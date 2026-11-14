# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024AJ....167..165B\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2024AJ....167..165B",
 "title": "An ALMA Molecular Inventory of Warm Herbig Ae Disks. II. Abundant Complex Organics and Volatile Sulphur in the IRS 48 Disk",
 "year": 2024,
 "journal": "The Astronomical Journal",
 "first_author": "Booth, Alice S.",
 "n_authors": 14,
 "arxiv_id": "2402.04002",
 "doi": "10.3847/1538-3881/ad26ff",
 "alma_projects_linked_by_archive": [
  "2017.1.00834.S",
  "2021.1.00738.S"
 ]
}
```

Paper text:
<paper>
# An ALMA molecular inventory of warm Herbig Ae disks:\
II. Abundant complex organics and volatile sulphur in the IRS 48 disk

## Abstract

The Atacama Large Millimeter/submillimeter Array (ALMA) can probe the molecular content of planet-forming disks with unprecedented sensitivity. These observations allow us to build up an inventory of the volatiles available for forming planets and comets. Herbig Ae transition disks are fruitful targets due to the thermal sublimation of complex organic molecule (COM) and likely -rich ices in these disks. The IRS 48 disk shows a particularly rich chemistry that can be directly linked to its asymmetric dust trap. Here, we present ALMA observations of the IRS 48 disk where we detect 16 different molecules and make the first robust detections of , , and (ethylene oxide) in a protoplanetary disk. All of the molecular emissions, aside from CO, are co-located with the dust trap and this includes newly detected simple molecules such as , and . Interestingly, there are spatial offsets between different molecular families, including between the COMs and sulphur-bearing species, with the latter being more azimuthally extended and radially located further from the star. The abundances of the newly detected COMs relative to are higher than the expected protostellar ratios, which implies some degree of chemical processing of the inherited ices during the disk lifetime. These data highlight IRS 48 as a unique astrochemical laboratory to unravel the full volatile reservoir at the epoch of planet and comet formation and the role of the disk in (re)setting chemical complexity.

# Introduction

Due to the sensitivity of the Atacama Large Millimeter/submillimeter Array (ALMA) we now have unmatched access to the volatile reservoir in planet-forming disks. In recent years, ALMA has enabled the detection of both new disk molecules including and , and rare isotopologues (e.g., and ) (cite: 2015Natur.520..198O; 2019ApJ...882L..31B; 2021A&A...651L...6B; 2022ApJ...926..148F). What is particularly exciting is the detection of complex organic molecules (COMs) which are defined as molecules containing at least 6 atoms and of which at least one is carbon (cite: 2009ARA&A..47..427H). Although the first detection of the simplest COM in a Class II T-Tauri disk (TW Hya) traced a very low abundance of cold (cite: 2016ApJ...823L..10W) subsequent observations of warmer Herbig Ae transition disks have revealed abundant thermally desorbed and even other COMs of higher complexity (cite: 2021NatAs...5..684B; 2021A&A...651L...5V; Booth2023; 2022A&A...659A..29B). The detection of abundant COMs in warm Herbig Ae disks is clear evidence for the inheritance of ices from the earlier stages of star formation. This is because only forms efficiently on the surfaces of cold dust grains and primarily via the hydrogenation of CO ice (cite: Watanabe2002; 2009A&A...505..629F; 2022ApJ...931L..33S).

In the warm young F/Herbig Ae disks HD 100546, IRS 48 and HD 169142 there is no evidence for significant CO freeze-out meaning that the observed reservoir of cannot have formed *in-situ*. This was shown directly for the HD 100546 disk using astrochemical models (cite: 2021NatAs...5..684B). Therefore, in order for to be present in these systems rich ices must survive the star formation process and be transported to the inner disk where they thermally sublimate. will come off the grains at a similar temperature as (cite: 2022ESC.....6..597M) and therefore the bulk of the volatile content of the disks should also be in the gas phase in this region of the disk. These sources therefore give us a window into a typically unobservable molecular reservoir in disks.

The disk most rich in COMs and potentially -derived volatiles like SO is the disk around the young star IRS 48. The IRS 48 disk has been well studied with ALMA and hosts the most asymmetric dust trap yet discovered at a distance of 60 au from the central star (cite: vanderMarel2013; 2021AJ....161...33V; 2023ApJ...948L...2Y). Its gas mass of only 5.5$\times10^{-4}$ M$_{\odot}$ is much lower than other Herbig Ae disks, yet it is very line rich, with detection’s of the CO isotopologues , , , along with , , , , , , and, tentatively (cite: vanderMarel2013; 2021A&A...651L...5V; 2021A&A...651L...6B; 2022A&A...659A..29B; 2023arXiv230300768L). The significance of the reported non-detections of CS, , in IRS 48 were quantified by (cite: 2021A&A...651L...6B) and (cite: 2023arXiv230300768L) and indicate a C/O ratio in the disk gas that is significantly less than 1. This low C/O and lack of is consistent with being in the gas-phase and a general lack of volatile depletion at least at the location of the dust trap (cite: 2023arXiv230300768L).

There are several key simple molecules that have yet to be targeted in the IRS 48 disk, which would allow for a more complete comparison to other Herbig Ae disks. Here we present the results of an ALMA line survey of the IRS 48 disk where we target $>$20 molecular species. These data provide key constraints on the abundances of , HCN, CN, and CS in this system. Additionally, we further unravel the volatile sulphur and complex organic reservoir of the disk and discuss the physical/chemical origin of the molecular sub-structures observed. We particularly make a direct comparison between the molecular inventory of the IRS 48 and HD 100546 disks where the initial results for the latter are presented in (cite: Booth2023_hd100546) and, contextualise the detections of COMs in these systems with protostellar environments.

# Observations

IRS 48 was observed in the ALMA program 2021.1.00738.S (PI. A. S. Booth) and the general properties of the IRS 48 system are listed in Table [\[tab:A1\]](#tab:A1). The data consist of two spectral settings with four spectral windows each at a spectral resolution of 976.6 kHz (0.84 km s$^{-1}$ at 350 GHz) and a bandwidth of 1.875 GHz. These spectral windows are centered at 338.790824, 340.732413, 348.916936 and 350.775389 GHz for setting A and, 344.240980, 3459.40999, 354.367095 and 356.067114 GHz for setting B. Further details on the individual execution blocks are provided in the Appendix in Table [2](#tab:A3) and for full details the data reduction, observational set-up and imaging please refer to the companion paper which also presents data on the HD 100546 system (cite: Booth2023_hd100546). The self-calibration was performed on the IRS 48 continuum data after flagging the strong lines which resulted in a continuum signal-to-noise increase from $\approx$475 to $\approx$3220. This process consisted of four rounds of phase-calibration and one round of amplitude calibration and resulted in the detection of the weak millimetre emission in the north of the IRS 48 disk. The data were imaged in CASA using `tCLEAN` with the multiscale deconvolver with a uniform velocity resolution of 0.9 km s$^{-1}$. These $\approx$0.3$''$ data have a beam area 2.5$\times$ smaller than that presented the series of papers from (cite: 2021A&A...651L...5V; 2021A&A...651L...6B; 2022A&A...659A..29B; 2023arXiv230300768L). Individual lines were cleaned with Keplerian masks down to 4$\times$ the rms of the dirty image where the Keplerian masks were constructed using the properties for the IRS 48 disk as listed in Table [\[tab:A1\]](#tab:A1). The properties of the transitions imaged and the resulting beam sizes and rms noise for each line are listed in Tables [\[tab:lines\]](#tab:lines) and [\[tab:irs48_images\]](#tab:irs48_images) in the Appendix.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | Type | Dist. | Incl. | PA | L | M$_{*}$ | M$_{dust}$ | M$_{gas}$ | log$_{10}(\dot{M}_{acc}$) | log10($L_{Xray}$) | v$_{sys}$ | Refs. |  |
|  |  | (pc) | (deg) | (deg) | ($L_{\odot}$) | ($M_{\odot}$) | ($M_{\odot}$) | ($M_{\odot}$) | ($M_{\odot}$ yr$^{-1}$) | (erg s$^{-1}$) | (km s$^{-1}$) |  |  |
| IRS 48 | A0 | 135 | 50.0 | 100.0 | 14.3 | 2.0 | 1.5$\times10^{-5}$ | 5.5$\times10^{-4}$ | -8.40 | $<$27.0 | 4.55 | \[1-7\] |  |
| HD 100546 | A0-A1 | 110 | 41.7 | 146.0 | 23.5 | 2.2 | 1.1$\times10^{-3}$ | 1.5$\times10^{-1}$ | -6.81 | 28.1 | 5.70 | \[8-13\] |  |

![](matched_filter_comparison_v4.png)

# Results

## Molecules detected

We use matched filtering to make an initial line identification (cite: Loomis2018). This technique uses the predictable Keplerian rotation of the disk gas to detect molecular lines in the visibility data via cross correlation of the uv-data with a filter. This filter can be a smooth model, e.g. a Keplerian mask, the FITS output of a line radiative transfer model or, a strong line detection in the disk. In Figure [1](#fig:1) we present the resulting matched filter response over the full data set for the IRS 48 disk with a Keplerian model with an outer radius of 150 au compared to the HD 100546 response (outer radius of 300 au) that is presented in (cite: Booth2023_hd100546). HD 100546 was observed in the same manner as IRS 48 and we find that the IRS 48 disk is more line rich but there are different molecules detected in each disk. These differences may be attributed to different physical properties of the systems and/or the dominant chemical processes. Both are disks around young A-type stars and the characteristics of these two systems are compared in Table [\[tab:A1\]](#tab:A1). In Section 4.2 we discuss the similarities and differences both physically and chemically between the two disks. The fully annotated version of the IRS 48 filter response is shown in the Appendix in Figure [7](#fig:irs48_filter). From this we have detected 16 molecular species in IRS 48 disk where a detection is defined as a matched filter response of at least 4 $\sigma$. This includes robust detections of the rare isotopologues , and and, the detection of the first heterocycle - ethylene oxide () - in protoplanetary disks. We detect two lines of with the fiducial Keplerian model filter at rest frequencies of 338.7720826 GHz and 350.3036524 GHz. Using alternative image filters does not yield a significant improvement in the detection strength - likely due to the compact nature of the emission. In the channel maps compact emission from is detected at the 4 $\sigma$ level over the 3 consecutive channels where the lines are strongest for both lines. Interestingly, although the isomer acetaldehyde () us typically more abundant (cite: 2001ApJ...560..792I; 2017A&A...597A..53L), it is not detected in the IRS 48 disk. Dimethyl ether () is detected again, as reported by (cite: 2022A&A...659A..29B), and their weak detection of methyl formate () is clearly confirmed in our data. A investigation into other COMs lines covered in these data and upper-limits on other non-detections will follow in Kipfer et al. (in prep). A summary of the molecules detected/not-detected in both the IRS 48 and HD 100546 disks are shown in Table [1](#tab:detections). It is unclear from visual inspection of the data if is detected in IRS 48 or not as this line is blended with a strong line. Using matched filtering and the HCN as a mask we find that , CN and are all not detected.

| Molecule | HD 100546 | IRS 48 |
|:--------:|:---------:|:------:|
|          |           |        |
|          |           |        |
|          |           |        |
|          |    \-     |   \-   |
|          |           |   \-   |
|          |           |        |
|          |           |   ?    |
|          |           |   \-   |
|          |           |        |
|          |    \-     |   \-   |
|          |    \-     |   \-   |
|          |           |   \-   |
|          |    \-     |   \-   |
|          |           |        |
|          |           |   \-   |
|          |           |        |
|          |           |        |
|          |    \-     |        |
|          |           |        |
|          |    \-     |   \-   |
|          |           |   \-   |
|          |           |        |
|          |           |        |
|          |           |        |
|          |           |        |
|          |    \-     |        |
|          |    \-     |        |

: Molecules detected () and not detected (-) in the ALMA observations of the IRS 48 and HD 100546 disks presented in this paper and (cite: Booth2023_hd100546).

## Integrated intensity maps

Figure [2](#fig:mom02) presents the 0.9 mm continuum map and the integrated intensity maps of the representative transitions of each molecule detected in the IRS 48 disk. This galley does not include the isotopologues of SO which will be the focus of a future work. These line maps were generated using the Keplerian masks generated in the CLEANing with no clipping thresholds. All of the molecules aside from and only show significant emission in the south of the disk - the same region of the disk as the millimetre dust trap. In the north of the disk the emission suffers from cloud absorption along the minor axis of the disk but there is weak millimetre dust and emission present here (also seen by (cite: 2014A&A...562A..26B) in the $J=6-5$). Previous studies have shown asymmetric emission for , , and several of the large organics (cite: 2021A&A...651L...5V; 2021A&A...651L...6B; 2022A&A...659A..29B). Here, we present the first detections of the simple molecules , and , and interestingly find that they all show a similar asymmetric emission morphology. However, not all of the molecules have the exact same asymmetric morphology.

![](IRS48_gallery.png)

## Sub-structures in the IRS 48 disk

The only molecule detected in the north of the IRS 48 disk is CO, while all of the other species are located in the south, but there are variations in where the different molecules peak both radially and azimuthally. Figure [3](#fig:irs48_azimuthal_profiles) shows azimuthal profiles taken from the intensity maps in Figure [2](#fig:mom02) at the radius where each of the molecules peak along with the normalised azimuthal profile of the millimetre dust. From this, it is clear that there are dips in the intensity of most species at the azimuthal peak of the dust emission. This could be due to line suppression from the optically thick dust (cite: 2018ApJ...853..113W; 2020ApJ...896L...3D) but interestingly this is not as apparent for the COMs emission. The COMs emission is also significantly narrower in azimuthal extent than the simpler molecules that are detected and are located at the dust peak with a similar width to the millimetre dust. This is highlighted further in Figure [4](#fig:irs48_azimuth) which presents a polar deprojection of the intensity maps. It is clear that the SO and peak radially further out in the disk than the and , which was not clear in the lower spatial resolution data presented in (cite: 2021A&A...651L...5V) and (cite: 2021A&A...651L...6B). Furthermore, the emission is peaking closer to the star, in the gas cavity, than the , and the is approximately co-spatial with the . The possible physical and chemical explanations for these different emission morphologies will be discussed further in Section 4.1.

![](IRS48_azimuthal_profiles.png)

![](IRS48_azimuth_plot.pdf)

## Disk integrated line fluxes

In Figure [5](#fig:fluxes) we show the disk-integrated fluxes for molecules detected/not detected in the IRS 48 disk compared to the HD 100546 disk, which was observed as part of the same ALMA program (cite: Booth2023_hd100546). For some molecules we detected multiple transitions but we only report the flux of a representative transition. These representative transitions are based on the strongest lines detected in the HD 100546 disk. In the case of CN, and the chosen lines are the strongest of the $N=3-2$, $N=4-3$ and $J=7/2-5/2$ hyper-fine groups, respectively. For the $J=6_{(4,2)}-6_{(3,3)}$ is the strongest line detected and for SO the $J=7_8-6_7$ transition is the strongest. For we pick the $J=7_{0}-6_{0}$ transition and for and we use the $J=3_1-3_0$ and $J=19-18$ transitions which are both blends of multiple transitions. These fluxes are extracted from Keplerian masks which are 2.0$''$ and 4.0$''$ in radius for the IRS 48 and HD 100546 disks, respectively. If a molecule is undetected we give the 3 $\sigma$ upper limit on the flux where $\sigma$ is propagated from the rms in the channel maps and the number of pixels included in the mask (cite: 2019A&A...623A.124C). All of the line fluxes are listed in Table [\[tab:irs48_images\]](#tab:irs48_images) with their associated errors. After accounting for the different distances to the two sources (110 pc v 135 pc) HD 100546 is brighter in all of the lines aside from: , , , , , and . Note that the IRS 48 (J=3-2) flux is a lower-limit due to foreground cloud absorption (cite: 2014A&A...562A..26B).

To take into account the significantly different gas masses of the HD 100546 and IRS 48 disks (with HD 100546 $>$100$\times$ more massive than IRS 48; see Table [\[tab:A1\]](#tab:A1)) we normalise the line fluxes with respect to the $J=3-2$ line. The line is the most optically thin CO isotopologue detected in both disks and this flux should be a good proxy for the total gas content in each disk (cite: 2021ApJS..257....5Z). These flux ratios are shown in Figure [5](#fig:fluxes) and from this, there are significant differences in the relative intensities of the different molecular lines between these two disks. There are caveats to this comparison, e.g., if lines are optically thick in one or both of the disks and/or the excitation temperatures are very different. This is, however, a good starting point for comparing the two sources. The observed line strengths of most of the simple molecules are within a factor of 3 for the two disks. The differences in the line ratios become more significant when looking at the molecules that are already brighter in IRS 48. There is a factor 15 difference for NO and , a factor 50 difference in the , and and a factor 80 difference for between the two disks. The largest difference is in the / line ratio which is $\approx$130$\times$ higher in IRS 48 than HD 100546.

![](line_fluxes.png)

## Column densities

We estimate column densities following the methods outlined in (cite: 2018ApJ...859..131L) and in the same manner as (cite: Booth2023_hd100546). For the molecules where multiple transitions are detected, e.g., and , we pick one representative transition. Future work will focus specifically on constraining the excitation conditions of these molecules individually. We compute azimuthal column density profiles for the IRS 48 disk from the profiles presented in Figure [3](#fig:irs48_azimuthal_profiles) and explore a range of excitation temperatures: 50, 100 and 150 K. These temperatures are motivated by the observations and modelling results from (cite: 2021A&A...651L...5V) and (cite: 2023arXiv230300768L). For the non-detected molecules, we calculate an upper limit propagated from the upper limits on the disk-integrated fluxes (listed in Table [\[tab:irs48_images\]](#tab:irs48_images)) assuming a conservative emitting area of a 2" aperture. The resulting profiles are shown in Figure [6](#fig:irs48_azimuthal_columns) and the main results are as follows:

- The peak column density is $\approx2.5\times10^{16}$ $\mathrm{cm^{-2}}$ at 100 K and the line is optically thin. With the assumption of ISM isotope ratios, this is equivalent to a CO column density of $\approx5\times10^{19}$ $\mathrm{cm^{-2}}$. In Table [\[tab:irs48_peaks\]](#tab:irs48_peaks) we list the peak column density ratios of each of the molecules relative to the average CO column density across the IRS 48 disk.

- The line emission from the simple molecules , and are all optically thin. and are both undetected with the 3 $\sigma$ disk-averaged upper limit of CN $\leq2\times10^{12}$ $\mathrm{cm^{-2}}$ and $\leq5\times10^{13}$ $\mathrm{cm^{-2}}$.

- The radical CS is detected with a peak column density of $\approx10^{13}~\mathrm{cm^{-2}}$ which is a factor of a few lower than the upper-limit report by (cite: 2021A&A...651L...6B). is not detected with a column density upper limit of $<2\times10^{13}$ $\mathrm{cm^{-2}}$ which relative to CS is not constraining when comparing to other disks.

- SO is abundant in the IRS 48 disk and therefore we use the $J=3_3-3_2$ transition for the column density calculation. This line has the lowest Einstein coefficient of the three SO transitions detected. The other two SO lines have lower column densities due to their higher optical depths. This results in a peak column density of $5\times10^{15}~\mathrm{cm^{-2}}$ at 100 K. This is $\approx4\times$ higher than the peak column density and results in a N(CS)/N(SO)$\approx10^{-3}$. When comparing the derived SO column density with the column density, the ratio is consistent with 22, the local ISM to ratio (cite: 1999RPPh...62..143W), indicating the $J=3_3-3_2$ line is indeed optically thin. A detailed analysis on the S isotopes detected in these data will follow in a future work. OCS is not detected with a column density upper limit of $<10^{12}$ $\mathrm{cm^{-2}}$, less than a few percent of the SO column density.

- Both and are robustly detected and we find a / column density ratio of $\approx4$. This is significantly lower than the expected / of 69 (cite: 1999RPPh...62..143W) indicating optically thick emission or a lower isotope ratio.

- The column density at peaks at $\approx2\times10^{15} \mathrm{cm^{-2}}$. Using the column density derived for the main isotopologue results in a column density ratio of / of 14$\pm1$ and using the and a C isotope ratio of 69 results in a ratio of 0.8$\pm0.1$. This means that if the is indeed optically thick the ratio of to is $\approx$1. The emission is still compact in these new data therefore, as discussed in (cite: 2022A&A...659A..29B) the emission may be optically thick and beam diluted. This will be investigated further in Temmink et al. (in prep.) along with the constraints from which remains undetected.

- The peak abundance ratios of the COMs , and with respect to the peak column density are $0.28\pm0.04$, $0.25\pm0.03$ and $0.017\pm0.006$, respectively, at a temperature of 100 K. is undetected with an upper-limit of $\approx4\times10^{13} \mathrm{cm^{-2}}$.

![](IRS48_azimuthal_column_densities.png)

|  |  |  |  |
|:--:|:--:|:--:|:--:|
| Molecule | N(X)/N(CO) | N(X)/N(CO) | N(X)/N(CO) |
|  | $T_{ex}$=50K | $T_{ex}$=100K | $T_{ex}$=150K |
|  | $2.8\pm0.9\times10^{-7}$ | $2.4\pm0.8\times10^{-7}$ | $2.3\pm0.8\times10^{-7}$ |
|  | $5.0\pm2.0\times10^{-7}$ | $5.0\pm2.0\times10^{-7}$ | $5.0\pm2.0\times10^{-7}$ |
|  | $<2.0\times10^{-8}$ | $<2.0\times10^{-8}$ | $<2.0\times10^{-8}$ |
|  | $4.0\pm1.0\times10^{-5}$ | $4.0\pm2.0\times10^{-5}$ | $4.0\pm2.0\times10^{-5}$ |
|  | $<5.0\times10^{-7}$ | $<5.0\times10^{-7}$ | $<5.0\times10^{-7}$ |
|  | $4.0\pm2.0\times10^{-7}$ | $3.0\pm1.0\times10^{-7}$ | $3.0\pm1.0\times10^{-7}$ |
|  | $2.3\pm0.7\times10^{-4}$ | $2.6\pm0.8\times10^{-4}$ | $2.7\pm0.9\times10^{-4}$ |
|  | $6.0\pm2.0\times10^{-5}$ | $6.0\pm2.0\times10^{-5}$ | $2.0\pm0.6\times10^{-5}$ |
|  | $1.0\pm0.3\times10^{-5}$ | $9.0\pm3.0\times10^{-6}$ | $9.0\pm3.0\times10^{-6}$ |
|  | $2.1\pm0.7\times10^{-6}$ | $2.1\pm0.7\times10^{-6}$ | $9.0\pm3.0\times10^{-7}$ |
|  | $1.1\pm0.3\times10^{-5}$ | $1.2\pm0.4\times10^{-5}$ | $1.3\pm0.4\times10^{-5}$ |
|  | $2.4\pm0.8\times10^{-4}$ | $3.0\pm1.0\times10^{-5}$ | $1.9\pm0.6\times10^{-5}$ |
|  | $7.0\pm2.0\times10^{-5}$ | $2.9\pm0.9\times10^{-5}$ | $2.4\pm0.8\times10^{-5}$ |
|  | $3.0\pm1.0\times10^{-6}$ | $2.0\pm1.0\times10^{-6}$ | $2.0\pm1.0\times10^{-6}$ |
| average | $1.3\pm0.4\times10^{19}$ | $1.8\pm0.4\times10^{19}$ | $2.3\pm0.8\times10^{19}$ |

# Discussion

In this section, we discuss the physical and chemical origins of the observed molecular emission in the IRS 48 disk. We place this unique source in context with another chemically well-characterised protoplanetary disk namely, the HD 100546 disk which has been observed in the same frequecny setting within the same ALMA program.

## The origin of the molecular sub-structures in the IRS 48 disk

The simplest explanation for the molecular complexity and high relative column densities of oxygen-bearing volatiles in the IRS 48 disk is the sublimation of ices. With this new data, there are clear spatial offsets between the different molecules that complicate this picture. As seen in Figures [2](#fig:mom02) and [4](#fig:irs48_azimuth), the COMs have the most compact emission that peaks with the dust and these are also the species with the highest binding energies. The and HCN emissions are roughly co-spatial with a depression in both the and emissions where the COMs (and dust) emission is brightest. Interestingly, the SO and emissions, which (cite: 2021A&A...651L...6B) proposed to originate first from the sublimation and photodissociation of and to OH and S respectively, are peaking radially further out in the disk compared to the , the latter of which should trace the same region as the . This may point to a different chemical origin for the SO and . There may also be a link between gas leading and trailing in the Keplerian orbit of the dust trap. The orbital direction is highlighted in Figure [4](#fig:irs48_azimuth). The dust trap in the IRS 48 disk has been proposed to be a large anticyclonic vortex (cite: 2013Sci...340.1199V) therefore, it could be expected that there is additional radial and vertical mixing, or turbulence, and this will affect the disk chemistry. (cite: 2011ApJS..196...25S) find that in their turbulent disk chemistry models the abundances of SO and can increase by two orders of magnitude relative to the laminar disk due to the enhanced sublimation of ices. The interplay between the dust and line optical depth may also be influencing the observed emission structures. Therefore, a more detailed analysis of the IRS 48 line emission, including mapping the disk temperature structure, will be the focus of future work (Temmink et al. in prep).

## In context with other Herbig disks

Both the IRS 48 and HD 100546 disks show rich reservoirs of complex organics and volatile sulphur that are yet to be detected in most other planet-forming disks (aside from HD 169142; (cite: Booth2023)). The simplest explanation for the chemical origin of these species is via the sublimation of and COM-rich ices. The brightness temperatures of the in these disks are 100 K indicating the physical conditions for ice-sublimation are indeed possible (cite: 2023A&A...670A.154W). There are significant differences between the two disks, especially when considering their mass and size. The HD 100546 disk has a gas mass 500$\times$ and dust mass 100$\times$ higher than the IRS 48 disk (see Table [\[tab:A1\]](#tab:A1)) and the HD 100546 CO disk extends to $\approx$600 au compared to $\approx$200 au for IRS 48. Given the different mass reservoirs in the disks, one may expect IRS 48 to have uniformly lower line fluxes than HD 100546 but, as shown in Figure [5](#fig:fluxes), this is not the case. On a disk average level the relative fluxes of simple oxygen molecules (NO, SO, ) and larger organics (, COMs) are 15 to 130 times brighter in IRS 48 than HD 100546.

The abundance in the IRS 48 disk is similarly low as found in HD 100546 and HD 142527 which, is 2 orders of magnitude lower than found in the HD 163296 and MWC 480 disks (cite: 2021ApJS..257...13A; 2023A&A...675A.131T; Booth2023_hd100546). This may be due to the low stellar X-ray flux of IRS 48 and/or the presence of gas-phase (not yet detected in IRS 48 but only inferred, (cite: 2023arXiv230300768L)) which effectively destroys . We do not detect CN in IRS 48 and similar to HD 100546 it has a low CN/HCN ratio when compared to other disks. The low CS/SO ratio and non-detection of is consistent with a disk C/O$<$1 as reported by (cite: 2021A&A...651L...6B). Similar to HD 100546, NO is the most abundant observed nitrogen carrier in the IRS 48 disk when compared to HCN or CN. The sulphur-bearing equivalent of , , was not detected in IRS 48. Given the high abundance of in IRS 48 this may be surprising but in the HD 100546 disk the follows the CS (as also found in MWC 480 and HD 169142; (cite: 2021ApJS..257...12L; Booth2023)) and not the sublimating SO in the inner disk. This indicates that the in disks is likely forming in the gas-phase at lower temperatures ($<$100 K) rather than having a significant abundance on the grains.

## Contextualising the volatile sulphur reservoir in the IRS 48 disk

In IRS 48 SO, and CS are detected but OCS and are not. With this family of molecules, we can compare the relative column density ratios of these species to both protostars and comets. In IRS 48 SO is the most abundant S-bearing volatile detected with peak column density ratios of /SO of $\approx$26%, CS/SO of $\approx$0.2%, /SO of $<$0.3% and, /SO of $<$1.0%. The /SO ratio in IRS 48 is similar to that detected in HD 100546 where again the SO column density is higher than the column density (cite: Booth2023_hd100546), but this is not the same as observed towards both protostars and comets. (cite: 2018MNRAS.476.4949D) compare the volatile sulphur reservoirs in the comet 67P and towards the protostar IRAS 16293–2422 B. Comparing these environments to IRS 48: , OCS and are all lower in abundance relative to SO in this disk than could be expected from the sublimation of cometary ices, although the SO/ ratio from 67 P has been shown to vary in time, exceeding 1 at points (cite: 2016MNRAS.462S.253C). Additionally, (cite: 2018MNRAS.476.4949D) show that OCS has strong variations between these two environments with OCS/SO $\approx$60% in 67P and $\approx$560% in IRAS 16293–2422 B, where in the latter source OCS is proposed to be enhanced due to UV irradiation. For both ratios, OCS would have been detectable in our data of the IRS 48 (and HD 100546) disk. (cite: 2022ApJ...941...32B) find that the column density of OCS in the ices toward massive young stellar objects (MYSOs) correlates with the abundance of ice. Therefore, with the detection of in IRS 48 we may expect to also see OCS if these ices are dually inherited by the disk, but the binding energy of OCS (pure ice 2430 K, (cite: 2012MNRAS.425.1264W)) is significantly lower than than of (on water ice 5000 K (cite: 2020ApJ...904...11F; 2022ESC.....6..597M)). The median ice abundance of OCS relative to towards the MYSOs target by (cite: 2022ApJ...941...32B) is $\approx$1% and in contrast for IRS 48 we find that gas-phase column density ratio of OCS/$<$0.1%. One explanation for the lack of OCS could be that during the disk lifetime, the volatile S in the simple inherited ices is converted to more refractory compounds like S allotropes due to processing via UV irradiation (cite: 2022A&A...657A.100C). Formation of S-allotropes can also can also act to destroy OCS on the ice, with models showing that OCS + S $\rightarrow$ + CO can be an important destruction pathway for OCS ice (cite: 2019A&A...624A.108L). If is desorbed from grains it can also play an important role in gas-phase SO (and SO2) formation, via reactions with atomic O. All in all, these comparisons show that the gas-phase volatile sulphur in IRS 48 is distinct to both the gas and ice detected towards protostars and in comets.

## Molecular complexity as evidence for ice processing?

The degree of molecular complexity detected in the IRS 48 disk is unique for protoplanetary disks with three $\geq$7 atom COMs detected - , and . is the first detection of a heterocyclic molecule in a protoplanetary disk. Heterocycles are abundant in comet 67P (cite: 2023arXiv230800343H) and more generally these rings of carbon with an oxygen are of biological importance. The peak abundance ratios of these COMs with respect to the peak column density show that these COMs have abundances $\approx$30, 25 and 2% of , respectively. Similarly, in the HD 100546 disk, in addition to , is also detected with an abundance of 70% relative to . Interestingly, is undetected in HD 100546 with an upper limit of $\lesssim$10% relative to . The slight differences in binding energies of and are not sufficient to explain the lack of in HD 100546 since they are both lower than the binding energy of (cite: 2022ESC.....6..597M; 2023A&A...676A..80L).

Typically, in the warm gas around low and high-mass protostars these COMs have fractional abundances of a few percent of (cite: 2020A&A...635A..48M; 2020A&A...639A..87V; 2023arXiv230802688C). The higher abundances we see in the Class II disks may simply be due to an underestimated column density due to optically thick and beam diluted line emission. Deeper observations to target isotopologues are needed to test this. Otherwise, if these high ratios are confirmed, these results reflect a different chemistry than is traced in observations of protostars. Similarly, the abundance ratio of to has been shown to be remarkably constant across different evolutionary stages of star formation (cite: 2020A&A...641A..54C; 2023arXiv230802688C). This ratio of $\approx$1 is also seen in IRS 48 but not for HD 100546 where we find a ratio $\gtrsim$7. is an isomer of acetaldehyde () and vinyl alcohol () both of which are undetected in our data. is typically the most abundant of these isomers by at least an order of magnitude: for example, observations of IRAS 16293-2422 find that is $\approx$10$\times$ more abundant than and relative to is $\approx$0.05% (cite: 2017A&A...597A..53L; 2020A&A...635A..48M) whereas, in IRS 48, / $\lesssim$1.

The high abundance ratios of COMs with respect to that we have observed so far in Class II disks and the variation in and ratios between sources could be the result of the energetic processing of ices in disks. Over the millions of years that ices are present in disks they will be exposed to UV photons, X-ray and cosmic rays - especially if vertical mixing is prominent. These energetic processes can break apart ice resulting in radicals (, , ) that can combine to form the more complex species , and (cite: 2009A&A...504..891O). The specific branching ratios for these radicals will play a key role in setting the new COMs ice abundances (cite: 2011ApJ...728...71L; 2014FaDi..168..389W). has been shown to form in the solid state via the reaction of and O where (cite: 2019ApJ...874..115B) find a branching ratio of 0.5 for relative to . Given the upper limit on in the IRS 48 disk this may indicate that the formation of COMs via oxygen insertion reactions is also important. Finally, there may also be a non-negligible contribution from gas-phase reactions in the inner disk where the gas is warm $>$100 K, UV irradiated and at a significantly higher density than in protostellar envelopes. This needs to be tested with astrochemical models which we leave to further work. Additionally, a larger sample of disks is needed to understand the spread of COMs abundances in disks and better place IRS 48 in context. Upper limits on other COMs lines covered in these data and deuterated isotopes, e.g. , in the IRS 48 disk, will be investigated in Kipfer et al. (in prep) where a further, more complete, comparison to proto-stellar environments and comets will be made.

# Conclusion

This paper is the second in a series presenting an ALMA molecular line survey towards the disks around the Herbig Ae stars HD 100546 and IRS 48. Here we focus on the IRS 48 disk where we detect 16 different molecular species and our main results are as follows:

- We report the first robust detections of , , and in protoplanetary disks and confirm the reported tentative detection of from (cite: 2022A&A...659A..29B) and is clearly seen. We also detect the simple molecules , and CS in the IRS 48 disk for the first time.

- The IRS 48 disk hosts an extremely asymmetric dust trap in the south of the disk. We find that all the molecular lines detected aside from CO show emission in the same region of the disk as the dust trap, including the simple molecules , and CS.

- The asymmetric molecular emissions from the different molecules are not all co-spatial. There are radial and azimuthal offsets in the peak position most clearly seen between the COMs and the SO and . This warrants further investigation of the chemistry in turbulent vortices.

- The low relative abundance of in IRS 48 is similar to the other Herbig disks HD 100546 and HD 142527, which could reflect the star’s lower X-ray luminosity when compared to other sources. Similar to regions of the HD 100546 disk, the CN/HCN ratio in IRS 48 is low $<$1, where the lack of CN may also be due to the low C/O ratio in the IRS 48 disk gas (cite: 2023arXiv230300768L). This is distinct from the elemental make up in the other Herbig Ae disks HD 163296 and MWC 480.

- CS and HCN are the only molecules detected in the IRS 48 disk without oxygen and the low CS/SO ratio and the non-detection of support the bulk of the gas in south of the IRS 48 disk having a C/O$<$1. In these data there is no evidence of an enhanced C/O$>$1 in the non-dust trap region of the disk. Further more, the partition of volatile S between SO, and CS and, the non-detected OCS and is distinct to that measured for comets and protostars with OCS/SO $<$0.3%.

- IRS 48 hosts the most chemically complex disk to date and the high abundances of COMs relative to when compared to protostars as well as the different relative COMs ratios may indicate processing of the inherited ices in protoplanetary disks. The apparently high column density ratios of COMs to needs to be confirmed via observations of optically thin tracers of . i.e., the isotopologues.

Our results solidify the IRS 48 disk as a unique astrochemical laboratory to study the full volatile reservoir available during planet formation and show the benefits of large unbiased surveys of protoplanetary disks. The clear association of the molecular emissions with the dust trap shows a strong coupling between the dust and ice chemistry. Nine different molecules have been detected for the first time in the IRS 48 disk in only two ALMA observing programs (2017.1.00834.S, 2021.1.00738) with just $\approx$10 hours of on-source time. The efficiency of these types of observations will improve dramatically with the planned Wideband Sensitivity Upgrade for ALMA which will increase both the simultaneously observable bandwidth and the imaging speed (cite: 2023pcsf.conf..304C).

# Acknowledgements

This paper makes use of the following ALMA data: 2021.1.00738S. We acknowledge assistance from Allegro, the European ALMA Regional Centre node in the Netherlands. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work has used the following additional software packages that have not been referred to in the main text: Astropy, IPython, Jupyter, Matplotlib and NumPy (cite: Astropy; IPython; Jupyter; Matplotlib; NumPy). Astrochemistry in Leiden is supported by funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 101019751 MOLDISK). A.S.B. is supported by a Clay Postdoctoral Fellowship from the Smithsonian Astrophysical Observatory. M.L. acknowledges support from grant 618.000.001 from the Dutch Research Council (NWO). J.I.D. acknowledges support from an STFC Ernest Rutherford Fellowship (ST/W004119/1) and a University Academic Fellowship from the University of Leeds. M.T. acknowledges support from the ERC grant 101019751 MOLDISK. C.W. acknowledges financial support from the University of Leeds, the Science and Technology Facilities Council, and UK Research and Innovation (grant numbers ST/X001016/1 and MR/T040726/1). L.E. acknowledges financial support from the Science and Technology Facilities Council (grant number ST/T000287/1). S.N. is grateful for support from RIKEN Special Postdoctoral Researcher Program (Fellowships), Grants-in-Aid for JSPS (Japan Society for the Promotion of Science) Fellows Grant Number JP23KJ0329, and MEXT/JSPS Grants-in-Aid for Scientific Research (KAKENHI) Grant Numbers JP 18H05441, JP20K22376, JP20H05845, JP20H05847, JP23K13155, and JP23H05441. Support for C.J.L. was provided by NASA through the NASA Hubble Fellowship grant No. HST-HF2-51535.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555.

natexlab

(ref: 2021ApJS..257...13A) Aikawa, Y., Cataldi, G., Yamato, Y., et al. 2021, ApJS, 257, 13, doi: [`10.3847/1538-4365/ac143c`](http://doi.org/10.3847/1538-4365/ac143c)

(ref: Astropy) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: 2019ApJ...874..115B) Bergner, J. B., Öberg, K. I., & Rajappan, M. 2019, ApJ, 874, 115, doi: [`10.3847/1538-4357/ab07b2`](http://doi.org/10.3847/1538-4357/ab07b2)

(ref: 2022ApJ...941...32B) Boogert, A. C. A., Brewer, K., Brittain, A., & Emerson, K. S. 2022, ApJ, 941, 32, doi: [`10.3847/1538-4357/ac9b4a`](http://doi.org/10.3847/1538-4357/ac9b4a)

(ref: Booth2023_hd100546) Booth, A., Leemker, M., & et al. 2024, submitted AJ

(ref: Booth2023) Booth, A. S., Law, C. J., Temmink, M., Leemker, M., & Macias, E. 2023, arXiv e-prints, arXiv:2308.07910, doi: [`10.48550/arXiv.2308.07910`](http://doi.org/10.48550/arXiv.2308.07910)

(ref: 2021A&A...651L...6B) Booth, A. S., van der Marel, N., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021a, A&A, 651, L6, doi: [`10.1051/0004-6361/202141057`](http://doi.org/10.1051/0004-6361/202141057)

(ref: 2019ApJ...882L..31B) Booth, A. S., Walsh, C., Ilee, J. D., et al. 2019, ApJL, 882, L31, doi: [`10.3847/2041-8213/ab3645`](http://doi.org/10.3847/2041-8213/ab3645)

(ref: 2021NatAs...5..684B) Booth, A. S., Walsh, C., Terwisscha van Scheltinga, J., et al. 2021b, Nature Astronomy, 5, 684, doi: [`10.1038/s41550-021-01352-w`](http://doi.org/10.1038/s41550-021-01352-w)

(ref: 2012ApJ...744..116B) Brown, J. M., Herczeg, G. J., Pontoppidan, K. M., & van Dishoeck, E. F. 2012, ApJ, 744, 116, doi: [`10.1088/0004-637X/744/2/116`](http://doi.org/10.1088/0004-637X/744/2/116)

(ref: Bruderer2014) Bruderer, S., van der Marel, N., van Dishoeck, E. F., & van Kempen, T. A. 2014a, A&A, 562, A26, doi: [`10.1051/0004-6361/201322857`](http://doi.org/10.1051/0004-6361/201322857)

(ref: 2014A&A...562A..26B) —. 2014b, A&A, 562, A26, doi: [`10.1051/0004-6361/201322857`](http://doi.org/10.1051/0004-6361/201322857)

(ref: 2022A&A...659A..29B) Brunken, N. G. C., Booth, A. S., Leemker, M., et al. 2022, A&A, 659, A29, doi: [`10.1051/0004-6361/202142981`](http://doi.org/10.1051/0004-6361/202142981)

(ref: 2016MNRAS.462S.253C) Calmonte, U., Altwegg, K., Balsiger, H., et al. 2016, MNRAS, 462, S253, doi: [`10.1093/mnras/stw2601`](http://doi.org/10.1093/mnras/stw2601)

(ref: 2019A&A...623A.124C) Carney, M. T., Hogerheijde, M. R., Guzmán, V. V., et al. 2019, A&A, 623, A124, doi: [`10.1051/0004-6361/201834353`](http://doi.org/10.1051/0004-6361/201834353)

(ref: 2023pcsf.conf..304C) Carpenter, J., Brogan, C., Iono, D., & Mroczkowski, T. 2023, in Physics and Chemistry of Star Formation: The Dynamical ISM Across Time and Spatial Scales, 304, doi: [`10.48550/arXiv.2211.00195`](http://doi.org/10.48550/arXiv.2211.00195)

(ref: 2022A&A...657A.100C) Cazaux, S., Carrascosa, H., Muñoz Caro, G. M., et al. 2022, A&A, 657, A100, doi: [`10.1051/0004-6361/202141861`](http://doi.org/10.1051/0004-6361/202141861)

(ref: 2023arXiv230802688C) Chen, Y., van Gelder, M. L., Nazari, P., et al. 2023, arXiv e-prints, arXiv:2308.02688, doi: [`10.48550/arXiv.2308.02688`](http://doi.org/10.48550/arXiv.2308.02688)

(ref: 2020A&A...641A..54C) Coletta, A., Fontani, F., Rivilla, V. M., et al. 2020, A&A, 641, A54, doi: [`10.1051/0004-6361/202038212`](http://doi.org/10.1051/0004-6361/202038212)

(ref: 2020ApJ...896L...3D) De Simone, M., Ceccarelli, C., Codella, C., et al. 2020, ApJL, 896, L3, doi: [`10.3847/2041-8213/ab8d41`](http://doi.org/10.3847/2041-8213/ab8d41)

(ref: 2018MNRAS.476.4949D) Drozdovskaya, M. N., van Dishoeck, E. F., Jørgensen, J. K., et al. 2018, MNRAS, 476, 4949, doi: [`10.1093/mnras/sty462`](http://doi.org/10.1093/mnras/sty462)

(ref: 2016JMoSp.327...95E) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95, doi: [`10.1016/j.jms.2016.03.005`](http://doi.org/10.1016/j.jms.2016.03.005)

(ref: 2020ApJ...904...11F) Ferrero, S., Zamirri, L., Ceccarelli, C., et al. 2020, ApJ, 904, 11, doi: [`10.3847/1538-4357/abb953`](http://doi.org/10.3847/1538-4357/abb953)

(ref: Follette2015) Follette, K. B., Grady, C. A., Swearingen, J. R., et al. 2015, ApJ, 798, 132, doi: [`10.1088/0004-637X/798/2/132`](http://doi.org/10.1088/0004-637X/798/2/132)

(ref: 2009A&A...505..629F) Fuchs, G. W., Cuppen, H. M., Ioppolo, S., et al. 2009, A&A, 505, 629, doi: [`10.1051/0004-6361/200810784`](http://doi.org/10.1051/0004-6361/200810784)

(ref: 2022ApJ...926..148F) Furuya, K., Tsukagoshi, T., Qi, C., et al. 2022, ApJ, 926, 148, doi: [`10.3847/1538-4357/ac45ff`](http://doi.org/10.3847/1538-4357/ac45ff)

(ref: Gaia2018) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1, doi: [`10.1051/0004-6361/201833051`](http://doi.org/10.1051/0004-6361/201833051)

(ref: 2021A&A...650A.182G) Guzmán-Dı́az, J., Mendigutı́a, I., Montesinos, B., et al. 2021, A&A, 650, A182, doi: [`10.1051/0004-6361/202039519`](http://doi.org/10.1051/0004-6361/202039519)

(ref: 2023arXiv230800343H) Hänni, N., Altwegg, K., Baklouti, D., et al. 2023, arXiv e-prints, arXiv:2308.00343, doi: [`10.48550/arXiv.2308.00343`](http://doi.org/10.48550/arXiv.2308.00343)

(ref: NumPy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: 2009ARA&A..47..427H) Herbst, E., & van Dishoeck, E. F. 2009, ARA&A, 47, 427, doi: [`10.1146/annurev-astro-082708-101654`](http://doi.org/10.1146/annurev-astro-082708-101654)

(ref: Matplotlib) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: 2001ApJ...560..792I) Ikeda, M., Ohishi, M., Nummelin, A., et al. 2001, ApJ, 560, 792, doi: [`10.1086/322957`](http://doi.org/10.1086/322957)

(ref: Kama2016twhya) Kama, M., Bruderer, S., van Dishoeck, E. F., et al. 2016, A&A, 592, A83, doi: [`10.1051/0004-6361/201526991`](http://doi.org/10.1051/0004-6361/201526991)

(ref: Jupyter) Kluyver, T., Ragan-Kelley, B., Pérez, F., et al. 2016, in Positioning and Power in Academic Publishing: Players, Agents and Agendas, ed. F. Loizides & B. Schmidt, IOS Press, 87 – 90

(ref: 2019A&A...624A.108L) Laas, J. C., & Caselli, P. 2019, A&A, 624, A108, doi: [`10.1051/0004-6361/201834446`](http://doi.org/10.1051/0004-6361/201834446)

(ref: 2011ApJ...728...71L) Laas, J. C., Garrod, R. T., Herbst, E., & Widicus Weaver, S. L. 2011, ApJ, 728, 71, doi: [`10.1088/0004-637X/728/1/71`](http://doi.org/10.1088/0004-637X/728/1/71)

(ref: 2021ApJS..257...12L) Le Gal, R., Öberg, K. I., Teague, R., et al. 2021, ApJS, 257, 12, doi: [`10.3847/1538-4365/ac2583`](http://doi.org/10.3847/1538-4365/ac2583)

(ref: 2023arXiv230300768L) Leemker, M., Booth, A. S., van Dishoeck, E. F., et al. 2023, arXiv e-prints, arXiv:2303.00768, doi: [`10.48550/arXiv.2303.00768`](http://doi.org/10.48550/arXiv.2303.00768)

(ref: 2023A&A...676A..80L) Ligterink, N. F. W., & Minissale, M. 2023, A&A, 676, A80, doi: [`10.1051/0004-6361/202346436`](http://doi.org/10.1051/0004-6361/202346436)

(ref: 2018ApJ...859..131L) Loomis, R. A., Cleeves, L. I., Öberg, K. I., et al. 2018a, ApJ, 859, 131, doi: [`10.3847/1538-4357/aac169`](http://doi.org/10.3847/1538-4357/aac169)

(ref: Loomis2018) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2018b, AJ, 155, 182, doi: [`10.3847/1538-3881/aab604`](http://doi.org/10.3847/1538-3881/aab604)

(ref: 2017A&A...597A..53L) Lykke, J. M., Coutens, A., Jørgensen, J. K., et al. 2017, A&A, 597, A53, doi: [`10.1051/0004-6361/201629180`](http://doi.org/10.1051/0004-6361/201629180)

(ref: 2020A&A...635A..48M) Manigand, S., Jørgensen, J. K., Calcutt, H., et al. 2020, A&A, 635, A48, doi: [`10.1051/0004-6361/201936299`](http://doi.org/10.1051/0004-6361/201936299)

(ref: 2012A&A...544A..78M) Meeus, G., Montesinos, B., Mendigutı́a, I., et al. 2012, A&A, 544, A78, doi: [`10.1051/0004-6361/201219225`](http://doi.org/10.1051/0004-6361/201219225)

(ref: 2022ESC.....6..597M) Minissale, M., Aikawa, Y., Bergin, E., et al. 2022, ACS Earth and Space Chemistry, 6, 597, doi: [`10.1021/acsearthspacechem.1c00357`](http://doi.org/10.1021/acsearthspacechem.1c00357)

(ref: 2009A&A...504..891O) Öberg, K. I., Garrod, R. T., van Dishoeck, E. F., & Linnartz, H. 2009, A&A, 504, 891, doi: [`10.1051/0004-6361/200912559`](http://doi.org/10.1051/0004-6361/200912559)

(ref: 2015Natur.520..198O) Öberg, K. I., Guzmán, V. V., Furuya, K., et al. 2015, Nature, 520, 198, doi: [`10.1038/nature14276`](http://doi.org/10.1038/nature14276)

(ref: IPython) Pérez, F., & Granger, B. E. 2007, Computing in Science and Engineering, 9, 21, doi: [`10.1109/MCSE.2007.53`](http://doi.org/10.1109/MCSE.2007.53)

(ref: 1998JQSRT..60..883P) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883, doi: [`10.1016/S0022-4073(98)00091-0`](http://doi.org/10.1016/S0022-4073(98)00091-0)

(ref: 2013ApJ...769...21S) Salyk, C., Herczeg, G. J., Brown, J. M., et al. 2013, ApJ, 769, 21, doi: [`10.1088/0004-637X/769/1/21`](http://doi.org/10.1088/0004-637X/769/1/21)

(ref: 2022ApJ...931L..33S) Santos, J. C., Chuang, K.-J., Lamberts, T., et al. 2022, ApJL, 931, L33, doi: [`10.3847/2041-8213/ac7158`](http://doi.org/10.3847/2041-8213/ac7158)

(ref: 2011ApJS..196...25S) Semenov, D., & Wiebe, D. 2011, ApJS, 196, 25, doi: [`10.1088/0067-0049/196/2/25`](http://doi.org/10.1088/0067-0049/196/2/25)

(ref: 2023A&A...675A.131T) Temmink, M., Booth, A. S., van der Marel, N., & van Dishoeck, E. F. 2023, A&A, 675, A131, doi: [`10.1051/0004-6361/202346272`](http://doi.org/10.1051/0004-6361/202346272)

(ref: 2021A&A...651L...5V) van der Marel, N., Booth, A. S., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021a, A&A, 651, L5, doi: [`10.1051/0004-6361/202141051`](http://doi.org/10.1051/0004-6361/202141051)

(ref: vanderMarel2016-isot) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2016, A&A, 585, A58, doi: [`10.1051/0004-6361/201526988`](http://doi.org/10.1051/0004-6361/201526988)

(ref: vanderMarel2013) —. 2013a, Science, 340, 1199, doi: [`10.1126/science.1236770`](http://doi.org/10.1126/science.1236770)

(ref: 2013Sci...340.1199V) —. 2013b, Science, 340, 1199, doi: [`10.1126/science.1236770`](http://doi.org/10.1126/science.1236770)

(ref: 2021AJ....161...33V) van der Marel, N., Birnstiel, T., Garufi, A., et al. 2021b, AJ, 161, 33, doi: [`10.3847/1538-3881/abc3ba`](http://doi.org/10.3847/1538-3881/abc3ba)

(ref: 2020A&A...639A..87V) van Gelder, M. L., Tabone, B., Tychoniec, Ł., et al. 2020, A&A, 639, A87, doi: [`10.1051/0004-6361/202037758`](http://doi.org/10.1051/0004-6361/202037758)

(ref: 2018A&A...620A.128V) Vioque, M., Oudmaijer, R. D., Baines, D., Mendigutı́a, I., & Pérez-Martı́nez, R. 2018, A&A, 620, A128, doi: [`10.1051/0004-6361/201832870`](http://doi.org/10.1051/0004-6361/201832870)

(ref: 2017A&A...607A.114W) Walsh, C., Daley, C., Facchini, S., & Juhász, A. 2017, A&A, 607, A114, doi: [`10.1051/0004-6361/201731334`](http://doi.org/10.1051/0004-6361/201731334)

(ref: 2014FaDi..168..389W) Walsh, C., Herbst, E., Nomura, H., Millar, T. J., & Weaver, S. W. 2014a, Faraday Discussions, 168, 389, doi: [`10.1039/C3FD00135K`](http://doi.org/10.1039/C3FD00135K)

(ref: 2014ApJ...791L...6W) Walsh, C., Juhász, A., Pinilla, P., et al. 2014b, ApJL, 791, L6, doi: [`10.1088/2041-8205/791/1/L6`](http://doi.org/10.1088/2041-8205/791/1/L6)

(ref: 2016ApJ...823L..10W) Walsh, C., Loomis, R. A., Öberg, K. I., et al. 2016, ApJL, 823, L10, doi: [`10.3847/2041-8205/823/1/L10`](http://doi.org/10.3847/2041-8205/823/1/L10)

(ref: 2012MNRAS.425.1264W) Ward, M. D., Hogg, I. A., & Price, S. D. 2012, MNRAS, 425, 1264, doi: [`10.1111/j.1365-2966.2012.21520.x`](http://doi.org/10.1111/j.1365-2966.2012.21520.x)

(ref: Watanabe2002) Watanabe, N., & Kouchi, A. 2002, ApJL, 571, L173, doi: [`10.1086/341412`](http://doi.org/10.1086/341412)

(ref: 2018ApJ...853..113W) Weaver, E., Isella, A., & Boehler, Y. 2018, ApJ, 853, 113, doi: [`10.3847/1538-4357/aaa481`](http://doi.org/10.3847/1538-4357/aaa481)

(ref: 1999RPPh...62..143W) Wilson, T. L. 1999, Reports on Progress in Physics, 62, 143, doi: [`10.1088/0034-4885/62/2/002`](http://doi.org/10.1088/0034-4885/62/2/002)

(ref: 2023A&A...670A.154W) Wölfer, L., Facchini, S., van der Marel, N., et al. 2023, A&A, 670, A154, doi: [`10.1051/0004-6361/202243601`](http://doi.org/10.1051/0004-6361/202243601)

(ref: 2023ApJ...948L...2Y) Yang, H., Fernández-López, M., Li, Z.-Y., et al. 2023, ApJL, 948, L2, doi: [`10.3847/2041-8213/acccf8`](http://doi.org/10.3847/2041-8213/acccf8)

(ref: 2021ApJS..257....5Z) Zhang, K., Booth, A. S., Law, C. J., et al. 2021, ApJS, 257, 5, doi: [`10.3847/1538-4365/ac1580`](http://doi.org/10.3847/1538-4365/ac1580)

# Observational set-up of IRS 48

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Setting | Date | No. Antenna$^{*}$ | Integration Time | Baselines | Mean PVW | MRS | Phase | Flux/Bandpass |  |
|  |  |  | (mins) | \(m\) | \(mm\) | (") | Calibrator | Calibrator |  |
| A | 30-05-2022 | 43 | 69 | 15.1-783.5 | 1.0 | 4.0 | J1626-2951 | J1517-2422 |  |
|  | 08-06-2022 | 41 | 72 | 15.1-783.5 | 0.6 | 3.9 | J1626-2951 | J1427-4206 |  |
|  | 08-06-2022 | 39 | 70 | 15.1-783.5 | 0.5 | 3.6 | J1626-2951 | J1427-4206 |  |
| B | 28-05-2022 | 45 | 73 | 15.1-783.5 | 1.2 | 3.6 | J1626-2951 | J1517-2422 |  |
|  | 28-05-2022 | 44 | 57 | 15.1-783.5 | 0.9 | 3.6 | J1626-2951 | J1517-2422 |  |
|  | 28-05-2022 | 43 | 73 | 15.1-783.5 | 0.9 | 4.0 | J1626-2951 | J1517-2422 |  |
|  | 29-05-2022 | 44 | 73 | 15.1-783.5 | 1.4 | 3.9 | J1626-2951 | J1517-2422 |  |
|  | 30-05-2022 | 43 | 73 | 15.1-783.5 | 0.9 | 4.1 | J1626-2951 | J1517-2422 |  |
|  |  |  |  |  |  |  |  |  |  |

: Execution block details. $^{*}$ Number of antenna after flagging.

# Molecular Data

c c c c c c c

\
Molecule & Transition & Frequency (GHz) & E$_{\mathrm{up}}$ (K) & log10($\mathrm{A_{ul}}$) & $\mathrm{g_{u}}$ & Detection\
& $J=3-2$ & 345.7959899 & 33.2 & -5.6027 & 7 &\
& $J=3-2$ & 337.0611298 & 32.7 & -5.6344 & 7 &\
& $J=4-3$ & 356.7342230 & 42.8 & -2.4471 & 9 &\
& $J=4-3$ & 354.5054779 & 42.5 & -2.6860 & 27 &\
& $J=4-3$ & 345.3397693 & 41.4 & -2.7216 & 27 & -\
& $J=4-3$ & 344.2001089 & 41.3 & -2.7258 & 9 &-\
CN & $J=7/2-5/2, F=7/2-5/2$ & 340.2477700 & 32.7 & -3.3839 & 10 & -\
& $J=7/2-5/2, F=7/2-5/2$ & 340.2477700 & 32.7 & -3.4206 & 8 & -\
& $J=7/2-5/2, F=5/2-3/2$ & 340.2485440 & 32.7 & -3.4347 & 6 & -\
& $J=7/2-5/2$,$\Omega=1/2- F=9/2-7/2$ & 351.0435240 & 36.1 & -5.2649 & 10 &\
& $J=7/2-5/2$,$\Omega=1/2- F=7/2-5/2$ & 351.0517050 & 36.1 & -5.2662 & 8 &\
& $J=7/2-5/2$, $\Omega=1/2- F=7/2-5/2$ & 351.0517050 & 36.1 & -5.3161 & 6 &\
& $J=38-37$ & 345.6090100 & 323.5 & -2.4812 & 77 & -\
& $J=39-38$ & 354.6974631 & 340.5 & -2.4473 & 79 & -\
& $J=19_0-18_0$& 349.4536999 & 167.7 & -2.5909 & 78 & -\
& $J=9/2-7/2,F=5-4$ & 349.3374558 & 41.9 & -3.7247 & 11 &\
& $J=9/2-7/2,F=4-3$ & 349.3387284 & 41.9 & -3.7349 & 9 &\
& $J=7-6$ & 342.8828503 & 65.8 & -3.0774 & 15 &\
& $J=10_{(1,10)}-9_{(1,9)}$ & 338.0831953 & 102.4 & -3.1995 & 63 & -\
& $J=3_3-3_2$ & 339.3414590 & 25.5 & -4.8372 & 7 &\
& $J=7_8-6_7$ & 340.7141550 & 81.2 & -3.3023 & 15 &\
& $J=8_8-7_7$ & 344.3106120 & 87.5 & -3.2852 & 17 &\
& $J=8_8-7_7$ & 337.5801467 & 77.3 & -3.3109 & 17 &\
& $J=9_8-8_7$ & 339.8572694 & 86.1 & -3.2944 & 19 &\
&$J=9_8-8_7$ $F=21/2-19/2$ & 343.0882949 & 78.0 & -3.2819 & 22&\
&$J=9_8-8_7$ $F=19/2-17/2$ & 343.0880780 & 78.0 & -3.2896 & 20&\
&$J=9_8-8_7$ $F=17/2-15/2$ & 343.0861019 & 78.0 & -3.2934 & 18 &\
&$J=9_8-8_7$ $F=15/2-13/2$ & 343.0872979 & 78.0 & -3.2916 & 16 &\
&$J=7_8-6_7$ $F=17/2-15/2$ & 337.1986199 & 80.5 & -3.3158 & 18&\
&$J=7_8-6_7$ $F=15/2-13/2$ & 337.1978453 & 80.5 & -3.3283 & 16&\
&$J=7_8-6_7$ $F=13/2-11/2$ & 337.1980219 & 80.5 & -3.3351 & 14&\
&$J=7_8-6_7$ $F=11/2-9/2$ & 337.1993711 & 80.5 & -3.3328 & 12 &\
& $J=6_{(4,2)}-6_{(3,3)}$ & 357.9258478 & 58.6 & -3.5845 & 13 &\
& $J=28-27$ & 340.4492733 & 237.0 & -3.9378 & 57 & -\
& $J=29-28$ & 352.5995703 & 253.9 & -3.8918 & 59 & -\
& $J=5_{(1,5)}-4_{(1,4)}$ & 351.7686450 & 62.5 & -2.9201 & 33 &\
& $J=5_{(1,5)}-4_{(1,4)}$ & 343.3257130 & 61.3 & -2.9517 & 33 &\
& $J=7_{0}-6_{0}$ & 338.4086980& 65.0 & -3.7691 & 60 &\
& $J=32_{(2,31)}-31_{(2,30)}$ & 344.0297653 &276.1 & -3.2099& 65 &\
& $J=32_{(1,32)}-31_{(1,31)}$ & 344.0297645&276.1&-3.2099 & 65 &\
&$J=32_{(0,32)}-31_{(0,31)}$ & 344.0295703 &276.1 & -3.2099& 65 &\
& $J=32_{(1,32)}-31_{(1,31)}$ & 344.0295694 &276.1&-3.2099 & 65 &\
& $J=19_{(0,19)}-18_{(1,18)}$ AE & 342.6080601 &167.1& -3.2816 & 117 &\
& $J=19_{(0,19)}-18_{(1,18)}$ EA & 342.6080602& 167.1& -3.2817& 78 &\
& $J=19_{(0,19)}-18_{(1,18)}$ EE & 342.6081188 &167.1 & -3.2816 & 312 &\
& $J=19_{(0,19)}-18_{(1,18)}$ AA & 342.6081774 &167.1 & -3.2816 & 195 &\
& $J=18_{(3,15)}-17_{(3,14)}$ A & 350.1334296 & 179.2& -2.82551&74 & -\
& $J=18_{(3,15)}-17_{(3,14)}$ E & 350.1343816 & 179.2& -2.82596&74 & -\
& $J=11_{(1,10)}-10_{(2,9)}$ (ortho) &338.77197600 & 104.0 & -3.19217 & 69 &\
&$J=11_{(1,10)}-10_{(2,9)}$ (para) &338.77197600 & 104.0& -3.19212 & 115 &\

# Image properties

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | robust | Beam | rms | Peak | Int. Flux |  |  |
|  |  |  | ($\ensuremath{''} \times \ensuremath{''}$ ($^{\circ}$)) | (mJy beam $^{-1}$) | (mJy beam $^{-1}$) | (mJy beam km s$^{-1}$) |  |  |
|  | $J=3-2$ | 0.5 | 0.34$\times$0.26 (-85.3) | 0.94 | 662.4 | $>$25334.0 |  |  |
|  | $J=3-2$ | 0.5 | 0.34$\times$0.28 (-89.6) | 1.2 | 19.2 | 328.0$\pm$20.0 |  |  |
|  | $J=4-3$ | 0.5 | 0.33$\times$0.26 (-84.1) | 1.19 | 30.8 | 529.0$\pm$21.0 |  |  |
|  | $J=4-3$ | 0.5 | 0.33$\times$0.26 (-84.8) | 1.04 | 29.5 | 400.0$\pm$18.0 |  |  |
|  | $J=4-3$ | 0.5 | 0.34$\times$0.26 (-85.2) | 0.92 | \- | $<$48.0 |  |  |
|  | $J=4-3$ | 0.5 | 0.34$\times$0.27 (-84.4) | 0.99 | \- | $<$50.0 |  |  |
|  | $N=4-3$ | 0.5 | 0.34$\times$0.27 (87.9) | 1.03 | \- | $<$52.0 |  |  |
|  | $J=38-37$ | 0.5 | 0.34$\times$0.26 (-85.2) | 0.94 | \- | $<66.0$ |  |  |
|  | $J=39-38$ | 0.5 | 0.33$\times$0.26 (-84.7) | 1.04 | \- | $<75.0$ |  |  |
|  | $J=19_0=18_0$ | 0.5 | 0.33$\times$0.26 (-89.3) | 1.05 | \- | $<$75.0 |  |  |
|  | $J=7/2-5/2$ | 0.5 | 0.33$\times$0.26 (-89.9) | 1.08 | 8.16 | 127.0$\pm$25.0 |  |  |
|  | $N=4-3$ | 0.5 | 0.33$\times$0.26 (-89.4) | 1.02 | \- | $<$53.0 |  |  |
|  | $J=7-6$ | 0.5 | 0.34$\times$0.27 (-84.4) | 1.03 | 5.82 | 40$\pm$17.0 |  |  |
|  | $J=10_{(1,10)}-9_{(1,9)}$ | 0.5 | 0.34$\times$0.27 (-89.3) | 1.16 | \- | $<$58.0 |  |  |
|  | $J=3_3-3_2$ | 0.5 | 0.34$\times$0.27 (87.9) | 0.79 | 87.60 | 1070.0$\pm$13.0 |  |  |
|  | $J=7_8-6_7$ | 0.5 | 0.34$\times$0.27 (-85.3) | 1.0 | 84.96 | 1063.0$\pm$23.0 |  |  |
|  | $J=8_8-7_7$ | 0.5 | 0.34$\times$0.27 (88.2) | 1.05 | 27.85 | 232.0$\pm$24.0 |  |  |
|  | $J=8_8-7_7$ | 0.5 | 0.34$\times$0.27 (88.0) | 0.98 | 28.81 | 251.00$\pm$22.0 |  |  |
|  | $J=9_8-8_7$ | 0.5 | 0.34$\times$0.27 (-89.4) | 1.13 | 23.93 | 187.0$\pm$26.0 |  |  |
|  | $J=7_8-6_7$ | 0.5 | 0.34$\times$0.27 (-84.5) | 1.0 | 10.64 | 115.0$\pm$23.0 |  |  |
|  | $J=9_8-8_7$ | 0.5 | 0.34$\times$0.28 (-89.5) | 1.15 | 8.60 | 60.0$\pm$20.0 |  |  |
|  | $J=6_{(4,2)}-6_{(3,3)}$ | 0.5 | 0.33$\times$0.26 (-84.2) | 0.88 | 26.83 | 261.0$\pm$15.0 |  |  |
|  | $J=28-27$ | 0.5 | 0.34$\times$0.27 (88.0) | 0.98 | \- | $<$67.0 |  |  |
|  | $J=27-26$ | 0.5 | 0.33$\times$0.26 (-90.0) | 1.42 | \- | $<$101 |  |  |
|  | $J=5_{(1,5)}-4_{(1,4)}$ | 0.5 | 0.33$\times$0.26 (90.0) | 1.21 | 77.54 | 824.0$\pm$21.0 |  |  |
|  | $J=5_{(1,5)}-4_{(1,4)}$ | 0.5 | 0.34$\times$0.27 (-84.5) | 1.02 | 17.34 | 169.0$\pm$17.0 |  |  |
|  | $J=7_{0}-6_{0}$ | 0.5 | 0.34$\times$0.27 (-89.5) | 1.11 | 19.83 | 182.0$\pm$18.0 |  |  |
|  | $J=31-30$ | 0.5 | 0.34$\times$0.27 (-84.4) | 0.98 | 12.50 | 95.0$\pm$23.0 |  |  |
|  | $J=19-28$ | 0.5 | 0.34$\times$0.27 (-89.6) | 0.82 | 13.14 | 87.0$\pm$23.0 |  |  |
|  | $J=18_{(3,15)}-17_{(3,14)}$ | 0.5 | 0.34$\times$0.27 (-89.7) | 0.79 | \- | $<$75 |  |  |
|  | $J=11_{(1,10)}-10_{(2,9)}$ | 2.0 | 0.37$\times$0.3 (27.7) | 0.77 | 5.70 | $39.0\pm$24 |  |  |

# Full spectrum matched filter response

![](selfcal_matched_filter_irs48.png)

</paper>

Write the methods card for this paper.