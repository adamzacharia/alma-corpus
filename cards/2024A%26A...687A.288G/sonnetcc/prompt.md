# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...687A.288G\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...687A.288G",
 "title": "Dark progenitors and massive descendants: A first ALMA perspective of radio-selected near-IR-dark galaxies in the COSMOS field",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Gentile, Fabrizio",
 "n_authors": 22,
 "arxiv_id": "2402.05994",
 "doi": "10.1051/0004-6361/202348623",
 "alma_projects_linked_by_archive": [
  "2021.1.01467.S"
 ]
}
```

Paper text:
<paper>
# Dark progenitors and massive descendants:\
A first ALMA perspective on Radio-Selected NIRdark galaxies in the COSMOS field

We present the first spectroscopic ALMA follow-up for a pilot sample of nine Radio-Selected NIRdark galaxies in the COSMOS field. These sources were initially selected as radio-detected sources ($S_{\rm 3GHz}>12.65\mu$Jy) lacking an optical/NIR counterpart in the COSMOS2015 catalog ($Ks\gtrsim24.7$ mag), with just three of them subsequently detected in the deeper COSMOS2020. Several studies highlighted how this selection could provide a population of highly dust-obscured, massive and star-bursting galaxies. With these new ALMA observations, we assess the spectroscopic redshifts of this pilot sample of sources and improve the quality of the physical properties estimated through SED-fitting. Moreover, we measure the quantity of molecular gas present inside these galaxies and forecast their potential evolutionary path, finding that the RS-NIRdark galaxies could represent a likely population of high-*z* progenitors of the massive and passive galaxies discovered at $z\sim3$. Finally, we present some initial constraints on the kinematics of the ISM within the analysed galaxies, reporting a high fraction ($\sim55\%$) of double-peaked lines that can be interpreted as the signature of a rotating structure in our targets or with the presence of major mergers in our sample. Our results presented in this paper showcase the scientific potential of (sub)mm observations for this elusive population of galaxies and highlight the potential contribution of these sources in the evolution of the massive and passive galaxies at high-*z*.

# Introduction

One of the biggest puzzles of modern astronomy concerns the recent discovery of a significant population of massive ($M_\star\sim10^{11}M_\odot$) and passive (sSFR$<10^{-11}$ yr$^{-1}$) galaxies already in place at $z\sim3$ (see some examples in (cite: Straatman_14; Schreiber_18; Valentino_20)).

This result challenges our galaxy evolution models for two main reasons. On the one hand, these galaxies assembled most of their stellar mass at $z>3$, in a period of the cosmic time when – according to studies based at optical/NIR wavelengths (see (cite: Madau_14) and references therein) – the cosmic Star Formation Rate Density (SFRD; i.e. the average amount of stellar mass created in the Universe per each year and each comoving Mpc$^3$) was at least one order of magnitude lower than at the so-called *cosmic noon* ($z\sim3$). On the other hand, looking at higher redshifts, we should detect a significant population of massive and star-forming galaxies on the way to quench their star-formation (the “*progenitors*” of these massive and passive galaxies; see e.g. (cite: Valentino_20)). However, when looking at the galaxies selected at these redshifts in the optical/NIR regimes (mostly Lyman Break Galaxies; LBGs, see (cite: Giavalisco_02) and references therein), we see a population of galaxies with stellar masses and star formation rates too low to be likely progenitors of these sources. In addition, the number density of LBGs at $z>3$ is generally found to be one or two orders of magnitude lower than the massive and passive galaxies at $z=3$ (cite: Stark_09; Toft_14; Valentino_20).

Before invoking a dramatic change in our galaxy evolution models, we must exclude the presence of any bias in our samples of high-*z* galaxies. A possible issue – for instance – could reside in the wavelength in which we select these sources. In the last decades, several studies (cite: Smail_99; Smail_02; Frayer_04; Simpson_14; Franco_18; Wang_19; Gruppioni_20; Smail_21; Talia_21; Manning_22; Enia_22; Behiri_23) unveiled the existence of a significant population of "dark" galaxies constantly missed by optical/NIR surveys: the so-called Dusty Star Forming Galaxies (DSFGs; see e.g. the review by (cite: casey_14)). These sources are characterized by significant amounts of dust in their interior, making them extremely faint (or even undetected) at short wavelengths.

Several studies selecting these sources at longer wavelengths (i.e. where the effect of dust is negligible or where we can take advantage of its bright thermal emission, mainly in the FIR/(sub)mm), assessed how they could represent a population of massive and star-forming galaxies, with estimated number densities comparable with those reported for the massive and passive galaxies at $z\sim3$ (cite: Toft_14; Valentino_20; Talia_21; Behiri_23). Moreover, the inclusion of these sources in the cosmic census of high-*z* galaxies could be significant enough to change the behavior of the cosmic SFRD at $z>3$ (cite: RowanRobinson_16; Gruppioni_20; Talia_21; Behiri_23; Traina_23).

The main drawback of these studies, when performed at FIR/sub(mm) wavelengths, resides in the size of the analysed samples. When employing old-generation instruments such as the SCUBA camera equipped on the *James Clerk Maxwell Telescope* (cite: Smail_97; Hughes_98; Dunlop_04) or the PACS and SPIRE cameras on the *Herschel Space Observatory* (cite: Gruppioni_13; Burgarella_13), the low sensitivity of these instruments biases these samples towards the most extreme objects. In addition, their coarse resolution makes it difficult to associate the right multi-wavelength counterpart to the FIR emission without a high-resolution follow-up (cite: Simpson_19; Simpson_20; Stach_19; Dudzevicute_21).

All these issues could be solved, in principle, with the employment of state-of-the-art facilities observing at these wavelengths such as the *Atacama Large (sub)Millimeter Array* (ALMA) or the *Northern Extended Millimeter Array* (NOEMA), with higher sensitivity and better spatial resolution. Nevertheless, these instruments are not designed to perform wide blind surveys: their small field of view makes incredibly time-consuming observing statistically significant volumes of the Universe (cite: Dunlop_17; Franco_18; Casey_21).

A possible solution to all these problems could reside in a radio selection. Since radio photons can be generated by free-free emission in HII regions and synchrotron emission from relativistic electrons accelerated in supernovae remnants, they represent a dust unbiased tracer of star formation (see e.g. (cite: Kennicutt_12) and references therein).

As shown for the first time by (cite: Chapman_01), the selection of faint radio sources lacking an optical/NIR counterpart can provide a sample of likely DSFGs (cite: Chapman_02; Chapman_04), but with a selection taking advantage of the large FOVs and optimal spatial resolution of modern radio interferometers. Moreover, the high sensitivity reached by deep radio surveys can unveil samples of galaxies with less-extreme properties than what is commonly obtained through FIR/(sub)mm selections (see e.g. (cite: Chapman_02; Chapman_04; Talia_21; Behiri_23; Gentile_24)).

Nevertheless, the drawback of this radio selection is represented by the possible contribution by AGN, since nuclear activity can also produce radio emission. This issue can be partly solved with a multi-wavelength approach, by focusing on extra-galactic fields where a broad photometric coverage is available and – therefore – where one can look for the characteristic signatures of AGN at other frequencies than radio (see e.g. the discussions in (cite: Enia_22) and (cite: Gentile_24); see also the review by (cite: Hickox_18) and references therein).

Focusing on deep radio surveys and requiring the lack of counterparts in deeper NIR surveys (than what initially employed by (cite: Chapman_01); see e.g. (cite: Talia_21), (cite: Enia_22), (cite: Behiri_23), (cite: VanDerVlugt_23), and (cite: Gentile_24)), we can collect the so-called Radio-Selected NIRdark galaxies[^1] (RS-NIRdark galaxies hereafter).

The first studies analyzing these sources ((cite: Talia_21; Enia_22; Behiri_23; Gentile_24)) reported a series of interesting results:

- The RS-NIRdark galaxies represent a population of highly dust-obscured ($A_{\rm v}\sim 4$ mag), massive ($M_\star\sim10^{11}M_\odot$) and star-forming (SFR$\sim 500$ M$_\odot$ yr$^{-1}$) galaxies. The bulk of the population is located at $z\sim3$ and there is a significant tail of high-*z* sources at $z>4.5$.

- When compared with other galaxies in the same redshift ranges, the RS-NIRdark galaxies always lie above the main sequence of star-forming galaxies, with nearly half of them in the starburst regime.

- Their number density at $z>3.5$ (not corrected for incompleteness or for the expected duty cycle) is higher than n=($3.3\pm0.9)\times10^{-6}$ Mpc$^{-3}$, just in moderate tension with that reported by (cite: Straatman_14), (cite: Schreiber_18), and (cite: Valentino_20) for the massive and passive galaxies at $z\sim3$.

- Their contribution to the cosmic SFRD at $z>4.5$ could be as high as 20-40% of that obtained only considering optically/NIR selected galaxies.

If, on the one side, these results increase the scientific potential of the RS-NIRdark galaxies, they make new questions to arise. Firstly, all these results are based on photometric redshifts and SED-fitting. Since the photometry of these sources is mostly constrained by upper limits in the optical/NIR regimes, a spectroscopic confirmation of the redshift is necessary to decrease the degeneracies affecting the physical properties estimated through this procedure. Secondly, if the number density of the RS-NIRdark galaxies is compatible with the passive galaxies at $z\sim3$, we need to constrain their evolutionary path to establish a possible relation between the progenitors and the descendants. Finally, we must explain their location in the SFR-stellar mass plane and unveil the physical processes taking place in their ISM responsible for such an intense star formation.

Clearly, most of these questions cannot be addressed just relying on the existing photometry already analysed in the previous studies on these sources: we need to collect more data. Given the elusive nature of the RS-NIRdark galaxies, our choice is limited to the new facilities observing at longer wavelengths: ALMA, NOEMA, and the *James Webb Space Telescope* (JWST). As noted by several previous studies, (sub)mm observations can be incredibly useful in assessing the true nature of "dark" galaxies selected at other wavelengths, allowing us to constrain their dust and gas content (cite: Chapman_01; Chapman_02; Chapman_04) as well as prove their obscured star formation (cite: Wang_19).

This paper is focused on the first ALMA follow-up of a pilot sample of nine RS-NIRdark galaxies selected in the COSMOS field by (cite: Talia_21) and analysed by (cite: Behiri_23) and (cite: Gentile_24). The first results involving an accepted NOEMA follow-up and the first JWST data obtained thanks to the COSMOS-Web survey (cite: Casey_22) will be described in following papers (Gentile et al., in prep.).

This study follows this structure. In Section [2](#sec:data) we introduce our targets, the ancillary photometry already available for them, and the new ALMA observations. In Section [3](#sec:methods), we describe the analysis of the ALMA cubes, the identification of any bright emission line in our targets, and our modeling of the spectroscopic redshifts. Moreover, we present some initial insights on the ISM kinematics and derive the physical properties of our pilot sample of galaxies through SED-fitting. Then, in Section [4](#sec:results), we discuss our results, estimate the gas mass within our sources, and forecast a possible evolutionary path for them. Finally, we draw our conclusions in Section [5](#sec:conclusions). Throughout this paper, we assume a (cite: Chabrier_03) Initial Mass Function (IMF) and a flat $\Lambda$CDM cosmology with $[\Omega_m,\Omega_\Lambda,h]=[0.3,0.7,0.7]$.

# Data

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | ID (Talia+21) | RA | Dec | C20 | Ks | IRAC Ch 2 |
|  |  | \[*hh:mm:ss*\] | \[*dd:mm:ss*\] |  | \[mag\] | \[mag\] |
| RSN-41 | COSMOSVLA3-49 | 09:58:17.869 | +02:30:38.305 | \- | $>25.7$ | $22.47\pm0.04$ |
| RSN-84 | COSMOSVLA3-106 | 09:58:43.440 | +02:45:18.135 | \- | $>25.8$ | $23.21\pm0.07$ |
| RSN-121 | COSMOSVLA3-152 | 09:59:14.234 | +02:35:26.432 |  | $25.0\pm0.3$ | $22.54\pm0.02$ |
| RSN-182 | COSMOSVLA3-225 | 09:59:46.699 | +02:48:41.215 | \- | $>25.0$ | $23.29\pm0.05$ |
| RSN-235 | COSMOSVLA3-291 | 10:00:09.550 | +01:42:50.834 | \- | $>26.2$ | $23.40\pm0.04$ |
| RSN-247 | COSMOSVLA3-308 | 10:00:23.785 | +01:41:59.273 |  | $24.9\pm0.3$ | $23.02\pm0.03$ |
| RSN-298 | COSMOSVLA3-370 | 10:00:57.970 | +01:38:26.078 | \- | $>25.7$ | $23.43\pm0.04$ |
| RSN-361 | COSMOSVLA3-442 | 10:01:28.390 | +02:21:27.857 |  | $25.0\pm0.3$ | $23.84\pm0.07$ |
| RSN-456 | COSMOSVLA3-576 | 10:02:48.219 | +02:24:30.629 | \- | $>25.7$ | $22.97\pm0.06$ |

## ALMA observations and data reduction

The main focus of this study is on the observations carried out by ALMA during its cycle 8 as a part of the observing program 2021.1.01467.S (PI: M. Talia). The required observations consisted of a spectroscopic follow-up at mm wavelengths for a pilot sample of 9 RS-NIRdark galaxies (Table [\[tab:coords\]](#tab:coords)). These sources were initially selected in the COSMOS field by (cite: Talia_21) among those located in the high-*z* tail of the redshift distribution (photo-$z>4.5$), with the best-sampled SEDs (i.e., with at least one significant detection at $S/N>3$ at FIR/(sub)mm wavelengths), and with a reliable SED-fitting. Following the selection by (cite: Talia_21), these objects were part of a sample of 476 galaxies robustly detected ($S_{\rm 3GHz}>12.65 \mu$Jy; $S/N>5.5$) in the catalog of the VLA-COSMOS 3GHz Large Project (cite: Smolcic_17) and lacking an optical/NIR counterpart in the COSMOS2015 catalog (cite: Laigle_16), i.e. the most recent NIR-selected catalog of the COSMOS field at the time of that study. As highlighted by (cite: Gentile_24), the public release of the deeper COSMOS2020 catalog ($\sim 1$ mag deeper in the $Ks$ band and with the detection operated in a more complete detection image; see (cite: Weaver_22)), allowed us to associate an optical/NIR counterpart for $\sim150$ sources analysed in (cite: Talia_21). The targets with a counterpart in the COSMOS2020 catalog are highlighted with an appropriate flag in Table [\[tab:coords\]](#tab:coords).[^2]

The main scientific goal of the observing program was to assess the spectroscopic redshifts of the nine targets. Therefore, we requested a spectral setup covering the whole band 3 of ALMA (i.e., all the frequencies between $\sim$84 and $\sim$115 GHz). This setup, analogous to those employed in similar studies in the current literature (see e.g. (cite: Walter_16; Jin_19; Jin_22; Cox_23)), ensures that at least one line among the CO and \[CI\] transitions should be detected for almost all the redshifts in the range $0<z<8$. Moreover, this spectral scan provides the possible detection of two lines for most of the redshifts higher than 3, allowing an unambiguous determination of the spec-*z* (see Figure [1](#fig:setup)). To cover the whole band 3 with ALMA, five settings were required. By estimating the integrated fluxes of the expected CO/\[CI\] lines observable in our setup, we requested a sensitivity of 0.32 mJy/beam per stacked channel for a total of 27h of ALMA observing time. The observations were performed in service mode between March and September 2022, when the interferometer was in its C-4/C-3 configurations (i.e. with baselines between 15 and 500/784 m, an expected beam size of 1.4”/0.92” and a maximum recoverable scale of 16.2”/11.2”). The calibration was performed by the Alma Regional Center through the ALMA standard pipeline. Once obtained the calibrated Measurement Sets, we merged the multiple observations through the *Common Astronomy Software Applications* package (CASA v6.1; (cite: CASA_22)). Finally, to achieve the sensitivity originally requested in the proposal, we re-sampled the native spectral resolution to obtain $\sim0.02$ GHz channels ($\sim$ 50 km/s at the reference frequency of 100 GHz). After a first cleaning (performed with the "TCLEAN" task and employing natural weighting to maximize the sensitivity; see (cite: Hogbom_74)), we verified that the median rms across the stacked channels was 0.2 mJy/beam (i.e. slightly better than what requested in the original proposal), increasing towards higher frequencies due to the decreasing transmissivity of the ALMA band 3 up to 0.4 mJy/beam. The various settings have some overlap in frequency, therefore those (overlapping) ranges have a better rms. The beam shape is quite uniform across the channels: it can be modeled as an ellipse with a Half Power Beam Width equal to 1.45” x 1.31” and a Position Angle of $\sim -70^\circ$.

![](Setup.png)

## Ancillary data

Since the nine galaxies analyzed in this work are located in the Cosmic Evolution Survey field (COSMOS; one of the most famous extra-galactic fields in modern astronomy, observed by most of the main telescopes in the last decades, see, e.g. (cite: Scoville_07; Koekemoer_07; Laigle_16; Civano_16; Weaver_22; Moneti_22; Casey_22)), they have an almost complete multi-wavelength coverage from the radio to the X-rays. Most of the photometry for these sources is described in (cite: Gentile_24) and briefly summarized here. The fluxes in the optical/NIR/MIR regimes are extracted from the scientific maps employed by (cite: Weaver_22) to build the COSMOS2020 catalog. These maps were produced by the HSC@Subaru, VIRCAM@VISTA, and IRAC@Spitzer instruments and telescope. (cite: Gentile_24) analysed these maps through the Photometry Extractor for Blended Objects (PHOEBO). This pipeline implements a modified version of the algorithm introduced by (cite: Labbe_06) and already employed in several studies (see e.g. (cite: Endsley_21; Whitler_22)), but optimized for the deblending of RS-NIRdark galaxies. It mainly relies on a double prior coming from the radio and NIR maps, employing a PSF-matching between the high-resolution maps (radio and NIR) and the low-resolution ones (mainly those produced by IRAC) to deblend the different sources and extract forced photometry. Further details on the algorithm and its validation are presented in (cite: Gentile_24), while the algorithm is freely available in a GitHub repository[^3]. Additional photometry at longer wavelengths is retrieved through cross-matching with pre-existing catalogs. More in detail, the photometry at FIR wavelengths is obtained from the SuperDeblended catalog (v20201010; (cite: Jin_18)), containing deblended photometry from MIPS@Spitzer, PACS/SPIRE@Herschel, and SCUBA-2@JCMT instruments and telescopes. The fluxes at (sub)mm wavelengths are retrieved through cross-matching with the catalog from the *Automated Mining of the ALMA Archive in the COSMOS Field* (A3COSMOS) survey (v.20200310; (cite: Liu_19)). Finally, radio fluxes at 1.28, 1.4, and 3 GHz are obtained from the catalogs of the COSMOS-VLA large program (cite: Schinnerer_10; Smolcic_17) and of the MIGHTEE Early Science Data Release (cite: Jarvis_16; Heywood_22). A shallow X-ray coverage is also available for the COSMOS field thanks to the public catalogs by (cite: Elvis_09) and (cite: Civano_16). This latter information was employed in (cite: Gentile_24) to ensure that none of the sources analyzed in this work are hosting a powerful and un-obscured AGN ($L_{\rm x}>10^{42}$ erg s$^{-1}$).

# Analysis of the datacubes

## Continuum images

The first analysis performed on the calibrated MSs consists in the production of a continuum image, useful to study the properties of dust in our targets. This procedure is performed through the CASA task "TCLEAN" in "multi-frequency synthesis" (mfs) mode, after masking any bright line that could contaminate the continuum emission. To maximize the sensitivity of the cleaned image, we employ a natural weighting throughout this procedure. To estimate the continuum fluxes, we perform an aperture photometry with CARTA (cite: CARTA_21), by employing an aperture corresponding to the $2\sigma$ contour of the continuum image. We verify that this estimate is compatible – within the estimated uncertainties – with the flux estimated through a 2D profile-fitting performed with the CASA task "IMFIT". The results of this procedure are reported in Table [1](#tab:cont). We obtain that 6 out of 9 targets are robustly detected (S/N$>$3) in the continuum images.

|     |                 |                    |                         |
|:---:|:---------------:|:------------------:|:-----------------------:|
| ID  |  $S_{3\rm mm}$  | $S_{850\rm \mu m}$ |       Other flux        |
|     |     \[mJy\]     |      \[mJy\]       |         \[mJy\]         |
| 41  | $(0.04\pm0.01)$ |   $(2.9\pm0.3)$    |           \-            |
| 84  | $(0.11\pm0.03)$ |   ${\bf(7\pm2)}$   | 0.873 mm: $(4.6\pm0.8)$ |
| 121 | $(0.09\pm0.03)$ |   $(3.9\pm0.4)$    |           \-            |
| 182 | $(0.14\pm0.02)$ |  ${\bf (5\pm1)}$   |           \-            |
| 235 | $(0.18\pm0.04)$ |  ${\bf (5\pm1)}$   |           \-            |
| 247 | $(0.09\pm0.01)$ |  ${\bf (5\pm1)}$   |           \-            |
| 298 |    $< 0.036$    |   $(3.3\pm0.3)$    |           \-            |
| 361 |    $< 0.036$    |   $(3.3\pm0.4)$    | 1.249 mm: $(2.0\pm0.4)$ |
| 456 |    $< 0.036$    |   $(1.9\pm0.2)$    |           \-            |

: Continuum fluxes for the RS-NIRdark galaxies analysed in this work. The values at $\lambda=3$ mm are obtained through aperture photometry on the continuum images obtained in Section [3.1](#sec:continuum). We consider a source as robustly detected with a S/N$>$3, therefore we report a $3\sigma$ upper limit for the undetected targets. The value at 850 $\mu$m are retrieved from the SuperDeblended catalog (cite: Jin_18) for the sources at S/N\>3 (reported in bold), while for the other galaxies, we report the best-fitting flux at 850 $\mu$m computed with CIGALE. For two sources, we also report an additional (sub)mm flux measured with ALMA through cross-matching with the A3COSMOS catalog (cite: Liu_19).

![image](49_cont.png) ![image](106_cont.png) ![image](152_cont.png) ![image](225_cont.png) ![image](291_cont.png)\
![image](308_cont.png) ![image](370_cont.png) ![image](442_cont.png) ![image](576_cont.png)

## Line identification and reliability

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | Line 1 | Freq | FWHM | SNR | Line 2 | Freq | SNR | $z_{\rm spec}$ | $z_{\rm phot}$ (G23) | $z_{\rm phot}$ (T21) |
|  |  | (GHz) | (km/s) |  |  | (GHz) |  |  |  |  |
| RSN-84 | CO(4-3) | 102.05 | $584\pm96$ | 11.23 | \[CI\](1-0) | 108.91 | 5.39 | 3.518 | $4.5\pm0.3$ | $5.2\pm0.9$ |
| RSN-121 | CO(4-3) | 106.64 | $683\pm77$ | 12.26 | \[CI\](1-0) | 113.74 | 4.89 | 3.323 | $3.3\pm0.2$ | $5.2\pm0.1$ |
| RSN-235 | CO(5-4) | 101.95 | $481\pm63$ | 13.24 | \[CI\](1-0) | 87.07 | 5.68 | 4.652 | $4.5\pm0.5$ | $5.1\pm0.5$ |
| RSN-298 | CO(4-3) | 89.53 | $408\pm93$ | 8.44 | CO(5-4) | 111.94 | 4.93 | 4.150 | $3.5\pm0.3$ | $5.4\pm0.8$ |
| RSN-361 | CO(5-4) | 103.19 | $349\pm81$ | 6.30 | \[CI\](1-0)$^{(a)}$ | 88.13 | 3.47 | 4.585 | $4.3\pm0.5$ | $5.1\pm0.9$ |
| RSN-41 | CO(3-2) | 91.50 | $627\pm60$ | 12.18 | \- | \- | \- | *2.779* | $3.0\pm0.2$ | $6.9\pm0.1$ |
| RSN-182 | CO(5-4) | 100.31 | $441\pm89$ | 9.59 | \- | \- | \- | *4.745* | $4.6\pm0.2$ | $5.9\pm0.9$ |
| RSN-247 | CO(3-2) | 88.02 | $905\pm285$ | 6.79 | \- | \- | \- | *2.929* | $3.4\pm0.4$ | $5.0\pm0.1$ |
| RSN-456 | CO(3-2) | 86.74 | $497\pm71$ | 7.22 | \- | \- | \- | *2.987* | $2.8\pm0.2$ | $6.8\pm0.7$ |

$^{(a)}$ Tentative second line, see the discussion in Section [3.3](#sec:redshifts).

The presence of emission lines inside our datacubes is unveiled through a line-finding algorithm analogous to those employed in several previous studies (cite: Daddi_15; Walter_16; Coogan_18; Puglisi_19; Jin_19; Jin_22) and summarized here:

1.  We obtain a continuum-subtracted MS for each source through the CASA task "UVCONTSUB". We model the continuum as a first-grade polynomial whose slope is fitted on the whole frequency range covered by our observations once masked any bright line that could contaminate the continuum estimation.

2.  We compute the 0th moment of the continuum-subtracted MS through the CASA task "IMMOMENTS" to unveil the spatial region of the datacube with a significant line emission. In all the analyzed targets, the 0th moment significantly overlaps with the radio emission at 3GHz visible in the maps by (cite: Smolcic_17). This result ensures that the mm emission can be safely associated to our targets.

3.  We perform the imaging of the continuum-subtracted visibilities through the CASA task "TCLEAN". We employ a natural weighting to maximize the cleaned images’ sensitivity.

4.  We convolve the cleaned datacube with a series of boxcar kernels with variable widths between 1 and 13 channels (i.e., between 60 and 780 km/s at a representative frequency of 100 GHz).

5.  For each convolved datacube, we produce an S/N cube by dividing each channel by the relative rms. This quantity is computed through a sigma clipping performed on the inner region of the primary beam to avoid possible biases due to the presence of significant emission and higher noise far from the phase center.

6.  Finally, we extract a S/N spectrum for each convolved datacube through the Python library INTERFEROPY (cite: interferopy). We employ as extracting region the 2$\sigma$ contour of the 0th moment map obtained in step number 2.

![image](106_CO43.png) ![image](106_CI10.png)\
![image](152_CO43.png) ![image](152_CI10.png)\
![image](225_CO54.png) ![image](291_CO54.png) ![image](291_CI10.png)

![image](370_CO43.png) ![image](370_CO54.png)\
![image](442_CO54.png) ![image](442_CI10.png)\
![image](49_CO32.png) ![image](308_CO32.png) ![image](576_CO32.png)

This procedure results in a list of possible lines, with the related S/N and Full Width Zero Intensity (FWZI)[^4]. However, given the nature of the noise in interferometric data, it is generally needed to establish the reliability of each line $R=1-p$ (where $p$ is the probability of a spurious detection). Since several methods exist to compute this quantity for interferometric data, in this study we follow two complementary approaches.

- Following (cite: Jin_19), we compute the spurious probability of each line as $$\begin{equation}
      \centering
      \label{eq:jin}
          p({\rm S/N})=1-R_0({\rm S/N})^{N_{\rm Eff}}
      
  \end{equation}$$

  where $R_0$ is the reliability expected in the Gaussian case (and – therefore – approaching the unity towards higher S/N) and $N_{\rm Eff}$ is the "number of effective searches". Through an extensive series of simulations, (cite: Jin_19) estimated that this quantity can be approximated through the relation $$\begin{equation}
      \centering
          N_{\rm Eff}\sim10\frac{N_{\rm total, ch}}{N_{\rm line,ch}}N_{\rm Line,ch}^{0.58}\log\frac{N^{\rm max}_{\rm line,ch}}{N^{\rm min}_{\rm line,ch}}
      
  \end{equation}$$ where $N_{\rm total, ch}$ is the total number of channels inside the datacube, $N_{\rm line, ch}$ is the number of channels in which the line is detected, and ${N^{\rm max}_{\rm line,ch}}$ and ${N^{\rm min}_{\rm line,ch}}$ are, respectively, the minimum and maximum width of the boxcar kernels employed during the line search (see point 4). While this approach is based on simulations and is not dependent on the properties of the actual cube, it relies on the hypothesis that the noise at the phase center of our observations is approximately Gaussian (reasonable assumption given the almost complete $uv$ coverage generally produced by ALMA).

- Following (cite: Walter_16), we compute the reliability of each line through the FINDCLUMPS algorithm as implemented in the Python library INTERFEROPY. This method estimates the reliability as $$\begin{equation}
      \centering
          R({\rm S/N})=1-\frac{N_P ({\rm S/N})}{N_N ({\rm S/N})}
      
  \end{equation}$$ where $N_P$ and $N_N$ are, respectively, the number of positive and negative peaks in the whole datacube in a given S/N bin. This approach does not rely on any assumption about nature of the noise in our datacubes, but it could be biased by the small statistics affecting the number of pixels in our observations.

The procedures described here allowed us to identify in all the targets at least one bright (S/N$>6$) line (see Table [\[tab:lines\]](#tab:lines)). Given the high S/N of all the detected lines, we can estimate for all of them a spurious probability lower than $10^{-6}$ following (cite: Jin_19). Similarly, since they have a S/N higher than every negative peak in the analysed datacubes, we can estimate for all of them a 100% reliability following (cite: Walter_16). By producing the 0th moment of each (continuum-subtracted) line through the CASA task "IMMOMENTS", we obtain the maps reported in the insets in Figure [3](#fig:spectra_lines). Moreover, by performing an aperture photometry with CARTA on the 2$\sigma$ contour of these maps, we measure the integrated line fluxes reported in Table [2](#tab:line_flux).

## Redshift estimation

Once detected the different lines present in our datacubes, we estimate the spectroscopic redshift of our sources following (cite: Jin_19). For doing so, we consider the line with the highest S/N in each cube (i.e. that with the highest reliability) and model it as each of the CO transitions that should be visible in the redshift range $0<z<8$ (see Figure [1](#fig:setup)). For all the redshifts higher than 3 –- for most of which a second line is expected – we search for a detection at the expected frequency in the line list produced in Section [3.2](#sec:lines). Through the S/N of each detection, we compute the reliability of the tentative second lines through Equation [\[eq:jin\]](#eq:jin). It is crucial to underline how – for the second line – the number of effective searches ($N_{\rm Eff}$) is much lower than those employed in Section [3.2](#sec:lines). In this case, we are not performing an active search of the line throughout the whole spectrum, but we are only analyzing the frequencies allowed by the first line. Therefore, the $N_{\rm Eff}$ just corresponds to the number of possible CO transitions with which we can model the first line. For each redshift, we can finally estimate a joint spurious probability given by the product between the spurious probability of the first and the second line. The redshift with the highest reliability is assumed to be the spectroscopic redshift of our sources.

This approach is sufficient for all the galaxies in which two lines are robustly detected. However, for four of our targets, no second line is detected at a sufficiently high S/N in the analysed spectra. For these galaxies, we assess the redshift taking advantage of the additional information coming from the photometry. More in detail, once added the continuum datapoint at 3 mm (Table [1](#tab:cont)) to the photometry presented in Section [2.2](#sec:ancillary) (or an upper limit for the galaxies undetected in the continuum images), we perform a SED-fitting through the code CIGALE ((cite: Boquien_19); see more details on the employed models in Section [3.5](#sec:SEDFitting)), fixing the redshift to all the spec-*z* allowed by the single line identified in the spectrum. Hence, we assume as the final value for the spec-*z* the redshift with the best agreement between the modeled SED and the photometry (i.e. that with the lowest value of the $\chi^2$). Remarkably, for one of the remaining galaxies (namely, RSN-182), the redshifts estimated through this procedure falls in a small range of frequency at $z\sim4.7$ where a single line (CO(5-4)) is expected. Similarly, three targets (namely, RSN-41, RSN-247, and RSN-456) have a redshift lower than three, where – according to our spectral setup – no second line is expected to be observed. We also report a "tentative" second line in RSN-361 at $\nu=88.13$ GHz. Even though this detection falls exactly where the \[CI\](1-0) line would be expected for a galaxy at $z=4.585$, the low $S/N\sim3.5$ and the spatial offset with the robustly detected line at $\nu=103.19$ GHz make the line identification unsure. Finally, we underline that continuum image (see Figure [2](#fig:continuum)) shows a quite irregular morphology for this source, suggesting the possible presence of a major merger (that could explain the spatial offset of the tentative \[CI\](1-0) line). It is important to notice how these redshifts based on a single detected line are clearly more uncertain than those relying on a double detection. We cannot exclude that a fainter line (e.g. a \[CI\](1-0)) would be observed in our frequency range with deeper observations. For instance, given the redshift estimated through CO(4-3) and CO(5-4) in RSN-298, we would expect a \[CI\](1-0) line at $\nu=95.57$ GHz in that source, even though nothing is detected at that frequency at S/N larger than 1$\sigma$. For the other galaxies where a single line is detected, however, these solutions would be disfavored by the photometry.

![](Mom1_Tot.png)

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | log(M$_\star$) | log(SFR) | log(L$_{\rm IR}$) | A$_{\rm V}$ | log(M$^{CO}_{\rm H_2}$) | log(M$^{[CI]}_{\rm H_2}$) | $\tau_{\rm D}$$^{(a)}$ |
|  | \[M$_\odot$\] | \[M$_\odot$ yr$^{-1}$\] | \[L$_\odot$\] | \[mag\] | \[M$_\odot$\] | \[M$_\odot$\] | \[Myr\] |
| RSN-41 | $11.0\pm0.1$ | $2.72\pm0.06$ | $12.56\pm0.06$ | $4.9\pm0.2$ | $11.10\pm0.06$ | \- | $242\pm50$ |
| RSN-84 | $11.0\pm0.1$ | $2.76\pm0.03$ | $12.57\pm0.03$ | $4.8\pm0.2$ | $10.86\pm0.08$ | $11.17\pm0.06$ | $258\pm53$ |
| RSN-121 | $11.0\pm0.1$ | $2.65\pm0.06$ | $12.47\pm0.06$ | $4.2\pm0.2$ | $11.11\pm0.07$ | $11.01\pm0.07$ | $229\pm60$ |
| RSN-182 | $11.1\pm0.1$ | $2.92\pm0.03$ | $12.72\pm0.03$ | $3.8\pm0.2$ | $11.02\pm0.08$ | \- | $126\pm27$ |
| RSN-235 | $11.3\pm0.1$ | $3.04\pm0.03$ | $12.83\pm0.04$ | $4.5\pm0.2$ | $11.07\pm0.08$ | $10.96\pm0.08$ | $83\pm18$ |
| RSN-247 | $10.7\pm0.2$ | $2.57\pm0.04$ | $12.46\pm0.04$ | $4.6\pm0.4$ | $10.71\pm0.09$ | \- | $140\pm31$ |
| RSN-298 | $11.0\pm0.1$ | $2.69\pm0.06$ | $12.58\pm0.06$ | $4.2\pm0.3$ | $10.81\pm0.08$ | \- | $132\pm30$ |
| RSN-361 | $10.8\pm0.3$ | $2.79\pm0.03$ | $12.61\pm0.03$ | $3.9\pm0.6$ | $10.7\pm0.1$ | $11.06\pm0.06$ | $186\pm34$ |
| RSN-456 | $10.8\pm0.2$ | $2.41\pm0.07$ | $12.37\pm0.07$ | $4.6\pm0.3$ | $10.93\pm0.06$ | \- | $288\pm63$ |
| Median$^{(b)}$ | $11.0\pm0.1$ | $2.6\pm0.1$ | $12.6\pm0.1$ | $4.5\pm0.4$ | $10.9\pm0.2$ | $11.03\pm0.07$ | $263\pm86$ |
| G24$^{(b)}$ | $11.0\pm0.4$ | $2.8\pm0.4$ | $12.6\pm0.4$ | $3.9\pm0.3$ | $-$ | $-$ | $-$ |

$^{(a)}$ Estimated from the $M^{[CI]}_{H_2}$ when available.

$^{(b)}$ The uncertainties on the median quantities are reported as half the interval between the 84th and the 16th percentile

## Initial insights on the ISM kinematics

As shown in Table [\[tab:lines\]](#tab:lines), most of our targets have quite broad lines (FWHMs of several hundreds of km/s). This result is familiar for what concerns high-*z* DSFGs and ULIRGs in general (see e.g. (cite: Jin_19; Jin_22; Cox_23)), and it is generally explained through an ISM much more turbulent than what is commonly observed in local galaxies. In this study – however – we can perform a more detailed analysis on some targets, since the FWHM of the lines is much larger than the spectral resolution requested in our observation. This property allows us to infer some initial insights into the ISM kinematics inside our galaxies. As visible in Figure [3](#fig:spectra_lines), most of the lines observed in our targets have a peculiar morphology, suggesting the possible presence of two peaks in the observed line spectrum. This result could be explained by the presence of a kinematically-decoupled component such as in a disk or in the later stage of a merger. To decide in a statistically motivated way if our lines should be modeled with a single or double component, we perform a test hypothesis. In our case, the null hypothesis consists in the modeling of the line with a single Gaussian, while the alternative hypothesis consists in the modeling with two Gaussians. Since we are employing two *nested* models (with four and seven free parameters, respectively, since we allow a residual continuum component), we perform a partial F-test (cite: Bevington_03) employing a threshold of 0.05 for the level of significance to reject the null hypothesis. Considering only the highest S/N line in each spectrum, we obtain that the presence of a double component is statistically significant for five out of nine targets ($\sim 55\%$). For most the galaxies where two lines are detected (with the notable exception of RSN-84), the lower S/N of the second line does not allow us to conclude that the additional component is statistically required for a correct modeling. For all the lines where the double model is statistically motivated, we report the best-fitting parameters in Table [3](#tab:decomposition). If we compare our fraction of double-peaked lines with other similar studies in the current literature presenting spectroscopic follow-up of SMGs at (sub)mm wavelengths, we find that our percentage is higher than the $\sim 30$% reported by (cite: Bothwell_13) (detecting CO emission in a large sample of 32 SMGs in the redshift range $1.2<z<4.1$) and (cite: Aravena_16) (observing 17 lensed DSFGs at $2.5<z<5.7$). and of the $\sim40\%$ of double-peaked profiled reported by (cite: Birkin_20) (studying 61 ALMA-detected SMGs). Unfortunately, the limited size of our sample does not allow us to unambiguously establish if this difference is due to the different selections or it is a consequence of the different S/N achieved by the different observations. The presence of two components with different velocities in our galaxies can be explained with both the presence of a rotating structure or as the signature of the late stage of a major merger. These hypotheses are also strengthened by the 1st moments of the CO/\[CI\] lines within three of our targets (those with the highest S/N in the CO-lines; namely, RSN-84, RSN-121, and RSN-235. In RSN-84 the same structure is visible in both the CO(4-3) and \[CI\](1-0) lines; see Figure [4](#fig:Mom1_84)). Unfortunately, the spatial resolution of our observations is not sufficient to distinguish between the two possible models (i.e. presence of disk or merger). Similarly, the coarse spatial and spectral resolution does not allow us to perform a proper modeling of the possible disk (see e.g. (cite: DiTeodoro_15; RomanOliveira_23)). Constraining the deprojected velocity of the gas and its velocity dispersion would allow us to determine if the structure is stable or not. This result would be of crucial importance to constrain some of the evolutionary models of massive galaxies (see Section [4.4](#sec:evolution)).

|     |                   |                   |                   |                 |
|:---:|:-----------------:|:-----------------:|:-----------------:|:---------------:|
| ID  | I$_{\rm CO(3-2)}$ | I$_{\rm CO(4-3)}$ | I$_{\rm CO(5-4)}$ | I$_{[CI](1-0)}$ |
|     |    \[Jy km/s\]    |    \[Jy km/s\]    |    \[Jy km/s\]    |   \[Jy km/s\]   |
| 41  |   $1.06\pm0.07$   |        \-         |        \-         |       \-        |
| 84  |        \-         |   $0.55\pm0.04$   |        \-         |  $0.53\pm0.08$  |
| 121 |        \-         |   $1.03\pm0.04$   |        \-         |  $0.40\pm0.07$  |
| 182 |        \-         |        \-         |   $0.61\pm0.05$   |       \-        |
| 235 |        \-         |        \-         |   $0.71\pm0.04$   |  $0.21\pm0.04$  |
| 247 |   $0.40\pm0.06$   |        \-         |        \-         |       \-        |
| 298 |        \-         |   $0.37\pm0.03$   |   $0.47\pm0.06$   |       \-        |
| 361 |        \-         |        \-         |   $0.31\pm0.04$   |  $0.27\pm0.04$  |
| 456 |   $0.63\pm0.03$   |        \-         |        \-         |       \-        |

: Integrated fluxes of the lines detected in our sources. All the values are obtained through aperture photometry on the 0th moment of each line with an aperture equal to the $2\sigma$ contour.

|                  |               |               |               |
|:----------------:|:-------------:|:-------------:|:-------------:|
|        ID        |  $\Delta v$   |  FWHM (red)   |  FWHM (blue)  |
|                  |   \[km/s\]    |   \[km/s\]    |   \[km/s\]    |
|   84 - CO(4-3)   | $(366\pm61)$  | $(191\pm99)$  | $(401\pm114)$ |
| 84 - \[CI\](1-0) | $(552\pm39)$  | $(234\pm51)$  | $(305\pm77)$  |
|       121        | $(449\pm33)$  | $(289\pm47)$  | $(319\pm68)$  |
|       182        | $(219\pm321)$ | $(387\pm440)$ | $(203\pm214)$ |
|       235        | $(290\pm132)$ | $(376\pm222)$ | $(233\pm78)$  |
|       298        | $(302\pm58)$  | $(208\pm129)$ | $(208\pm66)$  |

: Best-fitting parameters for the Gaussian modeling when two components are employed as described in Section [3.4](#sec:kinematics). The three columns report the IDs of the galaxies, the velocity offset between the two Gaussian components, and the FWHM of each component.

## SED-Fitting

Once assessed the spectroscopic redshift of our sources, we estimate their physical properties through a SED-fitting with the code CIGALE (cite: Boquien_19). To account for all the processes taking place inside our targets, we employ several libraries, following the same strategy employed in (cite: Gentile_24). Firstly, we include the stellar emission through the stellar population libraries by (cite: Bruzual_03), combined through an exponentially declining star formation history with random bursts of star formation. The stellar attenuation is modeled following (cite: Charlot_00), while the dust thermal emission is included in the templates through the (cite: Draine_14) models. Finally, radio emission is treated as described in (cite: Boquien_19). We also explore the possible presence of AGN within our sources, by adding a dusty torus component as modeled by (cite: Fritz_06). For all the models, we employ the parameters used by (cite: Donevski_20) in the analysis of their sample of DSFGs with CIGALE. The results of the SED-fitting and all the physical properties estimated with CIGALE are summarized in Figure [5](#fig:SED) and in Table [\[tab:properties\]](#tab:properties). More in detail, through SED-fitting we estimate the stellar mass ($M_\star$), the infrared luminosity ($L_{\rm IR}$), and the dust attenuation ($A_{\rm v}$). Since the photometric coverage in the FIR/(sub)mm/radio for our targets is significantly better than that in the optical/NIR, we estimate the SFR from the $L_{\rm IR}$ through the relation by (cite: Kennicutt_12) rescaled to a (cite: Chabrier_03) IMF. A last interesting parameter estimated through SED-fitting is the AGN fraction ($f_{\rm AGN}$), defined as the ratio between the luminosity of the host galaxy and that of the AGN in the wavelength range $[5,40]\mu$m. Interestingly, CIGALE reports a $f_{\rm AGN}=0$ for all our targets, therefore we can safely conclude that the photometry of our galaxies can be correctly reproduced without requiring a dusty torus component. Another indication about the lack of powerful AGN contribution in our sample comes from the estimation of the $q_{\rm TIR}$ from the infrared luminosity (computed through SED-fitting) and the radio flux (cite: Helou_85) The latter is converted into a 1.4 GHz radio luminosity through the spectroscopic redshift and the radio slope measured through the radio fluxes at 3 GHz and 1.4/1.28 GHz. For the galaxies lacking a second radio detection (namely, RSN-41, RSN-235, and RSN-298), we assume the median slope computed on the rest of the sample. We obtain that all the $q_{\rm TIR}$ are in the range \[2.45,2.55\], in good agreement with what is commonly measured for star-forming galaxies (cite: Yun_01).

![image](SED_41.png) ![image](SED_84.png)\
![image](SED_121.png) ![image](SED_182.png)\
![image](SED_235.png) ![image](SED_247.png)\
![image](SED_298.png) ![image](SED_361.png)\
![image](SED_456.png)

# Results and discussion

## Analysis of the spec-*z*

As visible in Table [\[tab:lines\]](#tab:lines), the nine galaxies analyzed in this paper have a spec-*z* between 2.8 and 4.7, with a median value of $\sim 3.52$. Comparing these values with the photometric redshifts estimated following (cite: Gentile_24) (once added the continuum point at 3 mm obtained in Section [3.1](#sec:continuum)), we can notice quite a good agreement (see Figure [6](#fig:comparison_zspec)). More quantitatively, we can measure the accuracy of our photo-*z* as: $$\begin{equation}
\centering
    {\rm median}\left(\frac{|z_{\rm phot}-\textit{z}_{\rm spec}|}{1+z_{\rm spec}}\right)=0.05
\end{equation}$$ when considering all the spec-*z* assessed in Section [3.3](#sec:redshifts). This result validates the procedure followed in (cite: Gentile_24) to estimate the photometric redshift of the RS-NIRdark galaxies and it is quite encouraging in planning future follow-ups for the high-*z* candidates reported in that study. Finally, we underline that – since for three of our galaxies with at least one line we have a counterpart in the COSMOS2020 catalog (see Table [\[tab:coords\]](#tab:coords)) – we can retrieve three photo-*z* from that catalog (namely $z=3.6\pm0.3$, $z=2.8\pm0.3$, and $4.6\pm0.3$ for RSN-84, RSN-247, and RSN-361, respectively). These quantities were computed by (cite: Weaver_22) with the two SED-fitting codes EAZY (cite: Brammer_08) and LEPHARE (cite: Arnouts_99; Ilbert_06) on the optical/NIR bands included in the COSMOS2020 catalog and on the first two channels of IRAC, and are in perfect agreement with the spectroscopic redshift estimated through (sub)mm spectroscopy (see Table [\[tab:lines\]](#tab:lines)). A last interesting comparison can be performed with the photometric redshifts computed by (cite: Talia_21) and employed to select the targets for these ALMA observations. Unfortunately, most the sources are located at a lower redshift than expected from that study (see Table [\[tab:lines\]](#tab:lines)). This difference can be explained by the several improvements in the photometry extraction and in the photo-*z* estimation employed in (cite: Gentile_24) with respect to (cite: Talia_21). We expect most of the differences to arise because of the new deblending procedure based on the PHOEBO algorithm (allowing us to better extract the photometry from low-resolution maps; e.g. the four IRAC channels), the deeper IRAC images employed in (cite: Gentile_24), and the more stringent upper limits employed in the photometric bands with no detections. A full comparison between the two procedures can be found in (cite: Gentile_24). We expect this difference in the photo-*z* computed by (cite: Gentile_24) and (cite: Talia_21) to produce different constraints on the contribution of the RS-NIRdark galaxies to the cosmic SFRD (especially at $z>4.5$, where most of the targets were located according to the previous photo-*z*). This point will be addressed in detail through the analysis of the full sample of RS-NIRdark galaxies in COSMOS in a forthcoming paper (Gentile et al., in prep.)

![](zspec_comparison_ALMA.png)

## Analysis of the physical properties

The results obtained through SED-fitting in Section [3.5](#sec:SEDFitting) allow us to confirm one of the main results established in (cite: Gentile_24). In that study, we assessed that the RS-NIRdark galaxies selection produces a sample of star-bursting DSFGs. However, since this result was based on a SED-fitting where the redshift was a free parameter, the quantities estimated through this procedure were affected by significant uncertainties due to the several degeneracies between the shape of the SED and the redshift. By assuming the spec-*z* measured through our ALMA observations, we can decrease the uncertainty on these quantities. First of all, we can see how the median properties estimated with the improved SED-fitting are broadly compatible with those estimated by (cite: Gentile_24) for the whole sample (see also the results discussed in (cite: Talia_21) and (cite: Behiri_23) regarding a smaller subset of the same sample). We underline – however – that since the galaxies in the proposal were selected among those with at least one secure detection in the FIR/(sub)mm regime, we do not expect the median properties of our sample to be necessarily similar to those of the whole sample of RS-NIRdark. A second interesting comparison between this study and that by (cite: Gentile_24) resides in the comparison between the SFR and stellar mass computed through the new SED-fitting and the main sequence of the star-forming galaxies. As visible in Figure [7](#fig:mainsequence), most of the targets are still located above the main sequence by (cite: Schreiber_15), close to the star-bursting regime (i.e. galaxies with a SFR at least three times higher than what expected from a main sequence source with the same mass and in the same redshift bin). We underline – however – that the location on the main sequence strongly relies on the estimated stellar mass, that is quite uncertain for our targets, being the rest-frame UV/optical continuum highly obscured by the dust. Nevertheless, the employment of the CIGALE code, relying on the energy balance principle between the dust absorption and emission allows us to obtain some indirect constrain on the dust extinction from the infrared and radio coverage. More stringent constraints on the stellar mass will be provided – for most of the galaxies in the whole sample of RS-NIRdark galaxies in COSMOS – by the deep NIR imaging provided by JWST as part of the COSMOS-Web survey ((cite: Casey_22), Gentile et al., in prep.). Figure [7](#fig:mainsequence) also reports, for comparison, the location of other populations of *"dark"* DSFGs in the stellar mass vs SFR plane: the H-dropouts by (cite: Wang_19) and the NIRfaint SMGs by (cite: Smail_21). While the overlap between our RS-NIRdark galaxies and the H-dropouts has already been studied in (cite: Gentile_24), the availability of the new (sub)mm data allows us to study more quantitatively how many of our sources would be selected with the criteria employed by (cite: Smail_21). We remind that these sources are part of a sample of 707 SMGs collected in the Ultra Deep Survey by re-imaging with ALMA (in band 7, i.e. at a representative frequency of 870 $\mu$m; (cite: Stach_19)) a sample of galaxies initially detected in the 850 $\mu$m maps produced with the SCUBA2 camera (cite: Geach_17). The sample studied by (cite: Smail_21) contains all[^5] the sources with $Ks>25.3$ mag (at 5 $\sigma$). Since the $Ks$ limiting magnitude in the UDS and in COSMOS are similar, we can study the overlap between the two populations by comparing the (sub)mm flux at 850 $\mu$m. For our sources, only RSN-84 has an ALMA flux at the same frequency (see Table [1](#tab:cont)). Three of the other galaxies have analogous fluxes coming from the deblending of the SCUBA2 maps (cite: Jin_18), while the other have only upper limits (S/N$<3\sigma$, since the uncertainties in the SuperDeblended catalog also account for the deblending procedure. For these sources, we employ the best-fitting fluxes at 850 $\mu$m computed with CIGALE. On the other side, the sources in (cite: Smail_21) were initially selected for having a SNR$>4\sigma$ (equivalent to $S_{\rm 850\mu m}\ge3.8$ mJy) in the original SCUBA2 maps. However, the higher resolution achieved by ALMA in the (cite: Stach_19) follow-up allowed the discovery of multiple fainter sources contributing to the original ones detected by SCUBA2, up to $S_{\rm 850\mu m}>1$ mJy and with a median value of $3.8\pm0.3$ mJy. Therefore, even though 4 out of 9 sources in our sample would not have been selected by the original SCUBA2 survey, being too faint for the limited sensitivity of that instrument (see Table [1](#tab:cont)), all of them would have been detected by the deeper ALMA follow-up.

![](Comparison_MS_ALMA.png)

![](Depletion.png)

## Gas mass and depletion time

![](Evolution.png)

Several studies highlighted how the \[CI\](1-0) and the CO(1-0) lines can be employed as good tracers of the molecular gas inside galaxies (cite: Papadopoulos_04; Valentino_20CI; Gururajan_23). For four galaxies in our sample (see Table [\[tab:lines\]](#tab:lines)), we observed the \[CI\](1-0) line: for them, we can directly estimate the molecular gas mass in our objects by employing the relation by (cite: Papadopoulos_04): $$\begin{equation}
\centering
\label{eq:ci}
M(H_2)^{[CI]}=1375.8\times10^{-12}\frac{D_L^2 I_{[CI](1-0)}}{(1+z)A_{10}Q_{10}X_{CI}}[M_\odot]
\end{equation}$$ where $D_L$ is the luminosity distance of our target expressed in Mpc, $I_{\rm CO}$ is the integrated line flux, and $A_{10}=0.793\times10^{-7}$ s$^{-1}$ is the Einstein coefficient. $Q_{10}$ and $X_{10}$ are, respectively, the \[CI\] excitation factor and the \[CI\]/H$_2$ abundance ratio. For these quantities, we employ literature-standard values of $X_{CI}=3\times10^{-5}$ and $Q_{10}=0.6$ (cite: Papadopoulos_04; Bothwell_17). Through Equation [\[eq:ci\]](#eq:ci), we estimate the gas masses for RSN-84, RSN-121, RSN-235, and RSN-361 reported in Table [\[tab:properties\]](#tab:properties). For all the other targets, in which we did not detect the \[CI\](1-0) line, we derive the gas mass from the CO(1-0) line through the relation $$\begin{equation}
\centering
\label{eq:alpha_co}
    M(H_2)^{\rm CO}=3.25\times10^7\alpha_{\rm CO} I_{\rm CO} \nu_{\rm obs}^{-2}D_L^2(1+z)^{-3}
\end{equation}$$ (see e.g. (cite: Bolatto_13) and references therein). It is well known that the value of $\alpha_{\rm CO}$ is highly uncertain and strongly dependent on the specific property of each galaxy. In this study, we choose a literature value of 0.8 $M_\odot$ \[K km s$^{-1}$ pc$^{-2}$\]$^{-1}$ usually employed for star-bursting galaxies (see e.g. (cite: Bolatto_13; Gururajan_23)). In order to use Equation [\[eq:alpha_co\]](#eq:alpha_co), we need to rescale the measured fluxes of our CO lines to the CO(1-0) transition by assuming a CO-Spectral Line Energy Distribution (SLED). Several studies highlighted how the CO-SLED of galaxies is strongly affected by the presence of AGN (cite: Vallini_19) and evolves with redshift (cite: Boogard_20). Since the previous test performed on our targets by (cite: Talia_21) and (cite: Gentile_24) (together with the null AGN fraction obtained through SED-fitting with CIGALE; Section [3.5](#sec:SEDFitting)) excluded the presence of strong nuclear activity, we choose the CO-SLED obtained by (cite: Bothwell_13) for a sample of DSFGs in the redshift range $1.2-4.1$ (i.e. compatible with the spec-*z* of our targets). More in detail, for our targets, we employ $R_{31}=2.3\pm0.3$, $R_{41}=3.0\pm0.4$, and $R_{51}=3.8\pm0.7$, where $R_{n1}$ is the ratio between the integrated line flux in the nth CO transition and the CO(1-0). The gas mass obtained through these relations are reported in Table [\[tab:properties\]](#tab:properties). For the galaxies with both a CO and a \[CI\] line, we report both the estimation of the gas mass. However, since the values estimated from the \[CI\](1-0) line rely on less assumption than those based on the CO lines (i.e. they do not rely on the assumed CO-SLED, albeit they still depend on the conversion factor between the \[CI\](1-0), as uncertain as the $\alpha_{\rm CO}$ value), we employ these gas masses in the following analyses. The information about the gas content of our galaxies can be combined with the SFR estimated in Section [3.5](#sec:SEDFitting) and reported in Table [\[tab:properties\]](#tab:properties) to assess the depletion time of our galaxies. This quantity is defined as the amount of time in which each object would transform its whole gas mass in stars assuming a constant SFR: $$\begin{equation}
\centering
    \tau_{\rm D}=\frac{M(H_2)}{\rm SFR}
\end{equation}$$ For our galaxies, we obtain the depletion times reported in the last column of Table [\[tab:properties\]](#tab:properties). The galaxies in our sample have values in the range $80-300$ Myr. These quantities can be compared with other population of galaxies in the current literature, as shown in Figure [8](#fig:depletion). More in detail, we can compare the depletion time of our targets with that expected from main sequence galaxies. (cite: Saintonge_13) reported a $\tau_{\rm D}$ evolving with redshift as $\tau_{\rm D}=1.5(1+z)^{\alpha}$, with several collaborations finding different values for the exponent, spanning from $\alpha=-1.0$ (cite: Davè_12) to $\alpha=-1.5$ (cite: Magnelli_13). Our targets result to have a shorter depletion time than main sequence galaxies. This result represents a further confirmation (independent from the more uncertain stellar mass) of the star-bursting nature of our sources. Similarly, we can compare the gas mass and the SFR of our RS-NIRdark galaxies with several SMGs in the current literature (namely, those analysed by (cite: Walter_11), (cite: Bothwell_17) and (cite: Canameras_18)). For all these sources, we retrieve the infrared luminosity and the \[CI\](1-0) line fluxes from the study by (cite: Valentino_20CI). Following the relations by (cite: Kennicutt_12) and (cite: Papadopoulos_04), we estimated the SFR and gas mass in a consistent way with those derived from our targets. We obtain that our RS-NIRdark galaxies are – on average – more gas rich than the SMGs analyzed in those studies, in the low-SFR tail of their distribution, and – therefore – with a longer depletion time.

## Possible evolutionary path

The gas mass and depletion times estimated in Section [4.3](#sec:gas_evolution) allows us to forecast a possible evolutionary path for our sources. We employ the same simplistic model used to define the depletion time: we assume that the SFR will stay constant inside our sources until all the gas mass is converted into stars. Clearly, this model does not account for any quenching mechanism (e.g. those due to possible AGN feedback; see e.g. (cite: Fabian_12)) or gas accretion from the inter-galactic medium (cite: Sancisi_08). With this model, we can assume that our galaxies will evolve from an initial state characterized by $z_0=z_{\rm spec}$ and $M_{\star,0}=M_\star$ to a final state with $z_f=z_{\rm spec} - \Delta z$ and $M_{\star, f}=M_\star + M_{\rm H_2}$, where $\Delta z$ is the difference in redshift elapsed during the depletion time. The results of this simplistic model applied to our targets is shown in Figure [9](#fig:evolution), where we consider all the uncertainties on the involved quantities through a MonteCarlo integration. We can compare the final stage of our galaxies with the redshift and stellar mass of the massive and passive galaxies discovered by (cite: Schreiber_18) at $z\sim3$, we can notice a significant overlap between the two populations. This result, combined with the number densities estimated by (cite: Talia_21), (cite: Behiri_23) and (cite: Gentile_24) suggest that the RS-NIRdark galaxies could represent a significant fraction of the progenitors of the massive and passive galaxies at $z\sim3$. In the broader context of galaxy evolution studies, this result confirms the idea that the dust-obscured galaxies play a significant role in the evolution of the most massive galaxies in the Universe (cite: casey_14; Toft_14; Valentino_20). In addition, the components with different velocities detected in our targets in Section [3.4](#sec:kinematics) could support two possible evolutionary scenarios for our galaxies. In one case, they could be the signature of a significant fraction of major mergers within our sample. This result would confirm the so-called *merger-driven* scenario for the formation of massive galaxies, where these objects are formed through a series of major mergers (see e.g. (cite: Hopkins_18a; Hopkins_18b)). On the other case, the double component in our galaxies could be due to the presence of a rotating disk. In this case, this result would support the so-called *in-situ* scenario, where the build-up of massive galaxies occurs via the rapid compaction of a gaseous outer disk triggering a huge burst of star formation, and via the subsequent stellar and AGN feedback processes quenching it within a relatively short timescale ($<1$ Gyr; see e.g (cite: Lapi_14), (cite: Lapi_14), (cite: Pantoni_19)). The possibility of shedding new light on these alternative scenario increases the scientific interest in the RS-NIRdark galaxies and the need for high-resolution follow-up for these sources.

# Summary

In this paper, we presented the first spectroscopic follow-up at mm wavelengths for a pilot sample of 9 RS-NIRdark galaxies in the COSMOS field. These sources were initially selected by (cite: Talia_21) as radio-detected sources at 3 GHz lacking an optical/NIR counterpart in the COSMOS2015 catalog, even though three of them (see Table [\[tab:coords\]](#tab:coords)) were subsequently detected in the deeper COSMOS2020. Through a new series of ALMA observations, we managed to identify at least one bright emission line in all the targets and two lines in five out of nine objects. From the analysis of the new ALMA data, we obtain the following results:

- Modeling the detected lines as CO/\[CI\] transitions, we estimated a spectroscopic redshift for all the galaxies in our sample. These values are in good agreement with those estimated through SED-fitting in (cite: Gentile_24).

- The new availability of a spectroscopic redshift allowed us to decrease the degeneracies in the SED-fitting procedure. This improved SED-fitting confirmed one of the main results concerning the RS-NIRdark galaxies: they represent a population of highly-obscured ($A_{\rm v}\sim4$), massive ($M_\star\sim10^{11}M_\odot$), and star-forming (SFR$\sim 500$ M$_\odot$ yr$^{-1}$) galaxies.

- The same improved SED-fitting, together with pre-existing data, allowed us to estimate the flux of our sources at 870 $\mu$m. This value is analogous to that reported by (cite: Smail_21) for their sample of NIR-faint SMGs, suggesting that our radio selection is able to provide a similar population of DSFGs as those obtained from (sub)mm selections. A similar conclusion is reached by observing the overlap between the physical properties (stellar mass and SFR) computed through SED-fitting for the two samples.

- Thanks to the good spectral resolution of the new ALMA observations, we assessed the presence of a high fraction ($\sim 55$%) of double-peaked profiles in the lines detected in our targets. We explained this result with the possible presence of a rotating structure within our galaxies or with the presence of major mergers in our sample. High-resolution follow-up with ALMA or JWST are needed to discriminate between these two possibilities.

- Thanks to the CO/\[CI\] lines detected in our targets, we estimated the gas mass and the depletion time of our galaxies. These results allowed us to forecast a possible evolutionary path for our objects, strongly suggesting that the RS-NIRdark galaxies could represent a significant fraction of the progenitors of the massive and passive galaxies at $z\sim 3$ and excellent probes to test galaxy evolution models.

# Acknowledgments

We thank the anonymous referee for their comments that improved the initial version of this paper. FG thanks Gayathri Gururajan for the insightful conversations about the gas tracers, Anton Koekemoer and Ian Smail for the careful reading of the manuscript and for the useful comments, and Roberto Decarli for the precious feedback on an early version of this paper. FG, MT, AL, MM and AC acknowledge the support from grant PRIN MIUR 2017-20173ML3WW_001. ‘Opening the ALMA window on the cosmic evolution of gas, stars, and supermassive black holes’. ID acknowledges support from INAF Minigrant "Harnessing the power of VLBA towards a census of AGN and star formation at high redshift". MV acknowledges financial support from the Inter-University Institute for Data Intensive Astronomy (IDIA), a partnership of the University of Cape Town, the University of Pretoria and the University of the Western Cape, and from the South African Department of Science and Innovation’s National Research Foundation under the ISARP RADIOSKY2020 and RADIOMAP Joint Research Schemes (DSI-NRF Grant Numbers 113121 and 150551) and the SRUG HIPPO Projects (DSI-NRF Grant Numbers 121291 and SRUG22031677). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.01467.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ

106 natexlab

(ref: Aravena_16) Aravena, M., Spilker, J. S., Bethermin, M., et al. 2016, [MNRAS](http://dx.doi.org/10.1093/mnras/stw275), [457, 4406](https://ui.adsabs.harvard.edu/abs/2016MNRAS.457.4406A)

(ref: Arnouts_99) Arnouts, S., Cristiani, S., Moscardini, L., et al. 1999, [MNRAS](http://dx.doi.org/10.1046/j.1365-8711.1999.02978.x), [310, 540](https://ui.adsabs.harvard.edu/abs/1999MNRAS.310..540A)

(ref: Behiri_23) Behiri, M., Talia, M., Cimatti, A., et al. 2023, [[arXiv e-prints](http://dx.doi.org/10.48550/arXiv.2309.00050), arXiv:2309.00050](https://ui.adsabs.harvard.edu/abs/2023arXiv230900050B)

(ref: Bevington_03) Bevington, P. R. & Robinson, D. K. 2003, Data reduction and error analysis for the physical sciences; 3rd ed. (New York, NY: McGraw-Hill)

(ref: Birkin_20) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021, [MNRAS](http://dx.doi.org/10.1093/mnras/staa3862), [501, 3926](https://ui.adsabs.harvard.edu/abs/2021MNRAS.501.3926B)

(ref: Bolatto_13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, [ARA&A](http://dx.doi.org/10.1146/annurev-astro-082812-140944), [51, 207](https://ui.adsabs.harvard.edu/abs/2013ARA&A..51..207B)

(ref: interferopy) Boogaard, L., Meyer, R. A., & Novak, M. 2021, Interferopy: analysing datacubes from radio-to-submm observations

(ref: Boogard_20) Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020, [ApJ](http://dx.doi.org/10.3847/1538-4357/abb82f), [902, 109](https://ui.adsabs.harvard.edu/abs/2020ApJ...902..109B)

(ref: Boquien_19) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, [A&A](http://dx.doi.org/10.1051/0004-6361/201834156), [622, A103](https://ui.adsabs.harvard.edu/abs/2019A&A...622A.103B)

(ref: Bothwell_17) Bothwell, M. S., Aguirre, J. E., Aravena, M., et al. 2017, [MNRAS](http://dx.doi.org/10.1093/mnras/stw3270), [466, 2825](https://ui.adsabs.harvard.edu/abs/2017MNRAS.466.2825B)

(ref: Bothwell_13) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, [MNRAS](http://dx.doi.org/10.1093/mnras/sts562), [429, 3047](https://ui.adsabs.harvard.edu/abs/2013MNRAS.429.3047B)

(ref: Brammer_08) Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, [ApJ](http://dx.doi.org/10.1086/591786), [686, 1503](https://ui.adsabs.harvard.edu/abs/2008ApJ...686.1503B)

(ref: Bruzual_03) Bruzual, G. & Charlot, S. 2003, [MNRAS](http://dx.doi.org/10.1046/j.1365-8711.2003.06897.x), [344, 1000](https://ui.adsabs.harvard.edu/abs/2003MNRAS.344.1000B)

(ref: Burgarella_13) Burgarella, D., Buat, V., Gruppioni, C., et al. 2013, [A&A](http://dx.doi.org/10.1051/0004-6361/201321651), [554, A70](https://ui.adsabs.harvard.edu/abs/2013A&A...554A..70B)

(ref: Canameras_18) Cañameras, R., Yang, C., Nesvadba, N. P. H., et al. 2018, [A&A](http://dx.doi.org/10.1051/0004-6361/201833625), [620, A61](https://ui.adsabs.harvard.edu/abs/2018A&A...620A..61C)

(ref: CASA_22) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, [PASP](http://dx.doi.org/10.1088/1538-3873/ac9642), [134, 114501](https://ui.adsabs.harvard.edu/abs/2022PASP..134k4501C)

(ref: Casey_22) Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023, [ApJ](http://dx.doi.org/10.3847/1538-4357/acc2bc), [954, 31](https://ui.adsabs.harvard.edu/abs/2023ApJ...954...31C)

(ref: casey_14) Casey, C. M., Narayanan, D., & Cooray, A. 2014, [Phys. Rep.](http://dx.doi.org/10.1016/j.physrep.2014.02.009), [541, 45](https://ui.adsabs.harvard.edu/abs/2014PhR...541...45C)

(ref: Casey_21) Casey, C. M., Zavala, J. A., Manning, S. M., et al. 2021, [ApJ](http://dx.doi.org/10.3847/1538-4357/ac2eb4), [923, 215](https://ui.adsabs.harvard.edu/abs/2021ApJ...923..215C)

(ref: Chabrier_03) Chabrier, G. 2003, [PASP](http://dx.doi.org/10.1086/376392), [115, 763](https://ui.adsabs.harvard.edu/abs/2003PASP..115..763C)

(ref: Chapman_02) Chapman, S. C., Lewis, G. F., Scott, D., Borys, C., & Richards, E. 2002, [ApJ](http://dx.doi.org/10.1086/339498), [570, 557](https://ui.adsabs.harvard.edu/abs/2002ApJ...570..557C)

(ref: Chapman_01) Chapman, S. C., Richards, E. A., Lewis, G. F., Wilson, G., & Barger, A. J. 2001, [ApJL](http://dx.doi.org/10.1086/319111), [548, L147](https://ui.adsabs.harvard.edu/abs/2001ApJ...548L.147C)

(ref: Chapman_04) Chapman, S. C., Smail, I., Blain, A. W., & Ivison, R. J. 2004, [ApJ](http://dx.doi.org/10.1086/423833), [614, 671](https://ui.adsabs.harvard.edu/abs/2004ApJ...614..671C)

(ref: Charlot_00) Charlot, S. & Fall, S. M. 2000, [ApJ](http://dx.doi.org/10.1086/309250), [539, 718](https://ui.adsabs.harvard.edu/abs/2000ApJ...539..718C)

(ref: Civano_16) Civano, F., Marchesi, S., Comastri, A., et al. 2016, [ApJ](http://dx.doi.org/10.3847/0004-637X/819/1/62), [819, 62](https://ui.adsabs.harvard.edu/abs/2016ApJ...819...62C)

(ref: CARTA_21) Comrie, A., Wang, K.-S., Hsu, S.-C., et al. 2021, CARTA: The Cube Analysis and Rendering Tool for Astronomy

(ref: Coogan_18) Coogan, R. T., Daddi, E., Sargent, M. T., et al. 2018, [MNRAS](http://dx.doi.org/10.1093/mnras/sty1446), [479, 703](https://ui.adsabs.harvard.edu/abs/2018MNRAS.479..703C)

(ref: Cox_23) Cox, P., Neri, R., Berta, S., et al. 2023, [[arXiv e-prints](http://dx.doi.org/10.48550/arXiv.2307.15732), arXiv:2307.15732](https://ui.adsabs.harvard.edu/abs/2023arXiv230715732C)

(ref: Daddi_15) Daddi, E., Dannerbauer, H., Liu, D., et al. 2015, [A&A](http://dx.doi.org/10.1051/0004-6361/201425043), [577, A46](https://ui.adsabs.harvard.edu/abs/2015A&A...577A..46D)

(ref: Davè_12) Davé, R., Finlator, K., & Oppenheimer, B. D. 2012, [MNRAS](http://dx.doi.org/10.1111/j.1365-2966.2011.20148.x), [421, 98](https://ui.adsabs.harvard.edu/abs/2012MNRAS.421...98D)

(ref: DiTeodoro_15) Di Teodoro, E. M. & Fraternali, F. 2015, [MNRAS](http://dx.doi.org/10.1093/mnras/stv1213), [451, 3021](https://ui.adsabs.harvard.edu/abs/2015MNRAS.451.3021D)

(ref: Donevski_20) Donevski, D., Lapi, A., Małek, K., et al. 2020, [A&A](http://dx.doi.org/10.1051/0004-6361/202038405), [644, A144](https://ui.adsabs.harvard.edu/abs/2020A&A...644A.144D)

(ref: Draine_14) Draine, B. T., Aniano, G., Krause, O., et al. 2014, [ApJ](http://dx.doi.org/10.1088/0004-637X/780/2/172), [780, 172](https://ui.adsabs.harvard.edu/abs/2014ApJ...780..172D)

(ref: Dudzevicute_21) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2021, [MNRAS](http://dx.doi.org/10.1093/mnras/staa3285), [500, 942](https://ui.adsabs.harvard.edu/abs/2021MNRAS.500..942D)

(ref: Dunlop_17) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, [MNRAS](http://dx.doi.org/10.1093/mnras/stw3088), [466, 861](https://ui.adsabs.harvard.edu/abs/2017MNRAS.466..861D)

(ref: Dunlop_04) Dunlop, J. S., McLure, R. J., Yamada, T., et al. 2004, [MNRAS](http://dx.doi.org/10.1111/j.1365-2966.2004.07700.x), [350, 769](https://ui.adsabs.harvard.edu/abs/2004MNRAS.350..769D)

(ref: Elvis_09) Elvis, M., Civano, F., Vignali, C., et al. 2009, [ApJS](http://dx.doi.org/10.1088/0067-0049/184/1/158), [184, 158](https://ui.adsabs.harvard.edu/abs/2009ApJS..184..158E)

(ref: Endsley_21) Endsley, R., Stark, D. P., Charlot, S., et al. 2021, [MNRAS](http://dx.doi.org/10.1093/mnras/stab432), [502, 6044](https://ui.adsabs.harvard.edu/abs/2021MNRAS.502.6044E)

(ref: Enia_22) Enia, A., Talia, M., Pozzi, F., et al. 2022, [ApJ](http://dx.doi.org/10.3847/1538-4357/ac51ca), [927, 204](https://ui.adsabs.harvard.edu/abs/2022ApJ...927..204E)

(ref: Fabian_12) Fabian, A. C. 2012, [ARA&A](http://dx.doi.org/10.1146/annurev-astro-081811-125521), [50, 455](https://ui.adsabs.harvard.edu/abs/2012ARA&A..50..455F)

(ref: Franco_18) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, [A&A](http://dx.doi.org/10.1051/0004-6361/201832928), [620, A152](https://ui.adsabs.harvard.edu/abs/2018A&A...620A.152F)

(ref: Frayer_04) Frayer, D. T., Reddy, N. A., Armus, L., et al. 2004, [AJ](http://dx.doi.org/10.1086/380943), [127, 728](https://ui.adsabs.harvard.edu/abs/2004AJ....127..728F)

(ref: Fritz_06) Fritz, J., Franceschini, A., & Hatziminaoglou, E. 2006, [MNRAS](http://dx.doi.org/10.1111/j.1365-2966.2006.09866.x), [366, 767](https://ui.adsabs.harvard.edu/abs/2006MNRAS.366..767F)

(ref: Geach_17) Geach, J. E., Dunlop, J. S., Halpern, M., et al. 2017, [MNRAS](http://dx.doi.org/10.1093/mnras/stw2721), [465, 1789](https://ui.adsabs.harvard.edu/abs/2017MNRAS.465.1789G)

(ref: Gentile_24) Gentile, F., Talia, M., Behiri, M., et al. 2024, [ApJ](http://dx.doi.org/10.3847/1538-4357/ad1519), [962, 26](https://ui.adsabs.harvard.edu/abs/2024ApJ...962...26G)

(ref: Giavalisco_02) Giavalisco, M. 2002, [ARA&A](http://dx.doi.org/10.1146/annurev.astro.40.121301.111837), [40, 579](https://ui.adsabs.harvard.edu/abs/2002ARA&A..40..579G)

(ref: Gruppioni_20) Gruppioni, C., Béthermin, M., Loiacono, F., et al. 2020, [A&A](http://dx.doi.org/10.1051/0004-6361/202038487), [643, A8](https://ui.adsabs.harvard.edu/abs/2020A&A...643A...8G)

(ref: Gruppioni_13) Gruppioni, C., Pozzi, F., Rodighiero, G., et al. 2013, [MNRAS](http://dx.doi.org/10.1093/mnras/stt308), [432, 23](https://ui.adsabs.harvard.edu/abs/2013MNRAS.432...23G)

(ref: Gururajan_23) Gururajan, G., B’ethermin, M., Sulzenauer, N., et al. 2023, [A&A](http://dx.doi.org/10.1051/0004-6361/202346449), [676, A89](https://ui.adsabs.harvard.edu/abs/2023A&A...676A..89G)

(ref: Helou_85) Helou, G., Soifer, B. T., & Rowan-Robinson, M. 1985, [ApJL](http://dx.doi.org/10.1086/184556), [298, L7](https://ui.adsabs.harvard.edu/abs/1985ApJ...298L...7H)

(ref: Heywood_22) Heywood, I., Jarvis, M. J., Hale, C. L., et al. 2022, [MNRAS](http://dx.doi.org/10.1093/mnras/stab3021), [509, 2150](https://ui.adsabs.harvard.edu/abs/2022MNRAS.509.2150H)

(ref: Hickox_18) Hickox, R. C. & Alexander, D. M. 2018, [ARA&A](http://dx.doi.org/10.1146/annurev-astro-081817-051803), [56, 625](https://ui.adsabs.harvard.edu/abs/2018ARA&A..56..625H)

(ref: Hogbom_74) Högbom, J. A. 1974, A&AS, [15, 417](https://ui.adsabs.harvard.edu/abs/1974A&AS...15..417H)

(ref: Hopkins_18b) Hopkins, P. F., Cox, T. J., Kereš, D., & Hernquist, L. 2008a, [ApJS](http://dx.doi.org/10.1086/524363), [175, 390](https://ui.adsabs.harvard.edu/abs/2008ApJS..175..390H)

(ref: Hopkins_18a) Hopkins, P. F., Hernquist, L., Cox, T. J., & Kereš, D. 2008b, [ApJS](http://dx.doi.org/10.1086/524362), [175, 356](https://ui.adsabs.harvard.edu/abs/2008ApJS..175..356H)

(ref: Hughes_98) Hughes, D. H., Serjeant, S., Dunlop, J., et al. 1998, [Nature](http://dx.doi.org/10.1038/28328), [394, 241](https://ui.adsabs.harvard.edu/abs/1998Natur.394..241H)

(ref: Ilbert_06) Ilbert, O., Arnouts, S., McCracken, H. J., et al. 2006, [A&A](http://dx.doi.org/10.1051/0004-6361:20065138), [457, 841](https://ui.adsabs.harvard.edu/abs/2006A&A...457..841I)

(ref: Jarvis_16) Jarvis, M., Taylor, R., Agudo, I., et al. 2016, in MeerKAT Science: On the Pathway to the SKA, [6](https://ui.adsabs.harvard.edu/abs/2016mks..confE...6J)

(ref: Jin_18) Jin, S., Daddi, E., Liu, D., et al. 2018, [ApJ](http://dx.doi.org/10.3847/1538-4357/aad4af), [864, 56](https://ui.adsabs.harvard.edu/abs/2018ApJ...864...56J)

(ref: Jin_19) Jin, S., Daddi, E., Magdis, G. E., et al. 2019, [ApJ](http://dx.doi.org/10.3847/1538-4357/ab55d6), [887, 144](https://ui.adsabs.harvard.edu/abs/2019ApJ...887..144J)

(ref: Jin_22) Jin, S., Daddi, E., Magdis, G. E., et al. 2022, [A&A](http://dx.doi.org/10.1051/0004-6361/202243341), [665, A3](https://ui.adsabs.harvard.edu/abs/2022A&A...665A...3J)

(ref: Kennicutt_12) Kennicutt, R. C. & Evans, N. J. 2012, [ARA&A](http://dx.doi.org/10.1146/annurev-astro-081811-125610), [50, 531](https://ui.adsabs.harvard.edu/abs/2012ARA&A..50..531K)

(ref: Koekemoer_07) Koekemoer, A. M., Aussel, H., Calzetti, D., et al. 2007, [ApJS](http://dx.doi.org/10.1086/520086), [172, 196](https://ui.adsabs.harvard.edu/abs/2007ApJS..172..196K)

(ref: Labbe_06) Labbé, I., Bouwens, R., Illingworth, G. D., & Franx, M. 2006, [ApJL](http://dx.doi.org/10.1086/508512), [649, L67](https://ui.adsabs.harvard.edu/abs/2006ApJ...649L..67L)

(ref: Laigle_16) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, [ApJS](http://dx.doi.org/10.3847/0067-0049/224/2/24), [224, 24](https://ui.adsabs.harvard.edu/abs/2016ApJS..224...24L)

(ref: Lapi_14) Lapi, A., Raimundo, S., Aversa, R., et al. 2014, [ApJ](http://dx.doi.org/10.1088/0004-637X/782/2/69), [782, 69](https://ui.adsabs.harvard.edu/abs/2014ApJ...782...69L)

(ref: Liu_19) Liu, D., Lang, P., Magnelli, B., et al. 2019, [ApJS](http://dx.doi.org/10.3847/1538-4365/ab42da), [244, 40](https://ui.adsabs.harvard.edu/abs/2019ApJS..244...40L)

(ref: Madau_14) Madau, P. & Dickinson, M. 2014, [ARA&A](http://dx.doi.org/10.1146/annurev-astro-081811-125615), [52, 415](https://ui.adsabs.harvard.edu/abs/2014ARA&A..52..415M)

(ref: Magnelli_13) Magnelli, B., Popesso, P., Berta, S., et al. 2013, [A&A](http://dx.doi.org/10.1051/0004-6361/201321371), [553, A132](https://ui.adsabs.harvard.edu/abs/2013A&A...553A.132M)

(ref: Manning_22) Manning, S. M., Casey, C. M., Zavala, J. A., et al. 2022, [ApJ](http://dx.doi.org/10.3847/1538-4357/ac366a), [925, 23](https://ui.adsabs.harvard.edu/abs/2022ApJ...925...23M)

(ref: Moneti_22) Moneti, A., Euclid Collaboration, McCracken, H. J., et al. 2022, [A&A](http://dx.doi.org/10.1051/0004-6361/202142361), [658, A126](https://ui.adsabs.harvard.edu/abs/2022A&A...658A.126E)

(ref: Pantoni_19) Pantoni, L., Lapi, A., Massardi, M., Goswami, S., & Danese, L. 2019, [ApJ](http://dx.doi.org/10.3847/1538-4357/ab2adc), [880, 129](https://ui.adsabs.harvard.edu/abs/2019ApJ...880..129P)

(ref: Papadopoulos_04) Papadopoulos, P. P., Thi, W. F., & Viti, S. 2004, [MNRAS](http://dx.doi.org/10.1111/j.1365-2966.2004.07762.x), [351, 147](https://ui.adsabs.harvard.edu/abs/2004MNRAS.351..147P)

(ref: Puglisi_19) Puglisi, A., Daddi, E., Liu, D., et al. 2019, [ApJL](http://dx.doi.org/10.3847/2041-8213/ab1f92), [877, L23](https://ui.adsabs.harvard.edu/abs/2019ApJ...877L..23P)

(ref: RomanOliveira_23) Roman-Oliveira, F., Fraternali, F., & Rizzo, F. 2023, [MNRAS](http://dx.doi.org/10.1093/mnras/stad530), [521, 1045](https://ui.adsabs.harvard.edu/abs/2023MNRAS.521.1045R)

(ref: RowanRobinson_16) Rowan-Robinson, M., Oliver, S., Wang, L., et al. 2016, [MNRAS](http://dx.doi.org/10.1093/mnras/stw1169), [461, 1100](https://ui.adsabs.harvard.edu/abs/2016MNRAS.461.1100R)

(ref: Saintonge_13) Saintonge, A., Lutz, D., Genzel, R., et al. 2013, [ApJ](http://dx.doi.org/10.1088/0004-637X/778/1/2), [778, 2](https://ui.adsabs.harvard.edu/abs/2013ApJ...778....2S)

(ref: Sancisi_08) Sancisi, R., Fraternali, F., Oosterloo, T., & van der Hulst, T. 2008, [A&ARv](http://dx.doi.org/10.1007/s00159-008-0010-0), [15, 189](https://ui.adsabs.harvard.edu/abs/2008A&ARv..15..189S)

(ref: Schinnerer_10) Schinnerer, E., Sargent, M. T., Bondi, M., et al. 2010, [ApJS](http://dx.doi.org/10.1088/0067-0049/188/2/384), [188, 384](https://ui.adsabs.harvard.edu/abs/2010ApJS..188..384S)

(ref: Schreiber_18) Schreiber, C., Glazebrook, K., Nanayakkara, T., et al. 2018, [A&A](http://dx.doi.org/10.1051/0004-6361/201833070), [618, A85](https://ui.adsabs.harvard.edu/abs/2018A&A...618A..85S)

(ref: Schreiber_15) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, [A&A](http://dx.doi.org/10.1051/0004-6361/201425017), [575, A74](https://ui.adsabs.harvard.edu/abs/2015A&A...575A..74S)

(ref: Scoville_07) Scoville, N., Aussel, H., Brusa, M., et al. 2007, [ApJS](http://dx.doi.org/10.1086/516585), [172, 1](https://ui.adsabs.harvard.edu/abs/2007ApJS..172....1S)

(ref: Simpson_20) Simpson, J. M., Smail, I., Dudzevičiūtė, U., et al. 2020, [MNRAS](http://dx.doi.org/10.1093/mnras/staa1345), [495, 3409](https://ui.adsabs.harvard.edu/abs/2020MNRAS.495.3409S)

(ref: Simpson_19) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2015, [ApJ](http://dx.doi.org/10.1088/0004-637X/799/1/81), [799, 81](https://ui.adsabs.harvard.edu/abs/2015ApJ...799...81S)

(ref: Simpson_14) Simpson, J. M., Swinbank, A. M., Smail, I., et al. 2014, [ApJ](http://dx.doi.org/10.1088/0004-637X/788/2/125), [788, 125](https://ui.adsabs.harvard.edu/abs/2014ApJ...788..125S)

(ref: Smail_21) Smail, I., Dudzevičiūtė, U., Stach, S. M., et al. 2021, [MNRAS](http://dx.doi.org/10.1093/mnras/stab283), [502, 3426](https://ui.adsabs.harvard.edu/abs/2021MNRAS.502.3426S)

(ref: Smail_97) Smail, I., Ivison, R. J., & Blain, A. W. 1997, [ApJL](http://dx.doi.org/10.1086/311017), [490, L5](https://ui.adsabs.harvard.edu/abs/1997ApJ...490L...5S)

(ref: Smail_99) Smail, I., Ivison, R. J., Kneib, J. P., et al. 1999, [MNRAS](http://dx.doi.org/10.1046/j.1365-8711.1999.02819.x), [308, 1061](https://ui.adsabs.harvard.edu/abs/1999MNRAS.308.1061S)

(ref: Smail_02) Smail, I., Owen, F. N., Morrison, G. E., et al. 2002, [ApJ](http://dx.doi.org/10.1086/344440), [581, 844](https://ui.adsabs.harvard.edu/abs/2002ApJ...581..844S)

(ref: Smolcic_17) Smolčić, V., Novak, M., Bondi, M., et al. 2017, [A&A](http://dx.doi.org/10.1051/0004-6361/201628704), [602, A1](https://ui.adsabs.harvard.edu/abs/2017A&A...602A...1S)

(ref: Stach_19) Stach, S. M., Dudzevičiūtė, U., Smail, I., et al. 2019, [MNRAS](http://dx.doi.org/10.1093/mnras/stz1536), [487, 4648](https://ui.adsabs.harvard.edu/abs/2019MNRAS.487.4648S)

(ref: Stark_09) Stark, D. P., Ellis, R. S., Bunker, A., et al. 2009, [ApJ](http://dx.doi.org/10.1088/0004-637X/697/2/1493), [697, 1493](https://ui.adsabs.harvard.edu/abs/2009ApJ...697.1493S)

(ref: Straatman_14) Straatman, C. M. S., Labbé, I., Spitler, L. R., et al. 2014, [ApJL](http://dx.doi.org/10.1088/2041-8205/783/1/L14), [783, L14](https://ui.adsabs.harvard.edu/abs/2014ApJ...783L..14S)

(ref: Talia_21) Talia, M., Cimatti, A., Giulietti, M., et al. 2021, [ApJ](http://dx.doi.org/10.3847/1538-4357/abd6e3), [909, 23](https://ui.adsabs.harvard.edu/abs/2021ApJ...909...23T)

(ref: Toft_14) Toft, S., Smolčić, V., Magnelli, B., et al. 2014, [ApJ](http://dx.doi.org/10.1088/0004-637X/782/2/68), [782, 68](https://ui.adsabs.harvard.edu/abs/2014ApJ...782...68T)

(ref: Traina_23) Traina, A., Gruppioni, C., Delvecchio, I., et al. 2023, [[arXiv e-prints](http://dx.doi.org/10.48550/arXiv.2309.15150), arXiv:2309.15150](https://ui.adsabs.harvard.edu/abs/2023arXiv230915150T)

(ref: Valentino_20CI) Valentino, F., Magdis, G. E., Daddi, E., et al. 2020a, [ApJ](http://dx.doi.org/10.3847/1538-4357/ab6603), [890, 24](https://ui.adsabs.harvard.edu/abs/2020ApJ...890...24V)

(ref: Valentino_20) Valentino, F., Tanaka, M., Davidzon, I., et al. 2020b, [ApJ](http://dx.doi.org/10.3847/1538-4357/ab64dc), [889, 93](https://ui.adsabs.harvard.edu/abs/2020ApJ...889...93V)

(ref: Vallini_19) Vallini, L., Tielens, A. G. G. M., Pallottini, A., et al. 2019, [MNRAS](http://dx.doi.org/10.1093/mnras/stz2837), [490, 4502](https://ui.adsabs.harvard.edu/abs/2019MNRAS.490.4502V)

(ref: VanDerVlugt_23) van der Vlugt, D., Hodge, J. A., Jin, S., et al. 2023, [ApJ](http://dx.doi.org/10.3847/1538-4357/acd549), [951, 131](https://ui.adsabs.harvard.edu/abs/2023ApJ...951..131V)

(ref: Walter_16) Walter, F., Decarli, R., Aravena, M., et al. 2016, [ApJ](http://dx.doi.org/10.3847/1538-4357/833/1/67), [833, 67](https://ui.adsabs.harvard.edu/abs/2016ApJ...833...67W)

(ref: Walter_11) Walter, F., Weiß, A., Downes, D., Decarli, R., & Henkel, C. 2011, [ApJ](http://dx.doi.org/10.1088/0004-637X/730/1/18), [730, 18](https://ui.adsabs.harvard.edu/abs/2011ApJ...730...18W)

(ref: Wang_19) Wang, T., Schreiber, C., Elbaz, D., et al. 2019, [Nature](http://dx.doi.org/10.1038/s41586-019-1452-4), [572, 211](https://ui.adsabs.harvard.edu/abs/2019Natur.572..211W)

(ref: Weaver_22) Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022, [ApJS](http://dx.doi.org/10.3847/1538-4365/ac3078), [258, 11](https://ui.adsabs.harvard.edu/abs/2022ApJS..258...11W)

(ref: Whitler_22) Whitler, L., Stark, D. P., Endsley, R., et al. 2022, [arXiv e-prints, arXiv:2206.05315](https://ui.adsabs.harvard.edu/abs/2022arXiv220605315W)

(ref: Yun_01) Yun, M. S., Reddy, N. A., & Condon, J. J. 2001, [ApJ](http://dx.doi.org/10.1086/323145), [554, 803](https://ui.adsabs.harvard.edu/abs/2001ApJ...554..803Y)

![](Spectra_All_1.png)

![](Spectra_All_2.png)

![](Cutout_All.png)

[^1]: <https://sites.google.com/inaf.it/rsnirdark/>

[^2]: Since these sources were detected in the COSMOS2020 catalog, they are not part of the sample analysed in (cite: Gentile_24). For these sources, we performed the same analysis (photometry extraction and SED-fitting) as described in that study.

[^3]: <https://github.com/fab-gentile/PhoEBO>

[^4]: The FWZI is an immediate product of the procedure employed to identify the lines in the extracted spectra since it corresponds to the binning maximizing the S/N of the line. However, in Table [\[tab:lines\]](#tab:lines), we report the more common Full With at Half Maximum (FWHM) obtained through the Gaussian modeling described in Section [3.4](#sec:kinematics).

[^5]: The original sample of NIRfaint sources by (cite: Smail_21) would contain other 50 sources that are not included in that study due to a contaminated photometry at optical/NIR frequencies. Here, we suppose that the 30 galaxies analysed by (cite: Smail_21) are representative of the full sample

</paper>

Write the methods card for this paper.