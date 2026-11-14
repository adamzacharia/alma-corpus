# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...687A.311A\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...687A.311A",
 "title": "V892 Tau: A tidally perturbed circumbinary disc in a triple stellar system",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Alaguero, Antoine",
 "n_authors": 11,
 "arxiv_id": "2405.12593",
 "doi": "10.1051/0004-6361/202449683",
 "alma_projects_linked_by_archive": [
  "2013.1.00498.S",
  "2021.1.01137.S"
 ]
}
```

Paper text:
<paper>
# V892 Tau: A tidally perturbed circumbinary disc in a triple stellar system [^1]

V892 Tau is a young binary star surrounded by a circumbinary disc that

shows hints of an interaction with the low-mass nearby star V892 Tau NE.

The goal of this paper is to constrain the orbit of V892 Tau NE and to determine the resulting circumbinary disc dynamics.

We present new ALMA observations of the V892 Tau circumbinary disc at a twice higher angular and spectral resolution. We modelled the data with V892 Tau as a triple system and performed a grid of hydrodynamical simulations testing several orbits of the companion. The simulation outputs were then post-processed to build synthetic maps that we compared to the observations.

The $^{12}$CO emission of the disc shows clear non-Keplerian features such as spiral arms. When comparing the data with our synthetic observations, we interpreted these features as ongoing interactions with the companion. Our simulations indicate that an eccentricity of $e\sim0.5$ of the companion is needed to reproduce the observed disc extent and that a mutual inclination of $\Delta i \sim 60\degree$ with the inner binary reproduces the measured disc tilt.

In order to explain most of the features of the circumbinary disc, we propose that V892 Tau NE follows an orbit with a mild eccentricity $0.2 < e < 0.5$ and a mutual inclination of $30\degree < \Delta i < 60\degree$. Such a misaligned companion suggests the disc is oscillating and precessing with time, stabilising in an intermediate plane with a non-zero mutual inclination with the inner binary. Given the orbital configuration, we show that the stability of future planets is compromised in the second half of the disc once the gas has dissipated.

# Introduction

During the early stages of star formation, a significant fraction of stars are found to be part of multiple systems (cite: Reipurth+2014; Offner+2022). Multiple systems naturally evolve to hierarchical configurations (cite: DucheneKraus2013), but allow a large diversity of possible configurations for protoplanetary discs. Circumstellar discs can in principle form around any hierarchical level of the system. As a consequence, discs in multiple systems are shaped by the disc-disc and star-disc interactions that depend on the geometrical configuration and physical properties of the system (cite: Bate2018). By means of those interactions, a large cavity is carved in circumbinary discs up to several times the binary semi-major axis, while the outer edge of the disc is set by tidal interactions with the outer stars of the system (cite: Artymowicz1994; MirandaLai2015). Spiral arms are usually launched in the process (cite: Rafikov2002). Gravitational torques from misaligned stars tend to incline discs and to make them precess (cite: PapaloizouTerquem1995), resulting in misaligned geometries of the disc plane with respect to the stellar orbital plane and even leading to a disc warp or break in some cases (e.g. (cite: Nixon+2013; Facchini+2013; Rabago+2023)). The investigation of these dynamical behaviours is key to understand disc dynamics in multiple systems and their resulting planetary architectures.

Hydrodynamical simulations have proven to be a powerful tool to infer orbits from disc morphology and kinematics in multiple systems. Multiplicity-induced substructures depend on the orbital parameters of companions. By running a grid of hydrodynamical models and comparing them to disc observations, one can now constrain orbits in multiple systems (cite: Price+2018; Gonzalez+2020; Nowak+2024). Even if this method is limited by observations in snapshots in time and the cost of hydrodynamical simulations, it provides constrains independent from astrometric measurements, and it can help to discriminate between available orbits.

V892 Tau is a young triple system located in a clustered sub-region of the Taurus star-forming cloud (Figure [1](#fig:V892-locator)). The system is composed of two central $3$ M$_{\odot}$ stars separated by $0.06\ensuremath{''}$ surrounded by a large circumbinary disc (CBD), which extends up to approximately $1.5\ensuremath{''}$ from the central stars (e.g. (cite: Monnier+2008; Long+2021)). The M3 star V892 Tau NE is projected at $4\ensuremath{''}$ north-east

from the inner binary and completes the system (cite: EsplinLuhman2019). The *Gaia*

DR3 (cite: GaiaDR3) parallax measurements result in distances of $d=134.5\pm 1.5$ pc and $d=131.3\pm 5.0$ pc, respectively, for V892 Tau and V892 Tau NE, which is consistent with a bound triple system within the error bars.

Observations with the Atacama Large Millimeter/submillimeter Array (ALMA) have unveiled the dust ring surrounding the inner binary of V892 Tau at a high spatial resolution (cite: Pinilla+2018). More recently, a detailed study of the system has been conducted by (cite: Long+2021) using that ALMA Band 6 data combined with additional

Very Large Array (VLA) observations: The eccentric inner binary has been resolved and its orbit tightly constrained, with two families of solutions for the longitude of the ascending node $\Omega_{in}$ and the argument of the periapsis $\omega_{in}$. The dust emission was found to have an $0.17\ensuremath{''}$-large inner gap, while the gas emission appears to extend to the innermost regions of the system. Both the dust and gas show hints of an inclined geometry with respect to the inner binary. The tilt of the disc with respect to the inner binary is measured at $\Delta = 8.0 \pm 4.2 \degree$ or $\Delta = 113.3 \pm 3.0 \degree$ depending of the orbital solution chosen. The size of the gas disc is consistent with a tidal interaction with V892 Tau NE and tentative spiral arms are distinguished in the redshifted side of the disc. A warp is suggested by deviations from Keplerian rotation in the outer disc and could be caused by interactions between the disc and the

inner or outer binary. In addition, recent near-IR interferometric observations have refined the orbit of the binary and detected a narrow circumstellar disc wide of $0.016\ensuremath{''}$ around the primary star of V892 Tau (cite: Vides+2023). In that work, the inner CBD was also modelled and tentative evidence of a warp was invoked to explain residual patterns from geometric models.

As a hierarchical triple system, V892 Tau is a perfect laboratory to study the formation channels of planets from discs in multiple systems, which depends on the binary-disc interactions and dynamics. Understanding the disc dynamics in such a system will help to constrain the planet formation regions in multiple stellar systems in general, but it would require the orbital configuration of the system to be known. Nonetheless, the orbit of the companion star V892 Tau NE remains unconstrained at the moment. Projected at a distance of $\sim 520$au of the central binary, the orbit of V892 Tau NE is critical to understand the dynamics of the CBD and the subsequent planet formation.

Following that effort, here we present new ALMA observations of V892 Tau that we combined with archival data. The observational setup and the resulting data are detailed in Section [2](#sec:observations). We fitted the observations with a Keplerian disc model before modelling the V892 Tau system as a triple star system with a CBD. We performed hydrodynamical simulations of that model, testing different orbits for the outer companion, and post-processed the simulation outputs to build synthetic observations. Methods are presented in Section [3](#sec:methods), while an analysis of the observations, of the synthetic observations,

and their relative comparison are described in Section [4](#sec:results). In Section [5](#sec:discussion) we give an overview of the system and discuss our results in the more general context of multiple systems. Our conclusions are summarised in Section [6](#sec:conclusion).

![](Figures/V892tau-locator.pdf)

# Observations

## Data calibration, reduction, and combination

The triple system V892 Tau was observed with ALMA in the context of the ALMA programme 2021.1.01137.S (PI: J. Miley) in Band 6. The observations were performed in two sessions, with the first session covered shorter baselines spanning $15-1997$ m ($12-1536 \;k\lambda$) with $42$ antennas. We call the resulting dataset of that session Short Baselines (SB hereafter). The second session used a more extended configuration also with $42$ antennas spanning baselines from $64$ m to $8283$ m ($49-6371 \;k\lambda$) and resulted in a dataset we call Long Baselines (LB hereafter). Each

dataset contains four

spectral windows (SPWs) with two of them set up for continuum detection centred at $217.875$ and $233.000$ GHz, with $2$ GHz of bandwidth distributed over 128 channels. The other two SPWs were centred at $230.538$ and $220.000$ GHz targeting the $^{12}$CO (2-1) and $^{13}$CO (2-1) transitions, each containing 3840 channels of $122$ kHz and $488$ kHz widths, respectively.

The raw visibility data were downloaded from the ALMA archive and subsequently calibrated using the available scripts provided by ALMA staff using the required CASA (cite: McMullin2007) 6.2.1.7 version. The band-pass and amplitude calibrator for the observations was J$0435+2532$, and J$0438+3004$ was used as the phase calibrator. The total on-source time reached approximately $18.5$ minutes.

The data were self-calibrated after the line-free channels were combined altogether to create continuum datasets. We performed several phase self-calibration rounds on each continuum dataset until the solution interval was tuned down to the integration time of $6.05$ s for the SB dataset and of $2.02$ s for the LB dataset. This process resulted in an increase of the peak

signal-to-noise ratio

(S/N) of about $6\%$ for SB and $36\%$ for LB, giving a peak S/N of $582$ and $233,$ respectively.

We downloaded the data used in  from the ALMA archive and re-calibrated it thanks to the ALMA reduction pipeline. The resulting dataset is called the Original Long et. al dataset (OLD hereafter). Then, we reduced the data and performed phase self-calibration rounds on the continuum data with solution intervals down to the integration time of $6.05$ s. The peak S/N increased by $9\%$ doing so to reach a value of $483$, which is a significant improvement given the already high S/N of the data.

The SB and LB visibility amplitudes were scaled with respect to the one of OLD to make sure the fluxes of all the datasets were consistent altogether before combination. To do so, we used the functions *estimate_scale_flux* and *rescale_flux* of the *reduction_utils.py* python script from the DSHARP project [^2]. We then created a combined continuum model with *tclean* in CASA v6.5.3 from the three datasets, using a Briggs weighting with a robust parameter of $0.5$ (cite: Briggs). On the basis of that common model, the individual datasets were self-calibrated in phase a second time. The resulting datasets were combined to create a final continuum image with *tclean* using a Briggs weighting with a robust of $-0.5$, which resulted in a RMS of $90 \mu$Jy. The resulting beam size is $0.11\ensuremath{''} \times 0.06\ensuremath{''}$ at a central frequency of $224$ GHz. Additional details regarding the data combination process are available in the Appendix [7](#app : data combination)

We also applied the resulting self-calibration tables to the gas observations, from which the continuum emission was subtracted by fitting a polynomial function to line-free channels using the *uvcontsub* task. An image cube of the $^{12}$CO (2-1) line emission was then created combining the three datasets using a Briggs weighting with a robust of $0.5$ and a channel width of $0.5$ km s$^{-1}$, giving a resulting beam size of $0.17\ensuremath{''} \times 0.11\ensuremath{''}$. We summarise the details of each of the continuum and $^{12}$CO (2-1) images in Table [\[table:comb_obs\]](#table:comb_obs). This paper presents the continuum observations but mainly focusses on the analysis and discussion of the gas emission, as a detailed description of the continuum data will be addressed in a future study.

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| OLD+SB+LB | Frequency | Beamsize | Flux $^{1}$ | RMS | $R_{90\%}$ |
|  | (GHz) | $(\ensuremath{''})$ | (mJy or Jy km s$^{-1}$ ) | (mJy beam$^{-1}$) | $(\ensuremath{''})$ |
| Continuum | $224$ | $0.11 \times 0.06$ | $297.1\pm0.1$ | $0.09$ | $0.38\pm0.01$ |
| $^{12}$CO (2-1) | $230.538$ | $0.17 \times 0.11$ | $15.8\pm0.1$ | $5.5$ | $1.45\pm0.02$ |
|  |  |  |  |  |  |
| OLD |  |  |  |  |  |
| Continuum | $224$ | $0.23 \times 0.16$ | $290.6\pm0.2$ | $0.08$ | $0.46\pm0.01$ |
| $^{12}$CO (2-1) | $230.538$ | $0.23 \times 0.16$ | $14.7\pm0.4$ | $6.4$ | $1.45\pm0.02$ |

Table notes: The top panel shows the results achieved from the data combined in this work. The bottom panel shows the results derived in the previous work of from the OLD dataset. $^{1}$The flux uncertainty was measured by multiplying the noise level by the square root of the number of pixels in the integrated area.

## Dust disc

![image](Figures/cont_contours.pdf) ![image](Figures/I_radial_profile_cont.pdf)

Figure [2](#fig:obs_cont) shows the ALMA $1.3$ mm continuum image and a deprojected brightness radial profile. The observed structure emerges as a Gaussian-like ring located at a separation of approximately $0.22\ensuremath{''}$ from the centre of the disc, following the position of the peak intensity radius. The inner binary has carved a cavity in the innermost parts of the system. We found a cavity radius of $R_{cav} = 0.14\pm 0.02\ensuremath{''}$that is defined as the radius at which the intensity first reaches half of its peak level with an incertitude taken as the difference with quarter peak radius. The dusty disc has a deprojected radius of $R_{90\%} = 0.38\pm0.01\ensuremath{''}$ measured as the radius encircling $90\%$ of the total flux.

The inclination $i$ and the position angle $PA$ of the disc are respectively best-fitted to $i=54.0 \pm 1.8\degree$ and $PA=51.5\pm0.5\degree$. Thanks to an improved angular resolution, the $1.3$ mm emission is found to be more compact than in previous observations (cite: Pinilla+2018). The cavity is spatially resolved along with an azimuthal asymmetry in the NW side of the disc. Indeed the northern side of the disc along the minor axis is $18\%$ brighter than its southern side. This trend was also found in and is consistent with the reported value of $20\%$. This kind of horse-shoe asymmetry is a known consequence of binarity (cite: Ragusa+2017). However optically thick warm dust emission from the inner rim of the disc may also produce similar patterns (cite: Ribas+2024). This emission coming from the far side of the disc, it would indicate that the closest side to the observer is the SE side of the disc. Like all the previous ALMA observations of V892 Tau, no emission is detected from the vicinity of V892 Tau NE in the $1.3$ mm continuum. The sensitivity and RMS of the observations presented in this paper being similar to the previous data, this result is not surprising.

We confirm the detection of unresolved emission in the cavity with a $30\sigma$ significance. This emission could be explained by circumstellar dusty material and could trace the circumstellar disc detected in the inner system (cite: Vides+2023). Future multi-wavelengths observations could allow a precise characterisation of the dust properties, while multi-epochs observations could allow the clump’s dynamical behaviour to be prescribed. Those questions are left for future investigations.

## CO emission

The $^{12}$CO emission of the disc is detected at a confidence level above $3\sigma$ from channel $-6$ km s$^{-1}$ to channel $23$ km s$^{-1}$ in the kinematic local standard of rest (LSRK) velocity. The data suffer from absorption by cloud material at the systemic velocity around $8$ km s$^{-1}$. The complete channel maps can be found in Appendix [8](#app : channel maps). $99\%$ of the flux is contained in a radius of $1.73\ensuremath{''}$, with a maximum recoverable scale of the observational setup estimated at $2.27\ensuremath{''}$ using the $5^{th}$ percentile of the shortest baseline lengths. The gas disc has a radius of $R_{90\%} = 1.45\ensuremath{''}$ and a flux of $15.8$ Jy km s$^{-1}$, which is in good agreement with . The north-east side of the disc appears blueshifted compared to the systemic velocity of $\sim 8$ km s$^{-1}$, which means the disc rotates in an anti-clockwise way. The morphology of the emission in the velocity channels is similar to the observations reported in : the faint lower emission surface of the disc lacks clear visibility, indicating potential blending with the upper emission surface due to spatial resolution constraints or possible non-detection. This makes the true orientation of the disc ambiguous and the closest side to the observer difficult to define. Irregularities at the edge of the redshifted side are recovered as well as in the northern side of the disc. However these irregularities are not found to be part of larger structures that could have traced potential interactions with the companion star V892 Tau NE. In the following, we model V892 Tau as a triple system and try to constrain the orbit of V892 Tau NE based on hydrodynamical simulations. Our methods to model the $^{12}$CO emission in detail and the hydrodynamical setups used are described in the Section [3](#sec:methods) below. From this modelling, we discuss in more detail the observations in Section [4](#sec:results).

# Methods

## Discminer

In order to understand at a deeper level the kinematical information contained in the structured disc of V892 Tau, we built a quantitative Keplerian model to be compared with the observations. To do so, we used the python package Discminer (cite: DiscminerI; DiscminerII) to fit the $^{12}$CO (2-1) line emission and kinematics channel by channel by a Keplarian disc model. Discminer first builds a Keplerian disc model from a set of parameters described hereafter. The position offset $(x_c, y_c)$, the inclination $i$ and the position angle $PA$ define the orientation of the disc. In this work, the PA was defined as the angle from the northern axis to the blueshifted semi-major axis. The velocity profile is set by the central stellar mass $M_{*}$ and the systemic velocity $v_{sys}$. The disc upper and lower surfaces are both defined by exponentially tapered power laws (Equation [\[eq:z_prof\]](#eq:z_prof)). The line profile width at half maximum $L_w$ and the line profile slope $L_s$ are defined as power laws as well (Equation [\[eq:L_prof\]](#eq:L_prof), valid for both $L_s$ and $L_w$). The reference intensity is taken from a peak intensity power law $I_p$ in a region $\mathcal{D}(R_{out})$ that extends from $r=0$ to $r=R_{out}$, where $R_{out}$ is the outer radius of the disc (Equation [\[eq:I_prof\]](#eq:I_prof)). This whole set of parameters builds the final Keplerian model of intensity $I_m$ using a Bell function kernel with a projected velocity $v_{k,los}$ along the line of sight corresponding to the channel velocity $v_{ch}$ (Equation [\[eq:I_chan\]](#eq:I_chan)). In the equation below, $r_0$ is the reference radius taken as $r_0=100$ au, while $z_0$, $L_0$ and $I_0$ are values of reference for the vertical height, linewidth/lineslope and intensity respectively. The critical radius $r_b$ describes the exponential cutoff of the disc surface, with $q$ describing the strength of this tapering. Finally, $p$ is the power-law index of the disc surface.

$$\begin{equation}
\label{eq:z_prof}
    z(r) = z_0 \left(\frac{r}{r_0}\right)^p \exp\left(\frac{-r}{r_b}\right)^q \, ,
\end{equation}$$ $$\begin{equation}
\label{eq:L_prof}
    L(r, z) = L_{0} \left(\frac{r}{r_0}\right)^{p_L} \left(\frac{|z|}{z_0}\right)^{q_L} \, ,
\end{equation}$$ $$\begin{equation}
\label{eq:I_prof}
    I_p(r, z) = I_{0} \left(\frac{r}{r_0}\right)^{p_I} \left(\frac{|z|} {z_0}\right)^{q_I}  \mathcal{D}(R_{out}) \, ,
\end{equation}$$ $$\begin{equation}
\label{eq:I_chan}
    I_m(r,z, v_{ch}) = I_p \left( 1+ \Big\rvert \frac{v_{ch} - v_{k,los}}{L_w}\Big\rvert^{2L_s}\right)^{-1} \, ,
\end{equation}$$

Discminer then fits the previous model to the data in the image plane channel by channel thanks to MCMC sampling using emcee (cite: emcee). More details about the initial conditions and the results of that procedure can be found in Appendix [9](#app : Discminer).

From the best-fit model channels, we then built moment maps from the data and model channels. First, a moment 0 map was computed by integrating the intensity in each pixel along the velocity axis. We then collapsed the cube by selecting the brightest pixel along the velocity axis for each pixel to create a peak temperature moment map (moment 8). Picking up the centroid velocity corresponding to that peak allowed for a velocity map of the disc to be built (moment 9). Finally, we built a moment map corresponding to the line-width around that centroid velocity. We applied a $3\sigma$ clipping in the building of data moment maps. The same mask delimiting the detected disc area was applied to the model moment maps. Residual maps were built by subtracting the masked model moment maps to the data moment maps.

## Hydrodynamical simulations

Several hints of interaction with the external star V892 Tau NE are detected in the V892 Tau CBD (tidal truncation, tentative spiral arms, disc tilt, tentative disc warp). In order to confirm that V892 Tau NE is bound to the V892 system and to constrain its orbit, we performed 3D hydrodynamical simulations using the Phantom (cite: Price+2018-phantom) smoothed particle hydrodynamics (SPH, e.g. (cite: Monaghan1992)) code. Our model consisted in a central binary star surrounded by a CBD and an outer stellar companion orbiting further out. The model used of $10^6$ SPH particles distributed in the disc according to a surface density distribution $\Sigma \propto r^{-p}$ with $p=1$ that extends initially from $14$ au to $200$ au for a total disc mass of $0.06$ M$_{\odot}$ (). The true orientation of the V892 Tau CBD is unconstrained due to an uncertainty on the inclination sign of the disc. We assumed that inclination to be positive and of $54.6\degree$, meaning the closest side to the observer was the SE side. The PA of the disc was set to $53\degree$ in agreement with the observations of . The inner border of the simulated CBD was set to $14.2$ au, which is twice the semi-major axis of the inner binary and in line with theoretical predictions of the cavity size (cite: Miranda+2017). The aspect ratio $H/r=0.055$ at the reference radius $R_0=100$ au and the sound speed exponent $q=0.185$ were set to match the fitted temperature profile in .

We modelled the stars as sink particles (cite: Bate+1995) with accretion radii of $1$ au for the two components of the inner binary and of $10$ au for the outer star. The inner binary was initialised coplanar in a prograde configuration with respect to the disc while its other orbital parameters and its mass were set in line with the observations (), which allows us to disentangle more easily the effects triggered by the companion solely. Moreover the observed inclination of the disc to the inner binary plane is measured to be down to $4\degree$, which is close to coplanarity (). The orbit of the companion star V892 Tau NE remains unconstrained so far. One of the goals of this work is to explore if this companion is bound to the inner binary and to constrain its eccentricity and inclination parameters $e_{out}$ and $i_{out}$ respectively. From there we modelled the V892 Tau system as a triple system in five numerical setups, with a different orbit for the outer companion each time:

- *ref* (reference case) : $e_{out} = 0.2$ & $\Delta i_{out} = 0\degree$,

- *e05* (eccentric case) : $e_{out} = 0.5$ & $\Delta i_{out} = 0\degree$,

- *i30* (inclined case 1) : $e_{out} = 0.2$ & $\Delta i_{out} = 30\degree$,

- *i60* (inclined case 2) : $e_{out} = 0.2$ & $\Delta i_{out} = 60\degree$,

- *ei60* (eccentric inclined case) : $e_{out} = 0.5$ & $\Delta i_{out} = 60\degree$,

where $\Delta i_{out}$ represents the mutual inclination between the companion and the inner binary orbital plane. It resulted in inclination parameters with respect to the sky plane of $i_{out}=54.6\degree$ for *ref* and *e05*, $i_{out}=24.6\degree$ for *i30* and $i_{out}=-5.4\degree$ for *i60* and *ei60*. The maximal eccentricity of the outer binary has been constrained to $e_{out} < 0.2$ considering a coplanar orbit and a disc extent of $R_{out}\sim200$ au (). This estimation assumed a coplanar companion, but a misaligned orbit could allow for more eccentric orbits in line with the truncation of the disc. We explored values up to $e_{out}=0.5$. We expect different eccentricity and inclination parameters to have consequences on the disc truncation and on the disc orientation. From dynamical considerations, it is more likely that V892 Tau NE is observed close to apoastron (cite: VanAlbada1968). We accordingly set the argument of the periapsis to $\omega_{out}=180\degree$. Given the projected separation of the companion of $\sim520$ au (cite: GaiaDR3), we assumed the semi-major axis to be $a_{out}=500$ au. The longitude of the ascending node $\Omega_{out}=53\degree$ was set in line with the observed disc PA. We assumed the mass of V892 Tau NE to be $0.5$ M$_\odot$, which is in agreement with the mass of similar M3 stars (cite: Luhman+2007; Flores+2022).

Table [1](#table:setups_params) summarises the parameters defining the orbital configuration of the setups. In that table, the reference plane is the plane of the sky and the origin is the centre of mass of the inner binary. Figure [3](#fig:grid_orbits) shows the initialised orbits for each setup projected in the sky-plane and a plane perpendicular to it. We evolved the hydrodynamical simulations for $50$ P$_{out}$, with $P_{out}=4375$ yrs the period of the outer binary for a semi-major axis of $a_{out} = 500$ au. It corresponds to $28400$ periods of the inner binary. At such timescales, the disc had time to relax from its initial condition and to evolve significantly.

+------------------------------------------------------------------------------------+
| Inner binary                                                                       |
+:==========================:+:=======================:+:===========================:+
| Parameter                  | Observations            | Simulations                 |
+----------------------------+-------------------------+-----------------------------+
| $M_{in}$ (M$_{\odot}$)     | $6.0\pm0.2$             | $6.0$                       |
+----------------------------+-------------------------+-----------------------------+
| $q_{in}$                   | $\sim0.5$               | $0.5$                       |
+----------------------------+-------------------------+-----------------------------+
| $a_{in}$ (au)              | $7.1\pm0.1$             | $7.1$                       |
+----------------------------+-------------------------+-----------------------------+
| $e_{in}$                   | $0.27\pm0.10$           | $0.27$                      |
+----------------------------+-------------------------+-----------------------------+
| $i_{in}$ ($\degree$)       | $59.3\pm2.7$            | $54.6$                      |
+----------------------------+-------------------------+-----------------------------+
| $\Omega_{in}$ ($\degree$)  | $50.5^{+9.6}_{-8.8}$    | $53$                        |
+----------------------------+-------------------------+-----------------------------+
| $\omega_{in}$ ($\degree$)  | $179.9^{+44.4}_{-30.3}$ | $180$                       |
+----------------------------+-------------------------+-----------------------------+
|                            |                         |                             |
+----------------------------+-------------------------+-----------------------------+
| Outer binary                                                                       |
+----------------------------+-------------------------+-----------------------------+
| Parameter                  | Observations            | Simulations                 |
+----------------------------+-------------------------+-----------------------------+
| $M_{out}$ (M$_{\odot}$)    | \-                      | $6.5$                       |
+----------------------------+-------------------------+-----------------------------+
| $q_{out}$                  | \-                      | $0.08$                      |
+----------------------------+-------------------------+-----------------------------+
| $a_{out}$ (au)             | \-                      | $500$                       |
+----------------------------+-------------------------+-----------------------------+
| $e_{out}$                  | \-                      | *ref*: $0.2$ *i30*: $0.2$   |
+----------------------------+-------------------------+-----------------------------+
|                            |                         | *e05*: $0.5$ *i60*: $0.2$   |
+----------------------------+-------------------------+-----------------------------+
|                            |                         | *ei60*: $0.5$               |
+----------------------------+-------------------------+-----------------------------+
| $i_{out}$ ($\degree$)      | \-                      | *ref*:$54.6$ *i30*: $24.6$  |
+----------------------------+-------------------------+-----------------------------+
|                            |                         | *e05*: $54.6$ *i60*: $-5.6$ |
+----------------------------+-------------------------+-----------------------------+
|                            |                         | *ei60*: $-5.6$              |
+----------------------------+-------------------------+-----------------------------+
| $\Omega_{out}$ ($\degree$) | \-                      | $53$                        |
+----------------------------+-------------------------+-----------------------------+
| $\omega_{out}$ ($\degree$) | \-                      | $180$                       |
+----------------------------+-------------------------+-----------------------------+
|                            |                         |                             |
+----------------------------+-------------------------+-----------------------------+
| Circumbinary disc                                                                  |
+----------------------------+-------------------------+-----------------------------+
| Parameter                  | Observations            | Simulations                 |
+----------------------------+-------------------------+-----------------------------+
| $R_{in}$ (au)              | \-                      | $14.2$                      |
+----------------------------+-------------------------+-----------------------------+
| $R_{out}$ (au)             | $196\pm3$               | $200$                       |
+----------------------------+-------------------------+-----------------------------+
| $R_{0}$ (au)               | $100$                   | $100$                       |
+----------------------------+-------------------------+-----------------------------+
| $M_d$ (M$_{\odot}$)        | $\sim0.06$              | $0.06$                      |
+----------------------------+-------------------------+-----------------------------+
| $p$                        | \-                      | $1$                         |
+----------------------------+-------------------------+-----------------------------+
| $q$                        | $0.185$                 | $0.185$                     |
+----------------------------+-------------------------+-----------------------------+
| $\Omega_d$ ($\degree$)     | $53.0 \pm 0.7$          | $53$                        |
+----------------------------+-------------------------+-----------------------------+
| $i_d$ ($\degree$)          | $54.6 \pm 1.3$          | $54.6$                      |
+----------------------------+-------------------------+-----------------------------+
| $\frac{H}{R}\vert _{R_0}$  | $0.055$                 | $0.055$                     |
+----------------------------+-------------------------+-----------------------------+
| $\alpha_{SS}$              | \-                      | $0.005$                     |
+----------------------------+-------------------------+-----------------------------+

: Initial parameters of the hydrodynamical simulations.

Table notes: The indices $in$, $out$ and $d$ refer to the inner binary, the outer binary and the disc respectively. ’-’ indicates a lack of data. The reference plane is the sky-plane. The disc parameters are taken from the centre of the inner binary. The observational values are taken from .

![](Figures/orbits.pdf)

## Radiative transfer and post-processing

The simulation outputs were post-processed via radiative transfer to produce intensity datacubes of the system. Because the disc oscillates and precesses during the simulations, its inclination and position angle are evolving with time. In order to have a proper comparison with the observations, the disc was manually moved back to an average inclination of $54.6\degree$ and an average PA of $53\degree$ before the post-processing. We report the inclination and PA values of the simulated discs before this rotation in Appendix [10](#app : manual move back). We used the radiative transfer code MCFOST (cite: Pinte+2006; Pinte+2009) that employs a Voronoi tesselation to build a grid based on the SPH particle distribution, with one cell per SPH particle. Since our SPH simulations contains gas particles only, the dust spatial distribution is assumed to follow the gas distribution. Dust grains were assumed to be at local thermal equilibrium and subject to passive heating. They were assumed compact and following opacity laws of astrosilicates (cite: WeingartnerDraine2001) with their scattering properties computed following the Mie theory framework. We used $100$ grain sizes from $0.03\mu$m to $1000 \mu$m logarithmically spaced in scale. The global distribution was normalised by integrating over all grain sizes, assuming a typical power-law of exponent $-3.5$ (cite: Mathis1977), and all over the grid to have a dust to gas mass ratio of $0.01$. We adopted a uniform value of $1\times10^{-4}$ for the $^{12}$CO abundance compared to H$_2$. The turbulent velocity was set to zero and the freeze-out temperature below which the grid cells do not emit, to $20$ K. The sink particles were considered as spherical stars that radiate isotropically as black-bodies with temperature and luminosity chosen in agreement with their mass at an age of $3$ Myr (cite: Siess+2000) consistent with an estimated age of the system of $\sim 2$ Myr (cite: KucukAkkaya2010). This way each $3$ M$_{\odot}$ component of the inner binary had a temperature of $10745$ K and a luminosity of $72$ L$_{\odot}$ while the $0.5$ M$_{\odot}$ companion had a surface temperature of $3758$ K and a luminosity of $0.3$ L$_{\odot}$. $1.28\times10^8$ photons packets were used to compute the 3D temperature using a Monte-Carlo approach and $1.28\times10^6$ other photons packets were used to compute images with a ray-tracing method based on the temperature structure.

$^{12}$CO (2-1) channel maps were produced with a $0.075$ km s$^{-1}$ resolution from $-15$ km s$^{-1}$ to $15$ km s$^{-1}$. The velocity axis was then shifted from the systemic velocity $v_{sys}=7.86$ km s$^{-1}$. The produced datacube was then post-processed with CASA (cite: McMullin2007) to produce synthetic observations. Using the *simalma* task, Measurement Sets (MS) were generated from the radiatively processed data with the right sampling of the *uv* plane. The sampling in the *uv* plane was taken from the antenna configurations used in the observations. Considering that the observations are made from $3$ observational datasets, we produced synthetic data corresponding to each individual dataset. The integration times were set to $9.25$ minutes for the synthetic SB and LB sets, and to $8$ minutes for the synthetic dataset matching the OLD set. The precipitable water vapour index $PWV=0.6$ mm was also chosen in line with the observing conditions. It resulted in $3$ synthetic MS each matching an actual MS. The simulated MS were then spectrally Hanning-smoothed to match the spectral resolution of the observations. The $3$ synthetic datasets had their continuum subtracted before being imaged together with the exact same *tclean* parameters used in the imaging process of the observations (see Section [2.1](#subsec : data)). Moment 0, moment 8 (peak temperature) and moment 9 (peak velocity) maps were created from the treated synthetic cubes using the same clipping as in the observations. The central channels where the data signal is absorbed were ignored in the process.

## N-body simulations

Additionally, we performed N-body simulations using the code rebound (cite: rebound). The setup reproduced the V892 Tau system with 3 stars and a CBD. Stars were modelled as to massive point particles and the disc was modelled using 10 test particles with the same inclination and position angle as the disc in the SPH setups. The test particles semi-major axis extended from $14.2$ au to $200$ au, corresponding to the borders of the disc. Their eccentricity and mass were set to zero. In agreement with the data, the test particles start the simulation with a mutual inclination of $8\degree$ with the inner binary. Five simulations were performed with the same parameters as the SPH setups *ref, e05, i30, i60*, and *ei60*, respectively. The system is then integrated with an *ias15* integrator (cite: ias15) during $2000$ periods of the outer binary, corresponding to $\sim 9$ Myr.

# Results

In the following, we investigate the structure of the gaseous disc and its deviations from our Keplerian model (see Section [3.1](#subsec:discminer)). We focus our analysis on these deviations and to what extent the simulations are able to capture those non-Keplerian patterns.

## Channel maps

Figure [4](#fig:channels) shows the best-fit model channels from Discminer and their comparison to the data. The modelled emission in the channels fits well to the bulk emission of the data and the geometry of the disc is well captured by the Keplerian model. The best-fit inclination $i=54.7\degree$, position angle $PA=53.6\degree$ and dynamical mass $M_*=5.99$ M$_{\odot}$ are in line with previous observations (). The systemic velocity is found to be around the channels that are experiencing absorption from the cloud at $v_{sys}=7.86$ km s$^{-1}$. The disc is thin and sharply truncated at the outer edge given the best-fit lower and upper emission surfaces. The full details of the best-fit parameters and the priors used can be found in Table [5](#table:discminer_fit).

Looking at the emission in individual velocity channels allows the deviations to be tracked from the model at specific velocities. From $3$ km s$^{-1}$ to $4$ km s$^{-1}$, the data emission extends further than the model emission. This excess in emission is directed towards V892 Tau NE. The $3\sigma$ emission contour shows irregular features at the top of the channel emission up to $5.5$ km s$^{-1}$. From $5$ km s$^{-1}$ to $11.5$ km s$^{-1}$, the emission of the lower wing is truncated with respect to its model counterpart while the emission extent of the upper wing of each channel is well reproduced by the model. Small deviations are also observed in the south-west part of the $12.5-14$ km s$^{-1}$ channels and irregular patterns are seen especially in the $12.5$ km s$^{-1}$ channel. These deviations could be part of a larger non-detected structure (), as for instance large spiral arms commonly launched by external companion at the edge of discs. We discuss that possibility in more details in Section [4.4](#subsec:spirals). Other possible explanations for these non-Keplerian features include a warped disc or a discrepancy in vertical height between the data and the model (cite: Law+2023).

![](Figures/channel_maps_obs_model.pdf)

Data channels at $3.5$ km s$^{-1}$, $11$ km s$^{-1}$ and $12.5$ km s$^{-1}$ show clear deviations from our Keplerian model. On Figure [5](#fig:channel_comp), we look at these particular channels in the simulations and check if the deviations are reproduced or not. The lower surface of the disc is also visible in the simulations *ref*, *i30*, and *i60* at $3.5$ km s$^{-1}$ and $12.5$ km s$^{-1}$, which is not the case for the other simulations *e05* and *ei60* and the observations. The emission in the $11$ km s$^{-1}$ synthetic channel extends further out in *ref*, *i30*, *i60*, and *ei60*. In general the signal is higher in the synthetic channels than in the data. The closest match is made with the synthetic channels built from *e05*: the emission pattern is comparable to the data in terms of size, morphology, and intensity. The *e05* disc is sharply truncated and very thin due to most of the initial disc material being ejected by the companion at the beginning of the simulation. Some deviations are also recovered in the outer disc, suggesting that the kinematics observed in the data and *e05* are similar.

![](Figures/channels_comp_tot.pdf)

## Disc morphology

The moment maps built from the best-fit modelled channels by Discminer are shown in Figure [6](#fig:obs_model_panel), which includes the data moment maps and the residual maps in the detected disc area following the subtraction of that data and best-fit. In this section we discuss the disc morphology based on the intensity and temperature moment maps that we compare to their corresponding synthetic maps. The main features of the residual maps are highlighted on Figure [7](#fig:sketch_obs). The velocity and linewidth moment maps will be discussed in Sections [4.4](#subsec:spirals) and Appendix [11](#app : incl sign).

![image](Figures/panel_mom0.pdf) ![image](Figures/panel_T.pdf) ![image](Figures/panel_mom1.pdf) ![image](Figures/panel_Lw.pdf)

![](Figures/sketch_ftrs_blue.pdf)

On the moment 0 map, the residual patterns show two main arcs at the disc edges:

one to the north of the blueshifted side and one other to the south of the redshifted side. The first arc represents a brightness excess while the second indicates a brightness deficit. The two arcs are quite symmetric with respect to the inner binary. Such residuals have already been identified in (). The possible explanation invoked in that study was the presence of a warp in the disc and a different PA between the inner and outer disc. The arcs are also recovered in the peak temperature residual map. The latter map also shows a temperature excess oriented towards the south-west at the centre of the redshifted side of the disc (see Fig [7](#fig:sketch_obs)) which had also been detected in (). Thanks to a better angular resolution, we are able to see this asymmetry heading towards the western

direction as it reaches the outer disc. Globally, the V892 Tau CBD is found to be a warmer disc than most T Tauri stars (e.g. (cite: Wolfer+2023)), heated by the two A-type stars at its heart and with a peak brightness temperatures found up to a few $110$ K.

The centre of the disc is not well reproduced by our Keplerian model according to the high residual levels in the middle of the residual maps. The modelling of the inner system of V892 Tau is complicated by the absorption of channels around the systemic velocity at the centre of the system which puts it beyond the scope of this work.

Each tested orbit of the companion leads to a different morphology of the CBD, as shown in the snapshots of Figure [8](#fig:simgrid_rho). While the discs in the *ref* and *e05* simulations are oriented close to their initial orientation, the inclination and the PA of the discs in *i30*, *i60*, and *ei60* have significantly changed. We comment on the disc orientation in Section [4.5](#subsec:tilttwist) below. The disc in *e05* shows a limited radial extent due the repeated passages of the companion star close to the disc, which also spread out material that forms streamers between the companion and the CBD in all the simulations. The external companion also triggers two large spiral arms at the edge of the disc while the inner binary carves a central cavity in every simulated discs. Lastly, a thin circumstellar disc is sometimes captured by the companion at the periastron but dissipates shortly after due to the large accretion radius used for the sink particle representing the companion. One can see that the *i30*, *i60*, and *ei60* discs are mildly eccentric at the end of the simulation.

Figures [9](#fig:simgrid_mom0_synth), [10](#fig:simgrid_mom8_synth) and [11](#fig:simgrid_mom9_synth) show the moment 0, moment 8 (peak temperature) and moment 9 (velocity of the brightest pixel along the spectral axis) maps respectively of the post-processed SPH simulation outputs as described in the Section [3.3](#subsec:rt_proc). The synthetic moment 0 maps have generally a higher flux than the data by approximately a factor $3$ but have similar levels of peak intensity except for *e05* of which the flux is comparable. This is mainly due to the more extended emission in the simulations than in the observations. The CBDs of *ref* and *e05* exhibit a morphology comparable to the observations on the moment 0 map. The moment 0 maps of *i30* and *i60* show visible spirals in the outer disc and material forming streamers to the companion. Since such extended structures are not recovered in the data, it indicates that the companion triggers mild perturbations in the disc or an unbound scenario. The irregularities in the outer disc (see Fig [7](#fig:sketch_obs)) are recovered on the synthetic images of every simulation and trace faint material spread out by the companion. The synthetic moment 8 maps are generally brighter than the data (by a factor $3$ in brightness flux and by $50\%$ in peak value), but the average temperature in the outer disc is well reproduced. The NW side of the disc is seen warmer (by $10\%$ in average) and the warm twisted pattern in the redshifted side of the disc is recovered in all the simulations. The synthetic maps are more structured than the data: *ref*, *i30*, *i60*, and *ei60* present visible perturbations towards the companion that correspond to streamers linking the disc and the companion. The *e05* simulation also shows subtle perturbations at the same locations, which better matches the data. As seen in *e05*, material could stand beyond the outer disc and not being bright enough to be detected (see bottom second snapshot from the right on Fig [8](#fig:simgrid_rho) in comparison to the top right image on Fig [9](#fig:simgrid_mom0_synth)). In the same fashion, it is not excluded that the V892 Tau disc exhibits non-detected large scale structures which could be probed with deeper observations. Moreover the irregularities in the outer disc are similar between the data and *e05* (see Fig [9](#fig:simgrid_mom0_synth) and Fig [10](#fig:simgrid_mom8_synth)) and could trace similar structures.

![](Figures/sim_grid2.pdf)

![](Figures/mom0_synth.pdf)

![](Figures/mom8_synth.pdf)

![](Figures/mom9_synth.pdf)

## Disc extent

The disc radial extent is measured in the $^{12}$CO observational data up to $R_{90\%} = 1.45 \ensuremath{''}$ that corresponds to $194$ au with the adopted distance of $d=134.5$ pc. Figure [12](#fig:radial_extent) shows the intensity profiles of the observations and of the simulated discs and the resulting $R_{90\%}$ for these discs. The intensity profile drops inside the dust ring but the imaging of a potential inner cavity is made difficult by the absorption around the systemic velocity. The disc size and the radial intensity profile measured in our observations are comparable to those in previous works (see Table [\[table:comb_obs\]](#table:comb_obs) and ).

In our hydrodynamical simulations, the inner binary quickly carves a cavity in the inner gas disc. This cavity is $4-5 a_{in}$ large , where $a_{in}$ is the semi-major axis of the inner binary. Given the eccentricity and mass ratio of the V892 Tau inner binary, the inner rim of the cavity should lie at $\sim 3.5 a_{in}$ in the case of a coplanar disc (cite: Hirsh+2020) which is in rough agreement with our simulations. The discrepancy could be explained by the large accretion radii used for the sink particles of the inner binary components. Due to the long duration of our simulations and the high computational cost of small accretion radii, modelling the inner disc precisely can not be achieved precisely with our numerical setup and we rather focus on the truncation of the disc by the external companion star.

![](Figures/I_radial_profile.pdf)

Tidal truncation by the close outer companion swiftly takes place early in the simulations and material from the disc is spread out in the outer system. After $50$ simulated orbits of the outer companion, the spread material has been cleared in *ref*, *e05*, and *i30*. In *i60* and *ei60*, the size of the bulk of the disc is set after a few orbits of the companion even if particles are still ejected from the disc at the end of the simulation. If the companion follows an eccentric orbit, its periastron is closer to the disc and the truncation is stronger, resulting in a more compact disc. When the eccentricity is lower, the disc is allowed to spread radially. In the simulations *ref*, *i30*, and *i60*, the disc is much larger due to the truncation not being efficient enough or due to material being spread out by the companion. In the *ei60* simulation, the eccentricity of the companion is higher but as is the inclination which result in a larger closest distance approach. Added to the material populating the outer system and contributing significantly to the disc emission, the estimations of the disc radius are higher in *ei60*. In the end, the observations are in better agreement with the *e05* simulation as both show comparable disc sizes.

## Spiral arms and kinematics

The launch of spiral arms in a disc by an external companion is a well established result (cite: Rafikov2002) and has been observed in various systems already (e.g. HD100453 (cite: Benisty+2017), UX Tau (cite: Menard+2020)). A binary star at the heart of a CBD can produce spiral features as well (cite: Poblete+2019), that are most visible at the cavity edge that propagate towards the outer disc (e.g. AB Aur (cite: Poblete+2020), HD 142527 (cite: Price+2018)) whereas an external companion triggers two wide open spiral arms at the Lindblad resonances, where one arm is pointing towards the companion and the other lays in the symmetrical side of the disc. For an orbiting companion, the scale of the spirals is reduced as the disc is truncated with time (see Fig [8](#fig:simgrid_rho) and simulations in (cite: Menard+2020)).

The velocity residual map on Fig [6](#fig:obs_model_panel) shows the disc as dominated by the Keplerian rotation. The central regions of the system exhibit pronounced residuals, which may stem from cloud absorption within the corresponding channel emission. The residual patterns suggest that two opposite spiral arms are traversing the disc. One arm delineated by red residuals extends from the inner blueshifted region to the outer redshifted side, passing through the northern section of the disc. Symmetrically the other arm is marked by blue residuals in the southern regions of the disc. We highlight these spiral patterns on the sketch shown in Figure [7](#fig:sketch_obs). Spirals have been tentatively identified in the outer redshifted part of the disc (): a region where the disc is irregular and where brightness residuals are high. Our observations support the presence of a spiral arm at that location and unveil its potential symmetrical component.

In the light of our simulations that we describe below, we present this given geometry of trailing spirals in the disc as a tentative evidence of CBD-companion interactions. The presence of these interactions is also supported by the rotation curve derived from the gas emission model, and that we detail in Appendix [9.2](#subapp : rotation curve). Due to the scale and prominence of the spirals, the best match is done with the *e05* setup. Non-Keplerian features in the $9-11.5$ km s$^{-1}$ channel maps could also trace a large scale spiral structure and the truncated lower wing of the channel map emission mentioned in Section [4.1](#subsec:channels_result_part) could be consistent with a spiral perturbation at that location.

In every simulations performed, the outer companion triggers two large spiral arms in the disc when passing by the periastron. The spirals are sustained throughout the simulation runs and are visible in the column density rendered plots of the SPH setups of Figure [8](#fig:simgrid_rho). After the post-processing done, hints of spiral structures remain visible in the synthetic moment maps. In *ref*, *i30*, *i60* and *ei60* the two spiral arms are traced by the gas emission on the moment 0 map where patterns are mainly visible to the

south and north-west of the CBD. The peak velocity maps also show bright emission at the same locations in these simulations. However no clear spiral structure is seen in the moment 0 map of the *e05* simulation and no clear deviation is observed in the corresponding peak velocity map of that simulation. In the small disc of the *e05* simulation, the spirals disperse more rapidly and are of lower strength making their detection difficult when the companion comes close to apoastron. It suggests that faint spiral arms could be present in the V892 Tau disc.

Gravitational instability and embedded planets are also sources of spiral patterns in discs. However the triggering of the gravitational instability requires a disc massive enough for its self-gravity to dominate the gas pressure and rotation (cite: GoldreichLynden1965). This is expected when $M_{disc} > 0.1 M_*$ (cite: KratterLodato2016), which is not the case of the V892 Tau CBD where $M_{disc} \sim 0.01 M_*$. Embedded planets interactions with their host disc can result in the formation of two spiral arms with one of them pointing to the planet (e.g. (cite: Dong+2015)). It has also been showed that internal massive planets could reproduce spiral features in discs (cite: Calcino+2020). In our N-body simulations, planets in the inner system are ejected of the system by the inner binary (see Section [4.7](#subsec:V892TauNE)) making the scenario of a planet inside the dust cavity unlikely. Planets could survive at larger separations and trigger the observed spiral patterns, but our data does not allow us to comment on that possibility.

## Inclination and orientation of the disc

The tilt $\Delta$ is defined as the angle between the disc and the inner binary orbital plane. From our fitting process, we recovered a disc orientation (i, PA) very similar to what was derived in previous works (). Thus, we assumed the disc to have the same tilt as previously calculated. Due to an ambiguity of $180\degree$ on the inner binary position angle, the two possible tilt values are $\Delta = 8.0\pm 4.2\degree$ and $\Delta = 113.2\pm 3.0\degree$. We believe the disc to be close to coplanarity and rotating prograde with the companion star. In this way, we assumed a tilt of $\Delta \sim 8.0\degree$ to be more likely. We further motivate this assumption in Section [5.1](#subsec:final_incl). We measure the tilt $\Delta$ and the position angle (PA or $\Omega$) of the simulated discs by averaging the tilt and PA of all the SPH particles tilt and PA having a semi-major axis between the inner border of the disc and $200$ au, which corresponds to an upper limit of the disc extent.

On the one hand, in the setups where the companion is on a coplanar orbit with the disc and the inner binary (*ref* and *e05*) the inclination and the PA of the disc remained the same as the initialised values during the entire simulation. The tilt $\Delta$ and PA are then of $0\degree$ and $53\degree$ respectively at the end of the simulation for these setups. On the other hand, in the setups where the companion is on an inclined orbit with respect to the disc and the inner binary, namely *i30*, *i60*, and *ei60*, both the inclination and the PA of the disc oscillate periodically with time, as seen on Figure [13](#fig:tilttwist). The tilt oscillations damp with time and tend to a non-zero value with an amplitude of the oscillations starting at about $14\degree$, $17\degree$ and $18\degree$ for *i30*, *i60*, and *ei60* respectively. The PA of the disc decreases in average while oscillating with an amplitude of the oscillations appearing to be maintained.

For the inclined setups *i30*, *i60,* and *ei60,* we fitted the inclination of the disc with a damped oscillations model (see Equation [\[eq:tiltfit\]](#eq:tiltfit)). The PA is fitted by a linear model on the top of which are sinusoidal oscillations (see Equation [\[eq:twistfit\]](#eq:twistfit)). The model is adjusted to the simulation data using a non-linear least squares method. The disc relaxes from the initial conditions during the first orbits of the outer binary. We exclude at least the first $15$ orbits of the outer companion of the fitting process to neglect that effect. The best-fit results can be found in Table [3](#table:fit params). $$\begin{align}
    \label{eq:tiltfit}
    \Delta(t) = a_1 + a_2 e^{-a_3 t} \cos(2\pi a_4 t + a_5) , \\
    \label{eq:twistfit}
    \Omega(t) = b_1 + b_2 t + b_3 \cos(2\pi b_4 t + b_5) ,
\end{align}$$

The best-fit asymptotic tilt value is around $6\degree$ and $8\degree$ for *i30* and *i60* respectively. We notice that the *i60* value is in excellent agreement with the value derived in . Yet the *i30* value is consistent as well within the errorbars. In the case of *ei60*, the model indicates an asymptotic tilt value of $3.5\degree$. The $b_2$ parameter of the PA model can be converted into a precession timescale of $1619$ P$_{out}$, $923$ P$_{out}$ and $1003$ P$_{out}$ for *i30*, *i60*, and *ei60*, respectively. The uncertainty of the fit for these values is around $100$ P$_{out}$. The $a_3$ parameter of the tilt model can be converted into a damping time that is $85$ P$_{out}$, $226$ P$_{out}$ and $19$ P$_{out}$, which corresponds to approximately $0.3$ Myr, $0.9$ Myr and $0.08$ Myr for *i30*, *i60*, and *ei60*, respectively. The incertitude on these values is $<20$ P$_{out}$. The $a_4$ and $b_4$ parameters can be converted into an oscillation period of the disc that is fitted on the tilt profile to $14.8$ P$_{out}$ for *i30*, $19.3$ P$_{out}$ for *i60* and $10.1$ P$_{out}$ for *ei60*. We applied the same process to the PA oscillations to find a period of $15.2$ P$_{out}$ for *i30*, $20.9$ P$_{out}$ for *i60* and $10.2$ P$_{out}$ for *ei60*. The uncertainty of the fit for these values is of $<0.2$ P$_{out}$. The oscillation period is shorter in *ei60* than in *i30* and *i60*. We note that the oscillation period of the tilt and the PA are similar for a given simulation. We also note that our model does not account well for the *ei60* disc dynamics where the oscillations are quickly damped and the disc ends up close to coplanarity with the inner binary. We discuss in more detail those dynamical behaviours in Sections [5.1](#subsec:final_incl) and [5.2](#subsec:precession).

The previous results indicate that an inclined companion with respect to the inner binary is able to misalign a disc initially in the inner binary plane. It proves that a misaligned geometry between the inner binary and the outer companion is needed to explain the observed tilt value of $\Delta_{obs}=8\degree$ derived in , which is best reproduced by an inclination of $60\degree$ of the companion and a low eccentricity of it (*i60*). Considering the oscillations of the disc tilt, the disc could be caught in a middle of an oscillation and be measured misaligned with the inner binary. However when comparing the damping time of these oscillations to the estimated age of the system of $\sim 2$ Myr (cite: KucukAkkaya2010), it is unlikely that the disc is still undergoing significant oscillations.

![image](Figures/fit_tilt_i30.pdf) ![image](Figures/fit_tilt_i60.pdf) ![image](Figures/fit_tilt_ei60.pdf) ![image](Figures/fit_Omega_i30.pdf) ![image](Figures/fit_Omega_i60.pdf) ![image](Figures/fit_Omega_ei60.pdf)

+:------------------------------:+:-------------------:+:-------------------:+:-------------------:+
|                                | Tilt                                                            |
+--------------------------------+-----------------------------------------------------------------+
|                                | $\Delta(t) = a_1 + a_2 e^{-a_3 t} \cos(2\pi a_4 t + a_5)$       |
+--------------------------------+---------------------+---------------------+---------------------+
| Setup                          | *i30*               | *i60*               | *ei60*              |
+--------------------------------+---------------------+---------------------+---------------------+
| $a_1$ ($\degree$)              | $5.71\pm 0.10$      | $8.21\pm 0.05$      | $3.47\pm 0.11$      |
+--------------------------------+---------------------+---------------------+---------------------+
| $a_2$ ($\degree$)              | $6.03\pm 0.62$      | $-6.06\pm 0.22$     | $-19.59\pm 9.00$    |
+--------------------------------+---------------------+---------------------+---------------------+
| $a_3$ ($10^{-2}P_{out}^{-1}$)  | $1.10 \pm 0.31$     | $-0.44\pm 0.11$     | $5.32\pm 1.27$      |
+--------------------------------+---------------------+---------------------+---------------------+
| $a_4$ ($10^{-2}P_{out}^{-1}$)  | $6.77\pm 0.05 \;$   | $5.19\pm 0.02$      | $9.84\pm 0.15$      |
+--------------------------------+---------------------+---------------------+---------------------+
| $a_5$                          | $-5.18\pm 0.10$     | $4.71\pm 0.03$      | $1.96\pm 0.33$      |
+--------------------------------+---------------------+---------------------+---------------------+
|                                                                                                  |
+--------------------------------+-----------------------------------------------------------------+
|                                | Position Angle                                                  |
+--------------------------------+-----------------------------------------------------------------+
|                                | $\Omega(t) = a_1 + a_2 t + a_3 \cos(2\pi a_4 t + a_5)$          |
+--------------------------------+---------------------+---------------------+---------------------+
| Setup                          | *i30*               | *i60*               | *ei60*              |
+--------------------------------+---------------------+---------------------+---------------------+
| $b_1$ ($\degree$)              | $50.77\pm 0.53$     | $52.80\pm 0.20$     | $52.12\pm 0.57$     |
+--------------------------------+---------------------+---------------------+---------------------+
| $b_2$ ($\degree.P_{out}^{-1}$) | $-0.22\pm 0.02$     | $-0.39\pm 0.01$     | $-0.36\pm 0.02$     |
+--------------------------------+---------------------+---------------------+---------------------+
| $b_3$ ($\degree$)              | $-4.24\pm 0.19$     | $5.04\pm 0.07$      | $3.10\pm 0.15$      |
+--------------------------------+---------------------+---------------------+---------------------+
| $b_4$ ($10^{-2}P_{out}^{-1}$)  | $6.57\pm 0.08$      | $4.78\pm 0.02$      | $9.77\pm 0.10$      |
+--------------------------------+---------------------+---------------------+---------------------+
| $b_5$                          | $-3.82\pm 0.18$     | $8.53\pm 0.04$      | $-9.89\pm 0.27$     |
+--------------------------------+---------------------+---------------------+---------------------+

: Model functions for the tilt and the PA evolution and best-fit results for *i30*, *i60*, and *ei60*

|     |     |     |     |
|:---:|:---:|:---:|:---:|

: Model functions for the tilt and the PA evolution and best-fit results for *i30*, *i60*, and *ei60*

## Disc warp

A warp is a non-constant inclination radial profile appearing preferentially in thinner, less viscous and larger discs (cite: PapaloizouPringle1983; Young+2023). Disc warping is known to occur in CBDs around eccentric and inclined binaries (e.g. (cite: Nixon+2013; LodatoFacchini2013)) and in circumstellar disc perturbed by an external misaligned companion (cite: Gonzalez+2020). In non-coplanar triple systems, these two effects occurs simultaneously. Given the previous results, a misaligned orbit of V892 Tau NE could explain the observed disc tilt (see Section [4.5](#subsec:tilttwist)). If such an orbit is able to misalign the disc, it could be able in principle to trigger a warp in the disc too. In the following we investigate the presence of a warp in the CBD of V892 Tau.

In order to search for the presence of a warp in our simulated discs, the disc was binned in semi-major axis from the inner cavity edge $r_{in}$ to $r = 200$ au and the tilt $\Delta$ was measured in each bin taking the standard deviation of the tilt of the particles in a bin as the corresponding error. In the SPH data, the cavity semi-major axis $a_{cav}$ was defined as $\rho(a_{cav}) = \rho_{max}/2$ with $\rho_{max}$ defined as the maximum of the radial density profile (cite: Artymowicz1994). Since the disc eccentricity stays below $0.1$ during the simulation, the cavity semi-major axis can be identified as the cavity radius. At $t=50$ P$_{out}$, $a_{cav}=45$ au for *i30* and $a_{cav}=44$ au for *i60*.

We inspect and plot the radial distribution of the tilt $\Delta (r)$ of the setups *i30*, *i60* and *ei60* at different time steps on Figure [14](#fig:tilt_rad): $t=10$ P$_{out}$, $t=30$ P$_{out}$ and $t=50$ P$_{out}$. The inner binary, the outer binary and the discs stayed in a coplanar configuration for the initially coplanar setups *ref* and *e05*. In the setups where the companion is on an inclined orbit (namely *i30*, *i60*, and *ei60*) a warp forms steadily during the first orbits. The tilt profile $\Delta(r)$ shows a continuously but modestly increasing trend: the inner parts of the disc are misaligned by $1\degree$ to $4\degree$ with respect to the outermost parts after a few orbits of the companion. That tilt profile is maintained during the early moments of the simulation in all the simulations with an inclined companion. However the disc becomes planar again within the errorbars after a time $t=30$ P$_{out}$. The companion bends the outer parts of the CBD at the beginning of the simulation, which creates a warp propagating in the bending wave regime (cite: PapaloizouTerquem1995) to the innermost parts of the disc. Because of the loss of material in the disc and its truncation by the companion, the disc behaves more and more rigidly with time. In this way, the strongest warping occurs at the beginning of the simulation. After a few orbits of the companion once the disc truncated enough, the tidal torque of the companion is insufficient to warp the disc: the warp is damped and the disc becomes planar again (cite: Deng+2021). At the end of the simulations, the disc can be considered planar within the errorbars and the amplitude of a potential warp in the disc would be only that of a few degrees. Measuring such a low warp our synthetic data is challenging and require a more in-depth analysis that we left for future studies. In the meantime, we favour a planar configuration for the discs in our simulations.

A warp in the CBD has been invoked to explain deviations from simple models (cite: Long+2021; Vides+2023). Residuals from our Keplerian model are similar to these deviations: the arcs at the disc edges on the moment 0 and peak temperature residual maps (see Figure [6](#fig:obs_model_panel) and Section [4.2](#subsec:disc_morph)) could be hints of a misalignment between the inner disc and the outer disc. According to the orbital parameters of the inner binary, the disc could be warped under the tidal torque of the binary if sufficiently misaligned (see Section [5.1](#subsec:final_incl)). V892 Tau NE could also warp the disc, if on a misaligned orbit with respect to the disc. We found the CBD of V892 Tau to be a thin disc with an emission surface aspect ratio of z/r$\sim$0.16 at 100 au, where most discs around young stars are found with z/r\>0.3 in the $^{12}$CO emission (cite: Law+2021). The disc of V892 Tau is also moderately extended. Thus we expect warping to be difficult in the disc. The high temperature in the disc up to $\sim 110$ K makes it prone to damp any potential warp (e.g. (cite: Rabago+2023)). In the end, even if the observed residuals could be consistent with a warped disc, the combined dataset used in this work can not robustly rule out nor confirm the presence of a warp in the disc.

![](Figures/tilt_radial_profile.pdf)

## The orbit of V892 Tau NE

### The flyby scenario

The orbit of V892 Tau NE is currently unconstrained. This means that V892 Tau NE could in principle be totally unbound to V892 Tau or following a flyby parabolic/hyperbolic orbit. In the unbound case, V892 Tau would be considered as a binary system. In such a configuration, a coplanar disc with respect to the inner binary and does not precess (see Appendix [12](#app : binary sims) for details). It means that the inner binary alone cannot explain the observed disc tilt, which allows us to rule out the unbound scenario. Moreover it has been recently shown that V892 Tau and V892 Tau NE are likely related (cite: Thomas+2023). In the case of a flyby event, efficient truncation and the formation of prominent short-lived spirals are expected (cite: Cuello+2019; Cuello+2020; Cuello+2023; Smallwood+2023). We can study the flyby scenario in our simulations by considering the state of the disc after the first orbit of the companion. Figure [8](#fig:simgrid_rho) shows column density views of the simulated discs after the completion of the first companion orbit. In all the simulations, dense spiral arms are triggered in the disc by the passage of the companion. The disc remains close to its original size, that is similar to the observed one, in all the simulations despite material being ejected. If the companion was to follow an inclined orbit with respect to the inner binary, Fig. [13](#fig:tilttwist) shows that the disc would be misaligned by $1-2\deg$ at the end of the first orbit considered here as the end of the flyby event. In our simulations, the companion approaches the disc closely with a closest distance no greater than 200 au. A more distant flyby would have produced fainter spirals and lower misalignments (cite: Cuello+2019). In any case, the subtle observed spiral patterns and the disc tilt of $\sim 8\deg$ suggest that a flyby event is unlikely to have happened in V892 Tau.

### Constraints on a bound orbit

+:------------:+:--------:+:--------:+:--------:+:--------:+:--------:+
| Criterion    | Simulation                                           |
+--------------+----------+----------+----------+----------+----------+
|              | *ref*    | *e05*    | *i30*    | *i60*    | *ei60*   |
+--------------+----------+----------+----------+----------+----------+
| Channel maps | $\times$ |          | $\times$ | $\times$ | $\sim$   |
+--------------+----------+----------+----------+----------+----------+
| Disc extent  | $\times$ |          | $\times$ | $\times$ | $\times$ |
+--------------+----------+----------+----------+----------+----------+
| Disc tilt    | $\times$ | $\times$ |          |          | $\sim$   |
+--------------+----------+----------+----------+----------+----------+
| Spirals      | $\sim$   |          | $\sim$   | $\sim$   | $\sim$   |
+--------------+----------+----------+----------+----------+----------+

: Summary of the observed disc features and to what extent they are reproduced by the different simulations.

Table [4](#table:best_sim) summarises the constraints placed on the V892 Tau NE orbit through our modelling of the V892 Tau disc. If bound, a medium eccentricity of the orbit of V892 Tau NE is needed to explain the observed disc extent while the orbit has also to be misaligned with respect to the inner binary to explain the slight misalignment between the disc and the inner binary. In such a configuration, the orbit of V892 Tau NE cannot be too eccentric ($e>0.5$), as high eccentricities tend to align the disc with the inner binary (Figure [13](#fig:tilttwist)).

From the points of the parameter space we probed with our simulations, we suggest constraints on the parameter eccentricity and mutual inclination of V892 Tau NE of $0.2<e<0.5$ and $30\degree < \Delta i < 60\degree$ respectively. If V892 Tau NE was to follow an eccentric inclined orbit, we expect the CBD to oscillate and precess in the light of the discs in the setups *i30*, *i60*, and *ei60*. According to our simulations, the CBD inclination oscillates with time and these oscillations are damped over a period of $\sim 1000$ yrs. Then the tilt of the disc reaches a non zero final value of $3\degree$ to $8\degree$ which is in good agreement with the observed value of $\sim 8\degree$. In such a configuration, we expect the disc $PA$ to oscillate with time on top of a linear precession. We discuss the non-coplanar configuration of the system and the resulting disc dynamics in the Sections [5.1](#subsec:final_incl) and [5.2](#subsec:precession) below.

## Stability of future planets

Considering the results of the previous Section [4.7](#subsec:V892TauNE), we consider the dynamics of planets in a system following the *ei60* orbital configuration. Although not fully encompassing all disc features, the parameter set represented by *ei60* delineates the boundary of the parameter space governing an inclined eccentric orbit of the companion. We anticipate that this particular configuration will induce the most pronounced perturbations on planets within the system, as alternative configurations would entail lower eccentricity and/or mutual inclination of the companion. Consequently, we present the following results as a worst-case scenario for the prospective planets in the system. The results for the other N-body setups can be found in Appendix [13](#app : nbody).

The stability of circumbinary planets in a system in the *ei60* configuration depends on the planets semi-major axis first. Figure [15](#fig:nbody) shows the evolution of the test particles in the N-body simulation of *ei60*, which is described in Section [3.4](#subsec:nbody). The test particles with a semi-major axis $a \geq 100$ au were ejected from the system during the simulation. The innermost test particle at $a = 20$ au was also gravitationally ejected from the system by the inner binary during the first orbit of the outer companion. Particles in between $a = 40$ au and $a = 80$ au remained stable during the simulation. This can be explained by the competition between two dynamical effects. First due to the presence of the misaligned companion, the test particles undergo von Zeipel-Kozai-Lidov (vZKL hereafter) cycles (cite: vonZeipel1910; Kozai1962; Lidov1962) with a characteristic timescale of $\sim 90$ P$_{out}$ at $100$ au (cite: Ceppi+2023). This effect results in a rise and oscillations in eccentricity and inclination of the test particles leading to the ejection of the test particles closer to the external star. Second the inner binary induces a nodal precession of the test particles around its angular momentum vector with a timescale of $\sim 98$ P$_{out}$ at $100$ au (e.g. (cite: FaragoLaskar2010; LodatoFacchini2013)). Closer to the inner binary, the timescale of this precession is lower than the vZKL timescale, stabilising the particles in the inner half of the disc ($a \leq 100$ au) (cite: VerrierEvans2009).

Still, the particles found stable at the end of the simulation were undergoing large oscillations in inclination (and eccentricity for the test particle at $a=80$ au) that questions their future stability on longer timescales. Thus if the current gas disc is ensuring the stability of forming planets, those planets could become unstable once the gas disc dissipated. On longer timescales, it implies the migration of circumbinary forming planets towards stable regions at an intermediate distance from the inner binary between $40$ au and $80$ au. We discuss these results in more details in the Section [5.3](#subsec:planetary_arch).

![image](Figures/nbody_ei60_a.pdf) ![image](Figures/nbody_ei60_e.pdf) ![image](Figures/nbody_ei60_i.pdf)

# Discussion

## Final inclination of the disc

CBDs are expected to reach a stable coplanar or polar configuration depending on the properties of the inner binary and of the initial mutual inclination. If the initial misalignment and the eccentricity of the inner binary are low, the disc is expected to move into a coplanar configuration (cite: Facchini+2013). On the opposite, for binaries with higher eccentricity and a high mutual inclination the CBD is expected to evolve towards a polar configuration (cite: Aly+2015; MartinLubow2017; Cuello&Giupponne2019). Nonetheless CBDs have been found with a medium mutual inclination with their inner binary in a configuration that is not coplanar nor polar. For example the CBD around GG Tau A is inclined of about $25\degree$ with respected to the inner binary (cite: Kohler2011; Andrews+2014). In SR24, the tilt of the CBD is around $35\degree$ with respect to the binary SR24N (cite: Fernandez_Lopez+2017). These non-zero tilt values could be explained by oscillations around the final configuration of the disc before reaching the equilibrium coplanar configuration. In hierarchical triple systems as V892 Tau, the picture is modified by the evolution of the stellar orbits that can occur on shorter timescales with respect to the disc lifetime. In particular in misaligned systems, the inclination of the orbits can change with time meaning that the intermediate tilt of CBDs could be due to the slow reaction of the disc to these variations (cite: Ceppi+2023). This means that the disc of V892 Tau could eventually be seen misaligned with the inner binary even if the orbit of the companion has a different inclination. Such a misalignment would be created over the timescale of the orbit evolution that we assume to be the precession timescale of the eccentricity vector. We find that the precession timescale of the inner (outer) binary is about $6000$ Myr ($24$ Myr) for V892 Tau (cite: Ceppi+2023). Compared to a typical disc lifetime of $10$ Myr (cite: Ribas2015) and to our $0.2$ Myr-long simulation runs, the orbital configurations tested in *ref* and *e05* setups are not expected to become misaligned with respect to the disc.

The CBD of V892 Tau is found with a misalignment of approximately $8\degree$ or $113\degree$ with the inner binary of eccentricity $0.25$ (, (cite: Vides+2023)). The two possible solutions derive from a lack of radial velocity information on the inner binary, making its true inclination difficult to constrain. If considered as a CBD in a triple system with the *ei60* orbital configuration, the disc of V892 Tau could go to a stable polar configuration (cite: Martin+2022; Ceppi+2023). The large semi major axis and the low mass of the companion do not hinder the polar alignment. However, polar alignment would require the disc to be initially misaligned by $66\degree$ or more (). In our simulations, the disc was initialised coplanar with the inner binary. Our simulations indicates that a misalignment of $\sim 8\degree$ is created and sustained by the outer companion. The disc oscillates around that equilibrium position. Given the proximity of our best-fit tilt value, we prefer the nearly coplanar configuration for the disc in the end. This non-zero tilt value shows that intermediate configurations are stable for CBDs, independently of secular dynamics of the stars in the system. The V892 Tau disc is in a sweet-spot of the parameter space that would allow this kind of configuration. In order to achieve this, the semi-major axis ratio between the inner and outer binaries should be relatively large and the inclination of the companion with respect to the inner binary around a medium value of $\sim 45\degree$. Future studies to characterise CBDs inclination in triple system as a function of the companion inclination would help to better understand this problem.

## Oscillations and precession

Due to gravitational torques applied by misaligned stars, discs in multiple systems very commonly undergo precession in the sense that their PA is evolving with time. Linear precession can occur in binary systems in CBD and circumstellar discs (e.g. (cite: PapaloizouTerquem1995)). Simulations of binary systems have already observed this phenomenon (e.g. HD 100453 (cite: Gonzalez+2020; Nealon+2020), GW Ori (cite: Smallwood+2021)).

We find that the V892 Tau CBD is linearly precessing but that its PA also oscillates with time (see Fig [13](#fig:tilttwist)). Assuming V892 Tau and V892 Tau NE as a binary system, the expected precession timescale of the disc is about $144$ P$_{out}$ for *i30* and $251$ P$_{out}$ for *i60* (following Eq. 6 from (cite: Gonzalez+2020) derived from (cite: Bate+2000) and (cite: Terquem+1998)). This is well below the precession timescales found in Section [4.5](#subsec:tilttwist). However these estimations are in line with precession timescales measured in simulations where the system is represented by only a binary. Those simulations are identical to *i30* and *i60* except that the inner binary is replaced by a single star of the same mass (see Appendix [12](#app : binary sims)). As seen on Figure [21](#fig:SPH_comp_binaries), the evolution of the tilt and PA of the disc in those binary-system simulations is different from the one in the triple-system simulations. The discs in the *i30* and *i60* runs start to linearly precess at the same rate as in the binary-system simulations, but their precession is then slowed down by the inner binary. It indicates that the disc dynamics are set by the triplicity of the system, that can not be simplified as a binary system.

In binary systems, a misaligned circumstellar disc is expected to align to the binary orbital plane in about a precession timescale in the presence of hydrodynamical instabilities such as the warp developed at the beginning of our simulations (cite: Bate+2000). In the binary-system simulations, the disc starts to align on a timescale in line with that prediction. However in *i30*, *i60* (and *ei60*) the disc oscillates and ends up misaligned with the orbital planes. The gravitational torques of both the inner and the outer binary try to align the disc in their respective planes that results in an equilibrium position in between those planes. It shows again that when considering the disc dynamics the misaligned hierarchical triple system V892 Tau can not be reduced to a binary system.

In the *i60* and *ei60* simulation setups, vZKL oscillations could be triggered in the CBD that would result in the disc eccentricity and inclination oscillating with time (cite: Martin+2014). As the inclination oscillation pattern are similar in *i30* and *i60*, this strength of this effect is low in *i60*. However knowing that the vZKL timescale decreases with a higher eccentricity of the outer orbit (e.g. (cite: Kiseleva+1998)), vZKL cycles could explain the dynamical behaviour. The vZKL timescale for *ei60* is about $\sim 16$ P$_{out}$ at $100$ au (cite: Ceppi+2023), which is comparable to the oscillation period in *ei60* (see Figure [13](#fig:tilttwist)). Moreover the CBD of the *ei60* SPH simulation shows clear eccentricity, showing the clear influence of the vZKL mechanism on this disc.

The disc is subject to the combined gravitational torques of the external companion and of the inner binary. While in the case of a binary system a linear precession is expected, in a triple system oscillations are also expected. This peculiar precession can be assessed by measuring the tilt $\Delta$ and the twist $\beta$. These oscillations, projected in the 2D sky plane, are traced by the disc inclination and PA. Previous studies have used complex variables to examine the dynamical evolution of discs (e.g. for eccentricity modes in the context of planet-disc interactions (cite: Ragusa+2018)). A similar study of the complex variable $\Delta = |\Delta| \exp(j\beta)$, where $j$ is the complex number, could help to clarify the connection between the tilt and twist oscillations and the resulting evolution of misaligned CBDs in triple systems.

## Resulting planetary architectures

In its current configuration, the misaligned disc of V892 Tau could result in the formation of misaligned planets with respect to the inner binary. Though those planets would have to migrate to the inner half of the disc to survive in the system (see Section [4.8](#subsec:nbody-result)). It is unclear to what extent this migration would impact the orbital elements of the planet. If the planet was to tilt relatively to the disc plane, this tilt would be damped and the planet would re-align (cite: Burns1976; TanakaWard2004). In the case of V892 Tau the resulting planets would stay close to the disc plane, inclined with respect to inner binary. The stability of inclined planets in hierarchical triple systems depends on the stellar orbital configuration. In triple systems with low semi-major axis ratio ($<20$) and eccentricity of the outer orbit, the outer bound of the stability zone is limited. If the mutual inclination between the companion star and the inner binary is not zero, the planets stability region extends vertically allowing for high inclination (cite: Busetti+2018). In that configuration, circular planets that form coplanar with the inner binary end up with their $i$ and $\Omega$ parameters oscillating on timescales several order of magnitude longer than the orbital period (cite: Busetti+2018). The inclination between the planet and the inner binary also sets the stability regime. Planets are generally found stable close to coplanarity with the inner binary, regardless of the inclination of the outer star. In the *ei60* configuration of V892 Tau, the stability region extends up to $\sim 100$ au from the inner binary and up to misalignments of the planet of $\sim 30\degree$ (cite: Gianuzzi+2024). Putting that result together with the results described in Section [4.8](#subsec:nbody-result), we expect future planets in the V892 Tau system to form at intermediate distance from the centre of the system between $40$ au to $80$ au with mild inclination with respect to the inner binary.

The dust disc of V892 Tau is one of the most massive class II disc (), potentially presenting an abundant pebble reservoir. The horseshoe asymmetry seen in the continuum could be explained by an over-density created by the inner binary, which could enhance planet formation at that particular location. Misaligned and warped discs around eccentric binaries are also subject to dust concentrations triggered by the difference in precession timescale between dust and gas, which results in dust traps and favours planet formation (cite: Aly+2021; Aly+2023). More advanced dust+gas hydrodynamical simulations would allow for the presence of warp instabilities in the V892 Tau CBD to be assessed and this would help to understand planet formation in triple systems in general.

## Circumbinary discs interactions with an external companion

In the system of V892 Tau, the inner binary dominates the mass budget and the low mass companion V892 Tau NE tidally interacts with the CBD. It induces spiral patterns within the disc, a truncation of the outer disc, a slight misalignment with the inner binary but no sustained warped geometry. In the following we explore how, given observations of a CBD, similar structures can be explained by ongoing interactions with an hypothetical companion. This companion may either follow a bound orbit around the inner binary or have been involved in a flyby event. In the absence of identifiable candidates in the vicinity of the CBD, *Gaia* astrometry remains a viable method to search for potential past external flyby occurrences.

Repeated or not, the passage of a star close to the CBD would dramatically reduce the size of the CBD by tidal truncation (e.g. (cite: Artymowicz1994; MirandaLai2015)), providing a potential explanation of small CBDs. The efficiency of truncation increases with a higher mass ratio between the inner binary and the outer companion, as well as with greater eccentricity or a smaller semi-major axis of the companion. During a close encounter, the companion may also accrete material from the CBD, leading to the formation of a new disc and associated streamers (e.g. VLA 1623-2417 (cite: Mercimek+2023), FU Ori-like systems (cite: Borchert+2022)).

CBD-binary misalignments are common and expected in binary systems and can find their origin in interactions with surrounding stars (cite: Czekala+2019; Elsender+2023). Indeed an external perturber would exert a gravitational torque on the CBD, if misaligned with respect to each other, aligning the CBD with the orbital plane of the perturber (cite: PapaloizouTerquem1995). Should the misalignment between the CBD and the inner binary reach a critical angle, the CBD may transition towards a polar configuration relatively to the (eccentric) inner binary (cite: MartinLubow2017; Martin+2022; Ceppi+2023). The disc can also become warped in the process or break at a given radius depending on the inner binary parameters (e.g. (cite: Nixon+2013; LodatoFacchini2013)). All these effects are enhanced by large companion to inner binary mass ratios and high misalignment degrees to the perturber, or in the case of a retrograde flyby (cite: Cuello+2019).

The observation of two diametrically

opposed spirals in the CBDs, as in AS 205 (cite: Kurtovic+2018), suggests the occurrence of a flyby event. Indeed, any close encounter would invariably induce spiral density waves within the disc through tidal effects (cite: Rafikov2002). Prograde encounters and close flybys tend to induce the formation of prominent spiral arms, whereas bound companions typically result in less conspicuous spiral arms (e.g. (cite: Cuello+2019; Menard+2020)).

However if none of the aforementioned structures are detected in a CBD, it remains plausible that the disc has undergone relaxation over time due to prior interactions with neighbouring stars. Lastly, some multiple systems show a lack of CBD (e.g. HT Lup; (cite: Kurtovic+2018), Sz65&Sz66; (cite: Miley+2024)). This absence could be attributed to the considerable separation between the binary components precluding the formation of a CBD (cite: Harris+2012; Elsender+2023). Moreover the hypothetical existence of such a disc suggests rapid dispersal, possibly stemming from intense interactions with a neighbouring star. These interactions could range from dramatic events like disc-penetrating flybys (cite: Cuello+2023) to the influence of additional radiation enhancing photoevaporation (cite: Dai+2018). In any case, a detailed systematic study of CBD in triple systems exploring the wide range of available orbital configurations will help to properly understand the previously cited effects.

## Limitations and caveats

The main limitation of our work is the low number of orbital configurations tested. Considering the total lack of orbital information on V892 Tau NE, we proposed orbital arrangements that could trigger the observed structures in the CBD. Admittedly our goal was not to thoroughly sample the available parameter space for the orbit of V892 Tau NE, which would have been too computationally demanding with SPH simulations. Instead we chose to model V892 Tau as a triple system with a CBD in order to put constraints on the companion’s orbit. Without any astrometric measurements available and considering the well-characterised inner binary orbit, disc forward modelling constitutes the most reliable method to infer the long-period orbit of V892 Tau NE.

We ensured an optimal quality of the data by combining previous datasets with new observations. Our disc model (surface density exponent, aspect ratio, viscosity, etc.) and the values used in the radiative calculations (dust to gas mass ratio, CO abundance, freeze-out temperature, etc...) are all typical values found in the literature for class II protoplanetary discs. We used gas only simulations for computational reasons. Therefore the dynamics of large dust grains (marginally coupled to gas) is not fully consistent. At any rate, in this work we focus on an in-depth study of the gas morphology and kinematics, which is marginally affected by our assumption regarding the gas-dust coupling.

Differences between the data and our synthetic maps could come from our numerical setup. Due to a lack of numerical resolution, the inner system is not well reproduced in our simulations. Absorption of the parent cloud at the centre of the system also limits its precise modelling. For example the circumprimary disc can not be captured due to an accretion radius of the sink particles being much larger than its expected physical size. This could explain the flux difference between our images and the data, as this narrow disc could capture incoming radiation of the primary. Also the large accretion radii of the sinks translate into an inner cavity wider than the one observed.

Last, the expense of the presented hydrodynamical simulations prohibits us from evolving the system until its equilibrium state. However our simulations reached a state close to this equilibrium, as the size of the bulk of the disc does not significantly change in the last $20$ orbits of the companion. Therefore our simulations are long enough to reasonably infer the long-term disc behaviour. For longer evolutionary times, we expect the companion to clear even more material in the outer regions, which should lead to smaller disc sizes — potentially in better agreement with the observations, especially for *ei60*.

# Conclusion

In this paper, we presented new ALMA Band 6 observations of V892 Tau at a high spatial and spectral resolution. We confirmed the presence of structures in the disc, which we interpreted as hints of an interaction with the companion star V892 Tau NE. Using 3D SPH simulations, we modelled V892 Tau as a triple system with a CBD and produced synthetic ALMA maps comparable to the observations. We investigated the available orbits for V892 Tau NE on the basis of their ability to reproduce the data. Once the orbital configuration was constrained, we discussed the resulting disc dynamics and planetary architectures.

Our main findings are summarised as follows:

1.  Our observations confirm the hints of an ongoing interaction between the circumbinary disc around V892 Tau and V892 Tau NE. The disc extent is consistent with tidal truncation models. Even if dominated by Keplerian rotation, the CBD harbours non-Keplerian structures that are seen in the channel maps and moment maps, such as spiral features.

    Finally, the data neither conclusively support nor refute the existence of a warp in the disc.

2.  An eccentric inclined orbit of V892 Tau NE reproduces features compatible with the disc observations. A non-zero mutual inclination of the companion with respect to the inner binary best explains the slight tilt of the disc. Given our limited parameter space sampling, this tilt seems to be reproduced best by a mutual inclination of $60\degree$. The eccentricity of the companion sets the disc extent, which seems to be reproduced best by eccentricity values around $0.5$.

3.  The misalignment between the inner binary and V892 Tau NE triggers disc damped oscillations in inclination and a non-linear precession. At equilibrium, the disc mid-plane is close to being coplanar with the inner binary, but on a slightly misaligned plane with respect to the orbital planes of the stars. Remarkably, the observed dynamical state of the disc cannot be explained using binary system models alone.

4.  Given the likely orbital configuration of V892 Tau and assuming planets will form in the disc, these circumbinary planets would become unstable in the very inner parts and in the outer parts of the disc — as soon as the gas dissipates. Any surviving planet should have an intermediate semi-major axis between $40$ au and $80$ au and is expected to undergo significant oscillations in eccentricity and inclination due to the interactions with the external companion.

Based on our investigation, V892 Tau constitutes the archetype of a hierarchical triple system with a CBD, standing out as a unique test bed for planet formation in multiple stellar systems. However, to thoroughly infer the available formation channels of circumbinary planets in such systems, detailed studies on dust dynamics and growth are required. In addition, future near-IR observations would be key to further characterise the disc content and morphology, which would add complementary and independent constraints on the disc structure. By combining this information to gas-dust hydrodynamical simulations coupled to dust growth algorithms, we could in principle identify the possible regions of planet formation in V892 Tau. This would pave the way for a global understanding of planet formation and dynamics in the context of multiple systems.

# Acknowledgements

This project has received funding from the European Research Council (ERC) under the European Union Horizon Europe programme (grant agreement No. 101042275, project Stellar-MADE). The Geryon2 cluster housed at the Centro de Astro-Ingeniería UC was used for the calculations performed in this paper. The BASAL PFB-06 CATA, Anillo ACT-86, FONDEQUIP AIC-57, and QUIMAL 130008 provided funding for several improvements to the Geryon/Geryon2 cluster. Some of the computations presented in this paper were performed using the GRICAD infrastructure (<https://gricad.univ-grenoble-alpes.fr>), which is supported by Grenoble research communities. A.R. has been supported by the UK Science and Technology research Council (STFC) via the consolidated grant ST/W000997/1 and by the European Union’s Horizon 2020 research and innovation programme under the Marie Sklodowska-Curie grant agreement No. 823823 (RISE DUSTBUSTERS project). R.N. acknowledges support from UKRI/EPSRC through a Stephen Hawking Fellowship (EP/T017287/1). Support for AI was provided by NASA through the NASA Hubble Fellowship grant No. HST-HF2-51532.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.01137.S., ADS/JAO.ALMA#2013.1.00498.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The data underlying this article will be shared on reasonable request to the corresponding author. The code Phantom used in this work is publicly available at <https://github.com/danieljprice/phantom>. The Discminer code used in this study is open source and can be found at <https://github.com/andizq/discminer>. This work makes use of Splash (cite: splash), Numpy (cite: numpy) and Matplotlib (cite: Matplotlib). We also acknowledge the use of Sarracen (cite: Sarracen). AA would like to extend his sincere appreciation to Jean-François Gonzalez and Enrico Ragusa for their fruitful discussions throughout the course of this research. We would like to express our profound gratitude to the anonymous referee for their insightful comments and suggestions which have greatly contributed to the improvement of this work.

106 natexlab

(ref: Aly+2015) Aly, H., Dehnen, W., Nixon, C., & King, A. 2015, MNRAS, 449, 65

(ref: Aly+2021) Aly, H., Gonzalez, J.-F., Nealon, R., et al. 2021, MNRAS, 508, 2743

(ref: Aly+2023) Aly, H., Nealon, R., & Gonzalez, J.-F. 2023, MNRAS \[\]

(ref: Andre+2010) André, P., Men’shchikov, A., Bontemps, S., et al. 2010, A&A, 518, L102

(ref: Andrews+2014) Andrews, S. M., Chandler, C. J., Isella, A., et al. 2014, ApJ, 787, 148

(ref: Artymowicz1994) Artymowicz, P. & Lubow, S. H. 1994, ApJ, 421, 651

(ref: Bate2018) Bate, M. R. 2018, MNRAS, 475, 5618

(ref: Bate+2000) Bate, M. R., Bonnell, I. A., Clarke, C. J., et al. 2000, MNRAS, 317, 773

(ref: Bate+1995) Bate, M. R., Bonnell, I. A., & Price, N. M. 1995, MNRAS, 277, 362

(ref: Benisty+2017) Benisty, M., Stolker, T., Pohl, A., et al. 2017, A&A, 597, A42

(ref: Borchert+2022) Borchert, E. M. A., Price, D. J., Pinte, C., & Cuello, N. 2022, MNRAS, 517, 4436

(ref: Briggs) Briggs, D. S. 1995, in American Astronomical Society Meeting Abstracts, Vol. 187, American Astronomical Society Meeting Abstracts, 112.02

(ref: Burns1976) Burns, J. A. 1976, American Journal of Physics, 44, 944

(ref: Busetti+2018) Busetti, F., Beust, H., & Harley, C. 2018, A&A, 619, A91

(ref: Calcino+2020) Calcino, J., Christiaens, V., Price, D. J., et al. 2020, MNRAS, 498, 639

(ref: Ceppi+2023) Ceppi, S., Longarini, C., Lodato, G., Cuello, N., & Lubow, S. H. 2023, MNRAS, 520, 5817

(ref: Cuello+2019) Cuello, N., Dipierro, G., Mentiplay, D., et al. 2019, MNRAS, 483, 4114

(ref: Cuello&Giupponne2019) Cuello, N. & Giuppone, C. A. 2019, A&A, 628, A119

(ref: Cuello+2020) Cuello, N., Louvet, F., Mentiplay, D., et al. 2020, MNRAS, 491, 504

(ref: Cuello+2023) Cuello, N., Ménard, F., & Price, D. J. 2023, European Physical Journal Plus, 138, 11

(ref: Czekala+2019) Czekala, I., Chiang, E., Andrews, S. M., et al. 2019, ApJ, 883, 22

(ref: Dai+2018) Dai, Y.-Z., Liu, H.-G., Wu, W.-B., et al. 2018, MNRAS, 480, 4080

(ref: Deng+2021) Deng, H., Ogilvie, G. I., & Mayer, L. 2021, MNRAS, 500, 4248

(ref: Dong+2015) Dong, R., Zhu, Z., Rafikov, R. R., & Stone, J. M. 2015, ApJL, 809, L5

(ref: DucheneKraus2013) Duchêne, G. & Kraus, A. 2013, ARA&A, 51, 269

(ref: Elsender+2023) Elsender, D., Bate, M. R., Lakeland, B. S., Jensen, E. L. N., & Lubow, S. H. 2023, MNRAS, 523, 4353

(ref: EsplinLuhman2019) Esplin, T. L. & Luhman, K. L. 2019, AJ, 158, 54

(ref: Facchini+2013) Facchini, S., Lodato, G., & Price, D. J. 2013, MNRAS, 433, 2142

(ref: FaragoLaskar2010) Farago, F. & Laskar, J. 2010, MNRAS, 401, 1189

(ref: Fernandez_Lopez+2017) Fernández-López, M., Zapata, L. A., & Gabbasov, R. 2017, ApJ, 845, 10

(ref: Flores+2022) Flores, C., Connelley, M. S., Reipurth, B., & Duchêne, G. 2022, ApJ, 925, 21

(ref: emcee) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: GaiaDR3) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1

(ref: Gianuzzi+2024) Gianuzzi, E., Cuello, N., Giuppone, C., & Sucerqueia, M. 2024, A&A, in preparation

(ref: GoldreichLynden1965) Goldreich, P. & Lynden-Bell, D. 1965, MNRAS, 130, 97

(ref: Gonzalez+2020) Gonzalez, J.-F., van der Plas, G., Pinte, C., et al. 2020, MNRAS, 499, 3837

(ref: Griffin+2010) Griffin, M. J., Abergel, A., Abreu, A., et al. 2010, A&A, 518, L3

(ref: Sarracen) Harris, A. & Tricco, T. 2023, The Journal of Open Source Software, 8, 5263

(ref: numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: Harris+2012) Harris, R. J., Andrews, S. M., Wilner, D. J., & Kraus, A. L. 2012, ApJ, 751, 115

(ref: Hirsh+2020) Hirsh, K., Price, D. J., Gonzalez, J.-F., Ubeira-Gabellini, M. G., & Ragusa, E. 2020, MNRAS, 498, 2936

(ref: Matplotlib) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90

(ref: DiscminerI) Izquierdo, A. F., Testi, L., Facchini, S., Rosotti, G. P., & van Dishoeck, E. F. 2021, A&A, 650, A179

(ref: DiscminerII) Izquierdo, A. F., Testi, L., Facchini, S., et al. 2023, A&A, 674, A113

(ref: Kenyon+2008) Kenyon, S. J., Gómez, M., & Whitney, B. A. 2008, in Handbook of Star Forming Regions, Volume I, ed. B. Reipurth, Vol. 4, 405

(ref: Kiseleva+1998) Kiseleva, L. G., Eggleton, P. P., & Mikkola, S. 1998, MNRAS, 300, 292

(ref: Kohler2011) Köhler, R. 2011, A&A, 530, A126

(ref: Kozai1962) Kozai, Y. 1962, AJ, 67, 591

(ref: KratterLodato2016) Kratter, K. & Lodato, G. 2016, ARA&A, 54, 271

(ref: KucukAkkaya2010) Küçük, I. & Akkaya, I. 2010, , 46, 109

(ref: Kurtovic+2018) Kurtovic, N. T., Pérez, L. M., Benisty, M., et al. 2018, ApJL, 869, L44

(ref: Law+2021) Law, C. J., Teague, R., Loomis, R. A., et al. 2021, ApJS, 257, 4

(ref: Law+2023) Law, C. J., Teague, R., Öberg, K. I., et al. 2023, ApJ, 948, 60

(ref: Lidov1962) Lidov, M. L. 1962, , 9, 719

(ref: LodatoFacchini2013) Lodato, G. & Facchini, S. 2013, MNRAS, 433, 2157

(ref: Long+2021) Long, F., Andrews, S. M., Vega, J., et al. 2021, ApJ, 915, 131

(ref: Luhman+2007) Luhman, K. L. 2007, ApJS, 173, 104

(ref: Martin+2022) Martin, R. G., Lepp, S., Lubow, S. H., et al. 2022, ApJL, 927, L26

(ref: MartinLubow2017) Martin, R. G. & Lubow, S. H. 2017, ApJL, 835, L28

(ref: Martin+2014) Martin, R. G., Nixon, C., Lubow, S. H., et al. 2014, ApJL, 792, L33

(ref: Mathis1977) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Menard+2020) Ménard, F., Cuello, N., Ginski, C., et al. 2020, A&A, 639, L1

(ref: Mercimek+2023) Mercimek, S., Podio, L., Codella, C., et al. 2023, MNRAS, 522, 2384

(ref: Miley+2024) Miley, J. M., Carpenter, J., Booth, R., et al. 2024, A&A, 682, A55

(ref: MirandaLai2015) Miranda, R. & Lai, D. 2015, MNRAS, 452, 2396

(ref: Miranda+2017) Miranda, R., Muñoz, D. J., & Lai, D. 2017, MNRAS, 466, 1170

(ref: Monaghan1992) Monaghan, J. J. 1992, ARA&A, 30, 543

(ref: Monnier+2008) Monnier, J. D., Tannirkulam, A., Tuthill, P. G., et al. 2008, ApJL, 681, L97

(ref: Nealon+2020) Nealon, R., Cuello, N., Gonzalez, J.-F., et al. 2020, MNRAS, 499, 3857

(ref: Nixon+2013) Nixon, C., King, A., & Price, D. 2013, MNRAS, 434, 1946

(ref: Nowak+2024) Nowak, M., Rowther, S., Lacour, S., et al. 2024, A&A, 683, A6

(ref: Offner+2022) Offner, S. S. R., Moe, M., Kratter, K. M., et al. 2022, arXiv e-prints, arXiv:2203.10066

(ref: PapaloizouPringle1983) Papaloizou, J. C. B. & Pringle, J. E. 1983, MNRAS, 202, 1181

(ref: PapaloizouTerquem1995) Papaloizou, J. C. B. & Terquem, C. 1995, MNRAS, 274, 987

(ref: Pinilla+2018) Pinilla, P., Tazzari, M., Pascucci, I., et al. 2018, ApJ, 859, 32

(ref: Pinte+2009) Pinte, C., Harries, T. J., Min, M., et al. 2009, A&A, 498, 967

(ref: Pinte+2006) Pinte, C., Ménard, F., Duchêne, G., & Bastien, P. 2006, A&A, 459, 797

(ref: Pinte+2018) Pinte, C., Price, D. J., Ménard, F., et al. 2018, ApJL, 860, L13

(ref: Poblete+2020) Poblete, P. P., Calcino, J., Cuello, N., et al. 2020, MNRAS, 496, 2362

(ref: Poblete+2019) Poblete, P. P., Cuello, N., & Cuadra, J. 2019, MNRAS, 489, 2204

(ref: splash) Price, D. J. 2007, PASA, 24, 159

(ref: Price+2018) Price, D. J., Cuello, N., Pinte, C., et al. 2018a, MNRAS, 477, 1270

(ref: Price+2018-phantom) Price, D. J., Wurster, J., Tricco, T. S., et al. 2018b, PASA, 35, e031

(ref: Rabago+2023) Rabago, I., Zhu, Z., Lubow, S., & Martin, R. G. 2023, arXiv e-prints, arXiv:2310.00459

(ref: Rafikov2002) Rafikov, R. R. 2002, ApJ, 569, 997

(ref: Ragusa+2017) Ragusa, E., Dipierro, G., Lodato, G., Laibe, G., & Price, D. J. 2017, MNRAS, 464, 1449

(ref: Ragusa+2018) Ragusa, E., Rosotti, G., Teyssandier, J., et al. 2018, MNRAS, 474, 4460

(ref: rebound) Rein, H. & Liu, S. F. 2012, A&A, 537, A128

(ref: ias15) Rein, H. & Spiegel, D. S. 2015, MNRAS, 446, 1424

(ref: Reipurth+2014) Reipurth, B., Clarke, C. J., Boss, A. P., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 267–290

(ref: Ribas2015) Ribas, Á., Bouy, H., & Merı́n, B. 2015, A&A, 576, A52

(ref: Ribas+2024) Ribas, Á., Clarke, C. J., & Zagaria, F. 2024, MNRAS, 532, 1752

(ref: Siess+2000) Siess, L., Dufour, E., & Forestini, M. 2000, A&A, 358, 593

(ref: Smallwood+2021) Smallwood, J. L., Nealon, R., Chen, C., et al. 2021, MNRAS, 508, 392

(ref: Smallwood+2023) Smallwood, J. L., Yang, C.-C., Zhu, Z., et al. 2023, MNRAS, 521, 3500

(ref: TanakaWard2004) Tanaka, H. & Ward, W. R. 2004, ApJ, 602, 388

(ref: Terquem+1998) Terquem, C. E. J. M. L. J. 1998, ApJ, 509, 819

(ref: Thomas+2023) Thomas, S. J., Rodgers, B., van der Bliek, N. S., et al. 2023, AJ, 165, 135

(ref: VanAlbada1968) van Albada, T. S. 1968, , 20, 47

(ref: VerrierEvans2009) Verrier, P. E. & Evans, N. W. 2009, MNRAS, 394, 1721

(ref: Vides+2023) Vides, C., Sallum, S., Eisner, J., Skemer, A., & Murray-Clay, R. 2023, arXiv e-prints, arXiv:2310.02241

(ref: vonZeipel1910) von Zeipel, H. 1910, Astronomische Nachrichten, 183, 345

(ref: WeingartnerDraine2001) Weingartner, J. C. & Draine, B. T. 2001, ApJ, 563, 842

(ref: Wolfer+2023) Wölfer, L., Facchini, S., van der Marel, N., et al. 2023, A&A, 670, A154

(ref: Young+2023) Young, A. K., Stevenson, S., Nixon, C. J., & Rice, K. 2023, MNRAS, 525, 2616

# Data combination

The data on which this paper is based come from a combination of data from two observational programs. A first dataset (OLD) has been acquired in the context of the ALMA programm $2013.1.00498.S$ in 2013, and analysed in details in . A second one has been acquired in end-2021 with longer baselines (LB) being covered during the ALMA programm $2021.1.01137.S$. A third dataset has been acquired mid-2022 in the context of the same ALMA programm and covering shorter baselines (SB).

The data reduction and calibration are described in Section [2.1](#subsec : data) and we add details about the self-calibration process of the data in the following. The three raw datasets were downloaded from the ALMA archive and calibrated using the available calibration scripts. At first, we reduced and self-calibrated each dataset independently. The line channels were flagged and the SPW averaged together to create continuum MS. Using the *gaincal* and *applycal*, self-calibration rounds in phase were conducted on the continuum data. The first calibration tables were created for combined SPWs, combined polarisation and a infinite solution interval to maximise the S/N. In the following rounds, the SPWs, polarisations were progressively decombined and the solution interval progressively turned down to the integration time. Between each rounds, the RMS was measured on images produced with *tclean*.

We ensured that the RMS was decreasing between the rounds without any decrease of the total flux and peak intensity.

Second, we created a common model for the three resulting continuum datasets using the *tclean* task. Before doing so, the observations were centred together with the *phaseshift* task using the centre of the cavity as a common reference. The different MS were also rescaled to a common flux reference using the DSHARP utilities [^3]. From this model, additional self-calibration rounds in phase were performed on the individual MS. It ensured that the three datasets were properly centred together. The calibration were stopped before the RMS stopped decreasing between the rounds. The *gaincal* parameters were turned down to a solution interval of two times the integration time, combined SPWs and independent polarisations. The final continuum image was created using *tclean* from the three resulting MS of the previous process.

Third, $^{12}$CO channels were separated from the original MS. The continuum level was subtracted from each MS using the task *uvcontsub*. The resulting gas MS were scaled to a common flux reference using the same correction factors that the continuum MS. The calibration tables of the previous self-calibration rounds were applied to the corresponding gas MS. Finally, the $^{12}$CO datacube was created using the *tclean* task, that ensures a spectral smoothing of the MS to a common spectral resolution of $0.5$ km s$^{-1}$.

Figure [16](#fig:reduc_comp) shows how the combination of the datasets affects the final continuum image and $^{12}$CO moment 0 images. The combination of the dataset used in  with our newer data enhances the final S/N compared to our data (SB +LB) alone. This S/N increase allows the continuum to be imaged with a more robust parameter controlling the Briggs weighting when applying the *tclean* task, and thus for more angular resolution than in previous studies.

![image](Figures/Comb_vs_JM_cont.pdf) ![image](Figures/Comb_vs_JM_gas.pdf)

# Channel maps

 

![](Figures/channel_maps_obs.pdf)

# Gas emission fitting with Discminer

## Initial conditions and results

The initial values of the MCMC sampling were chosen in agreement with the values derived in when possible, namely for the orientation and kinematic parameters. The initial values of the parameters defining the emission surfaces were set to initialise a thin disc, in agreement with the observations. The rest of the initial values were put in the middle of the prior range or at typical values. The reference radius $r_0$ was taken as $100$ au. Priors were defined to limit the sampling of the parameter space and the computational cost. The range of priors for all the parameters was set to a limit the disc to a reasonable extent. Following the need of a precise model, we initialised $256$ walkers with a total of $40000$ steps. The chains reached convergence well before the end of the sampling and the resulting auto-correlation length was $106$ steps. The first $6300$ steps are considered as a burn-in phase where the walkers explore the parameter space. After that, the walkers reached convergence and remained concentrated around the final value. The best-fit parameters are taken as the median of the posterior distributions. The errorbars are the $16$ and $84$ percentiles of the posterior distributions. Table [5](#table:discminer_fit) summarises the results of the fit.

| Parameter | Search range | Best-fit |
|:--:|:--:|:--:|
| $i$ | $[20;80]^\circ$ | $54.7 ^{+0.07\circ}_{-0.40}$ |
| $PA$ | $[20;80]^\circ$ | $53.6 ^{+0.07\circ}_{-0.11}$ |
| $x_c$ | $[-50;50]$ au | $4.26 \pm ^{+0.16}_{-0.82}$ au |
| $y_c$ | $[-50;50]$ au | $0.52 \pm ^{+0.22}_{-0.17}$ au |
|  |  |  |
| $M_{*}$ | $[5;7]$ M$_{\odot}$ | $5.99 ^{+0.03}_{-0.01}$ M$_{\odot}$ |
| $v_{sys}$ | $[7;9]$ km s$^{-1}$ | $7.86 ^{+0.01}_{-0.01}$ km s$^{-1}$ |
|  |  |  |
| $z_{0,low}$ | $[0;30]$ au | $13.7 ^{+0.55}_{-1.34}$ au |
| $p_{low}$ | $[0;3]$ | $1.35 ^{+0.02}_{-0.06}$ |
| $q_{low}$ | $[0;3]$ | $1.31 ^{+0.02}_{-0.07}$ |
| $R_{b,low}$ | $[100;400]$ au | $217 ^{+2}_{-2}$ au |
|  |  |  |
| $z_{0,up}$ | $[0;30]$ au | $14.7 ^{+0.59}_{-1.34}$ au |
| $p_{up}$ | $[0;3]$ | $1.21 ^{+0.01}_{-0.03}$ |
| $q_{up}$ | $[0;3]$ | $0.97 ^{+0.01}_{-0.02}$ |
| $R_{b,up}$ | $[100;400]$ au | $221 ^{+4}_{-4}$ au |
|  |  |  |
| $I_{0}$ | $[0;1000]$ Jy pixel$^{-1}$ | $3.80 ^{+0.52}_{-0.28}$ Jy pixel$^{-1}$ |
| $p_{I}$ | $[-10;10]$ | $-2.10 ^{+0.05}_{-0.03}$ |
| $q_{I}$ | $[0;5]$ | $2.16 ^{+0.02}_{-0.02}$ |
| $R_{out}$ | $[150;400]$ au | $223 ^{+4}_{-1}$ au |
|  |  |  |
| $L_{w,0}$ | $[0.005;5]$ km s$^{-1}$ | $0.19 ^{+0.01}_{-0.01}$ km s$^{-1}$ |
| $p_{L_w}$ | $[-5;5]$ | $-0.41 ^{+0.05}_{-0.03}$ |
| $q_{L_w}$ | $[-5;5]$ | $-0.53 ^{+0.03}_{-0.03}$ |
|  |  |  |
| $L_{s,0}$ | $[0.005;20]$ | $1.26 ^{+0.03}_{-0.02}$ |
| $p_{L_s}$ | $[-5;5]$ | $-0.01 ^{+0.04}_{-0.02}$ |
| $q_{L_s}$ | $0.00$ | Not fitted |

: Parameters of the best-fit model found by Discminer to the $^{12}$CO (2-1) emission.

Table notes: The reference radius is taken as $r_0=100$ au and the pixel scale is $0.01\ensuremath{''}$.

![](Figures/channel_maps_model.pdf)

## Rotation curve

Discminer allows velocity radial profiles from the results of the fitting procedure to be computed. The rotation curve of the data can be compared to the best-fit model velocity profile. From the resulting residuals and and their projection in the skyplane, the velocity deviation to a Keplerian profile $\Delta v_{\phi}$, the velocity of radial flows $v_r$ and the velocity of vertical flows $v_z$ can all be computed as a function of radius. In Figure [19](#fig:discminer_rotation_curve), we show these quantities from our best-fit model to the $^{12}$CO (2-1) emission of V892 Tau. The disc is dominated by Keplerian rotation, although slight offsets can be observed in the innermost and outermost parts of the disc. In the inner parts, this mainly translates into a rise of $v_r$, potentially triggered by interactions with the inner binary. The outer disc is characterised by inward radial flows, vertical motions of the gas and slight deviations from the keplerian rotation speed. These patterns are consistent with interactions with V892 Tau NE and support the hypothesis of a bound triple system.

![image](Figures/rot_curve_discminer.pdf) ![image](Figures/res_v_discminer.pdf)

# Manual rotation of the disc before post-processing

+-----------------------------------------------------------------------------------------+
| Inclination \[$\deg$\]                                                                  |
+:============:+:============:+:============:+:============:+:============:+:============:+
| Observations | *ref*        | *e05*        | *i30*        | *i60*        | *ei60*       |
+--------------+--------------+--------------+--------------+--------------+--------------+
| $54.6\pm1.3$ | $54.6\pm0.4$ | $54.6\pm0.3$ | $52.6\pm0.3$ | $47.2\pm0.5$ | $50.8\pm0.8$ |
+--------------+--------------+--------------+--------------+--------------+--------------+
|              |              |              |              |              |              |
+--------------+--------------+--------------+--------------+--------------+--------------+
| Position Angle \[$\deg$\]                                                               |
+--------------+--------------+--------------+--------------+--------------+--------------+
| Observations | *ref*        | *e05*        | *i30*        | *i60*        | *ei60*       |
+--------------+--------------+--------------+--------------+--------------+--------------+
| $53.0\pm0.7$ | $52.7\pm1.0$ | $53.1\pm0.6$ | $43.4\pm0.3$ | $30.2\pm0.9$ | $34.2\pm1.5$ |
+--------------+--------------+--------------+--------------+--------------+--------------+

Table notes: Each simulated disc was manually moved back to the inclination and PA of the observed disc before post-processing into synthetic observations.

Discs in multiple systems are expected to precess due to the gravitational torques applied by misaligned stars (cite: PapaloizouTerquem1995). We observe that precession in our hydrodynamical models of the disc of V892 Tau : the disc is initialised at its observed inclination and position angle (PA), but these values evolve during the simulation because of the gravitational perturbations induced by the inner binary and the external companion. Values of inclination and PA of the disc at the end of each simulation can be found in Table [\[table:disc_rotation\]](#table:disc_rotation) (see Fig [8](#fig:simgrid_rho) for a visual representation). However, for a proper comparison with the observations, the simulated discs should have the same orientation as the observed disc. But, it would be too computationally expensive to simulate the disc during a whole precession timescale, at the end of which the disc would have come back to its original PA while the inclination would have slightly changed. We tackle this issue by manually rotating the simulated discs back to their observed values of inclination and PA before going into their post-processing into synthetic observations. This assumes that the disc properties other than inclination and PA, and the interactions with the stars are independent of the disc orientation. We are aware of the discrepancy between the observed orientation of the disc and the orientation at the end of the simulations. But, we argue that this discrepancy is reasonably small, which allows us to work in the context of the previous hypothesis. This way, rotating the disc to the observed orientation will allow for an adequate comparison of the observations and the synthetic data.

# Inclination sign of the disc

![image](Figures/res_Lw.pdf)

Usually, it is straightforward to determine the closest side of a disc when its upper and lower emission surfaces are both detected (e.g. IM Lup, (cite: Pinte+2018)). Here and in previous studies of the system, the lower surface of the V892 Tau disc is not clearly detected, making the sign of the inclination uncertain. According to the fitted linewidths maps of the disc displayed on Figure [6](#fig:obs_model_panel) last row, the Keplerian model is able to reproduce the data well. Nonetheless, the linewidths seems larger in the NW side of the disc than in the SE side. When compared to the model, the NW side shows an excess in linewidth (see residual map on Figure [6](#fig:obs_model_panel) last row right panel). Lines are expected to be seen broader in the closest side of the disc to the observer due to the greater contribution of the lower emission surface (e.g. MWC480, (cite: DiscminerII)). Applied to V892 Tau, this could indicate that the NW side of the disc is the closest side to the observer and that the disc inclination is negative. Trying to confirm that result, we ran an MCMC sampling to fit the disc observations with a model with a negative inclination sign with the same method as described in Sections [3.1](#subsec:discminer) and [9](#app : Discminer). In that model, the closest side to the observer is the NW side of the disc. The resulting fitted values were similar to the original model apart from the inclination sign. It lead to a disc model quite identical to the original one in the outer disc, as showed by the linewidth map of each model on Figure [20](#fig:lw_res) below. This could be explained by the disc being significantly flat and its lower emission surface not being detected, which doesn’t allow to conclude on the true orientation of the disc. Differences still can be seen between the two models in the central parts of the disc, for which our data are not reliable due to cloud absorption.

In general, the far side of the disc is observed with a larger brightness temperature than the near side (cite: Law+2023), which is in line with our synthetic observations resulting from the simulations where the closest side to the observer is assumed to be the SE side. According to our $^{12}$CO observations, the NW side is brighter in average than the SE side by approximately 13$\%$. This agreement between the simulations and the observations is in favour of the SE side being the nearside of the CBD. Moreover, the temperature asymmetry plotted on Figure [7](#fig:sketch_obs) and heading toward the NW cloud also trace the flared far side of the disc, since similar patterns have already been observed in discs with a known orientation (see RXJ 1615 in (cite: Wolfer+2023), LkCa 15 and HD 34282 in (cite: Law+2023)). Considering the azimuthal asymmetry in the continuum disc arises from warm dust emission, this emission may come from the visible inner rim of the disc far side (cite: Ribas+2024). Such a scenario would indicate that the disc near side is the SE side of the disc.

The disc thickness and faint lower surface make the conclusion on the disc true inclination difficult. Nonetheless, we present the previous results as tentative evidences for the SE side of the disc being the closest side to the observer. Future scattered light observations or high resolution polarisation maps could help to characterise the dust scattering properties which would bring additional constrains on the disc true orientation.

# Binary-only simulations

We performed additional hydrodynamical SPH simulations of the V892 Tau system. In these simulations, we model the system as a binary system with a disc. The disc parameters are the same as described in Section [3.2](#subsec:hydro_sim). Then, we consider different setups where the companion star is ignored, or where the inner binary is merged into a single star with an equivalent mass. These setups are :

- the inner binary surrounded by the disc (*IB*).

- the outer binary initially misaligned of $30\degree$ with respect to the disc (*OB30*).

- the outer binary initially misaligned of $60\degree$ with respect to the disc (*OB60*).

The orbital parameters of the binary star in *IB* are the same as the orbital parameters of the inner binary in the triple system simulations. The orbital parameters of the binary star in *OB30* are the same as the orbital parameters of the outer binary in *i30*. The orbital parameters of the binary star in *OB60* are the same as the orbital parameters of the outer binary in *i60*. These simulations counted $10^6$ SPH particles and ran for a total time of $t=25$ P$_{out}$, where P$_{out}$ is the outer binary period in the triple system simulations.

The oscillations of the modelled CBD are triggered both by the inner binary and the outer binary. Yet, the contribution of each component to the dynamics of the disc is unclear : the simulated CBD is found in an intermediate plane between the inner and outer binary orbital planes, its global inclination oscillates without reaching a coplanar nor polar configuration and it precesses non-linearly. Simulations of the V892 Tau system modelled as a binary star could help to disentangle the dynamical effects of the inner and of the outer binaries on the disc.

Figure [21](#fig:SPH_comp_binaries) shows the inclination $i$ and the PA $\Omega$ of the disc as a function of time in the simulations *i30*, *i60*, *OB30*, *OB60*, and *IB*.

In the inner binary only simulation, the CBD remains coplanar with the inner binary and its PA remains at the initialised value. The PA of the disc follows a decreasing trend in all the other simulations. During the very first orbits, the disc has the same linear precession rate in the setups *i30* and *OB30*, and *i60* and *OB60* respectively. Then, the PA of the disc starts to oscillates in the triple system simulations, while the precession stays linear in the outer binary systems *OB30* and *OB60*. The precession slope in those setups is steeper than the average slope in the triple setups, but asymptotically reproduces the precession rate of the disc in triple systems during the first orbits of the companion. The precession rate is similar in the *OB30* and the *OB60* setups. We expect that kind of linear precession for binary systems (e.g. (cite: PapaloizouTerquem1995)). From dynamical considerations, we expect the precession rate of the disc to be $t_{prec, 0}= 144$ P$_{out}$ in the setup *OB30* and $t_{prec, 0}= 251$ P$_{out}$ in *OB60* (cite: Terquem+1998; Bate+2000). We measure a precession rate of $t_{prec}= 189\pm1$ P$_{out}$ and $t_{prec}= 195\pm1$ P$_{out}$ respectively, which is in rough agreement with that prediction.

We already saw that the disc inclination follows damped oscillations in the triple system setups *i30* and *i60*. In the *OB30* setup, the inclination of the disc drops with time, but that drops is not linear nonetheless. The *OB30* disc could then align with the orbital plane of the binary, but the simulation stopped too early to clarify this statement. In the *OB60* model, the inclination of the disc rises steadily in a linear way with a slope of $5.6\times10^{-2}\pm 0.2\times10^{-2}$ P$_{out}$. That particular behaviour could be explained by the disc starting to align with the binary orbital plane. The timescale of this alignment is larger that in the *OB30* case due to the higher mutual inclination of the disc to the orbital plane, which results in a smaller torque applied by the companion on the disc (cite: Bate+2000).

The three additional simulations *IB*, *OB30* and *OB60* show that the dynamical behaviour of the V892 Tau disc can not be reproduced by a binary system only. The triplicity of the system, which means both the inner binary and outer binary, is responsible for the inclination oscillations and the peculiar precession of the CBD.

![image](Figures/incl_bin_30.pdf) ![image](Figures/O_bin_30.pdf) ![image](Figures/incl_bin_60.pdf) ![image](Figures/O_bin_60.pdf)

# Other N-Body simulations

![image](Figures/nbody_ref_a.pdf) ![image](Figures/nbody_ref_e.pdf) ![image](Figures/nbody_ref_i.pdf)

![image](Figures/nbody_e05_a.pdf) ![image](Figures/nbody_e05_e.pdf) ![image](Figures/nbody_e05_i.pdf)

![image](Figures/nbody_i30_a.pdf) ![image](Figures/nbody_i30_e.pdf) ![image](Figures/nbody_i30_i.pdf)

![image](Figures/nbody_i60_a.pdf) ![image](Figures/nbody_i60_e.pdf) ![image](Figures/nbody_i60_i.pdf)

[^1]: Outputs of the hydrodynamical simulations underlying this article are available at <https://zenodo.org/records/11350568>

[^2]: <https://almascience.eso.org/almadata/lp/DSHARP/>

[^3]: <https://almascience.eso.org/almadata/lp/DSHARP/>

</paper>

Write the methods card for this paper.