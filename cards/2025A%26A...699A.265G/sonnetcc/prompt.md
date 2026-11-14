# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...699A.265G\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...699A.265G",
 "title": "First polarization study of the M87 jet and active galactic nuclei at submillimeter wavelengths with ALMA",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Goddi, Ciriaco",
 "n_authors": 272,
 "arxiv_id": "2505.10181",
 "doi": "10.1051/0004-6361/202554140",
 "alma_projects_linked_by_archive": []
}
```

Paper text:
<paper>
# First polarization study of the M87 jet and active galactic nuclei at submillimeter wavelengths with ALMA

We investigated the polarization and Faraday properties of Messier 87 (M87) and seven other radio-loud active galactic nuclei (AGNs) at $\lambda$0.87 mm (345 GHz) using the Atacama Large Millimeter/submillimeter Array (ALMA). Our goal was to characterize the linear polarization (LP) fractions, measure Faraday rotation measures (RMs), and examine the magnetic field structures in the emission regions of these AGNs.

We conducted full-polarization observations as part of the ALMA Band 7 very long baseline interferometry (VLBI) commissioning during the April 2021 Event Horizon Telescope (EHT) campaign. We analyzed the LP fractions and RMs to assess the nature of Faraday screens and magnetic fields in the submillimeter emission regions.

We find LP fractions between 1% and 17% and RMs exceeding $10^{5}$ rad m$^{-2}$, which are 1–2 orders of magnitude higher than typically observed at longer wavelengths ($\lambda>$3 mm). This suggests denser Faraday screens or stronger magnetic fields. Additionally, we present the first submillimeter polarized images of the M87 jet and the observed AGNs, revealing RM gradients and sign reversals in the M87 jet indicative of a kiloparsec-scale helical magnetic field structure.

Our results provide essential constraints for calibrating, analyzing, and interpreting VLBI data from the EHT at 345 GHz, representing a critical step toward submillimeter VLBI imaging.

# Introduction

The development of a phased-array capability for the Atacama Large Millimeter/submillimeter Array (ALMA) has revolutionized very long baseline interferometry (VLBI) at millimeter wavelengths (cite: APPPaper; Goddi2019). By significantly enhancing the sensitivity of VLBI baselines, particularly at 230 GHz ($\lambda\approx 1.3$ mm), the inclusion of phased-ALMA arrays into existing VLBI arrays made possible the first horizon-scale images of supermassive black holes, including M87\* in the Messier 87 Galaxy (cite: EHTC2019_1; EHTC2019_2; EHTC2019_3; EHTC2019_4; EHTC2019_5; EHTC2019_6; EHT2021_1; EHT2021_2; EHT_2023; EHT2024) and Sgr A\* at the heart of the Milky Way (cite: EHTC2022_1; EHTC2022_2; EHTC2022_3; EHTC2022_4; EHTC2022_5; EHTC2022_6; EHT2024_1).

In recent developments, ALMA’s phased array capabilities were extended to the submillimeter (ALMA Band 7; $\nu \approx 345$ GHz; $\lambda\approx 0.87$ mm), enabling a performance comparable to that of Band 6 ($\nu \approx 230$ GHz) under suitable observing conditions (cite: APP2B7). The first test of ALMA’s Band 7 phasing capability occurred in October 2018 during a global VLBI campaign, marking the detection of the first VLBI fringes in the submillimeter regime between ALMA and three other Event Horizon Telescope (EHT) sites (cite: Raymond2024). Following this success, a full end-to-end test of the Band 7 VLBI capability was conducted at the end of the ALMA-EHT science campaign in April 2021, with the aim of obtaining the first 345 GHz VLBI fringes toward the EHT key target M87\* and selected radio-loud active galactic nuclei (AGNs), as well as assessing the feasibility of VLBI imaging in the submillimeter regime.

Observations at $\nu \approx 345$ GHz offer a 50% improvement in angular resolution over 230 GHz and are expected to enhance $uv$ coverage through the combination with data from lower frequencies. Such a multifrequency synthesis will enable higher-fidelity imaging while minimizing interstellar scattering effects, which is particularly critical for imaging Sgr A\* (cite: EHTC2022_3).

To turn the ALMA array into a coherently phased aperture for millimeter VLBI and integrate it with other VLBI stations, the connected-element interferometric visibilities must first be calibrated (cite: QA2Paper). This process inherently generates a full-polarization interferometric dataset as a by-product of VLBI observations with ALMA. For VLBI experiments, these interferometric datasets serve multiple purposes: they provide source-integrated parameters to refine and validate VLBI calibration and imaging workflows (cite: EHTC2019_2; EHTC2019_3; EHT2021_1; EHTC2022_2; EHTC2022_3; EHT2024_1) and provide critical observational constraints for theoretical models and physical interpretations (cite: EHT2021_2; EHTC2022_4; EHTC2022_5; EHTC2022_6). However, beyond their role in VLBI, these datasets have significant standalone scientific value, enabling the derivation of millimeter emission, polarization, and Faraday properties of VLBI targets on arcsecond scales. At $\lambda$0.87 mm, synchrotron emission originates from a more optically thin region closer to the supermassive black hole when compared to $\lambda>$1 mm, providing a unique window into the jet base and accretion flow.

In this paper we present the analysis of connected-element interferometric data from the ALMA Band 7 VLBI test conducted in April 2021[^1]. Results from the full 345 GHz VLBI campaign, including data from other stations, will be discussed in a follow-up paper (EHTC et al., in prep.; hereafter Paper II).

Section [2](#sec:data) details the observational setup (Sect. [\[sec:obs\]](#sec:obs)), observed targets (Sect. [2.2](#sec:targets)), calibration procedures (Sect. [2.3](#sec:datacal)), and full-polarization image deconvolution (Sect. [2.4](#sec:dataimg)). Section [3](#sec:analysis) describes the data analysis, including the extraction of Stokes parameters, polarimetric and Faraday property estimation (Sect. [3.1](#sec:polan)), and polarized image production (Sect. [3.2](#sec:imaging)). Section [4](#sec:res) presents the polarimetric properties (Sect. [4.1](#sec:agnpol)) and spectral indices (Sect. [4.2](#sec:AGNpec)) of the observed AGN sources, with a focus on the submillimeter polarized emission in the M87 jet (Sect. [4.3](#sec:m87)). Section [5](#sec:conclusions) summarizes our conclusions.

# Observations, data calibration, and imaging

ALMA Band 7 observations were performed on April 19, 2021, at the end of the EHT science campaign conducted in Band 6. ALMA was operated as a phased array, and joined a global network of VLBI stations operating at this frequency for an end-to-end submillimeter VLBI commissioning observation.

Weather conditions at ALMA were excellent: typical opacity values were $\tau_{225} \sim 0.05$, while system temperatures ($T_{\rm sys}$) ranged from 95 to 276 K. The measured phasing efficiencies during the test varied between 81% and 97%, reflecting strong system performance under favorable conditions (cite: APP2B7).

+:------------:+:------------:+:------------:+:-------------------------+:---------------------:+------:+
|              | Coordinates                 | Calibration Intent$^{a}$ | T$_{\rm on \ source}$ |       |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
| Common Name  | J2000 Name   | RA (J2000)   | DEC (J2000)              |                       | (min) |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
| 3C 279       | J1256$-$0547 | 12:56:11.167 | $-$05:47:21.52           | Target 1              | 34.4  |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
| 3C 273       | J1229+0203   | 12:29:06.700 | +02:03:08.60             | Flux, Bandpass        | 25.8  |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
| M87          | NGC 4486     | 12:30:49.412 | +12:23:28.27             | Target 2              | 16.9  |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
| 4C 01.28     | J1058+0133   | 10:58:29.604 | +01:33:58.83             | Polarization          | 10.5  |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
| S4 1144+40   | J1146+3958   | 11:46:58.298 | +39:58:34.28             | …                     | 7.5   |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
| PKS 1510-089 | J1512$-$0905 | 15:12:50.533 | $-$09:05:59.83           | …                     | 3.8   |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
| PKS 1335-127 | J1337$-$1257 | 13:37:39.783 | $-$12:57:24.70           | …                     | 3.8   |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
| non-VLBI scans$^{b}$                                                                                  |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
| 4C 01.28     | J1058+0133   | 10:58:29.604 | +01.33.58.83             | Polarization          | 40.3  |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
| PKS 1243-072 | J1246$-$0730 | 12:46:04.232 | $-$07.30.46.575          | Phase                 | 24.7  |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
| 3C 273       | J1229+0203   | 12:56:11.167 | $-$05:47:21.52           | Flux, Bandpass        | 10.1  |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+
|              |              |              |                          |                       |       |
+--------------+--------------+--------------+--------------------------+-----------------------+-------+

+:-----------:+:--------:+:-----------------:+:------------------:+:----------------:+:-------------------:+:----------------:+:---------------------:+
| Source      | Day      | I$^{a}$           | Spectral Index     | LP               | $\chi$              | $\chi_0$         | RM                    |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+
|             | \(2021\) | (Jy)              | ($\alpha$)         | ($\%$)           | (deg)               | (deg)            | ($10^5$ rad m$^{-2}$) |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+
| 3C273       | Apr 19   | 4.17 $\pm$ 0.42   | -0.781 $\pm$ 0.008 | 1.67 $\pm$ 0.03  | -64.19 $\pm$ 0.52   | -38.9 $\pm$ 7.3  | -5.8 $\pm$ 1.7        |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+
| 3C279       | Apr 19   | 8.73 $\pm$ 0.87   | -0.48 $\pm$ 0.04   | 10.63 $\pm$ 0.03 | -46.711 $\pm$ 0.081 | -41.2 $\pm$ 1.1  | -1.26 $\pm$ 0.26      |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+
| 4C01.28     | Apr 19   | 1.50 $\pm$ 0.15   | -0.42 $\pm$ 0.03   | 8.67 $\pm$ 0.03  | -37.72 $\pm$ 0.11   | -37.4 $\pm$ 1.5  | -0.08 $\pm$ 0.35      |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+
| J1146+3958  | Apr 19   | 0.396 $\pm$ 0.040 | -0.4 $\pm$ 0.2     | 2.66 $\pm$ 0.07  | 87.27 $\pm$ 0.77    | 107 $\pm$ 11     | -4.4 $\pm$ 2.5        |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+
| J1337-1257  | Apr 19   | 3.13 $\pm$ 0.31   | -0.38 $\pm$ 0.05   | 16.68 $\pm$ 0.03 | -7.310 $\pm$ 0.055  | -8.15 $\pm$ 0.77 | 0.19 $\pm$ 0.18       |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+
| J1512-0905  | Apr 19   | 1.74 $\pm$ 0.17   | -0.42 $\pm$ 0.04   | 1.07 $\pm$ 0.04  | -65.72 $\pm$ 0.95   | -96 $\pm$ 13     | 6.9 $\pm$ 3.1         |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+
| M87         | Apr 19   | 0.970 $\pm$ 0.097 | -1.24 $\pm$ 0.02   | 2.80 $\pm$ 0.03  | 12.60 $\pm$ 0.35    | 8.5 $\pm$ 5.0    | 0.9 $\pm$ 1.1         |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+
| non-VLBI scans                                                                                                                                      |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+
| 3C273$^{b}$ | Apr 19   | 4.17 $\pm$ 0.42   | -0.68 $\pm$ 0.01   | ...              | ...                 | ...              | ...                   |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+
| 4C01.28     | Apr 19   | 1.50 $\pm$ 0.15   | -0.36 $\pm$ 0.02   | 8.66 $\pm$ 0.03  | -37.68 $\pm$ 0.11   | -38.0 $\pm$ 1.6  | 0.07 $\pm$ 0.37       |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+
| J1246-0730  | Apr 19   | 0.280 $\pm$ 0.028 | -0.56 $\pm$ 0.04   | 0.6 $\pm$ 0.1    | -17.0 $\pm$ 6.6     | -119 $\pm$ 95    | 23 $\pm$ 21           |
+-------------+----------+-------------------+--------------------+------------------+---------------------+------------------+-----------------------+

## Observational setup 

The observations at Band 7 spanned a continuous session of nearly 5 hours (from 01:16 to 06:08 UTC) and utilized 42 antennas. Of these, 31 were configured within a 400-meter radius around the reference antenna to form the phased array (baselines to 0.8 km). Eleven additional antennas (baselines to 1.3 km) completed the array and were used as un-phased comparison antennas for the determination of phasing efficiency estimates. The antenna locations on April 19 are plotted in Fig. [1](#fig:plotants).

![](figs/2019_1_00009_CSV_antpos)

The setup incorporated four spectral windows (SPWs) in dual linear polarization (LP); two in the lower sideband and two in the upper sideband, with central frequencies of 335.600, 337.5411[^2], 347.600, and 349.600 GHz. Each SPW offered an effective bandwidth of 1875 MHz. The ALMA interferometric data were averaged by a factor of 8 in frequency, resulting in 240 spectral channels per SPW with a channel spacing of 7.8125 MHz.

## Observed targets

As these observations were designed as a comprehensive end-to-end commissioning test, the well-known quasar 3C279 was selected as the primary target. Given the novelty of VLBI at 345 GHz, there is currently limited guidance on suitable calibrators for this frequency. To address this, a selection of promising candidates was included for calibration and evaluation. This candidate sample comprises bright quasars and other compact extragalactic sources that had previously produced VLBI fringes in Band 6 observations. Notably, the sample includes M87\*, a planned future science target for 345 GHz VLBI observations. It should be noted that the observations include scans on three targets during gaps in the VLBI schedule. These scans were observed by ALMA for calibration purposes. In total, eight targets were observed in VLBI mode, while one target was observed exclusively by ALMA. A detailed list of the observed sources and their adopted calibration roles is provided in Table [\[table:sources\]](#table:sources) (see also Sect. [2.3](#sec:datacal)).

## Data calibration

The ALMA data were calibrated using the Common Astronomy Software Applications (casa) package, following the specialized “Quality Assurance Level 2” (QA2) procedures described in (cite: QA2Paper). As detailed in those studies, the VLBI and non-VLBI scans are calibrated independently, resulting in separate calibration solutions.

3C273 was adopted as an absolute flux-density calibrator, a source routinely observed by ALMA as part of the flux-density monitoring program with the ALMA Compact Array (ACA; see Appendix [7](#app:amapola_comp)). From the ALMA database, the flux density at 342 GHz was derived as $S_{342 GHz} = 4.164$ Jy with a spectral index $\alpha$=–0.79.

Accurate calibration of ALMA VLBI science data requires a full polarization calibration of interferometric visibilities. ALMA’s linearly polarized feeds simultaneously receive both orthogonal polarizations (X and Y), with all antennas in the phased array aligned to the reference antenna. Since the reference antenna’s phase is set to zero in both polarizations, a residual phase bandpass remains in the cross-hands of all baselines. Correcting this residual XY phase is essential for accurately combining cross- and parallel-hands to extract Stokes parameters. Thus, the primary calibration requirement for VLBI correlation is determining the X-Y phase difference and delay at the reference antenna (see Sect. 5 of (cite: QA2Paper) for details). This step enables the conversion of ALMA’s linearly polarized data into a circular polarization basis, ensuring consistency with other VLBI stations (cite: PCPaper; QA2Paper). J1058+0133 (4C 01.28) was chosen as the polarization calibrator due to its adequate parallactic angle coverage and the presence of a compact, strongly polarized core (at the $\sim$8% level). This selection enabled the simultaneous determination of the source polarization model and an estimate of the XY cross-phase at the reference antenna. The Stokes parameters derived from the polarization model were determined as *IQUV* = \[1.50, 0.033, $-$0.126, 0.0\] Jy.

## Full-Stokes imaging

All targets observed in Band 7 were imaged using the casa task `tclean` in all Stokes parameters: $I$, $Q$, $U$, and $V$. A Briggs weighting scheme (cite: Briggs1995) was adopted with a robust parameter of 0.5 and a cleaning gain of 0.1.

A first cleaning step (100 iterations across all Stokes parameters) was performed within the inner 4$''$. If significant emission ($>7\sigma$) remained in the residual maps (e.g., for M87), an automatic script updated the cleaning mask, and a second, deeper cleaning (2000 iterations across all Stokes parameters) was conducted down to 2$\sigma$. Both cleaning steps were run with the parameter `interactive=False`. A final interactive cleaning step (`interactive=True`) was performed to manually adjust the mask, capturing any real emission missed by the automatic process and cleaning deeper sources with complex structures or high-residual signals.

The array configuration during phased-array observations provided synthesized beams ranging from \[0$\rlap{.}^{\prime\prime}$36–0$\rlap{.}^{\prime\prime}$50\] $\times$ \[0$\rlap{.}^{\prime\prime}$29–0$\rlap{.}^{\prime\prime}$34\], depending on the target. We produced 576$\times$576 pixel maps with a pixel size of 0$\rlap{.}^{\prime\prime}$06, resulting in a field of view of 34$\rlap{.}^{\prime\prime}$6 $\times$ 34$\rlap{.}^{\prime\prime}$6, which comfortably covered the primary beam of ALMA Band 7 (18$''$ at 350 GHz).

Maps were produced for individual SPWs and by combining SPWs in each sideband (SPW=0,1 and SPW=2,3) using `deconvolver=‘hogbom’` with `nterms=1`. Additionally, maps combining all four SPWs were created using `deconvolver=‘mtmfs’` with `nterms=2`, achieving better sensitivity and producing higher-quality images[^3]. Thus, the combined SPW images were used for the imaging analysis presented in this paper, except in cases where a per-SPW analysis was necessary, such as for spectral index or Faraday rotation studies.

# Data analysis

The data, calibrated and imaged as described in Sect. [\[sec:obs\]](#sec:obs), were analyzed following the procedures outlined in (cite: Goddi2021). The analysis consisted of two main components:

- Extract the Stokes parameters in the compact cores of the observed targets and estimate their polarimetric and Faraday properties (Sect. [3.1](#sec:polan)).

- Produce polarized images for each target and determine the spatial distribution of the polarimetric quantities on arcsecond (kiloparsec) scales (Sect. [3.2](#sec:imaging)).

## Polarization analysis of point sources

To extract flux values for Stokes $I$, $Q$, $U$, and $V$, we employed two alternative methods, one that utilizes the visibility data and the other full-Stokes images.

In the $uv$-plane analysis, we used the external casa library uvmultifit (cite: UVMULTIFIT). To optimize processing time, we first averaged all 240 frequency channels to produce eight-channel, four-SPW visibility $uv$ files. Assuming the emission is dominated by a central point source at the phase center, we fit a `delta` function to the visibilities, extracting Stokes $I$, $Q$, $U$, and $V$ parameters for each SPW individually.

For the image-based approach, we summed the central $5\times5$ pixels of the `CLEAN` model component map. Summing only these central pixels isolates core emission from the surroundings, which is particularly important for sources with extended structure.

(cite: Goddi2021) performed a statistical comparison of flux-extraction methods in the $uv$ and image planes for a sample of VLBI targets observed in Bands 3 and 6. They found that the median absolute deviation of the Stokes parameters between methods is $<$1% for both point and extended sources. This agreement holds for the current Band 7 observations as well.

Using the measured Stokes parameters, we determined polarization properties for all targets, including the fractional LP ($LP = \sqrt{Q^{2}+U^{2}}/I$), the electric vector position angle (EVPA; $2\chi=\mathrm{arctan}(U/Q)$), and its variation with frequency (Faraday rotation; see Sect. [3.1.2](#subsec:RM)). Uncertainties in LP include the thermal errors of Stokes $Q$ and $U$ and a 1$\sigma$ systematic error (added in quadrature) associated with Stokes $I$ leakage into Stokes $Q$ and $U$ (0.03% of Stokes $I$). This analysis results in LP uncertainties $<0.1\%$, consistent with previous studies (cite: Nagai2016; Bower2018; Goddi2021).

The polarization quantities, averaged across the four SPWs, are reported in Table [\[tab:EHT_uvmf_RM\]](#tab:EHT_uvmf_RM). Table [\[tab:EHT_uvmf_spw\]](#tab:EHT_uvmf_spw) provides the polarimetric quantities for each SPW. We note that while the polarization parameters of 4C 01.28 from non-VLBI scans closely match those from VLBI scans (indicating consistent independent polarization calibrations), the short observation of 3C 273 did not yield data of sufficient quality for meaningful polarization analysis. Consequently, non-VLBI scans of 3C 273 were excluded, and the polarization analysis is based solely on VLBI scans.

### Comparison with the AMAPOLA survey

For the purposes of absolute flux calibration, ALMA regularly monitors the flux density of bright sources (mainly blazars or quasi-stellar objects) distributed across the entire right ascension range ("the Grid"). These observations are conducted together with solar system objects as part of the Grid Survey (GS) program, which operates on a cadence of approximately 10 days. The observations are executed with the Atacama Compact Array (ACA) in Bands 3, 6, and 7. Since the full-polarization mode is employed, it is possible to extract polarimetric information from the GS sources.

This polarimetric analysis is performed using AMAPOLA[^4], a set of CASA-compatible Python scripts designed to reduce the full-Stokes polarimetry of GS observations. While the AMAPOLA values are primarily used for observation planning and the ACA and ALMA-VLBI arrays cover different $uv$ ranges, comparing our data with the AMAPOLA database helps identify any systematic effects or clear inconsistencies due to variability within a week-long time frame.

The GS includes multiple measurements in Band 3 and Band 7 from April 2021 for all our targets, except M87. Our analysis shows that the polarimetric measurements are generally consistent with the historical trends reported for the Grid sources. Additional details, including comparison plots, are provided in Appendix [7](#app:amapola_comp).

### Rotation measure

Since we measured the EVPA at four distinct frequencies (one for each SPW) spanning a 16 GHz frequency range (334.6–350.6 GHz), we could estimate the Faraday rotation measure (RM) in the 0.87 mm band. Assuming that the Faraday rotation arises from a single, external, homogeneous Faraday screen (i.e., the rotation occurs outside the plasma responsible for the polarized emission), a linear dependence between the EVPA and the wavelength squared is expected.

We modeled this relationship by fitting the RM and the mean wavelength EVPA ($\bar{\chi}$) using the standard linear relation:

$$\begin{equation}
\chi = \bar{\chi} + RM (\lambda^2 - \bar{\lambda}^2) \,,
\label{eq:rm}
\end{equation}$$

where $\chi$ is the observed EVPA at wavelength $\lambda$, and $\bar{\chi}$ is the EVPA at the mean wavelength $\bar{\lambda}$ (corresponding to the band center). Additionally, the EVPA extrapolated to zero wavelength (assuming the $\lambda^2$ dependence holds) is given by $$\begin{equation}
\chi_{0} = \bar{\chi} - RM \bar{\lambda}^2 \,.
\label{eq:chi0}
\end{equation}$$

The RM fitting is performed using a weighted least-squares method applied to $\chi$ as a function of $\lambda^2$. The values of $\bar{\chi}$, $\chi_{0}$, and the fitted RM are reported in the sixth, seventh, and eighth columns of Table [\[tab:EHT_uvmf_RM\]](#tab:EHT_uvmf_RM). We determine EVPA uncertainties ranging from 0.06$^{\circ}$ to 1$^{\circ}$ (excluding J1246-0730, where LP$<1$%), corresponding to RM propagated errors between 0.08 and $3 \times 10^5$ rad m$^{-2}$. Despite these relatively high uncertainties and the limited frequency coverage at these high frequencies, we achieve $3\sigma$ RM detections in 3C273 and 3C279. Details on the calculation of EVPA and RM uncertainties, as well as an evaluation of the robustness of RM fits derived from relatively narrow frequency coverage (16–18 GHz) at submillimeter wavelengths, are provided in (cite: Goddi2021).

![image](./figs/mapspoli/M87_I) ![image](./figs/mapspoli/M87_ALPHA) ![image](./figs/mapspoli/M87_LP) ![image](./figs/mapspoli/M87_RM)

## Polarization images

We used the full-Stokes images (produced as described in Sect. [2.4](#sec:dataimg)) to determine the spatial distribution of the polarimetric quantities on arcsecond scales. Specifically, we executed custom Python scripts in CASA that take as input the Stokes $I$, $Q$, and $U$ images and output images of the linear polarized intensity, the fractional LP, the EVPA, and the Faraday RM. All these polarization quantities were calculated as described in Sects. [3.1](#sec:polan) and [3.1.2](#subsec:RM) on a pixel-by-pixel basis after convolving all SPW images to the same synthesized beam. In generating the final images, we applied a threshold defined as $\rm 3 \times \sigma$ (rms noise level) for Stokes $I$ and $\rm 2 \times \sigma$ for the polarized flux density[^5].

Representative images are presented in Fig.[2](#fig:m87_polimage), showcasing M87, and Fig.[3](#fig:polimages), featuring 3C 279, 3C 273, and 4C 01.28[^6]. The raster image in each panel displays the total intensity, spectral index (for M87), LP fraction, and RM. White vectors overlaid on these images represent the orientation of the EVPAs, with their lengths linearly proportional to the polarized flux. It should be noted that these EVPAs are not corrected for Faraday rotation and that the magnetic field vectors should be rotated by $90\deg$.

![image](./figs/mapspoli/3C279_I) ![image](./figs/mapspoli/3C279_LP) ![image](./figs/mapspoli/3C279_RM)

![image](./figs/mapspoli/3C273_I) ![image](./figs/mapspoli/3C273_LP) ![image](./figs/mapspoli/3C273_RM) ![image](./figs/mapspoli/4C01.28_I) ![image](./figs/mapspoli/4C01.28_LP) ![image](./figs/mapspoli/4C01.28_RM)

# Results and discussion

We derived polarimetric properties and produced polarized images of eight AGNs observed in full-polarization mode with ALMA in the 0.87 mm band for the first time. In Sect. [4.1](#sec:agnpol) we analyze the polarization characteristics of the AGN; in Sect. [4.2](#sec:AGNpec) we discuss their spectral indices; and in Sect. [4.3](#sec:m87) we focus on the polarized submillimeter emission from the kiloparsec-scale jet in M87.

## AGN polarization properties

The polarimetric quantities for our AGN targets, derived as described in Sect. [3.1](#sec:polan), are summarized in Table [\[tab:EHT_uvmf_RM\]](#tab:EHT_uvmf_RM). The table also includes the measured LP fractions, EVPAs, and RMs, which can provide key insights into the magnetic field structures and plasma conditions within the AGN jets.

The LP fractions in the AGN central cores span a wide range, from $\lesssim 1$% for weakly polarized targets (e.g., PKS1243-072 and PKS1510-089) to 10–17% for strongly polarized sources like 3C279 and PKS1335-127, consistent with previous measurements (Appendix [7](#app:amapola_comp)).

This is the first time Faraday RMs have been measured in the submillimeter. In 3C273, we measure RM = $(-5.8 \pm 1.6) \times 10^5$  rad m$^{-2}$ at 0.87mm, which is consistent with previous ALMA observations at 1.3 mm (cite: Hovatta2019; Goddi2021) and higher than 3mm observations (cite: Goddi2021). Interestingly, the sign of the RM at 0.87mm differs from previous 1.3 mm observations, which we interpret as a result of time variability rather than a frequency-dependent effect (Carlos et al., in prep.).

In 3C279, earlier measurements showed RM values ranging from 1800 to 2700  rad m$^{-2}$ at 3.5mm (cite: Lee2015; Goddi2021) and an upper limit of 5000  rad m$^{-2}$ at 1.3 mm (cite: Goddi2021). Our new observations suggest a significant increase in RM at shorter wavelengths, supporting the idea that higher frequencies probe the innermost regions with stronger magnetic fields and denser plasma. Given the time variability of these sources, simultaneous multi-band observations are required to confirm this trend and establish the dependence of RM on wavelength. Some targets, including M87, 3C279, 3C273, and 4C 01.28, were observed at lower frequencies (Bands 3 and 6; $\nu\approx$86 GHz and 230 GHz, respectively) during the same week. A comparative analysis of polarization properties across ALMA bands is planned for a future study (Carlos et al., in prep.).

Our findings of RM exceeding $10^5$ rad m$^{-2}$ in AGN cores at $\lambda \sim$0.87mm align with previous studies at millimeter wavelengths (cite: Plambeck2014; IMV2015; Hovatta2019; Goddi2021). These high RM values, which are 1–2 orders of magnitude greater than those typically reported for AGNs at $\lambda >$ 3 mm (cite: Gabuzda2017; Peng2024), point to a denser Faraday screen or stronger magnetic fields in the submillimeter emission region.

## AGN spectral indices 

In addition to polarization parameters, we derived the total intensity spectral index $\alpha$ for all sources, where $\alpha$ is defined such that $I(\nu) \propto \nu^{\alpha}$. The spectral index was computed “in-band” using a weighted least-squares fit across the four flux-density measurements in each SPW. The AGN cores systematically show negative spectral indices in the range $\alpha = -1.3$ to $-0.4$, consistent with previous findings at millimeter wavelengths (cite: Agudo2018; Goddi2021). This contrasts with the flat spectral indices ($\alpha \approx 0$) typically observed at longer centimeter wavelengths, further supporting the idea that AGN cores become progressively more optically thin at shorter wavelengths.

For M87, the compact core exhibits a spectral index of $\alpha = -1.25$, consistent with previous measurements at 1.3 mm (cite: Goddi2021) but contrasting with the flatter spectra observed at 3 mm (cite: Doi2013) and at centimeter wavelengths (cite: Kravchenko2020). This steep spectral index suggests a spectral break between 3 mm and 1.3 mm, transitioning to a consistent power law from 1.3 mm to 0.87 mm. Such a break is likely due to the inclusion of contributions from both the compact core and the inner jet within the ALMA beam. While the compact (VLBI) core typically displays a flat spectrum, the jet component has a steeper spectral index, which dominates at higher frequencies due to decreased opacity at the jet base, as predicted by the standard jet model (cite: BlandfordKonigl1979).

## Polarization properties of the M87 jet at 345 GHz

High-resolution polarization imaging of the relativistic jet in M87 at millimeter wavelengths has been achieved through ALMA observations at $\lambda$3mm with a resolution $\sim$2.5$''$ (cite: Peng2024) and $\lambda$1.3mm with a resolution $\sim$1$''$ (cite: Goddi2021). These studies revealed the narrow, straight kiloparsec-scale jet extending over $\sim$25$''$ from the nucleus, including several prominent knots (D, F, A, B, C) previously identified in optical and radio images. At $\lambda$3 mm, the jet-inflated radio lobes are also visible, with features imaged in greater detail at lower frequencies (e.g., the NRAO 20 cm Very Large Array image[^7]).

Our $\lambda$0.87mm ALMA observations show a similar structure to the $\lambda$1.3mm image (cite: Goddi2021) but with improved angular resolution ($\sim$0$\rlap{.}^{\prime\prime}$3), allowing us to resolve HST-1 from the core. HST-1 is a bright, knot-like feature discovered with the *Hubble* Space Telescope and located approximately 0.85 arcseconds (about 60–70 parsecs) downstream from the central black hole (cite: Biretta1999). HST-1 has exhibited remarkable properties over the years, including rapid variability, superluminal motion, and significant flaring activity (cite: Cheung2007; Giroletti2012), making it a critical site for understanding particle acceleration, jet collimation, and magnetic field dynamics in the M87 jet and in AGNs in general.

The radio core dominates the Stokes I emission with a peak brightness of $\sim$1Jy beam$^{-1}$ (Fig.[2](#fig:m87_polimage), top left). In contrast, the jet knots become more prominent in the linearly polarized intensity, relative to the total intensity, as the fractional polarization increases from the core outward. The LP image (Fig.[2](#fig:m87_polimage), bottom left) shows the lowest fractional polarization ($\lesssim$3%) at the core, which rises to $\sim$20% toward HST-1 and peaks at $\sim$55%, 42%, and 40% in between knots D, E, and A, respectively. The high degree of polarization observed in the knots is indicative of a well-ordered magnetic field structure within these regions, likely resulting from shock compression or shear flows in the jet plasma (cite: Laing1980).

The EVPA distribution observed at $\lambda$0.87mm closely matches prior results at $\lambda$1.3mm (cite: Goddi2021) and $\lambda$3 mm (cite: Peng2024) and agrees with centimeter-wave polarization measurements from the Very Large Array (cite: Algaba2016; Pasetto2021). This consistency across multiple epochs suggests a stable magnetic field configuration. The EVPA distribution is generally perpendicular to the jet axis, except in the regions HST-1 and Knot A. Ignoring Lorentz transformation and light aberration, rotating the EVPA by 90° (without Faraday correction) indicates that the magnetic field is mostly parallel to the jet axis, except in HST-1 and Knot A, where it becomes nearly perpendicular. These deviations are likely caused by recollimation or standing shocks, which can alter the helicity of the magnetic field locally due to variations in the radial profiles of the poloidal and toroidal components (cite: Mizuno2015).

The RM, derived from EVPA measurements between 334.6GHz and 350.6GHz (Fig. [2](#fig:m87_polimage), bottom right), reveals both gradients and sign reversals along the jet. Near the core, the RM exhibits an east-to-west gradient, ranging from $(2.5\pm3.9)\times10^{5}$ rad m$^{-2}$ at 0.3$''$ east to $(-1.2\pm0.5)\times10^{5}$ rad m$^{-2}$ at 0.3$''$ west. Downstream in HST-1, the RM reaches $(44\pm18)\times10^{5}$ rad m$^{-2}$ at 0.96$''$ from the core, decreasing with distance. Knot D exhibits RM values ranging from $(47\pm23)\times10^{5}$ rad m$^{-2}$ to $(-29\pm11)\times10^{5}$ rad m$^{-2}$, while knot A displays an RM of $(20.3\pm4.1)\times10^{5}$ rad m$^{-2}$ that varies significantly across the region.

The observed reversals in RM sign along the jet indicate changes in the line-of-sight magnetic field direction, while the RM gradients across the jet width reveal oppositely directed line-of-sight magnetic fields at the jet edges. These results are consistent with previous lower-frequency studies, which reported similar RM gradients observed with ALMA at 3 mm (cite: Peng2024) and the VLA at 1.7–7.5 cm (cite: Pasetto2021). Such RM gradients and sign reversals are evidence of a helical magnetic field threading the jet, potentially persisting up to kiloparsec scales (cite: Pasetto2021). This configuration aligns with theoretical predictions of dynamically significant poloidal magnetic fields being twisted into a helix by the rotation of the black hole–accretion disk system (cite: Tchekhovskoy2011), and possibly with the "cosmic battery" model (cite: Myserlis2021; Contopoulos2022). Independent support for this interpretation is provided by EHT observations of polarized emission near the M87 black hole (cite: EHT2021_2), further corroborating the presence of a helical magnetic field structure.

A helical magnetic field could potentially also explain another feature observed in the M87 core, its high RM variability (cite: Goddi2021). Several scenarios may account for this variability, including turbulence in the accretion flow causing internal Faraday rotation, a dynamically changing external Faraday screen, or a rapidly varying source at horizon scales with a static external screen. Alternatively, a helical magnetic field could introduce RM variability through beam-averaging effects. Variations in beam size across different observations may sample regions with oppositely directed magnetic fields along the line of sight, leading to distinct RM measurements.

Our submillimeter observations, however, are limited by angular resolution, sensitivity, and frequency coverage, preventing a definitive differentiation between internal and external Faraday rotation and a precise characterization of the helical magnetic field in the M87 jet. While spatial RM variations along the jet axis are evident, the current imaging sensitivity is insufficient to continuously recover the polarized emission structure on kiloparsec scales. This limitation prevents us from confirming whether consistent RM and LP transverse gradients persist along the full extent of the jet. Moreover, the limited resolution impedes the separation of emissions originating from the jet’s edges and central axis, leaving open the possibility that the observed RM gradients are due to external material rather than the jet’s intrinsic magnetic field. Simultaneous observations with the EHT (which will be discussed in Paper II) are expected to shed light on the properties of the Faraday rotation medium in the core region and provide insights into the magnetic field structure at the base of the jet.

The observed time variability in RM (cite: Goddi2021) adds another layer of complexity, as it precludes using nonsimultaneous datasets to reliably confirm RM-wavelength dependences. Addressing these challenges requires simultaneous, beam-matched, and multifrequency ALMA observations. To this end, we plan to analyze a comprehensive dataset of ALMA observations, covering multiple frequency bands (Bands 3, 6, and 7) and spanning several years, with data obtained on multiple days. This systematic approach will enable a detailed investigation of time- and frequency-dependent effects and thus a more robust determination of the RM’s frequency dependence. Such an analysis will provide critical insights into whether the Faraday rotation is internal or external and refine our understanding of the helical magnetic field structure in the M87 jet. The findings from this extended analysis will be presented in an upcoming publication.

# Summary and conclusions

We have presented the first submillimeter full-polarization study of radio-loud AGNs with ALMA, analyzing their polarization and Faraday properties. We find LP fractions ranging from 1% to 17% and RMs exceeding $10^{5}$ rad m$^{-2}$, consistent with earlier studies at millimeter wavelengths (cite: Plambeck2014; IMV2015; Hovatta2019; Goddi2021). These RM values are 1–2 orders of magnitude higher than those observed in AGNs at $\lambda>$3 mm (cite: Gabuzda2017; Peng2024), indicating a denser Faraday screen or stronger magnetic fields in the submillimeter emission regions.

We produced the highest-frequency polarized images ever of these AGNs, which included M87 and its jet. For M87, we observe RM gradients and sign reversals both along and across the jet axis, potentially reflecting reversals in the magnetic field direction relative to the line of sight. If confirmed, this would support a helical magnetic field configuration on kiloparsec scales, as suggested by lower-frequency VLA studies (cite: Pasetto2021). In future work we will analyze multifrequency, multi-epoch ALMA data and explore the time- and frequency-dependent properties of Faraday rotation to better constrain the magnetic field structure in M87.

The ALMA data were obtained in the 0.87   band during VLBI commissioning tests conducted in collaboration with the EHT Collaboration. These data provided essential calibration and interpretation for simultaneous VLBI observations with the EHT. Notably, phased ALMA observations on April 19, 2021, enabled the first detection of VLBI fringes at 345 GHz for M87 and selected AGNs (cite: app2_report_2024). This milestone represents a key step in evaluating VLBI imaging feasibility in the submillimeter band.

Very long baseline interferometry observations at this frequency offer a 50% improvement in resolution compared to 230 GHz and substantially reduce interstellar scattering, which is especially relevant for imaging Sgr A\*. The combination of 230 GHz and 345 GHz data enhances *uv* coverage, enabling high-fidelity imaging with multifrequency synthesis. These advancements will open new pathways for studying black hole shadows in M87 and Sgr A\*, as well as accretion and jet formation in nearby AGNs. Reduced opacity at 345 GHz allows jet-launching regions closer to the black hole to be probed, offering critical insights into jet formation, collimation, acceleration, and the phenomenon of limb-brightening in inner jets, and thus deepening our understanding of AGN physics.

# Acknowledgements

The Event Horizon Telescope Collaboration thanks the following organizations and programs: the Academia Sinica; the Academy of Finland (projects 274477, 284495, 312496, 315721); the Agencia Nacional de Investigación y Desarrollo (ANID), Chile via NCN$19\_058$ (TITANs), Fondecyt 1221421 and BASAL FB210003; the Alexander von Humboldt Stiftung; an Alfred P. Sloan Research Fellowship; Allegro, the European ALMA Regional Centre node in the Netherlands, the NL astronomy research network NOVA and the astronomy institutes of the University of Amsterdam, Leiden University, and Radboud University; the ALMA North America Development Fund; the Astrophysics and High Energy Physics programme by MCIN (with funding from European Union NextGenerationEU, PRTR-C17I1); the Black Hole Initiative, which is funded by grants from the John Templeton Foundation (60477, 61497, 62286) and the Gordon and Betty Moore Foundation (Grant GBMF-8273) - although the opinions expressed in this work are those of the author and do not necessarily reflect the views of these Foundations; the Brinson Foundation; “la Caixa” Foundation (ID 100010434) through fellowship codes LCF/BQ/DI22/11940027 and LCF/BQ/DI22/11940030; the Canada Research Chairs (CRC) program; Chandra DD7-18089X and TM6-17006X; the China Scholarship Council; the China Postdoctoral Science Foundation fellowships (2020M671266, 2022M712084); Conicyt through Fondecyt Postdoctorado (project 3220195); Consejo Nacional de Humanidades, Ciencia y Tecnología (CONAHCYT, Mexico, projects U0004-246083, U0004-259839, F0003-272050, M0037-279006, F0003-281692, 104497, 275201, 263356, CBF2023-2024-1102, 257435); the Colfuturo Scholarship; the Consejería de Economía, Conocimiento, Empresas y Universidad of the Junta de Andalucía (grant P18-FR-1769), the Consejo Superior de Investigaciones Científicas (grant 2019AEP112); the Delaney Family via the Delaney Family John A. Wheeler Chair at Perimeter Institute; Dirección General de Asuntos del Personal Académico-Universidad Nacional Autónoma de México (DGAPA-UNAM, projects IN112820 and IN108324); the Dutch Research Council (NWO) for the VICI award (grant 639.043.513), the grant OCENW.KLEIN.113, and the Dutch Black Hole Consortium (with project No. NWA 1292.19.202) of the research programme the National Science Agenda; the Dutch National Supercomputers, Cartesius and Snellius (NWO grant 2021.013); the EACOA Fellowship awarded by the East Asia Core Observatories Association, which consists of the Academia Sinica Institute of Astronomy and Astrophysics, the National Astronomical Observatory of Japan, Center for Astronomical Mega-Science, Chinese Academy of Sciences, and the Korea Astronomy and Space Science Institute; the European Research Council (ERC) Synergy Grant “BlackHoleCam: Imaging the Event Horizon of Black Holes” (grant 610058) and Synergy Grant “BlackHolistic: Colour Movies of Black Holes: Understanding Black Hole Astrophysics from the Event Horizon to Galactic Scales” (grant 10107164); the European Union Horizon 2020 research and innovation programme under grant agreements RadioNet (No. 730562), M2FINDERS (No. 101018682) and FunFiCO (No. 777740); the European Research Council for advanced grant “JETSET: Launching, propagation and emission of relativistic jets from binary mergers and across mass scales” (grant No. 884631); the European Horizon Europe staff exchange (SE) programme HORIZON-MSCA-2021-SE-01 grant NewFunFiCO (No. 10108625); the Horizon ERC Grants 2021 programme under grant agreement No. 101040021; the FAPESP (Fundação de Amparo á Pesquisa do Estado de São Paulo) under grant 2021/01183-8; the Fondes de Recherche Nature et Technologies (FRQNT); the Fondo CAS-ANID folio CAS220010; the Generalitat Valenciana (grants APOSTD/2018/177 and ASFAE/2022/018) and GenT Program (project CIDEGENT/2018/021); the Gordon and Betty Moore Foundation (GBMF-3561, GBMF-5278, GBMF-10423); the Institute for Advanced Study; the ICSC – Centro Nazionale di Ricerca in High Performance Computing, Big Data and Quantum Computing, funded by European Union – NextGenerationEU; the Istituto Nazionale di Fisica Nucleare (INFN) sezione di Napoli, iniziative specifiche TEONGRAV; the International Max Planck Research School for Astronomy and Astrophysics at the Universities of Bonn and Cologne; the European Union NextGenerationEU" RRF M4C2 1.1 project n. 2022YAPMJH; DFG research grant “Jet physics on horizon scales and beyond” (grant No. 443220636); Joint Columbia/Flatiron Postdoctoral Fellowship (research at the Flatiron Institute is supported by the Simons Foundation); the Japan Ministry of Education, Culture, Sports, Science and Technology (MEXT; grant JPMXP1020200109); the Japan Society for the Promotion of Science (JSPS) Grant-in-Aid for JSPS Research Fellowship (JP17J08829); the Joint Institute for Computational Fundamental Science, Japan; the Key Research Program of Frontier Sciences, Chinese Academy of Sciences (CAS, grants QYZDJ-SSW-SLH057, QYZDJSSW-SYS008, ZDBS-LY-SLH011); the Leverhulme Trust Early Career Research Fellowship; the Max-Planck-Gesellschaft (MPG); the Max Planck Partner Group of the MPG and the CAS; the MEXT/JSPS KAKENHI (grants 18KK0090, JP21H01137, JP18H03721, JP18K13594, 18K03709, JP19K14761, 18H01245, 25120007, 19H01943, 21H01137, 21H04488, 22H00157, 23K03453); the MICINN Research Projects PID2019-108995GB-C22, PID2022-140888NB-C22; the MIT International Science and Technology Initiatives (MISTI) Funds; the Ministry of Science and Technology (MOST) of Taiwan (103-2119-M-001-010-MY2, 105-2112-M-001-025-MY3, 105-2119-M-001-042, 106-2112-M-001-011, 106-2119-M-001-013, 106-2119-M-001-027, 106-2923-M-001-005, 107-2119-M-001-017, 107-2119-M-001-020, 107-2119-M-001-041, 107-2119-M-110-005, 107-2923-M-001-009, 108-2112-M-001-048, 108-2112-M-001-051, 108-2923-M-001-002, 109-2112-M-001-025, 109-2124-M-001-005, 109-2923-M-001-001, 110-2112-M-001-033, 110-2124-M-001-007 and 110-2923-M-001-001); the National Science and Technology Council (NSTC) of Taiwan (111-2124-M-001-005, 112-2124-M-001-014 and 112-2112-M-003-010-MY3); the Ministry of Education (MoE) of Taiwan Yushan Young Scholar Program; the Physics Division, National Center for Theoretical Sciences of Taiwan; the National Aeronautics and Space Administration (NASA, Fermi Guest Investigator grant 80NSSC23K1508, NASA Astrophysics Theory Program grant 80NSSC20K0527, NASA NuSTAR award 80NSSC20K0645); NASA Hubble Fellowship Program Einstein Fellowship; NASA Hubble Fellowship grants HST-HF2-51431.001-A, HST-HF2-51482.001-A, HST-HF2-51539.001-A, HST-HF2-51552.001A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555; the National Institute of Natural Sciences (NINS) of Japan; the National Key Research and Development Program of China (grant 2016YFA0400704, 2017YFA0402703, 2016YFA0400702); the National Science and Technology Council (NSTC, grants NSTC 111-2112-M-001 -041, NSTC 111-2124-M-001-005, NSTC 112-2124-M-001-014); the US National Science Foundation (NSF, grants AST-0096454, AST-0352953, AST-0521233, AST-0705062, AST-0905844, AST-0922984, AST-1126433, OIA-1126433, AST-1140030, DGE-1144085, AST-1207704, AST-1207730, AST-1207752, MRI-1228509, OPP-1248097, AST-1310896, AST-1440254, AST-1555365, AST-1614868, AST-1615796, AST-1715061, AST-1716327, AST-1726637, OISE-1743747, AST-1743747, AST-1816420, AST-1935980, AST-1952099, AST-2034306, AST-2205908, AST-2307887); NSF Astronomy and Astrophysics Postdoctoral Fellowship (AST-1903847); the Natural Science Foundation of China (grants 11650110427, 10625314, 11721303, 11725312, 11873028, 11933007, 11991052, 11991053, 12192220, 12192223, 12273022, 12325302, 12303021); the Natural Sciences and Engineering Research Council of Canada (NSERC); the National Research Foundation of Korea (the Global PhD Fellowship Grant: grants NRF-2015H1A2A1033752; the Korea Research Fellowship Program: NRF-2015H1D3A1066561; Brain Pool Program: RS-2024-00407499; Basic Research Support Grant 2019R1F1A1059721, 2021R1A6A3A01086420, 2022R1C1C1005255, 2022R1F1A1075115); Netherlands Research School for Astronomy (NOVA) Virtual Institute of Accretion (VIA) postdoctoral fellowships; NOIRLab, which is managed by the Association of Universities for Research in Astronomy (AURA) under a cooperative agreement with the National Science Foundation; Onsala Space Observatory (OSO) national infrastructure, for the provisioning of its facilities/observational support (OSO receives funding through the Swedish Research Council under grant 2017-00648); the Perimeter Institute for Theoretical Physics (research at Perimeter Institute is supported by the Government of Canada through the Department of Innovation, Science and Economic Development and by the Province of Ontario through the Ministry of Research, Innovation and Science); the Portuguese Foundation for Science and Technology (FCT) grants (Individual CEEC program - 5th edition, <https://doi.org/10.54499/UIDB/04106/2020>, <https://doi.org/10.54499/UIDP/04106/2020>, PTDC/FIS-AST/3041/2020, CERN/FIS-PAR/0024/2021, 2022.04560.PTDC); the Princeton Gravity Initiative; the Spanish Ministerio de Ciencia e Innovación (grants PGC2018-098915-B-C21, AYA2016-80889-P, PID2019-108995GB-C21, PID2020-117404GB-C21, RYC2023-042988-I); the University of Pretoria for financial aid in the provision of the new Cluster Server nodes and SuperMicro (USA) for a SEEDING GRANT approved toward these nodes in 2020; the Shanghai Municipality orientation program of basic research for international scientists (grant no. 22JC1410600); the Shanghai Pilot Program for Basic Research, Chinese Academy of Science, Shanghai Branch (JCYJ-SHFY-2021-013); the Simons Foundation (grant 00001470); the State Agency for Research of the Spanish MCIU through the “Center of Excellence Severo Ochoa” award for the Instituto de Astrofísica de Andalucía (SEV-2017- 0709); the Spanish Ministry for Science and Innovation grant CEX2021-001131-S funded by MCIN/AEI/10.13039/501100011033; the Spinoza Prize SPI 78-409; the South African Research Chairs Initiative, through the South African Radio Astronomy Observatory (SARAO, grant ID 77948), which is a facility of the National Research Foundation (NRF), an agency of the Department of Science and Innovation (DSI) of South Africa; the Swedish Research Council (VR); the Taplin Fellowship; the Toray Science Foundation; the UK Science and Technology Facilities Council (grant no. ST/X508329/1); the US Department of Energy (USDOE) through the Los Alamos National Laboratory (operated by Triad National Security, LLC, for the National Nuclear Security Administration of the USDOE, contract 89233218CNA000001); and the YCAA Prize Postdoctoral Fellowship. This work was also supported by the National Research Foundation of Korea (NRF) grant funded by the Korea government(MSIT) (RS-2024-00449206). We acknowledge support from the Coordenação de Aperfeiçoamento de Pessoal de Nível Superior (CAPES) of Brazil through PROEX grant number 88887.845378/2023-00. We acknowledge financial support from Millenium Nucleus NCN23_002 (TITANs) and Comité Mixto ESO-Chile.

We thank the staff at the participating observatories, correlation centers, and institutions for their enthusiastic support. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00013.E. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The NRAO is a facility of the NSF operated under cooperative agreement by AUI. This research used resources of the Oak Ridge Leadership Computing Facility at the Oak Ridge National Laboratory, which is supported by the Office of Science of the U.S. Department of Energy under contract No. DE-AC05-00OR22725; the ASTROVIVES FEDER infrastructure, with project code IDIFEDER-2021-086; the computing cluster of Shanghai VLBI correlator supported by the Special Fund for Astronomy from the Ministry of Finance in China; We also thank the Center for Computational Astrophysics, National Astronomical Observatory of Japan. This work was supported by FAPESP (Fundacao de Amparo a Pesquisa do Estado de Sao Paulo) under grant 2021/01183-8.

APEX is a collaboration between the Max-Planck-Institut für Radioastronomie (Germany), ESO, and the Onsala Space Observatory (Sweden). The SMA is a joint project between the SAO and ASIAA and is funded by the Smithsonian Institution and the Academia Sinica. The JCMT is operated by the East Asian Observatory on behalf of the NAOJ, ASIAA, and KASI, as well as the Ministry of Finance of China, Chinese Academy of Sciences, and the National Key Research and Development Program (No. 2017YFA0402700) of China and Natural Science Foundation of China grant 11873028. Additional funding support for the JCMT is provided by the Science and Technologies Facility Council (UK) and participating universities in the UK and Canada. The LMT is a project operated by the Instituto Nacional de Astrófisica, Óptica, y Electrónica (Mexico) and the University of Massachusetts at Amherst (USA). The IRAM 30-m telescope on Pico Veleta, Spain is operated by IRAM and supported by CNRS (Centre National de la Recherche Scientifique, France), MPG (Max-Planck-Gesellschaft, Germany), and IGN (Instituto Geográfico Nacional, Spain). The SMT is operated by the Arizona Radio Observatory, a part of the Steward Observatory of the University of Arizona, with financial support of operations from the State of Arizona and financial support for instrumentation development from the NSF. Support for SPT participation in the EHT is provided by the National Science Foundation through award OPP-1852617 to the University of Chicago. Partial support is also provided by the Kavli Institute of Cosmological Physics at the University of Chicago. The SPT hydrogen maser was provided on loan from the GLT, courtesy of ASIAA.

This work used the Extreme Science and Engineering Discovery Environment (XSEDE), supported by NSF grant ACI-1548562, and CyVerse, supported by NSF grants DBI-0735191, DBI-1265383, and DBI-1743442. XSEDE Stampede2 resource at TACC was allocated through TG-AST170024 and TG-AST080026N. XSEDE JetStream resource at PTI and TACC was allocated through AST170028. This research is part of the Frontera computing project at the Texas Advanced Computing Center through the Frontera Large-Scale Community Partnerships allocation AST20023. Frontera is made possible by National Science Foundation award OAC-1818253. This research was done using services provided by the OSG Consortium (cite: osg07; osg09), which is supported by the National Science Foundation award Nos. 2030508 and 1836650. Additional work used ABACUS2.0, which is part of the eScience center at Southern Denmark University, and the Kultrun Astronomy Hybrid Cluster (projects Conicyt Programa de Astronomia Fondo Quimal QUIMAL170001, Conicyt PIA ACT172033, Fondecyt Iniciacion 11170268, Quimal 220002). Simulations were also performed on the SuperMUC cluster at the LRZ in Garching, on the LOEWE cluster in CSC in Frankfurt, on the HazelHen cluster at the HLRS in Stuttgart, and on the Pi2.0 and Siyuan Mark-I at Shanghai Jiao Tong University. The computer resources of the Finnish IT Center for Science (CSC) and the Finnish Computing Competence Infrastructure (FCCI) project are acknowledged. This research was enabled in part by support provided by Compute Ontario (http://computeontario.ca), Calcul Quebec (http://www.calculquebec.ca), and the Digital Research Alliance of Canada (https://alliancecan.ca/en).

The EHTC has received generous donations of FPGA chips from Xilinx Inc., under the Xilinx University Program. The EHTC has benefited from technology shared under open-source license by the Collaboration for Astronomy Signal Processing and Electronics Research (CASPER). The EHT project is grateful to T4Science and Microsemi for their assistance with hydrogen masers. This research has made use of NASA’s Astrophysics Data System. We gratefully acknowledge the support provided by the extended staff of the ALMA, from the inception of the ALMA Phasing Project through the observational campaigns of 2017 and 2018. We would like to thank A. Deller and W. Brisken for EHT-specific support with the use of DiFX. We thank Martin Shepherd for the addition of extra features in the Difmap software that were used for the CLEAN imaging results presented in this paper. We acknowledge the significance that Maunakea, where the SMA and JCMT EHT stations are located, has for the indigenous Hawaiian people.

51 natexlab

(ref: Agudo2018) Agudo, I., Thum, C., Ramakrishnan, V., et al. 2018, MNRAS, 473, 1850

(ref: Algaba2016) Algaba, J. C., Asada, K., & Nakamura, M. 2016, ApJ, 823, 86

(ref: Biretta1999) Biretta, J. A., Sparks, W. B., & Macchetto, F. 1999, ApJ, 520, 621

(ref: BlandfordKonigl1979) Blandford, R. D. & Königl, A. 1979, ApJ, 232, 34

(ref: Bower2018) Bower, G. C., Broderick, A., Dexter, J., et al. 2018, ApJ, 868, 101

(ref: Briggs1995) Briggs, D. S. 1995, in American Astronomical Society Meeting Abstracts, Vol. 187, American Astronomical Society Meeting Abstracts, 112.02

(ref: Cheung2007) Cheung, C. C., Harris, D. E., & Stawarz, Ł. 2007, ApJL, 663, L65

(ref: Contopoulos2022) Contopoulos, I., Myserlis, I., Kazanas, D., & Nathanail, A. 2022, Galaxies, 10, 80

(ref: APP2B7) Crew, G. B., Goddi, C., Matthews, L. D., et al. 2023, PASP, 135, 025002

(ref: Doi2013) Doi, A., Hada, K., Nagai, H., et al. 2013, in European Physical Journal Web of Conferences, Vol. 61, European Physical Journal Web of Conferences, 08008

(ref: EHT2024_1) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2024a, ApJL, 964, L25

(ref: EHT2024) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2024b, A&A, 681, A79

(ref: EHT_2023) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2023, ApJL, 957, L20

(ref: EHTC2022_1) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2022a, ApJL, 930, L12

(ref: EHTC2022_2) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2022b, ApJL, 930, L13

(ref: EHTC2022_3) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2022c, ApJL, 930, L14

(ref: EHTC2022_4) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2022d, ApJL, 930, L15

(ref: EHTC2022_6) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2022e, ApJL, 930, L17

(ref: EHTC2019_1) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2019a, ApJL, 875, L1

(ref: EHTC2019_2) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2019b, ApJL, 875, L2

(ref: EHTC2019_3) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2019c, ApJL, 875, L3

(ref: EHTC2019_4) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2019d, ApJL, 875, L4

(ref: EHTC2019_5) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2019e, ApJL, 875, L6

(ref: EHTC2019_6) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2019f, ApJL, 875, L5

(ref: EHTC2022_5) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2022f, ApJL, 930, L16

(ref: EHT2021_1) Event Horizon Telescope Collaboration, Akiyama, K., Algaba, J. C., et al. 2021a, ApJL, 910, L12

(ref: EHT2021_2) Event Horizon Telescope Collaboration, Akiyama, K., Algaba, J. C., et al. 2021b, ApJL, 910, L13

(ref: Gabuzda2017) Gabuzda, D. C., Roche, N., Kirwan, A., et al. 2017, MNRAS, 472, 1792

(ref: Giroletti2012) Giroletti, M., Hada, K., Giovannini, G., et al. 2012, A&A, 538, L10

(ref: Goddi2019) Goddi, C., Crew, G., Impellizzeri, V., et al. 2019a, The Messenger, 177, 25

(ref: Goddi2021) Goddi, C., Martı́-Vidal, I., Messias, H., et al. 2021, ApJL, 910, L14

(ref: QA2Paper) Goddi, C., Martı́-Vidal, I., Messias, H., et al. 2019b, PASP, 131, 075003

(ref: Hovatta2019) Hovatta, T., O’Sullivan, S., Martı́-Vidal, I., Savolainen, T., & Tchekhovskoy, A. 2019, A&A, 623, A111

(ref: Kravchenko2020) Kravchenko, E., Giroletti, M., Hada, K., et al. 2020, A&A, 637, L6

(ref: Laing1980) Laing, R. A. 1980, MNRAS, 193, 439

(ref: Lee2015) Lee, S.-S., Kang, S., Byun, D.-Y., et al. 2015, ApJL, 808, L26

(ref: IMV2015) Martı́-Vidal, I., Muller, S., Vlemmings, W., Horellou, C., & Aalto, S. 2015, Science, 348, 311

(ref: PCPaper) Martı́-Vidal, I., Roy, A., Conway, J., & Zensus, A. J. 2016, A&A, 587, A143

(ref: UVMULTIFIT) Martı́-Vidal, I., Vlemmings, W. H. T., Muller, S., & Casey, S. 2014, A&A, 563, A136

(ref: app2_report_2024) Matthews, L. D. & Crew, G. B. 2024, Enabling New Science with the ALMA Phasing System – Phase 2 (APP2), [Version 4.1](https://science.nrao.edu/facilities/alma/science_sustainability/APP2_Final_Report_v4.1.pdf)

(ref: APPPaper) Matthews, L. D., Crew, G. B., Doeleman, S. S., et al. 2018, PASP, 130, 015002

(ref: Mizuno2015) Mizuno, Y., Gómez, J. L., Nishikawa, K.-I., et al. 2015, ApJ, 809, 38

(ref: Myserlis2021) Myserlis, I. & Contopoulos, I. 2021, A&A, 649, A94

(ref: Nagai2016) Nagai, H., Nakanishi, K., Paladino, R., et al. 2016, ApJ, 824, 132

(ref: Pasetto2021) Pasetto, A., Carrasco-González, C., Gómez, J. L., et al. 2021, ApJL, 923, L5

(ref: Peng2024) Peng, S., Lu, R.-S., Goddi, C., et al. 2024, ApJ, 975, 103

(ref: Plambeck2014) Plambeck, R. L., Bower, G. C., Rao, R., et al. 2014, ApJ, 797, 66

(ref: Raymond2024) Raymond, A. W., Doeleman, S. S., Asada, K., et al. 2024, AJ, 168, 130

(ref: Remijan2019) Remijan, A., Biggs, A., Cortes, P., et al. 2019, ALMA Technical Handbook

(ref: Taylor2009) Taylor, A. R., Stil, J. M., & Sunstrum, C. 2009, ApJ, 702, 1230

(ref: Tchekhovskoy2011) Tchekhovskoy, A., Narayan, R., & McKinney, J. C. 2011, MNRAS, 418, L79

# Stokes parameters per ALMA frequency band (SPW)

Table [\[tab:EHT_uvmf_RM\]](#tab:EHT_uvmf_RM) in the main text reports the polarization quantities averaged across the four SPWs. Here we report the polarimetric quantities (Stokes $IQUV$, LP, and EVPA) for each SPW in Table [\[tab:EHT_uvmf_spw\]](#tab:EHT_uvmf_spw). The quoted uncertainties include the thermal error, the $1\sigma$ systematic error associated with Stokes $I$ leakage into Stokes $Q$, $U$ (0.03% of Stokes $I$), and Stokes $V$ (0.6% of Stokes $I$), as recommended by the ALMA observatory (cite: Remijan2019). The total uncertainties are computed by combining these contributions in quadrature. The uncertainty in LP is primarily dominated by systematic errors, except for the weakest sources, where thermal noise becomes significant. Unlike (cite: Goddi2021), we did not apply an LP bias correction because our sample does not include low-polarization sources with LP$<<1$%. We note that Stokes $V$ is assumed to be zero during polarization calibration (cite: QA2Paper), and no additional calibration step was applied to reliably constrain circular polarization (CP) in this experiment. Consequently, we do not claim CP detections for the observed sources. For an assessment of the reliability of Stokes $V$ detections in interferometric observations using linearly polarized feeds, we refer the reader to Appendix G in (cite: Goddi2021).

+:---------:+:-------------------:+:-----------------:+:------------------:+:---------------:+:----------------:+:-------------------:+
| Frequency | I                   | Q                 | U                  | V               | LP               | EVPA                |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| (GHz)     | (Jy)                | (mJy)             | (mJy)              | (mJy)           | (%)              | (deg)               |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| VLBI scans                                                                                                                          |
+-------------------------------------------------------------------------------------------------------------------------------------+
| 3C279                                                                                                                               |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 335.60    | 8.8086 $\pm$ 0.0003 | -63.2 $\pm$ 2.6   | -923.0 $\pm$ 2.6   | -52 $\pm$ 53    | 10.50 $\pm$ 0.03 | -46.960 $\pm$ 0.082 |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 337.54    | 8.7961 $\pm$ 0.0003 | -59.9 $\pm$ 2.6   | -927.2 $\pm$ 2.6   | -49 $\pm$ 53    | 10.56 $\pm$ 0.03 | -46.849 $\pm$ 0.081 |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 347.60    | 8.6754 $\pm$ 0.0003 | -50.1 $\pm$ 2.6   | -929.0 $\pm$ 2.6   | -43 $\pm$ 52    | 10.72 $\pm$ 0.03 | -46.542 $\pm$ 0.080 |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 349.60    | 8.6327 $\pm$ 0.0003 | -48.2 $\pm$ 2.6   | -923.8 $\pm$ 2.6   | -53 $\pm$ 52    | 10.72 $\pm$ 0.03 | -46.492 $\pm$ 0.080 |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 3C273                                                                                                                               |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 335.60    | 4.2364 $\pm$ 0.0001 | -45.4 $\pm$ 1.3   | -53.1 $\pm$ 1.3    | -44 $\pm$ 25    | 1.65 $\pm$ 0.03  | -65.28 $\pm$ 0.52   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 337.54    | 4.2165 $\pm$ 0.0001 | -45.1 $\pm$ 1.3   | -54.2 $\pm$ 1.3    | -41 $\pm$ 25    | 1.67 $\pm$ 0.03  | -64.88 $\pm$ 0.52   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 347.60    | 4.1226 $\pm$ 0.0001 | -41.1 $\pm$ 1.2   | -55.0 $\pm$ 1.2    | -36 $\pm$ 25    | 1.67 $\pm$ 0.03  | -63.39 $\pm$ 0.52   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 349.60    | 4.1019 $\pm$ 0.0002 | -40.9 $\pm$ 1.2   | -55.4 $\pm$ 1.2    | -43 $\pm$ 25    | 1.68 $\pm$ 0.03  | -63.22 $\pm$ 0.52   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| M87                                                                                                                                 |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 335.60    | 0.9944 $\pm$ 0.0002 | 25.22 $\pm$ 0.34  | 12.04 $\pm$ 0.34   | -14.9 $\pm$ 6.0 | 2.81 $\pm$ 0.03  | 12.76 $\pm$ 0.35    |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 337.54    | 0.9881 $\pm$ 0.0002 | 25.33 $\pm$ 0.33  | 12.03 $\pm$ 0.33   | -14.3 $\pm$ 5.9 | 2.84 $\pm$ 0.03  | 12.70 $\pm$ 0.34    |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 347.60    | 0.9526 $\pm$ 0.0002 | 24.00 $\pm$ 0.32  | 11.37 $\pm$ 0.33   | -12.2 $\pm$ 5.7 | 2.79 $\pm$ 0.03  | 12.67 $\pm$ 0.35    |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 349.60    | 0.9451 $\pm$ 0.0002 | 23.66 $\pm$ 0.33  | 10.79 $\pm$ 0.33   | -13.6 $\pm$ 5.7 | 2.75 $\pm$ 0.04  | 12.26 $\pm$ 0.37    |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 4C01.28                                                                                                                             |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 335.60    | 1.5159 $\pm$ 0.0002 | 32.89 $\pm$ 0.50  | -126.68 $\pm$ 0.50 | 1.0 $\pm$ 9.1   | 8.63 $\pm$ 0.03  | -37.72 $\pm$ 0.11   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 337.54    | 1.5102 $\pm$ 0.0002 | 32.80 $\pm$ 0.49  | -126.78 $\pm$ 0.49 | 1.0 $\pm$ 9.1   | 8.67 $\pm$ 0.03  | -37.75 $\pm$ 0.11   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 347.60    | 1.4915 $\pm$ 0.0002 | 32.61 $\pm$ 0.49  | -125.31 $\pm$ 0.49 | 1.1 $\pm$ 8.9   | 8.68 $\pm$ 0.03  | -37.71 $\pm$ 0.11   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 349.60    | 1.4906 $\pm$ 0.0002 | 32.67 $\pm$ 0.50  | -125.56 $\pm$ 0.50 | 1.3 $\pm$ 8.9   | 8.70 $\pm$ 0.03  | -37.71 $\pm$ 0.11   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| J1146+3958                                                                                                                          |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 335.60    | 0.4007 $\pm$ 0.0003 | -10.78 $\pm$ 0.29 | 1.24 $\pm$ 0.29    | -7.0 $\pm$ 2.4  | 2.71 $\pm$ 0.07  | 86.73 $\pm$ 0.76    |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 337.54    | 0.3975 $\pm$ 0.0002 | -10.65 $\pm$ 0.27 | 1.34 $\pm$ 0.27    | -6.2 $\pm$ 2.4  | 2.70 $\pm$ 0.07  | 86.42 $\pm$ 0.71    |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 347.60    | 0.3921 $\pm$ 0.0003 | -10.49 $\pm$ 0.28 | 0.79 $\pm$ 0.27    | -5.8 $\pm$ 2.4  | 2.68 $\pm$ 0.07  | 87.85 $\pm$ 0.74    |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 349.60    | 0.3953 $\pm$ 0.0003 | -10.03 $\pm$ 0.30 | 0.67 $\pm$ 0.30    | -7.0 $\pm$ 2.4  | 2.54 $\pm$ 0.08  | 88.08 $\pm$ 0.86    |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| J1512-0905                                                                                                                          |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 335.60    | 1.7563 $\pm$ 0.0004 | -12.30 $\pm$ 0.63 | -14.67 $\pm$ 0.62  | -18 $\pm$ 10    | 1.09 $\pm$ 0.04  | -64.99 $\pm$ 0.94   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 337.54    | 1.7541 $\pm$ 0.0003 | -11.27 $\pm$ 0.61 | -14.16 $\pm$ 0.61  | -16 $\pm$ 10    | 1.03 $\pm$ 0.03  | -64.25 $\pm$ 0.97   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 347.60    | 1.7340 $\pm$ 0.0004 | -12.91 $\pm$ 0.61 | -14.21 $\pm$ 0.61  | -14 $\pm$ 10    | 1.11 $\pm$ 0.04  | -66.14 $\pm$ 0.92   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 349.60    | 1.7254 $\pm$ 0.0004 | -12.90 $\pm$ 0.63 | -12.91 $\pm$ 0.63  | -18 $\pm$ 10    | 1.06 $\pm$ 0.04  | -67.48 $\pm$ 0.99   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| J1337-1257                                                                                                                          |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 335.60    | 3.1590 $\pm$ 0.0004 | 505.4 $\pm$ 1.0   | -132.5 $\pm$ 1.0   | -105 $\pm$ 19   | 16.54 $\pm$ 0.03 | -7.344 $\pm$ 0.055  |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 337.54    | 3.1469 $\pm$ 0.0004 | 504.46 $\pm$ 0.99 | -129.79 $\pm$ 0.99 | -99 $\pm$ 19    | 16.55 $\pm$ 0.03 | -7.214 $\pm$ 0.055  |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 347.60    | 3.1199 $\pm$ 0.0004 | 508.98 $\pm$ 0.99 | -132.01 $\pm$ 0.99 | -88 $\pm$ 19    | 16.85 $\pm$ 0.03 | -7.270 $\pm$ 0.054  |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 349.60    | 3.1042 $\pm$ 0.0004 | 503.87 $\pm$ 1.00 | -133.33 $\pm$ 1.00 | -104 $\pm$ 19   | 16.79 $\pm$ 0.03 | -7.411 $\pm$ 0.055  |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| non-VLBI scans$^{a}$                                                                                                                |
+-------------------------------------------------------------------------------------------------------------------------------------+
| J1246-0730                                                                                                                          |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 335.60    | 0.2826 $\pm$ 0.0003 | 1.50 $\pm$ 0.36   | -0.49 $\pm$ 0.36   | 0.7 $\pm$ 1.7   | 0.6 $\pm$ 0.1    | -9.1 $\pm$ 6.5      |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 337.54    | 0.2822 $\pm$ 0.0003 | 1.35 $\pm$ 0.35   | -1.03 $\pm$ 0.35   | 0.5 $\pm$ 1.7   | 0.6 $\pm$ 0.1    | -18.6 $\pm$ 6.0     |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 347.60    | 0.2776 $\pm$ 0.0004 | 1.16 $\pm$ 0.36   | -1.25 $\pm$ 0.36   | 0.0 $\pm$ 1.7   | 0.6 $\pm$ 0.1    | -23.5 $\pm$ 6.1     |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 349.60    | 0.2761 $\pm$ 0.0004 | 1.17 $\pm$ 0.38   | -0.76 $\pm$ 0.38   | 0.4 $\pm$ 1.7   | 0.5 $\pm$ 0.1    | -16.6 $\pm$ 7.9     |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 4C01.28                                                                                                                             |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 335.60    | 1.5126 $\pm$ 0.0002 | 33.13 $\pm$ 0.52  | -126.08 $\pm$ 0.52 | -0.0 $\pm$ 9.1  | 8.62 $\pm$ 0.03  | -37.64 $\pm$ 0.11   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 337.54    | 1.5079 $\pm$ 0.0002 | 32.94 $\pm$ 0.52  | -126.40 $\pm$ 0.52 | -0.0 $\pm$ 9.1  | 8.66 $\pm$ 0.03  | -37.70 $\pm$ 0.11   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 347.60    | 1.4920 $\pm$ 0.0003 | 32.82 $\pm$ 0.51  | -125.19 $\pm$ 0.51 | 0.1 $\pm$ 9.0   | 8.67 $\pm$ 0.03  | -37.66 $\pm$ 0.11   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+
| 349.60    | 1.4906 $\pm$ 0.0003 | 32.66 $\pm$ 0.52  | -125.53 $\pm$ 0.52 | 0.1 $\pm$ 8.9   | 8.70 $\pm$ 0.03  | -37.71 $\pm$ 0.12   |
+-----------+---------------------+-------------------+--------------------+-----------------+------------------+---------------------+

# Comparison of Stokes parameters with the AMAPOLA polarimetric Grid Survey

Figures [4](#fig:stokescomp_gs_1) and [5](#fig:stokescomp_gs_2) illustrate the polarimetric parameters reported in Table [\[tab:EHT_uvmf_spw\]](#tab:EHT_uvmf_spw) (green data points and error bars), specifically Stokes $I$, $Q$, $U$, LP, and EVPA. The shaded $\pm1\sigma$ regions represent the time-variance of the same parameters as measured by AMAPOLA over a 20-day period surrounding the VLBI observations (April 9 to 29, 2021). Inflections in the shaded trend lines indicate the times of GS observations. Blue corresponds to Band 3 measurements, while green and red corresponds to Bands 6 and 7, respectively. The figures show that most Band 7 measurements derived from our current study fall within the red-shaded regions, demonstrating general consistency with the AMAPOLA trends. The observed discrepancies may align with inter-GS cadence variability or differential time-variability between frequency bands, as also seen in some AMAPOLA monitoring cases.

We conclude that, despite differences in array configurations and data reduction methods, the ALMA-VLBI results are consistent with AMAPOLA. This consistency validates the accuracy of flux density and polarization calibration in VLBI mode for Band 7, extending the reliability previously demonstrated in Bands 3 and 6 (cite: QA2Paper; Goddi2021).

![image](./figs/amapola/3C279_i_2021) ![image](./figs/amapola/3C273_i_2021) ![image](./figs/amapola/4C01.28_i_2021)

![image](./figs/amapola/3C279_q_2021) ![image](./figs/amapola/3C273_q_2021) ![image](./figs/amapola/4C01.28_q_2021)

![image](./figs/amapola/3C279_u_2021) ![image](./figs/amapola/3C273_u_2021) ![image](./figs/amapola/4C01.28_u_2021)

![image](./figs/amapola/3C279_lp_2021) ![image](./figs/amapola/3C273_lp_2021) ![image](./figs/amapola/4C01.28_lp_2021)

![image](./figs/amapola/3C279_evpa_2021) ![image](./figs/amapola/3C273_evpa_2021) ![image](./figs/amapola/4C01.28_evpa_2021)

![image](./figs/amapola/J1337-1257_i_2021) ![image](./figs/amapola/J1512-0905_i_2021) ![image](./figs/amapola/J1146+3958_i_2021) ![image](./figs/amapola/J1246-0730_i_2021)

![image](./figs/amapola/J1337-1257_q_2021) ![image](./figs/amapola/J1512-0905_q_2021) ![image](./figs/amapola/J1146+3958_q_2021) ![image](./figs/amapola/J1246-0730_q_2021)

![image](./figs/amapola/J1337-1257_u_2021) ![image](./figs/amapola/J1512-0905_u_2021) ![image](./figs/amapola/J1146+3958_u_2021) ![image](./figs/amapola/J1246-0730_u_2021)

![image](./figs/amapola/J1337-1257_lp_2021) ![image](./figs/amapola/J1512-0905_lp_2021) ![image](./figs/amapola/J1146+3958_lp_2021) ![image](./figs/amapola/J1246-0730_lp_2021)

![image](./figs/amapola/J1337-1257_evpa_2021) ![image](./figs/amapola/J1512-0905_evpa_2021) ![image](./figs/amapola/J1146+3958_evpa_2021) ![image](./figs/amapola/J1246-0730_evpa_2021)

[^1]: These ALMA commissioning data are made public with this publication.

[^2]: The Local Oscillator setup at ALMA does not allow evenly spaced basebands in Band 7, unlike in VLBI’s Band 6.

[^3]: The `deconvolver=‘mtmfs’` configuration outperformed `deconvolver=‘hogbom’` when combining all four SPWs, yielding 30–40% better sensitivity on average, as expected for RMS $\propto 1/\sqrt{\Delta \nu}$. However, `deconvolver=‘hogbom’` performed poorly when combining all four SPWs, especially for sources with steep spectral indices, resulting in up to 50% worse RMS compared to `deconvolver=‘mtmfs’`.

[^4]: <http://www.alma.cl/~skameno/AMAPOLA/>

[^5]: The $\sigma$ error on the polarized flux includes the thermal error (residual image rms noise) and the systematic error (added in quadrature) associated with Stokes $I$ leakage onto Stokes $Q$ and $U$ (0.03% of Stokes $I$).

[^6]: Images for other targets are not included, as they remain unresolved on arcsecond scales and do not provide additional information beyond what is already summarized in Table [\[tab:EHT_uvmf_RM\]](#tab:EHT_uvmf_RM).

[^7]: <https://www.nrao.edu/archives/items/show/33382>

</paper>

Write the methods card for this paper.