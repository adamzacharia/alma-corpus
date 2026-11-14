# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...984L..58H\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2025ApJ...984L..58H",
 "title": "ALMASOP: Detection of Turbulence-induced Mass Assembly Shocks in Starless Cores",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Hsu, Shih-Ying",
 "n_authors": 11,
 "arxiv_id": "2504.11776",
 "doi": "10.3847/2041-8213/adcd6a",
 "alma_projects_linked_by_archive": [
  "2023.1.01067.S"
 ]
}
```

Paper text:
<paper>
# ALMASOP. Detection of Turbulence-induced Mass Assembly Shocks in Starless Cores

## Abstract

Star formation is a series of mass assembly processes and starless cores, those cold and dense condensations in molecular clouds, play a pivotal role as initial seeds of stars. With only a limited sample of known starless cores, however, the origin and growth of such stellar precursors had not been well characterized previously. Meanwhile, the recent discovery of CH$_3$OH emission, which is generally associated with desorbed icy mantle in warm regions, particularly at the periphery of starless cores also remains puzzling. We present sensitive ALMA (Band 3) observations (at 3 mm) toward a sample of newly identified starless cores in the Orion Molecular Cloud. The spatially resolved images distinctly indicate that the observed CH$_3$OH and N$_2$H$^+$ emission associated with these cores are morphologically anti-correlated and kinematically offset from each other. We postulate that the CH$_3$OH emission highlights the desorption of icy mantle by shocks resulting from gas piling onto dense cores in the filaments traced by N$_2$H$^+$. Our magnetohydrodynamic (MHD) simulations of star formation in turbulent clouds combined with radiative transfer calculations and imaging simulations successfully reproduced the observed signatures and reaffirmed the above scenario at work. Our result serves as an intriguing and exemplary illustration, a snapshot in time, of the dynamic star-forming processes in turbulent clouds. The results offer compelling insights into the mechanisms governing the growth of starless cores and the presence of gas-phase complex organic molecules associated with these cores.

UTF8bsmi

# Introduction

Starless cores are the precursors to stars; however, the processes governing their origin and growth remain poorly understood. Two main scenarios have been proposed to describe the evolution of starless cores: the ambipolar diffusion scenario and the supersonic turbulence scenario. The ambipolar diffusion model portrays the evolution of starless cores as a quasi-static gravitational accretion process (cite: 1987_Shu). In contrast, the supersonic turbulence model suggests that turbulence induces local compressions, leading to the formation of filaments and cores (cite: 1999Maclow_driving; 1999_Padoan; 2001_Hartmann)). Turbulent fragmentation has been shown to satisfactorily explain the core population in clouds including Orion B, whereas clouds influenced by external pressure (e.g., Chamaeleon I) do not follow this model (cite: 2024Fielder_G205M3). While magnetohydrodynamic (MHD) turbulence is now widely believed to play a crucial role in starless cores (cite: 2004Lazarian_review), direct observational evidence linking turbulence with core evolution remains scarce.

Recent detections of gas-phase complex organic molecules (COMs) in starless cores introduce further puzzles. COMs, such as CH$_3$OH, are saturated organic molecules containing at least six atoms (cite: 2009Herbst_COM_review), primarily formed in the icy mantles of dust grains. The presence of gaseous COMs, CH$_3$OH in particular, would indicate desorption of icy mantles. Thermal desorption mechanism, demonstrated by (cite: 2023Hsu_ALMASOP) for example, successfully explained the intensity and extent of CH$_3$OH emission in the localized warm gas around a sample of protostellar cores in the Orion molecular cloud. However, the desorption processes in starless cores remain debated, despite reports of gas-phase CH$_3$OH detection (cite: 2020Scibelli_ColdCoresTaurus_COMs; 2024Scibelli_Perseus_COM).

Several potential desorption mechanisms have been proposed, including cosmic ray ice sputtering (cite: 2019Dartois_CR_sputtering; 2021Wakelam_CR_sputtering) and reactive desorption (cite: 2007Garrod_reactive-desorption; 2013Vasyunin_reactive-desorption; 2017Vasyunin_reactive-desorption; 2018Chuang_reactive-desorption). Observationally, CH$_3$OH emission is found to be ubiquitous in chemical surveys toward the Taurus (cite: 2020Scibelli_ColdCoresTaurus_COMs) and the Perseus clouds (cite: 2024Scibelli_Perseus_COM), suggesting the prevalence of desorption mechanisms.

In this Letter, we present our observations of CH$_3$OH and N$_2$H$^+$ of five dense starless cores in the Orion Molecular Cloud. Section [2](#sec:methods) outlines our observational methods. Based on the morphology and kinematics, we identify shock interfaces between dense filaments and the surrounding diffuse gas, as detailed in Section [3](#sec:results). Our findings imply a framework in which turbulence-induced mass assembly shocks facilitate the release of methanol from ice surfaces to the gas phase. To support this framework, we incorporate core evolution simulations as is described in Section [4](#sec:ORION2). Finally, in Section [5](#sec:Disc), we discuss the broader implications of our results and their alignment with existing literature.

# Methods

| Source | Short | Cloud | $\alpha_{2000}$ | $\delta_{2000}$ | BMAJ | BMIN | BPA | $v_\mathrm{LSR}$ |
|:---|:---|:---|:---|:---|:---|:---|:---|---:|
| G205.46-14.56M3 | G205M3 | B | 05h46m06.01s | -00d09m32.8s | 2$.\!\!^{\prime\prime}$96 | 2$.\!\!^{\prime\prime}$34 | 84$^\circ$ | 10.2 km s$^{-1}$ |
| G208.68-19.20N2 | G208N2 | A | 05h35m21.04s | -05d00m57.9s | 2$.\!\!^{\prime\prime}$93 | 2$.\!\!^{\prime\prime}$28 | 87$^\circ$ | 11.0 km s$^{-1}$ |
| G209.29-19.65S1 | G209S1 | A | 05h34m55.86s | -05d46m05.0s | 2$.\!\!^{\prime\prime}$92 | 2$.\!\!^{\prime\prime}$26 | 88$^\circ$ | 6.7 km s$^{-1}$ |
| G209.94-19.52N | G209N | A | 05h36m11.32s | -06d10m44.8s | 2$.\!\!^{\prime\prime}$92 | 2$.\!\!^{\prime\prime}$26 | 88$^\circ$ | 8.0 km s$^{-1}$ |
| G212.10-19.15N1 | G212N1 | A | 05h41m21.21s | -07d52m26.9s | 2$.\!\!^{\prime\prime}$90 | 2$.\!\!^{\prime\prime}$23 | 88$^\circ$ | 5.0 km s$^{-1}$ |

Table notes: The coordinates are identified as the 3 mm continuum peak. BMAJ, BMIN, BPA are the major axis, minor axis, and the position angle of the beam, respectively. The $v_\mathrm{LSR}$ is the system velocity, derived from the velocity shift of the N$_2$H$^{+}$ transition.

## Sample Selection

To address these questions, we have selected a sample of five dense cores in the Orion Molecular Cloud, identified from the ALMA Survey of Orion PGCCs (ALMASOP) catalogue (cite: 2020Dutta_ALMASOP): G205.46-14.56M3, G208.68-19.20N2, G209.29-19.65S1, G209.94-19.52N, and G212.10-19.15N1 (hereafter referred to as G205M3, G208N2, G209S1, G209N, and G212N1, respectively).

The ALMASOP project targeted 72 extremely dense and compact 850 $\mu$m continuum sources located at the Orion cloud, aiming to study the star formation at their early stages. Based on the observations, (cite: 2020Dutta_ALMASOP) reported a catalogue of 23 starless cores and 56 Class 0/I protostellar cores. Our five targets represent the densest starless cores in the catalogue, identified through their significant detections (cite: 2021Sahu_ALMASOP_presstellar).

The high densities imply that they are at the critical time for the subsequently forming central protostar.

Details of the target cores are listed in Table [\[tab:coord\]](#tab:coord).

## Observations

This study utilized data from the Atacama Large Millimeter/submillimeter Array (ALMA) Cycle 10 program (#2023.1.01067.S, PI: Sheng-Yuan Liu) in Band 3 (3 mm). Observations were conducted with the 12-m array in the C-2 configuration, providing deprojected baseline lengths ranging from 5 to 104 k$\lambda$. The maximum recoverable scale in the observations was 28$.\!\!^{\prime\prime}$8 and the final images achieved an angular resolution of $\sim$3$.\!\!^{\prime\prime}$5.

The receivers captured data across 16 spectral windows (SPWs), comprising 12 SPWs with bandwidths of 59 MHz and four SPWs with bandwidths of 117 MHz. The channel width is 61 kHz, corresponding to a velocity resolution of 0.2 km s$^{-1}$. For this study, we focused on two SPWs having a bandwidth of 59 MHz centered at 93.164 GHz and 96.732 GHz, which covers the transitions of our targeted molecules, N$_2$H$^+$ and CH$_3$OH. N$_2$H$^+$ is known to be a good tracer of the cold and dense gas since it is easily destroyed by gaseous CO and, therefore, can only survive in CO-depleted region (cite: 2016Yamamoto_book). In our spectral coverage, the multiple N$_2$H$^+$ $J=1–0$ hyperfine lines form three groups at $\sim$ 93.172 ($F_1=1-1$), 93.174 ($F_1=2-1$), and 93.176 ($F_1=0-1$) GHz. We used the one at 93.176 GHz ($F_1=0-1$) consisting of three transitions ($F=1-0$, $F=1-1$, and $F=1-2$) for the following two reasons. First, its hyperfine lines have frequencies that are indistinguishable within our spectral resolution, reducing the impact of line blending in the channel maps. Second, this group had the weakest intrinsic line strength among the three; as a result, the emission was less optically thick. CH$_3$OH is the simplest COM and widely used as an indicator of complex organic chemistry. Three CH$_3$OH lines, namely the transitions $2_{0,2}–1_{0,1}~A$, $2_{1,2}–1_{1,1}~E$, $2_{0,2}–1_{0,1}~E$ having upper energies at 7, 13, and 20 K, respectively, were included in our spectral coverage. We primarily used the one at 7 K as it has the strongest line intensity.

Imaging was performed using the `tclean` task in CASA 6.5.4 (cite: casa:2022). The mask parameter was set to “auto-multithresh,” the deconvolver was “hogbom,” and a Briggs robust weighting value of 2.0 was applied. The imaging thresholds were 0.2 mJy for the full-band ($\sim$0.857 GHz) continuum and 10 mJy for individual channels ($\sim$61 kHz per channel). The final images achieved a beam size $\sim$3$.\!\!^{\prime\prime}$5 (1,400 au at 400 pc) and sensitivities of 0.025 mJy/beam for the full-band continuum and 2 mJy/beam for each channel.

# Results

## Morphology and Kinematics

![](figure/mom0_12m_Cycle10.pdf)

We imaged 3 mm continuum, N$_2$H$^+$ $J=1-0$ $F_1 = 0–1$, and CH$_3$OH $2_{0,2}$–$1_{0,1}~A^+$ with $E_\mathrm{u} = 7$ K line emissions in all five of our targets (Fig.[1](#fig:mom0_12m_Cycle~10)). In general, the N$_2$H$^+$ emission appears extended and encompasses the dust continuum, consistent with N$_2$H$^+$ tracing cold and dense gas. However, the N$_2$H$^+$ and dust continuum peaks do not coincide, suggesting a possible depletion of N$_2$H$^+$ in the innermost and densest regions of these dense cold cores. CH$_3$OH emission is distributed at the periphery of the N$_2$H$^+$ component and appears more fragmented. This behavior is similar to that observed in the starless core L1544 on a scale of $\sim$2$^\prime$  (cite: 2014Bizzocchi_L1544_CH2DOH; 2017Spezzano_L1544_ChemStructure), where CH$_3$OH does not peak at the same positions where the dust continuum and the N$_2$H$^+$ emission peak.

Interestingly, upon visually inspecting the channel map matrix, as exemplified in Fig. [6](#fig:matrix_G205M3), we observe velocity differences between CH$_3$OH and its neighboring N$_2$H$^+$ counterpart. For instance, Fig. [2](#fig:chn_shock_obs) presents the channel maps of G205M3, where the velocity jumps are recognized more clearly.

Taking the interface marked by the red segment as an example, the CH$_3$OH component appears at $v=10.6$ km/s, while the N$_2$H$^+$ counterpart appears at $v=10.2$ km/s, inferring a velocity jump of 0.4 km/s. For the blue segment, the velocity jump reaches $9.4-8.6=0.8$ km/s. These velocity jumps of 0.4 – 0.8 km/s are higher than the sound speed in cold cores (approximately 0.2 km/s at 10 K (cite: 2007Bergin_review)), suggesting the existence of shocks at the interface between CH$_3$OH and N$_2$H$^+$ gas components within a field size of $\sim$50$^{\prime\prime}$($\sim$20,000 au). The N$_2$H$^+$ component, characterized by CO depletion, represents denser regions of the core. The velocity jumps (0.4 – 0.8 km/s) between gas components are consistent with the velocity dispersion (0.45 km/s) due to the turbulence activities at a cloud size of 20,000 au inferred from (cite: 1981Larson_turbulence).

![](figure/chn_shock_obs.pdf)

## Implications of the detected Shocks

It is generally accepted that in cold starless cores CH$_3$OH is produced on dust grains and then liberated into the gas phase in the later protostellar stage (cite: 2009Herbst_COM_review)), despite other pathways were also suggested (cite: 2023Nakai_CH3OH_formation). Our findings suggest that the desorption leading to the observed CH$_3$OH gas is the result of the shocks induced by turbulence activities. Shocks could possibly cause the presence of COMs via thermal or mechanical processes. In the thermal processes, a slow shock with a velocity jump of 0.4 km/s can heat dust grains from 10 to 30 K and trigger the desorption of grain mantles (cite: 2001Dickens_TMC1; 2015Soma_TMC1). Alternatively, the “mechanical removal” of the icy mantle in oblique collisions between grains could lead to the presence of abundant gaseous COMs (cite: 2022Kalvans_desorption). We favor the latter interpretation, as the CH$_3$OH transition with higher upper energy ($E_\mathrm{u} = 20$ K) is either not detected or only weakly detected compared to the $E_\mathrm{u} = 7$ K transition (Figure [7](#fig:mom0_CH3OH_20K)). Particularly, in the case of G208N2, our observed CH$_3$OH is distributed on the northeastern side, whereas (cite: 2024Hirano_G208.68-19.20N2_dense) suggested that the southern edge of the filamentary cloud is relatively warmer, making thermal desorption of CH$_3$OH unlikely.

We further postulate that the turbulence we observed drives the gas assembly onto dense cores within filaments. Previous studies have demonstrated that MHD turbulence can facilitate mass assembly in molecular clouds and lead to the formation of high-density cores (cite: 2001Balsara_turbulent-MHD-model). Observationally, a transition from a turbulent parent cloud to the quiescent dense core was proposed to explain the coexistence of narrow and broad red-shifted NH$_3$ lines in the starless core TUKH122 (cite: 2016Ohashi_TUKH122_turbulence). Similarly, in two sources within the Cepheus-L1251 cloud, a velocity offset greater than 0.5 km/s between NH$_3$ and HC$_5$N was interpreted as evidence of a transition from the turbulent parental cloud to the quiescent dense region (cite: 2017Keown_CepheusL1251).

We estimated the mass assembly rate ($\Dot{M}$) using our observations, following the relation: $$\begin{equation}
\Dot{M} = \rho\ A\ \delta v, 
\end{equation}$$ where $\rho$ is the gas density, $A$ is the area, and $\delta v$ represents the assembly velocity. For each pixel, the area $A$ is assumed to be the physical size of the pixel, i.e., $A=$ (400 pc $\times$ 0$.\!\!^{\prime\prime}$5)$^{2}$. We assumed that the assembly velocity is comparable to the velocity difference between the quiescent dense core and its turbulent ambient, defined as $\delta v = v - v_\mathrm{LSR}$, where $v_\mathrm{LSR}$ is the systemic velocity of the dense core derived from the velocity shift of the N$_2$H$^+$ transition and $v$ corresponds to the frequency at which the CH$_3$OH line peaks. The velocity difference $\delta v$ was further multiplied by a factor of $\sqrt{3}$ to account for the projection. To estimate $\rho$, we first calculated the integrated brightness temperature ($W$) and derived the CH$_3$OH column density of the upper energy state ($N_\mathrm{u}$) using: $$\begin{equation}
N_\mathrm{u} = \frac{8\pi k_\mathrm{B}}{hc^3} \frac{\nu W}{A_\mathrm{ij}}, 
\end{equation}$$ where $A_{ij}$ and $\nu$ are the Einstein coefficient and transition frequency, respectively, with the assumption of optically thin CH$_3$OH emission. The total CH$_3$OH column density, $N$(CH$_3$OH), with the assumption of local-thermodynamic-equilibrium (LTE), was then determined as: $$\begin{equation}
N\mathrm{(CH}_3\mathrm{OH)} = Z(T)\, \frac{N_\mathrm{u}}{g_\mathrm{u}}\,e^{\frac{E_\mathrm{u}}{k_\mathrm{B}T}}, 
\end{equation}$$ where $T$ is the gas temperature (assumed to be 10 K), $Z(T) = 84$ is the corresponding partition function, and $g_\mathrm{u}$ and $E_\mathrm{u}$ are the statistical weight and energy of the upper state, respectively. Given a fractional abundance ($X$) and the core size ($\ell$), the gas density was estimated as: $$\begin{equation}
\label{eq:rate}
\rho = \mu\,m_\mathrm{H}\,n\mathrm{(H}_2\mathrm{)} = \frac{\mu\,m_\mathrm{H}\,N\mathrm{(CH}_3\mathrm{OH)}}{X\,\ell}, 
\end{equation}$$ where $\mu = 2.35$ is the mean molecular weight per free particle, and $m_\mathrm{H}$ is the hydrogen mass. The mass assembly rate, as shown in Eq. [\[eq:rate\]](#eq:rate), is inversely proportional to the fractional abundance ($X$) and the core size ($\ell$). Adopting the $X \sim 10^{-6}$ from (cite: 2015Boogert_review_ice) and the $\ell \sim 0.02$ pc from (cite: 2021Sahu_ALMASOP_presstellar), the total mass assembly rate ($\Dot{M}$) from $1.1$ to $3.1 \times 10^{-7}~M_\odot$$\>\rm yr^{-1}$. This value may be underestimated. First, the observed CH$_3$OH emission may not capture the mass under the assembling process. Second, the fractional abundance adopted here was measured from the ice compositions of low-mass protostellar cores. As a result, this fractional abundance may be overestimated due to factors such as a lower reservoir of CH$_3$OH molecules within the ice and uncertainties in the desorption efficiency of mechanical removal. A desorption efficiency of 10% would increase the estimated mass assembly rate to $10^{-6}$ $M\odot$$\>\rm yr^{-1}$, aligning with the expected lifetime of a solar-like starless core of $10^6$ years (cite: 2000Klessen_model_turbulence). A more detailed simulation incorporating factors such as collision geometry, complex organic chemistry networks, and molecule desorption efficiency would help refine this estimate.

# Core Evolution

To test this hypothesis of turbulence-induced mass assembly, we produced the synthesized images for a starless core extracted from a filamentary dark cloud formation simulation. This simulation used numerical method for the study of magnetic properties of clumps/cores in the turbulence filamentary dark clouds (cite: 2015Li_ORION2; 2019Li_ORION2). The ideal MHD simulation was performed using the multiphysics Godunov code ORION2 with block-structured Adaptive Mesh Refinement (AMR) framework (cite: 2012Li_ORION2; 2021Li_ORION2).

The simulation started with a uniform density and magnetic field at a thermal Mach number of 10 and an Alfv$\acute{e}$nic Mach number of 1. The initial turbulence driving over two crossing times of were applied at the largest scales with wave numbers $k = 1-2$ using the recipe described in (cite: 1999Maclow_driving). After the initial turbulence driving, the system was in statistical equilibrium state. Gravity was turned on and the system was continued to be driven to maintain a global turbulence at a thermal Mach number of 10. The system was scaled by the virial parameter of 1 when gravity was on.

Using line width-size relation from observations (cite: 2007McKee_linewidthsize), the velocity dispersion of a Mach 10 turbulence system gives the length of the simulation region to be 4.55 pc (see Equation 1 in (cite: 2019Li_ORION2). The virial parameter of 1 will define the scale of mass in the system to be $3110 {\rm M_{\odot}}$ (see equation of 5 in (cite: 2019Li_ORION2)). The Alfvenic Mach number of 1 will define the mean magnetic field strength of $31.6~\mu {\rm G}$, when virial parameter is 1 (see equation 8 in (cite: 2019Li_ORION2)). Periodic boundary conditions and isothermal equation of state were used for the simulation on a base grid of $512^3$ with 2 levels of refinement. The highest resolution is about 0.0022 pc (450 au). The density and velocity profiles of the simulated core were extracted when its peak number density reached $1\times10^7$ cm$^{-3}$, the value for G205M3 estimated by (cite: 2023Sahu_ALMASOP_prestellar).

We conducted radiative transfer calculations using “SPARX (Simulation Package for Astronomical Radiative Xfer)”, which is a radiative transfer code for submillimeter/millimeter wavelengths. For N$_2$H$^+$, we assumed it resides in gas with number densities exceeding its critical density ($6\times10^4$ cm$^{-3}$) and adopted a fractional abundance of $10^{-9}$. For CH$_3$OH, we assumed it is present in regions experiencing a velocity jump ($\Delta v$) greater than 0.4 km/s, with an fractional abundance of $10^{-6}$ (cite: 2015Boogert_review_ice). The velocity jump ($\Delta v$) is defined by the three-dimensional velocity differences at each location.

The dust temperature and the gas temperature were fixed to 10 K. The gas-to-dust mass ratio was set to 100.

![](figure/raster_3d.pdf)

The simulation results revealed that shocks are widespread around the dense filament because of supersonic turbulence (Fig. [3](#fig:raster_3d)). As a demonstration of the core in the Orion cloud, the velocity jump reaches 0.4 – 0.8 km s$^{-1}$ (Fig. [4](#fig:chn_shock_sim)). Further synthetic images made under the assumption that N$_2$H$^+$ traces dense gas and CH$_3$OH traces shocked regions, successfully reproduced the observed morphologically anti-correlated and kinematically mismatched CH$_3$OH and N$_2$H$^+$ emission. Additionally, the CH$_3$OH emission is widespread around the N$_2$H$^+$ emission, consistent with the observed spatial distribution (Fig. [4](#fig:chn_shock_sim)).

# Discussion and Conclusion

Our findings reveal that, as a tracer of turbulence-induced shocks, CH$_3$OH emission captures the ongoing mass assembly from the surrounding diffuse medium onto the dense core. This could explain why CH$_3$OH emission in starless cores often peaks at positions offset from N$_2$H$^+$ or the continuum, as observed in this study and in L1544 (cite: 2014Bizzocchi_L1544_CH2DOH; 2017Spezzano_L1544_ChemStructure). In cases such as G209S1 from our study, we observe spatially overlapping CH$_3$OH and N$_2$H$^+$ emissions. Based on our scenario, this overlap may indicate that the shocked regions are superimposed along the line of sight, either in front of or behind the N$_2$H$^+$ gas component, or that shocks (turbulence-induced or inflow-induced) exist within the dense core itself. Additionally, in G208N2, the observed CH$_3$OH emission could potentially be associated with nearby protostars (e.g., MMS 3, \[$\Delta \alpha_{2000}$, $\Delta \delta_{2000}]\sim$\[$-20\hbox{$^{\prime\prime}$}$, $0\hbox{$^{\prime\prime}$}$\]), possibly due to outflows originating from these objects.

Given that turbulence activity in the Orion Molecular Cloud is more intense than that in other nearby star-forming clouds, such as the Taurus and Perseus clouds (cite: 2022Ha_turbulence_clouds)), we examine whether there are compelling evidence indicating the association between gas-phase CH$_3$OH and turbulence activity across different clouds. In the starless core TMC1-CP, a “clump-clump collision shock” has been proposed to explain chemical variations at the cyanopolyyne peak and is discussed as a potential mechanism for CH$_3$OH production (cite: 2001Dickens_TMC1; 2015Soma_TMC1). Additionally, the line profile of CH$_3$OH in starless cores within the Taurus clouds suggests a combination of bulk motions (e.g., gradients or flows) and supersonic turbulence (cite: 2020Scibelli_ColdCoresTaurus_COMs). Moreover, surveys of starless cores in the Taurus (cite: 2020Scibelli_ColdCoresTaurus_COMs) and Perseus (cite: 2024Scibelli_Perseus_COM) clouds indicate low excitation temperatures for CH$_3$OH ($\mathrel{\hbox{\rlap{\hbox{
 \lower 4pt\hbox{$\sim$}}}\hbox{$<$}}}$ 10 K), supporting that CH$_3$OH is desorbed via mechanical removal. Further survey-type observations with high spatial and spectral resolution are essential to determine whether turbulence-induced mass assembly is also at work in these clouds, as observed in the Orion cloud, especially given the varying properties of star-forming regions (e.g., high- vs. low-mass regions and differences in dust temperature).

A further question is the timescale over which CH$_3$OH gas can persist in the gas phase before, for instance, depleting back onto dust grains. A short timescale would suggest that the observed CH$_3$OH emission represents a snapshot of an active turbulence-induced mass assembly process. Conversely, a longer survival timescale would imply the presence of an extended CH$_3$OH gas component, reflecting the widespread turbulence activity in starless cores (e.g., Fig. [3](#fig:raster_3d)). Future simulations that incorporate chemical networks, alongside laboratory experiments, could offer critical insights into this phenomenon. Moreover, comparisons between single-dish and interferometric observations may help identify and characterize such extended CH$_3$OH components.

![](figure/chn_shock_sim.pdf)

# Acknowledgments

This paper makes use of the following ALMA data: ADS/JAO.ALMA##2023.1.01067.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. Tie Liu acknowledges the supports by the National Key R&D Program of China (No. 2022YFA1603101), National Natural Science Foundation of China (NSFC) through grants No.12073061 and No.12122307. S.-Y. H. and S.-Y.L. acknowledge grants from the National Science and Technology Council of Taiwan (112-2112-M-001-060- and 113-2112-M-001-004-). P.S. Li acknowledges the supports by the National Key R&D Program of China (No. 2022YFA1603101) and NSFC through grant No. 1241101426. D.S. acknowledges the support from Ramanujan Fellowship (SERB, RJF/2021/000116) and PRL. X.L. acknowledges the support of the Strategic Priority Research Program of the Chinese Academy of Sciences under Grant No. XDB0800303.

# Software

astropy (cite: astropy:2013; astropy:2018), `CASA` (cite: casa:2007; casa:2022), `CARTA` (cite: 2021Comrie_CARTA), `SPARX`

# Supplementary figures

Fig. [5](#fig:chn_map) shows the channel maps of the observations and simulations for completeness of the report. Fig. [6](#fig:matrix_G205M3) shows the channel map matrix of G205.46-14.56M3, which we used for visually inspecting the shock interface. Fig. [7](#fig:mom0_CH3OH_20K) shows the integrated intensities of the CH$_3$OH $E_\mathrm{u}=7$ K transition and $E_\mathrm{u}=20$ K transitions and the 3 mm continuum.

![](figure/chn_map.pdf)

![](figure/matrix_G205M3.pdf)

![](figure/mom0_CH3OH_20K.pdf)

natexlab

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2001Balsara_turbulent-MHD-model) Balsara, D., Ward-Thompson, D., & Crutcher, R. M. 2001, Monthly Notices of the Royal Astronomical Society, 327, 715, doi: [`10.1046/j.1365-8711.2001.04787.x`](http://doi.org/10.1046/j.1365-8711.2001.04787.x)

(ref: 2007Bergin_review) Bergin, E. A., & Tafalla, M. 2007, Annual Review of Astronomy and Astrophysics, 45, 339, doi: [`10.1146/annurev.astro.45.071206.100404`](http://doi.org/10.1146/annurev.astro.45.071206.100404)

(ref: 2014Bizzocchi_L1544_CH2DOH) Bizzocchi, L., Caselli, P., Spezzano, S., & Leonardo, E. 2014, Astronomy and Astrophysics, 569, A27, doi: [`10.1051/0004-6361/201423858`](http://doi.org/10.1051/0004-6361/201423858)

(ref: 2015Boogert_review_ice) Boogert, A. C. A., Gerakines, P. A., & Whittet, D. C. B. 2015, Annual Review of Astronomy and Astrophysics, Vol 53, 53, 541, doi: [`10.1146/annurev-astro-082214-122348`](http://doi.org/10.1146/annurev-astro-082214-122348)

(ref: casa:2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacific, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: 2018Chuang_reactive-desorption) Chuang, K. J., Fedoseev, G., Qasim, D., et al. 2018, The Astrophysical Journal, 853, 102, doi: [`10.3847/1538-4357/aaa24e`](http://doi.org/10.3847/1538-4357/aaa24e)

(ref: 2021Comrie_CARTA) Comrie, A., Wang, K.-S., Hsu, S.-C., et al. 2021, Astrophysics Source Code Library, ascl:2103.031. <https://ui.adsabs.harvard.edu/abs/2021ascl.soft03031C>

(ref: 2019Dartois_CR_sputtering) Dartois, E., Chabot, M., Bacmann, A., et al. 2020, Astronomy and Astrophysics, 634, A103, doi: [`10.1051/0004-6361/201936934`](http://doi.org/10.1051/0004-6361/201936934)

(ref: 2001Dickens_TMC1) Dickens, J. E., Langer, W. D., & Velusamy, T. 2001, The Astrophysical Journal, 558, 693, doi: [`10.1086/322292`](http://doi.org/10.1086/322292)

(ref: 2020Dutta_ALMASOP) Dutta, S., Lee, C.-F., Liu, T., et al. 2020, ApJS, 251, 20, doi: [`10.3847/1538-4365/abba26`](http://doi.org/10.3847/1538-4365/abba26)

(ref: 2024Fielder_G205M3) Fielder, S. D., Kirk, H., Dunham, M. M., & Offner, S. S. R. 2024, The Astrophysical Journal, 968, 10, doi: [`10.3847/1538-4357/ad3d56`](http://doi.org/10.3847/1538-4357/ad3d56)

(ref: 2007Garrod_reactive-desorption) Garrod, R. T., Wakelam, V., & Herbst, E. 2007, Astronomy and Astrophysics, 467, 1103, doi: [`10.1051/0004-6361:20066704`](http://doi.org/10.1051/0004-6361:20066704)

(ref: 2022Ha_turbulence_clouds) Ha, T., Li, Y., Kounkel, M., et al. 2022, The Astrophysical Journal, 934, 7, doi: [`10.3847/1538-4357/ac76bf`](http://doi.org/10.3847/1538-4357/ac76bf)

(ref: 2001_Hartmann) Hartmann, L., Ballesteros-Paredes, J., & Bergin, E. A. 2001, The Astrophysical Journal, 562, 852, doi: [`10.1086/323863`](http://doi.org/10.1086/323863)

(ref: 2009Herbst_COM_review) Herbst, E., & van Dishoeck, E. F. 2009, Annual Review of Astronomy and Astrophysics, Vol 47, 47, 427, doi: [`10.1146/annurev-astro-082708-101654`](http://doi.org/10.1146/annurev-astro-082708-101654)

(ref: 2024Hirano_G208.68-19.20N2_dense) Hirano, N., Sahu, D., Liu, S.-Y., et al. 2024, The Astrophysical Journal, 961, 123, doi: [`10.3847/1538-4357/ad09e2`](http://doi.org/10.3847/1538-4357/ad09e2)

(ref: 2023Hsu_ALMASOP) Hsu, S.-Y., Liu, S.-Y., Johnstone, D., et al. 2023, The Astrophysical Journal, 956, 120, doi: [`10.3847/1538-4357/acefcf`](http://doi.org/10.3847/1538-4357/acefcf)

(ref: 2022Kalvans_desorption) Kalvāns, J., & Silsbee, K. 2022, Monthly Notices of the Royal Astronomical Society, 515, 785, doi: [`10.1093/mnras/stac1792`](http://doi.org/10.1093/mnras/stac1792)

(ref: 2017Keown_CepheusL1251) Keown, J., Di Francesco, J., Kirk, H., et al. 2017, The Astrophysical Journal, 850, 3, doi: [`10.3847/1538-4357/aa93ec`](http://doi.org/10.3847/1538-4357/aa93ec)

(ref: 2000Klessen_model_turbulence) Klessen, R. S., Heitsch, F., & Mac Low, M.-M. 2000, The Astrophysical Journal, 535, 887, doi: [`10.1086/308891`](http://doi.org/10.1086/308891)

(ref: 1981Larson_turbulence) Larson, R. B. 1981, Monthly Notices of the Royal Astronomical Society, 194, 809, doi: [`10.1093/mnras/194.4.809`](http://doi.org/10.1093/mnras/194.4.809)

(ref: 2004Lazarian_review) Lazarian, A., & Cho, J. 2004, Astrophysics and Space Science, 292, 29, doi: [`10.1023/B:ASTR.0000044998.74603.91`](http://doi.org/10.1023/B:ASTR.0000044998.74603.91)

(ref: 2021Li_ORION2) Li, P., Cunningham, A., Gaches, B., et al. 2021, The Journal of Open Source Software, 6, 3771, doi: [`10.21105/joss.03771`](http://doi.org/10.21105/joss.03771)

(ref: 2019Li_ORION2) Li, P. S., & Klein, R. I. 2019, Monthly Notices of the Royal Astronomical Society, 485, 4509, doi: [`10.1093/mnras/stz653`](http://doi.org/10.1093/mnras/stz653)

(ref: 2012Li_ORION2) Li, P. S., Martin, D. F., Klein, R. I., & McKee, C. F. 2012, The Astrophysical Journal, 745, 139, doi: [`10.1088/0004-637X/745/2/139`](http://doi.org/10.1088/0004-637X/745/2/139)

(ref: 2015Li_ORION2) Li, P. S., McKee, C. F., & Klein, R. I. 2015, Monthly Notices of the Royal Astronomical Society, 452, 2500, doi: [`10.1093/mnras/stv1437`](http://doi.org/10.1093/mnras/stv1437)

(ref: 1999Maclow_driving) Mac Low, M.-M. 1999, ApJ, 524, 169, doi: [`10.1086/307784`](http://doi.org/10.1086/307784)

(ref: 2007McKee_linewidthsize) McKee, C. F., & Ostriker, E. C. 2007, ARA&A, 45, 565, doi: [`10.1146/annurev.astro.45.051806.110602`](http://doi.org/10.1146/annurev.astro.45.051806.110602)

(ref: casa:2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, Vol. 376, San Francisco, Astronomical Society of the Pacific (ASP Conference Series)

(ref: 2023Nakai_CH3OH_formation) Nakai, Y., Sameera, W. M. C., Furuya, K., et al. 2023, The Astrophysical Journal, 953, 162, doi: [`10.3847/1538-4357/accf95`](http://doi.org/10.3847/1538-4357/accf95)

(ref: 2016Ohashi_TUKH122_turbulence) Ohashi, S., Tatematsu, K., Sanhueza, P., et al. 2016, Monthly Notices of the Royal Astronomical Society, 459, 4130, doi: [`10.1093/mnras/stw856`](http://doi.org/10.1093/mnras/stw856)

(ref: 1999_Padoan) Padoan, P., & Nordlund, A. 1999, The Astrophysical Journal, 526, 279, doi: [`10.1086/307956`](http://doi.org/10.1086/307956)

(ref: astropy:2018) Price-Whelan, A. M., Sipőcz, B. M., Günther, H. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2021Sahu_ALMASOP_presstellar) Sahu, D., Liu, S.-Y., Liu, T., et al. 2021, The Astrophysical Journal, 907, L15, doi: [`10.3847/2041-8213/abd3aa`](http://doi.org/10.3847/2041-8213/abd3aa)

(ref: 2023Sahu_ALMASOP_prestellar) Sahu, D., Liu, S.-Y., Johnstone, D., et al. 2023, The Astrophysical Journal, 945, 156, doi: [`10.3847/1538-4357/acbc26`](http://doi.org/10.3847/1538-4357/acbc26)

(ref: 2020Scibelli_ColdCoresTaurus_COMs) Scibelli, S., & Shirley, Y. 2020, The Astrophysical Journal, 891, 73, doi: [`10.3847/1538-4357/ab7375`](http://doi.org/10.3847/1538-4357/ab7375)

(ref: 2024Scibelli_Perseus_COM) Scibelli, S., Shirley, Y., Megías, A., & Jiménez-Serra, I. 2024, arXiv e-prints, arXiv:2408.11613, doi: [`10.48550/arXiv.2408.11613`](http://doi.org/10.48550/arXiv.2408.11613)

(ref: 1987_Shu) Shu, F. H., Adams, F. C., & Lizano, S. 1987, Annual Review of Astronomy and Astrophysics, 25, 23, doi: [`10.1146/annurev.aa.25.090187.000323`](http://doi.org/10.1146/annurev.aa.25.090187.000323)

(ref: 2015Soma_TMC1) Soma, T., Sakai, N., Watanabe, Y., & Yamamoto, S. 2015, The Astrophysical Journal, 802, 74, doi: [`10.1088/0004-637x/802/2/74`](http://doi.org/10.1088/0004-637x/802/2/74)

(ref: 2017Spezzano_L1544_ChemStructure) Spezzano, S., Caselli, P., Bizzocchi, L., Giuliano, B. M., & Lattanzi, V. 2017, Astronomy and Astrophysics, 606, A82, doi: [`10.1051/0004-6361/201731262`](http://doi.org/10.1051/0004-6361/201731262)

(ref: 2017Vasyunin_reactive-desorption) Vasyunin, A. I., Caselli, P., Dulieu, F., & Jiménez-Serra, I. 2017, The Astrophysical Journal, 842, 33, doi: [`10.3847/1538-4357/aa72ec`](http://doi.org/10.3847/1538-4357/aa72ec)

(ref: 2013Vasyunin_reactive-desorption) Vasyunin, A. I., & Herbst, E. 2013, The Astrophysical Journal, 769, 34, doi: [`10.1088/0004-637X/769/1/34`](http://doi.org/10.1088/0004-637X/769/1/34)

(ref: 2021Wakelam_CR_sputtering) Wakelam, V., Dartois, E., Chabot, M., et al. 2021, Astronomy and Astrophysics, 652, A63, doi: [`10.1051/0004-6361/202039855`](http://doi.org/10.1051/0004-6361/202039855)

(ref: 2016Yamamoto_book) Yamamoto, S. 2016, Introduction to Astrochemistry: Chemical Evolution from Interstellar Clouds to Star and Planet Formation (Springer Japan). <https://books.google.com.tw/books?id=Q0sbswEACAAJ>

</paper>

Write the methods card for this paper.