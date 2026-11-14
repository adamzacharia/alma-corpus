# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...685A..18L\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...685A..18L",
 "title": "Forming localized dust concentrations in a dust ring: DM Tau case study. The asymmetric 7 mm dust continuum of the DM Tau disk",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Liu, Hauyu Baobab",
 "n_authors": 11,
 "arxiv_id": "2402.02900",
 "doi": "10.1051/0004-6361/202348896",
 "alma_projects_linked_by_archive": [
  "2013.1.00498.S",
  "2013.1.00647.S",
  "2015.1.00296.S",
  "2016.1.00565.S",
  "2016.1.01042.S",
  "2017.1.01460.S",
  "2018.1.01755.S"
 ]
}
```

Paper text:
<paper>
# Forming localized dust concentrations in a dust ring: DM Tau case study

Previous high-angular-resolution 225 GHz ($\sim$1.3 mm) continuum observations of the transitional disk DM Tau have resolved an outer ring at 20-120 au radii that is weakly azimuthally asymmetric.

We aim to examine dust growth and filtration in the outer ring of DM Tau.

We performed $\sim$0.06$''$ ($\sim$8.7 au) resolution Karl G. Jansky Very Large Array (JVLA) 40–48 GHz ($\sim 7$ mm; Q band) continuum observations, along with complementary observations at lower frequencies. In addition, we analyzed the archival JVLA observations undertaken since 2010.

Intriguingly, the Q band image resolved the azimuthally highly asymmetric, knotty dust emission sources close to the inner edge of the outer ring. Fitting the 8-700 GHz spectral energy distribution (SED) with two dust components indicates that the maximum grain size ($a_{\mbox{\scriptsize max}}$) in these knotty dust emission sources is likely $\gtrsim$300 $\mu$m, whereas it is $\lesssim$50 $\mu$m in the rest of the ring. These results may be explained by a trapping of inwardly migrating "grown" dust close to the ring inner edge. The exact mechanism for developing the azimuthal asymmetry has not yet been identified, which may be due to planet-disk interaction that might also be responsible for the creation of the dust cavity and pressure bump. Otherwise, it may be due to the fluid instabilities and vortex formation as a result of shear motions. Finally, we remark that the asymmetries in DM Tau are difficult to diagnose from the $\gtrsim$225 GHz observations, owing to a high optical depth at the ring. In other words, the apparent symmetric or asymmetric morphology of the transitional disks may be related to the optical depths of those disks at the observing frequency.

# Introduction

The rich structures in protoplanetary disks resolved in recent (sub)millimeter interferometric and near infrared imaging observations have sparked a surge in theoretical follow-up studies (for a review, see (cite: Andrews2020ARA&A..58..483A)). In particular, intense discussions on the origin and subsequent evolution of the concentric gaps and rings seen in a large number of protoplanetary disks has been ongoing (e.g., (cite: Andrews2011ApJ...732...42A; Hashimoto2012ApJ...758L..19H; ALMA2015ApJ...808L...3A; Andrews_2018)). These structures may have been created as a result of ice lines (e.g., (cite: Zhang2015ApJ...806L...7Z; Okuzumi2016ApJ...821...82O)), planet-disk interaction ((cite: Zhang2015ApJ...806L...7Z; Okuzumi2016ApJ...821...82O)), secular gravitational instability (e.g., (cite: Takahashi2014ApJ...794...55T)), or other mechanisms.

|                                 |                                        |
|:--------------------------------|:---------------------------------------|
| ![image](dmtau_ALMA_smooth.pdf) | ![image](dmtau_JVLA_alltaper_rob2.pdf) |

DM Tau is a 0.53 M$_{\odot}$ star ($d\sim$145 pc; (cite: Gaia_2023)) with an effective temperature of 3705 K ((cite: Kudo2018ApJ...868L...5K)). Analyses of its near infrared spectral energy distribution (NIR SED) have indicated that DM Tau hosts a transitional disk that have a large inner cavity ((cite: Bergin2004ApJ...614L.133B; Calvet2005ApJ...630L.185C)). The 8–12 GHz and 12–18 GHz images ((cite: Terada2023ApJ...953..147T)) as well as the 8–10 GHz non-detection ((cite: Zapata2017ApJ...834..138Z)) have indicated that there are time varying free-free emission sources (e.g., ionized disk) within the dust cavity. The (sub)millimeter interferometric imaging observations of dust continuum emission using the Submillimeter Array (SMA) and the Atacama Large Millimeter/submillimeter Array (ALMA) have resolved the radially extended outer dusty ring at $\sim$20–120 au radii ((cite: Andrews2011ApJ...732...42A; Kudo2018ApJ...868L...5K)). The ALMA $\sim$225 GHz observations additionally resolved an inner ring at $\sim$4 au radii, which appears to be azimuthally asymmetric (cite: Kudo2018ApJ...868L...5K). The higher angular resolution ALMA $\sim$225 GHz continuum image further reveals a weak azimuthal asymmetry in the outer ring ((cite: Hashimoto2021ApJ...911....5H)). The dust mass and dust growth in the outer ring, which are tightly related to the formation of comets and ice giants, have not yet been constrained by optically thin observations.

In this work, we present the high-resolution National Radio Astronomy Observatory (NRAO) Karl G. Jansky Very Large Array (JVLA) observations of DM Tau, which is advantageous for probing $\gtrsim$1 mm sized dust. Besides examining the JVLA images, we based our study on fittings of the 8–700 GHz SED measured by JVLA, SMA, and ALMA to quantitatively constrain the dust column densities ($\Sigma_{\mbox{\scriptsize dust}}$) and dust maximum grain sizes ($a_{\mbox{\scriptsize max}}$). We introduce the data we utilized and the data calibration procedures in Section [2](#sec:observations). The results are presented in Section [3](#sec:results). In Section [4](#sec:discussion), we discuss the origin of the emission using SED models, and address the potential physical implication. A brief conclusion is given in Section [5](#sec:conc). Appendix [6](#appendix:image) provides a comparison of the JVLA 40–48 GHz images ($\sim$7 mm) carried out via a range of approaches. Appendix [7](#appendix:asym) details a model-independent approach to diagnose azimuthal asymmetry. We assess the degree of free-free contamination in the JVLA 40–48 GHz images in Appendix [8](#appendix:freefree). Appendix [9](#appendix:mcmc) provides the details of how we modeled the observed SED using the Markov chain Monte Carlo (MCMC) method.

# Data and reduction

## Data

We carried out the JVLA observations towards DM Tau at Q (40–48 GHz), Ku (12–18 GHz), and X (8–12 GHz) bands in 2019. The Ku and X bands observations which mainly traced free-free emission have been reported elsewhere (cite: Terada2023ApJ...953..147T). In addition, we retrieved and analyzed the archival JVLA data which were taken since August 22, 2010. Most of those data were taken from the Disk@EVLA project (project code: AC982; PI: C. Chandler), while some centimeter band data were taken from the Gould’s Belt Very Large Array Survey project (project code: BL175, PI: L. R. Loinard; (cite: Dzib2015ApJ...801...91D)) and project 13B-364 (PI: L. F. Rodriguez; (cite: Zapata2017ApJ...834..138Z)). These JVLA observations took full RR, RL, LR, and LL correlator products. Table [\[tab:obs\]](#tab:obs) summarizes the observational details and our data quality assessment.

We performed a $\sim$3$''$ angular resolution SMA 200–400 GHz survey towards 47 Class II objects in the Taurus-Auriga region in 2021 that included DM Tau as one of the target sources. The full survey will be reported in an upcoming paper (Chung et al. submitted). The present work utilizes the 200–400 GHz SED provided by this SMA survey, which was carefully calibrated.

We retrieved the archival ALMA Band 3 ($\sim$95–111 GHz), Band 4 ($\sim$144–159 GHz), and Band 9 ($\sim$659–676 GHz) observations that the maximum recoverable angular scales (MAS) are larger than 3$''$ for the purpose of deriving the (sub)millimeter SEDs. We visually inspected the spectra and only utilized the passbands that detected DM Tau and did not present significant spectral line emission. Table [\[tab:ALMAarchive\]](#tab:ALMAarchive) summarizes the ALMA measurements we included.

|                            |
|:--------------------------:|
| ![image](asym_m0_real.pdf) |
|   ![image](asym_m1.pdf)    |

Finally, to reference the locations of spatially resolved features in the JVLA observations, we utilized the high-angular-resolution ALMA 216–233 GHz images towards DM Tau, which were detailed in (cite: Kudo2018ApJ...868L...5K) (c.f. (cite: Hashimoto2021ApJ...911....5H)). Before comparing the ALMA and JVLA images, we corrected for the proper motions (R.A.: 11.788 mas yr$^{-1}$ and Decl.: $-$18.361 mas yr$^{-1}$) quoted from the Gaia Data Release 3 (cite: Gaia_2023), using the `fixplanets` task of the Common Astronomy Software Applications (CASA; (cite: McMullin2007ASPC..376..127M)) software package.

## JVLA data processing

We manually calibrated the JVLA data following the standard strategy (see details below) using the CASA software package. For all the JVLA observations we utilized, after implementing the antenna position corrections, weather information, gain-elevation curve, and opacity model, we bootstrapped delay fitting and passband calibrations, and then performed a complex gain calibration. We applied the absolute flux reference to our complex gain solutions and then applied all the derived solution tables to the target source.

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Epoch | Time | Band | Array config. | On-source time | Beam size | RMS noise | Peak intensity | Flux density | Flux calib. | Gain calib. | BP calib. |
|  | (UTC) | Freq. (GHz) | *uv*-dis. (m) | (min) |  | ($\mu$Jy/beam) | (mJy/beam) | (mJy) |  | Flux (Jy) | Flux (Jy) |
| A-1$^{a}$ | 2011 07 26 | C | A | 24 | 0.56$''$$\times$0.34$''$ | 8.0 | $\cdots$ | $\cdots$ | 3C138 | J0431$+$2037 | J0319$+$4130 |
|  | 09:55:29–13:54:48 | 4.3–7.8 | 793–36584 |  | (PA: -54$^\circ$) |  |  |  |  | 2.36$\pm$0.003 | 20.6$\pm$0.06 |
| A-2$^{b}$ | 2019 09 28 | Q | A | 35 | 0.054$''$$\times$0.044$''$ | 23 | $\cdots$ | $\cdots$ | 3C138 | J0431+1731 | J0319+4130 |
|  | 12:30:50–13:40:54 | 40.0–47.8 | 692–34720 |  | (PA: -3$^\circ$) |  |  |  |  | 0.196$\pm$0.0007 | 19.9$\pm$0.076 |
| A-3$^{b}$ | 2019 10 06 | Q | A | 35 | 0.046$''$$\times$0.041$''$ | 24 | $\cdots$ | $\cdots$ | 3C138 | J0431+1731 | J0319+4130 |
|  | 11:02:14–12:12:14 | 40.0–47.8 | 1678–36475 |  | (PA: -10$^\circ$) |  |  |  |  | 0.186$\pm$0.0005 | 19.0$\pm$0.054 |
| A-4$^{b}$ | 2019 10 14 | Q | A | 35 | 0.052$''$$\times$0.049$''$ | 23 | $\cdots$ | $\cdots$ | 3C138 | J0431+1731 | J0319+4130 |
|  | 10:13:50–11:23:50 | 40.0–47.8 | 742–36617 |  | (PA: 60$^\circ$) |  |  |  |  | 0.191$\pm$0.0004 | 18.8$\pm$0.038 |
| B-1$^{a}$ | 2011 02 25 | C | B | 3.5 | 1.1$''$$\times$1.1$''$ | 17 | $\cdots$ | $\cdots$ | 3C147 | J0449+1121 | 3C147 |
|  | 01:52:16–03:51:46 | 4.1–7.9 | 121–11124 |  | (PA: 20$^\circ$) |  |  |  |  | 1.23$\pm$0.001 | — |
| B-2$^{a}$ | 2011 04 17–18 | C | B | 3.5 | 1.1$''$$\times$1.0$''$ | 25 | $\cdots$ | $\cdots$ | 3C147 | J0449+1121 | 3C147 |
|  | 22:27:40–00:27:22 | 4.1–7.9 | 121–11124 |  | (PA: 7$^\circ$) |  |  |  |  | 1.02$\pm$0.002 | — |
| B-3$^{a}$ | 2011 05 14–15 | C | BnA | 3.5 | 1.5$''$$\times$0.48$''$ | 21 | $\cdots$ | $\cdots$ | 3C147 | J0449+1121 | 3C147 |
|  | 23:11:10–01:10:48 | 4.1–7.9 | 121–22816 |  | (PA: 62$^\circ$) |  |  |  |  | 0.95$\pm$0.002 | — |
| B-4 | 2012 08 12 | Q | B | 83 | 0.28$''$$\times$0.17$''$ | 26 | 0.19 | 0.56 | J0542$+$4951 | J0431$+$1731 | J0319$+$4130 |
|  | 08:45:42–11:44:48 | 41.0–43.0 | 109–11124 |  | (PA: -59$^\circ$) |  |  |  |  | 0.224$\pm$0.0004 | 22.2$\pm$0.02 |
| B-5 | 2012 08 29 | Q | B | 81 | 0.28$''$$\times$0.16$''$ | 24 | 0.18 | 0.57 | J0542$+$4951 | J0431$+$1731 | J0319$+$4130 |
|  | 08:08:54–11:07:54 | 41.0–43.0 | 109–11124 |  | (PA: -51$^\circ$) |  |  |  |  | 0.228$\pm$0.0002 | 21.5$\pm$0.02 |
| B-6 | 2012 09 04 | Q | B | 83 | 0.22$''$$\times$0.17$''$ | 26 | 0.17 | 0.59 | J0542$+$4951 | J0431$+$1731 | J0319$+$4130 |
|  | 08:46:47–11:44:12 | 41.0–43.0 | 121–11124 |  | (PA: -30$^\circ$) |  |  |  |  | 0.223$\pm$0.0002 | 23.3$\pm$0.06 |
| B-7 | 2012 09 15 | Q | BnA | 83 | 0.20$''$$\times$0.12$''$ | 25 | 0.14 | 0.70 | J0542$+$4951 | J0431$+$1731 | J0319$+$4130 |
|  | 07:31:51–10:30:57 | 41.0–43.0 | 256–22816 |  | (PA: -65$^\circ$) |  |  |  |  | 0.249$\pm$0.0005 | 23.9$\pm$0.05 |
| B-8$^{a}$ | 2013 10 29 | X | B | 19 | 0.97$''$$\times$0.82$''$ | 5.9 | $\cdots$ | $\cdots$ | J0137$+$3309 | J0409$+$1217 | J0137$+$3309 |
|  | 05:39:43–07:09:22 | 8.0–10.0 | 121–11124 |  | (PA: -62$^\circ$) |  |  |  |  | 0.343$\pm$0.0002 | $\cdots$ |
| C-1 | 2010 12 13 | Q | C | 126 | 0.80$''$$\times$0.60$''$ | 19 | 0.40 | 0.59 | J0542$+$4951 | J0431$+$1731 | J0319$+$4130 |
|  | 01:14:16–05:13:21 | 41.0–43.0 | 43–3387 |  | (PA: -53$^\circ$) |  |  |  |  | 0.361$\pm$0.0005 | 15.8$\pm$0.04 |
| D-1$^{a}$ | Aug. 24, 2010 | K | D | 9.5 | 4.5$''$$\times$3.4$''$ | 53 | $\cdots$ | $\cdots$ | J0542$+$4951 | J0431$+$2037 | J0319$+$4130 |
|  | 08:30:25–12:59:41 | 20.0–22.0 | 23–1031 |  | (PA: -61$^\circ$) |  |  |  |  | 0.754$\pm$0.0005 | 21.1$\pm$0.02 |
| D-2 | 2010 08 30 | Q | D | 9.0 | 1.9$''$$\times$1.7$''$ | 134 | 0.81 | 0.86 | J0542$+$4951 | J0431$+$2037 | J0319$+$4130 |
|  | 10:06:36–14:05:51 | 41.0–43.0 | 40–1031 |  | (PA: 83$^\circ$) |  |  |  |  | 0.434$\pm$0.0008 | 17.4$\pm$0.02 |
| D-3 | 2010 09 11 | K | D | 17 | 4.2$''$$\times$3.5$''$ | 11 | 0.14 | 0.13 | J0542$+$4951 | J0431$+$2037 | J0319$+$4130 |
|  | 08:20:06–12:18:50 | 20.0–22.0 | 22–1031 |  | (PA: -51$^\circ$) |  |  |  |  | 0.743$\pm$0.0003 | 21.2$\pm$0.01 |
| D-4 | 2010 09 12 | Ka | D | 13 | 2.9$''$$\times$2.1$''$ | 34 | 0.44 | 0.53 | J0542$+$4951 | J0431$+$2037 | J0319$+$4130 |
|  | 09:15:23–11:42:34 | 31.7–33.7 | 23–1031 |  | (PA: -3$^\circ$) |  |  |  |  | 0.631$\pm$0.0020 | 23.0$\pm$0.04 |

Table notes:

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Band | UTC date | Frequency | Angular resolution | MAS | $F_{\nu}$ | Project |  |
|  | (YYYY MM DD) | (GHz) | ($''$) | ($''$) | (mJy) |  |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) |  |
| 3 | 2014 08 15 | 95.70–97.69 | 0.65 | 12 | 9.9$\pm$0.3 | 2013.1.00647.S (PI: Gorti, Uma) |  |
|  |  | 97.51–99.49 |  |  | 10.5$\pm$0.3 |  |  |
|  |  | 109.01–110.90 |  |  | 14.6$\pm$0.5 |  |  |
| 3 | 2016 11 05 | 94.51–96.49 | 0.66 | 6.8 | 10.5$\pm$0.4 | 2016.1.01042.S (PI: Chandler, Claire) |  |
|  |  | 96.41–98.39 |  |  | 11.2$\pm$0.4 |  |  |
|  |  | 106.51–108.49 |  |  | 14.6$\pm$0.7 |  |  |
|  |  | 108.46–110.33 |  |  | 15.1$\pm$0.7 |  |  |
| 4 | 2016 07 25 | 144.02–146.01 | 0.45 | 5.0 | 29.7$\pm$1.5 | 2015.1.00296.S (PI: Semenov, Dmitry) |  |
|  |  | 145.92–145.98 |  |  | 27.8$\pm$1.8 |  |  |
|  |  | 146.58–146.64 |  |  | 29.7$\pm$2.0 |  |  |
|  |  | 156.96–157.01 |  |  | 34.5$\pm$2.3 |  |  |
|  |  | 158.17–158.23 |  |  | 37.4$\pm$2.7 |  |  |
|  |  | 158.95–159.00 |  |  | 36.5$\pm$2.3 |  |  |
| 9 | 2018 08 16 | 658.15–659.09 | 0.30 | 3.1 | 366$\pm$55 | 2016.1.00565.S (PI: Schwarz, Kamber) |  |
|  |  | 660.67–661.60 |  |  | 371$\pm$56 |  |  |
|  |  | 674.68–676.67 |  |  | 387$\pm$58 |  |  |
|  |  | 674.68–676.67 |  |  | 384$\pm$58 |  |  |

For the Q band (40–48 GHz) observations taken in 2019 (Table [\[tab:obs\]](#tab:obs)), we additionally used the observations on 3C138 to calibrate the cross-hand delay and absolute polarization position angle and we used the observations on J0319+4130 (3C84) to calibrate the polarization leakage (i.e., D-terms). In spite of the fact that 3C84 was shown to be weakly polarized in the Q band, previous studies have demonstrated that the D-term solutions derived from it can still help in suppressing polarization leakage. These solutions can also yield polarization images that are reasonably consistent with those that were calibrated by the more ideal D-term calibrators for the JVLA Q band observations (e.g., 0713+4349; (cite: Liu2016ApJ...821...41L; Ko2020ApJ...889..172K)). We did not detect significant Stokes Q, U, and V intensities at Q band and we omit them from any further discussion.

We performed multi-frequency synthesis (nterms$=$2) imaging ((cite: Rau2011A&A...532A..71R)) using the CASA `tclean` task. For individual epochs of observations, the achieved synthesized beams and root-mean-square (RMS) noise in the Briggs Robust$=$2.0 weighted images are summarized in Table [\[tab:obs\]](#tab:obs). We omitted the observations taken from epochs D-1 and D-2 (Table [\[tab:obs\]](#tab:obs)), owing to the compromised image quality and high RMS noise compared to the other observations taken at proximate time and frequency.

We jointly imaged all C band (4–8 GHz) observations taken in 2011, which yielded a 5.3 $\mu$Jy beam$^{-1}$ RMS noise. The target source, DM Tau, was neither detected in this image nor in the individual epochs of C band observations. DM Tau was also not detected in the X band (8–10 GHz) observations taken in 2013 (Table [\[tab:obs\]](#tab:obs); c.f., (cite: Zapata2017ApJ...834..138Z)). These results stand contrast to the significant X and Ku band detections in 2019 ((cite: Terada2023ApJ...953..147T)), which can only be explained by variability. We tried jointly imaging some Q band (40–48 GHz) observations using various combinations of observations and tapering. When concatenating the Q band data, the A, (B & BnA), and C array configuration observations were re-weighed (by factors of 4, 2, and 1, respectively) to yield a synthesized beam that is approximately Gaussian. We created the fiducial Q band image by limiting the *uv* distance range to $>$200 $k\lambda$. This helps achieve a synthesized beam that is small enough for diagnosing asymmetries. The 40–48 GHz flux densities are dominated by spatially compact sources and thus there is no issue of missing short-spacing. Using Briggs Robust$<2$ weighting (e.g., Robust$=$0, 1) to yield smaller synthesized beams significantly enhanced the thermal noise level, which is adverse for discerning localized sources. The profiles of the Q band images are discussed below in the relevant context.

# Results

Figure [1](#fig:image) shows a comparison of the Q band (40–48 GHz; $\sim$7 mm) continuum image generated from combining all the observations at $>$200 k$\lambda$ *uv* distances (Q-fiducial image, hereafter) and the ALMA 225 GHz image made at the same synthesized beam (Section [2.1](#sec:data)). In Appendix [6](#appendix:image), we provide the Q band images that were made from (1) combining all the Q band data we utilized (Q-all image, hereafter), (2) combining all observations taken in the A array configuration in 2019 (Q-A image, hereafter), (3) combining all observations taken in the A, BnA, and B configurations (Q-AB image, hereafter), and (4) combining only the observations taken in the B and BnA array observations in late 2012 (Q-B image, hereafter). In all these images, we only significantly detected the 40-48 GHz emission in a small region that is presented in the right panel of Figure [1](#fig:image).

The most prominent feature in the ALMA image is a ring at $\sim$25 au radii that is only weakly asymmetric.

In the $\sim$0.035$''$ resolution 225 GHz image published by (cite: Hashimoto2021ApJ...911....5H), only a very weak over-intensity (namely blob A, with a $\sim$1.2 contrast ratio) in the west can be robustly identified; a weaker blob B may be present in the south (contrast ratio $\sim$1.1) which remains to be confirmed by observations that have a better image fidelity. The contrast ratios of blobs A and B were smeared to be lower when smoothing the ALMA image to the synthesized beam of our JVLA image. In Figure [1](#fig:image), although a northern and a southern arcs in the $\sim$25 au ring can be marginally seen in the ALMA image, they were in fact artifiically created by the well known effect of synthesized beam smearing (see Equation 9 of (cite: Doi2021ApJ...912..164D)), which can be examined by smoothing the ALMA image.

In contrast, the JVLA Q band continuum images are dominated by an incomplete ring (Figure [1](#fig:image), right panel). In the Q band, in both the Q-A image taken in 2019 and the Q-B image taken in 2012, the intensity peaks located at the south, which are offset from the major axis (P.A.$=$157.8$^{\circ}$; (cite: Kudo2018ApJ...868L...5K)) of the 225 GHz ring. The consistency between these JVLA images is hard to explain if the resolved features were spuriously created due to thermal noise or imaging artifacts. With a better brightness temperature sensitivity, the Q-B image additionally detected an overintensity in the north. The Q band observations also detected emission sources that are distributed over the $\sim$25 au ring, which appear knotty in the Q-A or Q-AB images. In the Q-A image, some knots in the southeast and east have comparable or higher peak S/N than the most significant clump found in the Q-fiducial image and thus cannot be attributed to imaging artifacts.

In the Q-fiducial image (Figure [1](#fig:image)), several knots are detected at $\sim$3–6$\sigma$ level in east to south within the 25 au ring. They occupy about half of the ring and contribute $\sim300~\mu$Jy out of the free-free (Section [4.1](#sub:sed)) subtracted Q-band flux density of $\sim$500 $\mu$Jy. Assuming the remaining 200 $\mu$Jy is distributed smoothly in the other half of the ring (corresponding to $\sim6$ beam elements), we consider that the brightest knot in the south ($\sim$ 60 $\mu$Jy) may be at least 100% brighter than the opposite side of the ring. This is a lower limit of the level of asymmetry in 40–48 GHz. In contrast, the asymmetry in the higher angular resolution (0.035$''$) ALMA 225 GHz image is only $\sim$20% brighter than the opposite side of the ring ((cite: Hashimoto2021ApJ...911....5H)). Moreover, the blob A reported by (cite: Hashimoto2021ApJ...911....5H), in fact, is not co-located with the knots resolved in the Q-fiducial image. Also, "blob *B"* is also spatially offset from the brightest knot in the Q-fiducial image.

![](dmtau_sed_log.pdf)

The Q-B image made with 41–43 GHz observations (Table [\[tab:obs\]](#tab:obs)) additionally revealed some emission slightly inward of the eastern part of the $\sim$25 au ring, which appears a lot dimmer in the Q-all image, which has a slightly smaller synthesized beam. The 41–43 GHz emission inward of the $\sim$25 au ring is likely to be tracing the time-varying free-free emission. We cannot reliably analyze the 8–48 GHz spectral indices of the 40–48 GHz emission sources in the image domain due to the limited signal-to-noise ratio (S/N), and due to that the previous 8–12 GHz and 12–18 GHz images have indicated that both the flux density and position angles of the free-free emission sources may change day by day ((cite: Terada2023ApJ...953..147T)). We provide the quantitative estimates of the degree of free-free contamination in the 40–48 GHz images in Appendix [8](#appendix:freefree).

The comparison of the Q-A and Q-B images indicates that there is a stationary, azimuthally asymmetric 40–48 GHz ($\sim$7 mm) emission component in the $\sim$25 au ring, whose origin is likely attributable to dust emission. The presence of a (incomplete) ring can also be seen by directly analyzing the complex visibilities (for details, see Appendix [7](#appendix:asym)). The upper panel of Figure [2](#fig:dipole) shows the real part of the $m=0$ moment (i.e., azimuthal averaging) of the complex visibilities taken from the Q band, B and BnA array configuration observations (Table [\[tab:obs\]](#tab:obs)). Its shape is indeed consistent with that of the ring. It crosses zero at $\sim$500 k$\lambda$ *uv*-distance, which corresponds to a $\sim$0.15$''$ ($\sim$23 au) ring radius. Fitting it with a 0$^{\mbox{\scriptsize th}}$ order Bessel function of the first kind (Appendix [7](#appendix:asym)) indicates that the radius of the ring is $\sim$0.16$''$ ($\sim$23 au) which agrees with the $\sim$25 au ring seen in the ALMA image.

We performed a model-independent assessment of the azimuthal asymmetry at Q band by examining the dipole ($m=1$) moments of the B and BnA configuration visibility amplitudes (Figure [2](#fig:dipole)) which are sensitive to the angular scales of the $\sim$25 au ring (for details see Appendix [7](#appendix:asym)). Owing to the high noise, and due to the fact that the noise in the visibility amplitudes is positively biased, we are unable to robustly fit the dipole moments with a Bessel function. Nevertheless, from Figure [2](#fig:dipole), it is still possible to visually identify weakly enhanced signals (with respect to pure noise) at 500–1000 k$\lambda$ with a peak at $\sim$600 k$\lambda$. This indicates that the Q-Band intensity is azimuthally asymmetric on the spatial scale of $\sim 20$ au or less. Higher sensitivity data will robustly confirm the presence of asymmetry. The asymmetry may be caused by the non-uniform distribution of large grains within the $\sim$25 au ring or that of free-free emission sources ((cite: Terada2023ApJ...953..147T)).

Figure [3](#fig:sed_log) shows the 8–700 GHz SED of DM Tau and some upper limits at lower frequencies. We measured the 40–48 GHz flux density in 2019 from the Q-A image using aperture photometry. The flux densities of the other observations were extracted using two-dimensional (2D) Gaussian fittings. The SED presents complicated frequency variations and thus cannot be appropriately described or discussed assuming a constant spectral index. Instead, it signifies that there might be more than one emission sources, with one or some of them dominating the flux densities at certain frequency intervals. A more detailed discussion about the nature of these emission sources is given in Section [4](#sec:discussion).

# Discussion

## Spectral index distribution and model

We are based on a spatially unresolved SED model to diagnose the properties of the observed dust emission sources. The rationale of this approach is detailed in Appendix [9](#appendix:mcmc). In our models, the overall flux density is described by (quoting Equation 3 of (cite: Liu2019ApJ...884...97L)):

$$\begin{equation}
\label{eqn:multicomponent}
    F_{\nu} = \sum\limits_{i} F_{\nu}^{i} e^{-\sum\limits_{j}\tau^{i,j}_{\nu}}, 
\end{equation}$$ where $F_{\nu}^{i}$ is the flux density of the dust or free-free emission component, $i$, and $\tau^{i,j}_{\nu}$ is the optical depth of the emission component, $j,$ to obscure the emission component $i$ (e.g., $\tau^{i,j}_{\nu}=0$ if the component $i$ is not obscured by any other component in the line of sight).

For any emission component, the $F_{\nu}^{i}$ depends on the two free parameters, temperature ($T$) and solid angle ($\Omega$). For the free-free emission component, we adopted the approximated formulation outlined in (cite: Mezger1967ApJ...147..471M) and (cite: Keto2003ApJ...599.1196K), where $F_{\nu}^{i}$ depends on another free parameter: the emission measure ($EM$). We adopted the formulations and the default DSHARP size-dependent dust opacity tables published in (cite: Birnstiel2018ApJ...869L..45B) for the dust emission component. The default DSHARP opacity table assumes that the dust grains are compact and composed of water ice (cite: Warren1984ApOpt..23.1206W), astronomical silicates (cite: Drain2003ARA&A..41..241D), troilite, and refractory organics ((cite: Henning1996A&A...311..291H). The dust grain size ($a$) distribution $n(a)$ was assumed to be a power-law $\propto a^{-q}$ in between the minimum and maximum grain sizes ($a_{\mbox{\scriptsize min}}$, $a_{\mbox{\scriptsize max}}$), while it is 0 elsewhere. We assumed q=3.5 ((cite: Mathis1977ApJ...217..425M; Doi2023arXiv230816574D)) and nominally fixed the value of $a_{\mbox{\scriptsize min}}$ to $10^{-4}$ mm, since the (sub)millimeter opacity depends very weakly on $a_{\mbox{\scriptsize min}}$. In this case, the $F_{\nu}^{i}$ of dust emission components depend further on $a_{\mbox{\scriptsize max}}$ and dust column density ($\Sigma_{\mbox{\scriptsize dust}}$).

Given the large contrast between the morphology resolved in the ALMA 225 GHz and JVLA 40–48 GHz images (Figure [1](#fig:image)), it may be more appropriate to describe the SED with at least two dust components. We found that the observed SED (Figure [3](#fig:sed_log)) can be approximated with a small dust component, a grown dust component, and a free-free emission component. The free parameters of these components were optimized using the Markov chain Monte Carlo (MCMC) method, which are summarized in Table [\[table:model\]](#table:model). We regarded the parameters represented by the 50th percentile of the MCMC samples as the best-fit parameters. The best-fit models are overplotted with the observational data in Figure [3](#fig:sed_log), with the corner plots given in Figure [8](#fig:corner).

From Figure [3](#fig:sed_log), we see that the observed flux densities at $>$40 GHz are reasonably well explained. However, the Ka band (31.7–33.7 GHz) data and a X band (8.0–10.0 GHz) non-detection are largely offset from the best-fit model, probably due to the variability of free-free emission. At X band, this can be seen by comparing the non-detection in 2013 ((cite: Zapata2017ApJ...834..138Z)) and the detection in 2019 ((cite: Terada2023ApJ...953..147T); Figure [3](#fig:sed_log)); the variability at Ka band has not been directly constrained since there was only one epoch of observations in 2010 (Table [\[tab:obs\]](#tab:obs)). As a consequence of the poorly constrained variability, the free parameters of the free-free emission components were barely constrained (Figure [8](#fig:corner)).

+:-------------:+:--------------------:+:---------------------------------:+:----------------------------------:+:-------------------------:+:----------------------------------:+:-----------------------------:+
|               | $T$                  | $\Omega$$^{a}$                    | $\Sigma_{\mbox{\scriptsize dust}}$ | $a_{\mbox{\tiny max}}$    | EM                                 | $M_{\mbox{\scriptsize dust}}$ |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
|               | \(K\)                | ($10^{-12}$ sr)                   | (g cm$^{-2}$)                      | \(mm\)                    | (cm$^{-6}$ pc)                     | $M_{\oplus}$                  |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
|               | \(1\)                | \(2\)                             | \(3\)                              | \(4\)                     | \(5\)                              | \(6\)                         |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| Model with two dust components                                                                                                                                                                                 |
+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| small dust                                                                                                                                                                                                     |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| Initial$^{b}$ | 14.0                 | 6.5                               | 3.5                                | 0.045                     | $\cdots$                           | 690                           |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| MCMC$^{c}$    | 12.4$^{+2.7}_{-1.7}$ | 8.5$^{+2.8}_{-2.6}$               | 2.51$^{+0.81}_{-0.56}$             | 0.055$^{+0.021}_{-0.028}$ | $\cdots$                           | 640$^{+490}_{-300}$           |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| grown dust                                                                                                                                                                                                     |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| Initial$^{b}$ | 14.0                 | 2.5                               | 10.0                               | 0.35                      | $\cdots$                           | 750                           |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| MCMC$^{c}$    | 14.5$^{+6.1}_{-4.2}$ | 2.9$^{+1.3}_{-1.1}$               | 9.55$^{+3.9}_{-3.7}$               | 0.306$^{+0.195}_{-0.087}$ | $\cdots$                           | 840$^{+870}_{-520}$           |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| free-free emission                                                                                                                                                                                             |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| Initial$^{b}$ | 8000                 | 4$\cdot$10$^{-3}$                 | $\cdots$                           | $\cdots$                  | 5$\cdot$10$^{8}$                   | $\cdots$                      |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| MCMC$^{c}$    | 8000                 | 3.2$^{+2.2}_{-1.7}\cdot$10$^{-3}$ | $\cdots$                           | $\cdots$                  | 4.5$^{+3.5}_{-2.8}$$\cdot$10$^{8}$ | $\cdots$                      |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| Model with one dust component                                                                                                                                                                                  |
+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| dust                                                                                                                                                                                                           |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| Initial$^{b}$ | 14.0                 | 6.5                               | 3.5                                | 0.045                     | $\cdots$                           | 690                           |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| MCMC$^{c}$    | 15.4$^{+0.4}_{-0.4}$ | 6.1$^{+0.3}_{-0.3}$               | 6.9$^{+0.1}_{-0.2}$                | 0.021$^{+0.02}_{-0.01}$   | $\cdots$                           | 1280$^{+80}_{-100}$           |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| free-free emission                                                                                                                                                                                             |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| Initial$^{b}$ | 8000                 | 4$\cdot$10$^{-3}$                 | $\cdots$                           | $\cdots$                  | 5$\cdot$10$^{8}$                   | $\cdots$                      |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+
| MCMC$^{c}$    | 8000                 | 2.9$^{+2.4}_{-1.2}\cdot$10$^{-3}$ | $\cdots$                           | $\cdots$                  | 4.0$^{+3.1}_{-2.0}\cdot$10$^{8}$   | $\cdots$                      |
+---------------+----------------------+-----------------------------------+------------------------------------+---------------------------+------------------------------------+-------------------------------+

Table notes:

The solid angle of the small dust component is comparable to what can be expected from the ALMA 225 GHz image (Figure [1](#fig:image), left panel). The grown dust component has a smaller solid angle; this component may largely represent the azimuthally asymmetric, knotty 40–48 GHz intensity distribution resolved in the Q-A or Q-AB images (Figure [1](#fig:image), [4](#fig:moreimage)). The ALMA 225 GHz image only presents a weak azimuthal asymmetry (Figure [1](#fig:image)), likely due to the high optical depths of both the grown and small dust components. Conversely, the large contrast between the morphology resolved at 225 GHz and 40-48 GHz means that DM Tau cannot be optically thin at 225 GHz.

We only obtained a loose constraint on the $a_{\mbox{\scriptsize max}}$ of the small dust component, although we can be certain that it is below 100 $\mu$m. The $a_{\mbox{\scriptsize max}}$ value of the grown dust component has the highest probability of being around 0.2 mm, while the best-fit value is slightly higher due to degeneracy. We note that this degeneracy in the $a_{\mbox{\scriptsize max}}$ value may not be entirely artificial. While we only used one grown dust component in the model, the degeneracy in $a_{\mbox{\scriptsize max}}$ may reflect the fact that there are multiple optically thick dust concentrations that have various $a_{\mbox{\scriptsize max}}$ values. Presently, the best-fit $a_{\mbox{\scriptsize max}}$ value (0.3 mm) for the grown dust component should be regarded as a conservative lower limit. Due to the confusion of the time-varying free-free emission, we cannot presently rule out the possibility that there are dust concentrations that the $a_{\mbox{\scriptsize max}}$ are $\gtrsim$1 mm and can fractionally contribute to significant emission at $\sim$20–40 GHz. In the integrated SED (Figure [3](#fig:sed_log)), the excess of dust emission at $<$50 GHz does not look particularly obvious. Nevertheless, the $<$50 GHz excess is very significant if we examine the SEDs of some specific locations, for example, one synthesized beam area that covers the location of peak in the Q-fiducial image (Figure [1](#fig:image)).

In our best-fit, the grown dust component ($a_{\mbox{\scriptsize max}}\sim$0.3 mm) may have a comparably larger dust mass than the small dust component ($a_{\mbox{\scriptsize max}}\sim$50 $\mu$m), although the mass in the grown dust component may become smaller once its $a_{\mbox{\scriptsize max}}$ is updated to larger values in the future observational studies. The overall dust mass in our best-fit model is 1440$^{+1360}_{-820}$ Earth masses ($M_{\oplus}$). Large dust mass indicates a low gas-to-dust ratio for the disk to be stable against gravitational instability. Our dust mass estimates may be regarded upper limits, since the default DSHARP dust are not as opaque as those that included graphitic carbons (e.g., (cite: Ricci2010A&A...512A..15R; Woitke2016A&A...586A.103W)). In addition, it is possible to reduce the dust mass in the small dust component if we model it as two separate components that have distinct $a_{\mbox{\scriptsize max}}$ values. If we make the $a_{\mbox{\scriptsize max}}$ of one of them close to $\sim$100 $\mu$m, the anomalous reddening effect ((cite: Liu2019ApJ...877L..22L)) allows us to fit the (close to 2.0) spectral index observed at 200–400 GHz (Chung et al. submitted) with a dust column density that is considerably lower than our present best-fit value for the small dust component (Table [\[table:model\]](#table:model)). Nevertheless, the differences in the assumed opacities should not change the orders of magnitude of our dust mass estimates; as discussed above, the small dust component is unlikely to be optically thin everywhere. The grown dust mass budget in DM Tau may be sufficient for feeding the formation of massive planets that the metal masses are as high as several 10$^{2}$ $M_{\oplus}$ (c.f., (cite: Sato2005ApJ...633..465S; Thorngren2016ApJ...831...64T)).

Notwithstanding, we also tried fitting the observed SED with only one dust component, which is the approach we can take provided with only the unresolved SEDs, but without the spatially resolved image. This fitting favors a small $a_{\mbox{\scriptsize max}}$ value of $\sim$21 $\mu$m while it yields a similar overall dust mass as what was given by the two-component fitting (Table [\[table:model\]](#table:model)). This result of single-component fitting may be read with a caution, as we briefly discuss in Appendix [9](#appendix:mcmc).

## Physical implications

### Asymmetry in protoplanetary disks

Physically, two general ideas have been proposed to explain asymmetries in disk rings. In the first, the entire ring is asymmetric, and dust in the entire ring drifts towards a single azimuthal pressure bump. Such an azimuthal pressure bump may be realized by a global scale vortex ((cite: Birnstiel2013A&A...550L...8B)). The resulting dust asymmetries tend to have substantial contrasts. Possible examples in observations include IRS 48 ((cite: Ninke2013Sci...340.1199V; Ninke2015ApJ...810L...7V; Ohashi2020ApJ...900...81O)) and HD 142527 ((cite: Casassus2013Natur.493..191C; Kataoka2016ApJ...831L..12K; Satoshi2018ApJ...864...81O)). In the second scenario, the bulk of the ring is symmetric and asymmetries only arise in small localized regions due to certain properties, for example: small vortices. There can be more than one azimuthal dust concentration and part of the ring may not be affected by any dust concentration (i.e., in the smooth “background”). Such small-scale asymmetries may arise from hydrodynamic instabilities, as proposed in (cite: Li2020ApJ...892L..19L) and (cite: Huang2020ApJ...893...89HVortex). DM Tau and LkCa 15 ((cite: Isella2014ApJ...788..129I; Jin2019ApJ...881..108J; Facchini2020A&A...639A.121F)), may be examples of this type. The classification of the recently reported very-low-mass disks CIDA 1 ((cite: Pinilla2018CIDA1; Hashimoto2023arXiv230811837H)) is not yet clear since the asymmetry, despite being detected by the JVLA observations, was not resolved at a high spatial dynamic range.

Phenomenologically, we may also classify sources based on the morphology at 225 GHz and 40–48 GHz. The first kind appears largely azimuthally asymmetric at both 225 GHz and 40–48 GHz (e.g., IRS 48, MWC 758; (cite: Ninke2015ApJ...810L...7V; Ohashi2020ApJ...900...81O; Dong2018ApJ...860..124DMWC758; Casassus2019MNRAS.483.3278C)). In each of the two cases, IRS 48 and MWC 758, the 225–345 GHz peak and the 30–50 GHz peak are closely associated with each other. The second kind appears azimuthally symmetric or only weakly asymmetric, at both frequencies (e.g., GM Aur, HL Tau; (cite: Carrasco2016ApJ...821L..16C; Carrasco2019ApJ...883...71C; Macias2018ApJ...865...37M)).

The DM Tau dusty disk, which appears weakly azimuthally asymmetric and smooth at $\gtrsim$200 GHz and then appears highly asymmetric at $\lesssim$50 GHz, may represent a link between these two kinds. It may provide a hint that at least some symmetric and asymmetric disks potentially have a unified origin. For example, they may be simply related by optical depths, otherwise by their progress on developing azimuthally asymmetric $a_{\mbox{\scriptsize max}}$ distributions. In both cases, the observations at lower frequencies (i.e., longer wavelengths) may tend to find the disks asymmetric. In the former case, the lower optical depths at low frequency (e.g., $\lesssim$50 GHz) allow for the localized (sub)structures to be resolved at higher contrasts. Substructures that harbor pebble-sized (e.g., mm–cm) dust may also appear more prominent than the ambient dusty disk structures at $\lesssim$50 GHz frequencies, due to the higher emissivity of pebble-sized dust at such frequencies. Conversely, at a specific observing frequency, the apparent morphology of a disk that harbors substructures may evolve from weakly asymmetric to significantly asymmetric if the small dust grains that are aptly coupled with the (azimuthally symmetric) gaseous disk are depleted over time. The depletion of small dust grains reduces the overall optical depths; it also removes the azimuthally symmetric components. At $>$200 GHz, we may hypothesize that the morphology of DM Tau, CIDA 1, and LkCa 15 may become more like the classical asymmetric sources resolved in the previous $\sim$225 or $\sim$345 GHz observations (e.g., HD 142527, AB Aur, SR 21, SY Cha, MWC 758; Oph IRS 48; (cite: Hashimoto2011ApJ...729L..17H; Fukagawa2013PASJ...65L..14F; Ninke2013Sci...340.1199V; Satoshi2018ApJ...864...81O; Casassus2013Natur.493..191C; Tang2017ApJ...840...32T; Dong2018ApJ...860..124DMWC758; Casassus2019MNRAS.483.3278C; Yang2023ApJ...948..110Y; Orihara2023PASJ...75..424O)) when some small dust is depleted (e.g., by converting to grown dust and/or by dust and gas mass dispersal). AB Aur is indeed dominated by optically thinner dust emission that has a 3.34$^{+0.18}_{-0.18}$ spectral index at 200–400 GHz (Chung et al. submitted).

### Dust growth in an initially smooth background disk

Thanks to the bigger size of the DM Tau disk, the present, spatially well-resolved case study provides a clearer physical picture. From Figure [1](#fig:image), it appears that the grown dust ($\gtrsim$300 $\mu$m) were detected at the inner edge of the 20–120 au outer DM Tau dusty ring. Physically, this may be because that the $\gtrsim$100 $\mu$m sized dust becomes dynamically decoupled from the gaseous disk and rapidly migrated inward, until it is trapped by a pressure bump ((cite: Zsom2010A&A...513A..57Z; Birnstiel2016SSRv..205...41B)). In DM Tau, outside of the water-snow line, the presence of grown dust appears to be linked to the dust azimuthal asymmetries. It is not yet clear to us whether the dust azimuthal asymmetries facilitate further dust growth in the icy world or the asymmetry is a consequence of dust growth and dust migration. One concordant interpretation for the creation of the dust cavity (or gap), dust trapping in the inner edge of the $\sim$25 au ring and the azimuthally asymmetric distribution of grown dust may be planet-disk interaction (e.g., (cite: Dong2018ApJ...866..110D; Li2020ApJ...892L..19L) and references therein). Grain growth may be further promoted at the dust traps if the dust-to-gas mass ratios are locally enhanced, which may be an important mechanism to facilitate the formation of comets or ice giants in cases where the water-ice coated dust grains are not particularly sticky ((cite: Kimura2015ApJ...812...67K; Musiolik2019ApJ...873...58M; Steinpilz2019ApJ...874...60S; Pillich2021A&A...652A.106P; Arakawa2023ApJ...951L..16A)). Inefficient coagulation of icy dust grains may also explain why the dust mass in the 20–120 au ring in DM Tau has been largely preserved instead of being consumed to the formation of planetesimals or planets, and why the $a_{\mbox{\scriptsize max}}$ value in the 20–120 au ring remains $<$100 $\mu$m.

# Conclusion

DM Tau is a representative transitional disk whose weakly asymmetric dusty outer ring at 20–120 au radii has been resolved in the previous, high-angular-resolution ALMA 225 GHz continuum image. We carried out the 0.06$''$ ($\sim$8.7 au) resolution JVLA 40–48 GHz observations towards DM Tau and retrieved the archival JVLA observations on DM Tau that were taken after 2010. Intriguingly, the JVLA 40–48 GHz observations resolved an incomplete, knotty, ring-like structure at the radii ($\sim$25 au) that have a maximized 225 GHz intensity. Based on the resolved morphologies and the modeling for the 8–700 GHz SED, we found that the $>$225 GHz flux densities are dominated by optically thick dust thermal emission, while the $<$50 GHz flux densities are contributed by the dust thermal emission and time-varying free-free emission. In addition, our fiducial SED model indicates that the incomplete knotty ring resolved at 40–48 GHz is composed of some high column density dust concentrations that the maximum grain size $a_{\mbox{\scriptsize max}}$ is greater than 0.3 mm; in contrast, the rather symmetric 20–120 au ring resolved at 225 GHz traces a small dust population that the $a_{\mbox{\scriptsize max}}$ is only as large as $\sim$50 $\mu$m. The grown and small dust occupy different areas in the ring without apparent mutual obscuration.

Assuming the default DSHARP dust opacity, the overall dust mass in our SED model is 1440$^{+1360}_{-820}$ $M_{\oplus}$, which is approximately evenly shared by the grown ($a_{\mbox{\scriptsize max}}\gtrsim$300 $\mu$m) and small ($a_{\mbox{\scriptsize max}}\lesssim$50 $\mu$m) dust. In the DM Tau disk, the overall dust mass budget is likely largely preserved and is still sufficient for feeding to planetesimal and planet formation. Outside of the water-snow line in DM Tau, dust growth may not be rapid or efficient. Only a portion of the dust has been converted to "grown" dust ($a_{\mbox{\scriptsize max}}\gtrsim$0.3 mm), which may have migrated inward until it is trapped close to the inner edge of the DM Tau outer ring. Planet-disk interactions or shear instability may further lead to an azimuthally symmetric pressure distribution or the formation of vortices, resulting in the observed knotty and azimuthally asymmetric distribution of the grown dust component. As the small dust in the DM Tau is gradually depleted (e.g., due to grain growth or disk gas and dust mass dispersal), its morphology at 225 GHz (e.g., ALMA Band 6) may come to resemble well known asymmetric transitional disks such as AB Aur or HD142527.

# Acknowledgements

We thank the referee for the useful suggestions. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This paper makes use of the following ALMA data: ADS/JAO.ALMA #2013.1.00498.S, #2013.1.00647.S, #2015.1.00296.S, #2016.1.00565.S., #2016.1.01042.S, #2017.1.01460.S, #2018.1.01755.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The Submillimeter Array is a joint project between the Smithsonian Astrophysical Observatory and the Academia Sinica Institute of Astronomy and Astrophysics, and is funded by the Smithsonian Institution and the Academia Sinica ((cite: Ho2004ApJ...616L...1H)). H.B.L. is supported by the National Science and Technology Council (NSTC) of Taiwan (Grant Nos. 111-2112-M-110-022-MY3). This work was supported by JSPS KAKENHI Grant Number 23K03463 and 18H05441. T.M. is supported by Yamada Science Foundation Overseas Research Support Program. Y.H. was supported by the Jet Propulsion Laboratory, California Institute of Technology, under a contract with the National Aeronautics and Space Administration (80NM0018D0004).

72 natexlab

(ref: ALMA2015ApJ...808L...3A) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3

(ref: Andrews2020ARA&A..58..483A) Andrews, S. M. 2020, ARA&A, 58, 483

(ref: Andrews_2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41

(ref: Andrews2011ApJ...732...42A) Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42

(ref: Anglada1998AJ....116.2953A) Anglada, G., Villuendas, E., Estalella, R., et al. 1998, AJ, 116, 2953

(ref: Arakawa2023ApJ...951L..16A) Arakawa, S., Okuzumi, S., Tatsuuma, M., et al. 2023, ApJL, 951, L16

(ref: Bergin2004ApJ...614L.133B) Bergin, E., Calvet, N., Sitko, M. L., et al. 2004, ApJL, 614, L133

(ref: Birnstiel2013A&A...550L...8B) Birnstiel, T., Dullemond, C. P., & Pinilla, P. 2013, A&A, 550, L8

(ref: Birnstiel2018ApJ...869L..45B) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45

(ref: Birnstiel2016SSRv..205...41B) Birnstiel, T., Fang, M., & Johansen, A. 2016, Space Sci. Rev., 205, 41

(ref: Calvet2005ApJ...630L.185C) Calvet, N., D’Alessio, P., Watson, D. M., et al. 2005, ApJL, 630, L185

(ref: Carrasco2016ApJ...821L..16C) Carrasco-González, C., Henning, T., Chandler, C. J., et al. 2016, ApJL, 821, L16

(ref: Carrasco2019ApJ...883...71C) Carrasco-González, C., Sierra, A., Flock, M., et al. 2019, ApJ, 883, 71

(ref: Casassus2019MNRAS.483.3278C) Casassus, S., Marino, S., Lyra, W., et al. 2019, MNRAS, 483, 3278

(ref: Casassus2013Natur.493..191C) Casassus, S., van der Plas, G. M., Perez, S., et al. 2013, Nature, 493, 191

(ref: Doi2021ApJ...912..164D) Doi, K. & Kataoka, A. 2021, ApJ, 912, 164

(ref: Doi2023arXiv230816574D) Doi, K. & Kataoka, A. 2023, arXiv e-prints, arXiv:2308.16574

(ref: Dong2018ApJ...866..110D) Dong, R., Li, S., Chiang, E., & Li, H. 2018a, ApJ, 866, 110

(ref: Dong2018ApJ...860..124DMWC758) Dong, R., Liu, S.-y., Eisner, J., et al. 2018b, ApJ, 860, 124

(ref: Drain2003ARA&A..41..241D) Draine, B. T. 2003, ARA&A, 41, 241

(ref: Dzib2015ApJ...801...91D) Dzib, S. A., Loinard, L., Rodrı́guez, L. F., et al. 2015, ApJ, 801, 91

(ref: Facchini2020A&A...639A.121F) Facchini, S., Benisty, M., Bae, J., et al. 2020, A&A, 639, A121

(ref: Foreman-Mackey2013PASP) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: Fukagawa2013PASJ...65L..14F) Fukagawa, M., Tsukagoshi, T., Momose, M., et al. 2013, PASJ, 65, L14

(ref: Gaia_2023) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1

(ref: Hashimoto2012ApJ...758L..19H) Hashimoto, J., Dong, R., Kudo, T., et al. 2012, ApJL, 758, L19

(ref: Hashimoto2022ApJ...941...66H) Hashimoto, J., Liu, H. B., Dong, R., Liu, B., & Muto, T. 2022, ApJ, 941, 66

(ref: Hashimoto2023arXiv230811837H) Hashimoto, J., Liu, H. B., Dong, R., et al. 2023, arXiv e-prints, arXiv:2308.11837

(ref: Hashimoto2021ApJ...911....5H) Hashimoto, J., Muto, T., Dong, R., et al. 2021, ApJ, 911, 5

(ref: Hashimoto2011ApJ...729L..17H) Hashimoto, J., Tamura, M., Muto, T., et al. 2011, ApJL, 729, L17

(ref: Henning1996A&A...311..291H) Henning, T. & Stognienko, R. 1996, A&A, 311, 291

(ref: Ho2004ApJ...616L...1H) Ho, P. T. P., Moran, J. M., & Lo, K. Y. 2004, ApJL, 616, L1

(ref: Huang2020ApJ...893...89HVortex) Huang, P., Li, H., Isella, A., et al. 2020, ApJ, 893, 89

(ref: Isella2014ApJ...788..129I) Isella, A., Chandler, C. J., Carpenter, J. M., Pérez, L. M., & Ricci, L. 2014, ApJ, 788, 129

(ref: Jin2019ApJ...881..108J) Jin, S., Isella, A., Huang, P., et al. 2019, ApJ, 881, 108

(ref: Kataoka2016ApJ...831L..12K) Kataoka, A., Tsukagoshi, T., Momose, M., et al. 2016, ApJL, 831, L12

(ref: Keto2003ApJ...599.1196K) Keto, E. 2003, ApJ, 599, 1196

(ref: Kimura2015ApJ...812...67K) Kimura, H., Wada, K., Senshu, H., & Kobayashi, H. 2015, ApJ, 812, 67

(ref: Ko2020ApJ...889..172K) Ko, C.-L., Liu, H. B., Lai, S.-P., et al. 2020, ApJ, 889, 172

(ref: Kudo2018ApJ...868L...5K) Kudo, T., Hashimoto, J., Muto, T., et al. 2018, ApJL, 868, L5

(ref: Li2020ApJ...892L..19L) Li, Y.-P., Li, H., Li, S., et al. 2020, ApJL, 892, L19

(ref: Liu2019ApJ...877L..22L) Liu, H. B. 2019, ApJL, 877, L22

(ref: Liu2016ApJ...821...41L) Liu, H. B., Lai, S.-P., Hasegawa, Y., et al. 2016, ApJ, 821, 41

(ref: Liu2019ApJ...884...97L) Liu, H. B., Mérand, A., Green, J. D., et al. 2019, ApJ, 884, 97

(ref: Liu2021ApJ...923..270L) Liu, H. B., Tsai, A.-L., Chen, W. P., et al. 2021, ApJ, 923, 270

(ref: Macias2018ApJ...865...37M) Macı́as, E., Espaillat, C. C., Ribas, Á., et al. 2018, ApJ, 865, 37

(ref: Mathis1977ApJ...217..425M) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425

(ref: McMullin2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mezger1967ApJ...147..471M) Mezger, P. G. & Henderson, A. P. 1967, ApJ, 147, 471

(ref: Musiolik2019ApJ...873...58M) Musiolik, G. & Wurm, G. 2019, ApJ, 873, 58

(ref: Satoshi2018ApJ...864...81O) Ohashi, S., Kataoka, A., Nagai, H., et al. 2018, ApJ, 864, 81

(ref: Ohashi2020ApJ...900...81O) Ohashi, S., Kataoka, A., van der Marel, N., et al. 2020, ApJ, 900, 81

(ref: Okuzumi2016ApJ...821...82O) Okuzumi, S., Momose, M., Sirono, S.-i., Kobayashi, H., & Tanaka, H. 2016, ApJ, 821, 82

(ref: Orihara2023PASJ...75..424O) Orihara, R., Momose, M., Muto, T., et al. 2023, PASJ, 75, 424

(ref: Pillich2021A&A...652A.106P) Pillich, C., Bogdan, T., Landers, J., Wurm, G., & Wende, H. 2021, A&A, 652, A106

(ref: Pinilla2018CIDA1) Pinilla, P., Natta, A., Manara, C. F., et al. 2018, A&A, 615, A95

(ref: Rau2011A&A...532A..71R) Rau, U. & Cornwell, T. J. 2011, A&A, 532, A71

(ref: Ricci2010A&A...512A..15R) Ricci, L., Testi, L., Natta, A., et al. 2010, A&A, 512, A15

(ref: Sato2005ApJ...633..465S) Sato, B., Fischer, D. A., Henry, G. W., et al. 2005, ApJ, 633, 465

(ref: Steinpilz2019ApJ...874...60S) Steinpilz, T., Teiser, J., & Wurm, G. 2019, ApJ, 874, 60

(ref: Takahashi2014ApJ...794...55T) Takahashi, S. Z. & Inutsuka, S.-i. 2014, ApJ, 794, 55

(ref: Tang2017ApJ...840...32T) Tang, Y.-W., Guilloteau, S., Dutrey, A., et al. 2017, ApJ, 840, 32

(ref: Terada2023ApJ...953..147T) Terada, Y., Liu, H. B., Mkrtichian, D., et al. 2023, ApJ, 953, 147

(ref: Thorngren2016ApJ...831...64T) Thorngren, D. P., Fortney, J. J., Murray-Clay, R. A., & Lopez, E. D. 2016, ApJ, 831, 64

(ref: Ninke2015ApJ...810L...7V) van der Marel, N., Pinilla, P., Tobin, J., et al. 2015, ApJL, 810, L7

(ref: Ninke2013Sci...340.1199V) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2013, Science, 340, 1199

(ref: Warren1984ApOpt..23.1206W) Warren, S. G. 1984, , 23, 1206

(ref: Woitke2016A&A...586A.103W) Woitke, P., Min, M., Pinte, C., et al. 2016, A&A, 586, A103

(ref: Yang2023ApJ...948..110Y) Yang, Y., Liu, H. B., Muto, T., et al. 2023, ApJ, 948, 110

(ref: Zapata2017ApJ...834..138Z) Zapata, L. A., Rodrı́guez, L. F., & Palau, A. 2017, ApJ, 834, 138

(ref: Zhang2015ApJ...806L...7Z) Zhang, K., Blake, G. A., & Bergin, E. A. 2015, ApJL, 806, L7

(ref: Zsom2010A&A...513A..57Z) Zsom, A., Ormel, C. W., Güttler, C., Blum, J., & Dullemond, C. P. 2010, A&A, 513, A57

# Images for the JVLA data taken in various array configurations

Figure [4](#fig:moreimage) shows the JVLA 40–48 GHz images produced with various combinations of observational data.

|                                     |                                    |
|:------------------------------------|:-----------------------------------|
| ![image](dmtau_JVLA_all_rob2.pdf)   | ![image](dmtau_JVLA_allA_rob2.pdf) |
| ![image](dmtau_JVLA_allAB_rob2.pdf) | ![image](dmtau_JVLA_allB_rob2.pdf) |

# Asymmetry

Here, we briefly outline a model-independent method to detect asymmetric structures from visibility data. A full description of the methods and the demonstration will be presented elsewhere as a separate paper. The asymmetric structure in the image domain corresponds to the asymmetric distribution of the visibility in the *uv* domain; therefore, it is possible to assess the existence of the asymmetric structures by direct investigation of visibility. If the real surface brightness distribution of the source on sky is $I(r,\theta)$, where $r$ is the distance from the central star and $\theta$ is the position angle measured from north to east, the visibility $V(\rho,\phi)$ is given by $$\begin{equation}
    V(\rho,\phi) = \int I(r,\theta) e^{ 2\pi i \rho r \sin(\theta+\phi)} r dr d\theta,
\end{equation}$$ where $\rho$ is the $uv$-distance and $\phi$ is the azimuthal angle in the $uv$-plane measured from the $u$-axis.

We define the $m^{\mbox{\scriptsize th}}$ multipole moment of the image as: $$\begin{equation}
    \tilde{I}_m (r) = \frac{1}{2\pi} \int_{0}^{2\pi} I(r,\theta) e^{-im\theta} d\theta.
\end{equation}$$ If the surface brightness distribution is axisymmetric, $\tilde{I}_m = 0$ for $m\neq 0$. The higher order $m$ modes correspond to the smaller scale asymmetry in the azimuthal direction. The brightness distribution on sky $I(r,\theta)$ is expressed as the Fourier series of $\sum \tilde{I}_m(r) e^{im\theta}$ over $-\infty<m<\infty$ and therefore the visibility distribution is given by: $$\begin{equation}
    V(\rho,\phi) = \sum_{m=-\infty}^{\infty} e^{im\phi} 2\pi \int_{0}^{\infty} \tilde{I}^{\ast}_{m} (r) J_m (2\pi \rho r) r dr,
\end{equation}$$ where $J_m(x)$ denotes the $m^{\mbox{\scriptsize th}}$ order Bessel function and the asterisk denotes the complex conjugate. This indicates that the Hankel transformation of $\tilde{I}_m(r)$ gives the $m^{\mbox{\scriptsize th}}$ multipole moment of the visibility distribution of the $uv$-space. If the $m^{\mbox{\scriptsize th}}$ moment of the asymmetric structure is located only at the radius $r_0$, $\tilde{I}_{m}(r)$ is proportional to $\delta(r-r_0)$. In this case, the profile of the $m^{\mbox{\scriptsize th}}$ moment of visibility is $J_m(2\pi \rho r_0)$. Since the locations of zeros and peaks of Bessel function are well determined, it is possible to estimate the radial location of a ring (for 0-th moment) or a blob (for 1st or higher moments) using the locations of characteristic features (i.e., peak and zero) of the visibility profile, assuming that there is only one significant structure in radial direction. In Table [1](#tab:BesselCharacter), we summarize the relationship between the radial location $r_0$ on sky and the $uv$-distances of the first peak and the first zero $m=0$ and $1$.

In the analyses presented in Figure [2](#fig:dipole), we average the data over all the spectral windows in 40–43 GHz band and the integration over 30 s to improve the S/N and reduce the data size, while keeping sufficient number of data points in the visibility domain. After deprojecting the data using $i=$35.2$^{\circ}$ and P.A.$=$157.8$^{\circ}$ (cite: Kudo2018ApJ...868L...5K), the $uv$-plane is divided into 50 radial bins having similar data weights. The moments of the visibility are then calculated in each radial bin.

We note that incomplete $uv$-coverage, which is inevitable in interferometric observations, can introduce fake asymmetric structures and therefore the visibility data may need to be deconvolved for the $uv$-coverage. For our dataset, we have checked that deconvolution does not affect our results and therefore, we present the analyses without deconvolution in this paper. We will discuss more about how the incomplete $uv$-coverage affects the moment analyses in a separate paper that focuses more on analysis techniques.

|  | $m=0$ | $m=1$ |
|:--:|:--:|:--:|
| First zero \[k$\lambda$\] | $789(r_0/0.1\ensuremath{''})^{-1}$ | $1258(r_0/0.1\ensuremath{''})^{-1}$ |
| Second zero \[k$\lambda$\] | $1258(r_0/0.1\ensuremath{''})^{-1}$ | $604(r_0/0.1\ensuremath{''})^{-1}$ |

: uv-distance scale of the first ($\rho>0$) zero-point and the peak for $m=0$ and $m=1$ modes assuming that the structure in the sky plane is located at $r=r_0$. The first peak of $m=0$ is at the same location with the first zero of $m=1,$ since $J_0(z) = -J^{\prime}_1(z)$.

# Free-free contamination in the 40–48 GHz images

|  |  |  |
|:---|:---|:---|
| ![image](dmtau_Ku2019Aug04.pdf) | ![image](dmtau_X2019Aug06.pdf) | ![image](dmtau_Ku2019Aug18.pdf) |

In this section, we based on the morphology resolved in the Q-fiducial image and the intensity of free-free emission resolved in the previous X band (8–12 GHz) and Ku band (12–18 GHz) observations to assess the degree of free-free contamination in the Q-fiducial image.

First, we point out that the knots resolved in the Q-fiducial image are spatially closely associated with the 25 au ring (Figures [1](#fig:image)). In Figure [5](#fig:freefreeimages), we compared the ALMA 225 GHz image and the Q-fiducial image with the X-band (8–12 GHz) and Ku-band (12–18 GHz) images reported by (cite: Terada2023ApJ...953..147T). Those low frequency observations mainly traced the time-varying free-free emission. The morphology of the free-free emission changed day by day while the peak intensities, in terms of Jy beam$^{-1}$, were comparable ($\sim$30 $\mu$Jy beam$^{-1}$). In two of the three epochs of the observations, the free-free emission peaks are located inside the 25 au ring. If the free-free emission is strong enough to produce many knots resolved in our Q-fiducial or Q-A images, there should be a higher chance for us to detect 40–48 GHz emission knots at the area of the cavity instead of the 25 au ring. The close association of the 40–48 GHz emission knots (detected at $\gtrsim$3–5-$\sigma$) with the 25 au ring argues against the probability that these 40–48 GHz emission knots are mostly originate from free-free emission. Free-free emission also cannot explain why the Q band, B-configuration and A-configuration observations that were widely separated in time (Table [\[tab:obs\]](#tab:obs)) consistently detected the brightest knot at the same location in the south. Some weak Q band knots may or may not be confused by free-free emission knots. If the other Q band knots were indeed confused by free-free emission, it would only strengthen the argument that the southern Q band knot was detected at a very high contrast and the 40–48 GHz intensity distribution is highly lopsided.

In addition, the free-free emission likely becomes optically thin at $>$10 GHz frequency (see Figure [3](#fig:sed_log)). In this case, the spectral indices of free-free emission will be in the range of $-$0.1–0 at 10–48 GHz (e.g., (cite: Anglada1998AJ....116.2953A)). Therefore, in the Q band (40–48 GHz), the intensity of the brightest free-free emission knot will have a $\lesssim$30 $\mu$Jy beam$^{-1}$ peak intensity (Figure [5](#fig:freefreeimages)). This is an upper limit of the peak intensity of one free-free emission knot, since the previous X and Ku band observations had coarse angular resolutions and thus might cover multiple free-free emission knots in one synthesized beam. This means that there can be at most one free-free emission knot that can be detected at $\lesssim$3-$\sigma$ in our Q-fiducial image. The other free-free emission sources should have lower intensities and thus cannot be detected in our Q-fiducial image. In other words, the $>$3-$\sigma$ sources in our Q-fiducial image more likely trace dust emission instead of free-free emission.

The estimates above do still overestimate the peak intensity of free-free emission in the Q-fiducial image. In only one of the three epochs of X- or Ku-band observations (i.e., the 12–18 GHz image taken on 2019 August 04, presented in the left panel of Figure [5](#fig:freefreeimages)), there was a free-free knot that is colocated with the Q band knot by chance. This chance colocation alone is not sufficient to justify that the Q band knot is mainly contributed by free-free emission. The intensity peak in the 12–18 GHz image taken on 2019 August 04 was only 26 $\mu$Jy beam$^{-1}$. Supposing that in one of our three epochs of Q-band, A-configuration observations, the brightest Q band knot in the south would have also been confused with the free-free emission at a similar flux density. After we combine the three epochs of Q-band, A-configuration observations, the flux density of the time-smeared free-free emission will become $\lesssim$9 $\mu$Jy beam$^{-1}$, which is lower than 1-$\sigma$ of our Q-fiducial image. In the Q-fidicual and Q-A images, the knots detected at $\gtrsim$5-$\sigma$ have 50–70 $\mu$Jy beam$^{-1}$, which can hardly be explained by the much weaker free-free emission reported in (cite: Terada2023ApJ...953..147T).

As a summary, we assess that locally, the Q band (40–48 GHz) intensity can be partly contributed by free-free emission. However, the free-free emission is unlikely to be strong enough to produce many knots that can be detected in our Q-fiducial image. Conversely, the $>$3-$\sigma$ detected 40–48 GHz knots in the Q-fiducial image that are closely associated with the brightest 225 GHz ring are most likely dust emission sources. At Q band, the contribution of free-free emission can be prominent locally (i.e., in one synthesized beam of our Q-fiducial image) but should be a lot less significant as compared to dust emission in the integrated SED (Figure [3](#fig:sed_log)).

# SED modeling using MCMC

Based on the ALMA 225 GHz observations and the complementary infrared data and assuming azimuthal asymmetry, (cite: Kudo2018ApJ...868L...5K) and (cite: Hashimoto2021ApJ...911....5H) have modeled the radial profiles of dust emission. However, they did not take into consideration (sub)millimeter dust self-scattering, which has been known to be able to change the results considerably and usually makes the models more degenerate ((cite: Liu2019ApJ...877L..22L)). Incorporating (sub)millimeter dust self-scattering, with the frequency coverage, angular resolution, S/N, and image fidelity achieved by the existing observations on DM Tau, our assessment is that a spatially resolved model would be too degenerated to provide any valid information. Therefore, we followed the approach of (cite: Liu2019ApJ...884...97L) to model the integrated flux densities (Figure [3](#fig:sed_log)) as a spatially unresolved source, using components of dust and free-free emission. Limited by the number of available independent measurements, we assumed that the physical properties within each component are uniform. For the sake of robustness, we were restricted to use the smallest possible number of components that can approximate the observed flux densities. In this case, the model parameters for each component need to be regarded as the averaged properties of some emission sources that have similar SED shapes; thus, it is not necessary to focus on the face value of the number of the components we use. For example, the knotty intensity distributions at 40–48 GHz (Figure [1](#fig:image)) signified multiple distinct dust concentrations, whereas we can only use one dust emission component to quantify their collective behavior. In addition, since we did not constrain the properties of the free-free emission using simultaneous observations at multiple frequencies, we could neither faithfully include more than one free-free emission components nor fit the individual epochs of $<$50 GHz observations by modeling with time-varying free-free emission (e.g., (cite: Liu2021ApJ...923..270L)).

## Two-dust-component model (fiducial)

The simplest model that can be made without contradicting the distinct morphology resolved at 225 GHz and 40–48 GHz (Figure [1](#fig:image)) is a model based on two dust components. Naturally, we would expect one of these two dust components to represent the bulk of the DM Tau ring; the other presents the 40–48 GHz emission knots to some extent. Similar to other recent case studies (e.g., (cite: Liu2021ApJ...923..270L; Hashimoto2022ApJ...941...66H; Hashimoto2023arXiv230811837H)), we found that it is still possible to address some qualitative properties of dust emission based on such a simplified SED model (see discussion below).

(cite: Terada2023ApJ...953..147T) has resolved that the 8–18 GHz flux densities are dominated by the time-varying free-free emission. In addition, the Q-all and Q-B images (Figure [4](#fig:moreimage); Section [3](#sec:results)) show that not only dust but also free-free emission significantly contributed to the flux density at 40–48 GHz (Table [\[tab:obs\]](#tab:obs)) which also explains why the 8–18 GHz and 40–48 GHz flux densities varied (Figure [3](#fig:sed_log)). Since the flux densities of the 8–18 GHz free-free emission had been well under 0.2 mJy, which are more than two orders of magnitude lower than the flux densities observed at $>$90 GHz frequencies. Therefore, in our models, we required the flux densities observed at $>$90 GHz to be well-fit by stationary dust emission. We required the $<$50 GHz flux densities to be roughly described by the emission of a free-free emission component and the stationary dust emission components. We realized the rough fitting at $<$50 GHz frequencies as follows:

- Setting the log likelihood to negative infinity when the model flux densities are (i) higher than the observed flux densities at 40–48 GHz in 2019, (ii) lower than the lowest observed 41–43 GHz flux density in 2012. This avoids the samplers that either do not produce significant dust emission or produce unrealistically high flux density at 40–48 GHz.

- Omitting considering the C and X bands non-detections, and artificially setting the RMS errors (1-$\sigma$) of the X and Ku bands measurements to be identical to the observed flux densities (Table [\[tab:obs\]](#tab:obs)). The rationale is that the flux densities at these frequency bands are dominated by free-free emission that the variability (i.e., uncertainty) of flux densities appeared comparable to the flux densities (Figure [3](#fig:sed_log)). In our cases, the RMS noise of the observations were well below the uncertainties of flux densities.

Chung et al. (submitted) reported that the 200–400 GHz spectral index of DM Tau is 2.11$^{+0.18}_{-0.17}$. The spectral index becomes much lower at $>$400 GHz frequencies (Figure [3](#fig:sed_log)). The directly measured spectral index between 400 GHz and 659 GHz was only $\sim$0.5. To explain these low spectral indices, at $>$200 GHz frequencies, the dominant emission source is likely an optically very thick dust component that the averaged dust temperature is below the Rayleigh-Jeans limit. In addition, it may require $a_{\mbox{\scriptsize max}}\lesssim$50 $\mu$m in this component, so that the anomalous reddening due to dust self-scattering can help suppress the spectral index at $\sim$700 GHz frequency ((cite: Liu2019ApJ...877L..22L)). We call this dust component the "small dust component" hereafter. There is a weak degeneracy between the $a_{\mbox{\scriptsize max}}$ and $T_{\mbox{\scriptsize dust}}$ of the small dust component, which can be alleviated once the solid angle of the $\sim$700 GHz emission is better constrained by higher angular resolution observations. Given that the dust temperature in the small dust component is constrained, and given that it is optically thick, its solid angle can be obtained by comparing the expected dust intensity ((cite: Birnstiel2018ApJ...869L..45B)) with the observed flux densities (Figures [3](#fig:sed_log)).

It turns out that the flux densities of DM Tau at 95–110 GHz are too high and the spectral index between 110–160 GHz is too low to be consistent with the emission of the small dust component alone. If we increase the $\Sigma_{\mbox{\scriptsize dust}}$ of the small dust component to make its flux density closer to what were observed at 95–160 GHz (Figure [3](#fig:sed_log); Table [\[table:model\]](#table:model)), it will also contribute to high emission at 40–48 GHz, which will make tension with the JVLA Q band measurements. A better way to simultaneously fit the flux densities at 95–700 GHz, is to additionally include another optically thicker grown dust component that the $a_{\mbox{\scriptsize max}}$ is around 0.3 mm. With $a_{\mbox{\scriptsize max}}\sim$0.3 mm, the SED of the grown dust component is anomalously reddened at $\sim$100 GHz due to dust self-scattering (c.f., (cite: Liu2019ApJ...877L..22L)). As expected, the MCMC fittings yielded distinct $a_{\mbox{\scriptsize max}}$ values for the two assumed dust components. In this case, the grown dust component can contribute to extra $\sim$100 GHz with a very low spectral index. The results of MCMC fittings are presented in linear scale in Figure [6](#fig:sed).

The co-existence of the small and grown dust components is consistent with the visual impression for Figure [1](#fig:image) (described in Sections [3](#sec:results) and [4.1](#sub:sed)). Since the small dust component needs to have a high optical depth to explain the low spectral index observed at 200–400 GHz, we found that we cannot make the grown dust component obscured by the small dust component in the line-of-sight. Otherwise, the attenuation will make it impossible for the grown dust component to contribute enough flux density at $\sim$95–160 GHz.

We optimized the free parameters in our model using the MCMC method, which was implemented with the `emcee` software package. Without simultaneous, multi-frequency observations, the electron temperature ($T_{\mbox{\scriptsize e}}$) in the free-free emission component cannot be constrained. We nominally fixed $T_{\mbox{\scriptsize e}}$ to 8,000 K which is typical for ionized gas. We found the initial guesses for the other free parameters interactively, which are summarized in Table [\[table:model\]](#table:model). Our prior assumptions for the free parameters are flat probability distributions in the linear domains. These flat probability distributions are centered at our initial guesses and are upper and lower bounded by 10 and 0.1 times the initial guesses. We used 250 samplers. Before running MCMC, the samplers were randomly perturbed from our initial guesses based on the prior probability model. We advanced the positions of the samplers for 5$\times$10$^{5}$ iterations, discarding the first 10$^{4}$ iterations as the burn-in steps.

## Single dust component model

Using a similar approach as what was introduced in Appendix Section [9.1](#appsub:twodust), we fit the observed SED assuming there is only a single dust emission component. The single-component model (Figure [7](#fig:sedSingle)) cannot reproduce the 90–700 GHz data as closely as the two-component model introduced in the previous section, in spite that the marginalized posterior probability distributions appear confined (Figure [9](#fig:cornerSingle)). It overestimated the flux densities at $\sim$150 GHz frequency and underestimated the flux densities at $\sim$100 GHz and $>$300 GHz frequencies.

In this case, due to the formal definition of the likelihood function (c.f., (cite: Foreman-Mackey2013PASP)), the MCMC fittings favor a solution that is modestly deviated from every data point, instead of a solution that fit most data points excellently but is largely deviated from a few data points. It is difficult to objectively determine which model is better. This may be regarded as an ambiguity (or systematic bias) related to the choices in assessing the goodness-of-fit. With another way of assessing the goodness-of-fit, the single-component model can potentially yield a very different results.

This ambiguity in the MCMC fitting can also be interpreted as our degree of freedom of choosing prior probability functions ((cite: Foreman-Mackey2013PASP)). For example, if we use a prior probability function to force the single dust component model to fit the $\sim$150 GHz data excellently, such a model will significantly underestimate the flux density at $\sim$100 GHz. Physically, the means that there is some excess of low-frequency emission, which may be related to the presence of the knotty structures resolved at 40–48 GHz.

![](dmtau_sed.pdf)

![](dmtau_sed_ModelSingle.pdf)

![](temp_mcmc_cornor.pdf)

![](temp_mcmc_cornor_ModelSingle.pdf)

</paper>

Write the methods card for this paper.