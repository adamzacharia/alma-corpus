# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...990L..72K\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...990L..72K",
 "title": "Cosmic Cascades: How Disk Substructure Regulates the Flow of Water to Inner Planetary Systems",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Krijt, Sebastiaan",
 "n_authors": 20,
 "arxiv_id": "2508.10402",
 "doi": "10.3847/2041-8213/adfbe3",
 "alma_projects_linked_by_archive": [
  "2011.0.00531.S",
  "2013.1.00226.S",
  "2013.1.00366.S",
  "2013.1.00498.S",
  "2013.1.00601.S",
  "2013.1.00694.S",
  "2013.1.00798.S",
  "2015.1.00486.S",
  "2015.1.00964.S",
  "2016.1.00484.L",
  "2016.1.01164.S"
 ]
}
```

Paper text:
<paper>
# Cosmic cascades: How disk substructure regulates the flow of water to inner planetary systems

## Abstract

The influx of icy pebbles to the inner regions of protoplanetary disks constitutes a fundamental ingredient in most planet formation theories. The observational determination of the magnitude of this pebble flux and its dependence on disk substructure (disk gaps as pebble traps) would be a significant step forward. In this work we analyze a sample of 21 T Tauri disks (with ages $\approx 0.5{-}2\mathrm{~Myr}$) using JWST/MIRI spectra homogeneously reduced with the JDISCS pipeline and high-angular-resolution ALMA continuum data. We find that the 1500/6000 K water line flux ratio measured with JWST - a tracer of cold water vapor and pebble drift near the snowline - correlates with the radial location of the innermost dust gap in ALMA continuum observations (ranging from 8.7 to 69 au), confirming predictions from recent models that study connections between the inner and outer disk reservoirs. We develop a population synthesis exploration of pebble drift in gapped disks and find a good match to the observed trend for early and relatively effective gaps, while scenarios where pebble drift happens quickly, gaps are very leaky, or where gaps form late are disfavored on a population level. Inferred snowline pebble mass fluxes (ranging between $10^{-6}$ and $10^{-3}~M_\oplus/\mathrm{yr}$ depending on gap position) are comparable to fluxes used in pebble accretion studies and those proposed for the inner Solar System, while system-to-system variations suggest differences in the emerging planetary system architectures and water budgets.

show\]s.krijt@exeter.ac.uk

# Introduction

The journey of water from molecular clouds to protoplanetary disks and ultimately planets and potential biospheres is long and complex (cite: vandishoeck_2014; oberg_bergin_2021). A critical step that occurs during the protoplanetary disk phase is the transport of water ice to the terrestrial planet formation zone through aerodynamic drift of solids (cite: whipple1972) - a fundamental process long proposed for the Solar System (cite: morfill84; stevenson88; cyr98) that could eventually be linked to the formation of potentially habitable planets (cite: krijt_2023; lichtenberg_2023).

Seminal results on water transport in disks were achieved with the Infrared Spectrograph on the Spitzer Space Telescope (cite: irs), by finding (anti-)correlations between emission and the disk dust mass or size, suggestive of trapping of water ice beyond the snowline in massive or large disks (cite: najita_2013; banzatti_2020). The MIRI spectrograph on JWST (cite: miri; miri2; miri3) now probes physical and chemical conditions in the inner few au of planet-forming disks with unprecedented combination of high spectral resolution and sensitivity at infrared wavelengths. Analysis of the first MIRI-MRS disk spectra in Cycle 1 revealed a rich chemical diversity ranging from water-dominated to hydrocarbon-rich systems (cite: tabone_2023; grant23; banzatti_2023; kamp2023; pontoppidan_2024; henning2024; arulanantham2025). The sharper spectral view of MIRI has already improved upon previous Spitzer results by revealing that trends with dust disk radii are due to a cold ($\sim$170–400$\mathrm{~K}$) water vapor reservoir that is enhanced in compact disks that are considered to be drift-dominated (cite: banzatti_2023; romero-mirza_2024; banzatti_2025), supporting early predictions of ice delivery to the snowline by pebble drift (cite: cieslacuzzi2006). However, recent modeling works show that more than traced by the outer disk radius, pebble drift into the snowline region should be regulated by the radial location and depth of disk gaps acting as pebble traps (cite: kalyaan_2021; kalyaan_2023; easterwood_2024; mah_2024). A recent analysis of 8 compact disks of intermediate sizes (40–60 au) indeed finds a range in cold water enrichment that does not simply depend on the outer disk size (cite: temmink_2025)[^1], supporting discussions of larger samples in (cite: banzatti_2025; gasman2025).

In the past 10 years, ALMA has indeed revealed that the radial distributions of dust and pebbles in disks are often not smooth but show sub-structures in the form of rings and gaps (cite: andrews2018; andrews_2020), which can slow down and reduce pebble and water ice delivery to the inner disk (cite: kalyaan_2023; mah_2024). While models are quickly progressing and finding some support for the ice drift scenario to explain the correlations found with infrared water spectra, some aspects of the problem are emerging as key to this regulatory process. One aspect is the degree of ‘leakiness’ of disk gaps as pebble traps (cite: stammler_2023; pinilla_2024; tong_2025; kalyaan_2023; easterwood_2024; huang_2025), which should be directly linked to the amount of inner disk water enrichment by drift (with larger enrichment provided by leakier traps). A second major aspect is the timing of gap opening in the disk, which should typically start before the age of protoplanetary disks observed in nearby star-forming regions ${\sim}1{-}5$ Myr (cite: segura-cox2020; ALMA_HLTau; sheehan2020). A third aspect is the range of masses and radii disks may have when they form, which should provide different initial conditions of ice reservoirs for pebble drift. All these aspects could play a role in producing the scatter in inner disk water enrichment recently observed in larger samples with MIRI (cite: banzatti_2025; gasman2025; arulanantham2025).

![](data_figure_new.pdf)

# Data and analysis

This analysis requires using high quality data from MIRI and high spatial resolution ALMA observations to resolve dust gaps in inner disks. For MIRI, we adopt the samples published in (cite: banzatti_2025; gasman2025) all homogeneously reduced with the JDISCS pipeline, which adopts the standard MRS pipeline (cite: MIRI_pip) up to stage 2b and then uses asteroid calibrators to obtain the highest quality fringe correction, achieving signal-to-noise (S/N) of 200–400 (cite: pontoppidan_2024). As in (cite: banzatti_2025), we used the JDISCS reduction version 8.2 that used the MRS pipeline version 11.17.19 and Calibration Reference Data System context jwst_1253.pmap. The JWST data come from the following programs from the JDISCS and MINDS collaborations: GO-1282 (PI: T. Henning; co-PI: I. Kamp), GO-1549 (PI: K. Pontoppidan), GO-1584 (PI: C. Salyk; co-PI: K. Pontoppidan), GO-1640 (PI: A. Banzatti). For the ALMA data, we limit to high-resolution images as obtained in the DSHARP survey (cite: andrews2018) and the (cite: long_2019) survey of resolved disks in Taurus, which achieved spatial resolutions better than ${\sim}0''.1$ (${\approx}15 \mathrm{~au}$ at 150 pc). This work includes only T Tauri stars, and the specific sample available from the combined ALMA and JWST data covers stellar masses of 0.2–1 M$_{\odot}$ and ages of ${\sim}0.5{-}2\mathrm{~Myr}$ (see below). To have a sample that should focus on pebble drift effects, we also exclude disks where other processes are known to affect the observed water spectrum. Specifically, we exclude disks that have a spatially-resolved millimeter dust cavity (cite: salyk_2015; banzatti_2017), disks in a wide stellar binary system (cite: zagaria_2021), systems known to be episodic accretion bursters (cite: smith_2025), and disks that are viewed at an inclination angle higher than 65 deg (which causes inner disk obscuration and makes it hard to resolve inner gaps). With these criteria, we collected from published work a sample of 21 disks with properties reported in Table [1](#tab: sample).

To enable a consistent comparison of relative ages across our sample, we compiled effective temperatures and stellar luminosities from (cite: andrews2018; Manara_PPVII) and estimate stellar masses and ages by comparing them to evolutionary tracks. For this, we used the `Python` package `ysoisochrone`[^2] (cite: Deng_2025_ysoisochrone), which uses evolutionary tracks of (cite: Feiden16) for sources with $T_{\rm eff}>3900\mathrm{~K}$ and that of (cite: Baraffe15) for $T_{\rm eff} \le 3900\mathrm{~K}$. The typical uncertainty in the ages is ${\sim}0.5~\mathrm{Myr}$ and in the majority of cases, the age estimates are in good agreement with values reported in the literature (cite: andrews2018; long_2019; romero-mirza_2024). In a few instances, however, estimates from `ysoisochrone` are younger. We adopt our homogeneous approach to ensure internal consistency across the dataset. Lastly, we list in Table [1](#tab: sample) the approximate spatial resolution achieved by ALMA, typically around ${\sim}4{-}5~\mathrm{au}$ for the DSHARP sources and ${\sim}8{-}9\mathrm{~au}$ for other objects in Taurus with visibility analyses. The majority of sources thus have resolutions within a factor of $2{-}3$ and fall in the ‘high’ and ‘moderate’ angular resolution scenarios of (cite: mah_2024). We remark that even with the state-of-the-art resolution and analyses achieved in previous ALMA studies, in some cases the gap depth may be underestimated and (very) close-in and/or shallow gaps may have been missed (see Section  [4](#sec:discussion)).

Figure [1](#fig:data_trends) shows the cold water enrichment diagnostic, the 1500/6000 K flux ratio of water lines observed with MIRI as defined in (cite: banzatti_2025). Essentially, this line flux ratio measures the strength of lower-energy (upper level energy of $\sim1500$ K) water transitions in comparison to higher-energy (upper level energy of $\sim6000$ K) transitions and has been found to reflect the observed cold water mass in the disk surface (cite: romero-mirza_2024; banzatti_2025). The horizontal axes in the figure are the dust disk radius including 90–95% of the millimeter flux observed with ALMA (left) and the innermost disk gap location R$_{gap, in}$ (right). Several disks have additional gaps at larger radii (see Table [1](#tab: sample)), but we only use the innermost one as models predict it should have the strongest effect on water delivery (Section [1](#sec: intro)). For comparison to the gapped disks, we also include disks that have no gaps detected at the same spatial resolution; for these disks (five in total) as R$_{gap, in}$ in the right panel of Figure [1](#fig:data_trends) we use the dust disk size itself, since no inner gaps are detected inward of that.

While previous work found a significant anti-correlation with dust disk radius (cite: banzatti_2020; banzatti_2023; romero-mirza_2024), interpreted as a proxy for pebble drift efficiency over the disk as a whole, the larger sample included in this work is only weakly correlated (Pearson correlation coefficient of $-0.2$ and p-value of 0.47), as already discussed for similarly large samples in (cite: banzatti_2025; gasman2025). Using the same exact sample, the water diagnostic ratio is instead significantly correlated with the inner gap location (Pearson correlation coefficient of 0.5 and p-value of 0.06), directly confirming earlier model predictions (cite: kalyaan_2023). It is important to remark that models do not simply predict a linear correlation between the two, due to the age spread and the steep decline of the water enrichment curve in case of outer disk gaps (cite: kalyaan_2023). Additionally, variations in inner disk temperature structure and morphology (e.g., flaring) may increase the spread in diagnostic ratios. In fact, the data in Figure [1](#fig:data_trends) show a large spread of datapoints for gaps at 30–60 au, which is consistent with the spread in cold/hot water ratio measured in compact disks that have this range of sizes (cite: temmink_2025). It is also worth noting that some disks with deep inner gaps (e.g., CI Tau) also have large dust disk sizes due to the presence of multiple gaps. Together with smooth compact disks, these large disks with inner deep gaps were driving the previously reported anti-correlation between inner water enrichment and disk size in smaller samples (cite: banzatti_2023; banzatti_2025).

| Name | JWST PID | ratio | $R_\mathrm{gap}/\mathrm{au}$ | $W_\mathrm{gap}/\mathrm{au}$ | $D_\mathrm{gap}$ | \# gaps | $\log R_\mathrm{disk}/\mathrm{au}$ | Res/au | Ref. | age/Myr | $M_*/M_\odot$ |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:---|:---|:--:|:--:|:--:|:--:|:--:|
| AS 209 | 1584 | 3.05 | 8.7 | 4.7 | 0.45 | 7 | 2.14 | 4.4 | a | 0.93 | 0.80 |  |  |  |
| BP Tau | 1282 | 7.27 | 22.5 | 9.3 | 0.99 | 2 | 1.62 | 7.1$^\mathrm{v}$ | b,c | 0.56 | 0.54 |  |  |  |
| CI Tau | 1640 | 2.09 | 17 | 9.2 | 0.16 | 3 | 2.28 | 7.9 | d | 0.62 | 0.70 |  |  |  |
| CX Tau | 1282 | 5.71 | ... | ... | ... | 0 | 1.58 | 4.1 | e | 1.00 | 0.34 |  |  |  |
| DL Tau | 1282 | 2.83 | 14.7 | 4.2 | 0.86 | 7 | 2.22 | 8.7$^\mathrm{v}$ | b,c | 0.67 | 0.70 |  |  |  |
| DoAr 33 | 1584 | 3.68 | 9 | 1 | 0.95 | 1 | 1.43 | 3.4 | a | 1.48 | 1.01 |  |  |  |
| DR Tau | 1282 | 5.35 | 18.2 | 1.7 | 0.99 | 2 | 1.73 | 9.8$^\mathrm{v}$ | b,c | 0.54 | 0.68 |  |  |  |
| Elias 20 | 1584 | 7.23 | 25 | 3.5 | 0.75 | 2 | 1.81 | 3.2 | a | 0.50 | 0.52 |  |  |  |
| Elias 24 | 1584 | 7.84 | 57 | 22.8 | 0.03 | 2 | 2.13 | 4.7 | a | 0.50 | 0.71 |  |  |  |
| Elias 27 | 1584 | 4.20 | 69.1 | 14.3 | 0.73 | 1 | 2.41 | 5.5 | a | 0.74 | 0.58 |  |  |  |
| FZ Tau | 1549 | 3.00 | ... | ... | ... | 0 | 1.07 | 5.7 | f | 0.50 | 0.48 |  |  |  |
| GK Tau | 1640 | 6.79 | ... | ... | ... | 0 | 1.11 | 7.1$^\mathrm{v}$ | b,c | 0.62 | 0.64 |  |  |  |
| GO Tau | 1640 | 4.10 | 11.8 | 2.7 | 0.91 | 2 | 2.23 | 7.9$^\mathrm{v}$ | b,c | 1.58 | 0.35 |  |  |  |
| GQ Lup | 1640 | 10.3 | ... | ... | ... | 0 | 1.75 | 4.7 | g,h | 0.60 | 0.67 |  |  |  |
| GW Lup | 1282 | 3.31 | 47.5 | 2.4 | 0.99 | 3 | 2.02 | 6.6 | a | 1.62 | 0.42 |  |  |  |
| HP Tau | 1640 | 5.54 | ... | ... | ... | 0 | 1.35 | 9.7$^\mathrm{v}$ | b,c | 0.81 | 0.88 |  |  |  |
| IQ Tau | 1640 | 3.42 | 41 | 5.6 | 0.92 | 2 | 2.04 | 7.2$^\mathrm{v}$ | b,c | 0.56 | 0.48 |  |  |  |
| RU Lup | 1584 | 2.74 | 14 | 1 | 0.95 | 4 | 1.8 | 3.9 | a | 0.63 | 0.64 |  |  |  |
| SR 4 | 1584 | 1.93 | 11 | 6.3 | 0.23 | 1 | 1.49 | 4.6 | a | 0.77 | 0.65 |  |  |  |
| Sz 114 | 1584 | 8.02 | 38.6 | 4.3 | 0.94 | 1 | 1.78 | 4.6 | a | 1.04 | 0.17 |  |  |  |
| WSB 52 | 1584 | 5.21 | 21 | 1 | 0.95 | 1 | 1.5 | 3.7 | a | 0.67 | 0.47 |  |  |  |

: Sample properties for disks included in this work.

Table notes: The ratio is the 1500/6000 K line flux ratio that is sensitive to the cold water mass relative to the hot water mass in each disk, as defined in (cite: banzatti_2025). $R_\mathrm{gap}$, $W_\mathrm{gap}$, $D_\mathrm{gap}$, and \# gaps are the inner gap radius, width, depth, and total number of gaps detected in each disk as reported in (cite: huang_2018; zhang_2023; gasman2025). For disks without gap detections, we only use the outer radius that includes 90–95% of the millimeter emission ($R_{\rm{disk}}$) as reported in (cite: huang_2018; long_2019; facchini_2019; Guerra-Alvarado_2025). Spatial resolution (Res) is estimated as the distance $\times$ minor beam size (for data analyzed in the image plane), or (1/2) $\times$ distance $\times$ minor beam size (for data analyzed in the visibility plane, indicated by superscript ‘$^\mathrm{v}$’). ALMA references: a = (cite: huang_2018), b = (cite: zhang_2023), c = (cite: long_2019), d = (cite: clarke2018), e = (cite: facchini_2019), f = Long et al. (in prep.), g = (cite: wu2017), h = (cite: Guerra-Alvarado_2025). Stellar ages and masses are obtained as explained in Sect. [2](#sec:data).

# Model exploration

In order to test the observed trends presented in the previous section, we perform a population synthesis study that reproduce the outcome of dust evolution and pebble drift in disks of similar conditions to the observed sample, with a series of modeling steps as follows.

## Estimating pebble mass fluxes in disks with gaps

The temporal evolution of the pebble flux arriving at the inner disk is modeled using `pebble predictor`[^3] (cite: drazkowska_2021). The gas surface density is described as a tapered power-law (characterized by a size $R_\mathrm{taper}$) and pebble drift is calculated self-consistently assuming a combination of drift-limited and fragmentation-limited dust coagulation processes (cite: birnstiel_2024). `pebble predictor` has been successfully benchmarked against `dustpy` (cite: stammler_2022) for a range of disk masses, turbulence levels, and dust fragmentation velocities (cite: drazkowska_2021). Pebble fluxes are calculated at the midplane water snowline (defined as the position where $T_\mathrm{disk}=150\mathrm{~K}$) and we follow the approach of (cite: mulders_2021) to update the disk temperature profile when modeling different stellar masses. We use relatively fragile grains with constant fragmentation velocity $v_\mathrm{f} = 3\mathrm{~m/s}$, in line with recent laboratory, observational, and modeling studies favoring relatively fragile grains (cite: musiolik2019; jiang_2024; ueda2024; williams2025).

![](pebble_flux_overview_newages.png)

We expand these models to include one gap per disk, following previous work that showed the innermost gap, if deep enough, will dominate the regulatory process of water delivery by pebble drift even in the case of multiple gaps (cite: kalyaan_2023; easterwood_2024). In our models, gaps are described by three parameters: their location $R_\mathrm{gap}$, the time at which they appear $t_\mathrm{gap}$, and an effective ‘impact’ $\Lambda_\mathrm{gap}$ on the mass flux arriving at the water snowline – a parameter that in principle can depend on gap depth, width, but also its position and dust/pebble properties.

To synthesize lessons from dedicated studies investigating the impact of disk substructure on local pebble flux rates and inner disk water enrichment (cite: kalyaan_2021; kalyaan_2023; stammler_2023; easterwood_2024; mah_2024; tong_2025; huang_2025), we implement the appearance of outer disk substructure in `pebble predictor` as follows: once a gap opens (at position $R_\mathrm{gap}$ and time $t_\mathrm{gap}$), its impact on the snowline pebble flux is not felt until a time $$\begin{equation}
\label{eq:delay}
t^\mathrm{SL}_\mathrm{gap} = t_\mathrm{gap}+t_\mathrm{delay} = t_\mathrm{gap} + \frac{R_\mathrm{gap} - R_\mathrm{SL}}{\tilde{v}_\mathrm{peb}},
\end{equation}$$ where $R_\mathrm{SL}$ is the water snowline position and $\tilde{v}_\mathrm{peb}$ is a representative pebble drift speed that we set to $\tilde{v}_\mathrm{peb} = 2\times10^{-4}\mathrm{~au/yr}$ throughout[^4]. At times $t>t^\mathrm{SL}_\mathrm{gap}$, we multiply the pebble flux through the disk by a factor $\Lambda_\mathrm{gap}(<1)$ to mimic the gap’s ability to prevent material from drifting all the way to the snowline unhindered. We set $$\begin{equation}
\label{eq:gap_impact}
\Lambda_\mathrm{gap} =  1 - f^\mathrm{local}_\mathrm{gap} \times \exp\left[-\left(\frac{R_\mathrm{gap}}{R_\mathrm{taper}} \right)^\gamma\right]
\end{equation}$$ with $f^\mathrm{local}_\mathrm{gap}$ the fractional pebble flux that the gap blocks *locally* at $R_\mathrm{gap}$. With the focus being on relatively deep gaps, we use $f^\mathrm{local}_\mathrm{gap} = 0.99$ but vary this later. The exponential term in Eq. [\[eq:gap_impact\]](#eq:gap_impact) acts to reduce the impact far-out gaps have on the inner disk, as even though these gaps may be efficient filters locally, only a small fraction of the disk ice mass will be located exterior to their position (cite: easterwood_2024; williams2025). We set $\gamma=2$, for which we find the reduction in mass reaching the inner disk matches well the behavior in (cite: kalyaan_2023).

The blue curves in Fig. [2](#fig:pebble_flux_overview) show four representative models ($M_*=M_\odot$, $M_\mathrm{disk}=0.1M_*$, $\alpha_\mathrm{turb}=3\times10^{-4}$, $v_\mathrm{frag}=3\mathrm{~m/s}$, $R_\mathrm{taper}=60\mathrm{~au}$). While all three models with gaps use $t_\mathrm{gap}=10^5\mathrm{~yr}$ (and identical $f^\mathrm{local}_\mathrm{gap}$), closer-in gaps can be seen to lead to an earlier and more dramatic reduction in the pebble flux at the water snowline, ultimately allowing for a longer-lived (but lower) influx of material to the inner disk. The results of our semi-analytic model then broadly capture the relevant behavior observed in detailed simulations of (cite: kalyaan_2021; kalyaan_2023; easterwood_2024; mah_2024), while offering flexibility to explore various scenarios (see Sect.[3.4](#sec:parameter_exploration)).

## Pebble drift, cold water, and 1500/6000K ratios

Next, we use the approach detailed in (cite: romero-mirza_2024) to connect the pebble mass fluxes crossing the midplane water snowline $F^\mathrm{SL}_\mathrm{peb}(t)$ to an observable cold water mass $M^\mathrm{cold}_{\ce{H2O}}(t)$ in the disk surface layers overhead: $$\begin{equation}
\label{eq:carlos}
F^\mathrm{SL}_\mathrm{peb}(t) = \frac{M^\mathrm{cold}_{\ce{H2O}}(t)}{t_{\ce{H2O}}} \frac{\eta}{f_\mathrm{ice} f_{\ce{H2O}}},
\end{equation}$$ where $f_\mathrm{ice}$ is the mass fraction of pebbles that is ice, $f_{\ce{H2O}}$ is the mass fraction of ice that is water ice, $\eta$ is correction factor accounting for the unobservable water column beneath the optically thick layer, and $t_{\ce{H2O}}$ is the typical timescale on which newly-delivered water is removed/processed (either by chemistry or transport processes). Following (cite: romero-mirza_2024), we set $\eta=10^3$, $f_\mathrm{ice}=0.2$, $f_{\ce{H2O}} =0.8$, and $t_{\ce{H2O}} = 100~\mathrm{yr}$ and assume these parameters do not vary with time or between disks (cite: sellek2025; houge_2025; kanwar2025). With this approach, we are effectively assuming that the primary source of the cold (${\lesssim}300{-}400\mathrm{~K}$) water vapor reservoir in the disk surface is the sublimation of icy pebbles in the obscured midplane below, with the released vapor quickly being mixed upwards where it is observed (cite: banzatti_2023; banzatti_2025; houge_2025). In Fig. [2](#fig:pebble_flux_overview), Eq. [\[eq:carlos\]](#eq:carlos) is used to connect cold water masses (right-hand y-axis) to snowline pebble mass flux (left-hand y-axis).

We directly connect cold water water masses to 1500/6000K line flux ratios using an empirical relationship based on an investigation of published model series augmented by a new suite of multi-component slab models (see Appendix [5](#sec:appendix_B)). The adopted relation takes the form $$\begin{equation}
\label{eq:h2oratio}
1500/6000\mathrm{K} = \mathcal{A} + \left(\frac{M^\mathrm{cold}_{\ce{H2O}}}{0.4 ~ \mathrm{\mu} M_\oplus}\right)^{q}
\end{equation}$$ where we set $\mathcal{A}=1.75$ and $q=0.8$ to match the behavior observed in slab models (see Fig. [5](#fig:hockey_stick_figure)). Using Eq. [\[eq:h2oratio\]](#eq:h2oratio), we can compute cold water masses (and hence pebble fluxes) for all objects in Table [1](#tab: sample) and compare these to values from dust evolution models, pebble accretion models, and the Solar System[^5] in Fig. [2](#fig:pebble_flux_overview). While the populations overlap, the majority of the smooth disks (and disks with exclusively far-away gaps) are seen to cluster towards high pebble fluxes, while disks with close-in gaps include considerably lower fluxes.

![](popsynth_fiducial.png)

## Reproducing population-level trends

We present in Fig. [3](#fig:popsynth_1)A a total of $N=500$ unique models using a variation of star, disk, and gap parameters. For every iteration we randomly select a stellar mass $M_\star/M_\odot = [0.4,1]$, a gas disk mass $\log_{10}(M_\mathrm{disk}/M_\star) = [-1,-0.5]$, a disk size $R_\mathrm{taper}/\mathrm{au} = [30,80]$ (sampled logarithmically), and gap opening location $R_\mathrm{gap} = [5~\mathrm{au},1.5R_\mathrm{taper}]$. For the fiducial modeling series (see Table [2](#tab:model_params)) we set the turbulence strength to $\alpha_\mathrm{turb} = 10^{-3}$, dust-to-gas ratio to 0.02, fragmentation velocity $v_\mathrm{f}=3~\mathrm{m/s}$, and gap opening time to $t_\mathrm{gap}=10^5\mathrm{~yr}$. Initial disk masses and sizes are in line with results of star formation simulations (cite: bate_2018) and results of the AGE-PRO ALMA large program (cite: zhang2025; tabone2025), while turbulence levels are based on a variety of empirical constraints (cite: rosotti_2023; jiang_2024). We then sample each model exactly once at a random time between 0.5 and 2 Myr (roughly the age spread in our sample) and convert the pebble mass flux at that time into a 1500/6000 K ratio using Eqs. [\[eq:carlos\]](#eq:carlos) and [\[eq:h2oratio\]](#eq:h2oratio). The results of this exercise are shown in Fig. [3](#fig:popsynth_1)B, together with the data from Table [1](#tab: sample) (excluding the smooth disks). The models can be seen to yield results that are very consistent with the data: both avoiding the region in the top-left part of the plot (i.e., high line ratios with close-in gaps), while allowing for a range of 1500/6000 K ratios for (inner) gaps further out.

| Series | Fig. | $\alpha_\mathrm{turb}$ | $v_\mathrm{frag}$ | $t_\mathrm{gap}/\mathrm{yr}$ | Gap treatment |
|:---|:--:|:--:|:--:|:--:|:---|
| Fiducial | [3](#fig:popsynth_1)A,B | $10^{-3}$ | $3\mathrm{~m/s}$ | $10^5$ | Eq. [\[eq:gap_impact\]](#eq:gap_impact) and $f_\mathrm{gap}^\mathrm{local}=0.99$ |
| Rapid drift | [4](#fig:popsynth_2)A,B | $10^{-4}$ | $9\mathrm{~m/s}$ | \- | \- |
| Leaky gaps | [4](#fig:popsynth_2)C,D | \- | \- | \- | $f_\mathrm{gap}^\mathrm{local}=[0.5-0.9]$ |
| Later gaps | [4](#fig:popsynth_2)E,F | \- | \- | $10^6$ | \- |
| Indiscriminate gaps | [4](#fig:popsynth_2)G,H | \- | \- | \- | $\Lambda_\mathrm{gap} =  (1 - f^\mathrm{local}_\mathrm{gap})$ and $f_\mathrm{gap}^\mathrm{local}=[0.5-0.99]$ |

: Overview of parameters used in the disk population synthesis series of Sect. [3.3](#sec:popsynth) and [3.4](#sec:parameter_exploration).

Table notes: Entries marked ‘-’ default to the fiducial model. For the Later gaps case, ages are sampled only between 1-2 Myr in Fig. [4](#fig:popsynth_2) to avoid depicting systems with gaps that have not formed yet.

## On the timing of pebble drift and "leaky" gaps

An in-depth exploration of the impact of all parameters involved is beyond the scope of this study but we briefly discuss here the consequences of changing the timing of pebble delivery, the leakiness of gaps, and the timing of gap formation, concepts that have received considerable attention recently and that connect closely to the larger story of planet formation (cite: drazkowska_2021; segura-cox2020; stadler2022; ohashi2023; delussu2024; vioque2025). Specifically, we present in Fig. [4](#fig:popsynth_2) the results of a ‘rapid drift’ series of models in which pebbles grow larger and drift faster due to a lower turbulence and higher fragmentation velocity (see Table [2](#tab:model_params)), a ‘leaky gaps’ scenario (in which the $f_\mathrm{gap}^\mathrm{local}$ is lowered to between 0.5 and 0.9), a ‘later gaps’ series (in which $t_\mathrm{gap}=10^6\mathrm{~yr}$), and an ‘indiscriminate gaps’ case (in which the snowline pebble flux reduction is made independent of gap position).

Comparing the data and models in Fig. [4](#fig:popsynth_2)B it is evident that models in which a significant amount of pebble drift happens early (i.e., before gaps open) are not capable of reproducing the observed trends. This finding seems to match other studies highlighting the need for early substructure to slow down drift in order to reproduce observables such as mm fluxes, disk sizes, and spectral indices (cite: pinilla2012; delussu2024).

The permeability (i.e., leakiness) of gaps is an open question as various computational studies have highlighted that small grains can pass through planet-induced gaps relatively easily (cite: zhu2012; weber2018; drazkowska2019; stammler_2023; vanclepper2025). Our leaky gap scenario (Fig. [4](#fig:popsynth_2)D) does reproduce a range of line ratio values but fails to capture the trend with gap position, producing too many high line ratios for $R_\mathrm{gap}\lesssim20\mathrm{~au}$. For this particular sample of disks, we therefore favor relatively effective gaps, at least for the ones inside 20 au. If these gaps themselves turn out not to be capable of acting as effective drift barriers, additional effects such as the formation of planetesimals inside the associated pressure bumps (cite: carrera2019; lau2022) and their impact on water enrichment (cite: kalyaan_2023; danti2023) would have to be considered.

The models with later gaps (Fig. [4](#fig:popsynth_2)F) capture broadly the variation with $R_\mathrm{gap}$ but tend to underpredict line ratios across the board as the late appearance of gaps has allowed more pebbles to drift through during the first Myr. Moreover, some of later gap models have high line ratios because they are captured just between $t_\mathrm{gap}$ and $t_\mathrm{gap}+t_\mathrm{delay}$ (i.e., after the gap formed but before its impact in the disk is felt, see Eq. [\[eq:delay\]](#eq:delay)), which is a relatively short-lived phase and one that may be better captured in models with a (more) gradual gap opening treatment. Based on this exercise we conclude that to reproduce the observed trends of Fig. [1](#fig:data_trends) our models favor scenarios in which pebble drift is relatively slow and most gaps open within the first Myr.

As a final test we revisit the main working hypothesis in our models, based primarily on (cite: kalyaan_2021; kalyaan_2023), that close-in gaps may be the most effective in reducing inner water enrichment through pebble drift. To do so, in the bottom row of Fig. [4](#fig:popsynth_2) we present the case where gap position does *not* play that role (specifically, we have omitted the exponential term in Eq. [\[eq:gap_impact\]](#eq:gap_impact)). Including a spread in $f_\mathrm{gap}^\mathrm{local}$ values (between 0.5 and 0.99) does result in a range of line flux ratios (with higher $f_\mathrm{gap}^\mathrm{local}$ resulting in lower cold water masses, as expected, see Fig. [4](#fig:popsynth_2)H), but the trend with $R_\mathrm{gap}$ is absent. From this test we conclude that our models can only reproduce the behavior found in Fig. [1](#fig:data_trends) if their impact is indeed position-dependent.

![image](popsynth_rapiddrift.png) ![image](popsynth_leakygaps.png) ![image](popsynth_latergaps.png) ![image](popsynth_indiscriminategaps.png)

# Discussion and conclusions

In this study we have used a specific diagnostic (the 1500/6000 K water line flux ratio from JWST/MIRI) to target a specific reservoir (the observable cold water vapor in the disk surface) to investigate a process in a specific disk region (icy pebbles drifting across the midplane water snowline) to conclude that, in disks where substructure has been resolved, it is the innermost gaps that regulate water enrichment from ice drift into the terrestrial planet formation region (Fig. [1](#fig:data_trends)). This conclusion, reached for the first time by combining JWST and ALMA data, supports predictions from recent modeling works (cite: kalyaan_2021; kalyaan_2023; easterwood_2024; mah_2024). The population synthesis exploration performed in this work provides a fiducial model that can reproduce the observed trend in structured disks based on pebble drift models (Fig. [3](#fig:popsynth_1)), disfavoring scenarios where pebble drift happens early, where gaps are very leaky, or gaps form late (Fig. [4](#fig:popsynth_2)).

We remark, however, that the scenarios explored here are not necessarily universal and that water delivery in individual disks may be regulated by a combination of processes. Upcoming JWST programs aimed at expanding the sample of systems observed at different ages, across different spectral types, and across a range of mass accretion rates (cite: zhang_jwst; long_jwst; huang_jwst; majo_jwst), will be fundamental in providing additional multi-dimensional observational constraints. Moreover, increasing the sample of disks with uniform high-resolution ALMA continuum data will further test the correlation described in Sect. [2](#sec:data). To confirm the conclusions of this work, deep dust gaps that provide effective traps to ice-delivering pebbles should only be found with low 1500/6000 K water ratios in MIRI spectra, unless other processes affect the emission (e.g. a dust cavity or accretion bursts, see Section [2](#sec:data)). An example might be the case of BP Tau, where an inner dust cavity has recently been suggested from high-resolution ALMA data (cite: zhang_2023; gasman2025); if this is confirmed, the 1500/6000 K ratio might be slightly increased by dust dispersal rather than water delivery (cite: banzatti_2017).

Building on (cite: romero-mirza_2024; banzatti_2025), our methodology in this work focused on connecting pebble mass fluxes to cold water masses and line diagnostic ratios (Sect. [3.2](#sec:drift_to_cold_water)). While this approach captures the main factors involved in the story, we recognize that the water snowline region is characterized by complex interactions between thermochemistry, hydrodynamics, dust/ice evolution, and planet(esimal) formation (cite: hartmann2017; lichtenberg_2021; woitke2022; bosman2022; houge_2025; wang2025). Additionally, the full story of how the chemical and physical structure of the entire inner regions of protoplanetary disks (their midplanes *and* surface layers) respond to various degrees of pebble drift has to also include evolving elemental ratios (e.g., C/O) and molecular abundances for all relevant and observable species (cite: xie2023; sellek2025; long2025). The full JWST/MIRI spectra contain a wealth of information beyond the line ratio diagnostic used here that may help shed light on the bigger picture (cite: gasman2025; arulanantham2025).

The remarkable outcome of this work is that, in its simplicity, a population synthesis based on a few processes combined to new sensitive water line ratios from JWST and the highest-resolution ALMA observations finds support to recent models of dust evolution and pebble accretion to place them in context of the emerging exoplanet diversity and Solar System formation (Fig. [2](#fig:pebble_flux_overview)). Specifically, one aspect that is emerging is that the high pebble fluxes required to form Super-Earths in (cite: lambrechts_2019) (the top of the orange area in Fig. [2](#fig:pebble_flux_overview)), may be provided primarily by disks with no (deep) gaps in the inner ${\sim}20\mathrm{~au}$. Planets that form in these disks may accrete gas in water-vapor-rich environments, inheriting high O/H and low C/O ratio atmospheres (cite: bitsch2021; mah_2024). Conversely, disks with deeper gaps closer in are characterized by a rapidly decreasing pebble flux, perhaps more in line with what has been inferred for the inner Solar System (cite: kruijer_2020; lichtenberg_2021), suggesting a water-vapor-poor rocky planet formation environment. While bulk Earth is indeed very ‘dry’ (cite: krijt_2023) and the existence of a class of water-rich small planets (at least around M-dwarfs) has been argued to exist (cite: luque_2022), we have to remember terrestrial planets form primarily from solid building blocks and that water may be lost during the pebble accretion (cite: johansen_2021; wang2023) and planetesimal (cite: lichtenberg_2019; lichtenberg_2023) stages as well. Ultimately the observational trends presented in this study will have to be folded into state-of-the-art planet formation models to assess the impact of substructure and pebble drift (or the lack thereof) on emerging planetary properties.

We thank the reviewer for providing insightful comments that helped improve the manuscript. SK is grateful to Joanna Drążkowska and Tim Lichtenberg for sharing and discussing the Solar System model in Fig. [2](#fig:pebble_flux_overview). SK and TK acknowledge support from STFC Grant ST/Y002415/1. AB acknowledges support from JWST-GO-01640. KZ acknowledges support from JWST-GO-01584. This project was partially supported by the STScI grant JWST-GO01584 “A DSHARP–MIRI Treasury survey of Chemistry in Planet-forming Regions”. PP acknowledges funding from the UK Research and Innovation (UKRI) under the UK government’s Horizon Europe funding guarantee from ERC (under grant agreement No 101076489). Part of this research was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with the National Aeronautics and Space Administration (80NM0018D0004). This work benefited from information exchange within the program ‘Alien Earths’ (NASA Grant No. 80NSSC21K0593) for NASA’s Nexus for Exoplanet System Science (NExSS) research coordination network. The JWST data presented in this article were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute. The specific observations analyzed can be accessed via .

# Facilities

JWST(MIRI), ALMA

# Software

astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A; 2022ApJ...935..167A), iSLAT (cite: iSLAT; iSLAT_code; islat_3)

# Connecting cold water mass to 1500/6000K ratios

![](hockey_stick_figure.png)

Figure [5](#fig:hockey_stick_figure) compiles published cold water masses and water line flux ratios from (cite: romero-mirza_2024) and (cite: banzatti_2025). To explore the connection between these quantities further and to extend the range of cold water masses covered, we set up an additional grid of slab models with three components (hot: $850\, \mathrm{K}$, warm: $400\, \mathrm{K}$, and cold: $190\, \mathrm{K}$) using DuCKLinG (cite: Kaeufer2024) (shown in grey in Fig. [5](#fig:hockey_stick_figure)). DuCKLinG interpolates and integrates a grid of 0D LTE slab models (cite: Arabhavi2024) with water line data taken from HITRAN2020 (cite: Gordon2022) to derive the fluxes in the MIRI wavelength range. For this exercise, the emitting areas ($A_i$) of all slab components are quantified using the emitting radius ($R_i$) using $A_i=\pi R_i^2$. The radius of the warm component is double the radius of the hot component ($R_\mathrm{W}=2R_\mathrm{H}$), with the radius ($R_\mathrm{C}$) of the cold component being varied between $R_\mathrm{W}$ and $10R_\mathrm{W}$ on a logarithmic scale. The column density of the warm component is fixed to $5\times 10^{17}\,\mathrm{cm^{-2}}$ and the column densities of the hot and cold component are varied between $10^{18}-10^{19}\,\mathrm{cm^{-2}}$ and $10^{16}-10^{19}\,\mathrm{cm^{-2}}$, respectively[^6]. All temperatures, column densities, and radii are inspired by Table 8 from (cite: banzatti_2025) who set up slab models to overlap with the observed water line ratios. The cold water mass of every model is calculated as the mass of the cold slab component. The fluxes of a set of unblended water lines (cite: banzatti_2025) are integrated. The line tracing the hot water component has an upper level energy of $6052\,\mathrm{K}$, while the two lines whose sum is used to trace cold water have upper level energies of $1448\,\mathrm{K}$ and $1615\,\mathrm{K}$, respectively. The ratio of these integrated fluxes compared to the models’ cold water mass is shown in Fig. [5](#fig:hockey_stick_figure).

For cold water masses exceeding ${\sim}0.1-1 \mu M_\oplus$, Fig. [5](#fig:hockey_stick_figure) shows the 1500/6000K line flux ratio is sensitive to the amount of cold water – and hence pebble flux (top x-axis). This behavior is seen across the slab models, the model series from (cite: banzatti_2025), and the fits of (cite: romero-mirza_2024) to the full rotational rotational part of the spectrum. For the lowest cold water masses, relatively constant line ratios are predicted. This can be understood when considering that small cold water masses result in low fluxes of the examined cold water lines, which will make the typically small contribution from hotter water dominate also this wavelength region and therefore the ratio, i.e., the influence of changes from the cold component is minimized. For example, the integrated flux of the cold water lines for a cold water slab model with a mass of ${\sim}0.88\,\mathrm{\mu M_\oplus}$ (temperature: $400\,\rm K$, column density: $10^{18}\,\mathrm{cm^{-2}}$, and emitting radius: $0.5\,\mathrm{au}$) is about $7.5$ times larger than the flux of a typical hot water component (temperature: $850\,\rm K$, column density: $10^{18}\,\mathrm{cm^{-2}}$, and emitting radius: $0.1\,\mathrm{au}$). However, for a model (temperature: $400\,\rm K$, column density: $10^{18}\,\mathrm{cm^{-2}}$, and emitting radius: $0.2\,\mathrm{au}$) with a very low water masses ${\sim}0.14\,\mathrm{\mu M_\oplus}$ the integrated flux is only ${\sim}1.2$ the integrated flux of the hot component.

Apart from the cold water mass, the 1500/6000K ratio also depends on the remaining water reservoir. The gray points in Fig. [5](#fig:hockey_stick_figure) show how variations in $M_{\ce{H_2O}}^\mathrm{hot}$ of about an order of magnitude (similar to the spread observed in (cite: romero-mirza_2024)) introduce a scatter for identical $M_{\ce{H2O}}^\mathrm{cold}$. The larger amount of hot water in FZ Tau (cite: romero-mirza_2024) may thus be responsible for the apparent offset of that system in Fig. [5](#fig:hockey_stick_figure), although we note that FZ Tau is unusual also due to its ‘ring-like’ water vapor distribution and high mass accretion rate (cite: romero-mirza_2024). For the purposes of this study we adopt the trend described by Eq. [\[eq:h2oratio\]](#eq:h2oratio) (shown in green in Fig. [5](#fig:hockey_stick_figure)) that appears broadly consistent with existing water analyses (cite: romero-mirza_2024), but caution that variations in the amount and distribution of hot water may introduce significant scatter. These variations likely reflect differences in disk temperature and structure, but a connection to pebble drift cannot be fully excluded.

# Additional plots for the sample

![](data_figure_extra.pdf)

Figure [6](#fig: data_figure_names) includes target names for the right panel in Figure [1](#fig:data_trends), for guidance on identifying individual disks. The right panel in the figure shows the scatter of points when using the location of the deepest gap, taken from the same references as shown in Table [1](#tab: sample), rather than the innermost gap in each disk; the Pearson correlation decreases to -0.05 with p-value of 0.86.

natexlab

(ref: ALMA_HLTau) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3, doi: [`10.1088/2041-8205/808/1/L3`](http://doi.org/10.1088/2041-8205/808/1/L3)

(ref: andrews_2020) Andrews, S. M. 2020, ARA&A, 58, 483, doi: [`10.1146/annurev-astro-031220-010302`](http://doi.org/10.1146/annurev-astro-031220-010302)

(ref: andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: Arabhavi2024) Arabhavi, A. M., Kamp, I., Henning, T., et al. 2024, Science, 384, 1086, doi: [`10.1126/science.adi8147`](http://doi.org/10.1126/science.adi8147)

(ref: miri3) Argyriou, I., Glasse, A., Law, D. R., et al. 2023, A&A, 675, A111, doi: [`10.1051/0004-6361/202346489`](http://doi.org/10.1051/0004-6361/202346489)

(ref: arulanantham2025) Arulanantham, N., Salyk, C., Pontoppidan, K., et al. 2025, arXiv e-prints, arXiv:2505.07562, doi: [`10.48550/arXiv.2505.07562`](http://doi.org/10.48550/arXiv.2505.07562)

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2022ApJ...935..167A) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: islat_3) Banzatti, A., Johnson, M., Colmenares, M. J., Fuller, J., & egjellison. 2025, doi: [`10.5281/zenodo.15342712`](http://doi.org/10.5281/zenodo.15342712)

(ref: banzatti_2017) Banzatti, A., Pontoppidan, K. M., Salyk, C., et al. 2017, ApJ, 834, 152, doi: [`10.3847/1538-4357/834/2/152`](http://doi.org/10.3847/1538-4357/834/2/152)

(ref: banzatti_2020) Banzatti, A., Pascucci, I., Bosman, A. D., et al. 2020, ApJ, 903, 124, doi: [`10.3847/1538-4357/abbc1a`](http://doi.org/10.3847/1538-4357/abbc1a)

(ref: banzatti_2023) Banzatti, A., Pontoppidan, K. M., Carr, J. S., et al. 2023, ApJL, 957, L22, doi: [`10.3847/2041-8213/acf5ec`](http://doi.org/10.3847/2041-8213/acf5ec)

(ref: banzatti_2025) Banzatti, A., Salyk, C., Pontoppidan, K. M., et al. 2025, AJ, 169, 165, doi: [`10.3847/1538-3881/ada962`](http://doi.org/10.3847/1538-3881/ada962)

(ref: Baraffe15) Baraffe, I., Homeier, D., Allard, F., & Chabrier, G. 2015, A&A, 577, A42, doi: [`10.1051/0004-6361/201425481`](http://doi.org/10.1051/0004-6361/201425481)

(ref: bate_2018) Bate, M. R. 2018, MNRAS, 475, 5618, doi: [`10.1093/mnras/sty169`](http://doi.org/10.1093/mnras/sty169)

(ref: birnstiel_2024) Birnstiel, T. 2024, ARA&A, 62, 157, doi: [`10.1146/annurev-astro-071221-052705`](http://doi.org/10.1146/annurev-astro-071221-052705)

(ref: bitsch2021) Bitsch, B., Raymond, S. N., Buchhave, L. A., et al. 2021, A&A, 649, L5, doi: [`10.1051/0004-6361/202140793`](http://doi.org/10.1051/0004-6361/202140793)

(ref: bosman2022) Bosman, A. D., Bergin, E. A., Calahan, J., & Duval, S. E. 2022, ApJL, 930, L26, doi: [`10.3847/2041-8213/ac66ce`](http://doi.org/10.3847/2041-8213/ac66ce)

(ref: MIRI_pip) Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2024, JWST Calibration Pipeline, 1.15.1 Zenodo, doi: [`10.5281/zenodo.12692459`](http://doi.org/10.5281/zenodo.12692459)

(ref: carrera2019) Carrera, D., Simon, J. B., Li, R., Kretke, K. A., & Klahr, H. 2021, AJ, 161, 96, doi: [`10.3847/1538-3881/abd4d9`](http://doi.org/10.3847/1538-3881/abd4d9)

(ref: cieslacuzzi2006) Ciesla, F. J., & Cuzzi, J. N. 2006, Icarus, 181, 178, doi: [`10.1016/j.icarus.2005.11.009`](http://doi.org/10.1016/j.icarus.2005.11.009)

(ref: clarke2018) Clarke, C. J., Tazzari, M., Juhasz, A., et al. 2018, ApJL, 866, L6, doi: [`10.3847/2041-8213/aae36b`](http://doi.org/10.3847/2041-8213/aae36b)

(ref: colmenares2024) Colmenares, M. J., Lambrechts, M., van Kooten, E., & Johansen, A. 2024, A&A, 685, A114, doi: [`10.1051/0004-6361/202347737`](http://doi.org/10.1051/0004-6361/202347737)

(ref: majo_jwst) Colmenares Diaz, M. J., Arulanantham, N., Banzatti, A., et al. 2025, Can accretion explain the carbon dichotomy in planet-forming disks?,, JWST Proposal. Cycle 4, ID. #7662

(ref: cyr98) Cyr, K. E., Sears, W. D., & Lunine, J. I. 1998, Icarus, 135, 537, doi: [`10.1006/icar.1998.5959`](http://doi.org/10.1006/icar.1998.5959)

(ref: danti2023) Danti, C., Bitsch, B., & Mah, J. 2023, A&A, 679, L7, doi: [`10.1051/0004-6361/202347501`](http://doi.org/10.1051/0004-6361/202347501)

(ref: delussu2024) Delussu, L., Birnstiel, T., Miotello, A., et al. 2024, A&A, 688, A81, doi: [`10.1051/0004-6361/202450328`](http://doi.org/10.1051/0004-6361/202450328)

(ref: Deng_2025_ysoisochrone) Deng, D., Pascucci, I., & Fernandes, R. B. 2025, Journal of Open Source Software, 10, 7493, doi: [`10.21105/joss.07493`](http://doi.org/10.21105/joss.07493)

(ref: drazkowska2019) Drążkowska, J., Li, S., Birnstiel, T., Stammler, S. M., & Li, H. 2019, ApJ, 885, 91, doi: [`10.3847/1538-4357/ab46b7`](http://doi.org/10.3847/1538-4357/ab46b7)

(ref: drazkowska_2021) Drążkowska, J., Stammler, S. M., & Birnstiel, T. 2021, A&A, 647, A15, doi: [`10.1051/0004-6361/202039925`](http://doi.org/10.1051/0004-6361/202039925)

(ref: easterwood_2024) Easterwood, W., Kalyaan, A., & Banzatti, A. 2024, ApJ, 977, 21, doi: [`10.3847/1538-4357/ad891d`](http://doi.org/10.3847/1538-4357/ad891d)

(ref: facchini_2019) Facchini, S., van Dishoeck, E. F., Manara, C. F., et al. 2019, A&A, 626, L2, doi: [`10.1051/0004-6361/201935496`](http://doi.org/10.1051/0004-6361/201935496)

(ref: Feiden16) Feiden, G. A. 2016, A&A, 593, A99, doi: [`10.1051/0004-6361/201527613`](http://doi.org/10.1051/0004-6361/201527613)

(ref: gasman2025) Gasman, D., Temmink, M., van Dishoeck, E. F., et al. 2025, A&A, 694, A147, doi: [`10.1051/0004-6361/202452152`](http://doi.org/10.1051/0004-6361/202452152)

(ref: Gordon2022) Gordon, I. E., Rothman, L. S., Hargreaves, R. J., et al. 2022, JQSRT, 277, 107949, doi: [`10.1016/j.jqsrt.2021.107949`](http://doi.org/10.1016/j.jqsrt.2021.107949)

(ref: grant23) Grant, S. L., van Dishoeck, E. F., Tabone, B., et al. 2023, ApJL, 947, L6, doi: [`10.3847/2041-8213/acc44b`](http://doi.org/10.3847/2041-8213/acc44b)

(ref: Guerra-Alvarado_2025) Guerra-Alvarado, O. M., van der Marel, N., Williams, J. P., et al. 2025, A&A, 696, A232, doi: [`10.1051/0004-6361/202453338`](http://doi.org/10.1051/0004-6361/202453338)

(ref: hartmann2017) Hartmann, L., Ciesla, F., Gressel, O., & Alexander, R. 2017, Space Sci. Rev., 212, 813, doi: [`10.1007/s11214-017-0406-0`](http://doi.org/10.1007/s11214-017-0406-0)

(ref: henning2024) Henning, T., Kamp, I., Samland, M., et al. 2024, PASP, 136, 054302, doi: [`10.1088/1538-3873/ad3455`](http://doi.org/10.1088/1538-3873/ad3455)

(ref: irs) Houck, J. R., Roellig, T. L., van Cleve, J., et al. 2004, ApJS, 154, 18, doi: [`10.1086/423134`](http://doi.org/10.1086/423134)

(ref: houge_2025) Houge, A., Krijt, S., Banzatti, A., et al. 2025, MNRAS, 537, 691, doi: [`10.1093/mnras/staf057`](http://doi.org/10.1093/mnras/staf057)

(ref: huang_2018) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJL, 869, L42, doi: [`10.3847/2041-8213/aaf740`](http://doi.org/10.3847/2041-8213/aaf740)

(ref: huang_jwst) Huang, J., Banzatti, A., Birnstiel, T. D., et al. 2025, Do protoplanetary disk substructures regulate water enrichment and pebble drift across different environments?,, JWST Proposal. Cycle 4, ID. #7993

(ref: huang_2025) Huang, P., Yu, F., Lee, E. J., Dong, R., & Bai, X.-N. 2025, arXiv e-prints, arXiv:2503.19026. [`https://arxiv.org/abs/2503.19026`](https://arxiv.org/abs/2503.19026)

