# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024NewA..10902199M\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Instructions

You turn one published astronomy paper that used ALMA data into a structured METHODS CARD. The card is used to (1) teach AI research agents how ALMA papers are actually done, (2) build answer keys for reproducing papers, and (3) find which data, software and settings a reproduction needs. Accuracy matters more than coverage.

Hard rules:
1. Use only the paper text you are given. Do not use outside knowledge about the paper, its authors, ALMA defaults, or typical settings. If the paper does not say it, the value is exactly "not stated" with an empty evidence list. Never guess, never "typically", never fill a default.
2. Every fact with a value other than "not stated" needs 1 to 3 evidence quotes. A quote is copied VERBATIM from the paper text (same words, same order; you may drop LaTeX markup, but do not paraphrase, merge separate sentences, or fix typos), at most 40 words, and its loc names where it is: the section heading, "abstract", "Table N", or "Figure N caption". Quotes are checked mechanically against the text.
3. Keep values short and in the paper's own terms and units (e.g. "Band 6 (1.3 mm)", "robust = 0.5", "CASA 5.4.0").
4. Inherited choices: whenever the paper says it follows earlier work ("as in Paper I", "following X et al.", "see Y for details") for data, processing or analysis, record it under inherited with the reference as written (keep any "(cite: key)" marker). These are often what blocks a reproduction.
5. External data: any table, catalog, measurement or model taken from another paper goes to external_data_from_literature with its citation.
6. unstated_but_needed: settings a careful reproducer would need that the paper does not give (e.g. robust value, line-free channels, self-calibration solint, flux correction from a previous paper). This list is your reading, so it has no quotes; be specific and do not pad it.
7. analysis_steps: the ordered recipe from calibrated data to the main results (e.g. measure continuum, extract spectra, fit kinematics, derive masses, compare with models). Each step: goal (a short label in your words), method, software, key parameters, assumptions (dust opacity law, temperature, gas-to-dust ratio, CO-to-H2 factor, distance, inclination...), fitting (sampler, priors, likelihood) and how they validated it. Steps are numbered from 1.
8. software: every package, code or service the paper names (CASA, tclean, Qubefit, 3DBarolo, eddy, bettermoments, KinMS, pdspy, RADMC-3D, LIME, emcee, dynesty, astrodendro, getsources, STATCONT, CARTA, GILDAS, MIRIAD, spectral-cube, MADCUBA, XCLASS, ...) with what it was used for. Do not add software the paper does not name.
9. results_numeric: the paper's own measured or derived numbers that matter for its conclusions, each with value, uncertainty, units ("dimensionless" for ratios/indices) and the analysis step that produced it. These become answer keys, so copy numbers exactly. Skip numbers that are only quoted from other papers.
10. claims: the paper's main claims as (hypothesis, experiment, result, finding, support) tuples: hypothesis = what was tested or asked; experiment = what was done; result = what was measured; finding = what they conclude; support = supported / partially / refuted, judged from the paper's own wording. 2-6 claims.
11. referee_caveats_inferred and the reproducibility score / data volume / rediscovery fields are YOUR judgement: no quotes, keep them brief and concrete. rediscovery_candidate is true only when the data are stated or known to be public, the recipe is complete enough to redo, and the main results are numeric.
12. ALMA project codes look like 2015.1.00123.S; list each one the paper prints, with a quote. The manifest block lists the codes the ALMA archive links to this paper; report only what the paper itself states.
13. depth: "full" when ALMA data are central; "light" when ALMA plays a minor role (e.g. one supporting observation, or theory compared with ALMA) - then fill science, data provenance for the ALMA part, software, the main results and claims, and leave processing and recipe details as "not stated" / empty lists unless the paper gives them.
14. The paper text is Markdown converted from LaTeX or PDF. "(cite: key)" marks a citation and "(ref: key)" a reference-list entry. Tables may be Markdown tables. Ignore conversion noise; never quote it.
15. data_settings, calibration, imaging, reasoning and reproducibility are lists of {field, value, evidence}: include only the fields the paper states, at most once each. Fields you leave out are recorded as "not stated". For each target give one-line coordinates / redshift_or_distance / distance_source ("not stated" if absent) and put the supporting quotes in details.
16. Output only the JSON object, no prose and no code fence.

