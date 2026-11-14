# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...684A.174P\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...684A.174P",
 "title": "High turbulence in the IM Lup protoplanetary disk. Direct observational constraints from CN and C<SUB>2</SUB>H emission",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Paneque-Carreño, T.",
 "n_authors": 7,
 "arxiv_id": "2312.04618",
 "doi": "10.1051/0004-6361/202347757",
 "alma_projects_linked_by_archive": [
  "2019.1.01357.S"
 ]
}
```

Paper text:
<paper>
# High turbulence in the IM Lup protoplanetary disk

Constraining turbulence in disks is key to understanding their evolution via the transport of angular momentum. Measurements of high turbulence remain elusive, and methods for estimating turbulence mostly rely on complex radiative transfer models of the data. Using the disk emission from IM Lup, a source proposed to be undergoing magneto-rotational instabilities (MRIs) and to possibly have high turbulence values in the upper disk layers, we present a new way of directly measuring turbulence without the need of radiative transfer or thermochemical models.

Through the characterization of the CN and C$_2$H emission in IM Lup, we aim to connect the information on the vertical and thermal structure of a particular disk region to derive the turbulence at that location. By using an optically thin tracer, it is possible to directly measure turbulence from the nonthermal broadening of the line.

The vertical layers of the CN and C$_2$H emission were traced directly from the channel maps using ALFAHOR. By comparing their position to that of optically thick CO observations, we were able to characterize the kinetic temperature of the emitting region. Using a simple parametric model of the line intensity with DISCMINER, we accurately measured the emission linewidth and separated the thermal and nonthermal components. Assuming that the nonthermal component is fully turbulent, we were able to directly estimate the turbulent motions at the studied radial and vertical location of CN emission.

IM Lup shows a high turbulence of Mach 0.4-0.6 at $z/r \sim$ 0.25. Considering previous estimates of low turbulence near the midplane, this may indicate a vertical gradient in the disk turbulence, which is a key prediction in MRI studies. CN and C$_2$H are both emitting from a localized upper disk region at $z/r =$0.2-0.3, in agreement with thermochemical models.

# Introduction

The study of planet formation requires high sensitivity observations that can spatially and spectrally resolve the motions of the material in protoplanetary disks around young stars. In this context, the Atacama Large Millimeter/submillimeter Array (ALMA) is a unique facility, able to characterize these objects and their evolution mechanisms, which depend on the transportation of angular momentum (cite: Lynden_Bell_Pringle_1974). Turbulence is the mechanism proposed to shape the surface density of disks, by transporting angular momentum through velocity fluctuations and providing an effective viscosity at microscopic scales (cite: Shakura_Sunyaev_1973_visc). There are many hydrodynamic processes that could be the origin of turbulent motions (cite: Lesur_ppvii_2023); however, direct measurements of turbulence in protoplanetary disks have been hard to obtain, with only a few upper limits (cite: Hughes_2009_turb; Flaherty_2015_hd16_weakturb; Teague_2016_turb_TWHya) and one candidate with measured turbulence, DM Tau. In this system, high spatial and spectral resolution ALMA observations of CS allowed (cite: Guilloteau_2012_turb_dmtau) to initially measure turbulence values of 0.3-0.5$c_s$ (see also the initial studies by (cite: Guilloteau_Dutrey_1998) and (cite: Dartois_2003)). A later study by (cite: Flaherty_2020_DMTau) obtained lower, but still significant, turbulence values of 0.25-0.33$c_s$ through modeling of CO emission in DM Tau.

Current methods used to constrain turbulence mostly depend on comparing observations to complex parametric and radiative transfer models, which depend on fundamental physical disk properties such as surface density and temperature structure (cite: Hughes_2009_turb; Guilloteau_2012_turb_dmtau; Flaherty_2015_hd16_weakturb; Flaherty_2017_DCOp; Flaherty_2020_DMTau). While these methods constrain their best-fit parameters with state-of-the-art analysis, there are multiple effects that are hard to account for since precisely resolving the gas surface density profile requires knowledge of the dust grain distribution and excitation conditions of the observed molecule (cite: MAPS_Zhang; Miotello_ppvii_2023). Furthermore, the presence of substructure in the disk may or may not cause gaps and rings in the surface density, depending on their origin, which is also not trivial to determine (cite: Rosotti_2021_CITau; MAPS_Zhang; Teague_2018_hd16planet).

Due to their complexity, previous uses of these models to extract disk turbulence have assumed a single turbulence value for the whole protoplanetary disk, neglecting the possibility of a radial or vertical dependence. However, turbulence could have vertical variations, depending on the launching mechanism (cite: Forgan_2012; Simon_2015; shi_chiang_2014), and while various molecular tracers are used to probe the vertical structure in searches for vertical turbulence variations (cite: Flaherty_2017_DCOp), locating the exact position of the molecular emission in the disk is not straightforward in the modeling process and in some cases presents strong discrepancies with observational constraints. A successful case is the best-fit model to extract turbulence in DM Tau, where the CO ($J = 2-1$) emission is expected to arise from a layer of $z/r \sim$0.3-0.4 (cite: Flaherty_2020_DMTau), in good agreement with observational constraints from (cite: Law_2023_12CO_surf). However, analysis of HD 163296, where no significant turbulence was detected, predicts that CO ($J = 2-1$) emission is coming from $z/r <$0.1 (cite: Flaherty_2017_DCOp), which is many times lower than the measured emission surface of CO ($J = 2-1$), located at $z/r \sim$0.3 (cite: MAPS_Law_Surf; Paneque_2023_vert). These differences may be due to the limitations of the method, a lack of spatial resolution, or errors in the assumed density and temperature structure.

To alleviate these issues, this work focuses on directly tracing the vertical location of optically thin CN and C$_2$H transitions, measuring the radial profile of line broadening due to nonthermal motions, and relating this to vertically and radially resolved turbulence. CN and C$_2$H are expected to originate from chemical processes requiring energetic UV-photon radiation (cite: Visser_2018; Cazzoletti_2018_CN; Bergin_2016_c2h; Teague_2020_CN), and therefore their emission should arise from a sweet spot located at high elevation from the midplane (cite: Schreyer_2008; Cazzoletti_2018_CN), in a zone known as the photon-dominated region (cite: Aikawa_2002). As the emission should come from a vertically thin slab, it is possible to accurately determine the location of the emission surfaces of CN and C$_2$H despite the emission being optically thin (cite: Paneque-Carreno_2022_Elias_CN). In parallel, optically thick CO isotopologs can be used as tracers of the disk structure, with the resolved vertical emission location (cite: MAPS_Law_Surf; Paneque-Carreno_2022_Elias_CN) allowing us to provide a global three-dimensional characterization of the temperature structure, molecular emission, and turbulence in the upper disk layers. This is ultimately achieved by measuring the emission linewidth and separating the thermal from the nonthermal component. As we assume optically thin molecular emission, the nonthermal component is assumed to be mainly turbulent (cite: Hacar_2016_optdepth). A key tool in our analysis is the use of DISCMINER (cite: izquierdo_2021_discminer1; Izquierdo_2023_discminer2), a disk analysis package that fits the spectra per pixel of our data to precisely extract and parametrize the radial linewidth profile of the data, accounting for the effects of beam convolution and upper and lower emission surfaces.

Our work focuses on the protoplanetary disk around the young K5 star IM Lup, located at a distance of 158 pc (cite: Gaia_DR3). This system has been extensively studied using multiple tracers. Infrared scattered light shows a large, vertically extended disk, with radial rings and gaps (cite: Avenhaus_2018). Millimeter continuum traces tightly wound spiral arms and an outer ring (cite: Cleeves_LupusModel_2016; DSHARP_Huang_radial; DSHARP_Huang_Spirals), and gas line emission shows a rich molecular reservoir (cite: Pinte_2018_method; MAPS_Oberg). Recent observational and theoretical works have proposed that IM Lup has an inner turbulent disk (cite: Bosman_2023_imlup) and possible turbulent velocities of $\sim$100 m s$^{-1}$ in the outer disk (cite: Cleeves_LupusModel_2016). Due to its inclination and vertical extent, it is possible to trace the vertical disk structure and molecular layering of various lines; however, previous studies have been unable to extract CN or C$_2$H vertical profiles due the low signal-to-noise ratio (S/N) of the lower rotational transitions (cite: Paneque_2023_vert). New, higher-energy ALMA Band 7 transitions have sufficient S/N for an adequate characterization of their radial, azimuthal, and vertical features.

This paper is structured as follows. Section 2 presents the data and explains the calibration procedures. Section 3 studies the emission morphology, characterizing the vertical extent of the disk and the brightness temperature of CN and C$_2$H and comparing them to those of CO isotopologs. Section 4 shows the parametric model we used to extract the linewidth from CN, and Section 5 presents our results on the radial turbulence profile as traced by CN. Finally, Section 6 discusses the findings of this work in the context of previous constrains, and Section 7 summarizes our main conclusions.

![](imlup_emission.pdf)

+:----------------:+:--------------:+:--------------:+:---------------:+:-----:+:----------------------:+:-----:+:-------------------:+:-:+
| Species          | $J$ Transition | $F$ Transition | Frequency       | $E_u$ | $A_{ul}$               | $g_u$ | Int. Flux $^{*}$    |   |
+------------------+----------------+----------------+-----------------+-------+------------------------+-------+---------------------+---+
|                  |                |                | (GHz)           | \(K\) | (s$^{-1}$ )            |       | (Jy km s$^{-1}$)    |   |
+------------------+----------------+----------------+-----------------+-------+------------------------+-------+---------------------+---+
| CN ($N=3-2$)     | $J=7/2-5/2$    | $F=7/2-5/2$    | 340.24759$^{a}$ | 32.67 | 3.797$\times$10$^{-4}$ | 8     | 4.710 $\pm$ 0.029   |   |
|                  |                +----------------+-----------------+-------+------------------------+-------+                     +---+
|                  |                | $F=9/2-7/2$    | 340.24786$^{a}$ | 32.67 | 4.13$\times$10$^{-4}$  | 10    |                     |   |
|                  |                +----------------+-----------------+-------+------------------------+-------+                     +---+
|                  |                | $F=5/2-3/2$    | 340.24854       | 32.67 | 3.67$\times$10$^{-4}$  | 6     |                     |   |
|                  |                +----------------+-----------------+-------+------------------------+-------+---------------------+---+
|                  |                | $F=5/2-5/2$    | 340.26177       | 32.67 | 0.45$\times$10$^{-4}$  | 6     | 0.133 $\pm$ 0.029   |   |
|                  |                +----------------+-----------------+-------+------------------------+-------+---------------------+---+
|                  |                | $F=7/2-7/2$    | 340.26495       | 32.67 | 0.34$\times$10$^{-4}$  | 8     | 0.137 $\pm$ 0.029   |   |
|                  +----------------+----------------+-----------------+-------+------------------------+-------+---------------------+---+
|                  | $J=5/2-3/2$    | $F=5/2-5/2$    | 340.00813       | 32.63 | 0.62$\times$10$^{-4}$  | 6     | 0.140 $\pm$ 0.001   |   |
|                  |                +----------------+-----------------+-------+------------------------+-------+---------------------+---+
|                  |                | $F=3/2-3/2$    | 340.01963       | 32.63 | 0.93$\times$10$^{-4}$  | 4     | 0.091 $\pm$ 0.001   |   |
|                  |                +----------------+-----------------+-------+------------------------+-------+---------------------+---+
|                  |                | $F=7/2-5/2$    | 340.03155       | 32.63 | 3.84$\times$10$^{-4}$  | 8     | 1.594 $\pm$ 0.001   |   |
|                  |                +----------------+-----------------+-------+------------------------+-------+---------------------+---+
|                  |                | $F=3/2-1/2$    | 340.03527$^{b}$ | 32.63 | 2.89$\times$10$^{-4}$  | 4     | 1.610 $\pm$ 0.001   |   |
|                  |                +----------------+-----------------+-------+------------------------+-------+                     +---+
|                  |                | $F=5/2-3/2$    | 340.03551$^{b}$ | 32.63 | 3.23$\times$10$^{-4}$  | 6     |                     |   |
+------------------+----------------+----------------+-----------------+-------+------------------------+-------+---------------------+---+
| C$_2$H ($N=4-3$) | $J=9/2-7/2$    | $F = 5-4$      | 349.33771       | 41.91 | 1.31$\times$10$^{-4}$  | 11    | 0.7416 $\pm$ 0.0002 |   |
|                  |                +----------------+-----------------+-------+------------------------+-------+                     +---+
|                  |                | $F = 4-3$      | 349.33899       | 41.91 | 1.28$\times$10$^{-4}$  | 9     |                     |   |
|                  +----------------+----------------+-----------------+-------+------------------------+-------+---------------------+---+
|                  | $J=7/2-5/2$    | $F = 4-3$      | 349.39928       | 41.93 | 1.25$\times$10$^{-4}$  | 9     | 0.5611 $\pm$ 0.0002 |   |
|                  |                +----------------+-----------------+-------+------------------------+-------+                     +---+
|                  |                | $F = 3-2$      | 349.40067       | 41.93 | 1.20$\times$10$^{-4}$  | 7     |                     |   |
+------------------+----------------+----------------+-----------------+-------+------------------------+-------+---------------------+---+

Table notes:

# Observations

This work uses ALMA Band 7 C$_2$H ($N = 4-3$) and CN ($N = 3-2$) observations of IM Lup (Project code: #2019.1.01357.S, PI: R.Teague) taken during the second semester of 2019 and first semester of 2021. After initial calibration through the ALMA pipeline (cite: Hunter_2023_ALMA_pipeline), the data were flux-calibrated and self-calibrated in phase and amplitude using only the line-free spectral windows and channels with the tools of Common Astronomy Software Applications (cite: McMullin_CASA) as described in the following.

The observations from each execution block (EB; seven in total) were aligned to a common phase center, considering the peak of the continuum emission of each EB as fitted by CASA task imfit. After alignment, an amplitude scaling was applied to correct for the relative flux scale variations between EBs, which were $<$10%, following the procedures of ALMA large program DSHARP (cite: DSHARP_Andrews). Self-calibration was then applied to the short-baseline observations (two EBs, with a longest baseline of 0.3 km). Five rounds of phase and one round of amplitude calibration were performed, until there was no further improvement of the S/N, starting with a solution interval of 3360s and taking half the time step in each subsequent round. The S/N improvement in the short-baseline data was 726%, from 190 to 1380. Finally, self-calibration was performed on the joint dataset of the previously self-calibrated short baselines, concatenated to the flux-calibrated long baselines (five EBs, with a maximum baseline of 1.5km). Three rounds of phase and one round of amplitude calibration were performed, the initial time solution interval was 4800s and the final S/N increase was 428%, from 301 to 1289.

Each of the calibration solutions from the continuum analysis was then applied to the whole dataset, to correct spectral windows and channels with line emission. Using the CASA task uvcontsub, we produced continuum-subtracted measurement sets for each of our target emission lines. Each C$_2$H and CN hyperfine group was imaged using tclean with Briggs weighting and Keplerian masking[^1]. Multiple Keplerian masks, one for each of the expected hyperfine components, were used in the cleaning. A stellar mass of 1.1M$_\odot$ (cite: MAPS_Teague) and a constant $z/r$ value of 0.2 and 0.3 was used for C$_2$H and CN emission, respectively. To compromise between optimal angular resolution and high S/N, C$_2$H emission was imaged using a robust parameter of 2.0, resulting in a 0.27$\ensuremath{''} \times$ 0.25$\ensuremath{''}$ beam (PA: 64.83$^{\circ}$). CN is imaged using a 0.5 robust parameter with a final beam of 0.22$\ensuremath{''} \times$ 0.19$\ensuremath{''}$ (PA: 57.56$^{\circ}$). JvM correction (cite: MAPS_Czekala) was applied to our final images to account for the noise caused by having non-Gaussian beams. The epsilon correction factors are 0.24 and 0.52 or C$_2$H and CN, respectively (cite: MAPS_Czekala). The images used in the analysis where obtained using a channel spacing of 200 m s$^{-1}$ for C$_2$H and 100 m s$^{-1}$ for CN, to optimize spectral resolution and S/N. The final rms of the images for each molecule are 0.6 mJy/beam and 1 mJy/beam for C$_2$H and CN, respectively.

Figure [1](#imlup_emission) shows the integrated intensity maps (moment 0) and stacked spectra for the data imaged at the native spectral resolution, 50 m s$^{-1}$. The spectra were computed using the GoFish (cite: gofish) function, integrated_spectrum, over the whole disk. Each of the detected hyperfine components are marked with an orange vertical line and their properties, together with the integrated fluxes indicated in Table [\[table_molec\]](#table_molec). A clear ring is observed in both tracers for all hyperfine groups, a detailed analysis of this feature can be found in Appendix A.

# Emission morphology

## Vertical profile

From the channel maps it is possible to visually identify the CN and C$_2$H emission originating from the upper and lower sides of the disk. Tracing the vertical location of each molecule allows us to characterize the disk structure and physical conditions of the emitting gas in defined regions. To extract the vertical profiles, we used the code ALFAHOR (cite: Paneque_2023_vert), which traces the maxima of emission within a given masked region. The masks are visually determined and encircle the far and near sides of the disk upper surface (cite: Pinte_2018_method; Paneque-Carreno_2022_Elias_CN; Paneque_2023_vert). Only channels where both near and far sides of the upper surface can be confidently identified are used for this analysis. Figures [15](#channels_cn) and [16](#channels_c2h) present the masks and location of the emission maxima for each of the occupied transitions.

A key assumption of this method is that the intensity maxima trace a single isovelocity along each channel. Due to the strong blending of hyperfine components in the CN emission and the low S/N of some detected transitions, we only used the unblended and strongest component CN $N=3-2 J=5/2-3/2 F= 7/2-5/2$. C$_2$H also has blending in both transitions; however, it has a sufficient separation that we can identify both components in each group (see Fig. [2](#examp_height)). However, we extracted the surface only using the $J=9/2-7/2$ hyperfine group, as it has a higher S/N. We expect that these transitions are representative of the spatial location of all the detected transitions of the same molecule, as they all have similar upper state energies (see Table [\[table_molec\]](#table_molec)) and thus, originate from the same layer.

![](example_surf_chan.pdf)

![](best_fit_height.pdf)

The resulting vertical distribution is parametrized with an exponentially tapered power law to capture the inner flared surface, plateau and turnover regions at larger radii (cite: Teague_2019_meridonial) following

$$\begin{equation}
z(r) = z_0\times \left(\frac{r}{100\,\mathrm{au}}\right)^{\phi} \times \exp\left[\left(\frac{-r}{r_{\mathrm{taper}}}\right)^{\psi}\right].
\end{equation}$$

The best-fit values for $z_0$, $\phi$, $\psi,$ and $r_{\mathrm{taper}}$ were found using a Markov chain Monte Carlo sampler as implemented by emcee (cite: emcee_ref) and shown in Table [1](#table_bestfit). Figure [3](#best_fit_heights) shows the data considering all of the extracted maxima for CN and C$_2$H, together with the best-fit exponentially tapered power-law model.

|                  |        CN $N = 3-2$        |      C$_2$H $N = 4-3$      |
|:----------------:|:--------------------------:|:--------------------------:|
|    $z_0$ (au)    | 40.29 $^{+12.36}_{-13.87}$ |  8.03 $^{+4.79}_{-3.33}$   |
|      $\phi$      |  4.91 $^{+0.22}_{-0.38}$   |  6.43 $^{+0.55}_{-0.84}$   |
| $r_{taper}$ (au) | 65.72 $^{+26.77}_{-11.49}$ | 78.16 $^{+44.18}_{-21.86}$ |
|      $\psi$      |  1.03 $^{+0.13}_{-0.06}$   |  1.18 $^{+0.23}_{-0.12}$   |

: Best-fit parameters of vertical profiles.

Comparison with previously studied CO isotopolog emission from IM Lup (cite: Paneque_2023_vert) is presented in Figure [3](#best_fit_heights) demonstrating that the location of CN ($N=3-2$) is comparable to that of $^{13}$CO ($J=2-1$). The C$_2$H ($N=4-3$) emission is located slightly below, tracing the same region as C$^{18}$O ($J=2-1$). We note that C$_2$H presents a large scatter, likely due to the lower S/N of the observations; however, our result on the average vertical profile (panel C of Fig. [3](#best_fit_heights)) is consistent with $z/r \sim$0.2 expected from the visual channel map analysis (Fig. [2](#examp_height)).

![](brightness_temp_maps_prof.pdf)

## Brightness temperature

Considering the best-fit vertical surfaces, the radial peak brightness temperature profiles were extracted from the peak intensity maps (moment 8). The conversion from peak intensity ($I$) to brightness temperature ($T_b$) was done using Planck’s law,

$$\begin{equation}
    T_b = \frac{h \nu}{k} \ln^{-1}\left(1 + \frac{2h\nu^3}{I c^2}\right),
\end{equation}$$

where $h$ is the Planck constant, $k$ the Boltzmann constant, $c$ the speed of light, and $\nu$ the frequency of the emission. To compare the brightness temperatures of CN and C$_2$H to those of the CO isotopologs previously studied in (cite: Paneque_2023_vert), all brightness temperature profiles were calculated using cubes with an equal spectral resolution of 0.2 km s$^{-1}$ to match the resolution of the Molecules with ALMA at Planet-forming Scales (MAPS) Program data (cite: MAPS_Oberg).

![](model_channels_comp.pdf)

The peak intensity maps and brightness temperature profiles, compared to those of CO isotopologs (cite: Paneque_2023_vert), are presented in Figure [4](#brightness_temp). The radially extended bright feature along the major axis seen in the peak intensity maps for all tracers is a radiative transfer effect related to the higher density of isovelocity contours and does not indicate a physical feature. Based on our previous analysis we know that CN and C$_2$H emission is spatially colocated with $^{13}$CO; however, both transitions show lower brightness temperatures than $^{13}$CO for all hyperfine groups. The drop in temperature at the innermost radii is dominated by beam dilution as the emitting area becomes comparable to or smaller than the spatial resolution; however, this drop extends out to $\sim$150 au, which is beyond the beam size. Dust absorption is likely a big contributor to the low temperatures, as several works have shown that the inner disk of IM Lup is optically thick (cite: Cleeves_LupusModel_2016; sierra_2021_MAPS).

The brightness temperature may be a tracer of the excitation temperature of the region, but only in the cases where the emission is optically thick ($\tau>>$1), as it is proportional to $T_{ex}(1 - e^{-\tau})$. CO is expected to be abundant in IM Lup, in particular $^{12}$CO and $^{13}$CO should be optically thick (cite: Cleeves_LupusModel_2016) and therefore their brightness temperature may be taken as a tracer of the kinetic temperature in the region. On the other hand, CN and C$_2$H are expected to have lower column densities and be optically thin tracers (cite: Cazzoletti_2018_CN; MAPS_Bergner; Bergin_2016_c2h), which is corroborated by the lower brightness temperatures measured in this work. We note that the temperature difference between both CN hyperfine groups is due to the strong blending in the $J=7/2-5/2$ transition (see Fig. [1](#imlup_emission)), which means that the peak flux for a given pixel is the sum of multiple hyperfine components. This is the same situation that affects the integrated flux values shown in Table [\[table_molec\]](#table_molec).

# Parametric emission model: DISCMINER fit

Knowing that the molecular emission is optically thin enables us to directly determine turbulence from the nonthermal contributions to the linewidth (cite: Hacar_2016_optdepth). This is not possible in optically thick tracers (such as CO isotopologs) due to the additional opacity broadening that affects the linewidth in those cases, which is why in these cases radiative transfer models are needed to account for the opacity effect. Extracting the linewidth is not straightforward, it requires a parametric model that accounts for the vertically elevated emission, the upper and lower sides as well as radial intensity and velocity gradients. To this end, we used DISCMINER (cite: izquierdo_2021_discminer1), which allowed us to find the best-fit parametrization of our emission.

![](discminer_obs_comparison.pdf)

## Model setup

DISCMINER determines the best orientation, velocity, surface and line profile parameters for the observed emission by creating a model intensity, $I_m$ as a function of the disk cylindrical coordinates ($R, z$) and the velocity. The emission kernel has two components, one for the upper and another for the lower surface, which are well separated in the case of our studied emission. Contrary to previous works with DISCMINER, which focus on CO isotopolog emission (cite: izquierdo_2021_discminer1; Izquierdo_2021_hd16planet; Izquierdo_2023_discminer2), this work traces optically thin molecules that will be well reproduced by a Gaussian line profile (cite: Hacar_2016_optdepth). Therefore, we used a Gaussian kernel for each surface such that

$$\begin{equation}
  I_m(R,z;v_{chan}) = I_p\, \mathrm{exp}\left[-\frac{(v-v_{chan})^2}{\Delta V^{2}}\right],
\end{equation}$$

with $I_p$ being the peak intensity and $\Delta V$ the linewidth at a given radial and vertical distance from the star. Since we assumed fully optically thin emission, the final model intensity is given by the direct sum of the upper and lower disk surface intensity contributions and compared against the emission spectra extracted from each pixel of our observational data cube (cite: izquierdo_2021_discminer1; Izquierdo_2023_discminer2). Table [2](#table_discminer) indicates the equations used to model each of the disk attributes. Each emission surface is modeled independently as an exponentially tapered power law, the intensity is considered to be a power law with a Gaussian component, to account for the ring in the integrated emission maps (see Figure [1](#imlup_emission)). The linewidth is assumed to follow a simple radial and vertical power law (as indicated in Table [2](#table_discminer)).

| Attribute | Prescription |
|:---|:--:|
| Orientation | $i$, PA, $x_c$, $y_c$ |
| Velocity | $v_{\mathrm{rot}}=\sqrt{\frac{GM_*}{r^3}}R$, $v_{\mathrm{sys}}$ |
| Upper Surface | $z_{\mathrm{up}} = z_0 (R/D_0)^p$ exp$[-(R/R_t)^q]$ |
| Lower Surface | $z_{\mathrm{low}} = -z_0 (R/D_0)^p$ exp$[-(R/R_t)^q]$ |
| Peak intensity | $I_p = I_0 (R/D_0)^{p} (z/D_0)^{q} + I_g$ exp $\left[-\frac{(R - R_g)^2}{2 \sigma_{g}^{2}}\right ]$ |
| Line width | $\Delta V = L_0(R/D_0)^{p} (z/D_0)^{q}$ |

: Parametric model attributes.

Table notes: $G$ is the gravitational constant and $D_0$ = 100 au is a normalization factor. $R$ is the cylindrical radius and $z$ is the height from the midplane, always positive, $r$ is the spherical radius. The other variables are free parameters, even if named alike they are modeled independently for each attribute.

DISCMINER is not built to fit emission with multiple hyperfine components; therefore, we created a cube that only covers the emission of the strongest unblended hyperfine component of CN 3-2, J = 5/2 - 3/2 F= 7/2-5/2 (see Figure [1](#imlup_emission)). It is not possible to analyze the other CN hyperfine components, due to the strong blending of the high S/N lines, and the low signal of the other detections. C$_2$H is also excluded from this analysis due to its low S/N and the close blending of the lines, which does not allow us to isolate them as we can for CN (see Figure 3 for a comparison on how close the CN hyperfine components are compared to C$_2$H in the channel map emission). Future work incorporating hyperfine components to the DISCMINER kernel could allow us to optimize our model using the whole dataset, but it is beyond the scope of this study.

## Comparison to CN observations

The best-fit model parameters are found in Appendix C. Figure [5](#chan_discminer) shows the resulting model channel maps, convolved with a Gaussian beam to be at the same spatial resolution as the observations. The 5$\sigma$ residuals are presented in the bottom row, no coherent or systematic pattern is identified. Figure [6](#comp_discminer_obs) shows further comparison between the model and data. There is good agreement between the derived vertical and azimuthally averaged intensity profiles and the DISCMINER parametric forms. The rotation curve shows a $\sim$200m s$^{-1}$ residual between 200 and 250 au, which coincides with a $\sim$50m s$^{-1}$ negative residual in the linewidth. This velocity variation is also observed in $^{12}$CO (cite: Izquierdo_2023_discminer2) and the location of the feature is close to a dust gap at 209 au and a dust ring at 220 au (cite: DSHARP_Huang_radial), which may be related to these variations.

We note that the linewidth values extracted from the channel map images (red and gray curves, with uncertainty regions in lower right panel) are higher than the best-fit DISCMINER parametric form (traced by dashed black line). This is because the profiles extracted from the image correspond to direct measurements of the linewidth from the spectra extracted at each pixel in the image plane. These measurements will always be broader (have higher values) than the underlying molecular emission linewidth due to the linewidth broadening caused by the finite spatial resolution of the observations (cite: Teague_2020_CN). When we refer to the DISCMINER parametric form, we are describing what is expected to be the native molecular linewidth that, convolved with a Gaussian beam equal to the spatial resolution of the ALMA images ($\sim$0.22$\ensuremath{''}$), will match the broader values extracted directly from the data.

# Turbulence as traced by CN

The measured linewidth of an optically thin tracer will be dominated by doppler broadening caused by thermal and nonthermal motions (cite: Hacar_2016_optdepth). As we used a Gaussian kernel (see Eq. 3), our measured linewidth $\Delta V$ corresponds to the velocity dispersion such that the full width at half maximum (FWHM) of the kernel is $2\sqrt{ \mathrm{log}2} \,\Delta V$. The linewidth can then be written as

$$\begin{equation}
    \Delta V^2 = V_{\mathrm{th}}^2 + V_{\mathrm{non-th}}^2.
\end{equation}$$

The thermal component is well characterized and proportional to the ratio between the kinetic temperature and the molecular mass of the observed tracer (cite: Myers_Ladd_Fuller_1991). The nonthermal component can originate from non-Keplerian motion such as photo-evaporative winds, planet–disk interactions, or turbulence (cite: Fuller_Myers_1992; Hacar_2016_optdepth; Izquierdo_2023_discminer2). For this analysis we considered the case where nonthermal motion is fully due to turbulence; the implications and possibilities of other origins are reviewed in the discussion section. Therefore, the two components of the measured linewidth can be decomposed as

$$\begin{equation}
    \Delta V^2 =  \frac{2 k T_{kin}}{m_X}  + \varv_{\mathrm{turb}}^{2} .
\end{equation}$$

Here $k$ is the Boltzmann constant and $m_X$ the molecular mass, in this case, for CN, $m_X$ = 26.0 (cite: Klisch_1995_CN; lambda_database_Schoier_2005). The nonthermal broadening is assumed to be completely due to turbulence, $\varv_{\mathrm{turb}}$. Turbulence can then be expressed in terms of the Mach number, $\mathcal{M}$, such that

$$\begin{equation}
    \mathcal{M} =  \frac{\varv_{\mathrm{turb}}}{\sqrt{2} c_s}
,
\end{equation}$$

where $c_s$ is the local sound speed in the studied layer $c_s^2 = \frac{k T_{kin}}{\mu m_H}$ (cite: Balbus_Hawley_1998; Flaherty_2015_hd16_weakturb). We generally refer to turbulence in terms of the Mach number so it may be directly compared to previous works and estimations (cite: Flaherty_2015_hd16_weakturb; Flaherty_2017_DCOp; Flaherty_2020_DMTau; Teague_2016_turb_TWHya; Teague_2018_turb_nonlte).

![](turbulence_results_dm.pdf)

By spatially localizing the CN emission vertically and radially close to the optically thick CO isotopes, we have a tool to directly access the kinetic temperature without need to use parametric models or additional molecular transitions. Using the linewidth parametrization found by DISCMINER we can immediately calculate the turbulence radial profile, presented in Figure [7](#turb_imlup). Our results indicate turbulent motions of $\mathcal{M}=$0.4-0.6 at radii beyond $\sim$150 au. The shaded regions of the plot represent the variation of our results considering a 50 m s$^{-1}$ error in the linewidth measurement. While the statistical error of our fit is $<$5 m s$^{-1}$, we took the native resolution of our data as the largest possible deviation, in case effects such as Hanning smoothing are significantly affecting our linewidth extraction (cite: ALMA_tech_C10). Under the $\alpha$-prescription for turbulent viscosity (cite: Shakura_Sunyaev_1973_visc) it is possible to relate the turbulence Mach number $\mathcal{M}$ to $\alpha$ following, $\alpha \sim \mathcal{M}^{2}$ (cite: Rosotti_2023_turbulencerev). Our measurements indicate $\alpha \sim 10^{-1}$.

The total measured linewidth ($\Delta V$) and turbulence values increase steeply in the inner $\sim$150 au. While IM Lup has been proposed to be extremely turbulent in the inner disk (cite: Cleeves_LupusModel_2016; Bosman_2023_imlup) it is unclear if our analysis is sensitive to this effect, or if the high turbulence should extend beyond the innermost 20 au, given the lower estimated scale height for millimeter dust in this system (cite: Bosman_2023_imlup). Linewidth measurements are strongly affected by overlapping velocities in the inner disk (cite: Teague_2020_CN; Izquierdo_2021_hd16planet); therefore, we only considered the values beyond 150 au as accurate measurements and do not refer to the high values inward of 150 au.

The average total linewidth measured outward of 150 au is $\sim$221 m s$^{-1}$. Thermal broadening only accounts for 105-132 m s$^{-1}$, using the $^{13}$CO and $^{12}$CO brightness temperatures, respectively. Therefore, the nonthermal broadening ranges between 177 and 194 m s$^{-1}$ and would require temperatures $\sim$40 K higher than measured to account for it as thermal motion. Figures [8](#temp_linewidth) and [9](#spectra_pix_rich) illustrate the need of a high nonthermal component in order to explain the measured total linewidth (see Fig. [8](#temp_linewidth)) and the data spectra (see Fig. [9](#spectra_pix_rich)).

![](v_th_lineiwdth.pdf)

![](spectra_pix_comp.pdf)

# Discussion

## Vertical location of CN and C$_2$H

Our work traces the CN and C$_2$H emission originating from a vertical region similar to $^{13}$CO, at $z/r=$0.2-0.3 constrained radially between 50 and 350 au. These results are in agreement with chemical models of IM Lup that locate the tracer at $z/r =$0.2 (cite: Cleeves_2018). However, while in agreement with theoretical models, this is the first direct observational evidence of C$_2$H coming from vertically elevated layer in the outer disk, as previous works studying other protoplanetary disks had only traced C$_2$H inward of 150 au and closer to the midplane (cite: MAPS_Law_Surf; Paneque_2023_vert).

Both CN and C$_2$H are formed via UV-driven chemistry (cite: Nagy_2015_C2H; Bergin_2016_c2h; Visser_2018; Cazzoletti_2018_CN; Miotello_2019_c2h; MAPS_Guzman; MAPS_Bergner) and tracing their vertical distribution in various transitions will allow us to further understand the range of penetration that these energetic photons have toward the midplane, or the mixing processes that may result in some transitions tracing different vertical zones. The distribution of the small grains may have a particularly strong effect on how the UV field affects the disk (cite: Bergin_2016_c2h; maps_bosman). Combining scattered light observations with high resolution ALMA data of UV-sensitive molecular lines will give insight into these effects. Overall, future work should focus on characterizing differences in the vertical location of various transitions for a single system, particularly of CN and C$_2$H. IM Lup is the perfect laboratory for these studies.

## Origin of high turbulence in IM Lup

The physical structure of IM Lup has been thoroughly studied with models (cite: Cleeves_LupusModel_2016) that propose the existence of a turbulent inner disk (cite: Cleeves_2018; Bosman_2023_imlup) with high dust optical depth (cite: DSHARP_Huang_radial; sierra_2021_MAPS) that may be causing the cavity seen in molecular emission. Additionally, a series of instabilities may be ongoing in IM Lup. (cite: Bosman_2023_imlup) proposed that the turbulent inner disk could be related to vertical shear instability (cite: Urpin_Brandenburg_1998_VSI). The high disk-to-star mass ratio measured in multiple works (cite: Lodato_2023_mass_imlup; Cleeves_2018; MAPS_Zhang; sierra_2021_MAPS) suggests gravitational instabilities (cite: Kratter_Lodato_2016_GI) throughout some portion of the system. Finally, analysis of the ionization structure suggests a radial gradient in the cosmic ray ionization rate and adequate conditions for magneto-rotational instabilities (cite: Balbus_1991_MRI) in disk regions beyond the millimeter continuum disk edge ($\sim$313 au) or above 20 au or $z/r \sim$ 0.25 from the midplane (cite: Seifert_2021_MRI_imlup).

Indeed, high turbulence in this system is not surprising. Any of these instabilities, or their combined effect, could be causing turbulent motions. There have already been suggestions of nonthermal broadening from low-resolution CO data, as thermochemical models are able to explain the CO morphology using 100 m s$^{-1}$ turbulent velocities (cite: Cleeves_LupusModel_2016) a value within the order of our derived range of 177-194 m s$^{-1}$. In contrast with this, low turbulence values ($\alpha \sim 10^{-3}$) are derived from simultaneous modeling of millimeter (ALMA) and micrometer (SPHERE) dust observations (cite: Franceschi_2023_imlup_turbdust; Jiang_turb_dust). This low turbulence is mainly driven by the millimeter dust distribution, which traces the cold midplane. Through our analysis, we constrain high turbulence values ($\alpha \sim 10^{-1}$) traced by CN at $R>$150 au and in the vertically elevated disk layers (above the midplane) at $z/r = 0.25-0.3$, which would suggest a vertical gradient in the turbulence, with higher values in the upper disk and lower values toward the midplane. Theoretical MRI studies have shown that high $\alpha$ values may correlate with higher accretion rates (cite: Simon_2015). IM Lup has a measured disk accretion rate of 10$^{-8}$ M$_{\odot}$ yr$^{-1}$ (cite: alcala_2017_accretion), which is typical of lower $\alpha$. This is reminiscent of DM Tau, where the system showed measurable turbulence, but a low accretion rate (cite: Flaherty_2020_DMTau). It is important to note that the measured accretion rate is taken from the instantaneous accretion rate onto the star; however, the $\alpha$ values represent disk motions throughout the outer, and in the case of IM Lup the elevated, regions of the disk. Future work should look into this with dedicated models.

A vertical gradient in the turbulence, with high values approaching the sound speed above 2$H$, with $H$ being the disk hydrodynamical scale height, is a key prediction of MRIs (cite: Simon_2015; Flock_2015). The scale height in IM Lup is expected to be $H \sim 0.1$ (cite: MAPS_Zhang; Paneque_2023_vert); therefore, CN emission is originating above 2$H$. To fully confirm a vertical gradient in turbulence, studying molecules in the intermediate layers is necessary, such as HCO$^{+}$, H$_2$CO, and HCN, which have their vertical heights characterized and emit from in-between the midplane and $^{13}$CO (cite: Paneque_2023_vert). Unfortunately, the sensitivity and spectral resolution of the available data for these tracers (cite: MAPS_Oberg) is not sufficient to detect nonthermal broadening of $\leq$90m s$^{-1}$, such as detected for CN. Follow up observations at higher spectral resolution would allow us to replicate this analysis and confirm the existence of a vertical gradient.

As a first attempt to compare our results with other less abundant tracers, we repeated our analysis on C$^{18}$O $J=2-1$ data from the MAPS program (cite: MAPS_Oberg). Figure [3](#best_fit_heights) shows that C$^{18}$O $J=2-1$ comes from an elevated layer, comparable to that of CN, but slightly below. This emission is expected to come close to the CO freeze-out region and previous works have assumed an excitation temperature of 21 K for the C$^{18}$O gas (cite: Pinte_2018_method; Paneque-Carreno_2022_Elias_CN). Assuming that the nonthermal contribution is fully turbulent, the extracted turbulent dispersion profile of C$^{18}$O are slightly higher, but comparable within the uncertainty to the results obtained from CN assuming the temperature profile of $^{13}$CO. We note that while the brightness temperature of C$^{18}$O is below the assumed excitation temperature (see Figure [4](#brightness_temp)), the column density of CO in IM Lup (cite: MAPS_Zhang) and estimates from Elias 2-27 of C$^{18}$O under similar conditions (cite: Paneque-Carreno_2022_Elias_CN), show that this isotopolog may have optical depths of 1-2. In this case, opacity broadening could account for up to 25% of the measured linewidth value (cite: Hacar_2016_optdepth), biasing our result to higher turbulence profiles. Figure [10](#turb_C18O) shows the comparison between the CN results and the turbulent dispersion profiles of C$^{18}$O assuming a fully turbulent nonthermal contribution in the same way as our CN analysis (solid line) and considering an opacity broadening of 25% to the measured linewidth (dotted line). While the analysis of C$^{18}$O considering opacity broadening gives a turbulent dispersion profile below that of CN (using the $^{13}$CO temperature), all profiles are comparable within their uncertainty. This is likely due to the similarity in the emitting region, which overlap within the dispersion (cite: Paneque_2023_vert) and highlights the need for a follow up study using other optically thin tracers that clearly probe different innermost disk layers.

![](turb_analysis_C18O.pdf)

## Possible overestimation of the nonthermal component

We considered the possibility that we overestimated the turbulence in our analysis, for example by underestimating the temperatures in the CN emitting region or not taking into account alternative origins of the nonthermal broadening. Regarding the temperature profiles, we are confident that CO traces optically thick gas, even toward the outer disk regions. We confirmed this by comparing our temperature profiles to the gas temperature from dedicated thermochemical models of IM Lup (cite: Cleeves_LupusModel_2016), which coincide with the values used in this work; therefore, we have not underestimated the temperature. Determining other contributors to nonthermal broadening is harder: it could be that CN emission is not as optically thin as expected, that it is vertically extended and the velocity dispersion along the line of sight is considerable, or that some strong non-Keplerian motion is affecting the system. Below, we analyze each of these scenarios.

At optical depths of $\tau\sim$0.1 the opacity contribution to the linewidth is negligible, but at slightly higher values, even while $\tau<$1 as expected for CN in IM Lup (cite: MAPS_Bergner), opacity broadening could contribute up to $\sim$15% of the measured linewidth (cite: Hacar_2016_optdepth). For our measured linewidth of $\sim$221 m s$^{-1}$ outside of 150 au we considered a systematic error of 50 m s$^{-1}$ to account for Hanning smoothing effects, which corresponds to a 23% error in the linewidth measurement and also accounts for the possibility of having CN emission with an optical depth up to $\tau\sim$2. Our results would still be consistent with high turbulence, even if the emission were marginally optically thick and opacity was contributing to the nonthermal broadening.

CN emission is expected to arise from a geometrically thin layer (cite: Cazzoletti_2018_CN; Paneque-Carreno_2022_Elias_CN); however, at the peak of emission this layer may extend vertically up to $\sim$40 au (cite: Cazzoletti_2018_CN). It is not possible to estimate the vertical width of the CN emission with our current analysis, but we can test the impact on our measured linewidth caused by Keplerian shear along the line of sight for IM Lup. By considering the inclination of the system and taking the best-fit CN emission layer as the position of the lowest parcel of material, we measured the linewidth broadening caused by having different vertical widths. The detail of this analysis can be found in Appendix D. Figure [11](#width_textsingle) comprises the results, showing that at radial distances beyond 150 au the variation in the linewidth caused by vertical widths of up to 50 au is always $\leq$25 m s$^{-1}$. The width would have to be broader than $\sim$60 au to cause significant variations out to further radii, which is not expected for CN (cite: Cazzoletti_2018_CN). This indicates that even in the case of CN being vertically extended, our results beyond 150 au will not vary beyond our assumed uncertainty of 50 m s$^{-1}$ (Fig. [7](#turb_imlup)).

![](lw_width_text_single.pdf)

There are no immediate signs of non-Keplerian motion (cite: Pinte_2018_hd16planet; Teague_2018_hd16planet; Izquierdo_2021_hd16planet) beyond the strong residual at $\sim$220 au (Figure [6](#comp_discminer_obs)), which is in any case radially localized and would not change our main results across the complete radial extent. However, IM Lup has been found to be prone to strong photo-evaporative winds, even in the presence of a weak external radiation field. Theoretical work by (cite: Haworth_2017_imlupwind) shows that, if present, these winds would originate in the upper disk layers and possibly cause mass loss rates comparable to the disk accretion rate (cite: alcala_2017_accretion), due to the large vertical extent of the disk, which makes the surface material weakly gravitationally bound. Winds are expected to broaden the line (cite: Fuller_Myers_1992); however, as we do not detect any indication of them in the spectra or image plane, we did not include this uncertainty in our analysis.

## Comparison with other methods and results

We have presented a new methodology to directly extract turbulence, a fundamental disk property, from molecular line emission. By tracing the vertical location of an optically thin tracer and comparing it to that of optically thick CO lines we can immediately access the kinetic temperature of the region (cite: MAPS_Law_Surf; Law_2023_12CO_surf; Paneque-Carreno_2022_Elias_CN) and from the measured linewidth calculate the nonthermal contribution attributed to turbulent motions. This requires a precise parametric model of the spectra to extract the linewidth accounting for the upper and lower disk emission layers and the broadening caused by beam convolution, which is why we use DISCMINER (cite: izquierdo_2021_discminer1).

Previous works have mostly put upper limits on turbulence by modeling the emission using physical disk models (cite: Hughes_2009_turb; Guilloteau_2012_turb_dmtau; Flaherty_2015_hd16_weakturb; Flaherty_2017_DCOp; Flaherty_2020_DMTau). This approach is required when the observed tracer is optically thick, as the linewidth will be affected by an opacity broadening due to the column density of the molecule (cite: Hacar_2016_optdepth) and the comparison between model and data must be done taking into consideration radiative transfer calculations (cite: Flaherty_2015_hd16_weakturb). However, this has the additional difficulty of determining surface density and temperature structure parameters (cite: Hughes_2009_turb; Guilloteau_2012_turb_dmtau), which are hard to constrain (cite: Miotello_ppvii_2023). Models of CO emission must also account for freeze-out and desorption processes that may be relevant (cite: Oberg_2015_CO_desorp), adding further complexity in this kind of analysis to obtain turbulence (cite: Flaherty_2020_DMTau).

Analyzing CO isotopolog data in IM Lup using these complex models also results in high nonthermal motions associated with turbulence of $\mathcal{M}$ = 0.18-0.3 (Flaherty et al. in prep). Within our errors (see Figure 7) these values are consistent with our determination of $\mathcal{M}$ = 0.4-0.6; however, they are a factor of 2 lower. With only one system where it is possible compare both methods, we are not able to conclude if this is a systematic difference or how it would affect the determination of nonthermal motions in other disks. We note that previous best-fit disk radiative transfer models used for studying turbulence in HD 163296 show strong differences with the disk vertical structure that is more recently constrained by (cite: Paneque_2023_vert). (cite: Flaherty_2017_DCOp) predict that the expected location for CO ($J=2-1$) in HD 163296, based on their models used for setting upper limits on the turbulence, is $z/r < 0.1$ (cite: Flaherty_2017_DCOp). Direct observational measurements, however, trace the CO ($J=2-1$) emission surface in HD 163296 at $z/r\sim$0.3 (cite: MAPS_Law_Surf; Paneque_2023_vert), indicating that some of the underlying model assumptions may be incorrect and highlighting the need for high resolution data as well as the difficulty and possible errors of such methods.

Another approach of directly determining the thermal structure and turbulence is to obtain the temperature using multiple transitions, which is particularly useful for face-on disks where the vertical dimension is not accessible. This has been applied to the TW Hya disk to constrain an upper limit on turbulence of $\mathcal{M}\sim$0.1 (cite: Teague_2016_turb_TWHya; Teague_2018_turb_nonlte). This method is complementary to our approach, as it relies on direct observational constraints rather than physical models; however, it carries the uncertainty on the exact emission height of different transitions.

# Conclusions

We have presented new Band 7 observations at high spectral and spatial resolution of CN $N=3-2$ and C$_2$H $N=4-3$ in IM Lup. The emission from both tracers seems to be optically thin and comes from a vertically elevated layer colocated with $^{13}$CO $J=2-1$. This is the first time C$_2$H is seen to be vertically elevated as predicted by thermochemical models.

Through the use of a parametric model, we traced the emission morphology and constrained the linewidth of CN, which we then decomposed into its thermal and nonthermal components. Assuming that the nonthermal component corresponds to turbulent broadening, we conclude the following:

1.  IM Lup presents strong turbulence in the upper layers ($z/r \sim$0.25), as traced by CN emission. In this layer and beyond radial distances of 150 au, turbulent velocities are between $\mathcal{M}$ = 0.4 and 0.6 ($\alpha\sim$10$^{-1}$).

2.  Combined with constraints of low turbulence in the midplane (cite: Franceschi_2023_imlup_turbdust; Jiang_turb_dust), IM Lup shows evidence for a vertical gradient of turbulence, with higher values in the upper layers. This is a key prediction of MRI (cite: Simon_2015), which has been proposed to be ongoing in IM Lup due to its ionization structure (cite: Seifert_2021_MRI_imlup).

3.  The use of optically thin tracers, with emission constrained to a localized vertical region, together with the temperature profiles extracted from CO isotopologs can be leveraged to directly measure turbulence through simple parametric models of the line intensity, without the uncertainties imposed by the density and temperature structure of protoplanetary disks.

Further use of ALMA’s exquisite spectral and spatial resolution will allow us to expand this study to other sources and directly confirm if IM Lup is an exception, or if other disks have turbulent motions comparable to the sound speed in the upper layers.

# Acknowledgements

This paper makes use of ALMA data from project #2019.1.01357.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. Astrochemistry in Leiden is supported by the Netherlands Research School for Astronomy (NOVA), and by funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 101019751 MOLDISK). This project has received funding from the European Union’s Horizon 2020 research and innovation programme under the Marie Sklodowska-Curie grant agreement No 823823 (DUSTBUSTERS).

76 natexlab

(ref: Aikawa_2002) Aikawa, Y., van Zadelhoff, G. J., van Dishoeck, E. F., & Herbst, E. 2002, A&A, 386, 622

(ref: alcala_2017_accretion) Alcalá, J. M., Manara, C. F., Natta, A., et al. 2017, A&A, 600, A20

(ref: DSHARP_Andrews) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41

(ref: Avenhaus_2018) Avenhaus, H., Quanz, S. P., Garufi, A., et al. 2018, ApJ, 863, 44

(ref: Balbus_1991_MRI) Balbus, S. A. & Hawley, J. F. 1991, ApJ, 376, 214

(ref: Balbus_Hawley_1998) Balbus, S. A. & Hawley, J. F. 1998, Reviews of Modern Physics, 70, 1

(ref: Bergin_2016_c2h) Bergin, E. A., Du, F., Cleeves, L. I., et al. 2016, ApJ, 831, 101

(ref: MAPS_Bergner) Bergner, J. B., Öberg, K. I., Guzmán, V. V., et al. 2021, ApJS, 257, 11

(ref: maps_bosman) Bosman, A. D., Alarcón, F., Bergin, E. A., et al. 2021, ApJS, 257, 7

(ref: Bosman_2023_imlup) Bosman, A. D., Appelgren, J., Bergin, E. A., Lambrechts, M., & Johansen, A. 2023, ApJL, 944, L53

(ref: Cazzoletti_2018_CN) Cazzoletti, P., van Dishoeck, E. F., Visser, R., Facchini, S., & Bruderer, S. 2018, A&A, 609, A93

(ref: Cleeves_LupusModel_2016) Cleeves, L. I., Öberg, K. I., Wilner, D. J., et al. 2016, ApJ, 832, 110

(ref: Cleeves_2018) Cleeves, L. I., Öberg, K. I., Wilner, D. J., et al. 2018, ApJ, 865, 155

(ref: ALMA_tech_C10) Cortes, P., Vlahakis, C., Hales, A., et al. 2023, ALMA Cycle 10 Technical Handbook, Additional contributors to this edition: Yoshiharu Asaki, Tim Bastian, Brian Mason, Crystal Brogan, John Carpenter, Chinshin Chang, Geoff Crew, Ed Fomalont, Misato Fukagawa, Remy Indebetouw, Hugo Messias, Todd Hunter, Ruediger Kneissl, Andy Lipnicky, Sergio Martin, Lynn Matthews, Luke Maud, Anna Miotello, Yusuke Miyamoto, Tony Mroczkowski, Hiroshi Nagai, Kouichiro Nakanishi, Masumi Shimojo, Richard Simon, Carmen Toribio, Catarina Ubach, Catherine Vlahakis, Martin Zwaan

(ref: MAPS_Czekala) Czekala, I., Loomis, R. A., Teague, R., et al. 2021, ApJS, 257, 2

(ref: Dartois_2003) Dartois, E., Dutrey, A., & Guilloteau, S. 2003, A&A, 399, 773

(ref: Flaherty_2020_DMTau) Flaherty, K., Hughes, A. M., Simon, J. B., et al. 2020, ApJ, 895, 109

(ref: Flaherty_2017_DCOp) Flaherty, K. M., Hughes, A. M., Rose, S. C., et al. 2017, ApJ, 843, 150

(ref: Flaherty_2015_hd16_weakturb) Flaherty, K. M., Hughes, A. M., Rosenfeld, K. A., et al. 2015, ApJ, 813, 99

(ref: Flock_2015) Flock, M., Ruge, J. P., Dzyurkevich, N., et al. 2015, A&A, 574, A68

(ref: emcee_ref) Foreman-Mackey, D., Farr, W., Sinha, M., et al. 2019, The Journal of Open Source Software, 4, 1864

(ref: Forgan_2012) Forgan, D., Armitage, P. J., & Simon, J. B. 2012, MNRAS, 426, 2419

(ref: Franceschi_2023_imlup_turbdust) Franceschi, R., Birnstiel, T., Henning, T., & Sharma, A. 2023, A&A, 671, A125

(ref: Fuller_Myers_1992) Fuller, G. A. & Myers, P. C. 1992, ApJ, 384, 523

(ref: Gaia_DR3) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1

(ref: Guilloteau_Dutrey_1998) Guilloteau, S. & Dutrey, A. 1998, A&A, 339, 467

(ref: Guilloteau_2012_turb_dmtau) Guilloteau, S., Dutrey, A., Wakelam, V., et al. 2012, A&A, 548, A70

(ref: MAPS_Guzman) Guzmán, V. V., Bergner, J. B., Law, C. J., et al. 2021, ApJS, 257, 6

(ref: Hacar_2016_optdepth) Hacar, A., Alves, J., Burkert, A., & Goldsmith, P. 2016, A&A, 591, A104

(ref: Haworth_2017_imlupwind) Haworth, T. J., Facchini, S., Clarke, C. J., & Cleeves, L. I. 2017, MNRAS, 468, L108

(ref: DSHARP_Huang_radial) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018a, ApJL, 869, L42

(ref: DSHARP_Huang_Spirals) Huang, J., Andrews, S. M., Pérez, L. M., et al. 2018b, ApJL, 869, L43

(ref: Hughes_2009_turb) Hughes, A. M., Wilner, D. J., Cho, J., et al. 2009, ApJ, 704, 1204

(ref: Hunter_2023_ALMA_pipeline) Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023, Publications of the Astronomical Society of the Pacific, 135, 074501

(ref: Izquierdo_2021_hd16planet) Izquierdo, A. F., Facchini, S., Rosotti, G. P., van Dishoeck, E. F., & Testi, L. 2022, ApJ, 928, 2

(ref: izquierdo_2021_discminer1) Izquierdo, A. F., Testi, L., Facchini, S., Rosotti, G. P., & van Dishoeck, E. F. 2021, A&A, 650, A179

(ref: Izquierdo_2023_discminer2) Izquierdo, A. F., Testi, L., Facchini, S., et al. 2023, A&A, 674, A113

(ref: Jiang_turb_dust) Jiang, H., Macı́as, E., Guerra-Alvarado, O. M., & Carrasco-González, C. 2023, arXiv e-prints, arXiv:2311.07775

(ref: Klisch_1995_CN) Klisch, E., Klaus, T., Belov, S. P., Winnewisser, G., & Herbst, E. 1995, A&A, 304, L5

(ref: Kratter_Lodato_2016_GI) Kratter, K. & Lodato, G. 2016, ARA&A, 54, 271

(ref: MAPS_Law_radial) Law, C. J., Loomis, R. A., Teague, R., et al. 2021a, ApJS, 257, 3

(ref: MAPS_Law_Surf) Law, C. J., Teague, R., Loomis, R. A., et al. 2021b, ApJS, 257, 4

(ref: Law_2023_12CO_surf) Law, C. J., Teague, R., Öberg, K. I., et al. 2023, ApJ, 948, 60

(ref: Lesur_ppvii_2023) Lesur, G., Flock, M., Ercolano, B., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 465

(ref: Lodato_2023_mass_imlup) Lodato, G., Rampinelli, L., Viscardi, E., et al. 2023, MNRAS, 518, 4481

(ref: Lynden_Bell_Pringle_1974) Lynden-Bell, D. & Pringle, J. E. 1974, MNRAS, 168, 603

(ref: McMullin_CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Miotello_2019_c2h) Miotello, A., Facchini, S., van Dishoeck, E. F., et al. 2019, A&A, 631, A69

(ref: Miotello_ppvii_2023) Miotello, A., Kamp, I., Birnstiel, T., Cleeves, L. C., & Kataoka, A. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 501

(ref: Myers_Ladd_Fuller_1991) Myers, P. C., Ladd, E. F., & Fuller, G. A. 1991, ApJL, 372, L95

(ref: Nagy_2015_C2H) Nagy, Z., Ossenkopf, V., Van der Tak, F. F. S., et al. 2015, A&A, 578, A124

(ref: Oberg_2015_CO_desorp) Öberg, K. I., Furuya, K., Loomis, R., et al. 2015, ApJ, 810, 112

(ref: MAPS_Oberg) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1

(ref: Paneque-Carreno_2022_Elias_CN) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., et al. 2022, A&A, 666, A168

(ref: Paneque_2023_vert) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., et al. 2023, A&A, 669, A126

(ref: Pinte_2018_method) Pinte, C., Ménard, F., Duchêne, G., et al. 2018a, A&A, 609, A47

(ref: Pinte_2018_hd16planet) Pinte, C., Price, D. J., Ménard, F., et al. 2018b, ApJL, 860, L13

(ref: Rosotti_2023_turbulencerev) Rosotti, G. P. 2023, New A Rev., 96, 101674

(ref: Rosotti_2021_CITau) Rosotti, G. P., Ilee, J. D., Facchini, S., et al. 2021, MNRAS, 501, 3427

(ref: lambda_database_Schoier_2005) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369

(ref: Schreyer_2008) Schreyer, K., Guilloteau, S., Semenov, D., et al. 2008, A&A, 491, 821

(ref: Seifert_2021_MRI_imlup) Seifert, R. A., Cleeves, L. I., Adams, F. C., & Li, Z.-Y. 2021, ApJ, 912, 136

(ref: Shakura_Sunyaev_1973_visc) Shakura, N. I. & Sunyaev, R. A. 1973, A&A, 24, 337

(ref: shi_chiang_2014) Shi, J.-M. & Chiang, E. 2014, ApJ, 789, 34

(ref: sierra_2021_MAPS) Sierra, A., Pérez, L. M., Zhang, K., et al. 2021, ApJS, 257, 14

(ref: Simon_2015) Simon, J. B., Hughes, A. M., Flaherty, K. M., Bai, X.-N., & Armitage, P. J. 2015, ApJ, 808, 180

(ref: gofish) Teague, R. 2019, The Journal of Open Source Software, 4, 1632

(ref: MAPS_Teague) Teague, R., Bae, J., Aikawa, Y., et al. 2021, ApJS, 257, 18

(ref: Teague_2019_meridonial) Teague, R., Bae, J., & Bergin, E. A. 2019, Nature, 574, 378

(ref: Teague_2018_hd16planet) Teague, R., Bae, J., Bergin, E. A., Birnstiel, T., & Foreman-Mackey, D. 2018a, ApJL, 860, L12

(ref: Teague_2016_turb_TWHya) Teague, R., Guilloteau, S., Semenov, D., et al. 2016, A&A, 592, A49

(ref: Teague_2018_turb_nonlte) Teague, R., Henning, T., Guilloteau, S., et al. 2018b, ApJ, 864, 133

(ref: Teague_2020_CN) Teague, R. & Loomis, R. 2020, ApJ, 899, 157

(ref: Urpin_Brandenburg_1998_VSI) Urpin, V. & Brandenburg, A. 1998, MNRAS, 294, 399

(ref: Visser_2018) Visser, R., Bruderer, S., Cazzoletti, P., et al. 2018, A&A, 615, A75

(ref: MAPS_Zhang) Zhang, K., Booth, A. S., Law, C. J., et al. 2021, ApJS, 257, 5

# Radial features

The integrated intensity emission maps (moment 0) show a distinct radial feature for all the studied hyperfine groups (Fig. [1](#imlup_emission)). We compute the azimuthally averaged intensity profiles from these maps by accurately deprojecting using the best-fit vertical surfaces and the function radial_profile from GoFish (cite: gofish). Only emission from within a 60$^{\circ}$ wedge along the semimajor axis is considered, to avoid deprojection effects from emission close to the minor axis (cite: MAPS_Law_radial). Our results are shown in Figure [12](#radial_prof), where all tracers display a ringed structure peaking at $\sim$106 au.

![](radial_prof_gofish.pdf)

To characterize the width and any azimuthal variations of the ring feature, a set of two Gaussians are fitted to the radial profiles as done in (cite: MAPS_Law_radial). A broad component Gaussian is used to trace the emission at further out radii and a second Gaussian traces the ring structure. Figure [13](#fits_gauss_ring) shows the fitted Gaussians and FWHM value of the ring-component Gaussian. We used a Gaussian function such that

$$\begin{equation}
    I = I_0 \, \mathrm{exp}\left[ -\frac{1}{2} \frac{(R-R_0)^{2}}{\sigma^2} \right] 
,
\end{equation}$$where $I$ is the measured intensity, $R$ the radial distance, $I_0, R_0$ and $\sigma$ are the fitted parameters and the FWHM = 2$\sqrt{2\,\mathrm{log}(2)}\,\sigma$. While the peak of emission was coherent across different hyperfine groups, the ring width has slight variations. Overall the feature shows an average width of $\sim$89 au in CN and $\sim$109 au in C$_2$H.

Considering the broadest value of $\sim$115 au we calculate the averaged intensity throughout the angular extent of the ring, using azimuthal bins of 5$^{\circ}$. Figure [14](#ring_intensity) shows the results. CN displays a symmetric ring across azimuth, with slight variations along the semiminor axis likely due to projection effects. C$_2$H has a lower S/N and may show tentative asymmetries; however, the quality of the data is not sufficient to characterize them in detail.

![](fit_radial_profiles_gauss.pdf)

![](ring_intens_compass.pdf)

# Channel map analysis

To extract the vertical location of the emission layer, we traced the emission maxima from the channel map emission as explained in section 3.1. The channels, masks, and extracted emission maxima are presented in Figures [15](#channels_cn) and [16](#channels_c2h) for CN and C$_2$H, respectively.

![](channel_maps_cn.pdf)

![](channel_maps_c2h.pdf)

# DISCMINER best-fit parameters

Table [3](#table_params_dm) indicates the best-fit parameters obtained by DISCMINER for the CN emission model.

+----------------+--------------------+------------------+--------+
| Attribute      | Parameter          | Unit             | Value  |
+:===============+:==================:+:================:+:======:+
| Orientation    | $i$                | \[$^{\circ}$\]   | 50.53  |
|                +--------------------+------------------+--------+
|                | PA                 | \[$^{\circ}$\]   | 143.76 |
|                +--------------------+------------------+--------+
|                | $x_c$              | \[au\]           | -1.9   |
|                +--------------------+------------------+--------+
|                | $y_c$              | \[au\]           | 1.3    |
+----------------+--------------------+------------------+--------+
| Velocity       | $M_*$              | \[M$_{\odot}$\]  | 1.22   |
|                +--------------------+------------------+--------+
|                | $v_{\mathrm{sys}}$ | \[km s$^{-1}$\]  | 4.49   |
+----------------+--------------------+------------------+--------+
| Upper surface  | $z_0$              | \[au\]           | 18.98  |
|                +--------------------+------------------+--------+
|                | $p$                | \[-\]            | 1.50   |
|                +--------------------+------------------+--------+
|                | $R_t$              | \[au\]           | 427.50 |
|                +--------------------+------------------+--------+
|                | $q$                | \[-\]            | 3.34   |
+----------------+--------------------+------------------+--------+
| Lower surface  | $z_0$              | \[au\]           | 8.35   |
|                +--------------------+------------------+--------+
|                | $p$                | \[-\]            | 1.47   |
|                +--------------------+------------------+--------+
|                | $R_t$              | \[au\]           | 423.38 |
|                +--------------------+------------------+--------+
|                | $q$                | \[-\]            | 3.91   |
+----------------+--------------------+------------------+--------+
| Peak intensity | $I_0$              | \[Jy px$^{-1}$\] | 0.69   |
|                +--------------------+------------------+--------+
|                | $p$                | \[-\]            | -4.30  |
|                +--------------------+------------------+--------+
|                | $q$                | \[-\]            | 3.60   |
|                +--------------------+------------------+--------+
|                | $I_g$              | \[Jy px$^{-1}$\] | 2.42   |
|                +--------------------+------------------+--------+
|                | $R_g$              | \[au\]           | 32.74  |
|                +--------------------+------------------+--------+
|                | $\sigma_{g}$       | \[au\]           | 45.97  |
+----------------+--------------------+------------------+--------+
| Linewidth      | $L_0$              | \[km s$^{-1}$\]  | 0.415  |
|                +--------------------+------------------+--------+
|                | $p$                | \[-\]            | -0.205 |
|                +--------------------+------------------+--------+
|                | $q$                | \[-\]            | -0.238 |
+----------------+--------------------+------------------+--------+

: DISCMINER best-fit parameter values.

# Effect of vertical layer width

To estimate the effect of the Keplerian shear due to a nonzero vertical width of the CN emitting layer, we considered the best-fit CN emitting surface as a lower limit and used the geometry of the disk to calculate the line-of-sight path for different vertical widths (see panel A in Figure [17](#sketch_width)). The rotation velocity of a parcel of gas located at a position ($r, z$), in cylindrical coordinates, from the star is given by

$$\begin{equation}
    V^{2}_{rot} = \frac{GM_{*}r^{2}}{(r^2 + z^2)^{3/2}},
\end{equation}$$

where $G$ is the gravitational constant and $M_{*}$ the stellar mass. Using this formula, we calculated the velocity for a parcel of material along the line-of-sight path, between the initial ($r_1, z_1$) and final ($r_2, z_2$) positions, as shown in Figure [17](#sketch_width). The velocity variation is not linear, as it depends on both radial and vertical differences; to be sensitive to these variations, we sampled the line-of-sight path every 1 au. Using a series of Gaussian profiles with line centers at each of the sampled velocities, we computed the resulting average profile, which is of Gaussian form, and estimated the measured linewidth from it (panel B in Figure [17](#sketch_width)). As the temperature is not expected to change significantly in these upper disk layers for IM Lup (cite: Cleeves_LupusModel_2016), we assumed a constant intrinsic thermal linewidth in the Gaussian profiles for our estimation. The final linewidth broadening caused by a nonzero emission surface is then calculated by subtracting the intrinsic and measured linewidth values.

![](sketch_width_referee.png)

[^1]: https://github.com/richteague/keplerian_mask

</paper>

Write the methods card for this paper.