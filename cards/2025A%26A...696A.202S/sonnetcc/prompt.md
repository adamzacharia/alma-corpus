# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...696A.202S\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...696A.202S",
 "title": "ALMA-IMF: XVIII. The assembly of a star cluster: Dense N<SUB>2</SUB>H<SUP>+</SUP> (1─0) kinematics in the massive G351.77 protocluster",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Sandoval-Garrido, N. A.",
 "n_authors": 23,
 "arxiv_id": "2410.09843",
 "doi": "10.1051/0004-6361/202452589",
 "alma_projects_linked_by_archive": [
  "2013.1.01365.S",
  "2015.1.01273.S",
  "2017.1.01355.L"
 ]
}
```

Paper text:
<paper>
# ALMA-IMF XVIII: The assembly of a star cluster: Dense N$_2$H$^+$ (1-0) kinematics in the massive G351.77 protocluster

# Introduction

The fragmentation of molecular clouds leads to the formation of clumps. Regions where gas and dust are densely concentrated give rise to prestellar cores, where stars will later form (cite: lada). These regions, where the gas is actively turning into several young stars, are termed protoclusters, representing the gas-dominated bassinets of stellar clusters. These structures offer valuable insights into the initial stages of star cluster formation, enabling us to characterize their early evolution (cite: peretto; yueh; anualmotte; amy2018; rodrigo24).

![](Figure/1.png)

At the same time, filamentary structures are present in many star forming regions throughout the Galaxy. These have been shown to hold significant importance in both low and high mass star formation processes, presenting diverse and intricate morphologies (cite: john; Lee2014; Amy2015; amy2016; anualmotte; amy2018; hacar2023; hongli2023). Their formation can be triggered by different processes, such as shock fronts, cloud collisions, feedback, magnetic fields, gravitational instabilities, or global environmental effects (cite: amy2016; Louvet2016; montillaud; bonne; issac; shuo; hacar2023; hongli2023). More specifically, kinematics studies have revealed a powerful means to probe the physical processes at work within filaments coveting a range of line-masses. These processes include fragmentation, rotation, infall, magnetic instabilities, to name a few (cite: Henshaw; Manuel2014; liu2015; Amy2015; amy2016; amy2018.2; amy2018; hongli2019; Valentina19; Rodrigo21; Patricio2021; zhou2022; hacar2023; rodrigo24). Meanwhile, a strong link has been established between filamentary structures, dense cores, and protoclusters (cite: Schneider; Roberto2010; amy2016; amy2018; Plunkett; rodrigo24), leading to the discovery of connections between the kinematics and chemistry of dense cores and the gas surrounding the filamentary structure (cite: hacar2011; tafalla2014; amy2016; andre2019; hongli2020; kim2022; anirudh2023). Therefore, understanding the kinematic processes is crucial for characterizing the physical mechanisms associated with star formation over time. This understanding allows us to link mass, density, velocity gradients, and other properties associated with the formation of stars, with the characteristics of the cores found in these regions (cite: Nichol). These cores, which represent the sites where dust and gas will turn into individual or small numbers of stars through gravitational collapse, show strong relations with denser regions in molecular clouds. They are preferentially embedded within dense filamentary structures, which are influenced by gravitational effects and processes such as infall and magnetic fields (cite: amy2016; anualmotte; li23; hongli2023; pirogov23; kirk24; rodrigo24). Together, the above studies highlight the imperative need to connect the structures, namely filaments, within which cores and, ultimately, stars are born, to the cores themselves, including their kinematic properties.

In this context, the ALMA-IMF Large Program[^1] observed 15 massive $(2.5 - 33~\times10^3$ $\hbox{\rm M}_{\odot}$) and relatively nearby ($2 - 5.5$ kpc) protoclusters down to $\sim$ 2 kau resolution, with the main goal of understanding the origin of stellar masses. The ALMA-IMF Large Program utilized the 12m-array, 7m-array and Total Power (TP) antennas of the Atacama Large Millimeter/Submillimeter Array (ALMA), employing the 1.3 mm and 3 mm bands, providing observations of the continuum and spectral lines (cite: motte22; adam22; poetau1; brouillet; nony; poetau2; Nichol; danidiaz; towner; Armante; Melisse; Pierre; rodrigo24; Roberto; Fabien). A key aspect of the ALMA-IMF data-set is that the protoclusters were observed at approximately matched resolution and sensitivity. The 15 protoclusters were classified into different evolutionary stages, Young, Intermediate, and Evolved, based on their observed 1.3 mm and 3 mm fluxes, as well as the free-free emission at the H41$\alpha$ frequency (cite: motte22; Roberto). This classification takes into account the extent of dense gas impacted by local H ii regions (cite: motte22).

The 1.3 mm and 3 mm continuum images provide the possibility of detecting and analyzing cores and their key parameters, such as temperature, molecular composition, and masses, to name a few (cite: poetau1; brouillet; poetau2; Pierre; Fabien). These studies demonstrated that cores populations are influenced and characterized by the cloud formation process, their evolutionary stage, and the history of star formation. Additionally, they show that cores increase their masses during the protostellar phase through inflowing material, with massive cores exhibiting greater mass growth than their lower mass counterparts (cite: nony).

Simultaneously, spectral lines enable us to analyze core kinematics via e.g., DCN (cite: Nichol), demonstrating that this molecule can trace structures with different morphologies and complex velocity. These structures are more extended and filamentary in Evolved regions compared to Intermediate and Young regions, where the DCN emission appears more compact (see also (cite: Nichol)). Additionally, the emission from SiO and CO analyses have facilitated the detection of outflows in the protoclusters (cite: towner; nony), revealing that outflow properties are correlated with the total core mass and connections between outflow mass and the total mass of the protocluster.

Given the emergent nature of protoclusters, which are gas-dominated but also are main factories for the stellar content we can so readily observe in both our Galaxy and external ones, a precise gas tracer is crucial to delineate and comprehend the intricate gas dynamics during these early dense and cold phases. Moreover, a critical yet under-exploited aspect in the above studies is pinpointing the properties of the cold, dense extended gas outside the relatively compact cores. This gas is accessed here via the N$_2$H$^+$ (1-0) line at $\sim$ 93.173 GHz.

More thorough research in laboratories and nearby star-forming regions has revealed N$_2$H$^+$ (1-0) emissions occurring at seven different frequencies (cite: green74; turner74; tadeus75; Caselli95; Ivanov), resulting in hyperfine structure in the spectrum. N$_2$H$^+$ (1-0) has critical densities between $\sim~6.1~\times~10^4$ cm$^{-3}$ and $2.0~\times~10^4$ cm$^{-3}$ at kinetic temperatures from 10 K to 100 K (cite: shirley2015). N$_2$H$^+$ is formed during the gas-phase reactions from H$_3^{+}$ + N$_2$ $\rightarrow$ N$_2$H$^+$ + H$_2$ at temperatures of 20 K (cite: bergin2001; jorgensen2004; Bergin; hoff2017; Naiping2018) where it is mostly resistant to freezing onto dust grains. However, at temperatures above 20 K (but see (cite: Dale) for the theoretical side, and (cite: Tatematsu); (cite: amy2016); (cite: Valentina19); and (cite: Hacar2024) for the observational side), it can be destroyed by CO molecules, which are desorbed from the dust grains, leading to reactions such as N$_2$H$^+$ + CO $\rightarrow$ HCO$^{+}$ + N$_2$. Alternatively, it can be destroyed by free electrons in H ii regions, resulting in reactions like N$_2$H$^+$ + $e^{-}$ $\rightarrow$ N$_2$ + H or HN + N (cite: jorgensen2004; Patricio2012; tobin2013; Lippok2013; hoff2017). These characteristics make N$_2$H$^+$ (1-0) a reliable tracer for dense and cold gas. It allows us to investigate the initial stages in star-forming regions and understand the chemistry, kinematics, and dynamics of filamentary structures, protoclusters, and cores (cite: Daniel2005; fontani2006; Gemma2011; Storm; Pety; Chen2019; Schwarz2019; Valentina19; Rodrigo21; Elena22).

An important analysis that can be applied to the velocity structure of the dense gas derived from the N$_2$H$^+$ (1-0) line emission is the study of intensity-weighted Position-Velocity (PV) diagrams, utilizing integrated intensity, velocities, and positions (cite: Valentina19; Rodrigo21; rodrigo24). These diagrams enable the characterization of important kinematic patterns that can provide insight into rotation, infall, cloud-cloud collisions, or transversal velocity gradients within filaments (cite: Henshaw; Manuel2014; amy2016; montillaud; Rodrigo21; Elena22; rodrigo24). Additionally, PV diagrams provide a valuable tool for characterizing velocity gradients, measuring timescales, and estimating mass inflow rates at small scales, enabling us to link these characterizations to core scales. Notably, recent research of the G353.41 protocluster, one of the ALMA-IMF targets, has revealed correlations between cores and velocity structures observed in PV space at small scales. Meanwhile, large-scale analysis of the velocity structures on PV space suggest an ongoing infalling process (cite: rodrigo24). This approach allow us to associate these characterizations with core evolution, and infer the behavior and timescales of future processes.

The high-mass star-forming region G351.77-0.53 (IRAS 17233-3606) is a filamentary infrared dark cloud (IRDC) (see Fig. [1](#fig:rgbimage)) located at $\sim\,2\,\pm\,0.14$ kpc and whose estimated mass is $\sim\,10200$ $\hbox{\rm M}_{\odot}$ for the entire filament within an area of 11 pc$^2$ (cite: Simon). Recent observations of several molecular tracers such as CO, HCO$^+$, CH$_3$OH, CH$_3$CN, SiO, $^{13}$CO, C$^{17}$O, C$^{18}$O, H$_2$O and H$_2$ have shown a variety of physical processes along the filament. These processes encompass fragmentation into different clumps and the generation of turbulence, attributed to ongoing star formation activity within the region, magnetic fields, and gravitational effects produced by the ongoing high-mass star formation (cite: Leurini2011_1; Naiping2018; Leurini2019; Sabatini2019). Intriguingly, it has been estimated that the star formation efficiency and the star formation rate along the filament is extremely low compared to the mass reservoir (see above) and low compared to local clouds, and compared specifically to Orion A (cite: Simon).

![image](Figure/2_1.png) ![image](Figure/2_2.png)

Focusing on the most prominent clump, which we will henceforth refer to as the G351.77 protocluster, it is classified as being in an Intermediate evolutionary stage compared to other ALMA-IMF protoclusters (see above). An UCH ii region is located at its center (cite: motte22; Roberto), and the presence of clear outflows, sometimes bipolar, indicating vigorous and ongoing star formation (cite: Leurini2008; Zapata2008; Leurini2009; Leurini2011_2; Leurini2013; Leurini2014; Klaassen; Antyufeyev; towner). These outflows are closely linked to Young Stellar Objects (YSOs). Additionally, an evident velocity gradient is observed in several tracers, revealing two different velocity components (cite: Leurini2019). This gradient is also observed in some tracers from the ALMA-IMF survey such as DCN (3-2), and C$^{18}$O (2-1) (cite: Nichol). Furthermore, eighteen cores have been cataloged within the G351.77 protocluster, with masses from 0.5 $\hbox{\rm M}_{\odot}$ to 36.5 $\hbox{\rm M}_{\odot}$(cite: Fabien). An analysis of CH$_3$OCHO has identified five sources in the central part of the protocluster, 3 of which have been classified as hot cores (cite: Melisse). These hot cores may explain the lack of N$_2$H$^+$ (1-0) emission in the center of the protocluster (see Fig. [2](#fig:snrmap)). Moreover, kinematic analysis at scales $< 1$ kau in the central zone of the protocluster reveals the existence of disks with signs of outflows, infall, and rotation (cite: Zapata2008; Beuther).

In this paper, we focus on the kinematics of dense and cold gas within the massive G351.77 protocluster using the N$_2$H$^+$ (1-0) spectral line emission. To achieve this, we image the observations obtained from the 12m-array and 7m-array configurations for the ALMA-IMF Large Program, feathering them with TP observations, as explained in § [2](#sec:data). We employ specialized software to fit the individual spectra, enabling precise and meticulous characterization of the kinematics and spectral properties, a process detailed in § [3](#sec:line-fitting-process). We estimate column densities, relative abundances, and masses of N$_2$H$^+$ (1-0) in § [4](#sec:column-density-and-masses). Additionally, we analyze PV diagrams to characterize structures at both small and large scales in order to comprehend the physical processes occurring within the protocluster in § [5](#sec:kinematics-analysis). We present the discussion of the results, proposing potential physical scenarios in § [6](#sec:discussion). Finally, in § [7](#sec:conclusion) we present our conclusions.

# Data

We analyze the N$_2$H$^+$ (1-0) observations of the G351.77 protocluster in the 3 mm spectral band, observed by the 12m-array, 7m-array and TP configurations obtained from the ALMA-IMF Large Program (cite: motte22). Our data has a maximum spatial resolution of $\sim$ 4000 au and a spectral resolution of 0.23 $\rm km\,s^{-1}$. The beam sizes are (2.3$''$  $\times$ 2.1$''$), (16.9$''$ $\times$ 10.1$''$), and (69.6$''$ $\times$ 69.6$''$) for the 12m-array, 7m-array, and TP, respectively.

## N$_2$H$^+$ data imaging

The data imaging process was performed using CASA 6.2 (cite: CASA) along with the ALMA-IMF data pipeline[^2]. Initially, we imaged the 12m-array data to determine the optimal parameter settings to achieve the highest quality results. Among the different parameters tested within the *tclean*[^3] CASA task, we explored different imaging results by varying: *threshold*, *deconvolver*, *pbmask*, *pblimit* and *scales*. These parameter values [^4] were selected based on the analysis of the residuals, model, and the image returned after each imaging process, in a way that minimized the residuals in the final product. Subsequently, we applied the same parameter values to combine the 12m-array and 7m-array data with *tclean* to increase the Fourier coverage (7M12M, henceforth). This combination produces artifacts such as peaks and bowls of intensity around the edges. These appear to be due to the differing UV-plane coverage of the 12m-array versus 7m-array, as well as the low signal near the edges. However, by increasing the pblimit value from 0.05 to 0.2 for this product – the later of which is a commonly used threshold in similar ALMA datasets – these artifacts are no longer produced, as the edge regions with lower sensitivity are effectively excluded.

Continuum subtraction was accomplished using the CASA task *imcontsub*. This task uses the channels free of line emission to generate a continuum model, which is subtracted from the line emission channels. This process yields the continuum-subtracted 7M12M data.

As a final step, we employed the CASA task *feather* to combine the 7M12M continuum subtracted data with the TP data to recover the extended line emission. Here we define the 7M12M continuum subtracted data as the high resolution data, and the TP as the low resolution data. Finally, we obtain a fully combined spectral cube (data-cube, see Fig. [18](#fig:channelmap)), with a spectral resolution of 0.23 $\rm km\,s^{-1}$, and whose size final synthesized beam is 2.3$''$ $\times$ 2.1$''$ and a Beam-Position-Angle (BPA) of 89$^{\circ}$. The noise and signal-to-noise ratio (S/N) map of our imaged data are shown in Fig. [2](#fig:snrmap). The mean rms value across the entire map is $\sim$ 0.66 K, whereas the mean value in regions with S/N \> 9 is $\sim$ 0.40 K.

## Other ALMA-IMF data

In our analysis, we use the smoothed *getsf* (cite: Menshchikov) core catalog from (cite: Fabien), derived from the continuum images of the 1.3 mm band (cite: adam22). We also utilize the core kinematics, integrated intensity map, and mean velocity map obtained from the DCN (3-2) spectral line fits from the 12m-array (cite: Nichol). Further, we make use of the integrated intensity map and mean velocity map of H$_2$CO (3-2) derived from the 12m-array observations as part of the spectral setup of the ALMA-IMF Large Program (cite: motte22). Additionally, we use an intermediate product of the H$_2$ column density map of G351.77 at 6$''$ resolution, derived from a combination of 1.3 mm band, SOFIA/HAWC+ (53 $\mu$m, 89 $\mu$m, and 214 $\mu$m), APEX/SABOCA (350 $\mu$m) and APEX/LABOCA (870 $\mu$m) observations (cite: Pierre). Although the resolution of the final product of the H$_2$ column density is 2.5$''$, we use this intermediate product in order to reduce the uncertainties of our estimations that could be produced by the combination of the data of H$_2$ and from our fits. Moreover, this approach ensures a more uniform and reliable analysis by minimizing artifacts that may appear in maps at higher resolution and allows the calculation of one representative value of the relative abundance for the protocluster (Dell’Ova, private communication 2024).

# Line fitting procedure

Since our main goal in this paper is to analyze the fine and large scale protocluster kinematics of dense gas, we require the use of spectral line fitting to retrieve the radial velocity field. Moreover, the line fitting of N$_2$H$^+$ (1-0) hyperfine structure provides additional parameters of interest, i.e. the optical depth ($\tau$) and excitation temperatures (T$_{\rm ex}$, see below). The first examination of the data-cube immediately reveals that multiple velocity components exist over a significant number of spectra, consistent with previous research (cite: Leurini2019). Hence, we adopt an iterative approach to line fitting, as described in detail below.

We only fit spectra with S/N $>$ 9. This approach stems from our experimental findings, which reveal that spectra with a S/N $<$ 9 are inadequately fitted, yielding high uncertainties in the returned parameters (see Fig. [2](#fig:snrmap) and § [9](#sec:experiment)). We ultimately fit the spectral cube with 2-velocity-components when possible (driven mainly by S/N considerations, see § [3.2](#sec:two-component-fit)) and 1-velocity-component when the spectra are either relatively simple or the noise precludes more detailed velocity decomposition. To accomplish this fitting, we begin with a 1-velocity-component fit (see Fig. [\[fig:specwellfited1comp\]](#fig:specwellfited1comp)) and then with the 2-velocity-components fit (see Fig. [4](#fig:specwellfited2comp)), which are independent. We refer to these two relatively “raw” fits as the First Fitting Procedures (FFPs). We then analyze the S/N of the decomposed spectra to identify where we have reliable 2-velocity-components fits; where we do not, we adopt the 1-velocity-component fit for the spectrum being analyzed (see § [3.3](#sec:best-fit-and-final-model) and Fig. [5](#fig:map_components)).

+:-------------:+:----------------------:+:----------:+:--------------------------------------:+:-----------------------------------------:+:----------------------:+:--------:+:--------------------------------------:+:-----------------------------------------:+
|               |                        |            |                                        |                                           |                        |          |                                        |                                           |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
| Parameters    | T$_{\rm {ex,1}}$ \[K\] | $\tau_{1}$ | V$_{\rm {LSR,1}}$ \[$\rm km\,s^{-1}$\] | $\sigma_{\rm {v,1}}$ \[$\rm km\,s^{-1}$\] | T$_{\rm {ex,2}}$ \[K\] | $\tau_2$ | V$_{\rm {LSR,2}}$ \[$\rm km\,s^{-1}$\] | $\sigma_{\rm {v,2}}$ \[$\rm km\,s^{-1}$\] |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
|               |                        |            |                                        |                                           |                        |          |                                        |                                           |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
|               | Single velocity component                                                                                                |                                                                                                                        |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
|               |                        |            |                                        |                                           |                        |          |                                        |                                           |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
| FFP guesses   | 20.0                   | 1.0        | -3.0                                   | 1.0                                       |                        |          |                                        |                                           |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
| Final guesses | 12.4                   | 3.64       | -3.77                                  | 1.0                                       |                        |          |                                        |                                           |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
| Limits        | (2.73, 100)            | (0, 100)   | (-13, 3)                               | (0, 6)                                    |                        |          |                                        |                                           |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
|               |                        |            |                                        |                                           |                        |          |                                        |                                           |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
|               | First-velocity-component                                                                                                 | Second-velocity-component                                                                                              |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
|               |                        |            |                                        |                                           |                        |          |                                        |                                           |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
| FFP guesses   | 20.0                   | 1.0        | -5.0                                   | 1.0                                       | 20.0                   | 1.0      | -2.0                                   | 1.0                                       |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
| Final guesses | 9.22                   | 4.60       | -5.0                                   | 0.83                                      | 9.0                    | 7.4      | -2.6                                   | 0.66                                      |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+
| Limits        | (2.73, 100)            | (0, 100)   | (-13, 3)                               | (0, 6)                                    | (2.73, 100)            | (0, 100) | (-13, 3)                               | (0, 6)                                    |
+---------------+------------------------+------------+----------------------------------------+-------------------------------------------+------------------------+----------+----------------------------------------+-------------------------------------------+

Table notes: The “Single velocity component” shows the guesses and limits used in the 1-velocity-component fit. The “First-velocity-component” and “Second-velocity-component” show the guesses and limits used in the 2-velocity-component fit. The FFP guesses represent the initial guesses used in the first fitting process for both 1- and 2-velocity-component fits. The Final guesses are averaged of the parameters obtained from previous fits, used to improve the models in both 1- and 2-velocity-component fits. The Limits represent the range of values within which the returned parameters will lie.

![](Figure/3.png)

Here we use the N$_2$H$^+$ (1-0) line model *n2hp_vtau*[^5] from PySpecKit[^6] (cite: PySpecKit11; PySpecKit22) to fit the cube (cite: Elena; Valentina19; Rodrigo21). This model is an LTE model, whose spectroscopic predictions come from known molecular data under the LTE assumption, such as rest frequencies and hyperfine structures. This procedure returns 4 parameters per velocity component: excitation temperature (T$_{\rm ex}$, see Fig. [21](#fig:temp_map)), optical depth ($\tau$, see Fig. [22](#fig:tau_map)), centroid velocity (V$_{\text{LSR}}$), and line width ($\sigma_{\rm v}$), each representing a measurement for the entire spectrum.

To fit the data-cube, four different guesses must be entered to initialize PySpecKit. In addition to the guesses, each parameter is assigned both a lower and upper limit value, defining the range within which the final fitted values will lie. In Table [\[tab:guesses_table\]](#tab:guesses_table), we show the guess and limit values for each parameter used in the FFP and in the final fit. After the fitting process, PySpecKit returns the model spectra, parameter values (see above), and associated parameter errors. Finally, applying methods in order to define the best fit for each spectra we merge the 1- and 2-velocity-components fits into one model cube (see § [3.3](#sec:best-fit-and-final-model), Fig. [6](#fig:momentmaps0), and Fig. [7](#fig:velocity_map) for example maps of the spectral fits, including the integrated intensity, mean velocity and the line width, and also Fig. [21](#fig:temp_map) and Fig. [22](#fig:tau_map) for examples of excitation temperature maps and optical depth maps). In the analysis in § [3.4](#sec:bluest-and-reddest-velocity-component), we define the two main velocity components of the protocluster (see Fig. [6](#fig:momentmaps0) and Fig. [7](#fig:velocity_map)), where we also perform a careful measurement of the V$_{\text{LSR}}$ of G351.77 where $<$V$_{\rm LSR}>~=~-3.843~\pm~0.001~\rm km\,s^{-1}$. In the text that follows, we present more details of the procedures outlined above, and we will show in § [3.4](#sec:bluest-and-reddest-velocity-component) that there is a continuity between the 1- and 2-velocity-component fits except in some locations presenting jumps.

## One-velocity-component fit

As an initial step, we employed a straightforward approach by fitting a 1-velocity-component across the entire spectral cube (see Fig. [\[fig:specwellfited1comp\]](#fig:specwellfited1comp)), entering the “FFP guesses” and “Limits” listed in Table [\[tab:guesses_table\]](#tab:guesses_table). Since our goal is to achieve the best possible fit, we utilize the average of the parameters returned throughout the cube from the FFP to refine the input guesses, which are then applied in a new fitting process. New guesses are then estimated from these new fitting process. This is repeated until no variations are observed in the averages obtained for each parameter compared to previous fits. We define these parameter averages as “Final guesses” (see Table [\[tab:guesses_table\]](#tab:guesses_table)). In this way, we provide PySpecKit values that are more representative of the data in order to produce the final model with a 1-velocity-component fit.

The FFP reveals an issue produced by spectra with $\tau\,<\,1$, which generates misleading estimations of T$_{\rm ex}$, whose values lie between 80 K $\lesssim$ T$_{\rm ex}\,<\,10^4$ K. This issue also occurs in the 2-velocity-components fitting. This problem arises due to the intrinsic degeneracy when fitting a single transition, which makes it impossible to measure both T$_{\rm ex}$ and $\tau$ from the same transition when $\tau~<~1$. Since we aimed to preserve most of the data and use reliable values for each parameter, we address this issue by refitting the spectra with $\tau\,<\,1$ and assigning them a constant T$_{\rm ex}$ value (cite: Caselli1; Caselli2).

Thus, spectra with $\tau\,<\,1$ are selected and separated from the cube to be re-fitted by a 1-velocity-component with a constant T$_{\rm ex}$ value, whose value comes from averaging T$_{\rm ex}$ from spectra with $\tau\,>\,1$. The re-fitted spectra use the “Final guesses” listed in Table [\[tab:guesses_table\]](#tab:guesses_table). However, the T$_{\rm ex}$ limits are now 2.73 K to 12.4 K. At the end of this process, we obtain two separate spectral models and parameters from the spectra with $\tau \geq
1$, and from the spectra with $\tau\,<\,1$ for the 1-velocity-component fit, which correspond to the 64% and 36% of the spectra, respectively. As a final step in the fitting process, we merge these two spectral models and parameters, creating a final spectral model entirely fitted by the 1-velocity-component, with its corresponding parameters and associated errors.

Although this does not occur in every case, some spectra with $\tau~\gg~1$ ($\tau$ $\gtrsim~40$) exhibit a “flat-top” effect at the intensity peak of the hyperfine structures in the model spectra. These spectra have errors in $\tau$ exceeding 100% and are excluded from the analysis. However, this occurs in less than 1% of the spectra, where the median value of $\tau\,\sim~3$. The same issue arises in the 2-velocity-component fits with similar frequency.

## Two-velocity-component fit

Upon examining the spectral cube, we notice the presence of two distinct velocity components in several spectra. Consequently, a 1-velocity-component fit is not sufficient to describe the global kinematics of the data. This forces us to fit 2-velocity-components in the spectral cube (see Fig. [4](#fig:specwellfited2comp)), entering the “FFP guesses” and “Limits” for each velocity component, listed in Table [\[tab:guesses_table\]](#tab:guesses_table). In a similar way as we made in § [3.1](#sec:one-component-fit), and in order to get the best fit, we derive new guesses measuring the average of the values returned for each parameter of each component throughout the cube, until we obtain the “Final guesses” (see Table [\[tab:guesses_table\]](#tab:guesses_table)), which are used to generate the final model with a 2-velocity-components fit.

![image](Figure/4_1.png) ![image](Figure/4_2.png)

As we mentioned in § [3.1](#sec:one-component-fit), spectra with $\tau\,
<\,1$ produce bad estimations of the T$_{\rm ex}$. Therefore, spectra with $\tau\,<\,1$ are selected and separated to be re-fitted. However, because we are fitting two-velocity-components, it is necessary to separate the spectra into three different conditions (see Table [1](#tab:new_tex_limits)) to assign them a constant T$_{\rm ex}$ value. These constant values come from averaging T$_{\rm ex}$ of spectra with $\tau\,\geq\,1$ of each component. The re-fitted spectra will use the same “Final guesses” listed in Table [\[tab:guesses_table\]](#tab:guesses_table), while the T$_{\rm ex}$ limits depend on the the opacity values (see Table [1](#tab:new_tex_limits)).

|        |                                    |                  |                  |
|:------:|:----------------------------------:|:----------------:|:----------------:|
|        |                                    |                  |                  |
| Number |             Condition              | T$_{ex,1}$ \[K\] | T$_{ex,2}$ \[K\] |
|        |                                    |                  |                  |
|   1    | $\tau_{1} < 1$ & $\tau_{2} \geq 1$ |   (2.73, 9.22)   |   (2.73, 100)    |
|   2    | $\tau_{1} \geq 1$ & $\tau_{2} < 1$ |   (2.73, 100)    |   (2.73, 9.0)    |
|   3    |  $\tau_{1} < 1$ & $\tau_{2} < 1$.  |   (2.73, 9.22)   |   (2.73, 9.0)    |

: Conditions and T$_{\rm ex}$ limits for the re-fit of 2-velocity-components.

Table notes: New T$_{\rm ex}$ limits applied under each condition for the re-fit of the 2-velocity-components, based on $\tau$ values, in order to avoid poor T$_{\rm ex}$ estimations.

The refitting process produces new $\tau$ estimations for spectra with $\tau$ $\approx$ 1 where the value can drop below 1. Specifically, this occurs in 5% of the total spectra when applying conditions 1 and 2 (see Table [1](#tab:new_tex_limits)). As we already mentioned, these $\tau$ values generate bad estimations of T$_{\rm ex}$. It is necessary to select and separate the re-fitted model spectra under two new conditions:

1.  Model returned from the condition number 1 with $\tau_{2}\,<\,1$.

2.  Model returned from the condition number 2 with $\tau_{1}\,<\,1$.

These spectra are re-fitted again, using the “Final guesses” and “Limits” of the Table [\[tab:guesses_table\]](#tab:guesses_table). However, the T$_{\rm ex}$ limits are now T$_{\rm ex}$ = (2.73 K, 9.22 K) for the condition “a” and T$_{\rm ex}$ = (2.73 K, 9.0 K) for the condition “b”. The separation of the cube into different conditions to re-fit the spectra with $\tau\,<\,
1$ provides us with the security that all spectra have greater freedom in order to estimate $\tau$ values and obtain good or more reliable T$_{\rm ex}$ values in each spectrum.

At the end of this process, we obtain six separate model spectra and parameter cubes fitted by 2-velocity-components. One of these correspond to the model spectra with $\tau~\geq~1$, which account for 38% of the total spectra. The remaining five models spectra are derived from refitting process: conditions 1, 2, and 3 (see Table [1](#tab:new_tex_limits)) represent 30%, 15%, and 11% of the final spectra, respectively, while the condition “a” and “b” (see above) contribute 3% and 2% to the final spectra, respectively. As a final step in this process, we merge these six spectral models and parameter cubes, creating a final spectral model entirely fitted by 2-velocity-components (see Fig. [6](#fig:momentmaps0)). We refer to each component as the “First-velocity-component” and the “Second-velocity-component”, with their centroid velocities being the lowest and highest, respectively, and with their parameters and associated errors (see Fig. [4](#fig:specwellfited2comp)).

## Best fit and merging models

In § [3.1](#sec:one-component-fit) and § [3.2](#sec:two-component-fit), we described the complete fitting process of the data, fitting the whole cube with 1- and 2-velocity-components. However, our spectral cube shows spectra where we can identify just 1-velocity-component (see Fig. [\[fig:specwellfited1comp\]](#fig:specwellfited1comp)), spectra where we can identify 2-velocity-components (see Fig. [4](#fig:specwellfited2comp)), and spectra where it is not possible to make a clear identification by eye. Furthermore, it is necessary to determine which fit (1- or 2-velocity-components) is better for each spectra to simplify our analysis and to recover reliable kinematic information about the protocluster. Thus, we devised a method to determine if 1- or 2-velocity-components is appropriate for each spectrum based on S/N criteria and the parameters associated with each spectrum, specifically the line width.

![](Figure/5.png)

In order to determine if the spectrum is better fitted by 1- or 2-velocity-components we:

1.  Check the $\sigma_v$ value in the spectral model fitted by 2-velocity-components. From inspection of the spectral model fitted by 2-velocity-components, we find some “false component” spectra without emission whose $\sigma_v$ is equal to 0 (see Fig. [23](#fig:specdef1comp_1)). This implies that all spectra with these characteristics are better characterized by 1-velocity-component fit (see Fig. [23](#fig:specdef1comp_1)).

    ![image](Figure/6_1.png) ![image](Figure/6_2.png) ![image](Figure/6_3.png)

2.  Measure the S/N of the velocity component with the lower intensity in the 2-velocity-component fit. Deeper inspection shows that some additional velocity components have intensities similar to noise values. So, if the peak intensity is lower than five times the noise measured in that spectrum from the data-cube, the 1-velocity-component fit is adopted. Thus, we ensure the reliability of the additional velocity component (see Fig. [24](#fig:specdef1comp_2)).

Additionally, all fitted spectra with errors higher than five times the median error estimated for the centroid velocity ($\sim$ 0.2 $\rm km\,s^{-1}$) are removed for the kinematic analysis (see § [5](#sec:kinematics-analysis)). For the estimation of column density (see § [4](#sec:column-density-and-masses)), spectra with errors exceeding 10% for the line width, 30% for T$_{\rm ex}$, and 30% for $\tau$ are also excluded. These thresholds were estimated considering twice the median error measured for each parameter. Furthermore, we find that 95% of the spectra have error within the following ranges: \[0.05 K, 1.78 K\] for T$_{\rm ex}$, \[0.4, 9.7\] for $\tau$, \[0.007 $\rm km\,s^{-1}$, 0.26 $\rm km\,s^{-1}$\] for the centroid velocity, and \[0.1 $\rm km\,s^{-1}$, 0.17 $\rm km\,s^{-1}$\] for the line width.

After applying these criteria, we obtain spectra well-fitted by 1- and 2-velocity-components (see Fig. [4](#fig:specwellfited2comp)). All these spectra are merged in order to create a final spectral model composed of both 1- and 2-velocity-components (see Fig. [5](#fig:map_components)). Most of the spectra fitted by 2-velocity-components are located in internal regions toward highest integrated intensities (see Fig. [6](#fig:momentmaps0)).

## Blue and Red velocity component

From the four parameters returned by PySpecKit of the N$_2$H$^+$ (1-0) spectra, the centroid velocity is the one that has the lowest uncertainties with median values of 0.034 $\rm km\,s^{-1}$ (cases with higher errors than five times the median value are excluded, see § [3.3](#sec:best-fit-and-final-model)), which gives us information about the radial velocity distributions of the regions where we observe line emission. The general centroid velocity distributions that we derive are plotted in Fig. [3](#fig:histogram_veldistribution), which we discuss in detail below.

The mean velocity map from the model in the top panel of Fig. [7](#fig:velocity_map), shows various interesting features. One of these includes indications of a large-scale velocity gradient (VG) that is almost perpendicular ($\sim$ 83 $^{\circ}$) to the direction in which the molecular cloud filament that hosts the protocluster extends (which we call the Mother Filament, see Fig. [1](#fig:rgbimage)).

On the other hand, we observe jumps between the velocities of the spectra with 1- and 2-velocity-components that reaches velocities of up to $\sim$ 4 $\rm km\,s^{-1}$ (see top panel of Fig. [7](#fig:velocity_map)). This is an effect produced by averaging the two centroid velocities in spectra with 2-velocity-components, so is an artificial velocity averaging effect rooted in the complex motions in G351.77. Indeed, in the bottom two panels of Fig. [7](#fig:velocity_map), we separate the measured velocities and assign them to either a Blue- or Red-velocity component. To make this somewhat arbitrary but necessary velocity separation, we define the cut-off velocity as the midpoint based on the velocity distributions of the First-velocity-component and the Second-velocity-component (see Fig. [3](#fig:histogram_veldistribution)). We achieve this by applying the following simple relation:

$$\begin{equation}
<\text{V}_{\rm LSR,1}> + \hspace{0.1cm} X \times \sigma_{\rm v_{\rm LSR,1}} = \hspace{0.1cm} <\text{V}_{\rm LSR,2}> - \hspace{0.1cm} X \times \sigma_{\rm v_{\rm LSR,2}}\text{,}
\label{eq:vel_limit_eq}
\end{equation}$$

where $<\text{V}_{\rm LSR,1}>$ and $<\text{V}_{\rm LSR,2}>$ are the averaged centroid velocities of the First- and Second-velocity-component, respectively, $\sigma_{\rm v_{\rm LSR,1}}$ and $\sigma_{\rm v_{\rm LSR,2}}$ are the standard deviations of the centroid velocities in the First- and Second-velocity-component, respectively, and $X$ represents the cut-off value used as the middle\

![image](Figure/7_1.png) ![image](Figure/7_2.png) ![image](Figure/7_3.png)

point, normalized by the standard deviations of the centroid velocity distributions.

Applying Eq. [\[eq:vel_limit_eq\]](#eq:vel_limit_eq) we obtain a $X=0.025$. This value allows us to separate the centroid velocity distribution of the 1-velocity-component fit into two parts and combine the measurements with the First- and the Second-velocity-component. We define “Blue-velocity component” as the merger of all the spectra from the First-velocity-component and the spectra from the 1-velocity-component fit with centroid velocity $< 0.025~\rm km\,s^{-1}$, see middle panel of Fig. [7](#fig:velocity_map). Similarly, the “Red-velocity component” is the merger of all the spectra from the Second-velocity-component and the spectra from the 1-velocity-component fit with centroid velocity $>\,0.025~\rm km\,s^{-1}$ (see bottom panel of Fig. [7](#fig:velocity_map)).

# Column Density, mass, and N$_2$H$^+$ relative abundance

The spectral line fitting of N$_2$H$^+$ (1-0) shown in § [3](#sec:line-fitting-process) provides relevant information about the N$_2$H$^+$ (1-0) spectra, specifically excitation temperature (T$_{\rm ex}$), optical depth ($\tau$), and line width ($\sigma_v$). These parameters enable the estimation of column density maps of N$_2$H$^+$, N(N$_2$H$^+$), calculated by Eq. [\[eq:column-density\]](#eq:column-density) (see Fig. [8](#fig:columndensity)), and the mass of N$_2$H$^+$ in the protocluster, M(N$_2$H$^+$), calculated by Eq. [\[eq:n2hp-mass\]](#eq:n2hp-mass), which can be determined for both the Blue- and the Red-velocity component (see § [4.1](#sec:n2h+_column_density)). Additionally, the column density map of H$_2$, N(H$_2$), provided by (cite: Pierre), shown in Fig. [9](#fig:h2map), gives us the opportunity to estimate the N$_2$H$^+$ relative abundances, X(N$_2$H$^+$), in the protocluster (see Fig. [10](#fig:xfactor)) covering ten out of eighteen 1.3 mm dust continuum cores (hereafter referred to as “dense cores”) from the core catalog of (cite: Fabien), see Table [\[tab:core_parameters\]](#tab:core_parameters).

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  |  |  |  |  |
| Core | Int $\times$ $10^3$ | V$_{\text{LSR}} -$ \<V$_{\text{LSR}}$\>$^1$ | $\sigma_v$ $^1$ | T$_{\rm ex}$ $^1$ | $\tau$ $^1$ | N(N$_2$H$^+$) | X(N$_2$H$^+$)$^1$ | N$_{\rm tot}$$^2$ | M$_{\rm tot}$$^2$ |
| ID | \[K $\rm km\,s^{-1}$\] | \[$\rm km\,s^{-1}$\] | \[$\rm km\,s^{-1}$\] | \[K\] |  | $\times$ $10^{14}$ \[cm$^{-2}$\] | $\times$ $10^{-10}$ | $\times$ $10^{24}$ \[cm$^{-2}$\] | \[$\hbox{\rm M}_{\odot}$\] |
|  |  |  |  |  |  |  |  |  |  |
| L10 | 0.358 | -1.41 $\pm$ 0.03 | 0.92 $\pm$ 0.02 | 11.2 $\pm$ 0.7 | 5.44 $\pm$ 0.5 | 2.44 $\pm$ 0.26 | 2.91 $\pm$ 0.84 | 0.65 $\pm$ 0.08 | 0.56 $\pm$ 0.07 |
| L11 | 0.205 | 2.04 $\pm$ 0.03 | 1.51 $\pm$ 0.03 | 12.3 $\pm$ 1.1 | 1.97 $\pm$ 0.3 | 0.88 $\pm$ 0.14 | 0.34 $\pm$ 0.09 | 0.23 $\pm$ 0.02 | 0.20 $\pm$ 0.02 |
| L12 | 0.176 | -0.48 $\pm$ 0.06 | 1.08 $\pm$ 0.04 | 11.3 $\pm$ 1.4 | 1.51 $\pm$ 0.2 | 0.72 $\pm$ 0.18 | 0.45 $\pm$ 0.13 | 0.19 $\pm$ 0.02 | 0.16 $\pm$ 0.02 |
| L13 | 0.254 | -1.84 $\pm$ 0.10 | 1.19 $\pm$ 0.06 | 10.3 $\pm$ 1.2 | 2.64 $\pm$ 0.2 | 1.24 $\pm$ 0.26 | 1.15 $\pm$ 0.33 | 0.33 $\pm$ 0.03 | 0.28 $\pm$ 0.02 |
| L14 | 0.042 | -0.55 $\pm$ 0.04 | 0.70 $\pm$ 0.05 | 12.4 $\pm$ 1.1 | 0.71 $\pm$ 0.1 | 0.15 $\pm$ 0.04 | 0.06 $\pm$ 0.01 | 0.04 $\pm$ 0.01 | 0.03 $\pm$ 0.01 |
| L16 | 0.370 | -0.72 $\pm$ 0.01 | 0.56 $\pm$ 0.01 | 10.0 $\pm$ 0.2 | 22.8 $\pm$ 1.1 | 2.66 $\pm$ 0.25 | 2.90 $\pm$ 0.84 | 0.70 $\pm$ 0.08 | 0.61 $\pm$ 0.07 |
| L18 | 0.409 | -1.74 $\pm$ 0.01 | 1.01 $\pm$ 0.01 | 17.8 $\pm$ 0.3 | 4.74 $\pm$ 0.2 | 2.09 $\pm$ 0.08 | 0.83 $\pm$ 0.24 | 0.55 $\pm$ 0.06 | 0.47 $\pm$ 0.05 |
| L19 | 0.940 | -2.87 $\pm$ 0.01 | 1.18 $\pm$ 0.01 | 17.5 $\pm$ 0.2 | 5.21 $\pm$ 0.2 | 4.80 $\pm$ 0.22 | 1.44 $\pm$ 0.42 | 1.27 $\pm$ 0.15 | 1.10 $\pm$ 0.13 |
| L20 | 0.396 | -2.36 $\pm$ 0.02 | 0.82 $\pm$ 0.01 | 9.1 $\pm$ 0.9 | 8.08 $\pm$ 0.4 | 2.78 $\pm$ 0.51 | 0.24 $\pm$ 0.07 | 0.74 $\pm$ 0.09 | 0.64 $\pm$ 0.08 |
| L23 | 0.785 | -1.61 $\pm$ 0.03 | 0.74 $\pm$ 0.02 | 5.8 $\pm$ 1.4 | 2.61 $\pm$ 0.2 | 2.92 $\pm$ 0.36 | 0.33 $\pm$ 0.09 | 0.77 $\pm$ 0.01 | 0.67 $\pm$ 0.01 |

Table notes: The number in the first column indicate the cores number in Table E.11 in (cite: Fabien), and in Table F.9 in (cite: Nichol). The “L” is used to distinguish between the PV features associated with the dense cores from (cite: Fabien) and the PV features of possible cores under the 1.3 mm band detection limit (see § [5.2](#sec:kinematics-analysis-at-large-scales) and Table [\[tab:VGcores\]](#tab:VGcores)). The errors of N(N$_2$H$^+$) and N$_{\rm tot}$ are estimated based on the distribution of the percentage error in column densities, to prevent underestimations.\
$^1$ These quantities represent average measurements inside core regions.\
$^2$ Total column density and masses estimated from the N(N$_2$H$^+$) and relative abundance (see § [4.2](#sec:relative-abundances)).

## N$_2$H$^+$ column density and mass

In order to estimate the column density of N$_2$H$^+$, and given that T$_{\rm ex}$ is not well constrained due to the low optical depth of some spectrum, we use the optically thick transitions approximation given by the following expression (cite: Caselli2; Elena):

$$\begin{equation}
    \text{N(N}_2\text{H}^+) = \frac{4\pi^{3/2}}{\sqrt{\ln(2)}} \frac{\nu^3 \cdot Q \cdot \sigma_v}{c^3 \cdot A_{ul} \cdot g_u} \frac{\tau}{e^{h\nu/k_bT_{ex}} - 1} \cdot e^{E_u/k_bT_{ex}}, 
\label{eq:column-density}
\end{equation}$$

![](Figure/8.png)

where $\sigma_v$, $\tau$, and $T_{ex}$ correspond to the parameters returned by our fits, while $\nu$ is the frequency, $Q$ is the partition function, $c$ is the speed of light, $A_{ul}$ is the Einstein coefficient, $g_u$ is the statistical weight, $h$ is the Planck’s constant, $k_B$ is the Boltzmann’s constant, and $E_u$ is the energy of the upper limit (cite: Laurent; Jeffrey; Elena). The error of N(N$_2$H$^+$) is estimated making the error propagation over the Eq. [\[eq:column-density\]](#eq:column-density). We apply this expression over the Blue- and the Red-velocity component to obtain the column density of each one, N$_\text{B}$(N$_2$H$^+$) and N$_\text{R}$(N$_2$H$^+$), respectively. The total column density N$_\text{T}$(N$_2$H$^+$) is obtained by summing these (see Fig. [8](#fig:columndensity) and Table [2](#tab:columndensity_table)). Then, we can measure the mass per pixel of N$_2$H$^+$ by applying the following expression:

$$\begin{equation}
    \text{M(N}_2\text{H}^+) = \text{N(N}_2\text{H}^+) \cdot \text{A}_{\rm pixel} \cdot m_{\text{N}_2\text{H}^+}, 
\label{eq:n2hp-mass}
\end{equation}$$

where N(N$_2$H$^+$) is given by the Eq. [\[eq:column-density\]](#eq:column-density), A$_{\rm pixel}$ corresponds to the area of the pixel, and $m_{\text{N}_2\text{H}^+}$ corresponds to the mass of N$_2$H$^+$ molecule, where $m_{\text{N}_2\text{H}^+} = 4.817 \times 10^{-23}$ g. Table [2](#tab:columndensity_table) shows the mass for the Blue- and the Red-velocity components as well as the total N$_2$H$^+$ mass in the protocluster.

|  |  |  |
|:--:|:--:|:--:|
|  |  |  |
| N$_\text{col}$ | \<N(N$_2$H$^+$)\> | M(N$_2$H$^+$) |
|  | $\times$ $10^{13}$ \[$\text{cm}^{-2}$\] | $\times$ $10^{-6}$ \[$\hbox{\rm M}_{\odot}$\] |
|  |  |  |
| N$_\text{B}$(N$_2$H$^+$) | 1.49 $\pm$ 0.41 | 1.77 $\pm$ 0.49 |
| N$_\text{R}$(N$_2$H$^+$) | 1.79 $\pm$ 0.49 | 2.19 $\pm$ 0.61 |
| N$_\text{T}$(N$_2$H$^+$) | 2.28 $\pm$ 0.56 | 3.96 $\pm$ 0.78 |

: Column densities and masses of N$_2$H$^+$ in G351.77 protocluster.

Table notes: Averages of N$_2$H$^+$ column density estimations and total N$_2$H$^+$ masses. N$_\text{B}$, N$_\text{R}$ and N$_\text{T}$ correspond to the Blue-velocity component, the Red-velocity component and N$_\text{B}$ $+$ N$_\text{R}$, respectively. The errors are estimated based on the distribution of the percentage errors in column densities, to prevent underestimations.

## N$_2$H$^+$ relative abundance

We expect to estimate a new column density map of H$_2$(N$_{\rm tot}$) and mass map of H$_2$(M$_{\rm tot}$) for both small and large scale structures (see § [5](#sec:kinematics-analysis)), with at smaller spatial scale (see below) than the N(H$_2$) provided by (cite: Pierre). This estimation can not be made with the ALMA-IMF dust emission given its small spatial coverage. However, the N$_2$H$^+$ emission provides us with a better angular resolution and a larger spatial coverage. For this is necessary to know the X(N$_2$H$^+$) in the protocluster, which is given by the following expression:

$$\begin{equation}
\text{X(N}_2\text{H}^+) = \frac{\text{N(N}_2\text{H}^+)}{\text{N(H}_2)}.  
\label{eq:relativeabundance_equation}
\end{equation}$$

where the error of the relative abundance is estimated making the error propagation of the Eq. [\[eq:relativeabundance_equation\]](#eq:relativeabundance_equation) utilizing the error maps of N(N$_2$H$^+$) and N(H$_2$) at the same resolution.

Given the lower resolution of the N(H$_2$) data (see Fig. [9](#fig:h2map)), we perform a new fitting process of the N$_2$H$^+$ cube starting from the original spectral cube. In the first step, we convolved to a matched resolution and pixel scales the N(H$_2$) data. Subsequently, we implement the fitting processes shown in § [3](#sec:line-fitting-process). In this way, it is feasible to analyze both data-sets together in order to estimate the X(N$_2$H$^+$) correctly.

To ensure a more robust measurement of X(N$_2$H$^+$), we restrict our analysis to N(N$_2$H$^+$) and N(H$_2$) regions with S/N in column densities $\,>\,4$. Applying Eq. [\[eq:relativeabundance_equation\]](#eq:relativeabundance_equation) we obtain the relative abundance values for each pixel, which appears to follow a log-normal distribution (see Fig. [10](#fig:xfactor)). Based on these findings, our objective is to determine a representative value of X(N$_2$H$^+$), whose value will be equal to the mode of this distribution (the mean within the largest bin of the histogram, see Fig. [10](#fig:xfactor)). This allow us to compare structures across the whole protocluster and between the velocity components.

![](Figure/9.png)

However, taking into account the significant scatter of X(N$_2$H$^+$), with values that ranging from $\sim\,10^{-11}$ to $\sim\,10^{-9}$, and considering that the mode may vary depending on the bin width used, we implement the *Freedman Diaconis Estimator* method in order to derive the most representative value for the protocluster. This method[^7] provides the optimal bin width for a histogram, dividing the data sample into interquartile ranges (IQR), in order to equilibrate the distribution type, dispersion, and the size of the data sample.

|  |  |  |
|:--:|:--:|:--:|
|  |  |  |
| N$_\text{col}$ | \<N$_{\rm tot}$\> | M$_{\rm tot}$ |
|  | $\times$ $10^{23}$ \[cm$^{-2}$\] | \[$\hbox{\rm M}_{\odot}$\] |
|  |  |  |
| N$_{\rm tot,B}$ | 0.89 $\pm$ 0.24 | 740 $\pm$ 205 |
| N$_{\rm tot,R}$ | 1.08 $\pm$ 0.29 | 917 $\pm$ 253 |
| N$_{\rm tot,T}$ | 1.370 $\pm$ 0.38 | 1657 $\pm$ 326 |

: Total column densities and masses in G351.77 protocluster.

Table notes: Averages of total column density estimations and total masses derived from the N$_2$H$^+$ emission N$_{\rm tot,B}$, N$_{\rm tot,R}$ and N$_{\rm tot,T}$ corresponds to the Blue-velocity component, the Red-velocity component and N$_{\rm tot,B}$ $+$ N$_{\rm tot,R}$, respectively.

![](Figure/10.png)

Applying this method, the estimated optimal number of bins for our data distribution is 119 (see Fig. [10](#fig:xfactor)). With this number of bins, the mean within the largest bin (mode) corresponds to X(N$_2$H$^+$) $=\,(1.66\,\pm\,0.46)\,\times\,10^{-10}$. Additionally, by increasing the number of bins while preserving the log-normal shape of the distribution and averaging all the measured modes, we find that the modes converge to X(N$_2$H$^+$) $=\,1.66\,\times\,10^{-10}$. Thus, we define the representative relative abundance of G351.77 in the protocluster zone as\
X(N$_2$H$^+$) $=\,(1.66\,\pm\,0.46)\,\times\,10^{-10}$, whose value is within the ranges and magnitude order previously reported (cite: Caselli2002; fontani2006; Henshaw). We use this value to determine N$_{\rm tot}$ and the M$_{\rm tot}$ at a higher resolution based on the N(N$_2$H$^+$) emission at its original resolution (before convolving it). This facilitates the measurement of the M$_{\rm tot}$, at smaller scales, allowing to estimate masses related to cores and velocity gradients (see Table [3](#tab:h2col_table) and § [5](#sec:kinematics-analysis)).

We estimate a total mass M$_{\rm tot}$ in the G351.77 protocluster $\sim\,1660\,\pm\,326$  $\hbox{\rm M}_{\odot}$, which we consider a lower limit since this corresponds to the mass derived only from the regions with N$_2$H$^+$ emission. Additionally, the total mass estimated directly from the dust-based H$_2$ column density map from (cite: Pierre) is M(H$_2$)  $\sim$  2820  $\hbox{\rm M}_{\odot}$. However, if we consider the mass inside the N$_2$H$^+$ coverage (at S/N $>$ 9), we estimate a M(H$_2$)  $\sim$  2000  $\hbox{\rm M}_{\odot}$. This mass is within our uncertainties and hence represent a good agreement considering the different tracers and techniques involved in this comparison. Given that the N(H$_2$) map from (cite: Pierre) is not affected by the interferometric filtering, like the N$_2$H$^+$ data of this research, the column densities, and then the masses, are correctly comparable. Our M$_{\rm tot}$ estimation is also consistent with the total mass measured in (cite: Simon), which represents $\sim$ 16% of the total mass measured in the Mother Filament $\sim$ 10200  $\hbox{\rm M}_{\odot}$ in (cite: Simon). Aside from the global protocluster properties, we provide column densities, masses, and N$_2$H$^+$ relative abundances, in addition to the spectral fitting parameters (see § [3](#sec:line-fitting-process) and Table [\[tab:core_parameters\]](#tab:core_parameters)) of the dense cores. .

# Kinematic analysis

The main goal is to analyze the kinematics of the dense gas within the G351.77 protocluster traced by N$_2$H$^+$ (1-0). The spectral line fitting process described in § [3](#sec:line-fitting-process) provides us with the most reliable parameter measurable from each spectrum, the centroid velocity, whose median error estimations are $\sim\,0.034~\rm km\,s^{-1}$. This centroid velocity, combined with the angular resolution of our data, enables us to analyze the kinematics of the protocluster on different scales (see below). To achieve this, we utilize PV diagrams (see Fig. [11](#fig:pv_diagram1)), which correspond to projections of Position-Position-Velocity (PPV) diagrams. These PV diagrams allow us to characterize PV features, which may be produced by inflow, rotation, outflow, or cloud-cloud collisions (cite: Tobin; Henshaw; Haworth; Mori), and access to the physical information occurring at both $\sim$ small and large scales. To simplify the analysis, we therefore define small scales as scales from the resolution limit of the observations, or the “core” scales, of about 4 kau to about 10$\times$ larger. Conversely, larger scales encompass approximately from filament scales to the protocluster scale, so $\sim 0.2$ pc to 1.2 pc.

![](Figure/11.png)

In addition, we create and analyze PPV diagrams[^8], in order to inspect and distinguish PPV structures. This way, it is possible to extract structures at both small and large, potentially coarser, scales. In doing so, we isolate structures based on PPV distributions combined with their integrated intensity. We then analyze these while avoiding degeneracies that might arise from the use of projected PV diagrams alone.

We utilize three parameters to generate the intensity-weighted PV diagrams shown in e.g., Fig. [11](#fig:pv_diagram1). These parameters are the centroid velocity, integrated intensity (excluding points with emission below 11 K $\rm km\,s^{-1}$ to avoid introducing noise and to better highlight the dominant structures in the diagrams), and $b$ or $l$ coordinates (cite: Henshaw; Valentina19; Rodrigo21; Elena22; rodrigo24). The top left panel of the Fig. [11](#fig:pv_diagram1) shows the spatial distribution of the N$_2$H$^+$ (1-0) emission, where the blue and red colorbars represent the Blue- and Red-velocity components described in § [3.4](#sec:bluest-and-reddest-velocity-component). The top right and bottom left panels display PV diagrams, where the color of each point represents the integrated intensity weighted.

## Kinematic analysis on small scales

A cursory inspection of Fig. [11](#fig:pv_diagram1) reveals distinct PV features along the filamentary structures present in both the Blue- and the Red-velocity component, some of which appear to be consistent in position both with the dense cores (cite: Fabien) and with their estimated DCN (3-2) velocities (see Table F.9 in (cite: Nichol)).

We analyze the N$_2$H$^+$ (1-0) velocities around the dense cores within a radius 6 times the size of the core ($\sim$ 0.1 pc, see Table E.11 (cite: Fabien)). This radius criteria enables us to examine the behavior of the surrounding gas while avoiding the overlap of gas around other cataloged cores. Subsequently, we re-create the PV diagrams of N$_2$H$^+$ (1-0) emission in the vicinity of the cores, which permits the identification of two distinct types of features:

1.  V-shapes: where the core is positioned at or near the point where we measure the inflection point in the velocity field of N$_2$H$^+$ (1-0), and the surrounding gas transitions towards lower or higher velocities (see Fig. [12](#fig:cartoon1) and (cite: rodrigo24)).

2.  Straight-shapes: where the gas around the core transitions from high to low velocities, while the core is located $\sim$ halfway along this Straight-shape (see Fig. [13](#fig:strigth-shape); see also Figure 1 in (cite: Tobin)).

From the 1.3 mm continuum data, 18 dense cores have been cataloged (see Table E.11 in (cite: Fabien)), where 9 are located in zones with N$_2$H$^+$ (1-0) integrated intensity higher than 11 K $\rm km\,s^{-1}$ and S/N $>$ 9 (see Fig. [11](#fig:pv_diagram1)). However, only six dense cores have identifiable kinematic patterns in the PV diagram (3 V-shapes and 3 Straight-shapes, see Table [\[tab:VGcores\]](#tab:VGcores)).

In order to characterize the V- and Straight-shapes we apply a linear fit to the observed VGs, encompassing the upper and lower VG for the V-shapes (see Fig. [\[fig:core6_2\]](#fig:core6_2) and Fig. [13](#fig:strigth-shape)). The selection criteria for the points used in the fit are based on their integrated intensity and location along the V-shape structure. This approach allows us to specifically characterize the enveloping points of the V-shape structure, effectively providing a boundary or limit for the measurements derived from the characterization. For the linear fitting process the integrated intensity is used as a statistical weight. After characterizing the VGs, we estimate their associated timescales as $t_{\text{VG}} = \frac{1}{\text{VG}}$, (cite: Rodrigo21; rodrigo24). Furthermore, we measure the M$_{\rm tot}$(§ [4](#sec:column-density-and-masses)) associated with the points used to quantify the VGs in order to estimate the mass inflow rate $\dot{\textup{M}}_{\textup{tot,in}}$ following:

$$\begin{equation}
\label{eq:massinflowrate}
\dot{\textup{M}}_{\text{tot,in}} = \frac{\text{M}_{\text{tot}}}{t_{\text{VG}}}.
\end{equation}$$

We note that the above analysis of the VG and timescales is affected by the inclination angle $\theta$ of the filament relative to the plane of the sky. The relationship is given by $t_{\rm VG}\,=\,l/v_r\tan(\theta)$, where $l$ represents the projected length of the filament in the plane of the sky, $v_r$ denotes the radial velocity, and $\theta$ is the inclination angle of the filament. For our purposes, we can not measure the inclination of any given structure. The assumptions here are equivalent to assuming a 45$^{\circ}$ average inclination angle for all timescales and $\dot{\textup{M}}_{\text{tot,in}}$. Besides, (cite: rodrigo24) showed in their Fig. 11 that the estimated gradients (which they measure in a similar fashion as here) do not depend on the orientation angle of the spatial axis used in the PV diagrams. That is, V-shapes extracted along the $b$ coordinate still appear as clear V-shapes at other angles with gradients (and so timescales).

Focusing on the most prominent V-shape, we identify two clear VGs associated with a dense core (L19 in Fig. [14](#fig:vshapes_location) and Table [\[tab:VGcores\]](#tab:VGcores)). This core is located in the region with the highest N$_2$H$^+$ (1-0) emission, where the spectra are fitted by 2-velocity-components. We measure the VGs, timescales, mass, and mass inflow rate of the six PV features associated with dense cores, and we present these parameters in Table [\[tab:VGcores\]](#tab:VGcores).

(cite: Henshaw) proposed two physical processes related to the V-shapes structures in PV diagrams; inflows and outflows. However, we do not observe agreement between the position of outflow catalogs (cite: towner) and the position of cores associated with V-shapes in PV diagrams. We\

![image](Figure/12_1.png) ![image](Figure/12_2.png) ![image](Figure/12_3.png)

![](Figure/13.png)

![](Figure/14.png)

propose that the points utilized for the characterization of the VG in V-shapes represent the inflowing gas with the highest velocity along a filamentary structure, where the core may be located in a “knee” in the filament (see Fig. [12](#fig:cartoon1) and (cite: rodrigo24) for similar interpretation of the V-shapes). On the other hand, the Straight-shapes may be explained as filamentary structures with embedded cores, where the filaments inflow toward the inner and denser regions and the cores follow the stream of the surrounding gas, flowing along with the filaments (cite: hacar2011; Lu; anualmotte; Kim; Arzoumanian; Yang; Pan).

+:----------:+:------------:+:------------:+:--------:+:------------------------:+:------------------:+:--------------------------:+:-----------------------------------------------------------:+:-:+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| PV-feature | RA           | DEC          | Shape    | VG                       | $t_{\rm VG}$       | M$_{\rm tot}$              | $\dot{\textup{M}}_{\textup{tot,in}}$                        |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| ID         | \[ICRS (J2000)\]            |          | \[km s$^{-1}$pc$^{-1}$\] | \[kyr\]            | \[$\hbox{\rm M}_{\odot}$\] | $\times$ $10^{-4}$ \[$\hbox{\rm M}_{\odot}\,\rm{yr}^{-1}$\] |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| L13        | 17:26:45.089 | -36:09:19.42 | Straight | 26.90 $\pm$ 0.95         | 36.35 $\pm$ 1.29   | 9.74 $\pm$ 2.69            | 2.68 $\pm$ 0.74                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| L16        | 17:26:41.635 | -36:08:48.00 | V-shape  | 22.61 $\pm$ 2.65         | 43.25 $\pm$ 5.07   | 1.71 $\pm$ 0.47            | 0.40 $\pm$ 0.11                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 15.46 $\pm$ 0.89         | 63.24 $\pm$ 3.65   | 5.44 $\pm$ 1.50            | 0.86 $\pm$ 0.24                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| L18        | 17:26:42.725 | -36:09:02.42 | Straight | 15.50 $\pm$ 1.43         | 63.09 $\pm$ 5.81   | 18.36 $\pm$ 5.07           | 2.91 $\pm$ 0.80                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| L19        | 17:26:43.687 | -36:09:06.51 | V-shape  | 37.78 $\pm$ 2.08         | 25.88 $\pm$ 1.43   | 10.01 $\pm$ 2.76           | 3.87 $\pm$ 1.07                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 133.60 $\pm$ 16.96       | 7.32 $\pm$ 2.02    | 5.35 $\pm$ 1.48            | 7.31 $\pm$ 2.02                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| L20        | 17:26:42.830 | -36:09:11.97 | V-shape  | 24.8 $\pm$ 2.07          | 39.43 $\pm$ 3.30   | 1.02 $\pm$ 0.28            | 0.26 $\pm$ 0.07                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 29.42 $\pm$ 3.35         | 33.24 $\pm$ 3.78   | 2.39 $\pm$ 0.66            | 0.75 $\pm$ 0.20                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| L23        | 17:26:44.011 | -36:09:16.18 | Straight | 2.46 $\pm$ 0.14          | 397.63 $\pm$ 23.10 | 38.21 $\pm$ 10.56          | 0.96 $\pm$ 0.27                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C1         | 17:26:44.369 | -36:09:33.05 | V-shape  | 33.04 $\pm$ 2.41         | 29.6 $\pm$ 2.16    | 15.29 $\pm$ 4.22           | 5.17 $\pm$ 1.43                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 48.05 $\pm$ 6.21         | 20.35 $\pm$ 2.63   | 12.44 $\pm$ 3.44           | 6.11 $\pm$ 1.69                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C2         | 17:26:44.003 | -36:09:35.61 | V-shape  | 33.34 $\pm$ 2.19         | 29.32 $\pm$ 1.93   | 17.97 $\pm$ 4.96           | 6.13 $\pm$ 1.69                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 44.40 $\pm$ 3.53         | 22.02 $\pm$ 1.75   | 17.11 $\pm$ 4.72           | 7.77 $\pm$ 2.14                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C3         | 17:26:43.501 | -36:09:31.06 | V-shape  | 58.51 $\pm$ 10.24        | 16.71 $\pm$ 2.92   | 6.58 $\pm$ 1.82            | 3.94 $\pm$ 1.09                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 22.52 $\pm$ 1.03         | 43.42 $\pm$ 1.99   | 23.65 $\pm$ 6.53           | 5.45 $\pm$ 1.50                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C4         | 17:26:41.743 | -36:09:35.57 | V-shape  | 19.11 $\pm$ 1.65         | 51.17 $\pm$ 4.41   | 13.21 $\pm$ 3.64           | 2.58 $\pm$ 0.71                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 22.49 $\pm$ 2.32         | 43.47 $\pm$ 4.49   | 12.45 $\pm$ 3.44           | 2.86 $\pm$ 0.79                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C5         | 17:26:41.304 | -36:09:11.29 | V-shape  | 24.35 $\pm$ 2.73         | 40.16 $\pm$ 4.50   | 4.81 $\pm$ 1.32            | 1.20 $\pm$ 0.33                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 37.54 $\pm$ 4.13         | 26.05 $\pm$ 2.86   | 7.59 $\pm$ 2.09            | 2.91 $\pm$ 0.80                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C6         | 17:26:40.551 | -36:09:04.45 | Straight | 24.35 $\pm$ 2.73         | 40.16 $\pm$ 4.50   | 18.58 $\pm$ 5.13           | 4.63 $\pm$ 1.28                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C7         | 17:26:39.924 | -36:09:12.81 | V-shape  | 16.10 $\pm$ 1.38         | 60.75 $\pm$ 5.19   | 7.16 $\pm$ 1.97            | 1.18 $\pm$ 0.32                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 15.30 $\pm$ 2.81         | 63.92 $\pm$ 11.73  | 2.41 $\pm$ 0.66            | 0.38 $\pm$ 0.10                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C8         | 17:26:39.548 | -36:08:29.49 | V-shape  | 17.77 $\pm$ 1.19         | 55.01 $\pm$ 3.68   | 22.79 $\pm$ 6.29           | 4.14 $\pm$ 1.14                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 11.18 $\pm$ 0.78         | 87.43 $\pm$ 6.13   | 23.45 $\pm$ 6.48           | 2.68 $\pm$ 0.74                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C9         | 17:26:38.858 | -36:08:28.73 | V-shape  | 11.06 $\pm$ 0.90         | 88.40 $\pm$ 7.16   | 13.51 $\pm$ 3.73           | 1.53 $\pm$ 0.42                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 17.23 $\pm$ 3.55         | 56.76 $\pm$ 11.70  | 6.14 $\pm$ 1.69            | 1.08 $\pm$ 0.30                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C10        | 17:26:39.172 | -36:08:10.49 | Straight | 25.32 $\pm$ 1.13         | 38.62 $\pm$ 1.72   | 45.64 $\pm$ 5.08           | 11.82 $\pm$ 1.32                                            |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C11        | 17:26:40.677 | -36:08:35.57 | V-shape  | 17.75 $\pm$ 1.61         | 55.08 $\pm$ 4.99   | 5.08 $\pm$ 1.41            | 0.92 $\pm$ 0.26                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 20.91 $\pm$ 1.88         | 46.77 $\pm$ 4.20   | 2.33 $\pm$ 0.64            | 0.50 $\pm$ 0.14                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C12        | 17:26:42.190 | -36:08:53.34 | V-shape  | 20.47 $\pm$ 1.23         | 47.77 $\pm$ 2.86   | 12.76 $\pm$ 3.52           | 2.67 $\pm$ 0.74                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 33.46 $\pm$ 2.60         | 29.23 $\pm$ 2.27   | 10.65 $\pm$ 2.94           | 3.64 $\pm$ 1.01                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C13        | 17:26:42.185 | -36:08:55.85 | V-shape  | 20.49 $\pm$ 2.41         | 47.72 $\pm$ 5.60   | 10.53 $\pm$ 2.91           | 2.21 $\pm$ 0.61                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 35.59 $\pm$ 4.61         | 29.23 $\pm$ 3.56   | 9.17 $\pm$ 2.53            | 3.14 $\pm$ 0.87                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C14        | 17:26:46.011 | -36:09:18.13 | V-shape  | 12.55 $\pm$ 1.04         | 77.90 $\pm$ 6.43   | 3.18 $\pm$ 0.88            | 0.41 $\pm$ 0.11                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 34.67 $\pm$ 2.44         | 28.20 $\pm$ 1.98   | 3.62 $\pm$ 1.01            | 1.28 $\pm$ 0.36                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C15        | 17:26:45.320 | -36:09:21.17 | V-shape  | 48.40 $\pm$ 3.80         | 20.20 $\pm$ 1.58   | 8.81 $\pm$ 2.43            | 4.36 $\pm$ 1.20                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 42.72 $\pm$ 4.74         | 22.89 $\pm$ 2.54   | 5.01 $\pm$ 1.38            | 2.19 $\pm$ 0.60                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          |                          |                    |                            |                                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
| C16        | 17:26:46.340 | -36:09:18.52 | V-shape  | 12.27 $\pm$ 1.35         | 79.70 $\pm$ 8.74   | 9.08 $\pm$ 2.51            | 1.14 $\pm$ 0.31                                             |   |
|            |              |              |          +--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+
|            |              |              |          | 16.56 $\pm$ 2.11         | 59.03 $\pm$ 7.53   | 8.22 $\pm$ 2.27            | 1.39 $\pm$ 0.38                                             |   |
+------------+--------------+--------------+----------+--------------------------+--------------------+----------------------------+-------------------------------------------------------------+---+

Table notes: The “L” indicates the PV features associated with the dense cores from (cite: Fabien). The “C” indicates the PV features associated with core candidates under the 1.3 mm band detection limits. We provide the velocity gradient, timescale, mass and mass inflow rate for each PV feature, in addition to the potential position of the vertex.

Continuing the PV analysis at scales of 6 times the average radius of the dense cores, some of these PV features are even found without any detected dense cores (see Fig. [14](#fig:vshapes_location) and Table [\[tab:VGcores\]](#tab:VGcores)).

+:-------:+:------------:+:------------:+:------------------------:+:----------------:+:--------------------------:+:-----------------------------------------------------------:+
|         |              |              |                          |                  |                            |                                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| V-shape | RA           | DEC          | VG                       | $t_{\rm VG}$     | M$_{\rm tot}$              | $\dot{\textup{M}}_{\textup{tot,in}}$                        |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| ID      | \[ICRS (J2000)\]            | \[km s$^{-1}$pc$^{-1}$\] | \[kyr\]          | \[$\hbox{\rm M}_{\odot}$\] | $\times$ $10^{-4}$ \[$\hbox{\rm M}_{\odot}\,\rm{yr}^{-1}$\] |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
|         |              |              |                          |                  |                            |                                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| L16     | 17:26:41.635 | -36:08:48.00 | 19.04 $\pm$ 1.40         | 51.39 $\pm$ 3.78 | 7.15 $\pm$ 1.57            | 1.39 $\pm$ 0.32                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| L19     | 17:26:43.687 | -36:09:06.51 | 85.69 $\pm$ 8.54         | 11.42 $\pm$ 1.13 | 15.36 $\pm$ 3.13           | 13.45 $\pm$ 3.04                                            |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| L20     | 17:26:42.830 | -36:09:11.97 | 27.11 $\pm$ 1.97         | 36.09 $\pm$ 2.62 | 3.41 $\pm$ 0.71            | 0.94 $\pm$ 0.19                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
|         |              |              |                          |                  |                            |                                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C1      | 17:26:44.369 | -36:09:33.05 | 40.54 $\pm$ 3.33         | 24.13 $\pm$ 1.98 | 27.72 $\pm$ 5.44           | 11.49 $\pm$ 2.25                                            |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C2      | 17:26:44.003 | -36:09:35.61 | 38.87 $\pm$ 2.07         | 25.17 $\pm$ 1.34 | 35.08 $\pm$ 6.84           | 13.93 $\pm$ 2.72                                            |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C3      | 17:26:43.501 | -36:09:31.06 | 40.51 $\pm$ 5.14         | 24.15 $\pm$ 3.06 | 30.22 $\pm$ 6.77           | 12.51 $\pm$ 2.90                                            |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C4      | 17:26:41.743 | -36:09:35.57 | 20.80 $\pm$ 1.42         | 47.04 $\pm$ 3.21 | 25.66 $\pm$ 5.00           | 5.45 $\pm$ 1.06                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C5      | 17:26:41.304 | -36:09:11.29 | 30.94 $\pm$ 2.47         | 31.61 $\pm$ 2.53 | 12.40 $\pm$ 2.47           | 3.92 $\pm$ 0.78                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C7      | 17:26:39.924 | -36:09:12.81 | 15.70 $\pm$ 1.56         | 62.32 $\pm$ 6.21 | 9.57 $\pm$ 2.07            | 1.53 $\pm$ 0.33                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C8      | 17:26:39.548 | -36:08:29.49 | 14.47 $\pm$ 0.71         | 67.59 $\pm$ 3.32 | 46.23 $\pm$ 9.03           | 6.84 $\pm$ 1.33                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C9      | 17:26:38:858 | -36:08:28.73 | 14.14 $\pm$ 1.83         | 69.17 $\pm$ 8.95 | 19.65 $\pm$ 4.09           | 2.84 $\pm$ 0.59                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C11     | 17:26:40.677 | -36:08:35.57 | 19.33 $\pm$ 1.23         | 50.61 $\pm$ 3.24 | 7.41 $\pm$ 1.54            | 1.46 $\pm$ 0.30                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C12     | 17:26:42.190 | -36:08:53.34 | 26.96 $\pm$ 1.43         | 36.28 $\pm$ 1.93 | 23.41 $\pm$ 4.58           | 6.45 $\pm$ 1.26                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C13     | 17:26:42.185 | -36:08:55.85 | 28.04 $\pm$ 2.60         | 34.89 $\pm$ 3.23 | 19.70 $\pm$ 3.85           | 5.64 $\pm$ 1.10                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C14     | 17:26:46.011 | -36:09:18.13 | 23.61 $\pm$ 1.32         | 41.44 $\pm$ 2.32 | 6.80 $\pm$ 1.33            | 1.64 $\pm$ 0.32                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C15     | 17:26:45.320 | -36:09:21.17 | 45.56 $\pm$ 3.03         | 21.47 $\pm$ 1.43 | 13.82 $\pm$ 2.79           | 6.43 $\pm$ 1.30                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+
| C16     | 17:26:46.340 | -36:09:18.52 | 14.41 $\pm$ 1.25         | 67.87 $\pm$ 5.89 | 17.30 $\pm$ 3.38           | 2.54 $\pm$ 0.49                                             |
+---------+--------------+--------------+--------------------------+------------------+----------------------------+-------------------------------------------------------------+

Table notes: The “L” indicates the V-shapes observed in PV diagram, associated with the dense cores from (cite: Fabien). The “C” represent the V-shapes observed in PV diagram associated with the candidates to possible cores under the 1.3 mm band detection limits. We provide the averaged estimations of velocity gradient, and its respective timescale, mass and mass inflow rate for each V-shape.

Utilizing the PPV diagram, we find 16 PV features both V- and Straight-shapes in the protocluster without associated dense cores (see Fig. [14](#fig:vshapes_location)). We distinguish between these small scale PV features based on the velocity distribution in the PPV diagram and increases in integrated intensity. This way, we can rule out the possibility that a given PV feature is produced by the overlap of points that do not share nearby regions in the position-position diagram. We measured the VGs, timescales, mass, and $\dot{\textup{M}}_{\textup{tot,in}}$ of the PV features (see Table [\[tab:VGcores\]](#tab:VGcores)). Both the integrated intensities measured in the regions where these PV features are observed and the estimated $\dot{\textup{M}}_{\textup{tot,in}}$ values appear similar to what we have estimated for the PV features associated with dense cores.

Furthermore, it is possible to observe some consistences in position-position between the dense cores candidates and the cores detected by *GExt2D* (cite: Fabien). We suggest a relation between these PV features and possible cores that are under the detection limit on the 1.3 mm data (undetected by *getsf*) or regions where the gas is just beginning to accrete. We propose the location of these possible cores (see Table [\[tab:VGcores\]](#tab:VGcores)) as the spatial locations of the vertexes of the V-shapes. Moreover, based on the dense cores and the associated PV features, we may expect a discrepancy of no more than $\sim$ 0.03 pc between the proposed positions and the locations of the undetected cores. This because some gas flowing through filaments may move toward a local or global maximum of the gravitational potential, which might not necessarily coincide exactly with the position of a core (cite: Izquierdo). Additionally, inflowing gas along filaments can be disturbed by turbulence, shear, interaction with molecular outflows, H ii regions, and other dynamical processes (cite: Ruben2020; Enrique2024). These effects, in addition with projection effects, could explain the discrepancies observed between the position of dense cores and the vertex of the V-shapes, which, nevertheless, are always within about the beam size (see Fig.[\[fig:core6_2\]](#fig:core6_2)).

The estimation of $\dot{\textup{M}}_{\textup{tot,in}}$ of these PV features, particularly the V-shapes, could be correlated with the core mass buildup, due to the convergence of VGs at some dense core positions (see Fig. [12](#fig:cartoon1) and (cite: rodrigo24)). Moreover, the estimated $t_{\rm VG}$ could suggest the timescale for the collapse of filamentary structures towards cores (cite: rodrigo24). In total, we observe 17 V-shapes (see Table [\[tab:meanvg\]](#tab:meanvg)), where the average values of $t_{\rm VG}\,=\,$ 43.73 $\pm$ 0.94 kyr and $\dot{\textup{M}}_{\textup{tot,in}}$ $=\,5.59\,\pm$ 0.34) $\times~10^{-4}$ $\hbox{\rm M}_{\odot}\,\rm{yr}^{-1}$.

## Kinematics analysis on large scales

![](Figure/15.png)

The PV diagram of the N$_2$H$^+$ (1-0) emission, from filament scales to protocluster scales ($\sim$ 0.2 pc to $\sim$ 1.2 pc) reveals two distinct large-scale structures, separated by $\sim$ 2 $\rm km\,s^{-1}$ (see Fig. [11](#fig:pv_diagram1)). One appears to be dominated by the Blue-velocity component, while the other is characterized by the Red-velocity component. Furthermore, these two velocity structures seem to merge or tighten up towards the Galactic northern region of the protocluster, in the direction toward the Mother Filament (see top left panel in Fig. [11](#fig:pv_diagram1)). These large-scale structures present PV features like a zig-zag along the protocluster, which we suggest are produced by kinematic effects at smaller scales (see § [5.1](#sec:kinematic-analysis-at-small-scales)). However, upon deeper examination of the kinematics and inspection of the PPV diagram, we realize that these large-scale structures are not only separated in velocity but also by spatial position (see Fig. [15](#fig:pvcolores)).

In order to analyze these structures and identify the large-scale regions contributing to the features observed in the PV-diagram, we divided the emission into four regions (F1, F2, F3, and F4) defining clear boundaries for each. This separation was guided by the integrated intensity map, SNR map, and the column density map, allowing to distinguish between possible filamentary structures. The criteria used include integrated intensities drop below 50 K $\rm km\,s^{-1}$ (excluding F3) and velocity differences larger than $\sim$ 0.9 $\rm km\,s^{-1}$, enabling us to separate structures that exhibit sharp velocity transitions (see Fig. [15](#fig:pvcolores)):

- F1: This corresponds to the primary filamentary structure within the protocluster, where we observe the highest S/Ns, integrated intensities, and column densities. It is connected with the three other large-scale structures (F2, F3, and F4) defined within the protocluster. Furthermore, six out of the nine dense cores, from (cite: Fabien), located in regions with N$_2$H$^+$ emission, are situated within this filamentary structure. Notably, this structure exhibits large-scale velocity distributions converging near the position of the core (L19 in Table [\[tab:core_parameters\]](#tab:core_parameters)) where we observe the most prominent V-shape (see § [5.1](#sec:kinematic-analysis-at-small-scales)) along with three Straight-shapes associated with dense cores. Furthermore, along this structure, we find some small-scale PV features that we suggest represent cores under the detection limit (see § [5.1](#sec:kinematic-analysis-at-small-scales)). Most of the spectra in this structure are characterized by 2-velocity-components.

- F2: Adjacent to F1, the F2 structure is the next most obvious filamentary structure within G351.77. It connects to the F1 structure near the protocluster’s center through regions with low integrated intensity, but it merges with the F1 structure towards the Galactic north of the protocluster. This structure appears as a twisted filament, less monolithically well-defined than the F1 and not converging to a specific location. Nonetheless, two (cite: Fabien) dense cores are situated inside F2, as well as $\sim$ 50% of the V- and Straight-shapes. Multiple spectra within this structure are characterized by 2-velocity-components.

- F3: Located to the south of F1, F3 displays at least two clear velocity components along its length with a $\Delta$v reaching $\sim~3~\rm km\,s^{-1}$. F3 contains one dense core (L13 in Table [\[tab:core_parameters\]](#tab:core_parameters)), coinciding with the position where the filament exhibits a large-scale V-shape in the PV diagram (see Fig. [15](#fig:pvcolores)). Two of the core candidates are located at the Galactic south of this structure.

- F4: Situated in the northern region of the protocluster, where F1 and F2 merge, the F4 structure presents well defined V- and Straight-shapes without associated cores. This region is connected with the Mother Filament.

As a whole, these structures do not appear drastically different from each other in terms of their internal kinematics; we observe PV features in all of them.

# Discussion

## G351.77 vs G353.41 protoclusters

In § [5.1](#sec:kinematic-analysis-at-small-scales) we characterized the PV features associated with dense cores as well as PV features without cores, suggesting that the dense gas material traced by the N$_2$H$^+$ (1-0) line is inflowing in filamentary structures into dense cores or in larger scales inflowing towards denser regions (cite: Hacar2017; Lu; anualmotte; Rodrigo21; Kim; Arzoumanian; Yang; rodrigo24; Pan). The recent N$_2$H$^+$ analysis in the G353.41 protocluster (cite: rodrigo24), also observed by ALMA-IMF at matched physical resolution to the observations presented here, shows similar kinematic features although they use the N$_2$H$^+$ (1-0) isolated hyperfine component. The comparison to G351.41 is relevant beyond the similarities in the analysis techniques and the matched sensitivity and spatial resolution provided by ALMA-IMF.

Both protoclusters have similar masses, sizes, distances (cite: motte22; Simon; Pierre), and both exist inside isolated filamentary structures (cite: rodrigo24).

Moreover, G351.77 and G353.41 have both been classified as existing in an Intermediate evolutionary stage (cite: motte22), based predominantly on H41$\alpha$ emission (cite: Roberto). In finer detail, the larger number of dense cores and the smaller number of PV features in G353.41 compared to G351.77 together suggest that G351.77 is in a younger evolutionary stage relative to G353.41. (cite: rodrigo24) characterized multiple V-shapes associated with dense cores, which they suggest are inflowing material onto or near dense cores, similar to our results. Almost all of the V-shapes in G353.41 are located inside filamentary structures; moreover, the $t_{\rm VG}$ and $\dot{\textup{M}}_{\textup{tot,in}}$ are similar (within the same order of magnitude) as those measured here for G351.77. This indicates that the V-shapes observed in PV diagrams represent generic kinematic features in forming protoclusters and can be used more broadly to access the conditions during the assembly of stellar clusters and the so called “initial conditions” of star formation, especially for the kinematic attributes.

By averaging the VGs of the V-shapes associated *only* with the dense cores (see Table [\[tab:meanvg\]](#tab:meanvg)), we estimate a timescale $\sim$ 32.96 $\pm$ 1.58 kyr. Conversely, by averaging the VGs of the V-shapes not associated with the dense cores, we estimate a timescales of $\sim$ 43.12 $\pm$ 1.10 kyr. When averaging all the VGs associated with the V-shapes, we estimate a timescale of $\sim$ 41.33 $\pm$ 0.95 kyr. We observe that the average timescale estimated in G353.41 protocluster is $\sim$2$\times$ higher than the value measured in G351.77. This may also corroborate the above suggestion that G351.77 is younger, whereby the cores in the protocluster (which are also more numerous) may be accumulating mass faster than in G353.41, despite the mass reservoir similarity in both protoclusters (see above).

## G351.77 on small scales

The longest timescale we measure for a V-shape is 69.17 $\pm$ 8.95 kyr (see Table [\[tab:meanvg\]](#tab:meanvg)), whose time is lower than the lifetime of the prestellar cores (Valeille-Manet et al., submitted). Although we have not observed protostellar cores within the G351.77 protocluster, we expect that these PV features will disappear before the cores enter the protostellar phase, unless these structures are continuously fed with gas in some way. This could suggest that more evolved regions should display fewer V-shapes features in dense gas, which would be more closely associated with cores rather than prestellar and protostellar cores.

Additionally, utilizing the mass and sizes of the dense cores from Table D.11 in (cite: Fabien), associated with the V-shapes, we measure the free-fall time (t$_{ff}$) for each dense core, whose average is $\sim$ 13.6 kyr. This value is $\sim$ 2.5 times lower than the average timescale for the V-shapes ($\sim$ 33 kyr, see § [6.1](#G351VSG353)), suggesting that the dense cores may collapse gravitationally before the V-shapes dissipate. The accumulation of mass into the dense cores via the V-shapes would increases the dense core densities, further reducing t$_{ff}$ and accelerating the gravitational collapse. Consequently, the dense cores could collapse on shorter timescales, limiting the time available for sustained gas accretion from the V-shapes. This implies a dual role for the V-shapes: directly feeding the dense cores while potentially generating new dense regions along the filaments produced by local accumulation of gas. Further, collateral effects from dense core collapse, such as outflows, feedback, and concentration of magnetic fields, could significantly influence the dynamics of these structures. In an evolutionary context, these interactions could affect dense core evolution, and the properties of the stars formed within. The increase in dense core mass could impact the initial mass function (IMF), and the core mass function (CMF) measured in the protocluster (cite: Fabien). These effects suggest that the relation between the V-shapes, the dense cores, and the larger filamentary structures regulates gas supply of gas, evolution timescales, and star formation efficiency in the protocluster.

Furthermore, we estimate the total mass accretion rate considering both the V-shape structures associated and not associated with the dense cores (see Table [\[tab:meanvg\]](#tab:meanvg)). The total mass accretion rate measured is $\dot{\text{M}}_{\text{in},\text{T}}\,=\,(9.84\,\pm\,0.63)\,\times\,10^{-3}$ $\hbox{\rm M}_{\odot}\,\rm{yr}^{-1}$. Considering the total mass of the protocluster is $\sim$ 2820 $\hbox{\rm M}_{\odot}$, we can estimate the depletion timescales given by $t_{\rm dep}$ = M$_{\rm tot}$/$\dot{\text{M}}_{\text{in},\text{T}}$, obtaining a $t_{\rm dep}\,\sim$ 0.3 Myr.

A $t_{\rm dep}$ $\sim$ 0.3 Myr for the V-shapes is consistent with the short lifetime of dense gas traced by N$_2$H$^+$, as described in the simulations of (cite: Priestley), where N$_2$H$^+$ is exclusively associated with dense gas typically linked to material that will collapse to form stars. This suggests that the V-shapes associated with dense cores could represent gas in stages of gravitational collapse. In contrast, the V-shapes without associated dense cores could be material in transit toward higher densities, eventually becoming linked to star formation. Hence, we suggest that the V-shapes may serve as tracers of early SFR and the evolutionary stage of star-forming regions (cite: Sami).

Moreover, the fast $t_{\rm dep}$ measured could represent not only an ongoing star formation in early stages, but also the need for continuous mass feeding from the larger scales, such as the Mother Filament (see below). This scenario maybe consistent with the finding of (cite: Hacar2024), where they identified dense fibers as structures moving material into forming star clusters. These fibers could continuously feed the protocluster, compensating the fast depletion of the local gas and enabling efficient star cluster formation. We caution that without direct confirmation of inflow onto a central mass (the cores in this case), the depletion timescales associated with the total sample of all V-shapes may be overestimated.

## G351.77 on large scales

Moving to somewhat larger scales, in § [5.2](#sec:kinematics-analysis-at-large-scales) we divided the N$_2$H$^+$ (1-0) emission of the G351.77 protocluster into 4 larger ($\sim$ 0.2 pc to $\sim$ 1.2 pc) spatially distinguishable regions or filaments inside the protocluster. In particular, we show that the F1 filamentary structure seems to be inflowing toward a dense core, where we observe the most prominent V-shape in the PV diagram (see Fig. [11](#fig:pv_diagram1) and Fig. [15](#fig:pvcolores)). Given that F1 filamentary structure is connected with the F4 structure, the region which is directly connected with the Mother Filament, and its velocity distribution observed in PPV diagrams, we suggest that the inflowing gas is coming from the Mother Filament, flowing towards the protocluster (cite: Hacar2024). Furthermore, we find dense cores associated with Straight-shapes in the G351.77 protocluster, located along of the F1 filament structure (see Fig. [11](#fig:pv_diagram1)), near the position where we observe the most prominent V-shape. Considering the velocity distribution of N$_2$H$^+$ displayed in the PV diagrams of Straight-shapes, their location, and the consistency of the N$_2$H$^+$ (1-0) velocities with those measured for the cores (see Table F.9 in (cite: Nichol)), we propose that these cores are inflowing, along with the N$_2$H$^+$, towards the location of the most prominent V-shape, potentially entrained in the slow contraction of the protocluster (cite: Lu; anualmotte; Kim; Arzoumanian; Yang; Pan). All this, may suggests that the F1 structure is actively forming cores or stars.

In contrast to F1, the F2 filamentary structure does not show evidence of inflowing gas towards a specific location but rather presents inflow towards different locations along the structure. Moreover, most of the PV features on small scales do not have associated detected dense cores, which we propose as cores below the 1.3 mm band detection limit, located within the filament. This may suggest that this filamentary structure is participating in the formation of cores but at an earlier stage than the F1 structure. Additionally, hot cores are located in regions with N$_2$H$^+$ emission with S/N $<$ 9, limiting the kinematic information available from them. Regarding the detected SiO outflows (cite: towner), we identify four in F1 and two in F2, but none are associated with well-defined structures in the PV-diagrams. Instead, these outflows are located at the edges of the N$_2$H$^+$ emission rather than the internal regions of the filaments. This spatial distribution suggest that ongoing star formation activity may not be occurring within the densest regions of the filaments but rather in their outskirts. Furthermore, the more well-defined morphology of F1 compared to F2 supports the idea that these two exist at different evolutionary stages (see also (cite: Nichol) for the proposal of multiple stages inside a given ALMA-IMF protocluster).

The F3 filamentary structure shows little evidence of star formation activity within it, where we find one dense core, and two PV features at small scales without associated dense cores. The PV features and the large-scale velocity distribution of this filamentary structure in PPV diagrams, seems to indicate that the gas in this is inflowing towards the core location.

The F4 structure presents velocity distributions in the PPV diagram (see Fig. [11](#fig:pv_diagram1) and Fig. [15](#fig:pvcolores)) that supports the idea that the inflowing gas towards the denser N$_2$H$^+$ regions of the protocluster originate from the Mother Filament. Additionally, this region may also be a site where cores or stars could be forming, given the presence of PPV features on small scales that do not have detected dense cores associated.

## G351.77 in a Global Hierarchical Collapse scenario

The evidence that we have at small and large scales is consistent with the Global Hierarchical Collapse (GHC) scenario described in (cite: Enrique). This scenario explains the collapse process occurring on different scales in molecular clouds, where mass and gas flow and accrete through filamentary structures toward clumps and denser regions. It also describes how the timescales of accretion and contraction are shorter on smaller scales. These timescales play an important role in the star formation rate (SFR), with longer timescales allowing most of the mass to be dispersed due to feedback from massive stars, which later results in a low SFR.

Thus, by comparing the GHC model with our analysis, we suggest that the Mother Filament is undergoing global collapse, with a portion of it accreting and contracting toward the G351.77 protocluster. This implies that the protocluster will increase its mass over time. Although there is evidence of YSOs in the central part (cite: Leurini2011_1; Naiping2018; Leurini2019; Sabatini2019), the H41$\alpha$ emission is compact in the central region of the protocluster (cite: motte22; Roberto), where there is no N$_2$H$^+$ emission (S/N $<$ 9). This suggests that currently there is insufficient feedback to significantly reduce the SFR in the protocluster (cite: Enrique). This indicates that the low SFR measured in G351.77 and along the Mother Filament (cite: Simon) may be due to the fact that the molecular cloud and the protocluster are still in a young stage, consistent with our suggestions and those in (cite: Simon). Consequently, the SFR is expected to increase with the formation of more massive stars until feedback from these new stars disperses the gas, thereby decreasing the SFR (cite: Enrique).

Given that we suggest the G351.77 protocluster is younger than G353.41, and based on the GHC model (cite: Enrique), we could anticipate a higher SFR in G353.41. This expectation aligns with the H41$\alpha$ emission in G353.41, which is higher than in G351.77 (cite: motte22), indicating a larger amount of massive star feedback in the G353.41 protocluster. However, a larger number of hot cores are observed in G351.77 compared to G353.41 (cite: Melisse), presenting a scenario that could contradict the notion of G351.77 being younger, as we might expect to find more hot cores in more evolved regions. Nevertheless, considering the various lines of evidence suggesting that G351.77 in indeed younger, we propose that some as of now unknown process may be inhibiting the formation of hot cores in G353.41 protocluster.

## Multi-tracer modeling

![](Figure/16.png)

In order to complement and enhance our understanding of the kinematic processes occurring in the protocluster at large scales, we utilize H$_2$CO (2-1) and DCN (3-2) line emission covering the central part of the protocluster without N$_2$H$^+$ emission (cite: motte22; Nichol). Additionally, we modeled three possible cases for gas spheres: rotation-only, infall-only, and a combination between rotation and infall (see § [12](#sec:model)), whose radial velocities are used to recreate PV diagrams (cite: Tobin; Henshaw; Mori; rodrigo24). This approach allows us to analyze the PV features produced by these kinematic processes in the PV diagrams (see Fig. [16](#fig:tracers_and_models))

The modeled sphere is formed by *n* numbers of points, which are under gravitational infall and keplerian rotation. The velocity associated to each point is estimated by using the following relations: $$\begin{equation}
V_{\textup{in}} = - \sqrt{\frac{2GM}{r}}, \quad V_{\textup{rot}} = \sqrt{\frac{GM}{r}}
\label{eq:model}
\end{equation}$$ where $r$ is the distance of each point to the center of the sphere, $G$ is the gravitational constant and $M$ is the enclosed mass. The minimum distance between each point is of 0.007 pc, in order to simulate the pixel width of our data. Additionally, the sphere has a density profile that follows a power law described below: $$\begin{equation}
\rho(r) = \rho_0\left(\frac{r}{\textup{pc}}\right)^{-\gamma} 
\label{eq:model}
\end{equation}$$

where $r$ is the distance to the center of the sphere, and $\rho_0$ is a known density. To generate an infalling and rotating sphere model, we utilize a $r_{\rm min} = 0.007$pc and a $r_{\rm max}$ = 0.8 pc, which correspond approximately to the coverage radius of N$_2$H$^+$. Also, we define $\gamma$ = 3.1 based on the maximum velocities that the data reach and in how well are the model fits to the data. The total mass utilized is 270 $\hbox{\rm M}_{\odot}$ and 2700 $\hbox{\rm M}_{\odot}$, deriving $\rho_0$ = 3.466 $\hbox{\rm M}_{\odot}$ pc$^{-3}$ and $\rho_0$ = 34.66 $\hbox{\rm M}_{\odot}$ pc$^{-3}$, respectively. Although the general shape of the PV features of the modeled sphere in PV diagrams is not affected by the mass, the velocity amplitude does show differences.

Fig. [16](#fig:tracers_and_models) shows the PV diagram of N$_2$H$^+$ (1-0) and H$_2$CO (2-1) in comparison with the contours of a rotating and infalling sphere (see § [12](#sec:model)). We observe that H$_2$CO reaches $\Delta$v $\sim$ 13 $\rm km\,s^{-1}$, with its velocity peaks in the PV diagram aligning well with the contours of the model. Furthermore, upon examining the velocity distribution of DCN in the PV diagram, we observe similar PV features with H$_2$CO(see Fig. [28](#fig:dcn_in+rot) and Fig. [29](#fig:h2co_in+rot)), which appear to match reasonably with our model of the rotating and infalling sphere and similar models (cite: Tobin; Mori). Based on the spatial locations of H$_2$CO and DCN, along with the PV features in the PV diagrams described by our model, we suggest that rotation and infall processes are occurring in the center of the protocluster within a radius of $\sim$ 0.2 pc, similar scales as e.g., (cite: roberto2009) and (cite: liu2015), which is five times smaller than the N$_2$H$^+$ spatial coverage.

This scenario is consistent with the difference in velocity measured in N$_2$H$^+$ emission in the G351.77 protocluster, which suggests that the two clear N$_2$H$^+$ velocity structures observed in Fig. [11](#fig:pv_diagram1) are rotating relative to each other with a radial velocity gradient that is approximately perpendicular to the direction toward the Mother Filament ($\sim$ 83 $^{\circ}$), which extends above the top of Fig. [11](#fig:pv_diagram1) (see also Fig. [7](#fig:velocity_map)). However, the inflow signature in the radial velocities seems more dominant than rotation for N$_2$H$^+$ on large scales. On the other hand, the models of rotation-only and infall-only show that the rotating-only case better fits the shapes observed in H$_2$CO and DCN, suggesting that the central part of the protocluster is more dominated by rotation than infall (see Fig. [17](#fig:dcn_rot), Fig. [30](#fig:dcn_in), Fig. [31](#fig:h2co_rot), and Fig. [32](#fig:h2co_in)). This scenario is consistent with that proposed in e.g. (cite: anualmotte) for high-mass star-forming regions.

Given that the rotation axis appears parallel to Galactic latitude, in other words, the velocity gradient points along the Galactic longitude, we may hypothesize that the Galactic shear is in some way inducing the rotation in the G351.77 protocluster (cite: Braine2018; Braine2020). This scenario would then imply that the initial angular momentum is set externally, and drains from the outside inward (see also (cite: Rodrigo21) filament rotation scenario and Salinas et al., in prep)

![](Figure/17.png)

This interplay between infalling and rotating gas might both favor and disfavor the protocluster star forming activity at different scales. Despite infall dominating at the larger protocluster scales (traced by N$_2$H$^+$), in the very center of the protocluster the $-$ now dominant $-$ rotation might be reducing the rate at which the protocluster fuels its dense material. This cannot be preventing the cloud from forming a protocluster, as evidenced by the fact that the protocluster is there and obviously forming stars. Yet the Mother Filament, so on scales beyond the ALMA-IMF coverage, exhibits evidence for inefficient star forming activity compared to the large mass and mass-per-unit length profile (cite: Simon). In this scenario, our results may be providing an insight to explain this dichotomy observed on the global cloud scale, because they suggest that rotation of dense filamentary sub-structures at $\sim$ 0.8 pc scales may be ubiquitous along the entire Mother Filament, but being significantly more dominant than infall outside the protocluster itself. Indeed, correlations between the lack of evidence for star formation and velocity gradients consistent with rotation have been observed previously (cite: Rodrigo21), where they also inferred outside-in filament evolution as the system sheds its angular momentum and evolves toward more efficient star formation. The transition between these two regimes could be rooted in different angular momentum loss rates across the entire cloud, potentially driven or influenced by the magnetic field (cite: amy2016; amy2018). Meanwhile, independent of the possible effects of magnetic fields, the kinematics in the Mother Filament will be characterized in upcoming work, which will test the rotation hypothesis.

In the above modeling, the sphere used to obtain the models employs a mass of 270 $\hbox{\rm M}_{\odot}$, which is 10 times lower than the 2720 $\hbox{\rm M}_{\odot}$ measured inside a radius of 0.8 pc in G351.77, in the N(H$_2$) map provided by (cite: Pierre). The larger mass assumption causes our models to exhibit larger velocities than observed. Specifically, the model would predict velocity spreads of order $\Delta$v $\sim$ 44 $\rm km\,s^{-1}$, whereas the spreads that we observe are $\Delta$v $\sim$ 14 $\rm km\,s^{-1}$. That is, the velocities in the model are overestimated by a factor of $\sim$ 3. However, the shapes of the model PV diagram compared to the observed one are still very similar, which suggests that the qualitative combined infall and rotation signature exhibited by the model reproduces the observed PV diagram structure (cite: Arzoumanian; Kim; Lu).

The velocities measured for N$_2$H$^+$, H$_2$CO, and DCN seem to be similar, and the observed PV features of H$_2$CO and DCN seem to describe the same kinematic processes. All of this indicates that the measurements are reliable. However, in a global analysis the modeled sphere suggests higher velocities than the observed one given the mass budget, raising questions such as: Why do we measure lower velocities in the protocluster? What other physical processes are affecting the kinematics of the gas?

The total mass derived from the dense cores located at the center of the protocluster (see Fig. [17](#fig:dcn_rot)) is $\sim$ 100 $\hbox{\rm M}_{\odot}$(cite: Fabien). Furthermore, using average relative abundances, where X(DCN) $=2.06~\times~10^{-10}$ and X(H$_2$CO) $=4.66~\times~10^{-10}$ (cite: Maret; Minh), and the N(H$_2$) from (cite: Pierre), we estimate the DCN and H$_2$CO masses to be M(DCN) $=1.89~\times~10^{-6}$ $\hbox{\rm M}_{\odot}$ and M(H$_2$CO) $=4.56~\times~10^{-6}$ $\hbox{\rm M}_{\odot}$. Given their extremely low masses compared to the total enclosed mass, these components do not significantly contribute to the measured mass of 270 $\hbox{\rm M}_{\odot}$. Nonetheless, they may still play a role in shaping the gravitational potential influencing the observed kinematics. However, Fig. [17](#fig:dcn_rot) shows possible relations between the positions and velocities of dense cores (including hot cores) and features observed in the PV-diagram of DCN emission. Furthermore, current evidence demonstrates that processes such as infall and rotation are occurring at smaller scales ($\sim$ 0.06$''$) in cores located at the central part of the protocluster (cite: Beuther). Additionally, outflows have been cataloged in G351.77 (cite: towner), whose positions and velocity-ranges not show relations with PV-features (see Fig. [17](#fig:dcn_rot)). Moreover, the fragmentation into clumps observed along the Mother Filament has been attributed to turbulence and magnetic fields produced by the high-mass star formation (cite: Zapata2008; Leurini2009; Leurini2011_1; Leurini2011_2; Leurini2013; Naiping2018; Leurini2019; Sabatini2019). Considering all these physical processes, we could suggest that the kinematic behavior of the gas traced by N$_2$H$^+$, H$_2$CO, and DCN may not be as described in our model, which is simple and only considers two kinematic processes. However, in broad scopes, the model is consistent with a comparatively slow gravitational contraction of the protocluster with inner rotation.

# Conclusions

We conducted an analysis of the kinematics of the dense and cold gas within the massive G351.77 protocluster, traced by the spectral line N$_2$H$^+$ (1-0), utilizing the PV diagrams and characterization of physical processes involved in high-mass star formation. The spatial resolution of the N$_2$H$^+$ data cube is $\sim$ 4 kau, making this the first study of this kind in G351.77.

Through spectral line fitting we obtain the main accessible physical parameters such as excitation temperature, optical depth, centroid velocity, and line widths (see § [3](#sec:line-fitting-process)). We have implemented the spectral line fitting over the entire data-cube, fitting 1- and 2-velocity-components (see § [3.1](#sec:one-component-fit) and § [3.2](#sec:two-component-fit)). We developed a method to identify and extract each spectra with 1- or 2-velocity-components based on the line width and S/N of the modeled spectra (see § [3.3](#sec:best-fit-and-final-model)). We finally obtained modeled data that possess spectra with 1- or 2-velocity-components. Based on the centroid velocity distribution of each spectrum, we divided and isolated the data into 2 velocity components, which we named the Blue-velocity component and Red-velocity component (see § [3.4](#sec:bluest-and-reddest-velocity-component)).

The excitation temperature, optical depth, and line widths enable the estimation of column density maps and masses of N$_2$H$^+$(see § [4](#sec:column-density-and-masses)). Additionally, we utilize the column density map of H$_2$ provided by (cite: Pierre), to estimate the relative abundance of N$_2$H$^+$, X(N$_2$H$^+$) $\sim$ (1.66 $\pm$ 0.46) $\times$ 10$^{-10}$, from which we derived an estimated total mass in the N$_2$H$^+$ emitting gas in the protocluster of $\sim$ 1660 $\pm$ 326 $\hbox{\rm M}_{\odot}$.

The characterization of kinematic patterns, our main goal in this paper, revealed by the scrutiny of both the PV and PPV diagrams cubes allowed us to identify different small and large-scale features (see § [5](#sec:kinematics-analysis)). Our main results are:

1.  The PV diagram on small scales reveals features such as V- and Straight-shapes associated in position and in velocity with the dense cores (cite: Nichol; Fabien). We suggest that the V-shapes describe inflowing gas in filamentary structures, where the dense cores are located near the vertex of the V-shapes. On the other hand, the Straight-shapes describe inflowing filamentary structures going to denser N$_2$H$^+$ regions with dense cores following the stream produced by the gas (see Fig. [12](#fig:cartoon1)).

2.  We characterize these PV features by measuring the VGs, timescales, mass, and $\dot{\textup{M}}_{\textup{tot,in}}$. The most prominent V-shape reaches velocities $\sim$ -4.5 $\rm km\,s^{-1}$ relative to the V$_{\rm LSR}$, has an average $\dot{\textup{M}}_{\textup{tot,in}}$$\sim$ 13.45 $\times$ 10$^{-4}$ $\hbox{\rm M}_{\odot}\,\rm{yr}^{-1}$ and timescale $\sim$ 11.42 kyr (see § [5.1](#sec:kinematic-analysis-at-small-scales)).

3.  The above V-shapes have similar properties as those analyzed in (cite: rodrigo24) in G353.41 indicating that they may be ubiquitous in this stage of protocluster evolution.

4.  Similarly, we also find V- and Straight-shapes without associated dense cores; these have similar properties (timescales and $\dot{\textup{M}}_{\textup{tot,in}}$) as the above sample. We suggest that these arise from possible cores or accretion centers that are under the detection limit of the 1.3 mm data (see § [5.1](#sec:kinematic-analysis-at-small-scales) and Table [\[tab:VGcores\]](#tab:VGcores)).

5.  The averaged t$_{ff}$ of the dense cores is shorter than the timescales of the V-shapes. This suggest mass of cores is increasing over their lifetimes, in turn modifying the t$_{ff}$ itself and likely driving faster dense core collapse.

6.  The estimated timescales for the V-shapes is shorter than the timescale estimates for protostellar core envelope evolution (Valeille-Manet et al., submitted and references therein). This suggests that the V-shapes are short-lived accretion signatures, that are more easily detectable in the most intense mass buildup phase of core formation. Hence we may expect fewer relative numbers of V-shapes as star-forming regions evolve (see § [5.1](#sec:kinematic-analysis-at-small-scales)).

7.  The total V-shape $\dot{\textup{M}}_{\textup{tot,in}}$(summed over the sample) enables us to estimate a depletion timescale of $\sim$ 0.3 Myr in the protocluster. This implies a fast cluster formation timescale and/or a continuous mass feeding (see § [5.1](#sec:kinematic-analysis-at-small-scales)).

8.  The PV diagram of N$_2$H$^+$(on the largest scale we study of $\sim$ 1.2 pc) reveals two main filamentary structures within the protocluster (F1 and F2 in Fig. [15](#fig:pvcolores)). These filamentary structures are actively participating in the dense core and star formation, but at different levels, so we infer that they are at different evolutionary stages (see § [5.2](#sec:kinematics-analysis-at-large-scales)). This is consistent with previous findings of indications of different episodes of star formation in the ALMA-IMF protoclusters (cite: Nichol).

9.  The analysis of large-scale VGs reveals that one of the two main filamentary structures (F1 in Fig. [15](#fig:pvcolores)) maybe inflowing toward a dense core position, where we observe the most prominent V-shape in the PV diagram at small scales (see above and Fig. [\[fig:core6_2\]](#fig:core6_2)). Within this filamentary structure we find dense cores and PV features that are not associated with detected cores (see above). These seem to be inflowing along the filament (see § [5.2](#sec:kinematics-analysis-at-large-scales)).

10. The large-scale PV and PPV features seem to indicate that the protocluster is being fed from the the Mother Filament (see § [5.2](#sec:kinematics-analysis-at-large-scales)), which the protocluster is forming out of.

The kinematic evidence observed in the dense gas, along with its characterization, suggests that G351.77 is actively and vigorously forming dense cores. However, based on the comparison with G354.41 protocluster (cite: rodrigo24), the low SFR measured along the filament (cite: Simon), and its consistency with the Global Hierarchical Collapse scenario (cite: Enrique), we conclude that G351.77 protocluster is still in an early evolutionary stage. As the protocluster continues to be fed by the Mother Filament, we might expect to observe an increase in the number of cores, V-shaped features associated with them, and filamentary structures evolving into well-defined filaments, along with a rise in the SFR.

We have complemented the PV diagram analysis with the H$_2$CO (2-1) and DCN (3-2) tracers, which cover areas without N$_2$H$^+$ (1-0) emission. This allows us to explore the relation between the large-scale kinematics described by N$_2$H$^+$ and the central region of the protocluster. In addition, we have implemented a rotating and infalling sphere model in order to characterize the PV features in the PV diagram produced by these kinematic processes, which is consistent with previous work (cite: Tobin; Henshaw; Mori).

Here, in brief, we find that our simple toy model is consistent with larger scale slow contraction and inner rotation, implying outside-in evolution as the initial angular momentum, possibly induced by Galactic shear (cite: Braine2018; Braine2020), is dissipated (cite: Rodrigo21). The PV features in the PV diagram produced by H$_2$CO and DCN suggest that the central region of the protocluster may be experiencing simultaneous rotation and inflow, where the rotation appears to be the most dominant kinematic effect in the center (see § [6.5](#sec:multitracer_model)). On the other hand, considering the velocity distribution and the position-position of the 2 large-scale velocity structures of N$_2$H$^+$ separated by $\sim$ 2 $\rm km\,s^{-1}$ in the PV diagram, in addition to the possible rotation features described by H$_2$CO and DCN, we suggest that these 2 large-scale velocity structures could be rotating relative to each other, with the rotating axis parallel to the direction of the Mother Filament. However, the most prominent kinematic process present at the N$_2$H$^+$ filamentary structures appears to be inflow, which seem to be inflowing not towards the center of the protocluster but rather inflowing onto themselves towards denser N$_2$H$^+$ regions (see Fig. [16](#fig:tracers_and_models)).

Nevertheless, while the shapes and features presented in the model are consistent with those observed in the PV diagram by the tracers, the measured velocities exhibit inconsistency with the velocities returned by the models by a factor of 3 (see § [6.5](#sec:multitracer_model)). We attribute these differences to the simplicity of the toy model, which only considers two kinematic effects. At the same time, other works suggest the presence of rotation and infall at small scales, bipolar outflows produced by YSOs, gravitational instabilities along the filament, and magnetic fields in the protocluster, whose physical effect could be strongly affecting the behavior of the gas.

We have carried out a thorough analysis of the N$_2$H$^+$ line emission. One absolute imperative arising from this work is to ascertain the relationship of the protocluster to the Mother Filament (cite: Simon) and the kinematic state of this filament as a whole. This work will be carried out in the near future.

# Acknowledgements

We thank the referee for carefully comments, which helped improve this paper. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01355.L, #2013.1.01365.S, and #2015.1.01273.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The project leading to this publication has received support from ORP, which is funded by the European Union’s Horizon 2020 research and innovation program under grant agreement No. 101004719 \[ORP\]. This project has received funding from the European Research Council (ERC) via the ERC Synergy Grant *ECOGAL* (grant 855130) and from the French Agence Nationale de la Recherche (ANR) through the project *COSMHIC* (ANR-20-CE31-0009). A.S. gratefully acknowledges support by the Fondecyt Regular (project code 1220610), and ANID BASAL project FB210003. R.A. gratefully acknowledges support from ANID Beca Doctorado Nacional 21200897. R.G.M. acknowledges support from UNAM-PAPIIT project IN108822 and from CONAHCyT Ciencia de Frontera project ID 86372. Part of this work was performed at the high-performance computers at IRyA-UNAM. T.Cs. and M.B. have received financial support from the French State in the framework of the IdEx Université de Bordeaux Investments for the future Program. A.G. acknowledges support from the NSF under grants AST 2008101 and CAREER 2142300. M.B. is a postdoctoral fellow in the University of Virginia’s VICO collaboration and is funded by grants from the NASA Astrophysics Theory Program (grant num- ber 80NSSC18K0558) and the NSF Astronomy & Astrophysics program (grant number 2206516). P.S. was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI Number JP22H01271 and JP23H01221) of JSPS. R.A. gratefully acknowledges support from ANID Beca Doctorado Nacional 21200897. A.K. and L.B. gratefully acknowledges support from ANID BASAL project FB210003. S.R. acknowledges the funding and support of ANID-Subdirección de Capital Humano Magíster/Nacional/2021-22211000. G.B. acknowledge support from the PID2020-117710GB-I00 grant funded by MCIN/AEI(10.13039/501100011033 A.G. acknowledges the support of the Programme National ‘Physique et Chimie du Milieu Interstellaire’ (PCMI) of CNRS/INSU with INC/INP co-funded by CEA and CNES. H.-L. Liu is supported by Yunnan Fundamental Research Project (grant No. 202301AT070118, 202401AS070121). This work is supported by the China-Chile Joint Research Fund (CCJRF No. 2312). CCJRF is provided by Chinese Academy of Sciences South America Center for Astronomy (CASSACA) and established by National Astronomical Observatories, Chinese Academy of Sciences (NAOC) and Chilean Astronomy Society (SOCHIAS) to support China-Chile collaborations in astronomy. P. García is sponsored by the Chinese Academy of Sciences (CAS), through a grant to the CAS South America Center for Astronomy (CASSACA).

120 natexlab

(ref: Rodrigo21) Álvarez-Gutiérrez, R. H., Stutz, A. M., Law, C. Y., et al. 2021, ApJ, 908, 86

(ref: rodrigo24) Álvarez-Gutiérrez, R. H., Stutz, A. M., Sandoval-Garrido, N., et al. 2024, A&A, 689, A74

(ref: andre2019) André, P., Arzoumanian, D., Könyves, V., Shimajiri, Y., & Palmeirim, P. 2019, A&A, 629, L4

(ref: anirudh2023) Anirudh, R., Eswaraiah, C., Jiao, S., & Jose, J. 2023, Journal of Astrophysics and Astronomy, 44, 59

(ref: Antyufeyev) Antyufeyev, O. V., Shulga, V. M., & Zinchenko, I. I. 2016, Kinematics and Physics of Celestial Bodies, 32, 276

(ref: Armante) Armante, M., Gusdorf, A., Louvet, F., et al. 2024, A&A, 686, A122

(ref: Arzoumanian) Arzoumanian, D., Arakawa, S., Kobayashi, M. I. N., et al. 2023, ApJL, 947, L29

(ref: john) Bally, J., Langer, W. D., Stark, A. A., & Wilson, R. W. 1987, ApJL, 312, L45

(ref: bergin2001) Bergin, E. A., Ciardi, D. R., Lada, C. J., Alves, J., & Lada, E. A. 2001, ApJ, 557, 209

(ref: Bergin) Bergin, E. A. & Tafalla, M. 2007, ARA&A, 45, 339

(ref: Beuther) Beuther, H., Walsh, A. J., Johnston, K. G., et al. 2017, A&A, 603, A10

(ref: Melisse) Bonfand, M., Csengeri, T., Bontemps, S., et al. 2024, A&A, 687, A163

(ref: bonne) Bonne, L., Bontemps, S., Schneider, N., et al. 2020, A&A, 644, A27

(ref: Braine2020) Braine, J., Hughes, A., Rosolowsky, E., et al. 2020, A&A, 633, A17

(ref: Braine2018) Braine, J., Rosolowsky, E., Gratier, P., Corbelli, E., & Schuster, K. F. 2018, A&A, 612, A51

(ref: brouillet) Brouillet, N., Despois, D., Molet, J., et al. 2022, A&A, 665, A140

(ref: Gemma2011) Busquet, G., Estalella, R., Zhang, Q., et al. 2011, A&A, 525, A141

(ref: CASA) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Caselli2002) Caselli, P., Benson, P. J., Myers, P. C., & Tafalla, M. 2002a, ApJ, 572, 238

(ref: Caselli95) Caselli, P., Myers, P. C., & Thaddeus, P. 1995, ApJL, 455, L77

(ref: Caselli1) Caselli, P., Walmsley, C. M., Zucconi, A., et al. 2002b, ApJ, 565, 331

(ref: Caselli2) Caselli, P., Walmsley, C. M., Zucconi, A., et al. 2002c, ApJ, 565, 344

(ref: Chen2019) Chen, H.-R. V., Zhang, Q., Wright, M. C. H., et al. 2019, ApJ, 875, 24

(ref: Nichol) Cunningham, N., Ginsburg, A., Galván-Madrid, R., et al. 2023, arXiv e-prints, arXiv:2306.14710

(ref: Dale) Dale, J. E., Ngoumou, J., Ercolano, B., & Bonnell, I. A. 2014, MNRAS, 442, 694

(ref: Daniel2005) Daniel, F., Dubernet, M. L., Meuwly, M., Cernicharo, J., & Pagani, L. 2005, MNRAS, 363, 1083

(ref: Pierre) Dell’Ova, P., Motte, F., Gusdorf, A., et al. 2024, arXiv e-prints, arXiv:2407.07610

(ref: danidiaz) Dı́az-González, D. J., Galván-Madrid, R., Ginsburg, A., et al. 2023, arXiv e-prints, arXiv:2310.13872

(ref: Sami) Dib, S., Zhou, J. W., Comerón, S., et al. 2024, arXiv e-prints, arXiv:2405.00095

(ref: Manuel2014) Fernández-López, M., Arce, H. G., Looney, L., et al. 2014, ApJL, 790, L19

(ref: fontani2006) Fontani, F., Caselli, P., Crapsi, A., et al. 2006, A&A, 460, 709

(ref: Roberto) Galván-Madrid, R., Dı́az-González, D. J., Motte, F., et al. 2024, arXiv e-prints, arXiv:2407.07359

(ref: roberto2009) Galván-Madrid, R., Keto, E., Zhang, Q., et al. 2009, ApJ, 706, 1036

(ref: Roberto2010) Galván-Madrid, R., Zhang, Q., Keto, E., et al. 2010, ApJ, 725, 17

(ref: adam22) Ginsburg, A., Csengeri, T., Galván-Madrid, R., et al. 2022a, A&A, 662, A9

(ref: PySpecKit11) Ginsburg, A. & Mirocha, J. 2011, PySpecKit: Python Spectroscopic Toolkit, Astrophysics Source Code Library, record ascl:1109.001

(ref: PySpecKit22) Ginsburg, A., Sokolov, V., de Val-Borro, M., et al. 2022b, AJ, 163, 291

(ref: Valentina19) González Lobos, V. & Stutz, A. M. 2019, MNRAS, 489, 4771

(ref: green74) Green, S., Montgomery, J. A., J., & Thaddeus, P. 1974, ApJL, 193, L89

(ref: Ruben2020) Guerrero-Gamboa, R. & Vázquez-Semadeni, E. 2020, ApJ, 903, 136

(ref: Hacar2017) Hacar, A., Alves, J., Tafalla, M., & Goicoechea, J. R. 2017, A&A, 602, L2

(ref: hacar2023) Hacar, A., Clark, S. E., Heitsch, F., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 153

(ref: Hacar2024) Hacar, A., Socci, A., Bonanomi, F., et al. 2024, A&A, 687, A140

(ref: hacar2011) Hacar, A. & Tafalla, M. 2011, A&A, 533, A34

(ref: Haworth) Haworth, T. J., Shima, K., Tasker, E. J., et al. 2015, MNRAS, 454, 1634

(ref: Henshaw) Henshaw, J. D., Caselli, P., Fontani, F., Jiménez-Serra, I., & Tan, J. C. 2014, MNRAS, 440, 2860

(ref: issac) Issac, N., Tej, A., Liu, T., & Wu, Y. 2020, MNRAS, 499, 3620

(ref: Ivanov) Ivanov, D., Bu, C., Hillenbrand, P.-M., et al. 2024, in American Astronomical Society Meeting Abstracts, Vol. 244, American Astronomical Society Meeting Abstracts, 222.04

(ref: Izquierdo) Izquierdo, A. F., Galván-Madrid, R., Maud, L. T., et al. 2018, MNRAS, 478, 2505

(ref: jorgensen2004) Jørgensen, J. K., Schöier, F. L., & van Dishoeck, E. F. 2004, A&A, 416, 603

(ref: kim2022) Kim, S., Lee, C. W., Tafalla, M., et al. 2022a, ApJ, 940, 112

(ref: Kim) Kim, S., Lee, C. W., Tafalla, M., et al. 2022b, ApJ, 940, 112

(ref: kirk24) Kirk, J. M., Ward-Thompson, D., Di Francesco, J., et al. 2024, MNRAS

(ref: Klaassen) Klaassen, P. D., Johnston, K. G., Leurini, S., & Zapata, L. A. 2015, A&A, 575, A54

(ref: shuo) Kong, S., Whitworth, D. J., Smith, R. J., & Hamden, E. T. 2022, MNRAS, 517, 4679

(ref: lada) Lada, C. J. & Lada, E. A. 2003, ARA&A, 41, 57

(ref: Lee2014) Lee, K. I., Fernández-López, M., Storm, S., et al. 2014, ApJ, 797, 76

(ref: yueh) Lee, Y.-N. & Hennebelle, P. 2016, A&A, 591, A30

(ref: Leurini2013) Leurini, S., Codella, C., Gusdorf, A., et al. 2013, A&A, 554, A35

(ref: Leurini2011_1) Leurini, S., Codella, C., Zapata, L., et al. 2011a, A&A, 530, A12

(ref: Leurini2014) Leurini, S., Gusdorf, A., Wyrowski, F., et al. 2014, A&A, 564, L11

(ref: Leurini2008) Leurini, S., Hieret, C., Thorwirth, S., et al. 2008a, A&A, 485, 167

(ref: Leurini2009) Leurini, S., Hieret, C., Thorwirth, S., et al. 2008b, A&A, 485, 167

(ref: Leurini2011_2) Leurini, S., Pillai, T., Stanke, T., et al. 2011b, A&A, 533, A85

(ref: Leurini2019) Leurini, S., Schisano, E., Pillai, T., et al. 2019, A&A, 621, A130

(ref: li23) Li, X.-M., Zhang, G.-Y., Men’shchikov, A., et al. 2023, A&A, 674, A225

(ref: Lippok2013) Lippok, N., Launhardt, R., Semenov, D., et al. 2013, A&A, 560, A41

(ref: liu2015) Liu, H. B., Galván-Madrid, R., Jiménez-Serra, I., et al. 2015, ApJ, 804, 37

(ref: hongli2020) Liu, H.-L., Sanhueza, P., Liu, T., et al. 2020, ApJ, 901, 31

(ref: hongli2019) Liu, H.-L., Stutz, A., & Yuan, J.-H. 2019, MNRAS, 487, 1259

(ref: hongli2023) Liu, H.-L., Tej, A., Liu, T., et al. 2023, MNRAS, 522, 3719

(ref: Louvet2016) Louvet, F., Motte, F., Gusdorf, A., et al. 2016, A&A, 595, A122

(ref: Fabien) Louvet, F., Sanhueza, P., Stutz, A., et al. 2024, arXiv e-prints, arXiv:2407.18719

(ref: Lu) Lu, X., Zhang, Q., Liu, H. B., et al. 2018, The Astrophysical Journal, 855, 9

(ref: Jeffrey) Mangum, J. G. & Shirley, Y. L. 2017, Corrigendum: How to Calculate Molecular Column Density, Publications of the Astronomical Society of the Pacific, Volume 129, Issue 976, pp. 069201 (2017).

(ref: Maret) Maret, S., Ceccarelli, C., Caux, E., et al. 2004, A&A, 416, 577

(ref: Menshchikov) Men’shchikov, A. 2021, A&A, 649, A89

(ref: Minh) Minh, Y. C., Liu, H. B., Galvań-Madrid, R., et al. 2018, ApJ, 864, 102

(ref: montillaud) Montillaud, J., Juvela, M., Vastel, C., et al. 2019, A&A, 631, A3

(ref: Mori) Mori, S., Aikawa, Y., Oya, Y., Yamamoto, S., & Sakai, N. 2024, ApJ, 961, 31

(ref: motte22) Motte, F., Bontemps, S., Csengeri, T., et al. 2022, A&A, 662, A8

(ref: anualmotte) Motte, F., Bontemps, S., & Louvet, F. 2018, ARA&A, 56, 41

(ref: nony) Nony, T., Galván-Madrid, R., Motte, F., et al. 2023, A&A, 674, A75

(ref: Laurent) Pagani, L., Daniel, F., & Dubernet, M.-L. 2008, working paper or preprint

(ref: Pan) Pan, S., Liu, H.-L., & Qin, S.-L. 2024, ApJ, 960, 76

(ref: peretto) Peretto, N. & Fuller, G. A. 2009, A&A, 505, 405

(ref: Pety) Pety, J., Guzmán, V. V., Orkisz, J. H., et al. 2017, A&A, 599, A98

(ref: pirogov23) Pirogov, L. E., Zemlyanukha, P. M., Dombek, E. M., & Voronkov, M. A. 2023, Astronomy Reports, 67, 1355

(ref: Plunkett) Plunkett, A. L., Fernández-López, M., Arce, H. G., et al. 2018, A&A, 615, A9

(ref: poetau1) Pouteau, Y., Motte, F., Nony, T., et al. 2022, A&A, 664, A26

(ref: poetau2) Pouteau, Y., Motte, F., Nony, T., et al. 2023, A&A, 674, A76

(ref: Priestley) Priestley, F. D., Clark, P. C., Glover, S. C. O., et al. 2023, MNRAS, 526, 4952

(ref: Elena) Redaelli, E., Bizzocchi, L., Caselli, P., et al. 2019, A&A, 629, A15

(ref: Elena22) Redaelli, E., Bovino, S., Sanhueza, P., et al. 2022, ApJ, 936, 169

(ref: Simon) Reyes-Reyes, S. D., Stutz, A. M., Megeath, S. T., et al. 2024, MNRAS

(ref: Sabatini2019) Sabatini, G., Giannetti, A., Bovino, S., et al. 2019, MNRAS, 490, 4489

(ref: Patricio2021) Sanhueza, P., Girart, J. M., Padovani, M., et al. 2021, ApJL, 915, L10

(ref: Patricio2012) Sanhueza, P., Jackson, J. M., Foster, J. B., et al. 2012, ApJ, 756, 60

(ref: Schneider) Schneider, N., Csengeri, T., Bontemps, S., et al. 2010, A&A, 520, A49

(ref: Schwarz2019) Schwarz, K. R., Teague, R., & Bergin, E. A. 2019, ApJL, 876, L13

(ref: shirley2015) Shirley, Y. L. 2015, PASP, 127, 299

(ref: Storm) Storm, S., Mundy, L. G., Fernández-López, M., et al. 2014, ApJ, 794, 165

(ref: amy2018.2) Stutz, A. M. 2018, MNRAS, 473, 4890

(ref: amy2018) Stutz, A. M., Gonzalez-Lobos, V., & Gould, A. 2018, arXiv e-prints, arXiv:1807.11496

(ref: amy2016) Stutz, A. M. & Gould, A. 2016, A&A, 590, A2

(ref: Amy2015) Stutz, A. M. & Kainulainen, J. 2015, A&A, 577, L6

(ref: tafalla2014) Tafalla, M. & Hacar, A. 2014, in Dense Cores: Origin, Evolution, and Collapse, Vol. 4, 103.01

(ref: Tatematsu) Tatematsu, K., Kandori, R., Umemoto, T., & Sekimoto, Y. 2008, PASJ, 60, 407

(ref: tadeus75) Thaddeus, P. & Turner, B. E. 1975, ApJL, 201, L25

(ref: tobin2013) Tobin, J. J., Bergin, E. A., Hartmann, L., et al. 2013, ApJ, 765, 18

(ref: Tobin) Tobin, J. J., Hartmann, L., Bergin, E., et al. 2012, The Astrophysical Journal, 748, 16

(ref: towner) Towner, A. P. M., Ginsburg, A., Dell’Ova, P., et al. 2023, arXiv e-prints, arXiv:2310.13125

(ref: turner74) Turner, B. E. 1974, ApJL, 193, L83

(ref: hoff2017) van ’t Hoff, M. L. R., Walsh, C., Kama, M., Facchini, S., & van Dishoeck, E. F. 2017, A&A, 599, A101

(ref: Enrique2024) Vázquez-Semadeni, E., Hu, Y., Xu, S., Guerrero-Gamboa, R., & Lazarian, A. 2024, MNRAS, 530, 3431

(ref: Enrique) Vázquez-Semadeni, E., Palau, A., Ballesteros-Paredes, J., Gómez, G. C., & Zamora-Avilés, M. 2019, MNRAS, 490, 3061

(ref: Yang) Yang, D., Liu, H.-L., Tej, A., et al. 2023, ApJ, 953, 40

(ref: Naiping2018) Yu, N.-P., Xu, J.-L., Wang, J.-J., & Liu, X.-L. 2018, The Astrophysical Journal, 865, 135

(ref: Zapata2008) Zapata, L. A., Leurini, S., Menten, K. M., et al. 2008, AJ, 136, 1455

(ref: zhou2022) Zhou, J.-W., Liu, T., Evans, N. J., et al. 2022, MNRAS, 514, 6038

# N$_2$H$^+$ raw data

Figure [18](#fig:channelmap) displays different emission channels of the\
N$_2$H$^+$ (1-0) spectral line through the data-cube observed with ALMA (see § [2](#sec:data)). Out of the 215 channels of the data-cube, there are 110 that correspond to emission channels, which goes from -13.35 to 11.72 $\rm km\,s^{-1}$, with a spectral line resolution of 0.23 $\rm km\,s^{-1}$.

![](Figure/A1.png)

# PySpecKit experiment

To evaluate the performance of PySpecKit and determine the S/N threshold at which it provides reliable results, we conducted the following test: 1) We select a single spectrum from the data-cube, from regions with S/N \> 20, to fit it employing PySpecKit (with defined guesses and limits), obtaining a model and its respective parameters (input model). 2) We create a grid using this model, assigning a different S/N to each spectrum in the grid, artificially adding noise. 3) We fit the grid with PySpecKit (using the same guesses and limits as before), obtaining a new model for each spectrum (output models). By comparing parameters such as excitation temperature (T$_{\rm ex}$), optical depth ($\tau$), centroid velocity (V$_{\rm LSR}$), and line width ($\sigma_{\rm v}$) returned from the single spectrum (input model) versus the parameters returned from the grid (output model), we could assess the consistency of PySpecKit’s performance. This process was repeated for different spectra from the data-cube, fitting 1- and 2-velocity-components, conducting more than 200 different tests. The results of this experiment are consistent for both 1- and 2-velocity-component fits, showing that PySpecKit returns reliable values for S/N \> 9. In contrast, for spectra with S/N $<$ 9, the difference between the parameters from the input model and output models increases significantly, reaching values 3 times or more the standard deviation. Additionally, the uncertainties for each parameter rise to over the 30%, as expected. The Fig. [19](#fig:experiment1) and Fig. [20](#fig:experiment2) show the centroid velocity for the input and output models at different S/N levels, whose parameter exhibits the lowest uncertainties.

![](Figure/B1.png)

![](Figure/B2.png)

# PySpecKit parameters

The models returned by PySpecKit produce parameter maps of the excitation temperature (T$_{\rm ex}$), optical depth ($\tau$), centroid velocity (V$_{\rm LSR}$), and line width ($\sigma_{\rm v}$) for each velocity component fitted. Figures [21](#fig:temp_map) and [22](#fig:tau_map) show the T$_{\rm ex}$ and $\tau$ maps for the Blue- and Red-velocity component defined in § [3.4](#sec:bluest-and-reddest-velocity-component), while the Figures [6](#fig:momentmaps0) and [7](#fig:velocity_map) display the centroid velocity and line width maps for both same velocity components (see § [3.4](#sec:bluest-and-reddest-velocity-component)), respectively.

![image](Figure/C1_1.png) ![image](Figure/C1_2.png)

![image](Figure/C2_1.png) ![image](Figure/C2_2.png)

# Good and bad fitting examples

The 2-velocity-component fit of the N$_2$H$^+$ emission in G351.77 protocluster provides a more reliable fit for spectra that present multiple velocity components. However, this forces PySpecKit to fit “false velocity components” in spectra that reveal only one clear velocity component (see Fig. [23](#fig:specdef1comp_1) and Fig. [24](#fig:specdef1comp_2)). The two methods applied over the model fitted with 1- and 2-velocity-components (see § [3.3](#sec:best-fit-and-final-model)) enable us to define the best fit for each spectrum (see Fig. [\[fig:specwellfited1comp\]](#fig:specwellfited1comp) and Fig. [4](#fig:specwellfited2comp)).

![](Figure/D1.png)

![](Figure/D2.png)

# Infalling and rotating sphere model

The Fig. [25](#fig:model_rot) displays the modeled sphere under a Keplerian rotation (see Eq. [\[eq:model\]](#eq:model)) and its PV features produced in the PV diagrams. The Fig. [26](#fig:model_in) represent the infalling modeled sphere (see Eq. [\[eq:model\]](#eq:model)) and its PV features produced in the PV diagrams. The Fig. [27](#fig:model_in+rot) represent the modeled sphere under both Keplerian rotation and infall at the same time and its PV features observed in the PV diagrams. The figures Fig. [29](#fig:h2co_in+rot), Fig. [28](#fig:dcn_in+rot), Fig. [31](#fig:h2co_rot), Fig. [30](#fig:dcn_in), and Fig. [32](#fig:h2co_in) display the H$_2$CO and DCN spectral lines and its PV features observed in the PV diagrams, along with the PV features produced by the modeled sphere.

![](Figure/E1.png)

![](Figure/E2.png)

![](Figure/E3.png)

![](Figure/E4.png)

![](Figure/E5.png)

![](Figure/E6.png)

![](Figure/E7.png)

![](Figure/E8.png)

[^1]: <https://www.almaimf.com/>

[^2]: <https://github.com/ALMA-IMF/reduction>

[^3]: <https://casadocs.readthedocs.io/en/stable/api/tt/casatasks.imaging.tclean.html>

[^4]: <https://github.com/ALMA-IMF/reduction/blob/master/reduction/imaging_parameters.py>

[^5]: <https://pyspeckit.readthedocs.io/en/latest/example_n2hp_cube.html>

[^6]: <https://pyspeckit.readthedocs.io/en/latest/index.html#>

[^7]: <https://numpy.org/devdocs/reference/generated/numpy.histogram_bin_edges.html>

[^8]: <https://nicolas11399.github.io/Nicolas.Sandoval-Garrido_PVV.github.io/>

</paper>

Write the methods card for this paper.