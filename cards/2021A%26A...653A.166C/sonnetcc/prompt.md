# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...653A.166C\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...653A.166C",
 "title": "Structured velocity field in the inner envelope of B335: ALMA observations of rare CO isotopologues",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Cabedo, Victoria",
 "n_authors": 4,
 "arxiv_id": "2107.01986",
 "doi": "10.1051/0004-6361/202140754",
 "alma_projects_linked_by_archive": [
  "2016.1.01552.S"
 ]
}
```

Paper text:
<paper>
# Structured velocity field in the inner envelope of B335: ALMA observations of rare CO isotopologues

Studying Class 0 objects is very important, as it allows to characterize dynamical processes at the onset of the star formation process, and to determine the physical mechanisms responsible for the outcome of the collapse. Observations of dense gas tracers allow the characterization of key kinematics of the gas directly involved in the star-formation process, such as infall, outflow or rotation. This work aims at investigating the molecular line velocity profiles of the Class 0 protostellar object B335 and attempts to put constraints on the infall motions happening in the circumstellar gas of the object. Observations of C$^{17}$O (1-0), C$^{18}$O (1-0) and $^{12}$CO (2-1) transitions are presented and the spectral profiles are analyzed at envelope radii between 100 and 860 au. C$^{17}$O emission presents a double peaked line profile distributed in a complex velocity field. Both peaks present an offset of 0.2 to 1 km s$^{-1}$ from the systemic velocity of the source in the probed area. The optical depth of the C$^{17}$O emission has been estimated and found to be less than 1, suggesting that the two velocity peaks trace two distinct velocity components of the gas in the inner envelope. After discarding possible motions that could produce the complex velocity pattern, such as rotation and outflow, it is concluded that infall is producing the velocity field. Because inside-out symmetric collapse cannot explain those observed profiles, it is suggested that those are produced by non-isotropic accretion from the envelope into the central source along the outflow cavity walls.

# Introduction

Low-mass stars are known to form in dense molecular gas clouds. Class 0 objects represent the first stage of the star formation process, when most of the mass is still contained in the envelope surrounding the protostar ((cite: Andre1993), (cite: Andre1995)). Models of protostellar collapse ((cite: Shu1987)) suggest that it is during this phase that the circumstellar gas is transported to the central object thanks to accretion processes. During this stage, angular momentum needs to be removed from the envelope and stored in the central object or dissipated through viscous processes to allow the formation of the star. Moreover, the accretion mode, the rate at which it happens, and the duration of possible accretion episodes during this phase will determine the final stellar mass ((cite: Andre1995), (cite: Basu2004), (cite: Bate2005), (cite: Myers2012)). Therefore, studying this phase is crucial, as it allows to understand which are the kinematics and dynamics of the gas at the onset of collapse, and to determine how those affect the outcome of the star formation process.

The gas making most of the protostellar envelopes is typically probed using molecular gas line profiles, which trace the gas kinematics in the dense envelope and are used to measure gas motions such as rotation or infall. Observations of the molecular line emission from embedded protostars have been suggested to trace widespread infall signatures in the inner $\sim$ 2000 au of some protostellar envelopes ((cite: Zhou1993), (cite: Rawlings1996), (cite: DiFrancesco2001), (cite: Mottram2013)). Most of those studies rely on the detection and interpretation of the infall spectral signature known as blue asymmetry or inverse P-Cygni profile. In the center of a dense protostellar core, where gas densities become larger as the collapse proceeds ($>$ 10$^{5}$ cm$^{-3}$, (cite: Andre1995)), the large optical depth of some molecular line emission produce a self-absorbed line profile, with the dip centered on the emission at systemic velocity, where most of the circumstellar gas emits. Because the core is collapsing under the effect of gravity, line emission from dense gas tracers will present the typical blue-asymmetry line profile. Most works focused on modeling these line profiles to put constraints on protostellar infall models, rely on the assumption of a symmetrical cloud collapsing, which produces such double-peaked profile on optically thick emission, to extract key information such as central protostellar mass, infall velocities and mass accretion rates ((cite: Zhou1993), (cite: DiFrancesco2001), (cite: Evans2005), (cite: Evans2015)). However, blue-asymmetries in line profiles are not unique to infall motions. Complex gas kinematics ((cite: Maureira2017)), such as asymmetric collapse ((cite: Tokuda2014)), accretion streamers ((cite: Pineda2020), (cite: Segura-Cox2020)) or outflow-entrained gas, can produce separated velocity components on the same line-of-sight which are observed as double-peaked line profiles not caused by optical thickness.

The isolated Bok globule B335, which contains an embedded Class 0 protostar (cite: Keene1983) is located at a distance of 164.5 pc, (cite: Watson2020) and has been the prototypical object to test symmetrical collapse infall models, since blue-asymmetries were first detected in molecular emission of the source at core scales (cite: Zhou1993; Choi1995; Evans2005). Double-peaked line profiles have also been observed with interferometric observations of the molecular emission from the inner envelope ((cite: Chandler1993); (cite: Saito1999); (cite: Yen2010); (cite: Kurono2013); (cite: Evans2015)). Infall models in an optically thick line emission have attempted to compute infall mass rates ((cite: Yen2010), (cite: Evans2015), (cite: Yen2015b)), obtaining values affected by large uncertainties that range from 10$^{-7}$ M$_\odot$yr$^{-1}$ to $\sim$3$\times$10$^{-6}$ M$_\odot$yr$^{-1}$ at radii of 100-2000 au, and infall velocities from 1.5 km s$^{-1}$ to $\approx$0.8 km s$^{-1}$ at radii of $\sim$ 100 au. New models based on continuum emission and using the revised distance of 164.5 pc have determined an infall rate from the envelope to the disk of 6.2$\times$10$^{-6}$ M$_\odot$yr$^{-1}$ (Evans et al., in prep.). For the estimated age of 4$\times$10$^{4}$ yr, this implies a total mass at the center (star $+$ disk) of 0.26 M$_\odot$. The physical cause of these double peaked line profiles has been questioned, however. For example (cite: Kurono2013) pointed out that despite expecting the H$^{13}$CO$^{+}$ emission should be optically thin, the inverse p-Cygni profile and the position-velocity diagram they observe can be reproduced with models of moderately optically thick infalling gas. B335 is associated with an east-west outflow, prominently detected in $^{12}$CO  with an inclination of 10$^\circ$ on the plane of the sky and an opening angle of 45$^\circ$ ((cite: Hirano1988), (cite: Hirano1992), (cite: Yen2010)). The eastern lobe is slightly oriented on the near side ((cite: Stutz2008)) producing blueshifted emission on the eastern side and redshifted emission on the western side. While the core has been found to be slowly rotating at large scales ($>$ 2500 au) ((cite: Frerking1987), (cite: Saito1999), (cite: Yen2010), (cite: Yen2011)), no clear rotation was found at smaller radii ($<$ 1000 au) and no kinematic signature of a disk was reported down to $\sim$ 10 au ((cite: Yen2015b), (cite: Yen2018)). Recent observations of the hour-glass shaped magnetic field at small scales have suggested that B335 is an excellent candidate for magnetically regulated collapse ((cite: Maury2018)).

In this work, observations of the molecular lines C$^{17}$O (1-0) and C$^{18}$O (1-0), which trace the dense circumstellar gas of the inner envelope of B335, are presented along with the $^{12}$CO (2-1) line emission, tracing the outflow cavity. The molecular line profiles are analyzed and interpreted, giving new constraints on the gas kinematics close to the protostar.

# Observations and data reduction

Observations of the Class 0 protostellar object B335 were carried out with the ALMA interferometer during the cycle 4 observation period from October 2016 to September 2017, as part of the project 2016.1.01552.S (PI. A. Maury). In all the work, it is assumed that the centroid position of B335 is at $\alpha =$ 19:37:00.9 and $\delta =$ +07:34:09.6 in J2000 coordinates, corresponding to the peak of dust continuum obtained from high resolution maps ((cite: Maury2018)). All lines were targeted using a combination of ALMA configurations: C$^{17}$O (1-0) and C$^{18}$O (1-0) were targeted using two configurations, C40-2 and C40-5, and $^{12}$CO (2-1) was targeted using C40-1 and C40-4. Technical details of the observations are shown in Table [\[table:technicalInfo\]](#table:technicalInfo).

Preliminary analysis of the data was done with the product images delivered by ALMA to check if emission was detected and to check the shape of the line profiles. The C$^{17}$O emission was only detected in the most compact configuration (C40-2), therefore only this configuration has been used to produce C$^{17}$O and C$^{18}$O maps, while $^{12}$CO was detected in both configurations so a combination of the two data sets has been used to produce the maps. Calibration of the raw data was done using the standard script for cycle-4 ALMA data using the Common Astronomy Software Applications (CASA) version 5.6.1-8. Continuum emission was self-calibrated with CASA. Line emission was calibrated using the self-calibrated model derived from the continuum data when it was possible. Final images of the data were generated from the calibrated visibilities using the tCLEAN algorithm within CASA, using Briggs weighting with robust parameter set to 2 for C$^{17}$O and C$^{18}$O  and 1 for $^{12}$CO. After imaging, $^{12}$CO maps were smoothed to reach the same angular resolution as C$^{17}$O and C$^{18}$O. The resulting map characteristics are shown in Table [1](#table:ImageChar).

|                             |                 |                 |                |
|:---------------------------:|:---------------:|:---------------:|:--------------:|
|                             |                 |                 |                |
|         Transition          | $^{12}$CO (2-1) | C$^{17}$O (1-0) | C$^{18}$O(1-0) |
|    Rest Frequency (GHz)     |     230.53      |     112.359     |    109.782     |
|     Beam major (arcsec)     |       2.6       |       2.6       |      2.7       |
|     Beam minor (arcsec)     |       1.9       |       1.9       |      2.0       |
|            PA ()            |       88        |       88        |       88       |
| Spectral Res. (km s$^{-1}$) |      0.20       |      0.20       |      0.20      |
|       LRS\* (arcsec)        |      10.6       |      21.9       |      22.4      |
|       RMS (mJy/beam)        |     2016.9      |      10.0       |      10.7      |
|                             |                 |                 |                |

: Maps characteristics.

Largest recoverable scale computed as $\Theta_{LRS} = (0.6\lambda/B_{min})206265$ in arcsec, where $\lambda$ is the rest wavelength of the line, in m, and $B_{min}$ is the minimum baseline of the configuration, in m ((cite: ALMAc4)).

|                                                     |
|:----------------------------------------------------|
| ![image](Images/Intensity/C17O_cont_CO_outflow.pdf) |

# Results and analysis

Figure [1](#fig:C17O_intensity) shows the moment 0 of C$^{17}$O (1-0) emission in red contours. The mean radius of the 3$\sigma$ emission is 860 au, indicating that it traces the dense envelope. Top image shows in intensity the dust continuum map observed at 110 GHz, showing emission over 3$\sigma$. The bottom image shows in intensity the moment 0 of $^{12}$CO (2-1) emission. The $^{12}$CO emission probes the outflowing gas, therefore it is confirmed that the C$^{17}$O emission is tracing the envelope and it is not affected by the outflow.

In order to understand the dynamics of the gas that is being probed, the C$^{17}$O spectra were taken at every 0.5$''$ pixel of the emission cube, producing a spectral map shown on Fig. [2](#fig:lineProf_c17o). The line profile patterns show two distinct velocity components with a dip centered around the systemic velocity (8.3 km s$^{-1}$). Their respective intensities vary depending on the direction of the offset from the continuum peak, being the blue component more intense in the Eastern part of the core, while the red component is dominant in the Western part. This behavior is true for all the detected hyperfine components. A clear broadening of the line can be observed near the dust continuum emission peak, and in the North-East region part of the core. The former can be due to natural thermal broadening of the two velocity components as the temperature rises in the center of the object, while the latter might be the consequence of the overlapping of the two components due to other dynamical processes. The possibility of the dip being caused by interferometric filtering is discarded since the recovered emission size is of the order of the Largest Recoverable Scale (see Table [1](#table:ImageChar)). Moreover, because C$^{17}$O is a rare isotopologue, it is not expected to be abundant at largest scales and therefore no emission can be filtered at the systemic velocity. Figure [3](#fig:c17o_hfs_channelMaps) shows the velocity channel maps of the C$^{17}$O (1-0) emission, covering a velocity range from 7.7 to 9.1 km/s and only showing the main hyperfine component (Fig. [7](#fig:channel_maps_fullHFS) shows a range covering from 5.0 to 9.6 km/s, showing the two observed hyperfine components). It can be seen that the blue- and red-shifted emission are confined to the east and west regions, respectively, suggesting that the two components are probing gas with different dynamics.

Three independent methods have been used to investigate the origins of the C$^{17}$O spectral profiles and if the two distinct peaks could be produced by an optically thick line emission. In the following sections, the analysis of these methods and the modeling of the velocity field in the B335 inner envelope are presented.

![image](Images/LineProf/C17O_contsub_rob05_05arcsec_region_spectra.pdf)\

![image](Images/Intensity/b335_c17o10main_ch_def.pdf)\

## Line opacity estimation

The maximum opacity at the center of the source has been estimated from the H$_{2}$ column density and assuming a standard C$^{17}$O abundance using Eq. [\[eq:opacity\]](#eq:opacity) ((cite: Jansen1995)).

$$\begin{equation}
            \tau_{0} = \frac{A_{10}^{C^{17}O} c^{3}}{8\pi \nu^{3}}\frac{N_{0}^{H_{2}}[C^{17}O]}{\Delta V}
            \label{eq:opacity}
        
\end{equation}$$

Where $A_{10}^{C^{17}O}$ = 6.695 $\times$ 10$^{-8}$ s$^{-1}$ is the Einstein coefficient for the C$^{17}$O J = 1–0 transition ((cite: Hitran2017), (cite: Splatalogue2005)), $c$ is the speed of light, $\nu$ is the frequency of this transition, $N_{0}^{H_{2}}$ = 3.1 $\times$ 10$^{22}$ cm$^{-2}$ is the peak column density of H$_{2}$ in B335 at a radius of 3600 au ((cite: Launhardt2013)), \[C$^{17}$O\] = 5 $\times$ 10$^{-8}$ is the C$^{17}$O abundance relative to H$_{2}$ abundance ((cite: Thomas2008)) and $\Delta V$ $\approx$ 1 kms$^{-1}$ is the average observed linewidth for the two components together. Using these values the obtained opacity is $\tau_{0}$ = 0.77, which corresponds to an opacity typical from an optically thin line.

## Intensity ratio

Because of their similar mass and molecular structure, C$^{17}$O and C$^{18}$O should probe gas under similar physical conditions. The \[C$^{17}$O\]/\[C$^{18}$O\] isotope ratio does not appear to be affected by fractionation and, if emission from both C$^{17}$O and C$^{18}$O is associated to dense gas shielded from external ultraviolet radiation, selective photo-dissociation probably does not affect the relative abundances ((cite: vanDishoeck1988)). Thus, the only difference in the emission from these two isotopes should result from opacity effects, because C$^{18}$O is a factor of 3.6-3.9 more abundant than C$^{17}$O ((cite: Penzias1981), (cite: Jorgensen2002)). The ratio of integrated intensities is much less sensitive to linewidth effects than the ratio of peak intensity, therefore we use the latter to rule out any abundances effect on the C$^{17}$O emission.

We produced beam-matching maps for C$^{17}$O and C$^{18}$O to compare the gas at similar scales in both isotopes. The obtained synthesized beams are given in Table [1](#table:ImageChar). Intensities are integrated over the two velocity ranges of 4.8-6.2 km s$^{-1}$ and 7.4-9.4 km s$^{-1}$ for C$^{17}$O  hence taking into account the two observed hyperfine components, and 7.4-9.4 km s$^{-1}$ for C$^{18}$O. The fact that both lines emit in the same range of velocities and are spatially coincident indicates that they are probing the same reservoir of circumstellar gas.

The integrated intensity ratio was computed as W$_{C^{17}O}$/W$_{C^{18}O}$, where W$_{i}$ is the integrated intensity of each C$^{17}$O and C$^{18}$O individual spectra. Figure [4](#fig:c17o_c18o_ratio) shows the obtained integrated intensity ratio map, with values ranging from 0.15 to 0.50 and a mean value centered at 0.28. We note that the intensity ratio is quite homogeneous in most of the extension of the emission, but gets larger at the North and South-West regions. This is attributed to a line broadening of the C$^{17}$O in those regions when compared to the C$^{18}$O emission (see C$^{18}$O spectral map, Fig. [8](#fig:lineProf_c18o)). The origin of this broadening is unknown, but we attribute it to complex dynamical processes that might be taking place in these regions.

The expected ratio if both transitions are optically thin is computed as \[C$^{17}$O\]/\[C$^{18}$O\] $\approx$ 0.25, where \[C$^{17}$O\] and \[C$^{18}$O\] are respectively the C$^{17}$O and C$^{18}$O abundance with respect to H$_{2}$ (\[C$^{17}$O\] = 5 $\times 10^{-8}$ and \[C$^{18}$O\] = 2 $\times 10^{-7}$, (cite: Thomas2008)). Our observations are therefore in general agreement with the expected ratio if both transitions are optically thin. No increase of the intensity ratio is seen on the observations towards the center of the source, where opacity is expected to be higher, further confirming the later hypothesis. Note that this is also in agreement with the conclusions reached by the analysis of single-dish observations of the $\rm C^{18}O\ (2-1)$ and $\rm C^{17}O\ (2-1)$ ($\tau _{\rm C^{18}O\ (2-1)} \sim 0.8$, (cite: Evans2005)).

|                                                          |
|:---------------------------------------------------------|
| ![image](Images/Intensity/C18O_C17O_intensity_ratio.pdf) |

## Modeling of the molecular line profiles

The spectrum at each pixel has been modeled using a program that allows to fit the hyperfine structure of spectral lines with multiple velocity components (*HfS*, (cite: Estalella2017)). It also allows to compute the opacity of the line from the relative intensity of the different hyperfine components of the given transition. For every velocity component the general *HfS* procedure fits simultaneously four independent parameters: the linewidth assumed to be the same for each hyperfine component; the main line central velocity; the main line peak intensity and the optical depth. The fitting procedure samples the space parameters to find the minimum value of the fit residual $\chi^{2}$. Because the C$^{17}$O (1-0) emission is expected to be optically thin, it was attempted to model the double-peaked profiles with two velocity components, one blue- and another red-shifted. Initial expected values were introduced and the program is allowed to proceed to fit emission with a minimum signal-to-noise ratio of 3$\sigma$. The peak velocity, the linewidth and the opacity maps obtained from the fitting are shown in Fig. [5](#fig:c17o_fullmaps).

Velocity maps (top images of Fig. [5](#fig:c17o_fullmaps)) show that the two different components, blue and red-shifted, occupy generally two separated regions, at East and West offsets from the center of the source respectively, with some regions overlapping, where the double peak can be observed in the spectra. The mean average, velocity for the two components are 8.1 and 8.6 km s$^{-1}$ respectively. The velocity dispersion maps (middle images of Fig. [5](#fig:c17o_fullmaps)) show a mean velocity dispersion for the two components of 0.7 and 0.5 km s$^{-1}$, which get broader, up to 0.9$\sim$1, closer to the center of the object where the two components overlap (see central spectra in Fig. [2](#fig:lineProf_c17o)). The opacity maps (bottom images of Fig. [5](#fig:c17o_fullmaps)) show that the opacity is generally less than 1, and only goes up to 3 in some specific pixels. These larger values also have a very large error associated, of the order of the value itself, so they are not significant and are not shown in the plots. Figure [6](#fig:2comp_opacity_hist) shows the histograms for the opacity values for both fitted components. The average opacity has been estimated from the *HfS* modeling and is found to be $\tau_{bs}$ = 0.464 and $\tau_{rs}$ = 0.474, for the blue- and red-shifted components respectively, which is in concordance with the upper limit estimated before.

![image](Images/2comp_plots/2comp_plots_masked_def.pdf)\

|                                                                   |
|:------------------------------------------------------------------|
| ![image](Images/Opacity/C17O_C17O_opacity_histogram_arcsec_1.pdf) |

# Discussion

## Linewidths and kinetic temperature

The main radius probed with the C$^{17}$O emission was computed from the 3$\sigma$ contour and found to be 860 au. A region enclosing radii from 100 (about half of the FWHM beam) to 860 au has been chosen to analyze the gas kinematics. The kinetic temperature of the gas has been estimated from the formula for dust temperature in an optically thin regime assuming only central heating by the B335 protostar derived by (cite: Shirley2011). The underlying assumption is that dust and gas are expected to be in thermal equilibrium, being coupled via collisions at the densities probed here ($> 10^{5}$ cm$^{-3}$). We use Eq. [\[eq:temperature_prof\]](#eq:temperature_prof) ((cite: Evans2015)) which we adapted to the new distance of 164.5 pc.

$$\begin{equation}
            T_{\rm k}(r) = 67 \, \left[ \frac{r}{\rm 41\ au} \right]^{-0.4} \, {\rm K}
            \label{eq:temperature_prof}
        
\end{equation}$$

The gas kinetic temperature was computed for the two radii probed, with values in range of T$_{k}$(100 au) = 46 K and T$_{k}$(860 au) = 20 K. The observed linewidths obtained in the previous section have been compared with the expected thermal linewidth, given by:

$$\begin{equation}
            \Delta \nu_{th} = \sqrt{\frac{8\, \ln{2} \, k_{b} \, T_{\rm k}}{m}} \, {\rm km} \, {\rm s^{-1}}
            \label{eq:thermal_linewidth}
        
\end{equation}$$

where T$_{\rm k}$ is the gas kinetic temperature, $m$ is the molecular mass (29.01 amu for C$^{17}$O) and $k_{b}$ is the Boltzmann constant. The expected thermal linewidth for C$^{17}$O has been computed for the temperatures at the two different radii: $\Delta \rm v_{th}$(100 au) = 0.27 km s$^{-1}$ and $\Delta \rm v_{th}$ (860 au) = 0.17 km s$^{-1}$. The observed linewidths are larger than the thermal ones for both velocity components. This indicates that the observed linewidth is the result of the thermal component plus a non-thermal contribution (e.g. turbulence and large-scale motions like infall and outflow, $\rm v_{obs}^{2}$ = $\rm v_{th}^{2}$ + $\rm v_{non-th}^{2}$). The non-thermal contribution of the line has been computed for both velocity components and the results are shown in Table [2](#tab:c17o_kinetics). The non-thermal component at the inner and outer radius are indistinguishable because of the limited spectral resolution (0.2 km s$^{-1}$).

The sound speed, $c_{s}$, is in the 0.2–0.3 km s$^{-1}$ range for temperatures between 20 and 46  K and $\gamma \sim$ 7/5. This means that the non-thermal contribution to the linewidth is supersonic.

Simulations have shown that in star forming cores systematic large-scale motions (such as infall) can contribute significantly ($\sim$50%) to the non-thermal component of the linewidth (cite: Guerrero20). We can do a rough estimation of the contribution from infall, by measuring the infall velocity difference from two different radii, $\Delta\sigma = v_{ff}(r1)-v_{ff}(r2)$, where $v_{ff} (r)= \sqrt{\frac{2GM_{B335}(r)}{r}}$, G is the gravitational constant and M$_{B335}$(r) is the mass enclosed at the considered radius $r$. To compute the mass we consider that the total mass at different radii is the sum of the mass in the envelope plus the mass of the central object. The mass of the gas in the envelope contained up to a certain radius is computed by integrating the 110 GHz dust continuum emission, and using standard assumptions (see Eq. 4 in (cite: Jorgensen2007)). The maximum velocity difference along the line-of-sight would occur at the core’s center. For the two adopted radius, 860 and 100 au, the envelope mass, M$_{env}$, is $\sim$0.16 $M_\odot$ and $\sim$0.012 $M_\odot$, respectively. We also adopt a mass for the central object between 0.05 and 0.26 $M_\odot$, which are the predicted values from infall models (see (cite: Yen2015b), (cite: Evans2015), Evans et al. in prep.). Therefore, the total mass enclosed within a 100 and 860 au radii are in the 0.06–0.16 $M_\odot$ and 0.27–0.41 $M_\odot$ ranges, respectively. The estimated range of $\Delta \nu_{ff}$ is 0.46 - 1.01 km s$^{-1}$. Given the errors coming from the computation of all the previous parameters, the non-thermal contribution of the linewidth is of the same order as the broadening due to free-fall motions along the line of sight: it is hence possible that the observed velocity pattern is due to infall.

|                     |                   |                  |
|:-------------------:|:-----------------:|:----------------:|
|                     |                   |                  |
|                     | blue-shifted FWHM | red-shifted FWHM |
|                     |   (km s$^{-1}$)   |  (km s$^{-1}$)   |
|                     |                   |                  |
|   Observed total    |       0.78        |       0.56       |
| Non-thermal (100au) |       0.73        |       0.48       |
| Non-thermal (860au) |       0.76        |       0.52       |
|                     |                   |                  |

: C$^{17}$O (1-0) observed linewidth and non-thermal contributions at different radii.

## Possible origins of the observed gas motions

Our ALMA observations of the C$^{17}$O (1-0) emission suggest an optically thin emission at all scales probed by the observations (100-860 au). Overall, the spatial extent of the C$^{17}$O emission is similar to the one of the dust continuum emission, but C$^{17}$O is less peaked and decreases more smoothly with decreasing density outwards: this suggests that the gas traced with C$^{17}$O is not mostly related to the outflow cavity. The C$^{17}$O emission maximum is not coincident with the dust continuum peak position, which might suggest slight abundance variations of the C$^{17}$O at high densities close to the protostar. Nevertheless, the prominence of the double-peaked velocity pattern does not correlate with the intensity of the dust continuum emission, proving that those profiles are not due to red-shifted absorption against a strong continuum and/or C$^{17}$O source. These two velocity components thus trace distinguished gas motions. A simple isotropic inside-out envelope collapse can not easily reproduce the gas motions we observe in the B335 envelope. In this section, we discuss various hypothesis for the physical origin of the gas motions observed.

Despite being isolated, B335 is embedded in an extended molecular gas cloud of density $\sim 10^3$ cm$^{-3}$ ((cite: Frerking1987)). However, C$^{17}$O is a rare isotopologue which is mostly confined to a high-density central region and its low abundance at large-scales would prevent observing such a tenuous layer, suggesting there is no missing flux coming from large-scale C$^{17}$O emission. To confirm that this is the case, we estimated the missing flux from the C$^{18}$O (1-0) ALMA observations by comparing it with the 45 m Nobeyama data of the same transition presented in (cite: Saito1999). Our C$^{18}$O map was smoothed to match the beam size of the Nobeyama telescope, which at the frequency of this transition (109.782 GHz) is 16". We obtained the spectra on a region of one beam size around the center of B335 and transformed the flux density to brightness temperature using the Rayleigh-Jeans law. We obtained a peak temperature of T$_{\rm MB}$ = 0.79 $\pm$ 0.08 K and an integrated temperature of $\int$T$_{\rm MB} dv$ = 0.53 K km/s. This means that our ALMA observations are recovering around 14 $\%$ of the total flux detected with single-dish data. However, because C$^{17}$O is expected to be much more compact than C$^{18}$O  we expect the missing flux to be much less for the former. (cite: Frerking1987) presented single-dish data of the C$^{17}$O (1-0) transition and concluded that all their emission is coming from the center of the source in a region smaller than the beam of their telescope (1’.6 for the C$^{17}$O (1-0) transition). This extension is much smaller than the one observed for C$^{18}$O (1-0) detected in both works, which is about 4’. This is consistent with the fact that C$^{17}$O is much less abundant than C$^{18}$O, especially at large scales, and that it is mainly tracing the core and not the envelope. Therefore, we expect the missing flux of C$^{17}$O in our ALMA data to be much less, and to be recovering at least twice the recovered flux of C$^{18}$O, i.e. around 30 $\%$. We also note that while our observation might be missing flux, this should not be enough as to produce the huge dip in our data, and it can not explain the structured velocity pattern we observe in the spectral maps, since the missing flux will be at the systemic velocity and would not be able to completely absorb only one of the two components at different offsets.

A possible cause for observing blueshifted and redshifted gas motions in protostellar envelopes could be organized core rotation. Our observations do not support this hypothesis as they do not show a clear velocity gradient in the equatorial plane where rotation motions would mostly contribute to the observed velocity field. Instead, both redshifted and blueshifted velocities are observed in both the northern and southern regions (see Fig. 4). While rotation motions have only been detected at larger envelope radii in B335 ($>$ 2500 au, (cite: Saito1999); (cite: Yen2011)), we stress that the conclusion regarding the absence of small scale rotation (e.g. (cite: Yen2010)) should be further investigated using the new insights on gas motions in the envelope that our observations have uncovered.

B335 has a well-studied outflow, with its axis close to the plane of the sky and with a well defined X-shaped biconical shape in $^{12}$CO (cite: Bjerkeli2019). Although some contamination by the gas from the outflow cannot be completely ruled out, we present here arguments supporting the hypothesis that our C$^{17}$O maps can be used to study the envelope gas kinematics. C$^{17}$O is a rare isotopologue which is known to trace dense envelope gas and is not expected to be detected in more tenuous outflow cavities. The morphology of C$^{17}$O emission is very different from the one observed in typical outflow cavities tracers, such as C$_{2}$H (cite: Murillo2018) or $^{12}$CO (see bottom image in Fig. [1](#fig:C17O_intensity) and (cite: Bjerkeli2019)). Moreover, no spectral signature of outflow is observed, such as large wings observed in $^{12}$CO ((cite: Bjerkeli2019)), and the maximum velocity shift from the rest velocity remains quite small ($\pm$ 1 km s$^{-1}$). Therefore, the kinematic pattern observed in our C$^{17}$O maps cannot be produced by outflow alone, and it does provide a strong evidence of distinguished velocity contributions from the gas in the inner region of the B335 protostellar envelope.

The C$^{17}$O velocity maps in Fig. [5](#fig:c17o_fullmaps) show that the largest gas velocities are found $\sim1$$''$ from the center along the two northern outflow cavity walls, tracing gas at reverse velocities with respect to the outflow velocities. Considering the 10$^\circ$ inclination of the system, the spatial distribution of C$^{17}$O emission following closely that of the dust and other typical dense gas tracers, and the fact that the linewidths of the two velocity components are in general agreement with the expected linewidths from infall motions, the most likely hypothesis is that these high-velocity ($\pm$ 1 km s$^{-1}$) features trace accreting gas flowing along the outflow cavity walls, onto the central protostar. The peak velocities tentatively increase towards the central protostellar objects, for the features along the eastern outflow cavity walls, but no clear velocity gradient could be resolved in the current observations: additional observations with better spatial resolution may allow to test further this hypothesis. Finally, we note that the strongly redshifted emission at the North-East was already detected in ALMA C$^{18}$O observations reported by (cite: Yen2015b) (see Fig. 2 in their work).

Dust continuum emission observed with ALMA at various millimeter and sub-millimeter wavelengths all show a striking excess of dust emission associated to the outflow cavity walls. While this could be a temperature effect due to increased heating from the central protostar of these walls, it could also be a true density increase in compact features easily picked up by interferometric observations. Magnetized models of protostellar formation (for a review see (cite: Zhao2020a)) suggest cavity walls could be preferential sites to develop accretion streamers, as observed in the non-ideal magneto-hydrodynamic (MHD) models of protostellar accretion and outflow launching ((cite: Machida2014b) or Figure 8 and 9 in (cite: Tomida2012)). Indeed, these are locations where the poloidal magnetic field is mostly parallel to the inflow direction and therefore would exert less magnetic braking for material infalling along the walls. This hypothesis is also in agreement with the dust polarization observations of magnetic field lines in B335 (the redshifted gas feature we observe along the north-eastern cavity wall is associated to highly organized B-field lines aligned with the tentative gas flow), and the scenario of magnetically-regulated infall proposed in (cite: Maury2018).

We note that the observed non-thermal components of the linewidths are found to be supersonic. If the observed gas motions we detect indeed trace localized accretion motions, these could be supersonic. While the development of supersonic filamentary accretion features were reported in numerical models of protostellar formation ((cite: Padoan2005); (cite: Banerjee2006); (cite: Kuffmeier2019)), and observations suggested supersonic infall is occurring in a few protostellar envelopes at larger scales ($>1000$ au, (cite: Tobin2010); (cite: Mottram2013)), it is the first time such anisotropic supersonic infall motions are tentatively reported in the B335 inner envelope.

## Impact on the characterization of protostellar mass accretion rates

In the following, we briefly discuss the implications of our work, if the localized accretion features detected in B335 are common while remaining mostly unresolved in many observations of accreting protostars.

Self-similar solutions for analytical models of the collapse of an isothermal sphere, including only thermal pressure and gravity, predict typical mass accretion rates of the order $\sim 10^{-4}$ M$_{\odot}$ yr$^{-1}$ ((cite: Larson1969); (cite: Penston1969); (cite: Shu1977)). Turbulent models and MHD numerical models have produced slightly lower mass accretion rates $\sim 10^{-6}$–$10^{-5}$ M$_{\odot}$ yr$^{-1}$. Episodic accretion with highly variable rates (from a $\dot{M} \sim$ 10$^{-5}$ M$_{\odot}$ yr$^{-1}$ down to $\dot{M} <$ 10$^{-6}$ M$_{\odot}$ yr$^{-1}$) is often observed in both hydro and MHD numerical models of protostellar formation, in the accretion of envelope material onto the disk and the protostar itself (cite: Lee2021), and of disk material to the central growing protostar (cite: Dunham2012; Vorobyov2015).

Robust observational estimates of protostellar accretion rates are crucial to distinguish between models, but also to shed light on several open questions on star formation, since they are key quantities for our interpretation of the protostellar luminosities and of the typical duration of the main protostellar accretion phase (cite: Evans2009; Maury2011). Indeed, observations may have revealed a discrepancy between the observed protostellar bolometric luminosities, and the protostellar accretions rates: this is the so-called ‘luminosity problem’ (cite: Kenyon1990). Protostellar accretion rates derived from molecular line emission, and more particularly from the modeling of inverse p-Cygni profiles with analytical infall models, should produce luminosities 10-100 times larger than the typically observed bolometric luminosities (for a review, see (cite: Dunham2014)). Observations of the molecular line profiles in B335 (cite: Evans2005; Evans2015) have been used to fit models of protostellar infall suggesting $\dot{M} \sim 6.2 \times 10^{-6}$ M$_{\odot}$ yr$^{-1}$ (assuming an effective sound speed of 0.3 km/s, Evans et al. in prep.), although arguably these estimates are associated to large error bars. The observed bolometric luminosity of B335 lies an order of magnitude below the accretion luminosity L$_{\rm acc}$ such accretion rates should produce (cite: Evans2015): despite being a prototype for protostellar infall models, B335 also suffers from the luminosity problem.

If the ’true’ protostellar mass accretion rates stems from localized collapsing gas at small scales, potentially affected by unresolved multiple velocity components, the true linewidths associated to infalling gas feeding the growth of the protostar would be quadratically smaller than the ones measured at larger scales where these components would be entangled (or if the individual velocity components are interpreted as being part of a single velocity component with a central dip due to optically thickness). Smaller intrinsic linewidths of the infalling gas, at small radii, may result in smaller effective sound speed and hence lower mass accretion rate derived from the analytical infall models, since $\dot{M} \propto c_{\rm s}^{3}/G$. It is therefore possible that the observed bolometric luminosity of B335 is, ultimately, compatible with its accretion luminosity L$_{\rm acc}$. In the revised B335 scenario we propose here, the mass accretion rate on the protostar could be dictated by localized supersonic infall rather than by the large scale infall rate of the envelope: this may open a window to partially solve the ’luminosity problem’, although episodic vigorous accretion would probably still remain necessary to explain the relatively short statistical lifetimes for the Class 0 phase. Future observations should be used to carry out a more detailed characterization of whether a significant fraction of the final stellar mass could be fed to the central object through highly localized anisotropic infall. Recently, (cite: Pineda2020) reported the detection of an ’accretion streamer’, connecting the dense core to disk scales, and found a streamer infall rate $\sim 10^{-6}$ M$_{\odot}$ yr-1, of the same order of magnitude as the global mass accretion rate inferred from molecular line observations in B335. Hence, it is possible that many previous studies have failed to grasp the full complexity of the gas motions making up the accretion onto the central protostars. It is the large angular and spectral resolution, along with the great sensitivity of the presented ALMA observations which allowed to detect the two distinct velocity components on the line emission profiles in B335. More observations at the same small-scales and spectral resolution of optically thin emission in different protostars are needed in order to determine if these localized gas motions are common. Moreover, more refined protostellar infall models will have to be carried out in the future, to take this new small-scales into account and include more complex geometries with, e.g., asymmetric structures and preferential accretion along outflow cavities.

# Summary

ALMA observations of the C$^{17}$O emission tracing gas kinematics in the B335 envelope have been presented in this work. It is shown that the line emission exhibits widespread double-peaked profiles. From the analysis, the following conclusions have been obtained:

- Derivations of the line opacity have shown that the emission of the line is optically thin and therefore the observed double-peaked profiles cannot be produced by self-absorption. Therefore, inverse p-Cygni profiles coming from symmetrical inside-out collapse cannot fully explain the observed complex velocity field.

- After discarding filtering of large-scale emission or other types of motions, such as rotation or outflow, it is determined that only distinct gas motions contributing to the same line-of-sight could explain the observed line profiles pattern.

- Linewidth analysis have determined that the two velocity components are compatible with infall motions, and could be due to localized infall in preferential directions. The main hypothesis presented is that the collapse of the envelope onto the protostar is occurring along the equatorial plane but also along the outflow cavity walls, where the magnetic field topology is more favorable.

More observations at similar scales and spectral resolution are needed to determine if these double peaked profiles are common in protostellar objects at similar evolutionary states. Moreover, further modeling of the B335 envelope with more complex collapse models, such as anisotropic collapse, are needed to determine which is the exact physical origin of the observed velocity field.

# Acknowledgments

The authors acknowledge the very useful discussions with N. Evans and Y. Yang. This project has received funding from the European Research Council (ERC) under the European Union Horizon 2020 research and innovation program (MagneticYSOs project, grant agreement N$\ensuremath{^\circ}$ 679937). J.M.G. is supported by the grant AYA2017-84390-C2-R (AEI/FEDER, UE). This publication is based on data of ALMA data from the project 2016.1.01552.S (PI. A. Maury).

63 natexlab

(ref: Andre1995) André, P. 1995, Astrophys Space Sci, 224, 29

(ref: Andre1993) André, P., Ward-Thompson, D., & Barsony, M. 1993, ApJ, 406, 122

(ref: ALMAc4) Asayama, S., Biggs, A., de Gregorio, I., et al. 2016, ALMA Partnership

(ref: Banerjee2006) Banerjee, R., Pudritz, R. E., & Anderson, D. W. 2006, MNRAS, 373, 1091

(ref: Basu2004) Basu, S. & Jones, C. E. 2004, Mon. Not. R. Astron. Soc., 347, L47

(ref: Bate2005) Bate, M. R. & Bonnell, I. A. 2005, Mon. Not. R. Astron. Soc., 356, 1201

(ref: Bjerkeli2019) Bjerkeli, P., Ramsey, J. P., Harsono, D., et al. 2019, A&A, 631

(ref: Chandler1993) Chandler, C. J. & Sargent, A. I. 1993, ApJ, 414, L29

(ref: Choi1995) Choi, M., Evans, N. J., Gregersen, E. M., & Wang, Y. 1995, ApJ, 448, 742

(ref: DiFrancesco2001) Di Francesco, J., Myers, P. C., Wilner, D. J., Ohashi, N., & Mardones, D. 2001, ApJ, 562, 770

(ref: Dunham2014) Dunham, M. M., Stutz, A. M., Allen, L. E., et al. 2014, in Protostars and Planets VI (University of Arizona)

(ref: Dunham2012) Dunham, M. M. & Vorobyov, E. I. 2012, ApJ, 747, 52

(ref: Estalella2017) Estalella, R. 2017, Publications of the Astronomical Society of the Pacific, 129, 21

(ref: Evans2015) Evans, N. J., Di Francesco, J., Lee, J., et al. 2015, ApJ, 814, 22

(ref: Evans2009) Evans, N. J., Dunham, M. M., Jørgensen, J. K., et al. 2009, ApJ, 181, 321

(ref: Evans2005) Evans, N. J., Lee, J., Rawlings, J. M. C., & Choi, M. 2005, ApJ, 626, 919

(ref: Frerking1987) Frerking, M. A., Langer, W. D., & Wilson, R. W. 1987, ApJ, 313, 320

(ref: Hitran2017) Gordon, I. E., Rothman, L. S., Hill, C., et al. 2017, J Quant Spectrosc Ra-diat Transf, 203, 3

(ref: Guerrero20) Guerrero-Gamboa, R. & Vázquez-Semadeni, E. 2020, ApJ, 903, 136

(ref: Hirano1992) Hirano, N., Kameya, O., Kasuga, T., & Umemoto, T. 1992, ApJ, 390, L85

(ref: Hirano1988) Hirano, N., Kameya, O., Nakayama, M., & Takakuro, K. 1988, ApJ, 327, L69

(ref: Jansen1995) Jansen, D. 1995, PhD thesis, Leiden University

(ref: Jorgensen2007) Jørgensen, J. K., Bourke, T. L., Myers, P. C., et al. 2007, ApJ, 659, 479

(ref: Jorgensen2002) Jørgensen, J. K., Schöier, F. L., & van Dishoeck, E. F. 2002, A&A, 389, 908

(ref: Keene1983) Keene, J., Davidson, J. A., Harper, D. A., et al. 1983, ApJ, 274, 43

(ref: Kenyon1990) Kenyon, S. J., Hartmann, L. W., Strom, K. M., & Strom, S. E. 1990, AJ, 99

(ref: Kuffmeier2019) Kuffmeier, M., Calcutt, H., & Kristensen, L. E. 2019, A&A, 628

(ref: Kurono2013) Kurono, Y., Saito, M., Kamazaki, T., Morita, K., & Kawabe, R. 2013, ApJ, 765, 85

(ref: Larson1969) Larson, R. B. 1969, Mon. Not. R. astr. Soc., 145, 271

(ref: Launhardt2013) Launhardt, R., Stutz, A. M., Scmiedeke, A., et al. 2013, A&A, 551, A98

(ref: Lee2021) Lee, Y.-N., Charnoz, S., & Hennebelle, P. 2021, A&A, 648, A101

(ref: Machida2014b) Machida, M. N. 2014, Astrophys. J. Lett., 796, L17

(ref: Maureira2017) Maureira, M. J., Arce, H. G., Offner, S. S. R., et al. 2017, ApJ, 849, 89

(ref: Maury2011) Maury, A. J., André, P., Men’shchikov, A., Könyves, V., & Bontemps, S. 2011, A&A, 535, A77

(ref: Maury2018) Maury, A. J., Girart, J. M., Zhang, Q., et al. 2018, MNRAS, 477, 2760–2765

(ref: Mottram2013) Mottram, J. C., van Dishoeck, E. F., Schmalzl, M., et al. 2013, A&A, 558, A126

(ref: Murillo2018) Murillo, N. M., van Dishoeck, E. F., van der Wiel, M. H. D., et al. 2018, A&A, 617, A120

(ref: Myers2012) Myers, P. C. 2012, ApJ, 752, 9

(ref: Splatalogue2005) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winewisser, G. 2005, J. Mol. Struct., 215

(ref: Padoan2005) Padoan, P., Kritsuk, A., Norman, M., & Nordlund, Å. . 2005, ApJ, 622, L61

(ref: Penston1969) Penston, M. V. 1969, Mon. Not. R. astr. Soc., 144, 425

(ref: Penzias1981) Penzias, A. A. 1981, ApJ, 249, 518

(ref: Pineda2020) Pineda, J. E., D., S., Caselli, P., et al. 2020, Nat. Astron., 4, 1158–1163

(ref: Rawlings1996) Rawlings, J. M. C. 1996, Astrophys. Space Sci, 237, 299

(ref: Saito1999) Saito, M., Sunada, K., Kitamura, Y., & Hirano, N. 1999, ApJ, 518, 234

(ref: Segura-Cox2020) Segura-Cox, D. M., Schmiedeke, A., Pineda, J. E., et al. 2020, Nature, 586, 228

(ref: Shirley2011) Shirley, Y. L., Mason, B. S., Magnum, J. G., et al. 2011, ApJ, 141, 39

(ref: Shu1977) Shu, F. H. 1977, ApJ, 214, 488

(ref: Shu1987) Shu, F. H., Adams, F. C., & Lizano, S. 1987, Ann. Rev. Astron. Astrophys., 25, 23

(ref: Stutz2008) Stutz, M. A., Rubin, M., Werner, M. W., et al. 2008, ApJ, 687, 389

(ref: Thomas2008) Thomas, H. S. & Fuller, G. A. 2008, A&A, 479, 751

(ref: Tobin2010) Tobin, J. J., Hartmann, L., Looney, L. W., & Chang, H. F. 2010, ApJ, 712, 1010

(ref: Tokuda2014) Tokuda, K., Onishi, T., Saigo, K., et al. 2014, ApJ, 789, L4

(ref: Tomida2012) Tomida, K., Okuzumi, S., & Machida, M. N. 2012, ApJ, 801, 117

(ref: vanDishoeck1988) van Dishoeck, E. F. & Black, J. H. 1988, ApJ, 334, 771

(ref: Vorobyov2015) Vorobyov, E. I. & Basu, S. 2015, ApJ, 805, 115

(ref: Watson2020) Watson, D. M. 2020, Res. Notes AAS, 4, 88

(ref: Yen2015b) Yen, H. W., Takakuwa, S., Koch, P. M., et al. 2015, ApJ, 812

(ref: Yen2010) Yen, H. W., Takakuwa, S., & Ohashi, N. 2010, ApJ, 710

(ref: Yen2011) Yen, H. W., Takakuwa, S., & Ohashi, N. 2011, ApJ, 742, 57

(ref: Yen2018) Yen, H. W., Zhao, B., Koch, P. M., et al. 2018, A&A, 615, A58

(ref: Zhao2020a) Zhao, B., Caselli, P., Li, Z., et al. 2020, MNRAS, 492, 3375

(ref: Zhou1993) Zhou, S., Evans, N. J., Kömpe, C., & Walmsley, C. M. 1993, ApJ, 404, 232

# Technical details of the ALMA observations

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  |  |  |
| Config. | Date | Timerange | Center freq. | Spec. Res. | Flux cal. | Phase cal. | Bandpass cal. |
|  | (mm/dd/yy) | (hh:min:s.ms) | (GHz) | (km s$^{-1}$) |  |  |  |
|  |  |  |  |  |  |  |  |
| C40-1 | 19/03/2017 | 10:40:52.8 - 10:53:42.8 | 231.0 | 0.09 | J1751+0939 | J1851+0035 | J1751+0939 |
| C40-2 | 02/07/2017 | 15:30:38.9 - 15:49:59.2 | 110.0 | 0.08 | J1751+0939 | J1938+0448 | J1751+0939 |
| C40-4 | 21/11/2016 | 22:41:22.0 - 23:28:19.8 | 231.0 | 0.09 | J2148+0657 | J1851+0035 | J2148+0657 |
| C40-5 | 10/22/2016 - 10/23/2016 | 23:34:05.4 - 00:02:51.3 | 110.0 | 0.08 | J2148+0657 | J1938+0448 | J2025+3343 |
|  |  |  |  |  |  |  |  |

# C$^{17}$O full channel maps

![](Images/Intensity/b335_c17o10_2hfs_ch.pdf)

# C$^{18}$O spectral map

![image](Images/LineProf/C18O_contsub_rob05_05arcsec_5arcsec_region_spectra.pdf)\

</paper>

Write the methods card for this paper.