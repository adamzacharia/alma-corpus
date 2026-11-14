# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...985..124L\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...985..124L",
 "title": "The Nature of Optical Afterglows without Gamma-Ray Bursts: Identification of AT2023lcr and Multiwavelength Modeling",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Li, Maggie L.",
 "n_authors": 32,
 "arxiv_id": "2411.07973",
 "doi": "10.3847/1538-4357/adc800",
 "alma_projects_linked_by_archive": [
  "2022.A.00025.T"
 ]
}
```

Paper text:
<paper>
# The Nature of Optical Afterglows Without Gamma-ray Bursts:\
Identification of AT2023lcr and Multiwavelength Modeling

## Abstract

In the past few years, the improved sensitivity and cadence of wide-field optical surveys have enabled the discovery of several afterglows without associated detected gamma-ray bursts (GRBs). We present the identification, observations, and multi-wavelength modeling of a recent such afterglow (AT 2023lcr), and model three literature events (AT 2020blt, AT 2021any, and AT 2021lfa) in a consistent fashion. For each event, we consider the following possibilities as to why a GRB was not observed: 1) the jet was off-axis; 2) the jet had a low initial Lorentz factor; and 3) the afterglow was the result of an on-axis classical GRB (on-axis jet with physical parameters typical of the GRB population), but the emission was undetected by gamma-ray satellites. We estimate all physical parameters using `afterglowpy` and Markov Chain Monte Carlo methods from `emcee`. We find that AT 2023lcr, AT 2020blt, and AT 2021any are consistent with on-axis classical GRBs, and AT 2021lfa is consistent with both on-axis low Lorentz factor ($\Gamma_0 \approx 5 - 13$) and off-axis ($\theta_\mathrm{obs}=2\theta_\mathrm{jet}$) high Lorentz factor ($\Gamma_0 \approx 100$) jets.

# Introduction

In the internal-external shocks model for long-duration gamma-ray bursts (LGRBs; (cite: Piran_2005; Meszaros_2006; Kumar_2015)), the core of a massive star collapses and forms a neutron star or black hole, which launches an ultra-relativistic collimated outflow, or “jet". The jet’s internal collisions produce an initial burst of gamma-rays, called the “prompt emission", followed by the jet’s external collision with the ambient medium, producing an “afterglow" across the electromagnetic spectrum.

There are several reasons why we should be able to detect afterglows without associated detected GRBs. First, the Earth might not be within the jet’s opening angle (typically $\theta_c = 5-10^\circ$; (cite: Ghirlanda_2018)), which is collimated and relativistically beamed (initial $\theta_c = \Gamma_0^{-1}$) (cite: Totani_2002). In this “off-axis" GRB scenario, we will miss the prompt emission but still be able to observe an afterglow when the jet decelerates and spreads (cite: Rhoads1997). Second, a “dirty fireball" can occur if the outflow is less relativistic than that of a typical GRB ($\Gamma_0 \lesssim 100$) due to a baryon-loaded jet (cite: Dermer_1999; Huang_2002; Rhoads_2003). In this case, the jet will be below the pair-production threshold for gamma-rays (i.e. the compactness problem; (cite: Ruderman_1975)), so we would not be able to observe a GRB. Still, we might observe a less energetic prompt emission, such as an X-ray flash (cite: Dermer_1999; Heise_2001; Zhang_2004; Sakamoto_2005; Soderberg_2007). Third, the source could be an on-axis classical GRB whose prompt emission was undetected by gamma-ray satellites, possibly due to the occultation of the Earth or a weak prompt emission that failed to meet the triggering thresholds of gamma-ray satellites.

In recent years, high-cadence optical surveys have enabled the discovery of ten likely afterglows without associated detected GRBs, summarized in Table [1](#tab:orphan-summary). Prior to the Zwicky Transient Facility (ZTF; (cite: Graham2019; Bellm2019_ztf; Bellm2019_surveys; Dekany2020; Masci2019)), only one such event, PTF 11agg (cite: Cenko_2013), was discovered, found by the Palomar Transient Factory (cite: Law_2009). Since ZTF’s first light, nine other events have been confirmed as afterglows without associated detected GRBs, largely thanks to ZTF’s high cadence over a wide field-of-view, enabling the rapid identification of fast transients. Still, no convincing dirty fireballs or off-axis LGRB candidates have been discovered.

In this paper, we present the identification, follow-up, and multi-wavelength modeling of one of the most recent such events, AT 2023lcr. We only consider the afterglow light curve, although an associated Ic-BL supernova was identified at a later time (cite: lcr-supernova-photometry). As shown in Table [1](#tab:orphan-summary), AT 2023lcr is one of six afterglows discovered in optical-survey data with no detected GRB but with a measured redshift. To put our AT 2023lcr results into context, we also present multi-wavelength modeling of three afterglows in Table [1](#tab:orphan-summary): AT 2020blt, AT 2021any, and AT 2021lfa. For AT 2019pim, we refer the reader to (cite: Perley_2024), who used a similar approach to this work; for AT 2023sva, we refer the reader to (cite: 2023sva). All afterglows are modeled using Markov Chain Monte Carlo (MCMC) methods in `emcee` (version 3.1.4; (cite: Foreman_Mackey_2013)) and afterglow models from `afterglowpy` (version 0.7.3; (cite: Ryan_2020)).

| Afterglow | Redshift | Ref. | Proposed Models |
|:---|:--:|:---|:---|
| PTF 11agg | \- | \[1\] | on-axis, untriggered GRB \[1\]; dirty fireball \[1\]; neutron star merger \[2, 3\] |
| AT 2019pim | 1.2596 | \[4\] | on-axis jet with $\Gamma_0 \approx 30-50$; off-axis GRB with $\Gamma_0 \approx 100$ \[4\] |
| AT 2020blt | 2.9 | \[5\] | on-axis GRB with $\eta_\gamma < 0.3 - 14.5\%$ \[6\]; on-axis classical GRB \[0\] |
| AT 2021any | 2.5131 | \[7\] | on-axis classical GRB \[8; 0\]; on-axis moderately dirty fireball \[9; 0\] |
| AT 2021lfa | 1.063 | \[7, 10\] | on-axis jet with $\Gamma_0 \sim 20$ \[10, 11, 0\]; off-axis GRB with $\Gamma_0 \approx 100$ \[0\] |
| AT 2023avj | \- | \[12, 13\] | \- |
| AT 2023azs | \- | \[14, 15\] | \- |
| AT 2023jxk | \- | \[16, 17\] | \- |
| AT 2023lcr | 1.0272 | \[0\] | on-axis GRB with $\eta_\gamma < 0.95\%$ \[0\] |
| AT 2023sva | 2.281 | \[18, 19, 20, 21, 22\] | slightly off-axis structured jet \[22\] |

: Summary of afterglows discovered without associated detected GRBs.

Table notes: \[0\] this work, \[1\] (cite: Cenko_2013), \[2\] (cite: Wang_2013), \[3\] (cite: Wu_2013), \[4\] (cite: Perley_2024), \[5\] (cite: Ho_2020), \[6\] (cite: Sarin_2022), \[7\] (cite: Ho_2022), \[8\] (cite: Gupta_2022), \[9\] (cite: Xu_2023), \[10\] (cite: Lipunov_2022), \[11\] (cite: Ye_2024), \[12\] (cite: Wang2023_AT2023avj), \[13\] (cite: Ho2023_AT2023avj), \[14\] (cite: Andreoni2023_AT2023azs), \[15\] (cite: Perley2023_AT2023azs), \[16\] (cite: Vail2023_AT2023jxk), \[17\] (cite: Sfaradi2023_AT2023jxk), \[18\] (cite: Vail2023_AT2023sva), \[19\] (cite: deUgartePostigo2023_AT2023sva), \[20\] (cite: Rhodes2023_AT2023sva), \[21\] (cite: Roberts2023_AT2023sva), \[22\] (cite: 2023sva).

For each object, we consider the following explanations for why their prompt gamma-ray emission was missed: 1) the jet was off-axis; 2) the jet had a low Lorentz factor ($\Gamma_0 \lesssim 100$); and 3) the afterglow was the result of an on-axis classical GRB but the GRB was undetected by high-energy satellites. Because of imprecise constraints on the burst time, the possibility of an on-axis classical GRB cannot be ruled out for any of the afterglows on the basis of gamma-ray limits alone (cite: Ho_2020; Ho_2022).

AT 2020blt was previously modeled in (cite: Sarin_2022) (hereafter S22); AT 2021any was previously modeled in (cite: Gupta_2022) (G22) and (cite: Xu_2023) (X23); AT 2021lfa was previously modeled in (cite: Ye_2024) (Y24). In this work[^1], we explore additional jet structures, modeling configurations, and constraints on afterglow behavior, discussing comparisons between the mentioned works and this work in Section [5](#sec:results).

This paper is organized as follows: we present observations of AT 2023lcr in Section [2](#sec:at2023lcr). We describe observational features of AT 2023lcr in Section [3](#sec:observational-features). We describe our fitting framework in Section [4](#sec:method). In Section [5](#sec:results), we present the results of our fitting, discuss preferred models and physical interpretations, and compare our results to past works. Finally, we summarize and discuss implications and future work in Section [6](#sec:conclusion).

# AT2023lcr Observations

## Optical Photometry

AT 2023lcr was initially reported (cite: Tonry2023; Fulton2023) to the Transient Name Server (TNS) by the ATLAS survey (cite: Tonry2018) as ATLAS23msn. AT 2023lcr was also detected as part of the ZTF high-cadence partnership survey (cite: Bellm2019_surveys), with the first detection at[^2] 06:36:27 on 2023 June 18 (internal name ZTF23aaoohpy) at a position $\alpha= 16$:31:37.416 and $\delta= +$26:21:58.31 (J2000) and a Galactic latitude $b=41.25$ deg (cite: lcr-swain). AT 2023lcr was flagged as a transient of interest due to its rapid rise ($>1.2\,$mag d$^{-1}$ in $r$ band[^3]), red colors ($g-r=0.29\pm0.08\,$mag, corrected for Milky Way extinction with $E(B-V)=A_V/R_V=0.05$, assuming $R_v = 3.1$; (cite: Schlegel_1998)), and lack of a bright host-galaxy counterpart.

The red colors exhibited by AT 2023lcr were consistent with the synchrotron emission expected from an afterglow-like transient, which has been shown to be a useful discriminant from stellar flares in the Milky Way (cite: Ho_2020). Liverpool Telescope (LT; (cite: Steele2004)) IO:O imaging observations were attempted to confirm the synchrotron-like colors and check for rapid fading (as expected for an afterglow) but the telescope was offline due to a power supply problem. Confirmation of the red colors and rapid fading was obtained by ZTF through routine survey operations the following night: the transient faded by approximately one magnitude in both $g$- and $r$-band, and this behavior was flagged (cite: Swain2023) by the ZTFReST pipeline (cite: Andreoni2021).

The Gravitational-wave Optical Transient Observer (GOTO; (cite: Steeghs2022)) reported (cite: Gompertz2023) an early detection of AT 2023lcr at 01:27:41 on 2023 June 18 (60113.06089 MJD), five hours before the first ZTF detection, at $18.77\pm0.06$ in the L-band (400–700 nm). It was not detected in the previous GOTO epoch at 23:50:30 on 2023 June 17 with a 5-$\sigma$ limiting magnitude of $L>20.3\,$mag, establishing a short window for the onset time of 1 hour and 38 minutes.

Optical photometric follow-up observations were obtained during the week following the initial detection. Table [11](#tab:optical-photometry) in Appendix [11](#tab:optical-photometry) presents the LT, GROWTH-India Telescope (GIT), and Himalayan Chandra Telescope (HCT) photometry. To correct for Milky Way extinction we use $A_V=0.128$ mag (cite: Schlafly2011). The full optical light curve of AT 2023lcr is shown in Figure [1](#fig:lcr-indices). Follow-up observations were coordinated using the SkyPortal platform (cite: vanderWalt2019; SkyPortal).

Later, on 2023 August 12, a James Webb Space Telescope/NIRSPec spectrum was taken (cite: lcr-supernova-spectrum), which identified a Ic-BL supernova (SN) counterpart for AT 2023lcr. In this work, we only consider the afterglow. Since the source is at a redshfit $z=1.0272$, we assume that the contribution of the SN is negligible in our observations, supported by the lack of observed flattening in the optical light curve.

## Optical Spectroscopy

We triggered observations[^4] using the Low Resolution Imaging Spectrometer (LRIS; (cite: Oke1995)) on the Keck I 10-m telescope. Observations started at 07:22 on 2023 June 20 ($\Delta t = 2.3$ d from the last GOTO non-detection[^5][^6]), with exposure times of $2\times 1200$ s and $3\times 800$ s in the blue and red arms, respectively. Observations employed the 600/4000 blue grism and 600/7500 red grating, providing continuous wavelength coverage from 3140–8784 Å. Data were reduced using LPipe (cite: Perley2019lpipe). The spectrum (Figure [2](#fig:spec)) shows a simple continuum, well fit by a power law of $f_\lambda \propto \lambda^{-1}$. The signal-to-noise ratio is about 20 per resolution element (although lower blueward of 4000 Å). We detect clear (but weak) absorption lines at observer-frame wavelengths of 5688 and 5683 Å which we attribute to redshifted Mg II $\lambda\lambda$2796, 2803 at $z=1.0272$. Weak absorption from Fe II $\lambda$2383 and Fe II $\lambda$2600 at a consistent redshift is also securely detected, and Fe II $\lambda$2344 is marginally detected. We also detect a possible intervening Mg II absorber at $z=0.7795$. No other lines are apparent in the spectrum. Based on this information, we adopt $z=1.0272$ as the redshift of AT 2023lcr, and the corresponding luminosity distance[^7] as $D_L=7.0196\,$Gpc. While strictly this redshift is only a lower limit, the absence of any higher-redshift absorption features suggests that a higher-redshift origin is unlikely. The lack of Lyman-$\alpha$ absorption over the spectral range imposes a redshift upper limit of $z<1.6$.

## X-rays

![](lcr_spec.png)

| Instrument | Start Date (MJD) | Exposure Time (ks) | Flux ($10^{-13}$ erg s$^{-1}$ cm$^{-2}$) | $f_\nu$ (1 keV; $10^{-2}\,\mu$Jy) |
|:---|:--:|:--:|:--:|:--:|
| Swift/XRT | 60115.58090 | 3.00 | $3.70^{+0.88}_{-0.88}$ | $4.40^{+1.05}_{-1.05}$ |
| Swift/XRT | 60117.43457 | 3.30 | $1.56^{+0.94}_{-0.70}$ | $1.85^{+1.12}_{-0.83}$ |
| Swift/XRT | 60124.71261 | 9.10 | $0.57^{+0.25}_{-0.21}$ | $0.68^{+0.30}_{-0.24}$ |
| Chandra/ACIS | 60128.27391 | 18.83 | $0.28^{+0.10}_{-0.05}$ | $0.33^{+0.11}_{-0.06}$ |

We triggered observations of AT 2023lcr with the X-ray Telescope (XRT; (cite: Burrows2005)) on board the *Neil Gehrels Swift Observatory* through SkyPortal (cite: vanderWalt2019; SkyPortal). In total six epochs of observations were obtained under target-of-opportunity programs[^8], from 2023 June 20 to 2023 July 06 ($\Delta t=2$–18 d). The source was detected in three of those epochs, presented in Table [\[tab:xray\]](#tab:xray). Fitting the detections in the three epochs simultaneously using the online Swift tool (cite: Evans2007; Evans2009), with a Galactic hydrogen column density of $N_H=4.12\times10^{20}\,$cm$^{-2}$, we find a best-fit photon index of $\Gamma=1.8^{+0.8}_{-0.5}$ (90% confidence interval). To convert from count rate to flux density we take $\Gamma=2$, giving a counts to flux conversion factor (unabsorbed) of $3.93\times10^{-11}$ erg cm$^{-2}$ ct$^{-1}$. This photon index corresponds to a spectral index of $\beta_X=1-\Gamma=-1$ where $f_\nu \propto \nu^{\beta_X}$.

AT 2023lcr was also observed by the Advanced CCD imaging spectrometer (ACIS; (cite: Garmire2003)) on board the Chandra X-Ray Observatory (Chandra) [^9] under a Director’s Discretionary Time proposal[^10], four days after the final *Swift*/XRT detection. We reduced the data using the Chandra Interactive Analysis of Observations (CIAO; (cite: Fruscione2006)) software package (v4.15). Counts were extracted from AT 2023lcr using a circle with radius $2''$, and background counts were measured in source-free regions near AT 2023lcr. We used `specextract` to bin the spectrum (with 5 counts per bin). The routine `sherpa` (cite: sherpa1; sherpa2) was used to fit the spectrum in the range 0.5–6 keV, with the background subtracted, using a model with photoelectric absorption and a single-component power law (`xsphabs.abs1 `$\times$` powlaw1d.p1`). We set the Galactic hydrogen column density to be the same as for the *Swift* observations. The best-fit power law index was $\Gamma=1.16^{+0.95}_{-0.95}$ (68% confidence), consistent with the value from *Swift* but with much larger uncertainties, so for consistency we also adopt $\Gamma=2$. The flux reported in Table [\[tab:xray\]](#tab:xray) has been multiplied by a factor of 1.77 to correct from the 0.5–6 keV band to the 0.3–10 keV band. In Table [\[tab:xray\]](#tab:xray), we also present the spectral flux density at 1 keV assuming a spectral index of $f_\nu \propto \nu^{-1}$.

## Radio

![](lcr_radio_sed_no_fits.png)

We obtained 11 epochs of observations using the Karl G. Jansky Very Large Array (VLA[^11]; (cite: Perley2011).), spanning 2023 June 21 to 2023 September 29 ($\Delta t = 3$–103 d) in the L, S, C, X, Ku, and Ka-bands (1–40 GHz). The primary flux calibrator used was 3C286. Data were calibrated and imaged using standard procedures in the Astronomical Image Processing System (AIPS). Images were typically made in separate windows with a bandwidth of 1 GHz or 2 GHz, with adjustments made at lower frequencies due to radio frequency interference excision. Flux-density measurements were performed using `jmfit`. The second Ka-band epoch was hampered by poor weather conditions, resulting in poor phase stability (with insufficient signal to noise for self-calibration); this measurement should be regarded as a lower limit. Epoch 9 on 2023 August 19 ($\Delta t = 62$ d) was also hampered by poor phase stability. For Epochs 4–8 ($\Delta t = 9$–31 d) we obtained C-band observations at the beginning and end of the block in order to search for scintillation.

We obtained observations on epochs 2023 June 29 ($\Delta t = 11$ d) and 2023 July 04 ($\Delta t = 16$ d) using the Atacama Large Millimeter/sub-millimeter Array (ALMA) under Director’s Discretionary Time[^12]. Weather conditions in both epochs were excellent. Data were calibrated and imaged using the automated CASA-based pipeline (cite: CASA2022). Both observations were in Band 3 (100 GHz) and yielded a detection with a centroid position of $\alpha$ = 16:31:37.419, and $\delta$ = +26:21:58.27 (J2000), consistent with the optical position. The peak flux density of the source was $140\pm14\,\mu$Jy in the first epoch and $94\pm11\,\mu$Jy in the second epoch.

We obtained one epoch of observations with the Submillimeter Array (SMA[^13]) on 2023 June 24 ($\Delta t = 6$ d). Observations were conducted between 03:31 and 14:43 UT, using 7 antennas, with an local oscillator frequency of 225.5 GHz. Weather conditions were favorable (median $\tau_{225\,\mathrm{GHz}} = 0.070$), with good phase stability for all but the first hour of observations. A total of 6.75 hours was spent on source, with 1613+342 and 3C345 used as gain calibrators, and Ceres as the flux calibrator. There was no detection.

We obtained Giant Metrewave Radio Telescope (GMRT) observations from 2023 August 9.63 UT to 2023 August 22.63 UT through a DDT proposal[^14]. The observations were carried out in three frequency bands: band-5 (1000–1460 MHz), band-4 (550–850 MHz), and band-3 (250–500 MHz). The data were collected in standard continuum mode with a time integration of 10 seconds. We used a processing bandwidth of 400 MHz in band-5 and 200 MHz in bands-3 and 4, both split into 2048 channels. 3C286 was used as the flux density and bandpass calibrator while J1609+266 was used as the phase calibrator. Emission was detected at 1.37 GHz, but not at 0.75 or 0.44 GHz.

All radio flux density values are provided in Table [12](#tab:radio) in Appendix [9](#sec:radio-data). The radio light curves are shown in Figure [1](#fig:lcr-indices), and the evolution of the radio spectral energy distribution is shown in Figure [3](#fig:at2023lcr-radio-sed).

## Search for Gamma-ray Emission

Throughout the 1 hour and 38 minutes between the last GOTO non-detection and the first GOTO detection, the KONUS instrument on the *Wind* spacecraft (cite: Aptekar1995) was observing the entire sky, with no GRB detection. For a typical LGRB spectrum, the 90%-confidence upper limit on the 20–1500 keV peak flux was reported to be $1.8\times10^{-7}\,$erg cm$^{-2}\,$s$^{-1}$ on a 2.944 s scale (cite: Ridnaia2023). At the redshift of AT 2023lcr ($z=1.0272$), this corresponds to an upper limit on the isotropic-equivalent $\gamma$-ray luminosity of $L_{\gamma,\mathrm{iso}}<5.2\times10^{50}\,$erg s$^{-1}$. Assuming a similar scaling over longer time intervals (an observed duration of 40 s as in (cite: Perley_2024)) gives a limit on the isotropic-equivalent energy of $E_{\gamma,\mathrm{iso}}<2.1\times10^{52}\,$erg. We perform the same computation at the redshift upper limit of AT 2023lcr ($z=1.6$), obtaining $L_{\gamma,\mathrm{iso}}< 1.2\times10^{51}\,$erg s$^{-1}$ and $E_{\gamma,\mathrm{iso}}<4.9\times10^{52}\,$erg.

The position was visible to the *Fermi* Gamma-ray Burst Monitor (GBM; (cite: Meegan2009)) for one hour, from 00:23:05 to 01:22:27 on 2023 June 18 with no South Atlantic Anomaly interruptions. A subthreshold search yielded no detections, with a mean upper limit on the peak flux (for the same burst duration) of $8.2\times10^{-8}$ erg cm$^{-2}\,$s$^{-1}$. This corresponds to $L_{\gamma,\mathrm{iso}}<4.8\times10^{50}\,$erg s$^{-1}$, or $E_{\gamma,\mathrm{iso}}<9.5\times10^{51}\,$erg. The position was visible to the *Swift* Burst Alert Telescope (BAT; (cite: Barthelmy2005)) for 40 minutes, from approximately 00:38 to 01:20.

Given the incomplete coverage of both GBM and Swift BAT, we adopt the more conservative limit from KONUS in what follows.

# Observational Features of AT2023lcr

We find preliminary radio, optical, and X-ray temporal indices for AT 2023lcr. We also compare AT 2023lcr’s observational features to those of other $z \approx 1$ afterglows without associated detected GRBs, namely AT 2019pim at $z=1.2596$ (cite: Perley_2024) and AT 2021lfa at $z=1.0624$ (cite: Ho_2022).

## Optical

We fit the multi-band optical light curve of AT2023lcr assuming a magnitude offset between each pair of bands that is constant over time, rather than a single overall spectral index. We treat the GOTO $L$-band point as the average of the $r$- and $g$-band fluxes at that time. We fit the $g$-, $r$-, $i$-, and $z$-band extinction-corrected light curves using the following smoothed broken power law function (cite: Beuermann1999; Zeh2006):

$$\begin{equation}
\label{eq:beuermann}
    m(t) = m_c+\frac{2.5}{n}\log_{10}\left[ 
    \frac{(t-t_0)}{t_b-t_0}^{\alpha_1 n} +
    \frac{(t-t_0)}{t_b-t_0}^{\alpha_2 n} \right]
\end{equation}$$

where $m(t)$ is the apparent magnitude as a function of time, $n$ parameterizes the smoothness of the break ($n=\infty$ is a sharp break), $\alpha_1$ and $\alpha_2$ are the pre- and post-break temporal indices respectively, $t_0$ is the time of the explosion in days, $t_b$ is the time of the break in days, and $m_c$ is the magnitude at the time of the break assuming $n=\infty$. We assume no contribution from the host galaxy or the underlying SN. A typical GRB-SN would be both too faint for our observations and redshifted to the NIR. These assumptions are supported by the lack of observed flattening in the optical light curve. We fixed $n=2$ and allowed $t_0$ to vary between the time of the last GOTO non-detection and the first GOTO detection.

From a Markov Chain Monte Carlo (MCMC) fit, we find (see left panel of Figure [1](#fig:lcr-indices)), a break time $t_b=0.73^{+0.06}_{-0.06}$ d in the observer frame (68% confidence). The best-fit broken power-law temporal indices are $\alpha_1=0.23^{+0.04}_{-0.03}$ and $\alpha_2=1.39^{+0.05}_{-0.04}$. We find a best-fit $t_0$ that is $52^{+16}_{-18}$ min after the GOTO non-detection (and 45 min before the first GOTO detection), at MJD 60113.02965.

The optical light curve of AT 2023lcr is very similar to the early ($\Delta t<10\,$d) optical light curve of AT 2019pim, although the light curve of AT 2019pim was better resolved due to TESS coverage. From (cite: Ho_2022), the optical light curve of AT 2021lfa had a much steeper temporal decay index than AT 2023lcr, $t^{-2.5}$ rather than $t^{-1}$, although we caution that the decay index is highly sensitive to the explosion time, which for AT 2021lfa, is quite uncertain (1.79 d between the first detection and last non-detection). Using the burst time estimate obtained from results that follow in Section [5.1](#sec:lorentz-factor-constraints), AT 2021lfa returns a more similar temporal decay index $t^{-1.4}$.

Finally, to measure the spectral index across the optical bands, we use the $ugriz$ photometry from LT in the MJD range 60114.92765–60114.95733 and apply a correction for Milky Way extinction. We find a best-fit spectral index of $\beta_{\mathrm{opt}}=1.20^{+0.16}_{-0.16}$ (68% confidence) where $f_\nu\propto \nu^{-\beta_\mathrm{opt}}$, consistent with the spectral index measured from the optical spectrum (Figure [2](#fig:spec)). The spectral index from optical to X-ray bands, as well as within the X-ray band itself (Section [2.3](#sec:obs-xrays)), is also close to $f_\nu \propto \nu^{-1}$—this, together with the fairly smooth continuum observed in the spectrum, leads us to conclude that the impact of host-galaxy extinction is negligible.

## X-rays

We fit a single power law to the X-ray light curve of AT 2023lcr at 1 keV, and find a best-fit power law index $\alpha_X=1.47^{+0.17}_{-0.16}$ (68% confidence) where $f_\nu \propto t^{-\alpha_X}$, consistent with the slope of the optical light curve in the same time range. Given the similar optical and X-ray spectral indices ($f_\nu \propto \nu^{-1}$), we assume no host galaxy extinction. There was only one X-ray detection of AT 2021lfa, at a similar flux to AT 2023lcr. The X-ray light curves of AT 2023lcr and AT 2019pim have similar temporal decay indices, but the X-ray flux density of AT 2019pim was an order of magnitude fainter.

## Radio

![](lfa_radio_index.pdf)

The radio light curves of AT 2019pim, AT 2021lfa, and AT 2023lcr reach a similar peak flux density and have roughly a single peak, rising $\sim t^{1}$ then decaying $\sim t^{-1.5}$, although AT 2021lfa’s radio temporal indices are highly impacted by interstellar scintilation (see Figure [4](#fig:lfa-indices) for the radio light curve fit of AT 2021lfa; see Figure 7 in (cite: Perley_2024) for the radio light curve fit of AT 2019pim). However, the peak for AT 2023lcr is at $t<10$ d while the peak for AT 2019pim and AT 2021lfa is at tens of days. Additionally, AT 2023lcr, AT 2021lfa, and AT 2019pim all exhibit significant scintillation at $\nu \lesssim 10$ GHz. AT 2023lcr and AT 2019pim show evidence of scintillation until at least $\Delta t\approx30\,$d, but AT 2021lfa exhibits scintillation for much longer, until at least $\Delta t\approx100\,$d. The SED evolution is also similar among the three objects, with a hint of self-absorption in the first few days, and a broad peak that passes through $\nu\approx10\,$GHz over the course of the observations. The peak passes through 10 GHz at around 30 d for AT 2019pim and AT 2021lfa, and at around 10 d for AT 2023lcr.

# Fitting Framework

## Settings

| Parameter | Unit | Description | Prior (Uniform) |
|:--:|:--:|:---|:--:|
| $t_0$ | \[MJD\] | estimated burst time | \- |
| $\theta_\text{v}$ | \[rad\] | viewing angle | \[0, 1.57\] |
| $\log_{10}(E_\text{K,iso}/\text{erg})$ |  | isotropic equivalent kinetic energy of blast wave along jet axis | \[45, 57\] |
| $\theta_\text{c}$ | \[rad\] | half-opening angle of jet core | \[0.02, 0.78\] |
| $\theta_\text{w}$ | \[rad\] | wing truncation angle of a structured jet | $[1, 7] \times \theta_\text{c}$ |
| $\log_{10}(n_0/\text{cm}^{-3})$ |  | number density of protons in circumburst medium | \[-10, 10\] |
| $p$ |  | power law index of relativistic electron energy distribution | \[2, 3\] |
| $b$ |  | power law index of jet angular energy distribution | \[0, 10\] |
| $\log_{10}\epsilon_e$ |  | fraction of thermal energy in relativistic electrons | \[-5, 0\] |
| $\log_{10}\epsilon_B$ |  | fraction of thermal energy in magnetic field | \[-5, 0\] |
| $\xi_N$ |  | fraction of accelerated electrons | \[0, 1\] |
| $\log_{10}\Gamma_0$ |  | initial Lorentz factor of jet | \[0, 3\] |

We use `afterglowpy` (version 0.7.3; (cite: Ryan_2020)) and MCMC methods in `emcee` (version 3.1.4; (cite: Foreman_Mackey_2013)) to fit the radio, optical, and X-ray observations of AT 2023lcr with a set of physical parameters that describe the jet and circumburst medium. To put AT 2023lcr’s modeling into context, we also perform a consistent analysis on three similarly discovered events, shown in Table [1](#tab:orphan-summary): AT 2020blt, AT 2021any, and AT 2021lfa. For AT 2019pim, see (cite: Perley_2024), which explored a similarly broad range of scenarios; for AT 2023sva, see (cite: 2023sva). By contrast, previous works modeling AT 2020blt (cite: Sarin_2022), AT 2021any (cite: Gupta_2022; Xu_2023), and AT 2021lfa (cite: Ye_2024) explored more fixed setups.

All data used in this work for AT 2020blt and AT 2021any can be found in (cite: Ho_2020; Ho_2022). To model AT 2021lfa, we used all observations from (cite: Ho_2022) and additional observations from (cite: Lipunov_2022). Optical observations were corrected for Galactic extinction with $E(B-V)=A_V/R_V$, assuming $R_V = 3.1$ (cite: Schlegel_1998). For all afterglows, we converted X-ray fluxes to a 5 keV flux density assuming a spectral index of $\beta = -1$, where $f_\nu \propto \nu^\beta$.

Our `emcee` settings are as follows. To minimize bias, our priors are broad and uniform (see Table [\[table:priors\]](#table:priors)). We use the standard `EnsembleSampler` from `emcee`. We perform most runs using 64 walkers and 75,000 iterations, discarding 30,000 iterations as the burn-in. If samples do not appear converged with these settings, we run using 64 walkers and 225,000 iterations, discarding 125,000 as the burn-in. We use a simple Gaussian likelihood for each data point. For AT2020blt, we penalize samples that do not satisfy radio upper limits by finding the log likelihood between the sample-generated radio data point and a zero flux point.

We fit each afterglow to top hat, Gaussian, and power law jet structures found in `afterglowpy`. The simplest structure is a top hat model, in which energy is constant from the central axis to the edge of the jet:

$$\begin{equation}
    E(\theta) =
    \left\{
    \begin{array}{cc}
         E_\text{K,iso}, & \theta \leq \theta_\text{c} \\
         0, & \theta > \theta_\text{c}
    \end{array}
    \right\},
\label{eq:top-hat}
\end{equation}$$

where $E_\text{K,iso}$ is the isotropic-equivalent kinetic energy of the outflow along the jet axis and $\theta_\text{c}$ is the half-opening angle of the jet core. The top hat model offers no extended jet structure, unlike Gaussian or power law structures, which particularly affects off-axis or even slightly off-axis observations (cite: Ryan_2020; Cunningham_2020). For a Gaussian structured jet,

$$\begin{equation}
    E(\theta) =
    \left\{
    \begin{array}{cc}
         E_\text{K,iso} \exp{(-\frac{\theta^2}{2\theta_\text{c}^2})}, & \theta \leq \theta_\text{w} \\
         0, & \theta > \theta_\text{w}
    \end{array}
    \right\},
\label{eq:gauss}
\end{equation}$$

where the jet extends beyond $\theta_\text{c}$ to a “wing-truncation angle" $\theta_\text{w}$. A power law structured jet has a similar structure:

$$\begin{equation}
    E(\theta) = E_\text{K,iso} \left(1 + \frac{\theta^2}{b\theta_\text{c}^2}\right)^{-b/2},
\label{eq:power-law}
\end{equation}$$

where $b$ is the power law index at which the jet energy decreases. Because there is structure beyond $\theta_\text{c}$ in the Gaussian and power law models, observers are able to view afterglow emission beyond a viewing angle $\theta_\text{v} = \theta_\text{c}$. In this work, we attempt to describe each afterglow with the simplest possible structure (an on-axis top hat jet). We report the result of other structures only if the afterglow is inconsistent with an on-axis top hat jet (by eye, or has a $\chi^2$/DoF significantly worse than other models).

Along with top hat, Gaussian, and power law jet structures, we fit each afterglow to various combinations of multi-wavelength observations, since afterglow emission at different wavelengths can reveal different physics. For example, radio observations can capture “reverse shock" emission, which traces a shock propagating back through the outgoing jet shell and towards the central engine, typically crossing this region at the deceleration time (cite: Kobayashi_2000; Piran_2005; Laskar_2016). We fit each model only to optical observations, then only to optical and X-ray observations, then to all radio, optical, and X-ray observations—and report any significant differences in the results.

## afterglowpy Limitations

`afterglowpy` (version 0.7.3) uses the single-shell approximation (cite: single-shell) to model a blast wave propagating through a homogeneous circumburst medium (cite: Ryan_2020). `afterglowpy` is useful for its range of afterglow settings and its implementation of structured jets, but is limited in different ways which could affect our interpretations. For example, if support for Inverse Compton Cooling (ICC) is enabled, `afterglowpy` overestimates its radiative contribution. Additionally, by default, `afterglowpy` assumes $\Gamma_0 = \infty$, such that there is no initial coasting phase or deceleration break, which might produce unreliable early-time light curves. On the other hand, for a finite $\Gamma_0$, `afterglowpy` disables jet spreading, which might produce unreliable late-time light curves. To work around this, we run MCMC multiple times, with each combination: with and without ICC; and with $\Gamma_0 = \infty$ and $\Gamma_0 \neq \infty$. We report any notable differences in the inferred parameters.

In addition to the above, `afterglowpy` does not support reverse shock physics, which might particularly affect radio observations. Also, `afterglowpy` lacks support for synchrotron self-absorption. In this work, self-absorption affects AT 2021lfa, in which radio observations $\lesssim$ 21 days from the estimated burst time may be self-absorbed (cite: Ho_2022). There may also be hints of self-absorption in the first few days of AT 2023lcr’s SED evolution (see Figure [3](#fig:at2023lcr-radio-sed) in Section [2](#sec:at2023lcr)). We include all observations in the fit, but caution that the model may be expected to overpredict the radio luminosity at early times (while lacking the reverse shock may result in underpredicting the radio luminosity, particularly at early times).

Finally, `afterglowpy` implements a homogeneous circumburst medium, with no support for a stellar wind medium. Although in principle, a massive star progenitor should have a stellar wind medium, past works have shown that generally, a homogeneous medium fits well to most LGRBs (cite: Schulze_2010; Hjorth_2011), with some exceptions (cite: Panaitescu_2001).

## Goodness of Fit Metrics

To quantify the goodness of fit between modeling configurations, we use a reduced $\chi^2$ $$\begin{equation}
    \chi^2 \equiv \frac{1}{\text{DoF}} \sum \frac{(f_{\text{model}} - f_{\text{obs}})^2}{\sigma^2},
\end{equation}$$ where $f_{\text{model}}$ is the model generated light curve, $f_{\text{obs}}$ is the observed light curve, $\sigma$ is the uncertainty (systematic and statistical) in observations, and DoF is the difference between the number of observations and the number of MCMC parameters. In the results that follow, we report the minimum $\chi^2$ over 5,000 randomly selected posterior samples. We note that for VLA data, we include a $5\%$ systematic error on the flux densities for the L, S, C, X, and Ku-bands (1-18 GHz), and a $15\%$ systematic error for the K and Ka-bands (18-40 GHz).

We also use the Widely Available Information Criterion (WAIC; (cite: Watanabe_2010; Cunningham_2020)), which can be calculated from MCMC posterior samples. WAIC estimates the “expected log predictive density" ($\widehat{\text{elpd}}$), which describes how well a model should fit to new data. We do not normalize our WAIC scores, so a more positive $\widehat{\text{elpd}}$ indicates a stronger predictive power. In this paper, we report each $\widehat{\text{elpd}}$ calculated over 5,000 randomly selected posterior samples.

## Radiative Efficiencies

|            |                         |                           |
|:-----------|:------------------------|:--------------------------|
| Afterglow  | $E_{\gamma,\text{iso}}$ | Reference                 |
|            | ($10^{52}$ erg)         |                           |
| AT 2020blt | $< 1.0$                 | (cite: Ho_2020; Ho_2022)  |
|            | $< 0.1 - 0.6$           | (cite: Sarin_2022)        |
| AT 2021any | $< 14.3$                | (cite: Ho_2022)           |
| AT 2021lfa | $< 0.12$                | (cite: Ho_2022)           |
| AT 2023lcr | $< 2.1$                 | (cite: Ridnaia_2023);     |
|            |                         | this work; for $z=1.0272$ |
|            | $< 4.9$                 | for $z=1.6$               |

: Radiative energy upper limits for AT 2020blt, AT 2021any, AT 2021lfa, and AT 2023lcr. (cite: Sarin_2022)’s estimate uses *Fermi* observations, to which the position of AT 2020blt was not fully visible during the duration between its last non-detection and first detection.

To calculate the efficiency of gamma-ray radiation for each event, or “radiative efficiency", we use

$$\begin{equation}
    \eta_\gamma = \frac{E_{\gamma,\text{iso}}}{E_\text{K,iso} + E_{\gamma,\text{iso}}},
\label{eq:eff}
\end{equation}$$

where $E_\text{K,iso}$ is the isotropic-equivalent kinetic energy of the jet, found from modeling. $E_{\gamma,\text{iso}}$ is the observed isotropic-equivalent energy in gamma-rays, or “radiative energy" from flux or fluence upper limits of gamma-ray facilities. We calculate an $E_{\gamma,\text{iso}}$ upper limit for AT 2023lcr in Section [2.5](#sec:grb-search). Limits for AT 2020blt, AT 2021any, and AT 2021lfa have been calculated in (cite: Ho_2020), (cite: Ho_2022), and (cite: Sarin_2022). We summarize all $E_{\gamma,\text{iso}}$ upper limits in Table [2](#table:radiative-energies). We note that the upper limit from (cite: Sarin_2022) was based on a subthreshold search of *Fermi* observations, which experienced interruptions between AT 2020blt’s last non-detection and first detection.

# Results and Discussion

## Analytical Constraints on the Lorentz Factors

We follow (cite: Perley_2024) to obtain analytical estimates on the afterglow bulk Lorentz factors, summarizing results in Table [3](#table:analytical-lorentz-factors). Assuming a uniform medium density, we can obtain a limit on the initial Lorentz factor of the jet from the deceleration time using Equation 16 of (cite: Meszaros_2006),

$$\begin{equation}
\Gamma_{2.5} = \left( \frac{10\,\text{s} (1 + z)}{t_\text{dec}} \right)^{3/8} \left(\frac{E_{53}}{n_0}\right)^{1/8},
\label{eq:tdec}
\end{equation}$$

where $z$ is the redshift, $n_0$ is the number density of the circumburst medium in cm$^{-3}$, $E_{53} = E_{\text{K,iso}} / 10^{53}$, $\Gamma_{2.5} = \Gamma_0 / 10^{2.5}$, and $t_\text{dec}$ is the deceleration time in seconds[^15]. Typically, $t_\text{dec}$ coincides with the peak of the X-ray afterglow, which occurs on the same timescale as the afterglow rise time. Therefore, we approximate $t_\text{dec} \approx t_\text{rise}$, where $t_\text{rise}$ is the afterglow rise time. Using the difference between the first detection and last non-detection[^16] as an upper limit on $t_\text{rise}$, we obtain the $\Gamma_0$ lower limits shown in Table [3](#table:analytical-lorentz-factors), abbreviating $\kappa = (E_{53}/n_0)^{1/8}$. For AT 2021lfa, we also obtain an upper limit on $\Gamma_0$, since $t_\text{rise} > 0.13$ d, which is the time between AT 2021lfa’s first MASTER detection and ZTF peak detection.

|  |  |  |  |
|:---|:---|:---|:---|
| Afterglow | Rise Time | Spectrum | ISS |
|  | ($\Gamma_0 / \kappa$) | ($\Gamma_{\text{avg}}^\dag$) | ($\Gamma_{\text{avg}}^\dag$) |
| AT 2020blt | $\gtrsim 19.7$ | \- | \- |
| AT 2021any | $\gtrsim 81.2$ | $\gtrsim 45$, $\gtrsim 62$ | $\lesssim 127$, $\lesssim 175$ |
| AT 2021lfa | $\gtrsim 10.8$, $\lesssim 30.0$ | $\gtrsim 3$, $\gtrsim 27$ | $\lesssim 6.4$, $\lesssim 60$ |
| AT 2023lcr | $\gtrsim 37.8$ | $\gtrsim 14$, $\gtrsim 39$ | $\lesssim 86$, $\lesssim 328$ |

: Analytical constraints on the Lorentz factors for AT 2020blt, AT 2021any, AT 2021lfa, and AT 2023lcr. We abbreviate $\kappa = (E_{53} / n_0)^{1/8}$. $^\dag$Left hand values are average Lorentz factors at the time of first detection. Right hand values are average Lorentz factors at the beginning of deceleration. We assume a typical rest-frame deceleration time $t_\text{dec,rest} \approx t_\text{rise,rest} \approx 200$ s, but caution that if AT 2021lfa’s rising phase is due to deceleration, then its right hand values are overestimates.

We can also obtain a lower limit on the average Lorentz factor $\Gamma_\text{avg}$ from radio spectra using Equation 5 from (cite: Barniol_Duran_2013). We assume a full filling factor and use the time of the last non-detection as a lower limit on the explosion time. Since AT 2020blt lacks multifrequency radio observations, we only perform this calculation on AT 2021any, AT 2021lfa, and AT 2023lcr.

Radio observations of AT 2021any (cite: Ho_2022) are unlikely to be impacted by synchrotron self-absorption given their observed spectral indices, so we use observations from the its first radio epoch at $\Delta t = 4.91$ d to estimate $\Gamma_{\text{avg,4.91d}} \gtrsim 3.0$ at $4.91$ days from its last non-detection. On the other hand, the radio spectra of AT 2021lfa (cite: Ho_2022) and AT 2023lcr show possible self-absorption until $\Delta t \approx 20$ d and $\Delta t \approx 6$ d, respectively. Using observations from these epochs, we obtain $\Gamma_{\text{avg,22.69d}} \gtrsim 1.1$ for AT 2021lfa and $\Gamma_\text{avg,6.3d} \gtrsim 2.6$ for AT 2023lcr. Assuming that their light curve breaks are caused by jet expansion, we can follow (cite: Galama_2003) to extrapolate these estimates to the times of their first detections, obtaining the results in Table [3](#table:analytical-lorentz-factors). We extrapolate AT 2021any and AT 2023lcr using $\Gamma \propto t^{-1/2}$, which holds for post jet break expansion. AT 2021lfa exhibits no jet break, so for it we use the pre jet break case $\Gamma \propto t^{-3/8}$.

As discussed in (cite: Perley_2024), $\Gamma_\text{avg,first}$ is different from $\Gamma_0$, which can still be large if $t_\text{dec}$ is small. To alleviate this uncertainty, we also extrapolate $\Gamma_\text{avg}$ to $t_\text{dec}$ to obtain a closer estimate of $\Gamma_0$, assuming that $\Gamma$ is constant from explosion to the start of deceleration. If we take a typical rest-frame LGRB deceleration time $t_\text{dec,rest} \approx t_\text{rise,rest} \approx 200$ s (cite: Ghirlanda_2018), we obtain the larger values for $\Gamma_\text{avg}$ shown along initial estimates in Table [3](#table:analytical-lorentz-factors). We caution that if AT 2021lfa’s rising phase is due to deceleration and not off-axis behavior, then its value is an overestimate.

|            |        |         |               |                |
|:-----------|:------:|:-------:|:-------------:|:--------------:|
| Afterglow  |  $T$   | $\nu_0$ | $\theta_{F0}$ |      $D$       |
|            | (days) |  (GHz)  | ($\mu$arcsec) | ($10^{16}$ cm) |
| AT 2021any |   21   |   15    |       2       |      $5$       |
| AT 2021lfa |  104   |  $<8$   |     $<5$      |     $<13$      |
| AT 2023lcr |   10   |    9    |      3.5      |      $9$       |

: Approximate durations $T$ of strong ISS, critical frequencies ISS $\nu_0$, Fresnel scales $\theta_{F0}$, and physical sizes of the Fresnel scale $D$ of AT 2021any, AT 2021lfa, and AT 2023lcr. Critical ISS frequencies and Fresnel scales are found from (cite: Walker_2001).

Finally, we obtain upper limits on $\Gamma$ from the presence of strong interstellar scintillation (ISS), assuming that is responsible for the observed variability in AT 2021any, AT 2021lfa, and AT 2023lcr (AT 2020blt’s radio observations are too limited).

If a source exhibits strong ISS (radio fluctuations greater than a factor $\sim 2$) at a frequency near or less than its critical ISS frequency $\nu_0$ (cite: Walker_2001; Perley_2024), then the source’s size is at most as large as the Fresnel scale $\theta_{F0}$ at its location. Given the source size and estimated explosion time, an upper limit on the Lorentz factor can be calculated.

In Table [4](#table:iss-helpers), we list approximate timescales $T$ for strong ISS, critical ISS frequencies $\nu_0$, Fresnel scales $\theta_{F0}$ at $\nu_0$, and physical sizes of the Fresnel scale $D$ given the angular diameter distances of the three afterglows. From these values, we obtain $\Gamma_{\text{avg,21d}} \lesssim 3.4$ for AT 2021any, $\Gamma_{\text{avg,104d}} \lesssim 1.4$ for AT 2021lfa, and $\Gamma_{\text{avg,10d}} \lesssim 7.1$ for AT 2023lcr. Extrapolating to the times of their first detections and deceleration times, we obtain the upper limits found in Table [3](#table:analytical-lorentz-factors).

## AT2023lcr

We present the results of an on-axis top hat jet with a finite $\Gamma_0$ in Table [5](#tab:lcr-results) and Figure [5](#fig:lcr-results), with a corner plot in Figure [11](#fig:lcr-corner) of Appendix [10](#app:corner-plots). The model is able to reproduce key features of all observations, particularly the early-time optical *L*-band detection and the achromatic break $\sim 2$ days after the estimated burst time. However, the model somewhat overestimates radio observations in the radio L-band (1.39 GHz) and S-band (3.75 GHz), which may be due to the susceptibility of low frequency emission to synchrotron self-absorption, which `afterglowpy` does not model. The model also slightly overestimates the *u*-band detection, which may be due to host-galaxy extinction. Fitting configurations with different `afterglowpy` settings obtained similar results; see Table [13](#tab:lcr-selected) in Appendix [11](#app:selected) for results of selected configurations. Optical only and optical-X-ray only fits yielded on-axis low Lorentz factor ($\Gamma_0 \sim 30$) GRBs with typical efficiencies and much higher densities ($n_0 \sim 10^{-1} - 10^{-2}$ cm$^{-3}$), but had softer light curve breaks at $\Delta t \sim 2$ d and tended to severely overestimate radio detections.

Our results suggest that AT 2023lcr is consistent with an on-axis classical GRB, with a highly collimated jet ($\theta_\text{c} \approx 0.02$ rad, or equivalently, $1.15^\circ$) and a low density circumburst environment ($n_0 \sim 10^{-4}$ cm$^{-3}$). Calculations on large catalogues of GRBs find most GRBs to have opening angles $\sim 5^\circ$, with few GRBs populating the $\sim 1^\circ$ opening angle regime (cite: Goldstein_2016; Ghirlanda_2005). While there are GRBs that have circumburst densities as low as $10^{-5}$ cm$^{-3}$ (see GRB 090423; (cite: Tanvir_2009; Salvaterra_2009; Laskar_2013b)), most have circumburst densities within $n_0 = 10^{-1} - 10^{2}$ cm$^{-3}$ (cite: Laskar_2013b). If AT 2023lcr can be described by a homogeneous medium, then our modeling places AT 2023lcr in a small opening angle, lower density regime.

From the median values in Table [5](#tab:lcr-results), we obtain a beaming-corrected value of the blast wave energy $E_{K} \approx 2.2 \times 10^{50}$ erg, which falls within typical LGRB values of $E_{K}$ (cite: Laskar_2013b). We also note that our posterior $\Gamma_0 \approx 166$ is consistent with analytical estimates from Section [5.1](#sec:lorentz-factor-constraints).

AT 2023lcr is consistent with an on-axis GRB afterglow, yet KONUS-*Wind* found no GRB detection while observing the entire night sky during the time between the last GOTO non-detection and first GOTO detection. Therefore, AT 2023lcr had an isotropic radiative energy below $2.1 \times 10^{52}$ erg and a possible radiative efficiency $\eta_\gamma < 2.3\%$, which is consistent with typical LGRB efficiencies (cite: Racusin_2011).

| Parameter                              | Result                         |
|:---------------------------------------|:-------------------------------|
| $t_0$ \[MJD\]                          | $60113.03_{-0.02}^{+0.01}$     |
| $\theta_\text{v}$ \[rad\]              | $0.00_{-0.00}^{+0.00}$         |
| $\log_{10}(E_\text{K,iso}/\text{erg})$ | $53.95_{-0.17}^{+0.22}$        |
| $\theta_\text{c}$ \[rad\]              | $0.02_{-0.00}^{+0.00}$         |
| $\log_{10}(n_0/\text{cm}^{-3})$        | $-4.37_{-0.36}^{+0.53}$        |
| $p$                                    | $2.13_{-0.01}^{+0.01}$         |
| $\log_{10}\epsilon_e$                  | $-1.55_{-0.22}^{+0.16}$        |
| $\log_{10}\epsilon_B$                  | $-0.63_{-0.38}^{+0.32}$        |
| $\xi_N$                                | $0.63_{-0.24}^{+0.25}$         |
| $\log_{10}\Gamma_0$                    | $2.22_{-0.09}^{+0.06}$         |
| $\eta_\gamma$ ($z = 1.0272$)           | $< 1.3 - 3.4\%$                |
| $\eta_\gamma$ ($z = 1.6$)              | $< 3.2 - 7.5\%$                |
| $\chi^2$/DoF                           | $14.0$                         |
| $\widehat{\text{elpd}}$                | $(-1.7 \pm 0.4) \times 10^{2}$ |

: Final parameters ($68\%$ uncertainty) for the on-axis, top hat, $\Gamma_0 \neq \infty$ configuration for AT 2023lcr. We calculate $\eta_\gamma$ using the $1\sigma$ distribution of $E_\text{K,iso}$ and the $E_{\gamma,\text{iso}}$ limits from Table [2](#table:radiative-energies). We present the $\widehat{\text{elpd}}$ and minimum $\chi^2$/DoF over 5,000 posterior samples; the large $\chi^2$/DoF is due to the overestimation of lower-frequency radio bands (L, S). Ran with 64 walkers and 75,000 iterations; discarded 25,000.

## AT2020blt

We present the results of a top hat jet with $\Gamma_0 = \infty$ in Table [6](#tab:blt-results) and Figure [6](#fig:blt-results), with a corner plot in Figure [12](#fig:blt-corner) of Appendix [10](#app:corner-plots). The model is consistent with optical observations, but underpredicts the X-ray detection by 1.5 orders of magnitude. Other `afterglowpy` configurations produced a similar results, but models with a finite $\Gamma_0$ were inconsistent with the $\sim25$ d radio non-detection by a factor of 3. We also note that the top hat model we present has the smallest $\chi^2$ and highest predictive power ($\widehat{\text{elpd}}$) of all models attempted for AT 2020blt. See Table [14](#tab:blt-selected) in Appendix [11](#app:selected) for results of selected configurations. We note that modeling AT 2020blt without radio observations showed no significant improvement in the X-ray discrepancy. Optical only and optical-X-ray only configurations generally yielded on-axis classical GRBs, some with potentially very low efficiencies ($\eta_\gamma \lesssim 0.1 - 1.4\%$; using S22’s $E_{\gamma,\text{iso}}$ estimate in Table [2](#table:radiative-energies)).

| Parameter | This Work | S22 |
|:---|:---|:---|
| $t_0$ \[MJD\] | $58875.61_{-0.05}^{+0.10}$ | $58875.13_{-1.06}^{+0.58}$ |
| $\theta_\text{v}$ \[rad\] | $0.08_{-0.08}^{+0.08}$ | $0.06_{-0.04}^{+0.05}$ |
| $\log_{10}(E_\text{K,iso}/\text{erg})$ | $53.00_{-0.56}^{+0.67}$ | $53.61_{-0.35}^{+0.25}$ |
| $\theta_\text{c}$ \[rad\] | $0.09_{-0.04}^{+0.06}$ | $0.14_{-0.04}^{+0.04}$ |
| $\theta_\text{w}$ | \- | $0.42_{-0.02}^{+0.16}$ |
| $\log_{10}(n_0/\text{cm}^{-3})$ | $2.05_{-1.76}^{+1.15}$ | $1.90_{-1.72}^{+1.30}$ |
| $p$ | $2.83_{-0.23}^{+0.13}$ | $2.78_{-0.20}^{+0.14}$ |
| $b$ | \- | $5.14_{-2.76}^{+2.89}$ |
| $\log_{10}\epsilon_e$ | $-0.63_{-0.62}^{+0.41}$ | $-1.10_{-0.31}^{+0.34}$ |
| $\log_{10}\epsilon_B$ | $-3.56_{-0.86}^{+1.38}$ | $-1.64_{-0.83}^{+0.73}$ |
| $\xi_N$ | $0.46_{-0.31}^{+0.35}$ | $0.67_{-0.83}^{+0.73}$ |
| $\log_{10}\Gamma_0$ | $\infty^\dag$ | $2.70_{-0.43}^{+0.21}$ |
| $\eta_\gamma$ | $<2.1-26.6\%$ | $<0.1-3.2\%$ |
| $\eta_\gamma$ (*Fermi*) | $<0.2-17.9\%$ | $<0.1-3.2\%$ |
| $\chi^2$/DoF | $3.1$ | \- |
| $\widehat{\text{elpd}}$ | $(1.0 \pm 0.1) \times 10^{2}$ | \- |

: Final parameters ($68\%$ uncertainty) for the top hat, $\Gamma_0 = \infty$ configuration for AT 2020blt. We calculate $\eta_\gamma$ using the $1\sigma$ distribution of $E_\text{K,iso}$ and $E_{\gamma,\text{iso}}$ limits from Table [2](#table:radiative-energies). We present the $\widehat{\text{elpd}}$ and minimum $\chi^2$/DoF over 5,000 posterior samples. We also include the power law fitting results from (cite: Sarin_2022). Ran with 64 walkers and 225,000 iterations; discarded 125,000.\
$^\dag$ Not from MCMC.

From Table [6](#tab:blt-results), we obtain $\theta_\text{c} \sim 5^\circ$ and a beaming-corrected $E_\text{K} \sim 4 \times 10^{50}$ erg, physical parameters typical of GRBs. However, we acknowledge that all parameters have broad uncertainties due to AT 2020blt’s sparse observations. The modeled circumburst density is somewhat high, with $n_0 \sim 112$ cm$^{-3}$, but we note that LGRBs with densities as high as $n_0 \sim 600$ cm$^{-3}$ (see GRB 050904; (cite: Cummings_2005; Tagliaferri_2005; Haislip_2006; Laskar_2013b)) have been discovered. We also obtain a radiative efficiency $\eta_\gamma < 2.1-26.6\%$ using the KONUS-*Wind* $E_{\gamma,\text{iso}}$ limit (see Table [2](#table:radiative-energies)), which is typical of GRBs, as calculated in (cite: Racusin_2011). If we use the less conservative *Fermi* $E_{\gamma,\text{iso}}$ limit, we obtain possibly very low efficiencies $\eta_\gamma < 0.2\%$, lower than $98.5\%$ of LGRB efficiencies reported in (cite: Racusin_2011). Our high-$\Gamma$ fit is also consistent with the lower limits from Section [5.1](#sec:lorentz-factor-constraints)

We also obtain values of $\theta_\text{v}$ that allow for off-axis solutions. We include a comparison between off- and on-axis fits in Figure [7](#fig:blt-off-axis-results) and Table [7](#tab:blt-off-axis-comparison). As expected, the off-axis solution places the peak of the light curve at a later time and has a higher blast wave energy than the on-axis fit. Both fits have comparable $\chi^2$ and $\widehat{\text{elpd}}$ values, suggesting that AT 2020blt is consistent with classical on-axis and off-axis GRBs. Ultimately, we lack the early-time data to resolve the viewing angle degeneracy.

To summarize, we find that AT 2020blt is consistent with off-axis and on-axis classical GRBs. This multimodality may be from sparse observations or from `emcee` and `afterglowpy` limitations; in any case, a classical GRB origin cannot be ruled out for AT 2020blt. We also caution that all fits underestimate the X-ray observation by approximately 1.5 orders of magnitude. This X-ray excess could be from ongoing central engine activity (cite: Zhao_2020) or an insufficient $\chi^2$ penalty, since AT 2020blt has only a single X-ray observation with a large uncertainty ($f_\text{5\,keV} = 3.14\pm 1.04$ $\mu$Jy).

| Parameter                        | Off-axis     | On-axis     |     |
|:---------------------------------|:-------------|:------------|:----|
| $\theta_\text{v}$ \[rad\]        | 0.04         | 0.002       |     |
| $\theta_\text{c}$ \[rad\]        | 0.02         | 0.01        |     |
| $t_0$ \[MJD\]                    | 58875.65     | 58875.55    |     |
| $\log_{10}(E_\text{K,iso}$/)     | 54.0         | 52.6        |     |
| $\log_{10} (n_0/\text{cm}^{-3})$ | -1.0         | 0.09        |     |
| $\chi^2$/DoF                     | 3.1          | 3.3         |     |
| $\widehat{\text{elpd}}$          | $104 \pm 10$ | $103 \pm 9$ |     |

: Parameters of lowest-likelihood off- and on-axis solutions. To calculate the $\widehat{\text{elpd}}$, we split the posterior into off-axis and on-axis solution sets and find the $\widehat{\text{elpd}}$ over 5,000 samples from each set.

### Comparison to S22

S22 use `afterglowpy` and `dynesty` (cite: dynesty) to model the optical observations of AT 2020blt with top hat, power law, and cocooned jet structures, and find that AT 2020blt is best explained by an on-axis power law jet with physical parameters typical of LGRBs, consistent with this work. Using the upper limit for $E_{\gamma,\text{iso}}$ from a subthreshold search on *Fermi* (see Table [2](#table:radiative-energies)), which experienced interruptions between AT 2020blt’s last non-detection and first detection, S22 explain AT 2020blt as a low-efficiency burst with $\eta_\gamma < 0.1\%$, smaller than $98.5\%$ of LGRB efficiencies from (cite: Racusin_2011). This work reports more typical efficiencies $\eta_\gamma<2.1-26.6\%$ using the KONUS-*Wind* upper limit on $E_{\gamma,\text{iso}}$, but does obtain estimates as low as $\eta_\gamma < 0.2\%$ with the *Fermi* upper limit, consistent with S22. We note that S22 model only the optical observations of AT 2020blt; using the *Fermi* estimate, our optical only configurations also produce efficiencies as low as $\eta_\gamma < 0.1\%$. In any case, both S22 and this work indicate that AT 2020blt is consistent with an on-axis GRB with physical parameters that are fairly typical of the LGRB population.

## AT2021any

| Parameter | Free $t_0$ | Fixed $t_0$ | G22 | X24 |
|:---|:---|:---|:---|:---|
| $t_0$ \[MJD\] | $59230.28_{-0.00}^{+0.00}$ | $59230.29$ | $59230.276^\dag$ | $59230.29_{-0.12}^{+0.16}$ |
| $\theta_\text{v}$ \[rad\] | $0.05_{-0.01}^{+0.01}$ | $0.05_{-0.01}^{+0.01}$ | $0.55_{-0.27}^{+0.27}$ | $0.03_{-0.01}^{+0.01}$ |
| $\log_{10}(E_\text{K,iso}/\text{erg})$ | $53.54_{-0.36}^{+0.49}$ | $53.60_{-0.32}^{+0.34}$ | $52.58_{-0.03}^{+0.03}$ | $52.90_{-0.12}^{+0.12}$ |
| $\theta_\text{c}$ \[rad\] | $0.10_{-0.03}^{+0.03}$ | $0.11_{-0.02}^{+0.03}$ | $0.96_{-0.28}^{+0.17}$ | $0.08_{-0.01}^{+0.01}$ |
| $\log_{10}(n_0/\text{cm}^{-3})$ | $2.41_{-0.68}^{+0.56}$ | $2.57_{-0.43}^{+0.43}$ | $-0.06_{-0.17}^{+0.19}$ | $-0.78_{-0.19}^{+0.19}$ |
| $p$ | $2.01_{-0.01}^{+0.01}$ | $2.01_{-0.00}^{+0.01}$ | $2.30_{-0.05}^{+0.05}$ | $2.39_{-0.02}^{+0.02}$ |
| $\log_{10}\epsilon_e$ | $-0.36_{-0.49}^{+0.26}$ | $-0.33_{-0.37}^{+0.23}$ | $-1^\ddag$ | $-0.94_{-0.05}^{+0.05}$ |
| $\log_{10}\epsilon_B$ | $-4.70_{-0.22}^{+0.41}$ | $-4.78_{-0.16}^{+0.29}$ | $-2.23_{-0.13}^{+0.12}$ | $-2.76_{-0.24}^{+0.24}$ |
| $\xi_N$ | $0.63_{-0.29}^{+0.26}$ | $0.68_{-0.30}^{+0.22}$ | $1^\ddag$ | $1^\ddag$ |
| $\log_{10}\Gamma_0$ | $2.31_{-0.36}^{+0.45}$ | $1.91_{-0.09}^{+0.08}$ | $\infty^\ddag$ | $1.92_{-0.05}^{+0.06}$ |
| $\eta_\gamma$ | $< 11.8 - 48.6\%$ | $< 14.1 - 42.9\%$ | $< 77.8 - 80.1\%^\dag$ | $< 57.7 - 70.3\%^\dag$ |
| $\chi^2$/DoF | $17.0$ | $13.3$ | \- |  |
| $\widehat{\text{elpd}}$ | $(-1.3 \pm 4.3) \times 10^{2}$ | $10.3 \pm 31.3$ | \- | \- |

We present the results of an on-axis top hat jet with a finite $\Gamma_0$ in Table [\[tab:any-results\]](#tab:any-results) and Figure [8](#fig:any-results), with a corner plot in Figure [13](#fig:any-corner) of Appendix [10](#app:corner-plots). Since the first detection and last non-detection of AT 2021any are only 22 minutes apart, we also fit AT 2021any to an on-axis top hat jet with a fixed burst time $t_0 = 59230.290$ MJD, which we note is an arbitrary choice that lies between the last non-detection and first detection. We present the results of this configuration in Table [\[tab:any-results\]](#tab:any-results) and Figure [8](#fig:any-results), with a corner plot in Figure [14](#fig:any-t0-corner) of Appendix [10](#app:corner-plots). The free $t_0$ model places the peak of the light curve before the first ZTF detection, while the fixed $t_0$ model places it after. This is expected given the earlier burst time found for the free $t_0$ model in Table [\[tab:any-results\]](#tab:any-results). There are no other notable differences and both configurations are able to reproduce all observations. Other `afterglowpy` configurations are also consistent with observations, except those with ICC enabled, which fail to account for the X-ray observation. See Table [15](#tab:any-selected) in Appendix [11](#app:selected) for results of selected configurations. Optical only and optical-X-ray only fits allowed for potentially off-axis and low-efficiency solutions ($\eta_\gamma \lesssim 0.2 - 0.7\%$), all with typical Lorentz factors. However, the potentially off-axis solutions are highly ambiguous given the lack of early-time observations for AT 2021any.

As shown in Table [\[tab:any-results\]](#tab:any-results), both models also find low-$\Gamma_0$ and high-$\Gamma_0$ solutions. The free $t_0$ model finds $\Gamma_0 \approx 204_{-115}^{+371}$, while the fixed $t_0$ model finds $\Gamma_0 \approx 81_{-15}^{+17}$, indicating that AT 2021any is possibly consistent with both a moderate and ultra-relativistic jet. Ultimately, we lack the higher-cadence early optical data to resolve this degeneracy.

| Parameter | Top hat | Gaussian | Y24 |
|:---|:---|:---|:---|
| $t_0$ \[MJD\] | $59338.06_{-0.02}^{+0.01}$ | $59338.01_{-0.02}^{+0.03}$ | $59337.92_{-0.04}^{+0.08}$ |
| $\theta_\text{v}$ \[rad\] | $0.11_{-0.01}^{+0.01}$ | $0.06_{-0.05}^{+0.04}$ | $0.53_{-0.19}^{+0.18}$ |
| $\log_{10}(E_\text{K,iso}/\text{erg})$ | $51.76_{-0.23}^{+0.46}$ | $52.91_{-0.52}^{+0.45}$ | $54.77_{-0.39}^{+0.43}$ |
| $\theta_\text{c}$ \[rad\] | $0.23_{-0.02}^{+0.02}$ | $0.08_{-0.03}^{+0.05}$ | $0.66_{-0.24}^{+0.21}$ |
| $\theta_\text{w}$ | \- | $0.33_{-0.14}^{+0.25}$ | \- |
| $\log_{10}(n_0/\text{cm}^{-3})$ | $1.11_{-0.39}^{+0.42}$ | $3.62_{-0.88}^{+0.63}$ | $1.04_{-0.84}^{+0.70}$ |
| $p$ | $2.53_{-0.05}^{+0.06}$ | $2.17_{-0.04}^{+0.07}$ | $3.09_{-0.03}^{+0.03}$ |
| $\log_{10}\epsilon_e$ | $-0.32_{-0.45}^{+0.23}$ | $-0.28_{-0.54}^{+0.21}$ | $-1.18_{-0.33}^{+0.32}$ |
| $\log_{10}\epsilon_B$ | $-1.62_{-0.39}^{+0.30}$ | $-3.52_{-0.61}^{+0.78}$ | $-4.47_{-0.38}^{+0.70}$ |
| $\xi_N$ | $0.48_{-0.27}^{+0.31}$ | $0.11_{-0.06}^{+0.06}$ | $0.70_{-0.27}^{+0.22}$ |
| $\log_{10}\Gamma_0$ | $1.06_{-0.05}^{+0.06}$ | $0.78_{-0.06}^{+0.12}$ | $\approx 1.3^{\dag}$ |
| $\eta_\gamma$ | $<6.7-26.2\%$ | $<0.5-4.7\%$ | $< 0.01 - 0.05\%$ |
| $\chi^2$/DoF | $6.0$ | $4.7$ | \- |
| $\widehat{\text{elpd}}$ | $77.0 \pm 39.4$ | $36.7 \pm 43.6$ | \- |

Both models find physical parameters typical of the LGRB population, including an opening angle $\theta_\text{c} \approx 6^\circ$ and beaming-corrected $E_K \approx 2 \times 10^{51}$ erg. The densities found are somewhat high at $n_0 \sim 300$ cm$^{-3}$, but as discussed in Section [5.3](#subsec:blt-results), this is not physically implausible. The radiative efficiencies found are also typical of LGRBs (cite: Racusin_2011). Given the uncertainty on $\Gamma_0$ in both the `afterglowpy` fits and the analytical constraints in Section [5.1](#sec:lorentz-factor-constraints), we conclude that an on-axis classical GRB origin cannot be ruled out for AT 2021any.

### Comparison to G22 and X23

G22 use `afterglowpy` and `emcee` to model the optical and X-ray observations of AT 2021any, while X23 use GRB evolution models from (cite: Huang_2002_grbmodel1), (cite: Huang_2006_grbmodel2), (cite: Geng_2013), and (cite: Xu_2022). Both G22 and X23 set $\xi_N = 1$, and G22 uses a $\Gamma_0 = \infty$ `afterglowpy` configuration. The results from these works are shown in Table [\[tab:any-results\]](#tab:any-results). G22 finds that AT 2021any is consistent with an on-axis classical GRB, while X23 explains AT 2021any as an on-axis GRB with a moderate Lorentz factor $\Gamma_0 = 68$. Differences in physical parameters are likely due to differences in fitting configurations. Notably, both G22 and X23 set $\xi_N = 1$. Past works have shown that different values of $\xi_N$ can significantly change other physical parameters (cite: Cunningham_2020), so this is expected; the discrepancies between our results and G22/X24 are consistent with the expected effects of decreasing $\xi_N$ as discussed in (cite: Cunningham_2020). However, the physical conclusion is robust: an on-axis classical GRB cannot be ruled out for AT 2021any.

## AT2021lfa

We present the results of an on-axis top hat jet with a finite $\Gamma_0$ in Table [\[tab:lfa-results\]](#tab:lfa-results) and Figure [9](#fig:lfa-results), with a corner plot in Figure [15](#fig:lfa-corner) of Appendix [10](#app:corner-plots). The model is consistent with optical observations, but underestimates the X-ray detection by $\sim 1$ order of magnitude, and overestimates Ku-band (13 GHz) detections at $\Delta t \gtrsim 110$ d by around a factor of 3. We also include in Table [\[tab:lfa-results\]](#tab:lfa-results), Figure [9](#fig:lfa-results), and Figure [16](#fig:lfa-corner-gauss) of Appendix [10](#app:corner-plots) the results of a finite $\Gamma_0$ Gaussian jet, which is able to reproduce all observations, but slightly underestimates late-time Ku-band detections.

From Table [\[tab:lfa-results\]](#tab:lfa-results), we obtain a beaming-corrected $E_K \sim 10^{50}$ erg and opening angles $\theta_\text{c} \approx 4.6^\circ$ and $13.2^\circ$ respectively for the Gaussian and top hat models, typical of the LGRB population (cite: Ghirlanda_2018). The Gaussian model also prefers a much denser environment ($\approx 4000$ cm$^{-3}$). Both models have very low Lorentz factors, with $\Gamma_0 \approx 11$ for the top hat model and $\Gamma_0 \approx 6$ for the Gaussian model. The Gaussian model also allows for slightly off-axis ($\theta_\text{v} \sim \theta_\text{c}$) solutions. The Gaussian model also obtains a possibly low efficiency $\eta_\gamma < 0.5\%$, which is smaller than $98.5\%$ of LGRB efficiencies in (cite: Racusin_2011) but consistent with the $\lesssim 1\%$ efficiencies of internal shocks models (cite: Kumar_1999).

All other `afterglowpy` configurations (see Table [16](#tab:lfa-selected) in Appendix [11](#app:selected) for results of selected configurations) produce similar results but still have a strong preference for a very low Lorentz factor jet (typically, $\Gamma_0 \approx 5 - 20$), consistent with the analytical $\Gamma$ limits calculated in Section [5.1](#sec:lorentz-factor-constraints) and the $\Gamma_0 = 20 \pm 10$ estimate found from (cite: Lipunov_2022). We note that $\Gamma_0 = \infty$ configurations struggled to reproduce the MASTER observations.

We also fit to a range of data subsets. Optical only and optical-X-ray only configurations obtained on- and off-axis solutions, still with low Lorentz factors ($\Gamma_0 \approx 5 - 20$). We also ran fits that excluded the rising phase, which obtained both classical GRB solutions and on-axis, low Lorentz factor solutions. However, we note that the on-axis classical GRB fits underestimated the Ku-band (13.0 GHz) detections at $\Delta t \gtrsim 110$ d by around a factor of 3.

From our fitting, AT 2021lfa is consistent with on-axis and possibly off-axis low Lorentz factor jets. We explore an off-axis solution in more detail in Section [5.5.2](#sec:off-axis-lfa). In any case, the immediate results indicate a strong preference for a jet with $\Gamma_0 = 5 - 13$, which is remarkably small. The overwhelming majority of classical GRBs report having $\Gamma_0 \gtrsim 100$, with previous calculations on large catalogues of classical GRBs indicating a median $\Gamma_0 = 320$ for a homogeneous circumburst medium (cite: Ghirlanda_2018).

|            | $\alpha$ | $\beta$ |
|:-----------|:--------:|:-------:|
| ISM, slow  |   0.97   |  0.65   |
| ISM, fast  |   1.22   |  1.15   |
| Wind, slow |   1.47   |  0.65   |
| Wind, fast |   1.22   |  1.15   |
| Jet, slow  |   2.30   |  0.65   |

: Approximate values of the optical temporal index $\alpha$ and the optical SED index $\beta$ for various afterglow models using a typical $p = 2.3$. Values were estimated using standard closure relations from (cite: Zhang_2004b). We assume $\nu_m < \nu < \nu_c$ for slow cooling cases and $\nu > \nu_m$ for fast cooling cases.

Some stellar wind LGRBs with successful prompt emissions have had Lorentz factors as small as $\Gamma_0 \approx 20$ (cite: Ghirlanda_2018). Using standard closure relations from Table 1 of (cite: Zhang_2004b), we can determine if AT 2021lfa is consistent with having a wind medium. For AT 2021lfa, the optical SED index is $\beta = 0.32 \pm 0.46$ (cite: Ho_2022), but the optical temporal index $\alpha$ is uncertain, especially given the large latency (1.79 d) between the last GOTO non-detection (MJD = 59336.311) and first GOTO detection (MJD = 59338.105). Fitting a single power law to the optical light curve, we find $\alpha \in (1.2, 3.8)$. Considering a typical electron energy power law index $p \sim 2.3$ (cite: Zhang_2004b), we obtain values for $\alpha$ and $\beta$ in Table [8](#tab:closure_relations_lfa), finding that a stellar wind origin for AT 2021lfa cannot be ruled out.

AT 2021lfa could also be the result of a dirty fireball.

We estimate the baryon loading of AT 2021lfa with $E_\text{K,iso} = M \Gamma_0 c^2$ (cite: Ghirlanda_2018). From Table [\[tab:lfa-results\]](#tab:lfa-results), we find $M \approx 2.8 \times 10^{-4}$ M$_\odot$ for the top hat model and $M \approx 7.6 \times 10^{-3}$ M$_\odot$ for the Gaussian model, larger than typical LGRB baryon loading values (typically $10^{-6}$ M$_\odot$; (cite: Ghirlanda_2018)) and somewhat larger than the expected baryon loading content required to efficiently produce gamma-rays ($\lesssim 10^{-4}$ M$_\odot$; (cite: Piran_2005)), indicating that AT 2021lfa could be a dirty fireball with strong baryon loading (cite: Rhoads_2003; Huang_2002), and thus low gamma-ray photon production.

### Comparison to Y24

Y24 use `afterglowpy` and `emcee` to model all multi-wavelength observations of AT 2021lfa. Similarly to S22, Y24 fits the burst time $t_0$ independently from other parameters, obtaining $t_{0,\text{Y24}} = 59337.92_{-0.04}^{+0.08}$ MJD, consistent within $1\sigma$ of our estimated burst times. Otherwise, Y24’s physical parameters differ significantly from ours. Notably, Y24 obtain an opening angle $\theta_\text{c} \approx 38^\circ$ and a beaming-corrected blast wave energy $E_K \approx 1.3 \times 10^{54}$ erg, which is 4 orders of magnitude greater than our estimate. These values are larger than those of the vast majority of the LGRB population (cite: Ghirlanda_2005; Laskar_2013b; Goldstein_2016). The discrepancies between Y24 and this work are likely due to a difference in fitting configurations; Y24 use an `afterglowpy` configuration in which $\Gamma_0 = \infty$ and different priors. Despite configuring $\Gamma_0 = \infty$, Y24 constrains $\Gamma \approx 18$ from Equation [\[eq:tdec\]](#eq:tdec) using values from their MCMC fit, which is somewhat larger than our results, but still a remarkably low Lorentz factor.

### Off-axis Interpretation

| Parameter | Initial | Prior (Uniform) |
|:---|:---|:---|
| $t_0$ \[MJD\] | 59338.09 | \[59338.05, 59338.10$^\dag$\] |
| $\theta_\text{v}$ \[rad\] | 0.16 | $[1, 6] \times \theta_\text{c}$ |
| $\log_{10}(E_\text{K,iso}/\text{erg})$ | 53.14 | \[45, 57\] |
| $\theta_\text{c}$ \[rad\] | 0.09 | \[0.02, 0.78\] |
| $\theta_\text{w}$ \[rad\] | 0.15 | $[1, 7] \times \theta_\text{c}$ |
| $\log_{10}(n_0/\text{cm}^{-3})$ | -3.73 | \[-10, 10\] |
| $p$ | 2.79 | \[2, 3\] |
| $b$ | 5 | \[0, 10\] |
| $\log_{10}\epsilon_e$ | -1.59 | \[-5, 0\] |
| $\log_{10}\epsilon_B$ | -1.79 | \[-5, 0\] |
| $\xi_N$ | 0.10 | \[0, 1\] |
| $\log_{10}\Gamma_0$ | 2.30 | \[2, 5\] |

: Values around which the walkers were initialized and priors for the forced off-axis fit. We are aware that priors for $\epsilon_e$ and $\epsilon_B$ allow for $\epsilon_e + \epsilon_B > 1$, but none of the fit results are unphysical. $^\dag$In this table, we truncate the time of the first detection (MJD = $59338.1054282$), but use all decimal places in our MCMC analysis.

AT 2021lfa has a rest-frame rise time $\gtrsim 5600$ s, slower than all upper limits and observed LGRB rise times from (cite: Ghirlanda_2018) and (cite: Hasco_t_2014). Given the relation between $L_{\gamma,\text{iso}}$ and rise time, the rise time of AT 2021lfa would imply that any associated LGRB has $L_{\gamma,\text{iso}} \lesssim 10^{47}$ erg s$^{-1}$ (cite: Ghirlanda_2018) which is consistent with the limit $L_{\gamma,\text{iso}} < 2.6 \times 10^{51}$ erg s$^{-1}$ from (cite: Ho_2022).

Out of all discovered afterglows without associated detected GRBs, AT 2019pim is the only other event with a confirmed comparably long rest-frame rise time between $1800 - 7200$ s. If the rise times of AT 2019pim and AT 2021lfa are due to deceleration viewed on-axis, then it is likely that they are the result of low Lorentz factor jets, as explored in this work and (cite: Perley_2024). On the other hand, their long rise times may be due to being viewed off-axis, in which case a high-$\Gamma_0$ jet is possible. Indeed, this degeneracy is present in (cite: Perley_2024), where an on-axis low-$\Gamma_0$ jet and a slightly off-axis high-$\Gamma_0$ jet are both found as viable solutions for AT 2019pim. We note that if AT 2021lfa’s radio fluctuations are due to interstellar scintillation, then AT 2021lfa’s scintillation timescale would be $\sim 102$ d, favoring a low-$\Gamma_0$ interpretation (see Section [3](#table:analytical-lorentz-factors)). However, fluctuations could be explained by other effects, such as circumstellar density variations between the early and late time emission.

Motivated by AT 2021lfa’s slow rise time, (cite: Perley_2024), and off-axis solutions present in the posterior of the former analysis, we explore an off-axis fit for AT 2021lfa. First, we find a plausible off-axis high-$\Gamma_0$ solution by manually varying `afterglowpy` jet parameters, around which we set our priors, shown in Table [9](#tab:off-axis-prior). We run Gaussian and power law configurations, since only structured jets will be able to capture very off-axis ($\theta_\text{v} \gtrsim 2 \times \theta_\text{c}$) emission. We fit with a finite $\Gamma_0$, no ICC, and use all radio, optical, and X-ray observations. We also ran fits with $\Gamma_0 = \infty$, but they were unsuccessful, typically overestimating optical and radio light curves, especially the rising phase MASTER detections. We present the results of our fitting in Table [10](#tab:lfa-off-axis-results) and Figure [10](#fig:lfa-off-axis-results), with corner plots in Figures [17](#fig:lfa-off-axis-corner-gauss) and [18](#fig:lfa-off-axis-corner-power) in Appendix [10](#app:corner-plots).

| Parameter | Gaussian | Power law |
|:---|:---|:---|
| $t_0$ \[MJD\] | $59338.06_{-0.00}^{+0.01}$ | $59338.08_{-0.01}^{+0.01}$ |
| $\theta_\text{v}$ \[rad\] | $0.06_{-0.01}^{+0.01}$ | $0.13_{-0.01}^{+0.01}$ |
| $\log_{10}(E_\text{K,iso}/\text{erg})$ | $53.14_{-0.27}^{+0.85}$ | $52.41_{-0.23}^{+0.39}$ |
| $\theta_\text{c}$ \[rad\] | $0.03_{-0.00}^{+0.00}$ | $0.10_{-0.01}^{+0.01}$ |
| $\theta_\text{w}$ \[rad\] | $0.15_{-0.06}^{+0.07}$ | $0.11_{-0.01}^{+0.01}$ |
| $\log_{10}(n_0/\text{cm}^{-3})$ | $-2.59_{-0.39}^{+0.77}$ | $-0.16_{-0.43}^{+0.45}$ |
| $p$ | $2.96_{-0.04}^{+0.02}$ | $2.79_{-0.05}^{+0.05}$ |
| $b$ | \- | $4.50_{-3.38}^{+3.74}$ |
| $\log_{10}\epsilon_e$ | $-1.37_{-0.84}^{+0.27}$ | $-0.75_{-0.39}^{+0.22}$ |
| $\log_{10}\epsilon_B$ | $-0.53_{-0.83}^{+0.31}$ | $-1.29_{-0.39}^{+0.27}$ |
| $\xi_N$ | $0.44_{-0.38}^{+0.37}$ | $0.53_{-0.31}^{+0.31}$ |
| $\log_{10}\Gamma_0$ | $2.04_{-0.03}^{+0.05}$ | $2.19_{-0.14}^{+0.26}$ |
| $\eta_\gamma$ | $<0.1-1.6\%$ | $<1.9-7.3\%$ |
| $\chi^2$/DoF | $5.5$ | $5.5$ |
| $\widehat{\text{elpd}}$ | $(1.1 \pm 0.3) \times 10^{2}$ | $(1.2 \pm 0.3) \times 10^{2}$ |

: Final parameters ($68\%$ uncertainty) for the off-axis, finite $\Gamma_0$ jets for AT 2021lfa. We calculate $\eta_\gamma$ using the $1\sigma$ distribution of $E_\text{K,iso}$ and the $E_{\gamma,\text{iso}}$ limits from Table [2](#table:radiative-energies). We present the $\widehat{\text{elpd}}$ and minimum $\chi^2$/DoF over 5,000 posterior samples. Ran with 64 walkers and 225,000 iterations; discarded 125,000.

Both models are consistent with optical observations, but the Gaussian model struggles with the finer features of the rising phase $r$-band detections. The Gaussian fit also includes an optical light curve break at $\sim 0.5$ days, which is not present in the power law fit or the previous on-axis solutions. The models are also consistent with the radio emission at $\Delta t \lesssim 100$ d, similar to the on-axis fits, but underestimate late-time observations at $\gtrsim 110$ d by varying orders of magnitude, at most $\sim 0.5$. By contrast, the on-axis Gaussian solution (see Figure [5](#fig:lcr-results)) is generally consistent with late-time radio detections. This discrepancy may favor a wind environment, which would result in shallower light curves. Additionally, the Gaussian and power law jets underestimate the X-ray detection by $\sim 1.5$ and $\sim 1$ orders of magnitude, respectively. In comparison, the on-axis Gaussian solution is able to reproduce to X-ray detection, although the on-axis top hat model struggles by $\sim 1$ order of magnitude. As previously mentioned, observed X-ray excesses could be due to an ongoing central engine activity (cite: Zhao_2020) or, since AT 2021lfa only has a single X-ray detection, an insufficient $\chi^2$ penalty.

From Table [10](#tab:lfa-off-axis-results), we obtain $\theta_\text{c} \approx 1.7^\circ$ and $\theta_\text{v} \approx 3.4^\circ$ for the Gaussian solution, which is very off-axis ($\theta_\text{v} \approx 2 \times \theta_\text{c}$). For the power law fit, we obtain $\theta_\text{c} \approx 5.7^\circ$ and $\theta_\text{v} \approx 7.5^\circ$, which is less off-axis ($\theta_\text{v} \approx 1.3 \times \theta_\text{c}$). The Gaussian model obtains a beaming-corrected $E_\text{K} \sim 6 \times 10^{49}$ erg while the power law model obtains a somewhat greater $E_\text{K} \sim 10^{50}$ erg, both within typical ranges of LGRB kinetic energies (cite: Yi_2017; Ghirlanda_2018). Both models obtain typical Lorentz factors, the Gaussian jet with $\Gamma_0 \approx 110$ and power law jet with $\Gamma_0 \approx 155$. Lastly, the Gaussian model obtains a possibly low efficiency $\eta_\gamma < 0.1\%$, smaller than $98.5\%$ of bursts in (cite: Racusin_2011).

Generally, the off-axis solutions obtain comparable beaming-corrected kinetic energies ($\sim 10^{50}$ erg), smaller opening angles, and smaller densities to the on-axis fits in Table [\[tab:lfa-results\]](#tab:lfa-results). The off-axis solutions also obtain comparable $\chi^2$/DoFs, but more predictive $\widehat{\text{elpd}}$ scores.

Overall, we find that an off-axis high-$\Gamma_0$ origin for AT 2021lfa cannot be ruled out. The models’ underestimates of late-time radio emission may be due to `afterglowpy`’s lack of jet spreading for the finite $\Gamma_0$ setting, and the observed X-ray excesses may be due an insufficient $\chi^2$ penalty on the single X-ray detection or from ongoing central engine activity (cite: Zhao_2020).

# Conclusion

In this work, we presented the identification and multiwavelength observations of AT 2023lcr, a red, cosmological fast optical transient detected without a GRB trigger. With AT 2023lcr, there are now 10 total afterglows discovered without associated detected GRBs, and six such events with a measured redshift. Using `afterglowpy` and `emcee`, we modeled the multi-wavelength emission of AT 2023lcr and three similarly discovered afterglows, AT 2020blt, AT 2021any, and AT 2021lfa. We found that a classical on-GRB origin cannot be ruled out for AT 2023lcr, AT 2020blt, and AT 2021any.

However, we also found that AT 2020blt and AT 2021any could also be described with non-classical solutions (off-axis and/or low-$\Gamma_0$). The multimodalities in the solution may be due to a lack of detailed early-time data, but could also arise from `emcee`/`afterglowpy` biasing our posteriors to particular locations in parameter space.

Of all afterglows explored in this work, only AT 2021lfa has a convincing non-classical origin, largely motivated by the slow optical rise time. We found that AT 2021lfa is consistent with both on-axis low Lorentz factor ($\Gamma_0 = 5 - 13$) and off-axis high Lorentz factor ($\Gamma_0 \approx 100$) jets.

The long-lasting fluctuations in AT 2021lfa’s radio light curve may favor the low-$\Gamma_0$ solution, implying a smaller radius and therefore slower expansion speed than other events.

We note that without the rise phase of the optical light curve, multiwavelength modeling of AT 2021lfa yields a result consistent with an on-axis classical GRB. Since early-time observations are more sensitive to initial physical conditions, such as the initial Lorentz factor, being able to capture early-time emission is extremely important to constraining an afterglow’s origin.

The upcoming Argus Array (cite: Argus) promises a high sensitivity, high cadence, and wide field of view, so should be well-suited to routinely detect the rising phase.

Our analysis on AT 2021lfa makes it the second afterglow without an associated detected GRB that is consistent with both on-axis low-$\Gamma_0$ and off-axis high-$\Gamma_0$ solutions, the first being AT 2019pim (cite: Perley_2024).

To resolve the degeneracy, a detection of the prompt emission with wide-field X-ray surveys such as Einstein Probe (cite: Einstein_Probe) may be needed. Both dirty fireballs and off-axis GRBs would be expected to be accompanied by an X-ray flash (cite: Heise_2001; Zhang_2004; Sakamoto_2005; Soderberg_2007), but off-axis afterglow emission should be smoother, while on-axis prompt emission should have shorter-timescale variability. In addition, off-axis GRBs are expected to be accompanied by cocoon emission that peaks in the UV (cite: Nakar_2016). Such emission could be detected by the high cadence and sensitivity of the upcoming wide-field survey ULTRASAT (cite: Shvartzvald2024).

# Acknowledgements

M.L.L. was supported in part by a Roger and Mary Lou West Summer Fellowship. A.Y.Q.H. was supported in part by NASA Grant 80NSSC23K1155. We thank Murray Brightman for advice on Chandra data reduction. Research at Perimeter Institute is supported in part by the Government of Canada through the Department of Innovation, Science and Economic Development and by the Province of Ontario through the Ministry of Colleges and Universities. M.W.C acknowledges support from the National Science Foundation with grant numbers PHY-2308862 and PHY-2117997. J.S.B. was partially supported by a grant from the Gordon and Betty Moore Foundation and the National Science Foundation (2206744). N.S. acknowledges support from the Knut and Alice Wallenberg Foundation through the “Gravity Meets Light” project.

Based on observations obtained with the Samuel Oschin Telescope 48-inch and the 60-inch Telescope at the Palomar Observatory as part of the Zwicky Transient Facility project. ZTF is supported by the National Science Foundation under Grant No. AST-2034437 and a collaboration including Caltech, IPAC, the Weizmann Institute of Science, the Oskar Klein Center at Stockholm University, the University of Maryland, Deutsches Elektronen-Synchrotron and Humboldt University, the TANGO Consortium of Taiwan, the University of Wisconsin at Milwaukee, Trinity College Dublin, Lawrence Livermore National Laboratories, IN2P3, University of Warwick, Ruhr University Bochum, Cornell University, and Northwestern University. Operations are conducted by COO, IPAC, and UW.

The ZTF forced-photometry service was funded under the Heising-Simons Foundation grant #12540303 (PI: Graham). The Gordon and Betty Moore Foundation, through both the Data-Driven Investigator Program and a dedicated grant, provided critical funding for SkyPortal.

The Liverpool Telescope is operated on the island of La Palma by Liverpool John Moores University in the Spanish Observatorio del Roque de los Muchachos of the Instituto de Astrofisica de Canarias with financial support from the UK Science and Technology Facilities Council.

This work made use of data from the GROWTH-India Telescope (GIT) set up by the Indian Institute of Astrophysics (IIA) and the Indian Institute of Technology Bombay (IITB). It is located at the Indian Astronomical Observatory (Hanle), operated by IIA. We acknowledge funding by the IITB alumni batch of 1994, which partially supports operations of the telescope. Telescope technical details are available online (cite: Kumar2022). We thank the staff of IAO, Hanle and CREST, Hosakote, that made these obervations possible. The facilities at IAO and CREST are operated by the Indian Institute of Astrophysics, Bangalore.

Some of the data presented herein were obtained at the W. M. Keck Observatory, which is operated as a scientific partnership among the California Institute of Technology, the University of California, and NASA. The Observatory was made possible by the generous financial support of the W. M. Keck Foundation. The authors wish to recognise and acknowledge the very significant cultural role and reverence that the summit of Maunakea has always had within the indigenous Hawaiian community. We are most fortunate to have the opportunity to conduct observations from this mountain.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

GMRT is run by the National Centre for Radio Astrophysics of the Tata Institute of Fundamental Research

The Submillimeter Array is a joint project between the Smithsonian Astrophysical Observatory and the Academia Sinica Institute of Astronomy and Astrophysics and is funded by the Smithsonian Institution and the Academia Sinica.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.A.00025.T. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the NSF operated under cooperative agreement by Associated Universities, Inc.

This work made use of data supplied by the UK Swift Science Data Centre at the University of Leicester. The scientific results reported in this article are based in part on observations made by the *Chandra* X-ray Observatory. This research has made use of software provided by the Chandra X-ray Center (CXC) in the application packages CIAO and Sherpa.

natexlab

(ref: Andreoni2023_AT2023azs) Andreoni, I., Kumar, H., Coughlin, M., et al. 2023, GRB Coordinates Network, 33229, 1

(ref: Andreoni2021) Andreoni, I., Coughlin, M. W., Kool, E. C., et al. 2021, ApJ, 918, 63, doi: [`10.3847/1538-4357/ac0bc7`](http://doi.org/10.3847/1538-4357/ac0bc7)

(ref: Aptekar1995) Aptekar, R. L., Frederiks, D. D., Golenetskii, S. V., et al. 1995, Space Sci. Rev., 71, 265, doi: [`10.1007/BF00751332`](http://doi.org/10.1007/BF00751332)

(ref: Barniol_Duran_2013) Barniol Duran, R., Nakar, E., & Piran, T. 2013, The Astrophysical Journal, 772, 78, doi: [`10.1088/0004-637x/772/1/78`](http://doi.org/10.1088/0004-637x/772/1/78)

(ref: Barthelmy2005) Barthelmy, S. D., Barbier, L. M., Cummings, J. R., et al. 2005, Space Sci. Rev., 120, 143, doi: [`10.1007/s11214-005-5096-3`](http://doi.org/10.1007/s11214-005-5096-3)

(ref: Bellm2019_ztf) Bellm, E. C., Kulkarni, S. R., Graham, M. J., et al. 2019a, PASP, 131, 018002, doi: [`10.1088/1538-3873/aaecbe`](http://doi.org/10.1088/1538-3873/aaecbe)

(ref: Bellm2019_surveys) Bellm, E. C., Kulkarni, S. R., Barlow, T., et al. 2019b, PASP, 131, 068003, doi: [`10.1088/1538-3873/ab0c2a`](http://doi.org/10.1088/1538-3873/ab0c2a)

(ref: Beuermann1999) Beuermann, K., Hessman, F. V., Reinsch, K., et al. 1999, A&A, 352, L26. [`https://arxiv.org/abs/astro-ph/9909043`](https://arxiv.org/abs/astro-ph/9909043)

