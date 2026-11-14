# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...994..158G\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...994..158G",
 "title": "Oxygen Isotopes Reveal Low-mass Star Dominance in the Small Magellanic Cloud",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Gong, Yan",
 "n_authors": 12,
 "arxiv_id": "2510.16343",
 "doi": "10.3847/1538-4357/ae1035",
 "alma_projects_linked_by_archive": [
  "2015.1.00196.S",
  "2023.1.01576.S"
 ]
}
```

Paper text:
<paper>
# Oxygen isotopes reveal low-mass star dominance in the Small Magellanic Cloud

## Abstract

Oxygen isotope abundances and their ratios are fingerprints of stellar evolution and therefore provide a powerful tool in tracing the enrichment history of galaxies. However, their behavior in low-metallicity dwarf galaxies remains largely unexplored. The Small Magellanic Cloud (SMC), a nearby analog of young high-redshift galaxies, offers an ideal laboratory to investigate this regime. Using the Atacama Compact Array, we observed the $J=2\to 1$ transitions of $^{12}$CO, $^{13}$CO, C$^{18}$O, and C$^{17}$O from the massive star-forming region LIRS 36 (aka N12A), achieving the first detection of C$^{17}$O in the SMC. This detection enables the first direct measurement of the $^{18}$O/$^{17}$O abundance ratio of 0.87$\pm$0.26 in this galaxy, substantially lower than all values in the literature, including molecular clouds in the Milky Way and other galaxies. Such a low ratio of $^{18}$O/$^{17}$O, together with a high $^{13}$CO/C$^{18}$O ratio, indicates chemical enrichment dominated by low-mass stars, consistent with the observed paucity of high-mass stars in the SMC. We suggest that the SMC is governed by a top-light integrated galaxy-wide initial mass function, predicted by the SMC’s persistently low star-formation activities.

show\]ygong@pmo.ac.cn

# Introduction

Isotopic abundance ratios serve as powerful diagnostics of stellar nucleosynthesis, providing insight into the impact of stellar yields, the composition of stellar populations, and the broader context of galactic chemical evolution (cite: 1994ARA&A..32..191W; 2017MNRAS.470..401R; 2018Natur.558..260Z; 2022A&ARv..30....7R; 2023AA...670A..98Y; 2023A&A...679L...6G; 2024ApJ...970..136G). Oxygen, the most abundant metal element in the Universe, exhibits isotopic diversity with rare isotopes. For example, $^{18}$O is primarily synthesized through $\rm ^{14}N(\alpha, \gamma)^{18}F(\beta^+)^{18}O$ reaction during helium burning in massive stars, while $^{17}$O is produced in the hydrogen-burning zones of lower-mass stars via the cold or hot CNO cycles (cite: 1994ARA&A..32..191W; 2022A&ARv..30....7R). Novae may represent an important source of $^{17}$O enrichment, as shown in Galactic chemical evolution simulations (cite: 2003MNRAS.342..185R) and nova model calculations (cite: 1998ApJ...494..680J). Consequently, $^{17}$O is commonly injected into the interstellar medium (ISM) more slowly than $^{18}$O.

On the other hand, oxygen isotopes are not subject to chemical fractionation (cite: 1984ApJ...277..581L), since the scarcity of O$^{+}$ in molecular clouds make charge–exchange reactions negligible. Furthermore, the $^{18}$O/$^{17}$O isotope ratios can be directly determined by the optically thin transitions of C$^{18}$O and C$^{17}$O (cite: 2008A&A...487..237W; 2020ApJS..249....6Z; 2023MNRAS.522..559O). Isotope-selective photodissociation is unlikely to significantly affect these ratios, as both CO isotopologues exhibit similar self-shielding properties (cite: 2009A&A...503..323V). These properties make $^{18}$O/$^{17}$O isotope ratios a good probe of nuclear processing and metal enrichment in galaxies.

Recent studies have revealed a tentative gradient in the Milky Way, with the $^{18}$O/$^{17}$O isotope ratio increasing from the Galactic center ($\sim$3) toward the outer Galaxy (cite: 2008A&A...487..237W; 2020ApJS..249....6Z; 2023MNRAS.522..559O; 2023AA...670A..98Y). This finding supports an inside-out formation scenario for the Galactic disk (cite: 2001ApJ...554.1044C; 2012A&A...540A..56P). Beyond the Milky Way, $^{18}$O/$^{17}$O ratios have been measured to be $\sim$1.7 in the Large Magellanic Cloud (LMC) (cite: 1998A&A...332..493H; 2009ApJ...690..580W), $\gtrsim$8 in nearby starburst galaxies (cite: 1993AA...274..730H; 2021AA...656A..46M), and $>$10 in two intermediate redshift galaxies at $z =0.68$ and 0.89 (cite: 1995A&A...303L..61C; 2006A&A...458..417M; 2023AA...674A.101M). Despite these advances, determining the oxygen isotope ratios in very metal-poor galaxies ($Z\lesssim$0.2 $Z_{\odot}$), including local dwarf galaxies and low-metallicity galaxies at high redshift, is challenging, but essential to understand their role in the oxygen enrichment of the Universe (cite: 2022Galax..10...11H).

The Small Magellanic Cloud (SMC), at a distance of 62.1$\pm$1.9 kpc (cite: 2014ApJ...780...59G), is a nearby dwarf irregular galaxy with low star formation rates (cite: 2004AJ....127.1531H). Its gas-phase metallicity is characterized by an oxygen abundance of O/H$\sim 10^{-4}$ ($\sim$0.2 $Z_{\odot}$; e.g., (cite: 1997macl.book.....W)), while its nitrogen abundance is even more deficient at N/H$\sim 3.2\times10^{-6}$ (cite: 1998RMxAC...7..202K; 2022MNRAS.517.4497D). These make the SMC the best testbed to study metal-poor environments in the Local Group and a unique prototype for understanding the properties of metal-poor galaxies which were ubiquitous in the early Universe. Precise measurements of the gas-phase $^{18}$O/$^{17}$O isotope ratios in the SMC will yield important insight into its chemical evolution and establish it as a benchmark for studies of extremely metal-poor galaxies.

Several attempts have been undertaken to measure the isotope ratios of elements in the SMC. However, the results are still inconclusive. For instance, (cite: 1998A&A...330..901C) and (cite: 1998A&A...332..493H) attempted to detect C$^{18}$O in the SMC, but were unsuccessful. Their lower limits of the $^{13}$CO/C$^{18}$O line intensity ratios are much higher than those observed in Galactic molecular clouds. This finding was later confirmed by ALMA observations (cite: 2017ApJ...844...98M; 2018Natur.558..260Z), which revealed remarkably high intensity ratios of around 100. Similarly, (cite: 1999A&A...344..817H) reported a non-detection of C$^{18}$O and C$^{17}$O. As a result, the oxygen isotope ratios in the SMC remain largely unconstrained. Therefore, we performed new ALMA observations toward a molecular cloud in SMC, LIRS 36 (aka N12A), to measure the C$^{18}$O and C$^{17}$O emission and their abundance ratios. The observations are described in Sect. [2](#Sec:obs), and the results are presented in Sect. [3](#Sec:res). We discuss the implications of our findings in Sect. [4](#Sec:dis), and provide a summary in Sect. [5](#Sec:sum).

# Observations and data reduction

Based on the recently completed APEX $^{12}$CO $J=3\to 2$ and $^{13}$CO $J=3\to 2$ survey (C.-H. Rosie Chen, in prep.), which covers 5.1 square degrees of molecular clouds in the SMC, LIRS 36 in the southwest bar is identified as the brightest position in $^{13}$CO $J=3\to 2$ emission (see also (cite: 2024A&A...687A..26S) for a smaller $^{12}$CO $J=3\to 2$ survey of the SMC Bar at a shallower depth). The observations have an angular resolution of 18$''$ ($\sim$5.4 pc). This indicates that LIRS 36 has the highest $^{13}$CO (and therefore H$_{2}$) column density on the scale probed by the survey. Previous single-dish observations also suggest that LIRS 36 is one of the most prolific molecular line sources in the SMC (cite: 1998A&A...330..901C; 2016ApJ...822..105A). Therefore, we selected LIRS 36 as the target to search for rare CO isotopologues.

The observations of LIRS 36 (project code: 2023.1.01576.S, PI: Yan Gong) were conducted between 2024 June 24 and August 23 using the Atacama Compact Array (cite: 2009PASJ...61....1I). The phase center of the observations was located at ($\alpha_{\rm J2000}$, $\delta_{\rm J2000}$)=(00$^{\rm h}$46$^{\rm m}$40$^{\rm s}$8, $-$73$^{\circ}$06$^{\prime}$14$^{\prime\prime}$4). Observations were performed using the ALMA Band 6 receivers, covering both spectral line and continuum emission with two frequency setups comprising 16 spectral windows in total. In this study, we focus on four spectral windows centered on the $^{12}$CO $J=2\to1$, $^{13}$CO $J=2\to1$, C$^{18}$O $J=2\to1$, and C$^{17}$O $J=2\to1$ transitions. The former three transitions were observed simultaneously, while the last line was observed independently. The spectral channel width was 244 kHz, corresponding to a velocity spacing of $\sim$0.3 km s$^{-1}$ for the four transitions. The bandpass and flux calibrator was J2258$-$2758, while the phase calibrator was J0102$-$7546. The observations employed 7–10 antennas with baseline lengths of 8.9–48.9 m and a total of $\sim$60 hours of telescope time.

The raw data were calibrated using the ALMA pipeline of the Common Astronomy Software Applications (CASA) package (cite: 2022PASP..134k4501C). Subsequent imaging of the calibrated data was performed manually with CASA version 6.5.4. The image reconstruction was carried out using the “tclean” task, employing the Högbom algorithm (cite: 1974A&AS...15..417H) and Briggs weighting with a robust parameter of 0.5. The automated masking algorithm “AUTO-MULTITHRESH” was adopted in the task, with parameters set identically to those listed in Table 2 of (cite: 2020PASP..132b4505K). All cleaned images have a pixel size of 1$''$1, corresponding linearly to approximately 1/5 of their synthesized beams. A primary beam correction was applied to all cleaned data. The observational details are summarized in Table [1](#Tab:lin). Based on the measurements of the calibrators, the flux calibration accuracy is estimated to be better than 10%.

Total-power (TP) $^{12}$CO $J=2\to 1$, $^{13}$CO $J=2\to 1$, and C$^{18}$O $J=2\to 1$ observations were conducted in 2016 June and August (project code: 2015.1.00196.S; PI: Julia Roman-Duval). The target region was mapped using on-the-fly (OTF) mapping with Nyquist sampling, covering a 2$\ensuremath{'} \times$2$\ensuremath{'}$ rectangular region centered at ($\alpha_{\rm J2000}$, $\delta_{\rm J2000}$) = (00$^{\rm h}$46$^{\rm m}$41$^{\rm s}$279, $-$73$^{\circ}$05$^{\prime}$77$^{\prime\prime}$797). The single-dish data were reduced using the standard CASA pipeline. The half-power beam widths (HPBWs) are 29$\ensuremath{''}$1, 30$\ensuremath{''}$3, and 30$\ensuremath{''}$4 for transitions of $^{12}$CO, $^{13}$CO, and C$^{18}$O, respectively. The typical 1-$\sigma$ noise levels per 244 kHz (i.e., 0.3 km s$^{-1}$) channel are $\sim$0.5 Jy beam$^{-1}$ for both $^{12}$CO $J=2\to 1$ and $^{13}$CO $J=2\to 1$, and $\sim$ 0.4 Jy beam$^{-1}$ for C$^{18}$O $J=2\to 1$. In this study, we only adopt the $^{12}$CO $J=2\to 1$ and $^{13}$CO $J=2\to 1$ data to recover the missing flux in our ACA observations, as C$^{18}$O $J=2\to 1$ was not detected in the TP observations. The combination of the single-dish and ACA datasets was performed using the “feather” task in CASA. To reduce the different beam dilution effects, all data were convolved to a common circular beam of 7$''$5 for subsequent analysis.

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Transition | Frequency | Date | PWV | $\theta_{\rm maj}\times \theta_{\rm min}$, $PA$ | MRS | $\sigma$ | $\delta v$ |
|  | (MHz) |  | \(mm\) | ($''$$\times$$''$, $^\circ$) | ($''$) | (mJy beam$^{-1}$) | (km s$^{-1}$) |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) |
| $^{12}$CO $J=2\to 1$ | 230538.0000(5) | \[2024-Jul-17, 2024-Aug-23\] | 0.45–2.16 | 6.5$\times$5.7, $-$86 | 29.0 | 11 | 0.32 |
| $^{13}$CO $J=2\to 1$ | 220398.6842(1) | \[2024-Jul-17, 2024-Aug-23\] | 0.45–2.16 | 6.8$\times$6.8, 23 | 30.4 | 10 | 0.33 |
| C$^{18}$O $J=2\to 1$ | 219560.3577(3) | \[2024-Jul-17, 2024-Aug-23\] | 0.45–2.16 | 7.0$\times$6.1, $-$79 | 30.5 | 8 | 0.33 |
| C$^{17}$O $J=2\to 1$ | 224714.3858(3) | \[2024-Jun-24, 2024-Jul-26\] | 0.49–2.12 | 6.8$\times$5.9, $-$73 | 29.7 | 4 | 0.33 |

: Summary of ACA Observations.

Table notes: (1) Transition. (2) Rest frequency. Uncertainties in the last decimal digit, suggested by the Cologne Database for Molecular Spectroscopy (cite: 2016JMoSp.327...95E), are given in parentheses. (3) Observing date. (4) Precipitable water vapor during the observations. (5) Restoring beam. (6) Maximum recoverable scale. (7) Noise level at the corresponding channel width. (8) Channel width in units of km s$^{-1}$.

+----------------------+---------------+-----------------+---------------+----------------------------+----------------------------------------------+----------------------------------------------+
|                      |               |                 |               |                            | f=1                                          | f=0.34                                       |
+:====================:+:=============:+:===============:+:=============:+:==========================:+:============:+:=============================:+:============:+:=============================:+
| 6-7 (lr)8-9          |               |                 |               |                            |              |                               |              |                               |
+----------------------+---------------+-----------------+---------------+----------------------------+--------------+-------------------------------+--------------+-------------------------------+
| Transition           | $v_{\rm lsr}$ | $T_{\rm p}$     | $\Delta v$    | $\int T_{\rm mb} {\rm d}v$ | $T_{\rm ex}$ | $N_{\rm mol}$                 | $T_{\rm ex}$ | $N_{\rm mol}$                 |
+----------------------+---------------+-----------------+---------------+----------------------------+--------------+-------------------------------+--------------+-------------------------------+
|                      | (km s$^{-1}$) | \(K\)           | (km s$^{-1}$) | (K km s$^{-1}$)            | \(K\)        | (cm$^{-2}$)                   | \(K\)        | (cm$^{-2}$)                   |
+----------------------+---------------+-----------------+---------------+----------------------------+--------------+-------------------------------+--------------+-------------------------------+
| \(1\)                | \(2\)         | \(3\)           | \(4\)         | \(5\)                      | \(6\)        | \(7\)                         | \(8\)        | \(9\)                         |
+----------------------+---------------+-----------------+---------------+----------------------------+--------------+-------------------------------+--------------+-------------------------------+
| $^{12}$CO $J=2\to 1$ | 126.2$\pm$0.1 | 13.4$\pm$0.5    | 3.0$\pm$0.1   | 44.0$\pm$0.5               | 18.4$\pm$3   | ...                           | 46.5$\pm$8.2 | ...                           |
+----------------------+---------------+-----------------+---------------+----------------------------+--------------+-------------------------------+--------------+-------------------------------+
| $^{13}$CO $J=2\to 1$ | 126.1$\pm$0.1 | 3.88$\pm$0.04   | 2.1$\pm$0.1   | 8.88$\pm$0.02              | ...          | (5.9$\pm$1.5)$\times 10^{15}$ | ...          | (2.5$\pm$0.6)$\times 10^{16}$ |
+----------------------+---------------+-----------------+---------------+----------------------------+--------------+-------------------------------+--------------+-------------------------------+
| C$^{18}$O $J=2\to 1$ | 125.9$\pm$0.1 | 0.055$\pm$0.004 | 1.6$\pm$0.1   | 0.099$\pm$0.005            | ...          | (5.4$\pm$1.1)$\times 10^{13}$ | ...          | (2.2$\pm$0.5)$\times 10^{14}$ |
+----------------------+---------------+-----------------+---------------+----------------------------+--------------+-------------------------------+--------------+-------------------------------+
| C$^{17}$O $J=2\to 1$ | 126.1$\pm$0.1 | 0.051$\pm$0.003 | 2.1$\pm$0.1   | 0.114$\pm$0.002            | ...          | (6.2$\pm$1.5)$\times 10^{13}$ | ...          | (2.5$\pm$0.6)$\times 10^{14}$ |
+----------------------+---------------+-----------------+---------------+----------------------------+--------------+-------------------------------+--------------+-------------------------------+

Table notes: (1) Transition. (2) Velocity centroid. (3) Peak brightness temperature. (4) Full width at half maximum (FWHM) line width. (5) Integrated intensity. The values are obtained by integrating the velocity range of 105–145 km s$^{-1}$ for $^{12}$CO ($J=2\to 1$) and 122–129 km s$^{-1}$ for the other three transitions. (6)–(7) Excitation temperature and molecular column density assuming a beam filling factor of $f=1$. (8)–(9) Same as (6)–(7), but for $f=0.34$. The observed properties of $^{12}$CO ($2\to 1$) and $^{13}$CO ($2\to 1$) are derived from the ACA+TP combined datasets, whereas those of C$^{18}$O ($2 \to 1$) and C$^{17}$O ($2 \to 1$) are derived from the ACA-only datasets.

# Results

Figures [1](#Fig:N12A)a–[1](#Fig:N12A)d present the spatial distributions of the $J=2\to 1$ transitions of $^{12}$CO and its three isotopologues. All lines are detected and exhibit broadly similar morphologies, with emission peaking at nearly the center of the field of view and extending toward the northwest. The similar morphologies support the assumption that all transitions trace the same bulk molecular gas at the peak. Thanks to the high sensitivity and high angular resolution of our ACA observations, the C$^{17}$O $J=2\to1$ transition is detected with a signal-to-noise ratio of $>$10 (Fig. [1](#Fig:N12A)d), marking the first solid detection of C$^{17}$O in the SMC.

The $^{13}$CO $J=2\to 1$ integrated intensity map peaks at ($\alpha_{\rm J2000}$, $\delta_{\rm J2000}$)=(00$^{\rm h}$46$^{\rm m}$41$^{\rm s}$1, $-$73$^{\circ}$06$^{\prime}$14$^{\prime\prime}$41). The observed spectra toward this position are shown in Figs. [1](#Fig:N12A)e–[1](#Fig:N12A)h, and all exhibit single-peaked, Gaussian-like profiles. To mitigate the effects of potential missing flux (see Appendix [6](#app.a) for further discussion), we extracted spectra at the emission peak and used them to derive the isotopic ratios. We performed a Gaussian fitting to each spectrum (indicated by red lines in Figs. [1](#Fig:N12A)e–[1](#Fig:N12A)h), and the derived parameters are summarized in Table [\[Tab:obs\]](#Tab:obs). The velocity centroids of the four transitions are consistent within the uncertainties and are in good agreement with previous studies (cite: 1997A&A...317..548C; 1998A&A...330..901C). The $^{12}$CO $J=2\to 1$ line exhibits a broader FWHM than the other transitions, most likely due to opacity broadening, and also shows a weak blue-shifted wing not detected in the isotopologues. The integrated intensity ratio of $^{13}$CO/C$^{18}$O is 90$\pm$5, consistent with the high intensity ratios reported for N83C in the SMC (cite: 2017ApJ...844...98M). Such high ratios appear to be a common feature of the bright star-forming regions observed so far in the SMC. A galaxy-wide census of $^{13}$CO and C$^{18}$O emission would be required to assess whether this trend is representative of the global ISM in the SMC.

The C$^{17}$O $J=2\to 1$ line appears slightly broader than that of C$^{18}$O $J=2\to 1$ and shows a blue-shifted asymmetry profile, due to the hyperfine-structure splitting in C$^{17}$O $J=2\to 1$. In Fig. [1](#Fig:N12A)g, we marked the corresponding frequencies and relative intensity of the hyperfine transitions. It is remarkable that the integrated intensity of C$^{17}$O $J=2\to 1$ exceeds that of C$^{18}$O $J=2\to 1$. To our knowledge, this is the first instance in which C$^{17}$O emission exhibits a higher integrated intensity than C$^{18}$O emission in molecular clouds.

Assuming local thermodynamic equilibrium (LTE), optically thick $^{12}$CO $J=2\to1$ emission, and neglecting beam dilution (see Appendix [7](#app.lte)), we derive an excitation temperature of $18.6 \pm 3.0$ K from the peak intensity of the $^{12}$CO $J=2\to1$ line profile. Assuming that the four $J=2\to 1$ transitions have the same excitation temperature, we derive a peak optical depth of 0.34$\pm$0.02 for $^{13}$CO $J=2\to 1$. The optical depths of C$^{18}$O $J=2\to 1$ and C$^{17}$O $J=2\to 1$ are well below 0.01. Even if we assume a beam dilution factor of 0.34 (i.e., a source size of 5$''$4; see Appendix [7](#app.lte)), which increases the excitation temperature to 46.3$\pm$8.2 K, the optical depths of $^{13}$CO $J=2\to 1$, C$^{18}$O $J=2\to 1$, and C$^{17}$O $J=2\to 1$ stay almost unchanged. Hence, these three transitions can be considered optically thin for our study.

Using the LTE approach within the Markov chain Monte Carlo (MCMC) framework (see Appendix [7](#app.lte)) and adopting a 10% uncertainty in flux density, we derive the $^{13}$CO, C$^{18}$O, and C$^{17}$O column densities, as listed in Table [\[Tab:obs\]](#Tab:obs). The corresponding isotope ratios were directly determined from these column densities. Neglecting the beam dilution effects, we obtain $^{13}$C/$^{18}$O=109.3$\pm$35.6, $^{13}$C/$^{17}$O=95.2$\pm$31.4, and $^{18}$O/$^{17}$O=0.87$\pm$0.26. The dependence of the derived isotope ratios on the assumed source sizes is negligible (see Appendix [7](#app.lte)), indicating that these results are robust. Because the $^{12}$CO $J=2\to1$ transition is optically thick, the integrated intensity ratios of the $^{12}$CO $J=2\to1$ line to the C$^{18}$O $J=2\to1$ and C$^{17}$O $J=2\to1$ lines yield only lower limits of $^{16}$O/$^{18}$O$\gtrsim$444 and $^{16}$O/$^{17}$O$\gtrsim$386, respectively.

![](fig/smc-isotope.pdf)

# Discussion

Table [\[Tab:ratio\]](#Tab:ratio) compares oxygen isotope ratios with those measured in various environments. The $^{18}$O/$^{17}$O isotope ratio in the SMC is markedly lower than all previously reported values for molecular clouds in both extragalactic sources and the Milky Way. Given that $^{18}$O/$^{17}$O ratios are a valuable diagnostic for understanding galactic chemical enrichment, we explore the implications of this exceptionally low value below.

+----------------+-------------------+-------------------+-------------------+-----------+
| Region         | $^{18}$O/$^{17}$O | $^{16}$O/$^{18}$O | $^{16}$O/$^{17}$O | reference |
+:==============:+:=================:+:=================:+:=================:+:=========:+
| Extragalactic sources                                                                  |
+----------------+-------------------+-------------------+-------------------+-----------+
| SMC            | 0.87$\pm$0.26     | $\gtrsim$444      | $\gtrsim$386      | a         |
+----------------+-------------------+-------------------+-------------------+-----------+
| LMC            | 1.7$\pm$0.2       | 2000$\pm$250      | 3000$\pm$580      | b         |
+----------------+-------------------+-------------------+-------------------+-----------+
| NGC 253        | 8.7$\pm$1.2       | 48$\pm$5          | 400$\pm$40        | c         |
+----------------+-------------------+-------------------+-------------------+-----------+
| NGC 4945       | 6.4$\pm$0.3       | 200$\pm$50        | 1250$\pm$290      | d         |
+----------------+-------------------+-------------------+-------------------+-----------+
| M82            | 8$\pm$1           | $>$350            | $>$2800           | e, f      |
+----------------+-------------------+-------------------+-------------------+-----------+
| PKS 1830$-$211 | 11.5$\pm$0.5      | 65.3$\pm$0.7      | 751$\pm$34        | g         |
+----------------+-------------------+-------------------+-------------------+-----------+
| NGC 3256       | 5–12              | ...               | ...               | h         |
+----------------+-------------------+-------------------+-------------------+-----------+
| Arp 220        | $>$20             | ...               | ...               | i         |
+----------------+-------------------+-------------------+-------------------+-----------+
| M83            | 5.8–7.1           | ...               | ...               | j         |
+----------------+-------------------+-------------------+-------------------+-----------+
| The Milky Way                                                                          |
+----------------+-------------------+-------------------+-------------------+-----------+
| CMZ            | 3.4$\pm$0.1       | 260$\pm$50        | 890$\pm$160       | k         |
+----------------+-------------------+-------------------+-------------------+-----------+
| Inner disk     | 3.6$\pm$0.2       | 330$\pm$30        | 1180$\pm$130      | k         |
+----------------+-------------------+-------------------+-------------------+-----------+
| Local ISM      | 3.9$\pm$0.4       | 560$\pm$25        | 2180$\pm$240      | k         |
+----------------+-------------------+-------------------+-------------------+-----------+
| Outer Galaxy   | 4.8$\pm$0.6       | 630$\pm$140       | 3000$\pm$790      | k         |
+----------------+-------------------+-------------------+-------------------+-----------+
| Solar          | 5.5               | 490               | 2625              | l         |
+----------------+-------------------+-------------------+-------------------+-----------+

Table notes: $^a$This work; $^b$(cite: 2009ApJ...690..580W); $^c$(cite: 2021AA...656A..46M); $^d$(cite: 2004AA...422..883W); $^e$(cite: 1993AA...274..730H); $^f$(cite: 2010AA...522A..62M); $^g$(cite: 2023AA...674A.101M); $^h$(cite: 2018ApJ...855...49H); $^i$(cite: 2015AA...579A.101A); $^j$(cite: 2018ApJ...855...49H) $^k$(cite: 2023AA...670A..98Y); $^l$(cite: 1989GeCoA..53..197A).

In the Milky Way, low $^{18}$O/$^{17}$O ratios (sometimes below unity) are commonly observed in the circumstellar envelopes of carbon-rich stars (cite: 1994ARA&A..32..191W; 2017A&A...600A..71D; 2024Galax..12...70A). The detection of such a low $^{18}$O/$^{17}$O ratio in the SMC therefore could indicate a substantial contribution from low- and intermediate-mass stars. This is consistent with the finding that, owing to its low metallicity, the SMC hosts a higher fraction of carbon-rich stars than both the Milky Way and the LMC (cite: 1978Natur.271..638B; 1980ApJ...242..938B; 2005A&A...434..691M; 2006ApJ...645.1118S). At lower metallicities, reduced hot-bottom burning and more efficient third dredge-up episodes can help elevate C/O ratios (cite: 2013MNRAS.434..488M; 2014PASA...31...30K; 2018MNRAS.476..496F), enhancing the prevalence and chemical impact of such stars.

The nucleosynthetic origins of the two oxygen isotopes are distinct: $^{17}$O is mainly synthesized in LIMs via $\rm ^{16}O(p, \gamma)^{17}F(\beta^+ \nu)^{17}O$, while $^{18}$O is produced predominantly in high-mass stars through $\rm
^{14}N(\alpha, \gamma)^{18}F(\beta^+)^{18}O$ (cite: 1994ARA&A..32..191W; 2003MNRAS.342..185R; 2022A&ARv..30....7R). Consequently, an unusually low $^{18}$O/$^{17}$O ratio indicates chemical enrichment dominated by low- and intermediate-mass stellar populations, with little contribution from massive stars. This interpretation is consistent with the latest Gaia census of the SMC that finds the number of high-mass stars to be lower by a factor of 3–7 than expected from the low-mass population (cite: 2021A&A...646A.106S), implying a steep slope of the high-mass end of the initial mass function (IMF). Such a top-light IMF may also reduce the number of intermediate-mass stars that dominate $^{14}$N production via the CNO cycle, yielding the markedly low nitrogen abundance observed in the SMC (cite: 1998RMxAC...7..202K; 2022MNRAS.517.4497D) and, in turn, suppressing $^{18}$O synthesis from $^{14}$N in stars. Together, the paucity of intermediate- and high-mass stars provides a coherent explanation for both the $^{18}$O deficit and the low $^{18}$O/$^{17}$O ratio.

The abundances of elements and isotopes trace the cumulative chemical enrichment history of the SMC, extending back to the formation of its first-generation stars at least $\sim$10 Gyr ago (cite: 2004AJ....127.1531H). As oxygen isotopes originate from different stellar mass ranges, their relative abundance ratios are sensitive to the integrated galaxy-wide initial mass function (IGIMF), which depends on star formation rates and metallicity (cite: 2017A&A...607A.126Y; 2018A&A...620A..39J; 2020A&A...637A..68Y; 2023Natur.613..460L). According to the reconstructed star formation history of the SMC (cite: 2009AJ....138.1243H), the overall star formation rates were low, of order $<$0.3  M$_{\odot}$yr$^{-1}$ over the past $\gtrsim$10 Gyr (cite: 2004AJ....127.1531H). Theoretical models predict that such low star formation rates yield a top-light IGIMF, in which the formation of intermediate- and high-mass stars is strongly suppressed (cite: 2017A&A...607A.126Y; 2018A&A...620A..39J). The low $^{18}$O/$^{17}$O ratio that we measure is in line with this prediction, indicating long-term enrichment dominated by low-mass stars.

The ISM of the LMC appears to be well mixed, exhibiting nearly uniform isotope ratios across the galaxy (cite: 1998A&A...332..493H). In the SMC, large-scale mixing of nucleosynthetic products may also be expected, although this remains less well constrained. This expectation is supported by the similar $^{13}$CO/C$^{18}$O integrated intensity ratios observed in two different SMC clouds (see Sect. [3](#Sec:res)), as well as by comparable CNO elemental abundances measured in different SMC regions (cite: 1998RMxAC...7..202K; 2022MNRAS.517.4497D). The unusually low $^{18}$O/$^{17}$O isotope ratio detected in LIRS 36 provides a first indication that this value could be characteristic of the SMC, but establishing whether it is representative on a global scale will require future studies with larger samples.

In contrast, the outer Galaxy of the Milky Way, while also metal-poor, is characterized by higher $^{18}$O/$^{17}$O ratios of $\gtrsim$4 (cite: 2008A&A...487..237W; 2020ApJS..249....6Z; 2023MNRAS.522..559O). This difference supports our interpretation that the measured oxygen isotope ratios provide independent evidence for a top-light IGIMF in the SMC. Such a top-light IGIMF may be a common feature for the population of low-metallicity dwarf galaxies. A potential cause for the low star formation efficiencies observed in nearby extremely metal-poor galaxies (cite: 2014Natur.514..335S) could be the top-light IGIMF implied by our SMC $^{18}$O/$^{17}$O measurement.

# Summary and conclusion

In this work, we performed $^{12}$CO $J=2\to 1$, $^{13}$CO $J=2\to 1$, C$^{18}$O $J=2\to 1$, and C$^{17}$O $J=2\to 1$ observations with the Atacama Compact Array (ACA) toward LIRS 36, an active star-forming region in the Small Magellanic Cloud (SMC). Our observations resulted in the first detection of C$^{17}$O in the SMC, enabling a direct and accurate determination of the oxygen isotope ratios: \[$^{13}$C/$^{18}$O\] = 109.3$\pm$35.6, \[$^{13}$C/$^{17}$O\] = 95.2$\pm$31.4, \[$^{18}$O/$^{17}$O\] = 0.87$\pm$0.26, \[$^{16}$O/$^{18}$O\]$\gtrsim$444, and \[$^{16}$O/$^{17}$O\]$\gtrsim$386. This establishes a key benchmark for the oxygen isotopic ratio in the SMC and similar metal-poor dwarf galaxies. The $^{18}$O/$^{17}$O ratio in LIRS 36 is lower than all previously reported values for molecular clouds in both extragalactic sources and the Milky Way, indicating chemical enrichment dominated by low-mass stars. This is consistent with the top-light IGIMF expected from the SMC’s long-term low star formation rate. Our findings imply that such a top-light IGIMF may be a general feature of low-metallicity dwarf galaxies. Future systematic surveys of oxygen isotope ratios in local dwarf galaxies and low-metallicity galaxies at high redshift will be essential for advancing our understanding of stellar population and chemical evolution across cosmic time.

We thank the ALMA staff for their invaluable assistance throughout our observations. Y.G. was supported by the Ministry of Science and Technology of China under the National Key R&D Program under grant No. 2023YFA1608200, the National Natural Science Foundation of China (NSFC) under grant No. 12427901, and the Strategic Priority Research Program of the Chinese Academy of Sciences under grant No. XDB0800301. We acknowledge the support of the NSFC under grant No. 12041305, 12173016, 1257030642, and 12533003. C.H. acknowledges support by the Chinese Academy of Sciences President’s International Fellowship Initiative under grant No. 2025PVA0048. C.-H.R. C. acknowledges support from the Deutsches Zentrum für Luft- und Raumfahrt (DLR) grant NS1 under contract no. 50 OR 2214. W.Y. acknowledges the support from the NSFC (12403027), China Postdoctoral Science Foundation (2024M751376), and Jiangsu Funding Program for Excellent Postdoctoral Talent (2024ZB347). X.D.T. acknowledges the support of the National Key R&D Program of China under grant No. 2023YFA1608002, the Tianshan Talent Training Program of Xinjiang Uygur Autonomous Region under grant No. 2022TSYCLJ0005, and the Chinese Academy of Sciences (CAS) “Light of West China" Program under grant No. xbzg-zdsys-202212. We thank James Urquhart for his careful reading of the manuscript and for providing valuable comments. We thank Xiaoting Fu for fruitful discussions on stellar nucleosynthesis. This research has made use of NASA’s Astrophysics Data System. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2023.1.01576.S and ADS/JAO.ALMA#2015.1.00196.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

Y.G. served as the Principal Investigator of the ACA observing project, performed the data reduction, and drafted the initial manuscript. Z.Y.Z. first proposed the IGIMF concept in connection with isotope ratios and substantially revised the manuscript. C.H. contributed to the initial development of the project and to the writing of the manuscript. C.-H.R.C. assisted in selecting the target from her SMC CO survey. W.Y. resolved LaTeX issues and prepared the tables. All authors contributed to the discussion of the results and the revision of the manuscript.

# Facilities

ALMA, ACA, TP

# Software

astropy (cite: 2022ApJ...935..167A), NumPy (cite: 5725236), SciPy (cite: jones2001scipy), Matplotlib (cite: Hunter:2007), CASA (cite: 2022PASP..134k4501C), GILDAS (cite: 2005sf2a.conf..721P), emcee (cite: 2013PASP..125..306F).

# Short spacing

To quantify the contribution of single-dish data in recovering the flux densities of our ACA observations, we compare the ACA-only and ACA+TP datasets in Fig. [2](#Fig:N12A-mf). For the total flux density integrated over the field of view, the ACA-only data account for only 70% and 82% of the total flux densities in the ACA+TP combined data for $^{12}$CO $J=2 \to 1$ and $^{13}$CO $J=2 \to 1$, respectively. Based on the spectra at the peak position (see Fig. [2](#Fig:N12A-mf)a), the ACA-only spectra account for 83% and 97% of the flux densities of the ACA+TP combined spectra for $^{12}$CO $J=2 \to 1$ and $^{13}$CO $J=2 \to 1$, respectively. This comparison indicates that the $^{12}$CO $J=2 \to 1$ emission exhibits a moderate missing flux, emphasizing the need for total power data to accurately determine its brightness temperatures. In contrast, $^{13}$CO $J=2 \to 1$ emission is more compact and less affected by the absence of short spacings. Notably, the flux density of $^{13}$CO $J=2 \to 1$ shows negligible missing flux at the peak position. Given their lower optical depths, C$^{18}$O $J=2 \to 1$ and C$^{17}$O $J=2 \to 1$ are expected to have spatial distributions more similar to $^{13}$CO $J=2 \to 1$ than to $^{12}$CO $J=2 \to 1$, and are in fact observed to be even more compact (see Figs. [1](#Fig:N12A)b–[1](#Fig:N12A)d). Therefore, we conclude that the missing flux in the ACA-only data is negligible for the C$^{18}$O $J=2 \to 1$ and C$^{17}$O $J=2 \to 1$ spectra at the peak position, thus supporting the robustness of our analysis in Sect. [3](#Sec:res).

![](fig/smc-N12A-mf.pdf)

# Local thermodynamic equilibrium

Under local thermodynamic equilibrium (LTE) conditions, excitation temperatures are indispensable to derive molecular column densities. According to the radiative transfer equation (cite: 2015PASP..127..266M), the peak brightness temperature can be expressed as: $$\begin{equation}
\label{f.rad}
T_{\rm p} = f[J_{\nu}(T_{\rm ex})-J_{\nu}(T_{\rm bg})][1-{\rm exp}(-\tau)] \;,
\end{equation}$$ where $J_{\nu}(T)$ is given by: $$\begin{equation}
\label{f.jv}
J_{\nu}(T) = \frac{h\nu/k}{{\rm exp}(\frac{h\nu}{kT})-1}  \;,
\end{equation}$$ with $f$ representing the beam dilution factor, $\tau$ the optical depth, $T_{\rm bg}$ the background temperature, which is set to be 2.73 K (cite: 2009ApJ...707..916F). Here, the Planck constant, $h$, is 6.626$\times 10^{-27}$ erg s, the Boltzmann constant, $k$, is 1.38$\times 10^{-16}$ erg K$^{-1}$, and $\nu$ is the rest frequency. Assuming that $^{12}$CO $J=2\to 1$ is optically thick and neglecting the beam dilution effects (i.e., $\tau \approx \infty$ and $f\sim 1$), we can derive excitation temperatures from the peak brightness temperatures of $^{12}$CO $J=2\to 1$ using Eqs. ([\[f.rad\]](#f.rad))–([\[f.jv\]](#f.jv)). Assuming that the $J=2\to 1$ transitions of $^{13}$CO, C$^{18}$O, and C$^{17}$O have the same excitation temperature as that of $^{12}$CO $J=2 \to 1$, their optical depths can be estimated with Eqs. ([\[f.rad\]](#f.rad)).

To model the excitation temperature and molecular column densities simultaneously, we use the CLASS extension Weeds for the LTE spectral modeling (cite: 2011A&A...526A..47M). For the synthetic Weeds model, we assume a single Gaussian component for all molecules for simplicity. The Weeds model is defined by a set of five parameters: molecular column density, excitation temperature, source size, systemic velocity, and FWHM line width. The systemic velocities and FWHM line widths are based on Table [\[Tab:obs\]](#Tab:obs). The FWHM line width of C$^{17}$O $J=2\to 1$ is set to be identical to C$^{18}$O $J=2\to 1$, as the FWHM line width of C$^{17}$O $J=2\to 1$ is overestimated by the Gaussian fitting in Table [\[Tab:obs\]](#Tab:obs) as a result of the hyperfine-structure splitting. Therefore, we have three free parameters for each line. In this study, we only aim to derive the column densities for $^{13}$CO, C$^{18}$O, and C$^{17}$O.

To fit the observed spectra, we employed the *emcee* package (cite: 2013PASP..125..306F), which applies the affine-invariant ensemble sampler (cite: 2010CAMCS...5...65G) within a Markov chain Monte Carlo (MCMC) framework. This method enables a thorough exploration of the posterior distributions of the model parameters. We assumed uniform priors for the excitation temperature, $T_{\rm ex}$, $^{13}$CO column density, $N_{\rm ^{13}CO}$, C$^{18}$O column density, $N_{\rm C^{18}O}$, and C$^{17}$O column density, $N_{\rm C^{17}O}$. The posterior probability was calculated as the product of the prior and the likelihood, where the likelihood was taken to be Gaussian, $\mathcal{L} \propto \exp(-\chi^{2}/2)$, with $$\begin{equation}
\label{f.chi}
\chi^{2} = \sum_{i} \left( \frac{T_{{\rm obs},i} - T_{{\rm mod},i}}{\sigma_{i}} \right)^{2} \;,
\end{equation}$$ and $T_{{\rm obs},i}$, $T_{{\rm mod},i}$, and $\sigma_{i}$ denoting the observed and modeled peak brightness temperature, as well as the corresponding 1$\sigma$ observational uncertainties, respectively. The MCMC sampling was carried out with 10 walkers over 4500 iterations, following an initial burn-in phase to ensure convergence. The reported best-fit values and associated 1$\sigma$ errors correspond to the 16th and 84th percentiles of the posterior distributions.

Assuming the four lines trace the same parcel of molecular gas, we assume the same source size for the four lines. The source size is directly related to the beam dilution factor with $f=\frac{\theta_{\rm s}^{2}}{\theta_{\rm s}^{2}+\theta_{\rm b}^{2}}$. For the fiducial case, we neglect the beam dilution effects by assuming $f\sim 1$. The modeling results are shown in Fig. [3](#Fig:mcmc), where the four parameters are well constrained. Our approach results in $T_{\rm ex}$=18.4$\pm$3.0 K, $N_{^{13}{\rm CO}}$=(5.9$\pm$1.5)$\times 10^{15}$ cm$^{-2}$, $N_{{\rm C^{18}O}}$=(5.4$\pm$1.1)$\times 10^{13}$ cm$^{-2}$, and $N_{{\rm C^{17}O}}$=(6.2$\pm$1.3)$\times 10^{13}$ cm$^{-2}$. The derived isotope ratios are \[$^{13}$C/$^{18}$O\] = 109.3$\pm$35.6, \[$^{13}$C/$^{17}$O\] = 95.2$\pm$31.4, and \[$^{18}$O/$^{17}$O\] = 0.87$\pm$0.26. In order to test the impact of the assumed source size on the derived isotope ratios, the MCMC approach was performed again by assuming $\theta_{\rm s}$=5$''$4 which was inferred from the Gaussian fitting of the compact component in Fig. [1](#Fig:N12A)d. The physical parameters change to $T_{\rm ex}$=46.5$\pm$8.2 K, $N_{^{13}{\rm CO}}$=(2.5$\pm$0.6)$\times 10^{16}$ cm$^{-2}$, $N_{{\rm C^{18}O}}$=(2.2$\pm$0.5)$\times 10^{14}$ cm$^{-2}$, and $N_{{\rm C^{17}O}}$=(2.5$\pm$0.6)$\times 10^{14}$ cm$^{-2}$, indicating \[$^{13}$C/$^{18}$O\] = 113.3$\pm$37.6, \[$^{13}$C/$^{17}$O\] = 100.0$\pm$33.9, and \[$^{18}$O/$^{17}$O\] = 0.88$\pm$0.29. This suggests that the different source sizes affect $T_{\rm ex}$, $N_{\rm ^{13}CO}$, $N_{\rm C^{18}O}$, and $N_{\rm C^{17}O}$ significantly, but the isotope ratios remain almost identical. Therefore, the derived isotope ratios in the SMC are robust.

![](fig/mcmc.pdf)

natexlab

(ref: 2016ApJ...822..105A) Acharyya, K., & Herbst, E. 2016, ApJ, 822, 105, doi: [`10.3847/0004-637X/822/2/105`](http://doi.org/10.3847/0004-637X/822/2/105)

(ref: 2015AA...579A.101A) Aladro, R., Martı́n, S., Riquelme, D., et al. 2015, A&A, 579, A101, doi: [`10.1051/0004-6361/201424918`](http://doi.org/10.1051/0004-6361/201424918)

(ref: 2024Galax..12...70A) Alcolea, J., Masa, E., Khouri, T., et al. 2024, Galaxies, 12, 70, doi: [`10.3390/galaxies12060070`](http://doi.org/10.3390/galaxies12060070)

(ref: 1989GeCoA..53..197A) Anders, E., & Grevesse, N. 1989, , 53, 197, doi: [`10.1016/0016-7037(89)90286-X`](http://doi.org/10.1016/0016-7037(89)90286-X)

(ref: 2022ApJ...935..167A) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: 1978Natur.271..638B) Blanco, B. M., Blanco, V. M., & McCarthy, M. F. 1978, Nature, 271, 638, doi: [`10.1038/271638a0`](http://doi.org/10.1038/271638a0)

(ref: 1980ApJ...242..938B) Blanco, V. M., McCarthy, M. F., & Blanco, B. M. 1980, ApJ, 242, 938, doi: [`10.1086/158527`](http://doi.org/10.1086/158527)

(ref: 2022PASP..134k4501C) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: 2001ApJ...554.1044C) Chiappini, C., Matteucci, F., & Romano, D. 2001, ApJ, 554, 1044, doi: [`10.1086/321427`](http://doi.org/10.1086/321427)

(ref: 1998A&A...330..901C) Chin, Y. N., Henkel, C., Millar, T. J., Whiteoak, J. B., & Marx-Zimmer, M. 1998, A&A, 330, 901, doi: [`10.48550/arXiv.astro-ph/9710253`](http://doi.org/10.48550/arXiv.astro-ph/9710253)

(ref: 1997A&A...317..548C) Chin, Y. N., Henkel, C., Whiteoak, J. B., et al. 1997, A&A, 317, 548, doi: [`10.48550/arXiv.astro-ph/9606081`](http://doi.org/10.48550/arXiv.astro-ph/9606081)

(ref: 1995A&A...303L..61C) Combes, F., & Wiklind, T. 1995, A&A, 303, L61

(ref: 2017A&A...600A..71D) De Nutte, R., Decin, L., Olofsson, H., et al. 2017, A&A, 600, A71, doi: [`10.1051/0004-6361/201629195`](http://doi.org/10.1051/0004-6361/201629195)

(ref: 2022MNRAS.517.4497D) Domı́nguez-Guzmán, G., Rodrı́guez, M., Garcı́a-Rojas, J., Esteban, C., & Toribio San Cipriano, L. 2022, MNRAS, 517, 4497, doi: [`10.1093/mnras/stac2974`](http://doi.org/10.1093/mnras/stac2974)

(ref: 2016JMoSp.327...95E) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95, doi: [`10.1016/j.jms.2016.03.005`](http://doi.org/10.1016/j.jms.2016.03.005)

(ref: 2009ApJ...707..916F) Fixsen, D. J. 2009, ApJ, 707, 916, doi: [`10.1088/0004-637X/707/2/916`](http://doi.org/10.1088/0004-637X/707/2/916)

(ref: 2013PASP..125..306F) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: 2018MNRAS.476..496F) Fu, X., Bressan, A., Marigo, P., et al. 2018, MNRAS, 476, 496, doi: [`10.1093/mnras/sty235`](http://doi.org/10.1093/mnras/sty235)

(ref: 2023A&A...679L...6G) Gong, Y., Henkel, C., Menten, K. M., et al. 2023, A&A, 679, L6, doi: [`10.1051/0004-6361/202348017`](http://doi.org/10.1051/0004-6361/202348017)

(ref: 2010CAMCS...5...65G) Goodman, J., & Weare, J. 2010, Communications in Applied Mathematics and Computational Science, 5, 65, doi: [`10.2140/camcos.2010.5.65`](http://doi.org/10.2140/camcos.2010.5.65)

(ref: 2014ApJ...780...59G) Graczyk, D., Pietrzyński, G., Thompson, I. B., et al. 2014, ApJ, 780, 59, doi: [`10.1088/0004-637X/780/1/59`](http://doi.org/10.1088/0004-637X/780/1/59)

(ref: 2024ApJ...970..136G) Guo, Z., Zhang, Z.-Y., Yan, Z., et al. 2024, ApJ, 970, 136, doi: [`10.3847/1538-4357/ad4da2`](http://doi.org/10.3847/1538-4357/ad4da2)

(ref: 2018ApJ...855...49H) Harada, N., Sakamoto, K., Martı́n, S., et al. 2018, ApJ, 855, 49, doi: [`10.3847/1538-4357/aaaa70`](http://doi.org/10.3847/1538-4357/aaaa70)

(ref: 2004AJ....127.1531H) Harris, J., & Zaritsky, D. 2004, AJ, 127, 1531, doi: [`10.1086/381953`](http://doi.org/10.1086/381953)

(ref: 2009AJ....138.1243H) Harris, J., & Zaritsky, D. 2009, AJ, 138, 1243, doi: [`10.1088/0004-6256/138/5/1243`](http://doi.org/10.1088/0004-6256/138/5/1243)

(ref: 1998A&A...332..493H) Heikkila, A., Johansson, L. E. B., & Olofsson, H. 1998, A&A, 332, 493

(ref: 1999A&A...344..817H) Heikkilä, A., Johansson, L. E. B., & Olofsson, H. 1999, A&A, 344, 817

(ref: 2022Galax..10...11H) Henkel, C., Hunt, L. K., & Izotov, Y. I. 2022, Galaxies, 10, 11, doi: [`10.3390/galaxies10010011`](http://doi.org/10.3390/galaxies10010011)

(ref: 1993AA...274..730H) Henkel, C., & Mauersberger, R. 1993, A&A, 274, 730

(ref: 1974A&AS...15..417H) Högbom, J. A. 1974, A&AS, 15, 417

(ref: Hunter:2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: 2009PASJ...61....1I) Iguchi, S., Morita, K.-I., Sugimoto, M., et al. 2009, PASJ, 61, 1, doi: [`10.1093/pasj/61.1.1`](http://doi.org/10.1093/pasj/61.1.1)

(ref: 2018A&A...620A..39J) Jeřábková, T., Zonoozi, A. H., Kroupa, P., et al. 2018, A&A, 620, A39, doi: [`10.1051/0004-6361/201833055`](http://doi.org/10.1051/0004-6361/201833055)

(ref: jones2001scipy) Jones, E., Oliphant, T., Peterson, P., et al. 2001, SciPy: Open source scientific tools for Python, <http://www.scipy.org/>

(ref: 1998ApJ...494..680J) José, J., & Hernanz, M. 1998, ApJ, 494, 680, doi: [`10.1086/305244`](http://doi.org/10.1086/305244)

(ref: 2014PASA...31...30K) Karakas, A. I., & Lattanzio, J. C. 2014, PASA, 31, e030, doi: [`10.1017/pasa.2014.21`](http://doi.org/10.1017/pasa.2014.21)

(ref: 2020PASP..132b4505K) Kepley, A. A., Tsutsumi, T., Brogan, C. L., et al. 2020, PASP, 132, 024505, doi: [`10.1088/1538-3873/ab5e14`](http://doi.org/10.1088/1538-3873/ab5e14)

(ref: 1998RMxAC...7..202K) Kurt, C. M., & Dufour, R. J. 1998, in Revista Mexicana de Astronomia y Astrofisica Conference Series, Vol. 7, Revista Mexicana de Astronomia y Astrofisica Conference Series, ed. R. J. Dufour & S. Torres-Peimbert, 202

(ref: 1984ApJ...277..581L) Langer, W. D., Graedel, T. E., Frerking, M. A., & Armentrout, P. B. 1984, ApJ, 277, 581, doi: [`10.1086/161730`](http://doi.org/10.1086/161730)

(ref: 2023Natur.613..460L) Li, J., Liu, C., Zhang, Z.-Y., et al. 2023, Nature, 613, 460, doi: [`10.1038/s41586-022-05488-1`](http://doi.org/10.1038/s41586-022-05488-1)

(ref: 2015PASP..127..266M) Mangum, J. G., & Shirley, Y. L. 2015, PASP, 127, 266, doi: [`10.1086/680323`](http://doi.org/10.1086/680323)

(ref: 2011A&A...526A..47M) Maret, S., Hily-Blant, P., Pety, J., Bardeau, S., & Reynier, E. 2011, A&A, 526, A47, doi: [`10.1051/0004-6361/201015487`](http://doi.org/10.1051/0004-6361/201015487)

(ref: 2013MNRAS.434..488M) Marigo, P., Bressan, A., Nanni, A., Girardi, L., & Pumo, M. L. 2013, MNRAS, 434, 488, doi: [`10.1093/mnras/stt1034`](http://doi.org/10.1093/mnras/stt1034)

(ref: 2010AA...522A..62M) Martı́n, S., Aladro, R., Martı́n-Pintado, J., & Mauersberger, R. 2010, A&A, 522, A62, doi: [`10.1051/0004-6361/201014972`](http://doi.org/10.1051/0004-6361/201014972)

(ref: 2021AA...656A..46M) Martı́n, S., Mangum, J. G., Harada, N., et al. 2021, A&A, 656, A46, doi: [`10.1051/0004-6361/202141567`](http://doi.org/10.1051/0004-6361/202141567)

(ref: 2005A&A...434..691M) Matsuura, M., Zijlstra, A. A., van Loon, J. T., et al. 2005, A&A, 434, 691, doi: [`10.1051/0004-6361:20042305`](http://doi.org/10.1051/0004-6361:20042305)

(ref: 2006A&A...458..417M) Muller, S., Guélin, M., Dumke, M., Lucas, R., & Combes, F. 2006, A&A, 458, 417, doi: [`10.1051/0004-6361:20065187`](http://doi.org/10.1051/0004-6361:20065187)

(ref: 2023AA...674A.101M) Muller, S., Martı́-Vidal, I., Combes, F., et al. 2023, A&A, 674, A101, doi: [`10.1051/0004-6361/202245768`](http://doi.org/10.1051/0004-6361/202245768)

(ref: 2017ApJ...844...98M) Muraoka, K., Homma, A., Onishi, T., et al. 2017, ApJ, 844, 98, doi: [`10.3847/1538-4357/aa7a0b`](http://doi.org/10.3847/1538-4357/aa7a0b)

(ref: 2023MNRAS.522..559O) Ou, C., Wang, J., Zheng, S., et al. 2023, MNRAS, 522, 559, doi: [`10.1093/mnras/stad1004`](http://doi.org/10.1093/mnras/stad1004)

(ref: 2005sf2a.conf..721P) Pety, J. 2005, in SF2A-2005: Semaine de l’Astrophysique Francaise, ed. F. Casoli, T. Contini, J. M. Hameury, & L. Pagani, 721

(ref: 2012A&A...540A..56P) Pilkington, K., Few, C. G., Gibson, B. K., et al. 2012, A&A, 540, A56, doi: [`10.1051/0004-6361/201117466`](http://doi.org/10.1051/0004-6361/201117466)

(ref: 2022A&ARv..30....7R) Romano, D. 2022, A&ARv, 30, 7, doi: [`10.1007/s00159-022-00144-z`](http://doi.org/10.1007/s00159-022-00144-z)

(ref: 2003MNRAS.342..185R) Romano, D., & Matteucci, F. 2003, MNRAS, 342, 185, doi: [`10.1046/j.1365-8711.2003.06526.x`](http://doi.org/10.1046/j.1365-8711.2003.06526.x)

(ref: 2017MNRAS.470..401R) Romano, D., Matteucci, F., Zhang, Z. Y., Papadopoulos, P. P., & Ivison, R. J. 2017, MNRAS, 470, 401, doi: [`10.1093/mnras/stx1197`](http://doi.org/10.1093/mnras/stx1197)

(ref: 2024A&A...687A..26S) Saldaño, H. P., Rubio, M., Bolatto, A. D., et al. 2024, A&A, 687, A26, doi: [`10.1051/0004-6361/202348436`](http://doi.org/10.1051/0004-6361/202348436)

(ref: 2021A&A...646A.106S) Schootemeijer, A., Langer, N., Lennon, D., et al. 2021, A&A, 646, A106, doi: [`10.1051/0004-6361/202038789`](http://doi.org/10.1051/0004-6361/202038789)

(ref: 2014Natur.514..335S) Shi, Y., Armus, L., Helou, G., et al. 2014, Nature, 514, 335, doi: [`10.1038/nature13820`](http://doi.org/10.1038/nature13820)

(ref: 2006ApJ...645.1118S) Sloan, G. C., Kraemer, K. E., Matsuura, M., et al. 2006, ApJ, 645, 1118, doi: [`10.1086/504516`](http://doi.org/10.1086/504516)

(ref: 5725236) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science Engineering, 13, 22, doi: [`10.1109/MCSE.2011.37`](http://doi.org/10.1109/MCSE.2011.37)

(ref: 2009A&A...503..323V) Visser, R., van Dishoeck, E. F., & Black, J. H. 2009, A&A, 503, 323, doi: [`10.1051/0004-6361/200912129`](http://doi.org/10.1051/0004-6361/200912129)

(ref: 2009ApJ...690..580W) Wang, M., Chin, Y. N., Henkel, C., Whiteoak, J. B., & Cunningham, M. 2009, ApJ, 690, 580, doi: [`10.1088/0004-637X/690/1/580`](http://doi.org/10.1088/0004-637X/690/1/580)

(ref: 2004AA...422..883W) Wang, M., Henkel, C., Chin, Y. N., et al. 2004, A&A, 422, 883, doi: [`10.1051/0004-6361:20035722`](http://doi.org/10.1051/0004-6361:20035722)

(ref: 1997macl.book.....W) Westerlund, B. E. 1997, The Magellanic Clouds

(ref: 1994ARA&A..32..191W) Wilson, T. L., & Rood, R. 1994, ARA&A, 32, 191, doi: [`10.1146/annurev.aa.32.090194.001203`](http://doi.org/10.1146/annurev.aa.32.090194.001203)

(ref: 2008A&A...487..237W) Wouterloot, J. G. A., Henkel, C., Brand, J., & Davis, G. R. 2008, A&A, 487, 237, doi: [`10.1051/0004-6361:20078156`](http://doi.org/10.1051/0004-6361:20078156)

(ref: 2023AA...670A..98Y) Yan, Y. T., Henkel, C., Kobayashi, C., et al. 2023, A&A, 670, A98, doi: [`10.1051/0004-6361/202244584`](http://doi.org/10.1051/0004-6361/202244584)

(ref: 2017A&A...607A.126Y) Yan, Z., Jerabkova, T., & Kroupa, P. 2017, A&A, 607, A126, doi: [`10.1051/0004-6361/201730987`](http://doi.org/10.1051/0004-6361/201730987)

(ref: 2020A&A...637A..68Y) Yan, Z., Jerabkova, T., & Kroupa, P. 2020, A&A, 637, A68, doi: [`10.1051/0004-6361/202037567`](http://doi.org/10.1051/0004-6361/202037567)

(ref: 2020ApJS..249....6Z) Zhang, J. S., Liu, W., Yan, Y. T., et al. 2020, ApJS, 249, 6, doi: [`10.3847/1538-4365/ab9112`](http://doi.org/10.3847/1538-4365/ab9112)

(ref: 2018Natur.558..260Z) Zhang, Z.-Y., Romano, D., Ivison, R. J., Papadopoulos, P. P., & Matteucci, F. 2018, Nature, 558, 260, doi: [`10.1038/s41586-018-0196-x`](http://doi.org/10.1038/s41586-018-0196-x)

</paper>

Write the methods card for this paper.