# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...984L..18T\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...984L..18T",
 "title": "exoALMA. XIII. Gas Masses from N<SUB>2</SUB>H<SUP>+</SUP> and C<SUP>18</SUP>O: A Comparison of Measurement Techniques for Protoplanetary Gas Disk Masses",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Trapman, Leon",
 "n_authors": 40,
 "arxiv_id": "2504.19371",
 "doi": "10.3847/2041-8213/adc430",
 "alma_projects_linked_by_archive": [
  "2012.1.00158.S",
  "2012.1.00681.S",
  "2012.1.00870.S",
  "2015.1.00192.S",
  "2015.1.00657.S",
  "2015.1.00678.S",
  "2015.1.01017.S",
  "2016.1.00484.L",
  "2016.1.00724.S",
  "2017.1.00069.S",
  "2017.1.00940.S",
  "2017.1.01404.S",
  "2017.1.01419.S",
  "2018.1.00689.S",
  "2018.1.00945.S",
  "2018.1.01055.L",
  "2019.1.01683.S",
  "2021.1.01123.L",
  "2022.1.00485.S",
  "2023.1.00334.S"
 ]
}
```

Paper text:
<paper>
# ExoALMA XIII. gas masses from $\mathrm{N}_2\mathrm{H}^+$ and $\mathrm{C}^{18}\mathrm{O}$:\
a comparison of protoplanetary gas disk mass measurement techniques

## Abstract

The gas masses of protoplanetary disks are important but elusive quantities. In this work we present new ALMA observations of $\mathrm{N}_2\mathrm{H}^+$ (3-2) for 11 exoALMA disks. $\mathrm{N}_2\mathrm{H}^+$ is a molecule sensitive to CO freeze-out and has recently been shown to significantly improve the accuracy of gas masses estimated from CO line emission. We combine these new observations with archival $\mathrm{N}_2\mathrm{H}^+$ and CO isotopologue observations to measure gas masses for 19 disks, predominantly from the exoALMA Large program. For 15 of these disks the gas mass has also been measured using gas rotation curves. We show that the CO + $\mathrm{N}_2\mathrm{H}^+$ line emission-based gas masses typically agree with the kinematically measured ones within a factor 3 ($\sim1-2\sigma$). Gas disk masses from CO + $\mathrm{N}_2\mathrm{H}^+$ are on average a factor $2.3^{+0.7}_{-1.0}\times$ lower than the kinematic disk masses, which could suggest slightly lower N$_2$ abundances and/or lower midplane ionization rates than typically assumed. Herbig disks are found to have ISM level CO gas abundances based on their CO and $\mathrm{N}_2\mathrm{H}^+$ fluxes, which sets them apart from T-Tauri disks where abundances are typically $\sim3-30\times$ lower. The agreement between CO + $\mathrm{N}_2\mathrm{H}^+$-based and kinematically measured gas masses is promising and shows that multi-molecule line fluxes are a robust tool to accurately measure disk masses at least for extended disks.

# Introduction

The gas masses of protoplanetary disks are crucial information for planet formation (e.g. (cite: MorbidelliRaymond2016)). The total mass determines if, and how many, gas giants can be formed in the disk. Furthermore, the gas density plays a large role in the dust physics occurring in the disk, such grain growth and inward drift rates (e.g. (cite: Drazkowska2023; Birnstiel2024)). The gas surface density also dictates the migration of planets that have already formed (e.g. (cite: Paardekooper2023)).

Measuring the gas mass has been plagued with difficulties (see reviews by (cite: BerginWilliams2018; Miotello2023; Oberg2023)), mainly because H$_2$, the dominant component of the gas, does not significantly emit at the $\sim20-30$ K temperature of the bulk of gas mass in protoplanetary disks (e.g. (cite: Thi2001; Carmona2011; Pascucci2013; Pinte2018; Law2021bMAPS; Law2022; Paneque-Carreno2023)).

The gas mass therefore has to be measured indirectly. This is most commonly done from the millimeter (mm) dust continuum emission, where the observed flux is converted into a dust mass by assuming a dust opacity, average disk temperature and that the emission is optically thin (e.g. (cite: Beckwith1990; Williams2005; ansdell2016; manara2023)). This dust mass is then converted to a gas mass by assuming a gas-to-dust mass ratio, most commonly using the typical interstellar medium (ISM) value of 100. While perhaps the most straightforward way to estimate the disk mass, the dust properties that set the opacity and the gas-to-dust mass ratio are likely different for each disk. Furthermore, there is increasing evidence that some or all of the disk continuum emission is optically thick at wavelengths $\lesssim1.3$mm (e.g. (cite: Andrews2018b; Tazzari2021a)).

The gas mass can also be inferred from less abundant species in the gas. Among these, hydrogen deuteride (HD) is perhaps the most promising because of its close chemical similarities to H$_2$ (e.g. (cite: Trapman2017; calahan2021)). *Herschel* detected HD $J=1-0$ ($112 \mu$m) emission towards three disks which allowed for robust gas disk mass measurements (e.g. (cite: Bergin2013; McClure2016; calahan2021; Schwarz2021; Trapman2022b)), but with the end of the *Herschel* mission we currently lack a far-infrared observatory capable of observing HD in more disks.

The most commonly used gas mass tracer is therefore CO, the second most abundant molecule in the gas, whose bright millimeter lines are detected towards most protoplanetary disks (e.g. (cite: Dutrey1996; Dent2005; WilliamsBest2014; ansdell2016; ansdell2018; Long2017)). Initial gas mass measurements based on the optically thin isotopologues of CO, $^{13}\mathrm{CO}$ and $\mathrm{C}^{18}\mathrm{O}$, revealed gas-to-dust mass ratios that were much lower than the ISM value (e.g. (cite: WilliamsBest2014; miotello2017; Long2017)). Cross comparisons with independent gas mass tracers, such as HD, suggested that these CO-based gas masses were underestimating the true disk mass.

The likely cause for this underestimation is the omission of one or more processes affecting gaseous CO in disks (e.g. (cite: Miotello2023)). The original thermochemical models used to derive gas masses included (isotope-selective) photodissociation and freeze-out, the two dominant processes that set the CO abundance structure (e.g. (cite: Aikawa2002; Visser2009; Miotello2014; Ruaud2019)). Several processes have been suggested to explain the low CO-based gas masses, including the chemical conversion of CO into more complex, less volatile species (e.g., (cite: Aikawa1997; FuruyaAikawa2014; Yu2016; Yu2017; Bosman2018b; Schwarz2018; Ruaud2022; Furuya2022)) and locking up CO into larger dust bodies that settle towards the midplane (e.g. (cite: Bergin2010; Bergin2016; Kama2016; Krijt2018; Krijt2020; vanClepper2022; Powell2022)).

An alternative approach was suggested by (cite: Anderson2019) and (cite: Trapman2022b), namely to combine observations of CO and $\mathrm{N}_2\mathrm{H}^+$. In the presence of CO-rich gas the formation of $\mathrm{N}_2\mathrm{H}^+$ is inhibited and its destruction is increased, making $\mathrm{N}_2\mathrm{H}^+$ an excellent tracer of CO-poor gas in protoplanetary disks. By simultaneously fitting CO and $\mathrm{N}_2\mathrm{H}^+$, the latter provides an observational estimate of how much CO has been removed from the gas by the processes mentioned previously and therefore how much the CO-based gas mass needs to be corrected to obtain the correct total gas mass. (cite: Trapman2022b) showed that gas masses measured from the combination of CO isotopologue and $\mathrm{N}_2\mathrm{H}^+$ lines are consistent with HD-based gas masses. This approach was also recently used by (cite: AGEPRO_V_gas_masses) to measure gas masses for twenty of the disks in the AGE-PRO ALMA Large program (cite: AGEPRO_I_overview).

The unprecedented spatial and spectral resolution and sensitivity of the Atacama Large Millimeter/submillimeter Array (ALMA) has made it possible to measure protoplanetary disk masses in a new and completely independent way, namely through gas kinematics (for a review (cite: pinte23)). Briefly, while the motions of gas in protoplanetary disks are dominated by the gravitational potential of star modulated by the pressure gradient, the disk self-gravity can leave an observable signature in the gas kinematics from which the disk mass can be measured. In contrast to the methods discussed previously, kinematically measured gas masses trace the total disk mass directly and circumvent the main sources of uncertainty that affect the indirect methods, such as CO chemistry and dust grain properties.

This technique was first applied by (cite: Veronesi2021) for the disk around Elias 2-27 and similar mass measurements have been carried out for the five disks in from the MAPS ALMA Large program ((cite: Lodato2023; Martire2024); see also (cite: Andrews2024; Veronesi2024)). In an accompanying paper (cite: Longarini2025exoALMA) used the rotation curves derived by (cite: Stadler2025exoALMA) from observations from the exoALMA Large program (cite: Teague2025exoALMA) to kinematically measure disk masses of a subset of the exoALMA sample. They focused their attention on ten disks, for which the geometrical orientation in the sky allows robust constraints on disk masses from self-gravity.

Given the importance of gas disk mass for planet formation, it is crucial that indirect, but more widely applicable, line-flux-based gas masses are compared and benchmarked against kinematically measured gas masses. In this work we carry out this benchmark and present new $\mathrm{N}_2\mathrm{H}^+$ $J=3-2$ ALMA Band 7 observations of 11 disks and new $\mathrm{C}^{18}\mathrm{O}$ $J=2-1$ observations for one disk (RXJ1842.9-3532). We combine these observations with archival ALMA observations of $\mathrm{N}_2\mathrm{H}^+$, $^{13}\mathrm{CO}$ and $\mathrm{C}^{18}\mathrm{O}$ to measure gas disk masses for 19 disks, which we compare to kinematically based gas masses from the literature (cite: Veronesi2021; Martire2024; Longarini2025exoALMA).

The structure of this paper is as follows: In Section [2](#sec: observations) we outline our sample and describe the calibration and imaging of the new and archival observations. In Section [3](#sec: methods) we describe how we measure gas mass from these observations. Section [4](#sec: results) analyzes these gas masses and compares them to the kinematically measured gas masses. These results are discussed in Section [5](#sec: discussion) and we present our conclusions in Section [6](#sec: conclusions).

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | RA | Dec | dist | SpT | T$_{\rm eff}$ | L$_*$ | M$_*$ | F$_{\rm 1.3mm}$ | M$_{\rm dust}^{\dagger}$ | PA | $i$ | $v_{\rm LSR}$ | Ref. |
|  |  |  | \[pc\] |  | \[K\] | \[L$_{\odot}$\] | \[M$_{\odot}$\] | \[mJy\] | \[M$_{\oplus}$\] | \[deg\] | \[deg\] | \[km/s\] |  |
| DM Tau | 04:33:48.73 | 18:10:09.97 | 144 | M2 | 3715 | 0.24 | 0.45 | 104.7 | 79.3 | 336 | 39 | 6.0 | 1,2 |
| AA Tau | 04:34:55.42 | 24:28:53.03 | 135 | K7 | 4350 | 1.10 | 0.79 | 67.0 | 27.8 | 273 | 59 | 6.4 | 6 |
| LkCa 15 | 04:39:17.79 | 22:21:03.39 | 157 | K5 | 4365 | 1.00 | 1.14 | 151.0 | 85.9 | 62 | 50 | 6.2 | 5 |
| HD 34282 | 05:16:00.48 | -09:48:35.39 | 309 | A0 | 9520 | 10.8 | 1.61 | 99.0 | 109.4 | 117 | 58 | -2.4 | 11,13 |
| MWC 758 | 05:30:27.53 | 25:19:57.08 | 156 | A7 | 7850 | 14.0 | 1.40 | 70.7 | 19.1 | 240 | 19 | 6.0 | 13,14 |
| CQ Tau | 05:35:58.47 | 24:44:54.09 | 149 | F2 | 6890 | 10.0 | 1.4 | 144.0 | 44.4 | 235 | 52 | 6.1 | 12,13 |
| PDS 66 | 13:22:07.54 | -69:38:12.22 | 98 | K1V | 5035 | 1.20 | 1.28 | 148.0 | 30.4 | 189 | 32 | 4.0 | 7,8 |
| HD135344B | 15:15:48.45 | -37:09:16.02 | 135 | F5 | 6440 | 6.70 | 1.61 | 117.0 | 28.1 | 243 | 16 | 7.0 | 11 |
| HD143006 | 15:58:36.91 | -22:57:15.22 | 167 | G7 | 5620 | 3.80 | 1.56 | 59.0 | 24.6 | 169 | 17 | 7.8 | 9,10 |
| RXJ1615.3-3255 | 16:15:20.23 | -32:55:05.10 | 156 | K5 | 4350 | 0.60 | 1.14 | 480.0 | 312.3 | 325 | 47 | 8.0 | 1 |
| V4046 Sgr | 18:14:10.48 | -32:47:34.52 | 72 | K5/K7 | 4370 | 0.5/0.3$^{*}$ | 1.73 | 327.0 | 47.6 | 256 | 34 | 3.0 | 3 |
| RXJ1842.9-3532 | 18:42:57.98 | -35:32:42.83 | 151 | K2 | 4780 | 0.80 | 1.07 | 63.2 | 36.6 | 206 | 39 | 6.0 | 4 |
| RXJ1852.3-3700 | 18:52:17.30 | -37:00:11.95 | 147 | K2 | 4780 | 0.60 | 1.03 | 58.2 | 33.2 | 147 | 33 | 5.6 | 4 |
| GM Aur | 04:55:10.98 | 21:59:54.00 | 159 | K6 | 4350 | 1.20 | 1.10 | 162.0 | 88.3 | 57 | 53 | 5.6 | 15,16 |
| AS 209 | 16:49:15.30 | -14:22:08.64 | 121 | K5 | 4266 | 1.41 | 1.20 | 288.0 | 86.5 | 86 | 35 | 4.6 | 17,18 |
| IM Lup | 15:56:09.21 | -37:56:06.13 | 158 | K5 | 4266 | 2.57 | 1.10 | 253.0 | 108.3 | 144 | 48 | 4.5 | 19,20 |
| MWC 480 | 04:58:46.30 | 29:50:37.00 | 162 | A5 | 8250 | 21.9 | 2.10 | 253.0 | 61.9 | 148 | 37 | 5.1 | 21 |
| HD 163296 | 17:56:21.30 | -21:57:22.00 | 101 | A1 | 9355 | 17.0 | 2.00 | 715.0 | 73.0 | 133 | 47 | 4.8 | 11 |
| Elias 2-27 | 16:26:45.0 | -24:23:7.8 | 116 | M0 | 3850 | 0.92 | 0.49 | 330.0 | 103.9 | 119 | 56 | 2.0 | 18 |

**Notes:**$^*$V4046 Sgr is a compact binary system. The table lists the spectral type and stellar luminosity for both its stars. $^{\dagger}$ Dust masses are computed from the 1.3 millimeter continuum flux using M$_{\rm dust}$ = F$_{\rm 1.3mm}d^2/\kappa_{\nu}B_{\nu}$(T) assuming $\kappa_{\nu} = 2.3\times(\nu/{\rm 230~GHz})~{\rm cm}^2~{\rm g}^{-1}$ and T = 20 K (cf. (cite: Beckwith1990; manara2023)). **References:** $\ensuremath{M_{*}}, i$ and PA from (cite: Izquierdo_exoALMA), R.A., Dec and dist from Table 1 in (cite: Teague2025exoALMA). 1: (cite: Herbig1977), 2: (cite: Andrews2011), 3: (cite: Bouvier1999), 4: (cite: Andrews2018b), 5: (cite: Fairlamb2015), 6: (cite: Guzman-Diaz2021), 7: (cite: Acke2005), 8: (cite: Herbig1960), 9: (cite: Mamajek2002), 10: (cite: Ribas2023), 11: (cite: LuhmanMamajek2012), 12: (cite: Barenfeld2016), 13: (cite: Quast2000), 14: (cite: Manara2014), 15: (cite: Espaillat2010), 16: (cite: Macias2018), 17: (cite: HerbigBell1988), 18: (cite: Andrews2009), 19: (cite: alcala2017), 20: (cite: Alcala2019), 21: (cite: Montesinos2009)

# Observations & Sample

## Sample

The sample discussed in this work differs somewhat from the exoALMA disk sample (cite: Teague2025exoALMA). Of the 15 exoALMA disks, all but two, SY Cha and RXJ1604-3010 A, have observations of $\mathrm{N}_2\mathrm{H}^+$ (3-2) and $^{13}\mathrm{CO}$ and $\mathrm{C}^{18}\mathrm{O}$ (2-1) or (3-2) available in the ALMA archive or presented in this work. As we will discuss in Section [3](#sec: methods) these lines are needed to measure the gas mass, so we limit our analysis to these 13 disks. For nine of the 13 disks (cite: Longarini2025exoALMA) were able to measure kinematic gas masses from the rotation curves presented in (cite: Stadler2025exoALMA). The remaining four disks were either too face-on or their emission was too asymmetric to obtain reliable kinematic gas masses (see (cite: Longarini2025exoALMA) for details). While this prevents us from performing a gas mass comparison with kinematics, we do include these four disks in our other analyses.

We supplement our 13 exoALMA disks with six disks where kinematically measured gas masses are also available (cite: Veronesi2021; Martire2024) to maximize the number of disks with such measurements in our sample. These are the five disks from the MAPS large program (cite: Oberg2021MAPS) and Elias 2-27 (e.g. (cite: Perez2016; Paneque-Carreno2021)). These six disks also have the necessary line fluxes available to measure their gas masses. Our full sample thus consists of 19 disks, 15 of which have kinematically measured gas masses. Stellar and disk parameters of the sample are summarized in Table [\[tab: exoALMA parameters\]](#tab: exoALMA parameters).

## New observations

We present new ALMA Band 7 observations of $\mathrm{N}_2\mathrm{H}^+$ $J=3-2$ for AA Tau, CQ Tau, MWC 758, RXJ1615.3-3255, RXJ1852.3-3700, RXJ1842.9-3532, PDS 66, HD 34282, HD 143006, HD 135344B, and Elias 2-27 (IDs 2022.1.00485.S, 2023.1.00334.S; PI: L. Trapman). We also present ALMA Band 6 observations of $\mathrm{C}^{18}\mathrm{O}$ (2-1) and C$^{17}$O 2-1 for RXJ1842.9-3532 (ID 2023.1.00334.S).

The ALMA Band 6 and 7 observations were carried out October 2023-May 2024 for program 2023.1.00334.S, with baseline lengths between 15 and 1200 m and October 2022-January 2023 for program 2022.1.00485.S, with baseline lengths between 15 and 740 m.

The Band 7 correlator was set up to cover $\mathrm{N}_2\mathrm{H}^+$ (3-2) at 279.517 GHz, DCO$^{+}$ 4-3 at 288.149 GHz, DCN 4-3 at 289.65 GHz, C$^{34}$S 6-5 at 189.215 GHz and H$_2$CO 4$_{0,4}$ - 3$_{0,3}$ at 290.623 GHz. All lines are covered at a spectral resolution of 122 kHz ($\sim 120$ m/s) with the exception of H$_2$CO, which was covered at a coarser spectral resolution of 977 kHz ($1.2$ km/s). In addition to the lines the correlator setup also includes two 1.875 GHz wide continuum spectral window centered at 278.008 GHz and 290.870 GHz, respectively. Note that the higher frequency continuum spectral window is the same spectral window that covers the H$_2$CO line, hence why it has a coarser spectral resolution.

The Band 6 correlator was set up to cover the $\mathrm{C}^{18}\mathrm{O}$ (2-1) line at 219.565 GHz, C$^{17}$O 2-1 at 224.719 GHz, SO$_2$ 4$_{2,2}$ - 3$_{1,3}$ at 235.156 GHz, HCC$^{13}$CN 26-25 at 235.514 GHz, HC$^{13}$CCN 26-25 at 235.537 GHz, and HCCCN 26-25 at 236.517 GHz. All lines are covered at a spectral resolution of 122 kHz ($\sim150$ m/s) with the exception of $\mathrm{C}^{18}\mathrm{O}$ (2-1), which is covered at a higher spectral resolution of 61 kHz (83.3 m/s). In addition to the lines the correlator setup also includes a 1.875 GHz wide continuum spectral window centered at 237.063 GHz.

The on-source times for Band 7 and Band 6 were 30-50 min and 40 min, respectively.

![](exoALMA_new_obs_gallery.pdf)

### Data reduction

All observations were initially calibrated using the Common Astronomy Software Application (CASA; (cite: CASAteam2022)) pipeline version 6.4.1.12 for program 2022.1.00485.S and 6.5.4.9 for program 2023.1.00334.S using the `scriptforPI.py` as provided with the data.

The signal-to-noise (SNR) of our observations was high enough to conduct self-calibration after the initial pipeline calibration. Our approach was based on the self-cal procedures of the DSHARP, MAPS, and AGE-PRO large programs (e.g. (cite: Andrews2018; Czekala2021MAPS; AGEPRO_I_overview)). It is near-identical to the exoALMA self-calibration procedure, with the exception of the spatial alignment (see (cite: Loomis_exoALMA) for details).

First, continuum-only visibility data sets were created by flagging all channels with $\pm20$ km/s of one of the lines in our spectral setup, irrespective of whether this line was detected or not. The resulting line-free continuum channels were averaged together to channels with a maximum width of 125 MHz. Next, individual execution blocks were astrometrically aligned by fitting 2D Gaussians to their continuum emission in the image plane and aligning their phase centers to the coordinates listed in Table [\[tab: exoALMA parameters\]](#tab: exoALMA parameters). For HD135344B, HD143006, HD34282, and MWC 758 the continuum emission was found to be too asymmetric to be reliably fitted with a Gaussian. Here we instead fitted the data with a Gaussian ring, using its center to align the measurement sets.

After alignment we checked relative flux scaling between execution blocks by deprojecting the continuum visibilities using disk geometry from the literature (see Table [\[tab: exoALMA parameters\]](#tab: exoALMA parameters)) and comparing their amplitude profile as a function of baseline length. In all cases we found the fluxes of individual execution blocks for a single source to differ by less than 10%. As this is within the expected absolute flux uncertainty of ALMA we did not rescale the fluxes.

Self-calibration was then carried out first on just the short baseline observations, followed by a second self-calibration using the combined self-calibrated short baseline and non-self-calibrated long baseline observations. For both self-calibration sets we performed 1-3 rounds of phase-only self-calibration followed by a single round of amplitude+phase self-calibration. For the phase-only rounds the initial solution interval was chosen to be the full on-source time. Each consecutive round reduced that interval by a factor two, ending when the current phase-only solution improved the peak SNR by less than 10% compared to the previous solution.

After self-calibration the obtained gaintables were applied to the full visibility dataset, followed by a subtraction of the continuum using the task `uvcontsub`. For each spectral window we flag all channels within $\pm 20$ km/s of each line in the spectral setup before fitting the remaining channels with a first-order polynomial.

### Imaging

The lines and continuum were imaged with the `tclean` CASA task using the ‘multiscale’ deconvolver with scales of \[0, 5, 15\] $0.02\ensuremath{''}$ pixels, a ‘Briggs’ weighting with a robust parameter of 0.5, a gain of 0.08 and a small scale bias of 0.45. The images were cleaned down to a threshold of $1\sigma$, measured from an emission-free part of the cube. For imaging the lines we also include a Keplerian mask created using the routine from (cite: teague2020) with the parameters listed in Table [\[tab: exoALMA parameters\]](#tab: exoALMA parameters). This results in a typical beam of $\sim0.25\ensuremath{''}-0.35\ensuremath{''}$ and sensitivities of $\sim3-5$ mJy/beam per 0.25 km/s channel.

## Archival observations

In addition to the new $\mathrm{N}_2\mathrm{H}^+$ (3-2) observations presented in this work we also make use of a large set of archival observations, primarily ones that provide $^{13}\mathrm{CO}$ and $\mathrm{C}^{18}\mathrm{O}$ observations for our sources. In most cases these are of the $J=2-1$ transition, but for RXJ1615.3-3255, AA Tau, HD 143006, and HD 135344B, observations of this transition were not available in the ALMA archive so the $J=3-2$ transition is used instead. For Elias 2-27 observations of $J=2-1$ are available but show significantly more cloud contamination than the $J=3-2$ observations. We therefore opt to use the latter transition here. Table [\[tab: fluxes and programs\]](#tab: fluxes and programs) summarized the program IDs of the archival data sets and for further details on the observations and data reduction of each we refer the reader to the works listed in the table.

For two sources, RXJ1615.3-3255 and HD 143006, one or both of the CO isotopologue archival observations have not previously appeared in the literature. For these sources we calibrated, self-calibrated and imaged the archival data following the same procedure as was used for the new observations. A more in depth analysis of the CO isotopologue observations of HD 143006 will be presented in *van Terwisga et al., in prep.*

![](C18O_versus_225GHz_continuum.pdf)

![](N2Hp_versus_285GHz_continuum.pdf)

![](C18O_versus_N2Hp_fluxes.pdf)

## A first look at the observations

Integrated intensity maps of the 285 GHz continuum and $\mathrm{N}_2\mathrm{H}^+$ of each source in our sample are presented in Figure [1](#fig: B7 obs gallery). While some of the disks exhibit substructures, this work will focus on the gas mass derived from integrated fluxes and the analysis of the resolved emission will be presented in a future work.

To measure integrated fluxes, the data cubes were first corrected for the non-Gaussian beam resulting from multi-configuration ALMA observations following (cite: Czekala2021MAPS) (so-called JvM correction, see also (cite: JorsatervanMoorsel1995)). In the case of line emission, integrated intensity maps were created using the same Keplerian mask used for imaging. From the resulting 2D images the integrated flux was measured using a curve-of-growth method[^1]. Here the flux is measured using increasingly larger elliptical apertures with the same aspect ratio and orientation as the disk until integrated flux plateaus. We note that this method was only used to measure fluxes from the new observations and the archival observations where integrated fluxes had not been previously published. For sources where CO isotopologue or $\mathrm{N}_2\mathrm{H}^+$ integrated line fluxes were already available we adopt the published values to maintain consistency with existing literature. The integrated line and continuum fluxes are summarized in Table [\[tab: fluxes and programs\]](#tab: fluxes and programs).

Figure [2](#fig: integrated line fluxes) shows the integrated line and continuum fluxes from this work combined with the 20 class II disks from the AGE-PRO ALMA large program first presented in (cite: AGEPRO_III_Lupus; AGEPRO_IV_UpperSco). Note that for $\mathrm{C}^{18}\mathrm{O}$ we have scaled down the $\mathrm{C}^{18}\mathrm{O}$ (3-2) line fluxes by a factor 2.3, which is the median $\mathrm{C}^{18}\mathrm{O}$ (3-2)/$\mathrm{C}^{18}\mathrm{O}$ (2-1) flux line ratio for thermochemical models with $\ensuremath{M_{\rm disk}}\geq 10^{-4}~\ensuremath{\mathrm{M}_{\odot}}$ from (cite: AGEPRO_V_gas_masses). Starting from the top panel of Figure [2](#fig: integrated line fluxes), we see a correlation between $\mathrm{C}^{18}\mathrm{O}$ versus 225 GHz continuum fluxes, which is in line with earlier works (e.g., (cite: Bergner2019; Anderson2024; AGEPRO_III_Lupus; AGEPRO_IV_UpperSco)). The combined sample of the three ALMA large programs, MAPS, AGE-PRO, and exoALMA, shows that this correlation holds over over three orders of magnitude in both continuum and $\mathrm{C}^{18}\mathrm{O}$ flux.

If the Herbigs disks are excluded, a similar positive correlation can be seen between $\mathrm{N}_2\mathrm{H}^+$ (3-2) and the 285 GHz continuum fluxes for the T-Tauri disks, also in line with previous findings (e.g., (cite: Anderson2022; Anderson2024; AGEPRO_III_Lupus; AGEPRO_IV_UpperSco)). It is unclear if the same correlation is also present for faint ($\lesssim 10$ mJy) continuum sources due to the low detection rate of $\mathrm{N}_2\mathrm{H}^+$ (3-2) below that point. It should also be noted that, while suggestive, the trend of $\mathrm{N}_2\mathrm{H}^+$ upper limits with continuum flux is an artifact of the correlation between continuum flux and continuum disk size (e.g. (cite: Tripathi2017; Hendler2020)). For the $\mathrm{N}_2\mathrm{H}^+$ non-detections the continuum dust disk size was used as the aperture size for many sources, which when combined with the continuum flux-size relation leads to a positive correlation between the $\mathrm{N}_2\mathrm{H}^+$ upper limit threshold and the continuum flux (see (cite: AGEPRO_III_Lupus; AGEPRO_IV_UpperSco) for details).

The middle panel of Figure [2](#fig: integrated line fluxes) also shows that the Herbig disks in the sample do not follow the same $\mathrm{N}_2\mathrm{H}^+$-continuum flux correlation as is seen for the T-Tauri disks. For Herbig disks of a given continuum flux the $\mathrm{N}_2\mathrm{H}^+$ (3-2) integrated flux is approximately an order of magnitude fainter. A likely cause for this are the higher stellar luminosities of these sources warming up the disk. This results in less CO freeze-out and therefore a higher CO abundance that inhibits the formation of $\mathrm{N}_2\mathrm{H}^+$ (e.g. (cite: Qi2015)). Curiously, the $\mathrm{N}_2\mathrm{H}^+$ flux of Elias 2-27, itself a M0 T-Tauri star, lies closer to the Herbig disks than to the T-Tauri disks. A possible explanation could be the young age of the system, with active accretion through the disk and backwarming by an envelope increasing the disk temperature to similar levels as in the Herbig disks (e.g. (cite: DAlessio1998; Whitney2013; vtHoff2018; vtHoff2020; Kuznetsova2022)). An alternate explanation could be a low midplane ionization rate in this source, which we will discuss further in Section [5.3](#sec: constraining midplane ionization rates).

The bottom panel of Figure [2](#fig: integrated line fluxes) shows $\mathrm{C}^{18}\mathrm{O}$ set against $\mathrm{N}_2\mathrm{H}^+$. Again excluding the Herbig disks, we see that above a $\mathrm{C}^{18}\mathrm{O}$ flux of $\sim100$ mJy km/s the two lines are correlated, similar to what was recently found by (cite: Anderson2024). As discussed by these authors this correlation is unexpected given the anti-correlation between CO and $\mathrm{N}_2\mathrm{H}^+$, but it could suggest that other factors, such as disk mass and size dominate over chemical effects. Alternatively, a correlation would also be expected if CO abundances are similar between disks (e.g. (cite: AGEPRO_III_Lupus; AGEPRO_IV_UpperSco)). It is unclear if the correlation extends below this threshold. $\mathrm{N}_2\mathrm{H}^+$ is only detected for six of the eighteen sources with a $\mathrm{C}^{18}\mathrm{O}$ flux $\leq100$ mJy km/s, but one of those detections is for the source with the faintest $\mathrm{C}^{18}\mathrm{O}$ detection in the figure. As these are all AGE-PRO sources we refer the reader to (cite: AGEPRO_III_Lupus; AGEPRO_IV_UpperSco) for a more detailed analysis.

As with the middle panel, the Herbig disks and Elias 2-27 occupy a different part of the figure. These sources have $\mathrm{N}_2\mathrm{H}^+$ fluxes that are $\sim1-2$ orders of magnitude lower compared to T-Tauri disks with similar $\mathrm{C}^{18}\mathrm{O}$ fluxes. Located in between the Herbigs and the T-Tauris is the disk around HD 143006, a G7 spectral type star whose stellar luminosity lies in between the T-Tauri and Herbig stars that make up our sample. Its location in the bottom panel of Figure [2](#fig: integrated line fluxes) is consistent with the idea that a higher overall disk temperature, driven by a higher stellar luminosity, is what sets apart Herbig and T-Tauri disks.

![](exoALMA_and_MAPS_disk_masses_MCMC_v5.pdf)

# Measuring gas disk masses from line emission

For measuring the gas disk masses ($M_{\rm gas}$) in our sample we follow the approach from (cite: AGEPRO_V_gas_masses) using the grid of thermochemical models presented in the same work. To briefly summarize this approach: (cite: AGEPRO_V_gas_masses) used the thermochemical code `DALI` (cite: Bruderer2012; Bruderer2013) to run a large grid of disk models where they varied the disk mass, characteristic size, stellar luminosity, vertical structure, and dust properties. These models include isotope-selective photo-dissociation and chemistry for CO following (cite: Miotello2014), but they do not include the processes thought to be responsible for removing CO from the gas in the CO emitting layer. Instead, in their models the peak CO abundance in the CO emitting layer is included as a free parameter ($3\times10^{-7}~\leq x_{\rm CO}\leq 10^{-4}$), which serves as a proxy for processes beyond photodissocation and freeze-out that affect gaseous CO in the disk. Constraining this parameter is the main reason for including $\mathrm{N}_2\mathrm{H}^+$ in addition to the CO lines, as it breaks the degeneracy between disk mass and $x_{\rm CO}$ encountered when only using CO lines (e.g. (cite: Anderson2019; Anderson2022; Trapman2022b; Oberg2023)).

Using synthetic observations from this model grid they used a MCMC to carry out a $\chi^2$ fit of the observed 225 GHz continuum, $^{13}\mathrm{CO}$ (2-1), $\mathrm{C}^{18}\mathrm{O}$ (2-1), and $\mathrm{N}_2\mathrm{H}^+$ (3-2) integrated line fluxes and derive a posterior distribution for the disks in AGE-PRO (see (cite: AGEPRO_V_gas_masses) for further details).

In this work we make a few small modifications to this approach. First, we use $10^{-4}\ \ensuremath{\mathrm{M}_{\odot}}\leq \ensuremath{M_{\rm gas}}\leq 0.5\ \ensuremath{\mathrm{M}_{\odot}}$ as a prior for the disk mass, which is in line with the fact that the sources in this work are much brighter, and likely more massive than the AGE-PRO disks. This prior is assumed to be uniform in logspace as the gas mass is also fit in logspace. Second, six T-Tauri sources in our sample have stellar luminosities $L_* \geq 1\ \mathrm{L}_{\odot}$, which is the maximum stellar luminosity in the (cite: AGEPRO_V_gas_masses) model grid. As fitting the observations with a low stellar luminosity could lead to an overestimation of the amount of CO freeze-out and thus an overestimation of the gas disk mass, we ran an extra series of models[^2] with $L_* = 3.0$, varying all other parameters as in (cite: AGEPRO_V_gas_masses), except that we skip $R_{\rm c} =1~\mathrm{au}$ and $\ensuremath{M_{\rm gas}}< 10^{-4}~\ensuremath{\mathrm{M}_{\odot}}$ as these models would be too compact and/or low-mass to represent the disks in our sample. The fluxes for these models and the ones that will be discussed in Sections [5.2](#sec: effect inner cavity) and [5.4](#sec: n2hp for herbigs) will be made available as part of this manuscript.

It is also worth pointing out that many of the sources in the sample have large dust cavities and/or other dust substructures (e.g. Figure [1](#fig: B7 obs gallery); (cite: Perez2015; Paneque-Carreno2021; Sierra2021; Curone2025exoALMA)), which are not present in thermochemical models. We will revisit their impact on our results in Section [5.2](#sec: effect inner cavity).

The Herbig disks in our sample, i.e., HD 135344B, HD 34282, CQ Tau, MWC 758, HD 163296, and MWC 480, warrant a slightly different approach. The models in (cite: AGEPRO_V_gas_masses) were run using stellar properties typical for T-Tauri stars (T$_{\rm eff} = 3500-4000$ K; $L_* = 0.1 - 1.0$ L$_{\odot}$), making them not representative for these sources. Recently, (cite: Stapper2024) presented a large grid of thermochemical models for Herbig disks, which they used to measure gas masses for a large sample of Herbig disks. In order to have a gas mass measurement method as consistent as possible for both T-Tauri and Herbig disks we use the model grid from (cite: Stapper2024) and fit the observations, in this case the $^{13}\mathrm{CO}$, and $\mathrm{C}^{18}\mathrm{O}$, using a similar MCMC as was used for the T-Tauri disks. For consistency we also compare our derived Herbig disk gas masses with the values obtained by (cite: Stapper2024), finding excellent agreement between the two gas mass estimates, with gas masses being within a factor $\sim3$ ($1\sigma$) from each other.

It should be noted here that the models from (cite: Stapper2024) do not include the peak CO abundances as a free parameter. Several studies find that CO in Herbig disks is underabundant by an order of magnitude (e.g. (cite: PanequeCarreno2024; Rosotti_exoALMA)). However, as we will show in Section [5.4](#sec: n2hp for herbigs), including the CO abundance as a free parameter and fitting $\mathrm{N}_2\mathrm{H}^+$ in addition to the CO lines does not significantly change the derived gas mass.

# Results

## Line based gas disk masses

|  |  |  |  |
|:---|:--:|:--:|:--:|
| name | M$_{\rm gas}$ | $\log_{10}~\mathrm{x}_{\rm CO}$ | $\log_{10}~\zeta_{\rm mid}$ |
|  | \[M$_{\odot}$\] | \[-\] | \[s$^{-1}$\] |
| DM Tau | $0.102^{+0.064}_{-0.042}$ | $-4.24^{+0.15}_{-0.21}$ | $-17.75^{+0.68}_{-0.82}$ |
| V4046 Sgr | $0.035^{+0.018}_{-0.010}$ | $-4.60^{+0.20}_{-0.21}$ | $-17.62^{+0.91}_{-0.97}$ |
| RXJ1615.3-3255 | $0.207^{+0.148}_{-0.090}$ | $-4.12^{+0.08}_{-0.12}$ | \- |
| RXJ1852.3-3700 | $0.057^{+0.052}_{-0.027}$ | $-4.54^{+0.22}_{-0.24}$ | $-16.94^{+0.64}_{-0.98}$ |
| RXJ1842.9-3532 | $0.009^{+0.008}_{-0.004}$ | $-4.60^{+0.21}_{-0.22}$ | \- |
| LkCa 15 | $0.055^{+0.031}_{-0.022}$ | $-4.46^{+0.20}_{-0.21}$ | $-18.66^{+1.03}_{-0.84}$ |
| AA Tau | $0.024^{+0.020}_{-0.009}$ | $-4.60^{+0.24}_{-0.22}$ | $-17.71^{+0.98}_{-1.21}$ |
| PDS 66 | $0.050^{+0.102}_{-0.031}$ | $-5.53^{+0.28}_{-0.29}$ | $-17.55^{+0.96}_{-0.94}$ |
| HD 143006 | $0.021^{+0.024}_{-0.009}$ | $-5.11^{+0.25}_{-0.23}$ | \- |
| HD 135344B | $0.024^{+0.071}_{-0.014}$ | $-4.13^{+0.10}_{-0.17}$ | \- |
| CQ Tau | $0.049^{+0.092}_{-0.024}$ | $\mathit{-4.50^{+0.30}_{-0.08}}$$^{(\dagger)}$ | \- |
| HD 34282 | $0.148^{+0.082}_{-0.052}$ | $-4.11^{+0.07}_{-0.12}$ | \- |
| MWC 758 | $0.031^{+0.076}_{-0.018}$ | $-4.25^{+0.15}_{-0.21}$ | \- |
| GM Aur | $0.069^{+0.072}_{-0.029}$ | $-4.38^{+0.21}_{-0.23}$ | $-18.66^{+0.81}_{-0.77}$ |
| AS 209 | $0.087^{+0.132}_{-0.055}$ | $-4.68^{+0.25}_{-0.26}$ | $-16.80^{+0.54}_{-0.85}$ |
| IM Lup | $0.041^{+0.037}_{-0.018}$ | $-4.45^{+0.21}_{-0.20}$ | $-18.52^{+0.70}_{-0.79}$ |
| MWC 480 | $0.066^{+0.057}_{-0.020}$ | $-4.22^{+0.15}_{-0.21}$ | \- |
| HD 163296 | $0.074^{+0.078}_{-0.030}$ | $-4.28^{+0.17}_{-0.21}$ | \- |
| Elias 2-27 | $0.060^{+0.053}_{-0.030}$ | $-4.20^{+0.14}_{-0.19}$ | $-19.48^{+0.41}_{-0.33}$ |

: Emission line based gas masses

**Notes:** Best fit gas disk masses are the median of $M_{\rm gas}$-posteriors presented in Figures [3](#fig: disk mass comparisons) , with the uncertainties being the 16$^{\rm th}$ and 84$^{\rm th}$ quantile of the distribution. Herbig disk CO abundances are from the models discussed in Section [5.4](#sec: n2hp for herbigs). Midplane ionization rates are from the fits discussed in Section [5.3](#sec: constraining midplane ionization rates).$^{(\dagger)}$: The $\mathrm{x}_{\rm CO}$ fit for CQ Tau is bimodal and this value should be viewed with caution (see Section [5.4](#sec: n2hp for herbigs) for details).

Figure [3](#fig: disk mass comparisons) shows the gas masses derived from fitting the 225 GHz dust continuum and $^{13}\mathrm{CO}$, $\mathrm{C}^{18}\mathrm{O}$, and $\mathrm{N}_2\mathrm{H}^+$ integrated line fluxes. The gas masses are also summarized in Table [1](#tab: gas masses sample). We find overall high gas masses in the range of $\sim0.01 - 0.1\ \ensuremath{\mathrm{M}_{\odot}}$, which is unsurprising as the disks in the sample are among the brightest, and therefore most massive and/or largest, protoplanetary disks in the Solar neighborhood (e.g. (cite: Oberg2021MAPS; Teague2025exoALMA)).

![](Mgas_versus_Mdust.pdf)

In Figure [4](#fig: mgas versus mdust) we plot $M_{\rm gas}$ against the dust mass, computed from the continuum flux assuming a disk averaged temperature of 20 K and optically thin emission (see also (cite: Hildebrand1983; ansdell2016; manara2023)). We find gas-to-dust mass ratios between $\sim80$ and $\sim530$ for the 19 sources examined here, similar to what is found by (cite: Longarini2025exoALMA) using the kinematically measured gas masses and dust masses derived from the 870 $\mu$m continuum flux. This is a factor of a few higher than the typical ISM value of $\sim100$, which could indicate significant grain growth and inward radial drift. However, given the continuum brightness of our sources it is also very likely that their continuum emission is optically thick, in which case the gas-to-dust mass ratio here represents an upper limit.

Also shown in Figure [4](#fig: mgas versus mdust) are the twenty class II disks from the AGE-PRO ALMA large program (cite: AGEPRO_I_overview). Their gas masses and gas-to-dust ratios are discussed extensively in (cite: AGEPRO_V_gas_masses). We include them here mostly to highlight that in terms of both dust and gas mass the MAPS, AGE-PRO, and exoALMA large programs sample different groups of objects (see (cite: Oberg2021MAPS; AGEPRO_I_overview; Teague2025exoALMA)).

## Comparing with gas disk masses from kinematics

![](Mass_comparison_xVSy.pdf)

Figure [5](#fig: diff mgas vs mgas) shows a comparison of the line emission based gas masses from this work and kinematically measured gas masses from (cite: Veronesi2021; Martire2024; Longarini2025exoALMA) for 15 disks. Note that for five disks, AA Tau, RXJ1615.3-3255, RXJ1852.3-3700, PDS 66, and AS 209, the kinematically measured gas mass is an upper limit, set to $\ensuremath{M_{\rm disk}}/\ensuremath{M_{*}}= 5\%$ (see (cite: Martire2024; Longarini2025exoALMA) for details on these sources). For the five MAPS disks covered in (cite: Martire2024) we have adopted minimum gas mass uncertainties of 25% of the measured gas disk mass as recommended by (cite: Andrews2024; Veronesi2024).

Overall the two methods agree with each other within their respective errors. Quantitatively, we find that both gas mass estimates agree within $1-2\sigma$ and lie within a factor 2-3 of each other. Interestingly we also see that the line based gas disk masses are consistently lower than the kinematically measured gas masses. Assuming that the kinematically measured gas masses represent the true disk mass, this suggests that the line based gas mass, or at least our method of deriving it, underestimates the true disk mass by a small factor. To quantify this factor we compute the median ratio using a Kaplan-Meier estimator. To incorporate the uncertainties on each gas mass we repeat this process 10000 times, each time drawing random line-emission and kinematically measured gas masses from their respective posterior distributions. We find that the dynamical masses in our sample are on average $2.3^{+0.7}_{-1.0}\times$ higher than the CO + $\mathrm{N}_2\mathrm{H}^+$ gas masses. We will discuss possible explanations for this in more detail in Section [5.1](#sec: interpreting the (dis)agreement between the mass measurement methods).

Three sources show large differences between their two gas disk mass estimates. RXJ1842.9-3532 and AA Tau have CO + $\mathrm{N}_2\mathrm{H}^+$ gas masses that are $\sim5\times$ lower than their kinematically measured gas masses, while the CO + $\mathrm{N}_2\mathrm{H}^+$ gas mass of RXJ1615.3-3255 is $\gtrsim 4\times$ larger than its kinematically measured one. For AA Tau the uncertainties on the gas mass from kinematics are large due to its high inclination and difficulties in extracting its thermal structure (see (cite: Longarini2025exoALMA; GallowaySprietsma2025exoALMA)). As a result of this its two gas estimates are within $2\sigma$ of each other, similar to many of the other sources. For RXJ1842.9-3532 the uncertainties on both gas measurements are too small to explain their difference. From the kinematics side, a possible explanation could be that in the inner disk the $^{12}$CO and $^{13}\mathrm{CO}$ emitting heights overlap, thereby complicating the extraction of the temperature structure. From the chemistry side, a low midplane ionization rate $(\ensuremath{\zeta_{\rm mid}}\lesssim 10^{-19}\ \mathrm{s}^{-1})$ and/or an underabundance in N$_2$ could cause us to underestimate the CO + $\mathrm{N}_2\mathrm{H}^+$ gas mass of RXJ1842.9-3532. The difference for RXJ1615.3-3255 is harder to explain. As we will discuss in more detail in Section [5.1](#sec: interpreting the (dis)agreement between the mass measurement methods), possible biases in the CO + $\mathrm{N}_2\mathrm{H}^+$ gas mass measurement are more likely to underestimate the true disk mass. And kinematically this source does not show any obvious signs that could indicate that its kinematically measured mass is underestimated. It is worth mentioning that using CO + $\mathrm{N}_2\mathrm{H}^+$ RXJ1615.3-3255 has a star-to-disk mass ratio of $\sim0.2$, which would have left a detectable kinematic signature (see (cite: Andrews2024; Veronesi2024)).

# Discussion

## Interpreting the (dis)agreement between the two gas mass measurement methods

The previous section showed that emission line based and kinematically measured gas masses agree with each other, with the former typically being a factor $\sim2\times$ smaller than the latter. This is a promising result given that historically disk mass estimates could differ by up to two orders of magnitude (e.g. (cite: Miotello2023). However, we should keep in mind that both methods have their own set of systematic uncertainties. Here we highlight the most important ones for both methods and discuss how this affects the agreement in derived gas masses.

Starting with the kinematically measured gas masses, excellent summaries of the systematics were published by (cite: Andrews2024) and (cite: Veronesi2024). In addition to observational effects such as spatial resolution bias, the main uncertainties for a kinematically measured gas mass are the temperature structure of the disk and the measurement of the emitting surface. The temperature is commonly measured from optically thick CO emission at one or more heights in the disk, depending on the number of available optically thick CO lines (e.g. (cite: Law2021bMAPS; GallowaySprietsma2025exoALMA)), and must then be extrapolated to the midplane. Tests using both toy models and hydrodynamical simulations suggest that for massive disks $(\ensuremath{M_{\rm disk}}/\ensuremath{M_{*}}\geq 0.1)$ the true disk mass can be recovered with little bias $(\lesssim20\%)$ and relatively low uncertainties $(\lesssim25\%)$ (see (cite: Andrews2024; Veronesi2024) for details.)

Measuring the disk mass from line emission is more indirect than using kinematics because it, by necessity, requires the use of indirect tracers like CO as proxies for the bulk H$_2$. Most of the systematic uncertainties therefore arise from the assumptions made in the thermochemical models used to link the emission to the underlying gas mass. (cite: AGEPRO_V_gas_masses) provides a summary the main uncertainties for the method used in this work to measure line based gas masses, including the N$_2$ abundances, midplane ionization rate, and model assumptions. The first two most likely lead to an underestimation of the gas mass, which could explain why the line-based gas masses are lower than the kinematically measured ones. We will discuss the role of the cosmic ray ionization rate in more detail in Section [5.3](#sec: constraining midplane ionization rates). As for the model assumption, (cite: AGEPRO_III_Lupus) showed that different thermochemical models seem to converge when it comes to the derived gas mass, particularly for the larger, more massive disks.

The vertical temperature structure of the disk can also have an important effect on line fluxes. (cite: QiWilner2024) showed that the presence of a thick vertical isothermal layer causes the CO column density to drop substantially beyond the CO iceline, resulting in a narrow ring of $\mathrm{N}_2\mathrm{H}^+$ emission and lower integrated CO isotopologue fluxes (see also (cite: Qi2019)). The presence of such a layer could therefore explain the difference between the line based and kinematically measured gas masses. However, (cite: Qi2019) also showed that thick vertically isothermal layers are not present in three of their six disk sample, suggesting that it might not be a universal feature of protoplanetary disks.

![](Gas_masses_with_and_without_cavities_v2.pdf)

To summarize, the kinematically measured gas mass provides a more direct measure of the true disk mass. However, it requires the disk to be massive relative to its star ($\ensuremath{M_{\rm gas}}/\ensuremath{M_{*}}\geq 0.05$), at intermediate inclination and overall axi-symmetric. Furthermore, measuring the disk mass requires a good understanding of the disk temperature structure and the line emitting height. Conversely, the CO + $\mathrm{N}_2\mathrm{H}^+$ based gas mass measurement technique is more broadly applicable as it only requires integrated fluxes and can therefore be applied to a large sample, but it is more indirect and relies on our understanding of CO and $\mathrm{N}_2\mathrm{H}^+$ disk chemistry. It is therefore encouraging to see that both gas mass measurement techniques lie within a small factor ($\sim 2-3\times$) of each other.

## The effect of an inner dust cavity on measuring gas masses

As can be seen in Figure [1](#fig: B7 obs gallery), a large number of the disks in this sample have large inner dust cavities (see also (cite: Curone2025exoALMA)). These cavities are not included in the full disk thermochemical models of (cite: AGEPRO_V_gas_masses), but their presence will have an effect on the temperature structure of the disk (e.g. (cite: Bruderer2013; Leemker2022)) which could affect the gas mass measurement. To quantify the effect of a dust cavity on our gas masses we ran an additional set of models following the same setup as in (cite: AGEPRO_V_gas_masses), but with inner dust cavities of 10, 30, and 60 au. These cavities are included as in e.g. (cite: Bruderer2012; vdMarel2015), with the dust density inside the cavity set to zero. We do also include a small inner dust disk with a radius of 3 au and a dust depletion factor of $10^{-2}$, in line with the typical inner dust disks found in the survey of (cite: FrancisvdMarel2020). As it is computationally impracticable to rerun the full model grid we only run the dust cavity models for $\ensuremath{M_{\rm disk}}\in \left[10^{-4}, 10^{-3}, 10^{-2}, 10^{-1}\right]\ \ensuremath{\mathrm{M}_{\odot}}$, $L_* = \left[0.25, 0.5, 1.0\right] \ensuremath{\mathrm{L}_{\odot}}$, $\ensuremath{R_{\rm c}}\in \left[30, 60, 120, 180 \right] \mathrm{au}$. As the maximum stellar luminosity of these models is not representative of the Herbigs in our sample we will limit our analysis to the T-Tauri disks with dust cavities.

Using these dust cavity models we re-derive $M_{\rm gas}$ for six T-Tauri disks with observed dust cavities: AA Tau, DM Tau, LkCa 15, RXJ1842.9-3532, RXJ1852.3-3700, and V4046 Sgr. These $M_{\rm gas}$ are measured in the same fashion as is outlined in Section [3](#sec: methods) except that the dust cavity size is now included as a free parameter, for which we assume a Gaussian prior with a mean equal to dust cavity size from (cite: FrancisvdMarel2020) and a standard deviation of 10 au ($\sim0.5\times$ the typical beam of the observations used to measure the dust cavity size). Figure [6](#fig: cavity gas masses) shows the resulting gas mass posterior distributions and compares them to the ones obtained using the full disk models. In all cases the gas mass decreases when a dust cavity is included. This is unsurprising as the presence of the cavity increases the overall disk temperature and therefore the line brightness of the CO lines, meaning that the observations can be reproduced with a lower gas mass. However, Figure [6](#fig: cavity gas masses) also shows that this effect is typically small: For the six disks examined there the reduction in gas mass is within a factor $\sim2.5$.

## Constraining midplane ionization rates

![](Cosmic_ray_ionization_rates.pdf)

As an ion, the abundance of $\mathrm{N}_2\mathrm{H}^+$ depends on the midplane ionization rate, which is relatively poorly understood in protoplanetary disks (e.g. (cite: Cleeves2015; Seifert2021; Aikawa2022MAPS; Long2024)). It is therefore one of the main sources of uncertainty for a disk mass obtained from CO isotopologues and $\mathrm{N}_2\mathrm{H}^+$. However, given our additional constraints on the gas mass from kinematics, we can also exploit this dependence and use $\mathrm{N}_2\mathrm{H}^+$ to constrain the midplane ionization rate. We note here that ionization in the midplane of our models is set with a single ionization rate. In the disk midplane cosmic rays are thought to be the dominant source of ionization, but other sources, e.g. decay of radionuclides, scattered X-rays, can also contribute or even dominate if e.g. the midplane is shielded (e.g. (cite: Cleeves2015)). The midplane ionization rate discussed here should therefore be interpreted as the sum of these processes. It should also be noted that we are keeping the N$_2$ abundance fixed, effectively assuming that it is the main Nitrogen carrier in the disk. If this is not the case and the N$_2$ abundance is lower then the midplane ionization rates derived here would have to be higher to reproduce the observed amount of $\mathrm{N}_2\mathrm{H}^+$.

Figure [7](#fig: derived CR rates) shows the posterior distributions of $\zeta_{\rm mid}$ where we have refit the observations but now use the kinematically derived gas masses and their uncertainties as a prior during the fit. We exclude RXJ1842.9-3532 and RXJ1615.3-3255 as their line-based and kinematic gas mass proved too different from each other to use the kinematic gas mass as a prior while fitting the line emission. Overall we find a wide range of midplane ionization rates, from $\ensuremath{\zeta_{\rm mid}}\approx10^{-17}\ \mathrm{s}^{-1}$ for AS 209 and RXJ1852.3-3700 to $\ensuremath{\zeta_{\rm mid}}\approx 3\times10^{-20}\ \mathrm{s}^{-1}$ for Elias 2-27. We find a median ionization rate of $\ensuremath{\zeta_{\rm mid}}= 1.5\times10^{-18}\ \mathrm{s}^{-1}$. However, the uncertainty of $\zeta_{\rm mid}$ for individual sources is large, typically $\sim1.5$ dex, suggesting that $\mathrm{N}_2\mathrm{H}^+$ alone only provides a moderate constrain on the ionization rate.

Comparing our rough, disk-averaged rates to previous studies that used more complex models and observations of multiple ions (e.g. (cite: Seifert2021; Aikawa2022MAPS; Long2024)) we find overall agreement. For example, (cite: Long2024) find a moderate ionization rate of $10^{-18}\ \mathrm{s}^{-1}$ for DM Tau which agrees very well with our median value for the source $(\ensuremath{\zeta_{\rm mid}}=1.5\times10^{-18}\ \mathrm{s}^{-1})$. Similarly, (cite: Aikawa2022MAPS) report midplane ionization rates $(\zeta_{\rm mid})$ of $\zeta_{\rm mid} \gtrsim 10^{-18}\ \mathrm{s}^{-1}$ for AS 209 and IM Lup, and $\zeta_{\rm mid} \lesssim 10^{-18}\ \mathrm{s}^{-1}$ for GM Aur. For AS 209 and GM Aur our results are in agreement with (cite: Aikawa2022MAPS), but for IM Lup we find a somewhat lower value of $\sim3\times10^{-19}\ \mathrm{s}^{-1}$. However, (cite: Seifert2021) showed that IM Lup has radially varying midplane ionization rate, with $\zeta_{\rm mid} \lesssim 10^{-20}\ \mathrm{s}^{-1}$ inside 100 au and $\zeta_{\rm mid} \gtrsim 10^{-17}\ \mathrm{s}^{-1}$ between 100 and 300 au. As our sole constraint comes from the integrated $\mathrm{N}_2\mathrm{H}^+$ flux we are probing a mix of these two regions, which could explain our overall lower midplane ionization rate.

## The role of $\mathrm{N}_2\mathrm{H}^+$ in constraining Herbig gas disk masses

![](Herbigs_with_and_without_N2Hp.pdf)

In this work we have measured gas masses for T-Tauri and Herbig disks in slightly different ways, the largest difference being that for the Herbig disks we do not fit the $\mathrm{N}_2\mathrm{H}^+$ observations. Initial gas measurements using CO found that the gas-to-dust mass ratios of T-Tauri disks were much lower than the interstellar medium value of $\sim100$ (e.g. (cite: WilliamsBest2014; miotello2017; Long2017)). Comparisons with other gas mass traces such as HD (cite: Bergin2013; McClure2016) suggested that the CO is underabundant in the warm molecular layer of protoplanetary disks, leading to the inclusion of $\mathrm{N}_2\mathrm{H}^+$ as an additional constraint on the gas-phase CO abundance (cite: Anderson2019; Anderson2022; Trapman2022b; AGEPRO_V_gas_masses). For Herbig disks CO-based gas-to-dust mass ratios are routinely found to be at or above the ISM value of $\sim100$ (e.g. (cite: Stapper2024)). This suggests that the processes that reduce the gas-phase CO abundance in T-Tauri disks do not significantly affect disks around Herbig stars.

However, this does not exclude the possibility that the gas-phase CO in Herbig disks could be at least mildly underabundant and that their CO-based gas masses could therefore underestimate their true gas masses. Indeed, several studies have found that at least some Herbig disks seem underabundant in CO to some degree (e.g. (cite: Zhang2021MAPS; PanequeCarreno2024; Rosotti_exoALMA)). We can test this hypothesis by fitting the $\mathrm{N}_2\mathrm{H}^+$ flux in addition to the CO fluxes, identical to how we fitted the T-Tauri disks (see Section [3](#sec: methods)). Unfortunately the models in (cite: Stapper2024) do not include synthetic observations of $\mathrm{N}_2\mathrm{H}^+$. We therefore ran another set of models analogous to the new $L_* = 3\ \ensuremath{\mathrm{L}_{\odot}}$ models described in Section [3](#sec: methods) but using the observed stellar spectrum of HD 163296 ($L_* = 17\ \ensuremath{\mathrm{L}_{\odot}}$; (cite: Dionatos2019)).

Using these models we fit the observations of the six Herbig disks in our sample twice, once where we fit the 1.3 mm continuum and $^{13}\mathrm{CO}$, $\mathrm{C}^{18}\mathrm{O}$, and $\mathrm{N}_2\mathrm{H}^+$ line fluxes while having the peak CO abundance be a free parameter and once where we fit the 1.3 mm continuum and $^{13}\mathrm{CO}$, $\mathrm{C}^{18}\mathrm{O}$ line fluxes and keep the peak CO abundance fixed (analogous to fitting the Herbig disks using the (cite: Stapper2024) models). We note the (cite: Stapper2024) models cover a wider range of parameters relevant for Herbig disks (e.g, $L_*$, scale height) and have a higher mass resolution that our models. The disk masses derived here do therefore not supersede the ones presented in Section [4.1](#sec: line based gas disk masses).

Figure [8](#fig: Herbig with N2Hp) shows the resulting gas mass posteriors for the two fits. For all six source we find that the gas masses are near identical, with the mean estimates lying within $\sim15\%$ of each other. The dual peak structure of the posterior of CQ Tau is due to a lack of models. Its best fit characteristic radius using the (cite: Stapper2024) models is $\ensuremath{R_{\rm c}}\approx 12$ au, while the smallest model in our grid with $\ensuremath{M_{\rm disk}}= 0.5~\ensuremath{\mathrm{M}_{\odot}}$ has $\ensuremath{R_{\rm c}}=15$ au. This causes the MCMC to oscillate between these models and models with $\ensuremath{M_{\rm disk}}= 0.1~\ensuremath{\mathrm{M}_{\odot}}, \ensuremath{R_{\rm c}}=5$ au, which are included in the grid. Due to this incomplete fit we caution against using the $\ensuremath{x_{\rm CO}}$ for CQ Tau and we have excluded it from our analysis here.

![](xCO_histogram.pdf)

Figure [9](#fig: median CO abundances) shows a histogram of the median peak CO abundances of the Herbig disks discussed here and the T-Tauri disks examined previously. For the Herbig disks we find median values of $\log_{10} \ensuremath{x_{\rm CO}}\approx -4.35 - 4.1$, which is very close to the ISM value of $\log_{10} \ensuremath{x_{\rm CO}}\approx -4$. Peak CO abundances of the T-Tauri disks are typically lower, peaking at $\log_{10} \ensuremath{x_{\rm CO}}\approx -4.6$ and they can be as low as $\log_{10} \ensuremath{x_{\rm CO}}= -5.6$ (Table [1](#tab: gas masses sample)).

This suggests different chemical paths for the T-Tauri and Herbig disks, where in the colder T-Tauri disks a significant fraction of the gaseous CO freezes out and is converted into less volatile species such as CO$_2$, whereas in the warmer Herbig disks most of the CO stays in the gas and is not chemically converted (see (cite: Oberg2023) for a recent review).

The high peak CO abundances found here seem at odds with the lower values found in other works (e.g. (cite: Zhang2021MAPS; PanequeCarreno2024; Rosotti_exoALMA)). (cite: PanequeCarreno2024) and (cite: Rosotti_exoALMA) independently showed that the emitting height of optically thick CO lines are strongly correlated to both the disk mass and the CO abundance. They found that in order to reproduce the CO emitting height of a number of Herbig disks using the gas mass from previous estimates they need reduce the CO abundance by a factor of up to ten.

One possible explanation of the dichotomy between these works and the results here is that the two methods trace different parts of the disk. The $\mathrm{N}_2\mathrm{H}^+$ (3-2) emission predominantly traces the layer between the CO and N$_2$ icelines (e.g. (cite: Qi2013; Qi2019; vantHoff2017)) and is therefore most sensitive to the CO abundance of the gas close to the CO iceline. Conversely, the CO emitting height is most sensitive to the CO abundance at the top of the CO emitting layer, close to where CO is photo-dissociated.

We should note here the these results apply specifically for Herbig disks. Similar tests for T-Tauri disks show that their gas masses can be $\sim3-30\times$ higher and their CO peak gas abundances $\sim3-30\times$ lower if $\mathrm{N}_2\mathrm{H}^+$ is included with CO when measuring gas masses (e.g. Table [1](#tab: gas masses sample); see also (cite: Anderson2019; Anderson2022; Trapman2022; Sturm2023)).

# Conclusions

In this work we have presented new ALMA Band 7 observations of $\mathrm{N}_2\mathrm{H}^+$ (3-2) for 11 protoplanetary disks and Band 6 $\mathrm{C}^{18}\mathrm{O}$ (2-1) observations for one disk. These we combine with archival $\mathrm{N}_2\mathrm{H}^+$, $^{13}\mathrm{CO}$, and $\mathrm{C}^{18}\mathrm{O}$ observations to measure gas disk masses for 19 disks, primarily from the exoALMA and MAPS ALMA Large programs. For the 15 disks where kinematically measured gas masses are available we compare the two gas mass measuring techniques. Our main conclusions are listed below

- For T-Tauri disks we find clear correlations between the continuum flux and the $\mathrm{C}^{18}\mathrm{O}$ and $\mathrm{N}_2\mathrm{H}^+$ line fluxes similar to what previously found in the literature. Disks around Herbig stars lie on the same $\mathrm{C}^{18}\mathrm{O}$-continuum flux correlation, but have 1-2 orders of magnitude lower $\mathrm{N}_2\mathrm{H}^+$ fluxes compared to T-Tauri disks with similar continuum fluxes. This is likely due to the higher overall temperature and lower CO freeze-out in these disks, resulting in less CO-poor gas and therefore lower overall $\mathrm{N}_2\mathrm{H}^+$ abundances.

- We find overall high gas masses between $\sim0.01-0.1\ \ensuremath{\mathrm{M}_{\odot}}$ and gas-to-dust mass ratios in the range $\sim80-530$ for our sources. However, these high gas-to-dust ratios are likely lower upper limits due the continuum emission used to derive dust masses being optically thick.

- There is good agreement between the line emission based gas masses from this work and the ones measured from gas kinematics in the literature. With two exceptions, RXJ1842.9-3532 and RXJ1615.3-3255, the gas estimates from the two methods lie within a factor $\sim3$ ($1-2\sigma$) from each other.

- Gas disk masses from CO + $\mathrm{N}_2\mathrm{H}^+$ are on average a factor $2.3^{+0.7}_{-1.0}\times$ lower than the kinematically measured gas masses. Assuming the kinematics trace the true disk mass, this could point towards slightly lower N$_2$ abundances and/or lower midplane ionization rates than typically assumed.

- Herbig disks are found to have ISM level CO gas abundances based on their CO and $\mathrm{N}_2\mathrm{H}^+$ fluxes, which sets them apart from T-Tauri disks where the CO abundance in the CO emitting layer is typically $\sim3-30\times$ lower.

The agreement between the gas masses measured from gas kinematics and CO + $\mathrm{N}_2\mathrm{H}^+$ is promising as the former provides direct estimate of the mass that does not depend on disk chemistry, whereas the latter is much broadly applicable. It shows that multi-molecule line fluxes are a robust tool to accurately measure disk masses at least for extended disks.

# acknowledgements

We would like to thank the anonymous referee for their insightful feedback. LT and KZ acknowledge the support of the NSF AAG grant #2205617. CL has received funding from the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska-Curie grant agreement No. 823823 (DUSTBUSTERS) and by the UK Science and Technology research Council (STFC) via the consolidated grant ST/W000997/1. GR acknowledges funding from the Fondazione Cariplo, grant no. 2022-1217, and the European Research Council (ERC) under the European Union’s Horizon Europe Research & Innovation Programme under grant agreement no. 101039651 (DiscEvol). Views and opinions expressed are however those of the author(s) only, and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them. JB acknowledges support from NASA XRP grant No. 80NSSC23K1312.

MB, DF, and JS have received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (PROTOPLANETS, grant agreement No. 101002188). Computations have been done on the ’Mesocentre SIGAMM’ machine,hosted by Observatoire de la Cote d’Azur.

PC acknowledges support by the Italian Ministero dell’Istruzione, Università e Ricerca through the grant Progetti Premiali 2012 – iALMA (CUP C52I13000140001) and by the ANID BASAL project FB210003. S.F. is funded by the European Union (ERC, UNVEIL, 101076613). Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council. Neither the European Union nor the granting authority can be held responsible for them. S.F. acknowledges financial contribution from PRIN-MUR 2022YP5ACE.

MF is supported by a Grant-in-Aid from the Japan Society for the Promotion of Science (KAKENHI: No. JP22H01274).

JDI acknowledges support from an STFC Ernest Rutherford Fellowship (ST/W004119/1) and a University Academic Fellowship from the University of Leeds. Support for AFI was provided by NASA through the NASA Hubble Fellowship grant No. HST-HF2-51532.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555.

GL acknowledges support from the European Union’s Horizon 2020 research and innovation programme under the Marie Sklodowska-Curie grant agreement #823823 (RISE DUSTBUSTERS project) and from the Italian MUR through PRIN 20228JPA3A.

C.P. acknowledges Australian Research Council funding via FT170100040, DP18010423, DP220103767, and DP240103290.

H.-W.Y. acknowledges support from National Science and Technology Council (NSTC) in Taiwan through grant NSTC 110-2628-M-001-003-MY3 and from the Academia Sinica Career Development Award (AS-CDA-111-M03).

Support for BZ was provided by The Brinson Foundation. CH acknowledges support from the National Science Foundation Astronomy and Astrophysics Research Grants program No. 2407679. AJW has received funding from the European Union’s Horizon 2020 research and innovation programme under the Marie Skłodowska-Curie grant agreement No 101104656.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2023.1.00334.S, #2022.1.00485.S, #2021.1.01123.L, #2012.1.00158.S, #2012.1.00870.S, #2015.1.00192.S, #2015.1.00678.S, #2015.1.01017.S, #2016.1.00484.L, #2016.1.00724.S, #2017.1.00069.S, #2017.1.00940.S, #2017.1.01404.S, #2017.1.01419.S, #2018.1.00689.S, #2018.1.00945.S, #2018.1.01055.L, #2019.1.01683.S ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

All figures were generated with the `PYTHON`-based package `MATPLOTLIB` (cite: Hunter2007). This research made use of Astropy,[^3] a community-developed core Python package for Astronomy (cite: astropy:2013; astropy:2018).

ALMA

# Software

CASA (cite: McMullin2007; CASAteam2022), Astropy (cite: astropy:2013; astropy:2018), MATPLOTLIB (cite: Hunter2007)

natexlab

(ref: Acke2005) Acke, B., van den Ancker, M. E., & Dullemond, C. P. 2005, A&A, 436, 209, doi: [`10.1051/0004-6361:20042484`](http://doi.org/10.1051/0004-6361:20042484)

(ref: AGEPRO_IV_UpperSco) Agurto-Gangas, C., Pérez, L., Sierra, A., & Miley, J. M. , in press, AAS

(ref: Aikawa1997) Aikawa, Y., Umebayashi, T., Nakano, T., & Miyama, S. M. 1997, The Astrophysical Journal Letters, 486, L51

(ref: Aikawa2002) Aikawa, Y., van Zadelhoff, G., van Dishoeck, E. F., & Herbst, E. 2002, A&A, 386, 622

(ref: Aikawa2022MAPS) Aikawa, Y., Cataldi, G., Yamato, Y., et al. 2021, ApJS, 257, 13, doi: [`10.3847/1538-4365/ac143c`](http://doi.org/10.3847/1538-4365/ac143c)

(ref: alcala2017) Alcalá, J., Manara, C., Natta, A., et al. 2017, Astronomy & Astrophysics, 600, A20

(ref: Alcala2019) Alcalá, J. M., Manara, C. F., France, K., et al. 2019, A&A, 629, A108, doi: [`10.1051/0004-6361/201935657`](http://doi.org/10.1051/0004-6361/201935657)

(ref: Anderson2019) Anderson, D. E., Blake, G. A., Bergin, E. A., et al. 2019, ApJ, 881, 127, doi: [`10.3847/1538-4357/ab2cb5`](http://doi.org/10.3847/1538-4357/ab2cb5)

(ref: Anderson2022) Anderson, D. E., Cleeves, L. I., Blake, G. A., et al. 2022, ApJ, 927, 229, doi: [`10.3847/1538-4357/ac517e`](http://doi.org/10.3847/1538-4357/ac517e)

(ref: Anderson2024) —. 2024, ApJ, 966, 84, doi: [`10.3847/1538-4357/ad2fa2`](http://doi.org/10.3847/1538-4357/ad2fa2)

(ref: Andrews2024) Andrews, S. M., Teague, R., Wirth, C. P., Huang, J., & Zhu, Z. 2024, ApJ, 970, 153, doi: [`10.3847/1538-4357/ad5285`](http://doi.org/10.3847/1538-4357/ad5285)

(ref: Andrews2018b) Andrews, S. M., Terrell, M., Tripathi, A., et al. 2018a, ApJ, 865, 157, doi: [`10.3847/1538-4357/aadd9f`](http://doi.org/10.3847/1538-4357/aadd9f)

(ref: Andrews2018) —. 2018b, ApJ, 865, 157, doi: [`10.3847/1538-4357/aadd9f`](http://doi.org/10.3847/1538-4357/aadd9f)

(ref: Andrews2009) Andrews, S. M., Wilner, D., Hughes, A., Qi, C., & Dullemond, C. 2009, AJ, 700, 1502

(ref: Andrews2011) Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42, doi: [`10.1088/0004-637X/732/1/42`](http://doi.org/10.1088/0004-637X/732/1/42)

(ref: ansdell2016) Ansdell, M., Williams, J. P., van der Marel, N., et al. 2016, The Astrophysical Journal, 828, 46

(ref: ansdell2018) Ansdell, M., Williams, J. P., Trapman, L., et al. 2018, ApJ, 859, 21, doi: [`10.3847/1538-4357/aab890`](http://doi.org/10.3847/1538-4357/aab890)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Barenfeld2016) Barenfeld, S. A., Carpenter, J. M., Ricci, L., & Isella, A. 2016, The Astrophysical Journal, 827, 142

(ref: Beckwith1990) Beckwith, S. V. W., Sargent, A. I., Chini, R. S., & Guesten, R. 1990, AJ, 99, 924, doi: [`10.1086/115385`](http://doi.org/10.1086/115385)

(ref: Bergin2010) Bergin, E., Hogerheijde, M., Brinch, C., et al. 2010, Astronomy & Astrophysics, 521, L33

(ref: Bergin2016) Bergin, E. A., Du, F., Cleeves, L. I., et al. 2016, ApJ, 831, 101, doi: [`10.3847/0004-637X/831/1/101`](http://doi.org/10.3847/0004-637X/831/1/101)

(ref: BerginWilliams2018) Bergin, E. A., & Williams, J. P. 2018, ArXiv e-prints. [`https://arxiv.org/abs/1807.09631`](https://arxiv.org/abs/1807.09631)

