# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...971..187A\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...971..187A",
 "title": "High-resolution Study of the Outflow Activity and Chemical Environment of Chamaeleon-MMS1",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Allen, Veronica",
 "n_authors": 6,
 "arxiv_id": "2010.01151",
 "doi": "10.3847/1538-4357/ad5182",
 "alma_projects_linked_by_archive": [
  "2013.1.01113.S"
 ]
}
```

Paper text:
<paper>
# High-resolution study of outflow activity and chemical environment of Chamaeleon-MMS1

## Abstract

The earliest stages of low-mass star-formation are unclear, but it has been proposed that Chamaeleon-MMS1 is a candidate First Hydrostatic Core (FHSC), the transition stage between a prestellar and protostellar core. This work describes the local ($\sim$4000 AU) outflow activity associated with Chamaeleon-MMS1 and its effect on the surrounding material in order to determine the evolutionary state of this young low-mass source. We used the Atacama Large Millimeter/sub-millimeter Array (ALMA) to observe Chamaeleon-MMS1 at 220 GHz at high spatial ($\sim75$ AU) and spectral resolutions (0.1-0.3 km s$^{-1}$). A low energy outflow is detected through its interaction with the surrounding cloud. The outflow consists of two components, a broad spectral feature ($\Delta$v$\sim$8 km s$^{-1}$) to the northeast and narrow spectral features ($\Delta$v$\sim$1 km s$^{-1}$) to both the northeast and southwest. The molecular tracers CS, formaldehyde (H$_2$CO), and methanol (CH$_3$OH) were used to analyze the effect of the outflow on the surrounding gas as well as determine the rotational temperature of this gas. The rotational temperature of H$_2$CO is calculated to be 40 K toward the continuum source with similarly low temperatures (10-75 K) toward clumps affected by the outflow. CH$_3$OH is only detected toward gas clumps located away from the continuum source, where the methanol is expected to have been released by the energy of the outflow through ice sputtering in shock waves. Chamaeleon-MMS1 shows outflow activity with the power source likely being a single precessing outflow. While molecular emission and high outflow speeds rule it out as a FHSC, the outflow is less energetic than outflows detected from other Class 0 objects. The inferred gas temperatures toward the continuum source are also relatively low, indicating that Cha-MMS1 is one of the youngest known sources.

# Introduction

Understanding star formation is a central problem in astrophysics, with direct implications for our understanding of how galaxies evolve and how planets and life form. Stars form in collapsing cores, corresponding to the densest regions within molecular clouds, but the precise details of this process are still far from being completely understood, particularly during the initial collapse period. The numerical hydrodynamic simulations of (cite: Larson1969), more recently by (cite: Masunaga2000), (cite: Machida2008), and (cite: Tomida2010), show that the collapse of a molecular cloud is arrested by thermal pressure once the density (*n*) becomes sufficiently great that cooling by dust radiation is inhibited (at *n* $\gtrsim$ 10$^{11}$ cm$^{-3}$). At this point, a quasi-hydrostatic object is formed, known as the First Hydrostatic Core (FHSC). The FHSC is calculated to persist in an approximately adiabatic state for $\sim$10$^3$ yr, which is a sufficiently short time to make it a rare object in nearby star-forming regions. Observational signatures of the FHSC include a low luminosity ($\sim$0.01-0.1L$_{\odot}$), and an approximately thermal spectral energy distribution that peaks in the far-infrared/sub-mm range (cite: Saigo2011). A low luminosity source is generally considered to be a FHSC candidate if it shows little to no emission at wavelengths $< 70\mu$m. Calculations show that the FHSC should also produce a slow molecular outflow, which extends up to a distance of a few hundred AU from the core (cite: Machida2008; Tomida2010). Typically, slow uncollimated outflows are expected, but (cite: Price2012) demonstrated that collimated jets with velocities up to 7 km s$^{-1}$ are possible during the FHSC phase.

Several FHSC candidates are currently identified. These include L1451-mm (cite: Pineda2011); NGC 1333 - IRAS 4C (cite: Evgenia2016); L1535-NE/MC35-mm (cite: Fujishiro2020); Oph A N6 and Oph A SM1 (cite: Friesen2018); and G208.89-20. (cite: Dutta2022); and perhaps Per-Bolo 45 (cite: MariaJose2020). Distinguishing between an FHSC and a very low luminosity Class 0 protostar (known as a VeLLO) has proven difficult, in part due to a lack of detailed spectro-spatial information on outflow properties. VeLLOs appear to be young, low-mass protostars undergoing episodic accretion, and a number of these were identified by the c2d Spitzer survey of (cite: Dunham2008). The list of very low luminosity protostars includes IRAS 15398-3359 (cite: Okoda2020); L673-7 IRS (cite: Dunham2011); L1014 IRS (cite: Dunham2011); L1148 IRS (cite: Dunham2011); GSS30, SM1N, B2-A7 and IRAS 16267-2417 in Oph A (cite: Friesen2018), as well as sources formerly identified as FHSC candidates: B1b-N (cite: Marcelino2018) and B1b-S (cite: Hirano2019); Per-Bolo 58, L1448 IRS 2E and L1448 IRS 2E (cite: MariaJose2020); CB17-MMS (cite: Spear2021). The physics, chemistry, and observational signatures of FHSCs and VeLLOs have been discussed by (cite: Omukai2007), (cite: Lee2007), and (cite: Young2019). Specifically, CS emission was modeled to exist only in the central few AU around a late-stage FHSC.

Chamaeleon-MMS1 (Cha-MMS1) is a young protostar located at a distance of 192 pc (cite: Dzib2018) with a systemic velocity of 4.5 km s$^{-1}$ (cite: Belloche2006) and was first detected in 1.3 mm emission by (cite: Reipurth1996). The central object is deeply embedded inside a dense molecular cloud (cite: Cordiner2012) and has been classified by (cite: Belloche2006; Belloche2011) as either an extremely young VeLLO or an FHSC with an internal luminosity between 0.08 and 0.18 L$_{\ensuremath{\odot}}$ (cite: Tsitali). (cite: Belloche2006) did not find any evidence of CO outflow activity from Cha-MMS1 using single-dish (APEX) observations, and the studies by (cite: Hiramatsu2007; Ladd2011) determined that the nearby HH 49/50 outflow is driven by the more evolved Class I protostar Ced 110 IRS 4. (cite: Ladd2011) determined from single-dish CO observations that the IRS 4 outflow is deflected around (or grazes the edge of) the 100$''$-diameter dense clump that contains the collapsing protostar Cha-MMS1. (cite: Vaisala2014) analyzed NH$_3$ and continuum emission toward Cha-MMS1 using the Australia Telescope Compact Array (ATCA) and concluded that a warm central source was within, but it was at the Class 0 stage at the latest. Recently, (cite: Busch2020) published an analysis of the CO(3-2) emission tracing outflow activity associated with Cha-MMS1. The outflow in that article is qualitatively similar to the CO(2-1) emission in this work, but we also present the outflow activity as traced by CS, H$_{2}$CO, and CH$_{3}$OH, showing different structures than those traced by the CO observation. Additionally, analysis of multiple FHSC candidates (including Cha-MMS1) using dense envelope tracers was published by (cite: MariaJose2020). Both studies conclude that Cha-MMS1 is at a very young evolutionary state.

In this paper, we present the high-angular resolution analysis of the outflow activity associated with Cha-MMS1 and their effect on the surrounding material. In $\S$[2](#sec:obs), we give details of the ALMA observations and data reduction. $\S$[3](#sec:results) contains the details of five detected species including isotopologs (CO, $^{13}$CO, CS, H$_{2}$CO and CH$_{3}$OH), analysis of the outflow mechanical properties, and determination of the rotational temperature of various sub-regions in this source. $\S$[4](#sec:discuss), we discuss the implications of our results, and in $\S$[5](#sec:conc) we present our conclusions regarding the nature of this extremely young protostellar object.

![](Contmaptclean.pdf)

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Species | Transition | Frequency | E$_{\mathrm{up}}$ | log (A$_{\mathrm{ij}}$) |
|  |  | (GHz) | \(K\) |  |
| CO | 2-1 | 230.5380 | 16.6 | -6.16 |
| $^{13}$CO | 2-1 | 220.3986 | 15.9 | -6.22 |
| CS | 5-4 | 244.9355 | 35.3 | -3.53 |
| H$_2$CO | 3$_{0,3}$-2$_{2,1}$ | 218.2221 | 20.9 | -3.55 |
| H$_2$CO | 3$_{2,2}$-2$_{2,1}$ | 218.4756 | 68.1 | -3.80 |
| H$_2$CO | 3$_{1,2}$-2$_{1,1}$ | 225.6977 | 33.4 | -3.56 |
| CH$_3$OH | 5$_{3,2}$-4$_{3,1}$ | 218.4400 | 45.5 | -4.33 |
| CH$_3$OH | 5$_{-1,5}$-4$_{-1,4}$ | 241.7672 | 40.4 | -4.24 |
| CH$_3$OH | 5$_{0,5}$-4$_{0,4}$++ | 241.7914 | 34.8 | -4.22 |
| HC$_3$N | 24-23 | 218.3247 | 131.0 | -3.08 |

: Targeted spectral lines (E$_{\mathrm{up}}$ and A$_{\mathrm{ij}}$ from CDMS)

![](CObroadredcontourstclean.pdf)

![](COredcontourstcleanAll.pdf)

![](CObluecontourstcleanAll.pdf)

# Observations and data reduction

Cha-MMS1 was observed using the Atacama Large Millimeter/sub-millimeter Array (ALMA) on 16 July 2014 and 6 and 7 June 2015 using 26 antennas on 16 July, and 37-39 antennas on 6 and 7 June (project code 2013.1.01113.S) with an angular resolution of $\sim0.7''$ and spectral resolutions of $\sim$0.08 km s$^{-1}$ in three spectral windows (covering $^{12}$CO, $^{13}$CO and CS), 0.17 km s$^{-1}$ for H$_2$CO (218222 MHz), and 0.3 km s$^{-1}$ in the other four spectral windows. The calibrators used were Callisto, Ganymede, J0635-7516, J1058-8003, J1208-7809, J1107-4449, and J0538-4405. The pointing position of our ALMA observations was the millimeter position reported in (cite: Reipurth1996) rather than the Spitzer IR peak, therefore the source is consistently offset in our maps. Data reduction was performed with the CASA package (version 5.4.0). Corresponding spectral windows from different observation dates were concatenated and the continuum was subtracted. Imaging was done using the tclean process with a Hogbom deconvolver and Briggs weighting with a robust parameter of 0.5 and all images are primary beam corrected. The RMS noise for line-free channels was typically 2-4 mJy.

![](13COredcontourstcleanAll.pdf)

![](13CObluecontourstcleanAll.pdf)

# Results

## Continuum and Line Detection

Figure [1](#Contmap) shows the compact, unresolved continuum emission at 220 GHz detected toward Cha-MMS 1. Our observations targeted several molecular species expected in very young low-mass star-forming regions summarized in Table [1](#linesTable). $^{12}$CO emission is resolved out on large scales, but a weak spectral feature covering the broad velocity range of 8.7-17.1 km s$^{-1}$ is detected in $^{12}$CO to the northeast of the continuum source (§ [3.2.1](#broadoutflow), Figure [2](#CObroadred)). Moment maps were also made of narrow spectral features in $^{12}$CO and $^{13}$CO (§ [3.2.2](#narrowoutflow), Figures [3](#COcontours) and [4](#13COnarrowred)). There is self-absorption in both $^{12}$CO and $^{13}$CO with no signal for each in the ranges 4.0-5.7 km s$^{-1}$ and 4.4-5.1 km s$^{-1}$, respectively. $^{13}$CO shows strong emission towards the continuum source and weak emission (less than 3$\sigma$) cospatial with the narrow red $^{12}$CO emission southwest of the continuum source. CS emission is clumpy and, on larger spatial scales, the CS clumps seem to trace out a cone (§ [3.3](#CS), Figure [6](#CScontours)). Within 1.5$''$ (288 AU) of the continuum source spectral emission of CS shows shows an hourglass-like morphology. Three H$_2$CO lines were detected (§ [3.4](#h2cosec), Figure [15](#H2COcontours)) showing emission in different regions, most of which correspond with the locations of CS emission. Three weak CH$_3$OH transitions were detected at 5- to 10$\sigma$ RMS levels (§ [3.5](#ch3oh)) coinciding with the H$_2$CO emission that is not coincident with the Cha-MMS1 core. The targeted HC$_3$N transition was not detected.

![](COredblueContours.pdf)

![](COredblueContoursInset.pdf)

## Outflow activity

The emission detected in $^{12}$CO was used to determine the properties of outflow activity associated with this source. Both the red and blue lobes of the narrow outflow component are located toward the northeast and southwest of the continuum source with an additional broad red component appearing to the northeast.

### Broad red outflow component

A weak, broad red-shifted outflow is detected to the northeast of the continuum source in $^{12}$CO (Figure [2](#CObroadred)). It is quite collimated with a collimation factor of 5.5. A Gaussian fit made to this component of the $^{12}$CO emission shows that the center is at 10.9$\pm$0.2 km s$^{-1}$ and the full-width half-maximum (FWHM) is 6.7$\pm$0.4 km s$^{-1}$. The blue counterpart to the southwest is not nearly as broad or collimated (see Figure [3](#COcontours) right). A Gaussian fit of the southern blue component has a central velocity of 3.40$\pm$0.01 km s$^{-1}$ and a FWHM of 0.77$\pm$0.03 km s$^{-1}$. This much narrower spectral line may not be the opposite component of the broad red outflow, but no broader blue component was detected. No broad component is detected in $^{13}$CO (Figure [4](#13COnarrowred)).

### Narrow bipolar outflow

The left frames of Figures [3](#COcontours) and [4](#13COnarrowred) show $^{12}$CO and $^{13}$CO integrated intensity maps (between 5.7 and 8.7 km s$^{-1}$ and 5.1 and 6.0 km s$^{-1}$, respectively) of spectrally narrow red-shifted outflow activity to the south of the continuum source which coincide in an ’S’-like shape. The blue components of $^{12}$CO (Figure [3](#COcontours) right) are both to the northeast and southwest at the edges of the field-of-view. These blue components appear to be the ends of the outflow, but as we do not have a larger field-of-view, we cannot confirm. The line profiles of the $^{12}$CO components are narrow at 1.4$\pm$0.1 km s$^{-1}$ (southern red) and 0.72$\pm$0.07 km s$^{-1}$ (northern blue) with central peaks near v$_{LSR}$ of Cha-MMS1 at 6.94$\pm$0.04 km s$^{-1}$ and 3.55$\pm$0.03 km s$^{-1}$. The spectral lines for $^{13}$CO are even narrower at 0.34$\pm$0.02 and 0.35$\pm$0.01 with central peaks at 5.47$\pm$0.01 and 3.565$\pm$0.006 for the red and blue lobes, respectively. All three components of the $^{12}$CO outflow – broad red, narrow red, and narrow blue – are shown in Figure [5](#COallcontours). Details of the spectra across the region can be found in Appendix A in Figures [11](#cospec1) and [12](#cospec2).

|  | Northern Red | Southern Red | Northern Blue | Southern Blue | Calculated |
|:--:|:--:|:--:|:--:|:--:|:--:|
| V$_{\mathrm{max}}$ (km s$^{-1}$) | 12.4 (0.1) | 4.0 (0.1) | 3.2 (0.1) | 2.9 (0.1) | $\dagger$ |
| V$_{\mathrm{dep}}$ (km s$^{-1}$) | 71.8 (0.6) | 23.4 (0.6) | 18.6 (0.6) | 16.8 (0.6) | $\dagger$ |
| t$_{\mathrm{kin}}$ (yr) | 130 (10) | 490 (20) | 720 (20) | 800 (30) | $\dagger$ |
| Outflow mass (M$_{\ensuremath{\odot}}$) | 5.2 (1.0)$\times10^{-5}$ | 7.4 (1.7)$\times10^{-5}$ | 4.7 (0.6)$\times10^{-5}$ | 2.1 (0.1)$\times10^{-4}$ | 2.2-3.5$\times10^{-2}$ |
| Mass-loss rate (M$_{\ensuremath{\odot}}$ yr$^{-1}$) | 4.1 (1.2)$\times10^{-7}$ | 1.5 (0.4)$\times10^{-7}$ | 3.3 (0.7)$\times10^{-7}$ | 3.1 (0.3)$\times10^{-7}$ | $\dagger$ |
| Momentum (M$_{\ensuremath{\odot}}$ km s$^{-1}$) | 3.7 (0.8)$\times10^{-3}$ | 1.7 (0.4)$\times10^{-3}$ | 9.9 (1.2)$\times10^{-4}$ | 9.4 (0.7)$\times10^{-3}$ | $\dagger$ |
| Kinetic Energy (erg) | 2.6 (0.5)$\times10^{42}$ | 4.0 (0.9)$\times10^{41}$ | 1.6 (1.9)$\times10^{41}$ | 5.9 (0.4)$\times10^{41}$ | $\dagger$ |
| Mechanical Luminosity (L$_{\ensuremath{\odot}}$) | 1.1 (2.7)$\times10^{-1}$ | 5.7 (3.1)$\times10^{-3}$ | 2.3 (0.8)$\times10^{-3}$ | 2.4 (0.2)$\times10^{-2}$ | 2.2-3.6$\times10^{-3}$ |
| Momentum rate (M$_{\ensuremath{\odot}}$ km s$^{-1}$ yr$^{-1}$) | 2.9 (0.7)$\times10^{-5}$ | 3.6 (1.4)$\times10^{-6}$ | 1.4 (0.1)$\times10^{-6}$ | 1.1 (0.1)$\times10^{-5}$ | 2.2-4.0$\times10^{-6}$ |

### Mechanical outflow properties

We used the approach described in (cite: AlvaroOutflows) and (cite: AnaOutflows) to calculate the mechanical outflow properties. The measured properties for each outflow lobe are: the difference between the maximum velocity and systemic velocity (v$_{max}$), the length of the major axis (at the 5$\sigma$ contour), the area of the outflow (as an ellipse), and the integrated intensity of the emission between v$_{max}$ and 2$\sigma$ from the line peak ($\int$T$_{mb}$dv). The CO column density was determined assuming optically thin emission as in (cite: Goldsmith1999) equations (10) and (19) assuming excitation temperatures of 10, 20, and 30 K. The calculated CO column densities varied by a factor of 3-4 between the different temperatures, so we used the average for calculating the hydrogen column density (N$_{H2}$) assuming a CO abundance of 10$^{-4}$, as is typical (cite: Bolatto2013). Because the CO emission showed strong self-absorption at velocities near the velocity of the system (v$_{\mathrm{LSR}}$=4.9 km s$^{-1}$), the CO intensities were corrected assuming an $\tau$ value of 5.

The other calculated properties are: outflow mass (calculated using the area of the outflow lobe and the mass of the hydrogen from the calculated H$_2$ column density), the dynamical or kinetic time – t$_{kin}$ (the length of the outflow lobe divided by v$_{max}$), kinetic energy (outflow mass times 0.5 v$_{max}^2$), momentum (outflow mass times v$_{max}$), momentum rate – which is also called the force (momentum/t$_{dyn}$), mass-loss rate (outflow mass/t$_{dyn}$), and mechanical luminosity (kinetic energy/t$_{dyn}$). As the direction of the outflow is near the plane of the sky, we applied the inclination correction factors from (cite: Ana2010) assuming an inclination of 80$^{\circ}$. We determined this inclination geometrically taking into account the opening angle of the northern red outflow and the presence of red and blue components in each direction.

The mechanical outflow properties are summarized in Table [\[outflowTable\]](#outflowTable) for the detected outflow lobes. The fast broad outflow component (northern red) has a maximum relative velocity of $\sim$ 12 km s$^{-1}$ (deprojected to $\sim$ 70 km s$^{-1}$). The narrow components have a maximum velocity of $\sim$4 km s$^{-1}$ (deprojected to $\sim$20 km s$^{-1}$). Using the trends outlined in (cite: Wu2004), we calculated the momentum rate, outflow mass, and mechanical luminosity expected from a young star with a L$_{\mathrm{bol}}$ of 0.08-0.18. The momentum rate would be 2.2-4.0 $\times10^{-6}$ M$_{\ensuremath{\odot}}$ km s$^{-1}$ yr$^{-1}$, the outflow mass 2.2-3.5 $\times10^{-2}$ M$_{\ensuremath{\odot}}$, and the mechanical luminosity 2.2-3.6 $\times10^{-3}$ L$_{\ensuremath{\odot}}$. The outflows described in this paper have a mass 100-1000 times lower, and a momentum rate and mechanical luminosity comparable to the calculated value.

## CS

Figure [6](#CScontours) shows CS emission tracing a wide cone on larger scales, indicating the interaction between multiple outflows and the surroundings or a steep precessing angle of a single outflow. Alternatively, this morphology could be due to a spatially wider and low-velocity component tracing the cavity walls, as is commonly found towards other protostellar outflows. On smaller scales, the CS emission is hourglass-shaped and the first moment (velocity) maps (Figure [7](#CSmom1)) show inverse velocity gradients immediately above and below the continuum source.

![](CStotalcontourstcleanAll.pdf)

![](CSmom1.pdf)

![](CSmom1Zoom.pdf)

## H$_2$CO emission

H$_2$CO emission is detected toward the continuum as well as about 3$''$ ($\sim$600 au) to the south of the continuum source, about 16$''$ (3100 au) southwest of the continuum source, and 7.5$''$ (1500 au) northeast of the continuum source in all three detected transitions. We labeled these regions Main, south (S), west (W), and north (N) (See Figure [8](#H2CO)). The emission from H$_2$CO in these three regions coincides with CS emission in all cases, but does not show the hourglass morphology toward the central source (Main) seen in CS. Cha-MMS1 W corresponds to the southwestern lobe of the CO outflow emission. There is emission detected from the H$_2$CO transition at 218.222 GHz about 10$a ''$ (1900 au) north-northeast of the continuum source, but the emission detected in this area from the other two transitions is very weak. The higher energy H$_2$CO transition at 218.475 GHz (E$_{\mathrm{up}}$=68 K) shows very weak emission in each region (see Appendix A for spectra).

Table [2](#rotdTable) shows the rotational temperatures and column densities determined using the H$_2$CO transitions in a rotational diagram in the CASSIS software[^1] and the CDMS database. Rotational temperatures range from $\sim$25 K to 51 K with a temperature of 51.0 ($\pm$36.2) K toward the continuum source. The column densities are consistently $\sim 10^{13}$ cm$^{-2}$. The gas in these condensations appears to be sufficiently dense for the rotational temperature, gas temperature, and dust temperature to be equal (n$>10^{4.5}~cm^{-3}$ from (cite: Goldsmith2001)). In this case, based on the experimentally-measured sublimation temperature (144 K, (cite: Noble2012)), it is unlikely that the detected H$_2$CO originates in thermal desorption from warm dust. A gas-phase origin in reactions between oxygen atoms and CH$_3$ radicals is possible.

|        |                   |                                     |
|:------:|:-----------------:|:-----------------------------------:|
| Region |     T$_{rot}$     |              N$_{col}$              |
|        |       \(K\)       |             (cm$^{-2}$)             |
|  Main  | 40.4 (+2.7, -2.4) |     3.8 (0.4) $\times 10^{13}$      |
|   N    |  73 (+101, -27)   | 2.8 (+0.08, -0.01) $\times 10^{13}$ |
|   S    | 10.8 (+0.3, -0.2) |     1.4 (0.1) $\times 10^{13}$      |
|   W    | 36.5 (+7.0, -5.1) |  3.9 (+1.2, -0.9) $\times 10^{13}$  |

: H$_2$CO gas properties in different regions of Cha-MMS1 with errors in parentheses. Note that the fit for N was poor due to the low flux of the transition at 219475 MHz (E$_{\mathrm{up}}$ 68 K).

![](H2COlabel.png)

## CH$_3$OH emission

CH$_3$OH emission is detected towards the clumps associated with H$_2$CO emission to the northeast, south, and southwest of the continuum source, but not toward the continuum source itself. All CH$_3$OH emission is much weaker than in other detected species. The column densities are consistent between regions at $10^{13}$-$10^{14}$ cm$^{-2}$ (Table [3](#rotdTableCH3OH)). The upper limit for the column density of CH$_3$OH toward the main source was calculated assuming a T$_{rot}$ of 51 K (to match the temperature of H$_2$CO toward Main) and a line width of 0.7 km s$^{-1}$. The inferred dust temperatures are significantly lower than the sublimation temperature of CH$_3$OH derived from experiments (128 K; (cite: Penteado2017)) and so the observed methanol is likely being produced by ice sputtering in shock waves.

|        |             |                            |
|:------:|:-----------:|:--------------------------:|
| Region |  T$_{rot}$  |         N$_{col}$          |
|        |    \(K\)    |        (cm$^{-2}$)         |
|  Main  |    51\*     |  $<$1.2 $\times 10^{13}$   |
|   N    | 41.2 (30.8) | 8.6 (6.4) $\times 10^{13}$ |
|   S    | 23.2 (2.3)  | 4.8 (0.8) $\times 10^{13}$ |
|   W    | 15.7 (1.9)  | 1.1 (0.4) $\times 10^{14}$ |

: CH$_3$OH gas properties in different regions of Cha-MMS1. \* The rotational temperature of CH$_3$OH towards Main was assumed to be 51 K to mirror H$_2$CO toward Main and the column density is therefore an upper limit.

![](methanolh2coContours.pdf)

# Discussion

## Physical origin of outflow emission

The CO emission has multiple spatially overlapping components indicating that the outflow is nearly perpendicular to the line-of-sight. The shape of the red-shifted emission in CO and $^{13}$CO to the southwest of the continuum source implies that there is a dense clump of molecular gas diverting the outflowing material, which is traced in our observations by H$_2$CO and CH$_3$OH. This is also suggested in (cite: MariaJose2020) in maps of NH$_{2}$D. The alternative scenario is that this S-shaped emission and slower, more distant blue-shifted emission indicates a precessing outflow. The broad red-shifted emission to the northeast of the continuum may originate from a second source implying a tight binary system within the continuum. There is no corresponding blue-shifted broad component detected at similar velocities but it may have been disrupted by the molecular clump south of the continuum source. The irregular velocity structure demonstrates that in the early stages of star formation, the outflow launching is chaotic. The clumpy structure observed in CS and H$_2$CO emission may be due to small ejections from the early stages of the stellar outflow or simply the clumpiness of the surrounding cloud. The underlying power source driving the outflow activity associated with Cha-MMS1 could be either a single precessing outflow or two outflows from a close binary system. Alternative scenarios can also produce outflow precession, for instance, the misalignment between the outflow axis (a proxy for angular momentum axis) and the magnetic field axis as discussed in (cite: Busch2020), which does not require a binary. Similarly, a change in the angular momentum axis of the infalling material due to turbulent conditions can also produce shape distortions (cite: Matsumoto2017).

## Status of Cha-MMS1

While many FHSC candidates have been proposed over the past 20 years, most have now been identified as young class 0 objects, VeLLOs, or prestellar cores. Compared to the outflow properties of the remaining FHSC candidates with published outflow properties (G208.89-20.04 (cite: Dutta2022), MC35-mm (I1535-NE) (cite: Fujishiro2020), L1451-mm (cite: Pineda2011), and GF 9-2 (cite: Furuya2019)) Cha-MMS1 has a similar maximum velocity range, generally lower dynamical time, and higher mechanical luminosity (by at least 2 orders of magnitude). The mechanical luminosity is also several orders of magnitude higher than the VeLLOs identified in (cite: Dunham2011). The sources with the most similar outflow properties are the young stars in Barnard 1b (cite: Hirano2014). Numerous complex molecular lines have been detected toward B1b-S (cite: Marcelino2018), indicating that it is too evolved to be a FHSC.

### Mechanical properties

The mechanical outflow properties are several orders of magnitude lower than a 1 L$_{\ensuremath{\odot}}$ star. The mechanical properties we have derived for Cha-MMS1 are in line with the relationships between mass and luminosity and momentum rate and luminosity shown in (cite: Wu2004). The line of sight outflow properties we calculated using the CO (2-1) transition are generally similar to the values in (cite: Busch2020), which were calculated using the CO (3-2) transition. They concluded that Cha-MMS1 was not a FHSC, though it was one of the youngest Class 0 objects ever detected. We find the kinetic time to be on the order of hundreds of years, rather than thousands, which results in our time-dependent values being an order of magnitude higher. We agree with their assessment that the bent shape of the red-shifted emission in CO and $^{13}$CO to the southwest of the continuum source is likely due to the clump of molecular material there.

### Chemistry

The presence of H$_2$CO without corresponding CH$_3$OH towards the main source is striking and attests to the young age of this source. CH$_3$OH is also underabundant with respect to the CH$_3$OH/H$_2$CO ratio typically observed in the vicinity of low and high-mass protostars (cite: Floris2000). Using detected emission from three H$_2$CO transitions and three CH$_3$OH, we created rotational diagrams to determine the gas temperature and column density at the four positions described in the previous section: main, N, S and W. The resulting gas temperatures at Cha-MMS1 main and W are $\sim$50 K, indicating dust temperatures below those required to thermally desorb H$_2$CO (114 K) from icy dust grain mantles. The low dust temperature inferred from the temperature of CH$_3$OH is too cool for thermal desorption, which implies that this emission arises from ice sputtering from interactions with the out-flowing material, as CH$_3$OH is not easily made in the gas phase. The rotational temperatures for the emission at Cha-MMS1 S suggest dust temperatures lower than the sublimation temperature of both H$_2$CO and CH$_3$OH, therefore may also be the result of outflow shocks sputtering ices.

# Conclusions

We observed Cha-MMS1 with ALMA in Band 6 at high angular resolution and detected $^{12}$CO and $^{13}$CO emission as well as CS, H$_2$CO, and CH$_3$OH. We find a weak outflow nearly perpendicular to the line of sight toward the northeast and southwest of the continuum source. The effects of the outflow are seen on the local molecular cloud through CS, H$_2$CO, and CH$_3$OH emission. A kink in the southwestern outflow corresponds with low rotational temperature ($\sim$20-30 K) emission from H$_2$CO and CH$_3$OH indicating a clump of molecular material being shocked by the outflow.

Comparison of Cha-MMS1 with other low-luminosity protostars supports the view that it is not a viable FHSC. In fact, recent observations of SiO and CH$_3$OH in L1451-mm (cite: Wakelam2022) suggest that it too is not a FHSC. The weak outflow and relatively low temperatures associated with this object indicate that it is one of the youngest known Class 0 objects.

# Acknowledgments

*Acknowledgments:* This paper makes use of the following ALMA data: ADS/JAO.ALMA 2013.1.01113.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under a cooperative agreement by Associated Universities, Inc. V. Allen’s research for this article was supported by an appointment to the NASA Postdoctoral Program at the NASA Goddard Space Flight Center, administered by Universities Space Research Association under contract with NASA. V. Allen is currently supported by an NWO Veni grant number VI.Veni.202.135. V. Allen, M. Cordiner, and S.B. Charnley were supported by the NASA Planetary Science Division Internal Scientist Funding Program through the Fundamental Laboratory Research work package (FLaRe).

# Facilities

ALMA

# Spectra

![](COspeclabel.pdf)

![](COnorthblue.png)

![](CObroadred.png)

![](COmain.png)

![](COsouthred.png)

![](COwestred.png)

![](COsouthblue.png)

![](h2coMain.png)

![](h2coN.png)

![](h2coS.png)

![](h2coW.png)

![](ch3ohMain.png)

![](ch3ohN.png)

![](ch3ohS.png)

![](ch3ohW.png)

# Additional integrated intensity maps

![](H2CO218222contourstcleanAll.pdf)

![](H2CO218475contourstcleanAll.pdf)

![](H2CO225contourstcleanAll.pdf)

![](CH3OH218tcleanAll.pdf)

![](CH3OH241767tcleanAll.pdf)

![](CH3OH241791tcleanAll.pdf)

(ref: Bally2006) Bally, J., Walawender, J., Luhman, K. L., & Fazio, G. 2006, AJ, 132, 1923

(ref: Belloche2006) Belloche, A., Parise, B., van der Tak, F. F. S., et al. 2006, A&A, 454, L51

(ref: Belloche2011) Belloche, A., Schuller, F., Parise, B., et al. 2011, A&A, 527, A145

(ref: Bjerkeli2013) Bjerkeli, P., Liseau, R., Nisini, B., et al. 2013, A&A, 552, L8

(ref: Bolatto2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Busch2020) Busch, L. A., Belloche, A., Cabrit, S., et al. 2020, A&A, 633, A126

(ref: Chen2010) Chen, X., Arce, H. G., Zhang, Q., et al. 2010, ApJ, 715, 1344

(ref: Chen2012) Chen, X., Arce, H. G., Dunham, M. M., et al. 2012, ApJ, 751, 89

(ref: Cordiner2012) Cordiner, M. A., Charnley, S. B., Wirström, E. S., et al. 2012, ApJ, 744, 131

(ref: Dunham2011) Dunham, M. M., Chen, X., Arce, H. G., et al. 2011, ApJ, 742, 1

(ref: Dunham2008) Dunham, M. M., Crapsi, A., Evans, Neal J., I., et al. 2008, ApJS, 179, 249

(ref: Dutta2022) Dutta, S., Lee, C.-F., Hirano, N., et al. 2022, ApJ, 931, 130. doi:10.3847/1538-4357/ac67a1

(ref: Dzib2018) Dzib, S. A., Loinard, L., Ortiz-León, G. N., et al. 2018, ApJ, 867, 151

(ref: Friesen2018) Friesen, R. K., Pon, A., Bourke, T. L., et al. 2018, ApJ, 869, 158. doi:10.3847/1538-4357/aaeff5

(ref: Fujishiro2020) Fujishiro, K., Tokuda, K., Tachihara, K., et al. 2020, ApJL, 899, L10

(ref: Furuya2019) Furuya, R. S., Kitamura, Y., & Shinnaga, H. 2019, ApJ, 871, 137. doi:10.3847/1538-4357/aaf85c

(ref: Goldsmith1999) Goldsmith, P. F. & Langer, W. D. 1999, ApJ, 517, 209

(ref: Goldsmith2001) Goldsmith, P. F. 2001, ApJ, 557, 736

(ref: Hiramatsu2007) Hiramatsu, M., Hayakawa, T., Tatematsu, K., et al. 2007, ApJ, 664, 964

(ref: Hirano2014) Hirano, N. & Liu, F.-c. 2014, ApJ, 789, 50

(ref: Hirano2019) Hirano, N. 2019, ALMA2019: Science Results and Cross-Facility Synergies, 90. doi:10.5281/zenodo.3585378

(ref: distref) Knude, J., & Hog, E. 1998, A&A, 338, 897

(ref: Evgenia2016) Koumpia, E., van der Tak, F. F. S., Kwon, W., et al. 2016, A&A, 595, A51. doi:10.1051/0004-6361/201528042

(ref: Ladd2011) Ladd, E. F., Wong, T., Bourke, T. L., & Thompson, K. L. 2011, ApJ, 743, 108

(ref: Larson1969) Larson, R. B. 1969, MNRAS, 145, 271

(ref: Lee2007) Lee, J.-E. 2007, in American Astronomical Society Meeting Abstracts, Vol. 211, 89.13

(ref: AnaOutflows) López-Sepulcre, A., Codella, C., Cesaroni, R., Marcelino, N., & Walmsley, C. M. 2009, A&A, 499, 811

(ref: Ana2010) López-Sepulcre, A., Cesaroni, R., & Walmsley, C. M. 2010, A&A, 517, A66

(ref: Machida2008) Machida, M. N., Inutsuka, S.-i., & Matsumoto, T. 2008, ApJ, 676, 1088

(ref: Marcelino2018) Marcelino, N., Gerin, M., Cernicharo, J., et al. 2018, A&A, 620, A80. doi:10.1051/0004-6361/201731955

(ref: Masunaga2000) Masunaga, H. & Inutsuka, S.-i. 2000, ApJ, 531, 350

(ref: Matsumoto2017) Matsumoto, T., Machida, M. N., & Inutsuka, S.-. ichiro . 2017, ApJ, 839, 69. doi:10.3847/1538-4357/aa6a1c

(ref: MariaJose2020) Maureira, M. J., Arce, H. G., Dunham, M. M., et al. 2020, MNRAS. doi:10.1093/mnras/staa2894

(ref: Noble2012) Noble, J. A., Theule, P., Mispelaer, F., et al. 2012, A&A, 543, A5

(ref: Okoda2020) Okoda, Y., Oya, Y., Sakai, N., et al. 2020, ApJ, 900, 40. doi:10.3847/1538-4357/aba51e

(ref: Omukai2007) Omukai, K. 2007, PASJ, 59, 589

(ref: Penteado2017) Penteado, E. M., Walsh, C., & Cuppen, H. M. 2017, ApJ, 844, 71

(ref: Pineda2011) Pineda, J. E., Arce, H. G., Schnee, S., et al. 2011, ApJ, 743, 201

(ref: Price2012) Price, D. J., Tricco, T. S., & Bate, M. R. 2012, MNRAS, 423, L45

(ref: Reipurth1996) Reipurth, B., Nyman, L. A., & Chini, R. 1996, A&A, 314, 258

(ref: Saigo2011) Saigo, K. & Tomisaka, K. 2011, ApJ, 728, 78

(ref: AlvaroOutflows) Sánchez-Monge, Á., López-Sepulcre, A., Cesaroni, R., et al. 2013, A&A, 557, A94

(ref: Spear2021) Spear, S., Maureira, M. J., Arce, H. G., et al. 2021, ApJ, 923, 231. doi:10.3847/1538-4357/ac3083

(ref: H2COsub1) Tielens, A. G. G. M. & Hagen, W. 1982, A&A, 114, 245

(ref: Tsitali) Tsitali, A. E., Belloche, A., Commerçon, B., et al. 2013, A&A, 557, A98

(ref: Tomida2010) Tomida, K., Tomisaka, K., Matsumoto, T., et al. 2010, ApJ, 714, L58

(ref: Vaisala2014) Väisälä, M. S., Harju, J., Mantere, M. J., et al. 2014, A&A, 564, A99

(ref: Floris2000) van der Tak, F. F. S., van Dishoeck, E. F., & Caselli, P. 2000, A&A, 361, 327

(ref: Vastel2015) Vastel, C., Bottinelli, S., Caux, E., et al. 2015, SF2A-2015: Proceedings of the Annual meeting of the French Society of Astronomy and Astrophysics, 313

(ref: Wakelam2022) Wakelam, V., Coutens, A., Gratier, P., et al. 2022, A&A, 666, A191. doi:10.1051/0004-6361/202243459

(ref: Wu2004) Wu, Y., Wei, Y., Zhao, M., et al. 2004, A&A, 426, 503

(ref: Young2019) Young, A. K., Bate, M. R., Harries, T. J., et al. 2019, MNRAS, 487, 2853

[^1]: http://cassis.irap.omp.eu (cite: Vastel2015). CASSIS has been developed by IRAP-UPS/CNRS.

</paper>

Write the methods card for this paper.