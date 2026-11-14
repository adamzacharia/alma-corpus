# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...988..111I\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...988..111I",
 "title": "The Detection of Spatially Resolved Protostellar Outflows and Episodic Jets in the Outer Galaxy",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Ikeda, Toki",
 "n_authors": 8,
 "arxiv_id": "2506.08601",
 "doi": "10.3847/1538-4357/ade235",
 "alma_projects_linked_by_archive": [
  "2022.1.01270.S"
 ]
}
```

Paper text:
<paper>
# The detection of spatially resolved protosteller outflows and episodic jets in the outer Galaxy

## Abstract

We present the first detection of spatially resolved protostellar outflows and jets in the outer Galaxy. We observed five star-forming regions in the outer Galaxy (Sh 2–283, NOMF05-16/19/23/63; galactocentric distance = 15.7–17.4 kpc) with the Atacama Large Millimeter/submillimeter Array (ALMA). Towards Sh 2–283, we have detected distinct outflow ($\sim$5–50 km s$^{-1}$) and jet components ($\sim$50–100 km s$^{-1}$) associated with the protostar in CO(3–2) emission. The outflows and jets are well-collimated, with the jets exhibiting multiple bullet structures. The position-velocity diagram along the CO flow axis shows two characteristic structures: (a) the flow velocity which linearly increases with the position offset from the core center (Hubble-like flow), and (b) continuous velocity components of the periodical flows (spine-like structures), which may indicate the episodic mass-ejection event. The time intervals of the mass-ejection events are estimated to be 900–4000 years based on the slopes of these spine-like structures. These characteristics align with those of nearby protostellar systems, indicating that early star formation in low-metallicity environments, such as the outer Galaxy, resembles that in the inner Galaxy. In contrast to the physical similarities, the $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio in the jet bullet appears to be lower than that measured in the low-mass protostellar sources in the inner Galaxy. This may indicate the different shock chemistry or different dust composition in the outer Galaxy source, although non-LTE effects could also affect the observed low $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio. We also report the new detection of the other 4 outflow sources in the outer Galaxy.

# Introduction

Since its first discovery by (cite: snell1980), protostellar outflows have been universally detected toward star-forming regions (cite: Bally2016). Protostars grow through mass-accretion processes, and protostellar outflows are believed to play a crucial role in removing the excess angular momentum generated by the accretion process from the protostellar envelope.

Observations of protostellar systems suggest that mass ejection phenomena are composed of multiple velocity components: jets and outflows. Jets ($\sim$50–200 km s$^{-1}$ relative to the systemic velocity) are often detected as episodic flows (a.k.a. bullets or knots) and show collimated structures (cite: Santiago2009). Such high velocity jets are thought to be originated from the protostellar inner envelope and bullet structures are possibly related to the periodic mass-accretion events (cite: Matsushita2019; Dutta2022; Fischer2023; Dutta2024; Takahashi2024). Thus, jets would be directly related to the mass-accretion rate of the protostar and its evolution processes (cite: Arce2007; Bally2016). On the other hand, outflows ($\sim$ 10–50 km s$^{-1}$) usually show continuous and wide opening angle flows (cite: Santiago2009; Hirano2010).

Such outflow and jet structures have been detected by (sub)millimeter, infrared, and optical observations especially toward the low-mass protostellar sources (cite: bachiller90; Bac96; Lee2000; Hirano2010; Dutta2022; Takami2023; Omura2024; Dutta2024; Pyo2024; Takahashi2024). For high-mass protostars, the number of samples of such jet components is still limited (cite: Qiu2009; Torrelles2011; Cheng2019; Zinchenko2020; Zinchenko2021; Zinchenko2024). This would be due to their short existing time in the protostellar phase, limited sensitivities, and angular resolution because of their large distance from us.

The effects of environmental factors (e.g., metallicity) on the origin and driving mechanisms of outflows and jets have not been thoroughly investigated. Because the cosmic metallicity is increasing with the time evolution of the Universe, observing protostellar cores in low-metallicity environments is crucial to understand the star formation and chemical evolution processes in the past Milky Way or those in high-redshift galaxies (cite: Balestra2007; Rafelski2012; Delgado2019). Atacama Large Millimeter/submillimeter Array (ALMA) enables us to spatially resolve the protostellar cores ($\sim$0.1 pc scale) located in distant low-metallicity environments such as the Large Magellanic Cloud (LMC), the Small Magellanic Cloud (SMC), and the outer Galaxy.

Recent ALMA observations have detected massive protostellar cores associated with outflows in these regions (cite: Fukui2015; Shimonishi2016; Shimonishi2023; Tokuda2022; Tok25). Those with compact (size $\lesssim$0.1 pc), dense ($n_{\rm{H_2}}$ $\gtrsim$10$^6$ cm$^3$), and high-temperature (T $\gtrsim$100 K) molecular gas (i.e. hot molecular core) are also detected (cite: Shimonishi2016; Shimonishi2020; Shimonishi2021; Shimonishi2023; Sewilo2018; Sewilo2022; Gol24).

James Webb Space Telescope (JWST) is also a powerful telescope for observing outflows in distant low-metallicity environments. Based on JWST observations, (cite: Izumi2024) detected several outflow structures in star-forming regions in the outer Galaxy with a spatial resolution of 1000 au. These observations indicate that the physical and chemical events at the early stage of star formation, such as the launching of outflows and the emergence of hot cores, may be ubiquitous even in low-metallicity environments, although the number of samples is still limited.

While outflows have been detected in low-matellicity environments, their jet components have not been detected so far. (cite: Shimonishi2021) detected high-velocity SiO lines toward a protostellar source in the outer Galaxy, WB89-789 SMM2. It showed the symmetrical structure both in the spectra and the integrated intensity map of each red- and blue-shifted component. However, the detailed flow structures were not spatially resolved due to the insufficient angular resolution, and also the major outflow tracer, CO, was not covered by the observations. Hence, there is no sample of spatially resolved protostellar jets in low-metallicity environments, highlighting the need for high-resolution studies in such regions.

In this paper, we report the first detection of spatially resolved molecular outflows including their jet components in the outer Galaxy based on ALMA observations toward the star-forming region, Sharpless 2-283 (hereafter Sh 2–283). In addition, we also report the detection of CO outflows in the other 4 protostellar sources in the outer Galaxy. In Section [2](#sec_tarobsred), we describe the observation details and the data reduction. The observational results and analysis of the detected outflows and jets are presented in Section [3](#sec_res). The morphology, dynamical parameters, driving mechanisms, and chemical properties of the outflows and jets are discussed in Section [4](#sec_dis). The summary of this paper is given in Section [5](#sec_sum).

# Targets, Observations, and data reduction

## Targets

The target star-forming region is Sh 2–283. This region is known as a H$_\mathrm{II}$ region located in the outer Galaxy (cite: Fich1991). Based on the model A5 in (cite: Reid2014), the kinematic distance of Sh 2–283 is estimated to be 7.2 kpc, which corresponds to the galactocentric distance ($D_\mathrm{GC}$) of 15.2 kpc.

According to the astrometric data of a nearby cluster member (ALS 18674) in the Gaia Early Data Release 3 (cite: Gaia2021; Bra19), the distance to Sh 2–283 is estimated to be 7.9$^{+1.2}_{-1.1}$ kpc, which corresponds to the galactocentric distance of 15.7$^{+1.1}_{-0.9}$ kpc. The distance was directly derived from the parallax (0.1269759 mas), and the parallax bias was corrected following the method described in (cite: Lindegren2021). In this paper, we use the distance value derived from the Gaia data for determining dynamical properties. The metallicity of Sh 2–283 is estimated to be approximately 30 $\%$ of the solar value based on the optical spectroscopy of the associated H$_\mathrm{II}$ region (cite: Fer17). Moreover, the other 4 star-forming regions (cite: Nakagawa2005) were separately covered in our ALMA observations. Although the metallicities of these sources have not been measured, they are expected to be 20-30 $\%$ of the solar value based on the relation between the galactocentric distance and metallicity (cite: Are21).

Toward these regions, we observed in total 16 protostar candidates with ALMA. Information of the observed sources is summarized in Table [\[ta_source_prop\]](#ta_source_prop). For Sh 2–283 region, protostar candidates were selected by using the near-infrared data from the UKIDSS survey of the UKIRT 3.8 m telescope (cite: Lucas2008). For the other regions, a near-infrared imaging survey was conducted with the Gemini–South 8.1m telescope in Chile (Proposal ID: S22A-125, PI: N. Izumi) and IRSF 1.4m telescope in South Africa, whose details will be presented in a future paper (Izumi et al. in prep.). We have selected 11 reddened sources with \[H\] – \[K\] $>$ 1.3 mag, where \[H\] and \[K\] indicate H-band (1.65 $\mu$m) and K-band (2.16 $\mu$m) magnitude. Such a near-infrared color is consistent with theoretically-predicted colors of embedded protostars (cite: Rob06). We have also selected additional 4 sources (Sh 2–283-3, Sh 2–283-4, Sh 2–283-5, and NOMF05-19–4), whose \[H\] – \[K\] values are less than the above threshold or very faint in K-band, but they are very bright in mid-infrared and have \[K\] – \[22 $\mu$m\] $>$8 mag, according to the (cite: Wri10). Although WISE 22 $\mu$m data may be contaminated by nearby sources due to its low spatial-resolution (12$\ensuremath{''}$ at 22 $\mu$m), such mid-infrared bright sources would potentially indicate the presence of Class I protostars. In addition, we included the position of NOMF05-16–1, because high-velocity CO($J$ = 2–1) components were detected in previous ALMA mapping observations towards the whole NOMF05-16 region (Izumi et al. in prep.). The location and near-infrared color composite images of the targets are shown in Appendix [6](#sec_position).

## Observations

All data used in this work were acquired by ALMA as a Cycle 9 program (2022.1.01270.S, PI: T. Shimonishi). The band 7 receiver was employed to observe molecular emission lines (such as $^{12}$CO($J$ = 3–2), HCO$^+$($J$ = 4–3), SiO($J$ = 8–7), CH$_3$OH, SO$_2$, and SO) and the 0.87-mm continuum. Five spectral windows (SPWs) of the correlator were used in the frequency division mode. The channel spacing for all SPWs was set to 976.6 kHz. The two SPWs with a bandwidth of 0.938 GHz cover the sky frequencies of 344.038–344.976 and 344.978–345.916 GHz. The three SPWs were set to cover the sky frequencies of 345.919–347.794, 346.169–358.044, and 356.961–358.836 GHz, in which the bandwidth was 1.875 GHz. Five protostar candidates located in the Sh 2–283 star-forming region were separately observed in October 2022. The antenna configuration was C-2, resulting in a minimum and maximum baseline length of 15 m and 313 m, respectively. The on-source time per source was 27.2 minutes. The observations for Sh 2–283 were conducted in three execution blocks. During the observation period, 45 antennas were operated except for one execution, in which 42 antennas were used. The bandpass and flux calibrators for protostar candidates in Sh 2–283 were J0510+1800 and J0750+1231, and the phase calibrator was J0641-0320.

NOMF05-63–1 was observed in December 2022. The 45 antennas with the antenna configuration of C-3 (minimum and maximum baseline length of 15 m and 500 m, respectively) were used. The on-source time for NOMF05-63–1 was 25.8 minutes. The bandpass/flux and phase were calibrated with J0811-4929 and J0811-4929, respectively. The other observations toward the NOMF05-16, 19, and 23 region were carried out in December 2022 for the rest 8 protostar candidates using 46 antennas with the C-3 configuration (minimum and maximum baseline length of 15 m and 500 m, respectively). The on-source time for each source was 24.3 minutes. The bandpass/flux calibrators of J1037-2934 and J0519-4546 and the phase calibrator of J0828-3731 were used for these targets.

The observations and resultant image properties are summarized in Table [1](#tab_Obs).

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source Name | RA$^\mathrm{a}$ | Dec.$^\mathrm{a}$ | $D^\mathrm{b}$ | $D_\mathrm{GC}^\mathrm{b}$ | \[$K$\] | \[$H$\]-\[$K$\] | $V_\mathrm{sys}^\mathrm{c}$ | Outflow$^\mathrm{d}$ | Submm. Cont.$^\mathrm{e}$ |  |
|  | (J2000.0) | (J2000.0) | (kpc) | (kpc) | (mag) | (mag) | (km s$^{-1}$) | (Y/N) | (Y/N) |  |
| Sh 2–283–1a SMM1 | 06:38:29.66 | 0:44:40.73 | 7.9 | 15.7 | 15.6 | 1.9 | 53.2 | Y | Y |  |
| Sh 2–283–1b | 06:38:29.60 | 0:44:41.25 | 7.9 | 15.7 | 15.9 | 1.7 | 53.2 | N | N |  |
| Sh 2–283–1c | 06:38:29.38 | 0:44:36.25 | 7.9 | 15.7 | 15.2 | 1.5 | 53.2 | N | N |  |
| Sh 2–283-2 | 06:38:30.14 | 0:44:57.95 | 7.9 | 15.7 | 16.4 | 1.5 | 51.9 | N | Y |  |
| Sh 2–283-3 | 06:38:27.83 | 0:44:42.20 | 7.9 | 15.7 | 14.0 | 0.7$^\mathrm{f}$ | 47.5 | N | Y |  |
| Sh 2–283-4 | 06:38:27.83 | 0:44:42.25 | 7.9 | 15.7 | 12.7 | 0.5$^\mathrm{f}$ | 47.5 | N | Y |  |
| Sh 2–283-5 | 06:38:28.60 | 0:44:25.00 | 7.9 | 15.7 | 14.7 | 1.1$^\mathrm{f}$ | 45.4 | N | Y |  |
| NOMF05-16–1 | 08:03:37.95 | -37:08:06.38 | 12.8 | 17.3 | – | – | 107.4 | Y | N |  |
| NOMF05-19–1 | 08:06:31.80 | -37:29:52.43 | 12.7 | 17.1 | 16.3 | 1.4 | 39.5 | N | Y |  |
| NOMF05-19–2 | 08:06:33.78 | -37:30:14.27 | 12.7 | 17.1 | 14.7 | 2.9 | 38.1 | N | N |  |
| NOMF05-19–3 | 08:06:33.17 | -37:29:49.40 | 12.7 | 17.1 | 15.3 | 2.3 | 35.5 | N | Y |  |
| NOMF05-19–4 | 08:06:31.80 | -37:29:52.57 | 12.7 | 17.1 | 11.5 | 0.8$^\mathrm{f}$ | 36.6 | N | Y |  |
| NOMF05-23–1 | 08:05:33.01 | -39:09:24.61 | 13.2 | 17.4 | 14.4 | 1.4 | 108.4 | Y | Y |  |
| NOMF05-23–2 | 08:05:33.87 | -39:09:24.97 | 13.2 | 17.4 | 14.1 | 1.7 | 109.0 | N | N |  |
| NOMF05-23–3 | 08:05:34.81 | -39:09:16.85 | 13.2 | 17.4 | 15.6 | 1.3 | 105.7 | Y | Y |  |
| NOMF05-63–1 | 08:29:53.20 | -45:55:09.63 | 14.1 | 17.3 | 10.3 | 1.7 | 110.3 | Y | Y |  |

: Source Information

Table notes: See Section [2.1](#sec_tar) for the details of the target selection. $^\mathrm{a}$The peak position of continuum emission except for Sh 2–283–1b, Sh 2–283–1c, NOMF05-16–1, NOMF05-19–2, and NOMF05-23–2. For Sh 2–283-5 and NOMF05-16–1, the position corresponds to the emission peak of HCO$^+$($J$ = 4–3) because of the no detection of continuum emission. The near-infrared source positions are tabulated for Sh 2–283–1b, Sh 2–283–1c, NOMF05-19–2, and NOMF05-23–2. $^\mathrm{b}$For sources located in Sh 2–283 , both $D$ and $D_\mathrm{GC}$ are derived with the Gaia Early Data Release 3 (cite: Gaia2021). For the other sources, we use the values derived in (cite: Nakagawa2005). $^\mathrm{c}$The systemic velocities are derived from the molecular lines for each source. $^\mathrm{d}$CO(3-2) outflow detection.

$^\mathrm{e}$ 0.87-mm continuum detection. $^\mathrm{f}$\[H\] – \[K\] $<$ 1.3 mag, but \[K\] – \[22 $\mu$m\] $>$8 mag.

+-----------+----------------+-----------+-----------+-----------+----------+-------------------+------------------------------------------------+---------------------+---------+
| Region    | Observation    | Number    | On-Source | Mean      | Number   | Baseline$^{b}$    |                                                |                     | Channel |
+:==========+:==============:+:=========:+:=========:+:=========:+:========:+:=======:+:=======:+:==============================================:+:===================:+:=======:+
| 7-8       | Date           | of        | Time      | PWV$^{a}$ | of       | L5      | L80     | Beam Size$^{c}$                                | MRS$^{d}$           | Spacing |
+-----------+----------------+-----------+-----------+-----------+----------+---------+---------+------------------------------------------------+---------------------+---------+
|           |                | Pointings | (min)     | \(mm\)    | Antennas | \(m\)   | \(m\)   | ($\ensuremath{''}$ $\times$ $\ensuremath{''}$) | ($\ensuremath{''}$) | (kHz)   |
+-----------+----------------+-----------+-----------+-----------+----------+---------+---------+------------------------------------------------+---------------------+---------+
| Sh 2–283  | 2022 Oct 27–28 | 5         | 27.2      | 0.3       | 42–45    | 25.1    | 132.7   | 0.79 $\times$ 0.68                             | 6.3                 | 976.6   |
+-----------+----------------+-----------+-----------+-----------+----------+---------+---------+------------------------------------------------+---------------------+---------+
| NOMF05-16 | 2022 Dec 29    | 1         | 24.3      | 0.3       | 46       | 33.0    | 220.6   | 0.61 $\times$ 0.50                             | 4.8                 | 976.6   |
+-----------+----------------+-----------+-----------+-----------+----------+---------+---------+------------------------------------------------+---------------------+---------+
| NOMF05-19 | 2022 Dec 29    | 4         | 24.3      | 0.3       | 46       | 33.1    | 220.8   | 0.60 $\times$ 0.49                             | 4.8                 | 976.6   |
+-----------+----------------+-----------+-----------+-----------+----------+---------+---------+------------------------------------------------+---------------------+---------+
| NOMF05-23 | 2022 Dec 29    | 3         | 24.3      | 0.3       | 46       | 32.8    | 219.0   | 0.61 $\times$ 0.50                             | 4.8                 | 976.6   |
+-----------+----------------+-----------+-----------+-----------+----------+---------+---------+------------------------------------------------+---------------------+---------+
| NOMF05-63 | 2022 Oct 8     | 1         | 25.8      | 0.3       | 45       | 34.4    | 225.6   | 0.60 $\times$ 0.51                             | 4.8                 | 976.6   |
+-----------+----------------+-----------+-----------+-----------+----------+---------+---------+------------------------------------------------+---------------------+---------+

: Summary of ALMA Observations

Table notes: $^{a}$ Precipitable water vapor. $^{b}$ L5/L80 indicate the length that includes the 5th/80th percentile of all projected baselines. $^{c}$ The average beam size of line images. $^{d}$ Maximum Recoverable Scale.

## Data reduction

Data reduction, including calibration and imaging, was made with the Common Astronomy Software Applications package (cite: CASA2022) version 6.4.1.12. The raw data were calibrated with the pipeline script provided by the observatory for the initial data flagging, the calibration of bandpass, complex gain, flux scaling, and imaging (pipeline version 2022.2.0.64) for all sources.

The visibilities of the line emissions were made by subtracting the continuum visibilities using *uvcontsub* task in CASA. The clean images were produced using *tclean* task in CASA. The line image cubes were obtained adopting Briggs weighting with a robust parameter of 0.5 for each SPW.

For Sh 2–283–1a SMM1, since a variety of molecular emission were detected (see Figure [8](#image_spec_sum)), we performed phase self-calibration using the continuum after the calibration in order to improve the signal to noise ratio. One round of phase self-calibration was applied with the solution intervals of 60 seconds. Finally, we corrected the primary beam patterns using *impbcor* task.

The systematic error on the absolute flux was approximately 10 % according to the ALMA technical handbook [^1].

![](f1.eps)

![](f2.eps)

![](f3.eps)

![](f4.eps)

# Results and Analysis

As summarized in Table [\[ta_source_prop\]](#ta_source_prop), outflows were detected in 5 out of the 16 protostellar candidates (Sh 2–283–1a SMM1, NOMF05-16–1, NOMF05-23–1, NOMF05-23–3, and NOMF05-63–1). In this paper, we mainly focus on Sh 2–283–1a SMM1 since it is the only source which we detect the distinct jet components. The other 4 outflow sources are discussed in Section [4.4](#sec_others). The basic properties of the outflow driving sources are summarized in Table [\[ta_source_prop\]](#ta_source_prop). The information of the molecular transitions for detecting the outflows and jets is summarized in Table [2](#tab_linfo)

|          |            |                |         |     |
|:---------|:----------:|:--------------:|:-------:|:---:|
| Molecule | Transition | Rest Frequency | $E_u/k$ |     |
|          |            |     (GHz)      |  \(K\)  |     |
| CO       | $J$ = 3–2  |  345.7959899   |  33.2   |     |
| SiO      | $J$ = 8–7  |  347.3305810   |  75.0   |     |
| HCO$^+$  | $J$ = 4–3  |  356.7342230   |  42.8   |     |

: Molecular Transitions

|                    |                  |                 |        |     |
|:-------------------|:----------------:|:---------------:|:------:|:---:|
| Molecule           |  Velocity Range  | Median Velocity | Extent |     |
|                    |  (km s$^{-1}$)   |  (km s$^{-1}$)  |  (pc)  |     |
| CO($J$ = 3–2)      |                  |                 |        |     |
| Outflow–red        | \[55.7, 103.2\]  |      26.3       |  0.29  |     |
| Outflow–blue       |  \[-1.3, 50.1\]  |      28.8       |  0.36  |     |
| Jet–red            | \[103.3, 143.2\] |      70.1       |  0.33  |     |
| Jet–blue           | \[-31.0, -1.4\]  |      69.4       |  0.31  |     |
| SiO($J$ = 8–7)     |                  |                 |        |     |
| Jet–blue           | \[-24.0, -14.0\] |      72.2       |  0.08  |     |
| HCO$^+$($J$ = 4–3) |                  |                 |        |     |
| Outflow–red        |  \[55.7, 80.0\]  |      14.6       |  0.24  |     |
| Outflow–blue       |  \[25.2, 50.1\]  |      15.6       |  0.43  |     |

: Observed Properties of the Outflows and Jets in Sh 2–283–1a SMM1

Table notes: (1) -red and -blue mean the red- and blue-shifted components.\
(2) Median velocity is the relative value to the systemic velocity of the source (53.2 km s$^{-1}$).

## CO outflows and jets

We here analyze the multiple velocity components of the outflows and jets observed in Sh 2–283–1a SMM1.

Figure [1](#image_co_spec) shows the CO($J$ = 3–2) spectra extracted from the 4.0$\ensuremath{''}$ $\times$ 10.0$\ensuremath{''}$ (3.2 $\times$ 10$^4$ au $\times$ 7.9 $\times$ 10$^4$ au at 7.9 kpc from the Sun) elliptical region around the emission peak of the 0.87-mm continuum. We find that there are two components on both the red- and blue-shifted sides: the two peaks marked in yellow correspond to the outflow emission and the other two peaks marked in green correspond to the jet emission, respectively. The detailed information about the velocity regimes of the outflows and jets is summarized in Table [3](#tab_measure).

The velocity criteria for separating the core and outflow components are based on the Full Width at Tenth Maximum (FWTM = 1.8 $\times$ FWHM) of the HCO$^+$($J$ = 4–3) line profile. The FWHM of the HCO$^+$($J$ = 4–3) line was derived by performing a Gaussian fitting to the HCO$^+$ spectrum extracted from a 0.89$''$ × 0.70$''$ elliptical region centered at the peak of the 0.87-mm continuum emission. This small region was chosen to minimize contamination from the outflow wing components. This is similar to the method used by (cite: Maud2015), where the FWTM of C$^{18}$O is used to separate the core velocity components from the outflow velocity components. The velocity components larger than this FWTM are identified as outflow components. The terminal velocities of the outflows are determined by the morphology of the emission distribution and the line shape. For Sh 2–283–1a SMM1, bullet structures are appearing at the line of sight relative velocity of $V_{\rm{obs}}$ $\sim$50 km s$^{-1}$ for both red- and blue-shifted components in the channel maps, which correspond to the emission bottoms of the outflow peaks in Figure [1](#image_co_spec). The terminal velocities of the jets are determined whether the line intensity is below 3$\sigma$ of the rms noise level.

Integrated intensity map is obtained by integrating these velocity components for CO($J$ = 3–2) as shown in Figure [2](#image_co) (b).

This figure clearly shows the presence of both the bipolar outflows and jets which are often detected in nearby protostellar sources (cite: bachiller90; Lee2000; Santiago2009; Hirano2010; Tafalla2010; Matsushita2019; Łukasz2019). The orientation of the outflows and jets coincides with each other and they are seemed to be within the field of view. The red-shifted component of the jets extends toward the edge of the field of view, where the sensitivity is $\sim$3 times lower compared to the central region. Consequently, some flow components may be missed in the outer regions of the observations.

We find four jet bullets in the red-shifted side and two in the blue-shifted side.

This is the first time that such jets as well as bullet structures are detected and spatially resolved in a low-metallicity environment.

## SiO jet

In addition to CO, a jet component is also detected on the blue-shifted side with the SiO($J$ = 8–7) line (Figure [3](#image_SiO) (a)). The velocity peak of this SiO jet component ($V_{\rm{obs}}$ $\sim$70 km s$^{-1}$) well coincides with the CO blue-shifted jet as shown in this figure. The observed properties of this SiO jet component are summarized in Table [3](#tab_measure). The velocity range was derived in a similar manner to that of the CO jet (Section [3.1](#sec_line_co)). We extracted the spectra from a 0.70$''$-diameter region centered on the emission peak of the SiO jet and fitted a Gaussian profile to the extracted spectra. The velocity range of the jet component was then defined based on this fitted line profile.

SiO is thought to be produced in shocked regions through the sputtering of Si-bearing species in dust grains and chemical transformation to SiO in the gas phase (cite: Sch97_SiO). Thus, SiO is known to be a tracer of shocked gas and often traces jet components which continuously drive shocks along their paths (cite: Sch97_SiO; Nisini2007; Tafalla2010; Takahashi2024).

The coincidence in both the spatial distribution and relative velocity of the SiO jet and the CO jet components would indicate a physical association between these two components.

## HCO$^+$ Outflow

Outflow components are also detected with HCO$^+$($J$ = 4–3) on both the red- and blue-shifted lobes (Figure [4](#image_HCO)). The HCO$^+$ outflows have lower terminal velocities compared to the CO outflows (see Figure [4](#image_HCO) (a)). The distribution of these outflow components shows fragmentary structures and they seem to trace the edge of the CO outflows (see Figure [4](#image_HCO) (b)). Since the critical density ($n_{\rm{cr}}$) and upper state energy ($E_{\rm u}$) of HCO$^+$($J$ = 4–3) ($n_{\rm{cr}}$ $\sim$10$^5$ cm$^{-3}$ and $E_{\rm u}$ = 42.8 K) are relatively high compared to those of CO($J$ = 3–2) ($n_{\rm{cr}}$ $\sim$10$^3$ cm$^{-3}$ and $E_{\rm u}$ = 33.2 K), these HCO$^+$($J$ = 4–3) outflow components would trace the high density region of the CO($J$ = 3–2) outflows.

## Various molecular lines in Sh 2–283–1a SMM1

A variety of molecular species including complex organic molecules (COMs; organic molecules which consist of at least 6 atoms) are detected from the emission peak of 0.87-mm continuum (see Figure [8](#image_spec_sum)). This includes multiple high–excitation lines ($E_u$ $\geq$ 100 K) of CH$_3$OH and SO$_2$. It indicates that warm molecular gas is surrounding the protostar at the position of Sh 2–283–1a SMM1. Such a chemically-rich region is known as a hot core, which is a key signature of massive star formation activity. This is the second detection of a hot core in the outer Galaxy after WB89–789 SMM1 reported in (cite: Shimonishi2023). The detailed analyses of the chemical composition of the Sh 2–283–1a SMM1 hot core will be presented in a forthcoming paper (Ikeda et al. in prep.).

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  | Outflows |  |  | Jets |  |  |  |
| Parameters | Red | Blue | Total | Red | Blue | Total |  |  |
| Mass (M$_\ensuremath{\odot}$) | 31 | 42 | 73 | 1.9 | 1.9 | 3.8 |  |  |
| Median Velocity (km s$^{-1}$)$^a$ | 37.2 | 40.7 | – | 99.1 | 98.1 | – |  |  |
| Momentum (M$_\ensuremath{\odot}$ km s$^-1$)$^a$ | 1.1 $\times$ 10$^{3}$ | 1.7 $\times$ 10$^{3}$ | 2.8 $\times$ 10$^{3}$ | 1.8 $\times$ 10$^{2}$ | 1.8 $\times$ 10$^{2}$ | 3.6 $\times$ 10$^{2}$ |  |  |
| Dynamical Timescale (yr)$^a$ | 1.1 $\times$ 10$^{4}$ | 1.2 $\times$ 10$^{4}$ | – | 4.6 $\times$ 10$^{3}$ | 4.4 $\times$ 10$^{3}$ | – |  |  |
| Mass Loss Rate (M$_\ensuremath{\odot}$ yr$^{-1}$)$^a$ | 2.8 $\times$ 10$^{-3}$ | 3.4 $\times$ 10$^{-3}$ | 6.2 $\times$ 10$^{-3}$ | 4.0 $\times$ 10$^{-4}$ | 4.2 $\times$ 10$^{-4}$ | 8.2 $\times$ 10$^{-4}$ |  |  |
| Force (M$_\ensuremath{\odot}$ km s$^{-1}$ yr$^{-1}$)$^a$ | 0.11 | 0.14 | 0.25 | 4.0 $\times$ 10$^{-2}$ | 4.1 $\times$ 10$^{-2}$ | 8.1 $\times$ 10$^{-2}$ |  |  |
| Energy (erg)$^a$ | 4.2 $\times$ 10$^{47}$ | 6.9 $\times$ 10$^{47}$ | 1.1 $\times$ 10$^{48}$ | 1.8 $\times$ 10$^{47}$ | 1.8 $\times$ 10$^{47}$ | 3.6 $\times$ 10$^{47}$ |  |  |
| Kinetic Luminosity (erg yr$^{-1}$)$^a$ | 3.9 $\times$ 10$^{43}$ | 5.7 $\times$ 10$^{43}$ | 9.6 $\times$ 10$^{43}$ | 3.9 $\times$ 10$^{43}$ | 4.0 $\times$ 10$^{43}$ | 7.9 $\times$ 10$^{43}$ |  |  |

: Dynamical Properties of Outflows and Jets in Sh 2–283–1a SMM1

Table notes: $^a$$i$ = 45$^\circ$ is assumed.

# Discussion

## Comparison of the morphological and dynamical properties of Sh 2–283–1a SMM1 with the nearby protostellar sources

We compare the dynamical properties of the outflows and jets with CO($J$ = 3–2) in Sh 2–283–1a SMM1 with the protostellar sources located in the solar neighborhood. Since the outflows and jets are extended broadly in the field of view (see Figure [2](#image_co)), there must be some missing flux of the flow gas spread beyond the Maximum recoverable scale of the observations, resulting in underestimate the flow properties. In addition, the sensitivity at the edge of the field of view is $\sim$3 times lower than at the center, which could lead to the possibility of missing faint or diffuse components near the edge to be missed, further contributing to the underestimation.

Hence, the dynamical properties of the outflows and jets related to their flow mass (e.g., mass, momentum, energy) discussed below can be considered as lower limits.

First, we calculate the dynamical timescales ($t_{\rm{d}}$) for both the outflows and jets. $t_{\rm{d}}$ can be derived using the projected outflow length and velocity as follows: $$\begin{equation}
t_{\rm{d}} = \left(\frac{L_{\rm{obs}}}{V_{\rm{obs}}}\right)\left(\frac{\cos(i)}{\sin(i)}\right),
\label{Eq_dyn}
\end{equation}$$ where $V_{\rm{obs}}$ and $L_{\rm{obs}}$ are line of sight gas velocities and the projected length of the outflows and jets, respectively. $i$ is the inclination angle with respect to the line of sight and we here assume 45$^{\circ}$.

Although the inclination angle of Sh 2–283–1a SMM1 is unknown, the red- and blue-shifted lobes of both the outflows and jets have clear bipolar structures (Figure [2](#image_co)), which indicate that they are closer to the edge-on geometry rather than the face-on (i.e. $i \geq 40^\circ$). Note that the inclination angle affects the dynamical properties other than outflow mass. When $i$ $\geq$ 84$^\circ$, uncertainties in derived dynamical values due to the inclination angle become significant by about one order of magnitude compared to the accurate values.

The dynamical timescales of the outflows are approximately 1.2 $\times$ 10$^4$ years for the red lobe and 1.4 $\times$ 10$^4$ years for the blue lobe, with the assumption of the median flow velocity of each velocity component as the representative flow velocity of the CO($J$ = 3–2) outflows ($V_{\rm{obs}}$ = 26.3 and 28.8 km s$^{-1}$, respectively).

Under the same assumptions, the dynamical timescale of the jets is approximately 5.0 $\times$ 10$^3$ years for both the red and blue lobes, with assuming the representative flow velocities of $V_{\rm{obs}}$ = 70.1 and 69.4 km s$^{-1}$, respectively. These values are summarized in Table [3](#tab_measure).

With assuming that CO emission in both the outflow and jet components are optically thin and under the condition of the local thermodynamic equilibrium (LTE), the outflow mass ($M_{\rm{out}}$) is derived by using the following equation: $$\begin{equation}
M_{\rm out} =  2 \mu_p m_{\rm{p}} X_{\rm{CO}} \int T_{\rm{CO}}  dV,
\label{Eq_mass}
\end{equation}$$ where $\mu_p$ is mean atomic mass per H atom (1.41), $m_{\rm{p}}$ is mass of a hydrogen atom, $\int T_{\rm{CO}} dV$ is sum of integrated intensity of CO outflow, and $X_ {\rm{CO}}$ is a conversion factor of CO intensity to H$_2$ column density. Here, we use a metallicity-corrected $X_\mathrm{CO}$ of 5 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$) from (cite: Bol13). For both the outflow and jet components, we derive the dynamical properties (i.e., outflow momentum, mass loss rate, outflow force, outflow energy, and outflow kinetic luminosity) with assuming $i$ = 45$^\circ$. The derived dynamical properties for each lobe are summarized in Table [4](#ta_flow_dy). These dynamical properties are similar to those of massive protostellar sources detected in the solar neighborhood (cite: Beuther2002; Wu2004; Maud2015).

Note that CO($J$ = 3–2) with the LTE assumption is known to potentially underestimate the outflow mass, as this transition is often sub-thermally excited in outflows (cite: Ginsburg2011; Dunham2014). (cite: Ginsburg2011) conducted a non-LTE analysis using RADEX (cite: vdT07) and showed that CO($J$ = 3–2) with the LTE assumption can underestimate the outflow mass by up to 1–2 orders of magnitude compared to CO($J$ = 1–0), whose critical density is 27 times lower than that of CO($J$ = 3–2), with the gas densities of 10$^{2-4}$ cm$^{-3}$. Thus, the derived dynamical properties related to the flow mass would be underestimated by the order of 1–2. To obtain more accurate estimates of the flow properties for Sh 2–283–1a SMM1 and other newly discovered outflow sources (see Section [4.4](#sec_others)), follow-up observations using lower-excitation CO lines (i.e., $J$ = 2–1 or $J$ = 1–0) will be necessary.

Although the full spectral energy distribution (SED) of Sh 2–283–1a SMM1 is not available, we estimate its luminosity by scaling the luminosity of the LMC hot core (ST16) with its $K_s$-band magnitude (\[$K_s$\]) as conducted in (cite: Shimonishi2021). The luminosity of ST16 is determined by an infrared dataset from 1 to 1200 $\mu$m. The total luminosity of ST16 is 3.1 $\times$ 10$^5$ L$_\ensuremath{\odot}$ and \[$K_s$\] is 13.4 mag at 50 kpc. For Sh 2–283–1a SMM1, \[$K_s$\] is 15.6 mag at 7.9 kpc. With scaling the luminosity of ST16 with the \[$K_s$\] and distance, we obtain 6.7$\times$ 10$^3$ L$_\ensuremath{\odot}$ as the luminosity of Sh 2–283–1a SMM1. This value is consistent with the upper limit derived from far-infrared data obtained from the *AKARI* FIS all-sky survey (cite: Yam10). Note that this is an estimation from only one infrared data and the obtained value would have large uncertainty. Future high spatial resolution and multiwavelength observations are highly required. Moreover, we can roughly estimate the luminosity of Sh 2–283–1a SMM1 by using correlation between outflow mass and luminosity. (cite: Maud2015) performed a statistical study of protostellar outflows and they found correlations between outflow masses and luminosities (see their Figure 5). Using this correlation, the luminosity of Sh 2–283–1a SMM1 is estimated to be about 10$^3$ to 10$^5$ L$_{\ensuremath{\odot}}$. The estimated luminosity by two different methods is consistent with each other and Sh 2–283–1a SMM1 would be an intermediate- to high-mass protostellar source.

All these morphological and dynamical properties of Sh 2–283–1a SMM1 resemble those observed in nearby protostellar sources. It indicates that the driving mechanisms of outflows and jets in a low-metallicity protostellar core in the outer Galaxy are similar to those of the inner Galaxy counterparts.

![](f5.eps)

## The episodic mass-ejection events in Sh 2–283–1a SMM1

Figure [5](#im_pv) shows the position–velocity diagram (PV diagram) of Sh 2–283–1a SMM1 along the flow axis (p.a = 1.1$^\circ$). The vertical dotted lines to the horizontal axis show the positions of the jet bullets (R1, R2, R3, R4, B1, and B2) in Figure [2](#image_co). The PV diagram clearly shows that the velocity increases approximately linearly with respect to the distance from the continuum peak. This morphological characteristic in the PV diagram is commonly observed in nearby outflow sources and is often called as Hubble-like velocity structure or Hubble flow (cite: Lee2000; Hirano2010; Nony2020; Takahashi2024).

Moreover, we find several spine-like structures, which are emphasized by the solid lines (S1, S2, and S3) in Figure [5](#im_pv). S2 is connected to R3 and B1, as well as S3 is connected to R4 and B2, while S1 is not connected to any jet bullets.

These spine-like structures associated with the jet bullets would trace their entrained gas or multiple velocity components of the jets. Such distinctive structures in the PV diagram have also been confirmed in some outflow sources in nearby star-forming regions (cite: Plunkett2015; Nony2020; Takahashi2024).

(cite: Takahashi2024) observed an extremely young intermediate-mass protostellar source, MMS 1/OMC-3, and detected both the outflows and jets with CO($J$ = 2–1) and SiO($J$ = 5–4), respectively. Their PV diagram cut along the outflow axis (see their Figure 5) shows similar structures that are presented in Figure [5](#im_pv).

By comparing with numerical calculations made by (cite: Machida2019) and presented in (cite: Takahashi2024), the spine-like structures indicate the episodic mass-ejection which is related to each mass-accretion event to the central protostar.

Although the spatial resolution of this work ($\sim$5000 au) is approximately two orders of magnitude smaller than that of (cite: Takahashi2024) ($\sim$80 au), the velocity structures detected in the PV diagram are remarkably similar, suggesting that both studies trace the same phenomenon related to episodic mass-ejection events. This similarity may be attributed to the difference in dynamical timescales between the two sources. In (cite: Takahashi2024), the jets have a dynamical timescale of $\sim$50 years, which is significantly shorter than that of Sh 2–283–1a SMM1 ($t_{\rm{d}}$$\sim$4000 years). Therefore, it is plausible that such jet structures evolve over time and can remain detectable even on larger spatial scales. Furthermore, similar spine-like structures have also been identified at comparable spatial resolution ($\sim$5000 au) in nearby star-forming regions (cite: Nony2020), supporting the interpretation that episodic ejection features are observable even with the spatial resolution available in this study.

Since the inverse of the slope of the spine-like structures corresponds to their time scales, we can estimate the time intervals of the episodic mass-ejection events (jet episodicity) with the slope of each spine-like structure in Figure [5](#im_pv). The slopes of the red-shifted side of S1, S2, and S3 are 6.2, 18.8, and 33.3 km s$^{-1}$ arcsec$^{-1}$, and they correspond to the time scales of approximately 6000, 2000, and 1100 years. For the blue-shifted side of S1, S2, and S3, the slopes are 6.5, 14.0, and 30.0 km s$^{-1}$ arcsec$^{-1}$ and they correspond to the time scales of approximately 5800, 2700, and 1200 years. Thus, the time intervals of the episodic mass-ejection events for Sh 2–283–1a SMM1 are predicted to be on average 1600 years (900–4000 years). This value is comparable to those of the inner Galactic sources (cite: Nony2020).

## SiO abundance in the jet component

### Derivation of molecular column densities

Since we detect the jet components with CO and SiO lines, we can estimate the column densities of these molecular species and compare the chemical properties of the jet components with nearby jet sources. Here, we extract the spectra from a circular region (a radius of 0.35$''$) at the emission peak of the SiO jet component (see Figure [2](#image_co)). For simplicity, we assume that both the CO and SiO emission in the jet components are optically thin and under the LTE condition. We estimate the column densities by using the following formula (cite: Mangum2015): $$\begin{equation}
N_{u} = \frac{3 k \int T_{\mathrm{b}} \, dV \, g_{u} \, Q({T_{rot})}}{8 \pi^{3} \nu S \mu^{2}} \exp\left(\frac{E_{u}}{k T_{rot}}\right),
\label{Eq_col}
\end{equation}$$ where $N_u$ is the column density of the molecules in the upper state, $k$ is the Boltzmann constant, $T_\mathrm{b}$ is the brightness temperature, g$_u$ is the degeneracy of the upper state, $T_{\rm{rot}}$ is the rotational temperature, Q($T_{\rm{rot}}$) is the partition function at $T_{\rm{rot}}$, $\nu$ is the rest frequency, $S$ is the line strength, $\mu$ is the dipole moment, and $E_{\rm u}$ is the upper state energy. All the spectroscopic parameters (Q($T_{\rm{rot}}$), g$_u$, $\nu$, $\mu$, $E_{\rm u}$, and $S$) are extracted from the Cologne Database for Molecular Spectroscopy (CDMS) (cite: Muller2001; Muller2005). Since we detect only one transition for each molecule in this work, the rotational temperatures ($T_{\rm{rot}}$) of CO and SiO are unknown. We therefore estimate $T_{\rm{rot}}$ based on the literature and compare the $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio of the jet component with that of nearby outflow sources.

### Comparison of SiO abundance with nearby sources

Since we found no high-mass counterparts ($>$10$^3$ L$_{\ensuremath{\odot}}$) for comparing the $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio in the jet components. Consequently, the $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio is compared with those of low-mass sources.

A nearby low-mass protostellar source, L1448-mm (L1448), is known to have jet bullet structures (cite: bachiller90). (cite: Nisini2007) derived the rotational temperature of the SiO jet components with the multiwavelength observations. The SiO multi-line analysis was conducted (from $J = 2-1$ to $J = 11-10$), and the derived rotational temperatures and column densities are $T_{\rm{rot}}$(SiO) = 100–500 K and $N\mathrm{(SiO)}$ = 3 $\times$ 10$^{13}$ cm$^{-2}$, respectively. (cite: Tafalla2010) derived $T_{\rm{rot}}$(CO) = 11 K and $N\mathrm{(CO)}$ = 5.7 $\times$ 10$^{15}$ cm$^{-2}$ for this jet source (from $J$ = 1–0 and 2–1). From these results, the $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ of L1448 is 5 $\times$ 10$^{-3}$. Both (cite: Nisini2007) and (cite: Tafalla2010) conducted the observations using single-dish telescopes (the IRAM 30-m telescope and the James Clerk Maxwell Telescope) with a spatial resolution of $\sim$5000 au, which is comparable to this work. For a fair comparison, we assume that the rotational temperatures of the jet components of SiO and CO are 100–500 K and 11 K, respectively. Under these assumptions, we derive $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ = (1.1–3.2) $\times$ 10$^{-4}$, where $N\mathrm{(SiO)}$ = (1.9–5.2) $\times$ 10$^{12}$ cm$^{-2}$ and $N\mathrm{(CO)}$ = 2.1 $\times$ 10$^{16}$ cm$^{-2}$, respectively. This $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio is more than an order of magnitude lower than that of L1448.

(cite: Dutta2024) found 17 SiO jet driving sources in 39 protostars in the Orion molecular cloud. They derived the column densities of CO and SiO under the assumption of LTE, optically thin emission, and $T_{\rm rot}$ of 150 K for both CO and SiO. The derived $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ranges 5.3–88.4 $\times$ 10$^{-4}$ and the averaged $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ is 25.5 $\times$ 10$^{-4}$. For Sh 2–283–1a SMM1, applying the same assumption (i.e., LTE condition, optically thin emission, and $T_{\rm rot}$ of 150 K for both CO and SiO), the derived $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ is 1.7 ($\pm$ 0.6) $\times$ 10$^{-4}$. This result is close to the minimum value of (cite: Dutta2024) and about an order of magnitude lower than their average value.

The present analysis suggests the low gas-phase SiO/CO ratio in the jet bullet of Sh 2–283–1a SMM1, but the reason for this remains unclear. It is believed that energetic processes in the shock regions such as the sputtering or photolysis of dust grains help release silicon or silicon-bearing molecules into the gas-phase, leading to the efficient formation of SiO (cite: Sch97_SiO; Tab20). Since the kinematic and morphological properties of the outflows and jets in Sh 2–283–1a SMM1 are similar to those of nearby sources, we speculate that the different shock chemistry may be related to the different dust composition in a unique low-metallicity environment of the outer Galaxy.

The luminosity difference between Sh 2–283–1a SMM1 and its counterparts may also contribute to the observed variation in the $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio. As mentioned above, we cannot find the nearby high-mass protostellar sources for which both CO and SiO abundances in the jet components are measured. Since it is known that the dynamical properties of outflows have strong correlation to their luminosity (cite: Wu04; Maud2015), luminosity may affect the shock chemistry induced by outflows and jets. The luminosity of the counterparts to which we compared the $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio above is on the order of 10$^{-1}$ to 10$^{2}$ L$_{\ensuremath{\odot}}$, which is more than one order of magnitude lower than that of Sh 2–283–1a SMM1 (L $\sim$ 6.6 $\times$ 10$^3$ L$_{\ensuremath{\odot}}$, see Section [4.1](#sec_str)). We need to increase the number of high-mass outflow/jet sources to better understand the luminosity effect on the shock chemistry.

Although the $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio derived under the LTE assumption is lower than those reported for nearby sources, non-LTE calculations using RADEX yield different results. We performed non-LTE analyses for SiO($J$ = 8–7) and CO($J$ = 3–2), assuming kinetic temperatures ($T_\mathrm{kin}$) of 100–500 K and 11 K, respectively. For other input parameters, we adopted an H$_2$ density ($n(\mathrm{H_2})$) of 10$^{5}$–10$^{6}$ cm$^{-3}$, representing the typical gas density of jet bullets (cite: Nisini2007; Lefloch2015). The linewidths and peak intensities of SiO and CO were set to 8.5 and 9.1 km s$^{-1}$, and 0.15 and 1.45 K, respectively, as derived from the 0.70$''$-diameter aperture analysis described in Section [4.3.1](#sec_derive). The background temperature was set to 2.73 K.

The resultant $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio is 4.8–48$\times$10$^{-4}$ with $n(\mathrm{H_2})$ = 10$^{5}$ cm$^{-3}$, while it is 0.9–3.4$\times$10$^{-4}$ with $n(\mathrm{H_2})$ = 10$^{6}$ cm$^{-3}$. Thus, the derived $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio strongly depends on the assumed $n(\mathrm{H_2})$. When $n(\mathrm{H_2})$ = 10$^{5}$ cm$^{-3}$, the $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio is comparable to that of the nearby counterpart (L1448), whereas with $n(\mathrm{H_2})$ = 10$^{6}$ cm$^{-3}$, the value becomes similar to that of Sh 2–283–1a SMM1 under the LTE assumption. We also performed non-LTE calculations assuming a uniform $T_\mathrm{kin}$ = 150 K for both CO and SiO. In this case, the resultant $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio is 6.6$\times$10$^{-3}$ for $n(\mathrm{H_2})$ = 10$^{5}$ cm$^{-3}$, and 3.3$\times$10$^{-4}$ for $n(\mathrm{H_2})$ = 10$^{6}$ cm$^{-3}$.

These results imply that non-LTE effects should be carefully considered when interpreting molecular abundances in protostellar jets, as the $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio strongly depends on $n(\mathrm{H_2})$. Thus, caution must be exercised when directly comparing $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio derived under LTE assumptions among different sources without considering their excitation conditions. Multi-line observations of SiO and CO are necessary to understand the excitation conditions of these molecules in the jets.

## The other outflow sources in the outer Galaxy

We also detected 4 outflow sources besides Sh 2–283–1a SMM1 (Figure [6](#image_pv)). The plotted CO($J$ = 3–2) spectra in the figure are extracted from the elliptical regions that cover the outflow emitting area of each source.

The CO($J$ = 3–2) integrated intensity maps of NOMF05-16–1, 23–1, and 23–3 clearly show the bipolar structure for both the red- and blue-shifted components, while NOMF05-63–1 shows no clear bipolar structure. Although the red-shifted CO($J$ = 3–2) component of NOMF05-63–1 shows the extended structure, its blue-shifted component has the emission peak at the continuum center. Such monopolar outflows are often detected in the solar neighborhood, and they are believed to arise from various factors, such as obscuration by dense ambient material, asymmetric environments, deflection due to interaction with surrounding gas, or time-variable outflow activity (cite: Wu04; Fern2013; Louvet2018). All but NOMF05-16–1 are associated with 0.87-mm continuum point sources.

For these outflow sources, we derive the dynamical properties using the same way as in Section [4.1](#sec_str), assuming $i$ = 45$^\circ$. The derived values are summarized in Table [\[ta_othrflow_dy\]](#ta_othrflow_dy). The median velocities of these outflows ($\sim$5 to 19 km s$^{-1}$) are relatively low compared to those of Sh 2–283–1a SMM1 ($\sim$37 to 40 km s$^{-1}$).

The outflow masses vary depending on the source, and all of them are lower compared to Sh 2–283–1a SMM1. The dynamical timescales of these outflows are $\sim$10$^4$ years, consistent with those of 2–283–1a SMM1.

We do not detect any jet component and SiO emission in these 4 sources. This would be due to the insufficient sensitivity to detect the relatively low intensity emission of their jet components compared with the outflow components (see Figure [1](#image_co_spec)). Future high sensitivity and spatial resolution observations are strongly needed to investigate their jet structures or protoplanetary disks in the outer Galaxy.

![](f6.eps)

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source Name | Mass | Median | Momentum$^a$ | Dynamical | Mass Loss | Force$^a$ | Energy$^a$ | Kinetic |  |
|  |  | Velocity$^a$ |  | Timescale$^a$ | Rate$^a$ |  |  | Luminosity$^a$ |  |
|  | (M$_\ensuremath{\odot}$) | (km s$^{-1}$) | (M$_\ensuremath{\odot}$ km s$^{-1}$) | (yr) | (M$_\ensuremath{\odot}$ yr$^{-1}$) | (M$_\ensuremath{\odot}$ km s$^{-1}$ yr$^{-1}$) | (erg) | (erg yr$^{-1}$) |  |
| NOMF05-16–1 |  |  |  |  |  |  |  |  |  |
| Red | 20 | 18.7 | 3.7 $\times$ 10$^{2}$ | 3.9 $\times$ 10$^{4}$ | 5.2 $\times$ 10$^{-4}$ | 9.6 $\times$ 10$^{-3}$ | 6.9 $\times$ 10$^{46}$ | 1.8 $\times$ 10$^{42}$ |  |
| Blue | 23 | 17.0 | 3.8 $\times$ 10$^{2}$ | 5.2 $\times$ 10$^{4}$ | 4.4 $\times$ 10$^{-4}$ | 7.4$\times$ 10$^{-3}$ | 6.5 $\times$ 10$^{46}$ | 1.2 $\times$ 10$^{42}$ |  |
| Total | 45 | – | 7.6 $\times$ 10$^{2}$ | – | 9.6 $\times$ 10$^{-4}$ | 1.7 $\times$ 10$^{-2}$ | 1.3 $\times$ 10$^{47}$ | 3.0 $\times$ 10$^{42}$ |  |
| NOMF05-23–1 |  |  |  |  |  |  |  |  |  |
| Red | 2.6 | 9.1 | 2.4 $\times$ 10$^{1}$ | 5.6 $\times$ 10$^{4}$ | 4.7 $\times$ 10$^{-5}$ | 4.2 $\times$ 10$^{-4}$ | 2.1 $\times$ 10$^{45}$ | 3.8 $\times$ 10$^{40}$ |  |
| Blue | 12 | 9.6 | 1.1 $\times$ 10$^{2}$ | 3.0 $\times$ 10$^{4}$ | 3.9 $\times$ 10$^{-4}$ | 3.8 $\times$ 10$^{-3}$ | 1.1 $\times$ 10$^{46}$ | 3.6 $\times$ 10$^{41}$ |  |
| Total | 15 | – | 1.3 $\times$ 10$^{2}$ | – | 4.4 $\times$ 10$^{-4}$ | 4.2 $\times$ 10$^{-3}$ | 1.3 $\times$ 10$^{46}$ | 4.0 $\times$ 10$^{41}$ |  |
| NOMF05-23–3 |  |  |  |  |  |  |  |  |  |
| Red | 0.11 | 5.8 | 0.63 | 1.9 $\times$ 10$^{4}$ | 5.8 $\times$ 10$^{-6}$ | 3.4 $\times$ 10$^{-5}$ | 3.6 $\times$ 10$^{43}$ | 1.9 $\times$ 10$^{39}$ |  |
| Blue | 0.14 | 4.7 | 0.64 | 3.4 $\times$ 10$^{4}$ | 4.1 $\times$ 10$^{-6}$ | 1.9 $\times$ 10$^{-5}$ | 3.0 $\times$ 10$^{43}$ | 8.8 $\times$ 10$^{38}$ |  |
| Total | 0.25 | – | 1.3 | – | 9.9 $\times$ 10$^{-6}$ | 5.3 $\times$ 10$^{-5}$ | 6.6$\times$ 10$^{43}$ | 1.7 $\times$ 10$^{39}$ |  |
| NOMF05-63–1 |  |  |  |  |  |  |  |  |  |
| Red | 12 | 17.8 | 2.1 $\times$ 10$^{2}$ | 3.4 $\times$ 10$^{4}$ | 3.5 $\times$ 10$^{-4}$ | 6.3 $\times$ 10$^{-3}$ | 3.8 $\times$ 10$^{46}$ | 1.1 $\times$ 10$^{42}$ |  |
| Blue | 4.0 | 16.0 | 6.3 $\times$ 10$^{1}$ | 2.2 $\times$ 10$^{4}$ | 1.8 $\times$ 10$^{-4}$ | 2.9 $\times$ 10$^{-3}$ | 1.0 $\times$ 10$^{46}$ | 4.7 $\times$ 10$^{41}$ |  |
| Total | 16 | – | 2.7 $\times$ 10$^{2}$ | – | 5.3 $\times$ 10$^{-4}$ | 9.2 $\times$ 10$^{-3}$ | 4.8 $\times$ 10$^{46}$ | 1.5 $\times$ 10$^{42}$ |  |

: Dynamical Properties of Outflows in the other four the outer Galaxy sources

Table notes: $^a$$i$ = 45$^\circ$ is assumed.

# Summary

We report the first detection of spatially resolved protostellar outflows and jets in the outer Galaxy with the radio interferometric observations toward Sh 2–283–1a SMM1 ($D_\mathrm{GC}$ = 15.7 kpc and $Z$ = 0.3 $Z_\odot$) with ALMA. The morphology of the detected outflows and jets as well as their physical and chemical properties were discussed. We also reported the new detection of the other 4 outflow sources in the outer Galaxy ($D_\mathrm{GC}$ $\sim$ 17 kpc).

We summarized the obtained conclusions below.

1.  We have detected the outflows and jets with CO($J$ = 3–2) toward Sh 2–283–1a SMM1. The gas velocities relative to the systemic velocity are $\sim$5–50 km s$^{-1}$ for the outflows and $\sim$50–100 km s$^{-1}$ for the jets. The morphology of both the outflows and jets are well-collimated and resemble those observed in nearby protostellar systems. The jets show bullet structures, which indicate episodic launching of the jets.

    We have also detected a jet component with SiO($J$ = 8–7) and the outflow components with HCO$^+$($J$ = 4–3).

2.  The physical properties (e.g., mass, momentum, dynamical timescale, etc.) of the outflows and jets are derived from the CO($J$ = 3–2) line. According to the derived outflow mass and estimation from $K_s$-band magnitude, the luminosity of Sh 2–283–1a SMM1 would correspond to an intermediate- to high-mass protostellar sources.

3.  The PV diagram along the flow axis shows the two distinctive structures (Hubble flows and spine-like structures).

    These spine-like structures would reflect the episodic mass-ejection events with the time intervals of 900–4000 years according to the slopes of the spine-like structures.

4.  The derived $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ in the jet bullet based on the LTE analysis is one order of magnitude lower or even less than those observed in nearby star-forming regions. This would indicate the different shock chemistry in the outer Galaxy protostellar core, which may be related to the different dust composition due to its unique low-metallicity environment, although the non-LTE effect introduces significant uncertainty in the derived $N\mathrm{(SiO)}$/$N\mathrm{(CO)}$ ratio as indicated by the RADEX analyses.

5.  We also detected the 4 new outflow sources in the outer Galaxy in addition to Sh 2–283–1a SMM1, suggesting that star formation activities are ongoing in the outer Galaxy.

6.  The present results would indicate that the earliest star formation processes are not significantly different, at least physically, in a low-metallicity environment of the outer Galaxy. Future follow-up observations are highly required to investigate the smaller scale structures such as protoplanetary disks at low metallicity.

This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2022.1.01270.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work has made extensive use of the Cologne Database for Molecular Spectroscopy. This work was supported by JSPS KAKENHI grant Nos. JP20H05845, JP21H00037, and JP21H01145. Finally, we would like to thank an anonymous referee for insightful comments, which substantially improved this paper.

natexlab

(ref: Arce2007) Arce, H. G., Shepherd, D., Gueth, F., et al. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 245, doi: [`10.48550/arXiv.astro-ph/0603071`](http://doi.org/10.48550/arXiv.astro-ph/0603071)

(ref: Are21) Arellano-Córdova, K. Z., Esteban, C., Garcı́a-Rojas, J., & Méndez-Delgado, J. E. 2021, MNRAS, 502, 225, doi: [`10.1093/mnras/staa3903`](http://doi.org/10.1093/mnras/staa3903)

(ref: Bac96) Bachiller, R. 1996, ARA&A, 34, 111, doi: [`10.1146/annurev.astro.34.1.111`](http://doi.org/10.1146/annurev.astro.34.1.111)

(ref: bachiller90) Bachiller, R., Cernicharo, J., Martin-Pintado, J., Tafalla, M., & Lazareff, B. 1990, A&A, 231, 174

(ref: Balestra2007) Balestra, I., Tozzi, P., Ettori, S., et al. 2007, A&A, 462, 429, doi: [`10.1051/0004-6361:20065568`](http://doi.org/10.1051/0004-6361:20065568)

(ref: Bally2016) Bally, J. 2016, ARA&A, 54, 491, doi: [`10.1146/annurev-astro-081915-023341`](http://doi.org/10.1146/annurev-astro-081915-023341)

(ref: Beuther2002) Beuther, H., Schilke, P., Sridharan, T. K., et al. 2002, A&A, 383, 892, doi: [`10.1051/0004-6361:20011808`](http://doi.org/10.1051/0004-6361:20011808)

(ref: Bol13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: Bra19) Bragança, G. A., Daflon, S., Lanz, T., et al. 2019, A&A, 625, A120, doi: [`10.1051/0004-6361/201834554`](http://doi.org/10.1051/0004-6361/201834554)

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Cheng2019) Cheng, Y., Qiu, K., Zhang, Q., et al. 2019, ApJ, 877, 112, doi: [`10.3847/1538-4357/ab15d4`](http://doi.org/10.3847/1538-4357/ab15d4)

(ref: Delgado2019) Delgado Mena, E., Moya, A., Adibekyan, V., et al. 2019, A&A, 624, A78, doi: [`10.1051/0004-6361/201834783`](http://doi.org/10.1051/0004-6361/201834783)

(ref: Dunham2014) Dunham, M. M., Arce, H. G., Mardones, D., et al. 2014, ApJ, 783, 29, doi: [`10.1088/0004-637X/783/1/29`](http://doi.org/10.1088/0004-637X/783/1/29)

(ref: Dutta2022) Dutta, S., Lee, C.-F., Hirano, N., et al. 2022, ApJ, 931, 130, doi: [`10.3847/1538-4357/ac67a1`](http://doi.org/10.3847/1538-4357/ac67a1)

(ref: Dutta2024) Dutta, S., Lee, C.-F., Johnstone, D., et al. 2024, AJ, 167, 72, doi: [`10.3847/1538-3881/ad152b`](http://doi.org/10.3847/1538-3881/ad152b)

(ref: Fern2013) Fernández-López, M., Girart, J. M., Curiel, S., et al. 2013, ApJ, 778, 72, doi: [`10.1088/0004-637X/778/1/72`](http://doi.org/10.1088/0004-637X/778/1/72)

(ref: Fer17) Fernández-Martı́n, A., Pérez-Montero, E., Vı́lchez, J. M., & Mampaso, A. 2017, A&A, 597, A84, doi: [`10.1051/0004-6361/201628423`](http://doi.org/10.1051/0004-6361/201628423)

(ref: Fich1991) Fich, M., & Silkey, M. 1991, ApJ, 366, 107, doi: [`10.1086/169544`](http://doi.org/10.1086/169544)

(ref: Fischer2023) Fischer, W. J., Hillenbrand, L. A., Herczeg, G. J., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 355, doi: [`10.48550/arXiv.2203.11257`](http://doi.org/10.48550/arXiv.2203.11257)

(ref: Fukui2015) Fukui, Y., Harada, R., Tokuda, K., et al. 2015, ApJL, 807, L4, doi: [`10.1088/2041-8205/807/1/L4`](http://doi.org/10.1088/2041-8205/807/1/L4)

(ref: Gaia2021) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2021, A&A, 649, A1, doi: [`10.1051/0004-6361/202039657`](http://doi.org/10.1051/0004-6361/202039657)

(ref: Ginsburg2011) Ginsburg, A., Bally, J., & Williams, J. P. 2011, MNRAS, 418, 2121, doi: [`10.1111/j.1365-2966.2011.19279.x`](http://doi.org/10.1111/j.1365-2966.2011.19279.x)

(ref: Gol24) Hamedani Golshan, R., Sánchez-Monge, Á., Schilke, P., et al. 2024, arXiv e-prints, arXiv:2405.01710, doi: [`10.48550/arXiv.2405.01710`](http://doi.org/10.48550/arXiv.2405.01710)

(ref: Hirano2010) Hirano, N., Ho, P. P. T., Liu, S.-Y., et al. 2010, ApJ, 717, 58, doi: [`10.1088/0004-637X/717/1/58`](http://doi.org/10.1088/0004-637X/717/1/58)

(ref: Izumi2024) Izumi, N., Ressler, M. E., Lau, R. M., et al. 2024, AJ, 168, 68, doi: [`10.3847/1538-3881/ad4e2e`](http://doi.org/10.3847/1538-3881/ad4e2e)

(ref: Lee2000) Lee, C.-F., Mundy, L. G., Reipurth, B., Ostriker, E. C., & Stone, J. M. 2000, ApJ, 542, 925, doi: [`10.1086/317056`](http://doi.org/10.1086/317056)

(ref: Lefloch2015) Lefloch, B., Gusdorf, A., Codella, C., et al. 2015, A&A, 581, A4, doi: [`10.1051/0004-6361/201425521`](http://doi.org/10.1051/0004-6361/201425521)

(ref: Lindegren2021) Lindegren, L., Bastian, U., Biermann, M., et al. 2021, A&A, 649, A4, doi: [`10.1051/0004-6361/202039653`](http://doi.org/10.1051/0004-6361/202039653)

(ref: Louvet2018) Louvet, F., Dougados, C., Cabrit, S., et al. 2018, A&A, 618, A120, doi: [`10.1051/0004-6361/201731733`](http://doi.org/10.1051/0004-6361/201731733)

(ref: Lucas2008) Lucas, P. W., Hoare, M. G., Longmore, A., et al. 2008, MNRAS, 391, 136, doi: [`10.1111/j.1365-2966.2008.13924.x`](http://doi.org/10.1111/j.1365-2966.2008.13924.x)

(ref: Machida2019) Machida, M. N., & Basu, S. 2019, ApJ, 876, 149, doi: [`10.3847/1538-4357/ab18a7`](http://doi.org/10.3847/1538-4357/ab18a7)

(ref: Mangum2015) Mangum, J. G., & Shirley, Y. L. 2015, PASP, 127, 266, doi: [`10.1086/680323`](http://doi.org/10.1086/680323)

(ref: Matsushita2019) Matsushita, Y., Takahashi, S., Machida, M. N., & Tomisaka, K. 2019, ApJ, 871, 221, doi: [`10.3847/1538-4357/aaf1b6`](http://doi.org/10.3847/1538-4357/aaf1b6)

(ref: Maud2015) Maud, L. T., Moore, T. J. T., Lumsden, S. L., et al. 2015, MNRAS, 453, 645, doi: [`10.1093/mnras/stv1635`](http://doi.org/10.1093/mnras/stv1635)

(ref: Muller2005) Müller, H. S. P., Schlöder, F., Stutzki, J., et al. 2005, in Astrochemistry: Recent Successes and Current Challenges, ed. D. C. Lis, G. A. Blake, & E. Herbst, Vol. 231, 62

(ref: Muller2001) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49, doi: [`10.1051/0004-6361:20010367`](http://doi.org/10.1051/0004-6361:20010367)

(ref: Nakagawa2005) Nakagawa, M., Onishi, T., Mizuno, A., & Fukui, Y. 2005, PASJ, 57, 917, doi: [`10.1093/pasj/57.6.917`](http://doi.org/10.1093/pasj/57.6.917)

(ref: Nisini2007) Nisini, B., Codella, C., Giannini, T., et al. 2007, A&A, 462, 163, doi: [`10.1051/0004-6361:20065621`](http://doi.org/10.1051/0004-6361:20065621)

(ref: Nony2020) Nony, T., Motte, F., Louvet, F., et al. 2020, A&A, 636, A38, doi: [`10.1051/0004-6361/201937046`](http://doi.org/10.1051/0004-6361/201937046)

(ref: Omura2024) Omura, M., Tokuda, K., & Machida, M. N. 2024, arXiv e-prints, arXiv:2401.03086, doi: [`10.48550/arXiv.2401.03086`](http://doi.org/10.48550/arXiv.2401.03086)

(ref: Plunkett2015) Plunkett, A. L., Arce, H. G., Mardones, D., et al. 2015, Nature, 527, 70, doi: [`10.1038/nature15702`](http://doi.org/10.1038/nature15702)

(ref: Pyo2024) Pyo, T.-S., Hayashi, M., Takami, M., & Beck, T. L. 2024, ApJ, 963, 159, doi: [`10.3847/1538-4357/ad1f59`](http://doi.org/10.3847/1538-4357/ad1f59)

(ref: Qiu2009) Qiu, K., & Zhang, Q. 2009, ApJL, 702, L66, doi: [`10.1088/0004-637X/702/1/L66`](http://doi.org/10.1088/0004-637X/702/1/L66)

(ref: Rafelski2012) Rafelski, M., Wolfe, A. M., Prochaska, J. X., Neeleman, M., & Mendez, A. J. 2012, ApJ, 755, 89, doi: [`10.1088/0004-637X/755/2/89`](http://doi.org/10.1088/0004-637X/755/2/89)

(ref: Reid2014) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2014, ApJ, 783, 130, doi: [`10.1088/0004-637X/783/2/130`](http://doi.org/10.1088/0004-637X/783/2/130)

(ref: Rob06) Robitaille, T. P., Whitney, B. A., Indebetouw, R., Wood, K., & Denzmore, P. 2006, ApJS, 167, 256, doi: [`10.1086/508424`](http://doi.org/10.1086/508424)

(ref: Santiago2009) Santiago-Garcı́a, J., Tafalla, M., Johnstone, D., & Bachiller, R. 2009, A&A, 495, 169, doi: [`10.1051/0004-6361:200810739`](http://doi.org/10.1051/0004-6361:200810739)

(ref: Sch97_SiO) Schilke, P., Walmsley, C. M., Pineau des Forets, G., & Flower, D. R. 1997, A&A, 321, 293

(ref: Sewilo2018) Sewiło, M., Indebetouw, R., Charnley, S. B., et al. 2018, ApJL, 853, L19, doi: [`10.3847/2041-8213/aaa079`](http://doi.org/10.3847/2041-8213/aaa079)

(ref: Sewilo2022) Sewiło, M., Cordiner, M., Charnley, S. B., et al. 2022, ApJ, 931, 102, doi: [`10.3847/1538-4357/ac4e8f`](http://doi.org/10.3847/1538-4357/ac4e8f)

(ref: Shimonishi2020) Shimonishi, T., Das, A., Sakai, N., et al. 2020, ApJ, 891, 164, doi: [`10.3847/1538-4357/ab6e6b`](http://doi.org/10.3847/1538-4357/ab6e6b)

(ref: Shimonishi2021) Shimonishi, T., Izumi, N., Furuya, K., & Yasui, C. 2021, ApJ, 922, 206, doi: [`10.3847/1538-4357/ac289b`](http://doi.org/10.3847/1538-4357/ac289b)

(ref: Shimonishi2016) Shimonishi, T., Onaka, T., Kawamura, A., & Aikawa, Y. 2016, ApJ, 827, 72, doi: [`10.3847/0004-637X/827/1/72`](http://doi.org/10.3847/0004-637X/827/1/72)

(ref: Shimonishi2023) Shimonishi, T., Tanaka, K. E. I., Zhang, Y., & Furuya, K. 2023, ApJL, 946, L41, doi: [`10.3847/2041-8213/acc031`](http://doi.org/10.3847/2041-8213/acc031)

(ref: snell1980) Snell, R. L., Loren, R. B., & Plambeck, R. L. 1980, ApJL, 239, L17, doi: [`10.1086/183283`](http://doi.org/10.1086/183283)

(ref: Tab20) Tabone, B., Godard, B., Pineau des Forêts, G., Cabrit, S., & van Dishoeck, E. F. 2020, A&A, 636, A60, doi: [`10.1051/0004-6361/201937383`](http://doi.org/10.1051/0004-6361/201937383)

(ref: Tafalla2010) Tafalla, M., Santiago-Garcı́a, J., Hacar, A., & Bachiller, R. 2010, A&A, 522, A91, doi: [`10.1051/0004-6361/201015158`](http://doi.org/10.1051/0004-6361/201015158)

(ref: Takahashi2024) Takahashi, S., Machida, M. N., Omura, M., et al. 2024, arXiv e-prints, arXiv:2401.13204, doi: [`10.48550/arXiv.2401.13204`](http://doi.org/10.48550/arXiv.2401.13204)

(ref: Takami2023) Takami, M., Günther, H. M., Schneider, P. C., et al. 2023, ApJS, 264, 1, doi: [`10.3847/1538-4365/ac9afc`](http://doi.org/10.3847/1538-4365/ac9afc)

(ref: Tokuda2022) Tokuda, K., Zahorecz, S., Kunitoshi, Y., et al. 2022, ApJL, 936, L6, doi: [`10.3847/2041-8213/ac81c1`](http://doi.org/10.3847/2041-8213/ac81c1)

(ref: Tok25) Tokuda, K., Kunitoshi, Y., Zahorecz, S., et al. 2025, arXiv e-prints, arXiv:2501.02190, doi: [`10.48550/arXiv.2501.02190`](http://doi.org/10.48550/arXiv.2501.02190)

(ref: Torrelles2011) Torrelles, J. M., Patel, N. A., Curiel, S., et al. 2011, MNRAS, 410, 627, doi: [`10.1111/j.1365-2966.2010.17483.x`](http://doi.org/10.1111/j.1365-2966.2010.17483.x)

(ref: Łukasz2019) Tychoniec, Ł., Hull, C. L. H., Kristensen, L. E., et al. 2019, A&A, 632, A101, doi: [`10.1051/0004-6361/201935409`](http://doi.org/10.1051/0004-6361/201935409)

(ref: vdT07) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: Wri10) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868, doi: [`10.1088/0004-6256/140/6/1868`](http://doi.org/10.1088/0004-6256/140/6/1868)

(ref: Wu2004) Wu, Y., Wei, Y., Zhao, M., et al. 2004a, A&A, 426, 503, doi: [`10.1051/0004-6361:20035767`](http://doi.org/10.1051/0004-6361:20035767)

(ref: Wu04) —. 2004b, A&A, 426, 503, doi: [`10.1051/0004-6361:20035767`](http://doi.org/10.1051/0004-6361:20035767)

(ref: Yam10) Yamamura, I., Makiuti, S., Ikeda, N., et al. 2010, VizieR Online Data Catalog, II/298

(ref: Zinchenko2021) Zinchenko, I. I., Dewangan, L. K., Baug, T., Ojha, D. K., & Bhadari, N. K. 2021, MNRAS, 506, L45, doi: [`10.1093/mnrasl/slab070`](http://doi.org/10.1093/mnrasl/slab070)

(ref: Zinchenko2024) Zinchenko, I. I., Liu, S. Y., & Su, Y. N. 2024, arXiv e-prints, arXiv:2411.00116. [`https://arxiv.org/abs/2411.00116`](https://arxiv.org/abs/2411.00116)

(ref: Zinchenko2020) Zinchenko, I. I., Liu, S.-Y., Su, Y.-N., Wang, K.-S., & Wang, Y. 2020, ApJ, 889, 43, doi: [`10.3847/1538-4357/ab5c18`](http://doi.org/10.3847/1538-4357/ab5c18)

# Information of the target star-forming regions

Figure [7](#image_position) represents the positions of the target star-forming regions (panel (a)) and the near-infrared color composite images of the targets (panel (b)). In the panel (b) of this figure, the red circles indicate the positions of the targets, and the green contours show CO($J$ = 3–2) data for NOMF05-16/23/63 obtained by the Atacama Submillimeter Telescope Experiment (ASTE) observations.

![](fA1.eps)

# The detected molecular species at the core center

Figure [8](#image_spec_sum) shows the spectra of Sh 2–283–1a SMM1 which are extracted from the emission peak of 0.87-mm continuum (0.89$''$ $\times$ 0.70$''$ elliptical region). In this figure, the parentheses indicate the tentative detection.

![](fB2.eps)

[^1]: <https://almascience.nao.ac.jp/documents-and-tools/cycle11/alma-technical-handbook>

</paper>

Write the methods card for this paper.