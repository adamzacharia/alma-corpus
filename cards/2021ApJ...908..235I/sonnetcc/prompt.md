# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...908..235I\sonnetcc\reply.txt

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
 "bibcode": "2021ApJ...908..235I",
 "title": "Subaru High-z Exploration of Low-luminosity Quasars (SHELLQs). XII. Extended [C II] Structure (Merger or Outflow) in a z = 6.72 Red Quasar",
 "year": 2021,
 "journal": "The Astrophysical Journal",
 "first_author": "Izumi, Takuma",
 "n_authors": 34,
 "arxiv_id": "2101.01199",
 "doi": "10.3847/1538-4357/abd7ef",
 "alma_projects_linked_by_archive": [
  "2019.1.00074.S"
 ]
}
```

Paper text:
<paper>
# Subaru High-z Exploration of Low-Luminosity Quasars (SHELLQs) XII.\
Extended \[C II\] Structure (Merger or Outflow) in a $z = 6.72$ Red Quasar

## Abstract

We present ALMA \[C II\] 158 $\mu$m line and far-infrared (FIR) continuum emission observations toward HSC J120505.09$-$000027.9 (J1205$-$0000) at $z = 6.72$ with the beam size of $\sim 0\ensuremath{''}.8 \times 0\ensuremath{''}.5$ (or 4.1 kpc $\times$ 2.6 kpc), the most distant red quasar known to date. Red quasars are modestly reddened by dust, and are thought to be in rapid transition from an obscured starburst to an unobscured normal quasar, driven by powerful active galactic nucleus (AGN) feedback which blows out a cocoon of interstellar medium (ISM). The FIR continuum of J1205$-$0000 is bright, with an estimated luminosity of $L_{\rm FIR} \sim 3 \times 10^{12}~L_\odot$. The \[C II\] line emission is extended on scales of $r \sim 5$ kpc, greater than the FIR continuum. The line profiles at the extended regions are complex and broad (FWHM $\sim 630-780$ km s$^{-1}$). Although it is not practical to identify the nature of this extended structure, possible explanations include (i) companion/merging galaxies and (ii) massive AGN-driven outflows. For the case of (i), the companions are modestly star-forming ($\sim 10~M_\odot$ yr$^{-1}$), but are not detected by our Subaru optical observations ($y_{\rm AB,5\sigma} = 24.4$ mag). For the case of (ii), our lower-limit to the cold neutral outflow rate is $\sim 100~M_\odot$ yr$^{-1}$. The outflow kinetic energy and momentum are both much smaller than what predicted in energy-conserving wind models, suggesting that the AGN feedback in this quasar is not capable of completely suppressing its star formation.

# Introduction

It has long been considered that mergers or interactions of gas-rich galaxies are the trigger for intense starburst and black hole growth (cite: 1988ApJ...325...74S; 2006ApJS..163....1H). In this scenario, a substantial fraction of the black hole growth takes place inside a dusty starburst, during which time the system appears as an obscured active galactic nucleus (cite: 2018ARA&A..56..625H). Subsequent strong AGN feedback, particularly in the form of massive outflows (cite: 2012MNRAS.425L..66M; 2014A&A...562A..21C; 2016A&A...591A..28C; 2019A&A...630A..59B; 2019MNRAS.483.4586F; 2020A&A...633A.134L), is expected to clear gas and dust from the galaxy, halting further star formation and black hole growth. This feedback is also invoked in galaxy evolution models to shape the galaxy mass function and ultimately black hole-host galaxy co-evolution relations (cite: 2013ARA&A..51..511K).

High-redshift quasars are a unique laboratory to test or refine our understanding of the early supermassive black hole (SMBH) and galaxy formation (cite: 2019arXiv191105791I). To date, ${}>200$ quasars with absolute ultraviolet (UV) magnitude $M_{\rm 1450} \lesssim -22$ are known at $z > 5.7$, most of which were discovered by wide-field optical and near-infrared surveys (cite: 2001AJ....122.2833F; 2016ApJS..227...11B; 2016ApJ...828...26M; 2018PASJ...70S..35M; 2018ApJS..237....5M). Sub/millimeter observations have revealed that their host galaxies often possess copious amounts of dust ($\sim 10^8~M_\odot$) and gas ($\sim 10^{10}~M_\odot$) with high star formation rates (SFR) of $\gtrsim 100$–$1000~M_\odot$ yr$^{-1}$ (cite: 2013ApJ...773...44W; 2016ApJ...816...37V; 2017ApJ...845..154V; 2018ApJ...854...97D), while smaller values are found in lower luminosity quasars (cite: 2013ApJ...770...13W; 2015ApJ...801..123W; 2017ApJ...850..108W; 2018PASJ...70...36I; 2019PASJ...71..111I).

As a galaxy-overdensity increases the likelihood of interactions and mergers of galaxies, deep submillimeter searches for companion star-forming galaxies have been performed toward $z \gtrsim 6$ quasars mainly by using the Atacama Large Millimeter/submillimeter Array (ALMA). Such efforts tried to detect C$^+$ ${}^2P_{3/2} \rightarrow {}^2P_{1/2}$ 157.74 $\ensuremath{\mu}m$ (hereafter \[C II\] 158 $\ensuremath{\mu}m$) line and/or rest-frame far-infrared (FIR) continuum emission from companions. Indeed, some works found companions (cite: 2017Natur.545..457D; 2017ApJ...836....8T; 2017ApJ...850..108W; 2019ApJ...882...10N), or very close likely-merging galaxies (cite: 2019ApJ...880..157D; 2019ApJ...874L..30V; 2019ApJ...881L..23B), to the optically-luminous ($M_{\rm 1450} \lesssim -26$ mag) quasars, which would support the triggering of quasars by gas-rich major mergers. Contrary to this, no overdensity of submillimeter continuum emitters was reported for the case of optically less-luminous ($M_{\rm 1450} \gtrsim -25$ mag) quasars (cite: 2019PASJ...71..111I), implying that rather secular processes (cite: 2019MNRAS.482.4846S; 2020MNRAS.494.2747M) may also be capable of triggering $z \gtrsim 6$ quasars.

As massive quiescent galaxies already exist at $z \sim 3-4$ (cite: 2014ApJ...783L..14S; 2020ApJ...898..171E), we also anticipate that AGN feedback is already taking place at higher redshift. An outstanding case is the $z = 6.42$ quasar J1148$+$5251, in which a massive AGN-driven outflow (outflow rate $\dot{M}_{\rm out} > 1400~M_\odot$ yr$^{-1}$) extending to $r > 10$ kpc is detected in the \[C II\] 158 $\ensuremath{\mu}m$ emission line (cite: 2012MNRAS.425L..66M; 2015A&A...574A..14C). However, there is no other single $z>6$ quasar in which \[C II\] outflow has been reported, likely due to inadequate sensitivity. To overcome the sensitivity issue, (cite: 2019A&A...630A..59B) stacked the \[C II\] cubes of 48 quasars at $4.5 < z < 7.1$, and reported a successful detection of a broad \[C II\] wing: the inferred outflow rate ($\dot{M}_{\rm out} \sim 100~M_\odot$ yr$^{-1}$) is only modest, but may be enough to quench star formation in the central regions of these galaxies. On the other hand, (cite: 2020arXiv201014875N) performed another stacking analysis of \[C II\] cubes of 27 $z \gtrsim 6$ quasars, revealing no clear evidence of \[C II\] outflows (cite: 2018ApJ...854...97D). Hence the situation is quite controversial these days. In either case, however, previous $z \gtrsim 6$ studies are biased toward the unobscured (= blue) quasar population.

In this regard, one intriguing population of quasars, whose host galaxies have not been studied at all at $z > 6$, are the so-called *red quasars*. Unlike the unobscured population, they are reddened ($E(B-V) > 0.1$) by dust at rest-UV (cite: 2003AJ....126.1131R; 2004ApJ...607...60G; 2018ApJ...861...37G; 2015MNRAS.453.3932R). Red quasars typically have high Eddington ratios and are accompanied by broad absorption line (BAL) features indicative of nuclear fast outflows (cite: 2003AJ....126.1131R; 2009ApJ...698.1095U). At lower redshifts like $z \lesssim 2.5$, red quasars often host galaxy-scale outflows at various gas phases (cite: 2018A&A...612A..29B; 2019MNRAS.488.4126P; 2019MNRAS.489..497Z). In addition, high resolution imaging observations revealed that red quasars tend to be hosted by major mergers (cite: 2008ApJ...674...80U; 2015ApJ...806..218G). These properties support an evolutionary scenario, in which red quasars are emerging from the merger-induced dusty starburst phase likely by blowing out surrounding medium with powerful winds (cite: 2012ApJ...745..178F). However, as no red quasar has been identified at $z > 5$ primarily due to their apparent faintness in the rest-UV, it is not clear if this picture also holds in the first generation of quasars.

## Our target: J1205$-$0000

Very recently, we successfully discovered two red quasars at $z > 5.8$ (cite: 2020PASJ..tmp..230K) by matching the deep sample of quasars optically-selected from the Subaru Hyper Suprime-Cam (HSC) wide-field survey (cite: 2018PASJ...70S...4A) with mid-infrared photometric data obtained by the Wide-field Infrared Survey Explorer (WISE). In this work, we present our ALMA observations of \[C II\] 158 $\mu$m line and underlying FIR continuum emission of one of these two sources, J120505.09$-$000027.9 (hereafter 1205$-$0000; Figure [1](#fig1) top-right) at $z = 6.7$, by far the highest redshift red quasar known to date (cite: 2020PASJ..tmp..230K) [^1]. Without correcting for dust extinction, J1205$-$0000 has a rest-frame UV magnitude of $M_{\rm 1450} = -24.4$ mag (cite: 2016ApJ...828...26M). But once the extinction ($E(B-V) = 0.12$ mag) is accounted for, the quasar has $M_{\rm 1450} = -26.1$ mag, with an Eddington ratio of 0.22 (cite: 2020PASJ..tmp..230K): here the reddening was estimated by fitting a typical quasar template to the broad band (optical to mid-IR) spectral energy distribution with the Small Magellanic Cloud (SMC) dust extinction law. J1205$-$0000 hosts prominent N V and C IV BALs as well, confirming the existence of nuclear outflows (cite: 2019ApJ...880...77O).

In the following parts, we describe ALMA observations in § 2, extended nature of \[C II\] emission in § 3, and possible origins of the extended structures in § 4. We provide our conclusions in § 5. This is the twelfth in a series of publications presenting the results from our high redshift quasar survey, the Subaru High-z Exploration of Low-Luminosity Quasars (SHELLQs). Throughout this work, we adopt the standard cosmology with $H_0$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M} = 0.3$, and $\Omega_{\rm \Lambda} = 0.7$.

# ALMA Observations

We observed the redshifted \[C II\] line and FIR continuum emission of J1205$-$0000 in Band 6 on 2020 February 26 (ID = 2019.1.00074.S, PI: T. Izumi), with 41 antennas. Our observations were conducted in a single pointing with a $24\ensuremath{''}$ diameter field of view. The baseline length ranged from 15.1 m to 783.5 m, resulting in a maximum recoverable scale of $\sim 6\ensuremath{''}$. J1256$-$0547 was observed as a flux and bandpass calibrator and J1217$-$0029 was monitored to calibrate the complex gain. The total on-source time was 71 minutes.

The data were processed using `CASA` version 5.6 (<https://casa.nrao.edu>). All images were reconstructed with the `tclean` task using natural weighting to maximize the sensitivity. We averaged several channels to obtain a velocity resolution of 100 km s$^{-1}$, which resulted in a 1$\sigma$ channel sensitivity of 0.13 mJy beam$^{-1}$ (beam size = $0\ensuremath{''}.77 \times 0\ensuremath{''}.48$, P.A. = $-58\ensuremath{^\circ}$). Note that we first cleaned the line cube including the continuum emission down to 3$\sigma$ level to determine the line position. With this knowledge, we identified the channels free of line emission. All these line-free channels were integrated to generate a continuum map (1$\sigma$ = 17.6 $\mu$Jy beam$^{-1}$), which was subtracted in the $uv$ plane by using the first-order polynomial before making the final line cube.

Throughout the paper, only statistical errors are displayed unless mentioned otherwise (absolute flux uncertainty $\sim 10\%$; ALMA Cycle 7 Proposer’s Guide). As the \[C II\] emission turned out to fall at around the edge of one of the spectral windows, we display spectral data from two contiguous windows when necessary. We also used the `MIRIAD` software (cite: 1995ASPC...77..433S) for some of the analyses in this paper.

# Result: Extended \[C II\] emission

The top panels of Figure [1](#fig1) show the distributions of the velocity-integrated \[C II\] 158 $\ensuremath{\mu}m$ line emission and FIR continuum emission. The optical $y$-band image of J1205$-$0000 taken with the Subaru HSC is also shown for a reference. Figure [2](#fig2) shows the \[C II\] channel maps revealing the global velocity structure. We describe details of this emission in the following. The relevant physical properties are summarized in Table [1](#tbl1).

![](fig1.eps)

## FIR continuum properties

+------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
|                                                      | Area-integrated \[C II\] 158 $\mu$m Line Emission                                                                           |
+:====================================================:+:=======================================:+:=======================================:+:=======================================:+
| 2-4                                                  | Single Gaussian                         | Double Gaussian                                                                   |
+------------------------------------------------------+                                         +-----------------------------------------+-----------------------------------------+
| 3-4                                                  |                                         | Core                                    | Wing                                    |
+------------------------------------------------------+-----------------------------------------+-----------------------------------------+-----------------------------------------+
| $z_{\rm [CII]}$                                      | 6.7230 $\pm$ 0.0003                     | 6.7224 $\pm$ 0.0003                     | 6.7336 $\pm$ 0.0009                     |
+------------------------------------------------------+-----------------------------------------+-----------------------------------------+-----------------------------------------+
| FWHM$_{\rm [CII]}$ (km s$^{-1}$)                     | 536 $\pm$ 26                            | 442 $\pm$ 33                            | 232 $\pm$ 72                            |
+------------------------------------------------------+-----------------------------------------+-----------------------------------------+-----------------------------------------+
| $S_{\rm [CII]}\Delta V$ (Jy km s$^{-1}$)             | 1.69 $\pm$ 0.07                         | 1.49 $\pm$ 0.10                         | 0.21 $\pm$ 0.07                         |
+------------------------------------------------------+-----------------------------------------+-----------------------------------------+-----------------------------------------+
| $L_{\rm [CII]}$ (10$^8$ $L_\odot$)                   | 18.7 $\pm$ 0.8                          | 16.5 $\pm$ 1.0                          | 2.4 $\pm$ 0.8                           |
+------------------------------------------------------+-----------------------------------------+-----------------------------------------+-----------------------------------------+
| SFR$_{\rm [CII]}$ ($M_\odot$ yr$^{-1}$)              | 122 $\pm$ 5                             | 108 $\pm$ 7                             | 16 $\pm$ 6                              |
+------------------------------------------------------+-----------------------------------------+-----------------------------------------+-----------------------------------------+
| Size (beam-convolved)                                | (1$''$.55 $\pm$ 0$''$.30) $\times$ (1$''$.03 $\pm$ 0$''$.17) $=$ (8.3 $\pm$ 1.6) kpc $\times$ (5.5 $\pm$ 0.9) kpc           |
+------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| Size (beam-deconvolved)                              | (1$''$.43 $\pm$ 0$''$.36) $\times$ (0$''$.77 $\pm$ 0$''$.33) $=$ (7.7 $\pm$ 1.9) kpc $\times$ (4.1 $\pm$ 1.8) kpc           |
+------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| 1-4                                                  | \[C II\] 158 $\mu$m Line Emission at Selected Positions (Figure [1](#fig1))                                                 |
+------------------------------------------------------+-----------------------------------------+-----------------------------------------+-----------------------------------------+
|                                                      | A                                       | B                                       | C                                       |
+------------------------------------------------------+-----------------------------------------+-----------------------------------------+-----------------------------------------+
| 1-4 Line center (km s$^{-1}$)                        | $-$49 $\pm$ 54                          | 235 $\pm$ 61                            | 151 $\pm$ 69                            |
+------------------------------------------------------+-----------------------------------------+-----------------------------------------+-----------------------------------------+
| FWHM$_{\rm [CII]}$ (km s$^{-1}$)                     | 746 $\pm$ 124                           | 625 $\pm$ 145                           | 775 $\pm$ 162                           |
+------------------------------------------------------+-----------------------------------------+-----------------------------------------+-----------------------------------------+
| $S_{\rm [CII]}\Delta V$ (Jy beam$^{-1}$ km s$^{-1}$) | 0.34 $\pm$ 0.05                         | 0.22 $\pm$ 0.04                         | 0.27 $\pm$ 0.05                         |
+------------------------------------------------------+-----------------------------------------+-----------------------------------------+-----------------------------------------+
| $L_{\rm [CII]}$ (10$^8$ $L_\odot$)                   | 3.8 $\pm$ 0.6                           | 2.5 $\pm$ 0.5                           | 3.0 $\pm$ 0.6                           |
+------------------------------------------------------+-----------------------------------------+-----------------------------------------+-----------------------------------------+
| 1-4                                                  | Continuum Emission ($T_d$ = 47 K, $\beta$ = 1.6, $\kappa_{\rm 250GHz}$ = 0.4 cm$^2$ g$^{-1}$)                               |
+------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| 1-4 $f_{\rm 1.2mm}$ (mJy)                            | 1.17 $\pm$ 0.04                                                                                                             |
+------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| $L_{\rm FIR}$ (10$^{12}$ $L_\odot$)                  | 2.7 $\pm$ 0.1                                                                                                               |
+------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| $L_{\rm TIR}$ (10$^{12}$ $L_\odot$)                  | 3.9 $\pm$ 0.1                                                                                                               |
+------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| SFR$_{\rm TIR}$ ($M_\odot$ yr$^{-1}$)                | 575 $\pm$ 21                                                                                                                |
+------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| $M_{\rm dust}$ (10$^8$ $M_\odot$)                    | 2.0 $\pm$ 0.1                                                                                                               |
+------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| Size (beam-convolved)                                | (0$''$.79 $\pm$ 0$''$.02) $\times$ (0$''$.52 $\pm$ 0$''$.01) $=$ (4.3 $\pm$ 0.1) kpc $\times$ (2.8 $\pm$ 0.1) kpc           |
+------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| Size (beam-deconvolved)                              | (0$''$.25 $\pm$ 0$''$.06) $\times$ (0$''$.17 $\pm$ 0$''$.09) $=$ (1.3 $\pm$ 0.3) kpc $\times$ (0.9 $\pm$ 0.5) kpc           |
+------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+

: Observed and Derived Properties of J1205$-$0000

Table notes: The SFR$_{\rm [CII]}$ for the wing component is appropriate if this reflects a star-forming companion galaxy.

The continuum emission ($\lambda_{\rm obs} = 1.2$ mm) comes from the central $\sim 1\ensuremath{''}$ (see Table [1](#tbl1) for detailed sizes measured with the CASA task `imfit`). The continuum peaks at (RA, Dec)$_{\rm ICRS}$ = (12$^{\rm h}$05$^{\rm m}$05$^{\rm s}$.080, $-$00$\ensuremath{^\circ}$00$\ensuremath{'}$28$\ensuremath{''}$.04), which is consistent with the optical quasar position. To include all extended emission, we measure the continuum flux density with a 2$\ensuremath{''}$ diameter circular aperture placed at this peak position, resulting in $f_{\rm 1.2mm} = 1.17 \pm 0.04$ mJy.

We determine the FIR luminosity ($L_{\rm FIR}$; 42.5–122.5 $\ensuremath{\mu}m$) and the total IR luminosity ($L_{\rm TIR}$; 8–1000 $\ensuremath{\mu}m$) by assuming an optically-thin modified black body with dust temperature $T_d = 47$ K and emissivity index $\beta = 1.6$, values which are characteristic of high-redshift luminous quasars (cite: 2006ApJ...642..694B) and are commonly adopted in the literature (cite: 2018PASJ...70...36I). After correcting for the contrast and the additional heating effects of the cosmic microwave background radiation (cite: 2013ApJ...766...13D), we obtain $L_{\rm FIR} = (2.7 \pm 0.1) \times 10^{12}~L_\odot$ and $L_{\rm TIR} = (3.9 \pm 0.1) \times 10^{12}~L_\odot$, respectively. Note that there is actually a wide variety in $T_d$ from source to source (cite: 2018ApJ...866..159V). If we adopt $T_d = 35$ K, typical for local star-forming galaxies (cite: 2012ApJS..203....9U), these values become $\sim 2\times$ smaller.

With this $L_{\rm TIR}$ ($T_d = 47$ K) and the calibration of (cite: 2011ApJ...737...67M), we found a SFR of $575 \pm 21$ $M_\odot$ yr$^{-1}$. However, this should be regarded as an upper limit, as we have assumed that the FIR emission is due entirely to star formation, even though there may be a significant contribution from the AGN itself (cite: 2017MNRAS.465.1401S). Similarly, by adopting a rest-frame mass absorption coefficient of $\kappa_\nu = 0.4~(\nu/250{\rm GHz})^\beta$ cm$^2$ g$^{-1}$ (cite: 2004A&A...425..109A), we find a dust mass of $M_{\rm dust} = (2.0 \pm 0.1) \times 10^8~M_\odot$.

## \[C II\] line emission

Figure [1](#fig1) demonstrates that the \[C II\] emission is spatially more extended than the FIR continuum emission, extending to $r \sim 1\ensuremath{''}$ (5.4 kpc) [^2], and has a complex morphology. The extended structure that is directly connected to the continuum-bright core region is real, as we see positive signals from several contiguous velocity channels measured there (Figure [1](#fig1); positions A–C), over \[$-$500, $+$500\] km s$^{-1}$ relative to the systemic velocity (defined in the following).

![](fig2.eps)

Figure [3](#fig3) shows an area-integrated spectrum measured over the region within $1\ensuremath{''}.5$ radius of the nucleus in which \[C II\] integrated-intensity is detected at more than $3\sigma$. We first fit the spectrum with a single Gaussian function (Figure [3](#fig3)a), but the observed profile clearly deviates from this model; we found $\chi^2$/d.o.f. = 37.6/22 (estimated over $\pm$1200 km s$^{-1}$ range) for this single Gaussian fit. A notable deviation can be found at a positive velocity channels of $\sim 300-500$ km s$^{-1}$. As the spatially extended regions (Figure [2](#fig2)) have such high positive velocities, they must contribute to this *excess wing* of the area-integrated spectrum. We then performed a *double* Gaussian fit (Figure [3](#fig3)b) to account for that excess. This works fairly well with a returned $\chi^2$/d.o.f. = 21.1/19. With this difference in $\chi^2$, this model is preferred at $>99.9\%$ confidence. Note that we also see extended \[C II\] emission in negative velocity channels (Figure [2](#fig2)), but deeper observations are required to confirm its existence (or another wing at the bluer side of the area-integrated spectrum).

![](fig3.eps)

We naively attribute the core component in the double Gaussian fit to the host galaxy itself, hence providing its systemic redshift as $z_{\rm [CII]} = 6.7224 \pm 0.0003$. With respect to this $z_{\rm [CII]}$, Mg II emission ($z_{\rm MgII} = 6.699^{0.007}_{-0.001}$) (cite: 2019ApJ...880...77O) is blueshifted by $-1040^{+310}_{-50}$ km s$^{-1}$. In addition, an absorption feature of a higher ionization line C IV of J1205$-$0000 is further blueshifted by $\sim 2900-7400$ km s$^{-1}$ relative to Mg II (cite: 2019ApJ...880...77O), hence C IV is blueshifted up to $\sim 8500$ km s$^{-1}$ relative to $z_{\rm [CII]}$. These clearly manifest the existence of very fast nuclear outflows in this red quasar.

With the \[C II\] core flux and the 1.2 mm continuum flux density (Table [1](#tbl1)), we also measure a rest-frame \[C II\] equivalent width as $\rm{EW}_{\rm [CII]} = 0.67 \pm 0.05$ $\ensuremath{\mu}m$. This is roughly half of the mean $\rm{EW}_{\rm [CII]}$ of local star-forming galaxies (cite: 2013ApJ...774...68D). In optically low-luminosity $z > 6$ quasars (e.g., HSC quasars with $M_{\rm 1450} > -25$ mag) $\rm{EW}_{\rm [CII]}$ is usually $>1$ $\ensuremath{\mu}m$, but optically luminous quasars tend to show $\rm{EW}_{\rm [CII]} < 1$ $\ensuremath{\mu}m$ (cite: 2019PASJ...71..111I), the latter of which is consistent with the intrinsically luminous nature of J1205$-$0000 (cite: 2020PASJ..tmp..230K).

Lastly, we estimate SFR from the \[C II\] luminosity of this component (Table [1](#tbl1)), giving $108 \pm 7~M_\odot$ yr$^{-1}$ with the (cite: 2011MNRAS.416.2712D) calibration, which has $\sim 0.3$ dex dispersion. Again, this would be an upper limit, as some of the \[C II\] emission may be due to the quasar itself (i.e., narrow line region). Indeed, $L_{\rm [CII]}$ shows a marginal correlation with AGN power (cite: 2019PASJ...71..111I).

## Comparison to the other $z \gtrsim 6$ quasars

We briefly compare the quasar nuclear bolometric luminosity ($L_{\rm Bol}$) and $L_{\rm FIR}$ of a sample of $z \gtrsim 6$ quasars in Figure [4](#fig4). Here we adopted the bolometric correction factor 4.4 from 1450 Å luminosity (cite: 2006ApJS..166..470R) to compute $L_{\rm Bol}$. The same assumptions presented in § [3.1](#sec3.1) are made to derive $L_{\rm FIR}$. Optically luminous quasar data is compiled from a recent survey work of (cite: 2018ApJ...866..159V), whereas we collected the data of relatively low-luminosity quasars from (cite: 2013ApJ...770...13W; 2015ApJ...801..123W; 2017ApJ...850..108W) and (cite: 2018PASJ...70...36I; 2019PASJ...71..111I).

Although there is admittedly a wide spread in $L_{\rm FIR}$ for a given $L_{\rm Bol}$, J1205$-$0000 shows a characteristic $L_{\rm FIR}$ to the optically luminous quasars once its dust extinction is corrected. If we assume that a quasar-phase happens during a longer timescale starburst-phase (cite: 2007ApJ...671.1388D; 2008ApJS..175..356H; 2016A&A...587A..72B), there was once a growing *obscured AGN* phase in J1205$-$0000 which was embedded in this starburst host galaxy.

At the lower quasar luminosity regime, i.e., $L_{\rm Bol} < 10^{13}~L_\odot$, there are only two quasars (out of twelve) having comparable $L_{\rm FIR}$ to J1205$-$0000, namely J2239$+$0207 (cite: 2019PASJ...71..111I) and VIMOS2911 (cite: 2017ApJ...850..108W). J2239$+$0207 is likely to have a close \[C II\] companion galaxy, which may have triggered its intense starburst (cite: 2019PASJ...71..111I). VIMOS2911, which was originally discovered by (cite: 2015ApJ...798...28K), seems to be an outlier in this plane as no companion was reported (cite: 2017ApJ...850..108W), as well as its narrow \[C II\] line profile (FWHM = 264 km s$^{-1}$) indicates an absence of a merger-like active event. The remaining low-luminosity quasars all show $L_{\rm FIR} < 10^{12}~L_\odot$ (some show as low as $< 10^{11}~L_\odot$), which is clearly not the case of the optically luminous quasars.

Indeed, we found a positive correlation between $\log L_{\rm Bol}$ and $\log L_{\rm FIR}$, after excluding the objects with upper limits on $L_{\rm FIR}$, as $$\begin{equation}
\log \left( \frac{L_{\rm FIR}}{L_\odot} \right) = (0.64 \pm 0.03) \times \log \left( \frac{L_{\rm Bol}}{L_\odot} \right) + (3.55 \pm 0.45).
\end{equation}$$ A Spearman correlation coefficient for this $\log L_{\rm Bol}$–$\log L_{\rm FIR}$ data is 0.56 ($p$-value = $2.0 \times 10^{-4}$). Although it is still a marginal correlation, this implies that a black hole and its host galaxy are actually co-evolving at this high redshift. In addition, if we assume a common star-formation efficiency over the whole quasars used here, this correlation suggests that an optically luminous quasar tends to form in a gas richer galaxy. Note that (cite: 2018ApJ...866..159V) did not find a significant correlation between these two luminosities, likely because they only studied optically luminous quasars.

![](fig4.eps)

# Nature of the extended \[C II\] emission

We now turn to the physical origin of the extended \[C II\] structure, which also contributes to the \[C II\] wing in the area-integrated spectrum. Major possibilities include *companion/merging galaxy* and *cold outflow*. However, as detailed later, it is not possible to distinguish these two scenarios with the current dataset. Thus, we discuss both of these scenarios and provide relevant properties, respectively in the following. Note that other key properties including the early co-evolution of this quasar will be discussed in our forthcoming paper, along with those of the other HSC quasars observed in our ALMA Cycle 7 program (T. Izumi et al. in preparation).

## Companion/merging galaxies?

Major mergers of gas-rich galaxies has been considered to be a promising driver of quasar activity (cite: 1988ApJ...325...74S; 2005Natur.433..604D; 2006ApJS..163....1H). High resolution and/or high sensitivity observations at the low redshift universe indeed show an enhanced AGN fraction in major merger systems (cite: 2011MNRAS.418.2043E; 2011ApJ...743....2S; 2018PASJ...70S..37G; 2018Natur.563..214K). It is also noteworthy that (intrinsically luminous) red quasars tend to be hosted by major merger systems (cite: 2008ApJ...674...80U; 2015ApJ...806..218G). In this context, it is intriguing that recent sensitive ALMA observations of rest-FIR continuum and/or \[C II\] emission started to uncover star-forming companion galaxies to some $z \gtrsim 5-6$ luminous quasars (cite: 2011ApJ...739L..34W; 2017ApJ...836....8T; 2017Natur.545..457D; 2017ApJ...850..108W; 2019ApJ...882...10N), with some of these companions very close to, or even merging with, the main quasar (cite: 2019ApJ...880..157D; 2019ApJ...874L..30V; 2019ApJ...881L..23B; 2020ApJ...904..130V).

We found that the \[C II\] spatial distribution of J1205$-$0000 including the channel maps (Figures [1](#fig1) and [2](#fig2)) well resembles that of J1342$+$0928 at $z = 7.54$ (cite: 2019ApJ...881L..23B), which is considered to be an ongoing merger system. Therefore it is plausible that the extended \[C II\] structure of J1205$-$0000 is due to very close companion or merging galaxies. As the \[C II\] emission extends toward multiple directions, there could be corresponding multiple mergers in J1205$-$0000. This picture fits into an evolutionary scenario in which a red quasar corresponds to an emergent phase from a merger-induced dusty starburst. A high fraction of merger event in red quasar-host galaxies (cite: 2008ApJ...674...80U; 2015ApJ...806..218G) measured at lower redshifts also supports this scenario. Although we need higher resolution and sensitivity \[C II\] data to better understand the dynamical nature of this system, J1205$-$0000 has a great potential to be an ideal laboratory to study physical properties of merging galaxies that would eventually evolve into an unobscured luminous quasar.

Note that we do not find any companion in our optical $z$- and $y$-band maps ($\sim 0.\ensuremath{''}8$ resolution) with $5\sigma$ limiting magnitudes of ($z_{\rm AB}$, $y_{\rm AB}$) = (25.1, 24.4), taken by HSC (cite: 2016ApJ...828...26M). Although previous ALMA observations actually uncovered optically-unidentified \[C II\] or FIR continuum emitters around some $z > 6$ quasars (cite: 2017Natur.545..457D; 2019ApJ...881..163M), the situation appears to be different in J1205$-$0000. Those known companions are typically bright at FIR with SFR$_{\rm IR}$ of $> 100~M_\odot$ yr$^{-1}$. Hence their stellar emission would suffer severe dust extinction, which can make them optically unidentifiable (cite: 2019ApJ...881..163M). Contrary to this, the FIR continuum emission of J1205$-$0000 is undetected ($<1.5\sigma$) at the regions with the spatially extended \[C II\] emission (Figure [1](#fig1)). An inferred $3\sigma$ upper limit on SFR$_{\rm IR}$ by assuming a modest $T_d$ of 35 K (cite: 2012ApJS..203....9U) is only $\sim 10~M_\odot$ yr$^{-1}$. Hence a corresponding dust extinction is not so significant for the potential companions of J1205$-$0000. Rather, an insufficient optical survey depth would simply matter. If we suppose Lyman break galaxies (LBGs) are responsible for the potential companions, our $y$-band observation ($5\sigma_{\rm AB} = 24.4$ mag) only probes the bright-end of a UV luminosity function of LBGs at $z \sim 7$ (cite: 2018PASJ...70S..10O). In this regard, much deeper data from future facilities such as James Webb Space Telescope (JWST) is needed to conclusively identify the companions.

## Cold neutral outflows?

The extended and complex gas morphology of J1205$-$0000 also reminds us that of J1148$+$5251, the only other known $z > 6$ quasar with prominent \[C II\] outflows. While J1148$+$5251 is $\sim 5\times$ brighter than J1205$-$0000 at UV and the observed \[C II\] extent is as large as $r \sim 30$ kpc (cite: 2015A&A...574A..14C), this hints at the existence of cold outflows also in J1205$-$0000. In addition, the off-center \[C II\] spectra are all broad (FWHM $\gtrsim 600-800$ km s$^{-1}$). These are even broader than that of the core component, as well as than those of known companion galaxies of $z > 6$ quasars (cite: 2019ApJ...882...10N), which would prefer the outflow scenario. Thus, we discuss potential outflow properties hereafter by assuming that the extended structure is formed fully due to cold outflows. Given that the (potential) outflows are both spatially and spectrally resolved, we can measure the dynamical timescales of each \[C II\] blob defined in Figure [1](#fig1) (A, B, C). With these timescales, we follow the standard prescription (cite: 2019A&A...630A..59B) to estimate outflow rate, kinetic power, and momentum (Table [2](#tbl2)).

We define the outflow rate as $\dot{M}_{\rm out} = M_{\rm out} v_{\rm out}/R_{\rm out}$, where $M_{\rm out}$ is outflowing mass, $v_{\rm out}$ is outflow velocity, and $R_{\rm out}$ is the distance from the continuum peak. For $v_{\rm out}$, we adopt $|\Delta v| + {\rm FWHM}/2$, which combines the shift of the velocity centroid from the systemic and the FWHM of each blob. $R_{\rm out}$ is directly measured from Figure [1](#fig1) as 3.5, 6.4, and 5.1 kpc for the blobs A–C, respectively. Note that $v_{\rm out}$ is projected along the line of sight, and $R_{\rm out}$ is projected in the plane of the sky, thus, $\tau_{\rm out}$ should be corrected by a factor $|\tan \alpha|^{-1}$, where $\alpha$ is the angle between our line-of-sight and the outflow direction of each blob. While we do not know $\alpha$ a priori, the average of this factor over all angles is unity.

We calculate the outflow mass in neutral hydrogen gas $M_{\rm out}$ as $$\begin{equation}
\begin{split}
\frac{M_{\rm out}}{M_\odot} &= 0.77 \left( \frac{0.7L_{\rm [CII]}}{L_\odot} \right) \left( \frac{1.4 \times 10^{-4}}{X_{\rm C^+}} \right) \\
& \times \frac{1 + 2e^{-91/T_{\rm ex}} + n_{\rm crit}/n}{2 e^{-91/T_{\rm ex}}}
\end{split}
\end{equation}$$ where $X_{\rm C^+}$ is the C$^+$ fraction per H atom, $T_{\rm ex}$ is the excitation temperature in K, $n$ is the gas density, and $n_{\rm crit}$ is the line critical density ($\sim 3 \times 10^3$ cm$^{-3}$). As the actual gas density is unknown, we here assume the high density limit ($n \gg n_{\rm crit}$) to provide a *lower limit* on $M_{\rm out}$. The factor 0.7 in the first parenthesis indicates a typical fraction of \[C II\] arising from photodissociation regions (PDRs; i.e., the remaining 30% originates from H II regions). For consistency with previous works (cite: 2012MNRAS.425L..66M; 2015A&A...574A..14C), we adopt $X_{\rm C^+} = 1.4 \times 10^{-4}$ and $T_{\rm ex} = 200$ K, which are characteristic to PDRs (cite: 1997ARA&A..35..179H), but varying $T_{\rm ex} \in [100, 1000]$ K changes the inferred $M_{\rm out}$ by only $\sim 20\%$.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  | $v_{\rm out}$ | $M_{\rm out}$ | $\tau_{\rm out}$ | $\dot{M}_{\rm out}$ | $\dot{E}_{\rm out}$ | $\dot{P}_{\rm out}/\dot{P}_{\rm AGN}$ |
| Blob ID | (km s$^{-1}$) | (10$^8$ $M_\odot$) | (10$^7$ yr) | ($M_\odot$ yr$^{-1}$) | (10$^8$ $L_\odot$) | (%) |
| A | 422 $\pm$ 82 | 3.8 $\pm$ 0.6 | 0.8 $\pm$ 0.2 | 45 $\pm$ 11 | 6.6 $\pm$ 2.4 | 4.3 $\pm$ 1.4 |
| B | 547 $\pm$ 95 | 2.4 $\pm$ 0.5 | 1.1 $\pm$ 0.2 | 21 $\pm$ 5 | 5.1 $\pm$ 1.8 | 2.6 $\pm$ 0.8 |
| C | 538 $\pm$ 106 | 2.9 $\pm$ 0.5 | 0.9 $\pm$ 0.2 | 31 $\pm$ 8 | 7.5 $\pm$ 2.9 | 3.9 $\pm$ 1.3 |

: Possible Galaxy-scale \[C II\] Outflow Properties of J1205$-$0000

Interestingly, the (projected) flow times of the blobs A–C are all clustered around $\sim 10^7$ yr, which suggests that these outflows were launched at roughly the same time. Summing over these three blobs, the total atomic outflow mass and outflow rate are $M_{\rm out,A-C} = 9.0 \pm 0.9) \times 10^8~M_\odot$ and $\dot{M}_{\rm out,A-C} = 97 \pm 15$ $M_\odot$ yr$^{-1}$, respectively. The summed outflow rate is $\sim 8\times$ greater than a (current) BH accretion rate of J1205$-$0000 ($\dot{M}_{\rm BH} \sim 12.5~M_\odot$ yr$^{-1}$), which is estimated from the quasar bolometric luminosity (cite: 2020PASJ..tmp..230K) with a canonical radiative efficiency of $\varepsilon = 0.1$.

Note that, however, our (possible) outflow rate only refers to the neutral atomic component, while a significant fraction of the outflowing gas would be in a molecular phase. Indeed, (cite: 2019MNRAS.483.4586F) found in local galaxies that the total mass-flow rate is $\sim 0.5$ dex larger than the atom-only value. As our computation provided a lower limit on $M_{\rm out}$, and we measured rates only at the three selected positions, J1205$-$0000 is likely to have a (possible) total outflow rate of $\dot{M}_{\rm tot} \gtrsim 300~M_\odot$ yr$^{-1}$. This is factor $\gtrsim 3$ greater than the \[C II\]-based SFR, and it is not typical for star formation to drive a wind at a much greater rate than the SFR (cite: 2014A&A...562A..21C). We therefore naively suppose that the quasar itself powers this outflow. We emphasize that J1205$-$0000 is the highest redshift *red quasar* known to date. Therefore, it is intriguing that the existence of outflows on the scale of the host galaxy is hinted at here, suggesting that the surrounding interstellar medium is actively being blown out, as predicted in SMBH/galaxy evolution scenarios (cite: 2006ApJS..163....1H).

We found that the peak flux density of the red wing is $\sim 30\%$ of that of the core component, while (cite: 2012MNRAS.425L..66M) found a broad-to-narrow peak flux density ratio of $\sim 15\%$ for the case of J1148$+$5251. The (possible) outflow velocity is much smaller in J1205$-$0000 than J1148$+$5251, but we may be limited by the sensitivity of our measurement to detect faster components. Interestingly, a similar line profile to J1205$-$0000 is seen in cold outflows of lower redshift obscured quasars (cite: 2018A&A...612A..29B; 2018ApJ...856L...5F). Hence suppose for example that the high-peak wing is due to a dense gas that once obscured the nucleus in a shell-like form. It had a high wind velocity when it was launched, but is now decelerated after traveling a long way from the center. As time progresses and the quasar becomes less reddened, the outflow will continue to slow down. It would be hard to identify such a low-velocity component as an outflow unless it is spatially resolved. Indeed, spatially extended but low-velocity ($|\Delta v| < 200$ km s$^{-1}$) structures are also found in J1148$+$5251 (cite: 2015A&A...574A..14C).

If the extended structures were formed genuinely due to outflows, both the outflow kinetic power $$\begin{equation}
\dot{E}_{\rm out} = \frac{1}{2} \dot{M}_{\rm out} v^2_{\rm out}
\end{equation}$$ and the momentum load $$\begin{equation}
\dot{P}_{\rm out}/\dot{P}_{\rm AGN} = \frac{\dot{M}_{\rm out} \times v_{\rm out}}{L_{\rm AGN}/c}
\end{equation}$$ are significantly smaller (Table [2](#tbl2)) than what energy-conserving AGN feedback models typically predict (cite: 2015ARA&A..53..115K). The small values found here are comparable to those of J1148$+$5251 (cite: 2015A&A...574A..14C), implying that these may be typical among both red and blue $z \gtrsim 6$ quasars. Hence, the nuclear winds contribute only a small fraction of the galaxy-scale feedback if we apply this energy-conserving feedback scenario. This indicates that, without additional feedback from star formation, the AGN feedback is not able to completely suppress star formation over the entire host galaxy.

# Summary

We have presented ALMA observations of \[C II\] line and underlying FIR continuum emission of the highest redshift red quasar known to date, J1205$-$0000 at $z = 6.72$, which was discovered in our deep optical imaging survey with the Subaru Hyper Suprime-Cam (HSC). Although it appears as a low-luminosity quasar ($M_{\rm 1450} = -24.4$ mag), its intrinsic luminosity is as high as $M_{\rm 1450} = -26.1$ mag once its dust extinction is corrected. A red quasar population has been considered as an emergent phase from a dusty starburst by blowing out its surrounding dense obscuring medium. The main findings of this paper are summarized as follows.

- We successfully detected the \[C II\] line and FIR continuum emission. The \[C II\] emission is spatially more extended (over $r \sim 5$ kpc scale) than the continuum emission. The area-integrated \[C II\] line profile is complex and is characterized by two components, i.e., a main core component that is attributed to the host galaxy itself and an additional red wing component. Summing up these two, we found the line luminosity of $L_{\rm [CII]} = (1.9 \pm 0.1) \times 10^9~L_\odot$. The FIR continuum emission is also bright as $L_{\rm FIR} = (2.7 \pm 0.1) \times 10^{12}~L_\odot$ ($T_d = 47$ K, $\beta = 1.6$).

- The SFR inferred from the continuum luminosity and \[C II\] core luminosity is $575 \pm 21~M_\odot$ yr$^{-1}$ and $108 \pm 7~M_\odot$ yr$^{-1}$, respectively. Note that, however, these would be regarded as upper limits as we neglect a contamination from this intrinsically luminous quasar itself.

- Based on the \[C II\] equivalent width and $L_{\rm Bol}$–$L_{\rm FIR}$ relation, we found that J1205$-$0000 shows consistent properties to $z \gtrsim 6$ optically luminous quasars once its dust extinction is corrected. We also found a marginal positive correlation between $L_{\rm Bol}$ and $L_{\rm FIR}$, implying a black hole and its host galaxy are co-evolving.

- Although it is not practical to identify the physical origin of the spatially extended \[C II\] emission with the current dataset, possible explanations include (i) companion/merging galaxies and (ii) cold outflows. Both of these appear fascinating as they well fit into the merger-induced galaxy evolution scenario.

- If the extended structure is due to (multiple) companion/merging galaxies, this indicates that this red quasar indeed emerges with a merger event. While no counterpart was identified in our optical imaging survey with Subaru/HSC (e.g., $y$-band 5$\sigma$ limiting magnitude = 24.4 mag), dust extinction would not be the prime cause of this given the non-detection of FIR continuum emission. Rather, we may still not be sensitive enough to detect *normal* galaxies like LBGs at that high redshift. Deeper imaging observations by future facilities like JWST are necessary to search for the possible companion/merging galaxies.

- If the extended structure is due to cold outflows, we can argue that this red quasar is in a key transition phase from a dusty starburst by blowing our its surrounding medium. On the other hand, our lower-limit on the cold neutral outflow is only $\sim 100~M_\odot$ yr$^{-1}$, and we found that the outflow kinetic energy and momentum are both much smaller than what predicted in energy-conserving wind models. This suggests that the AGN feedback in this quasar, if genuinely exists, is not sufficient to suppress star-formation of the host galaxy.

In this work, we revealed some intriguing host galaxy properties of this red quasar. This red quasar was originally identified by matching our low-luminosity quasar sample and the mid-IR photometric data obtained by WISE (cite: 2020PASJ..tmp..230K). As the HSC survey has still been on-going and our sample of $z = 6-7$ low-luminosity quasars has been growing, we would be able to find other red quasars at this high redshift. They should be a good sample for extensive follow-up studies by, e.g., ALMA and JWST, to better understand the early black hole growth and co-evolution.

# Acknowledgments

We appreciate the anonymous referee’s thorough reading and very constructive comments that improved this paper greatly. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00074.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

The Hyper Suprime-Cam (HSC) collaboration includes the astronomical communities of Japan and Taiwan, and Princeton University. The HSC instrumentation and software were developed by the National Astronomical Observatory of Japan (NAOJ), the Kavli Institute for the Physics and Mathematics of the Universe (Kavli IPMU), the University of Tokyo, the High Energy Accelerator Research Organization (KEK), the Academia Sinica Institute for Astronomy and Astrophysics in Taiwan (ASIAA), and Princeton University. Funding was contributed by the FIRST program from the Japanese Cabinet Office, the Ministry of Education, Culture, Sports, Science and Technology (MEXT), the Japan Society for the Promotion of Science (JSPS), the Japan Science and Technology Agency (JST), the Toray Science Foundation, NAOJ, Kavli IPMU, KEK, ASIAA, and Princeton University.

T.I. is supported by the ALMA Japan Research Grant of the NAOJ ALMA Project, NAOJ-ALMA-249.

# Software

CASA (cite: 2007ASPC..376..127M), MIRIAD (cite: 1995ASPC...77..433S), astropy (cite: astropy:2013; astropy:2018).

natexlab

(ref: 2018PASJ...70S...4A) Aihara, H., Arimoto, N., Armstrong, R., et al. 2018, PASJ, 70, S4, doi: [`10.1093/pasj/psx066`](http://doi.org/10.1093/pasj/psx066)

(ref: 2004A&A...425..109A) Alton, P. B., Xilouris, E. M., Misiriotis, A., Dasyra, K. M., & Dumke, M. 2004, A&A, 425, 109, doi: [`10.1051/0004-6361:20040438`](http://doi.org/10.1051/0004-6361:20040438)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., SipHocz, B. M., et al. 2018, aj, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2016ApJS..227...11B) Bañados, E., Venemans, B. P., Decarli, R., et al. 2016, ApJS, 227, 11, doi: [`10.3847/0067-0049/227/1/11`](http://doi.org/10.3847/0067-0049/227/1/11)

(ref: 2019ApJ...881L..23B) Bañados, E., Novak, M., Neeleman, M., et al. 2019, ApJL, 881, L23, doi: [`10.3847/2041-8213/ab3659`](http://doi.org/10.3847/2041-8213/ab3659)

(ref: 2006ApJ...642..694B) Beelen, A., Cox, P., Benford, D. J., et al. 2006, ApJ, 642, 694, doi: [`10.1086/500636`](http://doi.org/10.1086/500636)

(ref: 2016A&A...587A..72B) Bergvall, N., Marquart, T., Way, M. J., et al. 2016, A&A, 587, A72, doi: [`10.1051/0004-6361/201525692`](http://doi.org/10.1051/0004-6361/201525692)

(ref: 2019A&A...630A..59B) Bischetti, M., Maiolino, R., Carniani, S., et al. 2019, A&A, 630, A59, doi: [`10.1051/0004-6361/201833557`](http://doi.org/10.1051/0004-6361/201833557)

(ref: 2018A&A...612A..29B) Brusa, M., Cresci, G., Daddi, E., et al. 2018, A&A, 612, A29, doi: [`10.1051/0004-6361/201731641`](http://doi.org/10.1051/0004-6361/201731641)

(ref: 2016A&A...591A..28C) Carniani, S., Marconi, A., Maiolino, R., et al. 2016, A&A, 591, A28, doi: [`10.1051/0004-6361/201528037`](http://doi.org/10.1051/0004-6361/201528037)

(ref: 2014A&A...562A..21C) Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21, doi: [`10.1051/0004-6361/201322464`](http://doi.org/10.1051/0004-6361/201322464)

(ref: 2015A&A...574A..14C) Cicone, C., Maiolino, R., Gallerani, S., et al. 2015, A&A, 574, A14, doi: [`10.1051/0004-6361/201424980`](http://doi.org/10.1051/0004-6361/201424980)

(ref: 2013ApJ...766...13D) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13, doi: [`10.1088/0004-637X/766/1/13`](http://doi.org/10.1088/0004-637X/766/1/13)

(ref: 2007ApJ...671.1388D) Davies, R. I., Müller Sánchez, F., Genzel, R., et al. 2007, ApJ, 671, 1388, doi: [`10.1086/523032`](http://doi.org/10.1086/523032)

(ref: 2011MNRAS.416.2712D) De Looze, I., Baes, M., Bendo, G. J., Cortese, L., & Fritz, J. 2011, MNRAS, 416, 2712, doi: [`10.1111/j.1365-2966.2011.19223.x`](http://doi.org/10.1111/j.1365-2966.2011.19223.x)

(ref: 2017Natur.545..457D) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457, doi: [`10.1038/nature22358`](http://doi.org/10.1038/nature22358)

(ref: 2018ApJ...854...97D) —. 2018, ApJ, 854, 97, doi: [`10.3847/1538-4357/aaa5aa`](http://doi.org/10.3847/1538-4357/aaa5aa)

(ref: 2019ApJ...880..157D) Decarli, R., Dotti, M., Bañados, E., et al. 2019, ApJ, 880, 157, doi: [`10.3847/1538-4357/ab297f`](http://doi.org/10.3847/1538-4357/ab297f)

(ref: 2005Natur.433..604D) Di Matteo, T., Springel, V., & Hernquist, L. 2005, Nature, 433, 604, doi: [`10.1038/nature03335`](http://doi.org/10.1038/nature03335)

(ref: 2013ApJ...774...68D) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2013, ApJ, 774, 68, doi: [`10.1088/0004-637X/774/1/68`](http://doi.org/10.1088/0004-637X/774/1/68)

(ref: 2011MNRAS.418.2043E) Ellison, S. L., Patton, D. R., Mendel, J. T., & Scudder, J. M. 2011, MNRAS, 418, 2043, doi: [`10.1111/j.1365-2966.2011.19624.x`](http://doi.org/10.1111/j.1365-2966.2011.19624.x)

(ref: 2020ApJ...898..171E) Estrada-Carpenter, V., Papovich, C., Momcheva, I., et al. 2020, ApJ, 898, 171, doi: [`10.3847/1538-4357/aba004`](http://doi.org/10.3847/1538-4357/aba004)

(ref: 2018ApJ...856L...5F) Fan, L., Knudsen, K. K., Fogasy, J., & Drouart, G. 2018, ApJL, 856, L5, doi: [`10.3847/2041-8213/aab496`](http://doi.org/10.3847/2041-8213/aab496)

(ref: 2001AJ....122.2833F) Fan, X., Narayanan, V. K., Lupton, R. H., et al. 2001, AJ, 122, 2833, doi: [`10.1086/324111`](http://doi.org/10.1086/324111)

(ref: 2012ApJ...745..178F) Farrah, D., Urrutia, T., Lacy, M., et al. 2012, ApJ, 745, 178, doi: [`10.1088/0004-637X/745/2/178`](http://doi.org/10.1088/0004-637X/745/2/178)

(ref: 2019MNRAS.483.4586F) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586, doi: [`10.1093/mnras/sty3449`](http://doi.org/10.1093/mnras/sty3449)

(ref: 2004ApJ...607...60G) Glikman, E., Gregg, M. D., Lacy, M., et al. 2004, ApJ, 607, 60, doi: [`10.1086/383305`](http://doi.org/10.1086/383305)

(ref: 2015ApJ...806..218G) Glikman, E., Simmons, B., Mailly, M., et al. 2015, ApJ, 806, 218, doi: [`10.1088/0004-637X/806/2/218`](http://doi.org/10.1088/0004-637X/806/2/218)

(ref: 2018ApJ...861...37G) Glikman, E., Lacy, M., LaMassa, S., et al. 2018, ApJ, 861, 37, doi: [`10.3847/1538-4357/aac5d8`](http://doi.org/10.3847/1538-4357/aac5d8)

(ref: 2018PASJ...70S..37G) Goulding, A. D., Greene, J. E., Bezanson, R., et al. 2018, PASJ, 70, S37, doi: [`10.1093/pasj/psx135`](http://doi.org/10.1093/pasj/psx135)

(ref: 2018ARA&A..56..625H) Hickox, R. C., & Alexander, D. M. 2018, ARA&A, 56, 625, doi: [`10.1146/annurev-astro-081817-051803`](http://doi.org/10.1146/annurev-astro-081817-051803)

(ref: 1997ARA&A..35..179H) Hollenbach, D. J., & Tielens, A. G. G. M. 1997, ARA&A, 35, 179, doi: [`10.1146/annurev.astro.35.1.179`](http://doi.org/10.1146/annurev.astro.35.1.179)

(ref: 2006ApJS..163....1H) Hopkins, P. F., Hernquist, L., Cox, T. J., et al. 2006, ApJS, 163, 1, doi: [`10.1086/499298`](http://doi.org/10.1086/499298)

(ref: 2008ApJS..175..356H) Hopkins, P. F., Hernquist, L., Cox, T. J., & Kereš, D. 2008, ApJS, 175, 356, doi: [`10.1086/524362`](http://doi.org/10.1086/524362)

(ref: 2019arXiv191105791I) Inayoshi, K., Visbal, E., & Haiman, Z. 2019, arXiv e-prints, arXiv:1911.05791. [`https://arxiv.org/abs/1911.05791`](https://arxiv.org/abs/1911.05791)

