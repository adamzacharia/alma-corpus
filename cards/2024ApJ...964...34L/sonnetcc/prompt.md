# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...964...34L\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...964...34L",
 "title": "Multiple Jets in the Bursting Protostar HOPS 373SW",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Lee, Seokho",
 "n_authors": 5,
 "arxiv_id": "2401.12449",
 "doi": "10.3847/1538-4357/ad21e3",
 "alma_projects_linked_by_archive": [
  "2015.1.00041.S",
  "2018.1.01565.S",
  "2019.1.00386.T"
 ]
}
```

Paper text:
<paper>
# Multiple Jets in the bursting protostar HOPS 373SW

## Abstract

We present the outflows detected in HOPS 373SW, a protostar undergoing a modest $30\%$ brightness increase at 850 $\mu$m. Atacama Large Millimeter/submillimeter Array (ALMA) observations of shock tracers, including SiO 8–7, CH$_3$OH 7$_{\rm k}$–6$_{\rm k}$, and $^{12}$CO 3–2 emission, reveal several outflow features around HOPS 373SW. The knots in the extremely high-velocity SiO emission reveal the wiggle of the jet, for which a simple model derives a 37$^\circ$ inclination angle of the jet to the plane of the sky, a jet velocity of 90 km s$^{-1}$, and a period of 50 years. The slow SiO and CH$_3$OH emission traces U-shaped bow shocks surrounding the two CO outflows. One outflow is associated with the high-velocity jets, while the other is observed to be close to the plane of the sky. The misaligned outflows imply that previous episodic accretion events have either reoriented HOPS 373SW or that it is an unresolved protostellar binary system with misaligned outflows.

# Introduction

Variable and episodic accretion is recognized as a standard feature of the star formation process (cite: Fischer2022). This expectation is supported by observations across a broad range of diagnostic signatures, including FU Orionis and EX Lup type brightening events (cite: Herbig1966; Hartmann1996; Audard2014), water and CO snow lines that extend beyond expectations for present-day luminosities (cite: Lee2007; Jorgensen2015; Hsieh2019), and multiple clumps within individual jets (cite: Lee2010) and outflows (cite: Plunkett2015). Furthermore, near-infrared, mid-infrared, and sub-mm monitoring observations provide direct evidence of variable accretion as a common protostar phenomenon (cite: Rice2015; Park21).

Protostellar jets and outflows are indirect records of the variable accretion history, being natural byproducts of the protostellar accretion process (cite: Frank2014; Lee2020; Fischer2022). Furthermore, the mass ejection rates are seen to be proportional to the mass accretion rates (cite: Lee2020). Within the outflows, high-velocity jets show quasi-episodic knots from which we can derive the timescales of the variability (cite: Plunkett2015; Lee2020; Jhan2022).

HOPS 373 is a protostellar binary system located in the Orion B cloud (cite: Johnstone2001) at a distance of 428 pc (cite: Kounkel2018) showing a modest 30% brightness variability at 850 $\mu$m in the James Clerk Maxwell Telescope (JCMT) Transient Monitoring Survey (cite: Yoon2022). HOPS 373 consists of two continuum sources with a separation of 3.$''$6 (1500 au at the distance of 428 pc): referred to as the northeast (NE) and southwest (SW) sources (cite: Tobin2015; Tobin2020; Yoon2022). Based on the spectral energy distribution, the estimated bolometric luminosity and the bolometric temperature of the HOPS 373 system are 5.3 $L_\odot$ and 37 K, respectively (cite: Kang2015; Furlan2016).

Complex outflow features are observed in HOPS 373. The $^{12}$CO 2–1 emission shows both a large-scale southeast (SE)-northwest (NW) outflow and a small-scale east-west outflow (cite: Tobin2016; Yoon2022). The dynamical age and the inclination of the large-scale CO outflow are 10$^4$ years and 40$^\circ$, respectively (cite: Furlan2016; Nagy2020). The small-scale CO outflow is associated only with HOPS 373SW. In contrast, no small-scale molecular emission has been detected in HOPS 373NE, except for the C$^{17}$O 3–2 line (cite: Yoon2022; Lee2023). (cite: Yoon2022) argued that the large-scale SE-NW outflow either is associated with the NE source or that wiggles within the outflow from the SW source changed its outflow direction from a blue-shifted large-scale SE outflow to a red-shifted small-scale east outflow.

High spatial resolution ALMA observations show prominent jets and bow shocks ejected from HOPS 373SW. In this work, we investigate the properties of these observed jets and outflows and derive the possible link with the observed variable accretion. The observations and archive data sets are described in Sections [2](#sec:obs). In Sections [3](#sec:jet_morphology)–[6](#sec:property_of_jet), the properties of SiO and CH$_3$OH jets/outflows are investigated. We discuss the stellar mass, episodic accretion, and the origin of the two outflows in Section [7](#sec:discussion) before summarizing our results in Section [8](#sec:summary).

# Observations

We investigated the jets and outflows in HOPS 373SW using Cycle 7 ALMA observations (2019.1.00386.T, PI: Jeong-Eun Lee) and Cycle 4 ALMA archive data (2015.1.00041.S, PI: John J. Tobin). Detailed observations and data reduction can be found in (cite: Lee2023) for the Cycle 7 data and in previous works (cite: Tobin2020; Yoon2022) for the Cycle 4 data.

The Cycle 7 observations were carried out on 2021 August 2 and 6 with thirty-eight 12-m antennas, and a longest baseline of 5.6 km. The total integration time on the source was 61 minutes. The jet tracers SiO 8–7 (347.330631 GHz) and CH$_3$OH 7$_{\rm k}$–6$_{\rm k}$ (338.34–338.73 GHz) (cite: Tafalla2010; Tychoniec2021) were covered with this observation. The SiO and CH$_3$OH lines were cleaned using the natural weighting with the uvtaper of 0.$''$2 ($\sim$455 k$\lambda$) to increase the sensitivity, resulting in the beam size of $\sim$0.$''$23 with a rms of $\sim$3 mJy beam$^{-1}$  over the 1 km s$^{-1}$  spectral resolution. In addition, two CH$_3$OH lines at 338.408698 GHz and 338.344588 GHz were averaged to increase the signal-to-noise ratio (S/N). A high resolution ($\sim$0.$''$08) SiO image with a rms of $\sim$2 mJy beam$^{-1}$  over the 1 km s$^{-1}$  was also cleaned using natural weighting without uvtaper in order to study the jets near the continuum peak.

$^{12}$CO 3–2 (345.7959899 GHz) was covered by the Cycle 4 archive data, which were observed on 2016 September 3 and 4 and on 2017 July 19. The $^{12}$CO line was cleaned using the natural weighting with the uvtaper of 500 k$\lambda$, resulting in a beam size of 0.$''$25 with a noise level of 20 mJy beam$^{-1}$  over 1 km s$^{-1}$  spectral resolution.

The Atacama Compact Array (ACA) archive data toward HOPS 373 were also used to check the extended features. These observations were carried out in March 2019 as a part of the program 2018.1.01565.S (PI: Tom Megeath). Lines of C$^{18}$O 2–1 and N$_2$D$^+$ 3–2 were covered with a beam size of 7.$''$4 $\times$ 4.$''$9 and a spectral resolution of 0.34 and 0.16 km s$^{-1}$, respectively.

# Morphology of Jets and Outflows

![](fig1.eps)

![](fig2.eps)

![](fig3.eps)

HOPS 373SW shows prominent jets and outflows. Figure [1](#fig:jets) presents the SiO channel maps over the peak intensity map of CH$_3$OH. In this work, we adopt the systemic velocity ($V_{\rm sys}$) of 10.13 km s$^{-1}$ derived from the $^{13}$CH$_3$OH  lines (cite: Lee2023). All velocities are presented using the relative velocity with respect to this systemic velocity ($\Delta V=V-V_{\rm sys}$). Typically for outflows, the CH$_3$OH  emission favors a low-velocity gas, while the SiO emission is more abundant in the fastest gas (cite: Tafalla2010). For HOPS 373SW, the CH$_3$OH  emission has only slow components ($|\Delta V|<$4 km s$^{-1}$) as shown in Figure [2](#fig:jets_chxoh). In contrast, the SiO emission has multiple velocity components: slow ($|\Delta V|<15$ km s$^{-1}$), fast (15 km s$^{-1}$$<|\Delta V|<40$ km s$^{-1}$), and extremely high velocity (EHV, $|\Delta V|>40$ km s$^{-1}$). Note that the observation window covers only up to $-$70 km s$^{-1}$  from the systemic velocity to the blue, while the red-shifted SiO emission is detected up to $\sim$90 km s$^{-1}$. Thus, we cannot rule out that the highest velocity component in the blue-shifted SiO emission has been missed. Previously, in low mass protostars, the SiO emission has been observed in clumps (cite: Tychoniec2021) rather than in the continuous outflow denoted by the CO, and these clumps have different peak velocities from the underlying outflow along with narrow line widths ($<$15 km s$^{-1}$). Due to this situation, the distribution of outflow shocks is more clearly revealed by the peak intensity (moment 8 in the CASA task ‘immoments’, the maximum value of the spectrum in each pixel) maps as shown in Figures [2](#fig:jets_chxoh) and [3](#fig:jets_zoom).

![](fig4.eps)

The EHV and fast SiO emission components trace the collimated NE-SW jet revealed by the EHV CO emission (cite: Yoon2022). Figure [5](#fig:spiztermap) shows that the NE-SW SiO emission is also associated with Spizter/IRAC 4.5 $\mu$m intensity tracing the H$_2$ emission in the NIR (cite: Tobin2007; Velusamy2011). The H$_2$ emission is detected only in the blue lobe (cite: Yoon2022). The red-shifted (NE) infrared emission might be extincted by the optically thick protostellar envelope and, therefore much fainter than the blue-shifted (SW) emission. The EHV and fast SiO emission consists of several knots in the red (HR1, HR2,...) and blue (HB1, HB2, and HB5) lobes, as shown in Figure [1](#fig:jets). The EHV SiO knots in the red lobe are well developed up to a terminal knot, HR5. On the other hand, the EHV SiO knot HB1 in the blue lobe is found only near the protostar, and the fast SiO knot HB2 and HB5 in the middle panel of Figure [1](#fig:jets) appear as counterparts to the red-shifted EHV SiO knots HR2 and HR5, respectively. The red-shifted SiO jet shows a wiggle from north to south as reported in the EHV CO map (cite: Yoon2022), for which we provide a plausible jet precession solution in Section [7.3](#sec:episodic). The SiO and CO emission within the blue lobe shows a point symmetry to those in the red lobe with respect to the continuum peak.

Figure [3](#fig:jets_zoom) shows the peak intensity and the absolute peak velocity maps for HR1 and HB1 near the continuum peak using the high spatial resolution images ($\sim$0$''$.08). They are derived after smoothing with a boxcar of 5 km s$^{-1}$. The knots HR1 and HB1 consist of several sub-knots. In the red lobe, the sub-knot HR1a exhibits a velocity gradient in the southeast direction. HR1b and HR1c appear to be connected, following a curved trajectory. There is an increase in velocity from HR1b to HR1c. HR1d and HR1e are weak compared to HR1a and HR1b. Counterparts in the blue lobe are identified by their distance from the protostar and peak velocity.

The slow SiO and CH$_3$OH  emission trace the bow shocks and two distinct outflows as shown in the top panel of Figure [1](#fig:jets) and [2](#fig:jets_chxoh), respectively. The NE-SW outflow (hereafter Outflow1) is confined by U-shaped bow shocks, LR1 and LB1 (see the black curves in Figures [1](#fig:jets), [2](#fig:jets_chxoh), and [4](#fig:co_chan)), which could be related to the above jet. The SE-NW outflow (hereafter Outflow2) is also surrounded by U-shaped bow shocks, LR2 and LB2. Similar U-shapes of CH$_3$OH  and SiO emission are seen in L1157 and they trace the wings of the bow shock (cite: Gomez-Ruiz2013; Codella2020).

The distribution of SiO and CH$_3$OH  emission is different between the two HOPS 373SW outflows. In Outflow1, the wings of LR1 are mainly traced by the SiO emission, while those of LB1 are traced by the CH$_3$OH  emission. In contrast, only SiO emission (e.g., HR5, HR5L, HB5, and HB5L) is detected at the apexes of LR1 and LB1 without corresponding CH$_3$OH  emission. In Outflow2, the CH$_3$OH  emission is detected at both the apexes and in the wings. Furthermore, slow SiO emission is clearly detected in LB2 but only marginally in LR2, while the tip of LB2 shows both red- and blue-shifted slow components of SiO and CH$_3$OH  emissions implying that the tip might be close to the plane of the sky.

Figure [4](#fig:co_chan) shows the CO channel maps overlaid on the SiO and CH$_3$OH  peak intensity (moment 8) maps. The EHV CO emission (bottom panel) traces the jets shown by the EHV SiO emission. The fast (middle panel) and slow (top panel) blue-shifted CO outflow components are confined by the wings of LB1, implying an association with Outflow1. The red-shifted Outflow1 can be traced by the fast red-shifted CO emission and the slow SiO emission (the wings of LR1).

The CO outflow associated with Outflow2 might be resolved out, except for the observed slow SE (red) and NW (blue) CO outflow components (A and B in the top panel of Figure [4](#fig:co_chan)). The velocities may therefore be close to the systematic velocity and Outflow2 oriented close to the plane of the sky, as revealed by the CH$_3$OH  emission at the tip of LB2. Note that we cannot rule out that all of the slowest CO emission in the map, except for the emission around the apexes of LR1 and LB1, might be related to Outflow2 because the slow CO emission in the north (south) wall within $\sim$3$''$ of the red (blue) lobe seems to connect to the wings of LR2 (LB2). In this case, the outflow velocity might have been decelerated through interaction with the ambient medium and have slowed to close to the systemic velocity near the apex of LR2 and LB2.

![](fig5.eps)

# Position velocity diagrams of jets and outflows

![](fig6.eps)

Figure [6](#fig:pv_ra) shows the position velocity diagram along the R.A. (jet) direction within $|\Delta$Dec.$|<$1.$''$5. The knots in the red-shifted jet have an observed jet velocity of $\sim$55 km s$^{-1}$  and a terminal velocity of $\sim$45 km s$^{-1}$  at HR5. On the other hand, the knots in the blue-shifted jet have decreasing velocities with $\sim$-55 km s$^{-1}$  at HB1, $\sim$-35 km s$^{-1}$  at HB2, and a terminal velocity of $\sim$-20 km s$^{-1}$  at HB5. Velocity asymmetries in the red and blue lobes are also observed in the SiO jets of L1448C (cite: Yoshida2021) and L1157 (cite: Podio2016), as well as in the optical/infrared jets from Class II sources (cite: Hirth1994). This asymmetric velocity could originate from the launching mechanism itself, for example, differences of launching velocity on each side of the disk by the magnetic field (cite: Dyda2015) or the accreting mass (cite: Liu2012), or as a result of interaction with an asymmetric environment (cite: Podio2016). In addition, this could originate due to different inclination angles in the blue and red lobes due to the wiggling of jet. However, the distance of terminal knot HB5 is closer to the protostar compared to HR5; thus, the velocity of the blue-shifted jet should be slower than that of the red-shifted one.

The HR1 knots could have been ballistically ejected. The yellow lines in the upper insert of Figure [6](#fig:pv_ra) indicate velocity gradients along the distance from the origin with 270 km s$^{-1}$ arcsec$^{-1}$ and 120 km s$^{-1}$ arcsec$^{-1}$. Therefore the sub-knots HR1a and HR1b would have been ejected 7.5 tan($i$) and 17 tan($i$) years ago, respectively, where $i$ is the inclination of jet from the plane of sky. The red lines indicate the velocity gradients for ejection events that occurred previously with a similar time interval (9.4 tan($i$) years). It is plausible that sub-knots HR1d and HR1e might have been ballistically ejected with the same cadence. On the other hand, sub-knots in HB1 do not show the velocity gradient along the distance despite their proximity to the velocity gradient associated with each counterpart. The absence of the velocity gradient in the HB1 could be attributed to the limitations in velocity coverage and/or the weaker emission in the blue lobe compared to the red lobe.

![](fig7.eps)

Figure [7](#fig:pv_dec) shows the position velocity diagram of CO 3–2 (image and white contours), SiO 8–7 (red contours), and CH$_3$OH  (green contours) along the Declination (perpendicular to the jet axis). Near the protostar at $\pm$1.$''$1 (bottom panels), both CO and SiO emission connect the high-velocity components (HR1e and HB1e) to the ambient envelope material, implying that the ambient material is being accelerated by the jet (cite: Rabenanahary2022) as also shown in HH 211 (cite: Jhan2021) and Cep E (cite: Schutzer2022). The emission in the velocity range of 20–50 km s$^{-1}$ is seen only in the southern region in the red-shifted lobe while no emission is seen in the northern region. The fast CO emission (the middle panel of Figure [4](#fig:co_chan)) also shows that the red-shifted fast CO emission is extended along southern part while stunted along the northern part near the protostar. The blue-lobe shows an opposite trend. Furthermore, the red-shifted EHV SiO knots reveal a wiggling pattern from north to south as shown in the red curve in the bottom panel of Figure [1](#fig:jets). Therefore, it is plausible that the environment toward the northern part of the red-shifted flow was previously entrained by the earlier north-east jet and outflow, producing the observed asymmetric emission.

Around the HB2 knot (-2.$''$6, middle right panel of Figure [7](#fig:pv_dec)), the SiO emission is similar to that in HB1e, but with smaller jet velocity. The north ($\Delta$Dec.= $+$0.$''$3) and south ($\Delta$Dec.= -0.$''$4) CH$_3$OH  emission (green contours) may trace the wings of the bow shocks LB1 and LB2, respectively, with velocities similar to the systemic velocity. Around HR2 ($+$2.$''$6), the knot HR2a might accelerate the north wall traced by the fast SiO and CO emission (see the fast CO outflows in the middle panel of Figure [4](#fig:co_chan)). The HR2b knot may be interpreted as a southern accelerated component. It is also possible, however, for HR2b to be associated with Outflow2 because it is on the trajectory of the bow shock LR2, as shown in Figure [1](#fig:jets).

The southern SiO component indicates the apex of LB1(-4.$''$1, top right panel of Figure [7](#fig:pv_dec)), and is surrounded by two CH$_3$OH  components at the systemic velocity. Northern SiO emission appears to be associated with LB2. Around the apex of LR1 (+5.$''$2, top left panel), we also see the terminal knot HR5 and entrained components. Weak SiO knots toward the south are associated with LR2.

# Jet Models

A simple jet model provides an estimate of the jet physical parameters (cite: Raga1990; Lee2004; Jhan2022). The regular spaced knots can be produced by a periodic velocity variation in which fast-jet material catches up with slow-jet material. This is in agreement with the position velocity diagram which shows higher velocities toward the central source as shown in HR2a, HR4, HB2, then HB5L in Figure [6](#fig:pv_ra).

A time dependent periodic jet velocity $V(t)$ with a fixed period ($P$), mean jet velocity ($V_j$), and velocity variation amplitude($\Delta V_j$) can be written as: $$\begin{equation}
    V = V_j - \frac{\Delta V_j}{2}\sin \left(\frac{2\pi t}{P}\right).
\end{equation}$$ With this model, the distance ($D$) to the first knot is $$\begin{equation}
    D = V_j\frac{V_j}{\Delta V_j/(P/\pi)}
\end{equation}$$ and the interval ($\Delta D$) between the knots is $$\begin{equation}
    \Delta D = P V_j.
\end{equation}$$ The observed distance to the first knot ($D_{\rm obs}$) and the observed interval of the knots ($\Delta D_{\rm obs}$) are $$\begin{eqnarray}
    D_{\rm obs} &=& D \cos i, \\
  \Delta D_{\rm obs} &=& \Delta D \cos i,
\end{eqnarray}$$ respectively, where $i$ is the inclination angle of the jet to the plane of the sky.

The observed jet velocity ($V_{\rm obs}$) and the observed sideways-ejection velocity ($\Delta V_{\rm obs}$) are $$\begin{eqnarray}
  V_{\rm obs} &=& V_j \sin i, \\
  \Delta V_{\rm obs} &=& \Delta V_j \cos i,
\end{eqnarray}$$ respectively, when no energy dissipation is assumed and the sideways-ejection velocity is equal to $\Delta V_j$. Therefore, the parameters of the jets ($V_j$, $\Delta V_j$, $P$, and $i$) can be derived from the observed parameters ($V_{\rm obs}$, $\Delta V_{\rm obs}$, $D_{\rm obs}$, and $\Delta D_{\rm obs}$). For example, the inclination is derived as $$\begin{equation}
     i = \tan^{-1}\left(
     \frac{V_{\rm obs}\,\Delta D_{\rm obs}}{\pi\,\Delta V_{\rm obs}\,D_{\rm obs}}  \right).
 
\end{equation}$$

cccc 2cMeasured parameters & 2cDerived parameters\
$D_{\rm obs}$ & 2.$''$8 $\pm$ 0.$''$3 & $i$ & 37 $\pm$ 11 $^\circ$\
$\Delta D_{\rm obs}$ & 1.$''$8 $\pm$ 0.$''$3 & $V_j$ & 91 $\pm$ 22 km s$^{-1}$\
$V_{\rm obs}$ & 55 $\pm$ 5 km s$^{-1}$& $\Delta V_j$ & 19 $\pm$ 3 km s$^{-1}$\
$\Delta V_{\rm obs}$ & 15 km s$^{-1}$& P & 50 $\pm$ 26 years

Table notes: see Section [5](#sec:jet_model).

The jet model is applied to the red-shifted EHV SiO knots HR2a and HR4. Both knots exhibit the velocity pattern predicted by the jet model, with the higher velocity in the upstream side and lower velocity in the downstream side, as previously mentioned. The knot HR3 is ignored because it does not show such a characteristic velocity pattern. In addition, the intensity of HR3 is lower than that of HR2a and HR4. Note that the knot HR1d seems to have the velocity pattern predicted by the jet model similar to HR2a and HR4, and might therefore be considered as a potential candidate for the first knot. However, the distance to the HR1d ($\sim$0.$''$8) is shorter than $\Delta D_{\rm obs}$ (1.$''$8) while the $D_{\rm obs}$ is generally longer than $\Delta D_{\rm obs}$ (cite: Jhan2022). In addition, the knot HR1 could be formed by the periodic ballistic ejection as mentioned in Section [4](#sec:pv). Therefore, the knot HR1d is not used as the first knot in our jet model.

The observed parameters provide the jet parameters as shown in Table [\[tb:jetmodel\]](#tb:jetmodel). Thus, knots HR2a and HR4 appear to have been ejected $\sim$80 and $\sim$130 years ago, respectively. If HR1a (0.20$''$), HR1b (0.48$''$), and HR5 (5.5$''$) have similar inclination and jet velocity, they were ejected $\sim$6, $\sim$13, and $\sim$150 years ago, respectively. The former two time scales are consistent with the dynamical time scales of HR1a (5.7 years) and HR1b (13 years) derived from the ballistic ejection in Section [4](#sec:pv). Note that when the HR3 is also considered in the jet model, the inclination (20$^\circ$) and the period (13 years) decrease while the jet velocity (155 km s$^{-1}$) increases. The dynamical time scales of knots are reduced by half compared to the jet model without HR3. Then HR1a was ejected in the minimum phase of flux variation (cite: Yoon2022). Thus, we prefer the jet model without HR3.

The knots HB2 and HB5 could be counterparts of the red-shifted SiO jet. Although their velocity is decreasing toward the terminal knot HB5, the projected distances from the continuum peak are similar to those of the counterpart. When the inclination and jet velocity in the red lobe are adopted, HB2 and HB5 were ejected 72 and 120 years ago, respectively.

# Physical and Chemical properties of Jets/Outflows

## SiO and CO

![](fig8.eps)

The CO 3–2 and SiO 8–7 lines constrain the physical condition within the HR1a knot, which lies 0.$''$2 from the continuum peak and appears to have been ejected $\sim$6 years ago. Using the CASA task, ‘imfit’, the high-resolution SiO 8–7 image (see Figure [3](#fig:jets_zoom)) shows a spatial width of the HR1a knot of 39 $\pm$ 10 mas (16.7 $\pm$ 4.3 au at the distance of 428 pc), a similar width as that seen in other jets (see Figure 7 in (cite: Lee2020)).

We derive the SiO and CO column densities using a Large Velocity Gradient (LVG) model (cite: vanderTak2007; Lee2013). The radiative and collision coefficients for CO and SiO are provided by the LAMDA database (cite: Schoier2005; Yang2010; Balanca2018).

A simple approach tells us that the HR1a knot appears to be dense clump. The SiO 8–7 spectrum at the location of HR1a shows a peak intensity of 60 K and a line width (FWHM) of 20 km s$^{-1}$(see the red spectrum in the top panel of Figure [8](#fig:co_sio_spectra)). Convolved to the beam size of the CO 3–2 image (0.$''$27), the intensity of the SiO emission (blue spectra) is a factor of 5 lower than that of the original (red) SiO spectrum due to beam dilution. The EHV gas traced by CO 3–2 and SiO 8–7 lines show similar spatial distribution in HH211 (cite: Jhan2021), so we assumed that the CO 3–2 and SiO 8–7 lines trace the same gas. The EHV CO 3–2 emission from the knot, corrected by the beam dilution factor using the ratio of the red and blue SiO 8–7 lines, has an intensity of $\sim$50 K as shown by the black spectrum in the top panel of Figure [8](#fig:co_sio_spectra). Assuming dense ($\sim$10$^7$ cm$^{-3}$) and warm gas (100–500 K) conditions, the CO column density is 1.1–2.9$\times$10$^{18}$ cm$^{-2}$. Thus, if the CO abundance is 10$^{-4}$ and the length of the line of sight is the same as the knot width (16.7 au), then the derived gas density is 0.4–1.2 $\times$ 10$^8$ cm$^{-3}$, which is consistent with our initial assumption. Further, the mass of HR1a is 0.4–1.1 $\times$10$^{-5} M_\odot$ and the implied mass ejection rate is 1.2–3.2 $\times$10$^{-6} M_\odot$ yr$^{-1}$, when the length of HR1a (123 $\pm$ 13 mas), the inclination (37$^\circ$), and the jet velocity (91 km s$^{-1}$) are adopted.

The abundance ratio of SiO with respect to CO is different between the EHV and the slow components. At HR1a, the EHV SiO column density is 2.7–3.2 $\times$ 10$^{15}$ cm$^{-2}$, and the abundance ratio of SiO to CO is 14–5 $\times$ 10$^{-3}$ (100 K – 500 K). At HR1b (the middle panel of Figure [8](#fig:co_sio_spectra)), where the line width is $\sim$10 km s$^{-1}$, the column density of SiO is 1.3–1.6 $\times$ 10$^{15}$ cm$^{-2}$, and the abundance ratio of SiO to CO is 2–10 $\times$ 10$^{-3}$ (100 K – 500 K). The EHV knots (HR2a to HR5) show a similar line width ($\sim$10 km s$^{-1}$) and a similar intensity ratio between SiO 8–7 and CO 3–2 within a factor of two.

For the slow component (the bottom panel of Figure [8](#fig:co_sio_spectra)), the abundance ratio decreases by an order of magnitude. The gas density and temperature of the slow component might be between those of the EHV component and those derived by the excitation analysis of CH$_3$OH (see Section [6.2](#sec:ch3oh)).

We applied the same approach used in the EHV SiO component above since the emitting area of the slow SiO component and CO emission at HB5L are similar. The gas temperature of the slow component is likely higher than 50 K because the peak intensity of the beam-corrected CO is $\sim$ 60 K (see the bottom panel of Figure [8](#fig:co_sio_spectra)). Thus, we adopt the gas density of 10$^7$ cm$^{-3}$ and the same gas temperature of 100–500 K as in HR1a. With this setup, the SiO column density is 2.8–4.8 $\times$ 10$^{14}$ cm$^{-2}$ and the abundance ratio of SiO to CO is 1.3–4.6 $\times$ 10$^{-4}$. We note that the red-shifted slow SiO component HR5L is not considered in this analysis because the CO data are too noisy. The EHV component has a higher abundance ratio of SiO to CO than the slow components, which is also seen in Ser-emb 8 (N) (cite: Tychoniec2019), and the ratios are similar to what is observed in other protostars (cite: Hirano2010; Podio2021; Dutta2022a; Dutta2022b).

The SiO could be formed in the EHV gas launched from a dust-poor or dust-free inner disk, where the Si in the dust grains has already been fully liberated into the gas phase, as appears to be the case for other protostellar sources (cite: Lee2020; Podio2021). In that case, the abundance ratio of SiO to CO of $\sim$5 $\times$ 10$^{-3}$ could be reproduced if the mass ejection rate is $\sim$10$^{-6} M_\odot$ yr$^{-1}$ for the dust-free case or $\sim$10$^{-7}M_\odot$ yr$^{-1}$ for the dust depletion (see Figure 12 in (cite: Tabone2020)). These ejection rates are consistent with rates estimated above for HOPS 373SW ($\sim$10$^{-6} M_\odot$ yr$^{-1}$, see the mass ejection rate derived with HR1a).

The abundance of SiO in the slow-moving gas is a factor of 10 lower than that in the EHV gas. For the gas density and temperature derived from the excitation condition, it takes $>$3000 years for the liberated SiO abundance to decrease by a factor of 10 (cite: Simone2022) due to freeze-out onto grain, which is much longer than the dynamical time scale ($\sim$100 years). Thus, the slow-moving SiO component is unlikely to have been originally produced within the jet, where the SiO abundance was high. Instead, the observed slow-moving SiO likely originated from grain sputtering within the bow shock. The grain sputtering in a C-shock could produce the slow-moving SiO emission (cite: Gusdorf2008). This low SiO abundance could be produced within a few tens years according to C-shock models (cite: Gusdorf2008).

## CH$_3$OH

![](fig9.eps)

Figure [9](#fig:spec) shows the CH$_3$OH  7$_k$–6$_k$ spectra at the CH$_3$OH  emission peaks (CR1-3 and CB1-3) presented as white crosses in Figure [2](#fig:jets_chxoh). The multiple CH$_3$OH  lines are fitted by the Large Velocity Gradient (LVG) model (cite: vanderTak2007; Lee2013) using the radiative and collision coefficients for CH$_3$OH provided by the LAMDA database (cite: Schoier2005; Rabli2010). We assume that the abundances of A- and E-type CH$_3$OH are the same. The results for the six CH$_3$OH  peaks are listed in Table [1](#tb:lvg). Except for CB1 and CR1, most CH$_3$OH  emitting regions have a CH$_3$OH  column density of $\sim$10$^{15}$ cm$^{-2}$, a gas density of 10$^{7}$ cm$^{-3}$, and a gas temperature of $\sim$50 K.

The knots CR1 and CB1 are likely associated with recent shocks. The CR1 knot has the highest gas temperature of 155 K, and the CB1 knot has highest density of 5 $\times$ 10$^7$ cm$^{-3}$. The CH$_3$OH 338.559963 GHz, line with the observed highest upper energy level of 128 K, is detected in only CB1. Furthermore, CR1 and CB1 are near the apex of the high-velocity CO outflow and SiO jet near the protostar as shown in the middle and bottom panels of Figure [4](#fig:co_chan). Thus, CR1 and CB1 are expected to be recently heated by shocks.

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
|  | **Position** | **Emitting area$^{a}$** | **N(CH$_3$OH)** | **n$_{\rm H_2}$** | **T$_{gas}$** |
|  | ($''$,$''$) |  | 10$^{15}$ cm$^{-2}$ | 10$^7$ cm$^{-3}$ | K |
| CR3 | (+7.4, -0.3) | 0.5 (0.2) | 6.3 (3.2) | 0.8 (1.1) | 30 (12) |
| CR2 | (+3.6, -0.1) | 0.3 (0.1) | 10.0 (6.7) | 0.4 (0.4) | 30 (8) |
| CR1 | (+1.9, -0.5) | 0.8 (0.2) | 0.6 (1.3) | 1.0 (0.5) | 155 (49) |
| CB1 | (-2.0, +0.4) | 0.4 (0.1) | 6.3 (5.3) | 5.0 (1.4) | 85 (18) |
| CB2 | (-3.6, -0.8) | 1.0 (0.2) | 2.0 (2.3) | 1.6 (0.3) | 55 (14) |
| CB3 | (-5.4, +1.1) | 0.2 (0.2) | 6.3 (15.6) | 0.6 (0.6) | 40 (20) |

:  LVG models for CH$_3$OH  emission in HOPS 373SW

Table notes: The values in the parentheses are the 1$\sigma$ error.\
$^{a}$ The unit of the emitting area is relative scale with respective to the beam size of CH$_3$OH.

# Discussions

## Protostellar mass

The protostellar mass is an important parameter needed to understand the separation and period of any potential binary. The protostellar mass is derived from the Keplerian rotation profile of the gas emission. A rotation feature is shown in the $^{13}$CH$_3$OH  (cite: Lee2023). However, the derived stellar mass ($<$0.001 M$_\odot$) is much lower than the theoretical mass of the hydrostatic core (cite: Larson1969; Penston1969; Masunaga1998; Saigo2006) when the Keplerian motion and the inclination of 37$^\circ$  are adopted. Thus, the observed velocity features near HOPS 373SW might trace the infalling rotating envelope, which has a velocity profile with a steeper power law index (1/$r$) than that of a Keplerian disk (1/$\sqrt{r}$), and HOPS 373SW might have a very small, as yet unobserved, disk ($<$ a few au).

The protostellar mass can be roughly estimated using an indirect method. Class 0 protostars have a similar ratio of mass ejection rate to mass accretion rate, $\dot{M}_{j}/\dot{M}_{acc}$, (cite: Nisini2015; Lee2020; Podio2021). The recent mass ejection rate derived in Section [6.1](#sec:sio) is 1.2–3.2 $\times$10$^{-6} M_\odot$ yr$^{-1}$, which results in a mass accretion rate of 0.6–1.7 $\times$10$^{-5} M_\odot$ yr$^{-1}$. Taking this value for the mass accretion rate, the stellar mass can be estimated from $$\begin{eqnarray}
  M_{star} &= & 0.035\, M_\odot \times \left(\frac{L_{\rm bol}}{5.3 L_\odot} \right) \left(\frac{R_{star}}{2R_\odot}\right) \nonumber \\
  & & \left(\frac{1.2 \times 10^{-5} M_\odot \mathrm{yr}^{-1}}{\dot{M}_{\mathrm acc}}\right) 
\end{eqnarray}$$ where the bolometric luminosity of 5.3 $L_\odot$ is adopted (cite: Kang2015; Yoon2022). The stellar mass is then found to be between 0.025–0.07 $M_\odot$.

The derived stellar mass provides a consistent condition launching the SiO jets. The jet-launching radius ($R_{\rm jet}$) is estimated as (cite: Lee2020), $$\begin{equation}
    R_{\rm jet} \sim \left(2\frac{\dot{M}_{acc}}{\dot{M}_{jet}} - 3\right) \frac{GM_{\rm star}}{V_j^2},
\end{equation}$$ where $G$ is the gravitational constant. The derived $R_{\rm jet}$ is $\sim$0.03 au, which is consistent with that in other jets (cite: Lee2020). The jet-launching radius is much smaller than the dust sublimation radius ($R_s$) of 0.16 au, implying that the jets are launched from the dust-free region as mentioned in Section [6.1](#sec:sio). The dust sublimation radius is calculated as (cite: Monnier2002) $$\begin{equation}
    R_s = 7.5 \sqrt{Q_R}\sqrt{L_{\rm bol}/L_\odot}\left(\frac{T_{\rm sub}}{1500 K}\right)^{-2} R_\odot,
\end{equation}$$ where $Q_R$ is the ratio of dust absorption efficiency at the color temperature of the incident and re-emitting radiation fields and $T_{\rm sub}$ is the dust sublimation temperature. Here, we adopt Q$_R$= 4 and T$_{\rm sub}$= 1500 K (cite: Dullemond2001). Note that the values of $M_{\rm star}$, $R_{\rm jet}$, and $R_s$ could be smaller than the values estimated here if the bolometric luminosity of HOPS 373SW itself is lower than 5.3 $L_\odot$, which is the total luminosity of HOPS 373 including the SW and NE sources.

## Dynamical time scales for the two outflows

Outflow1 producing the U-shaped bow shocks LR1 and LB1 is younger than Outflow2 producing LR2 and LB2 (see Figure [4](#fig:co_chan)). The EHV jets and the H$_2$ emission in the near-infrared are associated with Outflow1 (see Figure [5](#fig:spiztermap)). The jet model shows the knot HR5 at the tip of LR1 in the end of Outflow1 was ejected 150 years ago (see Section [5](#sec:jet_model)).

The dynamical time scale of Outflow2 can be derived indirectly. The peak intensity and velocity of the SiO knot at the LB2 tip are $\sim$40 K and -3.5 km s$^{-1}$, respectively, and those of the marginally detected weak SiO knot at the LR2 tip are $\sim$19 K and 4.5 km s$^{-1}$, respectively. The peak temperature of 19–40 K is produced by a $\sim$30 km s$^{-1}$  shock if the pre-shock density is 10$^6$ cm$^{-3}$ (cite: Gusdorf2008). In addition, in LR2 and LB2 the velocity of the peak SiO emission is slightly faster than that of the peak CH$_3$OH  emission by 0.6 km s$^{-1}$ and 2.4 km s$^{-1}$, respectively. The CH$_3$OH  is quickly destroyed through reactions with H atoms after sputtering from the grain surface in the high-velocity shock (cite: Suutarinen2014; Nesterenok2018). Thus, the SiO and CH$_3$OH  knots would trace the tip and wings of the bow shocks, respectively, as shown in the bow shock LB1, and they might be overlapping each other due to the slow shock velocity. Using the above estimated shock velocities the dynamical time scale of the Outflow2 can be estimated. For a shock velocity of 30 km s$^{-1}$, the inclination of the outflows is derived as 7–9$^\circ$ from the velocities at the peak intensities of LR2 (4.5 km s$^{-1}$) and LB2 (-3.5 km s$^{-1}$), and the LR2 and LB2 would have been ejected $\sim$500 and $\sim$370 years ago, respectively.

## Episodic accretions

The EHV SiO jet shows two periodic variation timescales. The jet model reveals a period of 50 years with an observed separation of 1.$''$9 along the HR2a and HR4 knots. The higher resolution image shows that three sub-components lie within HR1 and HR2a (as shown in Figure [1](#fig:jets)) where the separation is 0.$''$3, a factor of 6 smaller than the larger scale variation and implying a period of $\sim$8 years when the jet velocity and the inclination are assumed the same as the jet model.

These periodic variations may be related to a periodical perturbation of the accretion in the disk by a close binary companion (cite: Lee2020). Adopting a protostellar mass of 0.035 $M_\odot$, the variation with $\sim$8 years and $\sim$50 years could be induced by events at 1.3 au and 4.4 au, respectively, which cannot be resolved by the present observations where the major axis of the continuum emission (FWHM) is 71.1 $\pm$ 2.6 mas (30.4 $\pm$ 1.1 au). L1157 MMS, with a separation of 16 au, is the tightest known binary among the directly observed Class 0 protostars (cite: Tobin2022). Such small scales required detection via VLA continuum observations. Interestingly, the wiggle in the Class 0 protostellar jet HH 211 implies a binary separation of $\sim$4.6 au (cite: Lee2010). Theoretical modeling finds that the circumstellar disk is truncated by interaction with a binary such that the disk radius is 0.25–0.5 the binary semi-major axis distance (cite: Terqeum1999). Thus, for HOPS 373SW the 1.3 au length scale might be associated with the disk radius while the 4.4 au scale represents the separation of the binary.

This putative close binary could reproduce the wiggle pattern of the SiO EHV emission shown in Figure [1](#fig:jets). When a protostar has a mass of $M_p$, a disk radius of $r_{\rm d}$, and a companion is separated with a distance of $a$ and has a mass of $M_c$, then the ratio of precession period $\tau_p$ to orbital period $\tau_o$ is given by : $$\begin{equation}
    \frac{\tau_p}{\tau_o}=\frac{32}{15\cos{\beta}}\left(\frac{a}{r_{\rm d}}\right)^{3/2}\left(1 +\frac{M_c}{M_p}\right)^{1/2}\left(\frac{M_p}{M_c}\right),
\end{equation}$$ where $\beta$ is the half-openning angle (cite: Terqeum1999; Lee2020). Thus, $\tau_p$ is $\sim$15 times longer than $\tau_o$ assuming $M_p/M_c$=1. The wiggling pattern is described by the parametric equation using $\beta$, $V_j\cdot\tau_p$ (the spatial period), the phase angle ($\phi$), and the inclination (cite: Schutzer2022). The wiggle motion is roughly reproduced by the precession model assuming $M_p/M_c$=1 and using the parameters $V_j$, $P = \tau_o$, and $i$ from the jet model (Table  [\[tb:jetmodel\]](#tb:jetmodel)), $\beta$= 8$^\circ$, and $\phi$= 50$^\circ$ as shown in the red and blue curved lines in the bottom panel of Figure [1](#fig:jets).

![](fig10.eps)

According to the relic record provided by the observed knots, many burst events should have occurred in the past. Figure [10](#fig:aca) shows an anti-correlation between the C$^{18}$O 2–1 and N$_2$D$^+$ emission. The C$^{18}$O emission has the Full Width Half Maximum (FWHM) of 4.$''$63 $\pm$ 0.$''$61 which is measured by the CASA task, ‘imfit’. The expected FWHM from the current luminosity (5.3 $L_\odot$) is 1.$''$8 when the CO sublimation temperature is 21 K (cite: Frimann2017). Thus, the current CO emission is a factor of 2.6 more extended than that expected from the current luminosity. In addition, the peak of the N$_2$D$^+$ is 6.$''$3–7.$''$4 off from the center of HOPS 373SW, implying the luminosity during a past burst reached $\sim$40–60  $L_\odot$ (cite: Hsieh2019; Murillo2022).

We note that HOPS 373SW is very likely the dominant trigger for the extended CO snowline because the distribution of N$_2$D$^+$ emission implies the heating source is closer to the HOPS 373SW rather than HOPS 373NE, and the C$^{18}$O 2–1 emission peak is also close to the HOPS 373SW. Furthermore, the orientation of the two N$_2$D$^+$ peaks is approximately perpendicular to the large-scale CO outflow in the SE-NW direction, implying that the large-scale CO outflow is also associated with HOPS 373SW rather than HOPS 373NE.

The freeze-out time scales for CO and water provide an upper limit for when this large burst occurred. The number density of molecular hydrogen around the observed CO snowline is $\sim$5 $\times$ 10$^{5}$ cm$^{-3}$ when the density profile for HOPS 373 presented in (cite: Furlan2016) is adopted. At this density, the freeze-out time scale for CO is $\sim$10$^4$ years (cite: jelee04). On the other hand, the water snowline, which is derived by the boundary of emission distribution of complex organic molecules ($\sim$0.$''$1), is similar to that derived from the current luminosity (cite: Lee2023). The water snowline for a large burst (40–60 $L_\odot$) is $\sim$0.$''$23 (100 au at the distance of 428 pc), where the density is higher compared to that at the CO snowline and the freeze-out time scale for the water is $\sim$100 years (cite: vantHoff2022; Lee2023). Thus, we expect that this recent burst occurred between the freeze-out time scales for the CO and the water (between $\sim$10$^2$ and $\sim$10$^4$ years). The dynamical time scales of Outflow1 (150 years), Outflow2 ($\sim$500 years), and the large scale CO outflow in the SE-NW direction (cite: Nagy2020) are all within the estimated time range of the accretion burst that induced the observed CO snowline. Thus, the strongest burst associated with one of the three outflows likely shaped the observed CO snowline. Further observations and studies are needed to determine which outflow is associated with this strongest burst event.

## Origin of multiple Outflows

The SiO, CH$_3$OH, and CO lines toward HOPS 373SW reveal two outflows: Outflow1 (NE-SW) and Outflow2 (SE-NW). In addition, the large-scale CO outflow in the SE-NW direction was also ejected from HOPS 373SW. A possible explanation for these features is that the three outflows were successively ejected from a single protostar. Initially, the large-scale CO outflow had been ejected $\sim$10$^4$ years ago (cite: Nagy2020). Then, Outflow2 was ejected $\sim$370–500 years ago and lastly Outflow1 was formed $\sim$150 years ago after the system went through a reorientation, as appears to be the case for IRAS 15398-3359 (cite: Okoda2021). Given that HOPS 373 is an early stage Class 0 protostar (cite: Kang2015; Furlan2016; Stutz2013), it expected that the angular momentum axis of the accreting gas might change over time due to in-homogeneities in the star-forming core (cite: Sakai2018; Zhang2019; Gaudel2020; Okoda2021). In addition, the outflow reorientation also occurs when the rotation axis of the core is misaligned with the global magnetic field direction (cite: Machida2020). The extended CO snowline suggests that a strong accretion burst occurred 10$^2$–10$^4$ years ago. Therefore, the three observed misaligned outflows may have been induced by accretion bursts accompanied by reorientation.

A second possible explanation for the two outflows is that they are evidence of a tight protostellar binary. In this case as well, the change in the outflow axis from the large scale CO outflow in the SE-NW direction to Outflow1 or Outflow2 occurred by an accretion burst accompanied by reorientation. The EHV SiO jet shows the wiggling motion, which could be due the precession induced by a close-binary system as mentioned above. Quasi-episodic knots with a period of 50 years also support this hypothesis (cite: Lee2020). As mentioned above, it is possible that the knot HR2b is associated with Outflow2 and that the CH$_3$OH emission peaks CR2, CR1, and CB1 are on the trajectory of the bow shocks LR2 and LB2. If those CH$_3$OH peaks are associated with Outflow2, then CR1 and CB1 would have be ejected $\sim$130 years ago, similar to the time scale of the terminal knots ($\sim$150 years) in Outflow1. In addition, the two outflows have different spatial properties. They are misaligned by $\sim$30$^\circ$  and the jet velocities are $\sim$90 km s$^{-1}$  and $\sim$30 km s$^{-1}$, respectively. Therefore, each outflow might have been ejected by a different member of a close-in protostellar binary.

Such a misaligned close binary could be formed through core fragmentation. Misaligned outflows with an angle of 70$^\circ$  have been reported in the Class 0 protostellar binary system VLA 1623 A, where the binary separation is 36 au (cite: Hara2021). The binary separation in the HOPS 373SW is estimated to be 4.4 au (see above), which cannot be resolved with the present high-resolution continuum image (FWHM $\sim$34 au). Such a misaligned close binary might be formed initially at larger separations via turbulent fragmentation and have later migrated inward (cite: jelee17; Lee2019; Offner2022). We note that magnetohydrodynamic simulations (cite: Lee2019; Saiki2020) show that close binaries ($<$ 30 au) can be formed via core fragmentation. A recent hydrodynamical simulation for a multiple protostellar system also showed that the interaction between a close binary could also result in misaligned disks (cite: jelee23b).

# Summary

We have investigated the jets and outflows in HOPS 373SW using high-resolution ALMA observations of the SiO 8–7, CH$_3$OH, and CO 3–2 lines. The results are:

\(1\) The slow moving SiO and CH$_3$OH  show two distinct bow shocks which surround two separate CO outflows: Outflow1 (NE-SW) and Outflow2 (SE-NW).

\(2\) The extreme high velocity (EHV) and fast moving SiO emission show several knots, which could be formed in quasi-episodic jets with an inclination of 37$^\circ$, a jet velocity of 91 km s$^{-1}$, and a period of 50 years. These knots also show a wiggle motion previously noted in the CO and H$_2$ emissions by (cite: Yoon2022).

\(3\) The SiO jets show two periodic variation timescales with periods of 50 years and 8 years. The stellar mass is estimated to be 0.035 $M_\odot$ in which case the longer the periodic variation might be induced by a binary with a separation of 4.4 au.

\(4\) The observed extended CO snow line implies that a previous outburst with a luminosity of 40–60 $L_\odot$ occurred between $\sim$10$^2$ and $\sim$10$^4$ years ago. It is possible that the observed CO snowline is associated with either the bow shock LR1 and LB1 ($\sim$150 years ago) or the large scale CO outflow in the SE-NW direction ($\sim$10$^4$ years ago).

\(5\) The two observed misaligned outflows appear to have either be ejected from a single protostar, due to a reorientation of the angular momentum axis, or from protostellar binary, where each outflow is related to a different binary component. The necessary tight binary would have been formed thorough core fragmentation with a wider separation and after which it migrated inward.

# Acknowledgements

This work is supported by the Korea Astronomy and Space Science Institute under the R&D program (Project No. 2024-1-841-00) supervised by the Ministry of Science and ICT. J.-E. Lee is supported by National Research Foundation of Korea (NRF) grant funded by the Korea government (MSIT) (grant number 2021R1A2C1011718). G.J.H. is supported by general grants 12173003 awarded by the National Science Foundation of China. D.J. is supported by NRC Canada and by an NSERC Discovery Grant. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under a cooperative agreement by Associated Universities, Inc.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00386.T, ADS/JAO.ALMA#2015.1.0041.S, and ADS/JAO.ALMA#2018.1.01565.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

natexlab

(ref: Audard2014) Audard, M., Ábrahám, P., Dunham, M. M., et al. 2014, Protostars and Planets VI, 387, doi: [`10.2458/azu_uapress_9780816531240-ch017`](http://doi.org/10.2458/azu_uapress_9780816531240-ch017)

(ref: Balanca2018) Balança, C., Dayou, F., Faure, A., Wiesenfeld, L., & Feautrier, N. 2018, MNRAS, 479, 2692, doi: [`10.1093/mnras/sty1681`](http://doi.org/10.1093/mnras/sty1681)

(ref: Codella2020) Codella, C., Ceccarelli, C., Bianchi, E., et al. 2020, A&A, 635, A17, doi: [`10.1051/0004-6361/201936725`](http://doi.org/10.1051/0004-6361/201936725)

(ref: Schutzer2022) de A. Schutzer, A., Rivera-Ortiz, P. R., Lefloch, B., et al. 2022, A&A, 662, A104, doi: [`10.1051/0004-6361/202142931`](http://doi.org/10.1051/0004-6361/202142931)

(ref: Simone2022) De Simone, M., Codella, C., Ceccarelli, C., et al. 2022, MNRAS, 512, 5214, doi: [`10.1093/mnras/stac083`](http://doi.org/10.1093/mnras/stac083)

(ref: Dullemond2001) Dullemond, C. P., Dominik, C., & Natta, A. 2001, ApJ, 560, 957, doi: [`10.1086/323057`](http://doi.org/10.1086/323057)

(ref: Dutta2022a) Dutta, S., Lee, C.-F., Johnstone, D., et al. 2022a, ApJ, 925, 11, doi: [`10.3847/1538-4357/ac3424`](http://doi.org/10.3847/1538-4357/ac3424)

(ref: Dutta2022b) Dutta, S., Lee, C.-F., Hirano, N., et al. 2022b, ApJ, 931, 130, doi: [`10.3847/1538-4357/ac67a1`](http://doi.org/10.3847/1538-4357/ac67a1)

(ref: Dyda2015) Dyda, S., Lovelace, R. V. E., Ustyugova, G. V., et al. 2015, MNRAS, 450, 481, doi: [`10.1093/mnras/stv623`](http://doi.org/10.1093/mnras/stv623)

(ref: Fischer2022) Fischer, W. J., Hillenbrand, L. A., Herczeg, G. J., et al. 2022, arXiv e-prints, arXiv:2203.11257. [`https://arxiv.org/abs/2203.11257`](https://arxiv.org/abs/2203.11257)