Output format: one JSON object, with no prose and no code fence around it, that validates against this JSON Schema (every property is required; use "not stated" and empty lists where the paper is silent):
{"$defs":{"CalSetting":{"additionalProperties":false,"properties":{"field":{"enum":["pipeline_or_manual","casa_version","pipeline_version","archive_products_used_as_is","flux_calibrator","flux_scale_uncertainty","self_calibration"],"type":"string"},"value":{"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["field","value","evidence"],"type":"object"},"CitedWork":{"additionalProperties":false,"properties":{"citation":{"type":"string"},"why":{"type":"string"}},"required":["citation","why"],"type":"object"},"Claim":{"additionalProperties":false,"properties":{"hypothesis":{"type":"string"},"experiment":{"type":"string"},"result":{"type":"string"},"finding":{"type":"string"},"support":{"enum":["supported","partially","refuted"],"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["hypothesis","experiment","result","finding","support","evidence"],"type":"object"},"DataSetting":{"additionalProperties":false,"properties":{"field":{"enum":["bands","frequencies_and_spectral_setup","continuum_bandwidth","arrays","configurations","baselines","angular_resolution","max_recoverable_scale","sensitivity","time_on_source","observing_dates","pi_or_archival_as_stated"],"type":"string"},"value":{"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["field","value","evidence"],"type":"object"},"Evidence":{"additionalProperties":false,"properties":{"loc":{"description":"Section heading (e.g. '2.1 Observations') or 'abstract', 'Table 2', 'Figure 3 caption'","type":"string"},"quote":{"description":"Verbatim text copied from the paper, at most 40 words","type":"string"}},"required":["loc","quote"],"type":"object"},"ExternalData":{"additionalProperties":false,"properties":{"what":{"$ref":"#/$defs/Fact","description":"Table, catalog or measurement taken from another paper"},"citation":{"description":"The cited work as written in the paper, with its (cite: key) if present","type":"string"}},"required":["what","citation"],"type":"object"},"Facility":{"additionalProperties":false,"properties":{"name":{"type":"string"},"provided":{"$ref":"#/$defs/Fact","description":"What this facility, survey or archive contributed"}},"required":["name","provided"],"type":"object"},"Fact":{"additionalProperties":false,"properties":{"value":{"description":"The fact in the paper's terms, or exactly 'not stated'","type":"string"},"evidence":{"description":"1-3 verbatim quotes supporting the value; empty when not stated","items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["value","evidence"],"type":"object"},"ImgSetting":{"additionalProperties":false,"properties":{"field":{"enum":["task","deconvolver","weighting_robust","uv_taper","cell_size","image_size","masking","multiscale_scales","continuum_subtraction","line_free_channels","primary_beam_correction","array_combination","smoothing","final_beam","final_rms"],"type":"string"},"value":{"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["field","value","evidence"],"type":"object"},"Inherited":{"additionalProperties":false,"properties":{"what":{"$ref":"#/$defs/Fact","description":"A choice the paper takes from earlier work ('as in Paper I', 'following X')"},"from_reference":{"type":"string"}},"required":["what","from_reference"],"type":"object"},"NumericResult":{"additionalProperties":false,"properties":{"quantity":{"type":"string"},"value":{"type":"string"},"uncertainty":{"description":"As stated (e.g. '+0.3/-0.2', '10%'), or 'not stated'","type":"string"},"units":{"description":"Units as stated; 'dimensionless' for ratios and indices","type":"string"},"from_step":{"description":"order of the analysis step that produced it; 0 if not tied to one","type":"integer"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["quantity","value","uncertainty","units","from_step","evidence"],"type":"object"},"ProjectCode":{"additionalProperties":false,"properties":{"code":{"description":"ALMA project code exactly as printed, e.g. 2015.1.00123.S","type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["code","evidence"],"type":"object"},"ReasonSetting":{"additionalProperties":false,"properties":{"field":{"enum":["why_this_data","why_this_method","how_they_decided_enough"],"type":"string"},"value":{"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["field","value","evidence"],"type":"object"},"ReproSetting":{"additionalProperties":false,"properties":{"field":{"enum":["data_public_as_stated","products_in_archive"],"type":"string"},"value":{"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["field","value","evidence"],"type":"object"},"Software":{"additionalProperties":false,"properties":{"name":{"type":"string"},"version":{"description":"Version as stated, or 'not stated'","type":"string"},"used_for":{"$ref":"#/$defs/Fact"}},"required":["name","version","used_for"],"type":"object"},"SpectralLine":{"additionalProperties":false,"properties":{"species":{"type":"string"},"transition":{"type":"string"},"rest_frequency":{"type":"string"},"evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"}},"required":["species","transition","rest_frequency","evidence"],"type":"object"},"WireStep":{"additionalProperties":false,"properties":{"order":{"type":"integer"},"goal":{"description":"Short label for the step (our wording, e.g. 'measure the continuum flux')","type":"string"},"method":{"$ref":"#/$defs/Fact"},"software":{"items":{"type":"string"},"type":"array"},"key_parameters":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"assumptions":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"fitting":{"$ref":"#/$defs/Fact"},"validation":{"$ref":"#/$defs/Fact"}},"required":["order","goal","method","software","key_parameters","assumptions","fitting","validation"],"type":"object"},"WireTarget":{"additionalProperties":false,"properties":{"name":{"type":"string"},"details":{"description":"Quotes giving its coordinates, redshift/distance and where the distance comes from; empty if none","items":{"$ref":"#/$defs/Evidence"},"type":"array"},"coordinates":{"type":"string"},"redshift_or_distance":{"type":"string"},"distance_source":{"type":"string"}},"required":["name","details","coordinates","redshift_or_distance","distance_source"],"type":"object"}},"additionalProperties":false,"properties":{"depth":{"enum":["full","light"],"type":"string"},"paper_type":{"enum":["observational_alma_primary","archival_reuse","large_program_or_survey","multi_facility_alma_minor","technical_calibration_or_instrument","theory_or_simulation_compared_to_alma","data_release_or_catalog"],"type":"string"},"paper_type_evidence":{"items":{"$ref":"#/$defs/Evidence"},"type":"array"},"fields":{"items":{"enum":["protoplanetary_disks","debris_disks","star_formation","astrochemistry","high_z_galaxies","nearby_galaxies","agn_and_quasars","galaxy_clusters_and_sz","evolved_stars","stellar_physics","solar_system","sun","exoplanets","milky_way_ism","cosmology","transients","instrumentation","other"],"type":"string"},"type":"array"},"question":{"$ref":"#/$defs/Fact"},"targets":{"items":{"$ref":"#/$defs/WireTarget"},"type":"array"},"alma_project_codes":{"items":{"$ref":"#/$defs/ProjectCode"},"type":"array"},"data_settings":{"items":{"$ref":"#/$defs/DataSetting"},"type":"array"},"lines_targeted":{"items":{"$ref":"#/$defs/SpectralLine"},"type":"array"},"other_facilities":{"items":{"$ref":"#/$defs/Facility"},"type":"array"},"external_data_from_literature":{"items":{"$ref":"#/$defs/ExternalData"},"type":"array"},"simulations_or_models_as_data":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"calibration":{"items":{"$ref":"#/$defs/CalSetting"},"type":"array"},"imaging":{"items":{"$ref":"#/$defs/ImgSetting"},"type":"array"},"inherited":{"items":{"$ref":"#/$defs/Inherited"},"type":"array"},"unstated_but_needed":{"items":{"type":"string"},"type":"array"},"analysis_steps":{"items":{"$ref":"#/$defs/WireStep"},"type":"array"},"software":{"items":{"$ref":"#/$defs/Software"},"type":"array"},"results_numeric":{"items":{"$ref":"#/$defs/NumericResult"},"type":"array"},"findings_qualitative":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"claims":{"items":{"$ref":"#/$defs/Claim"},"type":"array"},"reasoning":{"items":{"$ref":"#/$defs/ReasonSetting"},"type":"array"},"alternatives_considered_or_rejected":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"limitations_admitted":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"referee_caveats_inferred":{"items":{"type":"string"},"type":"array"},"reproducibility":{"items":{"$ref":"#/$defs/ReproSetting"},"type":"array"},"code_released":{"items":{"$ref":"#/$defs/Fact"},"type":"array"},"missing_for_reproduction":{"items":{"type":"string"},"type":"array"},"estimated_data_volume_inferred":{"type":"string"},"score_inferred":{"type":"integer"},"score_reason":{"type":"string"},"rediscovery_candidate":{"type":"boolean"},"rediscovery_reason":{"type":"string"},"methods_papers":{"items":{"$ref":"#/$defs/CitedWork"},"type":"array"},"companion_papers":{"items":{"$ref":"#/$defs/CitedWork"},"type":"array"},"related_projects_or_surveys":{"items":{"type":"string"},"type":"array"}},"required":["depth","paper_type","paper_type_evidence","fields","question","targets","alma_project_codes","data_settings","lines_targeted","other_facilities","external_data_from_literature","simulations_or_models_as_data","calibration","imaging","inherited","unstated_but_needed","analysis_steps","software","results_numeric","findings_qualitative","claims","reasoning","alternatives_considered_or_rejected","limitations_admitted","referee_caveats_inferred","reproducibility","code_released","missing_for_reproduction","estimated_data_volume_inferred","score_inferred","score_reason","rediscovery_candidate","rediscovery_reason","methods_papers","companion_papers","related_projects_or_surveys"],"type":"object"}

## Paper

Manifest facts (from ADS and the ALMA archive, for orientation only):
```json
{
 "bibcode": "2024NewA..10902199M",
 "title": "Detection of possible glycine precursor molecule methylamine towards the hot molecular core G358.93─0.03 MM1",
 "year": 2024,
 "journal": "New Astronomy",
 "first_author": "Manna, Arijit",
 "n_authors": 2,
 "arxiv_id": "2402.16798",
 "doi": "10.1016/j.newast.2024.102199",
 "alma_projects_linked_by_archive": [
  "2019.1.00768.S"
 ]
}
```

Paper text:
<paper>
# Detection of possible glycine precursor molecule methylamine towards the hot molecular core G358.93–0.03 MM1

## Abstract

The search for the simplest amino acid, glycine (), in the interstellar medium (ISM) has become a never-ending story for astrochemistry and astrophysics researchers because that molecule plays a possible connection between the Universe and the origin of life. In the last forty years, all searches for in the ISM at millimeter and submillimeter wavelengths have failed. Since the detection of in the ISM was extremely difficult, we aimed to search for the possible precursors of . Earlier, many laboratory experiments have suggested that methylamine () plays an important role in the ISM as a possible precursor of . After spectral analysis using the local thermodynamic equilibrium (LTE) model, we identified the rotational emission lines of towards the hot molecular core G358.93–0.03 MM1 using the Atacama Large Millimeter/Submillimeter Array (ALMA). The column density of towards the G358.93–0.03 MM1 was estimated to be (1.10$\pm$0.31)$\times$10$^{17}$ cm$^{-2}$ with an excitation temperature of 180.8$\pm$25.5 K. The fractional abundance of with respect to towards the G358.93–0.03 MM1 was (8.80$\pm$2.60)$\times$10$^{-8}$. The column density ratio of and towards G358.93–0.03 MM1 was (1.86$\pm$0.95)$\times$10$^{2}$. The estimated fractional abundance of towards the G358.93–0.03 MM1 agrees fairly well with the previous three-phase warm-up chemical modelling abundance of . We also discussed the possible formation mechanism of , and we find that is most probably formed via the reactions of radical and radical on the grain surface of G358.93–0.03 MM1.

ISM: individual objects (G358.93–0.03 MM1) ,ISM: abundances ,stars: formation ,Astrochemistry

# Introduction

The initial chemical development leading to the formation of life is believed to have formed in molecular clouds, proceeded inside the protoplanetary disk, and transported into the planetary atmosphere with the help of comets and asteroids (cite: suz19). The investigation of complex nitrogen-bearing molecules like hydrogen cyanide (HCN), formamide (), methyleneimine (), methylamine (), cyanamide (), and aminoacetonitrile () was extremely important because these prebiotic molecules are essential for the production of amino acids in the interstellar medium (ISM) (cite: her09; gar13; bo19; man22a; man22b; man23a). In the ISM, the hot molecular cores are one of the earlier stages of high-mass star-formation regions, and they play a crucial role in enhancing the chemical complexity in the ISM (cite: shi21). The hot molecular cores are ideal candidates to study the complex prebiotic molecules because they contain a compact and small source size ($<$0.1 pc), a warm environment ($>$100 K), and a high gas density ($n_{\ce{H2}}$$>$10$^{6}$ cm$^{-3}$) that promotes molecular evolution by thermal hopping on dust grains (cite: van98; wi14). The chemistry of the hot cores is characterised by the sublimation of ice mantles, which accumulated during the star-formation activities (cite: shi21). The gaseous molecules and atoms are frozen onto the dust grains in prestellar cores and cold molecular clouds. As the temperature of the dust rises due to star-formation activities, the chemical interactions between heavy species become active on the grain surfaces, resulting in the formation of more complex organic molecules (cite: gar06; shi21). In addition, sublimated molecules such as methanol () and ammonia () are also subjected to further gas-phase reactions (cite: nom04; taq16). As a result, the warm, dense, and chemically abundant gas around the protostars develops into one of the strongest molecular line emitters, known as the hot molecular cores. The hot molecular cores are crucial objects for astrochemical studies because a multiplicity of simple and complex organic molecules are frequently found in the hot cores (cite: her09). The period of the hot molecular cores is thought to last about 10$^{5}$ years to 10$^{6}$ years (cite: van98; vi04; gar06; gar08; gar13).

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Band | Date of observation | Start time | End time | Number | Frequency range | Spectral resolution | Angular resolution |  |  |  |  |  |  |  |  |  |
|  | (yyyy mm dd) | (hh:mm) | (hh:mm) | of antennas | (GHz) | (kHz) | ($\prime\prime$) |  |  |  |  |  |  |  |  |  |
| 7 | 2019 Nov 11 | 20:50 | 21:20 | 47 | 290.51–292.39 | 976.56 | 0.42 |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  | 292.49–294.37 | 976.56 |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  | 302.62–304.49 | 976.56 |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  | 304.14–306.01 | 976.56 |  |  |  |  |  |  |  |  |  |  |

In recent years, several molecular species that are recognised as precursors to biologically relevant molecules have been identified in the ISM at millimeter and sub-millimeter wavelengths. The search for amino acids and their possible precursors in the hot molecular cores is one of the most important topics in modern astrochemistry because, earlier, several authors claimed the hot molecular core is an ideal candidate for searching for amino acids and their possible precursors (cite: hal13; gar13; ohi19; suz19; bo19). Previously, all surveys of the simplest amino acid glycine () towards the hot molecular cores (such as Sgr-B2, Orion KL, etc.) failed because the predicted emission lines of were blended with other nearby molecular transitions (cite: jon07; cun07). Earlier, (cite: kua03) claimed to have made the first detections towards the Orion KL, Sgr B2 (N-LMH), and W51 e1/e2, but multiple follow-up observations revealed that these detections were false (cite: jon07). The Rosetta Orbiter Spectrometer for Ion and Neutral Analysis (ROSINA) mass spectrometer has identified volatile from the coma of the comet 67P/Churyumov-Gerasimenko (cite: alt16). Earlier, all investigations of the towards the hot molecular cores failed due to the low-sensitivity telescopes, but recently, high-resolution ALMA has been designed specifically to detect the amino acids from the ISM. Earlier, (cite: jim14) computed a 1D spherically symmetric radiative transfer model, and they claimed that there are high chances of detecting the emission lines of from the low-mass pre-stellar core L1544 using ALMA bands 3 and 4. Previously, (cite: gar13) predicted that the emission lines of would be detectable using ALMA with one hour of on-source integration time towards the NGC 6334 IRS1.

The complex prebiotic molecule contains the simplest primary amine (R–) functional group and that molecule has been suggested as a possible precursor to the simplest amino acid, (cite: kim11; thu11; gar13). The interstellar molecule was first detected in the high-mass star-formation region Sgr B2, which is located in the galactic centre (cite: kai74). Later, (cite: hal13) detected individual 170 transition lines of towards the Sgr B2 (N) with a fractional abundance of 1.7$\times$10$^{-9}$. Earlier, the tentative absorption lines of were detected from the quasar PKS 1830–211 (cite: mu11). Earlier, (cite: lig15) made a spectral line survey towards the nine hot molecular cores using the James Clerk Maxwell Telescope (JCMT), but they could not identify that molecule within the 3$\sigma$ significance. The evidence of was also found from the coma of the comet 67P/Churyumov-Gerasimenko (cite: alt16). The abundance of with respect to in the comet 67P/Churyumov-Gerasimenko is 1.0$\pm$0.5 (cite: alt16). The column density of towards 67P/Churyumov-Gerasimenko is 1.18$\times$10$^{17}$ cm$^{-2}$ (cite: ma18). The emission lines of were also detected towards the hot molecular core region NGC 6334I MM1–MM3 using ALMA bands 7 and 10 (cite: bo19). The evidence of the emission lines of was also found towards the hot molecular core object G10.47+0.03, with an estimated fractional abundance of 1.5$\times$10$^{-8}$ (cite: ohi19). Recently, (cite: pag17) presented the tentative detection of the rotational emission lines of towards the Orion KL using ALMA in the frequency range of 219.442–220.127 GHz. Previously, (cite: lig18) attempted to use the ALMA to search for emission lines towards the low mass protostar IRAS 16293-2422 B, but they were unable to detect this molecule. Recently, (cite: naz22) made a spectral line survey of and other nitrogen-bearing molecules towards the thirty-seven high-mass sources using ALMA band 6.

![](cont.pdf)

The massive star-formation region G358.93–0.03 (RA: 17$^{h}$43$^{m}$10$^{s}$.02, Dec: -29$^{\circ}$51$^{\prime}$45.8$^{\prime\prime}$) is located at a distance of 6.75$\,{}\,^{\,+0.37}_{\,-0.68}$  kpc (cite: re14; bro19). The high-mass star-formation region G358.93–0.03 contains eight sub-millimeter continuum sources, which are designated MM1–MM8 in order of decreasing right ascension (R.A) (cite: bro19). The luminosity of G358.93–0.03 is $\sim$7.7$\times$10$^{3}$ L$_{\odot}$ and the total gas mass is 167$\pm$12M$_{\odot}$ (cite: bro19). Among the eight continuum sources, MM1 and MM3 (hereafter, G358.93–0.03 MM1 and G358.93–0.03 MM3) are the brightest continuum sources, which host line-rich hot molecular cores (cite: bro19; bay22). Earlier, (cite: bro19) and (cite: ste21) discussed the physical properties of hot molecular cores G358.93–0.03 MM1 and G358.93–0.03 MM3. Recently, (cite: bro19) discovered fourteen methanol () maser lines from G358.93–0.03 MM1, and they also detected the emission lines of methyl cyanide () from G358.93–0.03 MM1 and G358.93–0.03 MM3 using ALMA, but the authors do not estimate the abundance of . (cite: bro19) also do not describe the formation mechanism of and towards the G358.93–0.03 MM1. In the hot molecular cores, is a highly abundant molecule, and it is formed on the grain surface via the hydrogenation process from CO (CO$\stackrel{\ce{H2}}{\longrightarrow}$$\stackrel{\rm H_{2}}\longrightarrow$) (cite: gar13; suz16). Similarly, the molecule was formed in the hot molecular cores via the radiative association of $^{+}$ with HCN or CN with (cite: cha92; mil97). Recently, (cite: chen20) detected the maser emission lines of deuterated water (HDO), isocyanic acid (HNCO), and $^{13}$ towards the G358.93–0.03 using the TMRT and VLA radio telescopes. Recently, the rotational emission lines of the possible urea () precursor molecule cyanamide () and simplest sugar-like molecule glycolaldehyde () were also detected towards the G358.93–0.03 MM1 using ALMA (cite: man23a; man23b). The detection of and indicates that other nitrogen-bearing molecules such as HCN, , , and would be observable towards the G358.93–0.03 MM1. We first attempted to search for possible glycine precursor molecules towards the G358.93–0.03 MM1 using ALMA band 7.

In this article, we present the first detection of a possible precursor molecule, , towards the hot molecular core region G358.93–0.03 MM1 using ALMA. We applied the local thermodynamic equilibrium (LTE) model to estimate the column density and gas temperature of . We also discussed the possible formation mechanism of towards the G358.93–0.03 MM1. The ALMA observations and data reduction were presented in Section [2](#obs). The result of the detection of emission lines of was shown in Section [3](#res). The discussion and conclusion of the detection of towards the G358.93–0.03 MM1 were shown in Section [4](#dis) and [5](#conclu).

![](lte.pdf)

# Observations and data reductions

The high-mass star-formation region G358.93–0.03 was observed to study the massive protostellar accretion outburst using the Atacama Large Millimeter/Submillimeter Array (ALMA) band 7 (covering the frequency range 290.51–306.01 GHz) receiver (PI: Crystal Brogan). The observation of G358.93–0.03 was performed on November 11, 2019, with phase center ($\alpha,\delta$)$_{\rm J2000}$ = 17:43:10.000, –29:51:46.000 with on-source integration time 756.0 sec. During the observation, a total of 47 antennas were used. For ALMA band 7, the minimum baseline was 14 m and the maximum baseline was 2517 m. During the observation of G358.93–0.03, J1550+0527 was taken as a flux calibrator and bandpass calibrator, and J1744–3116 was taken as a phase calibrator. The observation summary is presented in Table [\[tab:obs\]](#tab:obs).

We used the Common Astronomy Software Application (`CASA 5.4.1`) for data reduction and imaging with the ALMA data reduction pipeline (cite: mc07). We used the Perley-Butler 2017 flux calibrator model for flux calibration with flux calibrator J1550+0527 for each baseline using the task `SETJY` (cite: pal17). We used the `CASA` pipeline with tasks `hifa_bandpassflag` and `hifa_flagdata` to construct the flux and bandpass calibration after flagging the bad antenna data. We utilised the task `MSTRANSFORM` to divide the target data set into another data set with all available rest frequencies after the initial data calibration. We create the continuum emission image of G358.93–0.03 using the task TCLEAN with line-free channels. The continuum emission image of G358.93–0.03 at frequency 291.318 GHz is shown in Figure [1](#fig:continuum). In the continuum emission image of G358.93–0.03, we observed all submillimeter continuum sources. Recently, (cite: man23a) and (cite: man23b) discussed in detail the continuum emission from G358.93–0.03 using ALMA. We used the task `UVCONTSUB` in the UV plane of split calibrated data for the continuum subtraction operation. For each rest frequency, we used task `TCLEAN` with a Briggs weighting robust value of 0.5 to construct spectral images of G358.93–0.03. For the correction of the primary beam pattern in the continuum and spectral images, we used the CASA task `IMPBCOR`.

# Result

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Observed frequency | Transition | $E_{u}$ | $A_{ij}$ | g$_{up}$ | $\mu^{2}S$$^{\dagger}$ | FWHM | Optical depth | Remark |  |  |  |  |  |  |  |  |
| (GHz) | (${\rm J^{'}_{K_a^{'}\Gamma^{'}}}$–${\rm J^{''}_{K_a^{''}\Gamma^{''}}}$) | \(K\) | (s$^{-1}$) |  | (Debye$^{2}$) | (km s$^{-1}$) | ($\tau$) |  |  |  |  |  |  |  |  |  |
| 290.567 | 13(2)$E_{1+1}$–13(1)$E_{1-1}$ | 209.85 | 6.10$\times$10$^{-5}$ | 324 | 69.19 | 3.50$\pm$0.56 | 5.81$\times$10$^{-2}$ | Non blended |  |  |  |  |  |  |  |  |
| 290.684 | 8(0)$E_{2+1}$–7(1)$E_{2-1}$ | 77.10 | 4.07$\times$10$^{-6}$ | 68 | 0.96 | 3.50$\pm$0.98 | 1.26$\times$10$^{-3}$ | Blended with c- |  |  |  |  |  |  |  |  |
| 290.824 | 9(0)$A_{2}$–8(1)$A_{1}$ | 95.63 | 8.18$\times$10$^{-5}$ | 76 | 21.71 | 3.50$\pm$0.39 | 2.67$\times$10$^{-2}$ | Blended with |  |  |  |  |  |  |  |  |
| 291.404 | 15(2)$E_{1-1}$–15(1)$E_{1-1}$ | 270.87 | 4.18$\times$10$^{-6}$ | 372 | 5.40 | 3.50$\pm$0.41 | 3.71$\times$10$^{-3}$ | Blended with |  |  |  |  |  |  |  |  |
| 291.430 | 16(2)$E_{1-1}$–15(3)$E_{1-1}$ | 304.85 | 2.63$\times$10$^{-5}$ | 396 | 36.09 | 3.50$\pm$0.59 | 2.21$\times$10$^{-2}$ | Blended with |  |  |  |  |  |  |  |  |
| 291.510 | 20(8)$E_{1-1}$–21(7)$E_{1-1}$ | 695.57 | 2.40$\times$10$^{-5}$ | 492 | 40.97 | 3.50$\pm$0.62 | 6.84$\times$10$^{-3}$ | Blended with |  |  |  |  |  |  |  |  |
| 292.349 | 13(2)$E_{2-1}$–13(1)$E_{2-1}$ | 209.81 | 7.30$\times$10$^{-5}$ | 108 | 27.11 | 3.50$\pm$0.97 | 2.29$\times$10$^{-2}$ | Non blended |  |  |  |  |  |  |  |  |
| 293.125 | 13(1)$E_{2-1}$–12(2)$E_{2+1}$ | 195.77 | 3.56$\times$10$^{-5}$ | 108 | 13.12 | 3.50$\pm$0.65 | 6.91$\times$10$^{-3}$ | Partially Blended with $^{13}$CO |  |  |  |  |  |  |  |  |
| 293.128 | 12(2)$B_{1}$–12(1)$B_{2}$ | 182.38 | 8.00$\times$10$^{-5}$ | 300 | 81.85 | 3.50$\pm$0.39 | 4.50$\times$10$^{-2}$ | Non blended |  |  |  |  |  |  |  |  |
| 293.898 | 9(5)$E_{2+1}$–10(4)$E_{2+1}$ | 193.50 | 1.84$\times$10$^{-5}$ | 76 | 4.72 | 3.50$\pm$0.47 | 4.48$\times$10$^{-3}$ | Blended with OS$^{17}$O |  |  |  |  |  |  |  |  |
|  302.802$^{*}$ | 16(7)$B_{1}$–17(6)$B_{2}$ | 480.15 | 2.50$\times$10$^{-5}$ | 396 | 30.58 | 3.50$\pm$0.37 | 1.15$\times$10$^{-2}$ | Blended with |  |  |  |  |  |  |  |  |
| 302.866 | 16(2)$E_{1-1}$–15(3)$E_{1+1}$ | 304.85 | 1.53$\times$10$^{-5}$ | 396 | 18.69 | 3.50$\pm$0.45 | 1.26$\times$10$^{-2}$ | Blended with |  |  |  |  |  |  |  |  |
| 303.734 | 9(0)$E_{2+1}$–8(1)$E_{2+1}$ | 96.21 | 8.94$\times$10$^{-5}$ | 76 | 20.82 | 3.50$\pm$0.79 | 2.82$\times$10$^{-2}$ | Non blended |  |  |  |  |  |  |  |  |
| 303.922 | 12(6)$E_{2-1}$–13(5)$E_{2-1}$ | 305.79 | 2.22$\times$10$^{-5}$ | 100 | 6.78 | 3.50$\pm$0.71 | 4.58$\times$10$^{-3}$ | Blended with |  |  |  |  |  |  |  |  |
| 304.630 | 5(4)$E_{2-1}$–6(3)$E_{2-1}$ | 94.69 | 1.18$\times$10$^{-5}$ | 44 | 1.57 | 3.50$\pm$0.57 | 2.15$\times$10$^{-3}$ | Blended with |  |  |  |  |  |  |  |  |
| 304.768 | 14(2)$A_{1}$–14(1)$A_{2}$ | 239.95 | 7.94$\times$10$^{-5}$ | 116 | 27.96 | 3.50$\pm$0.25 | 2.36$\times$10$^{-2}$ | Non blended |  |  |  |  |  |  |  |  |

\
\*–The transition of contain double with frequency difference $\leq$100 kHz. The second transition is not shown.\
$\dagger$–The line intensity $\mu^{2}S$ is defined by the product of the square of the dipole moment $\mu^{2}$ and transition line strength $S$. The values of $\mu^{2}S$ of detected transitions of are taken from the JPL molecular database.\

## Line emission towards G358.93–0.03

From the spectral images of G358.93–0.03, we observed that only the spectra of hot molecular cores G358.93–0.03 MM1 and G358.93–0.03 MM3 show any line emission. We cannot see any line emission from other sources in G358.93–0.03. The synthesized beam sizes of the spectral images of G358.93–0.03 at frequency ranges of 290.51–292.39 GHz, 292.49–294.37 GHz, 302.62–304.49 GHz, and 304.14–306.01 GHz are 0.425$^{\prime\prime}\times$0.369$^{\prime\prime}$, 0.427$^{\prime\prime}\times$0.376$^{\prime\prime}$, 0.413$^{\prime\prime}\times$0.364$^{\prime\prime}$, and 0.410$^{\prime\prime}\times$0.358$^{\prime\prime}$, respectively. We generate the molecular spectra from G358.93–0.03 MM1 and G358.93–0.03 MM3 by creating a 0.91$^{\prime\prime}$ diameter circular region, which is larger than the line emitting regions of G358.93–0.03 MM1 and G358.93–0.03 MM3. The position of G358.93–0.03 MM1 is RA (J2000) = 17$^{h}$43$^{m}$10$^{s}$.101, Dec (J2000) = –29$^\circ$51$^{\prime}$45$^{\prime\prime}$.693. The position of G358.93–0.03 MM3 is RA (J2000) = 17$^{h}$43$^{m}$10$^{s}$.0144, Dec (J2000) = –29$^\circ$51$^{\prime}$46$^{\prime\prime}$.193. Recently, (cite: man23b) shows the resultant spectra of G358.93–0.03 MM1 and G358.93–0.03 MM3 between the frequency range of 290.51–306.01 GHz in Figure 2. (cite: man23b) shows that the molecular spectra of G358.93–0.03 MM1 are more chemically rich than G358.93–0.03 MM3. From the molecular spectra of G358.93–0.03 MM1, (cite: man23b) observes the inverse P-Cygni profile associated with lines towards the G358.93–0.03 MM1. This may indicate that the G358.93–0.03 MM1 is undergoing an infall. (cite: man23b) does not observe any inverse P-cygni profile in the spectra of G358.93–0.03 MM3. The systemic velocities ($V_{LSR}$) of G358.93–0.03 MM1 and G358.93–0.03 MM3 are –16.5 km s$^{-1}$ and –18.2 km s$^{-1}$, respectively (cite: bro19).

### Identification of towards G358.93–0.03 MM1

To identify the rotational emission lines of towards the G358.93–0.03 MM1, we used the local thermodynamic equilibrium (LTE) model with the Jet Population Laboratory (JPL) (cite: pic88) spectroscopic molecular database. We have used the LTE-RADEX module in CASSIS for the LTE modelling (cite: vas15). The LTE assumptions are reasonable in the inner region of the hot molecular core candidate G358.93–0.03 MM1 because the gas density of the warm inner region of the hot core was 2$\times$10$^{7}$ cm$^{-3}$ (cite: ste21). Additionally, we also fitted the LTE model to the other 250 molecules over the observed molecular spectra of G358.93–0.03 MM1 to understand the blended effect between other molecules and , including those molecules detected by (cite: man23a) and (cite: man23b). The LTE-fitted rotational emission spectra of are shown in Figure [2](#fig:ltespec). After the LTE analysis, we observed that the sixteen transition lines of are present within the observed frequency ranges, out of which five lines of are non-blended and clearly detected, while the remaining ones are blended with other lines. All the non-blended emission lines of are identified as higher than 5$\sigma$ (confirmed from LTE modelling). The upper-level energies of the identified sixteen transitions of vary from 77.10 K to 695.57 K. The upper-level energies of the non-blended transitions of vary between 96.21 K and 239.95 K. All the transitions of , generated by LTE model (non-blended or blended), are detected in the observable frequency ranges. The best-fit column density of was (1.10$\pm$0.31)$\times$10$^{17}$ cm$^{-2}$ with an excitation temperature of 180.8$\pm$25.5 K and a source size of 0.5$^{\prime\prime}$. Our derived column density of towards G358.93–0.03 MM1 is similar to the column density of in the comet 67P/Churyumov-Gerasimenko. Additionally, we also detected the emission lines of , , , , , , , and , which we discuss in a separate paper.

After the identification of the rotational emission lines of using the LTE model, we obtained the quantum numbers (${\rm J^{'}_{K_a^{'}\Gamma^{'}}}$–${\rm J^{''}_{K_a^{''}\Gamma^{''}}}$), upper state energy ($E_u$) in K, Einstein coefficients ($A_{ij}$) in s$^{-1}$, line intensity ($\mu^{2}S$) in Debye$^{2}$, full-width half maximum (FWHM) in km s$^{-1}$, and optical depth ($\tau$). The transitions of are labelled by the torsion-inversion rotation between the primary amine (R–) and the methyl group (R–), which was represented as $\Gamma$. The $\Gamma$ states are labelled with the $A_{1}$, $A_{2}$, $B_{1}$, $B_{2}$, $E_{1\pm1}$, and E$_{2\pm1}$ (cite: ily07). The selection rules of are $\Gamma$ = $A_{1}$$\leftrightarrow$$A_{2}$, $B_{1}$$\leftrightarrow$$B_{2}$, $E_{1\pm1}$$\leftrightarrow$$E_{1\pm1}$, and E$_{2\pm1}$$\leftrightarrow$E$_{2\pm1}$. The symmetry levels of have nuclear spin-statistical weights of 1 for the $A_{1}$, $A_{2}$, and $E_{2}$ states and 3 for the $B_{1}$ , $B_{2}$, and $E_{1}$ states. The hyperfine structures of are not considered in this analysis because the line intensity ($\mu^{2}S$) of the main transitions of is higher than hyperfine lines and current spectral resolution is not sufficient to resolve the hyperfine lines of . After the LTE analysis, we observed J = 13(2)$E_{1+1}$–13(1)$E_{1-1}$, J = 13(2)$E_{2-1}$–13(1)$E_{2-1}$, J = 12(2)$B_{1}$–12(1)$B_{2}$, J = 9(0)$E_{2+1}$–8(1)$E_{2+1}$, and J = 14(2)$A_{1}$–14(1)$A_{2}$ transition lines of are not contaminated with other nearby molecular transitions. From Figure [2](#fig:ltespec), it is clear that all LTE-fitted lines of are consistent with the observed spectra, but some of them are contaminated by stronger lines from other species. The summary of the detected transitions and spectral line properties of was presented in Table [\[tab:MOLECULAR DATA\]](#tab:MOLECULAR DATA).

To determine the fractional abundance of , we used the column density of inside the 0.45$^{\prime\prime}$ beam, which we divided by the column density of G358.93–0.03 MM1. The fractional abundance of with respect to towards the G358.93–0.03 MM1 is (8.80$\pm$2.60)$\times$10$^{-8}$, where the column density of towards the G358.93–0.03 MM1 is (1.25$\pm$0.11)$\times$10$^{24}$ cm$^{-2}$ (cite: man23a). The column density ratio of and towards G358.93–0.03 MM1 is (1.86$\pm$0.95)$\times$10$^{2}$, where the column density of towards G358.93–0.03 MM1 is (5.9$\pm$2.5)$\times$10$^{14}$ cm$^{-2}$(cite: man23a). We estimate the column density ratio of and because acts as a possible precursor of in the gas-phase, and both molecules share as a common precursor (cite: ram23). Earlier, (cite: ohi19) found that the abundance of towards another hot molecular core, G10.47+0.03, was (1.5$\pm$1.1)$\times$10$^{-8}$, which is nearly similar to our derived abundance of towards G358.93–0.03 MM1. This may indicate that the chemical formation route(s) of towards the G358.93–0.03 MM1 are similar to those in G10.47+0.03.

![](rotd.png)

### Rotational diagram analysis: estimation of the rotational temperature of 

To verify the estimated temperature from the LTE modelling, we have created the rotational diagram based on the five non-blended transitions of . Initially, we assumed that the identified emission lines were optically thin and that they were populated under local thermal equilibrium (LTE) conditions. For optically thin molecular emission lines, the equation of column density can be written as (cite: gold99), $$\begin{equation}
{N_u^{thin}}=\frac{3{g_u}k_B\int{T_{mb}dV}}{8\pi^{3}\nu S\mu^{2}}
\end{equation}$$ where $\int T_{mb}dV$ indicated the integrated intensity, $k_B$ is the Boltzmann constant, $\mu$ indicated the electric dipole moment, $g_u$ is the degeneracy of the upper state, $S$ indicated the strength of the transition lines, and $\nu$ is the rest frequency. The total column density of under LTE conditions can be written as,

$$\begin{equation}
\frac{N_u^{thin}}{g_u} = \frac{N_{total}}{Q(T_{rot})}\exp(-E_u/k_BT_{rot})
\end{equation}$$ where $T_{rot}$ is the rotational temperature of , $E_u$ is the upper state energy of , and ${Q(T_{rot})}$ defines the partition function at the extracted rotational temperature. The rotational partition function of at 75 K is 15560, at 150 K is 44047, and at 300 K is 124715. Equation 2 can be rearranged as, $$\begin{equation}
ln\left(\frac{N_u^{thin}}{g_u}\right) = ln(N)-ln(Q)-\left(\frac{E_u}{k_BT_{rot}}\right)
\end{equation}$$

The equation 3 indicated a linear relationship between $\ln(N_{u}/g_{u}$) and the upper state energy ($E_{u}$) of . The value $\ln(N_{u}/g_{u}$) was calculated using the equation 1. Equation 3 indicates that the spectral parameters with respect to different transition lines of should be fitted with a straight line whose slope is inversely proportional to rotational temperature ($T_{rot}$). For the rotational diagram, we estimated the spectral line parameters of after fitting a Gaussian model over the non-blended observed spectra of using the line analysis module in CASSIS. The resultant rotational diagram of is shown in Figure [3](#fig:rotd). In the rotational diagram, the vertical black error bars indicate the absolute uncertainty of $\ln(N_{u}/g_{u}$), which was estimated from the $\int T_{mb}dV$. The rotational diagram yields the rotational temperature of 180.5$\pm$69.9 K. This result agrees reasonably well with the value of 180.8$\pm$25.5 K, which is derived by the LTE spectral modelling.

![](map.pdf)

### Searching for towards G358.93–0.03 MM3

After the successful detection of the towards the G358.93–0.03 MM1, we also searched for emission lines of towards the G358.93–0.03 MM3 using the LTE-modelled spectra, which yielded no detection. The derived upper limit column density of towards the G358.93–0.03 MM3 is $\leq$(5.21$\pm$1.23)$\times$10$^{15}$ cm$^{-2}$. The upper limit of the fractional abundance of towards the G358.93–0.03 MM3 is $\leq$(1.48$\pm$0.46)$\times$10$^{-8}$. The column density of towards the G358.93–0.03 MM3 was (3.51$\pm$0.7)$\times$10$^{23}$ cm$^{-2}$ (cite: man23b).

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Frequency | Transition | E$_{up}$ | Emitting region |  |  |  |  |  |  |  |  |
| GHz | (${\rm J^{'}_{K_a^{'}K_c^{'}}}$–${\rm J^{''}_{K_a^{''}K_c^{''}}}$) | \(K\) | ($^{\prime\prime}$) |  |  |  |  |  |  |  |  |
| 290.567 | 13(2)$E_{1+1}$–13(1)$E_{1-1}$ | 209.85 | 0.423 |  |  |  |  |  |  |  |  |
| 292.349 | 13(2)$E_{2-1}$–13(1)$E_{2-1}$ | 209.81 | 0.427 |  |  |  |  |  |  |  |  |
| 293.128 | 12(2)$B_{1}$–12(1)$B_{2}$ | 182.38 | 0.425 |  |  |  |  |  |  |  |  |
| 303.734 | 9(0)$E_{2+1}$–8(1)$E_{2+1}$ | 96.21 | 0.430 |  |  |  |  |  |  |  |  |
| 304.768 | 14(2)$A_{1}$–14(1)$A_{2}$ | 239.95 | 0.427 |  |  |  |  |  |  |  |  |

: Estimated emitting regions of non-blended transitions of towards G358.93–0.03 MM1.

## Spatial distribution of towards G358.93–0.03 MM1

After the identification of the rotational emission lines of from G358.93–0.03 MM1, we created the integrated emission maps of using the CASA task `IMMOMENTS`. The integrated emission maps of towards the G358.93–0.03 MM1 were presented in Figure [4](#fig:emi). The integrated emission maps of towards the G358.93–0.03 MM1 were constructed by integrating the spectral images in the velocity ranges where the emission lines of were identified. We created the integrated emission maps only for the five non-blended transitions of towards the G358.93–0.03 MM1. The resultant integrated emission maps of were overlaid with a 1.02 mm continuum emission image of G358.93–0.03. We noticed that the integrated emission maps of exhibit a peak at the position of the continuum. The integrated emission maps indicate that the emission lines of originate from the high gas density, the warm inner region of G358.93–0.03 MM1. After the extraction of the integrated emission maps, we estimated the emitting regions of towards the G358.93–0.03 MM1 by fitting the 2D Gaussian over the integrated emission map of using CASA task `IMFIT`. The deconvolved beam size of the emitting region was estimated by the following equation,\
$$\begin{equation}
\theta_{S}=\sqrt{\theta^2_{50}-\theta^2_{beam}}
\end{equation}$$ where $\theta_{50} = 2\sqrt{A/\pi}$ indicated the diameter of the circle whose area ($A$) was enclosing the 50% line peak, and $\theta_{beam}$ was the half-power width of the synthesised beam (cite: riv17). The estimated emitting regions of are presented in Table [1](#tab:emittingregion). The emitting regions of vary between 0.423$^{\prime\prime}$–0.430$^{\prime\prime}$. The synthesised ALMA beams are diluted by a factor of $\sim$0.63 to 0.65. We noticed that the estimated emitting regions of are comparable to or slightly greater than the synthesised beam sizes of the integrated emission maps. This demonstrates that the detected transition lines were not spatially resolved or were only marginally resolved towards the G358.93–0.03 MM1. As a result, concluding the morphology of the spatial distribution of towards the G358.93–0.03 MM1 is impossible. Higher spatial and angular resolution observations are required to understand the spatial distribution of towards the G358.93–0.03 MM1.

# Discussion

##  towards G358.93–0.03 MM1 and comparision with other sources

We present the first confirmed detection of towards G358.93–0.03 MM1 with an estimated fractional abundance of (8.80$\pm$2.60)$\times$10$^{-8}$. The estimated excitation temperature of is 180.8$\pm$25.5 K, which indicates the emission lines of arise from the warm inner region of the G358.93–0.03 MM1 because the temperature of the hot core is above 100 K (cite: van98). Earlier, (cite: ohi19) detected the rotational emission lines of from another hot molecular core object, G10.47+0.03, with a spectral width of 3.1–6.9 km s$^{-1}$. (cite: ohi19) also does not consider the blended effect of with other molecular transitions towards the G10.47+0.03. (cite: ohi19) estimated column density of towards the G10.47+0.03 was (1.0$\pm$0.7)$\times$10$^{15}$ cm$^{-2}$ with rotational temperature 46$\pm$21 K. The fractional abundance of towards the G10.47+0.03 was (1.5$\pm$1.1)$\times$10$^{-8}$ (cite: ohi19). The measurements of rotational temperature in (cite: ohi19), is probably erroneous due to the limited resolution of the Nobeyama 45 m single dish radio telescope. Later, (cite: suz19) also detected the rotational emission lines of towards the G10.47+0.03 using ALMA with column density 9.4$\times$10$^{17}$ cm$^{-2}$ and rotational temperature 166 K. Aside from G10.47+0.03, emission lines were also detected from other hot molecular core candidates, Sgr B2 and Orion KL (cite: hal13; pag17). The emission lines of also detected towards galactic center cloud G+0.693–0.027 (cite: ze18). The fractional abundances of towards the Sgr B2, Orion KL, and G+0.693–0.027 are 1.7$\times$10$^{-9}$, 1.0$\times$10$^{-9}$, 2.2$\times$10$^{-8}$ respectively (cite: hal13; pag17; ze18). The fractional abundance of towards G358.93–0.03 MM1 is approximately one order of magnitude higher as compared to Orion KL and Sgr B2. The abundance of towards the G358.93–0.03 MM1 is nearly similar to the G10.47+0.03 and G+0.693–0.027. If we compare the abundance of with all sources where is detected, then we observe that the G358.93–0.03 MM1 is the most highly abundant source ever known.

+---------+--------------------------------------------------------------+----------------------------------+------------------------------------------------------------------------------------+-----------------------------+-------------------+---------------------+-------------------------------+---------------------+----------------------+--------------------------------+-------------------+---+
|         | Simulated Values$^{\rm a}$                                   |                                  | Observed Values                                                                    |                             |                   |                     |                               |                     |                      |                                |                   |   |
+:=======:+:==================:+:==================:+:==================:+:================================:+:===========================:+:===================:+:==============================:+:===========================:+:=================:+:===================:+:=============================:+:===================:+:====================:+:==============================:+:=================:+:=:+
| Species | Fast               | Medium             | Slow               |                                  | G358.93–0.03 MM1$^{\rm b}$  |                     |                                | G10.47+0.03$^{\rm c}$       |                   |                     | Sgr B2$^{\rm d}$              |                     |                      | Orion KL$^{\rm e}$             |                   |   |
+---------+--------------------+--------------------+--------------------+----------------------------------+-----------------------------+---------------------+--------------------------------+-----------------------------+-------------------+---------------------+-------------------------------+---------------------+----------------------+--------------------------------+-------------------+---+
|         | $f$()              | $f$()              | $f$()              | $f$()                            | Gas density                 | L$_{\odot}$         | $f$()                          | Gas density                 | L$_{\odot}$       | $f$()               | Gas density                   | L$_{\odot}$         | $f$()                | Gas density                    | L$_{\odot}$       |   |
+---------+--------------------+--------------------+--------------------+----------------------------------+-----------------------------+---------------------+--------------------------------+-----------------------------+-------------------+---------------------+-------------------------------+---------------------+----------------------+--------------------------------+-------------------+---+
|         | $8.0\times10^{-8}$ | $3.6\times10^{-8}$ | $6.8\times10^{-9}$ | (8.80$\pm$2.60)$\times$10$^{-8}$ | 2$\times$10$^{7}$ cm$^{-3}$ | 7.7$\times$10$^{3}$ | (1.5$\pm$1.1)$\times$10$^{-8}$ | 1$\times$10$^{7}$ cm$^{-3}$ | 7$\times$10$^{5}$ | $1.70\times10^{-9}$ | 1.7$\times$10$^{7}$ cm$^{-3}$ | 1.8$\times$10$^{6}$ | 1.0$\times$10$^{-9}$ | 1-10$\times$10$^{7}$ cm$^{-3}$ | 1$\times$10$^{5}$ |   |
+---------+--------------------+--------------------+--------------------+----------------------------------+-----------------------------+---------------------+--------------------------------+-----------------------------+-------------------+---------------------+-------------------------------+---------------------+----------------------+--------------------------------+-------------------+---+

Notes: a – Values taken from Table 8 of (cite: gar13);\
b – this work\
c –Taken from (cite: ohi19)\
  d – Taken from (cite: hal13)\
  e – Taken from (cite: pag17).

## Possible formation mechanism of and linking with 

Earlier, (cite: gar08) and (cite: gar13) proposed that is formed on the grain surface of the hot molecular cores by the reaction between radical and radical . The radicals and are created from the photodissociation of primarily and . Similarly, (cite: kim11) suggested that the molecule will be formed in the hot molecular cores during the warm-up phases due to the reactions between and when exposed to cosmic rays on the grain surface (+$\longrightarrow$). Alternatively, (cite: thu11) proposed that the and molecules can be created towards hot molecular cores due to hydrogenation of HCN on the dust surface (HCN $\stackrel{\rm 2H}{\longrightarrow}$ CH$_2$NH$\stackrel{\rm 2H}{\longrightarrow}$CH$_3$NH$_2$). Earlier, (cite: wal14) claimed that is created on grains at 10 K by the atom addition reactions to solid . That means acted as a possible precursor of in the hot molecular cores. (cite: lig15) shows an alternative formation route of and by two different gas-phase reaction pathways, 1. created between the reaction of CH radical and in the gas-phase (CH$^{\bullet}$(g) + (g)$\longrightarrow$ + H), 2. created between the reaction of radicals and in the gas-phase ($^{\bullet}$(g) + (g)$\longrightarrow$ + H). Additional chemical modelling was required to establish whether these gas-phase reactions can effectively reproduce the observed abundance of .

The simplest amino acid can be created in the solid phase of hot molecular cores when thermally reacts with under vacuum UV irradiation ($\stackrel{\rm CO_{2}}{\longrightarrow}$) (cite: hol05). Alternatively, (cite: gar13) and (cite: suz17) confirmed another efficient chemical pathway for the formation of in the hot molecular cores. They claimed the gas-phase reaction between the radical and radical HOCO can create towards hot molecular cores ( + HOCO$\longrightarrow$). The radical can be created on the grain surface of hot molecular cores by the photodissociation of ( + h$\nu$ $\longrightarrow$ + H) (cite: ohi19). Similarly, (cite: ohi19) claimed that the radical HOCO would be created when hydrogen atoms react with in the grain surface of hot molecular cores ( + H $\longrightarrow$ HOCO), but we observe (cite: gar13) claimed that the HOCO radical can be created from formic acid (HCOOH), not from . After the detection of highly abundant towards the G358.93–0.03 MM1, we claimed that the hot molecular core candidate G358.93–0.03 MM1 is the new glycine survey candidate for the future.

## Previous chemical modelling of towards the hot molecular cores

To understand the formation mechanism of towards the hot molecular core, we used the three-phase (gas, grain, and ice mantle) warm-up chemical modelling abundance of , which was done by (cite: gar13). That chemical modelling of (cite: gar13) is mainly used to understand the formation mechanism of and its precursors towards the hot molecular cores. During chemical modelling, (cite: gar13) assumed the isothermal collapse phase after a static warm-up phase. In the first phase (free-fall collapse), the gas density rapidly increases from $n_{H}$ = 3$\times$10$^{3}$ to 10$^{7}$ cm$^{-3}$, and the dust temperature reduces to 8 K from 16 K under the free-fall collapse. In the second phase (warm-up phase), the gas density remains constant at $\sim$10$^{7}$ cm$^{-3}$ and the temperature fluctuates rapidly from 8 K to 400 K over the time scales 5$\times$10$^{4}$ yr (fast warm-up), 2$\times$10$^{5}$ yr (medium warm-up), and 1$\times$10$^{6}$ yr (slow warm-up). In the chemical network used by (cite: gar13), the recombination of the radical and radical dominates the production of on the grains. In the warm-up phase, (cite: gar13) shows the abundance of towards the hot molecular cores was 8.0$\times$10$^{-8}$ for the fast warm-up condition, 3.6$\times$10$^{-8}$ for the medium warm-up condition, and 6.8$\times$10$^{-9}$ for the slow warm-up condition.

## Comparison with modelled and observed abundance of 

To understand the formation pathways of towards G358.93–0.03 MM1, we compare our estimated abundance of with the three-phase warm-up chemical modelled abundance of , which were done by (cite: gar13). This comparison is physically reasonable because the temperature and gas density of G358.93–0.03 MM1 is $\sim$150 K (cite: chen20) and $\sim$2$\times$10$^{7}$ cm$^{-3}$ (cite: ste21), respectively. Hence, the three-phase warm-up chemical model based on the timescales of (cite: gar13) is appropriate for explaining the chemical evolution of towards the G358.93–0.03 MM1. The comparison between the observed abundance and modelled abundance of is estimated based on fast, medium, and slow warm-up models, which are presented in Table [\[tab:comp\]](#tab:comp). We noticed that the fast warm-up model result was nearly similar to the observation values of towards the G358.93–0.03 MM1. This comparison indicates that the may form on the grain surface via the reaction between radical and radical towards the G358.93–0.03 MM1. Furthermore, we also compared the fractional abundance of towards the G10.47+0.03, Sgr B2, and Orion KL with the modelled abundance of , which is estimated by (cite: gar13) as presented in Table. [\[tab:comp\]](#tab:comp). The three-phase warm-up chemical model of (cite: gar13) is also reasonable towards G10.47+0.03, Sgr B2, and Orion KL because the gas density of those hot molecular cores is 1$\times$10$^{7}$ cm$^{-3}$, 1.7$\times$10$^{7}$ cm$^{-3}$, and 1$\times$10$^{7}$ cm$^{-3}$, respectively (cite: hal13; pag17; ohi19). We noticed that the medium warm-up model satisfied the abundance of towards the G10.47+0.03, but the slow warm-up model satisfied the abundance of towards the Sgr B2 and Orion KL. That comparison indicates may be created on the grain surface via the reaction between radical and radical towards the G358.93–0.03 MM1, G10.47+0.03, Sgr B2, and Orion KL with different time scales.

## Searching of towards G358.93–0.03 MM1

After the detection of a possible precursor molecule towards G358.93–0.03 MM1, we also searched the emission lines of the simplest amino acid conformers I and II towards the G358.93–0.03 MM1. After spectral analysis using the LTE model spectra of conformers I and II, we observe that all LTE predicted emission lines of are blended and below 2$\sigma$. Based on our LTE modelling, we estimated the 3$\sigma$ upper limit column density of conformers I and II were $\leq$3.26$\times$10$^{15}$ cm$^{-2}$ and $\leq$1.20$\times$10$^{13}$ cm$^{-2}$, respectively. The conformer I has a dipole moment of $\mu_{a}$ = 0.911 D (a-type) and $\mu_{b}$ = 0.607 D (b-type), whereas conformer II has a dipole moment of $\mu_{a}$ = 5.372 D (a-type) and $\mu_{b}$ = 0.93 D (b-type) (cite: lov95). The a-type transitions of are more evident than the b-type in the ISM because the line intensity of the molecule is proportional to the square of the dipole moment (cite: lov95). Our successful detection of towards the G358.93–0.03 MM1 using ALMA gives more confidence that the G358.93–0.03 MM1 is the ideal candidate for searching for and its isomers. We propose a spectral line survey of other possible precursor molecules such as , , , and also conformers I and II with higher angular resolution and higher integration time to solve the puzzle of in the ISM.

# Conclusion

In this article, we analysed the ALMA band 7 data of the massive star-formation region of G358.93–0.03. The main conclusions of this work are as follows:\
\
1. We identified a total of sixteen transition lines of towards the hot molecular core G358.93–0.03 MM1, which was located in the massive star-formation region G358.93–0.03. Among the sixteen transitions, we observed that only five transitions are non-blended.\
\
2. The estimated column density of towards the G358.93–0.03 MM1 was (1.10$\pm$0.31)$\times$10$^{17}$ cm$^{-2}$ with an excitation temperature of 180.8$\pm$25.5 K. The estimated fractional abundance of towards the G358.93–0.03 MM1 with respect to was (8.80$\pm$2.60)$\times$10$^{-8}$. The column density ratio of and towards G358.93–0.03 MM1 was (1.86$\pm$0.95)$\times$10$^{2}$.\
\
3. We compared our estimated fractional abundance of with the three-phase warm-up model abundance of , which was done by (cite: gar13). After the comparison, we noticed that the fast warm-up model abundance of satisfied the observed abundance of towards the G358.93–0.03 MM1. That comparison indicates may be created on the grain surface via the reaction between radical and radical towards the G358.93–0.03 MM1. We also compare our estimated abundance of towards G358.93–0.03 with other hot molecular core objects G10.47+0.03, Sgr B2, Orion KL, and galactic center cloud G+0.693–0.027. After that comparison, we observed that G358.93–0.03 MM1 is the most highly abundant source ever known. We also discuss the possible formation mechanism of and the link between the and in the hot molecular cores.\
\
4. We also searched the emission lines of the simplest amino acid conformers I and II towards the G358.93–0.03 MM1. We did not detect the emission lines of conformers I and II within the limits of LTE analysis. The estimated upper limit column densities of glycine conformers I and II were $\leq$3.26$\times$10$^{15}$ cm$^{-2}$ and $\leq$1.20$\times$10$^{13}$ cm$^{-2}$ respectively.\
\
5. The unsuccessful detection of towards G358.93–0.03 MM1 using ALMA indicated that the emission lines of may be below the confusion limit in the G358.93–0.03 MM1. Combined spectral line studies of other precursor molecules using the LTE model and two or three-phase warm-up chemical modelling are required to understand the prebiotic chemistry towards G358.93–0.03 MM1, which will be carried out in our follow-up study.

# ACKNOWLEDGEMENTS

We thank the anonymous rewiewer for her/his constructive comments that helped improve the manuscript. A.M. acknowledges Professor Serena Viti for helping with the discussion part of this manuscript. A.M. acknowledges the Swami Vivekananda Merit-cum-Means Scholarship (SVMCM) for financial support for this research. This paper makes use of the following ALMA data: ADS /JAO.ALMA#2019.1.00768.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in co-operation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

# DATA AVAILABILITY

The plots within this paper and other findings of this study are available from the corresponding author on reasonable request. The data used in this paper are available in the ALMA Science Archive (<https://almascience.nrao.edu/asax/>), under project code 2019.1.00768.S.

# Conflicts of interest

The authors declare no conflict of interest.

# CRedit authorship contribution statement

Arijit Manna: Analysed the ALMA data of G358.93–0.03 and identified the emission lines of , Writing original draft. Sabyasachi Pal: Conceptualize the project.

99

(ref: alo18) Alonso, E. R., Kolesniková, L., Białkowska-Jaworska, E., Kisiel, Z., León, I., Guillemin, J. C., Alonso, J. L., 2018, ApJ, 861, 70

(ref: alt16) Altwegg, K., Balsiger, H., Bar-Nun, A., et al., 2016, Science, 2

(ref: bo19) Bøgelund, E. G., McGuire, B. A., Hogerheijde, M. R., van Dishoeck, E. F., Ligterink, N. F. W., 2019, A&A, 624, A82

(ref: bro19) Brogan, C. L., Hunter, T. R., Towner, A. P. M., et al. 2019, ApJL, 881, L39

(ref: bel08) Belloche, A., Menten, K. M., Comito, C., Müller, H. S. P., Schilke, P., Ott, J., Thorwirth, S., Hieret, C., 2008, A&A, 482, 179.

(ref: bay22) Bayandina, O.S., Brogan, C.L., Burns, R.A., et al. 2022, AJ, 163(2), p.83

(ref: cox00) Cox, A. N., & Pilachowski, C. A. 2000, Physics Today, 53, 77

(ref: chen20) Chen, X., Sobolev, A. M., Ren, Z.-Y., et al. 2020, NatAs, 4, 1170

(ref: cun07) Cunningham, M. R., Jones, P. A. et al., 2007, MNRAS, 3, 1201-1210

(ref: cha92) Charnley, S. B., Tielens, A. G. G. M., & Millar, T. J. 1992, ApJ, 399, L71

(ref: das08) Das, A., Chakrabarti, S. K., Acharyya, K., & Chakrabarti, S. 2008, NewA, 13, 457

(ref: dan11) Danger, G., et al., 2011, A&A, 535, A47

(ref: gar13) Garrod, R. T. 2013, ApJ, 765, 60

(ref: gar08) Garrod, R. T., Weaver, S. L. W., & Herbst, E. 2008, ApJ, 682, 283

(ref: gar06) Garrod, R. T., & Herbst, E. 2006, A&A, 457, 927

(ref: gold99) Goldsmith, P. F., & Langer, W. D., 1999, ApJ, 517, 209

(ref: gor20) Gorai P., Bhat B., Sil M., Mondal S. K. Ghosh R., Chakrabarti S. K., Das A., 2020, ApJ, 895, 86

(ref: hol05) Holtom, P. D., Bennett, C. J., Osamura, Y., Mason, N. J., & Kaiser, R. I., 2005, ApJ, 626, 940

(ref: hal13) Halfen, D. T., Ilyushin, V. V., & Ziurys, L. M. 2013, ApJ, 767, 66

(ref: ily07) Ilyushin, V. V., & Lovas, F. J. 2007, JPCRD, 36, 1141

(ref: jon07) Jones. F. A., Cunningham. M. R., Godfrey P. D. & Cragg D. M., 2007, MNRAS, 347, 579

(ref: jim14) Jiménez-Serra, I., testi, L., Caselli, P., Viti, S., 2014, ApJL, 787, L33

(ref: kim11) Kim, Y. S., & Kaiser, R. I., 2011, ApJ, 729, 68

(ref: kua03) Kuan Y., Charnley S. B., Huang H., Tseng W. & Kisiel Z., 2003, ApJ, 593, 848

(ref: kai74) Kaifu, N., Morimoto, M., Nagane, K., et al., 1974, ApJ, 191, L135

(ref: kis22) Kisiel, Z., et al., 2022, A&A, 657, A99

(ref: lov95) Lovas, F. J., Kawashima, Y., Grabow, J. U., Suenram, R. D., Fraser, G. T., Hirota, E., 1995, ApJ, 455, L201

(ref: lig15) Ligterink, N. F. W., Tenenbaum, E. D., & Van Dishoeck, E. F. 2015, A&A, 576, A35

(ref: lig18) Ligterink, N.F.W., Calcutt, H., Coutens, A., Kristensen, L.E., et al. 2018, A&A, 619, A28

(ref: ma18) Mahjoub, A., and Hodyss, R., 2018, APJ, 869, 2

(ref: man22a) Manna, A., Pal, S., 2022a, Life Sci. Space Res. 34, 9, <https://doi.org/10.1016/j.lssr.2022.04.002>

(ref: man22b) Manna, A., Pal, S., 2022b, J. Astrophys. Astron. 43, 83, [https://link. springer.com/article/10.1007/s12036-022-09868-x](https://link. springer.com/article/10.1007/s12036-022-09868-x)

(ref: man23a) Manna, A., & Pal, S., 2023, Astrophys Space Sci 368, 33, <https://doi.org/10.1007/s10509-023-04192-4>

(ref: man23b) Manna, A., Pal, S., Viti, S., Sinha, S., 2023, MNRAS, 525, 2229-2240 <https://doi.org/10.1093/mnras/stad2185>

(ref: mil97) Millar, T. J., Macdonald, G. H., & Gibb, A. G. 1997, A&A, 325, 1163

(ref: mil53) Miller, S, L., 1953. Science, 117, 528

(ref: mc07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., Golap, K. 2007. CASA Architecture and Applications. Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mu11) Muller, S., et al. 2011. A&A, 535, A103

(ref: moto19) Motogi, K., Hirota, T., Machida, M. N., et al. 2019, ApJL, 877, L25

(ref: nom04) Nomura, H., & Millar, T. J. 2004, A&A, 414, 409

(ref: naz22) Nazari, P. et al., 2022, A&A, 668, A109

(ref: ohi19) Ohishi, M., Suzuki, T., Hirota, T., Saito, M. Kaifu, N., 2019, PASJ, 71, 86.

(ref: pag17) Pagani, L., Favre, C., Goldsmith, P. F., et al., 2017, A&A, 604, A32

(ref: pal17) Perley, R. A., Butler, B. J. 2017, ApJ, 230, 1538

(ref: pic88) Pickett, H. M., Poynte, R. L., Cohen, E. A., et al. 1998, Journal of Quantitative Spectroscopy and Radiative Transfer, 60, 883

(ref: re14) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2014, ApJ, 783, 130

(ref: riv17) Rivilla, V. M., et al., 2017, A&A, 598, A59

(ref: ram23) Ramal-Olmedo, J. C., Menor-Salván, C. A., Miyoshi, A., Fortenberry, R. C., 2023, A&A, 672, A49

(ref: shi21) Shimonishi, T., Izumi, N., Furuya, K., & Yasui, C., 2021, ApJ, 2, 206

(ref: suz19) Suzuki, T., Majumdar, L., Tokuda, K., Minamoto, H., Ohishi, M., Saito, M., Hirota, T., Nomura, H., Oya, Y., 2019, arXiv:1909.00528

(ref: suz16) Suzuki, T., Ohishi, M., Hirota, T., Saito, M., Majumdar, L., Wakelam, V., 2016, ApJ, 825, 79

(ref: suz17) Suzuki, T. 2017, PhD thesis, Graduate University for Advanced Studies

(ref: ste21) Stecklum, B., Wolf, V., Linz, H., et al., 2021. A&A, 646, p.A161.

(ref: thu11) Theule, P., Borget, F., Mispelaer, F., Danger, G., Duvernay, F., Guillemin, J. C., Chiavassa, T., 2011, A&A, 534, A64.

(ref: taq16) Taquet, V., Wirstr$\ddot{o}$m, E. S., & Charnley, S. B. 2016, ApJ, 821, 46

(ref: vi04) Viti, S., Collings, M. P., Dever, J. W., McCoustra, M. R. S., & Williams, D. A. 2004, MNRAS, 354, 1141

(ref: van98) van Dishoeck E. F., & Blake G. A. 1998, Annu Rev Astron Astrophys, 36, 317

(ref: her09) Herbst, E., & van Dishoeck, E. F. 2009, ARA&A, 47, 427

(ref: vas15) Vastel, C., Bottinelli, S., Caux, E., Glorian, J. -M., Boiziot, M., 2015, CASSIS: a tool to visualize and analyse instrumental and synthetic spectra. Proceedings of the Annual meeting of the French Society of Astronomy and Astrophysics, 313-316

(ref: whi92) Whittet, D. C. B. 1992, Journal of the British Astronomical Association, 102, 230

(ref: wal14) Walsh, C., Millar, T. J., Nomura, H., et al. 2014, A&A, 563, A33

(ref: wi14) Williams D. A., Viti S., 2014, Observational Molecular Astronomy: Exploring the Universe Using Molecular Line Emissions. Cambridge Univ. Press, Cambridge

(ref: ze18) Zeng, S., Jiménez-Serra, I., Rivilla, V. M., et al., 2018, MNRAS, 478, 2962-2975

</paper>

Write the methods card for this paper.