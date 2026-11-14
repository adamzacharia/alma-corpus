# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...681A..82G\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...681A..82G",
 "title": "IRAS4A1: Multiwavelength continuum analysis of a very flared Class 0 disk",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Guerra-Alvarado, O. M.",
 "n_authors": 10,
 "arxiv_id": "2310.11999",
 "doi": "10.1051/0004-6361/202347685",
 "alma_projects_linked_by_archive": [
  "2018.1.00510.S"
 ]
}
```

Paper text:
<paper>
# IRAS4A1: Multi-wavelength continuum analysis of a very flared Class 0 disk

Understanding the formation of substructures in protoplanetary disks is vital for gaining insights into dust growth and the process of planet formation. Studying these substructures in highly embedded Class 0 objects using the Atacama Large Millimeter/submillimeter Array (ALMA), however, poses significant challenges. Nonetheless, it is imperative to do so to unravel the mechanisms and timing behind the formation of these substructures.

In this study, we present high-resolution ALMA data at Bands 6 and 4 of the NGC1333 IRAS4A Class 0 protobinary system. This system consists of two components, A1 and A2, separated by 1.8" and located in the Perseus molecular cloud at $\sim$293 pc distance.

To gain a comprehensive understanding of the dust properties and formation of substructures in the early stages, we conducted a multi-wavelength analysis of IRAS4A1. Additionally, we sought to address whether the lack of observed substructures in very young disks, could be attributed to factors such as high degrees of disk flaring and large scale heights. To explore this phenomenon, we employed radiative transfer models using RADMC-3D. We employed different approaches and compared the model outcomes with our observational data. This comparison allowed us to gain insights into the challenges in detecting substructures in nascent disks and shed light on the potential influence of the dust scale height on observations of protoplanetary disks.

The continuum data revealed the presence of two disks/envelopes around A1 and A2, along with structure connecting the two sources. Furthermore, spectral index measurements indicate lower optical depth within the A2 disk compared to A1. Our multi-wavelength analysis of A1 discovered characteristics such as high dust surface density, substantial dust mass within the disk, and elevated dust temperatures. These findings suggest the presence of large dust grains compared to the ones in the interstellar medium (ISM), greater than 100 microns in size within the region. By employing RADMC-3D, we confirmed that increasing the scale height creates the appearance of an asymmetry in protoplanetary disks. Our findings indicate that a scale height of at least 0.3 (H/R) is necessary to produce this observed asymmetry. Furthermore, while there’s no direct detection of any substructure, our models indicate that some, such as a small gap, must be present. However, reproducing the intensity profile along the major and minor axes necessitates considering other processes that may be occurring within the IRAS4A1 disk. In summary, this result implies that disk substructures may be masked or obscured by a large scale height in combination with a high degree of flaring in Class 0 disks.

# Introduction

+:--------------:+:------------------:+:-------:+:---------------:+:-------:+:-----------:+:-----------:+:-------:+:-------:+:-------:+:-------:+
| Project        |                    | ALMA    | Repr.           | ToS     |             | Sensitivity | Rms     | Min BL  | Max BL  | BW      |
+----------------+--------------------+---------+-----------------+---------+-------------+-------------+---------+---------+---------+---------+
| Code           | P.I                | Band    | Frequency (GHz) | \(s\)   | Array       | (mJy)       | (mJy)   | \(m\)   | \(m\)   | (GHz)   |
+----------------+--------------------+---------+-----------------+---------+-------------+-------------+---------+---------+---------+---------+
| Long baseline observations                                                                                                                    |
+----------------+--------------------+---------+-----------------+---------+-------------+-------------+---------+---------+---------+---------+
| 2018.1.00510.S | James Di Francesco | 6       | 265.88          | 7111    | TM1(C43-8)  | 0.0220      | 0.10    | 92.1    | 8547.6  | 248-268 |
+----------------+--------------------+---------+-----------------+---------+-------------+-------------+---------+---------+---------+---------+
| 2018.1.00510.S | James Di Francesco | 4       | 140.84          | 8913    | TM1(C43-9)  | 0.017       | 0.013   | 83.1    | 16196.3 | 136-154 |
+----------------+--------------------+---------+-----------------+---------+-------------+-------------+---------+---------+---------+---------+
| Short baseline observations                                                                                                                   |
+----------------+--------------------+---------+-----------------+---------+-------------+-------------+---------+---------+---------+---------+
| 2018.1.00510.S | James Di Francesco | 6       | 265.88          | 3267    | TM2 (C43-5) | 0.04690     | 0.02050 | 15.1    | 2617.4  | 248-268 |
+----------------+--------------------+---------+-----------------+---------+-------------+-------------+---------+---------+---------+---------+
| 2018.1.00510.S | James Di Francesco | 4       | 140.84          | 3125    | TM2 (C43-6) | 0.037       | 0.045   | 15      | 2516.9  | 136-154 |
+----------------+--------------------+---------+-----------------+---------+-------------+-------------+---------+---------+---------+---------+
|                |                    |         |                 |         |             |             |         |         |         |         |
+----------------+--------------------+---------+-----------------+---------+-------------+-------------+---------+---------+---------+---------+

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  | Central | Central | Synthesized beam |  |  |  |  |  |  |
|  | Frequency | Wavelength | Major $\times$ minor | Beam P.A. | rms | Peak flux A1 | Peak flux A2 | Robust | Peak SNR |
| Band | (GHz) | \(mm\) | (mas $\times$ mas) | (deg) | ($\mu$Jy/beam) | (mJy/beam) | (mJy/beam) |  |  |
| 6 | 256.994 | 1.2 | 78 $\times$ 31 | 20.82 | 135.299 | 14.04 | 19.92 | 0.0 | 147.5 |
| 4 | 145.009 | 2.1 | 47$\times$29 | 5.79 | 26.27 | 3.13 | 2.63 | 0.0 | 120.4 |
| VLA Ka | 32.95 | 9.1 | 75$\times$54 | 79.94 | 9.773 | 0.719 | 0.306 | 0.5 | 80 |
|  |  |  |  |  |  |  |  |  |  |

|        |                      |                |              |              |
|:------:|:--------------------:|:--------------:|:------------:|:------------:|
|        |   Synthesized beam   |                |              |              |
|        | Major $\times$ minor |      rms       | Peak flux A1 | Peak flux A2 |
|  Band  |  (mas $\times$ mas)  | ($\mu$Jy/beam) |  (mJy/beam)  |  (mJy/beam)  |
|   6    |     78$\times$78     |     370.5      |    33.94     |    40.01     |
|   4    |     78$\times$78     |     62.53      |    13.09     |     8.17     |
| VLA Ka |     78$\times$78     |      9.89      |    0.943     |    0.355     |
|        |                      |                |              |              |

Recent studies of young stellar objects (YSOs) have concluded that dust growth from small particles to planetesimals may occur very early in the lifetime of protoplanetary disks ((cite: 2020A&A...640A..19T); (cite: 2023ASPC..534..717D)). To stop the radial drift of dust particles and allow growth to happen, dust evolution models require dust particles to be trapped within disk substructures. This requirement implies that the formation of these substructures should be well underway during the Class 0/I phase of disk evolution. While such substructures have been detected in the disks of some Class I objects ((cite: 2020Natur.586..205S); (cite: 2020Natur.586..228S)), these are still very limited in number. Moreover, they have not yet been observed in Class 0 protoplanetary disks. High-resolution studies of more evolved (Class II) protoplanetary disks, however, have revealed that substructures are common ((cite: 2015ApJ...808L...3A);(cite: 2018ApJ...869L..41A);(cite: 2016PhRvL.117y1101I); (cite: 2018ApJ...869...17L)). These substructures, such as gaps, rings, arcs in cavities, and spiral arms (e.g., (cite: 2013atnf.prop.5561C); (cite: 2013Sci...340.1199V), (cite: 2016Sci...353.1519P); (cite: 2018ApJ...869L..43H)), have proven crucial in reconciling the timescales for dust drift and planet formation, allowing larger dust particles to decelerate and grow further ((cite: 2012A&A...538A.114P)).

Many groups propose that disk substructures form due to interactions between the disk and forming planets ((cite: 2015ApJ...809...93D); (cite: 2018ApJ...869L..47Z)). Other processes, however, may also contribute to their presence ((cite: 2015A&A...574A..68F); (cite: 2015IAUGA..2256118Z); (cite: 2016ApJ...821...82O); (cite: 2018ApJ...865..102T)). The presence of substructures in evolved disks raises questions about when these substructures form and how are they linked to planet formation. The origin of these substructures, however, remains a subject of debate.

In addition to radial drift, vertical settling is another crucial process that significantly influences the evolution of dust particles in protoplanetary disks allowing them to grow and move into the mid-plane. This settling refers to the vertical motion of particles within the protoplanetary disk, driven by the balance between the gravitational force from the central star and the gas drag experienced by the particles. This settling process is influenced by several factors, including the turbulence of the disk and the sizes of the dust grains ((cite: 2004A&A...421.1075D)). In effect, larger dust grains are generally more efficient at settling due to their greater inertia, decoupling from the gas and moving into the mid-plane where they can grow further, while smaller grains experience stronger gas drag and tend to stay more mixed with the gas in higher layers of the disk ((cite: 2005A&A...443..185B)). Vertical settling is expected to occur faster than radial drift and can be particularly pronounced in the inner regions of disks ((cite: 2014MNRAS.437.3055L)).

![](Continuumallbands78mas.pdf)

In evolved Class II disks, some studies have observed that the larger dust particles are already primarily located at the mid-plane, indicating that settling has already occurred ((cite: 2016ApJ...816...25P)). On the other hand, the larger dust particles in younger disks may not have had enough time to settle completely, and the settling process may be ongoing in Class I disks with larger vertical extend ((cite: 2020A&A...642A.164V; 2023ApJ...946...70V)). Furthermore, previous studies have provided enough evidence supporting the occurrence of grain growth in Class 0 young sources, as indicated by their low millimeter spectral indices. Notably, these studies have shown that the spectral index values are larger (ranging from 3.5 to 5) within the envelope at scales extending beyond 2000 au compared to the values (\< 3.5) at smaller scales (\<200 au) ((cite: 2009AAS...21341318K);(cite: 2007ApJ...659..479J)).

More recent findings suggest that young objects, particularly Class 0 YSOs, exhibit significant degrees of flaring and have considerable scale heights ((cite: 2022ApJ...934...95S); (cite: 2022ApJ...937..104M)). This flaring and large scale height, irrespective of resolution or optical depth considerations, may conceal substructures in these systems or even prevent their formation. As a result, the settling of large particles is still ongoing, and much material remains in higher layers of the disk. More recently, a large study was performed in the eDisk survey (cite: 2023ApJ...951....8O) of Class 0/I objects with several new findings about their young disks. Understanding the dust properties, vertical structures, and evolution of substructures from the early disk stages is crucial for comprehending the onset and progression of planet formation, as dust evolution and grain growth play vital roles in that process.

In this study, we investigate the protobinary system NGC1333-IRAS4A (IRAS4A), which is situated in the Perseus molecular cloud at a distance of 293 parsecs (pc) (cite: 2018ApJ...869...83Z). The system consists of two Class 0 protostars, namely IRAS4A1 and IRAS4A2, which are separated by an angular distance of 1.8" (cite: 2018ApJ...867...43T). Both IRAS4A1 and IRAS4A2 are surrounded by an envelope with a total mass of approximately 8 $M_{\odot}$ and a total luminosity of around 5 $L_{\odot}$ (cite: 2019A&A...621A..76M). Both objects have very well-distinguished outflows (cite: 2015A&A...584A.126S). We present here the continuum emission of both A1 and A2. We aim to study the structure of IRAS4A1 and investigate the absence of substructures in this component using radiative models. Additionally, in a separate paper, we will discuss the line emission and the presence of complex organic molecules in the IRAS4A system, as well as the continuum analysis of IRAS4A2.

# Observations

![](BSIFinalA1A2.pdf)

The observations used in this paper were obtained using the Atacama Large Millimeter/submillimeter Array (ALMA). Band 4 (1.2 mm) and Band 6 (2.1 mm) data were taken as part of the project code 2018.1.00510.S (PI: James Di Francesco). The calibration of the data was performed by the ALMA staff and was restored by the allegro team at Leiden University. For Band 4, the observations were carried out in five execution blocks spanning from October 16th, 2018 to September 12th, 2021. Band 6 data were acquired in four execution blocks from November 19th, 2018 to September 30th, 2019. The total observing time on source for Band 4 was 3.34 h, while Band 6 had a total observing time of 2.88 h. Table 1 provides additional information regarding the characteristics of the data utilized in this study.

The data reduction process was carried out using the Common Astronomy Software Applications (CASA, (cite: 2007ASPC..376..127M)) version 5.7.0. The continuum spectral windows were separated from the line spectral windows and then averaged into eight channels for both data sets, Band 6 has 12 spectral windows centered at 264 Ghz, 252 GHz, and 250 Ghz with a total bandwidth of 2 GHz each. Band 4 has 15 spectral windows centered at 138 GHz, 150 Ghz, and 152 GHz with a total bandwidth of 2 GHz each. The flux calibration errors are set to the nominal values of 5$\%$ at Bands 4, 6.

Self-calibration techniques were employed for each spectral window individually using solution intervals of inf, 60s and 30s. Initially, we performed phase only self-calibration to the short baseline data which resulted in significant improvements for Band 4 data (signal-to-noise ratio, from 88 to 380). For Band 6 data, however, only an increase in the SNR from 61 to 69 was achieved. In any case, sufficient self-calibration solutions were found, leading to enhanced data quality. Amplitude self-calibration was also performed but we stopped after a single step for most of the spectral windows, as it did not yield substantial improvements in the signal-to-noise ratio. For the long baseline data, we also performed phase self-calibration, although the improvement observed was comparatively less significant than in the short baseline data (Band 4 SNR from 42 to 86 and Band 6 SNR from 16 to 19). The reason for the lesser improvement in long baselines compared to short baselines could be attributed to a higher frequency of returns to the phase calibrator source during the long-baseline observations. Additionally, since self-calibration was exclusively applied in the same configuration, the cleaning process for long-baseline data often struggles to model the largest angular scales, even though they are present. This limitation affects the visibility data, especially considering the substantial amount of large scale emission present in these data. Amplitude self-calibration was only applied to a few specific spectral windows due to minimal enhancements in the SNR. The final data sets were obtained after concatenating all the spectral windows together in which no alignment was needed for any of them.

Moreover, Very Large Array (VLA) data of IRAS4A was obtained from the VLA Nascent Disk and Multiplicity (VANDAM) survey (cite: 2016ApJ...818...73T) conducted in the Perseus molecular cloud. The observations took place on October 21, 2013, employing the B-array configuration. For the correlator setup, two basebands with a total bandwidth of 4 GHz were utilized. These basebands were centered at frequencies of 36.9 GHz and 28.5 GHz, respectively. The setup was then further divided into 32 spectral windows each having a bandwidth of 128 MHz. The VLA Ka-band data in B-configuration has a shortest baseline length of 210 m and an estimated amplitude calibration uncertainty of $\sim$10$\%$.

The final continuum images were created using task *tclean* in CASA. In addition, we used the MTMFS deconvolver (cite: 2011A&A...532A..71R) with nterms=2, together with scales of 0, 10, 30, and 50 times the pixel size (0.003" and 0.01" for ALMA and VLA images, respectively). Briggs weighting was found optimal for the purpose of this project, as it provided the best compromised between sensitivity and resolution, and several Robust values were explored when making the final images. Furthermore, for the Band 4 data, the uv range was modified to decrease the resolution. A smooth tapering was applied by setting *uvtaper* to 0.058". Both, the Band 4 and Band 6 images were convolved to have the same 78 (milliarcsecond) beam. This common resolution allowed for a consistent analysis alongside the Very Large Array (VLA) data at 9.1 mm. Table 2 and Table 3 provide an overview of the characteristics of the images for Band 4 and Band 6, along with the VLA image obtained from the VANDAM survey.

We acknowledge that the ALMA data for IRAS4A at Band 4, with its high resolution, time on source, and rms, can be favorably compared to the data obtained in the ALMA 2014 Long Baseline Campaign (LBC) Science Verification (SV) data of HL Tau at Band 6 ((cite: 2015ApJ...808L...3A)). The data for HL Tau was specifically designed to search for substructures, a goal that was also intended for the observation of IRAS4A1. The IRAS4A data set has a resolution of 47 mas, a time on source of 3.34 h and an rms of 13 $\mu$Jy, while the HL Tau data had a resolution of  35 mas, a time on source of 4.5 h and an rms of 11 $\mu$Jy. Given the numerous substructures identified in the HL Tau disk and the comparable nature of the data, one would expect these observations to be sufficient for detecting substructures in the IRAS4A1 disk.

# Results

Figure 1 displays the continuum images obtained from the observations. IRASA1 and IRAS2A2 are well resolved in both the Band 4 and Band 6 images. The majority of the submillimeter (sub-mm) emission originates from within each of these two sources. There is, however, additional faint emission observed between and surrounding A1 and A2, indicating some form of structure between the two sources. This structure is particularly evident at 2.1 mm and 1.2 mm wavelengths but not at 9.1 mm, which might be related to the lower sensitivity to thermal dust emission at 9.1 mm (see Appendix [7](#fig: Continuum Emission convolved at 78 m.a.s FE)). The origin of this extended emission remains unknown but the material could potentially be associated with the surrounding molecular cloud or with some diffuse envelope/core material at these scales. In contrast, the emission surrounding A1 or A2 is likely originating from the inner envelope or a very optically thick flared disk. Moreover, the brightness peak emission from A1 is lower than that from A2 at 1.2 mm, contrary to what is observed at 2.1 mm and 9.1 mm (see section 2 for the flux values). One possible explanation for this discrepancy could be that both sources have different scale heights and different optical depths. Despite the objects’ similar age, Band 6 may be tracing different layers in A1 and A2, possibly not corresponding to the mid-plane.

Furthermore, our ALMA images have been thoroughly examined, and no additional compact objects, such as low-mass companions or distant galaxies, have been detected within the field of view (\> 3$\sigma$). Due to the high sensitivity and resolution of our data, it’s highly improbable that any such objects have been missed. This suggests that A1 and A2 are unlikely to be part of a binary with a separation greater than 20 au, which is the long axis of the beam. However, is important to note that our data is not sensitive enough to detect a star lacking a circumstellar disk.

Lastly, a distinct asymmetry is observed for A1 in the 1.2 mm image, which is not apparent in the 2.1 mm and 9.1 mm images. The cause of this asymmetry warrants further investigation as it may provide valuable insights into the vertical structure of its Class 0 protoplanetary disk.

The radial profiles from these images were obtained by averaging the emission in elliptical rings for both sources and the central position of the radial profile of A2 was determined based on the peak emission in the respective images. Since there is an asymmetry in the A1 source, the central position of the radial profiles was determined by a Gaussian fit using *imfit*. Although a slight bias might remain in the Gaussian fit, it was considerably less pronounced than using the peak emission center. Consequently, the center from the Gaussian fit is likely much closer to the ac- tual center of the source. For A1, the inclination and position angle values were set to 20 degrees and 96 degrees (NE direction, from North axis moving towards East), respectively, as reported for the outflow in (cite: 2016ApJ...819..159C). On the other hand, for A2 we took the inclination to be 14 degrees (cite: 2016ApJ...819..159C) while the position angle was taken from measurements on the inner outflow (cite: 2021ApJ...916...82C) (122 degrees NE). Finally, the brightness temperature values were calculated by applying the full Planck equation to the radial intensity profiles as indicated by (cite: 1979rpa..book.....R), the concept refers to the temperature of a blackbody having the same brightness at that specific frequency. Moreover, two additional radial profiles were generated, representing the spectral indices between 9.1 mm and 2.1 mm, as well as between 2.1 mm and 1.2 mm. Figure 2 displays both the brightness temperature profiles and the spectral indices for A1 and A2.

By examining Figure 2, we can observe the behavior of the spectral indices for A1 and A2. For A1, the spectral indices are very low at the center of the source. As the radius increases, however, these indices gradually become larger. This continues until the noise of the 9.1 mm image starts to dominate the emission. Comparing the spectral index between 2.1 mm and 1.2 mm for A1 with that of A2, we find that the index for A1 remains consistently below 2 across most radii. On the other hand, the spectral indices for A2 are consistently above 2 throughout the range of radii considered. This discrepancy suggests that the emission from A1 is significantly more optically thick than that from A2 at these wavelengths. The difference in spectral indices between A1 and A2 implies differences in the physical properties of the two sources. For example, A1 may have a denser and more optically thick environment, which affects the observed spectral behavior. Furthermore, dust self-scattering might be affecting the inner regions of the IRAS4A1 disk. Additionally, some free-free emission might be increasing the brightness temperature in the inner regions of the A1 VLA image, affecting the spectral index between 9.1 mm - 2.1 mm.

In the recent study conducted by (cite: 2019A&A...632A...5G) using independent measurements from the CALYPSO sample at 1.3 and 3.2 mm, they reported discovering remarkably low values of spectral indices (\<2.0) within the inner regions of the IRAS4A1 envelope, specifically at distances of less than 200 au. This is in agreement with our spectral index values of the IRAS4A1 inner regions. Additionally, (cite: 2019A&A...632A...5G) also observed higher spectral indices values extending up to 2000 au, which was attributed to grain growth processes occurring within the envelope. It is crucial to acknowledge that our high-resolution image might be causing the extended component of the envelope to be resolved out, thereby making it difficult to measure the spectral index of this particular component. (cite: 2007ApJ...659..479J), previously pointed out that when extracting emission from the envelope, the spectral index of compact components would be flattened. Then, spectral index values below 3.5 at smaller radii could be indicative of the presence of another component, most likely a disk.

## Multi-wavelength analysis of a Class 0 young stellar object.

![](MWA1.pdf)

In this study, we will adopt the hypothesis that the emission detected in our high-resolution images originates primarily from a disk rather than the envelope. The reason behind this is that the high resolution of our imaging may result in the loss of most of the emission from the extended components (envelope) and that, as mentioned before, our findings of low values of the spectral indices in Figure 2 further support the notion of a disk scenario. Of course, it needs to be noted that some emission coming from the inner envelope might still be contributing to the total emission. While there might still be some confusion within the envelope, we unfortunately didn’t account for a dynamical distinction. Separating the continuum from the envelope is challenging, and due to the optical depth, analyzing the lines becomes quite limited. Additionally, to align with previous research, we will also consider the disk to be flared, similar to observations and results found in Class 0 Young Stellar Objects (YSOs) using ALMA data ((cite: 2022ApJ...934...95S);(cite: 2022ApJ...937..104M)) and as suggested by edge on observations ((cite: 2020A&A...642A.164V; 2023ApJ...946...70V)) and recently, the eDisk survey (cite: 2023ApJ...951....8O).

Protoplanetary disks are commonly expected to have millimeter or even centimeter-sized dust particles. Because of such grain growth, the albedo of the dust can be high at millimeter wavelengths, indicating that scattering plays a significant role in the opacity of the dust emission. When scattering is a dominant factor, the spectral index of the dust emission can no longer be directly associated to a spectral index of the dust opacity (i.e., $\beta$) (e.g., (cite: 2020ApJ...892..136S); (cite: 2019ApJ...877L..18Z)).To analyze the spectral energy distribution (SED) of protoplanetary disks properly, it is crucial to consider both absorption and scattering effects in the dust opacity. To include the scattering effect, we can write the source function in the radiative transfer equation as: $$\begin{eqnarray}
S_{\nu}(T)=\omega_{\nu}J_{\nu}+(1-\omega_{\nu})B_{\nu}(T),
  \label{eq: Source function with scattering}
 
\end{eqnarray}$$ where $J_{\nu}$ is the local mean intensity and $\omega_{\nu}$ is the albedo, defined by the scattering coefficient and the absorption coefficient as $\omega_{\nu}=\frac{\sigma_{\nu}}{\kappa_{\nu}+\sigma_{\nu}}$. We can approximate this to the analytical solution found in (cite: 1993Icar..106...20M) assuming a disk as a vertically isothermal slab and with isotropic scattering: $$\begin{eqnarray}
J_{\nu}=B_{\nu}(T)[1 + f(t,\tau_{\nu},\omega_{\nu})],
  \label{eq:Approximation by Miyake & Nakagawa}
 
\end{eqnarray}$$ where $$\begin{eqnarray}
f(t,\tau_{\nu},\omega_{\nu})=\frac{\exp (-\sqrt3\epsilon_{\nu}t )+\exp (\sqrt3\epsilon_{\nu}(t-\tau_{\nu})) }{\exp(-\sqrt3\epsilon_{\nu}\tau_{\nu})(\epsilon_{\nu}-1)-(\epsilon_{\nu}+1)},
  \label{eq:Approximation by Miyake & Nakagawa }
 
\end{eqnarray}$$ where $t$ is the optical depth variable and $\tau_{\nu}$ = $\Sigma_{dust}\chi_{\nu}$, where both are measured perpendicular to the disk mid-plane. Also, $\epsilon_{\nu}=\sqrt{1-\omega_{\nu}}$. Considering inclination effects by correcting the optical depth by the inclination angle ($i$) of the disk, we reach the emergent specific intensity obtained by (cite: 2019ApJ...876....7S): $$\begin{eqnarray}
I_{\nu}=B_{\nu}(T)[(1-\exp( \tau_{\nu}/\mu))+\omega_{\nu}F(\tau_{\nu},\omega_{\nu})],
  \label{eq:emergent intensity (Sierra et al. 2019)}
 
\end{eqnarray}$$ where, $$\begin{eqnarray}
F(\tau_{\nu},\omega_{\nu})=\frac{1}{\exp(-\sqrt3\epsilon_{\nu}\tau_{\nu})(\epsilon_{\nu}-1)-(\epsilon_{\nu}+1)}\textsc{x}\nonumber\\ \left [  \frac{1-\exp(-(\sqrt{3}\epsilon_{\nu}+1/\mu)\tau_{\nu})}{\sqrt{3}\epsilon_{\nu}\mu+1}+\frac{\exp(-\tau_{\nu}/\mu)-\exp(-\sqrt{3}\epsilon_{\nu}\tau_{\nu})}{\sqrt{3}\epsilon_{\nu}\mu-1}  \right ],
  \label{eq:F(tau,omega) (Sierra et al. 2019)}
 
\end{eqnarray}$$

It is important to mention that for these equations isotropic scattering is assumed, which may be an incorrect approximation for $2\pi a\geqslant \lambda$. To reduce the effect of the approximation, we replace the scattering coefficient in all equations with an effective scattering coefficient in the form ((cite: 1978JOSA...68.1368I), (cite: 2018ApJ...869L..45B)): $$\begin{eqnarray}
\sigma^{eff}_{\nu}=(1-g_{\nu})\sigma_{\nu},
  \label{eq:Effective scattering coefficient}
 
\end{eqnarray}$$ where $g_{\nu}$ is the asymmetry parameter, i.e., the expectation value of cos $\theta$, where $\theta$ is the scattering angle (e.g., (cite: 1978JOSA...68.1368I), (cite: 2018ApJ...869L..45B)). The values of $g_{\nu}$ depend on the dielectric properties of the dust particles. For our calculations, the values obtained in (cite: 2018ApJ...869L..45B) for $\sigma^{eff}_{\nu}$ were used.

In our analysis, the particle size distribution is assumed to follow a power law with a slope ($n(a)\propto a^{-p}$), where p is commonly assumed to be 3.5 according to measurements of the ISM ((cite: 1977ApJ...217..425M)). Also, the DSHARP opacity data ((cite: 2018ApJ...869L..45B)) was employed, which considers particles without porosity and a composition of 20 $\%$ water fraction by mass, 32.91 $\%$ astronomical silicates, 7.43 $\%$ troilite, and 39.66 $\%$ refractory organics.

Equation 5 then ultimately depends on only three free parameters: dust temperature ($T_{dust}$), the surface density ($\Sigma_{dust}$), and the particle size ($a_{max}$). With three or more observed wavelengths, it becomes possible to solve the equation and obtain estimates for the three free parameters ($T_{dust}$, $\Sigma_{dust}$, $a_{max}$).

It is important to note that this model assumes a single temperature at each radius within the disk. This assumption generally holds when most of the dust is settled in the disk’s mid-plane. In cases where the emission is originating from an envelope or a flared disk involving different layers, however, this assumption may not be valid. So, it is worth noting that the temperature structure within protoplanetary disks can be complex, particularly if there are significant vertical temperature gradients or if different layers of the disk are contributing to the observed emission at different wavelengths. In these situations, a more sophisticated modeling approach that considers the vertical structure and temperature gradients within the disk would be necessary to interpret the observed SED.

A multi-wavelength analysis similar to ours here was previously performed before on HL Tau using four images between 8 mm and 0.9 mm (cite: 2019ApJ...883...71C) by simplifying the spectral behavior of the extinction coefficient using a power law. After that, it has been used in several other papers (e.g. (cite: 2021A&A...648A..33M), (cite: 2021ApJS..257...14S) and (cite: 2022A&A...664A.137G)) using the exact values of the dust opacity at each wavelength, including the work presented in this paper as well. This model is a first approach in determining the dust properties around a Class 0 YSO like A1.\
A Bayesian approach was employed to obtain the posterior probability distributions of the model parameters ($a_{max}$,$T_{dust}$,$\Sigma_{dust}$) at each radius. To achieve this, a standard log-normal likelihood function was used, which is defined as follows: $$\begin{eqnarray}
\ln p(\bar{I}(r)\mid \Theta )=-0.5 \sum_{i}^{}\left ( (\frac{\bar{I_{i}}-I_{m,i}}{\hat{\sigma}_{\bar{I,i}}})^{2}+\ln(2\pi\hat{\sigma}^{2}_{\bar{I,i}})  \right ),
  \label{eq:Log-normal likelihood function}
 
\end{eqnarray}$$

where $\bar{I}$ is the azimuthally averaged intensity at radius $r$ and at frequency $\nu_{i}$, $I_{m,i}$ is the model intensity from different combinations of the three free parameters at a radius $r$, $\Theta$ is the vector of the three free parameters. In addition, we assumed that the uncertainty $\hat{\sigma}_{\bar{I,i}}$ at radius $r$ is: $$\begin{eqnarray}
\hat{\sigma}_{\bar{I,i}}=\sqrt{\sigma^{2}_{\bar{I,i}}+(\delta_{i}\bar{I_{i}})^{2}},
  \label{eq:Uncertainty}
 
\end{eqnarray}$$

where $\sigma^{2}_{\bar{I,i}}$ is the error of the mean, obtained from the azimuthally averaged intensity profiles (See section 2), and $\delta_{i}$ is the flux calibration error at each frequency.

Figure 3 shows the analysis we performed, a model grid of intensities was created using various dust parameters. To infer the physical parameters of the dust particles, we compared the observed intensity at each radius with the expected spectral energy distribution (SED) derived from different combinations of the three free parameters in equations 5 and 6 ($a_{max}$ from 0.001 - 10 cm, $T_{dust}$ from 0.1 - 250 K, $\Sigma_{dust}$ from 0.1 - 1000 $gcm^{-2}$). In order to better match the observational data, the probability distribution of each parameter was plotted, along with the corresponding expected value (represented by the red curve in Figure 3). The expected value of each parameter was obtained by: $$\begin{eqnarray}
E(X)=\frac{\sum_{i} X_{i}P(X_{i}|\bar{I}(r))}{\sum_{i}P(X_{i}|\bar{I}(r))}
  \label{eq:Expected value}
 
\end{eqnarray}$$ where $X_{i}$ is each value in all the parameters inside our grid, and $P(X_{i}|\bar{I}(r))$ is the marginalized posterior probability of each parameter in every single cell of the grid.

Multiple equally likely solutions close to each other were found for the A1 source, which equally explained the observed intensity. All the possible solutions have similar $\Sigma_{dust}$ and dust temperature, which is explained in (cite: 2023ApJ...953...96Z) as there are no strong Mie interference patterns when $2\pi a<\lambda$. Finally, the optical depth values were derived from the analysis to provide insights into the dust properties at different locations within the disk. Figure 3 shows the dust parameters, the optical depths at each wavelength, and the intensities of the observations compared with the ones obtained from the model.

From Figure 3, it is evident that the A1 disk exhibits high optical thickness at the inner radii of A1, which poses challenges in fitting the dust parameters accurately. This observation suggests that the disk is highly unstable and contains very small dust particles (hundreds of microns in size) relative to dust grain sizes in protoplanetary disks. Notably, the derived temperature from the multi-wavelength analysis in A1 appears to be higher compared to other Class II disks analyzed using similar methods ((cite: 2021A&A...648A..33M), (cite: 2021ApJS..257...14S), (cite: 2019asrc.confE..88G) and (cite: 2019ApJ...883...71C)). This discrepancy may be attributed to the young age of the source and other processes occurring within the system, like infalling material that can contribute to the elevated temperature of the dust particles, viscous heating or even back warming by the envelope ((cite: 1993ApJ...412..761N)).

Furthermore, A1 displays a notably high dust surface density and mass in comparison to Class II disks. This result aligns with the notion that a significant portion of the material remains distributed as sub-mm particles surrounding the star rather than having settled and grown in the disk’s mid-plane where it cannot be detected by our observations due to high optical depths, the high mass inferred is expected for a very young source like A1, which is likely to be very gravitationally unstable having still a substantial circumprotostellar mass not yet accreted by the central star. We note that the particle sizes found in other disk studies often vary significantly depending on the presence of substructures, which are not detectable in the A1 source. Moreover, the particle sizes observed in other Class II disks tend to be larger (cm-sized particles) compared to the 0.1 mm particles found in A1. This disparity can be attributed to the different evolutionary stages of the disks, with the dust in the other disks having evolved and settled more in the mid-plane.

Figure 3 indicates that the material flowing in to form the disk already contains large dust particles (\> 10 microns) compared to the average ISM dust sizes. This suggests widespread grain growth across the entire disk radius. However, as one approaches the midplane and the central star, particles tend to become larger. These large dust particles compared to the ISM particles imply that grain growth is not limited to the midplane but also occurs in the flared regions of the disk where infall is the likely process that triggers this growth. Additionally, the increase in error at the outer region of the A1 disk is a result of the spatial sensitivity of the VLA image.\
We compare the temperature profile of A1 with other Class 0 sources and found that A1’s temperature agrees with those derived from CO and $H_{2}CO$ snowlines in IRAS04302 (Class I) and L1527 (Class I/O) by (cite: 2020A&A...633A...7V). Comparing with models from (cite: 2017ApJ...835..259Y) on the Class 0 Protostar BHR71; however, we note that the derived densities in A1 are at least an order of magnitude lower. This difference could potentially stem from the observations utilized by (cite: 2017ApJ...835..259Y) are of shorter wavelengths (*Herschel*) that are more sensitive to the cloud, the surrounding envelope, and smaller dust grains.

Concerning particle sizes, our analysis indicates that the inner disk of A1 comprises particles nearly 0.3 mm in size. This suggests that the dust size distribution in the disk is primarily characterized by larger particles when compared to typical interstellar medium (ISM) dust sizes. However, in comparison to pebbles found in more evolved disks, these particles are relatively small. This suggests that although some dust growth has already occurred, the process is still ongoing. Several studies focused on Class 0 objects have measured dust sizes in the envelope using low dust emissivity indices, revealing that grain growth might already happen in this Class 0 objects maybe even up to mm-sized particles ((cite: 2009A&A...507..861J),(cite: 2019A&A...632A...5G)). More specifically, scattering measurements from polarization observations in IRAS4A show the possibility of large millimeter size particles within the system ((cite: 2015ApJ...814L..28C)). These findings diverge from the multi-wavelength analysis in our work that shows smaller dust particles in IRAS4A1.

The findings presented in Figure 3 do not provide a definitive explanation for the spectral index below 2 in Figure 2. The particle sizes around 0.1 mm align with what is expected for dust self-scattering, indicating the presence of low spectral indices (cite: 2019ApJ...877L..22L). Nevertheless, these observed values can also be rationalized by considering a highly optically thick disk within r\<60 AU, where the inner layers are warmer than the outer layers. This scenario not only aligns with the observations but also corresponds to the outcomes illustrated in Figure 3, showcasing the high optical depth across all radii.

## Generic gap models with large scale heights.

![](HD163296MAC1)

![](IRAS4AFiguraPruebaModelos)

To explain the absence of observed substructures and the observed asymmetry in the IRAS4A1 disk, we employed radiative transfer models using RADMC-3D (cite: 2012ascl.soft02015D). For these models we assume that instead of observing a highly optically thick envelope with an embedded disk, IRAS4A1 is actually a flared disk with a significant scale height (the surrounding envelope has been resolved out in these high-res images, See section 3). When considering a greater scale height and flaring in the disk, it’s crucial to differentiate between flared disks, which represent an equilibrium configuration of orbiting material, and an infalling model. In this study, we will model the flared disk solely from the perspective of the dust continuum, without incorporating a dynamic approach such as infalling or rotational motions. This flaring effect can create an asymmetry in the disk and make it challenging to detect substructures, if they exist. The combination of disk inclination, large scale heights, and optically thick emission, even at Band 6, contributes to this effect. Evidence supporting the presence of a highly flared disk instead of an envelope has been observed in the Class 0 Protostar L1527 IRS by (cite: 2022ApJ...934...95S).

To test this assumption, a model of the dust continuum emission at 1.2 mm was constructed using RADMC-3D. Initially, "generic gap models" inspired by the disk of HD163296 were made to investigate the disappearance of substructures with increasing scale height. Subsequently, we developed a specific model to the IRAS4A1 disk to reproduce the observed asymmetry at 1.2 mm in combination with the absence of substructures. These radiative transfer models allow us to perform a detailed examination of the disk’s dust evolution and provide insights into its vertical structure.

For the generic gap models, we fixed certain parameters based on previous studies of HD163296. For the star, the parameters in Table 1 from (cite: 2018ApJ...869L..41A) were used: $M_{\ast}$ = 2.04 $M_{\odot}$, $L_{\ast}$ = 17 $L_{\odot}$, $T_{\ast}$ = 9332 K, and a distance of 101 pc. The positions of the two most prominent gaps were taken to be 49 and 86 au with a fixed width of 10 and 8 au, respectively.

The disk model was taken to have an inclination of i = 46.7°, a position angle of 133.3°, and a dust mass of 0.039$_{\odot}$ from (cite: 2020A&A...633A.137D). In addition, a size of 110 au for the disk was chosen. Inside RADMC-3D, a generic protoplanetary disk model was used, with the scale height varied in each model. To incorporate the DSHARP dust particle opacities, the optool software (cite: 2021ascl.soft04010D) was utilized, allowing for their utilization within RADMC-3D. Finally for completeness, RADMC-3D calculated the dust temperature using the density distribution for the generic protoplanetary disk model as follows:

$$\begin{eqnarray}
 \rho(r,z) =\frac{\sum(r)}{H_{p}\sqrt{2\pi}}exp(-\frac{z^{2}}{2H^{2}_{p}}),
 \label{eq: Density distribution}
 
\end{eqnarray}$$ , where r is the distance to the star from the disk, $\sum(r)$, is the dust surface density, and $H_{p}$ is the scale height of the dust disk.\
The scale height ($H_{p}$) in the generic protoplanetary disk model follows a power-law dependence on the radial distance as follows:

$$\begin{eqnarray}
H_{p}=H_{100}(\frac{r}{100 AU})^{1+\Psi},
 \label{eq: Scale Height}
 
\end{eqnarray}$$ where $\Psi$ is the flaring index, with a predefined value 0.14, and $H_{100}$, is the value of the scale height at a distance of 100 au from the central star.\
The scale height parameter was increased in the generic gap models until the substructures disappeared due to shadowing, obscuration, and/or contrast effects. Figure 4 shows the images of these models together with a cut through their major and minor axes.

In Figure 4, it is evident that substructures present in young Class 0 disks are challenging to observe, if present, due to the large scale heights that these disks may exhibit. The cuts shown in Figure 4 provide additional insights into the behavior of the disk at different scale heights. Along the major axis, even at a low scale height of 0.05, a strong flattening effect on the rings and gaps is observed. This effect is highly dependent on the inclination and position angle of the disk. The intensity variations along the minor axis reveal another interesting aspect: in the SW part of the disk, a lack of intensity is observed, an asymmetry caused by a large vertical structure in the disk, also seen in other sources, such as (cite: 2021ApJ...910...75L), (cite: 2023ApJ...951....9L). The direction of this asymmetry is determined by the orientation of the modeled disk. Furthermore, as the scale height increases, both the depth of the gaps and the visibility of substructures begin to flatten along the minor axis too. Eventually, there is a point where substructures ($\leq$10 au) can no longer be distinguished. This example demonstrates the impact of a highly flared disk on the visibility and discernibility of substructures, if any, in a young protoplanetary disk.

## Large scale height and very flared disk models of IRAS4A1

To investigate the asymmetry observed in the 1.2 mm image of the IRAS4A1 disk, additional modeling was performed in RADMC-3D. The objective was to determine whether or not the observed asymmetry could be reproduced in a large scale-height flared disk scenario. To set up the RADMC-3D models, we fixed specific parameters. Due to the difficulty of determining the stellar properties directly from the literature for a highly embedded Class 0 object like IRAS4A1, average values of stellar properties in a number of Class I systems were obtained from Tables 1 and 2 in (cite: 2023ApJ...944..135F). These average values include the stellar mass (1.55 $M_{\odot}$), radius (2.1 $R_{\odot}$), and effective temperature (3700 K). The inclination and position angle of the disk were fixed at 20° and 99°, respectively. The dust mass in the disk was taken from the multi-wavelength analysis, resulting in a value of 0.11$^{+0.08}_{-0.04}$ $M_{\odot}$. The scale height in the RADMC-3D models for the IRAS4A1 disk was initially set to H/R = 0.3, based on the appearance of asymmetry in the generic gap models. In addition to this base model, eight more models were created. three with a fixed scale height, three with a fixed high flaring index ($\Psi$ = 1.3), and two models with reduced gap widths. This variety allowed exploring different scale heights within the context of a consistently high flaring profile. Figure 5 shows the corresponding cuts through the major and minor axes in all eight models. The IRAS4A1 observation and the model that best reproduce its intensity along the major and minor axis are shown in Figure 6. By examining the outcomes of these various models, we can observe the influence of a gap presence, large flaring index, and large scale heights on the observed asymmetry and young Class 0 sources like the IRAS4A1 disk.

From the radiative transfer models of IRAS4A1, it is evident that an asymmetry is formed on the North (compared to South) part of the disk at large scale heights. The inclination and position angle in the models greatly influence the resulting asymmetry, emphasizing the uncertainties in these results. Furthermore, the simplicity of the model employed in this study may limit its ability to reproduce accurately the complexities of a Class 0 young stellar object like IRAS4A1. Nevertheless, the intensity profiles along the major and minor axes suggest the presence of "substructures" or other unknown processes occurring in the actual observations, as most models appear flat unless a gap is included. In the upcoming paragraphs, we will speculate about the substructure scenario in the IRAS4A1 disk although it is possible that something else is shaping the intensity profiles along the major and minor axis.

The models with a very small gap exhibit intensity profiles that more closely resemble the observed profile at 1.2 mm in both the major and minor axes. This difference may indicate that the gaps at these early stages are still forming and that we will need still higher resolution to see them. Regardless of whether IRAS4A1 is indeed a flared disk, a lower limit on the scale height for generating an asymmetry can be established (H/R \> 0.3). Note that the intensity profiles in the Figure are normalized, as the primary goal of this study is not to replicate the flux of the IRAS4A1 source precisely, but rather to provide insights into the earliest stages of disk and planet formation. Nevertheless, if our observations are capturing emission from higher layers in the disk and if the emission remains highly optically thick, it may be challenging to detect substructures with ALMA at the available resolution.

![](IRAS4AFiguraPrueba.pdf)

# Discussion

The inferred large scale height (H/R \> 0.3) in IRAS4A1 has significant implications for planet formation. Despite the fast settling expected during the disk’s lifetime, the optical thickness and asymmetry observed at Band 6 indicate the presence of material with varying grain sizes in higher layers of the disk. This result implies that settling is still ongoing for millimeter-sized particles. Indeed, this state is expected considering the settling timescales (\<1 Myr, (cite: 2004A&A...421.1075D)) and the estimated dynamical age of the outflows in IRAS4A (a few 0.01 Myr (cite: 2020A&A...637A..63T)). Furthermore, settling and radial drift are likely acting together during these early stages of dust evolution and growth in the disk.

The large scale height of the disk may also obscure young substructures, as suggested by models, particularly when combined with very narrow substructures measuring less than 4 au in size. While we are unable to directly resolve substructures (i.e., gaps) in the disk, our models suggest that some must be present to explain the observed bumps in the radial profile of IRAS4A1. These small-scale features are challenging to observe directly with current resolution capabilities (no substructures observed in IRAS4A1), but their presence at these early stages could indicate two possibilities. Firstly, if these substructures are caused by planet-disk interactions, it suggests that planets formed nearly instantaneously after the collapse of the molecular cloud. Furthermore, given sufficient time, substructures within protoplanetary disks are expected to widen, resembling those observed in other systems. This widening occurs as planets grow in size by accreting and carving out material from their surroundings.

We note that substructures can potentially arise from mechanisms other than planet-disk interaction. If this is the case, it introduces an intriguing possibility. In this scenario, the substructures initially form early on and are narrow, as indicated by the narrow gap width in the models. Given settling-induced growth of dust particles and other processes occurring within these narrow substructures, substructure formation through alternative mechanisms may itself trigger planet formation within such gaps. Hence, planet formation could take place very early in the disk’s evolution, following an evolutionary path similar to the first scenario.

An additional crucial aspect to consider is the large flaring index observed in IRAS4A1. If the "shoulder" position, which served as the basis for defining the gap position for the models, around the range of 20-40 AU is pointing to a substructure, this substructure could be relatively close to the disk mid-plane. For example, smaller scale heights may occur in the center of the disk, meaning that the closer a substructure forms to the center the easier it would be to detect it in a very flared disk. Consequently, any mechanism responsible for carving out these substructures probably starts in the mid-plane and is unable to reach large-scale heights, as seen in other protoplanetary disks when scattered light observations and sub-mm observations with ALMA are compared.

It is important to note, however, that the combination of large scale heights and a large flaring index could still hide further substructures in the outer radii of the IRAS4A1 disk. On the other hand, if there are no substructures in the flared disk of IRAS4A1, planet formation may then occur only at a later stage when larger particles have already settled in the disk midplane, taking into account the timescales required for settling.

Recently, similar results including the "shoulders", asymmetries, and large scale heights were found in YSOs in studies by the eDisk survey team (cite: 2023ApJ...951....8O). Regardless of the specific dynamics within the IRAS4A1 disk, it is becoming evident that Class 0 Young Stellar Objects (YSOs) exhibit flared disks with significant scale heights, providing valuable insights into the planet formation process.

# Summary and conclusions

We have shown high-resolution ALMA images (78 mas) of the IRAS4A binary system in Bands 4 and 6. In summary, the key findings of this paper can be outlined as follows:

- No substructures were detected in either A1 or A2 at the current resolution.

- Analysis of spectral indexes and brightness temperatures indicated that A1 is significantly more optically thick than A2.

- A multi-wavelength image analysis was carried out showing the dust parameters in A1. The expected values of the dust parameters inferred high temperatures (\>50 K), high surface densities (\>10 $gcm^{-2}$), and large dust size particles (\>30 $\mu$m) at all radius (\< 60 au) in the IRAS4A1 disk. In addition, the analysis showed high optical depth in the inner disk in Band 6 and Band 4.

- Radiative transfer models using RADMC-3D have shown that a minimum scale height of H/R \> 0.3 is adequate to render the substructures invisible and produce an asymmetry in the disks. Moreover, the models that incorporated a narrow gap around 34-50 au and increased flaring index, provided better matches to the observed intensity profiles, suggesting the presence of potential hidden substructures within a very flared disk in the IRAS4A1 system, even in these early stages of disk formation.

Observations with high resolution and sensitivity at cm wavelengths with the ngVLA can help unveil any substructure that might exist in IRAS4A1.

# Acknowledgements

We thank the referee for the very constructive comments. We also thank Dominique M. Segura-Cox for the useful discussion. We acknowledge assistance from Allegro, the European ALMA Regional Centre node in the Netherlands. This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2018.1.00510.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

EGC acknowledges support from the National Science Foundation through the NSF MPS-Ascend Fellowship Grant number 2213275. L.W.L. acknowledges support from NSF AST-1910364 and NSF AST-2108794.

67 natexlab

(ref: 2015ApJ...808L...3A) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3

(ref: 2018ApJ...869L..41A) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41

(ref: 2005A&A...443..185B) Barrière-Fouchet, L., Gonzalez, J. F., Murray, J. R., Humble, R. J., & Maddison, S. T. 2005, A&A, 443, 185

(ref: 2018ApJ...869L..45B) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45

(ref: 2019ApJ...883...71C) Carrasco-González, C., Sierra, A., Flock, M., et al. 2019, ApJ, 883, 71

(ref: 2013atnf.prop.5561C) Casassus, S., Maddison, S., Wright, C., Menard, F., & Perez, s. 2013, Planet formation feedback in HD142527, ATNF proposal id.C2094, Semester: April, 2013

(ref: 2016ApJ...819..159C) Ching, T.-C., Lai, S.-P., Zhang, Q., et al. 2016, ApJ, 819, 159

(ref: 2021ApJ...916...82C) Chuang, C.-Y., Aso, Y., Hirano, N., Hirano, S., & Machida, M. N. 2021, ApJ, 916, 82

(ref: 2015ApJ...814L..28C) Cox, E. G., Harris, R. J., Looney, L. W., et al. 2015, ApJL, 814, L28

(ref: 2021ascl.soft04010D) Dominik, C., Min, M., & Tazaki, R. 2021, Astrophysics Source Code Library, ascl:2104.010

(ref: 2015ApJ...809...93D) Dong, R., Zhu, Z., & Whitney, B. 2015, ApJ, 809, 93

(ref: 2023ASPC..534..717D) Drążkowska, J., Bitsch, B., Lambrechts, M., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 717

(ref: 2004A&A...421.1075D) Dullemond, C. P. & Dominik, C. 2004, A&A, 421, 1075

(ref: 2020A&A...633A.137D) Dullemond, C. P., Isella, A., Andrews, S. M., Skobleva, I., & Dzyurkevich, N. 2020, A&A, 633, A137

(ref: 2012ascl.soft02015D) Dullemond, C. P., Juhasz, A., Pohl, A., et al. 2012, RADMC-3D: A multi-purpose radiative transfer tool, Astrophysics Source Code Library, record ascl:1202.015

(ref: 2023ApJ...944..135F) Fiorellino, E., Tychoniec, Ł., Cruz-Sáenz de Miera, F., et al. 2023, ApJ, 944, 135

(ref: 2015A&A...574A..68F) Flock, M., Ruge, J. P., Dzyurkevich, N., et al. 2015, A&A, 574, A68

(ref: 2019A&A...632A...5G) Galametz, M., Maury, A. J., Valdivia, V., et al. 2019, A&A, 632, A5

(ref: 2019asrc.confE..88G) Guidi, G. 2019, in ALMA2019: Science Results and Cross-Facility Synergies, 88

(ref: 2022A&A...664A.137G) Guidi, G., Isella, A., Testi, L., et al. 2022, A&A, 664, A137

(ref: 2018ApJ...869L..43H) Huang, J., Andrews, S. M., Pérez, L. M., et al. 2018, ApJL, 869, L43

(ref: 2016PhRvL.117y1101I) Isella, A., Guidi, G., Testi, L., et al. 2016, , 117, 251101

(ref: 1978JOSA...68.1368I) Ishimaru, A. 1978, Journal of the Optical Society of America (1917-1983), 68, 1368

(ref: 2007ApJ...659..479J) Jørgensen, J. K., Bourke, T. L., Myers, P. C., et al. 2007, ApJ, 659, 479

(ref: 2009A&A...507..861J) Jørgensen, J. K., van Dishoeck, E. F., Visser, R., et al. 2009, A&A, 507, 861

(ref: 2009AAS...21341318K) Kwon, W., Looney, L. W., Mundy, L. G., Chiang, H., & Kemball, A. J. 2009, in American Astronomical Society Meeting Abstracts, Vol. 213, American Astronomical Society Meeting Abstracts #213, 413.18

(ref: 2014MNRAS.437.3055L) Laibe, G., Gonzalez, J.-F., Maddison, S. T., & Crespe, E. 2014, MNRAS, 437, 3055

(ref: 2021ApJ...910...75L) Lee, C.-F., Li, Z.-Y., Yang, H., et al. 2021, ApJ, 910, 75

(ref: 2023ApJ...951....9L) Lin, Z.-Y. D., Li, Z.-Y., Tobin, J. J., et al. 2023, ApJ, 951, 9

(ref: 2019ApJ...877L..22L) Liu, H. B. 2019, ApJL, 877, L22

(ref: 2018ApJ...869...17L) Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17

(ref: 2021A&A...648A..33M) Macı́as, E., Guerra-Alvarado, O., Carrasco-González, C., et al. 2021, A&A, 648, A33

(ref: 1977ApJ...217..425M) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425

(ref: 2019A&A...621A..76M) Maury, A. J., André, P., Testi, L., et al. 2019, A&A, 621, A76

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2022ApJ...937..104M) Michel, A., Sadavoy, S. I., Sheehan, P. D., Looney, L. W., & Cox, E. G. 2022, ApJ, 937, 104

(ref: 1993Icar..106...20M) Miyake, K. & Nakagawa, Y. 1993, Icarus, 106, 20

(ref: 1993ApJ...412..761N) Natta, A. 1993, ApJ, 412, 761

(ref: 2023ApJ...951....8O) Ohashi, N., Tobin, J. J., Jørgensen, J. K., et al. 2023, ApJ, 951, 8

(ref: 2016ApJ...821...82O) Okuzumi, S., Momose, M., Sirono, S.-i., Kobayashi, H., & Tanaka, H. 2016, ApJ, 821, 82

(ref: 2016Sci...353.1519P) Pérez, L. M., Carpenter, J. M., Andrews, S. M., et al. 2016, Science, 353, 1519

(ref: 2012A&A...538A.114P) Pinilla, P., Birnstiel, T., Ricci, L., et al. 2012, A&A, 538, A114

(ref: 2016ApJ...816...25P) Pinte, C., Dent, W. R. F., Ménard, F., et al. 2016, ApJ, 816, 25

(ref: 2011A&A...532A..71R) Rau, U. & Cornwell, T. J. 2011, A&A, 532, A71

(ref: 1979rpa..book.....R) Rybicki, G. B. & Lightman, A. P. 1979, Radiative processes in astrophysics

(ref: 2015A&A...584A.126S) Santangelo, G., Codella, C., Cabrit, S., et al. 2015, A&A, 584, A126

(ref: 2020Natur.586..228S) Segura-Cox, D. M., Schmiedeke, A., Pineda, J. E., et al. 2020, Nature, 586, 228

(ref: 2020Natur.586..205S) Sheehan, P. 2020, Nature, 586, 205

(ref: 2022ApJ...934...95S) Sheehan, P. D., Tobin, J. J., Li, Z.-Y., et al. 2022, ApJ, 934, 95

(ref: 2020ApJ...892..136S) Sierra, A. & Lizano, S. 2020, ApJ, 892, 136

(ref: 2019ApJ...876....7S) Sierra, A., Lizano, S., Macı́as, E., et al. 2019, ApJ, 876, 7

(ref: 2021ApJS..257...14S) Sierra, A., Pérez, L. M., Zhang, K., et al. 2021, ApJS, 257, 14

(ref: 2018ApJ...865..102T) Takahashi, S. Z. & Muto, T. 2018, ApJ, 865, 102

(ref: 2020A&A...637A..63T) Taquet, V., Codella, C., De Simone, M., et al. 2020, A&A, 637, A63

(ref: 2016ApJ...818...73T) Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2016, ApJ, 818, 73

(ref: 2018ApJ...867...43T) Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2018, ApJ, 867, 43

(ref: 2020A&A...640A..19T) Tychoniec, Ł., Manara, C. F., Rosotti, G. P., et al. 2020, A&A, 640, A19

(ref: 2013Sci...340.1199V) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2013, Science, 340, 1199

(ref: 2020A&A...633A...7V) van ’t Hoff, M. L. R., van Dishoeck, E. F., Jørgensen, J. K., & Calcutt, H. 2020, A&A, 633, A7

(ref: 2020A&A...642A.164V) Villenave, M., Ménard, F., Dent, W. R. F., et al. 2020, A&A, 642, A164

(ref: 2023ApJ...946...70V) Villenave, M., Podio, L., Duchêne, G., et al. 2023, ApJ, 946, 70

(ref: 2017ApJ...835..259Y) Yang, Y.-L., Evans, Neal J., I., Green, J. D., Dunham, M. M., & Jørgensen, J. K. 2017, ApJ, 835, 259

(ref: 2015IAUGA..2256118Z) Zhang, K., Blake, G., & Bergin, E. 2015, in IAU General Assembly, Vol. 29, 2256118

(ref: 2018ApJ...869L..47Z) Zhang, S., Zhu, Z., Huang, J., et al. 2018, ApJL, 869, L47

(ref: 2023ApJ...953...96Z) Zhang, S., Zhu, Z., Ueda, T., et al. 2023, ApJ, 953, 96

(ref: 2019ApJ...877L..18Z) Zhu, Z., Zhang, S., Jiang, Y.-F., et al. 2019, ApJL, 877, L18

(ref: 2018ApJ...869...83Z) Zucker, C., Schlafly, E. F., Speagle, J. S., et al. 2018, ApJ, 869, 83

# Faint emission between A1 and A2.

![](Continuumallbands78masFE.pdf)

</paper>

Write the methods card for this paper.