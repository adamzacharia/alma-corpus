# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...901...67W\sonnetcc\reply.txt

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
 "bibcode": "2020ApJ...901...67W",
 "title": "Monitoring the Morphology of M87* in 2009-2017 with the Event Horizon Telescope",
 "year": 2020,
 "journal": "The Astrophysical Journal",
 "first_author": "Wielgus, Maciek",
 "n_authors": 219,
 "arxiv_id": "2009.11842",
 "doi": "10.3847/1538-4357/abac0d",
 "alma_projects_linked_by_archive": [
  "2016.1.01154.V"
 ]
}
```

Paper text:
<paper>
# Monitoring the Morphology of M87$^{\ast}$ in 2009–2017 with the Event Horizon Telescope

## Abstract

The Event Horizon Telescope (EHT) has recently delivered the first resolved images of M87$^{\ast}$, the supermassive black hole in the center of the M87 galaxy. These images were produced using 230 GHz observations performed in 2017 April. Additional observations are required to investigate the persistence of the primary image feature – a ring with azimuthal brightness asymmetry – and to quantify the image variability on event horizon scales. To address this need, we analyze M87$^{\ast}$ data collected with prototype EHT arrays in 2009, 2011, 2012, and 2013. While these observations do not contain enough information to produce images, they are sufficient to constrain simple geometric models. We develop a modeling approach based on the framework utilized for the 2017 EHT data analysis and validate our procedures using synthetic data. Applying the same approach to the observational data sets, we find the M87$^{\ast}$ morphology in 2009–2017 to be consistent with a persistent asymmetric ring of ${\sim}40\,\mu$as diameter. The position angle of the peak intensity varies in time. In particular, we find a significant difference between the position angle measured in 2013 and 2017. These variations are in broad agreement with predictions of a subset of general relativistic magnetohydrodynamic simulations. We show that quantifying the variability across multiple observational epochs has the potential to constrain the physical properties of the source, such as the accretion state or the black hole spin.

# Introduction

The compact radio source in the center of the M87 galaxy, hereafter M87$^{\ast}$, has been observed at 1.3 millimeter wavelength (230 GHz frequency) using very long baseline interferometry (VLBI) since 2009. These observations, performed by early configurations of the Event Horizon Telescope (cite: Doeleman2009) array, measured the size of the compact emission to be $\sim\,40\,\mu$as, with large systematic uncertainties related to the limited baseline coverage (cite: Shep2012; Kazu2015). The addition of new sites and sensitivity improvements leading up to the April 2017 observations yielded the first resolved images of the source (cite: Paper1; Paper2; Paper3; Paper4; Paper5; Paper6). These images revealed an asymmetric ring (a crescent) with a diameter $d\,=\,42\pm3\,\mu$as and a position angle of the bright side $\phi_{\rm B}$ between $150^\circ$ and $200^\circ$ east of north , see the left panel of [1](#fig:images_intro). The apparent size and appearance of the observed ring agree with theoretical expectations for a $6.5 \times 10^9 M_\odot$ black hole driving a magnetized accretion inflow/outflow system, inefficiently radiating via synchrotron emission . Trajectories of the emitted photons are subject to strong deflection in the vicinity of the event horizon, resulting in a lensed ring-like feature seen by a distant observer – the anticipated shadow of a black hole (cite: Bardeen1973; Luminet1979; Falcke2000; Broderick2009).

General relativistic magnetohydrodynamic (GRMHD) simulations of relativistic plasma in the accretion flow and jet-launching region close to the black hole predict that the M87$^{\ast}$ source structure will exhibit a prominent asymmetric ring throughout multiple years of observations, with a mean diameter $d$ primarily determined by the black hole mass-to-distance ratio and a position angle $\phi_{\rm B}$ primarily determined by the orientation of the black hole spin axis. The detailed appearance of M87$^{\ast}$ may also be influenced by many poorly constrained effects, such as the black hole spin magnitude, magnetic field structure in the accretion flow , the electron heating mechanism (cite: Moscibrodzka2016; ChaelRowan2018), nonthermal electrons (cite: Jordy2019), and misalignment between the jet and the black hole spin (cite: White2020; Chatterjee2020). Moreover, turbulence in the accretion flow, perhaps driven by the magnetorotational instability (cite: MRI), is expected to cause stochastic variability in the image with correlation timescales of up to a few weeks ($\sim$ dynamical time for M87$^{\ast}$). The model uncertainties and expected time-dependent variability of these theoretical predictions strongly motivate the need for additional observations of M87$^{\ast}$, especially on timescales long enough to yield uncorrelated snapshots of the turbulent flow.

![](fig1_introB.pdf)

To this end, we analyze archival EHT observations of M87$^{\ast}$ from observing campaigns in 2009, 2011, 2012, and 2013. While these observations do not have enough baseline coverage to form images , they are sufficient to constrain simple geometrical models, following procedures similar to those presented in . We employ asymmetric ring models that are motivated by both results obtained with the mature 2017 array and the expectation from GRMHD simulations that the ring feature is persistent.

We begin, in [2](#sec:observations), by summarizing the details of these archival observations with the “proto-EHT” arrays. In [3](#sec:modeling), we describe our procedure for fitting simple geometrical models to these observations. In [4](#sec:synthetic), we test this procedure using synthetic proto-EHT observations of GRMHD snapshots and of the EHT images of M87$^{\ast}$. We then use the same procedure to fit models to the archival observations of M87$^{\ast}$ in [5](#sec:ModelingRealData). We discuss the implications of these results for our theoretical understanding of M87$^{\ast}$ in [6](#sec:discussion), and briefly summarize our findings in [7](#sec:summary).

# Observations and data

+:-----:+:--------------------------:+:-----------------------:+:--------------------:+:------------------:+:----------------:+:------------------:+:------------------:+:------------------:+:---:+
|       |                            |                         |                      | Detections on Nonredundant Baselines                                                                 |     |
+-------+----------------------------+-------------------------+----------------------+--------------------+------------------+--------------------+--------------------+--------------------+-----+
| Year  | Telescopes                 | Dates                   | Baselines$^\text{a}$ | Zero               | Short            | Medium$^\text{b}$  | Long$^\text{c}$    | Total              | CPs |
+-------+----------------------------+-------------------------+----------------------+--------------------+------------------+--------------------+--------------------+--------------------+-----+
|       |                            |                         |                      | $<\!0.1$G$\lambda$ | $<\!1$G$\lambda$ | $<\!3.6$G$\lambda$ | $>\!3.6$G$\lambda$ | $>\!0.1$G$\lambda$ |     |
+-------+----------------------------+-------------------------+----------------------+--------------------+------------------+--------------------+--------------------+--------------------+-----+
| 2009  | CA, AZ, JC                 | Apr 5, 6                | 3/3/3                | —                  | 12               | 16/5               | —                  | 28                 | —   |
+-------+----------------------------+-------------------------+----------------------+--------------------+------------------+--------------------+--------------------+--------------------+-----+
| 2011  | CA, AZ, JC, SM, CS         | Mar 29, 31; Apr 1, 2, 4 | 10/6/3               | 52                 | 33               | 21/6               | —                  | 54                 | —   |
+-------+----------------------------+-------------------------+----------------------+--------------------+------------------+--------------------+--------------------+--------------------+-----+
| 2012  | CA, AZ, SM                 | Mar 21                  | 3/3/3                | 14                 | 11               | 19/6               | —                  | 44                 | 7   |
+-------+----------------------------+-------------------------+----------------------+--------------------+------------------+--------------------+--------------------+--------------------+-----+
| 2013  | CA, AZ, SM, JC, AP         | Mar 21 – 23, Mar 26     | 10/7/5               | 39                 | 41               | 23/4               | 19/1               | 83                 | —   |
+-------+----------------------------+-------------------------+----------------------+--------------------+------------------+--------------------+--------------------+--------------------+-----+
| 2017  | AZ, SM, JC, AP, LM, PV, AA | Apr 6$^\text{d}$        | 21/21/10             | 24                 | —                | 33/13              | 92/16              | 125                | 67  |
+-------+----------------------------+-------------------------+----------------------+--------------------+------------------+--------------------+--------------------+--------------------+-----+
| 2017  | AZ, SM, JC, AP, LM, PV, AA | Apr 11$^\text{d}$       | 21/21/10             | 22                 | —                | 28/9               | 72/16              | 100                | 54  |
+-------+----------------------------+-------------------------+----------------------+--------------------+------------------+--------------------+--------------------+--------------------+-----+

$^\text{a}$ theoretically available / with detections / nonredundant, nonzero with detections, $^\text{b}$ all / SMT-Hawai’i, $^\text{c}$ all / SMT-Chile, $^\text{d}$ single-day data set

Our analysis covers five separate 1.3 mm VLBI observing campaigns conducted in 2009, 2011, 2012, 2013, and 2017. The M87$^{\ast}$ data from 2011 and 2013 have not been published previously. For all campaigns except 2012, M87$^{\ast}$ was observed on multiple nights. For the proto-EHT data sets (2009–2013) we simultaneously utilize the entire data set from each year, fitting to data from multiple days with a single source model, when available. This is motivated by the M87$^{\ast}$ dynamical timescale argument, little visibility amplitude variation reported by on a one-week timescale, as well as by the limited amount of available data and lack of evidence for interday variability in the proto-EHT data sets. We use incoherent averaging to estimate visibility amplitudes on each scan ($\sim$ few minutes of continuous observation) and bispectral averaging to estimate closure phases (cite: Rogers1995; MDJ2015; fish2016). The frequency setup in 2009–2013 consisted of two 480 MHz bands, centered at 229.089 and 229.601 GHz. Whenever both bands or both parallel-hand polarization components were available, we incoherently averaged all simultaneous visibility amplitudes. The data sets are summarized in [\[tab:detections\]](#tab:detections), where the number of detections for nonredundant baselines of different projected baseline lengths is given, with the corresponding $(u,v)$-coverage shown in [2](#fig:coverage). Redundant baselines yield independent observations of the same visibility. In [\[tab:detections\]](#tab:detections) we also indicate the number of available nonredundant closure phases (CPs, not counting redundant and intrasite baselines, minimal set, see (cite: closures)). As is the case for non-phase-referenced VLBI observations (cite: TMS), we do not have access to absolute visibility phases. All visibility amplitudes observed in 2009–2013 are presented in [3](#fig:fluxes).

A more detailed summary of the observational setup of the proto-EHT array in 2009–2013 and the associated data reduction procedures can be found in (cite: fish2016). All data sets discussed in this paper are publicly available[^1].

## 2009–2012

Prior to 2013, the proto-EHT array included telescopes at three geographical locations: (1) the Combined Array for Research in Millimeter-wave Astronomy (CARMA, CA) in Cedar Flat, California, (2) the Submillimeter Telescope (SMT, AZ) on Mt. Graham in Arizona, and (3) the Submillimeter Array (SMA, SM), the James Clerk Maxwell Telescope (JCMT, JC), and the Caltech Submillimeter Observatory (CSO, CS) on Maunakea in Hawai’i. These arrays were strongly east-west oriented, and the longest projected baselines, between SMT and Hawai’i, reached about 3.5 G$\lambda$, corresponding to the instrument resolution (maximum fringe spacing) of $\sim$ 60 $\mu$as.

The 2011 observations of M87$^{\ast}$ have not been published but follow the data reduction procedures described in (cite: Lu2013). The 2009 and 2012 observations and data processing of M87$^{\ast}$ have been published in (cite: Shep2012) and (cite: Kazu2015), respectively. However, our analysis uses a modified processing of the 2012 data because the original processing erroneously applied the same correction for atmospheric opacity at the SMT twice.[^2] The SMT calibration procedures have been updated since then (cite: Issaoun2017b).

Each observation included multiple subarrays of CARMA as well as simultaneous measurements of the total source flux density with CARMA acting as a connected-element interferometer; these properties then allow the CARMA amplitude gains to be “network calibrated” . Of these three observing campaigns, only 2012 provides closure phase information for M87$^{\ast}$, and all closure phases measured on the single, narrow triangle SMT–SMA–CARMA were consistent with zero to within $2\,\sigma$ (cite: Kazu2015), see [4](#fig:closures).

![](fig2_coverage.pdf)

## 2013

The 2013 observing epoch did not include the CSO, but added the

Atacama Pathfinder Experiment facility (APEX, AP) in the Atacama Desert in Chile. This additional site brought for the first time the long (${\approx 5-6\,\rm G}\lambda$) baselines CARMA–APEX and SMT–APEX, that are roughly orthogonal to the CARMA–Hawai’i and SMT–Hawai’i baselines, see [2](#fig:coverage). The addition of APEX increased the instrument resolution (maximum fringe spacing) to $\sim$ 35 $\mu$as. While the 2013 observations of Sgr A$^{\ast}$ were presented in several publications (cite: MDJ2015; fish2016; RuSen2018), the M87$^{\ast}$ observations obtained during the 2013 campaign have not been published previously.

The proto-EHT array observed M87$^{\ast}$ on March 21st, 22nd, 23rd, and 26th 2013. CARMA–APEX detections were found on March 22nd (11 detections) and 23rd (7 detections) with a single SMT–APEX detection on March 23rd. March 23rd (MJD 36374) was the only day with detections on baselines to each of the four geographical sites. No detections between Hawai’i and APEX were found, and there were no simultaneous detections over a closed triangle that would allow for the measurement of closure phase.

## 2017

In 2017, the EHT observed M87$^{\ast}$ with five geographical sites , without CSO and CARMA, but with the addition of the Large Millimeter Telescope Alfonso Serrano (LMT, LM) on the Volcán Sierra Negra in Mexico, the IRAM 30-m telescope (PV) on Pico Veleta in Spain, and the phased-up Atacama Large Millimeter/submillimeter Array (cite: phasingALMA; Goddi2019). The expansion of the array resulted in significant improvements in $(u,v)$-coverage, shown with gray lines in [2](#fig:coverage), and instrument resolution raised to $\sim$ $25\,\mu$as. In addition to hardware setup developments , the recorded bandwidth was increased from 2$\times$0.5 GHz to 2$\times$2 GHz (226-230 GHz). The 2017 data processing pipeline used ALMA as an anchor station . Its high sensitivity greatly improved the signal phase stability

and enabled data analysis based on robustly detected closure quantities obtained from coherently averaged visibilities rather than on visibility amplitudes alone.

These improvements allowed for

an unambiguous analysis of the M87$^{\ast}$ image by constraining the set of physical and geometric models representing the source morphology.

![](fig3_amplitudes.pdf)

## M87$^{\ast}$ data properties

VLBI observations sample the Fourier transform of the intensity distribution on the sky $I(x,y)$ via the van Cittert–Zernike theorem (cite: vancittert; zernike) $$\begin{equation}
    V(u,v) = \iint I(x,y) e^{-2 \pi \text{i}(xu + vy) }  \text{d} x \text{d} y \ ,
\end{equation}$$ where the measured Fourier coefficients $V(u,v)$ are referred to as “visibilities” (cite: TMS). When an array of $N$ telescopes observes a source, $N(N-1)/2$ independent visibility measurements are obtained, provided detections on all baselines are found. Certain properties of the geometry described by $I(x,y)$ can be inferred directly from inspecting the visibility data.

In the top panel of [3](#fig:fluxes) we summarize all the M87$^{\ast}$ detections obtained during 2009–2013 observations as a function of projected baseline length $\sqrt{u^2 + v^2}$. Dashed lines represent $\widehat{R}$, the analytic Fourier transform of an infinitely thin ring with a total intensity $I_0$ and a diameter $d_0$, $$\begin{equation}
\widehat{R}\left( \sqrt{u^2 + v^2} \right) = I_0 J_0 \left(  \pi d_0 \sqrt{u^2 + v^2}\right) \ ,
\end{equation}$$ where $J_0$ is a zeroth-order Bessel function of the first kind. This simple analytic model predicts the visibility null located at $$\begin{equation}
b_0 \approx 3.51 \left(\frac{d_0}{45\,\mu \text{as}} \right)^{-1} \text{G}\lambda \, ,
\label{eq:null}
\end{equation}$$ and a wide plateau around the first maximum, located at $$\begin{equation}
b_1 \approx 5.59 \left(\frac{d_0}{45\,\mu \text{as}} \right)^{-1}  \text{G}\lambda \, ,
\label{eq:plateau}
\end{equation}$$ recovering about 40% of the flux density seen on short baselines. In [3](#fig:fluxes) we use $d_0\,=\,45.0\,\mu$as and show $\widehat{R}$ curves corresponding to $I_0\,=\,$0.25, 0.5, 1.0, 1.5 to guide the eye. The behaviors of the visibility amplitudes, particularly the fall-off rate seen on medium-length baselines (1.0–3.6 G$\lambda$) in all data sets and the flux density recovery on long baselines to APEX in 2013, are roughly consistent with that of a simple ring model. Moreover, all detections on baselines to APEX have a similar flux density of $\sim\,0.2$ Jy, while the projected baseline length varies between 5.2 and 6.1 G$\lambda$. In the analytic thin ring model framework, this can be readily understood, because baselines to APEX sample the wide plateau around the maximum located at $b_1$, [\[eq:plateau\]](#eq:plateau).

The gray dots in [3](#fig:fluxes) correspond to the source model constructed based on the 2017 EHT observations – the mean of the four images reconstructed for April 5th, 6th, 10th and 11th 2017 with the `eht-imaging` pipeline . In the 2017 model, east–west baselines, such as SMT–Hawai’i, probe a deep visibility null located around $b_0$ ([\[eq:null\]](#eq:null)), where sampled amplitudes drop below 0.01 Jy. North–south baselines do not show a similar feature, which indicates source asymmetry. Irrespective of the orientation, visibility amplitudes flatten out around $b_1$. Gray dots with black envelopes represent the 2017 source model sampled at the $(u,v)$-coordinates of the past observations, for which all medium-length baselines were oriented in the east–west direction.

One can immediately notice interesting discrepancies. The visibility amplitudes measured on long baselines to APEX (projected baseline length $\sim\,b_1$) in 2013 were about a factor of 2 larger than the corresponding 2017 source model predictions. At the same time, the flux density on the short CARMA–SMT baseline is consistent between the 2013 measurements and the 2017 model predictions. This shows that the image on the sky has changed between 2013 and 2017 in a structural way, which cannot be explained with a simple total intensity scaling. We also notice that several detections obtained in 2009–2011, corresponding to projected $(u,v)$-distances of 3.2-3.5 G$\lambda$ on Hawai’i–USA baselines, record flux density above 0.1 Jy. At the same time, the 2017 model predicts that these baselines sample a visibility null region around $b_0$, with a flux density lower by an order of magnitude. However, the compact flux (on short baselines) did not change by more than a factor of two, remaining between 0.5 and 1.0 Jy throughout the 2009–2017 observations, see the bottom panel of [3](#fig:fluxes). This suggests that the null location in the past (if present) was different than that observed in 2017, which may correspond to a fluctuation of the crescent position angle or a changing degree of source symmetry.

Apart from the visibility amplitude data, a limited number of closure phases from the narrow triangle SMT–SMA–CARMA has been obtained from the 2012 data set (cite: Kazu2015). All of these closure phases are measured to be consistent with zero, which suggests a high degree of east–west symmetry in the geometry of the source observed in 2012. While the closure phases on this triangle were not observed in 2017 (CARMA was not part of the 2017 array), we can numerically resample the 2017 images to verify the consistency. In [4](#fig:closures) we show the closure phases obtained in 2012, averaged between bands, the two CARMA subarrays shown separately. Near-zero closure phases observed in 2012 are roughly consistent with at least some models from 2017. Unfortunately, technical difficulties that occurred during the 2012 campaign precluded obtaining measurements between UTC 7.5 and 10.5, where nonzero closure phases are predicted by all 2017 models.

![](fig4_cphases.pdf)

Altogether, we see strong suggestions that the 2009–2013 data sets describe a similar geometry to the 2017 results, but there are also substantial hints that the detailed properties of the source structure evolved between observations. These differences can be quantified with geometric modeling of the source morphology.

# Modeling Approach

The sparse nature of the pre-2017 data sets precludes reconstructing images in the manner employed for the 2017 data . However, the earlier data are still capable of providing interesting constraints on more strictly parameterized classes of models. [5](#fig:ring_or_gauss) shows the 2013 data set overplotted with a best-fit ring model[^3] (in blue; 5 degrees of freedom) and asymmetric Gaussian model (in red; 4 degrees of freedom). Both models attain similar fit qualities, as determined by Bayesian and Akaike information criteria (cite: Liddle2007). In the absence of prior information, we would be unable to confidently select a preferred model.

![](fig5_ringorgauss.pdf)

However, the robust image morphology reconstructed from the 2017 data provides a natural and strong prior for selecting an appropriate parameterization. The “generalized crescent” (GC) geometric models considered in yielded fit qualities comparable to those of image reconstructions for the 2017 data, and in this paper, we apply two variants of the GC model to the pre-2017 data sets. Owing to data sparsity, we restrict the parameter space of the models to a subset of that considered in containing only a handful of parameters of interest.

Throughout this paper, we use perceptually uniform color maps from the `ehtplot` library[^4] to display the images. In some of the figures we present models blurred to a resolution of 15 $\mu$as, adopted in this paper as the effective resolution of the EHT. The EHT instrument resolution measured as the maximum fringe spacing in 2017 is about 25 $\mu$as, however, for the image reconstruction methods employed in a moderate effect of superresolution can be expected (cite: Mareki2014; Chael2016). The effect may be much more prominent for the geometric models, which are not fundamentally limited by the resolution.

## Model specification

Given the image morphology inferred from the 2017 data, the primary parameters of interest we would like to constrain using the earlier data sets are the size of the source, the orientation of any asymmetry, and the presence or absence of a central flux depression. The analyses presented in this paper use two simple ring-like models – similar to those presented in (cite: Kamruddin2013) and (cite: Benkevitc2016) – both of which are subsets of the GC models from .

The first model we consider is a concentric “slashed” ring, where the ring intensity is modulated by a linear gradient, hereafter denoted as RT. In this model, the flux is contained within a circular annulus with the inner and outer radii $R_{\rm in}$ and $R_{\rm out}$, respectively. The model is described by five parameters:

1.  the mean diameter of the ring $d = R_{\rm in} + R_{\rm out}$,

2.  the position angle of the bright side of the ring $0 \le \phi_{\rm B} < 2 \pi$,

3.  the fractional thickness of the ring $0< \psi = 1 - R_{\rm in}/R_{\rm out} < 1$,

4.  the total intensity $0 < I_0 < 2$ Jy, and

5.  $\beta$, an intensity gradient (“slash”) across the ring in the direction given by $\phi_{\rm B}$, corresponding to the ratio between the dimmest and brightest points on the ring, $0 < \beta < 1$. A ring of uniform brightness has $\beta=1$, while a ring with vanishing flux at the dimmest part has $\beta = 0$.

This model reduces to a slashed disk for $\psi \rightarrow 1$. The assumed definition of mean diameter is consistent with the one used in , allowing for direct comparisons. Except where otherwise specified, we use this first model for the analyses discussed in this paper.

As a check against model-specific biases, we consider a second model consisting of an infinitesimally thin slashed ring, blurred with a Gaussian kernel . The equivalent five parameters for this model are:

1.  the mean diameter of the ring $d = 2 R_{\rm in} = 2 R_{\rm out}$,

2.  the position angle of the bright side of the ring $0 \le \phi_{\rm B} < 2 \pi$,

3.  the width of the Gaussian blurring kernel $0 < \sigma < 40\,\mu$as,

4.  the total intensity $0 < I_0 < 2$ Jy, and

5.  the slash $0 < \beta < 1$.

This second model, hereafter referred to as RG, reduces to a circular Gaussian for $d \ll \sigma$.

Both the RT and RG models provide a measure of the source diameter ($d$), the orientation of the brightness asymmetry ($\phi_{\text{B}}$), and the presence of a central flux depression. We quantify the latter property using the following general measure of relative ring thickness $$\begin{equation}
    f_{\rm w} = \frac{R_{\rm out} - R_{\rm in} + 2\sigma \sqrt{2 \ln 2}}{d} \ ,
\label{eq:fw}
\end{equation}$$ where $R_{\rm out} = R_{\rm in}$ for the RG model and $\sigma = 0$ for the RT model.

All data sets except 2009 contain observations from intrasite baselines (“zero baselines”), see [\[tab:detections\]](#tab:detections). For M87$^{\ast}$, these baselines are sensitive to the flux from the extended jet emission on $\sim$ arcsecond scales and do not directly inform us about the compact source structure on scales of $\sim$ tens of microarcseconds. However, the intrasite baselines still provide useful constraints on station gain parameters (see [3.2](#sec:FittingProcedure)), and hence, we do not flag them. Rather, we parameterize this large-scale flux using a large symmetric Gaussian component consisting of two parameters, flux and size. This component is entirely resolved out on intersite baselines and thus has no direct impact on the compact source geometry. Ultimately, the models that we use have 5 geometric parameters for the 2009 data set and 5+2=7 geometric parameters in all other cases.

## Fitting procedure and priors

We perform the parameter estimation for this paper using Themis, an analysis framework developed by (cite: broderick20) for the specific requirements of EHT data analysis. Themis operates within a Bayesian formalism, employing a differential evolution Markov chain Monte Carlo (MCMC) sampler to explore the posterior space. Prior to model fitting, the data products are prepared in a manner similar to that described in . Descriptions of the likelihood constructions for different classes of data products are given in (cite: broderick20).

One important difference between the 2017 and pre-2017 data sets is that the latter contain almost exclusively visibility amplitude information, rather than having access to the robust closure quantities in both phase and amplitude (cite: TMS; closures) that aided interpretation of the 2017 data. In addition to thermal noise, visibility amplitudes suffer from uncertainties in the absolute flux calibration, including potential systematic effects such as losses related to telescope pointing imperfections . These uncertainties are parameterized within Themis using station-based amplitude gain factors $g_i$, representing the scaling between the geometric model amplitudes $|\bar{V}_{ij}|$ and the gains-corrected model amplitudes $|\hat{V}_{ij}|$, $$\begin{equation}
\label{eq:gains}
|\hat{V}_{ij}| = (1 + g_i)(1+ g_j) |\bar{V}_{ij}| \, .
\end{equation}$$ Model amplitudes $|\hat{V}_{ij}|$ are then compared with the measured visibility amplitudes $|V_{ij}|$. Within Themis, the number of amplitude gain parameters $N_{\rm g}$ is equal to the number of (station, scan) pairs, i.e., the gains are assumed to be constant across a single scan but uncorrelated from one scan to another. By explicitly modeling station-based gains, we correctly account for the otherwise covariant algebraic structure of the visibility calibration errors (cite: closures). At each MCMC step, Themis marginalizes over the gain amplitude parameters (subject to Gaussian priors) using a quadratic expansion of the log-likelihood around its maximum given the current parameter vector; see (cite: broderick20) for details. For the analysis of the 2009–2013 data sets presented in this paper, we have adopted rather conservative 15% amplitude gain uncertainties for each station, represented by symmetric Gaussian priors with a mean value of 0.0 and standard deviation of 0.15. The width of these priors reflects our confidence in the flux density calibration rather than the statistical variation in the visibility data.

The RT model is parameterized within Themis in terms of $R_{\text{out}}$, $\phi_{\rm B}$, $\psi$, $I_0$, and $\beta$. Uniform priors are used for each of these parameters, with ranges of $[0,200]$ $\mu$as for $R_{\text{out}}$, $[0,2\pi]$ for $\phi_{\rm B}$, $[0,1]$ for $\psi$, $[0,2]$ Jy for $I_0$, and $[0,1]$ for $\beta$. We achieve the “infinitesimally thin” ring of the RG model within Themis by imposing a strict prior on $\psi$ of $[10^{-7},10^{-6}]$, and the prior on $\sigma$ is uniform in the range $[0,40]$ $\mu$as. Because $d$ and $f_{\rm w}$ are derived parameters, we do not impose their priors directly but rather infer them from appropriate transformations of the priors on $R_{\text{out}}$, $\psi$, and $\sigma$. The effective prior on $d = R_{\text{out}} (2 - \psi)$ is given by

$$\begin{equation}
\pi(d) = \begin{cases}
\frac{\ln(2)}{200} , & 0\,\text{\ensuremath{\mu}as} \leq d < 200\,\text{\ensuremath{\mu}as} \\
\frac{1}{200} \ln\left( \frac{400\,\text{\ensuremath{\mu}as}}{d} \right) , & 200\,\text{\ensuremath{\mu}as} \leq d < 400\,\text{\ensuremath{\mu}as} \\
0 , & \text{otherwise}
\end{cases} ,
\end{equation}$$

which is uniform within the range $[0,200]$ $\mu$as. For the RT model, the effective prior on $f_{\rm w} = \psi / (2 - \psi)$ is given by

$$\begin{equation}
\pi_{\text{RT}}(f_{\rm w}) = \begin{cases}
\frac{2}{(1 + f_{\rm w})^2} , & 0 \leq f_{\rm w} \leq 1 \\
0 , & \text{otherwise}
\end{cases} ,
\end{equation}$$

which is not uniform but rather increases toward smaller values. For the RG model, the effective prior on $f_{\rm w} = \sigma \sqrt{2 \ln(2)} / R_{\text{out}}$ is given by

$$\begin{equation}
\pi_{\text{RG}}(f_{\rm {\rm w}}) = \begin{cases}
\frac{1}{2 \alpha} , & 0 \leq f_{\rm w} \leq \alpha \\
\frac{\alpha}{2 f_{\rm w}^2} , & f_{\rm w} > \alpha \\
0 , & \text{otherwise}
\end{cases} ,
\end{equation}$$

where $\alpha = \sqrt{2 \ln(2)} / 5 \approx 0.235$ for our specified priors on $\sigma$ and $R_{\text{out}}$; this prior is uniform within the range $[0,\alpha]$.

## Degeneracies and limitations

Modeling tests revealed the presence of a large-diameter secondary ring mode in the posterior distributions for the 2009–2012 data sets, corresponding to the dashed green line in [5](#fig:ring_or_gauss). This mode is excluded by the detections on long baselines (APEX baselines in 2013, multiple baselines in 2017) and detections on medium-length (${\sim}1.5$ G$\lambda$) baselines (LMT–SMT in 2017). Excising this secondary mode, as we do for the posteriors presented in [6](#fig:grmhd_model_fits), effectively limits the diameter $d$ to be less than $\sim$ 80 $\mu$as. In all cases, the prior range is sufficient to capture the entire volume of the primary posterior mode, corresponding to an emission region of radius $\sim20\,\mu$as. We have verified numerically that this procedure produces the same results as restricting the priors on $R_{\rm out}$ to $[0,45]\, \mu$as for the analysis of the 2009–2012 data sets.

As a consequence of the Fourier symmetry of a real domain input signal, we have $V^*(u,v) = V(-u,-v)$. Hence, visibility amplitude data alone cannot break the degeneracy between the orientation of $\phi_{\rm B}$ and $\phi'_{\rm B} = \phi_{\rm B} + 180^\circ$, and effectively, we only constrain the axis of the crescent asymmetry. This is how the reported uncertainties should be interpreted. Having that in mind, for the 2009, 2011, and 2013, consisting exclusively of the visibility amplitude data, we choose the reported $\phi_{\rm B}$ using the prior information about the position angle of the jet $\phi_{\rm jet}$ to select the $\phi_{\rm B}$ such that $\phi_{\rm jet} - 180^\circ < \phi_{\rm B} < \phi_{\rm jet}$, where $\phi_{\rm jet} = 288^\circ$ (cite: Walker2018). In other words, between the orientations $\phi_{\rm B}$ and $\phi'_{\rm B}$, we choose the one that is closer to the expected bright side position $\phi_{\rm B, exp} = 198^\circ$. This is motivated by the theoretical interpretation of the asymmetric ring feature . In the case of the 2012 data set, for which a very limited number of closure phases is available, we report the orientation $\phi_{\rm B}$ of the maximum likelihood (ML) estimators, noting the bimodal character of the posterior distributions and the aforementioned $180^\circ$ degeneracy. These caveats do not apply to the 2017 data set, for which substantial closure phase information is available and breaks the degeneracy.

It is important to recognize that the parameters of a geometric model have no direct relation to the physical parameters of the source, unlike direct fitting using GRMHD simulation snapshots or ray-traced geometric source models (cite: Broderick2009; Broderick2016; Vincent2020) to the data. The crescent model is a phenomenological description of the source morphology in the observer’s plane. If physical parameters (such as black hole mass) are to be extracted, additional calibration, in general affected by the details of the assumed theoretical model and the $(u,v)$-coverage, needs to be performed .

![image](fig6a_posteriors.pdf) ![image](fig6b_posteriors.pdf) ![image](fig6c_posteriors.pdf) ![image](fig6d_posteriors.pdf)

![](fig7_syntheticB.pdf)

# Modeling synthetic data

In order to verify whether the $(u,v)$-coverage and signal-to-noise ratio of the 2009–2013 observations are sufficient to constrain source geometric properties with simple asymmetric ring models, we have designed tests using synthetic VLBI observations. The synthetic observations are generated with the `eht-imaging` software (cite: Chael2016; Chael2018) by sampling four emission models (GRMHD1, GRMHD2, MODEL1, MODEL2) with the $(u,v)$-coverage and thermal error budget reported for past observations. Additionally, corruption from time-dependent station-based gain errors has been folded into the synthetic observations. The ground-truth images that we use correspond to ray-traced snapshots of a GRMHD simulation and published images of M87$^{\ast}$ , reconstructed based on the 2017 observations.

## GRMHD snapshots

For the first two synthetic data tests, we use a random snapshot from a GRMHD simulation of a low magnetic flux standard and normal evolution (SANE)

accretion disk (cite: Narayan2012; Sadowski2013) around a black hole with spin $a_*\equiv Jc/GM^2=0.5$, shown in [1](#fig:images_intro) (second panel), and in [7](#fig:synthetic_images) (first panel). The GRMHD simulation was performed with the `iharm` code (cite: Gammie2003), and the ray tracing was done with `ipole` (cite: moscibrodzka2018). Following (cite: Moscibrodzka2016) and , we assume a thermal electron energy distribution function and relate the local ratio of ion ($T_{\rm i}$) and electron temperature ($T_{\rm e}$) to the plasma parameter $\beta_{\rm p}$ representing the ratio of gas to magnetic pressure $$\begin{equation}
    \frac{T_{\rm i}}{T_{\rm e}} = R_{\rm high} \frac{\beta_{\rm p}^2}{1+\beta_{\rm p}^2} + R_{\rm low} \frac{1}{1+\beta_{\rm p}^2} \, ,
\label{eq:R}
\end{equation}$$ with $R_{\rm high} = 40$ and $R_{\rm low} = 1$ for the considered snapshot. The prescription given by [\[eq:R\]](#eq:R) parameterizes complex plasma microphysics, allowing us to efficiently survey different models of electron heating, resulting in a different geometry of the radiating region. As an example, for the SANE models with large $R_{\rm high}$ the emission originates predominantly in the strongly magnetized jet base region, while for a small $R_{\rm high}$ disk emission dominates .

The image considered here is a higher resolution version (1280$\times$1280 pixels) of one of the images generated for the Image Library of and corresponds to a $6.5 \times 10^9 M_{\odot}$ black hole at a distance $D$ = 16.9 Mpc. This choice results in an $M/D$ ratio[^5] of 3.80 $\mu$as and an observed black hole shadow that is nearly circular with an angular diameter not substantially different from the Schwarzschild case, which is $2\sqrt{27}M/D = 39.45\,\mu$as (cite: Bardeen1973). For reference, the dashed circles plotted in [1](#fig:images_intro) and [7](#fig:synthetic_images) have a diameter of 42.0 $\mu$as. These parameters were chosen to be consistent with the ones inferred from the EHT 2017 observations . The camera is oriented with an inclination angle of $22^\circ$. The viewing angle was chosen to agree with the expected inclination of the M87$^{\ast}$ jet (cite: Walker2018). The choices of spin $a_*$, electron temperature parameter $R_{\rm high}$, and the SANE accretion state are arbitrary. The choice of $R_{\rm low}$ follows the assumptions made in . We also assume that the accretion disk plane is perpendicular to the black hole jet (the disk is not tilted). The first image, GRMHD1, has been rotated in such a way that the projection of the simulated black hole spin axis counteraligns with the observed position angle of the approaching M87$^{\ast}$ jet, $\phi_{\rm jet}\,=\,288^\circ$ (cite: Walker2018; kim2018). The GRMHD2 test corresponds to the same snapshot, but rotated counterclockwise by 90$^\circ$ to $\phi_{\rm jet}\,=\,18^\circ$, hence displaying a brightness asymmetry in the east-west rather than in the north-south direction, see the second panel of [7](#fig:synthetic_images). Because the $(u,v)$-coverage in 2009–2013 was highly anisotropic, a dependence of the fidelity of the results on the image orientation may be expected.

## M87$^{\ast}$ images

For additional synthetic data tests, we consider images of M87$^{\ast}$ generated based on the 2017 EHT observations, published in . We consider two days of the 2017 observations with good coverage and reported structural source differences - 2017 April 6th (MODEL1) and 2017 April 11th (MODEL2), see the first row of [7](#fig:synthetic_images). MODEL2 was also shown in the first panel of [1](#fig:images_intro). While these models are constructed based on the observational data, we resample them numerically to obtain synthetic data sets considered in this section. Synthetic closure phases on the SMT–SMA–CARMA triangle computed from these models were shown in [4](#fig:closures). Note that there is a subtle difference between resampling a model constructed based on the 2017 data with a numerical model of the 2017 array and direct modeling of the actual 2017 data, considered in [5](#sec:ModelingRealData). The sampled images were generated utilizing the `eht-imaging` pipeline through the procedure outlined in , with a resolution of 64$\times$64 pixels. This test can be viewed as an attempt to evaluate what the outcome of the modeling efforts would have been had the 2017 EHT observations been carried out with one of the proto-EHT 2009–2013 arrays rather than with the mature 2017 array.

## Results for the synthetic data sets

[7](#fig:synthetic_images) shows a summary of the maximum likelihood (ML) RT model fits to the synthetic data sets; each column shows the fits for a single ground-truth image, and each row shows the fits for a single array configuration. Though our simple ring models cannot fully reproduce the properties of the abundant and high signal-to-noise data sampled with the 2017 array (i.e., fits to these data sets are characterized by poor reduced-$\chi^2$ values of $\chi^2_n \sim 5$), they nevertheless recover diameter and orientation values that are reasonably consistent with those reported in for the 2017 observations, including the counterclockwise shift of the brightness position angle between 2017 April 6th (MODEL1) and 11th (MODEL2). We note that the underfitting of the data set sampled with the 2017 array results in an artificial narrowing of the parameter posteriors (the full posterior is captured in by considering a more complicated GC model). ML estimators for 2009–2013 data sets, on the other hand, typically fit the data much closer than the thermal error budget. Because we model time-dependent station gains in a small array (often only two to three telescopes observing at the same time in 2009–2013 with missing detections on some baselines), the number of model parameters may be formally larger than the number of data points, and this complicates our estimation of the number of effective degrees of freedom (see also [5.3](#subs:fit_quality)). As a consequence, we cannot generally utilize a $\chi^2_n$ goodness-of-fit statistic as was done in and .[^6]

The relevant parameter estimates and uncertainties from the RT model fits are listed in [1](#tab:results_sim). In [6](#fig:grmhd_model_fits) we show the marginalized posteriors for the diameter and position angle parameters. For each synthetic data set we also indicate the image domain position angle $\eta$, defined as $$\begin{equation}
    \eta = \text{Arg} \left( \frac{\sum_{k} I_{k} e^{i\phi_k} }{\sum_{k} I_{k}} \right) \, ,
\label{eq:PA}
\end{equation}$$ where $I_k$ is the intensity and $\phi_k$ is the position angle of the $k$th pixel in the image. A similar image domain position angle estimator was considered in . We notice that the image- and model-based estimators may occasionally display significant differences (e.g., GRMHD1). However, they are both sensitive to global properties of the brightness distribution, unlike some other estimators that could be considered, such as, e.g., the location of the brightest pixel. For the diameter $d$ estimates reported in [1](#tab:results_sim) we list both the median and ML values, with 68% and 95% confidence intervals, respectively. For the orientation angle $\phi_{\text{B}}$ we list the ML values with 68% confidence intervals, and for the fractional thickness $f_{\rm w}$ we list the 95th distribution percentile. Values of $\phi_B$ contained in parentheses indicate that the 68% confidence interval exceeds 100$^{\circ}$, in which case we have concluded that the orientation is effectively unconstrained. We find that the diameter is well constrained in general, with the GRMHD data sets recovering a typical value of ${\sim}44$ $\mu$as and 95% confidence intervals that never exceed ${\pm}$12 $\mu$as from this value; the analogous measurement for the MODEL data sets is $44\,\pm\,9\,\mu$as. Biases related to the array orientation can be seen - particularly with the 2013 coverage, the GRMHD2 test estimates an appreciably larger diameter than GRMHD1, inconsistent within the 68% confidence interval.

+:--------------------------:+:---------------:+:--------------------:+:---------------------:+:--------------------:+:-----------:+
|                            | Coverage        | $d\,(\mu$as)                                 | $\phi_{\rm B}$ (deg) | $f_{\rm w}$ |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
| Estimator                  |                 | Median               | ML                    | ML                   | At Most     |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
| Confidence                 |                 | 68%                  | 95%                   | 68%                  | 95%         |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
| GRMHD1                     | 2009            | $46.4^{+5.3}_{-7.9}$ | $51.1^{+4.9}_{-18.5}$ | $194^{+56}_{-5}$     | 0.88        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
|                            | 2011            | $40.9^{+5.6}_{-5.5}$ | $46.8^{+5.1}_{-13.9}$ | $217^{+55}_{-35}$    | 0.93        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
| $\eta^\text{a}= 170^\circ$ | 2012            | $44.0^{+4.9}_{-5.2}$ | $49.3^{+4.3}_{-15.1}$ | $244^{+25}_{-24}$    | 0.90        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
|                            | 2013            | $39.2^{+2.0}_{-0.8}$ | $41.3^{+2.1}_{-4.0}$  | $(246)$              | 0.56        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
|                            | 2017$^\text{b}$ | $43.8^{+0.1}_{-0.1}$ | $43.8^{+0.1}_{-0.1}$  | $225^{+1}_{-1}$      | 0.33        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
| GRMHD2                     | 2009            | $43.1^{+3.4}_{-5.0}$ | $37.2^{+11.8}_{-2.7}$ | $(302)$              | 0.95        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
|                            | 2011            | $44.3^{+2.9}_{-5.4}$ | $47.4^{+2.2}_{-12.4}$ | $(265)$              | 0.94        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
| $\eta^\text{a}= 260^\circ$ | 2012            | $42.2^{+3.3}_{-3.8}$ | $36.3^{+10.0}_{-0.5}$ | $310^{+6}_{-55}$     | 0.96        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
|                            | 2013            | $43.6^{+1.1}_{-0.6}$ | $43.5^{+2.4}_{-1.2}$  | $322^{+38}_{-55}$    | 0.50        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
|                            | 2017$^\text{b}$ | $42.4^{+0.1}_{-0.1}$ | $42.4^{+0.1}_{-0.1}$  | $295^{+1}_{-1}$      | 0.33        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
| MODEL1                     | 2009            | $45.7^{+3.0}_{-4.7}$ | $46.5^{+4.6}_{-9.1}$  | $169^{+10}_{-80}$    | 0.95        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
|                            | 2011            | $47.1^{+2.7}_{-4.6}$ | $49.6^{+2.2}_{-11.4}$ | $190^{+65}_{-5}$     | 0.90        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
| $\eta^\text{a}= 155^\circ$ | 2012            | $41.3^{+3.6}_{-4.0}$ | $36.4^{+9.9}_{-1.2}$  | $352^{+38}_{-47}$    | 0.96        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
|                            | 2013            | $43.1^{+2.1}_{-1.0}$ | $45.1^{+1.8}_{-3.9}$  | $177^{+36}_{-27}$    | 0.63        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
|                            | 2017$^\text{b}$ | $41.0^{+0.1}_{-0.1}$ | $41.0^{+0.1}_{-0.1}$  | $156^{+1}_{-1}$      | 0.47        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
| MODEL2                     | 2009            | $42.7^{+3.8}_{-3.7}$ | $36.0^{+11.9}_{-1.0}$ | $169^{+30}_{-69}$    | 0.97        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
|                            | 2011            | $48.3^{+2.1}_{-4.7}$ | $50.4^{+2.0}_{-10.7}$ | $180^{+72}_{-5}$     | 0.91        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
| $\eta^\text{a}= 172^\circ$ | 2012            | $41.0^{+3.3}_{-2.7}$ | $37.0^{+9.7}_{-0.3}$  | $(179)$              | 0.98        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
|                            | 2013            | $47.0^{+1.1}_{-1.3}$ | $47.3^{+1.8}_{-2.4}$  | $174^{+2}_{-10}$     | 0.53        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+
|                            | 2017$^\text{b}$ | $41.2^{+0.1}_{-0.1}$ | $41.2^{+0.1}_{-0.1}$  | $180^{+1}_{-1}$      | 0.50        |
+----------------------------+-----------------+----------------------+-----------------------+----------------------+-------------+

: Parameter estimates from fitting the RT model to the synthetic data sets.

$^\text{a}$ $\eta$ calculated with [\[eq:PA\]](#eq:PA), $^\text{b}$ using the $(u,v)$-coverage of 2017 April 6th

The orientation $\phi_{\rm B}$ is poorly constrained, with posterior distributions that depend strongly on the details of the $(u,v)$-coverage. Nevertheless, the 2009–2013 ML estimates provide orientations of the axis of asymmetry that are consistent within ${\pm}35^\circ$ with the results obtained using the 2017 synthetic coverage. We note that in 3 out of 4 synthetic data sets, the limited number of closure phases provided by the simulated data sets with the 2012 coverage is enough to correctly break the degeneracy in the position angle $\phi_{\rm B}$, discussed in [3.3](#sub:degenercies). For the synthetic GRMHD data sets, the preference for the correct brightness position angle is very strong (see [6](#fig:grmhd_model_fits)). For the MODEL data sets, the effect of closure phases is much less prominent, the distributions remain bimodal, and in the case of the MODEL1 data set, the ML estimator points at the wrong orientation, suggesting brightness located in the north.

We also consider the fractional thickness $f_{\rm w}$ of the ring, as defined in [\[eq:fw\]](#eq:fw). The fractional thickness provides a measure of whether the data support the presence of a central flux depression, a signature feature of the black hole shadow, or if it is consistent with a disk-like morphology (i.e., $f_{\rm w} \approx 1$ for the RT model). We find that $f_{\rm w}$ is less well constrained than the diameter $d$, consistently with the conclusions of . In some cases the ML estimator corresponds to a limit of a disk-like source morphology without a central depression (see [7](#fig:synthetic_images)). Only the 2013 and 2017 synthetic data sets allow us to confidently establish the presence of a central flux depression, with posterior distributions excluding $f_{\rm w} > 0.7$ for all synthetic data sets (see [1](#tab:results_sim)). For the 2009–2012 coverage synthetic data sets, $f_{\rm w}$ is not constrained sufficiently well to permit similar statements. We find that the RG model produces results that are typically consistent with those of the RT model (see [8](#app:imagesRG), [15](#fig:synthetic_images_blur)).

# Modeling real data

![image](fig8a_oldringsB.pdf) ![image](fig8b_oldrings.pdf)

![image](fig9a_oldringsB.pdf) ![image](fig9b_oldrings.pdf)

![image](fig10_posteriorsRT.pdf) ![image](fig10b_posteriorsRG.pdf)

Encouraged by the results of the tests on synthetic data sets, we performed the same analysis on the 2009–2013 proto-EHT M87$^{\ast}$ observations. We also present the analysis of the 2017 observations with the RT and RG models. In the latter case only lower band data (2 GHz bandwidth centered at 227 GHz) were used.

## Source geometry estimators

In the first row of [\[fig:oldrings\]](#fig:oldrings) we show the ML estimators obtained by fitting the RT model to each observational data set; in [8](#fig:oldrings_blur) we show the same for the RG model. For the 2009, 2011, and 2013 data sets, which only constrain the axis of the crescent asymmetry, the orientation of the brightness peak was selected with a prior derived from the approaching jet orientation on the sky, $\phi_{\rm B} \in (\phi_{\rm jet}-180^\circ, \phi_{\rm jet})$, [3.3](#sub:degenercies). The 2012 data set, for which some closure phases are available, indicates a weak preference toward the brightness position located in the north rather than in the south ([9](#fig:results), and Figures [16](#fig:cornerRT2009-2013)-[17](#fig:cornerRG2009-2013) in the [9](#app:cornerplots)). However, the posterior distribution remains bimodal and 47% of its volume remains consistent with the jet orientation based prior. Hence, the distinction is not very significant – it is entirely dependent on the sign of closure phases shown in [4](#fig:closures), which are all consistent with zero to within 2 $\sigma$. Closure phases predicted by the ML estimators for the RT and RG models are indicated in [4](#fig:closures). The 2017 data sets are consistent with the orientation imposed by the jet position prior. The second rows of Figures [\[fig:oldrings\]](#fig:oldrings) and [8](#fig:oldrings_blur) show the ML estimators blurred to a resolution of $15\,\mu$as. In the third rows of Figures [\[fig:oldrings\]](#fig:oldrings) and [8](#fig:oldrings_blur) we present “mean images” for each data set, obtained by sampling 2 $\times\,10^{4}$ sets of model parameters from the MCMC chains and averaging the corresponding images. The mean images highlight structure that is “typical” of a random draw from the posterior distribution, though we note that a mean image itself does not necessarily provide a good fit to the data. Because of the rotational degeneracy, the orientation is always assumed to be the one closer to the orientation given by the ML estimate of $\phi_{\rm B}$ for the construction of these images.

## Estimated parameters

The marginalized posteriors for the mean diameter $d$ and position angle $\phi_{\rm B}$ for the observational data sets are shown in [9](#fig:results) for both the RT and RG models, and tabulated values of the relevant estimates for the RT model are given in [2](#tab:results2). The posterior distributions for the 2009–2012 data sets have complex shapes, not all parameters are well constrained, and ML estimators do not necessarily coincide with the marginalized posteriors maxima of the individual model parameters, which can be seen in the corner plots (Figures [16](#fig:cornerRT2009-2013)-[17](#fig:cornerRG2009-2013) in the [9](#app:cornerplots)). The behavior of the posterior distributions is much improved for the 2013 data set, and becomes exemplary in the case of the 2017 data sets (Figures [18](#fig:corner2017)-[19](#fig:corner2017RG) in the [9](#app:cornerplots)).

+:---------------:+:--------------------:+:---------------------:+:-------------------:+:-----------:+
|                 | $d\,(\mu$as)                                 | $\phi_{\rm B}$(deg) | $f_{\rm w}$ |
+-----------------+----------------------+-----------------------+---------------------+-------------+
| Estimator       | Median               | ML                    | ML                  | At Most     |
+-----------------+----------------------+-----------------------+---------------------+-------------+
| Confidence      | 68%                  | 95%                   | 68%                 | 95%         |
+-----------------+----------------------+-----------------------+---------------------+-------------+
| 2009            | $39.8^{+5.5}_{-5.2}$ | $47.3^{+3.1}_{-16.0}$ | $202^{+68}_{-23}$   | 0.93        |
+-----------------+----------------------+-----------------------+---------------------+-------------+
| 2011            | $36.5^{+2.0}_{-4.3}$ | $38.6^{+2.8}_{-9.9}$  | $(130)$             | 0.91        |
+-----------------+----------------------+-----------------------+---------------------+-------------+
| 2012$^\text{a}$ | $40.1^{+2.1}_{-4.8}$ | $40.6^{+2.5}_{-8.3}$  | $342^{+42}_{-40}$   | 0.92        |
+-----------------+----------------------+-----------------------+---------------------+-------------+
| 2013            | $46.8^{+2.3}_{-2.9}$ | $47.6^{+3.0}_{-5.5}$  | $281^{+17}_{-34}$   | 0.28        |
+-----------------+----------------------+-----------------------+---------------------+-------------+
| 2017$^\text{b}$ | $41.1^{+0.1}_{-0.1}$ | $41.1^{+0.2}_{-0.2}$  | $155^{+1}_{-1}$     | 0.37        |
+-----------------+----------------------+-----------------------+---------------------+-------------+
| 2017$^\text{c}$ | $40.7^{+0.1}_{-0.1}$ | $40.7^{+0.1}_{-0.1}$  | $184^{+1}_{-1}$     | 0.44        |
+-----------------+----------------------+-----------------------+---------------------+-------------+

: Parameter estimates from fitting the RT model to the observational data sets.

$^\text{a}$ secondary mode present at $\phi_{\rm B}- 180^\circ$ (see the text), $^\text{b}$ 2017 April 6th, $^\text{c}$ 2017 April 11th

Similar to the case of the synthetic data sets, we find that the diameter $d$ is well constrained; the RT model 95% confidence intervals across all observational data sets always fall within $\pm$12 $\mu$as from $d = 40$ $\mu$as. The 2013 proto-EHT observations provide meaningful constraints on $\phi_{\rm B}$, indicating that the source asymmetry in 2013 was in the east-west direction, rather than in the north-south direction, as in the case of the 2017 data set. The 2009 and 2011 data sets do not constrain the orientation well.

All ML estimators and mean images from the RT model fits show a clear shadow feature, indicating that a disk-like, filled-in structure is disfavored by all of the observations (however, for 2009–2012 it cannot be excluded with high confidence based on the relative thickness parameter $f_{\rm w}$ distribution, [2](#tab:results2) and [9](#app:cornerplots)). This is contrary to the synthetic data results shown in [7](#fig:synthetic_images), where some of the ML estimators correspond to a disk-like morphology. On the other hand, the mean images for the 2009–2012 RG model fits show a significant flux density interior to the ring, indicating that these data sets are consistent with a symmetric Gaussian source model, having no central flux depression. This is a consequence of the resolution being limited by the lack of long baselines prior to 2013. Short and medium-length baselines alone provide insufficient information to fully exclude the Gaussian mode allowed by the RG model, or the disk-like mode allowed by the RT model. For the same reason we see flattened posterior distributions of the RG diameter for 2009–2012 in [9](#fig:results) – these indicate consistency with a small, strongly blurred ring with $f_{\rm w} > 1$, becoming a Gaussian in the limit of $\sigma \gg d$.

The slash parameter $\beta$ can be measured to be $0.3 \pm 0.1$ for the 2013 data set, which is consistent with the fits to the 2017 data sets that give $\beta \sim 0.20$ (RT) or $\beta \sim 0.35$ (RG). Fits to the 2012 data set indicate preference toward more symmetric brightness distribution, 2009 and 2011 do not provide meaningful constraints on $\beta$.

## Quality of the visibility amplitude fits

The quality of fits and their behavior in terms of $\chi^2_n$ are similar to the synthetic data sets (see the comments in [4.3](#subsec:synthetic_results) and [3](#tab:results_2017)). In Figures [10](#fig:fit_quality)-[11](#fig:fit_quality2) we explicitly give the number of independent visibility amplitude observations for each data set $N_{\rm ob}$ and the number of independent visibilities on nonzero (intersite) baselines $N_{\rm nz}$. Note that the latter is larger than the number of detections on nonzero, nonredundant baselines given in [\[tab:detections\]](#tab:detections), as some detections are independent but redundant. We also provide the number of explicitly modeled amplitude gains $N_{\rm g}$ for each data set (see [3.2](#sec:FittingProcedure) and [4.3](#subsec:synthetic_results)). Given the pathologies in the $\chi^2_n$ metric described in [4.3](#subsec:synthetic_results), we characterize the quality of the ML estimator fits to data using the two following metrics $$\begin{align}
    \bar{e} &= \frac{1}{N_{\rm nz}}\sum_{i=1}^{N_{\rm nz}} \left| \frac{|V_i| - |\bar{V}_{i}|}{\sigma_i} \right| \ , \label{eq:ebar} \\
     \hat{e} &= \frac{1}{N_{\rm nz}}\sum_{i=1}^{N_{\rm nz}} \left| \frac{|V_i| - |\hat{V}_{i}|}{\sigma_i} \right| \ .
\label{eq:ehat}
\end{align}$$ In Equations [\[eq:ebar\]](#eq:ebar)-[\[eq:ehat\]](#eq:ehat) we follow the notation of [\[eq:gains\]](#eq:gains), that is, $\bar{V}_i$ represents the visibilities of the geometric model while $\hat{V}_i$ corresponds to the model modified by applying the estimated gains, representing the final fit to observations $V_i$. Uncertainties $\sigma_i$ correspond to the thermal error budget. We only account for nonzero baselines, which describe the compact source properties. In the bottom rows of Figures [10](#fig:fit_quality)-[11](#fig:fit_quality2) we indicate two error bars. Black error bars correspond to the thermal uncertainties $\sigma_i$, while the red ones correspond to inflated uncertainties $$\begin{equation}
    s_i = \sqrt{\sigma_i^2 + 2\cdot(0.15 V_i)^2} \ ,
\label{eq:inflated_errors}
\end{equation}$$ approximately capturing the uncertainty related to the amplitude gains. For all 2009–2013 data sets, the flexibility of the full model is sufficient to fit the sparse data to within the thermal uncertainty level with a best-fit ML estimator.

![](fig115_residuals1.pdf)

![](fig115_residuals2.pdf)

## Consistency with the prior analysis

In order to assess model-related biases and verify to what extent our simplified models recover geometric parameters consistent with the ones reported by EHT, i.e., image domain results given in Tables 5 and 7, and geometric modeling results given in Tables 2 and 3, we gather these results in [3](#tab:results_2017). For the details of the methods and algorithms, see explanations and references in and . We notice that (1) differences between methods may be as large as 30$^\circ$ for the same data set, (2) models considered in this work measure diameter and position angle consistently with more complex crescent models (GC) and with the image domain methods within the expected intermodel variation, (3) RT and RG models are too simplistic to fully capture the properties of the 2017 data sets, resulting in underfitting, indicated by higher values of $\chi^2_n$, and (4) posteriors of the RT and RG models are narrower for the 2017 data sets than the GC posteriors as an effect of the underfitting.

+-----------+---------------+------------------------+-------------------------------------------+------------+
| Source    | Method        | $d\,(\mu$as)           | $\phi_{\rm B}$ or $\eta$ (deg)$^\text{a}$ | $\chi^2_n$ |
+:=========:+:=============:+:======================:+:=========================================:+:==========:+
|             2017 April 6th                                                                     |            |
+-----------+---------------+------------------------+-------------------------------------------+------------+
| this work | RT            | $41.1^{+0.09}_{-0.08}$ | $154.8 \pm 1.1$                           | $2.99$     |
+-----------+---------------+------------------------+-------------------------------------------+------------+
|           | RG            | $41.6 \pm 0.07$        | $154.3^{+1.2}_{-1.1}$                     | $3.04$     |
+-----------+---------------+------------------------+-------------------------------------------+------------+
|           | Themis        | $43.5 \pm 0.14$        | $153.0^{+2.0}_{-2.4}$                     | $1.32$     |
+-----------+---------------+------------------------+-------------------------------------------+------------+
| (GC)      | `dynesty`     | $43.4^{+0.27}_{-0.26}$ | $148.5^{+1.4}_{-1.2}$                     | $1.29$     |
+-----------+---------------+------------------------+-------------------------------------------+------------+
|           | `DIFMAP`      | $40.1 \pm 7.4$         | $162.1 \pm 9.7$                           | 2.10       |
+-----------+---------------+------------------------+-------------------------------------------+------------+
| (image    | `eht-imaging` | $39.6 \pm 1.8$         | $151.1 \pm 8.6$                           | 1.28       |
+-----------+---------------+------------------------+-------------------------------------------+------------+
| domain)   | `SMILI`       | $40.9 \pm 2.4$         | $151.7 \pm 8.2$                           | $1.34$     |
+-----------+---------------+------------------------+-------------------------------------------+------------+
|             2017 April 11th                                                                    |            |
+-----------+---------------+------------------------+-------------------------------------------+------------+
| this work | RT            | $40.7\pm 0.05$         | $184.2^{+0.6}_{-0.7}$                     | $7.26$     |
+-----------+---------------+------------------------+-------------------------------------------+------------+
|           | RG            | $41.6^{+0.05}_{-0.04}$ | $185.0\pm 0.6$                            | $7.49$     |
+-----------+---------------+------------------------+-------------------------------------------+------------+
|           | Themis        | $42.2^{+0.43}_{-0.41}$ | $201.1^{+2.5}_{-2.3}$                     | $1.07$     |
+-----------+---------------+------------------------+-------------------------------------------+------------+
| (GC)      | `dynesty`     | $41.6^{+0.51}_{-0.46}$ | $175.9^{+2.1}_{-2.0}$                     | $0.89$     |
+-----------+---------------+------------------------+-------------------------------------------+------------+
|           | `DIFMAP`      | $40.7 \pm 2.6$         | $173.3 \pm 4.8$                           | $2.19$     |
+-----------+---------------+------------------------+-------------------------------------------+------------+
| (image    | `eht-imaging` | $41.0 \pm 1.4$         | $168.0 \pm 6.9$                           | $0.97$     |
+-----------+---------------+------------------------+-------------------------------------------+------------+
| domain)   | `SMILI`       | $42.3 \pm 1.6$         | $167.6 \pm 2.8$                           | $1.08$     |
+-----------+---------------+------------------------+-------------------------------------------+------------+

: Comparison between parameters extraction results reported in This Paper, , and .

$^\text{a}$ results from this work and correspond to visibility domain-based estimator $\phi_{\rm B}$, while results from correspond to the image domain estimator $\eta$, similar to the one given by [\[eq:PA\]](#eq:PA)

![](fig11_fluxinfluenceE.pdf)

# Discussion and conclusions

Processing five independent observations of M87$^{\ast}$ in a unified framework offers important insights into the source morphology and stability. While the constraining power of the 2009–2013 data sets is rather weak in comparison to the 2017 observations, we find evidence for a persistent ring structure that shows modest structural variability. Both the persistence and variability offer important constraints for models of M87$^{\ast}$. We will now discuss our evidence and theoretical implications for the presence of the shadow feature in 2009–2017 ([6.1](#subsec:ringlike_morphology)), the persistence of the source geometry as an argument for its theoretical interpretation ([6.2](#sec:geometry_persistence)), and the variability of the source geometry ([6.3](#subsec:variability)). We also summarize the limitations and caveats of the theoretical interpretation within the GRMHD framework ([6.4](#sub:limitations)).

## Presence of the shadow feature

In [5](#sec:ModelingRealData) we have discussed the fits of the asymmetric ring models to the M87$^{\ast}$ observations, indicating that all data sets are consistent with such a geometry. Within the framework of a ring model, a key question for the archival observations is whether we unambiguously detect the inner flux depression seen in the 2017 results, the expected feature of a black hole shadow. While maximum likelihood estimators clearly indicate this feature in all cases ([\[fig:oldrings\]](#fig:oldrings)), a detailed inspection of the posterior distributions shown in [9](#app:cornerplots) allows us to conclude that only the 2013 archival data set provides a robust detection of the central flux depression, constraining the relative thickness of the ring $f_{\rm w}$ to less than 0.5 (see [2](#tab:results2)). For the 2009–2012 data sets, the RT model posteriors indicate some preference toward the presence of a flux depression; however, a disk-like filled-in geometry cannot be excluded with a high degree of confidence ([9](#app:cornerplots)). This is not entirely surprising, as the 2009–2012 observations lack baselines with projected lengths $> 3.6$ G$\lambda$, probing spatial frequencies higher than the visibility null $b_0$ ([2.4](#subs:salient_features)), which are more sensitive to differences between an empty ring, a filled-in disk, and a Gaussian.

However, the presence of the shadow feature is sensitive to changes in the optical depth. The total compact flux density in 2009–2012 was measured to be $0.8-0.9$ Jy, significantly higher than the $0.5-0.6$ Jy observed in 2013 and 2017 ([3](#fig:fluxes), bottom panel). Mildly elevated levels of X-ray emission from the nucleus of M87 before 2016 were also reported (cite: Sun2018). These measurements suggest a higher mass accretion rate in 2009–2012 and hence a larger density scale, in turn increasing the opacities and the optical depth, possibly changing the appearance of the black hole shadow (cite: Moscibrodzka2012; CK2015). Is it possible that the shadow feature had been obscured by a more optically thick medium in 2009–2012 than in the case of the more recent 2013 and 2017 observations? While the fully general answer to that question would require extensive testing of a variety of GRMHD models, we address this concern by analyzing a representative example from the library of simulated M87$^{\ast}$ images. We consider a random snapshot from a SANE simulation with spin $a_*\,=\,0.5$, and electron temperature parameter $R_{\rm high} = 20$. The $R_{\rm low}$ parameter is equal to 1, as it is throughout this paper. The snapshot is then repeatedly ray-traced with its density scale (and hence opacities and emissivities) adjusted to give a total compact flux density equal to 0.1, 0.3, 0.5, 0.7, 0.9, and 1.1 Jy. The resulting images, normalized by the brightness maximum, are shown in [12](#fig:scaling_flux). These findings indicate that variation in the total compact flux density between 0.1 and 1.1 Jy does not eliminate the central brightness depression. Judging from the similarity between blurred images, the flux density scaling is also not expected to influence the estimated diameter or the position angle appreciably. However, it is likely to influence measures of asymmetry, such as the slash parameter $\beta$ in the RT/RG models, discussed in [3.1](#sec:ModelSpecification). Interestingly, we see a preference toward more symmetric source geometry (larger $\beta$) in the 2012 posteriors ([9](#app:cornerplots)). We conclude that the central flux depression was most likely present throughout the 2009–2017 observations and that a lack of a high-confidence detection of this feature in 2009–2012 is presumably a consequence of the very limited $(u,v)$-coverage.

None of the EHT observations so far took place during an unambiguous flaring activity period of the M87 nucleus, such as the events discussed in (cite: Abramowski2012). We note that such an event could potentially influence the image morphology more strongly than the moderate increase of total brightness considered in [12](#fig:scaling_flux). Future simultaneous multiwavelength observational campaigns will shed light on the structural changes in the M87$^{\ast}$ compact radio image in relation to the enhanced activity in different parts of the spectrum, allowing the site of particle acceleration to be localized.

## Black hole shadow or a transient feature 

As discussed in [3](#sec:modeling), the 2009–2013 data sets can be successfully modeled with both an asymmetric Gaussian and a ring model, with each giving a similar fit quality. However, the maximum likelihood Gaussian models are very inconsistent in size, shape, and orientation across different years, see [13](#fig:oldgauss). In contrast, the best-fitting ring models, as seen in [\[fig:oldrings\]](#fig:oldrings), are similar in size over all epochs under the priors described in Sections [3.2](#sec:FittingProcedure) and [3.3](#sub:degenercies). Even when considered separately from the 2017 results, this consistency supports our choice to interpret the 2009–2013 morphology as a ring and to draw conclusions from the results of fitting asymmetric ring models to the data. The 95% confidence intervals of all 2009–2017 diameter posteriors lie within 40$\pm$12 $\mu$as, while ML estimators of the diameter from all years lie within 43 $\pm$5 $\mu$as, see [2](#tab:results2). These values are also consistent with the M87$^{\ast}$ diameter measurement of 42$\pm$3 $\mu$as reported by and with the expected size of an observed black hole of mass/distance corresponding to the stellar dynamics measurement (cite: Blakeslee2009; Gebhardt2011). All 2009–2017 diameter measurements are inconsistent with the gas dynamics mass measurement (cite: walsh13), which predicts a diameter roughly half as large. The consistency in the diameter across multiple observational epochs supports the interpretation of the ring-like feature as emission from the immediate surroundings of the supermassive black hole.

![](fig12_oldgauss.pdf)

The four EHT observations of M87$^{\ast}$ in 2017 spanned about a week, corresponding to a timescale of $\sim 15\,M$. With such a short time span, we cannot exclude a transient origin for the source morphology using 2017 data alone. However, such a feature would need to attain the geometry and apparent size expected of a shadow of a black hole (of independently measured mass-to-distance ratio) through an unusual coincidence. Moreover, transient features are unlikely to persist with a similar geometry throughout multiple years of observations, corresponding to $\sim 10^3\!-\!10^4\,M$ timescales (the total span of our analyzed observations is $7900 \,M$). For example, a lensed background source would need a low transverse velocity of $v \lesssim 40 \, \rm km \, \rm s^{-1}$ to travel $\lesssim 1 \,M$ between 2009 and 2017. This is much smaller than the gas velocities seen in the nucleus of M87 (cite: macchetto1997). A bright feature moving with the jet ($v \sim c$) should travel $\gtrsim 1$ pc on that timescale, a factor of roughly $10^3$ larger than the physical size of the ring itself. A bright knot or other stationary jet feature would need to persist with a similar location, flux density, and ring morphology to remain consistent with these results. The 8 yr span of the 2009–2017 monitoring is also much longer than the typical variability timescale of the M87 nucleus observed at 230 GHz, which is $\sim\!50$ days (cite: Bower2015). While features remaining stationary for many years in otherwise rapidly flowing jets have been reported and interpreted as standing recollimation shocks (cite: mojave2009), such a configuration would constitute one more unusual coincidence. Thus, we conclude that with multiple years of observations remaining consistent with a $\sim 40\,\mu$as ring model, it is highly unlikely that the origin of the observed geometry could be a transient feature.

## Time variability of the source geometry

In addition to conclusions from the persistence of the ring structure, we can also draw inferences from the variability observed in the ring structure across the 2009–2017 data sets. In particular, the spread of the diameter and brightness position angle estimates ([2](#tab:results2)) are significantly larger than the spread for corresponding static synthetic data sets ([1](#tab:results_sim)). As a specific example, the circular standard deviation of the ML position angle estimators given in [1](#tab:results_sim) is equal to 19$^\circ$, 19$^\circ$, 11$^\circ$, 4$^\circ$ for GRMHD1, GRMHD2, MODEL1, and MODEL2, respectively. For the observational data ([2](#tab:results2)) the circular standard deviation is equal to 48$^\circ$. This larger spread suggests that we are detecting intrinsic structural variability despite the large uncertainties in the parameters estimated with pre-2017 observations. Moreover, unambiguous signatures of intrinsic variability on a timescale of years can be seen directly in the visibility data ([2.4](#subs:salient_features)).

Because GRMHD simulations naturally model both the source structure and its variability, they provide an important pathway for drawing conclusions from the observed variability. As a preliminary demonstration for a comprehensive study that will be published separately, we consider a small subset of the EHT Image Library . The simulations are parameterized with the black hole spin $a_*$, the electron temperature parameter $R_{\rm high}$ (see [4.1](#subsec:grmhd_snapshots)) and the accretion state – strongly magnetized magnetically arrested disk (cite: Narayan2003), or standard and normal evolution (SANE) flow, such as those considered in Sections [4.1](#subsec:grmhd_snapshots) and [6.1](#subsec:ringlike_morphology). Other parameters (e.g., total compact flux density of 0.5 Jy, inclination, jet position angle) are adjusted to match the observed properties of M87$^{\ast}$. For our exploratory study, we utilize the following four simulations: (S1) MAD, $a_*=0.5$, $R_{\rm high}=10$ ; (S2) SANE, $a_*=0.5$, $R_{\rm high}=10$ ; (S3) MAD, $a_*=-0.5$, $R_{\rm high}=10$; (S4) MAD, $a_*=0.5$, $R_{\rm high}=160$. For each simulation, we take 500 ray-traced snapshots with $5\,M$ separation in time. For each snapshot we calculate the position angle of the bright component $\eta$ using [\[eq:PA\]](#eq:PA).

We then construct histograms of $\eta$ for each of the four simulations, shown in [14](#fig:sim_PA).

Each of the simulation parameters influences the distribution of $\eta$, both in terms of its mean and spread. Some of these differences can be readily understood, for instance, in the case of prograde accretion onto a spinning black hole, the radiation is boosted both with Doppler and with frame-dragging effects. The position angle of the bright component is thus expected to be relatively more influenced by the geometry (assumed to be fixed) and not by the stochastic component than the retrograde case, in which Doppler effect and frame-dragging counteract and the geometry becomes relatively less important. Irrespective of the mechanism, some variants of simulations have great difficulties explaining either source orientation on 2017 April 6th (bright component too far clockwise), or in 2013 (too far counterclockwise), as indicated in [14](#fig:sim_PA). Thus, continued EHT observations, with tight constraints on $\eta$ spaced over multiple years, will constrain these types of models on the basis of variability in $\eta$.

## Limitations of the current approach

![](fig13_PAhistograms.pdf)

There are caveats to the simple analysis outlined above that should be addressed in more focused future studies. The simulations that we consider do not capture the full extent of the physics relevant for M87$^{\ast}$. In particular, the electron temperature could be calculated in a more self-consistent fashion than via a temperature ratio prescription of [\[eq:R\]](#eq:R), by separately evolving the energy of ions and electrons (cite: Sadowski2017). Then, one could evolve a population of nonthermal electrons (cite: Chael2017), determine the electrons heating with a well-motivated subgrid prescription (cite: ChaelRowan2018; Jordy2019), or even employ nonideal MHD to model nonthermal emission caused by the particles accelerated through magnetic reconnection in a more self-consistent manner (cite: Bart2019). In the current analysis we also make an assumption of no tilt between the plane of accretion and the black hole spin. If the tilt is present, an additional degree of freedom (“camera longitude”) corresponding to a position angle of the black hole spin (misaligned with the jet position angle $\phi_{\rm jet}$) in the image plane will influence the observed crescent orientation (cite: Chatterjee2020). In that case, analysis of the position angle distributions could place joint constraints on the tilt magnitude, the longitude, and other parameters of the simulation. Large-scale parameter surveys with these extensions to the GRMHD setup are currently precluded by the immense computational costs.

A separate concern is whether the orientation of crescent models fitted to the VLBI data is consistent with the image domain $\eta$ ([\[eq:PA\]](#eq:PA)). In the case of the synthetic data sets considered in [4](#sec:synthetic), the two GRMHD data sets exhibited quite large biases while the two MODEL data sets showed a high level of consistency, so this issue requires further study. Characterizing GRMHD simulations in terms of VLBI observables is the subject of continued work.

# Summary

We have performed geometric modeling of the 2009–2017 EHT observations of M87$^{\ast}$. Motivated by EHT imaging and modeling results using the 2017 observations and the stability of fits across the archival observations, we have used a simple asymmetric ring model. We found that the fitted ring diameter is stable throughout these observations, which strongly argues in favor of its association with the shadow of a supermassive black hole. We observe indications of modest intrinsic variability in the total flux density of the ring and in its position angle.

Specifically, we find the brightness asymmetry along the east-west direction in the previously unpublished 2013 observations, while all other data sets are consistent with the north-south asymmetry direction seen in the 2017 EHT images. This degree of position angle variation is seen in some GRMHD simulations of M87$^{\ast}$, while others do not show position angle variations as broad as those observed between 2013 and 2017. Thus, the source variability over these observations provides new constraints on the simulation parameters, including the black hole spin, accretion flow magnetization, and electron heating model. As an example, the GRMHD MAD model with spin $a_*\!=\!0.5$ and $R_{\rm high}\!=\!160$ (last panel of [14](#fig:sim_PA)), which was determined to be viable by , is inconsistent with the presented position angle measurements. We expect that unmodeled physical effects such as black hole and accretion flow spin misalignment may also be important in interpreting this variability.

Our results extend the temporal span of EHT constraints on the ring morphology by nearly three orders of magnitude, from ${\sim}15\,M$ over the 2017 observations to ${\sim}7900\,M$ between the 2009 and 2017 campaigns. Because the correlation timescale for M87$^{\ast}$ is expected to be at least a few tens of $M$, the longer span is critical for decoupling stable image features such as the black hole shadow from transient features associated with the turbulent accretion flow. As continued EHT observations become available, the variation of the estimated position angle should allow us to discriminate between viable GRMHD models, providing constraints on the physical parameters of M87$^{\ast}$ and opening an exciting new avenue for quantitative time-domain studies of structural variability in M87$^{\ast}$.

# acknowledgements

The authors of the present paper thank the following organizations and programs: the Academy of Finland (projects 274477, 284495, 312496); the Advanced European Network of E-infrastructures for Astronomy with the SKA (AENEAS) project, supported by the European Commission Framework Programme Horizon 2020 Research and Innovation action under grant agreement 731016; the Alexander von Humboldt Stiftung; the Black Hole Initiative at Harvard University, through a grant (60477) from the John Templeton Foundation; the China Scholarship Council; Comisión Nacional de Investigación Cientı́fica y Tecnológica (CONICYT, Chile, via PIA ACT172033, Fondecyt projects 1171506 and 3190878, BASAL AFB-170002, ALMA-conicyt 31140007); Consejo Nacional de Ciencia y Tecnología (CONACYT, Mexico, projects 104497, 275201, 279006, 281692); the Delaney Family via the Delaney Family John A. Wheeler Chair at Perimeter Institute; Dirección General de Asuntos del Personal Académico-—Universidad Nacional Autónoma de México (DGAPA-—UNAM, project IN112417); the European Research Council Synergy Grant "BlackHoleCam: Imaging the Event Horizon of Black Holes" (grant 610058); the Generalitat Valenciana postdoctoral grant APOSTD/2018/177 and GenT Program (project CIDEGENT/2018/021); the Gordon and Betty Moore Foundation (grants GBMF-3561, GBMF-5278); the Istituto Nazionale di Fisica Nucleare (INFN) sezione di Napoli, iniziative specifiche TEONGRAV; the International Max Planck Research School for Astronomy and Astrophysics at the Universities of Bonn and Cologne; the Jansky Fellowship program of the National Radio Astronomy Observatory (NRAO); the Japanese Government (Monbukagakusho: MEXT) Scholarship; the Japan Society for the Promotion of Science (JSPS) Grant-in-Aid for JSPS Research Fellowship (JP17J08829); the Key Research Program of Frontier Sciences, Chinese Academy of Sciences (CAS, grants QYZDJ-SSW-SLH057, QYZDJ-SSW-SYS008, ZDBS-LY-SLH011); the Leverhulme Trust Early Career Research Fellowship; the Max-Planck-Gesellschaft (MPG); the Max Planck Partner Group of the MPG and the CAS; the MEXT/JSPS KAKENHI (grants 18KK0090, JP18K13594, JP18K03656, JP18H03721, 18K03709, 18H01245, 25120007); the MIT International Science and Technology Initiatives (MISTI) Funds; the Ministry of Science and Technology (MOST) of Taiwan (105-2112-M-001-025-MY3, 106-2112-M-001-011, 106-2119-M-001-027, 107-2119-M-001-017, 107-2119-M-001-020, and 107-2119-M-110-005); the National Aeronautics and Space Administration (NASA, Fermi Guest Investigator grant 80NSSC17K0649 and Hubble Fellowship grant HST-HF2-51431.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555); the National Institute of Natural Sciences (NINS) of Japan; the National Key Research and Development Program of China (grant 2016YFA0400704, 2016YFA0400702); the National Science Foundation (NSF, grants AST-0096454, AST-0352953, AST-0521233, AST-0705062, AST-0905844, AST-0922984, AST-1126433, AST-1140030, DGE-1144085, AST-1207704, AST-1207730, AST-1207752, MRI-1228509, OPP-1248097, AST-1310896, AST-1312651, AST-1337663, AST-1440254, AST-1555365, AST-1715061, AST-1615796, AST-1716327, OISE-1743747, AST-1816420); the Natural Science Foundation of China (grants 11573051, 11633006, 11650110427, 10625314, 11721303, 11725312, 11933007); the Natural Sciences and Engineering Research Council of Canada (NSERC, including a Discovery Grant and the NSERC Alexander Graham Bell Canada Graduate Scholarships-Doctoral Program); the National Youth Thousand Talents Program of China; the National Research Foundation of Korea (the Global PhD Fellowship Grant: grants NRF-2015H1A2A1033752, 2015-R1D1A1A01056807, the Korea Research Fellowship Program: NRF-2015H1D3A1066561); the Netherlands Organization for Scientific Research (NWO) VICI award (grant 639.043.513) and Spinoza Prize SPI 78-409; the New Scientific Frontiers with Precision Radio Interferometry Fellowship awarded by the South African Radio Astronomy Observatory (SARAO), which is a facility of the National Research Foundation (NRF), an agency of the Department of Science and Technology (DST) of South Africa; the Onsala Space Observatory (OSO) national infrastructure, for the provisioning of its facilities/observational support (OSO receives funding through the Swedish Research Council under grant 2017-00648) the Perimeter Institute for Theoretical Physics (research at Perimeter Institute is supported by the Government of Canada through the Department of Innovation, Science and Economic Development and by the Province of Ontario through the Ministry of Research, Innovation and Science); the Russian Science Foundation (grant 17-12-01029); the Spanish Ministerio de Economı́a y Competitividad (grants PGC2018-098915-B-C21, AYA2016-80889-P); the State Agency for Research of the Spanish MCIU through the "Center of Excellence Severo Ochoa" award for the Instituto de Astrofı́sica de Andalucı́a (SEV-2017-0709); the Toray Science Foundation; the US Department of Energy (USDOE) through the Los Alamos National Laboratory (operated by Triad National Security, LLC, for the National Nuclear Security Administration of the USDOE (Contract 89233218CNA000001)); the Italian Ministero dell’Istruzione Università e Ricerca through the grant Progetti Premiali 2012-iALMA (CUP C52I13000140001); the European Union’s Horizon 2020 research and innovation programme under grant agreement No 730562 RadioNet; ALMA North America Development Fund; the Academia Sinica; Chandra TM6-17006X; the GenT Program (Generalitat Valenciana) Project CIDEGENT/2018/021. This work used the Extreme Science and Engineering Discovery Environment (XSEDE), supported by NSF grant ACI-1548562, and CyVerse, supported by NSF grants DBI-0735191, DBI-1265383, and DBI-1743442. XSEDE Stampede2 resource at TACC was allocated through TG-AST170024 and TG-AST080026N. XSEDE JetStream resource at PTI and TACC was allocated through AST170028. The simulations were performed in part on the SuperMUC cluster at the LRZ in Garching, on the LOEWE cluster in CSC in Frankfurt, and on the HazelHen cluster at the HLRS in Stuttgart. This research was enabled in part by support provided by Compute Ontario (http://computeontario.ca), Calcul Quebec (http://www.calculquebec.ca) and Compute Canada (http://www.computecanada.ca). We thank the staff at the participating observatories, correlation centers, and institutions for their enthusiastic support. This paper makes use of the following ALMA data:

ADS/JAO.ALMA#2016.1.01154.V. ALMA is a partnership of the European Southern Observatory (ESO; Europe, representing its member states), NSF, and National Institutes of Natural Sciences of Japan, together with National Research Council (Canada), Ministry of Science and Technology (MOST; Taiwan), Academia Sinica Institute of Astronomy and Astrophysics (ASIAA; Taiwan), and Korea Astronomy and Space Science Institute (KASI; Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, Associated Universities, Inc. (AUI)/NRAO, and the National Astronomical Observatory of Japan (NAOJ). The NRAO is a facility of the NSF operated under cooperative agreement by AUI. APEX is a collaboration between the Max-Planck-Institut für Radioastronomie (Germany), ESO, and the Onsala Space Observatory (Sweden). The SMA is a joint project between the SAO and ASIAA and is funded by the Smithsonian Institution and the Academia Sinica. The JCMT is operated by the East Asian Observatory on behalf of the NAOJ, ASIAA, and KASI, as well as the Ministry of Finance of China, Chinese Academy of Sciences, and the National Key R&D Program (No. 2017YFA0402700) of China. Additional funding support for the JCMT is provided by the Science and Technologies Facility Council (UK) and participating universities in the UK and Canada. The LMT is a project operated by the Instituto Nacional de Astrófisica, Óptica, y Electrónica (Mexico) and the University of Massachusetts at Amherst (USA). The IRAM 30-m telescope on Pico Veleta, Spain is operated by IRAM and supported by CNRS (Centre National de la Recherche Scientifique, France), MPG (Max-Planck-Gesellschaft, Germany) and IGN (Instituto Geográfico Nacional, Spain). The SMT is operated by the Arizona Radio Observatory, a part of the Steward Observatory of the University of Arizona, with financial support of operations from the State of Arizona and financial support for instrumentation development from the NSF. The SPT is supported by the National Science Foundation through grant PLR- 1248097. Partial support is also provided by the NSF Physics Frontier Center grant PHY-1125897 to the Kavli Institute of Cosmological Physics at the University of Chicago, the Kavli Foundation and the Gordon and Betty Moore Foundation grant GBMF 947. The SPT hydrogen maser was provided on loan from the GLT, courtesy of ASIAA. The EHTC has received generous donations of FPGA chips from Xilinx Inc., under the Xilinx University Program. The EHTC has benefited from technology shared under open-source license by the Collaboration for Astronomy Signal Processing and Electronics Research (CASPER). The EHT project is grateful to T4Science and Microsemi for their assistance with Hydrogen Masers. This research has made use of NASA’s Astrophysics Data System. We gratefully acknowledge the support provided by the extended staff of the ALMA, both from the inception of the ALMA Phasing Project through the observational campaigns of 2017 and 2018. We would like to thank A. Deller and W. Brisken for EHT-specific support with the use of DiFX. We acknowledge the significance that Maunakea, where the SMA and JCMT EHT stations are located, has for the indigenous Hawaiian people.

natexlab

(ref: Abramowski2012) Abramowski, A., Acero, F., Aharonian, F., et al. 2012, ApJ, 746, 151, doi: [`10.1088/0004-637X/746/2/151`](http://doi.org/10.1088/0004-637X/746/2/151)

(ref: Kazu2015) Akiyama, K., Lu, R.-S., Fish, V. L., et al. 2015, ApJ, 807, 150, doi: [`10.1088/0004-637X/807/2/150`](http://doi.org/10.1088/0004-637X/807/2/150)

(ref: Andrae2010) Andrae, R., Schulze-Hartung, T., & Melchior, P. 2010, arXiv e-prints, arXiv:1012.3754. [`https://arxiv.org/abs/1012.3754`](https://arxiv.org/abs/1012.3754)

