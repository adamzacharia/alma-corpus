# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...976..258K\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...976..258K",
 "title": "Chemistry in the GG Tau A Disk: Constraints from H<SUB>2</SUB>D<SUP>+</SUP>, N<SUB>2</SUB>H<SUP>+</SUP>, and DCO<SUP>+</SUP> High Angular Resolution ALMA Observations",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Kashyap, Parashmoni",
 "n_authors": 20,
 "arxiv_id": "2407.07238",
 "doi": "10.3847/1538-4357/ad815c",
 "alma_projects_linked_by_archive": [
  "2021.1.00342.S"
 ]
}
```

Paper text:
<paper>
# Chemistry in the GG Tau A Disk: Constraints from H$_2$D$^+$, N$_2$H$^+$, and DCO$^+$ High Angular Resolution ALMA Observations

## Abstract

Resolved molecular line observations are essential for gaining insight into the physical and chemical structure of protoplanetary disks, particularly in cold, dense regions where planets form and acquire their chemical compositions. However, tracing these regions is challenging because most molecules freeze onto grain surfaces and are not observable in the gas phase. We investigated cold molecular chemistry in the triple stellar T Tauri disk GG Tau A, which harbours a massive gas and dust ring and an outer disk, using ALMA Band 7 observations. We present high angular resolution maps of and emission, with upper limits reported for , $^{13}$CS, and . The radial intensity profile of shows most emission near the ring outer edge, while exhibits double peaks, one near the ring inner edge and the other in the outer disk. With complementary observations of lower-lying transitions, we constrained the molecular surface densities and rotation temperatures. We compared the derived quantities with model predictions across different cosmic ray ionization (CRI) rates, carbon-to-oxygen (C/O) ratios, and stellar UV fluxes. Cold molecular chemistry, affecting , , and abundances, is most sensitive to CRI rates, while stellar UV flux and C/O ratios have minimal impact on these three ions. Our best model requires a low cosmic ray ionization rate of $10^{-18}$ s$^{-1}$. However, it fails to match the low temperatures derived from and , 12 to 16 K, which are much lower than the CO freezing temperature.

# Introduction

A protoplanetary disk is a crucial stage in the evolution of cosmic matter, where the interplay of inherited material from a parent cloud and the in-situ physics and chemistry establishes the conditions for planet formation. Protoplanetary disks are characterized by complex chemical stratification owing to radial and vertical variations in density, temperature, ionization, and dissociative radiation (cite: Aikawa2002). The uppermost layers usually allow the formation of simple atoms, ions, and photo-stable radicals, while the intermediate warm molecular layer produces most of the gas phase molecules traced by the Atacama Large Millimeter/submillimeter Array (ALMA) observations. There is minimal penetration of stellar radiation in the innermost regions near the midplane in the vertical direction, making them very cold and poorly ionized. In this dense region, most of the molecules freeze onto grain surfaces. Hence, midplane regions are very difficult to probe. N$_2$H$^+$, DCO$^+$, and H$_2$D$^+$ are among the very few molecules which remain in the gas phase in the midplane region (cite: Ceccarelli2004; Oberg2011).

N$_2$H$^+$ is expected to be abundant in regions where is depleted. This anti-correlation is observed in both dense cores (cite: Caselli1999; Bergin2002) as well as in disks (cite: Walsh2012). is produced through the protonation of and rapidly destroyed by CO in its presence to form . Hence, N$_2$H$^+$ can persist in the gas phase at temperatures a few Kelvin below the CO freeze-out temperature (cite: Oberg2005). N$_2$H$^+$ has been observed in multiple disks (cite: Dutrey2007; Qi2013; Phuong2021; Anderson2022), but is often characterized by comparatively weak emission.

An enhanced abundance of H$_2$D$^+$ is predicted by chemical models at low temperatures (T$<$20 K), with the major formation pathway being protonation of (cite: Robert2000). H$_2$D$^+$ can only be observed in high-density regions with low and content where has not already been destroyed. H$_2$D$^+$ has already been detected in prestellar cores (cite: Caselli2008), but there is no clear detection in any of the protoplanetary disks (cite: Ceccarelli2004; Thi2004; Qi2008; Chapillon2011).

DCO$^+$ serves as an effective indicator of low-temperature CO freezeout regions within the disk and is predominantly formed through the interaction of with H$_2$D$^+$ (cite: Wootten1987). On the one hand, the formation of mainly occurs through HD protonation and is hindered by the destruction of in the presence of CO. On the other hand, the presence of CO is essential for DCO$^+$ formation. Consequently, DCO$^+$ emission is expected to peak in a narrow region around the snowline where both the parent molecules are in the gas phase in small amounts (cite: Aikawa2002; Willacy2007; Mathews2013).

In summary, N$_2$H$^+$, DCO$^+$, and H$_2$D$^+$ are excellent tracers of low-temperature, high-density regions of the disk, specifically the midplane region in outer disks. Simultaneous observations of these molecules allow us to locate the CO snowline. Snowlines are thought to play an important role in planet formation because the ice coating on grains increases the solid mass, potentially promotes the coagulation of grains into larger particles, and/or the larger bodies formed from these grains require a higher collision velocity for destruction. These effects are particularly prominent just outside the snowline (cite: Okuzumi2012). Additionally, such observations provide insights into ionization fractions within the relevant disk areas, offering constraints that can impact magneto-rotational instability. In instances of excessively low ionization fractions, “dead zones" (cite: Gammie1996) form, which are conducive to efficient grain growth and subsequent planet formation (cite: Oberg2011).

This work reports spatially resolved emission from N$_2$H$^+$ (4-3) and DCO$^+$ (5-4) and upper limits for o-H$_2$D$^+$ (1(1,0)-1(1,1)), $^{13}$CS (8-7), and SO$_2$ 19(4,16)-19(3,17) in the disk around a triple stellar T Tauri system, GG Tau A, utilizing the ALMA interferometer. This represents the most sensitive observation of these molecules in GG Tau A to date. The system (age 1-5 Myr) is located at a distance of 150 pc (cite: Gaia2016; Gaia2018) from us in the Taurus-Auriga star-forming region. This circumtertiary disk is characterized by a dense ring of gas and dust between 193 and 285 au (from here on, we simply use the term ring to denote this region) where 90% of the continuum emission arises and an outer disk extended up to 800 au in $^{13}$CO observations (cite: Guilloteau1999; Dutrey2014). The majority of the total disk mass (0.15 $M_{\odot}$) is concentrated in the ring region (0.13 $M_{\odot}$) (cite: Guilloteau1999; Andrews2014). (cite: Dutrey2014) reported the presence of a hot spot located at the outer edge of the dense ring where a partial CO gap is observed (cite: Tang2016), suggesting the presence of an embedded planet. This hypothesis is reinforced by the detection of a CO spiral emanating from the hot spot (cite: Phuong2020a).

This disk is very cold, with a midplane temperature of $\sim$ 14 K (cite: Dutrey2014) and an atmospheric temperature of $\sim$ 30 K (cite: Guilloteau1999; Phuong2020), at a radial distance of 214 au from the center. The first-ever detection of in the outer disk of GG Tau A by (cite: Phuong2018) further confirms how dense and massive this system is. Given its substantial mass, high density (which should ease the detection of weak molecular lines), and low temperature, GG Tau A emerges as an ideal candidate for unravelling the intricacies of cold molecular chemistry within a protoplanetary disk.

We present our observational details in Section [2](#sec:obs) of this paper. We explain the schemes we undertake to reduce the data in Section [2.1](#subsec: data_red) and the observational results in Section [2.2](#subsec:obs_res), including integrated intensity maps, radial profiles, and Keplerian deprojected spectra. We also constrain the surface density of the detected molecules and the upper limits of surface density for the undetected molecules, as explained in Section [3](#sec:constr_disk_phy_params). We perform a chemical analysis to understand our observations better using our astrochemical model, detailed in Section [4](#sec:models). We discuss our results in Section [5](#sec:discussions) and summarize the key understandings of our study in Section [6](#sec:conclusion).

# Observations

+:---------------:+:-----------------------:+:---------------:+:---------------:+:---------------:+:---------------:+:---------------:+
| Spectral Window | Central Frequency (GHz) | Bandwidth                         | Resolution                        | No. of Channels |
|                 |                         +-----------------+-----------------+-----------------+-----------------+                 |
|                 |                         | Frequency (MHz) | Velocity (km/s) | Frequency (MHz) | Velocity (km/s) |                 |
+-----------------+-------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 25              | 358.000000              | 1875.00         | 1570.2          | 1.129           | 0.945           | 3840            |
+-----------------+-------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 27              | 359.770685              | 117.19          | 97.7            | 0.141           | 0.118           | 1920            |
+-----------------+-------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 29              | 360.169780              | 117.19          | 97.5            | 0.141           | 0.117           | 1920            |
+-----------------+-------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 31              | 369.908554              | 117.19          | 95.0            | 0.141           | 0.114           | 1920            |
+-----------------+-------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 33              | 372.421385              | 117.19          | 94.3            | 0.122           | 0.098           | 1920            |
+-----------------+-------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 35              | 372.672493              | 58.59           | 47.1            | 0.141           | 0.114           | 960             |
+-----------------+-------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+

: Spectral Setup of the ALMA Band 7 Observations of GG Tau A

The GG Tau A system (ICRS 04:32:30.3460, 17:31:40.642) was observed as part of the ALMA project #2021.1.00342.S (PI: Liton Majumdar) targeting to investigate the presence of Band 7 transitions, o-H$_2$D$^+$ (1(1,0)-1(1,1)), N$_2$H$^+$ (4-3), DCO$^+$ (5-4)  $^{13}$CS (8-7) and SO$_2$ 19(4,16)-19(3,17). The observations were made over two executions using 47 antennas with baselines ranging from 14 m to 456 m for a total on-source integration time of 2.7 hours. The spectral setup details can be found in Table [\[tab:spectral_setup\]](#tab:spectral_setup).

## Data Reduction

Calibration procedures involved bandpass and flux calibration, with the quasar source J0423-0120 utilized for this purpose. Phase calibration was conducted using the sources J0510+1800 and J0440+1437. The observed data were initially calibrated with CASA, the Common Astronomy Software Applications package (version 6.4.1.12) pipeline. Subsequently, five rounds of continuum self-phase calibration were performed for each execution, selecting line-free channels carefully. The self-calibration solutions were then applied to the entire dataset. To determine the disk center, we fitted the continuum structure with an ellipse, and both executions were recentered to the disk center using the `fixvis` task in CASA. The offset between the disk centers in the two executions was only (0.005$''$, 0.003$''$), which is well below our observed angular resolution of 0.5$''$– 0.9$''$. The data with the identical spectral setups from both executions were then combined using the `concat` task in CASA. We performed continuum subtraction on the self-calibrated recentered data by fitting a first-order polynomial to the continuum channels using `uvcontsub` task in CASA. We constructed the images from our visibility dataset in `tclean` task in CASA using `hogbom` deconvolving algorithm with `briggs` weighting (robust=1.0). This yielded an angular resolution of $0.93'' \times 0.77''$ at Position Angle (PA) $68.76^\circ$, and a typical sensitivity of 14.6 mJy/beam for N$_2$H$^+$ (channel maps are presented in Figure [9](#fig:ch_maps_n2hp)). For DCO$^+$, we achieved an angular resolution of $0.91'' \times 0.73''$ at PA $99.20^\circ$, with a sensitivity of 5.6 mJy/beam (channel maps are presented in Figure [10](#fig:ch_maps_dcop)). For H$_2$D$^+$, the noise (16.7 mJy/beam) is higher as the atmospheric transmission is degraded at this high frequency. For the weaker lines, including H$_2$D$^+$, we have used `multiscale` deconvolver with `scales = [0,5,15,25]` $\times$ pixels where each pixel corresponds to one-seventh of the beam size. We adopted the `natural` weighting scheme to enhance the signal-to-noise ratio for the weak lines. The masks used during cleaning were generated with the `keplerian_mask.py` tool [^1] with the geometric parameters $M_{*}$ = $1.37 M_{\odot}$, i = 37$^{\circ}$, and PA = 278$^{\circ}$ confined within inner and outer radii of 1$''$ and 3.5$''$ respectively (values rescaled from (cite: Guilloteau1999) for a distance of 150 pc). Additionally, a continuum image was generated for a spectral window with a central frequency of 358 GHz, utilizing the line-free channels. The deconvolution algorithm employed was `hogbom`, and the process utilized the `briggs` weighting scheme with the robust parameter set to 0.

## Observational Results

The integrated intensity maps were generated by collapsing the image cubes along the velocity axis while applying the Keplerian masks used for cleaning. We did not use any intensity threshold criteria to decide the inclusion of pixels while generating the moment map. For this purpose, we employed `bettermoments` python package (cite: 2018RNAAS...2c.173T). Figure [1](#fig:mo_maps) displays integrated intensity maps for the targeted molecules, where the elliptical contours indicate the location of the dust continuum ring region (193 au - 285 au) of the disk GG Tau. It also displays the continuum image at the central frequency of 358 GHz in the bottom right corner. Clear detections of N$_2$H$^+$ (4-3) and DCO$^+$ (5-4) are observed, while o-H$_2$D$^+$ (1(1,0)-1(1,1))  $^{13}$CS (8-7) and SO$_2$ 19(4,16)-19(3,17) show no detection.

![](M0_maps_22.pdf)

We generated radial distribution of velocity integrated brightness across the disk from the zeroth moment maps with the help of `radial_profile` function in `GoFish` python package (cite: GoFish) by dividing the disk radial range into a series of annular rings with a width 1/4th of the beam major axis and averaging the emission for each ring. The radial profiles for N$_2$H$^+$ (4-3) and DCO$^+$ (5-4) are shown in Figure [2](#fig:radial_intensity). The two vertical lines indicate the ring region (193 au - 285 au). We have also shown the radial profiles for all the transitions generated without keplerian masking in Figure [12](#fig:rad_profile_wihtout_kep). shows a slightly lower emission in the ring region in this case.

![](Integrated_intensity_radial_14th.pdf)

We employed the shifting and stacking technique using the `integrated_spectrum` function in the `GoFish` package (cite: GoFish) to generate a disk-integrated spectrum. Velocities for each pixel were shifted to the systemic one, 6.4 km/s, utilizing system kinematic information used in the generation of the Keplerian mask and stacked to create a Keplerian deprojected spectrum for each transition. The radial range for generating the integrated spectrum is between 120 au and 550 au. We have done a Gaussian fit to the observed spectrum using the `scipy.optimize.curve_fit` to determine the peak intensity and the velocity at which the peak occurs. The width of the observed signal is full width at half maximum, given by $2\sqrt{2 \ln{2}}\sigma$, where $\sigma$ is the standard deviation calculated from our fit. We used `numpy.trapz` function to calculate the disk-integrated flux density of the line signal over a velocity range determined by visual inspection (the shaded region in Figure [3](#fig:int_spectra)). The Keplerian deprojected spectra are shown in the upper panel of Figure [3](#fig:int_spectra). The stacked spectra for N$_2$H$^+$ (4-3) and DCO$^+$ (5-4) are peaking at the systemic velocity, $v_{\text{LSRK}}$ of 6.4 km/s, confirming the detections. The disk-integrated flux densities are reported in Table [\[tab:obs_lines\]](#tab:obs_lines). The $1\sigma$ errors are calculated as $f \times \delta S \times \delta v \times \sqrt{N}$, where $f$ is the spectral correlation factor derived from the noise autocorrelation spectrum), $\delta S$ is the noise associated with each channel, $\delta v$ is the channel width, and $N$ is the number of channels over which integration is performed.

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Species | Transition | Frequency | E$_u$ | log$_{10}$(A$_{ul}$$)$ | g$_u$ | Filter Response | Integrated Intensity | Line Width |
|  |  | (GHz) | \(K\) | (s$^{-1}$) |  | ($\sigma$) | (mJy km s$^{-1}$) | (km s$^{-1}$) |
| N$_2$H$^+$ | 4-3 | 372.6724808 | 44.71 | -2.50934 | 81 | 43 | 1570 $\pm$ 40 | 0.55 $\pm$ 0.01 |
| DCO$^+$ | 5-4 | 360.1697783 | 51.86 | -2.42480 | 11 | 20 | 290 $\pm$ 20 | 0.46 $\pm$ 0.01 |
| H$_2$D$^+$ | 1(1,0)-1(1,1) | 372.4213558 | 104.20 | -3.96567 | 9 | \- | \<58 | \- |
| $^{13}$CS | 8-7 | 369.9085505 | 79.89 | -2.97351 | 34 | \- | \<70 | \- |
| SO$_2$ | 19(4,16)-19(3,17) | 359.7706846 | 214.26 | -3.41473 | 39 | \- | \<35 | \- |

: Properties of the Lines Observed

Table notes: Here, E$_{u}$ is the upper energy level of the transition, A$_{ul}$ is the Einstein coefficient for spontaneous transition, and g$_u$ is the upper state degeneracy. The error bars on the integrated intensity for the detected molecules are 1$\sigma$. We have calculated a 3$\sigma$ upper limit on flux densities for the undetected molecules for an integration area between radius 150 au and 450 au and a line width of 0.55 km/s (Appendix [9](#sec:rotational_diagram)). The line width comes from the full-width half maximum of the Gaussian fitting in Figure [3](#fig:int_spectra) (Section [2.2](#subsec:obs_res)).

We further verified our detections with the matched filtering technique (cite: loomis2018detecting). In this method, we cross-correlate observed visibility with modelled visibility derived from the Keplerian masks used during cleaning. We utilized a package called `VISIBLE` (cite: loomis2018visible) for this task. For N$_2$H$^+$ (4-3), we found a filter response of 43 $\sigma$, and for DCO$^+$ (5-4), it is 20 $\sigma$ at the systemic velocity of 6.4 km/s (Table [\[tab:obs_lines\]](#tab:obs_lines)). The matched filter responses are shown in the Figure [13](#fig:matched_filter).

![](int_spetra.pdf)

Additionally, calibrated visibilities were exported to UVFITS format using the CASA task `exportuvfits` for subsequent analysis with the IMAGER program[^2] and the DISKFIT disk model fitting tool (cite: Pietu2007). Spectra and radial peak brightness profiles generated by `KEPLER` are presented in Figure [14](#fig:kepler-n2h) in Appendix [8](#app:imager). The `KEPLER` command in IMAGER is similar to the `GoFish` package. The reconstructed spectra and radial profiles slightly differ from those in Figure [3](#fig:int_spectra) because of the higher angular resolution ($0.65'' \times 0.53''$ at PA $80^\circ$) used in IMAGER.

Both N$_2$H$^+$ (4-3) and DCO$^+$ (5-4) are detected with a very high signal-to-noise ratio, with N$_2$H$^+$ (4-3) being the stronger detection among the two. Radial profiles (Figures [2](#fig:radial_intensity), [14](#fig:kepler-n2h)) indicate that the N$_2$H$^+$ (4-3) emission exhibits a ring-like radial distribution, peaking near the outer edge of the continuum ring. In contrast, the radial distribution of DCO$^+$ (5-4) peak brightness temperature (Figure [14](#fig:kepler-n2h)) shows a double-ringed structure. The inner DCO$^+$ (5-4) emission arises from the continuum ring, while an outer, brighter DCO$^+$ (5-4) emission originates from the outer disk region. This suggests radial variations in the deuteration process across the disk. However, this double-ringed structure is less prominent in the velocity-integrated radial profile (right panel in Figure [2](#fig:radial_intensity)), possibly due to the lower angular resolution. Other targeted species, including H$_2$D$^+$, , and SO$_2$, are not detected (Figure [13](#fig:matched_filter)).

# Derivation of Disk Physical Parameters

## DiskFit modelling

To derive disk properties, we perform a least-square fit to the observed visibilities to adjust an empirical parametric disk model to the data, using the DISKFIT tool from (cite: Pietu2007). This approach allows an accurate derivation of the geometrical parameters. Furthermore, when several transitions of the same molecules are available, it allows a quantitative estimate of the molecular surface densities and excitation temperatures. It also allows for consistent estimates of the errors on the disk parameters (within the framework of the adopted disk model). This can be done either from the covariance matrix (when parameter coupling is limited) or through a more elaborate Monte Carlo Markov Chain method.

The disk model is similar to that used in (cite: Phuong2020). It uses a flared disk geometry with a Gaussian vertical profile and a radial power-law for the scale height. Molecules are assumed to follow the same vertical distribution for simplicity. The model assumes level populations are governed by a Boltzmann law, with the temperature being a power law of radius. For a simple comparison with the observed data, we assume that the intrinsic line width remains constant with radius. In fact, fitting line width as a power law instead suggests a small but non-significant decrease of intrinsic line width with radius that does not affect the other disk parameters. The emerging line intensity is derived using simple ray tracing, considering the geometry and dynamics (position, orientation, inclination, velocity, and Keplerian rotation pattern) and level populations computed at every sampled point along the line of sight. The hyperfine structure of the observed lines is also considered at this stage. This approach implicitly accounts for line optical depth.

Visibilities are then computed on the same $(u,v)$ points as the data from the 3D data cube. A least square minimization is performed on the different visibilities using a modified Levenberg-Marquardt algorithm. Guided by the radial distribution of velocity-integrated brightness (Figure [2](#fig:radial_intensity)) and apparent brightness temperature (Figure [14](#fig:kepler-n2h)), we represented the radial surface density profiles for each molecule by the sum of two Gaussians, truncated to inner and outer radii of 150 and 550 au, respectively. The rotation temperature is assumed to be a simple power law, defined by its value at 250 au, $T_{250}$ and exponent $q$. The model thus has 15 possible parameters, 6 due to geometry and 9 to represent the molecular distribution and excitation conditions (see Tables [\[tab:geom\]](#tab:geom)-[\[tab:diskfitabun\]](#tab:diskfitabun) for their designation).

Error bars are derived from the covariance matrix. The six geometric parameters, the line width $\delta V$, and temperature parameters exhibit very little coupling among them and with the other ones. However, the Gaussian distribution parameters are strongly coupled, particularly the pair ($N_i, W_i$) for distribution $i$, so their error bars should be treated with caution.

The parameter fitting process involves a two-stage approach. In the first stage, geometric parameters are individually fitted for every observed transition. The geometric parameters derived from N$_2$H$^+$ and DCO$^+$ are given in Table [\[tab:geom\]](#tab:geom), using the distance of 150 pc determined from Gaia. These transitions are relatively optically thin and, thus, more reliable tracers of the disk inclination than those previously used. Derived inclinations and orientation agree (but offer better precision) with previous determinations from CO isotopologues (cite: Dutrey2014; Phuong2018).

The second stage entails averaging the corresponding values of six geometric parameters across both spectral lines, fixing these averaged values, and proceeding to fit the remaining nine parameters.

| Quantity | N$_{2}$H$^{+}$ (4-3) | DCO$^{+}$ (5-4) | Adopted |  |  |  |  |
|:---|---:|:--:|:---|---:|:--:|:---|:--:|
| X$_0$ ($''$) | -0.007 $\pm$ 0.011 | 0.019 $\pm$ 0.016 | 0 |  |  |  |  |
| Y$_0$ ($''$) | -0.001 $\pm$ 0.007 | 0.004 $\pm$ 0.011 | 0 |  |  |  |  |
| PA ($^\circ$) | 8.4 $\pm$ 0.5 | 8.1 $\pm$ 0.5 | 8 |  |  |  |  |
| $i$ ($^\circ$) | 36.5 $\pm$ 0.4 | 37.0 $\pm$ 0.4 | 37 |  |  |  |  |
| $V_{sys}$ (km.s$^{-1}$) | 6.45 $\pm$ 0.03 | 6.43 $\pm$ 0.03 | 6.43 |  |  |  |  |
| $V_{100}$ (km.s$^{-1}$) | 3.61 $\pm$ 0.03 | 3.54 $\pm$ 0.03 | 3.55 |  |  |  |  |

: Geometric and dynamic parameters determined through DISKFIT modelling

Table notes:\
Best fit geometric parameters from the observed visibilities. Offsets (X$_0$,Y$_0$) are from the ring center. $V_{100}$ is the Keplerian velocity at 100 au. PA of 8$^\circ$ in DISKFIT is equivalent to 278$^\circ$ in `GoFish`. In DISKFIT, PA is measured with respect to the disk minor axis, while in `GoFish`, this angle is measured with respect to the disk major axis. The “Adopted” column indicates the fixed parameter values used for the multi-transition model fit in Table [\[tab:diskfitabun\]](#tab:diskfitabun)

To derive the surface densities and rotation temperatures, we used complementary data, which is made of the interferometric visibilities obtained with NOEMA for N$_2$H$^+$ (1-0) and DCO$^+$ (1-0) from (cite: Phuong2021), and the DCO$^+$ (3-2) from (cite: Phuong2018). Geometric parameters from the “Adopted" column of Table [\[tab:geom\]](#tab:geom) were used at this stage. Results are presented in Table [\[tab:diskfitabun\]](#tab:diskfitabun). Figure [4](#fig:diskfit) shows the constrained radial distributions of surface densities. Agreement with the observations can be seen in Figure [14](#fig:kepler-n2h), where the best fit radial profile (reconstructed by imaging the model visibilities and applying the Kepler deprojection) is compared with the data.

While this process is appropriate for DCO$^+$, the N$_2$H$^+$ distribution can almost equally well be represented by a single Gaussian or a truncated power law. This, however, does not affect the temperature derivation. The temperature that best represents N$_2$H$^+$ is almost constant, slightly increasing with radius and quite low, 12 K. On the contrary, DCO$^+$ is better represented by higher temperatures, decreasing with radius from $\sim 18$ K at 200 au to $\sim 12$ K at 500 au.

As expected, the FWHM line width derived from the $uv$ plane analysis with DISKFIT (0.25  km/s using the 1/e values in Table [\[tab:diskfitabun\]](#tab:diskfitabun)) is smaller than those in the recentered spectra from `GoFish` (0.55 km/s, Fig.[3](#fig:int_spectra)) and `KEPLER` (0.37 km/s, Fig. [14](#fig:kepler-n2h)) because of the remaining Keplerian shear within the synthesized beams used in these image plane reconstructions.

For H$_2$D$^+$, we simply assumed the same geometrical parameters (“Adopted” column in Table [\[tab:geom\]](#tab:geom)), a constant temperature of 15 K, and a uniform surface density between 150 and 450 au. The best fit surface density of ortho-H$_2$D$^+$ from DISKFIT is then $(0.7 \pm 0.7) \times 10^{10}$ cm$^{-2}$. This gives the 3$\sigma$ upper limit on o- to be $2.1 \times 10^{10}$ cm$^{-2}$.

![](radial_colden_diskfit.pdf)

| Quantity   |   N$_{2}$H$^+$    |     DCO$^{+}$     | Unit                |
|:-----------|:-----------------:|:-----------------:|:--------------------|
| $\delta V$ | 0.149 $\pm$ 0.005 | 0.150 $\pm$ 0.005 | km s$^{-1}$         |
| $T_{250}$  |  12.2 $\pm$ 0.7   |  16.0 $\pm$ 1.2   | K                   |
| $q$        | -0.32 $\pm$ 0.19  |  0.39 $\pm$ 0.15  |                     |
| $N_{1}$    |    22 $\pm$ 8     |   2.8 $\pm$ 0.6   | $10^{11}$ cm$^{-2}$ |
| $R_{1}$    |    252 $\pm$ 9    |   210 $\pm$ 50    | au                  |
| $W_{1}$    |   95 $\pm$ 115    |   90 $\pm$ 360    | au                  |
| $N_{2}$    |    12 $\pm$ 2     |   5.3 $\pm$ 1.0   | $10^{11}$ cm$^{-2}$ |
| $R_{2}$    |   336 $\pm$ 20    |   375 $\pm$ 10    | au                  |
| $W_{2}$    |   145 $\pm$ 15    |    90 $\pm$ 15    | au                  |

: Best fit parameters for the molecular distributions and excitation conditions.

Table notes:\
Parameters derived from the best fit of a double Gaussian radial distribution model. $N_{i}$ is the peak surface density of Gaussian distribution $i$, $R_{i}$ its peak position, and $W_{i}$ its width (FWHM). $\delta V$ is the 1/e line width. $T_{250}$ is the temperature at 250 au, $q$ the exponent of the temperature power law **(**a positive exponent indicates a quantity decreasing with radius)

## Results

Figure [4](#fig:diskfit) displays the radial distribution derived from the DISKFIT modelling. The results from a classical LTE approach on disk averaged quantities (presented in Appendix [9](#sec:rotational_diagram)) are also indicated. The discrepancy between radial profile and disk averaged value for DCO$^+$ at large radii can be attributed to the assumption of constant $T_{rot} = 16$  K while the DISKFIT model shows it drops to 12 K at 500 au, leading to a stronger Boltzmann distribution correction factor.

We did not detect the lines o-H$_2$D$^+$ (1(1,0)-1(1,1)), $^{13}$CS (8-7), and SO$_2$ 19(4,16)-19(3,17). We calculated upper limits on disk averaged surface densities for these molecules using Equation [\[eq:Nt_thin\]](#eq:Nt_thin), while assuming optically thin emission. The calculations considered 3$\sigma$ values integrated over the line width of N$_2$H$^+$ (coming from Gaussian fit in Figure [3](#fig:int_spectra)). Here, the noise $\sigma = f \times \delta S \times \sqrt{\delta v \times \Delta v}$, where f is the spectral correlation factor of 1.6, $\delta S$ is the root mean squared noise in the flux, $\delta v$ is the channel width and $\Delta v$ is the line width over which noise is calculated. The excitation temperature was fixed at 15 K for this purpose. The integration area $\Omega$ is considered for a radial region ranging from 150 au to 450 au. The constrained values are tabulated in Table [\[tab:col_den\]](#tab:col_den).

Our simple LTE approach reports an upper limit on total (summation of both ortho and para species) surface density of $7.48 \times 10^{12}$ cm$^{-2}$, while our analysis quotes an upper limit on ortho- surface density of $2.1 \times 10^{10}$ cm$^{-2}$. Converting this to a total H$_2$D$^+$ surface density requires an assumption on the ortho-to-para ratio. Under the hypothesis of thermalization, this ratio can be very small since the ortho-H$_2$D$^+$ ground state is 86 K above the para ground state, leading to a huge Boltzmann correction factor (from 70 to 300 for temperatures ranging from 20 down to 15 K respectively). At 15 K, the 3$\sigma$ upper limit on the total surface density, derived from the ortho- value, is $6.3 \times 10^{12}$ cm$^{-2}$.

Note that the low-level detection of $^{13}$CS (2-1) with NOEMA, a low energy transition reported by (cite: Phuong2021), implies a surface density of $3 \times 10^{11}$ cm$^{-2}$ for $T_{rot} = 15$ K, below our upper limit.

| Species | Transition | surface density, N$_{T}$ (cm$^{-2}$) | Excitation Temperature, T$_{ex}$ (K) | Optical Depth, $\tau$ |
|:---|:--:|:--:|:--:|:--:|
| N$_2$H$^+$ | 4-3 | $(1.19 \pm 0.04) \times 10^{12}$ | 12 (fixed) | 0.42 |
| DCO$^+$ | 5-4 | $(1.27 \pm 0.08) \times 10^{11}$ | 16 (fixed) | 0.04 |
| H$_2$D$^+$ | 1(1,0)-1(1,1) | $<7.48 \times 10^{12}$ | 15 (fixed) | \- |
| $^{13}$CS | 8-7 | $<1.12 \times 10^{12}$ | 15 (fixed) | \- |
| SO$_2$ | 19(4,16)-19(3,17) | $<2.46 \times 10^{16}$ | 15 (fixed) | \- |

: Disk averaged surface densities of the detected molecules and upper limits on the undetected molecules under LTE assumption

Table notes:\
a) Surface density error are coming from 16th and 84th percentile of the posterior distribution.\
b) The upper limits on the disk averaged surface densities of the undetected molecules (H$_2$D$^+$, $^{13}$CS and SO$_2$) are constrained using the 3$\sigma$ upper limit on the line flux as explained in Section [9](#sec:rotational_diagram).\
c) In this table, we have reported the upper limit on the total (sum of ortho and para spin-states) surface density. The $3\sigma$ upper limit for o- from DISKFIT analysis is $2.1 \times 10^{10}$ cm$^{-2}$.

# Astrochemical Modeling

## Disk Physical Model

Our physical model is constructed for a radial range of 190 au to 290 au, which primarily includes the ring region around the central stellar system GG Tau A. Only 10-20% of the total disk mass is contained in the outer disk region, which, therefore, exhibits a lower density than in the ring. Moreover, the outer disk, under the shadow of the dense ring, is very cold (cite: Tang2016; Dutrey2014; Brauer2019) with poor constraints on the physical properties. We chose not to focus our present modelling effort on this outer region, which has a more complex structure (cite: Tang2016; Phuong2020).

In the ring, the radial distribution of the midplane (T$_{mid}$) and the atmospheric temperature (T$_{atm}$) are taken as power laws, constrained in previous studies by (cite: Dutrey2014) and (cite: Guilloteau1999) respectively. They are of the form $$\begin{align}
    T_{mid} (r) &= T_{mid, R_{\text{ref}}} \left( \frac{r}{R_{\text{ref}}} \right)^{-q} \label{eq:T_mid}\\
    T_{atm} (r) &= T_{atm, R_{\text{ref}}} \left( \frac{r}{R_{\text{ref}}} \right)^{-q}\label{eq:T_atm}
\end{align}$$

The values of the parameters can be found in Table [1](#tab:physical_model). The radial dependency of scale height, H$_r$ at the disk midplane is calculated assuming hydrostatic equilibrium using the midplane temperature (Equation [\[eq:T_mid\]](#eq:T_mid)), the mass of the stellar system, $M_* = 1.37 M_{\odot}$ (rescaled from (cite: Guilloteau1999) considering a distance of 150 pc), the mean molecular weight of the gas per H nuclei $\mu = 2.37$ and the atomic mass unit, $m_H$, as follows $$\begin{align}
    H_r= \sqrt{\frac{k_B T_{mid} r^3}{\mu \, m_H \, G M_*}} \label{eq:H}
\end{align}$$ Here $k_B$ and $G$ are Boltzmann and Gravitational constants, respectively. We constructed the 1D vertical structure at each radial point until 4H$_r$ height. The vertical temperature structure is adopted from (cite: Dartois2003) and (cite: Williams2014) given by, $$\begin{align}
    T(z) = T_{mid} + (T_{atm} - T_{mid})\left[ sin \left(\frac{\pi z}{2 z_q}\right)\right]^{2\sigma}
\end{align}$$

$T_{mid}$ and $T_{atm}$ are defined at the midplane (z = 0) and the upper end (z = z$_q$) of the atmosphere assuming Equations [\[eq:T_mid\]](#eq:T_mid) and [\[eq:T_atm\]](#eq:T_atm), respectively. $z_q$ is set at 4H$_{r}$ in our case. The parameter $\sigma$ denotes the stiffness of the vertical temperature distribution. As pointed out by (cite: Tang2016), the inner edge of the GG Tau ring obstructs a substantial amount of starlight, minimizing the vertical temperature variation within. Therefore, we have chosen a value of 0.5 for $\sigma$. We have kept the dust temperature equal to the gas temperature, as dust and gas are relatively well coupled for such densities ($>10^8$ cm$^{-3}$).

The gas surface density, $\Sigma_g(r)$ \[g cm$^{-2}$\] is parameterized as a power law profile suggested by (cite: Lynden1974), given by: $$\begin{align}
    \Sigma_g(r) = \Sigma_{g, R_{\text{ref}}} \left( \frac{r}{R_{\text{ref}}} \right)^{-\gamma} \label{eq:sigmag_r}  
\end{align}$$

The power law index $\gamma$ is taken to be 1.4 following (cite: Dutrey2014). The gas surface density at the reference radius $R_{\text{ref}}$, $\Sigma_{g, R_{\text{ref}}}$ is calculated considering the mass contained in the circumtertiary ring, $M_{g} = 0.13 M_{\odot}$ (cite: Guilloteau1999; Andrews2014). The calculations are as follows: $$\begin{align}
    M_g = 2\pi \int_{R_{in}}^{R_{out}} \Sigma_g(r)rdr\label{eq:Mg}
\end{align}$$

Substituting Equation [\[eq:sigmag_r\]](#eq:sigmag_r) in [\[eq:Mg\]](#eq:Mg), for $R_{\text{ref}}=214$ au, we get: $$\begin{align}
    \Sigma_{g, R_{\text{ref}}} = \frac{(2-\gamma) M_g}{2 \pi R_{\text{ref}}^\gamma} \left[ R_{\text{out}}^{2-\gamma} - R_{\text{in}}^{2-\gamma}\right]^{-1} = 9.7 \text{ g cm$^{-2}$}
\end{align}$$

We then calculate the number density \[cm$^{-3}$\] at the midplane with, $$\begin{align}
    n_{H_2,midplane} = \frac{\Sigma_g(r)}{\mu \,m_H\,H_r\sqrt{2\pi}}
\end{align}$$ Using the midplane density as the lower limit, we integrate the equation of hydrostatic equilibrium to obtain the vertical density structure (cite: Reboussin2015): $$\begin{align}
    \frac{\partial \ln{n_{H_2}(z)} }{\partial z} = - \left[ \left( \frac{G M_* z}{r^3} \right) \left( \frac{\mu m_H}{k_B T} \right) + \frac{\partial \ln{T}}{\partial z}\right]
\end{align}$$

The local visual extinction is determined from hydrostatic density structure, assuming a conversion factor of $(A_v/N_H)_0 = 6.25 \times 10^{-22}$ (cite: Wagenblast1989) where $N_H = 2N_{H_2}$ is the vertical hydrogen surface density. We assume $N_H$, and consequently $A_v$ are zero above 4H$_r$. To account for the impact of grain size ($r_d$) and dust-to-gas mass ratio ($\varepsilon$), we scale the conversion factor as follows (cite: Wakelam2019): $$\begin{align}
    \frac{A_v}{N_H} = \left( \frac{A_v}{N_H} \right)_0 \frac{\varepsilon}{10^{-2}} \frac{10^{-5}}{r_d(cm)}
\end{align}$$

The stellar UV flux factor $f_{\text{UV}}$ follows the inverse squared law of distance and acts on the top of the disk atmosphere, only half of which is scattered towards the midplane, the rest being absorbed or scattered upwards (cite: Wakelam2016):

$$\begin{align}
    f_{\text{UV}} (r) = \frac{1}{2}\frac{f_{\text{UV}, R_{\text{ref}}}}{\left( \frac{r}{R_{\text{ref}}}\right)^2 + \left( \frac{4H_r}{R_{\text{ref}}} \right)^2}
\end{align}$$ $f_{\text{UV}, R_{\text{ref}}}$ is defined at the surface of the disk in the units of interstellar DRAINE field spectrum, $\chi_0$ (cite: Drain1978) and reported in Table [1](#tab:physical_model). H$_r$ is calculated using Equation [\[eq:H\]](#eq:H). The vertical distribution of UV flux is obtained by multiplying $f_{UV}$ with $e^{-A_v/1.086}$, where $A_v$ is the visual extinction distribution (cite: Du2014).

In our models, we have not implemented grain growth; instead, we considered a uniform grain size of 0.1$\mu m$ (cite: Phuong2018) settling below 1H$_r$. To incorporate dust settling, we adjust the $\varepsilon$ to $10^{-3}$ above 1H$_r$, while maintaining the standard $\varepsilon$ of $10^{-2}$ below 1H$_r$. Figure [5](#fig:best_fit_structure) illustrates the corresponding structure of the best physical model.

| Parameter Description | Values | Units |
|:---|:--:|:--:|
| Fixed Parameters |  |  |
| Stellar mass: $M_*$ | 1.37 | M$_\odot$ |
| Ring mass: $M_g$ | 0.13$^a$ | M$_\odot$ |
| Ring inner radius: $R_{\text{in}}$ | 193 | au |
| Ring outer radius: $R_{\text{out}}$ | 285 | au |
| Reference radius: $R_{\text{ref}}$ | 214 | au |
| Midplane temperature at $R_{\text{ref}}$: $T_{\text{mid, R$_{\text{ref}}$}}$ | 14 | K |
| Atmospheric temperature at $R_{\text{ref}}$: $T_{\text{atm, R$_{\text{ref}}$}}$ | 30 | K |
| Surface density at $R_{\text{ref}}$: $\Sigma_{g,\text{ref}}$ | 9.7 | g cm$^{-2}$ |
| Temperature power-law index: $q$ | 1.1 |  |
| Temperature vertical gradient index: $\sigma$ | 0.5 |  |
| Surface density power law index: $\gamma$ | 1.4 |  |
| Grain size: $r_d$ | 0.1 | $\mu m$ |
| Adjusted Parameters |  |  |
| UV Flux: $f_{\text{UV}, R_{\text{ref}}}$ | 375 | Draine’s unit ($\chi_0$) |
| Cosmic ray ionization, $\zeta_{CR}$ | $10^{-18}$ | s$^{-1}$ |
| Dust settling | Yes |  |
| C/O ratio | 1.0 |  |
| Age of the parent molecular cloud | $10^6$ | yr |
| Age of the disk | $10^6$ | yr |

: Parameter prescription of the best-fit model considered

Table notes: All the fixed values are taken from (cite: Guilloteau1999; Dutrey2014) and $^a$(cite: Andrews2014) and rescaled considering a distance of 150 pc, except $\sigma$ and $\Sigma_{\text{ref}}$. $\sigma$ is expected to be small as the inner edge of the ring casts a shadow on the rest of the structure (cite: Tang2016). $\Sigma_{\text{ref}}$ is calculated using Equation [\[eq:sigmag_r\]](#eq:sigmag_r) assuming 0.13$M_{\odot}$ of total disk mass is contained in the ring region.

![](StructureD2_1e18_co1.0.pdf)

.

## Chemical Model and Network

The gas-grain astrochemical model DNAUTILUS, introduced in (cite: Majumdar2017), is used to compute the 1+1D chemical composition in the ring of GG Tau A by incorporating all the updates from DNAUTILUS 2.0 outlined in (cite: Kotomi2024). DNAUTILUS 2.0 has the capability to investigate deuterium fractionation in both two-phase (gas and grain surface) and three-phase (gas, grain surface, and grain bulk) modes. DNAUTILUS 2.0 includes 1606 gas species, 1472 grain-surface species, and 1472 grain-mantle species, connected by 83,715 gas-phase reactions, 10,967 reactions on grain surfaces, and 9431 reactions in the grain mantles.

Although including spin-state chemistry of hydrogenated species like , , , and their isotopologues would have allowed us to directly investigate chemistry, we chose not to do so. The primary reason is that the newly proposed state-to-species and species-to-state reaction rates for the systems by (cite: Sipila2017) vary depending on density and temperature regimes. Applying them to a protoplanetary disk would require rigorous benchmarking and testing across various star-forming environments, and such extensive validation is beyond the scope of this paper.

## Grid of Models

To find the model that best represents our observationally constrained radial surface density distribution of , , and the upper limits on , , and $^{13}$CS (cite: Phuong2021), we explored a grid of models utilizing the least squares method (refer to Appendix [10](#app:chemical_model)). These models span a range of initial carbon-to-oxygen (C/O) ratios, cosmic ray ionization (CRI) rates and UV flux values (see Table [\[tab:dnautilus_parameters\]](#tab:dnautilus_parameters) in Appendix [10](#app:chemical_model)). The model with the least disagreement with observations ($\chi^2_{\text{red}}$ = 2.78) is an inheritance disk model with initial abundances characterized from a starless dense molecular cloud, illuminated by stellar UV radiation of 375$\chi_0$ at a reference radius of 214 au. First, we allowed the molecular cloud to evolve chemically for $10^6$ years from initial atomic abundances (Table [2](#tab:initial_abun)) with typical physical conditions such as gas and dust temperature of 10 K, a total gas density of $2\times10^4$ cm$^{-3}$, a visual extinction of 15 mag and cosmic ray ionization rate of $1.3 \times 10^{-17}$ s$^{-1}$. We then computed the temporal evolution of chemistry for the inherited material from the cloud in the ring region around GG Tau A for $10^6$ years. The assumption that protoplanetary disks form from a cold, starless, dense molecular cloud with the mentioned physical conditions is based on detailed discussions from (cite: Wakelam2019), without taking into account the chemical evolution between the cold core phase and the protoplanetary disk itself (cite: Drozdovskaya2016). It is crucial to highlight that in order to reproduce the observed surface densities in our disk simulation, a cosmic ray ionization rate ($\zeta_{\text{CR}}$) of about $10^{-18}$ s$^{-1}$ and an initial C/O ratio of 1.0 are necessary. Table [1](#tab:physical_model) presents the parameters describing the best-fit model. Figure [6](#fig:modelled_abundances) showcases the modelled number density distributions within the ring region.

| Element |        Abundance relative to H        | References |
|:--------|:-------------------------------------:|:----------:|
|         |                 $0.5$                 |            |
| He      |         $9.00 \times 10^{-2}$         |     1      |
| N       |         $6.20 \times 10^{-5}$         |     2      |
| O       | $(1.40 - 3.3) \times 10^{-4}{}^{(a)}$ |     3      |
|         |         $1.70 \times 10^{-4}$         |     2      |
|         |         $8.00 \times 10^{-8}$         |     4      |
|         |         $8.00 \times 10^{-9}$         |     4      |
|         |         $3.00 \times 10^{-9}$         |     4      |
|         |         $2.00 \times 10^{-9}$         |     4      |
|         |         $7.00 \times 10^{-9}$         |     4      |
|         |        $2.00 \times 10^{-10}$         |     4      |
|         |         $1.00 \times 10^{-9}$         |     4      |
| F       |         $6.68 \times 10^{-9}$         |     5      |
| HD      |         $1.60 \times 10^{-5}$         |     6      |

: Initial abundances used in our cloud model

Table notes: (1) (cite: Wakelam2008); (2) (cite: Jenkins2009); (3) (cite: Reboussin2015) (4) Low metal abundances from (cite: Graedel1982); (5) Depleted value from (cite: Neufeld2005); (6) (cite: Majumdar2017). (a) O initial abundance is adjusted for C/O ratio ranging from 0.5 to 1.2

![](molecular_ndensD2_1e18_co1.0.pdf)

![](colden_cri.pdf)

![](colden_co.pdf)

# Discussion

## Comparison with Previous Observations

o-H$_2$D$^+$ (1(1,0)-1(1,1)) has been observed in multiple dense starless cores and prestellar cores (cite: Ceccarelli2014). (cite: Caselli2008) reports o- surface density $\sim 10^{12} - 10^{13}$ cm$^{-2}$ in regions characterized by gas density $\sim 10^{5} - 10^{6}$ cm$^{-3}$ and kinetic temperatures around 10 K, with most prominent detections in the densest and centrally concentrated cores. However, no clear detection has been obtained in protoplanetary disks. (cite: Chapillon2011) derived $3 \sigma$ upper limits on o- surface density for the T Tauri disks DM Tau and TW Hya. Depending on the physical model, DM Tau’s upper limit lies between $4.5 \times 10^{11}$ and $1.9 \times 10^{12}$ cm$^{-2}$ and for TW Hya, it is between $9.0 \times 10^{11}$ and $1.4 \times 10^{12}$ cm$^{-2}$. Our upper limit for o- in GG Tau is $2.1 \times 10^{10}$ cm$^{-2}$. Note that (cite: Chapillon2011)’s upper limits are from single-dish observations (1$\sigma$ noise level 0.33 Jy km s$^{-1}$). We have achieved a much higher sensitivity (1$\sigma$ noise level 0.019 Jy km s$^{-1}$), making our observation the best available constraint on the upper limit of o- surface density in any disk to date.

The (3-2) transition has been observed in all five disks (three around T Tauri stars: IM Lup, GM Aur, and AS 209, and two around Herbig Ae stars: HD 163296 and MWC 480) as part of the Molecules with ALMA at Planet-forming Scales (MAPS) program (cite: MAPSX). Despite the diverse continuum structures of the disks with multiple rings and gaps, emission showcases a ring morphology (Figure 4 in (cite: MAPSX)). Our emission is also characterized by a single-ring structure (Figure [2](#fig:radial_intensity)). (cite: Qi2013) has previously reported detection towards TW Hya, and the single-ring emission structure is also evident there. The ring morphology across different disks can be attributed to radial and vertical temperature variations (cite: Qi2013). In the MAPS survey by (cite: MAPSX), two different surface density values are derived by fixing the excitation temperature, $T_{\text{ex}}$, to a) the observationally constrained CO freeze-out temperature $\sim 20$ K and b) the midplane temperatures, $T_{\text{mid}}$, of the respective disks. For the T Tauri disks (IM Lup, GM Aur, and AS 209), the surface density peaks around 10$^{13}$ cm$^{-2}$, while for the Herbig Ae disks (HD 163296 and MWC 480), it reaches up to 10$^{12}$ cm$^{-2}$. Interestingly, GG Tau, despite being a T Tauri disk, exhibits a surface density of approximately 10$^{12}$ cm$^{-2}$. The surface density in TW Hya reported by (cite: Qi2013) ranges from $4 \times 10^{12}$ to $2 \times 10^{15}$ cm$^{-2}$ for different assumed physical structures. (cite: MAPSX) indicates that temperatures as low as 12 K in the emitting region can also explain the observed flux of the 3-2 transition in the protoplanetary disks (e.g., GM Aur, HD 163296, MWC 480) under the LTE assumption. Previously, in (cite: Phuong2021)’s study, in GG Tau A was assumed to be arising from the same layer as CO, following a radial temperature variation, $T(r) = 20 (r/250 \text{ au})^{-1}$ K. Our direct measure of $T(r) = 12$ K for the emitting region (Table [\[tab:diskfitabun\]](#tab:diskfitabun)), based on multi-line excitation analysis, suggests that we are tracing a region much closer to the midplane than initially assumed.

A ring-like radial distribution for has been commonly observed in multiple disks, including the TW Hya, DM Tau, AS 209, V4046 Sgr, MWC 480 and HD 163296 (cite: Qi2008; Mathews2013; Teague2015; Huang2017) and is facilitated by reaction between and (e.g. (cite: Willacy2007)). Contrary to the common scenario, we observe partially overlapping double-ring radial distribution of emission in GG Tau A (refer to Figure [2](#fig:radial_intensity)), which can likely be attributed to different chemical effects in the ring and the outer disk regions owing to the difference in densities between the two regions. This is discussed in detail in Sections [5.2](#subsec:chem_ring) and [5.3](#subsec:chem_outerdisk). Notably, (cite: Oberg2015a) observes double rings in the disk IM Lup. They found that abundance first decreases radially due to CO depletion, then another ring forms due to non-thermal desorption of CO in low surface density outer regions as a result of higher UV penetration. (cite: Phuong2018; Phuong2021) have previously assumed that emission originates from the same region as and characterized by radial temperature, $T(r) = 20 (r/ 250 \text{ au} )^{-1}$ K in GG Tau A. In this work, we found that emission region is best represented by $T(r) = 16 (r/250 \text{ au})^{-0.39}$ K (Table [\[tab:diskfitabun\]](#tab:diskfitabun)). Hence, we expect that emission region lies vertically between emitting region and emitting region and closer to the midplane than previously thought.

## Chemical Trends in the Ring Region

We present a sub-set of chemical models for a selected set of input parameters in Figures [7](#fig:comp_cr) and [8](#fig:comp_co) from the full model grids presented in Table [\[tab:dnautilus_parameters\]](#tab:dnautilus_parameters). Only the CRI rates and the C/O ratio were found to have any significant impact on the modelled surface densities of the targeted molecules. Other parameters cannot be constrained by the current data.

#### Cosmic Ray Ionization

Figure [7](#fig:comp_cr) shows the variation of modelled abundances with CRI rates while keeping the C/O ratio constant at 0.7, and the remaining parameters are set to the best-fit values. , , and abundances are quite sensitive to CRI rates, while UV flux values have no impact whatsoever. This is expected because these molecules probe a high-density, low-temperature, CO-depleted region near the mid-plane where UV penetration is minimal. Hence, cosmic rays are the primary ionization source for this cold molecular chemistry. However, the CRI rate has barely any impact on S-bearing species. It is worth noting that the standard interstellar CRI rate of $10^{-17}$ s$^{-1}$ predicts the surface density above the upper limit and a sub-interstellar CRI rate of $10^{-18}$ s$^{-1}$ explains the observationally constrained surface densities the best. This low CRI rate can be explained by a rise in the number of collisions experienced by CR particles due to the greater effective surface density as they gyrate towards the disk midplane (cite: Padovani2013b). The attenuation is especially prominent in our case, as our chemistry focuses on high-density near midplane regions. (cite: Cleeves2015) have previously inferred a very low CRI ($10^{-19}$ s$^{-1}$) in the protoplanetary disk TW Hya, which they suggest is due to an exclusion by a young stellar wind. Our current astrochemical model only includes a constant CR ionization rate across the disk. The inclusion of short-lived radionuclides (cite: Cleeves2013) and vertical distribution of CRI rates (cite: Padovani2018) may provide a better picture.

#### C/O ratio

We have also modelled abundances of our targeted molecules for different elemental C/O ratios from 0.5 to 1.2 by changing initial O abundances, as shown in Figure [8](#fig:comp_co). Changing the C/O ratios from 0.5 to 1.0 has decreased the surface density by a factor of approximately 2.5, while the surface density increases by at most a factor of 1-2. However, when the C/O ratio was further increased to 1.2, changes in the surface densities of and became significant (by a factor of approximately 10). surface density remains unaffected for any change in C/O ratio from 0.5 to 1.2. The chemistry of and , for which we obtained the upper limit from our observations, is quite sensitive to changes in the C/O ratio. The general trend is that O-poor chemistry favours the formation of the C-S bond, and for , it is the other way around (cite: Semenov+2018; LeGal2021). Our observations are best represented by a CRI rate of $10^{-18}$ s$^{-1}$ and an elemental C/O ratio of 1.0. At the commencement of the evolution of a molecular cloud, a significant amount of important elements, including carbon (C) and oxygen (O), exist in a refractory state, which is expected to shape the chemical budget of the protoplanetary disk formed from that cloud. Based on (cite: Boogert2015)’s observation on ice abundances, (cite: Oberg2021) reports that about 40% O chemical budget was unaccounted for at the onset of star and planet formation, leading to a poor constraint on initial C and O gas phase abundances. Our elemental C/O ratio of 1.0 suggests an oxygen-depleted environment in the dense ring. Similar inferences of high C/O ratios ($0.9-2.0$) were also found in more typical protoplanetary disks (cite: Ruaud2022; LeGal2021), which may have consequences on the formation of planets in the inner regions.

#### Spatial Distributions

Figure [6](#fig:modelled_abundances) represents the molecular number density distribution for our best model. We see a distribution in those regions where CO is available in the gas phase in small amounts. Observationally, follows a ring-like emission distribution in the ring region (refer to Figures [2](#fig:radial_intensity) and [14](#fig:kepler-n2h)). In our modelled abundances, is primarily peaking up in temperature regions representative of the warm molecular layer (2.5- 3.5H$_r$), somewhat showcasing the ring-like distribution. One of the dominant ions in the warm molecular layer is . It essentially forms through the protonation of and, in turn, produces DCO$^+$ through isotope exchange. The major reaction for DCO$^+$ production contributing to our observation above 2.5H$_r$ is . We also see some arising below the warm molecular layer ($\sim 0.5 - 2.5$ H$_r$) produced through a different channel, . Our DISKFIT analysis locates the peak of the ring at radial distance $210 \pm 50$ au (R$_1$ in Table [\[tab:diskfitabun\]](#tab:diskfitabun)), and this can be attributed to the fact that both the formation channels are contributing to abundances in this radial range. Near the disk midplane, starts depleting because its parent molecule, , efficiently freezes onto the grain surfaces owing to high density and low temperature.

modelled distribution lies just below the layer, with its number density peaking up in the regions where starts depleting. Our observationally constrained representative temperatures of 16 K and 12 K for and emitting regions, respectively (Table [\[tab:diskfitabun\]](#tab:diskfitabun)), suggest the same. N$_2$H$^+$ is abundant in the midplane at the inner edge of the ring as well as in the warm molecular layer (up to 3.0H$_r$) at the outer edge of the ring. All throughout the ring region, the major formation pathway of N$_2$H$^+$ is the protonation of , i.e., . So, the chemistry is mainly controlled by gas phase abundances of , , and . As long as remains in the gas phase, it destroys to form . When CO starts depleting, start increasing, as is still in the gas phase owing to its lower binding energy with respect to CO, forming and there is less destruction of because of the reduced CO presence. Our model predicts a decreasing surface density with increasing radius, contrary to the observed increase within the continuum ring. This discrepancy arises primarily from the model’s overestimation of depletion from the gas phase. A similar trend was observed in the protoplanetary disk around DM Tau, where (cite: Wakelam2019) conducted sensitivity analyses on various model parameters. One limitation of our model is the absence of a grain growth mechanism and the assumption that grains are perfectly spherical. (cite: Kataoka2013) proposed a dust growth mechanism in protoplanetary disks, which would create inhomogeneities in the dust distribution and potentially allow more UV penetration towards the disk’s mid-plane. UV penetration, in turn, facilitates photo-desorption of . Chemically, non-spherical grains would have a larger cross-sectional area for collisions with gas-phase species and a larger surface area, increasing the likelihood of desorption. Additionally, our models do not include X-ray chemistry, which could also affect the abundance of (cite: Teague2015; Cleeves2015).

Our astrochemical model suggests that is abundant in the midplane region, situated just below the layer. The major formation pathway predicted by our model is . As begins to freeze onto grain surfaces, more become available for to capture, and we see a rise in abundances and a fall in abundances.

We did not detect . In our effort to replicate the observed surface density for the detected molecules, we realized that a lower cosmic ray ionization rate may provide the best explanation for our observations. abundances are regulated by the availability of , which in turn is dependent on the rate of ionization of . A lower CRI rate results in reduced production (), leading to a lower abundance of (). Hence, a lower ionization rate at the midplane, owing to the very high density in the ring region, may explain the non-detection of o-H$_2$D$^+$ (1(1,0)-1(1,1)). Indeed, our model using a CR rate ($\zeta_{CR}$) of $10^{-18}$ s$^{-1}$ predicts a surface density of the order of $\sim 10^{12}$ cm$^{-2}$ close to the current upper limit reported in Table [\[tab:col_den\]](#tab:col_den). This limit suggests we are close to detection, and increasing the observation time should assure our chance of detection for . However, the upper limit on total is based on the assumption of thermalized ortho-to-para ratio (LTE), with a high correction Boltzmann factor (see Section [3.2](#sec:surfden_results)). While thermalization is facilitated by the very high mid-plane density, spin-dependent reaction rates may lead to a different prediction (cite: Chapillon2011).

## Possible Chemistry in the Outer Disk

N$_2$H$^+$ (4-3) and DCO$^+$ (5-4) emission are also spatially extended beyond the ring, reaching up to a radial distance of approximately 550 au (Figures [1](#fig:mo_maps), [2](#fig:radial_intensity)). The velocity-integrated radial profiles of N$_2$H$^+$ (4-3) and DCO$^+$ (5-4) (Figure [2](#fig:radial_intensity)) indicate that the former is decreasing as we go radially outward in the outer disk, while the latter shows another peak at around $\sim$ 375 au.

We have not modelled the outer disk due to its complex structure (cite: Tang2016; Phuong2020). However, based on our current understanding, the outer disk is characterized by lower density and colder temperatures as compared to the ring (refer to Section [4.1](#subsec:phy_model)). Lower densities outside the dense ring allow higher CR penetration, leading to non-thermal desorption of CO and . Consequently, an increased presence of CO and in the gas phase is anticipated in the outer disk, suggesting that the primary pathway for DCO$^+$ production would be through (cite: Phuong2018). On the other hand, formed through protonation of will be readily destroyed in the presence of , which will cause a rapid decrease in the abundances as seen in Figure [2](#fig:radial_intensity).

## Temperature Trends in the Ring Region

The DISKFIT analysis of our observations of N$_2$H$^+$ (4-3) and DCO$^+$ (5-4) along with NOEMA observations N$_2$H$^+$ (1-0) and DCO$^+$ (1-0, 3-2) by (cite: Phuong2021; Phuong2018) indicate that N$_2$H$^+$ and DCO$^+$ are best represented by average temperatures of 12 K and 16 K (Table [\[tab:diskfitabun\]](#tab:diskfitabun)) respectively. These rotation temperatures are consistent with N$_2$H$^+$ being located closer to the cold disk mid-plane than DCO$^+$ and a fortiori, CO and its isotopologues previously studied by (cite: Phuong2020).

However, in our chemical model, while the distribution of and extends to regions with temperatures of 12 and 16 K, their density-weighted average temperatures are 21 K and 24 K, respectively. The discrepancy with observed temperatures can be attributed to our limited understanding of the physical structure of the ring region and the simplifications applied in the model to derive the physical structure. DCO$^+$ abundances are sensitive to grain size, and the dust-to-gas mass ratio significantly influences gas-phase molecular abundances. (cite: Gavino2021; Gavino2023) recently investigated the impact of the dependence of the grain size on their temperature. They found that large grains exhibit lower temperatures than smaller ones, with an effect on chemistry that cannot be properly represented by a single grain size. This can influence the structure of the CO distribution (with more CO near the mid-plane) and, consequently, the gas-phase abundances of DCO$^+$ and N$_2$H$^+$ in the densest, coldest regions.

# Conclusions

In this paper, we have presented high-sensitivity ALMA band 7 observations of the circumstellar disk around the triple star system GG Tau A that highlights CO-regulated cold molecular chemistry in the shielded high-density regions near the disk midplane. Our key findings and conclusions are summarized below:

1.  With band 7 single-pointing observation of GG Tau A, we achieved a spectral resolution of 0.1 km/s and an angular resolution of 0.8-0.9$''$. We spatially resolved the emission from N$_2$H$^+$ (4-3) and DCO$^+$ (5-4)  while o-H$_2$D$^+$ (1(1,0)-1(1,1)), $^{13}$CS (8-7), and SO$_2$ 19(4,16)-19(3,17) show no detection.

2.  Comparing the predictions of a parametric disk model to our observed visibilities along with the lower excitation transition observations obtained with NOEMA by (cite: Phuong2018) and (cite: Phuong2020), we constrain the average temperature of and emitting regions to be around 12 K and 16 K respectively. This is at odds with the predictions from all the chemical models we explored and all the previous studies. Chemical models suggest peaks at 20-25 K, where some remains in the gas phase, and peaks around 20 K, where is fully frozen onto grains. On the contrary, our observational constraints indicate that both molecules trace regions below the CO layer (cite: Phuong2020a), much closer to the midplane than previously thought, with being the closest.

3.  Our radial distribution of DCO$^+$ (5-4) emission reveals an atypical partially overlapping double ring structure. The inner ring peaks at $210 \pm 50$ au within the continuum ring region, while the more intense outer ring peaks at $375 \pm 10$ au in the outer disk. We hypothesize that forms via two different pathways in the ring and the outer disk regions depending on gas-phase CO abundance. In the ring region, forms through isotope exchange after arises from protonation. However, constraining formation in the outer disk regions requires future work that takes into account the complex physical structure.

4.  N$_2$H$^+$ (4-3) emission shows a ring-like radial distribution facilitated through protonation of with its emission layer situated right below the layer. The anti-correlation between distribution with distribution is clearly visible in our modelled simulation.

5.  We ran numerous chemical models varying CRI rates, C/O ratios, and stellar UV fluxes. These models suggest that the chemistry of , , and in cold, dense regions is primarily influenced by gas-phase abundance and the dominant midplane ion, . These regions are shielded from external UV radiation, making CRI the most crucial factor in determining and abundances and, consequently, the distribution of , , and . On the other hand, the chemistry of and is very sensitive to the C/O ratio.

6.  After running a grid of astrochemical models to simultaneously fit the surface density constraints from the observed transitions along with the upper limits provided by the non-detections, our best-fit model, with a carbon-to-oxygen ratio of 1.0 and a sub-interstellar cosmic ray ionization rate of $10^{-18}$ s$^{-1}$, successfully reproduced the radial trends in surface density for but slightly overestimated both the content and the expected rotation temperatures. The CRI attenuation in the high-density GG Tau A ring can be attributed to an increased number of collisions experienced by CR particles as they gyrate towards the midplane.

7.  The non-detection of o-H$_2$D$^+$ (1(1,0)-1(1,1)) suggests that ionization is much lower than the standard interstellar rate in the disk-midplane due to its very high density. In the cold midplane region, is directly dependent on the abundance of , which, in turn, is regulated by the ionization rate. The non-detection of aligns with our best model, where the expected surface density is below our observationally determined 3$\sigma$ upper limit only for a sub-interstellar CRI rate.

The GG Tau A disk is very complex, but it is one of the nearest (hence larger) and more massive disks found around a low-mass star system. Such properties should facilitate the detection of o-H$_2$D$^+$ (1(1,0)-1(1,1)). However, its modelled surface density being close to the observationally constrained 3$\sigma$ upper limit, suggests that the detection of is within the ALMA capabilities, although at the cost of a significantly longer integration time.

# Acknowledgments

This paper makes use of the following ALMA data: ADS/JAO ALMA$\#$2021.1.00342.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under a cooperative agreement by Associated Universities, Inc. L.M. acknowledges the financial support from DAE and DST-SERB research grants (SRG/2021/002116 and MTR/2021/000864) of the Government of India. L.M. also acknowledges insightful discussions related to this project with Valentine Wakelam and Uma Gorti. A.D. and S.G. thank the French CNRS programs PNP, PNPS, and PCMI. This research was carried out in part at the Jet Propulsion Laboratory, which is operated for NASA by the California Institute of Technology. K.W. acknowledges the financial support from the NASA Emerging Worlds grant 18-EW-182-0083. Th.H. and D.S. acknowledge support from the European Research Council under the Horizon 2020 Framework Program via the ERC Advanced Grant Origins 83 24 28 (PI: Th. Henning). R.S. thanks NASA for financial support through various Astrophysics Data Program awards. N.T.P. acknowledges the financial support of Vingroup Innovation Foundation (VINIF) under project code VINIF.2023.DA.057$''$. A.C. received financial support from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (ERC Starting Grant “Chemtrip”, grant agreement No 949278). This work was also supported by the NKFIH excellence grant TKP2021-NKTA-64. We would like to thank the anonymous referees for their constructive comments, which helped improve the manuscript.

ALMA

# Software

`CASA` (cite: casa), `keplerian_mask` (cite: kepmask), `GoFish` (cite: GoFish), `VISIBLE` (cite: loomis2018visible), `dynesty` (cite: speagle2020dynesty), IMAGER (<https://imager.oasu.u-bordeaux.fr>), `DNAUTILUS` (cite: Majumdar2017), `numpy` (cite: numpy), astropy (cite: astropy:2013; astropy:2018; astropy:2022), `matplotlib` (cite: matplotlib)

# Channel Maps, Moment Maps and Radial Profiles

The generated channel maps for the detected transition, N$_2$H$^+$ (4-3) and DCO$^+$ (5-4) are shown in Figures [9](#fig:ch_maps_n2hp) and [10](#fig:ch_maps_dcop), respectively. Figure [11](#fig:m0_without_kepmask) shows integrated intensity maps between the velocity range 5.0 km/s and 8.0 km/s for all the targeted transitions. Sigma clipping and masking are not performed while generating these integrated intensity maps. Figure [12](#fig:rad_profile_wihtout_kep) shows the radial distribution of azimuthally averaged emission for the targeted transitions and the continuum generated from integrated intensity maps shown in Figure [11](#fig:m0_without_kepmask). We have displayed the matched filter responses for all the targeted transitions in Figure [13](#fig:matched_filter). The methods for generating all these figures are explained in Section [2.2](#subsec:obs_res).

![](channel_maps_65_n2hp.pdf)

![](channel_maps_65_dcop.pdf)

![](M0_maps_23.pdf)

![](Integrated_intensity_radial_without_kep.pdf)

![](filter_response.pdf)

# IMAGER and DiskFit analyis

Figure [14](#fig:kepler-n2h) shows the Keplerian deprojection produced by the IMAGER command `KEPLER`. Images used for this purpose were produced with IMAGER and have an angular resolution of $0.66 \times 0.53''$ at PA $83^\circ$. Spectral resolution prior to Keplerian velocity correction was about 0.1 km s$^{-1}$. This correction requires resampling of the spectra on a different grid, which results in correlated channels: the correlation factor is estimated from the **noise autocorrelation spectrum**. The best fit radial profile derived from DISKFIT is always slightly above the measured one because the deconvolution with limited signal to noise cannot recover the full line brightness, while the $uv$ plane fitting method is not biased in this respect.

![image](kep-n2h+43.pdf)\
![image](kep-dco+54.pdf)

# Simple LTE Approach

We have undertaken a simpler approach to calculate disk-averaged surface densities where we assume local thermodynamic equilibrium (LTE) considering the disk densities are relatively high compared to critical densities for the studied transitions. This method requires prior knowledge of rotational temperature for a single transition.

For optically thin emission, the surface density of molecules in the upper state of a specific transition is expressed as, $$\begin{align}
N_u^{thin} &= 
\frac{4\pi}{ h c A_{ul}} \frac{(\int S_\nu dv)}{\Omega} \\ 
&= 
\frac{8\pi k \nu^2 }{ h c^3 {A_{ul}}  } \left(\int T_b dv\right)
\end{align}$$ where $\int S_\nu dv$ is the velocity integrated flux density, $A_{ul}$ is the Einstein coefficient, $\Omega$ denotes the solid angle subtended by the emission area, and *h* and *c* stand for the Planck constant and the speed of light in a vacuum, respectively (cite: goldsmith1999population). In the alternate form, $\nu$ is the line frequency and $T_b$ the line brightness temperature.

The total surface density can be derived from the upper state surface density, assuming a Boltzmann distribution $$\begin{align}
    N_T^{thin} = N_u^{thin}  \frac{Q(T_{rot})}{g_u} exp \left(\frac{E_u}{T_{rot}}\right) \label{eq:Nt_thin}
\end{align}$$ where $g_u$ is the degeneracy, $E_u$ is the energy of the upper energy level in K, and *Q($T_{rot}$)* is the partition function at the rotation temperature $T_{rot}$, that can be computed by summation over the energy levels or by interpolating tabulated $Q$ values for discrete $T_{rot}$ values found in the Cologne Database for Molecular Spectroscopy (CDMS) (cite: endres2016cologne).

If the transition is optically thick, the above value gives a strict lower limit to the observed surface density. Opacity corrections are possible in a purely homogeneous medium with only turbulent or thermal line broadening (cite: goldsmith1999population): $$\begin{align}
    N_T = N_T^{thin} \frac{\tau}{1- e^{-\tau}} \label{eq:tau_correction}
\end{align}$$

where we can self-consistently calculate the optical depth, $\tau$ assuming a Gaussian-like line profile $\sim 1/\Delta v$ at the line center (cite: goldsmith1999population), $\Delta v$ = 0.25 km/s being the intrinsic full-width half maximum line width constrained from DISKFIT analysis: $$\begin{align}
\tau  = \frac{A_{ul}c^3}{8\pi \nu^3 \Delta v} N_u
    \left[ \exp\left(\frac{h \nu}{k T_{rot}} \right) - 1 \right]
    \label{eq:tau}
\end{align}$$

Unfortunately, in our case, the above-mentioned correction does not hold while calculating the radially resolved surface density, even if we apply this to radially dependent emission. Because of the Keplerian shear, there are significant regions in our images where the line of sight opacity varies both as a function of azimuth and radius, with both directions being insufficiently well resolved at our angular resolution (about 100 au). Accordingly, the azimuthally averaged brightness does not originate from a unique opacity below about 400 au.

However, the effect is expected to be small. The peak brightness of N$_2$H$^+$ (see Figure [14](#fig:kepler-n2h)) is 2 K, while the brightness temperature of an optically thick line would be $J_\nu(T_{rot}) = 5.3$ K for $T_{rot} = 12$ K at the J=4-3 line frequency. This indicates a peak line opacity of about 0.47, leading to a $\sim 22$% opacity correction at most. For DCO$^+$, whose emission is about 3 times fainter, the correction is even smaller, as for the (undetected) emission from H$_2$D$^+$ and other molecules. We thus expect the constraint given by the optically thin approximation to be a reasonable estimate for the mean surface density.

We explore the likely ranges of disk-averaged surface density using nested sampling while assuming log-normal priors for both the molecules in the range $10^5 <$ N$_{\text{T}} < 10^{18}$ cm$^{-2}$ and fixing the rotational temperature to the values constrained in DISKFIT analysis. The rotation temperatures for N$_2$H$^+$ and DCO$^+$ were set at 12 K and 16 K, respectively. A value of 15 K was used for the undetected molecules. The Python package utilized to sample the posterior distribution is `dynesty` (cite: speagle2020dynesty). We consider the median of the posterior as the best-fit value, while the 16th and 84th percentile values account for the $1 \sigma$ uncertainties. Posterior distributions for these averaged surface density derivations are shown in Figure [15](#fig:posterior).

![](posterior.pdf)

# Grids of Astrochemical Models and Finding the Best-Fit Model

We ran a large number of astrochemical models with various combinations of parameters. The grids of models are summarized in Table [\[tab:dnautilus_parameters\]](#tab:dnautilus_parameters). Note that we have not implemented any grain growth in our models due to poor constraints on larger grain size. We explored the parameter space using the least square method while simultaneously considering the observational constraints on surface densities for and from our observations and $^{13}$CS as reported by Phuong et al. (2021). We ensured that the modelled values for undetected molecules remained below their respective upper limits. To quantify the goodness of fit, we calculated reduced chi-square values. This metric evaluates the agreement between observed and modelled surface densities across multiple molecules and radii. The reduced chi-square calculation is defined as follows: $$\begin{align}
    \chi^2_{\text{red}} = \frac{1}{\nu} \sum_{j} \left( \sum_{i} \left( \frac{N_{\text{obs}}(i, j) - N_{\text{model}}(i, j)}{\sigma_{\text{obs}}(i, j) + \sigma_{\text{model}}(i, j)} \right)^2 \right)
\end{align}$$

In the equation, $\nu$, the number of degrees of freedom is 25. $N_{\text{obs}}(i, j)$ and $N_{\text{model}}(i, j)$ denote the observed and modelled surface densities of the j-th molecule at the i-th radial point, respectively. The terms $\sigma_{\text{obs}} (i,j)$ and $\sigma_{\text{model}} (i,j)$ represent the associated error estimates for the observed and modelled values, respectively. Observational errors were derived from the error bars in the peak column density values in Table [\[tab:diskfitabun\]](#tab:diskfitabun), while modelled errors were assumed to be 20% to account for uncertainties in the chemical models due to rate coefficients and other chemical parameters. The best-fit model is the one with the lowest $\chi^2_{\text{red}}$ value. Although the $\chi^2_{\text{red}}$ depends on the assumed errors, the best-fit solution was found to be independent of this assumption.

| Initial Abundances | Settling | Grain Growth | $f_{\text{UV, 214 \text{ au}}}^a$ ($\chi_0$) | C/O$^b$ | $\zeta_{\text{CR}}^c$ (s$^{-1}$) |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Atomic$^d$ | no | no | 375, 1500, 3000 | 0.5, 0.7, 0.9, 1.0, 1.2 | $10^{-16}$, $10^{-17}$, $10^{-18}$, $10^{-19}$, $10^{-20}$ |
| $10^6$ yr Molecular Cloud$^e$ | no | no | 375, 1500, 3000 | 0.5, 0.7, 0.9, 1.0, 1.2 | $10^{-16}$, $10^{-17}$, $10^{-18}$, $10^{-19}$, $10^{-20}$ |
| Atomic$^d$ | yes | no | 375, 1500, 3000 | 0.5, 0.7, 0.9, 1.0, 1.2 | $10^{-16}$, $10^{-17}$, $10^{-18}$, $10^{-19}$, $10^{-20}$ |
| $10^6$ yr Molecular Cloud$^e$ | yes | no | 375, 1500, 3000 | 0.5, 0.7, 0.9, 1.0, 1.2 | $10^{-16}$, $10^{-17}$, $10^{-18}$, $10^{-19}$, $10^{-20}$ |

: Parameter Space Explored with

Table notes: a) $f_{UV}$ is the stellar UV flux at reference radius, 214 au in the units of Draine interstellar UV field, $\chi_0$ b) Carbon to Oxygen (C/O) ratios have been considered around the standard value of 0.7 to account for “low depletion" and “high depletion" of oxygen (cite: Reboussin2015). c) Different cosmic ray ionization rates $\zeta_{\text{CR}}$ have been explored to account for how they impact our chemistry. d) In the reset scenario, we have taken our initial abundances in atomic forms along with and and run our astrochemical model for $10^6$ years. e) We have also considered the inheritance scenario as another possibility, where we have run a cloud model with atomic initial abundances, and the final abundances after $10^6$ years are used as initial abundance in the disk model. The disk model was then run for $10^6$ years.

natexlab

(ref: Aikawa2002) Aikawa, Y., van Zadelhoff, G. J., van Dishoeck, E. F., & Herbst, E. 2002, A&A, 386, 622, doi: [`10.1051/0004-6361:20020037`](http://doi.org/10.1051/0004-6361:20020037)

(ref: Anderson2022) Anderson, D. E., Cleeves, L. I., Blake, G. A., et al. 2022, ApJ, 927, 229, doi: [`10.3847/1538-4357/ac517e`](http://doi.org/10.3847/1538-4357/ac517e)

(ref: Andrews2014) Andrews, S. M., Chandler, C. J., Isella, A., et al. 2014, ApJ, 787, 148, doi: [`10.1088/0004-637X/787/2/148`](http://doi.org/10.1088/0004-637X/787/2/148)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: astropy:2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Bergin2002) Bergin, E. A., Alves, J., Huard, T., & Lada, C. J. 2002, ApJL, 570, L101, doi: [`10.1086/340950`](http://doi.org/10.1086/340950)

(ref: Boogert2015) Boogert, A. C. A., Gerakines, P. A., & Whittet, D. C. B. 2015, ARA&A, 53, 541, doi: [`10.1146/annurev-astro-082214-122348`](http://doi.org/10.1146/annurev-astro-082214-122348)

(ref: Brauer2019) Brauer, R., Pantin, E., Di Folco, E., et al. 2019, A&A, 628, A88, doi: [`10.1051/0004-6361/201935966`](http://doi.org/10.1051/0004-6361/201935966)

(ref: Caselli2008) Caselli, P., Vastel, C., Ceccarelli, C., et al. 2008, A&A, 492, 703, doi: [`10.1051/0004-6361:20079009`](http://doi.org/10.1051/0004-6361:20079009)

(ref: Caselli1999) Caselli, P., Walmsley, C. M., Tafalla, M., Dore, L., & Myers, P. C. 1999, ApJL, 523, L165, doi: [`10.1086/312280`](http://doi.org/10.1086/312280)

(ref: MAPSX) Cataldi, G., Yamato, Y., Aikawa, Y., et al. 2021, ApJS, 257, 10, doi: [`10.3847/1538-4365/ac143d`](http://doi.org/10.3847/1538-4365/ac143d)

(ref: Ceccarelli2014) Ceccarelli, C., Caselli, P., Bockelée-Morvan, D., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 859–882, doi: [`10.2458/azu_uapress_9780816531240-ch037`](http://doi.org/10.2458/azu_uapress_9780816531240-ch037)

(ref: Ceccarelli2004) Ceccarelli, C., Dominik, C., Lefloch, B., Caselli, P., & Caux, E. 2004, ApJL, 607, L51, doi: [`10.1086/421461`](http://doi.org/10.1086/421461)

(ref: Chapillon2011) Chapillon, E., Parise, B., Guilloteau, S., & Du, F. 2011, A&A, 533, A143, doi: [`10.1051/0004-6361/201117354`](http://doi.org/10.1051/0004-6361/201117354)

(ref: Cleeves2013) Cleeves, L. I., Adams, F. C., & Bergin, E. A. 2013, ApJ, 772, 5, doi: [`10.1088/0004-637X/772/1/5`](http://doi.org/10.1088/0004-637X/772/1/5)

(ref: Cleeves2015) Cleeves, L. I., Bergin, E. A., Qi, C., Adams, F. C., & Öberg, K. I. 2015, ApJ, 799, 204, doi: [`10.1088/0004-637X/799/2/204`](http://doi.org/10.1088/0004-637X/799/2/204)

(ref: Dartois2003) Dartois, E., Dutrey, A., & Guilloteau, S. 2003, A&A, 399, 773, doi: [`10.1051/0004-6361:20021638`](http://doi.org/10.1051/0004-6361:20021638)

(ref: Drain1978) Draine, B. T. 1978, ApJS, 36, 595, doi: [`10.1086/190513`](http://doi.org/10.1086/190513)

(ref: Drozdovskaya2016) Drozdovskaya, M. N., Walsh, C., van Dishoeck, E. F., et al. 2016, MNRAS, 462, 977, doi: [`10.1093/mnras/stw1632`](http://doi.org/10.1093/mnras/stw1632)

(ref: Du2014) Du, F., & Bergin, E. A. 2014, ApJ, 792, 2, doi: [`10.1088/0004-637X/792/1/2`](http://doi.org/10.1088/0004-637X/792/1/2)

(ref: Dutrey2007) Dutrey, A., Henning, T., Guilloteau, S., et al. 2007, A&A, 464, 615, doi: [`10.1051/0004-6361:20065385`](http://doi.org/10.1051/0004-6361:20065385)

(ref: Dutrey2014) Dutrey, A., di Folco, E., Guilloteau, S., et al. 2014, Nature, 514, 600, doi: [`10.1038/nature13822`](http://doi.org/10.1038/nature13822)

(ref: endres2016cologne) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. 2016, Journal of Molecular Spectroscopy, 327, 95

(ref: Gaia2016) Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1, doi: [`10.1051/0004-6361/201629272`](http://doi.org/10.1051/0004-6361/201629272)

(ref: Gaia2018) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1, doi: [`10.1051/0004-6361/201833051`](http://doi.org/10.1051/0004-6361/201833051)

(ref: Gammie1996) Gammie, C. F. 1996, ApJ, 457, 355, doi: [`10.1086/176735`](http://doi.org/10.1086/176735)

(ref: Gavino2023) Gavino, S., Kobus, J., Dutrey, A., et al. 2023, A&A, 680, A59, doi: [`10.1051/0004-6361/202346767`](http://doi.org/10.1051/0004-6361/202346767)

(ref: Gavino2021) Gavino, S., Dutrey, A., Wakelam, V., et al. 2021, A&A, 654, A65, doi: [`10.1051/0004-6361/202038788`](http://doi.org/10.1051/0004-6361/202038788)

(ref: goldsmith1999population) Goldsmith, P. F., & Langer, W. D. 1999, The Astrophysical Journal, 517, 209

(ref: Graedel1982) Graedel, T. E., Langer, W. D., & Frerking, M. A. 1982, ApJS, 48, 321, doi: [`10.1086/190780`](http://doi.org/10.1086/190780)

(ref: Guilloteau1999) Guilloteau, S., Dutrey, A., & Simon, M. 1999, A&A, 348, 570

(ref: numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Huang2017) Huang, J., Öberg, K. I., Qi, C., et al. 2017, ApJ, 835, 231, doi: [`10.3847/1538-4357/835/2/231`](http://doi.org/10.3847/1538-4357/835/2/231)

(ref: matplotlib) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Jenkins2009) Jenkins, E. B. 2009, ApJ, 700, 1299, doi: [`10.1088/0004-637X/700/2/1299`](http://doi.org/10.1088/0004-637X/700/2/1299)

(ref: Kataoka2013) Kataoka, A., Tanaka, H., Okuzumi, S., & Wada, K. 2013, A&A, 554, A4, doi: [`10.1051/0004-6361/201321325`](http://doi.org/10.1051/0004-6361/201321325)

(ref: LeGal2021) Le Gal, R., Öberg, K. I., Teague, R., et al. 2021, ApJS, 257, 12, doi: [`10.3847/1538-4365/ac2583`](http://doi.org/10.3847/1538-4365/ac2583)

(ref: loomis2018detecting) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2018a, The Astronomical Journal, 155, 182

(ref: loomis2018visible) Loomis, R. A., Oberg, K. I., Andrews, S. M., et al. 2018b, Astrophysics Source Code Library, ascl

(ref: Lynden1974) Lynden-Bell, D., & Pringle, J. E. 1974, MNRAS, 168, 603, doi: [`10.1093/mnras/168.3.603`](http://doi.org/10.1093/mnras/168.3.603)

(ref: Majumdar2017) Majumdar, L., Gratier, P., Ruaud, M., et al. 2017, MNRAS, 466, 4470, doi: [`10.1093/mnras/stw3360`](http://doi.org/10.1093/mnras/stw3360)

(ref: Mathews2013) Mathews, G. S., Klaassen, P. D., Juhász, A., et al. 2013, A&A, 557, A132, doi: [`10.1051/0004-6361/201321600`](http://doi.org/10.1051/0004-6361/201321600)

(ref: casa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Neufeld2005) Neufeld, D. A., Wolfire, M. G., & Schilke, P. 2005, ApJ, 628, 260, doi: [`10.1086/430663`](http://doi.org/10.1086/430663)

(ref: Oberg2021) Öberg, K. I., & Bergin, E. A. 2021, Phys. Rep., 893, 1, doi: [`10.1016/j.physrep.2020.09.004`](http://doi.org/10.1016/j.physrep.2020.09.004)

(ref: Oberg2015a) Öberg, K. I., Furuya, K., Loomis, R., et al. 2015, ApJ, 810, 112, doi: [`10.1088/0004-637X/810/2/112`](http://doi.org/10.1088/0004-637X/810/2/112)

(ref: Oberg2011) Öberg, K. I., Qi, C., Wilner, D. J., & Andrews, S. M. 2011, ApJ, 743, 152, doi: [`10.1088/0004-637X/743/2/152`](http://doi.org/10.1088/0004-637X/743/2/152)

(ref: Oberg2005) Öberg, K. I., van Broekhuizen, F., Fraser, H. J., et al. 2005, ApJL, 621, L33, doi: [`10.1086/428901`](http://doi.org/10.1086/428901)

(ref: Okuzumi2012) Okuzumi, S., Tanaka, H., Kobayashi, H., & Wada, K. 2012, ApJ, 752, 106, doi: [`10.1088/0004-637X/752/2/106`](http://doi.org/10.1088/0004-637X/752/2/106)

(ref: Padovani2013b) Padovani, M., Hennebelle, P., & Galli, D. 2013, A&A, 560, A114, doi: [`10.1051/0004-6361/201322407`](http://doi.org/10.1051/0004-6361/201322407)

(ref: Padovani2018) Padovani, M., Ivlev, A. V., Galli, D., & Caselli, P. 2018, A&A, 614, A111, doi: [`10.1051/0004-6361/201732202`](http://doi.org/10.1051/0004-6361/201732202)

(ref: Phuong2018) Phuong, N. T., Chapillon, E., Majumdar, L., et al. 2018, A&A, 616, L5, doi: [`10.1051/0004-6361/201833766`](http://doi.org/10.1051/0004-6361/201833766)

(ref: Phuong2020a) Phuong, N. T., Dutrey, A., Di Folco, E., et al. 2020a, A&A, 635, L9, doi: [`10.1051/0004-6361/202037682`](http://doi.org/10.1051/0004-6361/202037682)

(ref: Phuong2020) Phuong, N. T., Dutrey, A., Diep, P. N., et al. 2020b, A&A, 635, A12, doi: [`10.1051/0004-6361/201936173`](http://doi.org/10.1051/0004-6361/201936173)

(ref: Phuong2021) Phuong, N. T., Dutrey, A., Chapillon, E., et al. 2021, A&A, 653, L5, doi: [`10.1051/0004-6361/202141881`](http://doi.org/10.1051/0004-6361/202141881)

(ref: Pietu2007) Piétu, V., Dutrey, A., & Guilloteau, S. 2007, A&A, 467, 163, doi: [`10.1051/0004-6361:20066537`](http://doi.org/10.1051/0004-6361:20066537)

(ref: Qi2008) Qi, C., Wilner, D. J., Aikawa, Y., Blake, G. A., & Hogerheijde, M. R. 2008, ApJ, 681, 1396, doi: [`10.1086/588516`](http://doi.org/10.1086/588516)

(ref: Qi2013) Qi, C., Öberg, K. I., Wilner, D. J., et al. 2013, Science, 341, 630, doi: [`10.1126/science.1239560`](http://doi.org/10.1126/science.1239560)

(ref: Reboussin2015) Reboussin, L., Wakelam, V., Guilloteau, S., Hersant, F., & Dutrey, A. 2015, A&A, 579, A82, doi: [`10.1051/0004-6361/201525885`](http://doi.org/10.1051/0004-6361/201525885)

(ref: Robert2000) Roberts, H., & Millar, T. J. 2000, A&A, 361, 388

(ref: Ruaud2022) Ruaud, M., Gorti, U., & Hollenbach, D. J. 2022, ApJ, 925, 49, doi: [`10.3847/1538-4357/ac3826`](http://doi.org/10.3847/1538-4357/ac3826)

(ref: Semenov+2018) Semenov, D., Favre, C., Fedele, D., et al. 2018, A&A, 617, A28, doi: [`10.1051/0004-6361/201832980`](http://doi.org/10.1051/0004-6361/201832980)

(ref: Sipila2017) Sipilä, O., Harju, J., & Caselli, P. 2017, A&A, 607, A26, doi: [`10.1051/0004-6361/201731039`](http://doi.org/10.1051/0004-6361/201731039)

(ref: speagle2020dynesty) Speagle, J. S. 2020, Monthly Notices of the Royal Astronomical Society, 493, 3132

(ref: Tang2016) Tang, Y.-W., Dutrey, A., Guilloteau, S., et al. 2016, ApJ, 820, 19, doi: [`10.3847/0004-637X/820/1/19`](http://doi.org/10.3847/0004-637X/820/1/19)

(ref: Kotomi2024) Taniguchi, K., Rayalacheruvu, P., Yonetsu, T., et al. 2024, arXiv e-prints, arXiv:2401.06297, doi: [`10.48550/arXiv.2401.06297`](http://doi.org/10.48550/arXiv.2401.06297)

(ref: GoFish) Teague, R. 2019, The Journal of Open Source Software, 4, 1632, doi: [`10.21105/joss.01632`](http://doi.org/10.21105/joss.01632)

(ref: kepmask) —. 2020, richteague/keplerian_mask: Initial Release, Zenodo, doi: [`10.5281/ZENODO.4321137`](http://doi.org/10.5281/ZENODO.4321137)

(ref: 2018RNAAS...2c.173T) Teague, R., & Foreman-Mackey, D. 2018, Research Notes of the American Astronomical Society, 2, 173, doi: [`10.3847/2515-5172/aae265`](http://doi.org/10.3847/2515-5172/aae265)

(ref: Teague2015) Teague, R., Semenov, D., Guilloteau, S., et al. 2015, A&A, 574, A137, doi: [`10.1051/0004-6361/201425268`](http://doi.org/10.1051/0004-6361/201425268)

(ref: Thi2004) Thi, W. F., van Zadelhoff, G. J., & van Dishoeck, E. F. 2004, A&A, 425, 955, doi: [`10.1051/0004-6361:200400026`](http://doi.org/10.1051/0004-6361:200400026)

(ref: Wagenblast1989) Wagenblast, R., & Hartquist, T. W. 1989, Monthly Notices of the Royal Astronomical Society, 237, 1019, doi: [`10.1093/mnras/237.4.1019`](http://doi.org/10.1093/mnras/237.4.1019)

(ref: Wakelam2019) Wakelam, V., Chapillon, E., Dutrey, A., et al. 2019, MNRAS, 484, 1563, doi: [`10.1093/mnras/stz068`](http://doi.org/10.1093/mnras/stz068)

(ref: Wakelam2008) Wakelam, V., & Herbst, E. 2008, ApJ, 680, 371, doi: [`10.1086/587734`](http://doi.org/10.1086/587734)

(ref: Wakelam2016) Wakelam, V., Ruaud, M., Hersant, F., et al. 2016, A&A, 594, A35, doi: [`10.1051/0004-6361/201628748`](http://doi.org/10.1051/0004-6361/201628748)

(ref: Walsh2012) Walsh, C., Nomura, H., Millar, T. J., & Aikawa, Y. 2012, ApJ, 747, 114, doi: [`10.1088/0004-637X/747/2/114`](http://doi.org/10.1088/0004-637X/747/2/114)

(ref: Willacy2007) Willacy, K. 2007, ApJ, 660, 441, doi: [`10.1086/512796`](http://doi.org/10.1086/512796)

(ref: Williams2014) Williams, J. P., & Best, W. M. J. 2014, The Astrophysical Journal, 788, 59. <https://dx.doi.org/10.1088/0004-637X/788/1/59>

(ref: Wootten1987) Wootten, A. 1987, in Symposium-International Astronomical Union, Vol. 120, Cambridge University Press, 311–319

[^1]: <https://github.com/richteague/keplerian_mask>

[^2]: <https://imager.oasu.u-bordeaux.fr>

</paper>

Write the methods card for this paper.