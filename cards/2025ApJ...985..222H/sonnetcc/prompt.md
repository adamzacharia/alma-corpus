# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...985..222H\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...985..222H",
 "title": "The JCMT BISTRO-3 Survey: Variation of Magnetic Field Orientations on Parsec and Subparsec Scales in the Massive Star-forming Region G28.34+0.06",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Hwang, Jihye",
 "n_authors": 38,
 "arxiv_id": "2505.14047",
 "doi": "10.3847/1538-4357/adce80",
 "alma_projects_linked_by_archive": [
  "2016.1.00248.S",
  "2017.1.00793.S"
 ]
}
```

Paper text:
<paper>
# The JCMT BISTRO-3 Survey: Variation of magnetic field orientations on parsec and sub-parsec scales in the massive star-forming region G28.34$+$0.06

## Abstract

Magnetic fields play a significant role in star-forming processes on core to clump scales. We investigate magnetic field orientations and strengths in the massive star-forming clump P2 within the filamentary infrared dark cloud G28.34+0.06 using dust polarization observations made using SCUBA-2/POL-2 on the James Clerk Maxwell Telescope as part of the B-field In STar-forming Region Observations (BISTRO) survey. We compare the magnetic field orientations at the clump scale of $\sim$2 parsecs from these JCMT observations with those at the core scale of $\sim$0.2 parsecs from archival ALMA data, finding that the magnetic field orientations on these two different scales are perpendicular to one another. We estimate the distribution of magnetic field strengths, which range from 50 to 430 $\mu$G over the clump. The region forming the core shows the highest magnetic field strength. We also obtain the distribution of mass-to-flux ratios across the clump. In the region surrounding the core, the mass-to-flux ratio is larger than 1, which indicates the magnetic field strength is insufficient to support the region against gravitational collapse. Therefore, the change in the magnetic field orientation from clump to core scales may be the result of gravitational collapse, with the field being pulled inward along with the flow of material under gravity.

# Introduction

Magnetic fields play an important role in star formation and the evolution of the molecular cloud by either resisting gravitational collapse or channeling flows of gas and dust (e.g., (cite: Hwang2021; Hwang2022), (cite: Pattle2023), and references therein). Magnetic field lines observed in the plane of the sky show ordered structures on cloud scales ($\sim$10 pc), with fields tending to be perpendicular to high-density structures and parallel to low-density structures (e.g., (cite: Planck2016)). However, magnetic field orientations between parsec (pc) scale clumps and sub-pc scale cores are not as consistent as the large-scale fields seen in Planck observations, instead showing a bimodal distribution (e.g., (cite: Zhang2014)). It is known that the relative importance of magnetic fields, gravity, and turbulence can affect magnetic orientations and core fragmentation in clumps (e.g., (cite: Liu2018; Tang2019)). It is necessary to study magnetic fields on scales from clumps ($\sim$1 pc) to cores ($\sim$0.1 pc) in order to discern the role of magnetic fields in the overall star formation process (e.g., (cite: Koch2022)).

Magnetic fields in star-forming regions can be studied using polarized emission from dust grains aligned with respect to magnetic field lines by Radiative Alignment Torques (cite: Lazarian2007). Polarimeters on the James Clerk Maxwell Telescope (JCMT), Stratospheric Observatory for Infrared Astronomy (SOFIA), Submillimeter Array (SMA) and Atacama Large Millimeter/submillimeter Array (ALMA) have been widely used to study magnetic field properties in star-forming regions from clouds to cores (e.g., references in (cite: Pattle2023)). Several studies have shown the multi-scale magnetic field structures in star-forming regions (e.g., (cite: Zhang2014; Hull2017; Koch2018; Koch2022; Liu2024)). For example, magnetic field lines in a Class 0 protostellar source in Serpens have different directions on cloud and core scales (cite: Hull2017). Conversely, a consistent magnetic field orientation from core to clump scales is found in several star-forming regions (e.g, (cite: Tang2019; Liu2024)), which may imply that the magnetic field dominates over gravity and turbulence. To understand the role of the magnetic field in forming cores within a cloud or clump, we therefore need to examine multi-scale magnetic field properties.

Magnetic field strengths in molecular clouds are often estimated using the Davis-Chandrasekhar-Fermi (DCF) method (cite: Davis1951; ChanFer1953). An assumption in the method is that the underlying magnetic field is uniform, and variations are the result of distortion of the field by non-thermal gas motions. This distortion of magnetic field lines is estimated using polarization angle dispersion. However, magnetic fields may have underlying ordered variation as a result of gravitational infall, rotation, or other gas flows. In order to account for this curved magnetic field structure and estimate the angle dispersion due to non-thermal gas motions, (cite: Hwang2021) suggested a new method, extending the approach developed by (cite: Pattle2017). They calculated polarization angle dispersion in a box smaller than the radius of curvature of the magnetic field, in which the field lines can be assumed to be uniform. Using this moving box method, a map of the magnetic field strength can be obtained. The distribution of magnetic field strengths obtained using this method can help to better constrain the magnetic field strength inferred from dust polarization observations and thus to investigate the effect of magnetic fields on core formation within a cloud or clump.

G28.34$+$0.06 (hereafter G28) is an Infrared Dark Cloud (IRDC) located at 4.8 kpc (cite: Carey1998). IRDCs are thought to be in an early stage of the massive star formation process (cite: Wang2008). There are two clumps, P1 and P2, in the southern and northern parts of G28, respectively (as shown in Figure [1](#fig:polmag)) which have previously been identified in NH$_3$ intensity maps (cite: Wang2008). Recently, (cite: Liu2024) presented magnetic field orientations in G28 using JCMT and ALMA observations, showing that several cores have major axes aligned along the major axis of the P1 clump, while magnetic field lines are perpendicular to that axis. The magnetic field might regulate this aligned core fragmentation.

However, the P2 clump appears to show a different mode of core fragmentation than that in the P1 clump (cite: Liu2020). The core embedded in the P2 clump contains complex 15 dense condensations. (cite: Tang2019) suggested that core fragmentation types can be affected by the energy balance between gravity, turbulence, and the magnetic field. To investigate why the P2 and P1 clumps show different core fragmentation types, it is necessary to determine their energy balance. However, there are a few cases in which the role of the magnetic field in core fragmentation can be studied (e.g., (cite: Tang2019)). G28 is a good target to examine this role due to the two distinctive core fragmentation types in clumps P1 and P2. The P1 clump has already been studied, so we focus on the P2 clump in this work.

In this paper we present the results of polarized dust continuum and N$_2$H$^+$ observations of the P2 clump in G28 made using the JCMT as part of the B-field In STar-forming Region Observations (BISTRO) survey (cite: WardThompson2017) and the 14-m telescope at the Taeduk Radio Astronomy Observatory (TRAO) as a PI project, respectively. The N$_2$H$^+$ traces dense gas with a critical density of $\sim$ 10$^5$ (cite: Shirley2015), which is comparable to the density obtained by dust continuum. We used the velocity dispersion of N$_2$H$^+$ to estimate the magnetic field strength using the DCF method. We obtain magnetic field orientations and strengths in the P2 clump of G28 on $\sim$2 pc scales (at a distance of 4.8 kpc; (cite: Carey1998)), and compare these with those on $\sim$0.2 pc scales measured using ALMA in the P2 clump region, and examine the relative importance of magnetic fields, gravity, and turbulence in the P2 clump on multi-spatial scales.

This paper is organized as follows: in Section [2](#sec:obs), we describe the polarization and molecular line observations made using the JCMT and TRAO, and the archival ALMA data for G28. We present magnetic field orientations, strengths, and properties in the P2 clump in G28 in Section [3](#sec:Res). Measurements of mass-to-flux ratio and energy balance in the P2 clump are described in Section [4](#sec:Con). We summarize our results in Section [5](#sec:Sum).

# Observations and Data reduction

## JCMT Observations

We observed G28 in linearly polarized light, arising from dust continuum emission, using the POL-2 polarimeter mounted at the SCUBA-2 bolometer camera (cite: Holland2013) on the JCMT at 450 and 850 $\ensuremath{\mu}m$ simultaneously. In this work, we use the 850 $\ensuremath{\mu}m$ data only. The observations were conducted as part of the BISTRO Survey (Project ID : M20AL018). The 27 data sets were obtained between September 2020 and August 2022. The duration of each observation was 31-minutes. The effective beam size of the JCMT at 850 $\ensuremath{\mu}m$ is 14$''$.1 (cite: Dempsey2013). The observations were carried out in the JCMT Weather Band 2, in which the atmospheric opacity at 225 GHz ($\tau_{225 \mathrm{GHz}}$) is between 0.05 and 0.08. The observing mode was the POL-2 DAISY scan pattern, which produces a circular map with a diameter of 11$'$. The root mean square (rms) noise values are lower and uniform in the 3$'$-diameter central region of the map and increase towards the edge of the map. To improve the rms noise value, we further used 18 datasets obtained using the JCMT between February 2022 and June 2022 under the project code M22AP018 (PI: Junhao Liu, see (cite: Liu2024)). The data reduction procedures are explained in Appendix [6](#sec:datareduce).

The Stokes $I$, $Q$, and $U$ maps obtained are in units of pW with a 4$''$ pixel grid. The flux conversion factor at 850 $\ensuremath{\mu}m$ is 495 $\pm$ 32 Jy beam$^{-1}$ pW$^{-1}$ which is appropriate for data observed after June 30, 2018 (cite: Mairs2021). The POL-2 data are further corrected by an additional factor of 1.35 (which results in a final conversion factor of 668 Jy beam$^{-1}$ pW$^{-1}$), due to the reduced optical throughput caused by the introduction of the spinning POL-2 half-wave plate into the SCUBA-2 light path (cite: Mairs2021). This flux conversion factor is stable with time since 2018; although some scatter around the mean value may be seen in individual observations, our coadded set of 27 maps will be well-calibrated. The rms values of the Stokes $I$, $Q$, and $U$ maps are 7.6, 4.4, and 4.3 mJy beam$^{-1}$, respectively. We binned the polarization segments to a 12$''$ pixel grid using the $binsize$ parameter in the Starlink software; this pixel size is chosen for its similarity to the primary beam size of the JCMT at 850 $\ensuremath{\mu}m$. The polarization angle ($\theta_{obs}$), debiased polarization intensities ($PI$), debiased polarization fraction ($p$), and their uncertainties are obtained using the Stokes parameters,

$$\begin{eqnarray}
\theta_{obs} =1/2 \arctan(U/Q),\label{eq:pol}\\
\Delta{\theta_{obs}}=0.5\sqrt{(U\Delta Q)^2+(Q\Delta U)^2}/(Q^2+U^2), \label{eq:angerr}\\
PI=\sqrt{Q^2+U^2-\Delta{PI}^2},\\
\Delta{PI}=\sqrt{((Q\Delta Q)^2+(U\Delta 
 U)^2}/(Q^2+U^2) \\
p = (Q^2 + U^2 - 0.5[(\Delta Q)^2+(\Delta U)^2])^{1/2}/I,\\
\Delta p=\sqrt{\Delta{PI}^2/I^2 + (\Delta I^2(Q^2+U^2))/I^4},
\end{eqnarray}$$ where $\Delta Q^2$, $\Delta U^2$, $\Delta I^2$ and are the variances of Stokes $Q$, $U$, and $I$, respectively.

The polarization segments that we obtained, scaled by their debiased polarization fraction, are presented in the left panel of Figure [1](#fig:polmag). We selected polarization segments using the following criteria: $I$/$\Delta I \geq$ 10, $p$/$\Delta p \geq$ 3 and $p$ $<$ 20% (see Figure [1](#fig:polmag)). The maximum dust polarization fraction is 20% in *Planck* observations (cite: Planck2015).

## TRAO Observations

We carried out observations of N$_2$H$^+$ ($J$ = 1-0; 93.17631 GHz) spectral lines in G28 using the TRAO 14-m telescope located in Daejeon, Korea[^1]. The observations were conducted from January to February 2023. The data were obtained using the on-the-fly (OTF) mapping mode of the SEcond QUabbin Optical Image Array (SEQUOIA) receiver equipped with a 4$\times$4 monolithic microwave integrated-circuit (MMIC) preamplifier on the TRAO. Two IF modules in the observations allow us to simultaneously observe two sub-bands in a frequency range of 85 – 100 GHz or 100 – 115 GHz. Each spectrum has 4096 channels with a resolution of 15 kHz and a bandwidth of 62.5 MHz. The beam efficiency is 0.48 at 98 GHz (cite: Jeong2019).

The N$_2$H$^+$ ($J$ = 1-0) and HCO$^+$ ($J$ = 1-0) observations were made using two intermediate frequency (IF) modules whose center frequencies are 93.176 and 89.189 GHz, respectively. The TRAO beam sizes at these wavelengths are 54$''$ and 56$''$, respectively. Mapping observations were made over areas of 10$' \times$ 10$'$. The central position of the mapping area is Right Ascension (J2000) = 18$^{\mathrm{h}}$ 42$^{\mathrm{m}}$ 50.9$^{\mathrm{s}}$ and Declination (J2000) = –04$^{\mathrm{\circ}}$ 03$^{\mathrm{'}}$ 14$^{\mathrm{''}}$.

We performed four OTF scan observations over the same mapping area and added the scan data to get one averaged map. The integration time for each scan of size 10$' \times$ 10$'$ was about 100 minutes and thus about 6 hours 40 minutes in total were used for the full observations. The map was reconstructed with a pixel size of 22$''$ and a spectral resolution of 0.3 km s$^{-1}$. The rms of the N$_2$H$^+$ spectra varies from 0.02 to 0.03 K. Further analysis of the map data was performed using the Continuum and Line Analysis Single-dish Software (CLASS; (cite: Pety2005); (cite: gildasteam2013)).

## ALMA archive data

We used dust polarization observations of a core embedded in the P2 clump of the G28 obtained using ALMA in Band 6.

The receiver for the observations was tuned to cover $\sim$1.27–1.29 GHz, with a total bandwidth of 5.6 GHz in the full polarization mode.

The ALMA observations were made between April 2017 and June 2018 as part of the projects of 2016.1.00248.S (Cycle 4; PI: Qizhou Zhang) and 2017.1.00793.S (Cycle 5; PI: Qizhou Zhang). The data were presented by (cite: Liu2020) and reduced using the Common Astronomy Software Applications (CASA; (cite: McMullin2007)). The detailed data reduction processes are described by (cite: Liu2020). The synthesized beam sizes in the Stokes $I$, $Q$, and $U$ maps are 0$''$.8 $\times$ 0$''$.6 ($\sim$0.014 pc $\times$ 0.019 pc) and the maximum recoverable scale in the observation is $\sim$7$''$ ($\sim$0.16 pc). We produced polarization segments on 0.36 $''$ $\times$ 0.36 $''$ pixels, which is about half of the beam size. We calculated the polarization angles of the ALMA data using Equation ([\[eq:pol\]](#eq:pol)).

# Results

## Magnetic field orientations

The polarization segments from our JCMT/Pol2 observations are shown in the left panel of Figure [1](#fig:polmag). In the right panel, these segments are rotated by 90 degrees to show magnetic field orientations, with all segments scaled to the same length to better show the pattern of magnetic field orientations. Magnetic field lines are well-ordered within the P1 and P2 clumps in a fashion roughly perpendicular to the major axis of each elongated clump. The blue segments represent the *Planck* large-scale magnetic field orientations at 350 GHz ($\sim$857 $\ensuremath{\mu}m$). The beam size for the *Planck* observations is 5$'$ ($\sim$7 pc at the distance of G28), which covers the overall region of G28. The large-scale magnetic field orientation is directed from North-East to South-West.

As the details of the magnetic field orientation from cloud to core scales in the P1 clump were discussed by (cite: Liu2024), in this work, we focus on the magnetic field orientation in the P2 clump.

The left panel of Figure [2](#fig:polmag2) shows a zoomed-in view of the magnetic field distribution in the P2 clump. The right panel of Figure [2](#fig:polmag2) shows the magnetic field distribution in the core embedded within the P2 clump; the area shown is marked with a yellow rectangle in the left panel. In both panels, pink segments show magnetic field distribution obtained using the JCMT, while cyan segments in the right panel indicate the magnetic field distribution obtained using ALMA, with selection criteria of $\mathrm{PI}/\sigma_{\mathrm{PI}}$ $>$ 3, where $\mathrm{PI}$ and $\sigma_{\mathrm{PI}}$ are the polarized intensity and its uncertainty. The field orientations on JCMT and ALMA scales are roughly perpendicular to one another. Figure [3](#fig:polmag3) is a polar chart showing the distribution of magnetic field orientations.

Due to the 180-degree ambiguity on the direction of polarization segments, diametrically opposite angles on the plot agree. The *Planck* magnetic field orientation is shown in blue. The mean values of the JCMT (magenta histogram) and ALMA (cyan histogram) magnetic field directions are 24 and 117 degrees, with standard deviations of 19 and 32 degrees, respectively, indicating that the two magnetic field orientations are roughly perpendicular to one another with a mean angle difference of 87 degrees.

## Polarization angle dispersion

We obtained a map of polarization angle dispersion ($\sigma_\theta$) using the method introduced by (cite: Hwang2021), in which the mean magnetic field orientations are determined within a small box region. To decide the box size, we estimated a radius of curvature for a circle on which two adjacent segments become tangents (cite: Koch2012). We estimated the radii of curvature of four polarization segment pairs between a reference pixel and adjacent left, right, upper, and lower neighbors. We took the mean of these four radii of curvature as the radius of curvature for the polarization segment in the reference pixel. By repeating these calculations, we obtained radii of curvature for all pixels within the P2 clump. The derived radii of curvatures are larger than 36$''$, and thus we assume that the mean magnetic field orientation in a box of 36$''$ $\times$ 36$''$ (3 $\times$ 3 pixels) is uniform. In this way, we measured the mean polarization angle and angle dispersion within the box and then moved the box pixel by pixel to estimate the distribution of polarization angle dispersion (Figure [4](#fig:poldisp)) across the clump. The polarization angle dispersion in the P2 clump within the red contour marked in Figure [4](#fig:poldisp) varies from 3 to 20 degrees, with a mean value of 11 $\pm$ 4 degrees. The red contour marks the boundary of the P2 clump, which we identified using a dendrogram algorithm. For this, we used the Python package $astrodendro$[^2], which is used to recognize hierarchical structures in molecular clouds (cite: Rosolowsky2008). The uncertainties in each pixel are estimated from the measurement errors on the polarization segments (Equation ([\[eq:angerr\]](#eq:angerr))) in each box centered on the pixel.

## Volume density

To estimate the column density, and thus the volume density of the P2 clump we considered the area within the boundary of the P2 clump as defined in the previous section.

The column density of molecular hydrogen is calculated using the following equation, $$\begin{equation}
N(\text{H}_2) =I_\nu/ (\mu  m_{\text{H}}  \kappa(\nu) B_\nu(T)), 
\label{eq:col}
\end{equation}$$ where $I_\nu$ is the intensity at a frequency $\nu$, $\mu$ = 2.8 is the mean molecular weight per particle, assuming 10% of the total number of gas particles is helium (cite: Kauffmann2008), $m_\mathrm{H}$ is the mass of atomic hydrogen, $\kappa(\nu)=\kappa_{\nu_0}(\nu/\nu_0)^\beta$ is the dust opacity function where $\kappa_{\nu_0}$ is 0.1 cm$^2$ g$^{-1}$ at $\nu_0 = 1$ THz, taking the dust emissivity index $\beta$ to be 2 and assuming a dust-to-gas mass ratio of 1:100 (cite: Motte2001; Andre2010), and $B_\nu(T)$ is the Planck function at dust temperature $T$. We assumed that the dust temperature is similar to the rotation temperature of 29 K obtained using NH$_3$ ($J$, $K$) = (1,1) and (2,2) observations in the P2 clump (cite: Wang2008). This value is comparable to dust temperatures of 19-50 K derived using the ratio of intensities at 450 and 850 $\ensuremath{\mu}m$ in the clump and $\beta$ = 1.5-2.0 (cite: Carey2000). We estimated H$_2$ column densities in each pixel within G28 using 850 $\ensuremath{\mu}m$ intensity (Figure [5](#fig:col)). The mean value that we obtain is 3.0 $\times$ 10$^{22}$ cm$^{-2}$ which is comparable to the value estimated by (cite: Carey2000), 5.7 $\times$ 10$^{22}$ cm$^{-2}$ within a factor of $\sim 2$. We also compared our results with column density maps of G28 obtained using the point process mapping (PPMAP) tool and Spectral Energy Distribution (SED) fitting by (cite: Marsh2017) and (cite: Lin2017). Their mean column density values in the P2 clump are 11.0 $\times$ 10$^{22}$ cm$^{-2}$ and 4.7 $\times$ 10$^{22}$ cm$^{-2}$, respectively, which are consistent within a factor of a few with our value.

To estimate the volume density from the column density of the P2 clump, we took its depth to be the equivalent radius of the P2 clump, which is the radius of a circle with an area equal to that enclosed by the red contour defining the clump (Figure [4](#fig:poldisp)). The estimated radius was $\sim$1 pc. By dividing our column densities by this radius, we obtained volume densities of molecular hydrogen in each pixel, $$\begin{equation}
n(\text{H}_2)=N(\text{H}_2)/R,    
\end{equation}$$ where $R$ is the equivalent radius of the P2 clump. Volume densities in the clump range between (2.9 – 58.1) $\times$ 10$^3$ cm$^{-3}$, with a mean value of 1.0 $\times$ 10$^4$ cm$^{-3}$. We note that we have assumed that P2 clump is an oblate structure. If we instead took the depth to be 2$R$, the diameter of the equivalent-area circle described above, the volume density and magnetic field strength will decrease by a factor 2 and 1.4, respectively.

## Velocity dispersion

We used N$_2$H$^+$ ($J$=1–0) spectral line data to estimate non-thermal velocity dispersion values for the DCF method. The N$_2$H$^+$ line traces dense regions, due to its high critical density of 1.5 $\times$ 10$^5$ cm$^{-3}$, and its low degree of depletion in cold dense gas (e.g., (cite: Bergin1997; Caselli2002)). Due to these properties, it is one of the best tracers with which to measure non-thermal velocity dispersion within the P2 clump. The N$_2$H$^+$ ($J$ = 1–0) spectral feature have seven hyperfine structures (HFSs). However, six of these HFSs are found to be blended in G28 due of their large line widths (right panel of Figure [6](#fig:veldisp)). The observed N$_2$H$^+$ spectra show three Gaussian components. The two components in the center of the spectrum and at higher velocity each contain three hyperfine lines. Only the leftmost, low-velocity, component has one hyperfine line.

Figure [6](#fig:veldisp) shows a map of the non-thermal velocity dispersion obtained using the TRAO N$_2$H$^+$ observations. The beam size of the TRAO is 54$''$. However, the velocity dispersion map on a grid of 22$''$ as the spectra were observed on that grid. We fit each N$_2$H$^+$ spectrum with a hyperfine line model using the Python package of *pyspeckit* (an example is shown in the right panel of Figure [6](#fig:veldisp)). We estimated the velocity dispersion from the hyperfine structure fitting.

The non-thermal component $\sigma_{v_\mathrm{nth}}$of the velocity dispersion was estimated by subtracting the thermal component, $$\begin{equation}
\sigma_{v_\mathrm{nth}} =\sqrt{ \sigma_{v_{\text{obs}}}^2 - \frac{ k T_k}{m_{\text{N}_2\text{H}^+}}},
\label{eq:vel}
\end{equation}$$ where $\sigma_{v_{\text{obs}}}$ is the velocity dispersion obtained from the fit of the observed N$_2$H$^+$ spectral line, $T_k$ is the kinetic temperature which is taken here to be the rotational temperature of NH$_3$ spectral line, 29 K, and $m_{\text{N}_2\text{H}^+}$ is the mass of the N$_2$H$^+$ molecule. The velocity dispersion of the non-thermal gas component ranges from 1.29 to 1.48 km s$^{-1}$ in G28 with a mean value of 1.40 $\pm$ 0.03 km s$^{-1}$. The uncertainties are the propagation of the errors on the hyperfine structure fitting.

Since the beam size of the TRAO is four times larger than that of the JCMT, the velocity dispersion could be overestimated. However, the non-thermal velocity dispersion determined from NH$_3$ observations made using the Very Large Array (VLA) with a beam size of 3$''$ $\times$ 5$''$ is about 1.8 km s$^{-1}$ in the P2 clump, which is comparable to our results (cite: Wang2008). Therefore, it seems likely that the large beam of the TRAO does not affect the line broadening, so we used the non-thermal velocity dispersion obtained by the TRAO data.

## Magnetic field strengths

Plane-of-sky magnetic field strengths are typically inferred from dust polarization observations using the DCF method, in which we assume the magnetic field lines to be distorted by non-thermal gas motions. We used the polarization angle dispersion, the volume density and the non-thermal gas velocity dispersion to infer a map of the plane-of-sky magnetic field strength using the following simple formulation of the DCF method (cite: Crutcher2004), $$\begin{equation}
B_{\text{pos}} = Q\sqrt{4\pi\rho}  \frac{\sigma_{v_\mathrm{nth}}}{\sigma_\theta} \approx 9.3\sqrt{n(\text{H}_2)}\frac{\Delta V}{\sigma_\theta},
\label{eq:cf}
\end{equation}$$ where $B_{\text{pos}}$ is the magnetic field strength in the plane of the sky in $\mu$G, $Q$ is a correction factor which is taken to be 0.5 following (cite: Ostriker2001), $\rho$ = $\mu m_\mathrm{H} n(\mathrm{H}_2)$ is the mass density, $\sigma_{v_\mathrm{nth}}$ is the non-thermal velocity dispersion, $\sigma_\theta$ is the polarization angle dispersion, $n(\text{H}_2)$ is the number density of molecular hydrogen in units of cm$^{-3}$, and $\Delta V = \sqrt{8 \ln 2}\sigma_v$ is the full width at half maximum (FWHM) of the non-thermal line width in units of km s$^{-1}$. We note that $Q$ = 0.5 is estimated in a cloud with $n(\mathrm{H}_2) = 100$ cm$^{-3}$ and for a length ($l$) of 8 pc. In the case of the P2 clump, the volume density and length are 10$^4$ cm$^{-3}$ and 1 pc, respectively. (cite: Liu2022) has suggested a $Q$ value of 0.28 in a cloud with $n(\mathrm{H}_2) = 10^4-10^5$ cm$^{-3}$ and $l = 0.1-1$ pc using numerical simulations. If we use this $Q$ value, the estimated magnetic field strength will decrease by a factor of $\sim$2.

We obtained the map of plane-of-sky magnetic field strengths using the maps of polarization angle dispersion, volume density, and velocity dispersion. We re-grid the map to have the same coordinates as the polarization angle dispersion map with the pixel size of 12 $''$. We then substituted these values into the equation [\[eq:cf\]](#eq:cf). Figure [7](#fig:mag) shows the distribution of plane-of-sky magnetic field strengths in the P2 clump obtained using this method, which varies from 96 to 772 $\mu$G with a mean value of 330 $\pm$ 115 $\mu$G. If we use a $Q$ value of 0.28, the magnetic field strength will vary from 54 to 432 $\mu$G with a mean value of 185 $\pm$ 65 $\mu$G. We will use the magnetic field strengths determined using $Q$ = 0.28 in our analysis in the upcoming sections.

We further note that the DCF method gives us the plane-of-sky component of the magnetic field strength only. Statistically, $B_{\text{pos}}$ = ($\pi$/4)$B$ (cite: Crutcher2004). However, this correction is only valid over an ensemble of measurements, and so we do not apply it to our value of $B_{\text{pos}}$. However, we also note that this indicates that the correction from $B_{\text{pos}}$ to $B$ is typically small ($B = 1.27 B_{\text{pos}}$), and should not alter the conclusions of our work.

We note that the DCF method is subject to significant statistical and systematic uncertainties (e.g. (cite: Pattle2023)). Our error bars should be understood as an expression of the statistical uncertainty on the result arising from the velocity and angular dispersions, rather than as 1-sigma error bars, since there are significant systematic uncertainties on both gas density and on $Q$. Recent reviews and meta-analyses of DCF measurements (e.g. (cite: Liu2021; Pattle2023)) suggest that the DCF method produces magnetic field strength values that are correct to within a factor of a few. This is sufficient to inform our energetics analysis and discussion, below.

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| $\sigma_\theta$ | $\sigma_{v_\mathrm{nth}}$ | N$_{\mathrm{H}_2}$ | $n_{\mathrm{H}_2}$ | $B_\mathrm{pos}$ | $\mu_\Phi$ |
|  | \[km s$^{-1}$\] | \[10$^{22}$ cm$^{-2}$\] | \[10$^4$ cm$^{-3}$\] | \[$\mu$G\] |  |
| 11 $\pm$ 4 | 1.40 $\pm$ 0.03 | 3.5 | 1.0 | 185 $\pm$ 65 | 1.5 $\pm$ 0.5 |

: Parameters used for estimating magnetic field strength and mass-to-flux ratio

Table notes: These values are averaged in the P2 clump, bounded by the red contour marked on Figure [2](#fig:polmag2). We were unable to determine quantitative uncertainties of the column density and number densities of molecular hydrogen due to the uncertainties on the flux loss, dust opacity, and depth of the P2 clump. The magnetic field strength was obtained using the DCF method with $Q$ = 0.28.

# Discussions

## Mass-to-flux ratio

Mass-to-magnetic flux ratios ($\mu_\Phi$) have been used in previous studies to determine whether magnetic fields can support a star-forming region against gravitational collapse (cite: Mouschovias1976; Crutcher2004). The observed mass-to-flux ratio is scaled with a critical value, usually taken to be the value of a magnetized disk, $1/2\pi G^{1/2}$ where $G$ is the gravitational constant (cite: Nakano1978). The mass-to-flux ratio in units of the critical value (cite: Crutcher2004) is

$$\begin{equation}
\mu_\Phi = 7.6 \times10^{-21} \frac{N(\text{H}_2)}{B},\label{eq:mass_flux_ratio}      
\end{equation}$$

where $B$ is the three-dimensional (3D) magnetic field strength in units of $\mu$G. A value of $\mu_\Phi$ less than one implies that a star-forming region is magnetically subcritical, in which state the magnetic field is sufficiently strong to resist gravitational collapse. A value of $\mu_\Phi$ larger than one means that a star-forming region is magnetically supercritical, in which state the magnetic field cannot prevent gravitational collapse.

Figure [8](#fig:mtob) shows the distribution of mass-to-flux ratio in units of the critical value, as derived from our JCMT observations. When calculating the mass-to-flux ratio, we used the magnetic field strengths in the plane of the sky obtained as described in Section [3.5](#sec:mag) rather than the 3D magnetic field strengths. Therefore, the estimated mass-to-flux ratios may be upper limits. The derived mass-to-flux ratios vary from 0.3 to 3.2, with a mean value of 1.5 $\pm$ 0.5. We calculated the mean mass-to-flux ratios within circular regions of increasing radius, centered on the peak intensity position in our 850 $\ensuremath{\mu}m$ Stokes $I$ map. The right panel of Figure [8](#fig:mtob) shows the estimated mean mass-to-flux ratios as a function of radius. We find that the mass-to-flux ratio decreases as the radius increases. The P2 clump is in a magnetically supercritical state over all of the radii that we consider, indicating that the magnetic field cannot support the clump against gravitational collapse. This supports the first possibility discussed in Section [4.3](#sec:sce), below: that the gravitational collapse of the P2 clump may result in the change of the magnetic field orientations from clump to core scales seen when comparing JCMT and ALMA observations. Despite our large uncertainties, we can have some confidence that G28 is magnetically supercritical. The DCF method is known to typically overestimate magnetic field strengths; statistically, this overestimation appears to be by a factor $\sim$3-5 (cite: Pattle2023), although the applicability of this factor to any individual measurement is unclear. Finding a supercritical mass-to-flux ratio using the DCF method despite its tendency to overestimate magnetic field strengths thus strongly suggests that G28 is indeed supercritical. Moreover, the G28 clump is demonstrably a site of active star formation, and so our finding of a supercritical mass-to-flux ratio is fully consistent with the star formation history of the region.

## Energy Balance

We estimate the kinetic ($E_{\rm K}$), gravitational ($E_{\rm G}$), and magnetic energies ($E_{\rm B}$) in the P2 clump using the relations, $$\begin{eqnarray}
    E_{\rm K}=\frac{3}{2}M\sigma_{v_{\text{tot}}}^2, \\
    E_{\rm G}=-\frac{3}{5}\frac{GM^2}{R}, \, \\
    E_{\rm B}=\frac{1}{2}Mv_A^2,
\end{eqnarray}$$

where $M$ is the mass of the P2 clump, $\sigma_{v_{\text{tot}}}$ is the total velocity dispersion estimated as $\sigma_{v_{\text{tot}}}=\sqrt{\sigma_{v_\mathrm{nth}}^2+\sigma_{v_\mathrm{th}}}$ where $\sigma_{v_\mathrm{th}}$ is the thermal velocity dispersion for free particle with the mean molecular weight, $\mu$=2.37, $G$ is the gravitational constant, $R$ is the equivalent radius of the P2 clump, and $v_A$ is the Alfvén velocity ($B/\sqrt{4\pi\rho}$, where $\rho$ = $\mu m_\mathrm{H} n(\mathrm{H}_2)$ is the mass density). The mass of the P2 clump is calculated using the formulation (cite: Hildebrand1983), $$\begin{equation}
M = \sum_{i=1}^N \frac{I_{850,i}A}{\kappa_{\nu} B_{\nu} (T)},
\end{equation}$$ where $N$ is the number of pixels within the red contour defining the area of the P2 clump (Figure [8](#fig:mtob)), $I_{850,i}$ is the 850 $\ensuremath{\mu}m$ flux density of $i$-th pixel, $A$ is the pixel area, and $\kappa(\nu)$ and $B_\nu(T)$ are as defined in equation ([\[eq:col\]](#eq:col)). We calculate a mass for the P2 clump of 2037 M$_\odot$. The mean velocity dispersion of 1.2 km s$^{-1}$ and the magnetic field strength of 185 $\mu$G in the P2 clump are used when calculating $E_{\rm K}$ and $E_{\rm B}$.

The estimated kinetic, gravitational, and magnetic energies of the P2 clump are 12 $\times$ 10$^{46}$, 21 $\times$ 10$^{46}$, and 6 $\times$ 10$^{46}$ erg, respectively. We emphasize that these values are order-of-magnitude estimates only, and are subject to significant systematic and statistical uncertainties (e.g. (cite: Pattle2017)), but their relative values can nonetheless inform our discussion of the region. The gravitational potential energy is the dominant term in the energy budget of the P2 clump. This result is consistent with our mass-to-flux ratio analysis. The kinetic energy is also comparable to the gravitational energy. However, we note that we used our estimated plane-of-sky magnetic field strength to calculate the magnetic energy. Considering 3D magnetic field vectors are randomly oriented, the 3D magnetic field strength can be a factor of 4/$\pi$ larger than the plane-of-sky magnetic field strength (cite: Crutcher2004).If we applied this correction to our value, the magnetic energy would become 9.8 $\times$ 10$^{46}$ erg, which is still smaller than gravitational energy. However, this is a statistical correction that may not be relevant to this region. Future Zeeman measurements of the magnetic field strength along the line of sight would allow us to determine the 3D magnetic field strengths in the region, and thus calculate more accurate magnetic energy values (e.g., (cite: Hwang2024)).

## Scenarios changing magnetic field orientations

We have shown that the magnetic field orientations on core and clump scales are roughly perpendicular to each other in the P2 clump (Figure [2](#fig:polmag2)). The JCMT and ALMA observations show the magnetic fields on different physical scales. The JCMT observations trace scales from $\sim$2 pc to 0.3 pc and the ALMA observations from $\sim$0.3 pc (the maximum recoverable scale of the ALMA observations of 13$''$) down to 0.02 pc. We can see that there is little to no overlap in size scales: the ALMA observations are probing the magnetic field within the beam of the JCMT. Therefore, we need observations on intermediate scales between those mapped by the JCMT and ALMA to find the size scale on which the transition between magnetic field orientations occurs.

We suggest two possible scenarios to explain the change in magnetic field orientations between the clump to the core in G28. In the first scenario, gravitational collapse could change the magnetic field orientations from the P2 clump to the core. In the ambipolar diffusion model, magnetic field lines are aligned along the minor axis of an initially magnetically subcritical clump or core (e.g, (cite: Mouschovias1999)). In this model, neutral particles in the clump or core decouple from the ions and fall in under gravity. Once the core becomes magnetically supercritical, the ions drag the magnetic field inwards, creating a characteristic "hourglass" geometry. In a theoretical hourglass model of a collapsing core, the mass-to-flux ratio changes from transcritical to supercritical as the density increases from the edge to the center (e.g., (cite: Bino2021)). While field lines are only slightly curved on the clump scale, the lines are highly curved on the core scale, where the densities are highest. Figure [8](#fig:mtob) shows that the mass-to-flux ratios we measure are similar to this prediction, transitioning from magnetically subcritical to supercritical from the outer diffuse to the inner dense regions of the P2 clump. We note that the fractional uncertainty on the mass-to-flux ratio is about 33%, and so the clump could be trans-, rather than super-critical, although as discussed about, there is reason to expect that the clump’s supercriticality may in fact be underestimated by our analysis. We would need Zeeman measurements to determine the 3D magnetic field and estimate a more accurate mass-to-flux ratio. The dense core is embedded in the densest part of the P2 clump, in which the magnetic field strength is the highest, but is magnetically supercritical and undergoing gravitational collapse (cite: Liu2020). The magnetic field lines are dragged toward the central core, and the field orientations are shifted by 90 degrees with respect to the large-scale field (Figure [9](#fig:view)). (cite: Liu2020) found that the magnetic field revealed by ALMA is preferentially aligned with the direction of gravity in the P2 clump, which further supports this scenario.

The second scenario posits that the observed magnetic field geometry is the effect of the outflow from the core. (cite: Liu2020) detected an outflow from the core embedded in the P2 clump using ALMA CO (2-1) line observations (see Figure [11](#fig:co) in Appendix [8](#sec:co)). The CO outflow is aligned along the northwest/southeast directions, with a wide opening angle. The IRS 2 source is located in the core observed by the ALMA (R.A. = 18$^h$ 42$^m$ 51.92$^s$, Dec. = -03$^\circ$ 59$'$ 54$''$). However, it cannot be confirmed that the outflow arises from the IRS 2 source due to the differences in their positions. Although the kinetic energy is significant in this region and an outflow is detected, it is hard to constrain the effect of the outflow on the magnetic field orientations. To do so, observing other outflow or dense core tracers would be necessary. We cannot rule out the second scenario, but gravitational collapse could be the primary cause of the observed magnetic field geometry based on the mass-to-flux ratios in G28 (Section [4.1](#sec:mtob)).

# Summary

We present observations of polarized 850 $\ensuremath{\mu}m$ dust emission performed using the JCMT as part of the JCMT BISTRO Survey, and N2H+ (1-0) line observations performed using the TRAO, of the massive star-forming region G28. We investigate the magnetic field orientations and strengths on clump scales in the P2 clump of G28 using the JCMT observations. We compare the magnetic field orientations with those seen on core scales using archival ALMA data. The magnetic field segments obtained using the JCMT and ALMA are oriented nearly perpendicular to one another in the central parts of the P2 clump. We obtain the distribution of magnetic field strengths using volume density, velocity dispersion, and polarization angle dispersion. Using the DCF method, we use these quantities to derive estimated magnetic field strengths which vary from 54 to 432 $\mu$G with a mean value of 185 $\pm$ 65 $\mu$G. The magnetic field is strongest in the center of G28, where a core detected by ALMA is embedded. We also estimated the mass-to-flux ratios to investigate the relative importance of magnetic fields and gravity. We find mass-to-flux ratios ranging from 0.3 to 3.2 with a mean value of 1.5 $\pm$ 0.5. The mass-to-flux ratio is larger than 1 in the central parts of the P2 clump, and decreases with increasing distance from the peak intensity position of the P2 clump. Overall, the clump is magnetically supercritical, which indicates the magnetic field is not large enough to resist gravitational collapse. We also estimate the kinetic, gravitational potential, and magnetic energies of 12 $\times$ 10$^{46}$, 21 $\times$ 10$^{46}$, and 6 $\times$ 10$^{46}$ erg in the P2 clump. The gravitational potential energy is the dominant energy term in the P2 clump. We interpret the perpendicular magnetic field orientations on clump and core scales as potentially resulting from the gravitational collapse of the P2 clump.

# Software

CLASS (cite: Pety2005; gildasteam2013), KAPPA (cite: Currie2008), Starlink (cite: Jenness2013)

# Facilities

JCMT

The JCMT is operated by the East Asian Observatory on behalf of The National Astronomical Observatory of Japan; Academia Sinica Institute of Astronomy and Astrophysics; the Korea Astronomy and Space Science Institute; the Operation, Maintenance and Upgrading Fund for Astronomical Telescopes and Facility Instruments, budgeted from the Ministry of Finance of China. Additional funding support is provided by the Science and Technology Facilities Council of the United Kingdom and participating universities and organizations in the United Kingdom, Canada and Ireland. Additional funds for the construction of SCUBA-2 were provided by the Canada Foundation for Innovation. The authors wish to recognize and acknowledge the very significant cultural role and reverence that the summit of Maunakea has always had within the indigenous Hawaiian community. We are most fortunate to have the opportunity to conduct observations from this mountain. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00248.S and ADS/JAO.ALMA#2017.1.00793.S. ALMA is a partnership of the ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. K.P. is a Royal Society University Research Fellow, supported by grant number URF\R1\211322. C.W.L. is supported by the Basic Science Research Program through the NRF funded by the Ministry of Education, Science and Technology (NRF- 2019R1A2C1010851) and by the Korea Astronomy and Space Science Institute grant funded by the Korea government (MSIT; project No. 2024-1-841-00). K. Q. acknowledges National Natural Science Foundation of China (NSFC) grant Nos. 12425304 and U1731237, and the National Key R&D Program of China with Nos. 2023YFA1608204 and 2022YFA1603103. F.P. acknowledges support from the Spanish Ministerio de Ciencia, Innovación y Universidades (MICINN) under grant numbers PID2022-141915NB-C21. D.J. is supported by NRC Canada and by an NSERC Discovery Grant. W.K. is supported by the National Research Foundation of Korea (NRF) grant funded by the Korea government (MSIT) (RS-2024-00342488). M.Tahani is supported by the Banting Fellowship (Natural Sciences and Engineering Research Council Canada) hosted at Stanford University and the Kavli Institute for Particle Astrophysics and Cosmology (KIPAC) Fellowship. J.K. is supported by the Royal Society under grant number RF\ERE\231132, as part of project URF\R1\211322. N.B.N. was funded by Vingroup Innovation Foundation (VINIF) under project code VINIF.2023.DA.057.T M.Tamura. is supported by JSPS KAKENHI grant No.24H00242. J.K. is supported by JSPS KAKENHI grant No.24K07086. E.C. acknowledges the financial support from grant RJF/2020/000071 as a part of the Ramanujan Fellowship awarded by the Science and Engineering Research Board (SERB), Department of Science and Technology (DST), Govt. of India. T.L. acknowledges the supports by the National Key R&D Program of China (No. 2022YFA1603100), National Natural Science Foundation of China (NSFC) through grants No.12073061 and No.12122307, and the Tianchi Talent Program of Xinjiang Uygur Autonomous Region. S.-P.L. acknowledges the grants from the National Science and Technology Council of Taiwan under project numbers 112-2112-M-007-011 and 113-2112-M-007-004. R.S.F. was supported by the Visiting Scholars Program provided by the NAOJ Research Coordination Committee, NINS (NAOJ-RCC-23DS-050).

# Data reduction procedures

The raw data were reduced using the Submillimetre User Reduction Facility (SMURF) package (cite: Chapin2013) from the Starlink software suite (cite: Currie2014). The $pol2map$[^3] command is run twice to reduce the POL-2 data. In the first run of $pol2map$, raw bolometer timestreams for each observation are converted into separate Stokes $I$, $Q$, and $U$ timestreams. In this process, the SMURF routine $makemap$ (cite: Chapin2013) produces individual Stokes $I$ maps from the Stokes $I$ timestreams and then coadds those maps to form an initial Stokes $I$ map. The initial Stokes $I$ maps are used to make masks defining areas of astrophysical emission. The second run of $pol2map$ creates final Stokes $I$, $Q$, and $U$ maps, and a polarization segment catalog. In this second run, we used the $skyloop$ and $mapvar$ parameters in $pol2map$. The $skyloop$ parameter improves the signal-to-noise ratio and image fidelity by reducing all 45 observations concurrently. The $mapvar$ parameter calculates the variances of the Stokes $I$, $Q$, and $U$ maps from the spread of pixel data values between the individual observations. We used the August 2019 instrumental polarization model to correct the Stokes $Q$ and $U$ maps.

# N$_2$H$^+$

Figure [10](#fig:moments) shows maps of integrated intensity and centroid velocity of N$_2$H$^+$ obtained by the TRAO observations. We integrated N$_2$H$^+$ data from 60 to 110 km s$^{-1}$. The centroid velocity is determined from the Gaussian fit value of the isolated component (Section [3.4](#sec:veldisp)).

# CO outflow

Figure [11](#fig:co) shows the blueshifted and redshifted CO outflows obtained by the ALMA observations (cite: Liu2020). Magnetic field orientations are overlapped in the figure. The yellow star in the figure is the location of IRS 2 source. It is hard to constrain outflow direction from the IRS 2 source.

(ref: Andre2010) André, P., Men’shchikov, A., Bontemps, S., et al. 2010, A&A, 518, L102

(ref: Bergin1997) Bergin, E. A. & Langer, W. D. 1997, ApJ, 486, 316. doi:10.1086/304510

(ref: Bino2021) Bino, G. & Basu, S. 2021, ApJ, 911, 15. doi:10.3847/1538-4357/abe6a4

(ref: Carey1998) Carey, S. J., Clark, F. O., Egan, M. P., et al. 1998, ApJ, 508, 721. doi:10.1086/306438

(ref: Carey2000) Carey, S. J., Feldman, P. A., Redman, R. O., et al. 2000, ApJL, 543, L157. doi:10.1086/317270

(ref: Caselli2002) Caselli, P., Walmsley, C. M., Zucconi, A., et al. 2002, ApJ, 565, 344. doi:10.1086/324302

(ref: ChanFer1953) Chandrasekhar, S., & Fermi, E. 1953, ApJ, 118, 113

(ref: Chapin2013) Chapin, E. L., Berry, D. S., Gibb, A. G., et al. 2013, MNRAS, 430, 2545. doi:10.1093/mnras/stt052

(ref: Crutcher2004) Crutcher, R. M. 2004, Ap&SS, 292, 225. doi:10.1023/B:ASTR.0000045021.42255.95

(ref: Currie2008) Currie, M. J., Draper, P. W., Berry, D. S., et al. 2008, Astronomical Data Analysis Software and Systems XVII, 394, 650

(ref: Crutcher2009) Crutcher, R. M., Wandelt, B., Heiles, C., et al. 2010, ApJ, 725, 466. doi:10.1088/0004-637X/725/1/466

(ref: Currie2014) Currie, M. J., Berry, D. S., Jenness, T., et al. 2014, Astronomical Data Analysis Software and Systems XXIII, 485, 391

(ref: Davis1951) Davis, L. 1951, Physical Review, 81, 890

(ref: Dempsey2013) Dempsey, J. T., Friberg, P., Jenness, T., et al. 2013, MNRAS, 430, 2534

(ref: gildasteam2013) Gildas Team 2013, Astrophysics Source Code Library. ascl:1305.010

(ref: Hildebrand1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: Holland2013) Holland, W. S., Bintley, D., Chapin, E. L., et al. 2013, MNRAS, 430, 2513. doi:10.1093/mnras/sts612

(ref: Hull2017) Hull, C. L. H., Girart, J. M., Tychoniec, Ł., et al. 2017, ApJ, 847, 92. doi:10.3847/1538-4357/aa7fe9

(ref: Hwang2021) Hwang, J., Kim, J., Pattle, K., et al. 2021, ApJ, 913, 85. doi:10.3847/1538-4357/abf3c4 (ref: Hwang2022) Hwang, J., Kim, J., Pattle, K., et al. 2022, ApJ, 941, 51. doi:10.3847/1538-4357/ac99e0 (ref: Hwang2024) Hwang, J., Lee, C. W., Kim, J., et al. 2024, arXiv:2408.10506. doi:10.48550/arXiv.2408.10506

(ref: Jenness2013) Jenness, T., Chapin, E. L., Berry, D. S., et al. 2013, Astrophysics Source Code Library, ascl:1310.007

(ref: Jeong2019) Jeong, I.-G., Kang, H., Jung, J., et al. 2019, Journal of Korean Astronomical Society, 52, 227

(ref: Kauffmann2008) Kauffmann, J., Bertoldi, F., Bourke, T. L., et al. 2008, A&A, 487, 993

(ref: Koch2012) Koch, P. M., Tang, Y.-W., & Ho, P. T. P. 2012, ApJ, 747, 79

(ref: Koch2018) Koch, P. M., Tang, Y.-W., Ho, P. T. P., et al. 2018, ApJ, 855, 39. doi:10.3847/1538-4357/aaa4c1

(ref: Koch2022) Koch, P. M., Tang, Y.-W., Ho, P. T. P., et al. 2022, ApJ, 940, 89. doi:10.3847/1538-4357/ac96e3

(ref: Kumar2020) Kumar, M. S. N., Palmeirim, P., Arzoumanian, D., et al. 2020, A&A, 642, A87. doi:10.1051/0004-6361/202038232

(ref: Lazarian2007) Lazarian, A. & Hoang, T. 2007, MNRAS, 378, 910

(ref: Lin2017) Lin, Y., Liu, H. B., Dale, J. E., et al. 2017, ApJ, 840, 22. doi:10.3847/1538-4357/aa6c67

(ref: Liu2020) Liu, J., Zhang, Q., Qiu, K., et al. 2020, ApJ, 895, 142. doi:10.3847/1538-4357/ab9087

(ref: Liu2021) Liu, J., Zhang, Q., Commerçon, B., et al. 2021, ApJ, 919, 2, 79. doi:10.3847/1538-4357/ac0cec

(ref: Liu2022) Liu, J., Zhang, Q., & Qiu, K. 2022, Frontiers in Astronomy and Space Sciences, 9, 943556. doi:10.3389/fspas.2022.943556

(ref: Liu2024) Liu, J., Zhang, Q., Lin, Y., et al. 2024, ApJ, 966, 120. doi:10.3847/1538-4357/ad3105

(ref: Liu2018) Liu, T., Li, P. S., Juvela, M., et al. 2018, ApJ, 859, 151. doi:10.3847/1538-4357/aac025

(ref: Mairs2021) Mairs, S., Dempsey, J. T., Bell, G. S., et al. 2021, AJ, 162, 191. doi:10.3847/1538-3881/ac18bf

(ref: Marsh2017) Marsh, K. A., Whitworth, A. P., Lomax, O., et al. 2017, MNRAS, 471, 2730. doi:10.1093/mnras/stx1723

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., et al. 2007, Astronomical Data Analysis Software and Systems XVI, 376, 127

(ref: Motte2001) Motte, F., & André, P. 2001, A&A, 365, 440

(ref: Mouschovias1976) Mouschovias, T. C., & Spitzer, L. 1976, ApJ, 210, 326

(ref: Mouschovias1999) Mouschovias, T. C. & Ciolek, G. E. 1999, The Origin of Stars and Planetary Systems, 540, 305

(ref: Myers2009) Myers, P. C. 2009, ApJ, 706, 1341. doi:10.1088/0004-637X/706/2/1341

(ref: Nakano1978) Nakano, T. & Nakamura, T. 1978, PASJ, 30, 671

(ref: Ostriker2001) Ostriker, E. C., Stone, J. M., & Gammie, C. F. 2001, ApJ, 546, 980

(ref: Palmeirim2013) Palmeirim, P., André, P., Kirk, J., et al. 2013, A&A, 550, A38. doi:10.1051/0004-6361/201220500

(ref: Pattle2023) Pattle, K., Fissel, L., Tahani, M., et al. 2023, Protostars and Planets VII, 534, 193. doi:10.48550/arXiv.2203.11179

(ref: Pety2005) Pety, J. 2005, SF2A-2005: Semaine de l’Astrophysique Francaise, 721

(ref: Pillai2016) Pillai, T., Kauffmann, J., Wiesemeyer, H., & Menten, K. M. 2016, A&A, 591, A19

(ref: Pattle2017) Pattle, K., Ward-Thompson, D., Berry, D., et al. 2017, ApJ, 846, 122. doi:10.3847/1538-4357/aa80e5

(ref: Planck2015) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2015, A&A, 576, A104. doi:10.1051/0004-6361/201424082

(ref: Planck2016) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 586, A138. doi:10.1051/0004-6361/201525896.

(ref: Rosolowsky2008) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., et al. 2008, ApJ, 679, 1338. doi:10.1086/587685

(ref: Roy2014) Roy, A., André, P., Palmeirim, P., et al. 2014, A&A, 562, A138

(ref: Shirley2015) Shirley, Y. L. 2015, PASP, The Critical Density and the Effective Excitation Density of Commonly Observed Molecular Dense Gas Tracers, 127, 949, 299. doi:10.1086/680342

(ref: Tang2019) Tang, Y.-W., Koch, P. M., Peretto, N., et al. 2019, ApJ, 878, 10. doi:10.3847/1538-4357/ab1484

(ref: Wang2008) Wang, Y., Zhang, Q., Pillai, T., et al. 2008, ApJL, 672, L33. doi:10.1086/524949

(ref: WardThompson2017) Ward-Thompson, D., Pattle, K., Bastien, P., et al. 2017, ApJ, 842, 66

(ref: Zhang2014) Zhang, Q., Qiu, K., Girart, J. M., et al. 2014, ApJ, 792, 116. doi:10.1088/0004-637X/792/2/116

[^1]: <https://trao.kasi.re.kr>

[^2]: A minimum intensity level of 27 mJy beam$^{-1}$ (3 $\sigma_I$) and a minimum size of hierarchical structures of 14.1$''$ (the JCMT beam size) were used when applying the algorithm.

[^3]: <http://starlink.eao.hawaii.edu/docs/sun258.htx/sun258ss75.html>

</paper>

Write the methods card for this paper.