# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...985...84L\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2025ApJ...985...84L",
 "title": "A Multiline Analysis of the Distribution and Excitation of CS and H<SUB>2</SUB>CS in the HD 163296 Disk",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Law, Charles J.",
 "n_authors": 9,
 "arxiv_id": "2503.16605",
 "doi": "10.3847/1538-4357/adc304",
 "alma_projects_linked_by_archive": [
  "2015.1.00847.S",
  "2015.1.01137.S",
  "2016.1.00884.S",
  "2016.1.01086.S",
  "2017.1.01682.S",
  "2018.1.01055.L",
  "2021.1.00535.S",
  "2021.1.00899.S"
 ]
}
```

Paper text:
<paper>
# A Multi-line Analysis of the Distribution and Excitation of CS and H$_2$CS in the HD 163296 Disk

## Abstract

The abundance and distribution of sulfur-bearing molecules in protoplanetary disks directly influences the composition and potential habitability of nascent planets in addition to providing powerful probes of the physical gas conditions in the disks themselves. Here, we present new and archival ALMA and SMA observations of CS and H$_2$CS, and their C$^{34}$S and H$_2$C$^{34}$S isotopologues, at high-angular resolution (${\approx}$0.2$''$-0.4$''$; 20-40 au) in the HD 163296 disk, which reveal a central cavity and multi-ringed emission structure. These observations comprise the most comprehensive, multi-line CS data in a planet-forming disk to date, spanning a wide range of excitation conditions from E$_{\rm{u}}$=7.1 K to 129.3 K, and include new detections of C$^{34}$S, H$_2$CS, and H$_2$C$^{34}$S in this system. Using these data, we derive spatially-resolved rotational temperature and column density profiles for all species. We find a column density ratio N(H$_2$CS)/N(CS) $\approx$ 0.5, which is comparable to that of the similar MWC 480 disk and suggests that organic sulfur compounds may constitute a large fraction of the volatile sulfur reservoir in disks around Herbig stars generally. We derive $^{32}$S/$^{34}$S ratios of ${\approx}$5 (CS/C$^{34}$S) and ${\approx}$2 (H$_2$CS/H$_2$C$^{34}$S) based on disk-averaged and spatially-resolved analyses. Both values are consistent across these two pairs of optically-thin molecules and are well-below the expected ISM ratio of ${\approx}$22, suggesting significant sulfur fractionation. We also constrain the CS emitting layer ($z/r\lesssim 0.1$) using the vertical separations of the disk surfaces in the channel maps and based on the known 2D gas structure of the HD 163296 disk combined with our excitation analysis.

# Introduction

The chemical and physical structure of protoplanetary disks is tightly linked to the properties of nascent planets. Thanks to the high resolution of the Atacama Large Millimeter/submillimeter Array (ALMA), the molecular gas content of disks has now begun to be mapped in fine detail (cite: Bergner19; Miotello19; Oberg21_MAPSI; Booth24_HD100546; Rampinelli24). While many studies have focused on carbon-, oxygen-, and nitrogen-bearing molecules, relatively few have targeted sulfur-bearing species, despite the importance of sulfur for prebiotic chemistry and in determining potential planet habitability (cite: Chen15; Ranjan18).

Only a few sulfur-bearing species have been detected in disks. CS is the most commonly-observed molecule (cite: Dutrey97; vanderPlas14; Guilloteau16; Semenov18; Legal19; Legal21; Rosotti21; Teague22), followed by a handful of detections of H$_2$CS, CCS, and H$_2$S (cite: Phuong18; Legal19; Loomis20; Phuong21; Marichalar22; Booth23_HD169142). Oxygenated species such as SO and SO$_2$ are rare and have been mostly seen in younger disks with signs of active accretion, large-scale structures, and/or planet-induced shocks (cite: Fuente10; Pacheco16; Garufi22; Law23_HD16; Booth23; Booth24_IRS48; Huang24; Yoshida24; Dutrey24; Speedie25), indicating that the bulk of disk gas is, in general, likely highly-reduced. Few of these studies, however, possessed sufficiently high sensitivity and angular resolution while covering multiple lines spanning a range of excitation conditions necessary to constrain gas physical conditions in detail, even in the commonly-observed CS molecule. Such observations are required to capture important spatial variations across disks, e.g., at the location of dust gaps commonly associated with ongoing planet formation. Given its ease of detection in surveys and use as a tracer of disk gas properties (cite: Teague16; Teague18_CS), understanding the detailed distribution and excitation of CS is of critical importance.

Moreover, the exact nature of the sulfur reservoir in disks remains highly uncertain. Many S-bearing species not yet detected in either the interstellar medium (ISM) or disks are readily observed in Solar System objects, including comets and meteorites (cite: Jewitt97; BM04; Biver16; Calmonte16; Paquette17; Altwegg22). Chemical models suggest that volatile sulfur is significantly depleted in protoplanetary disks (cite: Legal21; Keyte24; Keyte24_HD169142) and much of this missing sulfur may be locked up in the mantles of icy dust grains (cite: Millar90; Ruffle99; Laas19; Fuente23) or in refractory components (cite: Kama19). However, only a small fraction (few percent) of sulfur has been detected in interstellar ices (cite: Boogert15), while gas-phase H$_2$S has only been detected in two Class II disks so far (cite: Dutrey11; Phuong18; Marichalar22), despite it being the main sulfur-carrier in comet 67P/C-G (cite: Calmonte16). Overall, this means that the distribution of sulfur-containing materials, including the volatile sulfur budget, is still poorly-constrained in disks.

Recent ALMA results, however, have begun to offer additional insights into disk sulfur chemistry (cite: Semenov18; Law23_HD16; Keyte23; Keyte24; Booth24_IRS48; Dutrey24). For instance, (cite: Legal19; Legal21) found an unexpectedly elevated column density ratio of H$_2$CS with respect to CS in the disk around the Herbig star MWC 480, which suggests that a substantial part of this sulfur reservoir may be in the form of organic compounds. Additionally, (cite: Booth24) identified potentially anomalous, non-ISM sulfur isotopic ratios in the IRS 48 disk, which indicates that significant fractionation may be taking place. Taken together, these findings imply that observations of more complex, organic species such as H$_2$CS in addition to simple molecules like CS along with their respective isotopologues provide one promising avenue to constrain this underlying sulfur reservoir, and to address the importance of inheritance versus *in situ* disk processes that may, in turn, alter this reservoir.

In this paper, we present the most comprehensive set of CS lines at high spatial resolution in a protoplanetary disk to date. We also include new detections of C$^{34}$S, H$_2$CS, and H$_2$C$^{34}$S in the HD 163296 disk. We use these new observations to derive spatially-resolved excitation conditions and sulfur isotopic ratios. In Section [2](#sec:HD163296_disk), we briefly describe the HD 163296 disk and summarize the ALMA and SMA archival observations used in this work in Section [3](#sec:observations_overview). We present our results in Section [4](#sec:results) and discuss the origins of the observed emission, including enhanced $^{34}$S isotopic ratios, and compare the sulfur chemistry in HD 163296 to that of other disks in Section [5](#sec:discussion). We summarize our conclusions in Section [6](#sec:conlcusions).

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Transition | Freq. | Beam | `robust` | $\delta$v | RMS | Project | E$_{\rm{u}}$ | A$_{\rm{ul}}$ | g$_{\rm{u}}$ | Int. Flux$^{a}$ |  |  |  |  |
|  | (GHz) | ($^{\prime \prime} \times ^{\prime \prime}$, $\deg$) |  | (km s$^{-1}$) | (mJy beam$^{-1}$) | Used | \(K\) | ($\log_{10}$ s$^{-1}$) |  | (Jy km s$^{-1}$) |  |  |  |  |
| CS J=2–1 | 97.980953 | 0.30$\times$0.30, 0.0 | 0.5, taper | 0.50 | 0.55 | 2018.1.01055.L | 7.1 | $-$4.776 | 5 | 0.307 $\pm$ 0.017 |  |  |  |  |
| CS J=3–2 | 146.969029 | 0.23$\times$0.18,$-$76.1 | 2.0, taper | 0.15 | 2.0 | 2017.1.01682.S | 14.1 | $-$4.218 | 7 | 1.195 $\pm$ 0.025 |  |  |  |  |
| CS J=4–3 | 195.954211 | 0.33$\times$0.33, 0.0 | 0.3, taper | 0.22 | 1.1 | 2021.1.00899.S | 23.5 | $-$3.828 | 9 | 1.779 $\pm$ 0.060 |  |  |  |  |
| CS J=5–4 | 244.935557 | 3.40$\times$2.74, 1.0 | 2.0 | 1.00 | 72.5 | 2020A-S018 | 35.3 | $-$3.527 | 11 | 1.759 $\pm$ 0.193 |  |  |  |  |
| CS J=7–6 | 342.882850 | 0.21$\times$0.21, 88.3 | 0.5, taper | 0.86 | 4.2 | 2016.1.01086.S | 65.8 | $-$3.077 | 15 | ${>}$1.415$^{b}$ |  |  |  |  |
| CS J=8–7 | 391.846890 | 0.35$\times$0.35, 0.0 | 0.5, taper | 0.75 | 11.8 | 2015.1.00847.S | 84.6 | $-$2.900 | 17 | 2.602 $\pm$ 0.370 |  |  |  |  |
| CS J=10–9 | 489.750921 | 0.86$\times$0.66, $-$76.0 | 2.0 | 0.15 | 65.8 | 2015.1.01137.S | 129.3 | $-$2.604 | 21 | 1.334 $\pm$ 0.165 |  |  |  |  |
| C$^{34}$S J=5–4 | 241.016089 | 0.52$\times$0.38, 77.4 | 0.5 | 0.31 | 2.4 | 2016.1.00884.S | 34.7 | $-$3.557 | 11 | 0.287 $\pm$ 0.030 |  |  |  |  |
| C$^{34}$S J=6–5 | 289.209068 | 0.38$\times$0.26, 69.1 | 0.5 | 0.13 | 1.4 | 2021.1.00535.S | 48.6 | $-$3.318 | 13 | 0.190 $\pm$ 0.019 |  |  |  |  |
| o-H$_2$CS J=6$_{1,5}-$5$_{1,4}$ | 209.200620 | 0.39$\times$0.33, $-$87.9 | 2.0 | 0.18 | 1.7 | 2021.1.00899.S | 48.3 | $-$3.886 | 39 | 0.152 $\pm$ 0.038 |  |  |  |  |
| o-H$_2$C$^{34}$S J=9$_{1,9}$–8$_{1,8}$ | 299.203444 | 0.37$\times$0.25, 69.2 | 0.5 | 1.20 | 0.47 | 2021.1.00535.S | 85.0 | $-$3.402 | 57 | 0.052 $\pm$ 0.014 |  |  |  |  |

: Image Cube and Line Properties

Table notes: The spectroscopic constants for all lines are taken from the CDMS database (cite: Muller01; Muller05; Endres16) with data from (cite: Bogey81; Bogey82; Ahrens99; Kim03; Gottlieb03; Muller19). $^{a}$ Uncertainties are derived via bootstrapping and do not include the systematic calibration flux uncertainty (${\sim}$10%). The image properties and flux for CS J=2–1 are taken from (cite: Oberg21_MAPSI). $^{b}$ Since the CS J=7–6 observations lack short-baseline data, we consider this flux a lower limit.

# The HD 163296 Disk

HD 163296 is a Herbig Ae star (cite: Fairlamb15) with a stellar mass of 2.0 M$_{\odot}$ (cite: Teague21), luminosity of 17 L$_{\odot}$, and age of at least 6 Myr (cite: Fairlamb15; Wichittanakom20) located at a distance of 101 pc (cite: Gaia21). HD 163296 hosts a massive, inclined protoplanetary disk with numerous indications of ongoing planet formation, including multiple dust rings and azimuthal asymmetries (cite: Isella16; Andrews18; Guidi22), kinematic planetary signatures (cite: Teague18_HD163296; Pinte18_HD16; Alarcon22; Calcino22; Izquierdo22), and meridional gas flows (cite: Teague_19Natur).

Due to its relative proximity, large size, highly-structured dust, and bright molecular lines, the HD 163296 disk has been extensively studied (cite: Thi04; Qi11; Fedele12; Rosenfeld13; Flaherty17; Salinas17; Muro_Arena18; Rich20_HST; Doi21; Calahan21; Oberg21_MAPSI; Booth21_MAPS; Hernandez_Vera24) and has emerged as a benchmark system for understanding gas and dust disk structure in detail. In particular, molecular line observations have detected numerous carbon-, nitrogen-, and oxygen-bearing species, which show a complex, multi-ringed spatial distribution (cite: LawMAPSIII). However, few observations have probed the gas-phase sulfur content of this disk (cite: Legal21; Ma24). Given the wealth of existing archival data and its well-constrained physical and chemical structure, the HD 163296 disk presents a unique opportunity to comprehensively characterize the distribution and excitation conditions of several sulfur-bearing species (CS, H$_2$CS) and their isotopologues (C$^{34}$S, H$_2$C$^{34}$S) at high-spatial resolution.

For all subsequent analysis, we adopt the following parameters for the HD 163296 system: PA=133.$^{\circ}$3, incl=46.$^{\circ}$7, v$_{\rm{sys}}$=5.8 km s$^{-1}$, and M$_*$=2.0 M$_{\odot}$ (cite: Oberg21_MAPSI; Teague21).

# Observations

## Archival Data and Observational Details

We compiled both published and archival observations of the HD 163296 disk from ALMA and the Submillimeter Array (SMA)[^1]. The ALMA observations span Band 3 to Band 8, and include multiple transitions of CS and C$^{34}$S and a single transition of H$_2$CS and H$_2$C$^{34}$S. Each archival project was initially calibrated by the ALMA staff using the ALMA calibration pipeline and the required version of CASA (cite: McMullin_etal_2007; CASA22). For all subsequent analysis, we used CASA `v6.3.0`. Calibration of the SMA archival data was done using the MIR software package[^2] and followed standard procedures (see Appendix [7](#sec:appendix:observational details) for additional details). Below, we describe the subsequent data reduction, including self-calibration when performed, along with the typical angular and velocity resolution of each of the lines. For programs whose data have already been published, observational details can be found in the references provided. In the case of new and unpublished archival data, we list the full observational details.

![](Figure1.pdf)

*CS J=2–1*: We obtained publicly-available data products from the Molecules with ALMA at Planet-forming Scales (MAPS) ALMA Large Program (cite: Oberg21_MAPSI; Legal21), which include Band 3 observations of CS J=2–1 at ${\approx}$0.3$''$ with a channel width of 0.5 km s$^{-1}$. Self-calibration and imaging details are available in (cite: Czekala21).

*CS J=3–2*: For the CS J=3–2 line data, we made use of the ALMA program 2017.1.01682.S (PI: G. Guidi), which included both short baseline (SB) and long baseline (LB) data, which covered the CS J=3–2 line in a spectral window with resolution of 35.3 kHz (${\approx}$0.06 km s$^{-1}$) at ${\approx}$0.1$''$. The continuum data were previously published in (cite: Guidi22), who describe the observational details. Following standard self-calibration procedures (cite: Andrews18), we first re-aligned all individual execution blocks (EBs) to a common disk center using the `fixvis` and `fixplanets` tasks and then performed two rounds of phase-only self-calibration (`solint`=‘900s’, ‘360s’) on the SB data. We then concatenated these data with the LB observations before running an additional round of phase-only self-calibration (`solint`=‘inf’). This resulted in an improvement of ${\approx}2\times$ in the peak continuum SNR. We then applied the resulting calibration tables to the aligned line visibilities.

*CS J=4–3, o-H$_2$CS J=6$_{1,5}-$5$_{1,4}$*: We made use of Band 5 observations at ${\approx}$0.3$''$ from the ALMA program 2021.1.00899.S (PI: K. Zhang). The data comprised three EBs observed from 31 July 2022 to 01 August 2022 and used between 41 and 43 antennas for a total on-source integration time of 107 min. Projected baselines ranged from 15.1-1996.7 m and the maximum recoverable scale (MRS) was 3.8$''$ with a typical PWV of 0.6-1.1 mm. One spectral window was centered on the CS J=4–3 line with a resolution of 141.1 kHz (${\approx}$0.2 km s$^{-1}$). Another spectral window, which was centered on HC$_3$N J=23–22, also serendipitously covered the o-H$_2$CS J=6$_{1,5}-$5$_{1,4}$ line at the same velocity resolution. Before performing self-calibration, all EBs were re-aligned to common center with the the `fixvis` and `fixplanets` tasks. Three rounds of phase (`solint`=‘inf’, ‘120s’, ‘60s’) and one round of amplitude (`solint`=‘inf’) self-calibration were performed, which improved the peak continuum SNR by ${\approx}$4$\times$. The solutions were then applied to the line data.

*CS J=5–4*: We made use of observations from the SMA program 2020A-S018 (PI: R. Le Gal), which were conducted on 10 August 2020 in the compact configuration of the SMA using 8 antennas. These data had an angular resolution of ${\approx}$3$^{\prime \prime}$ and were binned from a native velocity resolution of 140 kHz (${\approx}$0.2 km s$^{-1}$) to 1.0 km s$^{-1}$ to improve SNR during subsequent imaging. The SMA data were calibrated with the MIR software package using the bright quasar 3c454.3 as passband calibrator and Uranus as the flux calibrator. Gain calibration was performed with the quasars 1743-038 and nrao530. Once calibrated, the visibilities were then exported to CASA measurement sets for continuum subtraction and imaging.

*CS J=7–6*: We used Band 7 observations from ALMA program 2016.1.01086.S (PI: A. Isella) at ${\lesssim}$0.1$''$. The continuum data associated with this program were originally published in (cite: Guidi22), who describe the observational details. The CS J=7–6 line was covered in a broad spectral window with a resolution of 1,128.9 kHz (${\approx}$0.85 km s$^{-1}$). These observations contain only long-baselines and thus, have a MRS of ${\approx}$0.95$''$. We obtained the image cubes directly from the ALMA archive.

*CS J=8–7*: We used Band 8 observations from ALMA program 2015.1.00847.S (PI: F. Du) at ${\approx}$0.2$''$. These data were previously published in (cite: Bosman21), but only reported the non-detection of H$_2^{18}$O line emission. The CS J=8–7 line was covered in a broad spectral window at a resolution of 1,128.9 kHz (${\approx}$0.75 km s$^{-1}$). We performed two rounds of phase (`solint`=‘900s’, ‘360s’) and one round of amplitude (`solint`=‘inf’) self-calibration after flagged channels containing strong lines, which resulted in an improvement of ${\approx}$600% in the peak continuum SNR. All solutions were then applied to the unflagged line data.

*CS J=10–9*: We used Band 8 observations from ALMA program 2015.1.01137.S (PI: T. Tsukagoshi) at ${\approx}$0.7$''$. The \[C I\] $^3$P$_1$–$^3$P$_0$ line data from this program were previously published in (cite: Alarcon22), who describe the observations in detail. The CS J=10–9 line is covered in a narrow window at 244.1 kHz (${\approx}$0.15 km s$^{-1}$) resolution. We performed one round of phase-only self-calibration (`solint`=‘inf’), leading to a ${\approx}$350% improvement in the peak continuum SNR, and then used these solutions for the full line data.

*C$^{34}$S J=5–4*: We used Band 6 observations from ALMA program 2016.1.00884.S (PI: V. Guzmán) at ${\approx}$0.5$''$. These data were originally published in (cite: Hernandez_Vera24) but only focused on the H$_2$CO lines. The C$^{34}$S J=5–4 line was also covered in a spectral window with a resolution of 282.2 kHz (${\approx}$0.3 km s$^{-1}$). We directly obtained the self-calibration, continuum-subtraction measurement sets described in this work from the authors.

*C$^{34}$S J=6–5, o-H$_2$C$^{34}$S J=9$_{1,9}$–8$_{1,8}$*: We used Band 7 observations from ALMA program 2021.1.00535.S (PI: Y. Yamato) at ${\approx}$0.3$''$. The C$^{34}$S J=6–5 line was covered in a narrow spectral window at a resolution of 141.1 kHz (${\approx}$0.13 km s$^{-1}$) and the o-H$_2$C$^{34}$S J=9$_{1,9}$–8$_{1,8}$ line was serendipitously covered in a broad window at 1,128.9 kHz (${\approx}$1.0 km s$^{-1}$). Observational details, the self-calibration process, and a description of the original line detections are presented in (cite: Yamato25), from which we acquired the self-calibration, continuum-subtraction measurement sets.

## Imaging

For those programs which we obtained directly from the ALMA or SMA archives, we first subtracted the continuum using the `uvcontsub` task in CASA with a first-order polynomial. All lines were then imaged using the `tclean` task with Briggs weighting and Keplerian masks generated with the `keplerian_mask` (cite: rich_teague_2020_4321137) code. The masks were based on the stellar and disk parameters of HD 163296 and have a maximum radius of 4.2$''$, which is matched to that used for the HD 163296 disk in the MAPS Large Program (cite: Czekala21). We manually chose Briggs `robust` parameters to prioritize high SNR line detections. In a few cases, we also binned the image cubes in velocity with channel spacings ultimately ranging from 0.13-1.20 km s$^{-1}$ depending on the line. All images were made using the ‘multi-scale’ deconvolver with pixel scales of \[0,5,15,25\] and were CLEANed down to a 4$\sigma$ level, where $\sigma$ was the RMS noise measured across five line-free channels of the dirty image. During imaging, we applied *uv*-tapers to several lines to increase the SNR of the resulting images. Table [1](#tab:image_info) summarizes all image properties.

![](Figure2.pdf)

![image](Figure3a.pdf) ![image](Figure3b.pdf)

## Moment Maps, Radial Profiles, and Integrated Fluxes

We generated velocity-integrated intensity, or “zeroth moment," maps of line emission from the image cubes using `bettermoments` (cite: Teague18_bettermoments) with no flux threshold for pixel inclusion to ensure accurate flux recovery. All maps were generated using the same Keplerian masks employed during CLEANing. We also produced peak intensity maps using the ‘quadratic’ method of `bettermoments` (see Appendix [8](#sec:appendix_Fnu_maps)). We computed radial line intensity profiles using the `radial_profile` function in the `GoFish` python package (cite: Teague19JOSS) to deproject the zeroth moment maps. All radial profiles assume a flat, i.e., midplane, emitting surface. We computed line fluxes from spectra extracted using `GoFish` and the same Keplerian masks used to generate the zeroth moment maps. We estimated uncertainties via a bootstrapping approach as the standard deviation of the integrated fluxes within 500 randomly-generated Keplerian masks spanning only line-free channels. Table [1](#tab:image_info) lists all integrated fluxes.

# Results

## Spatial Distribution of Emission

Figure [1](#fig:figure1) presents a gallery of zeroth moment maps of all detected lines in the HD 163296 disk and Figure [2](#fig:figure2_radial_profiles) shows the corresponding radial profiles. We characterized line emission substructures using established nomenclature (cite: Huang18_DSHARPII; LawMAPSIII), with local maxima marked with “B” (for “bright”) and local minima indicated with “D” (for “dark”) followed by their radial location rounded to the nearest au. We refer to these features as rings and gaps, respectively.

All lines of CS and H$_2$CS, and their isotopologues, have a ringed structure and central cavity with the exception of CS J=5–4 and CS J=10–9. Given that the radial size of this cavity is 0.4$''$, or ${\approx}$40 au at the distance of HD 163296, the absence of a cavity, and lack of clear rings, in these lines is likely due to their larger beam sizes. In general, CS and C$^{34}$S take the form of two rings at radii of ${\approx}$40-50 au and ${\approx}$110-120 au. The relative contrast of the second ring, i.e., the depth of the gap between the two rings, is a function of the line excitation properties. Lines with low E$_{\rm{u}}$ values only show the inner ring with a broad shoulder (CS J=2–1, C$^{34}$S J=5–4), those with intermediate E$_{\rm{u}}$ values show a plateau-like feature, and those with the highest E$_{\rm{u}}$ values have a well-separated, double-ringed emission morphology (CS J=7–6, J=8–7). This pattern is not an artifact of differing angular resolutions and is clearly seen in the beam-matched profiles (see Section [4.3](#sec:radially_resolved_Ncol)).

H$_2$CS instead shows only a single ring at 56 au, which is similar to that of the inner CS ring, and a prominent emission shoulder extending to larger radii, while H$_2$C$^{34}$S peaks in a narrower ring at a smaller radius of 37 au. There is also a possible secondary ring in the H$_2$C$^{34}$S profile at ${\approx}$100 au. If real, it would approximately correspond to the location of the CS and C$^{34}$S outer rings and fall in-line with the trend of increasing ring contrast with higher E$_{\rm{u}}$. However, due to its low SNR, we consider this ring to be tentative and more sensitive observations are needed to robustly confirm this feature. Overall, CS, C$^{34}$S, and H$_2$CS possess broadly similar spatial distributions, including radial locations and widths of features and cavity sizes, while H$_2$C$^{34}$S appears to originate from a more compact ring.

In addition to the two inner rings, we also detected an additional two outer rings in CS J=3–2 and CS J=4–3. Figure [3](#fig:figure2_external_rings) shows zeroth moment and peak intensity maps, along with the corresponding radial profiles, of both lines, which have been smoothed to boost the SNR of the faint, diffuse outer rings. Two external rings at ${\approx}$240 au and ${\approx}$385 au are seen in CS J=4–3, while only the outermost, broad ring is detected in the less sensitive CS J=3–2 data. The radial location of the outermost CS J=3–2 ring differs by a few 10s of au from that of the same feature in J=4–3, but this shift is likely attributable to the additional spatial smoothing required to detect this ring in the J=3–2 data. This multi-ringed emission structure is consistent with that seen in other molecules in the same disk (cite: LawMAPSIII; Guzman21_MAPS; Bergner21ApJS). We return to the origin of these rings in the Discussion.

## Disk-Integrated Excitation

Next, we aim to determine the disk-averaged column densities and excitation temperatures of CS, C$^{34}$S, H$_2$CS, and H$_2$C$^{34}$S toward the HD 163296 disk. Following (cite: Legal19; Legal21), we used a rotational diagram analysis (cite: Goldsmith99). We assume all lines are in local thermal equilibrium (LTE), as in general, we expect the gas densities in the warm molecular layers of the HD 163296 disk (cite: Qi11; Zhang21) to be well-above the critical densities of the CS and H$_2$CS lines considered here (cite: Shirley15).

For optically-thin lines, the disk-integrated flux density $S_{\nu} \Delta v$, as measured for each transition in Table [1](#tab:image_info), is related to the column density of molecules in their respective upper energy state, N$_{\rm{u}}$ via:

$$\begin{equation}
    N_u = \dfrac{4 \pi S_{\nu} \Delta v}{A_{ul} \Omega hc},
\end{equation}$$

where $\Omega$ is the total solid angle covered by the Keplerian mask from which we measured the flux and A$_{ul}$ is the Einstein coefficient.

The upper state level population N$_u$ is related to the total column density N$_{\rm{T}}$ and rotational temperature T$_{\rm{rot}}$ by the Boltzmann equation:

$$\begin{equation}
    \dfrac{N_u}{g_u} = \dfrac{N_{\rm{T}}}{Q(T_{\rm{rot}})} e^{-E_u / k_{\rm{B}} T_{\rm{rot}}},
\end{equation}$$

where $g_u$ is the upper state degeneracy, $E_{\rm{u}}$ is the upper state energy, and Q is the molecular partition function. For the diatomic molecules CS and C$^{34}$S, we adopt the following partition function:

$$\begin{equation}
Q(T) \approx \dfrac{k_B T_{\rm{rot}}}{h B_0} + \dfrac{1}{3}
\end{equation}$$

with a rotational constant B$_0=$ 24495.56 $\times 10^6$ Hz for CS and B$_0=$ 24103.55 $\times 10^6$ Hz for C$^{34}$S (cite: Muller05). For H$_2$CS and H$_2$C$^{34}$S, we linearly interpolated values of the partition function from the CDMS catalog, from which we also obtained all spectroscopic line data as listed in Table [1](#tab:image_info).

The H$_2$CS molecule (and its isotopologue) has two different nuclear spin configurations, i.e., ortho and para corresponding to odd and even values of quantum number K$_{\rm{a}}$, respectively. The H$_2$CS and H$_2$C$^{34}$S lines presented here are ortho lines, which can be used to derive a column density of o-H$_2$CS and o-H$_2$C$^{34}$S, respectively. Thus, to derive total column densities, we adopt the statistical ortho-to-para ratio of 3, which is approximately consistent with the ratio (2.70$^{+0.20}_{-0.19}$) measured from H$_2$CO in the HD 163296 disk (cite: Hernandez_Vera24).

![](Figure4.pdf)

Following (cite: Loomis18), we also included an optical depth correction factor, C$_{\tau}$ = $\tau / 1 - e^{-\tau}$, for the true level populations for each line. We then constructed a likelihood function $\mathcal{L}$(data, N$_{\rm{T}}$, T$_{\rm{rot}}$) for $\chi^2$ minimization and used the affine-invariant Markov Chain Monte Carlo code `emcee` (cite: Foreman_Mackey13) to generate posterior probability distributions for T$_{\rm{rot}}$ and N$_{\rm{T}}$. For consistency, we adopted the same uniform priors as in (cite: Legal21) of T$_{\rm{rot}} (\rm{K}) = \mathcal{U}(3, 300)$ and N$_{\rm{T}} (\rm{cm}^{-2}) = \mathcal{U}(10^7, 10^{20})$. We used 256 walkers with 2000 burn-in steps and an additional 1000 steps to sample the posterior distribution. We adopt the median as the best-fitting value with uncertainties given by the 16th and 84th percentiles of the posterior distributions, which represent the 1$\sigma$ uncertainties of a Gaussian distribution. We also included a systematic flux calibration uncertainty of 10% added in quadrature to the statistical uncertainty on all measured line fluxes.

![](Figure5.pdf)

Figure [4](#fig:figure2) shows the fitted rotational diagrams for all molecules. Since only one transition is available for both H$_2$CS and H$_2$C$^{34}$S, we instead fixed the rotational temperature to that derived from CS for both species. This is a reasonable assumption based on the previously-derived H$_2$CS T$_{\rm{rot}}$ in the similar MWC 480 disk (cite: Legal21). We also experimented with other T$_{\rm{rot}}$ values (from 15 K to 60 K) and found that the derived N$_{\rm{T}}$ values of H$_2$CS and H$_2$C$^{34}$S varied by no more than 2$\times$ and 10$\times$, respectively (see Appendix [9](#sec:appendix:H2CS_trot)). Values of $\tau$ range from 0.0007 (H$_2$C$^{34}$S) to 0.08 (CS), which indicates optically thin emission for all lines and molecules. All fits used thermal line widths, with FWHMs of ${\approx}$1-2 km s$^{-1}$ measured from spectrally-resolved lines. To provide an upper bound on line optical depths, we adopted the significantly smaller intrinsic line widths of ${\approx}$0.3 km s$^{-1}$ possible in disks (cite: Paneque24). This resulted in line optical depths that were greater by a factor of ${\approx}$2-4, which implies that a few of the CS lines could, at most, have $\tau\approx$0.2-0.3.

We derive the following disk-integrated values:

- T$_{\rm{rot}}$ = 24.4$^{+1.2}_{-1.3}$ K and N$_{\rm{T}}$ = 5.53$^{+0.33}_{-0.33}\times10^{12}$ cm$^{-2}$ for CS

- T$_{\rm{rot}}$ = 12.5$^{+2.8}_{-1.6}$ K and N$_{\rm{T}}$ = 1.19$^{+0.53}_{-0.43}\times10^{12}$ cm$^{-2}$ for C$^{34}$S

- N$_{\rm{T}}$ = 2.97$^{+0.62}_{-0.61}\times10^{12}$ cm$^{-2}$ for H$_2$CS

- N$_{\rm{T}}$ = 1.05$^{+0.29}_{-0.30}\times10^{12}$ cm$^{-2}$ for H$_2$C$^{34}$S

We find disk-integrated ratios of: N(CS)/N(C$^{34}$S) = 4.7$^{+3.1}_{-1.6}$; N(H$_2$CS) / N(H$_2$C$^{34}$S) = 2.8$^{+2.0}_{-1.1}$; and N(H$_2$CS) / N(CS) = 0.54$^{+0.15}_{-0.13}$. The derived H$_2$CS/CS ratio is similar to that of the MWC 480 disk (cite: Legal21), and within a factor of a few of the ratios measured in the HD 100546 (cite: Booth24_HD100546) and HD 169142 (cite: Booth23_HD169142) disks. These high ratios indicate, as previously suggested by (cite: Legal21), that a substantial part of the volatile sulfur reservoir may be in organic form at least in Herbig sources. In particular, high H$_2$CS/CS ratios are in tension with existing chemical models (cite: Legal19), which predict H$_2$CS column densities that are 1–2 orders of magnitude below that of CS. As noted in (cite: Legal21), this underproduction of H$_2$CS is likely due to either missing ice formation pathways or the lack of precise laboratory-measured ice photodissociation rates. Within uncertainties, both CS/C$^{34}$S and H$_2$CS/H$_2$C$^{34}$S ratios indicate a consistent $^{32}$S/$^{34}$S ratio of ${\approx}$2-5, which is at least several times lower than the ISM ratio of ${\approx}$22 (cite: Wilson99). If we instead adopt the warmer excitation temperature of CS to determine the C$^{34}$S column density, the resulting disk-integrated ratio is N(CS)/N(C$^{34}$S) = 10.4$^{+2.0}_{-1.1}$, which is still considerably lower than the ISM value.

## Radially-resolved Analysis

Next, we perform a radially-resolved rotational diagram analysis. First, we selected the subset of lines with sufficiently high angular resolution that resolve one or both inner CS rings, i.e., CS J=2–1, 3–2, 4–3, 8–7, C$^{34}$S J=5–4, 6–5, H$_2$CS J=6–5, and H$_2$C$^{34}$S J=9–8. We excluded the CS J=7–6 line due to its small MRS (see Section [3.1](#sec:archival_data)), and thus likely missing flux. We re-imaged all CS and H$_2$CS lines with a carefully selected set of *uv*-tapers and `robust` values to ensure a 0.35$''$ circularized beam, following the approach outlined in (cite: Czekala21). Due to the larger beam size of the C$^{34}$S J=5–4 observation, we instead tapered both C$^{34}$S lines to a 0.5$''$ beam size. We then used these beam-matched images for the radially-resolved analysis as in the previous Section.

When fitting the C$^{34}$S profiles, we restricted our priors based on the disk-averaged fit and radially-resolved CS values (T$_{\rm{rot}} (\rm{K}) = \mathcal{U}(10, 35)$ and N$_{\rm{T}} (\rm{cm}^{-2}) = \mathcal{U}(10^9, 10^{17})$). To compute the column density profiles of H$_2$CS and H$_2$C$^{34}$S, we adopted the CS T$_{\rm{rot}}$ profile for both species (see Appendix [9](#sec:appendix:H2CS_trot) for more details). As in the disk-averaged analysis, all lines remain optically-thin in the spatially-resolved analysis.

Figure [5](#fig:figure_radially_prof_Ncol) shows the radially-resolved T$_{\rm{rot}}$ and N$_{\rm{T}}$ profiles, along with the beam-matched, azimuthally-averaged radial profiles used to construct them. The T$_{\rm{rot}}$ profile for CS smoothly decreases out to a radius of ${\approx}$250 au, with the exception of a dip (${\approx}$5 K) at ${\approx}$90 au, which is near the location of the D85 dust gap. The C$^{34}$S T$_{\rm{rot}}$ profile is consistent with a constant T$_{\rm{rot}}\approx15$ K out to a radius of 200 au but shows higher uncertainties, which reflect the smaller dynamic range in upper energy of the two lines used in the fitting.

In terms of N$_{\rm{T}}$, both CS and C$^{34}$S show smoothly declining profiles where N(CS) $>$ N(C$^{34}$S) at all radii. We note a small enhancement in the CS N$_{\rm{T}}$ profile at the location of the second CS ring (${\approx}$120 au). H$_2$CS and H$_2$C$^{34}$S also show generally smoothly declining profiles with the exception of a notable offset in their N$_{\rm{T}}$ profiles, with H$_2$C$^{34}$S peaking ${\approx}$20 au interior to H$_2$CS. This shift reflects the more compact H$_2$C$^{34}$S ring relative to H$_2$CS and results in an overlap region where the column density ratio is on the order of unity. We also observe a flattening of the H$_2$C$^{34}$S profile from ${\approx}$80-120 au, which corresponds to the tentative H$_2$C$^{34}$S secondary ring seen in the intensity profiles (Figure [2](#fig:figure2_radial_profiles)).

Figure [6](#fig:figure_radial_ratios) shows the spatially-resolved N$_{\rm{T}}$ ratios for both isotopologue pairs of CS/C$^{34}$S and H$_2$CS/H$_2$C$^{34}$S. The spatially-resolved ratios are approximately constant with radius and are broadly consistent with the disk-averaged values. At nearly all radii, the $^{32}$S/$^{34}$S ratios are inconsistent with the ISM value and could be enhanced in $^{34}$S by up to an order of magnitude.

![](Figure6.pdf)

![](Figure7.pdf)

## Emitting Regions of CS and C$^{34}$S

### Inferred From Channel Maps

For molecular line emission that arises above the midplane in the warm molecular layer, as is expected for CS and H$_2$CS (cite: Legal19), there is a spatial separation between the front and back disk surfaces (cite: Rosenfeld13; pinte18). In inclined and vertically-flared disks, such as HD 163296 (cite: Teague19Natur; Law21_MAPSIV; Paneque_MAPS), it is possible to directly resolve this vertical structure at high angular resolution. We searched through the channel maps of all available lines and found that this was possible for CS J=4–3.

We attempted to fit the emitting heights using the channel maps via standard techniques (cite: disksurf_Teague; Paneque_MAPS), but the data were of insufficient SNR to enable direct extraction of line emitting heights. However, we can still provide an approximate constraint on the CS emitting surface by overlaying a set of isovelocity contours at different heights and visually inspecting how well they match the observed emission.

In Figure [7](#fig:figure_emitting_heights_CS_43), we chose a set of representative channels where the separation of disk surfaces is expected to be greatest and labeled emission surfaces from the midplane ($z/r=0$) to a height of $z/r=0.2$ in increments of 0.05. Visually, we can rule out CS originating from altitudes of $z/r \geq 0.2$, which are too elevated relative to the observed emission. While, by-eye, isovelocity contours with heights from $z/r=0.1$ to 0.15 appear to best match the data, we are unable to robustly exclude a midplane or near-midplane origin of CS with the available angular resolution and SNR.

### Inferred from 2D Gas Structure

In addition to directly resolving the vertical line emission structure, we instead used our radially-resolved T$_{\rm{rot}}$ profile (Figure [5](#fig:figure_radially_prof_Ncol)) to infer the emitting regions of CS and C$^{34}$S based on the known 2D $T(r, z)$ gas temperatures of the HD 163296 disk. To do so, we followed the approach of (cite: Ilee21). Briefly, we first renormalized the 2D temperature profile of (cite: Law21_MAPSIV), which was derived from optically-thick CO isotopologues at intermediate-to-high disk altitudes and excluded temperatures below 20 K. This is done to ensure that the CO snowline matches the midplane radius derived in the thermochemical models of (cite: Zhang21). Then, by assuming that T$_{\rm{rot}}$ is equal to the gas temperature for each molecule, we can determine the emitting region in $(r,z)$-space.

![](Figure8.pdf)

Figure [8](#fig:figure_zr_heights) shows the inferred emission regions for CS and C$^{34}$S. CS is relatively well-constrained to a height of $z/r\lesssim0.1$, which is consistent with the visual height determination from the CS J=4–3 channel maps in the previous subsection. The apparent decrease in CS emitting heights at a radius of ${\approx}$80-100 au is due to the corresponding dip in the T$_{\rm{rot}}$ profile, which is likely a line excitation effect (see Section [5.2](#sec:CS_v_continuum)), rather than a true deviation in the emitting heights. The C$^{34}$S emitting region is considerably more uncertain due to the large uncertainties in T$_{\rm{rot}}$.

# Discussion

## Dust and Molecular Gas Structure

Figure [9](#fig:figure_rings_pos) shows the radial locations of all line emission features versus the known annular continuum substructures in the HD 163296 disk (cite: Huang18_DSHARPII; Sierra21_MAPS). The radial locations of rings and gaps are consistent across different lines. The inner CS and H$_2$CS rings are co-located with the D49 dust gap, while the outer ring is located beyond the dust ring at B101. The gap between these rings is located near the narrow D85 dust gap. One of the outer rings in CS J=4–3 is coincident with the edge of the mm dust. We do not observed any general trends in ring or gap radial locations versus the E$_{\rm{u}}$ of the lines, despite the resolved CS lines spanning nearly 100 K in E$_{\rm{u}}$.

The CS emission morphology also largely follows the known gas structure of the HD 163296 disk. As shown in Figure [10](#fig:figure_CS_MAPS), the radial locations of the four rings seen in the CS J=4–3 line approximately match those of other molecules, such as C$_2$H 3–2 and HCN 3–2 (cite: Guzman21_MAPS; Bergner21ApJS). All of these lines have comparable excitation properties, e.g., E$_{\rm{u}}$, n$_{\rm{crit}}$, and are expected to originate from similar disk heights of $z/r=0.1$-0.15 (cite: Law21_MAPSIV). Given that each of these molecules have different formation pathways, this indicates that the emission rings are likely tracing the underlying gas density structure in the HD 163296 disk.

![](Figure9.pdf)

In addition to the radial morphology, the tight constraints on the vertical emission structure of CS in HD 163296 provide valuable information on possible formation mechanisms. Although not directly measured, chemical models of the similar disk around the Herbig star MWC 480 from (cite: Legal21) suggest a CS reservoir at altitudes of $z/r\sim0.3$, while models of a generic disk around a Herbig star predict $z/r\gtrsim0.2$ at typical outer disk radii of ${\approx}$100 au (cite: Agundez18). The relatively lower CS heights in HD 163296 may point to efficient destruction in the disk upper layers, or suggest that significant CS formation is occurring via slower, neutral-neutral reactions rather than the more rapid ion-neutral pathways driven by S$^+$ as predicted by chemical models (cite: Semenov18; Legal19).

In fact, the CS emitting heights derived here are instead similar to those ($z/r\lesssim0.1$) inferred from high-angular resolution observations of the disk around the T Tauri star CI Tau (cite: Rosotti21) and toward the relatively flat disk around the Herbig star HD 100546 (cite: Booth24_HD100546). However, for both of these sources, the outer disks have evidence for being partially shadowed (cite: Rosotti21; Gravity_CITau; Keyte23), which would result in cooler temperatures and may inhibit CS formation via photoionization-driven pathways in the upper disk layers. Thus, more general conclusions about CS disk chemistry are limited by the small number of sources with directly mapped CS emission surfaces. High-angular resolution observations toward additional disks, such as those from the ongoing exoALMA Large Program, are vital to determine the typical location of the gas-phase CS reservoirs, and thus, constrain the nature of CS chemistry active in different types of disks.

(cite: Legal21) previously noted the potential presence of azimuthal asymmetries in CS J=2–1 in the HD 163296 disk. Such asymmetries in line emission are relatively rare in disks and are of considerable interest as they often point to dynamical interactions or underlying variations in disk structure (cite: vanderMarel13; Temmink23). Based on the system geometry, we view the disk far side through a known wind (cite: Klaassen13; Booth21_MAPS) and jet (cite: Grady00; Xie21), which led (cite: Legal21) to speculate about potential local alterations in the CS content due to, e.g., changing C/O ratios or entrained dust reducing line opacity. However, we do not observe any significant asymmetries (Figure [1](#fig:figure1)), and those lines with the highest SNR (i.e., CS J=4–3) appear the most azimuthally uniform. Thus, our multi-line analysis allows us to rule out the presence of any large-scale CS asymmetries in this disk.

![](Figure10.pdf)

## Local Sub-thermal CS Line Excitation in a Planet-Carved Gap

One of the most salient morphological features revealed by our multi-line CS observations is the increasing contrast of the inner two inner rings with consecutive J lines. As illustrated in Figure [2](#fig:figure2_radial_profiles), only a single, wide ring is seen in CS J=2–1, followed by a plateau-like feature in J=3–2 and J=4–3, and ultimately two distinct rings in J=7–6 and J=8–7. The radial location of the gap between these two rings is co-located with the D85 dust gap (Figure [9](#fig:figure_rings_pos)), which was likely carved by an embedded planet (cite: Teague18_HD163296; Zhang18). This gap has been estimated to have a significant local decrease in n$_{\rm{H}}$ (cite: Rab20; Zhang21) and thus, we need to revisit our assumption of LTE and thermalized lines locally at the gap position.

We find that the increasing contrast of the CS rings can be explained by sub-thermal line excitation in the higher J lines. The critical densities range from $n_{\rm{crit}}{\approx}$10$^{4}$ cm$^{-3}$ (J=2–1) to 5$\times10^6$ cm$^{-3}$ (J=8–7) at gas temperatures of ${\approx}$20-30 K (cite: Shirley15). While there is still sufficient gas density in the gap to thermalize the lower J transitions, this is no longer true for the higher J lines. As the n$_{\rm{crit}}$ of the lines increase, it approaches the actual gas density and each subsequent J line is progressively less thermalized than the next. By the time we reach CS J=8–7, which has the highest n$_{\rm{crit}}$ of the resolved lines in our sample, this line is significantly sub-thermally excited. Such a scenario not only naturally explains the apparent gap in the radial intensity profiles (Figure [2](#fig:figure2_radial_profiles)), but also predicts a lower CS rotational temperature at the gap location, as seen in Figure [5](#fig:figure_radially_prof_Ncol). We confirmed this interpretation via RADEX (cite: vanderTak07) calculations, which show that at the typical CS gas conditions in the gap, T$_{\rm{ex}}$ $\approx$ T$_{\rm{kin}}$ for J=2–1 and J=3–2, while the two differ by more than 20% in the CS J=7–6 and J=8–7 lines. Thus, at the gap location, by using the sub-thermal CS J=8–7 line fluxes in our excitation analysis, we should expect a ${\approx}$5-6 K underestimate of the kinetic temperature, which is exactly what we observe in the T$_{\rm{rot}}$ profile in Figure [5](#fig:figure_radially_prof_Ncol).

Given that we have a constraint on what density the CS lines become sub-thermally excited, we can use this to independently estimate the approximate gas density of a planet-carved gap in the HD 163296 disk. This is of particular interest given the wide, nearly two order-of-magnitude range in existing planet mass estimates of 0.07-3 M$_{\rm{Jup}}$ derived in the literature so far (cite: Isella16; Zhang18; Teague18_HD163296; Pinte20). If we assume that sub-thermal excitation becomes significant when n$_{\rm{H}}$ is within a factor of 10 from the critical density of the CS J=8–7 line, we can then estimate the corresponding gas surface density at this location. We find $\Sigma_{\rm{g}} \sim$ 1 g cm$^{-2}$, which is consistent with inferences based on gas pressure deviations due to a Jupiter-mass planet (cite: Teague18_HD163296). Our estimate, while quite uncertain, demonstrates the utility of line excitation as a way to independently measure planet masses. Additional high angular and spectral resolution observations of CS J=8–7 — and the higher n$_{\rm{crit}}$ line of CS J=10–9, which is mostly unresolved in our data — would allow for detailed non-LTE modeling and enable significantly improved measurements of the gap gas density, and thus, planet mass.

## Sulfur Isotopic Ratios

### Evidence of Sulfur Fractionation in the HD 163296 Disk

Measurements of isotopic ratios provide valuable constraints on the underlying gas reservoir available to forming planets and serve as diagnostics of disk physical conditions and chemical histories (cite: Favre15; Visser18; Cataldi21; Furuya22; Bergin24). However, sulfur fractionation remains little explored in protoplanetary disks, due in part to the relative scarcity of detections of S-bearing molecules and their isotopologues. It is thus unknown to what degree sulfur fractionation is active in disks, or what fractionation processes may be most important in disk environments. Here, we have measured both a disk-averaged and spatially-resolved $^{32}$S/$^{34}$S ratio from two independent optically-thin isotopologue pairs in the HD 163296 disk. In both cases, we find a consistent $^{32}$S/$^{34}$S ratio of ${\approx}$2-5, which indicates a significant enhancement in $^{34}$S from the expected ISM ratio of ${\approx}$22 (cite: Wilson99).

In disk models, CS efficiently forms in warm disk layers driven by rapid ion–neutral reactions between S$^+$ and small hydrocarbons, while H$_2$CS forms via a gas-phase neutral–neutral reaction of atomic S and CH$_3$ (cite: Legal19). Because of these differing formation routes, H$_2$CS is expected to lie deeper in the disk than CS due to the expected vertical distribution of atomic S versus S$^+$. The fact that both molecules show comparable $^{32}$S/$^{34}$S ratios, indicates a wide-spread $^{34}$S enhancement across the disk as both the ionized and atomic sulfur volatile reservoirs must share this enhancement. Moreover, a disk-wide $^{34}$S enhancement is also consistent with the nearly constant $^{32}$S/$^{34}$S ratios out to a radius of 200 au, as seen in Figure [6](#fig:figure_radial_ratios).

### Comparison to Class II Disks, Comets, and Pre-stellar Cores

We next aim to compare how the $^{32}$S/$^{34}$S ratio measured in the HD 163296 disk compares to those inferred in other disks, comets, and other ISM settings to shed light on possible fractionation mechanisms. Only a handful of Class II disks have existing measurements of $^{32}$S/$^{34}$S (cite: Legal21; Phuong21; Booth24_HD100546), which are shown in Figure [11](#fig:figure_ratios_vs_disks). The measurements for the MWC 480 and GG Tau disks represents disk-averaged values, while the ratios in the HD 100546 disk are measured at both the inner (${\approx}$50 au) and outer (${\approx}$200 au) rings. GG Tau and the outer ring of HD 100546 are consistent with the ISM ratio and show no evidence of enhanced $^{34}$S. However, the inner ring of HD 100546 and MWC 480 appear similar to that of HD 163296, but both of these measurements have associated caveats. As (cite: Booth24_HD100546) note, the measured N(CS)/N(C$^{34}$S) ratio in the inner HD 100546 ring may indicate optically-thick CS rather than an anomalous $^{32}$S/$^{34}$S ratio. On the other hand, while CS in the MWC 480 disk is optically-thin (cite: Legal21), the large upper range in uncertainty means that we cannot rule out an ISM-like $^{32}$S/$^{34}$S ratio.

![](Figure11.pdf)

We emphasize that only HD 163296 and MWC 480 have isotopic measurements derived from multi-line analysis in both CS and C$^{34}$S, where it was possible to confirm that both tracers are optically thin, while the ratios in GG Tau and HD 100546 are based on a single line of CS and C$^{34}$S each. If CS is indeed optically-thin in the inner ring of HD 100546, this then suggests that each of the Herbig sources observed so far have an enhanced $^{34}$S ratio. Unlike the HD 163296 disk, which shows a radially-constant $^{34}$S enhancement, this would imply a radial gradient in the $^{32}$S/$^{34}$S ratio in the HD 100546 disk. Taken together, this may point to fractionation pathways that depend on disk properties, e.g., gas temperatures, radiation field, which vary across Herbig versus T Tauri sources. We also note that, recently, (cite: Booth24) found that both $^{33}$S and $^{34}$S were depleted in the disk around Herbig star IRS 48 as measured via SO isotopologues, while $^{34}$SO$_2$ showed a potential enhancement. However, direct comparisons with our findings are challenging as these inferences of non-ISM-like isotopic ratios were highly dependent on the assumed excitation temperatures. Moreover, the observed volatile sulfur reservoir in IRS 48, unlike most Class II disks, is primarily in the form of SO with only a negligible contribution from CS to the total sulfur abundance (cite: Booth24_IRS48). Nonetheless, these results demonstrate that not all disks show ISM-like sulfur isotopic ratios and illustrate the urgent need for additional multi-line observations of sulfur-bearing isotopologues to assess how common fractionation is in disk settings.

We can also compare the measured $^{32}$S/$^{34}$S ratio in the HD 163296 disk to those derived in comets and earlier ISM phases, to assess if inheritance or *in situ* processes set this ratio in disks. Isotopic ratios have been thoroughly characterized in comets and no similar $^{34}$S enhancement is found in cometary material measured in a variety of sulfur tracers, including gas-phase molecules and refactory dust (cite: Heck12; Biver16; Calmonte17; Paquette17), which are instead consistent with the local ISM ratio. In contrast, few sulfur isotopic ratios have been robustly measured in earlier ISM phases. Such measurements are particularly difficult in the protostellar phase, since sulfur-bearing molecules often trace outflows and/or the surrounding envelopes, rather the disks themselves (cite: Villarmois23). However, the pre-stellar core L1544 has had its sulfur inventory categorized in detail by (cite: Vastel18). While CS emission is optically thick in L1544, (cite: Vastel18) report an ISM-like $^{32}$S/$^{34}$S ratio measured from the optically thin H$_2$CS/H$_2$C$^{34}$S column density ratio. Thus, the fractionation taking place in the HD 163296 disk appears distinct both from cometary values and those in low-mass pre-stellar cores, which again points to a potential origin in the differing gas environment present around a higher-mass star.

### Spatial Offset of H$_2$C$^{34}$S Ring

In Section [4.1](#sec:line_emission), we found that the H$_2$C$^{34}$S ring at 37 au appears spatially offset from that of H$_2$CS at 56 au, which corresponds to an offset of approximately half of the synthesized beam size. Similar offsets have been observed in the DCN, HC$^{15}$N, and H$^{13}$CN isotopologues in the PDS 70 disk, which were attributed to active *in-situ* fractionation pathways occurring at the inner cavity wall (cite: Rampinelli24). If so, we may be seeing a similar effect in the HD 163296 disk in sulfur isotopologues.

Alternatively, given the large difference in E$_{\rm{u}}$ between the H$_2$CS J=6–5 (E$_{\rm{u}}$=48.3 K) and H$_2$C$^{34}$S J=9–8 (E$_{\rm{u}}$=85.0 K) lines, this could instead be an excitation effect. However, we do not see any shifts in the CS or C$^{34}$S inner ring positions (Figure [9](#fig:figure_rings_pos)) as a function of E$_{\rm{u}}$, despite highly-resolved observations spanning a wider range in E$_{\rm{u}}$ from 7.1 K to 84.6 K. The origin and robustness of this shift in H$_2$C$^{34}$S, while intriguing, cannot be definitely confirmed without comparable observations of the same line in both H$_2$CS and H$_2$C$^{34}$S. Such observations will also allow us to robustly determine if this offset is an excitation effect or if it indicates that a different fractionation process is happening in H$_2$C$^{34}$S.

# Conclusions

We presented new and archival ALMA and SMA observations of CS and H$_2$CS, and their C$^{34}$S and H$_2$C$^{34}$S isotopologues, at high-angular resolution (${\approx}$0.2$''$-$''$0.4; 20-40 au) in the HD 163296 disk. These observations comprise the most comprehensive, multi-line CS data in a planet-forming disk to date, spanning a wide range of excitation conditions from E$_{\rm{u}}$=7.1 K to 129.3 K, and include new detections of C$^{34}$S, H$_2$CS, and H$_2$C$^{34}$S in this system. We conclude the following:

1.  Both CS and H$_2$CS, and their isotopologues, show a multi-ringed structure and central cavity. The radial location of the line emission rings and gaps do not show a consistent trend with the mm dust continuum. We also report the discovery of two outer (${>}$200 au) rings in CS J=3–2 and J=4–3. Overall, the sulfur chemistry appears to broadly follow the known molecular gas distribution in the HD 163296 disk.

2.  We derived both disk-averaged and radially-resolved rotational temperature and column density profiles for CS, C$^{34}$S, H$_2$CS, and H$_2$C$^{34}$S. We find that all molecules are optically thin.

3.  We report a N(H$_2$CS)/N(CS) ratio of $\approx$0.5, which is similar to that seen in the Herbig disk MWC 480 and suggests that organic sulfur compounds may constitute a large fraction of the total sulfur reservoir in disks around Herbig stars generally.

4.  The higher contrast of the two inner CS rings in subsequent J lines can be explained by sub-thermal line excitation of the higher J lines. Thus, we provide an independent estimate on the approximate gas density of the planet-carved gap at 85 au in the HD 163296 disk. We find $\Sigma_{\rm{g}} \sim 1$ g cm$^{-2}$, which is consistent with previous estimates indicating the presence of a Jupiter-mass planet.

5.  We derive robust $^{32}$S/$^{34}$S ratios of ${\approx}$5 (CS/C$^{34}$S) and ${\approx}$2 (H$_2$CS/H$_2$C$^{34}$S) based on both disk-averaged and spatially-resolved analyses. Both values are consistent across two independent pairs of optically-thin molecular traces. This ratio is well-below the expected ISM ratio, which suggests the presence of significant sulfur fractionation in the HD 163296 disk.

6.  We constrain the CS emitting height to be $z/r<0.2$ based on vertical separations of the disk surfaces in the CS J=4–3 channel maps. This is consistent with an independent inference of the CS emitting region indicating $z/r \lesssim 0.1$ using spatially-resolved T$_{\rm{rot}}$ profiles and the known 2D gas structure of the HD 163296 disk.

The authors thank the anonymous referee for valuable comments that improved both the content and presentation of this work. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00847.S, 2015.1.01137.S, 2016.1.00884.S, 2016.1.01086.S, 2017.1.01682.S, 2018.1.01055.L, 2021.1.00535.S, and 2021.1.00899.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. Support for C.J.L. was provided by NASA through the NASA Hubble Fellowship grant No. HST-HF2-51535.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555. C.H.-V. acknowledges support from the National Agency for Research and Development (ANID) – Scholarship Program through the Doctorado Nacional grant No. 2021-21212409. Y.Y. acknowledges support by Grant-in-Aid for the Japan Society for the Promotion of Science (JSPS) Fellows (KAKENHI Grant Number JP23KJ0636).

This paper also makes use of data obtained with the SMA. The Submillimeter Array is a joint project between the Smithsonian Astrophysical Observatory and the Academia Sinica Institute of Astronomy and Astrophysics and is funded by the Smithsonian Institution and the Academia Sinica. The authors wish to recognize and acknowledge the very significant cultural role and reverence that the summit of Maunakea has always had within the indigenous Hawaiian community. We are most fortunate to have had the opportunity to conduct observation from this mountain.

# Facilities

ALMA, SMA

# Software

Astropy (cite: astropy_2013; astropy_2018), `bettermoments` (cite: Teague18_bettermoments), CASA (cite: McMullin_etal_2007; CASA22), `cmasher` (cite: vanderVelden20), `GoFish` (cite: Teague19JOSS), `keplerian_mask` (cite: rich_teague_2020_4321137), Matplotlib (cite: Hunter07), MIR (<https://lweb.cfa.harvard.edu/~cqi/mircook.html>), NumPy (cite: vanderWalt_etal_2011), RADEX (cite: vanderTak07)

# SMA Data Calibration

The HD 163296 disk was observed in the compact configuration of the SMA on 2020 Aug 10 as part of project 2020A-S018 (PI: R. Le Gal). The observations consisted of 8 antennas with a typical 225 GHz opacity of 0.16 mm and used both the 230 GHz and 240 GHz receivers of the SWARM correlator, which at the time, provided 32 GHz of bandwidth. The tuning was set to cover the CS J=4–3 (195.95421 GHz) and CS J=5–4 (244.93564 GHz) lines.

The SMA data were calibrated using the MIR software package. During calibration, all data from Antenna 8 in the 240 GHz receiver, which covered the CS J=5–4 line, was flagged due to unstable phases. The bright quasar 3c454.3 was used as the passband calibrator, and Uranus was used as the flux calibrator. Gain calibration was performed using the quasars 1743-038 and nrao530. The calibrated visibilities were then exported into CASA `v6.3` (cite: McMullin_etal_2007; CASA22) for subsequent continuum subtraction and imaging.

# Peak Intensity Maps

Figure [12](#fig:figure_appendix_peak_intensities) shows peak intensity maps of all lines. In a few cases, the peak intensities more clearly show the emission morphology, which is not apparent in the zeroth moment maps (Figure [1](#fig:figure1)).

![](Figure12.pdf)

# The Impact of Rotational Temperature on the N(H$_2$CS) / N(H$_2$C$^{34}$S) Ratio

Since we only have one transition of both H$_2$CS and H$_2$C$^{34}$S, we must adopt a rotational temperature to derive column densities. In the main text, we chose to use the CS-derived T$_{\rm{rot}}$ values. Here, we explore the impact and uncertainties of this decision.

Figure [13](#fig:figure_appendix_H2CS_Trot) shows the column density profiles of H$_2$CS and H$_2$C$^{34}$S, and the correspondingly $^{32}$S/$^{34}$S ratio computed with a range of T$_{\rm{rot}}$ values. We tested a set of constant temperatures from 15 K, 30 K, 45 K, and 60 K, in addition to the CS-assumed T$_{\rm{rot}}$, which all result in a non-ISM like $^{32}$S/$^{34}$S ratio. Thus, our conclusion of significant sulfur fractionation in the H$_2$CS molecule does not depend sensitively on the assumed rotational temperature.

![](Figure13.pdf)

natexlab

(ref: Agundez18) Agúndez, M., Roueff, E., Le Petit, F., & Le Bourlot, J. 2018, A&A, 616, A19, doi: [`10.1051/0004-6361/201732518`](http://doi.org/10.1051/0004-6361/201732518)

(ref: Ahrens99) Ahrens, V., & Winnewisser, G. 1999, Zeitschrift Naturforschung Teil A, 54, 131, doi: [`10.1515/zna-1999-0207`](http://doi.org/10.1515/zna-1999-0207)

(ref: Alarcon22) Alarcón, F., Bergin, E. A., & Teague, R. 2022, ApJL, 941, L24, doi: [`10.3847/2041-8213/aca6e6`](http://doi.org/10.3847/2041-8213/aca6e6)

(ref: Altwegg22) Altwegg, K., Combi, M., Fuselier, S. A., et al. 2022, MNRAS, 516, 3900, doi: [`10.1093/mnras/stac2440`](http://doi.org/10.1093/mnras/stac2440)

(ref: Andrews18) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: Villarmois23) Artur de la Villarmois, E., Guzmán, V. V., Yang, Y. L., Zhang, Y., & Sakai, N. 2023, A&A, 678, A124, doi: [`10.1051/0004-6361/202346728`](http://doi.org/10.1051/0004-6361/202346728)

(ref: astropy_2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Bergin24) Bergin, E. A., Bosman, A., Teague, R., et al. 2024, ApJ, 965, 147, doi: [`10.3847/1538-4357/ad3443`](http://doi.org/10.3847/1538-4357/ad3443)

(ref: Bergner19) Bergner, J. B., Öberg, K. I., Bergin, E. A., et al. 2019, ApJ, 876, 25, doi: [`10.3847/1538-4357/ab141e`](http://doi.org/10.3847/1538-4357/ab141e)

(ref: Bergner21ApJS) Bergner, J. B., Öberg, K. I., Guzmán, V. V., et al. 2021, ApJS, 257, 11, doi: [`10.3847/1538-4365/ac143a`](http://doi.org/10.3847/1538-4365/ac143a)

(ref: Biver16) Biver, N., Moreno, R., Bockelée-Morvan, D., et al. 2016, A&A, 589, A78, doi: [`10.1051/0004-6361/201528041`](http://doi.org/10.1051/0004-6361/201528041)

(ref: BM04) Bockelée-Morvan, D., Crovisier, J., Mumma, M. J., & Weaver, H. A. 2004, in Comets II, ed. M. C. Festou, H. U. Keller, & H. A. Weaver, 391

(ref: Bogey81) Bogey, M., Demuynck, C., & Destombes, J. L. 1981, Chemical Physics Letters, 81, 256, doi: [`10.1016/0009-2614(81)80247-3`](http://doi.org/10.1016/0009-2614(81)80247-3)

(ref: Bogey82) —. 1982, Journal of Molecular Spectroscopy, 95, 35, doi: [`10.1016/0022-2852(82)90234-X`](http://doi.org/10.1016/0022-2852(82)90234-X)

(ref: Boogert15) Boogert, A. C. A., Gerakines, P. A., & Whittet, D. C. B. 2015, ARA&A, 53, 541, doi: [`10.1146/annurev-astro-082214-122348`](http://doi.org/10.1146/annurev-astro-082214-122348)

(ref: Booth23) Booth, A. S., Ilee, J. D., Walsh, C., et al. 2023a, A&A, 669, A53, doi: [`10.1051/0004-6361/202244472`](http://doi.org/10.1051/0004-6361/202244472)

(ref: Booth23_HD169142) Booth, A. S., Law, C. J., Temmink, M., Leemker, M., & Macı́as, E. 2023b, A&A, 678, A146, doi: [`10.1051/0004-6361/202346974`](http://doi.org/10.1051/0004-6361/202346974)

(ref: Booth21_MAPS) Booth, A. S., Tabone, B., Ilee, J. D., et al. 2021, ApJS, 257, 16, doi: [`10.3847/1538-4365/ac1ad4`](http://doi.org/10.3847/1538-4365/ac1ad4)

(ref: Booth24_HD100546) Booth, A. S., Leemker, M., van Dishoeck, E. F., et al. 2024a, AJ, 167, 164, doi: [`10.3847/1538-3881/ad2700`](http://doi.org/10.3847/1538-3881/ad2700)

(ref: Booth24_IRS48) Booth, A. S., Temmink, M., van Dishoeck, E. F., et al. 2024b, AJ, 167, 165, doi: [`10.3847/1538-3881/ad26ff`](http://doi.org/10.3847/1538-3881/ad26ff)

(ref: Booth24) Booth, A. S., Drozdovskaya, M. N., Temmink, M., et al. 2024c, ApJ, 975, 72, doi: [`10.3847/1538-4357/ad7817`](http://doi.org/10.3847/1538-4357/ad7817)

(ref: Bosman21) Bosman, A. D., & Bergin, E. A. 2021, ApJL, 918, L10, doi: [`10.3847/2041-8213/ac1db1`](http://doi.org/10.3847/2041-8213/ac1db1)

(ref: Calahan21) Calahan, J. K., Bergin, E. A., Zhang, K., et al. 2021, ApJS, 257, 17, doi: [`10.3847/1538-4365/ac143f`](http://doi.org/10.3847/1538-4365/ac143f)

(ref: Calcino22) Calcino, J., Hilder, T., Price, D. J., et al. 2022, ApJL, 929, L25, doi: [`10.3847/2041-8213/ac64a7`](http://doi.org/10.3847/2041-8213/ac64a7)

(ref: Calmonte16) Calmonte, U., Altwegg, K., Balsiger, H., et al. 2016, MNRAS, 462, S253, doi: [`10.1093/mnras/stw2601`](http://doi.org/10.1093/mnras/stw2601)

(ref: Calmonte17) —. 2017, MNRAS, 469, S787, doi: [`10.1093/mnras/stx2534`](http://doi.org/10.1093/mnras/stx2534)

(ref: CASA22) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Cataldi21) Cataldi, G., Yamato, Y., Aikawa, Y., et al. 2021, ApJS, 257, 10, doi: [`10.3847/1538-4365/ac143d`](http://doi.org/10.3847/1538-4365/ac143d)

(ref: Chen15) Chen, Y. J., Juang, K. J., Nuevo, M., et al. 2015, ApJ, 798, 80, doi: [`10.1088/0004-637X/798/2/80`](http://doi.org/10.1088/0004-637X/798/2/80)

(ref: Czekala21) Czekala, I., Loomis, R. A., Teague, R., et al. 2021, ApJS, 257, 2, doi: [`10.3847/1538-4365/ac1430`](http://doi.org/10.3847/1538-4365/ac1430)

(ref: Doi21) Doi, K., & Kataoka, A. 2021, ApJ, 912, 164, doi: [`10.3847/1538-4357/abe5a6`](http://doi.org/10.3847/1538-4357/abe5a6)

(ref: Dutrey97) Dutrey, A., Guilloteau, S., & Guelin, M. 1997, A&A, 317, L55

(ref: Dutrey11) Dutrey, A., Wakelam, V., Boehler, Y., et al. 2011, A&A, 535, A104, doi: [`10.1051/0004-6361/201116931`](http://doi.org/10.1051/0004-6361/201116931)

(ref: Dutrey24) Dutrey, A., Chapillon, E., Guilloteau, S., et al. 2024, A&A, 689, L7, doi: [`10.1051/0004-6361/202451299`](http://doi.org/10.1051/0004-6361/202451299)

(ref: Endres16) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95, doi: [`10.1016/j.jms.2016.03.005`](http://doi.org/10.1016/j.jms.2016.03.005)

(ref: Fairlamb15) Fairlamb, J. R., Oudmaijer, R. D., Mendigutı́a, I., Ilee, J. D., & van den Ancker, M. E. 2015, MNRAS, 453, 976, doi: [`10.1093/mnras/stv1576`](http://doi.org/10.1093/mnras/stv1576)

(ref: Favre15) Favre, C., Bergin, E. A., Cleeves, L. I., et al. 2015, ApJL, 802, L23, doi: [`10.1088/2041-8205/802/2/L23`](http://doi.org/10.1088/2041-8205/802/2/L23)

(ref: Fedele12) Fedele, D., Bruderer, S., van Dishoeck, E. F., et al. 2012, A&A, 544, L9, doi: [`10.1051/0004-6361/201219615`](http://doi.org/10.1051/0004-6361/201219615)

(ref: Flaherty17) Flaherty, K. M., Hughes, A. M., Rose, S. C., et al. 2017, ApJ, 843, 150, doi: [`10.3847/1538-4357/aa79f9`](http://doi.org/10.3847/1538-4357/aa79f9)

(ref: Foreman_Mackey13) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: Fuente10) Fuente, A., Cernicharo, J., Agúndez, M., et al. 2010, A&A, 524, A19, doi: [`10.1051/0004-6361/201014905`](http://doi.org/10.1051/0004-6361/201014905)

(ref: Fuente23) Fuente, A., Rivière-Marichalar, P., Beitia-Antero, L., et al. 2023, A&A, 670, A114, doi: [`10.1051/0004-6361/202244843`](http://doi.org/10.1051/0004-6361/202244843)

(ref: Furuya22) Furuya, K., Tsukagoshi, T., Qi, C., et al. 2022, ApJ, 926, 148, doi: [`10.3847/1538-4357/ac45ff`](http://doi.org/10.3847/1538-4357/ac45ff)

(ref: Gaia21) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2021, A&A, 649, A1, doi: [`10.1051/0004-6361/202039657`](http://doi.org/10.1051/0004-6361/202039657)

(ref: Garufi22) Garufi, A., Podio, L., Codella, C., et al. 2022, A&A, 658, A104, doi: [`10.1051/0004-6361/202141264`](http://doi.org/10.1051/0004-6361/202141264)

(ref: Goldsmith99) Goldsmith, P. F., & Langer, W. D. 1999, ApJ, 517, 209, doi: [`10.1086/307195`](http://doi.org/10.1086/307195)

(ref: Gottlieb03) Gottlieb, C. A., Myers, P. C., & Thaddeus, P. 2003, ApJ, 588, 655, doi: [`10.1086/368378`](http://doi.org/10.1086/368378)

(ref: Grady00) Grady, C. A., Devine, D., Woodgate, B., et al. 2000, ApJ, 544, 895, doi: [`10.1086/317222`](http://doi.org/10.1086/317222)

(ref: Gravity_CITau) Gravity Collaboration, Soulain, A., Perraut, K., et al. 2023, A&A, 674, A203, doi: [`10.1051/0004-6361/202346446`](http://doi.org/10.1051/0004-6361/202346446)

(ref: Guidi22) Guidi, G., Isella, A., Testi, L., et al. 2022, A&A, 664, A137, doi: [`10.1051/0004-6361/202142303`](http://doi.org/10.1051/0004-6361/202142303)

(ref: Guilloteau16) Guilloteau, S., Reboussin, L., Dutrey, A., et al. 2016, A&A, 592, A124, doi: [`10.1051/0004-6361/201527088`](http://doi.org/10.1051/0004-6361/201527088)

(ref: Guzman21_MAPS) Guzmán, V. V., Bergner, J. B., Law, C. J., et al. 2021, ApJS, 257, 6, doi: [`10.3847/1538-4365/ac1440`](http://doi.org/10.3847/1538-4365/ac1440)

(ref: Heck12) Heck, P. R., Hoppe, P., & Huth, J. 2012, , 47, 649, doi: [`10.1111/j.1945-5100.2012.01362.x`](http://doi.org/10.1111/j.1945-5100.2012.01362.x)

(ref: Hernandez_Vera24) Hernández-Vera, C., Guzmán, V. V., Artur de la Villarmois, E., et al. 2024, ApJ, 967, 68, doi: [`10.3847/1538-4357/ad3cdb`](http://doi.org/10.3847/1538-4357/ad3cdb)

(ref: Huang24) Huang, J., Bergin, E. A., Le Gal, R., et al. 2024, ApJ, 973, 135, doi: [`10.3847/1538-4357/ad6447`](http://doi.org/10.3847/1538-4357/ad6447)

(ref: Huang18_DSHARPII) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJL, 869, L42, doi: [`10.3847/2041-8213/aaf740`](http://doi.org/10.3847/2041-8213/aaf740)

(ref: Hunter07) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Ilee21) Ilee, J. D., Walsh, C., Booth, A. S., et al. 2021, ApJS, 257, 9, doi: [`10.3847/1538-4365/ac1441`](http://doi.org/10.3847/1538-4365/ac1441)

(ref: Isella16) Isella, A., Guidi, G., Testi, L., et al. 2016, , 117, 251101, doi: [`10.1103/PhysRevLett.117.251101`](http://doi.org/10.1103/PhysRevLett.117.251101)

(ref: Izquierdo22) Izquierdo, A. F., Facchini, S., Rosotti, G. P., van Dishoeck, E. F., & Testi, L. 2022, ApJ, 928, 2, doi: [`10.3847/1538-4357/ac474d`](http://doi.org/10.3847/1538-4357/ac474d)

(ref: Jewitt97) Jewitt, D., Matthews, H. E., Owen, T., & Meier, R. 1997, Science, 278, 90, doi: [`10.1126/science.278.5335.90`](http://doi.org/10.1126/science.278.5335.90)

(ref: Kama19) Kama, M., Shorttle, O., Jermyn, A. S., et al. 2019, ApJ, 885, 114, doi: [`10.3847/1538-4357/ab45f8`](http://doi.org/10.3847/1538-4357/ab45f8)

(ref: Keyte24_HD169142) Keyte, L., Kama, M., Booth, A. S., Law, C. J., & Leemker, M. 2024a, MNRAS, 534, 3576, doi: [`10.1093/mnras/stae2314`](http://doi.org/10.1093/mnras/stae2314)

(ref: Keyte24) Keyte, L., Kama, M., Chuang, K.-J., et al. 2024b, MNRAS, 528, 388, doi: [`10.1093/mnras/stae019`](http://doi.org/10.1093/mnras/stae019)

(ref: Keyte23) Keyte, L., Kama, M., Booth, A. S., et al. 2023, Nature Astronomy, 7, 684, doi: [`10.1038/s41550-023-01951-9`](http://doi.org/10.1038/s41550-023-01951-9)

(ref: Kim03) Kim, E., & Yamamoto, S. 2003, Journal of Molecular Spectroscopy, 219, 296, doi: [`10.1016/S0022-2852(03)00027-4`](http://doi.org/10.1016/S0022-2852(03)00027-4)

(ref: Klaassen13) Klaassen, P. D., Juhasz, A., Mathews, G. S., et al. 2013, A&A, 555, A73, doi: [`10.1051/0004-6361/201321129`](http://doi.org/10.1051/0004-6361/201321129)

(ref: Laas19) Laas, J. C., & Caselli, P. 2019, A&A, 624, A108, doi: [`10.1051/0004-6361/201834446`](http://doi.org/10.1051/0004-6361/201834446)

(ref: Law23_HD16) Law, C. J., Booth, A. S., & Öberg, K. I. 2023, ApJL, 952, L19, doi: [`10.3847/2041-8213/acdfd0`](http://doi.org/10.3847/2041-8213/acdfd0)

(ref: LawMAPSIII) Law, C. J., Loomis, R. A., Teague, R., et al. 2021a, ApJS, 257, 3, doi: [`10.3847/1538-4365/ac1434`](http://doi.org/10.3847/1538-4365/ac1434)

(ref: Law21_MAPSIV) Law, C. J., Teague, R., Loomis, R. A., et al. 2021b, ApJS, 257, 4, doi: [`10.3847/1538-4365/ac1439`](http://doi.org/10.3847/1538-4365/ac1439)

(ref: Legal19) Le Gal, R., Öberg, K. I., Loomis, R. A., Pegues, J., & Bergner, J. B. 2019, ApJ, 876, 72, doi: [`10.3847/1538-4357/ab1416`](http://doi.org/10.3847/1538-4357/ab1416)

(ref: Legal21) Le Gal, R., Öberg, K. I., Teague, R., et al. 2021, ApJS, 257, 12, doi: [`10.3847/1538-4365/ac2583`](http://doi.org/10.3847/1538-4365/ac2583)

(ref: Loomis18) Loomis, R. A., Cleeves, L. I., Öberg, K. I., et al. 2018, ApJ, 859, 131, doi: [`10.3847/1538-4357/aac169`](http://doi.org/10.3847/1538-4357/aac169)

(ref: Loomis20) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2020, ApJ, 893, 101, doi: [`10.3847/1538-4357/ab7cc8`](http://doi.org/10.3847/1538-4357/ab7cc8)

(ref: Ma24) Ma, R., Quan, D., Zhou, Y., et al. 2024, Research in Astronomy and Astrophysics, 24, 075017, doi: [`10.1088/1674-4527/ad5771`](http://doi.org/10.1088/1674-4527/ad5771)

(ref: McMullin_etal_2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Millar90) Millar, T. J., & Herbst, E. 1990, A&A, 231, 466

(ref: Miotello19) Miotello, A., Facchini, S., van Dishoeck, E. F., et al. 2019, A&A, 631, A69, doi: [`10.1051/0004-6361/201935441`](http://doi.org/10.1051/0004-6361/201935441)

(ref: Muller05) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215, doi: [`10.1016/j.molstruc.2005.01.027`](http://doi.org/10.1016/j.molstruc.2005.01.027)

(ref: Muller01) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49, doi: [`10.1051/0004-6361:20010367`](http://doi.org/10.1051/0004-6361:20010367)

(ref: Muller19) Müller, H. S. P., Maeda, A., Thorwirth, S., et al. 2019, A&A, 621, A143, doi: [`10.1051/0004-6361/201834517`](http://doi.org/10.1051/0004-6361/201834517)

(ref: Muro_Arena18) Muro-Arena, G. A., Dominik, C., Waters, L. B. F. M., et al. 2018, A&A, 614, A24, doi: [`10.1051/0004-6361/201732299`](http://doi.org/10.1051/0004-6361/201732299)

(ref: Oberg21_MAPSI) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1, doi: [`10.3847/1538-4365/ac1432`](http://doi.org/10.3847/1538-4365/ac1432)

(ref: Pacheco16) Pacheco-Vázquez, S., Fuente, A., Baruteau, C., et al. 2016, A&A, 589, A60, doi: [`10.1051/0004-6361/201527089`](http://doi.org/10.1051/0004-6361/201527089)

(ref: Paneque24) Paneque-Carreño, T., Izquierdo, A. F., Teague, R., et al. 2024, A&A, 684, A174, doi: [`10.1051/0004-6361/202347757`](http://doi.org/10.1051/0004-6361/202347757)

(ref: Paneque_MAPS) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., et al. 2023, A&A, 669, A126, doi: [`10.1051/0004-6361/202244428`](http://doi.org/10.1051/0004-6361/202244428)

(ref: Paquette17) Paquette, J. A., Hornung, K., Stenzel, O. J., et al. 2017, MNRAS, 469, S230, doi: [`10.1093/mnras/stx1623`](http://doi.org/10.1093/mnras/stx1623)

(ref: Phuong18) Phuong, N. T., Chapillon, E., Majumdar, L., et al. 2018, A&A, 616, L5, doi: [`10.1051/0004-6361/201833766`](http://doi.org/10.1051/0004-6361/201833766)

(ref: Phuong21) Phuong, N. T., Dutrey, A., Chapillon, E., et al. 2021, A&A, 653, L5, doi: [`10.1051/0004-6361/202141881`](http://doi.org/10.1051/0004-6361/202141881)

(ref: Pinte18_HD16) Pinte, C., Price, D. J., Ménard, F., et al. 2018a, ApJL, 860, L13, doi: [`10.3847/2041-8213/aac6dc`](http://doi.org/10.3847/2041-8213/aac6dc)

(ref: pinte18) Pinte, C., Ménard, F., Duchêne, G., et al. 2018b, A&A, 609, A47, doi: [`10.1051/0004-6361/201731377`](http://doi.org/10.1051/0004-6361/201731377)

(ref: Pinte20) Pinte, C., Price, D. J., Ménard, F., et al. 2020, ApJL, 890, L9, doi: [`10.3847/2041-8213/ab6dda`](http://doi.org/10.3847/2041-8213/ab6dda)

(ref: astropy_2018) Price-Whelan, A. M., Sipőcz, B. M., Günther, H. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Qi11) Qi, C., D’Alessio, P., Öberg, K. I., et al. 2011, ApJ, 740, 84, doi: [`10.1088/0004-637X/740/2/84`](http://doi.org/10.1088/0004-637X/740/2/84)

(ref: Rab20) Rab, C., Kamp, I., Dominik, C., et al. 2020, A&A, 642, A165, doi: [`10.1051/0004-6361/202038712`](http://doi.org/10.1051/0004-6361/202038712)

(ref: Rampinelli24) Rampinelli, L., Facchini, S., Leemker, M., et al. 2024, A&A, 689, A65, doi: [`10.1051/0004-6361/202449698`](http://doi.org/10.1051/0004-6361/202449698)

(ref: Ranjan18) Ranjan, S., Todd, Z. R., Sutherland, J. D., & Sasselov, D. D. 2018, Astrobiology, 18, 1023, doi: [`10.1089/ast.2017.1770`](http://doi.org/10.1089/ast.2017.1770)

(ref: Rich20_HST) Rich, E. A., Wisniewski, J. P., Sitko, M. L., et al. 2020, ApJ, 902, 4, doi: [`10.3847/1538-4357/abb2a3`](http://doi.org/10.3847/1538-4357/abb2a3)

(ref: Marichalar22) Rivière-Marichalar, P., Fuente, A., Esplugues, G., et al. 2022, A&A, 665, A61, doi: [`10.1051/0004-6361/202142906`](http://doi.org/10.1051/0004-6361/202142906)

(ref: Rosenfeld13) Rosenfeld, K. A., Andrews, S. M., Hughes, A. M., Wilner, D. J., & Qi, C. 2013, ApJ, 774, 16, doi: [`10.1088/0004-637X/774/1/16`](http://doi.org/10.1088/0004-637X/774/1/16)

(ref: Rosotti21) Rosotti, G. P., Ilee, J. D., Facchini, S., et al. 2021, MNRAS, 501, 3427, doi: [`10.1093/mnras/staa3869`](http://doi.org/10.1093/mnras/staa3869)

(ref: Ruffle99) Ruffle, D. P., Hartquist, T. W., Caselli, P., & Williams, D. A. 1999, MNRAS, 306, 691, doi: [`10.1046/j.1365-8711.1999.02562.x`](http://doi.org/10.1046/j.1365-8711.1999.02562.x)

(ref: Salinas17) Salinas, V. N., Hogerheijde, M. R., Mathews, G. S., et al. 2017, A&A, 606, A125, doi: [`10.1051/0004-6361/201731223`](http://doi.org/10.1051/0004-6361/201731223)

(ref: Semenov18) Semenov, D., Favre, C., Fedele, D., et al. 2018, A&A, 617, A28, doi: [`10.1051/0004-6361/201832980`](http://doi.org/10.1051/0004-6361/201832980)

(ref: Shirley15) Shirley, Y. L. 2015, PASP, 127, 299, doi: [`10.1086/680342`](http://doi.org/10.1086/680342)

(ref: Sierra21_MAPS) Sierra, A., Pérez, L. M., Zhang, K., et al. 2021, ApJS, 257, 14, doi: [`10.3847/1538-4365/ac1431`](http://doi.org/10.3847/1538-4365/ac1431)

(ref: Speedie25) Speedie, J., Dong, R., Teague, R., et al. 2025, arXiv e-prints, arXiv:2503.01957, doi: [`10.48550/arXiv.2503.01957`](http://doi.org/10.48550/arXiv.2503.01957)

(ref: Teague19JOSS) Teague, R. 2019, The Journal of Open Source Software, 4, 1632, doi: [`10.21105/joss.01632`](http://doi.org/10.21105/joss.01632)

(ref: rich_teague_2020_4321137) Teague, R. 2020, richteague/keplerian_mask: Initial Release, 1.0, Zenodo, doi: [`10.5281/zenodo.4321137`](http://doi.org/10.5281/zenodo.4321137)

(ref: Teague_19Natur) Teague, R., Bae, J., & Bergin, E. A. 2019a, Nature, 574, 378, doi: [`10.1038/s41586-019-1642-0`](http://doi.org/10.1038/s41586-019-1642-0)

(ref: Teague19Natur) —. 2019b, Nature, 574, 378, doi: [`10.1038/s41586-019-1642-0`](http://doi.org/10.1038/s41586-019-1642-0)

(ref: Teague18_HD163296) Teague, R., Bae, J., Bergin, E. A., Birnstiel, T., & Foreman-Mackey, D. 2018a, ApJL, 860, L12, doi: [`10.3847/2041-8213/aac6d7`](http://doi.org/10.3847/2041-8213/aac6d7)

(ref: Teague18_bettermoments) Teague, R., & Foreman-Mackey, D. 2018, Bettermoments: A Robust Method To Measure Line Centroids, v1.0, Zenodo, doi: [`10.5281/zenodo.1419754`](http://doi.org/10.5281/zenodo.1419754)

(ref: disksurf_Teague) Teague, R., Law, C. J., Huang, J., & Meng, F. 2021, Journal of Open Source Software, 6, 3827, doi: [`10.21105/joss.03827`](http://doi.org/10.21105/joss.03827)

(ref: Teague16) Teague, R., Guilloteau, S., Semenov, D., et al. 2016, A&A, 592, A49, doi: [`10.1051/0004-6361/201628550`](http://doi.org/10.1051/0004-6361/201628550)

(ref: Teague18_CS) Teague, R., Henning, T., Guilloteau, S., et al. 2018b, ApJ, 864, 133, doi: [`10.3847/1538-4357/aad80e`](http://doi.org/10.3847/1538-4357/aad80e)

(ref: Teague21) Teague, R., Bae, J., Aikawa, Y., et al. 2021, ApJS, 257, 18, doi: [`10.3847/1538-4365/ac1438`](http://doi.org/10.3847/1538-4365/ac1438)

(ref: Teague22) Teague, R., Bae, J., Andrews, S. M., et al. 2022, ApJ, 936, 163, doi: [`10.3847/1538-4357/ac88ca`](http://doi.org/10.3847/1538-4357/ac88ca)

(ref: Temmink23) Temmink, M., Booth, A. S., van der Marel, N., & van Dishoeck, E. F. 2023, A&A, 675, A131, doi: [`10.1051/0004-6361/202346272`](http://doi.org/10.1051/0004-6361/202346272)

(ref: Thi04) Thi, W. F., van Zadelhoff, G. J., & van Dishoeck, E. F. 2004, A&A, 425, 955, doi: [`10.1051/0004-6361:200400026`](http://doi.org/10.1051/0004-6361:200400026)

(ref: vanderMarel13) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2013, Science, 340, 1199, doi: [`10.1126/science.1236770`](http://doi.org/10.1126/science.1236770)

(ref: vanderPlas14) van der Plas, G., Casassus, S., Ménard, F., et al. 2014, ApJL, 792, L25, doi: [`10.1088/2041-8205/792/2/L25`](http://doi.org/10.1088/2041-8205/792/2/L25)

(ref: vanderTak07) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: vanderVelden20) van der Velden, E. 2020, The Journal of Open Source Software, 5, 2004, doi: [`10.21105/joss.02004`](http://doi.org/10.21105/joss.02004)

(ref: vanderWalt_etal_2011) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science and Engineering, 13, 22, doi: [`10.1109/MCSE.2011.37`](http://doi.org/10.1109/MCSE.2011.37)

(ref: Vastel18) Vastel, C., Quénard, D., Le Gal, R., et al. 2018, MNRAS, 478, 5514, doi: [`10.1093/mnras/sty1336`](http://doi.org/10.1093/mnras/sty1336)

(ref: Visser18) Visser, R., Bruderer, S., Cazzoletti, P., et al. 2018, A&A, 615, A75, doi: [`10.1051/0004-6361/201731898`](http://doi.org/10.1051/0004-6361/201731898)

(ref: Wichittanakom20) Wichittanakom, C., Oudmaijer, R. D., Fairlamb, J. R., et al. 2020, MNRAS, 493, 234, doi: [`10.1093/mnras/staa169`](http://doi.org/10.1093/mnras/staa169)

(ref: Wilson99) Wilson, T. L. 1999, Reports on Progress in Physics, 62, 143, doi: [`10.1088/0034-4885/62/2/002`](http://doi.org/10.1088/0034-4885/62/2/002)

(ref: Xie21) Xie, C., Haffert, S. Y., de Boer, J., et al. 2021, A&A, 650, L6, doi: [`10.1051/0004-6361/202140602`](http://doi.org/10.1051/0004-6361/202140602)

(ref: Yamato25) Yamato, Y., Aikawa, Y., & Law, C. J. 2025, in prep., in prep

(ref: Yoshida24) Yoshida, T. C., Nomura, H., Law, C. J., et al. 2024, ApJL, 971, L15, doi: [`10.3847/2041-8213/ad654c`](http://doi.org/10.3847/2041-8213/ad654c)

(ref: Zhang21) Zhang, K., Booth, A. S., Law, C. J., et al. 2021, ApJS, 257, 5, doi: [`10.3847/1538-4365/ac1580`](http://doi.org/10.3847/1538-4365/ac1580)

(ref: Zhang18) Zhang, S., Zhu, Z., Huang, J., et al. 2018, ApJL, 869, L47, doi: [`10.3847/2041-8213/aaf744`](http://doi.org/10.3847/2041-8213/aaf744)

[^1]: The Submillimeter Array is a joint project between the Smithsonian Astrophysical Observatory and the Academia Sinica Institute of Astronomy and Astrophysics and is funded by the Smithsonian Institution and the Academia Sinica.

[^2]: <https://lweb.cfa.harvard.edu/~cqi/mircook.html>

</paper>

Write the methods card for this paper.