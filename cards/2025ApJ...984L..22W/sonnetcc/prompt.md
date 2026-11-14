# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...984L..22W\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...984L..22W",
 "title": "exoALMA. XVII. Characterizing the Gas Dynamics around Dust Asymmetries",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Wölfer, Lisa",
 "n_authors": 34,
 "arxiv_id": "2504.20023",
 "doi": "10.3847/2041-8213/adc42c",
 "alma_projects_linked_by_archive": [
  "2021.1.01123.L"
 ]
}
```

Paper text:
<paper>
# exoALMA XVII. Characterizing the Gas Dynamics around Dust Asymmetries

## Abstract

The key planet-formation processes in protoplanetary disks remain an active matter of research. One promising mechanism to radially and azimuthally trap millimeter-emitting dust grains, enabling them to concentrate and grow into planetesimals, is anticyclonic vortices. While dust observations have revealed crescent structures in several disks, observations of their kinematic signatures are still lacking. Studying the gas dynamics is, however, essential to confirm the presence of a vortex and understand its dust trapping properties. In this work, we make use of the high-resolution and sensitivity observations conducted by the exoALMA large program to search for such signatures in the $^{12}$CO and $^{13}$CO molecular line emission of four disks with azimuthal dust asymmetries: HD 135344B, HD 143006, HD 34282, and MWC 758. To assess the vortex features, we constructed an analytical vortex model and performed hydrodynamical simulations. For the latter, we assumed two scenarios: a vortex triggered at the edge of a dead zone and of a gap created by a massive embedded planet. These models reveal a complex kinematical morphology of the vortex. When compared to the data, we find that none of the sources show a distinctive vortex signature around the dust crescents in the kinematics.

HD 135344B exhibits a prominent feature similar to the predictions from the simulations, thus making this the most promising target for sensitive follow-up studies at higher resolution and in particular with less abundant molecules at higher resolution and sensitivity, to trace closer to the disk midplane.

# Introduction

In recent years, high resolution and sensitivity observations of the dust and gas material in protoplanetary disks with facilities such as the Atacama Large Millimeter/submillimeter Array (ALMA; (cite: ALMA2015)), the Spectro-Polarimetric High-contrast Exoplanet REsearch (SPHERE; (cite: Sphere2019)), or the Gemini Planet Imager (GPI; (cite: Macintosh2014)) have revealed that various substructures are ubiquitous in disks, and may indicate planet–disk interactions. In the dust, this includes spiral arms, gaps or cavities, rings, and azimuthal asymmetries (e.g., review in (cite: Bae2023)).

The latter two are associated with local pressure maxima, where dust grains can be radially and/or azimuthally trapped and prevented from undergoing processes such as inward drift or fragmentation (e.g., (cite: Birnstiel2010b; Pinilla2012a; Pinilla2012b)).

Dust traps can further enable the streaming instability (cite: Stammler2019), thus allowing dust to grow to larger sizes and form planetesimals (e.g., (cite: Bai2010a; Bai2010b; Raettig2015)).

One possible origin of pressure bumps in disks is embedded planets, which - if massive enough - are capable of opening a gap in the disk and form symmetric dust rings (e.g., (cite: Ayliffe2012; Dipierro2015; Rosotti2016; Dong2017; Dong2018; Dipierro2018)). In low viscosity regions, the edges of such gaps or cavities can then become unstable against the Rossby wave instability (RWI, (cite: Lovelace1999; Li2000)), resulting in the formation of an anticyclonic vortex where dust can be trapped radially and azimuthally, possibly giving rise to the observed crescent-shaped asymmetries (e.g., (cite: Birnstiel2013; Fu2014b; Bae2016)).

Evidence of azimuthal dust trapping has been found in a number of sources with ALMA, seen as a large horseshoe structure (e.g. HD 142527, (cite: Casassus2013); IRS 48, (cite: Marel2013); AB Aur, (cite: Tang2012; Tang2017)), or as a concentration of dust within a dust ring (e.g. HD 135344B, SR 21 (cite: Perez2014); V1247 Ori (cite: Kraus2017); HD 34282 (cite: Plas2017); MWC 758 (cite: Boehler2018); HD 143006, (cite: perez2018)), with high resolution observations revealing more complex substructures in some of these sources (e.g. (cite: Marel2016; Cazzoletti2018; Muro2020; Yang2023)).

Alternatively to dust trapping, azimuthal dust asymmetries may be caused in a circumbinary disk by a sufficiently massive companion carving an eccentric cavity, which results in a gas overdensity at the cavity edge and a horseshoe structure (e.g. (cite: Ragusa2017; Price2018)). (cite: Marel2021) compare several disk observables in a number of asymmetric disks to distinguish between vortices, horseshoes created by binary companions, and spiral density waves, concluding that the current data do not allow for a clear classification. Apparent dust Asymmetries may further arise in inclined sources due to optically thick emission at the hot inner rim of a disk cavity (cite: Ribas2024; Guerra2024).

The edge of a disk cavity or gap favors vortex formation regardless of the underlying process creating the structure, not limited to planets. The RWI can further be triggered by infalling material (cite: Bae2015; Kuznetsova2022) or at the edge of a dead-zone (e.g., (cite: Flock2015; Flock2017a)).

Moreover, there are other instabilities which can lead to the formation of vortices: the vertical shear instability (cite: Richard2016; Flock2020; Manger2020; Pfeil2021), the convective overstability (cite: Lyra2014; Raettig2021), or the zombie vortex instability (e.g., (cite: Marcus2013; Marcus2015; Marcus2016)).

To differentiate the mechanisms and understand the process of dust trapping in vortices it is important to study their gas dynamics.

![](plots/cont_and_scat_and_12CO_v1.png)

The gas in protoplanetary disks is studied through a range of molecular lines, tracing different disk regions and probing various physical and chemical processes. While it is easier to observe substructures in the dust component of the disk due to the higher achieved sensitivity, an increasing number of substructures have also been observed in the gas (e.g. (cite: Bruderer2014; Zhang2014; Marel2016a; Dong2017b; Law2021; Woelfer2023; Teague_exoALMA)). Similar to the dust, this includes spirals, rings, and gaps or cavities. Narrow-band line emission brings the advantage of providing information about the gas dynamics. Studying the velocity field of the rotating gas and identifying deviations from purely Keplerian rotation yields information about the underlying processes which are shaping the rotation pattern (for a review see (cite: Pinte2022)). The different disk processes leave individual fingerprints in the kinematics but it remains difficult to disentangle them. Yet, observations of localized (e.g (cite: Pinte2018; Pinte2019; Pinte2020; Teague2018a; Teague2019a; Casassus2019; Casassus2022; Rosotti2021; Yu2021; Alarcon2022; Izquierdo2022)) and more extended (e.g non-Keplerian spirals; (cite: Teague2019Spiral; Teague2021; Teague2022; Rosotti2020a; Casassus2021; Garg2021; Woelfer2021; Stadler2023)) kinematical deviations from recent years are generally consistent with the presence of massive embedded planets.

Identifying vortex signatures in the gas dynamics is crucial to not only confirm their presence but also to study their dust trapping properties and understand the formation of the dust concentrations in disks. As shown by (cite: Robert2020), vortices produce signatures potentially discernible in the line-of-sight velocity through observations with current facilities. This includes the anticyclonic motions around the density maximum of a vortex as well as vortex-driven spirals, with the latter being comparable to those excited by a planet with a mass of a few to a few tens of Earth masses (cite: Huang2019). (cite: Yen2020) indeed report kinematical deviations in the HD 142527 disk, which are consistent with a local pressure bump and co-located with the large horseshoe structure seen in the dust disk, yet their observations do not allow to distinguish if the pressure bump is formed by a vortex or massive planet. (cite: Boehler2021) compare CO emission lines of the same disk with a vortex model, and find kinematic signatures consistent with the presence of a large vortex, however, due to limitations in the spatial resolution of the data, artificial velocity deviations generated by beam smearing, cannot be ruled out.

In this work, we make use of the unprecedented sensitivity at high resolution of the exoALMA data (cite: Teague_exoALMA) to study the kinematical features seen around the azimuthal asymmetries of four disks in the sample and search for a kinematical vortex counterpart. In that regard, we compare the observations with both an analytical model of vortices and hydrodynamical simulations of a vortex triggered at the edge of a dead zone and gap created by a massive planet, respectively. The paper is structured as follows: in [2](#sec:observations) we describe the source sample and present the observations. Our models are outlined in [3](#sec:methodsAna) and [4](#sec:methodsSim) and compared to the data in [5](#sec:results). Our results are summarized in [6](#sec:summary).

| Source          | HD 135344B | HD 143006 | HD 34282 | MWC 768 |
|:----------------|:----------:|:---------:|:--------:|:-------:|
| $i$ ($\degree$) |     16     |    17     |    58    |   19    |
| PA ($\degree$)  |    243     |    168    |   117    |   240   |

: Inclination and position angle of the sources, obtained by modelling the $^{12}$CO emission line with DISCMINER (cite: Izquierdo_exoALMA). The position angle is measured counterclockwise from the north to the redshifted axis of the disk.

# Observations

![](plots/vel_res_overview_arcsec.png)

Our source sample consists of four sources – namely HD 135344B, HD 143006, HD 34282, and MWC 758 – which were observed as part of the exoALMA large program (cite: Teague_exoALMA). They are among the six most asymmetric disks in continuum (cite: Curone_exoALMA) in the exoALMA sample and all show evidence of azimuthal dust traps in their millimetre (mm) continuum (compare top row of [1](#fig:dust_gas)), possibly caused by the presence of a vortex. Three of the sources – HD 135344B, HD 34282, and MWC 758 – are further marked by spiral structures in near-infrared (NIR) scattered light (compare middle row of [1](#fig:dust_gas), (cite: Stolker2017; Boer2021; Ren2023)). A summary of each source is provided [7](#sec:target_summary). The inclination and position angle of the targets, obtained with DISCMINER (cite: Izquierdo_exoALMA), are summarized in [1](#tab:dataInfo).

To study the gas features seen around the dust azimuthal asymmetries in our sample, we make use of the fiducial exoALMA images (cite: Teague_exoALMA) of the $^{12}$CO and $^{13}$CO $J=3-2$ emission lines (0$\hspace{1pt}.\!\!^{\prime\prime}$15; 100$\,$m$\,$s$^{-1}$, continuum-subtracted). The CS $J = 7-6$ images are excluded from this work due to their much lower SNR at the same resolution. For the full details of the imaging techniques, we refer the reader to (cite: Loomis_exoALMA). For both lines, the molecular emission channels were modeled with the DISCMINER package (cite: Izquierdo2021), which returns a smooth Keplerian model of the line intensity profile. To identify perturbations in the gas dynamics, it is then necessary to extract observables - such as the centroid velocity, line peak intensity, and line width - in a post-processing step and to compute deviations between the data and model (residuals). Here, this is done by fitting both the data and model line profiles with a Gaussian function, except for the HD 34282 disk for which a double-peaked bell profile is adopted. While for low-inclination disks, a single-peak profile is sufficient to represent the morphology of the profile, higher-inclination disks such as HD 34282 are better reproduced with a double-peak profile since emission from the back side of the disk is visible. This approach then allows to separate the contribution from the front and back sides of the disk. Details of the modeling procedures and choice of extraction methods can be found in (cite: Izquierdo_exoALMA).

In the bottom row of [1](#fig:dust_gas), a gallery of the $^{12}$CO peak intensity is shown for the four targets studied here. Emission below 5$\sigma$ is masked. The continuum emission (top row) is overlaid as contours, placed equally between 3$\sigma$ and the continuum peak, highlighting the location of the potential vortices at relatively small radii compared to the large extents of the gas disk. The latter exceeds the dust disk by a factor of roughly 2-3, which is expected from processes such as radial drift or the difference between dust and gas opacities (cite: Facchini2017; Trapman2019). Given that $^{12}$CO emission is optically thick, the peak intensity traces the temperature of the gas, with the observed temperatures of up to $\sim 100$ K being as expected in the upper disk layers (e.g. (cite: Bruderer2013; Bruderer2014; Leemker2022)). A thorough analysis of the 2-dimensional temperature structure of the disks can be found in (cite: Galloway_exoALMA).

## Velocity residuals

In [2](#fig:VelRes), we present the velocity centroid residuals of our targets after subtraction of the Keplerian DISCMINER model from the $^{12}$CO (top row) and $^{13}$CO (bottom row) data (Fukagawa et al. in prep.), respectively. For the HD 34282 disk, the contribution from the back side has been subtracted in the computation of the residuals, as discussed in (cite: Izquierdo_exoALMA). The other three disks are close to face on and do not require a removal of the lower surface.

![](plots/Vortex_analytical_model_arcsec.png)

The HD 135344B kinematics are marked by prominent asymmetric arc- and spiral-like structures, seen in both emission lines, as well as features resembling a Doppler flip. Similarly, MWC 758 shows a large spiral arm, covering more than one full azimuth. For both disks, similar features are seen in the peak intensities and line widths (compare [7](#fig:polarSpirals)). Altogether, this suggest strong perturbations in these disks. Interestingly, they are also the two disks in our sample that exhibit extended spirals in the near-infrared scattered light (see [8](#sec:spirals)). The patterns seen for the HD 143006 disk are less clear or consistent, but a prominent red-shifted arc can be distinguished in the kinematics traced by both lines (even though at an offset), which may connect to the extended red-shifted arc in the outer disk. The residuals of the HD 34282 disk are particularly difficult to interpret due to the high-inclination nature of the source. Even though the DISCMINER model and subsequent fit with a double-peaked bell profile account for both the upper and lower disk surface, contributions from the lower side seem to still be visible in the upper surface residuals and the vertical structure off the disk is seen as a butterfly pattern in the inner disk regions.

# Methods I: Analytical Vortex Model

In the following sections, we model the kinematical signature of a vortex to compare with the deviations seen in the residuals of our sample. For that purpose, we first construct a simple analytical model similar to (cite: Boehler2021), which serves as a guideline for understanding the general kinematical patterns triggered by a vortex, and helps to gain intuition for the more complex residuals. Subsequently, we perform 2-dimensional hydrodynamical simulations (see [4](#sec:methodsSim)).

Doing so, we are mostly interested in comparing the kinematical patterns of a vortex to the data rather than a full representation of the vortex properties, which remains challenging (cite: Huang2019; Robert2020).

![](plots/Vortex_analytical_model_several_v2_arcsec.png)

## Model description

We follow (cite: Boehler2021) in setting up the vortex flow as streamlines of constant velocity around a central position (r$_0$, $\phi_0$) in polar disk coordinates, with the rotation velocity of the vortex varying as a Gaussian in the radial direction. In contrast to (cite: Boehler2021), the streamlines are elliptical in the vortex frame in Cartesian coordinates, analogous to a shearing-box. Our parameterization is depicted in the first panel of [3](#fig:vortexAnalytical). Here, the vortex is shown in the Cartesian vortex frame (subscript v) and is thus centered around the origin of this frame. The velocity in the vortex increases to a maximum velocity $v_{\mathrm{max}}$ at the radius $r_{\mathrm{v}}$. The vortex is further described by an aspect ratio $\chi$, the ratio of the major axis in the azimuthal direction to the minor axis in the radial direction. The width of the Gaussian profile is given by $\omega_{\mathrm{V}}$.

The Cartesian vortex coordinates $(x_{\mathrm{V}},y_{\mathrm{V}})$ can be related to the polar disk coordinates $(r,\phi)$ through

$$\begin{align}
& x_{\mathrm{V}} = r (\phi - \phi_0)\,\,\&\\
& y_{\mathrm{V}} = r-r_0,
\end{align}$$

where $(r_0,\phi_0)$ describes the center of the vortex. These can further be transformed into polar vortex coordinates $(r',\phi')$ via

$$\begin{align}
& r' = \sqrt{x_{\mathrm{V}}^2 + (\chi \cdot y_{\mathrm{V}})^2}\,\,\& \\
& \phi' = \tan^{-1}\left(\frac{x_{\mathrm{V}}}{\chi \cdot y_{\mathrm{V}}}\right). 
\end{align}$$

The absolute rotation velocity of the Vortex is then given as $$\begin{equation}
|v(x_{\mathrm{V}},y_{\mathrm{V}})| = v_\mathrm{max} \cdot \exp \left[\left(\frac{r'-r_{\mathrm{V}}}{\omega_{\mathrm{V}}}\right)^2\right].    
\end{equation}$$

In [3](#fig:vortexAnalytical), the absolute orbital velocity is shown in the vortex frame (first panel) alongside the sky frame (second panel), using an inclination of $16\,\degree$ and position angle of $243\,\degree$ for the projection (same as for HD 135344B). The velocity projected along the line-of-sight is then given as $$\begin{equation}
v_0 = |v(x,y)| \cdot \cos{(\phi'+\phi)} \cdot \sin{i},    
\end{equation}$$

where $i$ represents the disk inclination. The projected velocity of the vortex is presented in the last panel of [3](#fig:vortexAnalytical) in the sky frame, showing a clear red-blue pattern with a complex morphology, which purely results from projection effects.

## Parameter exploration

In [4](#fig:vortexAnalytical2), we present the line-of-sight velocity for different disk geometries as well as parameters of the analytical vortex model. In this context, the parameters given on top of the figure correspond to the base model shown in the first panel, while the individual parameters changed compared to this model are given in each panel. This exercise highlights that while generally, a similar red-blue pattern is visible in all cases, the exact morphology and strength of the pattern varies substantially for different combinations of parameters. We further note that the vortex edges have strong radial components, while along the ‘arcs’, the deviations are dominated by azimuthal motions.

We attempted to constrain the basic properties of the dust crescents seen in our targets by implementing the simple vortex model in the `eddy` code (cite: eddy), which allows to fit a Keplerian profile to a rotation map. In this context, we first conducted a run to find a good representation of the main rotation pattern, and in subsequent runs fixed those values to only fit for the vortex parameters described in [3.1](#sec:AnalyticalSetup), fitting different disk regions. However, none of these runs converged and resulted in very degenerate distributions. Given the complex kinematical patterns seen in our targets (see [2](#fig:VelRes)), we conclude that a simple model is not sufficient to constrain the properties of the vortex. We are further limited by the low inclination of three of the four sources, making it hard to detect azimuthal motions projected into the line-of-sight. This is different for vertical motions. The importance of vertical motions is unclear at this point (e.g., (cite: Meheut2010; Meheut2012a; Lin2012; Richard2013)), but they may dominate the vortex signature in some cases, which cannot be captured by our simple 2D model. Moreover, other disk processes such as planet-disk interactions can create dynamical patterns which overlay the vortex signatures and make it challenging to isolate them (see also (cite: Barraza2024)). Nevertheless, the analytical model is useful to gain intuition for the general patterns created by a vortex and can help to interpret both the simulations and observations (see [4](#sec:methodsSim)).

![image](plots/Vortex_simulation_DZ.png) ![image](plots/Vortex_simulation_PL.png)

# Methods II: Simulations

We explore the kinematic structure from a vortex (and vortex+planet) by conducting 2D numerical simulations with the grid-based code PLUTO (cite: Mignone2007), version 4.4. In this context, we do not aim for a comprehensive parameter study but intend to expand beyond the relatively simple analytical model to try to capture some of the complexity seen in the data. We follow the disk evolution, solving the Navier-Stokes equations of fluid dynamics (for details see Section 2 in (cite: Barraza2024)) for two scenarios: a vortex triggered by the Rossby-wave instability (RWI) at the inner edge of a MRI dead-zone, and RWI triggered at the edge of a gap opened by a Jupiter mass planet. Even though the inner edge of the dead zone – in contrast to the outer edge – is unlikely to be relevant on exoALMA scales, we set up the simulation in this way to trigger a vortex at a particular location. The mechanism generating the vortex is the same for both the inner and outer edge, but in the latter case results in a less clean vortex and uncertain location due to radial migration. Here we are mainly interested in the morphology of the vortex and creating a vortex in the same location for both the dead zone and embedded planet simulation makes it easier to compare the two cases. In both cases, a vortex spontaneously forms within a few hundred orbits, computed at 1 code unit length in the dead zone scenario and corresponding to planetary orbits in the planetary case.

We use a PLUTO numerical setup with LINEAR reconstruction method, 2nd order Runge-Kutta time-stepping, the Harten-Lax-Van Leer Riemann (HLLC) solver, and we include the disk viscosity as a diffusion term integrated with Super-Time-Stepping (STS) technique. We set the Courant number (CFL) to 0.4.

## Disk Setup

We consider a two-dimensional disk in polar coordinates, including the evolution of the gas only. The disk initial conditions are based on the numerical setup presented in (cite: Miranda2017). Our simulations follow a locally isothermal equation of state $P=c_{\mathrm{s}}^2 \Sigma$, where $P$ is the vertically-integrated gas pressure, and the disk gas surface density $\Sigma_{\mathrm{g}}$ follows: $$\begin{equation}
    \Sigma_{\mathrm{g}} = \Sigma_0 \left(\frac{r}{r_0}\right)^{-1},
\end{equation}$$ with $r_0$ the code unit of length, and $\Sigma_0$ the gas surface density at $r=r_0$. The disk sound speed $c_{\mathrm{s}}$ has a radial dependency $c_{\mathrm{s}} = c_{\mathrm{s},0}(r/r_0)^{-0.25}$. The value of $c_{\mathrm{s},0}$ is set so that $H(r_0)/r_0=0.05$, with $H$ the disk pressure scale height, $H=c_s/\Omega_K$, where $\Omega_K = \sqrt{G M_{\star}/r^3}$ is the Keplerian orbital frequency. Our disk model results in a flared disk, with $H\propto r^{1.25}$.

The simulation domain covers 0.3-3.0 code units of length in the radial direction, and $2 \pi$ rad in azimuth. The simulations were run with a grid of $1024$ and $2048$ cells in $r$ and $\phi$, respectively, with a mesh uniformly spaced in both the radial and azimuthal directions. The grid uniform radial spacing allows a better resolved dead-zone edge transition and outer planetary gap edge relative to a logarithmic mesh. The effects of disk self-gravity are not taken into account in our models.

### Dead Zone Edge

To mimic a MRI-deadzone transition, we follow (cite: Miranda2017), however, for the inner edge of a dead-zone instead of the outer one, implementing a transition between two levels of viscosity described by a radially-dependent $\alpha$-viscosity model, $\nu=\alpha c_{\mathrm{s}} H$ (cite: Shakura1973), with $\alpha$ following

$$\begin{equation}
    \alpha(r) = \alpha_0 \left( 1 - \frac{1}{2} \left( 1 - \frac{\alpha_{\mathrm{DZ}}}{\alpha_0} \right) \left[ 1 + \tanh{\left( \frac{r-r_{\mathrm{DZ}}}{\Delta_{\mathrm{DZ}}} \right)} \right]  \right),
\end{equation}$$

with $\alpha_{\mathrm{DZ}}=10^{-5}$ and $\alpha_{0}=10^{-3}$ being the $\alpha$-viscosity parameters in the MRI-dead and MRI-active regions, respectively. The location of the transition between the active and dead zones is put as 1.2 code units of length ($r_{\mathrm{DZ}}=1.2 r_0$), and $\Delta_{\mathrm{DZ}}$ sets the width of the transition. We set $\Delta_{\mathrm{DZ}}=H(r_{\mathrm{DZ}})$, corresponding to the standard run from (cite: Miranda2017) (see their Table 1).

![](plots/compare_data_model_conv.png)

## Planet

In a second setup, we include a $1\,M_{\mathrm{J}}$ planet and the star as the gravitational potential of points of mass, and the indirect acceleration term

$$\begin{equation}
    \Phi = \frac{G M_{\star}}{r} - \frac{G m_{\mathrm{p}}}{\sqrt{|\vec{r}-\vec{r_{\mathrm{p}}}|^2+s^2}} + \frac{G m_{\mathrm{p}}}{r_{\mathrm{p}}^2}r \cos{\phi},
\end{equation}$$

where $\vec{r_{\mathrm{p}}}$ is the distance from the star to the planet, and $s$ a potential smoothing length set to $60\%$ of the local disk pressure scale height (see e.g, (cite: Masset2002; Muller2012; Weber2019)). We fix the planet orbital distance to 1 code unit of length (or $r_{\mathrm{p}}=r_0$). In addition, we include a tapering such that the planet mass smoothly reaches its final value in $30$ planetary orbits. Finally, for the planet simulation, we use a constant $\alpha$ viscosity value of $10^{-5}$.\
\
In [5](#fig:vortexSimulation), we show the density (left panel), radial velocity (middle panel), and azimuthal velocity relative to a sub-Keplerian background (right panel) resulting from the simulations of a vortex triggered by the RWI at the edge of a dead zone (top row) and gap created by a massive planet (bottom row), respectively. We have used a scaling radius of 70 au to convert from code units to physical units (thus $r_{\mathrm{DZ}} = 84\,\mathrm{au}$ and $r_{\mathrm{p}} = 70\,\mathrm{au}$). To highlight the patterns created by the vortex, we have subtracted the density field and sub-Keplerian rotation velocity of a smooth disk from the perturbed density and velocity fields. Since in this work we are primarily interested in the patterns created by a vortex and not the exact magnitude of the perturbation, we have further normalized the quantities by the local sub-Keplerian velocity. The simulation snapshots depicted correspond to 400 orbits measured at 1 code unit of length (dead zone) and 580 planetary orbits, respectively.

# Results

Similar to previous works (e.g (cite: Huang2019; Robert2020)), it is apparent that the vortex creates a prominent azimuthally asymmetric feature in the gas dynamics, seen as a clear red-blue dipole pattern, as well as spiral structures ([4](#fig:vortexAnalytical2) and [5](#fig:vortexSimulation)). The vortex motion looks similar in both the simulations and analytical model, but the spiral features cannot be captured by the latter. If a planet is included in the disk, it creates its own Doppler-flip signature and much stronger spiral features, which overlay on the pattern associated with the vortex, thus making it much harder to distinguish.

To compare the vortex signatures predicted by the simulations with the features seen in the velocity residuals, we post-processed the dead zone simulation with RADMC-3D (cite: Dullemond2012) and computed mock images of a flat disk model. In this context, we took the geometry of the sources into account and then matched the radial and azimuthal location of the vortex with the dust asymmetries seen in the data. To directly obtain the expected residuals from the simulated vortex dynamics, we subtracted the sub-Keplerian background from the azimuthal velocity used as an input in the radiative transfer model. We then created synthetic $^{12}$CO channel maps via ray-tracing with the same spectral resolution as the data. As a final step, we convolved the synthetic data cubes with a 0$\hspace{1pt}.\!\!^{\prime\prime}$15 Gaussian beam, and computed the line-of-sight velocity maps using BETTERMOMENTS (cite: bettermoments).

The result of this test is shown in [6](#fig:vortexCompare), where the first two rows represent the $^{12}$CO and $^{13}$CO residuals, and the bottom row the dead zone vortex simulation. The continuum emission is overlaid on the data to highlight the location of the dust crescents. For MWC 758, two representations are included since this disk is marked by several azimuthal asymmetries. The unconvolved model images are shown in [9](#sec:model_unconv).

Comparing the data and model, it becomes apparent that most disks do not show a clear vortex kinematic signature around the dust crescents as predicted by the simulation. In HD 135344B, a similar red-blue pattern is traced by both emission lines, yet it is shifted with respect to the dust asymmetry and, overlaid by the strong spiral features, and nearby the disk minor axis, where a change of sign due to coherent azimuthal variations is expected (Fig.5 in (cite: Teague2019Spiral)). Even though the vortex also triggers a similar spiral pattern, it is generally not expected to be strong enough to distinguish it in the kinematics (see also (cite: Huang2019)). Close to the inner crescent in MWC 758, a red-blue flip is present which resembles the vortex model, but it is part of the red and blue spiral arms and less distinct than the red-blue pair spanning the dust asymmetry in HD 135344B. Among our sample, this makes HD 135344B the most convincing example of a vortex and the best target to pursue with even deeper observations at very high angular resolution. Connected to that, when comparing the size of the dust asymmetries with the size of the beam, it becomes clear that they are very similar, thus the vortex signatures may not be resolved and therefore do not clearly show up in the kinematics.

Aside from planet-disc interactions, other processes such as (magneto-)hydrodynamical instabilities and the gravitational instability (cite: Barraza2024; Barraza_exoALMA; Hall2020), stellar interactions including binaries (cite: Calcino2020; Norfolk2022) and fly-bys (cite: Cuello2020), or magnetic winds (cite: Galloway2023) can contribute to the kinematics and may obscure the signatures from a vortex, resulting in complex patterns which are hard to disentangle. (cite: Ragusa2024) make predictions for the kinematics expected from an eccentric circumbinary disk, finding that they result in a single lobed pattern at the cavity edge. Compared to our data, we cannot distinguish such a pattern, though this may result from resolution effects.

# Summary & Conclusions

In this work, we have studied four disks within the exoALMA sample which show evidence of dust trapping in a vortex, to search for a kinematic counterpart of the latter. Our main results are summarized as follows.

- The kinematics of our targets, which all show azimuthal dust asymmetries, are marked by complex patterns, including spirals and Doppler flip features ([2](#fig:VelRes)). Two of the sources, HD 135344B and MWC 758, show prominent spirals in both the NIR scattered light and all three residuals, with the substructures partially coinciding ([8](#sec:spirals)).

- An analytical model of the velocity perturbation from a vortex reveals a distinct red-blue pattern but shows different morphologies depending on the underlying disk geometry and exact vortex parameters ([3](#fig:vortexAnalytical),[4](#fig:vortexAnalytical2)). This simple model is, however, insufficient to explain the complexity of structure seen in the data.

- Hydrodynamical simulations of a vortex and vortex+planet also reveal a clear red-blue kinematical pattern in addition to spiral features. In the planetary scenario, the signatures of the vortex are mixed with the strong perturbations from the planet, making it much more difficult to distinguish them ([5](#fig:vortexSimulation)). Other disk processes perturbing the gas dynamics are expected to further complicate this picture.

- Comparing the kinematical patterns of the data and model shows that the features seen around the dust crescents cannot unambiguously be linked to a vortex ([6](#fig:vortexCompare)). Aside from the complications arising due to different physical processes impacting the kinematics, our results may also limited be by the spatial resolution in comparison to the size of the dust asymmetries. While fully resolving the vortex is not necessarily needed to trace the red-blue flip, it is essential if we are to parameterize it and trace the pressure-profile across the vortex. As shown by (cite: Stadler_exoALMA), the pressure morphology of dust rings can only be inferred if they are spatially resolved and we are faced with same challenge in the context of vortices.

While it is necessary to aim for higher spatial resolution to unambiguously detect the kinematic signature of a vortex, it can also be useful to study emission lines which trace closer to the midplane, where vortices reside, to be more sensitive to the vortex dynamics (compare (cite: Pinte2019), showing how the strength of a planet’s perturbation diminishes with height). This is the case for CS $J=7-6$ (compare (cite: Galloway_exoALMA)), which was observed within the exoALMA program (Cataldi et al. in prep.). Both the SNR at high spatial resolution and likely the resolution itself are, however, insufficient to draw conclusions about the kinematical pattern around the dust asymmetries, but could be studied in a future work.

Getting as close as possible to the midplane may increase our chance of detecting the vortex in the gas dynamics significantly.

The vortex predictions presented in this work rely on 2D models. However, to reveal the full dynamics of a vortex and in particular understand the role of vertical motions, global 3D simulations are essential. These simulations are challenging and the formation and stability of 3-dimensional vortices remains an active matter of debate. Earlier works have addressed the question of 2D versus 3D vortices triggered by the RWI, but have resulted in different conclusions: While the general vortex patters are consistent between 2D and 3D simulations, some studies suggest vertical motions to be negligible (cite: Lin2012; Richard2013), others show that they can be more significant in certain cases (cite: Meheut2010; Meheut2012a). More detailed theoretical studies are needed to understand how the strength of features varies with height and if they may be reliably detectable in tracers such as $^{12}$CO and $^{13}$CO.

Within the exoALMA sample, the most promising source for follow-up observations to detect the kinematic signature of an anti-cyclonic vortex is HD 135344B, as it is marked by a relatively large dust crescent and the kinematics show a pattern which resembles the signatures of a vortex. In terms of the expected strength of the kinematic signature from a vortex, HD 34282 may be another useful target to follow-up with higher spatial resolution and less abundant tracers at higher sensitivity due to its large inclination. The dust asymmetry in this source is, however, relatively small and located closer to the star, making such observations challenging.

# Acknowledgments

We thank the anonymous referee for the comments, which greatly improved the quality of this paper.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.01123.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. We thank the North American ALMA Science Center (NAASC) for their generous support including providing computing facilities and financial support for student attendance at workshops and publications.

The authors acknowledge the MIT SuperCloud and Lincoln Laboratory Supercomputing Center for providing HPC resources that have contributed to the research results reported within this paper.

JB acknowledges support from NASA XRP grant No. 80NSSC23K1312. MB, DF, JS have received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (PROTOPLANETS, grant agreement No. 101002188). Computations by JS have been performed on the ’Mesocentre SIGAMM’ machine, hosted by Observatoire de la Cote d’Azur. PC acknowledges support by the Italian Ministero dell’Istruzione, Università e Ricerca through the grant Progetti Premiali 2012 – iALMA (CUP C52I13000140001) and by the ANID BASAL project FB210003. SF is funded by the European Union (ERC, UNVEIL, 101076613), and acknowledges financial contribution from PRIN-MUR 2022YP5ACE. MF is supported by a Grant-in-Aid from the Japan Society for the Promotion of Science (KAKENHI: No. JP22H01274). CH acknowledges support from NSF AAG grant No. 2407679. JDI acknowledges support from an STFC Ernest Rutherford Fellowship (ST/W004119/1) and a University Academic Fellowship from the University of Leeds. Support for AFI was provided by NASA through the NASA Hubble Fellowship grant No. HST-HF2-51532.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555. CL has received funding from the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska-Curie grant agreement No. 823823 (DUSTBUSTERS) and by the UK Science and Technology research Council (STFC) via the consolidated grant ST/W000997/1. FMe acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon Europe research and innovation program (grant agreement No. 101053020, project Dust2Planets). CP acknowledges Australian Research Council funding via FT170100040, DP18010423, DP220103767, and DP240103290. DP acknowledges Australian Research Council funding via DP18010423, DP220103767, and DP240103290. GR acknowledges funding from the Fondazione Cariplo, grant no. 2022-1217, and the European Research Council (ERC) under the European Union’s Horizon Europe Research & Innovation Programme under grant agreement no. 101039651 (DiscEvol). H-WY acknowledges support from National Science and Technology Council (NSTC) in Taiwan through grant NSTC 113-2112-M-001-035- and from the Academia Sinica Career Development Award (AS-CDA-111-M03). GWF acknowledges support from the European Research Council (ERC) under the European Union Horizon 2020 research and innovation program (Grant agreement no. 815559 (MHDiscs)). GWF was granted access to the HPC resources of IDRIS under the allocation A0120402231 made by GENCI. AJW has received funding from the European Union’s Horizon 2020 research and innovation programme under the Marie Skłodowska-Curie grant agreement No 101104656. TCY acknowledges support by Grant-in-Aid for JSPS Fellows JP23KJ1008. Support for BZ was provided by The Brinson Foundation. Views and opinions expressed by ERC-funded scientists are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council. Neither the European Union nor the granting authority can be held responsible for them.

# Summary of the sources

## HD 135344B

HD 135344B – or SAO 206462 – is a young (8.9 Myr; (cite: Asensio2021)) Herbig F-type star located in the Upper Centaurus-Lupus star-forming region at a distance of $\sim 135\,\mathrm{pc}$ (Gaia DR3; (cite: Gaia2023)). It is part of a visual binary system (separation 21$''$, i.e. $\sim$ 2800 au; (cite: Mason2001)) and surrounded by a low-inclination transition disk which has been extensively studied at different wavelengths.

The disk was first resolved with the *Hubble Space Telescope* (cite: Grady2009), with subsequent scattered light observations revealing substructures such as an inner dust cavity ($\sim$ 28 au) and two prominent spiral arms on a scale of $\sim$ 0.2-0.6$''$ (cite: Muto2012; Garufi2013; Stolker2016; Stolker2017), one being marked by a brightness asymmetry and pitch angle change, possibly caused by the spiral moving through a high-density vortex region (cite: Bae2016). Moreover, the scattered light images exhibit shadow features which may be related to misaligned inner disk regions (cite: Stolker2016; Stolker2017).

A large dust cavity ($\sim$ 50 au), originally suggested through SED modelling by (cite: Brown2007), was later confirmed in the mm-continuum with the SMA (cite: Brown2009; Andrews2011) and ALMA (cite: Perez2014; Marel2016; Cazzoletti2018). Additionally, these data revealed an asymmetric crescent located further out ($\sim$ 80 au), which is marked by an azimuthal peak shift with wavelength and matches the predictions of a dust-trapping vortex (cite: Marel2016; Cazzoletti2018). The two dust rings are connected by a filament, which co-locates with the deviation in the spiral arm and may be tracing a planetary wake crossing the dust gap (cite: Casassus2021).

Observations of CO gas in the disk revealed an inner gas cavity peaking inside the dust cavity ($\sim$ 30 au) and a spiral feature in the kinematics (cite: Marel2016; Casassus2021). Similar to the NIR data, shadows are seen in archival C$^{18}$O and exoALMA CS data (Cataldi et al. in prep.). Several works have shown that the different observations may be explained by one or more massive embedded planets (e.g. (cite: Muto2012; Garufi2013; Fung2015; Bae2016; Stolker2016; Dong2017a; Casassus2021; Izquierdo_exoALMA)). While such companions were previously not found in a variety of high-contrast imaging programs (e.g. (cite: Maire2017; Cugno2019; Zurlo2020; Asensio2021; Follette2023)), a potential candidate located at $\sim 300$ au in the disk was identified by (cite: Cugno2024) in JWST data.

## HD 143006

The HD 143006 system, located at a distance of $\sim 167\,\mathrm{pc}$ (cite: Gaia2023) in the Upper Scorpius star-forming region, consists of a G-type T Tauri star of age 7-12 Myr (cite: Andrews2018; Garufi2018) and a disk seen close to face-on.

Imaging of the disk’s infrared scattered light revealed various brightness asymmetries, including a broad dark region covering the west side of the disk, two narrow shadow lanes, and a prominent over-brightness located in the south-east of a ring at $\sim$ 18-30 au (cite: Benisty2018). A similar, yet less pronounced, over-brightness is also present in the outer disk ring at $\sim$ 50-83 au.

The mm-continuum on the other hand is marked by three concentric dust rings (8, 40, and 64 au) and a bright crescent-like structure in the south-east, just outside the outer dust ring at 74 au (cite: perez2018). The latter is further substructured into three different peaks and generally consistent with a vortex formed at the edge of a cavity, with its morphology, however, pointing towards a second-generation vortex (cite: perez2018). Moreover, the bright arc coincides with the outer over-brightness in the scattered light emission but is less extended, which matches predictions of dust trapping in vortices (cite: Baruteau2016).

Observations of CO gas emission in HD 143006 exhibit less structures but indicate gas depletion in the very inner disk and the presence of a kink-feature in some red-shifted channels (cite: perez2018; Pinte2020). Both the scattered light and mm-observations support the scenario of a misaligned inner disk (cite: Benisty2018; perez2018), with the morphology possibly being explained by the combination of a misaligned binary and an embedded aligned planet in the outer disk (cite: Ballabio2021).

## HD 34282

The Herbig Ae star HD 34282 – or V1366 Ori – is about 8.9 Myr old (cite: Asensio2021) and located at a distance of $\sim$ 309 pc (cite: Gaia2023). A highly inclined circumstellar disk around the source was resolved in the mm-emission by (cite: Pietu2003). A large inner dust cavity in the disk was suggested through modelling of the SED and mid-infrared Q-band images (cite: Acke2009; Khalafinejad2016) and later confirmed ($\sim$ 80 au) in ALMA data by (cite: Plas2017). These images further revealed that the $\sim$ 300 au wide dust ring contains an azimuthal asymmetry in the south-east. The authors suggest a massive brown dwarf companion ($\sim$ 50 M$_\mathrm{J}$) to be responsible for both observed substructures.

Scattered-light observations allowed (cite: Boer2021) to identify two inclined rings and a tightly wound single-arm spiral, which is generally consistent with a Jupiter-mass planet and coincides with the mm-crescent. The latter may be the signature of vortex in the disk which, as shown by (cite: Marr2022), can resemble a spiral arm in a highly inclined source. So far, no direct evidence of a companion in HD 34282 has been found (cite: Asensio2021; Boehler2021; Quiroz2022). The study of (cite: Bohn2022), who compare position angle and inclination of the inner disc measured with VLTI/GRAVITY and the outer disc measured with ALMA, suggests a misalignment between the inner and outer disk of the system, yet no clear shadow signatures are visible in the scattered light images

## MWC 758

Located in the Taurus star-forming region at a distance of 156 pc (cite: Gaia2023), the young ($\sim$ 8.9 Myr; (cite: Asensio2021)) Herbig Ae star MWC 758 – also known as HD 36112 – is surrounded by a low-inclination transition disk which has been the subject of a range of high resolution studies, revealing a complex asymmetric morphology.

NIR scattered light observations unveiled two prominent spiral arms (cite: Grady2013; Benisty2015) and other non-axisymmetric arc-like features (cite: Benisty2015). The detection of a third spiral arm and potential point-like source at $\sim$ 17 au were reported by (cite: Reggiani2018). Both gravitational instability (cite: Dong2015b) and massive planets (cite: Dong2015a; Bae2018; Baruteau2019; Calcino2020) have been suggested as the driving mechanism of the spirals, with the latter being favoured by an imaging study of the spiral pattern over 5 yr (cite: Ren2020).

No fully depleted cavity was found in the scattered light data, but the mm-continuum of the disk is marked by a large and eccentric cavity ($\sim$ 40 au; (cite: Dong2018_mwc)), possibly carved by an embedded planet (cite: Isella2010; Andrews2011; Marino2015; Boehler2018). Additionally, two bright emission clumps inside a double-ring structure are present at radii of $\sim$ 47 and 82 au (cite: Marino2015; Boehler2018; Dong2018_mwc; Casassus2019b), and may be related to dust-trapping pressure maxima in a vortex.

Several spirals have been identified in both the continuum emission (cite: Boehler2018; Dong2018_mwc; Shen2020) and CO data (cite: Boehler2018), which are partly co-located with the spirals observed in the infrared data. (cite: Baruteau2019) performed hydrodynamical simulations showing that the spirals, the eccentric and asymmetric ring structure, and the crescent-shaped features may all be explained by two Jupiter mass planets, one located inside and one outside the spirals. High-contrast imaging searches have reported the detection of such planets (cite: Reggiani2018; Wagner2019; Wagner2023), but they remain to be confirmed.

# Spiral features

In [7](#fig:polarSpirals), we present the polar-deprojected CO residuals for the centroid velocity, peak intensity, and line width alongside the polar-deprojected scattered light emission, for the two disks that show prominent spiral features: HD 135344B and MWC 758. For comparison, the spirals found in the near-infrared are further overlaid as contours on the gas emission residuals. The deprojection is performed by using the inclination and position angle (see [1](#tab:dataInfo), (cite: Izquierdo_exoALMA)) of the individual sources. This is sufficient due to the face-on nature of the disk.

For both disks, the inner spirals seen in the velocity residuals appear to align somewhat with the NIR spirals. In HD 135344B, both NIR spiral arms are located just inside the red-shifted velocity arms. In MWC 758, one of the NIR spiral ($-90$ to $90\degree$) has a red-shifted counterpart in the velocity residuals while the other has a blue-shifted counterpart ($-180$ to $-90\degree$). For the peak intensity, on the other hand, the spiral patterns seen for MWC 758 align very well with the NIR spirals, whereas this is not the case for HD 135344B. We note that the strong temperature decrement seen around 80 au in this source is the result of continuum subtraction. In the line width, spiral patterns are mostly visible in the negative residuals, which again seem to somewhat align with the NIR spirals for MWC 758 but not HD 135344B (for a detailed discussion see Benisty et al. in prep.).

![image](plots/polar_residuals_hd135344b_spiral_v2.png) ![image](plots/polar_residuals_mwc758_spiral_v2.png)

# Unconvolved model images

In [8](#fig:vortexCompareUnconv), we show the unconvolved model images of the dead zone simulation alongside the convolved images (0$\hspace{1pt}.\!\!^{\prime\prime}$15 beam). The continuum observations are overlaid as contours to highlight that the model has been adapted to each disk such that the vortex is present at the same location as the dust asymmetries. In this work, we are mainly interested in the kinematical patterns of a vortex and we note that the exact strength of these features depends on various factors. Moreover, we assume a flat disk and the magnitude of the vortex may be significantly underestimated. In that regard, the unconvolved images nevertheless emphasize the need for higher spatial resolution. In particular, an inclined source such as HD 34282 may show very strong vortex features if resolved at very high resolution.

![](plots/model_conv_noconv.png)

natexlab

(ref: Acke2009) Acke, B., Min, M., van den Ancker, M. E., et al. 2009, A&A, 502, L17, doi: [`10.1051/0004-6361/200912728`](http://doi.org/10.1051/0004-6361/200912728)

(ref: Alarcon2022) Alarcón, F., Bergin, E. A., & Teague, R. 2022, ApJL, 941, L24, doi: [`10.3847/2041-8213/aca6e6`](http://doi.org/10.3847/2041-8213/aca6e6)

(ref: ALMA2015) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3, doi: [`10.1088/2041-8205/808/1/L3`](http://doi.org/10.1088/2041-8205/808/1/L3)

(ref: Andrews2011) Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42, doi: [`10.1088/0004-637X/732/1/42`](http://doi.org/10.1088/0004-637X/732/1/42)

(ref: Andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: Asensio2021) Asensio-Torres, R., Henning, T., Cantalloube, F., et al. 2021, A&A, 652, A101, doi: [`10.1051/0004-6361/202140325`](http://doi.org/10.1051/0004-6361/202140325)

(ref: Ayliffe2012) Ayliffe, B. A., Laibe, G., Price, D. J., & Bate, M. R. 2012, MNRAS, 423, 1450, doi: [`10.1111/j.1365-2966.2012.20967.x`](http://doi.org/10.1111/j.1365-2966.2012.20967.x)

(ref: Bae2015) Bae, J., Hartmann, L., & Zhu, Z. 2015, ApJ, 805, 15, doi: [`10.1088/0004-637X/805/1/15`](http://doi.org/10.1088/0004-637X/805/1/15)

(ref: Bae2023) Bae, J., Isella, A., Zhu, Z., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 423, doi: [`10.48550/arXiv.2210.13314`](http://doi.org/10.48550/arXiv.2210.13314)

(ref: Bae2018) Bae, J., & Zhu, Z. 2018, ApJ, 859, 119, doi: [`10.3847/1538-4357/aabf93`](http://doi.org/10.3847/1538-4357/aabf93)

(ref: Bae2016) Bae, J., Zhu, Z., & Hartmann, L. 2016, ApJ, 819, 134, doi: [`10.3847/0004-637X/819/2/134`](http://doi.org/10.3847/0004-637X/819/2/134)

(ref: Bai2010a) Bai, X.-N., & Stone, J. M. 2010a, ApJ, 722, 1437, doi: [`10.1088/0004-637X/722/2/1437`](http://doi.org/10.1088/0004-637X/722/2/1437)

(ref: Bai2010b) —. 2010b, ApJL, 722, L220, doi: [`10.1088/2041-8205/722/2/L220`](http://doi.org/10.1088/2041-8205/722/2/L220)

(ref: Ballabio2021) Ballabio, G., Nealon, R., Alexander, R. D., et al. 2021, MNRAS, 504, 888, doi: [`10.1093/mnras/stab922`](http://doi.org/10.1093/mnras/stab922)

(ref: Barraza_exoALMA) Barraza-Alfaro, M. 2025, ApJL, TBD

(ref: Barraza2024) Barraza-Alfaro, M., Flock, M., & Henning, T. 2024, A&A, 683, A16, doi: [`10.1051/0004-6361/202347726`](http://doi.org/10.1051/0004-6361/202347726)

(ref: Baruteau2016) Baruteau, C., & Zhu, Z. 2016, MNRAS, 458, 3927, doi: [`10.1093/mnras/stv2527`](http://doi.org/10.1093/mnras/stv2527)

(ref: Baruteau2019) Baruteau, C., Barraza, M., Pérez, S., et al. 2019, MNRAS, 486, 304, doi: [`10.1093/mnras/stz802`](http://doi.org/10.1093/mnras/stz802)

(ref: Benisty2015) Benisty, M., Juhasz, A., Boccaletti, A., et al. 2015, A&A, 578, L6, doi: [`10.1051/0004-6361/201526011`](http://doi.org/10.1051/0004-6361/201526011)

(ref: Benisty2018) Benisty, M., Juhász, A., Facchini, S., et al. 2018, A&A, 619, A171, doi: [`10.1051/0004-6361/201833913`](http://doi.org/10.1051/0004-6361/201833913)

(ref: Sphere2019) Beuzit, J. L., Vigan, A., Mouillet, D., et al. 2019, A&A, 631, A155, doi: [`10.1051/0004-6361/201935251`](http://doi.org/10.1051/0004-6361/201935251)

(ref: Birnstiel2013) Birnstiel, T., Dullemond, C. P., & Pinilla, P. 2013, A&A, 550, L8, doi: [`10.1051/0004-6361/201220847`](http://doi.org/10.1051/0004-6361/201220847)

(ref: Birnstiel2010b) Birnstiel, T., Ricci, L., Trotta, F., et al. 2010, A&A, 516, L14, doi: [`10.1051/0004-6361/201014893`](http://doi.org/10.1051/0004-6361/201014893)

(ref: Boehler2018) Boehler, Y., Ricci, L., Weaver, E., et al. 2018, ApJ, 853, 162, doi: [`10.3847/1538-4357/aaa19c`](http://doi.org/10.3847/1538-4357/aaa19c)

(ref: Boehler2021) Boehler, Y., Ménard, F., Robert, C. M. T., et al. 2021, A&A, 650, A59, doi: [`10.1051/0004-6361/202040089`](http://doi.org/10.1051/0004-6361/202040089)

(ref: Bohn2022) Bohn, A. J., Benisty, M., Perraut, K., et al. 2022, A&A, 658, A183, doi: [`10.1051/0004-6361/202142070`](http://doi.org/10.1051/0004-6361/202142070)

(ref: Brown2009) Brown, J. M., Blake, G. A., Qi, C., et al. 2009, ApJ, 704, 496, doi: [`10.1088/0004-637X/704/1/496`](http://doi.org/10.1088/0004-637X/704/1/496)

(ref: Brown2007) Brown, J. M., Blake, G. A., Dullemond, C. P., et al. 2007, ApJL, 664, L107, doi: [`10.1086/520808`](http://doi.org/10.1086/520808)

(ref: Bruderer2013) Bruderer, S. 2013, A&A, 559, A46, doi: [`10.1051/0004-6361/201321171`](http://doi.org/10.1051/0004-6361/201321171)

(ref: Bruderer2014) Bruderer, S., van der Marel, N., van Dishoeck, E. F., & van Kempen, T. A. 2014, A&A, 562, A26, doi: [`10.1051/0004-6361/201322857`](http://doi.org/10.1051/0004-6361/201322857)

(ref: Calcino2020) Calcino, J., Christiaens, V., Price, D. J., et al. 2020, MNRAS, 498, 639, doi: [`10.1093/mnras/staa2468`](http://doi.org/10.1093/mnras/staa2468)

(ref: Casassus2022) Casassus, S., Cárcamo, M., Hales, A., Weber, P., & Dent, B. 2022, ApJL, 933, L4, doi: [`10.3847/2041-8213/ac75e8`](http://doi.org/10.3847/2041-8213/ac75e8)

(ref: Casassus2019) Casassus, S., & Pérez, S. 2019, ApJL, 883, L41, doi: [`10.3847/2041-8213/ab4425`](http://doi.org/10.3847/2041-8213/ab4425)

(ref: Casassus2013) Casassus, S., van der Plas, G. M., Perez, S., et al. 2013, Nature, 493, 191, doi: [`10.1038/nature11769`](http://doi.org/10.1038/nature11769)

(ref: Casassus2019b) Casassus, S., Marino, S., Lyra, W., et al. 2019, MNRAS, 483, 3278, doi: [`10.1093/mnras/sty3269`](http://doi.org/10.1093/mnras/sty3269)

(ref: Casassus2021) Casassus, S., Christiaens, V., Cárcamo, M., et al. 2021, MNRAS, 507, 3789, doi: [`10.1093/mnras/stab2359`](http://doi.org/10.1093/mnras/stab2359)

(ref: Cazzoletti2018) Cazzoletti, P., van Dishoeck, E. F., Pinilla, P., et al. 2018, A&A, 619, A161, doi: [`10.1051/0004-6361/201834006`](http://doi.org/10.1051/0004-6361/201834006)

(ref: Cuello2020) Cuello, N., Louvet, F., Mentiplay, D., et al. 2020, MNRAS, 491, 504, doi: [`10.1093/mnras/stz2938`](http://doi.org/10.1093/mnras/stz2938)

(ref: Cugno2019) Cugno, G., Quanz, S. P., Hunziker, S., et al. 2019, A&A, 622, A156, doi: [`10.1051/0004-6361/201834170`](http://doi.org/10.1051/0004-6361/201834170)

(ref: Cugno2024) Cugno, G., Leisenring, J., Wagner, K. R., et al. 2024, AJ, 167, 182, doi: [`10.3847/1538-3881/ad1ffc`](http://doi.org/10.3847/1538-3881/ad1ffc)

(ref: Curone_exoALMA) Curone, P., Facchini, S., Andrews, S. M., & Testi, L. 2025, ApJL, TBD

(ref: Boer2021) de Boer, J., Ginski, C., Chauvin, G., et al. 2021, A&A, 649, A25, doi: [`10.1051/0004-6361/201936787`](http://doi.org/10.1051/0004-6361/201936787)

(ref: Dipierro2015) Dipierro, G., Price, D., Laibe, G., et al. 2015, MNRAS, 453, L73, doi: [`10.1093/mnrasl/slv105`](http://doi.org/10.1093/mnrasl/slv105)

(ref: Dipierro2018) Dipierro, G., Ricci, L., Pérez, L., et al. 2018, MNRAS, 475, 5296, doi: [`10.1093/mnras/sty181`](http://doi.org/10.1093/mnras/sty181)

(ref: Dong2017a) Dong, R., & Fung, J. 2017, ApJ, 835, 38, doi: [`10.3847/1538-4357/835/1/38`](http://doi.org/10.3847/1538-4357/835/1/38)

(ref: Dong2015b) Dong, R., Hall, C., Rice, K., & Chiang, E. 2015a, ApJL, 812, L32, doi: [`10.1088/2041-8205/812/2/L32`](http://doi.org/10.1088/2041-8205/812/2/L32)

(ref: Dong2017) Dong, R., Li, S., Chiang, E., & Li, H. 2017a, ApJ, 843, 127, doi: [`10.3847/1538-4357/aa72f2`](http://doi.org/10.3847/1538-4357/aa72f2)

(ref: Dong2018) —. 2018a, ApJ, 866, 110, doi: [`10.3847/1538-4357/aadadd`](http://doi.org/10.3847/1538-4357/aadadd)

(ref: Dong2015a) Dong, R., Zhu, Z., Rafikov, R. R., & Stone, J. M. 2015b, ApJL, 809, L5, doi: [`10.1088/2041-8205/809/1/L5`](http://doi.org/10.1088/2041-8205/809/1/L5)

(ref: Dong2017b) Dong, R., van der Marel, N., Hashimoto, J., et al. 2017b, ApJ, 836, 201, doi: [`10.3847/1538-4357/aa5abf`](http://doi.org/10.3847/1538-4357/aa5abf)

(ref: Dong2018_mwc) Dong, R., Liu, S.-y., Eisner, J., et al. 2018b, ApJ, 860, 124, doi: [`10.3847/1538-4357/aac6cb`](http://doi.org/10.3847/1538-4357/aac6cb)

(ref: Dullemond2012) Dullemond, C. P., Juhasz, A., Pohl, A., et al. 2012, RADMC-3D: A multi-purpose radiative transfer tool, Astrophysics Source Code Library, record ascl:1202.015

(ref: Facchini2017) Facchini, S., Birnstiel, T., Bruderer, S., & van Dishoeck, E. F. 2017, A&A, 605, A16, doi: [`10.1051/0004-6361/201630329`](http://doi.org/10.1051/0004-6361/201630329)

(ref: Flock2017a) Flock, M., Fromang, S., Turner, N. J., & Benisty, M. 2017, ApJ, 835, 230, doi: [`10.3847/1538-4357/835/2/230`](http://doi.org/10.3847/1538-4357/835/2/230)

(ref: Flock2015) Flock, M., Ruge, J. P., Dzyurkevich, N., et al. 2015, A&A, 574, A68, doi: [`10.1051/0004-6361/201424693`](http://doi.org/10.1051/0004-6361/201424693)

(ref: Flock2020) Flock, M., Turner, N. J., Nelson, R. P., et al. 2020, ApJ, 897, 155, doi: [`10.3847/1538-4357/ab9641`](http://doi.org/10.3847/1538-4357/ab9641)

(ref: Follette2023) Follette, K. B., Close, L. M., Males, J. R., et al. 2023, AJ, 165, 225, doi: [`10.3847/1538-3881/acc183`](http://doi.org/10.3847/1538-3881/acc183)

(ref: Fu2014b) Fu, W., Li, H., Lubow, S., Li, S., & Liang, E. 2014, ApJL, 795, L39, doi: [`10.1088/2041-8205/795/2/L39`](http://doi.org/10.1088/2041-8205/795/2/L39)

(ref: Fung2015) Fung, J., & Dong, R. 2015, ApJL, 815, L21, doi: [`10.1088/2041-8205/815/2/L21`](http://doi.org/10.1088/2041-8205/815/2/L21)

(ref: Gaia2023) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1, doi: [`10.1051/0004-6361/202243940`](http://doi.org/10.1051/0004-6361/202243940)

(ref: Galloway_exoALMA) Galloway-Sprietsma, M., Bae, J., & Izquierdo, A. 2025, ApJL, TBD

(ref: Galloway2023) Galloway-Sprietsma, M., Bae, J., Teague, R., et al. 2023, ApJ, 950, 147, doi: [`10.3847/1538-4357/accae4`](http://doi.org/10.3847/1538-4357/accae4)

(ref: Garg2021) Garg, H., Pinte, C., Christiaens, V., et al. 2021, MNRAS, 504, 782, doi: [`10.1093/mnras/stab800`](http://doi.org/10.1093/mnras/stab800)

(ref: Garufi2013) Garufi, A., Quanz, S. P., Avenhaus, H., et al. 2013, A&A, 560, A105, doi: [`10.1051/0004-6361/201322429`](http://doi.org/10.1051/0004-6361/201322429)

(ref: Garufi2018) Garufi, A., Benisty, M., Pinilla, P., et al. 2018, A&A, 620, A94, doi: [`10.1051/0004-6361/201833872`](http://doi.org/10.1051/0004-6361/201833872)

(ref: Grady2009) Grady, C. A., Schneider, G., Sitko, M. L., et al. 2009, ApJ, 699, 1822, doi: [`10.1088/0004-637X/699/2/1822`](http://doi.org/10.1088/0004-637X/699/2/1822)

(ref: Grady2013) Grady, C. A., Muto, T., Hashimoto, J., et al. 2013, ApJ, 762, 48, doi: [`10.1088/0004-637X/762/1/48`](http://doi.org/10.1088/0004-637X/762/1/48)

(ref: Guerra2024) Guerra-Alvarado, O. M., Carrasco-González, C., Macı́as, E., et al. 2024, A&A, 686, A298, doi: [`10.1051/0004-6361/202349046`](http://doi.org/10.1051/0004-6361/202349046)

(ref: Hall2020) Hall, C., Dong, R., Teague, R., et al. 2020, ApJ, 904, 148, doi: [`10.3847/1538-4357/abac17`](http://doi.org/10.3847/1538-4357/abac17)

(ref: Huang2019) Huang, P., Dong, R., Li, H., Li, S., & Ji, J. 2019, ApJL, 883, L39, doi: [`10.3847/2041-8213/ab40c4`](http://doi.org/10.3847/2041-8213/ab40c4)

(ref: Isella2010) Isella, A., Natta, A., Wilner, D., Carpenter, J. M., & Testi, L. 2010, ApJ, 725, 1735, doi: [`10.1088/0004-637X/725/2/1735`](http://doi.org/10.1088/0004-637X/725/2/1735)

(ref: Izquierdo2022) Izquierdo, A. F., Facchini, S., Rosotti, G. P., van Dishoeck, E. F., & Testi, L. 2022, ApJ, 928, 2, doi: [`10.3847/1538-4357/ac474d`](http://doi.org/10.3847/1538-4357/ac474d)

(ref: Izquierdo_exoALMA) Izquierdo, A. F., Stadler, J., Bae, J., et al. 2025, ApJL, TBD

(ref: Izquierdo2021) Izquierdo, A. F., Testi, L., Facchini, S., Rosotti, G. P., & van Dishoeck, E. F. 2021, A&A, 650, A179, doi: [`10.1051/0004-6361/202140779`](http://doi.org/10.1051/0004-6361/202140779)

(ref: Khalafinejad2016) Khalafinejad, S., Maaskant, K. M., Mariñas, N., & Tielens, A. G. G. M. 2016, A&A, 587, A62, doi: [`10.1051/0004-6361/201423984`](http://doi.org/10.1051/0004-6361/201423984)

(ref: Kraus2017) Kraus, S., Kreplin, A., Fukugawa, M., et al. 2017, ApJL, 848, L11, doi: [`10.3847/2041-8213/aa8edc`](http://doi.org/10.3847/2041-8213/aa8edc)

(ref: Kuznetsova2022) Kuznetsova, A., Bae, J., Hartmann, L., & Mac Low, M.-M. 2022, ApJ, 928, 92, doi: [`10.3847/1538-4357/ac54a8`](http://doi.org/10.3847/1538-4357/ac54a8)

(ref: Law2021) Law, C. J., Loomis, R. A., Teague, R., et al. 2021, ApJS, 257, 3, doi: [`10.3847/1538-4365/ac1434`](http://doi.org/10.3847/1538-4365/ac1434)

(ref: Leemker2022) Leemker, M., Booth, A. S., van Dishoeck, E. F., et al. 2022, A&A, 663, A23, doi: [`10.1051/0004-6361/202243229`](http://doi.org/10.1051/0004-6361/202243229)

(ref: Li2000) Li, H., Finn, J. M., Lovelace, R. V. E., & Colgate, S. A. 2000, ApJ, 533, 1023, doi: [`10.1086/308693`](http://doi.org/10.1086/308693)

(ref: Lin2012) Lin, M.-K. 2012, MNRAS, 426, 3211, doi: [`10.1111/j.1365-2966.2012.21955.x`](http://doi.org/10.1111/j.1365-2966.2012.21955.x)

(ref: Loomis_exoALMA) Loomis, R. 2025, ApJL, TBD

(ref: Lovelace1999) Lovelace, R. V. E., Li, H., Colgate, S. A., & Nelson, A. F. 1999, ApJ, 513, 805, doi: [`10.1086/306900`](http://doi.org/10.1086/306900)

(ref: Lyra2014) Lyra, W. 2014, ApJ, 789, 77, doi: [`10.1088/0004-637X/789/1/77`](http://doi.org/10.1088/0004-637X/789/1/77)

(ref: Macintosh2014) Macintosh, B., Graham, J. R., Ingraham, P., et al. 2014, Proceedings of the National Academy of Science, 111, 12661, doi: [`10.1073/pnas.1304215111`](http://doi.org/10.1073/pnas.1304215111)

(ref: Maire2017) Maire, A. L., Stolker, T., Messina, S., et al. 2017, A&A, 601, A134, doi: [`10.1051/0004-6361/201629896`](http://doi.org/10.1051/0004-6361/201629896)

(ref: Manger2020) Manger, N., Klahr, H., Kley, W., & Flock, M. 2020, MNRAS, 499, 1841, doi: [`10.1093/mnras/staa2943`](http://doi.org/10.1093/mnras/staa2943)

(ref: Marcus2016) Marcus, P. S., Pei, S., Jiang, C.-H., & Barranco, J. A. 2016, ApJ, 833, 148, doi: [`10.3847/1538-4357/833/2/148`](http://doi.org/10.3847/1538-4357/833/2/148)

(ref: Marcus2015) Marcus, P. S., Pei, S., Jiang, C.-H., et al. 2015, ApJ, 808, 87, doi: [`10.1088/0004-637X/808/1/87`](http://doi.org/10.1088/0004-637X/808/1/87)

(ref: Marcus2013) Marcus, P. S., Pei, S., Jiang, C.-H., & Hassanzadeh, P. 2013, , 111, 084501, doi: [`10.1103/PhysRevLett.111.084501`](http://doi.org/10.1103/PhysRevLett.111.084501)

(ref: Marino2015) Marino, S., Casassus, S., Perez, S., et al. 2015, ApJ, 813, 76, doi: [`10.1088/0004-637X/813/1/76`](http://doi.org/10.1088/0004-637X/813/1/76)

(ref: Marr2022) Marr, M., & Dong, R. 2022, ApJ, 930, 80, doi: [`10.3847/1538-4357/ac63ab`](http://doi.org/10.3847/1538-4357/ac63ab)

(ref: Mason2001) Mason, B. D., Wycoff, G. L., Hartkopf, W. I., Douglass, G. G., & Worley, C. E. 2001, AJ, 122, 3466, doi: [`10.1086/323920`](http://doi.org/10.1086/323920)

(ref: Masset2002) Masset, F. S. 2002, A&A, 387, 605, doi: [`10.1051/0004-6361:20020240`](http://doi.org/10.1051/0004-6361:20020240)

(ref: Meheut2010) Meheut, H., Casse, F., Varniere, P., & Tagger, M. 2010, A&A, 516, A31, doi: [`10.1051/0004-6361/201014000`](http://doi.org/10.1051/0004-6361/201014000)

(ref: Meheut2012a) Meheut, H., Yu, C., & Lai, D. 2012, MNRAS, 422, 2399, doi: [`10.1111/j.1365-2966.2012.20789.x`](http://doi.org/10.1111/j.1365-2966.2012.20789.x)

(ref: Mignone2007) Mignone, A., Bodo, G., Massaglia, S., et al. 2007, ApJS, 170, 228, doi: [`10.1086/513316`](http://doi.org/10.1086/513316)

(ref: Miranda2017) Miranda, R., Li, H., Li, S., & Jin, S. 2017, ApJ, 835, 118, doi: [`10.3847/1538-4357/835/2/118`](http://doi.org/10.3847/1538-4357/835/2/118)

(ref: Muller2012) Müller, T. W. A., Kley, W., & Meru, F. 2012, A&A, 541, A123, doi: [`10.1051/0004-6361/201118737`](http://doi.org/10.1051/0004-6361/201118737)

(ref: Muro2020) Muro-Arena, G. A., Ginski, C., Dominik, C., et al. 2020, A&A, 636, L4, doi: [`10.1051/0004-6361/202037656`](http://doi.org/10.1051/0004-6361/202037656)

(ref: Muto2012) Muto, T., Grady, C. A., Hashimoto, J., et al. 2012, ApJL, 748, L22, doi: [`10.1088/2041-8205/748/2/L22`](http://doi.org/10.1088/2041-8205/748/2/L22)

(ref: Norfolk2022) Norfolk, B. J., Pinte, C., Calcino, J., et al. 2022, ApJL, 936, L4, doi: [`10.3847/2041-8213/ac85ed`](http://doi.org/10.3847/2041-8213/ac85ed)

(ref: Perez2014) Pérez, L. M., Isella, A., Carpenter, J. M., & Chandler, C. J. 2014, ApJL, 783, L13, doi: [`10.1088/2041-8205/783/1/L13`](http://doi.org/10.1088/2041-8205/783/1/L13)

(ref: perez2018) Pérez, L. M., Benisty, M., Andrews, S. M., et al. 2018, ApJL, 869, L50, doi: [`10.3847/2041-8213/aaf745`](http://doi.org/10.3847/2041-8213/aaf745)

(ref: Pfeil2021) Pfeil, T., & Klahr, H. 2021, ApJ, 915, 130, doi: [`10.3847/1538-4357/ac0054`](http://doi.org/10.3847/1538-4357/ac0054)

(ref: Pietu2003) Piétu, V., Dutrey, A., & Kahane, C. 2003, A&A, 398, 565, doi: [`10.1051/0004-6361:20021551`](http://doi.org/10.1051/0004-6361:20021551)

(ref: Pinilla2012b) Pinilla, P., Benisty, M., & Birnstiel, T. 2012a, A&A, 545, A81, doi: [`10.1051/0004-6361/201219315`](http://doi.org/10.1051/0004-6361/201219315)

(ref: Pinilla2012a) Pinilla, P., Birnstiel, T., Ricci, L., et al. 2012b, A&A, 538, A114, doi: [`10.1051/0004-6361/201118204`](http://doi.org/10.1051/0004-6361/201118204)

(ref: Pinte2022) Pinte, C., Teague, R., Flaherty, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 645, doi: [`10.48550/arXiv.2203.09528`](http://doi.org/10.48550/arXiv.2203.09528)

(ref: Pinte2018) Pinte, C., Price, D. J., Ménard, F., et al. 2018, ApJL, 860, L13, doi: [`10.3847/2041-8213/aac6dc`](http://doi.org/10.3847/2041-8213/aac6dc)

(ref: Pinte2019) Pinte, C., van der Plas, G., Ménard, F., et al. 2019, Nature Astronomy, 3, 1109, doi: [`10.1038/s41550-019-0852-6`](http://doi.org/10.1038/s41550-019-0852-6)

(ref: Pinte2020) Pinte, C., Price, D. J., Ménard, F., et al. 2020, ApJL, 890, L9, doi: [`10.3847/2041-8213/ab6dda`](http://doi.org/10.3847/2041-8213/ab6dda)

(ref: Price2018) Price, D. J., Cuello, N., Pinte, C., et al. 2018, MNRAS, 477, 1270, doi: [`10.1093/mnras/sty647`](http://doi.org/10.1093/mnras/sty647)

(ref: Quiroz2022) Quiroz, J., Wallack, N. L., Ren, B., et al. 2022, ApJL, 924, L4, doi: [`10.3847/2041-8213/ac3e62`](http://doi.org/10.3847/2041-8213/ac3e62)

(ref: Raettig2015) Raettig, N., Klahr, H., & Lyra, W. 2015, ApJ, 804, 35, doi: [`10.1088/0004-637X/804/1/35`](http://doi.org/10.1088/0004-637X/804/1/35)

(ref: Raettig2021) Raettig, N., Lyra, W., & Klahr, H. 2021, ApJ, 913, 92, doi: [`10.3847/1538-4357/abf739`](http://doi.org/10.3847/1538-4357/abf739)

(ref: Ragusa2017) Ragusa, E., Dipierro, G., Lodato, G., Laibe, G., & Price, D. J. 2017, MNRAS, 464, 1449, doi: [`10.1093/mnras/stw2456`](http://doi.org/10.1093/mnras/stw2456)

(ref: Ragusa2024) Ragusa, E., Lynch, E., Laibe, G., Longarini, C., & Ceppi, S. 2024, A&A, 686, A264, doi: [`10.1051/0004-6361/202449583`](http://doi.org/10.1051/0004-6361/202449583)

(ref: Reggiani2018) Reggiani, M., Christiaens, V., Absil, O., et al. 2018, A&A, 611, A74, doi: [`10.1051/0004-6361/201732016`](http://doi.org/10.1051/0004-6361/201732016)

(ref: Ren2020) Ren, B., Dong, R., van Holstein, R. G., et al. 2020, ApJL, 898, L38, doi: [`10.3847/2041-8213/aba43e`](http://doi.org/10.3847/2041-8213/aba43e)

(ref: Ren2023) Ren, B. B., Benisty, M., Ginski, C., et al. 2023, A&A, 680, A114, doi: [`10.1051/0004-6361/202347353`](http://doi.org/10.1051/0004-6361/202347353)

(ref: Ribas2024) Ribas, Á., Clarke, C. J., & Zagaria, F. 2024, MNRAS, 532, 1752, doi: [`10.1093/mnras/stae1534`](http://doi.org/10.1093/mnras/stae1534)

(ref: Richard2013) Richard, S., Barge, P., & Le Dizès, S. 2013, A&A, 559, A30, doi: [`10.1051/0004-6361/201322175`](http://doi.org/10.1051/0004-6361/201322175)

(ref: Richard2016) Richard, S., Nelson, R. P., & Umurhan, O. M. 2016, MNRAS, 456, 3571, doi: [`10.1093/mnras/stv2898`](http://doi.org/10.1093/mnras/stv2898)

(ref: Robert2020) Robert, C. M. T., Méheut, H., & Ménard, F. 2020, A&A, 641, A128, doi: [`10.1051/0004-6361/201937414`](http://doi.org/10.1051/0004-6361/201937414)

(ref: Rosotti2021) Rosotti, G. P., Ilee, J. D., Facchini, S., et al. 2021, MNRAS, 501, 3427, doi: [`10.1093/mnras/staa3869`](http://doi.org/10.1093/mnras/staa3869)

(ref: Rosotti2016) Rosotti, G. P., Juhasz, A., Booth, R. A., & Clarke, C. J. 2016, MNRAS, 459, 2790, doi: [`10.1093/mnras/stw691`](http://doi.org/10.1093/mnras/stw691)

(ref: Rosotti2020a) Rosotti, G. P., Benisty, M., Juhász, A., et al. 2020, MNRAS, 491, 1335, doi: [`10.1093/mnras/stz3090`](http://doi.org/10.1093/mnras/stz3090)

(ref: Shakura1973) Shakura, N. I., & Sunyaev, R. A. 1973, A&A, 500, 33

(ref: Shen2020) Shen, B.-T., Tang, Y.-W., & Koch, P. M. 2020, ApJ, 904, 125, doi: [`10.3847/1538-4357/abbd9f`](http://doi.org/10.3847/1538-4357/abbd9f)

(ref: Stadler_exoALMA) Stadler, J., Benisty, M., & Winter, A. J. 2025, ApJL, TBD

(ref: Stadler2023) Stadler, J., Benisty, M., Izquierdo, A., et al. 2023, A&A, 670, L1, doi: [`10.1051/0004-6361/202245381`](http://doi.org/10.1051/0004-6361/202245381)

(ref: Stammler2019) Stammler, S. M., Drążkowska, J., Birnstiel, T., et al. 2019, ApJL, 884, L5, doi: [`10.3847/2041-8213/ab4423`](http://doi.org/10.3847/2041-8213/ab4423)

(ref: Stolker2016) Stolker, T., Dominik, C., Avenhaus, H., et al. 2016, A&A, 595, A113, doi: [`10.1051/0004-6361/201528039`](http://doi.org/10.1051/0004-6361/201528039)

(ref: Stolker2017) Stolker, T., Sitko, M., Lazareff, B., et al. 2017, ApJ, 849, 143, doi: [`10.3847/1538-4357/aa886a`](http://doi.org/10.3847/1538-4357/aa886a)

(ref: Tang2012) Tang, Y. W., Guilloteau, S., Piétu, V., et al. 2012, A&A, 547, A84, doi: [`10.1051/0004-6361/201219414`](http://doi.org/10.1051/0004-6361/201219414)

(ref: Tang2017) Tang, Y.-W., Guilloteau, S., Dutrey, A., et al. 2017, ApJ, 840, 32, doi: [`10.3847/1538-4357/aa6af7`](http://doi.org/10.3847/1538-4357/aa6af7)

(ref: eddy) Teague, R. 2019, Journal of Open Source Software, 4, 1220, doi: [`10.21105/joss.01220`](http://doi.org/10.21105/joss.01220)

(ref: Teague2019a) Teague, R., Bae, J., & Bergin, E. A. 2019a, Nature, 574, 378, doi: [`10.1038/s41586-019-1642-0`](http://doi.org/10.1038/s41586-019-1642-0)

(ref: Teague2018a) Teague, R., Bae, J., Bergin, E. A., Birnstiel, T., & Foreman-Mackey, D. 2018, ApJL, 860, L12, doi: [`10.3847/2041-8213/aac6d7`](http://doi.org/10.3847/2041-8213/aac6d7)

(ref: Teague2019Spiral) Teague, R., Bae, J., Huang, J., & Bergin, E. A. 2019b, ApJL, 884, L56, doi: [`10.3847/2041-8213/ab4a83`](http://doi.org/10.3847/2041-8213/ab4a83)

(ref: Teague_exoALMA) Teague, R., Benisty, M., Facchini, S., Fukagawa, M., & Pinte, C. 2025, ApJL, TBD

(ref: bettermoments) Teague, R., & Foreman-Mackey, D. 2018, Research Notes of the American Astronomical Society, 2, 173, doi: [`10.3847/2515-5172/aae265`](http://doi.org/10.3847/2515-5172/aae265)

(ref: Teague2021) Teague, R., Bae, J., Aikawa, Y., et al. 2021, ApJS, 257, 18, doi: [`10.3847/1538-4365/ac1438`](http://doi.org/10.3847/1538-4365/ac1438)

(ref: Teague2022) Teague, R., Bae, J., Andrews, S. M., et al. 2022, ApJ, 936, 163, doi: [`10.3847/1538-4357/ac88ca`](http://doi.org/10.3847/1538-4357/ac88ca)

(ref: Trapman2019) Trapman, L., Facchini, S., Hogerheijde, M. R., van Dishoeck, E. F., & Bruderer, S. 2019, A&A, 629, A79, doi: [`10.1051/0004-6361/201834723`](http://doi.org/10.1051/0004-6361/201834723)

(ref: Marel2016) van der Marel, N., Cazzoletti, P., Pinilla, P., & Garufi, A. 2016a, ApJ, 832, 178, doi: [`10.3847/0004-637X/832/2/178`](http://doi.org/10.3847/0004-637X/832/2/178)

(ref: Marel2016a) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2016b, A&A, 585, A58, doi: [`10.1051/0004-6361/201526988`](http://doi.org/10.1051/0004-6361/201526988)

(ref: Marel2013) —. 2013, Science, 340, 1199, doi: [`10.1126/science.1236770`](http://doi.org/10.1126/science.1236770)

(ref: Marel2021) Van der Marel, N., Birnstiel, T., Garufi, A., et al. 2021, AJ, 161, 33, doi: [`10.3847/1538-3881/abc3ba`](http://doi.org/10.3847/1538-3881/abc3ba)

(ref: Plas2017) van der Plas, G., Ménard, F., Canovas, H., et al. 2017, A&A, 607, A55, doi: [`10.1051/0004-6361/201731392`](http://doi.org/10.1051/0004-6361/201731392)

(ref: Wagner2019) Wagner, K., Stone, J. M., Spalding, E., et al. 2019, ApJ, 882, 20, doi: [`10.3847/1538-4357/ab32ea`](http://doi.org/10.3847/1538-4357/ab32ea)

(ref: Wagner2023) Wagner, K., Stone, J., Skemer, A., et al. 2023, Nature Astronomy, 7, 1208, doi: [`10.1038/s41550-023-02028-3`](http://doi.org/10.1038/s41550-023-02028-3)

(ref: Weber2019) Weber, P., Pérez, S., Benı́tez-Llambay, P., et al. 2019, ApJ, 884, 178, doi: [`10.3847/1538-4357/ab412f`](http://doi.org/10.3847/1538-4357/ab412f)

(ref: Woelfer2021) Wölfer, L., Facchini, S., Kurtovic, N. T., et al. 2021, A&A, 648, A19, doi: [`10.1051/0004-6361/202039469`](http://doi.org/10.1051/0004-6361/202039469)

(ref: Woelfer2023) Wölfer, L., Facchini, S., van der Marel, N., et al. 2023, A&A, 670, A154, doi: [`10.1051/0004-6361/202243601`](http://doi.org/10.1051/0004-6361/202243601)

(ref: Yang2023) Yang, Y., Liu, H. B., Muto, T., et al. 2023, ApJ, 948, 110, doi: [`10.3847/1538-4357/acc325`](http://doi.org/10.3847/1538-4357/acc325)

(ref: Yen2020) Yen, H.-W., & Gu, P.-G. 2020, ApJ, 905, 89, doi: [`10.3847/1538-4357/abc55a`](http://doi.org/10.3847/1538-4357/abc55a)

(ref: Yu2021) Yu, H., Teague, R., Bae, J., & Öberg, K. 2021, ApJL, 920, L33, doi: [`10.3847/2041-8213/ac283e`](http://doi.org/10.3847/2041-8213/ac283e)

(ref: Zhang2014) Zhang, K., Isella, A., Carpenter, J. M., & Blake, G. A. 2014, ApJ, 791, 42, doi: [`10.1088/0004-637X/791/1/42`](http://doi.org/10.1088/0004-637X/791/1/42)

(ref: Zurlo2020) Zurlo, A., Cugno, G., Montesinos, M., et al. 2020, A&A, 633, A119, doi: [`10.1051/0004-6361/201936891`](http://doi.org/10.1051/0004-6361/201936891)

</paper>

Write the methods card for this paper.