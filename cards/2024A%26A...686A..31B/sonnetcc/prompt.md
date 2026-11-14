# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...686A..31B\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...686A..31B",
 "title": "Molecular isotopologue measurements toward super star clusters and the relation to their ages in NGC 253 with ALCHEMI",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Butterworth, J.",
 "n_authors": 21,
 "arxiv_id": "2402.10721",
 "doi": "10.1051/0004-6361/202348787",
 "alma_projects_linked_by_archive": [
  "2017.1.00161.L",
  "2018.1.00162.S"
 ]
}
```

Paper text:
<paper>
# Molecular isotopologue measurements toward super star clusters and the relation to their ages in NGC 253 with ALCHEMI

Determining the evolution of the CNO isotopes in the interstellar medium (ISM) of starburst galaxies can yield important constraints on the ages of superstar clusters (SSCs), or on other aspects and contributing factors of their evolution, such as the Initial Mass Function. Due to the time-dependent nature of the abundances of isotopes within the ISM as they are supplied from processes such as nucleosynthesis or chemical fractionation, this provides the possible opportunity to probe the ability of isotopes ratios to trace the ages of high star forming regions, such as SSCs.

The goal of this study is to investigate whether the isotopic variations in SSC regions within NGC 253 are correlated with their different ages as derived from stellar population modelling.

We have measured abundance ratios of CO, HCN and HCO$^{+}$ isotopologues in six regions containing SSCs within NGC 253 using high spatial resolution (1.6",$\sim 28$pc) data from the ALCHEMI (ALma Comprehensive High-resolution Extragalactic Molecular Inventory) ALMA Large program. We have then analysed these ratios using `RADEX` radiative transfer modelling, with the parameter space sampled using the nested sampling Monte Carlo algorithm MLFriends. These abundance ratios were then compared to ages predicted in each region via the fitting of observed star formation tracers (such as Br$\gamma$) to `Starburst99` starburst stellar population evolution models.

Through the use of non-LTE radiative transfer modelling, the isotopic column density ratios across multiple regions of SSC activity in NGC 253 are determined. We do not find any significant trend with age for the CO and HCN isotopologue ratios on the timescales for the ages of the SSC\* regions observed. HCO$^{+}$ may show a correlation with age over these timescales, in $^{12}$C/$^{13}$C.

The driving factors of these ratios within SSCs could be the Initial Mass Function as well as possibly fractionation effects. To further probe these effects in SSCs over time a larger sample of SSCs must be observed spanning a larger age range.

# Introduction

Starburst galaxies are characterized by vigorous star formation activity; this can lead to the emergence of super star clusters (SSCs). SSCs are typically quite young ($<10$ Myr) and have been observed within our Galaxy, with masses of $\sim10^4$ M$_\odot$ (cite: Ginsburg_2018). Even more massive ($\sim10^5$ M$_\odot$) clusters have been observed in starburst regions of nearby galaxies, such as NGC 4945 and NGC 253 (cite: 2018Leroy; Emig_2020; 2020_Rico-Villas; 2022_Rico_villas).

SSCs, as compact ($\sim$2-3 pc) regions of high star formation rate (up to 5 M$_\odot$ yr^-1^ ), serve as ideal laboratories to explore the processes that may influence and transform the interstellar medium (ISM), in particular, the variation of the isotope ratios of carbon (C), nitrogen (N), and oxygen (O). These atoms and their isotopes are important due to their high abundances and potential to probe stellar nucleosynthesis. This is due to the differing processes under which they typically form: $^{12}$C for example is believed to be primarily formed in Helium burning of both low- and high-mass stars. $^{13}$C on the other hand is believed to form in the CNO cycle of asymptotic giant branch (AGB) stars (cite: 1997Pagal). Both $^{14}$N and $^{15}$N are thought to be produced during the CNO cycles of massive stars and in the so-called hot bottom burning of asymptotic giant branch (AGB) stars with a higher proportion of both $^{14}$N and $^{15}$N formed in intermediate-mass stars relative to massive stars, $^{15}$N is also largely produced by novae (cite: Izzard_2004; Romano2017; 2019_Romano; 2022_Colzi). $^{16}$O and $^{18}$O are believed to be products of the helium burning phase of high-mass stars (with $^{18}$O, primarily formed in metal-rich stars) and $^{17}$O is formed as a product during the CNO cycle of intermediate mass stars ((cite: 2008Wouterloot; 2010Wiescher; 2014Henkel; Romano_Review_2022). As such the abundances of these isotopes and their evolution with time in a star-forming region are greatly affected by the initial conditions of star formation, such as the initial mass function (IMF) (cite: Papadopoulos_2010; Papadopoulos_2011).

Through the lens of sub-mm measurements these isotopic variations are traced primarily via the observations of isotopologues (isotope-bearing molecules). Thanks to the Atacama Large Millimeter Array (ALMA), it is possible to observe compact energetic sources, such as SSCs, on a resolvable scale in the starburst regions within nearby galaxies. Within the sub-mm regime probed by ALMA there are multiple rotational transitions of CNO bearing isotopologues available (e.g. CO, HCN, HCO$^{+}$). Observations of these isotopologues within the star-forming regions of galaxies (e.g. SSCs) can inform us also on the IMF (cite: Romano2017; Romano_Review_2022). For example, (cite: Romano2017) found that C, N and O isotope ratios imply a Top-Heavy IMF in nearby star-forming galaxies. Galaxies with a high star formation rate, such as starbursts, have been shown to possess a higher isotopic ratio of $^{12}$C/$^{13}$C than more ‘normal’ galaxies such as the Milky Way. Chemical fractionation can also influence the observed isotopologue ratios (cite: 2015Roueff; 2018_Colzi; 2019Viti; 2020Viti; 2020_Colzi; 2022_Colzi). For instance, the presence of certain exothermic chemical reactions in the gas phase of the ISM, under which isotopes are exchanged, may lead to chemical fractionation whereby the enhancement of certain isotopologues is favored over others (cite: 1984Langer; Szucs2014; 2019Loison; 2019Martin).

CO, HCN, HCO$^{+}$ and their isotopologues have been used as tools to investigate the $^{12}$C/$^{13}$C ratio in nearby galaxies (cite: 2004Pasquali; Jiang2011; GonzalezAlfonso2012; 2013Sliwa; 2014Sliwa; 2014Henkel; 2019Martin; 2019_Tang; Martin_ALCHEMI_2021) as well as in higher redshift galaxies (z $\leq 2.5$) (cite: Muller2006; Danielson_2013; 2014Spilker; Wallstrom2016). Meanwhile, $^{14}$N/$^{15}$N has been investigated through the use of HCN and its HC$^{15}$N isotopologue in extra-galactic sources (cite: 1998Henkel; 2018Henkel; 1999Chin; 2009Wang; 2014Wang; 2016Wang; Jiang2011; Martin_ALCHEMI_2021) and $^{16}$O/ $^{18}$O has been investigated towards individual Giant Molecular Clouds (GMCs) previously in NGC 253 using isotopologues of CO (cite: Meier_2015).

In this work we conduct a study to see whether the observed isotope ratios in starburst regions are determined by age or whether other mechanisms drive the variations in isotope ratio, such as proposed in (cite: Romano2017). In order to accomplish this, we present ALMA multi-transition observations of CO, HCN, and HCO$^{+}$ and their $^{13}$C, $^{15}$N, $^{17}$O and $^{18}$O isotopologues towards the starburst galaxy NGC 253. These measurements have been extracted from the ALMA large program imaging of the NGC 253 Central Molecular Zone (CMZ), "ALMA Comprehensive High-resolution Extragalactic Molecular Inventory", (cite: Martin_ALCHEMI_2021).

NGC 253 is a nearby (cite: Rekola+2005) galaxy containing a nuclear starburst (Star Formation Rate, SFR $\sim 2$M$_{\rm \odot}$ yr$^{-1}$, see (cite: Leroy2015)), which accounts for $\sim 50\%$ of the galaxy’s total star-forming activity. A previous study by (cite: 2018Leroy) has identified 14 SSCs located within the Central Molecular Zone (CMZ) of NGC 253. These clusters were estimated to have masses of $\sim$10$^5$ M$_{\rm \odot}$ with an upper limit to their ages of $<$10 Myr.

The broad frequency range of ALCHEMI allows for a systematic study of both the physical and chemical properties of NGC 253 as viewed through molecular observations. Other studies, made possible thanks to the ALCHEMI data, include: constraining the high cosmic-ray ionization rate (CRIR) nature of the galaxy (cite: Holdship+2021_SpectralRadex; Holdship+2022; Harada+2021; 2022_Behrens), the first detection of a phosphorus-bearing molecule in extragalactic sources (cite: Haasler+2022), the identification of new methanol maser transitions (cite: Humire+2022), the use of HOCO^+^ as a chemical tracer of CO$_2$ (cite: Harada+2022), and also the ability to reconstruct the shock history of the giant molecular clouds located within the CMZ of the galaxy (cite: Huang2023).

Alongside ALMA observations of the isotopologues of CO, HCN and HCO$^{+}$, the H39$\alpha$ emission was extracted from the ALCHEMI data in order to estimate the ionizing photon rate with a method consistent to that of (cite: Emig_2020). By combining these ionizing photon rates with other tracers of high star formation such as the Brackett Gamma (Br$\gamma$) line (cite: 2020_Pasha), the ages of star-forming populations can be approximated using stellar population evolution modelling (e.g., `Starburst99`, (cite: Starburst99_1999; Starburst99_2014)). Br$\gamma$ is, as a near-infrared hydrogen recombination line, primarily emitted in regions ionized by massive stars (O-, B-type stars). Br$\gamma$ also possesses relatively low dust attenuation ($\sim14\%$) making it an extremely potent tracer of the age of star-forming regions. We use observations on Br$\gamma$ taken with the SINFONI near-infrared (1.1-2.45 $\mu$m) integral field spectrograph installed on the Very Large Telescope (VLT) (cite: SINFONI_1; SINFONI_2).

This paper is structured as follows: in Section [2](#sec:Obs), we present an overview of the ALCHEMI data used alongside the data from SINFONI. Section [3.1](#subsec:CubeLineMoment) covers the methods under which the spectral lines were extracted and the moment maps were produced. In Section [4.1](#sec:LTE) we present an initial LTE analysis of the isotopologues. This is followed by a Non-LTE Large Velocity Gradient (LVG) modelling in order to determine the physical conditions within each SSC in Section [4.2](#sec:non-LTE). In Section [5](#sec:Ratio_age) we derive the ages of the SSCs and we correlate them with the observed molecular ratios. We summarise our conclusions in Section [6](#sec:Conc).

# Observations

## ALMA Observations

All of the ALMA observations used within this study are part of ALCHEMI (project code 2017.1.00161.L and 2018.1.00162.S). A detailed explanation of the calibration set-up, data acquisition and imaging of the data of this large program can be found in (cite: Martin_ALCHEMI_2021). We shall provide a brief summary here. ALCHEMI imaged the Central Molecular Zone (CMZ) of NGC 253 across the ALMA frequency Bands 3 to 7. This provided a near contiguous coverage of the frequencies from 84.2 GHz to 373.2 GHz. The nominal phase center of the observations is $\alpha$ = 00$^h$47$^m$33$^s$.26, $\delta$ = $-25^\circ$17$^\prime$17$^{\prime\prime}.7$ (ICRS). A common rectangular area with size $50^{\prime\prime} \times 20^{\prime\prime}$ ($850\times340$ pc) at a position angle of $65^\circ$ was imaged to cover the central nuclear region in NGC 253. The final homogeneous angular and spectral resolution for each of the image cubes produced from these measurements was $1.^{\prime\prime}6$ (cite: Martin_ALCHEMI_2021) and $\sim10$ km s$^{-1}$ , respectively. The common maximum recoverable angular scale achieved was $15^{\prime\prime}$ after combining the 12 m Array and Atacama Compact Array (ACA) measurements at all frequencies. The desired species for which the image cubes were created are summarised in Tables [\[tab:Line_list\]](#tab:Line_list)-[\[tab:Line_list_HCOP\]](#tab:Line_list_HCOP), and includes the main most abundant isotopologues of the molecules CO, HCN and HCO$^{+}$.

|           |            |                |         |                        |       |     |
|:---------:|:----------:|:--------------:|:-------:|:----------------------:|:-----:|:---:|
|  Species  | Transition | Rest Frequency | $E_{u}$ |        $A_{ul}$        | Ref.  |     |
|           |            |    \[GHz\]     |  \[K\]  |       \[s^-1^\]        |       |     |
|    CO     |    1-0     |    115.271     |  5.53   | 7.203 $\times 10^{-8}$ |       |     |
|           |    2-1     |    230.538     |  16.60  | 6.910 $\times 10^{-7}$ | 1,2,3 |     |
|           |    3-2     |    345.796     |  33.19  | 2.497 $\times 10^{-6}$ |       |     |
| $^{13}$CO |    1-0     |    110.201     |  6.25   | 6.333 $\times 10^{-8}$ |       |     |
|           |    2-1     |    220.399     |  15.87  | 6.075$\times 10^{-7}$  | 3,4,5 |     |
|           |    3-2     |    330.588     |  31.73  | 2.194$\times 10^{-6}$  |       |     |
| C$^{17}$O |    1-0     |    112.359     |  5.39   | 6.697$\times 10^{-8}$  |       |     |
|           |    2-1     |    224.715     |  16.18  | 6.425$\times 10^{-7}$  |  3,6  |     |
|           |    3-2     |    337.061     |  32.35  | 1.805$\times 10^{-6}$  |       |     |
| C$^{18}$O |    1-0     |    109.782     |  5.27   | 6.266$\times 10^{-8}$  |       |     |
|           |    2-1     |    219.560     |  15.81  | 6.012$\times 10^{-7}$  |  3,7  |     |
|           |    3-2     |    329.331     |  31.61  | 2.171$\times 10^{-6}$  |       |     |

\
We use molecular data of CO and its isotopologues from: 1) (cite: co_moldata_1994), 2) (cite: co_moldata_1997), 3) (cite: co_moldata_collis), 4) (cite: co_iso_moldata_2000), 5) (cite: 13co_moldata_2004), 6) (cite: c17o_moldata_2003), 7) (cite: c18o_moldata_2001). The data was sourced from the LAMDA database (cite: LAMDA_2005) and the Cologne Database for Molecular Spectroscopy (CDMS) catalogue [^2] (cite: CDMS_2001; CDMS_2005; CDMS_2016).

+:----------:+:----------:+:--------------:+:-------:+:---------------------:+:----:+:-:+
| Species    | Transition | Rest Frequency | $E_{u}$ | $A_{ul}$              | Ref. |   |
+------------+------------+----------------+---------+-----------------------+------+---+
|            |            | \[GHz\]        | \[K\]   | \[s^-1^\]             |      |   |
+------------+------------+----------------+---------+-----------------------+------+---+
| HCN        | 1-0        | 88.632         | 4.25    | 2.407$\times 10^{-5}$ | 1    |   |
+------------+------------+----------------+---------+-----------------------+      +---+
|            | 2-1        | 177.261        | 12.76   | 2.311$\times 10^{-4}$ |      |   |
+------------+------------+----------------+---------+-----------------------+      +---+
|            | 3-2        | 265.886        | 25.52   | 8.356$\times 10^{-4}$ |      |   |
+------------+------------+----------------+---------+-----------------------+      +---+
|            | 4-3        | 354.505        | 42.53   | 2.054$\times 10^{-3}$ |      |   |
+------------+------------+----------------+---------+-----------------------+------+---+
| H$^{13}$CN | 1-0        | 86.340         | 4.14    | 2.226$\times 10^{-5}$ | 1,2  |   |
+------------+------------+----------------+---------+-----------------------+      +---+
|            | 2-1        | 172.678        | 12.43   | 2.136$\times 10^{-4}$ |      |   |
+------------+------------+----------------+---------+-----------------------+      +---+
|            | 3-2        | 259.012        | 24.86   | 7.725$\times 10^{-4}$ |      |   |
+------------+------------+----------------+---------+-----------------------+      +---+
|            | 4-3        | 345.340        | 41.44   | 1.899$\times 10^{-3}$ |      |   |
+------------+------------+----------------+---------+-----------------------+------+---+
| HC$^{15}$N | 1-0        | 86.055         | 4.13    | 2.203$\times 10^{-5}$ | 1,3  |   |
+------------+------------+----------------+---------+-----------------------+      +---+
|            | 2-1        | 172.108        | 12.38   | 2.115$\times 10^{-4}$ |      |   |
+------------+------------+----------------+---------+-----------------------+      +---+
|            | 3-2        | 258.157        | 24.78   | 7.649$\times 10^{-4}$ |      |   |
+------------+------------+----------------+---------+-----------------------+      +---+
|            | 4-3        | 344.200        | 41.30   | 1.880$\times 10^{-3}$ |      |   |
+------------+------------+----------------+---------+-----------------------+------+---+

\
We use molecular data of HCN and its isotopologues from: 1) (cite: 2023_HCN_rates), 2) (cite: h13cn_moldata_2004), 3) ,(cite: hc15n_moldata_2005). The data was sourced from the Cologne Database for Molecular Spectroscopy (CDMS) catalogue (cite: CDMS_2001; CDMS_2005; CDMS_2016), or via private communication with authors.

+:----------------:+:----------:+:--------------:+:-------:+:----------------------:+:-------:+:-:+
| Species          | Transition | Rest Frequency | $E_{u}$ | $A_{ul}$               | Ref.    |   |
+------------------+------------+----------------+---------+------------------------+---------+---+
|                  |            | \[GHz\]        | \[K\]   | \[s^-1^\]              |         |   |
+------------------+------------+----------------+---------+------------------------+---------+---+
| HCO$^{+}$        | 1-0        | 89.188         | 4.28    | 4.187$\times 10^{-5}$  | 1,2,3,4 |   |
+------------------+------------+----------------+---------+------------------------+         +---+
|                  | 2-1        | 178.375        | 12.84   | 4.019$\times 10^{-4}$  |         |   |
+------------------+------------+----------------+---------+------------------------+         +---+
|                  | 3-2        | 267.558        | 25.68   | 1.453$\times 10^{-3}$  |         |   |
+------------------+------------+----------------+---------+------------------------+         +---+
|                  | 4-3        | 356.734        | 42.80   | 3.572$\times 10^{-3}$  |         |   |
+------------------+------------+----------------+---------+------------------------+---------+---+
| H$^{13}$CO$^{+}$ | 1-0        | 86.754         | 4.16    | 3.853$\times 10^{-5}$  | 1,2,5   |   |
+------------------+------------+----------------+---------+------------------------+         +---+
|                  | 2-1        | 173.507        | 12.46   | 3.699$\times 10^{-4}$  |         |   |
+------------------+------------+----------------+---------+------------------------+         +---+
|                  | 3-2        | 260.255        | 24.98   | 1.337$\times 10^{-3}$  |         |   |
+------------------+------------+----------------+---------+------------------------+         +---+
|                  | 4-3        | 346.998        | 41.63   | 3.287$\times 10^{-3}$  |         |   |
+------------------+------------+----------------+---------+------------------------+---------+---+
| HC$^{18}$O$^{+}$ | 1-0        | 85.162         | 4.09    | 3.6449$\times 10^{-5}$ | 1,2,6   |   |
+------------------+------------+----------------+---------+------------------------+         +---+
|                  | 2-1        | 170.322        | 12.26   | 3.498$\times 10^{-4}$  |         |   |
+------------------+------------+----------------+---------+------------------------+         +---+
|                  | 3-2        | 255.479        | 24.52   | 1.265$\times 10^{-3}$  |         |   |
+------------------+------------+----------------+---------+------------------------+---------+---+

\
We use molecular data of HCO$^{+}$and its isotopologues from: 1) (cite: 1999_hcop_collis), 2) (cite: 2020_hcop_collis), 3) (cite: hcop_moldata_2007), 4) (cite: hcop_tinti_moldata_2007), 5) (cite: h13cop_moldata_2001), 6) (cite: hc18op_moldata_2004). The data was sourced from the LAMDA database (cite: LAMDA_2005) and the Cologne Database for Molecular Spectroscopy (CDMS) catalogue (cite: CDMS_2001; CDMS_2005; CDMS_2016).

|          |                 |                           |                |
|:--------:|:---------------:|:-------------------------:|:--------------:|
|   SSC    |   R.A.(ICRS)    |        Dec.(ICRS)         |     Leroy      |
|  Group   | (00$^h$ 47$^m$) | ($-25^\circ$ 17$^\prime$) |      SSCs      |
| SSC-1\*  |   32$^s$.8108   |  21$^{\prime\prime}$.293  |     1,2,3      |
| SSC-4\*  |   32$^s$.9178   |  20$^{\prime\prime}$.426  |       4        |
| SSC-7\*  |   33$^s$.0147   |  19$^{\prime\prime}$.341  |     5,6,7      |
| SSC-9\*  |   33$^s$.0970   |  18$^{\prime\prime}$.053  |      8, 9      |
| SSC-13\* |   33$^s$.1927   |  16$^{\prime\prime}$.928  | 10, 11, 12, 13 |
| SSC-14\* |   33$^s$.2971   |  15$^{\prime\prime}$.583  |       14       |

: All the selected NGC 253 positions of the beam sized SSC\* regions described in Sect. [3.2](#subsec:Region_Selection). The SSCs defined in (cite: 2018Leroy) that are contained within each SSC group have been provided for clarity, using the nomenclature of that paper.

## SINFONI Observations

The Spectrograph for INtegral Field Observations in the Near-Infrared (SINFONI) at the ESO VLT was used to obtain infrared J-, H- and K-band images toward NGC 253. The SINFONI instrument is mounted at the Cassegrain focus of the Unit Telescope 4 at the Very Large Telescope (VLT). This paper uses the SINFONI K band observations first published in (cite: MullerSanchez2010), and a more detailed description of these observations may be found in that paper. In short, the observations of NGC 253 were made in visitor mode on August 28th, 2005. The K-band observations were taken using a spatial pixel scale of 0.25” corresponding to a field of view of 8” $\times$ 8” per frame and a spectral resolution of 68 km s$^{-1}$ . These observations were taken primarily to observe H$_2$ emission across the CMZ; thus multiple frames were taken along the CMZ until no H$_2$ was observed, resulting in 10 pointings altogether. This mosaic covers most of the CMZ of NGC 253; further details of these observations available in (cite: MullerSanchez2010).

# Moment Maps and Region Selection

## Spectral-Line Extraction

The molecules we focus on in this study are the $^{13}$C, $^{15}$N, $^{17}$O (of CO) and $^{18}$O isotopologues of CO, HCN and HCO$^{+}$. A full summary of the investigated lines are shown in Tables [\[tab:Line_list\]](#tab:Line_list) - [\[tab:Line_list_HCOP\]](#tab:Line_list_HCOP). The integrated spectral line intensities from our data cubes were extracted using `CubeLineMoment`[^3] (cite: 2019_Mangum_Heart). `CubeLineMoment` works by extracting integrated intensities for a given list of targeted spectral frequencies by applying a set of spectral and spatial masks (defined by the user). The `CubeLineMoment` masking process uses a brighter spectral line (typically the main isotopologue line of the same rotational transition), whose velocity structure over the galaxy is most representative of the science target line, which is used as a tracer of the velocity of the gas component inspected. The products of `CubeLineMoment` are moment 0, 1 and 2 maps in the desired units of the user, masked below a chosen $\sigma$ threshold (channel-based). (cite: 2019_Mangum_Heart) provides a more detailed overview of this process.

For use in the age approximation fitting (see Section [5.1](#sec:Age)), we have also extracted H39$\alpha$ (rest freq: 106.73738 GHz) radio recombination line emission from the ALCHEMI dataset in the six SSC apertures in order to estimate a dust-unobscured ionizing photon rate, elaborated upon in Section [5](#sec:Ratio_age). In order to completely image the line, we used the spectra over barycentric velocity ranges \[$-$200, 750\] km s$^{-1}$ to fit and measure the line emission. The Br$\gamma$ line was also extracted from the SINFONI data described, and is consistent with the map shown in Figure 11 of (cite: 2013Rosenberg).

## Region Selection

We have selected six SSC regions using the aperture size of the beam of the ALCHEMI observations. Due to the lower resolution of the ALCHEMI observations ($\sim28$ pc) with respect to the continuum observations of (cite: 2018Leroy) ($\sim2$ pc), we define new SSC regions, see Table [1](#tab:SSC_locations) for details. These regions were selected and identified such that they covered all of the SSC regions defined in (cite: 2018Leroy) at the ALCHEMI beam size resolution, with no overlap. Each of these regions contains within them between 1 to 4 of the SSC regions approximately resolved in (cite: 2018Leroy). Due to the fact that our newly defined regions do not correspond to those of (cite: 2018Leroy), a new nomenclature is needed. Thus from now on each region has been designated as a SSC\* region with its corresponding number chosen from one of the SSCs that it contains.

Within each SSC\* region, we have obtained the line intensities extracted over a beam-sized aperture of the available J transitions for each isotopologue. In Figs. [1](#fig:mom0_H13CN_10_21) and [2](#fig:mom0_H13CN_32_43) we present the velocity-integrated line intensity moment 0 maps from H$^{13}$CN (1-0) to (4-3) as an example of the lines we have imaged (Tables [\[tab:Line_list\]](#tab:Line_list)-[\[tab:Line_list_HCOP\]](#tab:Line_list_HCOP)). The remaining moment maps are shown in Appendix [7](#app:Mom0).

In each moment 0 map, the SSC\* regions listed in Table [1](#tab:SSC_locations) are shown with the ALCHEMI beam size plotted in the lower left corner in each map. The line intensities in each of these maps are shown in \[K km s$^{-1}$ \] units, the conversion to brightness temperature units from Jy/beam was accomplished using the `astropy` Python package (cite: 2022_Astropy). It must be noted that SSC-9\* and SSC-13\* tend to show weaker emission in each of our molecules, when compared to the other regions in the CMZ; this is seen towards the center of the moment maps shown in Figures [1](#fig:mom0_H13CN_10_21) and [2](#fig:mom0_H13CN_32_43). In fact, we identify an absorption feature at these locations, within certain J lines of certain isotopologues, which particularly affects the weaker emission species such as HC$^{15}$N, and H$^{13}$CO$^{+}$ and affects lower J lines most prominently. This absorption feature affecting both SSC-9\* and SSC-13\* is consistent with the position of the nuclear continuum source designated as ‘TH2’ (cite: 1985_TH2; 2010_TH2; 2019_Mangum_Heart). ‘TH2’ is a strong continuum source at the dynamical center of NGC 253 first identified in (cite: 1985_TH2) and long thought to possibly contain a Low Luminosity AGN (LLAGN), however it is now believed to be a supernova/supernova remnant source (cite: 2019_Mangum_Heart). This absorption primarily affects weaker lines, and as such no transitions of HC$^{15}$N were used for either SSC-9\* or SSC-13\*. An example of the effect of this absorption upon HC$^{15}$(1-0) in SSC-13\* compared to SSC-1\* is shown in Appendix [8](#app:absorption).

# Gas Properties Inference

## LTE Analysis

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-H13CN_10_H13CN_10_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(a\) |

|  |
|:---|
| ![image](images/Moment_Maps/Inset_KkmsM0_NGC253-H13CN_10_H13CN_10_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(b\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-H13CN_21_H13CN_21_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(a\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-H13CN_32_H13CN_32_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(b\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-H13CN_43_H13CN_43_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(c\) |

In order to aid in informing the priors of our non-LTE analysis, shown in the next sub-section [4.2](#sec:non-LTE), we obtain estimates of the molecular column densities assuming local thermodynamic equilibrium (LTE). The upper state column density, $N_u$, of a molecular transition can be approximated as $$\begin{equation}
    N_u = \frac{8\pi k \nu^2W}{hc^3A_{ul}}\left(\frac{1}{\eta_{ff}}\right) \frac{\tau}{1 - e^{- \tau}}, 
    \label{eq:uppercol}
\end{equation}$$ where $W$ is the integrated line intensity, $_u$ is signifying the upper level of a rotational transition, $A_{ul}$ is the Einstein A-coefficient, and $\tau$ is the optical depth. $\eta_{ff}$ is the beam filling factor. Given the variation between the beam size of this project ($1''.6 \times 1''.6$) and that of (cite: 2018Leroy) where these regions were first defined ($0''.11 \times 0''.11$) we accounted for the beam filling factor, $\eta_{ff}$ by defining it as:

$$\begin{equation}
\eta_{ff}=\frac{\theta^{2}_{S}}{\theta^{2}_{beam}+\theta^{2}_{S}}
\end{equation}$$

where $\theta_{S}$ and $\theta_{beam}$ are the respective resolutions of the source and the beam. For the purposes of the LTE estimation, $\theta_{S}$ was defined as the size of the regions observed in (cite: 2018Leroy). We could then use these transition column densities, $N_u$, to derive the total column density of the emitting molecule, $N$, by using $$\begin{equation}
    N=\frac{N_uZ(T)}{g_ue^{\frac{E_u}{kT}}}
    \label{eq:coldens},
\end{equation}$$ where $Z(T)$ is the partition function, $g_u$ is the statistical weight of level $u$, and $E_u$ is the excitation energy of level $u$. To compute the partition function, we make use of molecular data from the Cologne Database for Molecular Spectroscopy (CDMS) (cite: 2005_Muller; CDMS_2016). We used a combination of Eqs. [\[eq:uppercol\]](#eq:uppercol) and [\[eq:coldens\]](#eq:coldens) following the methodology of (cite: Goldsmith_1999) to compute an estimate of the total column density for each molecule. These total column densities were estimated over a range of temperatures and optical depth. The temperature range was left free up to the maximum range chosen to be consistent with the `RADEX` analysis (shown in Section [4.2](#sec:non-LTE)), with the upper limit being 500 K. We used a range of values for optical depth ($\tau$) from 0 to 10 in increments of 0.1 in the optically thin regime, $\tau < 1$ and 0.5 in the optically thick regime $\tau > 1$. These column densities, shown in Table [2](#tab:cols), are now used to define the prior distribution column density ranges studied during the `RADEX` modelling in the following section. Thanks to the fact that we have multiple transitions across each region for most of the species (the exceptions being weaker isotopologues (e.g. HC$^{15}$N and HC$^{18}$O$^{+}$) in the absorption affected regions) the temperature can also be constrained via the use of rotational diagrams. Most species across the regions, show a behaviour that can be explained by either multiple temperature components or the optical depth effects upon the higher J lines relatively to low-J. A notable exception to this is HCN which can consistently be fit with a single temperature component. This analysis drove the initial temperature ranges for each species seen in the non-LTE analysis (see Section [4.2](#sec:non-LTE)).

|     Species      | $N_{\rm min}$ | $N_{\rm max}$ |
|:----------------:|:-------------:|:-------------:|
|        CO        |    1.8e+18    |    8.9e+20    |
|    $^{13}$CO     |    6.1e+17    |    2.0e+20    |
|    C$^{17}$O     |    5.3e+15    |    3.9e+17    |
|    C$^{18}$O     |    9.1e+16    |    3.2e+19    |
|       HCN        |    3.1e+15    |    3.5e+17    |
|    H$^{13}$CN    |    7.7e+12    |    4.3e+16    |
|     HCO$^+$      |    1.4e+14    |    1.8e+17    |
| H$^{13}$CO$^{+}$ |    5.5e+12    |    9.8e+16    |
|    HC$^{15}$N    |    8.4e+11    |    1.0e+15    |
| HC$^{18}$O$^{+}$ |    2.0e+12    |    8.5e+15    |

: The minimum and maximum LTE column densities generated for each species directly from the observed intensities using the equations [\[eq:uppercol\]](#eq:uppercol) and [\[eq:coldens\]](#eq:coldens).

## Non-LTE Radex Analysis

We use a non-LTE analysis in order to infer the physical characteristics, as well as optical depth (per transition), of each region. We employ the radiative transfer code `RADEX` (cite: Van_der_Tak_2007). We reference the sources of the collisional data in the subtext of Tables [\[tab:Line_list\]](#tab:Line_list)-[\[tab:Line_list_HCOP\]](#tab:Line_list_HCOP).

In order to determine these physical conditions we followed a similar methodology, combining `SpectralRadex` and `UltraNest`, as (cite: Holdship+2021_SpectralRadex; 2022_Behrens; 2022Huang; Huang2023), with the difference being that in our study each group of isotopologues (e.g. HCN, H$^{13}$CN and HC$^{15}$N) were modelled together for the process. The physical conditions constrained within our modelling are: gas density ($n_{\rm H2}$), gas temperature ($T_{\rm kin}$), the total column density of each isotopologue (i.e. N(HCN), N(H$^{13}$CN), and N(HC$^{15}$N)), and the beam filling factor ($\eta_{\rm ff}$). The beam filling factor has been allowed to be a free parameter between 0 and 1, this has been done as the number of lines that we possess allow it to be constrained despite its degeneracy with N and $n_H$.

We inferred the gas properties by combining the `RADEX` modelling with a Bayesian inference process in order to properly sample the parameter space and obtain reliable uncertainties. While collisional data were available for HCO$^{+}$, HCN, H$^{13}$CN, HC$^{15}$N, CO, $^{13}$CO, C$^{18}$O and C$^{17}$O, this was not the case for the isotopologues of HCO$^{+}$. Collisional data of HCO$^{+}$ thus were used for its respective isotopologues, recommended by the LAMDA database (cite: LAMDA_2020) (See Table [\[tab:Line_list_HCOP\]](#tab:Line_list_HCOP)) . In order to test this, `RADEX` models were computed under the same physical parameters of the different isotopologues of CO, whose data are available, and the results were then compared. They were shown to be consistently similar and thus the assumption we make regarding the other isotopologues is valid.

The posterior probability distributions are derived with the nested sampling Monte Carlo algorithm MLFriends (cite: ultranest16; ultranest19), which was integrated into our analysis via the python package `UltraNest` [^4] (cite: ultranest21). Similarly to the approach adopted by (cite: 2022Huang; Huang2023), for each modelling run we assume prior distributions of our parameters to be uniform or log-uniform, where the column density priors are based upon the $N_u$ results obtained during the LTE analysis (see Section [4.1](#sec:LTE); these are given for each species group in Tables [3](#tab:table_prior_CO)-[5](#tab:table_prior_HCOP)). We assume that the uncertainty on our measured intensities is Gaussian so that our likelihood is given by $P(\theta | d) \sim \exp(-\frac{1}{2}\chi^2),$ where $\chi^2$ is the chi-squared statistic between our measured intensities and the `RADEX` output for a set of physical parameters $\theta$ (summarised earlier).

|               Variable               |       Range       | Distribution type |
|:------------------------------------:|:-----------------:|:-----------------:|
| Gas density, $n_{\rm H2}$ \[cm^-3^\] |  $10^{3}-10^{7}$  |    Log-uniform    |
| Gas temperature, $T_{\rm kin}$ \[K\] |     $40-500$      |      Uniform      |
|          $N$(CO) \[cm^-2^\]          | $10^{18}-10^{21}$ |    Log-uniform    |
|      $N$($^{13}$CO) \[cm^-2^\]       | $10^{17}-10^{20}$ |    Log-uniform    |
|      $N$(C$^{18}$O) \[cm^-2^\]       | $10^{15}-10^{19}$ |    Log-uniform    |
|      $N$(C$^{17}$O) \[cm^-2^\]       | $10^{16}-10^{19}$ |    Log-uniform    |
|   Beam filling factor, $\eta_{ff}$   |     $0.0-1.0$     |      Uniform      |

: The parameter space allowed as a prior for the nested sampling of the CO isotopologues `RADEX` models.

|               Variable               |       Range       | Distribution type |
|:------------------------------------:|:-----------------:|:-----------------:|
| Gas density, $n_{\rm H2}$ \[cm^-3^\] |  $10^{3}-10^{7}$  |    Log-uniform    |
| Gas temperature, $T_{\rm kin}$ \[K\] |     $40-500$      |      Uniform      |
|         $N$(HCN) \[cm^-2^\]          | $10^{14}-10^{18}$ |    Log-uniform    |
|      $N$(H$^{13}$CN) \[cm^-2^\]      | $10^{12}-10^{16}$ |    Log-uniform    |
|      $N$(HC$^{15}$N) \[cm^-2^\]      | $10^{11}-10^{15}$ |    Log-uniform    |
|   Beam filling factor, $\eta_{ff}$   |     $0.0-1.0$     |      Uniform      |

: The parameter space allowed as a prior for the nested sampling of the HCN isotopologues `RADEX` models.

|               Variable               |       Range       | Distribution type |
|:------------------------------------:|:-----------------:|:-----------------:|
| Gas density, $n_{\rm H2}$ \[cm^-3^\] |  $10^{3}-10^{7}$  |    Log-uniform    |
| Gas temperature, $T_{\rm kin}$ \[K\] |     $40-500$      |      Uniform      |
|      $N$(HCO$^{+}$) \[cm^-2^\]       | $10^{14}-10^{18}$ |    Log-uniform    |
|   $N$(H$^{13}$CO$^{+}$) \[cm^-2^\]   | $10^{12}-10^{17}$ |    Log-uniform    |
|   $N$(HC$^{18}$O$^{+}$) \[cm^-2^\]   | $10^{12}-10^{16}$ |    Log-uniform    |
|   Beam filling factor, $\eta_{ff}$   |     $0.0-1.0$     |      Uniform      |

: The parameter space allowed as a prior for the nested sampling of the HCO$^{+}$ isotopologues `RADEX` models.

This analysis provides an indication of the mean gas properties of our SSC\* regions, under the assumption that all of the fitted transitions in each group arise from the same gas component. Thus the results provided here are more of a mean property of the gas present in each SSC\* region as predicted by each molecule and its isotopologues. Along with the physical parameters described, this `RADEX` fitting also provides us with an indication of the optical depths, $\tau$, of the fitted lines for each region.

Figures [3](#fig:RADEX_corner_SSC4_CO)-[5](#fig:RADEX_corner_SSC4_HCOP) show the posterior distributions of the sampling for the CO, HCN, and HCO$^+$ isotopologues toward the SSC-4\* region. The remaining posterior distributions for the other regions are shown in Appendix [9](#app:Corners). A summary of the results of the `Ultranest` `RADEX` model fitting can be found in Tables [\[tab:CO_RADEX_Results\]](#tab:CO_RADEX_Results)-[\[tab:HCOP_RADEX_Results\]](#tab:HCOP_RADEX_Results). As can be seen from the figures, the majority of the parameters are constrained for each isotopologue group sampling, thanks to the large number of lines available in the ALCHEMI survey. The kinetic temperature, $T_{\rm K}$, however, remains largely unconstrained regardless of the region or isotopologue group. As already hinted by the LTE analysis, this may be (at least partly) due to the fact that there are multiple temperature components of the gas, a cold one being traced by the lower J transitions and another hot one being traced by higher J transitions. Another contributing factor is that the transitions being observed have an excitation temperature of $<\sim40$K, and since we are probing a temperature regime of $>100$K (cite: 2019_Mangum_Heart) in these regions, these lines are not suited to constrain $T_{\rm K}$.

As one would expect, the HCN and HCO$^{+}$ isotopologues trace denser regions of the gas ($\text{log}(n_H) > 4.3$) compared to the CO isotopologues ($\text{log}(n_H) \lesssim 3.5$). Also, as may be expected, CO isotopologues appear to be tracing more extended regions of the gas as shown by the larger beam filling factors, $\eta_{ff}$ ($\sim 0.3$, $\sim 5$ pc), compared to those of the HCN and HCO$^{+}$ isotopologues ($\lesssim 0.1$, $\lesssim 2$ pc, with the exception the 2 absorption affected regions for HCN). These lower values of $\eta_{ff}$ correspond to the scale of the constituent SSCs, as defined by (cite: 2018Leroy) (2-3 pc), located within each beam, thus reassuring us that the emission we are tracing and modelling is sourced from the SSCs we are observing rather than the larger scale GMCs defined in NGC 253 (cite: Martin_ALCHEMI_2021; Huang2023).

A particular region of note for HCN and HCO$^{+}$ and their isotopologues is SSC-14\* as it shows significantly higher-intensity emission than the other regions. This can be associated with the increased predicted column density of each of these molecules by $\leq0.5$ dex for some isotopologues, compared to the next most abundant region. In fact these high column densities approach the parameter space under which `RADEX` struggles to converge as a result of line saturation at high opacities, particularly for HCO$^{+}$ (N$_{\text{HCO}^+}>10^{17}$ $^{-2}$).

The predicted column densities of both HCO$^{+}$ and its corresponding $^{13}$C isotopologue are shown to consistently be higher than their corresponding HCN species counterparts. This enhancement is nearly of an order of magnitude for a couple of the regions (SSC-1\*, SSC-14\*). This supports the conclusion made in previous studies that HCO$^{+}$ (and thus its isotopologues) are relatively more abundant than HCN in regions of high star formation, usually when compared to other active regions, such as AGN-dominated regions (cite: Krips_2008; Izumi2016; 2022Butterworth).

![](images/Corners/CO_fill_SSC-4.pdf)

![](images/Corners/HCN_fill_SSC-4.pdf)

![](images/Corners/HCOP_fill_SSC-4.pdf)

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Location | T$_K$ | Log(n$_{\rm H}$ ) | Log(N$_{\rm CO}$) | Log(N$_{\rm ^{13}CO}$) | Log(N$_{\rm C^{18}O}$) | Log(N$_{\rm C^{17}O}$) | Beam Filling |
|  | \(K\) | (cm$^{-3}$) | (cm$^{-2}$) | (cm$^{-2}$) | (cm$^{-2}$) | (cm$^{-2}$) | Factor |
| SSC-1\* | $253_{-120}^{123}$ | $3.19_{-0.12}^{0.18}$ | $20.0_{-0.7}^{0.6}$ | $18.5_{-0.4}^{0.2}$ | $18.0_{-0.3}^{0.2}$ | $17.1_{-0.3}^{0.2}$ | $0.167_{-0.056}^{0.164}$ |
| SSC-4\* | $252_{-133}^{158}$ | $3.26_{-0.16}^{0.20}$ | $19.9_{-0.6}^{0.7}$ | $18.5_{-0.3}^{0.3}$ | $17.9_{-0.3}^{0.2}$ | $17.0_{-0.3}^{0.2}$ | $0.206_{-0.077}^{0.185}$ |
| SSC-7\* | $256_{-129}^{150}$ | $3.26_{-0.15}^{0.21}$ | $19.9_{-0.7}^{0.7}$ | $18.4_{-0.4}^{0.3}$ | $17.8_{-0.3}^{0.2}$ | $16.9_{-0.3}^{0.2}$ | $0.211_{-0.077}^{0.201}$ |
| SSC-9\* | $239_{-134}^{170}$ | $3.29_{-0.17}^{0.24}$ | $19.8_{-0.7}^{0.8}$ | $18.3_{-0.4}^{0.3}$ | $17.7_{-0.3}^{0.3}$ | $16.8_{-0.3}^{0.2}$ | $0.233_{-0.098}^{0.245}$ |
| SSC-13\* | $203_{-117}^{183}$ | $3.44_{-0.21}^{0.28}$ | $19.7_{-0.6}^{0.8}$ | $18.3_{-0.3}^{0.3}$ | $17.7_{-0.3}^{0.3}$ | $16.8_{-0.3}^{0.2}$ | $0.241_{-0.103}^{0.199}$ |
| SSC-14\* | $227_{-123}^{158}$ | $3.39_{-0.18}^{0.21}$ | $20.2_{-0.6}^{0.6}$ | $18.7_{-0.3}^{0.2}$ | $18.1_{-0.3}^{0.2}$ | $17.2_{-0.2}^{0.2}$ | $0.137_{-0.045}^{0.103}$ |

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Location | T$_K$ | Log(n$_{\rm H}$ ) | Log(N$_{\rm HCN}$) | Log(N$_{\rm H^{13}CN}$) | Log(N$_{\rm HC^{15}N}$) | Beam Filling |
|  | \(K\) | (cm$^{-3}$) | (cm$^{-2}$) | (cm$^{-2}$) | (cm$^{-2}$) | Factor |
| SSC-1\* | $271_{-109}^{134}$ | $5.48_{-0.09}^{0.10}$ | $16.5_{-0.3}^{0.3}$ | $15.2_{-0.3}^{0.3}$ | $14.4_{-0.2}^{0.2}$ | $0.069_{-0.022}^{0.041}$ |
| SSC-4\* | $294_{-120}^{131}$ | $5.54_{-0.08}^{0.09}$ | $16.6_{-0.3}^{0.3}$ | $15.3_{-0.2}^{0.2}$ | $14.4_{-0.2}^{0.2}$ | $0.063_{-0.017}^{0.031}$ |
| SSC-7\* | $325_{-147}^{120}$ | $5.56_{-0.08}^{0.09}$ | $16.7_{-0.3}^{0.2}$ | $15.5_{-0.2}^{0.2}$ | $14.5_{-0.2}^{0.1}$ | $0.055_{-0.011}^{0.023}$ |
| SSC-9\* | $310_{-144}^{127}$ | $5.78_{-0.26}^{0.15}$ | $15.4_{-0.5}^{1.2}$ | $14.2_{-0.5}^{0.9}$ | \- | $0.260_{-0.187}^{0.472}$ |
| SSC-13\* | $211_{-99}^{163}$ | $6.05_{-0.14}^{0.17}$ | $15.3_{-0.5}^{1.0}$ | $14.2_{-0.4}^{0.7}$ | \- | $0.293_{-0.222}^{0.437}$ |
| SSC-14\* | $264_{-130}^{138}$ | $5.78_{-0.09}^{0.09}$ | $16.8_{-0.2}^{0.2}$ | $15.7_{-0.2}^{0.1}$ | $14.9_{-0.1}^{0.1}$ | $0.047_{-0.007}^{0.012}$ |

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Location | T$_K$ | Log(n$_{\rm H}$) | Log(N$_{\rm HCO^+}$) | Log(N$_{\rm H^{13}CO^+}$ ) | Log(N$_{\rm HC^{18}O^+}$ ) | Beam Filling |
|  | \(K\) | (cm$^{-3}$) | (cm$^{-2}$) | (cm$^{-2}$) | (cm$^{-2}$) | Factor |
| SSC-1\* | $297_{-137}^{143}$ | $4.44_{-0.57}^{0.22}$ | $16.9_{-0.5}^{0.6}$ | $15.3_{-0.4}^{0.6}$ | $14.7_{-0.3}^{0.6}$ | $0.068_{-0.018}^{0.032}$ |
| SSC-4\* | $291_{-151}^{147}$ | $4.77_{-0.13}^{0.13}$ | $17.0_{-0.3}^{0.4}$ | $15.2_{-0.2}^{0.2}$ | $14.6_{-0.2}^{0.1}$ | $0.045_{-0.010}^{0.017}$ |
| SSC-7\* | $180_{-67}^{208}$ | $4.93_{-0.14}^{0.14}$ | $17.2_{-0.3}^{0.6}$ | $15.3_{-0.2}^{0.2}$ | $14.7_{-0.1}^{0.1}$ | $0.033_{-0.008}^{0.011}$ |
| SSC-9\* | $270_{-154}^{154}$ | $4.36_{-0.73}^{0.62}$ | $17.1_{-0.8}^{0.6}$ | $15.4_{-0.7}^{0.6}$ | $14.5_{-0.6}^{0.6}$ | $0.081_{-0.030}^{0.066}$ |
| SSC-13\* | $263_{-148}^{165}$ | $4.38_{-0.66}^{0.57}$ | $17.1_{-0.6}^{0.6}$ | $15.4_{-0.6}^{0.6}$ | $14.6_{-0.5}^{0.6}$ | $0.091_{-0.032}^{0.064}$ |
| SSC-14\* | $125_{-36}^{212}$ | $4.80_{-0.34}^{0.21}$ | $17.6_{-0.5}^{0.3}$ | $15.7_{-0.3}^{0.4}$ | $15.0_{-0.2}^{0.3}$ | $0.039_{-0.010}^{0.014}$ |

Moreover, the optical depth conditions of each investigated species and its respective transitions for each SSC\* region were obtained. These results are shown in Appendix [10](#app:tau). We observe that the majority of non-main isotopologues are indeed optically thin ($\tau < 1$) for the majority of our SSC\* regions, with a couple of notable exceptions. Specifically, $^{13}$CO, H$^{13}$CO$^{+}$ and HC$^{18}$O$^{+}$ have multiple lines across the different regions that are optically thick, primarily driven by the significant column densities that we observe of these species. The optical depth for each species is also predicted to be lower for the J=1-0 transitions than for the J=2-1 transitions ($\tau_{10}<\tau_{21}$). The physical reason for this occurrence can be explained by the dependence of $\tau$ on the $N_u$ and $B_{ul}$ parameters (cite: Goldsmith_1999) where $B_{ul}$ is the Einstein coefficient for induced emission. In the case of our lines the increase of $B_{ul}$ with increasing transitions is larger than the decrease of $N_u$, this thus results in increasing optical depth with transition level.

# Isotopic Ratios and their Relationship to SSC Ages

## SSC Age Determination

Since isotopes are generated and supplied to the ISM over varying timescales, dependent on the evolutionary stages of intermediate-mass or more massive stars, by examining and comparing how these ages correlate (or not) to abundance ratios we can more reliably test the hypothesis of that factors such as the IMF are the primary driving forces of observed isotopic ratios (cite: Romano2017). In order to determine ages for each SSC\* region we used the stellar population modelling software `Starburst99` to compute the evolution of how the equivalent width of the Br$\gamma$, EW(Br$\gamma$), as well as the ionizing photon rate estimated from the H39$\alpha$ line evolved with the age of the star-forming region (cite: Starburst99_1999; Starburst99_2014). How the ionizing photon rate is derived has been summarised in Appendix [11](#app:H39). Ionizing photon rate and EW(Br$\gamma$) are both inversely proportional to the age of a high star-forming region such as an SSC, as they are primarily driven by the presence of the most massive stars. `Starburst99` operates by populating a main sequence of stars under specified initial conditions and allowing the evolution of these populations to occur over a user-defined timescale (in this study, $10^4-10^9$ yrs). The evolution of these populations results in various effects upon observable properties, such as ionizing photon rate and EW(Br$\gamma$), as a result of how its constituent stars’ progress along their evolutionary track. `Starburst99` (S99) allows for the specification of the IMF and of upper mass boundary of formed stars. Means of formation of new stars in this model can be conducted in two primary ways: either all of the population can be created initially (known as Instantaneous formation) or continuously over the entire period of the model at intermittent time steps.

Before we can obtain ages for the SSC\* regions, we have to verify which combination of parameters reliably reproduces the observed conditions in these regions. S99 allows for various input parameters, but the ones most prudent to this study are IMF power law, stellar mass cutoff and formation type. To do this we fit the ionizing photon rates of H39$\alpha$ and the equivalent width of Br$\gamma$, as both are available outputs of S99. The range of initial conditions can be found in Table [6](#tab:S99_Params). The different formation types (Instantaneous and Continuous) determine whether S99 is entirely populated with stars initially or if there is a constant rate of new stars formed, respectively. The masses used as a part of these models were taken from a previous study of the SSCs in NGC 253 ($\sim 10^5$ M$_\odot$, (cite: 2018Leroy)). We found that, when setting appropriate masses to be achieved $10^5$ M$_\odot$ the Continuous models were not able to reproduce the observed values of Br$\gamma$ EW or ionizing photon rate over the entire time range and thus were discarded in favour of Instantaneous models. The remaining parameters of both IMF and Star Mass Boundary were then fit using the ionizing rate and EW(Br$\gamma$). The IMF power-law values were chosen to represent typical IMF scenarios, 1.5, 2.35 and 3.3 representing top-heavy, a typical Salpeter IMF and a bottom-heavy scenario respectively (cite: 1955_Salpeter).

|            Variable            |           Range           |
|:------------------------------:|:-------------------------:|
|         Formation Type         | Instantaneous, Continuous |
|        IMF (Power-law)         |      1.5, 2.35, 3.3       |
| Star Mass Boundary (M$_\odot$) |       100, 150, 250       |

: The investigated initial parameters of `Starburst99`.

We extracted H39$\alpha$ radio recombination line emission from the ALCHEMI dataset in the six SSC\* apertures in order to estimate an ionizing photon rate free of dust obscuration. In all SSCs\* a component consistent with He39$\alpha$ which has a velocity offset from H39$\alpha$ of $-$122.15 km s$^{-1}$ , was also present. In SSC-1\*, 4\*, 7\*, and 14\*, we fit one Gaussian component to hydrogen and one Gaussian component to helium. In SSCs-9\* and 13\*, we fit two Gaussian components to the two observed velocity components of hydrogen and one Gaussian component to helium. The spectra, shown with fitting, for each region are supplied in Appendix [11](#app:H39). We use the total hydrogen H39$\alpha$ integrated emission, summed over two components where applicable, to estimate the ionizing photon rate, as described in (cite: Emig_2020) and briefly in Appendix [11](#app:H39).

The equivalent width of the Br$\gamma$ line was obtained by measuring the line emission over the SSC\* apertures using the Br$\gamma$ image from (cite: 2013Rosenberg). The equivalent width was obtained by using this line emission in combination with the K continuum.

A top-heavy IMF power-law of 1.5 and a upper stellar mass cutoff of 150 M$_{\odot}$ with instantaneous star formation was shown to be the best fit to both the H39$\alpha$ and Br$\gamma$ data. We were thus able to obtain ages for each of the SSC\* regions as predicted by `Starburst99`. We find an average best fit for the age of the order of $10^6$ years, which implies that nucleosynthesis effects are unlikely to lead to isotopic differentiation across the SSC regions due to their young ages, on the order of $10^6$ years, relative to the necessary timescales required for the production of the isotopes ($\sim10^8$ yrs, (cite: Milam_2005)). For example, $^{13}$C is primarily produced from $^{12}$C during the CNO cycle of intermediate mass stars ($1.5-6$ M$_\odot$) and ejected during their AGB phase (cite: 13C). Similarly, $^{15}$N can be produced and supplied to the ISM via nova explosions, this can lead to variations in the $^{14}$N/$^{15}$N across the galactic disk, however $10^9$ yrs are typically required for significant enough nova to occur (cite: Romano2017; 2019_Romano; 2022_Colzi). We investigate the relationship between the SSCs\* ages and isotopic ratios in the next section to see whether a correlation indeed exists.

## Is There a Correlation Between SSC Age and Isotopic Ratio?

From the derived column densities we have the possibility to investigate whether there is a correlation between the age of each star-forming region and the isotopic ratio. Table [7](#tab:Ratio_Ranges) contains the ranges and means of the isotopologue column ratios produced from the `RADEX` modelling. To this end we shall summarise the primary isotopic ratios investigated in this study and how their predicted column densities correlate to the modelled ages of each region. The plots for the column densities ratios versus the predicted ages will be shown for each isotopologue ratio, but the line intensity ratio versus age will only be shown for the J(1-0) transition of $^{12}$CO/$^{13}$CO. The `RADEX` column density predictions give the abundance of a molecule and `RADEX` takes into account the optical depth effects, as such they give typically a more reliable result than individual line intensity ratios. For optically-thin LTE gas, both results should be comparable. Given the low sample size of 4 to 6 regions (depending on the ratio) quantified statistics of any possible correlation between age and column density ratio are not given. Instead a qualitative assessment of each ratio vs age plot has been completed.

|           Ratio            | X$_{Ratio}$  | $\bar{X}_{Ratio}$ |
|:--------------------------:|:------------:|:-----------------:|
|        CO/$^{13}$CO        |  26.7-35.9   |       28.3        |
| HCO$^{+}$/H$^{13}$CO$^{+}$ |  36.3-89.9   |       58.1        |
|       HCN/H$^{13}$CN       |  11.1-22.4   |       15.4        |
| HCO$^{+}$/HC$^{18}$O$^{+}$ | 144.6-409.6  |       262.7       |
|        CO/C$^{18}$O        | 100.0-145.1  |       106.6       |
|       HCN/HC$^{15}$N       |  75.7-183.4  |       128.4       |
|        CO/C$^{17}$O        | 778.8-1147.0 |       847.2       |

: The ranges and means of the isotopologue column density ratios from across all the SSC\* regions.

### $^{12}$C/$^{13}$C

Figure [6](#fig:CO_13CO_Ratios) shows the intensity and column density ratios of $^{12}$CO/$^{13}$CO. It is clear that, especially in column densities, this ratio shows no correlation with regards to the predicted ages of each region. It is indeed possible that this lack of correlation is a result of the fact that these regions are too young ($<<10^{8}$ yrs) to observe a meaningful effect as a result of nucleosynthesis from any but the most massive of stars. There is also no relation with regards to spatial location of these regions column density ratios. The regions away from the ‘TH2’ region do show lower $^{12}$C(1-0)/$^{13}$C(1-0) intensities ratios, though all fall within error bars.

Figure [7](#fig:HCOP_H13OP) shows the column density ratio of the H$^{12}$CO$^{+}$/H$^{13}$CO$^{+}$ ratio (range, $\sim36-90$) versus age. This ratio does indeed show a negative correlation with age, with the exception of SSC\*-13. However, we note that SSC\*-13 is the region most affected by the absorption source observed near the dynamical center of NGC 253, as discussed earlier. If we disregard this region it would imply that there are some processes, other than nucleosynthesis, on this timescale that can affect this ratio. In fact, (cite: 2015Roueff) found that H$^{12}$CO$^{+}$/H$^{13}$CO$^{+}$ experiences a turbulent variation due to fractionation processes up until $\sim10^6$ yr, which is of the same order as the observed ages of these regions (cite: 2023_Sipila). This is a tentative hypothesis however as we have only a few observed regions over a relatively small timescale, as well as assuming that SSC-13\* is significantly affected by absorption features.

|                                                     |
|:----------------------------------------------------|
| ![image](images/Abund_Ratio_Ages/N_CO__N_13CO_.png) |
| \(a\)                                               |

|                                                       |
|:------------------------------------------------------|
| ![image](images/Intens_Ratios_Ages/CO_10_13CO_10.png) |
| \(b\)                                                 |

If fractionation processes are indeed responsible for the trend seen in H$^{12}$CO$^{+}$/H$^{13}$CO$^{+}$ then it is possible that ISM fractionation processes have already approached an equilibrium with regards to the $^{12}$CO/$^{13}$CO ratio by the time frame covered by our regions. Indeed this would be consistent with the chemical models of (cite: 2015Roueff) who found that the $^{12}$CO/$^{13}$CO ratio approached equilibrium swiftly and with less variation than H$^{12}$CO$^{+}$/H$^{13}$CO$^{+}$.

![](images/Abund_Ratio_Ages/N_HCOP__N_H13COP_.png)

![](images/Abund_Ratio_Ages/N_HCN__N_H13CN_.png)

Similarly to the $^{12}$CO/$^{13}$CO ratio, the H$^{12}$CN/H$^{13}$CN ratio, shown in Figure [8](#fig:HCN_H13CN), shows little correlation with age, though the ratio shows significantly more variation between the regions than its CO counterpart. The H$^{12}$CN/H$^{13}$CN ratio has been predicted to undergo a similarly turbulent variation as H$^{12}$CO$^{+}$/H$^{13}$CO$^{+}$ approaching the timescales observed across these SSC\* regions; this may explain the significant variation observed (cite: 2015Roueff; 2023_Sipila).

H$^{13}$CO$^{+}$ and H$^{13}$CN are the $^{13}$C-bearing isotopologues of the dense gas tracers HCN and HCO$^{+}$. These isotopologues are optically thin unlike their $^{12}$C counterparts. An interesting relation was observed in the column density ratio of these isotopologues. As shown in Figure [9](#fig:H13COP_H13CN), once we disregard the absorption affected regions of SSC-9\* and SSC-13\* (for the reasons stated earlier, the equivalent plot including the absorption affected region can be seen in Appendix [8.2](#app:more:ratio_age_plots)) there appears to be a positive relation between age and this ratio. This is in contrast to the equivalent ratio of HCO$^{+}$/HCN shown in Figure [10](#fig:HCOP_HCN) in which no correlation with age can be seen. This result perhaps supports the fractionation hypothesis for the correlation seen in H$^{12}$CO$^{+}$/H$^{13}$CO$^{+}$. This ratio may also be a useful tool as a tracer of the age of SSC regions in the future as a result.

(cite: 2019Martin) observed isotope ratios using spatially resolved optically thin isotopologues of CO in NGC 253. They observed $^{12}$C/ $^{13}$C $\sim 21\pm 6$ using C$^{18}$O and $^{13}$C$^{18}$O. In comparison we observed a larger ratio than this when viewed with CO/$^{13}$CO ($\sim27-36$) and HCO$^{+}$/H$^{13}$CO$^{+}$ ($\sim36-80$) in our SSC\* regions. A smaller ratio is observed with HCN/H$^{13}$CN ($\sim11-22$), this range of values is consistent with observations of (cite: Meier_2015) who observed HCN/H$^{13}$CN at 2” scale with a range of $10 - 20$. (cite: Meier_2015) also observed HCO$^{+}$/H$^{13}$CO$^{+}$ at this scale and found a range of $10 - 20$.(cite: Martin_ALCHEMI_2021) observed these isotopologue ratios too, but at 15” ($\sim 255$pc) resolution, where they observed values for CO/$^{13}$CO of $13.3 \pm 1.4$, HCN/H$^{13}$CN of $26.1 \pm 1.3$ and HCO$^{+}$/H$^{13}$CO$^{+}$ of $21.2 \pm 1.5$. It should be noted that the assumed source size was 10” ($\sim$ 170 pc) for the CO ratio and 5” for the HCN and HCO$^{+}$ ratios. Thus, the resolution and region in which these ratios are observed significantly affect the result. (cite: 2019_Tang) observed CN and $^{13}$CN at 3.6" $\times$ 1.7" ($\sim68 \times 32$pc) resolution in NGC 253 and observed an average $^{12}$C/$^{13}$C ratio of $41.6 \pm 0.2$.

A similar study at a comparable resolution observing regions of intense star formation, like SSCs, has not been completed previously in nearby galaxies, as such a comparison to observations of the $^{12}$C/$^{13}$C ratio would not be appropriate. The $^{12}$C/$^{13}$C ratio has been observed over many regions over many galactic regions. (cite: 2023_Yan) provides an overview (In Table 7 of that paper) of $^{12}$C/$^{13}$C ratios observed across different regions of the Milky Way. On average the $^{12}$C/$^{13}$C varies between $\sim25 \pm 2$ in the CMZ up to $\sim69 \pm 12$ in the Outer Galaxy (cite: 1985_Henkel; 1990_Langer; 1993_Langer; 1996_Wouterloot; 1998_Keene; 2002_Savage; Milam_2005; 2019_Yan; 2023_Yan).

![image](images/Abund_Ratio_Ages/N_H13COP__N_H13CN__Zoomed.png)\

![image](images/Abund_Ratio_Ages/N_HCOP__N_HCN__Zoomed.png)\

In summary, the $^{12}$C/$^{13}$C column density ratio from our `RADEX` modelling shows little correlation with the ages of these star-forming regions. A possible exception being the H$^{12}$CO$^{+}$/H$^{13}$CO$^{+}$ ratio, which could be a result of chemical fractionation affecting this ratio on the observed timescales (rather than nucleosynthesis). The lack of correlation we observe supports the conclusion of (cite: Romano2017) that the IMF is a primary driving factor in the isotopic ratio observed in star- forming regions. Though it must be noted that this is only the age range covered by these SSCs.

### $^{16}$O/$^{18}$O

Figures [11](#fig:CO_C18O) and [12](#fig:HCOP_HCO18P) show the column density ratio of the C$^{16}$O/C$^{18}$O and HC$^{16}$O$^{+}$/HC$^{18}$O$^{+}$ ratio, respectively. C$^{16}$O/C$^{18}$O clearly shows no correlation between age and column density ratio. The HC$^{16}$O$^{+}$/HC$^{18}$O$^{+}$ ratio generally does not show a clear trend, though the oldest predicted region SSC-1\* does show a significantly smaller ratio than the rest. To explore whether this is a trend or not would require an investigation into more regions and a larger range of timescales. When compared to previous observations of $^{16}$O/$^{18}$O, CO/C$^{18}$O ($\sim100-145$) is largely consistent with those derived at 3” ($\sim51$ pc) resolution in (cite: 2019Martin) in NGC 253, using $^{13}$CO/$^{13}$C$^{18}$O (130 $\pm 40$), however our results for the ratio of HCO$^{+}$/HC$^{18}$O$^{+}$ are significantly higher ($140-410$). (cite: Martin_ALCHEMI_2021) provides ALMA Compact Array observations of $^{16}$O/$^{18}$O ratios in NGC 253 at 25” ($\sim 255$ pc) resolution calculated from CO/C$^{18}$O ($48 \pm 5$), $^{13}$CO/$^{13}$C$^{18}$O (520 $\pm 60$) and HCO$^{+}$/HC$^{18}$O$^{+}$ ($100 \pm 20$). (cite: Aladro2015) observed the HCO$^{+}$/HC$^{18}$O$^{+}$ at an even lower resolution of 28” found it to be $69 \pm 2$.

As was the case for $^{12}$C/$^{13}$C an appropriate comparison study in nearby galaxies has not yet been completed. $^{16}$O/$^{18}$O ratios, however, have been observed across different regions of the Milky Way. As viewed with H$_2$CO and its respective $^{18}$O isotopologue, the $^{16}$O/$^{18}$O varies from $\sim263 \pm 45$ in the CMZ up to $\sim625 \pm 144$ in the Outer Galaxy (cite: 1981_Gardner; 1994_Wilson; 2023_Yan).

The variations across all these observations and resulting ratios within the same galaxy, show that resolution and the regions being traced play a key role upon observed isotope ratio. As stated earlier, nucleosynthesis effects upon these ratios can most likely be discarded due to the young ages of these regions.

![](images/Abund_Ratio_Ages/N_CO__N_C18O_.png)

![](images/Abund_Ratio_Ages/N_HCOP__N_HC18OP_.png)

### $^{16}$O/$^{17}$O

The column density ratio of C$^{16}$O/C$^{17}$O is shown in Figure [13](#fig:CO_C17O). This ratio is largely unaffected by the SSC\* age, similar to what is observed in the other ratios. $^{17}$O, unlike $^{18}$O, can be produced during nucleosynthesis in the hydrogen burning of less massive stars, and so its enrichment in the ISM would likely be observed at even larger timescales than those expected by $^{18}$O. From the limited sample of this study, on the time scale probed by these regions, this ratio appears to be independent of SSC age. This ratio was observed at an observed source size of 10” as $400 \pm 40$ in NGC253 in (cite: Martin_ALCHEMI_2021), this is significantly lower than the what we observe in these SSC\* regions $\sim 780-1150$.

Again, due to a lack of an appropriate comparison study in nearby galaxies, we supply instead a comparison to galactic observations. $^{16}$O/$^{17}$O ratios have been observed across different regions of the Milky Way. As viewed with H$_2$CO and its respective $^{17}$O isotopologue, the $^{16}$O/$^{17}$O ratio varies from $\sim894 \pm 155$ in the CMZ up to $\sim3000 \pm 786$ in the Outer Galaxy according to (cite: 2023_Yan) using data from (cite: 1981_Gardner; 1994_Wilson; 2020_Zhang).

![](images/Abund_Ratio_Ages/N_CO__N_C17O_.png)

### $^{14}$N/$^{15}$N

Figure [14](#fig:HCN_HC15N) shows the column density ratio of the HC$^{14}$N/HC$^{15}$N ratio. The analysis of this ratio is affected greatly by the necessity to discount the two regions, SSC\*-9 and SSC\*-13 where absorption effects become noticeable in the HC$^{15}$N line profile. From the four remaining regions however we find again no sign of a correlation between age and the column density ratio. An interesting distinction is that the two regions located closest to the edge of the CMZ (SSC\*-1 and SSC\*-14) both have significantly lower HC$^{14}$N/HC$^{15}$N ratios than their more central counterparts (SSC\*-4 and SSC\*-7). Though without observing more regions we can not draw any conclusions from this. Galactic observations of $^{14}$N/$^{15}$N have been made in previous studies, including with HC$^{14}$N/HC$^{15}$N as was observed in this paper. The values of $^{14}$N/$^{15}$N viewed across the Milky Way, when observed with HC$^{14}$N/HC$^{15}$N, range from $284 \pm 63$ within the Inner Disk up to $388 \pm 32$ in the Outer Galaxy (cite: 2012_Adande; 2018_Colzi).

![](images/Abund_Ratio_Ages/N_HCN__N_HC15N_.png)

### Isotopic Ratios and ISM Fractionation

Table [7](#tab:Ratio_Ranges) lists the observed ranges of isotopic ratios for the various species. Focusing initially on $^{12}$C/$^{13}$C, (cite: 2020Viti) conducted a theoretical chemical modelling study on carbon fractionation across different physical conditions that may represent different types of galaxies. Taking the most suitable model from this study, representing starburst galaxies (see Figure 10 in (cite: 2020Viti)), H$^{12}$CN/H$^{13}$CN is predicted ($\sim 70$) to be higher than what we observe ($\sim11$-$22$). The models agree relatively well for the younger regions with regards to H$^{12}$CO$^{+}$/H$^{13}$CO$^{+}$ ($\sim 55$). $^{12}$CO/$^{13}$CO is also relatively well predicted by these models ($\sim 30$) relative to our observations ($\sim26$-$\sim36$).

(cite: 2019Viti) completed a similar study on nitrogen fractionation.

They found that, depending on the physical parameters, the resulting HC$^{14}$N/HC$^{15}$N abundance ratio could vary from $\sim 10$ to $\sim 1000$. The scenario for the most elevated ratios ($\sim 1000$) are where fractionation processes were suppressed; these were typically for cases of relatively low density $n_H \sim 10^4$ cm^-3^ and high cosmic-ray ionisation rate, visual extinctions or radiation fields. The significantly lower range of HC$^{14}$N/HC$^{15}$N seen in this study ($\sim 75-180$) as well as the higher densities predicted by the non-LTE results ($n_H > 10^5$ cm^-3^) would imply that fractionation processes are occurring within these regions.

# Conclusions

By using the plethora of data made available to us thanks to the ALCHEMI collaboration, we made use of lines from 10 isotopologues, collectively, of CO, HCN and HCO$^{+}$ in order to investigate the possibility of a correlation between the age of star-forming regions in NGC 253 and the observed isotopic ratios. Our findings are summarised below:

- From our `RADEX` results HCN and its isotopologues appear to be tracing a slightly denser component of the gas ($n_H>10^5$ cm^-3^) than HCO$^{+}$ and its isotopologues.

- HCO$^{+}$ and its isotopologues have larger column densities than their HCN counterparts. This is consistent with previous studies that have found HCO$^{+}$ to be more abundant than HCN in regions of high star formation. CO and its isotopologues, as one might expect, trace a more diffuse and extended component of the gas in these regions, as shown by their lower densities ($n_H<10^4$ cm^-3^).

- Our results regarding the $^{12}$CO/$^{13}$CO and H$^{12}$CN/H$^{13}$CN seem to discount a clear relation between the age of a star forming region and the isotopic ratio $^{12}$C/$^{13}$C.

- H$^{12}$CO$^{+}$/H$^{13}$CO$^{+}$ may show a tentative negative correlation, as long as one makes the assumption that the results for SSC\*-13 are being greatly perturbed by the absorption feature. In order to verify this trend, a follow-up study of these regions at higher resolution to differentiate the individual SSCs in HCO$^{+}$ and its isotopologues would be required. This would allow a more complete understanding of the possible fractionation occurring in these regions to be obtained.

- The $^{16}$O/$^{18}$O ratios generally show little correlation with age, with the exception of the oldest region (SSC\*-1) appearing to have a significantly lower HC$^{16}$O$^{+}$/HC$^{18}$O$^{+}$ ratio than the younger regions.

- The ratios HC$^{14}$N/HC$^{15}$N and HC$^{16}$O$^{+}$ and HC$^{17}$O$^{+}$ also show no correlation with the age of the SSCs.

- The ratios observed in this study generally support the conclusion that age has a minor effect upon isotopic ratios, at least over the limited age range observed in these regions, thus supporting the hypothesis that the IMF is a primary driving factor of the observed isotopic ratios in these regions (cite: Romano2017) or possibly fractionation effects.

To more confidently make conclusive statements regarding the use of C, N, or O isotopic ratios, a future study either observing the SSC regions in NGC 253 at higher spatial resolution, or perhaps a multi-object study observing a wider range of star-forming regions spanning a larger range of ages should be completed.

# Acknowledgements

J.B., S.V., K.Y.H. and M.B. have received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme MOPPEX 833460. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00161.L and ADS/JAO.ALMA#2018.1.00162.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. V.M.R. has received support from the project RYC2020-029387-I funded by MCIN/AEI /10.13039/501100011033, and from the the Consejo Superior de Investigaciones Científicas (CSIC) and the Centro de Astrobiología (CAB) through the project 20225AT015 (Proyectos intramurales especiales del CSIC). L.C. acknowledges financial support through the Spanish grant PID2019-105552RB-C41 funded by MCIN/AEI/10.13039/501100011033.

114 natexlab

(ref: 2012_Adande) Adande, G. R. & Ziurys, L. M. 2012, ApJ, 744, 194

(ref: Aladro2015) Aladro, R., Martı́n, S., Riquelme, D., et al. 2015, A&A, 579, A101

(ref: 2022_Astropy) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: 2022_Behrens) Behrens, E., Mangum, J. G., Holdship, J., et al. 2022, ApJ, 939, 119

(ref: Bendo_2015) Bendo, G. J., Beswick, R. J., D’Cruze, M. J., et al. 2015, MNRAS, 450, L80

(ref: SINFONI_2) Bonnet, H., Abuter, R., Baker, A., et al. 2004, The Messenger, 117, 17

(ref: ultranest16) Buchner, J. 2016, Statistics and Computing, 26, 383

(ref: ultranest19) Buchner, J. 2019, PASP, 131, 108005

(ref: ultranest21) Buchner, J. 2021, The Journal of Open Source Software, 6, 3001

(ref: 2022Butterworth) Butterworth, J., Holdship, J., Viti, S., & Garcı́a-Burillo, S. 2022, A&A, 667, A131

(ref: hc15n_moldata_2005) Cazzoli, G., Puzzarini, C., & Gauss, J. 2005, ApJS, 159, 181

(ref: 13co_moldata_2004) Cazzoli, G., Puzzarini, C., & Lapinov, A. V. 2004, ApJ, 611, 615

(ref: 1999Chin) Chin, Y.-n., Henkel, C., Langer, N., & Mauersberger, R. 1999, ApJL, 512, L143

(ref: 13C) Clayton, D. 2003, Handbook of Isotopes in the Cosmos

(ref: 2018_Colzi) Colzi, L., Fontani, F., Rivilla, V. M., et al. 2018, MNRAS, 478, 3693

(ref: 2022_Colzi) Colzi, L., Romano, D., Fontani, F., et al. 2022, A&A, 667, A151

(ref: 2020_Colzi) Colzi, L., Sipilä, O., Roueff, E., Caselli, P., & Fontani, F. 2020, A&A, 640, A51

(ref: Danielson_2013) Danielson, A. L. R., Swinbank, A. M., Smail, I., et al. 2013, Monthly Notices of the Royal Astronomical Society, 436, 2793

(ref: 2020_hcop_collis) Denis-Alpizar, O., Stoecklin, T., Dutrey, A., & Guilloteau, S. 2020, MNRAS, 497, 4276

(ref: SINFONI_1) Eisenhauer, F., Abuter, R., Bickert, K., et al. 2003, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 4841, Instrument Design and Performance for Optical/Infrared Ground-based Telescopes, ed. M. Iye & A. F. M. Moorwood, 1548–1561

(ref: Emig_2020) Emig, K. L., Bolatto, A. D., Leroy, A. K., et al. 2020, ApJ, 903, 50

(ref: CDMS_2016) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95

(ref: 1999_hcop_collis) Flower, D. R. 1999, MNRAS, 305, 651

(ref: h13cn_moldata_2004) Fuchs, U., Bruenken, S., Fuchs, G. W., et al. 2004, Zeitschrift Naturforschung Teil A, 59, 861

(ref: 1981_Gardner) Gardner, F. F. & Whiteoak, J. B. 1981, MNRAS, 194, 37P

(ref: Ginsburg_2018) Ginsburg, A., Bally, J., Barnes, A., et al. 2018, ApJ, 853, 171

(ref: Goldsmith_1999) Goldsmith, P. F. & Langer, W. D. 1999, The Astrophysical Journal, 517, 209

(ref: GonzalezAlfonso2012) González-Alfonso, E., Fischer, J., Graciá-Carpio, J., et al. 2012, A&A, 541, A4

(ref: co_moldata_1994) Goorvitch, D. 1994, ApJS, 95, 535

(ref: h13cop_moldata_2001) Gregersen, E. M. & Evans, Neal J., I. 2001, ApJ, 553, 1042

(ref: Haasler+2022) Haasler, D., Rivilla, V. M., Martı́n, S., et al. 2022, A&A, 659, A158

(ref: Harada+2022) Harada, N., Martı́n, S., Mangum, J. G., et al. 2022, ApJ, 938, 80

(ref: Harada+2021) Harada, N., Martı́n, S., Mangum, J. G., et al. 2021, ApJ, 923, 24

(ref: 2014Henkel) Henkel, C., Asiri, H., Ao, Y., et al. 2014, A&A, 565, A3

(ref: 1998Henkel) Henkel, C., Chin, Y. N., Mauersberger, R., & Whiteoak, J. B. 1998, A&A, 329, 443

(ref: 1985_Henkel) Henkel, C., Guesten, R., & Gardner, F. F. 1985, A&A, 143, 148

(ref: 2018Henkel) Henkel, C., Mühle, S., Bendo, G., et al. 2018, A&A, 615, A155

(ref: Holdship+2022) Holdship, J., Mangum, J. G., Viti, S., et al. 2022, arXiv e-prints, arXiv:2204.03668

(ref: Holdship+2021_SpectralRadex) Holdship, J., Viti, S., Martı́n, S., et al. 2021, A&A, 654, A55

(ref: 2022Huang) Huang, K. Y., Viti, S., Holdship, J., et al. 2022, arXiv e-prints, arXiv:2202.05005

(ref: Huang2023) Huang, K. Y., Viti, S., Holdship, J., et al. 2023, arXiv e-prints, arXiv:2303.12685

(ref: Humire+2022) Humire, P. K., Henkel, C., Hernández-Gómez, A., et al. 2022, A&A, 663, A33

(ref: Izumi2016) Izumi, T., Kohno, K., Aalto, S., et al. 2016, ApJ, 818, 42

(ref: Izzard_2004) Izzard, R. G., Tout, C. A., Karakas, A. I., & Pols, O. R. 2004, MNRAS, 350, 407

(ref: Jiang2011) Jiang, X., Wang, J., & Gu, Q. 2011, MNRAS, 418, 1753

(ref: 1998_Keene) Keene, J., Schilke, P., Kooi, J., et al. 1998, ApJL, 494, L107

(ref: co_iso_moldata_2000) Klapper, G., Lewen, F., Gendriesch, R., Belov, S. P., & Winnewisser, G. 2000, Journal of Molecular Spectroscopy, 201, 124

(ref: c18o_moldata_2001) Klapper, G., Lewen, F., Gendriesch, R., Belov, S. P., & Winnewisser, G. 2001, Zeitschrift Naturforschung Teil A, 56, 329

(ref: c17o_moldata_2003) Klapper, G., Surin, L., Lewen, F., et al. 2003, ApJ, 582, 262

(ref: Krips_2008) Krips, M., Neri, R., Garcı́a-Burillo, S., et al. 2008, The Astrophysical Journal, 677, 262

(ref: 1984Langer) Langer, W. D., Graedel, T. E., Frerking, M. A., & Armentrout, P. B. 1984, ApJ, 277, 581

(ref: 1990_Langer) Langer, W. D. & Penzias, A. A. 1990, ApJ, 357, 477

(ref: 1993_Langer) Langer, W. D. & Penzias, A. A. 1993, ApJ, 408, 539

(ref: hcop_moldata_2007) Lattanzi, V., Walters, A., Drouin, B. J., & Pearson, J. C. 2007, ApJ, 662, 771

(ref: Starburst99_2014) Leitherer, C., Ekström, S., Meynet, G., et al. 2014, ApJS, 212, 14

(ref: Starburst99_1999) Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999, ApJS, 123, 3

(ref: Leroy2015) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2015, ApJ, 801, 25

(ref: 2018Leroy) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2018, ApJ, 869, 126

(ref: 2019Loison) Loison, J.-C., Wakelam, V., Gratier, P., et al. 2019, MNRAS, 485, 5777

(ref: 2019_Mangum_Heart) Mangum, J. G., Ginsburg, A. G., Henkel, C., et al. 2019, ApJ, 871, 170

(ref: Martin_ALCHEMI_2021) Martı́n, S., Mangum, J. G., Harada, N., et al. 2021, A&A, 656, A46

(ref: 2019Martin) Martı́n, S., Muller, S., Henkel, C., et al. 2019, A&A, 624, A125

(ref: Meier_2015) Meier, D. S., Walter, F., Bolatto, A. D., et al. 2015, The Astrophysical Journal, 801, 63

(ref: Milam_2005) Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005, ApJ, 634, 1126

(ref: 2021_Mills) Mills, E. A. C., Gorski, M., Emig, K. L., et al. 2021, ApJ, 919, 105

(ref: CDMS_2005) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005a, Journal of Molecular Structure, 742, 215

(ref: 2005_Muller) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005b, Journal of Molecular Structure, 742, 215

(ref: CDMS_2001) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49

(ref: Muller2006) Muller, S., Guélin, M., Dumke, M., Lucas, R., & Combes, F. 2006, A&A, 458, 417

(ref: MullerSanchez2010) Müller-Sánchez, F., González-Martı́n, O., Fernández-Ontiveros, J. A., Acosta-Pulido, J. A., & Prieto, M. A. 2010a, ApJ, 716, 1166

(ref: 2010_TH2) Müller-Sánchez, F., González-Martı́n, O., Fernández-Ontiveros, J. A., Acosta-Pulido, J. A., & Prieto, M. A. 2010b, ApJ, 716, 1166

(ref: 2023_HCN_rates) Navarro-Almaida, D., Bop, C. T., Lique, F., et al. 2023, A&A, 670, A110

(ref: 1997Pagal) Pagel, B. E. J. 1997, Nucleosynthesis and Chemical Evolution of Galaxies

(ref: Papadopoulos_2010) Papadopoulos, P. P. 2010, ApJ, 720, 226

(ref: Papadopoulos_2011) Papadopoulos, P. P., Thi, W.-F., Miniati, F., & Viti, S. 2011, MNRAS, 414, 1705

(ref: 2020_Pasha) Pasha, I., Leja, J., van Dokkum, P. G., Conroy, C., & Johnson, B. D. 2020, ApJ, 898, 165

(ref: 2004Pasquali) Pasquali, A., Gallagher, J. S., & de Grijs, R. 2004, A&A, 415, 103

(ref: Rekola+2005) Rekola, R., Richer, M. G., McCall, M. L., et al. 2005, MNRAS, 361, 330

(ref: 2022_Rico_villas) Rico-Villas, F., González-Alfonso, E., Martı́n-Pintado, J., Rivilla, V. M., & Martı́n, S. 2022, MNRAS, 516, 1094

(ref: 2020_Rico-Villas) Rico-Villas, F., Martı́n-Pintado, J., González-Alfonso, E., Martı́n, S., & Rivilla, V. M. 2020, MNRAS, 491, 4573

(ref: Romano_Review_2022) Romano, D. 2022, A&ARv, 30, 7

(ref: 2019_Romano) Romano, D., Matteucci, F., Zhang, Z.-Y., Ivison, R. J., & Ventura, P. 2019, MNRAS, 490, 2838

(ref: Romano2017) Romano, D., Matteucci, F., Zhang, Z.-Y., Papadopoulos, P. P., & Ivison, R. J. 2017, Monthly Notices of the Royal Astronomical Society, 470, 401

(ref: 2013Rosenberg) Rosenberg, M. J. F., van der Werf, P. P., & Israel, F. P. 2013, A&A, 550, A12

(ref: 2015Roueff) Roueff, E., Loison, J. C., & Hickson, K. M. 2015, A&A, 576, A99

(ref: 1955_Salpeter) Salpeter, E. E. 1955, ApJ, 121, 161

(ref: 2002_Savage) Savage, C., Apponi, A. J., Ziurys, L. M., & Wyckoff, S. 2002, ApJ, 578, 211

(ref: hc18op_moldata_2004) Schmid-Burgk, J., Muders, D., Müller, H. S. P., & Brupbacher-Gatehouse, B. 2004, A&A, 419, 949

(ref: LAMDA_2005) Schöier, F. L., van der Tak, F. F., van Dishoeck, E. F., & Black, J. H. 2005, Astronomy & Astrophysics, 432, 369

(ref: 2023_Sipila) Sipilä, O., Colzi, L., Roueff, E., et al. 2023, A&A, 678, A120

(ref: 2014Sliwa) Sliwa, K., Wilson, C. D., Iono, D., Peck, A., & Matsushita, S. 2014, ApJL, 796, L15

(ref: 2013Sliwa) Sliwa, K., Wilson, C. D., Krips, M., et al. 2013, ApJ, 777, 126

(ref: 2014Spilker) Spilker, J. S., Marrone, D. P., Aguirre, J. E., et al. 2014, ApJ, 785, 149

(ref: Szucs2014) Szűcs, L., Glover, S. C. O., & Klessen, R. S. 2014, MNRAS, 445, 4055

(ref: 2019_Tang) Tang, X. D., Henkel, C., Menten, K. M., et al. 2019, A&A, 629, A6

(ref: hcop_tinti_moldata_2007) Tinti, F., Bizzocchi, L., Degli Esposti, C., & Dore, L. 2007, ApJL, 669, L113

(ref: 1985_TH2) Turner, J. L. & Ho, P. T. P. 1985, ApJL, 299, L77

(ref: Van_der_Tak_2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: LAMDA_2020) van der Tak, F. F. S., Lique, F., Faure, A., Black, J. H., & van Dishoeck, E. F. 2020, Atoms, 8, 15

(ref: 2020Viti) Viti, S., Fontani, F., & Jiménez-Serra, I. 2020, MNRAS, 497, 4333

(ref: 2019Viti) Viti, S., Fontani, F., Jiménez-Serra, I., & Holdship, J. 2019, MNRAS, 486, 4805

(ref: Wallstrom2016) Wallström, S. H. J., Muller, S., & Guélin, M. 2016, A&A, 595, A96

(ref: 2014Wang) Wang, J., Zhang, Z.-Y., Qiu, J., et al. 2014, ApJ, 796, 57

(ref: 2016Wang) Wang, J., Zhang, Z.-Y., Zhang, J., Shi, Y., & Fang, M. 2016, MNRAS, 455, 3986

(ref: 2009Wang) Wang, M., Chin, Y. N., Henkel, C., Whiteoak, J. B., & Cunningham, M. 2009, ApJ, 690, 580

(ref: 2010Wiescher) Wiescher, M., Görres, J., Uberseder, E., Imbriani, G., & Pignatari, M. 2010, Annual Review of Nuclear and Particle Science, 60, 381

(ref: 1994_Wilson) Wilson, T. L. & Rood, R. 1994, ARA&A, 32, 191

(ref: co_moldata_1997) Winnewisser, G., Belov, S. P., Klaus, T., & Schieder, R. 1997, Journal of Molecular Spectroscopy, 184, 468

(ref: 1996_Wouterloot) Wouterloot, J. G. A. & Brand, J. 1996, A&AS, 119, 439

(ref: 2008Wouterloot) Wouterloot, J. G. A., Henkel, C., Brand, J., & Davis, G. R. 2008, A&A, 487, 237

(ref: 2023_Yan) Yan, Y. T., Henkel, C., Kobayashi, C., et al. 2023, A&A, 670, A98

(ref: 2019_Yan) Yan, Y. T., Zhang, J. S., Henkel, C., et al. 2019, ApJ, 877, 154

(ref: co_moldata_collis) Yang, B., Stancil, P. C., Balakrishnan, N., & Forrey, R. C. 2010, ApJ, 718, 1062

(ref: 2020_Zhang) Zhang, J. S., Liu, W., Yan, Y. T., et al. 2020, ApJS, 249, 6

# Additional Moment 0 Maps

This appendix includes the remaining moment 0 maps generated using `CubeLineMoment`. The maps are provided in temperature units and cover the CMZ of NGC 253.

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-CO_10_CO_10_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(a\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-CO_21_CO_21_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(b\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-CO_32_CO_32_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(c\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-13CO_10_13CO_10_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(a\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-13CO_21_13CO_21_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(b\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-13CO_32_13CO_32_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(c\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-C18O_10_C18O_10_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(a\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-C18O_21_C18O_21_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(b\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-C18O_32_C18O_32_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(c\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-C17O_10_C17O_10_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(a\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-C17O_21_C17O_21_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(b\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-C17O_32_C17O_32_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(c\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HCN_10_HCN_10_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(a\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HCN_21_HCN_21_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(b\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HCN_32_HCN_32_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(c\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HCN_43_HCN_43_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(a\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HC15N_10_HC15N_10_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(b\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HC15N_21_HC15N_21_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(c\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HC15N_32_HC15N_32_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(a\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HC15N_43_HC15N_43_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(b\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HCOP_10_HCOP_10_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(c\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HCOP_21_HCOP_21_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(a\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HCOP_32_HCOP_32_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(b\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HCOP_43_HCOP_43_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(c\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-H13COP_10_H13COP_10_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(a\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-H13COP_21_H13COP_21_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(b\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-H13COP_32_H13COP_32_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(c\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-H13COP_43_H13COP_43_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(a\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HC18OP_10_HC18OP_10_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(b\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HC18OP_21_HC18OP_21_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |
| \(c\) |

|  |
|:---|
| ![image](images/Moment_Maps/KkmsM0_NGC253-HC18OP_32_HC18OP_32_moment0_widthscale1.0_sncut3.0_widthcutscale1.0.pdf) |

# Absorption at the TH2 Position

Within this section the effect of the ‘TH2’ region upon SSC-13\* and SSC-9\* are shown. This effect is shown both upon the affected spectra and column density ratio vs age diagrams.

## Affected Spectra

![](images/spectra/Comparison.pdf)

## Affected Abundance Ratio vs Age Diagrams

![](images/Abund_Ratio_Ages/N_H13COP__N_H13CN_.png)

![](images/Abund_Ratio_Ages/N_HCOP__N_HCN_.png)

# Additional Posterior Distributions

This Section contains the remaining Posterior distributions generated from the nested sampling of the `RADEX` modelling.

## SSC-1\*

![](images/Corners/CO_fill_SSC-1.pdf)

![](images/Corners/HCN_fill_SSC-1.pdf)

![](images/Corners/HCOP_fill_SSC-1.pdf)

## SSC-7\*

![](images/Corners/CO_fill_SSC-7.pdf)

![](images/Corners/HCN_fill_SSC-7.pdf)

![](images/Corners/HCOP_fill_SSC-7.pdf)

## SSC-9\*

![](images/Corners/CO_fill_SSC-9.pdf)

![](images/Corners/HCN_fill_SSC-9.pdf)

![](images/Corners/HCOP_fill_SSC-9.pdf)

## SSC-13\*

![](images/Corners/CO_fill_SSC-13.pdf)

![](images/Corners/HCN_fill_SSC-13.pdf)

![](images/Corners/HCOP_fill_SSC-13.pdf)

## SSC-14\*

![](images/Corners/CO_fill_SSC-14.pdf)

![](images/Corners/HCN_fill_SSC-14.pdf)

![](images/Corners/HCOP_fill_SSC-14.pdf)

# Optical Depths

This section contains the predicted optical depths of the best fitting `RADEX` model for each region for each transition.

| Transition | SSC-1\* | SSC-4\* |  SSC-7\*   | SSC\*-9 | SSC-13\* | SSC-14\* |
|:----------:|:-------:|:-------:|:----------:|:-------:|:--------:|:--------:|
|            |         |         |     CO     |         |          |          |
|   (1-0)    |  0.31   |  0.00   |    0.00    |  0.16   |   0.22   |   0.2    |
|   (2-1)    |  4.87   |  3.93   |    3.94    |  3.33   |   2.86   |   4.45   |
|   (3-2)    |  10.11  |  8.27   |    8.32    |  7.04   |   6.14   |   9.41   |
|            |         |         | $^{13}$CO  |         |          |          |
|   (1-0)    |  0.29   |  0.28   |    0.27    |  0.22   |   0.18   |   0.33   |
|   (2-1)    |  1.13   |  0.83   |    0.79    |  0.61   |   0.44   |   0.83   |
|   (3-2)    |  2.02   |  1.60   |    1.53    |  1.18   |   1.02   |   1.92   |
|            |         |         | C$^{18}$O  |         |          |          |
|   (1-0)    |  0.17   |  0.13   |    0.12    |  0.09   |   0.08   |   0.18   |
|   (2-1)    |  0.57   |  0.38   |    0.33    |  0.24   |   0.18   |   0.42   |
|   (3-2)    |  0.88   |  0.65   |    0.58    |  0.42   |   0.40   |   0.95   |
|            |         |         | C$^{17}$O  |         |          |          |
|   (1-0)    |  0.03   |  0.02   |    0.02    |  0.01   |   0.01   |   0.03   |
|   (2-1)    |  0.09   |  0.06   |    0.05    |  0.04   |   0.03   |   0.07   |
|   (3-2)    |  0.12   |  0.09   |    0.08    |  0.06   |   0.06   |   0.14   |
|            |         |         |    HCN     |         |          |          |
|   (1-0)    |  0.11   |  0.27   |    0.39    |  0.24   |   0.17   |   0.62   |
|   (2-1)    |  3.42   |  3.27   |    3.13    |  0.41   |   0.21   |   2.44   |
|   (3-2)    |  6.31   |  6.51   |    6.50    |  0.86   |   0.67   |   5.46   |
|   (4-3)    |  7.35   |  8.58   |    9.05    |  0.65   |   0.63   |   8.1    |
|            |         |         | H$^{13}$CN |         |          |          |
|   (1-0)    |  0.19   |  0.28   |    0.37    |  0.04   |   0.03   |   0.54   |
|   (2-1)    |  1.23   |  1.19   |    1.29    |  0.07   |   0.03   |   1.16   |
|   (3-2)    |  1.46   |  1.67   |    2.11    |  0.12   |   0.11   |   2.51   |
|   (4-3)    |  0.73   |  1.03   |    1.60    |  0.07   |   0.08   |   2.77   |
|            |         |         | HC$^{15}$N |         |          |          |
|   (1-0)    |  0.07   |  0.10   |    0.11    |   \-    |    \-    |   0.23   |
|   (2-1)    |  0.40   |  0.36   |    0.36    |   \-    |    \-    |   0.47   |
|   (3-2)    |  0.34   |  0.36   |    0.41    |   \-    |    \-    |   0.88   |
|   (4-3)    |  0.12   |  0.15   |    0.19    |   \-    |    \-    |   0.62   |

| Transition | SSC-1\* | SSC-4\* |     SSC-7\*      | SSC\*-9 | SSC-13\* | SSC-14\* |
|:----------:|:-------:|:-------:|:----------------:|:-------:|:--------:|:--------:|
|            |         |         |    HCO$^{+}$     |         |          |          |
|   (1-0)    |  3.30   |  1.40   |       1.39       |  4.47   |   4.28   |   4.26   |
|   (2-1)    |  13.49  |  8.23   |       8.35       |  17.43  |  16.79   |  17.75   |
|   (3-2)    |  25.03  |  16.73  |      17.38       |  32.77  |  31.46   |  36.67   |
|   (4-3)    |  31.8   |  24.72  |      26.86       |  42.83  |  40.88   |  57.43   |
|            |         |         | H$^{13}$CO$^{+}$ |         |          |          |
|   (1-0)    |  1.22   |  0.18   |       0.01       |  1.74   |   1.81   |   0.76   |
|   (2-1)    |  4.44   |  2.53   |       2.44       |  5.59   |   6.09   |   4.97   |
|   (3-2)    |  3.81   |  2.87   |       3.31       |  4.78   |   5.74   |   7.20   |
|   (4-3)    |  1.23   |  1.38   |       2.07       |  1.54   |   2.15   |   5.51   |
|            |         |         | HC$^{18}$O$^{+}$ |         |          |          |
|   (1-0)    |  0.67   |  0.07   |       0.04       |  0.64   |   0.67   |   0.34   |
|   (2-1)    |  2.17   |  1.30   |       1.33       |  1.58   |   1.74   |   2.64   |
|   (3-2)    |  1.13   |  1.02   |       1.31       |  0.59   |   0.70   |   2.52   |

# H39$\alpha$ Recombination Line Fitting

In Figure [44](#fig:H39_spectral_fitting), we show spectra in heliocentric velocity with respect to the H39$\alpha$ transition at a rest frequency of 106.73738 GHz for each of the SSC\*s. Other spectral emission that is present comes from He39$\alpha$ at a rest frequency of 106.78084 GHz which corresponds to $-$122.1 km s$^{-1}$ offset in velocity from H39$\alpha$, and C$_2$H$_3$CN at a rest frequency of 106.64139 GHz or offset by -269.6 km s$^{-1}$ with respect to H39$\alpha$. We’ve marked, with vertical dashed lines, the rest velocity velocities of He39$\alpha$ (cyan) and C$_2$H$_3$CN (purple) with respect to the fitted central velocity of H39$\alpha$ (pink) in the top panel.

We simultaneously fit Gaussian profiles to H39$\alpha$ and He39$\alpha$ emission, and for SSC-13\* C$_2$H$_3$CN emission as well. Gaussian fits to the emission are shown with dotted lines for H39$\alpha$ (pink), He39$\alpha$ (cyan) and C$_2$H$_3$CN (purple). The sum of the Gaussian fits is shown by a solid red line.

By combining Equations A4 and A14 from (cite: Emig_2020), the total ionizing photon rate expressed in terms of the flux density of the recombination line is

$$\begin{align*}
Q_0 = &\left(6.473\times 10^{51}~\mathrm{s}^{-1} \right) 
    \left(\frac{\int S_{\mathsf{n}}\,\mathrm{d}v}{100~\mathrm{mJy\, \text{km s}^{-1} }}\right)
    \left(\frac{1}{b_{\mathsf{n}+1}} \right) 
    \\ &
    \left( \frac{D}{4~\mathrm{Mpc}} \right)
    \left( \frac{\nu_{\mathsf{n}}}{100\,\mathrm{GHz}} \right)
    \left( \frac{ T_e }{ 10^4~\mathrm{K} } \right)^{0.667 - 0.034 \ln{(T_e\,/\,10^4\,\mathrm{K})} } 
\end{align*}$$ where $\int S_{\mathsf{n}}\,\mathrm{d}v$ is the integrated flux density of the RRL with principal quantum number $\mathsf{n}$, $b_{\mathsf{n}+1}$ is the LTE departure coefficient at $\mathsf{n}+1$, $D$ is the distance to the emitting region, $T_e$ is the electron temperature, and $\nu_{\mathsf{n}}$ is the rest frequency of the RRL. To derive the total ionizing photon rate at each SSC\*, we use the Gaussian area of the H39$\alpha$ emission or when necessary, the sum of the Gaussian areas of the H39$\alpha$ components. We assume a temperature of $T_e = 6000$ K and an LTE departure coefficient of $b_{\mathsf{n}+1} = 0.8$ (cite: Bendo_2015; 2021_Mills).

![](images/H39/H39a_SSC_fits.pdf)

[^1]: Jansky Fellow of the National Radio Astronomy Observatory

[^2]: https://cdms.astro.uni-koeln.de/

[^3]: <https://github.com/keflavich/cube-line-extractor>

[^4]: <https://johannesbuchner.github.io/UltraNest/>

</paper>

Write the methods card for this paper.