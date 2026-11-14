# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024RAA....24f5011X\sonnetcc\reply.txt

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
 "bibcode": "2024RAA....24f5011X",
 "title": "The ALMA-QUARKS Survey. II. The ACA 1.3 mm Continuum Source Catalog and the Assembly of Dense Gas in Massive Star-Forming Clumps",
 "year": 2024,
 "journal": "Research in Astronomy and Astrophysics",
 "first_author": "Xu, Fengwei",
 "n_authors": 33,
 "arxiv_id": "2404.02275",
 "doi": "10.1088/1674-4527/ad3dc3",
 "alma_projects_linked_by_archive": [
  "2019.1.00685.S",
  "2021.1.00095.S"
 ]
}
```

Paper text:
<paper>
# The ALMA-QUARKS Survey: II. the ACA 1.3 mm continuum source catalog and the assembly of dense gas in massive star-forming clumps

UTF8gbsn

# Introduction

High-mass stars ($M>8$ $M_\odot$), as the principal sources of UV radiation and heavy elements, play a major role in the evolution of galaxies. However, the properties and evolution of massive clumps hosting the precursors of massive stars currently forming in our Galaxy are still poorly known (cite: Zinnecker2007MSF; Tan2014MSF; Pineda2023PP7). Fragmentation of massive clumps into dense cores, where star formation ultimately occurs, is a critical step in the mass assembly process that gives rise to stars and clusters, as highlighted by (cite: Motte2018Review). Investigating how dense gas is concentrated and structured within these massive clumps serves as an intermediate step in understanding this intricate process.

Recent studies, such as (cite: Peretto2020ClumpFed), have conducted sub-millimeter continuum surveys of infrared dark clouds, revealing that the evolution of massive compact sources in mass-versus-temperature diagrams is better explained by an accretion scenario where cores gain mass while simultaneously collapsing to form protostars. Furthermore, the findings from (cite: Rigby2021GASTON) provide evidence for the mass growth of clumps, suggesting that similar mass accumulation processes may occur on a broader range of physical scales, which is further verified in several multiscale case studies (cite: Neupane2020Global; Xu2023ATOMS-XV; Yang2023G310). On the simulation side, the mass growth of a ‘core’ is believed to be the result of the collapse of the surrounding parsec-scale mass reservoir called a ‘clump’, hence the accretion scenario described above is referred to as ‘clump-fed’ (cite: Wang2010ClumpFed).

The ‘clump-fed’ scenario suggests that there must be a link between the properties of a clump and the fragments that form within it. In the case of clump fragmentation, (cite: Lin2019SABOCA) find a correlation between the mass of the clump and the mass of its most massive fragment of massive clumps from “the APEX Telescope Large Area Survey of the Galaxy” (cite: Schuller2009ATLASGAL). Besides, (cite: Barnes2021IRDCs) also find that more massive, and more turbulent clouds make more $\sim0.1$ pc scale cores. (cite: Anderson2021HFS) collected a sample of massive clumps with a wide range of evolutionary stages, and suggested time-dependent correlation between clump and core mass especially in hub-filament systems. The relation between the formation of dense cores and the properties of clumps such as turbulence is also discussed (cite: Xu2021HGaL; Xu2024Scarcity). On a smaller scale, studies such as (cite: Palau2014Fragmentation; Palau2021Fragmentation) find correlations between the level of fragmentation within massive dense cores ($<0.1$ pc) and their average volume density, aligning with the expectations of the Jeans instability (cite: Sanhueza2019ASHES; Morii2024). Furthermore, using ALMA with a resolution of approximately 0.02 pc, (cite: Xu2024ASSEMBLE) identified a sublinear correlation between the mass of the clump and the mass of its most massive core, in a sample of 11 massive protoclusters that show clump-scale infall motion. For comparison, no such correlation was found in a sample of 39 massive early-stage clumps from (cite: Morii2023ASHES). This suggests that the mass correlation between the clumps and the cores gradually builds up over the evolution of massive clumps.

Despite previous great advances, our understanding of the formation process of massive stars remains unclear and divided due to observational difficulties. On the one hand, considering their large distances (a few kpc) and high dust extinction, studies of massive clumps need high-resolution interferometric observations to resolve their internal gas structures and kinematics (cite: Wang2015Book; Motte2018Review; LinY2021PhDThesis). On the other hand, obtaining robust and definitive conclusions regarding the accretion history of high-mass stars requires a larger statistical sample. This, in turn, calls for rapid survey capabilities with adequate sensitivity. The Atacama Large Millimeter/submillimeter Array (ALMA), with both high resolution and high sensitivity, offers a unique valuable opportunity to investigate the hierarchical structures in massive star-forming regions in great detail. Therefore, we performed a 1.3-mm ALMA survey called “Querying Underlying mechanisms of massive star formation with ALMA-Resolved gas Kinematics and Structures” (QUARKS; PIs: Lei Zhu, Guido Garay and Tie Liu; Project ID: 2021.1.00095.S). The details of the survey description and the showcase of data combinations can be found in (cite: Liu2023QUARKS).

In this paper, we focus mainly on the Atacama Compact Array (ACA) 7-m continuum and line data sets. With relatively little free-free emission contamination and a maximum recoverable scale as large as $\sim27$$''$, ACA 1.3 mm continuum data are useful for tracking dense molecular gas within massive clumps. With an angular resolution of $\sim5$$''$, equivalent to 0.07 pc at a typical distance of 3 kpc within the QUARKS sample, the ACA data provide a global view of massive protostars or protoclusters therein. We first introduce the ACA observations and data imaging in Section [2](#sec:data), and then provide the first edition of the QUARKS atlas in Section [3](#sec:atlas). Section [4](#sec:results) constructs the ACA 1.3 mm continuum source catalog including physical parameters. In Section [5.1](#discuss:nature), we discuss the physical nature of ACA sources and find that they are condensed gas fragments within massive clumps. In Section [5.2](#discuss:corr), we find a mass correlation between clumps and their fragments. In Section [5.3](#discuss:DGF), we discuss the size-invariant and time-variant dense gas fraction. In Section [5.4](#discuss:fragmentation), we discuss limited fragmentation at the subclump scale. In Section [6](#sec:sum), we present a brief summary.

# QUARKS ACA Data

## Observing Strategy

QUARKS acts as a follow-up 1.3-mm survey of ALMA Three-millimeter Observations of Massive Star-forming regions (cite: Liu2020ATOMS-I), and aims at studying even smaller structures within the 3-mm cores or core clusters within massive star-forming clumps. To ensure uniformity of the sample and solid detection at 1.3 mm, we exclude: 1) two low-mass clumps ($<15$ $M_\odot$); 2) four sources dominated by extended HII regions with angular sizes larger than the primary beam at Band 6; 3) one source without continuum emission detection by ATOMS. As a result, 139 ATOMS massive clumps are selected as the QUARKS sample, hereafter the QUARKS clumps. A total of 156 ALMA 1.3 mm pointings were performed because some 3 mm emission show elongated or extended morphologies and need two mosaicked pointings (dual-pointing mosaicked field). The on-source time of each pointing was about 5 minutes.

The QUARKS ACA observations are separated into 15 scheduling blocks (SBs), hereafter called groups for short. The group ID and the number of fields therein are listed in columns (1)–(2) of Table [\[tab:almaobs\]](#tab:almaobs). To finish the observing queue, 1–3 execution blocks (EBs) were performed on different observing dates, which are listed in column (3). Fields in the same group have the proximity of sky coordinates and the same EBs, so they share similar minimum and maximum baselines (BL), angular resolution (AR), and maximum recoverable scale (MRS), which are listed in columns (4)–(6). Variations in AR and MRS are mostly the result of different configuration of the array and source elevation. Phase and flux calibrators are listed in column (7), while bandpass and flux calibrators are listed in column (8).

The observations utilized ALMA Band 6 receivers in dual-polarization mode, with the correlator frequencies configured into four spectral windows (SPWs 1–4). The four SPWs were designed with center frequencies at approximately 217.92 GHz, 220.32 GHz, 231.37 GHz, and 233.52 GHz, each with a bandwidth of 2 GHz and 4096 channels. This setup was chosen to cover a wide range of commonly used tracers representing different environments and excitation conditions. The targeted lines included, but were not limited to: 1) outflow tracers (e.g., CO, $^{13}$CO, SiO, SO, H$_2$CO); 2) cold gas tracer (N$_2$D$^+$); 3) dense core and filament tracers (e.g., C$^{18}$O, HC$_3$N); 4) hot core tracers (e.g., CH$_3$OH, C$_2$H$_5$CN, NH$_2$CHO, CH$_3$CN); 5) ionized-gas/HII-region tracer (H$_{30}\alpha$). The basics of the main targeted lines are summarized in Table 2 of (cite: Liu2023QUARKS).

+----------+-----------------------+------------+--------------+--------+--------+----------------------------+-------------------+
| Group ID | $n_{\rm field}$$^{a}$ | Obs. Date  | Min./Max. BL | AR     | MRS    | Calibrators                | cont. rms         |
+:========:+:=====================:+:==========:+:============:+:======:+:======:+:==========:+:=============:+:=================:+
| 7-8      |                       |            | (m/m)        | ($''$) | ($''$) | Phase      | Bandpass/Flux | (mJy beam$^{-1}$) |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
| \(1\)    | \(2\)                 | \(3\)      | \(4\)        | \(5\)  | \(6\)  | \(7\)      | \(8\)         | \(9\)             |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
| 1        | 6                     | 2021-11-06 | 8.9/45.0     | 4.9    | 20.0   | J0922-3959 | J1058+0133    | 10                |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
|          |                       | 2021-10-22 | 8.9/44.7     | 5.1    | 28.3   | J1047-6217 | J1058+0133    |                   |
|          |                       +------------+--------------+--------+--------+------------+---------------+                   |
|          |                       | 2022-05-21 | 8.9/45.0     | 4.9    | 28.7   | J1047-6217 | J1058+0133    |                   |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
| 3        | 7                     | 2023-01-02 | 8.9/48.9     | 5.0    | 28.3   | J1424-6807 | J1427-4206    | 9                 |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
|          |                       | 2023-01-13 | 8.9/48.9     | 4.8    | 28.3   | J1337-6509 | J1427-4206    |                   |
|          |                       +------------+--------------+--------+--------+------------+---------------+                   |
|          |                       | 2023-01-16 | 8.9/48.0     | 5.0    | 28.3   | J1337-6509 | J1427-4206    |                   |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
|          |                       | 2023-04-09 | 8.9/48.0     | 4.5    | 21.1   | J1604-4441 | J1427-4206    |                   |
|          |                       +------------+--------------+--------+--------+------------+---------------+                   |
|          |                       | 2023-04-13 | 8.9/48.0     | 4.9    | 27.1   | J1617-5848 | J1427-4206    |                   |
|          |                       +------------+--------------+--------+--------+------------+---------------+                   |
|          |                       | 2023-04-18 | 8.9/48.0     | 4.9    | 27.1   | J1617-5848 | J1427-4206    |                   |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
| 6        | 5                     | 2023-01-01 | 8.9/48.9     | 5.3    | 28.3   | J1524-5903 | J1427-4206    | 18                |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
|          |                       | 2023-05-17 | 8.9/48.9     | 4.8    | 27.1   | J1733-3722 | J1924-2914    |                   |
|          |                       +------------+--------------+--------+--------+------------+---------------+                   |
|          |                       | 2023-05-20 | 8.9/48.9     | 4.8    | 27.1   | J1733-3722 | J1924-2914    |                   |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
| 8        | 3                     | 2023-01-14 | 8.9/48.0     | 4.9    | 21.1   | J1924+1540 | J2232+1143    | 43                |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
| 9        | 3                     | 2023-01-22 | 8.9/48.0     | 5.0    | 28.3   | J1744-3116 | J1427-4206    | 22                |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
|          |                       | 2023-03-04 | 9.1/45.0     | 4.9    | 21.1   | J1851+0035 | J1924-2914    |                   |
|          |                       +------------+--------------+--------+--------+------------+---------------+                   |
|          |                       | 2023-04-16 | 8.9/48.0     | 4.9    | 27.1   | J1851+0035 | J1924-2914    |                   |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
| 11       | 7                     | 2023-04-08 | 8.9/48.0     | 4.5    | 21.1   | J1717-3342 | J1427-4206    | 28                |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
|          |                       | 2023-04-25 | 8.9/48.0     | 4.9    | 27.1   | J1604-4441 | J1427-4206    |                   |
|          |                       +------------+--------------+--------+--------+------------+---------------+                   |
|          |                       | 2023-05-01 | 8.9/48.0     | 4.9    | 27.1   | J1604-4441 | J1427-4206    |                   |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
|          |                       | 2023-03-04 | 9.1/45.0     | 4.9    | 21.1   | J1851+0035 | J1924-2914    |                   |
|          |                       +------------+--------------+--------+--------+------------+---------------+                   |
|          |                       | 2023-04-09 | 8.9/48.0     | 4.5    | 21.1   | J1851+0035 | J1924-2914    |                   |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
| 14       | 6                     | 2023-04-21 | 8.9/48.0     | 4.9    | 27.1   | J1820-2528 | J1924-2914    | 17                |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+
|          |                       | 2023-04-17 | 8.9/48.0     | 4.9    | 27.1   | J1832-2039 | J1924-2914    |                   |
|          |                       +------------+--------------+--------+--------+------------+---------------+                   |
|          |                       | 2023-04-18 | 8.9/48.0     | 4.9    | 27.1   | J1832-2039 | J1924-2914    |                   |
+----------+-----------------------+------------+--------------+--------+--------+------------+---------------+-------------------+

The QUARKS ACA observations are separated into 15 scheduling blocks which are called groups for short. The group ID, the number of targets therein, and the dates of observation are listed in columns (1)–(3). The minimum and maximum baselines (BL) of the configuration array are listed in column (4). Group-averaged angular resolution (AR) and maximum recoverable scale (MRS) are listed in columns (5)–(6). The phase calibrator(s) are listed in column (7) while the bandpass and flux calibrators are listed in column (8). The aggregated continuum imaging rms and spectral line rms per channel are listed in column (9).\
$^{(a)}$Including both single-pointing and dual-pointing fields, therefore 139 in total.

## Data Calibration and Imaging

QUARKS ACA data were acquired during the ALMA Cycle 8 and 9 observations. The data were routinely calibrated using the ALMA pipelines [^1] of Common Astronomy Software Applications (cite: McMullin2007CASA; CASA2022) in the corresponding versions of 6.2.1 and 6.4.1. The frequency tunings of the correlator are four wide bands, each with 2 GHz separated by 4096 channels. The edge channels of each spectral window ($\sim2\times128$) were flagged in the first version of data release due to the high temperature of the system noise and therefore the high level of noise.

Line emission channels were flagged to obtain the continuum and spectral lines simultaneously. (cite: Liu2023QUARKS) identified all the transitions of strong lines within the four SPWs by matching the reduced data cubes of the ALMA pipeline and the laboratory databases for the spectral lines (cite: Muller2001CDMS). The QUARKS team generated a model spectrum as a mask for line emission channels. For each source, the model spectrum was shifted and expanded with a width of 50 km s$^{-1}$ to ensure clean channels free from multiple velocity components and spectral line wings. With this method the line emission channels were flagged and the line-free channels were subtracted from the four spectral windows in the Fourier space using the task *uvcontsub* with linear fitting (polynomial order of 1). The continuum and line cube imaging processes were performed by the task *tclean* in CASA 6.5.6, with `briggs` robust weighting of 0.5. In the cleaning process, the images/cubes were automatically masked by `auto-multithresh` algorithm whose input parameters are recommended by the official guides [^2] for the ACA data. At the beginning of each minor cycle, the cleaning mask was updated on the basis of the current residual image. The algorithm uses multiple thresholds based on the noise and sidelobe levels in the residual image to determine the cleaning mask. Within the cleaning mask, we set the stopping `noisethreshold` to be 5$\sigma$ and `sidelobethreshold` to be $1.25\sigma$ in the dirty image/cube. However, the cleaning algorithm diverges when some fields have relatively strong emission or side lobes at the edge. For these fields, we performed a manual mask to further improve the imaging fidelity. To recover the potential large-scale structures in the spectral lines and mitigate artifacts produced by extended emission, we applied the `multiscale` deconvolver (cite: Cornwell2008Multiscale) to the cleaning process of line cubes, with scales of \[0,5,15\]. We uniformly set the image size of $108\times108$ pix$^2$ and cell size of 1$''$, to fully cover the 17 mosaic fields with dual pointings. The primary beam correction was performed with ` pblimit = 0.2`.

The noise rms of the cleaned continuum image is tabulated in column (9) of Table [\[tab:almaobs\]](#tab:almaobs). The rms levels have large variations between groups because some sources are too strong and the continuum sensitivities are limited by the dynamic range. Self-calibration can improve the sensitivity, but will not contribute much to the science goals in this paper. Therefore, self-calibration has not been performed on our released ACA data.

# QUARKS Atlas

With the inclusion of QUARKS as a high-resolution submillimeter dataset, we are now equipped to construct a comprehensive data atlas for the QUARKS sample, offering insights into the multiscale and multiphase interstellar medium (ISM) in high-mass star formation.

The mid infrared (MIR) Spitzer facility was equipped with the InfraRed Array Camera (IRAC) instrument that provided images at 3.6, 4.5, 5.8, and 8.0 $\mu$m simultaneously. Here we combine the Galactic Legacy Infrared Mid-Plane Survey Extraordinaire (GLIMPSE) data at 3.6, 4.5, and 8.0 $\mu$m into the pseudo color map in the left panel of Figure [1](#fig:atlas_example). The three bands can provide information about young stellar objects (YSOs), shocked molecular gas in protostellar outflows, and hot dust or polycyclic aromatic hydrocarbon (PAH) emission, respectively. The angular resolution of the images is smoothed to a uniform value of $2.0$$''$. Some of our source positions have no available Spitzer data, and for these we use ALLWISE data at 3.4, 4.6, and 22.0 $\mu$m (cite: Wright2010WISE; Mainzer2011NOEWISE) instead, which have an angular resolution of 6$.\!\!\ensuremath{''}$1, 6$.\!\!\ensuremath{''}$4, 6$.\!\!\ensuremath{''}$5, and 12$.\!\!\ensuremath{''}$0, respectively.

The submillimeter emission traces the cold and dense gas well. ATLASGAL explores the inner Galactic plane at submillimeter wavelengths ($\sim870$ $\mu$m) with a beam size of 19$.\!\!\ensuremath{''}$2 (cite: Schuller2009ATLASGAL). We use the ATLASGAL data to trace the large scale cold and dense gas which indicates the star formation region, in the white contours on the left panel. If no ATLASGAL data are available, far infrared (FIR) Herschel data from “the Herschel Infrared Galactic Plane Survey” (cite: Traficante2011HiGAL) at 500 $\mu$m is used instead, with a nominal beam size of 34$.\!\!\ensuremath{''}$5 (cite: Traficante2011HiGAL).

The MeerKAT Galactic Plane Survey 1.28 GHz data (cite: Padmanabh2023MeerKAT; Goedhart2023MGPS) provides essential radio information with a resolution of $\sim8\ensuremath{''}$. It is overlaid with yellow contours to indicate the ionized gas from ultra-compact HII (UCHII) and hyper-compact HII (HCHII) regions as well as radio jets.

On a smaller scale, the ATOMS 12m+ACA combined 3 mm continuum data can trace both the dust emission from cold dense cores and/or the free-free emission from UCHII and HCHII regions (cite: Liu2021ATOMS-III). The potential contamination from free-free emission can be estimated using centimeter wavelength data (cite: Avison2015SDC335; Olguin2022SDC335; Xu2023ATOMS-XV).

In Figure [1](#fig:atlas_example), the red circle indicates the field of view ($\sim80$$''$) of the ATOMS continuum data, zooming in on the substructures of $\sim2\ensuremath{''}$ in one of the QUARKS massive clump I13291-6229, as shown in the middle panel. The 3 mm continuum emission of I13291-6229 exhibits a filamentary morphology from the southeast to the northwest. Dense cores identified in (cite: Liu2021ATOMS-III) are marked with red ellipses and ID numbers. As a follow-up, the QUARKS 1.3 mm ACA observations are pointed towards the 3 mm continuum emission region, as marked by the white dashed circles where the 7-m primary beam response is 0.2. In the right panel, the QUARKS ACA data are shown in the background color map and four 1.3 mm sources are identified, where three are identified as solid detection with SNR$>9$ in red and one with SNR$<9$ in yellow.

![](I13291-6229_atlas.pdf)

The QUARKS survey updates the clump distances using the H$^{13}$CO$^+$ lines of the ATOMS survey and the latest model for the rotation curve of the Milky Way (cite: Reid2019Distance), as listed in Table A. of (cite: Liu2023QUARKS). At the bottom right of Figure [1](#fig:atlas_example), both the angular and physical scale bars are shown, with updated clump distance. The complete QUARKS data atlases are presented in the supplementary material.

# Results

## ACA 1.3 mm Continuum Source Catalog

We adopted an automatic source extraction algorithm SEXTRACTOR [^3] (cite: Bertin1996SExtractor) on the ACA 1.3 mm continuum emission maps to extract the 1.3 mm continuum sources. The advantages of SEXTRACTOR in our case are: 1) to subtract the background diffuse emission and rms noise automatically; 2) to support local rms noise input as pixelwise thresholds; 3) to deblend the potentially overlapped sources in crowded fields. The details for the algorithm input parameters are described in Appendix [7](#app:sextractor).

As a result, a total of 207 ACA 1.3 mm continuum sources are extracted from the 139 massive star-forming clumps and the fundamental measurements are summarized in Table [\[tab:measurements\]](#tab:measurements). At least one and at most five sources have been detected in one clump. The field name is listed in column (1) and the continuum source ID which is given in order from North to South is listed in column (2). Hereafter, the format of ACA 1.3 mm continuum source obeys “#Field_ACA#ID”. The ICRS coordinates of the sources are listed in columns (3)–(4). The FWHM of the major and minor axes and the position angle are listed in columns (5)–(7). The integrated flux and peak intensity, which are corrected by primary beam (see details in Section [7](#app:sextractor)), are listed in columns (8)–(9). The signal-to-noise (SNR) ratio, defined as the peak intensity over the local rms, is listed in column (10).

We note that the maximum observed angular size (convolved with the beam) of ACA sources is $\sim14\ensuremath{''}$, which is only half of the maximum recoverable scale in most cases (see Table [\[tab:almaobs\]](#tab:almaobs)). We thus ignore the effects of missing flux in the following analyses.

+:--------------:+:-----:+:-----------:+:-----------:+:--------------------:+:--------------------:+:-----:+:-------------:+:----------------:+:------:+
| Field          | ID    | Equatorial Coordinates    | $\theta_{\rm maj}\times\theta_{\rm min}$    | PA    | $F_{\rm int}$ | $I_{\rm peak}$   | SNR    |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+
|                | ACA   | RA (ICRS)   | DEC (ICRS)  | (arcsec)             | (arcsec)             | (deg) | (Jy)          | (Jy beam$^{-1}$) |        |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+
| 3-4 (r)5-6 (1) | \(2\) | \(3\)       | \(4\)       | \(5\)                | \(6\)                | \(7\) | \(8\)         | \(9\)            | \(10\) |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+
| I08303-4303    | 1     | 08:32:08.7  | -43:13:46.2 | 10.1                 | 7.0                  | 128.6 | 0.811         | 0.347            | 31.8   |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+
| I08448-4343    | 1     | 08:46:35.1  | -43:54:22.6 | 6.8                  | 5.1                  | 64.9  | 0.143         | 0.108            | 11.4   |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+
| I08448-4343    | 2     | 08:46:34.7  | -43:54:33.5 | 7.6                  | 4.1                  | 156.6 | 0.087         | 0.076            | 9.5    |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+
| I08448-4343    | 3     | 08:46:33.4  | -43:54:36.5 | 7.5                  | 4.6                  | 5.9   | 0.171         | 0.126            | 16.5   |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+
| I08448-4343    | 4     | 08:46:32.5  | -43:54:37.1 | 12.2                 | 4.4                  | 5.2   | 0.175         | 0.114            | 16.5   |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+
| I08470-4243    | 1     | 08:48:47.8  | -42:54:26.4 | 10.0                 | 6.0                  | 74.6  | 0.989         | 0.623            | 77.2   |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+
| I09002-4732    | 1     | 09:01:54.3  | -47:44:09.8 | 7.2                  | 5.8                  | 2.6   | 2.675         | 1.720            | 31.2   |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+
| I09018-4816    | 1     | 09:03:33.3  | -48:28:01.0 | 12.1                 | 7.0                  | 96.9  | 1.403         | 0.617            | 40.5   |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+
| I09094-4803    | 1     | 09:11:08.6  | -48:15:44.1 | 5.3                  | 5.0                  | 164.7 | 0.063         | 0.056            | 14.3   |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+
| I09094-4803    | 2     | 09:11:08.3  | -48:15:53.3 | 6.6                  | 5.2                  | 81.4  | 0.093         | 0.073            | 22.3   |
+----------------+-------+-------------+-------------+----------------------+----------------------+-------+---------------+------------------+--------+

The field name and the continuum source ID are listed in columns (1)–(2). The ICRS coordinates of the barycenter are listed in columns (3)–(4). The FWHM of the major and minor axes ($\theta_{\rm maj}$ and $\theta_{\rm min}$), and the position angle (PA) of sources are listed in columns (5)–(7). The integrated flux $F_{\rm int}$ and the peak intensity $I_{\rm peak}$ are listed in columns (8)–(9). The signal-to-noise ratio (SNR) is listed in column (10). The table is available in its entirety in machine-readable form.

## Temperature Estimation from Formaldehyde

Formaldehyde (H$_2$CO) is a suitable spectroscopic tool to derive the kinetic temperature of the molecular gas (cite: Ao2013CMZTemp). For instance, observations throughout the Central Molecular Zone (cite: Ginsburg2016CMZTemp), show that the H$_2$CO emission is spatially widespread and correlated with dust emission. Formaldehyde has two isomeric species, ortho-H$_2$CO (o-H$_2$CO) and para-H$_2$CO (p-H$_2$CO). (cite: Kahane1984OPR) reported that p-H$_2$CO is 1–3 times less abundant than o-H$_2$CO in three low-mass star forming regions. (cite: Mangum1993H2COTemp) reported ortho-to-para ratio of 1.5–3 in the Orion-KL high-mass star-forming region. Therefore, temperature estimation from p-H$_2$CO transition lines minimizes the uncertainties from a high optical depth. For example, (cite: Tang2017H2CO) find that the kinetic temperatures derived from p-H$_2$CO show a good agreement with those of the dust in the Large Magellanic Cloud (LMC), suggesting that the dust and p-H$_2$CO molecules are probing the same (or similar) gas component. More importantly, (cite: Tang2021H2CO) mapped two massive star forming regions in the Large Magellanic Cloud (LMC) using ALMA at a resolution of 0.4 pc and find a consistency in the spatial distribution of the dense gas traced by p-H$_2$CO with that of the 1.3 mm dust. Above all, these studies provide a practical foundation for using the p-H$_2$CO molecule to estimate the dust temperature of the ACA sources.

The QUARKS frequency tunings in SPW1 are designed to cover the p-H$_2$CO transition triplet, i.e., $J_{\rm K_A,K_c} = 3_{0,3} \rightarrow 2_{0,2}$ ($3_{03}$–$2_{02}$) at 218.22219 GHz, $3_{2,2}\rightarrow2_{2,1}$ ($3_{22}$–$2_{21}$) at 218.47563 GHz, and $3_{2,1}\rightarrow2_{2,0}$ ($3_{21}$–$2_{20}$) at 218.76007 GHz. Their upper state energies are 21.0 K, 68.09 K, and 68.11 K, respectively. We extracted spectra from 218.1 to 281.9 GHz in SPW1 to fully cover the frequency range of the H$_2$CO triplet, and perform a five-parameter model using the formaldehyde official model[^4] by PYSPECKIT (cite: Ginsburg2011Pyspeckit; Ginsburg2022Pyspeckit) with a non-LTE RADEX model. The details of the fitting model and results are summarized in Appendix [8](#app:h2co_fit). The derived kinetic temperatures have values between 24 to 180 K with median of 72 K, which are listed in column (3) of Table [\[tab:physical\]](#tab:physical).

![](Temp_fancy.pdf)

A mixture of gas and dust having density over $10^{4.5}$ cm$^{-3}$ due to collisional process (cite: Goldsmith2001Coolant) yields $T_{\rm dust}$ equal to $T_{\rm kin}$, which holds for most of the ACA sources (refer to Section [5.1.2](#nature:dense)). Therefore, in this work, we assume that the dust temperature of ACA source/fragment ($T_{\rm dust,frag}$) equals to the kinetic temperature derived from H$_2$CO triplet line fitting ($T_{\rm kin,H_2CO}$).

Figure [2](#fig:temp) illustrates the relationship between fragment-scale dust temperature $T_{\rm dust,frag}$ and the clump-averaged dust temperature $T_{\rm dust,clump}$ determined through infrared-to-submillimeter SED fitting (cite: Urquhart2018ATLASGAL). All the data points lie above the “isothermal line” ($T_{\rm kin,H_2CO}=T_{\rm dust,clump}$), shown in orange color. This suggests an outward negative temperature gradient, with the inner dense gas traced by H$_2$CO being warmer than the surrounding low-density gas and warmer than gas on average. The temperature gradient serves as an indirect observational evidence of the idea that the ACA sources are active star-forming regions. We note that seven sources with failed fitting (six with a strong self-absorption line profile and one with a weak detection) are assigned with the same value as $T_{\rm dust,clump}$, therefore on the orange line in Figure [2](#fig:temp).

## Physical Parameters of Sources

Assuming that all the emission comes from dust in a single component with $T_{\rm dust}$ and that the dust emission is optically thin, the masses of the sources can be calculated using $$\begin{equation}
\label{eq:mass}
   M_{\rm source} = \mathcal{R}\frac{F_{\rm int} D^2}{\kappa_\nu B_\nu (T_{\rm dust})},
\end{equation}$$ where $F_{\rm int}$ is the measured integrated flux of dust emission, $\mathcal{R}$ is the gas-to-dust mass ratio (assumed to be 100), $D$ is the clump distance, $\kappa_{\nu}$ is the dust opacity per gram of dust, and $B_\nu (T_{\rm dust})$ is the Planck function at a given dust temperature $T_{\rm dust}$. In our case, $\kappa_{\nu}$ is assumed to be 1 cm$^2$ g$^{-1}$ at $\nu\sim230$ GHz which is interpolated from the given table in (cite: O&H1994dust), assuming grains with thin ice mantles and the size distribution given by (cite: MRN1997) and a typical gas density of $10^6$ cm$^{-3}$ in our sample. Substituting $T_{\rm dust}$ assumed above to Equation [\[eq:mass\]](#eq:mass), the ACA source masses are then calculated and listed in the column (4). The major sources of uncertainty in the mass calculation come from the gas-to-dust ratio and the dust opacity. We adopt the uncertainties derived by (cite: Sanhueza2017G28) of 28% for the gas-to-dust ratio and of 23% for the dust opacity, contributing to the $\sim36$% uncertainty of the specific dust opacity. The uncertainty of $F_{\rm int}$ from flux calibration (assumed to be 10%; Yun et al. 2022 [^5]) and the uncertainty of distance (assumed to be 20%) are included. Monte Carlo methods are adopted for uncertainty estimation and $1\sigma$ confidence intervals are given.

ACA sources are characterized by 2D Gaussian-like ellipses with the FWHM of the major and minor axes ($\theta_{\rm maj}$ and $\theta_{\rm min}$), and position angle (PA) listed in columns (5)–(6) of Table [\[tab:measurements\]](#tab:measurements). Following (cite: Rosolowsky2010BGPSII) and (cite: Contreras2013ATLASGAL; Urquhart2014ATLASGAL), the source angular size can be calculated as the geometric mean of the deconvolved major and minor axes. $$\begin{equation}
\label{eq:theta}
    \theta_{\rm dec} = \eta\left[\left(\sigma^2_{\rm maj}-\sigma^2_{\rm bm}\right)\left(\sigma^2_{\rm min}-\sigma^2_{\rm bm}\right)\right]^{1/4},
\end{equation}$$ where $\sigma_{\rm maj}$ and $\sigma_{\rm min}$ are calculated from $\theta_{\rm maj}/\sqrt{8\ln2}$ and $\theta_{\rm min}/\sqrt{8\ln2}$ respectively. $\sigma_{\rm bm}$ is the averaged dispersion size of the beam (i.e., $\sqrt{\theta_{\rm bmaj}\theta_{\rm bmin}/(8\ln2)}$ where $\theta_{\rm bmj}$ and $\theta_{\rm bmin}$ are the FWHM of the major and minor axis of the beam). $\eta$ is a factor that relates the size of the emission distribution dispersion to the determined angular radius of the object. $\eta=2.4$, the median value derived for a range of models consisting of a spherical emissivity distribution (cite: Rosolowsky2010BGPSII), is adopted here. Therefore, the physical size can be calculated directly using $R_{\rm dec} = \theta_{\rm dec}\times D$, as shown in column (5) of Table [\[tab:physical\]](#tab:physical).

The source peak column density is estimated from $$\begin{equation}
    N^{\rm peak}_{\scriptscriptstyle\rm H_2} = \mathcal{R} \frac{I_{\rm peak}}{\Omega\mu_{\scriptscriptstyle\rm H_2} m_{\scriptscriptstyle\rm H}\kappa_{\nu}B_{\nu}(T_{\rm dust})},
\end{equation}$$ where $I_{\rm peak}$ is the measured peak flux of source within the beam solid angle $\Omega$.

The surface density averaged by the source can be calculated by $\Sigma=M_{\rm source}/(\pi R^2_{\rm dec})$. The source-averaged number density, $n_{\rm H_2}$, is then calculated by assuming a spherical source, $$\begin{equation}
 \label{eq:volume_density}
    n_{\scriptscriptstyle\rm H_2} = \frac{M_{\rm source}}{(4/3) \pi \mu_{\scriptscriptstyle\rm H_2} m_{\scriptscriptstyle\rm H}R_{\rm dec}^3},
\end{equation}$$ where $\mu_{\scriptscriptstyle\rm H_2}$ is the molecular weight per hydrogen molecule and $m_{\rm H}$ is the mass of a hydrogen atom. Throughout the paper, we adopt the molecular weight per hydrogen molecule $\mu_{\scriptscriptstyle\rm H_2} = 2.81$ (cite: Evans2022SlowSF). The calculated peak column density and the average surface density and volume densities of the source are given in columns (6)–(8) of Table [\[tab:physical\]](#tab:physical).

The velocity dispersion contributed by the thermal motion of H$_2$CO molecules is given by $$\begin{equation}
 \label{eq:sigmath_h2co}
    \sigma_{\scriptscriptstyle\rm th,H_2CO} = \sqrt{\frac{k_B T_{\rm kin}}{m_{\rm H_2CO}}},
\end{equation}$$ where $T_{\rm kin}$ is kinetic temperature derived in Section [4.2](#results:temperature) and $m_{\rm H_2CO}$ is the molecular weight 30 times $m_H$. With $\sigma_{\rm H_2CO}$ deduced from the observed velocity dispersion $\sigma_{\rm obs}$, the non-thermal velocity dispersion is derived as $$\begin{equation}
 \label{eq:sigmant}
    \sigma_{\rm nt} = \sqrt{\sigma^2_{\rm obs}-\Delta_{\rm chan}^2/(2\sqrt{2\ln 2})^2-\sigma^2_{\rm th,H_2CO}},
\end{equation}$$ where $\Delta_{\rm chan}=1.34$ km s$^{-1}$ is the channel width. We check that 30 sources with line width $>7$ km s$^{-1}$ are strongly influenced by outflow wings (see Appendix [8](#app:h2co_fit)), and set an averaged observed velocity dispersion of $1.66$ km s$^{-1}$.

The gas sound speed ($c_s$) or thermal velocity dispersion ($\sigma_{\rm th}$) is given by, $$\begin{equation}
 \label{eq:sigmath}
    c_s = \sigma_{\rm th} = \sqrt{\frac{k_B T_{\rm kin}}{\mu_{p} m_{\scriptscriptstyle\rm H}}},
\end{equation}$$ where $\mu_{p}=2.37$ for a mean molecular weight per free particle (cite: Kauffmann2008dust). The three-dimensional (3D) Mach number is defined as, $$\begin{equation}
 \label{eq:Mach}
    \mathcal{M} = \frac{\sqrt{3}\sigma_{\rm nt}}{c_s}.
\end{equation}$$ The sound speed, non-thermal velocity dispersion and Mach number are listed in columns (9)–(11) of Table [\[tab:physical\]](#tab:physical).

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Field | ID | $T_{\rm kin}$ | $M_{\rm source}$ | $R_{\rm dec}$ | $N^{\rm peak}_{\rm H_2}$ | $\Sigma$ | $n_{\rm H_2}$ | $c_s$ | $\sigma_{\rm nt}$ | $\mathcal{M}$ |
|  | ACA | \(K\) | ($M_\odot$) | (pc) | (cm$^{-2}$) | (g cm$^{-2}$) | (cm$^{-3}$) | (km s$^{-1}$) | (km s$^{-1}$) |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) | \(9\) | \(10\) | \(11\) |
| I13291-6229 | 1 | 32.8(6.3) | 2.7(1.4) | – | 1.7(0.7)$\times10^{22}$ | – | – | 0.34 | 1 | 3.0 |
| I13291-6229 | 2 | 74.8(1.4) | 8.1(3.5) | 0.054 | 3.3(1.2)$\times10^{22}$ | 0.18(0.08) | 1.8(0.8)$\times10^{5}$ | 0.51 | 1.4 | 2.7 |
| I13291-6229 | 3 | 56.6(0.7) | 3.5(1.5) | 0.032 | 1.8(0.7)$\times10^{22}$ | 0.23(0.10) | 3.7(1.6)$\times10^{5}$ | 0.44 | 0.93 | 2.1 |
| I13291-6229 | 4 | 66.6(1.8) | 2.3(1.0) | – | 1.1(0.4)$\times10^{22}$ | – | – | 0.48 | – | – |
| I13291-6249 | 1 | 87.4(3.4) | 281.3(122.0) | 0.3 | 8.9(3.3)$\times10^{22}$ | 0.21(0.09) | 3.6(1.6)$\times10^{4}$ | 0.55 | 1.9 | 3.5 |
| I13295-6152 | 1 | 44.5(0.6) | 26.3(11.3) | 0.12 | 5.4(2.0)$\times10^{22}$ | 0.13(0.05) | 5.6(2.4)$\times10^{4}$ | 0.39 | 0.96 | 2.5 |
| I13471-6120 | 1 | 78.0(0.9) | 119.7(51.6) | 0.048 | 2.2(0.8)$\times10^{23}$ | 3.51(1.51) | 3.8(1.6)$\times10^{6}$ | 0.52 | 1.5 | 2.8 |
| I13484-6100 | 1 | 73.0(14.5) | 119.6(61.4) | 0.1 | 9.9(3.9)$\times10^{22}$ | 0.74(0.38) | 3.7(1.9)$\times10^{5}$ | 0.5 | 2.5 | 5.0 |
| I14013-6105 | 1 | 98.0(2.5) | 83.1(35.9) | 0.11 | 1.2(0.5)$\times10^{23}$ | 0.47(0.20) | 2.2(1.0)$\times10^{5}$ | 0.58 | 1.5 | 2.6 |
| I14050-6056 | 1 | 120.0(6.9) | 18.4(8.0) | 0.11 | 3.5(1.3)$\times10^{22}$ | 0.10(0.04) | 4.9(2.1)$\times10^{4}$ | 0.65 | 1.5 | 2.3 |

Field name and the continuum source ID are listed in columns (1)–(2). Kinetic temperature is listed in column (3). Source mass ($M_{\rm source}$), deconvolved size ($R_{\rm dec}$), peak column density ($N^{\rm peak}_{\rm H_2}$), surface density ($\Sigma$), and volume density ($n_{\rm H_2}$) are listed in columns (4)–(8). The uncertainties of these parameters (except for $R_{\rm dec}$) are included in parentheses. Unresolved sources have ‘–’ in columns (5), (7) and (8). Sound speed ($c_s$), non-thermal velocity dispersion ($\sigma_{\rm nt}$), and Mach number ($\mathcal{M}$) are listed in columns (9)–(11). If H$_2$CO fitting fails, then mark with ‘–’ in columns (10)–(11). Only a part of the table is shown and the complete table is available in its entirety in machine-readable form.

# Discussion

## Nature of ACA Source

![](stats.pdf)

### Massive star-forming regions with supersonic turbulence

Six parameters from Table [\[tab:physical\]](#tab:physical), including kinetic temperature ($T_{\rm kin}$), source mass ($M_{\rm source}$), source size ($R_{\rm dec}$), volume density ($n_{\rm H_2}$), surface density ($\Sigma$) and Mach number ($\mathcal{M}$) are shown in histogram form in Figure [3](#fig:stats).

In panel (a), $T_{\rm kin}$ ranges from $\sim20$ to $\sim180$ K, with a mean and median of $\sim$68 K. More than 97% sources have a temperature larger than 30 K, indicating their protostellar nature. With a higher resolution of 2$''$, (cite: Qin2022ATOMS-VIII) identified 60 hot molecular cores with gas temperature $>100$ K, as the heating sources of massive clumps. As shown in Figure [2](#fig:temp), the temperatures of ACA sources are all larger than those of clumps, indicating that the ACA sources are heating their parent massive clumps. Theoretically, a massive protostellar embryo heats and eventually ionizes the gas of its surrounding envelope, creating an HII region that develops by expanding within the cloud (cite: Motte2018Review). Therefore, the embedded heating sources are expected, indicating ACA sources should be heating their parent massive clumps.

Panel (b) of Figure [3](#fig:stats) shows the mass distribution, with 16 and 84 percentile values of 6 and 160 $M_\odot$. Assuming monolithic collapse and that only a single star forms, 120 ACA sources (58%) are massive enough to form a massive star ($>8$ $M_\odot$) with a core-to-star efficiency $\sim30$% (cite: Matzner2000Efficiency; Federrath2012SFR). However, the ACA sources have fragmented and are forming protoclusters (see Section [5.1.3](#nature:ensemble)). If assuming that a cluster will form inside the ACA sources and using the empirical relation from star clusters given by (cite: Larson2003IMF), $$\begin{equation}
 \label{eq:cluster}
    \left(\frac{m_{\rm max}}{M_\odot}\right) = 1.2\left(\frac{M_{\rm cluster}}{M_{\odot}}\right)^{0.45},
\end{equation}$$ where $m_{\rm max}$ and $M_{\rm cluster}$ are the maximum mass and the total mass of the stellar cluster, we find that 72 out of 207 sources can form massive stars if only mass *in situ* participates in star formation. From panel (c), we observe that nearly all the sources possess surface densities ($\Sigma$) exceeding 0.05 g cm$^{-2}$, which aligns with the empirical threshold for high-mass star formation as suggested by (cite: Urquhart2014ATLASGAL). A total of 35 ACA sources exceed the more stringent surface density threshold of 1 g cm$^{-2}$ proposed by (cite: Krumholz2008Threshold). But it’s essential to bear in mind that these surface density thresholds can be scale-dependent. For example, if massive clumps have a density profile of $\rho\propto R^{-2}$, then the enclosed mass scales with $M\propto R$, resulting in $\Sigma\propto R^{-1}$. If we adjust for this relation, the surface density threshold for massive star formation should be approximately ten times higher at the scale of ACA sources. But in a turbulent-dominated clump, one argues that cores have a column density comparable to that of the clump as a whole, with only $\Sigma_{\rm core}/\Sigma_{\rm cl}=1.22$.

Core-scale (0.1 pc and $n>10^5$ cm$^{-3}$) infall motions have been statistically studied (cite: WuJ2003Infall; WuY2007Infall; Contreras2018G331; Xu2023JCMTInfall) and filamentary accretion flows are resolved in high-resolution observations (cite: Peretto2013SDC335; Liu2016NH3; Yuan2018G22; Lu2018Filament; Chen2019G14; Sanhueza2021I18089; Redaelli2022AG14; Xu2023ATOMS-XV; Yang2023G310). Hence, the identified ACA sources are likely to continue to accumulate mass throughout their evolution, achieving further growth of the core mass and enhancement of the surface density (cite: Liu2023HFS; Xu2024ASSEMBLE). Using H$^{13}$CO$^+$ (1–0), (cite: Zhou2022HFS) identified 68 hub-filament systems with clear velocity gradients in the ATOMS survey. In the context of massive cluster formation, these hub-filament structures play a crucial role in supporting gas accretion towards dense cores where massive stars form.

In panel (d), the Mach numbers $\mathcal{M}$ at the scale of the ACA sources are mostly greater than 2. We note that those sources with strong line wings are excluded when analyzing the line widths because of the widening effects of the H$_2$CO outflows as reported in (cite: Izumi2023ASHES-X). Assuming that turbulence dominates the non-thermal motion, the $\mathcal{M}$ values suggest the prevalence of supersonic turbulence, which aligns with what has been found earlier in several cases (cite: Zhang2009G28; Wang2014Snake). As a result, the supersonic turbulence can suppress thermal Jeans fragmentation (cite: Sanhueza2019ASHES) and enhances mass accretion onto central massive protostars, which is proposed in the model by (cite: McKee2003TC).

### Fragments with self-similar gravitational collapse

![](MRrelation.pdf)

According to panels (e) and (f) in Figure [3](#fig:stats), the ACA sources exhibit sizes ranging from 0.02 to 0.4 pc, volume densities exceeding $10^4$ cm$^{-3}$, with 107 of them surpassing $10^5$ cm$^{-3}$. The median volume density of the ACA sources is $1.6\times10^5$ cm$^{-3}$, which is 20 times larger than that of the clumps. This suggests that these ACA sources are the condensed gas fragments at a subclump scale. Therefore, the ACA sources serve as sub-clump structures and are also called (ACA) fragments in the following discussion.

We collect the QUARKS clump mass $M_{\rm clump}$ and radius $R_{\rm clump}$ from (cite: Liu2023QUARKS) and plot them (orange stars) with ACA fragments (blue pentagons) in Figure [4](#fig:MR). The source extraction algorithm of the clumps is the same as we do for ACA fragments, so there is no systematic bias due to the methodology in the following discussion. The mass versus radius ($M$–$R$) diagram can be used to study mass concentration at different scales. Sources that shares the same density profile should exhibit scaling relations with the same power law index in the $M$–$R$ diagram.

We perform a linear regression on the $M$–$R$ diagram for the QUARKS clumps, resulting in a correlation of $M\propto R^{1.8}$ (shown as orange line) with correlation coefficient of 0.91 and $1\sigma$ data scatter of 0.26. Assuming that all the QUARKS clumps share a similar density profile, then the power-law index corresponds to the expectation of the turbulent-support model proposed by (cite: Li2017Isolation). In their model, energy dissipation rate of external turbulence balances with that of internal virialized turbulence, resulting in a mass concentration relationship described by $M\propto R^{1.67}$.

The agreement between observations and theory suggests that the QUARKS massive clumps are currently in a transitional phase. In a turbulence-dominated cloud, a shallower density profile following $\rho\propto R^{-1}$ (cite: BT2012) and a steeper mass concentration of $M(<r)\propto R^{2}$ are expected. In contrast, in a dense structure dominated by gravity and the system reaches a quasi-stationary stage (cite: Xu2023ATOMS-XV) after relaxation processes, the density profile usually adheres to $\rho\propto R^{-2}$ (cite: Li2018Selfsimilar), with the mass concentration described by $M(<R)\propto R$.

As shown in blue pentagons of Figure [4](#fig:MR), the ACA fragments show a notable deviation from clump (orange color) at scales $\leq0.1$ pc, suggesting a different mass-radius relationship. These fragments have a higher mass for a given radius compared to the turbulent-supported model. A linear regression applied to the ACA fragments reveals a correlation of $M\propto R^{1.1}$, represented by a blue line, suggesting a power-law index close to 1. This scaling aligns with a density profile of $\rho\propto R^{-2}$, indicative of a scale-free gravitational collapse in a self-similar fashion (cite: Li2018Selfsimilar). In Section [5.3.1](#DGF:hierarchy), self-similarity of ACA fragments will be proposed in another manner.

The transition of mass concentration from several parsecs to tenths parsec is highly consistent with what has been found by (cite: Peretto2023Decouple), where star cluster progenitors are reported to be dynamically decoupled from their parent molecular clouds, exhibiting steeper density profiles $\rho\propto R^{-2}$ and flat velocity dispersion profiles $\sigma\propto R^0$, clearly departing from Larson’s relations. Similar scale-dependent gas dynamics have been found in several cases of multi-scale studies (cite: Liu2022ATOMS-IX; Saha2022ATOMS-XII), where gravity-driven gas motion takes over turbulence. In the QUARKS sample, it would be of great interest to investigate the behaviour of $M$–$R$ down to dense core scale as a follow-up work, similar to what has been done in infrared dark clouds (cite: Li2023ASHES).

### Protocluster ensembles

As shown in high-resolution studies by (cite: Xu2024ASSEMBLE) and (cite: Liu2023QUARKS), the QUARKS ACA 1.3 mm continuum sources contain protoclusters with a large number of dense cores, which are embedded in the parent ACA sources (cite: Zhang2021HMSCs). To further demonstrate this ubiquity, we performed a spatial cross-match between the ATOMS 3 mm continuum dense cores by (cite: Liu2021ATOMS-III) and the QUARKS ACA 1.3 mm continuum sources.

As a result, we have identified a total of 301 “QUARKS-ATOMS links” (links hereafter), as defined by Eq.[\[eq:ellipse\]](#eq:ellipse) discussed in Appendix [9](#app:crossmatch) and listed them in Table [\[tab:crossmatch\]](#tab:crossmatch). The remaining 128 ATOMS dense cores, without any associated ACA sources, are referred to as “field sources”. The presence of field sources can be attributed to the generally higher mass sensitivity of the ATOMS data compared to the QUARKS ACA data. Given a distance of 3 kpc and dust temperature of 20 K, typical ATOMS and QUARKS 7-m continuum sensitivities of 0.2 and 15 mJy give sensitivity limits of 1.5 and 3 $M_\odot$, respectively. Compared to 1.3 mm, the 3 mm continuum emission can be contaminated by free-free emission more easily and diffuse 3 mm emission cannot be seen in the ACA 1.3 mm continuum images.

There are 86 ACA sources (42%) with more than one ATOMS dense cores, and among them, 25 have three or more ATOMS dense cores, indicating the presence of substructures. Consequently, the detected QUARKS ACA sources are likely to be ensembles of protoclusters in nature. However, there are 95 ACA sources associated with single ATOMS dense cores, possibly due to limited resolution. Above all, the analyses at the scale of ACA sources provide a global view of massive protoclusters.

## Correlation Between Clumps and Fragments

As discussed in Section [5.1.2](#nature:dense), the ACA 1.3 mm continuum sources trace dense fragments ($n_{\rm H_2}>10^4$ cm$^{-3}$) within massive clumps. Figure [5](#fig:Maca_Mclump) presents maximum mass of ACA sources ($M_{\rm source,max}$) and the total mass of ACA sources ($M_{\rm source,total}$) versus their natal clump mass ($M_{\rm clump}$). These are shown with blue stars and orange triangles, respectively. Comparing the two panels, we find no clear difference between $M_{\rm source,max}$ and $M_{\rm source,total}$ in most cases, because the most massive ACA sources are dominated by mass within clumps.

Linear regression is used to correlate $M_{\rm source,max}$ with $M_{\rm clump}$. The derived scaling relation is $\log (M_{\rm source,max}/M_{\odot}) = 0.96 (\log M_{\rm clump}/M_{\odot}) - 1.33$ as indicated by blue line, with the correlation coefficient of 0.82 and 1$\sigma$ data scatter of 0.34 dex. To examine the distance effects on the mass correlation, we further perform linear regression in narrower distance bins (see Appendix [10](#app:dist)).

Consistent with our results, (cite: Lin2019SABOCA) find $M_{\rm source,max}\propto M_{\rm clump}^{0.96}$ in the 350 $\mu$m observations of 204 ATLASGAL clumps. Besides, (cite: Traficante2023SQUALO-I) also find a scaling relation of $M_{\rm source,max}\propto M_{\rm clump}^{1.02}$ in an ALMA survey of 13 massive clumps. However, the quasi-linear correlation could be a result of an evolutionary process, as it may not be evident in the early stages of massive clumps. For example, samples of massive starless clumps have shown a significantly small amount of mass stored in fragments (cite: Sanhueza2019ASHES; Svoboda2019HMSC; Morii2023ASHES), consistent with the idea that initial fragmentation in massive clumps are Jeans-like and producing low-mass cores. As a clump evolves, the continuous mass accretion feeds the most massive core (cite: Xu2023ATOMS-XV) and the mass correlation builds up (cite: Xu2024ASSEMBLE). The QUARKS sample predominantly covers mid- and late-stage massive star-forming clumps, characterized by luminosity-to-mass ratio range of 4–460 $L_{\odot}/M_{\odot}$ and a median value of 35 $L_{\odot}/M_{\odot}$, so the mass correlation is expected.

As indicated by orange line in the right panel of Figure [5](#fig:Maca_Mclump), linear regression gives $\log (M_{\rm source,total}/M_\odot) = 0.94 (\log M_{\rm clump}/M_{\odot}) - 1.22$. Intriguingly, the correlation is even tighter with coefficient of 0.85 and 1$\sigma$ data scatter of 0.30 dex, compared to the that of $M_{\rm source,max}$–$M_{\rm clump}$. The tightening correlation indicates that total ACA source (dense gas) mass could be a physical value that is more directly correlated with clump mass. In other words, the $M_{\rm source,max}$–$M_{\rm clump}$ relation could be a combined result of $M_{\rm source,total}$–$M_{\rm clump}$ and a mass function which correlates $M_{\rm source,total}$ with $M_{\rm source,max}$ (cite: Bonnell2004Simulation; Weidner2013Cluster).

![](Maca_Mclump.pdf)

## Dense Gas Fraction and Its Assembly

Star formation takes place in dense molecular gas. Here we take the ACA 1.3 mm continuum sources as “dense gas” relative to the total clump gas, and define the dense gas fraction (DGF), $$\begin{equation}
    \mathrm{DGF} \equiv \frac{M_{\rm dense}}{M_{\rm clump}},
\end{equation}$$ where $M_{\rm dense}=\sum\limits^{\rm \in clump} M_{\rm source}$ is the total ACA source mass within the clump. (cite: Urquhart2018ATLASGAL) performed the photometry from near- to far-infrared data of these massive clumps, by which the spectral energy distribution (SED) are fitted. By this method, the clump mass es, $M_{\rm clump}$, were derived and are scaled with the updated distances in this work.

As discussed in Section [5.2](#discuss:corr), the linearity in Figure [5](#fig:Maca_Mclump) indicates a constant DGF within the QUARKS sample, giving a value directly by its intercept of $10^{-1.22}$, i.e., 6%. In an alternative definition of core formation efficiency (CFE), a highly consistent median value of 6% is also reported in (cite: Traficante2023SQUALO-I), evidently consistent with what has been found here.

Although showing invariance with $M_{\rm clump}$, DGF still has a scatter of 1–10%. To further explore the origins of scatter, DGF versus clump radius ($R_{\rm clump}$) and luminosity-to-mass ratio ($L/M$) diagrams are explored in Section [5.3.1](#DGF:hierarchy) and Section [5.3.2](#DGF:growth), respectively

### Self-similarity in protocluster formation

![](DGF_Rclump.pdf)

As shown in the panel (a) of Figure [6](#fig:DGF_Rclump), the blue hexagons indicate the probability distributions of data points in the DGF versus clump radius diagram. The median DGF over $R_{\rm clump}$ bin, as indicated by the blue stars connected by line, shows no discernible systematic variations with $R_{\rm clump}$. Linear regression shows a weak correlation with a Spearman correlation coefficient of -0.12, indicating dense gas mass remains nearly constant relative to the clump mass across different scales from several tenths of parsec to several parsec. It’s worth noting that there are some clumps with very low DGF ($<$1%), indicating that QUARKS field of views are not large enough to cover all the dense gas in clumps with large sizes. However, the coverage-limit effect can be neglected in our sample because the QUARKS pointings are biased to the dense regions according to the ATOMS survey.

If we consider the ACA sources as what has been observed at various scales, that is, from parsec-scale clumps to sub-parsec-scale cores, then the multi-scale invariant DGF suggests that the gas tends to condense or fragment into dense structure with some constant ratio in a hierarchical system. It implies a self-similar fragmentation or collapsing mode in protocluster formation, as proposed in some case studies (cite: Wang2011G28; Wang2014Snake). More importantly, (cite: Dib2023Protocluster) performed delta-variance spectrum analysis of 15 ALMA-IMF cloud structures (cite: Motte2022ALMA-IMF-1) and discovered a self-similar regime $\lesssim$ 0.03–0.3 pc. Referring to panel (a) of Figure [6](#fig:DGF_Rclump), one can find it highly consistent with the sizes of the ACA sources, representing the most compact clumps within the protocluster forming clouds (cite: Dib2023Protocluster). Therefore, our result favors the self-similarity of density structure in massive protoclusters in a dependent way.

We also retrieved 39 ACA 1.3 mm continuum images from the “ALMA Survey of 70 $\mu$m Dark High-mass Clumps in Early Stages” (cite: Sanhueza2019ASHES; Morii2023ASHES). It is worth noting that the ASHES observations adopted a mosaic mode with larger fields of view than the QUARKS. To maintain consistency, we cropped the ASHES continuum images to the same size as the QUARKS. After adopting the same source extraction algorithm and mass calculation, we derive the DGF of 39 ASHES clumps which are shown with gray hexagons in the panel (b) of Figure [6](#fig:DGF_Rclump). The gray stars indicate the median values in corresponding parameter bins. Similarly, the ASHES sample also shows an invariance of DGF with size. Therefore, the self-similarity works in both early and late stages of the evolution of massive protoclusters.

### Dense gas grows with evolution

![](DGF_LtoM.pdf)

In Figure [6](#fig:DGF_Rclump), an intriguing feature is a systematically one-time larger DGF in the QUARKS than that in the ASHES clumps, and the DGF difference seems to be invariant with the clump size. Therefore, we refer to the evolutionary explanation of the DGF difference between two samples. Theoretically, a high-mass star grows in mass during its formation process, so its luminosity should increase. The ratio of bolometric luminosity to envelope mass $L/M$, can thus be used to indicate the evolutionary stage (cite: Sridharan2002HMPOs; Elia2017HiGAL). In Figure [7](#fig:DGF_LtoM), the DGF is plotted against $L/M$, where the gray and blue hexagons represent the probability distribution of data points of the ASHES and the QUARKS sample, respectively. The orange stars connected by dashed show the DGF median values of the QUARKS+ASHES combined sample in the $L/M$ bins from 0.04 to 400 $L_\odot/M_\odot$, spanning four orders of magnitude. To demonstrate the evolutionary trend, a linear regression is performed on the data points from the combined sample, resulting in a correlation of $\log({\rm DGF}) = 0.13\log{(L/M)}-1.59$, depicted by the orange solid line. The correlation yields a Spearman correlation coefficient of $R_s=0.41$ and an associated $p$ value of $2.9\times10^{-8}$, indicating an evident increase in the mass fraction of the dense part of the clump as it evolves.

We incorporate the DGF results from an ACA 0.87 mm survey (cite: Csengeri2017ACA) and the "Star formation in QUiescent And Luminous Objects" (SQUALO) project (cite: Traficante2023SQUALO-I), contributing 30 green and 13 orange data points in Figure [7](#fig:DGF_LtoM). To keep consistency, all the clump masses are retrieved from (cite: Urquhart2018ATLASGAL) in the following discussion. While the $L/M$ of the sample spans a similar range to ours, the DGF is systematically larger. This discrepancy arises because adopted a constant temperature $T_{\rm dust}=25$ K throughout the sample, which is systematically lower than what we used in Eq. [\[eq:mass\]](#eq:mass), resulting in a higher mass. improved this method by categorizing the sample into three evolutionary bins and estimating temperatures of 20, 30, and 40 K, respectively. Despite the limited sample size, the wide range of $L_\odot/M_\odot$ in indicates an increasing trend similar to the results of the QUARKS. As a result, two independent data sets mutually verify a dense mass growth in massive star-forming clumps as they evolve.

The methods in both and give a lower temperature compared to ours. According to Equation [\[eq:mass\]](#eq:mass), a lower temperature leads to a higher mass for a given flux. Therefore, we adopt the above temperature estimation methods to our sample, the resulting DGF will be even larger and the increasing trend will become more significant.

The mass growth of dense cores is widely found during the evolution of massive star-forming clumps (cite: Anderson2021HFS; Traficante2023SQUALO-I; Liu2023HFS; Li2023ASHES; Xu2024ASSEMBLE). Very recently, the ASHES team has found an increase in the mass dynamic range with respect to the protostellar core fraction, serving as a proxy for evolutionary stages (cite: Morii2024). Our work, encompassing a significantly larger sample with a broad range of evolutionary stages, substantiates the continuous growth of dense mass over time. Overall, recent ALMA studies portray a dynamic scenario wherein dense gas accumulates throughout the evolutionary process.

We note that the evolution-dependent DGF cannot explain the total scatter. The wide range of DGFs among the QUARKS samples can also arise from the dynamic balance between gas depletion/stellar feedback and gas infall. Specifically, gas infall and accretion processes function to concentrate the dense gas, while star formation depletes the dense gas. Stellar feedback mechanisms, such as winds and outflows, play a dual role by releasing gas back to the parent clump and preventing further gas accretion. But for the surrounding embedded dense gas structures, their kinematic properties may be less influenced by feedback from the most evolved stars in clumps (cite: Zhou2023Feedback). At any rate, a systematic investigations into gas kinematics and energetics have the potential to unveil dynamic effects on DGF and elucidate the origin of the scatter in DGF values.

## Limited Fragmentation

ACA sources are fragments from the clump scale. The facts that the mean number of fragments per clump is $\bar N_{\rm frag}\sim1.5$ and that 93 clumps have only one fragment, both suggest limited fragmentation, which is consistent with what has been found in another ACA survey by .

discussed the possibility that global collapse at the clump scale could explain the excessive mass of the subclump reservoir (cite: Schneider2010DR21; Peretto2013SDC335; Xu2023ATOMS-XV). This concept implies that the entire clump is involved in a dynamic process, wherein fragments and low-density gas experience global collapse. Equilibrium may never be reached at subclump scales, which aligns with the limited fragmentation observed. observed that the majority of the clumps are likely not in virial equilibrium, suggesting collapse on the clump scale. Furthermore, continuous mass accretion beyond the clump to the core-scale feed could fuel the formation of the protocluster (cite: Avison2021SDC335; Xu2023ATOMS-XV; Yang2023G310; Xu2023JCMTInfall). In this scenario, an increase in the number of fragments with time and a Jeans-like fragmentation to develop in more evolved stages are expected (cite: Palau2015Fragmentation), and appear to be in conflict with our observed evolution-independent limited fragmentation. However, the conflict can be reconciled, because the QUARKS ACA observations have limited mass sensitivity of $\gtrsim3$ $M_\odot$, at a temperature of 20 K and distance of 4 kpc and limited spatial resolution of $\gtrsim0.1$ pc. Therefore, those small low-mass fragments cannot be effectively resolved even if they exist. (cite: Liu2023QUARKS) show an example of Sgr B2(M) in the QUARKS high-resolution ($\sim0.3\ensuremath{''}$) data. Compared to the only detection in the ACA data in I17441-2822, (cite: Liu2023QUARKS) identified more than 30 spatially associated cores with the ACA 1.3 mm source and up to 93 cores in the entire cluster of cores.

Nevertheless, we propose another possibility where ACA fragments are the products of turbulent Jeans fragmentation from the natal clump. Although the thermal Jeans mass in massive clumps is as low as several $M_\odot$, at clump density of $\bar n_{\rm cl}\sim5\times10^{4-5}$ cm$^{-3}$ and kinetic temperature of $T_{\rm kin}=20\,K$, turbulent Jeans fragmentation favors more massive fragment, larger Jeans length, and therefore less fragments in a clump.

# Summary

The QUARKS survey, standing for ‘Querying Underlying mechanisms of massive star formation with ALMA-Resolved gas Kinematics and Structures’, is observing 139 massive gas clumps at ALMA Band 6 ($\lambda\sim$ 1.3 mm). This paper introduces the Atacama Compact Array (ACA) 7-m data of the QUARKS survey, describing the ACA observations and data reduction. Combining multi-wavelength data, we provide the first edition of QUARKS atlas, offering insights into the multiscale and multiphase interstellar medium (ISM) in high-mass star formation.

Leveraging the QUARKS ACA data, we construct the ACA 1.3 mm continuum source catalog with 207 sources. At least one source and up to five sources are found in one clump. Three source-averaged formaldehyde transition lines p-H$_2$CO (3–2) are fitted using non-LTE radiative transfer model, to obtain the gas kinetic temperature and line width. Based on the geometric and flux measurements of the ACA sources, and assuming that gas temperature equals the dust temperature, physical parameters including mass and surface/volume densities are derived. The thermal and non-thermal dispersion, as well as the Mach number, are also calculated from fitted p-H$_2$CO (3–2) line width.

Statistically speaking, the nature of ACA sources is massive gravity-dominated fragments with at the subclump scale, with supersonic turbulence and possibly embedded star-forming protocluster. A quasi-linear correlation between clump mass and ACA source mass is found, which can be explained by the dynamic coevolution between clump and core in a late stage. The dense gas fraction (DGF) is defined as total ACA source mass over the clump mass, and is found to be about 6%, although with a wide scatter of 1–10%. If we consider the massive clump sample as what has been observed at various scales, then the size-independent DGF indicates that the gas conversion efficiency at each scale level remains constant in a hierarchical system, implying a self-similar fragmentation or collapsing mode in protocluster formation. With the data across four orders of magnitude of luminosity-to-mass ratio, we find a significantly increasing trend of DGF with clump evolution. The fragmentation on the subclump scale is limited and the reasons could be that equilibrium may never be reached at subclump scale and massive clumps are undergoing a global collapse.

# Acknowledgements

We thank the anonymous referee for helpful comments.

This work has been supported by the National Science Foundation of China (12033005), the National Key R&D Program of China (No. 2022YFA1603102), the China Manned Space Project (CMS-CSST-2021-A09, CMS-CSST-2021-B06), and the China-Chile Joint Research Fund (CCJRF No. 2211). CCJRF is provided by Chinese Academy of Sciences South America Center for Astronomy (CASSACA) and established by National Astronomical Observatories, Chinese Academy of Sciences (NAOC) and Chilean Astronomy Society (SOCHIAS) to support China-Chile collaborations in astronomy. We acknowledge support from the Tianchi Talent Program of Xinjiang Uygur Autonomous Region. This research was carried out in part at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with the National Aeronautics and Space Administration (80NM0018D0004). PS was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI Number JP22H01271 and JP23H01221) of JSPS. AS, DM, GG, and LB gratefully acknowledge support by ANID Basal project FB210003. MJ acknowledges the support of the Research Council of Finland Grant No. 348342. K.M is supported by a Grants-in-Aid for the the JSPS Fellows (KAKENHI Number 22J21529). Data analysis was in part carried out on the Multi-wavelength Data Analysis System operated by the Astronomy Data Center (ADC), National Astronomical Observatory of Japan.

This paper uses the following ALMA data: ADS/JAO.ALMA#2019.1.00685.S and 2021.1.00095.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

The MeerKAT telescope is operated by the South African Radio Astronomy Observatory, which is a facility of the National Research Foundation, an agency of the Department of Science and Innovation.

*Software*. This research uses ASTROPY, a community-developed core Python package for Astronomy (cite: Astropy2013; Astropy2018; Astropy2022). This research has used the program SEXTRACTOR, which builds a catalog of objects from an astronomical image (cite: Bertin1996SExtractor). This research has used Python-based package PYSPECKIT to fit spectral lines (cite: Ginsburg2011Pyspeckit; Ginsburg2022Pyspeckit). This research has used RADEX, a computer program for fast non-LTE analysis of interstellar line spectra (cite: van2007RADEX).

# Source Extraction

For each field, we initially generated the background and rms map from the original continuum map without applying primary beam correction (`unpbcor`). Within each unit of boxes, whose size is equivalent to the maximum recoverable scale, we performed iterative clipping of the local background histogram until convergence was achieved at $\pm3\sigma$ around its median (cite: Bertin1996SExtractor). The background subtracted continuum map, together with the corresponding rms map, was then used as input for SEXTRACTOR. Before the program runs, $\texttt{nthresh}=4$ is set to mask the low SNR (`nthresh`$\times$local rms) pixels. During the extraction procedure, the deblending parameters, that is, the number of thresholds for the deblending, and the deblending contrast are set $\texttt{deblend\_nthresh}=512$ and $\texttt{deblend\_cont}=10^{-5}$. To ensure that the extraction focused on genuine sources rather than spurious features or cleaning artifacts, we set the parameter controlling the minimum pixel count for a source, `minarea`, to match the effective beam size.

Due to the Gaussian-like primary beam response, the real flux of source should be corrected by primary beam correction (`pbcor`). So, the `pb` map is interpolated to the barycenter and at the intensity peak of the source, by which the measured integrated flux and peak intensity are divided, respectively.

# Non-LTE Model Fitting of H$_2$CO

Following the method introduced in (cite: Ginsburg2016CMZTemp), we used RADEX (cite: van2007RADEX) to create model grids for the p-H$_2$CO molecular lines over 100 densities of $n=10^{2.5}$–$10^{7}$ cm$^{-3}$, 100 H$_2$CO column densities of $N$(H$_2$CO)$=10^{11}$–$10^{15}$ cm$^{-2}$, and 50 kinetic temperatures of $T_{\rm kin}=10$–$350$ K, with a fixed assumed line gradient of 5 km s$^{-1}$ pc$^{-1}$. In the grid modeling, the collision rates were taken from (cite: Wiesenfeld2013H2CO) and calculated for temperatures in the range from 10 to 300 K including energy levels up to about 200 cm$^{-1}$ for collisions with H$_2$. Based on the preconstructed non-LTE model grids, the line fitting is performed. The five parameters are kinetic temperature ($T_{\rm kin}$), formaldehyde column density ($\log N(\rm H_2CO)$), hydrogen molecule volume density ($\log n(\rm H_2)$), centroid velocity ($v_{\rm lsr}$) and line width (FWHM). For all the sources, only one velocity component is considered.

![](I13291-6229_ACA2_h2co_triplet_fit.pdf)

An example (I13291-6229_ACA2) of spectral line data and the fitting model is shown in Figure [8](#fig:fitexample), where $T_{\rm kin}$ is estimated to be 53($\pm11$) K. If the fitting fails (for seven spectra), then the $T_{\rm kin}$ is set to be equal to clump-averaged dust temperature $T_{\rm dust,clump}$ which is retrieved from (cite: Urquhart2018ATLASGAL). The kinetic temperatures for 207 ACA sources are then listed in column (3) of Table [\[tab:physical\]](#tab:physical).

## Validation

The volume density of the collisional partner, which is molecular hydrogen (H$_2$) in our case, serves as one of the non-LTE model parameters. Assuming a dust emission model and a good mix of dust and gas, it is possible to determine the source-averaged volume density of H$_2$. This value is listed in column (8) of Table [\[tab:physical\]](#tab:physical) independently.

As depicted in panel (f) of Figure [3](#fig:stats), the density of ACA sources predominantly falls within the range of $10^{4}$ to $10^{6}$ cm$^{-3}$, which is well-suited for H$_2$CO triplet model fitting. When the density surpasses $10^{6}$ cm$^{-3}$, the line ratio becomes less sensitive to kinetic temperature, primarily due to the effects of radiative trapping, as shown in Figure 6 of (cite: Ao2013CMZTemp). As we revisit and scrutinize the input parameters, we ensure the validity of our non-LTE model fitting for most of the QUARKS ACA sources.

In Figure [9](#fig:twodensity), we compare the volume density derived from RADEX line modeling $n_{\rm H_2,RADEX}$ and that derived from dust emission $n_{\rm H_2,dust}$ (Section [4.3](#results:physics)). The data points follow a bulk increasing trend although with a large dispersion, further justifying the self-consistency of the temperature estimation. Besides, we note that $n_{\rm H_2,RADEX}$ is systematically higher than $n_{\rm H_2,dust}$, as depicted by black dashed lines. This can be explained by the difference in spatial distribution or the sizes that the H$_2$CO/dust trace. If the size that dust traces is higher than that H$_2$CO traces, then $n_{\rm H_2,dust}$ should be naturally lower than $n_{\rm H_2,RADEX}$. Therefore, QUARKS high-resolution data should be essential to resolving and understanding internal density structure.

![](Twodensity.pdf)

## Caveats

The temperature estimation using the H$_2$CO triplet assumes that the H$_2$CO emission mainly traces dense gas, which is not the case in a sample of 12 infrared dark clouds (cite: Izumi2023ASHES-X). These authors argued that H$_2$CO emission is mainly sensitive to low-velocity outflow components rather than to quiescent gas expected in the early phases of star formation. So one must be keep in mind the fidelity of the temperature estimated from H$_2$CO triplets depends on how well H$_2$CO emission traces the gas in dense cores.

The non-LTE line modeling can be influenced by the line profile, including the wings of the line and self-absorption. For example, line wings can make least-square method fall into a false local minimum. There are six cases of severe self-absorption, for which we only assign them $T_{\rm dust,clump}$. If more than one velocity component is associated with an ACA source, the line width will be overestimated.

# QUARKS-ATOMS Link

Elliptical mask is defined by the geometrical measurement of the ACA 1.3 mm continuum source, $$\begin{equation}
 \label{eq:ellipse}
\begin{split}
    & \frac{\left[(x-x_Q)\cos\phi+(y-y_Q)\sin\phi\right]^2}{A^2} \\
    & + \frac{\left[(x-x_Q)\sin\phi-(y-y_Q)\cos\phi\right]^2}{B^2} \leq 1,
\end{split}
\end{equation}$$ where ${x,y}$ and ${x_Q,y_Q}$ are respectively the coordinates of the ATOMS and QUARKS sources, $A$, $B$, and $\phi$ are the major axis, minor axis, and the position angle of the QUARKS source. All parameters can be found in Table [\[tab:measurements\]](#tab:measurements) and ATOMS Table [\[tab:crossmatch\]](#tab:crossmatch). A QUARKS-ATOMS source link (link hereafter) is established when Eq. [\[eq:ellipse\]](#eq:ellipse) is satisfied.

We list the link, as introduced in Section [5.1](#discuss:nature), between ATOMS 3 mm dense cores and QUARKS 1.3 mm sources in Table [\[tab:crossmatch\]](#tab:crossmatch). The field name and the ATOMS dense core ID are listed in columns (1)–(2). The Galactic name of dense core, inherited from (cite: Liu2021ATOMS-III), is listed in column (3). The ICRS coordinates of the barycenter are listed in columns (4)–(5). The associated QUARKS source ID is listed in column (6). If no associated QUARKS source, then the ATOMS sources are referred as “field sources”, which are marked by “0”. The angular size ($L_{d}$) and position angle ($L_{\rm PA}$) of the link are listed in columns (7)–(8). The link fidelity, defined as how close the ATOMS source is to the QUARKS source, with values from 0 (unreliable) to 1 (reliable), is listed in column (9).

ccccccccc & & & & & $L_d$ & $L_{\rm PA}$ & Fidelity\
(r)4-5 & & & RA (ICRS) & DEC (ICRS) & & ($''$) & ($^{\circ}$) &\
(1) & (2) & (3) & (4) & (5) & (6) & (7) & (8) & (9)\
I08303-4303 & 1 & G261.6444-02.0876 & 08:32:09.0 & -43:13:42.9 & 1 & 4.5 & 41.6 & 0.69\
I08303-4303 & 2 & G261.6444-02.0890 & 08:32:08.6 & -43:13:45.8 & 1 & 1.2 & 108.5 & 0.99\
I08303-4303 & 3 & G261.6446-02.0899 & 08:32:08.4 & -43:13:48.3 & 1 & 3.9 & 57.0 & 0.8\
I08448-4343 & 1 & G263.7745-00.4266 & 08:46:35.0 & -43:54:23.8 & 1 & 1.4 & 28.5 & 0.93\
I08448-4343 & 2 & G263.7756-00.4281 & 08:46:34.9 & -43:54:30.3 & 2 & 3.5 & 23.7 & 0.57\
I08448-4343 & 3 & G263.7756-00.4291 & 08:46:34.6 & -43:54:32.6 & 2 & 1.7 & 123.7 & 0.94\
I08448-4343 & 4 & G263.7743-00.4317 & 08:46:33.7 & -43:54:34.8 & 3 & 3.5 & 59.9 & 0.77\
I08448-4343 & 5 & G263.7737-00.4326 & 08:46:33.3 & -43:54:35.1 & 3 & 1.7 & 150.5 & 0.91\
I08448-4343 & 6 & G263.7712-00.4363 & 08:46:31.8 & -43:54:36.4 & 4 & 7.6 & 95.0 & 0.59\
I08448-4343 & 7 & G263.7723-00.4350 & 08:46:32.4 & -43:54:36.6 & 4 & 1.6 & 108.5 & 0.97\
I08448-4343 & 8 & G263.7700-00.4379 & 08:46:31.1 & -43:54:36.7 & 0 & – & – & –\
I08448-4343 & 9 & G263.7744-00.4328 & 08:46:33.4 & -43:54:37.5 & 3 & 1.0 & 168.4 & 0.96\
I08448-4343 & 10 & G263.7766-00.4309 & 08:46:34.3 & -43:54:39.4 & 0 & – & – & –\
I08448-4343 & 11 & G263.7724-00.4366 & 08:46:32.0 & -43:54:40.5 & 4 & 6.7 & 59.6 & 0.19\
I08448-4343 & 12 & G263.7729-00.4364 & 08:46:32.1 & -43:54:41.4 & 0 & – & – & –\
I08448-4343 & 13 & G263.7776-00.4332 & 08:46:34.0 & -43:54:47.4 & 0 & – & – & –\

The field name and the ATOMS dense core ID are listed in columns (1)–(2). The Galactic name of dense core is listed in column (3). The ICRS coordinates of the barycenter are listed in columns (4)–(5). The associated QUARKS source ID is listed in column (6). If there is no associated QUARKS source, then “0”. The angular size ($L_{d}$) and position angle ($L_{\rm PA}$) of the link are listed in columns (7)–(8). The fidelity of the link is listed in column (9). The table is available in its entirety in machine-readable form.

Note that there are some ACA sources that lack associated ATOMS 3 mm sources, which can be categorized into two primary scenarios. In one scenario, the ATOMS dense core catalog prioritizes the high fidelity of genuinely dense cores, but this can lead to a higher false negative rate. Consequently, some QUARKS ACA sources with non-spherical morphologies may be missed in the ATOMS dense core catalog. An example of this is seen in sources I16132-5039_ACA1 and I16132-5039_ACA2, which are elongated sources without any associated ATOMS dense cores. In the other scenario, QUARKS data, particularly in certain fields, exhibit greater sensitivity than ATOMS. This higher sensitivity enables the detection of fainter structures. For example, I17269-3312_ACA3 and I17269-3312_ACA4, two relatively faint sources in the I17269-3312 field, are marginally seen in the ATOMS data and are not included in the catalog.

# Distance Effects on Mass Correlation

The calculations of the clump and the ACA source masses depend on distance by $M\propto d^2$. Therefore, it is crucial to examine the impact of distance on the mass correlation discussed in Section [5.2](#discuss:corr). To explore this, we categorize the QUARKS clumps into three groups based on their distances: $d\leq3$ kpc (Near), $3<d\leq6$ kpc (Mid), and $d>6$ kpc (Far). The selection of distance bins is solely based on achieving a similar sample size in each group.

We perform linear regression on the three groups individually and obtain similar quasi-linear correlations as observed in the total sample. The correlation coefficients for the three fittings are substantial, ranging from 0.72 to 0.74, and the $1\sigma$ scatters fall between 0.25 and 0.35. Both metrics indicate a significant correlation between $M_{\rm clump}$ and $M_{\rm source,total}$. Additionally, we observe wide mass range for narrow color (i.e., distance) range, suggesting that even narrower distance bins would still result in a relatively strong mass correlation. In summary, we assert a weak distance effect on the mass correlation in the QUARKS sample.

![](DistanceEffect.pdf)

107

(ref: Anderson2021HFS) Anderson, M., Peretto, N., Ragan, S. E., et al. 2021, MNRAS, 508, 2964

(ref: Ao2013CMZTemp) Ao, Y., Henkel, C., Menten, K. M., et al. 2013, A&A, 550, A135

(ref: Astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Astropy2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: Avison2015SDC335) Avison, A., Peretto, N., Fuller, G. A., et al. 2015, A&A, 577, A30

(ref: Avison2021SDC335) Avison, A., Fuller, G. A., Peretto, N., et al. 2021, A&A, 645, A142

(ref: Barnes2021IRDCs) Barnes, A. T., Henshaw, J. D., Fontani, F., et al. 2021, MNRAS, 503, 4601

(ref: Bertin1996SExtractor) Bertin, E., & Arnouts, S. 1996, A&AS, 117, 393

(ref: Bonnell2004Simulation) Bonnell, I. A., Vine, S. G., & Bate, M. R. 2004, MNRAS, 349, 735

(ref: BT2012) Butler, M. J., & Tan, J. C. 2012, ApJ, 754, 5

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Chen2019G14) Chen, H.-R. V., Zhang, Q., Wright, M. C. H., et al. 2019, ApJ, 875, 24

(ref: Contreras2013ATLASGAL) Contreras, Y., Schuller, F., Urquhart, J. S., et al. 2013, A&A, 549, A45

(ref: Contreras2018G331) Contreras, Y., Sanhueza, P., Jackson, J. M., et al. 2018, ApJ, 861, 14

(ref: Cornwell2008Multiscale) Cornwell, T. J. 2008, IEEE Journal of Selected Topics in Signal Processing, 2, 793

(ref: Csengeri2017ACA) Csengeri, T., Bontemps, S., Wyrowski, F., et al. 2017, A&A, 600, L10

(ref: Dib2023Protocluster) Dib, S. 2023, MNRAS, 524, 1625

(ref: Elia2017HiGAL) Elia, D., Molinari, S., Schisano, E., et al. 2017, MNRAS, 471, 100

(ref: Evans2022SlowSF) Evans, N. J., Kim, J.-G., & Ostriker, E. C. 2022, ApJL, 929, L18

(ref: Federrath2012SFR) Federrath, C., & Klessen, R. S. 2012, ApJ, 761, 156

(ref: Ginsburg2011Pyspeckit) Ginsburg, A., & Mirocha, J. 2011, PySpecKit: Python Spectroscopic Toolkit, Astrophysics Source Code Library, record ascl:1109.001

(ref: Ginsburg2022Pyspeckit) Ginsburg, A., Sokolov, V., de Val-Borro, M., et al. 2022, AJ, 163, 291

(ref: Ginsburg2016CMZTemp) Ginsburg, A., Henkel, C., Ao, Y., et al. 2016, A&A, 586, A50

(ref: Goedhart2023MGPS) Goedhart, S., Cotton, W. D., Camilo, F., et al. 2023, arXiv e-prints, arXiv:2312.07275

(ref: Goldsmith2001Coolant) Goldsmith, P. F. 2001, ApJ, 557, 736

(ref: Izumi2023ASHES-X) Izumi, N., Sanhueza, P., Koch, P. M., et al. 2023, arXiv e-prints, arXiv:2312.03935

(ref: Kahane1984OPR) Kahane, C., Frerking, M. A., Langer, W. D., Encrenas, P., & Lucas, R. 1984, A&A, 137, 211

(ref: Kauffmann2008dust) Kauffmann, J., Bertoldi, F., Bourke, T. L., Evans, N. J., I., & Lee, C. W. 2008, A&A, 487, 993

(ref: Krumholz2008Threshold) Krumholz, M. R., & McKee, C. F. 2008, Nature, 451, 1082

(ref: Larson2003IMF) Larson, R. B. 2003, in Astronomical Society of the Pacific Conference Series, Vol. 287, Galactic Star Formation Across the Stellar Mass Spectrum, ed. J. M. De Buizer & N. S. van der Bliek, 65

(ref: Li2017Isolation) Li, G.-X. 2017, MNRAS, 465, 667

(ref: Li2018Selfsimilar) Li, G.-X. 2018, MNRAS, 477, 4951

(ref: Li2023ASHES) Li, S., Sanhueza, P., Zhang, Q., et al. 2023, ApJ, 949, 109

(ref: LinY2021PhDThesis) Lin, Y. 2021, The structure of massive star-forming clumps, PhD thesis, Rheinische Friedrich-Wilhelms-Universität Bonn

(ref: Lin2019SABOCA) Lin, Y., Csengeri, T., Wyrowski, F., et al. 2019, A&A, 631, A72

(ref: Liu2021ATOMS-III) Liu, H.-L., Liu, T., Evans, Neal J., I., et al. 2021, MNRAS, 505, 2801

(ref: Liu2022ATOMS-IX) Liu, H.-L., Tej, A., Liu, T., et al. 2022, MNRAS, 511, 4480

(ref: Liu2023HFS) Liu, H.-L., Tej, A., Liu, T., et al. 2023a, MNRAS, 522, 3719

(ref: Liu2016NH3) Liu, T., Zhang, Q., Kim, K.-T., et al. 2016, ApJ, 824, 31

(ref: Liu2020ATOMS-I) Liu, T., Evans, N. J., Kim, K.-T., et al. 2020, MNRAS, 496, 2790

(ref: Liu2023QUARKS) Liu, X., Liu, T., Zhu, L., et al. 2023b, arXiv e-prints, arXiv:2311.08651

(ref: Lu2018Filament) Lu, X., Zhang, Q., Liu, H. B., et al. 2018, ApJ, 855, 9

(ref: Mainzer2011NOEWISE) Mainzer, A., Bauer, J., Grav, T., et al. 2011, ApJ, 731, 53

(ref: Mangum1993H2COTemp) Mangum, J. G., & Wootten, A. 1993, ApJS, 89, 123

(ref: MRN1997) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425

(ref: Matzner2000Efficiency) Matzner, C. D., & McKee, C. F. 2000, ApJ, 545, 364

(ref: McKee2003TC) McKee, C. F., & Tan, J. C. 2003, ApJ, 585, 850

(ref: McMullin2007CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Morii2023ASHES) Morii, K., Sanhueza, P., Nakamura, F., et al. 2023, ApJ, 950, 148

(ref: Morii2024) Morii, K., Sanhueza, P., Zhang, Q., et al. 2024, arXiv e-prints, arXiv:2403.07058

(ref: Motte2018Review) Motte, F., Bontemps, S., & Louvet, F. 2018, ARA&A, 56, 41

(ref: Motte2022ALMA-IMF-1) Motte, F., Bontemps, S., Csengeri, T., et al. 2022, A&A, 662, A8

(ref: Muller2001CDMS) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49

(ref: Neupane2020Global) Neupane, S., Garay, G., Contreras, Y., Guzmán, A. E., & Rodrı́guez, L. F. 2020, ApJ, 890, 76

(ref: Olguin2022SDC335) Olguin, F. A., Sanhueza, P., Ginsburg, A., et al. 2022, ApJ, 929, 68

(ref: O&H1994dust) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: Padmanabh2023MeerKAT) Padmanabh, P. V., Barr, E. D., Sridhar, S. S., et al. 2023, arXiv:2303.09231

(ref: Palau2014Fragmentation) Palau, A., Estalella, R., Girart, J. M., et al. 2014, ApJ, 785, 42

(ref: Palau2015Fragmentation) Palau, A., Ballesteros-Paredes, J., Vázquez-Semadeni, E., et al. 2015, MNRAS, 453, 3785

(ref: Palau2021Fragmentation) Palau, A., Zhang, Q., Girart, J. M., et al. 2021, ApJ, 912, 159

(ref: Peretto2023Decouple) Peretto, N., Rigby, A. J., Louvet, F., et al. 2023, MNRAS, 525, 2935

(ref: Peretto2013SDC335) Peretto, N., Fuller, G. A., Duarte-Cabral, A., et al. 2013, A&A, 555, A112

(ref: Peretto2020ClumpFed) Peretto, N., Rigby, A., André, P., et al. 2020, MNRAS, 496, 3482

(ref: Pineda2023PP7) Pineda, J. E., Arzoumanian, D., Andre, P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 233

(ref: Qin2022ATOMS-VIII) Qin, S.-L., Liu, T., Liu, X., et al. 2022, MNRAS, 511, 3463

(ref: Redaelli2022AG14) Redaelli, E., Bovino, S., Sanhueza, P., et al. 2022, ApJ, 936, 169

(ref: Reid2019Distance) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2019, ApJ, 885, 131

(ref: Rigby2021GASTON) Rigby, A. J., Peretto, N., Adam, R., et al. 2021, MNRAS, 502, 4576

(ref: Rosolowsky2010BGPSII) Rosolowsky, E., Dunham, M. K., Ginsburg, A., et al. 2010, ApJS, 188, 123

(ref: Saha2022ATOMS-XII) Saha, A., Tej, A., Liu, H.-L., et al. 2022, MNRAS, 516, 1983

(ref: Sanhueza2017G28) Sanhueza, P., Jackson, J. M., Zhang, Q., et al. 2017, ApJ, 841, 97

(ref: Sanhueza2019ASHES) Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886, 102

(ref: Sanhueza2021I18089) Sanhueza, P., Girart, J. M., Padovani, M., et al. 2021, ApJL, 915, L10

(ref: Schneider2010DR21) Schneider, N., Csengeri, T., Bontemps, S., et al. 2010, A&A, 520, A49

(ref: Schuller2009ATLASGAL) Schuller, F., Menten, K. M., Contreras, Y., et al. 2009, A&A, 504, 415

(ref: Sridharan2002HMPOs) Sridharan, T. K., Beuther, H., Schilke, P., Menten, K. M., & Wyrowski, F. 2002, ApJ, 566, 931

(ref: Svoboda2019HMSC) Svoboda, B. E., Shirley, Y. L., Traficante, A., et al. 2019, ApJ, 886, 36

(ref: Tan2014MSF) Tan, J. C., Beltrán, M. T., Caselli, P., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 149

(ref: Tang2017H2CO) Tang, X. D., Henkel, C., Chen, C. H. R., et al. 2017, A&A, 600, A16

(ref: Tang2021H2CO) Tang, X. D., Henkel, C., Menten, K. M., et al. 2021, A&A, 655, A12

(ref: Traficante2011HiGAL) Traficante, A., Calzoletti, L., Veneziani, M., et al. 2011, MNRAS, 416, 2932

(ref: Traficante2023SQUALO-I) Traficante, A., Jones, B. M., Avison, A., et al. 2023, MNRAS, 520, 2306

(ref: Urquhart2014ATLASGAL) Urquhart, J. S., Moore, T. J. T., Csengeri, T., et al. 2014, MNRAS, 443, 1555

(ref: Urquhart2018ATLASGAL) Urquhart, J. S., König, C., Giannetti, A., et al. 2018, MNRAS, 473, 1059

(ref: van2007RADEX) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: Wang2015Book) Wang, K. 2015, The Earliest Stages of Massive Clustered Star Formation: Fragmentation of Infrared Dark Clouds

(ref: Wang2011G28) Wang, K., Zhang, Q., Wu, Y., & Zhang, H. 2011, ApJ, 735, 64

(ref: Wang2014Snake) Wang, K., Zhang, Q., Testi, L., et al. 2014, MNRAS, 439, 3275

(ref: Wang2010ClumpFed) Wang, P., Li, Z.-Y., Abel, T., & Nakamura, F. 2010, ApJ, 709, 27

(ref: Weidner2013Cluster) Weidner, C., Kroupa, P., & Pflamm-Altenburg, J. 2013, MNRAS, 434, 84

(ref: Wiesenfeld2013H2CO) Wiesenfeld, L., & Faure, A. 2013, MNRAS, 432, 2573

(ref: Wright2010WISE) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868

(ref: WuJ2003Infall) Wu, J., & Evans, Neal J., I. 2003, ApJL, 592, L79

(ref: WuY2007Infall) Wu, Y., Henkel, C., Xue, R., Guan, X., & Miller, M. 2007, ApJL, 669, L37

(ref: Xu2023ATOMS-XV) Xu, F.-W., Wang, K., Liu, T., et al. 2023a, MNRAS, 520, 3259

(ref: Xu2023JCMTInfall) Xu, F., Wang, K., He, Y., et al. 2023b, ApJS, 269, 38

(ref: Xu2021HGaL) Xu, F., Wu, Y., Liu, T., et al. 2021, ApJ, 920, 103

(ref: Xu2024Scarcity) Xu, F., Wang, K., Liu, T., et al. 2024a, ApJL, 963, L9

(ref: Xu2024ASSEMBLE) Xu, F., Wang, K., Liu, T., et al. 2024b, ApJS, 270, 9

(ref: Yang2023G310) Yang, D., Liu, H.-L., Tej, A., et al. 2023, ApJ, 953, 40

(ref: Yuan2018G22) Yuan, J., Li, J.-Z., Wu, Y., et al. 2018, ApJ, 852, 12

(ref: Zhang2009G28) Zhang, Q., Wang, Y., Pillai, T., & Rathborne, J. 2009, ApJ, 696, 268

(ref: Zhang2021HMSCs) Zhang, S., Zavagno, A., López-Sepulcre, A., et al. 2021, A&A, 646, A25

(ref: Zhou2022HFS) Zhou, J.-W., Liu, T., Evans, N. J., et al. 2022, MNRAS, 514, 6038

(ref: Zhou2023Feedback) Zhou, J. W., Dib, S., Wyrowski, F., et al. 2023, arXiv e-prints, arXiv:2312.01497

(ref: Zinnecker2007MSF) Zinnecker, H., & Yorke, H. W. 2007, ARA&A, 45, 481

[^1]: <https://almascience.nrao.edu/processing/science-pipeline>

[^2]: [casaguide:automask](https://casaguides.nrao.edu/index.php?title=Automasking_Guide)

[^3]: <https://sextractor.readthedocs.io/en/latest/Introduction.html>.

[^4]: <https://pyspeckit.readthedocs.io/en/latest/formaldehyde_model.html>

[^5]: [ALMA Memo 211](https://library.nrao.edu/public/memos/alma/main/memo620.pdf)

</paper>

Write the methods card for this paper.