# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...966..130R\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...966..130R",
 "title": "Investigating the Drivers of Electron Temperature Variations in H II Regions with Keck-KCWI and VLT-MUSE",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Rickards Vaught, Ryan J.",
 "n_authors": 15,
 "arxiv_id": "2309.17440",
 "doi": "10.3847/1538-4357/ad303c",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S",
  "2013.1.00803.S",
  "2013.1.01161.S",
  "2015.1.00121.S",
  "2015.1.00782.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2016.1.00386.S",
  "2017.1.00392.S",
  "2017.1.00766.S",
  "2017.1.00886.L",
  "2018.1.00484.S",
  "2018.1.01321.S",
  "2018.1.01651.S",
  "2018.A.00062.S",
  "2019.2.00129.S"
 ]
}
```

Paper text:
<paper>
# Investigating the Drivers of Electron Temperature Variations in HII Regions with Keck-KCWI and VLT-MUSE

## Abstract

H II region electron temperatures are a critical ingredient in metallicity determinations and recent observations reveal systematic variations in the temperatures measured using different ions. We present electron temperatures ($T_e$) measured using the optical auroral lines (\[N II\]$\lambda5756$, \[O II\]$\lambda\lambda7320,7330$, \[S II\]$\lambda\lambda4069,4076$, \[O III\]$\lambda4363$, and \[S III\]$\lambda6312$) for a sample of H II regions in seven nearby galaxies. We use observations from the Physics at High Angular resolution in Nearby Galaxies survey (PHANGS) obtained with integral field spectrographs on Keck (Keck Cosmic Web Imager; KCWI) and the Very Large Telescope (Multi-Unit Spectroscopic Explorer; MUSE). We compare the different $T_e$ measurements with H II region and interstellar medium environmental properties such as electron density, ionization parameter, molecular gas velocity dispersion, and stellar association/cluster mass and age obtained from PHANGS. We find that the temperatures from \[O II\] and \[S II\] are likely over-estimated due to the presence of electron density inhomogeneities in H II regions. We measure high \[O III\] temperatures in a subset of regions with high molecular gas velocity dispersion and low ionization parameter, which may be explained by the presence of low-velocity shocks. In agreement with previous studies, the $T_{\rm{e}}$–$T_{\rm{e}}$ between \[N II\] and \[S III\] temperatures have the lowest observed scatter and follow predictions from photoionization modeling, which suggests that these tracers reflect H II region temperatures across the various ionization zones better than \[O II\], \[S II\], and \[O III\].

# Introduction

The characterization of abundance variations within galaxies provides insight into the physical processes that drive galaxy and chemical evolution. A galaxy’s gas-phase metal abundance (i.e. metallicity) reflects the history of chemical enrichment from stars and the net balance of gas flows (mixing, outflows, inflows of pristine material, etc.). In addition, the metallicity of ISM gas directly controls its cooling and other important ISM physics (cite: Draine2011piim.book.....D; Piembert2017PASP..129h2001P).

The distribution of gas-phase metals in a galaxy is commonly traced by the abundance of oxygen, nitrogen, sulfur, and other metals using the emission from ionized gas located inside H II regions (cite: Kennicutt1996; Bresolin2012ApJ...750..122B; Hernandez2013ApJ...777...19H; Ho2017ApJ...846...39H; Kreckel2019ApJ...887...80K; Kreckel2020MNRAS.499..193K; vanloon2021MNRAS.tmp.1227V; Grasha:2022). There are several indirect methods calibrated using strong optical emission lines to derive an estimate of the H II region metallicity (cite: 2008ApJ...681.1183K; Blanc:2015). A “direct” measure of an H II region metallicity requires knowledge of the electron temperature ($T_{\rm{e}}$) of the gas. Due to their exponential dependence on $T_{\rm{e}}$, one of the ways to infer electron temperature is through the auroral-to-nebular line ratios of collisionally excited lines (cite: Peimbert1967ApJ...150..825P; Osterbrock:2006; Piembert2017PASP..129h2001P). Nebular and auroral lines originate from different excited states of ions. Auroral lines are from higher energy levels, but are still accessible for collisional excitation in a $T \sim 10^4$ K gas. If the density of the gas is below the auroral and nebular line critical densities (i.e. when collisional de-excitation is negligible), then the auroral-to-nebular line ratio is sensitive to the electron temperature (cite: Osterbrock:2006). Given that the excitations to the auroral level are only accessible to electrons of higher energy, auroral line emission can be $> 100$ times weaker than nebular lines (cite: Kennicutt2003ApJ...591..801K; Esteban2004MNRAS.355..229E; Berg2020ApJ...893...96B). One alternative way to measure $T_{\rm{e}}$ include the ratio between recombination line (RL) emission from H and other species (cite: Peimbert1967ApJ...150..825P; Osterbrock:2006; Piembert2017PASP..129h2001P). But, because RLs of ions exhibit a much weaker dependence to temperature (cite: Piembert2017PASP..129h2001P), the optical RLs useful for use as temperature diagnostics are typically reserved for deep high S/N spectra as RL emission is typically much fainter than the emission from auroral lines.

For ions with optical auroral lines studied in this work, we can measure the temperatures for each ion using the following line ratios:

$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ $\rightarrow$ \[O III\]$\lambda4363$/$\lambda\lambda4959 ,5007$,

$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ $\rightarrow$ \[O II\]$\lambda\lambda7320,7330$/$\lambda\lambda3726,3729$[^1],

$T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ $\rightarrow$ \[S III\]$\lambda6312$/$\lambda\lambda9069,9532$,

$T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ $\rightarrow$ \[S II\]$\lambda\lambda4069,4076$/$\lambda\lambda6716,6731$,

$T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ $\rightarrow$ \[N II\]$\lambda5756$/$\lambda\lambda6548,6584$.

The O$^{+}$, N$^+$, S$^+$ ions require energies of $13.6$ eV, $14.5$ eV, and $10.3$ eV to be produced while S$^{++}$ and O$^{++}$ require energies 23 eV and 35 eV, respectively.

Several effects play competing roles in determining the ionization and temperature structure of H II regions. These include a radially decreasing intensity and hardening of the radiation field (photons closest to 13.6 eV are absorbed first) as well as a change in the ions which dominate gas cooling, and therefore the cooling efficiency (cite: stasinska:1980; Garnett1992AJ). Because of the varying degree of ionization within an H II region, a model of three ionization zones—low-, intermediate- and high—is often used to describe them. Because each ionization zone could theoretically have different temperatures, this further stresses the importance of observing multiple auroral lines and developing temperature priorities for use in accurately determining abundances (cite: Berg2015ApJ...806...16B; Berg2020ApJ...893...96B; Rogers:chaos:2021).

Observing the full set of optical auroral lines in an H II region can be challenging. In addition to the large wavelength range needed, $\sim$ 3700–10000 Å, some auroral lines are weaker than others depending on the metallicity and temperature of the gas. Because of these challenges, it is very important to establish temperature relationships that allow us to infer the conditions of a certain ionization zone from the others. Photoionization modeling (cite: Garnett1992AJ; BOND) has been used to derive temperature relationships, but standard models consider only simple geometries and homogeneous physical and ionization conditions, that might not be suitable for more complex regions potentially affected by shocks, stellar feedback, or other mechanism that produce density or temperature inhomogeneities (cite: Peimbert1967ApJ...150..825P; Peimbert1991shocks; Binette2012_OIII_shocks; Berg2015ApJ...806...16B; Berg2020ApJ...893...96B; Arellano2020; Nicholls2020PASP..132c3001N; Delgado_Desire2023arXiv230513136M; Delgado2023arXiv230511578M).

In the presence of temperature fluctuations, the exponential dependence of CEL strengths on temperature will bias auroral-to-nebular temperatures towards higher values than the true average (cite: Peimbert1967ApJ...150..825P; Peimbert:1969). Such inhomogeneities may be related to the presence of turbulence, density structure, and shocks associated with either stellar winds or radiation–pressure driven expansion. If the sources of temperature inhomogeneities are confined to the central part of the nebula, the effects that these phenomena have on temperature may primarily affect only the high ionization zone. This has been suggested by (cite: Delgado2023arXiv230511578M) who presented evidence for temperature inhomogeneities affecting only the highly ionized gas traced by \[O III\]. In a sample of Galactic and extra-galactic H II regions, they observed that differences between \[O III\] and \[N II\] temperatures correlated with the degree of deviation from the average temperature measured using faint O II recombination line emission. Furthermore, a strong correlation between the O II recombination and \[N II\] temperatures observed by (cite: Delgado2023arXiv230511578M) implies that temperatures inferred from the \[N II\] auroral line accurately measures the average $T_\mathrm{e}$ of the low-ionization zone (cite: Delgado2023arXiv230511578M; Delgado_Desire2023arXiv230513136M).

Due to the importance of obtaining accurate temperatures for precise abundances, significant effort has been devoted to advancing our understanding of the temperatures of different H II region ionization zones. For example, previous works have found that the scatter between temperatures of different ionization zones may be correlated with other properties of the gas such as the ionization parameter and metallicity (cite: Berg2015ApJ...806...16B; Arellano2020; Berg2020ApJ...893...96B; Yates2020A&A...634A.107Y).

To explore these questions, we use deep 3600–9500 Å IFU mapping to measure the set of optical auroral lines and nebular lines for a sample of H II regions. We use observations obtained from the Keck Cosmic Web Imager (cite: 2018ApJ...864...93M) and Multi-Unit Spectroscopic Explorer (cite: MUSE_INST:2010) to measure the electron temperature from all 3 ionization zones in H II regions in nearby galaxies. In Section [2](#sec:Observations) we present our sample galaxies as well as primary and supplemental observations. In Section [3](#sec:reduction) we discuss the reduction of the KCWI data. We assess the quality of the KCWI mosaics in Section [\[sec:data_quality_assesment\]](#sec:data_quality_assesment). We construct our H II region sample in Section [4](#sec:hii_cat_intro). We present the auroral line measurements in Section [5](#sec:auroral_fit). We derive H II region properties from nebular diagnostics and from ALMA and HST data in Section [6](#sec:hii_region_property_derivations). The results and discussion are presented in Section [7](#sec:RESULTS) and [8](#sec:DISCUSSION).

# Observations

The analysis presented here makes joint use of multi-wavelength observations of seven galaxies obtained with Keck-KCWI, VLT-MUSE, Atacama Large Millimeter/submillimeter Array (ALMA), and the Hubble Space Telescope (HST).

## Sample Selection

The seven galaxies in this analysis are drawn from the PHANGS-MUSE sample (cite: EmsellemMuse). To date, 90 galaxies make up the full PHANGS sample[^2] (cite: 2021Leroy_sample), and 19 have been observed by MUSE. In order to be observed with KCWI in the northern hemisphere, we selected the seven target galaxies from a subset of PHANGS-MUSE galaxies with declination, $\delta> -30^{\circ}$. Table [\[tab:sample_properties\]](#tab:sample_properties) presents general properties of these galaxies, including distances, masses, sizes, and the angular resolution of the MUSE data.

## Keck Cosmic Web Imager

We observed each galaxy using KCWI on the Keck II telescope with multiple pointings taken over several nights between the years 2017 and 2021. Clear conditions were present for the majority of observations, except for the nights of October 16 and 17, 2018, which suffered from variable cloud coverage. These poor conditions primarily affect the observations of NGC 628. The instrument was configured with the “Large” slicer and BL grating centered at 4600 Å. The usable spectral range afforded by this configuration is 3650–5550 Å with a spectral resolution $R\sim 900$, corresponding to a full width at half maximum (FWHM) $\sim 5.1$ Å (or $\sim$ 300 km s$^{-1}$) at the central wavelength. The Large slicer has an angular slice width of 1.35$''$. The field of view (FoV) using the Large slicer and BL grating is 33$''$ perpendicular and 20.4$''$ parallel to the slicer.

Because the FoV is small compared with the large angular size of each galaxy, we observed each galaxy over multiple fields. Most fields were observed two times using 1200 s (i.e. 20 min) integration times. The only exceptions were: all fields in NGC 3627, which were observed five times each with 120 s (2 min) integration times; field 17 in NGC 628 which was observed 3 times using 1200 s; and field 2 in NGC 5068 and field 5 in NGC 1385, both having only a single observation of 1200 s. A half slice width, or 0.675$''$, dither was applied between each exposure. We observed an off-galaxy region, selected to be free of extended emission and/or bright sources, in order to measure a sky spectrum close in time to the observations. These sky frames, observed using an integration time of $600$ s (i.e. 10 min), were used for sky subtraction during data reduction. We summarize the number of fields, exposure times, and dates in Table [\[tab:obs\]](#tab:obs) of Appendix [10](#appn:observations). The full data reduction is outlined in Section [3](#sec:reduction).

## Multi-Unit Spectroscopic Explorer

MUSE observations of these galaxies come from the PHANGS-MUSE survey (cite: EmsellemMuse). MUSE covers wavelengths between 4800–9500 Å. Taken in combination, KCWI and MUSE span the full optical spectrum. The full details of the MUSE data reduction and data products are presented in (cite: EmsellemMuse), and we provide a brief overview here. The PHANGS-MUSE program observed 19 galaxies using 168 individual 1$'\times1'$ pointings. The median spatial resolution across all pointings is $\sim 50$ pc (or $\sim$ 0.80$''$) with a typical spectral FWHM of $\sim 2.5$ Å (but varying with wavelength). The data were reduced using the `pymusepipe`[^3] and spectral fitting and analysis was performed using the Data Analysis Pipeline [^4] packages described in (cite: EmsellemMuse). The individual MUSE pointings were homogenized to a uniform Gaussian point-spread-function (PSF) with FWHM set to the largest FWHM measured for each target, resulting in “convolved and optimized” (COPT) mosaics. The PSFs of the COPT mosaics are listed in Table [\[tab:sample_properties\]](#tab:sample_properties). We use the COPT mosaics in the following work.

## ALMA

Our analysis makes use of Atacama Large Millimeter/submillimeter Array (ALMA) data obtained as part of PHANGS–ALMA (cite: 2021Leroy_sample). PHANGS-ALMA observed the $J=2-1$ rotational transition of $^{12}$CO, hereafter CO, for $90$ galaxies. The details of the data reduction are described in (cite: 2021Leroy_data). We make use of the ALMA datacubes with combined CO measurements from the 12m and 7m arrays plus Total Power (12m+7m+TP). The nominal angular resolution of 12m+7m+TP observations is $\sim 1.3\ensuremath{''}$, similar to the resolution of both KCWI and MUSE. The velocity resolution is $2.5$ km s$^{-1}$.

## HST

The PHANGS-HST survey (cite: 2022PHANGS_HST) observed[^5] our target galaxies using 5 HST filters: F275W (NUV), F336W (U), F438W (B), F555W (V), F814W (I). Of the high-level data products produced from this dataset, we make use of compact star cluster catalogs (cite: ThilkerCompactClusters) and multi-scale stellar association catalogs (cite: Larson2023). The association catalog identifies sources using both the V and NUV filters and has been convolved to several physical resolutions (8, 16, 32 and 64 pc, respectively). Following (cite: Scheuermann2023MNRAS.522.2369S) we used the NUV selected, 32 pc catalogs.

ccccccc Name & 2cDistance$^{a}$ & 2clog$_{10}(M_{*})$ $^{b}$ & 2c$R_{25}$$^{c}$ & 2cPSF$_{\mathrm{MUSE}}$$^{d}$ & PSF$_{\mathrm{KCWI}}$$^{e}$\
& 2c\[Mpc\] & 2c\[$M_{\odot}$\] & 2c\[Arcmin\] & 2c\[Arcsec\] & \[Arcsec\]\
NGC 628 & 9.8$\pm$0.6 & 10.34$\pm$0.1 & 4.9 & 0.92 & 2.0 $\pm$ 0.4\
NGC 1087 & 15.9$\pm$2.2 & 9.93$\pm$0.1 & 1.5 & 0.92 & 1.2 $\pm$ 0.1\
NGC 1300 & 19.0$\pm$2.3 & 10.62$\pm$0.1 & 3.0 & 0.89\* & 1.3 $\pm$ 0.1\
NGC 1385 & 17.2$\pm$2.6 & 9.98$\pm$0.1 & 1.7 & 0.77\* & 1.3 $\pm$ 0.1\
NGC 2835 & 12.2$\pm$0.9 & 10.00$\pm$0.1 & 3.2 & 1.15 & 1.4 $\pm$ 0.1\
NGC 3627 & 11.3$\pm$0.5 & 10.83$\pm$0.1 & 5.1 & 1.05 & 1.1 $\pm$ 0.1\
NGC 5068 & 5.2$\pm$0.2 & 9.40$\pm$0.1 & 3.7 & 1.04 & 1.5 $\pm$ 0.4

Table notes: $^{a}$ From the compilation of (cite: Anand2021MNRAS.501.3621A) $^{b}$ Derived by (cite: 2021Leroy_sample), using GALEX UV and WISE IR photometry. $^{c}$ From LEDA (cite: Makarov2014). $^{d}$ The FWHM of the Gaussian PSF for the homogenized COPT mosaic from PHANGS-MUSE (cite: EmsellemMuse). $^{e}$ The average FWHM of the KCWI PSF for the set of a galaxy’s observed pointings. $^{*}$ Denotes galaxies observed with MUSE using ground based adaptive optics.

# KCWI Data Reduction

The KCWI observations were reduced using the Version 1.0.1 Python implementation of the KCWI Data Extraction and Reduction Pipeline (KDRP)[^6]. It was built using the Keck Data Reduction Pipeline Framework package[^7] and is a port of the initial IDL reduction pipeline[^8] (cite: 2018ApJ...864...93M). The pipeline performs basic CCD reduction including bias and over-scan subtraction, gain correction, cosmic ray removal, dark and scattered light subtraction as well as a flat field correction.

Following these basic reductions, the KDRP used the continuum bar and Thorium/Argon arc lamp images to generate geometric and wavelength solutions to convert each 2D science image into a spectral datacube. The accuracy of the wavelength solutions were similar across all the observation nights. The average RMS for the derived wavelength solutions was 0.1 Å.

We derived an inverse sensitivity curve to flux calibrate each datacube from standard star observations. The measured standard deviation between all of the derived inverse sensitivity curves was $\sim9\%$ at $\lambda=4600$Å. The maximum standard deviation within the wavelength range containing the lines used in this analysis is $\sim11\%$. Details of each standard star observation can be found in Table [\[tab:std_obs\]](#tab:std_obs) of Appendix [10](#appn:observations). After flux calibration, each datacube was corrected for differential atmospheric refraction.

Because the instrument FoV is much smaller than each galaxy, our images contained no sky pixels. To perform sky subtraction, we observed dedicated sky positions interspersed between science observations. We assigned the sky frame closest in time to each science observation to be used for sky subtraction according to the instructions in the KDRP documentation[^9]. The KDRP then performed sky subtraction using our preferred frames. The sky in all pixels was averaged together and scaled by the ratio of science-to-sky exposure time to estimate the sky observed in the “on” position. The final data products output by the pipeline include flux calibrated science and $1\sigma$ uncertainty cubes, as well as a bad-pixel mask cube.

## Image Re-Projection

Next we constructed mosaics from the individual KCWI pointing datacubes. The steps involved included image registration, matching the flux calibration to MUSE, and image co-addition. We also compared the absolute flux calibration of the final KCWI mosaics to MUSE and SDSS

The datacubes output by the KDRP have rectangular pixels with pixel-scale 1.35$''$ $\times$ 0.29$''$. We reprojected the cubes onto a square pixel grid using the astronomical mosaic software `Montage`[^10]. Prior to running `Montage`, we converted the KCWI data to surface brightness units (erg s$^{-1}$ cm$^{-2}$ Å$^{-1}$ sr$^{-1}$) by dividing the flux per pixel by the pixel solid angle in steradians. The reprojected images have a final square pixel grid with a uniform pixel-scale of 0.29$''$ $\times$ 0.29$''$. We validated the flux-conservation in our data before and after reprojection.

## Image Registration

To co-add each galaxy’s set of cubes into a spectral mosaic, we placed each cube onto a common world coordinate system (WCS). It is typical to perform image registration by matching the location of foreground stars or background galaxies to known positions found in catalogs. However, in our case most individual fields did not contain a sufficient number of bright point sources. Instead, we performed image registration by maximizing the cross-correlation between individual KCWI fields and overlapping MUSE data in order to match the KCWI pointing astrometry to MUSE. The astrometry of the MUSE galaxy mosaics were validated against wide-field broadband imaging and stellar positions from the Gaia DR1 as described in (cite: EmsellemMuse). The MUSE astrometry, when compared to broadband imaging, exhibited better than 100 milli-arcseconds RMS. in both R.A. and Dec.

To cross-correlate KCWI and MUSE, we created synthetic photometry ($P_S$) images from spectral regions where the wavelength coverage of KCWI and MUSE overlap. Because there is some saturation in H$\beta$ and \[O III\] at the brightest locations in the KCWI data, we masked out those lines in both cubes to avoid any issues with the comparison between the two data cubes.

In order to determine the optimal astrometric shifts to apply to each KCWI science frame, we utilized a two-step grid search operation, first shifting in 1 pixel (or 0.29$''$) steps $\pm$ 17 pixels (or $5\ensuremath{''}$) from the center of the KCWI pointing in order to find the optimal R.A. and Dec. offsets which maximize the correlation of the KCWI and corresponding MUSE $P_S$ images. After locating 1st-pass shifts, we performed a secondary grid search using finer 1/2 pixel increments over a smaller range ($\pm 1\ensuremath{''}$ from the image center). The 0.5 pixel sampling corresponds to 0.145$''$  which is less than the MUSE pixel scale of 0.20$''$ but also corresponds to 1/10 the typical KCWI FWHM which is equal to 1.2$''$. Across the galaxy sample, the final offsets correspond to correlation coefficients $>$ 0.9 between KCWI and MUSE.

## Matching the MUSE Flux Calibration

In order to correct for any additive and/or multiplicative offsets between the MUSE and KCWI flux calibrations, we compared the surface brightness (SB) calculated in apertures in overlapping position and wavelength. To do this we made use of the $P_S$ images, described in Section [3.2](#sec:registration), and measured the surface brightness inside a number of 3$''$ radius apertures located at randomly drawn positions inside the combined KCWI and MUSE coverage. The aperture size was chosen to be large enough to minimize effects arising from the different PSFs of KCWI and MUSE. We determined the best-fit line to the measured $SB_{\mathrm{KCWI}}$ vs. $SB_{\mathrm{MUSE}}$ relationship, where the slope, $m$, and $y$-intercept, $b$, reflect the multiplicative and additive offset between the KCWI and MUSE flux calibration. We applied the correction by multiplying the KCWI datacubes by $m$ and adding $b$ to the full spectrum in each pixel. The average multiplicative and additive offsets were $m=1.03\pm0.02$ and $b=-7.6\pm1.7 \times 10^{-20}\ \mathrm{erg}\ \mathrm{s}^{-1}\ \mathrm{cm}^{-2}\ \text{\AA}^{-1}$. This $\sim 3\%$ deviation from a 1–1 slope and low level of additive offset show that the calibrations were already in good agreement.

## PSF of Individual KCWI Fields

Because the MUSE mosaics have been homogenized to a uniform Gaussian PSF, we have an image with a known (parameterized) PSF. This is advantageous, as we can directly measure the KCWI PSF per pointing using cross-convolution, following the steps outlined in (cite: EmsellemMuse). We briefly summarize the procedure here. 1) We produced $P_S$ images of both the MUSE mosaic and the individual KCWI pointings. 2) We re-projected the MUSE cutout onto the KCWI 0.29$''$ $\times$ 0.29$''$ pixel grid. 3) We convolved the KCWI pointing with a 2D Gaussian Kernel with PSF equal to the reference MUSE PSF. 4) In an iterative manner, the reference MUSE image is then convolved with a 2D Gaussian Kernel, PSF$_k$, where the PSF$_k$ represents the KCWI pointing PSF which is a free-parameter. We then varied the FWHM of this kernel until we maximized the correlation between the KCWI pointing and the reference MUSE image. For the set of images observed for each galaxy, we present the average and standard deviation of the measured PSFs in Table [\[tab:sample_properties\]](#tab:sample_properties). The average PSF across the galaxy sample is $1.4'' \pm 0.2''$ which is consistent with the PSFs measured using the Standard Star observations presented in Appendix [10](#appn:observations). We chose not to homogenize the PSF of the KCWI data. To do so, would mean convolving the KCWI data to the largest observed PSF. In turn, this would increase the mismatch in resolution between KCWI and MUSE as well as lead to larger H II region boundaries. The larger regions have higher susceptibility of contamination from the diffuse ionized gas.

## Image Co-Addition

After the KCWI datacubes had been aligned and flux calibrated to match the MUSE mosaics, the KCWI datacubes were co-added to create KCWI galaxy mosaics. The image co-addition was performed with `Montage`. The `mAddCube` call to `Montage` initiates the co-addition. The co-addition is performed by stacking the aligned images, according to the an output WCS determined by `Montage`, and then taking the average value between any overlapping pixels. Pseudo $g$-band images for the final mosaics of each galaxy are shown in Figure [1](#fig:gband_sample).

![](gband_tiles.pdf)

## Absolute Calibration of KCWI Compared to MUSE

We assessed the absolute calibration of the co-added KCWI mosaics by comparing the SB’s between the KCWI and MUSE mosaics. Comparisons of the MUSE mosaics with SDSS imaging in the $r$-band described in (cite: EmsellemMuse) showed that the MUSE absolute flux calibration is consistent with SDSS calibration within the instrument uncertainty of $0.06$ mag (cite: SDSS_mag_unc). We calculated the SB inside $r=3\ensuremath{''}$ apertures, randomly placed in the KCWI coverage. The SB offsets between the KCWI and MUSE mosaics are shown in Figure [2](#fig:muse_comparisons). The resulting offsets, summarized in Table [\[tab:sdss_kcwi\]](#tab:sdss_kcwi), reveal acceptable agreement between the MUSE and KCWI absolute calibration. The average percent SB offset with respect to the SDSS imaging, $\Delta \mathrm{SB}/\mathrm{SB}_{\mathrm{SDSS}}$, is between $-1.1$% and $0.7$% with a median value across all galaxies of $-0.1$% $\pm$ 4%.

![](muse_tiles.pdf)

![](sdss_tiles.pdf)

## Absolute Calibration of KCWI Compared to SDSS

We have shown agreement between KCWI and MUSE, but this comparison is only an assessment of the flux calibration in the overlapping wavelength range of KCWI and MUSE. To assess the absolute flux calibration across a wider wavelength range, we compared synthetic *g*-band images of the KCWI mosaics to Sloan Digital Sky Survey (cite: SDSS2003AJ....126.2081A) images of the same galaxies. Only four galaxies with KCWI mosaics have SDSS imaging: NGC  628, NGC 1087, NGC 3627 and NGC 5068. We constructed synthetic *g*-band images of these galaxies by convolving the spectrum in each pixel, $F_{\lambda}(x,y)$, with the $g$-band transmission curve, $T_{g}(\lambda)$, according to the following equation: $$\begin{equation}
    F_{g}(x,y)=\frac{\int F_{\lambda}(x,y)T_{g}(\lambda)d\lambda}{\int T_{g}(\lambda)d\lambda}.
\end{equation}$$ The SDSS imaging is presented in units of *nanomaggies* or $f_{\nu} =$ 3.631$\times 10^{-6}$ Jy. To compare with the KCWI data, with native units of flux density, $f_{\lambda}$, we converted to flux density with the following expression (cite: 2005PASP..117..421T), $$\begin{equation}
f_{\lambda}=\frac{c}{\lambda_{p}^2} f_{\nu},  
\end{equation}$$ where $\lambda_{p}$ is the pivot wavelength of the band-pass. The pivot wavelength for the *g*-band filter is $\lambda_{p}=4702$ Å. The surface brightness for both KCWI and SDSS are measured inside $3\ensuremath{''}$ radius apertures. The mean and 1$\sigma$ scatter of the measured surface brightness are shown in Figure [3](#fig:sdss_comparisons). We found overall agreement of the absolute calibration between KCWI and SDSS for the four galaxies. Summarized in Table [\[tab:sdss_kcwi\]](#tab:sdss_kcwi), the median offset across the sample galaxies, $\Delta \mathrm{SB}/\mathrm{SB}_{\mathrm{SDSS}}$ range between $-$1.0% and 3.0% and exhibits scatter between 3% and 10%. The source of the largest scatter is from the northern most observation of NGC 628. In spite of the quality of this KCWI field, we find that this field contains a single HII region and, as shown in Figure [27](#fig:hii_masks_0628) of Appendix [12](#appn:comparison_of_muse_and_kcwi_hii_regions), contains detectable auroral and nebular emission from ions only within the MUSE spectrum. Because of this, including this KCWI field will have no negative impact on the overall analysis. The median SB offset across all galaxies is $1 \pm 7$% which suggests that the KCWI calibration is in good agreement with SDSS.

ccccc Name & 2c$\mu(\Delta$SB)$^{a}$ & 2c$\sigma(\Delta$SB)$^{b}$ & 2c$\mu(\Delta$SB$_g$)$^{c}$ & 2c$\sigma(\Delta$SB$_g$)$^{d}$\
& 2c\[%\] & 2c\[%\]& 2c\[%\]& 2c\[%\]\
NGC 628 & 0.3 & 6.0 & 0.3 & 10.0 $^{f}$\
NGC 1087 & 0.5 & 3.6 & -1.0 & 3.4\
NGC 1300 & 1.5 & 4.0 & - & -\
NGC 1385 & -0.6 & 4.3 & - & -\
NGC 2835 & -0.4 & 3.6 & - & -\
NGC 3627 & 1.7 & 1.6 & -0.05 & 2.6\
NGC 5068 & 0.3 & 6.7 & 2.9 & 8.4

Table notes: $^{a}$ The median fractional surface brightness offset between KCWI and MUSE in %. $^{b}$ The standard deviation of the fractional surface brightness offset between KCWI and MUSE in %. $^{c}$ The median $g$-band surface brightness offset between KCWI and SDSS. $^{d}$ The standard deviation of $g$-band surface brightness offset between KCWI and SDSS. $^{f}$ Removing the problematic field, discussed in Section 3.7, reduces this standard deviation to 7% which is comparable to the other galaxies.

# H II Region Catalog

In order to assess the emission line properties of H II regions, we determine the H II region location and boundaries using H$\beta$ maps constructed from the KCWI spectral datacubes and the image segmentation software `HIIphot` (cite: Thilker2000AJ....120.3070T). Although H II region masks have previously been constructed from the MUSE H$\alpha$ maps for these galaxies (cite: Kreckel2019ApJ...887...80K; Santoro2022A&A...658A.188S; Groves2023NebCat; Congiu:2023), the MUSE angular resolution is higher than that of KCWI. Because of this, the H II region boundaries derived from MUSE may not fully encapsulate the spatial extent of the H II regions observed using KCWI. Furthermore, simply convolving or reprojecting the MUSE H II masks to the KCWI resolution or grid would introduce uncertainty on the boundaries for tightly spaced H II regions. We therefore perform H II region identification directly on the KCWI data.

## Construction of H$\beta$ Maps

H$\beta$ is the brightest H I recombination line observed by KCWI, and maps of this emission for the galaxies will be used to define our H II regions. The continuum near and underlying H$\beta$ emission must be removed in order to accurately map its emission. To remove the continuum we used `LZIFU`, an emission line fitting code designed specifically for use with IFUs (cite: Ho2016). `LZIFU` implements and streamlines the penalized pixel-fitting software (cite: Cappellari2004; Cappellari2017MNRAS.466..798C) for using `PPXF` on IFU emission line maps. To fit the continuum of the input spectrum `LZIFU` matches a series of input single-metallicity, $-1.31<$ \[Z/H\] $< 0.22$, stellar population models (cite: LZIFUMiles) that have been redshifted, and convolved to match the input spectrum PSF. `LZIFU` fits Gaussian models at the location of emission lines. In the output H$\beta$ map, pixels with weak or no H$\beta$ can contain ‘NaN’ values which can be problematic for `HIIphot`. To avoid these artifacts, we subtract the stellar continuum from each pixel’s spectrum and construct the final H$\beta$ maps by integrating the continuum-subtracted spectra between 4856–4876 Å. The final maps are suitable for H II region identification using `HIIphot`.

## H II Region Identification

`HIIphot` was designed to identify H II regions and complexes (unresolved or blended H II regions) while also minimizing the inclusion of surrounding diffuse ionized gas (or DIG). `HIIphot` works by first defining “seeds” at the location of peak emission in H$\beta$ (or H$\alpha$), then iteratively grows each “seed” and terminates only when the gradient of the H$\beta$ (or H$\alpha$) surface brightness distribution matches a termination value, in mandatory units of emission measure (EM), set by the user. The gradient of the surface brightness distribution is a more robust method of stopping uncontrolled growth at lower S/N compared to using only the average local background level. For each galaxy we apply the the same termination gradient, $\Delta=$ 5 EM pc$^{-1}$ or 2.43 $\times\ \rm{erg}\ \rm{s}^{-1}\ \rm{arcsec}^{-2}\ \rm{pc}^{-1}$, as the recent PHANGS-MUSE work by (cite: Santoro2022A&A...658A.188S).

`HIIphot` uses the PSF to convolve the input H$\beta$ map to different spatial scales to identify seeds. Using a constant PSF for all galaxies can potentially miss valid regions or generate non-physical regions. The PSF of the input H$\beta$ emission map is required by `HIIphot`. For each galaxy mosaic, we used the average PSF from the its KCWI pointings (see Table [\[tab:obs\]](#tab:obs) in Appendix [10](#appn:observations)) as the input for `HIIphot`. The resulting 2D mask returned by `HIIphot` contains H II regions with smooth and reasonable boundaries, judged by the distinction between clearly separated HII regions, the minimization of spurious small and pixelated regions or runaway growth. In total, `HIIphot` identifies $\sim$ 688 H II regions or complexes across all of the KCWI mosaics. This number is smaller than the 2169 potential H II regions identified for the Nebular catalog (cite: Kreckel2019ApJ...887...80K; Santoro2022A&A...658A.188S; Groves2023NebCat), and 2124 potential H II regions from (cite: Congiu:2023), inside the same KCWI footprints. This is largely due to the differences in angular resolution between KCWI and MUSE, and the three-fold decrease in strength of H$\beta$ emission relative to H$\alpha$. In Figure [20](#fig:lum) of Appendix [12](#appn:comparison_of_muse_and_kcwi_hii_regions) we show histograms of the H$\beta$ luminosity and radii for KCWI and Nebular catalog regions as well a comparisons of the spatial masks in Figures [21](#fig:hii_masks_1087)–[27](#fig:hii_masks_0628) of Appendix [12](#appn:comparison_of_muse_and_kcwi_hii_regions). Additionally, we also present in Table [\[tab:total_regions\]](#tab:total_regions) of Appendix [12](#appn:comparison_of_muse_and_kcwi_hii_regions) the number of regions detected per galaxy.

![](ngc1087_hii_regions_plot.pdf)

## Generation of Integrated H II Region Spectra

The KCWI H II region masks, produced by `HIIphot`, are used to isolate and sum the spectra in pixels belonging to each H II region, resulting in an integrated H II region spectrum. To produce a matching MUSE H II region mask we transformed the H II regions coordinates/boundaries from the KCWI pixel grid onto the MUSE pixel grid. These are then used to construct MUSE integrated spectra for each H II region. The KCWI and MUSE H II region spectra for a single H II region, with the full set of auroral lines highlighted, is shown in Figure [5](#fig:spectrum).

![](muse_kcwi_hii_region_auroral_lines.png)

We also produce integrated variance spectra for each H II region. The variance spectra for both KCWI and MUSE H II regions are constructed by propagating the pipeline-produced variance datacubes for pixels contained within each H II region boundary. In the case of MUSE, the datacubes have undergone an additional convolution process in order to generate mosaics with uniform PSF which introduces a correlation between neighboring pixels (cite: EmsellemMuse). Because of the additional convolution, we generated the MUSE variance spectra, assuming fully correlated conditions, by adding the pixel variance spectra linearly (cite: Taylor1997ieas.book.....T).

We verify this choice by comparing the median standard deviation of the propagated MUSE variance spectra, $\sigma_{\mathrm{propagated}}$, to the median standard deviation of the H II region spectrum, $\sigma_{\mathrm{measured}}$, in the emission line free wavelength range $5400-5450$ Å. We measured an average ratio between the propagated and measured error of $\sigma_{\mathrm{measured}}/\sigma_{\mathrm{propagated}}=$ $1.1 \pm 0.2$, implying that we are appropriately propagating the error. We also perform a similar comparison for KCWI, and find agreement, $\sigma_{\mathrm{measured}}/\sigma_{\mathrm{propagated}}=1.9\pm0.5$, between the measured and propagated error using uncorrelated pixel error propagation. To generate the appropriate variance we propagated the error using uncorrelated, for KCWI, and fully correlated error, for MUSE, propagation methods.

## H II Region Stellar and Emission Line Fitting

We modeled the stellar continuum and emission lines of the integrated H II region spectra using the general `PPXF` toolkit. Although the `LZIFU` implementation of `PPXF` allowed for the streamlined, full datacube, fitting of the KCWI H$\beta$ emission line map, the general `PPXF` toolkit offers more flexibility in the input fitting parameters. For example, we can input a wavelength dependent LSF function as well as fix the kinematics between emission lines of doublets and lines with similar levels of ionization. We followed (cite: EmsellemMuse) and fit the emission lines simultaneously with the stellar continuum. This particular fitting recipe was chosen to mirror the philosophy of the Mapping Nearby Galaxies at APO Data Analysis Pipeline (cite: MangaDAP2016AJ....152...83L; EmsellemMuse) and is suggested to mitigate the biases on emission line fluxes introduced from the masking of stellar absorption features around affected lines (cite: Sarzi2006_efit; Oh2011_efit; Belfiore2019_efit). `PPXF` robustly fits the stellar continuum by matching a set of templates to the observed H II region spectrum. The templates originate from the E-MILES library of simple stellar population (SSP) models (cite: Vazdekis2016MNRAS.463.3409V). The SSP ages were between $0.15-13.5$ Gyr. Each age bin contained SSPs with the following metallicities, $\mathrm{[Z/H]}=[-1.49, -0.96, -0.35, 0.06, 0.26, 0.4]$. Typically, `PPXF` convolves the SSP templates with a Gaussian model accounting for the spectral resolution of the input spectrum and the stellar velocity dispersion. However, because the KCWI line profile deviates significantly from a Gaussian (see Appendix [11](#sec:lsf)) we convolved the `PPXF` templates with a 4-moment Gauss-Hermite function while fitting KCWI emission lines. We constrained the fits of $h_4$ and $h_3$ in the Gauss-Hermite functions to values listed in Appendix [11](#sec:lsf). We performed the `PPXF` fitting of the KCWI H II region spectra independently from the MUSE H II region spectra. The fractional difference between the H II region H$\beta$ flux for KCWI and MUSE is $-2.3\pm7.5\%$.

We obtained errors on the emission line fluxes from the output of `PPXF`. The output errors are considered reliable if the `PPXF` derived reduced $\chi^2 \approx 1$. Together the resulting fits for both the KCWI and MUSE have an average reduced $\chi_{\mathrm{reduced}}^2 \approx 2.0$, indicative that the input variance spectra are under-estimated. We obtained a better estimate of the errors by re-scaling the returned errors, for each fit to KCWI and MUSE spectra, by a factor of $\sqrt{\chi_{\mathrm{reduced}}^2}$ (cite: Cappellari2004; Cappellari2017MNRAS.466..798C; EmsellemMuse).

## Dust Correction

We derive the V-band extinction ($A_V$) for each H II region using the Balmer decrement. To evaluate this decrement while also taking into account the errors on the measured H$\alpha$ and H$\beta$ emission, we construct a distribution of the MUSE H$\alpha$/H$\beta$ ratios by sampling the error for each line. Next, using `PyNeb`, we calculate the extinction by comparing the average of the H$\alpha$/H$\beta$ distribution to the theoretical value assuming the Case B recombination conditions $n_e=$10$^3$ cm$^{-3}$ and $T_e=10^4$ K (cite: Storey:1995). We explore how changing the assumed $T_e$ could affect the derived $A_V$ by sampling a range of temperatures between 5000 K and 1.5$\times10^4$ K and find that the standard deviation of $A_V$ for a fixed Balmer decrement is $\sim 0.06$ mag. We apply the wavelength dependent extinction correction assuming a (cite: ExtinctionCorr1994ApJ...422..158O) extinction curve. We present a histogram of the derived E($B$-$V$) in Figure [6](#fig:ebv_hist). The average E($B$-$V$) for the regions is $0.30$ mag and corresponds to an $A_V\sim0.9$ mag. We find a negligible difference when using KCWI H$\beta$ in place of the MUSE H$\beta$ flux. We add that a recent investigation shows that correcting, or not correcting, the Balmer lines for DIG contamination can impact the measured E($B$-$V$) (cite: Congiu:2023). For the range of E($B$-$V$) observed, a DIG-corrected E($B$-$V$) may return values of $A_V$ 0.05–0.1 mag lower than presented here. We discuss the effects that under/over-estimated extinction may have on the measured electron temperature in Section [7.1.1](#res:low_ionization_zone_te_te). Furthermore, given the good agreement between the integrated KCWI and MUSE H II region fluxes, we replace any saturated integrated H II region KCWI H$\beta$ and \[O III\] fluxes with those measured from their integrated MUSE spectrum.

![](eb_v_hist.pdf)

## Diffuse Ionized Gas

Emission from Balmer transitions, \[S II\]$\lambda\lambda6716,6731$, \[N II\]$\lambda6584$, and other lines originating from DIG surrounding the H II regions can contaminate the H II region emission line fluxes of the same transitions. Measuring the DIG contribution to H II region line flux is only beginning to being explored by IFU studies (cite: Belfiore2022_DIG; Congiu:2023). In order to remove regions with a large degree of DIG contamination we calculate the contrast between H II/DIG emission following the scheme outlined in (cite: KreckelChargeExchange). First, we mask each H II region in the MUSE emission line maps for: H$\alpha$, H$\beta$, \[S II\], \[N II\] and \[O I\]. For each emission line, we place a $10\ensuremath{''} \times 10\ensuremath{''}$ aperture around each H II region and measure the median DIG flux in pixels with $\rm{S/N} > 3$ and H$\alpha$ surface brightness $\rm{Log}_{10}(SB_{\rm{H}\alpha}/[\mathrm{erg}\ \mathrm{s}^{-1}\ \mathrm{kpc}^{-2}]) < 38$ (cite: Belfiore2022_DIG). Finally, we calculate the “integrated" DIG emission by multiplying the median DIG flux by the H II region size. For each DIG emission line, we calculate the percent contrast between the measured H II region flux and DIG flux. If the contrast between the H II region flux and DIG flux of any low-ionization emission line is $< 50$%, we exclude it from the sample.

## Quality Assessment and Classification of Regions

The regions identified by `HIIphot` are potentially a mix of H II regions, planetary nebulae, supernova remnants or low S/N in critical emission lines. We perform a set of cuts to reject non-H II regions and/or low S/N spectra from the catalog of H II regions.

- We exclude any H II region whose centroid coordinates are within 2$''$ from the edge of the mosaic. This step removes 86 H II regions

- We require the strong lines used for temperature determinations: H$\beta$, H$\alpha$, \[O III\]$\lambda\lambda4959,5007$ \[O II\]$\lambda3727$, \[N II\]$\lambda\lambda6548,6584$, \[S III\]$\lambda9069$ and \[S II\]$\lambda\lambda6716,6731$ to be detected above a threshold of S/N $>5$ . This step cuts 72 H II regions from the sample.

- Using the lines of H$\beta$, H$\alpha$, \[O III\] and \[N II\] we construct a Baldwin-Phillips-Terlevich (cite: BPT1981PASP...93....5B) diagram. We require H II regions to be consistent with photoionization by massive stars. Therefore, we require them to fall below the empirical \[O III\]/H$\beta$ vs. \[N II\]/H$\alpha$ (cite: KauffmanBPT) and \[O III\]/H$\beta$ vs. \[S II\]/H$\alpha$ (cite: Kewley2001ApJS..132...37K) lines. The BPT diagram showing the location of each H II region is shown in Figure [7](#fig:my_bpt). Out of the sample, 11 H II regions are above the empirical and theoretical line cut-offs and are removed.

- We exclude H II regions that fail our DIG contrast check in Section [4.6](#sec:dig). This step removes 98 H II regions.

The constraints together remove 267 out of the 688 detected H II regions leaving 421 H II regions remaining for use in future analysis. For these 421 regions, comparison of line ratios in Figure [7](#fig:my_bpt) to model classifications in Figure 3 of (cite: Congiu:2023) suggest that this sample is consistent with their H II region classification. In order to compare the electron temperatures derived from the lines which are critical for $T_{\rm{e}}$–$T_{\rm{e}}$ comparisons we also exclude regions with less than 2 significant (i.e. S/N $>3$, see Section [5](#sec:auroral_fit)) detections in any auroral line. This cut excludes removes 161 regions, leaving a final sample of 260 H II regions. We report in Table [\[tab:total_regions\]](#tab:total_regions) of Appendix [12](#appn:comparison_of_muse_and_kcwi_hii_regions) the number of regions with at least 2 auroral lines for each galaxy.

![](all_galaxy_bpt_n2ha_s2ha.pdf)

# Measurement of Auroral Line Emission

In order to robustly measure the flux and uncertainty for the faint, temperature sensitive auroral lines from \[N II\]$\lambda5756$, \[O II\]$\lambda\lambda7320,7330$, \[S II\]$\lambda\lambda4069,4076$, \[O III\]$\lambda4363$, and \[S III\]$\lambda6312$ we implement a specific auroral line fitting scheme in place of `PPXF`. This is necessary because any under/over subtraction of the continuum at the location of the faint auroral lines can bias the measured auroral line flux.

The framework of the auroral line fit is as follows. We first subtract the stellar continuum spectrum fitted by `PPXF`. This results in an H II region spectrum that contains only emission lines and residuals from the continuum subtraction. Next, we measure the standard deviation of the residuals, $\sigma_{cont}$, in a region near the auroral line but also free of emission. We then perform a large number of fits to the auroral line with random noise added to each wavelength bin, drawn from a normal distribution with standard deviation $\sigma_{cont}$. In each trial, we fit a single Gaussian (or double depending on the auroral line) plus a linear offset to the spectrum. The linear term is needed to correct for any residual continuum present in the continuum-subtracted spectrum. After completing the $N$ trials, we calculate the average integrated line flux, $F_{avg}$, and the standard deviation of the measured fluxes, $\sigma_{avg}$. If S/N $>3$ we consider the auroral line detected. In Figure [28](#fig:auroral_line_fits) of Appendix [13](#appn:auroral_fits) we show the model fits and residuals for a region in NGC 5068.

Although this general process is performed for all the auroral lines, the auroral line from \[O III\] is subject to additional constraints because emission from the \[O III\]$\lambda 4363$ can be blended with \[Fe II\]$\lambda4360$. This has been observed in both stacked galaxy and individual H II region spectra (cite: Curti2017MNRAS.465.1384C; Berg2020ApJ...893...96B; Arellano2020). The strength of the \[Fe II\]$\lambda4360$ has been observed to increase with the metallicity of the gas (cite: Curti2017MNRAS.465.1384C), although continuum pumping fluorescence contributes strongly to its emissivity (cite: rodriguez1999). \[Fe II\]$\lambda4360$ and \[Fe II\]$\lambda4288$ arise from the same atomic upper level and their relative intensities are independent of the physical conditions of the gas and depend solely on the atomic transition probabilities. Since $I(\lambda4360)/I(\lambda4288)=0.73$ (cite: Mendoza:2023), if \[Fe II\]$\lambda4360$ is detected, \[Fe II\]$\lambda4288$ should be present too.

To remove blending of the \[O III\]$\lambda 4363$ line by \[Fe II\]$\lambda4360$, we use the fixed ratio, $I(\lambda4360)/I(\lambda4288)=0.73$, to estimate the degree of contamination by measuring the strength of the brighter \[Fe II\]$\lambda4288$ emission. For each region we first fit the \[Fe II\]$\lambda4288$ line using a single Gaussian plus a linear continuum model. The initial guesses for the line center and width are taken from the parameters of H$\gamma$ returned by the `PPXF` fits. In the case that the \[Fe II\]$\lambda4288$ is not detected above a S/N threshold of 3, we instead use the 3$\sigma$ upper limit. We next fit \[O III\]$\lambda 4363$ using a single Gaussian plus constant offset model. The initial guesses for the kinematics of \[O III\]$\lambda 4363$ are taken from the `PPXF` fit of \[O III\]$\lambda4958$. After adding random noise, we generate a model for the \[Fe II\]$\lambda$4360 using the best fit parameters and errors derived from the fit to \[Fe II\]$\lambda4288$, using the fixed $I(\lambda4360)/I(\lambda4288)$ ratio. After generating the \[Fe II\]$\lambda$4360 model, we subtract it from the trial spectrum and proceed to then fit for the emission line flux originating from \[O III\]$\lambda 4363$. We also note that by performing the above fitting scheme on each region, we may be introducing a bias in the form of a systematic reduction of the \[O III\]$\lambda$4363 flux. However, this bias would favor systematically lower $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$, but, shown in Section [7](#sec:RESULTS), we do not observe any behaviour with $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ that would indicate the presence of such a systematic.

We detect emission from \[Fe II\]$\lambda4288$ in 30 H II regions, two of these are in regions with measurable \[O III\]$\lambda 4363$. The low number of \[Fe II\]$\lambda4288$ detections suggest that the combination of high-metallicity, needed for the presence of iron lines, and the exponential dampening of \[O III\]$\lambda 4363$ makes the contamination of \[O III\]$\lambda 4363$ by \[Fe II\]$\lambda4360$ a rare occurrence in spiral galaxies. From the non-detections, we determined that the 3$\sigma$ upper-limit on the \[Fe II\]$\lambda4360$ flux is 3.5 $\times 10^{-17} \rm{erg}\ \rm{s}^{-1}\ \rm{cm}^{-2}\ \rm{pc}^{-1}$ which is $\sim 20\%$ of the average \[O III\]$\lambda 4363$ flux. We show in Figure [29](#fig:auroral_line_fits_lowsn) Appendix [13](#appn:auroral_fits) an example \[O III\]$\lambda 4363$ fit which has had significant \[Fe II\]$\lambda4360$ contribution removed.

# H II Region Nebular, Environmental, and Stellar Properties

We assess the ionized gas physical conditions—$n_{\rm{e}}$, $T_e$, and ionization parameter $U$—of each H II region using a subset of the dust-corrected emission line fluxes. We also measure a number of characteristics of the H II region’s environment and local stellar population, as described below.

## Electron Density

Using `PyNeb` we calculate the electron density $n_{\rm{e}}$ for each H II region using the \[S II\]$\lambda\lambda 6716, 6731$ doublet. Based on our constraints discussed in Section [4.7](#sec:hiiconstraints), each H II region is guaranteed to have measured emission from this doublet at S/N $>5$. The \[O II\]$\lambda\lambda 3726,3729$ doublet is also commonly used to estimate $n_{\rm{e}}$. The atomic levels responsible for \[S II\]$\lambda\lambda6716,6731$ and \[O II\]$\lambda\lambda3726,3729$ both have critical densities, when collisional and radiative de-excitation are occurring at equal rates, that are of order $10^3$ cm$^{-3}$. The critical densities, as well as other references for the atomic data used, are listed in Table [\[tab:atomic_references\]](#tab:atomic_references). Both the \[S II\]$\lambda\lambda6716,6731$ and \[O II\]$\lambda\lambda3726,3729$ doublets are sensitive to densities $10^{2}\ \mathrm{cm}^{-3} < n_{\rm{e}} < 10^{3.5}\ \mathrm{cm}^{-3}$. However, in the KCWI measurements, the \[O II\]$\lambda\lambda3726,3729$ doublet is unresolved, and therefore we do not use it to measure $n_{\rm{e}}$. With the exception of a handful of regions, the measured electron densities are in the low-density limit, $n_{\rm{e}}\ <\ 100$ $\mathrm{cm}^{-3}$.

|  |  |  |  |
|:--:|:--:|:--:|:--:|
| Ion | Transition Probabilities | Collision Strengths | $n_{\mathrm{crit,nebular}}$ |
|  |  |  | ($10^3$ cm$^{-3}$) |
| $[$O II$]$ | (cite: Zeippen1982) | (cite: Kisielius2009) | 2$^{a}$ |
| $[$O III$]$ | (cite: Froese2004) | (cite: StoreyOIIIColl) | 691 |
| $[$N II$]$ | (cite: Froese2004) | (cite: Tayal2011) | 88 |
| $[$S II$]$ | (cite: RGJ19) | (cite: TayalSIIIColl) | 3$^{b}$ |
| $[$S III$]$ | (cite: FFCRecomData) | (cite: Tayal1999ApJ) | 543$^{c}$ |

: Transitions Probabilities, Collision Strengths, and Critical Densities for the relevant emission lines used in the PyNeb Temperature Determinations.

Table notes: $^{a}$ Average critical density for \[O II\]$\lambda\lambda3726,3729$ . $^{b}$ Average critical density for \[S II\]$\lambda\lambda6716,6731$ . $^{c}$ Average critical density for \[S III\]$\lambda\lambda9069,9532$ .

## H II Region Electron Temperatures

The auroral lines allow the determination of the electron temperatures for the O$^+$, O$^{2+}$, N$^+$, S$^+$ and S$^{2+}$ ions, or $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$, $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$, and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$, respectively. The temperatures are calculated via `PyNeb` using the collision strengths and transition probabilities, listed in Table [\[tab:atomic_references\]](#tab:atomic_references), as well the measured upper-limits of the electron density, $n_{\rm{e}}$, to convert an auroral-to-nebular ratio to temperature. The critical densities of the requisite lines, see Table [\[tab:atomic_references\]](#tab:atomic_references), used to estimate $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$, $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ are high enough such that the auroral-to-nebular lines ratios are insensitive to choice of $n_{\rm{e}} < 10^{4}$ $\mathrm{cm}^{-3}$. The density sensitivity in the lines used for $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ begins at smaller densities $n_{\rm{e}} \approx 10^{3}$ $\mathrm{cm}^{-3}$ and is further discussed in Section [7.3](#res:differences). The uncertainty for each temperature measurement is the standard deviation of the distribution of temperatures constructed by Monte Carlo sampling of the error for each auroral and nebular line included in the temperature determination. We summarize the number of detections and median temperature for each ion in Table [\[tab:temp_statistics\]](#tab:temp_statistics).

|  |  |  |
|:--:|:--:|:--:|
| T$_{\mathrm{e,Ion}}$ | Median$^{a}$ | $N_{\mathrm{regions}}$$^{b}$ |
|  | \[10$^4$ K\] |  |
| $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ | 0.95$^{+0.22}_{-0.12}$ | 156 |
| $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ | 0.81$^{+0.12}_{-0.09}$ | 245 |
| $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ | 0.94$^{+0.19}_{-0.14}$ | 305 |
| $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ | 0.89$^{+0.30}_{-0.10}$ | 143 |
| $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ | 1.20$^{+0.35}_{-0.16}$ | 26 |

Table notes: $^{a}$ The 50th $\pm$ the 16th – 84th percentile of the measured temperatures. $^{b}$ Number of H II regions with temperature measured from the particular ion.

## H II Region Ionization Parameters

The ionization parameter is an indicator of the strength of the ionizing radiation field. The Strömgren sphere descriptions of H II regions define the ionization parameter as $U=Q_0/(4\pi R^2 n_\mathrm{H} c)$, where $Q_0$ is the emission rate of photons capable of ionizing hydrogen (i.e. with energy $> 13.6$ eV), $R$ is the radius of the ionized region, $n_\mathrm{H}$ and $c$ are the hydrogen density and speed of light. However, calculating the ionization parameter using this definition is difficult (cite: Kreckel2019ApJ...887...80K; KreckelChargeExchange) as resolved studies show that H II regions exhibit a range of non-spherical morphologies and non-uniform densities (cite: Wood_hii_region_morph1989ApJS...69..831W).

Instead, we trace the ionization parameter using both the \[S III\]/\[S II\] and \[O III\]/\[O II\] emission line ratios. Photoionization modeling has shown that both the \[S III\]$\lambda\lambda9069,9532$/\[S II\]$\lambda\lambda6716,6731$ and \[O III\]$\lambda\lambda4959,5007$/\[O II\]$\lambda\lambda3626,3729$ correlate with the ionization parameter, $U$ (cite: Dors2011MNRAS.415.3616D). Although it has a positive correlation with the ionization parameter, the \[O III\]/\[O II\] also has a secondary dependence on metallicity, increasing with decreasing metallicity. \[S III\]/\[S II\] is not as sensitive to metallicity, making the ratio a more reliable tracer of the ionization parameter (cite: Kewley:2002). Differences between these diagnostics are discussed further in Section [7.3.1](#sec:result_ip). While \[S III\]$\lambda9532$ is not observed with MUSE, we measure the \[S III\]$\lambda9069$ and assume the fixed theoretical line ratio of \[S III\]$\lambda9532/\lambda9069=2.5$ (cite: FFCRecomData) in all calculations. Without observations of \[S III\]$\lambda9532$ we can not use this theoretical ratio to assess any impact of atmospheric absorption. Despite this, and discussed in Section [7.1.2](#res:te_te_intermediate), the low scatter between $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ suggest that the decrease in the \[S III\]$\lambda9069$ flux due to atmospheric absorption may be negligible.

## ALMA-CO: Intensity, Peak Temperature, and Velocity Dispersion

Using the ALMA 12m+7m+TP datacubes, we calculate moment 0, and 2 (integrated intensity and velocity dispersion) for molecular gas near each H II region. Because molecular and ionized gas are not entirely co-spatial at our resolution, it is necessary to make a selection to capture gas near the H II region. One possibility is to match H II regions to molecular clouds via a nearest-neighbor algorithm (cite: Grasha2019MNRAS.483.4707G; Zhang_starless_clumps2021A&A...646A..25Z; Zakardjian_GMC). We instead choose to integrate the ALMA spectrum contained in the H II region boundaries in order to measure the properties of the molecular gas closest in projection to the the ionized gas (i.e. in front, behind, or blended due to the resolution of KCWI) and likely affected by the radiative feedback. To measure the CO spectra, we reproject the H II region masks onto the grid of the ALMA datacubes and integrate the ALMA spectra for pixels located inside the footprint of each H II region.

From the ALMA spectrum, we then calculate the integrated intensity, $I_{\rm CO}$, peak temperature, $T_{\rm peak}$ and the velocity dispersion, $\sigma_{v, \mathrm{CO}}$. In order to accurately measure these CO moments in the presence of noise, we construct a signal mask following the basic approach from (cite: 2021Leroy_data). To do this, we locate the velocity channel which contains the peak emission and construct an integration window around this channel by including velocity channels with signal above the $1\sigma$ noise.

As a check on our analysis of molecular gas, we compare the calculated velocity dispersions to those from a sample of nearest-neighbor matched H II regions-GMC’s constructed by (cite: Zakardjian_GMC). We find that our $\sigma_{v, {\rm CO}}$ span a similar range, up to Log$_{10}$($\sigma_{v, {\rm CO}}/$\[km s$^{-1}$\])=1.5, with an average and standard deviations of Log$_{10}(\sigma_{v, {\rm CO}}/$\[km s$^{-1}$\])=0.88 $\pm$ 0.25; in line with the average from (cite: Zakardjian_GMC) which suggests that this method of extracting and measuring the CO properties is reasonable.

## H II Region Compact Clusters and Associations

In order to test for correlations between the young stellar populations that power H II regions and their electron temperatures, we compile the stellar mass and age of compact clusters and multi-scale stellar associations within our KCWI H II regions using results from HST observations.

We match the HST clusters to H II regions, with two or more auroral lines, by simply selecting all the clusters whose on-sky coordinates fall inside any H II region’s spatial footprint. For the associations, we match the NUV selected, 32 pc scale, stellar associations to the individual H II regions in the same manner as (cite: Scheuermann2023MNRAS.522.2369S). The associations catalog comes with spatial masks identifying the footprint of all the detected associations. Because the association masks have a finer pixel scale than the KCWI H II region masks, we reproject the KCWI mask onto the association mask pixel grid. We find for cluster matches that only 65 of 260 or (25%) of our H II regions are matched to a single cluster. 150 of 260 (or 57%) of our H II regions have zero matches. For association matches, only 85 or 260 (or 33%) of our H II regions are matched to a single association 45 of 260 (or 17%) of our H II regions have zero matches.

For the remaining regions with more than one clusters or association match, because we expect that the youngest and most massive clusters or associations contribute most to the overall ionization of the H II region, we assign to each H II region the age (mass) of the youngest (most massive) available cluster/association.

# Results

We present electron temperatures derived using the auroral-to-nebular line ratios from \[O II\], \[N II\], \[S II\], \[S III\], and \[O III\]. We construct $T_{\rm{e}}$–$T_{\rm{e}}$ diagrams to compare any multi-ionization zone $T_{\rm{e}}$ relationships to recently measured and/or modeled trends. We then compare the temperatures to properties of the ionized gas such as electron density, $n_{\rm{e}}$, and ionization parameter, $U$. We also relate the temperatures to properties of the molecular gas and stellar populations. We present in Table [\[tab:auroral_nebular_line_fluxes\]](#tab:auroral_nebular_line_fluxes) a summary of the measured emission lines and derived properties for the H II regions with two or more detected auroral line.

## Temperature-Temperature Relations

We show $T_{\rm{e}}$–$T_{\rm{e}}$ relations for our sample H II regions in Figures [8](#fig:temps_low_gals), [9](#fig:temps_intermediate_gals) and [10](#fig:temps_high_gals). The left panel displays the individual H II region measurements. To assess the significance of each $T_{\rm{e}}$–$T_{\rm{e}}$ relation, we calculate its p-value. A correlation is judged to be significant if it exhibits $p$ $\lesssim 10^{-3}$. With the exception of $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$–$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and the relations involving $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$, the remaining $T_{\rm{e}}$–$T_{\rm{e}}$ relations are deemed significant according to their p-value. For these significant $T_{\rm{e}}$–$T_{\rm{e}}$ relations we derive the best fitting linear relation using the Bayesian linear regression tool LINMIX [^11], which itself is a Python implementation of linear mixture model algorithm, LINMIX_ERR, constructed by (cite: Kelly:2007:linmix). The linear regression in LINMIX includes an additional term to represent the intrinsic scatter weighting each data point. In the panels of Figure [8](#fig:temps_low_gals) and Figure [9](#fig:temps_intermediate_gals) we report $\sigma_{int}$, or the median of the Normal distributed scatter around the linear regression, and the total scatter, $\sigma_{tot}$. Furthermore, to better see $T_{\rm{e}}$–$T_{\rm{e}}$ relationships in individual galaxies we show in the right panel the $T_{\rm{e}}$–$T_{\rm{e}}$ relations for temperatures binned in steps of 2000 K in the x-axis, with minimum 2 H II regions per bin, for each galaxy. Alongside the binned data we show recent $T_{\rm{e}}$–$T_{\rm{e}}$ relations from (cite: Berg2020ApJ...893...96B), (cite: Rogers:chaos:2021), (cite: Zurita2021MNRAS.500.2359Z), (cite: Garnett1992AJ), (cite: BOND), and (cite: Delgado_Desire2023arXiv230513136M).

### Low-Ionization Zone

The low-ionization zone $T_{\rm{e}}$–$T_{\rm{e}}$ relations are shown in Figure [8](#fig:temps_low_gals). The top figure shows the $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$–$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ comparison. We observe that $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ gives higher values than $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ by 1000 K on average. The magnitude of this offset is largest when $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$$>1.0\times10^4$ K. The $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$$>$$T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ inequality is also reflected in the relations from , , and . We also show in grey the best-fit line, and the corresponding 1$\sigma$ uncertainty, described by, $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$$=(0.47 \pm 0.13)\times$$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$$+(0.36\pm0.10)$. The , , and relations are within the uncertainties of the fit, indicating that the $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$–$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ relation is in good agreement with these studies. We also measure scatter around the trend line of $\sigma_{int}=560$ K and $\sigma_{tot}=844$ K, both of which are in good agreement with the reported values of $\sigma_{int}=588$ K and $\sigma_{tot}=810$ K by .

The comparison between $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$–$T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ is shown in the middle panel of Figure [8](#fig:temps_low_gals). The best-fit line is described by $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$$=(0.85 \pm 0.15)\times$$T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$$+(0.13\pm0.12)$. Only the trend from is within the uncertainties of our fit. Both and favor a steep slope (i.e. hotter $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$) which are outside the 1$\sigma$ bounds of our fit. We measure a low intrinsic scatter $\sigma_{int}=735$ K but a larger total scatter $\sigma_{tot}=4744$ K. For comparison, report $\sigma_{int}=945$ K and $\sigma_{tot}=1460$ K.

We show the temperature relation between $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$-$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ in the bottom-left panel. We observe large scatter around the line of equality, $\sigma_{tot}=2279$ K, towards hot temperatures and measure a p-value, p$=0.09$, that suggests the two temperatures are uncorrelated. We discuss a potential, physical explanation of the scatter in Section [7.2](#results:density_inhomogeneities), but first we explore effects on the correlation due to low S/N detections. Low S/N detections of weak emission can have an intrinsic bias towards higher values (cite: Rola1994A&A_SN), which in the case of weak detections of the auroral lines of \[S II\] and \[O II\], would result in high temperatures. To explore how S/N changes the observed trend, we re-calculated the p-value line using only $T_{\rm{e}}$ derived from \[S II\] and \[O II\] auroral lines with S/N $>$ 5. Using the higher S/N threshold, the p-value returned is now, p$=0.04$, but not significant according to our criteria. Furthermore, the total scatter, $\sigma_{tot}=1743$ K, around the 1-to-1 line is trend is high.

We observe in the $T_{\rm{e}}$–$T_{\rm{e}}$ relations that $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ are systematically hotter than $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$. Based on photoionization models (cite: cambell:1986; Garnett1992AJ), the low-ionization zone temperatures are expected to be equal. There are systematic effects that could increase $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ temperatures such that $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$$\sim$$T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$$>$$T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$. The wide wavelength range between \[O II\]$\lambda\lambda7320,7330$ and \[O II\]$\lambda\lambda3726,3729$ as well as \[S II\]$\lambda\lambda4068,4076$ and \[S II\]$\lambda\lambda6716,6731$, make these ratios sensitive to the applied reddening correction. An overestimate in the extinction would lead to an underestimate of $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and underestimate of $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$. At the same time this would leave $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ relatively unchanged due to the proximity in wavelength of the requisite lines. We see that both $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ are greater than $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ which is not compatible with the effects of overestimated extinction correction. Despite the above, our temperatures hierarchy could potentially be produced by under-estimated extinction as this would lead to over-estimates of $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ while again leaving $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ unchanged. We tested two different extinction prescriptions (cite: ExtinctionCorr1994ApJ...422..158O; Fitzpatrick1999PASP..111...63F) and found no change in our results. Due to the possible DIG contribution to the measured extinction, it is more likely that we could be overestimating the extinction than underestimating it (cite: Congiu:2023). Telluric contamination to the line emission at \[O II\]$\lambda\lambda7320,7330$ could be an additional systematic error, but is unlikely to be significant in our data because the \[O II\]$\lambda7320$/$\lambda7330$ ratio measured for our sample is $1.27 \pm 0.3$, in agreement with values predicted by the transition probabilities and the collisional strengths (cite: Zeippen1982; Kisielius2009) and observed in nearby H II regions (cite: 1957ApJ...125...66S; 1976ApJS...31..163K; Yates2020A&A...634A.107Y; mendezdelgadoHH514). The \[S II\]$\lambda\lambda4068,4076$ doublet may contain $\sim 10\%$ contamination due to O II recombination emission near the location of \[S II\]$\lambda\lambda4068,4076$ (cite: Delgado_Desire2023arXiv230513136M) that could bias $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ upwards by $\sim 0.2 \times 10^4$ K for $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ $< 2.0 \times 10^4$ K. The KCWI spectral resolution is too low to separate out any contamination in the measurements of \[S II\]$\lambda\lambda4068,4076$. Lastly, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ have a higher sensitivity to electron density inhomogeneities than $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ (cite: Rubin:1989; Osterbrock:2006; Delgado_Desire2023arXiv230513136M). \[O II\] and \[S II\] start to be dependent on density around $n_{\rm{e}}\approx 10^3$ cm$^{-3}$ while \[N II\] is independent of density up to $n_{\rm{e}} \approx 10^4$ cm$^{-3}$.

Despite the all of the above factors, including S/N considerations, and given the agreement of the $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$–$T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$–$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ trends with those from using the S/N $> 3$ \[O II\] and \[S II\] auroral lines, we are motivated to explore potential biases due to uncertainties in the measured electron density, see Section [7.2](#results:density_inhomogeneities).

### Intermediate Ionization Zone

The $T_{\rm{e}}$–$T_{\rm{e}}$ relations between the low and intermediate-ionization zone temperatures are shown in Figure [9](#fig:temps_intermediate_gals). Given the lower ionization potentials of O$^+$, N$^+$, and S$^+$ with respect to S$^{++}$, it is possible to have differences in the temperature in the different ionization zones (cite: Garnett1992AJ). We compare our observed $T_{\rm{e}}$–$T_{\rm{e}}$ relations to predictions from photoionization models for giant H II regions produced by the Bayesian Oxygen and Nitrogen abundance project and found in the Mexican Million Models database (cite: MexicanMillionModels). When available, we also compare the observations to relations from , , and .

The top panel of Figure [9](#fig:temps_intermediate_gals) shows the temperature comparisons between $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ and $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$. The best-fit line, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$$=(0.67 \pm 0.27)\times$$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$$+(0.022\pm0.022)$, closely follows the relationship reported by . We measure an intrinsic, $\sigma_{int}=1002$ K, and total scatter, $\sigma_{tot}=1496$ K. The models predict that the temperature $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ should be greater than $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ by a small constant offset across the full temperature range. However, our data suggest $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ rises faster than $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$. Our binned data favor the empirical trend line from . However, there is a grouping of points from NGC 5068 that show contrasting behavior in both the individual and binned data comparisons.

The $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ comparison, comprised of 108 H II regions, is shown in the middle panel of Figure [9](#fig:temps_intermediate_gals). The best fit line for this comparisons is described by, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$$=(1.11 \pm 0.25)\times$$T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$$-(0.045\pm0.21)$. Within uncertainties, the $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$$--$$T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ agree with trends observed by and that derived from . However, both the intrinsic, $\sigma_{int}=1627$ K, and total scatter, $\sigma_{tot}=2598$ K, are large. The binned data do not reveal a preference for either of the literature trend.

The series of CHAOS $T_{\rm{e}}$–$T_{\rm{e}}$ comparisons (cite: Berg2015ApJ...806...16B; Berg2020ApJ...893...96B; Rogers:chaos:2021; Rogers:chaos:2022) and have observed a tight relationship between $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ and $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$. We show in the bottom panel of Figure [9](#fig:temps_intermediate_gals) the $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ and $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ comparison. Satisfying the expectations driven by these past studies, we observe that the trend between $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ and $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ exhibits the smallest scatter of the $T_{\rm{e}}$–$T_{\rm{e}}$ relations presented here. The trend between these temperatures is described by, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$$=(1.35 \pm 0.15)\times$$T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$$-(0.24\pm0.11)$, and exhibit intrinsic scatter, $\sigma_{int}=997$ K, and total scatter, $\sigma_{tot}=$1313 K; both of which are larger than $\sigma_{int}=173$ K $\sigma_{tot}=$507 K reported by .

For the $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ and $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ comparison there are available empirical relations from , , and which we overlay in addition to the models. The data show a clear disagreement with the trend observed by . We observe a large fraction of the binned data that lie near the model, and relations at low $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$. Regions with hotter $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ would be needed to to further differentiate between the models and empirical trends.

### High Ionization Zone

We show $T_{\rm{e}}$–$T_{\rm{e}}$ relations between \[O III\] temperatures (which trace the high ionization zone) and those from the low-intermediate ionization zones in Figure [10](#fig:temps_high_gals). Additionally, we overlay $T_{\rm{e}}$–$T_{\rm{e}}$ relations from , , and . Although we observe some H II regions with $T_{\rm{e}}$–$T_{\rm{e}}$ relations that agree with literature relations, we also observe numerous H II regions with much higher $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ values of than what is predicted by models with the given low and intermediate ionization zone temperatures. The total scatter around the line of equality in $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ range between 3100 K and 4500 K. Given this large scatter we do not perform a linear regression analysis for these comparisons.

Based on previous findings from and , the scatter towards large excess in $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ for regions with cooler low and intermediate ionization zone temperatures is unexpected. With IFUs we are perhaps capturing a wider range of H II regions. Furthermore and extend to lower metallicities, and possibly higher ionization parameters, where $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ may be better behaved. Nevertheless, these regions represent an extremely limited sub-set of the data and are at the boundary of significant, so are subject to higher uncertainty. For the $\sim$ Solar metallicities for our H II region sample, where the relative flux \[O III\]$\lambda4363$ is expected to be $< 10^{-2} \times$ H$\beta$ (cite: Berg2015ApJ...806...16B), the temperature from \[O III\]$\lambda4363$ would have to be high in order to be detected. The small number of \[O III\]$\lambda4363$ detections reflects this. Because we do not expect to detect the line in most H II regions, the ones we do detect may be unusual cases or statistical outliers, especially given that the average S/N of the \[O III\] detections is $\sim$4. We explore S/N effects by increasing the threshold for comparison to S/N $> 5$ in \[O III\]$\lambda4363$. This reduces the sample of regions with $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ measurements to 5 which is too low to confidently fit a trend, but, we measure a large total scatter, $\sigma_{tot} > 2000$ K, around the line of equality. Discussed further in Section [7.3.1](#sec:result_ip) and in (cite: Yates2020A&A...634A.107Y), these regions exhibit low \[O III\]/\[O II\] ratios, meaning they are systems with low O$^{++}$/O$^{+}$. This would mean that small fraction of the total nebulae volume would be described by the high $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$. Despite this, there has been evidence (cite: Peimbert1991shocks; Binette2012_OIII_shocks) that shock excitation can preferentially enhance the high ionization zone temperature, with the highest enhancement occurring in high metallicity environments. How this scenario could apply to this small sub-set of H II regions is explored in Section [7.3.4](#res:high_o3).

![image](TOII_vs_TNII_gals.pdf) ![image](TNII_vs_TSII_gals.pdf) ![image](TOII_vs_TSII_gals.pdf)

![image](TOII_vs_TSIII_gals.pdf) ![image](TSII_vs_TSIII_gals.pdf) ![image](TNII_vs_TSIII_gals.pdf)

## The Impact of Density Inhomogeneities on \[S II\] and \[O II\] Temperatures

Recent studies have suggested that the temperatures obtained from the auroral-to-nebular lines ratios of \[O II\] and \[S II\] can be biased upwards due to the presence of density inhomogeneities, even while the average density is underestimated by nebular doublet line \[O II\]$\lambda\lambda3726,3729$ and \[S II\]$\lambda\lambda6716,6731$ diagnostics.

For example, in a sample of 190 high-signal-noise spectra of H II regions and other photoionized nebulae, (cite: Delgado_Desire2023arXiv230513136M) observed systematically hotter $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ relative to $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, similar to what we observe, which they attribute to the presence of density inhomogeneities. The atomic levels responsible for the nebular lines \[S II\]$\lambda\lambda6731,6716$ and \[O II\]$\lambda\lambda3726,3729$, listed in Table [\[tab:atomic_references\]](#tab:atomic_references), have critical densities of order $10^3$ cm$^{-3}$ which are at least two orders of magnitude lower than the critical densities for the nebular levels of \[N II\]. In addition, the auroral levels of the same ions have very high critical densities. This makes the auroral-to-nebular temperature diagnostics of $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ density sensitive above $10^3$ cm$^{-3}$, and therefore susceptible to biases if there are important contributions to the line flux from gas above that density. The auroral-to-nebular ratio of \[N II\], however, is not susceptible to such sensitivity until much higher densities.

Both \[S II\]$\lambda\lambda6731,6716$ and \[O II\]$\lambda\lambda3726,3729$ nebular line doublet ratios serve as density diagnostics for densities $10^2$ cm$^{-3}<$ $n_{\rm{e}}$ $<$ $10^{3.5}$ cm$^{-3}$. Furthermore, because of the bias described above, (cite: Delgado_Desire2023arXiv230513136M) show that at fixed temperature the auroral-to-nebular line ratios for \[O II\] and \[S II\] can serve as a density diagnostic over a large range of electron density, $10^2$ cm$^{-3}<$ $n_{\rm{e}}$ $<$ $10^{6}$ cm$^{-3}$. For a uniform density H II region, the $n_{\rm{e}}$ returned from both of these diagnostics should be identical, as long as $n_{\rm{e}}$ is within the sensitivity range of the diagnostics. However, in the presence of density inhomogeneities, different density diagnostics can return conflicting values. Even if high density gas clumps make up a small fraction of the gas, such regions can continue to contribute to the auroral line emission while no longer contributing significantly to the nebular lines, since the effects of collisional de-excitation on the nebular lines will reduce their emissivities relative to the auroral lines (cite: Rubin:1989). Because of this, the nebular \[S II\] and \[O II\] lines can reflect the dominant contribution of low-density gas, while the auroral \[S II\] and \[O II\] lines will be sensitive to volume of high-density gas (cite: Peimbert:1971; Rubin:1989; Delgado_Desire2023arXiv230513136M).

To investigate if the presence of density inhomogeneities could bias our measured $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ we compare the observed auroral-to-nebular line ratios \[O II\] and \[S II\] to those predicted using fixed $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$. For this comparison we use the regions with auroral line detections for all three low-ionization zone ions. We show in Figure [11](#fig:ne_result) the measured \[O II\]$\lambda\lambda7320,7330$/$\lambda\lambda3726,3729$ and \[S II\]$\lambda\lambda4069,4076$/$\lambda\lambda6716,6731$ line ratios versus the region’s $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$. We overlay the predicted trends of auroral-to-nebular line ratios calculated using $n_{\rm{e}}=10^2~\mathrm{cm}^{-3}$, $10^{2.5}~\mathrm{cm}^{-3}$, and $10^{3}~\mathrm{cm}^{-3}$. We see in Figure [11](#fig:ne_result) that under the assumption that $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$$=$$T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$$=$$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$, the largest measured auroral-to-nebular line ratios could be consistent with $T_{\rm{e}}$ traced by $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ but with a higher electron density than that returned by \[S II\]$\lambda\lambda6731,6716$ in the low-density limit. This suggests that under inhomogenous conditions, underestimated contributions from $>10^3$ cm$^{-3}$ gas to the nebular \[O II\] and \[S II\] lines could bias the density diagnostics and then the use of underestimated densities in temperature calculations for ions with low critical densities like \[O II\] and \[S II\] could lead to hotter estimated temperatures inferred from auroral-to-nebular ratios.

At the same time, Figure [11](#fig:ne_result) also shows that the lowest measured auroral-to-nebular ratios lie below the theoretical curves for ratios with densities equal to the low-density limit. It may be the case that, under our assumption that the H II region low-ionization zone $T_{\rm{e}}$ is described by $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, these regions physically exhibit volumes of gas with $n_{\rm{e}} \lesssim 10~\rm{cm}^{-3}$ or lower (cite: Kennicutt1984ApJ...287..116K). However, we are unable to verify this using the available diagnostics because densities returned by either the \[O II\] and \[S II\] doublet or their auroral-to-nebular line ratios are uncertain in this regime. For these reason we do not pursue further interpretation of these points.

![image](sii_auroral_ne.pdf) ![image](oii_auroral_ne.pdf) ![image](sii_ne_hb.pdf) ![image](oii_ne_hb.pdf)

We can further explore potential density inhomogeneities by comparing the measured auroral-to-nebular lines to the regions H$\beta$ surface brightness. The emission from any recombination lines is proportional to $n_{\rm{e}}n({\rm{X}^+})\alpha_{eff}$, where $n({\rm{X}^+})$ is the number density of the emitting ion and $\alpha_{eff}$ is the effective recombination coefficient (cite: Piembert2017PASP..129h2001P). For H$\beta$, $n({\rm{X}^+})\propto n_{\rm{e}}$ because 90% of free electrons will come from the photoionization of H which represents $\sim$90% of all the gas. For a uniform density H II region, the H$\beta$ surface brightness, SB$_{\rm{H}\beta}$, would be proportional to $n_{\rm{e}}^2$. In the case of H II regions with high density inclusions, the variance of $n_{\rm{e}}$ would be expected to rise due to the increase in the average of the density squared (i.e. $<n_{\rm{e}}^2>$). Under such conditions, it would be reasonable to expect that H$\beta$ surface brightness would increase as SB$_{\rm{H}\beta} \propto <n_{\rm{e}}^2>$.

If we interpret the departure of the measured auroral-to-nebular lines ratios from the theoretical ratios calculated by fixing the electron density at the low-density limit, $n_{\rm{e}}=100~\rm{cm}^{-3}$ and $T_{\rm{e}}=$$T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, then we could expect that this deviation would correlate with the H$\beta$ surface brightness. We show in the bottom panels of Figure [11](#fig:ne_result) the degree of inhomogeneities, measured by \[S II\]-\[S II\]($n_{\rm{e}}=100$, $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$) and \[O II\]-\[O II\]($n_{\rm{e}}=100$, $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$), against the regions H$\beta$ surface brightness.

We find a significant correlation, p-value $<10^{-3}$, between \[S II\]-\[S II\]($n_{\rm{e}}=100$, $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$) and SB$_{\rm{H}\beta}$, which suggests that the regions with large deviations from the predicted low-density limit auroral-to-nebular line ratios are consistent with density inhomogeneities. The best-fit line is described by \[S II\]-\[S II\]($n_{\rm{e}}=100$, $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$) $=0.0147(\pm 0.004)\times\rm{SB}_{\rm{H}\beta}+0.20(\pm0.05)$. To account for any uncertainties in the atomic data, we vary the absolute value of the \[S II\]($n_{\rm{e}}=100$, $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$) curve by $\pm$ 10% (cite: Mendoza_atomic_comparisons) and find no change in correlation strength. While this correlation is suggestive of density inhomogeneities, we acknowledge that the H II regions are not fully resolved which means we are measuring a PSF-averaged surface brightness. Because of this, it is unclear if this correlation can be fully link to density inhomogeneities.

For the comparison involving \[O II\]-\[O II\]($n_{\rm{e}}=100$, $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$), we find no significant correlation with H$\beta$ surface brightness, even when using S/N$>5$ auroral lines. While the exact reason for the non-correlation between \[O II\]-\[O II\]($n_{\rm{e}}=100$, $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$) and H$\beta$ surface brightness is unknown it is important to note that the ionization potential of \[S II\] is less than both $H\beta$ and \[O II\]. This difference in ionization potential means that H II region \[S II\] and \[O II\] may not be co-spatial, and may have different sensitivities as tracers of high density inclusions. However, given that these regions have measurements of all three low-ionization zone auroral lines and survive a DIG contrast constraint, we find that the correlation between \[S II\]-\[S II\]($n_{\rm{e}}=100$ and SB$_{\rm{H}\beta}$ suggests that density inhomogeneities may be affecting the low-ionization zone temperatures. Future studies with multiple density diagnostics and high spatial resolution will be valuable to exploring the potential impact inhomogeneous conditions have on these diagnostics.

## Temperature Differences Compared to H II Region Ionized Gas, Stellar Population, and Molecular Gas Properties.

Studies have shown that H II region temperatures for different ionization zones can be differently impacted by properties of the ISM. Temperature comparisons presented in (cite: Berg2020ApJ...893...96B) using H II regions observed in four nearby galaxies revealed that the dispersion around low-intermediate and intermediate-high $T_{\rm{e}}$–$T_{\rm{e}}$ relation ships increased (or decreased) with the ionization parameter. Another trend with ionization parameter was observed by (cite: Yates2020A&A...634A.107Y). They found that systems with low ionization, or larger ratios of O$^{+}$/O$^{2+}$ parameter would exhibit systematically hotter $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$. Though (cite: Arellano2020) argue this could be explained by increased iron contamination to \[O III\]$\lambda4363$. Discussed in Section [7.2](#results:density_inhomogeneities), density fluctuations can also bias the temperatures for the low-ionization zone due to the sensitivity of \[O II\] and \[S II\] with density (cite: Delgado2023arXiv230511578M; Delgado_Desire2023arXiv230513136M).

Given that stars are the primary source of ionizing photons, it is reasonable to suspect that the properties of the stellar population ionizing the H II region can potentially play a role in setting the $T_{\rm{e}}$ structure of H II regions. Another potential factor on the $T_{\rm{e}}$ structure, and traced by its effects on the surrounding molecular gas, is the degree of stellar feedback within H II regions. Although very important to our understanding, the physical processes that impact the $T_{\rm{e}}$ structure in H II regions remain uncertain (cite: Garnett1991ApJ...373..458G; Nicholls2020PASP..132c3001N).

The KCWI+MUSE H II regions combined with the PHANGS-HST and PHANGS-ALMA observations allow us to investigate how $T_{\rm{e}}$ is impacted by different H II ISM, stellar and molecular gas properties. We compare temperature differences, $\Delta$($T_{\mathrm{ion,1}}$,$T_{\mathrm{ion,2}}$)=$T_{\mathrm{ion,1}}$$-$$T_{\mathrm{ion,2}}$, between the low, intermediate, and high-ionization zone temperatures. with H II region properties derived from emission line diagnostics; with the properties of the surrounding molecular gas measured from ALMA (cite: 2021Leroy_data); and with stellar population masses/ages from SED fitting to HST photometry (cite: 2022PHANGS_HST; ThilkerCompactClusters; Larson2023).

To gauge the significance and monotonicity of each comparison we calculate the Pearson correlation coefficient (i.e. p-value or $p$), as well as the Spearman Rank Correlation Coefficient, $\rho$. A correlation is judged to be significant if it exhibits $p$ $\lesssim 10^{-3}$. The strength of the correlation is separated into the following regimes: $1 > |\rho| > 0.8$ corresponds to a *strong* correlation, $0.8 > |\rho| > 0.4$ corresponds to a *moderate* correlation and $0.4 > |\rho| > 0$ identifies a *weak* or no correlation.

As expected, we observe strong correlations between temperatures differences with ionization parameter. We do not report any significant correlations between $\Delta T_{\rm{e}}$ with any of the following properties: integrated CO intensity, CO peak temperature, molecular gas velocity dispersion, cluster mass, cluster age, association age, association age. Figures showing the $\Delta T_{\rm{e}}$ comparisons to these parameters are shown in Appendix [14](#appn:uncorrelated_properties). Despite no significant correlations, we do find interesting behavior between $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) with association mass, and excess $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ with molecular gas velocity dispersion. We discuss these special cases and the details of the comparisons in the following subsections. The statistics of the correlations with H II region ionization parameter are summarized in Table [\[tab:summary_table_1\]](#tab:summary_table_1).

cccc $\Delta T_{\rm{e}}$ & 2c\[S III\]/\[S II\] & 2c\[O III\]/\[O II\] & 2c$\eta$\
& 2c($\rho$, p) & 2c($\rho$, p) & 2c($\rho$, p)\
$\Delta$($T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$) & - & - & -\
$\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$) & (-0.27, $<10^{-3}$) & - & -\
$\Delta$($T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$) & (0.32, $<10^{-3}$) & - & -\
$\Delta$($T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) & - & - & -\
$\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) & - & - & -\
$\Delta$($T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) & (0.53, $<10^{-3}$) & - & (0.46, $<10^{-3}$)\
$\Delta$($T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$) & - & (0.85, $<10^{-3}$) & -\
$\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$) & (0.72, $<10^{-3}$) & (0.82, $<10^{-3}$) & -\
$\Delta$($T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$) & (0.75, $<10^{-3}$) & (0.75, $<10^{-3}$) & -\
$\Delta$($T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$) & - & (0.82, $<10^{-3}$) & -

### Correlations between Temperature Differences, Ionization Parameter, and Radiation Softness Parameter

We show in Figures [12](#fig:ip_S_comparisons) and [13](#fig:ip_O_comparisons) the comparisons between temperature differences and the ionization parameter, $U$, traced with both \[S III\]/\[S II\] and \[O III\]/\[O II\]. In both comparisons the low-ionization zones show no correlations, but there is a moderate correlation the low and intermediate-ionization zone, traced by $\Delta$($T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$), with \[S III\]/\[S II\]. The comparisons of the low-intermediate and high-ionization zones have high correlation with both \[S III\]/\[S II\] and \[O III\]/\[O II\].

![image](all_gall_tdiff_SIII_SII_low_ionization_.pdf) ![image](all_gall_tdiff_SIII_SII_mid_ionization_.pdf) ![image](all_gall_tdiff_SIII_SII_high_ion_.pdf)

![image](all_gall_tdiff_OIII_OII_low_ionization_.pdf) ![image](all_gall_tdiff_OIII_OII_mid_ionization_.pdf) ![image](all_gall_tdiff_OIII_OII_high_ion_.pdf)

We observe correlations between $\Delta$($T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) with \[S III\]/\[S II\]. For all temperature differences with $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ we also observe strong correlations between $\Delta T_{\rm{e}}$ and \[S III\]/\[S II\]. The largest temperature differences are associated with the smallest values of \[S III\]/\[S II\]. As \[S III\]/\[S II\] increases, $\Delta T_{\rm{e}}$ converges to $\Delta T_{\rm{e}}=0$. Shown in Figure [13](#fig:ip_O_comparisons), we present the same temperature differences but using \[O III\]/\[O II\] as a tracer for $U$. All the correlations with ionization parameter that do not involve $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ disappear when using \[O III\]/\[O II\] as a tracer. The remaining $\Delta T_{\rm{e}}$ that include $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ show similar correlations as before with ionization parameter when using \[O III\]/\[O II\]. In both cases, the largest temperature differences occur at the lowest values of ionization parameter, traced by either \[S III\]/\[S II\] or \[O III\]/\[O II\].

Our correlations with ionization parameter tracers are similar to the results presented in (cite: Yates2020A&A...634A.107Y). When comparing the temperatures of the low and high ionization zone for oxygen, (cite: Yates2020A&A...634A.107Y) observed an increase in the $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$/$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ ratio that is anti-correlated with the ratio of $\rm{O}^{2+}/\rm{O}^{+}$ (which closely follows the ionization parameter traced by \[O III\]/\[O II\]). Our H II regions are all likely to be in the relatively high metallicity regime, where $\rm{O}^{+}$ should be the dominant ionization state of oxygen. Here, the average electron temperature will be best described by the auroral-to-nebular line ratio of \[O II\] (with caution about density inhomogeneities, as previously noted). Nevertheless, emission from \[O III\]$\lambda4363$ can still be produced, albeit more weakly, and given the exponential temperature dependence, it will be biased towards hotter gas. Therefore, if there are temperature inhomogenieities, the \[O III\] temperatures may reflect a small amount of hot, high ionization gas and may not agree with the auroral-to-nebular line ratio of \[O II\]. (cite: Yates2020A&A...634A.107Y) predict that regions with $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ $>$ $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ will be $\rm{O}^{+}$ dominant, i.e. $\rm{O}^{+}/\rm{H}^{+}> \rm{O}^{2+}/\rm{H}^{+}$ . Because \[O III\]/\[O II\] $\propto$ $\rm{O}^{2+}/\rm{O}^{+}$, we would expect to see the largest deviations in $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ at the lowest \[O III\]/\[O II\]. To summarize, (cite: Yates2020A&A...634A.107Y) postulate that the differences between hotter high ionization zone temperatures, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ and the low ionization zone temperature, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ will increase with decreasing ionization parameter. These trends should in theory also be evident for sulfur, although these correlations were not explored by (cite: Yates2020A&A...634A.107Y). Similar trends of temperature differences associated with different ionization states of the gas have been discussed by (cite: Berg2020ApJ...893...96B).

![image](TOII_vs_TOIII_ip_gals.pdf) ![image](TSII_vs_TSIII_ip_gals.pdf)

In Figure [14](#fig:te_yates_plot), we plot the $T_{\rm{e}}$–$T_{\rm{e}}$ between $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$–$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$–$T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ colored by the value of \[O III\]/\[O II\] and \[S III\]/\[S II\]. We also annotate the plot according to the schematics from Figure 3 of (cite: Yates2020A&A...634A.107Y). For both oxygen and sulfur, the largest ratios of $T_{\rm{e},\text{[{X}{ \uppercase{\romannumeral 3\relax}}]}}$/$T_{\rm{e},\text{[{X}{ \uppercase{\romannumeral 2\relax}}]}}$, where X is either S or O, occur for the lowest values of ionization parameter, as indicated by the value of the line ratio. This suggests we are observing a similar correlation with ionization parameter as postulated by (cite: Yates2020A&A...634A.107Y).

If we consider the similarity between our results and (cite: Yates2020A&A...634A.107Y) as evidence for correlations between $\Delta T_{\rm{e}}$ and $U$, then why is it that the correlation between $\Delta$($T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) and $U$ traced by \[S III\]/\[S II\] is not evident when using \[O III\]/\[O II\] as a tracer for $U$? It might be the case that \[S III\]/\[S II\] and \[O III\]/\[O II\] do not change with $U$ in similar ways, as \[S III\] and \[O III\] arise from different ionization zones and conditions. It is possible that density inhomogeneities may be playing a role, both \[S II\] and \[O II\] have similar low critical densities, unlike either \[S III\] and \[O III\]. It remains unclear why some $\Delta T_{\rm{e}}$ vs. $U$ trends disappear.

We explore the correlations with $\Delta T_{\rm{e}}$ using a combination of both \[S III\]/\[S II\] and \[O III\]/\[O II\]. (cite: Vilchez:1988) define the “radiation softness" parameter, $\eta=$(\[O II\]/\[O III\])/(\[S II\]/\[S III\]), as a diagnostic of the effective temperature of the ionizing stars. Shown in Appendix [14](#appn:uncorrelated_properties) Figure [31](#fig:eta_comparisons), we find a correlation between $\Delta$($T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) and $\eta$ with similar $p$ and $\rho$ values as the correlation with $U$. There are no correlations between temperature differences involving $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ with $\eta$. Because $\eta$ is a measure of ionizing properties of the ionizing stars, the correlation between $\eta$ and $\Delta$($T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) may suggest that $T_{\rm{e}}$’s derived from sulfur lines are sensitive to the stellar population while $T_{\rm{e}}$’s from oxygen are more sensitive to the physical conditions of the ionized gas. However, a future comparison with a larger sample of $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$’s would be beneficial in solidifying such an interpretation.

### Temperatures Differences with Stellar Mass and Age

Next we compare temperature differences to stellar mass and ages from compact stellar clusters and associations matched to our H II regions. As presented in Appendix [12](#appn:comparison_of_muse_and_kcwi_hii_regions) Figures [32](#fig:age_cluster_comparisons)–[34](#fig:age_associations_comparisons), we find no correlations between $\Delta T_{\rm{e}}$ with cluster mass, cluster age, or with association mass and age.

Although the correlation is not statistically significant according to our criteria, we speculate on a possible positive correlation, between the most reliable $\Delta T_{\rm{e}}$ indicator without density inhomogeneity issues, $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) with the association mass. Figure [15](#fig:mass_associations_comparisons) shows the comparisons between $\Delta$($T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$), $\Delta$($T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$), and $\Delta$($T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$). While the scatter for both $\Delta$($T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) and $\Delta$($T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) are centered around zero, it appears to be the case that $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ is cooler than $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ towards the low-mass end and vice-versa on the high-mass end. As discussed in Section [6.5](#sec:hst_matching), we assigned the largest mass stellar population to the H II region if the region was matched to more than one association. To see if this choice has any impact on the strength of the correlation, we plot in Figure [16](#fig:total_mass) the $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) against the sum of the matched association masses. Using the total masses, we observe no change in the strength of the correlation.

![image](all_gall_tdiff_A_Mass_low_ionization_.pdf) ![image](all_gall_tdiff_A_Mass_mid_ionization_.pdf) ![image](all_gall_tdiff_A_Mass_high_ion_.pdf)

![](T_NII_T_SIII_diff_compare_association_Tmass.pdf)

It is possible that the correlation between $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) and association mass may result from biases introduced by an under-sampling of initial mass function. Similar to our study, (cite: Scheuermann2023MNRAS.522.2369S) matched the stellar association catalog (cite: Larson2023) to H II regions in the Nebular catalog (cite: Kreckel2019ApJ...887...80K; Groves2023NebCat). Instead of including all masses measured for the associations, which we do in this work, (cite: Scheuermann2023MNRAS.522.2369S) implement a cut-off and assume masses $< 10^4 M_{\odot}$, as masses below the threshold do not sample the IMF (cite: DaSilva:2012). We perform no such cutoff in this study. The correlation between $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) and $M_{\mathrm{Association}}$ correlation includes many regions with masses $< 10^4 M_{\odot}$, where the IMF may not be fully sampled. Despite this, we do not fully dismiss this correlation; however, the effects that undersampling the IMF could have on the correlation with $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) warrants further investigation with a larger sample size on order to expand the dynamic range of association mass.

### Temperatures Differences and Molecular Gas Properties

We compare temperature differences to the properties of the molecular gas derived from CO emission measured within the projected boundaries of our sample of H II regions. For the comparisons to $I_{\rm CO}$, shown in Figure [35](#fig:ico_comparisons) of Appendix [14](#appn:uncorrelated_properties) , and comparisons to $T_{\rm{peak}}$, shown in Figure [36](#fig:ptemp_comparisons) of Appendix [14](#appn:uncorrelated_properties), we observe no correlations with temperature differences between the low, intermediate, and high ionization zones.

We show in Figure [17](#fig:rms_comparisons) the temperature differences compared to the CO velocity dispersion ($\sigma_{v, \mathrm{CO}}$). We observe a moderate correlation between $\sigma_{v, \mathrm{CO}}$ and $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$). The values of $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) over the range of $\sigma_{v, \mathrm{CO}}$ is small, only encompassing $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) from $-$1000  K to 2000 K. Given the possible correlation with association mass, and this correlation with $\sigma_{v, \mathrm{CO}}$, we find it intriguing that these correlations between the low and intermediate ionization zone are only seen in $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$). It is possible that the low scatter in $T_{\rm{e}}$–$T_{\rm{e}}$ relationship between $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ and $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ in the presence of density inhomogeneities, contrary to the temperatures from \[S II\] and \[O II\], allow for better insight into these underlying trends.

We observe that all the correlations of $\Delta T_{\rm{e}}$ involving $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ and $\sigma_{v, \mathrm{CO}}$ have large, negative, $\rho$ values, but are all insignificant according to their p-values. The high Spearman rank values for the comparisons between $\Delta T_{\rm{e}}$ and $\sigma_{v, \mathrm{CO}}$ appears to be largely driven by the highest values of $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$. Despite the fact that the correlations are not strong, it is clear that the high $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ regions go along with high CO velocity dispersion.

![image](all_gall_tdiff_rms_bw_low_ionization_.pdf) ![image](all_gall_tdiff_rms_bw_mid_ionization_.pdf) ![image](all_gall_tdiff_rms_bw_high_ion_.pdf)

The CO velocity dispersion can be enhanced by low-velocity shocks originating from the interaction of molecular gas with late-time-expansion of supernovae remnants (cite: Koo:2001_SN_CO; Zhou:2023arXiv), as well as from interaction with low-velocity shocks from pressure-radiation driven H II region expansion (cite: Hill1978HII_Shocks; Kothes:2002; Watkins2023CO_bubbles). These low-velocity shocks are also predicted to enhance $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$. Shock modeling has shown that outward expanding low-velocity shocks can create conditions, such as pockets of high post-shock temperature, where the strength of \[O III\]$\lambda4363$ emission will be enhanced compared to the little to no increase in emission from \[O III\]$\lambda5007$ (cite: Peimbert1991shocks; Binette2012_OIII_shocks; MendezDelgado2021HerbigHaro). The combination of large temperature differences with $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ and high $\sigma_{v, \mathrm{CO}}$ suggests that we may be observing the effects of low-velocity shocks. Motivated by this scenario, we search the H II regions for evidence of low-velocity shocks in the following section.

### Investigating H II Regions for Presence of Low-Velocity Shocks

The correlations of $\Delta T_{\rm{e}}$ involving the high ionization zone and H II region properties: \[S III\]/\[S II\], \[O III\]/\[O II\], and the CO velocity dispersion appears to be driven by the presence of regions with high $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$, high $\sigma_{\mathrm{v,CO}}$ and low $U$. One potential explanation is the presence of low velocity shocks enhancing $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ (cite: Peimbert1991shocks; Binette2012_OIII_shocks; MendezDelgado2021HerbigHaro). To test this explanation, we search for evidence of shocks in enhanced optical line ratios and line broadening.

When shocks collide with and compress gas, the ionization parameter of the gas is reduced leading to partially ionized zones of enhanced nebular emission of low-ionization species such as S$^{+}$ and O relative to H$\beta$ and/or H$\alpha$ (cite: Dopita1996ApJS..102..161D; Allen2008ApJS..178...20A). In Figure [18](#fig:te_shocks), we show the \[S II\]/H$\alpha$ vs. \[O I\]/H$\alpha$ ratios, color-coded by $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$, for regions with measured \[O III\]$\lambda4363$. We find that H II regions with hotter $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ tend to populate a region with enhanced \[S II\]/H$\alpha$ and \[O I\]/H$\alpha$ ratios which suggests that these regions may host a partially ionized zone due to shocks. Between the two line ratios, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ is better correlated with \[S II\]/H$\alpha$, p-value$=0.0004$, than \[O I\]/H$\alpha$, p-value$=0.0016$. We note here that it is possible that harder photons and X-rays produced by X-ray binaries also enhance \[S II\] and \[O I\] relative to the Balmer emission (cite: Abolmasov:2007; Grise:2008). Furthermore, X-rays would provide high energy photons able to boost \[O III\]$\lambda4363$. However, lacking the high spatial resolution X-ray imaging of these H II regions, exploration of X-ray contributions to \[O III\]$\lambda4363$ emission is beyond the scope of this paper.

Another tracer that may indicate presence of shocks is the He II $\lambda4686$/H$\beta$ ratio (cite: Allen2008ApJS..178...20A) though it is also sensitive to the shape of the Lyman continuum below 228 Å (cite: Garnett1991ApJ...373..458G; Guseva2000ApJ...531..776G; Allen2008ApJS..178...20A). Wolf-Rayet (WR) stars are capable of releasing photons able to produce He II $\lambda4686$. WR stars host stellar winds and can be a source of high energy photons, E$> 54$ eV, capable of doubly ionizing Helium. We measured the He II$\lambda4686$/H$\beta$ in H II regions with $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ detections and found that these regions exhibit an average He II $\lambda4686$/H$\beta = 4.1\pm1.6\%$. This value is within the expected range of He II $\lambda4686$/H$\beta$ values for H II regions with WR, 0.04%-7% (cite: Guseva2000ApJ...531..776G; Thuan2005ApJS..161..240T; Mayya2023MUSE), and 100 km s$^{-1}$ shocks, 4%-6% (cite: Allen2008ApJS..178...20A). We visually inspected the spectra of regions with measured $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ for the characteristic red/blue bump associated with the presence of WR stars. We found the blue bump in only 2 regions with measurable \[O III\]$\lambda4363$, both of which have $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ $< 10^4$ K. Nevertheless, the He II $\lambda4686$/H$\beta$ for the high $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ regions lends evidence that these regions may host shocks or undetected WR stars.

We also searched for kinematic signatures of shocks, but find no clear kinematic evidence. Shocks can imprint asymmetries and/or broad emission near the base of an emission line. We inspected the fit residuals of \[O III\]$\lambda5007$ in H II regions with measured $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ and found no evidence of line broadening due to shocks. Next, we inspected the measured line widths of \[O III\]$\lambda5007$ in these regions. We compared the line-spread-function corrected \[O III\]$\lambda5007$, as measured by MUSE, velocity dispersion, $\sigma_{v,\lambda5007}$ vs. the CO velocity dispersion, $\sigma_{v, \mathrm{CO}}$. The line-widths of the optical and CO emission for regions with high $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ are comparable to regions with low, or not detected $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$. Despite this, the absence of these features may only exclude the presence of high-velocity shocks.

If the regions do host low-velocity shocks, then their impact on the line width of the optical emission may be too small to be resolved given the MUSE resolution; $\sim 70$ km s$^{-1}$ at $\lambda=5007$ Å. The high velocity resolution, $2.5~\mathrm{km} \mathrm{s}^{-1}$ of the PHANGS-ALMA data, are more sensitive than MUSE to low-velocity shocks, and are the strongest evidence for their presence in the high $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ H II regions.

![](T_OIII_vs_shocks_ver3.pdf)

# Discussion

## Electron Density Inhomogeneities

Similar to the results of (cite: Delgado_Desire2023arXiv230513136M), described in Section [7.2](#results:density_inhomogeneities), we have found that the presence of electron density inhomogeneities may cause the temperatures measured from \[O II\] and \[S II\] to be biased hotter compared to those measured using the \[N II\] auroral lines.

The critical densities of the nebular lines of \[S II\]$\lambda\lambda6716,6731$ and more so \[O II\]$\lambda\lambda3726,3729$ are low enough that at densities $n_{\rm{e}} > 10^3\ \mathrm{cm}^{-3}$ the lines will undergo increased collisional de-excitation. In the presence of density inhomogoneities above this value, the low critical densities will reduce the emissivity of the nebular emission lines from \[S II\] and \[O II\]. Because of this, the nebular diagnostic lines of \[S II\] and \[O II\] will mainly describe gas component with $n_{\rm{e}} < 10^3\ \mathrm{cm}^{-3}$. This biases the \[S II\] and \[O II\] density diagnostic to return electron densities that are lower than the true average density of the H II region. Since the auroral line critical densities are far higher, this also makes the measured \[S II\] and \[O II\] temperatures appear to reflect hotter values.

This effect has been observed in many studies. Densities measured in Milky Way H II regions (the Orion Nebula, NGC 3604 and NGC 3576) using \[Cl III\], which is sensitive to greater densities than \[S II\], routinely show that the \[S II\] diagnostic returns lower values than \[Cl III\]. (cite: PoggeOrion; GarciaRojas2007ApJ...670..457G; Nunez2013hsa7ORION; Weilbacher2015_MUSE_ORION). Although densities derived from the \[S II\] doublet are commonly used in the literature due to their strengths and their insensitivity to dust extinction, the \[S II\]$\lambda6731/\lambda6716$ ratio is less sensitive to density than \[Cl III\], \[Ar IV\], and \[Fe III\] diagnostics when $n_{\rm{e}} > 10^3$ cm$^{-3}$ (cite: Delgado_Desire2023arXiv230513136M). If the equality $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$$\approx$$T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$$\approx$$T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ predicted by photoionization models is true, then the auroral-to-nebular line ratios would suggest a factor of 10 higher density than the \[S II\] doublet, but neither may well represent the true average density of the region.

Electron density variations may arise from shocks, turbulence, and pre-existing non-uniform structure in the ISM (cite: Hill1978HII_Shocks; Dopita1996ApJS..102..161D; Allen2008ApJS..178...20A). (cite: JinFractal2022) have extended photoionization modeling of ionized nebulae to more complex geometries. Starting with an initial clumpy ISM, ionizing photons will pass through diffuse regions more readily than denser clumps. The resulting photoionized region will exhibit fluctuations in density and irregular geometry as opposed to a uniform density and spherical morphology. The ionization parameter in the dense clumps will be relatively lower than other regions of the nebulae due to the increased density. At these locations, the emission of low-ionization species, including \[S II\] and \[O II\], will be enhanced compared to higher ionization species. Due to the higher critical densities of the auroral lines of these ions, the emissivity of the auroral lines will be greater than those of the nebular lines in the high-density portion the nebula. In this scenario, the nebular density diagnostics can return an average density that traces the low-density portion of the nebula. In doing so, the value of $n_{\rm{e}}$ returned by the nebular diagnostics may inaccurately describe the ionizing conditions of the high-density clumps where the auroral line emissivities are greater than the nebular lines, and overestimate \[S II\] temperatures.

Density inhomogeneities have been reported in studies of highly resolved local HII regions like Orion where the inhomogeneities can be spatially resolved (cite: Baldwin_Orion:1991; PoggeOrion; Weilbacher2015_MUSE_ORION; McLeod2016Orioin; ODell_Orion:2017). (cite: Weilbacher2015_MUSE_ORION) mapped the spatial variation of density in the Orion nebulae and found variations of density between 500 cm$^{-3}$ and in excess of 10,000 cm$^{-3}$. A maximum of 25,000 cm$^{-3}$ is measured using \[Cl III\] at the location of the ionization front in the “Orion S” area. Density inhomogeneities, associated with turbulence driven velocity fluctuations, have been invoked as one mechanism to generate surface brightness fluctuations within the Orion Nebula (cite: Kainulainen2017ORION).

The Orion Nebula is not particularly comparable to the H II regions studied here due to the difference in scales (i.e. Orion is more compact) and resolution. A subset of our H II regions, as shown in the comparison between the MUSE H II regions mask in Appendix [12](#appn:comparison_of_muse_and_kcwi_hii_regions), are unresolved clusters of individual regions. Measurements of density inhomogeneities using density diagnostics besides the nebular \[O II\] and \[S II\] doublets for extragalactic H II regions that more closely match our sample are rare and require deep, high $S/N$ spectra (cite: Delgado_Desire2023arXiv230513136M). One consequence of the lack of different diagnostics is that many studies will often assume a fixed density of $100$ cm$^{-3}$ when either \[S II\], or \[O II\], return a density in the low-density limit (cite: Kreckel2019ApJ...887...80K). Studies using mid-infrared observations have shown this latter assumption could be incorrect, as densities up to $1000~\mathrm{cm}^{-3}$ have been measured using the \[S III\]$\lambda 18.7/33.5\ \mu$m density diagnostic (cite: Rubin:2016), and indicate that density inhomogeneities are present in extra-galactic H II regions.

The consistency of auroral-to-nebular ratios with $n_{\rm{e}}\sim1000$ cm$^{-3}$ assuming $T_{\rm{e}}=$ $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ in Figure [11](#fig:ne_result), as well as the correlation between degree of inhomogeneities with H$\beta$ surface brightness observed for \[S II\], supports this picture that inhomogeneities must be considered when deriving temperatures from the \[O II\] and \[S II\]. As a result, we consider $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ a more reliable indicator of the low-ionization zone temperature due to its relative insensitivity to density.

## $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ as Accurate Tracers of HII Region Temperatures

Within the set of $T_{\rm{e}}$–$T_{\rm{e}}$ between the low and intermediate ionization zones, we observed that the comparisons between $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$–$T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$–$T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ largely agree with those from (cite: Zurita2021MNRAS.500.2359Z). However, similar to recent studies (cite: Berg2015ApJ...806...16B; Berg2020ApJ...893...96B; Zurita2021MNRAS.500.2359Z; Rogers:chaos:2021) and (cite: Rogers:chaos:2022), we observed that the $T_{\rm{e}}$–$T_{\rm{e}}$ trend between $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ exhibits the lowest scatter and agrees with many of the literature trends presented in Figure [9](#fig:temps_intermediate_gals). These results suggest $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ temperatures are optimal tracers of H II region temperatures, more so than $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$.

Judged from the Oxygen CEL and RL temperatures, the high ionization zone is expected to be most affected by temperature fluctuations due to its proximity to sources of feedback (cite: Delgado2023arXiv230511578M). To what degree the intermediate ionization zone temperatures are affected is unclear (cite: Delgado_Desire2023arXiv230513136M). In Figure [9](#fig:temps_intermediate_gals), we showed that our best-fit trend, including those from the literature, between $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ “generally” (within 2$\sigma$) follow trends predicted from the photoionization models with temperature fluctuations set to zero. This suggests that $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ may be minimally affected by temperature inhomogeneities. (cite: Diaz2022MNRAS_sulphur) provide additional arguments for the use of $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ over $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$, including: 1) the emission lines of \[S III\] have a lower exponential dependence on electron temperature and 2) because \[S III\] overlaps gas volumes containing both $\mathrm{O}^{2+}$ and $\mathrm{O}^{+}$ that $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ can be representative of the entire H II region.

We also showed that $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$) is stable around the zero line for across the range of molecular gas velocity dispersion and the low values of ionization parameter, traced by both \[O III\]/\[O II\] and \[S III\]/\[S II\], observed in this work. This result follows the observations of (cite: Berg2020ApJ...893...96B), whom find that agreement between these two temperature tracers become more uncertain in high ionization parameter, traced by \[O III\]/\[O II\], H II regions. Due to stable behavior of between $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ and $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ across the multiple H II region properties observed in this work, and following the suggestions of (cite: Berg2015ApJ...806...16B; Berg2020ApJ...893...96B) and (cite: Rogers:chaos:2021), we will compare “direct” metallicities derived prioritizing \[N II\] and \[S III\] temperatures to several calibrated methods (Rickards Vaught et al., in prep).

## The High-Ionization Zone Temperature Excess

Within the sample of H II regions with measured \[O III\]$\lambda4363$, there are a small number of H II regions with high $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$, enhanced velocity dispersion in the surrounding molecular gas, and low-ionization parameter. We investigated these H II regions for enhanced low-ionization species emission line ratios \[S II\]/H$\alpha$, \[O I\]/H$\alpha$ and the high-ionization ratio He II/H$\beta$. We found that the high $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ regions exhibited enhanced low-ionization line ratios suggestive of shock ionization (or possibly X-ray ionization). We also found that the He II/H$\beta$ ratios for these regions are within the range of those expected from shock velocities $<100$ km s$^{-1}$ (cite: Allen2008ApJS..178...20A) and/or WR stars (cite: Guseva2000ApJ...531..776G; Thuan2005ApJS..161..240T; Mayya2023MUSE), though we only find characteristic red/blue bumps associated with the presence of WR stars, in 2 H II regions neither of which had elevated $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$. Absent the WR signatures, we are motivated to explore shocks as enhancers of the \[O III\] temperature.

We did not find any kinematic signatures of shocks in the optical emission line profiles. We determine that if shocks are present and broadening the CO emission, then the shock velocities are too low to be resolved by the MUSE spectral resolution. Either way, high-velocity shocks are not expected to effectively boost $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ (cite: MendezDelgado2021HerbigHaro). Despite the uncertainty in whether shocks are present in the high \[O III\] temperature regions, we can discuss the plausibility that low-velocity shocks are the cause for excess $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$.

### Shock-enhanced \[O III\] Temperature

Low velocity, $<$ 100 km s$^{-1}$, shocks can increase \[O III\]$\lambda4363$ while leaving \[O III\]$\lambda5007$ unchanged (cite: Peimbert1991shocks; Binette2012_OIII_shocks; MendezDelgado2021HerbigHaro). For a sample of giant H II regions, (cite: Binette2012_OIII_shocks) measured $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ up to 6000 K higher than $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ in regions with $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ $< 10^4$ K. To explore if shocks were boosting their \[O III\] temperatures relative to \[S III\], they model outward expanding shocks, mimicking those generated by stellar winds, by combining shock$+$photoionization models, with increasing shock velocities (analogous to increasing the post-shock temperature from 1.6$\times 10^4$ K to 7.2$\times 10^4$ K) between 20 and 60 km s$^{-1}$. Additionally, the models span 5 different metallicities between Z$=$0.01 Z$_{\odot}$ to Z$=$1.6 Z$_{\odot}$. Comparing the average properties of between the lowest and highest shock velocity models, (cite: Binette2012_OIII_shocks) found that mean doubly ionized fraction of oxygen, $\mathrm{O}^{2+}$/$\mathrm{O}$ , decreases while at the same time leaving the doubly ionized fraction of sulfur, $\mathrm{S}^{2+}$/$\mathrm{S}$, unchanged. The imbalance of the ionization fraction between oxygen and sulfur means that hotter, post-shock gas contributes proportionally more to the observed \[O III\] emission than \[S III\]. Because of the exponential sensitivity to temperature, the \[O III\] auroral line will be enhanced, tracing the hotter post-shock temperature rather than the local photoionized nebula temperature returned by $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$. Furthermore, the highest metallicity models show the largest temperature differences between $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ and $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$, up to $\sim 7000$ K. Although this difference is 3000 K lower than our largest measured $\Delta$($T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$), a complete understanding of the degree of enhancement of \[O III\]$\lambda4363$ with shocks require more complex 3D hydro-dynamical simulations (cite: Binette2012_OIII_shocks). Despite this, one extreme example of shock impact on electron temperatures was observed in the outflow of the H II region Sh 2-129 (cite: Corradi2014Shocks_outflows). This outflow, with velocity $\approx 100$ $\mathrm{km} \mathrm{s}^{-1}$, exhibits $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ $= 55,000$ K and $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ $\sim 20,000$ K. Much larger than $\Delta T_{\rm{e}}$ observed in this study.

It has also been shown that shocks driven by pressure–radiation H II region expansion, and SNR, impact the surrounding cold molecular and ionized gas. If the velocity of the expansion is greater than the sound speed ionized gas $\sim 10$ km s$^{-1}$, a layer of shocked H gas will form in-between the expanding ionization front and a surrounding molecular gas (cite: Hill1978HII_Shocks; Kothes:2002; Tremblin:2014; Watkins2023CO_bubbles). The impact of shock interaction with molecular gas has been studied in 18 galaxies observed as part of PHANGS-ALMA (cite: 2021Leroy_sample; 2021Leroy_data), where (cite: Watkins2023CO_bubbles) identified hundreds of super bubbles (i.e. pockets of expanding gas arising as byproducts of feedback). The superbubbles were identified using spatial correspondence between CO shells and stellar populations contained in PHANGS-HST catalogs (cite: 2022PHANGS_HST; ThilkerCompactClusters; Larson2023). Due to the ALMA spatial resolution (50–150 pc), (cite: Watkins2023CO_bubbles) measured the expansion velocity only for the largest superbubbles. Assuming the CO expansion velocity is equal to the shock velocity, (cite: Watkins2023CO_bubbles) measure the velocity of the approaching/receding CO shells and determine an average, line-of-sight, expansion velocity of $v_{\rm exp}=$9.8 $\pm$ 4.3 km s$^{-1}$. Although this value is similar to the sound speed of the ionized gas, superbubbles exhibit asymmetries in their morphology, and the velocity can potentially reach up to a few tens of km s$^{-1}$ depending on the conditions of the gas, source or energy injection, and age (cite: Watkins2023CO_bubbles). 1D models indicate that, at minimum, H II regions exhibit expansion speeds of a $\sim$few km s$^{-1}$ (cite: Tremblin:2014). This suggests that H II regions expand with a large range of velocities.

As for ionized gas, (cite: Egorov2023) identify in the PHANGS-MUSE galaxies more than 1400 regions of ionized gas with elevated intrinsic H$\alpha$ velocity dispersions $> 45$ km s$^{-1}$, and, under the assumption that these regions are undergoing expansion, (cite: Egorov2023) infer expansion velocities between $v_{\rm{ exp}}=$ 10–40 km s$^{-1}$ (cite: Egorov:2014; Egorov:2017; Cosens2022ApJ...929...74C). The ubiquity of H II region expansion, as well as their effects on the surrounding molecular gas, make them good candidates for drivers of low-velocity shocks capable of boosting \[O III\] temperatures.

### Temperature Inhomogeneities

Temperature fluctuations within H II regions are another potential explanation for the high \[O III\] temperature. As discussed in Section [1](#sec:intro), RL emissivities have a linear sensitivity to temperature rather than the exponential sensitivity of CELs. In the presence of temperature fluctuations CELs will return higher estimates of temperature. (cite: Delgado2023arXiv230511578M) have recently shown that differences between \[O III\] and \[N II\] temperatures are strongly correlated with the temperature fluctuations parameter, $t^2$, of the highly ionized gas. This suggests that $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ is likely to overestimate the representative H II region temperature. The observed excess in $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ are likely to be produced by phenomena other than those commonly observed in H II regions. Simple models from (cite: Binette2012_OIII_shocks) and the observations from (cite: Delgado2023arXiv230511578M) show that the effect from $t^2>0$ is more pronounced in lower-metallicity/high ionization parameter regions. Furthermore, the temperature excess $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ relative to the other ionization zones is too large in our observations to be caused solely by inhomogeneities. Using our measured $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$), we can infer from (cite: Delgado2023arXiv230511578M) that $t^2 > 0.2$ for $\Delta$($T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$, $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$) $>5000$ K. These values are much higher than what has been observed for nearby H II regions (cite: PPP2012_t2; Binette2012_OIII_shocks; Delgado2023arXiv230511578M). Even in the presence of classical temperature inhomogeneities, a secondary effect would also need to be included to explain our \[O III\] temperatures.

### Potential Observation Bias

Another possibility is that the high \[O III\] temperatures are statistical outliers. The galaxies in our sample exhibit strong line oxygen abundances $\gtrsim$ 8.3 (cite: Kreckel2019ApJ...887...80K). Because electron temperature is anti-correlated to the metallicity of the gas, the \[O III\]$\lambda4363$ temperatures for these galaxies are expected to be low. For \[O III\]$\lambda4363$ to be detectable, the temperature would need to be high, otherwise, we would likely not detect the auroral line. \[O III\] temperatures from a lower-metallicity sample may be compatible with photoionization models and $T_{\rm{e}}$–$T_{\rm{e}}$ relations. Finally, (cite: Rola1994A&A_SN) have shown that emission line measurements with S/N $< 5$ can potentially overestimate the true intensity by $80\%$. The average S/N \[O III\]$\lambda4363$ measured from our sample is $\sim 4.5$. Nevertheless, why we would measure high \[O III\]$\lambda4363$, even after removal of \[Fe II\]$\lambda4360$ contamination, that also exhibit enhanced molecular gas velocity dispersions is difficult to explain purely with statistical outliers.

# Conclusions

We presented combined KCWI and MUSE observations of the \[N II\]$\lambda5756$, \[O II\]$\lambda\lambda7320,7330$, \[S II\]$\lambda\lambda4069,4076$, \[O III\]$\lambda4363$, and \[S III\]$\lambda6312$ auroral lines in a sample of 421 H II regions in 7 nearby galaxies. We compared the derived electron temperatures and temperature differences between multiple H II region ionization zones to several H II region properties such as electron density, ionization parameter, molecular gas velocity dispersion, stellar mass, and age obtained from PHANGS observations. We found that:

- Similar to the results from (cite: Delgado_Desire2023arXiv230513136M), temperatures obtained from \[S II\] and \[O II\] are consistent with being overestimated due to the presence of density inhomogeneities in the H II regions. Because of these potential biases, we recommend the use \[N II\] temperatures to trace the low ionization zone.

- In addition to previous studies: (cite: Berg2015ApJ...806...16B; Berg2020ApJ...893...96B; Rogers:chaos:2021), and (cite: Zurita2021MNRAS.500.2359Z), we found that the \[N II\] and \[S III\] temperatures exhibited the lowest scatter of the $T_{\rm{e}}$– $T_{\rm{e}}$ relations and follow trends predicted from photoionization models. The well-behaved relationship between \[N II\] and \[S III\], even in potentially inhomogeneous conditions, may be better tracing the underlying H II region temperatures. This result, and those from the above studies, further stress the prioritization of \[N II\] and \[S III\] temperatures for metallicity determinations.

- We observed a subset of H II regions with high \[O III\] temperatures that do not agree with the cooler temperatures measured in the low and intermediate ionization zones. We found that the regions with high \[O III\] temperature tended to have enhanced molecular gas velocity dispersion and lower ionization parameter than those regions with \[O III\] temperatures that were in better agreement with other ionization zones. These regions also showed enhanced \[S II\]/H$\alpha$, \[O I\]/H$\alpha$, and He II/H$\beta$ ratios indicating the presence of secondary ionization sources (e.g. shocks, Wolf-Rayet and X-ray binary stars). Absent direct detection of shocks, we explored whether or not shocks are able to both enhance $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ and CO velocity dispersion. We found that low-velocity shocks are a plausible explanation for the observed \[O III\] temperatures and CO velocity dispersions. However, disentangling the effects of shocks from possible contributions to \[O III\] temperatures by harder ionization sources such as Wolf-Rayet stars or X-ray binaries require further investigation.

- We also explored temperature inhomogenities and observational uncertainties as causes for high \[O III\] temperatures measured for a small sub-sample of H II regions. We found that the degree of temperature inhomogeneity that would be required to produce the difference between high \[O III\] temperatures and those of the low and intermediate ionization zone are larger than what has been observed in most star-forming regions. Furthermore, if the regions with high \[O III\] temperatures are statistical outliers leading to overestimated temperatures, we lack an explanation as to why these temperatures would correlate with high molecular gas velocity dispersion.

In a follow-up paper, Rickards Vaught et al. (in prep), We will test temperature recommendations for measuring “direct" metallicities using our full set of measured auroral line temperatures. This work, along with the PHANGS-MUSE survey, demonstrate the power of integral field spectrographs on 10m class telescopes for measuring faint auroral emission lines from large samples of H II regions in nearby galaxies. Future efforts with deeper observations or expanded samples will be critical for further elucidating the temperature and ionization behavior of these regions, particularly as \[O III\]$\lambda4363$ and other faint lines are now being routinely detected in galaxies at high redshift with JWST and used in metallicity determinations.

# Acknowledgements

The authors thank the referee for a very thorough report which significantly improved the analysis presented here. The data presented herein were obtained at the W. M. Keck Observatory, which is operated as a scientific partnership among the California Institute of Technology, the University of California and the National Aeronautics and Space Administration. The Observatory was made possible by the generous financial support of the W. M. Keck Foundation. The authors wish to recognize and acknowledge the very significant cultural role and reverence that the summit of Maunakea has always had within the indigenous Hawaiian community. We are most fortunate to have the opportunity to conduct observations from this mountain. We also wish to thank all the Keck Observatory staff, including Gregg Doppman, Luca Rizzi, Sheery Yeh, and Rosalie McGurk for observational support.

This research is also based on observations collected at the European Southern Observatory under ESO programmes 094.C-0623 (PI: Kreckel), 095.C-0473, 098.C-0484 (PI: Blanc), 1100.B-0651 (PHANGS-MUSE; PI: Schinnerer), as well as 094.B-0321 (MAGNUM; PI: Marconi), 099.B-0242, 0100.B-0116, 098.B-0551 (MAD; PI: Carollo) and 097.B-0640 (TIMER; PI: Gadotti).

RRV and KS acknowledge funding support from National Science Foundation Award No. 1816462. FB acknowledges funding from the INAF Fundamental Astrophysics 2022 program. RRV wishes to thank Jonah Gannon, and Maren Consens for fruitful discussions on reducing the KCWI data. RRV would also like to acknowledge discussions with JEM-D, KK, OVE which greatly improved the manuscript. KK, JEM-D and OVE gratefully acknowledge funding from the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) in the form of an Emmy Noether Research Group (grant number KR4598/2-1, PI Kreckel). KG is supported by the Australian Research Council through the Discovery Early Career Researcher Award (DECRA) Fellowship (project number DE220100766) funded by the Australian Government. KG is supported by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. JN acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343). RSK acknowledges funding from the European Research Council via the ERC Synergy Grant “ECOGAL” (project ID 855130), from the German Excellence Strategy via the Heidelberg Cluster of Excellence (EXC 2181 - 390900948) “STRUCTURES”, and from the German Ministry for Economic Affairs and Climate Action in project “MAINN” (funding ID 50OO2206). He also thanks for computing resources provided by *The Länd* and DFG through grant INST 35/1134-1 FUGG and for data storage at SDS@hd through grant INST 35/1314-1 FUGG. G.A.B. acknowledges the support from the ANID Basal project FB210003.

This research made use of Montage. It is funded by the National Science Foundation under Grant Number ACI-1440620, and was previously funded by the National Aeronautics and Space Administration’s Earth Science Technology Office, Computation Technologies Project, under Cooperative Agreement Number NCC5-626 between NASA and the California Institute of Technology. This research has made use of NASA’s Astrophysics Data System. This research made use of Astropy, a community-developed core Python package for Astronomy (cite: Astropy), as well as substantial use of the nebular diagnostics toolkit Pyneb (cite: Luridiana2015A&A...573A..42L).

The distances in Table [\[tab:sample_properties\]](#tab:sample_properties) were compiled by (cite: Anand2021MNRAS.501.3621A) and are based on (cite: Freedman:2001); (cite: Nugent:2006); (cite: Jacobs:2009); (cite: Kourkchi:2017); (cite: Shaya:2017); (cite: Kourkchi:2020); (cite: Anand2021MNRAS.501.3621A); (cite: Scheuermann:2022)

natexlab

(ref: SDSS2003AJ....126.2081A) Abazajian, K., Adelman-McCarthy, J. K., Agüeros, M. A., et al. 2003, AJ, 126, 2081, doi: [`10.1086/378165`](http://doi.org/10.1086/378165)

(ref: Abolmasov:2007) Abolmasov, P., Fabrika, S., Sholukhova, O., & Afanasiev, V. 2007, Astrophysical Bulletin, 62, 36, doi: [`10.1134/S199034130701004X`](http://doi.org/10.1134/S199034130701004X)

(ref: Allen2008ApJS..178...20A) Allen, M. G., Groves, B. A., Dopita, M. A., Sutherland, R. S., & Kewley, L. J. 2008, ApJS, 178, 20, doi: [`10.1086/589652`](http://doi.org/10.1086/589652)

(ref: Anand2021MNRAS.501.3621A) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2021, MNRAS, 501, 3621, doi: [`10.1093/mnras/staa3668`](http://doi.org/10.1093/mnras/staa3668)

(ref: Arellano2020) Arellano-Córdova, K. Z., & Rodrı́guez, M. 2020, MNRAS, 497, 672, doi: [`10.1093/mnras/staa1759`](http://doi.org/10.1093/mnras/staa1759)

(ref: Astropy) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: MUSE_INST:2010) Bacon, R., Accardo, M., Adjali, L., et al. 2010, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7735, Ground-based and Airborne Instrumentation for Astronomy III, ed. I. S. McLean, S. K. Ramsay, & H. Takami, 773508, doi: [`10.1117/12.856027`](http://doi.org/10.1117/12.856027)

(ref: Baldwin_Orion:1991) Baldwin, J. A., Ferland, G. J., Martin, P. G., et al. 1991, ApJ, 374, 580, doi: [`10.1086/170146`](http://doi.org/10.1086/170146)

(ref: BPT1981PASP...93....5B) Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5, doi: [`10.1086/130766`](http://doi.org/10.1086/130766)

(ref: Belfiore2019_efit) Belfiore, F., Westfall, K. B., Schaefer, A., et al. 2019, AJ, 158, 160, doi: [`10.3847/1538-3881/ab3e4e`](http://doi.org/10.3847/1538-3881/ab3e4e)

(ref: Belfiore2022_DIG) Belfiore, F., Santoro, F., Groves, B., et al. 2022, A&A, 659, A26, doi: [`10.1051/0004-6361/202141859`](http://doi.org/10.1051/0004-6361/202141859)

(ref: Berg2020ApJ...893...96B) Berg, D. A., Pogge, R. W., Skillman, E. D., et al. 2020, ApJ, 893, 96, doi: [`10.3847/1538-4357/ab7eab`](http://doi.org/10.3847/1538-4357/ab7eab)

(ref: Berg2015ApJ...806...16B) Berg, D. A., Skillman, E. D., Croxall, K. V., et al. 2015, ApJ, 806, 16, doi: [`10.1088/0004-637X/806/1/16`](http://doi.org/10.1088/0004-637X/806/1/16)

(ref: Binette2012_OIII_shocks) Binette, L., Matadamas, R., Hägele, G. F., et al. 2012, A&A, 547, A29, doi: [`10.1051/0004-6361/201219515`](http://doi.org/10.1051/0004-6361/201219515)

(ref: Blanc:2015) Blanc, G. A., Kewley, L., Vogt, F. P. A., & Dopita, M. A. 2015, ApJ, 798, 99, doi: [`10.1088/0004-637X/798/2/99`](http://doi.org/10.1088/0004-637X/798/2/99)

(ref: Bresolin2012ApJ...750..122B) Bresolin, F., Kennicutt, R. C., & Ryan-Weber, E. 2012, ApJ, 750, 122, doi: [`10.1088/0004-637X/750/2/122`](http://doi.org/10.1088/0004-637X/750/2/122)

(ref: LEGUS:2015) Calzetti, D., Lee, J. C., Sabbi, E., et al. 2015, AJ, 149, 51, doi: [`10.1088/0004-6256/149/2/51`](http://doi.org/10.1088/0004-6256/149/2/51)

(ref: cambell:1986) Campbell, A., Terlevich, R., & Melnick, J. 1986, MNRAS, 223, 811, doi: [`10.1093/mnras/223.4.811`](http://doi.org/10.1093/mnras/223.4.811)

(ref: Cappellari2017MNRAS.466..798C) Cappellari, M. 2017, MNRAS, 466, 798, doi: [`10.1093/mnras/stw3020`](http://doi.org/10.1093/mnras/stw3020)

(ref: Cappellari2004) Cappellari, M., & Emsellem, E. 2004, PASP, 116, 138, doi: [`10.1086/381875`](http://doi.org/10.1086/381875)

(ref: slit_limiting) Casini, R., & de Wijn, A. G. 2014, Journal of the Optical Society of America A, 31, 2002, doi: [`10.1364/JOSAA.31.002002`](http://doi.org/10.1364/JOSAA.31.002002)

(ref: Congiu:2023) Congiu, E., Blanc, G. A., Belfiore, F., et al. 2023, A&A, 672, A148, doi: [`10.1051/0004-6361/202245153`](http://doi.org/10.1051/0004-6361/202245153)

(ref: Corradi2014Shocks_outflows) Corradi, R. L. M., Grosso, N., Acker, A., Greimel, R., & Guillout, P. 2014, A&A, 570, A105, doi: [`10.1051/0004-6361/201322718`](http://doi.org/10.1051/0004-6361/201322718)

(ref: Cosens2022ApJ...929...74C) Cosens, M., Wright, S. A., Murray, N., et al. 2022, ApJ, 929, 74, doi: [`10.3847/1538-4357/ac52f3`](http://doi.org/10.3847/1538-4357/ac52f3)

(ref: Curti2017MNRAS.465.1384C) Curti, M., Cresci, G., Mannucci, F., et al. 2017, MNRAS, 465, 1384, doi: [`10.1093/mnras/stw2766`](http://doi.org/10.1093/mnras/stw2766)

(ref: DaSilva:2012) da Silva, R. L., Fumagalli, M., & Krumholz, M. 2012, ApJ, 745, 145, doi: [`10.1088/0004-637X/745/2/145`](http://doi.org/10.1088/0004-637X/745/2/145)

(ref: Diaz2022MNRAS_sulphur) Dı́az, Á. I., & Zamora, S. 2022, MNRAS, 511, 4377, doi: [`10.1093/mnras/stac387`](http://doi.org/10.1093/mnras/stac387)

(ref: Dopita1996ApJS..102..161D) Dopita, M. A., & Sutherland, R. S. 1996, ApJS, 102, 161, doi: [`10.1086/192255`](http://doi.org/10.1086/192255)

(ref: Dors2011MNRAS.415.3616D) Dors, O. L., J., Krabbe, A., Hägele, G. F., & Pérez-Montero, E. 2011, MNRAS, 415, 3616, doi: [`10.1111/j.1365-2966.2011.18978.x`](http://doi.org/10.1111/j.1365-2966.2011.18978.x)

(ref: Draine2011piim.book.....D) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium

(ref: Egorov:2017) Egorov, O. V., Lozinskaya, T. A., Moiseev, A. V., & Shchekinov, Y. A. 2017, MNRAS, 464, 1833, doi: [`10.1093/mnras/stw2367`](http://doi.org/10.1093/mnras/stw2367)

(ref: Egorov:2014) Egorov, O. V., Lozinskaya, T. A., Moiseev, A. V., & Smirnov-Pinchukov, G. V. 2014, MNRAS, 444, 376, doi: [`10.1093/mnras/stu1369`](http://doi.org/10.1093/mnras/stu1369)

(ref: Egorov2023) Egorov, O. V., Kreckel, K., Glover, S. C. O., et al. 2023, arXiv e-prints, arXiv:2307.10277, doi: [`10.48550/arXiv.2307.10277`](http://doi.org/10.48550/arXiv.2307.10277)

(ref: EmsellemMuse) Emsellem, E., Schinnerer, E., Santoro, F., et al. 2022, A&A, 659, A191, doi: [`10.1051/0004-6361/202141727`](http://doi.org/10.1051/0004-6361/202141727)

(ref: Esteban2004MNRAS.355..229E) Esteban, C., Peimbert, M., Garcı́a-Rojas, J., et al. 2004, MNRAS, 355, 229, doi: [`10.1111/j.1365-2966.2004.08313.x`](http://doi.org/10.1111/j.1365-2966.2004.08313.x)

(ref: Fitzpatrick1999PASP..111...63F) Fitzpatrick, E. L. 1999, PASP, 111, 63, doi: [`10.1086/316293`](http://doi.org/10.1086/316293)

(ref: Freedman:2001) Freedman, W. L., Madore, B. F., Gibson, B. K., et al. 2001, ApJ, 553, 47, doi: [`10.1086/320638`](http://doi.org/10.1086/320638)

(ref: Froese2004) Froese Fischer, C., & Tachiev, G. 2004, Atomic Data and Nuclear Data Tables, 87, 1, doi: [`10.1016/j.adt.2004.02.001`](http://doi.org/10.1016/j.adt.2004.02.001)

(ref: FFCRecomData) Froese Fischer, C., Tachiev, G., & Irimia, A. 2006, Atomic Data and Nuclear Data Tables, 92, 607, doi: [`10.1016/j.adt.2006.03.001`](http://doi.org/10.1016/j.adt.2006.03.001)

(ref: GarciaRojas2007ApJ...670..457G) Garcı́a-Rojas, J., & Esteban, C. 2007, ApJ, 670, 457, doi: [`10.1086/521871`](http://doi.org/10.1086/521871)

(ref: Garnett1992AJ) Garnett, D. R. 1992, AJ, 103, 1330, doi: [`10.1086/116146`](http://doi.org/10.1086/116146)

(ref: Garnett1991ApJ...373..458G) Garnett, D. R., Kennicutt, Robert C., J., Chu, Y.-H., & Skillman, E. D. 1991, ApJ, 373, 458, doi: [`10.1086/170065`](http://doi.org/10.1086/170065)

(ref: Grasha2019MNRAS.483.4707G) Grasha, K., Calzetti, D., Adamo, A., et al. 2019, MNRAS, 483, 4707, doi: [`10.1093/mnras/sty3424`](http://doi.org/10.1093/mnras/sty3424)

(ref: Grasha:2022) Grasha, K., Chen, Q. H., Battisti, A. J., et al. 2022, ApJ, 929, 118, doi: [`10.3847/1538-4357/ac5ab2`](http://doi.org/10.3847/1538-4357/ac5ab2)

(ref: Grise:2008) Grisé, F., Pakull, M. W., Soria, R., et al. 2008, A&A, 486, 151, doi: [`10.1051/0004-6361:200809557`](http://doi.org/10.1051/0004-6361:200809557)

(ref: Groves2023NebCat) Groves, B., Kreckel, K., Santoro, F., et al. 2023, MNRAS, 520, 4902, doi: [`10.1093/mnras/stad114`](http://doi.org/10.1093/mnras/stad114)

(ref: Guseva2000ApJ...531..776G) Guseva, N. G., Izotov, Y. I., & Thuan, T. X. 2000, ApJ, 531, 776, doi: [`10.1086/308489`](http://doi.org/10.1086/308489)

(ref: Hernandez2013ApJ...777...19H) Hernandez, A. K., Wakker, B. P., Benjamin, R. A., et al. 2013, ApJ, 777, 19, doi: [`10.1088/0004-637X/777/1/19`](http://doi.org/10.1088/0004-637X/777/1/19)

(ref: Hill1978HII_Shocks) Hill, J. K., & Hollenbach, D. J. 1978, ApJ, 225, 390, doi: [`10.1086/156501`](http://doi.org/10.1086/156501)

(ref: Ho2016) Ho, I. T., Medling, A. M., Groves, B., et al. 2016, Ap&SS, 361, 280, doi: [`10.1007/s10509-016-2865-2`](http://doi.org/10.1007/s10509-016-2865-2)

(ref: Ho2017ApJ...846...39H) Ho, I. T., Seibert, M., Meidt, S. E., et al. 2017, ApJ, 846, 39, doi: [`10.3847/1538-4357/aa8460`](http://doi.org/10.3847/1538-4357/aa8460)

(ref: Jacobs:2009) Jacobs, B. A., Rizzi, L., Tully, R. B., et al. 2009, AJ, 138, 332, doi: [`10.1088/0004-6256/138/2/332`](http://doi.org/10.1088/0004-6256/138/2/332)

(ref: JinFractal2022) Jin, Y., Kewley, L. J., & Sutherland, R. S. 2022, ApJL, 934, L8, doi: [`10.3847/2041-8213/ac80f3`](http://doi.org/10.3847/2041-8213/ac80f3)

(ref: Kainulainen2017ORION) Kainulainen, J., Stutz, A. M., Stanke, T., et al. 2017, A&A, 600, A141, doi: [`10.1051/0004-6361/201628481`](http://doi.org/10.1051/0004-6361/201628481)

(ref: 1976ApJS...31..163K) Kaler, J. B., Aller, L. H., Czyzak, S. J., & Epps, H. W. 1976, ApJS, 31, 163, doi: [`10.1086/190379`](http://doi.org/10.1086/190379)

(ref: KauffmanBPT) Kauffmann, G., Heckman, T. M., Tremonti, C., et al. 2003, MNRAS, 346, 1055, doi: [`10.1111/j.1365-2966.2003.07154.x`](http://doi.org/10.1111/j.1365-2966.2003.07154.x)

(ref: Kelly:2007:linmix) Kelly, B. C. 2007, ApJ, 665, 1489, doi: [`10.1086/519947`](http://doi.org/10.1086/519947)

(ref: Kennicutt1984ApJ...287..116K) Kennicutt, R. C., J. 1984, ApJ, 287, 116, doi: [`10.1086/162669`](http://doi.org/10.1086/162669)

(ref: Kennicutt2003ApJ...591..801K) Kennicutt, Robert C., J., Bresolin, F., & Garnett, D. R. 2003, ApJ, 591, 801, doi: [`10.1086/375398`](http://doi.org/10.1086/375398)

(ref: Kennicutt1996) Kennicutt, Robert C., J., & Garnett, D. R. 1996, ApJ, 456, 504, doi: [`10.1086/176675`](http://doi.org/10.1086/176675)

(ref: Kewley:2002) Kewley, L. J., & Dopita, M. A. 2002, ApJS, 142, 35, doi: [`10.1086/341326`](http://doi.org/10.1086/341326)

(ref: 2008ApJ...681.1183K) Kewley, L. J., & Ellison, S. L. 2008, ApJ, 681, 1183, doi: [`10.1086/587500`](http://doi.org/10.1086/587500)

(ref: Kewley2001ApJS..132...37K) Kewley, L. J., Heisler, C. A., Dopita, M. A., & Lumsden, S. 2001, ApJS, 132, 37, doi: [`10.1086/318944`](http://doi.org/10.1086/318944)

(ref: Kisielius2009) Kisielius, R., Storey, P. J., Ferland, G. J., & Keenan, F. P. 2009, MNRAS, 397, 903, doi: [`10.1111/j.1365-2966.2009.14989.x`](http://doi.org/10.1111/j.1365-2966.2009.14989.x)

(ref: Koo:2001_SN_CO) Koo, B.-C., Rho, J., Reach, W. T., Jung, J., & Mangum, J. G. 2001, ApJ, 552, 175, doi: [`10.1086/320442`](http://doi.org/10.1086/320442)

(ref: Kothes:2002) Kothes, R., & Kerton, C. R. 2002, A&A, 390, 337, doi: [`10.1051/0004-6361:20020671`](http://doi.org/10.1051/0004-6361:20020671)

(ref: Kourkchi:2020) Kourkchi, E., Courtois, H. M., Graziani, R., et al. 2020, AJ, 159, 67, doi: [`10.3847/1538-3881/ab620e`](http://doi.org/10.3847/1538-3881/ab620e)

(ref: Kourkchi:2017) Kourkchi, E., & Tully, R. B. 2017, ApJ, 843, 16, doi: [`10.3847/1538-4357/aa76db`](http://doi.org/10.3847/1538-4357/aa76db)

(ref: Kreckel2019ApJ...887...80K) Kreckel, K., Ho, I. T., Blanc, G. A., et al. 2019, ApJ, 887, 80, doi: [`10.3847/1538-4357/ab5115`](http://doi.org/10.3847/1538-4357/ab5115)

(ref: Kreckel2020MNRAS.499..193K) —. 2020, MNRAS, 499, 193, doi: [`10.1093/mnras/staa2743`](http://doi.org/10.1093/mnras/staa2743)

(ref: KreckelChargeExchange) Kreckel, K., Egorov, O. V., Belfiore, F., et al. 2022, A&A, 667, A16, doi: [`10.1051/0004-6361/202243858`](http://doi.org/10.1051/0004-6361/202243858)

(ref: Larson2023) Larson, K. L., Lee, J. C., Thilker, D. A., et al. 2023, MNRAS, 523, 6061, doi: [`10.1093/mnras/stad1600`](http://doi.org/10.1093/mnras/stad1600)

(ref: MangaDAP2016AJ....152...83L) Law, D. R., Cherinka, B., Yan, R., et al. 2016, AJ, 152, 83, doi: [`10.3847/0004-6256/152/4/83`](http://doi.org/10.3847/0004-6256/152/4/83)

(ref: 2022PHANGS_HST) Lee, J. C., Whitmore, B. C., Thilker, D. A., et al. 2022, ApJS, 258, 10, doi: [`10.3847/1538-4365/ac1fe5`](http://doi.org/10.3847/1538-4365/ac1fe5)

(ref: 2021Leroy_sample) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021a, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: 2021Leroy_data) Leroy, A. K., Hughes, A., Liu, D., et al. 2021b, ApJS, 255, 19, doi: [`10.3847/1538-4365/abec80`](http://doi.org/10.3847/1538-4365/abec80)

(ref: Luridiana2015A&A...573A..42L) Luridiana, V., Morisset, C., & Shaw, R. A. 2015, A&A, 573, A42, doi: [`10.1051/0004-6361/201323152`](http://doi.org/10.1051/0004-6361/201323152)

(ref: Makarov2014) Makarov, D., Prugniel, P., Terekhova, N., Courtois, H., & Vauglin, I. 2014, A&A, 570, A13, doi: [`10.1051/0004-6361/201423496`](http://doi.org/10.1051/0004-6361/201423496)

(ref: Mayya2023MUSE) Mayya, Y. D., Plat, A., Gómez-González, V. M. A., et al. 2023, MNRAS, 519, 5492, doi: [`10.1093/mnras/stad017`](http://doi.org/10.1093/mnras/stad017)

(ref: McLeod2016Orioin) McLeod, A. F., Weilbacher, P. M., Ginsburg, A., et al. 2016, MNRAS, 455, 4057, doi: [`10.1093/mnras/stv2617`](http://doi.org/10.1093/mnras/stv2617)

(ref: mendezdelgadoHH514) Méndez-Delgado, J. E., Esteban, C., Garcı́a-Rojas, J., & Henney, W. J. 2022, MNRAS, 514, 744, doi: [`10.1093/mnras/stac1300`](http://doi.org/10.1093/mnras/stac1300)

(ref: MendezDelgado2021HerbigHaro) Méndez-Delgado, J. E., Esteban, C., Garcı́a-Rojas, J., et al. 2021, MNRAS, 502, 1703, doi: [`10.1093/mnras/stab068`](http://doi.org/10.1093/mnras/stab068)

(ref: Delgado2023arXiv230511578M) Méndez-Delgado, J. E., Esteban, C., Garcı́a-Rojas, J., Kreckel, K., & Peimbert, M. 2023a, Nature, 618, 249, doi: [`10.1038/s41586-023-05956-2`](http://doi.org/10.1038/s41586-023-05956-2)

(ref: Delgado_Desire2023arXiv230513136M) Méndez-Delgado, J. E., Esteban, C., Garcı́a-Rojas, J., et al. 2023b, MNRAS, 523, 2952, doi: [`10.1093/mnras/stad1569`](http://doi.org/10.1093/mnras/stad1569)

(ref: Mendoza_atomic_comparisons) Mendoza, C., & Bautista, M. A. 2014, ApJ, 785, 91, doi: [`10.1088/0004-637X/785/2/91`](http://doi.org/10.1088/0004-637X/785/2/91)

(ref: Mendoza:2023) Mendoza, C., Méndez-Delgado, J. E., Bautista, M., Garcı́a-Rojas, J., & Morisset, C. 2023, Atoms, 11, 63, doi: [`10.3390/atoms11040063`](http://doi.org/10.3390/atoms11040063)

(ref: MexicanMillionModels) Morisset, C. 2009, Mem. Soc. Astron. Italiana, 80, 397, doi: [`10.48550/arXiv.0909.3313`](http://doi.org/10.48550/arXiv.0909.3313)

(ref: 2018ApJ...864...93M) Morrissey, P., Matuszewski, M., Martin, D. C., et al. 2018, ApJ, 864, 93, doi: [`10.3847/1538-4357/aad597`](http://doi.org/10.3847/1538-4357/aad597)

(ref: Nicholls2020PASP..132c3001N) Nicholls, D. C., Kewley, L. J., & Sutherland, R. S. 2020, PASP, 132, 033001, doi: [`10.1088/1538-3873/ab6818`](http://doi.org/10.1088/1538-3873/ab6818)

(ref: Nunez2013hsa7ORION) Núñez-Dı́az, M., Esteban, C., & Mesa-Delgado, A. 2013, in Highlights of Spanish Astrophysics VII, ed. J. C. Guirado, L. M. Lara, V. Quilis, & J. Gorgas, 594–599

(ref: Nugent:2006) Nugent, P., Sullivan, M., Ellis, R., et al. 2006, ApJ, 645, 841, doi: [`10.1086/504413`](http://doi.org/10.1086/504413)

(ref: ODell_Orion:2017) O’Dell, C. R., Ferland, G. J., & Peimbert, M. 2017, MNRAS, 464, 4835, doi: [`10.1093/mnras/stw2713`](http://doi.org/10.1093/mnras/stw2713)

(ref: ExtinctionCorr1994ApJ...422..158O) O’Donnell, J. E. 1994, ApJ, 422, 158, doi: [`10.1086/173713`](http://doi.org/10.1086/173713)

(ref: Oh2011_efit) Oh, K., Sarzi, M., Schawinski, K., & Yi, S. K. 2011, ApJS, 195, 13, doi: [`10.1088/0067-0049/195/2/13`](http://doi.org/10.1088/0067-0049/195/2/13)

(ref: Osterbrock:2006) Osterbrock, D. E., & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and active galactic nuclei

(ref: SDSS_mag_unc) Padmanabhan, N., Schlegel, D. J., Finkbeiner, D. P., et al. 2008, ApJ, 674, 1217, doi: [`10.1086/524677`](http://doi.org/10.1086/524677)

(ref: PPP2012_t2) Peña-Guerrero, M. A., Peimbert, A., & Peimbert, M. 2012, ApJL, 756, L14, doi: [`10.1088/2041-8205/756/1/L14`](http://doi.org/10.1088/2041-8205/756/1/L14)

(ref: Peimbert1967ApJ...150..825P) Peimbert, M. 1967, ApJ, 150, 825, doi: [`10.1086/149385`](http://doi.org/10.1086/149385)

(ref: Peimbert:1971) —. 1971, Boletin de los Observatorios Tonantzintla y Tacubaya, 6, 29

(ref: Peimbert:1969) Peimbert, M., & Costero, R. 1969, Boletin de los Observatorios Tonantzintla y Tacubaya, 5, 3

(ref: Piembert2017PASP..129h2001P) Peimbert, M., Peimbert, A., & Delgado-Inglada, G. 2017, PASP, 129, 082001, doi: [`10.1088/1538-3873/aa72c3`](http://doi.org/10.1088/1538-3873/aa72c3)

(ref: Peimbert1991shocks) Peimbert, M., Sarmiento, A., & Fierro, J. 1991, PASP, 103, 815, doi: [`10.1086/132886`](http://doi.org/10.1086/132886)

(ref: PoggeOrion) Pogge, R. W., Owen, J. M., & Atwood, B. 1992, ApJ, 399, 147, doi: [`10.1086/171910`](http://doi.org/10.1086/171910)

(ref: rodriguez1999) Rodrı́guez, M. 1999, A&A, 348, 222, doi: [`10.48550/arXiv.astro-ph/9906291`](http://doi.org/10.48550/arXiv.astro-ph/9906291)

(ref: Rogers:chaos:2022) Rogers, N. S. J., Skillman, E. D., Pogge, R. W., et al. 2022, ApJ, 939, 44, doi: [`10.3847/1538-4357/ac947d`](http://doi.org/10.3847/1538-4357/ac947d)

(ref: Rogers:chaos:2021) —. 2021, ApJ, 915, 21, doi: [`10.3847/1538-4357/abf8b9`](http://doi.org/10.3847/1538-4357/abf8b9)

(ref: Rola1994A&A_SN) Rola, C., & Pelat, D. 1994, A&A, 287, 676

(ref: Rubin:1989) Rubin, R. H. 1989, ApJS, 69, 897, doi: [`10.1086/191330`](http://doi.org/10.1086/191330)

(ref: Rubin:2016) Rubin, R. H., Simpson, J. P., Colgan, S. W. J., et al. 2016, MNRAS, 459, 1875, doi: [`10.1093/mnras/stw719`](http://doi.org/10.1093/mnras/stw719)

(ref: RGJ19) Rynkun, P., Gaigalas, G., & Jönsson, P. 2019, A&A, 623, A155, doi: [`10.1051/0004-6361/201834931`](http://doi.org/10.1051/0004-6361/201834931)

(ref: Santoro2022A&A...658A.188S) Santoro, F., Kreckel, K., Belfiore, F., et al. 2022, A&A, 658, A188, doi: [`10.1051/0004-6361/202141907`](http://doi.org/10.1051/0004-6361/202141907)

(ref: Sarzi2006_efit) Sarzi, M., Falcón-Barroso, J., Davies, R. L., et al. 2006, MNRAS, 366, 1151, doi: [`10.1111/j.1365-2966.2005.09839.x`](http://doi.org/10.1111/j.1365-2966.2005.09839.x)

(ref: Scheuermann:2022) Scheuermann, F., Kreckel, K., Anand, G. S., et al. 2022, MNRAS, 511, 6087, doi: [`10.1093/mnras/stac110`](http://doi.org/10.1093/mnras/stac110)

(ref: Scheuermann2023MNRAS.522.2369S) Scheuermann, F., Kreckel, K., Barnes, A. T., et al. 2023, MNRAS, 522, 2369, doi: [`10.1093/mnras/stad878`](http://doi.org/10.1093/mnras/stad878)

(ref: 1957ApJ...125...66S) Seaton, M. J., & Osterbrock, D. E. 1957, ApJ, 125, 66, doi: [`10.1086/146282`](http://doi.org/10.1086/146282)

(ref: Shaya:2017) Shaya, E. J., Tully, R. B., Hoffman, Y., & Pomarède, D. 2017, ApJ, 850, 207, doi: [`10.3847/1538-4357/aa9525`](http://doi.org/10.3847/1538-4357/aa9525)

(ref: stasinska:1980) Stasińska, G. 1980, A&A, 84, 320

(ref: Storey:1995) Storey, P. J., & Hummer, D. G. 1995, MNRAS, 272, 41, doi: [`10.1093/mnras/272.1.41`](http://doi.org/10.1093/mnras/272.1.41)

(ref: StoreyOIIIColl) Storey, P. J., Sochi, T., & Badnell, N. R. 2014, MNRAS, 441, 3028, doi: [`10.1093/mnras/stu777`](http://doi.org/10.1093/mnras/stu777)

(ref: Tayal2011) Tayal, S. S. 2011, ApJS, 195, 12, doi: [`10.1088/0067-0049/195/2/12`](http://doi.org/10.1088/0067-0049/195/2/12)

(ref: Tayal1999ApJ) Tayal, S. S., & Gupta, G. P. 1999, ApJ, 526, 544, doi: [`10.1086/307971`](http://doi.org/10.1086/307971)

(ref: TayalSIIIColl) Tayal, S. S., & Zatsarinny, O. 2010, ApJS, 188, 32, doi: [`10.1088/0067-0049/188/1/32`](http://doi.org/10.1088/0067-0049/188/1/32)

(ref: Taylor1997ieas.book.....T) Taylor, J. 1997, Introduction to Error Analysis, the Study of Uncertainties in Physical Measurements, 2nd Edition

(ref: Thilker2000AJ....120.3070T) Thilker, D. A., Braun, R., & Walterbos, R. A. M. 2000, AJ, 120, 3070, doi: [`10.1086/316852`](http://doi.org/10.1086/316852)

(ref: ThilkerCompactClusters) Thilker, D. A., Whitmore, B. C., Lee, J. C., et al. 2022, MNRAS, 509, 4094, doi: [`10.1093/mnras/stab3183`](http://doi.org/10.1093/mnras/stab3183)

(ref: Thuan2005ApJS..161..240T) Thuan, T. X., & Izotov, Y. I. 2005, ApJS, 161, 240, doi: [`10.1086/491657`](http://doi.org/10.1086/491657)

(ref: 2005PASP..117..421T) Tokunaga, A. T., & Vacca, W. D. 2005, PASP, 117, 421, doi: [`10.1086/429382`](http://doi.org/10.1086/429382)

(ref: Tremblin:2014) Tremblin, P., Anderson, L. D., Didelon, P., et al. 2014, A&A, 568, A4, doi: [`10.1051/0004-6361/201423959`](http://doi.org/10.1051/0004-6361/201423959)

(ref: BOND) Vale Asari, N., Stasińska, G., Morisset, C., & Cid Fernandes, R. 2016, MNRAS, 460, 1739, doi: [`10.1093/mnras/stw971`](http://doi.org/10.1093/mnras/stw971)

(ref: vanderMarel_gauss_hermite) van der Marel, R. P., & Franx, M. 1993, ApJ, 407, 525, doi: [`10.1086/172534`](http://doi.org/10.1086/172534)

(ref: vanDokkum_guass_hermite) van Dokkum, P., Wasserman, A., Danieli, S., et al. 2019, ApJ, 880, 91, doi: [`10.3847/1538-4357/ab2914`](http://doi.org/10.3847/1538-4357/ab2914)

(ref: vanloon2021MNRAS.tmp.1227V) van Loon, M. L., Mitchell, P. D., & Schaye, J. 2021, MNRAS, doi: [`10.1093/mnras/stab1254`](http://doi.org/10.1093/mnras/stab1254)

(ref: Vazdekis2016MNRAS.463.3409V) Vazdekis, A., Koleva, M., Ricciardelli, E., Röck, B., & Falcón-Barroso, J. 2016, MNRAS, 463, 3409, doi: [`10.1093/mnras/stw2231`](http://doi.org/10.1093/mnras/stw2231)

(ref: LZIFUMiles) Vazdekis, A., Sánchez-Blázquez, P., Falcón-Barroso, J., et al. 2010, MNRAS, 404, 1639, doi: [`10.1111/j.1365-2966.2010.16407.x`](http://doi.org/10.1111/j.1365-2966.2010.16407.x)

(ref: Vilchez:1988) Vilchez, J. M., & Pagel, B. E. J. 1988, MNRAS, 231, 257, doi: [`10.1093/mnras/231.2.257`](http://doi.org/10.1093/mnras/231.2.257)

(ref: Watkins2023CO_bubbles) Watkins, E. J., Kreckel, K., Groves, B., et al. 2023, A&A, 676, A67, doi: [`10.1051/0004-6361/202346075`](http://doi.org/10.1051/0004-6361/202346075)

(ref: Weilbacher2015_MUSE_ORION) Weilbacher, P. M., Monreal-Ibero, A., Kollatschny, W., et al. 2015, A&A, 582, A114, doi: [`10.1051/0004-6361/201526529`](http://doi.org/10.1051/0004-6361/201526529)

(ref: Wood_hii_region_morph1989ApJS...69..831W) Wood, D. O. S., & Churchwell, E. 1989, ApJS, 69, 831, doi: [`10.1086/191329`](http://doi.org/10.1086/191329)

(ref: Yates2020A&A...634A.107Y) Yates, R. M., Schady, P., Chen, T. W., Schweyer, T., & Wiseman, P. 2020, A&A, 634, A107, doi: [`10.1051/0004-6361/201936506`](http://doi.org/10.1051/0004-6361/201936506)

(ref: Zakardjian_GMC) Zakardjian, A., Pety, J., Herrera, C. N., et al. 2023, arXiv e-prints, arXiv:2305.03650, doi: [`10.48550/arXiv.2305.03650`](http://doi.org/10.48550/arXiv.2305.03650)

(ref: Zeippen1982) Zeippen, C. J. 1982, MNRAS, 198, 111, doi: [`10.1093/mnras/198.1.111`](http://doi.org/10.1093/mnras/198.1.111)

(ref: Zhang_starless_clumps2021A&A...646A..25Z) Zhang, S., Zavagno, A., López-Sepulcre, A., et al. 2021, A&A, 646, A25, doi: [`10.1051/0004-6361/202038421`](http://doi.org/10.1051/0004-6361/202038421)

(ref: Zhou:2023arXiv) Zhou, X., Su, Y., Yang, J., et al. 2023, arXiv e-prints, arXiv:2308.03484, doi: [`10.48550/arXiv.2308.03484`](http://doi.org/10.48550/arXiv.2308.03484)

(ref: Zurita2021MNRAS.500.2359Z) Zurita, A., Florido, E., Bresolin, F., Pérez-Montero, E., & Pérez, I. 2021, MNRAS, 500, 2359, doi: [`10.1093/mnras/staa2246`](http://doi.org/10.1093/mnras/staa2246)

# KCWI Seeing FWHM from Standard Star Observations and Table of Observations

We summarize the details of all of the KCWI observations and standard star observations in Table [\[tab:obs\]](#tab:obs) and [\[tab:std_obs\]](#tab:std_obs). Additionally, we describe below the measurement of seeing from the set of standard stars.

To measure seeing, we fit a 2D Gaussian to each standard star observation. We find an average FWHM of $\sim 1.2$$''$, however, at some points during the nights of 10-17-2018, 03-27-2019, and 03-28-2019 the seeing was poorer with values between 1.6$''$-2$''$. Aside from these portions of the nights, the seeing was stable near the average FWHM. The FWHM measurements for each standard star observation are summarized in Table [\[tab:std_obs\]](#tab:std_obs).

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Field$^{a}$ | RA | RA$_{\mathrm{corr}}$$^{b}$ | Dec | Dec$_{\mathrm{corr}}$$^{b}$ | Date | Exposure | Airmass | PA | FWHM$^{c}$ |
|  | ($^{\circ}$) | ($\ensuremath{''}$) | ($^{\circ}$) | ($\ensuremath{''}$) | (UTC) | \(s\) |  | ($^{\circ}$) | ($''$) |
| NGC0628F17 | 24.188826 | 0.16 | 15.771491 | -1.75 | 2018-10-17T07:00:46 | 1200.0 | 1.46 | 45.0 | 2.14 |
| NGC0628F17 | 24.189230 | -1.30 | 15.771380 | -1.35 | 2018-10-17T07:35:05 | 1200.0 | 1.28 | 45.0 | 1.79 |
| NGC0628F17 | 24.189230 | -1.30 | 15.771380 | -1.35 | 2018-10-17T07:56:17 | 1200.0 | 1.20 | 45.0 | 1.97 |
| NGC0628F18 | 24.189057 | -0.68 | 15.771546 | -1.95 | 2018-10-17T08:29:45 | 1200.0 | 1.11 | 45.0 | 2.49 |
| NGC0628F18 | 24.188941 | -0.26 | 15.771657 | -2.35 | 2018-10-17T08:51:03 | 1200.0 | 1.07 | 45.0 | 2.49 |
| NGC0628F22 | 24.189576 | -2.55 | 15.771268 | -0.95 | 2018-10-17T09:29:26 | 1200.0 | 1.02 | 45.0 | 2.20 |
| NGC0628F22 | 24.189461 | -2.13 | 15.771380 | -1.35 | 2018-10-17T09:50:42 | 1200.0 | 1.01 | 45.0 | 2.49 |
| NGC0628F23 | 24.189519 | -2.34 | 15.770380 | 2.25 | 2018-10-17T10:24:20 | 1200.0 | 1.00 | 45.0 | 1.49 |
| NGC0628F23 | 24.189634 | -2.75 | 15.770324 | 2.45 | 2018-10-17T10:45:51 | 1200.0 | 1.01 | 45.0 | 1.60 |
| NGC0628F04 | 24.190558 | -6.08 | 15.770213 | 2.85 | 2018-10-16T10:08:04 | 1200.0 | 1.00 | 45.0 | 2.48 |
| NGC1087F10 | 41.606106 | -1.05 | -0.494058 | -0.15 | 2018-10-17T11:23:24 | 1200.0 | 1.07 | 90.0 | 1.26 |
| NGC1087F10 | 41.606106 | -1.05 | -0.494058 | -0.15 | 2018-10-17T11:44:36 | 1200.0 | 1.07 | 90.0 | 1.29 |
| NGC1087F09 | 41.605773 | 0.15 | -0.494446 | 1.25 | 2018-10-17T12:17:46 | 1200.0 | 1.09 | 90.0 | 1.19 |
| NGC1087F09 | 41.605773 | 0.15 | -0.494391 | 1.05 | 2018-10-17T12:38:58 | 1200.0 | 1.12 | 90.0 | 1.15 |
| NGC1087F08 | 41.605884 | -0.25 | -0.494391 | 1.05 | 2018-10-17T13:12:00 | 1200.0 | 1.19 | 90.0 | 1.16 |
| NGC1087F08 | 41.605884 | -0.25 | -0.494446 | 1.25 | 2018-10-17T13:33:09 | 1200.0 | 1.25 | 90.0 | 1.27 |
| NGC1087F04 | 41.606050 | -0.85 | -0.494169 | 0.25 | 2018-10-17T14:06:31 | 1200.0 | 1.39 | 90.0 | 1.21 |
| NGC1087F04 | 41.606050 | -0.85 | -0.494113 | 0.05 | 2018-10-17T14:27:51 | 1200.0 | 1.52 | 90.0 | 1.31 |
| NGC1087F11 | 41.605884 | -0.25 | -0.494391 | 1.05 | 2018-10-16T13:30:01 | 1200.0 | 1.23 | 90.0 | 1.24 |
| NGC1087F11 | 41.605773 | 0.15 | -0.494391 | 1.05 | 2018-10-16T13:08:26 | 1200.0 | 1.17 | 90.0 | 1.16 |
| NGC1087F12 | 41.606939 | -4.05 | -0.495113 | 3.65 | 2018-10-16T11:36:44 | 1200.0 | 1.07 | 90.0 | 1.07 |
| NGC1087F12 | 41.606050 | -0.85 | -0.494724 | 2.25 | 2018-10-16T12:11:21 | 1200.0 | 1.08 | 90.0 | 1.19 |
| NGC1087F12 | 41.606050 | -0.85 | -0.494669 | 2.05 | 2018-10-16T12:32:55 | 1200.0 | 1.11 | 90.0 | 1.19 |
| NGC1300F1 | 49.903140 | -2.39 | -19.400675 | 1.25 | 2021-10-07T10:58:14 | 1200.0 | 1.44 | 90.0 | 1.14 |
| NGC1300F1 | 49.903140 | -2.39 | -19.400786 | 1.65 | 2021-10-07T11:19:16 | 1200.0 | 1.38 | 90.0 | 1.50 |
| NGC1300F2 | 49.903022 | -1.96 | -19.401008 | 2.45 | 2021-10-07T11:52:07 | 1200.0 | 1.32 | 90.0 | 1.14 |
| NGC1300F2 | 49.903022 | -1.96 | -19.400953 | 2.25 | 2021-10-07T12:13:05 | 1200.0 | 1.30 | 90.0 | 1.33 |
| NGC1300F3 | 49.902963 | -1.75 | -19.401619 | 4.65 | 2021-10-07T12:45:25 | 1200.0 | 1.29 | 90.0 | 1.34 |
| NGC1300F3 | 49.902963 | -1.75 | -19.401508 | 4.25 | 2021-10-07T13:06:26 | 1200.0 | 1.30 | 90.0 | 1.20 |
| NGC1300F4 | 49.903788 | -4.72 | -19.401341 | 3.65 | 2021-10-07T13:42:40 | 1200.0 | 1.35 | 90.0 | 1.04 |
| NGC1300F4 | 49.903729 | -4.51 | -19.401341 | 3.65 | 2021-10-07T14:03:37 | 1200.0 | 1.40 | 90.0 | 1.03 |
| NGC1300F5 | 49.903611 | -4.08 | -19.401730 | 5.05 | 2021-10-07T14:36:25 | 1200.0 | 1.51 | 0.0 | 1.33 |
| NGC1300F5 | 49.903552 | -3.87 | -19.401730 | 5.05 | 2021-10-07T14:57:23 | 1200.0 | 1.62 | 0.0 | 1.34 |
| NGC1385F1 | 54.372099 | -2.25 | -24.496321 | 1.65 | 2021-10-06T10:52:05 | 1200.0 | 1.70 | 90.0 | 1.52 |
| NGC1385F1 | 54.372099 | -2.25 | -24.496321 | 1.65 | 2021-10-06T11:13:46 | 1200.0 | 1.59 | 90.0 | 1.43 |
| NGC1385F2 | 54.372038 | -2.03 | -24.496265 | 1.45 | 2021-10-06T11:50:22 | 1200.0 | 1.47 | 90.0 | 1.26 |
| NGC1385F2 | 54.372038 | -2.03 | -24.496321 | 1.65 | 2021-10-06T12:11:22 | 1200.0 | 1.43 | 90.0 | 1.20 |
| NGC1385F3 | 54.371916 | -1.59 | -24.496432 | 2.05 | 2021-10-06T12:44:09 | 1200.0 | 1.40 | 90.0 | 1.06 |
| NGC1385F3 | 54.371916 | -1.59 | -24.496487 | 2.25 | 2021-10-06T13:05:09 | 1200.0 | 1.39 | 90.0 | 1.35 |
| NGC1385F4 | 54.371794 | -1.15 | -24.496265 | 1.45 | 2021-10-06T13:38:12 | 1200.0 | 1.42 | 90.0 | 1.16 |
| NGC1385F4 | 54.371794 | -1.15 | -24.496265 | 1.45 | 2021-10-06T13:59:12 | 1200.0 | 1.45 | 90.0 | 1.06 |
| NGC1385F5 | 54.371611 | -0.49 | -24.495710 | -0.55 | 2021-10-06T14:41:06 | 1200.0 | 1.57 | 0.0 | 1.21 |
| NGC2835F1 | 139.471355 | -3.51 | -22.341874 | 0.05 | 2019-03-27T05:57:41 | 1200.0 | 1.47 | 90.0 | 1.42 |
| NGC2835F1 | 139.471355 | -3.51 | -22.341874 | 0.05 | 2019-03-27T06:18:44 | 1200.0 | 1.42 | 90.0 | 1.52 |
| NGC2835F2 | 139.471475 | -3.95 | -22.342430 | 2.05 | 2019-03-27T06:52:51 | 1200.0 | 1.36 | 90.0 | 1.51 |
| NGC2835F2 | 139.471475 | -3.95 | -22.342430 | 2.05 | 2019-03-27T07:13:56 | 1200.0 | 1.35 | 90.0 | 1.42 |
| NGC2835F3 | 139.471114 | -2.65 | -22.342874 | 3.65 | 2019-03-27T07:47:08 | 1200.0 | 1.36 | 90.0 | 1.39 |
| NGC2835F3 | 139.471054 | -2.43 | -22.342874 | 3.65 | 2019-03-27T08:08:11 | 1200.0 | 1.38 | 90.0 | 1.52 |
| NGC2835F4 | 139.470694 | -1.14 | -22.343041 | 4.25 | 2019-03-27T08:42:01 | 1200.0 | 1.45 | 90.0 | 1.26 |
| NGC2835F4 | 139.470634 | -0.92 | -22.342985 | 4.05 | 2019-03-27T09:03:11 | 1200.0 | 1.51 | 90.0 | 1.17 |
| NGC3627F1 | 170.056873 | -2.92 | 12.998914 | 1.45 | 2017-12-24T12:43:33 | 120.0 | 1.32 | 90.0 | 1.27 |
| NGC3627F1 | 170.056873 | -2.92 | 12.998858 | 1.65 | 2017-12-24T12:46:31 | 120.0 | 1.30 | 90.0 | 1.27 |
| NGC3627F1 | 170.056873 | -2.92 | 12.998858 | 1.65 | 2017-12-24T12:49:28 | 120.0 | 1.29 | 90.0 | 1.26 |
| NGC3627F1 | 170.056873 | -2.92 | 12.998858 | 1.65 | 2017-12-24T12:52:26 | 120.0 | 1.28 | 90.0 | 1.27 |
| NGC3627F1 | 170.056873 | -2.92 | 12.998858 | 1.65 | 2017-12-24T12:55:24 | 120.0 | 1.26 | 90.0 | 1.27 |
| NGC3627F1 | 170.056132 | -0.26 | 12.999192 | 0.45 | 2017-12-24T15:33:08 | 120.0 | 1.01 | 90.0 | 1.16 |
| NGC3627F1 | 170.056132 | -0.26 | 12.999192 | 0.45 | 2017-12-24T15:36:06 | 120.0 | 1.01 | 90.0 | 1.22 |
| NGC3627F1 | 170.056132 | -0.26 | 12.999192 | 0.45 | 2017-12-24T15:39:04 | 120.0 | 1.01 | 90.0 | 1.21 |
| NGC3627F1 | 170.056132 | -0.26 | 12.999192 | 0.45 | 2017-12-24T15:42:02 | 120.0 | 1.01 | 90.0 | 1.20 |
| NGC3627F2 | 170.057215 | -4.16 | 12.998747 | 2.05 | 2017-12-24T13:02:38 | 120.0 | 1.24 | 90.0 | 1.21 |
| NGC3627F2 | 170.057215 | -4.16 | 12.998747 | 2.05 | 2017-12-24T13:05:35 | 120.0 | 1.23 | 90.0 | 1.23 |
| NGC3627F2 | 170.057215 | -4.16 | 12.998747 | 2.05 | 2017-12-24T13:08:33 | 120.0 | 1.22 | 90.0 | 1.22 |
| NGC3627F2 | 170.057215 | -4.16 | 12.998747 | 2.05 | 2017-12-24T13:11:31 | 120.0 | 1.21 | 90.0 | 1.19 |
| NGC3627F2 | 170.057215 | -4.16 | 12.998747 | 2.05 | 2017-12-24T13:14:29 | 120.0 | 1.20 | 90.0 | 1.23 |
| NGC3627F3 | 170.057215 | -4.16 | 12.998747 | 2.05 | 2017-12-24T13:20:54 | 120.0 | 1.18 | 90.0 | 1.13 |
| NGC3627F3 | 170.057215 | -4.16 | 12.998747 | 2.05 | 2017-12-24T13:23:52 | 120.0 | 1.17 | 90.0 | 1.12 |
| NGC3627F3 | 170.057215 | -4.16 | 12.998747 | 2.05 | 2017-12-24T13:26:50 | 120.0 | 1.16 | 90.0 | 1.12 |
| NGC3627F3 | 170.057215 | -4.16 | 12.998747 | 2.05 | 2017-12-24T13:29:48 | 120.0 | 1.15 | 90.0 | 1.12 |
| NGC3627F3 | 170.057215 | -4.16 | 12.998747 | 2.05 | 2017-12-24T13:32:45 | 120.0 | 1.14 | 90.0 | 1.14 |
| NGC3627F4 | 170.057215 | -4.16 | 12.998580 | 2.65 | 2017-12-24T13:40:31 | 120.0 | 1.12 | 90.0 | 1.14 |
| NGC3627F4 | 170.057215 | -4.16 | 12.998580 | 2.65 | 2017-12-24T13:43:29 | 120.0 | 1.12 | 90.0 | 1.14 |
| NGC3627F4 | 170.057215 | -4.16 | 12.998580 | 2.65 | 2017-12-24T13:46:27 | 120.0 | 1.11 | 90.0 | 1.14 |
| NGC3627F4 | 170.057215 | -4.16 | 12.998580 | 2.65 | 2017-12-24T13:49:25 | 120.0 | 1.10 | 90.0 | 1.15 |
| NGC3627F4 | 170.057215 | -4.16 | 12.998580 | 2.65 | 2017-12-24T13:52:23 | 120.0 | 1.10 | 90.0 | 1.15 |
| NGC3627F5 | 170.057215 | -4.16 | 12.998525 | 2.85 | 2017-12-24T13:58:52 | 120.0 | 1.09 | 90.0 | 1.06 |
| NGC3627F5 | 170.057158 | -3.95 | 12.998525 | 2.85 | 2017-12-24T14:01:50 | 120.0 | 1.08 | 90.0 | 1.07 |
| NGC3627F5 | 170.057158 | -3.95 | 12.998525 | 2.85 | 2017-12-24T14:04:48 | 120.0 | 1.08 | 90.0 | 1.07 |
| NGC3627F5 | 170.057158 | -3.95 | 12.998525 | 2.85 | 2017-12-24T14:07:46 | 120.0 | 1.07 | 90.0 | 1.07 |
| NGC3627F5 | 170.057158 | -3.95 | 12.998525 | 2.85 | 2017-12-24T14:10:44 | 120.0 | 1.07 | 90.0 | 1.07 |
| NGC3627F6 | 170.056246 | -0.67 | 12.999136 | 0.65 | 2017-12-24T14:24:16 | 120.0 | 1.05 | 90.0 | 1.12 |
| NGC3627F6 | 170.056189 | -0.46 | 12.999136 | 0.65 | 2017-12-24T14:27:14 | 120.0 | 1.04 | 90.0 | 1.15 |
| NGC3627F6 | 170.056189 | -0.46 | 12.999136 | 0.65 | 2017-12-24T14:30:11 | 120.0 | 1.04 | 90.0 | 1.17 |
| NGC3627F6 | 170.056189 | -0.46 | 12.999136 | 0.65 | 2017-12-24T14:33:10 | 120.0 | 1.04 | 90.0 | 1.17 |
| NGC3627F6 | 170.056189 | -0.46 | 12.999136 | 0.65 | 2017-12-24T14:36:07 | 120.0 | 1.03 | 90.0 | 1.15 |
| NGC3627F7 | 170.056303 | -0.87 | 12.999136 | 0.65 | 2017-12-24T14:42:14 | 120.0 | 1.03 | 90.0 | 1.16 |
| NGC3627F7 | 170.056303 | -0.87 | 12.999136 | 0.65 | 2017-12-24T14:45:11 | 120.0 | 1.03 | 90.0 | 1.16 |
| NGC3627F7 | 170.056303 | -0.87 | 12.999136 | 0.65 | 2017-12-24T14:48:09 | 120.0 | 1.02 | 90.0 | 1.17 |
| NGC3627F7 | 170.056303 | -0.87 | 12.999136 | 0.65 | 2017-12-24T14:51:07 | 120.0 | 1.02 | 90.0 | 1.18 |
| NGC3627F7 | 170.056303 | -0.87 | 12.999136 | 0.65 | 2017-12-24T14:54:05 | 120.0 | 1.02 | 90.0 | 1.20 |
| NGC3627F8 | 170.056303 | -0.87 | 12.998914 | 1.45 | 2017-12-24T15:00:09 | 120.0 | 1.02 | 90.0 | 1.05 |
| NGC3627F8 | 170.056303 | -0.87 | 12.998914 | 1.45 | 2017-12-24T15:03:07 | 120.0 | 1.01 | 90.0 | 1.05 |
| NGC3627F8 | 170.056246 | -0.67 | 12.998914 | 1.45 | 2017-12-24T15:06:05 | 120.0 | 1.01 | 90.0 | 1.05 |
| NGC3627F8 | 170.056246 | -0.67 | 12.998914 | 1.45 | 2017-12-24T15:09:03 | 120.0 | 1.01 | 90.0 | 1.06 |
| NGC3627F8 | 170.056246 | -0.67 | 12.998914 | 1.45 | 2017-12-24T15:12:00 | 120.0 | 1.01 | 90.0 | 1.05 |
| NGC3627F9 | 170.056018 | 0.15 | 12.998803 | 1.85 | 2017-12-24T15:15:05 | 120.0 | 1.01 | 90.0 | 1.12 |
| NGC3627F9 | 170.056018 | 0.15 | 12.998803 | 1.85 | 2017-12-24T15:18:03 | 120.0 | 1.01 | 90.0 | 1.12 |
| NGC3627F9 | 170.056018 | 0.15 | 12.998803 | 1.85 | 2017-12-24T15:21:01 | 120.0 | 1.01 | 90.0 | 1.12 |
| NGC3627F9 | 170.056018 | 0.15 | 12.998803 | 1.85 | 2017-12-24T15:23:59 | 120.0 | 1.01 | 90.0 | 1.11 |
| NGC3627F9 | 170.056018 | 0.15 | 12.998803 | 1.85 | 2017-12-24T15:26:57 | 120.0 | 1.01 | 90.0 | 1.11 |
| NGC5068F1 | 199.704057 | -2.20 | -21.023638 | 0.85 | 2019-03-27T09:49:19 | 1200.0 | 1.47 | 90.0 | 1.51 |
| NGC5068F1 | 199.704057 | -2.20 | -21.023694 | 1.05 | 2019-03-27T10:10:22 | 1200.0 | 1.41 | 90.0 | 1.33 |
| NGC5068F2 | 199.703819 | -1.34 | -21.023638 | 0.85 | 2019-03-27T10:44:05 | 1200.0 | 1.35 | 90.0 | 1.40 |
| NGC5068F3 | 199.703938 | -1.77 | -21.023971 | 2.05 | 2019-03-27T11:38:24 | 1200.0 | 1.32 | 90.0 | 2.49 |
| NGC5068F3 | 199.703938 | -1.77 | -21.023971 | 2.05 | 2019-03-27T11:59:28 | 1200.0 | 1.34 | 90.0 | 2.49 |
| NGC5068F4 | 199.703700 | -0.91 | -21.024138 | 2.65 | 2019-03-27T12:32:51 | 1200.0 | 1.39 | 90.0 | 1.55 |
| NGC5068F4 | 199.703700 | -0.91 | -21.024194 | 2.85 | 2019-03-27T12:53:55 | 1200.0 | 1.45 | 90.0 | 1.88 |
| NGC5068F5 | 199.703403 | 0.16 | -21.023860 | 1.65 | 2019-03-27T13:28:21 | 1200.0 | 1.58 | 90.0 | 1.97 |
| NGC5068F5 | 199.703998 | -1.98 | -21.023694 | 1.05 | 2019-03-28T10:19:33 | 1200.0 | 1.38 | 90.0 | 1.69 |
| NGC5068F7 | 199.704057 | -2.20 | -21.023694 | 1.05 | 2019-03-28T10:54:58 | 1200.0 | 1.33 | 90.0 | 1.68 |
| NGC5068F7 | 199.703998 | -1.98 | -21.023694 | 1.05 | 2019-03-28T11:16:01 | 1200.0 | 1.32 | 90.0 | 1.67 |
| NGC5068F8 | 199.703879 | -1.55 | -21.024082 | 2.45 | 2019-03-28T11:49:43 | 1200.0 | 1.33 | 90.0 | 1.86 |
| NGC5068F8 | 199.703819 | -1.34 | -21.024027 | 2.25 | 2019-03-28T12:10:49 | 1200.0 | 1.36 | 90.0 | 1.87 |
| NGC5068F9 | 199.703403 | 0.16 | -21.024138 | 2.65 | 2019-03-28T12:44:48 | 1200.0 | 1.43 | 90.0 | 1.67 |
| NGC5068F9 | 199.703343 | 0.37 | -21.024138 | 2.65 | 2019-03-28T13:05:52 | 1200.0 | 1.50 | 90.0 | 1.65 |
| NGC5068F9 | 199.703700 | -0.91 | -21.023138 | -0.95 | 2022-02-24T14:57:54 | 1200.0 | 1.46 | 0.0 | 1.39 |
| NGC5068F9 | 199.703641 | -0.70 | -21.023138 | -0.95 | 2022-02-24T15:08:56 | 600.0 | 1.50 | 0.0 | 1.46 |
| NGC5068F10 | 199.703700 | -0.91 | -21.023527 | 0.45 | 2022-02-24T15:30:23 | 800.0 | 1.59 | 90.0 | 1.17 |
| NGC5068F10 | 199.703700 | -0.91 | -21.023471 | 0.25 | 2022-02-24T15:38:22 | 420.0 | 1.63 | 90.0 | 1.13 |

: *Summary of KCWI Observations*. This table reports the the galaxy and the field observed (Field). Note the repeated fields are offset by 1/2 slice width, with the exception of all the fields in NGC3627. The table also reports: the original coordinates of the field center in right ascension and declination (RA, DEC), the applied astrometric correction in right ascension and declination (RA$_{\mathrm{corr}}$, DEC$_{\mathrm{corr}}$) determined from the image registration, the UTC start-time and total integration the exposure in seconds (Date, Exposure) as well as the airmass (Airmass), position angle (Angle) and the angular FWHM of the pointing.

Table notes: $^{a}$ The field numbering is from internal lists of potential pointings which were not performed in numerical order, therefore the field number does not reflect the sequence of observations. $^{b}$ The astrometric correction is described in Section [3.2](#sec:registration). $^{c}$ The measured angular FWHM for the pointing, see Section [3.4](#sec:psf+per_pointing).

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Star$^{a}$ | RA | Dec | Date | Exposure | Airmass | FWHM$^{b}$ |
|  |  |  | (UTC) | \(s\) |  | ($''$) |
| He3 | 06:47:37.99 | +37:30:57.1 | 2018-10-16T15:00:13 | 20.0 | 1.06 | 1.32 |
| Feige15 | 01:49:09.49 | +13:33:11.7 | 2018-10-17T09:04:57 | 10.0 | 1.07 | 1.69 |
| Feige15 | 01:49:09.49 | +13:33:11.7 | 2018-10-17T09:06:11 | 1.0 | 1.07 | 1.12 |
| Feige15 | 01:49:09.49 | +13:33:11.7 | 2018-10-16T10:44:02 | 10.0 | 1.01 | 1.04 |
| Feige34 | 10:39:36.71 | +43:06:10.1 | 2019-03-27T09:21:06 | 5.0 | 1.10 | 1.28 |
| Feige34 | 10:39:36.71 | +43:06:10.1 | 2019-03-27T09:22:26 | 1.0 | 1.10 | 1.21 |
| Feige66 | 12:37:23.52 | +25:03:59.3 | 2019-03-27T13:45:25 | 1.0 | 1.35 | 1.99 |
| Feige66 | 12:37:23.52 | +25:03:59.3 | 2019-03-28T13:19:36 | 1.0 | 1.26 | 1.83 |
| Feige66 | 12:37:23.52 | +25:03:59.3 | 2019-03-28T13:20:57 | 5.0 | 1.26 | 1.83 |
| GD50 | 03:48:50.31 | -00:58:35.8 | 2021-10-06T10:17:51 | 1.0 | 1.47 | 1.13 |
| GD50 | 03:48:50.31 | -00:58:35.8 | 2021-10-06T10:19:37 | 1.0 | 1.46 | 1.13 |
| GD50 | 03:48:50.31 | -00:58:35.8 | 2021-10-06T10:20:53 | 10.0 | 1.45 | 1.18 |
| GD50 | 03:48:50.31 | -00:58:35.8 | 2021-10-06T10:22:37 | 15.0 | 1.44 | 1.22 |
| GD50 | 03:48:50.31 | -00:58:35.8 | 2021-10-06T14:13:09 | 10.0 | 1.11 | 1.01 |
| GD50 | 03:48:50.31 | -00:58:35.8 | 2021-10-06T14:14:54 | 15.0 | 1.11 | 1.04 |
| GD50 | 03:48:50.31 | -00:58:35.8 | 2021-10-06T14:16:28 | 1.0 | 1.11 | 1.06 |
| GD50 | 03:48:50.31 | -00:58:35.8 | 2021-10-07T10:29:40 | 1.0 | 1.38 | 1.07 |
| GD50 | 03:48:50.31 | -00:58:35.8 | 2021-10-07T10:30:56 | 10.0 | 1.38 | 1.11 |
| GD50 | 03:48:50.31 | -00:58:35.8 | 2021-10-07T10:32:17 | 15.0 | 1.37 | 1.10 |
| GD50 | 03:48:50.31 | -00:58:35.8 | 2021-10-07T13:19:16 | 10.0 | 1.07 | 1.11 |
| GD50 | 03:48:50.31 | -00:58:35.8 | 2021-10-07T13:20:43 | 15.0 | 1.07 | 1.18 |

: Summary of KCWI Standard Star Observations.

Table notes: $^{a}$ The name of each standard star as displayed in the KDRP list of standards. $^{b}$ The angular FWHM was measured from a 2D Gaussian fit to a white-light image of the standard star.

# KCWI Line Spread Function

The KCWI line spread function in the large slicer is non-Gaussian. Deviations from a Gaussian profile have been observed in KCWI data before. For example, using a combination of the medium slicer and grating (cite: vanDokkum_guass_hermite). Following (cite: vanderMarel_gauss_hermite), in order to parameterize the degree of deviation from a Gaussian profile, we fit the spectra from a pipeline reduced arc lamp exposure a Gauss-Hermite function of the form: $$\begin{eqnarray}
    \label{eq:gh}
   \nonumber G(X)=\frac{\gamma}{\sigma\sqrt{2\pi}}\exp{(-X^2/2)}\bigg[1+\ldots \\  h_3\frac{X(2X^2-3)}{\sqrt{3}} +  h_4\frac{4(X^2-3)X^2+3}{\sqrt{24}} \bigg],
\end{eqnarray}$$ with $X=(\lambda -\lambda_0)/\sigma$, amplitude ($\gamma$) and spectral width ($\sigma$). The anti-symmetric and symmetric deviations from pure Gaussian profiles are captured by the constants, $h_3$ and $h_4$. A Gaussian function is recovered by setting $h_3=h_4=0$. In Figure [19](#fig:hermite_maps) we show histograms of the fitted values from $h_3$ and $h_4$ after fitting Eq. [\[eq:gh\]](#eq:gh) to approximately $20$ isolated arc lamp emission lines. We find that the emission lines in the arc lamp images are consistently flat topped, with an average value of $h_4=-0.14 \pm 0.01$ across all spatial pixels. The degree that the line profile is non-Gaussian due to asymmetric deviations is small compared to symmetric deviations with an average value of $h_3=-0.007\pm 0.01$.

The authors state that the root cause of the deviation from a Gaussian profile is due to the slit width-limited resolution of the medium slicer (cite: slit_limiting). We posit that a similar limitation for the large slicer is responsible for the deviations measured in this work.

![image](h3_hist_large_slicer.pdf) ![image](h4_hist_large_slicer.pdf)

# Comparison of H II Region Identification Between KCWI and MUSE

We identify potential H II regions with H$\beta$ emission maps constructed from the KCWI galaxy mosaics using `HIIPhot`. H II regions, for the same galaxies, in the PHANGS Nebular Catalog were identified with `HIIPhot` and MUSE H$\alpha$ maps (cite: Kreckel2019ApJ...887...80K; Groves2023NebCat). Given the higher resolution of the MUSE imaging, as well as the three-fold brightness increase of H$\alpha$ relative to H$\beta$, we expect our H II region catalog to be less sensitive to the faintest and smallest H II regions.

In Figure [20](#fig:lum) we show both the distribution of dust-corrected H$\beta$ luminosity, $L_{\rm{H}\beta}$, and radii, for regions identified by *HIIPhot* using KCWI H$\beta$ maps, “KCWI–H$\beta$ regions”, and MUSE H$\alpha$ maps or “MUSE–H$\alpha$ regions” within the KCWI mosaic footprint. For KCWI–H$\beta$ regions we measure a median Log$_{10}(L_{\rm{H}\beta}/[\rm{erg}\ \rm{s}^{-1}]$) of 37.7$^{+0.9}_{-0.7}$ while for MUSE–H$\alpha$ regions the median is 37.1$^{+0.8}_{-1.7}$. This comparison shows that the KCWI H$\beta$ maps is less sensitive to regions with Log$_{10}(L_{\rm{H}\beta}/[\rm{erg}\ \rm{s}^{-1}]$) $<$ 37.

We also observe in Figure [20](#fig:lum) that regions with radii less than the KCWI angular resolution are missed KCWI–H$\beta$ region sample. This can be seen clearly in Figures [21](#fig:hii_masks_1087)–[27](#fig:hii_masks_0628), where we compare the boundaries of the MUSE–H$\alpha$ and KCWI–H$\beta$ regions. In these figures, we see that many of the missed regions are small, and unresolved in the KCWI H$\beta$ map. Also owing to the larger number of detections is that many of the larger KCWI–H$\beta$ regions are resolved into smaller structures in the MUSE–H$\alpha$ regions.

![image](lum_function.pdf) ![image](size_function.pdf)

|     Name      | $N_{\rm{KCWI}}$ | $N_{\rm{MUSE}}$ | $N_{ \rm{A}}$ |
|:-------------:|:---------------:|:---------------:|:-------------:|
| NGC 628$^{a}$ |       10        |       230       |       8       |
|   NGC 1087    |       173       |       364       |      73       |
|   NGC 1300    |       60        |       191       |      28       |
|   NGC 1385    |       133       |       417       |      58       |
|   NGC 2835    |       87        |       135       |      26       |
|   NGC 3627    |       163       |       451       |      19       |
|   NGC 5068    |       62        |       392       |      48       |

Table notes: $^{a}$ NGC 628 was imaged in the least ideal observing conditions.

![image](ngc1087_hii_regions.pdf) ![image](ngc1087_muse_hii_regions_compare.pdf)

![image](ngc1300_hii_regions.pdf) ![image](ngc1300_muse_hii_regions_compare.pdf)

![image](ngc1385_hii_regions.pdf) ![image](ngc1385_muse_hii_regions_compare.pdf)

![image](ngc2835_hii_regions.pdf) ![image](ngc2835_muse_hii_regions_compare.pdf)

![image](ngc3627_hii_regions.pdf) ![image](ngc3627_muse_hii_regions_compare.pdf)

![image](ngc5068_hii_regions.pdf) ![image](ngc5068_muse_hii_regions_compare.pdf)

![image](ngc628_hii_regions.pdf) ![image](ngc628_muse_hii_regions_compare.pdf)

# Example Gaussian Fits to Auroral Lines

In this section we show example auroral line fits. In Figure [28](#fig:auroral_line_fits) we show fits to high S/N auroral lines from an H II region in NGC 5068. We also include in Figure [28](#fig:auroral_line_fits) annotations describing the the standard deviation of the fit residuals, $\sigma_{res}$, the S/N for a single emission line (or in the instance of simultaneous double line fits the S/N of the *red* and *purple* Gaussian fit: S/N$_r$ and S/N$_p$), the continuum noise, $\sigma_{cont}$ and reduced $\chi^2$. In this particular example, the auroral line in these fits are isolated from contaminating sky lines or nearby emission, especially in the case of \[O III\]$\lambda4363$ Å  where the contribution from \[Fe II\]$\lambda4360$ Å is negligible. To demonstrate fitting \[Fe II\]$\lambda4360$ alongside \[O III\]$\lambda4363$ we show a low S/N detection with non-negligible contamination from \[Fe II\]$\lambda4360$ Å in Figure [29](#fig:auroral_line_fits_lowsn).

.

![](reg_28_specs_4363_dd_slope.pdf)

# Figures of the $\Delta T_e$ and H II Region Property Comparisons

In the section we present the comparisons between H II region properties that exhibit no significant correlations with $\Delta T_e$.

![image](all_gall_tdiff_N_e_low_ionization_.pdf) ![image](all_gall_tdiff_N_e_mid_ionization_.pdf) ![image](all_gall_tdiff_N_e_high_ion_.pdf)

![image](all_gall_tdiff_eta_low_ionization_.pdf) ![image](all_gall_tdiff_eta_mid_ionization_.pdf) ![image](all_gall_tdiff_eta_high_ion_.pdf)

![image](all_gall_tdiff_C_Age_low_ionization_.pdf) ![image](all_gall_tdiff_C_Age_mid_ionization_.pdf) ![image](all_gall_tdiff_C_Age_high_ion_.pdf)

![image](all_gall_tdiff_C_Mass_low_ionization_.pdf) ![image](all_gall_tdiff_C_Mass_mid_ionization_.pdf) ![image](all_gall_tdiff_C_Mass_high_ion_.pdf)

![image](all_gall_tdiff_A_Age_low_ionization_.pdf) ![image](all_gall_tdiff_A_Age_mid_ionization_.pdf) ![image](all_gall_tdiff_A_Age_high_ion_.pdf)

![image](all_gall_tdiff_mom0_low_ionization_.pdf) ![image](all_gall_tdiff_mom0_mid_ionization_.pdf) ![image](all_gall_tdiff_mom0_high_ion_.pdf)

![image](all_gall_tdiff_ptemp_low_ionization_.pdf) ![image](all_gall_tdiff_ptemp_mid_ionization_.pdf) ![image](all_gall_tdiff_ptemp_high_ion_.pdf)

# H II Region Measurements

| ID | NGC5068_1 | NGC5068_2 | NGC5068_3 | NGC5068_4 | NGC5068_5 | NGC5068_6 | NGC5068_7 | NGC5068_8 |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| $\rm{R.A.}(^{\circ})$ | 199.714 | 199.719 | 199.702 | 199.7 | 199.696 | 199.714 | 199.71 | 199.703 |
| $\rm{Dec.}(^{\circ})$ | -21.027 | -21.016 | -21.012 | -21.013 | -21.014 | -21.015 | -21.038 | -21.008 |
| $E(B-V)$(Mag) | 0.24 | 0.19 | 0.25 | 0.19 | 0.41 | 0.34 | 0.09 | 0.18 |
| H$\beta$$^{a}$ | 54.2$\pm$0.1 | 70.7$\pm$0.4 | 140.3$\pm$0.6 | 1385.6$\pm$7.3 | 211.4$\pm$1.4 | 37.6$\pm$0.2 | 27.2$\pm$0.2 | 59.8$\pm$0.3 |
| $\rm{[O~III]}$$\lambda$4363 | \- | \- | \- | 12.8$\pm$0.7 | \- | \- | \- | \- |
| $\rm{[O~III]}$$\lambda$5007 | 53.6$\pm$0.1 | 125.3$\pm$0.5 | 133.5$\pm$0.6 | 3239.9$\pm$15.0 | 415.7$\pm$1.8 | 35.6$\pm$0.1 | 16.5$\pm$0.2 | 78.2$\pm$0.3 |
| $\rm{[O~II]}$$\lambda$7320 | 0.8$\pm$0.1 | \- | 2.4$\pm$0.8 | 35.7$\pm$2.2 | 3.9$\pm$0.8 | \- | 0.4$\pm$0.1 | 0.9$\pm$0.3 |
| $\rm{[O~II]}$$\lambda$7331 | 0.8$\pm$0.1 | \- | 2.6$\pm$0.8 | 31.1$\pm$2.2 | 3.9$\pm$0.8 | \- | 0.4$\pm$0.1 | 1.1$\pm$0.3 |
| $\rm{[O~II]}$$\lambda$3727 | 79.0$\pm$0.5 | 128.0$\pm$1.4 | 515.4$\pm$2.6 | 3128.6$\pm$25.3 | 639.0$\pm$5.8 | 89.3$\pm$0.6 | 62.1$\pm$0.6 | 194.3$\pm$1.2 |
| $\rm{[S~II]}$$\lambda$4068 | 0.6$\pm$0.1 | 1.5$\pm$0.1 | 3.1$\pm$0.9 | 46.4$\pm$7.4 | 4.0$\pm$1.2 | 0.8$\pm$0.1 | 1.3$\pm$0.4 | 1.4$\pm$0.2 |
| $\rm{[S~II]}$$\lambda$4076 | 0.2$\pm$0.1 | 0.5$\pm$0.1 | 3.1$\pm$1.8 | 3.8$\pm$3.6 | 0.0$\pm$2.4 | 0.3$\pm$0.1 | 0.1$\pm$0.1 | 0.5$\pm$0.2 |
| $\rm{[S~III]}$$\lambda$6313 | 0.5$\pm$0.0 | 0.7$\pm$0.1 | 1.5$\pm$0.1 | 18.9$\pm$0.3 | 2.7$\pm$0.1 | 0.4$\pm$0.0 | 0.2$\pm$0.0 | 0.7$\pm$0.0 |
| $\rm{[S~II]}$$\lambda$6716 | 12.7$\pm$0.1 | 22.6$\pm$0.2 | 60.4$\pm$0.3 | 352.1$\pm$0.9 | 71.0$\pm$0.3 | 14.4$\pm$0.1 | 10.6$\pm$0.1 | 21.5$\pm$0.1 |
| $\rm{[S~II]}$$\lambda$6731 | 9.4$\pm$0.1 | 15.8$\pm$0.1 | 42.1$\pm$0.3 | 259.1$\pm$0.8 | 49.8$\pm$0.3 | 10.1$\pm$0.1 | 7.3$\pm$0.1 | 14.8$\pm$0.1 |
| $\rm{[S~III]}$$\lambda$9069 | 11.9$\pm$0.1 | 12.4$\pm$0.2 | 20.5$\pm$0.2 | 389.1$\pm$1.2 | 42.3$\pm$0.3 | 7.1$\pm$0.1 | 4.5$\pm$0.1 | 9.9$\pm$0.1 |
| $\rm{[N~II]}$$\lambda$5756 | 0.3$\pm$0.0 | 0.3$\pm$0.0 | 0.5$\pm$0.1 | 4.3$\pm$0.1 | 0.8$\pm$0.1 | 0.1$\pm$0.0 | 0.1$\pm$0.0 | 0.2$\pm$0.1 |
| $\rm{[N~II]}$$\lambda$6548 | 10.2$\pm$0.0 | 9.1$\pm$0.1 | 20.3$\pm$0.1 | 152.5$\pm$0.3 | 25.2$\pm$0.1 | 6.2$\pm$0.0 | 4.7$\pm$0.0 | 6.8$\pm$0.0 |
| $\rm{[N~II]}$$\lambda$6584 | 30.1$\pm$0.1 | 26.9$\pm$0.2 | 59.7$\pm$0.3 | 449.8$\pm$1.0 | 74.1$\pm$0.3 | 18.3$\pm$0.1 | 13.9$\pm$0.1 | 20.0$\pm$0.1 |
| $n_{\rm{e}}$($\rm{cm}^{-3}$) | 99 | 21 | 13 | 91 | 20 | 22 | 12 | 10 |
| /\[O II\]  | 0.68$\pm$0.0 | 0.98$\pm$0.01 | 0.26$\pm$0.0 | 1.04$\pm$0.01 | 0.65$\pm$0.01 | 0.4$\pm$0.0 | 0.27$\pm$0.0 | 0.4$\pm$0.0 |
| /\[S II\]  | 1.87$\pm$0.02 | 1.13$\pm$0.02 | 0.7$\pm$0.01 | 2.23$\pm$0.01 | 1.23$\pm$0.01 | 1.01$\pm$0.01 | 0.88$\pm$0.01 | 0.95$\pm$0.01 |
| $T_{\rm{e},\text{[{N}{ \uppercase{\romannumeral 2\relax}}]}}$ (K) | 8179.0$\pm$291.0 | 8769.0$\pm$563.0 | 8122.0$\pm$489.0 | 8486.0$\pm$90.0 | 9056.0$\pm$458.0 | 7461.0$\pm$657.0 | 8208.0$\pm$778.0 | 8232.0$\pm$858.0 |
| $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 2\relax}}]}}$ (K) | 7580.0$\pm$768.0 | 10364.0$\pm$594.0 | 11467.0$\pm$3028.0 | 14318.0$\pm$2652.0 | 7704.0$\pm$2444.0 | 8661.0$\pm$1044.0 | 14772.0$\pm$4095.0 | 10029.0$\pm$1260.0 |
| $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 2\relax}}]}}$ (K) | 10941.0$\pm$1467.0 | \- | 7999.0$\pm$1134.0 | 11243.0$\pm$700.0 | 8785.0$\pm$1009.0 | \- | 9042.0$\pm$1421.0 | 8120.0$\pm$1143.0 |
| $T_{\rm{e},\text{[{S}{ \uppercase{\romannumeral 3\relax}}]}}$ (K) | 8513.0$\pm$110.0 | 9528.0$\pm$421.0 | 10235.0$\pm$273.0 | 8755.0$\pm$52.0 | 9807.0$\pm$180.0 | 9249.0$\pm$365.0 | 8438.0$\pm$185.0 | 10250.0$\pm$297.0 |
| $T_{\rm{e},\text{[{O}{ \uppercase{\romannumeral 3\relax}}]}}$ (K) | \- | \- | \- | 8658.0$\pm$135.0 | \- | \- | \- | \- |

: Measured and Derived Properties for H II Regions with two more auroral lines.

Table notes: Table [\[tab:auroral_nebular_line_fluxes\]](#tab:auroral_nebular_line_fluxes) is published in its entirety in the machine-readable format. A portion is shown here for guidance regarding its form and content. $^{a}$ Emission line strengths, and uncertainties, are reported in units of $10^{-16}\times \rm{ergs}~\rm{s}^{-1}~\rm{cm}^{-2}$.

[^1]: \[O II\]$\lambda\lambda7320,7330$ is an unresolved quadruplet with transitions at $\lambda7319$, $\lambda7320$, $\lambda7330$ and $\lambda7331$ Å.

[^2]: [http://phangs.org/](https://sites.google.com/view/phangs/home)

[^3]: https://pypi.org/project/pymusepipe/

[^4]: https://gitlab.com/francbelf/ifu-pipeline

[^5]: (cite: 2022PHANGS_HST) use of previous NGC 628 HST imaging obtained as part of the Legacy ExtraGalactic Ultraviolet Survey (cite: LEGUS:2015).

[^6]: [KCWI DRP-Python](https://github.com/Keck-DataReductionPipelines/KCWI_DRP)

[^7]: [KeckDRPFramework](https://github.com/Keck-DataReductionPipelines/KeckDRPFramework)

[^8]: [KCWI DRP-IDL](https://github.com/Keck-DataReductionPipelines/KCWIDRP)

[^9]: https://kcwi-drp.readthedocs.io/en/latest/sky_subtraction.html

[^10]: See http://montage.ipac.caltech.edu/

[^11]: https://github.com/jmeyers314/linmix

</paper>

Write the methods card for this paper.