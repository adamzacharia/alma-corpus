# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...686A.298G\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...686A.298G",
 "title": "Into the thick of it: ALMA 0.45 mm observations of HL Tau at a resolution of 2 au",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Guerra-Alvarado, Osmar M.",
 "n_authors": 10,
 "arxiv_id": "2404.04164",
 "doi": "10.1051/0004-6361/202349046",
 "alma_projects_linked_by_archive": [
  "2011.0.00005.E",
  "2017.1.01178.S"
 ]
}
```

Paper text:
<paper>
# Into the thick of it:\
ALMA 0.45 mm observations of HL Tau at 2 au resolution

To comprehend the efficiency of dust evolution within protoplanetary disks, it is crucial to conduct studies of these disks using high-resolution observations at multiple wavelengths with the Atacama Large Millimeter/submillimeter Array (ALMA).

In this work, we present high-frequency ALMA observations of the HL Tau disk using its Band 9 centered at a wavelength of 0.45 mm. These observations achieve the highest angular resolution in a protoplanetary disk to date, 12 milliarcseconds (mas), allowing the study of the dust emission at scales of 2 au. We use these data to extend the previously published multi-wavelength analysis of the HL Tau disk, constraining the dust temperature, dust surface density, and maximum grain size throughout the disk. We perform this modeling for compact solid dust particles, as well as for porous particles. Our new 0.45 mm data traces mainly optically thick emission, providing a tight constraint to the dust temperature profile. We derive maximum particle sizes of $\sim1$ cm from the inner disk to $\sim60$ au. Beyond this radius, we find particles between 300 $\mu$m and 1 mm. The total dust mass of the disk is 2.1 M$_{J}$ with compact grains, and it increases to 6.3 M$_{J}$ assuming porous particles. Moreover, an intriguing asymmetry is observed at 32 au in the northeast inner part of the HL Tau disk at 0.45 mm. We propose that this asymmetry is the outcome of a combination of factors including the optically thick nature of the emission, the orientation of the disk, and a relatively large dust scale height of the grains preferentially traced at 0.45 mm. To validate this, we conducted a series of radiative transfer models using the RADMC-3D software. Our models, incorporating varying dust masses and scale heights, successfully replicate the observed asymmetry in the HL Tau disk. If this scenario is correct, our measured dust mass within 32 au would suggest a dust scale height H/R$>0.08$ for the inner disk. Finally, the unprecedented resolution allowed us to probe for the first time the dust emission down to a few au scales. We observed an increase in brightness temperature inside the estimated water snowline and speculate whether it could indicate the presence of a traffic jam effect in the inner disk. Our results showcase how 0.45 mm observations of protoplanetary disks can be used to robustly constrain their dust temperature radial profile. Additionally, the higher optical depths at this wavelength can be used to constrain the dust vertical scale height. Finally, these higher frequencies allow us to reach higher spatial resolutions that have the potential to resolve the region within the water snowline in disks.

# Introduction

Over the past ten years, the Atacama Large Millimeter/submillimeter Array (ALMA) has made significant contributions to our understanding of protoplanetary disks by revealing substructures within them. These studies (e.g. (cite: 2015ApJ...808L...3A), (cite: 2016PhRvL.117y1101I), and (cite: 2018ApJ...869...17L)) have shown the frequent appearance of substructures in protoplanetary disks having different morphologies ((cite: 2013Sci...340.1199V), (cite: 2016Sci...353.1519P), and (cite: 2018ApJ...869L..43H)). These substructures play a significant role in protoplanetary disks allowing dust grains to accumulate and grow, facilitating the formation of planets by providing regions of higher dust density and trapping, and slowing down the radial drift of dust grains, which would otherwise hinder the planet formation process ((cite: 2012A&A...545A..81P)).

Most ALMA studies on protoplanetary disks are performed at wavelengths around 1 mm, where dust emission is relatively bright and high angular resolutions around 30 mas can be achieved. In some disks, similar studies have also been performed at longer wavelengths where the emission is known to be optically thinner, up to 3 mm with ALMA (e.g., (cite: 2021MNRAS.506.5117T), (cite: 2018A&A...619A.161C),(cite: 2020ApJ...898...36L)) but also up to 1 cm with the Very Large Array (VLA) (e.g., (cite: 2016ApJ...821L..16C), (cite: 2023AJ....166..186H)). These observations at long wavelengths allow us to study the properties of the dust grains albeit at the expense of angular resolution. Observations of protoplanetary disks with ALMA at shorter wavelengths, although providing the highest angular resolutions possible with ALMA ($\sim$10 mas), are usually avoided because of the higher atmospheric opacity and turbulence, leading to necessarily longer integration and calibration times, and the fact that dust emission is expected to be optically thick. However, there is also complementary information that can be extracted from studies at such wavelengths. For instance, optically thick emission impose better constraints on the temperature and the albedo of the dust particles, improving the results from multi-wavelength modeling of disks. Moreover, observations at short wavelengths are the only way to explore the dust content in the gaps whose emission is usually very optically thin to be detected at long wavelengths.

Recent multi-wavelength analyses of Class II protoplanetary disks ((cite: 2019ApJ...883...71C), (cite: 2021A&A...648A..33M), (cite: 2021ApJS..257...14S), and (cite: 2022A&A...664A.137G)) have measured dust properties within these substructures. The dust sizes determined from these observations are around 1 mm. However, there is a discrepancy with measurements obtained from polarization observations ((cite: 2017ApJ...844L...5K)) which suggest dust sizes on the order of a few hundred micrometers. To reconcile these conflicting results, some studies by (cite: 2017ApJ...844L...5K) and (cite: 2020ApJ...900...81O) have proposed the existence of two dust populations. The larger particles (mm-sized) would experience more efficient vertical settling, becoming decoupled from the gas and gathering towards the midplane of the disk. On the other hand, smaller particles would remain mixed with the gas in higher layers of the disk ((cite: 2005A&A...443..185B)). More recently, (cite: 2023ApJ...953...96Z) proposed that large (sizes larger than 1 mm) and porous (porosities higher than 70$\%$) particles could reproduce both, multi-wavelength and polarization results. A very recent polarization multiwavelength study strongly supported the presence of porous particles in HL Tau (cite: 2023arXiv230910055L)

Studies by (cite: 2016ApJ...816...25P), (cite: 2020A&A...642A.164V), (cite: 2021ApJ...912..164D), (cite: 2022ApJ...930...11V) and (cite: 2023MNRAS.524.3184P) have focused on understanding the vertical structure of protoplanetary disks. Although limited in number, these studies suggest that Class II disks exhibit significantly low dust scale heights, particularly at longer wavelengths observed with ALMA. This is a consequence of the distribution of dust grains changing along the vertical direction due to settling ((cite: 2004A&A...421.1075D),(cite: 2021A&A...645A..70P)). Most constraints presented in these papers remain as upper limits (except in HD163296), with suggestions such as H(100au) \< 1 au. Additionally, (cite: 2023MNRAS.524.3184P) discovered values \< 4 au for certain DSHARP disks, particularly those with less favorable orientations. These findings were predominantly derived from the presence/depth of gaps and rings in the outer regions of the disks (outer 100 au) where the scale height in the inner regions remains mostly unknown.

In this work, we present high-resolution Band 9 observations of HL Tau, a young stellar object in the Taurus-Auriga molecular cloud ($\sim 147$pc, (cite: 2018ApJ...859...33G)) with an estimated age of less than 1 million years ((cite: 2017A&A...607A..74L)). HL Tau is considered a Class I-II disk ((cite: 2008ApJS..176..184F)) and it was the first protoplanetary disk in which the presence of dark and bright rings was discovered ((cite: 2015ApJ...808L...3A)). Since it has been intensively observed in the last years with ALMA and VLA, high-quality data covering a wide range of wavelengths, between 0.9 mm and 1 cm, are currently available ((cite: 2016ApJ...821L..16C), (cite: 2019ApJ...883...71C)). There have been also several previous studies modeling its continuum emission to infer the dust properties (e.g., (cite: 2016ApJ...818...76J), (cite: 2016ApJ...816...25P), (cite: 2017A&A...607A..74L)). From these, it has been well established that the dark rings are actually gaps in the dust distribution, i.e. regions of lower density than the adjacent bright rings. The origin of the substructures is still debated, but the most promising are planet-disk interactions (e.g., (cite: 2016ApJ...818...76J), (cite: 2016MNRAS.459L...1D)). Our new sensitive and high-resolution observations at 0.45 mm data are combined with the previous multi-wavelength observations to analyze the dust properties in the disk. The addition of shorter wavelength observations allowed us to improve previous modeling of the dust properties in the disk, as well as obtain new insights about the dust temperature very close to the protostar and the vertical structure of the disk.

![](HLTAUB9ZOOMFBIEN.pdf)

![](RADPROFTBB9FINAL2.pdf)

# Observations

We analyze archival observations obtained with the Atacama Large Millimeter/submillimeter Array (ALMA) at a wavelength of 0.45 mm. One of the archival datasets that we used was part of the test observations for the band-to-band calibration during the High-Frequency Long Baseline Campaign (cite: 2020ApJS..247...23A), project code: 2011.0.00005.E). The observations were taken during two execution blocks on November 3, 2017. The total observing time was 65 and 100 minutes for the first and second execution, respectively, which combined gives a 45-minute on-source time for HL Tau. The final data has 8 spectral windows, each of them covering a bandwidth of 2 GHz. We also used additional data at a lower resolution (project code: 2017.1.01178.S, PI: E. Humphreys) to complete the uv coverage at shorter baselines. These data have 8 spectral windows covering frequencies from 646-662 GHz with a bandwidth of 1.875 GHz each. The observations were taken from October 2, 2018 to October 18, 2018 with a total observing time on-source of 95 minutes.

We calibrated the data by using the calibration pipeline and scripts provided by the ALMA staff. We used version 5.6.1 of CASA (Common Astronomy Software Applications; (cite: 2007ASPC..376..127M) for self-calibration and cleaning in both data sets. We identified and flagged the spectral lines that were found in both data sets. We also averaged channels for the low and high-resolution data; the final self-calibrated datasets contain spectral windows of 8 channels of 200 MHz each.

We performed phase-only and amplitude self-calibration in both data sets. First, self-calibration was performed on the short baseline data. During the self-calibration process, we created the images using the task CLEAN in CASA. The MTMFS deconvolver (cite: 2011A&A...532A..71R) was used with scales of 0, 1, 3, and 5 times the beam size. We also used a Briggs weighting with a robust parameter of 0.5. For the low-resolution data set the self-calibration process resulted in a big improvement in the image quality. We applied 6 iterations of phase-only self-calibration decreasing the time solution interval down to 18s. Furthermore, we were also able to apply two rounds of amplitude and phase self-calibration (`calmode=ap`) until no improvement in the signal-to-noise ratio was found. By the end of the whole self-calibration process, we achieved an increase in the S/N by a factor of $\sim$17.4. We combined our short baseline data together with the long baseline data after aligning and correcting for proper motions and astrometric errors between our data sets. This was done by applying a Gaussian fit using CASA in the high-resolution image and using the tasks FIXVIS and FIXPLANETS to apply shifts to the low-resolution data. After this, self-calibration was attempted on the combined dataset. We started with phase-only self-calibration, however, due to the low S/N at the long baselines, no improvement was found.

Lastly, self-calibration separately on the long-baseline data was also attempted by using the model obtained from the self-calibrated low-resolution data, but no improvement was found either. Since not enough solutions were found with any method to improve the quality of the combined data set, the self-calibration process was stopped.

With our final data set at hand, we recalculated the weights using the task STATWT in CASA. For the final images, we used the TCLEAN task in CASA with the MTMFS deconvolver (cite: 2011A&A...532A..71R) using nterms=1 and scales at 0, 1, 3, and 5 times the beam size. We used a pixel size 10 times smaller than the beam size for all of the images. We explored different weightings: natural, uniform, and Briggs with different robust values. Finally, two images are used for this study. The first one, made by setting the parameter robust to 0 and using baselines shorter than 12 $k\lambda$ in length, gives us a good compromise between resolution and sensitivity and was used for the study of the large scale emission of the disk. This image has an rms noise of 270 $\mu$Jy beam$^{-1}$ and a beam size of $\sim$23 mas. A second image was done by setting the parameter robust to -0.5, which results in a beam size of $\sim$12 mas and an rms noise of 380 $\mu$Jy beam$^{-1}$. This higher angular resolution image allowed us a detailed study of the innermost part of the disk ($\lesssim$20 au). Both images are shown in Figure [1](#Fig1).

In order to study the radial properties of the disk, we also obtained radial profiles of the emission and convolved the images to a round beam (robust 0, 24 mas and robust -0.5, 13 mas). For this, we used the known inclination and position angles of the disk, 46.72$^{\circ}$ and 138.02$^{\circ}$, respectively (cite: 2015ApJ...808L...3A). However, due to the inclination of the disk, there is a loss in angular resolution in the NE-SW direction. Since the S/N of the image is very high, we could avoid this loss in resolution by simply averaging emission azimuthally within $\pm$0.2  rad of the major axis of the disk. Radial profiles of the brightness temperature obtained from the intensity profiles of both images are shown in Figure [2](#Fig2).

# Results

In Figures [1](#Fig1) and [2](#Fig2), it can be seen that our images at 0.45 mm recover emission from the whole disk with a radius of $\sim$1$\ensuremath{''}$ or $\sim$140 au, similar to previous ALMA images at longer wavelengths (see e.g., (cite: 2019ApJ...883...71C), (cite: 2015ApJ...808L...3A)). Our 0.45 mm image also shows some substructures but, as expected, due to the higher optical depth at this wavelength, substructures are detected with a lower contrast between dark and bright rings. This suggests that the gaps contain small particles traced by the 0.45 mm image, these particles are more coupled with the gas and might fill the gaps more than bigger particles observed at longer wavelengths ((cite: 2012A&A...538A.114P),(cite: 2013A&A...560A.111D)). Furthermore, we observed a slight deviation in the positions of the gaps and rings at 0.45 mm when compared to the radial profiles at other wavelengths (see Figure [2](#Fig2)), which suggests that there might be slight variations in the depth and width of the disk substructures at different wavelengths.

In the right-top of Figure [1](#Fig1), we show a zoomed-in view of the inner 50 au. An asymmetry can be seen in the 0.45 mm data that is not seen at longer wavelengths: the NE part of the first ring is more intense than the SW part of the ring.

In the right-bottom panel of Figure [1](#Fig1), we show our highest angular resolution image which allowed us to resolve, for the first time, the most internal part of the disk ($\lesssim 20$ au). In this image, we can observe the first ring and a very deep gap.

This first gap, centered at 13 au, while it shows some emission in the low resolution 0.45 mm, it appears very dark in our highest angular resolution image (see Figures [1](#Fig1) and [2](#Fig2)).

These observations provide a clearer view of the gap’s structure, revealing that it is likely deeper and more depleted of dust particles than what was initially observed with lower resolution at 0.87 mm and 1.3 mm. Moreover, the fact that we also detect a very deep gap in the 0.45 mm image strongly suggests that this gap is actually devoid of small dust particles as well.

In the inner panel of Figure [2](#Fig2), it can be seen that the brightness temperature increases within 2.5 au when observed at the highest angular resolution. This could potentially be attributed to substructures within the inner disk that are becoming resolved for the first time thanks to the higher angular resolution of our 0.45 mm data.

In the following section, we first discuss the updated modeling of the radial dust properties using all the currently available data of HL Tau, then the origin of the new features found in the 0.45 mm images, the asymmetry, and the substructure within the inner disk.

# Discussion

## Modeling of the dust properties

![](ResultsSNNNoPoroso.pdf)

![](ResultsSNPoroso.pdf)

Previous to this work, there have been several studies modeling the dust properties in the HL Tau using the available data at that moment (e.g., (cite: 2016ApJ...816...25P), (cite: 2017A&A...607A..74L), (cite: 2019ApJ...883...71C)). We perform a new modeling procedure by including the new 0.45 mm image reported here which will provide valuable constraints on the dust temperature and will enhance the comprehensiveness of our multi-wavelength analysis. Thus, this new analysis includes images at 0.45, 0.87, 1.3, 2.1 and 7.0 mm. We created a new 0.45 mm image with a robust parameter of 1.0, using baselines \< 12 $k\lambda$ in length as previously described for the robust 0.0 image. Then, we convolved it with a 50 mas Gaussian beam and extracted radial profiles in wedges along the major axis within radial beams of approximately 0.01 arcseconds. We also extracted radial profiles at the other wavelengths applying the same procedure to the images presented in (cite: 2019ApJ...883...71C). Subsequently, each point in the radial profiles was modeled independently. We note that each point in the model is not independent from its neighboring points due to the effects of the beam. Consequently, the contrast of the model parameters between rings and gaps will be slightly smoothed in our results. We follow a similar approach to (cite: 2019ApJ...883...71C), i.e., at each radius, we fit the spectral energy distribution (SED) in the millimeter wavelength range using a 1D slab model given by: $$\begin{eqnarray}
I_{\nu}=B_{\nu}(T)[(1-\exp( \tau_{\nu}/\mu))+\omega_{\nu}F(\tau_{\nu},\omega_{\nu})],
  \label{eq:emergent intensity (Sierra et al. 2019)}
 
\end{eqnarray}$$ where, $$\begin{eqnarray}
F(\tau_{\nu},\omega_{\nu})=\frac{1}{\exp(-\sqrt3\epsilon_{\nu}\tau_{\nu})(\epsilon_{\nu}-1)-(\epsilon_{\nu}+1)}\textsc{x}\nonumber\\ \left [  \frac{1-\exp(-(\sqrt{3}\epsilon_{\nu}+1/\mu)\tau_{\nu})}{\sqrt{3}\epsilon_{\nu}\mu+1}+\frac{\exp(-\tau_{\nu}/\mu)-\exp(-\sqrt{3}\epsilon_{\nu}\tau_{\nu})}{\sqrt{3}\epsilon_{\nu}\mu-1}  \right ],
  \label{eq:F(tau,omega) (Sierra et al. 2019)}
 
\end{eqnarray}$$

where $\omega_{\nu}=\frac{\sigma_{\nu}}{\kappa_{\nu}+\sigma_{\nu}}$ is the albedo, which is defined by the scattering coefficient ($\sigma_{\nu}$) and the absorption coefficient ($\kappa_{\nu}$), $\tau_{\nu}$ = $\Sigma_{dust}\chi_{\nu}$, where $\chi_{\nu}= {\kappa_{\nu}+\sigma_{\nu}}$, $\mu=cos(i)$ considers the inclination effects by correcting the optical depth by this inclination ($i$), and $\epsilon_{\nu}=\sqrt{1-\omega_{\nu}}$. This model assumes that most of the dust content is settled in the mid-plane (see (cite: 2019ApJ...876....7S) and (cite: 2019ApJ...883...71C) for details). While this assumption holds well for the outer HL Tau disk, it is not met within the initial $\sim$ 32 au. A particle size distribution that follows a power-law distribution was also assumed, specifically, $n(a) \propto a^{-p}$. We set the value of the exponent $p$ to 3.5, which is a common value used in the Interstellar Medium (ISM) (cite: 1977ApJ...217..425M).

The dust opacity values were obtained assuming the DSHARP dust composition and following the effective medium approximation (cite: 2018ApJ...869L..45B). As usual in the study of protoplanetary disks, we first consider compact solid spherical particles. However, we also perform an analysis by considering spherical porous dust particles with a porosity of 90%. This is motivated by very recent results which strongly suggest that the HL Tau disk contains porous dust particles ((cite: 2023ApJ...953...96Z) and (cite: 2023arXiv230910055L)).

The opacity tables for the porous particles were obtained using the same procedure as (cite: 2018ApJ...869L..45B): the grain is assumed to be composed of small monomers within a void matrix. The optical properties of the monomers are computed first using the Bruggeman rule. This same rule is also used for the compact grains. The monomers are then mixed with a void matrix using the Maxwell-Garnett rule. It is well-established that the fluxes and, consequently, dust masses exhibit significant dependence on the assumed dust composition, particularly the quantity of carbon. For instance, when using the opacities presented by (cite: 2010A&A...512A..15R) and (cite: 2022A&A...668A.104S) the fluxes they inferred were higher which made the spectral indices of typical disks more easily explained. Therefore, the composition of the grains plays a crucial role, and the total dust mass derived in the subsequent section should be approached with caution.

We model the SED of the disk at each radius independently and we fitted the dust parameters (T$_{dust}$, a$_{max}$ and $\Sigma_{dust}$). We assume a flux calibration uncertainty of 10% at 0.45 mm, 0.9 mm, 1.3 mm and 7 mm, and 5% at 2.1 mm. We compute the posterior probability distribution of our model at each radius using the Markov Chain Monte Carlo (MCMC) implementation within `emcee` (cite: 2013PASP..125..306F). We assume uniform priors in dust surface density and maximum grain size. Following (cite: 2021A&A...648A..33M), we use a conservative (i.e., wide) prior for the dust temperature based on the expected radial temperature profile for a passively irradiated disk, $T_d = (\phi {L}_{\star}/8 \pi r^2 \sigma_{\rm SB})^{0.25}$, assuming ${L}_{star} = 6 \pm 5~{L}_{\odot}$ (i.e., a very conservative uncertainty on the stellar luminosity) and a range in $\phi$ (i.e., flaring angle) between 0.005 and 0.3. This prior is wide enough to have no effect on the posterior of the temperature at most radii, only helping avoid reaching unphysically high dust temperatures at a few radii within the wide gap between 60 and 90 au, where the emission is optically thin and, therefore, the dust temperature and dust surface density are highly degenerated.

In Figures [3](#Fig3) and [4](#Fig4), we show the dust parameters for the HL Tau disk obtained from the fitting with the two different particles, solid and porous, respectively. In Appendix A, we show the model radial intensity profiles at each wavelength and their uncertainties, obtained from the median, 16th, and 86th percentiles of 500 random SEDs computed from the MCMC chains. As anticipated, the dust temperature is very well constrained for both cases, compact and porous particles. We also note that the surface density is well-constrained in both cases. Moreover, our findings reveal that dust particles in the HL Tau disk are relatively large, ranging from millimeters to centimeters in size, these resemble well with models of dust evolution with traps located at different distances (cite: 2015A&A...573A...9P).

Our models find a sudden, and likely unphysical, increase in particle size at the 13 au gap. However, figures [7](#Fig:A1) and [8](#Fig:A2) show that our models are in fact incapable of reproducing the observed emission at these radii. We believe the reason for this is our limited angular resolution, paired with the fact that the 13 au gap is highly depleted of large dust particles. As such, the SED at high frequencies is dominated by the small grains present in the gap, while at longer wavelengths the emission comes mostly from the beam smearing of the emission at the 20 au ring. Higher angular resolution observations at long wavelengths, only feasible with the upcoming ngVLA, are therefore necessary to accurately constrain the dust properties at these radii.

A distinct gap at 70 au, wide and with almost no large particles, is evident in [3](#Fig3) and [4](#Fig4), consistent with prior observations by (cite: 2019ApJ...883...71C). Interestingly, an increase in dust surface density is then present at the 84 au and 96 au rings, with grain sizes still remaining at a few hundreds of microns. We note that an infalling streamer has been found to be interacting with the HL Tau disk at these radii (cite: 2022A&A...658A.104G). We speculate that the small dust particles of this late infalling material might be responsible for the creation of this dust ring, which would explain why the particles at these radii have not yet grown up to mm/cm sizes. More detailed modeling of the interaction between the disk and infalling streamers would be needed to confirm this scenario.

Furthermore, clear distinctions emerge between the compact and porous particle solutions. In general, the model using compact particles exhibits lower temperatures and dust surface densities across the entire range of radii. The particle sizes predicted by the porous dust composition appear to be slightly smaller, although we note that they have a significantly wide uncertainty range.

Given that our new 0.45 mm data have allowed us to better constrain the radial dust temperature profile, we can more robustly compare the position of the rings and gaps in HL Tau with the expected positions of the snowlines of some of the most relevant volatiles in protoplanetary disks. We plot in Figures [3](#Fig3) and [4](#Fig4) the expected radii of the snowlines of H$_2$O, NH$_3$, CO$_2$, H$_2$S, and CO. Except for the H$_2$O snowline, the uncertainties in the sublimation temperatures of these volatiles now dominate the uncertainty in their positions. These large uncertainties still make it hard to extract any robust conclusion, despite our improved temperature profile. Given the abundance of substructures in HL Tau, these snowlines will always fall close to a ring or gap. This makes it hard to confidently reject that snowlines are at the origin of at least a few of the ring substructures in HL Tau, as previously proposed ((cite: 2015ApJ...806L...7Z); (cite: 2019ApJ...883...71C)). However, many other substructures appear to be far from the expected snowlines as in other protoplanetary disks (cite: 2023ASPC..534..423B). This applies mostly to the outer substructures, between 65 and 98 au, but also some between 36 to 45 au. We therefore conclude that mechanisms other than snowlines (e.g., MHD effects or planet-disk interactions) must be responsible for most, if not all, the ring substructures in HL Tau.

We infer a total dust masses of 2.1$^{+1.88}_{-0.84}$ and 6.3$^{+1.57}_{-1.04}$ M$_{J}$ from the compact and porous particles, respectively. The dust masses assuming porous particles are thus larger by a factor of $\sim3$, as previously reported by (cite: 2023ApJ...953...96Z). Our measurement of the dust mass with compact grains is two times higher than the mass obtained in (cite: 2019ApJ...883...71C) assuming compact particles with the same composition as ours (1.04 M$_{J}$). The primary difference between their analysis and ours is the inclusion of Band 9 in our sample. These additional data have allowed us to more robustly constrain the dust temperature, which in turn affects the rest of the modeling. We obtained lower dust temperatures across all radii. The surface density is comparable at the inner radius but it has a more rapid decline compared to their study. Additionally, our analysis reveals more pronounced substructures in the surface density. Notably, we observe larger dust particle sizes by approximately one order of magnitude within 60 AU, but beyond this point, the particle sizes decrease more significantly compared to the findings in (cite: 2019ApJ...883...71C). These larger particles inside 60 au have lower absorption opacities, which explains why we obtain a higher dust mass than (cite: 2019ApJ...883...71C). Additionally, (cite: 2020MNRAS.493L.108B) estimated a lower limit for the total gas mass of the disk to be 209.5 M$_{J}$. This reconciles well with our results of the compact dust particles if we consider a gas-to-dust ratio of a 100. However, the elevated mass associated with porous dust particles from our analysis might imply a reduced gas-to-dust ratio $\sim$ 33 when compared to the total disk mass of 209.5 M$_{J}$. This suggests that the total gas mass of the disk might indeed still be larger than 209.5 M$_{J}$.

We note that our assumption of a 1-D slab model might not be accurate in the inner radius \< 32 AU, where the emission at 0.45 mm is so optically thick that it could be tracing layers of the disk above the midplane (see section [4.2](#sec4.2)). If all wavelengths are effectively probing adjacent and close layers in the disk, indicating minimal variations in temperature and dust size distribution between them, then the assumption could still be valid. The midplane of protoplanetary disks is generally vertically isothermal, so it is most likely that, if our observations are tracing significantly different layers of the disk, this has only an effect on the maximum grain sizes traced at each wavelength. (cite: 2020ApJ...892..136S) explored these effects in more detail and found that the high optical depths in the innermost regions of disks could result in incorrectly measuring the maximum grain size to be of a few hundreds of microns. While we cannot discard that our modeling is affected by these effects, the fact that we find maximum grain sizes of $\sim5$ mm in the inner region, instead of the 200-300 microns found by (cite: 2020ApJ...892..136S) suggests that our modeling is not severely affected by the high optical depths.

## Azimuthally asymmetric emission in the inner disk

As mentioned in Section 3, the first ring, centered at 21 au, shows an azimuthal asymmetry at 0.45 mm that becomes fainter at longer wavelengths and we believe this is contingent upon the resolution and sensitivity of the observations. This asymmetry appears as an increase in brightness at the northeastern side of the ring, covering almost 180 degrees and centered on the minor axis of the disk (see Fig. [1](#Fig1)). The position of this asymmetry strongly suggests that it is caused by the combination of the disk’s inclination and its high optical depth at the observed wavelength (see Fig. [5](#Fig5)). Specifically, in the northeastern (NE) part of the disk, we are directly observing the emission from the internal wall of the first ring, which is directly irradiated by the central star, increasing its temperature. On the other hand, in the southwestern (SW) part of the disk there is no direct line of sight toward the wall, so the wall emission is blocked by the optically thick material in the line of sight (see Figure [5](#Fig5)).

Given that the HL Tau outflow is blue-shifted in the NE and red-shifted in the SW (cite: 2014AJ....147...72L), we can infer that the NE corresponds to the far side of the disk, while the SW corresponds to the close side of the disk to the observed, this explains the position of the asymmetry in that side of the minor axis of the disk.

The asymmetry, in this case, is fundamentally similar to those found in Class 0/I objects (e.g (cite: 2024A&A...681A..82G),(cite: 2023ApJ...951....9L),(cite: 2023ApJ...951....8O)) where the dust particles did not have time to settle or are affected by significant turbulence preventing the grains to fall into the midplane (larger dust scale height), remaining optically thick even at longer wavelengths with ALMA. On the other hand, this asymmetry is fundamentally different from the large-scale asymmetries observed in other disks, where the effects become more pronounced at longer wavelengths (e.g., IRS48 (cite: 2015ApJ...810L...7V) and HD142527 (cite: 2015ApJ...812..126C) which is contrary to the observed behavior in HL Tau. These asymmetries are commonly associated with dust traps where dust can grow up to cm sizes.

![image](ESQUEMATICRADMC.pdf)

In order to confirm that the asymmetry is caused by a geometric effect, we use a toy model to reproduce the observed asymmetry. We use RADMC-3D (cite: 2012ascl.soft02015D) to perform radiative transfer models at 0.45 mm while varying parameters such as the disk dust mass and scale height. We then compare the model emission with the observed data to gain insights into the disk’s physical properties and vertical structure. In this specific radiative modeling, a generic protoplanetary disk model was utilized within RADMC-3D. The disk dust masses and scale height were adjusted to explore different scenarios and to reproduce the observed asymmetry. The `optool` package (cite: 2021ascl.soft04010D) was employed to compute the DSHARP dust particle opacities using a$_{min}$ as 0.050 $\mu$m and a$_{max}$ as 3mm. For this toy model, we are only interested in the inner regions of the disk, so we consider only emission up to a radius of 32 au (the location of the second gap). We assumed that all the grains are at the same height and we set a small inner radius $R_{in}$=1 au. A gap between 8 au and 17 au was included in the model to capture the effects of the asymmetry at the outer edge of the gap.

The generic protoplanetary disk model uses a density distribution that goes as:

$$\begin{eqnarray}
 \rho(r,z) =\frac{\Sigma(r)}{H_{p}\sqrt{2\pi}}\exp(-\frac{z^{2}}{2H^{2}_{p}}),
 \label{eq: Density distribution}
 
\end{eqnarray}$$

where $r$ is the distance to the star from the disk, $H_{p}$(r) is the dust scale height of the disk and $\Sigma(r)$, is the dust surface density defined as:

$$\begin{eqnarray}
\Sigma(r)= \Sigma_{0}(\frac{r}{r_{out}})^{-1},
 \label{eq: Surface Density distribution}
 
\end{eqnarray}$$

The dust scale height in the radiative modeling is defined as a power-law-like dependence given by:

$$\begin{eqnarray}
H_{p}(r)=H_{100}(\frac{r}{100 AU})^{1+\Psi},
 \label{eq: Scale Height}
 
\end{eqnarray}$$

where $\Psi$ is the value of the flaring index set by default to 0.14 and $H_{100}$, is the value of the scale height at a distance of 100 AU from the central star.

Finally, a total stellar mass of 1.7 M${\odot}$ (cite: 2016ApJ...816...25P), a stellar luminosity of 6 $L_{\odot}$ and an effective temperature of 4395 $K$ (cite: 2004ApJ...616..998W) were assumed. In addition, the inclination angle for HL Tau was set to 46.72$^{\circ}$ and the distance to 147 pc.\
Several models were run by varying the dust scale height and the dust disk mass within 32 au (M$_{Disk}^{< 32 au}$) based on previous studies ((cite: 2016ApJ...816...25P); (cite: 2017A&A...607A..74L)). We showed this parameters and their combination in Table [1](#table:RADMC-3D parameters).

| M$_{Disk}^{< 32 au}$ | 1 M$_{J}$ | 3 M$_{J}$ | 5 M$_{J}$ |     |
|:--------------------:|:---------:|:---------:|:---------:|:---:|
|         H/R          |   0.01    |   0.01    |   0.01    |     |
|                      |   0.03    |   0.03    |   0.03    |     |
|                      |   0.05    |   0.05    |   0.05    |     |
|                      |   0.08    |   0.08    |   0.08    |     |
|                      |    0.1    |    0.1    |    0.1    |     |
|                      |           |           |           |     |

: Model parameters explored

The model images were then convolved using a Gaussian beam with the same beam as the 0.45 mm image. The final convolved model images that seem to better reproduce the emission of the observation are shown in Figure [6](#Fig6). We also extracted the deprojected emission from each pixel in a ring ranging from 0.12$\ensuremath{''}$ to 0.15$\ensuremath{''}$ and around 360$^{\circ}$ to capture the increased emission in the asymmetry. We show the normalized azimuthal profiles from the observation and all models in Figure [6](#Fig6). We note that our goal with this toy models is to show that this type of asymmetries can be obtained at 0.45 mm and that one could constrain the dust mass and scale height from these images. As such, we do not try to reproduce the exact flux of our observations, since that would require a much more detailed modeling varying more disk parameters. The azimuthal profiles for 1, 3, and 5 Jupiter masses (Inner disk mass + ring mass) are also shown in Figure 6.

![](AzimutalprofilesalltogetherMODELS2.pdf)

Our modeling shows that an asymmetry like the observed one in HL Tau can be produced by the combined effects of disk orientation, high optical depth, and larger scale heights at 0.45 mm. From Figure [6](#Fig6), it is evident that the dust mass plays a significant role in reproducing the observed asymmetry at 0.45 mm and in models with not a large enough scale height, the emission doesn’t produce an asymmetry.

If the asymmetry arises from the scenario we outlined before, we find that a disk dust mass (within 32 au) of approximately 1 $M_J$, combined with a scale height H/R of 0.08, a disk dust mass of 3 $M_J$ with a scale height H/R of 0.05, or a disk dust mass of 5 $M_J$ with a scale height H/R slightly smaller than 0.05 best reproduces the observed asymmetry in the observations. In other words, the higher the dust mass, the less dust scale height one needs to reproduce an asymmetry. Because of this, obtaining an independent estimation of the dust mass within 32 au would allow for a better constraint on the scale height of the disk. We employ the mass obtained from our multi-wavelength analysis in section [4.1](#sec4.1), acknowledging its known limitations, to give an initial approximation for the scale height in this specific region of the disk. From this analysis, we obtained a disk dust mass inside the first 32 au of 0.86$^{+1}_{-0.368}$ M$_J$. Therefore, if our proposed scenario is the reason of the asymmetry, our derived mass would imply a scale height $\sim$\>= 0.08 H/R in that specific region of the disk. As seen in Figure 6, to more effectively determine the scale height in subsequent studies we need a more restrictive constraint on the disk dust mass together with a model that reproduces the flux and the actual structure of the HL Tau disk.

We note that the scale height necessary to reproduce the observed asymmetry is significantly larger than the estimates from radiative transfer modeling of the 0.9-3 mm emission, H/R \< 0.01 (cite: 2016ApJ...816...25P). One possible explanation for this inconsistency is that, in (cite: 2016ApJ...816...25P), the focus was primarily on gaps and rings in the outer disk, rather than those within 30 au as constrained in this paper. This result then suggests that the HL Tau disk may exhibit greater vertical extent (thickness) in the inner regions while maintaining a flatter profile in the outer regions. Indeed, radial variations in scale height have been identified for the two rings of HD163296, with the 67au ring being very thick (\>4au) and the 100au ring being very flat (\<1au) ((cite: 2021ApJ...912..164D), (cite: 2022SCPMA..6529511L)).

While there are limited constraints on the radial variation of scale height, this outcome implies that turbulence in disks might be higher in the inner regions compared to the outer regions. This aligns well with the high accretion rates on some disks that cannot be explained by their current low turbulence values. In this context, the magnetically driven accretion disk models suggested by (cite: 2022A&A...658A..97D) could explain the heightened turbulence parameter and increased scale height, leading to the observed asymmetry beyond the dead zone (at 23 AU) and within the MRI-active layer in the HL Tau disk. Additionally, this is consistent with what is expected in the case of vertical shear instability with dust coagulation, where the transition between thick and thin occurs at around 100 au ((cite: 2023arXiv231007332P)). Finally, it also remains inconclusive whether the streamer observed by (cite: 2022A&A...658A.104G) in HL Tau could have an effect at smaller radii through the flow of material into the inner disk. The findings in (cite: 2024A&A...682A..32J) suggest a potential influence of this streamer on the turbulence at the outer radius (70 au), raising questions about a possible impact on smaller scales. Further analysis is essential to discern the factors contributing to the increased turbulence, if any, in the HL Tau inner disk and unravel the specifics of this phenomenon.

## Substructure in the inner disk: a sign of the traffic-jam effect?

As mentioned, our highest angular resolution image at 0.45 mm revealed an increase in the brightness temperature within $\sim$2.5 au (see the inset in Figure [2](#Fig2)). There are several possible explanations for this.

First, we discard that this increase is due to free-free contamination. It is well known that HL Tau drives a powerful jet whose emission has been previously modeled using high angular resolution VLA data at long wavelengths (cite: 2019ApJ...883...71C). Thus, we know that in the 23-43 GHz frequency range, the expected free-free emission from the radio jet is given by

$$\begin{eqnarray}
\left[\frac{F_{\nu}}{\mu Jy\ {beam}^{-1 }}\right ]=175\times\left [  \frac{\nu}{32.5\ GHz}\right ]^{0.7}
 \label{Eq1}
\end{eqnarray}$$

where $\nu$ is the frequency of the image at which we want to calculate the free-free emission. Note that in this frequency range, the free-free emission was found to be partially optically thin, which is reflected in the 0.7 spectral index. Now, since the optical depth of the free-free emission is proportional to $\nu^{-2.1}$ (e.g., (cite: 1986ApJ...304..713R)), at the frequency of our 0.45 mm image, i.e. $\sim$650 GHz, we expect free-free emission from the jet to be optically thin. Thus, there must be a turning point between 50 and 650 GHz. A conservative assumption is that emission from the jet becomes totally optically thin at 100 GHz. Then, using equation [\[Eq1\]](#Eq1) to estimate the free-free emission at 100 GHz, and extrapolating this with a spectral index of $-$0.1 to higher frequencies, we obtain that an estimate of the free-free contamination at 650 GHz would be $\sim$300 $\mu$Jy, which is a $\sim$2% of the peak emission at the center of the disk in the 0.45 mm image. Note that the actual contribution at this frequency should be lower since it is very likely that the free-free emission would become optically thin at a frequency lower than 100 GHz. Another potential explanation for a significant free-free emission at the central part of the disk is the possibility of it becoming highly optically thick due to photoionization. However, this scenario faces challenges because HL Tau is a K-type star, and such stars typically do not emit sufficient ionizing photons to fully ionize a very dense gas. Taking all of these factors into account, it leads us to the conclusion that the elevated emission in the inner region of the disk is unlikely to be primarily caused by free-free contributions.

An interesting explanation for the increased dust emission at the inner part of the disk is the possibility of a dust particle pile-up occurring in that region. In fact, our unprecedented angular resolution allows us to probe the dust emissions down a few au, inside the estimated water snowline at $\sim$ 5 au if one assumes $T_{disk} = T_{B}$ ((cite: 2015ApJ...806L...7Z), Figure [2](#Fig2)). Inside the water snowline, theoretical models predict the appearance of a traffic-jam effect (e.g (cite: 2015ApJ...815L..15B), (cite: 2017ApJ...845...68P)), as dry silicates are more sensitive to fragmentation than ice-rich grains ((cite: 1997ApJ...480..647D); (cite: 1997Icar..129..539S); (cite: 2013A&A...559A..62W); (cite: 2014acm..conf..191G)), leading to lower particle size and reduced drift speed. The traffic-jam effect offers a favored pathway for the formation of dry planetesimals in the inner disk, however, it has been recently put into question in the light of new experiments on the stickiness of ice-rich grains (e.g. (cite: 2018MNRAS.479.1273G); (cite: 2019ApJ...873...58M)) and observations of the resilience of icy pebbles to sublimation (cite: 2023arXiv231201856H). Interestingly, (cite: Facchini2024) recently detected water emission at 321 GHz coming from the inner disk of HL Tau, but their spatial resolution was not enough to robustly measure the position of the water snowline.

Our results could be consistent with the presence of a traffic-jam effect, as such a pile-up of solids would increase the dust density and optical depth inside the water snowline (e.g. (cite: 2015ApJ...815L..15B)), causing observations to probe higher layers of the disk with more elevated dust temperatures, thereby manifesting a higher brightness temperature as we see in Figure [2](#Fig2) (See (cite: 2017A&A...608A..92D) and (cite: 2019A&A...629A..65R)). Moreover, an increase in the population of smaller particles will also result in a decrease in the albedo, which in turn results in an increase in the emission.

A second possibility is that the increase in the brightness temperature is attributed to viscous heating occurring in the inner disk. Overall, the heating mechanisms in protoplanetary disks significantly influence the temperature profile of these. The two dominant heating processes in these disks are stellar radiation and viscous heating (cite: 2005ASPC..341..353D). Across the majority of the disk’s extent, stellar radiation contributes the most to the disk’s thermal structure. However, in the innermost regions of the disk close to the mid-plane, where dust surface densities reach notably high values, it is highly likely that viscous heating becomes the primary contributor to the disk temperature profile (cite: 2001ApJ...553..321D).More recently, (cite: 2009ApJ...705.1206C) found that the mid-plane temperature may be affected by viscous heating within the radial range of 1 to 40 au in protoplanetary disks. This phenomenon also influences the position of the snowline, which varies depending on the age of the disk. The position of these, however, is dependent upon the characteristics of the star and many other parameters which are hard to constrain.

As of now, it is challenging to distinguish between the traffic-jam or viscous heating scenarios, but we strongly encourage future works to focus on that aspect given the implications it could have concerning planet formation in the inner disk. For example, high angular resolution observations at other wavelengths could help constrain the dust emission spectral index and particle size, which would help in understanding the underlying mechanisms driving the observed changes in brightness temperature.\

# Summary and conclusions

We report new sensitive ALMA images at 0.45 mm of the HL Tau disk with an unprecedented high angular resolution of 12 mas or 1.7 au. At this wavelength, the detected emission is known to be highly optically thick. This is evidenced by the shallower substructures observed in our observation. The extended nature of the disk suggests that we are tracing smaller dust particles that are more closely coupled to the gas.

By combining the Band 9 image with the images at other wavelengths, we have updated the model of the dust properties in the disk. The 0.45 mm image has allowed us to better constrain the dust temperature of the disk, which provided better constraints on the dust density and particle size. The particle sizes are still predicted to be larger than mm sizes until $\sim60$ au but there is a significant decrease (to $\sim$ 200 $\mu$m) between 60-100 au. These smaller particles coincide with the region where an accretion shock of infalling material has been found traced by SO and SO$_{2}$. The final derived disk dust masses are 2.1 M$_{J}$ for compact particles and 6.3 M$_{J}$ for porous dust particles. These dust masses translate into gas-to-dust ratios $\leq$ 100.

Our 0.45 mm data clearly shows an asymmetry in the emission coming from the first ring. The emission is considerably more intense in the NE part of the disk than in the SW part. We interpreted this as a combination of very optically thick emission, a moderately inclined disk, and a large dust scale height. In the NE part of the disk, we are directly viewing the emission from the internal wall of the first ring, which is illuminated by the radiation from the central star. This interpretation is supported by our radiative transfer model which demonstrates the dependence of this asymmetry with the dust mass of the inner regions of the disk and the dust scale height. We propose that this kind of asymmetries in other disks can be used to constrain the dust scale height if an independent estimation of the dust mass of the disk has been made. Based on our proposed scenario and the multi-wavelength analysis model, we implied the possibility of a dust scale height H/R $\sim$ \>= 0.08 for the HL Tau disk at least in the inner 32 au. This approximation seems in large contrast with the constraints identified by (cite: 2016ApJ...816...25P) who determined H/R \< 0.01 in the outer disk. We note that this discrepancy might stem from higher turbulence in the inner regions of HL Tau compared to its outer region leading to radial variations of the vertical structure of the HL Tau disk. Incorporating vertical structure in the multi-wavelength analysis to determine the disk mass and employing more quantitative modeling approaches, rather than qualitative ones in RADMC-3D, may be necessary to obtain a more realistic scale height of the disk.

We have resolved the innermost part of the HL Tau disk showing that there is some previously unseen substructure, revealed as a steep increase of the brightness temperature very close to the central star, at radii smaller than 5 au. Interestingly, the radius at which this increase starts appears to coincide with the position of the water ice line. Therefore, we discuss the possibility of a pile-up of small particles due to a decrease in the drift velocity of the small grains after crossing the water snowline and suffer a more efficient fragmentation. We also discuss a different possibility in which we are resolving the region where the heating of the disk changes from being dominated by irradiation to being dominated by viscous heating. Previous theoretical models predict that this change should take place very close to the protostar. To further confirm either of these scenarios, additional modeling and observations at other wavelengths are necessary for the HL Tau disk.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2011.0.00005.E and ADS/JAO.ALMA$\#$2017.1.01178.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

C.C.-G. acknowledges support from UNAM DGAPA-PAPIIT grant IG101321 and from CONACyT Ciencia de Frontera project ID 86372.

The research of M.V. was supported by an appointment to the NASA Postdoctoral Program at the NASA Jet Propulsion Laboratory, administered by Oak Ridge Associated Universities, under contract with NASA.

79 natexlab

(ref: 2015ApJ...808L...3A) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3

(ref: 2020ApJS..247...23A) Asaki, Y., Maud, L. T., Fomalont, E. B., et al. 2020, ApJS, 247, 23

(ref: 2023ASPC..534..423B) Bae, J., Isella, A., Zhu, Z., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 423

(ref: 2015ApJ...815L..15B) Banzatti, A., Pinilla, P., Ricci, L., et al. 2015, ApJL, 815, L15

(ref: 2005A&A...443..185B) Barrière-Fouchet, L., Gonzalez, J. F., Murray, J. R., Humble, R. J., & Maddison, S. T. 2005, A&A, 443, 185

(ref: 2018ApJ...869L..45B) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45

(ref: 2020MNRAS.493L.108B) Booth, A. S. & Ilee, J. D. 2020, MNRAS, 493, L108

(ref: 2016ApJ...821L..16C) Carrasco-González, C., Henning, T., Chandler, C. J., et al. 2016, ApJL, 821, L16

(ref: 2019ApJ...883...71C) Carrasco-González, C., Sierra, A., Flock, M., et al. 2019, ApJ, 883, 71

(ref: 2015ApJ...812..126C) Casassus, S., Wright, C. M., Marino, S., et al. 2015, ApJ, 812, 126

(ref: 2018A&A...619A.161C) Cazzoletti, P., van Dishoeck, E. F., Pinilla, P., et al. 2018, A&A, 619, A161

(ref: 2009ApJ...705.1206C) Chambers, J. E. 2009, ApJ, 705, 1206

(ref: 2001ApJ...553..321D) D’Alessio, P., Calvet, N., & Hartmann, L. 2001, ApJ, 553, 321

(ref: 2005ASPC..341..353D) D’Alessio, P., Calvet, N., & Woolum, D. S. 2005, in Astronomical Society of the Pacific Conference Series, Vol. 341, Chondrites and the Protoplanetary Disk, ed. A. N. Krot, E. R. D. Scott, & B. Reipurth, 353

(ref: 2013A&A...560A.111D) de Juan Ovelar, M., Min, M., Dominik, C., et al. 2013, A&A, 560, A111

(ref: 2022A&A...658A..97D) Delage, T. N., Okuzumi, S., Flock, M., Pinilla, P., & Dzyurkevich, N. 2022, A&A, 658, A97

(ref: 2016MNRAS.459L...1D) Dipierro, G., Laibe, G., Price, D. J., & Lodato, G. 2016, MNRAS, 459, L1

(ref: 2021ApJ...912..164D) Doi, K. & Kataoka, A. 2021, ApJ, 912, 164

(ref: 2021ascl.soft04010D) Dominik, C., Min, M., & Tazaki, R. 2021, Astrophysics Source Code Library, ascl:2104.010

(ref: 1997ApJ...480..647D) Dominik, C. & Tielens, A. G. G. M. 1997, ApJ, 480, 647

(ref: 2017A&A...608A..92D) Drążkowska, J. & Alibert, Y. 2017, A&A, 608, A92

(ref: 2004A&A...421.1075D) Dullemond, C. P. & Dominik, C. 2004, A&A, 421, 1075

(ref: 2012ascl.soft02015D) Dullemond, C. P., Juhasz, A., Pohl, A., et al. 2012, RADMC-3D: A multi-purpose radiative transfer tool, Astrophysics Source Code Library, record ascl:1202.015

(ref: Facchini2024) Facchini, S., Testi, L., Humphreys, E., et al. 2024, Nature Astronomy

(ref: 2013PASP..125..306F) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: 2008ApJS..176..184F) Furlan, E., McClure, M., Calvet, N., et al. 2008, ApJS, 176, 184

(ref: 2018ApJ...859...33G) Galli, P. A. B., Loinard, L., Ortiz-Léon, G. N., et al. 2018, ApJ, 859, 33

(ref: 2022A&A...658A.104G) Garufi, A., Podio, L., Codella, C., et al. 2022, A&A, 658, A104

(ref: 2024A&A...681A..82G) Guerra-Alvarado, O. M., van der Marel, N., Di Francesco, J., et al. 2024, A&A, 681, A82

(ref: 2022A&A...664A.137G) Guidi, G., Isella, A., Testi, L., et al. 2022, A&A, 664, A137

(ref: 2014acm..conf..191G) Gundlach, B. & Blum, J. 2014, in Asteroids, Comets, Meteors 2014, ed. K. Muinonen, A. Penttilä, M. Granvik, A. Virkki, G. Fedorets, O. Wilkman, & T. Kohout, 191

(ref: 2018MNRAS.479.1273G) Gundlach, B., Schmidt, K. P., Kreuzig, C., et al. 2018, MNRAS, 479, 1273

(ref: 2023AJ....166..186H) Hashimoto, J., Liu, H. B., Dong, R., et al. 2023, AJ, 166, 186

(ref: 2023arXiv231201856H) Houge, A., Macı́as, E., & Krijt, S. 2023, arXiv e-prints, arXiv:2312.01856

(ref: 2018ApJ...869L..43H) Huang, J., Andrews, S. M., Pérez, L. M., et al. 2018, ApJL, 869, L43

(ref: 2016PhRvL.117y1101I) Isella, A., Guidi, G., Testi, L., et al. 2016, , 117, 251101

(ref: 2024A&A...682A..32J) Jiang, H., Macı́as, E., Guerra-Alvarado, O. M., & Carrasco-González, C. 2024, A&A, 682, A32

(ref: 2016ApJ...818...76J) Jin, S., Li, S., Isella, A., Li, H., & Ji, J. 2016, ApJ, 818, 76

(ref: 2017ApJ...844L...5K) Kataoka, A., Tsukagoshi, T., Pohl, A., et al. 2017, ApJL, 844, L5

(ref: 2023arXiv230910055L) Lin, Z.-Y. D., Li, Z.-Y., Stephens, I. W., et al. 2023a, arXiv e-prints, arXiv:2309.10055

(ref: 2023ApJ...951....9L) Lin, Z.-Y. D., Li, Z.-Y., Tobin, J. J., et al. 2023b, ApJ, 951, 9

(ref: 2022SCPMA..6529511L) Liu, Y., Bertrang, G. H. M., Flock, M., et al. 2022, Science China Physics, Mechanics, and Astronomy, 65, 129511

(ref: 2017A&A...607A..74L) Liu, Y., Henning, T., Carrasco-González, C., et al. 2017, A&A, 607, A74

(ref: 2020ApJ...898...36L) Long, F., Pinilla, P., Herczeg, G. J., et al. 2020, ApJ, 898, 36

(ref: 2018ApJ...869...17L) Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17

(ref: 2014AJ....147...72L) Lumbreras, A. M. & Zapata, L. A. 2014, AJ, 147, 72

(ref: 2021A&A...648A..33M) Macı́as, E., Guerra-Alvarado, O., Carrasco-González, C., et al. 2021, A&A, 648, A33

(ref: 1977ApJ...217..425M) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2019ApJ...873...58M) Musiolik, G. & Wurm, G. 2019, ApJ, 873, 58

(ref: 2023ApJ...951....8O) Ohashi, N., Tobin, J. J., Jørgensen, J. K., et al. 2023, ApJ, 951, 8

(ref: 2020ApJ...900...81O) Ohashi, S., Kataoka, A., van der Marel, N., et al. 2020, ApJ, 900, 81

(ref: 2016Sci...353.1519P) Pérez, L. M., Carpenter, J. M., Andrews, S. M., et al. 2016, Science, 353, 1519

(ref: 2023arXiv231007332P) Pfeil, T., Birnstiel, T., & Klahr, H. 2023, arXiv e-prints, arXiv:2310.07332

(ref: 2012A&A...545A..81P) Pinilla, P., Benisty, M., & Birnstiel, T. 2012a, A&A, 545, A81

(ref: 2012A&A...538A.114P) Pinilla, P., Birnstiel, T., Ricci, L., et al. 2012b, A&A, 538, A114

(ref: 2015A&A...573A...9P) Pinilla, P., de Juan Ovelar, M., Ataiee, S., et al. 2015, A&A, 573, A9

(ref: 2021A&A...645A..70P) Pinilla, P., Lenz, C. T., & Stammler, S. M. 2021, A&A, 645, A70

(ref: 2017ApJ...845...68P) Pinilla, P., Pohl, A., Stammler, S. M., & Birnstiel, T. 2017, ApJ, 845, 68

(ref: 2016ApJ...816...25P) Pinte, C., Dent, W. R. F., Ménard, F., et al. 2016, ApJ, 816, 25

(ref: 2023MNRAS.524.3184P) Pizzati, E., Rosotti, G. P., & Tabone, B. 2023, MNRAS, 524, 3184

(ref: 2011A&A...532A..71R) Rau, U. & Cornwell, T. J. 2011, A&A, 532, A71

(ref: 1986ApJ...304..713R) Reynolds, S. P. 1986, ApJ, 304, 713

(ref: 2010A&A...512A..15R) Ricci, L., Testi, L., Natta, A., et al. 2010, A&A, 512, A15

(ref: 2019A&A...629A..65R) Ros, K., Johansen, A., Riipinen, I., & Schlesinger, D. 2019, A&A, 629, A65

(ref: 2020ApJ...892..136S) Sierra, A. & Lizano, S. 2020, ApJ, 892, 136

(ref: 2019ApJ...876....7S) Sierra, A., Lizano, S., Macı́as, E., et al. 2019, ApJ, 876, 7

(ref: 2021ApJS..257...14S) Sierra, A., Pérez, L. M., Zhang, K., et al. 2021, ApJS, 257, 14

(ref: 2022A&A...668A.104S) Stadler, J., Gárate, M., Pinilla, P., et al. 2022, A&A, 668, A104

(ref: 1997Icar..129..539S) Supulver, K. D., Bridges, F. G., Tiscareno, S., Lievore, J., & Lin, D. N. C. 1997, Icarus, 129, 539

(ref: 2021MNRAS.506.5117T) Tazzari, M., Testi, L., Natta, A., et al. 2021, MNRAS, 506, 5117

(ref: 2015ApJ...810L...7V) van der Marel, N., Pinilla, P., Tobin, J., et al. 2015, ApJL, 810, L7

(ref: 2013Sci...340.1199V) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2013, Science, 340, 1199

(ref: 2020A&A...642A.164V) Villenave, M., Ménard, F., Dent, W. R. F., et al. 2020, A&A, 642, A164

(ref: 2022ApJ...930...11V) Villenave, M., Stapelfeldt, K. R., Duchêne, G., et al. 2022, ApJ, 930, 11

(ref: 2013A&A...559A..62W) Wada, K., Tanaka, H., Okuzumi, S., et al. 2013, A&A, 559, A62

(ref: 2004ApJ...616..998W) White, R. J. & Hillenbrand, L. A. 2004, ApJ, 616, 998

(ref: 2015ApJ...806L...7Z) Zhang, K., Blake, G. A., & Bergin, E. A. 2015, ApJL, 806, L7

(ref: 2023ApJ...953...96Z) Zhang, S., Zhu, Z., Ueda, T., et al. 2023, ApJ, 953, 96

# MCMC model vs observations: VLA fitting

![](Figure_profileMediansNoPoroso.pdf)

![](Figure_profileMediansPoroso.pdf)

</paper>

Write the methods card for this paper.