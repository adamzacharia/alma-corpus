# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...970..114T\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...970..114T",
 "title": "Evidence of Grain Alignment by Magnetically Enhanced Radiative Torques from Multiwavelength Dust Polarization Modeling of HL Tau",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Thang, Nguyen Tat",
 "n_authors": 7,
 "arxiv_id": "2401.00220",
 "doi": "10.3847/1538-4357/ad4f74",
 "alma_projects_linked_by_archive": [
  "2016.1.00115.S",
  "2016.1.00162.S",
  "2019.1.01051.S"
 ]
}
```

Paper text:
<paper>
# **Evidence of Grain Alignment by Magnetically Enhanced Radiative Torques from Multiwavelength Dust Polarization Modeling of HL Tau**

## Abstract

Atacama Large Millimeter/Submillimeter Array has revolutionized the field of dust polarization in protoplanetary disks across multiple wavelengths. Previous observations and empirical modeling suggested multiple mechanisms of dust polarization toward HL Tau, including grain alignment and dust scattering. However, a detailed modeling of dust polarization based on grain alignment physics is not yet available. Here, using our updated POLARIS code, we perform numerical modeling of dust polarization arising from both grain alignment by Magnetically Enhanced Radiative Torque mechanism and self-scattering to reproduce the HL Tau polarization observed at three wavelengths 0.87, 1.3, and 3.1$\,$mm. Our modeling results show that the observed multi-wavelength polarization could be reproduced only when large grains contain embedded iron inclusions and those with slow internal relaxation must have wrong internal alignment (i.e., the grain’s major axis parallel to its angular momentum). The abundance of iron embedded inside grains in the form of clusters is constrained to be $\gtrsim 16$%, and the number of iron atoms per cluster is $N_{\rm cl} \sim 9\times10^2$. Maximum grain sizes probed at wavelengths $\lambda$ = 0.87, 1.3, and 3.1$\,$mm are constrained at $\sim$ 60, 80, and 90$\,\mu$m, respectively.

# Introduction

Magnetic fields are thought to play a crucial role in protoplanetary disks in driving magnetorotational instability (cite: 1959JETP....9..995V; 1991ApJ...376..214B), disk formation (e.g., magnetic braking and angular momentum transport) (cite: 1991ApJ...376..214B; 1998RvMP...70....1B; 1994ASPC...54...73H), protostellar outflow launching (cite: 1982MNRAS.199..883B; 2021AAS...23832901S), and planet formation (cite: 1998ApJ...508..707Q; 2003A&A...411..623F; 2009IAUS..259..249J). Polarized thermal emission from aligned grains has been known as the leading tool to investigate the magnetic fields in the interstellar medium (ISM) and molecular clouds (MCs). Therefore, dust polarization is expected to be a powerful tool in studying magnetic fields (cite: 2014Natur.514..597S) and dust properties (cite: 2015ApJ...809...78K) in disks. Since the emergence of the Atacama Large Millimeter/submillimeter Array (ALMA), the field of (sub)millimeter-wavelength disk polarization has progressed significantly with the polarization signatures being observed to incredible detail and accuracy (cite: 2017ApJ...851...55S; 2017ApJ...844L...5K; 2018ApJ...855...92C; 2019ApJ...877L...2H; 2019ApJS..245....2S; 2023ApJ...947L...5T).

HL Tau is a perfect example to illustrate the evolutionary process of the field. It is a young protoplanetary disk (SED class I/II, age $\sim\,$1 Myr) (cite: 2004ApJ...616..998W) located in the Taurus molecular cloud, which is $\sim\,140\,$pc from Earth (cite: 2004AJ....127.1029R). It is one of the earliest disks observed with polarimetry by Combined Array for Research in Millimeter-wave Astronomy (CARMA) and Submillimeter Array (SMA). Its polarized emission was used to study the disk’s magnetic fields, supposing grains are magnetically aligned (cite: 2014Natur.514..597S). However, the study concluded that a simple magnetic field structure could not fully explain the detected polarization. Coming to the age of ALMA observations, the disk has been revealed to have a transition of polarization morphology from azimuthal to parallel to the disk’s minor axis when probing at longer to shorter wavelengths (cite: 2017ApJ...844L...5K; 2017ApJ...851...55S). These new observations essentially raise questions about the validity of tracing magnetic fields by dust polarization within the disk.

The complex polarization patterns indicate the possibility of multiple mechanisms involved in producing the dust-polarized emission of HL Tau at (sub)millimeter wavelengths. Indeed, previous studies have suggested that a superposition of self-scattering and thermal emission from azimuthally-aligned prolate grains can explain such observed polarized emission (cite: 2019MNRAS.483.2371Y; 2021ApJ...908..153M; 2022MNRAS.512.3922L). Self-scattering is caused by dust grains with sizes comparable to the observed wavelengths scattering and polarizing incident lights from the thermal emission of other grains (cite: 2015ApJ...809...78K). Grain alignment, on the other hand, has elongated grains being systematically aligned with a preferred direction and emitting polarized thermal electromagnetic waves. Nevertheless, which mechanisms exactly induce grain alignment in such a way is still a mystery since most of the proposed mechanisms (i.e., magnetic alignment, radiative alignment, aerodynamic alignment) fail to interpret the observed disk polarization (cite: 2017ApJ...839...56T; 2019MNRAS.483.2371Y; 2021ApJ...908..153M).

Grain alignment in the ISM and MCs has been studied with great success and made dust polarization an invaluable tool to trace magnetic fields within the environment (cite: 2015ARA&A..53..501A; 2019FrASS...6...15P). However, its applicability to the protostellar environment is complex due to the presence of very large grains (grain size $a\,\gtrsim\,\text{10}\,\mu$m) and significant gas randomization effect. Recently, (cite: 2022AJ....164..248H) considered a more realistic grain alignment model within such an environment in contrast to previous modelings where only perfect alignment is included. The process of grain alignment therein consists of the alignment of the axis of maximum moment of inertia ($\boldsymbol{\hat{a_1}}$) with the angular momentum ($\boldsymbol{J}$), so-called internal alignment (IA); and the alignment of $\boldsymbol{J}$ with a preferred direction, so-called external alignment (EA). Internal alignment can be achieved by internal relaxation (INR), e.g., Barnett relaxation (cite: 1993ApJ...418..287R) and inelastic relaxation (cite: 2003A&A...398..809M). External alignment, on the other hand, can be accomplished by grain precession (e.g., Larmor precession, radiative precession, and mechanical precession). Grains achieving external alignment with Larmor precession, radiative precession, or mechanical precession have $\boldsymbol{J}$ aligned along the direction of the magnetic field ($\boldsymbol{B}$), radiation beam ($\boldsymbol{k}$), or gas flow ($\boldsymbol{\nu}$). The mechanisms behind such alignments are called magnetic alignment ((cite: 2022ApJ...928..102H)), radiative alignment ($k$-RAT; (cite: 2007MNRAS.378..910L)), or mechanical alignment ($v$-MET; (cite: 2007ApJ...669L..77L)), respectively.

Recently, (cite: 2023MNRAS.520.3788G) incorporated such grain alignment model (i.e., realistic internal alignment and external alignment model) into POLARIS (cite: 2016A&A...593A..87R) taking into account only the grain alignment mechanism of Magnetically-enhanced Radiative Torque (MRAT) (cite: 2016ApJ...831..159H) which was specifically applied to study thermal dust polarization towards protostellar cores. With this mechanism, grains can be aligned with the disk magnetic fields by radiative torques (RATs; (cite: 1976Ap&SS..43..291D; 1997ApJ...480..633D; 2008MNRAS.388..117H)) with enhanced efficiencies by (super)paramagnetic relaxation (cite: 1951ApJ...114..206D; 2008MNRAS.388..117H; 2016ApJ...831..159H).

In this paper, our main goal is to test the validity of grain alignment with the MRAT mechanism and put a strong constraint on grain magnetic properties as well as grain growth in HL Tau. To do so, we perform multi-wavelength modeling of disk polarization using the updated POLARIS (cite: 2023MNRAS.520.3788G) for three well-studied ALMA Bands 3, 6, and 7 corresponding to the wavelengths $\lambda$ = 3.1, 1.3, and 0.87$\,$mm.

The structure of this paper is as follows. In Section [2](#model), we describe the disk and dust model used in our modeling. Subsequently, our main results including synthetic polarization from thermal aligned dust emission with MRAT mechanism; and from the mixture of grain alignment and self-scattering are shown in Section [3.1](#ncl_pol_result) and [3.2](#resultf), respectively. We further discuss the implications, grain alignment properties, and grain growth in Section [4](#sec:discussions). Finally, the main findings are summarized in Section [5](#summary).

![](figures/observation.png)

c c c c c c c c c c **Band** & **$\lambda$** & **$\sigma_{I}$** & **$\sigma_{PI}$** & **BMAJ** & **BMIN** & **BPA** & **Proj.code** & **P.I.** & **Reference**\
& (mm) & $\left(\frac{\mu \rm Jy}{\rm beam}\right)$ & $\left(\frac{\mu \rm Jy}{\rm beam}\right)$ & (arcsec) & (arcsec) & (deg) & & &\
(1) & (2) & (3) & (4) & (5) & (6) & (7) & (8) & (9) & (10)\
& 3.1 & 58 & 22 & 0.45 & 0.29 & $-12.8$ & 2016.1.00115.S & Kataoka, Akimasa & (I), (II), (III)\
6 & 1.3 & 170 & 37 & 0.33 & 0.24 & $-53.4$ & 2016.1.00162.S & Stephens, Ian & (II), (III)\
7 & 0.87 & 409 & 92 & 0.20 & 0.13 & $-80.9$ & 2019.1.01051.S & Stephens, Ian & (III)\

**Note** (1) Name of the observation band; (2) Central wavelength; (3) Noise level of Stokes $I$ emission; (4) Noise level of polarized emission; (5) Beam’s major axis; (6) Beam’s minor axis; (7) Beam’s position angle; (8) Project code; (9) Principal Investigator; (10) Associated reference.\
**References.** (I) (cite: 2017ApJ...844L...5K); (II) (cite: 2017ApJ...851...55S); (III) (cite: 2024MNRAS.528..843L).

# Dust and Disk Models

The outline of our model is briefly described as follows. Firstly, we construct a dust model and a best-fitted disk model to the Stokes $I$ emissions obtained by ALMA at the three wavelengths $\lambda$ = 3.1, 1.3, and 0.87$\,$mm. Then, by separately measuring direct thermal emission from grains aligned by MRAT and scattered emission from self-scattering[^1], we combine their Stokes parameters to obtain the combined linear polarization from the dust emission.

Figure [1](#observation) shows ALMA Stokes $I$ intensity overlaid with polarization vectors of HL Tau disk at $\lambda$ = 3.1, 1.3, and 0.87$\,$mm. The details of the information regarding the observational data used in this paper are summarized in Table [\[table::obs\]](#table::obs). The observational data is taken directly from the ALMA archive, which has been reduced and calibrated by ALMA staff. We only further perform de-biasing the polarized intensity and polarization degree via the method described in (cite: 2014ApJS..213...13H) and (cite: 2015JAI.....450005H). The ALMA minimum detectable polarization degree is expected at 0.1%, and defined as three times the systematic calibration uncertainty. Hence, we use the error of 0.033% when the polarization degree uncertainty is less than this value.

The notable features of the observations are (1) the transition of the polarization patterns from azimuthal to parallel to the disk’s minor axis from 3.1 to $0.87\,\rm mm$ and (2) the polarization degree is generally at the level of $\sim$1% for the whole three wavelengths.

## Dust Model

We adopt a dust model with compositions from (cite: 2018ApJ...869L..45B), where dust grains are a mixture of astronomical silicate, troilite, refractory organics, and water ice. The refractive index used in the calculation is from (cite: 2003ARA&A..41..241D) for astronomical silicate, (cite: 1996A&A...311..291H) for troilite, and (cite: 2008JGRD..11314220W) for refractory organics and water ice. Assuming compact grains, the mean refractive index of the mixture is then calculated with the effective medium theory using Bruggeman rule (cite: 1998asls.book.....B).

The grain sizes are assumed to follow a power-law distribution with a power index $q = -3.5$ (cite: 1977ApJ...217..425M), a maximum grain size $a_{\rm max}$, and a fixed minimum grain size $a_{\rm min}$ = 0.05 $\mu$m. We assume the grain population to be the same throughout the disk. As discussed in (cite: 2022MNRAS.512.3922L), the value of $a_{\rm max}$ does not converge for the three ALMA wavelengths (i.e., there is no single value could satisfy the polarization constraint at the three wavelengths at once). Therefore, we leave $a_{\rm max}$ as a wavelength-dependent parameter. We assume the Rayleigh regime (cite: 1985ApJ...290..211L) for the polarization calculation. This approximation holds when the size parameter $x\,=\,2\pi a/\lambda\,<<\,1$. Indeed, later on, this is shown to be the case with the maximum grain sizes found to be $\sim$60, 80, and 90$\,\mu$m for the three probing wavelengths 0.87, 1.3, and 3.1$\,$mm, respectively.

p8cm c c **Parameter** & **Denotation** & **Value**\
Dust mixture & - & silicate, organics, water ice, troilite\
Grain size distribution & dn/da & $Ca^{-3.5}$\
Minimum grain size & $a_{\rm min}$ & 0.05$\, \mu$m\
Maximum grain size & $a_{\rm max}$ & $\lambda$ - dependent\
Grain aspect ratio & $s$ & 1/2 (ray-tracing) or 1 (MCRT)\
Iron fraction of PM grains & $f_{\rm p}$ & 0.1\
Iron cluster volume filling factor of SPM grains & $\phi_{\rm sp}$ & 0.1\
Number of iron atoms per cluster of SPM grains & $N_{\rm cl}$ & \[ 20, $10^5$ \]\
IA efficiency at low-$J$ and slow INR & $Q_{\rm X,low-J}$ & $-0.4$ (wrong IA) or 0.4 (right IA)\
IA efficiency at high-$J$ and slow INR & $Q_{\rm X,high-J}$ & 0.4\

**Notes.** PM/SPM grains denote the grains made of paramagnetic/superparamagnetic materials. IA denotes internal alignment process, and INR denotes internal relaxation.

We assume two different grain shapes for direct thermal dust emission ray tracing and Monte-Carlo radiative transfer (MCRT) calculation (i.e., radiation field, radiative heating, and dust scattering calculations). For dust emission ray tracing, which is used to trace aligned grain emission, oblate grains with aspect ratio $s$ ($0<s<1$) are assumed. Note that grain shape has a strong effect on the degree of polarization. Grains with smaller $s$ are expected to produce higher polarization degrees. However, since the exact grain geometry in the disk environment is not yet constrained, we choose an average value of $s=1/2$ for simplicity. The grains’ optical properties including extinction and RAT efficiencies are then pre-calculated with DDSCAT (cite: 1994JOSAA..11.1491D). For the MCRT calculation, we adopt spherical grains (i.e., $s\,=\,$1), whose dust optical properties can be analytically calculated with Mie theory (cite: 2012mith.book...53W). Though the two-grain shapes are not consistent, we neglect the effect of scattering with non-spherical grains for simplicity. As pointed out by (cite: 2020A&A...638A.116K), assuming perfect compact spherical grains yields quantitative errors compared to non-spherical grains. However, the errors are negligible in the Rayleigh regime (i.e., spherical grains are still an acceptable representation).

Self-scattering-induced polarization is achieved by treating dust as photon emitters in dust scattering radiative transfer simulation. The controlling parameter of scattering is the maximum grain size, $a_{\rm max}$. Self-scattering polarization is most effective when $a_{\rm max}\,\sim\,\lambda/2\pi$ (cite: 2015ApJ...809...78K).

In the present work, grain alignment is considered to be induced only by MRAT. Under the framework of MRAT, grains can efficiently be aligned with magnetic fields owing to the enhanced efficiency by RATs and (super)paramagnetic relaxation due to iron inclusion within the grains (cite: 2008ApJ...676L..25L; 2016ApJ...831..159H). Recent observations show more evidence for iron inclusion in the form of clusters in different environments such as in protostellar core (cite: 2023MNRAS.520.3788G), filament (cite: 2023ApJ...953...66N), and the envelope of evolved stars (cite: 2023arXiv230801215T). RATs can spin grains up to suprathermal rotation (so-called high-$J$ attractors) or de-spin them down to thermal rotation (so-called low-$J$ attractors). Grains with iron inclusion are dubbed paramagnetic material (PM) or superparamagnetic material (SPM). Considering paramagnetic grains, we assign the value of the fraction of iron atoms diffusely distributed within grains as $f_{\rm p} = 0.1$. For superparamagnetic grains, we fix the volume filling factor of iron clusters to $\phi_{\rm sp}$ = 0.1, which corresponds to an iron abundance of $\sim$30% presented in the form of iron clusters[^2] and vary the number of iron atoms per cluster $N_{\rm cl}$ to describe different degree of grain alignment enhancement due to superparamagnetic relaxation. The possible value of $N_{\rm cl}$ spans from $\sim$ 20 to $10^5$ (cite: 1967ApJ...147..943J).

Note that for internal relaxation of grains, although the case of RATs quickly bringing $\boldsymbol{J}$ to align with $\boldsymbol{\hat{a_1}}$ (fast internal relaxation, (cite: 2021ApJ...908...12L)) has been well-studied, the case of internal relaxation timescale being much longer than gas damping timescale (slow internal relaxation) is not as well-defined (cite: 2022AJ....164..248H). Hence, in this study, for the case of slow internal relaxation, we fix the values of internal alignment efficiency $Q_{\rm X}$ as follows. When grains are aligned at high-$J$ attractors, the internal alignment efficiency is $Q_{\rm X,high-J}$ = 0.4. On the other hand, when grains are at low-$J$ attractors, they can be aligned at either right or wrong internal alignment (cite: 2009ApJ...697.1316H). In the case of right internal alignment, $\boldsymbol{J}$ is aligned parallel to $\boldsymbol{\hat{a_1}}$, which coincides with the minor axis of the ellipsoidal grains. In the case of wrong internal alignment, their alignment direction is perpendicular instead. When $Q_{\rm X,low-J} = -0.5$, grains are defined to achieve perfect wrong internal alignment (cite: 2023MNRAS.520.3788G). We set $Q_{\rm X,low-J}$ = 0.4 for the case of grains aligning at right internal alignment, and $Q_{\rm X,low-J} = -0.4$ at wrong internal alignment. The choice of the values of $Q_{\rm X,high-J}$ and $Q_{\rm X,low-J}$ at wrong internal alignment is taken as the median value of the constraint which will be given in Section [4.3](#sINR). The value of $Q_{\rm X,low-J}$ at right internal alignment is set to be similar to $Q_{\rm X,high-J}$ based on the assumption that $\boldsymbol{J}$ would have a negligible effect on the grains’ internal alignment efficiency when they are aligned with slow internal relaxation. Throughout the paper, we will call wrong internal alignment/right internal alignment for short in referring to the case of grains aligned with wrong or right internal alignment when they are at low-$J$ attractors and aligned with slow internal relaxation. The procedure to calculate the alignment degree of dust grains with magnetic fields in POLARIS is nicely summarized in Figure 2 of (cite: 2023MNRAS.520.3788G).

A summary of the critical parameters used in our dust model is given in Table [\[table::dust\]](#table::dust).

![](figures/obs_model.png)

## Disk Model

In this section, we construct an axisymmetric disk model that best reproduces Stokes $I$ images of the polarization observations at 3.1$\,$mm, 1.3$\,$mm, and 0.87$\,$mm, which corresponds to ALMA observation band 3, 6, and 7, respectively.

First, we assume a single radiation source to be the protostar at the disk center. The protostar has the effective temperature $T_{\star}$ = 4000 K and radius $R_{\star}=7R_\odot$, which corresponds to a luminosity $L_{\star}\sim$$11L_{\odot}$ (cite: 1999ApJ...519..257M; 2016ApJ...816...25P; 2017A&A...607A..74L). The radiation field and dust temperature within the disk are then calculated using radiative transfer calculation. Since temperature is a strong function of grain size, we fix $a_{\rm max}$ = 100 ${\mu}$m for temperature calculation to fix the disk’s temperature profile.

Next, we build the surface density profile for the disk. It is commonly estimated by using the spectral energy distribution (SED) fitting. However, it is only simple when the temperature profile is fixed or can be analytically approximated. In our study, the main source of the disk temperature is radiative heating requiring radiative transfer calculation which is computationally costly. Thus, for simplicity, we assume a surface density profile taken from (cite: 2011ApJ...741....3K), $$\begin{align}
    \Sigma \propto \left(\frac{R}{R_c}\right)^{-\gamma} \text{exp}\left[\left(\frac{R}{R_{\text{c}}}\right)^{2-\gamma}\right]\text{,}
\end{align}$$ where $R$ is the distance to the disk center, $R_{\rm c}$ = 78.9 AU and $\gamma = -0.2$. Note that the dust surface density profile is assumed to have a smooth radial distribution and ignore all the gaps and rings observed with higher spatial resolution in (cite: 2015ApJ...808L...3A); this is the case for the lower resolution of ALMA polarimetric observations that we are attempting to reproduce.

The vertical dust density is assumed to follow Gaussian distribution, $$\begin{align}
    \rho = \frac{\Sigma}{\sqrt{2\pi}h_{\rm d}} \text{exp}\left(\frac{-z^2}{2h_{\rm d}^2}\right),
\end{align}$$ where $z$ is the height from the disk midplane and $h_{\rm d}$ is the disk dust scale height whose profile is taken as $$\begin{align}
    h_{\rm d}(R) = h_{0}\left(\frac{R}{100\;\text{AU}}\right)^{\beta},
\end{align}$$ with $h_0$ = 10 AU being the scale height at 100$\,$AU from the center of the disk, and $\beta$ = 1.15 the exponent factor characterizing the flaring effect of the disk ((cite: 2016ApJ...816...25P; 2017A&A...607A..74L)). However, HL Tau was studied to have a high degree of dust settling based on the appearance of rings and gaps on millimeter observations (cite: 2016ApJ...816...25P). Dust settling is expected to have a significant effect on polarization due to self-scattering (cite: 2017MNRAS.472..373Y). Hence, in the calculation for self-scattering only, we take into account the effect of dust-settling by dividing the scale height $h_{\rm d}$ by a factor $f_{\rm settle}=10$, which is defined as the dust-settling factor from the disk scale height, following (cite: 2016ApJ...820...54K). In this calculation, the temperature distribution is taken identical to that from the radiative heating calculation with the original scale height. We assume that the disk geometrical thickness would have a minor effect on the intrinsic dust thermal emission at (sub)millimeter wavelength for simplicity.

Assuming the fiducial grain size of $a_{\rm max}$ = 100 ${\mu}$m, we take the total dust mass of the system $M_{\rm d}$ as a calibrating parameter to reproduce the three Stokes $I$ emissions at the three wavelengths mentioned earlier. $M_{\rm d}$ = $1.3\times10^{-2}M_{\odot}$ is found to be the best-fitted value, which produces total emissions comparable to the observations as shown in Figure [2](#obs_model). This value is similar to the level of $M_{\rm d} \sim 1\times10^{-2}M_{\odot}$ as estimated in (cite: 2021ApJ...908..153M) and (cite: 2023ApJ...953...96Z), in the case where grain size at $\sim100\,\mu$m is employed. Although the residuals are still significant, we stress that our aim is to reproduce axisymmetric continuum emissions for the whole three wavelengths with a simple model and ignore the asymmetries of the disk in the later modeling. Therefore, we will not further search for more optimal parameter sets. For the gas part, under the common assumption of gas-to-dust ratio equal to 100 (i.e., the typical value in the ISM), the total disk mass (gas+dust) would be $M_{\rm disk}\,\sim\,1.3\,M_{\odot}$. This total disk mass is similar to that of the central star ($M_{\star}\,=\,1.7\,M_{\odot}$, (cite: 2016ApJ...816...25P)), which would imply that the disk is extremely unstable and therefore, unrealistic. On the other hand, (cite: 2011ApJ...741....3K), (cite: 2017A&A...607A..74L), and (cite: 2019ApJ...883...71C) give the value of total dust mass is $M_{\rm d}\,=\,1\times10^{-3}M_{\odot}$. Assuming gas-to-dust ratio equal to 100, the value of total disk mass is $M_{\rm disk}\,=\,0.1\,M_{\odot}$, which is an order-of-magnitude lower than our estimated value and much more reasonable. Thus, to obtain the gas density, we normalize the density profile with $M_{\rm g}\,=\,0.1\,M_{\odot}$, which is equivalent to a gas-to-dust ratio equal to $\sim\,10$.

The radiation field and temperature profile resulting from radiative transfer calculation with this disk model are shown in Appendix [6](#radfield_app). We assume gas temperature to be the same as the dust temperature for simplicity.

Concerning the magnetic field, we assume that it is dominated by toroidal component as indicated in (cite: 2015A&A...574A..68F) with the strength’s profile as estimated in (cite: 2011ApJ...739...50B) assuming the accretion process within the disk is solely driven by magnetorotational instability in the active layer. $$\begin{align}
    B = 1.0\;\text{G} \times \left(\frac{\dot{M}}{10^{-8}\;M_\odot\;\text{yr}^{-1}}\right)^{-1/2}\left(\frac{R}{1\; \text{AU}}\right)^{-11/8}
\end{align}$$ where $\dot{M} = 1.6 \times 10^{-7} M_\odot\;\text{yr}^{-1}$ is the accretion rate measured by (cite: 2004ApJ...616..998W).

![](figures/pol_align.png)

# Numerical Results

## Effect of Grain Magnetic Properties on Disk Polarization

Here, we investigate the effect of grain magnetic properties on disk polarization due to the MRAT mechanism at $\lambda$ = 3.1$\,$mm with fiducial grain size $a_{\rm max}=100\;\mu$m. Note that although the same disk and dust models as described in Section [2](#model) are applied, we temporarily ignore the effect of self-scattering for this study.

In Figure [3](#align_result), we show the resulting polarization degree maps overlaid with polarization vectors considering three different scenarios of internal alignment. The different grain alignment scenarios considered in this section are summarised in Table [\[appen_alig\]](#appen_alig).

Initially, we examine the ideal scenario (top left panel) in which all grains have perfect internal alignment (i.e., the fraction of grains aligned at high-$J$ attractors is $f_{\rm high-J}\,=\,1$). In this case, grains are expected to have their longer axis aligned perpendicular to the toroidal magnetic field with optimal efficiency, which results in the radial polarization pattern with a very high polarization degree of up to the level of $\sim$10%.

In the subsequent scenarios, we take into account the effect of slow internal relaxation and enhanced (super)paramagnetic alignment by MRAT. We consider both cases of right and wrong internal alignment (middle and right panels). The effect of paramagnetic grains (top panels) and superparamagnetic grains with $N_{\rm cl}\;=\;10^3$ and $10^4$ (middle and bottom panels) are also included for comparison.

In the case of right internal alignment (middle panels), the polarization vectors are the same as in the ideal case, yet the polarization degree is significantly lower. When grains are made of paramagnetic material, the polarization degree is $\sim$0.01%. In this case, the alignment of very large grains is extremely weak and easily dwarfed by other mechanisms such as $k$-RAT (cite: 2017ApJ...839...56T). Hence, it would be impossible to observe such a disk polarization in reality. For superparamagnetic grains, the alignment is considerably more efficient (i.e., the polarization degree is two orders of magnitude higher than in the paramagnetic grains scenario). With increasing $N_{\rm cl}$, higher values of $f_{\rm high-J}$ (i.e., more efficient grain alignment) are expected due to increasing magnetic relaxation (cite: 2016ApJ...831..159H). However, when grains are aligned with slow internal relaxation in the same direction, their internal alignment efficiencies are the same whether at high-$J$ or low-$J$ attractors. Thus, the polarization degrees observed at $N_{\rm cl}\,=\,10^3\;\text{and}\;10^4$ are seemingly identical.

In the case of wrong internal alignment (right panels), the polarization morphology is more diverse. Grain alignment is weak for paramagnetic grains with polarization degrees as low as $\sim$0.01%. The polarization vectors show an azimuthal pattern owning to the inefficient internal alignment of grains’ $\boldsymbol{\hat{a_1}}$ perpendicular to $\boldsymbol{J}$ at low-$J$ attractors with slow internal relaxation and external alignment of $\boldsymbol{J}$ along $\boldsymbol{B}$. superparamagnetic grains, conversely, induce a higher polarization degree with increasing $N_\text{cl}$. However, the polarization pattern alters when we keep increasing $N_\text{cl}$. Indeed, the increased level of iron inclusion also causes the increased abundance of grains at high-$J$ attractors (i.e., higher $f_\text{high-J}$) and more efficient Barnett relaxation, which would drive them to have more efficient internal alignment with the grains’ longer axis being aligned perpendicular to the magnetic field. As a result, the polarization vectors would eventually have the radial direction when $N_{\rm cl}\;=\;10^4$.

colspec=\|\>m1.4cm\|c\|c c c\| && Grain Alignment Model &&\
& & perfect IA & right IA & wrong IA\
Grain Magnetic Property & $\chi\,\sim\,\infty$ & Ideal & &\
& PM grains & & rIA, PM & wIA, PM\
& SPM grains ($N_{\rm cl}\,=\,10^3$) & & rIA, SPM, $N_{\rm cl}\,=\,10^3$ & wIA, SPM, $N_{\rm cl}\,=\,10^3$\
& SPM grains ($N_{\rm cl}\,=\,10^4$) & & rIA, SPM, $N_{\rm cl}\,=\,10^4$ & wIA, SPM, $N_{\rm cl}\,=\,10^4$\

**Notes**. $\chi$ is the grain magnetic susceptibility, which takes a very large value for the ideal case. Grain alignment models right IA/wrong IA denotes the models where grains are aligned with right internal alignment/wrong internal alignment when they are at low-$J$ attractors and slow internal relaxation.

colspec=\|\>m1.2cm\|c c\|c c\|c c\|c c\| &&& **Grain Magnetic Property (SPM)** &&\
&&& $N_{\rm cl}\,=\,10^2$ && $N_{\rm cl}\,=\,9\,\times\,10^2$ && $N_{\rm cl}\,=\,10^4$ &\
**Grain Size** & $\lambda\,=\,3.1\,$mm & $a_{\rm max}\,=\,50\,\mu$m & 0.91 & 0.24 & 0.85 & 0.61 & $-0.77$ & 1.77\
&& $a_{\rm max}\,=\,90\,\mu$m & 0.61 & 0.03 & **0.93** & **0.69** & $-0.76$ & 2.18\
&& $a_{\rm max}\,=\,200\,\mu$m & 0.07 & $-0.26$ & 0.39 & $-0.34$ & $-0.52$ & 1.83\
& $\lambda\,=\,1.3\,$mm & $a_{\rm max}\,=\,50\,\mu$m & 0.91 & 0.24 & 0.86 & 0.25 & $-0.22$ & $-0.44$\
&& $a_{\rm max}\,=\,80\,\mu$m & 0.83 & 0.38 & **0.93** & **0.63** & 0.17 & $-0.82$\
&& $a_{\rm max}\,=\,100\,\mu$m & 0.84 & 0.52 & 0.87 & 0.64 & 0.50 & $-0.38$\
& $\lambda\,=\,0.87\,$mm & $a_{\rm max}\,=\,50\,\mu$m & 0.97 & 0.04 & 0.93 & 0.06 & 0.58 & $-0.87$\
&& $a_{\rm max}\,=\,60\,\mu$m & 0.97 & 0.06 & **0.93** & **0.09** & 0.77 & $-0.57$\
&& $a_{\rm max}\,=\,100\,\mu$m & 0.88 & 0.50 & 0.82 & 0.30 & 0.93 & 0.85\
&&& $\overline{AM}$ & $c_{\rm P}$ & $\overline{AM}$ & $c_{\rm P}$ & $\overline{AM}$ & $c_{\rm P}$\

**Notes**. We only consider superparamagnetic (SPM) grains in the model. Each column represents the model with a different value of the number of iron atoms per cluster ($N_{\rm cl}$). Each row represents the model with different grain sizes at each wavelength. Each model with a couple value of $N_{\rm cl}$ and $a_{\rm max}$ has two validating factors $\overline{AM}$ and $c_{\rm P}$. $\overline{AM}$ is the average value of alignment measure across the image. $c_{\rm P}$ is the correlation factor of pixel-by-pixel polarization degree between the models and observations. The closer the values of $\overline{AM}$ and $c_{\rm P}$ to unity, the better the model compared to the observations.

![](figures/result.png)

Note that the features of disk polarization only induced by grain alignment observed above also hold for observations at both wavelengths $\lambda = 1.3$ and 0.87$\,$mm.

## Mixture of MRAT Grain Alignment and Self-scattering: Final Results

(cite: 2021ApJ...908..153M) concluded that a superposition of azimuthally aligned grains and self-scattering can produce the HL Tau disk polarization. In the previous Section [3.1](#ncl_pol_result), we demonstrate that only the grain alignment model of wrong internal alignment with superparamagnetic grains having $N_{\rm cl}$ at the level of $\sim$$10^3$ can produce the azimuthal polarization morphology and the polarization degree at $\sim$1%, which are ones of the notable features of the observations and in line with the description from the literature. Hence, in this section, we limit our grain alignment model to this scenario and add the effect of self-scattering to reproduce the observational data.

To validate the agreement between models and observations, we compare separately their polarization degree and polarization patterns. We check the pixel-by-pixel correlation for the polarization degree ($c_{\rm P}$) while computing the Alignment Measure ($AM$) as introduced in (cite: 2017ApJ...835...41G) to compare the polarization orientation. $$\begin{align}
    AM = 2\left(\text{cos}^{2}\theta_\text{r}-\frac{1}{2}\right),
\end{align}$$ where $\theta_\text{r}$ = $|\theta_\text{mod}\;-\;\theta_\text{obs}|$ is the angle difference between the model and observation. The scale of $AM$ is from $-1$ to 1, where $AM=1$ corresponds to a perfect match of polarization vectors and $AM=-1$ indicates that the two vectors are perpendicular to each other. We then take its average value across the image $\overline{AM}$ to represent the overall correlation between polarization vectors of the model and observations. Finally, the values of $c_{\rm P}$ and $\overline{AM}$ are compared between each model to find the best model for the observations. Note that the closer the values of $c_{\rm P}$ and $\overline{AM}$ to unity, the better the agreement between the model and the observations. Table [\[MOP\]](#MOP) summarizes the values of $c_{\rm P}$ and $\overline{AM}$ of the typical models that we considered.

As shown in Table [\[MOP\]](#MOP), the model that best reproduces the disk polarization observed by ALMA is found at $N_{\rm cl}=9\times 10^2$; $a_{\rm max}=$ 90, 80, and 60 $\mu$m for $\lambda$ = 3.1, 1.3, and 0.87$\,$mm, respectively. The disk polarization corresponding to this model is displayed in Figure [4](#final_result). As expected, very large grains with wrong internal alignment produce azimuthal polarization vectors with strong polarization degrees along the major axis while self-scattering produces both polarization vectors and strong polarization degrees along the disk minor axis. Furthermore, as the probing wavelength decreases, the optical depth of the disk increases, which induces a weaker polarization signature from grain alignment due to dichroic extinction (cite: 2022MNRAS.512.3922L). As a result of their superposition at different wavelengths, the polarization shows a transition from azimuthal to parallel to the disk minor axis patterns as in the observations.

# Discussions

## Comparison to Previous Studies and Implications

Since ALMA’s first polarimetric detection of HL Tau (cite: 2014Natur.514..597S), there have been many observational and theoretical studies aiming to understand the diversity of dust polarization observed toward the disk. Using the RAT alignment theory, (cite: 2017ApJ...839...56T) first performed a theoretical study of grain alignment in protoplanetary disks and concluded that magnetic alignment is impossible for mm-sized grains in this environment, even with a high degree of iron inclusion, consistent with predictions in (cite: 2016ApJ...831..159H). The authors suggested that such large grains can be aligned via radiation direction (i.e., $k$-RAT, (cite: 2007MNRAS.378..910L)), which can produce the observed azimuthal polarization pattern. However, (cite: 2017ApJ...839...56T) assumed the right internal alignment for very large grains with slow internal relaxation, but their wrong internal alignment cannot be ruled out (cite: 2022AJ....164..248H). In this paper, our detailed modeling for HL Tau using the updated POLARIS shows that the disk polarization can be reproduced with magnetic alignment via the MRAT mechanism, but very large grains with slow internal relaxation must have wrong internal alignment. Therefore, dust polarization can still trace the magnetic field within protoplanetary disks. Moreover, due to the wrong internal alignment, the polarization vectors are along the magnetic field direction, so that one does not need to rotate the polarization vectors by $90^{\circ}$ to infer the magnetic field, as in the case of right internal alignment.

However, (cite: 2019MNRAS.483.2371Y) and (cite: 2021ApJ...908..153M) modeled the HL Tau polarization observed at ALMA Band 3 ($\lambda$ = 3.1$\,$mm) and concluded that $k$-RAT could not explain its polarization pattern, which turns out to be more delicate being elliptical, namely the polarization radiation is required to be emitted only in the disk plane. Therefore, the authors suggest that the HL Tau polarization could be reproduced by effective prolate grains that are aligned with their major axis along the azimuthal direction. However, the reason why the grains could be aligned in such a way is not discussed. In our detailed modeling, such a scenario is the outcome of grain alignment physics in which the grains’ longer axes are aligned along their angular momenta due to wrong internal alignment for grains with slow internal relaxation, and the grains’ angular momenta are aligned along the direction of the toroidal magnetic field as a result of enhanced superparamagnetic relaxation and Larmor precession for grains with embedded iron inclusions.

(cite: 2020A&A...634L..15G) proposed that in the Mie regime ($\rm x\,=\,2\pi a/\lambda\,\sim\,1$), the polarized emission can turn into a negative value, which results in the polarization vectors parallel to the toroidal magnetic field for elongated spheroidal grains aligned with right internal alignment. This idea can provide an alternative to our model in explaining the azimuthal polarization pattern observed in the disk. However, the persistence of the azimuthal polarization pattern across a large range of wavelength, from $\lambda\,=\,0.87\,$mm up to $7\,$mm (cite: 2023MNRAS.520.1210L), means that they must all be well within the Mie regime, or the effective grain size must be up to $a_{max}\,\sim\,1\,$mm. This is in contradiction with our constrained grain size where they are only placed at $\sim\,100\,\mu$m-scaled. Hence, the grain size constraint would have implications in determining whether the ALMA observations are in the Rayleigh or Mie regime. Alternatively, it is also worth noticing that as soon as $\rm \lambda\,>\,2\pi a$, the polarized emission of aligned grains is predicted to become positive. Therefore, observing whether there is a polarization flip to a radial pattern at a shorter wavelength than 0.87$\,$mm or longer than 7$\,$mm can help further clarify which is the correct explanation for the observed disk polarization.

In addition to the polarization properties, grain growth in HL Tau has also been in the spotlight due to the conflict of its constraint from polarization degree and spectral index of thermal emission (cite: 2021ApJ...908..153M; 2021ApJ...913..117U; 2023MNRAS.520.1210L; 2023ApJ...953...96Z). Earlier in the current study, $a_{\rm max}$ was constrained to be different when probing at different wavelengths (90$\,\mu$m, 80$\,\mu$m, and 60$\,\mu$m at $\lambda\,=\,\text{3.1}\,$mm, 1.3 mm, and 0.87$\,$mm, respectively). However, they are all at $\sim\,100\,\mu$m, which is still greatly differs from the 1 mm grain size constrained from spectral index SED fitting. Further discussions are presented in Section [4.5](#grainsizepop).

## Constraints on Iron Abundance within Grains in the form of Clusters

Our results in Section [3](#sec:results) show that paramagnetic grains produce a very low polarization degree, $\sim$0.01%, which is much lower than the observed polarization level. On the contrary, grains with embedded iron clusters can produce the observed polarization level. Therefore, iron atoms are unlikely distributed diffusely inside dust grains, but must be present in the form of iron clusters.

In Section [3](#sec:results), for convenience, we fixed the value of $\phi_{\rm sp}$ = 0.1 and varied $N_\text{cl}$ to obtain the different magnetic susceptibility of grains (see e.g. Equation 3 in (cite: 2023MNRAS.520.3788G)). In this section, we treat $\phi_{\rm sp}$ as a free parameter to investigate its effect on disk polarization. For simplicity, we test the effect using $q'_{100}$, which is the polarization degree of Stokes $Q$ in the principal frame at the radius of 100 AU along the disk minor axis. A principal frame is a frame whose ordinate coincides with the disk minor axis. In this way, $q'_{100}$ would have a positive value when the polarization vector is radial and negative when it is azimuthal. We demonstrate the effect at $\lambda$ = 3.1$\,$mm, where alignment is expected to be the dominant component over self-scattering. The value of $-q'_{100}=1.95$ due to the alignment component as decomposed in (cite: 2022MNRAS.512.3922L) will be chosen as the reference value. An error of 0.5$\%$ is assigned to represent the uncertainty of the method.

The demonstration is shown in the top panel of Figure [5](#pqx). Generally, at each value of $\phi_\text{sp}$, the curve describing the dependence of $-q'_{100}$ on $N_\text{cl}$ follows a parabolic shape. The reason behind this is as described in Section [3.1](#ncl_pol_result) in which increased $N_\text{cl}$ not only increases polarization degree through enhancing external alignment but also increases $f_\text{high-J}$ which drives polarization vector from azimuthal to radial direction. The value of $-q'_{100}$ is at its peak when the effect of superparamagnetic alignment from $N_\text{cl}$ is not negligible so that grains can efficiently align with the magnetic field, yet not too significant so that $f_\text{high-J}$ is small enough to keep the polarization vectors at the azimuthal direction. With the higher value of $\phi_\text{sp}$, this peak shifts to the position corresponding to the lower value of $N_\text{cl}$.

![](figures/PQX.png)

This test puts a constraint on $\phi_{\rm sp}$ with its minimum value at $\sim$0.05, which corresponds to $\sim$16% of iron locked inside grains in the form of cluster. Finally, it is crucial to point out that not only our constrained value of $N_{\rm cl}\sim 9 \times 10^2$ is consistent with the $-q'_{100}$ reference when considering $\phi_{\rm sp}$ = 0.1 as in our dust model, but the range of $N_{\rm cl}$ is also found to be at $\sim$$2 \times 10^2$ - $2 \times 10^3$ within the valid values of $\phi_{\rm sp}$.

## Constraints on Internal Alignment Efficiency for Slow Internal Relaxation

Slow internal relaxation is generally responsible for internal alignment of large dust grains within protoplanetary disks since large grains above $\sim$10 $\mu$m and high density are ubiquitous in these environments (cite: 2022ApJ...928..102H). However, the efficiency of internal alignment for the case of slow internal relaxation is not yet available from theory (cite: 2009ApJ...697.1316H; 2022AJ....164..248H). Usually, the efficiency of internal alignment by slow internal relaxation is represented by two quantities $Q_{\rm X,low-J}$ and $Q_{\rm X,high-J}$. In Section [3](#sec:results), our modeling results showed that $Q_{\rm X,low-J}$ must have a negative value (i.e., wrong internal alignment) to reproduce the azimuthal polarization pattern observed toward the HL Tau disk. On the contrary, grains at high-$J$ attractors always have the right internal alignment or $Q_{\rm X,high-J}$ is always positive (cite: 2009ApJ...697.1316H). It indicates that the directions of internal alignment of grains aligned at low-$J$ and high-$J$ attractors are opposite.

Here, we will attempt to empirically constrain the magnitude of $Q_{\rm X,low-J}$ and $Q_{\rm X,high-J}$ for slow internal relaxation using the observed polarization data. To do so, we consider the extreme scenarios where parameters involved in the internal alignment process are set to their respective extremes. We initially fix $\phi_{\rm sp}=\phi_\text{sp,max}=0.3$. To obtain the maximum value of $|Q_{\rm X,high-J}|$, we set $|Q_{\rm X,low-J}|=|Q_{\rm X,low-J,max}|=0.5$. On the other hand, $|Q_{\rm X,high-J}|=|Q_{\rm X,high-J, min}|\sim$ 0.01 is set to constrain the minimum value of $|Q_{\rm X,low-J}|$. Following Section [4.2](#sphisp), we use $-q'_{100}$ at $\lambda=3.1$ mm as the referenced polarization degree for the disk polarization. Its value is calculated for different values of $Q_{\rm X,high-J}$ or $Q_{\rm X,low-J}$ and over the range $N_{\rm cl}$ = \[$10^2$, $10^4$\]. The plots are shown in the middle and bottom panels of Figure [5](#pqx). By considering the values satisfying the reference value, we can deduce the maximum possible value of $|Q_{\rm X,high-J}|$ is $\sim$0.8, while the minimum value of $|Q_{\rm X,low-J}|$ is at $\sim$0.15.

## Other Grain Alignment Mechanisms

Besides MRAT, grain alignment due to interaction of the gas flow and grains, including Gold alignment (cite: 1952MNRAS.112..215G) and mechanical torque (MET) alignment with the grain’s long axis along the flow velocity (so-called $v$-MET; (cite: 2022AJ....164..248H)) can also produce an azimuthal polarization pattern.

Gold alignment was thought to be the most promising mechanism to explain the polarization morphology caused by grain alignment in HL Tau (cite: 2019MNRAS.483.2371Y). However, the possibility of the Gold mechanism causing grain alignment in disk environments is highly questionable (cite: 2021ApJ...908..153M). Since the mechanism requires supersonic gas speed to have effectively aligned grains, whereas it is generally subsonic in protoplanetary disks (cite: 2007ApJ...669.1085C), it is unlikely to induce grain alignment within this environment.

$v$-MET, on the other hand, offers a rather promising alternative. If grains with Keplerian motions align with the drift direction with wrong internal alignment, the polarization pattern is also expected to be azimuthal (cite: 2022AJ....164..248H). However, it may not be the case if we take a more thorough inspection. The polarization direction depends on the direction of gas flow in the frame of dust grains, which is a strong function of Stokes number denoting how well dust grains couple to ambient gas. With $a_{\rm max} \sim 100$ $\mu$m, and assuming a gas surface density of $\Sigma_{\rm g}\,\sim$ 5 g cm$^{-2}$, the Stokes number is estimated to be $St \sim 5.4 \times 10^{-3}$. This value is much smaller than unity which indicates that the direction of gas velocity with respect to the grains will be radial (see Figure 2 in (cite: 2019ApJ...874L...6K)). In the case of right internal alignment, a circular polarization pattern is produced. On the other hand, if grains are aligned with the wrong internal alignment, the pattern will be radial. Both cases are not compatible with the elliptical patterns from observations (cite: 2019MNRAS.483.2371Y). Note that the argument still holds even when considering grain size up to 1 mm as constrained in (cite: 2019ApJ...883...71C), which corresponds to $St \sim 5.4 \times 10^{-2} \ll 1$.

Nevertheless, it is crucial to stress that we cannot rule out the possibility of enhanced alignment with grain drift (cite: 2022AJ....164..248H), which is neglected in our model. Since the direction of gas flow with respect to the grains is radial, which coincides with the direction of the radiation beam, the combined effect of grain drift and radiation can significantly improve the efficiency of grain alignment within the disk.

In conclusion, it has been demonstrated that MRAT is the only grain alignment mechanism in the constraint of current understanding on grain alignment theory that can explain the polarization signatures observed in the HL Tau disk by ALMA.

## Grain Size Population

Grain size was constrained primarily from the dust polarization of the self-scattering component. Therefore, in order to address the detailed view of the grain size constraint given in Section [3](#sec:results), we provide the polarization efficiency from dust scattering of each dust model, as a function of wavelength in Figure [6](#POmega). Polarization efficiency is represented by the polarization degree at $90^{\circ}$ scattering times the albedo P$\rm \omega$ following (cite: 2015ApJ...809...78K).

![](figures/POmega.png)

We could reproduce the observed dust polarization assuming that the three wavelengths trace different layers of the disk, which contain grains of discrete sizes. In the optically thick region of HL Tau, this is the case because the differential dust-settling effect can cause light at different wavelengths to trace different layers of the disk with longer wavelengths leaning towards the disk midplane where larger grains are expected to be present (cite: 2020A&A...640A.122B; 2021ApJ...913..117U). Indeed, the grain size in our results is constrained at larger values when tracing the dust by longer wavelengths, namely $a_{\rm max}$ = 60, 80, and 90$\,\mu$m at $\lambda$ = 0.87, 1.3, and 3.1$\,$mm, respectively.

However, this argument is only valid at the optically thick inner region of the disk. The optical depth would decrease with the radial distance from the disk center. Thus, the dust differential settling effect would have a weaker impact on the outer region. Irregular grain structures have been studied to alleviate the grain size conflict between polarization and spectral index SED fitting (cite: 2023MNRAS.520.1210L; 2023ApJ...953...96Z). Moreover, it offers a promising explanation for the spectral dependence of the polarization degree across (sub)millimeter wavelengths as in Figure [6](#POmega). According to the literature, grain size can be larger than 1$\,$mm depending on the grain porosity. Furthermore, grains with large porosity have less steeper-slope spectral dependence of scattering efficiency, which generates a similar trend for polarization degree resulted from self-scattering. Therefore, it is crucial to incorporate the effect of grain porosity into detailed modeling of grain alignment to have a more complete picture of HL Tau polarization.

## Disk Polarization with Substructures

Previously in our original disk model in Section [2.2](#diskmodel), the disk is assumed to have a smooth radial density distribution. However, (cite: 2015ApJ...808L...3A) has revealed that the disk contains an alternate distribution of rings and gaps, which is a crucial sign for planet formation. (cite: 2023Natur.623..705S) are recently able to detect the dust polarization within the substructures at $\lambda\,=\,0.87\,$mm and find the distinguishable features observed in gaps compared to the rings. In the gaps, the authors find the polarization vectors to be azimuthal with a higher polarization degree (up to $\sim$4%) than within the rings. This is understandable considering within the gaps, the optical depth is at unity, which induces a higher polarization degree due to self-scattering (up to $\sim$3%, (cite: 2016ApJ...820...54K)). The lower dust opacity also induces lower dichroic extinction, which means a higher polarization degree of the intrinsic emission from aligned grains. The lower gas density in the gaps is also expected to make the grain alignment process more efficient with less effective gas damping (cite: 2022AJ....164..248H). However, too low gas density may also induce more grains aligning with fast internal relaxation and lower the degree of azimuthal polarization. This essentially signifies the importance of having accurate gas density for polarization calculation. Furthermore, with lower gas density, dust and gas are expected to couple more efficiently and the effect of grain alignment due to grain drift would be non-negligible. We attempt to model the disk with substructures in Appendix [7](#appen::gap). However, it is only a rough estimation and cannot reproduce the entire detailed polarimetric observation as in (cite: 2023Natur.623..705S). One of which is the high polarization degree at the gaps, where their further modeling suggests that the intrinsic polarization could be up to 10-15$\,\%$ without beam smearing effect. This is potentially because the dust vertical settling effect has not been taken into account, which ignores the larger grain size being probed in the gaps due to less opacity. The gas-to-dust ratio contrast in these gaps and rings is also still uncertain (cite: 2016ApJ...816...25P; 2019ApJ...880...69Y) and the simple assumption of constant gas-to-dust ratio throughout the disk is no longer acceptable. The accumulation of magnetic field inside the gaps also needs to be considered if they were formed due to magneto-hydrodynamic (MHD) effects (cite: 2015A&A...574A..68F). Moreover, the effect of mechanical torque alignment (cite: 2022AJ....164..248H) has not been taken into account. Its incorporation into modeling still faces difficulty due to its significant sensitivity to grain shape (cite: 2023A&A...674A..47R). Hence, additional studies are needed to fully reproduce the high-resolution HL Tau dust polarization observed by ALMA.

## Caveats

Our model is subject to the unresolved grain shape inconsistency. While we calculate the direct polarized thermal emission from aligned elongated dust grains, spherical grains are used in the MCRT calculations. This is due to the difficulties in computing the optical properties of non-spherical dust grains, especially its scattering property.

The assumed geometrically thick disk in intrinsic dust thermal emission calculation may cause unwanted near-far side asymmetry in the disk emission at optically thick region due to more dichroic extinction in the near side of the disk. However, we ignore this effect due to the nature of our simple disk model setup and the preferred need to use a precise approximation of the radiation field and gas density for grain alignment calculation.

# Summary

The origin of the polarized emission of HL Tau at different wavelengths has been debated in previous studies. In this work, through our detailed multi-wavelength modeling, the following results are found.

1.  The ideal scenario of magnetic alignment significantly overestimates the polarization degree compared to the realistic cases. In the realistic scenario, especially when grains are aligned at low-$J$ attractors with slow internal relaxation, grains can either align with wrong or right internal alignment, which manifests in azimuthal or radial polarization patterns, respectively. Additionally, paramagnetic grains cannot reproduce the observed polarization data and thus cannot be the primary dust material in HL Tau.

2.  A mixture of self-scattering and MRAT grain alignment mechanism where grains are aligned with wrong internal alignment at low-$J$ attractors and slow internal relaxation can reproduce the dust polarization observed in HL Tau by ALMA at (sub)millimeter wavelengths.

3.  Grains are shown to be made of superparamagnetic materials with the number of iron atoms inside each cluster is $N_{\rm cl} \sim 9\times10^2$. The abundance of embedded iron inside grains identified from our model is at $\sim$16% minimum.

4.  By assuming grain sizes probed to be $\lambda$-dependent, maximum grain sizes are constrained at $a_{\rm max} \sim$ 60, 80, and 90$\,\mu$m when probing at $\lambda$ = 0.87, 1.3, and 3.1$\,$mm, respectively.

5.  MRAT is found to be the only mechanism in the contemporary grain alignment theory that can explain the polarization morphology caused by the grain alignment component within the HL Tau disk.

# Acknowledgements

We thank the anonymous referee for his/her constructive comments that helped improve the presentation of this paper. We thank Ph.D. candidate Nguyen Chau Giang (KASI) for providing the updated POLARIS and significant discussion about the code along with its embedded grain alignment physics. N.T.T. is supported by a grant from the Simons Foundation to IFIRSE, ICISE (916424, N.H.). N.T.P. and P.N.D. are funded by Vingroup Innovation Foundation (VINIF) under project code VINIF.2023.DA.057. N.B.N. was funded by the Master, Ph.D. Scholarship Programme of Vingroup Innovation Foundation (VINIF), code VINIF.2023.TS077.

This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2016.1.00115.S, ADS/JAO.ALMA$\#$2016.1.00162.S,

ADS/JAO.ALMA$\#$2019.1.01051.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

# Software

POLARIS

# Radiation Field and Dust Temperature

With the radiation source at the disk center, the radiation flux $J_{\rm rad}$, spectrum weighted wavelength $\overline{\lambda}$, and anisotropy parameter $\overline{\gamma}$ (defined in (cite: 2007ApJ...663.1055B)) are calculated and illustrated in Figure [7](#rad_field).

While stellar radiation dominates the upper layers of the disk, the inner disk region is dominated by emission from warm dust from the surface and intermediate layers. The upper layers of the disk correspond to the disk photosphere, where it can be observed with IR/NIR observations. The inner disk region, on the other hand, can be traced by radio observations, which is the case in our modeling. Calculations show that the radiation at this region is dominated at $\overline{\lambda}\sim$ 140$\;\mu$m, with anisotropy parameter $\overline{\gamma}\sim 0.1$. Therefore, only about 10$\%$ of the radiation flux primarily at $\overline{\lambda}$ $\sim$ 140 $\mu$m can contribute to RATs towards the grains within the disk because only the anisotropic radiation is important for RAT alignment.

In our model, we also use radiative heating to calculate the temperature profile of the disk. Our radiative transfer calculation yields a temperature profile at the disk mid-plane of

$$\begin{align}
    T(R) = 347\left(\frac{R}{1\,\text{AU}}\right)^{-0.64}~{\rm K}.
\end{align}$$

![](figures/rad_field.png)

# Disk model with ring/gap structures

Throughout this work, we adopted the smoothed structure of the HL Tau disk. However, (cite: 2023Natur.623..705S) reported ring and gap structures with the new ALMA observations. They found that the polarization degree is much higher in the gaps than in the rings, and the polarization vectors are azimuthal.

This section aims to understand this newly observed phenomenon based on the same physical model. We first mimic the disk structure at $\lambda\,=\,0.87\,$mm as in (cite: 2023Natur.623..705S), which yields the surface density profile $$\begin{align}
    \Sigma \propto \Sigma_{a}\left(\frac{R}{R_0}\right)^{-p} \text{exp}\left[-\left(\frac{R}{R_{\text{c}}}\right)^{1.5}\right] + \sum_{i=1}^{N} \Sigma_{i}\,\text{exp}\left[-\frac{1}{2}\left(\frac{R-C_{i}}{W_{i}}\right)^2 \right] \text{,}
\end{align}$$ where $\Sigma_{a}\,=\,2.3$, $R_{0}\,=\,10\,$AU, $p\,=\,0.5$, and the parameters for the rings are given in Table [\[table::gap\]](#table::gap). In this investigation, instead of using temperature calculated from radiative transfer calculation, for simplicity, we adopt directly the temperature profile as in the literature: $T(R)\,=\,110\,\times\,[R/(10\,AU)]^{-0.5}$. We then normalize the dust density by the total dust mass of $M_{\rm d} \sim 5 \times 10^{-3} M_{\odot}$ to produce a comparable Stokes $I$ emission at $\lambda = 0.87$ mm as in (cite: 2023Natur.623..705S). The gas density, on the other hand, is obtained by normalizing the density profile with the total gas mass of $M_{\rm g}\,=\,0.1\,M_{\odot}$ similar to that done in Section [2.2](#diskmodel). This is equivalent to a gas-to-dust ratio of $\sim\,20$.

| Ring number | $\Sigma_{i}$ | $C_{i}$ \[AU\] | $W_{i}$ \[AU\] |
|:-----------:|:------------:|:--------------:|:--------------:|
|      1      |      8       |       24       |       4        |
|      2      |      5       |       39       |       3        |
|      3      |      5       |       49       |       3        |
|      4      |      8       |       59       |       2        |
|      5      |      3       |       73       |       4        |
|      6      |      8       |       88       |       3        |
|      7      |      8       |      102       |       2        |
|      8      |      8       |      116       |       2        |

For the polarization calculation, we adopt the same dust models as constrained in Section [3.2](#resultf) with $N_{\rm cl}=9 \times 10^2$, and $a_{\rm max}=60\,\mu$m. The predicted polarization degree and polarization angles with the ring/gap disk are shown in Figure [8](#fig::gap). Even with the simple dust model, we can spot differences between the polarization observed in the rings and gaps. In the gaps, we found that the polarization degree is higher, and the polarization caused by the self-scattering component becomes less dominant, resulting in a more azimuthal polarization pattern. These features are consistent with the new observations in HL Tau.

![](figures/gap.png)

natexlab

(ref: 2015ApJ...808L...3A) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3, doi: [`10.1088/2041-8205/808/1/L3`](http://doi.org/10.1088/2041-8205/808/1/L3)

(ref: 2015ARA&A..53..501A) Andersson, B. G., Lazarian, A., & Vaillancourt, J. E. 2015, ARA&A, 53, 501, doi: [`10.1146/annurev-astro-082214-122414`](http://doi.org/10.1146/annurev-astro-082214-122414)

(ref: 2011ApJ...739...50B) Bai, X.-N. 2011, ApJ, 739, 50, doi: [`10.1088/0004-637X/739/1/50`](http://doi.org/10.1088/0004-637X/739/1/50)

(ref: 1991ApJ...376..214B) Balbus, S. A., & Hawley, J. F. 1991, ApJ, 376, 214, doi: [`10.1086/170270`](http://doi.org/10.1086/170270)

(ref: 1998RvMP...70....1B) —. 1998, Reviews of Modern Physics, 70, 1, doi: [`10.1103/RevModPhys.70.1`](http://doi.org/10.1103/RevModPhys.70.1)

(ref: 2007ApJ...663.1055B) Bethell, T. J., Chepurnov, A., Lazarian, A., & Kim, J. 2007, ApJ, 663, 1055, doi: [`10.1086/516622`](http://doi.org/10.1086/516622)

(ref: 2018ApJ...869L..45B) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45, doi: [`10.3847/2041-8213/aaf743`](http://doi.org/10.3847/2041-8213/aaf743)

(ref: 1982MNRAS.199..883B) Blandford, R. D., & Payne, D. G. 1982, MNRAS, 199, 883, doi: [`10.1093/mnras/199.4.883`](http://doi.org/10.1093/mnras/199.4.883)

(ref: 1998asls.book.....B) Bohren, C. F., & Huffman, D. R. 1998, Absorption and Scattering of Light by Small Particles (Wiley-VCH)

(ref: 2020A&A...640A.122B) Brunngräber, R., & Wolf, S. 2020, A&A, 640, A122, doi: [`10.1051/0004-6361/202037981`](http://doi.org/10.1051/0004-6361/202037981)

(ref: 2019ApJ...883...71C) Carrasco-González, C., Sierra, A., Flock, M., et al. 2019, ApJ, 883, 71, doi: [`10.3847/1538-4357/ab3d33`](http://doi.org/10.3847/1538-4357/ab3d33)

(ref: 2007ApJ...669.1085C) Cho, J., & Lazarian, A. 2007, ApJ, 669, 1085, doi: [`10.1086/521805`](http://doi.org/10.1086/521805)

(ref: 2018ApJ...855...92C) Cox, E. G., Harris, R. J., Looney, L. W., et al. 2018, ApJ, 855, 92, doi: [`10.3847/1538-4357/aaacd2`](http://doi.org/10.3847/1538-4357/aaacd2)

(ref: 1951ApJ...114..206D) Davis, Leverett, J., & Greenstein, J. L. 1951, ApJ, 114, 206, doi: [`10.1086/145464`](http://doi.org/10.1086/145464)

(ref: 1976Ap&SS..43..291D) Dolginov, A. Z., & Mitrofanov, I. G. 1976, Ap&SS, 43, 291, doi: [`10.1007/BF00640010`](http://doi.org/10.1007/BF00640010)

(ref: 2003ARA&A..41..241D) Draine, B. T. 2003, ARA&A, 41, 241, doi: [`10.1146/annurev.astro.41.011802.094840`](http://doi.org/10.1146/annurev.astro.41.011802.094840)

(ref: 1994JOSAA..11.1491D) Draine, B. T., & Flatau, P. J. 1994, Journal of the Optical Society of America A, 11, 1491, doi: [`10.1364/JOSAA.11.001491`](http://doi.org/10.1364/JOSAA.11.001491)

(ref: 1997ApJ...480..633D) Draine, B. T., & Weingartner, J. C. 1997, ApJ, 480, 633, doi: [`10.1086/304008`](http://doi.org/10.1086/304008)

(ref: 2003A&A...411..623F) Fendt, C. 2003, A&A, 411, 623, doi: [`10.1051/0004-6361:20034154`](http://doi.org/10.1051/0004-6361:20034154)

(ref: 2015A&A...574A..68F) Flock, M., Ruge, J. P., Dzyurkevich, N., et al. 2015, A&A, 574, A68, doi: [`10.1051/0004-6361/201424693`](http://doi.org/10.1051/0004-6361/201424693)

(ref: 2023MNRAS.520.3788G) Giang, N. C., Hoang, T., Kim, J.-G., & Tram, L. N. 2023, MNRAS, 520, 3788, doi: [`10.1093/mnras/stad020`](http://doi.org/10.1093/mnras/stad020)

(ref: 1952MNRAS.112..215G) Gold, T. 1952, MNRAS, 112, 215, doi: [`10.1093/mnras/112.2.215`](http://doi.org/10.1093/mnras/112.2.215)

(ref: 2017ApJ...835...41G) González-Casanova, D. F., & Lazarian, A. 2017, ApJ, 835, 41, doi: [`10.3847/1538-4357/835/1/41`](http://doi.org/10.3847/1538-4357/835/1/41)

(ref: 2020A&A...634L..15G) Guillet, V., Girart, J. M., Maury, A. J., & Alves, F. O. 2020, A&A, 634, L15, doi: [`10.1051/0004-6361/201937314`](http://doi.org/10.1051/0004-6361/201937314)

(ref: 2019ApJ...877L...2H) Harrison, R. E., Looney, L. W., Stephens, I. W., et al. 2019, ApJL, 877, L2, doi: [`10.3847/2041-8213/ab1e46`](http://doi.org/10.3847/2041-8213/ab1e46)

(ref: 1994ASPC...54...73H) Hawley, J. F., Gammie, C. F., & Balbus, S. A. 1994, in Astronomical Society of the Pacific Conference Series, Vol. 54, The Physics of Active Galaxies, ed. G. V. Bicknell, M. A. Dopita, & P. J. Quinn, 73

(ref: 1996A&A...311..291H) Henning, T., & Stognienko, R. 1996, A&A, 311, 291

(ref: 2016ApJ...831..159H) Hoang , T., & Lazarian, A. 2016, ApJ, 831, 159, doi: [`10.3847/0004-637X/831/2/159`](http://doi.org/10.3847/0004-637X/831/2/159)

(ref: 2022ApJ...928..102H) Hoang, T. 2022, ApJ, 928, 102, doi: [`10.3847/1538-4357/ac5408`](http://doi.org/10.3847/1538-4357/ac5408)

(ref: 2008MNRAS.388..117H) Hoang, T., & Lazarian, A. 2008, MNRAS, 388, 117, doi: [`10.1111/j.1365-2966.2008.13249.x`](http://doi.org/10.1111/j.1365-2966.2008.13249.x)

(ref: 2009ApJ...697.1316H) —. 2009, ApJ, 697, 1316, doi: [`10.1088/0004-637X/697/2/1316`](http://doi.org/10.1088/0004-637X/697/2/1316)

(ref: 2022AJ....164..248H) Hoang, T., Tram, L. N., Minh Phan, V. H., et al. 2022, AJ, 164, 248, doi: [`10.3847/1538-3881/ac9af5`](http://doi.org/10.3847/1538-3881/ac9af5)

(ref: 2015JAI.....450005H) Hull, C. L. H., & Plambeck, R. L. 2015, Journal of Astronomical Instrumentation, 4, 1550005, doi: [`10.1142/S2251171715500051`](http://doi.org/10.1142/S2251171715500051)

(ref: 2014ApJS..213...13H) Hull, C. L. H., Plambeck, R. L., Kwon, W., et al. 2014, ApJS, 213, 13, doi: [`10.1088/0067-0049/213/1/13`](http://doi.org/10.1088/0067-0049/213/1/13)

(ref: 2009IAUS..259..249J) Johansen, A. 2009, in Cosmic Magnetic Fields: From Planets, to Stars and Galaxies, ed. K. G. Strassmeier, A. G. Kosovichev, & J. E. Beckman, Vol. 259, 249–258, doi: [`10.1017/S1743921309030592`](http://doi.org/10.1017/S1743921309030592)

(ref: 1967ApJ...147..943J) Jones, R. V., & Spitzer, Lyman, J. 1967, ApJ, 147, 943, doi: [`10.1086/149086`](http://doi.org/10.1086/149086)

(ref: 2016ApJ...820...54K) Kataoka, A., Muto, T., Momose, M., Tsukagoshi, T., & Dullemond, C. P. 2016, ApJ, 820, 54, doi: [`10.3847/0004-637X/820/1/54`](http://doi.org/10.3847/0004-637X/820/1/54)

(ref: 2019ApJ...874L...6K) Kataoka, A., Okuzumi, S., & Tazaki, R. 2019, ApJL, 874, L6, doi: [`10.3847/2041-8213/ab0c9a`](http://doi.org/10.3847/2041-8213/ab0c9a)

(ref: 2017ApJ...844L...5K) Kataoka, A., Tsukagoshi, T., Pohl, A., et al. 2017, ApJL, 844, L5, doi: [`10.3847/2041-8213/aa7e33`](http://doi.org/10.3847/2041-8213/aa7e33)

(ref: 2015ApJ...809...78K) Kataoka, A., Muto, T., Momose, M., et al. 2015, ApJ, 809, 78, doi: [`10.1088/0004-637X/809/1/78`](http://doi.org/10.1088/0004-637X/809/1/78)

(ref: 2020A&A...638A.116K) Kirchschlager, F., & Bertrang, G. H. M. 2020, A&A, 638, A116, doi: [`10.1051/0004-6361/202037943`](http://doi.org/10.1051/0004-6361/202037943)

(ref: 2011ApJ...741....3K) Kwon, W., Looney, L. W., & Mundy, L. G. 2011, ApJ, 741, 3, doi: [`10.1088/0004-637X/741/1/3`](http://doi.org/10.1088/0004-637X/741/1/3)

(ref: 2008ApJ...676L..25L) Lazarian , A., & Hoang, T. 2008, ApJL, 676, L25, doi: [`10.1086/586706`](http://doi.org/10.1086/586706)

(ref: 2007MNRAS.378..910L) Lazarian, A., & Hoang, T. 2007a, MNRAS, 378, 910, doi: [`10.1111/j.1365-2966.2007.11817.x`](http://doi.org/10.1111/j.1365-2966.2007.11817.x)

(ref: 2007ApJ...669L..77L) —. 2007b, ApJL, 669, L77, doi: [`10.1086/523849`](http://doi.org/10.1086/523849)

(ref: 2021ApJ...908...12L) —. 2021, ApJ, 908, 12, doi: [`10.3847/1538-4357/abd02c`](http://doi.org/10.3847/1538-4357/abd02c)

(ref: 1985ApJ...290..211L) Lee, H. M., & Draine, B. T. 1985, ApJ, 290, 211, doi: [`10.1086/162974`](http://doi.org/10.1086/162974)

(ref: 2022MNRAS.512.3922L) Lin, Z.-Y. D., Li, Z.-Y., Yang, H., et al. 2022, MNRAS, 512, 3922, doi: [`10.1093/mnras/stac753`](http://doi.org/10.1093/mnras/stac753)

(ref: 2023MNRAS.520.1210L) —. 2023, MNRAS, 520, 1210, doi: [`10.1093/mnras/stad173`](http://doi.org/10.1093/mnras/stad173)

(ref: 2024MNRAS.528..843L) Lin, Z.-Y. D., Li, Z.-Y., Stephens, I. W., et al. 2024, MNRAS, 528, 843, doi: [`10.1093/mnras/stae040`](http://doi.org/10.1093/mnras/stae040)

(ref: 2017A&A...607A..74L) Liu, Y., Henning, T., Carrasco-González, C., et al. 2017, A&A, 607, A74, doi: [`10.1051/0004-6361/201629786`](http://doi.org/10.1051/0004-6361/201629786)

(ref: 1977ApJ...217..425M) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425, doi: [`10.1086/155591`](http://doi.org/10.1086/155591)

(ref: 1999ApJ...519..257M) Men’shchikov, A. B., Henning, T., & Fischer, O. 1999, ApJ, 519, 257, doi: [`10.1086/307333`](http://doi.org/10.1086/307333)

(ref: 2003A&A...398..809M) Molina, A., Moreno, F., & Martı́nez-López, F. 2003, A&A, 398, 809, doi: [`10.1051/0004-6361:20021742`](http://doi.org/10.1051/0004-6361:20021742)

(ref: 2021ApJ...908..153M) Mori, T., & Kataoka, A. 2021, ApJ, 908, 153, doi: [`10.3847/1538-4357/abd08a`](http://doi.org/10.3847/1538-4357/abd08a)

(ref: 2023ApJ...953...66N) Ngoc, N. B., Diep, P. N., Hoang, T., et al. 2023, ApJ, 953, 66, doi: [`10.3847/1538-4357/acdb6e`](http://doi.org/10.3847/1538-4357/acdb6e)

(ref: 2019FrASS...6...15P) Pattle, K., & Fissel, L. 2019, Frontiers in Astronomy and Space Sciences, 6, 15, doi: [`10.3389/fspas.2019.00015`](http://doi.org/10.3389/fspas.2019.00015)

(ref: 2016ApJ...816...25P) Pinte, C., Dent, W. R. F., Ménard, F., et al. 2016, ApJ, 816, 25, doi: [`10.3847/0004-637X/816/1/25`](http://doi.org/10.3847/0004-637X/816/1/25)

(ref: 1998ApJ...508..707Q) Quillen, A. C., & Trilling, D. E. 1998, ApJ, 508, 707, doi: [`10.1086/306421`](http://doi.org/10.1086/306421)

(ref: 2004AJ....127.1029R) Rebull, L. M., Wolff, S. C., & Strom, S. E. 2004, AJ, 127, 1029, doi: [`10.1086/380931`](http://doi.org/10.1086/380931)

(ref: 2023A&A...674A..47R) Reissl, S., Meehan, P., & Klessen, R. S. 2023, A&A, 674, A47, doi: [`10.1051/0004-6361/202142528`](http://doi.org/10.1051/0004-6361/202142528)

(ref: 2016A&A...593A..87R) Reissl, S., Wolf, S., & Brauer, R. 2016, A&A, 593, A87, doi: [`10.1051/0004-6361/201424930`](http://doi.org/10.1051/0004-6361/201424930)

(ref: 1993ApJ...418..287R) Roberge, W. G., Degraff, T. A., & Flaherty, J. E. 1993, ApJ, 418, 287, doi: [`10.1086/173390`](http://doi.org/10.1086/173390)

(ref: 2019ApJS..245....2S) Sadavoy, S. I., Stephens, I. W., Myers, P. C., et al. 2019, ApJS, 245, 2, doi: [`10.3847/1538-4365/ab4257`](http://doi.org/10.3847/1538-4365/ab4257)

(ref: 2021AAS...23832901S) Sharkawi, M., Basu, S., & Machida, M. N. 2021, in American Astronomical Society Meeting Abstracts, Vol. 53, American Astronomical Society Meeting Abstracts, 329.01

(ref: 2014Natur.514..597S) Stephens, I. W., Looney, L. W., Kwon, W., et al. 2014, Nature, 514, 597, doi: [`10.1038/nature13850`](http://doi.org/10.1038/nature13850)

(ref: 2017ApJ...851...55S) Stephens, I. W., Yang, H., Li, Z.-Y., et al. 2017, ApJ, 851, 55, doi: [`10.3847/1538-4357/aa998b`](http://doi.org/10.3847/1538-4357/aa998b)

(ref: 2023Natur.623..705S) Stephens, I. W., Lin, Z.-Y. D., Fernández-López, M., et al. 2023, Nature, 623, 705, doi: [`10.1038/s41586-023-06648-7`](http://doi.org/10.1038/s41586-023-06648-7)

(ref: 2023ApJ...947L...5T) Tang, Y.-W., Dutrey, A., Koch, P. M., et al. 2023, ApJL, 947, L5, doi: [`10.3847/2041-8213/acc45b`](http://doi.org/10.3847/2041-8213/acc45b)

(ref: 2017ApJ...839...56T) Tazaki, R., Lazarian, A., & Nomura, H. 2017, ApJ, 839, 56, doi: [`10.3847/1538-4357/839/1/56`](http://doi.org/10.3847/1538-4357/839/1/56)

(ref: 2023arXiv230801215T) Truong, B., Hoang, T., Chau Giang, N., et al. 2023, arXiv e-prints, arXiv:2308.01215, doi: [`10.48550/arXiv.2308.01215`](http://doi.org/10.48550/arXiv.2308.01215)

(ref: 2021ApJ...913..117U) Ueda, T., Kataoka, A., Zhang, S., et al. 2021, ApJ, 913, 117, doi: [`10.3847/1538-4357/abf7b8`](http://doi.org/10.3847/1538-4357/abf7b8)

(ref: 1959JETP....9..995V) Velikhov, E. P. 1959, Soviet Journal of Experimental and Theoretical Physics, 9, 995

(ref: 2008JGRD..11314220W) Warren, S. G., & Brandt, R. E. 2008, Journal of Geophysical Research (Atmospheres), 113, D14220, doi: [`10.1029/2007JD009744`](http://doi.org/10.1029/2007JD009744)

(ref: 2004ApJ...616..998W) White, R. J., & Hillenbrand, L. A. 2004, ApJ, 616, 998, doi: [`10.1086/425115`](http://doi.org/10.1086/425115)

(ref: 2012mith.book...53W) Wriedt, T. 2012, in The Mie Theory: Basics and Applications, ed. W. Hergert & T. Wriedt, Vol. 169 (Springer), 53, doi: [`10.1007/978-3-642-28738-1_2`](http://doi.org/10.1007/978-3-642-28738-1_2)

(ref: 2017MNRAS.472..373Y) Yang, H., Li, Z.-Y., Looney, L. W., Girart, J. M., & Stephens, I. W. 2017, MNRAS, 472, 373, doi: [`10.1093/mnras/stx1951`](http://doi.org/10.1093/mnras/stx1951)

(ref: 2019MNRAS.483.2371Y) Yang, H., Li, Z.-Y., Stephens, I. W., Kataoka, A., & Looney, L. 2019, MNRAS, 483, 2371, doi: [`10.1093/mnras/sty3263`](http://doi.org/10.1093/mnras/sty3263)

(ref: 2019ApJ...880...69Y) Yen, H.-W., Gu, P.-G., Hirano, N., et al. 2019, ApJ, 880, 69, doi: [`10.3847/1538-4357/ab29f8`](http://doi.org/10.3847/1538-4357/ab29f8)

(ref: 2023ApJ...953...96Z) Zhang, S., Zhu, Z., Ueda, T., et al. 2023, ApJ, 953, 96, doi: [`10.3847/1538-4357/acdb4e`](http://doi.org/10.3847/1538-4357/acdb4e)

[^1]: The updated POLARIS code described in (cite: 2023MNRAS.520.3788G) was built up from a rather old version of POLARIS, whose dust scattering feature is less well-tested. Hence, for the Monte-Carlo radiative transfer calculation of dust self-scattering, we use the POLARIS code taken from <https://github.com/polaris-MCRT/POLARIS/tree/master-old> instead.

[^2]: In reality, $\phi_{\rm sp}$ can be as large as 0.3, which corresponds to an iron abundance of $\sim$100% presented in the form of iron clusters (cite: 2016ApJ...831..159H)

</paper>

Write the methods card for this paper.