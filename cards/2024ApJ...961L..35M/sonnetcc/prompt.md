# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...961L..35M\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...961L..35M",
 "title": "The ALMA-QUARKS Survey: Detection of Two Extremely Dense Substructures in a Massive Prestellar Core",
 "year": 2024,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Mai, Xiaofeng",
 "n_authors": 35,
 "arxiv_id": "2401.04322",
 "doi": "10.3847/2041-8213/ad19c3",
 "alma_projects_linked_by_archive": [
  "2019.1.00685.S",
  "2021.1.00095.S"
 ]
}
```

Paper text:
<paper>
# The ALMA-QUARKS survey: Detection of two extremely dense substructures in a massive prestellar core

## Abstract

Only a handful of massive starless core candidates have been discovered so far, but none of them have been fully confirmed. Within the MM1 clump in the filamentary infrared dark cloud G34.43+0.24 that was covered by the ALMA-ATOMS survey at Band 3 ($\sim2\ensuremath{''}$, 6000 au) and the ALMA-QUARKS survey at Band 6 ($\sim 0.3\ensuremath{''}$, 900 au), two prestellar core candidates MM1-C and E1 with masses of 71 and 20 $M_{\odot}$ and radii of 2100–4400 au were discovered. The two cores show no obvious sign of star-formation activities. In particular, MM1-C is a very promising massive prestellar core candidate with a total gas mass of 71 $M_{\odot}$. Within MM1-C, we detected two extremely dense substructures, C1 and C2, as characterized by their high densities of $\rm n_{H_2}\sim 10^{8-9} cm^{-3}$. Moreover, evidence of further fragmentation in C2 was also revealed. We have detected the primordial fragmentation in the earliest stage of massive star formation, and we speculate that MM1-C would be the birthplace of a massive multiple system. However, we cannot fully rule out the possibility that the massive prestellar core MM1-C will just form a cluster of low-mass stars if it undergoes further fragmentation.

[^1]

[^2]

[^3]

# Introduction

Massive stars with their enormous UV radiation and large mechanical energy output, profoundly impact the surrounding interstellar medium (ISM) and play a pivotal role in the evolution of galaxies and even the Universe. However, observing the progenitors of massive stars is very challenging due to their rapid evolutionary timescale and the highly opaque molecular clouds surrounding them. Consequently, the formation of massive stars remains enigmatic, which has led to very diverse ideas on the mechanisms involved. For instance, the *Turbulent Core* model (cite: 2003ApJ...585..850M) proposes that massive stars form in the same way as low-mass stars, by gradually accumulating gas from their natal cores (sizes $\sim$ 0.1 pc). In this case, massive prestellar cores should thus be the progenitors of massive stars. Conversely, the “clump-feed" models such as *Competitive Accretion* (cite: 2001MNRAS.323..785B), the *Inertial Inflow* (cite: 2020ApJ...900...82P), and the *Global Hierarchical Collapse* model (cite: 2009ApJ...707.1023V; 2019MNRAS.490.3061V) suggest that massive stars form from low-mass cores within clouds amassing through further gas accretion from their natal clumps or even clouds.

Hunting for massive prestellar cores is one of the most straightforward ways to distinguish among different scenarios. Due to their rapid evolution, only a few promising massive prestellar core candidates have been identified to date: e.g. (cite: 2023A&A...675A..53B), (cite: 2018A&A...618L...5N), and (cite: Liu2017), etc. However, none of these massive starless core candidates have been fully confirmed, indicating that the search for massive prestellar core candidates warrants further observational efforts. Given that the current sample size is small, a comprehensive understanding requires persistent efforts in identifying additional samples of massive prestellar core candidates. On the other hand, surveys aiming to identify massive prestellar cores in the earliest phases of massive clumps have yielded no conclusive results in their favor (cite: 2017ApJ...841...97S; 2019ApJ...886..102S; 2021ApJ...923..147M; 2023ApJ...950..148M; 2023ApJ...949..109L). Specifically, (cite: 2023ApJ...950..148M) reported the absence of massive prestellar cores within a substantial sample of 70 $\rm \mu m$ dark IRDCs, encompassing over 800 cores. (cite: 2019ApJ...886..102S) suggested that if massive prestellar cores do indeed exist, they are likely embedded in the more evolved environment. Recently, in an ALMA 0.87 mm survey of 11 clumps, (cite: Xu2023ASSEMBLE) confirmed that starless cores are becoming more massive in evolved clumps as compared to early-stage clumps, through continuous gas accretion. Therefore, it might be more promising to search for massive starless cores in a protocluster environment.

Located 3.0 kpc away from the Sun (cite: 2023ApJ...949...10M), the filamentary IRDC G34.43+0.24 (hereafter G34) is a well studied high-mass star forming region (cite: 2004ApJ...610..313G; 2005ApJ...630L.181R; 2010ApJ...715...18S; 2012ApJ...756...60S; 2013ApJ...775L..31S; 2014ApJ...791..108F; 2016ApJ...819..117X; 2019ApJ...883...95S; 2020ApJ...901...31L). Molecular outflows have been reported for the dense core G34-MM1 by (cite: 2010ApJ...715...18S) and (cite: 2018ApJS..235....3Y) at low resolution ($\sim 18\ensuremath{''}$). Given that molecular outflows are one of the earliest signatures of star formation activities (cite: 2022A&A...658A.160Y), the dense core G34-MM1 in the IRDC G34 is supposed to be in the early stage of star formation. (cite: 2022MNRAS.510.5009L) have extensively studied this complex using the high angular resolution ($\sim 2\ensuremath{''}$) data of the ATOMS survey (cite: 2020MNRAS.496.2790L), and identified six dense cores in its G34-MM1 clump with masses ranging from 20 to 122 $M_{\odot}$[^4]. However, the evolutionary stages of these cores need to be explored further. The ALMA-QUARKS survey (cite: liu2023almaquarks) observed the densest kernels of the ATOMS sources at Band 6 with a much higher resolution of $\sim 0.3\ensuremath{''}$, providing the possibility of verifying the existence of massive starless cores in G34-MM1 in a spatial resolution of $\sim 1000$ au. In this letter, we revisit these cores and report the discovery of the two cores MM1-C and MM1-E1, situated close to the boundary of G34-MM1 clump, as candidate massive prestellar cores containing extremely dense substructures.

![](fig/all_C_E.pdf)

# Observations

G34-MM1 was observed as part of the ALMA project “ALMA Three-millimeter Observations of Massive Star-forming regions" (ATOMS, Project ID: 2019.1.00685.S; PI: Tie Liu). The observations were conducted with the 7-m array (ACA) and 12-m arrays (C43-2 or C43-3) at Band 3. The observation setup and data reduction can be found in (cite: 2020MNRAS.496.2790L). The angular resolution and maximum recoverable scales (MRS) for the ACA and 12-m array are 13.3$''$ and 76.9$''$, and 1.5$''$ and 19.4$''$, respectively. The ACA and 12-m combined data have resulted in a resolution of $\sim2\ensuremath{''}$ for continuum emission. The combined continuum image of G34-MM1 reaches an rms noise level of 0.3 mJy beam$^{-1}$. Eight spectral windows (SPWs) were set including six SPWs with high spectral resolution and two wide SPWs with 1875 MHz bandwidth. The spectral data reaches a noise level of 12 mJy beam$^{-1}$ per 0.062 MHz channel ($\sim$0.2–0.4 km s$^{-1}$) for six SPWs, and 3.6 mJy beam$^{-1}$ per 0.488 MHz channel ($\sim 1.6$ km s$^{-1}$) for wide SPWs.

G34-MM1 was also observed as part of a new ALMA project, “Querying Underlying mechanisms of massive star formation with ALMA-Resolved gas Kinematics and Structures" (QUARKS, PIs: Lei Zhu, Guido Garay and Tie Liu). The QUARKS project targets are the same objects as in the ATOMS survey but with a much higher resolution, of $\sim0.25\ensuremath{''}$, at Band 6 (ALMA Project IDs: 2021.1.00095.S and 2023.1.00425.S; PI: Lei Zhu). The observations were conducted with ACA and 12-m arrays (C43-2 and C43-5) at Band 6. The observation setup and data reduction of QUARKS are described in (cite: liu2023almaquarks). The ACA and 12-m combined data were resulting in an angular resolution of 0.3$''$, and the corresponding combined continuum image achieves a rms noise level of 0.25 mJy beam$^{-1}$. Four wide SPWs with 1875 MHz bandwidth were set, resulting in a noise level of 5 mJy beam$^{-1}$ per 0.488 MHz channel ($\sim 0.6$ km s$^{-1}$).

![](fig/spws.pdf)

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | R.A. | Decl. | $\rm FWHM^{Deconv}$ | PA | $R_{\rm eff}$ | $S_{\nu}$ | $T_{\rm gas}$ | $M_{\rm gas}$ | $n_{\rm H_2}$ |
|  | (J2000) | (J2000) | ($''$) | ($\ensuremath{^\circ}$) | (au) | (mJy) | \(K\) | ($M_{\odot}$) | ($\rm 10^7~cm^{-3}$) |
| *Band 3$^*$* |  |  |  |  |  |  |  |  |  |
| MM1-C | 18:53:18.30 | 1:25:13.60 | $3.5\times2.4$ | 16.0 | $4390\pm 239$ | $9.1$ | 14.2 | $71.2\pm33.4$ | $2.6\pm1.3$ |
| MM1-E1 | 18:53:18.74 | 1:25:26.84 | $2.3\times1.3$ | 2.1 | $2169\pm 142$ | $4.2$ | 22.6 | $20.3\pm9.6$ | $3.5\pm1.8$ |
|  *Band 6* |  |  |  |  |  |  |  |  |  |
| MM1-C1 | 18:53:18.32 | 1:25:13.56 | $0.62\times0.35$ | 27.9 | $701\pm 38$ | $6.1$ | 14.2 | $2.1\pm1.1$ | $18.4\pm11.2$ |
|  |  |  |  |  |  |  | 10 | $3.7\pm1.7$ | $32.7\pm16.0$ |
|  |  |  |  |  |  |  | 6.5 | $8.2\pm3.8$ | $71.7\pm35.9$ |
| MM1-C2 | 18:53:18.27 | 1:25:13.85 | $1.09\times0.77$ | 55.6 | $1387\pm 75$ | $21.2$ | 14.2 | $7.3\pm3.4$ | $8.4\pm4.4$ |
|  |  |  |  |  |  |  | 10 | $12.9\pm6.0$ | $14.9\pm7.5$ |
|  |  |  |  |  |  |  | 6.5 | $28.4\pm13.2$ | $32.8\pm16.3$ |
| MM1-E1 | 18:53:18.73 | 1:25:26.30 | $0.83\times0.45$ | 66.8 | $925\pm 50$ | $10.2$ | 22.6 | $2.0\pm0.9$ | $7.6\pm3.8$ |

# Results

## Detection of massive starless core candidates 

Fig. [1](#fig:continuum) presents the ALMA Band 3 (3 mm) and Band 6 (1.3 mm) continuum emission maps of the G34-MM1 clump. Reexamination of the Band 3 continuum emission revealed that the MM1-E core identified in (cite: 2022MNRAS.510.5009L) is in fact two separate cores (namely E1, E2) instead of one single core, as clearly seen from higher-resolution 1.3 mm emission. We performed two-component two-dimensional Gaussian fitting toward E1 and E2 following the same procedure as in (cite: 2021MNRAS.505.2801L), which is a combination of *Dendrogram* (cite: 2008ApJ...679.1338R) and *CASA-imfit* for consistency. The measured core properties of these two cores are summarized in Table [\[tab:coreproperties\]](#tab:coreproperties). In this work, we only focus on the two massive starless core candidates MM1-C and MM1-E1.

Since the MRS of the Band 3 data is two times larger than that of the Band 6 data and the 3 mm continuum emission is relatively optically thin than the 1.3 mm continuum emission, we use the 3 mm continuum emission to calculate the total gas masses of dense cores MM1-C and MM1-E1. Assuming that the 3 mm continuum emission is optically thin under local thermodynamic equilibrium (LTE) conditions, the core masses can be calculated as (cite: 2021ApJ...912..148L), $$\begin{equation}
    M_{\rm gas}=\frac{R_{\rm gd}S_{\nu}D^2}{\kappa_{\nu}B_{\nu}(T_{\rm dust})},
    \label{eqa:mass}
\end{equation}$$ where $S_{\nu}$ is the integrated 3 mm continuum flux, $D$ is the distance to the region (3.0 kpc), and $B_{\nu}(T_{\rm dust})$ is the Planck function at dust temperature $T_{\rm dust}$. The dust temperature $T_{\rm dust}=$14.2 K and 22.6 K for MM1-C and E1 respectively are taken as the gas kinetic temperature of $\rm NH_3$ from VLA observations at the resolution of $\sim$ 3$''$ (cite: 2014ApJ...790...84L). We assume a typical gas-dust mass ratio $R_{\rm gd}$ of 100. A value for $\kappa_\nu$ of 0.18 $\rm cm^{2}~g^{-1}$ is adopted from the ‘OH5’ model(cite: 1994A&A...291..943O; 1994ApJ...421..615P) and extended to the longer wavelength by (cite: 2005ApJ...627..293Y). Furthermore, by assuming a spherical geometry, the number density can be estimated as $n_{\rm H_2}=3M/(4\pi\mu_{\rm H_2}m_{\rm H}R_{\rm core}^3)$, where the molecular weight per hydrogen molecule $\mu_{\rm H_2}$ is 2.8, and $m_{\rm H}$ is the mass of a proton. The effective radii of the cores $R_{\rm core}$ are estimated as $\rm (FWHM^{Deconv}_{major}\times FWHM^{Deconv}_{minor})^{\frac{1}{2}}/2\times D$ where $\rm FWHM^{Deconv}_{major}$ and $\rm FWHM^{Deconv}_{minor}$ are the deconvolved FWHM of the major and minor axis, respectively.

Several sources of uncertainty can influence the mass determination. Following (cite: 2017ApJ...841...97S; 2019ApJ...886..102S), we conservatively assign the uncertainties of 25% for $R_{\rm dg}$ and $\kappa_\nu$, 5% for the absolute flux uncertainty at Band 3[^5] and the distance ($3.03^{+0.17}_{-0.16}$ kpc). The combined uncertainty of mass determination is $\sim$ 50%. The mass, deconvolved size, number density, and column density estimated from Band 3 continuum emission are summarized in Table [\[tab:coreproperties\]](#tab:coreproperties). We find that the cores MM1-C and E1 are massive and dense, having masses of 71 $M_{\odot}$ and 20 $M_{\odot}$ , respectively, on a scale of approximately 4000–8000 au (0.02–0.04 pc). Their densities reach up to $\sim3\times10^7$ cm$^{-3}$. Considering a star formation efficiency (a conversion efficiency of core mass into star mass; $\epsilon_{\rm core}$) of 50%, which is reasonable and maybe even conservative for extreme density cores (cite: 2010A&A...524A..18B; 2013ApJ...762..120P; Motte2018; Pouteau2022), the two massive and dense cores in G34-MM1 clump (MM1-C and E1) will have the potential to form a massive star or a small star cluster with a stellar mass $M_{\rm star}>$8 $M_\ensuremath{\odot}$ eventually.

Fig. [2](#fig:spectra) shows the core-averaged spectra of MM1-C and E1 in four wide-band spectral windows at Band 6, and two wide-band spectral windows at Band 3. For comparison, we also plot the spectra of the hot molecular core MM1-A, which has already formed high-mass protostars (cite: 2022MNRAS.511.3463Q). It can be easily noticed that very few lines are detected toward MM1-C and E1, which is in strong contrast with the ‘line forest’ of MM1-A. Some absorption features in the spectra of molecules including H$_2$CO, $^{13}$CO, C$^{18}$O, and CH$_3$OH are likely caused by the missing flux issue as a result of interferometer observations due to sidelobe or a lack of shorter baselines and total power (TP) data. As shown in the moment 0 maps in Fig. [4](#fig:appendixa), no clear emission or absorption features of CH$_3$OH with signal-to-noise ratios (SNRs) larger than 3$\sigma$ were detected toward both MM1-C and E1. In addition, as shown in Figure [5](#fig:appendixb), the beam-averaged spectra at band 6 toward the continuum emission peak of MM1-C1 show no absorption features in either H$_2$CO or CH$_3$OH lines, which could be caused by warm or hot continuum background sources (or protostars) within MM1-C1.

Additionally, (cite: 2022MNRAS.510.5009L) identified six outflow lobes in the MM1 clump, but none of them seem to come from MM1-C or E1. We also carefully checked the $^{12}$CO *J*=2-1 and SiO *J*=5-4 lines toward the two cores and found no evidence of high-velocity emission. We present the CO outflows in Fig. [6](#fig:appendixc). Both MM1-C and E1 are far away from CO outflow lobes. Also, no radio jets are detected by the GLOSTAR survey (cite: 2023A&A...670A...9D) associated with these two cores (cite: 2023arXiv231009777Y). Taking into account both the paucity of spectral lines and the absence of outflows, we postulate that there is no ongoing star-formation activity within cores MM1-C and E1. Thus, we classify these two cores as starless cores, among which MM1-C is a more promising massive starless core (cite: 2017ApJ...841...97S).\

+--------+---------------+-----------------------------------------------------+-----------------------------------------------------------+
| Source |               | $\sigma_{\rm v, N_2D^+}=0.74~{\rm km~s^{-1}}$       | $\sigma_{\rm v, H^{13}CO^+}=0.46~{\rm km~s^{-1}}$         |
+:=======+:==============+:===============:+:===============:+:===============:+:=================:+:=================:+:=================:+
| 3-8    | $T_{\rm gas}$ | $L_{\rm J}$     | $M_{\rm J}$     | $\alpha$        | $L_{\rm J}$       | $M_{\rm J}$       | $\alpha$          |
+--------+---------------+-----------------+-----------------+-----------------+-------------------+-------------------+-------------------+
|        | \(K\)         | (au)            | ($M_{\odot}$)   |                 | (au)              | ($M_{\odot}$)     |                   |
+--------+---------------+-----------------+-----------------+-----------------+-------------------+-------------------+-------------------+
| MM1-C  | 14.2          | –               | –               | 0.76            | –                 | –                 | 0.28              |
+--------+---------------+-----------------+-----------------+-----------------+-------------------+-------------------+-------------------+
| MM1-C1 | 14.2          | 2146            | 7.25            | 3.86            | 1276              | 1.52              | 1.69              |
|        +---------------+-----------------+-----------------+-----------------+-------------------+-------------------+-------------------+
|        | 10            | 1685            | 5.69            | 2.13            | 1002              | 1.20              | 0.91              |
|        +---------------+-----------------+-----------------+-----------------+-------------------+-------------------+-------------------+
|        | 6.5           | 1139            | 3.85            | 0.95            | 677               | 0.81              | 0.40              |
+--------+---------------+-----------------+-----------------+-----------------+-------------------+-------------------+-------------------+
| MM1-C2 | 14.2          | 3248            | 10.97           | 2.06            | 1931              | 2.31              | 0.90              |
|        +---------------+-----------------+-----------------+-----------------+-------------------+-------------------+-------------------+
|        | 10            | 2521            | 8.52            | 1.21            | 1499              | 1.79              | 0.52              |
|        +---------------+-----------------+-----------------+-----------------+-------------------+-------------------+-------------------+
|        | 6.5           | 1704            | 5.76            | 0.54            | 1013              | 1.21              | 0.23              |
+--------+---------------+-----------------+-----------------+-----------------+-------------------+-------------------+-------------------+

: Jeans and virial analysis.

## Detection of extremely dense Substructures within Core MM1-C

Panels (c) and (d) in Fig. [1](#fig:continuum) show high-resolution Band 6 (1.3 mm) continuum emission at a resolution of $\sim$0.3$''$ toward the two massive cores MM1-C and MM1-E. MM1-E1 shows no evidence of fragmentation, remaining a single condensation at this resolution, whereas two prominent condensations (namely, C1 and C2) are clearly seen in MM1-C. The fragmentation could be interferometric artifacts, as discussed in (cite: 2019ApJ...874...89C). However, the detection was at the 3$\sigma$ level in their synthetic observations, while in our observations, the detection of the fragments is more reliable, at $\sim10\sigma$ level. In particular, the fragments are well separated by 2400 au (about 3 beam sizes, or 0.8$''$ at 3 kpc), and can be reliably identified by the *Dendrogram* algorithm. Therefore, we argue that core MM1-C shows obvious fragmentation.

As shown by the black contour in Panel (c) in Fig. [1](#fig:continuum), two condensations were identified by *Dendrogram*[^6]. Due to the proximity, we performed a simultaneous 2D Gaussian fitting of the cores. The estimated sizes of C1 and C2 are 701 and 1381 au, respectively. We also assign the uncertainties of the parameters in Eq. ([\[eqa:mass\]](#eqa:mass)) as in Sec. [3.1](#sec:3.1), with the exception of the absolute flux, which has an uncertainty of 10% at Band 6 (See also ALMA proposal guide). For $\kappa_\nu$ at Band 6, we adopt a value of 0.9 $\rm cm^2\,g^{-1}$ (cite: 1994A&A...291..943O). Assuming they have the same temperature as the natal core, the masses of C1 and C2 are $\sim$2.1 $M_{\odot}$ and $\sim$7.3 $M_{\odot}$, respectively. The derived densities are remarkably high, of the order $\rm \sim10^8\,cm^{-3}$. Negative temperature gradients of prestellar cores have been reported (cite: 2007A&A...470..221C; 2021ApJ...923..231S). The core-average temperature is possibly an upper limit, and therefore the estimated masses are lower limits. We further calculate their masses assuming lower temperatures of 10 K and 6.5 K. The corresponding parameters of C1 and C2 are also listed in Table [\[tab:coreproperties\]](#tab:coreproperties). The mass of MM1-C2 can be as high as 10-30 $M_\ensuremath{\odot}$ if $T_{\rm dust}\leq 10$ K. In addition, MM1-C2 could further accumulate its mass through accreting gas from its collapsing natal core as well as a cold filament (see section [4.2](#sec:n2dp)). Within such a small-scale region ($\sim1000$ au) containing extremely high density ($\sim10^8$ cm$^{-3}$) gas, a higher $\epsilon_{\rm core}\sim50\%-100\%$ could be possible (cite: 2010A&A...524A..18B; 2013ApJ...762..120P; Benedettini2018; Motte2018; Pouteau2022). Thus, it is possible that MM1-C2 can form a massive star ($M_{\rm star}>$8 $M_\ensuremath{\odot}$) in the future.

![](fig/n2dp.pdf)

# Discussion

## Stability and Dynamical State

Dense cores or condensations will form stars only when they are presently collapsing or will be collapsing in the future. To assess the dynamical state of the dense core MM1-C and its two extremely dense substructures (C1 and C2), we estimated their virial parameters. We use molecular line data of $\rm N_2D^+$ *J*=3-2 from Band 6 observations and $\rm H^{13}CO^+$ *J*=1-0 from Band 3 observations (cite: 2022MNRAS.510.5009L) to estimate the thermal velocity dispersion $\sigma_{\rm th}$ and non-thermal (turbulence) velocity dispersion $\sigma_{\rm nt}$. The total velocity dispersion is $\sigma_v^2=\sigma_{\rm th}^2+\sigma_{\rm nt}^2$, where $\sigma_{\rm th}=\sqrt{k_B T/\mu m_H}$. On the core scale, we obtain $\sigma_v=0.73\,{\rm km~s}^{-1}$ for $\rm N_2D^+$ and $0.46\,{\rm km~s}^{-1}$ for $\rm H^{13}CO^+$. We note that the velocity dispersion measured from gaussian fit of $\rm N_2D^+$ should be treated as an upper limit because of its hyperfine structure. We use the same $\sigma_v$ for the two condensations in virial analysis. If we assume the gas temperature is 14.2 K, the thermal sound speed is $c_s=0.22\,{\rm km~s}^{-1}$. The non-thermal velocity dispersion $\sigma_{\rm nt}=0.72\,{\rm km~s}^{-1}$ for $\rm N_2D^+$ and 0.45$\,{\rm km~s}^{-1}$ for $\rm H^{13}CO^+$ . The effective sound speed considering thermal and turbulent motion $c_{\rm s}^{\rm eff}=\sqrt{c_s^2+\sigma_{\rm nt}^2}$ is 0.76 and 0.50$\,{\rm km~s}^{-1}$ for $\rm N_2D^+$ and $\rm H^{13}CO^+$, respectively. The virial parameter $\alpha_{\rm vir}=M_{\rm vir}/M_{\rm gas}=5\sigma_{\rm 3D}^2 R_{\rm eff}/G M_{\rm gas}$, where the 3D velocity dispersion is $\sigma_{\rm 3D}=\sqrt{3}c_{\rm s}^{\rm eff}$. The derived virial parameters are listed in Table [1](#tab:dynamics). We also derive virial parameters assuming a gas temperature of 10$\,$K or 6.5 K.

The virial parameter of the core MM1-C is $\alpha_{\rm vir}$ = 0.3–0.8, lower than the critical limit, which suggests that the whole core is likely collapsing if additional support from the magnetic field is ignored. Therefore, MM1-C is a good candidate to be a massive prestellar core. We note that the condensation C1 is trans- or sub-virial except for the temperature of 14.2 K, while C2 is always sub-virial. Note also, that the parent core MM1-C appears more bound than the substructures. This is consistent with (cite: 2021MNRAS.502.4963G), which shows that for any collapsing object with a density profile shallower than $r^{-2}$, the central region will appear unbound. However, half of the super-viral objects in the simulation of (cite: 2016ApJ...833..113C) are contracting instead of being unbound, indicating that the external turbulent compressions provide the assembly of the gas. As their masses grow, gravitational contractions will take over. Since the natal core is in overall collapse, the $M_{\rm gas}$ of C1 and C2 should further grow continuously via gas accretion. Therefore, both C1 and C2 are already contracting or will likely be gravitationally bound in the future.

A core or condensation will fragment if the physical size is larger than Jeans length, when the internal pressure (thermal+turbulence) can not prevail over gravity. The Jeans length is given as (cite: 2014MNRAS.439.3275W)

$$\begin{align}
    L_{\rm J} &=c^{\rm eff}_s\left(\frac{\pi}{G\rho}\right)^{1/2} \\
    &=0.06\,{\rm pc} \left(\frac{\sigma_v}{0.188\,{\rm km~s}^{-1}}\right)\left(\frac{n}{10^5\, {\rm cm}
^{-3}}\right)^{-1/2},\notag
    \label{equation: jl}
\end{align}$$ and the corresponding Jeans Mass is given by $$\begin{align}
    M_{\rm J}&=\frac{\pi^{5/2}{c_s^{\rm eff}}^3}{6\sqrt{G^3\rho}} \\
    &=0.8\,M_{\odot}\left(\frac{\sigma_v}{0.188\,{\rm km~s}^{-1}}\right)\left(\frac{n}{10^5\, {\rm cm}^{-3}}\right)^{-1/2}. \notag
    \label{equation:mj}
\end{align}$$

We use $\rm N_2D^+$ and $\rm H^{13}CO^+$ to determine the stability of C1 and C2. The Jeans lengths and the estimated Jeans masses are summarized in Table [1](#tab:dynamics). As the temperature is varied from 6.5 to 14 K, C1 has a size larger than the Jeans length when $T_{\rm gas}$ is slightly higher than 6.5 K, suggesting C1 is Jeans unstable only when $T_{\rm gas} \lesssim 6.5$ K. C2 has a size larger than the Jeans length corresponding to $T_{\rm gas}$ of 10–14 K, suggesting that C2 is likely Jeans unstable and would undergo further fragmentation.

Interestingly, alongside the two notable condensations C1 and C2, two looming substructures are seen inside C2 with a separation of 0.3$\ensuremath{''}$ ($\sim$900 au). As this separation is comparable to the synthesis beam size, *Dendrogram* can not resolve these two peaks. These two substructures indicate that C2 itself is already undergoing further fragmentation, which can be tested by future higher-resolution observations.

Compact substructures have been detected in low-mass prestellar cores such as G205-M3 (cite: 2021ApJ...907L..15S), while fragmentation in massive prestellar cores is rarely reported. We have detected extremely dense substructures within MM1-C, representing the primordial fragmentation within a massive prestellar core. Statistic surveys of massive multiple systems reveal that the distribution of the mass ratio $q=M_{\rm comp}/M_{\rm prim}$ exhibits a peak at 0.3–0.5 for wide multiple systems, where $M_{\rm comp}$ is the mass of the companion and $M_{\rm prim}$ is the mass of the primary, accompanied by the negative power-law index(cite: 2013ARA&A..51..269D; 2023ASPC..534..275O). That is to say, the massive wide multiple systems favor low-mass companions. Therefore we speculate that the massive prestellar core MM1-C will eventually form a multiple stellar system with one massive primary and 1–2 lower-mass companions. However, we cannot fully rule out the possibility that the massive prestellar core MM1-C could undergo further fragmentation and give birth to a cluster of low-mass stars eventually.

## Cold Filaments Traced by $\rm N_2D^+$ 

As shown in Fig. [2](#fig:spectra), $\rm N_2D^+$ is detected firmly toward core MM1-C. To increase the signal-to-noise ratio, the $\rm N_2D^+$ data was smoothed to 1$''$ resolution. Shown in Fig. [3](#fig:n2dp), MM1-C appears to be situated at one end of a 0.3 pc-long thin structure traced by $\rm N_2D^+$ with a clear velocity gradient. This thin structure seems to trace two filaments connecting dense cores: the southern filament is a gas bridge connecting MM1-C and MM1-F, and the northern filament extends to the filament hub region close to MM1-A.

We extracted a position-velocity (PV) diagram along the filaments. By fitting the PV diagram, we determined the velocity gradients of $\sim$ 15 and 10 $\rm km~s^{-1}~pc^{-1}$ for the southern and northern filaments, respectively. The velocity gradients are quite comparable with the velocity gradients along small-scale filaments in other observations of massive star forming regions (cite: 2021ApJ...915L..10S; 2022MNRAS.514.6038Z; Hacar2023; 2023MNRAS.520.3259X) and also in simulations (cite: 2020MNRAS.492.1594S). Through the filaments, cold unbounded gas from the envelope of the clump could be channeled to dense cores (cite: Kirk2013), further increasing their gas masses.

## Indications to high-mass star formation Models

Our observations reveal a very promising massive prestellar core (MM1-C) that seems to align with the *Turbulent Core* model. However, the presence of internal fragmentation and the identification of a cold gas filament connecting to the core (MM1-C) challenges the model’s expectation of forming a high-mass star through monolithic collapse of an isolated and centrally concentrated core. On the contrary, the presence of a cold filament seem to follow the competitive accretion scenario or other “clump-fed" models that suggest dynamical mass inflow beyond cores in high-mass star formation. However, the initial conditions in those “clump-feed" models do not favor the existence of a massive prestellar core with such a large gas mass . The complexities in our observations pose questions about the dynamics of massive star formation. The coexistence of massiveness with internal fragmentation and ongoing accretion in core MM1-C underscores the need for more comprehensive comparisons between theories and observations in future studies.

# Conclusions

We present the new ALMA Band 6 continuum and line observations toward the G34-MM1 clump. Accompanied by ATOMS Band 3 data, we report the discovery of two massive prestellar core candidates MM1-C and E1. The line-poor spectra and the absence of outflows suggest their prestellar nature. Their total gas masses are 70 and 20 $M_{\odot}$ for MM1-C and E1, respectively. Band 6 observations of $\sim$ 0.3$''$ resolution show that MM1-E1 remains a singular condensation at this resolution. On the other hand, MM1-C is found to be fragmented into two condensations C1 and C2, with mass estimates ranging 1.9–7.0 and 6.5–24.3 $M_{\odot}$, respectively, assuming the temperature is in the range of 6.5–14.2 K. The effective radii are 700 and 1380 au for C1 and C2, resulting in an extremely high density $\rm n_{H_2}\sim 10^{8-9} cm^{-3}$. Condensation C1 is found to be Jeans stable if $T_{\rm gas} \gtrsim 6.5$ K, while C2 is Jeans unstable when $T_{\rm gas} \lesssim 14.2$ K. In addition, C2 seems to have begun to further fragment into two substructures, hinting at its thermal instability. We also detected two gas filaments in $\rm N_2D^+$ line emission, one connecting core MM1-C to MM1-F, and another extending from MM1-F to the central hub region. Both filaments show a clear velocity gradient of 10–15 $\rm km~s^{-1}~pc^{-1}$. The core MM1-C may further accumulate gas mass along the filament.

To conclude, we detected a fragmenting massive prestellar core candidate, which may give birth to a multiple stellar system containing high-mass star(s).

# Acknowledgements

This work has been supported by the National Key R$\&$D Program of China (No. 2022YFA1603101), and National Natural Science Foundation of China (NSFC) through grants No. 12073061, 12122307, 12203086, 12103045, and 12033005.

T.L. acknowledges the supports by the international partnership program of Chinese Academy of Sciences through grant No.114231KYSB20200009, and Shanghai Pujiang Program 20PJ1415500.

X.L. is also support by CPSF No. 2022M723278.

H.-L. Liu is supported by Yunnan Fundamental Research Project (grant No. 202301AT070118).

M.J. acknowledges the support of the Research Council of Finland grant No. 348342.

E.M. is funded by the University of Helsinki doctoral school in particle physics and universe sciences (PAPU).

This research was carried out in part at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with the National Aeronautics and Space Administration (80NM0018D0004).

PS was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI Number JP22H01271 and JP23H01221) of JSPS.

G.G and L.B. gratefully acknowledge support from the ANID BASAL project FB210003.

B.Z. acknowledges support by the Natural Science Foundation of China (NSFC, grant No. U1831136 and U2031212) and Shanghai Astronomical Observatory (N-2020-06-09-005).

The work of Q-L.G. is supported by Shanghai Rising-Star Program (23YF1455600)

K.T. was supported by JSPS KAKENHI (Grant Number JP20H05645).

Y.P. Peng acknowledges support from NSFC through grant No. 12303028.

C.W.L. is supported by the Basic Science Research Program through the National Research Foundation of Korea (NRF) funded by the Ministry of Education, Science and Technology (NRF-2019R1A2C1010851) and by the Korea Astronomy and Space Science Institute grant funded by the Korea government (MSIT; Project No. 2023-1-84000).

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00685.S, 2021.1.00095.S and 2023.1.00425. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# Facilities

ALMA

# Software

astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A), CASA (cite: 2022PASP..134k4501C), CARTA (cite: 2021ascl.soft03031C), Astrodendro (cite: 2008ApJ...679.1338R)

# Integrated intensity maps of CH$_3$OH lines

Fig. [4](#fig:appendixa) shows the integrated intensity maps of CH$_3$OH $4_2$-$3_1$ (rest frequency: 218.440063 GHz; E$_u$=45.46 K) at Band 6 and another low excitation transition CH$_3$OH 2(1,1)–1(1,0)A (rest frequency: 97.582798 GHz; E$_u$=21.56 K) at Band 3. Panel (a) in Fig. [4](#fig:appendixa) with negative and positive contours demonstrates that the absorption features like CH$_3$OH seen in the spectra in Fig. [2](#fig:spectra) could be due to the missing flux issue in interferometric observations. As shown in Panel (b), the low excitation transition line CH$_3$OH 2(1,1)–1(1,0)A as extended as the high excitation one shown in Panel (a), while no emission or absorption is detected toward MM1-C. That means CH$_3$OH is still frozen onto dust grain in such a relatively cold environment. The other molecules such as H$_2$CO and C$^{18}$O are similar to CH$_3$OH toward MM1-C.

![](fig/appendixa.pdf)

# Spectra at the continuum emission peak of MM1-C1

Figure [5](#fig:appendixb) presents the beam-averaged spectra at Band 6 toward the continuum emission peak of MM1-C1. No absorption features are seen in H$_2$CO and CH$_3$OH lines, indicating that there are no warm or hot continuum background sources within MM1-C1.

![](fig/peakspw.pdf)

# CO outflows

To better illustrate the starless characteristics of core MM1-C, we integrated the blue and red wings of the CO high-velocity emission. As Fig. [5](#fig:appendixb) shows, G34-MM1 clump shows complicated outflow activities, which will be fully explored in a forthcoming paper. However, no CO outflow emission originates from either core MM1-C or MM1-E1.

![](fig/cooutflow.pdf)

natexlab

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2023A&A...675A..53B) Barnes, A. T., Liu, J., Zhang, Q., et al. 2023, A&A, 675, A53, doi: [`10.1051/0004-6361/202245668`](http://doi.org/10.1051/0004-6361/202245668)

(ref: Benedettini2018) Benedettini, M., Pezzuto, S., Schisano, E., et al. 2018, A&A, 619, A52, doi: [`10.1051/0004-6361/201833364`](http://doi.org/10.1051/0004-6361/201833364)

(ref: 2001MNRAS.323..785B) Bonnell, I. A., Bate, M. R., Clarke, C. J., & Pringle, J. E. 2001, MNRAS, 323, 785, doi: [`10.1046/j.1365-8711.2001.04270.x`](http://doi.org/10.1046/j.1365-8711.2001.04270.x)

(ref: 2010A&A...524A..18B) Bontemps, S., Motte, F., Csengeri, T., & Schneider, N. 2010, A&A, 524, A18, doi: [`10.1051/0004-6361/200913286`](http://doi.org/10.1051/0004-6361/200913286)

(ref: 2016ApJ...833..113C) Camacho, V., Vázquez-Semadeni, E., Ballesteros-Paredes, J., et al. 2016, ApJ, 833, 113, doi: [`10.3847/1538-4357/833/1/113`](http://doi.org/10.3847/1538-4357/833/1/113)

(ref: 2022PASP..134k4501C) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: 2019ApJ...874...89C) Caselli, P., Pineda, J. E., Zhao, B., et al. 2019, ApJ, 874, 89, doi: [`10.3847/1538-4357/ab0700`](http://doi.org/10.3847/1538-4357/ab0700)

(ref: 2021ascl.soft03031C) Comrie, A., Wang, K.-S., Hsu, S.-C., et al. 2021, CARTA: Cube Analysis and Rendering Tool for Astronomy, Astrophysics Source Code Library, record ascl:2103.031. [`http://ascl.net/2103.031`](http://ascl.net/2103.031)

