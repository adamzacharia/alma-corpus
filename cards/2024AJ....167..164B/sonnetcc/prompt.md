# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024AJ....167..164B\sonnetcc\reply.txt

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
 "bibcode": "2024AJ....167..164B",
 "title": "An ALMA Molecular Inventory of Warm Herbig Ae Disks. I. Molecular Rings, Asymmetries, and Complexity in the HD 100546 Disk",
 "year": 2024,
 "journal": "The Astronomical Journal",
 "first_author": "Booth, Alice S.",
 "n_authors": 14,
 "arxiv_id": "2402.04001",
 "doi": "10.3847/1538-3881/ad2700",
 "alma_projects_linked_by_archive": [
  "2021.1.00738.S"
 ]
}
```

Paper text:
<paper>
# An ALMA molecular inventory of warm Herbig Ae disks:\
I. Molecular rings, asymmetries and complexity in the HD 100546 disk

## Abstract

Observations of disks with the Atacama Large Millimeter/submillimeter Array (ALMA) allow us to map the chemical makeup of nearby protoplanetary disks with unprecedented spatial resolution and sensitivity. The typical outer Class II disk observed with ALMA is one with an elevated C/O ratio and a lack of oxygen-bearing complex organic molecules, but there are now some interesting exceptions: three transition disks around Herbig Ae stars all show oxygen-rich gas traced via the unique detections of the molecules SO and . We present the first results of an ALMA line survey at $\approx$337 to 357 GHz of such disks and focus this paper on the first Herbig Ae disk to exhibit this chemical signature - HD 100546. In these data, we detect 19 different molecules including NO, and (methyl formate). We also make the first tentative detections of and in protoplanetary disks. Multiple molecular species are detected in rings, which are, surprisingly, all peaking just beyond the underlying millimeter continuum ring at $\approx$200 au. This result demonstrates a clear connection between the large dust distribution and the chemistry in this flat disk. We discuss the physical and/or chemical origin of these sub-structures in relation to ongoing planet formation in the HD 100546 disk. We also investigate how similar and/or different the molecular make up of this disk is to other chemically well-characterised Herbig Ae disks. The line-rich data we present motivates the need for more ALMA line surveys to probe the observable chemistry in Herbig Ae systems which offer unique insight into the composition of disk ices, including complex organic molecules.

# Introduction

There is now clear evidence that planet-formation is well underway in the $>$1 Myr old disks of gas, dust and ice around young stars (cite: 2018A&A...617A..44K; 2019NatAs...3..749H; 2019ApJ...879L..25I). Although the direct detection of giant planets in disks is still rare (cite: 2018A&A...617A..44K) there are now a number of candidate planets (cite: 2022arXiv220505696C; 2023MNRAS.522L..51H; 2023NatAs...7.1208W), and, the expected impact forming planets have on their parent disk is traceable in the millimetre dust emission, CO gas kinematics, and tentatively, in the disk chemistry (cite: Andrews2018dsharp; 2018ApJ...860L..12T; 2019NatAs...3.1109P; 2022ApJ...928....2I; 2022ApJ...937L...1L; 2022ApJ...934L..20B; 2023A&A...669A..53B; 2023arXiv230613710L). The physical processes that drive planet formation and determine the composition of these forming planets are set by the parent protoplanetary disk (cite: 2021PhR...893....1O; 2022arXiv220309818M). Therefore, unravelling the physical and chemical conditions in disks is key to understanding the planet formation process.

From both small population studies and detailed studies on a handful of individual disks with the Atacama Large Millimeter/submillimeter Array (ALMA) a picture of the “typical" Class II disk composition has emerged. In most cases, the disk molecular layer on 10-100 au scales has an elevated carbon-to-oxygen ratio (C/O). This is traced via column densities of that are orders of magnitude higher than initially predicted (cite: 2019A&A...631A..69M); disk averaged column density ratios of CS-to-SO that are greater than 1 (cite: 2021ApJS..257...12L); and complex molecules that lack oxygen (, and ) are more abundant than anticipated (cite: 2021ApJS..257....9I). These results are all consistent with the gas-phase depletion of both oxygen and carbon in the molecular layer but with O more strongly depleted than C resulting in C/O$>$1 (cite: 2016A&A...592A..83K; 2021ApJS..257....7B). This can be achieved by the removal of and from the disk molecular layer due to the growth, settling and drift of small ice-coated dust grains coupled with gas-phase and ice-phase chemical depletion mechanisms (cite: 2015ApJ...807L..32D; 2018ApJ...856...85S; 2018A&A...618A.182B; 2020ApJ...899..134K; 2022A&A...665A..45P; 2022ApJ...938...29F; 2023NatAs...7...49C). The depletion of gas-phase C and O implies that the ice is enriched in these elements.

The above picture holds for disks around T-Tauri and Herbig Ae stars, although, for the latter, there are only a few sources for which the chemistry has been studied in detail. This includes the HD 163296 and MWC 480 disks, which we note are gapped disks but not transition disks with a large central cavity (cite: 2021ApJS..257....1O). There are expected differences in the chemistry of these typically higher-mass sources due to the increased temperature of the host star and the different incident UV and X-ray radiation fields. Physical and chemical models predict warmer disks, lower levels of ionisation and, due to the increased FUV flux, the warm molecular layer is expected to reside closer to the disk midplane (cite: 2015A&A...582A..88W; 2018A&A...616A..19A). Although the sample size for the Herbig Ae disks is small there is observational evidence to support these trends: this includes lower /CO column density ratios, less abundant , and lower detection rates of the cold chemistry tracers and DCN (cite: 2004A&A...425..955T; 2020ApJ...893..101L; 2020ApJ...890..142P; 2021ApJS..257...13A; 2023arXiv230302167P; Booth2023).

Transition disks around young Herbig Ae type stars appear to be outliers from the “typical" disk. In the few of these sources that have been observed in detail in molecular lines - HD 100546, IRS 48 and HD 169142 - a reservoir of oxygen-rich gas has been revealed primarily by emission lines of and . These sources give us a window into the typically unobservable volatile reservoir in disks. First, SO and were detected in the HD 100546 disk along with a compact component of , all of which thought to originate from the warm edge of the millimetre dust cavity (cite: 2018A&A...611A..16B; 2021NatAs...5..684B; 2023A&A...669A..53B). Observations of IRS 48 then revealed the first detections of , and in protoplanetary disks (cite: 2021A&A...651L...5V; 2021A&A...651L...6B; 2022A&A...659A..29B; 2023arXiv230300768L). In addition, the measured rotational temperatures for and in IRS 48 of $\approx$100-200 K thus indicate the conditions for and COMs ice sublimation (cite: 2021A&A...651L...5V). Most recently, the HD 169142 disk was also revealed to have a reservoir of and within the millimetre dust cavity (cite: 2023arXiv230613710L; Booth2023). Although the observations are mostly spatially unresolved, (cite: Booth2023) report additional detections of DCN, CS, , and - hinting at similarities in the chemistry of the HD 169142 disk to the non-transitional Herbig Ae disks (cite: 2019ApJ...876...72L; 2021ApJS..257...12L; 2021ApJS..257....9I). The only other chemically well studied transition disk around a Herbig source is HD 142527. Observations so far do not show bright or emission, however, the millimetre dust (and ice) trap, is located further from the star where it remains too cold for thermal ice sublimation (cite: 2023A&A...675A.131T).

It is not yet clear how the chemistry in these warm Herbig Ae transition disks compares to other well-studied sources, both full Herbig Ae disks and T-Tauri disks. This is in terms of the abundances of both simple molecules, e.g., , , and , and, the more complex molecules, e.g., and , and, the spatial distribution of these species with respect to millimetre dust substructures. This paper presents ALMA Band 7 observations of the planet-forming disk HD 100546 where we target $>$20 molecules at $\approx$0.3$''$ ($\approx$30 au) resolution. These line-rich data enable us to put the HD 100546 disk in proper context with other Class II disks whose chemistry has been studied in greater detail. In paper II, (cite: Booth2023_irs48), we present data on the IRS 48 disk which was observed in the same ALMA program. With this molecular inventory we determine the relationship (if any) between the different molecular tracers and the millimetre dust sub-structures, we use the simple molecules to constrain the underlying physical/chemical conditions, and we investigate the degree of molecular complexity that has been attained in this disk.

# Methods

## Target

HD 100546 is nearby young Herbig Ae star host to a gas-rich protoplanetary disk (see Table [\[tab:A1\]](#tab:A1)). The millimetre dust emission from the HD 100546 disk has been well studied with ALMA, which detected two dust rings peaking at $\approx$25 and $\approx$200 au (cite: 2014ApJ...791L...6W; 2019ApJ...871...48P; 2021A&A...651A..90F). Molecular line observations of the HD 100546 disk with ALMA have reported detections of the CO isotopologues , , and the aforementioned detections of , and (cite: 2019MNRAS.485..739M; 2018A&A...611A..16B; 2021NatAs...5..684B; 2023A&A...669A..53B). Additionally, and have been detected with the Australia Telescope Compact Array (ATCA) and the Atacama Compact Array (ACA), respectively (cite: Wright2015; 2023NatAs.tmp...92K).

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| SpT | Dist. | Incl. | PA | L$_{*}$ | M$_{*}$ | M$_{dust}$ | M$_{gas}$ | log$_{10}(\dot{M}_{acc}$) | log10($L_{Xray}$) | v$_{sys}$ |  |
|  | (pc) | (deg) | (deg) | ($L_{\odot}$) | ($M_{\odot}$) | ($M_{\odot}$) | ($M_{\odot}$) | ($M_{\odot}$ yr$^{-1}$) | (erg s$^{-1}$) | (km s$^{-1}$) |  |
| A0-A1 \[1\] | 110 \[2\] | 41.7 \[3\] | 146.0 \[3\] | 23.5 \[2\] | 2.2 \[2\] | 1.1$\times10^{-3}$ \[4\] | 1.5$\times10^{-1}$ \[4\] | -6.81 \[1\] | 28.1 \[5\] | 5.70 \[3\] |  |

![](matched_filter_hd100546.png)

## Data reduction

HD 100546 was observed with ALMA in program 2021.1.00738.S (PI. A. S. Booth). These observations were taken in configuration C4 in Band 7 with baselines ranging from $\approx$15 to $\approx$1300 m. These $\approx$0.3$''$ data are sufficient to distinguish between gas in the cavity and associated to the two dust rings but cannot resolve the gas within the cavity. The data consist of two spectral settings with four spectral windows each at a spectral resolution of 976.6 kHz (0.84 km s$^{-1}$ at 350 GHz) and a bandwidth of 1.875 GHz. These spectral windows are centered at 338.790824, 340.732413, 348.916936 and 350.775389 GHz for setting A and, 344.240980, 3459.40999, 354.367095 and 356.067114 GHz for setting B. Further details on the spectral set-up and individual execution blocks are provided in the Appendix in Table [1](#tab:A3). This program also targeted the IRS 48 disk and these data will be presented in (cite: Booth2023_irs48). The data were calibrated via the standard ALMA pipeline using `CASA` version 6.2.1 (cite: 2007ASPC..376..127M). These individually calibrated executions were aligned to a common phase centre using the `fixvis` and `fixplanets` tasks. Self-calibration was performed on the continuum data after flagging the strong lines. Both phase (6 rounds of decreasing solint intervals) and amplitude (1 round) calibrations were applied until the signal-to-noise of the continuum data plateaued. For HD 100546 this resulted in a peak continuum signal-to-noise increase from $\approx$525 to $\approx$5450. Self-calibration was necessary to detect the weak outer ring of millimetre emission in the HD 100546 disk. These solutions were then applied to the line data. The continuum was subtracted using `uvcontsub` with a fit order of 1 and excluding channels of bright lines and atmospheric absorption features that were identified via visual inspection of the data with the `plotms` task.

## Line identification

For an initial line identification in the data, we applied matched filtering (cite: Loomis2018). This technique utilises the predictable kinematic pattern of Keplerian line emission to detect weak line emission whereby a filter, e.g., Keplerian model or strong line detection in the same disk (a so called image filter), is cross-correlated with the visibility data. Figure [1](#fig:1) shows the resulting matched filter response using a Keplerian model with an outer radius of 300 au, which illustrates the frequency coverage of our observations and the line-rich nature of the data. We take a line detection to be any peak above the 4 $\sigma$ level. As the impulse response depends on how accurately the filter represents the underlying emission structure, different filters, e.g., Keplerian models of different sizes and image filters of different strong lines, will yield a different signal-to-noise for a detected line (cite: 2020ApJ...893..101L). This is investigated further for the detection of weaker lines in Section 2.5.

## Imaging

The data were imaged in CASA using `tCLEAN` with the multiscale deconvolver. Individual lines were cleaned with Keplerian masks down to 4$\times$ the noise level of the dirty image. The Keplerian masks were constructed using the properties for the HD 100546 disk as listed in Table [\[tab:A1\]](#tab:A1). These masks were generated with the code from (cite: rich_teague_2020_4321137). A channel width of 976.6 kHz for each of the eight spectral windows results in a range of velocity resolutions from 0.82 to 0.87 km s$^{-1}$ over the 337 to 356 GHz range of the observations. Therefore, for consistency, all of the spectral windows were imaged using a velocity resolution of 0.9 km s$^{-1}$. For the strong lines, a briggs robust of +0.5 was used and for the weaker lines +0.5 or +2.0 was used depending on the emission morphology, e.g., compact or extended, respectively. The resulting beam sizes and rms noise for each line imaged are listed in Table [\[tab:hd100546_images\]](#tab:hd100546_images) in the Appendix.

## Weak-line detections

To search for and confirm the detections of weak lines in the data we use the visibility and image plane techniques: matched filtering and spectral stacking with *GoFish* ((cite: Loomis2018) and (cite: GoFish), respectively). For the matched filtering, as well as the Keplerian model result shown in Figure [1](#fig:1), we also use specific strong lines as filters to look for weaker lines of molecules that are either isotopologues of the strong line or are expected to share a common emission morphology. We also imaged the potentially weak line detections and used the spectral stacking tool *GoFish* to create average spectra over different radial regions of the disks.

## Column density calculations

We estimate column densities following the methods outlined in (cite: 2018ApJ...859..131L). This assumes that the gas is in local thermodynamic equilibrium and includes an optical depth correction factor where we assume a line width of 1 km s$^{-1}$. Since we only have one detected transition for most molecules we do this over a set of fixed rotational temperatures. For the molecules where multiple transitions, e.g., , are detected we pick one representative transition. Future work will focus specifically on constraining the excitation conditions of these molecules individually. In the case of CN, and the chosen lines are the strongest of the $N=3-2$, $N=4-3$ and $J=7/2-5/2$ hyper-fine groups, respectively. For the $J=6_{(4,2)}-6_{(3,3)}$ is the strongest line detected and for SO the strongest transition is the $J=7_8-6_7$. For we pick the $J=7_{0}-6_{0}$ transition and for and we use the $J=31-30$ and $J=19-18$ transitions which are both blends of multiple transitions.

![](HD100546_gallery.png)

# Results

## Molecule detection summary

In total, we have detected 19 different molecules in the HD 100546 disk. This includes the first detections of the rare isotopologues and in protoplanetary disks. A range of nitrogen- (, , ) and sulphur- (, , , ) bearing species are detected including some of the isotopologues along with , , and . Multiple transitions are detected and we also robustly detect (methyl formate). The larger organic molecules commonly detected in other disks, e.g., , , (cite: 2021ApJS..257....9I), remain undetected in our observations and this is primarily due to a combination of line sensitivity and the intrinsic properties of the lines covered.

## Weak-line detections / non-detections

The results of the search for weak-line detections in the HD 100546 disk are summarised below and the associated figures are shown in Figure [10](#fig:weaklines) in the Appendix.

- Using CS as a filter we detect with a 9 $\sigma$ significance compared to the 6 $\sigma$ with the smooth 300 au Keplerian filter.

- The filter detects at the 7 $\sigma$ level and the GoFish profile shows weak emission in the outer disk on 100-300 au scales.

- The filter does not detect .

- To search for NO we compared the results of a few different image filters and found to have the highest response and detect three NO lines (two of which are blended) at 5 and 4 $\sigma$, respectively. There are additional NO transitions covered in these data at 350.689 GHz but they are blended with a line (as was also seen for the IRS 48 disk by (cite: 2022A&A...659A..29B; 2023arXiv230300768L)).

- With the SO filter we tentatively detect the $J=9_8-8_7$ transition at the 4 $\sigma$ level. In the channel maps with a Briggs robust of +0.5, compact emission is detected at the 3 $\sigma$ level across 5 consecutive channels which correspond to the same velocity range in which the SO is brightest. The other line we cover ($J=8_8-7_7$) is not detected but the noise is higher in the region of this line than for the detected line (see Table [\[tab:hd100546_images\]](#tab:hd100546_images)). We also report the non-detection of two lines.

- Due to the strong detection of in HD 100546 we could expect to also detect since these molecules share a common gas-phase formation pathway via OH (cite: 2018A&A...617A..28S). No lines are robustly detected with matched filtering using neither a Keplerian model nor an image filter. Since matched filtering works best for detecting weak emission that is spatially extended and spectrally resolved, if the is compact like the , it may not be detected with this technique. Indeed, in the image plane, 3 lines with upper energy levels of $\approx$60-70 K are detected with GoFish. The strongest for which is the $J=6_{(4,2)}-6_{(3,3)}$ line.

- With the strongest CN, HCN and lines as filters we detect weaker hyper-fine components of these transitions and also report non-detections of , and .

## Integrated intensity maps

Figure [2](#fig:mom01) presents the integrated intensity maps of the representative transitions of each molecule (not all isotopologues) detected in the HD 100546 disk and the 0.9 mm continuum emission. The integrated intensity maps of the SO, CS and isotopologues are shown in Figure [10](#fig:weaklines) in the Appendix and the HCN isotopologues will be the focus of future work. These line maps were generated using the Keplerian masks from the CLEAN-ing with no clipping thresholds. There are clear ring structures with radii of $\approx$200 au in the , , , , and emission maps whereas the shows no clear signs of sub-structure on these scales. The bulk of the emission is compact with evidence of a central cavity at $<$20 au, also seen in high resolution continuum data (cite: 2019ApJ...871...48P), and the emission drops off steeply beyond $\approx$100 au. In comparison, the emission is centrally peaked. In the outer disk, the molecular rings appear to be approximately co-spatial with the weak millimetre dust ring. In some of the rings, there is an azimuthal variation in brightness (e.g. CN and CS) most strongly seen in the . The detection of NO is weak but it also appears to be ringed. The and show compact emission as reported in (cite: 2021NatAs...5..684B; 2023A&A...669A..53B) and the new detections of and are compact as well.

![](HD100546_radial_profiles.png)

## Sub-structures in the HD 100546 disk

Many of the integrated intensity maps of the molecular lines detected in the HD 100546 disk show clear radial and azimuthal substructures. In particular, the outer molecular rings are at a similar location to the outer dust ring, which to date, has not typically been seen in disk observations (cite: 2021ApJS..257....3L). In this section, we describe these different features and the possible physical and/or chemical processes responsible for generating these different sub-structures will be discussed in Section 4.

Figure [3](#fig:HD100546_radial_profiles) shows the azimuthally averaged radial intensity profiles for the lines shown in Figure [2](#fig:mom01). The gas disk traced by is 600 au in size which is $\approx$2$\times$ the radial extent of the millimetre continuum emission. The CO isotopologues show a cavity in the inner disk and while there is no apparent gap in the outer disk traced in there is a shelf of emission across the location of the outer dust ring. Interestingly, the emission is centrally peaked and also shows a clear gap that follows the dust rings. The array of molecular rings at $\approx$200 to 240 au clearly align with the location of the outer dust ring but there are some shifts between different molecules, e.g., the HCN and CN peaks are offset by approximately half a beam from each other. The line flux within the outer dust gap at $\approx$110 au also varies between molecules where is the least reduced and the deepest gaps are found for and . There is also variation in the relative brightness of the two rings in different molecules. For example, the and rings in the inner and outer disk are similarly bright, whereas the , , , and rings are $\approx$2-5$\times$ fainter in the outer disk. In the inner disk, there is a clear anti-correlation between the SO (and ) and the CS (and ). Weak rings of emission are present in the radial profiles for SO (also shown more clearly in (cite: 2023A&A...669A..53B)) and (tentatively detected in (cite: 2021NatAs...5..684B)). To check more robustly for weak extended emission from other molecules we use GoFish (cite: GoFish) to create average spectra stacked within an annulus, of 180-250 au, which encompasses the emission detected in the outer ring. With this analysis, the outer rings of and are confirmed along with outer rings of and . Rings of and both go undetected. These six spectra are shown in Figure [11](#fig:gofish) in the Appendix.

To examine the relative locations of these rings in more detail we plot the location of the ring peaks for each molecule in Figure [4](#fig:radial_scatter) overlaid on a map of the azimuthally averaged radial profile of the continuum emission. There is a clear correlation between the positions of the peaks of the dust rings and the peaks of the molecular rings. Note this alignment of molecular rings with the dust is similar to what was seen in the PDS 70 disk (cite: 2021AJ....162...99F) and in the HD 163296 disk for the dust ring at 101 au (cite: 2021ApJS..257....3L). For the inner disk, all the molecules that contain oxygen (except ) peak within the central dust cavity and other molecules peak just outside center of the first dust ring. In the outer disk, the molecules all align with the second dust ring at 200 au but there is a gradient, e.g., CN and reach a brightness maximum farther out radially than the HCN and .

To explore whether or not these differences in peak radial locations are due to a different emitting height of these molecules in the disk we overlay ellipses on the integrated intensity maps of , HCN, CN, , CS and (see Figure [5](#fig:ellipses)). The ellipses are tracing the Z/R (geometric height from the midplane divided by radius) of 0 (the midplane), 0.1 and 0.25 surfaces at the radius where each of the species peaks in emission. Although we do not have the kinematic resolution to directly measure the emitting heights of these different molecules from the channel maps (e.g., (cite: 2023A&A...669A.126P)) we can gain insight from the geometry of the molecular rings compared with the different Z/R ellipses. The molecular rings in the outer disk appear to be arising from a layer in the disk close to the midplane and, given the spatial resolution of our observations, we can constrain this to be from a layer with Z/R$<$0.1. This is in contrast with the measurements of the emitting height where both (cite: 2022ApJ...932..114L) and (cite: 2023A&A...669A.158S) derive a Z/R of $\approx$0.25 at 200 au. Therefore, different emitting heights are likely not responsible for the different ring peak locations. For the inner disk, $<$50 au, we do not have the spatial resolution to rule out that these inner rings are arising from different layers in the disk.

There are also azimuthal asymmetries in the brightness of the outer molecular rings in HD 100546. This asymmetry is most clearly seen in , CN and CS. In Figure [6](#fig:hd100546_azimuth) we show polar deprojections of the integrated intensity maps for the 0.9 mm continuum, , , , HCN, , CS and . From this visualisation, it is clear that the molecules peak in similar azimuthal regions of the disk and this also follows an underlying asymmetry in the dust emission (as reported in (cite: 2021A&A...651A..90F)). There is a tentative eccentricity in the molecular line emission, seen most clearly in the , which is also seen in the dust by (cite: 2021A&A...651A..90F).

(cite: 2023A&A...669A..53B) reported asymmetric SO within the central dust cavity of the HD 100546 disk. In this work, we present two additional SO lines along with the other sulphur species CS and . Figure [7](#fig:hd100546_sulphur) shows the integrated intensity maps of the dust emission from (cite: 2019ApJ...871...48P) and the two new SO transitions detected in this work ($J=7_8-6_7$ and $J=8_8-7_7$) alongside the CS $J=7-6$, $J=10_{(1,10)}-9_{(1,9)}$ and, the detection of $J=9_8-8_7$. From this image gallery it is clear that the SO is sitting inside a broadly symmetric ring of CS and the SO asymmetry is most prominent in the warmest line we have detected (this is also the line with the smallest restoring beam). In addition, the is only detected in the south of the cavity where the main SO isotopologue is the brightest.

![](HD100546_radial_grid.png)

![](HD100546_ring_ellipses.png)

![](HD100546_azimuth_plot.png)

![](HD100546_SO_CS_planet_mom0_zoom.png)

## Column densities

We compute radial column density profiles for the molecules in the HD 100546 disk from the profiles presented in Figure [3](#fig:HD100546_radial_profiles). We explore a range of excitation temperatures: 30, 50, and 100 K and the results are shown in Figure [8](#fig:hd100546_radial_columns) and we summarise our findings here.

- reaches a peak column density of the order of $10^{17}~\mathrm{cm^{-2}}$ but becomes optically thick with a temperature of 50 K within 40 au and approaching optically thick at 100 K ($\tau\approx0.6$). In Table [\[tab:ratios\]](#tab:ratios) we list the column density ratios of different molecules relative to CO at their peak locations in the inner disk (at 100 K) and peak in the outer disk (at 30 K and 50 K). The column density is determined from the column density assuming /=557 and /=3.6 (cite: 1999RPPh...62..143W). For the inner disk these column density ratios are tentative due to potentially optically thick emission.

- and HCN are both approaching optically thick in the inner 40 au of the disk with the peak value for $\tau$ ranging from 0.1 to 1.0 depending on the gas temperature, and have similar overall column densities. In comparison, the CN, NO and are optically thin throughout the disk and NO has the highest column density of the three nitrogen-bearing molecules detected.

- For both CS and SO we can assess the optical depth of the main isotopologues with the detections of and where in the local ISM / is 22 (cite: 1999RPPh...62..143W). In the inner disk where the CS and SO peak, the respective column densities of the isotopologues can be up to 3$\times$ higher than the main isotopologue once correcting for the isotope ratio. This indicates optically thick emission from the main isotopologues in the inner disk or an enhanced isotope abundance. In the outer ring at 220 au N(CS)$\approx$N()$\times$22 which indicates optically thin CS emission if the S isotope ratio is indeed the local interstellar value. The / ratio is $\approx2\pm$2 in this outer ring. For the inner disk we use the optically thin and with $\times$22 we find a / ratio of 1$\pm$0.5 in the inner ring. For / using the results in a column density ratio of $\approx$2.0$\pm$1.0 in the inner disk.

- For the larger organics , and in the inner disk the lines appear to be optically thin but may be beam diluted. The peak column density ratios in the inner disk for / is $18\pm4$ and for / is 0.7$\pm$0.2 at 100 K for the inner disk. In the outer ring / is $1.1\pm0.6$ at both 30 and 50 K.

![](HD100546_radial_column_densities.png)

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Inner Peak | N(X)/N(CO) | Outer Ring Peak | N(X)/N(CO) | N(X)/N(CO) |
|  | (au) | $T_{ex}$=100 K | (au) | $T_{ex}$=30 K | $T_{ex}$=50 K |
|  | 5.5$\pm$19 | $2.2\pm0.3\times10^{-8}$ | 203.5$\pm$19 | $4.8\pm0.5\times10^{-7}$ | $3.9\pm0.4\times10^{-7}$ |
|  | 38.5$\pm$19 | $3.8\pm0.3\times10^{-8}$ | 214.5$\pm$19 | $6.0\pm0.8\times10^{-7}$ | $5.1\pm0.7\times10^{-7}$ |
|  | 38.5$\pm$21 | $1.6\pm0.2\times10^{-8}$ | 225.0$\pm$21 | $1.1\pm0.2\times10^{-6}$ | $1.1\pm0.2\times10^{-6}$ |
|  | 5.5$\pm$26 | $2.3\pm0.7\times10^{-7}$ | 181.0$\pm$26 | $3.0\pm2.0\times10^{-6}$ | $3.0\pm2.0\times10^{-6}$ |
|  | 38.5$\pm$20 | $6.0\pm1.0\times10^{-8}$ | 214.5$\pm$20 | $5.0\pm1.0\times10^{-6}$ | $5.0\pm1.0\times10^{-6}$ |
|  | 49.5$\pm$19 | $3.4\pm0.4\times10^{-8}$ | 214.5$\pm$19 | $1.3\pm0.3\times10^{-6}$ | $9.0\pm2.0\times10^{-7}$ |
|  | 5.5$\pm$20 | $5.2\pm0.7\times10^{-7}$ | 214.5$\pm$20 | $3.0\pm3.0\times10^{-7}$ | $6.0\pm5.0\times10^{-7}$ |
|  | 38.5$\pm$21 | $6.0\pm1.0\times10^{-8}$ | 214.5$\pm$21 | $6.0\pm5.0\times10^{-7}$ | $3.0\pm3.0\times10^{-7}$ |
|  | 5.5$\pm$20 | $1.0\pm0.2\times10^{-7}$ | 203.5$\pm$20 | $3.2\pm0.4\times10^{-6}$ | $3.2\pm0.4\times10^{-6}$ |
|  | 5.5$\pm$19 | $1.8\pm0.3\times10^{-6}$ | 214.5$\pm$19 | $4.0\pm2.0\times10^{-6}$ | $4.0\pm2.0\times10^{-6}$ |

# Discussion

In this section we discuss the potential physical and/or chemical origins of the molecular sub-structures detected in the HD 100546 disk and compare this disk to other chemically well-characterized Herbig Ae disks.

## The origin of the ringed molecular sub-structures in HD 100546

The HD 100546 disk shows clear rings in all of the molecules detected aside from CO and the locations of these rings all correlate with the radii of the mm-dust rings. This is the first time such a clear connection between dust and molecular rings has been in the outer regions of a disk. The most straightforward explanation for this coincidence would be the presence of a $\approx$100 au wide and deep gas gap that has shaped the larger millimetre-sized dust. The hydrodynamical models of planet-disk interactions presented in (cite: 2021A&A...651A..90F) that reproduce the mm-dust emission estimate approximately an order of magnitude drop in gas column density within the outer dust gap. Although there is a shelf of emission a clear gap is column density not immediately apparent. This is in contrast to other systems with 10’s of au wide dust gaps where corresponding CO gas gaps have been detected (cite: 2019ApJ...871..107F; 2022MNRAS.517.5942G).

Molecular rings can also arise in disks due to the disk chemistry rather than the disk’s physical structure. The cyanides CN and HCN are expected to be ringed due to the interaction of the disk surface layer with the stellar UV radiation (cite: 2018A&A...609A..93C; 2018A&A...615A..75V). is also expected have a central depression where is abundant in the gas-phase (cite: 2021A&A...646A...3L) but interestingly, in HD 100546 we find centrally peaked emission from within the gas cavity. (cite: 2022A&A...665A..45P) model the lines detected/not-detected in the HD 100546 disk with *Herschel* and suggest that the in the central cavity has been photo-dissociated to form OH, therefore, this could allow for to be present. Finally, the hydrocarbon is proposed to be abundant at the edge of the pebble disk and in the dust gaps (cite: 2021ApJ...910....3B). These chemical rings are not all expected to arise at the same radial location as each other as seen in the data.

The molecular rings we detect could also be shaped by radial variations in the disk gas-phase C/O. This would require an elevated C/O at the dust rings where the is bright and a C/O$<$1 within the central dust cavity and in the outer gap. Cold vapour has been detected within this outer gap region $\approx$40-150 au (cite: 2021A&A...648A..24V; 2022A&A...665A..45P) and the detection of within the central cavity would be consistent with this. This interpretation also fits with the central compact SO located inside a ring of CS where the switch between dominant gas-phase S-carrier occurs across the snowline. This is because, if the SO and CS are forming via gas-phase reactions their relative abundances will reflect the underlying C/O (cite: 2020A&A...638A.110F). It is not quite as simple as this though since SO, NO, and are detected in the dust outer ring as well as the , CS and CN. There are some radial offsets in the peak locations of these outer rings, as shown in Figures [4](#fig:radial_scatter) and [6](#fig:hd100546_azimuth) and that along with the apparent flat nature of the emission can be investigated with disk chemical models. There is likely also a contribution of molecular column density to the outer ring from non-thermal desorption, particularly evident from the detection of at $\approx$200 au and the cold from *Herschel*. The physical and chemical origin of these rings will be investigated further with grids of thermochemical models in Leemker et al. (2023, in prep) and the radial variation in / and contribution from non-thermal desorption mechanisms will be investigated in Evans et al. (2023, in prep).

## The origin of the asymmetric molecular sub-structures in HD 100546

The molecular emission maps in Figure [2](#fig:mom01) also show azimuthal asymmetries on large scales as highlighted most clearly in Figure [6](#fig:hd100546_azimuth). There is a drop in emission for all of the well-detected molecules in both the East and West of the disk that is also seen in the continuum emission. The azimuthal asymmetries in the outer rings could be due to azimuthal variation in temperature, but the lack of clear signature in the optically thick does not support this. Alternatively, the asymmetry could be the result of varying incident UV radiation due to self-shadowing from the mm-dust ring at 20 au, but this warrants further investigation (cite: 2010A&A...519A.110P; 2017A&A...607A.114W; 2021MNRAS.505.4821Y; 2023NatAs...7..684K). (cite: 2021A&A...651A..90F), who have higher angular resolution continuum observations than are presented here, show that the outer dust ring is clumpy and eccentric. Our line observations appear to trace this sub-structure but $\approx$0.1" line data are needed to understand the connection between the gas and the large dust in the disk midplane. All and all, this could point to an azimuthal variation in molecular column density that is following the dust.

On smaller, $<$1" scales, we recover the SO spatial asymmetry presented by (cite: Booth2023). The SO (and ) are brightest in the south of the disk where excess CO ro-vibrational emission was detected with VLT/CRIRES and where a disk-feature was detected in scattered light ((cite: 2019ApJ...883...37B; 2015ApJ...814L..27C); see Figure [7](#fig:hd100546_sulphur)). Additionally, the two new SO lines detected show the same asymmetric line profile as the two lines from (cite: Booth2023). The lower signal-to-noise emission does not show a clear asymmetry in the integrated intensity maps but the emission in the channel maps appears to be brightest in the south of the disk. Further, high-angular resolution, observations particularly of shock-tracing species such as SiO should help elucidate the nature of this emission and if it is indeed related to a forming giant planet (cite: 2023arXiv230613710L).

## In context with other Herbig Ae disks

Here we compare the HD 100546 disk to the HD 163296 and MWC 480 disks which were both observed in the ALMA Large Program MAPS (cite: 2021ApJS..257....1O). We also include some comparisons to the asymmetric transition disk HD 142527 (cite: 2023A&A...675A.131T) and the ringed transition disk HD 169142 (cite: Booth2023) where applicable. There are also now some efforts to survey the chemistry in Herbig Ae disks, but we do not cover the same molecules/transitions as these works (cite: 2022MNRAS.510.1148S; 2023arXiv230302167P). We will therefore mainly focus on the above individual disks where column densities have been calculated and the observations are spatially resolved.

![](HD100546_MAPS_column_density_comparison.png)

### Disk physical structure

The dust masses, gas masses and the gas disk sizes of the HD 100546, HD 163296 and MWC 480 disks are all similar (cite: 2021ApJS..257...14S; 2021ApJS..257....5Z; 2021ApJS..257...17C; 2021ApJS..257....3L). One notable difference in physical structure between these three disks is that the HD 100546 disk is warmer with no evidence for significant CO freeze-out (cite: 2016A&A...592A..83K). In comparison, the HD 163296 and MWC 480 disks each have a midplane CO snowline at 65 and 100 au, respectively, where beyond this radius gas-phase CO is depleted by $\approx$10$\times$. This temperature difference may be due to the large central cavity in the HD 100546 disk resulting in a warmer midplane throughout the disk. Figure [9](#fig:comparison) shows the CO column density in the HD 100546 disk determined from derived under the assumption of ISM isotope ratios compared to that for HD 163296 and MWC 480 from (cite: 2021ApJS..257....5Z). In the outer disk, at the location of the HD 100546 second dust ring, the CO column density is $\approx3\times$ higher in HD 100546 compared to the other two disks at the same radii. This is likely due to less efficient CO depletion in this warmer disk (cite: 2018A&A...618A.182B). The actual CO column could be higher by an additional factor of $\approx3$ if the abundance is underestimated due to isotope-selective photo-dissociation (cite: 2016A&A...594A..85M). So although these disks have a similar mass and size there is significantly more gas-phase CO available in the HD 100546 disk particularly at the location of the observed chemical rings in the outer disk.

### Ionization

The primary tracer of ionization in disks in the warm molecular layer is the cation . forms via the reaction of CO with which forms via the ionization of . The main destruction routes of are dissociative recombination with an electron or a charge transfer reaction with (cite: 2021A&A...646A...3L). The radial column density in the HD 100546 disk compared to HD 163296 and MWC 480 is shown in Figure [9](#fig:comparison) where the data for the other two disks are taken from (cite: 2021ApJS..257...13A). Overall, the column density is generally lower in HD 100546 disk by a factor of $\approx$10. The ratio / can be used as a proxy for the degree of ionization in the disk and (cite: 2021ApJS..257...13A) found that for HD 163296 and MWC 480 this value ranges from $\approx10^{-5}$ to $\approx10^{-4}$ and $\approx10^{-6}$ to $\approx10^{-5}$ from 100 to 400 au for each of these two disks respectively which is broadly in agreement with X-ray ionization disk chemical models. In HD 100546, we find that at $\approx$200 au (where and are optically thin) this is at least an order of magnitude lower - $3-5\times10^{-7}$ (see Table 2). This lower value is similar to the HD 142527 disk where N()/N(CO) are $\approx2\times10^{-7}$ (cite: 2023A&A...675A.131T). The primary sources of ionisation in disks are stellar X-rays in the warm molecular layer and cosmic rays and short-lived radionuclides (SLRs) in the disk midplane. The X-ray luminosity of HD 100546 is a factor of 2-5$\times$ lower than that of HD 163296 and MWC 480 (cite: 2019A&A...625A..66D). There is currently no evidence to suggest differences in the cosmic ray ionisation rates or SLRs abundances between these three sources; hence, the difference in stellar X-ray properties could account for the different abundances but is likely not the whole story. In addition to a lower ionization rate, as an alternative scenario, the presence of gas-phase water could also reduce the abundance (cite: 2018A&A...613A..29V; 2021A&A...646A...3L; 2021A&A...650A.180N). HD 100546 is one of the only disks that has a detection of gas with *Herschel* (cite: 2021A&A...648A..24V; 2022A&A...665A..45P) and water ice in the surface layers (cite: 2016ApJ...821....2H).

### UV field

The column density ratio of CN to HCN has been long suggested as a probe of the strength of the UV field impinging onto protoplanetary disks (cite: 2012A&A...537A..60C). Due to different photo-dissociation cross sections of CN and HCN, CN is predicted to survive in less dense and more UV irradiated regions therefore in a higher vertical layer in protoplanetary disks than HCN (cite: 2018A&A...616A..19A). (cite: 2021ApJS..257...11B) use high angular resolution observations of HCN and CN to explore photochemistry across the HD 163296 and MWC 480 disks. They find that N(CN)/N(HCN) increases as a function of radius and the value of this ratio is always $>$10. The resulting HCN and CN column density profiles from (cite: 2021ApJS..257...11B) are shown in Figure [9](#fig:comparison) along with our values for HD 100546. It is immediately apparent that CN is under-abundant across the whole of the HD 100546 disk compared to the others by more than an order of magnitude. The CN abundance in disks has been shown to be sensitive to the UV field and the degree of flaring in the protoplanetary disk (cite: 2018A&A...609A..93C). All three stars have similar UV luminosities but HD 100546 is slightly brighter, and this would be predicted to give a higher CN abundance. Therefore, it could be that the disk structure is responsible for the differences in CN abundance (cite: 2012A&A...544A..78M). The CN and HCN in the HD 163296 disk have been shown to originate from a layer in the disk at Z/R$\approx$0.2 but for MWC 480 this these molecules are emitting from Z/R$<$0.1 (cite: 2021ApJS..257....4L; 2023A&A...669A.126P).

Our analysis in Figure [5](#fig:ellipses) indicates these species come from close to the midplane in the HD 100546 disk with Z/R$<$0.1. Therefore, a molecular layer closer to the midplane due to a shallow disk and/or a higher UV flux pushing the molecular later deeper into the disk could explain the lack of CN in the HD 100546. In comparison, in the inner disk the HCN column density is significantly lower than the two other disks but the HCN in the HD 100546 outer ring is within a factor of a few. The lack of HCN (and CN) in the inner disk is at least partly due to the $\approx$15 au gas cavity in HD 100546 which is not present in the other two disks. Overall we find that N(CN)/N(HCN) over the HD 100546 disk ranges from $10^{-1}$ to 10 from 10 to 350 au which is different to the other disks observed so far but is broadly consistent with the thermochemical models from (cite: 2014ApJ...797..113S) which have no volatile depletion of C and O.

### C/O

Individual molecules such as and pairs of molecules, e.g., CS/SO and CN/NO, can be used to unravel the underlying elemental C/O in disk gas (cite: 2018A&A...617A..28S; 2019A&A...631A..69M; 2019ApJ...886...86L). In the HD 163296 and MWC 480 disks there is evidence for an elevated C/O of $\approx$2 in the disk warm molecular layer traced by (cite: 2021ApJS..257....7B). As shown in Figure [9](#fig:comparison), is abundant out to $\approx$150 au in these disks. In the HD 100546 disk, the peak column density is $\approx100\times$ lower that of HD 163296 and MWC 480. This difference can attributed to the lack of CO freeze-out and volatile depletion in HD 100546 compared to these other two disks despite the extreme dust evolution. (cite: 2016A&A...592A..83K) show that the C/H and O/H in HD 100546 are consistent with interstellar abundances and are at most modestly depleted $<10\times$. Whereas, the models from (cite: 2021ApJS..257....7B) require a depletion of C/H of 4-10$\times$ and O/H 20-50$\times$ to reproduce the high column densities observed towards HD 163196 and MWC 480. The second ring of in HD 100546 peaks just beyond the second dust ring and, as proposed by (cite: 2021ApJ...910....3B), may trace gas with a specific balance between UV irradiation and density that favours the formation of . Interestingly though, the is not bright within the dust gap as proposed by (cite: 2021ApJ...910....3B).

In comparison, the CS column density in HD 100546 is within a factor of a few compared to MWC 480 (cite: 2021ApJS..257...12L). This may indicate that the elevated C/O traced by in the MAPS disks is not necessarily traced by the CS. One mechanism to enhance the volatile carbon in the surface layers of protoplanetary disk is via the destruction of refractory carbon (cite: 2017ApJ...845...13A; 2021ApJ...910....3B). CS is predicted to come from a lower layer in the disk than (cite: 2018A&A...616A..19A) therefore if this is a process occurring in the higher disk layers it might not be traced as effectively with CS. But, the CS abundance is limited by the volatile sulphur abundance which is significantly lower than that of carbon. We do though see clear evidence for radial C/O variations in the HD 100546 disk traced by the SO and CS where SO is abundant in the cavity (see Figure [7](#fig:hd100546_sulphur)) as also reported for HD 169142 (cite: Booth2023). Our SO peak column density in HD 100546 is $\approx100\times$ higher than the disk-averaged upper-limit in the MAPS Herbig disks of $<3\times10^{12}$ cm$^{-2}$. The weak SO emission in the outer disk of HD 100546 has a column density of $\approx3\times10^{12}$ cm$^{-2}$ so if this reservoir of cold SO is present in HD 163296 and MWC 480 it may just be below the detection limit of the MAPS data.

In HD 100546, NO is the nitrogen-bearing molecule with the highest column density we have detected. NO is not typically targeted in disk observations but, the high NO/CN and overall low CN abundance in HD 100546 disk may also be related to the lack of volatile depletion (cite: 2019ApJ...886...86L; 2023arXiv230300768L). Across the HD 100546 disk the N(CN)/N(NO) varies from $10^{-1}$ to 1. Detailed thermochemical modelling from Leemker et al. (2023, in prep) will determine more quantitative constraints on the C/O ratio across the HD 100546 to better place it in context with other Class II disks.

### Large organics

The organic molecule is ubiquitous in protoplanetary disks (cite: 2020ApJ...890..142P). The detected in disks can form in the gas phase via neutral-neutral reactions, e.g., + O, or on the surfaces of icy dust grains via CO ice hydrogenation (cite: 2002ApJ...571L.173W; 2015ApJ...809L..25L). is detected in HD 100546 with a similar column density across the disk to HD 163296 and MWC 480, as shown in Figure [9](#fig:comparison), despite the lack of significant CO freeze-out in HD 100546 (as also seen for HD 169142; (cite: Booth2023)). This could hint at the gas-phase formation of rather an CO ice hydrogenation as being the dominant in-situ source of in these disks, but if these disks begin their evolution with inherited rich ices then is likely also present on the grains in these disks regardless of the freeze-out of CO.

Since and have a common formation pathway on grain surfaces via CO ice (cite: 2002ApJ...571L.173W; 2009A&A...505..629F; 2022ApJ...931L..33S) the former has been proposed as a tracer of the underlying complexity in disks. Unfortunately, the general lack of in -rich sources shows that is not that simple. In HD 100546 we find a peak abundance ratio of / of $18\pm4$ in the inner disk at 100 K and $1.1\pm0.6$ in the outer disk at 30 K. This is a few times lower than the HD 169142 / ratio of 100 of the inner disk and the upper-limit of $\approx$3 for the outer disk (cite: Booth2023). In HD 163296 and MWC 480 the upper limits on the disk averaged column densities are $<2\times10^{12}$ and $<8\times10^{12}$ cm$^{-2}$ so if the same reservoir of, particularly warm thermally desorbed, was present in these sources it should have been detected. The lack of COMs emission could be attributed to disk structure instead of disk chemistry. In HD 100546 the COMs can desorb at the edge of the millimetre dust cavity where as the millimetre dust is optically thick within the snowline locations in HD 163296 and MWC 480 disks (cite: 2021ApJS..257....5Z; 2021ApJS..257...14S). We also detect in HD 100546 at a high relative abundance to . This larger molecule is also present in IRS 48 but, unlike in the IRS 48 disk (cite: 2022A&A...659A..29B), another COM is not detected in HD 100546 with a / column density ratio $>$7. A more detailed discussion on the COMs reservoir in the HD 100546 disk will follow in (cite: Booth2023_irs48) and Evans et al. (in prep.).

The sulphur-bearing equivalent of , , is detected in HD 100546 and follows the CS (also found for MWC 480 and HD 169142; (cite: 2019ApJ...876...72L; 2021ApJS..257...12L; Booth2023)) and not the sublimating SO in the inner disk. This indicates that the is likely forming in the gas phase rather than having a significant abundance on the grains. The column density ratio observed towards HD 100546 is within a factor of a few of that measured in the other two Herbig disks, HD 169142 and MWC 480. OCS is not detected in our data and we place an upper-limit on the column density of $<$10$^{12}$ cm$\mathrm{^{-2}}$ at 100 K, which corresponds to $<$1% of the SO column density and thus we can conclude that OCS not a significant source of gaseous volatile sulphur in this disk.

We do not detect , or in our observations of the HD 100546 disk but the lines covered do have higher upper energy levels than those targeted in MAPS (cite: 2021ApJS..257....9I). Using the upper limits on the disk-integrated fluxes (from Table [1](#tab:A3)) we calculate disk-integrated column density upper limits at 50 K within a radius of 100 au. This results in a column density $<$2$\times$10$^{13}$  cm$\mathrm{^{-2}}$ for , $<$1$\times$10$^{14}$ cm$\mathrm{^{-2}}$ for and $<$6$\times$10$^{12}$ cm$\mathrm{^{-2}}$ for . Compared to (cite: 2021ApJS..257....9I) these upper limits are not sensitive enough compared to the and column densities to detect the same level of complexity as seen in the HD 163296 and MWC 480 disks. Additionally, the abundance of these species is expected to be enhanced in high C/O environments therefore, we might expect them to be less abundant in HD 100546 relative to HCN and (cite: 2023NatAs...7...49C). The lack of these species could also indicate that the small grains within the dust cavity are not hot enough to trigger carbon grain sublimation which would result in the in-situ gas-phase formation of of hydrocarbons and nitriles (cite: 2020ApJ...897L..38V).

# Conclusion

This paper presents an ALMA molecular line survey towards the disk around the Herbig Ae star HD 100546. We detect 19 different molecular species and our main results are as follows:

- This work reports the first detections of and in protoplanetary disks. We also robustly detect along with and showing that these molecules are detectable in Class II disks.

- The molecular emission from the HD 100546 disk shows clear radial sub-structures that peak just beyond the the outer millimetre dust ring at $\approx$200 au and these emission rings appear to be flat. This spatial coincidence is in contrast with what is generally seen in other sources. A similarly clear gap is not seen in the CO isotopologues indicating that a deep gas () gap cannot solely explain the presence of these molecular rings.

- There is a consistent azimuthal brightness asymmetry in the outer HD 100546 molecular rings that is most prominent in the radicals , CN and CS. This could be due to shadowing from the inner dust disk leading to an azimuthal temperature gradient and/or varying incident UV irradiation. There is also asymmetric SO emission originating from within the central dust cavity which may be linked to ongoing giant planet formation, as proposed in (cite: 2023A&A...669A..53B).

- The fractional abundance of relative to CO in HD 100546 is $\approx10^{-7}$. This is 1-3 orders of magnitude lower than the ranges reported for the other Herbig Ae disks HD 163296 and MWC 480, but is consistent with the HD 142527 disk. This may be explained by a different ionization structure in transition and non-transitional disks. The presence of gas-phase in the HD 100546 disk will also contribute to the lack of .

- The low CN abundance relative to CO and HCN in the HD 100546 disk is unique when compared to other sources. The stellar UV flux from HD 100546 is similar to that of HD 163296 and MWC 480 but the CN is $\approx10-100\times$ less abundant across the disk. If the CN emitting layer in HD 100546 is close to the midplane due to a flat or self-shadowed disk, as supported by the morphology of the outer ring, the CN abundance could be expected to be low. Chemical modelling is needed to test this hypothesis.

- We detect multiple species that can be used to trace the underlying C/O ratio in the disk gas. The / clearly trace the transition over the snowline in the inner disk. The column density is $\times$100 lower than other Herbig disks of a similar mass indicating less oxygen depletion in this system and suggesting a low C/O. The , and have similar radial emission profiles and could trace rings in the disk where C/O$\approx$1. The relationship between CN and NO, the SO and CS, and the in the outer ring in the context of radial C/O variations requires further investigation.

- Both and are detected in the HD 100546 disk indicating a hot corino/core-like chemistry may be active in the inner region of disks. In comparison to other disks, , and are all undetected in our data but, this can primarily be attributed to sensitivity limits of the data.

The chemical diversity and richness of the spectra we present here motivate the need for more uniform surveys of protoplanetary disks around Herbig Ae stars. These class of disks are typically larger and brighter than T-Tauri disks and the sublimation of ices in these disks makes them excellent observational laboratories to unravel disk chemistry at the time of planet formation. It is particularly important to understand the ongoing chemistry in these disks as they are the precursors to the star, debris disk and giant-planet systems like HR 8799 and Beta Pictoris (cite: 2008Sci...322.1348M; 2009A&A...493L..21L).

# Acknowledgements

This paper makes use of the following ALMA data: 2021.1.00738S. We acknowledge assistance from Allegro, the European ALMA Regional Centre node in the Netherlands. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work has used the following additional software packages that have not been referred to in the main text: Astropy, IPython, Jupyter, Matplotlib and NumPy (cite: Astropy; IPython; Jupyter; Matplotlib; NumPy). Astrochemistry in Leiden is supported by funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 101019751 MOLDISK). A.S.B. is supported by a Clay Postdoctoral Fellowship from the Smithsonian Astrophysical Observatory. M.L. acknowledges support from grant 618.000.001 from the Dutch Research Council (NWO). J.I.D. acknowledges support from an STFC Ernest Rutherford Fellowship (ST/W004119/1) and a University Academic Fellowship from the University of Leeds. M.T. acknowledges support from the ERC grant 101019751 MOLDISK. C.W. acknowledges financial support from the University of Leeds, the Science and Technology Facilities Council, and UK Research and Innovation (grant numbers ST/X001016/1 and MR/T040726/1). L.E. acknowledges financial support from the Science and Technology Facilities Council (grant number ST/T000287/1). S.N. is grateful for support from RIKEN Special Postdoctoral Researcher Program (Fellowships), Grants-in-Aid for JSPS (Japan Society for the Promotion of Science) Fellows Grant Number JP23KJ0329, and MEXT/JSPS Grants-in-Aid for Scientific Research (KAKENHI) Grant Numbers JP 18H05441, JP20K22376, JP20H05845, JP20H05847, JP23K13155, and JP23H05441. Support for C.J.L. was provided by NASA through the NASA Hubble Fellowship grant No. HST-HF2-51535.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555.

natexlab

(ref: 2018A&A...616A..19A) Agúndez, M., Roueff, E., Le Petit, F., & Le Bourlot, J. 2018, A&A, 616, A19, doi: [`10.1051/0004-6361/201732518`](http://doi.org/10.1051/0004-6361/201732518)

(ref: 2021ApJS..257...13A) Aikawa, Y., Cataldi, G., Yamato, Y., et al. 2021, ApJS, 257, 13, doi: [`10.3847/1538-4365/ac143c`](http://doi.org/10.3847/1538-4365/ac143c)

(ref: 2017ApJ...845...13A) Anderson, D. E., Bergin, E. A., Blake, G. A., et al. 2017, ApJ, 845, 13, doi: [`10.3847/1538-4357/aa7da1`](http://doi.org/10.3847/1538-4357/aa7da1)

(ref: Andrews2018dsharp) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: Astropy) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: 2022ApJ...934L..20B) Bae, J., Teague, R., Andrews, S. M., et al. 2022, ApJL, 934, L20, doi: [`10.3847/2041-8213/ac7fa3`](http://doi.org/10.3847/2041-8213/ac7fa3)

(ref: 2021ApJS..257...11B) Bergner, J. B., Öberg, K. I., Guzmán, V. V., et al. 2021, ApJS, 257, 11, doi: [`10.3847/1538-4365/ac143a`](http://doi.org/10.3847/1538-4365/ac143a)

(ref: Booth2023_irs48) Booth, A., Temmink, M., & et al. 2024, submitted AJ

(ref: 2023A&A...669A..53B) Booth, A. S., Ilee, J. D., Walsh, C., et al. 2023a, A&A, 669, A53, doi: [`10.1051/0004-6361/202244472`](http://doi.org/10.1051/0004-6361/202244472)

(ref: Booth2023) Booth, A. S., Law, C. J., Temmink, M., Leemker, M., & Macias, E. 2023b, arXiv e-prints, arXiv:2308.07910, doi: [`10.48550/arXiv.2308.07910`](http://doi.org/10.48550/arXiv.2308.07910)

(ref: 2021A&A...651L...6B) Booth, A. S., van der Marel, N., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021a, A&A, 651, L6, doi: [`10.1051/0004-6361/202141057`](http://doi.org/10.1051/0004-6361/202141057)

(ref: 2018A&A...611A..16B) Booth, A. S., Walsh, C., Kama, M., et al. 2018, A&A, 611, A16, doi: [`10.1051/0004-6361/201731347`](http://doi.org/10.1051/0004-6361/201731347)

(ref: 2021NatAs...5..684B) Booth, A. S., Walsh, C., Terwisscha van Scheltinga, J., et al. 2021b, Nature Astronomy, 5, 684, doi: [`10.1038/s41550-021-01352-w`](http://doi.org/10.1038/s41550-021-01352-w)

(ref: 2021ApJ...910....3B) Bosman, A. D., Alarcón, F., Zhang, K., & Bergin, E. A. 2021a, ApJ, 910, 3, doi: [`10.3847/1538-4357/abe127`](http://doi.org/10.3847/1538-4357/abe127)

(ref: 2018A&A...618A.182B) Bosman, A. D., Walsh, C., & van Dishoeck, E. F. 2018, A&A, 618, A182, doi: [`10.1051/0004-6361/201833497`](http://doi.org/10.1051/0004-6361/201833497)

(ref: 2021ApJS..257....7B) Bosman, A. D., Alarcón, F., Bergin, E. A., et al. 2021b, ApJS, 257, 7, doi: [`10.3847/1538-4365/ac1435`](http://doi.org/10.3847/1538-4365/ac1435)

(ref: 2019ApJ...883...37B) Brittain, S. D., Najita, J. R., & Carr, J. S. 2019, ApJ, 883, 37, doi: [`10.3847/1538-4357/ab380b`](http://doi.org/10.3847/1538-4357/ab380b)

(ref: 2022A&A...659A..29B) Brunken, N. G. C., Booth, A. S., Leemker, M., et al. 2022, A&A, 659, A29, doi: [`10.1051/0004-6361/202142981`](http://doi.org/10.1051/0004-6361/202142981)

(ref: 2021ApJS..257...17C) Calahan, J. K., Bergin, E. A., Zhang, K., et al. 2021, ApJS, 257, 17, doi: [`10.3847/1538-4365/ac143f`](http://doi.org/10.3847/1538-4365/ac143f)

(ref: 2023NatAs...7...49C) Calahan, J. K., Bergin, E. A., Bosman, A. D., et al. 2023, Nature Astronomy, 7, 49, doi: [`10.1038/s41550-022-01831-8`](http://doi.org/10.1038/s41550-022-01831-8)

(ref: 2018A&A...609A..93C) Cazzoletti, P., van Dishoeck, E. F., Visser, R., Facchini, S., & Bruderer, S. 2018, A&A, 609, A93, doi: [`10.1051/0004-6361/201731457`](http://doi.org/10.1051/0004-6361/201731457)

(ref: 2012A&A...537A..60C) Chapillon, E., Guilloteau, S., Dutrey, A., Piétu, V., & Guélin, M. 2012, A&A, 537, A60, doi: [`10.1051/0004-6361/201116762`](http://doi.org/10.1051/0004-6361/201116762)

(ref: 2022arXiv220505696C) Currie, T., Biller, B., Lagrange, A.-M., et al. 2022, arXiv e-prints, arXiv:2205.05696. [`https://arxiv.org/abs/2205.05696`](https://arxiv.org/abs/2205.05696)

