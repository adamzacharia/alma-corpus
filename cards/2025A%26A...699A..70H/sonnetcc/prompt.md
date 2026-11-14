# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...699A..70H\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...699A..70H",
 "title": "Investigating the chemical link between H<SUB>2</SUB>CO and CH<SUB>3</SUB>OH within the central molecular zone of NGC 253",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Huang, K.-Y.",
 "n_authors": 6,
 "arxiv_id": "2505.16255",
 "doi": "10.1051/0004-6361/202554156",
 "alma_projects_linked_by_archive": [
  "2017.1.00161.L",
  "2018.1.00162.S"
 ]
}
```

Paper text:
<paper>
# Investigating the chemical link between H$_2$CO and CH$_3$OH within the CMZ of NGC 253

The formaldehyde (H$_2$CO) and methanol (CH$_3$OH) molecules have served as traditional tracers of the star formation process for decades. Studies of the environments which produce formaldehyde and methanol emission, though, have pointed to significant differences in the physical environments within which each molecule resides.

In this article we aim to investigate the detailed physical and chemical conditions which give rise to formaldehyde and methanol emission in the nearby starburst galaxy NGC 253.

We employ high spatial ($1.^{\prime\prime}$6 or $\sim28$ pc) and spectral ($\sim10$ km/s) imaging of the NGC 253 central molecular zone (CMZ) from the ALCHEMI Large Program to constrain radiative transfer models of the dense gas

volume density, kinetic temperature, molecular species column density, and source filling factor within eight giant molecular clouds (GMCs). We also measure the relative abundances of the two nuclear spin isomers of CH$_3$OH to investigate its formation history.

The physical and chemical conditions derived clearly indicate that these two molecular species originate from distinct physical environments. H$_2$CO traces low volume density and high kinetic temperatures, while CH$_3$OH traces high volume density and low kinetic temperatures. The H$_2$CO abundances are constant, though poorly constrained, within the eight NGC 253 GMCs analyzed, while the CH$_3$OH abundance shows a radial gradient from low to high values within the NGC 253 CMZ.

Our findings highlight the complex chemical and physical differentiation of CH$_3$OH and H$_2$CO in the starburst environment of NGC 253. Methanol formation appears to be influenced by warm, dynamic processes rather than cold cloud chemistry, while formaldehyde primarily forms via gas-phase reactions. These results challenge the assumption of a direct chemical link between CH$_3$OH and H$_2$CO and underscores the impact of starburst-driven shocks, turbulence, and cosmic rays on molecular gas chemistry.

# Introduction

The evolution of galaxies is shaped by several key physical and chemical processes within the interstellar medium (ISM). Such processes are often tied to star formation and active galactic nuclei (AGN) activities. Strong stellar feedback associated with high star-forming rates (SFRs) can trigger outflows of ionized, neutral, and molecular gas. The significant energy input from starburst activities makes starburst galaxies prime targets for investigating feedback processes in the ISM (cite: Melioli2004A&A; Krieger2020ApJ)

NGC 253 is a barred spiral galaxy with an inclination of $76^{\circ}$ (cite: McCormick+2013) that makes it almost edge-on. The proximity of NGC 253 (cite: Rekola+2005) also makes it one of the most well studied starburst systems. The central molecular zone (CMZ) of NGC 253 extends approximately $300\times100$ pc (cite: Sakamoto+2011) and encompasses over ten extensively studied giant molecular clouds (GMCs). With a SFR of $\sim2$ M$_{\odot}$yr^-1^ arising from its CMZ (cite: Leroy+2015; Bendo+2015), which is half of its global star formation activity, NGC 253 is also classified as a prototype of a nuclear starburst system. A large-scale outflow in NGC 253 has been revealed by multiwavelength observations: in X-rays (cite: Strickland+2000; Strickland+2002), H$\alpha$ (cite: Westmoquette+2011), molecular emission (cite: Turner1985; Bolatto+2013; Walter+2017; Krieger+2019), and dust (cite: Levy+2022). This large-scale outflow is considered a result of the galaxy’s starburst activity (cite: McCarthy+1987) due to the lack of AGN signatures (cite: MS+2010; Lehmer+2013). At the more localized scales, shocks and turbulence also contribute mechanical energy to the ISM feedback processes.

To trace shocks, there are well-known molecular tracers such as silicon monoxide (SiO) and isocyanic acid (HNCO) (cite: sio_MP+1997; Schilke+1997; Huttemeister+1998; Zinchenko+2000; J-S+2008_shocktracers; Martin+2008_HNCO_galactic; hnco+RF+2010). The presence of gas-phase methanol () in the ISM of starburst galaxies has also been proposed as an indicator of the shock influence. As the simplest complex organic molecule (COM; (cite: Herbst_vanDishoeck_2009)), can form efficiently in cold environments (12-20K) on ice grains with continuous hydrogenation of CO (cite: Fuchs+2009) and H-abstraction reaction of radicals on ice grains (cite: Alvarez+2018; Simons+2020; Santos+2022). The solid-state can be liberated into gas phase via thermal sublimation or non-thermal desorption processes. In the presence of shocks, ice mantle sputtering quickly releases solid-state into the gas phase. On the other hand, the destruction of can also take place in the presence of dissociative shock conditions, as proposed by (cite: Suutarinen+2014). Nevertheless, overall, the non-dissociative shocks remain efficient in enhancing gas-phase in the ISM.

Formaldehyde () is an important precursor of in its formation process on ice grains. Unlike methanol, however, can also form in the cold gas phase by reactions of CH$_2$ and CH$_3$ with O$_2$ and O, respectively, depending on the region (Ramal-Olmedo et al. 2021). In warmer regions, H$_2$CO can form by reactions of CH$_3^+$ with OH (cite: Woodall2007AandA).

As a slightly asymmetric rotor, has been found to be an excellent tracer of the gas kinetic temperature (cite: Mangum_Wootten_1993).

Molecules that host two or more hydrogen atoms such as , , and , exist in two isomeric forms: ortho- (hydrogen nuclei spin are parallel) and para- (hydrogen nuclei spin are anti-parallel). Both and have two spin isomers. For , they are referred to as E- and A- owing to the combinations of nuclear spin alignment in the three H-atoms of the methyl () group. In A-type , the nuclear spins of the three protons in the methyl group are parallel. For E-type , one of the protons in the methyl group has an anti-parallel nuclear spin with respect to the others. The E/A ratio can be a probe of the history of methanol formation (see Section 5.3). On the other hand, for , the two nuclear spin isomers are referred to as o- and p- . Observationally the spin isomers of both molecules have different spectroscopic properties including transition frequencies.

Both and have been imaged in NGC 253. In particular, (cite: Mangum+2019) imaged the CMZ of NGC 253 with multi-transition observations at spatial resolution $1.^{\prime\prime}5-0.^{\prime\prime}4$ and found that, while at large scales ($\sim5.^{\prime\prime}0$) $T_{kin}\gtrsim50$ K, at smaller scales ($\lesssim 1.5^{\prime\prime}$) temperatures were at least 300 K, highlighting the importance of high spatial resolution in order to determine the real temperature structure of the central region of this starburst galaxy.

was imaged by the ALMA large program, “ALMA Comprehensive High-resolution Extragalactic Molecular Inventory" (cite: ALCHEMI_main_2021). Several ALCHEMI studies have already been published and have revealed a high cosmic-ray ionization rate (cite: Holdship+2021_SpectralRadex; Holdship+2022; Harada+2021; Behrens2022ApJ; Behrens2024), as well as various types of shocks throughout the CMZ (cite: Humire+2022; Harada+2022; Huang+2023).

The aim of the current study is to investigate both the physical and chemical properties traced by and in the nearby starburst galaxy, NGC 253, and investigate whether the two species are chemically linked. We present a multi-transition molecular study using and observations from the ALMA large program, ALCHEMI (cite: ALCHEMI_main_2021). The paper is structured as follows. In Section [2](#sec:obs) we describe the observations and the transition selections for our analysis. In Section [3](#sec:line_emission) we discuss the molecular transition intensity images. In Section [4](#sec:radex) we present our non-LTE radiative transfer analysis in order to constrain the physical conditions of the gas traced by and . We then explore in Section [5](#sec:Discussion) the physical origin of the CH$_3$OH and H$_2$CO emission and investigate whether these two molecules are chemically linked. This discussion includes an assessment of the relative abundances of CH$_3$OH, H$_2$CO, SiO, HNCO, OCS, H$_2$CS, H$_2$S, and CS within eight of the giant molecular clouds (GMCs) of the NGC 253 CMZ. We then summarize our findings in Section [6](#sec:conclusions).

# Observations and data analysis

In this section we summarize the observational setup and the fundamental properties of the ALCHEMI survey data. Full details regarding the data acquisition, calibration, and imaging are described in (cite: ALCHEMI_main_2021). ALCHEMI is an ALMA Large Program (project code 2017.1.00161.L and 2018.1.00162.S) that imaged the CMZ of NGC 253 with rest-frequency coverage from 84.2 to 373.2 GHz, corresponding to the ALMA frequency Bands 3, 4, 5, 6, and 7. With wide and thorough spectral scanning across the CMZ of NGC 253, ALCHEMI provides a comprehensive molecular view of its nucleus. A common rectangular area with a size of $50^{\prime\prime} \times 20^{\prime\prime}$ ($850\times340$ pc) at a position angle of $65^\circ$ was imaged to cover the central nuclear region in NGC 253. A common maximum recoverable angular scale of $15^{\prime\prime}$ was achieved after combining the 12 m Array and Atacama Compact Array (ACA) measurements at all frequencies. The nominal phase center of the observations is $\alpha(\rm ICRS)$ = 00$^h$47$^m$33$^s$.26, $\delta(\rm ICRS)$ = $-25^\circ$17$^\prime$17$^{\prime\prime}.7$. The angular and spectral resolution of the image cubes generated from these measurements were $1.^{\prime\prime}6$ (cite: ALCHEMI_main_2021) and $\sim10$ km s$^{-1}$, respectively.

From the ALCHEMI data, we extracted the spectral cubes of NGC 253 for the selected 39 transitions (Table [\[tab:table_obsinfo_ch3oh\]](#tab:table_obsinfo_ch3oh)) and 10 transitions (Table [\[tab:table_obsinfo_h2co\]](#tab:table_obsinfo_h2co)). We chose and transitions based on the following criteria: (1) the transition needs to be bright enough, specifically with signal-to-noise ratio (SNR) greater than 3; and (2) no significant contamination from other molecule(s) involved. In regard to this criterion, we note that the methanol transitions at 165 GHz and 302 GHz are blended with, respectively, an SO$_2$ transition ($\sim$ 27%) and an NH$_2$OH transition ($\sim$ 23%), while the H$_2$CO transitions at 140 GHz and 364 GHz suffer from contamination by, respectively, a transition of NH$_2$CN ($\sim$ 25%) and a transition of SO$_2$ ($\sim$ 25%). We have tested the impact of these contaminants on our derivation of physical parameters performed in Section 4 and found that the derived physical parameters are unchanged within the uncertainties in each parameter fit. Note that we do include transitions that show self blending, including among different spin isomers (see Table [\[tab:offsets\]](#tab:offsets)).

We note that our compilation of transitions is distinct from the set of transitions analyzed by (cite: Humire+2022) which had different transition selection criteria from ours, and focused on masing . Specifically, our list of transitions does not involve any maser candidates from (cite: Humire+2022).

We use `CubeLineMoment`[^3] (cite: Mangum+2019) to extract integrated spectral-line intensities from our data cubes. `CubeLineMoment` employs a set of spectral and spatial masks to extract robust integrated intensities for a defined list of target spectral frequencies. The spectral masking process of `CubeLineMoment` uses a chosen bright spectral line in each cube as a velocity tracer of the inspected gas component. This makes the definition of velocity span for integration precise while avoiding contamination from adjacent but still separable transitions. Final products from the `CubeLineMoment` analysis include moment 0 (integrated intensity; Jy beam^-1^ $\cdot$ km s^-1^), 1 (average velocity; km s^-1^), and 2 (velocity dispersion; km s^-1^) images masked below a $3\sigma$ threshold (channel-based). After making the velocity-integrated maps (moment-0 maps) for all the selected transitions, we converted them from \[Jy beam^-1^ $\cdot$ km s^-1^\] to \[K $\cdot$ km s^-1^\] for further physical modeling analysis using Equation [\[eq:jperk\]](#eq:jperk).

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Transition |  | Rest Frequency | E~u~ | $A_{ul}$ | Integrated Intensity (GMC 3) |
|  |  | \[GHz\] | \[K\] | \[s$^{-1}$\] | \[K km s$^{-1}$\] |
| E- | $2_{-1} - 1_{-1}$ | 96.739360 | 12.5 | 2.558E-06 | 111$\pm$17 |
| E- | $2_0 - 1_0$ | 96.744550 | 20.1 | 3.407E-06 |  |
| E- | $2_1 - 1_1$ | 96.755500 | 28.0 | 2.624E-06 |  |
| A- | $2_0 - 1_0$ | 96.741370 | 7.0 | 3.408E-06 |  |
| A- | $2_{-1} - 1_{-1}$ | 97.582800 | 21.6 | 2.626E-06 | 8.4$\pm$1.3 |
| A- | $3_1 - 4_0$ | 107.013830 | 28.3 | 3.066E-06 | 6.7$\pm$1.0 |
| A- | $3_1 - 2_1$ | 143.865790 | 28.3 | 1.069E-05 | 12.7$\pm$1.9 |
| A- | $3_{-1} - 2_{-1}$ | 146.368330 | 28.6 | 1.125E-05 | 13.3$\pm$2.0 |
| A- | $2_1 - 3_0$ | 156.602400 | 21.4 | 8.926E-06 | 13.5$\pm$2.0 |
| E- | $7_0 - 7_{-1}$ | 156.828520 | 78.1 | 1.878E-05 | 2.8$\pm$0.4 |
| E- | $4_0 - 4_{-1}$ | 157.246060 | 36.3 | 2.098E-05 | 120$\pm$18 |
| E- | $1_0 - 1_{-1}$ | 157.270830 | 15.4 | 2.206E-05 |  |
| E- | $3_0 - 3_{-1}$ | 157.272340 | 27.1 | 2.146E-05 |  |
| E- | $2_0 - 2_{-1}$ | 157.276020 | 20.1 | 2.182E-05 |  |
| E- | $1_1 - 1_0$ | 165.050170 | 23.4 | 2.349E-05 | 76$\pm$11 |
| E- | $2_1 - 2_0$ | 165.061130 | 28.0 | 2.343E-05 |  |
| E- | $14_6 - 15_5$ | 165.074350 | 422.4 | 5.365E-06 |  |
| E- | $3_1 - 3_0$ | 165.099240 | 35.0 | 2.333E-05 |  |
| E- | $4_1 - 4_0$ | 165.190470 | 44.3 | 2.321E-05 | 22.0$\pm$3.3 |
| E- | $5_1 - 5_0$ | 165.369340 | 55.9 | 2.308E-05 | 11.5$\pm$1.7 |
| E- | $6_1 - 6_0$ | 165.678650 | 69.8 | 2.295E-05 | 5.6$\pm$0.9 |
| E- | $3_2 - 2_1$ | 170.060590 | 36.2 | 2.552E-05 | 30.6$\pm$4.6 |
| A- | $4_{-1} - 3_{-1}$ | 195.146790 | 38.0 | 2.917E-05 | 14.8$\pm$2.2 |
| A- | $1_1 - 2_0$ | 205.791270 | 16.8 | 6.277E-05 | 13.5$\pm$2.0 |
| A- | $5_{-1} - 4_{-1}$ | 243.915790 | 49.7 | 5.966E-05 | 12.1$\pm$1.8 |
| E- | $5_2 - 4_1$ | 266.838150 | 57.1 | 7.736E-05 | 16.0$\pm$2.4 |
| A- | $6_1 - 5_1$ | 287.670770 | 62.9 | 1.006E-04 | 7.3$\pm$1.1 |
| A- | $6_{-1} - 5_{-1}$ | 292.672890 | 63.7 | 1.060E-04 | 7.6$\pm$1.1 |
| E- | $3_0 - 2_{-1}$ | 302.369770 | 27.1 | 4.661E-05 | 20.3$\pm$3.0 |
| A- | $1_{-1} - 1_0$ | 303.366920 | 16.9 | 2.263E-04 | 36.0$\pm$5.4 |
| A- | $2_{-1} - 2_0$ | 304.208350 | 21.6 | 2.116E-04 | 44.7$\pm$6.7 |
| A- | $3_{-1} - 3_0$ | 305.473490 | 28.6 | 1.632E-04 | 44.1$\pm$6.6 |
| E- | $3_1 - 2_0$ | 310.192990 | 35.0 | 8.800E-05 | 27.4$\pm$4.1 |
| A- | $6_{-1} - 6_0$ | 311.852610 | 63.7 | 1.712E-04 | 14.0$\pm$2.0 |
| A- | $7_{-1} - 7_0$ | 314.859530 | 80.1 | 1.749E-04 | 8.5$\pm$1.3 |
| E- | $6_2 - 5_1$ | 315.266860 | 71.0 | 1.183E-04 | 9.9$\pm$1.5 |
| A- | $7_1 - 6_1$ | 335.582020 | 79.0 | 1.628E-04 | 3.8$\pm$0.6 |
| A- | $1_1 - 0_0$ | 350.905100 | 16.8 | 3.315E-04 | 33.2$\pm$5.0 |
| E- | $4_1 - 3_0$ | 358.605800 | 44.3 | 1.319E-04 | 21.6$\pm$3.2 |

\
Table notes: Frequencies and spectroscopic parameters have been extracted from the JPL catalogue (cite: Pickett+1998). The available data for CH$_3$OH are from (cite: Xu+2008). Note that only transitions covered within $\pm 150$ km s^-1^ with respect to the main transition are listed as shown with vertical lines in Figure [5](#fig:Spec_I) and [6](#fig:Spec_II) - these are considered to be the "contributors" of the velocity-integrated intensities measured from the moment-0 maps. It is worth noting that around 165 GHz, the methanol transition with $E_{\text{u}}=422$ K will only contribute significantly if $T_{\text{kin}}> 100$ K. The main line refers to transitions with the lowest $E_{u}$ in each frequency group. Measured integrated intensity values and their uncertainties for GMC 3 are provided as a reference. Integrated intensities measured toward the GMCs listed in Table [1](#tab:GMC_locations) are available as a machine-readable table [online](https://doi.org/10.5281/zenodo.15442733).

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Transition |  | Rest Frequency | E~u~ | $A_{ul}$ | Integrated Intensity (GMC 3) |
|  |  | \[GHz\] | \[K\] | \[s$^{-1}$\] | \[K km s$^{-1}]$ |
| o- | $2_{12} - 1_{11}$ | 140.839500 | 21.9 | 5.304E-05 | 104$\pm$16 |
| o- | $3_{12} - 2_{11}$ | 225.697800 | 33.4 | 2.772E-04 | 46.0$\pm$6.9 |
| o- | $4_{14} - 3_{13}$ | 281.526900 | 45.6 | 5.883E-04 | 42.5$\pm$6.4 |
| p- | $4_{23} - 3_{22}$ | 291.237800 | 82.1 | 5.210E-04 | 7.1$\pm$1.1 |
| o- | $4_{32} - 3_{31}$ | 291.380500 | 140.9 | 3.044E-04 | 15.6$\pm$2.3 |
| o- | $4_{31} - 3_{30}$ | 291.384300 | 140.9 | 3.044E-04 |  |
| p- | $4_{22} - 3_{21}$ | 291.948100 | 82.1 | 5.249E-04 | 8.8$\pm$1.4 |
| o- | $5_{15} - 4_{14}$ | 351.768600 | 62.5 | 1.202E-03 | 27.6$\pm$4.1 |
| p- | $5_{24} - 4_{23}$ | 363.945900 | 99.5 | 1.165E-03 | 5.8$\pm$0.9 |
| p- | $5_{23} - 4_{22}$ | 365.363400 | 99.7 | 1.179E-03 | 4.7$\pm$0.7 |

\
Table notes: Frequencies and spectroscopic parameters have been extracted from CDMS (cite: Muller+2005; Endres+2016). The available data for H$_2$CO are from (cite: Muller+2017). Note that only transitions covered within $\pm 150$ km s^-1^ with respect to the main transition are listed as shown with vertical lines in Figure [6](#fig:Spec_II) - these are considered to be the "contributors" of the velocity-integrated intensities measured from the moment-0 maps. The main line refers to transitions with the lowest $E_{u}$ in each frequency group. Measured integrated intensity values and their uncertainties for GMC 3 are provided as a reference. Integrated intensities measured toward the GMCs listed in Table [1](#tab:GMC_locations) are available as a machine-readable table [online](https://doi.org/10.5281/zenodo.15442733).

# Molecular line emission

In Fig. [1](#fig:Maps_m3_mom0-I) we present the velocity-integrated transition intensity images from the 96.7 GHz transition group and $2_{12} - 1_{11}$ transition as representative cases for each species (see Appendix [9](#sec:mom0_maps) for the integrated intensity maps for all transitions listed in Tables [\[tab:table_obsinfo_ch3oh\]](#tab:table_obsinfo_ch3oh) and [\[tab:table_obsinfo_h2co\]](#tab:table_obsinfo_h2co)). We also show the representative spectra extracted from GMC 6 for all transitions analyzed in this work in Appendix [8](#sec:spectra) (Fig. [5](#fig:Spec_I) and [6](#fig:Spec_II)). We convert the integrated emission from Jy beam$^{-1}$ km s$^{-1}$ to K km s$^{-1}$ using the following expression $$\begin{equation}
    I(\text{K}) = 13.59\left(\dfrac{300\text{GHz}}{\nu}\right)^2 \times \left(\dfrac{1^{\prime\prime}}{\theta_{max}}\right)\left(\dfrac{1^{\prime\prime}}{\theta_{min}}\right)I(\text{Jy}),
    \label{eq:jperk}
\end{equation}$$ where $\nu$ is the rest frequency of the line, $\theta_{max}$ and $\theta_{min}$ are the major and minor axes, respectively, of our Gaussian beam, and $I$ is the integrated intensity.

The molecular line emission presented in Fig. [1](#fig:Maps_m3_mom0-I) shows several bright regions across the CMZ of NGC 253. Overall they match well with the line emission spatial distribution reported by prior ALCHEMI studies with other molecular species - including (cite: Holdship+2022), and (cite: Harada+2021), and (cite: Holdship+2022), (cite: Harada+2022), and (cite: Behrens2022ApJ; Behrens2024), and (cite: Huang+2023), sulfur-bearing species (cite: Bouvier+2024), and and their isotopologues (cite: Butterworth+2024).

We note that absorption features in GMC 5 - due to the strong continuum in the background toward the center of the galaxy and potential self-absorption in the optically thick regime - have been reported from multiple studies with different species (cite: Meier+2015_hncosio_253; Humire+2022). Such features are also seen in our data. To interpret the intensity measurements from this region requires an advanced radiative-transfer model which includes strong background continuum emission. Such a modeling effort is beyond the scope of the present study. Additionally, in GMC 10, there is a lack of detection in most transitions. As a result, we do not discuss these two regions (GMCs 5 and 10) any further.

The positions of all the remaining GMCs are listed in Table [1](#tab:GMC_locations). These 8 GMC regions are also marked as white circles on both representative CH$_3$OH and H$_2$CO moment-0 images shown in Fig. [1](#fig:Maps_m3_mom0-I).

|        |                 |                           |
|:------:|:---------------:|:-------------------------:|
|  GMC   |   R.A.(ICRS)    |        Dec.(ICRS)         |
|        | (00$^h$ 47$^m$) | ($-25^\circ$ 17$^\prime$) |
| GMC 1a |   31$^s$.9344   |  28$^{\prime\prime}$.822  |
| GMC 2b |   32$^s$.3449   |  18$^{\prime\prime}$.886  |
| GMC 3  |   32$^s$.8056   |  21$^{\prime\prime}$.552  |
| GMC 4  |   32$^s$.9736   |  19$^{\prime\prime}$.968  |
| GMC 6  |   33$^s$.3312   |  15$^{\prime\prime}$.756  |
| GMC 7  |   33$^s$.6432   |  13$^{\prime\prime}$.272  |
| GMC 8a |   33$^s$.9443   |  10$^{\prime\prime}$.888  |
| GMC 9a |   34$^s$.1287   |  12$^{\prime\prime}$.040  |

: The 8 selected NGC 253 GMC positions described in Sect. [3](#sec:line_emission).

![image](moment0_maps/pdf_KkmsM3_CH3OH_nu096.741371_B3dI.pdf)\
![image](moment0_maps/pdf_KkmsM3_H2CO_nu140.839502_B4e.pdf)

# Non-LTE radiative transfer modeling analysis

We performed non-LTE radiative transfer modeling to characterize the average gas properties traced by and over beam-sized ($1.^{\prime\prime}6$ or 28 pc) structures. Given the plethora of transitions we have measured for both species, spanning a wide range in excitation energy, radiative transfer analysis can be used to properly constrain the gas physical characteristics. We use the radiative transfer code `RADEX` (cite: radex_vandertak_2007) via the Python package `SpectralRadex`[^4] (cite: Holdship+2021_SpectralRadex). The collisional excitation rates used for are from (cite: Dagdigian_2023) while the rates are from (cite: H2CO_mole_data). These rates were obtained from the Excitation of Molecules and Atoms for Astrophysics (EMAA)[^5] and the LAMDA databases (cite: Schoier2005A&A), respectively. For kinetic temperature priors below or above the lower or upper limits to the kinetic temperatures at which collisional excitation rates are provided (3 to 250 and 10 to 300 K for CH$_3$OH and H$_2$CO, respectively), `SpectralRadex` uses the minimum or maximum kinetic temperature at which collisional excitation rates are provided.

One should note that there is a noticeable difference in the derived E-/A- spin isomer column density ratio (EAR) for CH$_3$OH when using the old (from (cite: CH3OH_mol_data_2010)) and the new (from (cite: Dagdigian_2023)) collisional excitation rates. With the (cite: CH3OH_mol_data_2010) rates, the average range for the best EAR was 0.85–2.84 whilst with the (cite: Dagdigian_2023) rates, the range is 0.25–1.26. By comparing the brightness temperatures for the $3_0-2_0$A and $2_{-1}-1_{-1}$E lines of at 145.103 GHz and 96.739 GHz, respectively, (cite: Dagdigian_2023) showed that the largest difference in both quantities occurred for the E-type transition at low temperature (10 K; see their Fig. 5), with the brightness temperature calculated with the new rates being lower (by maximum 10%) than with the previous rates, in particular for $n_{\mathrm{H2}}\geq 10^4$ cm$^{-3}$. The difference is less important at 100 K. Although the comparison has been made for one E-type transition, this difference could explain the change in the derived EAR between the old and new excitation rates that we found. The choice of the rates used for thus seem more critical if one aims to derive the EAR.

We coupled radiative transfer modeling with the `Nautilus` sampler (cite: nautilus)[^6] for Bayesian posterior and evidence estimation.

We then perform the Bayesian inference of the parameter probability distributions. We assume priors of uniform or log-uniform distribution within the determined ranges (listed in Table [2](#tab:table_prior)). We also assume that the uncertainty on our measured intensities is Gaussian so that our likelihood is given by $P(\theta | d) \sim \exp(-\frac{1}{2}\chi^2),$ where $\chi^2$ is the chi-squared statistic between our measured intensities and the `RADEX` predictions based on a set of parameters $\theta$. This allows us to assess the influence of the physical conditions in the excitation of the transitions analyzed. Note that for each blending group, we model the integrated intensities of the transitions that make up the blending group separately, sum up the emission from each of these lines, and then compare this summed value to the total measured blended intensity for that group.

The following physical parameters are explored: the gas volume density ($n_{H2})$, gas kinetic temperature ($T_{kin}$), the species column density of both spin isomers of each molecule (N(E-CH$_3$OH) and N(A-CH$_3$OH) for and N(o-H$_2$CO) and N(p-H$_2$CO) for ), and the beam filling factor ($\eta_{ff}=\frac{\theta^{2}_{S}}{\theta^{2}_{MB}+\theta^{2}_{S}}$). The prior ranges and distributions are given in Table [2](#tab:table_prior).

We list the best fit for all the explored parameters in Tables [\[tab:Bayesian_gasphys_ch3oh\]](#tab:Bayesian_gasphys_ch3oh) and [\[tab:Bayesian_gasphys_h2co\]](#tab:Bayesian_gasphys_h2co), and present the inference results from a representative GMC (GMC 3) for both and in Fig. [2](#fig:Baye_GMC3). The rest of the inference results can be found in Appendix [10](#sec:corners). In the following subsections we discuss our findings.

![](Bayesian_NTLS/GMC3_corner_allMols_newRates.pdf)

|               Variable               |       Range       | Distribution type |
|:------------------------------------:|:-----------------:|:-----------------:|
| Gas density, $n_{\rm H2}$ \[cm^-3^\] |  $10^{2}-10^{8}$  |    Log-uniform    |
| Gas temperature, $T_{\rm kin}$ \[K\] |     $10-800$      |      Uniform      |
|          $N$(A-) \[cm^-2^\]          | $10^{12}-10^{18}$ |    Log-uniform    |
|          $N$(E-) \[cm^-2^\]          | $10^{12}-10^{18}$ |    Log-uniform    |
|          $N$(o-) \[cm^-2^\]          | $10^{12}-10^{18}$ |    Log-uniform    |
|          $N$(p-) \[cm^-2^\]          | $10^{12}-10^{18}$ |    Log-uniform    |
|   Beam filling factor, $\eta_{ff}$   |     $0.0-1.0$     |      Uniform      |

: Prior ranges adopted for our parameter space explored in the `RADEX`-Bayesian inference process described in Sect. [4](#sec:radex).

| GMC | log(n~H2~) | $T_{\text{kin}}$ | log(N~A-CH3OH~) | log(N~E-CH3OH~) | $\eta_{ff}$ | EAR~best~ | EAR range | X~CH3OH~ range |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 1a | $4.22^{+0.11}_{-0.11}$ | $76.06^{+11.44}_{-9.69}$ | $16.60^{+0.06}_{-0.06}$ | $16.32^{+0.13}_{-0.11}$ | $0.08^{+0.01}_{-0.01}$ | 0.52 | \[0.35, 0.81\] | $1.2\times10^{-8}-1.4\times10^{-7}$ |
| 2b | $5.18^{+0.12}_{-0.09}$ | $11.14^{+0.57}_{-0.55}$ | $16.40^{+0.10}_{-0.14}$ | $16.38^{+0.16}_{-0.19}$ | $0.09^{+0.01}_{-0.01}$ | 0.95 | \[0.49, 1.91\] | $1.2\times10^{-8}-1.2\times10^{-7}$ |
| 3 | $6.53^{+0.19}_{-0.16}$ | $19.42^{+0.98}_{-0.93}$ | $15.96^{+0.08}_{-0.08}$ | $16.02^{+0.11}_{-0.11}$ | $0.18^{+0.04}_{-0.03}$ | 1.15 | \[0.74, 1.78\] | $1.8\times10^{-9}-6.1\times10^{-9}$ |
| 4 | $6.89^{+0.21}_{-0.17}$ | $26.79^{+1.55}_{-1.37}$ | $14.99^{+0.18}_{-0.11}$ | $15.06^{+0.18}_{-0.10}$ | $0.73^{+0.19}_{-0.25}$ | 1.17 | \[0.62, 2.29\] | $4.0\times10^{-10}-2.2\times10^{-9}$ |
| 6 | $6.86^{+0.25}_{-0.19}$ | $21.49^{+1.10}_{-1.01}$ | $15.76^{+0.12}_{-0.15}$ | $15.86^{+0.14}_{-0.16}$ | $0.28^{+0.11}_{-0.07}$ | 1.26 | \[0.66, 2.45\] | $9.3\times10^{-10}-5.3\times10^{-9}$ |
| 7 | $5.33^{+0.05}_{-0.05}$ | $23.39^{+0.99}_{-0.96}$ | $16.64^{+0.05}_{-0.05}$ | $16.25^{+0.07}_{-0.07}$ | $0.12^{+0.01}_{-0.01}$ | 0.41 | \[0.31, 0.54\] | $2.8\times10^{-8}-1.4\times10^{-7}$ |
| 8a | $4.95^{+0.06}_{-0.06}$ | $29.47^{+2.05}_{-1.74}$ | $16.36^{+0.06}_{-0.05}$ | $15.75^{+0.08}_{-0.08}$ | $0.09^{+0.01}_{-0.01}$ | 0.25 | \[0.18, 0.33\] | $3.7\times10^{-9}-8.8\times10^{-8}$ |
| 9a | $4.82^{+0.07}_{-0.07}$ | $24.87^{+1.33}_{-1.22}$ | $16.33^{+0.07}_{-0.07}$ | $15.89^{+0.10}_{-0.10}$ | $0.14^{+0.01}_{-0.01}$ | 0.36 | \[0.25, 0.54\] | $8.0\times10^{-9}-1.3\times10^{-7}$ |
| Range | $4.11-7.11$ | $10.59-87.5$ | $14.88-16.66$ | $14.96-16.54$ | $0.07-0.92$ | $0.25-1.26$ | \[$0.18-2.45$\] | $4.0\times10^{-10} - 1.4\times10^{-7}$ |

\
Table notes: The "EAR" stands for E-/A- spin isomer column density ratio of . In the column "EAR~best~" we list the best-estimate EAR in each GMC region based on the inferred column density of A- and E- respectively. In the column "EAR range" we list the range of possible EAR subtended by the uncertainties of the inferred E- and A- column densities.

| GMC | log(n~H2~) | $T_{\text{kin}}$ | log(N~o-H2CO~) | log(N~p-H2CO~) | $\eta_{ff}$ | X~H2CO~ range |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 1a | $4.05^{+0.77}_{-0.65}$ | $95.94^{+27.58}_{-17.87}$ | $15.99^{+0.94}_{-0.99}$ | $15.13^{+0.91}_{-0.97}$ | $0.21^{+0.27}_{-0.11}$ | $1.4\times10^{-10}-1.4\times10^{-6}$ |
| 2b | - - | $83.91^{+18.34}_{-13.78}$ | - - | - - | - - | - - |
| 3 | $3.71^{+0.49}_{-0.43}$ | $129.71^{+49.30}_{-32.99}$ | $17.24^{+0.49}_{-0.56}$ | $16.85^{+0.50}_{-0.58}$ | $0.10^{+0.06}_{-0.03}$ | $2.1\times10^{-9}-1.7\times10^{-7}$ |
| 4 | $3.89^{+0.39}_{-0.37}$ | $266.73^{+316.23}_{-122.64}$ | $17.43^{+0.37}_{-0.50}$ | $16.97^{+0.40}_{-0.48}$ | $0.07^{+0.04}_{-0.03}$ | $1.4\times10^{-9}-9.4\times10^{-8}$ |
| 6 | $3.86^{+0.37}_{-0.36}$ | $> 200$ | $17.56^{+0.30}_{-0.46}$ | $17.09^{+0.35}_{-0.47}$ | $0.07^{+0.05}_{-0.03}$ | $1.8\times10^{-9}-1.2\times10^{-7}$ |
| 7 | $3.94^{+0.43}_{-0.46}$ | $107.36^{+28.68}_{-21.35}$ | $16.20^{+0.68}_{-0.51}$ | $15.64^{+0.66}_{-0.50}$ | $0.41^{+0.26}_{-0.16}$ | $5.7\times10^{-9}-1.1\times10^{-6}$ |
| 8a | $3.88^{+0.65}_{-0.65}$ | $94.12^{+22.82}_{-16.30}$ | $15.69^{+1.02}_{-0.69}$ | $15.00^{+0.99}_{-0.71}$ | $0.36^{+0.33}_{-0.19}$ | $3.3\times10^{-10}-1.2\times10^{-6}$ |
| 9a | $4.14^{+0.61}_{-0.55}$ | $79.91^{+17.51}_{-12.68}$ | $15.83^{+0.68}_{-0.79}$ | $14.97^{+0.69}_{-0.81}$ | $0.22^{+0.25}_{-0.10}$ | $1.7\times10^{-10}-3.1\times10^{-7}$ |
| Range | $3.50-4.75$ | $\geq67.23$ | $15.00-17.86$ | $14.16-17.44$ | $0.04-0.67$ | $1.4\times10^{-10}-1.4\times10^{-6}$ |

\

## Properties of the gas as traced by CH$_3$OH and H$_2$CO

In general traces dense gas components, with gas volume density ranging from $\sim 10^{5} - 10^{7}$ cm^-3^. The methanol in the inner GMCs (GMCs 3, 4, 6, 7) traces the densest gas components (n~H2~ $\gtrsim 4\times 10^{5} - 10^7$ cm^-3^) compared to the rest of the GMCs in the outer regions (n~H2~ $\leq 2\times10^{5}$ cm^-3^). The gas temperatures probed by seem to be surprisingly low, with the lowest temperature being $\sim11$ K in GMC 2b and not exceeding 30 K in all GMCs except 1a. In this region, we infer a gas temperature of $\sim76$ K, more than twice the temperature inferred from CH$_3$OH in all other regions across NGC 253. We note that using the more recent collisional excitation rates from (cite: Dagdigian_2023) resulted in a higher kinetic temperature, whereas the rates calculated by (cite: CH3OH_mol_data_2010) yielded a temperature of $\sim36$ K. However, both (cite: Huang+2023) and (cite: Tanaka2024) also identified high ($>100$ K) gas temperatures in GMC 1a using HNCO and a selection of dense gas tracers, respectively. (cite: Gorski2017) also noted the presence of an expanding shell of gas near GMC 1a, and (cite: Tanaka2024) suggest this could indicate that the gas near GMC 1a is being shocked and mechanically heated by a supernova remnant.

While seems to largely trace cold gas, (cite: Rico-Villas+2020) used vibrationally excited transitions of HC$_3$N to derive gas kinetic temperatures of $\gtrsim 100$ K across all the super star clusters (SSCs) in the inner GMCs of NGC 253, with gas density n~H2~ $\gtrsim 10^{6}$ cm^-3^. It is possible that $v=0$ CH$_3$OH is emitted from a lower temperature gas, especially if we are seeing a post-shocked gas whereby methanol has been released (e.g. via shocks) in the gas phase from ices; nevertheless it is worth also exploring the possibility that methanol is subthermally excited.

We therefore inspected the excitation conditions given the low gas temperatures probed by . Specifically, we compared the collisional and radiative excitation rate (cite: Goldsmith+2012) based on the on-the-spot measurements of opacity, gas density, and gas temperature in each GMC.

We find that overall only about half of the transitions may be undergoing sub-thermal excitation conditions. Moreover, at the low temperature probed by , the molecule is either expected to still be frozen on the dust (if methanol formed on the ices) or to freeze fairly quickly (if methanol was formed in the gas phase when the gas was warmer[^7]). Alternatively, we can invoke either the presence of periodic shocks and/or desorption via cosmic rays, as a non-thermal desorption process that releases the from the ices.

In contrast, probes gas components of lower density compared to . In fact, the gas density traced by is surprisingly homogeneous across all GMCs (n~H2~ $\sim 10^4$ cm^-3^).

On the other hand, traces warmer gas, with $T_{\text{kin}}\gtrsim 100$ K across all GMCs, with the highest $T_{\text{kin}}$ in GMCs 4 and 6. We also compared the collisional and radiative excitation rates based on on-the-spot measurements of opacity, gas density, and gas temperature in each GMC for . Surprisingly the majority of transitions possess sub-thermal excitation conditions.

The fact that we do not see H$_2$CO in the cold component traced by methanol implies that, if methanol is indeed sublimated by non-thermal desorption processes, solid H$_2$CO is not abundant, making it unlikely that their formation paths are chemically connected. We therefore suggest that the H$_2$CO we observe is mainly formed in the gas phase, via reactions of CH$_3$ and atomic oxygen (cite: Loomis2015ApJL; Guzman2013A&A). If these two species were to both form on the ices, then once non-thermally desorbed we would expect them to be co-spatial.

## Comparison with existing measurements of CH$_3$OH and H$_2$CO towards NGC 253

(cite: Humire+2022) estimated molecular column densities and excitation temperatures ($T_{ex}$) of E-/A- via an LTE analysis assuming optically thin conditions. Comparing our CH$_3$OH column density measurements (Table [\[tab:Bayesian_gasphys_ch3oh\]](#tab:Bayesian_gasphys_ch3oh)) to those reported by (cite: Humire+2022), with the exception of GMC 4, our derived column densities of E- and A- are at least 1-2 orders of magnitude higher. This discrepancy can be explained by the fact that their LTE analysis assumed a filling factor of 1. As can be seen in Table 5, all of our best fits derive a much smaller filling factor than 1, with the exception of GMC 4 where the best fit filling factor is $\sim$0.7. We note that the $T_{ex}$ from (cite: Humire+2022) is consistent with our kinetic temperature using non-LTE radiative transfer modeling. Similarly, we also compare our inference of column density as well as our inferred kinetic temperatures with those derived by (cite: Mangum+2019) where optically thin conditions were also assumed[^8]. Our derived column densities of o- and p- are at least 1-2 orders of magnitude higher than the prediction by (cite: Mangum+2019), again probably due to the fact that they assumed a beam filling factor of 1. Our derived kinetic temperatures are all greater than 80 K, consistent with the high kinetic temperature derived by (cite: Mangum+2019).

## Derivation of H$_2$CO and CH$_3$OH abundances

To derive the methanol and formaldehyde abundances, we used the H$_2$ column densities from (cite: Mangum+2019). In particular, we used the values of $N_{H2}$ derived from the continuum emission at 220 GHz (see their Table 5). Since the beam of their observations is slightly smaller compared to ours ($1.56'' \times 0.89 ''$ versus $1.6'' \times 1.6''$), we rescaled their H$_2$ column densities to match our angular resolution. This resulted in multiplying their $N_{H2}$ by a factor of 0.63. Then, as the column densities derived for H$_2$CO and CH$_3$OH correspond to a certain beam-filling factor, we applied a beam filling factor to the scaled H$_2$ column densities for each region, using the values of $\eta_{ff}$ from Table [\[tab:Bayesian_gasphys_ch3oh\]](#tab:Bayesian_gasphys_ch3oh). In (cite: Mangum+2019) the H$_2$ column densities being only available for the regions GMC 3 to GMC 7, we used the $N_{H2}$ values from (cite: Harada+2022) for the other regions, i.e., for GMC 1a, GMC 2b, GMC 8a, and GMC 9a. For these regions, we used $N_{H2}=(3-10)\times10^{22}$ cm$^{-2}$ (see their Figure 4c). As the observations in (cite: Harada+2022) are also ALCHEMI observations, we did not rescale $N_{H2}$. However, we did apply the beam filling factors from Table [\[tab:Bayesian_gasphys_h2co\]](#tab:Bayesian_gasphys_h2co) to the H$_2$ column densities for each region.

The range of abundances derived for methanol, X$_{\rm{CH3OH}}$, and formaldehyde, X$_{\rm{H2CO}}$, are listed in Tables [\[tab:Bayesian_gasphys_ch3oh\]](#tab:Bayesian_gasphys_ch3oh) and [\[tab:Bayesian_gasphys_h2co\]](#tab:Bayesian_gasphys_h2co) and shown in Figure [3](#fig:abundances). Since the column densities of the E- and A- forms of CH$_3$OH are similar when taking account of the range of uncertainties, we derived X$_{\rm{CH3OH}}$ for both forms together. We did the same for X$_{\rm{H2CO}}$, the p- and o- forms having the same column densities within the range of uncertainties derived. Overall, we derive X$_{\rm{CH3OH}}$ in the range $4.0\times 10^{-10} - 1.4 \times 10^{-7}$, with the lowest abundances towards GMC 4, and the highest towards the four outermost GMCs, i.e., GMC 1a, GMC 2b, GMC 8a, and GMC 9a. For X$_{\rm{H2CO}}$, the range is $1.4\times 10^{-10} - 1.4\times10^{-6}$. The range of abundances for H$_2$CO stays relatively constant between the different regions.

![](Abundances_Regions_new.pdf)

# Discussion

In this Section we discuss our results within the framework of determining the physical origin of CH$_3$OH and H$_2$CO and whether they are chemically linked. We first examine whether these two species are tracing shocked gas (Section [5.1](#subsec:comp_hnco_sio) and [5.2](#sec:comp_sulfur)) and then attempt to trace their chemical origin and hence their link (or lack thereof) by examining their abundances (Section [5.3](#sec:abundance_met_form)) and by exploiting the well measured E/A ratio of methanol to track its origin.

![](Bayesian_NTLS/GMC3_temp_dens_allSpecies_newRates.pdf)

## Do methanol and formaldehyde trace the same gas as SiO and HNCO?

The existing evidence for shocks in NGC 253 includes the detection of HNCO and SiO (cite: GB+2000_sio_253; Meier+2015_hncosio_253; Huang+2023), the presence of Class I methanol () masers (cite: Humire+2022), and the elevated fractional abundances of (cite: Harada+2022). Given that HNCO and SiO (cite: Huang+2023) were also observed as part of the ALCHEMI large program, we compare the gas characteristics as traced by these two molecules with our and results. A comparison of these species for GMC 3 is shown in Figure [4](#fig:gmc3_temp_dens), and similar plots for all other GMCs can be found in Appendix [12](#sec:temp_dens_plots).

CH$_3$OH:

:   Methanol is tracing denser environments by at least 1-2 orders of magnitude when compared to HNCO (particularly for the outer regions), and by 2-3 orders of magnitude, when compared to SiO for all GMCs. The temperature traced by , ranging between $T_{kin} \in 21-36$ K, is the lowest among the tracers, with being slightly higher with a range of $T_{kin} \in 25-100$ K across all GMCs except for GMC 1a (cite: Huang+2023). On the other hand, the presence of methanol masers in the CMZ indicates that the thermal lines of CH$_3$OH could still be associated with shocks. The stark differences in physical properties as traced by SiO and CH$_3$OH lead us to exclude methanol as a tracer of fast shocks. On the other hand, methanol could be tracing slow shocks (which would also explain its abundance in a cold gas). In this scenario, two possibilities could explain the difference in gas properties traced by HNCO and CH$_3$OH. The first is that both species trace the same low-velocity-type of shock, but CH$_3$OH is tracing a denser, and possibly older, gas which would make its cooling timescale faster than that of HNCO. This is consistent with the lower gas temperature traced by CH$_3$OH compared to HNCO. The second possibility is that the two species are tracing shocks of different origins (e.g. sporadic shocks, cloud-cloud collisions or outflow-induced shocks; (cite: Huang+2023)). Finally, looking at the abundances of , , and towards the CMZ shown in Fig. [3](#fig:abundances), we see that while the abundance clearly decreases towards the innermost GMCs (i.e. GMC 3, GMC 4, and GMC 6), the trend is less clear for the abundances of and , although their maximum derived abundance is the lowest towards these same GMCs. This could support the hypothesis of tracing shocks which may be different to those traced by SiO and HNCO.

    (cite: Huang2023FaDi) performed chemical modelling of these three species in NGC 253 and found that a high cosmic ray ionization rate (CRIR) suppresses the abundances of these three species. It is therefore possible that the general decrease in abundances is partly due to the high cosmic ray ionization rate observed in the inner GMCs (cite: Holdship+2022; Behrens2022ApJ; Behrens2024). However we also note that chemical models show that all these species are completely destroyed once the CRIR reaches 1000 time the galactic one. Hence it is unlikely that the differences we see among CH$_3$OH, SiO and HNCO are primarily due to the enhanced cosmic ray ionization rate.

H$_2$CO:

:   The gas density traced by lies between those derived from and . consistently probes gas temperatures around 100 K except for GMC 4 and GMC 6 where the derived temperature is $>200$ K, although not very well constrained. H$_2$CO seems therefore to trace a separate gas component that is associated with the heating sources of the GMCs, and not exclusively with shocks. This is also consistent with the fact that contrary to , the abundance of remains constant throughout the CMZ, as shown in Fig. [3](#fig:abundances).

## Comparison with S-bearing species

Most S-bearing species have been found to be tracing slow shocks toward the CMZ of NGC 253 (see (cite: Bouvier+2024)). Comparing the gas parameters traced by methanol with those traced by these S-bearing species (see Figure [4](#fig:gmc3_temp_dens) and Appendix [12](#sec:temp_dens_plots)),

we see in general that the densities and temperatures derived from methanol are close to those derived from the sulfur-bearing species, in particular H$_2$CS, and OCS. This is somewhat consistent with the conclusion that CH$_3$OH may trace slow shocks/post-shock gas. This possibility is also consistent with the fact that Class I methanol masers were detected in the CMZ (cite: Humire+2022). Interestingly, from Fig. [3](#fig:abundances), we can see that the abundance behaviour of and OCS throughout the GMCs seem to be relatively similar, with a clear decrease towards the innermost GMCs. Looking at the other S-bearing species, their abundance does not show such variation across the GMCs, which could indicate that and OCS are tracing similar types of shocks. H$_2$CO, on the other hand, is clearly almost always "displaced" in density and temperature from the gas traced by sulfur bearing species, again supporting our previous conclusion that it is unlikely to trace the same gas as methanol.

## Methanol and formaldehyde abundances

In this section we briefly discuss the derived abundances for methanol and formaldehyde. In particular we note that the abundance range of methanol across the GMCs is consistent with the large ranges found toward massive young stars: e.g. (cite: vandertak2000) find an abundance of $\sim$ 10$^{-9}$ for the coldest sources and of up to $\sim$ 10$^{-7}$ for the warmest sources. They trace the origin of the methanol to icy mantles and hence propose methanol as an evolutionary indicator. While we are unable to correlate in a similar manner our abundances to a temperature gradient, we note that there is a distinct gap in abundance between the inner (3, 4 and 6) and outer (1a, 2b, 7, 8a, 9a) GMCs, with the outer regions being richer in methanol. Moreover, abundances in GMCs 3, 4 and 6 are consistent with those found in infrared dark clouds (e.g. Gomez et al. 2011), possibly implying that the inner regions are at a younger evolutionary stage than the outer regions and in agreement with (cite: vandertak2000) conclusions. (cite: vandertak2000) also present H$_2$CO abundances for the same sample of young massive star forming regions and find that H$_2$CO traces cooler gas than methanol, in contrast to our findings. The derived (cite: vandertak2000) abundances are constant at $10^{-9}$, which is in fact closer to the lower limit for our outer GMCs, with the inner GMCs showing a higher abundance of this species. It is unlikely that we are tracing the same type of gas. Interestingly, they also conclude that H$_2$CO is primarily produced in the gas phase and not correlated to methanol.

## The E/A Ratio in NGC 253 as a probe of methanol formation and destruction

Methanol is characterized by two spin isomers, $E$ and $A$. The latter has three parallel protons in the methyl group, while in the former one of the protons has an anti-parallel spin compared to the others. Their importance lies in the fact that the conversion of one isomer to the other is highly unlikely within the lifetime of an average methanol molecule (Wirström et al. 2011). Hence the ratio of these two isomers should be fixed at the time of the formation of methanol (cite: Kawakita_Kobayashi_2009). In thermal equilibrium (TE)[^9], the relative population between the E- and A- is given by: $$\begin{equation}
\label{eq:EAR}
    EAR \equiv E/A = \frac{\sum_{i} {g}_{i}^{E-type}\exp(-\frac{{E}_{i}^{E-type}}{k_{B}T_{spin}})}{\sum_{i} {g}_{i}^{A-type}\exp(-\frac{{E}_{i}^{A-type}}{k_{B}T_{spin}})} \in [0.0,1.0], 
\end{equation}$$

At cold temperatures (e.g. $10-15$ K), EAR $<1.0$ is expected (cite: Friberg1988; Wirstrom+2011). If CH$_3$OH is formed at warmer temperatures, the EAR will reach its theoretical upper limit of 1.0. Interestingly, the measured EAR in Galactic star-forming regions is not always consistent with the theoretical predictions (cite: Friberg1988; Wirstrom+2011). Indeed, whilst an EAR $\leq$ 1 has been measured in cold dense cores (cite: Friberg1988; Bizzocchi2014; JimenezSerra2021; Megias2023), Galactic outflows (cite: Holdship+2019), and high-mass star-forming regions (cite: Menten1988; zhao2023), EAR \> 1 has been measured in some Galactic high-mass star-forming regions (cite: Wirstrom+2011; purcell2009; kalenskii2016; hernandez-hernandez2019) and proto-brown dwarfs (cite: riaz2023).

From Table [\[tab:Bayesian_gasphys_ch3oh\]](#tab:Bayesian_gasphys_ch3oh) we see that, in most GMCs, the overall isomer ratios, while high, are less than unity. This suggests that, for these GMCs, methanol has formed on the ices. The kinetic temperatures of the GMCs are generally too high to allow methanol formation on the ices, hence the observed methanol is a fossil record of a previous colder gas. However, for the inner GMCs (3, 4 and 6), the EAR is $>$ 1. This may suggest that methanol has formed in the gas phase at higher temperatures. Qualitatively this is also consistent with the picture that the CMZ of NGC 253 is a very dynamic region where large-scale outflows, starburst events, and high cosmic-ray ionization rates (cite: Holdship+2022; Behrens2022ApJ; Behrens2024) are present. On the other hand, proton exchange reactions with with can in principle equalize the A and E methanol abundances (cite: Wirstrom+2011) if these ions are very abundant, which may be the case in NGC 253 due to the high cosmic ray ionization rate (e.g. (cite: Holdship+2022)). In this case, methanol can still form in the ice but its EAR would not be fixed at formation.

In extragalactic environments, there are only three other existing E-/A- ratio measurements. The EAR inferred by (cite: Muller+2021) for PKS 1830-211 at z=0.89 and the EAR estimated by (cite: Huang+2024) for the nearby galaxy NGC 1068 are both fairly close to unity. Both analyses employed non-LTE radiative transfer modeling. On the other hand, the LTE analysis for NGC 253 by (cite: Humire+2022) gave a wide range of EAR, varying between $\sim1.1-5.0$ (cite: Humire+2022) but with a caveat due to the opacity discussed in their Sect. [4.1](#sec:radex_phys). However we note that in the (cite: Muller+2021) and (cite: Huang+2024) studies, the collisional rates for methanol from (cite: Dagdigian_2023) were not employed.

# Conclusions

We performed a multi-transition study using methanol () and formaldehyde () transitions to constrain the physical properties of the gas at GMC scales ($\sim$ 28 pc) in the CMZ of NGC 253 using ALCHEMI data. We conclude the following:

1.  and trace distinct physical environments. Both molecular species show significant differences in kinetic temperatures and densities. is found in high-density ($\approx 10^7$cm$^{-3}$) and low-temperature ($T_{kin}<40$ K) regions, while is associated with lower-density ($\approx 10^4$cm$^{-3}$) but warm gas ($T_{kin}>100$ K).

    The presence of sub-thermal excitation conditions in many and transitions suggests that different non-thermal desorption mechanisms, such as periodic shocks or cosmic ray-induced desorption, may be responsible for maintaining methanol in the gas phase. This suggests that the formation processes of these two species are not directly linked within NGC 253’s starburst environment.

2.  and do not trace the same gas conditions as classical shock tracers like silicon monoxide () and isocyanic acid (). is found in significantly denser regions and appears to trace slow shocks or post-shock gas, rather than fast shocks. In contrast, traces a different gas component, likely associated with local heating sources rather than direct shock interactions.

3.  The density and temperature conditions traced by closely resemble those of sulfur-bearing species like and , further supporting its association with slow shocks. The similar abundance trends of and across the GMCs suggest they may trace the same type of shock-driven chemistry, while other sulfur-bearing species show more uniform distributions. , however, remains distinct, reinforcing that it does not trace the same gas as .

4.  Molecular abundances of methanol suggest an evolutionary trend. The abundance shows a radial gradient, with higher values in the outer GMCs, suggesting different chemical histories or evolutionary stages between the inner and outer CMZ regions. A distinct abundance gap is found between the inner (3, 4, and 6) and outer (1a, 2b, 7, 8a, 9a) GMCs, with the outer regions being methanol-rich. This suggests that the inner GMCs may be at a younger evolutionary stage, similar to infrared dark clouds, and aligns with the idea that abundance may be an indicator of star-forming region evolution.

5.  While previous Galactic studies find that traces cooler gas than methanol, our findings indicate the opposite. The derived abundances in NGC 253 suggest that it is primarily formed in the gas phase, rather than through sublimation from icy mantles. This is consistent with the proposed chemical formation pathway via reactions of and atomic oxygen. The uniformity of its volume density across the GMCs further supports this interpretation.

6.  The E/A isomer ratio (EAR) of methanol provides insight into its formation mechanisms in NGC 253. In most GMCs, EAR values remain below unity, indicating ice-grain formation at colder temperatures. However, in inner GMCs (3, 4, and 6), EAR $> 1$ suggests gas-phase methanol formation at higher temperatures, possibly influenced by strong outflows, starburst activity, and high cosmic-ray ionization rates. Proton exchange reactions with and may further modify the EAR, preventing it from being solely dictated by formation conditions. Compared to other extragalactic environments, the EAR in NGC 253 displays distinct behavior, emphasizing the impact of starburst-driven processes on molecular chemistry.

# Data availability

All of the integrated intensities for the and transitions listed in Tables [\[tab:table_obsinfo_ch3oh\]](#tab:table_obsinfo_ch3oh) and [\[tab:table_obsinfo_h2co\]](#tab:table_obsinfo_h2co) toward the GMC positions listed in Table [1](#tab:GMC_locations) are available [online](https://doi.org/10.5281/zenodo.15442733).

# Acknowledgements

KYH, SV, and MB received funding from the European Research Council (ERC) Advanced Grant MOPPEX 833460.

KYH acknowledges assistance from Allegro, the European ALMA Regional Center node in the Netherlands. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00161.L, ADS/JAO.ALMA#2018.1.00162.S. ALMA is a partnership of ESO (represent- ing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in co-operation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This research has made use of spectroscopic and collisional data from the EMAA database (<https://emaa.osug.fr> and <https://dx.doi.org/10.17178/EMAA>). EMAA is supported by the Observatoire des Sciences de l’Univers de Grenoble (OSUG).

83 natexlab

(ref: Alvarez+2018) Álvarez-Barcia, S., Russ, P., Kästner, J., & Lamberts, T. 2018, MNRAS, 479, 2007

(ref: Behrens2022ApJ) Behrens, E., Mangum, J. G., Holdship, J., et al. 2022, ApJ, 939, 119

(ref: Behrens2024) Behrens, E., Mangum, J. G., Viti, S., et al. 2024, ApJ, 977, 38

(ref: Bendo+2015) Bendo, G. J., Beswick, R. J., D’Cruze, M. J., et al. 2015, MNRAS, 450, L80

(ref: Bizzocchi2014) Bizzocchi, L., Caselli, P., Spezzano, S., & Leonardo, E. 2014, A&A, 569, A27

(ref: Bolatto+2013) Bolatto, A. D., Warren, S. R., Leroy, A. K., et al. 2013, Nature, 499, 450

(ref: Bouvier+2024) Bouvier, M., Viti, S., Behrens, E., et al. 2024, A&A, 689, A64

(ref: ultranest21) Buchner, J. 2021, The Journal of Open Source Software, 6, 3001

(ref: Butterworth+2024) Butterworth, J., Viti, S., Van der Werf, P. P., et al. 2024, A&A, 686, A31

(ref: Dagdigian_2023) Dagdigian, P. J. 2023, MNRAS, 527, 2209

(ref: Endres+2016) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95

(ref: Friberg1988) Friberg, P., Madden, S. C., Hjalmarson, A., & Irvine, W. M. 1988, A&A, 195, 281

(ref: Fuchs+2009) Fuchs, G. W., Cuppen, H. M., Ioppolo, S., et al. 2009, A&A, 505, 629

(ref: GB+2000_sio_253) Garcı́a-Burillo, S., Martı́n-Pintado, J., Fuente, A., & Neri, R. 2000, A&A, 355, 499

(ref: Goldsmith+2012) Goldsmith, P. F., Langer, W. D., Pineda, J. L., & Velusamy, T. 2012, ApJS, 203, 13

(ref: Gorski2017) Gorski, M., Ott, J., Rand, R., et al. 2017, ApJ, 842, 124

(ref: Guzman2013A&A) Guzmán, V. V., Goicoechea, J. R., Pety, J., et al. 2013, A&A, 560, A73

(ref: Harada+2022) Harada, N., Martı́n, S., Mangum, J. G., et al. 2022, ApJ, 938, 80

(ref: Harada+2021) Harada, N., Martı́n, S., Mangum, J. G., et al. 2021, ApJ, 923, 24

(ref: Herbst_vanDishoeck_2009) Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427

(ref: hernandez-hernandez2019) Hernández-Hernández, V., Kurtz, S., Kalenskii, S., et al. 2019, AJ, 158, 18

(ref: Holdship+2022) Holdship, J., Mangum, J. G., Viti, S., et al. 2022, ApJ, 931, 89

(ref: Holdship+2019) Holdship, J., Viti, S., Codella, C., et al. 2019, ApJ, 880, 138

(ref: Holdship+2021_SpectralRadex) Holdship, J., Viti, S., Martı́n, S., et al. 2021, A&A, 654, A55

(ref: Huang+2024) Huang, K. Y., Abbink, D., Viti, S., & Garcı́a-Burillo, S. 2024, A&A, 688, A130

(ref: Huang2023FaDi) Huang, K.-Y. & Viti, S. 2023, FaDi, 245, 181

(ref: Huang+2023) Huang, K. Y., Viti, S., Holdship, J., et al. 2023, A&A, 675, A151

(ref: Humire+2022) Humire, P. K., Henkel, C., Hernández-Gómez, A., et al. 2022, A&A, 663, A33

(ref: Huttemeister+1998) Hüttemeister, S., Dahmen, G., Mauersberger, R., et al. 1998, A&A, 334, 646

(ref: J-S+2008_shocktracers) Jiménez-Serra, I., Caselli, P., Martı́n-Pintado, J., & Hartquist, T. W. 2008, A&A, 482, 549

(ref: JimenezSerra2021) Jiménez-Serra, I., Vasyunin, A. I., Spezzano, S., et al. 2021, ApJ, 917, 44

(ref: kalenskii2016) Kalenskii, S. V. & Kurtz, S. 2016, Astronomy Reports, 60, 702

(ref: Kawakita_Kobayashi_2009) Kawakita, H. & Kobayashi, H. 2009, ApJ, 693, 388

(ref: Krieger2020ApJ) Krieger, N., Bolatto, A. D., Koch, E. W., et al. 2020, ApJ, 899, 158

(ref: Krieger+2019) Krieger, N., Bolatto, A. D., Walter, F., et al. 2019, ApJ, 881, 43

(ref: nautilus) Lange, J. U. 2023, MNRAS, 525, 3181

(ref: Lehmer+2013) Lehmer, B. D., Wik, D. R., Hornschemeier, A. E., et al. 2013, ApJ, 771, 134

(ref: Leroy+2015) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2015, ApJ, 801, 25

(ref: Levy+2022) Levy, R. C., Bolatto, A. D., Leroy, A. K., et al. 2022, ApJ, 935, 19

(ref: Loomis2015ApJL) Loomis, R. A., Cleeves, L. I., Öberg, K. I., Guzman, V. V., & Andrews, S. M. 2015, ApJL, 809, L25

(ref: Mangum+2019) Mangum, J. G., Ginsburg, A. G., Henkel, C., et al. 2019, ApJ, 871, 170

(ref: Mangum_Wootten_1993) Mangum, J. G. & Wootten, A. 1993, ApJS, 89, 123

(ref: ALCHEMI_main_2021) Martı́n, S., Mangum, J. G., Harada, N., et al. 2021, A&A, 656, A46

(ref: Martin+2008_HNCO_galactic) Martı́n, S., Requena-Torres, M. A., Martı́n-Pintado, J., & Mauersberger, R. 2008, ApJ, 678, 245

(ref: sio_MP+1997) Martı́n-Pintado, J., de Vicente, P., Fuente, A., & Planesas, P. 1997, ApJL, 482, L45

(ref: McCarthy+1987) McCarthy, P. J., van Breugel, W., & Heckman, T. 1987, AJ, 93, 264

(ref: McCormick+2013) McCormick, A., Veilleux, S., & Rupke, D. S. N. 2013, ApJ, 774, 126

(ref: Megias2023) Megı́as, A., Jiménez-Serra, I., Martı́n-Pintado, J., et al. 2023, MNRAS, 519, 1601

(ref: Meier+2015_hncosio_253) Meier, D. S., Walter, F., Bolatto, A. D., et al. 2015, ApJ, 801, 63

(ref: Melioli2004A&A) Melioli, C. & de Gouveia Dal Pino, E. M. 2004, A&A, 424, 817

(ref: Menten1988) Menten, K. M., Walmsley, C. M., Henkel, C., & Wilson, T. L. 1988, A&A, 198, 253

(ref: Muller+2017) Müller, H. S. P. & Lewen, F. 2017, Journal of Molecular Spectroscopy, 331, 28

(ref: Muller+2005) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: Muller+2021) Muller, S., Ubachs, W., Menten, K. M., Henkel, C., & Kanekar, N. 2021, A&A, 652, A5

(ref: MS+2010) Müller-Sánchez, F., González-Martı́n, O., Fernández-Ontiveros, J. A., Acosta-Pulido, J. A., & Prieto, M. A. 2010, ApJ, 716, 1166

(ref: Pickett+1998) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: purcell2009) Purcell, C. R., Longmore, S. N., Burton, M. G., et al. 2009, MNRAS, 394, 323

(ref: CH3OH_mol_data_2010) Rabli, D. & Flower, D. R. 2010, MNRAS, 406, 95

(ref: Rekola+2005) Rekola, R., Richer, M. G., McCall, M. L., et al. 2005, MNRAS, 361, 330

(ref: riaz2023) Riaz, B., Thi, W. F., & Machida, M. N. 2023, MNRAS, 522, 4934

(ref: Rico-Villas+2020) Rico-Villas, F., Martı́n-Pintado, J., González-Alfonso, E., Martı́n, S., & Rivilla, V. M. 2020, MNRAS, 491, 4573

(ref: Roberts2007MNRAS) Roberts, J. F., Rawlings, J. M. C., Viti, S., & Williams, D. A. 2007, MNRAS, 382, 733

(ref: hnco+RF+2010) Rodrı́guez-Fernández, N. J., Tafalla, M., Gueth, F., & Bachiller, R. 2010, A&A, 516, A98

(ref: Sakamoto+2011) Sakamoto, K., Mao, R.-Q., Matsushita, S., et al. 2011, ApJ, 735, 19

(ref: Santos+2022) Santos, J. C., Chuang, K.-J., Lamberts, T., et al. 2022, ApJL, 931, L33

(ref: Schilke+1997) Schilke, P., Walmsley, C. M., Pineau des Forets, G., & Flower, D. R. 1997, A&A, 321, 293

(ref: Schoier2005A&A) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369

(ref: Simons+2020) Simons, M. A. J., Lamberts, T., & Cuppen, H. M. 2020, A&A, 634, A52

(ref: Strickland+2000) Strickland, D. K., Heckman, T. M., Weaver, K. A., & Dahlem, M. 2000, AJ, 120, 2965

(ref: Strickland+2002) Strickland, D. K., Heckman, T. M., Weaver, K. A., Hoopes, C. G., & Dahlem, M. 2002, ApJ, 568, 689

(ref: Suutarinen+2014) Suutarinen, A. N., Kristensen, L. E., Mottram, J. C., Fraser, H. J., & van Dishoeck, E. F. 2014, MNRAS, 440, 1844

(ref: Tanaka2024) Tanaka, K., Mangum, J. G., Viti, S., et al. 2024, ApJ, 961, 18

(ref: Turner1985) Turner, B. E. 1985, ApJ, 299, 312

(ref: radex_vandertak_2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: vandertak2000) van der Tak, F. F. S., van Dishoeck, E. F., & Caselli, P. 2000, A&A, 361, 327

(ref: Walter+2017) Walter, F., Bolatto, A. D., Leroy, A. K., et al. 2017, ApJ, 835, 265

(ref: Westmoquette+2011) Westmoquette, M. S., Smith, L. J., & Gallagher, J. S., I. 2011, MNRAS, 414, 3719

(ref: H2CO_mole_data) Wiesenfeld, L. & Faure, A. 2013, MNRAS, 432, 2573

(ref: Wirstrom+2011) Wirström, E. S., Geppert, W. D., Hjalmarson, Å., et al. 2011, A&A, 533, A24

(ref: Woodall2007AandA) Woodall, J., Agúndez, M., Markwick-Kemper, A. J., & Millar, T. J. 2007, A&A, 466, 1197

(ref: Xu+2008) Xu, L.-H., Fisher, J., Lees, R. M., et al. 2008, Journal of Molecular Spectroscopy, 251, 305

(ref: zhao2023) Zhao, J. Y., Zhang, J. S., Wang, Y. X., et al. 2023, ApJS, 266, 29

(ref: Zinchenko+2000) Zinchenko, I., Henkel, C., & Mao, R. Q. 2000, A&A, 361, 1079

#  and spectra

The and spectra sampled from GMC 6 are shown in Figures [5](#fig:Spec_I) and [6](#fig:Spec_II). Table [\[tab:offsets\]](#tab:offsets) lists velocity offsets for each and transition group.

|                                             |
|:--------------------------------------------|
| ![image](SpecKs/paperKSpec_CH3OH_file0.png) |

|                                             |
|:--------------------------------------------|
| ![image](SpecKs/paperKSpec_CH3OH_file1.png) |

|                                             |
|:--------------------------------------------|
| ![image](SpecKs/paperKSpec_CH3OH_file2.png) |

|                                             |
|:--------------------------------------------|
| ![image](SpecKs/paperKSpec_CH3OH_file3.png) |

|                                             |
|:--------------------------------------------|
| ![image](SpecKs/paperKSpec_CH3OH_file4.png) |

|                                            |
|:-------------------------------------------|
| ![image](SpecKs/paperKSpec_H2CO_file0.png) |

|                                            |
|:-------------------------------------------|
| ![image](SpecKs/paperKSpec_H2CO_file1.png) |

.

|                              |                        |          |     |     |     |     |
|:----------------------------:|:----------------------:|:--------:|:---:|:---:|:---:|:---:|
| Species and Transition Group |       Transition       |    dv    |     |     |     |     |
|                              |                        |  (km/s)  |     |     |     |     |
|   CH$_3$OH near 96.74 GHz    | E- ($2_{-1} - 1_{-1}$) |   6.24   |     |     |     |     |
|                              |    E- ($2_0 - 1_0$)    | $-9.84$  |     |     |     |     |
|                              |    E- ($2_1 - 1_1$)    | $-43.79$ |     |     |     |     |
|                              |    A- ($2_0 - 1_0$)    |   0.0    |     |     |     |     |
|   CH$_3$OH near 157.26 GHz   |  E- ($4_0 - 4_{-1}$)   |  47.22   |     |     |     |     |
|                              |  E- ($1_0 - 1_{-1}$)   |   0.00   |     |     |     |     |
|                              |  E- ($3_0 - 3_{-1}$)   | $-2.87$  |     |     |     |     |
|                              |  E- ($2_0 - 2_{-1}$)   | $-9.89$  |     |     |     |     |
|   CH$_3$OH near 165.07 GHz   |    E- ($1_1 - 1_0$)    |   0.00   |     |     |     |     |
|                              |    E- ($2_1 - 2_0$)    | $-19.90$ |     |     |     |     |
|                              |   E- ($14_6 - 15_5$)   | $-43.92$ |     |     |     |     |
|                              |    E- ($3_1 - 3_0$)    | $-89.12$ |     |     |     |     |
|   H$_2$CO near 291.38 GHz    | o- ($4_{32} - 3_{31}$) |   0.00   |     |     |     |     |
|                              | o- ($4_{31} - 3_{30}$) | $-3.89$  |     |     |     |     |

\

# Moment-0 maps

The and integrated intensity (Moment-0) images for all transitions in this study are shown in Figures [7](#fig:all_ch3oh_mom0) and [8](#fig:all_h2co_mom0), respectively.

![](moment0_maps/CH3OH_allMoments.pdf)

![](moment0_maps/H2CO_allMoments.pdf)

# All corner plots

and corner plots for GMC 1a, 2b, 4, and 6 (Figure [9](#fig:corners_1a_2b_3_4)) and GMCs 7, 8a, and 9a. (Figure [10](#fig:corners_6_7_8a_9a)).

|                                                           |
|:----------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC1a_corner_allMols_newRates.pdf) |

|                                                           |
|:----------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC2b_corner_allMols_newRates.pdf) |

|                                                          |
|:---------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC4_corner_allMols_newRates.pdf) |

|                                                          |
|:---------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC6_corner_allMols_newRates.pdf) |

|                                                          |
|:---------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC7_corner_allMols_newRates.pdf) |

|                                                           |
|:----------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC8a_corner_allMols_newRates.pdf) |

|                                                           |
|:----------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC9a_corner_allMols_newRates.pdf) |

# Abundances

We list in Table [\[tab:abundance_range\]](#tab:abundance_range) the abundances derived for HNCO, SiO, and the S-bearing species presented in Fig. [3](#fig:abundances). To calculate the abundances, we used the column densities of HNCO and SiO from (cite: Huang+2023) and of the S-bearing species from (cite: Bouvier+2024). We used the same H$_2$ column densities as for CH$_3$OH and H$_2$CO, and we applied the beam filling factor derived for each region and each species from the non-LTE analyses performed in (cite: Huang+2023) and (cite: Bouvier+2024). The beam filling factor was calculated from the source’s size using the formula for the beam filling factor (Section [4](#sec:radex)).

| Region | X(SiO) | X(HNCO) | X(OCS) | X(H$_2$CS) | X(H$_2$S) | X(CS) |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| GMC 1a | $8.3\times 10^{-10}-1.3\times10^{-6}$ | $1.5\times 10^{-8}-3.1\times10^{-7}$ | $2.7\times 10^{-9}-1.0\times10^{-7}$ | $5.0\times 10^{-10}-3.5\times10^{-8}$ | ... | $4.8\times 10^{-10}-1.2\times10^{-8}$ |
| GMC 2b | $2.8\times 10^{-10}-1.5\times10^{-6}$ | $1.3\times 10^{-9}-9.5\times10^{-8}$ | $3.0\times 10^{-9}-6.7\times10^{-8}$ | $1.5\times 10^{-11}-9.0\times10^{-8}$ | ... | $1.6\times 10^{-10}-2.7\times10^{-10}$ |
| GMC 3 | $1.8\times 10^{-10}-1.4\times10^{-8}$ | $1.3\times 10^{-10}-1.6\times10^{-8}$ | $2.5\times 10^{-10}-6.0\times10^{-9}$ | $1.3\times 10^{-10}-2.8\times10^{-9}$ | $1.6\times10^{-9}-6.4\times10^{-9}$ | $3.7\times 10^{-10}-3.0\times10^{-9}$ |
| GMC 4 | $1.3\times 10^{-10}-2.8\times10^{-8}$ | $1.1\times 10^{-11}-1.8\times10^{-8}$ | $2.8\times 10^{-10}-4.7\times10^{-10}$ | $2.9\times 10^{-12}-1.1\times10^{-8}$ | $1.6\times10^{-9}-8.1\times10^{-9}$ | $1.6\times 10^{-10}-4.0\times10^{-9}$ |
| GMC 6 | $3.4\times 10^{-10}-2.8\times10^{-8}$ | $6.2\times 10^{-11}-1.3\times10^{-8}$ | $2.3\times 10^{-10}-4.1\times10^{-9}$ | $4.3\times 10^{-11}-5.4\times10^{-8}$ | $3.0\times10^{-9}-1.7\times10^{-8}$ | $1.8\times 10^{-10}-9.5\times10^{-9}$ |
| GMC 7 | $1.2\times 10^{-8}-4.5\times10^{-7}$ | $3.3\times 10^{-9}-1.1\times10^{-7}$ | $3.6\times 10^{-10}-6.5\times10^{-8}$ | $3.3\times 10^{-9}-6.2\times10^{-8}$ | $4.0\times10^{-9}-1.5\times10^{-8}$ | $1.4\times 10^{-9}-3.3\times10^{-8}$ |
| GMC 8a | $3.7\times 10^{-10}-1.2\times10^{-6}$ | $1.4\times 10^{-9}-9.5\times10^{-9}$ | $1.6\times 10^{-9}-1.5\times10^{-7}$ | $1.0\times 10^{-10}-2.0\times10^{-7}$ | ... | $1.4\times 10^{-10}-2.0\times10^{-8}$ |
| GMC 9a | $3.9\times 10^{-10}-9.7\times10^{-7}$ | $1.7\times 10^{-9}-1.7\times10^{-7}$ | $1.0\times 10^{-9}-3.0\times10^{-7}$ | $4.0\times 10^{-11}-9.0\times10^{-8}$ | ... | $5.7\times 10^{-11}-5.0\times10^{-8}$ |

# Temperature versus density plots

Kinetic temperature versus volume density plots showing the same information as Figure [4](#fig:gmc3_temp_dens) but for GMCs 1a, 2b, 4, 6, 7, 8a, and 9a.

|                                                                 |
|:----------------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC1a_temp_dens_allSpecies_newRates.pdf) |

|                                                                 |
|:----------------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC2b_temp_dens_allSpecies_newRates.pdf) |

|                                                                |
|:---------------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC4_temp_dens_allSpecies_newRates.pdf) |

|                                                                |
|:---------------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC6_temp_dens_allSpecies_newRates.pdf) |

|                                                                |
|:---------------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC7_temp_dens_allSpecies_newRates.pdf) |

|                                                                 |
|:----------------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC8p_temp_dens_allSpecies_newRates.pdf) |

|                                                                 |
|:----------------------------------------------------------------|
| ![image](Bayesian_NTLS/GMC9p_temp_dens_allSpecies_newRates.pdf) |

[^1]: bouvier@strw.leidenuniv.nl

[^2]: Jansky Fellow of the National Radio Astronomy Observatory

[^3]: <https://github.com/keflavich/cube-line-extractor>

[^4]: https://spectralradex.readthedocs.io

[^5]: <https://emaa.osug.fr/>

[^6]: As a side note, we find that `Nautilus` is substantially more efficient than `UltraNest` (cite: ultranest21) (cite: Holdship+2022; Behrens2022ApJ; Huang+2023), while providing indistinguishable results.

[^7]: At n~H2~ $\sim 10^{7}$ cm^-3^ the freeze-out time scale $\sim 10^{9}/\rm{n_{H2}} \sim 10^2$ yrs; this can be longer if one considers non-thermal desorption (cite: Roberts2007MNRAS)

[^8]: (cite: Mangum+2019) assumed an excitation temperature T = 150 K and a beam filling factor of 1

[^9]: This is generally expected for reactions taking place on ice grains.

</paper>

Write the methods card for this paper.