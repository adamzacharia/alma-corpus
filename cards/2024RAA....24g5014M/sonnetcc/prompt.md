# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024RAA....24g5014M\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. reproducibility.score_inferred is on a 1-5 scale (1 = cannot be reproduced from what is published, 5 = public data plus a complete recipe and numeric results). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2024RAA....24g5014M",
 "title": "Observation of Complex Organic Molecules Containing Peptide-like Bonds Toward Hot Core G358.93─0.03 MM1",
 "year": 2024,
 "journal": "Research in Astronomy and Astrophysics",
 "first_author": "Manna, Arijit",
 "n_authors": 2,
 "arxiv_id": "2406.00428",
 "doi": "10.1088/1674-4527/ad539b",
 "alma_projects_linked_by_archive": [
  "2018.A.00031.T",
  "2019.1.00768.S"
 ]
}
```

Paper text:
<paper>
# Observation of Complex Organic Molecules Containing Peptide-like Bonds Toward Hot Core G358.93–0.03 MM1

# Introduction

In complex organic molecules (hereafter COMs), the peptide bond \[–NH–C(=O)–\] links two amino acids to produce proteins. So, those COMs with peptide bonds provide information regarding the origin of life in the universe. In the interstellar medium (ISM), formamide (NH$_{2}$CHO), cyanamide (NH$_{2}$CN), isocyanic acid (HNCO), and acetamide (CH$_{3}$CONH$_{2}$) are COMs containing peptide-like bonds. has an amide-amide bond (–N–C(=O)–), which is crucial for the synthesis of proteins. NH$_{2}$CHO contains carbon (C), hydrogen (H), oxygen (O), and nitrogen (N), which are important for biological systems. NH$_{2}$CHO also acts as a prebiotic precursor of genetic and metabolic materials (cite: sal12). The dipole moment of NH$_{2}$CHO is $\mu_{a}$ = 3.61 Debye and $\mu_{b}$ = 0.852 (cite: kur57). The emission lines of NH$_{2}$CHO were first detected in high-mass star-formation regions Sgr B2 and Orion KL (cite: ru71). The evidence of NH$_{2}$CHO was also found in several high- and low-mass star-formation regions (cite: bis07; ad13; ka13; lo15; man24), extragalactic sources (cite: mu13), comets (cite: bro00; biv14; go15), and shocked regions (cite: yam12; men14).

In ISM, isocyanic acid (HNCO) is the simplest organic molecule, consisting of four biogenic elements, C, H, O, and N, all of which are present in living bodies. HNCO also acts as a precursor of several prebiotic COMs, including those molecules linked with astrochemical and astrobiological interest, such as amino acids, nucleobases, and sugars (cite: gor20; fed20). Laboratory experiments suggested that CH$_{4}$ and HNCO can produce peptide-bonded molecules in the solid state (cite: lig18). HNCO is a prolate asymmetric top molecule, and its rotational levels exhibit hyperfine splitting owing to the nuclear spin of nitrogen (cite: ni95; lap07). The dipole moment of HNCO is $\mu_{a}$ = 1.60 Debye and $\mu_{b}$ = 1.35 Debye (cite: ku71). The evidence of HNCO was first found towards Sgr B2 (cite: syn72; ch86; ku96). Additionally, evidence of HNCO has also been found towards hot cores and hot corinos (cite: bl87; van95; mac96; bis08; gor20; can21), galactic molecular clouds (cite: jak84; zin00), and translucent clouds (cite: tur99). Although there were many chemical modelling works to investigate the evolution of and HNCO, the formation pathways of both molecules remain unclear (cite: gor20).

The most chemically rich objects in the ISM are the hot molecular cores (hereafter HMCs) (cite: bis07; bel13; man22a; man22b; man23b). HMCs represent the early phases of high-mass star-forming regions. The typical masses of HMCs are $\geq$100 $\textup{M}_\odot$, which indicates that HMCs are reservoirs of several types of COMs, including precursors of NH$_{2}$CH$_{2}$COOH (cite: van98). Our current idea regarding high-mass star formation regions is incomplete due to a lack of a sufficient number of observations of this kind of source. Recent observational studies indicate the evolution of high-mass star-forming regions as follows: infrared dark clouds (IRDCs) $\rightarrow$ HMCs $\rightarrow$ hyper/ultra-compact H II regions $\rightarrow$ H II regions, which are surrounded by ionized high-mass stars (cite: beu07). The middle stages between the IRDCs and ultracompact HII regions are known as the HMCs. Owing to the lack of UV photons, the temperatures of the central protostars in the HMCs rise because of the increase in the temperatures of the dust and gaseous material. In ISM, HMCs have a high gas density ($n_{{H_{2}}}$$\geq$10$^{6}$ cm$^{-3}$), a warm temperature ($\geq$100 K), and a compact and small source size ($\leq$0.1 pc) (cite: van98; wi14). Previous molecular line surveys at millimeter and sub-millimeter wavelengths show that several types of COMs like CH$_{3}$OH, CH$_{3}$OCHO, CH$_{3}$OCH$_{3}$, CH$_{3}$CN, and C$_{2}$H$_{5}$CN are frequently found in different HMCs because of the high temperature and evaporation of H$_{2}$O and organic ice mantles ((cite: her09), and references therein).

![](continuum.pdf)

G358.93–0.03 (RA: 17$^{h}$43$^{m}$10$^{s}$.02, Dec: -29$^{\circ}$51$^{\prime}$45.8$^{\prime\prime}$) is the massive star-forming region that was located 6.75$\,{}\,^{\,+0.37}_{\,-0.68}$  kpc from Earth (cite: re14; bro19). There are eight sub-millimeter continuum sources in G3589.93–0.03, which have been designated from G3589.93–0.03 MM1 to G3589.93–0.03 MM8 in decreasing right ascension (R.A) (cite: bro19). The luminosity and mass of G358.93–0.03 are $\sim$7.7$\times$10$^{3}$ L$_{\odot}$ and 167$\pm$12M$_{\odot}$, respectively (cite: bro19). Two of the eight sources, G358.93–0.03 MM1 (hereafter MM1) and G358.93–0.03 MM3 (hereafter MM3), have been confirmed as having line-rich hot molecular cores (cite: bro19; bay22). Earlier, maser lines of , $^{13}$CH$_{3}$OH, HNCO, and HDO were detected towards MM1 using the ALMA, TMRT, and VLA radio telescopes (cite: bro19; chen20). Except for the maser lines, (cite: bro19) also detected the emission lines of from MM1 and MM3, but they do not estimate the abundance of this molecule. The emission lines of NH$_{2}$CN, the simplest sugar-like molecule CH$_{2}$OHCHO, and the antifreeze molecule (CH$_{2}$OH)$_{2}$, and possible NH$_{2}$CH$_{2}$COOH precursor molecule CH$_{3}$NH$_{2}$ were also detected towards MM1 using the ALMA bands 6 and 7 (cite: man23a; man23b; man24b; man24a). The detection of the above-mentioned molecules indicates that the MM1 is an ideal candidate for studying the emission lines of different types of complex biomolecules, including biologically relevant molecules. 

In this paper, we report the first detection of the emission lines of and HNCO towards the hot molecular core MM1 with the ALMA. The gas temperature and column density of and HNCO were estimated using the local thermodynamic equilibrium (LTE) model. We also address the probable formation pathways of and HNCO towards MM1. The observations and data analysis are shown in section [2](#obs). The results of the emission line detection of NH$_2$CHO and HNCO are shown in Section [3](#res). The discussion and conclusions are presented in Sections  [4](#dis) and [5](#conclu).

# Observation and data reductions

We used openly available raw data of the massive star-forming region G358.93–0.03, observed with the Atacama Large Millimeter/Submillimeter Array (ALMA) 12-m arrays with bands 6 and 7 (which span the frequency ranges of 290.51–306.01 GHz and 225.44–242.06 GHz) (PI: Crystal Brogan). The band 6 observation was performed in four spectral windows with frequency ranges of 225.44–226.38 GHz, 229.48–229.72 GHz, 240.26–241.20 GHz, and 241.12–242.06 GHz. Similarly, the band 7 observation was performed in four spectral windows with frequency ranges of 290.51–292.39 GHz, 292.49–294.37 GHz, 302.62–304.49 GHz, and 304.14–306.01 GHz. The ALMA bands 6 and 7 observations were conducted on April 16, 2019 and November 11, 2019, with on-source integration times of 3265.92 sec and 756.0 sec. The star-formation region G358.93–0.03’s phase centre was ($\alpha,\delta$)$_{\rm J2000}$ = 17:43:10.000, –29:51:46.000. To observe G358.93–0.03 in ALMA band 6, 45 antennas were set up with a minimum baseline of 15.1 m and a maximum baseline of 740.4 m. To observe G358.93–0.03 for ALMA band 7, 47 antennas were set up with a minimum baseline of 14 m and a maximum baseline of 2517 m. The bandpass and flux calibrators for bands 6 and 7 during the observations were J1924–2914 and J1550+0527, respectively, whereas the phase calibrator for bands 6 and 7 was J1744–3116.

We employed the Common Astronomy Software Application (CASA 5.4.1) with an ALMA data analysis pipeline for data reduction and imaging (cite: mc07). We utilized the Perley-Butler 2017 flux calibrator model with the `SETJY` task for flux calibration (cite: pal17). After flagging the bad antenna data, we subsequently constructed the flux and bandpass calibration using pipeline tasks HIFA_BANDPASSFLAG and HIFA_FLAGDATA. We separated the target data with all available rest frequencies using the CASA task MSTRANSFORM after gain calibration. Utilizing the CASA task TCLEAN with line-free channels, we constructed a continuum emission image of G358.93–0.03. The continuum emission image of G358.93–0.03 at a frequency of 303.39 GHz is shown in Figure [1](#fig:continuum). Utilizing these data, (cite: man23b) recently investigated in detail the dust continuum emissions from G358.93–0.03 (see Figure 1 in (cite: man23b)). In addition to eight sources, (cite: man23b) also discovered two additional sources associated with MM1 and MM2, which are referred to as MM1A and MM2A. Thus, in this study, we did not address the continuum emission characteristics of G358.93–0.03. Next, we employ the UVCONTSUB task to remove the continuum emission from the UV plane of the calibrated data. After that, to produce spectral data cubes of G358.93–0.03, we used the CASA task `TCLEAN` with the SPECMODE = CUBE parameter and Briggs weighting at a robust value of 0.5. Finally, we corrected the primary beam pattern in continuum images and spectral data cubes using the `IMPBCOR` task.

![](spectra.pdf)

# Result

## Molecular lines in G358.93–0.03

In the spectral data cubes of G358.93–0.03, we observed molecular line emissions from hot cores MM1 and MM3. We did not find any molecular line emissions from other sources in G358.93–0.03. The synthesized beam sizes of the spectral data cubes of G358.93–0.03 at ALMA band 6 were 0.55$^{\prime\prime}\times$0.45$^{\prime\prime}$, 0.53$^{\prime\prime}\times$0.46$^{\prime\prime}$, 0.52$^{\prime\prime}\times$0.42$^{\prime\prime}$, and 0.51$^{\prime\prime}\times$0.42$^{\prime\prime}$. Similarly, the synthesized beam sizes of the spectral data cubes at ALMA band 7 were 0.42$^{\prime\prime}\times$0.36$^{\prime\prime}$, 0.42$^{\prime\prime}\times$0.37$^{\prime\prime}$, 0.41$^{\prime\prime}\times$0.36$^{\prime\prime}$, and 0.41$^{\prime\prime}\times$0.35$^{\prime\prime}$, respectively. The molecular spectra were extracted by drawing a 0.90$^{\prime\prime}$ diameter circular region over the MM1 and MM3, which is greater than the line emitting regions of both hot cores. The pointing centre of MM1 is $\alpha$ (J2000) = 17$^{h}$43$^{m}$10$^{s}$.101, $\delta$ (J2000) = –29$^\circ$51$^{\prime}$45$^{\prime\prime}$.693. Similarly, the pointing centre of MM3 is $\alpha$ (J2000) = 17$^{h}$43$^{m}$10$^{s}$.0144, $\delta$ (J2000) = –29$^\circ$51$^{\prime}$46$^{\prime\prime}$.193. Recently, (cite: man23b) used this band 7 data, and they claimed that MM1 is more chemically rich than MM3. In the band 7 molecular spectra of MM1, (cite: man23b) noticed an inverse P-cygni profile in the emission lines of . That indicates MM1 is undergoing an infall. (cite: man23b) did not see any inverse P-cygni profile in the emission lines of towards MM3. The velocities of the spectra ($V_{LSR}$) of MM1 and MM3 are –16.5 km s$^{-1}$ and –18.2 km s$^{-1}$, respectively, (cite: man23b; man24a). From the chemically rich spectra, we focused only on studying the emission lines of COMs that contain peptide-like bonds, which are discussed in the following sections.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Frequency | Transition | $E_{u}$ | $A_{ij}$ | g$_{up}$ | $S\mu^{2}$ | FWHM | $\rm{\int T_{mb}dV}$ | Optical depth | Remarks |  |  |  |  |  |  |  |  |
|  | (GHz) | (${\rm J^{'}_{K_a^{'}K_c^{'}}}$–${\rm J^{''}_{K_a^{''}K_c^{''}}}$) | \(K\) | (s$^{-1}$) |  | (Debye$^{2}$) | (km s$^{-1}$) | (K km s$^{-1}$) | ($\tau$) |  |  |  |  |  |  |  |  |  |
| NH$_{2}$CHO | 225.679 | 22(2,20)–22(1,21) | 275.80 | 3.20$\times$10$^{-5}$ | 45 | 10.762 | 3.55$\pm$0.82 | 13.57$\pm$0.43 | 1.37$\times$10$^{-1}$ | Non blended |  |  |  |  |  |  |  |  |
|  | 303.451 | 15(1,15)–14(1,14) | 120.01 | 2.05$\times$10$^{-3}$ | 93 | 585.30 | 3.58$\pm$0.29 | 44.61$\pm$0.96 | 2.04$\times$10$^{-1}$ | Non blended |  |  |  |  |  |  |  |  |
|  | 303.661 | 14(1,13)–13(1,12) | 113.00 | 2.04$\times$10$^{-3}$ | 87 | 545.30 | 3.56$\pm$0.37 | 42.71$\pm$0.34 | 1.99$\times$10$^{-1}$ | Non blended |  |  |  |  |  |  |  |  |
|  | 304.882 | 14(2,12)–13(2,11) | 120.54 | 2.04$\times$10$^{-3}$ | 87 | 538.17 | 3.55$\pm$0.44 | 27.44$\pm$0.52 | 1.88$\times$10$^{-1}$ | Non blended |  |  |  |  |  |  |  |  |
| HNCO | 240.875 | 11(1,11)–10(1,10) | 112.64 | 1.90$\times$10$^{-4}$ | 23 | 26.922 | 3.55$\pm$0.62 | 20.56$\pm$0.82 | 1.98$\times$10$^{-1}$ | Non blended |  |  |  |  |  |  |  |  |
|  |   241.498$^{*}$ | 11(4,7)-10(4,6) | 720.30 | 1.40$\times$10$^{-4}$ | 23 | 19.679 | – | – | 1.04$\times$10$^{-2}$ | Blended with CHDCO |  |  |  |  |  |  |  |  |
|  |   241.619$^{*}$ | 11(3,8)–10(3,7) | 444.56 | 1.63$\times$10$^{-4}$ | 23 | 22.877 | 3.58$\pm$0.59 | 18.45$\pm$0.34 | 8.55$\times$10$^{-2}$ | Non blended |  |  |  |  |  |  |  |  |
|  |   241.703$^{*}$ | 11(2,10)–10(2,9) | 239.89 | 1.81$\times$10$^{-4}$ | 23 | 25.357 | 3.49$\pm$0.21 | 15.28$\pm$0.22 | 2.27$\times$10$^{-1}$ | Non blended |  |  |  |  |  |  |  |  |
|  |   241.708$^{*}$ | 11(2,9)–10(2,8) | 239.89 | 1.81$\times$10$^{-4}$ | 23 | 25.356 | 3.48$\pm$0.35 | 20.67$\pm$0.61 | 2.37$\times$10$^{-1}$ | Non blended |  |  |  |  |  |  |  |  |
|  | 241.774 | 11(0,11)–10(0,10) | 69.62 | 1.96$\times$10$^{-4}$ | 23 | 27.458 | 3.52$\pm$0.69 | 29.54$\pm$0.87 | 5.69$\times$10$^{-1}$ | Non blended |  |  |  |  |  |  |  |  |
|  | 304.166 | 25(1,25)-26(0,26) | 384.78 | 1.50$\times$10$^{-4}$ | 51 | 23.34 | 3.55$\pm$0.92 | 15.81$\pm$0.21 | 1.13$\times$10$^{-1}$ | Non blended |  |  |  |  |  |  |  |  |

\
\*–There are two transitions less than 100 kHz. We showed only the first transition.

## Rotational emission lines NH$_{2}$CHO towards MM1

We employed the local thermodynamic equilibrium (LTE) model with the Cologne Database for Molecular Spectroscopy (CDMS) and Jet Population Laboratory (JPL) molecular databases to find the rotational emission lines of NH$_{2}$CHO from the chemically rich molecular spectra of MM1 (cite: mu05; pic88). For fitting the LTE spectral model over the observed emission lines of , we employed the Markov Chain Monte Carlo (MCMC)[^1] algorithm in the CASSIS software package (cite: vas15). The gas density of the inner region of MM1 is 2$\times$10$^{7}$ cm$^{-3}$, indicating that the LTE assumptions are true for this source (cite: ste21). Through analysing the molecular spectra using the LTE model, we have detected four rotational emission lines of the complex N- and O-bearing molecule NH$_{2}$CHO towards MM1. The upper state energies of the detected emission lines of NH$_{2}$CHO varied between 113 K and 275.80 K. After detecting the emission lines of NH$_{2}$CHO, we obtained the molecular transitions, upper state energy ($E_u$) in K, Einstein coefficients ($A_{ij}$) in s$^{-1}$, line intensity ($S\mu^{2}$) in Debye$^{2}$, full-width half maximum (FWHM) in km s$^{-1}$, optical depth ($\tau$), and integrated intensities ($\rm{\int T_{mb}dV}$) in K km s$^{-1}$. The LTE fitting spectral lines of NH$_{2}$CHO are shown in Figure [2](#fig:line) and the corresponding spectral parameters are listed in Table [\[tab:MOLECULAR DATA\]](#tab:MOLECULAR DATA). Except for NH$_{2}$CHO, we also fitted the rest of the 250 molecular transitions, which were taken from CDMS and JPL molecular databases, across the observed spectra of MM1 to better understand the blending effect. After spectral analysis, we noticed that all detected lines of NH$_{2}$CHO are non-blended, and all transition lines exhibit $\geq$4 $\sigma$ statistical significance. The best-fit column density of NH$_{2}$CHO is (2.80$\pm$0.29)$\times$10$^{15}$ cm$^{-2}$ with an excitation temperature of 165$\pm$21 K, which was estimated based on LTE modelling. The estimated excitation temperature of NH$_{2}$CHO suggests this molecule originates from the warm inner region of MM1 because the gas temperature of the warm inner region of the hot molecular cores is above 100 K (cite: van98; wi14). The abundance of NH$_{2}$CHO towards MM1 with respect to molecular H$_{2}$ is (9.03$\pm$1.44)$\times$10$^{-10}$, where the column density of molecular H$_{2}$ towards MM1 is (3.10$\pm$0.2)$\times$10$^{24}$ cm$^{-2}$ (cite: man23b).

![](emission.pdf)

## Rotational emission lines of HNCO towards MM1

Using the LTE-modelled spectra, we detected seven rotational emission lines of HNCO towards MM1 using the ALMA bands 6 and 7. The upper-state energies ($E_{u}$) of the identified rotational emission lines of HNCO vary between 69.62 K and 720.30 K. After spectral analysis, we noticed that the emission line of HNCO at a frequency of 241.498 GHz (J = 11(4,7)–10(4,6)) is blended with CHDCO. All other detected transitions are non-blended. The non-blended emission lines of HNCO exhibited $\geq$4.5 $\sigma$ statistical significance. The resultant LTE-fitted spectral line and spectra line parameters of HNCO are shown in Figure [2](#fig:line) and Table [\[tab:MOLECULAR DATA\]](#tab:MOLECULAR DATA). The best-fit column density of HNCO is (1.80$\pm$0.42)$\times$10$^{16}$ cm$^{-2}$ with an excitation temperature of 170$\pm$32 K, which was estimated based on LTE modelling. The abundance of HNCO with respect to molecular H$_{2}$ towards the MM1 is (5.80$\pm$2.09)$\times$10$^{-9}$, where the column density of molecular H$_{2}$ towards the MM1 is (3.10$\pm$0.2)$\times$10$^{24}$ cm$^{-2}$ (cite: man23b).

## Searching the emission lines of NH$_{2}$CHO and HNCO towards MM3

After the detection of the rotational emission lines of NH$_{2}$CHO and HNCO towards MM1, we used the LTE-modelled spectra to search for these molecules towards MM3. However, we were unable to find the emission lines of those molecules towards MM3. As per the LTE analysis, the upper limit column densities of NH$_{2}$CHO and HNCO towards MM3 are $\leq$(2.05$\pm$0.85)$\times$10$^{13}$ cm$^{-2}$ and $\leq$(8.12$\pm$1.26)$\times$10$^{14}$ cm$^{-2}$, respectively. The upper limit of the abundances of NH$_{2}$CHO and HNCO towards MM3 are $\leq$(5.84$\pm$1.26)$\times$10$^{-11}$ and $\leq$(2.31$\pm$1.27)$\times$10$^{-9}$, where the column density of molecular H$_{2}$ towards the MM3 is (3.51$\pm$0.7)$\times$10$^{23}$ cm$^{-2}$ (cite: man23b).

## Spatial distribution of NH$_{2}$CHO and HNCO towards MM1

After detection of the emission lines of NH$_{2}$CHO and HNCO towards MM1, we produced the integrated emission maps of the non-blended emission lines of those molecules by integrating the spectral data cubes using the channel ranges with the help of CASA task `IMMOMENTS`. The emission maps of NH$_{2}$CHO and HNCO towards MM1 are presented in Figure [3](#fig:emissionmap). The emission maps of NH$_{2}$CHO and HNCO are overlaid with a 988 $\mu$m continuum emission image of G358.93–0.03. The dust continuum image of G358.93–0.03 is taken from (cite: man23b). From the integrated emission maps, we observed that NH$_{2}$CHO and HNCO arose from the warm-inner regions of MM1. Since the excitation temperature of and HNCO towards MM1 is 165$\pm$21 K and 170$\pm$32 K, which indicates both molecules may exist in the same region of MM1. So, there is a high chance of a chemical link between and HNCO towards MM1. We estimate the size of the emitting regions of NH$_{2}$CHO and HNCO by fitting the 2D Gaussians over the emission maps of NH$_{2}$CHO and HNCO using the `IMFIT` task. The sizes of the emitting regions of NH$_{2}$CHO and HNCO corresponding to the non-blended transition lines are shown in Table [1](#tab:emittingregion). We observed that the emitting regions of NH$_{2}$CHO and HNCO are similar or marginally larger than the beam sizes of the emission maps. This suggests that the emission maps of NH$_{2}$CHO and HNCO are not spatially resolved towards MM1. Therefore, we could not determine the chemical morphologies of NH$_{2}$CHO and HNCO from the integrated emission maps. Higher spatial and angular resolution observations are needed to learn the spatial distribution of NH$_{2}$CHO and HNCO towards MM1. 

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Frequency | Transition | E$_{up}$ | Emitting region |  |  |  |  |  |  |  |
|  | GHz | (${\rm J^{'}_{K_a^{'}K_c^{'}}}$–${\rm J^{''}_{K_a^{''}K_c^{''}}}$) | \(K\) | ($^{\prime\prime}$) |  |  |  |  |  |  |  |
| NH$_{2}$CHO | 225.679 | 22(2,20)–22(1,21) | 275.80 | 0.42 |  |  |  |  |  |  |  |
|  | 303.451 | 15(1,15)–14(1,14) | 120.01 | 0.43 |  |  |  |  |  |  |  |
|  | 303.661 | 14(1,13)–13(1,12) | 113.00 | 0.42 |  |  |  |  |  |  |  |
|  | 304.882 | 14(2,12)–13(2,11) | 120.54 | 0.43 |  |  |  |  |  |  |  |
| HNCO | 240.875 | 11(1,11)–10(1,10) | 112.64 | 0.42 |  |  |  |  |  |  |  |
|  |   241.619$^{*}$ | 11(3,8)–10(3,7) | 444.56 | 0.42 |  |  |  |  |  |  |  |
|  |   241.703$^{*}$ | 11(2,10)–10(2,9) | 239.89 | 0.43 |  |  |  |  |  |  |  |
|  |   241.708$^{*}$ | 11(2,9)–10(2,8) | 239.89 | 0.43 |  |  |  |  |  |  |  |
|  | 241.774 | 11(0,11)–10(0,10) | 69.62 | 0.43 |  |  |  |  |  |  |  |
|  | 304.166 | 25(1,25)–26(0,26) | 384.78 | 0.44 |  |  |  |  |  |  |  |

: Emitting regions of NH$_{2}$CHO and HNCO towards the MM1.

\*–There are two transitions within less than 100 kHz. We show only the first transition.\

## Searching of other peptide bonds molecules towards MM1

After the detection of the rotational emission lines of NH$_{2}$CHO and HNCO towards MM1, we also search the rotational emission lines of other COMs that have peptide bonds, such as HOCH$_{2}$C(O)NH$_{2}$, CH$_{3}$NCO, CH$_{3}$NHCHO, NH$_{2}$C(O)CN, CH$_{3}$CH$_{2}$NCO, CH$_{3}$C(O)NH$_{2}$, and NH$_{2}$C(O)NH$_{2}$ using the LTE modelled spectra. During the spectral analysis, we observed that all the above-mentioned molecules are blended with other molecular transitions. So, there is a very low chance of identifying these molecules. The upper-limit column densities of peptide bond molecules HOCH$_{2}$C(O)NH$_{2}$, CH$_{3}$NCO, CH$_{3}$NHCHO, NH$_{2}$C(O)CN, CH$_{3}$CH$_{2}$NCO, CH$_{3}$C(O)NH$_{2}$, and NH$_{2}$C(O)NH$_{2}$ are $\leq$3.56$\times$10$^{14}$ cm$^{-2}$, $\leq$8.26$\times$10$^{14}$ cm$^{-2}$, $\leq$5.20$\times$10$^{13}$ cm$^{-2}$, $\leq$2.96$\times$10$^{13}$ cm$^{-2}$, $\leq$9.62$\times$10$^{13}$ cm$^{-2}$, $\leq$1.16$\times$10$^{14}$ cm$^{-2}$, and $\leq$9.28$\times$10$^{12}$ cm$^{-2}$, respectively.

# Discussion

## Comparison of the abundances of and HNCO towards MM1 and other sources

To understand the distribution of NH$_{2}$CHO and HNCO in the ISM, we compare the fractional abundance of those molecules towards MM1 and other hot molecular cores such as G10.47+0.03, G31.41+0.31, Orion KL, Sgr B2, and hot corino object IRAS 16293–2422 B. This comparison is presented in Table [\[tab:comparision\]](#tab:comparision). After comparison, we noticed that the fractional abundance of NH$_{2}$CHO towards MM1 is nearly similar to Sgr B2 and IRAS 16293–2422 B. The fractional abundance of NH$_{2}$CHO towards MM1 is one order of magnitude lower than the G31.41+0.31, G10.47+0.03, and Orion KL. Similarly, the fractional abundance of HNCO towards MM1 is similar to that of Orion KL and Sgr B2. The fractional abundance of HNCO is one order of magnitude lower than that of G10.47+0.03 and G31.41+0.31. Furthermore, we notice that the fractional abundance of HNCO towards MM1 is two orders of magnitude larger than that of IRAS 16293–2422 B. Based on that comparison, we identify that G31.41+0.31 and G10.47+0.03 are the most abundant NH$_{2}$CHO and HNCO sources in the ISM. The low abundances of NH$_{2}$CHO and HNCO towards MM1 indicate that the detection probabilities of other peptide bond COMs are very low in these sources.

| Molecule | MM1$^{a}$ | G10.47+0.03$^{b}$ | G31.41+0.31$^{c}$ | Orion KL$^{d}$ | Sgr B2$^{e}$ | IRAS 16293–2422 B$^{f}$ |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| NH$_{2}$CHO | (9.03$\pm$1.44)$\times$10$^{-10}$ | 2.87$\times$10$^{-9}$ | (5.4$\pm$1.5)$\times$10$^{-9}$ | 5.80$\times$10$^{-9}$ | 1.3$\times$10$^{-10}$ | 1.05$\times$10$^{-10}$ |  |  |  |  |  |  |  |  |  |  |
| HNCO | (5.80$\pm$2.09)$\times$10$^{-9}$ | 1.02$\times$10$^{-8}$ | (1.1$\pm$0.3)$\times$10$^{-8}$ | 4.08$\times$10$^{-9}$ | 7.20$\times$10$^{-9}$ | (1.8$\pm$0.4)$\times$10$^{-11}$ |  |  |  |  |  |  |  |  |  |  |

\
Notes: a: Our work, b: (cite: gor20), c: (cite: col21), d: (cite: ka13), (cite: ter10), e: (cite: hal11), (cite: ad10), f: (cite: ka13), (cite: he19)\

## Possible formation mechanism of NH$_{2}$CHO and HNCO towards MM1

The formation mechanism(s) of NH$_{2}$CHO in ISM is still debatable in the astrochemistry community. We observed that only a few reactions have been proposed to understand the formation pathways of NH$_{2}$CHO in both the grain surface and the gas phase. Previously, (cite: qu07) claimed that the NH$_{2}$CHO created via the ion-molecule reaction and subsequent electron recombination reaction between NH$_{4}$$^{+}$ and H$_{2}$CO:\
\
NH$_{4}$$^{+}$ + H$_{2}$CO$\longrightarrow$ NH$_{3}$CHO$^{+}$ + H$_{2}$             (1)\
\
NH$_{3}$CHO$^{+}$ + e$^{-}$$\longrightarrow$NH$_{2}$CHO + H               (2)\
\
Subsequently, (cite: gar08) claimed that the rates of reactions 1 and 2 are unknown. In particular, (cite: gar08) proposed the following radical-neutral reaction in the gas phase:\
\
H$_{2}$CO + NH$_{2}$$\longrightarrow$ NH$_{2}$CHO + H                  (3)\
\
However, (cite: red14) showed that the net activation barrier energy of this reaction is above 1000 K. Earlier, (cite: gar13) and (cite: gor20) showed that reaction 3 is responsible for the formation of towards hot molecular cores and hot corions. Previously (cite: cou16) showed that was formed via the reaction between and (reaction 3) in the gas phase towards the hot corino IRAS 16293–2422 B. Similarly, reaction 3 is also responsible for the formation of in the shock region L1157–B1, hot cores Sgr B2 (N), G10.47+0.03, Orion KL, G31.41+0.31, and the high-mass protostar IRAS 18089–1732 (cite: hal11; ka13; cod17; gor20; col21; man24).

Previous studies have proposed that the emission lines of HNCO originate from the high-density warm-inner regions of hot cores and hot corinos. Therefore, HNCO may play an important role as a tracer for dense gases in hot molecular cores (cite: jak84). Previously, (cite: ig77) claimed that the HNCO produced in the gas phase via the ion-neutral reaction towards Sgr B2:\
\
NCO$^{+}$ + H$_{2}$ $\longrightarrow$ HNCO$^{+}$ + H                  (4)\
\
HNCO$^{+}$ + H$_{2}$ $\longrightarrow$ HNCOH$^{+}$ + H            (5)\
\
HNCOH$^{+}$ + e$^{-}$ $\longrightarrow$ HNCO + H              (6)\
\
Previously, (cite: tur00) suggested another neutral-neutral reaction to create HNCO:\
\
CN + O$_{2}$ $\longrightarrow$ NCO + O                           (7)\
\
NCO + H$_{2}$ $\longrightarrow$ HNCO + H                     (8)\
\
Reaction 8 has an activation barrier. Previously, (cite: gar08) showed that the HNCO also formed on the grain surface via the thermal reaction:\
\
NH + CO $\longrightarrow$ HNCO                             (9)\
\
(cite: gar08) claimed that reaction 9 has no activation barrier and that the molecule is released in the gas phase via desorption. Earlier, (cite: gar13) and (cite: gor20) show that reaction 9 is the most efficient reaction for the formation of HNCO towards the hot molecular cores.

Previously, (cite: gor20) computed a three-phase (gas + grain + ice mantle) warm-up chemical model to understand the possible formation mechanisms of NH$_{2}$CHO and HNCO. During chemical modelling, they assumed the free-fall collapse of a cloud (Phase I), which was followed by the warm-up phase. In phase I, the density of the gas rapidly increased from 10$^{3}$ cm$^{-3}$ to 1$\times$10$^{7}$ cm$^{-3}$ and the dust temperature was constant at 10 K. In phase II (the warm-up stage), the dust temperature was increased from 10 K to 400 K, and the density of the gas was constant at 1$\times$10$^{7}$ cm$^{-3}$. At this stage, the gas and dust in the hot core were well coupled. During chemical modelling, (cite: gor20) used the radical-neutral reaction between H$_{2}$CO and NH$_{2}$ (reaction 3) and the reaction between NH and CO (reaction 9) for the formation of NH$_{2}$CHO and HNCO in the gas phase and grain surface, respectively. Previously, (cite: gar13) also showed that reactions 3 and 9 are the most efficient for the formation of NH$_{2}$CHO and HNCO in the gas phase and grain surface towards hot molecular cores. In the warm-up stage, (cite: gor20) estimated the modelled abundances of NH$_{2}$CHO and HNCO towards hot molecular cores to be 8.27$\times$10$^{-10}$ and 4.8$\times$10$^{-9}$, respectively.

To understand the possible formation mechanism of NH$_{2}$CHO and HNCO towards MM1, we compared our derived abundance of NH$_{2}$CHO and HNCO with the modelled abundance of (cite: gor20). This comparison is reasonable because the gas density and temperature of this source are 2$\times$10$^{7}$ cm$^{-3}$ and 150 K, respectively (cite: chen20; ste21). Therefore, the three-phase warm-up chemical model of (cite: gor20) is efficient for understanding the formation pathways of NH$_{2}$CHO and HNCO towards the MM1. (cite: gor20) derived the modelled abundance of NH$_{2}$CHO and HNCO to be 8.27$\times$10$^{-10}$ and 4.8$\times$10$^{-9}$, respectively. The observed fractional abundances of NH$_{2}$CHO and HNCO towards MM1 are (9.03$\pm$1.44)$\times$10$^{-10}$ and (5.80$\pm$2.09)$\times$10$^{-9}$, which are nearly similar to the modelled abundance results in (cite: gor20). This result indicates that NH$_{2}$CHO is produced by the reaction of NH$_{2}$ and H$_{2}$CO in the gas phase towards MM1. Similarly, HNCO is created by the reaction of NH and CO on the surface of the grains of the MM1.

## Chemical link between NH$_{2}$CHO and HNCO

Several studies have shown that NH$_{2}$CHO and HNCO are chemically connected. Earlier, (cite: gar08), (cite: hau19), and (cite: gor20) claimed that the subsequently hydrogenation of HNCO creates NH$_{2}$CHO in the grain surface:\
\
HNCO + H $\longrightarrow$ NH$_{2}$CO                  (10)\
\
NH$_{2}$CO + H $\longrightarrow$ NH$_{2}$CHO              (11)\
\
In another way, (cite: lo15) demonstrated the molecular correlation between the abundance of HNCO and NH$_{2}$CHO towards the high-mass star-formation regions. From the molecular correlation plot, (cite: lo15) found a positive correlation between the abundances of and HNCO, and they found a correlation equation $X$(NH$_{2}$CHO) = 0.04$X$(HNCO)$^{0.93}$ (see Figures 2 and 3 in (cite: lo15)). According to the molecular correlation equation of (cite: lo15), we found that the abundance of NH$_{2}$CHO is (8.75$\pm$1.98)$\times$10$^{-10}$, which is very similar to our observed abundance of NH$_{2}$CHO towards MM1. This result indicates that HNCO and NH$_{2}$CHO are chemically connected towards MM1.

# Conclusion

In this article, we present the identification of the emission lines of HNCO and NH$_{2}$CHO towards hot core MM1 using the ALMA bands 6 and 7. The conclusions of this study are summarised below:\
\
1. We successfully detected four and six non-blended rotational transition lines of peptide bond molecules NH$_{2}$CHO and HNCO towards the hot core MM1.\
\
2. The estimated column densities of NH$_{2}$CHO and HNCO towards the MM1 are (2.80$\pm$0.29)$\times$10$^{15}$ cm$^{-2}$ and (1.80$\pm$0.42)$\times$10$^{16}$ cm$^{-2}$ with excitation temperatures of 165$\pm$21 K and 170$\pm$32 K, respectively. The fractional abundances of NH$_{2}$CHO and HNCO towards the MM1 are (9.03$\pm$1.44)$\times$10$^{-10}$ and (5.80$\pm$2.09)$\times$10$^{-9}$.\
\
3. We compared the estimated abundances of NH$_{2}$CHO and HNCO with the existing three-phase warm-up chemical model abundances and noticed that the observed and modelled abundances are very close.\
\
4. We claim that NH$_{2}$CHO is produced by the reaction of NH$_{2}$ and H$_{2}$CO in the gas phase towards MM1. Similarly, HNCO is created by the reaction of NH and CO on the grain surface of MM1.\
\
5. We also discuss the chemical links between and HNCO. According to the correlation equation of (cite: lo15), both and HNCO are chemically linked towards the MM1. The presence of and HNCO indicates that other O- and N-bearing molecules exist in this source, which we discuss in follow-up studies.

# acknowledgments

We thank the anonymous referee for the helpful comments that improved the manuscript. A.M. acknowledges the SVMCM for financial support for this research. This paper makes use of the following ALMA data: ADS /JAO.ALMA#2019.1.00768.S and ADS /JAO.ALMA#2018.A.00031.T. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in co-operation with the Republic of Chile. The joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

# Conflicts of interest

The authors declare no conflict of interest.

natexlab

(ref: ad13) Adande, G. R., Woolf, N. J., & Ziurys, L. M. 2013, Astrobiol., 13, 439

(ref: ad10) Adande, G. R., Halfen, D. T., Ziurys, L. M., Quan, D., Herbst, E. 2010, ApJ, 725, 561

(ref: bis07) Bisschop, S. E., Jørgensen, J. K., van Dishoeck, E. F. et al. 2007, A&A, 465, 913

(ref: bel13) Belloche, A., Müller, H. S. P., Menten, K. M. et al. 2013, A&A, 559, A47

(ref: beu07) Beuther, H., Churchwell, E. B., McKee, C. F., Tan, J. C., 2007, in Reipurth B., Jewitt D., Keil K.eds, Protostars and Planets V. University of Arizona Press, Tucson, AZ, p. 165

(ref: bis07) Bisschop, S. E., Jørgensen, J. K., van Dishoeck, E. F., & de Wachter, E. B. M. 2007, A&A, 465, 913

(ref: bis08) Bisschop, S. E., Jørgensen, J. K., Bourke, T. L., Bottinelli, S., & van Dishoeck, E. F. 2008, A&A, 488, 959

(ref: bro19) Brogan, C. L., Hunter, T. R., Towner, A. P. M., et al. 2019, ApJL, 881, L39

(ref: bay22) Bayandina, O.S., Brogan, C.L., Burns, R.A., et al. 2022, AJ, 163(2), p.83

(ref: bro00) Bockelée-Morvan, D., Lis, D. C., Wink, J. E., et al. 2000, A&A, 353, 1101

(ref: biv14) Biver, N., Bockelée-Morvan, D., Debout, V., et al. 2014, A&A, 566, L5

(ref: col21) Colzi, L., Rivilla, V. M., Beltrán, M. T., et al., 2021, A&A, 653, A129

(ref: cod17) Codella, C., Ceccarelli, C., Caselli, P., et al. 2017, A&A, 605, L3

(ref: chen20) Chen, X., Sobolev, A. M., Ren, Z.-Y., et al. 2020, NatAs, 4, 1170

(ref: ch86) Churchwell, E., Wood, D., Myers, P. C., & Myers, R. V. 1986, ApJ, 305, 405

(ref: cou16) Coutens, A., Jørgensen, J. K., van der Wiel, M. H. D., et al., 2016, A&A, 590, L6

(ref: bl87) Blake, G. A., Sutton, E. C., Masson, C. R., & Phillips, T. G. 1987, ApJ, 315, 621

(ref: can21) Canelo, C. M., Bronfman, L., Mendoza, E., et al., 2021, MNRAS, 504, 4428

(ref: fed20) Fedoseev G., Ioppolo S., Zhao D., Lamberts T., Linnartz H., 2015, MNRAS, 446, 439

(ref: go15) Goesmann, F., Rosenbauer, H., Bredehöft, J. H., et al. 2015, Science, 349, 020689

(ref: gor20) Gorai P., Bhat B., Sil M., Mondal S. K. Ghosh R., Chakrabarti S. K., Das A., 2020, ApJ, 895, 86

(ref: gar08) Garrod R. T., Weaver S. L. W., Herbst E., 2008, ApJ, 682, 283

(ref: gar13) Garrod, R. T. 2013, ApJ, 765, 60

(ref: her09) Herbst E., & van Dishoeck E. F., 2009, ARA&A, 47, 427

(ref: hal11) Halfen, D. T., Ilyushin, V., Ziurys, L. M. 2011, ApJ, 743, 60

(ref: hau19) Haupa, K. A., Tarczay, G., & Lee, Y.-P. 2019, JAChS, 141, 11614

(ref: he19) Hernández-Gómez, A., Sahnoun, E., Caux, E., et al., 2019, MNRAS, 483, 2014

(ref: ig77) Iglesias E., 1977, ApJ, 218, 697

(ref: jak84) Jackson, J. M., Armstrong, J. T., & Barrett, A. H. 1984, ApJ, 280, 608

(ref: kur57) Kurland, R. J., & Wilson, E. B., 1957, J. Chem. Phys. 27, 585

(ref: ka13) Kahane, C., Ceccarelli, C., Faure, A., & Caux, E. 2013, ApJ, 763, L38

(ref: ku71) Kukolich, S. G., Nelson, A. C., Yamanashi, B. S., 1971, J. Am. Chem. Soc, 93(25), 6769-6771

(ref: ku96) Kuan, Y., & Snyder, L. E. 1996, ApJ, 470, 981

(ref: lo15) López-Sepulcre, A., Jaber, A. A., Mendoza, E., et al. 2015, MNRAS, 449, 2438

(ref: lap07) Lapinov A. V., Golubiatnikov G. Y., Markov V. N., Guarnieri A., 2007, Astron. Lett., 33, 121

(ref: lig18) Ligterink N. F. W., Terwisscha van Scheltinga J., Taquet V., Jørgensen J. K., Cazaux S., van Dishoeck E. F., Linnartz H., 2018, MNRAS, 480, 3628

(ref: men14) Mendoza, E., Lefloch, B., López-Sepulcre, A., et al. 2014, MNRAS, 445, 151 353, 1101

(ref: mu13) Muller, S., Beelen, A., Black, J. H., et al. 2013, A&A, 551, A109

(ref: mac96) MacDonald, G. H., Gibb, A. G., Habing, R. J., & Millar, T. J. 1996, A&AS, 119, 333

(ref: man22a) Manna, A., Pal, S., 2022a, Life Sciences in Space Research, 34, 9

(ref: man22b) Manna, A., Pal, S., 2022b, Journal of Astrophysics and Astronomy, 43, 83

(ref: man23a) Manna, A., & Pal, S., 2023, Astrophys Space Sci, 368, 33

(ref: man23b) Manna, A., Pal, S., Viti, S., Sinha, S., 2023, MNRAS, 525, 2229-2240

(ref: man24) Manna, A., Pal, S., Baug, T., Mondal, S., 2024, Res. Astron. Astrophys, 24, 065008

(ref: man24b) Manna, A., Pal, S., Viti, S., 2024, submitted in MNRAS

(ref: man24a) Manna, A., & Pal, S., 2024, New Astronomy, 109, 102199

(ref: mc07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., Golap, K. 2007. CASA Architecture and Applications. Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mu05) Müller, H. S. P., SchlM$\ddot{o}$der, F., Stutzki, J. Winnewisser, G., 2005, [Journal of Molecular Structure](https://ui.adsabs.harvard.edu/abs/2005JMoSt.742..215M/abstract), 742, 215

(ref: ni95) Niedenhoff M., Yamada K. M. T., Belov S. P., Winnewisser G., 1995, Journal of Molecular Spectroscopy, 174, 151

(ref: pal17) Perley, R. A., Butler, B. J. 2017, ApJ, 230, 1538

(ref: pic88) Pickett, H. M., Poynte, R. L., Cohen, E. A., et al. 1998, Journal of Quantitative Spectroscopy and Radiative Transfer, 60, 883

(ref: qu07) Quan D., Herbst E., 2007, A&A, 474, 521

(ref: ru71) Rubin R. H., Swenson G. W., Jr, Benson R. C., Tigelaar H. L., Flygare W. H., 1971, ApJ, 169, L39

(ref: re14) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2014, ApJ, 783, 130

(ref: red14) Redondo P., Barrientos C., Largo A., 2014, ApJ, 780, 181

(ref: sal12) Saladino, R., Crestini, C., Pino, S., Costanzo, G., & Di Mauro, E. 2012, Physics of Life Reviews, 9, 84

(ref: syn72) Snyder, L. E., & Buhl, D. 1972, ApJ, 177, 619

(ref: ste21) Stecklum, B., Wolf, V., Linz, H., et al., 2021. A&A, 646, p.A161

(ref: tur99) Turner, B. E., Terzieva, R., & Herbst, E. 1999, ApJ, 518, 699

(ref: tur00) Turner B. E., 2000, ApJ, 542, 837

(ref: ter10) Tercero, B., Cernicharo, J., Pardo, J. R., Goicoechea, J. R. 2010, A&A, 517, A96

(ref: van98) van Dishoeck E. F. & Blake G. A., 1998, Annu Rev Astron Astrophys, 36, 317

(ref: van95) van Dishoeck, E. F., Blake, G. A., Jansen, D. J., & Groesbeck, T. D. 1995, ApJ, 447, 760

(ref: vas15) Vastel, C., Bottinelli, S., Caux, E., Glorian, J. -M., Boiziot, M., 2015, CASSIS: a tool to visualize and analyse instrumental and synthetic spectra. Proceedings of the Annual meeting of the French Society of Astronomy and Astrophysics, 313-316

(ref: wi14) Williams D. A., Viti S., 2014, Observational Molecular Astronomy: Exploring the Universe Using Molecular Line Emissions. Cambridge Univ. Press, Cambridge

(ref: yam12) Yamaguchi, T., Takano, S., Watanabe, Y., et al. 2012, PASJ, 64, 105

(ref: zin00) Zinchenko, I., Henkel, C., & Mao, R. Q. 2000, A&A, 361, 1079

[^1]: <https://cassis.irap.omp.eu/docs/CassisScriptingDoc/computation/mcmc_method.html#mcmc-method>

</paper>

Write the methods card for this paper.