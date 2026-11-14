# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...992...18P\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...992...18P",
 "title": "Early Planet Formation in Embedded Disks (eDisk). XXII. Keplerian Disk, Disk Structures, and Jets/Outflows in the Class 0 Protostar IRAS 04166+2706",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Phuong, Nguyen Thi",
 "n_authors": 23,
 "arxiv_id": "2508.07212",
 "doi": "10.3847/1538-4357/adfa92",
 "alma_projects_linked_by_archive": [
  "2019.1.00261.L"
 ]
}
```

Paper text:
<paper>
# Early Planet Formation in Embedded Disks (eDisk) XXII:\
Keplerian disk, disk structures and jets/outflows in the Class 0 protostar IRAS 04166+2706

## Abstract

We present ALMA observations of the Class 0 protostar IRAS 04166+2706, obtained as part of the ALMA large program Early Planet Formation in Embedded Disks (eDisk). These observations were made in the 1.3 mm dust continuum and molecular lines at angular resolutions of $\sim 0.05''$ ($\sim 8$ au) and $\sim 0.16''$ ($\sim25$ au), respectively. The continuum emission shows a disk-like structure with a radius of $\sim22$ au. Kinematical analysis of $^{13}$CO (2–1), C$^{18}$O (2–1), H$_2$CO (3$_{0,3}$–2$_{0,2}$), CH$_3$OH (4$_2$–3$_1$) emission demonstrates that these molecular lines trace the infalling-rotating envelope and possibly a Keplerian disk, enabling us to estimate the protostar mass to be $0.15\,\rm{M_\odot} < \rm{M_\star} < 0.39 \,M_\odot$. The dusty disk is found to exhibit a brightness asymmetry along its minor axis in the continuum emission, probably caused by a flared distribution of the dust and the high optical depth of the dust emission. In addition, the $^{12}$CO (2–1) and SiO (5–4) emissions show knotty and wiggling motions in the jets. Our high angular resolution observations revealed the most recent mass ejection events, which have occurred within the last $\sim 25$ years.

# Introduction

Planets are expected to form in circumstellar disks surrounding protostars. Therefore, studying the gas and dust properties in disks is essential to understand the formation processes of planetary systems. Observations of protoplanetary disks revealed prominent substructures, including ring, gap, crescent, and spiral. The formation of these features is attributed to several proposed mechanisms such as planet-disk interactions (cite: Paardekooper+Mellema_2004), photoevaporation (cite: Alexander+Clarke+etal-2006), magneto-rotational and hydrodynamic instabilities (cite: Flock+Ruge+etal_2015), dust accumulation at snowlines (cite: Zhang+Jin+2015), gravitational or stellar perturbations (cite: Dong+Hall_2015), and the processes of dust evolution and radial drift (cite: Ohashi-S+etal_2021). Among these proposed hypotheses, planet-disk interaction remains the leading interpretation for the observed ring and gap patterns. Indeed, ring and gap structures that can be precursors of planet formation have been observed in Class I protostars such as WL 17 and GY 91 (cite: Sheehan+etal_2017; Sheehan+etal_2018), IRS 63 (cite: Cox+etal_2020), in a flat-spectrum protostar, BHB\[2007\]1 (cite: Alves+etal_2020), and in 7 Class 0/I/Flat spectrum disks in Orion (cite: Sheehan+etal_2020). This supports the hypothesis that planetesimals and ultimately giant planet cores are formed in the disk during the earlier stages of the evolution of the protostar when it is still deeply embedded within its natal envelope (cite: Greaves+Rice_2010; Booth+Clarke_2016).

To investigate the possibility of planet formation during the protostellar phase, 12 Class 0 and 7 Class I protostars were observed as part of the ALMA Large Program Early Planet Formation in Embedded Disks (cite: Ohashi+edisk_2023) in dust continuum and line emission at the angular resolutions of 0.03 – 0.1$''$. The main objective of the eDisk program is to search for possible primordial signature of planet formation, the substructures in the disks surrounding these young protostars.

In this paper, we present observations of IRAS 04166+2706, a young stellar object (cite: Chen+etal_1995; Park+etal_2002) located in the B213 cloud, part of the Taurus molecular cloud complex. The distance to B213 was estimated to be 161.3 pc by (cite: Luhman_2018) based on Gaia DR2 measurements of stars associated with the cloud. (cite: Galli+Loinard+etal_2019) used both Gaia DR2 and VLBI data to estimate the distance of the cloud B213 to be 160.7 pc (+2.6/–2.5). (cite: Roccatagliata+etal_2020) classified B213 as part of Taurus E and reported the distance of Taurus E based on Gaia DR2 data of 160.2 (+/-0.6) pc. More recently, (cite: Krolikowski+etal_2021) used the new data of Gaia EDR3 and calculated the distance of the region to be 155.94 pc. For this paper, we adopt the most recent distance of the source as 156 pc. Using the revised distance as well as the spectral energy distribution from infrared through millimeter wavelengths, the eDisk collaboration estimated the bolometric luminosity and temperature of the source to be 0.41 L$_\odot$ and 54 K respectively, classifying it as a Class 0 protostar (cite: Ohashi+edisk_2023). The youth of the source is also witnessed by its very high-velocity outflows and collimated jets as reported by single dish and interferometric observations (cite: Tafalla+Santiago+etal_2004; Tafalla+Su+etal_2017; Santiago+etal_2009; Wang+Shang+etal_2014; Wang+Shang+etal_2019).

This paper is laid out as follows: the observations and data reduction are described in Section [2](#sec:obs). Section [3](#sec:obs_results) introduces the observing results of the 1.3 mm dust and the molecular line (CO, $^{13}$CO, C$^{18}$O, H$_2$CO, and CH$_3$OH) emission toward IRAS 04166+2706. Section [4](#sec:ana) presents the data analysis, where we explore the dust disk morphology, and its possible substructure, as well as the Position-Velocity diagrams of $^{13}$CO (2–1), C$^{18}$O (2–1), H$_2$CO (3$_{0,3}$–2$_{0,2}$)  and CH$_3$OH (4$_2$–3$_1$)  line emission in search for Keplerian gas motion in the disk to estimate the dynamical mass of the central protostar. We discuss the results in Section [5](#sec:dis) and provide a summary of the paper in Section [6](#sec:sum).

# Observation and Data Reduction

+:---------------------------:+:-----------------------------------------:+:-----------------------------------------:+:-----------------------------------------:+:------------------------------------------:+
| Date                        | 30 September, 1, 18, 24                                                               | 3 July, 2022                                                                           |
+-----------------------------+---------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
| Configuration               | C43–8                                                                                 | C43–5                                                                                  |
+-----------------------------+---------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
| Projected baseline (m)      | 46–11886                                                                              | 15–1301                                                                                |
+-----------------------------+---------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
| Time on source              | 3.0 hours                                                                             | 57 minutes                                                                             |
+-----------------------------+---------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
| Calibrator                  | J0328+1636, J0433+2905                                                                | J0510+1800, J0438+3004                                                                 |
+-----------------------------+---------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
| Phase center                | $04^{\rm{h}}19^{\rm{m}}42.51s$, $+27^{\circ}13{\ensuremath{'}}35.8\ensuremath{''}$    | $04^{\rm{h}}19^{\rm{m}}42.51s$, $+27^{\circ}13{\ensuremath{'}}35.8\ensuremath{''}$     |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+
|                             | Continuum$^\dag$                          | $^{12}$CO (2–1)$^{\dag\dag}$              | $\mbox{$^{13}$CO (2--1)}^{\dag\dag}$      | $\mbox{C$^{18}$O (2--1)}^{\dag\dag}$       |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+
| Frequency (GHz)             | 225                                       | 230.53800                                 | 220.39868                                 | 219.56035                                  |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+
| Freq. width/vel. resolution | $\sim$2 GHz                               | 0.635 km s$^{-1}$                         | 0.167 km s$^{-1}$                         | 0.167 km s$^{-1}$                          |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+
| E$_u$ (K)                   |                                           | 16.6                                      | 15.9                                      | 15.8                                       |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+
| Beam (P.A.)                 | $0.05''\times0.04''$(22$^\circ$)          | $0.17''\times0.14''$(7$^\circ$)           | $0.18''\times0.15''$(6$^\circ$)           | $0.18''\times0.14''$(8$^\circ$)            |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+
| rms                         | 23 $\mu$Jy beam$^{-1}$                    | 2.0 mJy beam$^{-1}$                       | 3.1 mJy beam$^{-1}$                       | 2.4 mJy beam$^{-1}$                        |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+
|                             |                                           | SiO (5–4)$^{\dag\dag}$                    | CH$_3$OH (4$_2$–3$_1$)$^{\dag\dag}$       | H$_2$CO (3$_{0,3}$–2$_{0,2}$)$^{\dag\dag}$ |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+
| Frequency (GHz)             |                                           | 217.10498                                 | 218.4401                                  | 218.2222                                   |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+
| E$_u$ (K)                   |                                           | 31.3                                      | 45.5                                      | 21.0                                       |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+
| Vel. resolution             |                                           | 1.34 km s$^{-1}$                          | 1.34 km s$^{-1}$                          | 1.34 km s$^{-1}$                           |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+
| Beam (P.A.)                 |                                           | $0.18''\times0.14''$(6$^\circ$)           | $0.17''\times0.14''$(6$^\circ$)           | $0.17''\times0.14''$(6$^\circ$)            |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+
| rms                         |                                           | 1.0 mJy beam$^{-1}$                       | 0.7 mJy beam$^{-1}$                       | 0.8 mJy beam$^{-1}$                        |
+-----------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+--------------------------------------------+

$^{\dag}:$ robust=0.0, $^{\dag\dag}:$ robuts=2.0

IRAS 04166+2706 was observed as part of the ALMA Large program eDisk: Early Planet Formation in Embedded Disks (cite: Ohashi+edisk_2023) using two configurations C43-8 and C43-5. The long baseline data (configuration C43-8) were obtained in 4 execution blocks (EBs) on 2021 September 30, October 1, 18, and 24, providing an observing time of $\sim 6.7$ hours with a total on-source time of $\sim 3.0$ hours. The numbers of antennas used in each block were 44, 45, 43, and 45, respectively. The baselines among the antennas ranged from 15 m to 11.89 km.

The short baseline data (configuration C43-5) were obtained in 2 blocks on 2022 July 3 with a total observing time of 2.95 hours and on-source time of $\sim 57$ minutes. The number of effective antennas used in these blocks is 41, resulting in the baselines among the antennas from 15 m to 1.3 km. The details of the spectral setup and the procedures for data processing can be found in the overview paper of eDisk (cite: Ohashi+edisk_2023). Here, we briefly summarize their main points only.

The data were reduced using the CASA version 6.2.1 and pipeline version 2021.2.0.128. The three latter EBs of long baseline data have the QA0 status of “semi-pass”[^1] due to high phase decoherence. We downloaded the raw data and ran the ALMA calibration pipeline manually. The continuum emission was obtained from line-free channels. We then imaged each execution block (EB) individually and shifted the brightest source in the image to common phase center which was obtained from the *imfit* task in CASA. After that, we computed the azimuthally averaged visibility amplitude of each dataset and plotted them together to determine the average scale factors between each EB. At this stage, we realized that the amplitude profiles of these EBs exhibited different behaviors. Therefore, we could not apply the standard eDisk reduction procedure to this dataset but the “two-pass” method is needed (cite: Ohashi+edisk_2023). Namely, we first completed the self-calibration process and determined the scale factors after self-calibration. We then reran the entire procedure from the beginning, applying these scale factors a priori. This process was performed first with the short baseline data only and then with the short baseline and long baseline data combined. Both phase self-calibration and amplitude self-calibration were used[^2]. The self-calibration solutions were then applied to all line emission.

The visibility data were imaged with different robust parameters using the task *tclean* in CASA. For this paper, we present the image of dust emission produced with a robust parameter of 0.0, while all the lines have been produced with a robust parameter of 2.0. All the maps are corrected for primary beam attenuation, and the noise levels of the line maps were measured in emission-free channels. To emphasize the presence of extended dust emission, we also present the dust emission image produced using a robust parameter of 2.0 and an $uv$ taper of 1000$k \lambda$. The main analyses of the continuum emission in this paper are performed using the image with a robust parameter 0.0 which is found to provide the best compromise between the angular resolution and sensitivity. Table 1 summarizes the main parameters of our ALMA observations for IRAS 04166+2706.

# Results

## Dust emission

![](iras04166_cont_0p0+2p0.pdf)

Figure [1](#fig:cont) shows the intensity maps of 1.3 mm dust emission produced using *robust=0.0* (left) and *robust=2.0* with a taper of 1000 $k \lambda$ (right). The left panel shows the disk-like structure out to 0.2$''$ in radius with the peak emission slightly shifted to the northeast direction from the map center (phase center). The right panel shows that besides the compact disk-like structure in the center, there are also two faint arm-like features extending out to $\sim 1.0''$.

We fit the continuum image produced with the *robust=0.0* with a model of 2D Gaussian using *imfit* task in CASA. The results of the 2D Gaussian fit are given in Table [1](#tab:imfit). The deconvolved size of the dusty disk is $138\,\rm{mas} \times 94\,\rm{mas}$, which corresponds to a linear size of $\sim$22 au$\times$15 au (at the distance of 156 pc). The position angle of the disk is P.A.=$122^\circ$ (measured counterclockwise from the north), and the inclination of the disk is $\sim47^\circ$ from $\cos^{-1}(94/138)$ under the assumption of a vertically thin circular disk geometry. The flux density of the continuum emission is $70.8\pm0.3$ mJy. We note that the fit was performed with the image produced using *robust=0.0* without any $uv$ tapering. So, possibly some extended emission (e.g. the emission from the weak envelope) may not be included in this fit value. Indeed, when all the emission greater than $3\sigma$ in the image produced with a robust value of 2.0 and a $uv$ taper of 1000$k \lambda$ (Figure [1](#fig:cont)b) are summed up, the total flux density increases to 73.5$\pm$0.15 mJy. Note that the total flux density that we detected is $\sim20$% higher than the value of $59\pm2$ mJy by IRAM PdBI observations at 1.3 mm (cite: Santiago+etal_2009).

+:---------------:+:-----------------------------------------------------:+
| Position (ICRS) | R.A: $04^{\rm{h}}19^{\rm{m}}42.51s$                   |
|                 +-------------------------------------------------------+
|                 | DEC: $+27{^\circ}13\ensuremath{'}35.8\ensuremath{''}$ |
+-----------------+-------------------------------------------------------+
| Major axis      | $137.9\pm0.7$ mas                                     |
+-----------------+-------------------------------------------------------+
| Minor axis      | $93.7\pm0.5$ mas                                      |
+-----------------+-------------------------------------------------------+
| Position angle  | $121.5^\circ\pm0.5^\circ$                             |
+-----------------+-------------------------------------------------------+
| Flux density    | $70.8\pm0.3$ mJy                                      |
+-----------------+-------------------------------------------------------+

: Result of the 2D Gaussian fit to dust continuum image of *robust=0.0*

The major axis, minor axis and position angle are deconvolved

## Molecular line emission

Figure [2](#fig:Tpeak-all) shows the peak brightness temperature maps of $^{12}$CO (2–1), $^{13}$CO (2–1), C$^{18}$O (2–1), H$_2$CO (3$_{0,3}$–2$_{0,2}$), and CH$_3$OH (4$_2$–3$_1$). The brightness temperature was computed using Planck function. We describe detailed features of each molecular line emission below.

![](iras04166_Tpeak.pdf)

**$^{12}$CO (2–1) and SiO (5–4):** Figure [3](#fig:12co-moments) shows the integrated intensity (moment 0) and mean velocity (moment 1) maps of the $^{12}$CO (2–1) emission. Both moment 0 and 1 maps were made with a threshold of $3\sigma$ in the velocity range of $V_{LSR}=-60~\rm{to}~ 60$ km s$^{-1}$. The panels (b) and (c) show mean velocity maps of the high- and low- velocity components, respectively. These maps display the conical outflows and jets structures where the blue-shifted emission is stronger on the north-east side than the red-shifted emission, as shown in the peak brightness temperature map (Figure [2](#fig:Tpeak-all)), which was also reported by (cite: Santiago+etal_2009), (cite: Wang+Shang+etal_2014) and (cite: Tafalla+Su+etal_2017). The structures of conical outflows and jets are almost symmetric with respect to the minor axis of the dust disk, suggesting that the the axis of the outflows and jets are almost aligned with the disk minor axis. We note that there is also $^{12}$CO (2–1) emission distribution perpendicular to the outflows axis around the protostar, as better seen in Figure [3](#fig:12co-moments)(d), which may mostly originate from the disk/envelope.

Figure [4](#fig:sio-moments) shows the moment maps of SiO (5–4). The moments were computed in a velocity range of –70 to 70 km s$^{-1}$  with a threshold of 3 $\sigma$. The SiO (5–4) emission reveals episodic jets at a high velocity of $|V_{LSR}|>20$ km s$^{-1}$, with the blue-shifted emission stronger than the red-shifted counterpart. The right panel of this figure shows a closer view of the central region, which reveals several intensity peaks (contours) and a stretched S-shape morphology on the blue-shifted side, suggesting wiggling or precession motions in the jet. Intensity maps integrated in narrower velocity ranges will be discussed in Section [4.4](#sec:jets_outflows).

![image](12co-intensity-map.pdf) ![image](12co-velocity-maps.pdf) ![image](12co-intensity+velocity-zoom.pdf)

![image](sio-intensity.pdf) ![image](sio-velocity.pdf) ![image](sio-intensity+velocity-Zoom-map.pdf)

**$^{13}$CO (2–1) and C$^{18}$O (2–1):** Figure [5](#fig:c18o+13co_moments) shows moment 0 and 1 maps of $^{13}$CO (2–1) and C$^{18}$O (2–1) emission. The moment 0 maps are made in the velocity range of $V_{LSR}$=3.5 to 10 km s$^{-1}$, and the velocity maps are produced with a threshold of 4 $\sigma$. Note that both intensities of $^{13}$CO (2–1) and C$^{18}$O (2–1) emission are significantly dropped at the center. This may be caused by the absorption of line emission by the continuum. The velocity maps show complicated gas kinematics with red-shifted and blue-shifted emission mixed, probably revealing the combination of the disk and envelope kinematics. The right panels of this figure show the same velocity maps zoomed in the central protostar region. The dust disk region shows a velocity gradient between red-shifted emission on the western side and blue-shifted emission on the eastern side. The direction of the velocity gradient appears to be misaligned from the direction of the major axis of the dust disk. The blue-shifted emission close to the central star may trace some part of the outflow, as such blue-shifted emission is also well distributed toward the north-east side. However, as shown in the Figure [5](#fig:c18o+13co_moments) (c) and (f), the features are very close to the area where dust emission detected, suggesting that velocity pattern can be also interpreted as a mixture of rotation and infalling motion in the flattened disk/envelope (cite: Momose_1998).

![image](13co21-intensity.pdf) ![image](13co21-velocity.pdf) ![image](c18o21_intensity.pdf) ![image](c18o21_velocity.pdf)

**H$_2$CO (3$_{0,3}$–2$_{0,2}$) and CH$_3$OH (4$_2$–3$_1$):** Figure [6](#fig:h2co+ch3oh-moments) shows moment 0 and 1 maps of the H$_2$CO (3$_{0,3}$–2$_{0,2}$) and CH$_3$OH (4$_2$–3$_1$) emission. The moments were computed in the velocity range of $V_{LSR}$=3.5 to 10 km s$^{-1}$ with a threshold of $3\sigma$.

The H$_2$CO (3$_{0,3}$–2$_{0,2}$) maps show primarily two emission components; one component surrounding the dust disk, similar to the $^{13}$CO (2–1) and C$^{18}$O (2–1) emissions, and the other tracing the outflow-related components. The former one exhibits rather complicated velocity structures, which may be a combined effect of rotation, infall, and innermost outflowing gas motions. Zooming in the dust disk region, we see a clear velocity gradient along the major axis of the dust disk indicating the presence of rotating motions in the disk.

It is noted that this axis is slightly offset towards the blue-shifted emission. Although it is not clear why there is such an offset, our low spectral resolution ($\sim1.34$ km s$^{-1}$) observations of these lines can be one possible reason. The H$_2$CO (3$_{0,3}$–2$_{0,2}$) maps include the blue-shifted outflow component to the north along the outflow axis, which is slightly tilted toward the southeast with respect to the outflow axis, and the X-shape outflow components near the protostar. Note that there is no red-shifted H$_2$CO (3$_{0,3}$–2$_{0,2}$) emission along the outflow axis to the south, while there are blue and red-shifted components in the X-shape outflow.

The CH$_3$OH (4$_2$–3$_1$) emission is seen in the central region of the system, mostly coinciding with the dust emission, and has a velocity gradient along the major axis of the dust disk, again possibly tracing the rotational motions. In addition, the northeast blue-shifted outflow-related emission is also observed in CH$_3$OH (4$_2$–3$_1$) at about the same position and the same velocity as the H$_2$CO (3$_{0,3}$–2$_{0,2}$) emission. Like the case of H$_2$CO (3$_{0,3}$–2$_{0,2}$) emission, there is no counterpart of the outflow to the southwest direction.

We present channel maps of all the mentioned lines in Appendix [7](#sec:channel-maps). Our observations also include two other lines of H$_2$CO (H$_2$CO (3$_{2,1}$–2$_{2,0}$) and H$_2$CO (3$_{2,2}$–2$_{2,1}$)), SO (6$_5$–5$_4$), DCN (3–2), and 3 lines of c-C$_3$H$_2$ (c-C$_3$H$_2$ (6$_{0,6}$–5$_{1,5}$), c-C$_3$H$_2$ (5$_{1,4}$–4$_{2,3}$), c-C$_3$H$_2$ (5$_{2,4}$–4$_{1,3}$)). We present their moment 0 and moment 1 maps in Appendix [8](#sec:other_lines).

![image](h2co-intensity.pdf) ![image](h2co-velocity.pdf)\
![image](ch3oh-intensity-map.pdf) ![image](ch3oh-velocity-map.pdf)

# Analysis

## Disk mass

Assuming that the dust emission is optically thin and isothermal, we can estimate the disk dust mass using the following equation: $$\begin{equation}
\centering
M_d=\frac{S_\nu\,d^2}{\kappa_\nu\,B_\nu(T_d)}, 
\end{equation}$$ where $\nu$ is the observed frequency (225 GHz), $S_\nu$ is the flux density of dust emission (70.8 mJy) derived from the previous 2D Gaussian fit (to the *robust=0.0* image), $d$ is the source distance (156 pc), $B_\nu(T_d)$ is the Planck function at the dust temperature of $T_d$, and $\kappa_\nu$ is the dust mass opacity at the observed frequency. We adopt the dust opacity of $\kappa_{1.3\,mm}$=2.3 cm$^2$ g$^{-1}$ (cite: Beckwith+etal_1990), and assume a dust temperature of 20 K which is the median value of dust temperatures of disks in the Taurus star-forming region as derived by (cite: Andrews+etal_2005). Assuming a gas-to-dust ratio of 100, we obtained the disk mass of 0.015 M$_{\odot}$.

(cite: Tobin+etal_2020) introduced a more realistic method to estimate the dust temperature of Class 0/I objects based on the source luminosity as $T_{\rm{d}}=43\,(L_{\rm{bol}}/\rm{L}_\odot)^{0.25}$. Applying this equation to the case of IRAS 04166+2706 ($L_{\rm{bol}}=0.41\,\rm{L}_\odot$) we obtain the dust temperature of $\sim$34 K in this disk. Using the dust temperature of 34 K and all the other parameters the same as above, we obtain the total mass in the disk of 0.008 M$_\odot$.

(cite: Santiago+etal_2009) estimated a value of 0.02 M$_\odot$ for the disk mass. They derived the mass from IRAM PdBI observations of 1.3 mm using dust temperature of 20 K and dust opacity of 1.0  cm$^{2}$ g$^{-1}$ (cite: Ossenkopf+Henning_1994). Adopting their value of opacity, we obtained 0.028 M$_\odot$ for the disk mass, in good agreement with the value quoted by (cite: Santiago+etal_2009). These estimates would be only valid if the emission is indeed optically thin. If it is optically thick, the derived mass would be a lower limit. We also emphasize that our estimate of the disk mass is also consistent with the estimate of (0.027 M$_\odot$) from RADMC-3D modeling and MCMC fit using a wide range SED set data including CARMA mm data (cite: Sheehan+Eisner_2017).

## Identifying a possible substructure in the continuum disk

In this section, we attempt to identify any possible faint substructures in the continuum disk which can be a signature of primordial formation of proto-planets.

Figure [7](#fig:cont-assy) shows intensity profiles of the 1.3 mm dust-continuum emission along the major and minor axes on both sides with respect to the disk center. The figure reveals overall a symmetric distribution of the dust continuum along the major axis of the disk, but with a slight depression of intensity ($<3\sigma$) at a radii of $0.18''$, deeper to the northwest direction than to the southeast direction. On the other hand, the profile along the minor axis presented in the lower panel of the figure shows an asymmetric distribution at $r>0.06''$.

![](continuum_robust0_minor-major_revised.pdf)

Figure [8](#fig:cont-radial-profile) shows the radial intensity profile of the 1.3 mm dust emission azimuthally averaged in annuli of 0.01$''$ ($\sim$ 1/4 of the beam) in the plane of the disk. The deprojection was performed using a position angle of 121.5$^\circ$ and an inclination of 47$^\circ$, as derived from the 2D Gaussian fit presented above, assuming a flat-thin disk geometry. A single Gaussian function did not adequately fit the data. Therefore we performed a two Gaussian function fit to the radial profile. The results of the fit and its residual are presented in Figure [8](#fig:cont-radial-profile). The residual profile shows two peaks and two valleys at different amplitudes which we refer to as “ring” and “gap”, respectively. To characterize the rings, we fit the residual with Gaussian functions. The inner ring has an amplitude at the level of 2.4 $\sigma$, and the outer ring has an amplitude of $129\pm40\,\mu$Jy ($\sim6\pm2\,\sigma$) located at $\sim0.09''$ (14 au) with a width of 10.3 mas (1.6 au), indicating that the amplitude level of the inner ring is not statistically significant. In addition, the width of the outer ring is only a fraction of the beam. Although the above analyses suggest the presence of possible “ring” and “gap” features in the protostellar disk, we note that this residual could be due to an azimuthally and radially local brightness enhancement, rather than a ring (i.e., an azimuthally uniform enhancement) since the intensity is averaged in the azimuthal direction. Additionally, because these features are close to our sensitivity level and resolution, we are unable to confirm them unambiguously.

![](continuum_profile.pdf)

## An analysis of Position-Velocity diagrams of $^{13}$CO (2–1)  and C$^{18}$O (2–1) 

In this section, we attempt to estimate the protostellar mass by searching for a signature of Keplerian motion in the gas disk. For this purpose, we examine the position-velocity (PV) diagrams of the $^{13}$CO (2–1) and C$^{18}$O (2–1) emissions along the major axis of the dust disk (P.A.=122$^\circ$ east of north), within the width of one beam. As shown in Figure [9](#fig:c18o+13co_pv-full), emissions are present in all 4 quadrants, indicating that the lines also trace other motions such as infall motions and/or outflows.

![](pv-major-13co+c18o.pdf)

We analyze these PV diagrams using the $pvanalysis$ module in the Python package Spectral Line Analysis/Modeling code[^3] (cite: Aso+Sai_2024). The analysis and fitting processes are described in detail in the overview paper of the eDisk project (cite: Ohashi+edisk_2023). Briefly, we first determine the emission edge and ridge positions (or velocities) from a one-dimensional cut of the PV diagram along the position (or velocity) axis. The ridge is determined from the peak derived by the 1D Gaussian fitting to the emission along the positional (or velocity) axis, while the edge is determined as the outermost contour of the emission above a given threshold. The derived positions and velocities $(r,v)$ can then be fitted with a power-law function: $$\begin{equation}
\label{eq:pv}
\centering 
V_{rot}=|v-V_{sys}|=v_b(\frac{r}{r_b})^{-p}, 
\end{equation}$$ where $V_{sys}$ is the systemic velocity, $r_b$ is a characteristic radius, where $v_b$ is measured.

+-------+-----------+------------------+------------------+-------------+
|       |           | $^{13}$CO (2–1)  | C$^{18}$O (2–1)  | Unit        |
+:=====:+:=========:+:=================+:=================+:===========:+
| Edge  | $r_b$     | $31.2\pm1.0$     | $35.3\pm2.3$     | au          |
|       +-----------+------------------+------------------+-------------+
|       | $v_b$     | $2.4\pm0.01$     | $2.3\pm0.01$     | km s$^{-1}$ |
|       +-----------+------------------+------------------+-------------+
|       | $V_{sys}$ | $7.0\pm0.02$     | $7.0\pm0.07$     | km s$^{-1}$ |
+-------+-----------+------------------+------------------+-------------+
|       | $p$       | $0.66\pm0.13$    | $0.58\pm0.22$    |             |
+-------+-----------+------------------+------------------+-------------+
|       | $M_\star$ | $0.38\pm0.01$    | $0.39\pm0.03$    | $M_\odot$   |
+-------+-----------+------------------+------------------+-------------+
| Ridge | $r_b$     | $16.1\pm1.1$     | $13.0\pm2.3$     | au          |
|       +-----------+------------------+------------------+-------------+
|       | $v_b$     | $2.4\pm0.01$     | $2.3\pm0.01$     | km s$^{-1}$ |
|       +-----------+------------------+------------------+-------------+
|       | $V_{sys}$ | $6.8\pm0.15$     | $6.8\pm0.11$     | km s$^{-1}$ |
+-------+-----------+------------------+------------------+-------------+
|       | $p$       | $0.67\pm0.16$    | $0.49\pm0.22$    |             |
+-------+-----------+------------------+------------------+-------------+
|       | $M_\star$ | $0.19\pm0.01$    | $0.15\pm0.03$    | $M_\odot$   |
+-------+-----------+------------------+------------------+-------------+

: Best fit parameters to the PV diagrams for $^{13}$CO (2–1) and C$^{18}$O (2–1) emissions along the major axis of the dust disk.

![](pv_SLAM-13co+c18o-highvelo.pdf)

Figure [9](#fig:c18o+13co_pv-full) shows that the $^{13}$CO (2–1) and C$^{18}$O (2–1) PV diagrams consistently exhibit only red-shifted components in the first quadrant within the velocity range of $v\geqslant8.5$ km s$^{-1}$. Conversely, in the third quadrant, only blue-shifted components are observed, specifically, in $^{13}$CO (2–1) at v $v\leqslant4.5$ km s$^{-1}$ and in C$^{18}$O (2–1) at $v\leqslant4.7$ km s$^{-1}$.

We determine the edge and ridge data points at this velocity range and fit them with the power-law function ([\[eq:pv\]](#eq:pv)) to check whether the Keplerian disk is present in this small region. The ridge was derived using a threshold of $6\sigma$ for the case of $^{13}$CO (2–1). For the case of lower signal-to-noise emission of C$^{18}$O (2–1), we derived the ridge using a threshold of $3\sigma$. The best-fit parameters are $p=0.66\pm0.13$ and $p=0.67\pm0.16$ in the edge and ridge for the $^{13}$CO (2–1) emission, respectively. In the case of C$^{18}$O (2–1), these parameters are $p=0.58\pm0.20$, and $p=0.49\pm0.22$, respectively. The derived edge and ridge points and their corresponding best-fit function are presented Figures [10](#fig:13co+c18o-pv-fit) and the best-fit values are summarized in Tables [2](#tab:PV-13co+c18o). The power-law fit indices agree with each other within their mutual uncertainties for the rotating gas motions to be closely consistent with Keplerian rotation ($V_{rot}\propto r^{-0.5}$) in the disk.

Thus the stellar mass can be estimated under the assumption that the gases are in the Keplerian motion ($v=\sqrt{GM_\star/r}$) in the disk with inclination of $i=47^\circ$ around the central star. The stellar masses derived from the edge and ridge results of $^{13}$CO (2–1) and C$^{18}$O (2–1)  are consistent within their respective uncertainties. It is not clear which of the two techniques is more reliable. However, it is well known that the ridge fitting systematically underestimates, while the edge fitting overestimates the stellar mass (cite: Maret+Maury_2020; Aso+etal_2015). Therefore, we have simply adopted the lowest and highest of derived values as the lower and upper limits of our stellar mass estimate as $0.15\,\rm{M_\odot} < \rm{M_\star} < 0.39 \,M_\odot$.

![](pv-major-ch3oh_h2co.pdf)

As shown in Figure [6](#fig:h2co+ch3oh-moments), the velocity gradient of H$_2$CO (3$_{0,3}$–2$_{0,2}$) and CH$_3$OH (4$_2$–3$_1$) in the disk is well aligned with the major axis of the dust disk. Namely, these lines can be tracers of rotation motion in the disk. Figure [11](#fig:ch3oh+h2co-pv) presents PV diagrams of the CH$_3$OH (4$_2$–3$_1$) and H$_2$CO (3$_{0,3}$–2$_{0,2}$) emission along the major axis of the dust disk in a width of 1 beam. On the large scale, the H$_2$CO (3$_{0,3}$–2$_{0,2}$) emission appears in all quadrants in the PV diagram, suggestive of infalling motion, with a slight velocity gradient between the east and west, indicative of rotation. On the other hand, the CH$_3$OH (4$_2$–3$_1$) emission is mostly confined to the region of dust continuum emission from the disk and likely shows a linear velocity gradient. On the small scale, the H$_2$CO (3$_{0,3}$–2$_{0,2}$) emission may show signatures of possible Keplerian motions in the disk. However, the poor velocity resolution of 1.34 km s$^{-1}$ of CH$_3$OH (4$_2$–3$_1$) and H$_2$CO (3$_{0,3}$–2$_{0,2}$) prevents us from performing a similar analysis to what we did for the $^{13}$CO (2–1) and C$^{18}$O (2–1) emission. Instead of making power law fitting of the data, we overlaid the Keplerian trajectories of gas motions by a central source of 0.15 M$_\odot$ and 0.39 M$_\odot$ in the PV diagrams for these tracers in the right panel of Figure [11](#fig:ch3oh+h2co-pv), indicating that H$_2$CO (3$_{0,3}$–2$_{0,2}$)  emission is consistent with the Keplerian motion.

## Jets and Outflows

The molecular jets and outflows in IRAS 04166+2706 have been previously reported in $^{12}$CO (2–1) and SiO (2–1) using the IRAM 30m telescope (cite: Tafalla+Santiago+etal_2004) and using the IRAM PdBI (cite: Santiago+etal_2009). Those observations showed that the outflows and jets from IRAS 04166+2706 extend up to $\sim 450''$. Within $\sim120''$, the jets are found to include 7 pairs of knots at high-velocity of $30<\mid V-V_{\rm{sys}}\mid<50$ km s$^{-1}$ (cite: Santiago+etal_2009). (cite: Wang+Shang+etal_2014) then observed similar outflows and jets in the CO(3–2) line using ALMA. Recently, the outflows and jets in $^{12}$CO (2–1) and SiO (5–4) observations at 1.0$''$ resolution have been reported by (cite: Tafalla+Su+etal_2017). Our observations also reveal the emission of $^{12}$CO (2–1) and SiO (5–4) of the two pairs of knots (R1, B1) and (R2, B2) within 24$''$ as reported by (cite: Wang+Shang+etal_2014), and particularly resolve another pair of knots at the distance of $\sim0.5''-2''$ from the protostar (R0 and B0 marked in Figure [12](#fig:12co+sio_regimes)) thanks to the higher resolution of the present data.

To look for more detailed structures in the outflows and jets, we present the moment 0 maps of the $^{12}$CO (2–1) (top) and SiO (5–4) (bottom) emissions integrated in the three velocity ranges of $10<\mid V-V_{\rm{sys}}\mid<30$ km s$^{-1}$, $30<\mid V-V_{\rm{sys}} \mid<50$ km s$^{-1}$, and $50<\mid V-V_{\rm{sys}} \mid<65$ km s$^{-1}$ in Figure [12](#fig:12co+sio_regimes). In the case of $^{12}$CO (2–1), we also present the intensity map of the low-velocity outflow component integrated in the range of $2<\mid V-V_{\rm{sys}} \mid<10$ km s$^{-1}$  in the leftmost panel of the figure. These intensity maps in specific velocity ranges are found to be very useful to reveal more prominent shapes of the conical bipolar outflows in the velocity range ($2<\mid V-V_{\rm{sys}} \mid<10$ km s$^{-1}$) and the collimated jets in the range of $30<\mid V-V_{\rm{sys}} \mid<65$ km s$^{-1}$. The integrated intensity map in the velocity range of $10<\mid V-V_{\rm{sys}}\mid<30$ km s$^{-1}$ also reveals the presence of the faint emission of B2 knot and the outer bow of the R2 knot of the jet. At high-velocities, we clearly see the symmetric distribution of these two pairs of knots as reported earlier in (cite: Wang+Shang+etal_2014). We also notice the presence of two bow shapes of the R2 knot in the $^{12}$CO (2–1) map in the velocity range of $30<\mid V-V_{\rm{sys}}\mid<50$ km s$^{-1}$. At the highest velocities, the narrower jets are found closer to the central source, separated from the B1 and R1 knots (marked as B0, and R0), much stronger in the SiO (5–4) than in the $^{12}$CO (2–1) emission. Particularly, the B0 and R0 knots seem reveal the wiggling motion as mentioned in the Section [3](#sec:obs_results). These jets imply the presence of three episodic mass ejections (R0 to R2 and B0 to B2) with an average velocity of 40 km s$^{-1}$  within a radius of $11''$, yielding an average ejection period of

$$\begin{equation}
\frac{11''\times 156 [\rm{pc}]}{\cos(i) \times 3\times 40\,[\rm{km/s}] / \sin(i)} \sim 73\, \rm{years},
\end{equation}$$ where $i=47^\circ$.

![image](12co-shv_colorbar.png) ![image](12co-ihv_colorbar.png) ![image](12co-ehv_colorbar.png) ![image](12co-e2hv_colorbar.png)\
![image](sio-ihv_colorbar.png) ![image](sio-ehv_colorbar.png) ![image](sio-e2hv_colorbar.png)

Figure [13](#fig:12co+sio-jets) shows a comparison between the high-velocity components of SiO (5–4) and $^{12}$CO (2–1) emission in the range of $30<|V-V_{\rm{sys}}|<65$ km s$^{-1}$, indicating that the SiO (5–4) and $^{12}$CO (2–1) jets spatially overlap, and thus they might arise from the same mass ejection events.

(Jy beam$^{-1}$)\
![image](sio+co-jet.png)

Figure [14](#fig:12co+sio-pv-EHV) shows the PV diagrams of the high-velocity jets of $^{12}$CO (2–1) and SiO (5–4) emission along the jets/outflows axis (P.A.=32$^\circ$). At the high velocities, both $^{12}$CO (2–1) and SiO (5–4) show a saw-tooth feature exhibiting episodic “slow head” and “fast tail” properties - the “head” of the mass ejection, which is further in the distance than the “tail" from the central star, moves slower than the “tail", as already reported by (cite: Santiago+etal_2009). The difference in the velocity between the “head” and the “tail” is about 15–20  km s$^{-1}$. The features were interpreted as arising from gas ejected sideways in a series of internal shocks inside the pulsating jets (cite: Tafalla+Su+etal_2017) or by a spherically expanding wind with axial density concentration (cite: Wang+Shang+etal_2019). Previous observations by (cite: Wang+Shang+etal_2014) identified the two pairs of knot (B1, R1) and (B2, R2), but not as clearly as our observations with $\sim 40$ times better spatial resolution. Especially, in the red-shifted part of the $^{12}$CO (2–1) emission, each knot is found to contain two features that were marked with black lines in the upper left panel of Figure [14](#fig:12co+sio-pv-EHV). We also note that there are two other knots (B0, R0) close to the central protostar, each likely contains also two continuous ejection events at distances of about 100 au and 300 au (see Figure [14](#fig:12co+sio-pv-EHV)), respectively. Based on the B0 and R0 knots, we estimate that the most recent ejection events may have occurred only about 20–25 years ago.

![image](12co-high_velo-outflow.pdf) ![image](sio-high_velo-outflow.pdf)

The PV diagram of the $^{12}$CO (2–1)  low-velocity outflow component (left panel of Figure [15](#fig:pv_SHV)) shows that the mean velocity of the outflow is within 5 km s$^{-1}$  with respect to the systemic velocity. The blue-shifted emission is much stronger than the red-shifted emission. Figure [15](#fig:pv_SHV) (right panel) shows the PV diagrams of H$_2$CO (3$_{0,3}$–2$_{0,2}$) and CH$_3$OH (4$_2$–3$_1$) along jets/outflows axis superimposed by the CO outflow emission, suggesting that the H$_2$CO (3$_{0,3}$–2$_{0,2}$) and CH$_3$OH (4$_2$–3$_1$) features in the velocity range of $V_{\rm{LSR}}\sim 0-4$ km s$^{-1}$ at large distance from the central protostar ($\sim 800$ au) can be likely outflow-related.

![](low_velo_outflow.pdf)

# Discussion

## Brightness asymmetry, dust mass in the disk, and disk stability

In Section [4.2](#sec:dust-morp), we have shown that the 1.3  mm observation reveals a disk structure with a radius of $\sim22$ au, with the presence of a brightness asymmetry along the minor axis of the disk. This asymmetric emission distribution along the minor axis has been also seen in other protostellar disks which are on close edge-on geometry, such as HH212 mms (cite: Lee-CF+etal_2017) and the eDisk targets (CB 68; (cite: Kido+eDisk_2023), L1527IRS; (cite: vanHoff+eDisk_2023), IRAS 04302+2247; (cite: Lin+eDisk_2023), and GSS30 IRS3; (cite: Santamaria-Miranda+eDisk_2023)). Recent 3D radiative transfer (RADMC-3D) calculations by (cite: Takakuwa+eDisk_2024) demonstrated that this asymmetric distribution of dust disk emission can be caused by the combined effect of vertically extended dust emission above the mid-plane, a so called flared distribution of the dust and high optical depth of the dust emission. Therefore it is thought that for IRAS 04166+2706, its inclined disk is probably flared in a way that its far and near sides are on the northeastern (NE) and southwestern (SW) parts of the disk, respectively, as expected from the outflow patterns blueshifted to the northeast and redshifted to the southwest. This geometry of the disk would result in its northeastern part being brighter and the southwestern part being fainter, as our observing line-of-sight would preferentially observe the hotter part of the northern disk and cooler part of the southeastern disk. We measured an integrated flux ratio of 1.17 between the northeastern (NE) and southwestern (SW) hemispheres, indicating that the far-side hemisphere is 17% brighter than the near side. This is broadly consistent with the asymmetry seen in the synthetic continuum image from (cite: Takakuwa+eDisk_2024). Their models suggest that, for a disk with $M_{\rm{disk}} \leq 0.14 M_\star$, a flaring index of $h/r \propto r^{0.3}$ is required to produce a clearly asymmetric intensity profile along the minor axis. An even higher flaring index is needed for disks with lower mass, such as in the case of IRAS 04166+2706. However, other reasons, such as non-axisymmetric internal structures, cannot be ruled out. It is possible that the large-scale spirals as shown in the Figure [1](#fig:cont)(b) contribute to the observed asymmetric distribution. A more quantitative comparison between the observed asymmetry and the radiative transfer model is needed to determine the origin of the asymmetry in the disk.

On the other hand, our estimated dust mass in the disk of the order of 25 to 50 M$_\oplus$ is found to be useful to make a discussion on the potential for planet formation in the disk. As discussed by (cite: Tychoniec+etal_2020), the planet formation efficiency is of the order of $15\%$ assuming that the planet starts to form in the Class 0 disk. In this scenario, the disk mass of IRAS 04166 +2706 is sufficient to form a core (of a planet) with a mass of 4 - 7 M$_\oplus$ in the disk. Moreover, this young disk at the Class 0/I stage is still accreting the material from its natal envelope. Then the amount of the material both in the solid and gas in the disk may be replenished, thus increasing the material available for planet formation to form a giant planet core in the future. In this case, the solid mass in the disk of IRAS 04166+2706 is likely sufficient to form a giant planet core of $\geqslant7_\oplus$.

The stability of a disk against gravitational collapse can be examined by using Toomre’s criterion of (cite: Toomre_1994) $$\begin{equation}
Q=\frac{c_s\Omega}{\pi G \Sigma} = 2 \frac{M_\star}{M_{\rm{disk}}}\frac{H}{R}, 
\end{equation}$$ where $M_\star$ is the mass of the central star, $M_{\rm{disk}}$ is the mass of the disk, R is the radius of the disk, and $H=c_s/\Omega$ while $c_s$ is sound speed and $\Omega=\sqrt{G M_\star/R^3}$. A geometrically thin disk would be gravitationally unstable if its Toomre number of $Q<1-1.5$ depending on the type of disturbances in disk (cite: Durisen+etal_2007). In the case of IRAS 04166+2706, adopting R=22 au $M_\star$=0.15–0.39 $M_\odot$, $M_{\rm{disk}}$=0.015 $M_\odot$ and 0.008 $M_\odot$, and the sound speeds $c_s$ for the dust temperature of 20 K and 34 K, we derive the Toomre number of $\sim1.4$ to 5.6. This result indicates that the disk of IRAS 04166+2706 is stable, or at most, marginally unstable but we emphasize that there are still significant uncertainties due to the assumptions about optical depth, dust opacity, and dust temperature.

## Wiggling motion in the jets and knotty jets

In this section, we discuss other indirect signatures for substructures in the disk. The wiggling motion in the high-velocity jet component seen in the SiO (5–4) emission as shown in the right panel of Figure [4](#fig:sio-moments) is one of them. The wiggling structure observed in the molecular outflows/jets is not fully understood in the field. It can be explained in terms of the variability of mass ejection directions (cite: Gueth+etal_1996; Podio+etal_2016) caused by orbital motion of a companion (cite: Masciadri+Raga_2002), or tidal interactions between the protostellar disk and noncoplanar binary component (cite: Terquem+etal_1999), which all require a companion (binary system). (cite: Frank+Ray_2014) also proposed a mechanism that such mass ejection angle variability can be caused by the ejection mechanism itself (e.g. controlled by the disk B-field) in a single star system. At the very high angular resolution observations of 8 au in our eDisk observations, we could not resolve any binary component in the IRAS 04166+2706 system, thus the former hypothesis may not be plausible to explain the wiggling jets observed in the SiO (5–4) emission. However, it may be interesting to examine in the future whether the presence of an unresolved companion, like planets in the system, can affect any pattern of jet gas motions from a protostellar object.

The knotty jets observed in $^{12}$CO (2–1) and SiO (5–4) may indicate episodic mass ejections of a period of $\sim73$ years (cite: Tafalla+Su+etal_2017). Our observations also revealed the presence of a pair of recent mass ejection events occurred $\sim 20-25$ years ago. We note that the removal of angular momentum and disk mass via magnetocentrifual wind can lead to the formation of local substructures such as rings or gaps (cite: Pascucci+etal_2022). Future identification of substructures in the disk would be highly useful to examine a possible link between their formation in the disk and the knotty jets in the IRAS 04166+2706 in relation with an episodic angular momentum removal.

# Summary

This paper presents the results of ALMA observations of 1.3 mm dust continuum at an angular resolution of $0.05''$, and molecular lines ($^{12}$CO (2–1), $^{13}$CO (2–1), C$^{18}$O (2–1), H$_2$CO (3$_{0,3}$–2$_{0,2}$) and CH$_3$OH (4$_2$–3$_1$)) at an angular resolution of $\sim 0.15''$ towards the Class 0 source IRAS 04166+2706. Our main results are summarized as follows:

- The observation at 1.3 mm revealed a dust disk structure of a radius of 0.15$''$ ($\sim$22 au), its major axis at P.A.=122$^\circ$, and an inclination of 47$^\circ$. The mass of the disk is estimated to be $M_{\rm{disk}}\sim1.5\times10^{-2}\,\rm{M}_\odot$.

- The dust disk shows an asymmetric brightness distribution along the minor axis in the sense of the brightness peaking to the northeast of the disk geometric center. We are cautious to interpret this as an existence of a possible substructure in the disk, as such brightness asymmetry can be easily caused by the combined effect of a flared distribution of the dust and high optical depth of the dust emission.

- Multiple molecular lines such as the $^{13}$CO (2–1), C$^{18}$O (2–1), H$_2$CO (3$_{0,3}$–2$_{0,2}$) and CH$_3$OH (4$_2$–3$_1$) lines are found to probe the rotating gas motions in the disk. Particularly C$^{18}$O (2–1) line likely traces the Keplerian motion, enabling to estimate the mass of the protostar mass to be $0.15\,\rm{M_\odot} < \rm{M_\star} < 0.39 \,M_\odot$.

- Molecular lines of $^{12}$CO (2–1)  and SiO (5–4)  show energetic, knotty jets as already found in previous studies. However, our results showed the innermost jet/outflow knots, B0 and R0, close to the central protostar, which may have very recently occurred only 20–25 years ago.

# Acknowledgments

We are grateful to the anonymous reviewer for valuable comments. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00261.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. C.W.L. was supported by the Basic Science Research Program through the National Research Foundation of Korea (NRF) funded by the Ministry of Education, Science and Technology (NRF-2019R1A2C1010851), and by the Korea Astronomy and Space Science Institute grant funded by the Korea government (MSIT; project No. 2024-1-841-00). J.J.T. acknowledges support from NASA XRP 80NSSC22K1159. Z.Y.L is supported in part by NASA 80NSSC20K0533 and NSF AST-2307199 and AST-1910106. J.K.J. and S.G. acknowledge support from the Independent Research Fund Denmark (grant No. 0135-00123B). S.T. is supported by JSPS KAKENHI Grant Numbers 21H00048 and 21H04495. This research is funded by the Vietnam Academy of Science and Technology under grant number VAST08.02/25-26. This work was supported by NAOJ ALMA Scientific Research Grant Code 2022-20A. This work was partly supported by a grant from the Simons Foundation to IFIRSE, ICISE(916424;N.H.). L.W.L acknowledges support from NSF AST-2108794. ZYDL acknowledges support from NASA 80NSSCK1095, the Jefferson Scholars Foundation, the NRAO ALMA Student Observing Support (SOS) SOSPA8-003, the Achievements Rewards for College Scientists (ARCS) Foundation Washington Chapter, the Virginia Space Grant Consortium (VSGC), and UVA research computing (RIVANNA). N.O. and C.F. acknowledge support from National Science and Technology Council (NSTC) in Taiwan through NSTC 113-2112-M-001-037 and from Academia Sinica Investigator Project Grant AS-IV-114-M02.

natexlab

(ref: Alexander+Clarke+etal-2006) Alexander, R. D., Clarke, C. J., & Pringle, J. E. 2006, MNRAS, 369, 229, doi: [`10.1111/j.1365-2966.2006.10294.x`](http://doi.org/10.1111/j.1365-2966.2006.10294.x)

(ref: Alves+etal_2020) Alves, F. O., Cleeves, L. I., Girart, J. M., et al. 2020, ApJL, 904, L6, doi: [`10.3847/2041-8213/abc550`](http://doi.org/10.3847/2041-8213/abc550)

(ref: Andrews+etal_2005) Andrews, S. M., & Williams, J. P. 2005, ApJ, 631, 1134, doi: [`10.1086/432712`](http://doi.org/10.1086/432712)

(ref: Aso+Sai_2024) Aso, Y., & Sai, J. I. C. 2024, Publications of the Korean Astronomical Society, 39, 27. <http://pkas.kas.org/journal/article.php?code=91201>

(ref: Aso+etal_2015) Aso, Y., Ohashi, N., Saigo, K., et al. 2015, ApJ, 812, 27, doi: [`10.1088/0004-637X/812/1/27`](http://doi.org/10.1088/0004-637X/812/1/27)

(ref: Beckwith+etal_1990) Beckwith, S. V. W., Sargent, A. I., Chini, R. S., & Guesten, R. 1990, AJ, 99, 924, doi: [`10.1086/115385`](http://doi.org/10.1086/115385)

(ref: Booth+Clarke_2016) Booth, R. A., & Clarke, C. J. 2016, MNRAS, 458, 2676, doi: [`10.1093/mnras/stw488`](http://doi.org/10.1093/mnras/stw488)

(ref: Chen+etal_1995) Chen, H., Myers, P. C., Ladd, E. F., & Wood, D. O. S. 1995, ApJ, 445, 377, doi: [`10.1086/175703`](http://doi.org/10.1086/175703)

(ref: Dong+Hall_2015) Dong, R., Hall, C., Rice, K., & Chiang, E. 2015, ApJL, 812, L32, doi: [`10.1088/2041-8205/812/2/L32`](http://doi.org/10.1088/2041-8205/812/2/L32)

(ref: Durisen+etal_2007) Durisen, R. H., Boss, A. P., Mayer, L., et al. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 607, doi: [`10.48550/arXiv.astro-ph/0603179`](http://doi.org/10.48550/arXiv.astro-ph/0603179)

(ref: Flock+Ruge+etal_2015) Flock, M., Ruge, J. P., Dzyurkevich, N., et al. 2015, A&A, 574, A68, doi: [`10.1051/0004-6361/201424693`](http://doi.org/10.1051/0004-6361/201424693)

(ref: Frank+Ray_2014) Frank, A., Ray, T. P., Cabrit, S., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 451–474, doi: [`10.2458/azu_uapress_9780816531240-ch020`](http://doi.org/10.2458/azu_uapress_9780816531240-ch020)

(ref: Galli+Loinard+etal_2019) Galli, P. A. B., Loinard, L., Bouy, H., et al. 2019, A&A, 630, A137, doi: [`10.1051/0004-6361/201935928`](http://doi.org/10.1051/0004-6361/201935928)

(ref: Greaves+Rice_2010) Greaves, J. S., & Rice, W. K. M. 2010, MNRAS, 407, 1981, doi: [`10.1111/j.1365-2966.2010.17043.x`](http://doi.org/10.1111/j.1365-2966.2010.17043.x)

(ref: Gueth+etal_1996) Gueth, F., Guilloteau, S., & Bachiller, R. 1996, A&A, 307, 891

(ref: Kido+eDisk_2023) Kido, M., Takakuwa, S., Saigo, K., et al. 2023, ApJ, 953, 190, doi: [`10.3847/1538-4357/acdd7a`](http://doi.org/10.3847/1538-4357/acdd7a)

(ref: Krolikowski+etal_2021) Krolikowski, D. M., Kraus, A. L., & Rizzuto, A. C. 2021, AJ, 162, 110, doi: [`10.3847/1538-3881/ac0632`](http://doi.org/10.3847/1538-3881/ac0632)

(ref: Lee-CF+etal_2017) Lee, C.-F., Li, Z.-Y., Ho, P. T. P., et al. 2017, Science Advances, 3, e1602935, doi: [`10.1126/sciadv.1602935`](http://doi.org/10.1126/sciadv.1602935)

(ref: Lin+eDisk_2023) Lin, Z.-Y. D., Li, Z.-Y., Tobin, J. J., et al. 2023, ApJ, 951, 9, doi: [`10.3847/1538-4357/acd5c9`](http://doi.org/10.3847/1538-4357/acd5c9)

(ref: Luhman_2018) Luhman, K. L. 2018, AJ, 156, 271, doi: [`10.3847/1538-3881/aae831`](http://doi.org/10.3847/1538-3881/aae831)

(ref: Maret+Maury_2020) Maret, S., Maury, A. J., Belloche, A., et al. 2020, A&A, 635, A15, doi: [`10.1051/0004-6361/201936798`](http://doi.org/10.1051/0004-6361/201936798)

(ref: Masciadri+Raga_2002) Masciadri, E., & Raga, A. C. 2002, ApJ, 568, 733, doi: [`10.1086/338767`](http://doi.org/10.1086/338767)

(ref: Momose_1998) Momose, M., Ohashi, N., Kawabe, R., Nakano, T., & Hayashi, M. 1998, ApJ, 504, 314, doi: [`10.1086/306061`](http://doi.org/10.1086/306061)

(ref: Ohashi+edisk_2023) Ohashi, N., Tobin, J. J., Jørgensen, J. K., et al. 2023, ApJ, 951, 8, doi: [`10.3847/1538-4357/acd384`](http://doi.org/10.3847/1538-4357/acd384)

(ref: Ohashi-S+etal_2021) Ohashi, S., Kobayashi, H., Nakatani, R., et al. 2021, ApJ, 907, 80, doi: [`10.3847/1538-4357/abd0fa`](http://doi.org/10.3847/1538-4357/abd0fa)

(ref: Ossenkopf+Henning_1994) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: Paardekooper+Mellema_2004) Paardekooper, S. J., & Mellema, G. 2004, A&A, 425, L9, doi: [`10.1051/0004-6361:200400053`](http://doi.org/10.1051/0004-6361:200400053)

(ref: Park+etal_2002) Park, S., & Kenyon, S. J. 2002, AJ, 123, 3370, doi: [`10.1086/340467`](http://doi.org/10.1086/340467)

(ref: Pascucci+etal_2022) Pascucci, I., Cabrit, S., Edwards, S., et al. 2022, arXiv e-prints, arXiv:2203.10068, doi: [`10.48550/arXiv.2203.10068`](http://doi.org/10.48550/arXiv.2203.10068)

(ref: Podio+etal_2016) Podio, L., Codella, C., Gueth, F., et al. 2016, A&A, 593, L4, doi: [`10.1051/0004-6361/201628876`](http://doi.org/10.1051/0004-6361/201628876)

(ref: Roccatagliata+etal_2020) Roccatagliata, V., Franciosini, E., Sacco, G. G., Randich, S., & Sicilia-Aguilar, A. 2020, A&A, 638, A85, doi: [`10.1051/0004-6361/201936401`](http://doi.org/10.1051/0004-6361/201936401)

(ref: Santamaria-Miranda+eDisk_2023) Santamarı́a-Miranda, A., de Gregorio-Monsalvo, I., Ohashi, N., et al. 2024, A&A, 690, A46, doi: [`10.1051/0004-6361/202449981`](http://doi.org/10.1051/0004-6361/202449981)

(ref: Santiago+etal_2009) Santiago-Garcı́a, J., Tafalla, M., Johnstone, D., & Bachiller, R. 2009, A&A, 495, 169, doi: [`10.1051/0004-6361:200810739`](http://doi.org/10.1051/0004-6361:200810739)

(ref: Cox+etal_2020) Segura-Cox, D. M., Schmiedeke, A., Pineda, J. E., et al. 2020, Nature, 586, 228, doi: [`10.1038/s41586-020-2779-6`](http://doi.org/10.1038/s41586-020-2779-6)

(ref: Sheehan+etal_2017) Sheehan, P. D., & Eisner, J. A. 2017a, ApJL, 840, L12, doi: [`10.3847/2041-8213/aa6df8`](http://doi.org/10.3847/2041-8213/aa6df8)

(ref: Sheehan+Eisner_2017) Sheehan, P. D., & Eisner, J. A. 2017b, ApJ, 851, 45, doi: [`10.3847/1538-4357/aa9990`](http://doi.org/10.3847/1538-4357/aa9990)

(ref: Sheehan+etal_2018) Sheehan, P. D., & Eisner, J. A. 2018, ApJ, 857, 18, doi: [`10.3847/1538-4357/aaae65`](http://doi.org/10.3847/1538-4357/aaae65)

(ref: Sheehan+etal_2020) Sheehan, P. D., Tobin, J. J., Federman, S., Megeath, S. T., & Looney, L. W. 2020, ApJ, 902, 141, doi: [`10.3847/1538-4357/abbad5`](http://doi.org/10.3847/1538-4357/abbad5)

(ref: Tafalla+Santiago+etal_2004) Tafalla, M., Santiago, J., Johnstone, D., & Bachiller, R. 2004, A&A, 423, L21, doi: [`10.1051/0004-6361:200400015`](http://doi.org/10.1051/0004-6361:200400015)

(ref: Tafalla+Su+etal_2017) Tafalla, M., Su, Y. N., Shang, H., et al. 2017, A&A, 597, A119, doi: [`10.1051/0004-6361/201629493`](http://doi.org/10.1051/0004-6361/201629493)

(ref: Takakuwa+eDisk_2024) Takakuwa, S., Saigo, K., Kido, M., et al. 2024, ApJ, 964, 24, doi: [`10.3847/1538-4357/ad1f57`](http://doi.org/10.3847/1538-4357/ad1f57)

(ref: Terquem+etal_1999) Terquem, C., Eislöffel, J., Papaloizou, J. C. B., & Nelson, R. P. 1999, ApJL, 512, L131, doi: [`10.1086/311880`](http://doi.org/10.1086/311880)

(ref: Tobin+etal_2020) Tobin, J. J., Sheehan, P. D., Megeath, S. T., et al. 2020, ApJ, 890, 130, doi: [`10.3847/1538-4357/ab6f64`](http://doi.org/10.3847/1538-4357/ab6f64)

(ref: Toomre_1994) Toomre, J. 1994, in American Astronomical Society Meeting Abstracts, Vol. 184, American Astronomical Society Meeting Abstracts #184, 50.02

(ref: Tychoniec+etal_2020) Tychoniec, Ł., Manara, C. F., Rosotti, G. P., et al. 2020, A&A, 640, A19, doi: [`10.1051/0004-6361/202037851`](http://doi.org/10.1051/0004-6361/202037851)

(ref: vanHoff+eDisk_2023) van’t Hoff, M. L. R., Tobin, J. J., Li, Z.-Y., et al. 2023, ApJ, 951, 10, doi: [`10.3847/1538-4357/accf87`](http://doi.org/10.3847/1538-4357/accf87)

(ref: Wang+Shang+etal_2019) Wang, L.-Y., Shang, H., & Chiang, T.-Y. 2019, ApJ, 874, 31, doi: [`10.3847/1538-4357/ab07b5`](http://doi.org/10.3847/1538-4357/ab07b5)

(ref: Wang+Shang+etal_2014) Wang, L.-Y., Shang, H., Su, Y.-N., et al. 2014, ApJ, 780, 49, doi: [`10.1088/0004-637X/780/1/49`](http://doi.org/10.1088/0004-637X/780/1/49)

(ref: Zhang+Jin+2015) Zhang, Y., & Jin, L. 2015, ApJ, 802, 58, doi: [`10.1088/0004-637X/802/1/58`](http://doi.org/10.1088/0004-637X/802/1/58)

# Channel maps of main molecular lines

In this section, we present the channel maps of the main molecular lines that we presented and discussed in Section [3](#sec:obs_results). Channel maps of $^{13}$CO (2–1)and C$^{18}$O (2–1) are presented in Figure [16](#fig:channel-13co+c18o). Channel maps of SiO (5–4) are presented in Figure [17](#fig:channel-sio), and channel maps of H$_2$CO (3$_{0,3}$–2$_{0,2}$)and CH$_3$OH (4$_2$–3$_1$) are presented in Figure [18](#channel-h2co+ch3oh).

![image](iras04166_13CO_channel.png) ![image](iras04166_C18O_channel.png)

![image](iras04166_SiO_blue_channel.png)\
![image](iras04166_SiO_red_channel.png)

![image](iras04166_H2CO_channel.png) ![image](iras04166_CH3OH_channel.png) ![image](iras04166_CH3OH_channel_zoom.png)

# Other molecular lines

In this section, we present all the other molecular lines that we observed in the eDisk program towards IRAS04166+2706. They are H$_2$CO (3$_{2,1}$–2$_{2,0}$), H$_2$CO (3$_{2,1}$–2$_{2,0}$), SO (6$_5$–5$_4$), c-C$_3$H$_2$ (6$_{0,6}$–5$_{1,5}$), c-C$_3$H$_2$ (5$_{1,4}$–4$_{2,3}$), c-C$_3$H$_2$ (5$_{2,4}$–4$_{1,3}$), and DCN (3–2). All images are produced using $robust$ parameters of 2.0. We summarize the main parameters of these observations in Table [3](#tab:other_lines) and present their moment maps in Figures [19](#fig:c3h2+dcn) and [20](#fig:h2co+so). The moment 0 and moment 1 maps of these 7 lines have been computed using a threshold of 3$\sigma$ in the velocity range of $V_{\rm{LSR}}$=3–11 km s$^{-1}$.

Figure [19](#fig:c3h2+dcn) shows the moment 0 and moment 1 maps of three c-C$_3$H$_2$ lines and DCN emission. The c-C$_3$H$_2$ (6$_{0,6}$–5$_{1,5}$) and c-C$_3$H$_2$ (5$_{1,4}$–4$_{2,3}$) lines are well detected and show X-shape like features in the center region of $\sim 3.0''$ as in the case of H$_2$CO (3$_{0,3}$–2$_{0,2}$). Also, the moment 1 maps reveal the complicated kinematics mixed between the red- and blue-shifted emission at the same offset position. The DCN emission is detected in the central region of $\sim 1.25''$ with complex kinematics.

As shown in Figure [20](#fig:h2co+so), the two lines of H$_2$CO (3$_{2,1}$–2$_{2,0}$) and H$_2$CO (3$_{2,2}$–2$_{2,1}$) (upper-level energy $E_u$=68 K) are well detected in the central region close to the protostar but the extent is much narrower than that of its lower energy level line of H$_2$CO (3$_{0,3}$–2$_{0,2}$)($E_u$=21 K). The SO (6$_5$–5$_4$) line is also well detected in the very compact center region and peaks outside the central protostar at an offset of $\sim 0.1''$ in the southwest quadrant. In addition, the blueshifted outflow-related feature has been detected in all three lines like in the case of CH$_3$OH (4$_2$–3$_1$) (and lower energy level transition of H$_2$CO). This likely supports that the emission is caused by shocks from the outflow.

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Lines | Frequency | Velocity resolution | E$_u$ | Beam (P.A) | Noise |
|  | (GHz) | (km s$^{-1}$) | \(K\) |  | (mJy beam$^{-1}$) |
| H$_2$CO (3$_{2,1}$–2$_{2,0}$) | 218.760056 | 0.167 | 68.1 | $0.17''\times0.14''(\rm{7^\circ})$ | 1.97 |
| H$_2$CO (3$_{2,2}$–2$_{2,1}$) | 218.475642 | 1.34 | 68.1 | $0.17''\times0.14''(\rm{7^\circ})$ | 0.71 |
| c-C$_3$H$_2$ (6$_{0,6}$–5$_{1,5}$) | 217.829416 | 1.34 | 38.6 | $0.17''\times0.14''(\rm{6^\circ})$ | 0.77 |
| c-C$_3$H$_2$ (5$_{1,4}$–4$_{2,3}$) | 217.947320 | 1.34 | 35.4 | $0.17''\times0.14''(\rm{6^\circ})$ | 0.71 |
| c-C$_3$H$_2$ (5$_{2,4}$–4$_{1,3}$) | 218.167717 | 1.34 | 35.4 | $0.17''\times0.14''(\rm{6^\circ})$ | 0.71 |
| SO (6$_5$–5$_4$) | 219.953477 | 1.34 | 35.0 | $0.18''\times0.15''(\rm{10^\circ})$ | 2.45 |
| DCN (3–2) | 217.245846 | 1.34 | 20.9 | $0.18''\times0.14''(\rm{7^\circ})$ | 8.0 |

: Summary of ALMA observations of the SO, DCN, H$_2$CO and c-C$_3$H$_2$ molecular lines

![](c3h2_dcn.pdf)

![](h2co-so.pdf)

[^1]: QA stands for Quality-Assurance. The QA0 is a near-real-time verification of data quality, reflecting the quality of the calibrations included in each EB. The QA2 includes full calibration of the entire collection of EBs.

[^2]: See detail in https://github.com/jjtobin/edisk

[^3]: The Spectral Line Analysis/Modeling (SLAM) tool is publicly available at https://github.com/jinshisai/SLAM.

</paper>

Write the methods card for this paper.