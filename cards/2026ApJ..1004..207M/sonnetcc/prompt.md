# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026ApJ..1004..207M\sonnetcc\reply.txt

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
 "bibcode": "2026ApJ..1004..207M",
 "title": "Global and Local Infall in the ASHES Sample (GLASHES). II. Asymmetric Line Profiles Around Dense Cores in 70 μm Dark Massive Clumps",
 "year": 2026,
 "journal": "The Astrophysical Journal",
 "first_author": "Morii, Kaho",
 "n_authors": 4,
 "arxiv_id": "2605.12595",
 "doi": "10.3847/1538-4357/ae6db8",
 "alma_projects_linked_by_archive": [
  "2018.1.00299.S",
  "2023.1.01150.S",
  "2024.1.01505.S"
 ]
}
```

Paper text:
<paper>
# Global and Local Infall in the ASHES Sample (GLASHES). II. Asymmetric Line Profiles around Dense Cores in 70 μm Dark Massive Clumps

## Abstract

Gravitational collapse is fundamental to star formation, yet direct kinematic evidence of infall at the core scale in high-mass star-forming regions remains poorly constrained. We present the first large-scale statistical study of infall signatures in 304 dense cores within 24 massive 70 $\mu$m-dark clumps from the GLASHES (Global and Local Infall in the ASHES Sample) survey. Using ALMA Band 6 observations of the optically thick tracers HCO$^{+}$ and HNC ($J$=3–2), we systematically characterize blue asymmetry line profiles indicative of infalling motions. We employ two complementary metrics, the velocity difference parameter ($\delta_v$) and the asymmetry parameter ($A$), to quantify infall signatures, finding consistent results across both tracers. Blue asymmetry profiles are detected in $\sim$50-60% of cores ($\delta_v<$0 or $A>$0).

Spectral classification reveals that $\sim$60% of cores exhibit double-peaked profiles, and 34% and 39% show blue asymmetry profiles in HCO$^{+}$ and HNC, respectively, with the percentage increasing with core mass and surface density. Accounting for geometric effects that can obscure infall signatures, our results suggest that gravitational collapse is prevalent in and around the cores. Importantly, infall signatures are detected from the prestellar stage and become more dominant as cores’ evolution proceeds. Even cores with virial parameters $\alpha_{vir} > 2$ show infall signatures, suggesting that external compression may trigger collapse in addition to self-gravity or that linewidth may include inward motion in addition to turbulence. Furthermore, a moderate correlation between clump-scale and core-scale asymmetry supports a hierarchical collapse scenario, implying a dynamic and multi-scale process of high-mass star formation.

show\]kaho.morii@cfa.harvard.edu

# Introduction

Gravitational collapse is the fundamental process driving the formation of stars. As comprehensively reviewed by (cite: Evans99) and (cite: Evans03), identifying the kinematic signatures of this collapse is crucial for understanding the earliest stages of star formation. Specifically, the “blue asymmetry” profile, a line profile with brighter emission on the blue side, observed in optically thick molecular lines toward central dense regions, provides direct spectroscopic evidence of infalling gas motions (cite: Jackson19). Such a profile is produced when the excitation temperature increases toward the center of the structure (e.g., cloud, clumps, or cores). This signature has been observed for about five decades across a wide range of environments, including molecular clouds (cite: LeungBrown77; Myers96), dense cores in nearby low-mass star-forming regions (cite: Zhou93; Tafalla98; LeeMyers11; Campbell16), dense cores in high-mass star-forming regions (cite: Csengeri11; Contreras18; Morii25; Gupta26), high-mass protostellar cores (cite: HoHaschick86; KetoHoHaschick88; ZhangHoOhashi98; FullerWilliamsSridharan05), massive clumps (cite: Sanhueza10; Schneider10; Reiter11; Rygl13; He16; Wyrowski16; Traficante17; Jackson19; Yang21; Xu23_hcn; Jackson26), and (UC)H$\textsc{II}$ regions (cite: ZhangHo97). However, while infall has been well characterized at the core scale ($\sim$0.01–0.1 pc) in nearby low-mass star-forming regions, direct kinematic evidence at the same scale in high-mass star-forming regions remains limited to some case studies.

Understanding infall in high-mass star formation is of particular importance in the context of current theoretical frameworks. Models such as the “clump-fed” accretion scenario (cite: Bonnell04; Wang10; Padoan20) including the Global Hierarchical Collapse (GHC) model (cite: vazquez19) predict that gas inflow or infall is continuous from the parent molecular cloud down to individual cores, implying that core-scale infall is a direct result of large-scale dynamical accretion. Characterizing infall at the core scale is therefore essential to validate these scenarios and to understand how high-mass stars accumulate sufficient mass. However, observational verification at the core scale in high-mass star-forming regions presents significant challenges due to their typically large distances ($\gtrsim 3$ kpc) and highly clustered environments, and previous studies have largely been limited to coarse spatial resolutions at the clump scale ($\sim$1 pc), or to a handful of particularly bright massive protostars and (UC)HII regions.

At the clump scale, large surveys such as MALT90 (cite: Foster11; Jackson13) have successfully identified global infall motions (cite: Jackson19), and suggest that infall is particularly active in earlier evolutionary stages, including infrared dark clouds (cite: Menten05; Sridharan05; Rathborne06; Chambers09; Sanhueza12; Sanhueza13; Sanhueza17; Morii21). Although some interferometric studies have inferred gas inflow from velocity gradients in IRDCs (cite: Csengeri11; Beuther13; Henshaw14; Lu18; Chen19; Sanhueza21; Redaelli22; Sanhueza25), direct kinematic evidence of gravitational collapse via blue asymmetry at the core scale has been reported in only a few individual case studies (cite: Csengeri11; Contreras18; Morii25). A comprehensive statistical understanding of core-scale infall in the earliest stages of high-mass star formation therefore remains lacking.

To address this observational gap, the “Global and Local Infall in the ASHES Sample” (GLASHES) survey targets 70 μm dark massive clumps identified in the ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES; (cite: Sanhueza19; Morii23)), which represent ideal laboratories for studying the initial conditions of high-mass star formation (cite: Li20; Tafoya21; Sakai21; Li22; Sabatini22; Li23; Izumi24; Morii24; Lin25; Morii26). In our pilot study in one of the ASHES targets, G337.54, hosting 17 cores (cite: Morii25), we established a robust methodology to extract core-scale infall signatures, derived infall velocities, and confirmed that they are higher than those found in nearby low-mass star-forming regions. Following it, this study extends the analysis to 24 massive clumps containing 304 dense cores to provide the first large-scale statistical evidence of gravitational collapse in the earliest stages of high-mass star formation. The primary goal of this paper is to report the detection rates of blue asymmetry across a large sample and to rigorously evaluate the classification criteria using multiple metrics. We also investigate how the frequency of these signatures relates to core properties and the surrounding clump environment. Detailed radiative transfer modeling to derive quantitative infall rates and other physical parameters will be presented in a subsequent paper. We describe the observational setup in Section [2](#sec:obs), present the line emission results and methods for profile characterization and spectral classification in Section [3](#sec:results), discuss the detection rates and correlations with core and clump properties in Section [4](#sec:discussion), and summarize our findings in Section [5](#sec:conclusion).

# Observations and Data Reduction

The GLASHES project consists of data from Band 3 and 6 taken with the main 12-m array, and the Atacama Compact Array (ACA), including both the 7-m array and Total Power (TP) array. The observations have been done during Cycles 6 (2018.1.00299.S, PI: Y. Contreras), 10 (2023.1.01150.S, PI: K. Morii), and 11 (2024.1.01505.S, PI: K. Morii). Targets are 24 massive clumps selected from the ASHES sample, which contains at least one sub-virial ($\alpha_{\rm vir}<2$), intermediate-mass cores ($M>4\,M_\odot$). The correlator setup covered HCO$^{+}$ ($J=3-2$, $\nu$=267.557633 GHz), HNC ($J=3-2$, $\nu$=271.981111 GHz) and HC$^{18}$O$^+$ ($J=3-2$), $\nu$=255.479 GHz in Band 6 and N$_2$H$^+$ ($J=1-0$, $\nu$=93.173763 GHz) in Band 3. In this paper, we mainly use Band 6 data.

N$_2$H$^+$ data was used only for determining the systemic velocity (see Appendix [6](#sec:Vsys)).

The ALMA 12 m array consisted of 41–47 antennas, with a baseline ranging from 15 to 313 m and 779 m for Band 6 and Band 3, respectively.

The total on-source time was $\sim$7–20 minutes. These observations are sensitive to angular scales smaller than $\sim$10$''$ and $\sim$15$''$ for Band 6 and Band 3, respectively. More extended emission was recovered by including ACA data. The 7 m array observations consisted of 8–11 antennas, with baselines ranging from 5 to 48 m.

The total on-source time was $\sim$50–97 minutes for Band 6 and $\sim$29–58 minutes for Band 3. These observations are sensitive to angular scales smaller than $\sim$25$''$ and $\sim$72$''$ for Band 6 and Band 3, respectively. We also obtained total power data to cover the zero-baseline information. The total power array consisted of three antennas, and the total on-source time was $\sim$300 minutes and $\sim$250 minutes for Band 6 and Band 3, respectively. All observations have been done in single-pointing. Such observation setup (observation dates, baseline, number of antennas, and total on-source time) is summarized in Table [1](#tab:obs_set).

+:-------+:------------------:+:-------------------------:+:-----------:+:-----:+:-----:+:--+
| Band   | Config.            | Obs. Dates                |             |       |       |   |
+--------+--------------------+---------------------------+-------------+-------+-------+---+
| \(m\)  | $N_{\rm ant}$      |                           |             |       |       |   |
+--------+--------------------+---------------------------+-------------+-------+-------+---+
| (min)  |                    |                           |             |       |       |   |
+--------+--------------------+---------------------------+-------------+-------+-------+---+
| Band 6 | 12m (C43-1, C43-2) | 2024 Mar. 17–2024 Dec. 10 | 15.1–313.7  | 43–47 | 7–15  |   |
|        +--------------------+---------------------------+-------------+-------+-------+---+
|        | 7m                 | 2024 Jan. 21–2024 Jun. 13 | 8.9–48.9    | 8–11  | 50–97 |   |
+--------+--------------------+---------------------------+-------------+-------+-------+---+
|        | 12m (C43-3, C43-4) | 2024 Jan. 15–2025 Jan. 25 | 15.1–783.5  | 35–46 | 13–22 |   |
+--------+--------------------+---------------------------+-------------+-------+-------+---+
|        | 7m                 | 2023 Oct. 25–2024 Jan. 26 | 8.9–48.9    | 7–10  | 29–58 |   |
+--------+--------------------+---------------------------+-------------+-------+-------+---+
|        |                    |                           |             |       |       |   |
+--------+--------------------+---------------------------+-------------+-------+-------+---+

: Summary of ALMA Observations

Table notes: $^{a}$ On-source integration time per region.

Data reduction was carried out using CASA software package versions 6.5.4.9 and 6.6.1.17 for calibration and 6.6.3-22 for imaging (cite: CASA22). After subtracting continuum emission, we combined the 12 m array data with the 7 m array data

and cleaned together. After that, we combined TP data with the interferometric images using the CASA task, feather. We used TCLEAN with Briggs’ robust weighting of 0.5 to the visibilities and an imaging option of MULTISCALE with scales of 0, 5, 15, 25, and 50 times the pixel size (0.2$''$), considering the spatially extended nature of the emission. We used the automasking algorithm, auto-multithresh (cite: Kepley19-automask), where the parameters of sidelobethreshold, noisethreshold, lownoisethreshold, negativethreshold, and minbeamfrac are set to 1.75, 2, 1.5, 0, and 0.3, respectively, mostly following the recommended values by (cite: Kepley19-automask).

The achieved beam size of HCO$^{+}$, HNC and HC$^{18}$O$^+$ cubes are (0.89–1.06) arcsec $\times$ (1.05–1.29) arcsec, whilst N$_2$H$^+$ cubes have beam size of (1.10–1.38) arcsec $\times$ (1.40–1.80) arcsec.

The velocity resolution of HNC, HCO$^+$ and HC$^{18}$O$^+$ is 0.27 km s$^{-1}$ and that of N$_2$H$^+$ is 0.19 km s$^{-1}$. Average 1$\sigma$ rms noise level measured from line-free channel is $\sim$7 and 5 mJy beam$^{-1}$, corresponding to 1.0 K and 0.3 K, for Band 6 and Band 3 cubes, respectively. All data shown in the paper about these three lines are ALMA 12 m, bf 7 m, and TP combined, and before the primary beam correction. Appendix [7](#sec:TP-combination) discusses how combining TP data with interferometric data affects the line shape.

Additionally, in this paper, we also use the 1.3 mm continuum emission and the optically thin tracers of DCO$^{+}$ ($J$=3–2), N$_2$D$^{+}$ ($J$=3–2), DCN ($J$=3–2) from the ASHES project (cite: Li22; Li23; Morii23; Morii24), see Appendix [6](#sec:Vsys). These are 12m+7m combined datasets without TP combination, but with a similar beam size of $\sim$1.2”. Core physical information such as size, mass, density, virial parameter, and evolutionary stages has been taken from (cite: Morii23) and (cite: Morii24).

# Results

## Spatial distribution

Figure [1](#fig:mom0_cont) shows the integrated intensity (zeroth-order moment) map of HNC, overlaid with 1.3 mm dust continuum. It indicates the consistency between bright spots of HNC and dust continuum emission, as well as a more extended distribution of HNC emission than dust continuum.

![](G023.47_mom0_hnc.pdf)

Figure [2](#fig:cont_profile) shows (a) line spectra map of HNC overlaid on a three color image (r/b/g: CO redshifted, CO blue shifted, and continuum), and (c) zoom-in spectral map of HNC (green), HCO$^+$ (blue) and DCO$^+$ (orange) around the brightest core. It indicates that double peak profiles are seen widely spread in the field, not only around or inside dense cores but also in inter-core regions. Spectra that overlap with CO outflows sometimes have high-velocity or tail/wing components. Panel (b) shows the comparison of the spectra. HNC and HCO$^+$ show double peak profiles around the most massive core, where DCO$^{+}$ typically peaks at their dip velocity. The profiles of HNC and HCO$^+$ look generally the same, but sometimes differ in intensity and peak velocity, for example the profile at RA=18h33m39.40s and Decl.=–8d21m16s.

![](G023.47_spectrum.pdf)

## Line Detection

Line profiles of HCO$^{+}$ and HNC toward the 304 identified cores were extracted by averaging within the cores. This was done by creating an ellipse mask from the major and minor axes and position angle information obtained from dendrogram analysis applied to continuum emission (cite: Morii23). HCO$^+$ emission was detected in 282 cores, and HNC in 285 cores, at the $>5\sigma$ noise level. The detected profiles exhibit a variety of morphologies, including single peaks, skewed profiles, and double peaks with either the blue or red peak stronger. High-velocity line wings and tails indicative of outflows were also observed in a subset of cores, especially in HCO$^{+}$. Figure [13](#fig:class_profile) in Appendix [8](#sec:profile-classification) presents several examples of the extracted profiles.

Using the HC$^{18}$O$^+$ ($J=3-2$) as an optically thin reference, we estimated the peak optical depth of HCO$^+$ ($J=3-2$) for 30 cores in three representative regions (see Appendix [9](#sec:opticaldepth) for details). For cores where HC$^{18}$O$^+$ is detected, the derived optical depths ($\tau = 1.7-11.4$).

These values serve as lower limits due to the uncertainties in excitation temperature, thereby confirming that the optically thick assumption is valid for these sources. For cores without HC$^{18}$O$^+$ detection, predominantly low-mass prestellar cores, only upper limits could be obtained. However, none of these upper limits indicate clearly optically thin conditions. Therefore, in the following analysis, we treat both HCO$^{+}$ and HNC as optically thick tracers.

## Infall Statistics

Blue asymmetry profiles sometimes refer to both blue skew profiles and double peak profiles with the blue peak stronger (or blue double peak profile). To avoid contamination from the multi-velocity components in a line of sight, the blue asymmetry profile is confirmed with an optically thin line. If the optically thick line shows a double peak profile with a dip close to the systemic velocity, where an optically thin line shows a single peak, the profile is considered to be an indicator of inward or outward motion. If the blue-shifted component is brighter, it implies inward motion. A profile without a clear dip but with a blue skew, indicating that the peak is shifted to the blue side relative to the systemic velocity, is defined as a blue-skew profile. After determining the systemic velocity for all the cores (see Appendix [6](#sec:Vsys)), we employed two methods to quantitatively characterize blue asymmetry profiles:

1.  Velocity Difference by (cite: Mardones97): $$\begin{equation}
            \delta_v \equiv \frac{V_{\rm thick} - V_{\rm thin}}{\Delta V_{\rm thin}}
            \label{equ:delta_v}
        
    \end{equation}$$ Here $V_{\rm thick}$ is the brightest peak velocity of the optically thick line, $V_{\rm thin}$ is the peak velocity of the optically thin line tracing the systemic velocity of the dense core, and $\Delta V_{\rm thin}$ is the full width at half maximum (FWHM) of the optically thin line. The blue asymmetries correspond to $\delta_v<0$. Restrictively, $\delta_v<-0.25$ is considered to be a significant blue asymmetric profile.

2.  Asymmetry Parameter by (cite: Jackson19): $$\begin{equation}
           A \equiv \frac{I_{\rm blue} - I_{\rm red}}{I_{\rm blue} + I_{\rm red}},
           \label{equ:A}
        
    \end{equation}$$ where $I_{\rm blue}$ is the integrated intensity at velocities less than the reference velocity and $I_{\rm red}$ is the integrated intensity at more positive velocities. The integration range for $I_{\rm blue}$ extended from $V_{\rm thin} - 2\Delta V_{\rm thin}$ to $V_{\rm thin}$ and that for $I_{\rm red}$ was from $V_{\rm thin}$ to $V_{\rm thin} + 2\Delta V_{\rm thin}$, where $V_{\rm thin}$ is the reference line velocity and $\Delta V_{\rm thin}$ is the observed velocity FWHM of optically thin line. $A$ represents the fraction of the total line flux that lies to the blueshifted (or redshifted) side of the systemic velocity. In this scheme, line profiles with a blue asymmetry will have values of $A>0$, symmetric line profiles will have $A=0$, and line profiles with a red asymmetry will have $A<0$. Larger absolute values of $A$ are more asymmetric line profile. In the absence of absorption against a continuum source, $A$ is bounded between -1 and +1.

Applying these methods to both HCO$^{+}$ and HNC, we found almost consistent results across the two metrics and also across the lines. Figure [3](#fig:A_delta_scatterplot) shows the $\delta_v$ and $A$ scatter plots derived for both HCO$^{+}$ (blue) and HNC (green). Cores with a large uncertainty ($>$100%) are colored in gray. The uncertainties for both parameters are estimated following (cite: Jackson19). The majority of the sample lies along the line from the top-left to the bottom-right, implying consistent classification from the $\delta_v$ and $A$ parameters. Quantitatively, in terms of $\delta_v$, 50.3% and 58.0% of cores have $\delta_v <$0, corresponding to inward motion, in HCO$^+$ and HNC, respectively. More restrictively, $\delta_v <$-0.25 are found in 40% and 45% of the whole sample. In terms of $A$, 48.3% and 53.7% of cores show $A>0$ in HCO$^+$ and HNC, respectively. Some cores show $|A|>1$ due to absorption in the profile. Compared to HCO$^+$, a higher percentage of inward-indicating results is obtained from HNC lines. This is clearly seen in the histogram of $\delta_v$, whose peak is located $<-0.25$. However, the fraction of blue asymmetry profiles is still not significantly higher than that of red asymmetry.

![](delta_A_joint_2lines.pdf)

## Line Profile

Beyond the quantitative asymmetry measures, we further characterize the profile by its shape. As discussed in Appendix [7](#sec:TP-combination), ignoring TP data may cause significantly different results in such analysis. We measured the peak velocity and performed one- or two-Gaussian fits, and using the velocity dispersion ($\sigma$) and peak velocity separation ($\Delta V = |v_{\rm gauss, 1} - v_{\rm gauss, 2}|$), we classified spectrum into single, skew, double peak, or complex classes as summarized in Figure [4](#fig:class-fig). The detailed steps are described in Appendix [8](#sec:profile-classification).

![](class-tree.pdf)

As a result, $\sim$60% of the sample is classified as double peak profiles by both HCO$^+$ and HNC, which can be roughly described by two Gaussians. 15% show a skew profile without a clear dip or profile described by a closely located two Gaussians, 10% show a single peak, and the other $\sim$15% show a complex profile. Some examples of the classification are shown in Figure [13](#fig:class_profile). Figure [14](#fig:class_corr) in the Appendix shows the correlation plot of line classification between HCO$^+$ and HNC, indicating the good correlation between the two lines, albeit with occasional discrepancies in classification. More detailed discussion of these classifications and cores’ physical properties is presented in Section [4.2](#sec:class-phy). All the measured parameters and classifications are listed in Table [\[tab:infall\]](#tab:infall).

lcccCcCCCCcc Region & ID & Evolutionary & Gravitational & $V_{\rm cen}$ & $\sigma_{\rm thin}$ & & &\
& & Stage$^{a}$ & Boundness$^{b}$ & (km s$^{-1}$) & (km s$^{-1}$) & HCO$^+$ & HNC & HCO$^+$ & HNC & HCO$^+$ & HNC\
G016.97 & 1 & outflow & bound & 41.34 & 0.36 & -0.90 & -0.57 & 0.41 & 0.40 & blue double peak & blue double peak\
G016.97 & 2 & warm & bound & 40.54 & 0.26 & 0.30 & 0.31 & 0.20 & 0.11 & red skew & red skew\
G016.97 & 3 & prestellar & bound & 40.67 & 0.31 & -0.31 & -0.30 & 0.16 & 0.02 & blue double peak & blue skew\
G016.97 & 4 & prestellar & non-detection & 40.41 & 0.34 & -0.30 & -0.28 & 0.41 & 0.21 & blue skew & blue skew\
G016.97 & 5 & outflow & non-detection & 41.32 & 0.40 & -1.08 & -1.64 & 0.62 & 0.46 & blue double peak & blue double peak\
G016.97 & 6 & prestellar & non-detection & 40.35 & 0.37 & -0.98 & -0.19 & 0.33 & 0.13 & complex & blue skew\
G016.97 & 8 & prestellar & non-detection & 40.47 & 0.29 & 2.18 & -0.42 & -0.04 & -0.07 & red double peak & blue double peak\
G016.97 & 9 & outflow & non-detection & 40.46 & 0.14 & -0.06 & -0.42 & 0.41 & 1.61 & single & single\
G016.97 & 10 & prestellar & non-detection & 40.52 & 0.37 & 0.22 & 0.54 & -0.01 & -0.31 & red skew & red skew\
G016.97 & 11 & prestellar & non-detection & 40.88 & 0.45 & 0.63 & -0.27 & -0.45 & -0.01 & red double peak & blue double peak

Table notes: $^{*}$ Full version is available online as machine-readable table. $^{a}$ Determined based on the detections of CO outflow and warm gas tracers in (cite: Li22) and (cite: Morii24). $^{b}$ Determined from the virial analysis considering gravity and non-thermal velocity dispersion excluding external pressure and magnetic field support (cite: Morii24).

How such classification correlates with $\delta_v$ and $A$ parameters can be confirmed in Figure [5](#fig:Adelta_class), where color represents the classification. Cores showing double peak profiles (dark orange and navy colors) have larger $|\delta_v|$ and $|A|$, while skew peak profiles (orange and blue) are found in cores showing smaller absolute values. Single profiles (green) are seen around 0 in both parameters. These results confirm that the quantitative asymmetry parameters and the morphological classification are in good agreement.

![](Adelta_class_2lines.pdf)

# Discussion

## Infall Statistics and Cores Properties

As they deviate from zero, both $A$ and $\delta_v$ indicate stronger inward/outward motion. Figure [6](#fig:Adelta_evol) shows the $\delta_v$ and $A$ scatter plots colored by cores’ evolutionary stages. The left and right panels show HCO$^+$ and HNC, respectively. The cores’ evolutionary stages are classified in (cite: Morii24). Cores associated with outflows (red diamonds) and with the detections of warm gas tracers (green crosses) are protostellar core candidates. Prestellar core candidates without any signs of protostars are plotted as blue squares.

The difference among the evolutionary stages in the $A$ parameter lies in its dispersion, with prestellar cores showing greater variation. The median value does not differ significantly among the three evolutionary stages, but $A$ estimated from HNC peaks at $A>0$. Similarly, the $\delta_v$ distributions for all evolutionary stages take a peak $\delta_v<$-0.25 in HNC, indicating the large population showing inward motion in HNC. In $\delta_v$, a bimodal distribution is seen in protostellar cores, although prestellar cores show relatively smaller $|\delta_v|$ values with a single peak. The median value or the peak of $\delta_v$ distribution shifts to smaller values as evolution, implying that inward motion is more clearly seen in the protostellar phase. Since protostellar cores are more massive and denser (cite: Morii26), there is a weak correlation indicating that more massive and denser cores show relatively smaller $\delta_v$ and larger $A$, which is discussed in Appendix [10](#sec:Adelta_phy).

![](Adelta_evol_2lines.pdf)

## Line Profile Classification and Core Properties

![](Phy_class_2lines.pdf)

Figure [7](#fig:Core_phy_class_boxplot) shows the core physical properties distribution ($M$, $\Sigma$, $\alpha_{vir}$) along with the spectral classification. The left and right columns show the case of HCO$^+$ and HNC, respectively. Overall, the features seen in these plots are independent of the lines. Single and red skew profiles are seen in cores with low-mass, low-density, and relatively high virial parameters. Blue skew, blue double-peak, and red double-peak profiles are found in relatively more massive and dense cores with a small virial parameter ($\lesssim$2). Complex profiles are also found in low- to high-mass cores.

Figure [8](#fig:class_binplot) shows the percentage of each profile by dividing the sample into several mass and surface density bins in the first two rows. It clearly shows that the percentage of single-peak profiles decreases, while the percentage of blue double-peak profiles generally increases as mass and density increase. Considering HCO$^{+}$ is more affected by outflows and focusing on the HNC plots, the blue asymmetry profile is the dominant category at the highest mass and density bin.

![](MSbin_Evol_Bound_2lines.pdf)

It should be noted that, considering the physics behind the double peak profile, it is natural to see a clearer double peak profile in denser and more massive objects, where there is likely a steeper density and temperature gradient. Single or skew profiles in low-mass, low-density cores imply that those conditions may not be sufficient to make 3-2 lines optically thick (see also Section[3.2](#sec:line_detection)). However, as mentioned in the previous search for suitable lines tracing infall by numerical simulation (cite: Chira14; Jin-Jin21), lower transitions would suffer more from the ambient gas around cores, raising the complexity to observe inward motion from low-mass, lower-density cores in massive clumps.

The line profile classification and the relation with cores’ evolutionary stage are summarized in the third row of Figure [8](#fig:class_binplot). Prestellar cores have the highest percentage of skew and single profiles. On the contrary, outflow-associated cores tend to show a double-peak profile (70% when combining blue and red cases), indicating a broader line width. This implies that the blue asymmetry profile emerges from the prestellar stage and becomes increasingly dominant as evolution proceeds.

Interestingly, we detected clear blue asymmetry profiles even in cores classified as gravitationally unbound (virial parameter $\alpha_{vir} > 2$). The bottom row of Figure [8](#fig:class_binplot) shows the percentage for each category. Although the percentage ($\sim$20%) is not as high as bound cores ($\sim$30-40%), this is also confirmed in the scatter plot (right column of Figure [3](#fig:A_delta_scatterplot)) where some unbound cores ($\alpha_{vir} \sim$2-4) show $A>0$ and $\delta<0$. This finding may challenge the simple interpretation of virial analysis, where external pressure is not considered. Or, as implied by (cite: Morii25), this may be due to the overestimation of the non-thermal velocity dispersion caused by the broadening produced by local infall motions. It suggests that these cores may be undergoing collapse driven by external pressure (e.g., from the surrounding clump weight or feedback), rather than purely by self-gravity, as expected in accretion-driven star formation (cite: Gomez21), or turbulent fragmentation (cite: Ishihara25).

Our statistical analysis reveals that blue asymmetry is detected in nearly 60% of the dense cores, excluding complex profiles. Numerical simulations by (cite: Smith12; Smith13) suggest that viewing angles, complex filamentary geometries, and large-scale gas flows can easily obscure infall signatures even in genuinely collapsing cores. The measured fraction is comparable to that reported by (cite: Chira14) for collapsing objects in simulations without feedback, implying that core-scale collapse is prevalent in 70 μm-dark clumps. The fact that blue asymmetry is not ubiquitous likely reflects the combined effects of unfavorable viewing geometry and outflow contamination, rather than an absence of infall.

## Hierarchical Inward Motion

Gravitational collapse occurs not only at the core-scale but also at the clump-scale. Using the total-power data, we measured $\delta_v$ and $A$ parameters at the clump-scale. The measured parameters are listed in Table [2](#tab:infall-clump). Figure [9](#fig:delta_A_cl) is the same plot as Figure [3](#fig:A_delta_scatterplot), but for clump-scale profiles. The overall trend, such as the correlation between two parameters, is similar; however, the parameter space is much smaller. For example $|\delta_v|<0.6$ for clumps, but $\lesssim$2 for cores. Compared to core-scale, clump-scale HCO$^+$ and HNC profiles are more likely to show a single peak, especially for HNC, resulting in small $\delta_v$ and $A$ variation. In clump-scale, HCO$^+$ rather shows blue-skew or double-peak profiles. This is consistent with (cite: Jackson26), who report that HNC and HCN tend to show smaller asymmetries than HCO$^{+}$ due to their lower optical depth. Even at core scales, HNC becomes optically thick closer to the core center than HCO$^{+}$ (cite: Chira14), so based on optical depth alone, HCO$^{+}$ would be expected to show a higher blue asymmetry fraction. The fact that the opposite trend is observed, though not significantly, is consistent with the earlier finding that HCO$^{+}$ profiles are more affected by outflows and diffuse gas flows, which can suppress or distort infall signatures.

![](delta_A_joint_2lines_cl.pdf)

+:--------+:----------------:+:---------------------:+:--------------------:+:----------:+:----------:+:------------:+:-----------------:+
| Region  | n(H$_2$)$^{a}$   | $f_{\rm proto}$$^{b}$ | $N_{\rm core}$$^{c}$ | $f_{\rm blue, all}$     | $A_{\rm cl}$ | $\delta_{\rm cl}$ |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
|         | 10$^4$ cm$^{-3}$ |                       |                      | HCO$^+$    | HNC        |              |                   |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G016.97 | 4.19             | 0.38                  | 12                   | 0.33       | 0.33       | 0.14         | -0.28             |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G018.80 | 4.09             | 0.75                  | 6                    | 0.17       | 0.17       | -0.07        | 0.37              |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G018.93 | 2.04             | 0.47                  | 5                    | 0.20       | 0.20       | -0.31        | 0.55              |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G022.69 | 1.75             | 0.42                  | 9                    | 0.11       | 0.11       | -0.25        | 0.07              |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G023.47 | 8.39             | 0.53                  | 12                   | 0.75       | 0.75       | -0.00        | -0.11             |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G024.01 | 11.52            | 0.62                  | 13                   | 0.46       | 0.46       | 0.17         | -0.62             |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G024.52 | 2.91             | 0.65                  | 18                   | 0.33       | 0.33       | 0.43         | -0.38             |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G025.16 | 3.74             | 0.56                  | 13                   | 0.46       | 0.46       | 0.15         | -0.48             |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G028.54 | 2.86             | 0.39                  | 16                   | 0.25       | 0.25       | 0.12         | 0.04              |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G028.56 | 8.36             | 0.71                  | 26                   | 0.23       | 0.23       | 0.03         | -0.03             |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G028.92 | 2.44             | 0.56                  | 7                    | 0.57       | 0.57       | 0.15         | 0.06              |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G030.70 | 1.73             | 0.52                  | 10                   | 0.60       | 0.60       | 0.03         | 0.08              |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G030.91 | 6.17             | 0.42                  | 10                   | 0.50       | 0.50       | 0.08         | 0.08              |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G033.33 | 1.21             | 0.33                  | 7                    | 0.29       | 0.29       | -0.35        | 0.37              |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G034.13 | 1.58             | 0.13                  | 10                   | 0.00       | 0.00       | 0.36         | -0.08             |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G034.73 | 4.48             | 0.58                  | 10                   | 0.00       | 0.00       | -0.01        | 0.29              |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G036.66 | 5.04             | 0.54                  | 9                    | 0.44       | 0.44       | 0.21         | -0.20             |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G305.79 | 9.30             | 0.47                  | 27                   | 0.41       | 0.41       | -0.06        | 0.10              |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G327.11 | 4.10             | 0.19                  | 11                   | 0.09       | 0.09       | -0.09        | 0.35              |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G332.96 | 1.94             | 0.10                  | 7                    | 0.14       | 0.14       | -0.07        | 0.32              |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G333.48 | 4.04             | 0.20                  | 18                   | 0.67       | 0.67       | -0.05        | -0.06             |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G333.52 | 10.93            | 0.71                  | 28                   | 0.43       | 0.43       | 0.36         | -0.33             |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G337.54 | 5.64             | 0.53                  | 11                   | 0.18       | 0.18       | -0.23        | -0.17             |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+
| G340.39 | 2.90             | 0.10                  | 9                    | 0.44       | 0.44       | 0.35         | -0.19             |
+---------+------------------+-----------------------+----------------------+------------+------------+--------------+-------------------+

: Summary of Clump Properties

Table notes: $^{a}$ Estimated in (cite: Morii23). $^{b}$ Fraction of the protostellar cores estimated in (cite: Morii24). $^{b}$ Number of cores in the field-of-views of GLASES observations.

![](delta_A_phy_cl.pdf)

We investigate the preferred physical conditions for detecting blue asymmetry profiles at the clump scale and their correlation with core-scale inward motion. We find some moderate correlation with clump density, protostellar core fraction and number of cores, which roughly traces the evolution of clumps. The left three panels of Figure [10](#fig:delta_A_phy_cl) are scatter plots of $A$ and $\delta$ derived from HCO$^+$ with clump density, protostellar core fraction, and the number of cores. Data implying inward/outward motion are colored by blue and red, respectively. There is a moderate correlation, implying the clearer inward motion is seen in denser, likely more evolved clumps, with a larger number of cores.

The two right panels of Figure [10](#fig:delta_A_phy_cl) show the correlation found between clump-scale $A$ and $\delta$ derived from HCO$^+$ and core-scale profile classification. $f_{blue, all}$ is the fraction of blue-skew or blue-double peak profiles against the total number of cores in the region. All values used for the plots are in Table [2](#tab:infall-clump). The correlation between clump-scale and core-scale inward motion implies multiscale, hierarchical collapse (cite: Smith09; VazquezSemadeni24): if clumps show inward motion, a higher percentage of cores show inward motion. However, we cannot fully rule out the possibility that the TP data partially reflect the cumulative emission from multiple cores rather than purely tracing the diffuse clump gas. Lower-transition observations would help to disentangle these contributions.

## Implications for Infall Velocity

Before applying an infall model, we obtain a rough idea of the infall velocity and its variation with the peak difference or the peak velocity offset from the dip velocity.

![](Vdip_Vpeak_violinplot_2lines.pdf)

Figure [11](#fig:Vdip_Vpeakdif) shows the difference of $v_{\rm dip} - v_{\rm sys}$ and the velocity difference of the two peaks $\Delta V_{peak}$ if available, which roughly trace the infall velocity and the velocity dispersion, respectively. The top row indicates a weak trend of higher infall velocity with increasing evolution or mass. The median value is almost flat in both HCO$^{+}$ and HNC plots. This implies a weak correlation between the evolutionary stage of cores and the expected infall velocity. The bottom row indicates an increase in velocity peak separation, implying a broader line width or stronger turbulence with evolution. However, as suggested by (cite: De_Vries05), for example, more careful fitting with parameters of optical depth, temperature, and density, as well as infall velocity, is required to estimate the infall parameters.

# Conclusions

We have presented the first large-scale statistical survey of gravitational infall signatures in high-mass dense cores using ALMA observations of optically thick molecular lines HCO$^+$ ($J$=3–2) and HNC ($J$=3–2). Our analysis of 304 dense cores within 24 massive 70 μm-dark clumps from the GLASHES survey provides comprehensive evidence that core-scale collapse is prevalent in the earliest stages of high-mass star formation. The main findings of this study are summarized as follows:

1.  Blue-asymmetric line profiles, indicative of infalling gas motions, are detected in approximately 50–60% of the cores using both the velocity difference parameter ($\delta_v < 0$) and the asymmetry parameter ($A > 0$). More restrictive criteria ($\delta_v < -0.25$) yield detection rates of 40–45%. Spatially, these profiles are found not only inside cores but also around cores. Considering that geometric effects and viewing angles can obscure infall signatures in genuinely collapsing cores, our results imply that infall motion is occurring around a substantial fraction of cores.

2.  The two optically thick tracers yield broadly consistent results, with HNC showing slightly higher detection rates of blue asymmetry (58% vs. 50% for $\delta_v < 0$). This difference may reflect the fact that HCO$^+$ is more susceptible to contamination from outflow emission, which can introduce red-shifted components. Despite these minor discrepancies, the overall agreement between the two tracers strengthens the robustness of our infall classifications.

3.  Approximately 60% of the sample exhibits double-peaked profiles that can be described by two-component Gaussian fits, while 15% show blue- or red-skewed profiles, 10% show single peaks, and the remaining $\sim$15% display complex morphologies. Blue-asymmetric profiles become increasingly prevalent in more massive and denser cores, especially in cores with masses $M \gtrsim 10~M_{\odot}$ and surface densities $\Sigma \gtrsim 0.1$ g cm$^{-2}$.

4.  Blue asymmetry is detected across all evolutionary stages, from prestellar cores to protostellar cores associated with outflows and warm gas emission lines.

    As cores evolve, the profiles transition toward more pronounced double-peaked morphologies with larger velocity dispersions, suggesting increasing turbulence, feedback effects, or infall velocity. The shift in the median $\delta_v$ toward more negative values with evolutionary stage indicates that infall signatures become more prominent in the protostellar phase.

5.  Remarkably, blue-asymmetric profiles are detected in $\sim$20% of cores with virial parameters $\alpha_{\rm vir} > 2$, which are nominally gravitationally unbound. This finding implies that external compression from the surrounding core material may trigger collapse, or non-thermal velocity dispersion is overestimated due to the contribution of infall motion.

6.  Analysis of clump-scale profiles reveals that inward motions occur simultaneously at both clump and core scales. We find a moderate positive correlation between clump-scale infall signatures and the fraction of cores showing blue asymmetry within those clumps. Clumps with higher densities, larger numbers of cores, and higher protostellar core fractions exhibit stronger infall signatures at both scales. This hierarchical pattern supports the clump-fed accretion scenario.

7.  Preliminary estimates based on dip velocities and peak separations imply

    a weak trend of increasing infall velocity and velocity dispersion with evolutionary stage and core mass.

In summary, our statistical survey demonstrates that gravitational collapse at the core scale is a prevalent and continuous process in high-mass star-forming regions. The detection of blue asymmetry across evolutionary stages, the infall signatures in nominally unbound cores, and the evidence for hierarchical inward motions from clump to core scales all underscore the dynamic and multi-scale nature of high-mass star formation.

We thank the anonymous referee for their careful reading and constructive comments, which improved the manuscript. PS was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI Number JP23H01221) of JSPS. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00299.S (PI: Y. Contreras), ADS/JAO.ALMA#2023.1.01150.S (PI: K. Morii) and ADS/JAO.ALMA#2024.1.01505.S (PI: K. Morii). ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

ALMA

# Software

Astropy (cite: Astropy_13; Astropy18; Astropy22), CASA (cite: CASA22), Matplotlib (cite: Hunter_matplotlib), Numpy (cite: Harris20_numpy), seaborn (cite: Waskom2021_seaborn).

# Systemic Velocity Determination

To determine the systemic velocities ($V_{\rm thin}$) of the 304 cores in our sample, we first utilized the optically thin DCO$^{+}$ and N$_2$D$^{+}$ ($J$=3–2) lines. (cite: Morii24) applied a single Gaussian fit to the core-averaged spectra and estimated the properties for 227 cores. We excluded 5 cores from this subset due to marginal 3$\sigma$ detections and ambiguous systemic velocities, leaving 222 cores with robust DCO$^{+}$or N$_2$D$^{+}$measurements.

By carefully checking the spectra of these 222 cores, along with DCN($J$=3–2), we found that 39 cores host multiple velocity peaks. In particular, clumps G025.16, G028.56, G305.79, G333.48, G333.52, and G340.39 contain more than three cores showing multiple components. For these 39 cores, we determined the representative velocity from the brightest DCO$^{+}$peak and added a flag to distinguish them from those with a single velocity component.

For the remaining 82 cores (i.e., 304 total $-$ 222) where neither DCO$^{+}$ nor N$_2$D$^{+}$ was securely detected, we fit an isolated hyperfine component of N$_2$H$^+$ ($J$=1–0, $F_1, F$ = 0,1–1,2 $\nu$= 93.176265 GHz). Through this method, we obtained $V_{\rm thin}$ for 68 of the 82 cores. Consequently, we successfully derived velocity information from optically thin lines for a total of 290 cores (222 from DCO$^{+}$ or N$_2$D$^{+}$ + 68 from N$_2$H$^+$). For the final 14 cores without any thin line detections, we assigned the average $V_{\rm thin}$ of their respective regions.

To reduce the impact of ambiguous $V_{\rm thin}$ measurements in our analysis, we flagged a total of 121 cores: the 82 cores lacking DCO$^{+}$ or N$_2$D$^{+}$ detections and the 39 cores exhibiting multiple components. This leaves a highly reliable sub-sample of 183 cores. The 121 flagged cores are highlighted in most of the figures. The derived $V_{\rm thin}$ for each core is summarized in Table [\[tab:infall\]](#tab:infall).

# Total–power Data Combination Effects

In our data analysis, we combine total power data to recover the extended emission lost due to the interferometer. To illustrate the significance of this process, in this Appendix we compare the data before and after the TP combination. Figure [12](#fig:TP-combination) shows the difference in the spatial distribution and profile of the emission. From left to right, the images show a single channel of a 12-m data cube, a 12-m + 7-m combined data cube, and a 12-m + 7-m + TP combined data cube, respectively. The color scale of the three images is the same. Clearly, the peak intensity and spatial distribution differ. Panel (a) shows negative components around the continuum cores, while panel (c) shows more extended emission than the continuum. The spectrum in panel (d) also clearly illustrates the differences. There is no significant difference far from the line center ($v_{\rm lsr} \sim$88 km s$^{-1}$), however, differences in intensity of a factor of a few exist around $v_{lsr} \sim$85.5–90 km s$^{-1}$. Regardless of the infall profile classification or modeling based on the line profile, it is clear that the combination of the 7 m and TP matters and can alter the conclusion.

![](TP_comparison.pdf)

# Line Profile Classification

The spectral profile was classified using a combination of peak-based criteria, dip significance, and Gaussian decomposition parameters. First, all local intensity maxima with S/N $>$3 were identified within a velocity range of $\pm$ 4$\times \sigma_{\rm thin}$ around the systemic velocity ($V_{\text{sys}}$). A peak was considered significant only if its amplitude exceeded the rms noise level by a factor of 3. The significant peaks were then divided into blue-shifted and red-shifted groups. If no reliable peak velocity could be determined, the profile was labeled as *undetermined*. When multiple significant peaks were present on either side, we selected only the strongest peak (i.e., the peak with the maximum intensity) as the representative blue or red component.

For profiles with $N_{\text{peak}} = 2$ (i.e., both blue and red peaks exist), a double-Gaussian model was applied immediately. For other cases, a single-Gaussian fit was first performed. If the resulting residuals exceeded $5\sigma_{\text{rms}}$ noise level, the model was upgraded to a double-Gaussian to account for hidden sub-structures. When a two-component Gaussian fit was available (six fit parameters), for each fitted Gaussian, the observed peak velocities close to each centroid velocity were identified. The relative amplitudes at these matched peak velocities were then compared to determine whether the dominant component lies on the blue- or red-shifted side relative to the systemic velocity. This matching procedure is necessary because extended components, such as outflows, can produce broad Gaussian fits whose centroids are displaced from the local spectral maxima.

Then, the velocity separation between the two Gaussian centroids ($\Delta v$) and the sum of their widths $\sigma_{1}+\sigma_{2}$ were used to distinguish morphological types:

- If $\Delta v < 0.2\ \mathrm{km\ s^{-1}}$, the profile was classified as *single*.

- If $\Delta v > \sigma_{1}+\sigma_{2}$, the profile was classified as a *double peak*; the dominant side (blue or red) was indicated according to the matched amplitudes.

- Otherwise, the profile was classified as *blue-skewed* or *red-skewed* depending on which side exhibited the stronger matched component.

- If either Gaussian width satisfied $\sigma>2.0\ \mathrm{km\ s^{-1}}$, the profile was labeled as *complex*.

When only a single-Gaussian fit was available, the profile was classified as *single*. If Gaussian fitting was not available or not conclusive, classification was done based on the peak velocity information: two detected peaks with separation $<0.2\ \mathrm{km\ s^{-1}}$ were labeled *single*; peaks separated by $>2.0\ \mathrm{km\ s^{-1}}$ were labeled *complex*; intermediate separations were assigned *blue-skewed* or *red-skewed* according to the relative peak intensities.

Figure [13](#fig:class_profile) shows some examples of the profiles with classified classes, such as double peak, skew, single, and complex, respectively. As seen in the bottom left panel, *single* may be due to the lack of sensitivity to detect the counterpart. Most *complex* profiles are affected by the multi-velocity components implied by the optically thin tracer, but as shown in the bottom right, there is a core with a single peak in optically thin line but with multiple peaks in optically thick lines.

![](ex_profiles.pdf)

Figure [14](#fig:class_corr) shows the correlation plot of line classification between HCO$^+$ and HNC, indicating the good correlation between the two lines, but not always the same. In particular, $\sim$30% of cores showing blue double profile in HNC show red double peak in HCO$^+$. This may reflect the contribution from outflow according to the higher chance of spectra with tail/wing structures seen in HCO$^+$. Some showing a single peak profile in HNC, which tend to be low-mass or less dense cores, show a skew profile in HCO$^+$, implying the initial signature of inward motion is easier to see in HCO$^+$ than HNC. More detailed discussion of these classifications and cores’ physical properties is in Section [4.2](#sec:class-phy).

![](Class_corr_2lines.pdf)

# Optical Depth Estimation of HCO$^{+}$ ($J=3-2$)

To estimate the peak optical depth ($\tau$) of the HCO$^{+}$ ($3–2$) transition, we utilized the rarer isotopologue HC$^{18}$O$^+$ ($J=3-2$) as an optically thin reference. We analyzed three representative regions (G022.69, G023.47, and G030.91), covering a total of 30 cores that span all line-profile categories discussed in this work (prestellar, protostellar, double-peaked, blue/red-skewed, and single-peaked). Both data sets used the TP+12m+7m combined products. Assuming Local Thermodynamic Equilibrium (LTE)

, the total column density is given by: $$\begin{equation}
    
    
    N = \frac{8\pi \nu^3}{c^3} \frac{ Q(T_{\rm ex})}{g_{\rm u} A_{\rm ul}}
    \frac{ {\rm exp} (E_{\rm u}/T_{\rm ex}) }{[{\rm exp} (h\nu/k_B T_{\rm ex})-1]} \int \tau dv
    \approx \frac{8\pi \nu^3}{c^3} \frac{ Q(T_{\rm ex})}{g_{\rm u} A_{\rm ul}}
    \frac{ {\rm exp} (E_{\rm u}/T_{\rm ex})}{[{\rm exp} (h\nu/k_B T_{\rm ex})-1]} \frac{W}{J(T_{\rm ex}) - J(T_{\rm bg})}
\end{equation}$$ where the approximation in the second line holds under the optically thin assumption ($\tau \ll1$) and $J(T) = \frac{h\nu/k_B}{{\rm exp}(h\nu/k_B T)-1}$. Here $W= T_{\rm b,peak}\,\Delta v_{\rm FWHM}\sqrt{\frac{\pi}{4\ln 2}}$ is the integrated intensity estimated from a Gaussian fit to the HC$^{18}$O$^+$ line, $T_{\rm b,peak}$ is the peak brightness temperature, $\Delta v_{\rm FWHM}$ is the full width at half maximum derived from the Gaussian fit, $A_{\rm ul}$ is the Einstein A coefficient, $g_{\rm u}$ is the upper-level degeneracy, $E_{\rm u}$ is the upper-level energy, $Q(T_{\rm ex})$ is the partition function, and $T_{\rm bg} = 2.73$ K is the cosmic microwave background temperature. The spectroscopic parameters adopted for HC$^{18}$O$^+$ ($J=3-2$) are $\nu =$255.488 GHz, $A_{\rm ul}=1.265\times10^{-3}$ s$^{-1}$, $E_{\rm u} = 24.52$ K, and $g_{\rm u} = 7$. We adopted the excitation temperature $T_{\rm ex} =$18.0, 13.9, and 12.4 K for G022.69, G023.47, and G030.91, derived from Herschel SED fitting (cite: Morii23), and assumed that both isotopologues share the same $T_{\rm ex}$. It should be noted that if the true excitation temperature of HCO$^{+}$ is lower than our assumed $T_{ex}$, the derived optical depth $\tau$(HCO$^+$) would be underestimated.

The total HCO$^{+}$ column density was obtained by applying the Galactocentric distance-dependent isotopic abundance ratio: $$\begin{equation}
    \frac{[{\rm ^{16}O}]}{[{\rm ^{18}O}]} = 58.8\,R_{\rm GC}\,{\rm (kpc)} + 37.1
\end{equation}$$ following (cite: Wilson94). The adopted Galactocentric distances and resulting abundance ratios are $R_{\rm GC} =$4.38, 4.19, and 5.81 kpc for G022.69, G023.47, and G030.91 (cite: Whitaker17), corresponding to ratios of $\sim$295, $\sim$284, and $\sim$379, respectively. The peak optical depth was then derived by inverting the standard LTE column density expression: $$\begin{equation}
\tau_{\rm HCO^+} = N_{\rm HCO^+} / \left[\dfrac{8\pi\nu^3}{c^3} \cdot \dfrac{Q(T_{\rm ex})}{g_{\rm u} A_{\rm ul}} \cdot \dfrac{{\rm exp}(E_{\rm u}/T_{\rm ex)}}{{\rm exp}(h\nu/k_B T_{\rm ex})-1} \cdot \Delta v_{\rm FWHM}\sqrt{\dfrac{\pi}{4\ln 2}}\right]
\end{equation}$$ where the spectroscopic parameters for HCO$^{+}$ (3–2) are $\nu = 267.566$ GHz, $A_{\rm ul} = 1.438\times10^{-3}$ s$^{-1}$, $E_{\rm u} = 25.68$ K, $g_{\rm u} = 7$, and the partition function is approximated as $Q(T_{\rm ex}) = 0.4671\,T_{\rm ex} + 0.3445$.

Of the 30 cores analyzed, HC$^{18}$O$^+$ ($J=3-2$) was detected in 14 cores, yielding optical depths in the range of 1.7–11.4 (mean=6.3), confirming that HCO$^{+}$($3–2$) is optically thick across a wide range of core properties. The majority of these detections correspond to cores exhibiting double-peaked HCO$^{+}$profiles. For the remaining 16 cores where HC$^{18}$O$^+$ was not detected, we used the $3\sigma$ rms noise level of the spectra to derive upper limits, obtaining $\tau_{\rm HCO^+} < 0.8 –13.7$ (mean upper limit = 6.7). None of the non-detections indicate clearly optically thin conditions, and optical thickness cannot be excluded in any of these cases.

# Infall Parameters and Physical Parameters

We investigated if there is any correlation between these parameters and cores physical properties. Figure [15](#fig:Adelta_MS) shows the scatter plots of $A$ and $\delta_v$ against core mass (left), surface density (middle), and virial parameters (right). Cores with blue asymmetry line profiles (i.e., a blue double peak or blue skew) are shown in color, where color represents the molecule, same as Figure [3](#fig:A_delta_scatterplot). The lines overlaid are regression plots. There is a trend of A-increase as core mass and surface density increase, and a decrease in the virial parameter. The $\delta_v$ parameter does not significantly change with core mass, density, and virial parameter. However, there are some trends when all cores are considered (gray triangles for the HNC case). These tendencies imply that more inward motions are seen from more massive, denser, and bound cores, which is consistent with the main conclusion from the main text.

![](Adelta_phy_2lines.pdf)

</paper>

Write the methods card for this paper.