(ref: 2015ApJ...814L..27C) Currie, T., Cloutier, R., Brittain, S., et al. 2015, ApJL, 814, L27, doi: [`10.1088/2041-8205/814/2/L27`](http://doi.org/10.1088/2041-8205/814/2/L27)

(ref: 2019A&A...625A..66D) Dionatos, O., Woitke, P., Güdel, M., et al. 2019, A&A, 625, A66, doi: [`10.1051/0004-6361/201832860`](http://doi.org/10.1051/0004-6361/201832860)

(ref: 2015ApJ...807L..32D) Du, F., Bergin, E. A., & Hogerheijde, M. R. 2015, ApJL, 807, L32, doi: [`10.1088/2041-8205/807/2/L32`](http://doi.org/10.1088/2041-8205/807/2/L32)

(ref: 2016JMoSp.327...95E) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95, doi: [`10.1016/j.jms.2016.03.005`](http://doi.org/10.1016/j.jms.2016.03.005)

(ref: 2021AJ....162...99F) Facchini, S., Teague, R., Bae, J., et al. 2021, AJ, 162, 99, doi: [`10.3847/1538-3881/abf0a4`](http://doi.org/10.3847/1538-3881/abf0a4)

(ref: 2019ApJ...871..107F) Favre, C., Fedele, D., Maud, L., et al. 2019, ApJ, 871, 107, doi: [`10.3847/1538-4357/aaf80c`](http://doi.org/10.3847/1538-4357/aaf80c)

(ref: 2020A&A...638A.110F) Fedele, D., & Favre, C. 2020, A&A, 638, A110, doi: [`10.1051/0004-6361/202037927`](http://doi.org/10.1051/0004-6361/202037927)

(ref: 2021A&A...651A..90F) Fedele, D., Toci, C., Maud, L., & Lodato, G. 2021, A&A, 651, A90, doi: [`10.1051/0004-6361/202141278`](http://doi.org/10.1051/0004-6361/202141278)

(ref: 2009A&A...505..629F) Fuchs, G. W., Cuppen, H. M., Ioppolo, S., et al. 2009, A&A, 505, 629, doi: [`10.1051/0004-6361/200810784`](http://doi.org/10.1051/0004-6361/200810784)

(ref: 2022ApJ...938...29F) Furuya, K., Lee, S., & Nomura, H. 2022, ApJ, 938, 29, doi: [`10.3847/1538-4357/ac9233`](http://doi.org/10.3847/1538-4357/ac9233)

(ref: 2022MNRAS.517.5942G) Garg, H., Pinte, C., Hammond, I., et al. 2022, MNRAS, 517, 5942, doi: [`10.1093/mnras/stac3039`](http://doi.org/10.1093/mnras/stac3039)

(ref: 2021ApJS..257....6G) Guzmán, V. V., Bergner, J. B., Law, C. J., et al. 2021, ApJS, 257, 6, doi: [`10.3847/1538-4365/ac1440`](http://doi.org/10.3847/1538-4365/ac1440)

(ref: 2021A&A...650A.182G) Guzmán-Dı́az, J., Mendigutı́a, I., Montesinos, B., et al. 2021, A&A, 650, A182, doi: [`10.1051/0004-6361/202039519`](http://doi.org/10.1051/0004-6361/202039519)

(ref: 2019NatAs...3..749H) Haffert, S. Y., Bohn, A. J., de Boer, J., et al. 2019, Nature Astronomy, 3, 749, doi: [`10.1038/s41550-019-0780-5`](http://doi.org/10.1038/s41550-019-0780-5)

(ref: 2023MNRAS.522L..51H) Hammond, I., Christiaens, V., Price, D. J., et al. 2023, MNRAS, 522, L51, doi: [`10.1093/mnrasl/slad027`](http://doi.org/10.1093/mnrasl/slad027)

(ref: NumPy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: 2016ApJ...821....2H) Honda, M., Kudo, T., Takatsuki, S., et al. 2016, ApJ, 821, 2, doi: [`10.3847/0004-637X/821/1/2`](http://doi.org/10.3847/0004-637X/821/1/2)

(ref: Matplotlib) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: 2021ApJS..257....9I) Ilee, J. D., Walsh, C., Booth, A. S., et al. 2021, ApJS, 257, 9, doi: [`10.3847/1538-4365/ac1441`](http://doi.org/10.3847/1538-4365/ac1441)

(ref: 2019ApJ...879L..25I) Isella, A., Benisty, M., Teague, R., et al. 2019, ApJL, 879, L25, doi: [`10.3847/2041-8213/ab2a12`](http://doi.org/10.3847/2041-8213/ab2a12)

(ref: 2022ApJ...928....2I) Izquierdo, A. F., Facchini, S., Rosotti, G. P., van Dishoeck, E. F., & Testi, L. 2022, ApJ, 928, 2, doi: [`10.3847/1538-4357/ac474d`](http://doi.org/10.3847/1538-4357/ac474d)

(ref: 2016A&A...592A..83K) Kama, M., Bruderer, S., van Dishoeck, E. F., et al. 2016a, A&A, 592, A83, doi: [`10.1051/0004-6361/201526991`](http://doi.org/10.1051/0004-6361/201526991)

(ref: Kama2016twhya) —. 2016b, A&A, 592, A83, doi: [`10.1051/0004-6361/201526991`](http://doi.org/10.1051/0004-6361/201526991)

(ref: 2018A&A...617A..44K) Keppler, M., Benisty, M., Müller, A., et al. 2018, A&A, 617, A44, doi: [`10.1051/0004-6361/201832957`](http://doi.org/10.1051/0004-6361/201832957)

(ref: 2023NatAs.tmp...92K) Keyte, L., Kama, M., Booth, A. S., et al. 2023a, Nature Astronomy, doi: [`10.1038/s41550-023-01951-9`](http://doi.org/10.1038/s41550-023-01951-9)

(ref: 2023NatAs...7..684K) —. 2023b, Nature Astronomy, 7, 684, doi: [`10.1038/s41550-023-01951-9`](http://doi.org/10.1038/s41550-023-01951-9)

(ref: Jupyter) Kluyver, T., Ragan-Kelley, B., Pérez, F., et al. 2016, in Positioning and Power in Academic Publishing: Players, Agents and Agendas, ed. F. Loizides & B. Schmidt, IOS Press, 87 – 90

(ref: 2020ApJ...899..134K) Krijt, S., Bosman, A. D., Zhang, K., et al. 2020, ApJ, 899, 134, doi: [`10.3847/1538-4357/aba75d`](http://doi.org/10.3847/1538-4357/aba75d)

(ref: 2009A&A...493L..21L) Lagrange, A. M., Gratadour, D., Chauvin, G., et al. 2009, A&A, 493, L21, doi: [`10.1051/0004-6361:200811325`](http://doi.org/10.1051/0004-6361:200811325)

(ref: 2023arXiv230613710L) Law, C. J., Booth, A. S., & Öberg, K. I. 2023, arXiv e-prints, arXiv:2306.13710, doi: [`10.48550/arXiv.2306.13710`](http://doi.org/10.48550/arXiv.2306.13710)

(ref: 2021ApJS..257....3L) Law, C. J., Loomis, R. A., Teague, R., et al. 2021a, ApJS, 257, 3, doi: [`10.3847/1538-4365/ac1434`](http://doi.org/10.3847/1538-4365/ac1434)

(ref: 2021ApJS..257....4L) Law, C. J., Teague, R., Loomis, R. A., et al. 2021b, ApJS, 257, 4, doi: [`10.3847/1538-4365/ac1439`](http://doi.org/10.3847/1538-4365/ac1439)

(ref: 2022ApJ...932..114L) Law, C. J., Crystian, S., Teague, R., et al. 2022, ApJ, 932, 114, doi: [`10.3847/1538-4357/ac6c02`](http://doi.org/10.3847/1538-4357/ac6c02)

(ref: 2019ApJ...886...86L) Le Gal, R., Brady, M. T., Öberg, K. I., Roueff, E., & Le Petit, F. 2019a, ApJ, 886, 86, doi: [`10.3847/1538-4357/ab4ad9`](http://doi.org/10.3847/1538-4357/ab4ad9)

(ref: 2019ApJ...876...72L) Le Gal, R., Öberg, K. I., Loomis, R. A., Pegues, J., & Bergner, J. B. 2019b, ApJ, 876, 72, doi: [`10.3847/1538-4357/ab1416`](http://doi.org/10.3847/1538-4357/ab1416)

(ref: 2021ApJS..257...12L) Le Gal, R., Öberg, K. I., Teague, R., et al. 2021, ApJS, 257, 12, doi: [`10.3847/1538-4365/ac2583`](http://doi.org/10.3847/1538-4365/ac2583)

(ref: 2023arXiv230300768L) Leemker, M., Booth, A. S., van Dishoeck, E. F., et al. 2023, arXiv e-prints, arXiv:2303.00768, doi: [`10.48550/arXiv.2303.00768`](http://doi.org/10.48550/arXiv.2303.00768)

(ref: 2021A&A...646A...3L) Leemker, M., van’t Hoff, M. L. R., Trapman, L., et al. 2021, A&A, 646, A3, doi: [`10.1051/0004-6361/202039387`](http://doi.org/10.1051/0004-6361/202039387)

(ref: 2022ApJ...937L...1L) Long, F., Andrews, S. M., Zhang, S., et al. 2022, ApJL, 937, L1, doi: [`10.3847/2041-8213/ac8b10`](http://doi.org/10.3847/2041-8213/ac8b10)

(ref: 2018ApJ...859..131L) Loomis, R. A., Cleeves, L. I., Öberg, K. I., et al. 2018a, ApJ, 859, 131, doi: [`10.3847/1538-4357/aac169`](http://doi.org/10.3847/1538-4357/aac169)

(ref: 2015ApJ...809L..25L) Loomis, R. A., Cleeves, L. I., Öberg, K. I., Guzman, V. V., & Andrews, S. M. 2015, ApJL, 809, L25, doi: [`10.1088/2041-8205/809/2/L25`](http://doi.org/10.1088/2041-8205/809/2/L25)

(ref: Loomis2018) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2018b, AJ, 155, 182, doi: [`10.3847/1538-3881/aab604`](http://doi.org/10.3847/1538-3881/aab604)

(ref: 2020ApJ...893..101L) —. 2020, ApJ, 893, 101, doi: [`10.3847/1538-4357/ab7cc8`](http://doi.org/10.3847/1538-4357/ab7cc8)

(ref: 2008Sci...322.1348M) Marois, C., Macintosh, B., Barman, T., et al. 2008, Science, 322, 1348, doi: [`10.1126/science.1166585`](http://doi.org/10.1126/science.1166585)

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2012A&A...544A..78M) Meeus, G., Montesinos, B., Mendigutı́a, I., et al. 2012, A&A, 544, A78, doi: [`10.1051/0004-6361/201219225`](http://doi.org/10.1051/0004-6361/201219225)

(ref: 2019MNRAS.485..739M) Miley, J. M., Panić, O., Haworth, T. J., et al. 2019, MNRAS, 485, 739, doi: [`10.1093/mnras/stz426`](http://doi.org/10.1093/mnras/stz426)

(ref: 2022arXiv220309818M) Miotello, A., Kamp, I., Birnstiel, T., Cleeves, L. I., & Kataoka, A. 2022, arXiv e-prints, arXiv:2203.09818, doi: [`10.48550/arXiv.2203.09818`](http://doi.org/10.48550/arXiv.2203.09818)

(ref: 2016A&A...594A..85M) Miotello, A., van Dishoeck, E. F., Kama, M., & Bruderer, S. 2016, A&A, 594, A85, doi: [`10.1051/0004-6361/201628159`](http://doi.org/10.1051/0004-6361/201628159)

(ref: 2019A&A...631A..69M) Miotello, A., Facchini, S., van Dishoeck, E. F., et al. 2019, A&A, 631, A69, doi: [`10.1051/0004-6361/201935441`](http://doi.org/10.1051/0004-6361/201935441)

(ref: 2021A&A...650A.180N) Notsu, S., van Dishoeck, E. F., Walsh, C., Bosman, A. D., & Nomura, H. 2021, A&A, 650, A180, doi: [`10.1051/0004-6361/202140667`](http://doi.org/10.1051/0004-6361/202140667)

(ref: 2021PhR...893....1O) Öberg, K. I., & Bergin, E. A. 2021, Phys. Rep., 893, 1, doi: [`10.1016/j.physrep.2020.09.004`](http://doi.org/10.1016/j.physrep.2020.09.004)

(ref: 2021ApJS..257....1O) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1, doi: [`10.3847/1538-4365/ac1432`](http://doi.org/10.3847/1538-4365/ac1432)

(ref: 2023A&A...669A.126P) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., et al. 2023, A&A, 669, A126, doi: [`10.1051/0004-6361/202244428`](http://doi.org/10.1051/0004-6361/202244428)

(ref: 2010A&A...519A.110P) Panić, O., van Dishoeck, E. F., Hogerheijde, M. R., et al. 2010, A&A, 519, A110, doi: [`10.1051/0004-6361/200913709`](http://doi.org/10.1051/0004-6361/200913709)

(ref: 2020ApJ...890..142P) Pegues, J., Öberg, K. I., Bergner, J. B., et al. 2020, ApJ, 890, 142, doi: [`10.3847/1538-4357/ab64d9`](http://doi.org/10.3847/1538-4357/ab64d9)

(ref: 2023arXiv230302167P) Pegues, J., Öberg, K. I., Qi, C., et al. 2023, arXiv e-prints, arXiv:2303.02167. [`https://arxiv.org/abs/2303.02167`](https://arxiv.org/abs/2303.02167)

(ref: IPython) Pérez, F., & Granger, B. E. 2007, Computing in Science and Engineering, 9, 21, doi: [`10.1109/MCSE.2007.53`](http://doi.org/10.1109/MCSE.2007.53)

(ref: 1998JQSRT..60..883P) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883, doi: [`10.1016/S0022-4073(98)00091-0`](http://doi.org/10.1016/S0022-4073(98)00091-0)

(ref: 2019ApJ...871...48P) Pineda, J. E., Szulágyi, J., Quanz, S. P., et al. 2019, ApJ, 871, 48, doi: [`10.3847/1538-4357/aaf389`](http://doi.org/10.3847/1538-4357/aaf389)

(ref: 2019NatAs...3.1109P) Pinte, C., van der Plas, G., Ménard, F., et al. 2019, Nature Astronomy, 3, 1109, doi: [`10.1038/s41550-019-0852-6`](http://doi.org/10.1038/s41550-019-0852-6)

(ref: 2022A&A...665A..45P) Pirovano, L. M., Fedele, D., van Dishoeck, E. F., et al. 2022, A&A, 665, A45, doi: [`10.1051/0004-6361/202244104`](http://doi.org/10.1051/0004-6361/202244104)

(ref: 2022ApJ...931L..33S) Santos, J. C., Chuang, K.-J., Lamberts, T., et al. 2022, ApJL, 931, L33, doi: [`10.3847/2041-8213/ac7158`](http://doi.org/10.3847/2041-8213/ac7158)

(ref: 2014ApJ...797..113S) Schwarz, K. R., & Bergin, E. A. 2014, ApJ, 797, 113, doi: [`10.1088/0004-637X/797/2/113`](http://doi.org/10.1088/0004-637X/797/2/113)

(ref: 2018ApJ...856...85S) Schwarz, K. R., Bergin, E. A., Cleeves, L. I., et al. 2018, ApJ, 856, 85, doi: [`10.3847/1538-4357/aaae08`](http://doi.org/10.3847/1538-4357/aaae08)

(ref: 2018A&A...617A..28S) Semenov, D., Favre, C., Fedele, D., et al. 2018, A&A, 617, A28, doi: [`10.1051/0004-6361/201832980`](http://doi.org/10.1051/0004-6361/201832980)

(ref: 2021ApJS..257...14S) Sierra, A., Pérez, L. M., Zhang, K., et al. 2021, ApJS, 257, 14, doi: [`10.3847/1538-4365/ac1431`](http://doi.org/10.3847/1538-4365/ac1431)

(ref: 2022MNRAS.510.1148S) Smirnov-Pinchukov, G. V., Moór, A., Semenov, D. A., et al. 2022, MNRAS, 510, 1148, doi: [`10.1093/mnras/stab3146`](http://doi.org/10.1093/mnras/stab3146)

(ref: 2023A&A...669A.158S) Stapper, L. M., Hogerheijde, M. R., van Dishoeck, E. F., & Paneque-Carreño, T. 2023, A&A, 669, A158, doi: [`10.1051/0004-6361/202245137`](http://doi.org/10.1051/0004-6361/202245137)

(ref: GoFish) Teague, R. 2019, The Journal of Open Source Software, 4, 1632, doi: [`10.21105/joss.01632`](http://doi.org/10.21105/joss.01632)

(ref: rich_teague_2020_4321137) —. 2020, richteague/keplerian_mask: Initial Release, 1.0, Zenodo, doi: [`10.5281/zenodo.4321137`](http://doi.org/10.5281/zenodo.4321137)

(ref: 2018ApJ...860L..12T) Teague, R., Bae, J., Bergin, E. A., Birnstiel, T., & Foreman-Mackey, D. 2018, ApJL, 860, L12, doi: [`10.3847/2041-8213/aac6d7`](http://doi.org/10.3847/2041-8213/aac6d7)

(ref: 2023A&A...675A.131T) Temmink, M., Booth, A. S., van der Marel, N., & van Dishoeck, E. F. 2023, A&A, 675, A131, doi: [`10.1051/0004-6361/202346272`](http://doi.org/10.1051/0004-6361/202346272)

(ref: 2004A&A...425..955T) Thi, W. F., van Zadelhoff, G. J., & van Dishoeck, E. F. 2004, A&A, 425, 955, doi: [`10.1051/0004-6361:200400026`](http://doi.org/10.1051/0004-6361:200400026)

(ref: 2021A&A...651L...5V) van der Marel, N., Booth, A. S., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021, A&A, 651, L5, doi: [`10.1051/0004-6361/202141051`](http://doi.org/10.1051/0004-6361/202141051)

(ref: 2021A&A...648A..24V) van Dishoeck, E. F., Kristensen, L. E., Mottram, J. C., et al. 2021, A&A, 648, A24, doi: [`10.1051/0004-6361/202039084`](http://doi.org/10.1051/0004-6361/202039084)

(ref: 2020ApJ...897L..38V) van ’t Hoff, M. L. R., Bergin, E. A., Jørgensen, J. K., & Blake, G. A. 2020, ApJL, 897, L38, doi: [`10.3847/2041-8213/ab9f97`](http://doi.org/10.3847/2041-8213/ab9f97)

(ref: 2018A&A...613A..29V) van ’t Hoff, M. L. R., Persson, M. V., Harsono, D., et al. 2018, A&A, 613, A29, doi: [`10.1051/0004-6361/201731656`](http://doi.org/10.1051/0004-6361/201731656)

(ref: 2018A&A...620A.128V) Vioque, M., Oudmaijer, R. D., Baines, D., Mendigutı́a, I., & Pérez-Martı́nez, R. 2018, A&A, 620, A128, doi: [`10.1051/0004-6361/201832870`](http://doi.org/10.1051/0004-6361/201832870)

(ref: 2018A&A...615A..75V) Visser, R., Bruderer, S., Cazzoletti, P., et al. 2018, A&A, 615, A75, doi: [`10.1051/0004-6361/201731898`](http://doi.org/10.1051/0004-6361/201731898)

(ref: 2023NatAs...7.1208W) Wagner, K., Stone, J., Skemer, A., et al. 2023, Nature Astronomy, 7, 1208, doi: [`10.1038/s41550-023-02028-3`](http://doi.org/10.1038/s41550-023-02028-3)

(ref: 2017A&A...607A.114W) Walsh, C., Daley, C., Facchini, S., & Juhász, A. 2017, A&A, 607, A114, doi: [`10.1051/0004-6361/201731334`](http://doi.org/10.1051/0004-6361/201731334)

(ref: 2015A&A...582A..88W) Walsh, C., Nomura, H., & van Dishoeck, E. 2015, A&A, 582, A88, doi: [`10.1051/0004-6361/201526751`](http://doi.org/10.1051/0004-6361/201526751)

(ref: 2014ApJ...791L...6W) Walsh, C., Juhász, A., Pinilla, P., et al. 2014, ApJL, 791, L6, doi: [`10.1088/2041-8205/791/1/L6`](http://doi.org/10.1088/2041-8205/791/1/L6)

(ref: 2002ApJ...571L.173W) Watanabe, N., & Kouchi, A. 2002, ApJL, 571, L173, doi: [`10.1086/341412`](http://doi.org/10.1086/341412)

(ref: 1999RPPh...62..143W) Wilson, T. L. 1999, Reports on Progress in Physics, 62, 143, doi: [`10.1088/0034-4885/62/2/002`](http://doi.org/10.1088/0034-4885/62/2/002)

(ref: Wright2015) Wright, C. M., Maddison, S. T., Wilner, D. J., et al. 2015, MNRAS, 453, 414, doi: [`10.1093/mnras/stv1619`](http://doi.org/10.1093/mnras/stv1619)

(ref: 2021MNRAS.505.4821Y) Young, A. K., Alexander, R., Walsh, C., et al. 2021, MNRAS, 505, 4821, doi: [`10.1093/mnras/stab1675`](http://doi.org/10.1093/mnras/stab1675)

(ref: 2021ApJS..257....5Z) Zhang, K., Booth, A. S., Law, C. J., et al. 2021, ApJS, 257, 5, doi: [`10.3847/1538-4365/ac1580`](http://doi.org/10.3847/1538-4365/ac1580)

# Observational set-up

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Setting | Date | No. Antenna | On Source Time | Baselines | Mean PVW | MRS | Phase | Flux/Bandpass |  |
|  |  |  | (mins) | \(m\) | \(mm\) | (") | Calibrator | Calibrator |  |
| A | 05-01-2022 | 42 | 62 | 14.9-783.1 | 0.5 | 3.5 | J1147-6753 | J142-4206 |  |
|  | 27-05-2022 | 46 | 62 | 15.1-783.5 | 0.8 | 3.9 | J1147-6753 | J142-4206 |  |
|  | 09-07-2022 | 41 | 62 | 15.1-783.5 | 0.2 | 3.4 | J1147-6753 | J142-4206 |  |
|  | 10-07-2022 | 41 | 62 | 15.1-783.5 | 0.1 | 3.4 | J1147-6753 | J142-4206 |  |
| B | 05-01-2022 | 42 | 53 | 14.9-783.1 | 0.5 | 3.5 | J1147-6753 | J142-4206 |  |
|  | 06-01-2022 | 45 | 53 | 14.9-976.6 | 1.0 | 3.5 | J1147-6753 | J142-4206 |  |
|  | 10-07-2022 | 41 | 53 | 15.1-1213.4 | 0.5 | 3.7 | J1147-6753 | J142-4206 |  |
|  | 13-07-2022 | 43 | 53 | 15.1-1213.4 | 0.2 | 3.2 | J1147-6753 | J142-4206 |  |
|  | 14-07-2022 | 44 | 53 | 15.1-1301.6 | 0.3 | 2.8 | J1147-6753 | J142-4206 |  |
|  |  |  |  |  |  |  |  |  |  |

: Execution block details for ALMA program 2021.100738.S targeting HD 100546.

# Molecular Data

| Molecule | Transition | Frequency (GHz) | E$_{\mathrm{up}}$ (K ) | log10${\mathrm{(A_{ul}}}$) | $\mathrm{g_{u}}$ | Detection |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  | $J=3-2$ | 345.7959899 | 33.2 | -5.6027 | 7 |  |
|  | $J=3-2$ | 337.0611298 | 32.7 | -5.6344 | 7 |  |
|  | $J=4-3$ | 356.7342230 | 42.8 | -2.4471 | 9 |  |
|  | $J=4-3$ | 340.6306916 | 41.8 | -2.5310 | 12 | \- |
|  | $J=4-3$ | 354.5054779 | 42.5 | -2.6860 | 27 |  |
|  | $J=4-3$ | 345.3397693 | 41.4 | -2.7216 | 27 |  |
|  | $J=4-3$ | 344.2001089 | 41.3 | -2.7258 | 9 |  |
| CN | $J=7/2-5/2, F=7/2-5/2$ | 340.2477700 | 32.7 | -3.3839 | 10 |  |
|  | $J=7/2-5/2, F=7/2-5/2$ | 340.2477700 | 32.7 | -3.4206 | 8 |  |
|  | $J=7/2-5/2, F=5/2-3/2$ | 340.2485440 | 32.7 | -3.4347 | 6 |  |
|  | $J=7/2-5/2$,$\Omega=1/2- F=9/2-7/2$ | 351.0435240 | 36.1 | -5.2649 | 10 |  |
|  | $J=7/2-5/2$,$\Omega=1/2- F=7/2-5/2$ | 351.0517050 | 36.1 | -5.2662 | 8 |  |
|  | $J=7/2-5/2$, $\Omega=1/2- F=7/2-5/2$ | 351.0517050 | 36.1 | -5.3161 | 6 |  |
|  | $J=38-37$ | 345.6090100 | 323.5 | -2.4812 | 77 | \- |
|  | $J=39-38$ | 354.6974631 | 340.5 | -2.4473 | 79 | \- |
|  | $J=19_0-18_0$ | 349.4536999 | 167.7 | -2.5909 | 78 | \- |
|  | $J=9/2-7/2,F=5-4$ | 349.3374558 | 41.9 | -3.7247 | 11 |  |
|  | $J=9/2-7/2,F=4-3$ | 349.3387284 | 41.9 | -3.7349 | 9 |  |
|  | $J=10_{(0,10)}-9_{(1,9)}$ | 351.7815780 | 96.5 | -2.6125 | 63 | \- |
|  | $J=10_{(0,10)}-9_{(1,9)}$ | 351.7815780 | 96.5 | -2.6126 | 21 | \- |
|  | $J=7-6$ | 342.8828503 | 65.8 | -3.0774 | 15 |  |
|  | $J=7-6$ | 337.3964590 | 50.2 | -3.1180 | 15 |  |
|  | $J=10_{(1,10)}-9_{(1,9)}$ | 338.0831953 | 102.4 | -3.1995 | 63 |  |
|  | $J=3_3-3_2$ | 339.3414590 | 25.5 | -4.8372 | 7 | \- |
|  | $J=7_8-6_7$ | 340.7141550 | 81.2 | -3.3023 | 15 |  |
|  | $J=8_8-7_7$ | 344.3106120 | 87.5 | -3.2852 | 17 |  |
|  | $J=8_8-7_7$ | 337.5801467 | 77.3 | -3.3109 | 17 | \- |
|  | $J=9_8-8_7$ | 339.8572694 | 86.1 | -3.2944 | 19 |  |
|  | $J=6_{(4,2)}-6_{(3,3)}$ | 357.9258478 | 58.6 | -3.5845 | 13 |  |
|  | $J=28-27$ | 340.4492733 | 237.0 | -3.9378 | 57 | \- |
|  | $J=29-28$ | 352.5995703 | 253.9 | -3.8918 | 59 | \- |
|  | $J=5_{(1,5)}-4_{(1,4)}$ | 351.7686450 | 62.5 | -2.9201 | 33 |  |
|  | $J=5_{(1,5)}-4_{(1,4)}$ | 343.3257130 | 61.3 | -2.9517 | 33 |  |
|  | $J=7_{0}-6_{0}$ | 338.4086980 | 65.0 | -3.7691 | 60 |  |
|  | $J=32_{(2,31)}-31_{(2,30)}$ | 344.0297653 | 276.1 | -3.2099 | 65 |  |
|  | $J=32_{(1,32)}-31_{(1,31)}$ | 344.0297645 | 276.1 | -3.2099 | 65 |  |
|  | $J=32_{(0,32)}-31_{(0,31)}$ | 344.0295703 | 276.1 | -3.2099 | 65 |  |
|  | $J=32_{(1,32)}-31_{(1,31)}$ | 344.0295694 | 276.1 | -3.2099 | 65 |  |
|  | $J=19_{(0,19)}-18_{(1,18)}$ AE | 342.6080601 | 167.1 | -3.2816 | 117 | \- |
|  | $J=19_{(0,19)}-18_{(1,18)}$ EA | 342.6080602 | 167.1 | -3.2817 | 78 | \- |
|  | $J=19_{(0,19)}-18_{(1,18)}$ EE | 342.6081188 | 167.1 | -3.2816 | 312 | \- |
|  | $J=19_{(0,19)}-18_{(1,18)}$ AA | 342.6081774 | 167.1 | -3.2816 | 195 | \- |

# Image properties

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | robust | Beam | rms | Peak | Int. Flux |  |  |
|  |  |  | ($''$ $\times$ $''$ ($^{\circ}$)) | (mJy beam $^{-1}$) | (mJy beam $^{-1}$) | (mJy km s$^{-1}$) |  |  |
|  | $J=3-2$ | 0.5 | 0.35$\times$0.23 (59.7) | 0.76 | 1128.66 | 190464.0$\pm$28.0 |  |  |
|  | $J=3-2$ | 0.5 | 0.39$\times$0.31 (28.5) | 0.86 | 216.49 | 5693.0$\pm$26.0 |  |  |
|  | $J=4-3$ | 0.5 | 0.34$\times$0.23 (59.8) | 0.88 | 48.81 | 5952.0$\pm$33.0 |  |  |
|  | $J=4-3$ | 2.0 | 0.37$\times$0.29 (28.8) | 0.78 | \- | $<$33.0 |  |  |
|  | $J=4-3$ | 0.5 | 0.34$\times$0.23 (59.7) | 0.81 | 72.58 | 3699.0$\pm$30.0 |  |  |
|  | $J=4-3$ | 0.5 | 0.35$\times$0.23 (59.7) | 0.72 | 6.12 | 172.0$\pm$26.0 |  |  |
|  | $J=4-3$ | 0.5 | 0.35$\times$0.24 (59.3) | 0.78 | 8.17 | 134.0$\pm$29.0 |  |  |
|  | $N=4-3$ | 0.5 | 0.38$\times$0.30 (29.5) | 0.83 | 28.77 | 2732.0$\pm$26.0 |  |  |
|  | $J=7/2-5/2$ | 2.0 | 0.47$\times$0.37 (30.8) | 0.73 | 3.75 | 134.0$\pm$27.0 |  |  |
|  | $J=38-37$ | 2.0 | 0.47$\times$0.33 (58.3) | 0.67 | \- | $<$23.0 |  |  |
|  | $J=39-38$ | 2.0 | 0.46$\times$0.32 (58.5) | 0.69 | \- | $<$25.0 |  |  |
|  | $J=19_0=18_0$ | 2.0 | 0.46$\times$0.37 (30.7) | 0.68 | \- | $<$24.0 |  |  |
|  | $N=4-3$ | 0.5 | 0.37$\times$0.30 (26.7) | 0.80 | 20.88 | 1601.0$\pm$25.0 |  |  |
|  | $J=10_{(0,10)}-9_{(1,9)}$ | 2.0 | 0.47$\times$0.37 (30.8) | 0.70 | \- | $<$27.0 |  |  |
|  | $J=7-6$ | 0.5 | 0.35$\times$0.24 (59.4) | 0.77 | 30.38 | 932.0$\pm$28.0 |  |  |
|  | $J=7-6$ | 2.0 | 0.48$\times$0.39 (31.9) | 0.74 | 7.00 | 86.0$\pm$18.0 |  |  |
|  | $J=10_{(1,10)}-9_{(1,9)}$ | 2.0 | 0.38$\times$0.30 (27.7) | 0.85 | 11.69 | 128.0$\pm$27.0 |  |  |
|  | $J=7_8-6_7$ | 0.5 | 0.37$\times$0.30 (28.8) | 0.82 | 25.79 | 343.0$\pm$26.0 |  |  |
|  | $J=8_8-7_7$ | 0.5 | 0.35$\times$0.23 (59.6) | 0.75 | 23.69 | 281.0$\pm$27.0 |  |  |
|  | $J=3_3-3_2$ | 0.5 | 0.38$\times$0.30 (28.8) | 0.76 | \- | $<$32.0 |  |  |
|  | $J=8_8-7_7$ | 0.5 | 0.38$\times$0.30 (28.8) | 0.77 | 3.49 | 32.0$\pm$10.0 |  |  |
|  | $J=7_8-6_7$ | 0.5 | 0.38$\times$0.30 (27.8) | 0.82 | \- | $<$33.0 |  |  |
|  | $J=6_{4,2}-6_{3,3}$ | 2.0 | 0.47$\times$0.32 (60.8) | 0.78 | 5.39 | 98.0$\pm$21.0 |  |  |
|  | $J=28-27$ | 2.0 | 0.48$\times$0.37 (32.8) | 0.69 | \- | $<$21.0 |  |  |
|  | $J=27-26$ | 2.0 | 0.46$\times$0.37 (32.8) | 0.97 | \- | $<$33.0 |  |  |
|  | $J=5_{(1,5)}-4_{(1,4)}$ | 0.5 | 0.37$\times$0.30 (27.1) | 0.94 | 55.27 | 3065.0$\pm$30.0 |  |  |
|  | $J=5_{(1,5)}-4_{(1,4)}$ | 2.0 | 0.47$\times$0.33 (58.2) | 0.79 | 3.88 | 66.0$\pm$21.0 |  |  |
|  | $J=7_{0}-6_{0}$ | 0.5 | 0.38$\times$0.30 (28.3) | 0.80 | 6.92 | 39.0$\pm$12.0 |  |  |
|  | $J=31-30$ | 0.5 | 0.35$\times$0.24 (59.3) | 0.76 | 8.47 | 82.0$\pm$12.0 |  |  |
|  | $J=19-18$ | 0.5 | 0.36$\times$0.24 (59.4) | 0.83 | \- | $<$39.0 |  |  |

# Weak-line detections

![image](HD100546_weaklines_C34S.png) ![image](HD100546_weaklines_H213CO.png) ![image](HD100546_weaklines_NO.png) ![image](HD100546_weaklines_34SO.png) ![image](HD100546_weaklines_SO2_59K.png)

![](HD100546_gofish_rings.png)

</paper>

Write the methods card for this paper.