(ref: iSLAT) Jellison, E. G., Banzatti, A., Johnson, M. B., & Bruderer, S. 2024, AJ, 168, 99, doi: [`10.3847/1538-3881/ad6142`](http://doi.org/10.3847/1538-3881/ad6142)

(ref: jiang_2024) Jiang, H., Macı́as, E., Guerra-Alvarado, O. M., & Carrasco-González, C. 2024, A&A, 682, A32, doi: [`10.1051/0004-6361/202348271`](http://doi.org/10.1051/0004-6361/202348271)

(ref: johansen_2021) Johansen, A., Ronnet, T., Bizzarro, M., et al. 2021, Science Advances, 7, eabc0444, doi: [`10.1126/sciadv.abc0444`](http://doi.org/10.1126/sciadv.abc0444)

(ref: iSLAT_code) Johnson, M., Banzatti, A., Fuller, J., & Jellison, E. 2024, spexod/iSLAT: Second release, v4.03 Zenodo, doi: [`10.5281/zenodo.12167853`](http://doi.org/10.5281/zenodo.12167853)

(ref: Kaeufer2024) Kaeufer, T., Min, M., Woitke, P., Kamp, I., & Arabhavi, A. M. 2024, A&A, 687, A209, doi: [`10.1051/0004-6361/202449936`](http://doi.org/10.1051/0004-6361/202449936)

(ref: kalyaan_2021) Kalyaan, A., Pinilla, P., Krijt, S., Mulders, G. D., & Banzatti, A. 2021, ApJ, 921, 84, doi: [`10.3847/1538-4357/ac1e96`](http://doi.org/10.3847/1538-4357/ac1e96)

(ref: kalyaan_2023) Kalyaan, A., Pinilla, P., Krijt, S., et al. 2023, ApJ, 954, 66, doi: [`10.3847/1538-4357/ace535`](http://doi.org/10.3847/1538-4357/ace535)

(ref: kamp2023) Kamp, I., Henning, T., Arabhavi, A. M., et al. 2023, Faraday Discussions, 245, 112, doi: [`10.1039/D3FD00013C`](http://doi.org/10.1039/D3FD00013C)

(ref: kanwar2025) Kanwar, J., Woitke, P., Kamp, I., Rimmer, P., & Helling, C. 2025, A&A, 698, A294, doi: [`10.1051/0004-6361/202452249`](http://doi.org/10.1051/0004-6361/202452249)

(ref: krijt_2023) Krijt, S., Kama, M., McClure, M., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 1031, doi: [`10.48550/arXiv.2203.10056`](http://doi.org/10.48550/arXiv.2203.10056)

(ref: kruijer_2020) Kruijer, T. S., Kleine, T., & Borg, L. E. 2020, Nature Astronomy, 4, 32, doi: [`10.1038/s41550-019-0959-9`](http://doi.org/10.1038/s41550-019-0959-9)

(ref: lambrechts_2019) Lambrechts, M., Morbidelli, A., Jacobson, S. A., et al. 2019, A&A, 627, A83, doi: [`10.1051/0004-6361/201834229`](http://doi.org/10.1051/0004-6361/201834229)

(ref: lau2022) Lau, T. C. H., Drążkowska, J., Stammler, S. M., Birnstiel, T., & Dullemond, C. P. 2022, A&A, 668, A170, doi: [`10.1051/0004-6361/202244864`](http://doi.org/10.1051/0004-6361/202244864)

(ref: lichtenberg_2021) Lichtenberg, T., Drążkowska, J., Schönbächler, M., Golabek, G. J., & Hands, T. O. 2021, Science, 371, 365, doi: [`10.1126/science.abb3091`](http://doi.org/10.1126/science.abb3091)

(ref: lichtenberg_2019) Lichtenberg, T., Golabek, G. J., Burn, R., et al. 2019, Nature Astronomy, 3, 307, doi: [`10.1038/s41550-018-0688-5`](http://doi.org/10.1038/s41550-018-0688-5)

(ref: lichtenberg_2023) Lichtenberg, T., Schaefer, L. K., Nakajima, M., & Fischer, R. A. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 907, doi: [`10.48550/arXiv.2203.10023`](http://doi.org/10.48550/arXiv.2203.10023)

(ref: long_2019) Long, F., Herczeg, G. J., Harsono, D., et al. 2019, ApJ, 882, 49, doi: [`10.3847/1538-4357/ab2d2d`](http://doi.org/10.3847/1538-4357/ab2d2d)

(ref: long_jwst) Long, F., Andrews, S. M., Banzatti, A., et al. 2025a, Linking the outer structure with inner chemistry in disks around the most common planet hosts,, JWST Proposal. Cycle 4, ID. #7280

(ref: long2025) Long, F., Pascucci, I., Houge, A., et al. 2025b, ApJL, 978, L30, doi: [`10.3847/2041-8213/ad99d2`](http://doi.org/10.3847/2041-8213/ad99d2)

(ref: luque_2022) Luque, R., & Pallé, E. 2022, Science, 377, 1211, doi: [`10.1126/science.abl7164`](http://doi.org/10.1126/science.abl7164)

(ref: mah_2024) Mah, J., Savvidou, S., & Bitsch, B. 2024, A&A, 686, L17, doi: [`10.1051/0004-6361/202450322`](http://doi.org/10.1051/0004-6361/202450322)

(ref: Manara_PPVII) Manara, C. F., Ansdell, M., Rosotti, G. P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 539, doi: [`10.48550/arXiv.2203.09930`](http://doi.org/10.48550/arXiv.2203.09930)

(ref: morfill84) Morfill, G. E., & Voelk, H. J. 1984, ApJ, 287, 371, doi: [`10.1086/162697`](http://doi.org/10.1086/162697)

(ref: mulders_2021) Mulders, G. D., Drążkowska, J., van der Marel, N., Ciesla, F. J., & Pascucci, I. 2021, Why Do M Dwarfs Have More Transiting Planets?, doi: [`10.3847/2041-8213/ac2947`](http://doi.org/10.3847/2041-8213/ac2947)

(ref: musiolik2019) Musiolik, G., & Wurm, G. 2019, ApJ, 873, 58, doi: [`10.3847/1538-4357/ab0428`](http://doi.org/10.3847/1538-4357/ab0428)

(ref: najita_2013) Najita, J. R., Carr, J. S., Pontoppidan, K. M., et al. 2013, ApJ, 766, 134, doi: [`10.1088/0004-637X/766/2/134`](http://doi.org/10.1088/0004-637X/766/2/134)

(ref: oberg_bergin_2021) Öberg, K. I., & Bergin, E. A. 2021, Phys. Rep., 893, 1, doi: [`10.1016/j.physrep.2020.09.004`](http://doi.org/10.1016/j.physrep.2020.09.004)

(ref: ohashi2023) Ohashi, N., Tobin, J. J., Jørgensen, J. K., et al. 2023, ApJ, 951, 8, doi: [`10.3847/1538-4357/acd384`](http://doi.org/10.3847/1538-4357/acd384)

(ref: pinilla_2024) Pinilla, P., Benisty, M., Waters, R., Bae, J., & Facchini, S. 2024, A&A, 686, A135, doi: [`10.1051/0004-6361/202348707`](http://doi.org/10.1051/0004-6361/202348707)

(ref: pinilla2012) Pinilla, P., Birnstiel, T., Ricci, L., et al. 2012, A&A, 538, A114, doi: [`10.1051/0004-6361/201118204`](http://doi.org/10.1051/0004-6361/201118204)

(ref: pontoppidan_2024) Pontoppidan, K. M., Salyk, C., Banzatti, A., et al. 2024, ApJ, 963, 158, doi: [`10.3847/1538-4357/ad20f0`](http://doi.org/10.3847/1538-4357/ad20f0)

(ref: miri) Rieke, G. H., Wright, G. S., Böker, T., et al. 2015, PASP, 127, 584, doi: [`10.1086/682252`](http://doi.org/10.1086/682252)

(ref: romero-mirza_2024) Romero-Mirza, C. E., Banzatti, A., Öberg, K. I., et al. 2024, ApJ, 975, 78, doi: [`10.3847/1538-4357/ad769e`](http://doi.org/10.3847/1538-4357/ad769e)

(ref: rosotti_2023) Rosotti, G. P. 2023, New A Rev., 96, 101674, doi: [`10.1016/j.newar.2023.101674`](http://doi.org/10.1016/j.newar.2023.101674)

(ref: salyk_2015) Salyk, C., Lacy, J. H., Richter, M. J., et al. 2015, ApJL, 810, L24, doi: [`10.1088/2041-8205/810/2/L24`](http://doi.org/10.1088/2041-8205/810/2/L24)

(ref: segura-cox2020) Segura-Cox, D. M., Schmiedeke, A., Pineda, J. E., et al. 2020, Nature, 586, 228, doi: [`10.1038/s41586-020-2779-6`](http://doi.org/10.1038/s41586-020-2779-6)

(ref: sellek2025) Sellek, A. D., Vlasblom, M., & van Dishoeck, E. F. 2025, A&A, 694, A79, doi: [`10.1051/0004-6361/202451137`](http://doi.org/10.1051/0004-6361/202451137)

(ref: sheehan2020) Sheehan, P. D., Tobin, J. J., Federman, S., Megeath, S. T., & Looney, L. W. 2020, ApJ, 902, 141, doi: [`10.3847/1538-4357/abbad5`](http://doi.org/10.3847/1538-4357/abbad5)

(ref: smith_2025) Smith, S. A., Romero-Mirza, C. E., Banzatti, A., et al. 2025, ApJL, 984, L51, doi: [`10.3847/2041-8213/adcab8`](http://doi.org/10.3847/2041-8213/adcab8)

(ref: stadler2022) Stadler, J., Gárate, M., Pinilla, P., et al. 2022, A&A, 668, A104, doi: [`10.1051/0004-6361/202243338`](http://doi.org/10.1051/0004-6361/202243338)

(ref: stammler_2022) Stammler, S. M., & Birnstiel, T. 2022, ApJ, 935, 35, doi: [`10.3847/1538-4357/ac7d58`](http://doi.org/10.3847/1538-4357/ac7d58)

(ref: stammler_2023) Stammler, S. M., Lichtenberg, T., Drążkowska, J., & Birnstiel, T. 2023, A&A, 670, L5, doi: [`10.1051/0004-6361/202245512`](http://doi.org/10.1051/0004-6361/202245512)

(ref: stevenson88) Stevenson, D. J., & Lunine, J. I. 1988, Icarus, 75, 146, doi: [`10.1016/0019-1035(88)90133-9`](http://doi.org/10.1016/0019-1035(88)90133-9)

(ref: tabone_2023) Tabone, B., Bettoni, G., van Dishoeck, E. F., et al. 2023, Nature Astronomy, 7, 805, doi: [`10.1038/s41550-023-01965-3`](http://doi.org/10.1038/s41550-023-01965-3)

(ref: tabone2025) Tabone, B., Rosotti, G. P., Trapman, L., et al. 2025, arXiv e-prints, arXiv:2506.10742, doi: [`10.48550/arXiv.2506.10742`](http://doi.org/10.48550/arXiv.2506.10742)

(ref: temmink_2025) Temmink, M., Sellek, A. D., Gasman, D., et al. 2025, arXiv e-prints, arXiv:2505.15237, doi: [`10.48550/arXiv.2505.15237`](http://doi.org/10.48550/arXiv.2505.15237)

(ref: tong_2025) Tong, S., & Alexander, R. 2025, MNRAS, 537, 3525, doi: [`10.1093/mnras/staf245`](http://doi.org/10.1093/mnras/staf245)

(ref: ueda2024) Ueda, T., Tazaki, R., Okuzumi, S., Flock, M., & Sudarshan, P. 2024, Nature Astronomy, 8, 1148, doi: [`10.1038/s41550-024-02308-6`](http://doi.org/10.1038/s41550-024-02308-6)

(ref: vanclepper2025) Van Clepper, E., Price, E. M., & Ciesla, F. J. 2025, ApJ, 980, 201, doi: [`10.3847/1538-4357/ada8a4`](http://doi.org/10.3847/1538-4357/ada8a4)

(ref: vandishoeck_2014) van Dishoeck, E. F., Bergin, E. A., Lis, D. C., & Lunine, J. I. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 835–858, doi: [`10.2458/azu_uapress_9780816531240-ch036`](http://doi.org/10.2458/azu_uapress_9780816531240-ch036)

(ref: vioque2025) Vioque, M., Kurtovic, N. T., Trapman, L., et al. 2025, arXiv e-prints, arXiv:2506.10746, doi: [`10.48550/arXiv.2506.10746`](http://doi.org/10.48550/arXiv.2506.10746)

(ref: wang2023) Wang, Y., Ormel, C. W., Huang, P., & Kuiper, R. 2023, MNRAS, 523, 6186, doi: [`10.1093/mnras/stad1753`](http://doi.org/10.1093/mnras/stad1753)

(ref: wang2025) Wang, Y., Ormel, C. W., Mori, S., & Bai, X.-N. 2025, A&A, 696, A38, doi: [`10.1051/0004-6361/202453036`](http://doi.org/10.1051/0004-6361/202453036)

(ref: weber2018) Weber, P., Benı́tez-Llambay, P., Gressel, O., Krapp, L., & Pessah, M. E. 2018, ApJ, 854, 153, doi: [`10.3847/1538-4357/aaab63`](http://doi.org/10.3847/1538-4357/aaab63)

(ref: whipple1972) Whipple, F. L. 1972, in From Plasma to Planet, ed. A. Elvius, 211

(ref: williams2025) Williams, J., & Krijt, S. 2025, MNRAS, 537, 831, doi: [`10.1093/mnras/staf075`](http://doi.org/10.1093/mnras/staf075)

(ref: woitke2022) Woitke, P., Arabhavi, A. M., Kamp, I., & Thi, W. F. 2022, A&A, 668, A164, doi: [`10.1051/0004-6361/202244554`](http://doi.org/10.1051/0004-6361/202244554)

(ref: miri2) Wright, G. S., Rieke, G. H., Glasse, A., et al. 2023, PASP, 135, 048003, doi: [`10.1088/1538-3873/acbe66`](http://doi.org/10.1088/1538-3873/acbe66)

(ref: wu2017) Wu, Y.-L., Sheehan, P. D., Males, J. R., et al. 2017, ApJ, 836, 223, doi: [`10.3847/1538-4357/aa5b96`](http://doi.org/10.3847/1538-4357/aa5b96)

(ref: xie2023) Xie, C., Pascucci, I., Long, F., et al. 2023, ApJL, 959, L25, doi: [`10.3847/2041-8213/ad0ed9`](http://doi.org/10.3847/2041-8213/ad0ed9)

(ref: zagaria_2021) Zagaria, F., Rosotti, G. P., & Lodato, G. 2021, MNRAS, 504, 2235, doi: [`10.1093/mnras/stab985`](http://doi.org/10.1093/mnras/stab985)

(ref: zhang2025) Zhang, K., Pérez, L. M., Pascucci, I., et al. 2025a, arXiv e-prints, arXiv:2506.10719, doi: [`10.48550/arXiv.2506.10719`](http://doi.org/10.48550/arXiv.2506.10719)

(ref: zhang_jwst) Zhang, K., Armitage, T., Banzatti, A., et al. 2025b, Population Study of Chemistry in the First Million Years of Planet Formation: A MIRI Survey of Embedded Disks in Ophiuchus,, JWST Proposal. Cycle 4, ID. #7135

(ref: zhang_2023) Zhang, S., Kalscheur, M., Long, F., et al. 2023, ApJ, 952, 108, doi: [`10.3847/1538-4357/acd334`](http://doi.org/10.3847/1538-4357/acd334)

(ref: zhu2012) Zhu, Z., Nelson, R. P., Dong, R., Espaillat, C., & Hartmann, L. 2012, ApJ, 755, 6, doi: [`10.1088/0004-637X/755/1/6`](http://doi.org/10.1088/0004-637X/755/1/6)

[^1]: This work included only one disk more compact than $\sim 40$ au, therefore focusing on intermediate-size disks.

[^2]: <https://github.com/DingshanDeng/ysoisochrone>

[^3]: <https://github.com/astrojoanna/pebble-predictor>

[^4]: Pebble drift velocities depend on grain size and various disk parameters, with maximum values typically around $50 \mathrm{~m/s} \simeq 10^{-2} \mathrm{~au/yr}$ (cite: birnstiel_2024), however, even the largest particles in the outer disk will generally have Stokes numbers $\mathrm{St}\ll1$. Our choice of a velocity of $2\times10^{-4}\mathrm{~au/yr}$ matches well the observed delay in inner disk mass reduction shown in the more comprehensive models of (cite: kalyaan_2023).

[^5]: There is ongoing debate about the degree to which material could flow into the inner Solar System during the first few Myr (cite: kruijer_2020). We only show one representative example in Fig. [2](#fig:pebble_flux_overview) but note that other recent studies find comparable pebble mass fluxes and time evolutions (cite: colmenares2024).

[^6]: Additionally, we restrict the grid to models with column densities of the cold component smaller than the column density of the hot component. This avoids unrealistic parameter combinations that contradict typical output from thermochemical models (cite: Kaeufer2024).

</paper>

Write the methods card for this paper.