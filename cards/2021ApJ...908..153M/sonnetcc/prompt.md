# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...908..153M\sonnetcc\reply.txt

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
 "bibcode": "2021ApJ...908..153M",
 "title": "Modeling of the ALMA HL Tau Polarization by Mixture of Grain Alignment and Self-scattering",
 "year": 2021,
 "journal": "The Astrophysical Journal",
 "first_author": "Mori, Tomohiro",
 "n_authors": 2,
 "arxiv_id": "2012.01735",
 "doi": "10.3847/1538-4357/abd08a",
 "alma_projects_linked_by_archive": [
  "2016.1.00115.S"
 ]
}
```

Paper text:
<paper>
# Modeling of the ALMA HL Tau Polarization by Mixture of Grain Alignment and Self-scattering [^1]

## Abstract

Dust polarization at (sub)millimeter wavelengths has been observed for many protoplanetary disks. Theoretically, multiple origins potentially contribute to the polarized emission but it is still uncertain what mechanism is dominant in disk millimeter polarization. To quantitatively address the origin, we perform radiative transfer calculations of the mixture of alignment and self-scattering induced polarization to reproduce the 3.1 mm polarization of the HL Tau disk, which shows azimuthal pattern in polarization vectors. We find that a mixture of the grain alignment and self-scattering is essential to reproduce the HL Tau 3.1 mm polarization properties. Our model shows that the polarization of the HL Tau at 3.1 mm can be decomposed to be the combination of the self-scattering parallel to the minor axis and the alignment-induced polarization parallel to the major axis, with the orders of $\sim 0.5\%$ fraction for each component. This slightly eases the tight constraints on the grain size of $\sim 70~\ensuremath{\mu}m$ to be $\sim 130~\ensuremath{\mu}m$ in the previous studies but further modeling is needed. In addition, the grain alignment model requires effectively prolate grains but the physics to reproduce it in protoplanetary disks is still a mystery.

# Introduction

The presence of dust polarization of protoplanetary disks at submillimeter/millimeter wavelengths have been indicated for several protostars and T Tauri stars with the James Clerk Maxwell Telescope (JCMT) single-channel polarimeter (cite: akeson1997; tamura1995; tamura1999). However, for two decades, spatially resolved polarization has not been obtained due to the lack of the sensitivity and spatial resolutions of the instruments (cite: Hughes2009; Hughes2013) until the first detection of the millimeter polarization for the HL Tau disk by (cite: stephens2014). Nowadays, ALMA dust polarization observations have enabled us to obtain the polarization for various class II protoplanetary disks, showing the various polarization morphology and polarization fraction (cite: kataoka2016b; kataoka2017; stephens2017; hull2018; bacciotti2018; ohashi2018; dent2019; harrison2019; mori2019).

One difficulty in interpreting the disk polarization is that multiple mechanisms of polarization are at work at millimeter wavelengths. One mechanism is the grain alignment, where elongated dust grains are aligned to some directions and emit polarized thermal dust emission. The grain alignment mechanism has been long and well studied, especially the radiative torques (RATs) (cite: lazarian2007). Here we only discuss which direction the grains are aligned to because it reflects the polarization orientation. The directions of the grain alignment may represent magnetic fields (cite: davis1951; cho2007), radiation (cite: tazaki2017), or gas flow (cite: gold1952; lazarian2007; kataoka2019). Since the grain alignment has been mainly studied in the condition of the interstellar medium, further discussion of the alignment physics in the protoplanteary disks is necessary. Another mechanism that would produce polarization is the self-scattering, where the dust grains scatter and polarize the incoming thermal emission from other dust grains (cite: kataoka2015). Dust grains with the size comparable to observed wavelengths efficiently scatter and polarize the thermal emission. The interpretations of the observations depend on each target. However, the interpretation itself is one of the major issues of the millimeter polarization of protoplanetary disks.

To interpret the dust polarization, it is essential to disentangle the polarization mechanisms. In this paper, as one step toward complete understanding of the polarization, we investigate the effects of superposition of the two major polarization mechanisms, which are the self-scattering and alignment. Especially, we model the 3.1 mm polarization of the HL Tau disk, which has been interpreted purely as alignment-induced polarization (cite: kataoka2017), but also pointed out to be contaminated by self-scattering (cite: yang2019).

HL Tau is a class I/II protostar in the Taurus star-forming complex at a distance of 140 pc from the solar system (cite: rebull2004; robitaille2007). A notable feature of the surrounding disk is the concentric multi-ringed structure with a spatial scale of $\sim$100 au (cite: alma2015). The polarization morphology at millimeter wavelengths on the HL Tau disk shows strong wavelength dependence (cite: stephens2014; kataoka2017; stephens2017). The polarization morphology at 870 $\ensuremath{\mu}m$ is parallel to the disk minor axis, while that at 3.1 mm shows almost the azimuthal pattern. The polarization pattern with the vectors parallel to the minor axis is well reproduced by the self-scattering model (cite: yang2016; kataoka2016). Therefore, the $870~\ensuremath{\mu}m$ polarization has been interpreted by the self-scattering. In contrast, the origin of the 3.1 mm polarization has been interpreted by dust alignment because the self-scattering fails to explain the azimuthal pattern. It has been first interpreted by grain alignment with the radiative anisotropy (cite: tazaki2017; kataoka2017), but slight inconsistency in the morphology has also been pointed out (cite: yang2019).

The switching of the polarization mechanisms between 870 $\ensuremath{\mu}m$ and 3.1 mm must be explained. The reason why the self-scattering disappear at 3.1 mm is an expected behavior because polarization fraction quickly drops if dust grains are larger than the wavelengths divided by $2\pi$ (cite: kataoka2015). However, this requires the grain size to be $\sim$ 100 $\ensuremath{\mu}m$, which is not consistent with the general SED analysis, which requests millimeter to centimeter dust grains (cite: beckwith1991; ricci2010). (cite: carlos2019) analyzed the millimeter SED of the HL Tau disk with the effects of scattering-induced intensity reduction (cite: liu2019; zhu2019) and obtained grain size to be millimeter, which is larger than $\sim$ 100 $\mu$m. In contrast, the reason why alignment-induced polarization are observed at 3.1 mm but disappear at 870 $\ensuremath{\mu}m$ is still unresolved. One idea to explain the transition is that the grain size is comparable to the wavelengths, and their intrinsic polarization is strong enough to be detected at 3.1 mm but too weak at 870 $\ensuremath{\mu}m$. This happens because of the transition from Rayleigh to Mie regime. If the grain size is much smaller than the wavelengths, the intrinsic polarization does not have strong wavelength dependence. If the grain size is much larger than the wavelengths, in contrast, the polarization fraction drops. Note that if the grain size is comparable to the wavelengths, polarization direction becomes perpendicular to the grain major axis because of the Mie regime (cite: guillet2020). In this way, the wavelength dependence between millimeter and submillimeter wavelengths are the key to understanding the polarization.

Toward the full understanding of the wavelength-dependent polarization of the HL Tau, in this paper, we focus on the modeling the 3.1 mm polarization by the mixture of the self-scattering and grain alignment. (cite: yang2019) raised the issue that neither of aerodynamic nor radiative flux induced polarization can explain the 3.1 mm polarization and speculated that possible contamination of the self-scattering component. We quantitatively investigate how strong the self-scattering contamination is even at the 3.1 mm band and leave the full modeling of the three wavebands for future studies. Note that this does not solve the issue that no alignment model can perfectly explain the polarization, but it may change the wavelength dependence of the self-scattering components in the HL Tau polarization, which may have an impact on the grain size constraints.

![](HLTau_observation_I_PI_PF.pdf)

# Model

We briefly describe the outline of the radiative transfer models in this study. First, we construct a dust disk model that reproduces the Stokes I emission obtained with the 3.1 mm polarization observation. Then, on the constructed disk model, we take into account the effect of the grain alignment and self-scattering in calculating polarization.

## Disk Model

Figure [1](#fig:HLTau_Band3) shows the Stokes I intensity, polarized intensity, and polarization fraction, all of which are overlaid with the polarization vectors. The notable features of the 3.1 mm polarization are (1) azimuthal polarization morphology and (2) azimuthally uniform polarization fraction at $\sim$ 1%.

We construct an axisymmetric disk model that reproduces the stokes I image obtained on the polarization observation at 3.1 mm (cite: kataoka2017; stephens2017). By assuming that the Stokes I emission at 3.1 mm is optically thin, we construct the radial profile of the optical depth at 3.1 mm with the form of $$\begin{equation}
\rm \tau_{model} (r) = \tau_0 \: \Bigl(\frac{r}{\rm 1 \: au}\Bigr)^{-\gamma_1}\exp\Bigl[\Bigl(\frac{r}{r_c}\Bigr)^{-\gamma_2}\Bigr],
\label{eqn:tau_profile_model}
\end{equation}$$ with the temperature profile of $\rm T(r) = 310 (r/1 AU)^{-0.57}$ K (cite: okuzumi2019). We note that both the dust surface density and temperature are assumed to have smooth radial distributions without any ring and gap structures observed with the higher spatial resolution (cite: alma2015) for simplicity.

We adopt the parameter set of ($\rm \tau_0, r_c, \gamma_1, \gamma_2$) = (1.0, 129.2, 6.6, 9.0), which reproduces the Stokes I emission. Figure [2](#fig:HLTau_observation_model_stokesI) shows the images of observed and modeled Stokes I produced assuming the parameter set and residual.

We derive the dust surface density profile $\rm \Sigma_d (r)$ by calculating $\rm \Sigma_d (r)$ = $\rm \tau_{model}/\kappa_{abs}$, where $\rm \kappa_{abs}$ is the absorption opacity. As we will describe below, the value of $\kappa_{abs}$ is a function of $a_{max}$ and $\lambda$ when constituent materials are determined. For the fiducial value, we adopt $\rm \kappa_{abs}(a_{max} = 100 \: \ensuremath{\mu}m, \lambda = 3.1 \: mm)$ = 0.0788 cm$^2$ g$^{-1}$ in calculating the dust surface density.

The vertical dust density is assumed to be Gaussian density distribution with a dust scale height $h_d$ such that $\rm \rho_d = \Sigma_d/\sqrt{2\pi}h_d \exp(-z^2/2h_d^2)$. We also assume that $h_d$ is same as the gas pressure scale height.

While the residuals are still significant, they show axisymmetric distribution. For this study, we aim at reproducing the continuum emission with an axisymmetric model for simplicity, and thus we do not further search the parameter sets.

![](HLTau_observation_model_stokesI.pdf)

.

## Dust Model

We use a grain composition model developed by (cite: birnstiel2018), where the grains are the mixture of silicate, troilite, organics, and water ice. The refractive index used in the calculation is as follows: (cite: draine2003) for astronomical silicate, (cite: henning1996) for troilite and refractory organics, and (cite: warren2008) for water ice. We compute the mixture of them with the effective medium theory using the Maxwell-Garnett rule (e.g., (cite: bohren1983; miyake1993)). We assume the grains have a power-law-size distribution with a power of $q$ = -3.5 (cite: mathis1977) with the maximum grain size of $a_{max}$, while the minimum grain size is fixed at $a_{min}$ = 0.05 $\mu$m. We assume the same grain population throughout the disk.

To reproduce polarization, we consider both alignment and scattering-induced polarization. For the alignment-induced polarization, we consider both prolate and oblate grains. [^2] The motivation to consider the both models is the observed polarization morphology. There are two ways to reproduce azimuthal polarization vectors; effectively prolate grains with their major axis to be parallel to the disk azimuthal direction and effectively oblate grains with their minor axis parallel to the disk radial direction. We assume the Rayleigh regime (cite: lee1985) to calculate the intrinsic polarization. This approximation holds when the size parameter $x=2\pi a/  \lambda \ll 1$. We assume the grain size up to 200 $\ensuremath{\mu}m$ at the wavelength of 3.1 mm, which corresponds to the size parameter of $x=0.42$, which justifies the use of Rayleigh regime. We assume the axes ratio of the grains to be $\alpha = 0.9$ for prolate grains and $\alpha = 1.1$ for oblate grains and that the alignment efficiency to be $\epsilon=0.6$. We assume that the oblate grains are aligned with their short axis parallel to the radial direction of the disk while the prolate grains are aligned with their long axis parallel to the azimuthal direction of the disk. We ignore the effects of temperature for simplicity.

As pointed out by (cite: guillet2020), to discuss the wavelength dependence of the alignment-induced polarization, the Mie regime is essential to be considered. In this paper, however, we do not treat the Mie regime for simplicity and we focus on the single band observations on the HL Tau at 3.1 mm. In the cases of further modeling at 870 $\ensuremath{\mu}m$ and at 1.3 mm, the Mie regime treatment is required because the size parameter of $200~\ensuremath{\mu}m$ grains becomes $x=1.44$ at 870 $\ensuremath{\mu}m$ and $x=0.97$ at 1.3 mm.

The scattering-induced polarization is included by turning on the scattering in the radiative transfer simulations. We treat the full phase function and take into account the multiple scattering. The controlling parameter of the scattering is the maximum grain size, $a_{max}$. The self-scattering polarization is the most effective when the maximum grain size is $a_{max}$ $\sim$ $\lambda/2\pi$ (cite: kataoka2015).

We assume spherical dust grains for computing self-scattering while we assume oblate or prolate grains for computing alignment-induced polarization. These are not consistent but we neglect the effects of scattering by non-spherical grains for simplicity. The angle-averaged absorption opacity of oblate/prolate grains is set to be the same as the spherical grains.

We also note a technical treatment. The radiative transfer code RADMC-3D allows users to compute the alignment-induced polarization only when the dust scattering is turned on. To reproduce the alignment-induced polarization without scattering, therefore, we use $a_{max}$ = 50 $\mu$m with the scattering turned on, where the scattering-induced polarization is negligible.

# Results

## Alignment-only Model

First, we see how the beam dilution affects the appearance of the polarization vectors. We use the same disk model of HL Tau but assume that the disk is observed with a face-on view, $i=0^\circ$. The left panels of Figure [3](#fig:HLTau_inclination_PI) demonstrates the effects of beam dilution with the face-on view. To reproduce the azimuthal polarization pattern, the prolate grains are assumed to be aligned with their long axis to be parallel to the azimuthal direction, while the oblate grains are with their short axis to be parallel to the radial direction. Both models generally shows the azimuthal pattern in polarization vectors, but the vectors at around the central region have certain inclination angles, which is not expected in the case without beam dilution.

Next, we see the effects of changing the disk inclination angle on the appearance of the polarization vectors and polarized intensity. The center and right columns of Figure [3](#fig:HLTau_inclination_PI) show the case of the inclination angles of 45$^\circ$, and 60$^\circ$. The polarization vectors are almost in the azimuthal directions in the inclination angles of 45$^\circ$ and 60$^\circ$ for both the prolate and oblate grains, except the central regions where the beam dilution affect the morphology.

(cite: yang2019) proposed that, if the disk inclination is non-zero, we can distinguish the alignment models between effectively prolate and oblate grains by investigating if the polarization vectors are in the azimuthal directions (i.e., azimuthal pattern) or are with their normal direction to be toward the disk center (i.e., circular pattern). However, as we see in Figure [3](#fig:HLTau_inclination_PI), the difference between elliptical and circular patterns is hard to be distinguished because of the beam dilution.

In contrast, the polarized intensity shows prominent differences between the prolate and oblate grain models; the prolate grain models show higher polarized intensity (i.e., brighter color in Figure [3](#fig:HLTau_inclination_PI)) along the minor axis than the major axis, while the oblate models show higher polarized intensity along the major axis. The reason can be understood by a simple geometry. Prolate grains along the disk minor axis always shows the longest axis in the observed projected plane even if the disk inclination is changed, while those along the disk major axis shows less polarization fraction if the disk inclination changes to be closer to edge-on view because of the projection effects. The situation is completely opposite in the case of oblate grains. Oblate grains along the disk major axis always shows the longest axis to the observers while those along the minor axis becomes fainter in higher inclination angles because of the projection effects. Therefore, investigating the polarized intensity pattern is a promising way to distinguish the mechanisms between prolate and oblate models if the polarization is purely due to the grain alignment.

Now we come back to the case of the HL Tau disk. As shown in the central panel of Figure [1](#fig:HLTau_Band3), the polarized intensity of the HL Tau disk at 3.1 mm wavelength shows little variation in the azimuthal direction. This is different from the models that we discussed, where the prolate grain model shows that polarized intensity is brighter along the disk minor axis while the oblate model shows it is brighter along the disk major axis. This illustrates that alignment-only models may not be able to reproduce the observed polarized intensity pattern. This motivates us to add another mechanism of polarization, self-scattering, which we will discuss in the next chapter.

We note that the general properties described above hold for the polarization fraction as shown in Figure [5](#fig:HLTau_main_PF). In addition, the general behavior and differences between prolate and oblate grain models is also discussed by (cite: yang2019) with semi-analytical models.

![](HLTau_alignment_inclination_PI.pdf)

## Mixture of Alignment and Scattering Models

Next, we discuss a possibility that a mixture of the alignment and self-scattering models can reproduce the HL Tau polarization at 3.1 mm. The self-scattering polarization generally produces the polarization vectors parallel to the minor axis, and the fraction is a strong function of the grain size. Therefore, we set the maximum grain size $a_{max}$ to be the the major parameter and changes it to reflect the strength of the self-scattering polarization. We use the same disk models of the alignment-induced polarization of the prolate and oblate cases, and add the self-scattering-induced polarization.

Figure [4](#fig:HLTau_main_PI) shows the polarized intensity of the prolate and oblate grain models with $i$ = 45$^\circ$. The contributions of the self-scattering model increases by increasing $a_{max}$ from left to right panels while that of the alignment models are fixed.

As expected, the oblate + scattering models do not reproduce the observation. Both polarization of the alignment of oblate grains and self-scattering produces stronger polarization along the major axis. As a result of superposition, the azimuthal variation becomes stronger, which is not consistent with the observation as shown in Figure [1](#fig:HLTau_Band3), which shows little azimuthal variation in polarized intensity. Instead, the prolate + scattering model shows less azimuthal variation than the oblate + scattering model. This is because the prolate grain alignment produces strong polarization along the disk major axis while the self-scattering does along the disk minor axis. As a result of their superposition, the polarized intensity shows less azimuthal variation, which is consistent with the observations.

Now the question is how strong is the contributions of the alignment and scattering. We focus on the prolate + scattering model and discuss it. The top three panels of Figure [4](#fig:HLTau_main_PI) show the case of different grain sizes, which corresponds to difference of contribution of self-scattering. As demonstrated in the figure, the $a_{max}$ = 100 $\mu$m case is dominated by the alignment-induced polarization because the polarized intensity is stronger along the minor axis, while the $a_{max}$ = 200 $\mu$m is by the self-scattering because it is stronger along the major axis. The $a_{max}$ = 130 $\mu$m case shows the half and half contributions between alignment and scattering, which reproduce little azimuthal variation as observed. Therefore, we conclude that prolate + scattering model with $a_{max}$ = 130 $\mu$m best reproduces the observed HL Tau polarization at 3.1 mm. Note that we also successfully reproduce the observed polarization fraction with the mixture model $a_{max}$ = 130 $\ensuremath{\mu}m$ as shown in Figure [5](#fig:HLTau_main_PF).

![](HLTau_prolate_oblate_scattering_PIimage.pdf)

# Discussion

The main results of the radiative transfer calculations are (1) the HL Tau 3.1 mm polarization can be reproduced with the mixture of the alignment and self-scattering models and (2) prolate grain model can explain the observations but oblate model does not. In this section, we discuss the implications on the grain properties from both alignment and scattering theories as well as the caveats of our models.

## What can reproduce effectively prolate shape?

As discussed also by (cite: yang2019), the effectively prolate grain model is more preferable for reproducing the HL Tau polarization but it is theoretically counter-intuitive. We usually assume that grains are spinning if they are aligned, and they are observed as effectively oblate grains.

One possible speculation for explaining the prolate grain model is that grains are not spinning in the HL Tau disk. The only mechanism that does not assume grain spinning so far would be the mechanical alignment with a supersonic gas flow, which is so-called Gold alignment, where the long axis of needle-like grains is parallel to the gas flow onto dust grains (cite: gold1952). However, the Gold alignment assumes that the gas speed on the dust grains is supersonic whereas that is generally subsonic in protoplanetary disks (cite: cho2007). All the discussion above is phenomenological and we need further development of general grain alignment theory in protoplanetary disks.

Furthermore, we note that, even if the Gold mechanism is at work, the predicted polarization pattern is not consistent with the observations. The direction of the polarization would be parallel to the gas flow on the frame of dust grains (cite: kataoka2019), which is a strong function of the Stokes number, which denotes how well dust grains couple to ambient gas. The grain radius $a$ is found to be $a_{max}$ = 130 $\ensuremath{\mu}m$ in our modeling, which gives the Stokes number to be St = 5 $\times$ 10$^{-3}$ with the assumption of the gas surface density of $\rm \Sigma_g$ $\sim$ 20 g cm$^{-2}$. With such a small number of St much smaller than unity, the directions of gas velocity on grains would be in the radial directions (cite: kataoka2019). Note that this discussion holds even for ring-like disks (cite: mori2019). However, our modeling has found that the directions of the relative velocity are dominantly in the azimuthal directions, which is incompatible with the theory.

## How Efficient is the Scattering at 3.1 mm?

The size of dust grains has been constrained by modeling the wavelength dependence of the contribution of the scattering-induced polarization. In the case of HL Tau disk, previous studies have assumed that the Band 7 (0.87 mm) polarization is dominated by self-scattering while the Band 3 (3.1 mm) has no contribution of self-scattering, which results in the tight constraint on the grain size to be 70 $\ensuremath{\mu}m$ in size (cite: kataoka2016; yang2016; kataoka2017). However, we have revealed that there is a contribution of self-scattering even for the 3.1 mm polarization. Therefore, we discuss if our modeling changes the interpretation of the grain size in the HL Tau disk.

To estimate the scattering component at each wavelength, as conducted in (cite: kataoka2017), we compute the total polarization across the HL Tau disk, which is given by $$\begin{eqnarray}
PF_{total} =  
\left\{ 
\begin{array}{ll}
1 & \rm{(minor)}\\
-1 &\rm{(major)}\\
\end{array}
\right\}
\times {\sqrt{(\Sigma Q)^2 + (\Sigma U)^2}}{\Sigma I}  , 
\label{eqn:total_polarization}
\end{eqnarray}$$ where $\Sigma$I, $\Sigma$Q, and $\Sigma$U are the Stokes I, Q, and U emissions integrated for the whole disk. Here, we explicitly define the sign of the total polarization fraction; $PF_{total}$ is positive if the position angle of the total polarization, which is calculated from $\Sigma$Q, and $\Sigma$U, is closer to the disk minor axis, while $PF_{total}$ is negative if the position angle is closer to the disk major axis. This is motivated to be able to estimate the canceling out effects. In the case of axisymmetric protoplanetary disks, the position angle of polarization is usually parallel to either the disk minor or major axes because of the symmetry. If this is the case, defining sign with respect to the disk minor and major axes helps to see which components dominate the total polarization.

Table [1](#tab:scattering_contributions) summarizes the computed total polarization fraction for the observations and models. We update the total polarization fraction presented in (cite: kataoka2017), who used the SMA and CARMA data, with the ALMA data in Band 6 and 7 while its upper limit in ALMA 3 is presented the same as that study. $PF_{total}$ is calculated from the final images as shown in Figure [4](#fig:HLTau_main_PI) with the equation ([\[eqn:total_polarization\]](#eqn:total_polarization)). We also show $PF_{scat, model}$ and $PF_{align, model}$, which represent the total polarization of the cases where either scattering or alignment model is calculated. As shown in the table [1](#tab:scattering_contributions), the total polarization fraction is nearly equal to the sum of those of the scattering and alignment components. This illustrates the powerful estimation of the total polarization by considering the positive and negative signs of each polarization components.

|  | $\lambda$ \[mm\] | $PF_{total} (\simeq PF_{scat}+PF_{align})$ \[%\] | $PF_{scat}$ \[%\] | $PF_{align}$ \[%\] |
|:--:|:--:|:--:|:--:|:--:|
| oblate | 3.1 | 1.07 | 0 | 1.07 |
| oblate + scattering ($a_{max}$ = 100 $\ensuremath{\mu}m$) | 3.1 | 1.25 | 0.20 | 1.07 |
| oblate + scattering ($a_{max}$ = 130 $\ensuremath{\mu}m$) | 3.1 | 1.47 | 0.42 | 1.07 |
| oblate + scattering ($a_{max}$ = 200 $\ensuremath{\mu}m$) | 3.1 | 2.23 | 1.21 | 1.07 |
| prolate | 3.1 | -0.55 | 0 | -0.55 |
| prolate + scattering ($a_{max}$ = 100 $\ensuremath{\mu}m$) | 3.1 | -0.35 | 0.20 | -0.55 |
| prolate + scattering ($a_{max}$ = 130 $\ensuremath{\mu}m$) | 3.1 | -0.12 | 0.42 | -0.55 |
| prolate + scattering ($a_{max}$ = 200 $\ensuremath{\mu}m$) | 3.1 | 0.68 | 1.21 | -0.55 |
| observation | 3.1 | $-0.1<PF_{total}<0.1$ | $\--$ | $\--$ |
| observation | 1.3 | $0.551 \pm 0.003$ | $\--$ | $\--$ |
| observation | 0.87 | $0.619 \pm 0.004$ | $\--$ | $\--$ |

:  Summary of the total polarization fraction of the models and observations. The first column represents the model names. $\lambda$ is the wavelengths. $PF_{total}$ represents the total polarization fraction, which can be decomposed to the scattering component, $PF_{scat}$ and the alignment component, $PF_{align}$. We define positive values of the polarization fraction for the component parallel to the disk minor axis while negative values for that parallel to the disk major axis.

As shown in the table [1](#tab:scattering_contributions), oblate grain model always shows the positive value while the prolate grain model shows the negative values, where positive value corresponds to the polarization parallel to the disk minor axis while negative value corresponds to that parallel to the disk major axis. In contrast, the self-scattering always shows positive values because of the disk geometry. To reproduce the tight upper limit on the absolute value of the total polarization fraction to be less than 0.1 %, the oblate grain model is not favored and the combination of the prolate model and self-scattering is the key.

Here, we emphasize our big assumption that we do not know the wavelength dependency of the alignment-induced polarization, and assume that there is no contribution from alignment polarization at the wavelengths of the Band 6 and 7. To reproduce this, we need to calculate the intrinsic polarization in the Mie regime (cite: guillet2020; kirchschlager2019), which computationally costs.

By assuming that there is no contribution of alignment induced polarization at Bands 6 and 7, we confirm the decreasing trend of the observed total polarization fraction from 0.87 mm to 3.1 mm, which has been discussed by (cite: kataoka2017) partially with the SMA and CARMA results from (cite: stephens2014). Furthermore, our study revealed that the non-detection of total polarization at 3.1 mm is explained by the combination of the alignment (-0.55 %) and the self-scattering ($+0.42$ %), which requires modification on the wavelength-dependence of the self-scattering polarization. However, the contribution of self-scattering to the total polarization at 3.1 mm, which is estimated to be 0.42 % in this study, is still smaller than the 0.87 mm and 1.3 mm total polarization fractions. This means that the decreasing trend of the self-scattering polarization still holds, which supports the idea of $\sim 100$ micron-size grains because the wavelength, at which the self-scattering polarization peaks is, 0.87 mm or shorter (cite: kataoka2016; kataoka2017; yang2016).

Still, there are significant differences in the size measurements between millimeter-wave polarization and spectral indices. Latest modeling for the continuum emission of the HL Tau disk obtained at multiple wavelengths from 0.9 mm to 13 mm found the radial gradient of the grain sizes from $a_{max}$ = 1.5 mm in the inner region to $a_{max}$ = 500 $\ensuremath{\mu}m$ in the outer region, which is at least four times larger than that in this study (cite: carlos2019). Plenty of differences between the two studies, for example, the observation wavelengths, angular resolutions, and modeling methods can affect the size measurements and partly explain the discrepancy. Another primary difference is assumed constituent materials of the dust grains, which determine refractive indices. Because the absolute values of the absorption/scattering opacities and their wavelength dependence are strongly sensitive to the assumption on the composition, this can affect the measurement conducted in both of the studies (cite: testi2014). To reconcile the discrepancy, further modeling that assumes the same grain composition and disk parameters should be conducted.

## Caveats

In the radiative transfer calculations, the dust models are not fully consistent between the alignment and scattering models. When we calculate the polarization of aligned elongated grains, we set an angle-dependent absorption opacities. However, we assume spherical dust grains that have the same absorption opacities for elongated grains for calculating their scattering because of the difficulties in calculating scattering opacities of non-spherical dust grains.

# Conclusions

The origin of the polarized emission of the HL Tau disk at 3.1 mm has been debated in the previous works. We have focused on the 3.1 mm polarization of HL Tau, which shows the azimuthal pattern of polarization vectors, and have conducted radiative transfer simulations for the 3.1 mm HL Tau polarization. Our main findings are as follows.

1.  By radiative transfer simulations, we confirmed that alignment-induced polarization cannot reproduce the 3.1 mm polarization feature of the HL Tau disk as discussed by (cite: yang2019) with a semi-analytical model.

2.  Next, we run models of the mixture of the grain alignment and self-scattering and found that the combination of the effectively prolate grain emission and self-scattering can reproduce the observations. However, the combination of the effectively oblate grain emission and self-scattering cannot reproduce the polarization. Our model shows that the total polarization fraction at 3.1 mm can be understood by the combination of 0.42 % polarization due to the self-scattering, which is parallel to the disk minor axis, and 0.55 % of the alignment-induced polarization, which is parallel to the disk major axis.

3.  We found that the maximum size of the scattering dust grains is $a_{max}$ $\sim$ 130 $\ensuremath{\mu}m$ to reproduce the azimuthally uniform polarization fraction. This size is consistent with them obtained on the polarization observation in Band 6 and 7. However, the size is a few times smaller than that was measured by the multi-wavelength continuum analysis (cite: carlos2019). We confirmed that effectively prolate grain models are more preferable than the oblate grain models to reproduce the 3.1 mm polarization of HL Tau. However, the physical model to reproduce the situation is still uncertain.

We note that while the radiative transfer calculations have been performed for explaining the 3.1 mm polarization of the HL Tau disk, further modeling of the multi-wavelength polarization with the results at 870 $\ensuremath{\mu}m$ and 1.3 mm is required in future studies. Modeling of the multiband polarization observations will provide the spectrum of alignment and scattering efficiency, which enable us to further constrain the grain sizes and shapes.

# Acknowledgments

We gratefully thank Ian Stephens for providing us the analyzed ALMA Band 3 polarization data, which has enabled us to conduct the modeling work. We are also deeply grateful to Takashi Miyata, Takafumi Kamizuka, and Ryou Ohsawa for fruitful discussions for our study. This work is supported by JSPS KAKENHI Numbers 18K13590 and 19H05088. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

# Facilities

ALMA

# The Polarization Fraction in the Mixture Models (Alignment + Self-scattering)

Figure [5](#fig:HLTau_main_PF) shows polarization fraction mixture of the grain alignment and self-scattering. As well as Figure [4](#fig:HLTau_main_PI) in Section [3](#sec:results), the model with prolate grains and $a_{max}$ = 130 $\ensuremath{\mu}m$ (top-central panel) successfully reproduces the azimuthally uniform polarization fraction with $\sim$1$\--$2 %, whereas other models predict significant azimuthal variations.

![](HLTau_prolate_oblate_scattering_PFimage.pdf)

natexlab

(ref: akeson1997) Akeson, R. L., & Carlstrom, J. E. 1997, ApJ, 491, 254, doi: [`10.1086/304949`](http://doi.org/10.1086/304949)

(ref: alma2015) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3, doi: [`10.1088/2041-8205/808/1/L3`](http://doi.org/10.1088/2041-8205/808/1/L3)

(ref: bacciotti2018) Bacciotti, F., Girart, J. M., Padovani, M., et al. 2018, ApJL, 865, L12, doi: [`10.3847/2041-8213/aadf87`](http://doi.org/10.3847/2041-8213/aadf87)

(ref: beckwith1991) Beckwith, S. V. W., & Sargent, A. I. 1991, ApJ, 381, 250, doi: [`10.1086/170646`](http://doi.org/10.1086/170646)

(ref: birnstiel2018) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45, doi: [`10.3847/2041-8213/aaf743`](http://doi.org/10.3847/2041-8213/aaf743)

(ref: bohren1983) Bohren, C. F. 1983, Tellus Series B Chemical and Physical Meteorology B, 35B, 65, doi: [`10.1111/j.1600-0889.1983.tb00008.x`](http://doi.org/10.1111/j.1600-0889.1983.tb00008.x)

(ref: carlos2019) Carrasco-González, C., Sierra, A., Flock, M., et al. 2019, ApJ, 883, 71, doi: [`10.3847/1538-4357/ab3d33`](http://doi.org/10.3847/1538-4357/ab3d33)

(ref: cho2007) Cho, J., & Lazarian, A. 2007, ApJ, 669, 1085, doi: [`10.1086/521805`](http://doi.org/10.1086/521805)

(ref: davis1951) Davis, Leverett, J., & Greenstein, J. L. 1951, ApJ, 114, 206, doi: [`10.1086/145464`](http://doi.org/10.1086/145464)

(ref: dent2019) Dent, W. R. F., Pinte, C., Cortes, P. C., et al. 2019, MNRAS, 482, L29, doi: [`10.1093/mnrasl/sly181`](http://doi.org/10.1093/mnrasl/sly181)

(ref: draine2003) Draine, B. T. 2003, ARA&A, 41, 241, doi: [`10.1146/annurev.astro.41.011802.094840`](http://doi.org/10.1146/annurev.astro.41.011802.094840)

(ref: gold1952) Gold, T. 1952, MNRAS, 112, 215, doi: [`10.1093/mnras/112.2.215`](http://doi.org/10.1093/mnras/112.2.215)

(ref: guillet2020) Guillet, V., Girart, J. M., Maury, A. J., & Alves, F. O. 2020, arXiv e-prints, arXiv:2001.08400. [`https://arxiv.org/abs/2001.08400`](https://arxiv.org/abs/2001.08400)

