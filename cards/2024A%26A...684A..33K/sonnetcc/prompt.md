# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...684A..33K\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...684A..33K",
 "title": "The cold molecular gas in z ≳ 6 quasar host galaxies",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Kaasinen, Melanie",
 "n_authors": 11,
 "arxiv_id": "2402.05165",
 "doi": "10.1051/0004-6361/202348463",
 "alma_projects_linked_by_archive": [
  "2012.1.00882.S",
  "2013.1.00273.S"
 ]
}
```

Paper text:
<paper>
# The cold molecular gas in $z\gtrsim 6$ quasar host galaxies

\[ISM\]interstellar medium \[SED\]Spectral Energy Distribution \[SFR\]star formation rate \[VLA\]Karl G. Jansky Very Large Array \[ALMA\]Atacama Large Millimeter/submillimeter Array \[NOEMA\]NOrthern Extended Millimeter Array \[VLT\]Very Large Telescope \[\]Common Astronomy Software Application (cite: 2022PASP..134k4501C) \[FWHM\]full width at half maximum \[IR\]infrared \[FIR\]far-infared \[UV\]ultraviolet \[rms\]root mean square \[S/N\]signal-to-noise ratio

Probing the molecular gas reservoirs of $z\gtrsim6$ quasar (QSO) host galaxies is fundamental to understanding the coevolution of star formation and black hole growth in these extreme systems. Yet, there is still an inhomogeneous coverage of molecular gas tracers for $z\gtrsim6$ QSO hosts.

To measure the average excitation and mass of the molecular gas reservoirs in the brightest $z>6.5$ QSO hosts, we combined new observations of CO(2–1) emission with existing observations of CO(6–5), CO(7–6), \[C I\] (2–1), \[C II\] 158 μm, and dust-continuum emission.

We reduced and analysed observations of CO(2–1), taken with the Karl G. Jansky Very Large Array, in three $z=6.5-6.9$ QSO hosts—the highest redshift observations of CO(2–1) to date. By combining these with the nine $z=5.7-6.4$ QSO hosts for which CO(2–1) emission has already been observed, we studied the spread in molecular gas masses and CO excitation of $z\gtrsim6$ QSOs.

Two of our three QSOs, P036+03 and J0305–3150, were not detected in CO(2–1), implying more highly excited CO than in the well-studied $z=6.4$ QSO J1148+5251. However, we detected CO(2–1) emission at $5.1\sigma$ for our highest-redshift target, J2348–3054, yielding a molecular gas mass of $(1.2\pm0.2)\times 10^{10}\, \mathrm{M}_\odot$, assuming $\alpha_\mathrm{CO} = 0.8$ (K km s$^{-1}$ pc$^2$)$^{-1}$ and $r_\mathrm{2,1}=1$. This molecular gas mass is equivalent to the lower limit on the dynamical mass measured previously from resolved \[C II\] 158 μm observations, implying that there is little mass in stars or neutral gas within the \[C II\]-emitting region and that a low CO-to-H$_2$ conversion factor is applicable. On average, these $z\gtrsim6$ QSO hosts have far higher CO(6–5)-, CO(7–6)-, and \[C II\] 158 μm versus CO(2–1) line ratios than the local gas-rich and IR-luminous galaxies that host active galactic nuclei, but with a large range of values, implying some variation in their interstellar medium conditions. We derived a mean CO(6–5)-to-CO(1–0) line luminosity ratio of $r_\mathrm{6,1}=0.9\pm0.2$.

Our new CO(2–1) observations show that even at 780 Myr after the Big Bang, QSO host galaxies can already have molecular gas masses of $10^{10}$ M$_\odot$, consistent with a picture in which these $z\gtrsim6$ QSOs reside in massive starbursts that are coevolving with the accreting supermassive black holes. Their high gas versus dynamical masses and extremely high line excitation imply the presence of extremely dense and warm molecular gas reservoirs illuminated by strong interstellar radiation fields.

# Introduction

First discovered in optical surveys in the early 2000s, luminous $z\gtrsim6$ quasars (QSOs) have challenged our understanding of how supermassive black holes (SMBHs) grow and coevolve with their host galaxies (cite: 2023ARA&A..61..373F). Studies of the optical and near-infrared (NIR) spectra of these QSOs reveal that they host SMBHs with masses of $\gtrsim10^9\,\mathrm{M}_\odot$ (cite: 2007AJ....134.1150J; 2007ApJ...669...32K; 2014ApJ...790..145D; 2015Natur.518..512W), implying the presence of enormous black hole seeds at $z>15$ and/or early episodes of super-Eddington accretion (cite: 2016PASA...33...51L; 2017MNRAS.468.5020I; 2021IAUS..356..261T). To understand how these SMBHs grow and impact star formation, it is crucial to constrain the mass and properties of their gas reservoirs. Doing so will also help reveal the evolutionary path of the gas-poor elliptical galaxies that host today’s most massive SMBHs (cite: 2013ARA&A..51..511K).

To discern the type of galaxies in which $z\gtrsim6$ QSOs reside, they have been observed at radio and (sub)millimetre wavelengths, where the emission from the host galaxies’ ism dominates that of the QSO. Observations of their dust-continuum emission have revealed that many of the hosts are bright in the far-infrared (FIR), with high FIR luminosities of $L_\mathrm{FIR} \sim 10^{12} - 10^{13}\,\mathrm{L}_\odot$, which have been interpreted as signatures of significant dust heating associated with high star formation rates (cite: 2003A&A...406L..55B; 2006ApJ...642..694B; 2007ApJ...671L..13R; 2017Natur.545..457D). The best studied of these appear to exhibit moderately high dust temperatures of $30-60$ K (cite: 2013ApJ...772..103L; 2023MNRAS.523.3119W) and dust masses of $\gtrsim 10^9\,\mathrm{M}_\odot$ (cite: 2017ApJ...851L...8V; 2019ApJ...876...99S; 2022ApJ...927..152M), implying large molecular gas masses of $\gtrsim 10^{10}\,\mathrm{M}_\odot$ (assuming similar or higher gas-to-dust mass ratios than in the Milky Way) and efficient supernova dust production (cite: 2010A&A...522A..15M; Gall_2011; 2012MNRAS.424L..34K). Observations of the dominant ISM coolant, \[C II\] 158 μm, also show this emission to be bright, again indicating high SFRs (cite: 2009Natur.457..699W; 2012ApJ...751L..25V; 2013ApJ...773...44W; 2015ApJ...805L...8B; 2016ApJ...816...37V). Combined with the underlying continuum emission, these results yield \[C II\]/FIR luminosity ratios similar to high-redshift starbursts and local Ultra-Luminous Infrared Galaxies (ULIRGS). Moreover, the recent wealth of resolved studies of \[C II\] (cite: Willott_2017; 2019ApJ...880....2W; 2020ApJ...904..130V; 2020ApJ...904..131N; 2021ApJ...911..141N), most recently pushing down to scales of $\sim 200-300$ pc (cite: 2022ApJ...927...21W; 2023ApJ...956..127M), have revealed the presence of some rotating gas disks, in which most of the gas is concentrated in highly compact, central regions.

For some $z\gtrsim6$ QSO hosts, observations of the warm and dense molecular gas component traced by CO(6–5) and/or CO(7–6) emission have also revealed the presence of massive molecular gas reservoirs of $\sim10^{10}\,\mathrm{M}_\odot$ (cite: 2003A&A...409L..47B; 2007ApJ...666L...9C; 2010ApJ...714..699W; 2011AJ....142..101W; 2013ApJ...773...44W; 2017ApJ...845..154V). Yet, converting these observations to a molecular gas mass requires robust constraints on the CO excitation ladders. To test how much molecular gas is in the cold/diffuse state and hence correctly calibrate the CO excitation for these $z\gtrsim6$ QSO hosts, it is critical to also observe their low-$J$ ($J=1,2$) CO emission. But low-$J$ CO emission is intrinsically much fainter than the mid-$J$ CO and \[C II\] emission. To date, nine QSOs at $z=5.7-6.4$ have observations of CO(2–1) emission (cite: 2010ApJ...714..699W; 2011ApJ...739L..34W; 2015MNRAS.451.1713S; 2016ApJ...830...53W; 2019ApJ...876...99S). In combination with their previously detected CO(5–4), CO(6–5), and/or CO(7–6) emission, these observations have revealed the presence of highly-excited CO, with what seems to be a dearth of diffuse cold gas.

To continue systematically exploring the molecular gas reservoirs of $z\gtrsim6$ QSO host galaxies, we used the vla to observe the CO(2-1) emission of three QSOs with existing observations of CO(6–5), CO(7–6), \[C I\] and \[C II\] emission (cite: 2015ApJ...805L...8B; 2016ApJ...816...37V; 2017ApJ...851L...8V). By combining these lines, we robustly measured their molecular mass, anchored the CO excitation, and compared their ISM properties to those of highly star-forming galaxies and QSO hosts at lower redshift.

This paper is organised as follows. In Section [2](#sec:data), we present the VLA observations of our three QSO hosts and present the literature sample. In Section [3](#sec:analysis), we infer physical properties from these observations. We place these properties in the context of other galaxy samples in Section [4](#sec:results), and discuss the physical implications in Section [5](#sec:discussion). In Section [6](#sec:conclusions), we present a short summary. Throughout this work, we adopt a Lambda–cold dark matter cosmology, with $H_0 = 70$  km s$^{-1}$ Mpc$^{-1}$, $\Omega_M = 0.3$, and $\Omega_\lambda = 0.7$.

# Observations and data reduction

## Sample

In this work, we reduce the CO(2–1) observations of P036+03 (at $z=6.54$), J0305–3150 (at $z=6.61$), and J2348–3054 (at $z=6.90$). P036+03 was originally identified as part of the Panoramic Survey Telescope & Rapid Response System 1 (Pan-STARRS1) (cite: 2015ApJ...801L..11V) whereas the other two QSOs were identified from the VISTA Kilo-Degree Infrared Galaxy Survey (VIKING) (cite: 2013ApJ...779...24V). Their coordinates and previously derived properties are provided in Table [\[tab:source_prop\]](#tab:source_prop).

|  | P036+03 | J0305–3150 | J2348–3054 |
|:---|:---|:---|:---|
| **Coordinates and BH properties** |  |  |  |
| RA (J2000) | :26:01.875 | :05:16.91 | :48:33.34 |
| DEC (J2000) | :02:59.40 | :50:55.9 | :54:10.24 |
| z$_\mathrm{MgII}$ | $6.527\pm0.002$ | $6.605\pm0.002$ | $6.889\pm0.007$ |
| $M_\mathrm{BH}$ ($\times 10^9\,\mathrm{M}_\odot$) | $2.7 \pm 0.5^a$ | $0.8 \pm 0.2^b$ | $3.2^{+1.2}_{-0.9}$$^{,b}$ |
| $L_\mathrm{bol}$ ($\times 10^{13}$ L$_\odot$) | $6.47\pm0.04^c$ | $2.45\pm0.03^c$ | $1.93\pm0.05^c$ |
| **Previous sub-/mm observations** |  |  |  |
| z$_\mathrm{[C\,\textsc{ii}]}$ | $6.541\pm0.002$ | $6.6145\pm0.0001$ | $6.9018\pm0.0007$ |
|  158 μm flux (Jy $\rm{km}\, \rm{s}^{-1}$) | $3.16\pm0.09\,^d$ | $5.25\pm0.30\,^e$ | $1.53\pm0.16\,^{f,d}$ |
| FWHM$_\mathrm{[C\,\textsc{ii}]}$ (km s$^{-1}$) | $237\pm10\,^d$ | $268\pm20\,^e$ | $457\pm50\,^d$ |
| Underlying ($\sim 1$ mm) continuum flux density (mJy) | $2.55\pm0.05\,^d$ | $5.34\pm0.13\,^d$ | $2.28\pm0.07\,^f$ |
| z$_\mathrm{CO, [CI]}$ | $6.5410\pm0.0003$ | $6.6139\pm0.0005$ | $6.9007\pm0.0005$ |
| CO(6-5) flux (Jy $\rm{km}\, \rm{s}^{-1}$) | $0.35\pm0.03\,^g$ | $0.63\pm0.04\,^e$ | $0.28\pm0.05\,^f$ |
|  (2–1) flux (Jy $\rm{km}\, \rm{s}^{-1}$) | $0.21\pm0.04\,^g$ | $0.25\pm0.03\,^e$ | $0.16\pm0.06\,^f$ |
| CO(7-6) flux (Jy $\rm{km}\, \rm{s}^{-1}$) | $0.40\pm0.04\,^g$ | $0.55\pm0.04\,^e$ | $0.26\pm0.06\,^f$ |
| Underlying ($\sim 3$ mm) continuum flux density (mJy) | $0.13\pm0.02\,^g$ | $0.27\pm0.02\,^e$ | $0.12\pm0.01\,^f$ |
| CO(10-9) flux (Jy $\rm{km}\, \rm{s}^{-1}$) | $0.38\pm0.08\,^*$ | ... | ... |
| **Previously measured sizes** |  |  |  |
| deconv. \[C II\] 158 μm size (kpc) $^d$ | $2.4\pm1.6$ | $2.8\times2.6$ | $1.0\times0.5$ |
| $2\, r_\mathrm{half,[C\,\textsc{ii}]}$ (kpc) $^{h,i}$ | $2.3\pm0.1$ | $3.6\pm0.1$ | $0.88\pm0.03$ |
| **VLA observations** |  |  |  |
| Beam FWHM ($"$) | $1.00 \times 0.77$ | $1.86 \times 0.74$ | $1.49 \times 0.68$ |
| Beam FWHM (kpc) | $5.5 \times 4.2$ | $10.2 \times 4.0$ | $9.6 \times 3.8$ |
| rms over channels of 1.2 FWHM$_\mathrm{[CII]}$ (mJy beam$^{-1}$) |  |  |  |
| CO(2-1) flux (Jy $\rm{km}\, \rm{s}^{-1}$) | **$<0.05^{4\sigma}$** | **$<0.06^{4\sigma}$** | $0.04\pm0.01$ |
| **Derived dust and molecular gas masses** |  |  |  |
| $M_\mathrm{mol, CO(2-1)}$ (M$_\odot$) | $<1.2\times10^{10}$ | $<1.6\times10^{10}$ | $(1.2\pm0.2)\times10^{10}$ |
| $M_\mathrm{mol, [C I](2-1)}$ (M$_\odot$) | $(1.9\pm0.9)\times10^{10}$ | $(2.4\pm1.0)\times10^{10}$ | $(1.6\pm0.9)\times10^{10}$ |
| $M_\mathrm{dust}$ (M$_\odot$) | $(1.2\pm0.7)\times10^{8}$ | $(2.3\pm0.7)\times10^{9}$ | $(1.1\pm0.6)\times10^{8}$ |

25pt25pt **References:** $^a$ (cite: 2023A&A...676A..71M), $^b$ (cite: 2022ApJ...941..106F), $^c$ (cite: Schindler_2020),

$^d$ (cite: 2020ApJ...904..130V), $^e$ (cite: 2022ApJ...930...27L), $^f$ (cite: 2017ApJ...851L...8V), $^g$ (cite: 2022A&A...662A..60D),

$^h$ (cite: 2021ApJ...911..141N), $^i$ (cite: 2022ApJ...927...21W), $^*$from a Gaussian fit to the spectrum extracted from the NOEMA observations of programmes S15DA and W15FD (also used in (cite: 2022A&A...662A..60D))

The ISM emission of the three QSOs was first observed via the \[C II\] 158 μm and FIR emission, obtained as part of two programmes. P036+03 was observed with the NOEMA interferometer (cite: 2015ApJ...805L...8B), whereas the two, higher redshift QSOs from VIKING, were observed with ALMA (cite: 2016ApJ...816...37V). For J0305–3150 and J2348–3054, observations of the CO(6–5), CO(7–6), and \[C I\] (2–1) emission were conducted with ALMA (cite: 2017ApJ...845..154V) and for P036+03 observations of CO(6–5), CO(7–6), \[C I\] (2–1), and CO(10–9) emission were conducted with NOEMA (cite: 2022A&A...662A..60D).

## Observations

The CO(2–1) observations analysed here were taken as part of the VLA programmes, 16A-160 and 17A-336 (PI: Venemans). For programme 16A-160, 11 observational blocks were conducted between 2016/03/04 and 2017/05/17, resulting in 10 h of observations of J2348–3054, 2 h of J0305–3150 and no observations of P036+03. To complete the experiment, 20 further observational blocks were requested as part of the programme 17A-336, with 18 h to be spent on J2348–3054, 12 h on J0305–3150 and 10 h on P036+03. This supplementary programme was carried out in full between 2017/05/20 and 2017/08/08. Across the two programmes, almost all observation blocks were carried out in the C configuration, with one instead conducted in the B configuration. All observations were carried out in the Ka Band, spanning 26.5–40 GHz.

We performed bandpass and flux calibrations using observations of 3C48 (for J0305–3150 and J2348–3054) and 3C147 (for P036+03). Phase and amplitude calibrations were performed using observations of J0201+0343, J0348-2749, and J2359-3133 (for P036+03, J0305–3150 and J2348–3054 respectively). The total on-source integration times for the three targets were 5.3 h, 7.42 h, and 14.84 h (for P036+03, J0305–3150, and J2348–3054 respectively). The synthesised beam sizes and $1\sigma$ root-mean-square (rms) noise values are provided in Table [\[tab:source_prop\]](#tab:source_prop).

![image](P036+03_284kms_3channel_map.pdf)   ![image](CO21_spectrum_P036+03_2.pdf)\
![image](J0305-3150_321kms_3channel_map.pdf)   ![image](CO21_spectrum_J0305-3150_2.pdf)\
![image](J2348-3054_548kms_3channel_map.pdf)   ![image](CO21_spectrum_J2348-3054_2.pdf)\

## Data reduction

To calibrate the data from each two-hour observation set, we used the casa pipeline version 5.6.2 as described in <https://science.nrao.edu/facilities/vla/data-processing/pipeline#section-26> (that is, we included most of the standard calibration tasks and disabled the application of Hanning smoothing). After examining the calibrated data, we performed additional flagging, removing the RFI at 29.43 GHz remaining in the observation sets of J2348–3054 and the poor individual antenna data for short time windows in two observation sets (one for J0305–3150 and one set for J2348–3054). This leads to some of the gaps in data in the spectra of Fig. [1](#fig:channelmaps).

To test whether the CO(2–1) emission is detected, we made three-channel cubes, by integrating each channel over $1.2\times$ the fwhm of the previously detected \[C II\] 158 μm line emission (see Table [\[tab:source_prop\]](#tab:source_prop)) and centring the frequency range on the CO(6–5)-derived redshift. Assuming that the CO(2–1) emission has the same linewidth as \[C II\] 158 μm and systemic velocity of the other CO transitions, this velocity range should encompass 84% of the CO(2–1) emission. We applied a natural weighting scheme and cleaned down to $2\sigma$ within $3\ensuremath{''}$ of the source centre. These cleaned maps are shown in Fig. [1](#fig:channelmaps), with the beam properties and rms values provided at the bottom of Table [\[tab:source_prop\]](#tab:source_prop). Using the same central frequency, we also created image cubes of 100 km s$^{-1}$, cleaning down to $2\sigma$ and applying natural weighting. The spectra extracted from the single pixel corresponding to the peak in the moment-0 maps of these cubes, are shown in the right panels of Fig. [1](#fig:channelmaps).

## Line fluxes and upper limits

We tested whether the CO(2–1) emission of the three QSO hosts was detected using the moment-0 maps described above. For our highest-redshift target, J2348–3054, we detect a $5.1\sigma$ peak in emission, consistent with the expected source position. We find a $3.3\,\sigma$ peak offset by $0.43\ensuremath{''}$ (2.4 kpc) from the source centre for P036+03; however, other peaks of emission exceeding this value are apparent in the integrated channel maps at the same frequency and in the channels on either side. Thus, we treat it as an upper limit. Likewise, we detect no CO(2–1) emission for J0305–3150, with a peak value near the source centre of $2.6 \,\sigma$. At a spectral resolution of 100 km s$^{-1}$, none of the three sources exceed $\mathrm{S/N}=3$ across the expected line width. Moreover, none of the three QSOs targeted show any evidence of continuum emission, nor is there any spectrally offset CO(2–1) emission. We also searched for evidence of the companions reported in (cite: 2020ApJ...904..130V), but find nothing exceeding $\sim2.5 \,\sigma$ at the expected positions and frequencies.

Based on the moment-0 maps, we treated the CO(2–1) emission from J2348–3054 as a significant detection and derived $4\sigma$ upper limits for the other two sources, consistent with our detection threshold. We derived the line flux measurement for J2348–3054 by first measuring the value of the single pixel at the peak position ($0.3\ensuremath{''}$ offset from the source centre quoted in Table  [\[tab:source_prop\]](#tab:source_prop)) in the central channel of the bottom row in Fig. [1](#fig:channelmaps), multiplying by the channel width, and accounting for the extra 16% of the line flux not included in $1.2\,\times$ FWHM. To derive the upper limits, we measured the root mean square (rms) of the moment-0 map, also multiplying this value by $1.2\,\times$ FWHM$_\mathrm{[CII]}$, accounting for the extra 16%, and multiplying by our detection threshold of $4\sigma$. We also accounted for potentially extended emission underlying the noise, assuming that the CO(2–1) emission arises from the same size region as the \[C II\] 158 μm emission. We deem it unlikely that the CO emission would be significantly more extended than the \[C II\] 158 μm emission (cite: 2011ApJ...739L..32R). To test how much flux we would miss by deriving an upper limit (line flux) from only the pixel rms (peak pixel value), we followed the approach of (cite: 2020MNRAS.499.5136C). That is, we simulated both a point source and extended (Gaussian) emission, using the \[C II\] 158 μm size ($2\,r_\mathrm{1/2,[C~II]}$, Table [\[tab:source_prop\]](#tab:source_prop)), position angle, and inclination measured for each galaxy. We then performed mock VLA observations under the same configuration used for the real observations and compared the flux extracted from the peak pixel for both the point source and extended source. We performed noise-free tests to accurately recover the difference between the flux of the point versus extended source (which we cannot recover from our data). Based on this modelling, we found that for P036+03, we would miss 15% of the flux if the CO(2–1) emission is as extended as the \[C II\] 158 μm emission. Similarly, for J0305-3150, we would miss 19% of the flux. We added these potentially missing extended components when deriving the $4\sigma$ upper limits, based on the rms. For J2348-3054, the peak pixel extraction for the extended source is equivalent to that of the point source (only 0.004% less), because the CO(2–1) beam ($7.8 \times 3.6$ kpc), is significantly larger than twice the measured \[C II\] 158 μm half-light radius ($\sim 0.8$  kpc) (cite: 2021ApJ...911..141N). This is also consistent with the fact that the CO(2–1) emission from J2348–3054 is well fit by a (convolved) point source and the flux extracted from this point source matches that extracted from a larger circular aperture of $2.5\ensuremath{''}$. Thus, we performed no correction for any missing flux for J2348–3054.

Given the low S/N of these observations, we derived the CO(2–1) line flux density and upper limits assuming that the CO(2–1) line width is the same as that measured for the much higher S/N \[C II\] 158 μm emission; that is, we use the highest S/N prior we have. This seems to be a reasonable assumption, as for most of the $z>5$ QSO host galaxies detected at $>5\sigma$ in both CO(2–1) and \[C II\] 158 μm, the reported FWHM values of the two lines have been consistent within uncertainties (cite: 2013ApJ...773...44W; 2016ApJ...830...53W; 2019ApJ...876...99S; 2022A&A...664A..39K; 2022ApJ...927..152M). Although we use the most recent measurements of the \[C II\] 158 μm line FWHM (cite: 2020ApJ...904..130V; 2022ApJ...930...27L) for the integrated CO(2–1) line flux density and upper limits, we also tested our results using the values derived in the original studies that reported the \[C II\] 158 μm detections (cite: 2015ApJ...805L...8B; 2016ApJ...816...37V). The integrated CO(2–1) line flux densities (hereafter simply ‘line fluxes’) and upper limits remain consistent, within errors. However, the S/N of the detection of J2348–3054 increases with the wider FWHM measured in (cite: 2020ApJ...904..130V) versus (cite: 2016ApJ...816...37V).

# Derived quantities

## Line luminosities and dust properties

For the three galaxies studied here, and for the comparison samples, we computed the line luminosities as $$\begin{align}
                L_\mathrm{line}^\prime = 3.25\times 10^7 S_\mathrm{line} \Delta v \dfrac{D_L^2}{(1+z)^3 \nu_\mathrm{obs}^2} ~ \mathrm{K~km~s^{-1}~pc^2}
            
\end{align}$$ where $D_L$ is the luminosity distance in Mpc, $\nu_\mathrm{obs}$ is the observed central frequency of the line in GHz and $S_\mathrm{line} \Delta v$ is the line flux in Jy km s$^{-1}$.

At the redshift of these QSOs, the high temperature of the cosmic microwave background (CMB) may have a pronounced effect on the observed CO line fluxes, becoming a strong background against which lines are measured as well as potentially boosting the higher- versus lower-$J$ transitions (cite: 2013ApJ...766...13D; 2016RSOS....360025Z; 2016ApJ...819..161T). We therefore derived both CMB-corrected and uncorrected values for the CO line luminosities. As shown in (cite: 2013ApJ...766...13D), the ratio of the observed versus intrinsic line flux depends on the temperature and density of the gas. To perform the CMB corrections, we adopted their non-LTE, high-density ($n_\mathrm{H_2}=10^{4.2}$ cm$^{-3}$) and high-temperature ($T_\mathrm{kin}=40$ K) scenario. In their model, they assume that the kinetic temperature of the gas is coupled to that of the dust: $T_\mathrm{k} = T_\mathrm{d}$. Thus, we partly motivate the choice of this scenario by the high inferred dust temperatures ($\sim$40 K), as well as the compact gas reservoirs and high observed line ratios, which imply high densities and temperatures (see Sec. [5](#sec:discussion)). Adopting this correction, the fraction of CO(2–1) line flux observed against the CMB, $f_\mathrm{CMB}$, for P036+03, J0305-3150, and J2348-3054 is 0.56, 0.55, and 0.53 (respectively), whereas the fraction of CO(6–5) observed against the CMB is 0.67, 0.65, and 0.64 (respectively). This additional correction results in higher intrinsic line fluxes, and hence luminosities, than without the CMB correction.

We also refit the dust SEDs, ensuring that we take into account the effects of the CMB by adopting a similar approach to (cite: 2021ApJ...919...30D) and (cite: 2022ApJ...927..152M) (see Appendix [8](#sec:dust_sed_fitting)). We fit the dust SEDs with a modified blackbody, assuming optically thin dust emission at $\lambda>40$ μm. Our method accounts for the effects of the CMB, correcting for both the heating by and contrast against the CMB (as prescribed by (cite: 2013ApJ...766...13D)) and includes the most up-to-date continuum data. In this way, we obtained new values for the FIR luminosities, dust masses, dust temperatures, and emissivity indices of all $z\gtrsim6$ QSO hosts, including our three and the literature sample (Table [\[tab:dust_sed\]](#tab:dust_sed)). We note that in most cases, the dust temperatures and emissivity indices remain unconstrained due to the limited number of continuum data points. For these, the errors on the dust masses and FIR luminosities ($L_\mathrm{FIR}$) are higher, taking into account the full prior range on $T_\mathrm{dust}$ and $\beta$. We provide two sets of $L_\mathrm{FIR}$ values to ease the literature comparison, integrating between 40-400 μm and 42.5-122.5 μm (e.g. as in (cite: Liu_2015) versus (cite: 2011A&A...530L...8D)).

If the QSO host galaxies have high dust columns, the dust may actually be optically thick at $\lambda>40$ μm, contrary to our assumption. Given the large dust masses of $10^8-10^9$ M$_\odot$ inferred here (albeit for the optically thin assumption) and small galaxy sizes of $r_\mathrm{half}\sim 1$  kpc (as in the measurements for the highest-quality \[C II\] 158 μm observations of J2348+3054, (cite: 2022ApJ...927...21W)) this is certainly plausible. As shown by (cite: 2021ApJ...919...30D), accounting for the wavelength up to which dust remains optically thick ($\lambda_\mathrm{thick}=60-140$ μm for their sample) has the effect of shifting the best-fit dust temperatures of their sample 10 K higher, on average, and dust masses to a few times lower values. However, the derived FIR luminosities and $\beta$ remain practically the same. Thus, our $L_\mathrm{FIR}$ should not change significantly in the case of optically thick dust emission but our dust temperatures and masses may be biased to slightly lower and higher values, respectively.

![](Mmol_comp_ULIRGalphaCO_2.pdf)

![](mass_comp_ULIRGalphaCO.pdf)

## Molecular gas masses

We derived the molecular gas masses from the CO(2–1) emission assuming that the low-$J$ emission is thermalised, $L_\mathrm{CO(2-1)}^\prime = L_\mathrm{CO(1-0)}^\prime$, as in low-redshift QSOs (cite: 2023arXiv231010235M). To convert $L_\mathrm{CO(1-0)}^\prime$ to a molecular gas mass, we assumed an intrinsic ULIRG-like $\alpha_\mathrm{CO}=0.8$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$, as derived in (cite: Downes_1998) (for ULIRG centres) based on resolved CO(2–1) or CO(1–0) observations of 10 local ULIRGs. These low values were found to be necessary in order for the molecular gas masses not to exceed the inferred dynamical masses. Similarly, early comparisons of dynamical mass estimates and CO-derived molecular gas masses in $z\gtrsim6$ QSO hosts motivated the choice of such low $\alpha_\mathrm{CO}$ also in these systems (cite: 2003Natur.424..406W; 2004ApJ...615L..17W). Following the majority of the literature on $z\gtrsim6$ QSOs (cite: 2013ARA&A..51..105C), we adopted the same value but it is important to note that this may need to be adjusted in future, once robust constraints on $\alpha_\mathrm{CO}$ can be determined for each QSO. For example, by modelling the multi-line and continuum emission, (cite: 2021ApJ...908...95H) show that for systems in which the CO gas column density is mostly traced by higher-$J$ lines, $\alpha_\mathrm{CO}$ is shifted to higher values. We also inferred the molecular gas masses based on the CMB-corrected CO(2–1) emission (see Sec. [3.1](#sub:luminosities)). This additional correction results in a higher intrinsic molecular gas masses than without the CMB correction (although for lower assumed temperatures and densities these corrections would be much larger). In effect, this additional CMB correction leads to an increased $\alpha_\mathrm{CO}$, that is $\alpha_\mathrm{CO, tot.} = \alpha_\mathrm{CO, intr.} / f_\mathrm{CMB}$. Thus, Milky-Way-like values of $\alpha_\mathrm{CO}\sim 4\,\mathrm{M}_\odot$(K km s$^{-1}$ pc$^2$)$^{-1}$ are feasible for host galaxies with lower average molecular gas temperatures or densities than in the model we have assumed here.

Dust emission can also be used as a molecular gas tracer, as long as the dust temperature, emissivity index, and dust-to-gas ratios can be well-constrained or safely assumed (cite: Groves_2015; 2016ApJ...820...83S; 2018MNRAS.478L..83L). In this work, we derived the molecular gas masses from the dust masses fit here (see Appendix [8](#sec:dust_sed_fitting)). To derive molecular gas masses, we scaled the dust masses by the local gas-to-dust ratio of 100 (cite: 2007ApJ...663..866D), which has been found to be consistent with some $z\gtrsim6$ QSO hosts (cite: 2016ApJ...830...53W; 2022A&A...662A..60D; Feruglio_2023).

In recent years, atomic carbon, \[C I\], has also garnered significant attention as a potentially reliable and efficient molecular gas tracer for $z>2$ star-forming galaxies (cite: 2011ApJ...730...18W; 2013MNRAS.435.1493A; 2017MNRAS.466.2825B; 2017PhDT........21Y; 2018A&A...615A.142A; 2018ApJ...869...27V; 2019A&A...624A..23N). At these high redshifts, the two \[C I\] transitions are shifted to millimetre wavelengths and can be detected in less time than CO(2–1). Unlike for $^{12}$CO, \[C I\] emission has mostly been found to be optically thin, (cite: 2002ApJS..139..467I; 2003A&A...409L..41W; 2021ApJ...908...95H), potentially making it a more straightforward tracer. Moreover, \[C I\] emission is widespread within clouds, stemming from both the cloud interiors and surfaces (cite: 2002ApJS..139..467I; 2008A&A...477..547K; 2015ApJ...803...37B; 2017ApJ...839...90B; 2015MNRAS.448.1607G; 2019MNRAS.486.4622C). \[C I\] has therefore been proposed to be a more reliable molecular gas tracer than low-$J$ CO emission in diffuse and/or metal-poor gas (cite: 2004MNRAS.351..147P; 2016MNRAS.456.3596G).

To derive molecular gas masses from the observed \[C I\] (2–1) emission, we assumed the \[C I\] emission is optically thin, and in LTE (cite: 2005A&A...438..533W). In this case, the mass of neutral carbon is given by, $$\begin{align}
                \dfrac{M_\mathrm{CI}}{\mathrm{M}_\odot} = \dfrac{4.556}{10^4} \dfrac{Q_\mathrm{ex}}{5} \exp(62.5/T_\mathrm{ex}) \dfrac{L_\mathrm{[CI]2-1}^\prime}{\mathrm{K~km~s^{-1}}} \, 
            
\end{align}$$ where $Q_\mathrm{ex} = 1+3\exp(-23.6/T_\mathrm{ex}) + 5\exp(-62.5/T_\mathrm{ex})$ is the partition function and $T_\mathrm{ex}$ is the excitation temperature. We assumed the atomic carbon is in thermal equilibrium with the dust, with the average dust temperature typically quoted in the literature, $T_\mathrm{ex} = 47$  K (cite: 2006ApJ...642..694B; 2014ApJ...785..154L). If we instead assume $T_\mathrm{ex} =$ 30 K, the \[C I\]-derived molecular gas masses would be 1.5$\times$ the values presented here, whereas if we assume $T_\mathrm{ex} =$ 100 K the molecular gas masses would be 0.8$\times$ our values, therefore making little difference to the derived values.

To convert the atomic carbon mass to a molecular gas mass, we applied the mean atomic carbon abundance of $\left<\mathrm{[C I]/H_2}\right>=(6.82\pm3.04)\times10^{-5}$, measured by (cite: 2021ApJ...908...95H) for their sample of 18, $z=2-3$ lensed starburst galaxies with \[C I\] observations. This value is consistent with the implied high value of $7\times 10^{-5}$ found by (cite: 2017MNRAS.466.2825B) for their sample of 13 lensed $z\sim 4$ dusty star-forming galaxies, when assuming the same low $\alpha_\mathrm{CO}$ as in this work. However, these values are higher, on average, than those measured for less IR-luminous, main-sequence star-forming galaxies at $z=1.2-2.5$. For example, (cite: 2020ApJ...902..109B) derive a value of \[C I\]/H$_2 = (1.9 \pm 0.4) \times 10^{-5}$ based on the \[C I\] detections of six main-sequence star-forming galaxies, and (cite: 2018ApJ...869...27V) find a value of \[C I\]/H$_2 = (1.6 \pm 0.8) \times 10^{-5}$ for their sample of $z=1.2$ main-sequence galaxies. These lower values may be attributed to the difference in physical conditions (e.g. cosmic ray, X-ray, and/or mechanical heating effects) and/or the calibration methods.[^1] We take the value of (cite: 2021ApJ...908...95H) here since their sample are comprised of starbursts, and thus are more similar to the $z\gtrsim6$ QSO hosts studied to date (cite: 2011AJ....142..101W; 2016ApJ...830...53W; 2019ApJ...876...99S). Moreover, they do not assume an $\alpha_\mathrm{CO}$, but instead model the $\alpha_\mathrm{CO}$ and \[C I\] abundance simultaneously.

\[C II\] 158 μm has been proposed as an even more efficient molecular gas tracer for high-redshift and metal-poor galaxies (cite: 2018MNRAS.481.1976Z; 2020A&A...643A.141M). However, as a multi-phase gas tracer, \[C II\] 158 μm emission is an indirect probe of the bulk of the cold, molecular gas and has not yet been systematically tested against more common molecular gas tracers at $z>6$. To infer the molecular gas masses from \[C II\], we applied the mean conversion factor from the calibration of (cite: 2018MNRAS.481.1976Z), $\alpha_\mathrm{[C II]}=31\,\mathrm{M}_\odot/\mathrm{L}_\odot$, folding in the 0.3 dex standard deviation around this value as the uncertainty. (cite: 2018MNRAS.481.1976Z) derive this value based on a comparison of molecular gas masses versus \[C II\] 158 μm emission. For most of the $z=1-5$ main-sequence and starburst galaxies underlying their empirical calibration, the molecular gas masses were derived from CO observations. However, for the local starbursts underlying this calibration, the molecular gas masses were instead mostly derived using relations between the depletion timescale ($t_\mathrm{depl}=M_\mathrm{mol}/SFR$) and specific star formation rate, sSFR (see Sec. [4.1](#sub:molecular_gas_masses)).

# Results

## Molecular gas mass comparison

Based on the molecular gas mass comparison shown in Fig. [2](#fig:Mmol_comp), we find that the CO(2–1)-based molecular gas masses of the three, $z=6.6-6.9$ QSO hosts studied here (top three) are consistent with the $z=5.7-6.4$ QSO hosts with existing CO(2–1) measurements (cite: 2010ApJ...714..699W; 2011ApJ...739L..34W; 2015MNRAS.451.1713S; 2016ApJ...830...53W; 2019ApJ...876...99S), with $M_\mathrm{mol}\sim(0.8-4.5)\times 10^{10}\,\mathrm{M}_\odot$. Even our newly CO(2–1)-detected QSO host, J2348–3054 at $z=6.9$, already has a molecular gas mass of $\sim 1\times 10^{10}\,\mathrm{M}_\odot$. The fact that these extremely IR-bright $z\gtrsim 6$ QSO hosts all have similarly massive molecular gas reservoirs implies that there is something about these systems that enables massive molecular gas reservoirs to form very rapidly. It also implies that the radiation from the rapidly accreting SMBHs is not dissociating significant amounts of CO.

In Fig. [2](#fig:Mmol_comp), we compare the CO(2–1)-derived masses to those inferred from \[C I\] (2–1), \[C II\] 158 μm and dust-continuum emission. We find that the molecular gas masses inferred from the dust mass measurements are mostly consistent with those inferred from CO(2–1), implying that, on average, the gas-to-dust ratios are consistent with, or only somewhat higher than, the assumed Milky Way value of 100 (also shown in Fig. [3](#fig:mass_comp)). The only two exceptions, J0305–3150 and J2310+1855, are systems for which the best-fit dust temperatures are low ($\lesssim 30$ K). It may be that for these galaxies, the gas-to-dust ratios are actually lower (implying more plentiful dust), or that the best-fit solution is inaccurate due to optical depth effects or, poor sampling of the dust SED for J0305–3150.

For our our three $z>6.5$ QSO hosts, and J1148+5251 (cite: 2009ApJ...703.1338R; 2015MNRAS.451.1713S), we find that the \[C I\] (2–1)-derived molecular gas masses are consistent with the CO(2–1)-derived values, when assuming both the ULIRG $\alpha_\mathrm{CO}$ value and the high atomic carbon abundance measured in (cite: 2021ApJ...908...95H). If we instead applied a Milky-Way-like $\alpha_\mathrm{CO}$, the \[C I\]-derived molecular gas masses would be $\sim5\times$ lower in comparison. In that case, the lower carbon abundances measured by (cite: 2020ApJ...902..109B) and (cite: 2018ApJ...869...27V) would be appropriate. If the assumed $\alpha_\mathrm{CO}$ is correct, this comparison indicates that the gas in these QSO hosts may be highly carbon enriched and/or subject to several sources of strong heating. We discuss the implications, including additional effects that complicate this comparison, in Sec. [5](#sec:discussion).

In contrast to the other tracers, we find that the \[C II\] 158 μm-based molecular gas masses are systematically higher than those derived from the CMB-uncorrected CO(2–1), by a factor of $6.8\pm1.9$ (mean and standard deviation for the whole sample of $z\gtrsim6$ QSO hosts). For J2348–3054, the \[C ii\]-derived value is 4.6$\times$ that of the CO(2–1) derived value. Assuming the other values are accurate, this implies that the mean conversion factor derived for local and high-redshift galaxies, $\alpha_\mathrm{[CII]} = 31\,\ensuremath{\rm{M}_{\odot}}/L_{\odot}$, is too high for these $z\gtrsim6$ QSO host galaxies. This may be because $\alpha_\mathrm{[CII]}$ is still uncertain for such highly star-forming galaxies. At high sSFR, the calibration from (cite: 2018MNRAS.481.1976Z) mostly relies on local starbursts taken from (cite: 2017ApJ...846...32D), which were without CO observations. To derive the molecular gas masses of this sample (and hence calibrate these against the \[C II\] 158 μm luminosity), (cite: 2018MNRAS.481.1976Z) rely on two literature scaling relations between the depletion time and sSFR—those of (cite: Sargent_2014) and (cite: 2017ApJ...837..150S)—comparing the calibration derived from the average of the two, and from (cite: 2017ApJ...837..150S) only (see Fig. 9 of (cite: 2018MNRAS.481.1976Z)). When also using the (cite: Sargent_2014) relation (which is based on a metallicity-dependent $\alpha_\mathrm{CO}$) they find $\alpha_\mathrm{[CII]}$ values of $\leq10$ at the highest sSFRs ($\mathrm{sSFR/sSFR_{MS}}>10$). Thus, they also derive some values consistent with what we find for the $z\gtrsim 6$ QSO host galaxies, depending on the assumed scaling relation.

## Mass budget

In Fig. [3](#fig:mass_comp), we compare the molecular gas masses derived here against the other main mass components of the QSO host galaxies—the dust, black hole, and total (dynamical) mass. We use the dust masses derived here (Sec. [3.1](#sub:luminosities) and Appendix [8](#sec:dust_sed_fitting)). For the black hole masses of our three QSOs, we take the measured values from (cite: 2023A&A...676A..71M) and (cite: 2022ApJ...941..106F), which were derived from Mg II following the method from (cite: 2011ApJS..194...45S). Likewise for the literature sample, we take the Mg II-based values from (cite: 2019ApJ...873...35S), (cite: 2022ApJ...941..106F), and (cite: 2023A&A...676A..71M). For the dynamical mass estimates, we take the values derived by (cite: 2021ApJ...911..141N), based on $0.25\ensuremath{''}$ observations of \[C II\] 158 μm emission. These dynamical masses were estimated from the best-fit \[C II\] 158 μm half-light radius, rotation velocity, and velocity dispersion (where these values were fit using the parametric kinematic fitting code, `qubefit`; (cite: qubefit)).

Assuming a ULIRG-like $\alpha_\mathrm{CO}$, the CO(2–1)-derived gas masses (opaque filled symbols with errorbars in Fig. [3](#fig:mass_comp)) are 3-11 times greater than the black hole masses, $20-190\times$ greater than the dust masses, and $0.1-1\times$ the dynamical masses. In order for the CO(2–1)-derived molecular gas masses (and upper limits) of the three QSOs studied here not to exceed the estimated dynamical masses, the applied CO-to-H$_2$ conversion factors need to be low, similar to the ULIRG value we have adopted. This also means that only a minimal CMB correction (as for the non-LTE, high temperature and density case assumed here) is required. In particular for J2348–3054, the molecular gas mass is almost equivalent (0.98$\times$) to the lower limit on the dynamical mass of $\geq1.2\times10^{10}\,\mathrm{M}_\odot$, whereas the black hole mass is $(3.3\pm1)\times 10^9\,\mathrm{M}_\odot$. If the dynamical masses are reliable, the CO(2–1)-derived molecular gas masses also imply that the molecular gas in most of these systems, especially in J2348–3054, dominates the mass budget, leaving barely any mass in neutral gas or stars within the region traced by \[C II\] 158 μm.

Our finding that the molecular gas comprises a large fraction of the total mass, at least in the central regions, is consistent with earlier findings for some of the literature sample and for J2348–3054 based on dynamical modelling of \[C II\] 158 μm versus CO(6–5)- or \[C II\] 158 μm-derived gas masses (cite: 2021ApJ...917...99Y; 2021ApJ...914...36I; 2021ApJ...911..141N; 2022ApJ...927...21W). However, it appears to be in tension with the mean stellar masses of $\geq 10^{10}\,\mathrm{M}_\odot$ recently inferred for six $z\gtrsim 6$ QSOs by modelling the spectral energy distribution of their JWST photometry (cite: 2023arXiv230904614Y). The only QSO host with both a dynamical mass (cite: 2021ApJ...911..141N) and stellar mass (from their study) is J0100+2802, for which the dynamical mass is $1.2_{-0.7}^{+0.6}\times 10^{10}$, the CO(2–1)-derived molecular gas mass is $(0.95\pm0.32)\times 10^{10}$ and the stellar mass derived by (cite: 2023arXiv230904614Y) is $<30\times10^{10}$. For this source, which is in both our samples, the upper limit could still yield a consistent mass budget. Better photometry are needed for the full sample of QSO hosts studied here to accurately characterise their stellar masses and compare these to the other baryonic components.

The above argument that the molecular gas masses dominate the mass budget, relies on a big ‘if’; in reality, the measured dynamical masses are highly uncertain and could be systematically underestimated if the measured sizes and/or circular velocities are too small, or if the assumed geometry is incorrect (cite: 2021ApJ...911..141N). If the gas is not in a planar stucture or if the dynamics are not supported by gravity (but instead by large outflows or turbulence), then the models assumed in fitting the dynamics are inappropriate. The dynamical masses may also be underestimated if these $z\gtrsim6$ QSO host systems are not in dynamical equilibrium. Indeed, all evidence points to these systems being in a state of rapid evolution, implying that the assumptions used in the modelling are not appropriate for these systems and leaving room for higher $\alpha_\mathrm{CO}$ factors.

An additional complication for the dynamical versus gas mass comparison, is that current \[C II\] 158 μm observations may be missing the much fainter, extended component, as shown (cite: 2020ApJ...904..131N) based on the stacked \[C II\] 158 μm emission of 20 $z\gtrsim6$ QSO hosts (including those studied here). The much larger extent of this faint component would mean that the measured rotation curves do not probe far enough into the galaxy ‘disk’ to sample the maximum rotation velocity, nor would the measured sizes then represent the whole disk. This is why dynamical masses are quoted within certain radii. In the case of the QSO hosts studied here, we quote values inferred from within twice the \[C II\] 158 μm scale length (2$r_\mathrm{d,[CII]}$). In order for the molecular gas traced by CO(2–1) to make up a small fraction of the total mass within this region, it would have to be significantly more extended than the \[C II\] 158 μm emission. Although we cannot test this scenario at the resolution of our data, it seems unlikely based on low-redshift galaxies (cite: Blok_2016; Bigiel_2020). Accurately testing how much of the total mass is in the form of molecular gas, will require deep, high-resolution observations of the host galaxy (and its environment), as well as better sampling of the CO excitation ladders, enabling robust constraints on $\alpha_\mathrm{CO}$.

## Depletion timescales

Combining the CO(2–1)-derived molecular gas masses and IR-inferred SFRs, we find that these $z\gtrsim6$ QSO hosts have extremely short gas depletion timescales. Our highest-redshift target, J2348–3054, has a high molecular gas mass of $\sim1\times10^{10}\,\mathrm{M}_\odot$. Assuming that 25-60% of its IR luminosity is attributable to star formation (cite: 2013ApJ...772..103L) and following the SFR-IR calibration of (cite: Hao_2011), this equates to a SFR of $500-1300 \,\mathrm{M}_\odot\,\mathrm{yr}^{-1}$. Combined with the CO(2–1)-derived molecular gas mass, this implies a short depletion timescale ($t_\mathrm{depl} = M_\mathrm{mol}/\mathrm{SFR}$) of only $8-20$ Myr. This value is consistent with the full literature sample, which span SFRs of $400-7000\,\mathrm{M}_\odot\,\mathrm{yr}^{-1}$ and depletion timescales of $4-50$ Myr. These depletion timescales are significantly shorter than for most ULIRGS and high-redshift star-forming galaxies, which have $t_\mathrm{depl} \sim 10^7-10^8$ Myr (cite: 2005ARA&A..43..677S; 2020ARA&A..58..157T), but are comparable to a handful of hyperluminous starbursts at $z>2$ (cite: 2012A&A...538L...4C; 2016MNRAS.457.4406A; 2020A&A...635A..27C). These results imply that IR-luminous $z\gtrsim6$ QSO hosts are undergoing an extreme starburst phase. However, better sampling of the dust-continuum emission is still required to disentangle the AGN and SFR contributions in these systems.

![](combined_COsled.pdf)

![](Lfir_vs_Lco.pdf)

## CO line excitation

The fact that we do not detect the CO(2–1) emission of P036+03 and J0305–3150 implies that their average CO excitation is more extreme than that of the $z=6.4$ QSO host J1148+5251, which is the best-studied CO line excitation ladder of any $z\gtrsim6$ QSO studied to date. To investigate this further, we compare the CO line excitation ladders to those of the local AGN and QSOs investigated by (cite: 2016ApJ...829...93K) and (cite: 2015ApJ...801...72R) in Fig. [4](#fig:CO_ladders). Unlike for the local AGN and QSOs, many of the $z\gtrsim 6$ QSO hosts have thermalised or even supra-thermal mid-to-low $J$ line ratios (left panel) (cite: 2009ApJ...703.1338R; 2010ApJ...714..699W; 2011ApJ...739L..34W). To test whether this is caused by significantly lower CO(2–1) or significantly higher mid-$J$ CO emission we also show the CO excitation ladder in units of $\mathrm{L_\odot}$ (right hand panel). From this comparison, it seems that the difference between the samples is much more pronounced at $J=6$ and $7$ than for $J=2$, implying that there is an even greater fraction of molecular gas in these, more highly excited states in the $z\gtrsim 6$ versus $z\sim0$ QSOs. We discuss this further in Sec. [5](#sec:discussion).

Based on our results, in combination with the literature $z>5.7$ QSO hosts, we caution that when inferring molecular gas masses from mid-$J$ observations of these extreme systems, it is important to apply a higher excitation factor than what is measured for local AGN and ULIRGs ($r_{6,1}=0.23$) or $z=2-3$ star-forming galaxies ($r_{6,1}=0.28$, (cite: 2020ApJ...902..109B)). For the full sample of $z\gtrsim6$ QSOs with observations of both the CO(6–5) and CO(2–1) transitions, we measure a mean and standard deviation on the CO(6–5)-to-CO(2–1) line luminosity ratio of $r_{6,2}=0.9\pm0.2$. Assuming that the first three levels are thermalised, this also equates to a CO(6–5)-to-CO(1-0) line luminosity ratio of $r_{6,1}=0.9\pm0.2$.

## FIR versus CO line luminosities

We test whether these $z\gtrsim6$ QSO hosts follow empirical relations between the CO line luminosities and FIR luminosities, and hence whether they are consistent with trends found for local (U)LIRGs and $z=1-4$ star-forming galaxies, in Fig. [5](#fig:Lco_Lfir). The FIR luminosities of the $z\gtrsim6$ QSO hosts are corrected for CMB effects as described in Sec. [3.1](#sub:luminosities). However, for the CO line luminosities, we show both the measured values and those calculated using a CMB correction consistent with the high-density and temperature, non-LTE case of (cite: 2013ApJ...766...13D). To compare FIR luminosities derived for different integration widths, we apply two scaling factors. For the sample of (cite: 2020ApJ...890...24V), we use the provided scaling $L_\mathrm{TIR, 8-1000 \mu m} = 1.2 L_\mathrm{FIR, 40-400 \mu m}$. We also assumed $L_\mathrm{TIR, 8-1000 \mu m} = 1.45 L_\mathrm{FIR, 42.5-122.5 \mu m}$ (cite: 2011A&A...530L...8D). We compare to three sets of $L_\mathrm{FIR}$ versus $L^\prime_\mathrm{CO}$ relations derived by (cite: Greve_2014), (cite: Liu_2015) and (cite: 2016ApJ...829...93K). We adopt the FIR wavelength range convention of $L_\mathrm{FIR, 40-400 \mu m}$ also used in (cite: Liu_2015) and scale the (cite: Greve_2014) relations using the mean value of their local sample, $\left< L_\mathrm{TIR, 8-1000 \mu m} / L_\mathrm{FIR, 30-500 \mu m} \right> = 1.77$. By converting in this manner, we are introducing an additional level of uncertainty. However, the conversion is crucial to avoid systematic offsets.

We find that the measured CO(2–1) line luminosities of the $z\gtrsim 6$ QSOs are offset, on average, to 2-6$\times$ lower values that predicted from the relations with $L_\mathrm{FIR}$ (although consistent with the scatter of lower-redshift sources), whereas the higher-$J$ transitions are consistent with these literature relations. This minor systematic offset may be the result of various factors: 1) the FIR luminosities of QSOs may be the result of both the SFRs *and* a significant contribution from the AGN, such that this comparison no longer reflects the correlation between the molecular gas mass and SFR, 2) the combined effects of the heating by, and contrast against the CMB serves to decrease the observed CO(2–1) line flux more than the $J=6$ or $7$ transitions, or 3) previous calibrations do not accurately constrain the slope of the relation as they did not sample the extremely high $L_\mathrm{FIR}$ regime well enough.

To test whether the dust is being significantly heated by the AGN in these QSOs (explanation 1), would require consistently well-sampled dust SEDs, with which the different dust components can be disentangled, as in (cite: 2013ApJ...772..103L). By modelling the contributions to the FIR luminosities of 11, $z>5$ QSO hosts, they find that the AGN contribute 40-75% to the FIR luminosity. Subtracting the mean AGN contribution of their sample, shifts the $z\gtrsim6$ QSO hosts studied here close to the $L_\mathrm{CO(2-1)}^\prime$ versus $L_\mathrm{FIR}$ relation (systematically above but consistent with the scatter), and systematically below but within the scatter of the $L_\mathrm{CO(6-5)}^\prime$ and $L_\mathrm{CO(7-6)}^\prime$ versus $L_\mathrm{FIR}$ relations. In Fig. [2](#fig:Mmol_comp), we also show that most of the $z\sim1.2$ AGN from (cite: 2020ApJ...890...24V) lie towards lower CO(2–1) line luminosities than predicted from the total FIR luminosities. However, when subtracting the AGN contribution (which they model in their SED fitting) this systematic offset also disappears. The adopted CMB correction (faint outlined squares and circles) also brings the values more in line with the CO(2–1) relation, while still keeping the high-$J$ lines consistent with these relations. However, it may well be that no correction is needed, due to the extremely high gas densities and temperatures in these QSO hosts. Isolating the CMB effects from the heating and turbulence generated through star formation and the central QSO will require dedicated simulations of these systems.

# Discussion

The high line ratios and implied low $\alpha_\mathrm{CO}$ of these $z\gtrsim 6$ QSO hosts indicate the presence of more extreme molecular ISM conditions than in the less-luminous, and mostly gas-poorer, local AGN and QSO hosts and ULIRGs we have compared them to. These are likely caused by a combination of both strong ISRFs (and high X-ray fluxes), and the presence of compact, dense gas reservoirs. Our qualitative argument for this can be summarised as follows.

To keep a significant component of molecular gas (without dissociating it) this gas must be extremely dense and/or well shielded. Both appear to be the case, in that the $z\gtrsim6$ QSO hosts galaxies studied here already have a high implied gas-to-dust ratios and small measured sizes; with \[C II\] 158 μm half-light radi of 0.8 to 4.5 kpc (cite: 2021ApJ...911..141N; 2022ApJ...927...21W; 2022ApJ...927..152M). The extent of this \[C II\] 158 μm emission is significantly smaller (by at least a factor of five) than the scale of the emission in the local AGN and QSO hosts we are comparing to. Compounding this, the molecular gas masses inferred via the same $\alpha_\mathrm{CO}$ conversion factors are a few times larger on average (or of the same order as) the local comparison sample; the molecular gas masses of the $z\gtrsim6$ QSO hosts are $\sim$few $\times10^{10} \mathrm{M}_\odot$ versus the $\sim$few$\,\times10^{9} \mathrm{M}_\odot$ measured for gas-rich local AGN and QSO hosts (cite: 2012MNRAS.426.2601P; 2015ApJ...801...72R; 2016ApJ...829...93K). Indeed, (cite: 2019ApJ...876...99S) infer densities of a $10^5-10^6$ cm$^{-3}$ for three of the literature QSO hosts included here. Not only do the $z\gtrsim 6$ QSO hosts have more molecular gas per unit volume than the local AGN and QSO hosts, they also have an order of magnitude higher (on average) FIR luminosities than the local AGN and QSO hosts. The implied SFRs of $400-7000$ M$_\odot$ yr$^{-1}$, which stem from a smaller volume than in the local galaxies, imply higher ISRF strengths (with $G_0 \gtrsim 10^3$ in Habing units for some of the $z\gtrsim6$ QSO hosts included here, according to the modelling performed by (cite: 2019ApJ...876...99S) and (cite: 2022A&A...662A..60D)). In combination, this is consistent with a picture in which the molecular clouds in these $z\gtrsim6$ QSO hosts are more closely spaced and/or much denser than in local AGN and QSO hosts and are illuminated by stronger radiation fields.

The high CO(7–6)- and CO(6–5)-to-CO(2–1) line ratios (consistent with thermalised and even supra-thermal CO) imply the presence of dense, warm, and highly turbulent gas. Similarly high line ratios have been found in the local photodissociation region (PDR) known as the Orion Bar. Modelling the far more extensive set of molecular and atomic emission lines (including isotopologues) observed for this region, several groups (cite: 2015ApJ...812...75G; 2016Natur.537..207G; 2019A&A...622A..91G; 2017A&A...598A...2A; 2018A&A...617A..77P) have found evidence for clumps of extremely high-density ($n_H\sim10^5-10^6$  cm$^{-3}$), and high-temperature ($T\sim150-300$s K) molecular gas. To produce such high line ratios, the gas temperatures may exceed the average dust temperature (cite: 2014PhR...539...49K; 2021ApJ...908...95H). Several sources of heating could elevate the kinetic temperatures of the gas. High star formation rate densities should give rise to more cosmic rays (compared to local ULIRGS/AGN), providing an additional, strong source of heating that increases the gas temperatures and causes the CO excitation ladders to peak at higher-$J$ (cite: 2012MNRAS.426.2601P; 2023MNRAS.519..729B). If large amounts of energy (e.g. from star formation and/or the QSO) are being injected into such a small volume of gas, then this gas is likely also more turbulent, providing another source of heating and implying a lower intrinsic $\alpha_\mathrm{CO}$ (cite: 2011MNRAS.418..664N; 2012ApJ...751...10P). In combination with the high densities, this increase in velocity dispersion would serve to counteract any increase in $\alpha_\mathrm{CO}$ caused by a higher ISRF or higher cosmic ray ionisation rate (cite: 2015MNRAS.452.2057C).

The high carbon abundances implied by our results are also consistent with the presence of highly turbulent gas. Mixing caused by strong turbulence may result in elevated \[C I\]/H$_2$ in the cloud interiors, thereby giving rise to bright \[C I\] emission (cite: 1995ApJ...440..674X; 2015MNRAS.448.1607G). Moreover, strong contributions from cosmic rays, X-rays and/or shocks (cite: 2014A&A...562A..96I; 2015A&A...578A..95I) would enhance the brightness of \[C i\] compared to low-$J$ CO emission (cite: 2014A&A...562A..96I; 2015A&A...578A..95I; 2018MNRAS.478.1716P; 2022MNRAS.510..725P). These additional heating sources may drive atomic carbon out of the state of LTE asumed here. Indeed, (cite: 2021ApJ...908...95H) and (cite: 2022MNRAS.510..725P) show that the \[C i\] excitation of high-redshift star-forming galaxies and local (U)LIRGS is best described by non-LTE radiative transfer models; with the LTE assumption easily accounting for a factor of a few too high $M_\mathrm{[CI]}$. In that case, a lower atomic carbon abundance than what we assumed may still be appropriate. Testing the impact of turbulence, cosmic rays, and X-rays will require better-sampled CO excitation ladders, \[C I\] transitions (including the addition of the \[C I\](1–0) line) and dust spectral energy distributions than are currently available for these $z\gtrsim6$ QSO hosts.

Given our data, it is unclear to what extent the extreme conditions within the molecular gas of these $z\gtrsim 6$ QSO host galaxies are driven by star formation versus the luminous accreting black holes. In Fig. [6](#fig:lumratio_versus), we show that the higher line ratios of the $z\gtrsim 6$ versus $z\sim 0$ QSO (and AGN) hosts correlate with proxies for both the AGN power and star formation activity. The left column illustrates that such luminous QSO hosts have not been observed in CO in the local Universe; instead the most powerful AGN in the local Universe are hosted in elliptical galaxies with little molecular gas. However, we compare to these $z\sim0$ systems to span a wider range of bolometric and FIR luminosities. We use the bolometric luminosity $L_\mathrm{bol}$ (middle column) as a proxy of the AGN power[^2] and the FIR luminosity, $L_\mathrm{FIR}$ (right-most column) as a proxy for the SFR. The fact that these three line ratios correlate with the FIR luminosity is expected, e.g. high star formation rate densities lead to greater dust heating (and hence higher $L_\mathrm{FIR}$) and also higher CO excitation (cite: 2014MNRAS.442.1411N). We also find a clear correlation with the bolometric luminosity, albeit with a large scatter. This scatter can be attributed to the different, indirect methods used to infer the $L_\mathrm{bol}$: scaling the 3000Å luminosity following (cite: 2011ApJS..194...45S)[^3] for the $z\gtrsim6$ QSO hosts, scaling the luminosity at 14–150 keV following (cite: 2017ApJS..233...17R) for the local sample (BASS catalogue of (cite: 2022ApJS..261....2K)) and scaling the \[O III\]$\lambda 5007$Å line luminosity[^4] for the sample of (cite: 2023arXiv231010235M). Thus, neither the tightness nor slope of these correlations allow us to disentangle the impact of star formation versus AGN activity on the molecular gas.

The lack of high-$J$ CO emission and inhomogeneous X-ray coverage also do not allow us to disentangle the impact of star formation versus AGN activity. These QSOs may be heavily obscured and have inhomogeneous X-ray coverage. Two of our sample (J0305–3150 and J2348–3054) have only upper limits on the X-ray fluxes from Chandra, with net counts at 0.5-7 keV of $\leq15$ and $\leq21$ (cite: 2021ApJ...908...53W), whereas P036+03 and two of the literature sample, J0100+2802 and J1429+5447, are detected with XMM Newton (cite: 2021MNRAS.504..576M; https://doi.org/10.48550/arxiv.2305.02347). For this sample of five, the data reveal no correlation between the CO line ratios probed here and the X-ray luminosity (e.g. at 2-10 keV). Future X-ray observations and observations of high-$J$ CO transitions, up to CO(11–10), will enable tests against predicted trends with the X-ray flux (cite: 2019MNRAS.490.4502V).

![](lineratios_v_global.pdf)

Overall, we find little evidence for any loss of signal due to the contrast against the CMB. The lack of a large systematic offset from empirical relations between the CO line versus CMB-corrected FIR luminosities indicates that little correction for the CMB contrast is needed for the CO lines. Likewise, the low $\alpha_\mathrm{CO}$ value needed to ensure the molecular gas masses do not exceed the dynamical masses also indicates that minimal correction for the CMB contrast is needed. However, the CMB can have multiple effects, which we cannot disentangle from variations in the ISRF and/or ISM density: it is a stronger background against which the lines are observed, but it is also an additional source of heating, thereby changing the temperature and density structure of the molecular ISM. As shown by (cite: 2013ApJ...766...13D), heating by the CMB can serve to make the CO excitation ladders peak at higher $J$, similar to effects of heating through strong ISRFs, cosmic rays, or X-rays. To disentangle these effects it is crucial to observe CO, \[C I\], and dust-continuum emission from samples of QSOs across different epochs, with the same high IR luminosities and molecular gas masses.

We check whether the compactness (proxy for density) impacts the molecular gas conditions as traced by the relative line strengths. To this end, high-resolution observations of the \[C II\] 158 μm and FIR emission are available for our set of QSOs (P036+03, J0305–3150 and J2348–3054) and four of the literature sample (J0129-0035, J2054-0005, J0100+2802, and J1148+5251) (cite: 2020ApJ...904..130V; 2021ApJ...911..141N; 2022ApJ...927..152M; 2023arXiv230601644T). Measuring sizes has so far proven challenging, with different assumed surface brightness profiles and modelling tools being applied. Nonetheless, by any metric, J2348–3054 is the most compact of the seven galaxies ($r_\mathrm{eff,[C II]}\sim 0.46$ kpc). J0129–0035 and J2054–0005 are the next most compact ($r_\mathrm{eff, [C II]}\sim 0.8$  kpc). We find marginal evidence that the compactness is related to the CO excitation. Whereas J2348–3054 and J0129–0035 exhibit some of the highest CO(6–5)-to-CO(2–1) line ratios, J1148+5251, the most extended of these resolved $z\gtrsim 6$ QSOs, has line ratios consistent with the sample mean (neither at the low nor high end). The fact that the two most compact sources seem to have the highest excitation is consistent with the picture of a denser and warmer ISM in galaxies with higher UV flux per unit volume (originating either from the central black hole or star formation). However, the sample size with both multi-line observations and resolved \[C II\] 158 μm emission remains too small to draw any strong conclusions.

We also attempt to test whether the presence of companions (and hence interactions) affects the relative line strengths or molecular gas masses. J2348–3054 and J2054-0005 have no confirmed companions, whereas J0305–3150 and J0100+2802 do (cite: 2019ApJ...874L..30V; 2023arXiv230601644T; 2023ApJ...951L...4W). J1429+5447 is a known merger (cite: 2022A&A...664A..39K). Of these, J0305–3150 has the highest mid-to-low-$J$ CO line ratios, considering the upper limit on CO(2–1). J0100+2802 and J1429+5447 are consistent with the mean excitation of the full sample. Within this small sample, we find no clear connection yet between the presence of companions and the molecular gas masses or excitation. However, future JWST observations, as in (cite: 2023ApJ...951L...4W), will help shed light on this issue.

# Conclusions

In this paper, we present the VLA Ka Band observations of CO(2–1) in three QSO host galaxies at $6.5 < z <6.9$, thereby probing their cold molecular gas reservoirs. These three QSO hosts were already detected in \[C II\] 158 μm emission and the underlying FIR continuum (cite: 2015ApJ...805L...8B; 2016ApJ...816...37V) and in CO(6–5), CO(7-6) and \[C I\] (2–1) emission (cite: 2017ApJ...851L...8V). For the highest-redshift QSO host, J2348–3054 at $z=6.9$, we robustly detected the CO(2–1) emission, revealing a molecular gas reservoir of $\sim 1\times 10^{10}\,\mathrm{M}_\odot$ already 780 Myr after the Big Bang. However, for the other two QSO hosts, P036+03 and J0305–3150, the CO(2–1) observations are consistent with noise, yielding $4\sigma$ upper limits on the molecular gas masses of $(1.0-1.5) \times 10^{10}\,\mathrm{M}_\odot$. We detect no underlying continuum emission for these three targets, nor any CO or continuum emission from their known companions.

We combine these three QSO hosts with the full set of nine $z>5$ QSO host galaxies that already have CO(2–1) observations (Table [\[tab:lit_QSOs\]](#tab:lit_QSOs)), thereby performing a broader study of trends in the molecular gas masses and CO excitation. To this end, we consistently re-derive the FIR luminosities and dust masses, taking CMB effects into account. Based on the CO(2–1) observations, and the assumptions of a ULIRG $\alpha_\mathrm{CO}=0.8$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (see (cite: 2013ARA&A..51..105C)) and thermalised low-$J$ transitions ($r_\mathrm{2,1}=1$), the molecular gas masses of the three QSO hosts studied here are consistent with the literature sample, which spans $(0.8 - 5) \times 10^{10}\, \mathrm{M}_\odot$. These values are mostly consistent with those inferred from the dust masses, assuming a gas-to-dust ratio of 100. However, the molecular gas masses estimated from the \[C II\] 158 μm line luminosity using the mean $\alpha_\mathrm{[C~II]}$ of (cite: 2018MNRAS.481.1976Z) are a factor of $6.8\pm1.9$ higher than the CO(2–1)-based values, reflecting a potential decrease in $\alpha_\mathrm{[C~II]}$ with sSFR. In order for these CO(2–1)-derived values to also be consistent with those inferred from \[C I\] (2–1), atomic carbon must be already be abundant (\[C i\]/H$_2 \sim 9 \times 10^{-5}$) and/or be undergoing significant heating through cosmic rays, X-rays, turbulence, and/or shocks.

The three QSO hosts studied here have high CO excitation, with CO(7–6)- and CO(6–5)- versus CO(2–1) line ratios consistent with or higher than most of the $z\gtrsim6$ QSO hosts studied previously (cite: 2010ApJ...714..699W; 2011ApJ...739L..34W; 2013ApJ...773...44W; 2015MNRAS.451.1713S). For P036+03 and J0305–3150, the gas excitation is significantly higher than for the $z=6.4$ QSO J1148+5251 (cite: 2009ApJ...703.1338R; 2015MNRAS.451.1713S), implying more extreme physical conditions in these systems. Despite the small range of molecular gas masses, the combined set of $z\gtrsim6$ QSO hosts spans a wide range in CO excitation. Nonetheless, the line ratios studied here are systematically higher than for local AGN and QSO host galaxies with observations of the same transitions; the mean CO(6–5)-to-CO(2–1) line luminosity ratio is $r_\mathrm{6,2} = 0.9 \pm 0.2$ (2.5$\times$ higher than in local AGN and QSOs) and the mean \[C II\] 158 μm-to-CO(2–1) line luminosity ratios is $1.0 \pm 0.4$ (2$\times$ higher than in local AGN and QSOs). Assuming that the CO(2–1) emission is thermalised, the mean CO(6–5)-to-CO(1–0) line luminosity ratio is also $r_\mathrm{6,1} = 0.9 \pm 0.2$. These higher line ratios should be considered when inferring the molecular gas masses of $z>5$ QSO hosts from only their mid-$J$ CO lines.

Comparing the CO(2–1) observations to the existing dynamical mass measurements, we find that the mass budget of the three QSOs studied here is likely dominated by the molecular gas. In particular, J2348–3054 has a molecular gas mass consistent with the lower limit on the dynamical mass, leaving little mass in neutral gas or stars within the \[C II\] 158 μm-emitting region. If the dynamical masses based on the resolved \[C II\] observations are correct, these CO(2–1) observations imply that the CO-to-H$_2$ conversion factor must be low—similar to the ULIRG value—to yield molecular gas masses that are lower than the dynamical masses. Thus, little correction for the contrast against the CMB is needed for these bright, compact systems. Combined with the high CO excitation, these results imply the presence of warm and dense molecular gas reservoirs. In combination with the literature sample, we find that the CO(2–1)-derived molecular gas masses are $20-190\times$ higher than the dust masses, implying the presence of significant, enriched reservoirs of dense molecular gas and dust. Moreover, the CO(2–1)-derived molecular gas masses are $3-11\times$ higher than the black hole masses.

Our new CO(2–1) observations support a picture in which these IR-luminous $z\gtrsim6$ QSO host galaxies have rapidly assembled copious amounts of molecular gas (either through accretion or mergers). Combining the previously detected CO(6–5), CO(7–6), and \[C I\] (2–1) emission with the new CO(2–1) constraints, indicates that all three QSO hosts studied here harbour significant amounts of warm and dense, metal-enriched gas—indicating that these are already highly evolved galaxies. In particular, the newly CO(2–1)-detected $z=6.9$ QSO host J2348–3054, has properties consistent with a massive starburst that is rapidly coevolving with the luminous central AGN (as found previously for some of the literature sample).

With these highest-redshift CO(2–1) observations, we confirm that it is possible to detect the cold, molecular gas traced by CO(2–1) emission at $z>6.5$ within $\sim15$  hours of VLA time. These observations are also now feasible with ALMA Band 1 (although it remains less efficient than the VLA at $z>5$). Observing CO(3–2) is also now feasible up $z=8.8$ with ALMA’s Band 1, whereas \[C i\](1–0) can soon be observed with ALMA’s Band 2, up to $z=6.3$. Complementing the existing plentiful \[C II\] 158 μm observations of $z\gtrsim6$ QSO hosts with observations of the cold, diffuse molecular gas is therefore achievable, albeit time-intensive. Next-generation facilities, such as the Next-Generation VLA (cite: ngVLA_book), will enable such observations to be conducted even more efficiently. The next step is to systematically model the average conditions within these massive molecular gas reservoirs—constraining the turbulence within the molecular gas, the carbon abundance and $\alpha_\mathrm{CO}$. To achieve this, it is now crucial to obtain QSO samples with a homogeneous coverage of CO (up to $J>8$), \[C i\], and dust emission. The compilation of $z\gtrsim6$ QSO hosts studied here will serve as a crucial basis for this work.

# Acknowledgements

This paper makes use of the following VLA data: 16A-160 and 17A-336. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This work made use of the public code package `Interferopy` (cite: 2021ascl.soft12005B)[^5] as well as `CASA` (cite: 2022PASP..134k4501C). L.A.B., R.A.M., M.N., and F.W. acknowledge support from the ERC Advanced Grant 740246 (Cosmic_Gas). R.A.M. acknowledges support from the Swiss National Science Foundation (SNSF) through project grant 200020_207349. EdC gratefully acknowledges the Australian Research Council as the recipient of a Future Fellowship (project FT150100079) and the ARC Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D; project CE170100013). The authors wish to thank F. Valentino for useful discussions that improved the quality of this work. We also thank the anonymous referee, whose feedback improved our interpretation.

185 natexlab

(ref: 2013MNRAS.435.1493A) Alaghband-Zadeh, S., Chapman, S. C., Swinbank, A. M., et al. 2013, MNRAS, 435, 1493

(ref: 2018A&A...615A.142A) Andreani, P., Retana-Montenegro, E., Zhang, Z.-Y., et al. 2018, A&A, 615, A142

(ref: 2017A&A...598A...2A) Andree-Labsch, S., Ossenkopf-Okada, V., & Röllig, M. 2017, A&A, 598, A2

(ref: 2008AJ....136.1118A) Ao, Y., Dinh-V-Trung, Lim, J., Yang, J., & Matsushita, S. 2008, AJ, 136, 1118

(ref: 2008A&A...491..173A) Aravena, M., Bertoldi, F., Schinnerer, E., et al. 2008, A&A, 491, 173

(ref: 2016MNRAS.457.4406A) Aravena, M., Spilker, J. S., Bethermin, M., et al. 2016, MNRAS, 457, 4406

(ref: 2015ApJ...805L...8B) Bañados, E., Decarli, R., Walter, F., et al. 2015, ApJL, 805, L8

(ref: Barvainis_2002) Barvainis, R. & Ivison, R. 2002, The Astrophysical Journal, 571, 712

(ref: 2006ApJ...642..694B) Beelen, A., Cox, P., Benford, D. J., et al. 2006, ApJ, 642, 694

(ref: 2004A&A...423..441B) Beelen, A., Cox, P., Pety, J., et al. 2004, A&A, 423, 441

(ref: 2003A&A...406L..55B) Bertoldi, F., Carilli, C. L., Cox, P., et al. 2003a, A&A, 406, L55

(ref: 2003A&A...409L..47B) Bertoldi, F., Cox, P., Neri, R., et al. 2003b, A&A, 409, L47

(ref: Bigiel_2020) Bigiel, F., de Looze, I., Krabbe, A., et al. 2020, The Astrophysical Journal, 903, 30

(ref: 2015ApJ...803...37B) Bisbas, T. G., Papadopoulos, P. P., & Viti, S. 2015, ApJ, 803, 37

(ref: 2023MNRAS.519..729B) Bisbas, T. G., van Dishoeck, E. F., Hu, C.-Y., & Schruba, A. 2023, MNRAS, 519, 729

(ref: 2017ApJ...839...90B) Bisbas, T. G., van Dishoeck, E. F., Papadopoulos, P. P., et al. 2017, ApJ, 839, 90

(ref: 2021ascl.soft12005B) Boogaard, L., Meyer, R. A., & Novak, M. 2021, Interferopy: Analyzing datacubes from radio-to-submm observations, Astrophysics Source Code Library, record ascl:2112.005

(ref: 2020ApJ...902..109B) Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020, ApJ, 902, 109

(ref: 2017MNRAS.466.2825B) Bothwell, M. S., Aguirre, J. E., Aravena, M., et al. 2017, MNRAS, 466, 2825

(ref: 2013MNRAS.429.3047B) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, MNRAS, 429, 3047

(ref: Bradford_2009) Bradford, C. M., Aguirre, J. E., Aikin, R., et al. 2009, The Astrophysical Journal, 705, 112

(ref: 2008ApJ...681L..53C) Capak, P., Carilli, C. L., Lee, N., et al. 2008, ApJL, 681, L53

(ref: 2011ApJ...739L..33C) Carilli, C. L., Hodge, J., Walter, F., et al. 2011, ApJL, 739, L33

(ref: 2002AJ....123.1838C) Carilli, C. L., Kohno, K., Kawabe, R., et al. 2002, AJ, 123, 1838

(ref: 2007ApJ...666L...9C) Carilli, C. L., Neri, R., Wang, R., et al. 2007, ApJL, 666, L9

(ref: Carilli_2005) Carilli, C. L., Solomon, P., Bout, P. V., et al. 2005, The Astrophysical Journal, 618, 586

(ref: 2013ARA&A..51..105C) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: 2020MNRAS.499.5136C) Carniani, S., Ferrara, A., Maiolino, R., et al. 2020, MNRAS, 499, 5136

(ref: 2019MNRAS.489.3939C) Carniani, S., Gallerani, S., Vallini, L., et al. 2019, MNRAS, 489, 3939

(ref: 2013A&A...559A..29C) Carniani, S., Marconi, A., Biggs, A., et al. 2013, A&A, 559, A29

(ref: 2022PASP..134k4501C) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: 2020A&A...635A..27C) Ciesla, L., Béthermin, M., Daddi, E., et al. 2020, A&A, 635, A27

(ref: 2015MNRAS.452.2057C) Clark, P. C. & Glover, S. C. O. 2015, MNRAS, 452, 2057

(ref: 2019MNRAS.486.4622C) Clark, P. C., Glover, S. C. O., Ragan, S. E., & Duarte-Cabral, A. 2019, MNRAS, 486, 4622

(ref: 1993MNRAS.261..299C) Clements, D. L., Andreani, P., & Chase, S. T. 1993, MNRAS, 261, 299

(ref: 2012A&A...538L...4C) Combes, F., Rex, M., Rawle, T. D., et al. 2012, A&A, 538, L4

(ref: 2010MNRAS.407L.103C) Coppin, K. E. K., Chapman, S. C., Smail, I., et al. 2010, MNRAS, 407, L103

(ref: Cox_2011) Cox, P., Krips, M., Neri, R., et al. 2011, The Astrophysical Journal, 740, 63

(ref: 2013ApJ...766...13D) da Cunha, E., Groves, B., Walter, F., et al. 2013a, ApJ, 766, 13

(ref: 2021ApJ...919...30D) da Cunha, E., Hodge, J. A., Casey, C. M., et al. 2021, ApJ, 919, 30

(ref: 2013ApJ...765....9D) da Cunha, E., Walter, F., Decarli, R., et al. 2013b, ApJ, 765, 9

(ref: Blok_2016) de Blok, W. J. G., Walter, F., Smith, J.-D. T., et al. 2016, The Astronomical Journal, 152, 51

(ref: 2011A&A...530L...8D) De Breuck, C., Maiolino, R., Caselli, P., et al. 2011, A&A, 530, L8

(ref: 2014ApJ...790..145D) De Rosa, G., Venemans, B. P., Decarli, R., et al. 2014, ApJ, 790, 145

(ref: 2022A&A...662A..60D) Decarli, R., Pensabene, A., Venemans, B., et al. 2022, A&A, 662, A60

(ref: 2017Natur.545..457D) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457

(ref: 2017ApJ...846...32D) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32

(ref: Downes_1998) Downes, D. & Solomon, P. M. 1998, The Astrophysical Journal, 507, 615

(ref: Downes_2003) Downes, D. & Solomon, P. M. 2003, The Astrophysical Journal, 582, 37

(ref: 2007ApJ...663..866D) Draine, B. T., Dale, D. A., Bendo, G., et al. 2007, ApJ, 663, 866

(ref: 2003MNRAS.341..589D) Dunne, L., Eales, S. A., & Edmunds, M. G. 2003, MNRAS, 341, 589

(ref: ngVLA_book) Eric Murphy and the ngVLA Science Advisory Council. 2018, Science with a Next Generation Very Large Array (Astronomical Society of the Pacific Conference Series)

(ref: 2023ARA&A..61..373F) Fan, X., Bañados, E., & Simcoe, R. A. 2023, ARA&A, 61, 373

(ref: 2022ApJ...941..106F) Farina, E. P., Schindler, J.-T., Walter, F., et al. 2022, ApJ, 941, 106

(ref: 2011ApJ...740L..29F) Ferkinhoff, C., Brisbin, D., Nikola, T., et al. 2011, ApJL, 740, L29

(ref: Feruglio_2023) Feruglio, C., Maio, U., Tripodi, R., et al. 2023, The Astrophysical Journal Letters, 954, L10

(ref: 2013PASP..125..306F) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: Gall_2011) Gall, C., Andersen, A. C., & Hjorth, J. 2011, Astronomy & Astrophysics, 528, A14

(ref: Gilli_2011) Gilli, R., Su, J., Norman, C., et al. 2011, The Astrophysical Journal, 730, L28

(ref: 2016MNRAS.456.3596G) Glover, S. C. O. & Clark, P. C. 2016, MNRAS, 456, 3596

(ref: 2015MNRAS.448.1607G) Glover, S. C. O., Clark, P. C., Micic, M., & Molina, F. 2015, MNRAS, 448, 1607

(ref: 2016Natur.537..207G) Goicoechea, J. R., Pety, J., Cuadrado, S., et al. 2016, Nature, 537, 207

(ref: 2019A&A...622A..91G) Goicoechea, J. R., Santa-Maria, M. G., Bron, E., et al. 2019, A&A, 622, A91

(ref: 2015ApJ...812...75G) Goicoechea, J. R., Teyssier, D., Etxaluze, M., et al. 2015, ApJ, 812, 75

(ref: Greve_2014) Greve, T. R., Leonidaki, I., Xilouris, E. M., et al. 2014, The Astrophysical Journal, 794, 142

(ref: Groves_2015) Groves, B. A., Schinnerer, E., Leroy, A., et al. 2015, The Astrophysical Journal, 799, 96

(ref: Hao_2011) Hao, C.-N., Kennicutt, R. C., Johnson, B. D., et al. 2011, The Astrophysical Journal, 741, 124

(ref: 2021ApJ...908...95H) Harrington, K. C., Weiss, A., Yun, M. S., et al. 2021, ApJ, 908, 95

(ref: 2002ApJS..139..467I) Ikeda, M., Oka, T., Tatematsu, K., Sekimoto, Y., & Yamamoto, S. 2002, ApJS, 139, 467

(ref: 2017MNRAS.468.5020I) Inayoshi, K., Hirai, R., Kinugawa, T., & Hotokezaka, K. 2017, MNRAS, 468, 5020

(ref: 2014A&A...562A..96I) Israel, F. P., Güsten, R., Meijerink, R., et al. 2014, A&A, 562, A96

(ref: 2015A&A...578A..95I) Israel, F. P., Rosenberg, M. J. F., & van der Werf, P. 2015, A&A, 578, A95

(ref: 2021ApJ...914...36I) Izumi, T., Matsuoka, Y., Fujimoto, S., et al. 2021, ApJ, 914, 36

(ref: 2007AJ....134.1150J) Jiang, L., Fan, X., Vestergaard, M., et al. 2007, AJ, 134, 1150

(ref: 2016ApJ...829...93K) Kamenetzky, J., Rangwala, N., Glenn, J., Maloney, P. R., & Conley, A. 2016, ApJ, 829, 93

(ref: 2022A&A...664A..39K) Khusanova, Y., Bañados, E., Mazzucchelli, C., et al. 2022, A&A, 664, A39

(ref: 2013ARA&A..51..511K) Kormendy, J. & Ho, L. C. 2013, ARA&A, 51, 511

(ref: 2022ApJS..261....2K) Koss, M. J., Ricci, C., Trakhtenbrot, B., et al. 2022, ApJS, 261, 2

(ref: 2008A&A...477..547K) Kramer, C., Cubick, M., Röllig, M., et al. 2008, A&A, 477, 547

(ref: 2014PhR...539...49K) Krumholz, M. R. 2014, Phys. Rep., 539, 49

(ref: 2012MNRAS.424L..34K) Kuo, T.-M. & Hirashita, H. 2012, MNRAS, 424, L34

(ref: 2007ApJ...669...32K) Kurk, J. D., Walter, F., Fan, X., et al. 2007, ApJ, 669, 32

(ref: 2016PASA...33...51L) Latif, M. A. & Ferrara, A. 2016, PASA, 33, e051

(ref: 2013ApJ...772..103L) Leipski, C., Meisenheimer, K., Walter, F., et al. 2013, ApJ, 772, 103

(ref: 2014ApJ...785..154L) Leipski, C., Meisenheimer, K., Walter, F., et al. 2014, ApJ, 785, 154

(ref: Leipski_2014) Leipski, C., Meisenheimer, K., Walter, F., et al. 2014, The Astrophysical Journal, 785, 154

(ref: 2011ApJ...739L..30L) Lestrade, J.-F., Carilli, C. L., Thanjavur, K., et al. 2011, ApJL, 739, L30

(ref: 2010A&A...522L...4L) Lestrade, J. F., Combes, F., Salomé, P., et al. 2010, A&A, 522, L4

(ref: 2022ApJ...930...27L) Li, J., Venemans, B. P., Walter, F., et al. 2022, ApJ, 930, 27

(ref: 2018MNRAS.478L..83L) Liang, L., Feldmann, R., Faucher-Giguère, C.-A., et al. 2018, MNRAS, 478, L83

(ref: Liu_2015) Liu, D., Gao, Y., Isaak, K., et al. 2015, The Astrophysical Journal, 810, L14

(ref: 2018ApJ...864...38L) Lu, N., Cao, T., Dı́az-Santos, T., et al. 2018, ApJ, 864, 38

(ref: Lutz_2007) Lutz, D., Sturm, E., Tacconi, L. J., et al. 2007, The Astrophysical Journal, 661, L25

(ref: 2020A&A...643A.141M) Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A, 643, A141

(ref: 2023A&A...676A..71M) Mazzucchelli, C., Bischetti, M., D’Odorico, V., et al. 2023, A&A, 676, A71

(ref: 2021MNRAS.504..576M) Medvedev, P., Gilfanov, M., Sazonov, S., Schartel, N., & Sunyaev, R. 2021, MNRAS, 504, 576

(ref: 2023ApJ...956..127M) Meyer, R. A., Neeleman, M., Walter, F., & Venemans, B. 2023, ApJ, 956, 127

(ref: 2022ApJ...927..152M) Meyer, R. A., Walter, F., Cicone, C., et al. 2022, ApJ, 927, 152

(ref: 2010A&A...522A..15M) Michałowski, M. J., Murphy, E. J., Hjorth, J., et al. 2010, A&A, 522, A15

(ref: 2023arXiv231010235M) Molyneux, S. J., Calistro Rivera, G., De Breuck, C., et al. 2023, arXiv e-prints, arXiv:2310.10235

(ref: 2011MNRAS.418..664N) Narayanan, D., Krumholz, M., Ostriker, E. C., & Hernquist, L. 2011, MNRAS, 418, 664

(ref: 2014MNRAS.442.1411N) Narayanan, D. & Krumholz, M. R. 2014, MNRAS, 442, 1411

(ref: qubefit) Neeleman, M. 2021, Qubefit v1.0.1

(ref: 2021ApJ...911..141N) Neeleman, M., Novak, M., Venemans, B. P., et al. 2021, ApJ, 911, 141

(ref: 2019A&A...624A..23N) Nesvadba, N. P. H., Cañameras, R., Kneissl, R., et al. 2019, A&A, 624, A23

(ref: 2020ApJ...904..131N) Novak, M., Venemans, B. P., Walter, F., et al. 2020, ApJ, 904, 131

(ref: Omont_2013) Omont, A., Willott, C. J., Beelen, A., et al. 2013, Astronomy & Astrophysics, 552, A43

(ref: 2022MNRAS.510..725P) Papadopoulos, P., Dunne, L., & Maddox, S. 2022, MNRAS, 510, 725

(ref: 2018MNRAS.478.1716P) Papadopoulos, P. P., Bisbas, T. G., & Zhang, Z.-Y. 2018, MNRAS, 478, 1716

(ref: 2004MNRAS.351..147P) Papadopoulos, P. P., Thi, W. F., & Viti, S. 2004, MNRAS, 351, 147

(ref: 2012ApJ...751...10P) Papadopoulos, P. P., van der Werf, P., Xilouris, E., Isaak, K. G., & Gao, Y. 2012a, ApJ, 751, 10

(ref: 2012MNRAS.426.2601P) Papadopoulos, P. P., van der Werf, P. P., Xilouris, E. M., et al. 2012b, MNRAS, 426, 2601

(ref: 2018A&A...617A..77P) Parikka, A., Habart, E., Bernard-Salas, J., Köhler, M., & Abergel, A. 2018, A&A, 617, A77

(ref: 2018ApJ...864...49P) Pavesi, R., Sharon, C. E., Riechers, D. A., et al. 2018, ApJ, 864, 49

(ref: 2006AJ....132.1307P) Petric, A. O., Carilli, C. L., Bertoldi, F., et al. 2006, AJ, 132, 1307

(ref: 1999Sci...286.2493P) Planesas, P., Martin-Pintado, J., Neri, R., & Colina, L. 1999, Science, 286, 2493

(ref: 2017ApJS..233...17R) Ricci, C., Trakhtenbrot, B., Koss, M. J., et al. 2017, ApJS, 233, 17

(ref: 2013Natur.496..329R) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329

(ref: 2011ApJ...739L..32R) Riechers, D. A., Carilli, C. L., Maddalena, R. J., et al. 2011a, ApJL, 739, L32

(ref: 2011ApJ...739L..31R) Riechers, D. A., Hodge, J., Walter, F., Carilli, C. L., & Bertoldi, F. 2011b, ApJL, 739, L31

(ref: 2009ApJ...703.1338R) Riechers, D. A., Walter, F., Bertoldi, F., et al. 2009, ApJ, 703, 1338

(ref: 2007ApJ...671L..13R) Riechers, D. A., Walter, F., Carilli, C. L., & Bertoldi, F. 2007, ApJL, 671, L13

(ref: 2008ApJ...686L...9R) Riechers, D. A., Walter, F., Carilli, C. L., Bertoldi, F., & Momjian, E. 2008, ApJL, 686, L9

(ref: 2006ApJ...650..604R) Riechers, D. A., Walter, F., Carilli, C. L., et al. 2006, ApJ, 650, 604

(ref: 2015ApJ...801...72R) Rosenberg, M. J. F., van der Werf, P. P., Aalto, S., et al. 2015, ApJ, 801, 72

(ref: Sargent_2014) Sargent, M. T., Daddi, E., Béthermin, M., et al. 2014, The Astrophysical Journal, 793, 19

(ref: Schindler_2020) Schindler, J.-T., Farina, E. P., Bañados, E., et al. 2020, The Astrophysical Journal, 905, 51

(ref: 2008ApJ...689L...5S) Schinnerer, E., Carilli, C. L., Capak, P., et al. 2008, ApJL, 689, L5

(ref: 2012MNRAS.423.2132S) Schumacher, H., Martı́nez-Sansigre, A., Lacy, M., Rawlings, S., & Schinnerer, E. 2012, MNRAS, 423, 2132

(ref: 2017ApJ...837..150S) Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150

(ref: 2016ApJ...820...83S) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83

(ref: 2019ApJ...876...99S) Shao, Y., Wang, R., Carilli, C. L., et al. 2019, ApJ, 876, 99

(ref: 2011ApJS..194...45S) Shen, Y., Richards, G. T., Strauss, M. A., et al. 2011, ApJS, 194, 45

(ref: 2019ApJ...873...35S) Shen, Y., Wu, J., Jiang, L., et al. 2019, ApJ, 873, 35

(ref: 2005ARA&A..43..677S) Solomon, P. M. & Vanden Bout, P. A. 2005, ARA&A, 43, 677

(ref: 2010ApJ...724..957S) Stacey, G. J., Hailey-Dunsheath, S., Ferkinhoff, C., et al. 2010, ApJ, 724, 957

(ref: 2015MNRAS.451.1713S) Stefan, I. I., Carilli, C. L., Wagg, J., et al. 2015, MNRAS, 451, 1713

(ref: 2020ARA&A..58..157T) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157

(ref: 2021IAUS..356..261T) Trakhtenbrot, B. 2021, in Nuclear Activity in Galaxies Across Cosmic Time, ed. M. Pović, P. Marziani, J. Masegosa, H. Netzer, S. H. Negu, & S. B. Tessema, Vol. 356, 261–275

(ref: 2023arXiv230601644T) Tripodi, R., Scholtz, J., Maiolino, R., et al. 2023, arXiv e-prints, arXiv:2306.01644

(ref: 2016ApJ...819..161T) Tunnard, R. & Greve, T. R. 2016, ApJ, 819, 161

(ref: 2018ApJ...869...27V) Valentino, F., Magdis, G. E., Daddi, E., et al. 2018, ApJ, 869, 27

(ref: 2020ApJ...890...24V) Valentino, F., Magdis, G. E., Daddi, E., et al. 2020, ApJ, 890, 24

(ref: 2019MNRAS.490.4502V) Vallini, L., Tielens, A. G. G. M., Pallottini, A., et al. 2019, MNRAS, 490, 4502

(ref: 2004ApJ...614L..97V) Vanden Bout, P. A., Solomon, P. M., & Maddalena, R. J. 2004, ApJL, 614, L97

(ref: 2021ApJ...923...59V) Vayner, A., Zakamska, N., Wright, S. A., et al. 2021, ApJ, 923, 59

(ref: 2015ApJ...801L..11V) Venemans, B. P., Bañados, E., Decarli, R., et al. 2015, ApJL, 801, L11

(ref: 2013ApJ...779...24V) Venemans, B. P., Findlay, J. R., Sutherland, W. J., et al. 2013, ApJ, 779, 24

(ref: 2012ApJ...751L..25V) Venemans, B. P., McMahon, R. G., Walter, F., et al. 2012, ApJL, 751, L25

(ref: 2019ApJ...874L..30V) Venemans, B. P., Neeleman, M., Walter, F., et al. 2019, ApJL, 874, L30

(ref: 2017ApJ...851L...8V) Venemans, B. P., Walter, F., Decarli, R., et al. 2017a, ApJL, 851, L8

(ref: 2017ApJ...845..154V) Venemans, B. P., Walter, F., Decarli, R., et al. 2017b, ApJ, 845, 154

(ref: 2020ApJ...904..130V) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130

(ref: 2016ApJ...816...37V) Venemans, B. P., Walter, F., Zschaechner, L., et al. 2016, ApJ, 816, 37

(ref: Venturini_2003) Venturini, S. & Solomon, P. M. 2003, The Astrophysical Journal, 590, 740

(ref: 2012ApJ...752L..30W) Wagg, J., Wiklind, T., Carilli, C. L., et al. 2012, ApJL, 752, L30

(ref: 2003Natur.424..406W) Walter, F., Bertoldi, F., Carilli, C., et al. 2003, Nature, 424, 406

(ref: 2004ApJ...615L..17W) Walter, F., Carilli, C., Bertoldi, F., et al. 2004, ApJL, 615, L17

(ref: 2012Natur.486..233W) Walter, F., Decarli, R., Carilli, C., et al. 2012, Nature, 486, 233

(ref: 2022ApJ...927...21W) Walter, F., Neeleman, M., Decarli, R., et al. 2022, ApJ, 927, 21

(ref: 2009Natur.457..699W) Walter, F., Riechers, D., Cox, P., et al. 2009, Nature, 457, 699

(ref: 2011ApJ...730...18W) Walter, F., Weiß, A., Downes, D., Decarli, R., & Henkel, C. 2011, ApJ, 730, 18

(ref: 2021ApJ...908...53W) Wang, F., Fan, X., Yang, J., et al. 2021, ApJ, 908, 53

(ref: 2019ApJ...880....2W) Wang, F., Wang, R., Fan, X., et al. 2019, ApJ, 880, 2

(ref: 2023ApJ...951L...4W) Wang, F., Yang, J., Hennawi, J. F., et al. 2023, ApJL, 951, L4

(ref: 2010ApJ...714..699W) Wang, R., Carilli, C. L., Neri, R., et al. 2010, ApJ, 714, 699

(ref: 2011AJ....142..101W) Wang, R., Wagg, J., Carilli, C. L., et al. 2011a, AJ, 142, 101

(ref: 2013ApJ...773...44W) Wang, R., Wagg, J., Carilli, C. L., et al. 2013, ApJ, 773, 44

(ref: 2011ApJ...739L..34W) Wang, R., Wagg, J., Carilli, C. L., et al. 2011b, ApJL, 739, L34

(ref: 2016ApJ...830...53W) Wang, R., Wu, X.-B., Neri, R., et al. 2016, ApJ, 830, 53

(ref: 2007A&A...467..955W) Weiß, A., Downes, D., Neri, R., et al. 2007, A&A, 467, 955

(ref: 2003A&A...409L..41W) Weiß, A., Henkel, C., Downes, D., & Walter, F. 2003, A&A, 409, L41

(ref: 2012ApJ...753..102W) Weiß, A., Walter, F., Downes, D., et al. 2012, ApJ, 753, 102

(ref: 2005A&A...438..533W) Weiß, A., Walter, F., & Scoville, N. Z. 2005, A&A, 438, 533

(ref: Willott_2017) Willott, C. J., Bergeron, J., & Omont, A. 2017, The Astrophysical Journal, 850, 108

(ref: 2007AJ....133..564W) Willott, C. J., Martı́nez-Sansigre, A., & Rawlings, S. 2007, AJ, 133, 564

(ref: 2023MNRAS.523.3119W) Witstok, J., Jones, G. C., Maiolino, R., Smit, R., & Schneider, R. 2023, MNRAS, 523, 3119

(ref: 2015Natur.518..512W) Wu, X.-B., Wang, F., Fan, X., et al. 2015, Nature, 518, 512

(ref: 1995ApJ...440..674X) Xie, T., Allen, M., & Langer, W. D. 1995, ApJ, 440, 674

(ref: 2017PhDT........21Y) Yang, C. 2017, PhD thesis, Institut d’Astrophysique Spatiale; CAS, Purple Mountain Observatory

(ref: 2023arXiv230904614Y) Yue, M., Eilers, A.-C., Simcoe, R. A., et al. 2023, arXiv e-prints, arXiv:2309.04614

(ref: 2021ApJ...917...99Y) Yue, M., Yang, J., Fan, X., et al. 2021, ApJ, 917, 99

(ref: 2018MNRAS.481.1976Z) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976

(ref: https://doi.org/10.48550/arxiv.2305.02347) Zappacosta, L., Piconcelli, E., Fiore, F., et al. 2023, HYPerluminous quasars at the Epoch of ReionizatION (HYPERION). A new regime for the X-ray nuclear properties of the first quasars

(ref: 2016RSOS....360025Z) Zhang, Z.-Y., Papadopoulos, P. P., Ivison, R. J., et al. 2016, Royal Society Open Science, 3, 160025

# Literature samples

To help interpret our results, we compiles a list of all $z>5$ QSO host galaxies with existing CO(2–1) observations from the literature (Table [\[tab:lit_QSOs\]](#tab:lit_QSOs)). We also put these galaxies in context with a sample of star-forming galaxies at $z\gtrsim4$ with CO(2–1), CO(6–5) and/or CO(7-6) detections (Table [\[tab:highz_SFGs\]](#tab:highz_SFGs)), a sample of $z=1-4$ QSO hosts (Table [\[tab:intz_qsos\]](#tab:intz_qsos)) the $z\sim 1.2$ star-forming galaxies and AGN of (cite: 2020ApJ...890...24V) and the low-redshift (U)LIRGS, especially those hosting AGN or QSOs, in (cite: 2016ApJ...829...93K) and (cite: 2015ApJ...801...72R).

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | z | $M_{BH}$ | $L_\mathrm{bol}$ | $M_{dyn}$ | $S\Delta v_\mathrm{CO(2-1)}$ | $S\Delta v_\mathrm{CO(3-2)}$ | $S\Delta v_\mathrm{CO(5-4)}$ | $S\Delta v_\mathrm{CO(6-5)}$ | $S\Delta v_\mathrm{CO(7-6)}$ | $S\Delta v_\mathrm{CO(8-7)}$ | $S\Delta v_\mathrm{CO(9-8)}$ | $S\Delta v_\mathrm{[C \textsc{i}(2-1)]}$ | $S\Delta v_\mathrm{[C \textsc{ii}]}$ |
|  |  | ($\times 10^9$ M$_\odot$) | ($\times 10^{13}$ L$_\odot$) | ($\times 10^{10}$ M$_\odot$) | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) |
| J0927+2001 | 5.7722 | $4.9_{-1.3}^{+1.3}$ $^a$ | $3.1 ^c$ | \- | $0.13\pm0.02~^j$ | \- | $0.44\pm0.07^o$ | $0.69\pm0.13^o$ | \- | \- | \- | \- | \- |
| J0129-0035 | 5.7794 | \- | $5.7 ^d$ | $5.4_{-3.8}^{+3.3}$ $^i$ | $0.036\pm0.005^k$ | \- | \- | $0.37\pm0.07^e$ | \- | \- | \- | \- | $1.99\pm0.12^d$ |
| J0840+5624 | 5.8437 | $3.5_{-1.5}^{+1.5}$ $^a$ | $5.8 ^e$ | \- | $0.06\pm0.02^j$ | \- | $0.60\pm0.07^o$ | $0.72\pm0.15^o$ | \- | \- | \- | \- | \- |
| J2310+1855 | 6.003 | $3.7_{-0.5}^{+0.6}$ $^b$ | $8.1 ^c$ | \- | $0.18\pm0.02^k$ | \- | $0.89\pm0.09^d$ | $1.52\pm0.13^d$ | \- | $1.55\pm0.13^q$ | $1.46\pm0.18^q$ | \- | $8.83\pm0.44^d$ |
| J2054-0005 | 6.0379 | $2.2_{-0.3}^{+0.3}$ $^b$ | $3.2 ^f$ | $>2.9$ $^i$ | $0.06\pm0.01^k$ | \- | \- | $0.34\pm0.07^o$ | \- | \- | \- | \- | $3.37\pm0.12^d$ |
| J1429+5447 | 6.1831 | $1.8_{-1.6}^{+1.6}$ $^a$ | $2.3 ^g$ | \- | $0.065\pm0.011^j$ | \- | \- | \- | \- | \- | \- | \- | $3.6\phantom{0}\pm0.2\phantom{0}$ $^r$ |
| J1623+3112 | 6.26 | $2.5_{-0.3}^{+0.3}$ $^a$ | \- | \- | $< 0.062^j$ | \- | \- | \- | \- | \- | \- | \- | \- |
| J0100+2802 | 6.3 | $6.6_{-0.7}^{+0.3}$ $^c$ | $3.7 ^f$ | $10.2_{-7.1}^{+6.1}$ $^i$ | $0.04\pm0.01^l$ | \- | \- | $0.32\pm0.084^l$ | \- | \- | \- | \- | $3.36\pm0.46^l$ |
| J1148+5251 | 6.4187 | $8.7_{-0.4}^{+0.4}$ $^a$ | $9.7 ^h$ | \- | $0.095\pm0.007^m$ | $0.18\pm0.04^n$ | \- | $0.73\pm0.07^p$ | $0.64\pm0.08^p$ | \- | \- | $0.22\pm0.05^p$ | $3.9\phantom{0}\pm0.3\phantom{0}$ $^s$ |

**References:** $^a$ (cite: 2019ApJ...873...35S), $^b$ (cite: 2022ApJ...941..106F) $^c$ (cite: 2023A&A...676A..71M), $^d$ (cite: 2013ApJ...773...44W), $^e$ (cite: 2011AJ....142..101W), $^f$ (cite: Schindler_2020), $^g$ (cite: Omont_2013), $^h$ (cite: https://doi.org/10.48550/arxiv.2305.02347), $^i$ (cite: 2021ApJ...911..141N), $^j$ (cite: 2011ApJ...739L..34W), $^k$ (cite: 2019ApJ...876...99S), $^l$ (cite: 2016ApJ...830...53W), $^m$ (cite: 2015MNRAS.451.1713S), $^n$ (cite: 2004ApJ...615L..17W), $^o$ (cite: 2010ApJ...714..699W), $^p$ (cite: 2009ApJ...703.1338R), $^q$ (cite: 2019MNRAS.489.3939C), $^r$ (cite: 2022A&A...664A..39K), $^s$ (cite: 2022ApJ...927..152M)

|  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | z | $\log(L_\mathrm{FIR}/L_\odot)$ | FIR $\lambda$ range | magnfication factor | $S\Delta v_\mathrm{CO(2-1)}$ | $S\Delta v_\mathrm{CO(6-5)}$ | $S\Delta v_\mathrm{CO(7-6)}$ |  |  |  |  |
|  |  |  | μm | μ | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) |  |  |  |  |
| MM18423+5938 | 3.929 | $14.2_{-0.4}^{+0.4}$ $^a$ | 14.0-608.0 | 1.0 | $2.74\pm0.23$ $^a$ | $6.6\pm0.6$ $^m$ | $3.9\pm0.5$ $^m$ |  |  |  |  |
| GN20 / SMMJ123711+622212 | 4.050 | $13.27_{-0.5}^{+0.5}$ $^b$ | 40-400 | 1.0 | $0.87\pm0.09$ $^j$ |  | $1.6\pm0.2$ $^b$ |  |  |  |  |
| H-ATLASJ142413.9+023040/ID141 | 4.243 | $13.93_{-0.02}^{+0.02}$ $^c$ | 42.5-122.5 | 4.6 |  |  | $6.5\pm1.4$ $^c$ |  |  |  |  |
| J1000+0234 | 4.542 | $12.93_{-0.26}^{+0.26}$ $^d$ | 42.5-122.5 | 1.0 | $0.057\pm0.017$ $^k$ |  | \- |  |  |  |  |
| J0332-2756 | 4.755 | $12.62_{-0.06}^{+0.06}$ $^e$ | 42.5-122.5 | 1.0 | $0.09\pm0.02$ $^l$ |  | \- |  |  |  |  |
| SMMJ12365+621226, HDF850.1 | 5.183 | $12.81_{-0.07}^{+0.07}$ $^f$ | 42.5-122.5 | 1.4 | $0.17\pm0.04$ $^f$ | $0.39\pm0.1$ $^f$ | \- |  |  |  |  |
| J0918+5142 | 5.2429 | $13.96_{-0.0 }^{+0.0 }$ $^g$ | 42.5-122.5 | 11.0 | $7.1\pm1.0$ $^g$ | $27.0\pm2.8$ $^g$ | $24.0\pm2.1$ $^g$ |  |  |  |  |
| HZ10 | 5.6543 | $12.03_{-0.23}^{+0.37}$ $^h$ | 42.5-122.5 | 1.0 | $0.1\pm0.02$ $^h$ |  |  |  |  |  |  |
| J170647.8+584623, HFLS3 | 6.3369 | $13.45_{-0.05}^{+0.05}$ $^i$ | 42.5-122.5 | 1.0 | $0.315\pm0.028$ $^i$ | $2.74\pm0.68$ $^i$ | $2.9\pm0.77$$^i$ |  |  |  |  |

70pt70pt **References:** $^a$ (cite: 2011ApJ...739L..30L), $^b$ (cite: 2013MNRAS.429.3047B), $^c$ (cite: Cox_2011), $^d$ (cite: 2008ApJ...681L..53C), $^e$ (cite: 2011A&A...530L...8D), $^f$ (cite: 2012Natur.486..233W), $^g$ (cite: 2012A&A...538L...4C), $^h$ (cite: 2018ApJ...864...49P), $^i$ (cite: 2013Natur.496..329R), $^j$ (cite: 2011ApJ...739L..33C), $^k$ (cite: 2008ApJ...689L...5S), $^l$ (cite: 2010MNRAS.407L.103C), $^m$ (cite: 2010A&A...522L...4L)

|  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | z | $L_\mathrm{FIR}/L_\odot$ | $L_\mathrm{bol}/L_\odot$ | μ | $S\Delta v_\mathrm{CO(2-1)}$ | $S\Delta v_\mathrm{CO(6-5)}$ | $S\Delta v_\mathrm{CO(7-6)}$ | $S\Delta v_\mathrm{[C \textsc{i}(2-1)]}$ | $S\Delta v_\mathrm{[C \textsc{ii}]}$ |  |  |
|  |  |  |  |  | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) | (Jy km s$^{-1}$) |  |  |
| Q0957+561 | 1.414 | $5.63\times10^{12}$ $^1$ | \- | \- | $1.2\pm0.1$ $^{24}$ |  |  |  |  |  |  |
| 3C318 | 1.5771 | $9.34\times10^{12}$ $^2$ | $2.1\times10^{12}$ $^{15}$ | \- | $1.19\pm0.22$ $^2$ |  |  |  |  |  |  |
| COSBO11 / J100038.01+020822.4 | 1.8275 | $5.70\times10^{12}$ $^3$ | $3.0\times10^{13}$ $^{16}$ | 1 $^3$ | $1.33\pm0.08$ $^3$ | $4.86\pm0.8$ $^3$ |  |  | $77$ $^3$ |  |  |
| B1938+666 | 2.059 | $3.30\times10^{13}$ $^4$ | \- | \- | $3.8\pm1.1$ $^4$ |  |  |  |  |  |  |
| IRASF10214+4724 | 2.2855 | $5.00\times10^{12}$ $^5$ | $1.4\times10^{14}$ $^{17}$ | \- |  | $7.09\pm0.47$ $^{27}$ | $5.43\pm0.56$$^{27}$ |  |  |  |  |
| Cloverleaf | 2.558 | $2.40\times10^{13}$ $^6$ | $7.0\times10^{14}$ $^{18}$ | 11 $^{23}$ |  | $37\pm8.1$ $^{28}$ | $45\pm2$ $^{28}$ |  |  |  |  |
| SMMJ14011+0252 | 2.56 | $6.55\times10^{12}$ $^7$ | \- | \- |  |  | $3.2\pm0.5$ $^7$ | $3.1\pm0.3$$^7$ |  |  |  |
| VCVJ1409+5628 / J140955.5+562827 | 2.58 | $2.45\times10^{13}$ $^8$ | $2.4\times10^{14}$ $^{19}$ | \- |  |  | $4.1\pm1.0$ $^{30}$ |  |  |  |  |
| AMS12 | 2.7668 | $3.16\times10^{13}$ $^9$ | \- | \- |  |  | $2.7\pm0.3$ $^9$ | $1.5\pm0.3$ $^9$ |  |  |  |
| RXJ0911+0551 | 2.796 | $3.81\times10^{13}$ $^{10}$ | \- | \- |  |  | $5.3\pm0.4$ $^{31}$ | $2.3\pm0.4$ $^{31}$ |  |  |  |
| APM08279+5255 | 3.9 | $9.45\times10^{13}$ $^{10}$ | $3.7\times10^{14}$ $^{20}$ | 7 $^{12}$ | $0.81\pm0.18$ $^{11}$ | $7.3\pm0.8$ $^{29}$ |  | $<1.1$ $^{29}$ |  |  |  |
| PSSJ2322+1944 | 4.119 | $5.09\times10^{12}$ $^{11}$ |  | 3.5 $^{12}$ | $0.92\pm0.30$ $^{25}$ |  |  | $1.4\pm0.3$ $^{25}$ |  |  |  |
| BR1335-0417 | 4.407 | $2.76\times10^{13}$ $^{12}$ |  | 1 $^{12}$ | $0.43\pm0.02$ $^{12}$ |  | $3.08\pm0.11$ $^{32}$ | $1.04\pm0.1$ $^{12}$ | $26.2\pm4.3$ $^{32}$ |  |  |
| BR1202-0725 | 4.692 | $3.17\times10^{13}$ $^{13}$ | $1.3\times10^{14}$ $^{21}$ | 1 $^{12}$ | $0.49\pm0.06$ $^{26}$ |  | $3.1\pm0.86$ $^{11}$ |  |  |  |  |
| LESSJ033229.4-275619 | 4.755 | $4.20\times10^{12}$ $^{14}$ | $1.8\times10^{14}$ $^{22}$ | 0 $^{11}$ | $0.09\pm0.02$ $^{14}$ |  |  |  |  |  |  |

35pt35pt **References:** $^1$ (cite: Barvainis_2002), $^2$ (cite: 2007AJ....133..564W), $^3$ (cite: 2010ApJ...724..957S), $^4$ (cite: 2011ApJ...739L..31R), $^5$ (cite: 2004ApJ...614L..97V), $^6$ (cite: 2003A&A...409L..41W), $^7$ (cite: Downes_2003), $^8$ (cite: Carilli_2005), $^9$ (cite: 2012MNRAS.423.2132S), $^{10}$ (cite: 2011ApJ...730...18W) , $^{11}$ (cite: 2006ApJ...650..604R), $^{12}$ (cite: 2008ApJ...686L...9R), $^{13}$ (cite: 2012ApJ...752L..30W), $^{14}$ (cite: 2010MNRAS.407L.103C), $^{15}$ (cite: 2021ApJ...923...59V), $^{16}$ (cite: 2008A&A...491..173A), $^{17}$ (cite: 1993MNRAS.261..299C), $^{18}$ (cite: Lutz_2007), $^{19}$ (cite: 2006AJ....132.1307P), $^{20}$ (cite: 2011ApJ...740L..29F), $^{21}$ (cite: 2013A&A...559A..29C), $^{22}$ (cite: Gilli_2011), $^{23}$ (cite: Venturini_2003), $^{24}$ (cite: 1999Sci...286.2493P), $^{25}$ (cite: 2011ApJ...739L..33C), $^{26}$ (cite: 2002AJ....123.1838C), $^{27}$ (cite: 2008AJ....136.1118A), $^{28}$ (cite: Bradford_2009), $^{29}$ (cite: 2007A&A...467..955W), $^{30}$ (cite: 2004A&A...423..441B), $^{31}$ (cite: 2012ApJ...753..102W), $^{32}$ (cite: 2018ApJ...864...38L)

# Dust SED fitting

| Name | $\log(M_\mathrm{dust} / \mathrm{M_\odot})$ | $T_\mathrm{dust}$ (K) | $\beta$ | $\log(L_\mathrm{FIR, 40-400\mu m} / L_\odot)$ | $\log(L_\mathrm{FIR, 42.5-122.5\mu m} / L_\odot )$ |
|:---|:---|:---|:---|:---|:---|
| P036+03 | $8.1_{-0.3}^{+0.5}$ | \- | $1.7_{-0.2}^{+0.3}$ | $13.21_{-0.26}^{+0.26}$ | $13.14_{-0.26}^{+0.24}$ |
| J0305-3150 | $9.5_{-0.2}^{+0.2}$ | $29_{-\phantom{0}2}^{+\phantom{0}2}$ | $2.1_{-0.1}^{+0.1}$ | $12.78_{-0.05}^{+0.05}$ | $12.65_{-0.07}^{+0.08}$ |
| J2348-3054 | $8.0_{-0.2}^{+0.3}$ | $61_{-13}^{+18}$ | $1.4_{-0.2}^{+0.2}$ | $12.93_{-0.13}^{+0.18}$ | $12.87_{-0.13}^{+0.17}$ |
| J0927+2001 | $8.5_{-0.3}^{+0.5}$ | \- | $2.0_{-0.3}^{+0.4}$ | $13.60_{-0.33}^{+0.53}$ | $13.52_{-0.32}^{+0.50}$ |
| J0129-0035 | $8.0_{-0.3}^{+0.5}$ | \- | $1.4_{-0.3}^{+0.4}$ | $12.94_{-0.25}^{+0.32}$ | $12.87_{-0.25}^{+0.30}$ |
| J0840+5624 | $8.6_{-0.6}^{+0.5}$ | $40_{-10}^{+25}$ | $2.0_{-0.6}^{+0.6}$ | $12.90_{-0.20}^{+0.43}$ | $12.80_{-0.24}^{+0.46}$ |
| J2310+1855 | $9.3_{-0.1}^{+0.1}$ | $34_{-\phantom{0}1}^{+\phantom{0}1}$ | $2.0_{-0.1}^{+0.1}$ | $13.10_{-0.02}^{+0.02}$ | $13.01_{-0.03}^{+0.03}$ |
| J2054-0005 | $8.4_{-0.3}^{+0.3}$ | $45_{-10}^{+13}$ | $1.8_{-0.5}^{+0.6}$ | $12.91_{-0.08}^{+0.08}$ | $12.85_{-0.08}^{+0.08}$ |
| J1429+5447 | $8.2_{-0.3}^{+0.5}$ | \- | \- | $13.03_{-0.34}^{+1.91}$ | $12.97_{-0.34}^{+1.76}$ |
| J0100+2802 | $7.7_{-0.3}^{+0.5}$ | \- | $0.7_{-0.2}^{+0.5}$ | $12.52_{-0.30}^{+0.37}$ | $12.45_{-0.32}^{+0.36}$ |
| J1148+5251 | $8.4_{-0.4}^{+0.4}$ | \- | $2.1_{-0.3}^{+0.3}$ | $13.24_{-0.20}^{+0.36}$ | $13.18_{-0.20}^{+0.33}$ |

25pt25pt \*\* In cases where the fit parameters were poorly constrained (essentially returning the priors), we do not quote the results.

We fit the dust SEDs with a modified blackbody of the form, $$\begin{align}
                S\Delta v ^\mathrm{against~CMB} (\nu_\mathrm{rest}) = \dfrac{f_\mathrm{CMB}(1+z)}{d_L^2} M_\mathrm{dust} \kappa_\mathrm{\nu_{rest}} \left(B[T_\mathrm{CMB}] - B[T_\mathrm{dust}] \right)
            
\end{align}$$ where $d_L$ is the luminosity distance, $B (\nu, T)$ is the blackbody function and the contrast against the CMB is accounted for by $f_\mathrm{CMB} = 1- B_\mathrm{\nu} [T_\mathrm{CMB}(z)] / B_\mathrm{\nu} [T_\mathrm{dust}(z)]$ (cite: 2013ApJ...765....9D). We thereby assume optically thin dust emission at $\lambda>40$ μm and correct for both the heating by and contrast against the CMB. We assumed that the dust opacity scales as $\kappa_{\nu_\mathrm{rest}} = \kappa_{\nu_0} (\nu_\mathrm{rest} /\nu_0)^\beta$ where $\beta$ is the dust spectral emissivity index. Following (cite: 2003MNRAS.341..589D) we take $\nu_0 = c/(125$μm) and $\kappa_{\nu_0} = 2.64~\mathrm{m^2 kg^{-1}}$. We used a Bayesian approach to fit the dust SEDs and recover posterior likelihood distributions for the log of the total dust mass ($\log(M_\mathrm{dust})$), the dust temperature ($T_\mathrm{dust}$) and dust emissivity index ($\beta$). We apply uniform priors of $2.73 (1+z) < T_\mathrm{dust} < 100$, $6 < \log{M_\mathrm{dust}} < 11$ and $1 < \beta < 3$.

Because we are assuming thermal dust, we only included observations sampling the dust SED at $\lambda_\mathrm{rest}>70$ μm. At shorter wavelengths, the effects from stochastically heated grains become more dominant (cite: 2021ApJ...919...30D) and contamination by QSO non-thermal and torus emission becomes significant (cite: Leipski_2014). We also omitted data at the other end of the SED, in the radio regime where synchrotron and free-free emission dominate ($\nu_\mathrm{rest}\lesssim 100$ GHz). To sample the probability distributions we applied Markov Chain Monte Carlo sampling via the `emcee` package (cite: 2013PASP..125..306F). The resulting likelihood posteriors as well as the median, 16th and 84th percentile values are shown for our sample and the literature sample in Fig. [7](#fig:dust_seds_our_sample) and [8](#fig:dust_seds_lit_sample), respectively. The data that were fit are shown as light blue circles. We also show additional continuum data that were not fit, in purple. The derived values are provided in Table [\[tab:dust_sed\]](#tab:dust_sed).

![image](P036+03_dust_fit.png)\
![image](J0305-3150_dust_fit.png)

![](J2348-3054_dust_fit.png)

![image](J0927+2001_dust_fit.png)\
![image](J0129-0035_dust_fit.png)

![image](J0840+5624_dust_fit.png)\
![image](J2310+1855_dust_fit.png)

![image](J2054-0005_dust_fit.png)\
![image](J1429+5447_dust_fit.png)

![image](J0100+2802_dust_fit.png)\
![image](J1148+5251_dust_fit.png)

[^1]: (cite: 2018ApJ...869...27V) and (cite: 2020ApJ...902..109B) calibrated the atomic carbon abundance against the CO-derived molecular gas masses, for which they assume a Milky-Way-like $\alpha_\mathrm{CO}$, which is higher than the ULIRG value assumed for similar calibrations of higher-redshift sub-millimetre/IR-bright galaxies.

[^2]: representing the total luminosity produced by the accretion disk

[^3]: $L_\mathrm{bol}=5.15\,\lambda L_\mathrm{\lambda,3000}$

[^4]: via $L_\mathrm{bol} = 3500 L_\mathrm{[O III]}$

[^5]: <https://interferopy.readthedocs.io/en/latest/>

</paper>

Write the methods card for this paper.