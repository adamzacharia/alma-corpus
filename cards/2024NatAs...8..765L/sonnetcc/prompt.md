# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024NatAs...8..765L\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2024NatAs...8..765L",
 "title": "Orbital polarimetric tomography of a flare near the Sagittarius A<SUP>*</SUP> supermassive black hole",
 "year": 2024,
 "journal": "Nature Astronomy",
 "first_author": "Levis, Aviad",
 "n_authors": 5,
 "arxiv_id": "2310.07687",
 "doi": "10.1038/s41550-024-02238-3",
 "alma_projects_linked_by_archive": [
  "2016.1.01404.V"
 ]
}
```

Paper text:
<paper>
# Orbital Polarimetric Tomography of a Flare Near the Sagittarius A$^*$ Supermassive Black HoleOrbital Polarimetric Tomography of a Flare Near the Sagittarius A$^*$ Supermassive Black Hole: Supplementary Material

![](figures/ALMA_recovery_v2.pdf)

The compact region around the Galactic Center supermassive black hole Sgr A$^*$ is a unique environment where the magnetized turbulent flow of an accretion disk is subject to extreme gravitational physics. The dynamical evolution of this complex system occasionally leads to the production of energetic flares (cite: genzel2003near) seen in X-ray (cite: neilsen2013chandra), infra-red (cite: fazio2018multiwavelength), and radio (cite: Wielgus2022lc). The physical nature, structure, origin, formation, and eventual dissipation of flares are topics of active research (cite: fazio2018multiwavelength; Marrone_2008; Haggardetal2019; dexter2020sgr; Witzel_2021) key to our understanding of accretion flows around black holes. One proposed explanation for Sgr A$^*$ flares is the formation of compact bright regions caused by hot pockets of lower-density plasma within the accretion disk, that are rapidly energized (e.g. through magnetic reconnection (cite: broderick2005imaging)). These “bubbles”, “hotspots” or “flux tubes”, observed in numerical simulations (e.g. (cite: ripperda2022black)), are hypothesized to form in orbit close to the innermost stable circular orbit (ISCO) of Sgr A$^*$. The association of flares with orbiting hotspots close to the event horizon is consistent with near-infrared detections made by the GRAVITY Collaboration (cite: gravity18; gravity20) and radio observations of the Atacama Large Millimeter/Submillimeter Array (ALMA) (cite: wielgus2022orbital).

The context for this work is set by the first images (cite: akiyama2022firstI) of Sgr A$^*$ revealed by the Event Horizon Telescope (EHT) collaboration. The images, reconstructed from Very Long Baseline Interferometry (VLBI) observations from April 6–7, 2017, show a ring-like structure with a central brightness depression – a strong suggestion that the source is indeed a supermassive black hole (cite: akiyama2022firstVI). Even in its quiescent state imaged by EHT on April 6/7, Sgr A$^*$ has shown significant structural variability (cite: akiyama2022firstIII). On April 11, 2017, Sgr A$^*$ was observed by ALMA directly after a high-energy flare seen in X-ray. The ALMA light curves exhibit an even higher degree of variability to April 6/7 (cite: Wielgus2022lc; akiyama2022firstII), including distinct coherent patterns in the linear polarization (cite: wielgus2022orbital) with variability on the scale of an orbit. The presence of synchrotron-radiating matter very close to the horizon of Sgr A$^*$ could potentially give rise to bright 3D structures that orbit and evolve within the accretion disk. In this work, we present the first 3D recovery of emission in orbit around Sgr A$^*$ reconstructed from ALMA light curves observed on April 11, 2017 (Fig. [1](#fig:alma_rec)).

To achieve this 3D reconstruction we develop a novel computational approach which we term: *orbital polarimetric tomography*. In contrast to prior work by (cite: gravity18) and (cite: wielgus2022orbital), which employed a strongly constrained parametric hotspot model, with only a handful of parameters to tune and interpret the observations, the goal of this work is to recover the complex 3D structure of flares as they orbit and evolve in the accretion disk around Sgr A$^*$.

Tackling this inverse problem necessitates a change from typical tomography, wherein 3D recovery is enabled by multiple viewpoints. Instead, the tomography setting we propose relies on observing a structure in orbit, traveling through curved spacetime, from a fixed viewpoint. As it orbits the black hole, the emission structure is observed (projected) along different curved ray paths. These observations of the evolving structure over time effectively replace the observations from multiple viewpoints required in traditional tomography. Our approach builds upon prior work on dynamical imaging and 3D tomography in curved spacetime, which showed promising results in *simulated* future Event Horizon Telescope (EHT) observations (cite: Tiede_2020; levis2021inference; levis2022gravitationally).

Similar to the computational images recovered by EHT (cite: akiyama2022firstIII), our approach solves an under-constrained inverse problem to fit a model to the data. Nevertheless, ALMA observations do not resolve event horizon scales ($\sim 10^5$ lower resolution), which makes the tomography problem we propose particularly challenging. To put it differently, we seek to recover an evolving 3D structure from a single-pixel observation over time. In order to solve this challenging task, we integrate the emerging approach of neural 3D representations (cite: levis2022gravitationally; mildenhall2020nerf), which has an implicit regularization that favors smooth structures (cite: tancik2020fourfeat), with physics constraints (details in the Methods section). The robustness of the results thus relies on the validity of the constraints imposed by the gravitational and synchrotron emission models.

We take advantage of the very high signal-to-noise and cadence of the ALMA dataset (cite: Wielgus2022lc), as well as the linear polarization information (cite: wielgus2022orbital). The choice to only fit the LP light curves reflects the uncertainty associated with the un-polarized intensity of the background accretion disk. While the total intensity light curve is dominated by the accretion disk, such extended emission structures are partially depolarized in an image-average sense (cite: wielgus2022orbital). In contrast, compact bright sources, such as a putative hotspot, are characterized by a large fractional linear polarization (LP) and fast evolution on dynamical timescales (cite: wielgus2022orbital; Gravity2023), hence allowing separation of the flare component from the background accretion. In the Supplementary (Sec. 2.2), we quantitatively assess the effect of the background accretion disk on simulated reconstruction results.

![](figures/ALMA_data_v3.pdf)

# Results

On April 11, 2017, ALMA observed Sgr A$^*$ at $\sim 230 {\rm GHz}$ as part of a larger EHT campaign (Fig. [2](#fig:alma_datafit) top). The radio observations directly followed a flare seen in the X-ray. The LP, measured by ALMA-only light curves (cite: Wielgus2022lc; wielgus2022orbital) as a complex time series $Q(t)+iU(t)$, appears to evolve in a structured, periodic, manner suggesting a compact emission structure in orbit. The work of (cite: wielgus2022orbital) hypothesizes a simple bright spot (i.e. idealized point-source (cite: gelles2021polarized) or spherical Gaussian (cite: vos2022polarimetric)) at $r\sim 11 {\rm M}$, however, a rigorous data-fitting was not performed. Furthermore, the proposed parametric model is limited and does not explain all of the data features. The orbital polarimetric tomography approach that we propose enables a rigorous data-fitting and recovery of flexible 3D distributions of the emitting matter, relaxing the assumption of a fixed orbiting feature enforced by prior studies (cite: gravity18; wielgus2022orbital; yfantis2023). This opens up a new window into understanding the spatial structure and location of flares relative to the event horizon.

Our model, detailed in the Methods section, is able to fit the ALMA light curve data very accurately (Fig. [2](#fig:alma_datafit) bottom). The optimization procedure simultaneously constrains the inclination angle of the observer and estimates a 3D distribution of the emitting matter associated with this flaring event, starting from 9:20 UT ($\sim 30$ minutes after the peak of the X-ray flare (cite: wielgus2022orbital)). Despite the fact that ALMA observations are unresolved (effectively a single pixel with time-dependent complex LP information) at the horizon scale, our analysis suggests some interesting insights:

- Low inclination angles ($\theta_{\rm o}<18^\circ$, Fig. [1](#fig:alma_rec) left panel, red) are preferred by the *validation-$\chi^2$* (Methods section). While the methodology is different, this result is broadly consistent with EHT findings from April 6/7 (cite: akiyama2022firstV), which favored low inclination angles of $\sim 30^\circ$ by comparing recovered images with General Relativistic Magneto Hydro Dynamic simulations. The fiducial model of (cite: wielgus2022orbital) corresponded to an inclination angle of $\sim 22^\circ$. Low inclination was also favored in the analysis of the GRAVITY infra-red flares (cite: gravity18; gravity20; Gravity2023).

- The recovered 3D emission has two compact bright regions at $r \sim 11M, 13M$ (Fig. [1](#fig:alma_rec) middle/right panels). The location (radius and azimuthal position) of the bright region is consistent with the qualitative analysis of (cite: wielgus2022orbital; yfantis2023).

![](figures/method_overview_v2.pdf)

## Data fitting

Before solving the tomography problem, we perform pre-processing according to the procedure outlined in (cite: wielgus2022orbital). In particular, we time average the data, subtract a constant (time-averaged) LP component interpreted as the ring-like accretion disk component observed by the EHT, and de-rotate the electric vector polarization angle (EVPA) to account for Faraday rotation (details in the Methods section). Figure [2](#fig:alma_datafit) illustrates the data before and after the pre-processing.

To obtain a model prediction a 3D emission structure is adjusted so that, when placed in orbit, the numerically ray-traced light curves align with the observations. To recover the vertical structure, our approach primarily leverages asymmetries in the polarimetric radiative transfer. In particular, the geometry of space-time and the magnetic field dictate the angle of linear polarization (Q-U). Moving an emission point changes the observed angle of linear polarization. Thus, erroneously placing emission at $t=0$ and propagating it in time will rotate to the overall linear polarization in directions that are incompatible with the observed Q-U time series.

Computing the model predictions relies on ray tracing, which requires knowledge of the path rays take in 3D curved spacetime. These geodesic paths depend on the *unknown* black hole properties (cite: gelles2021polarized): mass, spin, and inclination. Nevertheless, the mass of Sgr A$^*$ is well constrained through stellar dynamics (cite: ghez2008measuring); $M\simeq 4 {\times} 10^6 M_\odot$ where $M_\odot$ denotes solar mass. Furthermore, Fig. [1](#fig:alma_rec) (blue curve) illustrates that the data-fit is not very sensitive to black hole spin: $a\in[0,1]$. Thus, the only remaining unknown is the inclination angle.

To estimate the inclination, we numerically bin $\theta_{\rm o}\in [0,\pi/2]$ and recover the 3D emission for every given (fixed) angle. For each angle, we recover a (locally) optimal 3D emission by minimizing a $\chi^2$ loss over the model parameters. Practically, for numerical stability, we avoid the extreme angles of face-on and edge-on by gridding $\theta_{\rm o}\in[4^\circ, 80^\circ]$ (at $2^\circ$ increments). Figure [1](#fig:alma_rec) plots the validation-$\chi^2$: a robust likelihood approximation for $\theta_{\rm o}$, which appears to favor low inclination angles (details in the Methods section). For each inclination, the recovery is run five times with a random initialization for the 3D structure. Therefore, the error bars are not a measure of posterior uncertainty; rather, they indicate the stability of the locally optimal solution.

An overview of the tomographic data-fitting framework is illustrated in Fig. [3](#fig:overview). Mathematically, the 3D emission volume is estimated by minimizing a $\chi^2$ loss between the observed LP and the model prediction. The continuous 3D emission volume is represented by a coordinate-based, fully-connected, neural network (“neural representation”) and is constrained to a domain with a radius of $6{\rm M} \leq r \leq 20 {\rm M}$ and close to the equatorial disk $|z| \leq 4{\rm M}$ ($6M$ is the innermost stable circular orbit of a non-spinning black hole). The data-fit used in this work relies on the reduced $\chi^2$ definitions of (cite: akiyama2019firstIV). This is not a strict definition of reduced $\chi^2$ that includes degrees of freedom in normalization. Rather, it is normalized by the total number of data points, which is useful for comparing fit quality in our experiments where degrees of freedom remain fixed.

![](figures/ALMA_3D_Recoveries_different_seeds_and_inc.pdf)

The ill-posed inverse problem we solve does not have a unique solution. The recovered 3D structure depends, among other factors, on the assumed inclination angle. Furthermore, solving a non-convex optimization problem with stochastic gradient descent methods leads to a local (and not global) minimum. Thus, the recovered 3D structure also depends on the random initialization of the network weights. Figure [4](#fig:alma_3d_variability) highlights the robustness of the recovered 3D structure across different inclinations and initial conditions. While this is not an exploration of the posterior distribution, the different recoveries give a sense of the solution’s stability. Qualitatively, the details of each recovered structure exhibit dependence on both the inclination angle and initialization. Nevertheless, some key features are consistent across these two axes. While the exact angular extent of the structures is not stable, the azimuthal and radial positions appear stable and consistent with the average structure. Moreover, the separation of the emission into two distinct structures appears consistent across the different recoveries.

To analyse the ability to recover and detect different underlying 3D morphologies, we simulated synthetic datasets mimicking ALMA observations for three underlying 3D structures: `Simple Hotspot`, `Flux Tube`, `Double Source`. Figure [5](#fig:sim_recoveries) highlights the recovery results obtained from these datasets at two (unknown) inclination angles. A comprehensive analysis of the simulated datasets and reconstruction results is given in the Supplementary (Sec. 2).

![](figures/simulated_recoveries_HI_vs_LO_v2_w_subrays.pdf)

## Assumptions and systematic noise

![](figures/ALMA_validation_fit_magnetic_configs_cw_vs_ccw_subkep_frac_3.pdf)

Recovering the 3D structure from light curve observations is highly ill-posed. Thus, the recovery relies on physical constraints and model choices that we impose through the gravitational and synchrotron emission models. The robustness of the results depends on the validity of these model choices, detailed in Table [\[table:1\]](#table:1), and discussed below.

The key assumption for orbital tomography is that the emission is in orbit within an accretion disk, near the equatorial plane, and can be modeled as a simple transformation to a canonical (or initial) 3D emission. Note that small shifts from the equatorial plane are allowed by our model. This enables the formulation of an inverse problem for estimating the 3D emission from observations. We consider orbits characterized by a Keplerian angular velocity profile (neglecting radial or vertical velocity components), accounting for shearing due to differential rotation (ignored by the previous analyses (cite: gravity18; wielgus2022orbital; yfantis2023)) while neglecting the dynamics of cooling, heating, expansion, and turbulence. While this simplifying assumption does not hold in general, it is consistent with theoretical simulations (cite: ripperda2022black), which show consistent structures on short $\sim 1$ orbit timescales.

Furthermore, in modeling synchrotron emission, we assume a homogeneous vertical magnetic field that is externally fixed and is independent of the flare or accretion disk dynamics. The choice of a vertical magnetic field for the fiducial recovery is motivated by the notion that vertical magnetic fields could be powering Sgr A$^*$ flares, apparent in GRMHD simulations that produce magnetic eruption events (cite: ripperda2022black). Moreover, from an observational standpoint, vertical magnetic fields are preferred by both the near infrared analysis of GRAVITY (cite: gravity18; gravity20; Gravity2023) and mm ALMA analysis of (cite: wielgus2022orbital). Nevertheless, the true spatial structure and dynamic properties of the magnetic fields around Sgr A$^*$ are largely unknown.

In Fig. [6](#fig:magnetic_fits_cw_ccw) we analyze some of the systematic model choices detailed above by exploring the effects of a) magnetic field configuration b) rotation direction and c) sub-Keplerian orbits on the data fit and 3D reconstruction. It is important to note that we do not aim to exhaustively test all possible magnetic field and orbital velocity models, but instead highlight the sensitivity of our reconstruction to these model choices. The top-left panel of Fig. [6](#fig:magnetic_fits_cw_ccw) compares the validation-$\chi^2$ for three magnetic field configurations: vertical, radial, and toroidal, respectively denoted by subscripts: $z, r, \phi$. For a radial magnetic field, the best fit recovery is not a compact bright emission region (Fig. [6](#fig:magnetic_fits_cw_ccw) bottom left). Rather, it is a fainter, diffuse structure. Even so, according to the data-fit, and consistent with prior studies, vertical magnetic fields are preferred with a lower validation-$\chi^2$ value.

The center and rightmost panels in Fig. [6](#fig:magnetic_fits_cw_ccw) highlight how clockwise rotation (`CW`) and a Keplerian orbit are favorable to counter-clockwise rotation (`CCW`) or sub-Keplerian orbits, consistent with the analyses of GRAVITY (cite: Gravity2023), and (cite: wielgus2022orbital). To test the fit of orbit direction and sub-Keplerian fraction, we set the angular velocity profile to $\Omega= \pm f_{\rm K}\Omega_{\rm K}$ where the $\pm$ sign dictates the direction (`CW/CCW`) and $f_{\rm K}$ the magnitude ($f_{\rm K}= 1$ results in a clockwise Keplerian orbit). The 3D recovery under $f_{\rm K}= 0.9$ is shown in the bottom-right panel of Fig. [6](#fig:magnetic_fits_cw_ccw), highlighting a broadly consistent recovery with the fiducial model assumptions. However, this consistency eventually breaks down at strong deviations from the Keplarian velocity assumption (also resulting in lower validation-$\chi^2$ values). The top view illustrates how a sub-Keplerian orbit impacts the recovered flare’s radial position.

Another key assumption made by our work is that the millimeter emission region is optically thin. This is consistent with both EHT observations of Sgr A$^*$ (cite: akiyama2022firstII) and their theoretical interpretation (cite: akiyama2022firstIII; akiyama2022firstV). Moreover, theoretical analysis (cite: ripperda2022black) has shown that a “flux tube” flare would be optically thinner due to its higher temperature and lower density compared to the surrounding accretion flow.

Finally, we assume that the recovered emission structure is within the accretion disk. While our model does not account for an alternative jet interpretation, the assumption of accretion flares is consistent with a) theoretical simulations showing powerful equatorial current sheaths associated with flux eruptions forming within the accretion disk (cite: ripperda2022black); b) observational evidence from EHT / VLBI analyses consistent with a compact source model without any detectable jet contribution (cite: akiyama2022firstII; Issaoun2019; cho2022) and c) the GRAVITY detection, indicating an astrometric center aligning with the mass center, implies that the orbiting feature is in proximity to the equatorial plane. The alternative scenario demands a precise alignment between the direction of the jet and the observer’s line of sight.

# Discussion

We present a novel computational approach to image dynamic 3D structures orbiting the most massive objects in the universe. Integrating polarimetric general relativistic ray tracing and neural radiance fields enables resolving a highly ill-posed tomography in the extremely curved space-time induced by black holes. Applying this approach to ALMA observations of Sgr A$^*$ reveals a 3D structure of a flare, with a location broadly consistent with the qualitative analysis presented in (cite: wielgus2022orbital). This first attempt at a 3D reconstruction of a Sgr A$^*$ flare suggests an azimuthally elongated bright structure at a distance of $~11{\rm M}$ trailed by a dimmer source at $~13 {\rm M}$. Although the recovered 3D is subject to, and sometimes sensitive, to the gravitational and emission models, under physically motivated choices, we find that the 3D reconstructions are stable and our approach is successful on simulated data. Moreover, our data-fit metrics provide constraints favoring low inclination angles and clockwise rotation of the orbital plane, supporting the analyses of (cite: wielgus2022orbital), EHT (cite: akiyama2022firstIII), and GRAVITY (cite: gravity18).

Orbital polarimetric tomography shows great promise for 3D reconstructions of the dynamic environment around a black hole. Excitingly, extending the approach and analysis to spatially resolved observations (e.g., EHT) and multi-frequency data could enable relaxing assumptions to further constrain the underlying physical structures that govern the black hole and plasma dynamics (e.g., black hole spin, orbit dynamics, magnetic fields). To that end, future work will likely need to extend our model to non-optically thin media and non-azimuthal velocity patterns. Lastly, by adapting orbital polarimetric tomography to other rich sources of black hole time series observations (e.g., quasars and microquasars), this imaging technology could open the door to population statistics and improve our understanding of black holes and their accretion processes.

+---------------------+-----------------------------------------------------------------------------------------------------------------+
| Emission model      | |                                                       |                                                       |
|                     | |:-----------------------------------------------------:|                                                       |
|                     | |                      Synchrotron                      |                                                       |
|                     | | fixed vertical magnetic field;    optically thin disk |                                                       |
+:====================+:===============================================================================================================:+
| Dynamical model     | |  |                                                                                                            |
|                     | |:--:|                                                                                                          |
|                     | | Keplerian |                                                                                                   |
|                     | | $t_0=$9:20 UT;   clockwise orbit (no radial / vertical velocity);    velocity shear |                         |
+---------------------+-----------------------------------------------------------------------------------------------------------------+
| Gravitational model | |  |                                                                                                            |
|                     | |:--:|                                                                                                          |
|                     | | Kerr |                                                                                                        |
|                     | | mass $= 4.154{\times}10^6 M_\odot$;    non spinning;    $\theta_{\rm o}$ estimated from data |                |
+---------------------+-----------------------------------------------------------------------------------------------------------------+
| 3D model            | |  |                                                                                                            |
|                     | |:--:|                                                                                                          |
|                     | | Neural representation |                                                                                       |
|                     | | Recovery domain: $6{\rm M} \leq r \leq 20 {\rm M}$ (FOV $\approx 200 \mu {\rm as}$);    $|z| \leq 4{\rm M}$ | |
+---------------------+-----------------------------------------------------------------------------------------------------------------+

# Methods

In the following section, we describe our methodology, which is evaluated on synthetic simulations and analyzed in the Supplementary Material.

## Pre-processing

We reduced the ${\sim}100$ minutes of ALMA light curves by time-averaging over ${\sim}1$ minute intervals, resulting in ${\sim}100$ data points for each Stokes component. Following the procedures outlined in (cite: wielgus2022orbital) we subtract a constant LP component with magnitude and angle of $P_{\rm disk}= 0.16~\text{Jy}$, $\xi_{\rm disk}= -37^\circ$ respectively, to account for the background accretion disk; We de-rotate the electric vector polarization angle (EVPA) by $32.2^\circ$ to account for the estimated Faraday rotation (cite: wielgus2022orbital). We model the data as homoscedatic within a short and stable observation window with a polarimetric noise level estimated at $\sigma_Q = \sigma_U = 0.01~\text{Jy}$ (cite: wielgus2022orbital). While we do not fit the total intensity, we regularize the model to have a total intensity around $0.3~\text{Jy}$ with a standard deviation of $0.15~\text{Jy}$ (cite: wielgus2022orbital). Following (cite: wielgus2022orbital) we set 9:20 UT as the initial time of the analysis and 3D reconstruction of the flare. Supplementary Fig. 3 shows an analysis of different initial times around 9:20 UT, which provides further motivation for the selection of this initial time.

## Forward model

In this section, we formulate the forward model, which takes a canonical 3D emission around a black hole as input and synthesizes light curves as output. Figure [3](#fig:overview) provides a high-level overview of the forward model, divided into four key building blocks, which we describe in the sections below.

### 1. Orbit dynamics

The key assumption for orbital tomography is that the 4D (space and time) emission, $e(t,{\bf x})$, is in orbit around the black hole and can be modeled as a simple transformation of a canonical (or initial) 3D emission, $e_0({\bf x})$: $$\begin{equation}
    e(t, {\bf x}) = e_0({\bf T}_t {\bf x}),
\end{equation}$$ The transformation ${\bf T}_t$ propagates the initial 3D structure in time and connects dynamic observations, such as light curves, to the canonical 3D structure. This in turn enables formulating an inverse problem of estimating $e_0({\bf x})$ from time-variable observations. While the assumption of a coordinate transformation does not hold in general, it is well suited for compact, bright structures over short time scales, during which complex dynamics are negligible.

In our work, we consider a Keplerian orbit model with an angular velocity: $$\begin{equation}
\Omega(r) =\frac{\sqrt{M}}{r^{3/2} + a\sqrt{M}},
\label{eq:angular_velocity}
\end{equation}$$ where $r$ is the distance from the black-hole center and $M$ is the black-hole mass. Note that for $a=0$, Eq. [\[eq:angular_velocity\]](#eq:angular_velocity) coincides with the Newtonian expression for angular velocity. A purely azimuthal orbit is suitable outside the innermost stable circular orbit (ISCO), where radial velocities play a smaller role. Thus, we formulate the coordinate transformation as a shearing operation: $$\begin{equation}
    {\bf T}_t = {\bf S}_{\phi},
\end{equation}$$ where ${\bf S}_{\phi}$ is a rotation matrix at an angle: $$\begin{equation}
\phi \left(t, r\right) = (t -t_0)\Omega(r).
\end{equation}$$ The angular velocity dependence on $r$ (Eq. [\[eq:angular_velocity\]](#eq:angular_velocity)) causes shearing due to the faster motion of inner radii.

### 2. Image formation

In this section, we describe how $e_0$ relates to light curve observations through an image-formation model. Each image pixel collects radiation along a geodesic curve: $\Gamma({\bf \Theta}, \alpha, \beta)$ terminating at the image coordinates $(\alpha, \beta)$. The ray path $\Gamma$ is determined by a handful of black hole parameters: ${\bf \Theta}$. Omitting the explicit dependency on image coordinates (for brevity), we model image pixels through the polarized radiative transfer (cite: GRay; grtrans; ipole) of an optically thin disk (attenuation can be neglected for Sgr A$^*$ 230GHz observations (cite: akiyama2022firstV)): $$\begin{equation}
    {\bf p}(t) =     
    \begin{bmatrix}
    p_I(t) \\ p_Q(t) \\ p_U(t) \\ p_V(t)
    \end{bmatrix}
    = \! \! \! \! \! \int \limits_{{\bf x}\in\Gamma({\bf \Theta})} \! \! \! \! \! \! \!g({\bf x})^2  e(t{+}\tau_{\bf x}, {\bf x}) {\bf R}({\bf x}) {\bf J}({\bf x}) d{\bf x}.
    \label{eq:rt}
\end{equation}$$ Equation [\[eq:rt\]](#eq:rt) describes how pixel values are computed through an integration along geodesic curves $\Gamma$ computed by solving a set of differential equations (cite: kgeo2023) (Supplementary Material, Sec. 3). The integrand in comprised of five elements: $g$, $e$, ${\bf R}$ and ${\bf J}$. $e(t{+}\tau_{\bf x}, {\bf x})$ is the *unknown* scalar emissivity that depends on microphysical properties (e.g. local electron density and temperature) and $\tau_{\bf x}$ is the time delay that accounts for photon travel time (often referred to as slow-light). We model the polarized synchrotron radiation as this scalar emissivity function multiplied by a Stokes-vector ${\bf J}$ proportional to (cite: gelles2021polarized) $$\begin{align}
    J_I &\propto g^{\alpha_\nu}\left(|{\bf B}|\sin\phi_B\right)^{\alpha_\nu+1}  \\ 
    J_Q &\propto q_f J_I \\ 
    J_U &= 0
    
    \label{eq:J_factors}
\end{align}$$ In this work, we consider only linear polarization, thus, setting $J_V=0$. Moreover, the spectral index (reflecting the change in the local emission with frequency) is approximated as $\alpha_\nu\simeq1$ (cite: Narayan2021). Note that the local emission frame is defined to align with Stokes-$Q$, therefore, $J_U\equiv0$. The scaling factor $q_f \in [0,1]$ is the (volumetric) fraction of linear polarization and $\phi_B$ is the angle between the local magnetic field $\bf B$ and photon momentum $\bf k$, given by $$\begin{equation}
\sin\phi_B({\bf x}) = \frac{{\bf k}({\bf x}) \times {\bf B}({\bf x})}{\left|{\bf k}({\bf x})\right|\left| {\bf B}({\bf x}) \right|}
\end{equation}$$ The two remaining quantities to define are ${\bf R}$ and $g$. The matrix ${\bf R}$ rotates the LP, $(J_Q, J_U)$, from the emission frame to the image coordinates through *parallel-transport* (cite: himwich2020universal) (see Supplementary Material Sec. 3.4). The scalar field $g({\bf x})$ is a General Relativistic (GR) red-shift factor, which decreases the emission when the material is deep in the gravitational field or moving away from the observer. More generally $g({\bf x})$ depends on the local direction of motion, ${\bf u}$, relative to the photon momentum ${\bf k}$ $$\begin{equation}
g({\bf x}) = \big\langle {\bf u}({\bf x}),{\bf k}({\bf x}) \! \big\rangle
\end{equation}$$ Note that ${\bf u},{\bf k}$ are 4-vectors, more explicitly defined in the Supplementary Material (Sec. 3).

### 3. Light curves

For a given 3D emission, ray-tracing Eq. [\[eq:rt\]](#eq:rt) enables computing a single pixel value over time. We compute light curves by numerically sampling a large field-of-view (FOV) and summing over image-plane coordinates: $$\begin{equation}
    {\bf I}(t) =     
    \begin{bmatrix}
    I_I(t) \\ I_Q(t) \\ I_U(t) \\ I_V(t)
    \end{bmatrix} =
    \sum\limits_{\alpha, \beta} {\bf p}(t, \alpha, \beta)
    \label{eq:lc}
\end{equation}$$

### 4. Neural representation

We formulate a tomographic recovery relying on a *neural representation* (cite: levis2022gravitationally; mildenhall2020nerf) of the unknown 3D volume: $e_0({\bf x})$. Thus, instead of a traditional voxel discretization, the volume is represented by the weights, ${\bf w}$, of a multilayer perceptron (MLP), that are adjusted to fit the observations.

The implicit regularization of the multilayer perceptron (MLP) architecture enables tackling highly ill-posed inverse problems (cite: levis2022gravitationally; zhong2021cryodrgn). The MLP takes continuously-valued coordinates ${\bf x}$ as input, and outputs the corresponding scalar emission at that coordinate: $$\begin{equation}
    e_0 \left({\bf x}\right) = \operatorname{MLP}_{{\bf w}}(\gamma({\bf x})),
    \label{eq:MLP}
\end{equation}$$ where $\gamma({\bf x})$ is a positional encoding of the input coordinates.

Studies have shown (cite: tancik2020fourfeat) that encoding the coordinates, instead of directly taking them as inputs, can capture continuous fields better (converging in the width limit to a stationary interpolation kernel (cite: jacot2018neural)). Thus, our work relies on a positional encoding that projects each coordinate onto a set of sinusoids with exponentially increasing frequencies: $$\begin{equation}
    \gamma({\bf x}) {=} \Big[ \sin({\bf x}), \cos({\bf x}), \ldots 
    ,\sin\!\big(2^{L-1} {\bf x}\big), \cos\!\big(2^{L-1} {\bf x}\big) \Big]^T
\end{equation}$$ The positional encoding controls the underlying interpolation kernel used by the MLP, where the parameter $L$ determines the bandwidth of the interpolation kernel (cite: tancik2020fourfeat).

In our work, we use a small MLP with 4 fully connected layers, where each layer is 128 units wide and uses ReLU activations. We use a maximum positional encoding degree of $L=3$. The low degree of $L$ is suitable for volumetric emission fields, which are naturally smooth (cite: levis2022gravitationally).

Once the neural network weights, ${\bf w}$, are adjusted to fit the data, the network can be sampled at any 3D point, ${\bf x}$, to produce the emission value at that point. This allows us to: a) sample the network at regular grid points to extract a 3D volume representation of the recovered emission; b) ray trace the recovered emission as it would be seen by a perspective (pin-hole) camera (used for the visualizations throughout the paper).

## Solving the inverse problem

In this section, we formulate an optimization approach that enables jointly estimating the 3D emission and inclination, which are the parameters of the forward model. Supplementary Fig. 1 shows a high-level illustration of the data-fitting procedure introduced in the following section.

### Tomographic reconstruction

To estimate the 3D emission from light curve observations, we formulate a minimization problem. We estimate ${\bf w}$, which parameterizes $e_0({\bf x})$, by minimizing a $\chi^2$ data fit for each Stokes component, evaluated for a fixed set of black hole parameters, ${\bf \Theta}$: $$\begin{equation}
    \mathcal{\chi}^2({\bf w}|{\bf \Theta}) = \mathcal{\chi}^2_I({\bf w}|{\bf \Theta}) + \mathcal{\chi}^2_Q({\bf w}|{\bf \Theta}) + \mathcal{\chi}^2_U({\bf w}|{\bf \Theta}).
    \label{eq:chisq}
\end{equation}$$ Here, we restrict the discussion to the total intensity and LP components: $I, Q, U$. Each $\chi^2$ is calculated as a sum over discrete temporal data points $$\begin{equation}
    \mathcal{\chi}^2_s({\bf w}|{\bf \Theta}) = \frac{1}{N_{\rm obs}}\sum \limits_i \left( \frac{{\bf y}_s(t_i) - I_s(t_i, {\bf w}|{\bf \Theta})}{\sigma_s} \right)^2,
    \label{eq:chisq_stokes}
\end{equation}$$ where $N_{\rm obs}$ is the total number of data points and the subscript $s=\left\{ I, Q, U, V \right\}$ represents the stokes components, ${\bf y}_s$, $I_s$ and $\sigma_s$ are the polarimetric observations, model, and noise standard deviation, respectively. Note that $I_s(t_i, {\bf w}|{\bf \Theta})$ is simply the light curve given by Eq. [\[eq:lc\]](#eq:lc), sampled at discrete time $t_i$, where ${\bf w}|{\bf \Theta}$ highlight its dependency/conditioning on the network/black hole parameters.

Equation [\[eq:chisq\]](#eq:chisq) depends on *unknown* black hole parameters; nevertheless, the mass of Sgr A$^*$ can be constrained through stellar dynamics (cite: ghez2008measuring; abuter2022mass); $M\simeq 4 {\times} 10^6 M_\odot$ where $M_\odot$ denotes solar masses. Furthermore, since the data fit is insensitive to black hole spin, the only estimated parameter is the inclination angle. To estimate the inclination, we numerically bin $\theta_{\rm o}\in [0,\pi/2]$ and recover the 3D emission by minimizing Eq. [\[eq:chisq\]](#eq:chisq): $$\begin{equation}
{\bf w}^\star (\theta_{\rm o}) = \arg \min_{\bf w}\chi^2\left({\bf w}|\theta_{\rm o}\right).
\label{eq:minimization}
\end{equation}$$ By interpreting Eq. [\[eq:minimization\]](#eq:minimization) as a function of $\theta_{\rm o}$ we approximate the marginal log-likelihood as $$\begin{equation}
\mathcal{L} (\theta_{\rm o}|{\bf y}) \propto \chi^2(\theta_{\rm o}|{\bf w}^\star).
\label{eq:theta_likelihood}
\end{equation}$$ Equation [\[eq:theta_likelihood\]](#eq:theta_likelihood) is a zero-order expansion about the maximum likelihood estimator: ${\bf w}^\star$.

### Model selection using Validation-$\chi^2$

While Eq. [\[eq:theta_likelihood\]](#eq:theta_likelihood) tells us how well each model (inclination) fits the data, it is susceptible to over-fitting. To mitigate over-fitting, we define a more robust metric called *validation-$\chi^2$* (see Supplementary Fig. 5). The inclination angle is then estimated through the following procedure:

1.  During optimization, ray positions are fixed to the center of each image pixel. In our recoveries, we use an evenly sampled $64\times64$ grid for a FOV of $200~\mu {\rm as}$.

2.  We compute $\chi^2$ for perturbed pixel positions (off-center) within a small pixel area. In our recoveries, we used a pixel area of $3.125 \times 3.125~\mu {\rm as}^2$.

3.  We average $\chi^2$ of 10 randomly sampled (uniform) ray positions to compute validation-$\chi^2$ curves.

4.  $\theta_{\rm o}^\star$ is estimated as the global minimum of the validation $\chi^2$.

Through simulations, we highlight how this procedure is a more robust selection criterion for models that are not overfitting the fixed ray positions (Supplementary Fig. 5).

### Optimization procedure

The neural network was implemented in `JAX` (cite: jax2018github). Both the synthetic experiments (Supplementary Material, Sec. 2) and the ALMA recovery were optimized using an ADAM optimizer (cite: kingma2014adam) with a polynomial learning rate transitioning from $1{\rm e}^{-4} \rightarrow 1{\rm e}^{-6}$ over $50{\rm K}$ iterations. Run times were ${\sim} 1$ hour on two NVIDIA Titan RTX GPUs. Network weights were randomly initialized (Gaussian distributed) with several initial seeds.

# Data Availability

This paper makes use of the ALMA data set ADS/JAO.ALMA#2016.1.01404.V, available through the ALMA data portal. Fully calibrated data and other materials are available from the corresponding author upon reasonable request.

# Code Availability

The software packages used analyze the data are available at the following sites: `kgeo` (<https://github.com/achael/kgeo>), `bhnerf` (<https://github.com/aviadlevis/bhnerf>).

# Acknowledgements

We would like to thank Vikram Ravi and Bart Ripperda for fruitful discussions. This work was supported by NSF awards 1935980, 2048237, and the Carver Mead New Adventures Fund. A. A. C. is supported by the Princeton Gravity Initiative. M. W.’s research is supported by the ERC advanced grant “M2FINDERS - Mapping Magnetic Fields with INterferometry Down to Event hoRizon Scales” (Grant No. 101018682)

# Author Contributions

A. L. and K. L. B. identified and formulated the tomography problem and conceived and designed the experiments. A. L., K. L. B., and P. P. S. developed the neural representation-based tomography approach. A. A. C. and A. L. developed the polarimetric ray tracing. A. A. C formulated and implemented the geodesic computations. M. W. worked on data calibration. A. L. performed the tomographic reconstructions. All authors contributed to the analysis, interpretation, discussions, and writing of the manuscript.

# Competing interests

The authors declare no competing interests.

10

(ref: genzel2003near) R. Genzel, R. Schödel, T. Ott, A. Eckart, T. Alexander, F. Lacombe, D. Rouan, and B. Aschenbach. Near-infrared flares from accreting gas around the supermassive black hole at the Galactic Centre. , 425(6961):934-937, 2003.

(ref: neilsen2013chandra) J. Neilsen, M. A. Nowak, C. Gammie, J. Dexter, S Markoff, D. Haggard, S. Nayakshin, Q. D. Wang, N. Grosso, D. Porquet, et al. A Chandra/HETGS Census of X-ray Variability From Sgr A$^{*}$ during 2012. , 774(1):42, 2013.

(ref: fazio2018multiwavelength) G. G. Fazio, J. L. Hora, G. Witzel, S. P. Willner, M. L. N. Ashby, F. Baganoff, E. Becklin, S. Carey, D. Haggard, C. Gammie, et al. Multiwavelength Light Curves of Two Remarkable Sagittarius A$^{*}$ Flares. , 864(1):58, 2018.

(ref: Wielgus2022lc) M. Wielgus, N. Marchili, I. Martı́-Vidal, G. K. Keating, V. Ramakrishnan, P. Tiede, E. Fomalont, S. Issaoun, J. Neilsen, M. A. Nowak, et al. . , 930(2):L19, 2022.

(ref: Marrone_2008) D. P. Marrone, F. K. Baganoff, M. R. Morris, J. M. Moran, A. M. Ghez, S. D. Hornstein, C. D. Dowell, D. J. Muñoz, M. W. Bautz, G. R. Ricker, W. N. Brandt, G. P. Garmire, J. R. Lu, K. Matthews, J. H. Zhao, R. Rao, and G. C. Bower. . , 682(1):373–383, 2008.

(ref: Haggardetal2019) D. Haggard, M. Nynka, B. Mon, N. de la Cruz Hernandez, M. Nowak, C. Heinke, J. Neilsen, J. Dexter, P. Chris Fragile, F. Baganoff, G. C. Bower, L. R. Corrales, F. Coti Zelati, N. Degenaar, S. Markoff, M. R. Morris, G. Ponti, N. Rea, J. Wilms, and F. Yusef-Zadeh. . , 886(2):96, 2019.

(ref: dexter2020sgr) J. Dexter, A. Tchekhovskoy, A. Jiménez-Rosales, S. M. Ressler, M. Bauböck, Y. Dallilar, P. T. de Zeeuw, F. Eisenhauer, S. von Fellenberg, F. Gao, R. Genzel, S. Gillessen, M. Habibi, T. Ott, J. Stadler, O. Straub, and F. Widmann. . , 497(4):4999–5007, 2020.

(ref: Witzel_2021) G. Witzel, G. Martinez, S. P. Willner, E. E. Becklin, H. Boyce, T. Do, A. Eckart, G. G. Fazio, A. Ghez, M. A. Gurwell, D. Haggard, R. Herrero-Illana, J. L. Hora, Z. Li, J. Liu, N. Marchili, M. R. Morris, H. A. Smith, M. Subroweit, and J. A. Zensus. . , 917(2):73, 2021.

(ref: broderick2005imaging) A. E. Broderick and A. Loeb. . , 363(2):353–362, 2005.

(ref: ripperda2022black) B. Ripperda, M. Liska, K. Chatterjee, G. Musoke, A. A. Philippov, S. B. Markoff, A. Tchekhovskoy, and Z. Younsi. Black hole flares: ejection of accreted magnetic flux through 3D plasmoid-mediated reconnection. , 924(2):L32, 2022.

(ref: gravity18) GRAVITY Collaboration. . , 618:L10, 2018.

(ref: gravity20) GRAVITY Collaboration. . , 635:A143, 2020.

(ref: wielgus2022orbital) M. Wielgus, M. Moscibrodzka, J. Vos, Z. Gelles, I. Martı́-Vidal, J. Farah, N. Marchili, C. Goddi, and H. Messias. . , 665:L6, 2022.

(ref: akiyama2022firstI) Event Horizon Telescope Collaboration. . , 930(2):L12, 2022.

(ref: akiyama2022firstVI) Event Horizon Telescope Collaboration. . , 930(2):L17, 2022.

(ref: akiyama2022firstIII) Event Horizon Telescope Collaboration. . , 930(2):L14, 2022.

(ref: akiyama2022firstII) Event Horizon Telescope Collaboration. . , 930(2):L13, 2022.

(ref: Tiede_2020) P. Tiede, H. Y. Pu, A. E. Broderick, R. Gold, M. Karami, and J. A. Preciado-López. . , 892(2):132, 2020.

(ref: levis2021inference) A. Levis, D. Lee, J. A. Tropp, C. F.  Gammie, and K. L. Bouman. Inference of Black Hole Fluid-Dynamics from Sparse Interferometric Measurements. In *Proc. IEEE/CVF Intl. Conf. Comput. Vision (ICCV)*, 2340–2349, 2021.

(ref: levis2022gravitationally) A. Levis, P. P. Srinivasan, A. A. Chael, R. Ng, and K. L. Bouman. Gravitationally Lensed Black Hole Emission Tomography. In *Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR)*, 19841–19850, 2022.

(ref: mildenhall2020nerf) B. Mildenhall, P. P. Srinivasan, M. Tancik, J. T. Barron, R. Ramamoorthi, and R. Ng. NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis. , 2020.

(ref: tancik2020fourfeat) M. Tancik, P. P. Srinivasan, B. Mildenhall, S. F. Keil, N. Raghavan, U. Singhal, R. Ramamoorthi, J. T. Barron, and R. Ng. Fourier Features Let Networks Learn High Frequency Functions in Low Dimensional Domains. , 33:7537-7547, 2020.

(ref: Gravity2023) Gravity Collaboration. . , 677:L10, 2023.

(ref: gelles2021polarized) Z. Gelles, E. Himwich, M. D. Johnson, and D. C. M. Palumbo. Polarized image of equatorial emission in the Kerr geometry. , 104(4):044060, 2021.

(ref: vos2022polarimetric) J. Vos, M. A. Mościbrodzka, and M. Wielgus. . , 668:A185, 2022.

(ref: yfantis2023) A. I. Yfantis, M. A. Mościbrodzka, M. Wielgus, J. T. Vos, A. Jimenez-Rosales. . , 2310.07762, 2023.

(ref: akiyama2022firstV) Event Horizon Telescope Collaboration. . , 930(2):L16, 2022.

(ref: ghez2008measuring) A. M. Ghez, S. Salim, N. N. Weinberg, J. R. Lu, T. Do, J. K. Dunn, K. Matthews, M. R. Morris, S. Yelda, E. E. Becklin, et al. Measuring Distance and Properties of the Milky Way’s Central Supermassive Black Hole with Stellar Orbits. , 689(2):1044, 2008.

(ref: akiyama2019firstIV) Event Horizon Telescope Collaboration. . , 875(1):L4, 2019.

(ref: Issaoun2019) S. Issaoun, M. D. Johnson, L. Blackburn, C. D.  Brinkerink, M. Mościbrodzka, A. Chael, C. Goddi, I. Martí-Vidal, J.  Wagner, S. S. Doeleman, H Falcke. . , 871(1):30, 2019.

(ref: cho2022) I. Cho, G. Y. Zhao, T. Kawashima, M. Kino, K. Akiyama, M. D. Johnson et al.. . , 926(2):108, 2022.

(ref: GRay) CK. Chan, D. Psaltis, and F. Özel. . , 777(1):13, 2013.

(ref: grtrans) J. Dexter. . , 462(1):115–136, 2016.

(ref: ipole) M. Mościbrodzka and C. F. Gammie. . , 2018.

(ref: kgeo2023) A Chael. kgeo (version 1.0.0). <https://github.com/achael/kgeo>, 2023. Online; accessed 01-June-2023.

(ref: Narayan2021) R. Narayan, D. C. M.  Palumbo, M. D. Johnson, Z. Gelles, E. Himwich, D. O. Chang, A. Ricarte, J. Dexter, C. F. Gammie, A. A. Chael, and Event Horizon Telescope Collaboration. . , 912(1):35, 2021.

(ref: himwich2020universal) E. Himwich, M. D. Johnson, A. Lupsasca, and A. Strominger. Universal polarimetric signatures of the black hole photon ring. , 101(8):084020, 2020.

(ref: zhong2021cryodrgn) E. D. Zhong, T. Bepler, B. Berger, and J. H. Davis. CryoDRGN: reconstruction of heterogeneous cryo-EM structures using neural networks. , 18(2):176–185, 2021.

(ref: jacot2018neural) A. Jacot, F. Gabriel, and C. Hongler. Neural Tangent Kernel: Convergence and Generalization in Neural Networks. , 31, 2018.

(ref: abuter2022mass) R Abuter, N Aimar, A Amorim, J Ball, M Bauböck, JP Berger, H Bonnet, G Bourdarot, W Brandner, V Cardoso, et al. Mass distribution in the galactic center based on interferometric astrometry of multiple stellar orbits. , 657:L12, 2022.

(ref: jax2018github) J. Bradbury, R. Frostig, P. Hawkins, M. J. Johnson, C. Leary, D. Maclaurin, G. Necula, A. Paszke, J. VanderPlas, S. Wanderman-Milne, and Q. Zhang. : composable transformations of Python+NumPy programs, 2018. (ref: kingma2014adam) D. P. Kingma and J. Ba. Adam: A Method for Stochastic Optimization. In *International Conference for Learning Representations (ICLR)*, 2015.

In this work, we formulate a novel approach for estimating an evolving 3D structure around a black hole from light curve observations. To solve a tomography from a single viewpoint, we rely on both radiative emission and gravitational physics around the black hole. Integrating these physical models with a neural representation of the unknown 3D structure enables solving a highly ill-posed inverse problem, which we term *orbital polarimetric tomography*. By scanning over a range of possible inclination angles, we jointly estimate the inclination angle and 3D structure that best fit the polarimetric light curve data. Supplementary Fig. [7](#fig:datafit_illustration) shows an overview of the data-fitting procedure.

In the supplementary material we a) detail our evaluation of the orbital polarimetric tomography on synthetic simulations and b) add additional details and context for the general relativistic ray tracing. The organization is as follows: Sec [1](#sec:synthetic_gen) describes the data generation, Sec. [2](#sec:synthetic_rec) analyses the recovery results, and Sec. [3](#sec:GR) covers additional details for general relativistic ray tracing, not included in the main text.

![](figures/illustration_lightcurves.pdf)

# Synthetic data generation

To quantitatively assess our approach and the ability to recover the 3D structures and constrain an unknown inclination angle we generate synthetic data mimicking ALMA observations. Synthetic simulations allow for careful control of the sources of variability to evaluate the overall impact on the recovery performance. Each dataset consists of a flare on top of a background accretion disk as described in the following sections.

## Emission flares

![](figures/3D_cases.pdf)

![](figures/chi2_initial_t.pdf)

We generate data consisting of three distributions of emission: `Simple Hotspot`, `Flux Tube`, `Double Source` (Supplementary Fig. [8](#fig:3d_cases)). Each volume spans a $40 \times 40 \times 40~[{\rm M}^3]$ cube with emission occupying an equatorial disk of $\sim 4-6M$ thickness. For these simulations, we assume a non-spinning black hole with a constant vertical magnetic field ${\bf B}({\bf x})=\hat{\bf z}B_{z}$. We model flares with high fractional polarization resulting in average fluxes matching the real ALMA data (cite: wielgus2022orbital_supp) $$\begin{align}
    \bar{I}_I &\simeq 0.3-0.4 ~\text{Jy}, \label{eq:flux_req_I} \\
    \bar{P} &= \sqrt{I_Q^2 + I_U^2} \simeq 0.1-0.15 ~\text{Jy}.
    \label{eq:flux_req_P}
\end{align}$$ Image frames and subsequent light curves are computed by discretizing an FOV of $40M$ (${\sim} 200 \mu {\rm as}$ for Sgr A$^*$) into $64{\times}64$ pixels. To reduce aliasing, each pixel value is computed by ray-tracing and averaging 10 sub-pixel rays, sampled uniformly within the pixel fov. For each 3D structure, observations are generated at two inclination angles: $\theta_{\rm o}^{\rm lo}=12^\circ$ and $\theta_{\rm o}^{\rm hi}=64^\circ$ resulting in a dataset of six polarimetric light curve observations. Supplementary Fig. [8](#fig:3d_cases) shows the 3D geometry and a sample of ray traced frames.

Based on our analysis of the validation-$\chi^2$ for different initial times around 9:20 UT, we set the initial time of the flare to 9:20 UT, where the $\chi^2$ of the ALMA data-fitting is lowest (Supplementary Fig. [9](#fig:chi2_init_t)). For each simulated emission structure, we synthesize $\sim 100$ minutes of observations to mimic the time-averaged ALMA observations. We use a sampling cadence of $\sim1$ data point per minute with appropriate scan gaps taken from the observational data.

To produce fluxes that are comparable to ALMA observed fluxes, we adjust the magnitude of the 3D emission structure and the volumetric LP fraction to satisfy Eqs. [\[eq:flux_req_I\]](#eq:flux_req_I)–[\[eq:flux_req_P\]](#eq:flux_req_P). We use a $q_f=0.85$ to generate observations at $\theta_{\rm o}^{\rm lo}$ and $q_f=0.5$ for $\theta_{\rm o}^{\rm hi}$; A lower $q_f$ is used at a high inclination to account for the stronger Doppler boosting.

## Accretion disk

![](figures/accretion_illustration.pdf)

While ALMA observations have low instrumental noise ($\sim2$ orders of magnitude less than the signal), a significant source of systematic noise is the unaccounted-for variability of the background accretion disk. To assess the impact the background signal has on reconstructions we generate synthetic data of a dynamic accretion disk. We model the accretion disk as a stochastic flow designed to mimic the statistics around Sgr A$^*$ (cite: akiyama2022firstIII_supp; levis2021inference_supp). The 2D spiral flow is generated as a Gaussian Random Field (GRF) (cite: lee2021disks_supp) which is inflated to 3D through convolution with a 1D vertical Gaussian kernel with a full-width half max (FWHM) of $2.35{\rm M}$. Subsequently, the 3D flow is gravitationally lensed (with the same ray-tracing procedure described for the foreground emission flares) to generate a polarized image plane. Supplementary Fig. [10](#fig:accretion_illustration) illustrates the 3D evolution of a randomly sampled `Accretion Disk` alongside the `Simple Hotspot`. Furthermore, the image plane containing both components is shown at two different evolution times.

# Synthetic data recovery

In this section, we study the recovery performance through experiments designed to highlight different aspects of the tomography approach. In all recoveries, the 3D structure is visualized by sampling the network on a 3D grid at a resolution of $\sim 0.15{\rm M}$. The visualized volumes are in-fact the estimated intrinsic 3D emission (without spacetime curvature).

## Estimating inclination

![](figures/HI_LO_train_val_logloss.pdf)

Using the `Simple Hotspot` model with background accretion noise ($\sigma_P$) we show how the conditional $\chi^2(\theta_{\rm o}|{\bf w}^\star)$ enables differentiating $\theta_{\rm o}^{\rm lo}$ from $\theta_{\rm o}^{\rm hi}$ (Supplementary Fig. [11](#fig:train_val_loss)). The right panel of Supplementary Fig. [11](#fig:train_val_loss) highlights the overfitting gap, illustrating how low inclination angles are prone to overfitting. Intuitively, this is because a high inclination provides a stronger physical constraint, requiring the 3D emission to “disappear” behind the black hole for parts of the orbit. Nevertheless, the validation curves mitigate over-fitting and enable estimating $\theta_{\rm o}^\star$ (as the global minimum) to within $\pm10^\circ$ of the underlying true inclination. This is because overfit structures do not generalize as well and are less stable under perturbations to pixel positions on the image plane.

## Sensitivity to background noise

![](figures/simple_gaussian_w_noise_v3.pdf)

In reality, observed variability is due to both the flare and accretion, however, it is difficult to determine the relative contributions of each source. Any un-modeled accretion dynamics will impact recovery results as our model fully attributes dynamics to orbital motion. We explore this aspect by sampling random fields that mimic an accretion process with varying degree of polarization ($q_f=\{0.25, 0.5, 0.75\}~{\rm Jy}$) producing noise light curves with $\sigma_P=\{0.01, 0.03, 0.06\}~{\rm Jy}$. Similar to the pre-processing of ALMA data (cite: wielgus2022orbital_supp), we subtract the time-averaged LP component (the static component of the background emission). A comparison between the simulated `Simple Hotspot` flare and accretion disk light curves, for different levels of variability, is shown in Supplementary Fig. [12](#fig:simple_hs_w_noise) (top panels). In these simulations, the underlying true inclination is $\theta_{\rm o}^{\rm lo}$. For each level of noise, $\sigma_P$, we are able to estimate $\theta_{\rm o}^\star$ to within $\pm4^\circ$ of the true value.

using the validation-$\chi^2$ minimum, our approach is able to recover the inclination angle to within $\pm4^\circ$ of the true value (see $\chi^2$ curves at the bottom of Supplementary Fig. [12](#fig:simple_hs_w_noise)). Subsequently, using the estimate $\theta_{\rm o}^\star$, we recover the unknown 3D emission. Supplementary Fig. [12](#fig:simple_hs_w_noise) (middle row) shows a comparison between the recovered 3D emission and the ground truth. As the unaccounted disk variability increases, more emission is attributed sporadically within the volume. Nevertheless, the compact hotspot remains the brightest feature in the recovered 3D volume centered around the true azimuthal position.

## Recovering different 3D morphology

![](figures/inc_validation_HI_LO_noise_analysis.pdf)

![](figures/simulated_recoveries_HI_vs_LO_v2_w_subrays.pdf)

In these simulations, we highlight the tomographic ability to recover different underlying emission structures and distinguish between different 3D flare morphologies.

For each of the datasets we add accretion disk noise with $\sigma_P=0.01~\text{Jy}$ and estimate the inclination angle, $\theta_{\rm o}^\star$ as the minimum in the validation-$\chi^2$ (curves are given in Supplementary Fig. [13](#fig:sim_recoveries_incval)). Our approach is able to estimate $\theta_{\rm o}^{\rm lo}$ to within $\pm 6^\circ$ for all three levels of accretion noise and 3D fiducial datasets. While low and moderate accretion noise enable detection $\theta_{\rm o}^{\rm hi}$ to within $\pm 16^\circ$, it is difficult to estimate $\theta_{\rm o}^{\rm hi}$ under high accretion noise. Nonetheless, even with high accretion noise, the trends of the validation-$\chi^2$ curves enable a robust binary detection of low vs high inclinations.

Supplementary Fig. [14](#fig:sim_recoveries1) highlights how our approach is able to simultaneously estimate an unknown inclination and 3D structure from unresolved light curve observations. In each case, the recovered 3D captures the unique morphology of the underlying ground truth structure and is smoothed out by the tomographic reconstruction process.

It is instructive to visualize noise present in the 3D reconstructions. To illustrate noisy features we recover the 3D volume of a stochastic disk, without an orbiting bright flare, from light curve observations. In these recoveries the dynamic signal does not conform to the model assumptions made by the orbital tomography algorithm as brightness does not merely orbit and shear but also appears and disappears. Supplementary Fig. [15](#fig:inoisy_rec) demonstrates the 3D reconstructions with different random seeds (initial conditions for the neural network / 3D volume). Under certain initializations compact emission may appear, however, in contrast to the reconstructions of flares, these components are not stable. The consistent artifacts at the boundary, also present in the real data reconstructions (Figs. 1, 4 of the main text), suggest these are likely an artifact of the reconstruction algorithm.

![](figures/inoisy_3D_Recoveries.pdf)

## Recovery blind spot

![](figures/two_gaussians.pdf)

Close to the event horizon, gas is orbiting at relativistic velocities resulting in a substantial Doppler boosting effect, Doppler boosting effects are particularly strong at high inclination angles where emission moving away appears very faint compared to emission moving towards the observer. This is clearly illustrated in Supplementary Fig. [8](#fig:3d_cases) where one of the bright spots in the `Double Source` images is extremely faint due to the clockwise rotational motion. For this reason, we anticipate that reconstruction errors will not be distributed equally across the orbital plane.

To test this hypothesis we simulate observations with two sources, one at a fixed `11 o’clock` azimuthal position and the other at variable `2/4/8 o’clock` positions (Supplementary Fig. [16](#fig:two_gaussians)). The recoveries shown in Supplementary Fig. [16](#fig:two_gaussians) reveal an “invisible region” at high inclination angles where sources are dim due to Doppler boosting. Due to recovery blurring, bright features that are close together merge to form a single region (see `2/4/8 o’clock` positions in Supplementary Fig. [16](#fig:two_gaussians)). Nevertheless, these regions contain two distinct brightness peaks attributed to the two hotspots. Doppler boosting is weaker at low inclination angles which are favored by the real data fit.

# General Relativistic Ray Tracing

This section describes the General Relativistic (GR) equations used to compute geodesic paths and polarized radiative transfer.

## Kerr metric

We work in the Kerr black hole spacetime in units where $G=c=1$. A Kerr black hole has mass $M$ and spin $a$. We use Boyer-Lindquist coordinates, where points in the spacetime are indicated by a four-vector $x^\mu=(t,r,\theta,\phi)$.

The structure of spacetime is encoded in the metric $g_{\mu\nu}$, which is a $4\times4$ symmetric matrix. In Boyer-Lindquist coordinates, the nonzero components of the metric are $$\begin{align}
g_{tt} &= -(1-2Mr/\Sigma)  \\
g_{rr} &= \Sigma/\Delta \\
g_{\theta\theta} &= \Sigma \\
g_{\phi\phi} &= \Pi\sin^2\theta/\Sigma \\
g_{t\phi} &= g_{\phi t} = -2Mar\sin^2\theta/\Sigma.
\end{align}$$ where the following are commonly used abbreviations. $$\begin{align}
    \Delta &= r^2 +a^2 - 2Mr \\
    \Sigma &= r^2 + a^2\cos^2\theta \\
    \Pi &= (r^2 +a^2)^2 - a^2\Delta \sin^2\theta \\
    \omega &= 2aMr/\Pi.
\end{align}$$ The nonzero components of the inverse metric $g^{\mu\nu}$ are $$\begin{align}
g^{tt} &= -\Pi/\Delta\Sigma \\
g^{rr} &= \Delta/\Sigma \\
g^{\theta\theta} &= 1/\Sigma \\
g^{\phi\phi} &= (\Delta-a^2\sin^2\theta)/(\Delta\Sigma\sin^2\theta) \\
g^{t\phi} &= g^{\phi t} = -2Mar/\Delta\Sigma.
\end{align}$$

## Ray tracing

We define the image plane of the observer at time $t=0$, at radius $r_o\rightarrow \infty$, and at an inclination angle $\theta_o$ to the angular momentum axis of the black hole (BH). We use Cartesian coordinates $(\alpha,\beta)$ on the image plane, measured in units of $M$. Restoring physical units, the image plane coordinates are in radians with the scale given by $GM/Dc^2$ where $D$ is the distance to the BH. Time is measured in units of $GM/c^3$. The origin $\alpha=\beta=0$ is the line of sight to the black hole at $r=0$, and the $+\beta$ image plane axis is parallel with the BH spin direction (i.e. with the $-\theta$ direction).

We solve for the trajectories of photons backward from a specific position $(\alpha,\beta)$ on the image plane using a set of differential equations which in Einstein notation can be written as: $$\begin{equation}
    \frac{dx^\mu}{d\sigma} = k^\mu.
    \label{eq:ode}
\end{equation}$$ Here $\sigma$ is the path parameter (“affine time”) and $$\begin{equation}
    x^\mu(\sigma) = \left(t(\sigma), r(\sigma), \theta(\sigma), \phi(\sigma) \right),
\end{equation}$$ is a parameterized trajectory in spherical (Boyer-Lindquist) coordinates.

Each photon trajectory is defined by three *constants of motion*: $(E,\lambda,\eta)$. $E$ is photon energy at infinity (i.e., observed frequency). The parameters $\lambda$ (angular momentum) and $\eta$ (Carter constant) are fully determined by the photon’s coordinates on the observer screen: $$\begin{align}
    \lambda &= -\alpha\sin\theta_o \\
    \eta &= (\alpha^2-a^2)\cos^2\theta_o + \beta^2.
\end{align}$$ From these constants, at each point along the trajectory, the photon’s *covariant momentum* (lower index) $k_\mu$ is given by (cite: gralla2020null_supp): $$\begin{align}
\label{eq:photonmomentum0}
    k_t &= -E \\
    k_r &= \pm E \sqrt{\mathcal{R}(r)} / \Delta \\
    k_\theta &= \pm E \sqrt{\Theta(\theta)} \\
    k_\phi &= E\lambda,
    \label{eq:photonmomentum1}
\end{align}$$ where $\mathcal{R}$ and $\Theta$ are *radial and polar potentials*: $$\begin{align}
    \mathcal{R}(r) &= (r^2 + a^2 - a \lambda)^2 - \Delta\left[\eta + (\lambda-a)^2\right]\\
    \Theta(\theta) &= \eta + a^2\cos^2\theta - \lambda^2/\tan^2\theta.
\end{align}$$ The choice of $\pm$ sign in Eq ([\[eq:photonmomentum0\]](#eq:photonmomentum0)–[\[eq:photonmomentum1\]](#eq:photonmomentum1)) depends on the direction of motion (signs reverse at angular and radial turning points when $k^\theta=0$ or $k^r=0$, respectively.).

Equation [\[eq:ode\]](#eq:ode) is described in terms of the *contravariant* (upper index) momentum vector $k^\mu$, which is obtained by multiplying the *covariant* momentum (Eqs. [\[eq:photonmomentum0\]](#eq:photonmomentum0)–[\[eq:photonmomentum1\]](#eq:photonmomentum1)) by the inverse metric $$\begin{equation}
k^\mu = g^{\mu\nu}k_\nu.
\end{equation}$$ To compute geodesic paths $x^\mu(\sigma)$, we solve Eq. [\[eq:ode\]](#eq:ode) using the explicit parametric form described by (cite: gralla2020null_supp) and implemented in (cite: kgeo2023_supp).

## Fluid Velocity and Redshift

Outside the ISCO, the four-velocity $u^\mu$ of prograde circular orbits in the equatorial plane is $u^\mu(r)$, where: $$\begin{align}
    u^t &= u^t \\
    u^r &= 0 \\
    u^\theta &= 0 \\
    u^\phi &= u^t\Omega,
\end{align}$$ Since the four-velocity must be normalized so that $u^\mu u_\mu = g_{\mu\nu}u^\mu u^\nu=-1$, $$\begin{align}
    u^t &= \frac{1}{\sqrt{-g_{tt} - 2\Omega g_{t\phi} - \Omega^2g_{\phi\phi}}}.
\end{align}$$

The redshift factor $g$ describes the change in frequency of a photon between the observer’s frame at infinity and the frame where it is emitted. $$\begin{equation}
\label{eq:doppler}
    g^{-1} = \frac{\nu_\mathrm{emis}}{\nu_{\rm obs}} = \frac{-k_\mu u^\mu}{E}.
\end{equation}$$

## Parallel transport

Ray-tracing polarization in curved spacetime requires parallel transport of the emitted polarization to the observer screen. We define this operation as a rotation matrix: ${\bf R}$ (main text: Eq. 5). This matrix multiplies the emission-frame Stokes vector $\bf J$ to rotate the linearly polarized components: $$\begin{equation}
\label{eq:paralleltrans}
    {\bf R}{\bf J} = 
    \begin{bmatrix}
    1 & 0 & 0 & 0 \\
    0 & \cos2\chi & -\sin2\chi & 0 \\
    0 & \sin2\chi & \cos2\chi & 0 \\
    0 & 0 & 0 & 1
    \end{bmatrix}
    \begin{bmatrix}
    J_{I} \\ J_{Q} \\ 0 \\ J_{V}
    \end{bmatrix}.
\end{equation}$$ The angle $\chi$ at pixel coordinates $(\alpha, \beta)$ is given by (cite: himwich2020universal_supp): $$\begin{equation}
    e^{2i\chi} = \frac{(\beta+i\mu)(\kappa_1 - i\kappa_2)}{(\beta-i\mu)(\kappa_1 + i\kappa_2)},
\end{equation}$$ where $\kappa = \kappa_1 + i\kappa_2$ is the complex Penrose-Walker constant, a quantity that is computed in the emission frame and then conserved in parallel transport, and $\mu = -(\alpha+a\sin\theta_o)$.

To compute $\kappa$ in the emitter frame we first convert the coordinate-frame 4-vectors $k^\mu$ and $b^\mu$ for the magnetic field to local 3-vectors $\bf{k}$ and $\bf{B}$ using the tetrad matrices $e^\mu_a$ (which depend on the emission position and fluid velocity) as described in (cite: grtrans_supp) (Equations 36-42). We then compute the local emitted polarization vector $\bf{f}$ from $$\begin{equation}
    \mathbf{f} = \frac{\mathbf{k}\times\mathbf{B}}{|\mathbf{k}|}.
\end{equation}$$ We then convert $\bf{f}$ to a coordinate frame four-vector $f^\mu$ using the transpose tetrad matrix. The constant $\kappa$ is then (cite: grtrans_supp; gelles2021polarized_supp) $$\begin{align}
    \kappa &= \kappa_1 + i\kappa_2 = (r-ia\cos\theta)(A-iB)\\
    A&=(k^tf^r-k^rf^t)+a\sin^2\theta(k^rf^\phi-k^\phi f^r)\\
    B&=\left[(r^2+a^2)(k^\phi f^\theta-k^\theta f^\phi)-a(k^tf^\theta - k^\theta f^t)\right]\sin\theta.
\end{align}$$

10

(ref: wielgus2022orbital_supp) M. Wielgus, M. Moscibrodzka, J. Vos, Z. Gelles, I. Martı́-Vidal, J. Farah, N. Marchili, C. Goddi, and H. Messias. . , 665:L6, 2022.

(ref: akiyama2022firstIII_supp) Event Horizon Telescope Collaboration. . , 930(2):L14, 2022.

(ref: levis2021inference_supp) A. Levis, D. Lee, J. A. Tropp, C. F.  Gammie, and K. L. Bouman. Inference of Black Hole Fluid-Dynamics from Sparse Interferometric Measurements. In *Proc. IEEE/CVF Intl. Conf. Comput. Vision (ICCV)*, 2340–2349, 2021.

(ref: lee2021disks_supp) D. Lee and C. F. Gammie. Disks as Inhomogeneous, Anisotropic Gaussian Random Fields. , 906(1):39, 2021.

(ref: akiyama2022firstI_supp) Event Horizon Telescope Collaboration. . , 930(2):L12, 2022.

(ref: gralla2020null_supp) S. E. Gralla and A. Lupsasca. Null geodesics of the Kerr exterior. , 101(4):044032, 2020.

(ref: kgeo2023_supp) A Chael. kgeo (version 1.0.0). <https://github.com/achael/kgeo>, 2023. Online; accessed 01-June-2023.

(ref: himwich2020universal_supp) E. Himwich, M. D. Johnson, A. Lupsasca, and A. Strominger. Universal polarimetric signatures of the black hole photon ring. , 101(8):084020, 2020.

(ref: grtrans_supp) J. Dexter. . , 462(1):115–136, 2016.

(ref: gelles2021polarized_supp) Z. Gelles, E. Himwich, M. D. Johnson, and D. C. M. Palumbo. Polarized image of equatorial emission in the Kerr geometry. , 104(4):044060, 2021.

</paper>

Write the methods card for this paper.