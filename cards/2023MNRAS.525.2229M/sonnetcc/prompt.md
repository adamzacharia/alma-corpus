# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.525.2229M\sonnetcc\reply.txt

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
 "bibcode": "2023MNRAS.525.2229M",
 "title": "Identification of the simplest sugar-like molecule glycolaldehyde towards the hot molecular core G358.93-0.03 MM1",
 "year": 2023,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Manna, Arijit",
 "n_authors": 4,
 "arxiv_id": "2308.14454",
 "doi": "10.1093/mnras/stad2185",
 "alma_projects_linked_by_archive": [
  "2019.1.00768.S"
 ]
}
```

Paper text:
<paper>
# Identification of the simplest sugar-like molecule glycolaldehyde towards the hot molecular core G358.93–0.03 MM1

## Abstract

Glycolaldehyde () is the simplest monosaccharide sugar in the interstellar medium, and it is directly involved in the origin of life via the “RNA world” hypothesis. We present the first detection of glycolaldehyde () towards the hot molecular core G358.93–0.03 MM1 using the Atacama Large Millimeter/Submillimeter Array (ALMA). The calculated column density of towards G358.93–0.03 MM1 is (1.52$\pm$0.9)$\times$10$^{16}$ cm$^{-2}$ with an excitation temperature of 300$\pm$68.5 K. The derived fractional abundance of with respect to is (4.90$\pm$2.92)$\times$10$^{-9}$, which is consistent with that estimated by existing two-phase warm-up chemical models. We discuss the possible formation pathways of within the context of hot molecular cores and hot corinos and find that is likely formed via the reactions of radical HCO and radical on the grain surface of G358.93–0.03 MM1.

ISM: individual objects (G358.93–0.03 MM1) – ISM: abundances – ISM: kinematics and dynamics – stars: formation – astrochemistry

# Introduction

In the interstellar medium (ISM), glycolaldehyde () is known as one of the simplest aldehyde sugar, and it is the only sugar detected in space (cite: hal04). The monosaccharide sugar molecule is an isomer of both methyl formate () and acetic acid () (cite: bel09; min20). is one of the important interstellar organic molecule in the ISM because when reacts with propenal (), it forms ribose () (cite: bel09). Ribose () is known as the central constituent of RNA, and it is directly involved in the hypothesis of the origin of life in the universe. The organic molecule also has a major role in the formation of three, four, and five-carbon sugars (cite: hal06). The molecular lines of were first detected towards Sgr B2 (N) (cite: hal00; hal01; hal04; hal06; bel13; xu19) and subsequently towards the hot molecular core G31.41+0.31 (cite: bel09; cal14; riv17; min20), the solar-like protostar IRAS 16293–2422 B (cite: jo12; riv19), the class 0 protostar NGC 7129 FIRS 2 (cite: flu14), and the hot corino NGC 1333 IRAS2A (cite: cou15). Recently, emission lines of were also tentatively detected from the hot molecular core G10.47+0.03 (cite: mondal21).

![](cont.pdf)

The chemistry of hot cores is characterized by the sublimation of ice mantles, which accumulate during the star formation process (cite: shi21). In prestellar cores and cold molecular clouds, the atoms and gaseous molecules freeze onto the dust grains. During the process of star-formation, the thermal energy and pressure increase due to the gravitational collapse. Therefore, dust temperatures also increase, and chemical interactions between heavy species become active on the grain surfaces (cite: gar06; shi21). This leads to the formation of large complex organic molecules (cite: gar06; shi21). In addition, sublimated molecules such as ammonia () and methanol () are also subject to further gas-phase reactions (cite: nom04; taq16; shi21). Consequently, the warm and dense gas surrounding the protostars becomes chemically rich, resulting in the formation of one of the strongest and most powerful molecular line emitters known as hot molecular cores (cite: shi21). Hot molecular cores are ideal targets for astrochemical studies because a variety of simple and complex organic molecules are frequently found towards these objects (cite: her09). They are one of the earliest stages of star formation and play an important role in increasing the chemical complexity of the ISM (cite: shi21). Hot molecular cores are small, compact objects ($\leq$0.1 pc) with a warm temperature ($\geq$100 K) and high gas density ($n_{\ce{H2}}$$\geq$10$^{6}$ cm$^{-3}$) that promote molecular evolution by thermal hopping on dust grains (cite: van98; wi14). The lifetime of hot molecular cores is thought to be approximately 10$^{5}$ years (medium warm-up phase) to 10$^{6}$ years (slow warm-up phase) (cite: van98; vi04; gar06; gar08; gar13).

The hot molecular core candidate G358.93–0.03 MM1 is located in the high-mass star-formation region G358.93–0.03 at a distance of 6.75$\,{}\,^{\,+0.37}_{\,-0.68}$ kpc (cite: re14; bro19). The total gas mass of G358.93–0.03 is 167$\pm$12M$_{\odot}$ and its luminosity is $\sim$7.7$\times$10$^{3}$L$_{\odot}$ (cite: bro19). The high-mass star-formation region G358.93–0.03 contains eight sub-millimeter continuum sources, which are designated as G358.93–0.03 MM1 to G358.93–0.03 MM8 in order of decreasing right ascension (cite: bro19). G358.93–0.03 MM1 is the brightest sub-millimeter continuum source that hosts a line-rich hot molecular core (cite: bro19; bay22). Previously, maser lines of deuterated water (HDO), isocyanic acid (HNCO), and methanol () were detected towards G358.93–0.03 MM1 using the ALMA, TMRT, and VLA radio telescopes (cite: bro19; chen20). The rotational emission lines of methyl cyanide () with transition J = 11(4)–10(4) were also detected from both G358.93–0.03 MM1 and G358.93–0.03 MM3 using the ALMA (cite: bro19). The excitation temperature of towards the G358.93–0.03 MM1 and G358.93–0.03 MM3 is 172$\pm$3 K (cite: bro19). The systematic velocities of G358.93–0.03 MM1 and G358.93–0.03 MM3 are –16.5$\pm$0.3 km s$^{-1}$ and –18.6$\pm$0.2 km s$^{-1}$, respectively (cite: bro19). Recently, rotational emission lines of the possible urea precursor molecule cyanamide () were also detected towards G358.93–0.03 MM1 using the ALMA (cite: man23).

In this article, we present the first detection of the simplest sugar-like molecule towards the hot molecular core G358.93–0.03 MM1 using the Atacama Large Millimeter/Submillimeter Array (ALMA). ALMA data and their reductions are presented in Section [2](#obs). The line identification and the determination of the physical properties of the gas are presented in Section [3](#res). A discussion on the origin of in this hot molecular core and conclusions are shown in Section [4](#dis) and [5](#conclu), respectively.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | R.A. | Decl. | Deconvolved source size | Integrated flux | Peak flux | RMS | Remark |  |  |  |  |  |  |  |  |  |
|  |  |  | ($^{\prime\prime}$$\times$$^{\prime\prime}$) | (mJy) | (mJy beam$^{-1}$) | ($\mu$Jy) |  |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM1 | 17:43:10.1015 | –29:51:45.7057 | 0.116$\times$0.085 | 72.80$\pm$2.20 | 34.81$\pm$0.75 | 68.5 | Resolved |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM1A | 17:43:10.0671 | –29:51:46.4511 | 0.469$\times$0.411 | 67.71$\pm$2.60 | 3.53$\pm$0.13 | 21.1 | Resolved |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM2 | 17:43:10.0357 | –29:51:44.9019 | 0.231$\times$0.088 | 14.20$\pm$1.40 |   4.47$\pm$0.35 | 35.5 | Resolved |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM2A | 17:43:10.0209 | –29:51:45.1577 | – | 2.30$\pm$0.58 | 1.52$\pm$0.18 | 20.3 | Not resolved |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM3 | 17:43:10.0145 | –29:51:46.1933 | 0.072$\times$0.019 |   6.12$\pm$0.32 |   5.10$\pm$0.16 | 18.6 | Resolved |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM4 | 17:43:09.9738 | –29:51:46.0707 | 0.160$\times$0.087 | 10.50$\pm$2.42 |   4.38$\pm$0.32 | 49.8 | Resolved |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM5 | 17:43:09.9063 | –29.51.46.4814 | 0.245$\times$0.078 |   7.80$\pm$1.10 |   2.50$\pm$0.48 | 30.4 | Resolved |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM6 | 17:43:09.8962 | –29:51:45.9802 | 0.107$\times$0.062 | 3.28$\pm$0.21 |   1.98$\pm$0.08 |  7.9 | Resolved |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM7 | 17:43:09.8365 | –29:51:45.9498 | 0.216$\times$0.116 | 13.91$\pm$1.82 |   3.85$\pm$0.39 | 38.5 | Resolved |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM8 | 17:43:09.6761 | –29:51:45.4688 | – |   6.50$\pm$0.11 |   4.582$\pm$0.06 |  6.4 | Not resolved |  |  |  |  |  |  |  |  |  |

# Observations and data reduction

The high-mass star-forming region G358.93–0.03 was observed using the ALMA band 7 receivers (PI: Crystal Brogan). The observation of G358.93–0.03 was performed on October 11, 2019, with a phase center of ($\alpha,\delta$)$_{\rm J2000}$ = (17:43:10.000, –29:51:46.000) and an on-source integration time of 756.0 sec. During the observations, a total of 47 antennas were used, with a minimum baseline of 14 m and a maximum baseline of 2517 m. J1550+0527 was used as the flux calibrator and bandpass calibrator, and J1744–3116 was used as the phase calibrator. The observed frequency ranges of G358.93–0.03 were 290.51–292.39 GHz, 292.49–294.37 GHz, 302.62–304.49 GHz, and 304.14–306.01 GHz, with a spectral resolution of 977 kHz (0.963 km s$^{-1}$).

We used the Common Astronomy Software Application (`CASA 5.4.1`) for data reduction and imaging using the ALMA data reduction pipeline (cite: mc07). We used the Perley-Butler 2017 flux calibrator model for flux calibration using the task `SETJY` (cite: pal17). After the initial data reduction using the CASA pipeline, we utilized task `MSTRANSFORM` to separate the target data G358.93–0.03 with all the available rest frequencies. The continuum image is created by selecting line-free channels. Before creating the spectral images, the continuum emission is subtracted from the spectral data using the `UVCONTSUB` task. To create the spectral images of G358.93–0.03, we used Briggs weighting (cite: bri95) and a robust value of 0.5. We used the CASA task `IMPBCOR` to correct the synthesized beam pattern in continuum and spectral images.

# Results

## Continuum emission

### Sub-millimeter wavelength continuum emission towards G358.93–0.03

The continuum emission of G358.93–0.03 is observed at 303.39 GHz (988 $\mu$m), as shown in Figure [1](#fig:cont). The synthesized beam size is 0.412$^{\prime\prime}$$\times$0.363$^{\prime\prime}$. In the continuum emission image, we observe eight sub-millimeter continuum sources, G358.93–0.03 MM1 to G358.93–0.03 MM8. Among the eight sources, G358.93–0.03 MM1 and G358.93–0.03 MM3 are known as hot molecular cores (cite: bro19). Additionally, we also detected two other continuum sources associated with G358.93–0.03 MM1 and G358.93–0.03 MM2. We define these two continuum sources as G358.93–0.03 MM1A and G358.93–0.03 MM2A. We individually fit the 2D Gaussian for each source in G358.93–0.03 using the CASA task `IMFIT` and estimate the integrated flux density, peak flux density, deconvolved source size, and RMS, which are shown in Table [\[tab:cont\]](#tab:cont). Except for G358.93–0.03 MM2A and G358.93–0.03 MM8, we see that the continuum emissions of other sources are resolved. (cite: bro19) also detected the sub-millimeter wavelength continuum emission from the eight individual continuum sources (G358.93–0.03 MM1 to G358.93–0.03 MM8) of G358.93–0.03 at frequencies of 195.58 GHz, 233.75 GHz, and 337.26 GHz.

![](fullspectra.pdf)

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | $N_{\ce{H2}}$ | $T_{mb}$ | $\tau$ |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | (cm$^{-2}$) | \(K\) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM1 | (3.10$\pm$0.2)$\times$10$^{24}$ | 4.10 | 27.72$\times$10$^{-3}$ |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM1A | (1.21$\pm$0.8)$\times$10$^{24}$ | 0.41 | 13.71$\times$10$^{-3}$ |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM2 | (1.53$\pm$0.7)$\times$10$^{24}$ | 0.52 | 17.66$\times$10$^{-3}$ |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM2A | (5.22$\pm$0.2)$\times$10$^{23}$ | 0.17 |   5.93$\times$10$^{-3}$ |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM3 | (3.51$\pm$0.7)$\times$10$^{23}$ | 0.60 |   4.01$\times$10$^{-3}$ |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM4 | (1.50$\pm$0.3)$\times$10$^{24}$ | 0.51 | 17.29$\times$10$^{-3}$ |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM5 | (8.59$\pm$0.5)$\times$10$^{23}$ | 0.29 |   9.84$\times$10$^{-3}$ |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM6 | (6.80$\pm$0.6)$\times$10$^{23}$ | 0.23 |   7.70$\times$10$^{-3}$ |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM7 | (1.32$\pm$0.5)$\times$10$^{24}$ | 0.45 | 15.06$\times$10$^{-3}$ |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM8 | (1.57$\pm$0.8)$\times$10$^{24}$ | 0.54 | 18.13$\times$10$^{-3}$ |  |  |  |  |  |  |  |  |  |  |  |  |  |

: Column densities of molecular and optical depths towards the continuum sources in G358.93–0.03.

### Estimation of molecular hydrogen () column density and optical depth ($\tau$) towards G358.93–0.03

Here we focus on estimating the molecular hydrogen column densities from all continuum sources in G358.93–0.03. The peak flux density ($S_\nu$) of the optically thin dust continuum emission can be expressed as $$\begin{equation}
S_\nu = B_\nu(T_d)\tau_\nu\Omega_{beam}
\end{equation}$$ where the Planck function at dust temperature ($T_d$) is represented by $B_\nu(T_d)$ (cite: whi92), $\tau_\nu$ is the optical depth, and $\Omega_{beam} = (\pi/4 \ln 2)\times \theta_{major} \times \theta_{minor}$ is the solid angle of the synthesized beam. The expression for the optical depth in terms of the mass density of dust can be written as, $$\begin{equation}
\tau_\nu =\rho_d\kappa_\nu L
\end{equation}$$ where $\rho_d$ is the mass density of the dust, $\kappa_{\nu}$ is the mass absorption coefficient, and $L$ the path length. The mass density of the dust can be expressed in terms of the dust-to-gas mass ratio ($Z$), $$\begin{equation}
\rho_d = Z\mu_H\rho_{H_2}=Z\mu_HN_{H_2}2m_H/L
\end{equation}$$ where $\mu_H$ is the mean atomic mass per hydrogen, $\rho_{H_2}$ is the hydrogen mass density, $m_H$ indicates the mass of hydrogen, and $N_{H_2}$ is the column density of hydrogen. For the dust temperature, $T_d$, we adopt 150 K, as derived by (cite: chen20) for the two hot cores, G358.93–0.03 MM1 and G358.93–0.03 MM3. For the rest of the cores, we adopt a dust temperature of 30.1 K as estimated by (cite: ste21). We also take $\mu_H = 1.41$ and $Z = 0.01$ (cite: cox00). The peak flux density of all the continuum sources in G358.93–0.03 at frequency 303.39 GHz is listed in Table [\[tab:cont\]](#tab:cont). From equations 1, 2, and 3, the column density of molecular hydrogen can be expressed as,

$$\begin{equation}
N_{H_2} = \frac{S_\nu /\Omega}{2\kappa_\nu B_\nu(T_d)Z\mu_H m_H}
\end{equation}$$ For the estimation of the mass absorption coefficient ($\kappa_{\nu}$), we use the formula $\kappa_\nu = 0.90(\nu /230 ~\textrm{GHz})^{\beta}$  cm$^{2}$ g$^{-1}$ (cite: moto19), where $k_{230} = 0.90$ cm$^{2}$ g$^{-1}$ indicates the emissivity of the dust grains at a gas density of $\rm{10^{6}\ cm^{-3}}$. We use the dust spectral index $\beta$ $\sim$ 1.7 (cite: bro19). From equation 4, we find the column densities of molecular hydrogen ($N_{\ce{H2}}$) towards all observed continuum sources in G358.93–0.03, which we report in Table [1](#tab:hydrogen).

We also determine the value of the dust optical depth ($\tau_\nu$) using the following equation,

$$\begin{equation}
T_{mb} = T_{d}(1-exp(-\tau_\nu))
\end{equation}$$ where $T_{mb}$ represents the brightness temperature and $T_{d}$ is the dust temperature. For an estimation of the brightness temperature ($T_{mb}$), we use the Rayleigh-Jeans approximation, 1 Jy beam$^{-1} \equiv$ 118 K. Using equation 5, we estimate the dust optical depth towards all observed continuum sources in G358.93–0.03 (listed in Table [1](#tab:hydrogen)). We find that the optical depth of all observed continuum sources is less than 1, indicating that all observed continuum sources in G358.93–0.03 are optically thin at the frequency of 303.39 GHz.

![](spectra1.pdf)

![](spectra2.pdf)

![](spectra3.pdf)

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Observed frequency | Transition | $E_{u}$ | $A_{ij}$ | $G_{up}$ | FWHM | Optical depth | $I_p$$^{\dagger}$ | $\rm{\int T_{mb}dV}$ | Remark |  |  |  |  |  |  |  |
| (GHz) | (${\rm J^{'}_{K_a^{'}K_c^{'}}}$–${\rm J^{''}_{K_a^{''}K_c^{''}}}$) | \(K\) | (s$^{-1}$) |  | (km s$^{-1}$) | ($\tau$) | \(K\) | (K.km s$^{-1}$) |  |  |  |  |  |  |  |  |
|   290.589$^{*}$ | 18(12,6)–18(11,7) | 182.3 | 2.59$\times$10$^{-4}$ | 37 | 3.2$\pm$0.2 | 1.2$\times$10$^{-2}$ | 4.1 | 11.9$\pm$1.2 | Non blended |  |  |  |  |  |  |  |
| 290.726 | 15(5,10)–14(4,11) |   82.3 | 2.23$\times$10$^{-4}$ | 31 | – | 1.3$\times$10$^{-2}$ | 3.6 | – | Blended with DCOOH |  |  |  |  |  |  |  |
|   290.760$^{*}$ | 17(12,6)–17(11,7) | 172.3 | 2.39$\times$10$^{-4}$ | 35 | – | 1.0$\times$10$^{-2}$ | 4.8 | – | Blended with $^{13}$CHO |  |  |  |  |  |  |  |
| 290.824 | 25(11,15)–24(11,14) | 254.2 | 7.78$\times$10$^{-6}$ | 51 | – | 3.9$\times$10$^{-4}$ | 5.7 | – | Blended with |  |  |  |  |  |  |  |
| 290.824 | 25(11,14)–24(11,13) | 254.2 | 7.78$\times$10$^{-6}$ | 51 | – | 3.9$\times$10$^{-4}$ | 5.7 | – | Blended with |  |  |  |  |  |  |  |
| 290.850 | 26(4,22)–25(5,21) | 210.9 | 3.16$\times$10$^{-4}$ | 53 | – | 1.9$\times$10$^{-2}$ | 3.7 | – | Blended with |  |  |  |  |  |  |  |
| 290.853 | 33(1,32)–33(0,33) | 288.5 | 6.82$\times$10$^{-5}$ | 67 | – | 4.0$\times$10$^{-3}$ | 2.5 | – | Blended with |  |  |  |  |  |  |  |
| 290.853 | 33(2,32)–33(1,33) | 288.5 | 6.82$\times$10$^{-5}$ | 67 | – | 4.0$\times$10$^{-3}$ | 2.5 | – | Blended with |  |  |  |  |  |  |  |
|   290.902$^{*}$ | 16(12,4)–16(11,5) | 162.9 | 2.16$\times$10$^{-4}$ | 33 | – | 9.7$\times$10$^{-3}$ | 4.9 | – | Blended with |  |  |  |  |  |  |  |
| 290.929 | 48(9,40)–48(8,41) | 710.5 | 3.81$\times$10$^{-4}$ | 97 | – | 8.0$\times$10$^{-3}$ | 1.8 | – | Blended with |  |  |  |  |  |  |  |
| 290.933 | 44(13,32)–44(12,33) | 656.0 | 4.49$\times$10$^{-4}$ | 89 | – | 8.2$\times$10$^{-3}$ | 2.8 | – | Blended with |  |  |  |  |  |  |  |
|   291.019$^{*}$ | 15(12,4)–15(11,5) | 154.0 | 1.89$\times$10$^{-4}$ | 31 | – | 8.1$\times$10$^{-3}$ | 3.5 | – | Blended with |  |  |  |  |  |  |  |
| 291.094 | 27(2,25)–26(3,24) | 207.9 | 5.47$\times$10$^{-4}$ | 55 | 3.3$\pm$0.3 | 3.4$\times$10$^{-2}$ | 5.0 | 14.3$\pm$2.3 | Non blended |  |  |  |  |  |  |  |
|   291.114$^{*}$ | 14(12,2)–14(11,3) | 145.7 | 1.55$\times$10$^{-4}$ | 29 | – | 6.5$\times$10$^{-3}$ | 12.0 | – | Blended with $^{18}$OH |  |  |  |  |  |  |  |
| 291.173 | 27(3,25)–26(2,24) | 207.9 | 5.47$\times$10$^{-4}$ | 55 | – | 3.5$\times$10$^{-2}$ | 5.7 | – | Blended with |  |  |  |  |  |  |  |
|   291.189$^{*}$ | 13(12,2)–13(11,3) | 137.9 | 1.15$\times$10$^{-4}$ | 27 | – | 4.5$\times$10$^{-3}$ | 4.5 | – | Blended with |  |  |  |  |  |  |  |
|   291.248$^{*}$ | 12(12,0)–12(11,1) | 130.7 | 6.40$\times$10$^{-5}$ | 25 | – | 2.5$\times$10$^{-3}$ | 2.3 | – | Blended with HC$^{18}$O |  |  |  |  |  |  |  |
| 291.571 | 43(13,30)–43(12,31) | 631.1 | 4.47$\times$10$^{-4}$ | 87 | – | 1.1$\times$10$^{-2}$ | 2.4 | – | Blended with $^{13}$ |  |  |  |  |  |  |  |
| 291.624 | 11(7,5)–10(6,4) |   66.4 | 4.49$\times$10$^{-4}$ | 23 | – | 2.0$\times$10$^{-2}$ | 8.9 | – | Blended with |  |  |  |  |  |  |  |
| 291.626 | 11(7,4)–10(6,5) |   66.4 | 4.49$\times$10$^{-4}$ | 23 | – | 2.0$\times$10$^{-2}$ | 8.9 | – | Blended with |  |  |  |  |  |  |  |
| 291.784 | 28(1,27)–27(2,26) | 211.4 | 6.46$\times$10$^{-4}$ | 57 | 3.4$\pm$0.1 | 4.2$\times$10$^{-2}$ | 8.1 | 27.9$\pm$4.8 | Non blended |  |  |  |  |  |  |  |
| 291.784 | 28(2,27)–27(2,26) | 211.4 | 9.58$\times$10$^{-6}$ | 57 | 3.4$\pm$0.1 | 4.2$\times$10$^{-2}$ | 8.1 | 27.9$\pm$4.8 | Non blended |  |  |  |  |  |  |  |
| 291.784 | 28(1,27)–27(1,26) | 211.4 | 9.58$\times$10$^{-6}$ | 57 | 3.4$\pm$0.1 | 4.2$\times$10$^{-2}$ | 8.1 | 27.9$\pm$4.8 | Non blended |  |  |  |  |  |  |  |
| 291.786 | 28(2,27)–27(1,26) | 211.4 | 6.46$\times$10$^{-4}$ | 57 | 3.4$\pm$0.1 | 4.2$\times$10$^{-2}$ | 8.1 | 27.9$\pm$4.9 | Non blended |  |  |  |  |  |  |  |
| 291.920 | 26(4,23)–25(3,22) | 203.1 | 4.41$\times$10$^{-4}$ | 53 | – | 2.8$\times$10$^{-2}$ | 4.7 | – | Blended with $^{13}$ |  |  |  |  |  |  |  |
| 291.937 | 47(11,37)–46(12,34) | 708.1 | 8.68$\times$10$^{-5}$ | 95 | – | 1.8$\times$10$^{-3}$ | 4.8 | – | Blended with |  |  |  |  |  |  |  |
| 292.101 | 58(11,47)–58(10,48) | 1050.4 | 4.50$\times$10$^{-4}$ | 117 | – | 3.7$\times$10$^{-3}$ | 1.5 | – | Blended with |  |  |  |  |  |  |  |
| 292.205 | 19(5,15)–18(4,14) | 121.5 | 2.13$\times$10$^{-4}$ | 39 | – | 1.2$\times$10$^{-2}$ | 4.2 | – | Blended with E- |  |  |  |  |  |  |  |
| 292.314 | 41(5,36)–41(4,37) | 498.2 | 2.79$\times$10$^{-4}$ | 83 | – | 1.1$\times$10$^{-2}$ | 7.5 | – | Blended with |  |  |  |  |  |  |  |
| 292.536 | 29(0,29)–28(1,28) | 213.6 | 7.37$\times$10$^{-4}$ | 59 | 3.3$\pm$0.2 | 5.0$\times$10$^{-3}$ | 5.3 | 15.4$\pm$3.5 | Non blended |  |  |  |  |  |  |  |
| 292.536 | 29(1,29)–28(1,28) | 213.6 | 9.77$\times$10$^{-6}$ | 59 | 3.3$\pm$0.2 | 5.0$\times$10$^{-3}$ | 5.3 | 15.4$\pm$3.5 | Non blended |  |  |  |  |  |  |  |
| 292.536 | 29(0,29)–28(0,28) | 213.6 | 9.77$\times$10$^{-6}$ | 59 | 3.3$\pm$0.2 | 5.0$\times$10$^{-3}$ | 5.3 | 15.4$\pm$3.5 | Non blended |  |  |  |  |  |  |  |
| 292.536 | 29(1,29)–28(0,28) | 213.6 | 7.37$\times$10$^{-4}$ | 59 | 3.3$\pm$0.2 | 5.0$\times$10$^{-3}$ | 5.3 | 15.4$\pm$3.5 | Non blended |  |  |  |  |  |  |  |
| 292.737 | 35(2,33)–35(1,34) | 336.7 | 1.31$\times$10$^{-4}$ | 71 | 3.2$\pm$0.5 | 7.0$\times$10$^{-3}$ | 1.3 | 3.5$\pm$0.1 | Non blended |  |  |  |  |  |  |  |
| 292.737 | 35(3,33)–35(2,34) | 336.7 | 1.31$\times$10$^{-4}$ | 71 | 3.2$\pm$0.6 | 7.0$\times$10$^{-3}$ | 1.3 | 3.5$\pm$0.1 | Non blended |  |  |  |  |  |  |  |
| 292.924 | 15(4,11)–14(3,12) |   77.6 | 1.09$\times$10$^{-4}$ | 31 | – | 6.1$\times$10$^{-3}$ | 1.4 | – | Blended with |  |  |  |  |  |  |  |
| 293.257 | 43(13,31)–43(12,32) | 631.1 | 4.54$\times$10$^{-4}$ | 87 | – | 1.1$\times$10$^{-2}$ | 1.5 | – | Blended with |  |  |  |  |  |  |  |
| 293.617 | 39(4,35)–39(3,36) | 441.7 | 2.37$\times$10$^{-4}$ | 79 | – | 9.8$\times$10$^{-3}$ | 1.0 | – | Blended with $^{13}$ |  |  |  |  |  |  |  |
| 293.634 | 39(5,35)–39(4,36) | 441.7 | 2.37$\times$10$^{-4}$ | 79 | – | 9.8$\times$10$^{-3}$ | 2.5 | – | Blended with |  |  |  |  |  |  |  |
| 293.698 | 37(3,34)–37(2,35) | 387.8 | 1.88$\times$10$^{-4}$ | 75 | – | 8.9$\times$10$^{-3}$ | 5.0 | – | Blended with |  |  |  |  |  |  |  |
| 293.701 | 37(4,34)–37(3,35) | 387.8 | 1.88$\times$10$^{-4}$ | 75 | – | 8.9$\times$10$^{-3}$ | 5.0 | – | Blended with |  |  |  |  |  |  |  |
| 293.932 | 20(5,16)–19(4,15) | 132.8 | 2.21$\times$10$^{-4}$ | 41 | – | 1.3$\times$10$^{-2}$ | 5.6 | – | Blended with $^{13}$CN |  |  |  |  |  |  |  |
| 293.951 | 9(8,2)–8(7,3) |   63.8 | 6.30$\times$10$^{-4}$ | 19 | – | 2.2$\times$10$^{-2}$ | 5.7 | – | Blended with $^{13}$ |  |  |  |  |  |  |  |
| 293.951 | 9(8,1)–8(7,2) |   63.8 | 6.30$\times$10$^{-4}$ | 19 | – | 2.2$\times$10$^{-2}$ | 5.7 | – | Blended with $^{13}$ |  |  |  |  |  |  |  |
| 302.698 | 52(14,39)–52(13,40) | 890.6 | 5.30$\times$10$^{-4}$ | 105 | – | 6.1$\times$10$^{-3}$ | 6.5 | – | Blended with |  |  |  |  |  |  |  |
| 302.761 | 48(12,36)–47(13,35) | 748.6 | 1.07$\times$10$^{-4}$ | 97 | – | 1.8$\times$10$^{-3}$ | 6.3 | – | Blended with HC$^{18}$O |  |  |  |  |  |  |  |
| 302.797 | 38(13,25)–38(12,36) | 515.7 | 4.70$\times$10$^{-4}$ | 77 | – | 1.3$\times$10$^{-2}$ | 5.3 | – | Blended with |  |  |  |  |  |  |  |
| 302.895 | 66(13,53)–66(12,54) | 1362.2 | 5.32$\times$10$^{-4}$ | 133 | – | 1.6$\times$10$^{-3}$ | 4.0 | – | Blended with $^{13}$CHO |  |  |  |  |  |  |  |
| 302.911 | 38(13,26)–38(12,27) | 515.7 | 4.71$\times$10$^{-4}$ | 77 | – | 1.2$\times$10$^{-2}$ | 15.3 | – | Blended with |  |  |  |  |  |  |  |
| 302.933 | 38(3,35)–38(2,36) | 407.5 | 2.09$\times$10$^{-4}$ | 77 | – | 8.5$\times$10$^{-3}$ | 3.5 | – | Blended with H$^{13}$CCCN |  |  |  |  |  |  |  |
| 302.934 | 38(4,35)–38(3,36) | 407.5 | 2.09$\times$10$^{-4}$ | 77 | – | 8.5$\times$10$^{-3}$ | 3.5 | – | Blended with H$^{13}$CCCN |  |  |  |  |  |  |  |
| 302.962 | 40(4,36)–40(3,37) | 462.7 | 2.54$\times$10$^{-4}$ | 81 | – | 9.5$\times$10$^{-3}$ | 2.2 | – | Blended with CH$^{13}$CN |  |  |  |  |  |  |  |
| 302.971 | 40(5,36)–40(4,37) | 462.7 | 2.54$\times$10$^{-4}$ | 81 | – | 9.5$\times$10$^{-3}$ | 1.5 | – | Blended with HCOOD |  |  |  |  |  |  |  |
| 303.089 | 12(7,6)–11(6,5) |   73.0 | 4.68$\times$10$^{-4}$ | 25 | – | 2.1$\times$10$^{-2}$ | 7.2 | – | Blended with $^{+}$ |  |  |  |  |  |  |  |
| 303.094 | 12(7,5)–11(6,6) |   73.0 | 4.68$\times$10$^{-4}$ | 25 | – | 2.0$\times$10$^{-2}$ | 6.8 | – | Blended with c-HCOOH |  |  |  |  |  |  |  |
| 303.846 | 27(4,23)–26(5,22) | 225.9 | 3.86$\times$10$^{-4}$ | 55 | – | 2.1$\times$10$^{-2}$ | 5.2 | – | Blended with D$^{13}$CCCN |  |  |  |  |  |  |  |
| 304.347 | 37(13,24)–37(12,25) | 494.4 | 4.71$\times$10$^{-4}$ | 75 | – | 1.4$\times$10$^{-2}$ | 3.3 | – | Blended with |  |  |  |  |  |  |  |
| 304.409 | 37(13,25)–37(12,26) | 494.4 | 4.71$\times$10$^{-4}$ | 75 | – | 1.4$\times$10$^{-2}$ | 5.3 | – | Blended with NCHCCO |  |  |  |  |  |  |  |
| 304.509 | 26(9,18)–25(9,16) | 245.0 | 9.75$\times$10$^{-6}$ | 53 | – | 4.8$\times$10$^{-4}$ | 0.5 | – | Blended with $^{13}$ |  |  |  |  |  |  |  |
| 304.574 | 26(9,17)–25(9,16) | 245.0 | 9.76$\times$10$^{-6}$ | 53 | – | 4.8$\times$10$^{-4}$ | 0.3 | – | Blended with C$^{15}$N |  |  |  |  |  |  |  |
| 304.609 | 61(14,48)–61(13,49) | 1182.5 | 5.58$\times$10$^{-4}$ | 123 | – | 2.8$\times$10$^{-3}$ | 0.8 | – | Blended with |  |  |  |  |  |  |  |
| 304.612 | 61(17,45)–60(18,42) | 1232.1 | 1.07$\times$10$^{-4}$ | 123 | – | 4.6$\times$10$^{-4}$ | 0.8 | – | Blended with |  |  |  |  |  |  |  |
| 304.895 | 25(6,19)–24(6,18) | 206.1 | 1.05$\times$10$^{-5}$ | 51 | – | 5.7$\times$10$^{-4}$ | 0.9 | – | Blended with H$^{13}$CCN |  |  |  |  |  |  |  |
| 304.930 | 33(7,26)–32(8,25) | 350.1 | 1.50$\times$10$^{-4}$ | 67 | – | 6.6$\times$10$^{-3}$ | 4.9 | – | Blended with |  |  |  |  |  |  |  |
| 304.954 | 39(9,30)–38(10,29) | 491.1 | 1.17$\times$10$^{-4}$ | 79 | – | 3.8$\times$10$^{-3}$ | 1.8 | – | Blended with |  |  |  |  |  |  |  |
| 305.040 | 47(7,40)–47(6,41) | 670.3 | 3.90$\times$10$^{-4}$ | 95 | 3.4$\pm$0.6 | 6.1$\times$10$^{-3}$ | 1.6 | 5.806$\pm$1.87 | Non blended |  |  |  |  |  |  |  |
| 305.106 | 52(10,43)–52(9,44) | 836.5 | 4.59$\times$10$^{-4}$ | 105 | – | 3.1$\times$10$^{-3}$ | 0.7 | – | Blended with |  |  |  |  |  |  |  |
| 305.113 | 26(6,21)–25(6,20) | 218.9 | 1.05$\times$10$^{-5}$ | 53 | – | 2.6$\times$10$^{-4}$ | 3.0 | – | Blended with |  |  |  |  |  |  |  |

\

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Observed frequency | Transition | $E_{u}$ | $A_{ij}$ | $G_{up}$ | FWHM | Optical depth | $I_p$$^{\dagger}$ | $\rm{\int T_{mb}dV}$ | Remark |  |  |  |  |  |  |  |
| (GHz) | (${\rm J^{'}_{K_a^{'}K_c^{'}}}$–${\rm J^{''}_{K_a^{''}K_c^{''}}}$) | \(K\) | (s$^{-1}$) |  | (km s$^{-1}$) | ($\tau$) | \(K\) | (K km s$^{-1}$) |  |  |  |  |  |  |  |  |
| 305.203 | 51(14,38)–51(13,39) | 861.2 | 5.38$\times$10$^{-4}$ | 103 | – | 3.1$\times$10$^{-3}$ | 3.2 | – | Blended with |  |  |  |  |  |  |  |
| 305.483 | 16(5,11)–15(4,12) |   91.4 | 2.29$\times$10$^{-4}$ | 33 | – | 5.4$\times$10$^{-3}$ | 3.9 | – | Blended with |  |  |  |  |  |  |  |
| 305.488$^{*}$ | 10(8,3)–9(7,2) |   69.4 | 6.41$\times$10$^{-4}$ | 21 | 3.4$\pm$0.5 | 1.1$\times$10$^{-2}$ | 6.2 | 24.2$\pm$2.6 | Non blended |  |  |  |  |  |  |  |
| 305.669 | 57(15,42)–57(14,43) | 1062.5 | 5.56$\times$10$^{-4}$ | 115 | – | 1.9$\times$10$^{-3}$ | 1.4 | – | Blended with |  |  |  |  |  |  |  |
| 305.700 | 47(8,40)–47(7,41) | 670.3 | 3.93$\times$10$^{-4}$ | 95 | – | 4.1$\times$10$^{-3}$ | 15.6 | – | Blended with |  |  |  |  |  |  |  |
| 305.740 | 36(13,23)–36(12,24) | 473.6 | 4.71$\times$10$^{-4}$ | 73 | – | 7.0$\times$10$^{-3}$ | 3.5 | – | Blended with |  |  |  |  |  |  |  |
| 305.773 | 36(13,24)–36(12,25) | 473.6 | 4.71$\times$10$^{-4}$ | 73 | – | 7.0$\times$10$^{-3}$ | 2.5 | – | Blended with $^{18}$OH |  |  |  |  |  |  |  |

\*– There are two transitions that have close frequencies ($\leq  100$ kHz), and only the frequency of the first transition is shown.\
$\dagger$–$I_p$ is the peak intensity of the emission lines of .

## Line emission from G358.93–0.03

From the spectral images of G358.93–0.03, we see that only the spectra of G358.93–0.03 MM1 and G358.93–0.03 MM3 show any line emission. The synthesized beam sizes of the spectral images of G358.93–0.03 at frequency ranges of 290.51–292.39 GHz, 292.49–294.37 GHz, 302.62–304.49 GHz, and 304.14–306.01 GHz are 0.425$^{\prime\prime}\times$0.369$^{\prime\prime}$, 0.427$^{\prime\prime}\times$0.376$^{\prime\prime}$, 0.413$^{\prime\prime}\times$0.364$^{\prime\prime}$, and 0.410$^{\prime\prime}\times$0.358$^{\prime\prime}$, respectively. We extract the molecular spectra from G358.93–0.03 MM1 and G358.93–0.03 MM3 by drawing a 0.912$^{\prime\prime}$ diameter circular region, which is larger than the line emitting regions of G358.93–0.03 MM1 and G358.93–0.03 MM3. The phase centre of G358.93–0.03 MM1 is RA (J2000) = 17$^{h}$43$^{m}$10$^{s}$.101, Dec (J2000) = –29$^\circ$51$^{\prime}$45$^{\prime\prime}$.693. The phase centre of G358.93–0.03 MM3 is RA (J2000) = 17$^{h}$43$^{m}$10$^{s}$.0144, Dec (J2000) = –29$^\circ$51$^{\prime}$46$^{\prime\prime}$.193. The resultant spectra of G358.93–0.03 MM1 and G358.93–0.03 MM3 are shown in Figure [2](#fig:fullspectra). From the spectra, it can be seen that G358.93–0.03 MM1 is more chemically rich than G358.93–0.03 MM3. Additionally, we also observe the signature of an inverse P-Cygni profile associated with the emission lines towards G358.93–0.03 MM1. This may indicate that the hot molecular core G358.93–0.03 MM1 is undergoing infall. We do not observe any evidence of an inverse P-Cygni profile in the spectra of G358.93–0.03 MM3. The systematic velocities ($V_{LSR}$) of G358.93–0.03 MM1 and G358.93–0.03 MM3 are –16.5 km s$^{-1}$ and –18.2 km s$^{-1}$, respectively, (cite: bro19).

### Identification of towards G358.93–0.03 MM1

To identify the rotational emission lines of , we assume local thermodynamic equilibrium (LTE) and use the Cologne Database for Molecular Spectroscopy (CDMS) (cite: mu05). For LTE modelling, we use CASSIS (cite: vas15). The LTE assumption is valid in the inner region of G358.93–0.03 MM1 because the gas density of the warm inner region of the hot core is 2$\times$10$^{7}$ cm$^{-3}$ (cite: ste21). To fit the LTE model spectra of over the observed molecular spectra, we use the Markov Chain Monte Carlo (MCMC) algorithm in CASSIS. Previously, (cite: gor20) discussed the fitting of the LTE model spectrum using MCMC in detail. We have identified a total of seventy-five transitions of towards G358.93–0.03 MM1 between the frequency ranges of 290.51–292.39 GHz, 292.49–294.37 GHz, 302.62–304.49 GHz, and 304.14–306.01 GHz. The upper-level energies of the identified seventy-five transitions of vary from 63.86 K to 1362.19 K. Among the detected seventy-five transitions, we find that only fourteen transitions of are not blended, and these lines are identified to be higher than 4$\sigma$ (confirmed from LTE modelling). The upper-level energies of the non-blended transitions of vary between 69.40 K and 670.33 K. There are no missing transitions in in the observed frequency ranges. The blended transitions of will not be considered in our modelling. From the LTE modelling, the best-fit column density of is found to be (1.52$\pm$0.9)$\times$10$^{16}$ cm$^{-2}$ with an excitation temperature of 300$\pm$68.5 K and a source size of 0.45$^{\prime\prime}$. The FWHM of the LTE spectra of is 3.35 km s$^{-1}$. We observed that the FWHM of the spectra of is nearly similar to the FWHM of another molecule towards G358.93–0.03 MM1, which was estimated by (cite: bro19). The LTE-fitted rotational emission spectra of are shown in Figure [3](#fig:ltespec). In addition to , the hot molecular core G358.93–0.03 MM1 also contains several other complex organic molecules, including , , , , , , and , which we discuss in a separate paper.

We report the details of all the detected lines in Table [\[tab:MOLECULAR DATA\]](#tab:MOLECULAR DATA). Additionally, we also fitted the Gaussian model over the non-blended emission lines of to estimate the proper full width-half maximum (FWHM) in km s$^{-1}$ and integrated intensity ($\rm{\int T_{mb}dV}$) in K km s$^{-1}$. We have observed three different non-blended emission lines of at frequencies of 291.784 GHz, 292.536 GHz, and 292.737 GHz that contain multiple transitions of . These transitions are reported in Table [\[tab:MOLECULAR DATA\]](#tab:MOLECULAR DATA). We cannot separate these observed transitions as they are very close to each other, i.e., blended with each other. To obtain the line parameters of those transitions of , we have fitted a multiple-component Gaussian using the Levenberg-Marquardt algorithm in CASSIS to the observed spectra. For multiple Gaussian fittings, we have used fixed values of velocity separation and the expected line intensity ratio. During the fitting of a multi-component Gaussian, only the FWHM is kept as a free parameter. This method works well in the observed spectral profiles around 291.784 GHz, 292.536 GHz, and 292.737 GHz of . The summary of the detected transitions and spectral line properties of is presented in Table [\[tab:MOLECULAR DATA\]](#tab:MOLECULAR DATA).

To determine the fractional abundance of , we use the column density of inside the 0.45$^{\prime\prime}$ beam, and divide it by the column density found in Section [3.1.2](#sec:hydrogen). The fractional abundance of with respect to towards the G358.93–0.03 MM1 is (4.90$\pm$2.92)$\times$10$^{-9}$, where the column density of towards the G358.93–0.03 MM1 is (3.10$\pm$0.2)$\times$10$^{24}$ cm$^{-2}$. Recently, (cite: min20) found that the abundance of towards another hot molecular core, G31.41+0.31, was (5.0$\pm$1.4)$\times$10$^{-9}$, which is close to our derived abundance of towards G358.93–0.03 MM1. This indicates that the chemical formation route(s) of towards the G358.93–0.03 MM1 may be similar to those in G31.41+0.31.

![image](map1.pdf) ![image](map2.pdf) ![image](map3.pdf)

### Searching for towards G358.93–0.03 MM3

After the successful detection of in G358.93–0.03 MM1, we also search for emission lines of towards G358.93–0.03 MM3, which yield no detection. The derived upper-limit column density of towards this core is $\leq$(3.52$\pm$1.2)$\times$10$^{15}$ cm$^{-2}$. The upper limit of the fractional abundance is $\leq$(1.01$\pm$0.40)$\times$10$^{-8}$.

## Spatial distribution of towards G358.93–0.03 MM1

We create the integrated emission maps (moment zero maps) of towards G358.93–0.03 MM1 using the CASA task `IMMOMENTS`. In task `IMMOMENTS`, we use channels corresponding to the velocity ranges, where the emission lines of were detected. The integrated emission maps are shown in Figure [4](#fig:emissionmap). After the extraction, we apply the CASA task `IMFIT` to fit the 2D Gaussian over the integrated emission maps of to estimate the size of the emitting regions. The following equation is used

$$\begin{equation}
        
\theta_{S}=\sqrt{\theta^2_{50}-\theta^2_{\text{beam}}}
\end{equation}$$ where $\theta_{\text{beam}}$ is the half-power width of the synthesized beam and $\theta_{50} = 2\sqrt{A/\pi}$ denotes the diameter of the circle whose area is surrounded by the $50\%$ line peak of (cite: riv17). The derived sizes of the emitting regions of and velocity ranges at different frequencies are listed in Table [2](#tab:emitting region). The synthesized beam sizes of the integrated emission maps are 0.425$^{\prime\prime}\times$0.369$^{\prime\prime}$, 0.427$^{\prime\prime}\times$0.376$^{\prime\prime}$, 0.413$^{\prime\prime}\times$0.364$^{\prime\prime}$, and 0.410$^{\prime\prime}\times$0.358$^{\prime\prime}$, respectively. We observe that the estimated emitting region of is comparable to or slightly greater than the synthesized beam sizes of the integrated emission maps. This indicates that the detected transition lines are not spatially resolved or are only marginally resolved towards G358.93–0.03 MM1. Hence, we cannot draw any conclusions regarding the morphology of the spatial distributions of . Higher spatial and angular resolution observations are required to understand the spatial distribution of towards G358.93–0.03 MM1.

# Discussion

In this section, we compare the derived abundance of in G358.93–0.03 MM1 with that of other hot cores and corinos. We also discuss the possible pathways for the formation of in the context of hot molecular cores. Finally, we compare the observed abundance with those derived from chemical models.

## Comparison with other sources

We list the abundances of towards IRAS 16293–2422 B, NGC 7129 FIRS 2, NGC 1333 IRAS2A, Sgr B2 (N), G31.41+0.31, and G10.47+0.0 taken from the literature in Table [3](#tab:abundance). We note that for NGC 1333 IRAS 2A, (cite: cou15) did not actually derive an abundance with respect to but instead with respect to ()$_{2}$ and . We, therefore, used their derived column density of as well as the column density of as derived by (cite: taq15) to infer an abundance with respect to . Using the rotational diagram, (cite: cou15) derived the column density of towards NGC 1333 IRAS2A as 2.4$\times$10$^{15}$ cm$^{-2}$ with a rotational temperature of 130 K. The column density of molecular hydrogen towards NGC 1333 IRAS2A is 5.0$\times$10$^{24}$ cm$^{-2}$ (cite: taq15). To determine the fractional abundance of with respect to towards NGC 1333 IRAS2A, we use the column density of , which is divided by the column density of . We deduce a fractional abundance for towards NGC 1333 IRAS2A with respect to of 4.8$\times$10$^{-10}$.

Our estimate for the abundance of towards G358.93–0.03 MM1 ((4.90$\pm$2.92)$\times$10$^{-9}$) is quite similar to that of the hot molecular core G31.41+0.31 and the hot corino object IRAS 16293–2422 B while approximately one order of magnitude higher than that of G10.47+0.03, Sgr B2 (N), NGC 1333 IRAS 2A, and NGC 7129 FIRS 2. The similarity among G358.93–0.03 MM1, G31.41+0.31, and IRAS 16293–2422 B may indicate that the formation route(s) of may be similar in all three sources.

## Possible formation mechanisms of towards hot molecular cores and hot corinos

To date, only a few efficient formation pathways of have been proposed on grain surfaces in hot molecular cores and hot corinos (cite: gar06; gar08; gar13; cou18; riv19; min20). In the high temperature ($\geq 100$ K) regime, the radicals gain sufficient energy to diffuse across the surface and react to create complex organic molecules (cite: min20). Initially, two main formation pathways were proposed for the formation of :\
\
HCO + $\rightarrow$            (1)\
\
and\
\
+ HCO$\rightarrow$+H      (2)\
\
In reaction 1, radical HCO and radical react with each other on the grain surfaces to form (cite: gar08; gar13; cou18; riv19). This reaction appears to be responsible for the production of towards IRAS 16293–2422 B and G31.41+0.31 (cite: jo12; riv19; min20). In reaction 2, the radicals HCO and react with each other on the grain surfaces to produce , but this reaction has not yet been tested in a laboratory (cite: min20). Initially, (cite: fed15) and (cite: chu16) experimentally studied the possible formation pathways of on dust grains at low temperatures ($\sim$10 K). The experimental results of (cite: fed15) and (cite: chu16) were later confirmed by (cite: sim20) by using microscopic kinetic Monte Carlo simulations based on ice chemistry.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Observed frequency | $E_{u}$ | emitting region | Velocity ranges |  |  |  |  |  |  |  |  |  |  |  |  |  |
| (GHz) | \(K\) | ($^{\prime\prime}$) | (km s$^{-1}$) |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  290.589$^{*}$ | 182.37 | 0.410 | –14.29 to –19.61 |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 291.094 | 207.92 | 0.412 | –13.39 to –18.68 |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 291.784 | 211.41 | 0.413 | –14.38 to –20.57 |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 292.536 | 213.68 | 0.414 | –13.35 to –19.31 |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 292.737 | 336.79 | 0.415 | –14.40 to –19.22 |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 305.040 | 670.33 | 0.411 | –13.34 to –18.44 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  305.488$^{*}$ |  69.40 | 0.410 | –14.14 to –18.79 |  |  |  |  |  |  |  |  |  |  |  |  |  |

: Estimated emitting regions of towards the G358.93–0.03 MM1.

\*–There are two transitions that have close frequencies ($\leq 100$ kHz), and only the frequency of the first transition is shown.\

## Chemical modelling of in hot molecular cores

To understand the formation mechanisms and abundance of in hot molecular cores, (cite: cou18) computed a two-phase warm-up chemical model using the gas grain chemistry code `UCLCHEM` (cite: hol17). They assumed a free-fall collapse of a cloud (Phase I), followed by a warm-up phase (Phase II). In the first phase (Phase I), the gas density increased from $n_{H}$ = 300 cm$^{-3}$ to 10$^{7}$ cm$^{-3}$, and they assumed a constant dust temperature of 10 K. In the second phase (phase II), the gas density remained constant at 10$^{7}$ cm$^{-3}$, whereas the dust temperature increased with time from 10 to 300 K. This phase was known as the warm-up phase. In the chemical network used by (cite: cou18), the recombination of the radicals HCO and (Reaction 1) dominates the production of on the grains. Reaction 1 is the most likely pathway because (cite: but15) tested this reaction in the laboratory and confirmed that the reaction produced . In the warm-up phase, (cite: cou18) showed that the abundance of varied from $\sim$10$^{-9}$ to 10$^{-8}$ (see Figure 3 in (cite: cou18)). (cite: cou18) did not include reaction 2 (recombination of the radical HCO and ) as earlier work by (cite: wo12) showed that by including reaction 2, the estimated model abundance of was as high as $\sim$10$^{-5}$ (cite: wo12). This modelled abundance of by reaction 2 does not match any of the observed abundances in the sample of objects considered here.

## Comparison between observed and chemically modelled abundance of 

In order to understand the formation pathways of towards G358.93–0.03 MM1, we compare our estimated abundance with the modelled ones from (cite: cou18). This comparison is physically reasonable because the dust temperature of this source is 150 K, which is a typical hot core temperature, and the number density (n$_{H}$) of this source is $\sim$2$\times$10$^{7}$ cm$^{-3}$ (cite: chen20; ste21). Hence, the two-phase warm-up chemical model based on the timescales in (cite: cou18) is appropriate for explaining the chemical evolution of towards G358.93–0.03 MM1. (cite: cou18) showed that the abundances of varies between $\sim$10$^{-9}$ and 10$^{-8}$. We find that our estimated abundance towards G358.93–0.03 MM1 is (4.90$\pm$2.92)$\times$10$^{-9}$, which is in good agreement with the theoretical results in (cite: cou18). This comparison indicates that the simplest sugar-like molecule, , may form on the grain surface via the reaction between radical HCO and radical (Reaction 1) towards G358.93–0.03 MM1. Of course, the modelled abundance of is also similar to the observed abundance of towards the hot molecular core G31.41+0.31 and the hot corino object IRAS 16293–2422 B, indicating that reaction 1 may be the most likely pathway for the production of towards these two objects too. Radical HCO and radical may be created in the ISM by the hydrogenation of CO (CO + H$\rightarrow$HCO$^{\bullet}$+H$\rightarrow$$\rightarrow$) (cite: ha13). After hydrogenation, radical is converted into ( + H$\rightarrow$) (cite: ha13). Our conclusion agrees with the recent work of (cite: min20), who also found that reaction 1 is the most efficient pathway for the formation of towards the hot core G31.41+0.31, as well as other hot molecular cores.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | X() | Refreances |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Name |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G358.93–0.03 MM1 | (4.90$\pm$2.92)$\times$10$^{-9}$ | This paper |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| IRAS 16293–2422 B | 5.8$\times$10$^{-9}$ | (cite: jo12) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| NGC 7129 FIRS 2 | 5.0$\times$10$^{-10}$ | (cite: flu14) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| NGC 1333 IRAS2A | 4.8$\times$10$^{-10}$ | See section 4.1 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Sgr B2 (N) | 1.6$\times$10$^{-10}$ | (cite: xu19) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G31.41+0.31 | (5.0$\pm$1.4)$\times$10$^{-9}$ | (cite: min20) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G10.47+0.03 | 9.6$\times$10$^{-10}$ | (cite: mondal21) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

: Abundance of in different objects.

# Conclusions

We present the first detection of using ALMA in the hot molecular core G358.93–0.03 MM1. We identify a total of seventy-five transitions of , where the upper-level energies vary between 63.86 K and 1362.19 K. The derived abundance of is (4.90$\pm$2.92)$\times$10$^{-9}$. We compare our estimated abundance with that of other hot molecular cores and hot corinos and note that the abundance of towards G358.93–0.03 MM1 is quite similar to that found towards another hot molecular core, G31.41+0.31, and the hot corino, IRAS 16293–2422 B (cite: jo12; min20). We discuss the possible formation mechanisms of in hot molecular cores. We compare our estimated abundance of with the theoretical abundance from the chemical model presented in (cite: cou18) and find that they are similar. We conclude that is most likely formed via the reaction of radical HCO and radical on the grain surfaces in G358.93–0.03 MM1 and other hot molecular cores.

The identification of abundant in G358.93–0.03 MM1 suggests that grain surface chemistry is also efficient for the formation of other complex organic molecules in this hot molecular core, including isomers of , and . Indeed, the highly chemically rich spectra and detection of towards G358.93–0.03 MM1 make this object another ideal hot core to search for and study other complex organic molecules in star-forming regions. A spectral line study combined with a radiative transfer as well as a two-phase warm-up chemical model is required to understand the prebiotic chemistry of G358.93–0.03 MM1, which will be carried out in our follow-up study.

# ACKNOWLEDGEMENTS

We thank the anonymous referee for her/his constructive comments that helped improve the manuscript. A.M. acknowledges the Swami Vivekananda Merit-cum-Means Scholarship (SVMCM) for financial support for this research. SV acknowledges support from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation program MOPPEX 833460. This paper makes use of the following ALMA data: ADS /JAO.ALMA#2019.1.00768.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in co-operation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

# DATA AVAILABILITY

The plots within this paper and other findings of this study are available from the corresponding author on reasonable request. The data used in this paper are available in the ALMA Science Archive (<https://almascience.nrao.edu/asax/>), under project code 2019.1.00768.S.

natexlab

(ref: bel13) Belloche A., Müller H. S. P., Menten K. M., Schilke P., Comit C., 2013, A&A, 559, A47

(ref: bel09) Beltrán M. T., Codella C., Viti S., Neri R., Cesaroni R., 2009, ApJL, 690, L93

(ref: bro19) Brogan C. L., Hunter T. R., Towner A. P. M. et al., 2019, ApJL, 881, L39

(ref: bay22) Bayandina O.S., Brogan C.L., Burns, R.A., et al. 2022, AJ, 163(2), p.83

(ref: but15) Butscher T., Duvernay F., Theule P., Danger G., Carissan Y., Hagebaum-Reignier D., Chiavassa T., 2015, MNRAS, 453, 1587

(ref: bri95) Briggs, D. S. 1995, PhD Thesis, New Mex. Inst Min. Tech

(ref: cal14) Calcutt H., Viti, S., Codella C., Beltrán M. T., Fontani F., Woods, P. M., 2014, MNRAS, 443, 3157

(ref: cou18) Coutens A., Viti S., Rawlings J. M. C., et al. 2018, MNRAS, 475, 2

(ref: cou15) Coutens A., Persson M. V., Jørgensen J. K., Wampfler S. F., Lykke J. M., 2015, A&A, 576, A5

(ref: chu16) Chuang K. J., Fedoseev G., Ioppolo S., van Dishoeck E. F., & Linnartz H., 2016, MNRAS, 455, 1702

(ref: cox00) Cox A. N., & Pilachowski C. A., 2000, Physics Today, 53, 77

(ref: chen20) Chen X., Sobolev A. M., Ren Z.-Y., et al. 2020, NatAs, 4, 1170

(ref: fed15) Fedoseev G., Cuppen H. M., Ioppolo S., Lamberts T., & Linnartz H., 2015, MNRAS, 448, 1288

(ref: flu14) Fuente A., Cernicharo J., Caselli P., et al. 2014, A&A, 568, A65

(ref: gar13) Garrod R. T., 2013, ApJ, 765, 60

(ref: gar06) Garrod R. T., & Herbst E. 2006., A&A, 457, 927

(ref: gar08) Garrod R. T., Widicus Weaver S. L., & Herbst E., 2008, ApJ, 682, 283

(ref: gor20) Gorai P., Bhat B., Sil M., Mondal S. K. Ghosh R., Chakrabarti S. K., Das A., 2020, ApJ, 895, 86

(ref: ha13) Hama T., Watanabe N., 2013, Chem. Rev., 113, 8783

(ref: hol17) Holdship J., Viti S., Jiménez-Serra I., Makrymallis A., Priestley F., 2017, AJ, 154, 38

(ref: hal00) Hollis J. M., Lovas F. J., & Jewell P. R., 2000, ApJ, 540, L107

(ref: hal01) Hollis J. M., Vogel S. N., Snyder L. E., Jewell P. R., & Lovas F. J., 2001, ApJ, 554, L81

(ref: hal04) Hollis J. M., Jewell P. R., Lovas F. J., & Remijan A., 2004, ApJL, 613, L45

(ref: hal06) Halfen D. T., Apponi A. J., Woolf N., Polt R., Ziurys L. M., 2006, ApJ, 639, 237

(ref: her09) Herbst E., & van Dishoeck E. F., 2009, ARA&A, 47, 427

(ref: jo12) Jørgensen J. K., Favre C., Bisschop S. E., Bourke T. L., van Dishoeck E. F., Schmalzl M., 2012, ApJL, 757, L4

(ref: man23) Manna, A. & Pal, S., 2023, Astrophys Space Sci, 368, 33, <https://doi.org/10.1007/s10509-023-04192-4>

(ref: mondal21) Mondal S. K., Gorai P., Sil M., Ghosh R., Etim E. E., Chakrabarti S. K., Shimonishi T., Nakatani N., Furuya K., Tan J. C., Das, A., 2021, ApJ, 922, 194

(ref: mc07) McMullin J. P., Waters B., Schiebel D., Young W., & Golap K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mu05) Müller H. S. P., SchlM$\ddot{o}$der F., Stutzki J. Winnewisser G., 2005, Journal of Molecular Structure, 742, 215

(ref: min20) Mininni C. et al., 2020, A&A, 644, A84

(ref: moto19) Motogi K., Hirota T., Machida M. N., et al. 2019, ApJL, 877, L25

(ref: nom04) Nomura H., & Millar T. J., 2004, A&A, 414, 409

(ref: pal17) Perley R. A., Butler B. J., 2017, ApJ, 230, 1538

(ref: re14) Reid M. J., Menten K. M., Brunthaler, A., et al. 2014, ApJ, 783, 130

(ref: riv17) Rivilla V. M., Beltrán M. T., Cesaroni R., et al. 2017, A&A, 598, A59

(ref: riv19) Rivilla V. M., Beltrán M. T., Vasyunin A., et al. 2019, MNRAS, 483, 806

(ref: shi21) Shimonishi T., Izumi N., Furuya K., & Yasui C., 2021, ApJ, 2, 206

(ref: ste21) Stecklum B., Wolf V., Linz H., et al., 2021. A&A, 646, p.A161

(ref: sim20) Simons M. A. J., Lamberts T., & Cuppen H. M., 2020, A&A, 634, A52

(ref: taq15) Taquet, V., L$\acute{o}$pez-Sepulcre, A., Ceccarelli, C., et al. 2015, ApJ, 804, 81

(ref: taq16) Taquet V., Wirstr$\ddot{o}$m E. S., & Charnley S. B. 2016, ApJ, 821, 46

(ref: vas15) Vastel C., Bottinelli S., Caux E., Glorian J. -M., Boiziot M., 2015, CASSIS: a tool to visualize and analyse instrumental and synthetic spectra. Proceedings of the Annual meeting of the French Society of Astronomy and Astrophysics, 313-316

(ref: vi04) Viti, S., Collings, M. P., Dever, J. W., McCoustra, M. R. S., & Williams, D. A. 2004, MNRAS, 354, 1141

(ref: van98) van Dishoeck E. F. & Blake G. A., 1998, Annu Rev Astron Astrophys, 36, 317

(ref: wo12) Woods P. M., Kelly, G., Viti, S., et al., 2012, APJ, 750, 19

(ref: whi92) Whittet D. C. B., 1992, Journal of the British Astronomical Association, 102, 230

(ref: wi14) Williams D. A., Viti S., 2014, Observational Molecular Astronomy: Exploring the Universe Using Molecular Line Emissions. Cambridge Univ. Press, Cambridge

(ref: xu19) Xue C., Remijan A. J., Burkhardt A. M., & Herbst E., 2019, ApJ, 871, 112

[^1]: E-mail:arijitmanna@mcconline.org.in

[^2]: E-mail:sabya.pal@gmail.com

</paper>

Write the methods card for this paper.