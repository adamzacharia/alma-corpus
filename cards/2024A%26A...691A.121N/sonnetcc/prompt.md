# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...691A.121N\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...691A.121N",
 "title": "A 260 pc resolution ALMA map of HCN(1─0) in the galaxy NGC 4321",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Neumann, Lukas",
 "n_authors": 27,
 "arxiv_id": "2406.12025",
 "doi": "10.1051/0004-6361/202449496",
 "alma_projects_linked_by_archive": [
  "2015.1.00956.S",
  "2017.1.00815.S",
  "2011.0.00004.SV"
 ]
}
```

Paper text:
<paper>
# A 260 pc resolution ALMA map of HCN(1–0) in the galaxy NGC 4321

# Introduction

Galactic observations of dust in star-forming regions show that stars form in dense substructures, where the inferred star formation rate (SFR) is found to be linearly related to the amount of dense gas (cite: Heiderman2010; Lada2010; Lada2012; Evans2014). (cite: Gao2004) found that this linear relation also holds for global measurements of galaxies when tracing the SFR with the total infrared (IR) luminosity and the dense gas mass ($M_{\text{dense}}$) via the luminosity of $\text{HCN(1--0)}$. Molecular line emission from HCN has an effective critical density of $\ensuremath{n_{\text{eff}}}\sim\SI{5e3}{\per\cubic\cm}$, which is at least one order of magnitude higher than that of CO (cite: Shirley2015). Over the last two decades, many studies aimed at mapping HCN across other galaxies (cite: Usero2015; Bigiel2016; Gallagher2018a; Jimenez-Donaire2019; Querejeta2019; Sanchez-Garcia2022; Neumann2023a). These observations of star-forming, spiral galaxies and numerical works (cite: Onus2018) tell us that the IR luminosity, tracing embedded SFR, is tightly (scatter of $\pm\SI{0.4}{\dex}$) and linearly correlated with the HCN luminosity, tracing $M_{\text{dense}}$, spanning ten orders of magnitude (cite: Jimenez-Donaire2019; Neumann2023a).

Despite the clear relation between SFR and dense gas, there is still a total scatter of $\approx\SI{1}{dex}$ that cannot solely be explained by measurement uncertainties, instead indicating that the dense gas star formation efficiency ($\text{SFR}/\ensuremath{M_{\text{dense}}}\equiv\ensuremath{\text{SFE}_{\text{dense}}}$) depends on other physical quantities. Over the last decade, resolved, kpc-scale observations of nearby galaxies (cite: Usero2015; Bigiel2016; Gallagher2018a; Gallagher2018b; Jimenez-Donaire2019; Querejeta2019; Sanchez-Garcia2022; Neumann2023a) have studied the variation of spectroscopic ratios, like HCN/CO, a proxy of the dense gas fraction ($\ensuremath{f_{\text{dense}}}\equiv \ensuremath{M_{\text{dense}}}/\ensuremath{M_{\text{mol}}}$, where $M_{\text{mol}}$ is the molecular gas mass), and IR/HCN, a proxy of the dense gas star formation efficiency ($\text{SFE}_{\text{dense}}$) with environmental properties, such as the stellar mass surface density ($\Sigma_{\star}$), the molecular gas surface density ($\Sigma_{\text{mol}}$) or the hydrostatic pressure in the ISM disc ($P_{\text{DE}}$). These studies find that $f_{\text{dense}}$ and $\text{SFE}_{\text{dense}}$ vary systematically with the environment. In particular, $f_{\text{dense}}$ is significantly enhanced while $\text{SFE}_{\text{dense}}$ is systematically suppressed in high-surface density, high-pressure regions indicating a connection between the properties of molecular clouds and their host environment. These results are also supported by studies of the Milky Way central molecular zone (CMZ), where $\text{SFE}_{\text{dense}}$ is found to be systematically lower than across the Milky Way disc (cite: Longmore2013; Kruijssen2014b; Henshaw2023).

In pioneering work, (cite: Gallagher2018b) find systematic correlations between the kpc-scale $f_{\text{dense}}$, $\text{SFE}_{\text{dense}}$, and the molecular gas surface density measured at giant molecular cloud (GMC) scales, i.e. $\sim\SI{100}{\parsec}$. Building upon this, (cite: Neumann2023a) use HCN observations of 25 nearby galaxies from the “ACA Large-sample Mapping Of Nearby galaxies in Dense gas” (ALMOND) survey in order to compare the kpc-scale spectroscopic line ratios with the properties of the molecular gas as traced by $\text{CO(2--1)}$ on $\sim\SI{100}{\parsec}$ scales from the “Physics at High ANgular resolution GalaxieS”–“Atacama Large Millimetre Array” (PHANGS–ALMA) survey (cite: Leroy2021b). They showed that $f_{\text{dense}}$ increases and $\text{SFE}_{\text{dense}}$ decreases with increasing surface density ($\Sigma_{\text{mol}}$) and velocity dispersion ($\sigma_{\text{mol}}$) of the molecular gas measured at GMC scales. These results are also in agreement with predictions from models describing the star formation in turbulent clouds (cite: Padoan2002; Krumholz2005; Krumholz2007) and the ISM disc structure (cite: Ostriker2010), hence yielding a coherent picture between dense gas, star formation and turbulent cloud models. In particular, these results have shown that $\text{SFE}_{\text{dense}}$ is not universal but depends on the environment, and that density-sensitive line ratios like HCN/CO are powerful extragalactic tools to trace the underlying density structure at $\sim\SI{100}{\parsec}$ scale even if measured at kpc-scales.

Previous studies of the relationship between dense gas, star formation and environment (cite: Usero2015; Gallagher2018a; Gallagher2018b; Jimenez-Donaire2019; Neumann2023a) were thus limited to mapping dense gas at kpc-scales. There exist only a few $\sim\SI{100}{\parsec}$ resolution maps of HCN, or other dense gas tracers ((cite: Kepley2014), M82, 200; (cite: Chen2017), outer spiral arm of M51, 150; (cite: Harada2018), NGC 3256, 200; (cite: Viaene2018), GMCs in M31; 100; (cite: Kepley2018), IC10, 34; (cite: Querejeta2019), M51, 100; (cite: Harada2019), circumnuclear ring of M83, 60; (cite: Beslic2021), NGC 3627, 100; (cite: Martin2021), NGC 253, 250 with the potential of resolutions $<\SI{50}{\parsec}$; (cite: Eibensteiner2022), central 2   of NGC 6946, 150; (cite: Sanchez-Garcia2022), NGC 1068, 60; (cite: Stuber2023)., M51, 125; Bešlić et al. subm., NGC 253, 300). However, these are typically less sensitive and they target certain regions but not the full disc, compared to the observations presented here. Many of these works that mapped the whole molecular gas disc did not detect much emission in individual sight lines outside of galaxy centres and hence had to average over larger regions, e.g. via spectral stacking (cite: Schruba2011; Caldu-Primo2013; Jimenez-Donaire2017; Jimenez-Donaire2019; Neumann2023b), at the cost of spatial information. Apart from a few exceptions (M51, NGC 253, see references above), there are no deep, wide-field studies of these dense gas ratios at sub-kpc scales, which detect individual sight lines in different morphological environments across the whole molecular gas disc out to 10   in galactocentric radius. Such a study is, however, needed to study the sub-kpc structured ISM without blending many regions together that may have substantially different environmental and dynamical conditions for the formation of dense gas and its conversion to stars. We need $\lesssim\SI{500}{\parsec}$ scale resolution in order to resolve environments like the centre (size of $\sim\SI{1}{\kilo\parsec}$), spiral arms (width of $\sim\SI{1}{\kilo\parsec}$) and bar ends (size of $\sim 0.5-\SI{1}{\kilo\parsec}$).

In this work, we present new ALMA observations of dense molecular gas tracers, including $\text{HCN(1--0)}$, $\text{HCO}^+\text{(1--0)}$, and $\text{CS(2--1)}$, across the nearby spiral galaxy $\mathrm{NGC\,4321}$ at $\ang{;;3.5}\sim\SI{260}{\parsec}$ resolution covering the full disc, i.e. out to $1.1\, r_{25}$. These data are paired with $\text{CO(2--1)}$ observations from PHANGS–ALMA (cite: Leroy2021b), tracing the bulk molecular gas, and extinction corrected $\text{H}\alpha$ from PHANGS–MUSE (cite: Emsellem2022), as well as 21 $\mu$ m observations from PHANGS–JWST (cite: Lee2023) and 33 GHz observations from VLA (cite: Linden2020), used to trace the SFR. These give us one of the best high-resolution, high-sensitivity data sets combining interferometric and total power observations of high critical-density molecular line emission accompanied by the most robust tracers of SFR across the full disc of a nearby star-forming galaxy.

The paper is structured as follows. In Sect. [2](#sec:data), we present the observations and ancillary data of $\mathrm{NGC\,4321}$ used in this work, including new ALMA HCN observations. In Sect. [3](#sec:methods), we describe the methods to derive physical quantities from the observations, including the dense gas content, star formation rate and ISM pressure. Then, in Sect. [4](#sec:results), we show the results, where we analyse the dense gas spectroscopic line ratios and their variation with environment, which are discussed in Sect. [5](#sec:discussion). Finally, we conclude and summarise the key findings in Sect. [6](#sec:conclusions).

# Observations

![](Figures/ngc4321_jwst_rgb_image_with_hcn_contours_compressed.pdf)

![](Figures/ngc4321_maps_data_compressed.pdf)

## The target – NGC 4321

We selected $\mathrm{NGC\,4321}$ for this study as previous ALMA/IRAM mapping showed clear HCN detections, supporting data covers almost all aspects of the ISM and galactic structure, and its favourable distance to obtain a wide area map while still resolving, e.g., the galactic centre, bar, arms and other regions. $\mathrm{NGC\,4321}$(main properties listed in Table [1](#tab:target)) is a well-studied, spiral, barred (cite: Querejeta2021) galaxy (Hubble classification: SABbc) that contains a large reservoir of molecular gas ($M_{\ensuremath{\text{H}_2}}=\SI{7.77e9}{\Msun}$; (cite: Leroy2021b)), is actively forming stars ($\mathrm{SFR}=\SI{3.56}{\Msun\per\year}$; (cite: Leroy2019)) and can be observed relatively face-on ($i=\SI{38.5}{\degree}$; (cite: Lang2020)). Fig. [1](#fig:jwst_map) shows a JWST three-colour image overlaid with HCN contours from this work that highlight the spiral arm structure of the galaxy, seen in dust, gas and star formation. At a distance of $d=\SI{15.2}{\mega\parsec}$ (cite: Anand2021) it is relatively nearby, allowing access to GMC scales ($<\SI{100}{\parsec}$) at $\sim\ang{;;1}$ angular resolution.

Moreover, $\mathrm{NGC\,4321}$ is a spiral galaxy with similar stellar mass ($M_\star=\SI{5.6e10}{\Msun}$) to our Galaxy ($M_\star=\SI{6.1e10}{\Msun}$, (cite: Licquia2015)), making it an interesting object to compare with Galactic studies. $\mathrm{NGC\,4321}$ has been extensively studied as part of large observing campaigns like PHANGS–ALMA (cite: Leroy2021b), mapping $\text{CO(2--1)}$ across the full disc of the galaxy at $\sim\ang{;;1}\sim\SI{100}{\parsec}$ resolution, as well as EMPIRE (cite: Jimenez-Donaire2019) and ALMOND (cite: Neumann2023a) mapping various dense gas tracers including HCN and HCO$^+$ with the IRAM 30-m telescope and the Atacama Compact Array (ACA), respectively, at kpc scales. Furthermore, $\mathrm{NGC\,4321}$ was part of the ALMA science verification $\text{CO(1--0)}$ observations (cite: Pan2017) and has high-quality maps of $\text{H}\,{\tiny\text{I}}$(HERACLES; (cite: Leroy2009)), stellar structure (cite: Sheth2010), star formation tracers ($\text{H}\alpha$ from MUSE; (cite: Emsellem2022)), as well as near and mid-infrared maps from the James Webb Space Telescope (cite: Lee2023).

We show a compilation of the key observations used in this work in Figure [2](#fig:maps_observations).

| Property | Value |
|:---|:---|
| Alternative Name | M100 |
| Right Ascension (J2000)$^{\rm (a)}$ |  12°21′54.9″ |
| Declination (J2000)$^{\rm (a)}$ | 04°28′25.5″ |
| Inclination, $i^{\rm (b)}$ | $(38.5\pm 2.4)^\circ$ |
| Position Angle$^{\rm (b)}$ | $(156.2\pm 1.7)^\circ$ |
| Radius, $r_{25}^{\rm (d)}$ | $(182.9\pm 47.3)$$''$ |
| Systemic Velocity, $V_{\rm LSR}^{\rm (b)}$ | $(1572\pm 5)\,$km s$^{-1}$ |
| Distance, $d^{\rm (a)}$ | $(15.21\pm 0.49)$ Mpc |
| Linear Scale | 73.5 pc/$''$ |
| Matched Beam Size | $\SI{3.5}{\ensuremath{''}} \sim \SI{260}{\parsec}$ |
| Morphology$^{\rm (e)}$ | SAB(s)bc |
| ${\rm SFR}^{\rm (c)}$ | $(3.56\pm 0.92)$  M$_\odot$ yr$^{-1}$ |
| $\log_{10}(M_\star/\mathrm{M}_\odot)^{\rm (c)}$ | $10.75\pm 0.11$ |

: Properties of NGC 4321.

**Notes:**\
(a) (cite: Anand2021);\
(b) (cite: Lang2020);\
(c) (cite: Leroy2019);\
(d) HyperLeda database (cite: Makarov2014);\
(e) NASA Extragalactic Database (NED).

## New ALMA maps of HCN

In this work, we present ALMA Band-3 observations (2017.1.00815.S; PI.: Molly Gallagher) which mapped $\text{HCN(1--0)}$(along with $\text{HCO}^+\text{(1--0)}$ and $\text{CS(2--1)}$) across the full disc of the galaxy $\mathrm{NGC\,4321}$ at a high angular resolution of 3.5″ using 216.7 h of ALMA telescope time. The observations combine interferometric observations from the 12-m array (18.1 h observing time) with the ACA consisting of the 7-m array (73.4 h) and the 12-m dishes observing in total power (TP) mode (125.2 h). The mapped area on the sky is $\ang{;;200}\times\ang{;;120}$ large created via a mosaic consisting of 27 Nyquist-spaced pointings with the 12-m array. The spectral setup encompasses four spectral windows, each with a bandwidth of 1875 MHz and a channel width of $\SI{976}{\kilo\hertz}$. The first window, centred at 88.5 GHz targets $\text{HCN(1--0)}$  (88.6 GHz) and $\text{HCO}^+\text{(1--0)}$  (89.2 GHz). The second window at 87.0 GHz covers SiO(2–1) (86.9 GHz) and isotopologues of HCN and HCO$^+$, i.e. H$^{13}$CN (1–0), H$^{13}$CO$^+$ (1–0). The third spectral window at 98.5 GHz comprises $\text{CS(2--1)}$(97.9809533 GHz). The fourth spectral window at 100 GHz is used to detect continuum emission. The channel width of $\approx\SI{3}{\kilo\metre\per\second}$ is sufficient to resolve the spectral lines across the whole disc of the galaxy, and the bandwidth of $\approx\SI{6000}{\kilo\metre\per\second}$ allows mapping all lines over the full velocity extent.

The data reduction was performed using the PHANGS–ALMA pipeline (details can be found in (cite: Leroy2021a)) which utilises the standard ALMA data reduction package `CASA` (cite: casa_package). In this first study, we focus on $\text{HCN(1--0)}$(hereafter HCN) as the brightest proxy for dense molecular gas. The resulting HCN position-position-velocity cube has $\sim\SI{8}{\milli\kelvin}$ noise per 5 km s^−1^ channel. The high resolution, which corresponds to 260 pc physical scales allows us to resolve individual environmental regions including the centre, bar, bar ends, spiral arms and interarm regions (Fig. [3](#fig:hcn_ratio_maps), right panel) yielding detection of 302 independent lines of sight in HCN emission (see Sect. [3.1](#sec:methods:mom0_maps) for details on masking and derivation of moment-0 maps).

## Ancillary data

In addition to the new HCN data, tracing dense molecular gas, we use CO observations to trace the bulk molecular gas (Sect. [3.2](#sec:methods:sigmol)) and $\text{H}\alpha$ observations to trace SFR (Sect. [3.4](#sec:methods:sfr_halpha)). Furthermore, we include $\text{H}\,{\tiny\text{I}}$ 21-cm observations (Sect. [7.2](#sec:appendix:hi)) and 3.6 $\mu$ m infrared maps (Sect. [7.3](#sec:appendix:mstar)) to trace the atomic gas and the stellar mass content, respectively. In the Appendix, we further present additional tracers of the SFR, i.e. F2100W hot dust observations from JWST (Sect. [9.1](#sec:appendix:sfr_21mu)) and 33 GHz free-free emission from the VLA (Sect. [9.2](#sec:appendix:sfr_33ghz)), supporting the use of $\text{H}\alpha$ as the primary SFR tracer in this work.

# Methods

## Integrated intensity maps

We produce integrated intensity maps (moment-0 maps) from the CO and HCN position-position-velocity (PPV) cubes following (cite: Neumann2023a). The methodology goes back to (cite: Schruba2011) and was utilised in several studies such as EMPIRE (cite: Jimenez-Donaire2019), CLAWS (cite: denBrok2022) and ALMOND (cite: Neumann2023a). First, we homogenise the data by convolving the CO data to the HCN resolution (using `convolution.convolve` from `astropy`). Then, we adopt a hexagonal spaxel grid with a beam-size spaxel separation and sample all data to the same spaxel grid and spectral axis. This means that every hexagonal pixel is an independent line-of-sight (LOS) measurement. Then, we create velocity masks based on the CO on a pixel-by-pixel basis to select the velocity range where we also expect to find HCN emission. This is done by building a $4\sigma$ mask that is expanded into channels above $2\sigma$ in order to recover broader emission belonging to a $4\sigma$ core (cite: Neumann2023a). By applying the CO-based mask to our data, we compute the integrated intensity of CO ($W_{\rm CO}$) and HCN ($W_{\rm HCN}$) by integrating the line’s brightness temperatures ($T_{\rm line}$, where ${\rm line}=\{\mathrm{CO}, \mathrm{HCN}\}$) over the velocity range selected by the mask: $$\begin{align}
    \left(\dfrac{W_{\rm line}}{\SI{}{\Kkms}}\right) = \sum_{n=1}^{N_{\rm mask}} \left(\dfrac{T_{\rm line, n}}{\SI{}{\kelvin}}\right) \times \left(\dfrac{\Delta v_\text{channel}}{\SI{}{\kilo\metre\per\second}}\right) \;.
\end{align}$$ The uncertainties of the integrated intensities ($\sigma_{W_{\rm line}}$) are then given by: $$\begin{align}
    \left(\dfrac{\sigma_{W_{\rm line}}}{\SI{}{\Kkms}}\right) = \left(\dfrac{\sigma_{T_{\rm line}}}{\SI{}{\kelvin}}\right) \times \left(\dfrac{\Delta v_\mathrm{channel}}{\SI{}{\kilo\metre\per\second}}\right) \times \sqrt{N_{\rm mask}} \;,
    \label{equ:emom0}
\end{align}$$ where $\sigma_{T_{\rm line}}$ is the standard deviation in the emission-free channels (i.e. channels not selected by the mask), $\Delta v_\mathrm{channel}$ is the channel width of 5 km s^−1^ and $N_{\rm mask}$ is the number of channels selected by the mask for each LOS.

We note that we also homogenise the two-dimensional maps, e.g. the MUSE $\text{H}\alpha$ and JWST 21 $\mu$ m maps, with the produced moment-0 maps. This means, we convolve the maps to the 260 HCN resolution and reproject them onto the same beam-size hexagonal pixel grid. A summary of the data products is presented in Fig. [16](#fig:data_products_maps). We describe the derivation of the physical quantities in the following subsections.

## Molecular gas surface density – CO

We use $\text{CO(2--1)}$(hereafter CO) line observations from PHANGS–ALMA (cite: Leroy2021b) to trace the bulk molecular gas.

For $\mathrm{NGC\,4321}$, the CO data are at 1.67″ resolution, which corresponds to 120 physical scale at the distance of the galaxy.

[^3] We infer the molecular gas surface density ($\Sigma_{\text{mol}}$) from the $\text{CO(2--1)}$ line intensity ($W_{\text{CO(2--1)}}$) using the $\text{CO(2--1)}$-to-$\text{CO(1--0)}$ line ratio ($R_{21}$) and the CO-to-$\text{H}_2$ conversion factor ($\alpha_{\text{CO}}$), which includes the mass contribution from helium: $$\begin{equation}
    \ensuremath{\Sigma_{\text{mol}}}= \ensuremath{\alpha_{\text{CO}}}\, R_{21}^{-1} \, \ensuremath{W_{\text{CO(2--1)}}}\cos(i).
\end{equation}$$ $\cos(i)$ corrects for the inclination $i=\ang{38.5}$ of the galaxy. Throughout this work, we adopt two methods (see Appendix [7.1](#sec:appendix:aco) for more details): 1) using constant $\alpha_{\text{CO}}$ and $R_{21}$ conversion factors (Sect. [7.1.1](#sec:methods:sigmol_const_aco)) which enter the estimation of the dense gas fraction as traced by the HCN-to-CO line ratio (Sect. [3.3](#sec:methods:fdense)). We use a constant $\alpha_{\text{CO}}$ for the HCN-to-CO line ratio due to the poor knowledge about variations of the HCN-to-dense gas conversion factor thus keeping $f_{\text{dense}}$ proportional to HCN/CO. 2) using spatially varying $\alpha_{\text{CO}}$ and $R_{21}$ (Sect. [7.1.1](#sec:methods:sigmol_const_aco)) for computing $\Sigma_{\text{mol}}$ and the dynamical equilibrium pressure (Sect [3.6](#sec:methods:pde)).

## Dense gas fraction – HCN/CO

In this study, we present new HCN observations (Sect. [2.2](#sec:data:hcn)) and use the HCN line intensity ($W_{\text{HCN}}$) as a proxy for the amount of dense gas. For the main part of this work, we focus on studying the observational HCN-to-CO line ratio, i.e. $W_{\text{HCN}}$/$W_{\text{CO(2--1)}}$(hereafter HCN/$\text{CO(2--1)}$ or simply HCN/CO) as a density-sensitive line ratio. (cite: Gallagher2018b) and (cite: Neumann2023a) have shown that HCN/CO is indeed tracing the $\sim\SI{100}{\parsec}$-scale mean gas density and it has been reported to scale with the gas surface density within Galactic clouds (cite: Tafalla2023) as expected by molecular line modelling (cite: Leroy2017a).

In addition, the reported linear relation between the HCN/CO and $\text{N}_2\text{H}^+$/CO line ratios across Galactic and extragalactic studies underlines the credibility of HCN/CO as a proxy for the dense gas fraction (cite: Jimenez-Donaire2023; Stuber2023). Throughout the discussion (Sect. [5](#sec:discussion)), we comment on the implications of the dense gas fraction ($f_{\text{dense}}$) as a physical quantity proportional to HCN/CO with some uncertainties linked to abundance, temperature and opacity.

Following many previous works (cite: Usero2015; Bigiel2016; Gallagher2018a; Gallagher2018b; Jimenez-Donaire2019; Bemis2019; Neumann2023a), the dense gas fraction is defined as the ratio of the dense gas to bulk molecular gas surface density ($\ensuremath{f_{\text{dense}}}=\ensuremath{\Sigma_{\text{dense}}}/\ensuremath{\Sigma_{\text{mol}}}$): $$\begin{align}
    \ensuremath{f_{\text{dense}}}= \dfrac{\ensuremath{\Sigma_{\text{dense}}}}{\ensuremath{\Sigma_{\text{mol}}}} = \dfrac{\ensuremath{\alpha_{\text{HCN}}}\ensuremath{W_{\text{HCN}}}}{\ensuremath{\alpha_{\text{CO}}} R_\text{21}^{-1}\ensuremath{W_{\text{CO(2--1)}}}} \approx 2.1\dfrac{\ensuremath{W_{\text{HCN}}}}{\ensuremath{W_{\text{CO(2--1)}}}}  \, .
\end{align}$$ The above conversion adopts constant mass-to-light ratios $\ensuremath{\alpha_{\text{CO}}}=\SI{4.35}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$ (cite: Bolatto2013) and $\ensuremath{\alpha_{\text{HCN}}}=\SI{14}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$ (cite: Onus2018) for CO and HCN, respectively, and a fiducial $\text{CO(2--1)}$-to-$\text{CO(1--0)}$ line ratio of $R_{21}=0.65$ (cite: denBrok2022; Leroy2022). Here, we use the above conversion to infer $f_{\text{dense}}$ as an alternative axis in the HCN/CO relations.

The adopted constant HCN-to-dense gas mass conversion factor is expected to trace gas above $n_{{\rm H}_2}\approx\SI{5e3}{\per\cubic\centi\metre}$ (cite: Onus2018)[^4]. In contrast to $\alpha_{\text{CO}}$, systematic variations of $\alpha_{\text{HCN}}$ are poorly understood and estimated values range from 0.3 to $\SI{300}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$, spanning three orders of magnitude (cite: Garcia-Burillo2012; Kauffmann2017; Nguyen-Luong2017; Shimajiri2017; Evans2020; Barnes2020; Tafalla2023), where extragalactic studies, capturing larger physical areas and thus more diffuse emission typically yield values around $\SIrange{10}{20}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$.

The $\alpha_{\text{HCN}}$ conversion factor might vary similarly to $\alpha_{\text{CO}}$ due to its dependence on optical depth, which is a key driver of $\alpha_{\text{CO}}$ variations (cite: Teng2023), though HCN and CO optical depth variations are not expected to be identical. In that case, we could even induce systematic trends by adopting a more accurate, spatially varying $\alpha_{\text{CO}}$, but keeping $\alpha_{\text{HCN}}$ constant. Therefore, the best current approach is to study the observational HCN/CO line ratio.

As laid out in this section, we adopt the classical view of utilising HCN/CO as a proxy of $f_{\text{dense}}$. However, we want to point out that the conversion factors are subject to large uncertainties (especially $\alpha_{\text{HCN}}$) such that our $f_{\text{dense}}$ estimates are expected to be uncertain by a factor of a few. Therefore, recent works (cite: Gallagher2018a; Gallagher2018b; Jimenez-Donaire2019; Neumann2023a; Tafalla2023), which study HCN/CO as a function of the molecular gas surface density suggest to interpret HCN/CO as a predictor of the cloud-scale ($\sim\SI{100}{\parsec}$) average gas density based on the robust relation between HCN/CO and $\Sigma_{\text{mol}}$(see also Sect. [4.5](#sec:discussion:hcn_co)). This means, HCN/CO is expected to track $\langle\Sigma_{\text{mol}}\rangle$ more robustly than $f_{\text{dense}}$. We note, that in turbulent cloud models (cite: Krumholz2005), an increase of HCN/CO would indicate an increase in $f_{\text{dense}}$ as well as $\langle\Sigma_{\text{mol}}\rangle$. Therefore, both interpretation, i.e. HCN/CO traces $f_{\text{dense}}$ and HCN/CO traces $\langle\Sigma_{\text{mol}}\rangle$, are reasonable. Throughout this work, we base our results on the observable HCN/CO line ratio, and provide a secondary $f_{\text{dense}}$-axis in Figures [6](#fig:hcn_ratios_vs_radius_and_pressure) to [\[equ:hcn_co_vs_sigmol\]](#equ:hcn_co_vs_sigmol), so that, taking into considering aforementioned caveats, HCN/CO can be interpreted as the dense gas fraction via a proportional conversion or alternatively as an indicator of the mean gas density.

## Star formation rate (SFR) – $\text{H}\alpha$

We use $\text{H}\alpha$ recombination line emission taken by the Multi Unit Spectroscopic Explorer (MUSE) of the Very Large Telescope (VLT) as part of the PHANGS–MUSE survey (cite: Emsellem2022) to trace the star formation rate. In Appendix [9](#sec:appendix:sfr_tracers), we discuss using alternative SFR tracers including 21 $\mu$ m (F2100W) hot dust emission from JWST (cite: Lee2023) and 33 GHz free-free emission from the VLA (cite: Linden2020), which can differ significantly (up to one order of magnitude) in the central few kiloparsecs of galaxies. Here, we find that SFR values inferred from the 33 GHz emission confirm the extinction-corrected $\text{H}\alpha$ inferred values in the centre of $\mathrm{NGC\,4321}$. Moreover, 21 $\mu$ m emission also yields similar SFR values (within 0.2) when adopting a linear conversion (for more details see App. [9.3](#sec:appendix:sfr_comparison)). Therefore, throughout this work we adopt $\text{H}\alpha$ emission as a robust tracer of SFR validated by free-free data in the centre.

We use Balmer decrement-corrected $\text{H}\alpha$ maps to measure the star formation rate surface density ($\Sigma_{\text{SFR}}$). Those rely on the extinction curve from (cite: O’Donnell1994) as described in (cite: Pessa2022) and (cite: Belfiore2023). The attenuation corrected $\text{H}\alpha$ flux ($L_{\ensuremath{\text{H}\alpha},\mathrm{corr}}$) is converted into SFR via $\mathrm{SFR}/(\SI{}{\Msun\per\year})=C_{\ensuremath{\text{H}\alpha}}\times L_{\ensuremath{\text{H}\alpha},\mathrm{corr}}/(\SI{}{\erg\per\second})$ using the conversion factor $C_{\ensuremath{\text{H}\alpha}}=\num{5.3e-42}$ from (cite: Calzetti2007). This conversion assumes a constant star formation history, age of 100  , solar metallicity, and a (cite: Kroupa2001) initial mass function (IMF) (cite: Belfiore2023). In surface density units the above formalism translates to:

$$\begin{equation}
    \left(\dfrac{\Sigma_{\rm SFR, \ensuremath{\text{H}\alpha}}}{\SI{}{\Msun\per\year\per\square\kilo\parsec}}\right) = \num{6.3e2} \left( \dfrac{I_{\ensuremath{\text{H}\alpha}, \rm corr}}{\SI{}{\erg\per\second\per\square\centi\metre\per\steradian}} \right) \cos(i) \;.
    \label{equ:sfr_halpha}
\end{equation}$$

## Dense gas star formation efficiency – SFR/HCN

We take the ratio of the star formation rate surface density ($\Sigma_{\text{SFR}}$) to the HCN line intensity ($W_{\text{HCN}}$), i.e. $\Sigma_{\text{SFR}}$/$W_{\text{HCN}}$(hereafter SFR/HCN) as a proxy of the star formation efficiency of the dense gas ($\text{SFE}_{\text{dense}}$). Similar to HCN/CO tracing $f_{\text{dense}}$, we also focus on the more observationally based SFR/HCN in our analysis and discuss implications on the inferred $\text{SFE}_{\text{dense}}$ connected to uncertainties in the conversion factor ($\alpha_{\text{HCN}}$). $\text{SFE}_{\text{dense}}$ is defined as the ratio of SFR surface density to dense gas mass surface density ($\ensuremath{\text{SFE}_{\text{dense}}}=\ensuremath{\Sigma_{\text{SFR}}}/\ensuremath{\Sigma_{\text{dense}}}$) as in previous works (listed in Sect. [3.3](#sec:methods:fdense)): $$\begin{align}
    \ensuremath{\text{SFE}_{\text{dense}}}= \dfrac{\ensuremath{\Sigma_{\text{SFR}}}}{\ensuremath{\Sigma_{\text{dense}}}} = \ensuremath{\alpha_{\text{HCN}}}^{-1}\,\dfrac{\ensuremath{\Sigma_{\text{SFR}}}}{\ensuremath{W_{\text{HCN}}}} \, .
    \label{EQU:sfedense}
\end{align}$$ The above equation yields $$\begin{align}
    \left(\dfrac{\ensuremath{\text{SFE}_{\text{dense}}}}{\SI{}{\per\mega\year}}\right) = 0.071 \left(\dfrac{\ensuremath{\Sigma_{\text{SFR}}}}{\SI{}{\Msun\per\year\per\square\kilo\parsec}}\right) \left(\dfrac{\ensuremath{W_{\text{HCN}}}}{\SI{}{\Kkms}}\right)^{-1} \, .
\end{align}$$ when using the same, constant HCN-to-dense gas mass conversion ($\ensuremath{\alpha_{\text{HCN}}}=\SI{14}{\Msun\per\square\parsec}(\SI{}{\Kkms})^{-1}$, (cite: Onus2018)) as for $f_{\text{dense}}$(Sect. [3.3](#sec:methods:fdense)).

![](Figures/ngc4321_maps_hcn_ratios_compressed.pdf)

## Dynamical equilibrium pressure

We compute the dynamical equilibrium pressure, or ISM pressure ($P_{\text{DE}}$) at 260 scale following the prescription by (cite: Sun2020a). In this prescription the dynamical equilibrium pressure is composed of a pressure term created by the ISM due to the self-gravity of the ISM disc and a term due to the gravity of the stars (see e.g. (cite: Spitzer1942)), such that: $$\begin{align}
    \ensuremath{P_{\text{DE}}}= \dfrac{\pi G}{2} \ensuremath{\Sigma_{\text{gas}}}^2 + \ensuremath{\Sigma_{\text{gas}}}\sqrt{2G\ensuremath{\rho_{\star}}}\, \sigma_{\text{gas,z}} \; ,
    \label{equ:PDE_large}
\end{align}$$ where we assume a smooth, single-fluid gas disc, and that all gas shares a similar velocity dispersion, so that $\ensuremath{\Sigma_{\text{gas}}}=\ensuremath{\Sigma_{\text{mol}}}+\ensuremath{\Sigma_{\text{atom}}}$ is the total gas surface density, composing of a molecular ($\Sigma_{\text{mol}}$) and an atomic ($\Sigma_{\text{atom}}$) gas component.

$\rho_{\star}$ is the stellar mass volume density (App. [7.3](#sec:appendix:mstar)) near the disc mid-plane and $\sigma_{\text{gas,z}}$ is the velocity dispersion of the gas perpendicular to the disc.

In many previous extragalactic studies (cite: Spitzer1942; Elmegreen1989; Elmegreen1994; Wong2002; Blitz2004; Blitz2006; Leroy2008; Koyama2009; Ostriker2010; Ostriker2011; Kim2011; Shetty2012; Kim2013; Kim2015; Benincasa2016; Herrera-Camu2017; Gallagher2018b; Fisher2019; Schruba2019; Jimenez-Donaire2019) $P_{\text{DE}}$ was typically estimated using Equ. [\[equ:PDE_large\]](#equ:PDE_large) with homogenised $\Sigma_{\text{gas}}$, $\rho_{\star}$, $\sigma_{\text{gas,z}}$ at kpc scales. Recently, (cite: Sun2020a) came up with a new formalism which makes use of the high resolution $\sim\SI{100}{\parsec}$ scale $\text{CO(2--1)}$ data from PHANGS–ALMA. Most importantly, it takes into account the self-gravity of the (molecular) gas at high resolution.

In this study we adopt their formalism and combine the 120 scale molecular gas term ($\langle P_{\text{cloud}}\rangle$; converted to the lower resolution via a $\Sigma_{\text{mol}}$-weighted average) with the 260 scale atomic gas term ($P_{\text{atom}}$): $$\begin{align}
    \ensuremath{\langle P_{\text{DE}}\rangle}= \ensuremath{\langle P_{\text{cloud}}\rangle}+ \ensuremath{P_{\text{atom}}}.
    \label{equ:PDE_avg}
\end{align}$$ $\langle P_{\text{cloud}}\rangle$ consists of three terms accounting for the self-gravity of the molecular gas, the gravity of larger molecular structures and the gravity of stars. $P_{\text{atom}}$ includes the self-gravity of the atomic gas and the gravitational interaction of the atomic gas with the 260 scale molecular gas and the stars (see App. [7.4](#sec:appendix:pde) for more details).

## Morphological environmental masks

We adopt the environmental masks presented in (cite: Querejeta2021), which identify morphological environmental regions based on the appearance of the stellar mass content traced by the *Spitzer* 3.6 μm emission from S$^4$G (cite: Sheth2010). We use the “simple” mask, where each pixel is uniquely assigned to a dominant environment. We define the bar ends as the overlap of the spiral arms with the bar footprint. For simplicity, we combine interbar, interarm into one region, referred to as interarm. We end up with five environments – centre, bar, bar ends, spiral arms, interam, which are re-sampled onto the same hexagonal grid as the other data defined by the HCN map (Sect. [3.1](#sec:methods:mom0_maps)). We show the adopted environments in the right panel of Fig. [3](#fig:hcn_ratio_maps).

## Stacking and linear regression

To study the average trends, we stack the data (HCN, CO, SFR) in equally spaced bins in linear scale ($r_{\rm gal}$) or logarithmic scale ($P_{\text{DE}}$). The spectral stacking is done using the `python` package `PyStacker`[^5], which yields average CO and HCN spectra in each respective bin (the stacked spectra are presented in Fig. [4](#fig:stacks_envir) and in App. [8](#sec:appendix:stacking)). Those average spectra are used to compute the average integrated intensities in each bin. For SFR, we simply compute the mean of the SFR values in the respective bin. The bin ratios are then computed as the ratios of the stacked measurements. To first order, HCN and CO lines show similar kinematics across most of the galaxy, so the line ratio, which we discuss in this first paper, encodes most of the relevant information.

We fit the stacked data in order to probe the underlying global relation without “population” biases and to not be dominated by non-detections in constraining the best-fit line. We note, however, that we have also fitted the individual sight-line measurements using `LinMix`[^6] resulting in similar fit relations in agreement within 1-sigma uncertainties with the fits reported here for the binned data. We use these sight-line fits to quantify the uncertainty of the regression slopes since the MARS fitting routine (see below) does not yield uncertainties.

We then apply a ‘multivariate adaptive regression spline’ (MARS; (cite: Friedman1991)) model to the binned data in order to find the best piece-wise linear regression function that describes the data (see Sect. [4.2](#sec:results:radius) and [4.3](#sec:results:pressure)). MARS is a generalisation of a recursive partitioning algorithm, which iteratively splits the data into separate $x$-axis regimes and optimises the split point with respect to the the piece-wise linear regression in each regime via minimising the $\chi^2$ value of the data to the model. The algorithm is adapted to only add another split point if a further component significantly improves the fit, meaning that the $\chi^2$ value is improved by more than 0.01. In this way, we employ a statistically robust and objective method to find the threshold at which the trends change significantly thus identifying physically different regimes in the relations. To perform the MARS model we utilise the `R`-package `earth`[^7]. Here, we force the model to only consist of up to two linear functions, i.e. it can either find one or two regimes depending on if a second regime improves the fit significantly.

![](Figures/ngc4321_stacked_spectra_environments_compressed.pdf)

+:-----------:+:-----------------:+:-----------------:+:------------------:+:------------------:+:------------------:+:------------------:+
| Environment | $W_{\rm CO(2-1)}$ | $L_{\rm CO(2-1)}$ | $f_{\rm CO(2-1)}$  | $W_{\rm HCN(1-0)}$ | $L_{\rm HCN(1-0)}$ | $f_{\rm HCN(1-0)}$ |
|             +-------------------+-------------------+                    +--------------------+--------------------+                    |
|             | \[ mK km s^−1^\]  | \[  \]            |                    | \[ mK km s^−1^\]   | \[  \]             |                    |
+-------------+-------------------+-------------------+--------------------+--------------------+--------------------+--------------------+
| full galaxy | 3861 $\pm$ 10     | 822.2 $\pm$ 2.1   | 1471/3489 (42.2 %) | 168 $\pm$ 4        | 35.8 $\pm$ 0.8     | 275/3489 (7.9 %)   |
+-------------+-------------------+-------------------+--------------------+--------------------+--------------------+--------------------+
| centre      | 82790 $\pm$ 76    | 217.3 $\pm$ 0.2   | 42/43 (97.7 %)     | 7462 $\pm$ 36      | 19.6 $\pm$ 0.1     | 42/43 (97.7 %)     |
+-------------+-------------------+-------------------+--------------------+--------------------+--------------------+--------------------+
| bar         | 8233 $\pm$ 35     | 147.2 $\pm$ 0.6   | 227/293 (77.5 %)   | 303 $\pm$ 8        | 5.4 $\pm$ 0.1      | 70/293 (23.9 %)    |
+-------------+-------------------+-------------------+--------------------+--------------------+--------------------+--------------------+
| bar ends    | 10875 $\pm$ 56    | 33.9 $\pm$ 0.2    | 50/51 (98.0 %)     | 464 $\pm$ 15       | 1.4 $\pm$ 0.0      | 26/51 (51.0 %)     |
+-------------+-------------------+-------------------+--------------------+--------------------+--------------------+--------------------+
| spiral arms | 4577 $\pm$ 13     | 264.8 $\pm$ 0.8   | 594/948 (62.7 %)   | 129 $\pm$ 6        | 7.5 $\pm$ 0.4      | 97/948 (10.2 %)    |
+-------------+-------------------+-------------------+--------------------+--------------------+--------------------+--------------------+
| interarm    | 1178 $\pm$ 11     | 154.9 $\pm$ 1.4   | 558/2154 (25.9 %)  | 18 $\pm$ 4         | 2.4 $\pm$ 0.5      | 40/2154 (1.9 %)    |
+-------------+-------------------+-------------------+--------------------+--------------------+--------------------+--------------------+

**Notes:** Columns 2 and 5 list the stacked integrated intensities of $\text{CO(2--1)}$ and $\text{HCN(1--0)}$ for the full galaxy (first row) and respective morphological environments. The stacked spectra are shown in Fig. [4](#fig:stacks_envir). The corresponding $\text{CO(2--1)}$ and $\text{HCN(1--0)}$ line luminosities are shown in columns 3 and 6. Columns 4 and 7 present the detection fractions of $\text{CO(2--1)}$ and $\text{HCN(1--0)}$, respectively, by environment. Shown are the number of detected ($\rm{S/N}\geq 3$) independent sight lines w.r.t. the total number of sight lines in the respective region and the corresponding detection fraction in percent in brackets.

![](Figures/ngc4321_hcn_ratios_violins_compressed.pdf)

# Results

## Dense gas spectroscopic ratios across the full disc of NGC 4321 at 260 pc scale

The new high-resolution, deep, wide-field HCN observations presented in this work, allow us for the first time to study variations of HCN/CO, a proxy of $f_{\text{dense}}$, and SFR/HCN, a proxy of $\text{SFE}_{\text{dense}}$, across the full disc of a Milky Way-like galaxy at unprecedented resolution (260) such that morphological environments can be well separated. These data represent one of the rare deep, wide-field HCN maps of a nearby galaxy which allows analysis of 275 detected sight lines even outside of the galaxy centre as illustrated by Fig. [2](#fig:maps_observations) (top left panel). By environment, we detect 42 HCN sight lines in the centre, 70 in the bar, 26 in the bar ends, 97 in the spiral arms, and 40 in the interarm regions (we list the values along with stacked integrated intensities and luminosities in Tab. [\[tab:stacking_values\]](#tab:stacking_values)). Figure [2](#fig:maps_observations) shows that where CO is detected, HCN is also often detected, though HCN is found to be more concentrated in the centre, bar, bar ends and spiral arms. To first order, $\text{H}\alpha$ and 21 $\mu$ m emission, tracers of SFR, are spatially correlated with both CO and HCN. The 260 scale, resolved observations of $\mathrm{NGC\,4321}$ confirm the well-established linear correlation between HCN luminosity and SFR.

In Figure [3](#fig:hcn_ratio_maps), we show maps of HCN/CO and SFR/HCN. The variability of these ratios provides information about how HCN correlates with CO and SFR, as discussed below.

In the following, we distinguish between five environmental regions (centre, bar, bar ends, spiral arms, interarm) introduced in Sect. [3.7](#sec:methods:environments). The right panel of Figure [3](#fig:hcn_ratio_maps) shows the applied environments sampled onto the same coordinate grid and overlaid with HCN contours. Overall, the HCN emission follows the stellar mass morphology such that outside of the centre, most of the HCN emission is associated with the stellar spiral arms, whereas less HCN is found in the interarm regions. However, there is also large amounts of (dense) molecular gas when following the bar eastward beyond the bar ends. These regions, here depicted as interarm regions, could be interpreted as minor spiral arms or spurs between the spiral arms that harbour large amounts of molecular gas (similar to the spurs observed in M51; (cite: Schinnerer2017)). Though not explored here and considered part of the interarm environment, it could be interesting to study these spurs in more detail in further studies.

### HCN/CO variations

Figure [5](#fig:hcn_ratios_violins) (left panel) shows the distribution of HCN/CO values in different environments, stacked in increments of 0.1. We also show the mean and scatter of the detected data of the respective distributions. Since S/N clipping systematically selects luminous HCN regions, these values will be biased towards high HCN/CO and low SFR/HCN, with the significance of the bias depending on the completeness of detections in the respective environments. Therefore, we also show the stacked means of all sight lines across each environment (squares in Fig. [5](#fig:hcn_ratios_violins)). The values are listed in Tab. [2](#tab:histogram_statistics).

We find that HCN/CO spans roughly 0.6 when considering only detected lines of sight ($\mathrm{S/N}\geq 3$). In agreement with previous studies (cite: Usero2015; Bigiel2016; Gallagher2018a; Jimenez-Donaire2019; Querejeta2019; Neumann2023a), HCN/CO increases towards the centre of the galaxy, where it reaches values around $0.1$ (mean of $0.089\pm 0.0003$), indicating an increase of the dense gas fraction, or average gas density in centres of galaxy or/and a change in excitation conditions, e.g. optical depth, gas temperature, or abundance (cite: Jimenez-Donaire2017; Eibensteiner2022).

Throughout the disc of the galaxy (spiral arms and interarm region), HCN/CO is lower by a factors of two (mean of $\leq 0.049$ across detections, with 1-sigma scatter of $\pm \SI{0.15}{\dex}$) compared to the centre (mean of $0.89$) and does not show trends with radius or environment (further discussed in Sect. [4.2](#sec:results:radius)). This suggests, assuming that HCN/CO is a robust tracer of density (cite: Neumann2023a), that the density distribution of the molecular gas, which is detected in HCN, is very similar across the disc of $\mathrm{NGC\,4321}$. However, we note that when taking into account censored data, the average HCN/CO is lower by almost a factor of two in the interarm region (mean of $0.015\pm 0.003$) than in the spiral arms (mean of $0.028\pm 0.001$).

Compared to the disc of the galaxy and taking into account non-detections, we observe enhanced HCN/CO in the bar ends (mean of $0.043\pm 0.001$) pointing towards the piling up of dense molecular gas, e.g. via gas streams from the spiral arms and the bar towards the bar ends (predicted by simulations, e.g. (cite: Renaud2015) and observed in NGC 3627 (cite: Beslic2021)). Moreover, we observe indications of a mild gradient of HCN/CO with angular offset from the spiral arm across the southern spiral arm (Fig. [3](#fig:hcn_ratio_maps)). If taken at face value, the found HCN/CO gradient could imply a systematic density variation across the spiral arm, changing the physical conditions of the emitting gas.

+:-----------------------------------------------:+:-----------:+:------------------------------------:+:--------------------:+:----------------:+
| Ratio                                           | Environment | (16$^{\rm th}$, 84$^{\rm th}$) perc. | mean                 | stacks           |
|                                                 |             +--------------------------------------+----------------------+------------------+
|                                                 |             | $\mathrm{S/N}\geq 3$                 | $\mathrm{S/N}\geq 3$ | all S/N          |
+-------------------------------------------------+-------------+--------------------------------------+----------------------+------------------+
| $\dfrac{\rm HCN}{\ensuremath{\text{CO(2--1)}}}$ | full galaxy | (0.035, 0.076)                       | 0.067                | $0.043\pm 0.001$ |
|                                                 +-------------+--------------------------------------+----------------------+------------------+
|                                                 | centre      | (0.060, 0.104)                       | 0.089                | $0.090\pm 0.001$ |
|                                                 +-------------+--------------------------------------+----------------------+------------------+
|                                                 | bar         | (0.037, 0.065)                       | 0.049                | $0.037\pm 0.001$ |
|                                                 +-------------+--------------------------------------+----------------------+------------------+
|                                                 | bar ends    | (0.036, 0.058)                       | 0.046                | $0.043\pm 0.001$ |
|                                                 +-------------+--------------------------------------+----------------------+------------------+
|                                                 | spiral arms | (0.031, 0.057)                       | 0.041                | $0.028\pm 0.001$ |
|                                                 +-------------+--------------------------------------+----------------------+------------------+
|                                                 | interarm    | (0.037, 0.074)                       | 0.049                | $0.015\pm 0.003$ |
+-------------------------------------------------+-------------+--------------------------------------+----------------------+------------------+
| $\dfrac{\rm{SFR}_{\mathrm{H}\alpha}}{\rm{HCN}}$ | full galaxy | (0.019, 0.122)                       | 0.040                | $0.069\pm 0.002$ |
|                                                 +-------------+--------------------------------------+----------------------+------------------+
|                                                 | centre      | (0.016, 0.049)                       | 0.025                | $0.025\pm 0.001$ |
|                                                 +-------------+--------------------------------------+----------------------+------------------+
|                                                 | bar         | (0.007, 0.049)                       | 0.028                | $0.039\pm 0.001$ |
|                                                 +-------------+--------------------------------------+----------------------+------------------+
|                                                 | bar ends    | (0.040, 0.124)                       | 0.083                | $0.086\pm 0.003$ |
|                                                 +-------------+--------------------------------------+----------------------+------------------+
|                                                 | spiral arms | (0.055, 0.146)                       | 0.112                | $0.125\pm 0.006$ |
|                                                 +-------------+--------------------------------------+----------------------+------------------+
|                                                 | interarm    | (0.036, 0.131)                       | 0.084                | $0.274\pm 0.057$ |
+-------------------------------------------------+-------------+--------------------------------------+----------------------+------------------+

: HCN/CO and SFR/HCN statistics by environment.

**Notes:** Statistics of spectroscopic ratios across the different environments (right panel of Fig. [3](#fig:hcn_ratio_maps)) corresponding to the distributions shown in Fig. [5](#fig:hcn_ratios_violins). The third column shows the 16th and 84th percentiles of the detected measurements ($\mathrm{S/N}\geq 3$). The fourth column lists the mean of the detected data, which is computed as the sum of the numerator data over the sum of the denominator data of the spectroscopic ratio. The fifth column shows the stacks mean over all S/N along with measurement uncertainties (in dex) in the respective environment. The measurement uncertainties are computed from the rms of the emission-free channels of the stacks (Equ. [\[equ:emom0\]](#equ:emom0)) and do not include any calibration or systematic uncertainties.

![](Figures/ngc4321_HCN_ratios_vs_radius_and_pressure_ACO_B13_MUSEGPR_compressed_v3.pdf)

+--------------------------------+-----------------------------------------+----------------------------------------------------+----------------+--------------+---------------+---------+
| x-axis                         | y-axis                                  | Regime                                             | Slope (stacks) | Slope (los)  | Corr. ($p$)   | Scatter |
+:==============================:+:=======================================:+:==================================================:+:==============:+:============:+:=============:+:=======:+
| $r_{\rm gal}$                  | HCN/CO($2-1$)                           | $\leq\SI{2.0}{\kilo\parsec}$                       | -0.38          | -0.26 (0.02) | -0.86 (0.0)   | 0.14    |
|                                |                                         +----------------------------------------------------+----------------+--------------+---------------+---------+
|                                |                                         | $>\SI{2.0}{\kilo\parsec}$                          | 0.00           | 0.00 (0.01)  | -0.03 (0.306) | 0.23    |
|                                +-----------------------------------------+----------------------------------------------------+----------------+--------------+---------------+---------+
|                                | SFR$_{\ensuremath{\text{H}\alpha}}$/HCN | $\leq\SI{2.8}{\kilo\parsec}$                       | 0.34           | 0.22 (0.06)  | 0.32 (0.0)    | 0.41    |
|                                |                                         +----------------------------------------------------+----------------+--------------+---------------+---------+
|                                |                                         | $>\SI{2.8}{\kilo\parsec}$                          | 0.08           | 0.08 (0.01)  | 0.41 (0.0)    | 0.38    |
+--------------------------------+-----------------------------------------+----------------------------------------------------+----------------+--------------+---------------+---------+
| $\langle P_{\text{DE}}\rangle$ | HCN/CO($2-1$)                           | $\leq\SI{4.0e5}{\kB\kelvin\per\cubic\centi\metre}$ | 0.18           | 0.23 (0.02)  | 0.47 (0.0)    | 0.24    |
|                                |                                         +----------------------------------------------------+----------------+--------------+---------------+---------+
|                                |                                         | $>\SI{4.0e5}{\kB\kelvin\per\cubic\centi\metre}$    | 0.42           | 0.40 (0.03)  | 0.64 (0.0)    | 0.16    |
|                                +-----------------------------------------+----------------------------------------------------+----------------+--------------+---------------+---------+
|                                | SFR$_{\ensuremath{\text{H}\alpha}}$/HCN | $\leq\SI{1.6e6}{\kB\kelvin\per\cubic\centi\metre}$ | -0.32          | -0.53 (0.04) | -0.47 (0.0)   | 0.54    |
|                                |                                         +----------------------------------------------------+----------------+--------------+---------------+---------+
|                                |                                         | $>\SI{1.6e6}{\kB\kelvin\per\cubic\centi\metre}$    | -0.89          | -0.70 (0.22) | -0.39 (0.003) | 0.39    |
+--------------------------------+-----------------------------------------+----------------------------------------------------+----------------+--------------+---------------+---------+

**Notes** – Linear regression parameters for the respective relations and $x$-axis regimes presented in Fig. [6](#fig:hcn_ratios_vs_radius_and_pressure). The forth column is showing the slopes obtained from the multivariate adaptive regression spline (`MARS`) method, producing a continuous piece-wise linear regression. Columns five to seven show the linear regression parameters obtained from the individual sight-line measurements, taking into account all data in the respective regime, using the linear regression tool `LinMix`. ‘Corr.’ is the Pearson correlation coefficient of sight-line data and ‘$p$’ is the associated $p$-value. The scatter denotes the $3\sigma$ standard deviation of the detected sight-line data about the fit line. The cloud-scale pressure thresholds correspond to 260-scale beam-matched values of $\ensuremath{P_{\text{DE}}}\approx\SI{1.5e5}{\kB\kelvin\per\cubic\centi\metre}$ and $\ensuremath{P_{\text{DE}}}=\SI{6.3e5}{\kB\kelvin\per\cubic\centi\metre}$, respectively.

### SFR/HCN variations

Analogously to HCN/CO, we show violin plots along with mean scatter bars of SFR/HCN, a proxy of $\text{SFE}_{\text{dense}}$, in the right panel of Figure [5](#fig:hcn_ratios_violins). In total, the SFR/HCN values span about 2 across the detected LOSs indicating a large scatter in SFR/HCN, consistent with the cloud-to-cloud variation found in Galactic studies (cite: Moore2012; Eden2012; Csengeri2016; Urquhart2021). Certainly, some of the scatter can be attributed to systematic variations with molecular gas conditions (cite: Neumann2023a) and environment (discussed in this work).

In the inner $\sim \SI{4}{\kilo\parsec}$ of $\mathrm{NGC\,4321}$, SFR/HCN appears to be spatially anti-correlated with HCN/CO (Fig. [3](#fig:hcn_ratio_maps)), confirming kpc-scale measurements of previous studies, e.g. (cite: Usero2015; Gallagher2018a; Jimenez-Donaire2019). As has been reported in several previous studies (cite: Chen2015; Beslic2021; Neumann2023a), SFR/HCN decreases towards the centre of the galaxy (mean of $0.025\pm 0.0001$ in units of $(\SI{}{\Msun\per\year\per\square\kilo\parsec})/(\SI{}{\Kkms})$) supporting the picture that HCN traces more of the bulk material in dense environments. In addition to the centre, we find SFR/HCN to be particularly low in the bar of the galaxy (mean of $0.039\pm 0.001$) (further discussed in Sect. [5.3](#sec:discussion:bar)), while it is higher by a factor of two to seven across the disc (i.e. bar ends, spiral arms and interarm regions, have means between $0.086\pm 0.003$ and $0.274\pm 0.057$).

The low SFR/HCN in the centre and bar environments can be explained in several ways. On the one hand, the low SFR/HCN can be caused by an increase in HCN emissivity. On the other hand, it could indicate a decrease in SFR at fixed HCN emission, i.e. an actually reduced star formation efficiency of dense gas. Another alternative explanation put forward in previous works (cite: Gallagher2018a; Jimenez-Donaire2019; Neumann2023a) is that, in these high-density, high-pressure environments, HCN is not tracing the actual overdensities anymore, but become more of a bulk molecular gas tracer. The former can be caused by radiative trapping (cite: Shirley2015; Jimenez-Donaire2017), lowering the effective critical density of HCN and yielding subthermally excited HCN emission (cite: Leroy2017a; Jones2023; Garcia-Rodriguez2023) or electron excitation (cite: Goldsmith2017) boosting the HCN emission. The reduced $\text{SFE}_{\text{dense}}$ could be the result of a strong influence of gas dynamics on the star formation process (bar), e.g. shear, hampering the formation of stars despite the availability of dense gas (Sect. [5.3](#sec:discussion:bar)). We note that centres are much more affected by variations in conversion factors ($\alpha_{\text{CO}}$ and $\alpha_{\text{HCN}}$) than discs, and the SFR estimator (extinction-corrected $\text{H}\alpha$) is potentially less accurate due to increasing dust attenuation towards centres and the effects of AGN-driven $\text{H}\alpha$ emission (although this galaxy has no AGN according to (cite: Veron2010)). Most probably, the low SFR/HCN in the centre is a combination of an increase in gas turbulence driving HCN emission and a lower HCN-to-dense gas conversion factor.

Spiral arms, interarm regions and bar ends share a similar SFR/HCN distribution suggesting they are similarly efficiently converting dense gas into stars.

This is contradictory to the hypothesis that bar ends are the sites of increased star formation efficiency, e.g. via cloud-cloud collision that might boost the SFE (cite: Watanabe2011; Maeda2021). However, we note that the aforementioned works investigate the star formation efficiency of the bulk molecular gas, traced via SFR/CO. Therefore, their implications are likely not applying to our study of SFR/HCN, since high SFR/CO does not imply high SFR/HCN.

Overall, spiral arms and interarm regions show comparable HCN/CO and SFR/HCN distributions and means across the detected sight lines (HCN/CO of $0.041$ and $0.049$, SFR/HCN of $0.112$ and $0.084$, respectively in spiral arms and interarm regions) which demonstrates that, although spiral arms appear to show higher gas pressure and accumulate gas, they do not contain higher density clouds nor are more efficiently converting the dense gas to stars. This result agrees with findings from Milky Way clouds (cite: Dib2012; Moore2012; Eden2012; Eden2013; Eden2015; Ragan2016; Ragan2018; Rigby2019; Urquhart2021) as well as supported by high-resolution simulations of galactic-scale star formation (cite: Tress2020).

![](Figures/ngc4321_HCN_ratios_vs_radius_environments_compressed_v3.pdf)

## Radial trends

Figure [6](#fig:hcn_ratios_vs_radius_and_pressure) (left) shows the variation of HCN/CO and SFR/HCN with galactocentric radius. To show the average trend (red markers), we stack the data in radial bins of 0.5   width, i.e. at twice the beam size. We then fit a piece-wise linear regression model (MARS), using the `R`-package `earth` as described in Sect. [3.8](#sec:methods:fitting). The resulting piece-wise linear regression parameters are listed in Tab. [\[tab:fit_parameters\]](#tab:fit_parameters). The MARS model finds two regimes in each of the radial correlations, which separates the relations into a central region ($\leq\SI{2.0}{\kilo\parsec}$ for HCN/CO and $\leq\SI{2.8}{\kilo\parsec}$ SFR/HCN) and a disc region (outside of the aforementioned thresholds). The central region covers about half of the bar length, which extends out to 4  

We note that the apparent offset between the significant data ($\rm{S/N}\geq 3$; dark blue markers) and the stacked average trends is expected in the presence of low HCN detection fraction, which is the case for most data at high $r_{\rm gal}$ or low $\langle P_{\text{DE}}\rangle$. While the stacks take into account the non-detections thus recovering the true, unbiased average value, the 3-sigma clipped data are (on average) biased towards higher HCN/CO because the low HCN/CO sightline measurements tend to fall below the 3-sigma threshold, but are included in the stacked measurement.

### HCN/CO vs galactocentric radius

In the inner 2.0  , we measure a very strong (slope $m=-0.38\pm 0.02$, Pearson correlation coefficient $\rho=-0.86$, $p=\num{1.73e-51}$), tight (scatter of 0.14) relation between HCN/CO and $r_{\rm gal}$. HCN/CO increases towards the centre of the galaxy where it is almost one order of magnitude higher than on average at larger $r_{\rm gal}$ agreeing with the spatial variations discussed in Section [4.1](#sec:results:spatial_variations). Assuming HCN/CO traces density, this suggests that the fraction of dense gas is higher in the centre, consistent with resolved observations of galaxies (cite: Bigiel2016; Gallagher2018a; Jimenez-Donaire2019; Beslic2021; Neumann2023a).

Across the disc ($\ensuremath{r_{\rm gal}}>\SI{2.0}{\kilo\parsec}$), HCN/CO remains constant on average ($m=0.0\pm 0.01$, $\rho=-0.14$, $p=0.306$) suggesting a more constant cloud mean density outside of galaxy centres. However, we observe a large scatter (0.23) about the fit line, indicating substantial variations in HCN/CO depending on the exact location in the galaxy. Overall, this means that outside of the centre of $\mathrm{NGC\,4321}$$r_{\rm gal}$ is not a good predictor of HCN/CO at 260 resolution.

### SFR/HCN vs galactocentric radius

Similar to HCN/CO, in the central 2.8  , SFR/HCN varies systematically with radius ($m=0.34\pm 0.02$, $\rho=0.32$, $p=\num{1.64e-05}$), though with the opposite sign ($m=0.08\pm 0.01$, $\rho=0.41$, $p=\num{1.64e-05}$). SFR/HCN drops towards the centre ($\mathrm{SFR/HCN}\sim\num{1e-2}$) by roughly one order of magnitude with respect to the disc average value ($\mathrm{SFR/HCN}\sim\num{1e-1}$) which, taken at face value, points towards galaxy centres being less efficient in converting dense gas to stars in line with many previous works studying dense gas via HCN (cite: Usero2015; Bigiel2016; Gallagher2018a; Jimenez-Donaire2019; Querejeta2019; Beslic2021; Neumann2023a). However, we note that both HCN (due to optical depth and excitation effects) and $\text{H}\alpha$(due to increased extinction, though here supported by additional SFR tracers; see App. [9](#sec:appendix:sfr_tracers) for a discussion about SFR tracers in the galaxy centre) are expected to become less robust tracers of dense gas mass and SFR in galaxy centres thus mitigating any conclusions about $\text{SFE}_{\text{dense}}$ in these regions.

## ISM pressure relations

Similar to the radial trends (Sect. [4.2](#sec:results:radius)), we employ the MARS tool to the stacked data in order to find regimes with different linear behaviour. The fit results are listed in Tab. [\[tab:fit_parameters\]](#tab:fit_parameters) and shown in the right-hand panels of Fig. [6](#fig:hcn_ratios_vs_radius_and_pressure). We find a pressure threshold in both relations (HCN/CO and SFR/HCN) at $\ensuremath{\langle P_{\text{DE}}\rangle}\approx\SI{4e5}{\kB\kelvin\per\cubic\centi\metre}$ and $\ensuremath{\langle P_{\text{DE}}\rangle}\approx\SI{1e6}{\kB\kelvin\per\cubic\centi\metre}$ computed via Equ. [\[equ:PDE_avg\]](#equ:PDE_avg) (the threshold value is shown as a contour overlaid on the galaxy map in the Appendix, Fig. [14](#fig:maps_pressure_contours); the corresponding pressure values using the alternative Equ. [\[equ:PDE_large\]](#equ:PDE_large) are $\ensuremath{P_{\text{DE}}}\approx\SI{4e5}{\kB\kelvin\per\cubic\centi\metre}$ (HCN/CO) and $\ensuremath{P_{\text{DE}}}\approx\SI{1e5}{\kB\kelvin\per\cubic\centi\metre}$ (SFR/HCN)). We note that our cloud-scale $\langle P_{\text{DE}}\rangle$ measurements yield a factor of two to three larger values than the beam-matched 260-scale pressure measurements. For better comparison with previous studies that have no access to $\sim\SI{100}{\parsec}$-scale molecular gas measurements, we quote the corresponding threshold pressure values of $\ensuremath{P_{\text{DE}}}\approx\SIrange{1.5e5}{6.3e5}{\kB\kelvin\per\cubic\centi\metre}$, which consider the CO data convolved to 260-scale (opposed to the weighted average of the 120-scale CO measurements).

### HCN/CO vs pressure

We find a strong positive correlation between the ($\langle P_{\text{DE}}\rangle$-average) HCN/CO and the ISM pressure, $\langle P_{\text{DE}}\rangle$, in both the high ($\rho=0.64$, $p=\num{2.84e-34}$) and low-pressure regime ($\rho=0.79$). The correlation is steeper in the high-pressure ($m=0.42\pm 0.03$) regime compared to the low-pressure regime ($m=0.18\pm 0.03$). However, the realtion could also be well fitted with a single linear function with $m=0.35\pm 0.02$. Thus, the average HCN/CO increases in a roughly uniform way from $\ensuremath{\langle P_{\text{DE}}\rangle}\approx\SIrange{5e4}{3e7}{\kB\kelvin\per\cubic\centi\metre}$ suggesting that the ISM pressure is well correlated with the average HCN/CO ($\rho=0.75$) over almost three orders of magnitude in pressure.

### SFR/HCN vs pressure

In the high-pressure regime we find a moderate negative correlation ($\rho=-0.39$, $p=0.003$,$m=-0.89\pm 0.22$) between the ($\langle P_{\text{DE}}\rangle$-average) SFR/HCN and ISM pressure extending over two order of magnitude in $x$- and $y$-axis. In the low-pressure regime the relation is significantly flatter ($m=-0.32\pm 0.04$) than in the high-pressure regime showing that across the disc, where the ISM pressure is low, SFR/HCN seems to partly decouple from the environmental pressure. However, in both regimes, there is a significant scatter (0.39 to 0.54) about the average relation indicating that SFR/HCN is likely affected by other physical conditions than just the pressure or cloud properties (see App. [10.1](#sec:appendix:cloud_relations)), e.g. star formation time scales or gas dynamics, where the latter could play a major role in galaxy centres and bars.

![](Figures/ngc4321_HCN_ratios_vs_pressure_environments_compressed.pdf)

## Morphological environments

In the next step, we analyse the individual morphological environments (centre, bar, bar ends, spiral arms, and interarm, as in Sect. [4.1](#sec:results:spatial_variations)) in the above-discussed scaling relations. The radial relations (Fig. [7](#fig:hcn_ratios_vs_radius_env)) show that the centre and bar are well separated from the other environments as a function of galactocentric radius, completely dominating the strong negative (HCN/CO) and positive (SFR/HCN) trends with $r_{\rm gal}$. At larger radii, i.e. $\ensuremath{r_{\rm gal}}\gtrsim\SI{2.5}{\kilo\parsec}$, we find several overlapping environments (bar, bar ends, spiral arms, and interam) as a function of radius. The mean trends of the HCN/CO and SFR/HCN vs $r_{\rm gal}$ relation for each environment show an identical behaviour as the global relation shown in Sect. [4.4](#sec:results:environments) and we do not find a difference between these environments.

In the HCN/CO vs $\langle P_{\text{DE}}\rangle$ relation (top row of Fig. [8](#fig:hcn_ratios_vs_pressure_env)), we observe parallel trends among all environments, with the bar ends and the centre being shifted to higher HCN/CO values (following the mean trends presented as coloured lines). Spiral arms and interarm regions show similar HCN/CO vs pressure relations suggesting that in these environments the molecular clouds have a similar mean density.

In the SFR/HCN vs $\langle P_{\text{DE}}\rangle$ relations (bottom row of Fig. [8](#fig:hcn_ratios_vs_pressure_env)) the strong trend in the high-pressure regime is again dominated by the centre where SFR/HCN drops by one order of magnitude with increasing ISM pressure. Comparing spiral arms and interarm regions, we find very similar, almost flat trends showing that spiral arms and interarm regions have similar SFR/HCN across $\SIrange{1}{2}{\dex}$ of ISM pressure and that across the disc SFR/HCN is less dependent on the ISM pressure. In the bar ends we also find a flat trend as a function of pressure but shifted to lower SFR/HCN compared to the disc. The bar, despite having similar HCN/CO than the disc, shows much lower SFR/HCN across the whole range of ISM pressure, more consistent with the values found in the centre. This shows that the bar region is a peculiar environment in its star formation properties (see Sect. [5.3](#sec:discussion:bar) for further discussion).

## HCN/CO as a density tracer

Extragalactic studies of nearby galaxies at kpc-scales (cite: Gallagher2018a; Jimenez-Donaire2019), report a positive correlation of the HCN/CO line ratio with the kpc-scale molecular gas surface density ($\Sigma_{\text{mol}}$) as traced by the CO line intensity over more than two orders of magnitude. These observational results are supported by theoretical works which show that HCN/CO is expected to positively correlate with the dense gas fraction and the mean gas density (cite: Leroy2017a). The physical interpretation put forward for explaining the strong relation between HCN/CO and $\Sigma_{\text{mol}}$ is that HCN/CO is expected to trace the density distribution of molecular clouds within the beam. This interpretation is strongly supported by recent works (cite: Gallagher2018b; Neumann2023b) which compared the kpc-scale HCN/CO with the cloud-scale $\Sigma_{\text{mol}}$ finding a strong positive correlation. Recently, (cite: Tafalla2023) measured the HCN/CO vs $\text{H}_2$ column density relation in three Solar Neighbourhood clouds, finding a similar, strong positive correlation, at least qualitatively in agreement with the extragalactic results.

With the new 260-scale HCN observations of $\mathrm{NGC\,4321}$, we can now take the next step and study the relation between HCN/CO and $\Sigma_{\text{mol}}$ at sub-kpc scales, making these results more comparable to Galactic works. In Fig. [9](#fig:hcn_co_scaling), we present the relation between the $\text{HCN(1--0)}$-to-$\text{CO(1--0)}$ line ratio and $\Sigma_{\text{mol}}$, measured at 260 resolution. Here, $\Sigma_{\text{mol}}$ is inferred from the $\text{CO(2--1)}$ line intensity using the lower-resolution $R_{21}$ map and the surface density-metallicity based $\alpha_{\text{CO}}$ prescription as described in Sect. [3.2](#sec:methods:sigmol). We note, that here we use the HCN/$\text{CO(1--0)}$, inferred from the $\text{CO(2--1)}$ using the estimated $R_{21}$, instead of the HCN/$\text{CO(2--1)}$ line ratio in order to better compare with literature relations. The resulting dense gas fraction, $f_{\text{dense}}$, shown as a secondary $y$-axis, is computed using a MW-based, constant $\ensuremath{\alpha_{\text{CO}}}=\SI{4.35}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$ and a constant $\ensuremath{\alpha_{\text{HCN}}}=\SI{14}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$. Hence $f_{\text{dense}}$ is assumed to be proportional to HCN/$\text{CO(1--0)}$(App. [7.1](#sec:appendix:aco)).

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| $m$ (unc.) | $b$ (unc.) | $\sigma$ | $\Sigma_{\text{mol}}$ res. | HCN/CO res. | $\Sigma_{\text{mol}}$ method | Reference |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) |
| 0.61 (0.10) | -2.64 (0.21) | 0.28 | 260 | 260 | beam-matched | this work |
| 0.72 (—) | -2.88 (—) | — | $300-\SI{600}{\parsec}$ | $300-\SI{600}{\kilo\parsec}$ | beam-matched | (cite: Gallagher2018a) |
| 0.81 (0.09) | -3.80 (0.21) | — | 120 | 650 | CO-weighted average | (cite: Gallagher2018b) |
| 0.50 (0.10) | -2.40 (0.20) | — | $\sim\SI{2}{\kilo\parsec}$ | $\sim\SI{2}{\kilo\parsec}$ | beam-matched | (cite: Jimenez-Donaire2019) |
| 0.41 (0.03) | -2.70 (0.08) | 0.14 | $\sim\SI{100}{\parsec}$ | $1- \SI{2}{\kilo\parsec}$ | CO-weighted average | (cite: Neumann2023a) |
| 0.71 (0.03) | -3.30 (0.80) | — | $\sim\SI{0.1}{\parsec}$ | $\sim\SI{0.1}{\parsec}$ | beam-matched | (cite: Tafalla2023) |
| 0.59 (0.03) | -2.64 (0.04) | 0.18 | $1- \SI{2}{\kilo\parsec}$ | $1- \SI{2}{\kilo\parsec}$ | beam-matched | Neumann, Jiménez-Donaire et al. in prep. |

**Notes** – Best-fit lines of HCN/CO vs $\Sigma_{\text{mol}}$ of the form shown in Equ. [\[equ:hcn_co_vs_sigmol\]](#equ:hcn_co_vs_sigmol), with slope $m$ (column 1), intercept $b$ (column 2) and respective uncertainties. $\sigma$ (column 3) denotes the 1-sigma scatter of the significant data about the fit line. The lines are plotted in Fig. [9](#fig:hcn_co_scaling). Columns 4 and 5 list the respective $x-$ ($\Sigma_{\text{mol}}$) and $y-$axis (HCN/CO) resolutions. “Beam-matched” (column 6) refers to a matched resolution of the $x-$ and $y-$axis data, and “CO-weighted average” denotes a CO intensity-weighted average measurement of $\Sigma_{\text{mol}}$, adopted in (cite: Gallagher2018b) and (cite: Neumann2023a). The differences between the physical scales and methodologies are discussed in the text.

Analogous to previous sections and following Sect. [3.8](#sec:methods:fitting), we stack and fit the data to obtain the mean relation: $$\begin{align}
    
    \log_{10}\left(\dfrac{\rm HCN}{\ensuremath{\text{CO(1--0)}}}\right) = -2.64 + 0.61\,\log_{10}\left(\dfrac{\ensuremath{\Sigma_{\text{mol}}}}{\SI{}{\Msun\per\square\parsec}}\right) \,.
    \label{equ:hcn_co_vs_sigmol}
\end{align}$$ We list the relation parameters along with uncertainties and relations from the literature in Tab. [\[tab:hcn_co_relation\]](#tab:hcn_co_relation). We note that we exclude data below $\ensuremath{\Sigma_{\text{mol}}}<\SI{10}{\Msun\per\square\parsec}$ (shaded region in Fig. [9](#fig:hcn_co_scaling)) from the fit, because at lower surface densities the trend does not seem to continue in the same manner. This could indicate that at low surface densities, HCN/CO does not increase with $\Sigma_{\text{mol}}$ anymore. (cite: Santa-Maria2023) argued that this could be due to HCN being excited in hot, low-surface density regions. However, due to a lack of sensitivity below $\ensuremath{\Sigma_{\text{mol}}}=\SI{10}{\Msun\per\square\parsec}$, we can not test this hypothesis with our data. We stress hat such a trend can be the result of low completeness thus reflecting the biased-high average HCN/CO if either HCN and CO are clipped ($\rm{S/N}\geq 3$) or if the $x$-axis is not complete. First and foremost, at $\ensuremath{\Sigma_{\text{mol}}}>\SI{10}{\Msun\per\square\parsec}$, we find a strong positive correlation between HCN/CO and $\Sigma_{\text{mol}}$ which agrees well with much of the prior literature. Though, the scatter in the individual 260 sight-line measurements is twice as large (0.28) as the scatter at kpc-scales (0.14). The larger scatter at smaller scales indicates strong cloud-to-cloud variations in qualitative agreement with Galactic studies finding large $f_{\text{dense}}$ variations (cite: Moore2012; Eden2012; Csengeri2016; Urquhart2021; Tafalla2023). One explanation for the increased scatter at smaller scales can be cloud evolution effects, leading to changes in the HCN/CO line ratio over the life cycle of molecular clouds, which can only be resolved at smaller scales (cite: Kruijssen2014a). (cite: Tafalla2023) suggest that some of the variations are caused by gas temperature variations between clouds, affecting the HCN excitation. In addition, HCN (and CO) emissivity can be affected by optical depth (cite: Shirley2015; Leroy2017a; Jimenez-Donaire2017; Jones2023; Garcia-Rodriguez2023) and electron excitation (cite: Goldsmith2017), further driving the scatter about the relation. Certainly, in-depth investigations of HCN at higher resolution in nearby galaxies are needed to understand what is driving HCN/CO at fixed surface density.

![](Figures/ngc4321_HCN_CO_vs_Sigmol_ACO_B13_MUSEGPR_compressed.pdf)

Comparing with previous literature findings, the exact relations vary significantly between different studies. The reported slopes span values from 0.41 over 0.61 (this work) to 0.81. Neumann, Jiménez-Donaire et al. in prep. combine measurements from EMPIRE (cite: Jimenez-Donaire2019) and ALMOND (cite: Neumann2023a) and match methodologies to obtain an updated, more robust constraint on the HCN/CO vs $\Sigma_{\text{mol}}$ relation at kpc-scales, yielding a slope of 0.59 consistent with the slope found for $\mathrm{NGC\,4321}$ in this work. Some of the differences between studies can at least partially be attributed to different methodologies. For instance, the adopted $\alpha_{\text{CO}}$ prescription significantly affects the measured relation. For $\mathrm{NGC\,4321}$, using a constant $\alpha_{\text{CO}}$ yields a shallower relation (slope of 0.48) compared to 0.61 with a varying $\alpha_{\text{CO}}$ using the prescription described by Equ. [\[equ:aco\]](#equ:aco). Moreover, the physical scales observed can significantly affect slopes ((cite: Gallagher2018b) found a slope of 0.41 at 2.8  -scale opposed to 0.81 at 650-scale). In addition, using $\text{CO(2--1)}$ instead of $\text{CO(1--0)}$ will affect the slope if a constant $R_{21}$ is used to convert $\text{CO(2--1)}$ to $\text{CO(1--0)}$, making the slope flatter than a native $\text{CO(1--0)}$ measurement, since $R_{21}$ negatively correlates with $\Sigma_{\text{mol}}$(cite: Leroy2022). For these reasons, comparisons between different studies have to be taken with care. Nevertheless, we want to stress that, independent of methodologies, HCN/CO, at least qualitatively, robustly traces the average molecular gas density from sub-pc to kpc scales.

Even if tracers and methods are matched, the resolution is expected to affect the observed relation if the emission is not beam-filling. EMPIRE (cite: Jimenez-Donaire2019) and ALMOND (cite: Neumann2023a) both studied kpc-scale HCN/CO as a function of $\Sigma_{\text{mol}}$. However, ALMOND used (intensity-weighted) cloud-scale (150) $\Sigma_{\text{mol}}$, while EMPIRE used matched-resolution kpc-scale $\Sigma_{\text{mol}}$. Comparing the HCN/CO vs $\Sigma_{\text{mol}}$ from EMPIRE and ALMOND, we find a $\sim\SI{1}{\dex}$ shift of the relation towards higher $\Sigma_{\text{mol}}$ at smaller scales. These results suggest that the CO filling factor is lower by a factor of $\sim 10$ at $\sim\SI{1}{\kilo\parsec}$ compared to $\sim\SI{100}{\parsec}$. Furthermore, increasing the resolution of the HCN measurements, i.e. going to smaller-scale HCN/CO measurements, appears to make the relations steeper (see above) and shifted towards higher HCN/CO, suggesting that HCN is clumpier and/or tracing denser gas than CO.

HCN abundance is expected to vary with metallicity due to the strong decrease of nitrogen-bearing species (e.g. HCN) with decreasing metallicity opposed to oxygen-bearing species (e.g. HCO$^+$) (cite: Braine2017; Braine2023). However, across $\mathrm{NGC\,4321}$ the metallicity varies by only $\sim\SI{0.1}{\dex}$ (see bottom panel of Fig. [13](#fig:maps_conversion_factors)). Therefore, abundance and optical depth variations connected to metallicity changes are expected to play only a minor role in affecting the HCN emissivity. In the appendix (Fig. [15](#fig:metallicity_trends)), we show how the HCN-to-HCO$^+$ line ratio varies with metallicity across $\mathrm{NGC\,4321}$, finding almost no dependence of HCN/HCO$^+$ on metallicity, supporting the aforementioned statement that HCN is yielding similar results as other dense gas tracers. To further support this statement, we investigated the same scaling relations that are shown in Fig. [6](#fig:hcn_ratios_vs_radius_and_pressure), replacing HCN by HCO$^+$ as a dense gas tracer, yielding the same trends with $r_{\rm gal}$ and $\langle P_{\text{DE}}\rangle$. The average relations agree within 10 % with the HCN results except for the central $\sim\SI{1}{\kilo\parsec}$, where HCN is about 30 % brighter than the average line ratio value of $\rm{HCN/HCO}^+\approx 1.3$.

We note that the trend expressed by Equ. [\[equ:hcn_co_vs_sigmol\]](#equ:hcn_co_vs_sigmol) could be driven by the centre, where we find the strongest systematic variations in HCN/CO. If HCN/CO is interpreted as $f_{\text{dense}}$, we expect the highest centre-to-disc variations in the $\alpha_{\text{CO}}$ and $\alpha_{\text{HCN}}$ conversion factors in the centre caused e.g. by strong variations in optical depth and excitation temperature, which could additional affect the correlation between $f_{\text{dense}}$ and $\Sigma_{\text{mol}}$. We checked that both the centre and the disc show a significant positive correlation between HCN/CO and $\Sigma_{\text{mol}}$ with slopes of 0.25 (centre) and 0.35 (disc), which shows that even when the centre is excluded there is a clear dependence of HCN/CO on $\Sigma_{\text{mol}}$. However, the relations in the individual environments are much flatter compared to the overall trend (slope of 0.61) and offset by about 0.4, which indicates that the overall HCN/CO vs $\Sigma_{\text{mol}}$ trend might be enhanced by a centre-to-disc dichotomy.

# Discussion

## Pressure threshold for dense gas and star formation

Over the last decade, resolved kpc-scale observations of nearby galaxies have found a systematic correlation between high-critical density tracer ratios, i.e. HCN/CO and SFR/HCN, and the environmental pressure in the ISM disc (cite: Gallagher2018a; Gallagher2018b; Jimenez-Donaire2019; Neumann2023a). These results are qualitatively supported by observations of the Milky Way’s CMZ, where the star formation efficiency of the (dense) molecular gas is low (cite: Longmore2013; Kruijssen2014b; Henshaw2023). These results contrast with Solar neighbourhood results that tend to find a constant SFR/HCN (cite: Heiderman2010; Lada2010; Lada2012; Evans2014). However, these Solar Neighbourhood observations probe a much lower ISM pressure environment ($\ensuremath{P_{\text{DE}}}\lesssim\SI{2e4}{\kB\kelvin\per\cubic\centi\metre}$) than typical extragalactic works. The apparent tension between the Galactic and extragalactic works could, however, be solved if there existed a pressure threshold above which cloud properties and hence the observed spectroscopic ratios depend on pressure. Below this threshold, the clouds would be able to decouple from the environment and show universal behaviour in converting the dense gas to stars, a concept also put forward by theoretical works (cite: Krumholz2007; Ostriker2010; Krumholz2012). (cite: Gallagher2018a) suggests that this pressure threshold could be at $\ensuremath{P_{\text{DE}}}\approx\SI{2e5}{\kB\kelvin\per\cubic\centi\metre}$, which is similar to the internal pressure of a typical GMC with $\ensuremath{\Sigma_{\text{mol}}}=\SI{100}{\Msun\per\square\parsec}$. We note that our formulation of the ISM pressure includes both the environment (gas and stellar mass) as well as cloud-scale molecular gas mass leading to a factor of 2–3 higher $P_{\text{DE}}$ values compared to the purely kpc-scale environmental $P_{\text{DE}}$(cite: Sun2020a). Therefore, the exact value of the pressure threshold is likely to vary with the resolution at which the pressure is measured.

With the new wide-field, deep HCN observations of $\mathrm{NGC\,4321}$ presented in this work, we can now for the first time explore the low-pressure environment ($\ensuremath{P_{\text{DE}}}\approx\SI{1e5}{\kB\kelvin\per\cubic\centi\metre}$) at 260 scales in a Milky Way-like galaxy and address the question: “Is there a pressure threshold for dense gas and star formation?” In Figure [6](#fig:hcn_ratios_vs_radius_and_pressure) (right panels), we determined two pressure regimes in each of the relations based on the change in the behaviour of the mean trends using the methodology described in Sect. [3.8](#sec:methods:fitting). Focusing on the SFR/HCN vs $\langle P_{\text{DE}}\rangle$ relation, we find a clear negative correlation at high pressures which significantly flattens in the low-pressure regime (especially evident in the mean trends of the individual environments), with the threshold being at $\ensuremath{\langle P_{\text{DE}}\rangle}_{\rm threshold}=\SI{1.6e6}{\kB\kelvin\per\cubic\centi\metre}$. Thus, our results might support the pressure threshold hypothesis laid out above (slope changes by 30 %), though finding a threshold that is one order of magnitude higher than the value inferred from simple theoretical considerations ($\ensuremath{P_{\text{DE}}}\approx\SI{2e5}{\kB\kelvin\per\cubic\centi\metre}$). We note, however, that the measured pressure estimates depend strongly on the scales at which they are measured. (cite: Sun2020a) show that larger physical scales ($\sim\SI{1}{\kilo\parsec}$) can lead to lower pressure estimates due to averaging out GMC-scale ($\sim\SI{100}{\parsec}$) variations of the molecular gas. Therefore, even higher resolution observations ($\lesssim\SI{100}{\parsec}$) are needed to obtain robust quantitative pressure estimates comparable with Solar Neighbourhood measurements.

In the appendix, we also present the relations between the spectroscopic ratios and the 120-scale molecular gas properties (Fig. [11](#fig:hcn_ratios_vs_cloud_props)) representing the self-gravity term on the ISM pressure as well as the relation with stellar mass surface density (Fig. [12](#fig:hcn_ratios_vs_stars)) representing the environment term. We find that a threshold-like behaviour is only seen in the cloud property relation, where SFR/HCN becomes almost constant in the low-$\Sigma_{\text{mol}}$, low-$\sigma_{\text{mol}}$ regime. In contrast, SFR/HCN shows a monotonic negative relation with $\Sigma_{\star}$ suggesting that clouds are always connected to the environmental pressure, but in the low-pressure environment the amount of dense gas is converted into stars in a uniform way independent of the cloud-scale properties.

## Normal star formation efficiency in bar ends

Observations (cite: Kenney1991; Harada2019; Sormani2019; Yu2022a; Yu2022b) and simulations (cite: Sormani2018) show that gas inflow from the spiral arms and gas outflow from the bar can feed the bar ends with molecular gas. As a consequence, the bar ends are the principal site for cloud-cloud collisions, which are thought to either boost (cite: Habe1992; Benjamin2005; Lopez-Corredoira2007; Furukawa2009; Ohama2010; Fukui2014; Renaud2015; Fukui2016; Fukui2018; Torii2017; Sormani2020) or lower (cite: Fujimoto2020) the formation of stars, depending on the relative speed of the colliding clouds (cite: Takahira2014). his raises the question: “Do bar ends boost or suppress star formation?” In accordance with the picture that bar ends are fed by gas flows, we observe relatively bright HCN and CO emission, implying an accumulation of (dense) molecular gas in the bar ends. However, we do not find an increased $\text{SFE}_{\text{dense}}$, traced by SFR/HCN, compared to the rest of the disc (spiral arms and interarm), suggesting that collisions might enhance density but not necessarily lead to different processes in the dense gas. We discuss the bar environment in the following subsection (Sect. [5.3](#sec:discussion:bar)).

## Star formation suppression in the bar

Galactic bars are the sites of strong shear and gas streaming motions, which can potentially affect the (density) structure of molecular clouds and their ability to form stars (cite: Athanassoula1992; Emsellem2015; Sormani2018). (cite: Diaz-Garcia2021) find that bar strength can affect quenching, suggesting that bars are loci of suppressed star formation. However, (cite: Fraser-McKelvie2020) also find evidence for increased star formation along bars. (cite: Maeda2023) propose that the star formation efficiency of molecular gas (SFR/CO; $\text{SFE}_{\text{mol}}$) in nearby spiral galaxies is systematically suppressed in bars. Here, we go a step further and study the denser molecular gas (traced by HCN) that is more tightly related to SFR and its star formation efficiency, $\text{SFE}_{\text{dense}}$. On the one hand, we find very similar HCN/CO, tracing $f_{\text{dense}}$, in the bar as well as throughout the disc. Additionally, we observe the same average trend with ISM pressure as in all other environments suggesting that bars contain clouds with similar mean density than galaxy discs. On the other hand, the agreement with disc trends changes for the dense gas star formation efficiency ($\text{SFE}_{\text{dense}}$ traced by SFR/HCN), which is much lower than in the disc. The systematically lower SFR/HCN in the bar becomes even more evident in the relation with pressure, where the average trend of the bar is $\approx\SI{0.5}{\dex}$ lower compared to the other environments. This suggests that the bar of $\mathrm{NGC\,4321}$ is indeed much less efficient in converting dense molecular gas into stars despite the presence of overdense gas.

One explanation for the low $\text{SFE}_{\text{dense}}$ could be shearing motions inside the bar that are solenoidal in nature, lowering the star formation efficiency (cite: Federrath2016) or high-speed cloud-cloud collisions (cite: Fujimoto2020). Recent simulations (cite: Sormani2018) and observations (cite: Wallace2022) suggest that gas dynamics in the bar are more dominated by streaming motions from the bar ends towards the galactic centre. These streaming motions can result in deformation and stretching of the molecular clouds in the bar leading to elongated, destructed molecular clouds, which might counteract the gravitational collapse hence quenching star formation.

# Conclusions

We present new, deep, wide-field $\text{HCN(1--0)}$ dense molecular gas observations at scales of 260 of the nearby spiral galaxy $\mathrm{NGC\,4321}$. In combination with recent, high-resolution ($\sim\SI{1}{\ensuremath{''}}\sim\SI{100}{\parsec}$) observations of CO (PHANGS–ALMA, (cite: Leroy2021b)), tracing the bulk molecular gas and $\text{H}\alpha$ observations (PHANGS–MUSE; (cite: Emsellem2022)) tracing SFR (supported by 21 $\mu$ m observations from PHANGS–JWST (cite: Lee2023), we are able to study for the first time dense gas spectroscopic ratios (HCN/CO, SFR/HCN) in many individual sight lines and environments expanding into the low-pressure regime that is similar to the Solar neighbourhood environment. We use morphological masks based on the stellar mass content (cite: Querejeta2021) to distinguish between different environmental regions that have different structural and dynamical properties potentially affecting the properties of molecular clouds and their ability to form stars. We study how HCN/CO, a proxy of the dense gas fraction ($f_{\text{dense}}$), and SFR/HCN, a proxy of the dense gas star formation efficiency ($\text{SFE}_{\text{dense}}$), vary between different galactic environments and depend on the ISM pressure. Our key findings are:

1.  HCN/CO increases and SFR/HCN decreases towards the centre of the galaxy, and are roughly flat across the galactic disc. This suggests that galaxy centres have denser molecular clouds, but those are less efficiently converted into stars than in the disc. These global trends are consistent with previous results from kpc-scale surveys, but our superior resolution allows us to analyse the role of the environment in more detail. Distinguishing between environmental regions (centre, bar, bar ends, spiral arms, and interarm), we find HCN/CO to be significantly higher in the centre, while SFR/HCN is lower in both the centre and the bar. This shows that the star formation process is roughly universal across the disc of $\mathrm{NGC\,4321}$. In particular, we find no significant difference of HCN/CO and SFR/HCN between the spiral arms and interarm regions, but star formation from the dense gas is significantly less efficient in the bar and centre. The strong trends towards the centre of $\mathrm{NGC\,4321}$ suggest either that clouds couple strongly to the surrounding environment or that HCN is tracing more of the bulk molecular gas that is less efficiently converted into stars, the latter being in agreement with predictions from gravo-turbulent cloud models.

2.  The mean dense gas spectroscopic trends in the disc ($\ensuremath{r_{\rm gal}}\gtrsim\SI{2}{\kilo\parsec}$) of $\mathrm{NGC\,4321}$ are very similar among different environments (Fig. [7](#fig:hcn_ratios_vs_radius_env), Fig. [8](#fig:hcn_ratios_vs_pressure_env)). However, we observe a significant scatter of 0.14 to 0.54 in all relations at fixed radius or fixed pressure. This indicates that, although on average similar, cloud properties and their environment vary more significantly at smaller scales and are potentially strongly affected by local, cloud-scale ($\lesssim\SI{100}{\parsec}$) physics and local excitation conditions (e.g. gas temperature, optical depth).

3.  We identify a pressure threshold for dense gas and star formation at $\ensuremath{\langle P_{\text{DE}}\rangle}_{\rm threshold}\approx\SI{1e6}{\kB\kelvin\per\cubic\centi\metre}$ (Equ. [\[equ:PDE_avg\]](#equ:PDE_avg); Fig. [6](#fig:hcn_ratios_vs_radius_and_pressure)) corresponding to 260-scale $\ensuremath{P_{\text{DE}}}\approx\SI{4e5}{\kB\kelvin\per\cubic\centi\metre}$ (Equ. [\[equ:PDE_large\]](#equ:PDE_large)). While the relation between pressure and HCN/CO can also be well described by a single relation covering both regimes, the relation with SFR/HCN significantly flattens in the low-pressure regime. This supports the idea that there is a pressure threshold below which the star formation process in molecular clouds becomes less dependent on the environment as seen in Galactic measurements of molecular clouds. Thus, our findings hint towards resolving the tension between Galactic and extragalactic studies of dense gas and star formation.

4.  The bar of $\mathrm{NGC\,4321}$ is showing significantly lower SFR/HCN than the disc and is systematically shifted to lower SFR/HCN in relation to the ISM pressure. This is a strong indication that the star formation in the bar is suppressed by shear or streaming motion that prevents the gravitational collapse and thus star formation.

5.  We find a strong, positive correlation between HCN/CO and $\Sigma_{\text{mol}}$(Fig. [9](#fig:hcn_co_scaling)) with a slope of 0.61, using a varying $\alpha_{\text{CO}}$ to compute $\Sigma_{\text{mol}}$(for comparison, a constant $\alpha_{\text{CO}}$ yields a slope of 0.48). Our 260-scale results are in agreement with many previous studies from sub-pc (Galactic) to kpc-scales (extragalactic) and support the use of HCN/CO as a powerful tracer of molecular cloud average density. We emphasise that the exact relation depends on methodology and that scatter increases at smaller scales. We find a scale-dependence of the relation likely connected to the beam filling factors of CO and HCN, indicating that HCN emission is tracing denser gas than CO and originating from smaller than 260-scale regions.

These findings present the next step in connecting extragalactic and Galactic studies of dense gas and star formation. Overall, our results motivate the presence of a pressure threshold for dense gas and star formation and advertise the potential to link Galactic and extragalactic works. However, we are still not able to resolve individual GMCs ($\lesssim\SI{100}{\parsec}$) in galaxies beyond the local group and explore conditions similar to the Solar neighbourhood ($\ensuremath{P_{\text{DE}}}\approx\SI{2e4}{\kB\kelvin\per\cubic\centi\metre}$). Even deeper observations of dense gas tracers are needed to find better constraints on spectroscopic dense gas ratios in the Solar neighbour-like low-pressure environment. Moreover, we show that across the disc SFR tracers yield similar results, but towards the centre they can differ a lot, hence requiring more in-depth studies of galaxy centres to infer robust prescriptions of dense gas and star formation in these extreme environments. Further, this work investigates only a single galaxy. Ultimately, we need similar dense gas studies in a large sample of galaxies (as done in PHANGS) to study, e.g. the effect of bar dynamics on the star formation efficiency, or the pressure threshold hypothesis in a statistically meaningful sample of galaxies. Besides, the scale-dependence of the HCN/CO vs. $\Sigma_{\text{mol}}$ relation requires a more detailed study, particularly addressing the CO and HCN filling factors at sub-100 scales.

# Acknowledgements

LN acknowledges funding from the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) - 516405419.

AKL gratefully acknowledges support by grants 1653300 and 2205628 from the National Science Foundation, by award JWST-GO-02107.009-A, and by a Humboldt Research Award from the Alexander von Humboldt Foundation. The work of AKL is partially supported by the National Science Foundation under Grants No. 1615105, 1615109, and 1653300. AU acknowledges support from the Spanish grants PID2019-108765GB-I00, funded by MCIN/AEI/10.13039/501100011033, and PID2022-138560NB-I00, funded by MCIN/AEI/10.13039/501100011033/FEDER, EU. ER acknowledges the support of the Natural Sciences and Engineering Research Council of Canada (NSERC), funding reference number RGPIN-2022-03499.

MB acknowledges support by the ANID BASAL project FB210003 and by the French government through the France 2030 investment plan managed by the National Research Agency (ANR), as part of the Initiative of Excellence of Université Côte d’Azur under reference number ANR-15-IDEX-01.

MC gratefully acknowledges funding from the DFG through an Emmy Noether Research Group (grant number CH2137/1-1). COOL Research DAO is a Decentralized Autonomous Organization supporting research in astrophysics aimed at uncovering our cosmic origins.

KG is supported by the Australian Research Council through the Discovery Early Career Researcher Award (DECRA) Fellowship (project number DE220100766) funded by the Australian Government. KG is supported by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. JDH gratefully acknowledges financial support from the Royal Society (University Research Fellowship; URF/R1/221620). HAP acknowledges support by the National Science and Technology Council of Taiwan under grant 110-2112-M-032-020-MY3. MQ acknowledges support from the Spanish grant PID2019-106027GA-C44, funded by MCIN/AEI/10.13039/501100011033. TS acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343). ES acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343). SKS acknowledges financial support from the German Research Foundation (DFG) via Sino-German research grant SCHI 536/11-1. Y-HT acknowledges funding support from NRAO Student Observing Support Grant SOSPADA-012 and from the National Science Foundation (NSF) under grant No. 2108081. TGW acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343).

This paper makes use of the following ALMA data\
ADS/JAO.ALMA#2011.0.00004.SV,\
ADS/JAO.ALMA#2015.1.00956.S,\
ADS/JAO.ALMA#2017.1.00815.S.\
ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory (NRAO) is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Data availability

The data used within this paper will be provided on reasonable request to the corresponding author.

156 natexlab

(ref: Anand2021) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2021, MNRAS, 501, 3621

(ref: Athanassoula1992) Athanassoula, E. 1992, MNRAS, 259, 345

(ref: Barnes2020) Barnes, A. T., Kauffmann, J., Bigiel, F., et al. 2020, MNRAS, 497, 1972

(ref: Belfiore2023) Belfiore, F., Leroy, A. K., Sun, J., et al. 2023, A&A, 670, A67

(ref: Bemis2019) Bemis, A. & Wilson, C. D. 2019, AJ, 157, 131

(ref: Benincasa2016) Benincasa, S. M., Wadsley, J., Couchman, H. M. P., & Keller, B. W. 2016, MNRAS, 462, 3053

(ref: Benjamin2005) Benjamin, R. A., Churchwell, E., Babler, B. L., et al. 2005, ApJL, 630, L149

(ref: Beslic2021) Bešlić, I., Barnes, A. T., Bigiel, F., et al. 2021, MNRAS, 506, 963

(ref: Bigiel2016) Bigiel, F., Leroy, A. K., Jiménez-Donaire, M. J., et al. 2016, ApJL, 822, L26

(ref: Blitz2004) Blitz, L. & Rosolowsky, E. 2004, ApJL, 612, L29

(ref: Blitz2006) Blitz, L. & Rosolowsky, E. 2006, ApJ, 650, 933

(ref: Bolatto2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Braine2017) Braine, J., Shimajiri, Y., André, P., et al. 2017, A&A, 597, A44

(ref: Braine2023) Braine, J., Sun, Y., Shimajiri, Y., et al. 2023, A&A, 676, A27

(ref: Caldu-Primo2013) Caldú-Primo, A., Schruba, A., Walter, F., et al. 2013, AJ, 146, 150

(ref: Calzetti2007) Calzetti, D., Kennicutt, R. C., Engelbracht, C. W., et al. 2007, ApJ, 666, 870

(ref: casa_package) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Chen2017) Chen, H., Braine, J., Gao, Y., Koda, J., & Gu, Q. 2017, ApJ, 836, 101

(ref: Chen2015) Chen, H., Gao, Y., Braine, J., & Gu, Q. 2015, ApJ, 810, 140

(ref: Csengeri2016) Csengeri, T., Weiss, A., Wyrowski, F., et al. 2016, A&A, 585, A104

(ref: denBrok2022) den Brok, J. S., Bigiel, F., Sliwa, K., et al. 2022, A&A, 662, A89

(ref: denBrok2021) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS, 504, 3221

(ref: Diaz-Garcia2021) Dı́az-Garcı́a, S., Lisenfeld, U., Pérez, I., et al. 2021, A&A, 654, A135

(ref: Dib2012) Dib, S., Helou, G., Moore, T. J. T., Urquhart, J. S., & Dariush, A. 2012, ApJ, 758, 125

(ref: Eden2013) Eden, D. J., Moore, T. J. T., Morgan, L. K., Thompson, M. A., & Urquhart, J. S. 2013, MNRAS, 431, 1587

(ref: Eden2012) Eden, D. J., Moore, T. J. T., Plume, R., & Morgan, L. K. 2012, MNRAS, 422, 3178

(ref: Eden2015) Eden, D. J., Moore, T. J. T., Urquhart, J. S., et al. 2015, MNRAS, 452, 289

(ref: Eibensteiner2022) Eibensteiner, C., Barnes, A. T., Bigiel, F., et al. 2022, A&A, 659, A173

(ref: Elmegreen1989) Elmegreen, B. G. 1989, ApJ, 338, 178

(ref: Elmegreen1994) Elmegreen, B. G. & Parravano, A. 1994, ApJL, 435, L121

(ref: Emsellem2015) Emsellem, E., Renaud, F., Bournaud, F., et al. 2015, MNRAS, 446, 2468

(ref: Emsellem2022) Emsellem, E., Schinnerer, E., Santoro, F., et al. 2022, A&A, 659, A191

(ref: Evans2014) Evans, Neal J., I., Heiderman, A., & Vutisalchavakul, N. 2014, ApJ, 782, 114

(ref: Evans2020) Evans, Neal J., I., Kim, K.-T., Wu, J., et al. 2020, ApJ, 894, 103

(ref: Federrath2016) Federrath, C., Rathborne, J. M., Longmore, S. N., et al. 2016, ApJ, 832, 143

(ref: Fisher2019) Fisher, D. B., Bolatto, A. D., White, H., et al. 2019, ApJ, 870, 46

(ref: Fraser-McKelvie2020) Fraser-McKelvie, A., Aragón-Salamanca, A., Merrifield, M., et al. 2020, MNRAS, 495, 4158

(ref: Friedman1991) Friedman, J. H. 1991, The Annals of Statistics, 19, 1

(ref: Fujimoto2020) Fujimoto, Y., Maeda, F., Habe, A., & Ohta, K. 2020, MNRAS, 494, 2131

(ref: Fukui2014) Fukui, Y., Ohama, A., Hanaoka, N., et al. 2014, ApJ, 780, 36

(ref: Fukui2018) Fukui, Y., Torii, K., Hattori, Y., et al. 2018, ApJ, 859, 166

(ref: Fukui2016) Fukui, Y., Torii, K., Ohama, A., et al. 2016, ApJ, 820, 26

(ref: Furukawa2009) Furukawa, N., Dawson, J. R., Ohama, A., et al. 2009, ApJL, 696, L115

(ref: Gallagher2018b) Gallagher, M. J., Leroy, A. K., Bigiel, F., et al. 2018a, ApJL, 868, L38

(ref: Gallagher2018a) Gallagher, M. J., Leroy, A. K., Bigiel, F., et al. 2018b, ApJ, 858, 90

(ref: Gao2004) Gao, Y. & Solomon, P. M. 2004, ApJ, 606, 271

(ref: Garcia-Burillo2012) Garcı́a-Burillo, S., Usero, A., Alonso-Herrero, A., et al. 2012, A&A, 539, A8

(ref: Garcia-Rodriguez2023) Garcı́a-Rodrı́guez, A., Usero, A., Leroy, A. K., et al. 2023, A&A, 672, A96

(ref: jwst-mission) Gardner, J. P., Mather, J. C., Abbott, R., et al. 2023, PASP, 135, 068001

(ref: Goldsmith2017) Goldsmith, P. F. & Kauffmann, J. 2017, ApJ, 841, 25

(ref: Habe1992) Habe, A. & Ohta, K. 1992, PASJ, 44, 203

(ref: Harada2018) Harada, N., Sakamoto, K., Martı́n, S., et al. 2018, ApJ, 855, 49

(ref: Harada2019) Harada, N., Sakamoto, K., Martı́n, S., et al. 2019, ApJ, 884, 100

(ref: Hassani2023) Hassani, H., Rosolowsky, E., Leroy, A. K., et al. 2023, ApJL, 944, L21

(ref: Heiderman2010) Heiderman, A., Evans, Neal J., I., Allen, L. E., Huard, T., & Heyer, M. 2010, ApJ, 723, 1019

(ref: Henshaw2023) Henshaw, J. D., Barnes, A. T., Battersby, C., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 83

(ref: Herrera-Camu2017) Herrera-Camus, R., Bolatto, A., Wolfire, M., et al. 2017, ApJ, 835, 201

(ref: Jimenez-Donaire2017) Jiménez-Donaire, M. J., Bigiel, F., Leroy, A. K., et al. 2017, MNRAS, 466, 49

(ref: Jimenez-Donaire2019) Jiménez-Donaire, M. J., Bigiel, F., Leroy, A. K., et al. 2019, ApJ, 880, 127

(ref: Jimenez-Donaire2023) Jiménez-Donaire, M. J., Usero, A., Bešlić, I., et al. 2023, A&A, 676, L11

(ref: Jones2023) Jones, G. H., Clark, P. C., Glover, S. C. O., & Hacar, A. 2023, MNRAS, 520, 1005

(ref: Kauffmann2017) Kauffmann, J., Goldsmith, P. F., Melnick, G., et al. 2017, A&A, 605, L5

(ref: Kelly2007) Kelly, B. C. 2007, ApJ, 665, 1489

(ref: Kenney1991) Kenney, J. D. P. & Lord, S. D. 1991, ApJ, 381, 118

(ref: Kennicutt2012) Kennicutt, R. C. & Evans, N. J. 2012, ARA&A, 50, 531

(ref: Kepley2018) Kepley, A. A., Bittle, L., Leroy, A. K., et al. 2018, ApJ, 862, 120

(ref: Kepley2014) Kepley, A. A., Leroy, A. K., Frayer, D., et al. 2014, ApJL, 780, L13

(ref: Kim2011) Kim, C.-G., Kim, W.-T., & Ostriker, E. C. 2011, ApJ, 743, 25

(ref: Kim2015) Kim, C.-G. & Ostriker, E. C. 2015, ApJ, 815, 67

(ref: Kim2013) Kim, C.-G., Ostriker, E. C., & Kim, W.-T. 2013, ApJ, 776, 1

(ref: Koyama2009) Koyama, H. & Ostriker, E. C. 2009, ApJ, 693, 1346

(ref: Kregel2002) Kregel, M., van der Kruit, P. C., & de Grijs, R. 2002, MNRAS, 334, 646

(ref: Kroupa2001) Kroupa, P. 2001, MNRAS, 322, 231

(ref: Kruijssen2014a) Kruijssen, J. M. D. & Longmore, S. N. 2014, MNRAS, 439, 3239

(ref: Kruijssen2014b) Kruijssen, J. M. D., Longmore, S. N., Elmegreen, B. G., et al. 2014, MNRAS, 440, 3370

(ref: Krumholz2012) Krumholz, M. R., Dekel, A., & McKee, C. F. 2012, ApJ, 745, 69

(ref: Krumholz2005) Krumholz, M. R. & McKee, C. F. 2005, ApJ, 630, 250

(ref: Krumholz2007) Krumholz, M. R. & Thompson, T. A. 2007, ApJ, 669, 289

(ref: Lada2012) Lada, C. J., Forbrich, J., Lombardi, M., & Alves, J. F. 2012, ApJ, 745, 190

(ref: Lada2010) Lada, C. J., Lombardi, M., & Alves, J. F. 2010, ApJ, 724, 687

(ref: Lang2020) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122

(ref: Lee2023) Lee, J. C., Sandstrom, K. M., Leroy, A. K., et al. 2023, ApJL, 944, L17

(ref: Lee2022) Lee, J. C., Whitmore, B. C., Thilker, D. A., et al. 2022, ApJS, 258, 10

(ref: Leroy2021a) Leroy, A. K., Hughes, A., Liu, D., et al. 2021a, ApJS, 255, 19

(ref: Leroy2022) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2022, ApJ, 927, 149

(ref: Leroy2023) Leroy, A. K., Sandstrom, K., Rosolowsky, E., et al. 2023, ApJL, 944, L9

(ref: Leroy2019) Leroy, A. K., Sandstrom, K. M., Lang, D., et al. 2019, ApJS, 244, 24

(ref: Leroy2021b) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021b, ApJS, 257, 43

(ref: Leroy2017a) Leroy, A. K., Usero, A., Schruba, A., et al. 2017, ApJ, 835, 217

(ref: Leroy2009) Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137, 4670

(ref: Leroy2008) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782

(ref: Licquia2015) Licquia, T. C. & Newman, J. A. 2015, ApJ, 806, 96

(ref: Linden2020) Linden, S. T., Murphy, E. J., Dong, D., et al. 2020, ApJS, 248, 25

(ref: Longmore2013) Longmore, S. N., Bally, J., Testi, L., et al. 2013, MNRAS, 429, 987

(ref: Lopez-Corredoira2007) López-Corredoira, M., Cabrera-Lavers, A., Mahoney, T. J., et al. 2007, AJ, 133, 154

(ref: Maeda2023) Maeda, F., Egusa, F., Ohta, K., Fujimoto, Y., & Habe, A. 2023, ApJ, 943, 7

(ref: Maeda2021) Maeda, F., Ohta, K., Fujimoto, Y., & Habe, A. 2021, MNRAS, 502, 2238

(ref: Makarov2014) Makarov, D., Prugniel, P., Terekhova, N., Courtois, H., & Vauglin, I. 2014, A&A, 570, A13

(ref: Martin2021) Martı́n, S., Mangum, J. G., Harada, N., et al. 2021, A&A, 656, A46

(ref: Meidt2014) Meidt, S. E., Schinnerer, E., van de Ven, G., et al. 2014, ApJ, 788, 144

(ref: Moore2012) Moore, T. J. T., Urquhart, J. S., Morgan, L. K., & Thompson, M. A. 2012, MNRAS, 426, 701

(ref: Murphy2012) Murphy, E. J., Bremseth, J., Mason, B. S., et al. 2012, ApJ, 761, 97

(ref: Neumann2023b) Neumann, L., den Brok, J. S., Bigiel, F., et al. 2023a, A&A, 675, A104

(ref: Neumann2023a) Neumann, L., Gallagher, M. J., Bigiel, F., et al. 2023b, MNRAS, 521, 3348

(ref: Nguyen-Luong2017) Nguyen-Luong, Q., Anderson, L. D., Motte, F., et al. 2017, ApJL, 844, L25

(ref: O’Donnell1994) O’Donnell, J. E. 1994, ApJ, 422, 158

(ref: Ohama2010) Ohama, A., Dawson, J. R., Furukawa, N., et al. 2010, ApJ, 709, 975

(ref: Onus2018) Onus, A., Krumholz, M. R., & Federrath, C. 2018, MNRAS, 479, 1702

(ref: Ostriker2010) Ostriker, E. C., McKee, C. F., & Leroy, A. K. 2010, ApJ, 721, 975

(ref: Ostriker2011) Ostriker, E. C. & Shetty, R. 2011, ApJ, 731, 41

(ref: Padoan2002) Padoan, P. & Nordlund, Å. 2002, ApJ, 576, 870

(ref: Pan2017) Pan, H.-A. & Kuno, N. 2017, ApJ, 839, 133

(ref: Pessa2022) Pessa, I., Schinnerer, E., Leroy, A. K., et al. 2022, A&A, 663, A61

(ref: Querejeta2015) Querejeta, M., Meidt, S. E., Schinnerer, E., et al. 2015, ApJS, 219, 5

(ref: Querejeta2021) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, A&A, 656, A133

(ref: Querejeta2019) Querejeta, M., Schinnerer, E., Schruba, A., et al. 2019, A&A, 625, A19

(ref: Ragan2016) Ragan, S. E., Moore, T. J. T., Eden, D. J., et al. 2016, MNRAS, 462, 3123

(ref: Ragan2018) Ragan, S. E., Moore, T. J. T., Eden, D. J., et al. 2018, MNRAS, 479, 2361

(ref: Renaud2015) Renaud, F., Bournaud, F., Emsellem, E., et al. 2015, MNRAS, 454, 3299

(ref: Rigby2019) Rigby, A. J., Moore, T. J. T., Eden, D. J., et al. 2019, A&A, 632, A58

(ref: Salo2015) Salo, H., Laurikainen, E., Laine, J., et al. 2015, ApJS, 219, 4

(ref: Sanchez-Garcia2022) Sánchez-Garcı́a, M., Garcı́a-Burillo, S., Pereira-Santaella, M., et al. 2022, A&A, 660, A83

(ref: Santa-Maria2023) Santa-Maria, M. G., Goicoechea, J. R., Pety, J., et al. 2023, A&A, 679, A4

(ref: Schinnerer2017) Schinnerer, E., Meidt, S. E., Colombo, D., et al. 2017, ApJ, 836, 62

(ref: Schruba2019) Schruba, A., Kruijssen, J. M. D., & Leroy, A. K. 2019, ApJ, 883, 2

(ref: Schruba2011) Schruba, A., Leroy, A. K., Walter, F., et al. 2011, AJ, 142, 37

(ref: Sheth2010) Sheth, K., Regan, M., Hinz, J. L., et al. 2010, PASP, 122, 1397

(ref: Shetty2012) Shetty, R. & Ostriker, E. C. 2012, ApJ, 754, 2

(ref: Shimajiri2017) Shimajiri, Y., André, P., Braine, J., et al. 2017, A&A, 604, A74

(ref: Shirley2015) Shirley, Y. L. 2015, PASP, 127, 299

(ref: Sormani2019) Sormani, M. C. & Barnes, A. T. 2019, MNRAS, 484, 1213

(ref: Sormani2020) Sormani, M. C., Tress, R. G., Glover, S. C. O., et al. 2020, MNRAS, 497, 5024

(ref: Sormani2018) Sormani, M. C., Treß, R. G., Ridley, M., et al. 2018, MNRAS, 475, 2383

(ref: Spitzer1942) Spitzer, Lyman, J. 1942, ApJ, 95, 329

(ref: Stuber2023) Stuber, S. K., Pety, J., Schinnerer, E., et al. 2023, A&A, 680, L20

(ref: Sun2020a) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2020, ApJ, 892, 148

(ref: Sun2022) Sun, J., Leroy, A. K., Rosolowsky, E., et al. 2022, AJ, 164, 43

(ref: Sun2018) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860, 172

(ref: Tafalla2023) Tafalla, M., Usero, A., & Hacar, A. 2023, A&A, 679, A112

(ref: Takahira2014) Takahira, K., Tasker, E. J., & Habe, A. 2014, ApJ, 792, 63

(ref: Teng2023) Teng, Y.-H., Sandstrom, K. M., Sun, J., et al. 2023, ApJ, 950, 119

(ref: Torii2017) Torii, K., Hattori, Y., Hasegawa, K., et al. 2017, ApJ, 835, 142

(ref: Tress2020) Tress, R. G., Smith, R. J., Sormani, M. C., et al. 2020, MNRAS, 492, 2973

(ref: Urquhart2021) Urquhart, J. S., Figura, C., Cross, J. R., et al. 2021, MNRAS, 500, 3050

(ref: Usero2015) Usero, A., Leroy, A. K., Walter, F., et al. 2015, AJ, 150, 115

(ref: vanderKruit1988) van der Kruit, P. C. 1988, A&A, 192, 117

(ref: Veron2010) Véron-Cetty, M. P. & Véron, P. 2010, A&A, 518, A10

(ref: Viaene2018) Viaene, S., Forbrich, J., & Fritz, J. 2018, MNRAS, 475, 5550

(ref: Wallace2022) Wallace, J., Battersby, C., Mills, E. A. C., et al. 2022, ApJ, 939, 58

(ref: Walter2008) Walter, F., Brinks, E., de Blok, W. J. G., et al. 2008, AJ, 136, 2563

(ref: Watanabe2011) Watanabe, Y., Sorai, K., Kuno, N., & Habe, A. 2011, MNRAS, 411, 1409

(ref: Williams2022) Williams, T. G., Kreckel, K., Belfiore, F., et al. 2022, MNRAS, 509, 1303

(ref: Wong2002) Wong, T. & Blitz, L. 2002, ApJ, 569, 157

(ref: miri-paper) Wright, G. S., Rieke, G. H., Glasse, A., et al. 2023, PASP, 135, 048003

(ref: Yu2022b) Yu, S.-Y., Kalinova, V., Colombo, D., et al. 2022a, A&A, 666, A175

(ref: Yu2022a) Yu, S.-Y., Xu, D., Ho, L. C., Wang, J., & Kao, W.-B. 2022b, A&A, 661, A98

# Ancillary data

## CO-to-$\text{H}_2$ conversion factor – $\alpha_{\text{CO}}$

In this work, we employ two different conversion factors to convert the $\text{CO(2--1)}$ line intensity into a molecular gas surface density as described in Sect. [3.2](#sec:methods:sigmol).

### Constant conversion factor

As a first step, we study variations of the HCN-to-CO line ratio, which is a proxy for the dense gas fraction, adopting constant mass-to-light ratios (Sect. [3.3](#sec:methods:fdense)). We adopt a Milky-Way average CO-to-$\text{H}_2$ conversion factor of $\ensuremath{\alpha_{\text{CO}}}=\SI{4.35}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$ that is uncertain by a factor of two (cite: Bolatto2013). To convert the $\text{CO(2--1)}$ into a $\text{CO(1--0)}$ line intensity, we use a $\text{CO(2--1)}$-to-$\text{CO(1--0)}$ line ratio of $R_{21}=0.65\pm 0.17$ (cite: denBrok2021; Leroy2022).

### Spatially varying conversion factor

As a second step, we adopt varying conversion factors to obtain the most accurate estimation of the molecular gas surface density given the current knowledge about spatial variations of $\alpha_{\text{CO}}$ and $R_{21}$ in nearby galaxies at $\sim\SI{100}{\parsec}$ scales. This prescription enters the estimation of the dynamical equilibrium pressure (Sect. [3.6](#sec:methods:pde)). We convert the $\text{CO(2--1)}$ moment-0 ($W_{\text{CO(2--1)}}$) into a molecular gas surface density ($\Sigma_{\text{mol}}$) in a two-step process: First, we convert the $\text{CO(2--1)}$ into a $\text{CO(1--0)}$ line intensity by applying a spatially varying $\text{CO(2--1)}$-to-$\text{CO(1--0)}$ line ratio ($R_{21}$) map. This makes use of archival $\text{CO(1--0)}$ observations of $\mathrm{NGC\,4321}$ with ALMA at 4″ resolution. Hence we can compute $R_{21}$ at $\ang{;;4}\sim\SI{300}{\parsec}$ scale and infer $\text{CO(1--0)}$ from the measured $\text{CO(2--1)}$ at $\ang{;;1.67}\sim\SI{120}{\parsec}$ resolution: $$\begin{equation}
    W_{\ensuremath{\text{CO(1--0)}}}^{\ang{;;1.67}} \approx W_{\ensuremath{\text{CO(2--1)}}}^{\ang{;;1.67}} / R_{21}^{\ang{;;4}}
\end{equation}$$ Certainly, we expect small-scale variations of $R_{21}$ at $<\SI{300}{\parsec}$ scales, but using a 300-smoothed $R_{21}$ still provides more accurate estimates of $\text{CO(1--0)}$ and hence $\Sigma_{\text{mol}}$ than adopting a constant $R_{21}$. Here, we measure a median $R_{21}=0.54$ and a scatter of 0.16. We show a map of $R_{21}$ in Fig. [13](#fig:maps_conversion_factors).

Next, we convert the inferred $\text{CO(1--0)}$ moment-0 map ($W_{\ensuremath{\text{CO(1--0)}}}$) into $\Sigma_{\text{mol}}$ by applying the prescription described by Equation 31 from (cite: Bolatto2013): $$\begin{equation}
    \left(\dfrac{\alpha_{\ensuremath{\text{CO(1--0)}}}}{\SI{}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}}\right) = 2.9\, \exp\left(\dfrac{0.4}{Z^{\prime}\,\Sigma_{\rm GMC}^{100}}\right) \left(\dfrac{\Sigma_{\rm total}}{\SI{100}{\Msun\per\square\parsec}}\right)^{-\gamma}
    \label{equ:aco}
\end{equation}$$ following the iterative approach presented in (cite: Sun2022). $Z^{\prime}$ is the local metallicity in units of Solar metallicities, and $\gamma$ is 0.5 if $\Sigma_{\rm total}>\SI{100}{\Msun\per\square\parsec}$ and 0 otherwise. The local metallicity is estimated from optical line measurements taken by MUSE applying a Gaussian Process Regression (GPR) to model the 2D metallicity distribution (cite: Williams2022).

Here, $\Sigma_{\rm GMC}^{100}$ is fixed at unity, i.e. we adopt a fiducial GMC surface density of 100  and the total surface density ($\Sigma_{\rm total}$) includes molecular gas (CO), atomic gas ($\text{H}\,{\tiny\text{I}}$, Sect. [7.2](#sec:appendix:hi)), and stellar mass (3.6 $\mu$ m, Sect. [7.3](#sec:appendix:mstar)). Since $\alpha_{\text{CO}}$ is implicitly needed to compute $\Sigma_{\rm total}$, Equation [\[equ:aco\]](#equ:aco) must be solved iteratively. We show a map of the adopted $\alpha_{\text{CO}}$ map in Fig. [13](#fig:maps_conversion_factors). The median $\alpha_{\text{CO}}$ value is $\SI{3.3}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$ and thus by a factor of 1.3 lower than the MW based $\alpha_{\text{CO}}$ listed above. For this galaxy, $\alpha_{\text{CO}}$ systematically decreases by a factor of $\sim 3$ from the disc over the spiral arms towards the centre of $\mathrm{NGC\,4321}$, with a scatter of 0.10. Overall, the inferred total $\text{H}_2$ mass of the varying $\alpha_{\text{CO}}$ across the FOV used in this work is $M_{\ensuremath{\text{H}_2}}=\SI{1.6e9}{\Msun}$, which is lower by a factor of 0.57 than the value obtained via a constant MW-based $\alpha_{\text{CO}}$, yielding $M_{\ensuremath{\text{H}_2}}=\SI{2.8e9}{\Msun}$.

We note that (cite: Teng2023) inferred cloud-scale $\alpha_{\text{CO}}$ values for the central 2 kpc of $\mathrm{NGC\,4321}$ using a multi-line modelling approach based on cloud-scale multi-line, multi-transition CO isotopologues. Despite the existing robust $\alpha_{\text{CO}}$ measurement, we employ the surface density-metallicity-based calibration from (cite: Bolatto2013) to obtain continuous $\alpha_{\text{CO}}$ values across the full disc of $\mathrm{NGC\,4321}$ and note that the measurements from (cite: Teng2023) are on average 0.20 smaller than the values used here, but consistent at the 1-sigma level within 0.21.

## Atomic gas – $\text{H}\,{\tiny\text{I}}$ 21-cm

We utilise $\text{H}\,{\tiny\text{I}}$ 21-cm line observations to measure the atomic gas surface density. The $\text{H}\,{\tiny\text{I}}$ data are from VLA observations associated with HERACLES (cite: Leroy2009) mapping several nearby galaxies in $\text{H}\,{\tiny\text{I}}$ at $\sim\ang{;;20}$ resolution. We convert the integrated intensity of $\text{H}\,{\tiny\text{I}}$($W_{\rm 21cm}$) into atomic gas surface density via (cite: Walter2008): $$\begin{equation}
   \left(\dfrac{\ensuremath{\Sigma_{\text{atom}}}}{\SI{}{\Msun\per\square\parsec}}\right) = \num{1.97e-2} \left(\dfrac{W_{\rm 21cm}}{\SI{}{\Kkms}}\right) \cos(i),
\end{equation}$$ where $\cos(i)$ is accounting for the inclination of the galaxy ($i=\SI{38.5}{\degree}$).

## Stellar mass – 3.6 μm

We use the stellar mass surface density map from (cite: Querejeta2015), who use 3.6 μm observations from the *Spitzer* Survey of Stellar Structure in Galaxies (cite: Sheth2010). The 3.6 μm maps are corrected for dust attenuation using an “Independent Component Analysis” (ICA) method that separates stars and dust on a pixel-to-pixel basis (for more details, see (cite: Querejeta2015)) We convert the attenuation-corrected 3.6 μm map into stellar mass surface density, $\Sigma_{\star}$, via: $$\begin{equation}
   \left(\dfrac{\ensuremath{\Sigma_{\star}}}{\SI{}{\Msun\per\square\parsec}}\right) = \num{4.22e2} \left(\dfrac{I_{\SI{3.6}{\ensuremath{\mu}m}}}{\SI{}{\mega\jansky\per\steradian}}\right) \,,
\end{equation}$$ which assumes a constant mass-to-light ratio of $0.6\,\SI{}{\Msun}/\SI{}{\Lsun}$ (cite: Meidt2014).

In App. [7.4](#sec:appendix:pde), we use the stellar mass volume density ($\rho_{\star}$) to compute the dynamical equilibrium pressure of the ISM in the galaxy disc. We estimate $\rho_{\star}$ from the stellar mass surface density, adopting the recipes used in (cite: Blitz2006; Leroy2008; Ostriker2010; Sun2020a): $$\begin{align}
    \ensuremath{\rho_{\star}}= \dfrac{\ensuremath{\Sigma_{\star}}}{4H_\star} = \dfrac{\ensuremath{\Sigma_{\star}}}{0.54\,R_\star}\,,
\end{align}$$ where $H_\star$ and $R_\star$ are the scale height and radial scale length of the stellar disc. Above equation assumes an isothermal density profile along the vertical direction (cite: vanderKruit1988) and a fixed stellar disc flattening ratio of $R_\star/H_\star=7.3$ (cite: Kregel2002). We adopt $R_\star=\SI{61.1}{\ensuremath{''}}\sim\SI{4.5}{\kilo\parsec}$ from the S$^4$G photometric decomposition analysis (cite: Salo2015).

## Dynamical equilibrium pressure

We compute the dynamical equilibrium pressure, or ISM pressure ($P_{\text{DE}}$) following the prescription by (cite: Sun2020a). $P_{\text{DE}}$ describes the pressure regulated by the mass content in the ISM disc and thus provides an important gauge of the local environment of molecular clouds. The distribution of stars and gas in a galaxy disc can approximately be described as isothermal fluids in a plane-parallel geometry. In this prescription the dynamical equilibrium pressure is composed of a pressure term created by the ISM due to the self-gravity of the ISM disc and a term due to the gravity of the stars (see e.g. (cite: Spitzer1942)), such that: $$\begin{align}
    \ensuremath{P_{\text{DE}}}= \dfrac{\pi G}{2} \ensuremath{\Sigma_{\text{gas}}}^2 + \ensuremath{\Sigma_{\text{gas}}}\sqrt{2G\ensuremath{\rho_{\star}}}\, \sigma_{\text{gas,z}} \; ,
    \label{EQU:PDE_large_app}
\end{align}$$ where we assume a smooth, single-fluid gas disc, and that all gas shares a similar velocity dispersion, so that $\ensuremath{\Sigma_{\text{gas}}}=\ensuremath{\Sigma_{\text{mol}}}+\ensuremath{\Sigma_{\text{atom}}}$ is the total gas surface density, $\rho_{\star}$ is the stellar mass volume density near disc midplane and $\sigma_{\text{gas,z}}$ is the velocity dispersion of the gas perpendicular to the disc.

(cite: Sun2020a) proposed a new formalism which takes into account the self-gravity of the molecular gas at high resolution, i.e. 100 scale. In this work, we adopt their formalism, which is described in the following. To combine the cloud-scale $\Sigma_{\text{mol, 120\,pc}}$ data with the large-scale $\Sigma_{\text{atom}}$ and $\rho_{\star}$, we split $P_{\text{DE}}$ into two parts: the pressure of the molecular gas at cloud-scale, $P_{\text{cloud}}$, and the pressure of the smooth extended atomic gas due to the gravity of all gas (atomic and molecular) and the stars, $P_{\text{atom}}$. The cloud-scale $P_{\text{cloud}}$ consists of three terms accounting for the self-gravity of the molecular gas, the gravity of larger molecular structures and the gravity of stars: $$\begin{align}
    \ensuremath{P_{\text{cloud}}}= & \dfrac{3\pi}{8}G\ensuremath{\Sigma_{\text{mol, 120\,pc}}}^2 + \dfrac{\pi}{2}G\ensuremath{\Sigma_{\text{mol, 120\,pc}}}\ensuremath{\Sigma_{\text{mol, 260\,pc}}}\nonumber\\ 
    & + \dfrac{3\pi}{4}G\ensuremath{\rho_{\star}}\ensuremath{\Sigma_{\text{mol, 120\,pc}}} D_{\text{beam}}\;,
    \label{EQU:Pcloud}
\end{align}$$ where $\rho_{\star}$ is computed as described in App. [7.3](#sec:appendix:mstar). In Equ. [\[EQU:Pcloud\]](#EQU:Pcloud), $\Sigma_{\text{mol, 120\,pc}}$ is given at the cloud-scale resolution (here 120) while $\Sigma_{\text{mol, 260\,pc}}$ and $\rho_{\star}$ describe the distributions of the molecular gas and the stellar mass density at 260 scale. In typical units, Equ. [\[EQU:Pcloud\]](#EQU:Pcloud) reads: $$\begin{align}
    &\left(\dfrac{\ensuremath{P_{\text{cloud}}}}{\SI{}{\kB\kelvin\per\cubic\centi\metre}}\right) = \num{2.48e5}\left(\dfrac{\ensuremath{\Sigma_{\text{mol, 120\,pc}}}}{\SI{e2}{\Msun\per\square\parsec}}\right)^2 \\
    &\quad + \;\num{3.31e5}\left(\dfrac{\ensuremath{\Sigma_{\text{mol, 120\,pc}}}}{\SI{e2}{\Msun\per\square\parsec}}\right)\left(\dfrac{\ensuremath{\Sigma_{\text{mol, 260\,pc}}}}{\SI{e2}{\Msun\per\square\parsec}}\right) \nonumber\\
    &\quad + \;\num{7.01e4}\left(\dfrac{\ensuremath{\Sigma_{\text{mol, 120\,pc}}}}{\SI{e2}{\Msun\per\square\parsec}}\right)\left(\dfrac{\ensuremath{\rho_{\star}}}{\SI{e-1}{\Msun\per\cubic\parsec}}\right)\left(\dfrac{D_{\text{beam}}}{\SI{150}{\parsec}}\right)\nonumber\;,
\end{align}$$

The large-scale $P_{\text{atom}}$ includes the self-gravity of the atomic gas and the gravitational interaction of the atomic gas with the (large-scale) molecular gas and the stars: $$\begin{align}
    \ensuremath{P_{\text{atom}}}= \dfrac{\pi G}{2}\ensuremath{\Sigma_{\text{atom}}}^2 + \pi G \ensuremath{\Sigma_{\text{atom}}}\ensuremath{\Sigma_{\text{mol, 260\,pc}}}+ \ensuremath{\Sigma_{\text{atom}}}\sqrt{2G\ensuremath{\rho_{\star}}}\,\sigma_{\text{atom}}\;,
    \label{EQU:Patom}
\end{align}$$ where $\sigma_{\text{atom}}$ is the velocity dispersion of the atomic gas which is fixed at $\sigma_{\text{atom}}=\SI{10}{\kilo\metre\per\second}$. In Equ. [\[EQU:Patom\]](#EQU:Patom) all quantities are convolved to the large-scale resolution. Converting to typical units we obtain: $$\begin{align}
    &\left(\dfrac{\ensuremath{P_{\text{atom}}}}{\SI{}{\kB\kelvin\per\cubic\centi\metre}}\right) = \num{3.31e5}\left(\dfrac{\ensuremath{\Sigma_{\text{atom}}}}{\SI{e2}{\Msun\per\square\parsec}}\right)^2 \\
    &\quad + \;\num{6.62e5}\left(\dfrac{\ensuremath{\Sigma_{\text{atom}}}}{\SI{e2}{\Msun\per\square\parsec}}\right)\left(\dfrac{\ensuremath{\Sigma_{\text{mol, 260\,pc}}}}{\SI{e2}{\Msun\per\square\parsec}}\right) \nonumber\\
    &\quad + \;\num{1.02e5}\left(\dfrac{\ensuremath{\Sigma_{\text{atom}}}}{\SI{e2}{\Msun\per\square\parsec}}\right)\left(\dfrac{\ensuremath{\rho_{\star}}}{\SI{e-1}{\Msun\per\cubic\parsec}}\right)^{1/2}\nonumber\;,
\end{align}$$ Finally, we compute the intensity-weighted average, $\langle P_{\rm cloud,\,120\,pc}\rangle_{\rm 260\,pc}$, at the large-scale to combine the molecular gas weight with the large-scale $P_{\text{atom}}$ pixel by pixel: $$\begin{align}
    \langle P_{\rm DE,\,120\,pc}\rangle_{\rm 260\,pc} = \langle P_{\rm cloud,\,120\,pc}\rangle_{\rm 260\,pc} + \ensuremath{P_{\text{atom}}}
\end{align}$$

![](Figures/ngc4321_SFEdense_sfr_tracers_compressed.pdf)

![](Figures/ngc4321_HCN_ratios_vs_cloud_props_weighted_avg_ACO_B13_MUSEGPR_compressed.pdf)

![](Figures/ngc4321_HCN_ratios_vs_stars_envir_mask_ACO_B13_MUSEGPR_compressed.pdf)

![](Figures/ngc4321_maps_conversion_factors_compressed.pdf)

![](Figures/ngc4321_map_pressure_threshold_compressed.pdf)

![](Figures/ngc4321_HCN_ratios_vs_metallicity_compressed.pdf)

![](Figures/ngc4321_maps_data_products_compressed.pdf)

![](Figures/ngc4321_stacked_spectra_radius_compressed_v3.pdf)

![](Figures/ngc4321_stacked_spectra_pressure_compressed.pdf)

![](Figures/ngc4321_stacked_spectra_Sigmol_compressed.pdf)

+-------------------------------------+---------------+----------------------------------------+----------------+--------------+-------------+---------+
| x-axis                              | y-axis        | Regime                                 | Slope (stacks) | Slope (los)  | Corr. ($p$) | Scatter |
+:===================================:+:=============:+:======================================:+:==============:+:============:+:===========:+:=======:+
| $\langle\Sigma_{\text{mol}}\rangle$ | HCN/CO(2$-$1) |                                        | 0.58           | 0.40 (0.04)  | 0.43 (0.0)  | 0.25    |
|                                     +---------------+----------------------------------------+----------------+--------------+-------------+---------+
|                                     | SFR/HCN       | $\leq\SI{74}{\Msun\per\square\parsec}$ | 0.00           | -0.75 (0.13) | -0.30 (0.0) | 0.60    |
|                                     |               +----------------------------------------+----------------+--------------+-------------+---------+
|                                     |               | $>\SI{74}{\Msun\per\square\parsec}$    | -1.33          | -2.30 (0.45) | -0.53 (0.0) | 0.39    |
+-------------------------------------+---------------+----------------------------------------+----------------+--------------+-------------+---------+
| $\langle\sigma_{\text{mol}}\rangle$ | HCN/CO(2$-$1) |                                        | 0.81           | 0.51 (0.04)  | 0.57 (0.0)  | 0.23    |
|                                     +---------------+----------------------------------------+----------------+--------------+-------------+---------+
|                                     | SFR/HCN       | $\leq\SI{8.3}{\kilo\metre\per\second}$ | 0.00           | -1.05 (0.26) | -0.27 (0.0) | 0.52    |
|                                     |               +----------------------------------------+----------------+--------------+-------------+---------+
|                                     |               | $>\SI{8.3}{\kilo\metre\per\second}$    | -2.29          | -1.58 (0.16) | -0.60 (0.0) | 0.37    |
+-------------------------------------+---------------+----------------------------------------+----------------+--------------+-------------+---------+
| $\langle\alpha_{\text{vir}}\rangle$ | HCN/CO(2$-$1) |                                        | 0.65           | 0.46 (0.03)  | 0.52 (0.0)  | 0.21    |
|                                     +---------------+----------------------------------------+----------------+--------------+-------------+---------+
|                                     | SFR/HCN       |                                        | -0.84          | -1.11 (0.07) | -0.55 (0.0) | 0.44    |
+-------------------------------------+---------------+----------------------------------------+----------------+--------------+-------------+---------+
| $\Sigma_{\star}$                    | HCN/CO(2$-$1) |                                        | 0.52           | 0.44 (0.03)  | 0.57 (0.0)  | 0.19    |
|                                     +---------------+----------------------------------------+----------------+--------------+-------------+---------+
|                                     | SFR/HCN       |                                        | -0.73          | -1.02 (0.06) | -0.50 (0.0) | 0.46    |
+-------------------------------------+---------------+----------------------------------------+----------------+--------------+-------------+---------+

**Notes** – Linear regression parameters for the respective relations and $x$-axis regimes presented in Fig. [12](#fig:hcn_ratios_vs_stars) and [11](#fig:hcn_ratios_vs_cloud_props) analogous to Tab. [\[tab:fit_parameters\]](#tab:fit_parameters). The slopes of the binned relations (column 4) are either determined by `MARS` if two distinct regimes with different linear regression behaviour have been found, or computed with `LinMix` if the relation is well described with a single line according to the `MARS` algorithm.

# Spectral stacking

We compute spectral stacks using the `python` package `PyStacker`[^8] presented in (cite: Neumann2023b). `PyStacker` uses a high-significance prior (here $\text{CO(2--1)}$) to determine the velocity field of the line emission. It then uses this velocity information to shift the spectra of various line to correct for the Doppler shift, assuming all lines share the same velocity field. Afterwards, we average the shuffled spectra over larger regions usually resulting in higher-significance detections. Here, we stack the emission of $\text{CO(2--1)}$(from PHANGS–ALMA) and $\text{HCN(1--0)}$(this work) via morphological environment (Fig. [4](#fig:stacks_envir)), galactocentric radius, $r_{\rm gal}$(Fig. [17](#fig:stacks_radius)), dynamical equilibrium pressure, $\langle P_{\text{DE}}\rangle$(Fig. [18](#fig:stacks_pressure)), molecular gas surface density (Fig. [19](#fig:stacks_sigmol)), $\Sigma_{\text{mol}}$, stellar mass surface density, $\Sigma_{\star}$, and molecular cloud properties, $\langle\Sigma_{\text{mol}}\rangle$, $\langle\sigma_{\text{mol}}\rangle$, $\langle\alpha_{\text{vir}}\rangle$. We use these averaged spectra to compute integrated intensities, where the velocity-integration window is inferred based on the average $\text{CO(2--1)}$ spectrum using the same masking method as described in Sect. [3.1](#sec:methods:mom0_maps). We note that the spectral stacks agree within $\pm \SI{10}{\percent}$ with binned integrated intensities computed within the same stacking bins if $\text{CO(2--1)}$ is used as a prior to define the velocity-integration mask.

# SFR tracers

## SFR – 21 $\mu$ m

We use 21 $\mu$ m (F2100W) emission from recent JWST–MIRI (cite: jwst-mission; miri-paper) observations as a another probe of SFR, in addition to $\text{H}\alpha$ from PHANGS–MUSE (Sect. [3.4](#sec:methods:sfr_halpha)) and 33 GHz from VLA (Sect. [9.2](#sec:appendix:sfr_33ghz)). These data are part of the “PHANGS–JWST Treasury Program” (cite: Lee2023) and have been reduced via the PHANGS–JWST data reduction pipeline (Williams et al. in prep.). $\mathrm{NGC\,4321}$ was observed by JWST in June 2023 and we use version 0.9 of the PHANGS–JWST data reduction.

Physically, the strong radiation field from young, massive stars heat up the surrounding dust, which re-emits at infrared wavelength probed by F2100W. 21 $\mu$ m point sources correlate well with $\text{H}\,{\tiny\text{II}}$ regions (cite: Hassani2023) and the F2100W intensity correlates well, though non-linearly, with extinction-corrected $\text{H}\alpha$ intensity (cite: Leroy2023; Belfiore2023). However, the F2100W also captures stochastically heated emission from small dust grains that can trace the ISM. It may thus be both more robust to extinction than $\text{H}\alpha$ and more subject to contamination by diffuse ISM emission.

To infer $\Sigma_{\text{SFR}}$ from F2100, we use the empirical relation from (cite: Leroy2023) (their equation 5), which re-scales the 21 $\mu$ m flux into a 24 $\mu$ m flux using $R_{\SI{21}{\ensuremath{\mu}m}/\SI{24}{\ensuremath{\mu}m}}=0.80$ and then converts to SFR via a linear conversion (cite: Kennicutt2012), such that the SFR surface density is given by: $$\begin{equation}
    \left(\dfrac{\Sigma_{\rm SFR, F2100W}}{\SI{}{\Msun\per\year\per\square\kilo\parsec}}\right) = \num{3.7e-3} \left( \dfrac{I_{\nu, \rm{F2100W}}}{\SI{}{\erg\per\second\per\square\centi\metre\per\steradian}} \right)\cos(i) \;,
    \label{equ:sfr_21um_lin}
\end{equation}$$ Thus, we adopt a linear relation between F2100W dust emission and the SFR. We also contrast this prescription to a power law relation based on (cite: Leroy2023) which leads to up to a factor of three higher values in the central $\sim\SI{2}{\kilo\parsec}$ of $\mathrm{NGC\,4321}$.

## SFR – 33 GHz

We note that above SFR tracers might lead to significantly discrepant results in galaxy centres, where optical recombination lines can become too extinct to recover robust Balmer decrement corrections and 21 $\mu$ m emission might be systematically contaminated by stochastically heated dust grain. Therefore, we use free-free 33 GHz emission from as an additional SFR tracer in the centre of $\mathrm{NGC\,4321}$. The data are coming from Very Large Array (VLA) observations of a large sample of galaxies, including $\mathrm{NGC\,4321}$, at 3 GHz–33 GHz at $\sim\ang{;;2}$ resolution (cite: Linden2020).

At high radio frequencies the ionising flux of young massive stars is directly proportional to the thermal spectral luminosity. This allows us to trace the SFR via the thermal part of the 33 GHz flux measured by the VLA following the prescription in (cite: Murphy2012) (their equation 6): $$\begin{align}
    \left(\dfrac{\Sigma_{\rm SFR,\SI{33}{\giga\hertz}}}{\SI{}{\Msun\per\year\per\square\kilo\parsec}}\right) = & \, \num{5.5e16} \, \left( \dfrac{T_{\rm e}}{\SI{e4}{\kelvin}} \right)^{-0.45} \left( \dfrac{\nu}{\SI{}{\giga\hertz}} \right)^{0.1} \, f_{\rm thermal} \nonumber\\ 
    & \times \left( \dfrac{I_{\nu,\SI{33}{\giga\hertz}}}{\SI{}{\erg\per\second\per\square\centi\metre\per\steradian}} \right) \,\cos(i) \;,
    \label{equ:sfr_33ghz}
\end{align}$$ where the thermal fraction ($f_{\rm thermal}$) values are taken from (cite: Linden2020) (their table 4; $\sim\SI{200}{\parsec}$ apertures) and we adopt an electron temperature of $T_{\rm e}=\SI{e4}{\kelvin}$ and $\nu=\SI{33}{\giga\hertz}$.

## SFR tracer comparison

Throughout this work, we have used Balmer decrement-corrected $\text{H}\alpha$ emission as a tracer of SFR (Sect. [3.4](#sec:methods:sfr_halpha)). Despite being overall a robust tracer of SFR, when corrected for dust attenuation, in the centres of galaxies, $\text{H}\alpha$ might miss some of the SFR-related $\text{H}\alpha$ emission due to extremely high attenuation by denser dust thus biasing the SFR estimate high. Also, in extreme environments, like the centre, $\text{H}\alpha$ emission might be associated with other processes than young stars and thus bias the SFR high. Therefore, the question is: “How robust are our findings against the choice of the SFR tracer?”

We use JWST F2100W emission to trace SFR via the hot dust emission that is less affected by attenuation effects in the centre of the galaxy as long as these galaxy centres contain sufficient amounts of dust (Sect. [9.1](#sec:appendix:sfr_21mu)). Using the F2100W-inferred SFR (instead of $\text{H}\alpha$) leads to similar SFR/HCN values across the disc and in the low-pressure regime for both prescriptions (linear and power-law conversion) adopted here (see Fig. [10](#fig:hcn_ratios_sfr_tracers). However, the two calibrations differ by up to a factor of three in the central kpc of the galaxy. The change is so severe that using the power-law calibration yields similar SFR$_{\rm F2100W}$/HCN values in the centre (median $10^{-1.05}$) as in bar ends (median $10^{-0.96}$), spiral arms (median $10^{-1.06}$) and interarm (median $10^{-1.19}$), and statistically the same SFR$_{\rm F2100W}$/HCN distribution in the centre compared to the aforementioned environments.

In addition, we compare the two SFR tracers ($\text{H}\alpha$ and F2100W) with the 33 GHz-inferred values, being the most robust tracer of the SFR in the centre of $\mathrm{NGC\,4321}$(Sect. [9.2](#sec:appendix:sfr_33ghz)). We find that $\text{H}\alpha$(decrement-corrected) and 33 GHz yield very consistent results across the whole central 1   probed by 33 GHz emission, agreeing within 20 %. F2100W (linear conversion) leads to a factor of two higher values in the central 260, but otherwise consistent values. Therefore, we conclude that for $\mathrm{NGC\,4321}$ Balmer decrement-corrected $\text{H}\alpha$ emission is an excellent tracer of the SFR, even in the centre of the galaxy, where increased dust attenuation could have depreciated $\text{H}\alpha$ as a robust SFR tracer. Moreover, these results suggest that F2100W is proportional to the SFR across the full disc of $\mathrm{NGC\,4321}$.

# Scaling relations

## Molecular cloud relations

In Fig. [11](#fig:hcn_ratios_vs_cloud_props), we present the relations between HCN/CO and SFR/HCN, respectively with the properties of molecular gas at GMC scales, i.e. here, at 120. The cloud-scale molecular gas properties are computed following the prescriptions of (cite: Sun2018) and (cite: Neumann2023a), but adopting the varying $\alpha_{\text{CO}}$ and $R_{21}$ conversions introduced in Sect. [7.1.2](#sec:methods:sigmol_varying_aco). We compute the molecular gas surface density from the $\text{CO(2--1)}$ integrated intensity ($W_{\text{CO(2--1)}}$): $$\begin{align}
    \ensuremath{\Sigma_{\text{mol}}}= \ensuremath{\alpha_{\text{CO}}}\, R_{21}^{-1} \, \ensuremath{W_{\text{CO(2--1)}}}\,.
\end{align}$$ The molecular gas velocity dispersion is obtained from the $\text{CO(2--1)}$ equivalent line width and corrected for the velocity channel-to-channel correlation: $$\begin{align}
    & \sigma_{\rm measured} = \dfrac{\ensuremath{W_{\text{CO(2--1)}}}}{\sqrt{2\pi}T_{\rm peak}} \,,\\
    & \ensuremath{\sigma_{\text{mol}}}= \sqrt{\sigma_{\rm measured}^2 + \sigma_{\rm response}^2} \,,
\end{align}$$ where $\sigma_{\rm measured}$ assumes a Gaussian line profile and $\sigma_{\rm response}$ takes into account the instrument channel width and channel-to-channel correlation. To estimate the virial parameter ($\alpha_{\text{vir}}$), we assume spherically symmetric clouds with a given density profile $\rho\propto r^{-1}$, so that $\alpha_{\text{vir}}$ can be computed from the $\text{CO(2--1)}$ data using $\Sigma_{\text{mol}}$ and $\sigma_{\text{mol}}$: $$\begin{align}
    \ensuremath{\alpha_{\text{vir}}}= \dfrac{9\,\ln{2}}{\pi\,G} \dfrac{\ensuremath{\sigma_{\text{mol}}}^2}{\ensuremath{\Sigma_{\text{mol}}}\,D_{\rm beam}} \propto \dfrac{\ensuremath{\sigma_{\text{mol}}}^2}{\ensuremath{\Sigma_{\text{mol}}}}\,,
\end{align}$$ where $G$ is the gravitational constant. These molecular gas properties are computed at $D_{\rm beam} =\SI{120}{\parsec}$ scale and converted to the HCN resolution, i.e. 260, via a $\Sigma_{\text{mol}}$-weighted average, similar to $P_{\text{DE}}$ as described in Sect. [3.6](#sec:methods:pde), hence the notation $\langle X_{\SI{120}{\parsec}}\rangle_{\SI{260}{\parsec}}$, where $X$ is the quantity to by averaged.

Similar to the relations with radius (Sect. [4.2](#sec:results:radius)) and pressure (Sect. [4.3](#sec:results:pressure)), we apply the MARS linear regression tool (Sect. [3.8](#sec:methods:fitting)) to the cloud property relations shown in Fig. [11](#fig:hcn_ratios_vs_cloud_props). We find that HCN/CO correlated positively and with $\Sigma_{\text{mol}}$, $\sigma_{\text{mol}}$ and $\alpha_{\text{vir}}$ and is well-described by a single power law over the whole data range that is probed. Similarly, we observe a negative correlation between SFR/HCN and $\Sigma_{\text{mol}}$, $\sigma_{\text{mol}}$, $\alpha_{\text{vir}}$. However, for SFR/HCN vs $\Sigma_{\text{mol}}$ and $\sigma_{\text{mol}}$ we find a change in the relation (as determined via MARS) at $\ensuremath{\Sigma_{\text{mol}}}=\SI{74}{\Msun\per\square\parsec}$ and $\ensuremath{\sigma_{\text{mol}}}=\SI{8.3}{\km\per\second}$, such that SFR/HCN is roughly constant at low $\Sigma_{\text{mol}}$($\sigma_{\text{mol}}$) and strongly decreasing with increasing $\Sigma_{\text{mol}}$($\sigma_{\text{mol}}$) at high $\Sigma_{\text{mol}}$($\sigma_{\text{mol}}$).

## Stellar mass relations

Fig. [12](#fig:hcn_ratios_vs_stars) shows the HCN/CO and SFR/HCN scaling relation with the stellar mass surface density, $\Sigma_{\star}$. We compute $\Sigma_{\star}$ from the *Spitzer* 3.6 $\mu$ m image as described in Sect. [7.3](#sec:appendix:mstar). Following the same methodology as in Sect. [4.2](#sec:results:radius),  [4.3](#sec:results:pressure),  [10.1](#sec:appendix:cloud_relations), we determine the power law behaviour of the mean trend finding strong correlations between HCN/CO (positive correlation) and SFR/HCN (negative correlation) with $\Sigma_{\star}$. For HCN/CO vs. $\Sigma_{\star}$, we observe a tighter relation (0.19 scatter) that is consistent over all environments and the whole probed data range, spanning two orders of magnitude in stellar mass surface density ($\SI{1e2}{\Msun\per\square\parsec}$ to $\SI{1e4}{\Msun\per\square\parsec}$). The found relation shows that $\Sigma_{\star}$ is a good predictor of HCN/CO over the whole disc of a nearby galaxy at sub-kpc scales, though most of the dynamic range of $\Sigma_{\star}$ is covered by only two regions, the centre and the bar. The relation between SFR/HCN and $\Sigma_{\star}$ shows much higher scatter (0.46) with the bar region being offset to the main relation by 0.2, stressing the strongly suppressed star formation efficiency in the bar (Sect. [5.3](#sec:discussion:bar)). Combined with the results presented in Sect. [10.1](#sec:appendix:cloud_relations), the found relations suggest that the threshold behaviour in the SFR/HCN vs $P_{\text{DE}}$ relation (Sect. [4.3](#sec:results:pressure)) is caused by molecular gas cloud-scale physics rather than larger scale environment.

# Additional figures

Fig. [13](#fig:maps_conversion_factors) shows the $\text{CO(2--1)}$-to-$\text{CO(1--0)}$ line ratio ($R_{\rm 21}$) computed from the $\SI{4}{\ensuremath{''}}\sim\SI{300}{\parsec}$ resolution $\text{CO(1--0)}$ data from (cite: Pan2017) and homogenised $\text{CO(2--1)}$ observations form PHANGS–ALMA (cite: Leroy2021b). We use the measured 300-scale $R_{\rm 21}$ map to infer the cloud-scale (120) $\text{CO(1--0)}$ line intensities from the observed $\text{CO(2--1)}$ line intensities, which enter the estimation of the dynamical equilibrium pressure (Sect. [3.6](#sec:methods:pde)). In Sect. [4.5](#sec:discussion:hcn_co), we use the $R_{\rm 21}$ map to convert the 260-scale $W_\ensuremath{\text{CO(2--1)}}$ into $W_\ensuremath{\text{CO(1--0)}}$ to compare the HCN-to-$\text{CO(1--0)}$ vs. $\Sigma_{\text{mol}}$ scaling relation with literature findings.

In Fig. [14](#fig:maps_pressure_contours), we show a map of the morphological environments overlaid with HCN contours similar to Fig. [3](#fig:hcn_ratio_maps), right panel. In addition, we indicate two loci of ISM pressure, $P_{\text{DE}}$, matching the pressure thresholds inferred for the HCN/CO and SFR/HCN vs $P_{\text{DE}}$ scaling relations (Sect. [4.3](#sec:results:pressure)).

Fig. [15](#fig:metallicity_trends) presents HCN/CO and HCN/HCO$^+$ line ratio trends with metallicity. Detected sigh line measurements of HCN/CO show no correlation with metallcity ($\rho_{\rm Pearson}=0.12$). The stacked average HCN/CO increases with metallicity, suggesting that the HCN abundance is more strongly depending on metallicity than CO, which is expected if nitrogen decreases more sharply with metallicity than oxygen (cite: Braine2017; Braine2023). In this scenario we would expect a systematic increase of the HCN/HCO$^+$ line ratio with metallicity. However, we find only a weak correlation between HCN/HCO$^+$ and metallicity ($\rho=0.35$), indicating that metallicity effect play only a minor role across $\mathrm{NGC\,4321}$, potentially due to the small dynamic range in metallicity, spanning less than 0.1 (8.54 to 8.62).

In Fig. [16](#fig:data_products_maps), we display maps of various data products surface density maps of the atomic gas, (dense) molecular gas and stellar mas, ISM pressure and SFR inferred from $\text{H}\alpha$ and 21 $\mu$ m, respectively. In addition, we show the star formation efficiency of the molecular gas, SFR/CO.

[^1]: [ ](https://orcid.org/lukas.neumann.astro@gmail.com)

[^2]: Member of the International Max Planck Research School (IMPRS) for Astronomy and Astrophysics at the Universities of Bonn and Cologne.

[^3]: We do not use the archival $\text{CO(1--0)}$ observations as a tracer of molecular gas because of their poorer angular resolution (4″, corresponding to $\sim 300$ pc), but we do use them to inform our conversion of $\text{CO(2--1)}$ intensity to molecular gas surface density, as described later in Sect. [3.2](#sec:methods:sigmol).

[^4]: Note that many previous works (cite: Gao2004) use a slightly smaller value of $\ensuremath{\alpha_{\text{HCN}}}=\SI{10}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$ tracing gas above $n_{{\rm H}_2}\approx\SI{3e4}{\per\cubic\centi\metre}$. However, choosing a different (constant) $\alpha_{\text{HCN}}$ has no qualitative effect on our results.

[^5]: <https://github.com/PhangsTeam/PyStacker>

[^6]: <https://linmix.readthedocs.io/en/latest/index.html>; `LinMix` is a Bayesian inference tool to linear regression, which can take into account upper limits and infers the posterior distribution of the fit line parameters via MCMC simulation (cite: Kelly2007).

[^7]: <https://cran.r-project.org/package=earth>

[^8]: <https://github.com/PhangsTeam/PyStacker>

</paper>

Write the methods card for this paper.