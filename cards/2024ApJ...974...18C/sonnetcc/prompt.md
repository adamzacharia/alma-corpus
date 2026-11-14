# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...974...18C\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...974...18C",
 "title": "The Peculiar Radio Evolution of the Tidal Disruption Event ASASSN-19bt",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Christy, Collin T.",
 "n_authors": 18,
 "arxiv_id": "2404.12431",
 "doi": "10.3847/1538-4357/ad675b",
 "alma_projects_linked_by_archive": [
  "2018.1.01766.T"
 ]
}
```

Paper text:
<paper>
# The Peculiar Radio Evolution of the Tidal Disruption Event ASASSN-19bt

## Abstract

We present detailed radio observations of the tidal disruption event (TDE) ASASSN-19bt/AT2019ahk, obtained with the Australia Telescope Compact Array (ATCA), the Atacama Large Millimeter/submillimeter Array (ALMA), and the MeerKAT radio telescopes, spanning 40 to 1464 days after the onset of the optical flare. We find that ASASSN-19bt displays unusual radio evolution compared to other TDEs, as the peak brightness of its radio emission increases rapidly until 457 days post-optical discovery and then plateaus. Using a generalized approach to standard equipartition techniques, we estimate the energy and corresponding physical parameters for two possible emission geometries: a non-relativistic spherical outflow and a relativistic outflow observed from an arbitrary viewing angle. We find that the non-relativistic solution implies a continuous energy rise in the outflow from $E\sim10^{46}$ erg to $E\sim10^{49}$ erg with $\beta \approx 0.05$, while the off-axis relativistic jet solution instead suggests $E\approx10^{52}$ erg with $\Gamma\sim10$ erg at late times in the maximally off-axis case. We find that neither model provides a holistic explanation for the origin and evolution of the radio emission, emphasizing the need for more complex models. ASASSN-19bt joins the population of TDEs that display unusual radio emission at late times. Conducting long-term radio observations of these TDEs, especially during the later phases, will be crucial for understanding how these types of radio emission in TDEs are produced.

# Introduction

Tidal disruption events (TDEs) arise as a natural consequence of having supermassive black holes (SMBHs) populate the centers of galaxies. These events occur when a star’s orbit passes within the tidal radius of a massive black hole; for solar-type stars, this occurs outside of the event horizon for black holes with masses $M_{\rm BH} \lesssim 10^8 M_{\odot}$ (cite: hills_1975). When a star passes close enough to be disrupted in a single flyby, roughly half of the debris escapes on hyperbolic orbits, while the remaining material circularizes to form an accretion disk around the black hole (cite: Rees1998). TDEs are important to study because they act as cosmic laboratories for accretion physics, outflow mechanisms, and jet formation. Radio observations in particular are used to characterize outflows in TDEs and other extragalactic transient phenomena (cite: alexander2020). Radio observations of transients provide key diagnostics such as calorimetry, outflow velocity, magnetic field strength, and the density of the immediate environments surrounding the transient (cite: 1998chevalier; Metzger_2012; Margalit_2021; matsumoto).

In recent years, many TDEs have undergone follow-up radio observations, revealing a wide range of outflow properties (see (cite: alexander2020) for a review). A few TDEs have been observed to launch luminous, on-axis relativistic jets (cite: Zauderer_2011; cenko_2012; Brown_2017; Andreoni_2022; AT2022cmc_pasham_2023; AT2022cmc_matsumoto_metzger2023; Yao_2024) showing long-lasting luminous radio emission after the initial disruption of the star. More commonly, TDEs may exhibit fainter radio emission consistent with a non-relativistic outflow from accretion-driven winds, the unbound debris expanding into the surrounding medium, and/or collision-induced outflows from the fallback stream (cite: Strubbe; Tchekhovskoy; alexander_2016; krolik_2016; bonnerot_2020; at2019dsg). However, the exact origin of the less luminous radio emission is not yet clear; any/multiple of these possibilities may be correct. It is also common for follow-up observations of TDEs to reveal no radio emission at all on timescales of days to years post-disruption, which implies the absence of an energetic outflow with emission pointing along our line of sight (cite: alexander2020; van_Velzen_2023).

Recently, as many as 40% of TDEs have been reported to show delayed ($\gtrsim 1$ yr) radio emission relative to their optical discovery, suggesting that previous radio monitoring campaigns were insufficiently sensitive or ended too early (cite: yvette_2023). An early example of such a case is the TDE ASASSN-15oi, which displayed no prompt radio emission, then a detection of a flare six months later, followed by a second and brighter flare years later (cite: horesh_15oi). Another notable example is the TDE AT2018hyz which showed rapidly rising radio emission after two years of non-detections (cite: AT2018hyz; Sfaradi_2024). In a few instances, delayed low luminosity radio emission in TDE candidates has been successfully modeled as off-axis jets (cite: perlman_2017; ARP_2018), but the overall prevalence of jets in TDEs remains an open question hampered by inconsistent radio follow up. Radio emission from a relativistic jet viewed off-axis may not be visible until months or years post-disruption when the jet decelerates, and in such cases careful multi-frequency modeling spanning several years may be required to discriminate between an off-axis jet and a delayed non-relativistic outflow (cite: matsumoto). Thus, dedicated long-term radio monitoring campaigns are necessary to fully characterize the origin(s) of radio emission in individual TDEs.

Adding to the existing set of TDE observations, we present $\sim$ 4 years of radio observations of the TDE ASASSN-19bt/AT2019ahk. ASASSN-19bt ($z = 0.0262$) was discovered by the All-Sky Automated Survey for SuperNovae (cite: Shappee; Kochanek_2017) on 2019 January 29 in the galaxy 2MASX J07001137-6602251 (cite: holoien_2019). This event marked the first TDE discovered in the Transiting Exoplanet Survey Satellite (cite: Ricker_2015) Continuous Viewing Zone, resulting in a high-cadence optical light curve. Upon this source’s classification as a TDE, we quickly began our radio monitoring, with our first observation occurring near the time of peak optical emission. In their discovery paper, (cite: holoien_2019) found that the optical/UV emission of ASASSN-19bt indicated a luminosity, temperature, radius, and spectroscopic evolution similar to those of previously-studied optical TDEs. However, its X-ray properties are unusual: its X-ray luminosity is among the lowest observed for any optically-selected TDE, and (cite: holoien_2019) report an X-ray photon index of $\Gamma = 1.47^{+0.3}_{-0.3}$ at the time of peak optical light and $\Gamma = 2.34^{+0.8}_{-0.6}$ after optical peak, both harder than those of many optically-selected TDEs (cite: guolo_23). Radio observations may illuminate the nature of this emission by constraining the disruption geometry and the characteristics of any resulting outflows.

In this work, we present the radio evolution of ASASSN-19bt and consider two possible models: an off-axis relativistic jet or a spherical non-relativistic outflow. We find that the emission cannot be fully described by either of these simple limiting cases. In §[2](#sec:obs), we outline our observations and data reduction methods. In §[3](#sec:modeling), we describe our modeling framework for the radio emission. In §[4](#sec:analysis), we infer the physical properties of the outflow and the circumnuclear density for both models.

In §[5](#sec:disc), we examine the characteristics of the outflow and discuss ASASSN-19bt in context of other TDEs. In §[6](#sec:conc) we summarize our findings and present our conclusions.

# Observations

We obtained radio, mm, and X-ray observations of ASASSN-19bt as described below. In addition, we also use archival X-ray and radio data and data first published in (cite: holoien_2019). We define $\delta t$ as the time between our observation and 2019 January 21.6, the date where the TESS light curve indicates that the transient began to brighten (cite: holoien_2019). We assume a distance of 115.2 Mpc for ASASSN-19bt.

|            |           |               |            |       |                          |
|:-----------|:----------|:-------------:|:----------:|:-----:|:------------------------:|
| Date       | Telescope |     Array     | $\delta t$ | $\nu$ |    $F_\nu$ ($\mu$Jy)     |
| (UTC)      |           | Configuration |   (days)   | (GHz) | $\pm$ statistical error  |
|            |           |               |            |       |  $\pm$ systematic error  |
| 2015-12-07 | ATCA      |     1.5A      |   -1142    |  2.1  |  464 $\pm$ 70 $\pm$ 23   |
| 2016-08-19 | ATCA      |      6C       |    -886    |  2.1  |  400 $\pm$ 86 $\pm$ 20   |
| 2019-03-03 | ALMA      |     C43-1     |     40     | 97.5  |   143 $\pm$ 21 $\pm$ 7   |
| 2019-03-12 | ATCA      |      6A       |     49     | 16.7  |  220 $\pm$ 13 $\pm$ 11   |
| 2019-03-12 | ATCA      |      6A       |     49     | 21.2  |  206 $\pm$ 23 $\pm$ 10   |
| 2019-03-24 | ALMA      |     C43-2     |     61     | 97.5  |   89 $\pm$ 16 $\pm$ 4    |
| 2019-04-11 | ATCA      |     750C      |     79     | 17.0  |  235 $\pm$ 25 $\pm$ 11   |
| 2019-04-11 | ATCA      |     750C      |     79     | 19.0  |  216 $\pm$ 28 $\pm$ 10   |
| 2019-04-13 | ALMA      |     C43-3     |     81     | 97.5  |   60 $\pm$ 14 $\pm$ 3    |
| 2019-04-19 | ATCA      |     750C      |     87     |  5.5  |  418 $\pm$ 32 $\pm$ 20   |
| 2019-04-19 | ATCA      |     750C      |     87     |  9.0  |  330 $\pm$ 25 $\pm$ 16   |
| 2019-05-15 | ATCA      |     1.5B      |    113     |  2.1  |  440 $\pm$ 60 $\pm$ 22   |
| 2019-06-03 | ATCA      |      6A       |    132     |  2.1  |  789 $\pm$ 91 $\pm$ 39   |
| 2019-06-03 | ATCA      |      6A       |    132     |  5.5  |  630 $\pm$ 43 $\pm$ 31   |
| 2019-06-03 | ATCA      |      6A       |    132     |  9.0  |  493 $\pm$ 40 $\pm$ 24   |
| 2019-06-03 | ATCA      |      6A       |    132     | 17.0  |  276 $\pm$ 32 $\pm$ 13   |
| 2019-06-03 | ATCA      |      6A       |    132     | 19.0  |  266 $\pm$ 37 $\pm$ 13   |
| 2019-06-20 | ALMA      |   C43-9/10    |    149     | 97.5  |          $<$31           |
| 2019-07-27 | ATCA      |     750C      |    186     |  2.1  | 1153 $\pm$ 125 $\pm$ 57  |
| 2019-07-27 | ATCA      |     750C      |    186     |  5.5  |  759 $\pm$ 35 $\pm$ 37   |
| 2019-07-27 | ATCA      |     750C      |    186     |  9.0  |  497 $\pm$ 25 $\pm$ 24   |
| 2019-07-27 | ATCA      |     750C      |    186     | 17.0  |  272 $\pm$ 34 $\pm$ 13   |
| 2019-07-27 | ATCA      |     750C      |    186     | 19.0  |   194 $\pm$ 25 $\pm$ 9   |
| 2020-04-23 | ATCA      |      6A       |    457     |  2.1  | 3589 $\pm$ 127 $\pm$ 179 |
| 2020-04-23 | ATCA      |      6A       |    457     |  5.0  | 5044 $\pm$ 91 $\pm$ 252  |
| 2020-04-23 | ATCA      |      6A       |    457     |  6.0  | 4833 $\pm$ 40 $\pm$ 241  |
| 2020-04-23 | ATCA      |      6A       |    457     |  8.5  | 3907 $\pm$ 38 $\pm$ 195  |
| 2020-04-23 | ATCA      |      6A       |    457     |  9.5  | 3453 $\pm$ 40 $\pm$ 172  |
| 2020-04-23 | ATCA      |      6A       |    457     | 17.0  | 1806 $\pm$ 115 $\pm$ 90  |
| 2020-04-23 | ATCA      |      6A       |    457     | 19.0  | 1494 $\pm$ 154 $\pm$ 74  |
| 2021-03-25 | ATCA      |      6D       |    793     |  5.0  | 3568 $\pm$ 154 $\pm$ 178 |
| 2021-03-25 | ATCA      |      6D       |    793     |  6.0  | 3078 $\pm$ 74 $\pm$ 153  |
| 2021-03-25 | ATCA      |      6D       |    793     |  8.5  |  1709 $\pm$ 83 $\pm$ 85  |
| 2021-03-25 | ATCA      |      6D       |    793     |  9.5  |  1265 $\pm$ 94 $\pm$ 63  |
| 2021-04-10 | ATCA      |      6D       |    809     |  2.1  | 5000 $\pm$ 250 $\pm$ 250 |
| 2021-04-19 | MeerKAT   |      \-       |    818     |  1.3  | 4400 $\pm$ 140 $\pm$ 220 |
| 2022-09-30 | ATCA      |      6D       |    1347    |  1.6  | 5503 $\pm$ 140 $\pm$ 275 |
| 2022-09-30 | ATCA      |      6D       |    1347    |  2.6  | 4015 $\pm$ 89 $\pm$ 200  |
| 2022-09-30 | ATCA      |      6D       |    1347    |  5.0  | 2418 $\pm$ 54 $\pm$ 120  |
| 2022-09-30 | ATCA      |      6D       |    1347    |  6.0  | 2087 $\pm$ 35 $\pm$ 104  |
| 2022-09-30 | ATCA      |      6D       |    1347    |  8.5  |  1414 $\pm$ 37 $\pm$ 70  |
| 2022-09-30 | ATCA      |      6D       |    1347    |  9.5  |  1299 $\pm$ 40 $\pm$ 64  |
| 2023-01-25 | MeerKAT   |      \-       |    1464    |  0.8  | 6764 $\pm$ 54 $\pm$ 338  |
| 2023-01-25 | MeerKAT   |      \-       |    1464    |  1.3  | 6145 $\pm$ 39 $\pm$ 307  |

## Radio/Millimeter

We collected radio observations of ASASSN-19bt using the Australia Telescope Compact Array (ATCA) in the 6A, 6D, 1.5B, 750C configurations with a frequency range 2-19 GHz under programs C3325 (PI: K. Alexander) and CX432 (Director’s Time, PI: Alexander). Additionally, we included data from 2019-03-12 under program C3148 (PI: S. van Velzen). The results of these observations can be found in Table [\[tab:radio_data\]](#tab:radio_data). To process the data, we applied standard data reduction techniques using the package *Miriad* (cite: Miriad). For calibration, we employed B1934-638 as the primary flux calibrator for all observations and frequencies. J0700-6610 served as the phase calibrator for all frequencies. For the 2.1 GHz observations, we centered the field on J0700-6610 rather than slewing back and forth to the target. Due to its proximity to the TDE, we employed the “peeling” technique to improve the data calibration (see e.g., (cite: peeling)). This is a procedure for applying direction dependent gains to a limited portion of an image to reduce the artifacts due to a nearby bright source.

The data were imaged using the *Miriad* tasks `mfclean,  restor`. In observations where the target was sufficiently bright, we split the data into 2 subbands of 1024 MHz for imaging. Flux densities and their associated uncertainties were determined by fitting a point source model (gaussian with the width of the point-spread-function) using the `imfit` command within *Miriad*.

We also obtained four Band 3 observations using the Atacama Large Millimeter/submillimeter Array (ALMA) with a mean frequency of 97.5 GHz under program 2018.1.01766.T (PI: K. Alexander). The data were calibrated with the ALMA data pipeline version Pipeline-CASA54-P1-B using J0519-4546 as the flux calibrator and J0700-6610 as the phase calibrator. We detected ASASSN-19bt in the first three observations, while the 2019 June 20 observation yielded an upper limit. We imaged the data using the Common Astronomy Software Applications (CASA; version 6.2.1.7) software package (cite: CASA_team), wherein we fit the flux densities and associated uncertainties by fitting an elliptical Gaussian fixed to the size of the synthesized beam using the CASA task `imfit`.

Finally, we obtained observations with MeerKAT at 0.82 GHz ($UHF-$ band) and 1.28 GHz ($L-$band) under program SCI-20210212-YC-01 (PI: Y. Cendes). For these observations we used J0408-6545 as the flux calibrator and J0906-6829 as the phase calibrator. We used the calibrated images obtained via the South African Radio Astronomy Observatory Science Data Processor (SDP) [^1]. For these observations, we fit the flux densities and associated uncertainties by fitting an elliptical Gaussian fixed to the size of the synthesized beam using the CASA task `imfit`.

We note that the uncertainties derived from our fitting procedure are statistical errors only. When modelling we include an additional uncertainty of 5% of the source flux density to account for the known absolute flux density scale calibration accuracy of ATCA, ALMA, and MeerKAT. We include both sets of errors in Table [\[tab:radio_data\]](#tab:radio_data).

![](img/ATCAplusALMA_lightcurve.pdf)

![](img/litTDE_lightcurves.pdf)

## Archival Radio Observations

The host galaxy of ASASSN-19bt was previously detected by ATCA serendipitously due to its proximity to J0700-6610. These observations were taken at 2.1 GHz in 2015 December and 2016 August under the programs C1473 (PI: S. Ryder) and C3101 (PI: A. Edge) respectively. We reduced and imaged these data using the same procedure outlined above for our ATCA observations. The resulting archival flux densities are shown in Table [\[tab:radio_data\]](#tab:radio_data). A pre-disruption radio detection implies that some of the radio emission we observe is due to background emission from the host galaxy and not associated with the TDE. If the host galaxy emission component is constant in time, then the archival radio observations and the non-detection from ALMA in 2019 require that the host spectral energy distribution (SED) at radio frequencies follows a power law $F_\nu\propto\nu^{-0.7}$ or steeper.

For our modeling, we follow the same procedure outlined in (cite: alexander_2016), and assume that the host component of the radio emission follows a single power law with $F_\nu\approx(439\ \rm{\mu Jy}) (\nu/2.1 \rm GHz)^{-1}$, where 439 $\rm{\mu Jy}$ is the weighted average of the two archival detections at 2.1 GHz.

We find that the archival detection is consistent with radio emission from ongoing star formation in the host galaxy. Extrapolating the quiescent component to 1.4 GHz, the observed radio luminosity requires the formation rate of stars more massive than 5 $M_\odot$ to be $\sim0.22$ $M_\odot \ \rm yr^{-1}$ (cite: Condon_2002). This is consistent with (cite: holoien_2019), who reported that an archival spectrum of 2MASX J07001137-6602251 was well fit by a star-formation rate (SFR) of $0.17^{+0.06}_{-0.01}$ $M_\odot \ \rm yr^{-1}$. We note that (cite: holoien_2019) did not include a possible AGN component when modelling the archival host galaxy spectrum, therefore the inferred SFR should only be considered an upper limit.

Alternately, the pre-disruption radio detection could imply the presence of a compact AGN. The non-detection from ALMA suggests that if prior to the TDE the host contained a compact AGN with the flat radio spectrum typically seen in such sources, then its radio emission at all wavelengths must have been quenched at the time of disruption, and 100% of the emission observed during our monitoring campaign originated from the TDE. A steep-spectrum AGN component is allowed by our data, but in this case the host emission would likely arise from a relic AGN jet at sufficiently large physical separation from the SMBH to be unaffected by the TDE. We thus conclude it is reasonable to assume that the host galaxy emission component is constant in time.

After subtracting the host component, we find that the resulting transient component exhibits the shape of a self-absorbed synchrotron spectrum in all epochs (see Figure [3](#fig:1)). The remainder of our analysis will focus on modelling and interpreting the transient component of the radio emission. For completeness, we also model the observed emission as a single component and present our results in Appendix [7](#appendix:sed); we note that these results do not alter the basic conclusions of our analysis.

| Instrument | Observation IDs | MJD | $\delta t$ | $L_X/10^{40}$ erg/s |
|:---|:---|:---|:--:|:--:|
| Swift-XRT | 38456001 | 54853.65 $^{+0.17}_{-0.03}$ | -3652 | 16.26$^{+12.44}_{-8.37}$ |
| Swift-XRT | 38456002 | 54874.51 $^{+0.13}_{-0.13}$ | -3631 | $<$30.49 |
| Swift-XRT | 41619001 | 55538.59 $^{+0.01}_{-0.01}$ | -2967 | $<$85.48 |
| Swift-XRT | 83377001 | 56830.70 $^{+0.01}_{-0.01}$ | -1675 | $<$262.6 |
| Swift-XRT | 83377002 | 58181.14 $^{+1.01}_{-0.01}$ | -324 | $<$80.28 |
| Swift-XRT | 11115001-11 | 58535.23 $^{+9.40}_{-20.55}$ | 30 | 4.62$^{+1.91}_{-1.58}$ |
| XMM-Newton${^*}$ | 0831791001 | 58543.2 | 38 | 4.48$^{+0.77}_{-0.78}$ |
| Swift-XRT | 11115012-14 | 58561.71 $^{+0.27}_{-0.27}$ | 56 | $<$9.45 |
| Swift-XRT | 11115015-22 | 58581.48 $^{+18.86}_{-9.50}$ | 76 | $<$6.07 |
| XMM-Newton${^*}$ | 0831791101 | 58589.0 | 84 | 1.24$^{+0.40}_{-0.38}$ |
| CXO-ACIS-S | 22182 | 58591.07 | 85 | 2.01$^{+0.98}_{-0.56}$ |
| Swift-XRT | 11115024-25 | 58618.17 $^{+3.30}_{-0.17}$ | 113 | $<$25.45 |
| CXO-ACIS-S | 22183 | 58643.59 | 138 | 3.18$^{+0.77}_{-1.11}$ |
| Swift-XRT | 11115026-27 | 58646.39 $^{+4.68}_{-1.37}$ | 141 | 6.47$^{+4.39}_{-3.13}$ |
| Swift-XRT | 11115028-33 | 58680.73 $^{+10.25}_{-15.18}$ | 175 | 4.51$^{+2.54}_{-1.92}$ |
| Swift-XRT | 11115034-40 | 58730.84 $^{+17.78}_{-12.43}$ | 225 | 4.9$^{+2.24}_{-1.79}$ |
| Swift-XRT | 11115041-45 | 58802.80 $^{+5.11}_{-23.69}$ | 297 | $<$12.12 |
| Swift-XRT | 11115046-49 | 58829.49 $^{+0.01}_{-7.57}$ | 324 | $<$16.17 |
| Swift-XRT | 11115050-54 | 58840.13 $^{+16.66}_{-0.00}$ | 335 | $<$10.6 |
| Swift-XRT | 11115055-56 | 58898.48 $^{+7.70}_{-0.07}$ | 393 | $<$26.76 |
| Swift-XRT | 11115057-63 | 58940.59 $^{+20.75}_{-18.61}$ | 435 | $<$7.48 |
| Swift-XRT | 11115064-65 | 58971.52 $^{+4.25}_{-0.00}$ | 466 | $<$17.11 |
| Swift-XRT | 11115066-67 | 59177.46 $^{+6.18}_{-0.00}$ | 672 | $<$54.95 |
| Swift-XRT | 11115069 | 59193.66 $^{+0.01}_{-0.00}$ | 688 | $<$76.33 |
| Swift-XRT | 11115072 | 59206.46 $^{+1.34}_{-0.00}$ | 701 | $<$35.08 |
| Swift-XRT | 11115073 | 59219.41 $^{+0.00}_{-0.00}$ | 714 | $<$696.02 |
| Swift-XRT | 11115075-78 | 59247.70 $^{+0.27}_{-14.01}$ | 742 | $<$27.09 |
| Swift-XRT | 96581001 | 59811.58 $^{+0.40}_{-0.40}$ | 1306 | $<$27.1 |
| Swift-XRT | 96581002 | 59831.46 $^{+0.53}_{-0.01}$ | 1326 | $<$37.73 |
| Swift-XRT | 11115079-80 | 60114.40 $^{+3.57}_{-0.01}$ | 1609 | $<$50.62 |

X-ray luminosity measurements are from grouped EPIC-PN, EPIC-MOS1, and EPIC-MOS2 data, exact values are obtained from (cite: holoien_2019)

## X-rays: Chandra X-ray Observatory

We obtained two epochs of deep X-ray observations of ASASSN-19bt with the Chandra X-ray Observatory (CXO) on 2019-04-17 and 2019-06-09 (Obs IDs 22182 and 22183, PI: K. Alexander, exposure time of 9.98 ks for each ObsID), which is $\delta t=$ 85 days and $\delta t=$ 138 days after the optical discovery of the TDE. The data were reduced with the `CIAO` software package (v4.15) applying standard ACIS data filtering. An X-ray source is blindly detected with `wavdetect` with high statistical confidence $>4\,\sigma$ (Gaussian equivalent) at coordinates consistent with the optical and radio location of the TDE in each of the two CXO observations. The net 0.5-8 keV count-rates are $(8.7\pm3.0)\times 10^{-4}\,\rm{c\,s^{-1}}$ and $(10.8\pm3.3)\times 10^{-4}\,\rm{c\,s^{-1}}$, respectively. We find no statistical evidence for temporal variability of the source in the CXO dataset.

For each observation, we extracted a spectrum with `specextract` using a $1.5\ensuremath{''}$ source region and a source-free background region. Due to the low-number statistics, we cannot statistically constrain the spectral shape and both thermal and non-thermal models are statistically acceptable. Adopting an absorbed simple power-law model (`tbabs*ztbabs*pow` within `Xspec`), we find best-fitting photon index values in the range $\Gamma=1.6-1.7$ and no evidence for intrinsic absorption. The Galactic neutral hydrogen column density in the direction of ASASSN-19bt is $N_{H,MW}=7.1\times 10^{20}\,\rm{cm^{-2}}$ (cite: Kalberla05). We find no statistical evidence for spectral evolution. A joint fit of the two CXO epochs leads to the following best fitting parameters: $\Gamma= 1.64^{+0.57}_{-0.50}$, $N_{H,int}< 3.7\times 10^{22}\,\rm{cm^{-2}}$, where the uncertainties are provided at the $1\,\sigma$ (Gaussian equivalent) confidence level (c.l.) and the upper limit at the $3\,\sigma$ c.l.. These spectral parameters are consistent with those constrained from XMM observations in (cite: holoien_2019). The unabsorbed 0.3–10 keV fluxes and luminosities for all X-ray observations used in this work are reported in Table [\[tab:xray\]](#tab:xray).

## X-rays: Swift-XRT

ASASSN-19bt was monitored with the X-ray Telescope (cite: Burrows05) onboard the Neil Gehrels Swift Observatory (cite: Gehrels04), between 2019-01-31 and 2023-08-15 ($\delta t= 9-1666$ days). We analyzed all available *Swift*-XRT data using HEASoft v.6.32.1 and corresponding calibration files. We extracted a 0.3-10 keV count-rate light-curve using the online automated tools released by the Swift-XRT team (cite: Evans09) [^2] and custom scripts (cite: Margutti13). A targeted search for X-ray emission from the TDE leads to the detection of a weak but persistent X-ray source with approximately constant count-rate at $\delta t<250$ days. For the count-to-flux calibration we adopt the best-fitting spectral parameters derived from the joint fit of the two CXO epochs of §[2.3](#subsec:ChandraDataAnalysis), which leads to flux levels comparable to the CXO and XMM inferences. No X-ray source is detected by *Swift*-XRT observations acquired at $\delta t>250$ days. However, these late-time flux limits are not deep enough to constrain the fading of the source. A persistent X-ray source with $L_x\sim$ a few $10^{40}\,\rm{erg\,s^{-1}}$ cannot be ruled out, which makes the X-rays from ASASSN-19bt among the least luminous ever detected from an optically-selected TDE (Fig. [2](#fig:lit_lc)).

We note that analyzing data serendipitously acquired by *Swift*-XRT years before the TDE in the same way leads to the potential identification of a source of X-ray emission in 2009, as previously reported by (cite: holoien_2019). The source is not blindly detected, but has a targeted detection significance of $3\,\sigma$. If real and attributed to star formation in the host galaxy, the source flux would require a star formation rate of $8.9 ^{+15.2}_{-6.4}$ $M_{\odot}$ yr$^{-1}$ (cite: Riccio_2023), which is higher than the rates inferred from the archival spectra and radio detections (§[2.2](#sec:archival_radio)). Therefore, this marginal detection may indicate prior activity of the central SMBH. We further discuss the X-ray emission from ASASSN-19bt in §[5.5](#sec:xray_disc).

![](img/transient_seds.jpg)

# Synchrotron Emission Modeling

We model the radio SEDs as synchrotron emission generated from outflowing material expanding into an external medium. During this process, the blast wave generated by the outflow accelerates the electrons to a power-law distribution of energies, $N(\gamma) \propto \gamma^{-p}$ for $\gamma \geq \gamma_{m,0}$, immediately behind the shock; here, $\gamma$ is the electron Lorentz factor, $\gamma_{m,0}$ is the minimum Lorentz factor of the shocked electrons, and $p$ is the power law index of the energy distribution. The shape of the synchrotron spectrum is in general a multiple broken power-law, described by its break frequencies and an overall normalization factor (e.g., (cite: Granot_2002)).

For ASASSN-19bt, we assume that the spectral break frequencies follow $\nu_m < \nu_a < \nu_c$, where $\nu_m$ is the typical synchrotron frequency of the minimal electron energy in the power law, $\nu_a$ is the synchrotron self-absorption frequency, and $\nu_c$ is the synchrotron cooling frequency. For the energies and high density environments typical of most TDEs, we expect the SED peak to be located at the synchrotron self-absorption frequency and the other break frequencies to be located outside of the ATCA frequency range (cite: alexander_2016; at2019dsg; AT2019azh). We therefore initially fit our data with a singly broken power law, where the peak frequency is the self-absorption frequency $\nu_a$ with $F_\nu \propto \nu^{5/2}$ below the peak, and $F_\nu \propto \nu^{(1-p)/2}$ above the peak. While the peak frequency is typically associated with $\nu_a$ for non-relativistic sources, the peak is often located at $\nu_m$ for relativistic sources at early times (cite: Eftekhari; Andreoni_2022). We note that instead considering the peak as $\nu_m$ in our relativistic SED modeling (§[4.2](#sec:jet)) wouldn’t change the inferred physical parameters significantly.

We group our radio observations into 7 epochs, subtract our model for the quiescent host emission (§[2.2](#sec:archival_radio)), and fit the remaining transient component of each SED with our synchrotron model (see Appendix [7](#appendix:sed) for fits to the total flux densities). Although we use the analytic SED shape from the (cite: Granot_2002) model for synchrotron emission from gamma-ray burst (GRB) afterglows for the regime where $\nu_m \ll \nu_a$, we note that we fit each SED independently, without requiring any specific dynamic evolution of the emission. The model SED is expressed as:

$$\begin{equation}
    \centering
    F_\nu = F_{\nu,\rm ext}  \left[ \left( \frac{\nu}{\nu_b} \right)^{-s \beta_1}+ \left( \frac{\nu}{\nu_b} \right)^{-s\beta_2} \right]^{-1/s}
    \label{eq:1}
\end{equation}$$ where $\beta_1 = {5/2}$ and $\beta_2 = {(1-p)/2}$ are the spectral slopes below and above the break, $s=1.25 - 0.18p$ describes the sharpness of the peak, and $\nu_b = \nu_a$ is the self-absorption frequency. We use the (cite: Granot_2002) analytical expression for $s$ appropriate for an ambient density profile described by $\rho\propto r^{-2}$. This scenario most closely approximates the expected circumnuclear density profile around TDE SMBHs (cite: alexander2020).

We employed the Markov Chain Monte Carlo (MCMC) module `emcee` (cite: emcee) in Python to determine the optimal model parameters, assuming a Gaussian likelihood for all the parameters. We adopt uniform priors on the model parameters $p$, $F_{\nu,\rm ext}$, and $\nu_a$, where $p \in [2,4]$, log($F_{\nu,\rm ext}/ \rm{mJy}$) $\in [-4,2]$, and log($\nu_a/\rm{Hz}$) $\in [6,11]$. In the initial modeling stage, we fit for $F_{\nu,\rm ext}$, $\nu_a$, and $p$ in each epoch. Our analysis revealed no significant indication of time-dependent variations in the value of $p$. Therefore, we adopted a weighted average of $p = 2.80 \pm 0.02$ for the transient component ($p =  2.75 \pm 0.02$ for the total flux density fits). In our subsequent analysis, we set $p$ to be constant at these values and only fit for $F_{\nu,\rm ext}$ and $\nu_a$. We sampled the posterior distributions for $F_{\nu,\rm ext}$ and $\nu_a$ with 100 MCMC chains using the sampler EnsembleSampler from `emcee`. To ensure the convergence of the samples, we ran each chain for 2,000 steps and discarded the initial 1,000 steps. We report the best fit transient SED parameters in Table [1](#tab:2) and Figure [3](#fig:1) shows the resulting transient SED fits (for fits to the total flux density, see Figure [10](#fig:1_orig) in Appendix [7](#appendix:sed)).

![](img/SED_cooling.pdf)

|  |  |  |  |
|:---|:--:|:--:|:--:|
| Date | $\langle \delta t \rangle$ | $\nu_p$ | $F_p$ |
| (UTC) | (days) | (GHz) | (mJy) |
| 2019 Mar 12 | 49 | 28.56 $\pm$ 3.34 | 0.20 $\pm$ 0.02 |
| 2019 Apr 11/13/19 | 88 | 7.79 $\pm$ 1.22 | 0.25 $\pm$ 0.02 |
| 2019 Jun 3 | 132 | 4.27 $\pm$ 0.64 | 0.53 $\pm$ 0.06 |
| 2019 Sep 27 | 186 | 2.53 $\pm$ 0.41 | 0.79 $\pm$ 0.11 |
| 2020 Apr 23 | 457 | 4.03 $\pm$ 0.12 | 4.96 $\pm$ 0.14 |
| 2021 Mar 25/Apr 10/19 | 800 | 1.95 $\pm$ 0.09 | 4.46 $\pm$ 0.15 |
| 2022 Sep 30/2023 Jan 25 | 1377 | 1.06 $\pm$ 0.05 | 5.78 $\pm$ 0.20 |

: Spectral energy distribution parameters from the synchrotron emission model. We fit only the transient component of the radio flux densities.

## Synchrotron Cooling

On 2019 June 20, we obtained an upper limit on the flux density at 97.5 GHz that is inconsistent with our single-break synchrotron SED model fit to the contemporaneous observations at $\lesssim20$ GHz. This discrepancy may be due to the presence of a synchrotron cooling break at a frequency of $\nu_c$, given by (cite: Sari_1998):

$$\begin{equation}
    \nu(\gamma_c) = \frac{q_e B}{2 \pi m_e c} \Gamma \gamma_c^2, 
    \label{eq:2}
\end{equation}$$ where $\gamma_c$ is the critical Lorentz factor required for synchrotron cooling, defined as $\gamma_c = 6\pi m_e c / \sigma_T B^2 \Gamma t$, $\Gamma$ is the bulk Lorentz factor of the shocked material, and $t$ refers to the time since the launch of the outflow in the frame of the observer. We conservatively assume that the radio outflow was launched at $\delta t=0$ days.[^3]

In Figure [4](#fig:3), we show the single break SED for the data from day 132, along with a model SED that describes the single break plus synchrotron cooling. The SED model including the cooling break is given by (cite: Granot_2002):

$$\begin{equation}
    \centering
    F_{\nu_c} = F_{\nu}  \left[1+\left( \frac{\nu}{\nu_c} \right)^{s(\beta_2-\beta_3)}\right]^{-1/s},
\end{equation}$$ where $F_\nu$ is the model described by equation ([\[eq:1\]](#eq:1)), $\beta_3 = {-p/2}$ is the spectral slope above the cooling break, and $s=10$ describes the smoothing [^4] describes the smoothing. Our best-fit synchrotron cooling model suggests that $\nu_c \approx 19 \ \rm GHz$. Due to the $B$ dependence of $\nu_c$, measuring the location of the cooling break leads to an estimate of $\epsilon_B$, the fraction of post-shock energy in magnetic fields. We outline our expressions for $B$ explicitly in §[4](#sec:analysis). The observed $\nu_c$ is consistent with $\epsilon_B \approx 0.2$ under the assumption that the outflow is spherical and non-relativistic. In the off-axis jet scenario, the implied magnetic field strength $B$ becomes a function of the observer viewing angle. We find $\epsilon_B$ ranges from $\sim 3 \times10^{-4}$ to $\sim 0.005$ depending on the viewing angle (for exact values see Table [2](#tab:eb) in Appendix [7](#appendix:sed)).

![](img/peak_flux_freq.pdf)

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Geometry | $\langle \delta t \rangle$ | log($R$) | log($E$) | log($E_\text{wide}$) | log($B$) | log($N_e$) | log($n_\text{ext}$) | $\beta$ |
|  | ($\text{days})$ | $(\text{cm})$ | $(\text{erg})$ | $(\text{erg})$ | $(\text{G})$ |  | ($\text{cm}^{-3})$ |  |
| Spherical | 49 | 15.30 $^{+ 0.05 }_{- 0.04 }$ | 46.40 $^{+ 0.05 }_{- 0.04 }$ | \- | 0.86 $^{+ 0.04 }_{- 0.05 }$ | 50.57 $^{+ 0.05 }_{- 0.04 }$ | 4.01 $^{+ 0.09 }_{- 0.09 }$ | 0.016 $^{+ 0.002 }_{- 0.001 }$ |
| $f_A=1$ | 88 | 15.91 $^{+ 0.09 }_{- 0.06 }$ | 47.08 $^{+ 0.12 }_{- 0.09 }$ | \- | 0.29 $^{+ 0.07 }_{- 0.07 }$ | 51.26 $^{+ 0.12 }_{- 0.09 }$ | 2.85 $^{+ 0.15 }_{- 0.13 }$ | 0.036 $^{+ 0.008 }_{- 0.005 }$ |
| $f_V=0.36$ | 132 | 16.32 $^{+ 0.08 }_{- 0.07 }$ | 47.72 $^{+ 0.11 }_{- 0.10 }$ | \- | -0.01 $^{+ 0.06 }_{- 0.06 }$ | 51.89 $^{+ 0.11 }_{- 0.10 }$ | 2.26 $^{+ 0.14 }_{- 0.11 }$ | 0.062 $^{+ 0.011 }_{- 0.010 }$ |
| $\epsilon_e = 0.1$ | 186 | 16.64 $^{+ 0.11 }_{- 0.08 }$ | 48.16 $^{+ 0.16 }_{- 0.11 }$ | \- | -0.26 $^{+ 0.07 }_{- 0.07 }$ | 52.34 $^{+ 0.16 }_{- 0.11 }$ | 1.77 $^{+ 0.15 }_{- 0.12 }$ | 0.090 $^{+ 0.023 }_{- 0.016 }$ |
| $\epsilon_B = 0.2$ | 457 | 16.81 $^{+ 0.02 }_{- 0.02 }$ | 48.92 $^{+ 0.02 }_{- 0.02 }$ | \- | -0.14 $^{+ 0.02 }_{- 0.01 }$ | 53.09 $^{+ 0.02 }_{- 0.02 }$ | 2.01 $^{+ 0.03 }_{- 0.03 }$ | 0.055 $^{+ 0.002 }_{- 0.002 }$ |
|  | 800 | 17.11 $^{+ 0.02 }_{- 0.03 }$ | 49.18 $^{+ 0.03 }_{- 0.03 }$ | \- | -0.45 $^{+ 0.02 }_{- 0.02 }$ | 53.35 $^{+ 0.03 }_{- 0.03 }$ | 1.38 $^{+ 0.05 }_{- 0.04 }$ | 0.062 $^{+ 0.003 }_{- 0.004 }$ |
|  | 1377 | 17.42 $^{+ 0.03 }_{- 0.02 }$ | 49.57 $^{+ 0.04 }_{- 0.03 }$ | \- | -0.73 $^{+ 0.02 }_{- 0.03 }$ | 53.75 $^{+ 0.04 }_{- 0.03 }$ | 0.83 $^{+ 0.04 }_{- 0.05 }$ | 0.074 $^{+ 0.006 }_{- 0.004 }$ |
| Geometry | $\langle \delta t \rangle$ | log($R$) | log($E$) | log($E_\text{wide}$) | log($B$) | log($N_e$) | log($n_{ext}$) | $\Gamma$ |
|  | ($\text{days})$ | $(\text{cm})$ | $(\text{erg})$ | $(\text{erg})$ | $(\text{G})$ |  | ($\text{cm}^{-3})$ |  |
| Jet | 49 | 17.28 $^{+ 0.01 }_{- 0.01 }$ | 50.48 $^{+ 0.07 }_{- 0.07 }$ | 52.21 $^{+ 0.11 }_{- 0.12 }$ | 0.54 $^{+ 0.05 }_{- 0.07 }$ | 52.83 $^{+ 0.05 }_{- 0.04 }$ | 3.31 $^{+ 0.09 }_{- 0.10 }$ | 51.2 $^{+ 3.3 }_{- 3.7 }$ |
| $\theta_\text{obs}$=1.05 | 88 | 17.54 $^{+ 0.01 }_{- 0.01 }$ | 50.35 $^{+ 0.09 }_{- 0.09 }$ | 51.56 $^{+ 0.22 }_{- 0.17 }$ | -0.17 $^{+ 0.10 }_{- 0.09 }$ | 52.86 $^{+ 0.05 }_{- 0.06 }$ | 2.05 $^{+ 0.18 }_{- 0.14 }$ | 28.3 $^{+ 3.4 }_{- 3.7 }$ |
| $f_A = 1$ | 132 | 17.71 $^{+ 0.01 }_{- 0.01 }$ | 50.46 $^{+ 0.07 }_{- 0.06 }$ | 51.31 $^{+ 0.22 }_{- 0.14 }$ | -0.56 $^{+ 0.10 }_{- 0.08 }$ | 53.04 $^{+ 0.03 }_{- 0.04 }$ | 1.35 $^{+ 0.18 }_{- 0.12 }$ | 19.0 $^{+ 2.7 }_{- 2.1 }$ |
| $f_V = 1$ | 186 | 17.86 $^{+ 0.01 }_{- 0.01 }$ | 50.54 $^{+ 0.08 }_{- 0.08 }$ | 51.15 $^{+ 0.23 }_{- 0.17 }$ | -0.86 $^{+ 0.10 }_{- 0.10 }$ | 53.17 $^{+ 0.04 }_{- 0.05 }$ | 0.80 $^{+ 0.19 }_{- 0.15 }$ | 14.4 $^{+ 2.2 }_{- 2.2 }$ |
| $\epsilon_e = 0.1$ | 457 | 18.25 $^{+ 0.01 }_{- 0.01 }$ | 51.78 $^{+ 0.02 }_{- 0.02 }$ | 52.72 $^{+ 0.05 }_{- 0.04 }$ | -0.66 $^{+ 0.02 }_{- 0.02 }$ | 54.24 $^{+ 0.01 }_{- 0.01 }$ | 1.02 $^{+ 0.04 }_{- 0.03 }$ | 20.8 $^{+ 0.6 }_{- 0.5 }$ |
| $\epsilon_B = 0.003$ | 800 | 18.50 $^{+ 0.01 }_{- 0.01 }$ | 51.93 $^{+ 0.02 }_{- 0.02 }$ | 52.79 $^{+ 0.07 }_{- 0.05 }$ | -0.99 $^{+ 0.03 }_{- 0.03 }$ | 54.41 $^{+ 0.01 }_{- 0.01 }$ | 0.39 $^{+ 0.06 }_{- 0.04 }$ | 19.0 $^{+ 0.9 }_{- 0.7 }$ |
|  | 1377 | 18.73 $^{+ 0.01 }_{- 0.01 }$ | 52.14 $^{+ 0.02 }_{- 0.03 }$ | 52.89 $^{+ 0.06 }_{- 0.07 }$ | -1.30 $^{+ 0.03 }_{- 0.04 }$ | 54.65 $^{+ 0.02 }_{- 0.02 }$ | -0.20 $^{+ 0.05 }_{- 0.06 }$ | 16.7 $^{+ 0.7 }_{- 0.9 }$ |
| Jet | 49 | 17.02 $^{+ 0.01 }_{- 0.01 }$ | 50.24 $^{+ 0.07 }_{- 0.07 }$ | 51.37 $^{+ 0.11 }_{- 0.12 }$ | 0.66 $^{+ 0.05 }_{- 0.07 }$ | 52.70 $^{+ 0.05 }_{- 0.04 }$ | 3.38 $^{+ 0.09 }_{- 0.10 }$ | 25.7 $^{+ 1.6 }_{- 1.9 }$ |
| $\theta_\text{obs}$=1.57 | 88 | 17.27 $^{+ 0.01 }_{- 0.01 }$ | 50.12 $^{+ 0.09 }_{- 0.09 }$ | 50.72 $^{+ 0.22 }_{- 0.17 }$ | -0.04 $^{+ 0.10 }_{- 0.09 }$ | 52.73 $^{+ 0.05 }_{- 0.06 }$ | 2.12 $^{+ 0.18 }_{- 0.14 }$ | 14.2 $^{+ 1.7 }_{- 1.8 }$ |
| $f_A = 1$ | 132 | 17.44 $^{+ 0.01 }_{- 0.01 }$ | 50.23 $^{+ 0.07 }_{- 0.06 }$ | 50.48 $^{+ 0.22 }_{- 0.14 }$ | -0.43 $^{+ 0.10 }_{- 0.08 }$ | 52.90 $^{+ 0.04 }_{- 0.04 }$ | 1.42 $^{+ 0.18 }_{- 0.12 }$ | 9.5 $^{+ 1.3 }_{- 1.1 }$ |
| $f_V = 1$ | 186 | 17.59 $^{+ 0.01 }_{- 0.01 }$ | 50.30 $^{+ 0.08 }_{- 0.08 }$ | 50.31 $^{+ 0.23 }_{- 0.17 }$ | -0.73 $^{+ 0.10 }_{- 0.10 }$ | 53.03 $^{+ 0.04 }_{- 0.05 }$ | 0.87 $^{+ 0.19 }_{- 0.15 }$ | 7.2 $^{+ 1.1 }_{- 1.1 }$ |
| $\epsilon_e = 0.1$ | 457 | 17.98 $^{+ 0.01 }_{- 0.01 }$ | 51.55 $^{+ 0.02 }_{- 0.02 }$ | 51.88 $^{+ 0.05 }_{- 0.04 }$ | -0.53 $^{+ 0.02 }_{- 0.02 }$ | 54.11 $^{+ 0.01 }_{- 0.01 }$ | 1.09 $^{+ 0.04 }_{- 0.03 }$ | 10.4 $^{+ 0.3 }_{- 0.3 }$ |
| $\epsilon_B = 0.005$ | 800 | 18.23 $^{+ 0.01 }_{- 0.01 }$ | 51.69 $^{+ 0.02 }_{- 0.02 }$ | 51.95 $^{+ 0.07 }_{- 0.05 }$ | -0.87 $^{+ 0.03 }_{- 0.03 }$ | 54.28 $^{+ 0.01 }_{- 0.02 }$ | 0.46 $^{+ 0.06 }_{- 0.05 }$ | 9.5 $^{+ 0.5 }_{- 0.3 }$ |
|  | 1377 | 18.46 $^{+ 0.01 }_{- 0.01 }$ | 51.91 $^{+ 0.02 }_{- 0.03 }$ | 52.05 $^{+ 0.06 }_{- 0.07 }$ | -1.17 $^{+ 0.03 }_{- 0.04 }$ | 54.51 $^{+ 0.02 }_{- 0.02 }$ | -0.13 $^{+ 0.05 }_{- 0.06 }$ | 8.3 $^{+ 0.4 }_{- 0.4 }$ |

![](img/equipartition_plots_jet.pdf)

# Outflow Modelling

The SED fits described in §3 allow us to constrain the peak frequency ($\nu_p$) and the peak flux density ($F_p$) in each epoch (Table [1](#tab:2) and Figure [5](#fig:2)). We found that the peak flux density $F_p$ for the transient component increases for the first five epochs, then appears to plateau in the subsequent two epochs. The most dramatic brightening occurred between $\delta t \sim 186$ days and $\delta t \sim 457$ days post-discovery, with the peak flux density evolving as $t^{2.1}$ and all single-frequency radio light curves increasing by factors of $\sim3-8$. During this time range, we also find that the self-absorption frequency $\nu_a$ increases, which is unusual but not unprecedented when compared to previously seen behavior in other TDEs (cite: alexander_2016; Eftekhari; AT2020vwl; AT2018hyz). We find that $\nu_a$ decays as $t^{-1.4}$ and $t^{-1.3}$ in the epochs preceding and succeeding the brightening event that occurred between days $\delta t \sim 186$ and $\delta t \sim 457$. To model the atypical evolution of the SED, we examined two scenarios: (1) the radio emission is caused by a non-relativistic spherical outflow, or (2) the emission is due to a relativistic outflow in the form of a collimated jet viewed off-axis from the line of sight. While we initially assume that the complete radio evolution can be explained by a single outflow, we also discuss the possibility of multiple outflows in §[\[sec:split_launch\]](#sec:split_launch).

![](img/Ek_gamma.pdf)

## Non-Relativistic Outflow

Assuming the observed radio emission is produced by synchrotron radiation generated in the shock between a blast wave and the ambient circumnuclear environment, we can determine the physical properties of the outflow using the procedures outlined in (cite: Barniol_Duran_2013). In our analysis, we associate $\nu_p$ with $\nu_a$ and assume $\nu_m < \nu_a$. Following (cite: Barniol_Duran_2013), we define the emitting area $f_A \equiv A/ (\pi R^2/\Gamma^2)$ and the emitting volume $f_V \equiv V/ (\pi R^3/\Gamma^4)$ and take $\Gamma=1$ for an assumed non-relativistic outflow. To compare to previously studied TDEs from the literature (cite: alexander_2016; at2019dsg; AT2018hyz), we assume that the emitting volume of the outflow is confined to a spherically-symmetric shell of radius $0.1R$, implying $f_A = 1$ and $f_V = \frac{4}{3}(1-0.9^3) \approx 0.36$. With this framework, we can now derive the radius $R$ and energy $E$ using this geometry and the observed values of $F_p$ and $\nu_p$. With $p=2.8$, the expressions for the radius and energy are given by (cite: Barniol_Duran_2013):

$$\begin{equation}
    R \approx \   (2.2 \times 10^{17} {\rm cm})\frac{F_{p,{\rm mJy}}^{\frac{44}{93}}d_{L,28}^{\frac{88}{93}} \epsilon^{\frac{1}{17}}\xi^{\frac{1}{93}} 4^{\frac{1}{93}}}{
    \nu_{p,10} (1+z)^{\frac{137}{93}} f_A^{\frac{13}{93}} f_V^{\frac{5}{93}}\gamma_m^\frac{4}{93}}
\end{equation}$$

$$\begin{equation}
    E\approx (2.9 \times 10^{50} {\rm erg}) \frac{F_{p,{\rm mJy}}^{\frac{112}{93}}d_{L,28}^{\frac{224}{93}}f_V^{\frac{38}{93}}\xi^{\frac{55}{93}} 4^{\frac{55}{93}} (11+6\epsilon)}{ 
    \nu_{p,10}(1+z)^{\frac{205}{93}}f_A^{\frac{19}{31}} \gamma_m^\frac{44}{93}(17 \epsilon^{\frac{6}{17}})}
\end{equation}$$ where $F_p$ is scaled to units of mJy, $\nu_p$ to units of 10 GHz, and the luminosity distance $d_L$ in units of $10^{28}$ cm. In our analysis we set the minimum Lorentz factor $\gamma_m=2$ and incorporate additional factors of 4 as specified in (cite: Barniol_Duran_2013) for the Newtonian limit. We parameterize deviations from equipartition by defining $\epsilon = (11/6)(\epsilon_B/\epsilon_e)$, where $\epsilon_e$ and $\epsilon_B$ are the fractions of the total energy in electrons and the magnetic field respectively. In our analysis, we adopt the typical value of $\epsilon_e=0.1$ (cite: Panaitescu_2002) and fix $\epsilon_B = 0.2$, which is motivated by the observed location of the cooling break at 132 days (§[3.1](#sec:cool)). We assume that the kinetic energy is dominated by the protons in the outflow; we thus incorporate the extra energy carried by the hot protons using the correction factor $\xi =1+\epsilon_e^{-1}$ to the total energy (cite: Barniol_Duran_2013).

With the computed values of $R$, we can also solve for the magnetic field strength $B$, the Lorentz factor $\gamma_e$ of the electrons that radiate at $\nu_p$, and the total number of electrons in the observed region $N_e$ (see equations 14, 15, 16 in (cite: Barniol_Duran_2013)). The inferred values of $N_e$ and $R$ allow us to estimate the density of electrons in the ambient medium at radius $R$ as $n_\text{ext} = n_e/4$ where $n_e = N_e/V$ is the number density of the electrons in the outflow and the factor of $1/4$ accounts for the shock jump conditions. Here, $V$ is the emitting volume as defined above: a spherical shell with a thickness of $0.1R$ just behind the blast wave. The results of our analysis are shown in Table [\[tab:3\]](#tab:3).

In Figure [6](#fig:eq_jet), we show the temporal evolution of the emitting region size $R$ and the corresponding minimum equipartition energy $E$. The size of the synchrotron emitting region increases monotonically with time as one would expect for an expanding outflow. Including all epochs, the radius expands at a rate of $R\propto t^{1.3}$, however the four observations in 2019 ($\delta t = 49 - 186$) follow a much steeper trend of $R\propto t^{2.3}$, and from 2020 onward ($\delta t = 457 - 1377$) the radius increases as $R\propto t^{1.3}$. The minimum energy of this region also shows a positive trend in time, increasing more than three orders of magnitude as $E\propto t^{2.2}$ over the full four years of observation. The inferred specific momentum ($\Gamma \beta$) also goes up with time for some portion of the light curve. We also construct a radial profile for the magnetic field strength (see Figure [6](#fig:eq_jet)). We find that the magnetic field decays with increasing distance as $B(r)\propto r^{-0.8}$ at early times and as $B(r)\propto r^{-1}$ at late times. For discussion of the density profile see Section §[5.2](#sec:density).

## Relativistic Jet from an Arbitrary Viewing Angle

Given the nearby ($z=0.0262$) location of this TDE, the radio luminosity, evolution timescale, and lack of detected $\gamma$-ray emission suggest that this outflow is not due to a relativistic jet pointed on-axis towards the observer. However, the appearance of a relativistic or collimated outflow can change due to the viewing angle. If a relativistic jet were to be launched off-axis, the emission would become suppressed at early times due to relativistic beaming away from the viewer. As the jet decelerates, the observer may begin seeing emission from inside the beaming cone.

We examined the possibility of a relativistic jet in ASASSN-19bt by employing the model outlined in (cite: matsumoto). This work generalizes (cite: Barniol_Duran_2013)’s analysis of an on-axis relativistic jet in energy equipartition to consider a jet observed from arbitrary viewing angles. Here, we briefly summarize this model and update the equations from (cite: matsumoto) to account for deviations from energy equipartition and the additional kinetic energy carried by hot protons, as we did in §[4.1](#outflow:nonrel). Unless otherwise specified, all variables have the same definitions as in §[4.1](#outflow:nonrel).

In the relativistic limit, there are two additional degrees of freedom: the jet Lorentz factor $\Gamma$ and the viewing angle $\theta_\text{obs}$ between the observer’s line of sight and the source’s direction of motion. The energy therefore does not have a global minimum and we require an additional constraint on the system to solve for the physical parameters of the jet as we did above. We obtain this constraint by making an assumption about the outflow launch time, following (cite: matsumoto). As in §[3.1](#sec:cool), we take the launch time to be $\delta t=0$ days.

Following the procedure outlined in (cite: matsumoto), we first solved for the radius that minimizes the total energy under a $p=2.8$ power law distribution of electrons.

In this model, the observed location of the cooling break implies $3\times 10^{-4} < \epsilon_B < 0.005$ depending on the viewing angle (Table [2](#tab:eb) in Appendix [7](#appendix:sed) gives the precise values). This suggests that the system is not in equipartition; therefore, as in the non-relativistic case, we incorporate additional terms to accommodate this deviation following (cite: Barniol_Duran_2013). For $p=2.8$, the corresponding radius and energy are:

$$\begin{equation}
    R \approx \   (2.4 \times 10^{17} {\rm cm})\frac{F_{p,{\rm mJy}}^{\frac{44}{93}}d_{L,28}^{\frac{88}{93}} \Gamma  \epsilon^{\frac{1}{12}}\xi^{\frac{1}{93}}}{
    \nu_{p,10} (1+z)^{\frac{137}{93}} f_A^{\frac{13}{93}} f_V^\frac{5}{93} \gamma_m^\frac{4}{93} \delta_D^\frac{13}{31}}
\end{equation}$$

$$\begin{equation}
    E \approx (6.6 \times 10^{50} {\rm erg}) \frac{F_{p,{\rm mJy}}^{\frac{112}{93}}d_{L,28}^{\frac{224}{93}}f_V^{\frac{38}{93}}\xi^{\frac{55}{93}} \Gamma(11+6\epsilon)}{ 
    \nu_{p,10}(1+z)^{\frac{205}{93}}f_A^{\frac{19}{31}} \gamma_m^\frac{44}{93} \delta_D^\frac{81}{31}(17\epsilon^{\frac{5}{12}})}
\end{equation}$$

In this case, $\gamma_m = \chi_e (\Gamma-1)$, where $\chi_e = (p-2/p-1)\epsilon_e(m_p/m_e)$, and $\delta_D\equiv1/\Gamma(1-\beta \cos{\theta_\text{obs}})$ is the relativistic Doppler factor for a given source velocity $\beta=\sqrt{1-1/\Gamma^2}$. The additional terms involving $\xi$ and $\epsilon$ account for hot protons and deviations from equipartition with the same definitions as in §[4.1](#outflow:nonrel). We solve for $\Gamma$ in each epoch using the same procedure outlined (cite: matsumoto).

We initially set the jet area and volume filling factors to be $f_A=f_V=1$. This accounts only for energy within an angle of $1/\Gamma$ from our line of sight. Material at larger angles will contribute negligibly to the observed emission due to relativistic beaming, so this provides the minimum energy required to explain our observations at each epoch. However, a jet with an evolving opening angle of $\theta_j=1/\Gamma$ is not physically likely; while we do eventually expect lateral spreading of the jet as it decelerates, theoretical work suggests that jet spreading is likely not yet important at the large bulk $\Gamma$ values required by our observations (cite: duffell_2018). We therefore also consider other possible jet geometries in which the jet opening angle remains fixed independent of $\Gamma$. We did not include any narrow jet geometries ($\theta_j < 1/\Gamma$) as the implied jet opening angle became nonphysical due to large bulk $\Gamma$s. We do investigate the effect of a wide jet geometry by accounting for additional energy outside the beamed emission region within an angle of $1/\Gamma$, which contributes negligibly to the observed emission but increases the total energy of the jet. The true collimation of TDE jets is still unknown. AGN jets are typically seen to have $\Gamma \lesssim 10$ with opening angles around $\theta_{j}\sim20^\circ$ whereas GRBs have been seen to launch highly collimated jets with $\Gamma\sim 100$ with opening angles often below $10^\circ$ ((cite: Goldstein_2016); (cite: Pushkarev_2017); (cite: Rouco_2023)). Therefore, for our analysis, we impose an intermediate jet opening angle of $\theta_{j} = 10^\circ$. For this fixed opening angle, we are always in the regime where $\theta_{j} > 1/\Gamma$ and subsequently correct for the unseen material by multiplying the equipartition energy by a factor of $4\Gamma^2(1 - \cos{\theta_j})$. The other derived quantities are unaffected, as they depend only on the emission within the observable region (so we can keep $f_A=f_V=1$ throughout).

In Figure [6](#fig:eq_jet), we show our derived physical parameters for six possible viewing angles: $\theta_\text{obs} = 0.1,0.26,0.52,0.79,1.05,1.57$ (i.e., $6^\circ, 15^\circ, 30^\circ,  45^\circ, 60^\circ$, and $90^\circ$). We find that the solutions become exceedingly extreme for small viewing angles. Solutions for the most on axis case we tested ($\theta_\text{obs} \approx 6^\circ$) resulted in unphysical outflow velocities of $\Gamma>1000$ and energies approaching $10^{54}$ erg. These solutions diverge to higher energies for small $\theta_\text{obs}$ due to the large beaming effects needed to reduce the observed flux towards the observer. We find that our most reasonable solutions appear to be when we consider the relativistic outflow as a highly off-axis collimated jet (the two most off-axis cases are shown in Table [\[tab:3\]](#tab:3)). A jet truly spreading with $\theta_j = 1/\Gamma$ would exhibit two periods of roughly constant energy at $\sim 2 \times 10^{50}$ erg from $\sim$ 50 - 190 days and $\sim 7 \times 10^{51}$ erg from $\sim$ 460 - 1380 days. The wide jet geometry with $\theta_j = 10^\circ$ instead implies that the energy decreases by a factor of $\sim10$ during the first 200 days, then remains constant at $E\sim 10^{52} \ \text{erg}$ at later times. All viewing angles yield a solution where the jet propagates at nearly light speed with $\Gamma\sim10-20$ for the most off-axis viewing angles. We find that the jet slows as $\Gamma\propto t^{-1}$. After the radio re-brightening, we find that $\Gamma$ exhibits a weaker decay where $\Gamma\propto t^{-0.2}$. We note that $\Gamma$ is dependent on the inferred launch date of the jet, for discussion of alternative launch dates see Section §[\[sec:split_launch\]](#sec:split_launch).

# Discussion

Each of the two models discussed in §[4](#sec:analysis) provides a reasonable fit to the data, but each has some implications that are difficult to explain. Here, we present the implications of these two models and compare ASASSN-19bt to other TDEs in the literature.

Aspects of ASASSN-19bt’s radio light curve resemble those of a few other known TDEs (Figure [8](#fig:lit_lc_radio)) as many have displayed delayed radio brightening a few years after discovery (cite: horesh_15oi; iPTF16fnl; AT2019azh; AT2018hyz; yvette_2023). At early times, ASASSN-19bt appears most similar to the slow rise seen in AT2019azh (cite: AT2019azh). AT2019azh also exhibited a late-time flare at a similar timescale to ASASSN-19bt’s brightening (cite: sfaradi_19azh). The origin of the radio emission in AT2019azh was difficult to determine, with only the unbound debris stream ruled out as a possibility (cite: AT2019azh). The late-time evolution and observed luminosity of ASASSN-19bt is also similar to IGR J12580+0134 and ARP 299-B AT1, TDEs with suspected off-axis relativistic jets (cite: IGR_Lei; ARP_2018). However, its radio evolution is quite different from that of two other TDEs that may harbor powerful jets: AT2018hyz, which may have an off-axis jet and continues to brighten rapidly $>1000$ days post-discovery, and Sw J1644+57, which had an on-axis jet but remained much more luminous than ASASSN-19bt at every phase of its evolution (even at late times when its jet has decelerated and the observed emission should be independent of the viewing angle). We develop these comparisons further below.

![](img/litTDE_radiolightcurves.pdf)

## Energy and Velocity

We show the outflow kinetic energy and inferred velocity of ASASSN-19bt in comparison to those of known TDEs in Figure [7](#fig:Ek_gamma). As mentioned previously, ASASSN-19bt exhibits a dramatic energy increase under the Newtonian model, increasing by 3 orders of magnitude over the period of our observations. This is by far the largest energy increase ever seen in any TDE. The off-axis jet scenario also requires the energy to increase with time, with a total energy in the final epoch $\sim50$ times larger than in the first epoch for $\theta_j = 1/\Gamma$ and $\sim5$ times larger for $\theta_j = 10^\circ$.

While energy injection has been inferred for TDEs before (e.g. (cite: berger_2012) for Sw J1644+57, but see also (cite: Beniamini_2023)), the much larger energy increase required for ASASSN-19bt is difficult to explain. The energy increase observed in Sw J1644+57 was by a factor $\sim20$ (cite: Eftekhari) and energy increases were also seen in the non-jetted TDEs AT2019dsg (factor $\sim10$; (cite: at2019dsg)) and AT2019azh (factor $\sim100$; (cite: AT2019azh)). Our non-relativistic shell model for ASASSN-19bt indicated $E\propto t^{2.2}$ on average, with a steeper dependence during the first four epochs and a shallow dependence for the remaining three epochs. In the off-axis jet model with $\theta_j =1/\Gamma$, the energy undergoes shallower growth with $E\propto t^{0.1}$ at early times and $E\propto t^{0.7}$ at late times. The energy is declining then flat for the $\theta_j=10^{\circ}$ jet.

While the jet energy we calculate for ASASSN-19bt for the most off-axis viewing angles is similar to that computed for the jetted TDE Sw J1644+57, our model implies a surprisingly large $\Gamma$ that persists through our last observation at $\delta t\sim1377$ days (Figure [6](#fig:eq_jet), top right panel). This is similar to AT2018hyz, which was modeled by (cite: matsumoto) as an off-axis jet. When we repeat their analysis under the same assumptions used for ASASSN-19bt we find that modeling AT2018hyz as an off-axis jet requires a slightly higher energy, with slightly lower but still relativistic $\Gamma$ at late times (see Figure [7](#fig:Ek_gamma)). In contrast, Sw J1644+57’s jet had decelerated to non-relativistic speeds ($\Gamma\sim1$) by $\delta t\sim700$ days (cite: Eftekhari). If the relativistic jet model is correct, it would imply that ASASSN-19bt launched the most highly relativistic outflow seen in any TDE to date. It is difficult to understand how such a jet would remain relativistic to such late times in the high-density nuclear environments in which TDEs occur. The velocity evolution is equally perplexing in the Newtonian model; while the outflow velocities in the non-relativistic model are consistent with the sample of optically discovered thermal TDEs, ASASSN-19bt’s outflow would have to speed up with time (Figure [6](#fig:eq_jet), bottom left panel), which is difficult to understand physically. In steep density profiles, Newtonian shocks can accelerate; however, this requires a much steeper density profile than we see for ASASSN-19bt (cite: Govreen-Segal_2021).

## Circumnuclear Density

In Figure [9](#fig:density_profile) we show the inferred circumnuclear density profiles for our ASASSN-19bt models compared to previously studied TDEs with observed radio emission. To standardize the comparison, we scale the radii by the Schwarzschild radius ($R_s = 2 G M_{\rm BH}/c^2$) of the SMBH at the center of each TDE host galaxy and recompute the inferred densities for the thermal TDEs ASASSN-14li, AT2019dsg, CNSS J0019+00, AT2018hyz, AT2020opy, and AT2020vwl using a standard definition for the volume of the emitting region (a spherical 0.1$R$ shell). We use the SMBH masses from Alexander et al. 2024 (in prep.) and references therein (particularly (cite: Yao_2024)).

The outflow from ASASSN-19bt probes a relatively large fraction of the circumnuclear environment when compared to that of other previously studied TDEs. Both the Newtonian and jet models appear to recover the presence of two separate radial profiles for the magnetic field strength and number density of emitting electrons, corresponding to the pre-brightening and post-brightening portions of the radio light curves. We find that the density profile under the non-relativistic model exhibits a $n \propto r^{-3/2}$ slope similar to other thermal TDEs such as AT2020opy and the early epochs of AT2019dsg (cite: at2019dsg; at2020opy). This is consistent with the classical expectation for spherical Bondi accretion (cite: Bondi_1952).

After the blast wave reaches $R\sim 10^{16.5}$ cm, the density increases briefly then continues to decay at a slightly steeper rate $n(r)\propto r^{-1.9}$. This is within the range of density profiles previously observed in TDEs, as a

$n \propto r^{-2.5}$ profile was measured for ASASSN-14li ((cite: alexander_2016); and CNSS J0019+00 (cite: CNSS)).

In the relativistic model, we estimate the density of the unshocked ambient medium at radius $R$ as $n_\text{ext} = n_e/4\Gamma^2$ where $n_e = N_e/V$ is the number density of emitting electrons behind the blastwave and $V = \pi R^3/\Gamma^4$ is the volume of the emission region (cite: Barniol_Duran_2013). From this we find that the constructed density profile decays as $n(r)\propto r^{-4.3}$ at early times and as $n(r)\propto r^{-2.6}$ at late times, which is the steepest density profile seen around any TDE to date. We find that the ASASSN-19bt exhibits a similar density profile to that of AT2018hyz if the latter is modeled as an off-axis jet (cite: matsumoto), but our observations span a much wider range of circumnuclear radii.

Along with the steepness of the density profile, the off-axis jet models also yield higher densities at large radii compared to other TDEs (for both ASASSN-19bt and AT2018hyz). Assuming that the emitting electrons were swept up by the jet, we can approximate swept up mass as $M_\text{swept}\sim m_\text{p} N_e \left({\theta_j}\right)^2\left(1/\Gamma_\text{latest} \right)^2 \simeq 3 \times 10^{-3} \text{M}_\odot$ for the most off-axis case, assuming a fixed opening angle of $\theta_j = 10^\circ$. As the jet is still relativistic and has not yet decelerated, this implies the total kinetic energy responsible for such a jet is $E_\text{kin} \gtrsim \Gamma M_\text{swept} c^2 \simeq 10^{53} \text{erg}$ (in the more conservative case where $\theta_j = 1/\Gamma_\text{latest} < 10^\circ$, then the required energy is lower by a factor $\sim2$). This energy is among the largest ever inferred for any extragalactic transient; however, it is similar to the energy required by several radio modellings for Swift J1644+57 (cite: matsumoto).

![](img/density_profile.pdf)

## Multiple Outflows?

The models described in §[4](#sec:analysis) both assume that a single impulsive outflow powers the entire observed radio evolution. However, as previously noted, $F_p$ increases dramatically between $\delta t \sim 186$ days and $\delta t \sim 457$ days. This abrupt radio brightening, together with the presence of a clear discontinuity in the outflow parameters between days $\delta t \sim 186$ and $\delta t \sim 457$ days in both models may imply the presence of two outflows contributing to the radio emission on different timescales. This scenario would make ASASSN-19bt similar to ASASSN-15oi, which showed two distinct emission episodes in its radio light curve (cite: horesh_15oi). Modeling of ASASSN-15oi’s radio emission revealed that the second emission peak likely corresponds to a more energetic outflow launched several hundred days post-disruption (Hajela et al. in prep).

Following (cite: alexander_2016) and (cite: yvette_2023), we examined the evolution of ASASSN-19bt’s emission radius to estimate the outflow launch time for the pre- and post-brightening subsets of the data. For the non-relativistic model outlined in (cite: Barniol_Duran_2013), if the outflow is assumed to be moving at a constant velocity then we can apply a linear fit to the radius evolution and extrapolate to $R = 0$. However, applying a linear fit to all of the data implies a launch date of $\delta t \approx46$ days, which is inconsistent with our initial radio detection at $\delta t = 40$ days. A linear fit to just the early epochs prior to the re-brightening yields a similarly unphysical launch date of $\delta t \approx52$ days and overall provides a poor fit to the data. If instead we fit the radius evolution in the early epochs with a power law, we find that a much better fit to the data can be obtained if the emitting region is expanding as $R \propto t^{2.3}$. This however suggests a dramatic acceleration of the outflow during the first 186 days, which is difficult to explain (as noted in Section [5.1](#sec:ev)). Linearly extrapolating the radius evolution for the later epochs ($\delta t > 1$ year) separately would imply a launch date of $\delta t \approx 210$ days, possibly implying that a second outflow launched substantially after the time of disruption powers the latter half of the radio light curve.

For the relativistic solutions outlined in (cite: matsumoto), a launch date must be assigned in order to solve for the outflow velocity $\Gamma$; for our analysis we set this to be $\delta t = 0$ days. We found that the resulting off-axis jet solutions preferred outflow velocities with $\Gamma \gtrsim 8$. For all viewing angles, $\Gamma$ decreases by a factor $\sim3$ over the first 186 days, then increases slightly at 457 days, and then resumes slowly decreasing.

Given the suggested launch date for the later epochs in the non-relativistic case, we considered the possibility of two relativistic outflows, where one outflow was launched at $\delta t = 0$ days and the other was launched $\sim210$ days later. This still requires $\Gamma \approx 8$ for the emission at $\delta t > 1$ yr in the most off-axis case and does not fully resolve the energy and density discontinuities. Although this is perhaps more physically plausible than the accelerating outflow required in the non-relativistic case, it is still surprising that even for the most off-axis viewing angles, $\Gamma$ remains significantly $>1$ even in our last observation at 1377 days.

## Outflow Mechanism

In order to assess the likelihood of either model, we need to evaluate whether these results are consistent with existing theories describing the origin of radio emission from TDEs. Most TDEs that have received extensive follow-up in the radio are modelled using the Newtonian formalisms outlined in (cite: Barniol_Duran_2013), therefore, this model is most easily comparable to other TDEs in the literature. The bulk outflow velocity implied by the Newtonian model ($\beta\approx0.05$) matches well with the expected velocities of $\beta\approx0.01-0.1$ for winds due to accretion onto a SMBH (cite: Strubbe; Tchekhovskoy). However, outflows launched with these velocities could also be explained by the unbound debris propagating into the circumnuclear medium or ejecta from a collision-induced outflow (CIO) where the debris fallback stream intersects with itself (cite: krolik_2016; bonnerot_2020). Nonetheless, these non-relativistic outflow scenarios all fail to address the apparent acceleration of the outflow in the first 186 days from $\beta\approx0.016$ to $\beta\approx0.09$. Moreover, while increasing energy has previously been found to be expected in some non-relativistic models for TDEs (cite: matsumoto_19dsg), ASASSN-19bt’s exceptionally rapid energy increase may be challenging to explain. If the thousandfold increase in the energy is to be attributed to energy injection, it is difficult to conceive of a central engine that remains continuously active for years after the star had been initially disrupted. For example, if we assume that the central engine is only active during the super-Eddington phase, then one would expect the energy injection to stop after approximately 500 days as that was thought to be the duration of the super-Eddington phase for Sw J1644+57 based on a rapid shutoff of the X-ray emission at that time (cite: Mangano_2016; berger_2012). Other on-axis jetted TDEs, such as AT2022cmc, show even earlier jet shutoff times (cite: eftekhari_2024). Alternately, energy injection can occur in transients with radially stratified velocity in their ejecta, as previously proposed for some TDEs (e.g. Sw J1644+57; (cite: berger_2012)) and other transients (e.g. GW170817; (cite: li_2018)). However, the spherical outflow model for ASASSN-19bt requires a larger and more rapid energy increase than either of these cases.

The off-axis relativistic jet scenario avoids the dramatic energy injection required by the non-relativistic outflow, but is also puzzling. We find that the minimal energy of the outflow appears roughly constant at $\sim 2 \times 10^{50}$ erg at early times, then increasing to $\sim 7 \times 10^{51}$ erg at late times for the most off-axis cases ($\theta_\text{obs} \gtrsim 60^\circ$). For a jet with $\theta_j=10^{\circ}$, the energy decreases by a factor of $\sim10$ during the first 200 days, then remains constant at $E\sim 10^{52} \ \text{erg}$ at later times. It is not clear that this initial energy decrease is physical. Furthermore, as discussed in Section [5.2](#sec:density), a higher total kinetic energy is required such that $M_\text{jet} > M_\text{swept}$ to avoid complete deceleration of the jet.

A similar increase in energy was observed in the prototypical jetted TDE Swift J1644+57 on a similar timescale (cite: Eftekhari). In Swift J1644+57, this energy increase may have also been accompanied by a slight density enhancement, similar to (but less dramatic than) the discontinuity in the density profile seen around ASASSN-19bt that accompanies its energy increase (cite: Eftekhari). (cite: berger_2012) argued that the energy injection found in Swift J1644+57 could not be explained by further accretion of the fallback stream and instead is likely due to the relativistic jet launching with a wide range of initial Lorentz factors. However, recently, (cite: Beniamini_2023) argued that the observed energy increase can be explained purely by the jet being initially viewed slightly off-axis; as the jet slowed down, the beaming cone opens up to reveal more emission. This explanation does not work for ASASSN-19bt as $\Gamma$ increases slightly between the two epochs where the energy jumps. Instead, the discrepancy between the early and late time energies may indicate the presence of two outflows launched at separate times. A scenario where the accretion rate and subsequent jet launch is significantly delayed relative to peak optical light may explain the presence of a more energetic outflow launched several hundred days post-discovery (cite: Metzger_2022). It is also possible that accretion starts earlier and the jet is launched only once the accretion rate falls below some Eddington threshold (cite: Giannios_2011; Pasham_2018).

If the radio emission in ASASSN-19bt is in fact due to a relativistic jet launched away from our line of sight, then one might expect the temporal evolution to follow that of AT2018hyz. In Figures [7](#fig:Ek_gamma) and [9](#fig:density_profile), we show that ASASSN-19bt exhibits very similar radii, energy, outflow velocity, and density to AT2018hyz using the off-axis jet model. In contrast, the 5 GHz light curve for ASASSN-19bt appears remarkably different from that of AT2018hyz (see Figure [8](#fig:lit_lc_radio)). Furthermore the radio $F_p$ for ASASSN-19bt is plateauing, which is counter-intuitive for an off-axis jet that has not yet decelerated to non-relativistic speeds. Given the freely expanding jet and steep density profile, this evolution may be still acceptable, but is not indefinitely sustainable. An important prediction of the off-axis model (if true) is that $\Gamma$ should decline in future epochs and the radio luminosity should increase again as the jet decelerates to $\Gamma\sim1$.

## X-ray Emission

As seen in Figure [2](#fig:lit_lc), TDEs exhibit a diverse range of X-ray luminosities. ASASSN-19bt has the faintest known X-ray emission of any optically-selected TDE at $\delta t\lesssim50$ days and remains faint in the X-rays to late times ($\delta t\sim700$ days). Initially-faint X-ray emission followed by a brightening phase has often been explained as evidence for delayed formation of the accretion disk (cite: Gezari_2017; liu_22). However, (cite: guolo_23) showed that X-ray obscuration may be a more likely cause for this behavior. Many models invoke some form of X-ray suppression via the reprocessing of X-ray emission into lower-energy emission by optically thick gas surrounding the black hole. In particular, some have proposed models where the degree of X-ray reprocessing is orientation dependent (cite: Dai_2018; Thomsen_2022; Parkinson_2022). In the context of these models, the reprocessing layer is produced by super-Eddington disk outflows, which would result in early time X-ray suppression corresponding to when the accretion rate was highest. For TDEs with low inclination angles, where the accretion disk is viewed face-on, the expected reprocessing is minimal. However, for high inclination angles, where the disk is viewed edge-on, the reprocessing of X-ray emission is expected to dominate, leading to fainter emission. Under this scenario, one would expect the most X-ray dim TDEs to be those with the highest inclination angles.

The presence of the cooling break identified in §[3.1](#sec:cool) suggests that the synchrotron emission seen in the radio under-predicts ASASSN-19bt’s X-ray emission if extrapolated to higher frequencies, requiring an additional emission component. In Swift J1644+57, one model for the X-rays at early times is inverse Compton emission from the jet, which produces a rather hard spectrum (cite: Crumley_2016). For ASASSN-19bt, the measured photon index $\Gamma$ is significantly harder than the X-rays of most optically-selected TDEs (cite: guolo_23). Therefore, one possibility is that the X-rays we see in ASASSN-19bt could be inverse Compton emission.

Alternately, the observed X-rays could be intrinsically softer X-ray emission that is highly absorbed. In this case, ASASSN-19bt’s exceptionally faint X-ray emission might imply that we are viewing this system nearly perfectly edge-on, which would also be consistent with the most plausible relativistic jet model for the radio emission, where the jet is launched maximally off-axis ($\sim 90^\circ$) with respect to our line of sight. However, our X-ray spectral modeling found no evidence for intrinsic X-ray absorption, although the limits are not tight. The apparent lack of X-ray absorption by neutral or partially ionized material may be caused by the X-ray obscuring material in the edge-on disk already being fully ionized.

# Conclusions

We present the results of our radio and X-ray monitoring of the TDE ASASSN-19bt, spanning nearly four years after the onset of the optical flare. Radio emission was first detected shortly after the optical discovery and continued to rise for years afterward, with the peak radio flux density plateauing $\delta t\gtrsim1$ years post-discovery. In contrast, ASASSN-19bt displays very little activity in the X-rays; its early X-ray emission was among the least luminous of any optically-selected TDE and no X-rays have been detected since approximately 225 days post-discovery.

The location of the cooling break suggests that the X-ray emission is not synchrotron in origin. We find that ASASSN-19bt’s harder X-ray spectrum hints at inverse Compton emission from a possible jet or heavily absorbed softer X-ray emission being viewed through a reprocessing layer (we see no evidence for absorption in the X-ray spectrum, but the constraints are modest due to the faintness of the source). In the latter case, the lack of luminous X-ray emission may be a result of viewing the accretion disk edge-on, as orientation-dependent X-ray reprocessing models align with ASASSN-19bt’s dim X-ray emission.

We employed two models to describe the possible origins of the radio emission, a non-relativistic spherical blast wave and a relativistic jet launched off-axis from our line of sight. We find that a spherical outflow model would imply a continuous energy rise in the outflow from $\sim10^{46}$ erg to $\sim10^{49}$ erg with speeds consistent with $v\approx 0.016c-0.09c$. A bulk outflow velocity of $\beta\approx0.05$ aligns with expected velocities for accretion-driven winds, unbound debris, or collision-induced outflows. Notably, all of these non-relativistic scenarios fall short in explaining the observed outflow acceleration within the first 186 days. In contrast, the off-axis relativistic model for a jet with $\theta_j = 1/\Gamma$ instead implies that the outflow expands at speeds corresponding to $\Gamma\approx10$ and takes on two periods of roughly constant energy at $\sim 2 \times 10^{50}$ erg to $\sim 7 \times 10^{51}$ erg for the most off-axis cases ($\theta_\text{obs} \gtrsim 60^\circ$). If we impose a fixed jet opening angle of $\theta_j = 10^\circ$, we instead see decreasing energy at early times and a roughly constant energy of $E\approx 10^{52}$ erg at late times in the maximally off-axis case. The peak flux density and self-absorption frequency both increase $\sim1$ year post-optical peak, resulting in discontinuities in the magnetic field and density profiles surrounding the SMBH for both models.

We find that the off-axis relativistic jet model alleviates some of the concerns presented by the simple Newtonian model (e.g. the large increase in the energy), but also has some aspects that appear physically implausible (e.g. the overall energy budget). Neither model appears to provide a complete explanation for the radio emission and evolution, suggesting that the true emission geometry is likely more complex than either of the two limiting cases considered here, possibly involving multiple outflow mechanisms operating on different timescales. A key takeaway from this analysis is that more holistic TDE models are needed, incorporating information from emission across the electromagnetic spectrum.

ASASSN-19bt now becomes part of the collection of TDEs demonstrating unusual radio emission in the later stages. Undertaking extended radio observations of these TDEs, particularly at late times ($\sim$years post-disruption), will play a pivotal role in understanding the mechanisms behind the unusual late time radio emission displayed by a growing number of TDEs. We particularly emphasize the importance of Very Long Baseline Interferometry (VLBI) observations for nearby TDEs, as they are crucial for directly testing the off-axis relativistic jet hypothesis. The perpendicular motion of the jet relative to our line of sight makes VLBI observations of centroid motion a definitive smoking gun for relativistic jets within these systems (cite: ARP_2018). Careful interpretation of the physical parameters derived from the equipartition process may be needed on an event-by-event basis to properly distinguish between truly non-relativistic outflows and highly off-axis jets, with implications for the overall occurrence rate of powerful jets in TDEs.

# Acknowledgements

The Australia Telescope Compact Array is part of the Australia Telescope National Facility (<https://ror.org/05qajvd42>) which is funded by the Australian Government for operation as a National Facility managed by CSIRO. We acknowledge the Gomeroi people as the Traditional Owners of the Observatory site. The National Radio Astronomy Observatory (NRAO) is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. C. T. C. and K. D. A. acknowledge support provided by the NSF through award SOSPA9-007 from the NRAO and award AST-2307668. This work was partially supported by the Australian government through the Australian Research Council’s Discovery Projects funding scheme (DP200102471). The Berger Time-Domain Group at Harvard is supported by NSF and NASA grants. F.D.C. acknowledges support from the DGAPA/PAPIIT grant 113424.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01766.T. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We acknowledge the use of public data from the Swift data archive. This research is partially based on observations made by the Chandra X-ray Observatory under program DDT-20708675 (obsIDs 22182 and 22183; PI Alexander) and software provided by the Chandra X-ray Center (CXC) in the application package CIAO.

# Total Flux SED Fits and Equipartition Analysis

As described in Section [2.2](#sec:archival_radio), we detect archival radio emission from the host galaxy of ASASSN-19bt that predates the TDE. We therefore opted to subtract off a quiescent emission component scaled to this detection and assumed to be constant in time, modeling only the transient emission component. For completeness, here we show the observed SEDs without subtracting any host component, their model fits, and the extracted outflow parameters using the same methods outlined in Section §$\ref{sec:analysis}$ (Figures [10](#fig:1_orig), [11](#fig:eq_jet_orig), and Table [2](#tab:eb)). We note that these results do not alter the basic conclusions of our analysis. In particular, at late times the assumed host galaxy emission component is much fainter than the transient emission component at all frequencies; thus, the parameters at late times are virtually unchanged.

![](img/original_seds.jpg)

![](img/equipartition_plots_jet_original.pdf)

![](img/Ek_gamma_original.pdf)

+--------------------+--------------------+------------------------------+-------------------------------+
| $\theta_{\rm rad}$ | $\theta_{\rm deg}$ | $\epsilon_{B,\rm transient}$ | $\epsilon_{B,\rm total flux}$ |
+:==================:+:==================:+:============================:+:=============================:+
| *Off-Axis Relativistic Jet*                                                                            |
+--------------------+--------------------+------------------------------+-------------------------------+
| 0.1                | 6$^\circ$          | 0.0003                       | 0.0016                        |
+--------------------+--------------------+------------------------------+-------------------------------+
| 0.26               | 15$^\circ$         | 0.001                        | 0.004                         |
+--------------------+--------------------+------------------------------+-------------------------------+
| 0.52               | 30$^\circ$         | 0.002                        | 0.008                         |
+--------------------+--------------------+------------------------------+-------------------------------+
| 0.79               | 45$^\circ$         | 0.003                        | 0.012                         |
+--------------------+--------------------+------------------------------+-------------------------------+
| 1.05               | 60$^\circ$         | 0.003                        | 0.016                         |
+--------------------+--------------------+------------------------------+-------------------------------+
| 1.57               | 90$^\circ$         | 0.005                        | 0.022                         |
+--------------------+--------------------+------------------------------+-------------------------------+
| *Non-relativistic Spherical Outflow*                                                                   |
+--------------------+--------------------+------------------------------+-------------------------------+
| \-                 | \-                 | 0.2                          | 0.65                          |
+--------------------+--------------------+------------------------------+-------------------------------+

: Inferred values for $\epsilon_B$ assuming different outflow geometries.

natexlab

(ref: alexander_2016) Alexander, K. D., Berger, E., Guillochon, J., Zauderer, B. A., & Williams, P. K. G. 2016, ApJL, 819, L25, doi: [`10.3847/2041-8205/819/2/L25`](http://doi.org/10.3847/2041-8205/819/2/L25)

(ref: alexander2020) Alexander, K. D., van Velzen, S., Horesh, A., & Zauderer, B. A. 2020, Space Sci. Rev., 216, 81, doi: [`10.1007/s11214-020-00702-w`](http://doi.org/10.1007/s11214-020-00702-w)

(ref: CNSS) Anderson, M. M., Mooley, K. P., Hallinan, G., et al. 2020, ApJ, 903, 116, doi: [`10.3847/1538-4357/abb94b`](http://doi.org/10.3847/1538-4357/abb94b)

(ref: Andreoni_2022) Andreoni, I., Coughlin, M. W., Perley, D. A., et al. 2022, Nature, 612, 430, doi: [`10.1038/s41586-022-05465-8`](http://doi.org/10.1038/s41586-022-05465-8)

(ref: Barniol_Duran_2013) Barniol Duran, R., Nakar, E., & Piran, T. 2013, The Astrophysical Journal, 772, 78, doi: [`10.1088/0004-637X/772/1/78`](http://doi.org/10.1088/0004-637X/772/1/78)

(ref: Beniamini_2023) Beniamini, P., Piran, T., & Matsumoto, T. 2023, MNRAS, 524, 1386, doi: [`10.1093/mnras/stad1950`](http://doi.org/10.1093/mnras/stad1950)

(ref: berger_2012) Berger, E., Zauderer, A., Pooley, G. G., et al. 2012, ApJ, 748, 36, doi: [`10.1088/0004-637X/748/1/36`](http://doi.org/10.1088/0004-637X/748/1/36)

(ref: Bondi_1952) Bondi, H. 1952, MNRAS, 112, 195, doi: [`10.1093/mnras/112.2.195`](http://doi.org/10.1093/mnras/112.2.195)

(ref: bonnerot_2020) Bonnerot, C., & Lu, W. 2020, MNRAS, 495, 1374, doi: [`10.1093/mnras/staa1246`](http://doi.org/10.1093/mnras/staa1246)

(ref: Brown_2017) Brown, G. C., Levan, A. J., Stanway, E. R., et al. 2017, MNRAS, 472, 4469, doi: [`10.1093/mnras/stx2193`](http://doi.org/10.1093/mnras/stx2193)

(ref: Burrows05) Burrows, D. N., Hill, J. E., Nousek, J. A., et al. 2005, Space Sci. Rev., 120, 165, doi: [`10.1007/s11214-005-5097-2`](http://doi.org/10.1007/s11214-005-5097-2)

(ref: CASA_team) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: at2019dsg) Cendes, Y., Alexander, K. D., Berger, E., et al. 2021a, ApJ, 919, 127, doi: [`10.3847/1538-4357/ac110a`](http://doi.org/10.3847/1538-4357/ac110a)

(ref: Cendes_2021) Cendes, Y., Eftekhari, T., Berger, E., & Polisensky, E. 2021b, ApJ, 908, 125, doi: [`10.3847/1538-4357/abd323`](http://doi.org/10.3847/1538-4357/abd323)

(ref: AT2018hyz) Cendes, Y., Berger, E., Alexander, K. D., et al. 2022, ApJ, 938, 28, doi: [`10.3847/1538-4357/ac88d0`](http://doi.org/10.3847/1538-4357/ac88d0)

(ref: yvette_2023) —. 2023, arXiv e-prints, arXiv:2308.13595, doi: [`10.48550/arXiv.2308.13595`](http://doi.org/10.48550/arXiv.2308.13595)

(ref: cenko_2012) Cenko, S. B., Krimm, H. A., Horesh, A., et al. 2012, ApJ, 753, 77, doi: [`10.1088/0004-637X/753/1/77`](http://doi.org/10.1088/0004-637X/753/1/77)

(ref: 1998chevalier) Chevalier, R. A. 1998, ApJ, 499, 810, doi: [`10.1086/305676`](http://doi.org/10.1086/305676)

(ref: Condon_2002) Condon, J. J., Cotton, W. D., & Broderick, J. J. 2002, AJ, 124, 675, doi: [`10.1086/341650`](http://doi.org/10.1086/341650)

(ref: Crumley_2016) Crumley, P., Lu, W., Santana, R., et al. 2016, MNRAS, 460, 396, doi: [`10.1093/mnras/stw967`](http://doi.org/10.1093/mnras/stw967)

(ref: Dai_2018) Dai, L., McKinney, J. C., Roth, N., Ramirez-Ruiz, E., & Miller, M. C. 2018, ApJL, 859, L20, doi: [`10.3847/2041-8213/aab429`](http://doi.org/10.3847/2041-8213/aab429)

(ref: duffell_2018) Duffell, P. C., & Laskar, T. 2018, ApJ, 865, 94, doi: [`10.3847/1538-4357/aadb9c`](http://doi.org/10.3847/1538-4357/aadb9c)

(ref: Eftekhari) Eftekhari, T., Berger, E., Zauderer, B. A., Margutti, R., & Alexander, K. D. 2018, ApJ, 854, 86, doi: [`10.3847/1538-4357/aaa8e0`](http://doi.org/10.3847/1538-4357/aaa8e0)

(ref: eftekhari_2024) Eftekhari, T., Tchekhovskoy, A., Alexander, K. D., et al. 2024, Late-time X-ray Observations of the Jetted Tidal Disruption Event AT2022cmc: The Relativistic Jet Shuts Off. [`https://arxiv.org/abs/2404.10036`](https://arxiv.org/abs/2404.10036)