(ref: harrison2019) Harrison, R. E., Looney, L. W., Stephens, I. W., et al. 2019, ApJL, 877, L2, doi: [`10.3847/2041-8213/ab1e46`](http://doi.org/10.3847/2041-8213/ab1e46)

(ref: henning1996) Henning, T., & Stognienko, R. 1996, A&A, 311, 291

(ref: Hughes2013) Hughes, A. M., Hull, C. L. H., Wilner, D. J., & Plambeck, R. L. 2013, AJ, 145, 115, doi: [`10.1088/0004-6256/145/4/115`](http://doi.org/10.1088/0004-6256/145/4/115)

(ref: Hughes2009) Hughes, A. M., Wilner, D. J., Cho, J., et al. 2009, ApJ, 704, 1204, doi: [`10.1088/0004-637X/704/2/1204`](http://doi.org/10.1088/0004-637X/704/2/1204)

(ref: hull2018) Hull, C. L. H., Yang, H., Li, Z.-Y., et al. 2018, ApJ, 860, 82, doi: [`10.3847/1538-4357/aabfeb`](http://doi.org/10.3847/1538-4357/aabfeb)

(ref: kataoka2016) Kataoka, A., Muto, T., Momose, M., Tsukagoshi, T., & Dullemond, C. P. 2016a, ApJ, 820, 54, doi: [`10.3847/0004-637X/820/1/54`](http://doi.org/10.3847/0004-637X/820/1/54)

(ref: kataoka2019) Kataoka, A., Okuzumi, S., & Tazaki, R. 2019, ApJL, 874, L6, doi: [`10.3847/2041-8213/ab0c9a`](http://doi.org/10.3847/2041-8213/ab0c9a)

(ref: kataoka2017) Kataoka, A., Tsukagoshi, T., Pohl, A., et al. 2017, ApJL, 844, L5, doi: [`10.3847/2041-8213/aa7e33`](http://doi.org/10.3847/2041-8213/aa7e33)

(ref: kataoka2015) Kataoka, A., Muto, T., Momose, M., et al. 2015, ApJ, 809, 78, doi: [`10.1088/0004-637X/809/1/78`](http://doi.org/10.1088/0004-637X/809/1/78)

(ref: kataoka2016b) Kataoka, A., Tsukagoshi, T., Momose, M., et al. 2016b, ApJL, 831, L12, doi: [`10.3847/2041-8205/831/2/L12`](http://doi.org/10.3847/2041-8205/831/2/L12)

(ref: kirchschlager2019) Kirchschlager, F., Bertrang, G. H. M., & Flock, M. 2019, MNRAS, 488, 1211, doi: [`10.1093/mnras/stz1763`](http://doi.org/10.1093/mnras/stz1763)

(ref: lazarian2007) Lazarian, A., & Hoang, T. 2007, ApJL, 669, L77, doi: [`10.1086/523849`](http://doi.org/10.1086/523849)

(ref: lee1985) Lee, H. M., & Draine, B. T. 1985, ApJ, 290, 211, doi: [`10.1086/162974`](http://doi.org/10.1086/162974)

(ref: liu2019) Liu, H. B. 2019, ApJL, 877, L22, doi: [`10.3847/2041-8213/ab1f8e`](http://doi.org/10.3847/2041-8213/ab1f8e)

(ref: mathis1977) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425, doi: [`10.1086/155591`](http://doi.org/10.1086/155591)

(ref: miyake1993) Miyake, K., & Nakagawa, Y. 1993, Icarus, 106, 20, doi: [`10.1006/icar.1993.1156`](http://doi.org/10.1006/icar.1993.1156)

(ref: mori2019) Mori, T., Kataoka, A., Ohashi, S., et al. 2019, ApJ, 883, 16, doi: [`10.3847/1538-4357/ab3575`](http://doi.org/10.3847/1538-4357/ab3575)

(ref: ohashi2018) Ohashi, S., Kataoka, A., Nagai, H., et al. 2018, ApJ, 864, 81, doi: [`10.3847/1538-4357/aad632`](http://doi.org/10.3847/1538-4357/aad632)

(ref: okuzumi2019) Okuzumi, S., & Tazaki, R. 2019, ApJ, 878, 132, doi: [`10.3847/1538-4357/ab204d`](http://doi.org/10.3847/1538-4357/ab204d)

(ref: rebull2004) Rebull, L. M., Wolff, S. C., & Strom, S. E. 2004, AJ, 127, 1029, doi: [`10.1086/380931`](http://doi.org/10.1086/380931)

(ref: ricci2010) Ricci, L., Testi, L., Natta, A., et al. 2010, A&A, 512, A15, doi: [`10.1051/0004-6361/200913403`](http://doi.org/10.1051/0004-6361/200913403)

(ref: robitaille2007) Robitaille, T. P., Whitney, B. A., Indebetouw, R., & Wood, K. 2007, ApJS, 169, 328, doi: [`10.1086/512039`](http://doi.org/10.1086/512039)

(ref: stephens2014) Stephens, I. W., Looney, L. W., Kwon, W., et al. 2014, Nature, 514, 597, doi: [`10.1038/nature13850`](http://doi.org/10.1038/nature13850)

(ref: stephens2017) Stephens, I. W., Yang, H., Li, Z.-Y., et al. 2017, ApJ, 851, 55, doi: [`10.3847/1538-4357/aa998b`](http://doi.org/10.3847/1538-4357/aa998b)

(ref: tamura1999) Tamura, M., Hough, J. H., Greaves, J. S., et al. 1999, ApJ, 525, 832, doi: [`10.1086/307953`](http://doi.org/10.1086/307953)

(ref: tamura1995) Tamura, M., Hough, J. H., & Hayashi, S. S. 1995, ApJ, 448, 346, doi: [`10.1086/175965`](http://doi.org/10.1086/175965)

(ref: tazaki2017) Tazaki, R., Lazarian, A., & Nomura, H. 2017, ApJ, 839, 56, doi: [`10.3847/1538-4357/839/1/56`](http://doi.org/10.3847/1538-4357/839/1/56)

(ref: testi2014) Testi, L., Birnstiel, T., Ricci, L., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 339, doi: [`10.2458/azu_uapress_9780816531240-ch015`](http://doi.org/10.2458/azu_uapress_9780816531240-ch015)

(ref: warren2008) Warren, S. G., & Brandt, R. E. 2008, Journal of Geophysical Research (Atmospheres), 113, D14220, doi: [`10.1029/2007JD009744`](http://doi.org/10.1029/2007JD009744)

(ref: yang2016) Yang, H., Li, Z.-Y., Looney, L., & Stephens, I. 2016, MNRAS, 456, 2794, doi: [`10.1093/mnras/stv2633`](http://doi.org/10.1093/mnras/stv2633)

(ref: yang2019) Yang, H., Li, Z.-Y., Stephens, I. W., Kataoka, A., & Looney, L. 2019, MNRAS, 483, 2371, doi: [`10.1093/mnras/sty3263`](http://doi.org/10.1093/mnras/sty3263)

(ref: zhu2019) Zhu, Z., Zhang, S., Jiang, Y.-F., et al. 2019, ApJL, 877, L18, doi: [`10.3847/2041-8213/ab1f8c`](http://doi.org/10.3847/2041-8213/ab1f8c)

[^1]: Released on June, 10th, 2019

[^2]: Grains are believed to be spinning when they are aligned. The spinning motion makes the grains to be effectively prolate or oblate ellipsoidal bodies. We call prolate/oblate grains for simplicity but this does not rule out any complex shapes of the dust grains.

</paper>

Write the methods card for this paper.