(ref: Burrows2005) Burrows, D. N., Hill, J. E., Nousek, J. A., et al. 2005, Space Sci. Rev., 120, 165, doi: [`10.1007/s11214-005-5097-2`](http://doi.org/10.1007/s11214-005-5097-2)

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Cenko_2013) Cenko, S. B., Kulkarni, S. R., Horesh, A., et al. 2013, The Astrophysical Journal, 769, 130, doi: [`10.1088/0004-637X/769/2/130`](http://doi.org/10.1088/0004-637X/769/2/130)

(ref: SkyPortal) Coughlin, M. W., Bloom, J. S., Nir, G., et al. 2023, The Astrophysical Journal Supplement Series, 267, 31, doi: [`10.3847/1538-4365/acdee1`](http://doi.org/10.3847/1538-4365/acdee1)

(ref: Cummings_2005) Cummings, J., Angelini, L., Barthelmy, S., et al. 2005, GRB Coordinates Network, 3910, 1

(ref: Cunningham_2020) Cunningham, V., Cenko, S. B., Ryan, G., et al. 2020, The Astrophysical Journal, 904, 166, doi: [`10.3847/1538-4357/abc2cd`](http://doi.org/10.3847/1538-4357/abc2cd)

(ref: deUgartePostigo2023_AT2023sva) de Ugarte Postigo, A., Malesani, D. B., Agui Fernandez, J. F., Thoene, C. C., & Geier, S. 2023, GRB Coordinates Network, 34740, 1

(ref: Dekany2020) Dekany, R., Smith, R. M., Riddle, R., et al. 2020, PASP, 132, 038001, doi: [`10.1088/1538-3873/ab4ca2`](http://doi.org/10.1088/1538-3873/ab4ca2)

(ref: Dermer_1999) Dermer, C. D., Chiang, J., & Bottcher, M. 1999, The Astrophysical Journal, 513, 656–668, doi: [`10.1086/306871`](http://doi.org/10.1086/306871)

(ref: sherpa2) Doe, S., Nguyen, D., Stawarz, C., et al. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 543

(ref: Evans2007) Evans, P. A., Beardmore, A. P., Page, K. L., et al. 2007, A&A, 469, 379, doi: [`10.1051/0004-6361:20077530`](http://doi.org/10.1051/0004-6361:20077530)

(ref: Evans2009) —. 2009, MNRAS, 397, 1177, doi: [`10.1111/j.1365-2966.2009.14913.x`](http://doi.org/10.1111/j.1365-2966.2009.14913.x)

(ref: Foreman_Mackey_2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, Publications of the Astronomical Society of the Pacific, 125, 306–312, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: sherpa1) Freeman, P., Doe, S., & Siemiginowska, A. 2001, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 4477, Astronomical Data Analysis, ed. J.-L. Starck & F. D. Murtagh, 76–87, doi: [`10.1117/12.447161`](http://doi.org/10.1117/12.447161)

(ref: Fruscione2006) Fruscione, A., McDowell, J. C., Allen, G. E., et al. 2006, Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 6270, CIAO: Chandra’s data analysis system, 62701V, doi: [`10.1117/12.671760`](http://doi.org/10.1117/12.671760)

(ref: Fulton2023) Fulton, M. D., Smartt, S. J., Chen, T. W., et al. 2023, Transient Name Server AstroNote, 179, 1

(ref: Galama_2003) Galama, T. J., Frail, D. A., Sari, R., et al. 2003, The Astrophysical Journal, 585, 899–907, doi: [`10.1086/346083`](http://doi.org/10.1086/346083)

(ref: Garmire2003) Garmire, G. P., Bautz, M. W., Ford, P. G., Nousek, J. A., & Ricker, George R., J. 2003, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 4851, X-Ray and Gamma-Ray Telescopes and Instruments for Astronomy., ed. J. E. Truemper & H. D. Tananbaum, 28–44, doi: [`10.1117/12.461599`](http://doi.org/10.1117/12.461599)

(ref: Geng_2013) Geng, J. J., Wu, X. F., Huang, Y. F., & Yu, Y. B. 2013, The Astrophysical Journal, 779, 28, doi: [`10.1088/0004-637X/779/1/28`](http://doi.org/10.1088/0004-637X/779/1/28)

(ref: Ghirlanda_2005) Ghirlanda, G., Ghisellini, G., & Firmani, C. 2005, Monthly Notices of the Royal Astronomical Society: Letters, 361, L10–L14, doi: [`10.1111/j.1745-3933.2005.00053.x`](http://doi.org/10.1111/j.1745-3933.2005.00053.x)

(ref: Ghirlanda_2018) Ghirlanda, G., et al. 2018, Astronomy & Astrophysics, 609, A112, doi: [`10.1051/0004-6361/201731598`](http://doi.org/10.1051/0004-6361/201731598)

(ref: Goldstein_2016) Goldstein, A., Connaughton, V., Briggs, M. S., & Burns, E. 2016, The Astrophysical Journal, 818, 18, doi: [`10.3847/0004-637x/818/1/18`](http://doi.org/10.3847/0004-637x/818/1/18)

(ref: Gompertz2023) Gompertz, B., Ackley, K., Ramsay, G., et al. 2023, GRB Coordinates Network, 34023, 1

(ref: Graham2019) Graham, M. J., Kulkarni, S. R., Bellm, E. C., et al. 2019, PASP, 131, 078001, doi: [`10.1088/1538-3873/ab006c`](http://doi.org/10.1088/1538-3873/ab006c)

(ref: Gupta_2022) Gupta, R., Kumar, A., Pandey, S. B., et al. 2022, Journal of Astrophysics and Astronomy, 43, 11, doi: [`10.1007/s12036-021-09794-4`](http://doi.org/10.1007/s12036-021-09794-4)

(ref: Haislip_2006) Haislip, J. B., Nysewander, M. C., Reichart, D. E., et al. 2006, Nature, 440, 181, doi: [`10.1038/nature04552`](http://doi.org/10.1038/nature04552)

(ref: Hasco_t_2014) Hascoët, R., Beloborodov, A. M., Daigne, F., & Mochkovitch, R. 2014, The Astrophysical Journal, 782, 5, doi: [`10.1088/0004-637x/782/1/5`](http://doi.org/10.1088/0004-637x/782/1/5)

(ref: Heise_2001) Heise, J., Zand, J. i. t., Kippen, R. M., & Woods, P. M. 2001, in Gamma-Ray Bursts in the Afterglow Era, ed. E. Costa, F. Frontera, & J. Hjorth (Berlin, Heidelberg: Springer Berlin Heidelberg), 16–21

(ref: Hjorth_2011) Hjorth, J., & Bloom, J. S. 2011, The Gamma-Ray Burst - Supernova Connection. [`https://arxiv.org/abs/1104.2274`](https://arxiv.org/abs/1104.2274)

(ref: Ho2023_AT2023avj) Ho, A. Y. Q. 2023, GRB Coordinates Network, 33238, 1

(ref: Ho_2020) Ho, A. Y. Q., et al. 2020, The Astrophysical Journal, 905, 98, doi: [`10.3847/1538-4357/abc34d`](http://doi.org/10.3847/1538-4357/abc34d)

(ref: Ho_2022) —. 2022, The Astrophysical Journal, 938, 85, doi: [`10.3847/1538-4357/ac8bd0`](http://doi.org/10.3847/1538-4357/ac8bd0)

(ref: Huang_2006_grbmodel2) Huang, Y. F., Cheng, K. S., & Gao, T. T. 2006, The Astrophysical Journal, 637, 873, doi: [`10.1086/498423`](http://doi.org/10.1086/498423)

(ref: Huang_2002_grbmodel1) Huang, Y. F., Dai, Z. G., & Lu, T. 2000, MNRAS, 316, 943, doi: [`10.1046/j.1365-8711.2000.03683.x`](http://doi.org/10.1046/j.1365-8711.2000.03683.x)

(ref: Huang_2002) Huang, Y. F., Dai, Z. G., & Lu, T. 2002, Monthly Notices of the Royal Astronomical Society, 332, 735, doi: [`10.1046/j.1365-8711.2002.05334.x`](http://doi.org/10.1046/j.1365-8711.2002.05334.x)

(ref: Kobayashi_2000) Kobayashi, S., & Sari, R. 2000, ApJ, 542, 819, doi: [`10.1086/317021`](http://doi.org/10.1086/317021)

(ref: Kumar2022) Kumar, H., Bhalerao, V., Anupama, G. C., et al. 2022, AJ, 164, 90, doi: [`10.3847/1538-3881/ac7bea`](http://doi.org/10.3847/1538-3881/ac7bea)

(ref: Kumar_1999) Kumar, P. 1999, The Astrophysical Journal, 523, L113–L116, doi: [`10.1086/312265`](http://doi.org/10.1086/312265)

(ref: Kumar_2015) Kumar, P., & Zhang, B. 2015, Physics Reports, 561, 1–109, doi: [`10.1016/j.physrep.2014.09.008`](http://doi.org/10.1016/j.physrep.2014.09.008)

(ref: Laskar_2013b) Laskar, T., Berger, E., Tanvir, N., et al. 2013, The Astrophysical Journal, 781, 1, doi: [`10.1088/0004-637x/781/1/1`](http://doi.org/10.1088/0004-637x/781/1/1)

(ref: Laskar_2016) Laskar, T., Alexander, K. D., Berger, E., et al. 2016, The Astrophysical Journal, 833, 88, doi: [`10.3847/1538-4357/833/1/88`](http://doi.org/10.3847/1538-4357/833/1/88)

(ref: Law_2009) Law, N. M., Kulkarni, S. R., Dekany, R. G., et al. 2009, Publications of the Astronomical Society of the Pacific, 121, 1395–1408, doi: [`10.1086/648598`](http://doi.org/10.1086/648598)

(ref: Argus) Law, N. M., Corbett, H., Galliher, N. W., et al. 2022, PASP, 134, 035003, doi: [`10.1088/1538-3873/ac4811`](http://doi.org/10.1088/1538-3873/ac4811)

(ref: Lipunov_2022) Lipunov, V., Kornilov, V., Zhirkov, K., et al. 2022, Monthly Notices of the Royal Astronomical Society, 516, 4980–4987, doi: [`10.1093/mnras/stac1906`](http://doi.org/10.1093/mnras/stac1906)

(ref: lcr-supernova-photometry) Martin-Carrillo, A., Schneider, B., Laskar, T., et al. 2023a, GRB Coordinates Network, 34370, 1

(ref: lcr-supernova-spectrum) Martin-Carrillo, A., Levan, A. J., de Ugarte Postigo, A., et al. 2023b, Transient Name Server Classification Report, 2023-1961, 1

(ref: Masci2019) Masci, F. J., Laher, R. R., Rusholme, B., et al. 2019, PASP, 131, 018003, doi: [`10.1088/1538-3873/aae8ac`](http://doi.org/10.1088/1538-3873/aae8ac)

(ref: Meegan2009) Meegan, C., Lichti, G., Bhat, P. N., et al. 2009, ApJ, 702, 791, doi: [`10.1088/0004-637X/702/1/791`](http://doi.org/10.1088/0004-637X/702/1/791)

(ref: Meszaros_2006) Mészáros, P. 2006, Reports on Progress in Physics, 69, 2259–2321, doi: [`10.1088/0034-4885/69/8/r01`](http://doi.org/10.1088/0034-4885/69/8/r01)

(ref: Nakar_2016) Nakar, E., & Piran, T. 2016, The Astrophysical Journal, 834, 28, doi: [`10.3847/1538-4357/834/1/28`](http://doi.org/10.3847/1538-4357/834/1/28)

(ref: Oke1995) Oke, J. B., Cohen, J. G., Carr, M., et al. 1995, PASP, 107, 375, doi: [`10.1086/133562`](http://doi.org/10.1086/133562)

(ref: Panaitescu_2001) Panaitescu, A., & Kumar, P. 2001, The Astrophysical Journal, 560, L49–L53, doi: [`10.1086/324061`](http://doi.org/10.1086/324061)

(ref: Perley2019lpipe) Perley, D. A. 2019, PASP, 131, 084503, doi: [`10.1088/1538-3873/ab215d`](http://doi.org/10.1088/1538-3873/ab215d)

(ref: Perley2023_AT2023azs) —. 2023, GRB Coordinates Network, 33253, 1

(ref: Perley_2024) Perley, D. A., Ho, A. Y. Q., Fausnaugh, M., et al. 2024, AT2019pim: A Luminous Orphan Afterglow from a Moderately Relativistic Outflow. [`https://arxiv.org/abs/2401.16470`](https://arxiv.org/abs/2401.16470)

(ref: Perley2011) Perley, R. A., Chandler, C. J., Butler, B. J., & Wrobel, J. M. 2011, ApJL, 739, L1, doi: [`10.1088/2041-8205/739/1/L1`](http://doi.org/10.1088/2041-8205/739/1/L1)

(ref: Piran_2005) Piran, T. 2005, Reviews of Modern Physics, 76, 1143–1210, doi: [`10.1103/revmodphys.76.1143`](http://doi.org/10.1103/revmodphys.76.1143)

(ref: Planck_2020) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6, doi: [`10.1051/0004-6361/201833910`](http://doi.org/10.1051/0004-6361/201833910)

(ref: Racusin_2011) Racusin, J. L., Oates, S. R., Schady, P., et al. 2011, ApJ, 738, 138, doi: [`10.1088/0004-637X/738/2/138`](http://doi.org/10.1088/0004-637X/738/2/138)

(ref: Rhoads1997) Rhoads, J. E. 1997, ApJL, 487, L1, doi: [`10.1086/310876`](http://doi.org/10.1086/310876)

(ref: Rhoads_2003) Rhoads, J. E. 2003, The Astrophysical Journal, 591, 1097–1103, doi: [`10.1086/368125`](http://doi.org/10.1086/368125)

(ref: Rhodes2023_AT2023sva) Rhodes, L., Fender, R., Green, D., & Titterington, D. 2023, GRB Coordinates Network, 34796, 1

(ref: Ridnaia2023) Ridnaia, A., Frederiks, D., Lysenko, A., et al. 2023, GRB Coordinates Network, 34051, 1

(ref: Ridnaia_2023) Ridnaia, A., et al. 2023, ZTF23aaoohpy (AT2023lcr/ATLAS23msn): Upper limits from Konus-Wind observations. <https://gcn.nasa.gov/circulars/34051>

(ref: Roberts2023_AT2023sva) Roberts, O. J., Bala, S., Meegan, C., & Fermi GBM Team. 2023, GRB Coordinates Network, 34748, 1

(ref: Ruderman_1975) Ruderman, M. 1975, in Seventh Texas Symposium on Relativistic Astrophysics, ed. P. G. Bergman, E. J. Fenyves, & L. Motz, Vol. 262, 164–180, doi: [`10.1111/j.1749-6632.1975.tb31430.x`](http://doi.org/10.1111/j.1749-6632.1975.tb31430.x)

(ref: Ryan_2020) Ryan, G., Eerten, H. v., Piro, L., & Troja, E. 2020, The Astrophysical Journal, 896, 166, doi: [`10.3847/1538-4357/ab93cf`](http://doi.org/10.3847/1538-4357/ab93cf)

(ref: Sakamoto_2005) Sakamoto, T., Lamb, D. Q., Kawai, N., et al. 2005, The Astrophysical Journal, 629, 311, doi: [`10.1086/431235`](http://doi.org/10.1086/431235)

(ref: Salvaterra_2009) Salvaterra, R., Valle, M. D., Campana, S., et al. 2009, Nature, 461, 1258–1260, doi: [`10.1038/nature08445`](http://doi.org/10.1038/nature08445)

(ref: Sarin_2022) Sarin, N., Hamburg, R., Burns, E., et al. 2022, Monthly Notices of the Royal Astronomical Society, 512, 1391–1399, doi: [`10.1093/mnras/stac601`](http://doi.org/10.1093/mnras/stac601)

(ref: Schlafly2011) Schlafly, E. F., & Finkbeiner, D. P. 2011, ApJ, 737, 103, doi: [`10.1088/0004-637X/737/2/103`](http://doi.org/10.1088/0004-637X/737/2/103)

(ref: Schlegel_1998) Schlegel, D. J., Finkbeiner, D. P., & Davis, M. 1998, The Astrophysical Journal, 500, 525–553, doi: [`10.1086/305772`](http://doi.org/10.1086/305772)

(ref: Schulze_2010) Schulze, S., Klose, S., Björnsson, G., et al. 2010, Astronomy & Astrophysics, 526, A23, doi: [`10.1051/0004-6361/201015581`](http://doi.org/10.1051/0004-6361/201015581)

(ref: Sfaradi2023_AT2023jxk) Sfaradi, I., Horesh, A., Rhodes, L., et al. 2023, Transient Name Server AstroNote, 237, 1

(ref: Shvartzvald2024) Shvartzvald, Y., Waxman, E., Gal-Yam, A., et al. 2024, ApJ, 964, 74, doi: [`10.3847/1538-4357/ad2704`](http://doi.org/10.3847/1538-4357/ad2704)

(ref: Soderberg_2007) Soderberg, A. M., Nakar, E., Cenko, S. B., et al. 2007, The Astrophysical Journal, 661, 982, doi: [`10.1086/515562`](http://doi.org/10.1086/515562)

(ref: dynesty) Speagle, J. S. 2020, Monthly Notices of the Royal Astronomical Society, 493, 3132–3158, doi: [`10.1093/mnras/staa278`](http://doi.org/10.1093/mnras/staa278)

(ref: 2023sva) Srinivasaragavan, G. P., Perley, D. A., Ho, A. Y. Q., et al. 2025, Monthly Notices of the Royal Astronomical Society, 538, 351, doi: [`10.1093/mnras/staf290`](http://doi.org/10.1093/mnras/staf290)

(ref: Steeghs2022) Steeghs, D., Galloway, D. K., Ackley, K., et al. 2022, MNRAS, 511, 2405, doi: [`10.1093/mnras/stac013`](http://doi.org/10.1093/mnras/stac013)

(ref: Steele2004) Steele, I. A., Smith, R. J., Rees, P. C., et al. 2004, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 5489, Proc. SPIE, ed. J. Oschmann, Jacobus M., 679–692, doi: [`10.1117/12.551456`](http://doi.org/10.1117/12.551456)

(ref: lcr-swain) Swain, V., Andreoni, I., Coughlin, M., Kumar, H., & Salgundi, A. 2023a, Transient Name Server AstroNote, 178, 1

(ref: Swain2023) Swain, V., Andreoni, I., Coughlin, M., et al. 2023b, GRB Coordinates Network, 34022, 1

(ref: Tagliaferri_2005) Tagliaferri, G., Antonelli, L. A., Chincarini, G., et al. 2005, A&A, 443, L1, doi: [`10.1051/0004-6361:200500196`](http://doi.org/10.1051/0004-6361:200500196)

(ref: Tanvir_2009) Tanvir, N. R., Fox, D. B., Levan, A. J., et al. 2009, Nature, 461, 1254–1257, doi: [`10.1038/nature08459`](http://doi.org/10.1038/nature08459)

(ref: Tonry2023) Tonry, J., Denneau, L., Weiland, H., et al. 2023, Transient Name Server Discovery Report, 2023-1419, 1

(ref: Tonry2018) Tonry, J. L., Denneau, L., Heinze, A. N., et al. 2018, PASP, 130, 064505, doi: [`10.1088/1538-3873/aabadf`](http://doi.org/10.1088/1538-3873/aabadf)

(ref: Totani_2002) Totani, T., & Panaitescu, A. 2002, The Astrophysical Journal, 576, 120–134, doi: [`10.1086/341738`](http://doi.org/10.1086/341738)

(ref: Vail2023_AT2023jxk) Vail, J., Li, M., Ho, A., et al. 2023a, GRB Coordinates Network, 33934, 1

(ref: Vail2023_AT2023sva) Vail, J. L., Li, M. L., Wise, J., et al. 2023b, GRB Coordinates Network, 34730, 1

(ref: vanderWalt2019) van der Walt, S., Crellin-Quick, A., & Bloom, J. 2019, The Journal of Open Source Software, 4, 1247, doi: [`10.21105/joss.01247`](http://doi.org/10.21105/joss.01247)

(ref: single-shell) van Eerten, H., Zhang, W., & MacFadyen, A. 2010, ApJ, 722, 235, doi: [`10.1088/0004-637X/722/1/235`](http://doi.org/10.1088/0004-637X/722/1/235)

(ref: Walker_2001) Walker, M. A. 2001, Monthly Notices of the Royal Astronomical Society, 321, 176, doi: [`10.1046/j.1365-8711.2001.04104.x`](http://doi.org/10.1046/j.1365-8711.2001.04104.x)

(ref: Wang2023_AT2023avj) Wang, K., Ho, A. Y. Q., Perley, D., & Transient Facility, Z. C. 2023, GRB Coordinates Network, 33226, 1

(ref: Wang_2013) Wang, L.-J., & Dai, Z.-G. 2013, The Astrophysical Journal, 774, L33, doi: [`10.1088/2041-8205/774/2/l33`](http://doi.org/10.1088/2041-8205/774/2/l33)

(ref: Watanabe_2010) Watanabe, S. 2010, Asymptotic Equivalence of Bayes Cross Validation and Widely Applicable Information Criterion in Singular Learning Theory. [`https://arxiv.org/abs/1004.2316`](https://arxiv.org/abs/1004.2316)

(ref: Wu_2013) Wu, X.-F., Gao, H., Ding, X., et al. 2013, The Astrophysical Journal, 781, L10, doi: [`10.1088/2041-8205/781/1/l10`](http://doi.org/10.1088/2041-8205/781/1/l10)

(ref: Xu_2022) Xu, F., Geng, J.-J., Wang, X., Li, L., & Huang, Y.-F. 2022, MNRAS, 509, 4916, doi: [`10.1093/mnras/stab3342`](http://doi.org/10.1093/mnras/stab3342)

(ref: Xu_2023) Xu, F., Huang, Y.-F., & Geng, J.-J. 2023, Astronomy & Astrophysics, 679, A103, doi: [`10.1051/0004-6361/202346674`](http://doi.org/10.1051/0004-6361/202346674)

(ref: Ye_2024) Ye, X.-M., Wei, D.-M., Zhu, Y.-M., & Jin, Z.-P. 2024, Research in Astronomy & Astrophysics, 24, 045011, doi: [`10.1088/1674-4527/ad2b39`](http://doi.org/10.1088/1674-4527/ad2b39)

(ref: Yi_2017) Yi, S.-X., Lei, W.-H., Zhang, B., et al. 2017, Journal of High Energy Astrophysics, 13-14, 1, doi: [`https://doi.org/10.1016/j.jheap.2017.01.001`](http://doi.org/https://doi.org/10.1016/j.jheap.2017.01.001)

(ref: Einstein_Probe) Yuan, W., Zhang, C., Chen, Y., & Ling, Z. 2022, The Einstein Probe Mission (Springer Nature Singapore), 1–30, doi: [`10.1007/978-981-16-4544-0_151-1`](http://doi.org/10.1007/978-981-16-4544-0_151-1)

(ref: Zeh2006) Zeh, A., Klose, S., & Kann, D. A. 2006, ApJ, 637, 889, doi: [`10.1086/498442`](http://doi.org/10.1086/498442)

(ref: Zhang_2004b) Zhang, B., & Mészáros, P. 2004, International Journal of Modern Physics A, 19, 2385–2472, doi: [`10.1142/s0217751x0401746x`](http://doi.org/10.1142/s0217751x0401746x)

(ref: Zhang_2004) Zhang, W., Woosley, S. E., & Heger, A. 2004, The Astrophysical Journal, 608, 365, doi: [`10.1086/386300`](http://doi.org/10.1086/386300)

(ref: Zhao_2020) Zhao, L., Liu, L., Gao, H., et al. 2020, The Astrophysical Journal, 896, doi: [`10.3847/1538-4357/ab8f91`](http://doi.org/10.3847/1538-4357/ab8f91)

# Optical data

| Start Date (MJD) | Instrument$^{a}$ | Filter | Mag$^{b}$      |
|:-----------------|:-----------------|:-------|:---------------|
| 60112.26888      | P48              | $r$    | $>21.61$       |
| 60112.30249      | P48              | $r$    | $>21.63$       |
| 60112.31690      | P48              | $i$    | $>20.76$       |
| 60112.36221      | P48              | $g$    | $>21.67$       |
| 60112.40275      | P48              | $g$    | $>21.54$       |
| 60113.27531      | P48              | $g$    | $19.63\pm0.05$ |
| 60113.32655      | P48              | $g$    | $19.57\pm0.05$ |
| 60113.33749      | P48              | $r$    | $19.29\pm0.04$ |
| 60113.36493      | P48              | $r$    | $19.17\pm0.04$ |
| 60114.26641      | P48              | $g$    | $20.53\pm0.15$ |
| 60114.27940      | P48              | $g$    | $20.73\pm0.16$ |
| 60114.32899      | P48              | $r$    | $20.35\pm0.12$ |
| 60114.34106      | P48              | $r$    | $20.36\pm0.10$ |
| 60114.35403      | P48              | $r$    | $20.24\pm0.10$ |
| 60114.40855      | P48              | $g$    | $20.75\pm0.17$ |
| 60114.73413      | GIT              | $r$    | $20.67\pm0.06$ |
| 60114.77990      | GIT              | $g$    | $21.37\pm0.15$ |
| 60114.80649      | GIT              | $i$    | $20.70\pm0.16$ |
| 60114.92765      | LT               | $g$    | $21.32\pm0.08$ |
| 60114.93103      | LT               | $r$    | $20.88\pm0.06$ |
| 60114.93440      | LT               | $i$    | $20.68\pm0.06$ |
| 60114.94962      | LT               | $r$    | $21.04\pm0.06$ |
| 60114.95300      | LT               | $z$    | $20.47\pm0.10$ |
| 60114.95733      | LT               | $u$    | $22.31\pm0.68$ |
| 60115.27025      | P48              | $g$    | $>21.65$       |
| 60115.29196      | P48              | $i$    | $>21.09$       |
| 60115.31154      | P48              | $r$    | $>21.54$       |
| 60115.35355      | P48              | $r$    | $20.98\pm0.19$ |
| 60115.43086      | P48              | $g$    | $>21.30$       |
| 60115.70108      | GIT              | $r$    | $21.26\pm0.08$ |
| 60116.00182      | LT               | $g$    | $21.77\pm0.22$ |
| 60116.00592      | LT               | $r$    | $21.53\pm0.14$ |
| 60116.00928      | LT               | $i$    | $21.40\pm0.16$ |
| 60116.01265      | LT               | $z$    | $21.14\pm0.20$ |
| 60116.71280      | GIT              | $r$    | $21.79\pm0.08$ |
| 60117.02526      | LT               | $g$    | $22.14\pm0.21$ |
| 60117.03004      | LT               | $r$    | $21.89\pm0.18$ |
| 60117.03410      | LT               | $i$    | $21.64\pm0.19$ |
| 60117.68238      | GIT              | $g$    | $>21.86$       |
| 60117.74601      | GIT              | $r$    | $21.92\pm0.17$ |
| 60117.97296      | LT               | $i$    | $22.21\pm0.25$ |
| 60117.97904      | LT               | $r$    | $22.04\pm0.20$ |
| 60117.98509      | LT               | $g$    | $22.34\pm0.24$ |
| 60118.70342      | GIT              | $r$    | $22.24\pm0.10$ |
| 60118.99971      | LT               | $i$    | $22.62\pm0.28$ |
| 60119.00955      | LT               | $r$    | $22.93\pm0.27$ |
| 60119.01938      | LT               | $g$    | $23.28\pm0.38$ |
| 60119.82540      | HCT              | $r$    | $22.74\pm0.18$ |
| 60120.02784      | LT               | $i$    | $23.15\pm0.40$ |
| 60120.03768      | LT               | $r$    | $22.68\pm0.24$ |
| 60120.04750      | LT               | $g$    | $23.59\pm0.40$ |

: Optical photometry of AT 2023lcr.

Table notes: $^{a}$ P48: Palomar Observatory 48-inch Samuel Oschin Telescope; GIT: GROWTH-India Telescope; LT: Liverpool Telescope. $^{b}$ Not corrected for Milky Way extinction

# Radio data

| Epoch | Start MJD | Instrument$^{b}$ | $\nu_\mathrm{obs}$ (GHz) | $f_\nu$ ($\mu$Jy) |
|:--:|:---|:---|:---|:---|
| 1 | 60116.26547 | VLA | 8.5 | $109\pm9$ |
| 1 | 60116.26547 | VLA | 9.5 | $140\pm9$ |
| 1 | 60116.26547 | VLA | 10.5 | $164\pm9$ |
| 1 | 60116.26547 | VLA | 11.5 | $282\pm11$ |
| 2 | 60117.26563 | VLA | 4.5 | $267\pm11$ |
| 2 | 60117.26563 | VLA | 5.5 | $256\pm11$ |
| 2 | 60117.26563 | VLA | 6.5 | $257\pm10$ |
| 2 | 60117.26563 | VLA | 7.5 | $375\pm10$ |
| 2 | 60117.28324 | VLA | 8.5 | $561\pm11$ |
| 2 | 60117.28324 | VLA | 9.5 | $625\pm10$ |
| 2 | 60117.28324 | VLA | 10.5 | $666\pm11$ |
| 2 | 60117.28324 | VLA | 11.5 | $710\pm12$ |
| 2 | 60117.30085 | VLA | 2.2 | $48\pm21$ |
| 2 | 60117.30085 | VLA | 2.8 | $35\pm19$ |
| 2 | 60117.30085 | VLA | 3.2 | $151\pm16$ |
| 2 | 60117.30085 | VLA | 3.8 | $227\pm16$ |
|  | 60119.14653 | SMA | 230.0 | $<600$ |
| 3 | 60119.29234 | VLA | 13.0 | $631\pm11$ |
| 3 | 60119.29234 | VLA | 15.0 | $672\pm10$ |
| 3 | 60119.29234 | VLA | 17.0 | $699\pm13$ |
| 3 | 60119.30164 | VLA | 4.5 | $298\pm14$ |
| 3 | 60119.30164 | VLA | 5.5 | $382\pm12$ |
| 3 | 60119.30164 | VLA | 6.5 | $356\pm11$ |
| 3 | 60119.30164 | VLA | 7.5 | $374\pm11$ |
| 3 | 60119.31363 | VLA | 8.5 | $516\pm12$ |
| 3 | 60119.31363 | VLA | 9.5 | $582\pm12$ |
| 3 | 60119.31363 | VLA | 10.5 | $621\pm12$ |
| 3 | 60119.31363 | VLA | 11.5 | $677\pm13$ |
| 3 | 60119.32570 | VLA | 2.2 | $108\pm21$ |
| 3 | 60119.32570 | VLA | 2.8 | $112\pm18$ |
| 3 | 60119.32570 | VLA | 3.2 | $192\pm16$ |
| 3 | 60119.32570 | VLA | 3.8 | $218\pm15$ |
| 4 | 60122.25104 | VLA | 4.5 | $144\pm14$ |
| 4 | 60122.25104 | VLA | 5.5 | $200\pm14$ |
| 4 | 60122.25104 | VLA | 6.5 | $242\pm12$ |
| 4 | 60122.25104 | VLA | 7.5 | $290\pm12$ |
| 4 | 60122.25556 | VLA | 5.0 | $151\pm14$ |
| 4 | 60122.25556 | VLA | 7.0 | $235\pm13$ |
| 4 | 60122.25754 | VLA | 1.4 | $83\pm25$ |
| 4 | 60122.25754 | VLA | 1.8 | $52\pm18$ |
| 4 | 60122.28969 | VLA | 2.2 | $102\pm21$ |
| 4 | 60122.28969 | VLA | 2.8 | $100\pm18$ |
| 4 | 60122.28969 | VLA | 3.2 | $151\pm16$ |
| 4 | 60122.28969 | VLA | 3.8 | $153\pm16$ |
| 4 | 60122.30117 | VLA | 8.5 | $352\pm13$ |
| 4 | 60122.30117 | VLA | 9.5 | $396\pm8$ |
| 4 | 60122.30117 | VLA | 10.5 | $394\pm13$ |
| 4 | 60122.30117 | VLA | 11.5 | $412\pm14$ |
| 4 | 60122.31543 | VLA | 19.0 | $410\pm14$ |
| 4 | 60122.31543 | VLA | 21.0 | $432\pm21$ |
| 4 | 60122.31543 | VLA | 23.0 | $372\pm36$ |
| 4 | 60122.31543 | VLA | 25.0 | $376\pm19$ |
| 4 | 60122.34082 | VLA | 30.0 | $292\pm21$ |
| 4 | 60122.34082 | VLA | 32.0 | $340\pm25$ |
| 4 | 60122.34082 | VLA | 34.0 | $370\pm24$ |
| 4 | 60122.34082 | VLA | 36.0 | $316\pm26$ |
| 4 | 60122.36696 | VLA | 13.0 | $405\pm13$ |
| 4 | 60122.36696 | VLA | 15.0 | $387\pm13$ |
| 4 | 60122.36696 | VLA | 17.0 | $395\pm17$ |
| 4 | 60122.37847 | VLA | 5.0 | $195\pm14$ |
| 4 | 60122.37847 | VLA | 7.0 | $299\pm12$ |
| 5 | 60123.23863 | VLA | 4.5 | $322\pm13$ |
| 5 | 60123.23863 | VLA | 5.5 | $435\pm13$ |
| 5 | 60123.23863 | VLA | 6.5 | $559\pm12$ |
| 5 | 60123.23863 | VLA | 7.5 | $613\pm12$ |
| 5 | 60123.24306 | VLA | 5.0 | $347\pm12$ |
| 5 | 60123.24306 | VLA | 7.0 | $514\pm12$ |
| 5 | 60123.24511 | VLA | 1.4 | $85\pm21$ |
| 5 | 60123.24511 | VLA | 1.8 | $84\pm17$ |
| 5 | 60123.27727 | VLA | 2.2 | $112\pm17$ |
| 5 | 60123.27727 | VLA | 2.8 | $123\pm15$ |
| 5 | 60123.27727 | VLA | 3.2 | $222\pm14$ |
| 5 | 60123.27727 | VLA | 3.8 | $246\pm12$ |
| 5 | 60123.29294 | VLA | 8.5 | $690\pm14$ |
| 5 | 60123.29294 | VLA | 9.5 | $705\pm13$ |
| 5 | 60123.29294 | VLA | 10.5 | $643\pm10$ |
| 5 | 60123.29294 | VLA | 11.5 | $635\pm15$ |
| 5 | 60123.31137 | VLA | 19.0 | $382\pm14$ |
| 5 | 60123.31137 | VLA | 21.0 | $354\pm19$ |
| 5 | 60123.31137 | VLA | 23.0 | $378\pm20$ |
| 5 | 60123.31137 | VLA | 25.0 | $372\pm16$ |
| 5 | 60123.33328 | VLA | 31.0 | $321\pm19$ |
| 5 | 60123.35726 | VLA | 13.0 | $456\pm12$ |
| 5 | 60123.35726 | VLA | 15.0 | $379\pm12$ |
| 5 | 60123.35726 | VLA | 17.0 | $335\pm15$ |
| 5 | 60123.36806 | VLA | 5.0 | $372\pm13$ |
| 5 | 60123.36806 | VLA | 7.0 | $629\pm12$ |
|  | 60124.15000 | ALMA | 90.5 | $163\pm29$ |
|  | 60124.15000 | ALMA | 92.4 | $166\pm25$ |
|  | 60124.15000 | ALMA | 102.5 | $147\pm26$ |
|  | 60124.15000 | ALMA | 105.5 | $132\pm23$ |
| 6 | 60125.05966 | VLA | 4.5 | $191\pm12$ |
| 6 | 60125.05966 | VLA | 5.5 | $163\pm11$ |
| 6 | 60125.05966 | VLA | 6.5 | $232\pm11$ |
| 6 | 60125.05966 | VLA | 7.5 | $265\pm12$ |
| 6 | 60125.06250 | VLA | 5.0 | $172\pm12$ |
| 6 | 60125.06250 | VLA | 7.0 | $212\pm12$ |
| 6 | 60125.06815 | VLA | 1.4 | $96\pm20$ |
| 6 | 60125.06815 | VLA | 1.8 | $94\pm17$ |
| 6 | 60125.08433 | VLA | 2.2 | $109\pm18$ |
| 6 | 60125.08433 | VLA | 2.8 | $153\pm15$ |
| 6 | 60125.08433 | VLA | 3.2 | $150\pm13$ |
| 6 | 60125.08433 | VLA | 3.8 | $167\pm13$ |
| 6 | 60125.10000 | VLA | 8.5 | $324\pm14$ |
| 6 | 60125.10000 | VLA | 9.5 | $361\pm13$ |
| 6 | 60125.10000 | VLA | 10.5 | $340\pm13$ |
| 6 | 60125.10000 | VLA | 11.5 | $353\pm15$ |
| 6 | 60125.11298 | VLA | 13.0 | $336\pm12$ |
| 6 | 60125.11298 | VLA | 15.0 | $298\pm11$ |
| 6 | 60125.11298 | VLA | 17.0 | $277\pm15$ |
| 6 | 60125.12500 | VLA | 5.0 | $212\pm12$ |
| 6 | 60125.12500 | VLA | 7.0 | $256\pm12$ |
|  | 60129.04549 | ALMA | 90.5 | $139\pm20$ |
|  | 60129.04549 | ALMA | 92.4 | $120\pm18$ |
|  | 60129.04549 | ALMA | 102.5 | $<69$ |
|  | 60129.04549 | ALMA | 105.5 | $<60$ |
| 7 | 60130.99178 | VLA | 4.5 | $148\pm9$ |
| 7 | 60130.99178 | VLA | 5.5 | $115\pm9$ |
| 7 | 60130.99178 | VLA | 6.5 | $108\pm12$ |
| 7 | 60130.99178 | VLA | 7.5 | $117\pm13$ |
| 7 | 60130.99306 | VLA | 5.0 | $141\pm15$ |
| 7 | 60130.99306 | VLA | 7.0 | $89\pm13$ |
| 7 | 60130.99826 | VLA | 1.4 | $68\pm22$ |
| 7 | 60130.99826 | VLA | 1.8 | $143\pm19$ |
| 7 | 60131.01449 | VLA | 2.2 | $158\pm21$ |
| 7 | 60131.01449 | VLA | 2.8 | $142\pm16$ |
| 7 | 60131.01449 | VLA | 3.2 | $124\pm14$ |
| 7 | 60131.01449 | VLA | 3.8 | $161\pm13$ |
| 7 | 60131.03141 | VLA | 8.5 | $135\pm13$ |
| 7 | 60131.03141 | VLA | 9.5 | $107\pm12$ |
| 7 | 60131.03141 | VLA | 10.5 | $92\pm10$ |
| 7 | 60131.03141 | VLA | 11.5 | $100\pm15$ |
| 7 | 60131.04550 | VLA | 20.0 | $94\pm15$ |
| 7 | 60131.04550 | VLA | 24.0 | $92\pm17$ |
| 7 | 60131.06055 | VLA | 13.0 | $137\pm12$ |
| 7 | 60131.06055 | VLA | 15.0 | $131\pm11$ |
| 7 | 60131.06055 | VLA | 17.0 | $103\pm14$ |
| 7 | 60131.07292 | VLA | 5.0 | $162\pm14$ |
| 7 | 60131.07292 | VLA | 7.0 | $147\pm12$ |
| 8 | 60143.98697 | VLA | 4.5 | $113\pm13$ |
| 8 | 60143.98697 | VLA | 5.5 | $124\pm12$ |
| 8 | 60143.98697 | VLA | 6.5 | $123\pm13$ |
| 8 | 60143.98697 | VLA | 7.5 | $129\pm13$ |
| 8 | 60143.98958 | VLA | 5.0 | $91\pm15$ |
| 8 | 60143.98958 | VLA | 7.0 | $102\pm13$ |
| 8 | 60143.99346 | VLA | 1.4 | $104\pm23$ |
| 8 | 60143.99346 | VLA | 1.8 | $68\pm20$ |
| 8 | 60144.00969 | VLA | 2.2 | $41\pm20$ |
| 8 | 60144.00969 | VLA | 2.8 | $80\pm16$ |
| 8 | 60144.00969 | VLA | 3.2 | $77\pm14$ |
| 8 | 60144.00969 | VLA | 3.8 | $68\pm13$ |
| 8 | 60144.02565 | VLA | 8.5 | $110\pm15$ |
| 8 | 60144.02565 | VLA | 9.5 | $110\pm15$ |
| 8 | 60144.02565 | VLA | 10.5 | $99\pm15$ |
| 8 | 60144.02565 | VLA | 11.5 | $78\pm16$ |
| 8 | 60144.03977 | VLA | 13.0 | $40\pm16$ |
| 8 | 60144.03977 | VLA | 15.0 | $51\pm10$ |
| 8 | 60144.03977 | VLA | 17.0 | $41\pm12$ |
| 8 | 60144.05556 | VLA | 5.0 | $152\pm13$ |
| 8 | 60144.05556 | VLA | 7.0 | $152\pm12$ |
| 9 | 60175.63000 | GMRT | 1.4 | $135\pm26$ |
| 9 | 60175.87542 | VLA | 5.0 | $32\pm10$ |
| 9 | 60175.87542 | VLA | 7.0 | $0\pm30$ |
| 9 | 60175.88190 | VLA | 3.5 | $25\pm9$ |
| 9 | 60175.90322 | VLA | 10.0 | $0\pm29$ |
|  | 60177.63000 | GMRT | 0.6 | $<90$ |
|  | 60178.63000 | GMRT | 0.4 | $<420$ |
| 10 | 60187.11613 | VLA | 5.0 | $46\pm6$ |
| 10 | 60187.11613 | VLA | 7.0 | $32\pm6$ |
| 10 | 60187.13373 | VLA | 9.0 | $23\pm6$ |
| 10 | 60187.13373 | VLA | 11.0 | $22\pm6$ |
| 10 | 60187.15885 | VLA | 13.0 | $35\pm9$ |
| 10 | 60187.15885 | VLA | 15.0 | $35\pm9$ |
| 10 | 60187.15885 | VLA | 17.0 | $0\pm50$ |
| 11 | 60216.00837 | VLA | 5.0 | $23\pm3$ |
| 11 | 60216.00837 | VLA | 7.0 | $19\pm2$ |

: Radio observations of AT 2023lcr$^a$

Table notes: $^{a}$ Upper limits reported as 3$\times$ image RMS. Epochs of VLA observations are numbered. We report statistical errors, but include systematic errors in our reported reduced $\chi^2$/DoFs. $^{b}$ VLA: Karl G. Jansky Very Large Array; SMA: Submillimeter Array; ALMA: Atacama Large Millimeter/sub-millimeter Array; GMRT: Giant Metrewave Radio Telescope.

# Corner Plots

![](lcr_corner.pdf)

![](blt_corner.pdf)

![](any_corner.pdf)

![](any_t0_corner.pdf)

![](lfa_corner.pdf)

![](lfa_corner_gauss.pdf)

![](lfa_off_gauss_corner.pdf)

![](lfa_off_power_corner.pdf)

# Selected configurations

|  |  |  |  |
|:---|:---|:---|:---|
| Parameter | Gaussian | Top hat | Top hat |
|  |  | (ICC) | ($\Gamma_0=\infty$) |
| $t_0$ \[MJD\] | $60113.03_{-0.02}^{+0.01}$ | $60113.02_{-0.02}^{+0.01}$ | $60112.99_{-0.00}^{+0.00}$ |
| $\theta_\text{v}$ \[rad | $0.00_{-0.00}^{+0.00}$ | $0.00_{-0.00}^{+0.00}$ | $0.00_{-0.00}^{+0.00}$ |
| $\log_{10}(E_\text{K,iso}/\text{erg})$ | $53.93_{-0.17}^{+0.22}$ | $54.14_{-0.27}^{+0.67}$ | $54.51_{-0.20}^{+0.25}$ |
| $\theta_\text{c}$ \[rad\] | $0.02_{-0.00}^{+0.00}$ | $0.03_{-0.01}^{+0.00}$ | $0.02_{-0.00}^{+0.00}$ |
| $\theta_\text{w}$ | $0.02_{-0.00}^{+0.00}$ | \- | \- |
| $\log_{10}(n_0/\text{cm}^{-3})$ | $-4.20_{-0.41}^{+0.54}$ | $-3.81_{-0.74}^{+1.21}$ | $-5.22_{-0.19}^{+0.25}$ |
| $p$ | $2.14_{-0.01}^{+0.01}$ | $2.14_{-0.01}^{+0.01}$ | $2.09_{-0.01}^{+0.01}$ |
| $\log_{10}\epsilon_e$ | $-1.52_{-0.22}^{+0.16}$ | $-1.42_{-0.29}^{+0.48}$ | $-2.23_{-0.28}^{+0.24}$ |
| $\log_{10}\epsilon_B$ | $-0.73_{-0.40}^{+0.34}$ | $-1.16_{-2.89}^{+0.66}$ | $-0.21_{-0.26}^{+0.15}$ |
| $\xi_N$ | $0.63_{-0.25}^{+0.24}$ | $0.60_{-0.25}^{+0.27}$ | $0.20_{-0.09}^{+0.14}$ |
| $\log_{10}\Gamma_0$ | $2.19_{-0.08}^{+0.07}$ | $2.15_{-0.09}^{+0.10}$ | $\infty$ |
| $\eta_\gamma$ ($z=1.0272$) | $< 1.5-3.5\%$ | $< 0.3-2.8\%$ | $< 0.4-1.0\%$ |
| $\eta_\gamma$ ($z=1.6$) | $< 3.4-7.8\%$ | $< 0.8-6.2\%$ | $< 0.8-2.3\%$ |
| $\chi^2$/DoF | $10.8$ | $7.9$ | $14.3$ |
| $\widehat{\text{elpd}}$ | $(-5.7 \pm 7.9) \times 10^{2}$ | $31.8 \pm 62.3$ | $(-2.5 \pm 2.2) \times 10^{2}$ |

: Final parameters ($68\%$ uncertainty) for selected configurations of AT 2023lcr. We calculate $\eta_\gamma$ using the $1\sigma$ distribution of $E_\text{K,iso}$ and the $E_{\gamma,\text{iso}}$ limits from Table [2](#table:radiative-energies). We present the $\widehat{\text{elpd}}$ and minimum $\chi^2$/DoF over 5,000 posterior samples. Ran with 64 walkers and 75,000 iterations; discarded 25,000.

|  |  |  |  |
|:---|:---|:---|:---|
| Parameter | Gaussian$^\ddag$ | Top hat$^\ddag$ | Top hat$^\ddag$ |
|  | ($\Gamma_0\neq\infty$) | (ICC, $\Gamma_0\neq\infty$) | ($\Gamma_0\neq\infty$) |
| $t_0$ \[MJD\] | $58875.67_{-0.08}^{+0.11}$ | $58875.78_{-0.12}^{+0.13}$ | $58875.66_{-0.08}^{+0.11}$ |
| $\theta_\text{v}$ \[rad\] | $0.09_{-0.04}^{+0.04}$ | $0.01_{-0.00}^{+0.01}$ | $0.07_{-0.07}^{+0.05}$ |
| $\log_{10}(E_\text{K,iso}/\text{erg})$ | $52.77_{-0.53}^{+0.58}$ | $53.56_{-0.75}^{+0.84}$ | $52.97_{-0.88}^{+0.71}$ |
| $\theta_\text{c}$ \[rad\] | $0.05_{-0.02}^{+0.03}$ | $0.08_{-0.01}^{+0.01}$ | $0.07_{-0.03}^{+0.09}$ |
| $\theta_\text{w}$ | $0.16_{-0.08}^{+0.14}$ | \- | \- |
| $\log_{10}(n_0/\text{cm}^{-3})$ | $1.91_{-1.02}^{+1.00}$ | $0.47_{-0.64}^{+1.16}$ | $1.85_{-1.24}^{+1.10}$ |
| $p$ | $2.96_{-0.06}^{+0.03}$ | $2.95_{-0.08}^{+0.04}$ | $2.95_{-0.06}^{+0.03}$ |
| $\log_{10}\epsilon_e$ | $-0.47_{-0.43}^{+0.28}$ | $-0.94_{-1.06}^{+0.55}$ | $-0.58_{-0.44}^{+0.33}$ |
| $\log_{10}\epsilon_B$ | $-2.51_{-1.33}^{+1.13}$ | $-2.98_{-1.32}^{+1.39}$ | $-2.74_{-1.39}^{+1.31}$ |
| $\xi_N$ | $0.49_{-0.29}^{+0.32}$ | $0.23_{-0.21}^{+0.48}$ | $0.51_{-0.32}^{+0.32}$ |
| $\log_{10}\Gamma_0$ | $2.11_{-0.41}^{+0.50}$ | $2.49_{-0.42}^{+0.35}$ | $2.00_{-0.50}^{+0.54}$ |
| $\eta_\gamma$ | $<4.3-36.5\%$ | $<0.4-13.4\%$ | $<2.0-44.8\%$ |
| $\eta_\gamma$ (*Fermi*) | $<0.4-5.4\%$ | $<0.04-1.5\%$ | $<0.2-7.5\%$ |
| $\chi^{2 ^ \dag}$ | $3.6$ | $3.5$ | $3.4$ |
| $\widehat{\text{elpd}}$ | $38.9 \pm 38.2$ | $47.1 \pm 35.1$ | $5.3 \pm 60.5$ |

: Final parameters ($68\%$ uncertainty) for selected configurations of AT 2020blt. We calculate $\eta_\gamma$ using the $1\sigma$ distribution of $E_\text{K,iso}$ and the $E_{\gamma,\text{iso}}$ limits from Table [2](#table:radiative-energies). We present the $\widehat{\text{elpd}}$ and minimum $\chi^2$/DoF over 5,000 posterior samples. Ran with 64 walkers and 75,000 iterations; discarded 25,000.\
$^\dag$ $\chi^2$ does not account for non-detections.\
$^\ddag$ Fails to account for the radio non-detection at $\sim25$ d and struggles or fails with the radio non-detection at $\sim100$ d

|  |  |  |  |
|:---|:---|:---|:---|
| Parameter | Gaussian | Top hat | Top hat |
|  |  | (ICC) | ($\Gamma_0=\infty$) |
| $t_0$ \[MJD\] | $59230.28_{-0.00}^{+0.00}$ | $59230.29_{-0.00}^{+0.00}$ | $59230.28_{-0.00}^{+0.00}$ |
| $\theta_\text{v}$ \[rad\] | $0.04_{-0.01}^{+0.01}$ | $0.03_{-0.00}^{+0.01}$ | $0.04_{-0.02}^{+0.03}$ |
| $\log_{10}(E_\text{K,iso}/\text{erg})$ | $53.31_{-0.32}^{+0.42}$ | $53.87_{-0.53}^{+0.62}$ | $53.94_{-0.73}^{+1.33}$ |
| $\theta_\text{c}$ \[rad\] | $0.09_{-0.02}^{+0.02}$ | $0.03_{-0.01}^{+0.01}$ | $0.08_{-0.05}^{+0.07}$ |
| $\theta_\text{w}$ | $0.34_{-0.18}^{+0.25}$ | \- | \- |
| $\log_{10}(n_0/\text{cm}^{-3})$ | $2.79_{-0.54}^{+0.50}$ | $-1.04_{-0.48}^{+0.52}$ | $1.66_{-1.80}^{+1.22}$ |
| $p$ | $2.01_{-0.01}^{+0.01}$ | $2.04_{-0.02}^{+0.03}$ | $2.01_{-0.01}^{+0.01}$ |
| $\log_{10}\epsilon_e$ | $-0.25_{-0.39}^{+0.18}$ | $-0.30_{-0.30}^{+0.21}$ | $-0.79_{-1.35}^{+0.64}$ |
| $\log_{10}\epsilon_B$ | $-4.78_{-0.16}^{+0.32}$ | $-2.28_{-1.39}^{+1.14}$ | $-4.49_{-0.40}^{+1.02}$ |
| $\xi_N$ | $0.64_{-0.28}^{+0.25}$ | $0.26_{-0.12}^{+0.20}$ | $0.59_{-0.31}^{+0.28}$ |
| $\log_{10}\Gamma_0$ | $2.28_{-0.36}^{+0.45}$ | $2.90_{-0.09}^{+0.07}$ | $\infty$ |
| $\eta_\gamma$ | $< 21.0-59.4\%$ | $< 4.4-39.5\%$ | $<0.7-46.9\%$ |
| $\chi^2$/DoF | $16.9$ | $10.4^\dag$ | $12.4$ |
| $\widehat{\text{elpd}}$ | $6.4 \pm 34.1$ | $34.2 \pm 22.4$ | $21.2 \pm 26.5$ |

: Final parameters ($68\%$ uncertainty) for selected configurations of AT 2021any. We calculate $\eta_\gamma$ using the $1\sigma$ distribution of $E_\text{K,iso}$ and the $E_{\gamma,\text{iso}}$ limits from Table [2](#table:radiative-energies). We present the $\widehat{\text{elpd}}$ and minimum $\chi^2$/DoF over 5,000 posterior samples. Ran with 64 walkers and 75,000 iterations; discarded 25,000.\
$^\dag$ Although this is the smallest $\chi^2$ of all AT 2021any configurations shown in this work, the top hat with ICC model underestimates the X-ray by $\sim 1/2$ an order of magnitude; the smaller $\chi^2$ is likely because this model has a slightly better agreement with X-band (9.0 - 9.7 GHz) observations.

|  |  |  |  |
|:---|:---|:---|:---|
| Parameter | Gaussian | Top hat |  |
|  | ($\Gamma_0=\infty$) | (ICC) |  |
| $t_0$ \[MJD\] | $59337.19_{-0.17}^{+0.19}$ | $59338.06_{-0.01}^{+0.01}$ |  |
| $\theta_\text{v}$ \[rad | $0.20_{-0.01}^{+0.01}$ | $0.05_{-0.00}^{+0.00}$ |  |
| $\log_{10}(E_\text{K,iso}/\text{erg})$ | $54.95_{-0.31}^{+0.20}$ | $52.66_{-0.28}^{+0.42}$ |  |
| $\theta_\text{c}$ \[rad\] | $0.02_{-0.00}^{+0.01}$ | $0.12_{-0.01}^{+0.01}$ |  |
| $\theta_\text{w}$ | $0.10_{-0.05}^{+0.05}$ | \- |  |
| $\log_{10}(n_0/\text{cm}^{-3})$ | $5.14_{-0.33}^{+0.25}$ | $-0.52_{-0.27}^{+0.38}$ |  |
| $p$ | $2.13_{-0.04}^{+0.05}$ | $2.64_{-0.05}^{+0.05}$ |  |
| $\log_{10}\epsilon_e$ | $-0.14_{-0.17}^{+0.10}$ | $-0.56_{-0.37}^{+0.21}$ |  |
| $\log_{10}\epsilon_B$ | $-4.71_{-0.20}^{+0.26}$ | $-1.88_{-0.69}^{+0.57}$ |  |
| $\xi_N$ | $0.02_{-0.01}^{+0.01}$ | $0.55_{-0.31}^{+0.30}$ |  |
| $\log_{10}\Gamma_0$ | $\infty$ | $1.34_{-0.02}^{+0.03}$ |  |
| $\eta_\gamma$ | $<0.01-0.03\%$ | $<1.0-4.8\%$ |  |
| $\chi^2$/DoF | $5.4$ | $4.5$ |  |
| $\widehat{\text{elpd}}$ | $(-1.0 \pm 0.3) \times 10^{2}$ | $(1.3 \pm 0.2) \times 10^{2}$ |  |

: Final parameters ($68\%$ uncertainty) for selected configurations of AT 2021lfa. We calculate $\eta_\gamma$ using the $1\sigma$ distribution of $E_\text{K,iso}$ and the $E_{\gamma,\text{iso}}$ limits from Table [2](#table:radiative-energies). We present the $\widehat{\text{elpd}}$ and minimum $\chi^2$/DoF over 5,000 posterior samples. Ran with 64 walkers and 75,000 iterations; discarded 25,000.

[^1]: Code and data products can be found in the repository <https://github.com/liluhua2/afterglowfit-public>.

[^2]: All times in this paper are in UT.

[^3]: All magnitudes are in AB unless specified otherwise.

[^4]: PI K. El-Badry.

[^5]: In this work, $\Delta t$ is the observer-frame time in days since the afterglow’s last non-detection, unless specified otherwise. For AT 2023lcr, the last GOTO non-detection was at $60112.99340$ MJD.

[^6]: In this work, all times are observer-frame unless specified otherwise.

[^7]: $\Lambda$CDM cosmology of (cite: Planck_2020) is used throughout.

[^8]: TOO IDs 18987 and 18992, PIs M. Coughlin and D. Malesani.

[^9]: This paper employs a list of Chandra datasets, obtained by the Chandra X-ray Observatory, contained in Chandra Data Collection .

[^10]: Proposal Number 24508916, PI A. Martin-Carrillo.

[^11]: Program IDs 23A-355 and 23A-426, PI D. Perley.

[^12]: Program ID 2022.A.00025.T, PI A. Ho.

[^13]: Program ID 2022B-S046, PI E. Berger.

[^14]: Proposal ID DDTC293, PI Nayana AJ.

[^15]: All times in this work are in the observer frame unless specified otherwise. Rest-frame quantities will be denoted with a subscript, e.g. $t_\text{rise,rest}$ for a rest-frame rise time.

[^16]: The latency is 0.740 d for AT 2020blt. 0.015 d for AT 2021any, 1.794 d for AT 2021lfa, and 0.067 d for AT 2023lcr.

</paper>

Write the methods card for this paper.