(ref: Bergin2013) Bergin, E. A., Cleeves, L. I., Gorti, U., et al. 2013, Nature, 493, 644, doi: [`10.1038/nature11805`](http://doi.org/10.1038/nature11805)

(ref: Bergner2019) Bergner, J. B., Öberg, K. I., Bergin, E. A., et al. 2019, ApJ, 876, 25, doi: [`10.3847/1538-4357/ab141e`](http://doi.org/10.3847/1538-4357/ab141e)

(ref: Birnstiel2024) Birnstiel, T. 2023, arXiv e-prints, arXiv:2312.13287, doi: [`10.48550/arXiv.2312.13287`](http://doi.org/10.48550/arXiv.2312.13287)

(ref: Bosman2018b) Bosman, A. D., Walsh, C., & van Dishoeck, E. F. 2018, A&A, 618, A182, doi: [`10.1051/0004-6361/201833497`](http://doi.org/10.1051/0004-6361/201833497)

(ref: Bouvier1999) Bouvier, J., Chelli, A., Allain, S., et al. 1999, A&A, 349, 619

(ref: Bruderer2013) Bruderer, S. 2013, A&A, 559, A46, doi: [`10.1051/0004-6361/201321171`](http://doi.org/10.1051/0004-6361/201321171)

(ref: Bruderer2012) Bruderer, S., van Dishoeck, E. F., Doty, S. D., & Herczeg, G. J. 2012, A&A, 541, A91, doi: [`10.1051/0004-6361/201118218`](http://doi.org/10.1051/0004-6361/201118218)

(ref: calahan2021) Calahan, J. K., Bergin, E., Zhang, K., et al. 2021, ApJ, 908, 8, doi: [`10.3847/1538-4357/abd255`](http://doi.org/10.3847/1538-4357/abd255)

(ref: Carmona2011) Carmona, A., van der Plas, G., van den Ancker, M. E., et al. 2011, A&A, 533, A39, doi: [`10.1051/0004-6361/201116561`](http://doi.org/10.1051/0004-6361/201116561)

(ref: CASAteam2022) CASA-Team, Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacific, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Cleeves2015) Cleeves, L. I., Bergin, E. A., Qi, C., Adams, F. C., & Öberg, K. I. 2015, ApJ, 799, 204, doi: [`10.1088/0004-637X/799/2/204`](http://doi.org/10.1088/0004-637X/799/2/204)

(ref: Curone2025exoALMA) Curone, P., Facchini, S., Andrews, S. M., & Testi, L. , in press, ApJL

(ref: Czekala2021MAPS) Czekala, I., Loomis, R. A., Teague, R., et al. 2021, ApJS, 257, 2, doi: [`10.3847/1538-4365/ac1430`](http://doi.org/10.3847/1538-4365/ac1430)

(ref: DAlessio1998) D’Alessio, P., Cantö, J., Calvet, N., & Lizano, S. 1998, ApJ, 500, 411, doi: [`10.1086/305702`](http://doi.org/10.1086/305702)

(ref: AGEPRO_III_Lupus) Deng, D., Pascucci, I., & Vioque, M. , in press, AAS

(ref: Dent2005) Dent, W. R. F., Greaves, J. S., & Coulson, I. M. 2005, MNRAS, 359, 663, doi: [`10.1111/j.1365-2966.2005.08938.x`](http://doi.org/10.1111/j.1365-2966.2005.08938.x)

(ref: Dionatos2019) Dionatos, O., Woitke, P., Güdel, M., et al. 2019, A&A, 625, A66, doi: [`10.1051/0004-6361/201832860`](http://doi.org/10.1051/0004-6361/201832860)

(ref: Drazkowska2023) Drażkowska, J., Bitsch, B., Lambrechts, M., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 717, doi: [`10.48550/arXiv.2203.09759`](http://doi.org/10.48550/arXiv.2203.09759)

(ref: Dutrey1996) Dutrey, A., Guilloteau, S., Duvert, G., et al. 1996, A&A, 309, 493

(ref: Espaillat2010) Espaillat, C., D’Alessio, P., Hernández, J., et al. 2010, ApJ, 717, 441, doi: [`10.1088/0004-637X/717/1/441`](http://doi.org/10.1088/0004-637X/717/1/441)

(ref: Fairlamb2015) Fairlamb, J. R., Oudmaijer, R. D., Mendigutı́a, I., Ilee, J. D., & van den Ancker, M. E. 2015, MNRAS, 453, 976, doi: [`10.1093/mnras/stv1576`](http://doi.org/10.1093/mnras/stv1576)

(ref: Flaherty2020) Flaherty, K., Hughes, A. M., Simon, J. B., et al. 2020, ApJ, 895, 109, doi: [`10.3847/1538-4357/ab8cc5`](http://doi.org/10.3847/1538-4357/ab8cc5)

(ref: FrancisvdMarel2020) Francis, L., & van der Marel, N. 2020, ApJ, 892, 111, doi: [`10.3847/1538-4357/ab7b63`](http://doi.org/10.3847/1538-4357/ab7b63)

(ref: FuruyaAikawa2014) Furuya, K., & Aikawa, Y. 2014, ApJ, 790, 97, doi: [`10.1088/0004-637X/790/2/97`](http://doi.org/10.1088/0004-637X/790/2/97)

(ref: Furuya2022) Furuya, K., Lee, S., & Nomura, H. 2022, ApJ, 938, 29, doi: [`10.3847/1538-4357/ac9233`](http://doi.org/10.3847/1538-4357/ac9233)

(ref: GallowaySprietsma2025exoALMA) Galloway-Sprietsma, M., & Bae, J. , in press, ApJL

(ref: Guzman-Diaz2021) Guzmán-Dı́az, J., Mendigutı́a, I., Montesinos, B., et al. 2021, A&A, 650, A182, doi: [`10.1051/0004-6361/202039519`](http://doi.org/10.1051/0004-6361/202039519)

(ref: Hendler2020) Hendler, N., Pascucci, I., Pinilla, P., et al. 2020, ApJ, 895, 126, doi: [`10.3847/1538-4357/ab70ba`](http://doi.org/10.3847/1538-4357/ab70ba)

(ref: Herbig1960) Herbig, G. H. 1960, ApJS, 4, 337, doi: [`10.1086/190050`](http://doi.org/10.1086/190050)

(ref: Herbig1977) —. 1977, ApJ, 214, 747, doi: [`10.1086/155304`](http://doi.org/10.1086/155304)

(ref: HerbigBell1988) Herbig, G. H., & Bell, K. R. 1988, Third Catalog of Emission-Line Stars of the Orion Population : 3 : 1988

(ref: Hildebrand1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: Hunter2007) Hunter, J. D. 2007, Computing in science & engineering, 9, 90

(ref: Izquierdo_exoALMA) Izquierdo, A. F. , in press, ApJL, TBD

(ref: JorsatervanMoorsel1995) Jorsater, S., & van Moorsel, G. A. 1995, AJ, 110, 2037, doi: [`10.1086/117668`](http://doi.org/10.1086/117668)

(ref: Kama2016) Kama, M., Bruderer, S., van Dishoeck, E. F., et al. 2016, A&A, 592, A83, doi: [`10.1051/0004-6361/201526991`](http://doi.org/10.1051/0004-6361/201526991)

(ref: Krijt2020) Krijt, S., Bosman, A. D., Zhang, K., et al. 2020, ApJ, 899, 134, doi: [`10.3847/1538-4357/aba75d`](http://doi.org/10.3847/1538-4357/aba75d)

(ref: Krijt2018) Krijt, S., Schwarz, K. R., Bergin, E. A., & Ciesla, F. J. 2018, ApJ, 864, 78, doi: [`10.3847/1538-4357/aad69b`](http://doi.org/10.3847/1538-4357/aad69b)

(ref: Kuznetsova2022) Kuznetsova, A., Bae, J., Hartmann, L., & Mac Low, M.-M. 2022, ApJ, 928, 92, doi: [`10.3847/1538-4357/ac54a8`](http://doi.org/10.3847/1538-4357/ac54a8)

(ref: Law2021bMAPS) Law, C. J., Teague, R., Loomis, R. A., et al. 2021, ApJS, 257, 4, doi: [`10.3847/1538-4365/ac1439`](http://doi.org/10.3847/1538-4365/ac1439)

(ref: Law2022) Law, C. J., Crystian, S., Teague, R., et al. 2022, arXiv e-prints, arXiv:2205.01776. [`https://arxiv.org/abs/2205.01776`](https://arxiv.org/abs/2205.01776)

(ref: Leemker2022) Leemker, M., Booth, A. S., van Dishoeck, E. F., et al. 2022, A&A, 663, A23, doi: [`10.1051/0004-6361/202243229`](http://doi.org/10.1051/0004-6361/202243229)

(ref: Lodato2023) Lodato, G., Rampinelli, L., Viscardi, E., et al. 2023, MNRAS, 518, 4481, doi: [`10.1093/mnras/stac3223`](http://doi.org/10.1093/mnras/stac3223)

(ref: Long2024) Long, D. E., Cleeves, L. I., Adams, F. C., et al. 2024, ApJ, 972, 88, doi: [`10.3847/1538-4357/ad5c67`](http://doi.org/10.3847/1538-4357/ad5c67)

(ref: Long2017) Long, F., Herczeg, G. J., Pascucci, I., et al. 2017, The Astrophysical Journal, 844, 99

(ref: Longarini2025exoALMA) Longarini, C., Lodato, G., Rosotti, G. P., et al. , in press, ApJL

(ref: Loomis_exoALMA) Loomis, R., Facchini, S., & Benisty, M. , in press, ApJL, TBD

(ref: Loomis2017) Loomis, R. A., Öberg, K. I., Andrews, S. M., & MacGregor, M. A. 2017, ApJ, 840, 23, doi: [`10.3847/1538-4357/aa6c63`](http://doi.org/10.3847/1538-4357/aa6c63)

(ref: Loomis2020) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2020, ApJ, 893, 101, doi: [`10.3847/1538-4357/ab7cc8`](http://doi.org/10.3847/1538-4357/ab7cc8)

(ref: LuhmanMamajek2012) Luhman, K. L., & Mamajek, E. E. 2012, ApJ, 758, 31, doi: [`10.1088/0004-637X/758/1/31`](http://doi.org/10.1088/0004-637X/758/1/31)

(ref: Macias2018) Macı́as, E., Espaillat, C. C., Ribas, Á., et al. 2018, ApJ, 865, 37, doi: [`10.3847/1538-4357/aad811`](http://doi.org/10.3847/1538-4357/aad811)

(ref: Mamajek2002) Mamajek, E. E., Meyer, M. R., & Liebert, J. 2002, AJ, 124, 1670, doi: [`10.1086/341952`](http://doi.org/10.1086/341952)

(ref: manara2023) Manara, C. F., Ansdell, M., Rosotti, G. P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 539, doi: [`10.48550/arXiv.2203.09930`](http://doi.org/10.48550/arXiv.2203.09930)

(ref: Manara2014) Manara, C. F., Testi, L., Natta, A., et al. 2014, A&A, 568, A18, doi: [`10.1051/0004-6361/201323318`](http://doi.org/10.1051/0004-6361/201323318)

(ref: Martire2024) Martire, P., Longarini, C., Lodato, G., et al. 2024, A&A, 686, A9, doi: [`10.1051/0004-6361/202348546`](http://doi.org/10.1051/0004-6361/202348546)

(ref: McClure2016) McClure, M. K., Bergin, E. A., Cleevs, L. I., et al. 2016, AJ

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Miotello2014) Miotello, A., Bruderer, S., & van Dishoeck, E. F. 2014, A&A, 572, A96, doi: [`10.1051/0004-6361/201424712`](http://doi.org/10.1051/0004-6361/201424712)

(ref: Miotello2023) Miotello, A., Kamp, I., Birnstiel, T., Cleeves, L. C., & Kataoka, A. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 501, doi: [`10.48550/arXiv.2203.09818`](http://doi.org/10.48550/arXiv.2203.09818)

(ref: miotello2017) Miotello, A., van Dishoeck, E., Williams, J., et al. 2017, Astronomy & Astrophysics, 599, A113

(ref: Montesinos2009) Montesinos, B., Eiroa, C., Mora, A., & Merı́n, B. 2009, A&A, 495, 901, doi: [`10.1051/0004-6361:200810623`](http://doi.org/10.1051/0004-6361:200810623)

(ref: MorbidelliRaymond2016) Morbidelli, A., & Raymond, S. N. 2016, Journal of Geophysical Research: Planets, 121, 1962

(ref: Oberg2023) Öberg, K. I., Facchini, S., & Anderson, D. E. 2023, ARA&A, 61, 287, doi: [`10.1146/annurev-astro-022823-040820`](http://doi.org/10.1146/annurev-astro-022823-040820)

(ref: Oberg2021MAPS) Oberg, K. I., Guzman, V. V., Walsh, C., et al. 2021, arXiv e-prints, arXiv:2109.06268. [`https://arxiv.org/abs/2109.06268`](https://arxiv.org/abs/2109.06268)

(ref: Paardekooper2023) Paardekooper, S., Dong, R., Duffell, P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 685, doi: [`10.48550/arXiv.2203.09595`](http://doi.org/10.48550/arXiv.2203.09595)

(ref: PanequeCarreno2024) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., Rosotti, G., & Tabone, B. 2025, arXiv e-prints, arXiv:2501.08294, doi: [`10.48550/arXiv.2501.08294`](http://doi.org/10.48550/arXiv.2501.08294)

(ref: Paneque-Carreno2023) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., et al. 2023, A&A, 669, A126, doi: [`10.1051/0004-6361/202244428`](http://doi.org/10.1051/0004-6361/202244428)

(ref: Paneque-Carreno2021) Paneque-Carreño, T., Pérez, L. M., Benisty, M., et al. 2021, ApJ, 914, 88, doi: [`10.3847/1538-4357/abf243`](http://doi.org/10.3847/1538-4357/abf243)

(ref: Pascucci2013) Pascucci, I., Herczeg, G., Carr, J., & Bruderer, S. 2013, AJ, 779, 178

(ref: Perez2015) Pérez, L. M., Chandler, C. J., Isella, A., et al. 2015, The Astrophysical Journal, 813, 41

(ref: Perez2016) Pérez, L. M., Carpenter, J. M., Andrews, S. M., et al. 2016, Science, 353, 1519, doi: [`10.1126/science.aaf8296`](http://doi.org/10.1126/science.aaf8296)

(ref: pinte23) Pinte, C., Teague, R., Flaherty, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 645, doi: [`10.48550/arXiv.2203.09528`](http://doi.org/10.48550/arXiv.2203.09528)

(ref: Pinte2018) Pinte, C., Ménard, F., Duchêne, G., et al. 2018, A&A, 609, A47, doi: [`10.1051/0004-6361/201731377`](http://doi.org/10.1051/0004-6361/201731377)

(ref: Powell2022) Powell, D., Gao, P., Murray-Clay, R., & Zhang, X. 2022, Nature Astronomy, 6, 1147, doi: [`10.1038/s41550-022-01741-9`](http://doi.org/10.1038/s41550-022-01741-9)

(ref: Qi2015) Qi, C., Öberg, K. I., Andrews, S. M., et al. 2015, ApJ, 813, 128, doi: [`10.1088/0004-637X/813/2/128`](http://doi.org/10.1088/0004-637X/813/2/128)

(ref: QiWilner2024) Qi, C., & Wilner, D. J. 2024, ApJ, 977, 60, doi: [`10.3847/1538-4357/ad8d55`](http://doi.org/10.3847/1538-4357/ad8d55)

(ref: Qi2013) Qi, C., Öberg, K. I., Wilner, D. J., et al. 2013, Science, 341, 630, doi: [`10.1126/science.1239560`](http://doi.org/10.1126/science.1239560)

(ref: Qi2019) Qi, C., Öberg, K. I., Espaillat, C. C., et al. 2019, ApJ, 882, 160, doi: [`10.3847/1538-4357/ab35d3`](http://doi.org/10.3847/1538-4357/ab35d3)

(ref: Quast2000) Quast, G. R., Torres, C. A. O., de La Reza, R., da Silva, L., & Mayor, M. 2000, in IAU Symposium, Vol. 200, IAU Symposium, ed. B. Reipurth & H. Zinnecker, 28

(ref: Ribas2023) Ribas, Á., Macı́as, E., Weber, P., et al. 2023, A&A, 673, A77, doi: [`10.1051/0004-6361/202245637`](http://doi.org/10.1051/0004-6361/202245637)

(ref: Rosotti_exoALMA) Rosotti, G., Longarini, C., & Paneque-Carreño, T. , in press, ApJL, TBD

(ref: Ruaud2019) Ruaud, M., & Gorti, U. 2019, ApJ, 885, 146, doi: [`10.3847/1538-4357/ab4996`](http://doi.org/10.3847/1538-4357/ab4996)

(ref: Ruaud2022) Ruaud, M., Gorti, U., & Hollenbach, D. J. 2022, ApJ, 925, 49, doi: [`10.3847/1538-4357/ac3826`](http://doi.org/10.3847/1538-4357/ac3826)

(ref: Schwarz2018) Schwarz, K. R., Bergin, E. A., Cleeves, L. I., et al. 2018, ApJ, 856, 85, doi: [`10.3847/1538-4357/aaae08`](http://doi.org/10.3847/1538-4357/aaae08)

(ref: Schwarz2021) Schwarz, K. R., Calahan, J. K., Zhang, K., et al. 2021, ApJS, 257, 20, doi: [`10.3847/1538-4365/ac143b`](http://doi.org/10.3847/1538-4365/ac143b)

(ref: Seifert2021) Seifert, R. A., Cleeves, L. I., Adams, F. C., & Li, Z.-Y. 2021, ApJ, 912, 136, doi: [`10.3847/1538-4357/abf09a`](http://doi.org/10.3847/1538-4357/abf09a)

(ref: Sierra2021) Sierra, A., Pérez, L. M., Zhang, K., et al. 2021, ApJS, 257, 14, doi: [`10.3847/1538-4365/ac1431`](http://doi.org/10.3847/1538-4365/ac1431)

(ref: Stadler2025exoALMA) Stadler, J., Benisty, M., & Winter, A. J. , in press, ApJL, TBD

(ref: Stapper2024) Stapper, L. M., Hogerheijde, M. R., van Dishoeck, E. F., et al. 2024, A&A, 682, A149, doi: [`10.1051/0004-6361/202347271`](http://doi.org/10.1051/0004-6361/202347271)

(ref: Sturm2023) Sturm, J. A., Booth, A. S., McClure, M. K., Leemker, M., & van Dishoeck, E. F. 2023, A&A, 670, A12, doi: [`10.1051/0004-6361/202244227`](http://doi.org/10.1051/0004-6361/202244227)

(ref: Tazzari2021a) Tazzari, M., Testi, L., Natta, A., et al. 2021, MNRAS, 506, 5117, doi: [`10.1093/mnras/stab1912`](http://doi.org/10.1093/mnras/stab1912)

(ref: teague2020) Teague, R. 2020, richteague/keplerian_mask: Initial Release, 1.0, Zenodo, doi: [`10.5281/zenodo.4321137`](http://doi.org/10.5281/zenodo.4321137)

(ref: Teague2025exoALMA) Teague, R., Benisty, M., Facchini, S., Fukagawa, M., & Pinte, C. , in press, ApJL

(ref: Thi2001) Thi, W. F., van Dishoeck, E. F., Blake, G. A., et al. 2001, ApJ, 561, 1074, doi: [`10.1086/323361`](http://doi.org/10.1086/323361)

(ref: Trapman2017) Trapman, L., Miotello, A., Kama, M., van Dishoeck, E. F., & Bruderer, S. 2017, A&A, 605, A69, doi: [`10.1051/0004-6361/201630308`](http://doi.org/10.1051/0004-6361/201630308)

(ref: Trapman2022) Trapman, L., Tabone, B., Rosotti, G., & Zhang, K. 2022a, ApJ, 926, 61, doi: [`10.3847/1538-4357/ac3ed5`](http://doi.org/10.3847/1538-4357/ac3ed5)

(ref: Trapman2022b) Trapman, L., Zhang, K., van’t Hoff, M. L. R., Hogerheijde, M. R., & Bergin, E. A. 2022b, ApJL, 926, L2, doi: [`10.3847/2041-8213/ac4f47`](http://doi.org/10.3847/2041-8213/ac4f47)

(ref: AGEPRO_V_gas_masses) Trapman, L., Zhang, K., Rosotti, G., et al. , in press, AAS

(ref: Tripathi2017) Tripathi, A., Andrews, S. M., Birnstiel, T., & Wilner, D. J. 2017, ApJ, 845, 44, doi: [`10.3847/1538-4357/aa7c62`](http://doi.org/10.3847/1538-4357/aa7c62)

(ref: vanClepper2022) Van Clepper, E., Bergner, J. B., Bosman, A. D., Bergin, E., & Ciesla, F. J. 2022, ApJ, 927, 206, doi: [`10.3847/1538-4357/ac511b`](http://doi.org/10.3847/1538-4357/ac511b)

(ref: vdMarel2015) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2016, A&A, 585, A58, doi: [`10.1051/0004-6361/201526988`](http://doi.org/10.1051/0004-6361/201526988)

(ref: vtHoff2018) van ’t Hoff, M. L. R., Tobin, J. J., Harsono, D., & van Dishoeck, E. F. 2018, A&A, 615, A83, doi: [`10.1051/0004-6361/201732313`](http://doi.org/10.1051/0004-6361/201732313)

(ref: vantHoff2017) van ’t Hoff, M. L. R., Walsh, C., Kama, M., Facchini, S., & van Dishoeck, E. F. 2017, A&A, 599, A101, doi: [`10.1051/0004-6361/201629452`](http://doi.org/10.1051/0004-6361/201629452)

(ref: vtHoff2020) van’t Hoff, M. L. R., Harsono, D., Tobin, J. J., et al. 2020, ApJ, 901, 166, doi: [`10.3847/1538-4357/abb1a2`](http://doi.org/10.3847/1538-4357/abb1a2)

(ref: Veronesi2024) Veronesi, B., Longarini, C., Lodato, G., et al. 2024, A&A, 688, A136, doi: [`10.1051/0004-6361/202348237`](http://doi.org/10.1051/0004-6361/202348237)

(ref: Veronesi2021) Veronesi, B., Paneque-Carreño, T., Lodato, G., et al. 2021, ApJL, 914, L27, doi: [`10.3847/2041-8213/abfe6a`](http://doi.org/10.3847/2041-8213/abfe6a)

(ref: Visser2009) Visser, R., van Dishoeck, E. F., & Black, J. H. 2009, A&A, 503, 323, doi: [`10.1051/0004-6361/200912129`](http://doi.org/10.1051/0004-6361/200912129)

(ref: Whitney2013) Whitney, B. A., Robitaille, T. P., Bjorkman, J. E., et al. 2013, ApJS, 207, 30, doi: [`10.1088/0067-0049/207/2/30`](http://doi.org/10.1088/0067-0049/207/2/30)

(ref: Williams2005) Williams, J. P., Andrews, S. M., & Wilner, D. J. 2005, ApJ, 634, 495, doi: [`10.1086/444493`](http://doi.org/10.1086/444493)

(ref: WilliamsBest2014) Williams, J. P., & Best, W. M. J. 2014, ApJ, 788, 59, doi: [`10.1088/0004-637X/788/1/59`](http://doi.org/10.1088/0004-637X/788/1/59)

(ref: Yu2017) Yu, M., Evans, Neal J., I., Dodson-Robinson, S. E., Willacy, K., & Turner, N. J. 2017, ApJ, 841, 39, doi: [`10.3847/1538-4357/aa6e4c`](http://doi.org/10.3847/1538-4357/aa6e4c)

(ref: Yu2016) Yu, M., Willacy, K., Dodson-Robinson, S. E., Turner, N. J., & Evans, Neal J., I. 2016, ApJ, 822, 53, doi: [`10.3847/0004-637X/822/1/53`](http://doi.org/10.3847/0004-637X/822/1/53)

(ref: Zhang2021MAPS) Zhang, K., Booth, A. S., Law, C. J., et al. 2021, ApJS, 257, 5, doi: [`10.3847/1538-4365/ac1580`](http://doi.org/10.3847/1538-4365/ac1580)

(ref: AGEPRO_I_overview) Zhang, K., Pérez, L., Pascucci, I., et al. , subm., AAS

# Observational details

+:---------------+:-------------:+:--------:+:---------:+:--------------:+:-------------------:+:----------------:+:---------------:+
|                | ALMA Band 7 - N$_2$H$^+$                                                                                         |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| Name           | Date          | Antennas | Baselines | Time on source | Bandpass Calibrator | Phase Calibrator | Flux Calibrator |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                |               |          | \[m\]     | \[min\]        |                     |                  |                 |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| RXJ1615.3-3255 | 2 April 2024  | 42       | 15-251    | 8              | J1924-2914          | J1626-2951       | J1924-2914      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 1 July 2024   | 41       | 15-1261   | 22             | J1427-4206          | J1427-4206       | J1626-2951      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 1 July 2024   | 36       | 15-649    | 23             | J1427-4206          | J1610-3958       | J1427-4206      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| RXJ1852.3-3700 | 1 April 2024  | 41       | 15-280    | 8              | J1924-2914          | J1839-3453       | J1924-2914      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 28 May 2024   | 42       | 15-984    | 23             | J1924-2914          | J1802-3940       | J1924-2914      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| RXJ1842.9-3532 | 1 April 2024  | 41       | 15-280    | 8              | J1924-2914          | J1839-3453       | J1924-2914      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 28 May 2024   | 42       | 15-984    | 23             | J1924-2914          | J1802-3940       | J1924-2914      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| AA Tau         | 27 July 2024  | 46       | 14-499    | 9              | J0423-0120          | J0438+3004       | J0423-0120      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 8 Sep 2024    | 43       | 15-1604   | 25             | J0423-0120          | J0438+3004       | J0423-0120      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| PDS 66         | 21 March 2024 | 45       | 15-313    | 9              | J1427-4206          | J1147-6753       | J1427-4206      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 29 May 2024   | 41       | 15-984    | 25             | J1427-4206          | J1147-6753       | J1427-4206      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| HD 143006      | 12 April 2024 | 44       | 15-314    | 8              | J1924-2914          | J1625-2527       | J1924-2914      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 4 Jun 2024    | 40       | 15-1397   | 22             | J1924-2914          | J1551-1755       | J1924-2914      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| HD 135344B     | 12 April 2024 | 44       | 15-313    | 8              | J1924-2914          | J1457-3539       | J1924-2914      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 28 May 2024   | 41       | 15-984    | 23             | J1256-0547          | J1457-3539       | J1256-0547      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| CQ Tau         | 31 July 2024  | 45       | 14-483    | 9              | J0423-0120          | J0521+1638       | J0423-0120      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 22 Sep 2024   | 43       | 15-1397   | 25             | J0423-0120          | J0521+1638       | J0423-0120      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| HD 34282       | 1 Aug 2024    | 46       | 14-313    | 23             | J0423-0120          | J0501-0159       | J0423-0120      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 1 Nov 2024    | 46       | 14-313    | 8              | J0423-0120          | J0501-0159       | J0423-0120      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| MWC 758        | 31 July 2024  | 45       | 14-483    | 9              | J0423-0120          | J0521+1638       | J0423-0120      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 22 Sep 2024   | 43       | 15-1397   | 25             | J0423-0120          | J0521+1638       | J0423-0120      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| Elias 2-27     | 6 Oct 2022    | 10       | 8-48      | 19             | J1427-4206          | J1625-2527       | J1427-4206      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 7 Oct 2022    | 10       | 8-48      | 34             | J1427-4206          | J1625-2527       | J1427-4206      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 9 Oct 2022    | 10       | 8-48      | 34             | J1427-4206          | J1625-2527       | J1427-4206      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 9 Jan 2023    | 40       | 15-740    | 28             | J1427-4206          | J1700-2610       | J1427-4206      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                                                                                                                                   |
+----------------+------------------------------------------------------------------------------------------------------------------+
|                | ALMA Band 6 - C$^{18}$O                                                                                          |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| Name           | Date          | Antennas | Baselines | Time on source | Bandpass Cal.       | Phase Cal.       | Flux Cal.       |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                |               |          | \[m\]     | \[min\]        |                     |                  |                 |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
| RXJ1842.9-3532 | 21 Dec 2023   | 46       | 15-1397   | 32             | J1924-2914          | J1826-3650       | J1924-2914      |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+
|                | 25 March 2024 | 48       | 15-314    | 9              | J1924-2914          | J1826-3650       | J1924-291       |
+----------------+---------------+----------+-----------+----------------+---------------------+------------------+-----------------+

**Notes:**

+:------------------------+:----------------:+:------------------:+:-----------------:+:-----------------:+:------------------------------:+:-------------:+
| source                  | Disk-integrated fluxes (mJy \[km s$^{-1}$\])                                  | Program IDs                    | refs          |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
|                         | 285 GHz cont.    | $^{13}$CO (2-1)    | C$^{18}$O (2-1)   | N$_2$H$^+$ (3-2)  |                                |               |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| DM Tau                  | $99.1 \pm 1.4$   | $5341.7 \pm 34.3$  | $1275.6 \pm 21.8$ | $1437.6 \pm 39.2$ | 2016.1.00724.S, 2015.1.00678.S | \[3,2,2,3\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| V4046 Sgr               | $576.0 \pm 12.0$ | $8275.7 \pm 44.3$  | $1936.0 \pm 38.5$ | $3736.1 \pm 31.6$ | 2016.1.00724.S, 2015.1.00678.S | \[3,2,2,3\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| RXJ1852.3-3700          | $93.0 \pm 0.6$   | $1587.5 \pm 37.7$  | $504.4 \pm 22.1$  | $541.0 \pm 17.1$  | 2018.1.00689.S, 2023.1.00334.S | \[1,1,1,1\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| RXJ1842.9$\dagger$      | $87.6 \pm 0.5$   | \-                 | $238 \pm 4$       | $359.4 \pm 7.9$   | 2023.1.00334.S, 2021.1.01123.L | \[1,4,1,1\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| LkCa 15                 | $281.0 \pm 6.9$  | $6074.2 \pm 16.1$  | $1198.1 \pm 15.6$ | $1869.0 \pm 33.5$ | 2018.1.00945.S, 2015.1.00678.S | \[3,5,5,3\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| PDS 66                  | $162.2 \pm 8.0$  | $790.0 \pm 50.0$   | $210.0 \pm 20.0$  | $1000.7 \pm 14.5$ | 2017.1.01419.S, 2023.1.00334.S | \[1,7,7,1\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| CQ Tau                  | $207.5 \pm 1.9$  | $1120.0 \pm 40.0$  | $600.0 \pm 20.0$  | $19.9 \pm 5.88$   | 2017.1.01404.S, 2023.1.00334.S | \[1,8,8,1\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| HD 34282                | $205.2 \pm 6.9$  | $3460.0 \pm 50.0$  | $1890.0 \pm 40.0$ | $288.2 \pm 9.2$   | 2017.1.01404.S, 2023.1.00334.S | \[1,8,8,1\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| MWC 758                 | $101.3 \pm 0.4$  | $1870.0 \pm 70.0$  | $780.0 \pm 40.0$  | $71.8 \pm 6.3$    | 2017.1.00940.S, 2023.1.00334.S | \[1,8,8,1\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| GM Aur                  | $286.4 \pm 2.6$  | $5028.0 \pm 48.0$  | $1092.0 \pm 39.0$ | $1484.0 \pm 14.6$ | 2018.1.01055.L, 2015.1.00678.S | \[3,9,9,3\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| AS 209                  | $289.0 \pm 4.5$  | $2269.0 \pm 38.0$  | $538.0 \pm 27.0$  | $884.5 \pm 14.3$  | 2018.1.01055.L, 2015.1.00678.S | \[3,9,9,3\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| IM Lup                  | $243.7 \pm 6.2$  | $8370.0 \pm 83.0$  | $1592.0 \pm 60.0$ | $2040.0 \pm 49.0$ | 2018.1.01055.L, 2015.1.00678.S | \[3,9,9,3\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| MWC 480                 | $490.0 \pm 49.0$ | $8361.0 \pm 57.0$  | $3017.0 \pm 41.0$ | $228.0 \pm 13.0$  | 2018.1.01055.L, 2015.1.00657.S | \[3,9,9,10\]  |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| HD 163296               | $791.6 \pm 1.6$  | $15885.0 \pm 80.0$ | $5783.0 \pm 51.0$ | $556.1 \pm 49.1$  | 2018.1.01055.L, 2012.1.00681.S | \[3,9,9,11\]  |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
|                         | 285 GHz cont.    | $^{13}$CO (3-2)    | C$^{18}$O (3-2)   | N$_2$H$^+$ (3-2)  |                                |               |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| RXJ1615.3-3255          | $245.9 \pm 0.4$  | $11504.0 \pm 41.8$ | $3226.8 \pm 48.2$ | $563.6 \pm 6.2$   | 2012.1.00870.S, 2023.1.00334.S | \[1,1,1,1\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| RXJ1842.9-3532$\dagger$ | \-               | $2831.2 \pm 10.3$  | \-                |                   | 2023.1.00334.S, 2021.1.01123.L | \[1,4,1,1\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| AA Tau                  | $112.0 \pm 0.5$  | $5102.0 \pm 42.0$  | $1217.5 \pm 53.4$ | $686.6 \pm 10.8$  | 2015.1.01017.S, 2023.1.00334.S | \[1,7,7,1\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| HD 143006               | $102.0 \pm 0.4$  | $1668.0 \pm 7.6$   | $483.3\pm 10.1$   | $330.9 \pm 8.8$   | 2019.1.01683.S, 2023.1.00334.S | \[1,1,1,1\]   |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| HD 135344B              | $302.8 \pm 0.6$  | $7482.5 \pm 39.1$  | $3115.4 \pm 46.1$ | $40.3 \pm 5.8$    | 2012.1.00158.S, 2023.1.00334.S | \[1,12,12,1\] |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+
| Elias 2-27              | $467.6 \pm 0.5$  | $22260.0 \pm 90.0$ | $4450.0 \pm 60.0$ | $447 \pm 6.5$     | 2016.1.00724.S, 2022.1.00485.S | \[1,13,13,1\] |
+-------------------------+------------------+--------------------+-------------------+-------------------+--------------------------------+---------------+

**Notes:** $^{\dagger}$: For RXJ1842.9 the two CO isotopologue lines are $^{13}\mathrm{CO}$ (3-2) from (cite: GallowaySprietsma2025exoALMA) and $\mathrm{C}^{18}\mathrm{O}$ (2-1) from this work. Flux uncertainties do no include absolute flux uncertainties. References are given for each individual line. \[1\]: *This work*, \[2\]: (cite: Flaherty2020), \[3\]: (cite: Qi2019),

\[4\]: (cite: GallowaySprietsma2025exoALMA), \[5\]: (cite: Sturm2023), \[6\]: (cite: Loomis2017), \[7\]: (cite: Ribas2023), \[8\]: (cite: Stapper2024), \[9\]: (cite: Oberg2021MAPS), \[10\]: (cite: Loomis2020), \[11\]: (cite: Qi2015), \[12\]: (cite: vdMarel2015),

\[13\]: (cite: Paneque-Carreno2023)

[^1]: as implemented in <https://zenodo.org/records/14973489>

[^2]: The fluxes for these models and the ones presented in Section [5.2](#sec: effect inner cavity) and [5.4](#sec: n2hp for herbigs) are available at Zenodo DOI: <https://zenodo.org/records/15148628>

[^3]: http://www.astropy.org

</paper>

Write the methods card for this paper.