(ref: Frank2014) Frank, A., Ray, T. P., Cabrit, S., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 451, doi: [`10.2458/azu_uapress_9780816531240-ch020`](http://doi.org/10.2458/azu_uapress_9780816531240-ch020)

(ref: Frimann2017) Frimann, S., Jørgensen, J. K., Dunham, M. M., et al. 2017, A&A, 602, A120, doi: [`10.1051/0004-6361/201629739`](http://doi.org/10.1051/0004-6361/201629739)

(ref: Furlan2016) Furlan, E., Fischer, W. J., Ali, B., et al. 2016, ApJS, 224, 5, doi: [`10.3847/0067-0049/224/1/5`](http://doi.org/10.3847/0067-0049/224/1/5)

(ref: Gaudel2020) Gaudel, M., Maury, A. J., Belloche, A., et al. 2020, A&A, 637, A92, doi: [`10.1051/0004-6361/201936364`](http://doi.org/10.1051/0004-6361/201936364)

(ref: Gomez-Ruiz2013) Gómez-Ruiz, A. I., Hirano, N., Leurini, S., & Liu, S. Y. 2013, A&A, 558, A94, doi: [`10.1051/0004-6361/201118473`](http://doi.org/10.1051/0004-6361/201118473)

(ref: Gusdorf2008) Gusdorf, A., Cabrit, S., Flower, D. R., & Pineau Des Forêts, G. 2008, A&A, 482, 809, doi: [`10.1051/0004-6361:20078900`](http://doi.org/10.1051/0004-6361:20078900)

(ref: Hara2021) Hara, C., Kawabe, R., Nakamura, F., et al. 2021, ApJ, 912, 34, doi: [`10.3847/1538-4357/abb810`](http://doi.org/10.3847/1538-4357/abb810)

(ref: Hartmann1996) Hartmann, L., & Kenyon, S. J. 1996, ARA&A, 34, 207, doi: [`10.1146/annurev.astro.34.1.207`](http://doi.org/10.1146/annurev.astro.34.1.207)

(ref: Herbig1966) Herbig, G. H. 1966, Vistas in Astronomy, 8, 109, doi: [`10.1016/0083-6656(66)90025-0`](http://doi.org/10.1016/0083-6656(66)90025-0)

(ref: Hirano2010) Hirano, N., Ho, P. P. T., Liu, S.-Y., et al. 2010, ApJ, 717, 58, doi: [`10.1088/0004-637X/717/1/58`](http://doi.org/10.1088/0004-637X/717/1/58)

(ref: Hirth1994) Hirth, G. A., Mundt, R., Solf, J., & Ray, T. P. 1994, ApJL, 427, L99, doi: [`10.1086/187374`](http://doi.org/10.1086/187374)

(ref: Hsieh2019) Hsieh, T.-H., Murillo, N. M., Belloche, A., et al. 2019, ApJ, 884, 149, doi: [`10.3847/1538-4357/ab425a`](http://doi.org/10.3847/1538-4357/ab425a)

(ref: Jhan2021) Jhan, K.-S., & Lee, C.-F. 2021, ApJ, 909, 11, doi: [`10.3847/1538-4357/abd6c5`](http://doi.org/10.3847/1538-4357/abd6c5)

(ref: Jhan2022) Jhan, K.-S., Lee, C.-F., Johnstone, D., et al. 2022, ApJL, 931, L5, doi: [`10.3847/2041-8213/ac6a53`](http://doi.org/10.3847/2041-8213/ac6a53)

(ref: Johnstone2001) Johnstone, D., Fich, M., Mitchell, G. F., & Moriarty-Schieven, G. 2001, ApJ, 559, 307, doi: [`10.1086/322323`](http://doi.org/10.1086/322323)

(ref: Jorgensen2015) Jørgensen, J. K., Visser, R., Williams, J. P., & Bergin, E. A. 2015, A&A, 579, A23, doi: [`10.1051/0004-6361/201425317`](http://doi.org/10.1051/0004-6361/201425317)

(ref: Kang2015) Kang, M., Choi, M., Stutz, A. M., & Tatematsu, K. 2015, ApJ, 814, 31, doi: [`10.1088/0004-637X/814/1/31`](http://doi.org/10.1088/0004-637X/814/1/31)

(ref: Kounkel2018) Kounkel, M., Covey, K., Suárez, G., et al. 2018, AJ, 156, 84, doi: [`10.3847/1538-3881/aad1f1`](http://doi.org/10.3847/1538-3881/aad1f1)

(ref: Larson1969) Larson, R. B. 1969, MNRAS, 145, 271, doi: [`10.1093/mnras/145.3.271`](http://doi.org/10.1093/mnras/145.3.271)

(ref: Lee2019) Lee, A. T., Offner, S. S. R., Kratter, K. M., Smullen, R. A., & Li, P. S. 2019, ApJ, 887, 232, doi: [`10.3847/1538-4357/ab584b`](http://doi.org/10.3847/1538-4357/ab584b)

(ref: Lee2010) Lee, C.-F., Hasegawa, T. I., Hirano, N., et al. 2010, ApJ, 713, 731, doi: [`10.1088/0004-637X/713/2/731`](http://doi.org/10.1088/0004-637X/713/2/731)

(ref: Lee2004) Lee, C.-F., & Sahai, R. 2004, ApJ, 606, 483, doi: [`10.1086/381677`](http://doi.org/10.1086/381677)

(ref: Lee2013) Lee, J., Lee, J.-E., Lee, S., et al. 2013, ApJS, 209, 4, doi: [`10.1088/0067-0049/209/1/4`](http://doi.org/10.1088/0067-0049/209/1/4)

(ref: Lee2007) Lee, J.-E. 2007, Journal of Korean Astronomical Society, 40, 83, doi: [`10.5303/JKAS.2007.40.4.083`](http://doi.org/10.5303/JKAS.2007.40.4.083)

(ref: jelee04) Lee, J.-E., Bergin, E. A., & Evans, Neal J., I. 2004, ApJ, 617, 360, doi: [`10.1086/425153`](http://doi.org/10.1086/425153)

(ref: jelee17) Lee, J.-E., Lee, S., Dunham, M. M., et al. 2017, Nature Astronomy, 1, 0172, doi: [`10.1038/s41550-017-0172`](http://doi.org/10.1038/s41550-017-0172)

(ref: Lee2023) Lee, J.-E., Baek, G., Lee, S., et al. 2023a, ApJ, 956, 43, doi: [`10.3847/1538-4357/ace34b`](http://doi.org/10.3847/1538-4357/ace34b)

(ref: jelee23b) Lee, J.-E., Matsumoto, T., Kim, H.-J., et al. 2023b, ApJ, 953, 82, doi: [`10.3847/1538-4357/acdd5b`](http://doi.org/10.3847/1538-4357/acdd5b)

(ref: Lee2020) Lee, S., Lee, J.-E., Aikawa, Y., Herczeg, G., & Johnstone, D. 2020, ApJ, 889, 20, doi: [`10.3847/1538-4357/ab5a7e`](http://doi.org/10.3847/1538-4357/ab5a7e)

(ref: Liu2012) Liu, C.-F., & Shang, H. 2012, ApJ, 761, 94, doi: [`10.1088/0004-637X/761/2/94`](http://doi.org/10.1088/0004-637X/761/2/94)

(ref: Machida2020) Machida, M. N., Hirano, S., & Kitta, H. 2020, MNRAS, 491, 2180, doi: [`10.1093/mnras/stz3159`](http://doi.org/10.1093/mnras/stz3159)

(ref: Masunaga1998) Masunaga, H., Miyama, S. M., & Inutsuka, S.-i. 1998, ApJ, 495, 346, doi: [`10.1086/305281`](http://doi.org/10.1086/305281)

(ref: Monnier2002) Monnier, J. D., & Millan-Gabet, R. 2002, ApJ, 579, 694, doi: [`10.1086/342917`](http://doi.org/10.1086/342917)

(ref: Murillo2022) Murillo, N. M., Hsieh, T. H., & Walsh, C. 2022, A&A, 665, A68, doi: [`10.1051/0004-6361/202142982`](http://doi.org/10.1051/0004-6361/202142982)

(ref: Nagy2020) Nagy, Z., Menechella, A., Megeath, S. T., et al. 2020, A&A, 642, A137, doi: [`10.1051/0004-6361/201937342`](http://doi.org/10.1051/0004-6361/201937342)

(ref: Nesterenok2018) Nesterenok, A. V. 2018, Ap&SS, 363, 151, doi: [`10.1007/s10509-018-3370-6`](http://doi.org/10.1007/s10509-018-3370-6)

(ref: Nisini2015) Nisini, B., Santangelo, G., Giannini, T., et al. 2015, ApJ, 801, 121, doi: [`10.1088/0004-637X/801/2/121`](http://doi.org/10.1088/0004-637X/801/2/121)

(ref: Offner2022) Offner, S. S. R., Moe, M., Kratter, K. M., et al. 2022, arXiv e-prints, arXiv:2203.10066. [`https://arxiv.org/abs/2203.10066`](https://arxiv.org/abs/2203.10066)

(ref: Okoda2021) Okoda, Y., Oya, Y., Francis, L., et al. 2021, ApJ, 910, 11, doi: [`10.3847/1538-4357/abddb1`](http://doi.org/10.3847/1538-4357/abddb1)

(ref: Park21) Park, W., Lee, J.-E., Contreras Peña, C., et al. 2021, ApJ, 920, 132, doi: [`10.3847/1538-4357/ac1745`](http://doi.org/10.3847/1538-4357/ac1745)

(ref: Penston1969) Penston, M. V. 1969, MNRAS, 144, 425, doi: [`10.1093/mnras/144.4.425`](http://doi.org/10.1093/mnras/144.4.425)

(ref: Plunkett2015) Plunkett, A. L., Arce, H. G., Mardones, D., et al. 2015, Nature, 527, 70, doi: [`10.1038/nature15702`](http://doi.org/10.1038/nature15702)

(ref: Podio2016) Podio, L., Codella, C., Gueth, F., et al. 2016, A&A, 593, L4, doi: [`10.1051/0004-6361/201628876`](http://doi.org/10.1051/0004-6361/201628876)

(ref: Podio2021) Podio, L., Tabone, B., Codella, C., et al. 2021, A&A, 648, A45, doi: [`10.1051/0004-6361/202038429`](http://doi.org/10.1051/0004-6361/202038429)

(ref: Rabenanahary2022) Rabenanahary, M., Cabrit, S., Meliani, Z., & Pineau des Forêts, G. 2022, A&A, 664, A118, doi: [`10.1051/0004-6361/202243139`](http://doi.org/10.1051/0004-6361/202243139)

(ref: Rabli2010) Rabli, D., & Flower, D. R. 2010, MNRAS, 406, 95, doi: [`10.1111/j.1365-2966.2010.16671.x`](http://doi.org/10.1111/j.1365-2966.2010.16671.x)

(ref: Raga1990) Raga, A. C., Canto, J., Binette, L., & Calvet, N. 1990, ApJ, 364, 601, doi: [`10.1086/169443`](http://doi.org/10.1086/169443)

(ref: Rice2015) Rice, T. S., Reipurth, B., Wolk, S. J., Vaz, L. P., & Cross, N. J. G. 2015, AJ, 150, 132, doi: [`10.1088/0004-6256/150/4/132`](http://doi.org/10.1088/0004-6256/150/4/132)

(ref: Saigo2006) Saigo, K., & Tomisaka, K. 2006, ApJ, 645, 381, doi: [`10.1086/504028`](http://doi.org/10.1086/504028)

(ref: Saiki2020) Saiki, Y., & Machida, M. N. 2020, ApJL, 897, L22, doi: [`10.3847/2041-8213/ab9d86`](http://doi.org/10.3847/2041-8213/ab9d86)

(ref: Sakai2018) Sakai, N., Hanawa, T., Zhang, Y., et al. 2018, Nature, 565, 206, doi: [`10.1038/s41586-018-0819-2`](http://doi.org/10.1038/s41586-018-0819-2)

(ref: Schoier2005) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369, doi: [`10.1051/0004-6361:20041729`](http://doi.org/10.1051/0004-6361:20041729)

(ref: Stutz2013) Stutz, A. M., Tobin, J. J., Stanke, T., et al. 2013, ApJ, 767, 36, doi: [`10.1088/0004-637X/767/1/36`](http://doi.org/10.1088/0004-637X/767/1/36)

(ref: Suutarinen2014) Suutarinen, A. N., Kristensen, L. E., Mottram, J. C., Fraser, H. J., & van Dishoeck, E. F. 2014, MNRAS, 440, 1844, doi: [`10.1093/mnras/stu406`](http://doi.org/10.1093/mnras/stu406)

(ref: Tabone2020) Tabone, B., Godard, B., Pineau des Forêts, G., Cabrit, S., & van Dishoeck, E. F. 2020, A&A, 636, A60, doi: [`10.1051/0004-6361/201937383`](http://doi.org/10.1051/0004-6361/201937383)

(ref: Tafalla2010) Tafalla, M., Santiago-Garcı́a, J., Hacar, A., & Bachiller, R. 2010, A&A, 522, A91, doi: [`10.1051/0004-6361/201015158`](http://doi.org/10.1051/0004-6361/201015158)

(ref: Terqeum1999) Terquem, C., Eislöffel, J., Papaloizou, J. C. B., & Nelson, R. P. 1999, ApJL, 512, L131, doi: [`10.1086/311880`](http://doi.org/10.1086/311880)

(ref: Tobin2022) Tobin, J. J., Cox, E. G., & Looney, L. W. 2022, ApJ, 928, 61, doi: [`10.3847/1538-4357/ac5594`](http://doi.org/10.3847/1538-4357/ac5594)

(ref: Tobin2007) Tobin, J. J., Looney, L. W., Mundy, L. G., Kwon, W., & Hamidouche, M. 2007, ApJ, 659, 1404, doi: [`10.1086/512720`](http://doi.org/10.1086/512720)

(ref: Tobin2015) Tobin, J. J., Stutz, A. M., Megeath, S. T., et al. 2015, ApJ, 798, 128, doi: [`10.1088/0004-637X/798/2/128`](http://doi.org/10.1088/0004-637X/798/2/128)

(ref: Tobin2016) Tobin, J. J., Stutz, A. M., Manoj, P., et al. 2016, ApJ, 831, 36, doi: [`10.3847/0004-637X/831/1/36`](http://doi.org/10.3847/0004-637X/831/1/36)

(ref: Tobin2020) Tobin, J. J., Sheehan, P. D., Megeath, S. T., et al. 2020, ApJ, 890, 130, doi: [`10.3847/1538-4357/ab6f64`](http://doi.org/10.3847/1538-4357/ab6f64)

(ref: Tychoniec2019) Tychoniec, Ł., Hull, C. L. H., Kristensen, L. E., et al. 2019, A&A, 632, A101, doi: [`10.1051/0004-6361/201935409`](http://doi.org/10.1051/0004-6361/201935409)

(ref: Tychoniec2021) Tychoniec, Ł., van Dishoeck, E. F., van’t Hoff, M. L. R., et al. 2021, A&A, 655, A65, doi: [`10.1051/0004-6361/202140692`](http://doi.org/10.1051/0004-6361/202140692)

(ref: vanderTak2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: vantHoff2022) van’t Hoff, M. L. R., Harsono, D., van Gelder, M. L., et al. 2022, ApJ, 924, 5, doi: [`10.3847/1538-4357/ac3080`](http://doi.org/10.3847/1538-4357/ac3080)

(ref: Velusamy2011) Velusamy, T., Langer, W. D., Kumar, M. S. N., & Grave, J. M. C. 2011, ApJ, 741, 60, doi: [`10.1088/0004-637X/741/1/60`](http://doi.org/10.1088/0004-637X/741/1/60)

(ref: Yang2010) Yang, B., Stancil, P. C., Balakrishnan, N., & Forrey, R. C. 2010, ApJ, 718, 1062, doi: [`10.1088/0004-637X/718/2/1062`](http://doi.org/10.1088/0004-637X/718/2/1062)

(ref: Yoon2022) Yoon, S.-Y., Herczeg, G. J., Lee, J.-E., et al. 2022, ApJ, 929, 60, doi: [`10.3847/1538-4357/ac5632`](http://doi.org/10.3847/1538-4357/ac5632)

(ref: Yoshida2021) Yoshida, T., Hsieh, T.-H., Hirano, N., & Aso, Y. 2021, ApJ, 906, 112, doi: [`10.3847/1538-4357/abc94f`](http://doi.org/10.3847/1538-4357/abc94f)

(ref: Zhang2019) Zhang, Y., Tan, J. C., Tanaka, K. E. I., et al. 2019, Nature Astronomy, 3, 517, doi: [`10.1038/s41550-019-0718-y`](http://doi.org/10.1038/s41550-019-0718-y)

</paper>

Write the methods card for this paper.