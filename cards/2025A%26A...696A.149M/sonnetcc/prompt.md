# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...696A.149M\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2025A&A...696A.149M",
 "title": "ALMAGAL: I. The ALMA evolutionary study of high-mass protocluster formation in the Galaxy: Presentation of the survey and early results",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Molinari, S.",
 "n_authors": 76,
 "arxiv_id": "2503.05555",
 "doi": "10.1051/0004-6361/202452702",
 "alma_projects_linked_by_archive": [
  "2019.1.00195.L"
 ]
}
```

Paper text:
<paper>
# ALMAGAL I. The ALMA evolutionary study of high-mass protocluster formation in the Galaxy

A large fraction of stars form in clusters containing high-mass stars, which subsequently influences the local and galaxy-wide environment. Fundamental questions about the physics responsible for fragmenting molecular parsec-scale clumps into cores of a few thousand astronomical units (au) are still open, that only a statistically significant investigation with ALMA is able to address; for instance: the identification of the dominant agents that determine the core demographics, mass, and spatial distribution as a function of the physical properties of the hosting clumps, their evolutionary stage and the different Galactic environments in which they reside. The extent to which fragmentation is driven by clumps dynamics or mass transport in filaments also remains elusive. With the ALMAGAL project, we observed the 1.38 mm continuum and lines toward more than 1000 dense clumps in our Galaxy, with $M\,\geq$ 500 M$_{\odot}$, $\Sigma\geq 0.1$ g cm$^{-2}$ and $d$ $\leq$ 7.5 kiloparsec (kpc). Two different combinations of ALMA Compact Array (ACA) and 12-m array setups were used to deliver a minimum resolution of $\sim$1000 au over the entire sample distance range. The sample covers all evolutionary stages from infrared dark clouds (IRDCs) to Hii regions from the tip of the Galactic bar to the outskirts of the Galaxy. With a continuum sensitivity of 0.1 mJy, ALMAGAL enables a complete study of the clump-to-core fragmentation process down to $M\sim 0.3\,$M$_{\odot}$ across the Galaxy. The spectral setup includes several molecular lines to trace the multiscale physics and dynamics of gas, notably CH$_3$CN, H$_2$CO, SiO, CH$_3$OH, DCN, HC$_3$N, and SO, among others. We present an initial overview of the observations and the early science product and results produced in the ALMAGAL Consortium , with a first characterization of the morphological properties of the continuum emission detected above 5$\sigma$ in our fields. We used "perimeter-versus-area" and convex hull-versus-area metrics to classify the different morphologies. We find that more extended and morphologically complex (significantly departing from circular or generally convex) shapes are found toward clumps that are relatively more evolved and have higher surface densities. ALMAGAL is poised to serve as a game-changer for a number of specific issues in star formation: clump-to-core fragmentation processes, demographics of cores, core and clump gas chemistry and dynamics, infall and outflow dynamics, and disk detections. Many of these issues will be covered in the first generation of papers that closely follow on the present publication.

# Introduction

Most stars form in clusters (cite: Lada+Lada03; PSZ2010; Adams2010; Adamo2020) and about 50% of them, including the Sun itself (and the fraction probably was even higher in the early Universe), form in very rich clusters of at least 1000 stars, containing at least one 10 M$_{\odot}$ star. High-mass stars (M$\geq$8M$_{\odot}$) influence their immediate environment through gravitational (ejection of stars from the cluster, disk truncation, etc.), mechanical (winds, outflows), radiative interaction (e.g., radiative heating, photo-ionization, and radiation pressure), and, eventually, through their supernovae explosions. Hence, the formation process of low-mass stars and their associated planets in such clusters will

vastly differ from star formation in isolation or small clusters. However, the latter scope is where most low-mass star formation studies have taken place so far, mostly because such objects are close by and easier to study. However, they are not representative of the most significant fraction of star formation.

High-mass stars dominate the energy input into the ISM through feedback processes, not only locally, but also on galactic scales (cite: veilleux2005; Bolatto+2013). They also enrich the ISM with heavy elements, which, in turn, influences subsequent events of star formation (cite: klessen2016). Yet, their formation processes differ

significantly from low-mass stars: while the Kelvin-Helmholtz timescale of low-mass stars is significantly longer than the time required to assemble them, for any reasonable accretion rate, it is shorter for high-mass stars. Hence, high-mass stars will continue accreting up to and even after reaching the main sequence (cite: Maeder2000; KW2006; Zinnecker2007). The combination of being deeply embedded in dusty cores through most of their evolution, their scarcity and correspondingly high average distance, together with evolution in clusters with many sources close together, make these observations challenging.

Cluster formation involves cores (linear scales $\leq$0.1 pc) forming inside molecular clumps (linear scales of 0.5-1.0 pc), as indeed observed at high spatial resolution at mm wavelengths (cite: Zhang+2015; Beuther+2018; Svoboda+19; Sanhueza+19; Traficante+2023; Avison+2023). A full understanding of the fragmentation process and its role in allowing high-mass stars to collect material up to their final mass is still elusive. Furthermore, thermal (cite: Jeans1902) mass fragmentation leads to low-mass objects (cite: Rees1976; Larson1985) that are less massive than the observed masses of high-mass stars (M$\geq$8M$_{\odot}$). Mechanisms to stop fragmentation and delay collapse, allowing the collection of enough gas in existing fragments to form massive stars, are a possible solution. Turbulent support (e.g., (cite: mck03)) or magnetic and radiation feedback (e.g., (cite: Krumholz+2009c; Comm+2011)) have recently been invoked. In this model family (hereafter monolithic collapse), the final stellar mass of the emerging stars is pre-assembled in the cores, and we would expect to find high-mass monolithic prestellar cores. Yet, the search for high-mass protostellar clumps without any sign of star formation has only resulted in very few candidates (e.g., (cite: Tackenberg+2012; Beuther+2015; Nony+18; Motte+2018)); so, this is unlikely to be a dominant path to high-mass star formation.

In the more dynamical scenario of competitive accretion, cores compete (cite: Bonnell+2007) for gas from the cloud mass reservoir that is not initially local to the core itself (cite: Klessen2000; BonnellBate2006; Peters2011; Girichidis2012), whereas high-mass monolithic prestellar cores should not feasibly exist (cite: Smith+2009). Infall motions would be dominated by accretion from the cloud onto the core. Indeed, observations reveal large-scale infall motions in massive star-forming regions, showing that high-mass clumps are not isolated from the cloud mass reservoir and they are shown, instead, to globally accrete while star formation is internally ongoing (e.g., (cite: Wu+2003; Rygl+2013; Klaassen+2012; He+2015; Traficante+2017; Contreras+2018; Traficante+2020)) also via continuous mass flow along filaments to stars forming at filamentary hubs (cite: Peretto+2013; Chen+2019; Wells+2024). Theoretical studies have shown that infall motions are crucial both for initiating the formation of high-mass stars and in subsequent evolutionary stages for maintaining accretion flows to increase the stellar mass (e.g., (cite: Jijina+1996; yor02; Gong+2009; Peters2010; Vazquez2019)).

To make fundamental progress in our understanding of the formation of high-mass stars and their surrounding clusters, we want to investigate two key issues in a statistically significant way: 1) what physical processes govern the fragmentation of cluster-forming clumps and how they evolve with time; and 2) how cores gain mass and how this process is influenced by internal feedback from the cores into the clump gas.

So far, $\sim$300 dense and massive clumps have been observed at interferometric spatial resolution in total over fewer than a dozen different observing programs. In particular, early-stage, 70 $\mu$m-dark, or IRDC-like targets have received considerable attention. (cite: Svoboda+19) targeted 12 such massive clumps at a resolution of $\sim$3000 au, revealing fragmentation with separations comparable to the thermal Jeans length, as previously proposed by (cite: Palau+2015). Likewise, ASHES (cite: Sanhueza+19) observed a sample of similar size at slightly lower resolutions ($\sim$4500 au), confirming fragmentation in these early stages of evolution, Jeans-compatible fragmentation lengths, and also suggesting sub-clustering in the distribution of the fragments. (cite: MAnderson+21) observed with ALMA six hub-filament systems in IRDCs at resolutions $\sim$6000 au; combining them with data from 29 clumps previously observed by (cite: Csengeri+2017) offered evidence of clump-fed accretion. A similarly sized sample of IRDCs was recently studied by (cite: Rigby+2024), displaying gas kinematics that is also consistent with the latter scenario.

At the other end of the evolutionary path, (cite: Beuther+2018) observed 20 relatively more evolved massive clumps with luminosities in excess of $10^4$ L$_{\odot}$using NOEMA with high resolutions ($\sim$1000 au), revealing various levels of fragmentation, again compatible with thermal Jeans length and typical fragment separations showing no dependence on core masses. More recently, ATOMS (cite: Liu+2020) targeted 146 evolved UC/HC-HII regions, while ASSEMBLE (cite: Xu+2024) observed 11 evolved massive clumps at $\sim$2000 au resolution. Similarly, (cite: Ishihara+2024) observed 30 hot cores at $\sim$1000 au resolution confirming that thermal Jeans fragmentation may be at work. Other surveys have a wider coverage in the evolutionary stage of targeted clumps, with TEMPO (cite: Avison+2023) reporting (with resolutions $\sim$3000–4000 au) Jeans-compatible fragmentation distance only in a fraction of the clumps; or, as in SQUALO (cite: Traficante+2023), suggesting that the mass and minimum distance between fragments, respectively, increase or decrease with evolution.

The significance and robustness of these results are hampered by the relatively low number of targets in each study, as well as the different selection criteria that prevent trustworthy conclusions from studies of composite samples that, in principle, could be assembled. In addition, the different frequency setups and different linear resolutions used make a quantitative comparison difficult. Large ALMA projects like ALMA-IMF (cite: Motte+2022) partially overcome these limitations by imaging 15 well-known large star formation complexes (e.g., the W43 Galactic starburst), harbouring regions of very different mass and evolution with extensive spectroscopic coverage, to address the issue of the emergence of the IMF.

Answering the fundamental questions outlined above requires a number of crucial observables to be measured in a statistically significant way and compared to predictions from numerical simulations over a wide variety of evolutionary stages and Galactic environments: i) the spatial distribution of dense cores as a function of mass within dense clumps; ii) their fragmentation properties, such as average distances and their relation to Jeans masses or filament fragmentation scales; iii) their evolution both in morphology and in total number; iv) the temperature and density distribution of gas in the clumps; v) the velocity field of the clumps gas and the presence of global infall motions; and vi) the dynamical state of the compact fragments.

The ALMAGAL Large Program was specifically designed to deliver this key science by mapping more than 1000 intermediate and high-mass dense clumps with ALMA in band 6 (Sect. [3](#sample)) at a spatial resolution of 1000 au. Figure [1](#sample_comparison) shows that ALMAGAL is a game-changer with respect to coupling the ability to map the variance of physical, evolutionary, and environmental conditions of the targets (Fig. [2](#sample_fig)) with an unprecedented resolution and statistical significance.

The paper is structured as follows. In Sect. [2](#obs_setup), we summarize the characteristics of the ALMAGAL observations, deferring a much more thorough discussion to the companion paper by (cite: SanchezMonge+2025). In Sect. [3](#sample), we discuss in detail the properties of the observed clumps and the process of revision of source distances following the ALMAGAL observations and the homogeneization of the way in which physical parameters (e.g., masses and luminosities) are derived. In Sect. [4](#continuum), we present a characterization of the continuum emission detected with ALMA in the context of clump-integrated properties (Sect. [4.1](#alma_higal)) and in terms of the morphology of the emission (Sect. [4.2](#cont_morph)). In Sect. [5](#outlook), we outline the potential of the ALMAGAL science in a number of areas, anticipating the dedicated papers that are anticipated in the near future. Finally, in Sect. [6](#concl), we summarize our conclusions.

![image](ALMAGAL_Nclumps-L_M.jpg) ![image](ALMAGAL_Nclumps-Ncores.jpg) ![image](ALMAGAL_Nclumps-Spatial_res.jpg)

# Observational setup

The ALMA Band 6 217 to 220 GHz frequency range is ideally suited to provide access to the J=2-1 lines of $^{13}$CO and C$^{18}$O (for column density and velocity structure), SiO (5 – 4) (to trace outflows), three H$_2$CO lines (temperature and density, infall and outflow tracers), CH$_3$OH (temperature estimates), the K-ladder of the CH$_3$CN (12–11) and CH$_3^{13}$CN (12–11) lines (temperature, velocity structure), and several other species (DCN (3 – 2), OCS (19 – 18), HC$_3$N(24 – 23)  etc.). The correlator was configured to produce two 1.875-GHz wide windows, providing $\sim1.4$ km s$^{-1}$ resolution, plus two higher resolution windows with a $\sim0.34$ km s$^{-1}$ resolution. To be able to address our science goals, it is imperative to recover signal from the minimum target 1000 au scale up to the clump-size scale. To achieve this goal in an optimal way, given the large distance range of our sources, all the targets have been observed in single-pointing, with the ACA plus two configurations of the 12-m array with two different antenna configuration combinations, depending on the source distances; the C-5/C-2/ACA setup was chosen for sources with d\<4.7 kpc (hereafter the "near" subsample, amounting to 538 objects), while the C-6/C-3/ACA setup was adopted for sources with d\>4.7 kpc (the "far" subsample, with 479 objects). In band 6, these combinations provide maximum angular resolutions of 0.13$''$ (C-6 for the "far" subsample) and 0.24$''$ (C-5 for the "near" subsample), along with a largest recoverable scale of about 30$''$. More details about the observations setup are given in the companion paper (cite: SanchezMonge+2025).

We will refer to as "*7m*" the data taken with the ACA, "TM2" the data taken in short baseline (hence lower resolution) configurations of the 12-m array (C-2 for the "near" sample, and C-3 for the "far" sample), and "TM1" the data taken in long baseline (hence higher resolution) configurations (C-5 for the "near" sample, and C-6 for the "far" sample). A fundamental step in data processing was the production of continuum images and spectral cubes by jointly deconvolving the combined data taken with ACA *7m* array and the different 12-m array configurations. In a first set of products, we combined ACA and the TM2 into what is called here and in all ALMAGAL papers the *7m+tm2* products. In a subsequent step, the TM1 data were also combined to obtain the full resolution *7m+tm2+tm1* products.

We required a 0.1 mJy continuum sensitivity for all targets irrespective of clump properties, which should (in principle) allow for detections at the 3$\sigma$ level of compact cores with a mass of $\geq$0.3M$_{\odot}$ (assuming dust temperature of 20K and opacity from (cite: OH1994) with index $\beta=1.75$) at a distance of 7.5kpc; this is sufficient to reliably sample the peak of the core mass function in a star-forming region such as Aquila (cite: Konyves+2010), but at up to 7.5 kpc from the Sun. This estimate is based on pure sensitivity requirements, while the effective detection of compact objects in interferometric maps critically depends on local background conditions and residuals from the CLEANing procedures. More details are given in (cite: SanchezMonge+2025; Coletta+2025). The ALMAGAL Large Program (2019.1.00195.L) was approved in ALMA Cycle 7, for a total granted observing time of 117.7 hours for all the 12-m array configurations, and 88.4 hours for the ACA observations (cite: SanchezMonge+2025).

# The ALMAGAL sample and observations

## Initial selection and survey planning

The ALMAGAL sample initially consisted of 1017 targets with declination $\delta \leq 0\degree$, distributed from the near tip of the Galactic bar to the third quadrant, spanning a large range of clump masses, evolutionary stages and Galactocentric distances.

![](almagal_updated_galpos_Final.pdf)

![](LM_4paper0a_v2.pdf)

The larger fraction of the sample (915 objects) was selected from the complete catalog of dense clumps from (cite: Elia+2017) based on the Hi-GAL 70-500$\mu$m photometry (cite: Molinari+2016a) complemented with ancillary data at $\lambda\leq$24 $\mu$m and $\lambda$\> 500$\mu$m  and with a distance determined after cross-comparison with an extensive suite of CO surveys of the Galactic plane, extinction maps, and Hi line profile analysis, following (cite: Mege+2021). The following selection criteria were adopted: i) distance \< 7.5 kpc from the Sun to be able to resolve the target 1000 au spatial scale with the selected configurations setup (Sect. [2](#obs_setup)); ii) clump masses \> 500 M$_{\odot}$ in the inner and 250 M$_{\odot}$ in the outer Galaxy; and iii) surface densities $\Sigma\geq$ 0.1 g cm$^{-2}$ threshold that is critical for high-mass star formation (cite: Kauffmann+Pillai2010; Krumholz+2014; Tan+2014; Traficante+2020). These selection criteria, adopted at the time of the proposal, are no longer 100% fulfilled, following a revision of target physical parameters using the ALMAGAL data itself (see Sect. below). Overall, more than 90% of targets fulfill the initial selection requirements. Target sources are spread over 3-14 kpc in Galactocentric distance from the near tip of the Galactic bar to the outskirts of the Milky Way (Fig. [2](#sample_fig)a). They span the full evolutionary path from the IRDC to the Hii region stage (Fig. [2](#sample_fig)b). They reside in very different environments, such as arm and inter-arm regions, and proximity to triggering agents, such as OB associations and expanding Hii region bubbles.

Sources in the inner 20 around the Galactic Center were excluded because this range subtends the central regions of the Galaxy. These regions are heavily affected by non-circular motions that make distance estimates unreliable (cite: Hunter2024). In addition, our main goal is to characterize the variance of the environmental conditions in the Galactic disc. In this sense, the central regions show peculiar conditions not representative of the disc and they are typically studied with dedicated programs such as ACES (cite: Nonhebel+2024).

We visually inspected the PACS 70-160 $\mu$m and the SPIRE 250-350-500 $\mu$m *Herschel* maps of all candidate targets to confirm the presence of compact emission at the position of the catalog source. The position of the 250 $\mu$m peak was adopted for the ALMA observations. From the evolutionary viewpoint, both the $L/M$ and the shape of the SED for $\lambda\leq$70 $\mu$m have been used as a broad evolutionary classification of the clumps (cite: Molinari+2008; Duarte-Cabral13; Molinari+2016c; Molinari+2019; Traficante+2018; Merello19; Wells+2022). The values of clump $L/M$ go from $\sim$0.05, which is typical of early-stage IRDC-like clumps, to $\sim$450, which is common to IR-bright clumps hosting actively forming protostellar objects often associated with HII regions (e.g., (cite: Cesaroni+2015; Elia+2021)).

To extend the coverage of the sample toward relatively more evolved Hii regions, we also included 98 objects drawn from the Red Midcourse Space Experiment Source (RMS) catalog of star-forming regions (cite: Lumsden+2013), using the same distance cut and with luminosity in excess of 3000 L$_{\odot}$. The RMS initial selection being based on the the mid-IR 8-21 $\mu$m wavelength range allows it to be more representative of relatively late stages; the sources selected do indeed display 1$\leq$L/M$\leq$ 200. The distribution of the final ALMAGAL sources sample in the Galaxy and in the L versus M evolutionary plot is presented in Fig. [2](#sample_fig), where the asterisk-symbols mark the location of the target clumps with Hii counterparts (cite: Purcell2013; Irabor+2023) in the CORNISH and CORNISH-S 5 GHz radio continuum surveys and occupy mostly the region above ${L/M}=10$. This confirms that the ALMAGAL sample spans the entire path from IRDC-hosted clump to the Hii region phase.

During the analysis stage, after the observations were taken, it was realized that the template WR stellar system $\eta$ Car, which has the target ID ’653755’ in the name of the data files in the ALMA Archive was included by error in the sample. We also overlooked that three fields (with target IDs ’615590’, ’G348.7342-01.0359B’, and ’G323.7410-00.2552C’ for reference in the ALMA Archive) had coordinates closer than 10$^{\prime \prime}$ to other targets in the sample and they are therefore considered to be duplications. Since they have larger noise levels compared to the fields they duplicate, we removed them from the ALMAGAL sample data considered in the rest of the paper and, thus, from further scientific analysis (amounting to 1013 targets). Figure [2](#sample_fig) reports the Galactocentric distribution and the L-M plot for the sample targets, with distances and physical parameters updated based on the new ALMAGAL observations, as explained in the next subsection below.

## Revision of ALMAGAL targets physical properties

A critical aspect in ALMAGAL science is relating the physical properties of ALMA detected cores, as well as the properties of the dense gas at all sampled spatial scales, to the physical properties of the parent dense clumps ((cite: Coletta+2025; Mininni+2025), Elia et al., in prep, Jones et al., in prep.). To this end, we decided to revise and update the target clump distances (also based on ALMAGAL itself) and physical properties, for three reasons:

- The methods by which the distance to the targets is estimated may have changed due to new evidence. For the fraction of the sample selected from the Hi-GAL survey, a new source catalog with new distance estimates and revised physical properties was released (cite: Elia+2021). For the RMS-based selected targets, their properties are constantly updated on the project’s website.[^1]

- The $v_{\rm LSR}$ of the bulk gas traced by high-critical density lines in the ALMAGAL spectral cubes provide a much more reliable input for kinematic distance estimates, especially in cases where CO (even with its rarer isotopologs) shows multiple gas components along the line of sight (Sect. [3.2.1](#dist_update)).

- A meaningful and reliable science analysis of the ALMAGAL data requires that clumps physical properties (in particular mass and luminosity) are estimated in a homogeneous way for the Hi-GAL and the RMS-based fractions of the sample (Sect. [3.2.2](#sample_homo)).

We report these updates in the following subsections.

### Revision of targets distance

Assigning a heliocentric distance to a source detected in 2D thermal continuum images is a mandatory critical step for any subsequent physical parameter estimate. The typical backbone workflow of any distance determination recipe can be summarized as follows (cite: Urquhart+2018; Mege+2021) in order of precision and priority: i) check source position against literature catalogs of maser or stellar parallax that offer the most reliable of all estimates; ii) correlate source position and velocity against literature catalogs of optical, radio, or absorption line Hii regions, or in YSOs where the distance has already been determined via, for instance, optical spectroscopy; iii) correlate source position with submm/radio molecular line surveys, use a Galactic rotation curve to derive the distance and (in cases where this places the source in the inner Galaxy) to try to solve the kinematic distance ambiguity (KDA) using additional evidence such as an association with IRDCs, Hi absorption features, and so on. A similar methodology was used to derive distances for the Hi-GAL and RMS catalogs, with only small differences.

To obtain a homogenized set of properties for the sample of target clumps and to take advantage of the ALMAGAL spectroscopy that offers the ideal database to improve existing kinematic distance estimate, in particular, for those objects (the majority), where only CO and its isotopologues were previously used in the literature, we revised the distances by measuring the $v_{\rm LSR}$  from several high critical density transitions and applied the final module of the (cite: Mege+2021) algorithm (previously used for deriving distances for the Hi-GAL catalog) that converts $v_{\rm LSR}$  into kinematic distance. The details of this work will be reported in Benedettini et al. (in prep.). In summary, for each ALMAGAL source, we extracted subcubes from the ALMAGAL *7m* datacubes over large velocity ranges ($\pm$180km s$^{-1}$) centered on CH$_3$OH, H$_2$CO, DCN (3 – 2), SO (6$_5$ – 5$_4$), HC$_3$N(24 – 23), SiO (5 – 4), C$^{18}$O (2–1), and $^{13}$CO (2–1) lines. For each line, the cubes were co-added over the emitting region, defined by selecting the spatial pixels where the moment zero map is above three times its noise level, to obtain integrated spectra that were fed to an automatic 3$\sigma$-clipping line detection and Gaussian fitting algorithm. The $v_{\rm LSR}$ of the targets were then derived averaging the fitted line centers of all the detected lines with a good fit among the transitions with critical density higher than 10$^5$ cm$^{-3}$; namely, CH$_3$OH, H$_2$CO, DCN (3 – 2), SO (6$_5$ – 5$_4$), HC$_3$N(24 – 23) and SiO (5 – 4). C$^{18}$O (2–1), and $^{13}$CO (2–1) were used only for 207 targets where none of the other higher critical density lines were detected. We assigned an uncertainty to the derived $v_{\rm LSR}$ of 1.4 km s$^{-1}$, which is the spectral resolution of the data. The formal uncertainty obtained from averaging the $v_{\rm LSR}$ of the individual lines used is much lower than this. However, since the resolution element is sampled with only 2 channels and the linewidths are generally below $\sim$2km s$^{-1}$, we decided to adopt the resolution as a conservative uncertainty. It is worth noting that in 257 ALMAGAL targets we found that more than one emission feature is present in the spectrum centered toward the C$^{18}$O (2–1) frequency, indicating that multiple components of gas are present in the same ALMA field of view (FOV). In these cases we selected the densest component choosing the velocity where line emissions were detected also in the transitions with higher critical densities (\> 10$^5$ cm$^{-3}$). We also have 12 targets with two components both revealed also in the high density tracers for which the most intense component was adopted. Figure [3](#distance_fig)a shows the extent of the variations found in the $v_{\rm LSR}$  derived from ALMAGAL data with respect the ones used at the time of the proposal and that were used to define the two subsamples observed with different 12m-array configurations (see Sect. [2](#obs_setup)). In 77 sources, the new $v_{\rm LSR}$ values differ from the original ones by more than 7 km s$^{-1}$ in absolute value. This is a threshold that we consider here, along with common literature (e.g., (cite: Mege+2021) and references therein), a reliable upper limit for local gas motions above which $v_{\rm LSR}$ variations are likely to reflect different kinematic distances. We therefore chose to adopt this limit as an uncertainty in the determination of the $v_{\rm LSR}$ of a target. Propagating this uncertainty on distance greatly depends on the Galactic longitude of the source, as we discuss below. The differences (sometimes very large) that we found in $v_{\rm LSR}$ with respect to the initial values at target selection are due to an incorrect choice of the CO component that was associated with the sources in the Hi-GAL/RMS samples, among the multiple components found along the sources’ line of sight. This resulted in a substantial revision of distances and physical properties for these 77 sources (see below).

![image](VLSR_ALMAGAL-vs-VLSR_Final.pdf) ![image](Dist_ALMAGAL-vs-Dist_Orig_Final.pdf)

The newly determined ALMAGAL-based $v_{\rm LSR}$ values were converted to distances using the final module of the (cite: Mege+2021) algorithm, with one important exception. In cases where there was no way to help resolve the KDA for Hi-GAL sources in the inner Solar circle, (cite: Mege+2021) adopted (by default) the far distance, while in similar conditions, RMS sources (Urquhart et al. 2018) were put at the near distance. To provide as a homogeneous as possible table of source properties, we chose for this study to adopt the same approach of the RMS catalog and place the Hi-GAL sources for which KDA could not be resolved (7 out of the 915 Hi-GAL sources in the ALMAGAL sample) at the *near* distance. In estimating the error associated with the distance we considered possible deviations from purely circular motions and proper motions as anticipated above, by applying an additional offset to the velocity of 7 km s$^{-1}$ as in (cite: Mege+2021); the corresponding offset recovered in the distance to each source will of course be dependent on the Galactic longitude of the object, and is adopted as the distance uncertainty as reported in Table 1, available at the CDS. Error propagation transfers twice the distance relative uncertainty to source luminosity and masses. No uncertainty originating from distance affects distance-independent quantities such as $L/M$ or clump surface densities.

In Fig. [3](#distance_fig)b, we compare the newly obtained distances with the original ones at the time of the proposal. We find that for 95 objects out of the total 1013 sources sample, the new distance differs by more than 0.5 kpc from the original one. For 24 objects the change in distance is such that the source would switch from the "near" to the "far" ALMAGAL subsample. Having been observed with the "near" C-5/C-2 ALMA antenna configuration, the target 1000 au linear scale was not reached for these objects. Conversely, for 39 objects, the change in distance is such that the source would switch from the "far" to the "near" ALMAGAL subsample; having been observed with the "far" C-6/C-3 ALMA antenna configuration, the linear scale achieved for these objects was smaller than the target 1000 au. Finally, for 44 objects, the new distance would put them beyond the 7.5 kpc distance limit adopted for the initial source selection; for these sources as well, the target resolved 1000 au linear scale was not reached.

### A homogeneous methodology for SED fitting.

Of the ALMAGAL targets extracted from the RMS sample, 59 were also present in the Hi-GAL clumps catalogs of (cite: Elia+2017; Elia+2021), where the requirement for inclusion was that a source should have a convex SED with at least 4 adjacent *Herschel* bands. For these sources (the "G" sources in col. 3 of Table 1 with "no sed" flag in the last column) the set of physical parameters reported in Table 1 were adopted from the Hi-GAL catalogs. For the rest of the RMS sources in the sample the above criteria were failed and hence they required a custom analysis of their SED to estimate parameters with the same approach as in Hi-GAL (described in detail in the above cited Elia’s papers). The different situations encountered can be grouped as follows, identified by a flag that is also reported in Table 1:

- **-sed_irr**: the RMS source had an entry with at least four adjacent bands in the Hi-GAL band-merged photometric catalog, but the *Herschel* SED was "irregular" in the sense that it showed changes in concavity directions. For the present work, the processing to derive the mass, L$_{\mathrm{bol}}$, T$_{dust}$, and T$_{bol}$, was also applied to these sources.

- **-sed_rebuilt**: the RMS source had multiple "$<$4-bands" entries in the Hi-GAL band-merged photometric catalog. A typical occurrence would be a RMS source with two counterparts at 250$\mu$m, where one of them would be linked to a $70-160$$\mu$m SED branch, and the other to another 350-500$\mu$m SED branch. Both branches would feature less than four adjacent bands and would not pass the criteria to be included in the Hi-GAL physical parameters catalog. For these cases, in the present work the partial branches were reconnected (e.g., in the example above, forcing a single 250$\mu$m source to be extracted).

- **-sed_sat**: the RMS source is associated with saturated pixels in *Herschel* 250 or 350$\mu$m bands. As such, the fluxes for the source could not be extracted in four adjacent bands. For the present work we forced the Hi-GAL processing allowing for "holes" in the SED.

- **-sed_noband**: the RMS source has a 3-band 70-160-250$\mu$m counterpart in the Hi-GAL band-merged catalog, vanishing with at 350 and 500$\mu$m. For the present work we forced the Hi-GAL processing with 3-bands *Herschel* SEDs.

- **-sed_noprops**: the RMS source has a counterpart only at 70$\mu$m and, hence, no Hi-GAL-like processing can be applied to derive physical parameters.

Finally, in addition to the evolutionary information provided by the $L/M$ ratio, we also report the classification according to the method from (cite: Urquhart+2022) who define classes as quiescent, protostellar, YSO, and HII regions based on visual inspection at different wavelengths. Each region is visually inspected at 70, 24 and 8 $\mu$m. Roughly 65% of the ALMAGAL sources were cross-matched with the ATLASGAL catalog and the classification adopted from there. The remaining 35% of sources were classified by hand using the same methodology.

Table 1, available at the CDS, reports the consolidated properties of the ALMAGAL targets as revised above. Uncertainties are explicitly given in the table for the distance to each source. Uncertainties on masses and luminosities are easily derived from those and are not explicitly reported. Columns explanation is available in Appendix [7](#appendix_clump_prop).

# Properties of continuum emission

![](almagal_maps_v2_paper0a_0.jpg)

![](almagal_maps_v2_paper0a_1.jpg)

The ALMAGAL target sample spans large ranges in several physical and environmental parameters (Sect. [3](#sample)) and this is reflected in the wide variety of properties and morphologies of the 1.38 mm continuum emission. While a complete gallery of 1.38 mm continuum images is available on the project’s website[^2], in Fig. [4](#continuum_maps), we illustrate 12 continuum emission maps that illustrate the whole spectrum of morphologies in the ALMAGAL sources. Fields AG013.4582-0.0377 (#46) and AG284.0055-0.8459 (#400) shows relatively extended emission that is mostly resolved at the 1000 au scale of the full-resolution images. We can then see fields with variable level of fragmentation, from single main cores as in AG013.7869-0.2359 (#48), to small clusters more (AG285.2633-0.0501, #417), or less compact as in AG024.5252-0.1390 (#186) and AG311.4675+0.3724 (#592), to larger clusters embedded in sometimes considerable extended emission with either distinctively filamentary, as in AG028.3456+0.0605 (#263), AG320.2463-0.2942 (#647), or more irregular (the remaining panels) shapes.

In this section, we provide a characterization of the continuum emission properties in our ALMA images in relationship to the integrated properties of the target clumps. The analysis is based on the 1.38 mm continuum emission detected over 5$\sigma$ level over the root mean square (rms). This noise level is computed in each field using the residual map outside of the largest CLEAN mask used in the ALMAGAL pipeline processing (cite: SanchezMonge+2025) and it is stored in the keyword AGSTDREM of the maps FITS Header. The 5$\sigma$ threshold was adopted to minimize the inclusion of noise residuals in the morphological analysis. For each of the 1013 independent fields we produce masks containing the pixels of the continuum images with flux above the 5$\sigma$ level, which we call RoI (Region of Interest). Each cluster of connected pixels constitutes an individual RoI, so that each field may have many RoIs. For each RoI, we compute the area and the perimeter, and all RoIs smaller than the beam are discarded from further analysis. For each valid RoI, we computed the fluxes (peak, total, and median fluxes) by projecting the RoI mask onto the primary beam-corrected images (PBCOR). Figure [5](#stat_rois) reports the distribution of the number of RoIs, and their total area, per imaged clump where emission was detected. It is dominated by fields with relatively low number of RoIs, showing that the threshold level is adequate to recover areas with reliable emission. The distribution of areas is instead relatively flat, implying that large areas of emission do not necessarily result from the total contribution of many RoIs in the field.

![](Histo_NRoIs-Areas_tm1_nsig5.pdf)

In addition, for each field, we also computed the perimeter and area of the convex hull for each of the 5$\sigma$ emission contours, which is the smallest convex figure containing the contour (see Fig. [14](#area-roi-chull) for an example). Any of these geometrical properties of the dust emission in the observed fields can then be related to other integrated field properties (e.g., clump mass, surface density, $L/M$ as estimated from *Herschel* measurements), or can be compared among different fields in the sample.

## ALMA 1.38 mm emission vs *Herschel* clump properties

It is interesting to compare the ALMA 1.38 mm emission properties with global clump parameters mostly based on *Herschel* observations and listed in Table 1, particularly as parameters such as the far-IR (FIR) flux and surface density have been used as the selection criteria (Sect. [3](#sample)).

One initial aspect we want to quantify is how the thermal dust emission at different spatial scales is conserved. Interferometers introduce a spatial filtering of the emission that has a spatial scale larger than the one sampled by the shorter antenna baselines. The selection of the ALMAGAL targets sample has been based on properties directly (flux) or indirectly (mass, luminosity, surface density) estimated from the *Herschel* thermal far infrared emission. The comparison of these properties with similar properties derived from the millimeter thermal dust emission from ALMA can provide interesting insight concerning the spatial distribution of the cold dust within the target clumps. For this comparison, we chose to use the *7m+tm2* continuum images with primary-beam-corrected fluxes (PBCOR).

![](F350-tm2-Rescaled_nsig4.pdf)

Figure [6](#ftot_tm2_f350) shows the relationship between the *Herschel* 350 $\mu$m flux of the ALMAGAL target fields and the 350 $\mu$m-rescaled total flux obtained from the total 1.38 mm continuum in the 4$\sigma$ contour of the PBCOR images in the *7m+tm2* configuration, provided that the area of the contour is larger than the synthesized beam. In particular, we extrapolated the mm flux to 350$\mu$m using a modified black-body assuming different dust opacities and temperatures (see below). A 4$\sigma$ was specifically adopted here (instead of the 5$\sigma$ use in the rest of the analysis) to make sure we could recover as much as possible the emission area for a most reliable assessment of a missing flux problem. Signal is detected toward 941 out of 1013 fields ($\sim$93%), and in 336 out of 941 fields ($\sim$36%), the discrepancy between the fluxes is less than 50%. For a fraction of the fields the rescaled 350 $\mu$m flux is above the *Herschel* measured flux, but that is compatible with the uncertainties due to the assumptions in terms of dust temperature and opacities that we are forced to make to rescale the 1.38 mm flux to 350 $\mu$m. Indeed, the vertical bar in the figure represents the extent of the overall spread of 350 $\mu$m-rescaled fluxes obtained varying the temperature between 20 K and 50 K, dust spectral index $\beta$ between 1.5 and 2 (a range typical for diffuse ISM and dense clumps), and assuming opacities from (cite: preib93), (cite: OH1994) and (cite: Draine2003).

The figure shows that the distribution is strongly skewed toward low *7m+tm2*-rescaled fluxes. For about 64% of the fields the rescaled *7m+tm2* recovered flux is much less than 50% of the *Herschel* flux, and for these fields this is a clear indication of missing emission. The extent of the emission in the 350 $\mu$m *Herschel* images is generally larger than the ALMA FOV, so that the discrepancy could result simply from the different sizes of the areas sampled. However, the beam of *Herschel* at 350 $\mu$m is $\sim$80% of the ALMA FOV and therefore the far-IR emission could plausibly come from smaller areas within the ALMA FOV. In particular, for 90% of the targets the measured clump FWHM from *Herschel* is smaller than the ALMA FOV; the percentage rises to 95% if the beam-deconvolved *Herschel* size is adopted. We conclude that it was only in 10% of the targets that the discrepancy in recovered flux could be attributed to differences in the areas of the sky sampled by *Herschel* and ALMA.

Instead, the color scale of the points shows that these fields have the lowest surface density, as estimated from *Herschel*; hence, the dust distribution is expected to be less compact and more prone to spatial filtering by the interferometer. This indicates that for a significant fraction of targets we may be missing flux from larger angular scales, and the use of physical parameters such as the total clump mass that could be derived from integrated ALMA millimeter fluxes is not reliable for the majority of the fields.

![](emissionarea-vs-F350_tm1_nsig5.pdf)

We wanted to concentrate on the morphology of continuum emission for this work. Figure [7](#roi-area_f350) shows the relationship between the 1.38 mm total emission area above 5$\sigma$ level in the ALMA *7m+tm2+tm1* image as a function of the *Herschel* 350 $\mu$m flux. The plot outlines a very good correlation among the two parameters that is not influenced by the different distances of the targets as neither of the two parameters depends on it (figs. [19](#roi-area_dist),[20](#f350_dist)). The Pearson linear correlation coefficient is $r_P$=0.74.

The fraction of fields with no detected emission above 5$\sigma$ in ALMA is concentrated toward the low end of the 350 $\mu$m flux distribution, but there is no indication of an exact far-IR flux threshold for the 1.38mm detection. The figure confirms that the 350 $\mu$m flux cut adopted for the selection of the ALMAGAL target clumps is well matched to the chosen ALMAGAL target sensitivity. A fraction of targets below 10% is not detected with ALMA also for relatively large 350 $\mu$m fluxes. The average properties of non-detected fields are discussed in Elia et al. (in prep.).

Figure [8](#roi-area_surf_d) shows the relationship between the ALMA 1.38 mm 5$\sigma$ area and the clump surface density estimated from Hi-GAL data. As in the previous figure, the red histogram shows the $\Sigma_{\mathrm{Clump}}$ distribution for fields without 5$\sigma$ detection. Here again a correlation is clearly apparent, with $r_P$=0.57 suggesting indeed a good correlation, although with a large scatter in the $y$-axis distribution.

The problem of possible missing flux may play a role in determining the scatter of the points; however this should affect only the relatively lower surface density clumps (see Fig. [6](#ftot_tm2_f350)), while the scatter we see in the Y direction in Fig. [8](#roi-area_surf_d) is independent from the range of surface density. The points reported in green color identify the clumps with $L/M \geq 5$, showing that they predominantly populate the upper range of the points distribution. Therefore, it is the clump evolutionary stage that introduces most of scatter.

The relation between the Hi-GAL $\Sigma_{\mathrm {clump}}$ and the ALMAGAL 1.38-mm 5$\sigma$ area is interesting for two key reasons. First, it again reinforces the adopted choice of parameters to drive the ALMAGAL source selection. The 1.38 mm emitting area, under the optically thin assumption, is a proxy for the dust column density spatially resolved in the ALMAGAL maps; the surface density estimated from *Herschel* observations is also a measurement of column density that is, however, an integrated quantity averaged over the extent of the clump. It is then reassuring to verify that in spite of the missing flux problem and taking into account evolutionary effects, the two parameters are indeed correlated. In addition, the fractional distribution of $\Sigma_{\mathrm{Clump}}$ for non-detected fields in ALMA is heavily skewed toward the lower end of the range and this suggests that the choice of the target sensitivity adopted for the ALMAGAL observations is very well matched to the average properties of selected targets.

![](emissionarea-vs-surfdens_tm1_nsig5.pdf)

Second, since the millimeter continuum in interferometric observations traces denser and compact rather than diffuse and extended ISM (as suggested in Fig. [8](#roi-area_surf_d)), the degree of mass concentration as traced by the clump-averaged $\Sigma_{\mathrm{Clump}}$ has a role in determining the amount of dense material that is found at smaller spatial scales probed by ALMA. Furthermore the correlation present in Fig. [8](#roi-area_surf_d) completely disappears if we use the clump mass instead of its surface density (see Fig. [24](#roi_area_mass)), confirming that is not simply the available mass that drives the process by which the clump ISM is shaped at smaller and smaller scales, but the shape of the gravitational potential. This was anticipated by, for instancem, (cite: MKT2002) and will be explored in more detail in Elia et al. (in prep.). To illustrate how we excluded the possible presence of a bias introduced by the different distances of the targets, in Fig. [21](#roi-area-surf_d_bins) we report the same two quantities of Fig. [8](#roi-area_surf_d), but in separate distance bins, showing that the relationship holds irrespectively of the distance to the sources.

To illustrate more clearly the degree to which the extent of dense ISM in the clumps fields depends on their evolutionary stage, we report in Fig. [9](#roi-area_lm) the 1.38 mm ALMA 5$\sigma$ emission area as a function of the clumps, $L/M$. The two parameters appear indeed correlated, and the large scatter in the Y axis is this time due to the spread in surface density. Indeed in the figure we outline with green symbols the clumps with higher surface density, finding that the larger 1.38 mm emission areas are indeed found on average toward clumps with higher surface density. The correlation coefficient for the entire dataset in Fig. [9](#roi-area_lm) is $r_P$=0.53, confirming a relatively good correlation. However, this is mostly driven by the higher $\Sigma_{\mathrm{Clump}}$ points for which we have $r_P$=0.66 and for which the correlation is therefore stronger. The correlation for the subset with lower $\Sigma_{\mathrm{Clump}}$ is only moderate, with correlation coefficient dropping to $r_P$=0.42.

![](emissionarea-vs-LM_tm1_nsig5.pdf)

Since the clump surface density does not appear to be an evolutionary indicator based on the $L/M$ (cite: Elia+2017), we conclude from this preliminary global analysis of the continuum emission in ALMAGAL fields that the presence of dense ISM substructures in the target clumps depends both on the initial conditions for clumps fragmentation (as traced by the clump-averaged surface density) and the global evolutionary stage of the clumps as traced by the $L/M$ parameter.

## The morphology of 1.38 mm emission in ALMAGAL

Given this large variance in the morphological appearance of the 1.38 mm continuum emission (Fig. [4](#continuum_maps)), we would like to verify whether there is a metric that is able to clearly categorize the morphology into different classes that could be then related to physical parameters. In the following, we explore the relationship between the area of the emission with its perimeter and with the area of its convex hull.

### Area vs perimeter

A first simple approach in the characterization of the morphology of the 1.38 mm continuum’s spatial distribution, is to analyse the relationship between the area A and the perimeter P of the RoIs identified by thresholding images above the 5$\sigma$ level. In generalized terms, the two quantities are related as:

$$\begin{equation}
    P=k A^{d/2}
\label{eq_perimarea} 
,
\end{equation}$$

with $k$ depending on the specific geometric figure describing the RoI delimiting shape; for instance, in 2D we have $k$=4 for a square or $k=2\sqrt{\pi}$ for a circle.

The exponent $d$ is the dimension of the shape bounding the RoI; it is $d=1$ for linear contours in 2D space and $d=2$ for surfaces enclosing volumes in 3D. As we depart from regular Euclidean planar figures, replicating so-called generator patterns in a self-similar way at smaller and smaller scales to describe increasingly irregular contours, $d$ can assume non-integer values between 1 and 2 and in this we recognize the fractal dimension.

Figure [10](#area_perim_roi) illustrates the perimeter-area plot for the 5$\sigma$ RoIs identified in each ALMAGAL field, where the two parameters have been summed over all RoI. To understand the meaning of the spread of the points in this plot, it is useful to mark locations that would be compatible with simple structures or their combination. For example, the black and red lines corresponds to Eq. [\[eq_perimarea\]](#eq_perimarea) in the case of one circle ($k=2\sqrt{\pi}$) or of one ellipse[^3] with aspect ratio $\mathrm{a.r.}=3$. We see that only in a small number of cases the emission area is compatible with a single circular or elliptical shape and only for small areas of a few arcsec$^2$, corresponding to about four to five times the maximum beam area represented by the vertical dashed line (from (cite: SanchezMonge+2025)). As another example, if we assume that the total emission area is divided in, say, five equal circular RoIs then the correspondent locus in the plot is given by the green line; similarly, the blue line shows the locus in case the emission area was composed of ten equal elliptical RoIs with $\mathrm{a.r.}$=5.

The distribution of points shows a continuum of situations. The limited vertical scatter for relatively small emission areas (left of the vertical dashed line) is a construction bias, as for these small areas, there is low maximum number of RoIs it can be divided into and still be at least the size of the beam. The vertical scatter becomes much wider as we increase the total RoIs area. All clumps below and about the green line would be compatible with small clusters of compact objects even for relatively large total emission areas (up to $\sim$100 sq. arcsec.). Clumps with emission showing a larger departure from the circularity could be compatible with even larger cluster of compact roughly circular objects, or a more limited number of filamentary patches idealized as the combination of ten high-a.r. ellipses and represented by the blue line. Of course, large deviations from a single circular RoI may also be compatible with a few patches of very irregular emission; we present an additional characterization in this respect below.

![](AllStruct_Area-vs-Perim_tm1_nsig5.pdf)

To quantify this behavior, we defined a parameter $\Delta^{\rm circ} _{5\sigma}$ computed as the distance between each point and the black line (along the direction perpendicular to the line) in Fig. [10](#area_perim_roi).

![](hist_circ-depart_tm1_nsig5.pdf)

In Fig. [11](#histo_deltacirc), we report the distribution of the $\Delta^{\rm circ} _{5\sigma}$ parameters in our fields, computed individually for all the RoIs in the fields (black line), for the largest RoI in each field (green line), and for the sum of the RoIs in each field (blue line). Histograms are normalized to their integral to make their comparison meaningful. The distribution for all RoIs (black) shows a clear predominance of circular and slightly elongated shapes, with a monotonically decreasing trend toward larger values of $\Delta^{\rm circ} _{5\sigma}$. This might suggest that in many cases the secondary RoIs at the 5$\sigma$ level are dominated by small circular areas that are either fainter patches of extended emission or compact objects isolated with respect to the main emission area in the field.

When considering only the largest RoI in each field (green), the distribution is clearly different and shows a first component peaked around 0 (circular shape) decreasing down to about $\Delta^{\rm circ} _{5\sigma}$$\sim0.2$, followed by a second smaller and broader peak down to $\Delta^{\rm circ} _{5\sigma}$$\sim 0.5$. If, instead, we consider all the RoIs in each field and we compute the total perimeter and total area, the corresponding $\Delta^{\rm circ} _{5\sigma}$ distribution is the blue line; in addition to this blue line, a narrow component skewed toward 0 (i.e., circular structure) shows an even broader (compared to the green distribution) component extending to $\sim0.8$. This metric seems therefore able to select fields that are showing either complex patterns of extended emission or collections of roughly circular or elongated structures (or, mostly likely, both). Values of $\Delta^{\rm circ} _{5\sigma}$ for all clumps are reported in Table 2.

![](circ-depart_total_tm1_nsig5-vs-SURF_D.pdf)

It is interesting to verify whether these metrics are related to global clump properties. The relationship of the $\Delta^{\rm circ} _{5\sigma}$ parameter with the clump-averaged surface density in Fig. [12](#deltacirc_surfd_fig) shows a positive correlation, although as usual with a large scatter around the median values computed in bins of $\Sigma_{\mathrm{Clump}}$ (the red asterisks). While clumps with $\Sigma_{\mathrm{Clump}}\leq$1 g cm$^{-2}$ span the entire range of $\Delta^{\rm circ} _{5\sigma}$, almost the totality of denser clumps have $\Delta^{\rm circ} _{5\sigma}$ higher than values compatible with circular or slightly elliptical shapes. Similarly to Fig. [8](#roi-area_surf_d), we exclude the presence of remarkable distance biases in Fig. [12](#deltacirc_surfd_fig) as similar trends are found if the two parameters are plotted for sources in 1 kpc-bin distances (Fig. [23](#deltacirc_surfd_fig_d_bins)).

![](circ-depart_total_tm1_nsig5-vs-LM.pdf)

A similar situation is found when relating $\Delta^{\rm circ} _{5\sigma}$ with $L/M$. Figure [13](#deltacirc_lm_fig) shows that the scatter in the Y axis grows with evolution, with median-averaged values clearly rising with $L/M$, depicting the more and more frequent presence of complex morphologies with evolution. The points in the figure are color-coded with the clump surface density, and confirm (see also Fig. [12](#deltacirc_surfd_fig)) that this parameter has a strong role in modulating the scatter in the Y axis of Fig. [13](#deltacirc_lm_fig). For example, if we restrict to the clumps with $\Sigma_{\mathrm{Clump}}\geq 1$g cm$^{-2}$ (the cyan to red points), we are left with a moderate but significant $\Delta^{\rm circ} _{5\sigma}$-$L/M$ trend with $r_P$$\sim0.46$.

### Area versus convex hull

Another interesting metric to characterize the complexity of the emission morphology is offered by the comparison of the areas of the RoIs and the respective convex hull areas. For a bounded subset of the plane, the convex hull may be visualized as the shape enclosed by a rubber band stretched around the subset (cite: Berg+2008). As it essentially represents the smallest convex geometric figure containing the emission RoIs, we expect the two areas to be very similar in case of very regular (roughly circular or elliptical) shapes. On the contrary,. the two areas will be different in case where the RoI is the result of the merging of two or more distinct regions, for instance, or in the case of hub-like filamentary structure. In the following, we define the parameter $Q^{\rm hull} _{5\sigma}$ as the ratio $A_{RoI}/A_{C-Hull}$ between the area of the largest RoI and its convex hull area computed over the areas with signal above the 5$\sigma$ level.

![image](figure_chull_126991.jpg) ![image](figure_chull_658676.jpg)

Figure [14](#area-roi-chull) shows an example of two extreme cases in which the emission area above 5$\sigma$ has a similar extent (inside the blue contour), but $Q^{\rm hull} _{5\sigma}$ is relatively high ($\sim0.85$) for the relatively regular source (top), and drops to 0.5 for the more complex structure field (bottom). Figure [15](#histo-roi-chull) reports the histogram of this parameter over the entire sample where 5$\sigma$ continuum emission is detected, and suggests that there may possibly be two peaks in the distribution, separated at a value of $\sim$0.8. We ran the Silverman test (cite: Silverman1981) to characterize multi-modality using kernel density estimates over the distribution of the original data, and hence not on binned histograms. The test confirms that the distribution reported in Fig. [15](#histo-roi-chull) has a 100% probability of being better described by two modes instead of one. $Q^{\rm hull} _{5\sigma}$ then offers a simple metric to classify fields based on the convex (or not) nature of their continuum emission.

![](Histo_RoI-CHull_ratio_tm1_nsig5.pdf)

The relationship of this parameter with the clump’s evolutionary stage in Fig. [16](#area-roi-chull-lm) shows a broadly decreasing trend with $L/M$, indicating that the emission morphology of the largest emission area in each field gets more and more complex as the field is more evolved. This is also clearly shown in Fig. [17](#histo-area-roi-chull-lm), where the distribution of $L/M$ is reported separately for the fields with “regular” ($Q^{\rm hull} _{5\sigma}$$\geq$0.8, black line) and “irregular” ($Q^{\rm hull} _{5\sigma}$$\leq$0.8, red line) continuum emission morphologies. The $L/M$ for the two fields in Fig. [14](#area-roi-chull) is $\sim$0.05 for AG028.5671-0.2329 and $\sim26$ for AG288.9609+0.2643, respectively.

![](RoI-CHull_ratio_tm1_nsig5-vs-LM.pdf)

![](Histo_LM_RoI-CHull_ratio_tm1_nsig5-vs-LM.pdf)

There is, of course, a bias introduced by the finite resolution of the images. Fields with only compact beam-like emission patches will naturally be roughly circular in morphology, making this metric not informative. These are, however, only a portion of the fields with high $Q^{\rm hull} _{5\sigma}$. Figure [18](#area-vs-chull) illustrates the relationship between $Q^{\rm hull} _{5\sigma}$ and the 5$\sigma$ emission area. The horizontal dashed line marks the $Q^{\rm hull} _{5\sigma}$$\sim$0.8 threshold identified in Fig. [15](#histo-roi-chull) to distinguish approximately circular areas of emission from more complex morphologies, while the vertical dashed line indicates the maximum area of the beam for all fields. If roughly circular areas were only due to beam-like or modestly resolved compact emission, we would not expect to see points in the top-right quadrant (defined by the two dashed lines) that instead contains $\sim44$% of the fields with $Q^{\rm hull} _{5\sigma}$$\geq$0.8. We then conclude that the $Q^{\rm hull} _{5\sigma}$ metric contains valuable information to classify the continuum emission morphology.

![](RoI-CHull_ratio-vs-Area_tm1_nsig5.pdf)

From a qualitative viewpoint, both the $\Delta^{\rm circ} _{5\sigma}$ and the $Q^{\rm hull} _{5\sigma}$ metrics suggest that a more complex dust spatial structure is observed as the clumps evolve. This is fully compatible with a concurrent contribution from increasing column density and/or increasing temperature of the dust with $L/M$ due to radiative (and possibly dynamical) feedback from the forming protostars. In both cases, the millimeter flux would increase, causing more and more material to become detectable above the noise. Figure [9](#roi-area_lm) shows that indeed the area of detectable emission increases with $L/M$ (or evolution), and Figs. [13](#deltacirc_lm_fig), [16](#area-roi-chull-lm), and [17](#histo-area-roi-chull-lm) show that this larger area deviates more and more from a roughly circular shape and gets more and more irregular and complex with $L/M$. In other words as the clumps evolve we do not find relevant occurrences of large and circular areas of emission. This certainly agrees with a dynamically evolving clump fragmentation, also influenced by increasing levels of feedback. Conversely, these findings do not support the notion of relatively massive seeds of fragmentation that regularly grow in extension with increasing column density or temperatures. In Table 2, available at the CDS, contains some of the parameters we have presented in this section; namely, for each field, the emission area above 5$\sigma$ level both in physical units and as fraction of the field of view, plus the $\Delta^{\rm circ} _{5\sigma}$ and the $Q^{\rm hull} _{5\sigma}$ parameters determined for the largest detected structure in each field.

# Forward outlook

ALMAGAL is a game changer in areas like fragmentation statistics and morphologies, gas dynamics in infall and outflow motions in the clumps, chemistry, and systematic disk detections, among others. Here, we present a brief summary of the more immediate works that are already published or will be submitted and published in the next six months. (cite: Wells+2024) published a first study of flow dynamics in a subsample of 100 ALMAGAL fields based on H$_2$CO lines. (cite: Coletta+2025) presents the first release of a continuum compact source catalog, which includes the core physical properties and a first discussion of the core mass function in evolutionary terms. Elia et al. (in prep.) will discuss core properties in the context of the hosting clumps, while Schisano et al. (in prep.) will present an in-depth analysis of the morphological distribution of cores and their mass segregation. Wallace et al. (in prep.) will investigate the multiscale morphological properties of continuum emission, greatly extending the preliminary analysis presented in this paper. (cite: Mininni+2025) discusses the multiscale morphological relationship between the dust continuum and molecular line emission of CH$_3$CN, CH$_3$OH, H$_2$CO, HC$_3$N, and other tracers. Benedettini et al. (in prep.) analyses the relationship between the distribution of $v_{\rm LSR}$ of molecular lines and the dynamical properties of the hosting clumps gas. An investigation of the $^{13}$C/$^{12}$C Galactic gradient will be presented by Law et al. (in prep.), while Stroud et al. (in prep.) will discuss the evolutionary properties of continuum cores in the context of the association with methanol masers. Finally, Jones et al. (in prep.) and Allande et al. (in prep.) will present a first catalog of molecular lines, complete with the derived gas physical properties, toward the 1.38 mm cores of (cite: Coletta+2025).

Extending the forward look toward 2026, we anticipate studies on complex organic molecules (Allande et al., in prep.), line-based physical and evolutionary studies based on machine-learning methodologies (Sanchez-Monge et al., in prep.) and cores virial analysis (Mininni et al., in prep.). Finally, the ALMAGAL data have also proved effective for preliminary studies of disks towards the brightest cores that led to follow-up studies that will be presented by Ahmadi et al. (in prep.).

A first complete public release of the *7m+tm2+tm1* and *7m+tm2* continuum images will be done after the acceptance of the first round of continuum-based papers introduced above, and we anticipate this to take place no later than December 2025. A first round of papers with a preliminary exploitation of the *7m+tm2+tm1* and *7m+tm2* spectroscopic datacubes is in relatively less advanced stage, so that their public release takes place no later than December 2026.

# Conclusions

The ALMAGAL Large Program has mapped 1013 dense star-forming clumps in the 1.38 mm continuum and lines to obtain the first statistically significant demographic description of the fragmentation process that leads to the formation of dense cores. In this first paper, we present a complete review of the target clumps physical properties, with a first analysis of the morphological properties of the dust continuum emission. We find that metrics such as the perimeter and area ratio, along with the convex hull and area ratio, are effective in mapping the emergence of complex irregular morphologies proportionally to the evolutionary stage of the clumps and their surface density.

# Acknowledgements

S.M and the Team at INAF-IAPS gratefully acknowledge financial support from the European Research Council via the ERC Synergy Grant “ECOGAL” (project ID 855130). R.S.K. acknowledges financial support from the European Research Council via the ERC Synergy Grant “ECOGAL” (project ID 855130), from the Heidelberg Cluster of Excellence (EXC 2181 - 390900948) “STRUCTURES”, funded by the German Excellence Strategy, and from the German Ministry for Economic Affairs and Climate Action in project “MAINN” (funding ID 50OO2206). R.S.K. is grateful for support from the Harvard Radcliffe Institute for Advanced Studies and Harvard-Smithsonian Center for Astrophysics for their hospitality and support during his sabbatical. The team in Heidelberg also thanks for computing resources provided by the Ministry of Science, Research and the Arts (MWK) of *The Länd* through bwHPC and the German Science Foundation (DFG) through grant INST 35/1134-1 FUGG and 35/1597-1 FUGG, and also for data storage at SDS@hd funded through grants INST 35/1314-1 FUGG and INST 35/1503-1 FUGG. S.W. gratefully acknowledges the Deutsche Forschungsgemeinschaft (DFG) for funding through SFB 1601 “Habitats of massive stars across cosmic time’’ (sub-project A5) and the ”NRW-Cluster for data-intensive radio astronomy: Big Bang to Big Data (B3D)” funded through the ”Profilbildung 2020” program of the Ministry of Culture and Science of the State of North Rhine-Westphalia, Germany. A.S.-M. acknowledges support from the RyC2021-032892-I grant funded by MCIN/AEI/10.13039/501100011033 and by the European Union ‘Next GenerationEU’/PRTR, as well as the program Unidad de Excelencia María de Maeztu CEX2020-001058-M, and support from the PID2020-117710GB-I00 (MCI-AEI-FEDER, UE). L.B. gratefully acknowledges support by the ANID BASAL project FB210003. G.A.F gratefully acknowledges the Deutsche Forschungsgemeinschaft (DFG) for funding through SFB 1601 “Habitats of massive stars across cosmic time’’ (sub-project B2), the University of Cologne and its Global Faculty Programme. A.A. acknowledges support from the UK ALMA Regional Centre (ARC) Node which is supported by the Science and Technology Facilities Council \[grant number ST/T001488/1\]. C.B. and J.W. gratefully acknowledge funding from the National Science Foundation under Award Nos. 2108938 and 2206510, as well as CAREER 2145689 for C.B. R.K. acknowledges financial support via the Heisenberg Research Grant funded by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) under grant no. KU 2849/9, project no. 445783058. Part of this research was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with the National Aeronautics and Space Administration (80NM0018D0004).\
This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00195.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

87 natexlab

(ref: Adamo2020) Adamo, A., Zeidler, P., Kruijssen, J. M. D., et al. 2020, Space Sci. Rev., 216, 69

(ref: Adams2010) Adams, F. C. 2010, ARA&A, 48, 47

(ref: MAnderson+21) Anderson, M., Peretto, N., Ragan, S. E., et al. 2021, MNRAS, 508, 2964

(ref: Avison+2023) Avison, A., Fuller, G. A., Frimpong, N. A., et al. 2023, MNRAS, 526, 2278

(ref: Berg+2008) Berg, M., van Kreveld, M., Overmars, M., & Schwarzkopf, O. 2008, Computational Geometry: Algorithms and Applications (3rd ed.) (Springer)

(ref: Beuther+2015) Beuther, H., Henning, T., Linz, H., et al. 2015, A&A, 581, 119

(ref: Beuther+2018) Beuther, H., Mottram, J. C., Ahmadi, A., et al. 2018, A&A, 617, 100

(ref: Bolatto+2013) Bolatto, A. D., Warren, S. R., Leroy, A. K., et al. 2013, Nature, 499, 450

(ref: BonnellBate2006) Bonnell, I. A. & Bate, M. R. 2006, MNRAS, 370, 488

(ref: Bonnell+2007) Bonnell, I. A., Larson, R. B., & Zinnecker, H. 2007, Protostars and Planets V, 149

(ref: Cesaroni+2015) Cesaroni, R., Pestalozzi, M., Beltrán, M. T., et al. 2015, A&A, 579, 71

(ref: Chen+2019) Chen, H.-R. V., Zhang, Q., Wright, M. C. H., Busquét, G., & et al. 2019, ApJ, 875, 24

(ref: Coletta+2025) Coletta, A., Molinari, S., Schisano, E., et al. 2025, A&A, Accepted

(ref: Comm+2011) Commercon, B., Hennebelle, P., & Henning, T. 2011, ApJl, 742, L9

(ref: Contreras+2018) Contreras, Y., Sanhueza, P., Jackson, J. M., et al. 2018, ApJ, 861, 14

(ref: Csengeri+2017) Csengeri, T., Bontemps, S., Wyrowski, F., et al. 2017, A&A, 600, 10

(ref: Draine2003) Draine, B. T. 2003, ARA&A, 41, 241

(ref: Duarte-Cabral13) Duarte-Cabral, A., Bontemps, S., Motte, F., et al. 2013, A&A, 558, A125

(ref: Elia+2021) Elia, D., Merello, M., Molinari, S., et al. 2021, MNRAS, 504, 2742

(ref: Elia+2017) Elia, D., Molinari, S., Schisano, E., et al. 2017, MNRAS, 471, 100

(ref: Girichidis2012) Girichidis, P., Federrath, C., Banerjee, R., & Klessen, R. S. 2012, MNRAS, 420, 613

(ref: Gong+2009) Gong, H. & Ostriker, E. C. 2009, ApJ, 699, 230

(ref: He+2015) He, Y.-X., Zhou, J.-J., Esimbek, J., et al. 2015, MNRAS, 450, 1926

(ref: Hunter2024) Hunter, G. H., Sormani, M. C., Beckmann, J. P., et al. 2024, arXiv e-prints, arXiv:2403.18000

(ref: Irabor+2023) Irabor, T., Hoare, M., Burton, M., et al. 2023, MNRAS, 520, 1073

(ref: Ishihara+2024) Ishihara, K., Sanhueza, P., Nakamura, F., et al. 2024, ApJ, arXiv:2407.06845

(ref: Jeans1902) Jeans, J. H. 1902, Philosophical Transactions of the Royal Society of London Series A, 199, 1

(ref: Jijina+1996) Jijina, J. & Adams, F. C. 1996, ApJ, 462, 874

(ref: Kauffmann+Pillai2010) Kauffmann, J. & Pillai, T. 2010, ApJl, 723, L7

(ref: KW2006) Keto, E. & Wood, K. 2006, ApJ, 637, 850

(ref: Klaassen+2012) Klaassen, P. D., Testi, L., & Beuther, H. 2012, A&A, 538, 140

(ref: Klessen2000) Klessen, R. S. 2000, ApJ, 535, 869

(ref: klessen2016) Klessen, R. S. & Glover, S. C. O. 2016, Saas-Fee Advanced Course, 43, 85

(ref: Konyves+2010) Konyves, V., André, P., Men’shchikov, A., et al. 2010, A&A, 518, 106

(ref: Krumholz+2014) Krumholz, M. R., Bate, M. R., Arce, H. G., et al. 2014, Protostars and Planets VI, 243

(ref: Krumholz+2009c) Krumholz, M. R., Klein, R. I., McKee, C. F., Offner, S. S. R., & Cunningham, A. J. 2009, Science, 323, 754

(ref: Lada+Lada03) Lada, C. J. & Lada, E. A. 2003, ARA&A, 41, 57

(ref: Larson1985) Larson, R. B. 1985, MNRAS, 214, 379

(ref: Liu+2020) Liu, T., Evans, II, N. J., Kim, K., & et al. 2020, MNRAS, 496, 2790

(ref: Lumsden+2013) Lumsden, S. L., Hoare, M. G., Urquhart, J. S., et al. 2013, ApJS, 208, 11

(ref: Maeder2000) Maeder, A. & Meynet, G. 2000, ARA&A, 38, 143

(ref: MKT2002) McKee, C. F. & Tan, J. C. 2002, Nature, 416, 59

(ref: mck03) McKee, C. F. & Tan, J. C. 2003, ApJ, 585, 850

(ref: Mege+2021) Mege, P., Russeil, D., Zavagno, A., et al. 2021, A&A, 646, 74

(ref: Merello19) Merello, M., Molinari, S., Rygl, K. L. J., et al. 2019, MNRAS, 483, 5355

(ref: Mininni+2025) Mininni, C., Molinari, S., Soler, J. D., et al. 2025, A&A, Subm.

(ref: Molinari+2019) Molinari, S., Baldeschi, A., Robitaille, T. P., et al. 2019, MNRAS, 486, 4508

(ref: Molinari+2016c) Molinari, S., Merello, M., Elia, D., et al. 2016a, ApJl, 826, L8

(ref: Molinari+2008) Molinari, S., Pezzuto, S., Cesaroni, R., et al. 2008, A&A, 481, 345

(ref: Molinari+2016a) Molinari, S., Schisano, E., Elia, D., et al. 2016b, A&A, 591, 149

(ref: Motte+2022) Motte, F., Bontemps, S., Csengeri, T., et al. 2022, A&A, 662, 8

(ref: Motte+2018) Motte, F., Nony, T., Louvet, F., et al. 2018, Nature Astronomy, 2, 478

(ref: Nonhebel+2024) Nonhebel, M., Barnes, A. T., Immer, K., et al. 2024, A&A, 691, 70

(ref: Nony+18) Nony, T., Louvet, F., Motte, F., et al. 2018, A&A, 618

(ref: OH1994) Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943

(ref: Palau+2015) Palau, A., Ballesteros-Paredes, J., Vázquez-Semadeni, E., & et. al. 2015, MNRAS, 453

(ref: Peretto+2013) Peretto, N., Fuller, G. A., Duarte-Cabral, A., et al. 2013, A&A, 555, 112

(ref: Peters2011) Peters, T., Banerjee, R., Klessen, R. S., & Mac Low, M.-M. 2011, ApJ, 729, 72

(ref: Peters2010) Peters, T., Banerjee, R., Klessen, R. S., et al. 2010, ApJ, 711, 1017

(ref: PSZ2010) Portegies Zwart, S. F., McMillan, S. L. W., & Gieles, M. 2010, ARA&A, 48, 431

(ref: preib93) Preibisch, T., Ossenkopf, V., Yorke, H., & Henning, T. 1993, A&A, 279, 577

(ref: Purcell2013) Purcell, C. R., Hoare, M. G., Cotton, W. D., et al. 2013, ApJS, 205, 1

(ref: Rees1976) Rees, M. J. 1976, MNRAS, 176, 483

(ref: Rigby+2024) Rigby, A. J., Peretto, N., Anderson, M., Ragan, S. E., & et al. 2024, MNRAS, 528, 1172

(ref: Rygl+2013) Rygl, K. L. J., Wyrowski, F., Schuller, F., & Menten, K. M. 2013, A&A, 549, 5

(ref: SanchezMonge+2025) Sanchez-Monge, A., Brogan, C. L., Hunter, T. R., et al. 2025, A&A, Accepted

(ref: Sanhueza+19) Sanhueza, P., Contreras, Y., Wu, B., Jackson, J. M., & et al. 2019, ApJ, 886, 102

(ref: Silverman1981) Silverman, B. W. 1981, J. Roy. Stat. Soc., 43, 97

(ref: Smith+2009) Smith, R. J., Clark, P. C., & Bonnell, I. A. 2009, MNRAS, 396, 830

(ref: Svoboda+19) Svoboda, B. E., Shirley, Y. L., Traficante, A., et al. 2019, ApJ, 886, 36

(ref: Tackenberg+2012) Tackenberg, J., Beuther, H., Henning, T., et al. 2012, A&A, 540, 113

(ref: Tan+2014) Tan, J. C., Beltrán, M. T., Caselli, P., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. Klessen, C. P. Dullemond, & T. Henning

(ref: Traficante+2018) Traficante, A., Duarte-Cabral, A., Elia, D., et al. 2018, MNRAS, 477, 2220

(ref: Traficante+2017) Traficante, A., Fuller, G. A., Billot, N., et al. 2017, MNRAS, 470, 3882

(ref: Traficante+2020) Traficante, A., Fuller, G. A., Duarte-Cabral, A., et al. 2020, MNRAS, 491, 4310

(ref: Traficante+2023) Traficante, A., Jones, B. M., Avison, A., et al. 2023, MNRAS, 520, 2306

(ref: Urquhart+2022) Urquhart, J., Wells, M. R. A., Pillai, T., et al. 2022, MNRAS, 510, 3389

(ref: Urquhart+2018) Urquhart, J. S., Koenig, C., Giannetti, A., et al. 2018, MNRAS, 473, 1059

(ref: Vazquez2019) Vázquez-Semadeni, E., Palau, A., Ballesteros-Paredes, J., Gómez, G. C., & Zamora-Avilés, M. 2019, MNRAS, 490, 3061

(ref: veilleux2005) Veilleux, S., Cecil, G., & Bland-Hawthorn, J. 2005, ARA&A, 43, 769

(ref: Wells+2024) Wells, M. R. A., Beuther, H., Molinari, S., & et al. 2024, A&A, 690, 185

(ref: Wells+2022) Wells, M. R. A., Urquhart, J. S., Moore, T. J. T., et al. 2022, MNRAS, 516, 4245

(ref: Wu+2003) Wu, J. & Evans, II, N. J. 2003, ApJl, 592, L79

(ref: Xu+2024) Xu, F., Wang, K., Liu, T., & et al. 2024, ApJS, 270, 9

(ref: yor02) Yorke, H. W. & Sonnhalter, C. 2002, ApJ, 569, 846

(ref: Zhang+2015) Zhang, Q., Wang, K., Lu, X., & Jimenez-Serra, I. 2015, ApJ, 804, 141

(ref: Zinnecker2007) Zinnecker, H. & Yorke, H. W. 2007, ARA&A, 45, 481

# ALMAGAL Clumps Properties

Here, we give a brief description the Table 1, available at the CDS, containing the consolidated properties of the ALMAGAL targets revised as explained in the main text:

- Col. 1: an ordinal number of the field

- Cols. 2-3: unique ALMAGAL source name file ID together with the original designations either in the Hi-GAL band-merged catalog ("HBM" prefix) ot the RMS survey ("G" prefix)

- Cols. 4-5: Galactic coordinates of the fields center

- Col 6: the target membership to either "near" or "far" ALMAGAL subsamples (col. 6) defining the ALMA antenna configurations used and hence the minimum achieved angular resolution (0$^{\prime \prime}$,15 and 0$^{\prime \prime}$.3 respectively)

- Col. 7: revised $v_{\rm LSR}$

- Col. 8: revised heliocentric distance

- Cols. 9-10: Clump mass and bolometric luminosity from (cite: Elia+2021), or derived with the same methodology (see Sect. [3.2.2](#sample_homo) above) rescaled at the revised distance of Col. 8

- Cols. 11-12: cold dust temperature and bolometric temperature as in (cite: Elia+2021), or derived with the same methodology.

- Col. 13: clump surface density reported from (cite: Elia+2021), with the difference that the area used for the computation is based on the measured clump size without deconvolving the *Herschel* beam.

- Col. 14: Evolutionary class after (cite: Urquhart+2022): Q (quiescent), P (protostellar), Y (young stellar object), and H (HII region). Cases where the methodology failed to identify a specific class are labeled "n/a".

The last column may contain a series of strings describing some specificities about the revision process of the target properties. The strings have the following meanings:

- **-kda_defnear**: source originally set at FAR kinematic distance solution by Mege et al. 2021 in absence of any KDA discriminator. In this work the NEAR distance decision is instead adopted for these sources, for consistency with the approach followed for the sources from the RMS sample.

- **-V7**: the new ALMAGAL-based $v_{\rm LSR}$ differs from the original by more than 7 km s$^{-1}$

- **-D500**: the new ALMAGAL-based distance differs from the original by more than 500pc.

- **-Dn2f**: the new distance determined from the $v_{\rm LSR}$ of ALMAGAL dense tracer lines, switches this source from the NEAR to the FAR sample. As originally belonging to the NEAR sample it was observed with a maximum 0.3 arcsec resolution, therefore now resulting in a sub-optimal linear resolution.

- **-Df2n**: the new distance determined from the $v_{\rm LSR}$ of ALMAGAL dense tracer lines, switches this source from the FAR to the NEAR sample. As originally belonging to the FAR sample it was observed with a maximum 0.15 arcsec resolution, therefore now resulting in a super-optimal linear resolution.

- **-D\>8**: the new distance determined from the $v_{\rm LSR}$ of ALMAGAL dense tracer lines, puts the source beyond the distance limit used to select the original sample.

- **-refit40k**: the dust temperature estimated from *Herschel* fluxes has been updated here with respect to Elia et al. (2017, 2021) due to a 40K hard limit that was reached in the grey-body fit.

- **-sed_irr**: RMS source with a Hi-GAL counterpart in the *Herschel* 5 bands, but the SED is irregular (not a single downward-facing concavity) and did not pass criteria to be included in Elia et al. (2017,2021). This criteria have been relaxed for the present work to estimate physical parameters.

- **-sed_rebuilt**: RMS source not in Elia et al. (2017, 2021), that needed a custom build of the *Herschel* SED to estimate physical parameters in the present work. Possible reasons: source had multiple counterparts in one *Herschel* band, or counterparts were not linked in a single SED.

- **-sed_sat**: RMS source not in Elia et al. (2017, 2021) due to saturation in some *Herschel* bands. To estimate physical parameters for the present work the SED has been manually built allowing missing bands.

- **-sed_noband**: RMS source not in Elia et al. (2017, 2021) because of missing 350-500$\mu$m*Herschel* bands due to source faintness. Physical parameters for the present work are estimated using three remaining bands

- **-no_props**: RMS source not in Elia et al. (2017, 2021) because has a *Herschel* counterpart in 1 or 2 bands only. It was not possible to estimate physical parameters.

# Plots for distance bias characterization and other supporting material

This section reports useful plots for the characterization of observational biases and to support the conclusions in the various relationships explored in this work. They are referenced where needed in the body of the paper.

![](emissionarea-vs-dist.pdf)

![](F350-vs-distance.pdf)

![image](emissionarea-vs-surfdens_tm1_nsig5_D-2000.pdf) ![image](emissionarea-vs-surfdens_tm1_nsig5_D-3000.pdf) ![image](emissionarea-vs-surfdens_tm1_nsig5_D-4000.pdf)

![image](emissionarea-vs-surfdens_tm1_nsig5_D-5000.pdf) ![image](emissionarea-vs-surfdens_tm1_nsig5_D-6000.pdf) ![image](emissionarea-vs-surfdens_tm1_nsig5_D-7000.pdf)

![](circ-depart_total_tm1_nsig5-vs-Dist.pdf)

![image](circ-depart_total_tm1_nsig5_D-2000.pdf) ![image](circ-depart_total_tm1_nsig5_D-3000.pdf) ![image](circ-depart_total_tm1_nsig5_D-4000.pdf)

![image](circ-depart_total_tm1_nsig5_D-5000.pdf) ![image](circ-depart_total_tm1_nsig5_D-6000.pdf) ![image](circ-depart_total_tm1_nsig5_D-7000.pdf)

![](emissionarea-vs-mass_tm1_nsig5.pdf)

[^1]: http://rms.leeds.ac.uk

[^2]: www.almagal.org

[^3]: For the ellipse we adopted an approximation for $k$ obtained from the approximation formula P$_{\rm ellipse}\sim \pi\sqrt{2(a^2+b^2)}$.

</paper>

Write the methods card for this paper.