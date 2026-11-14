# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...689A.273R\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...689A.273R",
 "title": "The ALMA-ALPAKA survey: II. Evolution of turbulence in galaxy disks across cosmic time: Difference between cold and warm gas",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Rizzo, F.",
 "n_authors": 11,
 "arxiv_id": "2407.06261",
 "doi": "10.1051/0004-6361/202450455",
 "alma_projects_linked_by_archive": [
  "2011.0.00124.S",
  "2012.1.00650.S",
  "2012.1.00978.S",
  "2013.1.00059.S",
  "2013.1.00803.S",
  "2013.1.01161.S",
  "2015.1.00121.S",
  "2015.1.00330.S",
  "2015.1.00456.S",
  "2015.1.00723.S",
  "2015.1.00782.S",
  "2015.1.00862.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2015.1.01564.S",
  "2016.1.00386.S",
  "2016.1.01155.S",
  "2016.1.01499.S",
  "2017.1.00127.S",
  "2017.1.00392.S",
  "2017.1.00394.S",
  "2017.1.00413.S",
  "2017.1.00471.S",
  "2017.1.00766.S",
  "2017.1.00886.L",
  "2017.1.00908.S",
  "2017.1.01020.S",
  "2017.1.01045.S",
  "2017.1.01052.S",
  "2017.1.01228.S",
  "2017.1.01471.S",
  "2017.1.01659.S",
  "2017.1.01674.S",
  "2017.1.01677.S",
  "2018.1.00001.S",
  "2018.1.00484.S",
  "2018.1.00543.S",
  "2018.1.00974.S",
  "2018.1.01146.S",
  "2018.1.01306.S",
  "2018.1.01321.S",
  "2018.1.01651.S",
  "2018.A.00062.S",
  "2019.1.00862.S",
  "2019.1.01362.S",
  "2019.2.00129.S"
 ]
}
```

Paper text:
<paper>
# The ALMA-ALPAKA survey II. Evolution of turbulence in galaxy disks across cosmic time: Difference between cold and warm gas

# Introduction

The gas within the interstellar medium (ISM) of both low- (cite: Elmegreen_2004; Utomo_2019; Bacchini_2020) and high–$z$ (cite: Forster_2020) galaxies is known to be supersonically turbulent. The strongest observational evidence for the presence of turbulent motions within the ISM is that the gas velocity dispersion $\sigma$, which measures the broadening of emission lines, exceeds the expected broadening from thermal motions. This additional broadening allows for quantifying the random, chaotic motions of the gas in the ISM.

For $z \approx 0$ galaxies, turbulence is usually measured through spatially-resolved observations of emission lines tracing the cold molecular and atomic gas (cite: Ianjamasimanana_2015; Mogotsi_2016; Utomo_2019; Bacchini_2020). For $z > 0$ galaxies, obtaining spatially-resolved observations of cold gas emission lines requires exceptionally long integration times (cite: Rizzo_2023), even with the Atacama Large Millimiter Array (ALMA). Consequently, studies of gas turbulence at $z > 0$ have mainly relied on Integral Field Unit (IFU) or long-slit observations of emission lines tracing warm, ionized gas , that were possible only up to $z\approx3$ before the launch of JWST. Crucially, these studies based on ionized gas measurements have assumed that, for high-$z$ galaxies, the ionized gas kinematics (i.e., $\sigma$ and rotation velocity $V$) is consistent with the ones derived from cold gas (cite: Genzel_2011; Wisnioski_2015; Johnson_2018).

One of the main results from warm gas kinematic studies is that the turbulence strongly evolves as a function of redshift (cite: Epinat_2009; Forster_2009; Wisnioski_2015; Simons_2017; Turner_2017; Johnson_2018; Birkin_2023; Puglisi_2023). Galaxy disks at $z = 2 - 3$ are more turbulent and less rotationally supported (i.e., values of rotation-to-velocity dispersion ratio, $V/\sigma \lesssim 5$) than galaxy disks at $z < 1$. These results have been recently challenged by an increasing number of kinematic studies obtained from \[CII\] observations of $z \gtrsim 4$ galaxies (cite: Neeleman_2020; Rizzo_2020; Rizzo_2021; Lelli_2021; Tsukui_2021; Pope_2023; Posses_2023; Roman_2023) using ALMA. These works find that the gas turbulence within $z > 4$ galaxy disks is, on average, lower than those expected by extrapolating the evolution of the $\sigma - z$ relation obtained from warm gas studies at $z = 0 - 3$ (cite: Ubler_2019) and that $z \sim 4$ disks are dynamically cold, with $V/\sigma$ values of $\approx 10$ (cite: Neeleman_2020; Rizzo_2020; Fraternali_2021; Rizzo_2021; Lelli_2021; Tsukui_2021; Pope_2023; Roman_2023).

The above discrepancy between the kinematics obtained from \[CII\] observations and those extrapolated using ionized gas could be due to intrinsic differences between the cold and warm gas components. At $z = 0$, the values of $\sigma$ from cold gas (e.g., CO, HI) are, in fact, systematically lower than the ones obtained from H$\alpha$ (cite: Epinat_2008; Varidel_2020; Law_2022). Moreover, (cite: Kohandel_2024) use synthetic observations of zoom-in simulations of galaxies at $z > 4$ to highlight a potential additional bias in turbulence measurements derived from warm gas velocity dispersion. In their studies, unresolved non-circular motions induced by outflows contaminate the measurements of turbulence from warm gas. As a result, warm gas $\sigma$ values are $2-3$ times higher than the cold gas ones. In other words, in addition to the thermal and turbulent motions, the shape of the emission lines tracing the warm gas can be affected by the presence of non-circular (radial or vertical) motions, induced by outflows. These motions can mimic the broadening due to turbulence when the spectral or angular resolutions of the data are suboptimal.

In addition to the different kinematic tracers, potential contamination from outflows, and the redshift range (i.e., $1 - 3$ for warm gas and $> 4$ for cold gas), there are two additional potential reasons that can explain the discrepancy between warm and cold gas kinematic studies at $z > 0$: intrinsic differences in the galaxy populations or biases due to observational limitations. First, the results obtained with warm gas rely on observations of main-sequence galaxies (cite: Rodighiero_2011; Whitaker_2012) with a wide range of stellar masses ($M_{\star} = 10^{9} - 10^{10} M_{\odot}$), while the \[CII\] studies at $z > 4$ have focused on massive ($M_{\star} \gtrsim 10^{10} M_{\odot}$) upper main-sequence or starburst galaxies. Second, the typical angular resolution of ground-based telescopes used to observe $z = 1 - 3$ galaxies (cite: Wisnioski_2015; Harrison_2017; Turner_2017; Puglisi_2023) poses challenges due to beam smearing, potentially leading to degeneracies between rotation velocity and velocity dispersion (cite: DiTeodoro_2015; Rizzo_2022). Additionally, even when the galaxies are well spatially resolved thanks to JWST, the spectral resolutions of current facilities (e.g., FWHM $\gtrsim$ 100 km/s for JWST/NIRSpec) complicate the kinematic analysis, hampering the possibility of both cleanly disentangling between turbulent and non-circular motions and measuring values of $\sigma \lesssim$ FHWM/2.35 $\approx$ 40 km/s. On the other hand, cold gas emission lines usually fall in the sub-mm to radio range of the electromagnetic spectrum. In these wavelength ranges, the typical spectral resolutions of instruments is of a few km/s for low-$z$ data and 30 km/s for high-$z$ data. Combined with the typical angular resolution of $\approx$0.2", this kind of observations allows one to identify or isolate the circular motions in the rare cases when cold gas outflows are present (cite: Rizzo_2023; Roman_2023).

Understanding whether the origin of the discrepancy between studies based on warm and cold gas tracers is driven by different galaxy populations or biases due the kinematic tracers and observational limitations has significant implications on galaxy formation and evolution, even besides the theories of disk formation. For instance, the clumpy morphology of high-$z$ galaxies and the formation of galaxy bulges at high-$z$ have been explained within the framework of highly turbulent disks (cite: Bournaud_2010). In this scenario, mergers and vigorous gas accretion give rise to highly turbulent motions and instabilities within disks. These instabilities cause fragmentation of the gas disk, the formation of massive star-forming regions, and their migration into the inner regions (cite: Dekel_2013; Bournaud_2014). Finally, inaccurate measurements of the velocity dispersion can significantly affect the derivation of the mass and distribution of dark matter in galaxies, as their rotation curves must be corrected for the asymmetric drift which depends on $\sigma$ (cite: Lelli_2022).

Given the aforementioned potential biases on the $\sigma$ measured using the warm, ionized gas, key questions arise: Do the cold gas kinematics exhibit differences compared to warm counterparts when galaxies with similar physical properties are considered? Do the dynamical properties of galaxies depend on the gas tracers used to probe the gas kinematics? Does turbulence in disks evolve with cosmic time when measured from cold gas tracers?

In this paper, we address these questions by analyzing dynamical properties obtained from cold gas tracers across a redshift range from 0 to 5. The paper is structured as follows: in Section [2](#sec:sample), we describe the sample used in our analysis; in Section [3](#sec:evolution), we provide an empirical parametrization for the redshift evolution of $\sigma$ and $V/\sigma$ and we compare it with ionized gas studies from the literature. In Section [4](#sec:drivers), we briefly discuss the potential drivers of turbulence, while in Section [5](#sec:model), we present a physically-motivated model, calibrated on observations, predicting the turbulence evolution in star-forming galaxies. Caveats regarding the available values of $\sigma$ and star-formation rate (SFR) and a summary of this work are discussed in Sections [6](#sec:caveats) and [7](#sec:conclusions), respectively.

# ALPAKA and the extended sample

The primary objective of this paper is to study turbulence through the kinematics of cold gas across the widest possible redshift range. While previous works have explored turbulent motions and their driving mechanisms at $z > 0$, the focus has largely been on the range of $z = 4 - 5$ (cite: Neeleman_2020; Rizzo_2021; Tsukui_2021; Roman_2023). This particular redshift interval offers favorable conditions for conducting systematic, high-resolution observations crucial for accurate kinematic measurements, primarily due to the brightness of the \[CII\]-158$\mu$m emission line (cite: Carilli_2013). Observational campaigns targeting the intermediate-redshift range (i.e., $z = 0.5 - 4$) are significantly challenging. In fact, observations of \[CII\] are almost unfeasible because of the limited atmospheric transmission in the frequency range of the redshifted \[CII\] line and the restricted coverage of ALMA bands (cite: Carilli_2013). CO or \[CI\] emission lines are promising alternatives for probing the kinematics of cold gas within this intermediate redshift range. Nonetheless, the faintness of CO and \[CI\] emission lines poses significant observational challenges. Even with ALMA’s capabilities, long integration time (i.e., $\gtrsim 20$ hours) are typically needed to spatially resolve the CO emission in normal main-sequence galaxies at $z \sim 2$. Consequently, despite a decade of ALMA operations, there have been no high-resolution systematic surveys of CO at $z = 0.5 - 4$, but only observations of single targets.

In response to this limitation, we initiated the "ALMA Archival Large Program to Advance Kinematic Analysis" (ALMA-ALPAKA) project (cite: Rizzo_2023). ALPAKA is based on the mining of the ALMA archive to gather high-quality observations of CO or \[CI\] emission lines from non-lensed, star-forming galaxies within the redshift range of $z = 0.5 - 4$. The ALPAKA project encompasses $\approx$0.25" observations for 28 massive star-forming galaxies, representing the most extensive $z = 0.5 - 4$ sample, to date, with spatially-resolved cold gas kinematics.

In (cite: Rizzo_2023), we used the ALMA data to infer the dynamical state of the ALPAKA galaxies, and then divide the sample in three kinematic classes: rotating disks (19/28), interacting systems (2/28), uncertain (7/28). Rotation velocity ($V$) and velocity dispersion ($\sigma$) profiles derived using $^{\scriptstyle 3\mathrm{D}}$B  (cite: DiTeodoro_2015) are presented and discussed in detail in (cite: Rizzo_2023).

For the analysis presented in this paper, we selected the 17 ALPAKA disks with robust (i.e., uncertainties $\lesssim 60\%$) estimates of their stellar masses $M_{\star}$ and SFR (cite: Rizzo_2023). Due to the aforementioned observational limitations, the 17 ALPAKA disks are representative of the star-forming galaxy population, with stellar masses $M_{\star} \gtrsim 10^{10} M_{\odot}$. Most of the galaxies that are included in the ALPAKA sample were discovered as bright sources in the infrared or submillimeter wavelength (cite: Rizzo_2023). The 17 ALPAKA galaxies have SFRs that are 1.3 to 28 times higher than the SFR of a main-sequence galaxy (SFR$_{\mathrm{MS}}$). We quantify this offset $\Delta_{\mathrm{MS}}= \mathrm{SFR}/\mathrm{SFR_{MS}}(M_{\star}, z)$ using the prescriptions recently published by (cite: Popesso_2023) and normalized to a Chabrier Initial Mass Function (cite: Chabrier_2003):

$$\begin{align}
    MS(M_{\star}, z) \equiv \log \left[\frac{\mathrm{SFR_{MS}}(M_{\star}, z)}{M_{\odot} yr^{-1}} \right] = 
    \begin{aligned}[t]
    &(-0.034\,t(\mathrm{Gyr}) + 4.722) \times m \\
    &-0.1925 \times m^2 + \\
    & + (-26.16+0.2\,t(\mathrm{Gyr})),
    \end{aligned}
    \label{eq:sfr}
\end{align}$$ where $t$ is the cosmic time and $$\begin{equation*}
m = \left[\log \left( \frac{M_{\star}}{M_{\odot}} \right) + 0.025\right].
\end{equation*}$$

To trace the evolution of the dynamical properties of galaxies across cosmic time, we supplement the ALPAKA dataset with kinematic measurements obtained from CO, \[CI\], or \[CII\] spatially resolved observations from the literature. Throughout the paper, we refer to this sample as the extended sample. This includes only galaxies that are classified as rotating disks (cite: Rizzo_2023) and with stellar masses $M_{\star} \gtrsim 10^{10} M_{\odot}$ to ensure consistency with the stellar mass range covered by the ALPAKA sample. In Table [\[tab:tab1\]](#tab:tab1), we summarize the properties of the extended sample, which is described in details in Sects. [2.1](#sec:lowz) and [2.2](#sec:highz). Figure [1](#fig:ssfr) displays the distribution of $\Delta_{\mathrm{MS}}$ versus redshift for all the galaxies in the extended sample. These galaxies span both the main-sequence and starburst regimes (cite: Rodighiero_2011). In Table [1](#tab:deltams), we list the 50th, 2nd and 98th percentiles of the $\Delta_{\mathrm{MS}}$ distributions for the galaxies included in the extended sample (see Appendix [8](#sec:details_sample) for further details). This summary statistics allow us to quantify the spread of the $\Delta_{\mathrm{MS}}$ values in three redshift bins: $0 - 0.13$, $0.5 - 3.5$, $4 - 5$. While the three bins contain both main-sequence and starburst galaxies, the redshift interval $z = 3 - 5$ is skewed towards the starburst region. This bias stems from a selection effect, as at $z > 3$ high-resolution observations are available mostly for bright dusty galaxies. The $\sigma$ used in this paper refer to the values obtained as a radial average of the velocity dispersion profiles for each galaxy in the extended sample (see Appendix [8](#sec:details_sample)). The $V/\sigma$ values are obtained as a ratio between the maximum value of the rotation velocity and the average velocity dispersion.

![](figures/ssfr_z.png)

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Name | Number of galaxies | Redshift | Kinematic tracer | Reference for the kinematic analysis |
| HERACLES | 4 | 0 | CO(2-1) | (cite: Bacchini_2020) |
| PHANGS | 10 | 0 | CO(2-1) | This work |
| DYNAMO | 9 | 0.07 - 0.13 | CO(3-2), CO(4-3) | (cite: Girard_2021) |
| ALPAKA | 17 | 0.5 - 3.5 | CO and \[CI\] lines | (cite: Rizzo_2023) |
| Girard+19 | 2 | 1.03, 1.04 | CO(4-3) | (cite: Girard_2019) |
| Lelli+23 | 2 | 1.46, 2.23 | CO(4-3) | (cite: Lelli_2023) |
| Rizzo+20, 21 | 6 | 4 - 5 | \[CII\] | (cite: Rizzo_2021) |
| Fraternali+21 | 2 | 4.54, 4.57 | \[CII\] | (cite: Fraternali_2021) |
| Lelli+21 | 1 | 4.76 | \[CII\] | (cite: Lelli_2021) |
| Roman-Oliveira+23 | 4 | 4 - 5 | \[CII\] | (cite: Roman_2023) |
|  |  |  |  |  |

|    Subsample     | Redshift range | 50th | 2nd | 98th |
|:----------------:|:--------------:|:----:|:---:|:----:|
|     Low-$z$      |  $0.5 - 3.5$   | 3.6  | 0.4 |  15  |
| Intermediate-$z$ |  $0.5 - 3.5$   | 2.8  | 0.5 |  20  |
|     High-$z$     |    $4 - 5$     |  9   |  1  |  46  |
|                  |                |      |     |      |

: Percentiles of the $\Delta_{\mathrm{MS}}$ distributions for the galaxies in the extended sample, divided in three redshift bins.

## Low-z subsample

In the low-$z$ subsamples, we select 23 galaxies with kinematic data obtained from CO observations and $\Delta_{\mathrm{MS}} \gtrsim 0.3$, matching their properties with those of galaxies at $z \gtrsim 0.5$. Throughout the paper, we will denote the galaxies in this subsample by the name of the surveys to which they belong, as outlined below.

HERACLES: (cite: Bacchini_2020) analyzed the CO(2-1) kinematics of 7 disk galaxies from the Heterodyne Receiver Array CO Line Extragalactic Survey (cite: Leroy_2009) using $^{\scriptstyle 3\mathrm{D}}$B (cite: DiTeodoro_2015). In our extended sample, we include the 4 galaxies from (cite: Bacchini_2020) with stellar masses $M_{\star} \gtrsim 10^{10} M_{\odot}$.

PHANGS: We include ten galaxies from the Physics at High Angular resolution in Nearby Galaxies (PHANGS)-ALMA survey (cite: Leroy_2021). PHANGS-ALMA maps the CO(2-1) emission from a sample of nearby star-forming galaxies. The velocity $V$ and velocity dispersion $\sigma$ values used in this paper are derived after applying $^{\scriptstyle 3\mathrm{D}}$B (cite: DiTeodoro_2015) to the publicly available data cubes (cite: Leroy_2021; Leroy_2021b).

DYNAMO: The DYnamics of Newly Assembled Massive Objects (DYNAMO) survey (cite: Green_2014) includes massive ($M_{\star} > 10^{10} M_{\odot}$) disk galaxies at $z \approx 0.1$ with properties akin to main-sequence galaxies at $z = 1.5 - 2$. DYNAMO galaxies are starbursts, exhibiting high SFR ($\approx$ 10 M$_{\odot}$/yr) and high gas fractions (cite: Fisher_2014; Fisher_2017). In our sample, we include the 9 DYNAMO galaxies with gas kinematics derived from CO(3-2) and CO(4-3) emission lines (cite: Girard_2021).

## High-z subsamples

For galaxies at $z \gtrsim 0.5$, in addition to the stellar mass-based selection criterion, we imposed a criterion based on the quality of observational data. We specifically selected galaxies from the literature covered by at least 3 independent resolution elements along the major axis of the gas disk. This ensures the reliability of $V$ and $\sigma$ measurements and allows us to minimize contamination from mergers and beam smearing (cite: Rizzo_2022). This quality criterion is not needed for the selection of the low-$z$ samples presented in Sect. [2.1](#sec:lowz) as their major axes are typically resolved with more than ten independent resolution elements.

In addition to the ALPAKA galaxies, the sample at $0.5 < z < 4$ comprises two gravitationally lensed galaxies at $z \approx 1$, whose kinematic analysis from CO(4-3) is detailed in (cite: Girard_2019), and two main-sequence galaxies at $z = 1.46$ and $2.23$, with CO(4-3) kinematics presented by (cite: Lelli_2023).

At $z > 4$, we identified 6 lensed (cite: Rizzo_2020; Rizzo_2021) and 7 non-lensed disk galaxies (cite: Fraternali_2021; Lelli_2021; Roman_2023) with spatially-resolved \[CII\] observations. To the best of our knowledge, there is currently no availability of resolved (i.e., at least 3 resolution elements along the major axis) \[CII\] observations for disk galaxies at $z \gtrsim 5$.

## Considerations on the extended sample

The studies of the dynamical properties of galaxies and the impact of different astrophysical mechanisms (e.g., environment, stellar mass, SFR) on the ISM properties requires the analysis of a sample spanning a large range of physical properties. However, the current limitations in sample size and statistics hinder such investigations at present. Only with the next generation of facilities (e.g., ALMA upgrade, ngVLA), these studies can be conducted with greater precision (cite: Carpenter_2020; Kadler_2023), allowing for a more comprehensive understanding of the evolution of galaxy dynamics across cosmic time. Nevertheless, leveraging the sample compiled in this work offers a promising avenue to initiate these studies. Despite comprising galaxies selected through various methods (e.g., sub-mm, infrared, or optical observations), the extended sample covers a narrow range in stellar mass ($M_{\star}\approx10^{10} - 10^{11} M_{\odot}$) but 4 orders of magnitude in SFR. These characteristics allow us to investigate the evolution of the dynamics of the massive galaxy population. Furthermore, the extended sample allows us to minimize observational biases (e.g., beam-smearing effect, inclusion of non-resolved interacting systems) as it includes only observations with high data quality.

# Redshift evolution of galaxy dynamics using cold gas tracers

In this section, we use the extended sample to study how $\sigma$ and $V/\sigma$ evolve as a function of redshift (Sect.  [3.1](#sec:bestfit)). We then compare the dynamical properties of our extended sample with previous results from the literature (Sect.  [3.2](#sec:comparison)).

## Empirical relations using the extended sample

In Fig. [2](#fig:vs_cold), we present the distribution of $\sigma$ (left panels) and $V/\sigma$ (right panel) with respect to redshift for our extended sample, represented by colored markers. Despite the scatter, discernible trends emerge in both panels. Specifically, we observe an increase (decrease) by a factor of $\approx 2 - 3$ in $\sigma$ ($V/\sigma$) values in the redshift range $z = 0 - 1$ . Interestingly, these trends become less pronounced at $z > 1$, where a pleatau in both $\sigma$ and $V/\sigma$ is visible.

To quantify these observed trends, we employ the following functional forms:

$$\begin{equation}
 \label{eq:sigma}
 \sigma = a_{\sigma} + b_{\sigma} \exp({-z_{0, y}/z}) + s_{\sigma},
\end{equation}$$

$$\begin{equation}
 \label{eq:vsigma}
 V/\sigma = a_{V/\sigma} + b_{V/\sigma} \exp({-z/z_{0, y}}) + s_{V/\sigma}.
\end{equation}$$ In both equations, the parameters $s_{\sigma}$ and $s_{V/\sigma}$ represent the intrinsic scatter around the median scaling relation. The fits are performed adopting a hierarchical Bayesian method and sampling the parameter space by means of an Hamiltonian Monte Carlo algorithm (see Appendix [9](#sec:fit) for details). Table [2](#tab:bestfit) reports the best-fit parameters, while the pink solid lines in Fig. [2](#fig:vs_cold) show the best fit relation with the two dark and shaded regions representing the scatters due to the uncertainties on the parameters and the intrinsic scatters parametrized by $s_{\sigma}$ and $s_{V/\sigma}$. The values of $\sigma$ at $z = 0$, 2, and 4 derived from the best-fit relations are 9, 30, 37 km/s, while the corresponding values of $V/\sigma$ are 18, 9, and 8. The high values of $V/\sigma$ up to $z \sim 5$ indicate that massive galaxy disks are dynamically cold across cosmic time, despite having turbulent motions higher than their local counterparts.

Our results corroborate and strengthen the conclusions of previous works based on samples covering smaller redshift ranges (cite: Neeleman_2020; Rizzo_2020; Fraternali_2021; Lelli_2021; Tsukui_2021; Roman_2023; Lelli_2023): star-forming massive disk at $z = 0 - 5$ are well settled and rotation-dominated, rather than being highly perturbed by mergers or intense gas accretion. It is noteworthy that despite these results being obtained from a sample comprising both main-sequence and starburst galaxies, this conclusion remains conservative, as turbulent motions would be even lower if only main-sequence galaxies were considered (see Sect. [5](#sec:model) for details).

The discovery of dynamically cold disks at $\sim 4 - 5$ (cite: Neeleman_2020; Rizzo_2020; Rizzo_2021; Lelli_2021) prompted the exploitation of zoom-in simulations (cite: Pallottini_2022) to identify galaxies with similar dynamical properties (cite: Kohandel_2020; Kret_2022; Kohandel_2024). For instance, (cite: Kret_2022) observed that these dynamically cold disks can form as transient phenomena in their simulations following the accretion of co-planar, co-rotating gas via cold cosmic-web streams. Similarly, (cite: Kohandel_2024) identified dynamically cold disks among their galaxies at $z > 4$. However, owing to the intrinsic characteristics of zoom-in simulations (e.g., limited volumes, resolutions, implementation of feedback presciptions) and the absence of galaxies with stellar masses and SFR comparable to those in the extended sample, it remains challenging to quantify whether state-of-the-art cosmological simulations can produce dynamically cold massive disks with properties (e.g., SFR, $V/\sigma$) similar to those in our extended sample.

| Parameter  |    $y=\sigma$    | $y=V/\sigma$ |
|:----------:|:----------------:|:------------:|
|  $a_{y}$   |  9$\pm$ 1 km/s   |   7$\pm$2    |
|  $b_{y}$   |  39$\pm$5 km/s   |   13$\pm$2   |
| $z_{0, y}$ |   1.1$\pm$0.3    | 1.5$\pm$0.9  |
|  $s_{y}$   | 3.3$\pm$0.9 km/s | 4.5$\pm$0.6  |

: Best-fit parameters defining the relations between $\sigma$-$z$, Eq ([\[eq:sigma\]](#eq:sigma)) and $V/\sigma$-$z$, Eq ([\[eq:vsigma\]](#eq:vsigma)).

![](figures/evolution_cold.png)

## Comparison with warm gas kinematics

![](figures/evolution_comparison.png)

Ideally, one would like to compare the cold and warm gas kinematics in the same sample of galaxies. However, this comparison is hampered by the lack of warm gas observations (e.g., H$\alpha$) for most galaxies in our extended sample. Therefore, we compare the best-fit relations derived in Sect. [3.1](#sec:bestfit) with trends of $\sigma$-$z$ and $V/\sigma$-$z$ obtained from warm, ionized gas observations and models available in the literature.

### H$\alpha$ observations

The redshift evolution of turbulence and $V/\sigma$ from warm gas tracers has been mainly studied using compilations of main-sequence galaxies with a wide range of stellar masses ($\log(M_{\star}/M_{\odot}) = 9 - 11$, see Appendix [10.1](#sec:ms1) and [10.2](#sec:ms2)). However, to investigate the impact on the kinematic tracers on the derived $\sigma$ and $V/\sigma$ and minimize potential biases due to differences in physical properties of galaxies, we make comparisons using samples that match the stellar masses and SFRs of our extended sample. In the central columns of Table [\[tab:comparison\]](#tab:comparison), we summarize the main properties of the different subsamples. For comparison, we report in the right columns the number and the median $\sigma$ and $V/\sigma$ values of galaxies in our extended samples contained in the same redshift bins of the comparison H$\alpha$ subsamples.

In our comparative analysis at $z \approx 0$, we incorporate two distinct subsets. The first subset consists of the 9 DYNAMO galaxies, which are part of our extended sample and for which H$\alpha$ or H$\beta$ kinematics are presented in (cite: Girard_2021). In the second subset, we included galaxies from the Sydney-AAO Multiobject Integral field Spectrograph (SAMI) survey (cite: Croom_2012; Scott_2018). In particular, we selected the 67 SAMI galaxies with $M_{\star} \gtrsim 10^{10} M_{\odot}$ and $\Delta_{\mathrm{MS}} \gtrsim 0.3$. Their H$\alpha$ kinematics is presented by (cite: Varidel_2020). (cite: Girard_2021) have previously studied the comparison between CO and warm gas $\sigma$ values for the 9 DYNAMO galaxies, revealing that, on average, warm gas $\sigma$ values are a factor of 3$\pm1$ greater than those derived from CO. Likewise, the median CO $\sigma$ value within our extended sample at $z \approx 0$ (i.e., PHANGS and HERACLES) is 8$\pm$2 km/s, that is a factor of 3 lower compared to the median H$\alpha$ $\sigma$ of 25$\pm$6 km/s obtained for the SAMI galaxies. The $V/\sigma$ values from CO are on average a factor of 3 higher with respect to the warm gas $V/\sigma$ values for the 9 DYNAMO galaxies. A similar difference of $\approx 3$ is obtained when we compare the median CO $V/\sigma$ from our extended sample to the median H$\alpha$ $V/\sigma$ for the SAMI galaxies.

In our comparative analysis at $z > 0$, we include the $z \sim 2$ samples studied by (cite: Hogan_2021) and (cite: Birkin_2023). To our knowledge, there are no systematic H$\alpha$ studies at $z > 4$. The sample analyzed by (cite: Hogan_2021) consists of 6 ultra luminous infrared galaxies (ULIRG) at $z = 2.1 - 2.4$, while the one analyzed by (cite: Birkin_2023) consists of 31 dusty star-forming galaxies (DSFGs) at $z = 1.3 - 2.6$. Galaxies in both studies have high stellar masses ($\log(M_{\star}/M_{\odot}) > 10$) and $\Delta_{\mathrm{MS}}$ matching the properties of the intermediate-$z$ subsample (see the percentile values in Table [\[tab:comparison\]](#tab:comparison)). (cite: Hogan_2021) and (cite: Birkin_2023) report median values of $\sigma$ of $160 \pm 60$ km/s and $87 \pm 6$ km/s for the ULIRG and DSFG samples, respectively. The median $V/\sigma$ values are $2.6 \pm 0.9$ for the ULIRGs and $2.4 \pm 0.5$ for the DSFGs (green shaded area in Fig. [3](#fig:vs)). We now compare these values from H$\alpha$ with the median $\sigma$ and $V/\sigma$ values of our extended sample in the two redshift bins $z = 2.1 - 2.4$ and $z = 1.3 - 2.6$ (see Table [\[tab:comparison\]](#tab:comparison)). The values of $\sigma$ from cold gas are a factor of 2 and 4 lower than those found by (cite: Hogan_2021) and (cite: Birkin_2023), while the corresponding values of $V/\sigma$ from cold gas are a factor of 3 and 4 lower than their H$\alpha$ values. This result clearly indicates that, when considering galaxies with similar stellar masses and $\Delta_{\mathrm{MS}}$, the values of $\sigma$ and $V/\sigma$ from H$\alpha$ are, on average, systematically higher and lower, respectively, than those obtained using cold gas tracers. Providing further support to the findings in this section, we highlight that the systematic disparity of approximately a factor of 3 between cold and warm gas $\sigma$ aligns with observations from the few $z > 1$ galaxies for which both high-resolution CO (or \[CII\]) and H$\alpha$ data are available (cite: Girard_2021; Parlanti_2023).

Due to the data quality of current H$\alpha$ observations (see details in Sect. [6](#sec:caveats)), we cannot determine what is causing the discrepancy between warm and cold gas kinematics. As a result, we cannot discriminate whether this difference is mainly due to: (i) differences in the disk thickness of the two gas phases; (ii) outflow contaminating the measurements of turbulence from warm gas; (iii) insufficient angular and/or spectral resolution which are biasing the measurements of warm gas $\sigma$.

+:-----------:+:--------------:+:------:+:--------:+:--------:+:--------:+:---------------:+:-------------:+:----------:+:----------------:+:--------------:+
|             | Comparison samples (warm gas)                                                              | Extended sample (cold gas)                     |
+-------------+----------------+--------+--------------------------------+-----------------+---------------+------------+------------------+----------------+
| redshift    | Name           | Number | $\Delta_{\mathrm{MS}}$         | $\sigma$        | $V/\sigma$    | Number     | $\sigma$         | $V/\sigma$     |
+-------------+----------------+--------+----------+----------+----------+-----------------+---------------+------------+------------------+----------------+
|             |                |        | 50th     | 2nd      | 98th     | km/s            |               |            | km/s             |                |
+-------------+----------------+--------+----------+----------+----------+-----------------+---------------+------------+------------------+----------------+
| $\approx 0$ | SAMI$^{a}$     | 67     | 1.7      | 0.3      | 6        | 25$\pm6$        | $7^{+2}_{-1}$ | 15         | 8$\pm2$          | $21^{+8}_{-6}$ |
+-------------+----------------+--------+----------+----------+----------+-----------------+---------------+------------+------------------+----------------+
| 0.07 - 0.13 | DYNAMO$^{b}$   | 9      | 9        | 4        | 17       | $36^{+10}_{-9}$ | $5^{+4}_{-2}$ | 9          | $12^{+3}_{-4}$   | $17^{+9}_{-2}$ |
+-------------+----------------+--------+----------+----------+----------+-----------------+---------------+------------+------------------+----------------+
| 2.1 - 2.4   | Hogan+21$^{c}$ | 6      | 2.6      | 0.8      | 6.2      | 160$\pm60$      | $2.6\pm0.9$   | 4          | $36^{+34}_{-11}$ | $9^{+5}_{-3}$  |
+-------------+----------------+--------+----------+----------+----------+-----------------+---------------+------------+------------------+----------------+
| 1.3 - 2.6   | KAOSS$^{d}$    | 31     | 2.9      | 0.9      | 8.2      | 87$\pm6$        | 2.4$\pm0.5$   | 13         | $40^{+9}_{-11}$  | 10$\pm4$       |
+-------------+----------------+--------+----------+----------+----------+-----------------+---------------+------------+------------------+----------------+

Table notes: Kinematics from: .

### Models calibrated on H$\alpha$ observations

In addition to the comparison with the H$\alpha$ samples, we consider the expected evolution of $\sigma$ and $V/\sigma$ according to the disk-instability model proposed by (cite: Wisnioski_2015). This model is calibrated to reproduce the redshift trends of $\sigma$ and $V/\sigma$ from warm gas observations (cite: Wisnioski_2015; Turner_2017; Johnson_2018) and it is based on two assumptions: cold gas disks are marginally unstable to perturbations; and the cold gas $\sigma$ values are similar to the warm gas ones. The presence of instabilities is commonly quantified through measurements of the Toomre parameter $Q$ (cite: Toomre), $$\begin{equation}
 \label{eq:toomre}
Q = \frac{\kappa \sigma}{\pi G \Sigma_{\mathrm{gas}}}.
\end{equation}$$ In Eq. ([\[eq:toomre\]](#eq:toomre)), $\Sigma_{\mathrm{gas}}$ is the surface density of the gas and $\kappa$ is the epicyclic frequency which is a function of the angular velocity $\Omega = V/R$. A disk is unstable if $Q \lesssim 1$, that is, when the self-gravity of the gas overcomes the repelling forces due to gas pressure (i.e., $\sigma$) and rotation support ($\Omega$). In (cite: Wisnioski_2015) model, the evolution of the dynamical properties of the star-forming galaxy population is explained in terms of the redshift increase of gas fraction $f_{\mathrm{gas}}$ within marginally unstable disks. In particular, the evolution of $\sigma$ and $V/\sigma$, defined by approximating Eq. ([\[eq:toomre\]](#eq:toomre)) (cite: Genzel_2011), are given by the following equations: $$\begin{equation}
\label{eq:di1}
    \sigma(z) = \frac{Q}{\sqrt{2}} V f_{\mathrm{gas}}(z)
\end{equation}$$

$$\begin{equation}
\label{eq:di2}
    \frac{V}{\sigma} = \frac{\sqrt{2}}{f_{\mathrm{gas}}(z) Q},
\end{equation}$$

Following (cite: Wisnioski_2015), we use Eqs. ([\[eq:di1\]](#eq:di1)) and ([\[eq:di2\]](#eq:di2)) with $Q = 1$, which is the typical value for marginal instability. We compute the expected evolution of $\sigma$ and $V/\sigma$ in the two cases:

1.  massive main-sequence galaxies. We compute $f_{\mathrm{gas}}$ using the empirical relation in Eq. (3) in (cite: Wisnioski_2015), which is a function of redshift and stellar mass. We fix the stellar mass at $10^{10.5} M_{\odot}$ and use $V = 200$ km/s, the average rotation velocity typically measured for massive main-sequence galaxies (cite: Harrison_2017; Forster_2018). The resulting relations are shown in Fig. [3](#fig:vs) (bottom panels) by a black dashed line.

2.  galaxies from our extended sample. We compute the expected values of $\sigma$ and $V/\sigma$ using Eqs.([\[eq:di1\]](#eq:di1)) and ([\[eq:di2\]](#eq:di2)) ($\sigma_{\mathrm{exp, DI}}$, $(V/\sigma)_{\mathrm{exp, DI}}$) for the galaxies in our extended sample. The values of $\sigma_{\mathrm{exp, DI}}$ and $(V/\sigma)_{\mathrm{exp, DI}}$ represent, therefore, the values predicted by the disk-instability model for galaxies with $V$ and $f_{\mathrm{gas}}$ equal to the measured values of our extended sample. We then fitted the resulting distributions using Eqs. ([\[eq:sigma\]](#eq:sigma)) and ([\[eq:vsigma\]](#eq:vsigma)) (see Appendix [10.3](#sec:comparison_di) for details). The dash-dotted lines in Fig. [3](#fig:vs) are the best-fit relations to the resulting redshift distributions of $\sigma_{\mathrm{exp, DI}}$ and $(V/\sigma)_{\mathrm{exp, DI}}$.

Both the dashed and dash-dotted curves in Fig. [3](#fig:vs) systematically overestimate the values of $\sigma$ from cold gas by factors of 2 - 4 at $z \gtrsim 1$, while simultaneously underestimating $V/\sigma$ by the same factors. This discrepancy implies that the disk-instability model fails to accurately reproduce the evolution of the dynamical properties inferred from cold gas tracers. It is important to note that, although the instability-model curves are consistent with the observational results from H$\alpha$ kinematics (green areas), this agreement does not imply that the warm gas disks are marginally unstable. First, the instability-model proposed by (cite: Wisnioski_2015) is valid for the cold gas, under the assumption that cold and warm gas have similar kinematics. As shown in Sect. [3.2](#sec:comparison), this assumption is not valid as, on average, the $\sigma$ values from cold gas appear to be a factor of 3 lower than the warm values. Second, (cite: Bacchini_2024) show that the approximation of the Toomre parameter used by (cite: Wisnioski_2015) to derive Eqs. ([\[eq:di1\]](#eq:di1)) and  ([\[eq:di2\]](#eq:di2)) significantly underestimates the values of $Q$.

# Drivers of turbulence

Theoretical models and simulations indicate that turbulence decays rapidly relative to the dynamical timescale of the galaxy (cite: Maclow_1998; Kim_2015). Therefore, continuous driving mechanisms are necessary to explain the observed level of turbulence. Stellar feedback is expected to be the primary source of turbulence energy in star-forming galaxies (cite: Maclow_2004; Ostriker_2011; Hayward_2017; Orr_2020). However, a number of additional processes (e.g., radial gas flows due to gravitational instabilities (cite: Bournaud_2010; Krumholz_2016; Krumholz_2018; Ginzburg_2022), gas accretion from the cosmic web (cite: Klessen_2010; Forbes_2023; Jimenez_2023)) are considered when the impact of stellar feedback alone is insufficient to account for the observed turbulence.

(cite: Krumholz_2016) and (cite: Krumholz_2018) developed analytical predictions for the dependence of the cold gas velocity dispersion on SFR considering two driving mechanisms of turbulence, stellar feedback and radial gas flows (also called transport model). The transport model predicts values of $\sigma$ which are more than 4 times higher than those predicted by the feedback model at fixed SFR, due to the different scaling between $\sigma$ and SFR in the transport and feedback models. In the transport model, $\sigma \propto \mathrm{SFR}$, while $\sigma \propto \mathrm{SFR}^{1/2}$ for the feedback model with a star formation efficiency free to vary as a function of $\sigma$; no relationship between SFR and $\sigma$ is predicted for the feedback model with fixed star formation efficiency (Appendix [11](#sec:assumptionfeedback)). Comparisons of K18 models with warm gas $\sigma$ of $z = 1 - 3$ galaxies suggest that energy injected by stellar feedback is not sufficient to explain the high values of the observed velocity dispersion. In contrast, the transport model is in good agreement with high-$z$ observations derived from warm gas (cite: Johnson_2018; Ubler_2019). The feedback model alone reproduces the observations at low-$z$. The fiducial model proposed by K18 is, therefore, a combination of the feedback and transport models and it can reproduce both low and high-$z$ galaxies.

![](figures/sfrvdisp_alpaka.png)

In this context, we compare the values of cold gas $\sigma$ with the fiducial and feedback models proposed by K18, in order to understand what is the potential origin of the cold gas turbulence in our extended sample. In Fig. [4](#fig:krum), we show the distribution of the extended sample in the $\sigma$-SFR plane and the feedback and transport+feedback models. In both models, we assume the fiducial parameters (i.e., rotation velocities and orbital times) for high-$z$ galaxies reported by K18 and we use the range of values of our extended sample (shaded area).

The $\sigma$-SFR distribution of our sample aligns with the predictions of the stellar feedback model proposed by K18. Conversely, the transport+feedback model predicts, that high-$z$ galaxies with SFR in the range of the extended sample have $\sigma$ values which are, on average, $3-10$ times higher than the values of $\sigma$ of our galaxies. The findings presented in this section corroborate previous studies showing that the turbulence measured from cold gas kinematics can be explained by stellar feedback (cite: Girard_2021; Rizzo_2021; Roman_2024). This underscores that the warm gas kinematics is not the ideal observable to investigate the mechanisms driving turbulence.

# A predictive model for the evolution of turbulence

## Feedback-driven model

In Sect. [4](#sec:drivers), we demonstrate that the $\sigma$-SFR distribution for galaxies in our extended sample aligns with the K18 feedback-driven models. These models, however, are based on assumptions about star-formation efficiency and the Toomre parameter (see Appendix [11](#sec:assumptionfeedback) for details). Additionally, the K18 models rely on a series of free parameters that are adjusted for different redshift ranges and specific galaxy populations. Given these complexities, in this section, we adopt the simpler feedback-driven model proposed by (cite: Fraternali_2021). The F21 model has fewer free parameters, enabling us to better control and understand their impact on the results. Despite its simplicity, the F21 model effectively describes galaxies at both low(cite: Bacchini_2020) and high redshift (cite: Rizzo_2021; Roman_2024). This approach allows us to maintain accuracy while reducing the uncertainties inherent in more complex models. F21 assumes that supernovae must provide energy at a rate, $\dot{E}_{\mathrm{SN}}$, equal to the rate at which turbulent kinetic energy, $E_{\mathrm{kin}}$ is dissipated, that is, $\dot{E}_{\mathrm{SN}} = E_{\mathrm{kin}}/\tau$. The kinetic energy and supernova energy rate are defined as $$\begin{equation}
 \label{eq:ekin}
    E_{\mathrm{kin}} = \frac{3}{2} M_{\mathrm{gas}} \sigma^2
  
\end{equation}$$ $$\begin{equation}
 \label{eq:esn}
    \dot{E}_{\mathrm{SN}} = \epsilon_{\mathrm{SN}}\,\mathrm{SFR}\,\eta_{\mathrm{SN}}\,E_{\mathrm{SN}}\,
  
\end{equation}$$ where $\epsilon_{\mathrm{SN}}$ is the efficiency at which the kinetic energy is transferred to the ISM, $\eta_{\mathrm{SN}}$ is the supernova rate, $E_{\mathrm{SN}}$ is the supernova energy equal to 10$^{51}$ erg. The timescale of turbulence dissipation $\tau$ can be defined as $\tau = 2 h/\sigma$ (cite: Maclow_1998) where $h$ is the scale height of the gas disk. For a gas disk in hydrostatic equilibrium, the scale height can be written, to first-order approximation, as: $$\begin{equation}
    h(R) = \sigma(R)\left[\frac{\partial{\phi(R,0)}}{\partial Z}\right]^{-1/2}
\end{equation}$$ where $\phi(R,0)$ is the galactic gravitational potential in the plane of the disk ($Z = 0$). Using $\dot{E}_{\mathrm{SN}} = E_{\mathrm{kin}}/\tau$, we derive the relation between $\sigma$ and SFR: $$\begin{equation}
    \sigma = \mathrm{SFR}^{1/3} \left( \frac{4 \, \epsilon_{\mathrm{SN}} \, \eta_{\mathrm{SN}} \, E_{\mathrm{SN}}\,h}{3 \, M_{\mathrm{gas}}} \right)^{1/3}.
    \label{eq:slope0.33}
\end{equation}$$ Establishing the relationship between the local values of the SFR and $\sigma$ using Eq. ([\[eq:slope0.33\]](#eq:slope0.33)) is non-trivial due to the dependence of $h(R)$ not only on $\sigma(R)$ but also on the SFR via $M_{\mathrm{gas}}$, which affects the gravitational potential (cite: Bacchini_2020b; Ostriker_2022). As a consequence the ratio $h/M_{\mathrm{gas}}$ may depend on both $\sigma$ and SFR. To investigate this, we used the scale height profiles $h(R)$ for 17 galaxies (4 at low-$z$ and 13 at high-$z$) from our extended sample. These profiles are presented and described in (cite: Bacchini_2019) and (cite: Bacchini_2024), and they are derived using a method which assumes vertical hydrostatic equilibrium and takes into account the full galactic potential, including contributions from stars, dark matter, and gas (cite: Bacchini_2019). We averaged these profiles radially and analyzed them in relation to $\sigma$, SFR, and $\sigma \times {\mathrm{SFR}}$. Additionally, we examined the distribution of $\epsilon_{\mathrm{SN}}h/M_{\mathrm{gas}}$ as a function of $\sigma$, SFR, and $\sigma \times {\mathrm{SFR}}$. This analysis revealed that the dependencies of $h$ and $\epsilon_{\mathrm{SN}}h/M_{\mathrm{gas}}$ on $\sigma$ and SFR cancel out when considering the average values of $h(R)$ and $\sigma(R)$ along with the global SFRs and $M_{\mathrm{gas}}$. Moreover, the factor $CC = [\epsilon_{\mathrm{SN}} (h/\mathrm{pc})/(M_{\mathrm{gas}}/M_{\odot}]^{1/3}$ remains approximately constant over cosmic time. The individual parameters in $CC$ evolve in such a way that they cancel out any redshift dependence. For low-$z$ galaxies, $CC \sim 10^{-3}$ considering: $h \sim 200$ pc (cite: Bacchini_2020b), $\epsilon_{\mathrm{SN}} \sim 0.01$ when global values of $h$ and $\sigma$ are considered (cite: Bacchini_2020), $M_{\mathrm{gas}} \sim 10^9 M_{\odot}$ (cite: Leroy_2021b). For high-$z$ galaxies, $CC \sim 10^{-3}$, considering: $h \sim 200$ pc (cite: Bacchini_2024), $\epsilon_{\mathrm{SN}} \sim 0.01 - 0.1$ (cite: Rizzo_2020; Rizzo_2021; Roman_2024), $M_{\mathrm{gas}} \sim 10^{10} M_{\odot}$. Throughout the rest of the paper, we adopt $CC$ as a constant value, leading to $\sigma \propto \mathrm{SFR}^{1/3}$, which differs from the K18 feedback models, which predict that $\sigma \propto \mathrm{SFR}^{1/2}$ or $\sigma$ remains constant.

## Calibrating the model

In this section, we calibrate the physically-motivated model described in Sect. [5.1](#sec:sfrmodel) using our extended sample. The final aim is to provide a relationship that predicts the average turbulence, derived from cold gas tracers, for galaxies with known global SFRs. To quantify the relationship between $\sigma$ and SFR, we fit a linear model between $\log(\sigma)$ and $\log(\mathrm{SFR})$ (see Appendix [9](#sec:fit) for details, Fig. [5](#fig:sigma_sfr)), and we fixed its slope at 0.33, the value expected in the case of F21 feedback-driven turbulence. The analysis yields the following median relation:

$$\begin{equation}
 \label{eq:sigma-sfr}
       \log{\sigma} = 0.33 \times \log{\mathrm{SFR}} + (0.77\pm 0.03),
    
\end{equation}$$

with an intrinsic scatter of 0.13 dex. In Eq. ([\[eq:sigma-sfr\]](#eq:sigma-sfr)), $\sigma$ is in units of km s$^{-1}$ and SFR is in units of $M_{\odot}$ yr$^{-1}$. We note that, if the slope is left free to vary, we find a value of 0.27$\pm$0.03, consistent with the fixed-slope case within the 2-$\sigma$ uncertainties and $\gtrsim 8$-$\sigma$ larger than the slope of $\gtrsim 0.5$ predicted by K18 models (see Appendix [11](#sec:assumptionfeedback) for details). Furthermore, the leave-one-out cross-validation and the widely applicable information criterion methods (cite: Vehtari_2015) indicate that the model with the fixed slope is favored over the one with the free value. This is another confirmation of the supernova-driven nature of the turbulence. Based on eq. ([\[eq:slope0.33\]](#eq:slope0.33)), the relative small scatter in this relation confirms that the factor $CC = [\epsilon_{\mathrm{SN}} (h/\mathrm{pc})/(M_{\mathrm{gas}}/M_{\odot}]^{1/3}$ has small variations that do not correlate with the galaxy SFR and the galaxy mass. In Appendix [12](#appendix:correlation), we also perform a diagnostic check to ensure that the residuals of the linear relation (Eq. [\[eq:sigma-sfr\]](#eq:sigma-sfr)) do not correlate with $\log{\sigma}$ and $\log{\mathrm{SFR}}$. Additionally, we estimate the partial correlation between these two quantities to isolate their relationship against residuals.

![](figures/sigma_sfr_rel_fixedslope_hr.png)

## Turbulence across cosmic time

In this section, we present a semi-empirical model predicting the redshift evolution of turbulence when considering populations of main-sequence and starburst galaxies, at fixed $M_{\star}$ and $\Delta_{\mathrm{MS}}$. The main assumption of this model is that the evolution of $\sigma$ is mainly driven by the injection of energy due to the supernova explosions (see Sect. [4](#sec:drivers)) and that, at fixed stellar mass, high-$z$ galaxies have higher SFRs than the local ones. By assuming the prescription of the redshift evolution of the SFR proposed by (cite: Popesso_2023), and combining it with Eq. ([\[eq:sigma-sfr\]](#eq:sigma-sfr)), we derive the following evolution of $\sigma$ for galaxies at $z = 0 - 7$: $$\begin{equation}
 \log{\sigma} (M_{\star}, z, \Delta_{\mathrm{MS}}) = 0.33 \times [\mathrm{MS}(M_{\star}, z) + \log{\Delta_{\mathrm{MS}}}] + 0.77.  
\end{equation}$$

It is important to emphasize that this evolution of $\sigma$ as a function of redshift is entirely due to the evolution of the main-sequence relation. The physics of turbulence driving does not appear to evolve with time (see Fig. [5](#fig:sigma_sfr)).

![](figures/model_evolution.png)

Fig. [6](#fig:model) shows the redshift evolution for populations of main-sequence galaxies with $M_{\star}$ of $10^{11} M_{\odot}$ and $10^{10} M_{\odot}$ in the left panel, while the right panel showcases the evolution for populations of starburst galaxies with $\mathrm{SFR}$ ten times higher than that of a main-sequence galaxy. We highlight the $\sigma$-$z$ relations in Fig. [6](#fig:model) are not evolutionary tracks for individual galaxies, but profiles showing the evolution of $\sigma$ when galaxy populations with similar properties (i.e., $M_{\star}$, $\Delta_{\mathrm{MS}}$) are investigated. Interestingly, the supernova-driven model predicts that, at fixed redshift, main-sequence galaxies with lower stellar masses have lower velocity dispersions compared to galaxies with higher stellar masses, due to their lower SFRs. We also show the evolution of $\sigma$ for galaxies with $M_{\star} = 10^{9} M_{\odot}$ with the dotted line. This model should be taken with caution as it relies on the extrapolation of the $\sigma$-SFR relation below the mass range probed by the extended sample. The values of $\sigma$ for the main-sequence galaxies at $z \gtrsim 4$ are consistent with the \[CII\]-derived values of $\sigma$ reported for galaxies from the zoom-in SERRA simulation (cite: Kohandel_2024).

The models shown in Fig. [6](#fig:model) suggest only a mild redshift evolution of turbulence motion within the range $z = 0$ - 2 and no significant evolution at $z > 2$. For instance, a main-sequence galaxy with $M_{\star} = 10^{10} M_{\odot}$ has $\sigma\approx$ 5 km/s at $z = 0$ to $\sigma\approx$ 16, 20, and 21 km/s at $z = 2$, 4, and 6. On the other hand, for a starburst galaxy with $\Delta_{\mathrm{MS}} = 10$, the model predicts $\sigma$ values of $\approx$ 10, 35, 46 km/s at $z = 0, 2$ and 6. For galaxies with smooth build-up history that grow in mass following the main-sequence relation (cite: vandokkum_2013), our model predicts that there is only a moderate evolution of turbulence over a large fraction of cosmic time. For instance, the Milky Way is expected to grow from $\approx 10^{10} M_{\odot}$ at $z = 2$ to a stellar mass of $\approx 5 \times 10^{10}$ at $z = 0$ (cite: Bland_2016). During this time range, the average $\sigma$ values are expected to evolve from 16 to 6 km/s if the galaxy evolves following the main-sequence relation. Remarkably, the value of 6 km/s predicted by our model for a Milky-Way like galaxy at $z = 0$ is consistent with the average values of the velocity dispersion measured from molecular ($\approx$ 4 km/s) and atomic gas ($\approx 8$ km/s) (cite: Kramer_2016; Marasco_2017).

Predicting the evolution of the $V/\sigma$ across cosmic time is not straightforward, as it requires determining the evolution of the rotation velocity. The latter depends on the dynamical mass and the size of the galaxy. However, we can set lower limits for the evolution of $V/\sigma$ at fixed stellar mass by employing the local stellar Tully-Fisher relation, a scaling relation between the velocity and the stellar mass of a galaxy (cite: Tully; Reyes_2011). The evolution of the stellar Tully-Fisher relation (TFR) has not been established within the redshift range of our extended sample; nonetheless, we can use the local stellar TFR to determine the lower limits of the velocity of galaxies at fixed stellar masses. This is because, within the $\Lambda$CMD cosmology framework, the stellar TFR is expected to evolve such that at fixed stellar mass, high-$z$ galaxies have higher velocity than $z = 0$ galaxies (cite: Dutton_2011). In Fig. [7](#fig:tfr), we show the profiles obtained by dividing the velocity from the local stellar TFR from (cite: Reyes_2011) with respect to $\sigma$ from the supernova-driven model. This combination of the TFR and the supernova-driven model predicts that at $z > 1$, galaxies are rotationally supported with $V/\sigma$ of $\approx 10$, even for the low-mass ($M_{\star} = 10^9 M_{\odot}$) galaxy population.

![](figures/evolution_vs_model_tfr.png)

As a consistency check, in Fig. [8](#fig:comparison), we compare the distribution of the main-sequence (upper panels) and starburst (bottom panels) galaxies in the extended sample with the predictions from our model, by dividing the galaxies in three stellar mass bins. The model is in good agreement with observations,

but the typical uncertainties on the $\sigma$ values and the low number of galaxies in each bin of stellar mass and $\Delta_{\mathrm{MS}}$ inhibit a detailed comparison. In the future, high-data quality observations (e.g., high S/N, angular resolutions) and larger sample sizes will facilitate the validation and refinement of this supernova-driven evolution model. For reference, in each panel of Fig.[8](#fig:comparison), we show the empirical relation of $\sigma$-$z$ presented in Sect.[3.1](#sec:bestfit) with a gray dotted line. Its comparison with the supernova-driven models highlights how this relation reflects the heterogeneity of the extended sample, which consists of galaxies spanning a wide range of $\Delta_{\mathrm{MS}}$.

![](figures/model2_scatter.png)

# Caveats

The results presented in this work rely on three observables: cold gas $\sigma$, warm gas $\sigma$, and SFR. In this section, we address potential caveats that may influence their measurements.

## Uncertainties on the velocity dispersion

As discussed in Sect. [2](#sec:sample), deriving the kinematics of high-$z$ galaxies poses significant challenges. A primary limitation arises from angular resolution, often implying that the emission of high-$z$ galaxies is resolved by only few independent resolution elements. Consequently, the kinematics of high-$z$ galaxies can be influenced by the beam-smearing effect, leading to a degeneracy between $V$ and $\sigma$ and artificially inflated values of $\sigma$ (cite: DiTeodoro_2015; Rizzo_2022). For example, for about half of the extended sample at $z > 0.5$, the major axis is sampled by 3 - 4 independent resolution elements. While the kinematic analysis for all galaxies of our extended sample was performed using state-of-the-art forward-modeling techniques to mitigate the beam-smearing effect, overcoming this issue in the case of low-resolution data remains difficult. Consequently, velocity dispersion values may be slightly overestimated. Moreover, the velocity dispersion at $z \gtrsim 1$ are $\approx$ 30 km/s, a value similar to the typical spectral resolution of the ALMA data. Thus, we cannot exclude that certain $\sigma$ values within our high-$z$ extended subsample may be slightly overestimated. This makes our conclusion even more robust. In fact, if the $\sigma$ values from cold gas were smaller, the discrepancy with the $\sigma$ values of warm gas would be even stronger.

The H$\alpha$ measurements used in Sect. [3.2](#sec:comparison) are potentially affected by more severe issues compared to the CO and \[CII\] data. Both in the case of low- and high-$z$ galaxies, the spectral resolutions of the instruments used for H$\alpha$ are worse than the ones used for cold gas observations (see also Sect [1](#sec:intro)). For instance, the spectral resolution (FWHM) of the SAMI data is $\approx 70$ km/s, while the one for the KMOS data used by (cite: Birkin_2023) is $\approx 150$ km/s. In addition, the IFU data at $z \sim 2$ are taken in seeing-limited mode (resolution of $\approx$0.6", a factor of 3 worse than the ALMA data), resulting in H$\alpha$ emission which are only marginally resolved in some cases (cite: Hogan_2021; Birkin_2023). As a result of these observational limitations, the warm gas $\sigma$ may be overestimated by some factor. This latter is not straightforward to quantify, as it would require the modelling of several mock datacubes at different spatial and spectral resolutions and for galaxies with different properties (e.g., size, inclination), a task beyond the scope of this work.

## Different cold gas tracers

In this study, we investigate the kinematics of cold gas (T$< 10^4$ K) using a range of emission lines, including multiple CO transitions, \[CI\], and \[CII\]. While we expect minimal differences in the kinematics among various CO transitions and \[CI\] lines (cite: Rizzo_2023), the \[CII\] emission line may exhibit variations compared to the kinematics traced by CO and \[CI\] lines. Having a lower ionization potential than HI (11.3 eV instead of 13.6 eV), \[CII\] can be generated in multiple phases of the ISM, including molecular, atomic, and ionized phases (cite: Rigopoulou_2014; Diaz_santos_2017; Wolfire_2022), although several studies suggest that the majority (60 - 80%) of \[CII\] emission arises from the molecular gas phase (cite: Pineda_2013; Vallini_2015; DeBreuck_2019). As a rough estimate, if \[CII\] originates from warmer gas (T $\approx 10^2 -10^3$ K) than that traced by CO (T $\lesssim 10^2$ K), we estimate a thermal broadening speed of $\approx$ 2 km/s. Consequently, similar to CO at $z < 4$, the dominant contribution to the \[CII\] broadening ($\approx 30$ - 40 km/s) at $z = 4 - 5$ stems from gas turbulence. Conversely, if \[CII\] originates from the diffuse atomic and ionized phases, we expect \[CII\] velocity dispersion values that are, on average, larger than CO values. The absence of kinematic studies on both CO and \[CII\] for the same galaxies, both locally and at high-$z$, precludes us from providing quantitative estimates at present. However, future observations can potentially complement ALMA observations of \[CII\] at $z > 3$ with CO or \[CI\] observations using the high-frequency bands of the Square Kilometre Array (cite: Braun_2019) or the next generation Very Large Array (cite: Kadler_2023). Considering that the average \[CII\] $\sigma$ at $z > 4$ is only about 1.2 times larger than those measured at $z \sim 2$, any disparities between CO and \[CII\] kinematics would strengthen our findings, further attenuating the redshift evolution of turbulent motion.

## Considerations on SFR

The model presented in Sect. [5](#sec:model) relies on the $\sigma$-SFR relation. However, the SFR values of the extended sample are derived from diverse methodologies and assumptions as they are taken from the literature. We normalized the SFR values to a common IMF, but variations in assumptions and methodologies may introduce scatter (cite: Pacifici_2023).

Although radial profiles of $\sigma$ are available for the majority of galaxies within our extended sample, the absence of SFR surface density maps impedes an investigation of the efficiency of the turbulence drivers as a function of the galactocentric distance, as has been done for local galaxy samples (cite: Utomo_2019; Bacchini_2020). Analyzing global $\sigma$ and SFR values enables an assessment of the primary mechanisms driving turbulence. Future high-quality observations mapping the H$\alpha$ or UV emission will allow us to obtain spatially-resolved maps of the SFR distribution and finally investigate the relative role of different driving mechanisms in the different regions of galaxies.

# Summary and conclusions

In this study, we analyze the redshift evolution of galaxy dynamics (i.e., $\sigma$, $V/\sigma$) using kinematics from cold gas tracers (CO, \[CI\], \[CII\]). Our initial sample consists of 17 galaxy disks from the ALPAKA sample with high data quality. We complement ALPAKA with $\sigma$ and $V/\sigma$ measurements from the literature for subsamples of galaxies with spatially-resolved observations of emission lines tracing cold gas. This extended sample consists of 57 main-sequence and starburst disks at $z = 0 - 5$ and it covers a narrow range in stellar masses ($M_{\star} \approx 10^{10} - 10^{11} M_{\odot}$), but a wide range of 4 order of magnitude in SFRs. Our main results are the following.

- There is a trend of $\sigma$ increasing by around 2 to 3 times across the redshift range $z = 0 - 1$, while $V/\sigma$ decreases by a similar amount. However, these trends become less apparent at $z > 1$, where both $\sigma$ and $V/\sigma$ exhibit a plateau. We quantify the observed evolution using empirical relations, even though the derived trends reflect the heterogeneity of our extended sample, consisting of galaxies with a large range of SFRs.

- We compare the kinematics of cold gas from our extended sample with the ones of warm gas. For the latter, we selected galaxies from the literature with physical properties (i.e., $M_{\star}$, SFR) matching the ones of our extended sample. The values of $\sigma$ ($V/\sigma$) from H$\alpha$ are a factor of $\approx 3$ higher (lower) than the ones from cold gas both for low and high-$z$ galaxies.

- We investigate the potential drivers of turbulence and find that stellar feedback can reproduce the observed turbulence, traced by velocity dispersion measurements obtained from cold gas tracers. In contrast, gravitational instabilities tend to overpredict turbulence measured from cold gas. This finding diverges from previous studies based on warm gas kinematics, which suggested that turbulence is mainly driven by gravitational instabilities in $z > 1$ galaxies.

- We present a physically-motivated model predicting that turbulence is fed by the energy injected into the ISM by supernova explosions, and that the physics of turbulence driving does not to evolve with time. We calibrated this model on observations and developed a semi-empirical framework to predict the redshift evolution of turbulence in star-forming galaxies based on the evolution of the main-sequence relation. This model suggests a mild increase in turbulence within the redshift range 0 - 2 and no significant evolution at $z > 2$ for populations of galaxies at fixed stellar mass. Within this framework, for a Milky-Way-like progenitor, the velocity dispersion from cold gas evolve from $\approx 16$ km/s to 6 km/s in the last 10 Gyr ($z \lesssim 2$) of cosmic history. Interestingly, the supernova-driven model indicates that galaxies with lower stellar masses have lower velocity dispersion compared to more massive counterparts. By combining this model with the local stellar Tully-Fisher relation, we set lower limits for the redshift evolution of $V/\sigma$ at fixed stellar mass. We predict that high-$z$, low mass ($M_{\star} \gtrsim 10^9 M_{\odot}$) galaxy disks should be rotationally supported, with $V/\sigma \sim 10$.

The results presented in this paper indicate that the dynamical properties of galaxies significantly differ when derived from warm or cold gas. This work highlights the importance of studying the evolution of galaxy dynamics, the turbulence within the ISM and its origin using cold gas tracers. The difference between cold and warm gas kinematics evidenced in our analysis may be due to (i) diffuse nature of warm, ionized gas compared to the cold one; (ii) bias of the velocity dispersion measurements to higher values due to contamination from non-circular motions due to outflows; (iii) insufficient spectral and angular resolution. In the future, studies of the ionized gas kinematics using high angular and spectral resolution observations (FWHM $\lesssim 40$ km/s, e.g., VLT/ERIS; ELT/HARMONI) will be able to discriminate between these three hypotheses.

The supernova-driven model presented in this paper makes testable predictions on the evolution of turbulence in galaxy disks across cosmic time. As more cold gas observations of star-forming galaxies with a wide range of stellar masses will be collected over the next years, we should be able to gain a more complete picture on the formation of the progenitors of disks in Milky-Way-like and local spiral galaxies.

# Acknowledgements

The author thank the anonymous referee for constructive comments and suggestions. FR is grateful to Pavel Mancera Piña for useful comments and discussions. FR acknowledges support from the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska-Curie grant agreement No. 847523 ‘INTERACTIONS’. This work has been supported by the Cosmic Dawn Center (DAWN), funded by the Danish National Research Foundation under grant No. 140. CB acknowledges support from the Carlsberg Foundation Fellowship Programme by Carlsbergfondet. LDM acknowledges support from the French government, through the UCA^J.E.D.I.^ Investments in the Future project managed by the National Research Agency (ANR) with the reference number ANR-15-IDEX-01. FRO acknowledges support from the Dutch Research Council (NWO) through the Klein-1 Grant code OCEN2.KLEIN.088. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01659.S; ADS/JAO.ALMA#2017.1.00471.S; ADS/JAO.ALMA#2017.1.01674.S; ADS/JAO.ALMA#2015.1.00862.S; ADS/JAO.ALMA#2017.1.01228.S; ADS/JAO.ALMA#2018.1.00974.S; ADS/JAO.ALMA#2017.1.00413.S; ADS/JAO.ALMA#2019.1.01362.S; ADS/JAO.ALMA#2017.1.01045.S; ADS/JAO.ALMA#2013.1.00059.S; ADS/JAO.ALMA#2018.1.00543.S; ADS/JAO.ALMA#2015.1.00723.S; ADS/JAO.ALMA#2018.1.01146.S; ADS/JAO.ALMA#2016.1.01155.S; ADS/JAO.ALMA#2017.1.01677.S; ADS/JAO.ALMA#2018.1.01306.S; ADS/JAO.ALMA#2017.1.00908.S; ADS/JAO.ALMA#2012.1.00650.S; ADS/JAO.ALMA#2013.1.00803.S; ADS/JAO.ALMA#2013.1.01161.S; ADS/ JAO.ALMA#2015.1.00121.S; ADS/JAO.ALMA#2015.1.00782.S; ADS/JAO.ALMA#2015.1.00925.S; ADS/JAO.ALMA#2015.1.00956.S; ADS/JAO.ALMA#2016.1.00386.S; ADS/JAO.ALMA#2017.1.00392.S; ADS/JAO.ALMA#2017.1.00766.S; ADS/JAO.ALMA#2017.1.00886.L; ADS/JAO.ALMA#2018.1.00484.S; ADS/JAO.ALMA#2018.1.01321.S; ADS/JAO.ALMA#2018.1.01 651.S; ADS/JAO.ALMA#2018.A.00062.S; ADS/JAO.ALMA#2019.1.01235.S; ADS/JAO.ALMA#2019.2.00129.S; ADS/JAO.ALMA#2016.1.01499.S; ADS/JAO.ALMA#2015.1.00330.S; ADS/JAO.ALMA#2017.1.00127.S; ADS/JAO.ALMA#2017.1.00394.S; ADS/JAO.ALMA#2017.1.01052.S; ADS/JAO.ALMA#2018.1.00001.S; ADS/JAO.ALMA#2017.1.01020.S; ADS/JAO.ALMA#2019.1.00862.S; ADS/JAO.ALMA#2017.1.01471.S; ADS/JAO.ALMA#2015.1.00456.S; ADS/JAO.ALMA#2011.0.00124.S; ADS/JAO.ALMA#2012.1.00978.S; ADS/JAO.ALMA#2015.1.01564.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.\
We acknowledge usage of the Python programming language (cite: python3), Astropy (cite: astropy), Matplotlib (cite: matplotlib), NumPy (cite: numpy), and SciPy (cite: scipy).

119 natexlab

(ref: astropy) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Bacchini_2019) Bacchini, C., Fraternali, F., Iorio, G., & Pezzulli, G. 2019, A&A, 622, A64

(ref: Bacchini_2020) Bacchini, C., Fraternali, F., Iorio, G., et al. 2020a, A&A, 641, A70

(ref: Bacchini_2020b) Bacchini, C., Fraternali, F., Pezzulli, G., & Marasco, A. 2020b, A&A, 644, A125

(ref: Bacchini_2024) Bacchini, C., Nipoti, C., Iorio, G., et al. 2024, arXiv e-prints, arXiv:2405.00103

(ref: Birkin_2023) Birkin, J. E., Smail, I., Swinbank, A. M., et al. 2023, arXiv e-prints, arXiv:2301.05720

(ref: Bland_2016) Bland-Hawthorn, J. & Gerhard, O. 2016, ARA&A, 54, 529

(ref: Bournaud_2010) Bournaud, F., Elmegreen, B. G., Teyssier, R., Block, D. L., & Puerari, I. 2010, MNRAS, 409, 1088

(ref: Bournaud_2014) Bournaud, F., Perret, V., Renaud, F., et al. 2014, ApJ, 780, 57

(ref: Braun_2019) Braun, R., Bonaldi, A., Bourke, T., Keane, E., & Wagg, J. 2019, arXiv e-prints, arXiv:1912.12699

(ref: Carilli_2013) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: Carpenter_2020) Carpenter, J., Iono, D., Kemper, F., & Wootten, A. 2020, arXiv e-prints, arXiv:2001.11076

(ref: Chabrier_2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Cioffi_1988) Cioffi, D. F., McKee, C. F., & Bertschinger, E. 1988, ApJ, 334, 252

(ref: Croom_2012) Croom, S. M., Lawrence, J. S., Bland-Hawthorn, J., et al. 2012, MNRAS, 421, 872

(ref: Curran_2014) Curran, P. A. 2014, arXiv e-prints, arXiv:1411.3816

(ref: DeBreuck_2019) De Breuck, C., Weiß, A., Béthermin, M., et al. 2019, A&A, 631, A167

(ref: Dekel_2013) Dekel, A., Zolotov, A., Tweed, D., et al. 2013, MNRAS, 435, 999

(ref: DiMascolo2024) Di Mascolo, L. 2024, lucadimascolo/scattr

(ref: DiTeodoro_2015) Di Teodoro, E. M. & Fraternali, F. 2015, MNRAS, 451, 3021

(ref: DiTeodoro_2016) Di Teodoro, E. M., Fraternali, F., & Miller, S. H. 2016, A&A, 594, A77

(ref: Diaz_santos_2017) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32

(ref: Dutton_2011) Dutton, A. A., van den Bosch, F. C., Faber, S. M., et al. 2011, MNRAS, 410, 1660

(ref: Elmegreen_2004) Elmegreen, B. G. & Scalo, J. 2004, ARA&A, 42, 211

(ref: Epinat_2008) Epinat, B., Amram, P., & Marcelin, M. 2008, MNRAS, 390, 466

(ref: Epinat_2009) Epinat, B., Contini, T., Le Fèvre, O., et al. 2009, A&A, 504, 789

(ref: Fisher_2014) Fisher, D. B., Glazebrook, K., Bolatto, A., et al. 2014, ApJL, 790, L30

(ref: Fisher_2017) Fisher, D. B., Glazebrook, K., Damjanov, I., et al. 2017, MNRAS, 464, 491

(ref: Forbes_2023) Forbes, J. C., Emami, R., Somerville, R. S., et al. 2023, ApJ, 948, 107

(ref: Forster_2009) Förster Schreiber, N. M., Genzel, R., Bouché, N., et al. 2009, ApJ, 706, 1364

(ref: Forster_2018) Förster Schreiber, N. M., Renzini, A., Mancini, C., et al. 2018, ApJS, 238, 21

(ref: Forster_2020) Förster Schreiber, N. M. & Wuyts, S. 2020, ARA&A, 58, 661

(ref: Fraternali_2021) Fraternali, F., Karim, A., Magnelli, B., et al. 2021, A&A, 647, A194

(ref: Genzel_2011) Genzel, R., Newman, S., Jones, T., et al. 2011, ApJ, 733, 101

(ref: Ginzburg_2022) Ginzburg, O., Dekel, A., Mandelker, N., & Krumholz, M. R. 2022, MNRAS, 513, 6177

(ref: Girard_2019) Girard, M., Dessauges-Zavadsky, M., Combes, F., et al. 2019, A&A, 631, A91

(ref: Girard_2021) Girard, M., Fisher, D. B., Bolatto, A. D., et al. 2021, ApJ, 909, 12

(ref: Green_2014) Green, A. W., Glazebrook, K., McGregor, P. J., et al. 2014, MNRAS, 437, 1070

(ref: Harrison_2017) Harrison, C. M., Johnson, H. L., Swinbank, A. M., et al. 2017, MNRAS, 467, 1965

(ref: Hayward_2017) Hayward, C. C. & Hopkins, P. F. 2017, MNRAS, 465, 1682

(ref: Hoffman_2011) Hoffman, M. D. & Gelman, A. 2011, arXiv e-prints, arXiv:1111.4246

(ref: Hogan_2021) Hogan, L., Rigopoulou, D., Magdis, G. E., et al. 2021, MNRAS, 503, 5329

(ref: matplotlib) Hunter, J. D. 2007, Computing in Science Engineering, 9, 90

(ref: Ianjamasimanana_2015) Ianjamasimanana, R., de Blok, W. J. G., Walter, F., et al. 2015, AJ, 150, 47

(ref: Jimenez_2023) Jiménez, E., Lagos, C. d. P., Ludlow, A. D., & Wisnioski, E. 2023, MNRAS, 524, 4346

(ref: Johnson_2018) Johnson, H. L., Harrison, C. M., Swinbank, A. M., et al. 2018, MNRAS, 474, 5076

(ref: Kadler_2023) Kadler, M., Riechers, D. A., Baczko, A. K., et al. 2023, arXiv e-prints, arXiv:2311.10056

(ref: Kassin_2012) Kassin, S. A., Weiner, B. J., Faber, S. M., et al. 2012, ApJ, 758, 106

(ref: Kelly_2007) Kelly, B. C. 2007, ApJ, 665, 1489

(ref: Kendall_1973) Kendall, M. & Stuart, A. 1973, The Advanced Theory of Statistics. Vol. 2: Inference and: Relationsship (Griffin)

(ref: Kim_2015) Kim, C.-G. & Ostriker, E. C. 2015, ApJ, 815, 67

(ref: Kim_2017) Kim, C.-G. & Ostriker, E. C. 2017, ApJ, 846, 133

(ref: Klessen_2010) Klessen, R. S. & Hennebelle, P. 2010, A&A, 520, A17

(ref: Kohandel_2020) Kohandel, M., Pallottini, A., Ferrara, A., et al. 2020, MNRAS, 499, 1250

(ref: Kohandel_2024) Kohandel, M., Pallottini, A., Ferrara, A., et al. 2023, arXiv e-prints, arXiv:2311.05832

(ref: Kramer_2016) Kramer, E. D. & Randall, L. 2016, ApJ, 829, 126

(ref: Kret_2022) Kretschmer, M., Dekel, A., & Teyssier, R. 2022, MNRAS, 510, 3266

(ref: Krumholz_2016) Krumholz, M. R. & Burkhart, B. 2016, MNRAS, 458, 1671

(ref: Krumholz_2018) Krumholz, M. R., Burkhart, B., Forbes, J. C., & Crocker, R. M. 2018, MNRAS, 477, 2716

(ref: Law_2022) Law, D. R., Belfiore, F., Bershady, M. A., et al. 2022, ApJ, 928, 58

(ref: Lelli_2022) Lelli, F. 2022, Nature Astronomy, 6, 35

(ref: Lelli_2021) Lelli, F., Di Teodoro, E. M., Fraternali, F., et al. 2021, Science, 371, 713

(ref: Lelli_2023) Lelli, F., Zhang, Z.-Y., Bisbas, T. G., et al. 2023, A&A, 672, A106

(ref: Leroy_2021b) Leroy, A. K., Hughes, A., Liu, D., et al. 2021a, ApJS, 255, 19

(ref: Leroy_2021) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021b, ApJS, 257, 43

(ref: Leroy_2009) Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137, 4670

(ref: Maclow_2004) Mac Low, M.-M. & Klessen, R. S. 2004, Reviews of Modern Physics, 76, 125

(ref: Maclow_1998) Mac Low, M.-M., Klessen, R. S., Burkert, A., & Smith, M. D. 1998, , 80, 2754

(ref: Marasco_2017) Marasco, A., Fraternali, F., van der Hulst, J. M., & Oosterloo, T. 2017, A&A, 607, A106

(ref: Martizzi_2015) Martizzi, D., Faucher-Giguère, C.-A., & Quataert, E. 2015, MNRAS, 450, 504

(ref: Mogotsi_2016) Mogotsi, K. M., de Blok, W. J. G., Caldú-Primo, A., et al. 2016, AJ, 151, 15

(ref: Neal_2011) Neal, R. 2011, in Handbook of Markov Chain Monte Carlo, 113–162

(ref: Neeleman_2020) Neeleman, M., Prochaska, J. X., Kanekar, N., & Rafelski, M. 2020, Nature, 581, 269

(ref: Orr_2020) Orr, M. E., Hayward, C. C., Medling, A. M., et al. 2020, MNRAS, 496, 1620

(ref: Ostriker_2022) Ostriker, E. C. & Kim, C.-G. 2022, ApJ, 936, 137

(ref: Ostriker_2011) Ostriker, E. C. & Shetty, R. 2011, ApJ, 731, 41

(ref: Pacifici_2023) Pacifici, C., Iyer, K. G., Mobasher, B., et al. 2023, ApJ, 944, 141

(ref: Pallottini_2022) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2022, MNRAS, 513, 5621

(ref: Parlanti_2023) Parlanti, E., Carniani, S., Übler, H., et al. 2023, arXiv e-prints, arXiv:2309.05713

(ref: Pillepich_2019) Pillepich, A., Nelson, D., Springel, V., et al. 2019, MNRAS, 490, 3196

(ref: Pineda_2013) Pineda, J. L., Langer, W. D., Velusamy, T., & Goldsmith, P. F. 2013, A&A, 554, A103

(ref: Pope_2023) Pope, A., McKinney, J., Kamieneski, P., et al. 2023, ApJL, 951, L46

(ref: Popesso_2023) Popesso, P., Concas, A., Cresci, G., et al. 2023, MNRAS, 519, 1526

(ref: Posses_2023) Posses, A. C., Aravena, M., González-López, J., et al. 2023, A&A, 669, A46

(ref: Puglisi_2023) Puglisi, A., Dudzevičiūtė, U., Swinbank, M., et al. 2023, MNRAS, 524, 2814

(ref: Reyes_2011) Reyes, R., Mandelbaum, R., Gunn, J. E., Pizagno, J., & Lackner, C. N. 2011, MNRAS, 417, 2347

(ref: Rigopoulou_2014) Rigopoulou, D., Hopwood, R., Magdis, G. E., et al. 2014, ApJL, 781, L15

(ref: Rizzo_2022) Rizzo, F., Kohandel, M., Pallottini, A., et al. 2022, A&A, 667, A5

(ref: Rizzo_2023) Rizzo, F., Roman-Oliveira, F., Fraternali, F., et al. 2023, A&A, 679, A129

(ref: Rizzo_2021) Rizzo, F., Vegetti, S., Fraternali, F., Stacey, H. R., & Powell, D. 2021, MNRAS, 507, 3952

(ref: Rizzo_2020) Rizzo, F., Vegetti, S., Powell, D., et al. 2020, Nature, 584, 201

(ref: Rodighiero_2011) Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, ApJL, 739, L40

(ref: Roman_2023) Roman-Oliveira, F., Fraternali, F., & Rizzo, F. 2023, MNRAS, 521, 1045

(ref: Roman_2024) Roman-Oliveira, F., Fraternali, F., & Rizzo, F. 2024, MNRAS, 521, 1045

(ref: Sawicki_2012) Sawicki, M. 2012, PASP, 124, 1208

(ref: Scott_2018) Scott, N., van de Sande, J., Croom, S. M., et al. 2018, MNRAS, 481, 2299

(ref: Sereno_2016) Sereno, M. 2016, MNRAS, 455, 2149

(ref: Simons_2016) Simons, R. C., Kassin, S. A., Trump, J. R., et al. 2016, ApJ, 830, 14

(ref: Simons_2017) Simons, R. C., Kassin, S. A., Weiner, B. J., et al. 2017, ApJ, 843, 46

(ref: Stott_2016) Stott, J. P., Swinbank, A. M., Johnson, H. L., et al. 2016, MNRAS, 457, 1888

(ref: Tacconi_2013) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74

(ref: Thornton_1998) Thornton, K., Gaudlitz, M., Janka, H. T., & Steinmetz, M. 1998, ApJ, 500, 95

(ref: Toomre) Toomre, A. 1964, ApJ, 139, 1217

(ref: Tsukui_2021) Tsukui, T. & Iguchi, S. 2021, Science, 372, 1201

(ref: Tully) Tully, R. B. & Fisher, J. R. 1977, A&A, 54, 661

(ref: Turner_2017) Turner, O. J., Cirasuolo, M., Harrison, C. M., et al. 2017, MNRAS, 471, 1280

(ref: Ubler_2018) Übler, H., Genzel, R., Tacconi, L. J., et al. 2018, ApJL, 854, L24

(ref: Ubler_2019) Übler, H., Genzel, R., Wisnioski, E., et al. 2019, ApJ, 880, 48

(ref: Utomo_2019) Utomo, D., Blitz, L., & Falgarone, E. 2019, ApJ, 871, 17

(ref: Vallini_2015) Vallini, L., Gallerani, S., Ferrara, A., Pallottini, A., & Yue, B. 2015, ApJ, 813, 36

(ref: numpy) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science Engineering, 13, 22

(ref: vandokkum_2013) van Dokkum, P. G., Leja, J., Nelson, E. J., et al. 2013, ApJL, 771, L35

(ref: python3) Van Rossum, G. & Drake, F. L. 2009, Python 3 Reference Manual (Scotts Valley, CA: CreateSpace)

(ref: Varidel_2020) Varidel, M. R., Croom, S. M., Lewis, G. F., et al. 2020, MNRAS, 495, 2265

(ref: Vehtari_2015) Vehtari, A., Gelman, A., & Gabry, J. 2015, arXiv e-prints, arXiv:1507.04544

(ref: scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: Whitaker_2012) Whitaker, K. E., van Dokkum, P. G., Brammer, G., & Franx, M. 2012, ApJL, 754, L29

(ref: Wisnioski_2015) Wisnioski, E., Förster Schreiber, N. M., Wuyts, S., et al. 2015, ApJ, 799, 209

(ref: Wolfire_2022) Wolfire, M. G., Vallini, L., & Chevance, M. 2022, ARA&A, 60, 247

# Catalogue and table for the extended sample

With this paper we release[^1] a catalogue containing the physical properties for the 57 galaxies in the extended sample. The kinematic analysis of these galaxies is presented and discussed in previous papers (see Table [\[tab:tab1\]](#tab:tab1)), with the exception of the PHANGS galaxies. For the latter, we used the combined 12-m and 7-m publicly available data cubes[^2] (cite: Leroy_2021b; Leroy_2021) to fit their kinematics using $^{\scriptstyle 3\mathrm{D}}$B. The parameter files used for the fitting and the corresponding outputs are available online [^3].

# Fitting empirical relations

To fit Eqs. ([\[eq:sigma\]](#eq:sigma)), ([\[eq:vsigma\]](#eq:vsigma)) and ([\[eq:sigma-sfr\]](#eq:sigma-sfr)), we use a hierarchical Bayesian approach[^4] for the estimation of the likelihood function of the measured data (cite: Kelly_2007; Sereno_2016). This hierarchical Bayesian method accounts for measurement uncertainties, intrinsic scatter, and upper limits. The sampling is performed by means of a Hamiltonian Monte Carlo (HMC; (cite: Neal_2011)) inference approach, with No U-Turn Sampler (cite: Hoffman_2011) adaptation of the HMC step length.

## Fitting equations ([\[eq:sigma\]](#eq:sigma)) and ([\[eq:vsigma\]](#eq:vsigma))

We aim at constraining the set of free parameters $\vec{\theta} = \{a, b, z_{0}\}$ of a given functional form $f(z;\vec{\theta})$ (i.e., Eq. ([\[eq:sigma\]](#eq:sigma)) or ([\[eq:vsigma\]](#eq:vsigma))) described by a set of independent variables $z$ and observed quantities $y$ (i.e., $\sigma$, $V/\sigma$). Here, we assume $z$ to represent a set of measurements not affected by intrinsic scatter and characterized by negligible uncertainties. This is related to the corresponding observed quantity $y$ through the relation

$$\begin{equation}
    y = \eta_y(z)+\epsilon_{y},
\end{equation}$$

where $\epsilon_y$ is the corresponding measurement uncertainty that follows a normal probability distribution with known variance $u^2_y$. The parameter $\eta_y$ instead represents the true value of the observed quantity $y$. To account for any potential scatter intrinsic to the measurement process or the measured quantities themselves, we assume $\eta$ to be drawn from the conditional distribution $p(\eta|z,\vec{\theta})$, assumed to be a normal density distribution $\mathcal{N}\{f(z;\vec{\theta}),s^2_{y}\}$ with mean equal to $f(z;\vec{\theta})$ and variance $s_{y}^2$. The latter term specifically quantifies the intrinsic scatter of the analysed data around the mean relation $f(z;\vec{\theta})$, and we include it as free parameter in the fit. The likelihood function of each measured data point is thus given by

$$\begin{equation}
    p(y|z,\vec{\theta}) = \int p(y|z, \eta) p (\eta| z,\vec{\theta}) d\eta.
\end{equation}$$ Since the data points are statistically independent, the full likelihood is the product of the likelihood function for the individual data points. For the prior probability of each model parameter, we assume wide uniform priors (see Table [3](#tab:priors)).

| Parameter |  $\sigma$  | $V/\sigma$ |
|:---------:|:----------:|:----------:|
|    $a$    | \[0, 100\] | \[0, 100\] |
|    $b$    | \[0, 100\] | \[0, 100\] |
|  $z_{0}$  | \[0, 10\]  | \[0, 10\]  |
|  $s_{y}$  | \[0, 100\] | \[0, 100\] |

: Ranges of the uniform priors used to perform the fitting of the $\sigma$-$z$ and $V/\sigma$-$z$ distributions using Eqs. ([\[eq:sigma\]](#eq:sigma)) and ([\[eq:vsigma\]](#eq:vsigma)).

![](figures/corner_sigma_z.png)

![](figures/corner_vsigma_z.png)

.

## Fitting equation ([\[eq:sigma-sfr\]](#eq:sigma-sfr))

In this case, both the independent ($\sigma$) and dependent variable (SFR) sets comprise observed quantities. As such, we should account for any associated measurement uncertainties and potential intrinsic scatter in both cases. To do so, we extend the hierarchical approach presented in the previous section to both the dependent and independent variables $x \equiv \sigma$ and $y \equiv$ SFR: $$\begin{equation}
    \begin{split}
        x &= \eta_{x}(\xi)+\epsilon_x, \hspace{1cm} \eta_{x}=\mathcal{N}\{f_x(\xi;\vec{\theta}_x),s^{2}_{x}\}\\
        y &= \eta_{y}(\xi)+\epsilon_y, \hspace{1cm} \eta_{y}=\mathcal{N}\{f_y(\xi;\vec{\theta}_y),s^{2}_{y}\}.
    \end{split}
\end{equation}$$ In accordance with the notation in Sec. [9.1](#sec:fit:1), the variables $\eta_i$, $\epsilon_i$, denote the true values and measurement uncertainties of each variable $i=\{x,y\}$, respectively, and the corresponding functional model $f_i$, parameters $\vec{\theta}_i$ and intrinsic scatter$s^2_i$. Following (cite: Kelly_2007; Sereno_2016), we further define $\xi$ as a reference independent variable drawn from a mixture of Gaussian probability distributions and related to the true values $\eta_{i}$ through the normal probability distributions $\mathcal{N}(f_i;s^2_i)$. In our specific case, $$\begin{equation}
 \label{eq:linear}
    \begin{split}
        f_x & = f_x(\xi) = 10^{\xi}, \\
        f_y & = f_y(\xi;b) = 10^{0.33\xi+b}.
    \end{split}
\end{equation}$$

For the prior probability on the offset parameter $b$ in Eq. ([\[eq:linear\]](#eq:linear)), we assume a wide uniform prior in the range $[-100, 100]$. The joint likelihood function can instead be rewritten as

$$\begin{equation}
    p(x,y|\vec{\theta}) = \iint p(x,y|\eta_x,\eta_y) p(\eta_y|\xi,\vec{\theta}) p(\eta_x|\xi,\vec{\theta}) p(\xi) d\eta_x d\eta_y,
\end{equation}$$ where $p(\xi)$ is the underlying Gaussian mixture model. The term $p(x,y|\eta_x,\eta_y)$ represents the joint likelihood distribution for the $\{x,y\}$ variables at given $\{\eta_x,\eta_y\}$ and, such, could be interpreted as the probability function accounting for the uncertainties on each observed quantity. For most of the data in our sample, this can be described as a normal distribution with mean equal to the observed quantity $i$ and variance $u^2_i$ ($i=\{x,y\}$). However, for a subset of the analysed sample, we have access only to marginal constrain on the corresponding observed $y$ values. For these data points, we thus encode the available upper limits in the probability function $p(x,y|\eta_x,\eta_y)$ following the prescription by (cite: Sawicki_2012) and considering the cumulative distribution function of a normal probability distribution integrated up to the given upper limit. For a given set of $n$ independent data points $\{x,y\}$ with $m$ available upper limits on $y$, we can express the joint likelihood distribution as follows: $$\begin{equation}
    \begin{split}
        p(x,y | \eta_x,\eta_y) 
             = &\prod^{n}_{k=1}\frac{1}{\sqrt{2\pi ~ u^2_{x,k}}}\exp{\left\{-\frac{1}{2}\left(\frac{x_{k}-\eta_{x,k}}{u_{x,k}}\right)^2\right\}} \\
        \times~ &\prod^{n-m}_{k=1}\frac{1}{\sqrt{2\pi ~ u^2_{y,k}}}\exp{\left\{-\frac{1}{2}\left(\frac{y_{k}-\eta_{y,k}}{u_{y,k}}\right)^2\right\}} \\
        \times~ &\prod^{n}_{k=m} \frac{1}{2}\left[1+\mathrm{erf}\left(\frac{y_{k}-\eta_{y,k}}{\sqrt{2}~u_{y,k}}\right)\right].
    \end{split}
\end{equation}$$

# Further comparison with previous works

## Warm gas kinematics from main-sequence galaxies

In Sect. [3.2](#sec:comparison), we compare the redshift distribution of $\sigma$ from cold gas with the warm gas observations and models. Such comparison was conducted using observational samples that match the physical properties (i.e., stellar masses, SFR) of our extended sample. In this Section, we compare the cold gas $\sigma$ with the warm gas $\sigma$ derived using samples of main-sequence galaxies with a wider range of stellar masses than our extended sample.

![](figures/evolution_appendix.png)

In Fig. [11](#fig:vs_main), the black dashed line represents the $\sigma$-redshift relation derived by (cite: Ubler_2019). This relation was established by fitting warm gas $\sigma$ measurements from various IFU studies spanning $z = 0 - 3.8$ and comprising around 500 galaxies, while the line extension beyond $z = 3.8$ is based on an extrapolation. The compilation by (cite: Ubler_2019) includes main-sequence galaxies with stellar masses in the range $\log(M_{\star}/M_{\odot}) = 9 - 11.5$. The dashed gray line in Fig. [11](#fig:vs_main) represents the $\sigma$-$z$ relation derived by (cite: Simons_2017) using H$\alpha$ slit observations from the DEEP2 (cite: Kassin_2012) and SIGMA (cite: Simons_2016) surveys, which include around 500 main-sequence galaxies with $\log(M_{\star}/M_{\odot}) = 9 - 11.5$ at $z = 0.1 - 2.5$. Interestingly, (cite: Simons_2017) find that the $\sigma$-redshift relation does not exhibit strong dependence on stellar mass, although simulations suggest that, on average, low-mass galaxies have lower velocity dispersions than high-mass galaxies (cite: Pillepich_2019; Kohandel_2024). However, this discrepancy between observations and simulations might be explained by a systematic bias towards high $\sigma$ due to the beam-smearing effect (Sect. [6](#sec:caveats)). This effect might be amplified in low-mass galaxies, which are typically only marginally resolved (cite: Ubler_2019). Similarly to the results described in Sect. [3.2](#sec:comparison), both the relations by (cite: Ubler_2019) and (cite: Simons_2017), derived from warm gas, systematically overestimate the values of the majority of CO/\[CII\] $\sigma$ of our extended sample.

## Cold gas kinematics

To date, comprehensive investigations of the evolution of galaxy dynamics, leveraging kinematic data derived from cold gas tracers, remain largely unexplored due to the dearth of spatially-resolved observations for large samples of galaxies at redshifts beyond $z > 0$. An initial endeavor in this direction was undertaken by (cite: Ubler_2019), who assembled a dataset comprising 9 main-sequence galaxies spanning the redshift range $z = 0.7 - 2.4$, with low-angular resolution ($\gtrsim 0.6$") CO observations (cite: Tacconi_2013; Ubler_2018). The dotted purple line in Fig. [11](#fig:vs_main) is from (cite: Ubler_2019) and represents the first attempt to establish an empirical relation describing the evolution of $\sigma$ with redshift using cold gas kinematics. The best-fit relation found by (cite: Ubler_2019) is in overall agreement with the one obtained in Sect. [3.1](#sec:bestfit) in the redshift range $z = 0.7 - 2$. However, (cite: Ubler_2019) do not provide an explanation for the data re-processing procedure used to infer the adopted CO $\sigma$ values, most of which are systematically lower ($\sim2\times$) than the original values reported in the first paper describing their kinematic analysis (cite: Tacconi_2013). In Fig. [11](#fig:vs_main), we show the extrapolation of the $\sigma$-$z$ at $z > 2.4$. As noted already by (cite: Rizzo_2021), this extrapolation tends to overestimate, on average, the values of $\sigma$ measured at $z > 2$.

## Disk instability model and H$\alpha$ observations

In Sect. [3.2](#sec:comparison), we compare the evolution of galaxy dynamics from cold gas with the predictions of the disk-instability model (cite: Wisnioski_2015). To estimate the expected values of $\sigma_{\mathrm{exp, DI}}$ and $(V/\sigma)_{\mathrm{exp, DI}}$, we use Eq. ([\[eq:di1\]](#eq:di1)) and Eq. ([\[eq:di2\]](#eq:di2)) adopting our $f_{\mathrm{gas}}$ measurements. Given that $z = 0$ galaxies are not unstable (i.e., $Q \gg 1$), we compute $\sigma_{\mathrm{exp, DI}}$ and $(V/\sigma)_{\mathrm{exp, DI}}$ only for the galaxies that are expected to be unstable according to the Toomre instability criterion: low-$z$ starbursts (cite: Girard_2021) and galaxies at $z > 0$ (cite: Wisnioski_2015; Turner_2017; Johnson_2018). In Fig. [12](#fig:fit_di), we show the best-fit relations, obtained by fitting Eqs. ([\[eq:sigma\]](#eq:sigma)) and ([\[eq:vsigma\]](#eq:vsigma)) to the redshift distributions of $\sigma_{\mathrm{exp, DI}}$ and $(V/\sigma)_{\mathrm{exp, DI}}$.

![](figures/evolution_di2.png)

# Assumptions of feedback models

## Krumholz et al. 2018

The feedback models in K18 are derived under the assumption that the energy injected into the ISM by supernova explosions drives the turbulence. Unlike the approach taken by F21 (see Sect. [5.1](#sec:sfrmodel)), K18 define the rate at which star formation adds energy to the gas not in terms of the energy injected by each supernova $E_{\mathrm{SN}}$ but in terms of the mean momentum injected per unit mass of stars formed ($p_{\star}/m_{\star})$, which is assumed to be 3000 km/s, based on numerical simulations (cite: Cioffi_1988; Thornton_1998; Martizzi_2015; Kim_2017). The rate of energy injected by supernovae into the ISM per unit area is, therefore, defined, as $$\begin{equation}
\dot{E}_{\mathrm{SN, K18}} = \Sigma_{\mathrm{SFR}} \left( \frac{p_{\star}}{m_{\star}} \right)\,\sigma,
\label{eq:snk18}
\end{equation}$$ where $\Sigma_{\mathrm{SFR}}$ is the SFR per unit area. Similarly to F21, the kinetic energy dissipated per unit area is defined as $$\begin{equation}
\dot{E}_{\mathrm{kin, K18}} = \frac{3}{2} \frac{\Sigma_{\mathrm{gas}} \sigma^3}{h}. 
\label{eq:kink18}
\end{equation}$$ In K18, Eq. ([\[eq:kink18\]](#eq:kink18)) is also expressed in terms of other model parameters, such as $Q$, $\Omega$ and the fractional contribution of gas to $Q$. A key difference between F21 and K18 is that, in K18, the rate of star formation per unit area is defined by the star formation law:

$$\begin{equation}
\Sigma_{\mathrm{SFR}} = \epsilon_{\mathrm{ff}} \frac{\Sigma_{\mathrm{gas}}}{t_{\mathrm{ff}}},
\label{eq:sfrk18}
\end{equation}$$ where $\epsilon_{\mathrm{ff}}$ is the star formation efficiency and $t_{\mathrm{ff}}$ is the free-fall time and $\Sigma_{\mathrm{gas}}$ is expressed as a function of $\sigma$ and $Q$, Eq. ([\[eq:toomre\]](#eq:toomre)).

In the K18 model, equations for $\epsilon_{\mathrm{ff}}$ and $Q$ are obtained by equating Eq. ([\[eq:snk18\]](#eq:snk18)) and ([\[eq:kink18\]](#eq:kink18)). These two equations are then used to derive the relation between $\sigma$ and $\Sigma_{\mathrm{SFR}}$ and its integral SFR in two scenarios. In the first scenario, the disk is marginally unstable (i.e., value of $Q$ is fixed) and the star-formation efficiency is allowed to vary. By equating equations ([\[eq:snk18\]](#eq:snk18)) and ([\[eq:kink18\]](#eq:kink18)), it is found that $\epsilon_{\mathrm{ff}} \propto \sigma$, which, when substituted into Eq. ([\[eq:sfrk18\]](#eq:sfrk18)), results in $\sigma \propto \Sigma_{\mathrm{SFR}}^{1/2} \propto \mathrm{SFR}^{1/2}$. In the second scenario, the disk is assumed to be Toomre stable, with a fixed $\epsilon_{\mathrm{ff}}$ and variable $Q$. By equating Eqs. ([\[eq:snk18\]](#eq:snk18)) and ([\[eq:kink18\]](#eq:kink18)), it is determined that $\sigma$ can only take one specific value, resulting in no direct relationship between $\sigma$ and $\mathrm{SFR} \propto \Sigma_{\mathrm{SFR}}$.

## Energy vs momentum

In this section, we derive the relation between $\sigma$ and SFR by adopting the approach of F21, but using the momentum injected by supernovae rather than their energy. The energy injection rate is defined as

$$\begin{equation}
\dot{E}_{\mathrm{SN, p}} = \mathrm{SFR} \left( \frac{p_{\star}}{m_{\star}} \right)\,\sigma .
\label{eq:snkf}
\end{equation}$$ By equating this expression with Eq. ([\[eq:ekin\]](#eq:ekin)), we obtain the following relationship: $$\begin{equation}
\sigma^2 =  \mathrm{SFR} \left( \frac{p_{\star}}{m_{\star}} \right) \frac{4\, h}{3\, M_\mathrm{gas}}
\end{equation}$$ The primary difference from the F21 model lies in the slope. Here, $\sigma \propto \mathrm{SFR}^{1/2}$ when assuming a constant value for $\left(\frac{p_{\star}}{m_{\star}}\right)$ as in K18, or $\sigma \propto \mathrm{SFR}$ when assuming $p_{\star} \propto \sigma$. In contrast, F21 finds that $\sigma \propto \mathrm{SFR}^{1/3}$.

For a consistency check, we fit the relation $\log{\sigma} = m \times \log{\mathrm{SFR}} + c$ with $m$ fixed at 0.5 (dark green dashed curve in Fig.[13](#fig:slope)) and 1 (light green dotted curve in Fig.[13](#fig:slope)). For comparison, we also include the fit with $m = 0.33$ (see Sect. [5](#sec:model) and Fig. [5](#fig:sigma_sfr). As discussed in Sect. [5](#sec:model), the relation with a slope of $m = 0.33$ is the only one that accurately reproduces the data.

![](figures/sigma_sfr_rel_fixedslope0.5_hr.png)

# Statistical analysis of the residuals

In Sect. [5](#sec:model), we derived the expected relation between $\sigma$ and SFR (Eq. ([\[eq:slope0.33\]](#eq:slope0.33)) and discuss the potential dependence of $h$ and $M_{\mathrm{{gas}}}$ on $\sigma$ and SFR. As a diagnostic check, in this section we study the correlation between the residuals of the best-fit linear relations Eq. ([\[eq:sigma-sfr\]](#eq:sigma-sfr)) as a function of $\log\sigma$ and $\log\mathrm{SFR}$ (Fig. [14](#fig:residuals)). Any correlations between the residuals and $\log\sigma$ and $\log\mathrm{SFR}$ would suggest that the linear model we are assuming with a slope fixed at 0.33 might not be appropriate. To perform this test, we compute the orthogonal distance between each data point ($\log\sigma_\mathrm{i},\log\mathrm{SFR_i}$) and the best-fit linear relation. To accurately propagate the uncertainties of the data points, we simulate multiple (N = 10000) datasets through bootstrapping. We then compute the distributions of the Pearson rank correlation coefficient $\rho$ (cite: Kendall_1973) between SFR and residuals and between $\sigma$ and the residuals, and their corresponding p-value distributions using a Monte Carlo approach (cite: Curran_2014). This methodology allows for robustly evaluating the correlation between quantities that have associated uncertainties. The resulting distributions for $r_{\mathrm{Pearson}}$ and the p-values are plotted in Fig. [15](#fig:correlation). We find that the correlation coefficients are $r_{\mathrm{Pearson}} = -0.23_{-0.31}^{+0.15}$ for the $\log\mathrm{SFR}$ vs residual and $r_{\mathrm{Pearson}} = 0.13_{-0.03}^{+0.23}$ for the $\log\mathrm{\sigma}$ and residual distributions, respectively. The fractions of the two distributions with p-values $< 0.05$ are 36% and 11%, respectively. In other words, there is only a weak and no statistically significant correlation between residuals and $\log\mathrm{SFR}$, and between residuals and $\log\sigma$, respectively.\
As an additional consistency check, we calculate the partial correlation coefficients (cite: Kendall_1973) between $\log\mathrm{\sigma}$ and $\log\mathrm{SFR}$ while controlling for spurious or extra correlations beyond the linear relation by using the residuals as control variables. This analysis allows us to determine whether the correlation between $\log\mathrm{\sigma}$ and $\log\mathrm{SFR}$ is statistically significant or if it can be attributed to any correlations not accounted for in the adopted model. This is easily measured as a non-null correlation with the residuals, whose scatter and distribution could depend on $h/M_{\mathrm{gas}}$ and, therefore, on $\sigma$ and SFR. In Fig. [16](#fig:partial), we present the distributions of the partial correlation coefficients ($r_{\mathrm{partial}}$) and the corresponding p-values. The analysis yields $r_{\mathrm{partial}} = 0.86_{-0.06}^{+0.04}$. Based on the p-value distribution, where 100% of p-values are less than 0.05, we conclude that the correlation between $\log\mathrm{\sigma}$ and $\log\mathrm{SFR}$ is statistically significant. This finding supports the robustness of the observed relationship, indicating that it persists even when accounting for the potential influence of residuals. Consequently, our results provide strong evidence that the relationship between $\log\mathrm{\sigma}$ and $\log\mathrm{SFR}$ is not merely an artifact of the residual effects of the assumed model.

![](figures/residuals.pdf)

![](figures/correlation.png)

![](figures/partial.png)

[^1]: The information on the ALPAKA sources and the extended sample is available in electronic format at <https://alpaka-survey.github.io>, where later releases and updates will also be placed.

[^2]: [https://www.canfar.net/storage/list/phangs](https://www.canfar.net/storage/list/phangs/RELEASES/PHANGS-ALMA/)

[^3]: [DOI:10.5281/zenodo.10968307](10.5281/zenodo.10968307)

[^4]: The analysis code — `scattr` (cite: DiMascolo2024) — is available at: <https://github.com/lucadimascolo/scattr>.

</paper>

Write the methods card for this paper.