(ref: Arras2020) Arras, P., Frank, P., Haim, P., et al. 2020, arXiv e-prints, arXiv:2002.05218. [`https://arxiv.org/abs/2002.05218`](https://arxiv.org/abs/2002.05218)

(ref: MRI) Balbus, S. A., & Hawley, J. F. 1991, ApJ, 376, 214, doi: [`10.1086/170270`](http://doi.org/10.1086/170270)

(ref: Bardeen1973) Bardeen, J. M. 1973, in Black Holes (Les Astres Occlus), ed. C. Dewitt & B. S. Dewitt, 215–239

(ref: Benkevitc2016) Benkevitch, L., Akiyama, K., Lu, R., Doeleman, S., & Fish, V. 2016, arXiv e-prints, arXiv:1609.00055. [`https://arxiv.org/abs/1609.00055`](https://arxiv.org/abs/1609.00055)

(ref: closures) Blackburn, L., Pesce, D. W., Johnson, M. D., et al. 2020, ApJ, 894, 31, doi: [`10.3847/1538-4357/ab8469`](http://doi.org/10.3847/1538-4357/ab8469)

(ref: hops2019) Blackburn, L., Chan, C.-k., Crew, G. B., et al. 2019, ApJ, 882, 23, doi: [`10.3847/1538-4357/ab328d`](http://doi.org/10.3847/1538-4357/ab328d)

(ref: Blakeslee2009) Blakeslee, J. P., Jordán, A., Mei, S., et al. 2009, ApJ, 694, 556, doi: [`10.1088/0004-637X/694/1/556`](http://doi.org/10.1088/0004-637X/694/1/556)

(ref: Bower2015) Bower, G. C., Dexter, J., Markoff, S., et al. 2015, ApJL, 811, L6, doi: [`10.1088/2041-8205/811/1/L6`](http://doi.org/10.1088/2041-8205/811/1/L6)

(ref: Broderick2009) Broderick, A. E., & Loeb, A. 2009, ApJ, 697, 1164, doi: [`10.1088/0004-637X/697/2/1164`](http://doi.org/10.1088/0004-637X/697/2/1164)

(ref: Broderick2016) Broderick, A. E., Fish, V. L., Johnson, M. D., et al. 2016, ApJ, 820, 137, doi: [`10.3847/0004-637X/820/2/137`](http://doi.org/10.3847/0004-637X/820/2/137)

(ref: broderick20) Broderick, A. E., Gold, R., Karami, M., et al. 2020, ApJ, 897, 139, doi: [`10.3847/1538-4357/ab91a4`](http://doi.org/10.3847/1538-4357/ab91a4)

(ref: ChaelRowan2018) Chael, A., Rowan, M., Narayan, R., Johnson, M., & Sironi, L. 2018a, MNRAS, 478, 5209, doi: [`10.1093/mnras/sty1261`](http://doi.org/10.1093/mnras/sty1261)

(ref: Chael2018) Chael, A. A., Johnson, M. D., Bouman, K. L., et al. 2018b, ApJ, 857, 23, doi: [`10.3847/1538-4357/aab6a8`](http://doi.org/10.3847/1538-4357/aab6a8)

(ref: Chael2016) Chael, A. A., Johnson, M. D., Narayan, R., et al. 2016, ApJ, 829, 11, doi: [`10.3847/0004-637X/829/1/11`](http://doi.org/10.3847/0004-637X/829/1/11)

(ref: Chael2017) Chael, A. A., Narayan, R., & Sadowski, A. 2017, MNRAS, 470, 2367, doi: [`10.1093/mnras/stx1345`](http://doi.org/10.1093/mnras/stx1345)

(ref: CK2015) Chan, C.-k., Psaltis, D., Özel, F., et al. 2015, ApJ, 812, 103, doi: [`10.1088/0004-637X/812/2/103`](http://doi.org/10.1088/0004-637X/812/2/103)

(ref: Chatterjee2020) Chatterjee, K., Younsi, Z., Liska, M., et al. 2020, arXiv e-prints, arXiv:2002.08386. [`https://arxiv.org/abs/2002.08386`](https://arxiv.org/abs/2002.08386)

(ref: Jordy2019) Davelaar, J., Olivares, H., Porth, O., et al. 2019, A&A, 632, A2, doi: [`10.1051/0004-6361/201936150`](http://doi.org/10.1051/0004-6361/201936150)

(ref: Dexter2010) Dexter, J., Agol, E., Fragile, P. C., & McKinney, J. C. 2010, ApJ, 717, 1092, doi: [`10.1088/0004-637X/717/2/1092`](http://doi.org/10.1088/0004-637X/717/2/1092)

(ref: Doeleman2009) Doeleman, S., Agol, E., Backer, D., et al. 2009, in astro2010: The Astronomy and Astrophysics Decadal Survey, Vol. 2010, 68

(ref: Shep2012) Doeleman, S. S., Fish, V. L., Schenck, D. E., et al. 2012, Science, 338, 355, doi: [`10.1126/science.1224768`](http://doi.org/10.1126/science.1224768)

(ref: Paper1) Event Horizon Telescope Collaboration, Akiyama, K., Alberdi, A., et al. 2019a, ApJL, 875, L1, doi: [`10.3847/2041-8213/ab0ec7`](http://doi.org/10.3847/2041-8213/ab0ec7)

(ref: Paper2) —. 2019b, ApJL, 875, L2, doi: [`10.3847/2041-8213/ab0c96`](http://doi.org/10.3847/2041-8213/ab0c96)

(ref: Paper3) —. 2019c, ApJL, 875, L3, doi: [`10.3847/2041-8213/ab0c57`](http://doi.org/10.3847/2041-8213/ab0c57)

(ref: Paper4) —. 2019d, ApJL, 875, L4, doi: [`10.3847/2041-8213/ab0e85`](http://doi.org/10.3847/2041-8213/ab0e85)

(ref: Paper5) —. 2019e, ApJL, 875, L5, doi: [`10.3847/2041-8213/ab0f43`](http://doi.org/10.3847/2041-8213/ab0f43)

(ref: Paper6) —. 2019f, ApJL, 875, L6, doi: [`10.3847/2041-8213/ab1141`](http://doi.org/10.3847/2041-8213/ab1141)

(ref: Falcke2000) Falcke, H., Melia, F., & Agol, E. 2000, ApJL, 528, L13, doi: [`10.1086/312423`](http://doi.org/10.1086/312423)

(ref: Fish2011) Fish, V. L., Doeleman, S. S., Beaudoin, C., et al. 2011, ApJL, 727, L36, doi: [`10.1088/2041-8205/727/2/L36`](http://doi.org/10.1088/2041-8205/727/2/L36)

(ref: fish2016) Fish, V. L., Johnson, M. D., Doeleman, S. S., et al. 2016, ApJ, 820, 90, doi: [`10.3847/0004-637X/820/2/90`](http://doi.org/10.3847/0004-637X/820/2/90)

(ref: GENA2019) Fromm, C. M., Younsi, Z., Baczko, A., et al. 2019, A&A, 629, A4, doi: [`10.1051/0004-6361/201834724`](http://doi.org/10.1051/0004-6361/201834724)

(ref: Gammie2003) Gammie, C. F., McKinney, J. C., & Tóth, G. 2003, ApJ, 589, 444, doi: [`10.1086/374594`](http://doi.org/10.1086/374594)

(ref: Gebhardt2011) Gebhardt, K., Adams, J., Richstone, D., et al. 2011, ApJ, 729, 119, doi: [`10.1088/0004-637X/729/2/119`](http://doi.org/10.1088/0004-637X/729/2/119)

(ref: Goddi2019) Goddi, C., Martı́-Vidal, I., Messias, H., et al. 2019, PASP, 131, 075003, doi: [`10.1088/1538-3873/ab136a`](http://doi.org/10.1088/1538-3873/ab136a)

(ref: Mareki2014) Honma, M., Akiyama, K., Uemura, M., & Ikeda, S. 2014, PASJ, 66, 95, doi: [`10.1093/pasj/psu070`](http://doi.org/10.1093/pasj/psu070)

(ref: Issaoun2017b) Issaoun, S., Folkers, T. W., Marrone, D. P., et al. 2017, EHT Memo Series, 2017-CE-03

(ref: casa) Janssen, M., Goddi, C., van Bemmel, I. M., et al. 2019, A&A, 626, A75, doi: [`10.1051/0004-6361/201935181`](http://doi.org/10.1051/0004-6361/201935181)

(ref: MDJ2015) Johnson, M. D., Fish, V. L., Doeleman, S. S., et al. 2015, Science, 350, 1242, doi: [`10.1126/science.aac7087`](http://doi.org/10.1126/science.aac7087)

(ref: Kamruddin2013) Kamruddin, A. B., & Dexter, J. 2013, MNRAS, 434, 765, doi: [`10.1093/mnras/stt1068`](http://doi.org/10.1093/mnras/stt1068)

(ref: Kim2016) Kim, J., Marrone, D. P., Chan, C.-K., et al. 2016, ApJ, 832, 156, doi: [`10.3847/0004-637X/832/2/156`](http://doi.org/10.3847/0004-637X/832/2/156)

(ref: kim2018) Kim, J. Y., Krichbaum, T. P., Lu, R. S., et al. 2018, A&A, 616, A188, doi: [`10.1051/0004-6361/201832921`](http://doi.org/10.1051/0004-6361/201832921)

(ref: Liddle2007) Liddle, A. R. 2007, MNRAS, 377, L74, doi: [`10.1111/j.1745-3933.2007.00306.x`](http://doi.org/10.1111/j.1745-3933.2007.00306.x)

(ref: mojave2009) Lister, M. L., Cohen, M. H., Homan, D. C., et al. 2009, AJ, 138, 1874, doi: [`10.1088/0004-6256/138/6/1874`](http://doi.org/10.1088/0004-6256/138/6/1874)

(ref: Lu2013) Lu, R.-S., Fish, V. L., Akiyama, K., et al. 2013, ApJ, 772, 13, doi: [`10.1088/0004-637X/772/1/13`](http://doi.org/10.1088/0004-637X/772/1/13)

(ref: RuSen2018) Lu, R.-S., Krichbaum, T. P., Roy, A. L., et al. 2018, ApJ, 859, 60, doi: [`10.3847/1538-4357/aabe2e`](http://doi.org/10.3847/1538-4357/aabe2e)

(ref: Luminet1979) Luminet, J.-P. 1979, A&A, 75, 228

(ref: macchetto1997) Macchetto, F., Marconi, A., Axon, D. J., et al. 1997, ApJ, 489, 579, doi: [`10.1086/304823`](http://doi.org/10.1086/304823)

(ref: phasingALMA) Matthews, L. D., Crew, G. B., Doeleman, S. S., et al. 2018, PASP, 130, 015002, doi: [`10.1088/1538-3873/aa9c3d`](http://doi.org/10.1088/1538-3873/aa9c3d)

(ref: Moscibrodzka2016) Mościbrodzka, M., Falcke, H., & Shiokawa, H. 2016, A&A, 586, A38, doi: [`10.1051/0004-6361/201526630`](http://doi.org/10.1051/0004-6361/201526630)

(ref: moscibrodzka2018) Mościbrodzka, M., & Gammie, C. F. 2018, MNRAS, 475, 43, doi: [`10.1093/mnras/stx3162`](http://doi.org/10.1093/mnras/stx3162)

(ref: Moscibrodzka2012) Mościbrodzka, M., Shiokawa, H., Gammie, C. F., & Dolence, J. C. 2012, ApJL, 752, L1, doi: [`10.1088/2041-8205/752/1/L1`](http://doi.org/10.1088/2041-8205/752/1/L1)

(ref: Narayan2003) Narayan, R., Igumenshchev, I. V., & Abramowicz, M. A. 2003, PASJ, 55, L69, doi: [`10.1093/pasj/55.6.L69`](http://doi.org/10.1093/pasj/55.6.L69)

(ref: Narayan2012) Narayan, R., Sądowski, A., Penna, R. F., & Kulkarni, A. K. 2012, MNRAS, 426, 3241, doi: [`10.1111/j.1365-2966.2012.22002.x`](http://doi.org/10.1111/j.1365-2966.2012.22002.x)

(ref: Porth2019) Porth, O., Chatterjee, K., Narayan, R., et al. 2019, ApJS, 243, 26, doi: [`10.3847/1538-4365/ab29fd`](http://doi.org/10.3847/1538-4365/ab29fd)

(ref: Bart2019) Ripperda, B., Bacchini, F., Porth, O., et al. 2019, ApJS, 244, 10, doi: [`10.3847/1538-4365/ab3922`](http://doi.org/10.3847/1538-4365/ab3922)

(ref: Rogers1995) Rogers, A. E. E., Doeleman, S. S., & Moran, J. M. 1995, AJ, 109, 1391, doi: [`10.1086/117371`](http://doi.org/10.1086/117371)

(ref: Sadowski2013) Sądowski, A., Narayan, R., Penna, R., & Zhu, Y. 2013, MNRAS, 436, 3856, doi: [`10.1093/mnras/stt1881`](http://doi.org/10.1093/mnras/stt1881)

(ref: Sadowski2017) Sądowski, A., Wielgus, M., Narayan, R., et al. 2017, MNRAS, 466, 705, doi: [`10.1093/mnras/stw3116`](http://doi.org/10.1093/mnras/stw3116)

(ref: Sun2018) Sun, X.-N., Yang, R.-Z., Rieger, F. M., Liu, R.-Y., & Aharonian, F. 2018, A&A, 612, A106, doi: [`10.1051/0004-6361/201731716`](http://doi.org/10.1051/0004-6361/201731716)

(ref: TMS) Thompson, A. R., Moran, J. M., & Swenson, George W., J. 2017, Interferometry and Synthesis in Radio Astronomy, 3rd Edition (Springer), doi: [`10.1007/978-3-319-44431-4`](http://doi.org/10.1007/978-3-319-44431-4)

(ref: vancittert) van Cittert, P. H. 1934, Physica, 1, 201, doi: [`/10.1016/S0031-8914(34)90026-4`](http://doi.org//10.1016/S0031-8914(34)90026-4)

(ref: Vincent2020) Vincent, F. H., Wielgus, M., Abramowicz, M. A., et al. 2020, arXiv e-prints, arXiv:2002.09226. [`https://arxiv.org/abs/2002.09226`](https://arxiv.org/abs/2002.09226)

(ref: Walker2018) Walker, R. C., Hardee, P. E., Davies, F. B., Ly, C., & Junor, W. 2018, ApJ, 855, 128, doi: [`10.3847/1538-4357/aaafcc`](http://doi.org/10.3847/1538-4357/aaafcc)

(ref: walsh13) Walsh, J. L., Barth, A. J., Ho, L. C., & Sarzi, M. 2013, ApJ, 770, 86, doi: [`10.1088/0004-637X/770/2/86`](http://doi.org/10.1088/0004-637X/770/2/86)

(ref: White2020) White, C. J., Dexter, J., Blaes, O., & Quataert, E. 2020, ApJ, 894, 14, doi: [`10.3847/1538-4357/ab8463`](http://doi.org/10.3847/1538-4357/ab8463)

(ref: Yuan2014) Yuan, F., & Narayan, R. 2014, ARA&A, 52, 529, doi: [`10.1146/annurev-astro-082812-141003`](http://doi.org/10.1146/annurev-astro-082812-141003)

(ref: zernike) Zernike, F. 1938, Physica, 5, 785, doi: [`10.1016/S0031-8914(38)80203-2`](http://doi.org/10.1016/S0031-8914(38)80203-2)

# ML estimators for the RG model

Figure [15](#fig:synthetic_images_blur) presents RG models best-fitting the synthetic data sets, following the procedures described in Section [4](#sec:synthetic).

![](fig14_syntheticblurB.pdf)

# Corner plots for the RT and the RG models

We present the posterior probability distributions corresponding to fitting the 2009–2013 data sets with the RT model, Figure [16](#fig:cornerRT2009-2013), and with the RG model, Figure [17](#fig:cornerRG2009-2013). Similarly, for the 2017 data sets, we show the posterior distributions obtained for the RT model, Figure [18](#fig:corner2017), and for the RG model, Figure [19](#fig:corner2017RG).

![image](corn2009RT_360.pdf) ![image](corn2011RT_360.pdf) ![image](corn2012RT_360.pdf) ![image](corn2013RT_360.pdf)

![image](corn2009RG_360.pdf) ![image](corn2011RG_360.pdf) ![image](corn2012RG_360.pdf) ![image](corn2013RG_360.pdf)

![image](corn2017_6RT.pdf) ![image](corn2017_11RT.pdf)

![image](corn2017_6RG.pdf) ![image](corn2017_11RG.pdf)

[^1]: <https://eventhorizontelescope.org/for-astronomers/data>

[^2]: An opacity correction raises visibility amplitudes on SMT baselines by $\sim$10% in nominal conditions; our visibility amplitudes on SMT baselines are, thus, slightly lower than those reported by (cite: Kazu2015). However, the calibration error does not change the primary conclusions of (cite: Kazu2015).

[^3]: This is the maximum likelihood estimator for the slashed thick ring model (RT), as discussed in [3.1](#sec:ModelSpecification).

[^4]: <https://github.com/liamedeiros/ehtplot>

[^5]: Hereafter, we use the natural units in which $G=c=1$.

[^6]: See, e.g., (cite: Andrae2010) for further comments about the problems with the $\chi^2_n$ metric and counting the degrees of freedom.

</paper>

Write the methods card for this paper.