(ref: 2018PASJ...70...36I) Izumi, T., Onoue, M., Shirakata, H., et al. 2018, PASJ, 70, 36, doi: [`10.1093/pasj/psy026`](http://doi.org/10.1093/pasj/psy026)

(ref: 2019PASJ...71..111I) Izumi, T., Onoue, M., Matsuoka, Y., et al. 2019, PASJ, 71, 111, doi: [`10.1093/pasj/psz096`](http://doi.org/10.1093/pasj/psz096)

(ref: 2015ApJ...798...28K) Kashikawa, N., Ishizaki, Y., Willott, C. J., et al. 2015, ApJ, 798, 28, doi: [`10.1088/0004-637X/798/1/28`](http://doi.org/10.1088/0004-637X/798/1/28)

(ref: 2020PASJ..tmp..230K) Kato, N., Matsuoka, Y., Onoue, M., et al. 2020, PASJ, doi: [`10.1093/pasj/psaa074`](http://doi.org/10.1093/pasj/psaa074)

(ref: 2015ARA&A..53..115K) King, A., & Pounds, K. 2015, ARA&A, 53, 115, doi: [`10.1146/annurev-astro-082214-122316`](http://doi.org/10.1146/annurev-astro-082214-122316)

(ref: 2013ARA&A..51..511K) Kormendy, J., & Ho, L. C. 2013, ARA&A, 51, 511, doi: [`10.1146/annurev-astro-082708-101811`](http://doi.org/10.1146/annurev-astro-082708-101811)

(ref: 2018Natur.563..214K) Koss, M. J., Blecha, L., Bernhard, P., et al. 2018, Nature, 563, 214, doi: [`10.1038/s41586-018-0652-7`](http://doi.org/10.1038/s41586-018-0652-7)

(ref: 2020A&A...633A.134L) Lutz, D., Sturm, E., Janssen, A., et al. 2020, A&A, 633, A134, doi: [`10.1051/0004-6361/201936803`](http://doi.org/10.1051/0004-6361/201936803)

(ref: 2012MNRAS.425L..66M) Maiolino, R., Gallerani, S., Neri, R., et al. 2012, MNRAS, 425, L66, doi: [`10.1111/j.1745-3933.2012.01303.x`](http://doi.org/10.1111/j.1745-3933.2012.01303.x)

(ref: 2020MNRAS.494.2747M) Marshall, M. A., Mutch, S. J., Qin, Y., Poole, G. B., & Wyithe, J. S. B. 2020, MNRAS, 494, 2747, doi: [`10.1093/mnras/staa936`](http://doi.org/10.1093/mnras/staa936)

(ref: 2016ApJ...828...26M) Matsuoka, Y., Onoue, M., Kashikawa, N., et al. 2016, ApJ, 828, 26, doi: [`10.3847/0004-637X/828/1/26`](http://doi.org/10.3847/0004-637X/828/1/26)

(ref: 2018PASJ...70S..35M) —. 2018a, PASJ, 70, S35, doi: [`10.1093/pasj/psx046`](http://doi.org/10.1093/pasj/psx046)

(ref: 2018ApJS..237....5M) Matsuoka, Y., Iwasawa, K., Onoue, M., et al. 2018b, ApJS, 237, 5, doi: [`10.3847/1538-4365/aac724`](http://doi.org/10.3847/1538-4365/aac724)

(ref: 2017ApJ...849...91M) Mazzucchelli, C., Bañados, E., Venemans, B. P., et al. 2017, ApJ, 849, 91, doi: [`10.3847/1538-4357/aa9185`](http://doi.org/10.3847/1538-4357/aa9185)

(ref: 2019ApJ...881..163M) Mazzucchelli, C., Decarli, R., Farina, E. P., et al. 2019, ApJ, 881, 163, doi: [`10.3847/1538-4357/ab2f75`](http://doi.org/10.3847/1538-4357/ab2f75)

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2011ApJ...737...67M) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67, doi: [`10.1088/0004-637X/737/2/67`](http://doi.org/10.1088/0004-637X/737/2/67)

(ref: 2019ApJ...882...10N) Neeleman, M., Bañados, E., Walter, F., et al. 2019, ApJ, 882, 10, doi: [`10.3847/1538-4357/ab2ed3`](http://doi.org/10.3847/1538-4357/ab2ed3)

(ref: 2020arXiv201014875N) Novak, M., Venemans, B. P., Walter, F., et al. 2020, arXiv e-prints, arXiv:2010.14875. [`https://arxiv.org/abs/2010.14875`](https://arxiv.org/abs/2010.14875)

(ref: 2018PASJ...70S..10O) Ono, Y., Ouchi, M., Harikane, Y., et al. 2018, PASJ, 70, S10, doi: [`10.1093/pasj/psx103`](http://doi.org/10.1093/pasj/psx103)

(ref: 2019ApJ...880...77O) Onoue, M., Kashikawa, N., Matsuoka, Y., et al. 2019, ApJ, 880, 77, doi: [`10.3847/1538-4357/ab29e9`](http://doi.org/10.3847/1538-4357/ab29e9)

(ref: 2019MNRAS.488.4126P) Perrotta, S., Hamann, F., Zakamska, N. L., et al. 2019, MNRAS, 488, 4126, doi: [`10.1093/mnras/stz1993`](http://doi.org/10.1093/mnras/stz1993)

(ref: 2003AJ....126.1131R) Richards, G. T., Hall, P. B., Vand en Berk, D. E., et al. 2003, AJ, 126, 1131, doi: [`10.1086/377014`](http://doi.org/10.1086/377014)

(ref: 2006ApJS..166..470R) Richards, G. T., Lacy, M., Storrie-Lombardi, L. J., et al. 2006, ApJS, 166, 470, doi: [`10.1086/506525`](http://doi.org/10.1086/506525)

(ref: 2015MNRAS.453.3932R) Ross, N. P., Hamann, F., Zakamska, N. L., et al. 2015, MNRAS, 453, 3932, doi: [`10.1093/mnras/stv1710`](http://doi.org/10.1093/mnras/stv1710)

(ref: 1988ApJ...325...74S) Sanders, D. B., Soifer, B. T., Elias, J. H., et al. 1988, ApJ, 325, 74, doi: [`10.1086/165983`](http://doi.org/10.1086/165983)

(ref: 1995ASPC...77..433S) Sault, R. J., Teuben, P. J., & Wright, M. C. H. 1995, in Astronomical Society of the Pacific Conference Series, Vol. 77, Astronomical Data Analysis Software and Systems IV, ed. R. A. Shaw, H. E. Payne, & J. J. E. Hayes, 433. [`https://arxiv.org/abs/astro-ph/0612759`](https://arxiv.org/abs/astro-ph/0612759)

(ref: 2019MNRAS.482.4846S) Shirakata, H., Okamoto, T., Kawaguchi, T., et al. 2019, MNRAS, 482, 4846, doi: [`10.1093/mnras/sty2958`](http://doi.org/10.1093/mnras/sty2958)

(ref: 2011ApJ...743....2S) Silverman, J. D., Kampczyk, P., Jahnke, K., et al. 2011, ApJ, 743, 2, doi: [`10.1088/0004-637X/743/1/2`](http://doi.org/10.1088/0004-637X/743/1/2)

(ref: 2014ApJ...783L..14S) Straatman, C. M. S., Labbé, I., Spitler, L. R., et al. 2014, ApJL, 783, L14, doi: [`10.1088/2041-8205/783/1/L14`](http://doi.org/10.1088/2041-8205/783/1/L14)

(ref: 2017MNRAS.465.1401S) Symeonidis, M. 2017, MNRAS, 465, 1401, doi: [`10.1093/mnras/stw2784`](http://doi.org/10.1093/mnras/stw2784)

(ref: 2017ApJ...836....8T) Trakhtenbrot, B., Lira, P., Netzer, H., et al. 2017, ApJ, 836, 8, doi: [`10.3847/1538-4357/836/1/8`](http://doi.org/10.3847/1538-4357/836/1/8)

(ref: 2012ApJS..203....9U) U, V., Sanders, D. B., Mazzarella, J. M., et al. 2012, ApJS, 203, 9, doi: [`10.1088/0067-0049/203/1/9`](http://doi.org/10.1088/0067-0049/203/1/9)

(ref: 2009ApJ...698.1095U) Urrutia, T., Becker, R. H., White, R. L., et al. 2009, ApJ, 698, 1095, doi: [`10.1088/0004-637X/698/2/1095`](http://doi.org/10.1088/0004-637X/698/2/1095)

(ref: 2008ApJ...674...80U) Urrutia, T., Lacy, M., & Becker, R. H. 2008, ApJ, 674, 80, doi: [`10.1086/523959`](http://doi.org/10.1086/523959)

(ref: 2019ApJ...874L..30V) Venemans, B. P., Neeleman, M., Walter, F., et al. 2019, ApJL, 874, L30, doi: [`10.3847/2041-8213/ab11cc`](http://doi.org/10.3847/2041-8213/ab11cc)

(ref: 2016ApJ...816...37V) Venemans, B. P., Walter, F., Zschaechner, L., et al. 2016, ApJ, 816, 37, doi: [`10.3847/0004-637X/816/1/37`](http://doi.org/10.3847/0004-637X/816/1/37)

(ref: 2017ApJ...845..154V) Venemans, B. P., Walter, F., Decarli, R., et al. 2017, ApJ, 845, 154, doi: [`10.3847/1538-4357/aa81cb`](http://doi.org/10.3847/1538-4357/aa81cb)

(ref: 2018ApJ...866..159V) Venemans, B. P., Decarli, R., Walter, F., et al. 2018, ApJ, 866, 159, doi: [`10.3847/1538-4357/aadf35`](http://doi.org/10.3847/1538-4357/aadf35)

(ref: 2020ApJ...904..130V) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130, doi: [`10.3847/1538-4357/abc563`](http://doi.org/10.3847/1538-4357/abc563)

(ref: 2011ApJ...739L..34W) Wang, R., Wagg, J., Carilli, C. L., et al. 2011, ApJL, 739, L34, doi: [`10.1088/2041-8205/739/1/L34`](http://doi.org/10.1088/2041-8205/739/1/L34)

(ref: 2013ApJ...773...44W) —. 2013, ApJ, 773, 44, doi: [`10.1088/0004-637X/773/1/44`](http://doi.org/10.1088/0004-637X/773/1/44)

(ref: 2015ApJ...801..123W) Willott, C. J., Bergeron, J., & Omont, A. 2015, ApJ, 801, 123, doi: [`10.1088/0004-637X/801/2/123`](http://doi.org/10.1088/0004-637X/801/2/123)

(ref: 2017ApJ...850..108W) —. 2017, ApJ, 850, 108, doi: [`10.3847/1538-4357/aa921b`](http://doi.org/10.3847/1538-4357/aa921b)

(ref: 2013ApJ...770...13W) Willott, C. J., Omont, A., & Bergeron, J. 2013, ApJ, 770, 13, doi: [`10.1088/0004-637X/770/1/13`](http://doi.org/10.1088/0004-637X/770/1/13)

(ref: 2019MNRAS.489..497Z) Zakamska, N. L., Sun, A.-L., Strauss, M. A., et al. 2019, MNRAS, 489, 497, doi: [`10.1093/mnras/stz2071`](http://doi.org/10.1093/mnras/stz2071)

[^1]: (cite: 2017ApJ...849...91M) performed submm observations toward this quasar by using NOEMA interferometer, but did not detect \[C II\] emission as the line was out of their frequency coverage.

[^2]: Although the distribution is complex, we fit a 2-dimensional elliptical Gaussian to it (CASA task imfit; Table [1](#tbl1)). The estimated beam-deconvolved size is $\sim 7.7 \times 4.1$ kpc$^2$, which is much larger than that of the FIR continuum.

</paper>

Write the methods card for this paper.