(ref: Evans09) Evans, P. A., Beardmore, A. P., Page, K. L., et al. 2009, MNRAS, 397, 1177, doi: [`10.1111/j.1365-2966.2009.14913.x`](http://doi.org/10.1111/j.1365-2966.2009.14913.x)

(ref: emcee) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: Gehrels04) Gehrels, N., Chincarini, G., Giommi, P., et al. 2004, ApJ, 611, 1005, doi: [`10.1086/422091`](http://doi.org/10.1086/422091)

(ref: Gezari_2017) Gezari, S., Cenko, S. B., & Arcavi, I. 2017, ApJL, 851, L47, doi: [`10.3847/2041-8213/aaa0c2`](http://doi.org/10.3847/2041-8213/aaa0c2)

(ref: Giannios_2011) Giannios, D., & Metzger, B. D. 2011, MNRAS, 416, 2102, doi: [`10.1111/j.1365-2966.2011.19188.x`](http://doi.org/10.1111/j.1365-2966.2011.19188.x)

(ref: Goldstein_2016) Goldstein, A., Connaughton, V., Briggs, M. S., & Burns, E. 2016, ApJ, 818, 18, doi: [`10.3847/0004-637X/818/1/18`](http://doi.org/10.3847/0004-637X/818/1/18)

(ref: AT2019azh) Goodwin, A. J., van Velzen, S., Miller-Jones, J. C. A., et al. 2022, MNRAS, 511, 5328, doi: [`10.1093/mnras/stac333`](http://doi.org/10.1093/mnras/stac333)

(ref: AT2020vwl) Goodwin, A. J., Alexander, K. D., Miller-Jones, J. C. A., et al. 2023a, MNRAS, 522, 5084, doi: [`10.1093/mnras/stad1258`](http://doi.org/10.1093/mnras/stad1258)

(ref: at2020opy) Goodwin, A. J., Miller-Jones, J. C. A., van Velzen, S., et al. 2023b, MNRAS, 518, 847, doi: [`10.1093/mnras/stac3127`](http://doi.org/10.1093/mnras/stac3127)

(ref: Govreen-Segal_2021) Govreen-Segal, T., Nakar, E., & Levinson, A. 2021, ApJ, 907, 113, doi: [`10.3847/1538-4357/abd180`](http://doi.org/10.3847/1538-4357/abd180)

(ref: Granot_2002) Granot, J., & Sari, R. 2002, The Astrophysical Journal, 568, 820, doi: [`10.1086/338966`](http://doi.org/10.1086/338966)

(ref: guolo_23) Guolo, M., Gezari, S., Yao, Y., et al. 2023, arXiv e-prints, arXiv:2308.13019, doi: [`10.48550/arXiv.2308.13019`](http://doi.org/10.48550/arXiv.2308.13019)

(ref: hills_1975) Hills, J. G. 1975, Nature, 254, 295, doi: [`10.1038/254295a0`](http://doi.org/10.1038/254295a0)

(ref: holoien_2019) Holoien, T. W. S., Vallely, P. J., Auchettl, K., et al. 2019, ApJ, 883, 111, doi: [`10.3847/1538-4357/ab3c66`](http://doi.org/10.3847/1538-4357/ab3c66)

(ref: horesh_15oi) Horesh, A., Cenko, S. B., & Arcavi, I. 2021a, Nature Astronomy, 5, 491, doi: [`10.1038/s41550-021-01300-8`](http://doi.org/10.1038/s41550-021-01300-8)

(ref: iPTF16fnl) Horesh, A., Sfaradi, I., Fender, R., et al. 2021b, ApJL, 920, L5, doi: [`10.3847/2041-8213/ac25fe`](http://doi.org/10.3847/2041-8213/ac25fe)

(ref: Kalberla05) Kalberla, P. M. W., Burton, W. B., Hartmann, D., et al. 2005, A&A, 440, 775, doi: [`10.1051/0004-6361:20041864`](http://doi.org/10.1051/0004-6361:20041864)

(ref: Kochanek_2017) Kochanek, C. S., Shappee, B. J., Stanek, K. Z., et al. 2017, PASP, 129, 104502, doi: [`10.1088/1538-3873/aa80d9`](http://doi.org/10.1088/1538-3873/aa80d9)

(ref: krolik_2016) Krolik, J., Piran, T., Svirski, G., & Cheng, R. M. 2016, ApJ, 827, 127, doi: [`10.3847/0004-637X/827/2/127`](http://doi.org/10.3847/0004-637X/827/2/127)

(ref: IGR_Lei) Lei, W.-H., Yuan, Q., Zhang, B., & Wang, D. 2016, ApJ, 816, 20, doi: [`10.3847/0004-637X/816/1/20`](http://doi.org/10.3847/0004-637X/816/1/20)

(ref: li_2018) Li, B., Li, L.-B., Huang, Y.-F., et al. 2018, ApJL, 859, L3, doi: [`10.3847/2041-8213/aac2c5`](http://doi.org/10.3847/2041-8213/aac2c5)

(ref: liu_22) Liu, X.-L., Dou, L.-M., Chen, J.-H., & Shen, R.-F. 2022, ApJ, 925, 67, doi: [`10.3847/1538-4357/ac33a9`](http://doi.org/10.3847/1538-4357/ac33a9)

(ref: Mangano_2016) Mangano, V., Burrows, D. N., Sbarufatti, B., & Cannizzo, J. K. 2016, ApJ, 817, 103, doi: [`10.3847/0004-637X/817/2/103`](http://doi.org/10.3847/0004-637X/817/2/103)

(ref: Margalit_2021) Margalit, B., & Quataert, E. 2021, ApJL, 923, L14, doi: [`10.3847/2041-8213/ac3d97`](http://doi.org/10.3847/2041-8213/ac3d97)

(ref: Margutti13) Margutti, R., Zaninoni, E., Bernardini, M. G., et al. 2013, MNRAS, 428, 729, doi: [`10.1093/mnras/sts066`](http://doi.org/10.1093/mnras/sts066)

(ref: AT2022cmc_matsumoto_metzger2023) Matsumoto, T., & Metzger, B. D. 2023, MNRAS, 522, 4028, doi: [`10.1093/mnras/stad1182`](http://doi.org/10.1093/mnras/stad1182)

(ref: matsumoto) Matsumoto, T., & Piran, T. 2023, MNRAS, 522, 4565, doi: [`10.1093/mnras/stad1269`](http://doi.org/10.1093/mnras/stad1269)

(ref: matsumoto_19dsg) Matsumoto, T., Piran, T., & Krolik, J. H. 2022, MNRAS, 511, 5085, doi: [`10.1093/mnras/stac382`](http://doi.org/10.1093/mnras/stac382)

(ref: ARP_2018) Mattila, S., Pérez-Torres, M., Efstathiou, A., et al. 2018, Science, 361, 482, doi: [`10.1126/science.aao4669`](http://doi.org/10.1126/science.aao4669)

(ref: Metzger_2022) Metzger, B. D. 2022, ApJL, 937, L12, doi: [`10.3847/2041-8213/ac90ba`](http://doi.org/10.3847/2041-8213/ac90ba)

(ref: Metzger_2012) Metzger, B. D., Giannios, D., & Mimica, P. 2012, MNRAS, 420, 3528, doi: [`10.1111/j.1365-2966.2011.20273.x`](http://doi.org/10.1111/j.1365-2966.2011.20273.x)

(ref: Panaitescu_2002) Panaitescu, A., & Kumar, P. 2002, ApJ, 571, 779, doi: [`10.1086/340094`](http://doi.org/10.1086/340094)

(ref: Parkinson_2022) Parkinson, E. J., Knigge, C., Matthews, J. H., et al. 2022, MNRAS, 510, 5426, doi: [`10.1093/mnras/stac027`](http://doi.org/10.1093/mnras/stac027)

(ref: Pasham_2018) Pasham, D. R., & van Velzen, S. 2018, ApJ, 856, 1, doi: [`10.3847/1538-4357/aab361`](http://doi.org/10.3847/1538-4357/aab361)

(ref: AT2022cmc_pasham_2023) Pasham, D. R., Lucchini, M., Laskar, T., et al. 2023, Nature Astronomy, 7, 88, doi: [`10.1038/s41550-022-01820-x`](http://doi.org/10.1038/s41550-022-01820-x)

(ref: perlman_2017) Perlman, E. S., Meyer, E. T., Wang, Q. D., et al. 2017, ApJ, 842, 126, doi: [`10.3847/1538-4357/aa71b1`](http://doi.org/10.3847/1538-4357/aa71b1)

(ref: perlman_2022) —. 2022, ApJ, 925, 143, doi: [`10.3847/1538-4357/ac3bba`](http://doi.org/10.3847/1538-4357/ac3bba)

(ref: Pushkarev_2017) Pushkarev, A. B., Kovalev, Y. Y., Lister, M. L., & Savolainen, T. 2017, MNRAS, 468, 4992, doi: [`10.1093/mnras/stx854`](http://doi.org/10.1093/mnras/stx854)

(ref: Rees1998) Rees, M. J. 1988, Nature, 333, 523, doi: [`10.1038/333523a0`](http://doi.org/10.1038/333523a0)

(ref: Riccio_2023) Riccio, G., Yang, G., Małek, K., et al. 2023, A&A, 678, A164, doi: [`10.1051/0004-6361/202346857`](http://doi.org/10.1051/0004-6361/202346857)

(ref: Ricker_2015) Ricker, G. R., Winn, J. N., Vanderspek, R., et al. 2015, Journal of Astronomical Telescopes, Instruments, and Systems, 1, 014003, doi: [`10.1117/1.JATIS.1.1.014003`](http://doi.org/10.1117/1.JATIS.1.1.014003)

(ref: Rouco_2023) Rouco Escorial, A., Fong, W., Berger, E., et al. 2023, ApJ, 959, 13, doi: [`10.3847/1538-4357/acf830`](http://doi.org/10.3847/1538-4357/acf830)

(ref: Sari_1998) Sari, R., Piran, T., & Narayan, R. 1998, ApJL, 497, L17, doi: [`10.1086/311269`](http://doi.org/10.1086/311269)

(ref: Miriad) Sault, R. J., Teuben, P. J., & Wright, M. C. H. 1995, in Astronomical Society of the Pacific Conference Series, Vol. 77, Astronomical Data Analysis Software and Systems IV, ed. R. A. Shaw, H. E. Payne, & J. J. E. Hayes, 433, doi: [`10.48550/arXiv.astro-ph/0612759`](http://doi.org/10.48550/arXiv.astro-ph/0612759)

(ref: sfaradi_19azh) Sfaradi, I., Horesh, A., Fender, R., et al. 2022, ApJ, 933, 176, doi: [`10.3847/1538-4357/ac74bc`](http://doi.org/10.3847/1538-4357/ac74bc)

(ref: Sfaradi_2024) Sfaradi, I., Beniamini, P., Horesh, A., et al. 2024, MNRAS, 527, 7672, doi: [`10.1093/mnras/stad3717`](http://doi.org/10.1093/mnras/stad3717)

(ref: Shappee) Shappee, B. J., Prieto, J. L., Grupe, D., et al. 2014, ApJ, 788, 48, doi: [`10.1088/0004-637X/788/1/48`](http://doi.org/10.1088/0004-637X/788/1/48)

(ref: Strubbe) Strubbe, L. E., & Quataert, E. 2009, MNRAS, 400, 2070, doi: [`10.1111/j.1365-2966.2009.15599.x`](http://doi.org/10.1111/j.1365-2966.2009.15599.x)

(ref: Tchekhovskoy) Tchekhovskoy, A., Metzger, B. D., Giannios, D., & Kelley, L. Z. 2014, MNRAS, 437, 2744, doi: [`10.1093/mnras/stt2085`](http://doi.org/10.1093/mnras/stt2085)

(ref: Thomsen_2022) Thomsen, L. L., Kwan, T. M., Dai, L., et al. 2022, ApJL, 937, L28, doi: [`10.3847/2041-8213/ac911f`](http://doi.org/10.3847/2041-8213/ac911f)

(ref: van_Velzen_2023) van Velzen, S., Frail, D. A., Körding, E., & Falcke, H. 2013, A&A, 552, A5, doi: [`10.1051/0004-6361/201220426`](http://doi.org/10.1051/0004-6361/201220426)

(ref: peeling) Williams, P. K. G., Allers, K. N., Biller, B. A., & Vos, J. 2019, Research Notes of the American Astronomical Society, 3, 110, doi: [`10.3847/2515-5172/ab35d5`](http://doi.org/10.3847/2515-5172/ab35d5)

(ref: Yao_2024) Yao, Y., Lu, W., Harrison, F., et al. 2024, ApJ, 965, 39, doi: [`10.3847/1538-4357/ad2b6b`](http://doi.org/10.3847/1538-4357/ad2b6b)

(ref: Zauderer_2011) Zauderer, B. A., Berger, E., Soderberg, A. M., et al. 2011, Nature, 476, 425, doi: [`10.1038/nature10366`](http://doi.org/10.1038/nature10366)

[^1]:

[^2]: <https://www.swift.ac.uk/user_objects/>

[^3]: We note that while the radio outflow was not necessarily launched exactly at $\delta t =0$ days, the launch date must be before the date of our first ALMA detection at $\delta t\approx40$ days. This allowed range accounts for a very small fractional difference in time when considering the later epochs, so this assumption has minimal impact on our results.

[^4]: We note that this smoothing term is much steeper than the suggested value in (cite: Granot_2002), which was derived in the context of GRB afterglows. Instead, we adopt the smoothing parameter used in (cite: at2019dsg) for the TDE AT2019dsg, which was motivated by the observed sharpness of the break.

</paper>

Write the methods card for this paper.