(ref: 2007A&A...470..221C) Crapsi, A., Caselli, P., Walmsley, M. C., & Tafalla, M. 2007, A&A, 470, 221, doi: [`10.1051/0004-6361:20077613`](http://doi.org/10.1051/0004-6361:20077613)

(ref: 2013ARA&A..51..269D) Duchêne, G., & Kraus, A. 2013, ARA&A, 51, 269, doi: [`10.1146/annurev-astro-081710-102602`](http://doi.org/10.1146/annurev-astro-081710-102602)

(ref: 2023A&A...670A...9D) Dzib, S. A., Yang, A. Y., Urquhart, J. S., et al. 2023, A&A, 670, A9, doi: [`10.1051/0004-6361/202143019`](http://doi.org/10.1051/0004-6361/202143019)

(ref: 2014ApJ...791..108F) Foster, J. B., Arce, H. G., Kassis, M., et al. 2014, ApJ, 791, 108, doi: [`10.1088/0004-637X/791/2/108`](http://doi.org/10.1088/0004-637X/791/2/108)

(ref: 2004ApJ...610..313G) Garay, G., Faúndez, S., Mardones, D., et al. 2004, ApJ, 610, 313, doi: [`10.1086/421437`](http://doi.org/10.1086/421437)

(ref: 2021MNRAS.502.4963G) Gómez, G. C., Vázquez-Semadeni, E., & Palau, A. 2021, MNRAS, 502, 4963, doi: [`10.1093/mnras/stab394`](http://doi.org/10.1093/mnras/stab394)

(ref: Hacar2023) Hacar, A., Clark, S. E., Heitsch, F., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 153, doi: [`10.48550/arXiv.2203.09562`](http://doi.org/10.48550/arXiv.2203.09562)

(ref: Kirk2013) Kirk, H., Myers, P. C., Bourke, T. L., et al. 2013, ApJ, 766, 115, doi: [`10.1088/0004-637X/766/2/115`](http://doi.org/10.1088/0004-637X/766/2/115)

(ref: 2023ApJ...949..109L) Li, S., Sanhueza, P., Zhang, Q., et al. 2023, ApJ, 949, 109, doi: [`10.3847/1538-4357/acc58f`](http://doi.org/10.3847/1538-4357/acc58f)

(ref: 2020ApJ...901...31L) Liu, H.-L., Sanhueza, P., Liu, T., et al. 2020a, ApJ, 901, 31, doi: [`10.3847/1538-4357/abadfe`](http://doi.org/10.3847/1538-4357/abadfe)

(ref: 2021MNRAS.505.2801L) Liu, H.-L., Liu, T., Evans, Neal J., I., et al. 2021a, MNRAS, 505, 2801, doi: [`10.1093/mnras/stab1352`](http://doi.org/10.1093/mnras/stab1352)

(ref: 2022MNRAS.510.5009L) Liu, H.-L., Tej, A., Liu, T., et al. 2022, MNRAS, 510, 5009, doi: [`10.1093/mnras/stab2757`](http://doi.org/10.1093/mnras/stab2757)

(ref: Liu2017) Liu, T., Lacy, J., Li, P. S., et al. 2017, ApJ, 849, 25, doi: [`10.3847/1538-4357/aa8d73`](http://doi.org/10.3847/1538-4357/aa8d73)

(ref: 2020MNRAS.496.2790L) Liu, T., Evans, N. J., Kim, K.-T., et al. 2020b, MNRAS, 496, 2790, doi: [`10.1093/mnras/staa1577`](http://doi.org/10.1093/mnras/staa1577)

(ref: liu2023almaquarks) Liu, X., Liu, T., Zhu, L., et al. 2023, The ALMA-QUARKS survey: – I. Survey description and data reduction. [`https://arxiv.org/abs/2311.08651`](https://arxiv.org/abs/2311.08651)

(ref: 2021ApJ...912..148L) Liu, X. C., Wu, Y., Zhang, C., et al. 2021b, ApJ, 912, 148, doi: [`10.3847/1538-4357/abee73`](http://doi.org/10.3847/1538-4357/abee73)

(ref: 2014ApJ...790...84L) Lu, X., Zhang, Q., Liu, H. B., Wang, J., & Gu, Q. 2014, ApJ, 790, 84, doi: [`10.1088/0004-637X/790/2/84`](http://doi.org/10.1088/0004-637X/790/2/84)

(ref: 2023ApJ...949...10M) Mai, X., Zhang, B., Reid, M. J., et al. 2023, ApJ, 949, 10, doi: [`10.3847/1538-4357/acc52a`](http://doi.org/10.3847/1538-4357/acc52a)

(ref: 2003ApJ...585..850M) McKee, C. F., & Tan, J. C. 2003, ApJ, 585, 850, doi: [`10.1086/346149`](http://doi.org/10.1086/346149)

(ref: 2021ApJ...923..147M) Morii, K., Sanhueza, P., Nakamura, F., et al. 2021, ApJ, 923, 147, doi: [`10.3847/1538-4357/ac2365`](http://doi.org/10.3847/1538-4357/ac2365)

(ref: 2023ApJ...950..148M) —. 2023, ApJ, 950, 148, doi: [`10.3847/1538-4357/acccea`](http://doi.org/10.3847/1538-4357/acccea)

(ref: Motte2018) Motte, F., Nony, T., Louvet, F., et al. 2018, Nature Astronomy, 2, 478, doi: [`10.1038/s41550-018-0452-x`](http://doi.org/10.1038/s41550-018-0452-x)

(ref: 2018A&A...618L...5N) Nony, T., Louvet, F., Motte, F., et al. 2018, A&A, 618, L5, doi: [`10.1051/0004-6361/201833863`](http://doi.org/10.1051/0004-6361/201833863)

(ref: 2023ASPC..534..275O) Offner, S. S. R., Moe, M., Kratter, K. M., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 275, doi: [`10.48550/arXiv.2203.10066`](http://doi.org/10.48550/arXiv.2203.10066)

(ref: 1994A&A...291..943O) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: 2020ApJ...900...82P) Padoan, P., Pan, L., Juvela, M., Haugbølle, T., & Nordlund, Å. 2020, ApJ, 900, 82, doi: [`10.3847/1538-4357/abaa47`](http://doi.org/10.3847/1538-4357/abaa47)

(ref: 2013ApJ...762..120P) Palau, A., Fuente, A., Girart, J. M., et al. 2013, ApJ, 762, 120, doi: [`10.1088/0004-637X/762/2/120`](http://doi.org/10.1088/0004-637X/762/2/120)

(ref: 1994ApJ...421..615P) Pollack, J. B., Hollenbach, D., Beckwith, S., et al. 1994, ApJ, 421, 615, doi: [`10.1086/173677`](http://doi.org/10.1086/173677)

(ref: Pouteau2022) Pouteau, Y., Motte, F., Nony, T., et al. 2022, A&A, 664, A26, doi: [`10.1051/0004-6361/202142951`](http://doi.org/10.1051/0004-6361/202142951)

(ref: 2022MNRAS.511.3463Q) Qin, S.-L., Liu, T., Liu, X., et al. 2022, MNRAS, 511, 3463, doi: [`10.1093/mnras/stac219`](http://doi.org/10.1093/mnras/stac219)

(ref: 2005ApJ...630L.181R) Rathborne, J. M., Jackson, J. M., Chambers, E. T., et al. 2005, ApJL, 630, L181, doi: [`10.1086/491656`](http://doi.org/10.1086/491656)

(ref: 2008ApJ...679.1338R) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ, 679, 1338, doi: [`10.1086/587685`](http://doi.org/10.1086/587685)

(ref: 2021ApJ...907L..15S) Sahu, D., Liu, S.-Y., Liu, T., et al. 2021, ApJL, 907, L15, doi: [`10.3847/2041-8213/abd3aa`](http://doi.org/10.3847/2041-8213/abd3aa)

(ref: 2013ApJ...775L..31S) Sakai, T., Sakai, N., Foster, J. B., et al. 2013, ApJL, 775, L31, doi: [`10.1088/2041-8205/775/1/L31`](http://doi.org/10.1088/2041-8205/775/1/L31)

(ref: 2010ApJ...715...18S) Sanhueza, P., Garay, G., Bronfman, L., et al. 2010, ApJ, 715, 18, doi: [`10.1088/0004-637X/715/1/18`](http://doi.org/10.1088/0004-637X/715/1/18)

(ref: 2012ApJ...756...60S) Sanhueza, P., Jackson, J. M., Foster, J. B., et al. 2012, ApJ, 756, 60, doi: [`10.1088/0004-637X/756/1/60`](http://doi.org/10.1088/0004-637X/756/1/60)

(ref: 2017ApJ...841...97S) Sanhueza, P., Jackson, J. M., Zhang, Q., et al. 2017, ApJ, 841, 97, doi: [`10.3847/1538-4357/aa6ff8`](http://doi.org/10.3847/1538-4357/aa6ff8)

(ref: 2019ApJ...886..102S) Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886, 102, doi: [`10.3847/1538-4357/ab45e9`](http://doi.org/10.3847/1538-4357/ab45e9)

(ref: 2021ApJ...915L..10S) Sanhueza, P., Girart, J. M., Padovani, M., et al. 2021, ApJL, 915, L10, doi: [`10.3847/2041-8213/ac081c`](http://doi.org/10.3847/2041-8213/ac081c)

(ref: 2001ApJ...551..747S) Simon, R., Jackson, J. M., Clemens, D. P., Bania, T. M., & Heyer, M. H. 2001, ApJ, 551, 747, doi: [`10.1086/320230`](http://doi.org/10.1086/320230)

(ref: 2006ApJ...653.1325S) Simon, R., Rathborne, J. M., Shah, R. Y., Jackson, J. M., & Chambers, E. T. 2006, ApJ, 653, 1325, doi: [`10.1086/508915`](http://doi.org/10.1086/508915)

(ref: 2020MNRAS.492.1594S) Smith, R. J., Treß, R. G., Sormani, M. C., et al. 2020, MNRAS, 492, 1594, doi: [`10.1093/mnras/stz3328`](http://doi.org/10.1093/mnras/stz3328)

(ref: 2019ApJ...883...95S) Soam, A., Liu, T., Andersson, B. G., et al. 2019, ApJ, 883, 95, doi: [`10.3847/1538-4357/ab39dd`](http://doi.org/10.3847/1538-4357/ab39dd)

(ref: 2021ApJ...923..231S) Spear, S., Maureira, M. J., Arce, H. G., et al. 2021, ApJ, 923, 231, doi: [`10.3847/1538-4357/ac3083`](http://doi.org/10.3847/1538-4357/ac3083)

(ref: 2009ApJ...707.1023V) Vázquez-Semadeni, E., Gómez, G. C., Jappsen, A. K., Ballesteros-Paredes, J., & Klessen, R. S. 2009, ApJ, 707, 1023, doi: [`10.1088/0004-637X/707/2/1023`](http://doi.org/10.1088/0004-637X/707/2/1023)

(ref: 2019MNRAS.490.3061V) Vázquez-Semadeni, E., Palau, A., Ballesteros-Paredes, J., Gómez, G. C., & Zamora-Avilés, M. 2019, MNRAS, 490, 3061, doi: [`10.1093/mnras/stz2736`](http://doi.org/10.1093/mnras/stz2736)

(ref: 2014MNRAS.439.3275W) Wang, K., Zhang, Q., Testi, L., et al. 2014, MNRAS, 439, 3275, doi: [`10.1093/mnras/stu127`](http://doi.org/10.1093/mnras/stu127)

(ref: Xu2023ASSEMBLE) Xu, F., Wang, K., Liu, T., et al. 2023a, arXiv e-prints, arXiv:2309.14684, doi: [`10.48550/arXiv.2309.14684`](http://doi.org/10.48550/arXiv.2309.14684)

(ref: 2023MNRAS.520.3259X) Xu, F.-W., Wang, K., Liu, T., et al. 2023b, MNRAS, 520, 3259, doi: [`10.1093/mnras/stad012`](http://doi.org/10.1093/mnras/stad012)

(ref: 2016ApJ...819..117X) Xu, J.-L., Li, D., Zhang, C.-P., et al. 2016, ApJ, 819, 117, doi: [`10.3847/0004-637X/819/2/117`](http://doi.org/10.3847/0004-637X/819/2/117)

(ref: 2018ApJS..235....3Y) Yang, A. Y., Thompson, M. A., Urquhart, J. S., & Tian, W. W. 2018, ApJS, 235, 3, doi: [`10.3847/1538-4365/aaa297`](http://doi.org/10.3847/1538-4365/aaa297)

(ref: 2022A&A...658A.160Y) Yang, A. Y., Urquhart, J. S., Wyrowski, F., et al. 2022, A&A, 658, A160, doi: [`10.1051/0004-6361/202142039`](http://doi.org/10.1051/0004-6361/202142039)

(ref: 2023arXiv231009777Y) Yang, A. Y., Dzib, S. A., Urquhart, J. S., et al. 2023, arXiv e-prints, arXiv:2310.09777, doi: [`10.48550/arXiv.2310.09777`](http://doi.org/10.48550/arXiv.2310.09777)

(ref: 2005ApJ...627..293Y) Young, C. H., & Evans, Neal J., I. 2005, ApJ, 627, 293, doi: [`10.1086/430436`](http://doi.org/10.1086/430436)

(ref: 2022MNRAS.514.6038Z) Zhou, J.-W., Liu, T., Evans, N. J., et al. 2022, MNRAS, 514, 6038, doi: [`10.1093/mnras/stac1735`](http://doi.org/10.1093/mnras/stac1735)

[^1]: E-mail:maixf@shao.ac.cn

[^2]: E-mail:liutie@shao.ac.cn

[^3]: E-mail:zb@shao.ac.cn

[^4]: The mass in (cite: 2022MNRAS.510.5009L) was estimated based on the kinematic distance (cite: 2001ApJ...551..747S; 2006ApJ...653.1325S). Those values in this paper are corrected using the parallax distance in (cite: 2023ApJ...949...10M).

[^5]: ALMA proposal guide:[https://almascience.eso.org/proposing/proposers-guide##autotoc-item-autotoc-79](https://almascience.eso.org/proposing/proposers-guide##autotoc-item-autotoc-79)

[^6]: An intensity threshold of 2.5$\sigma_{\rm b6}$, step of 1$\sigma_{\rm b6}$, and a minimum pixel number contained in a restoring beam, 44 in this case, were fed into the *Dendrogram* algorithm.

</paper>

Write the methods card for this paper.