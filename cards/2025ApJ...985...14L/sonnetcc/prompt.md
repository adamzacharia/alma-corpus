# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...985...14L\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...985...14L",
 "title": "Cloud-scale Gas Properties, Depletion Times, and Star Formation Efficiency per Freefall Time in PHANGS─ALMA",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Leroy, Adam K.",
 "n_authors": 34,
 "arxiv_id": "2502.04481",
 "doi": "10.3847/1538-4357/adbcab",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S",
  "2013.1.00803.S",
  "2013.1.01161.S",
  "2015.1.00121.S",
  "2015.1.00782.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2016.1.00386.S",
  "2017.1.00392.S",
  "2017.1.00766.S",
  "2017.1.00886.L",
  "2018.1.01321.S",
  "2018.1.01651.S",
  "2018.A.00062.S",
  "2019.2.00129.S"
 ]
}
```

Paper text:
<paper>
# Cloud-scale gas properties, depletion times, and star formation efficiency per free-fall time in PHANGS–ALMA

## Abstract

We compare measurements of star formation efficiency to cloud-scale gas properties across the PHANGS–ALMA sample. Dividing $67$ galaxies into $1.5$ kpc scale regions, we calculate the molecular gas depletion time $\ensuremath{\tau_{\rm dep}^{\rm mol}}= \Sigma_{\rm mol} / \Sigma_{\rm SFR}$ and the star formation efficiency per free-fall time $\ensuremath{\epsilon_{\rm ff}^{\rm mol}}= \tau_{\rm ff} / \ensuremath{\tau_{\rm dep}^{\rm mol}}$ for each region. Then we test how $\tau_{\rm dep}^{\rm mol}$ and $\epsilon_{\rm ff}^{\rm mol}$ vary as functions of the regional mass-weighted mean molecular gas properties on cloud scales (60–150 pc): gas surface density, $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, velocity dispersion, $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$, virial parameter, $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, and gravitational free-fall time, $\langle \tau_{\rm ff}^{\rm cloud} \rangle$. $\langle \tau_{\rm ff}^{\rm cloud} \rangle$ and $\tau_{\rm dep}^{\rm mol}$ correlate positively, consistent with the expectation that gas density plays a key role in setting the rate of star formation. Our fiducial measurements suggest $\ensuremath{\tau_{\rm dep}^{\rm mol}}\propto \ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}^{0.5}$ and $\ensuremath{\epsilon_{\rm ff}^{\rm mol}}\approx 0.39\%$, though the exact numbers depend on the adopted fitting methods. We also observe anti-correlations between $\tau_{\rm dep}^{\rm mol}$ and $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ and between $\tau_{\rm dep}^{\rm mol}$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$. All three correlations may reflect the same underlying link between density and star formation efficiency combined with systematic variations in the degree to which self-gravity binds molecular gas in galaxies. We highlight the $\tau_{\rm dep}^{\rm mol}$–$\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ relation because of the lower degree of correlation between the axes. Contrary to theoretical expectations, we observe a weak anti-correlation between $\tau_{\rm dep}^{\rm mol}$ and $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ and no significant correlation between $\epsilon_{\rm ff}^{\rm mol}$ and $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$. Our results depend sensitively on the adopted CO-to-H$_2$ conversion factor, with corrections for excitation and emissivity effects in inner galaxies playing an important role. We emphasize that our simple methodology and clean selection allow easy comparison to numerical simulations and highlight this as a logical next direction.

# Introduction

Stars form from clouds of molecular gas, with star formation and molecular gas well-correlated across nearby galaxies (cite: WONG02SFGAS; LEROY08SFGAS; BIGIEL08SFGAS; SCHRUBA11SFGAS; KENNICUTT12REVIEW). Thanks to new surveys by ALMA, we now know that the ${\approx} 100$ pc “cloud-scale” properties of molecular gas — including surface density, velocity dispersion, and dynamical state — vary systematically, responding to and reflecting their galactic environment (cite: SUN18CLOUDS; SCHRUBA19GMCS; SUN22CLOUDS; SCHINNERER24REVIEW). So far, observations only weakly constrain how these variations in cloud-scale gas properties affect the process of star formation. In other words, a major open question in the field of star formation remains: “How do the properties of the parent molecular clouds affect the efficiency and rate of star formation?”

The initial properties of a cloud of gas *should* affect the rate at which stars form. In a given environment and at fixed mass, denser clouds will be more tightly bound by self-gravity. A cloud with a higher mean density, $\rho^{\rm cloud}_{\rm mol}$, will also have a shorter corresponding cloud-scale gravitational free-fall time, $\tau_{\rm ff}^{\rm cloud} = \sqrt{3 \pi / (32 G \rho_{\rm mol}^{\rm cloud})}$ and might be expected to collapse to form stars faster, all other things being equal. For motions dominated by supersonic, isothermal turbulence, the cloud-scale velocity dispersion, which reflects the Mach number via $\mathcal{M} \propto \sigma_{\rm mol}^{\rm cloud}$, relates to the width of the density distribution (cite: VAZQUEZ94TURB; PADOAN02TURB). Meanwhile, the density distribution sets the fraction of high density, gravitationally bound gas (cite: KRUMHOLZ05EFF). The densest molecular gas is observed to be the immediate site for star formation and to correlate with tracers of star formation in the Milky Way and other galaxies (cite: GAO04DENSE; LADA10DENSE; GARCIABURILLO12DENSE; EVANS14DENSE; JIMENEZ19DENSE). The balance between kinetic and gravitational energy, often expressed as the virial parameter, $\alpha_{\rm vir} \equiv 2 K / U$, will also affect the ability of gas to collapse and form stars. In both analytic theory and numerical simulations, $\alpha_{\rm vir}$ plays a main role in setting $\epsilon_{\rm ff}$ when all other factors are equal (cite: KRUMHOLZ05EFF; PADOAN12EFF; FEDERRATH13EFF; KIM21FEEDBACKSIMS), though models in which star formation is dynamically triggered (cite: FUKUI21COLLIDE) or in which clouds exist in a state of approximate free-fall (cite: VAZQUEZ24EFF) also remain viable.

Observationally, this picture is less clear. Despite decades of studies of molecular cloud properties, there are relatively few quantitative, large-scale comparisons between the efficiency of star formation and the cloud-scale properties of molecular gas. The studies that do exist mainly concentrate on a single region or galaxy, and often focus on a few specific prototype spiral galaxies (cite: MEIDT13SFGAS; LEROY17SFGAS; HIROTA18GMCS; QUEREJETA23SFGAS) with (cite: SCHRUBA19GMCS) and (cite: SUN22CLOUDS) almost the only two studies that compare cloud properties, $\ensuremath{\tau_{\rm dep}^{\rm mol}}\equiv M_{\rm mol}/{\rm SFR}$, and $\epsilon_{\rm ff} \equiv \tau_{\rm ff} / \ensuremath{\tau_{\rm dep}^{\rm mol}}$ across significant samples of galaxies and environments. Overall, these works find mixed or weak evidence for any general correlation between $\epsilon_{\rm ff}$ and $\alpha_{\rm vir}$ (cite: LEROY17SFGAS; SCHRUBA19GMCS). Even the relationship of $\tau_{\rm dep}^{\rm mol}$ to cloud-scale mean density, expressed as $\tau_{\rm ff}$, often appears weaker than the theoretically expected $\ensuremath{\tau_{\rm dep}^{\rm mol}}\propto \tau_{\rm ff}$ or even non-existent (cite: LEROY17SFGAS; SUN23SFGAS; QUEREJETA23SFGAS).

Milky Way studies of local clouds demonstrate a clear connection between the distribution of gas density in a cloud and star formation activity (cite: KAINULAINEN09DENSE; LADA10DENSE; LADA12DENSE; EVANS14DENSE). However, most of these studies target a narrow range of environments with limited statistical power, partially because of the difficulty of accessing the spatially or time-averaged efficiency of star formation from our position within the Milky Way. In one of the most general studies to date, (cite: EVANS21GMCS) consider clouds across the whole Milky Way disk and do find evidence of a correlation between $\alpha_{\rm vir}$ and $\epsilon_{\rm ff}$. They also show that this conclusion depends on methodology, particularly the approach used to estimate molecular gas mass.

In this paper, we attempt to take a next logical step addressing this question by comparing star formation activity to cloud-scale gas properties using the largest homogeneous cloud-scale data set on molecular gas in galaxies, PHANGS–ALMA (cite: PHANGSALMA21SURVEY). Specifically, we compare the molecular gas depletion time ($\ensuremath{\tau_{\rm dep}^{\rm mol}}\equiv M_{\rm mol}/{\rm SFR}$), and the star formation efficiency per free fall time ($\epsilon_{\rm ff} \equiv \tau_{\rm ff}/\ensuremath{\tau_{\rm dep}^{\rm mol}}$) to the mass-weighted mean molecular gas properties on cloud scales. This paper builds on previous work using PHANGS–ALMA and acts as a direct follow up to (cite: SUN22CLOUDS), but represents the first systematic attempt to correlate the cloud-scale gas properties with $\ensuremath{\tau_{\rm dep}^{\rm mol}}$ and $\epsilon_{\rm ff}$ across the whole data set.

We adopt the cross-scale methodology developed in (cite: LEROY16GMCS), (cite: LEROY17SFGAS), (cite: SCHRUBA19GMCS), (cite: SUN20PRESS) and (cite: SUN22CLOUDS). This approach, described in §[2](#sec:methods), breaks galaxies into $\sim$kpc sized regions and summarizes the smaller-scale molecular gas properties via mass-weighted averages. These properties include mass surface density ($\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$), velocity dispersion ($\langle \sigma_{\rm mol}^{\rm cloud} \rangle$), and the dynamical state of the gas expressed via the virial parameter ($\langle \alpha_{\rm vir}^{\rm cloud} \rangle$). We compare these gas properties to the regional mean molecular gas depletion time ($\ensuremath{\tau_{\rm dep}^{\rm mol}}$) and star formation efficiency per gravitational free fall time ($\ensuremath{\epsilon_{\rm ff}^{\rm mol}}$). By working with these kpc-sized regions, we average out the time evolution of individual star-forming regions, which causes systematic changes in their apparent $\ensuremath{\tau_{\rm dep}^{\rm mol}}$ and $\ensuremath{\epsilon_{\rm ff}^{\rm mol}}$ (cite: SCHRUBA10SFGAS; LEROY13SFGAS; SEMENOV18GMCS; SEMENOV21GMCS; KRUIJSSEN19TIMES; CHEVANCE20TIMES; KIM22TIMES). In practice, estimating $\Sigma_{\rm SFR}$ at this resolution also allows us to reduce stochasticity and utilize infrared (IR) data with limited $\approx 15''$ angular resolution. This approach should be simple to reproduce in numerical simulations and easy to apply to other data sets.

We present our core results in §[3](#sec:results). We find that the estimated gravitational free-fall time and molecular gas depletion time show the expected correlation, but the details depend sensitively on the adopted CO-to-H$_2$ conversion factor. This same relationship manifests as anti-correlations between $\tau_{\rm dep}^{\rm mol}$ and the cloud-scale surface density and velocity dispersion. On the other hand, our results comparing the virial parameter to $\tau_{\rm dep}^{\rm mol}$ and the star formation efficiency per free fall time seem to suggest that star formation becomes more efficient when the virial parameter is higher. This is opposite to theoretical expectations for turbulent gas clouds, which predict more efficient star formation for lower virial parameter.

In discussing the results, we suggest a path forward on this topic. We highlight rigorous comparison between observations and numerical simulations as an immediately possible, highly promising next step. In this regard, we emphasize that our measurements are easy to reproduce in simulations of galaxies, and we give a concrete checklist to do so in Appendix [7](#sec:stepbystep). On intermediate timescales, we also discuss the need for next-generation data sets that cover diverse environments with much higher physical resolution, high completeness, and reliable cloud-scale indicators of star formation activity.

# Data and methods

+:-----------------------------------------------------------------------------:+:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:+
| **Mass-weighted region-averaged cloud-scale gas properties**                                                                                                                                                                                                                      |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| (mass-weighted averages estimated in each $1.5$ kpc diameter region based on CO (2-1) emission)                                                                                                                                                                                   |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $\left< \Sigma_{\rm mol}^{\rm cloud} \right>$                                 | Cloud-scale molecular gas mass surface density in M$_\odot$ pc$^{-2}$ .                                                                                                                           |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                                                                               | Estimated from CO (2-1) line intensity using $\alpha_{\rm CO}^{2-1}$ from (cite: SCHINNERER24REVIEW).                                                                                             |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                                                                               | Corrected for completeness and inclination following (cite: SUN22CLOUDS).                                                                                                                         |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $\left< \tau_{\rm ff}^{\rm cloud} \right>$                                    | Gravitational free-fall time in yr.                                                                                                                                                               |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                                                                               | Calculated via $\tau_{\rm ff} = \sqrt{3 \pi / (32 G \rho_{\rm mol}^{\rm cloud})}$ and $\rho = 3 M_{\rm mol}^{\rm beam} / (4 \pi R_{\rm pix}^3$).                                                  |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                                                                               | $R_{\rm pix} = {\rm min}\!\left[ \ell / 2, \left( \ell^2 H_\mathrm{mol} / (8 \cos i) \right)^{1/3} \right]$ following (cite: SUN22CLOUDS).                                                        |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $\left< \sigma_{\rm mol}^{\rm cloud} \right>$                                 | Cloud-scale velocity dispersion in km s$^{-1}$.                                                                                                                                                   |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                                                                               | Calculated via the CO (2-1) line effective width and corrected for inclination and completeness.                                                                                                  |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $\left< \alpha_{\rm vir}^{\rm cloud} \right>$                                 | Dimensionless virial parameter $\alpha_{\rm vir} = 2~K/U$ considering only gas self-gravity.                                                                                                      |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                                                                               | Calculated via $\alpha_{\rm vir}^{\rm cloud} = 5 \sigma^2_{\rm mol} R_{\rm pix} / (f G M_{\rm mol}^{\rm beam})$.                                                                                  |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Region-averaged quantities related to star formation efficiency**                                                                                                                                                                                                               |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| (calculated by averaging all emission in each large $1.5$ kpc diameter region)                                                                                                                                                                                                    |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $\Sigma_{\rm mol}^{\rm kpc}$                                                  | Mean molecular gas surface density over each 1.5 kpc region in M$_\odot$ pc$^{-2}$.                                                                                                               |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $\Sigma_{\rm SFR}^{\rm kpc}$                                                  | Mean star formation rate surface density over each 1.5 kpc region in M$_\odot$ yr$^{-1}$ kpc$^{-2}$.                                                                                              |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $\tau_{\rm dep}^{\rm mol}$                                                    | Molecular gas depletion time in yr, defined as $\tau_{\rm dep}^{\rm mol} = \Sigma_{\rm mol}^{\rm kpc} / \Sigma_{\rm SFR}^{\rm kpc}$.                                                              |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $\epsilon_{\rm ff}^{\rm mol}$                                                 | Dimensionless star formation efficiency per free fall time, defined as $\epsilon_{\rm ff}^{\rm mol} = \left< \tau_{\rm ff}^{\rm cloud} \right> / \tau_{\rm dep}^{\rm mol}$                        |
|                                                                               |                                                                                                                                                                                                   |
|                                                                               | $^{a}$.                                                                                                                                                                                           |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **CO-to-H$_2$ conversion factor**                                                                                                                                                                                                                                                 |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| (following (cite: SCHINNERER24REVIEW) and based on references given in text)                                                                                                                                                                                                      |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $\alpha_{\rm CO}^{2-1}$                                                       | Calculated via $\alpha_{\rm CO,MW}^{1-0} \times f(Z) \times g(\Sigma_\star) \times R_{21}(\Sigma_{\rm SFR})^{-1}$                                                                                 |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $\alpha_{\rm CO,MW}^{1-0}$                                                    | $=4.35\;\mbox{$\rm M_\odot~pc^{-2}\ (K~km~s^{-1})^{-1}$}$; Milky Way CO (1-0) conversion factor (cite: BOLATTO13REVIEW)                                                                           |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $f (Z)$                                                                       | $=\left(Z / Z_\odot \right)^{-1.5}$ ; metallicity-dependent “CO-dark” term                                                                                                                        |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $g (\Sigma_\star)$                                                            | $=\left( {\rm max}\!\left( \Sigma_\star , 100~{\rm M}_\odot~{\rm pc}^{-2} \right)\;/\;100~{\rm M}_\odot~{\rm pc}^{-2} \right)^{-0.25}$; “starburst” emissivity term following (cite: CHIANG24XCO) |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $R_{21} (\Sigma_{\rm SFR})$                                                   | $=0.65 \left( \Sigma_{\rm SFR}\;/\;0.018~{\rm M}_\odot~{\rm yr}^{-1}~{\rm kpc}^{-2} \right)^{0.125}$ with min 0.35, max 1.0; CO line excitation term                                              |
+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Data selection**                                                                                                                                                                                                                                                                |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| (requiring cloud-scale CO flux completeness $f_{\rm comp} > 0.5$, and $\ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}> 20$ M$_\odot$ pc$^{-2}$)                                                                                                                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| At $\ell = 150$ pc, this selection scheme yields 841 independent, 1.5 kpc hexagonal regions in 67 galaxies                                                                                                                                                                        |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

: Experiment Summary

Table notes: Calculations and database described in detail in (cite: SUN22CLOUDS) and (cite: SUN23SFGAS). Conversion factor treatment described in (cite: SCHINNERER24REVIEW). $i$ refers to galaxy inclination, $\ell$ to cloud scale data resolution (beam FWHM), $H_\mathrm{mol}$ to the assumed FWHM vertical thickness of the molecular layer, $M_{\rm mol}^{\rm beam} = \Sigma_{\rm mol}^{\rm cloud} A_{\rm beam}$ with $A_{\rm beam} = \pi \theta^2 / (4 \ln 2)$. $^{a}$ $\epsilon_{\rm ff}^{\rm mol}$ combines region-averaged properties and mass-weighted cloud-scale properties. See §[3.6](#sec:effvsprops) for discussion.

We measure how star formation efficiency correlates with diagnostics that trace the physical state of molecular gas across local galaxies. To do this, we compare cloud-scale ($\ell=150$ pc FWHM resolution) gas properties to the mean molecular gas depletion time over $1.5$ kpc diameter hexagonal regions, which collectively cover the area mapped by the PHANGS–ALMA survey (cite: PHANGSALMA21SURVEY). PHANGS–ALMA targeted nearby ($d \lesssim 20$ Mpc), low to moderately inclined ($i \lesssim 75^\circ$), relatively massive ($\log_{10} M_\star / {\rm M}_\odot \gtrsim 9.75$, star-forming ($\log_{10} M_\star / {\rm SFR} > -11$ yr$^{-1}$) galaxies and offers a representative view of massive galaxies on or near the star-forming main sequence.

We conduct our analysis using the high-level data products (“the PHANGS mega-tables”) assembled by (cite: SUN22CLOUDS; SUN23SFGAS). They break galaxies into individual sub-galactic regions and then measure a rich set of galaxy structural, stellar, and ISM properties in each region. Here we consider their main data product, which breaks 80 massive, star-forming disk galaxies from PHANGS–ALMA into individual $1.5$ kpc hexagonal regions. Within each region, the “mega-tables” record star formation activity, the total molecular gas mass, and the mass-weighted mean averages of cloud-scale gas properties. We summarize the quantities relevant to our analysis below and in Table [1](#tab:experiment) and refer to (cite: SUN22CLOUDS) and (cite: SUN23SFGAS) for detailed descriptions of how all other quantities are calculated. Appendix [7](#sec:stepbystep) gives a step-by-step guide to reproduce our measurements, e.g., to compare numerical simulations to PHANGS–ALMA.

The core data sets aggregated by (cite: SUN22CLOUDS) that contribute to our measurements are: the PHANGS–ALMA CO (2-1) maps (cite: PHANGSALMA21SURVEY); ground-based narrowband H$\alpha$ maps (cite: SCHINNERER19TIMES; PAN22TIMES; QUEREJETA24SFGAS); GALEX (cite: GALEX05) ultraviolet images compiled by (cite: LEROY19Z0MGS); WISE (cite: WISE10) 3.4–22$\mu$m images compiled by (cite: LEROY19Z0MGS); and IRAC $3.6\mu$m images (cite: S4GSURVEY; QUEREJETA21). We adopt distances and orientation parameters for all PHANGS–ALMA targets as measured and compiled by (cite: LANG20KINEMATICS; ANAND21DISTANCES; PHANGSALMA21SURVEY).

## Cloud-scale gas properties

To assess the physical state of molecular gas, we use cloud-scale (physical beam size $\ell = 150$ pc) imaging[^1] of the CO (2-1) line, which traces the bulk of the molecular gas. Within each region of each galaxy, we measure four gas properties for each individual line of sight where CO is detected. Then, we weight each line of sight by the local gas surface density to derive mass-weighted, region-averaged molecular gas properties. This mass-weighting scheme, illustrated in Fig. [1](#fig:experiment), is intended to yield estimates of the physical conditions that set the star formation rate per unit gas, i.e., $\tau_{\rm dep}^{\rm mol}$, in the region. It has been described in detail by (cite: LEROY16GMCS; LEROY17SFGAS; UTOMO18EFF) and (cite: SUN22CLOUDS). We refer to quantities computed via this cross-scale averaging as $\left< X^{\rm cloud} \right>$, indicating original measurements on cloud scales followed by weighted averaging over the 1.5 kpc hexagonal regions.

We focus on four gas properties, summarized in Table [1](#tab:experiment), that should be relevant to the efficiency of star formation:

1.  *Cloud-scale molecular gas surface density ($\Sigma_{\rm mol}^{\rm cloud}$).* The molecular gas mass per unit area relates to the density of the gas, its gravitational potential, and its shielding from external radiation.

2.  *Gravitational free-fall time ($\tau_{\rm ff}^{\rm cloud}$).* Based on $\Sigma_{\rm mol}^{\rm cloud}$ and an estimated line-of-sight depth for the gas (see discussion of $R_{\rm pix}$ below), (cite: SUN22CLOUDS) estimate the mass volume density, $\rho_{\rm mol}^{\rm cloud}$, and the corresponding gravitational free fall time $\tau_{\rm ff}^{\rm cloud}$. Note that the region averaging for $\tau_{\rm ff}^{\rm cloud}$ follows a weighting scheme that ensures $\ensuremath{\tau_{\rm dep}^{\rm mol}}\propto \left< \tau_{\rm ff}^{\rm cloud} \right>$ for a fixed $\epsilon_{\rm ff}^{\rm mol}$ (cite: SUN22CLOUDS).

3.  *Cloud-scale molecular gas velocity dispersion ($\sigma_{\rm mol}^{\rm cloud}$).* Within individual clouds, turbulence is expected to make a significant contribution to the CO line width (cite: IBANEZMEJIA16GMCS; MEIDT18GMCS; HENSHAW20SCOUSE). In cases where the line width is dominated by supersonic, isothermal turbulence, the gas velocity dispersion (reflected by the line width) should be proportional to the Mach number of the turbulence (cite: MACLOW04REVIEW). This, in turn, relates to the expected width of the gas density distribution (cite: PADOAN02TURB). All other things being equal, a broader density distribution should lead to more dense, potentially star-forming gas.

4.  *Virial parameter ($\alpha_{\rm vir}^{\rm cloud}$).* The virial parameter $\alpha_{\rm vir} = 2 K / U \propto \sigma_{\rm mol}^2 / (\Sigma_{\rm mol}~R_{\rm cloud})$ expresses the ratio of kinetic energy to potential energy associated with self-gravity in the gas (cite: MCKEE92GMCS; BERTOLDI92GMCS). Gas with a lower virial parameter should be prone to collapse and therefore more susceptible to star formation. Many theories of turbulence-regulated star formation predict an anti-correlation between $\alpha_{\rm vir}^{\rm cloud}$ and $\epsilon_{\rm ff}^{\rm mol}$ (cite: PADOAN11EFF; FEDERRATH12EFF), and a similar relationship is also seen in simulations (cite: PADOAN12EFF; KIM21FEEDBACKSIMS). As with $\tau_{\rm ff}^{\rm cloud}$, $\alpha_{\rm vir}^{\rm cloud}$ requires adopting a relevant size scale, $R_{\rm pix}$.

For both $\tau_{\rm ff}^{\rm cloud}$ and $\alpha_{\rm vir}^{\rm cloud}$ we require an adopted size scale (see Table [1](#tab:experiment)). Following (cite: SUN22CLOUDS), we take the relevant scale to be $R_{\rm pix} \equiv (\ell^2 H_{\rm mol} / (8 \cos i))^{1/3}$ at the fiducial $\ell=150$ pc resolution, with $H_{\rm mol}=100$ pc. This assumes that the mass measured in each beam is spread over the entire beam and over a line-of-sight depth of $H_\mathrm{mol}/\cos{i}$, with $H_\mathrm{mol} = 100$ pc the adopted molecular gas disk scale height (cite: HEYER15REVIEW). In a similar analysis targeting M51, (cite: LEROY17SFGAS) explored the difference between fixed and dynamical estimates of $H$ and found qualitatively consistent results between the two approaches. Moreover, (cite: SUN22CLOUDS) showed a good overall match between results for an object oriented analysis, where size is measured from morphological analysis, and this sightline based approach. For more information on $R_{\rm pix}$, as well as the definition, calculation, and physical meaning of these and other quantities, see discussions in (cite: SUN20GMCS), (cite: SUN22CLOUDS), (cite: ROSOLOWSKY21GMCS), and (cite: SCHINNERER24REVIEW).

The main difference here compared to (cite: SUN22CLOUDS) or (cite: ROSOLOWSKY21GMCS) is that we adopt the new CO-to-H$_2$ conversion factor $\alpha_{\rm CO}^{2-1}$ recommended by (cite: SCHINNERER24REVIEW)[^2]. This prescription, which we reproduce in Table [1](#tab:experiment), attempts to account for excitation variations, emissivity variations, and metallicity effects based on synthesizing work by (cite: BOLATTO13REVIEW; ACCURSO17XCO; GONG20XCO; HU22XCO; SUN20PRESS; SUN22CLOUDS; DENBROK21LINES; LEROY22LINES; TENG23XCO; CHIANG24XCO). In practice, it resembles a refined version of the $\alpha_{\rm CO}$ recommended by (cite: BOLATTO13REVIEW). To assess the impact of this choice, we also run our analysis using a fixed Galactic $\alpha_{\rm CO}$. We discuss that the choice of $\alpha_{\rm CO}$ exerts a large impact on our results in §[3.5](#sec:alphaco).

## Star formation rate per unit gas

![](experiment_sketch.png)

We compare region-averaged cloud-scale gas properties to two measures of the efficiency with which molecular gas forms stars. The molecular gas depletion time,

$$\begin{equation}
\label{eq:tdep}
\ensuremath{\tau_{\rm dep}^{\rm mol}}= \frac{\Sigma_{\rm mol}^{\rm kpc}}{\Sigma_{\rm SFR}^{\rm kpc}} ,
\end{equation}$$

expresses the time needed for current star formation to consume the molecular gas reservoir without replenishment. Here $\Sigma_{\rm mol}^{\rm kpc}$ and $\Sigma_{\rm SFR}^{\rm kpc}$ are the mean molecular gas and star formation rate surface densities over the whole large $1.5$-kpc averaging aperture.[^3] Although $\tau_{\rm dep}^{\rm mol}$ is formally a timescale, the physical meaning here is that it expresses the star formation rate per unit molecular gas mass. That is, $(\tau_{\rm dep}^{\rm mol})^{-1}$ is the “specific” star formation rate of molecular gas, so that a short $\tau_{\rm dep}^{\rm mol}$ indicates a high rate of star formation per unit molecular gas.

We also compute the star formation efficiency per free fall time,

$$\begin{equation}
\label{eq:eff}
\epsilon_{\rm ff}^{\rm mol} = \frac{\left< \tau_{\rm ff}^{\rm cloud} \right>}{\ensuremath{\tau_{\rm dep}^{\rm mol}}} ,
\end{equation}$$

which contrasts $\tau_{\rm dep}^{\rm mol}$ with the gravitational free-fall time, $\tau_{\rm ff}^{\rm cloud}$, estimated from the cloud-scale CO imaging. $\epsilon_{\rm ff}^{\rm mol}$ expresses the efficiency of star formation relative to uninhibited gravitational collapse. This is viewed as a theoretically important quantity (cite: MCKEE07REVIEW; FEDERRATH12EFF; FEDERRATH13EFF; KRUMHOLZ14REVIEW) and is often implemented as a controlling parameter in sub-grid models for star formation in numerical simulations (cite: KATZ92SIMS; HOPKINS11SIMS; KIM14SIMS; AGERTZ21SIMS; SEMENOV21GMCS). Nonetheless, we caution that comparing $\epsilon_{\rm ff}^{\rm mol}$ to cloud-scale gas properties unavoidably involves plotting highly correlated quantities against one another, because they all depend on the same cloud-scale CO imaging data.

As with the cloud-scale gas properties, we estimate $\Sigma_{\rm mol}$ from PHANGS–ALMA CO (2-1) imaging using our adopted CO-to-H$_2$ conversion factor. At the $1.5$ kpc resolution where we calculate $\Sigma_{\rm mol}$ and $\tau_{\rm dep}^{\rm mol}$, PHANGS–ALMA yields high significance CO detection for almost every region, and CO flux completeness at low resolution plays little role in our data selection. By default, we estimate $\Sigma_{\rm SFR}$ combining H$\alpha$ narrowband measurements and WISE $22\mu$m mid-infrared emission. These measurements follow (cite: BELFIORE23SFRLARGE) as implemented by (cite: SUN23SFGAS) using narrowband H$\alpha$ maps from A. Razza et al. (in preparation) and $22\mu$m WISE4 maps from (cite: LEROY19Z0MGS). When H$\alpha$ maps are not available, we instead combine GALEX FUV emission and WISE 22$\mu$m emission, and in a handful of cases we use only WISE $22\mu$m emission. Both (cite: SUN23SFGAS) and (cite: QUEREJETA24SFGAS) have both considered star formation scaling relations in this data set and shown that using narrowband H$\alpha$ and/or H$\alpha$+22$\mu$m matches the results using the “gold standard” VLT/MUSE maps to $\approx 0.1$ dex accuracy (though see discussion about next steps in §[4.6](#sec:nextsteps)).

## Data selection and completeness

![](paper_completeness.png)

![image](paper_sfscaling.png) ![image](paper_cloudscaling.png)

Measuring $\Sigma_{\rm mol}^{\rm cloud}$, $\sigma_{\rm mol}^{\rm cloud}$, and $\alpha_{\rm vir}^{\rm cloud}$ requires detecting and characterizing CO (2-1) emission over individual high-resolution lines of sight. In particular, robust detections are required to estimate the velocity dispersion, $\sigma_{\rm mol}$, and virial parameter, $\alpha_{\rm vir}$. PHANGS–ALMA has sensitivity to detect individual $\sim 10^{5}$ M$_\odot$ GMCs in each $60{-}150$ pc beam (cite: PHANGSALMA21SURVEY). However, over many regions much of the CO flux appears associated with lines of sight that have lower surface brightness. This means only a fraction of the total CO flux in each 1.5 kpc region will enter our high-resolution cloud-scale gas property measurements. (cite: SUN22CLOUDS) calculate this CO flux “completeness,”

$$\begin{equation}
\label{eq:fcomp}
f_{\rm comp}^{\rm CO} \equiv \frac{\sum_{\rm high~S/N~mask} \I_{\rm CO}^{\rm cloud}}{\sum_{\rm full~region} I_{\rm CO}^{\rm cloud}}~,
\end{equation}$$

by comparing the flux associated with individually detected high signal-to-noise sightlines (the numerator) to the total CO (2-1) flux[^4] (the denominator). A high $f_{\rm comp}^{\rm CO}$ means that our cloud-scale measurements capture the physical conditions of the *bulk* molecular gas, which is relevant to the overall $\tau_{\rm dep}^{\rm mol}$ in the region. Conversely, a low $f_{\rm comp}^{\rm CO}$ indicates that we merely sample the “tip of the iceberg” and that our cloud-scale measurements are not representative and may have little relevance to region-averaged star formation activity.

(cite: SUN22CLOUDS) correct the measured cloud-scale surface density and $\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$ in each hexagonal region to account for the effects of completeness by assuming lognormal probability distribution function for the surface density, in good agreement with observations (see that paper). However, this implies that in regions with very low $f_{\rm comp}$, the measured cloud properties will represent a rather aggressive extrapolation. With this in mind, we consider a region appropriate for the current analysis if the cloud-scale CO (2-1) completeness $f_{\rm comp}^{\rm CO} > 50\%$.

Figure [2](#fig:completeness) shows $f_{\rm comp}^{\rm CO}$ in PHANGS–ALMA as a function of $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$. Based on this figure we impose a $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ cut at $20$ M$_\odot$ pc$^{-2}$ in addition to requiring $f_{\rm comp}^{\rm CO} > 50\%$. This yields a uniform data set and avoids the case where a few high completeness galaxies dominate low $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ bins and drive our results on their own. Table [1](#tab:experiment) reports the number of hexagonal regions and galaxies that survive these cuts. Applying this criteria to the $\ell = 150$ pc resolution PHANGS–ALMA data set in (cite: SUN22CLOUDS), we select $841$ regions in $67$ galaxies.

## Correlation analysis, binning, fitting, and uncertainties

While parametrized fitting and correlation analyses provide useful insights, we would like to first emphasize the region-by-region measurements as our key products. These represent our best estimates of $\tau_{\rm dep}^{\rm mol}$, $\epsilon_{\rm ff}^{\rm mol}$, and gas properties with a well-understood selection function for a representative set of nearby galaxies. We present the full measurement set in Table [2](#tab:data). Appendix [7](#sec:stepbystep) summarizes this section in a simple, step by step guide that can be used to reproduce matched measurements from simulations or other data sets.

We treat the cloud-scale gas properties as independent variables and measure how $\tau_{\rm dep}^{\rm mol}$ and $\epsilon_{\rm ff}^{\rm mol}$ (the $y$ axis) vary as a function of these mass-weighted average gas properties (the $x$ axis). We measure Spearman’s rank correlation relating $\tau_{\rm dep}^{\rm mol}$ and $\epsilon_{\rm ff}^{\rm mol}$ to each property and fit $y$ as a function of $x$ for each gas property using the functional form

$$\begin{equation}
\label{eq:line}
y = m \left( x - x_0 \right) + b
\end{equation}$$

where $y$ refers to either $\log_{10} \ensuremath{\tau_{\rm dep}^{\rm mol}}$ or $\log_{10} \ensuremath{\epsilon_{\rm ff}^{\rm mol}}$, $x$ to the $\log_{10}$ of one of the gas properties that we consider. We calculate $x_0$ as the median of the $x$ data, then maximize the log-likelihood to infer $m$ and $b$. We also include an intrinsic scatter term in the fit, but this tends to be very small given our adopted uncertainty estimates (see below). We therefore report $\sigma$, the robustly estimated rms residual of the data about each fit.

Because we average over large regions selected to have high $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, the formal statistical uncertainty associated with any individual measurement is small. Instead, systematic effects dominate our uncertainties. In deriving the calibrations that we use for $\Sigma_{\rm SFR}$, (cite: BELFIORE23SFRLARGE) found $\approx 0.15$ dex point-to-point scatter between the estimators that we use and “gold standard” extinction corrected H$\alpha$ estimates from MUSE ((cite: LEROY19Z0MGS) found similar scatter comparing to (cite: GSWLC16)). Our $\alpha_{\rm CO}$ estimate heavily leverages the work of (cite: CHIANG24XCO) who find $\approx 0.2$ dex scatter between their dust-based $\alpha_{\rm CO}^{2-1}$ and the fit to local conditions that we employ. Combining the uncertainties, we consider any individual $\tau_{\rm dep}^{\rm mol}$ estimate to be uncertain by $\approx 0.3$ dex due to uncertainties in our ability to estimate star formation rates and molecular gas masses. We consider molecular gas surface densities to be uncertain by $0.2$ dex at any scale, and $\tau_{\rm ff} \propto \Sigma_{\rm mol}^{-0.5}$ to be uncertain by $0.1$ dex. The main systematic uncertainty on the mass-weighted line width, $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$, is related to measurement technique and correction for sensitivity biases (cite: HENSHAW16GMCS; KOCH18LINEWIDTH; ROSOLOWSKY21GMCS); we consider these $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ values to be uncertain by $\approx 0.15$ dex. When we include these uncertainty estimates in the fitting described above, we find little or no need for an intrinsic scatter term. This may imply that the estimates are slightly conservative, i.e., too large, but they do appear grounded in the current literature.

We observe significant galaxy-to-galaxy scatter in our data, meaning that individual galaxies trace out offset relationships in the $\tau_{\rm dep}^{\rm mol}$ vs. gas properties parameter space. This situation is common in resolved studies of star formation scaling relations (cite: LEROY13SFGAS) and likely reflects a mixture of physical scatter due to unplotted additional parameters and/or systematic uncertainties that operate galaxy by galaxy (e.g., calibration uncertainties, uncertainties in the adopted $\alpha_{\rm CO}$, SFR calibration uncertainties, etc.). We account for this in two ways. First we estimate uncertainties on our fits using a “per galaxy” bootstrapping approach, where we repeatedly re-draw $N$ galaxies from the parent sample and refit the relation between $\tau_{\rm dep}^{\rm mol}$ and gas properties. Second, we construct a version of our plots in which we first normalize the $\tau_{\rm dep}^{\rm mol}$ or $\epsilon_{\rm ff}^{\rm mol}$ for each region by the mean $\tau_{\rm dep}^{\rm mol}$ or $\epsilon_{\rm ff}^{\rm mol}$ for the galaxy in which that region resides and then analyze the normalized results. We calculate the mean $\tau_{\rm dep}^{\rm mol}$ or $\epsilon_{\rm ff}^{\rm mol}$ used for normalization by a molecular mass ($\Sigma_{\rm mol}^{\rm kpc}$) weighted average over the selected regions for that galaxy.

For each variable pair $(x,y)$ we distill the median and 16-84% percentile in $y$ as a function of $x$. To do this, we apply two dimensional gaussian kernel density estimation (KDE) to the data, allowing the bandwidth to be chosen using the default “Scott’s rule” implement in `scipy` (this typically yields bandwidths of $\lesssim 0.3$ dex). We evaluate the density on a regularly spaced grid spanning the 1-99% range of the data in $x$ and the full range of the data in $y$. Then, we calculate the median and 16-84% range in $y$ for each value of $x$ in this grid. The results visually match the spine and span of the data well. We fit lines to the median trends, but found them to be similar to those found fitting the data and only report the fits to the data.

We emphasize that the choice to fit $y$ (i.e., $\tau_{\rm dep}^{\rm mol}$ or $\epsilon_{\rm ff}^{\rm mol}$) while treating $x$ (cloud-scale gas properties) as an independent variable has a significant impact on our results. Our data show significant scatter compared to the dynamic range in both $x$ and $y$, and many of the correlations that we examine are relatively weak. Fitting $x$ as a function of $y$ or conducting a bivariate fit would yield different results. Our adopted scheme is motivated by the desire to address the question “Given some cloud-scale gas properties, how well can we predict $\tau_{\rm dep}^{\rm mol}$?” (see §[1](#sec:intro)). Our selection (§[2.3](#sec:selection)) also imposes a strong selection in $x$, which would need to be carefully accounted for in any bivariate fit (cite: LEROY13SFGAS) but does not affect our adopted approach. The key point for the reader is that rigorous comparison to our fitting results should consider the same formulation of dependent and independent variable.

Finally, note that we examine many cases with correlated axes. In some cases this correlation is explicit, e.g., $\ensuremath{\epsilon_{\rm ff}^{\rm mol}}\propto \langle \left( \Sigma_{\rm mol}^{\rm cloud} \right)^{-0.5} \rangle$. In other cases, e.g., $\tau_{\rm dep}^{\rm mol}$ vs. $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, the correlation depends on a cross-scale relationship between $\Sigma_{\rm mol}$ and $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$. In many cases our adopted $\alpha_{\rm CO}$ affects both axes. We indicate our expectations for covariance with a vector in each plot along with the typical uncertainties.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Galaxy | Radius | $\tau_{\rm dep}^{\rm mol}$ | $\frac{\tau_{\rm dep}^{\rm mol}}{\left< \tau_{\rm dep}^{\rm mol} \right>_{\rm gal}}$ | $\alpha_{\rm CO}^{2-1}$ | $i$ | $\log_{10} M_\star$ | $\log_{10} {\rm SFR}$ | $\left< \Sigma_{mol}^{\rm cloud} \right>$ | $\left< \tau_{ff}^{\rm cloud} \right>$ | $\left< \sigma_{mol}^{\rm cloud} \right>$ | $\left< \alpha_{vir}^{\rm cloud} \right>$ | $\epsilon_{\rm ff}^{\rm mol}$ | $\frac{\epsilon_{\rm ff}^{\rm mol}}{\left< \epsilon_{\rm ff}^{\rm mol} \right>_{\rm gal}}$ |
|  | (kpc) | (Gyr) | (norm.) | ($\frac{{\rm M}_\odot~{\rm pc}^{-2}}{{\rm K~km~s}^{-1}}$) | ($^\circ$) | (M$_\odot$) | (M$_\odot$ yr$^{-1}$) | (M$_\odot$ pc$^{-2}$) | (Myr) | (km s$^{-1}$) |  |  | (norm.) |
| ESO097-013 | 0.0 | 0.11 | 0.35 | 1.73 | 64.3 | 10.5 | 0.6 | 182.0 | 3.57 | 24.5 | 7.38 | 0.0339 | 1.23 |
| ESO097-013 | 1.54 | 0.42 | 1.42 | 3.26 | 64.3 | 10.5 | 0.6 | 25.0 | 9.4 | 8.1 | 4.93 | 0.0223 | 0.81 |
| ESO097-013 | 3.36 | 0.99 | 3.32 | 6.65 | 64.3 | 10.5 | 0.6 | 54.0 | 6.69 | 6.0 | 1.04 | 0.0068 | 0.25 |
| IC1954 | 0.0 | 0.92 | 0.66 | 5.26 | 57.1 | 9.7 | -0.4 | 32.0 | 9.1 | 7.1 | 3.52 | 0.0099 | 1.28 |
| IC1954 | 1.82 | 1.71 | 1.23 | 8.29 | 57.1 | 9.7 | -0.4 | 25.0 | 10.65 | 4.7 | 2.05 | 0.0062 | 0.8 |
| IC1954 | 1.82 | 1.41 | 1.02 | 8.14 | 57.1 | 9.7 | -0.4 | 22.0 | 11.35 | 4.6 | 2.37 | 0.0081 | 1.04 |
| IC1954 | 1.97 | 1.52 | 1.1 | 8.29 | 57.1 | 9.7 | -0.4 | 29.0 | 9.92 | 5.2 | 2.36 | 0.0065 | 0.84 |
| IC1954 | 1.97 | 1.54 | 1.11 | 8.42 | 57.1 | 9.7 | -0.4 | 25.0 | 10.76 | 5.1 | 2.51 | 0.007 | 0.9 |
| IC1954 | 2.76 | 1.44 | 1.04 | 9.43 | 57.1 | 9.7 | -0.4 | 21.0 | 11.57 | 4.6 | 2.3 | 0.008 | 1.03 |

: Measurements for individual regions at $\ell = 150$ pc in 1.5 kpc diameter regions

Table notes: This is a stub. The full table is available online as part of a machine readable table. Columns: (1) galaxy name, (2) galactocentric radius, (3) molecular gas depletion time, (4) molecular gas depeletion time normalized to galaxy average, (5) CO (2-1) to H$_2$ conversion factor, (6) galaxy inclination, (7) galaxy integrated stellar mass, (8) galaxy integrated star formation rate, region-averaged mass weighted molecular gas: (9) surface density, (10) gravitational free-fall time, (11) line width, and (12) virial parameter, (13) star formation efficiency per free fall time, (14) star formation efficiency per free fall time normalized to galaxy average.

# Results

| $x$ | Rank. corr. | $m$ | $x_0$ | $b$ | $\sigma$ |
|:--:|:--:|:--:|:--:|:--:|:--:|
| — | — | — | — | $9.33$ | $0.3$ |
| $\log_{10} \left< \tau_{\rm ff}^{\rm cloud} \right>$ | $0.18$ | $0.51$ | $6.94$ | $9.31$ | $0.28$ |
| (normalized) | $0.28$ | $0.43$ | — | — | $0.18$ |
| $\log_{10} \left< \Sigma_{\rm mol}^{\rm cloud} \right>$ | $-0.22$ | $-0.3$ | $1.58$ | $9.32$ | $0.28$ |
| (normalized) | $-0.28$ | $-0.23$ | — | — | $0.18$ |
| $\log_{10} \left< \sigma_{\rm mol}^{\rm cloud} \right>$ | $-0.31$ | $-0.48$ | $0.74$ | $9.32$ | $0.26$ |
| (normalized) | $-0.31$ | $-0.3$ | — | — | $0.18$ |
| $\log_{10} \left< \alpha_{\rm vir}^{\rm cloud} \right>$ | $-0.27$ | $-0.27$ | $0.3$ | $9.31$ | $0.27$ |
| (normalized) | $-0.21$ | $-0.11$ | — | — | $0.19$ |

: $\tau_{\rm dep}^{\rm mol}$ and cloud-scale gas properties

Table notes: Results correlating $\tau_{\rm dep}^{\rm mol}$ with cloud-scale gas properties for our fiducial sample of regions with high gas surface density. Cloud scale properties measured at 150 pc resolution, and our best estimate $\alpha_{\rm CO}$. Fit has form $y = m (x - x_0) + b$. Quantities defined in Table [1](#tab:experiment). Normalized results first normalize $\tau_{\rm dep}^{\rm mol}$ by the galaxy-average value.

Our selection yields gas properties, molecular gas depletion times, and estimates of the star formation efficiency per free fall time for $841$ independent $1.5$ kpc-sized regions in $67$ galaxies with properties measured at $\ell = 150$ pc resolution (we also make measurements using higher resolution CO data, though for fewer galaxies, and provide these in Appendix [8](#sec:resn)). Table [1](#tab:experiment) summarizes the selection and other details of the experiment. Our core results are the measurements of and relationships between $\tau_{\rm dep}^{\rm mol}$, $\epsilon_{\rm ff}^{\rm mol}$, and cloud-scale gas properties. We present the measurements in Table [2](#tab:data), summarize the correlation analyses in Tables [3](#tab:tdep), [4](#tab:fixaco), and [5](#tab:eff), and illustrate the results in § [3.1](#sec:tdepvstff) through § [3.6](#sec:effvsprops), but first we show the properties of our selected regions in Figure [3](#fig:scaling).

The left panel in Figure [3](#fig:scaling) shows the region-averaged $\Sigma_{\rm SFR}$ as a function of $\Sigma_{\rm mol}$ for our working data set. These measurements do not involve cloud-scale information but simply show the resolved molecular Kennicutt-Schmidt relation at 1.5 kpc scales. Our selected regions span more than an order of magnitude in $\Sigma_{\rm SFR}$ and $\Sigma_{\rm mol}$. The selected data agree well with the power-law fit by (cite: SUN23SFGAS), shown by the dashed line,[^5] in which $\Sigma_{\rm SFR} \propto \Sigma_{\rm mol}^{1.2}$. This slope reflects that the highest surface density regions in our targets also have the shortest $\tau_{\rm dep}^{\rm mol}$.

The right panel in Figure [3](#fig:scaling) presents a complementary view, now with cloud-scale information. It shows mass-weighted, region-averaged, cloud-scale velocity dispersion normalized by the adopted size scale, $\ensuremath{\langle \sigma_{\rm mol}^{\rm cloud} \rangle}/ R_{\rm pix}^{0.5}$, as a function of the cloud-scale surface density, $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$. Our selection also samples $> 1.5$ dex in $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, and $\approx 1$ dex in $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$. On average, our target regions follow the “Heyer-Keto” relation of $\sigma_{\rm mol}^{\rm cloud} / R_{\rm pix}^{0.5} \propto \left( \Sigma_{\rm mol}^{\rm cloud}\right)^{0.5}$. This is expected among gas structures with similar dynamical state, i.e., similar $\alpha_{\rm vir}$ values (cite: HEYER09GMCS; HEYER15REVIEW; SUN18CLOUDS; SUN20GMCS; SCHINNERER24REVIEW). As a result of this, $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ are significantly correlated, and we will see similar relationships between $\tau_{\rm dep}^{\rm mol}$ and these two quantities.

While $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ show a strong correlation, there is still substantial scatter and significant deviations from the fiducial Heyer-Keto relation. In particular, a subset of regions show enhanced $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ at fixed $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$. The gas in these regions has high $\ensuremath{\langle \alpha_{\rm vir}^{\rm cloud} \rangle}\propto \left( \sigma_{\rm mol}^{\rm cloud}\right)^2 / (R_{\rm pix} \Sigma_{\rm mol}^{\rm cloud})$ and thus appears less bound by self-gravity. These high $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ data often come from the inner parts of galaxies and show high $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$. There, stellar gravity can more strongly affect the molecular gas dynamical state, and unresolved streaming motions and shadowing of multiple components may also contribute to the observed broad CO line width (cite: MEIDT13SFGAS; MEIDT18GMCS; SUN18CLOUDS; SUN20GMCS). We return to this point in more detail in §[3.4](#sec:byrad).

## Molecular gas depletion time as a function of gravitational free-fall time

![](paper_tdep_vs_tff.png)

Figure [4](#fig:tdepvstff) plots $\tau_{\rm dep}^{\rm mol}$ as a function of the region-averaged cloud-scale gravitational free-fall time, $\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$. All other things being equal, higher density gas should form stars faster, and the characteristic time for the gas to collapse under its own gravity, $\tau_{\rm ff} \propto \rho^{-0.5} \propto \left( \Sigma_{\rm mol}^{\rm cloud} \right)^{-0.5}$, has been considered a key timescale in this context.

![image](paper_tdep_vs_tff_bygal.png) ![image](paper_tdepnorm_vs_tff_bygal.png)

Figure [4](#fig:tdepvstff) does show a weak correlation between $\tau_{\rm dep}^{\rm mol}$ and $\langle \tau_{\rm ff}^\mathrm{cloud} \rangle$, with Spearman rank correlation coefficient $0.18$. Gas with higher density (low $\langle \tau_{\rm ff}^{\rm cloud} \rangle$) coincides with regions that show higher star formation rate per unit gas (low $\tau_{\rm dep}^{\rm mol}$). The blue line showing fixed $\ensuremath{\epsilon_{\rm ff}^{\rm mol}}$ shows that a single $\epsilon_{\rm ff}^{\rm mol}$ can reasonably describe the bulk of the measurements. Most of the data lie within $\pm 0.3$ dex (i.e., a factor of two) of the blue line (cite: SUN23SFGAS). A fixed $\ensuremath{\epsilon_{\rm ff}^{\rm mol}}$ thus provides a reasonable approximate description of the data. But in detail, $\ensuremath{\epsilon_{\rm ff}^{\rm mol}}$ tends to be somewhat higher (i.e., the points lie below the blue line) at high $\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$, corresponding to low density. This manifests as a best fit $\tau_{\rm dep}^{\rm mol}$–$\langle \tau_{\rm ff}^{\rm cloud} \rangle$ relation with slope $m = 0.51$ (the red line, Table [3](#tab:tdep)). This is shallower than the $\ensuremath{\tau_{\rm dep}^{\rm mol}}\propto \ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$ expected for fixed $\epsilon_{\rm ff}^{\rm mol}$, though we reiterate that this specific slope depends on the choice to fit $\ensuremath{\tau_{\rm dep}^{\rm mol}}$ while treating $\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$ as the independent variable (see §[2.4](#sec:fits)).

The right panel in Fig. [4](#fig:tdepvstff) also shows $\tau_{\rm dep}^{\rm mol}$ as a function of $\langle \tau_{\rm ff}^{\rm cloud} \rangle$ but first normalizes $\tau_{\rm dep}^{\rm mol}$ by the galaxy-average value. Normalizing leads to an even sharper correlation (Tab. [3](#tab:tdep)), with the rank correlation coefficient increasing to $0.28$ after normalization. This indicates that $\ensuremath{\tau_{\rm dep}^{\rm mol}}$ correlates better with $\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$ within individual galaxies. The best fit $\ensuremath{\tau_{\rm dep}^{\rm mol}}{-}\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$ slope becomes slightly shallower after normalization (Tab. [3](#tab:tdep)), $m = 0.43$, but the overall picture appears similar as in the left panel.

Fig. [5](#fig:tdepbygal) shows why normalizing by galaxy-average $\ensuremath{\tau_{\rm dep}^{\rm mol}}$ sharpens the $\ensuremath{\tau_{\rm dep}^{\rm mol}}{-}\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$ relation. We plot binned results for individual galaxies before any normalization in the left panel. To a large extent, galaxies trace offset relations in the $\tau_{\rm dep}^{\rm mol}$–$\langle \tau_{\rm ff}^{\rm cloud} \rangle$ space. This reflects some overall correlation of $\tau_{\rm dep}^{\rm mol}$ with host galaxy properties, with a general sense that lower mass galaxies show shorter $\ensuremath{\tau_{\rm dep}^{\rm mol}}$ (i.e., darker lines tend to appear lower in Fig. [5](#fig:tdepbygal)). This might reflect real physics, or might reflect that the metallicity-dependence in our $\alpha_{\rm CO}$ prescription remains too weak (cite: MAIOLINO19REVIEW). Global variation of $\tau_{\rm dep}^{\rm mol}$ as a function of $M_\star$ has been considered extensively (cite: SAINTONGE11SFGAS; SAINTONGE17SFGAS; SAINTONGE22REVIEW; SCHRUBA12XCO; LEROY13SFGAS; TACCONI20REVIEW). For our purposes, the key points are that (1) $\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$ variations do not appear to explain all of the observed galaxy-to-galaxy scatter (nor do $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$, or $\alpha_{\rm vir}$ variations), and (2) $\tau_{\rm dep}^{\rm mol}$ correlates with $\langle \tau_{\rm ff}^{\rm cloud} \rangle$ more strongly within individual galaxies.

In the right panels in Fig. [4](#fig:tdepvstff) and [5](#fig:tdepbygal), after normalization most galaxies lie together along a common relation, with individual regions showing rms scatter $\approx 0.2$ dex about the median trend. This represents ${\sim}\sqrt{2}$ times lower scatter than we find before normalizing, implying that about half the total scatter in $\tau_{\rm dep}^{\rm mol}$ can be attributed to galaxy-to-galaxy scatter, while the rest represents scatter within individual galaxies. This resembles results from previous work on $\tau_{\rm dep}^{\rm mol}$ and kpc-scale star formation scaling relations by (cite: LEROY13SFGAS) and (cite: JIMENEZ19DENSE).

## Molecular gas depletion time as a function of cloud-scale surface density and line width

![image](paper_tdep_vs_sd.png) ![image](paper_tdep_vs_vdisp.png)

Fig. [6](#fig:tdep_vs_gasprops) shows $\tau_{\rm dep}^{\rm mol}$ as a function of cloud-scale gas surface density, $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, and velocity dispersion, $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$. Tab. [3](#tab:tdep) reports results for the corresponding correlation analysis. $\ensuremath{\tau_{\rm dep}^{\rm mol}}$ anti-correlates with both quantities. Surface density and velocity dispersion represent more direct observables than $\langle \tau_{\rm ff}^{\rm cloud} \rangle$, and we therefore view these as our most fundamental results. They should be easy to reproduce by applying our methodology to simulations or other data sets (following Appendix [7](#sec:stepbystep)).

To first order, Figs. [4](#fig:tdepvstff) and [6](#fig:tdep_vs_gasprops) could be viewed as three different manifestations of the same underlying relationship between gas density and star formation efficiency. Because[^6] $$\begin{eqnarray}
\tau_{\rm dep}^{\rm mol} &=& \frac{\tau_{\rm ff}^\mathrm{cloud}}{\ensuremath{\epsilon_{\rm ff}^{\rm mol}}} \\
\nonumber \tau_{\rm ff}^\mathrm{cloud} &=& \sqrt{\pi / (8 G \Sigma_{\rm mol}^\mathrm{cloud} / R_{\rm cloud})}
\end{eqnarray}$$ so that for a fixed $\epsilon_{\rm ff}^{\rm mol}$ and size scale, $$\begin{equation}
\label{eq:tdepsdmol}
\ensuremath{\tau_{\rm dep}^{\rm mol}}\propto \ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}^{-0.5}
\end{equation}$$ The expected anti-correlation with $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ emerges because for fixed dynamical state, $\alpha_{\rm vir}$ (cite: HEYER09GMCS; SUN18CLOUDS; ROSOLOWSKY21GMCS; SCHINNERER24REVIEW), $\Sigma_{\rm mol}$ and $\sigma_{\rm mol}$ are related as $$\begin{eqnarray}
\sigma_{\rm mol} &=& \sqrt{\alpha_{\rm vir}~R~\frac{f G \pi \Sigma_{\rm mol}}{5}} 
\end{eqnarray}$$ with $f$ a geometrical factor related to the cloud density distribution (Table [1](#tab:experiment)). Since $\sigma_{\rm mol} \propto \sqrt{\Sigma_{\rm mol}}$ at given $\alpha_\mathrm{vir}$ and size scale, we expect $$\begin{eqnarray}
\label{eq:tdepsigmol}
\tau_{\rm mol}^{\rm dep} \propto \ensuremath{\langle \sigma_{\rm mol}^{\rm cloud} \rangle}^{-1}
\end{eqnarray}$$ The expected scaling between $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ and $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ appears in our data (cite: SUN18CLOUDS; SUN20GMCS; ROSOLOWSKY21GMCS). We indicate power-laws with the fiducial slopes (Eqs. [\[eq:tdepsdmol\]](#eq:tdepsdmol) and [\[eq:tdepsigmol\]](#eq:tdepsigmol)) as blue lines in Fig. [6](#fig:tdep_vs_gasprops).

As in Fig. [4](#fig:tdepvstff), most of the data lie within $\pm 0.3$ dex of the fiducial relationships, though our fit relations again have shallower slopes compared to the expectations for fixed $\epsilon_{\rm ff}^{\rm mol}$, fixed dynamical state clouds: $m = -0.3$ for $\ensuremath{\tau_{\rm dep}^{\rm mol}}{-}\ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}$ (compared to $-0.5$ expected) and $m = -0.48$ for $\ensuremath{\tau_{\rm dep}^{\rm mol}}{-}\ensuremath{\langle \sigma_{\rm mol}^{\rm cloud} \rangle}$ (compared to $-1$ expected). Again we caution that the adopted methodology affects the precise value of the fit slopes.

Our results for the $\ensuremath{\tau_{\rm dep}^{\rm mol}}{-}\ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}$ relationship match limited previous measurements. In M51, (cite: LEROY17SFGAS) found $\ensuremath{\tau_{\rm dep}^{\rm mol}}\propto \ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}^{-0.14}$ (using fixed $\alpha_{\rm CO}$). Adopting the (cite: BOLATTO13REVIEW) CO-to-H$_2$ prescription, similar to what we use here, the (cite: SUN23SFGAS) fit to the “free-fall time regulated star formation” relation yields $\Sigma_{\rm SFR}^{\rm kpc} \propto \left( \Sigma_{\rm mol}^{\rm kpc} / \ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}\right)^{0.75}$, which implies $\ensuremath{\tau_{\rm dep}^{\rm mol}}\propto \ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}^{-0.125}$ to $\ensuremath{\tau_{\rm dep}^{\rm mol}}\propto \ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}^{-0.375}$ depending on the precise dependence of $\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$ on $\Sigma_{\rm mol}^{\rm kpc}$. Our fit value lies intermediate in this regime. They also used the PHANGS–ALMA dataset, so this does not represent an independent measurement, but they did use a different selection and fitting methodology.

We emphasize the $\tau_{\rm dep}^{\rm mol}$ vs. $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ anti-correlation as a useful and new way to approach this topic. This anti-correlation is physically expected for fixed $\epsilon_{\rm ff}^{\rm mol}$, fixed dynamical state clouds (Eq. [\[eq:tdepsigmol\]](#eq:tdepsigmol)). This first-order expectation does not involve any turbulence physics, it simply reflects that the gas velocity dispersion traces the underlying gravitational potential of the clouds.

This $\tau_{\rm dep}^{\rm mol}$ vs. $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ relationship is particularly intriguing because $\alpha_{\rm CO}$ only affects the vertical axis[^7], so that these plots have less built-in covariance between the axes than most of the other relationships we consider (though see below). Moreover, $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ may not depend as sensitively on resolution as $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$. In the limit of an isolated, low-mass, unresolved cloud, ALMA might still measure an accurate CO line width given enough sensitivity, whereas in this situation $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ will be strongly affected by beam dilution.

We note that near galaxy centers, the blending of multiple clouds along the line of sight can be a concern, especially at our resolution (cite: ROSOLOWSKY21GMCS). When estimating the CO line width using moment methods, this can lead the moment-based line width to reflect the inter-cloud dispersion rather than the line width of any individual component (cite: JEFFRESON22GMCS). Our line width measurements are not second moments but “effective widths” (cite: HEYER01GMCS; LEROY16GMCS; SUN22CLOUDS) derived from the ratio of the line integral to the peak, $\sigma \equiv I_{\rm CO} / \sqrt{2 \pi} I_{\rm pk}$. This has less sensitivity to any inter-cloud dispersion but will still be biased high in case of multi-velocity components. It will be interesting to explore how different line width measures correlate with $\ensuremath{\tau_{\rm dep}^{\rm mol}}$ and important to match methodology when comparing to our measurements.

## Molecular gas depletion time as a function of cloud-scale virial parameter

![](paper_tdep_vs_avir.png)

Fig. [7](#fig:tdep_vs_avir) shows $\tau_{\rm dep}^{\rm mol}$ as a function of $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, the region-mean cloud-scale virial parameter. Theoretical models of star formation in turbulent clouds make a clear prediction that, all other things being equal, $\tau_{\rm dep}^{\rm mol}$ should correlate with $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$. This reflects that more gravitationally bound gas should form stars more effectively. In Fig. [7](#fig:tdep_vs_avir) the dashed line shows the expected relationship from (cite: PADOAN12EFF) for fixed $\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$; similar predictions would arise from, e.g., (cite: KRUMHOLZ05EFF) or (cite: FEDERRATH12EFF; FEDERRATH13EFF). Our observations do not show the predicted correlation. In fact, we observe an anti-correlation between $\tau_{\rm dep}^{\rm mol}$ and $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, such that gas less bound by self-gravity appears to form stars more efficiently. We find a best-fit slope of $m = -0.27$, though this drops to $m = -0.11$ after normalize each galaxy by its mean $\tau_{\rm dep}^{\rm mol}$.

Though contradictory at first glance, this observation fits well with our current understanding of gas properties in the context of galaxy structure. We see that short $\tau_{\rm dep}^{\rm mol}$ regions often correspond to galaxy centers, which also show high $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ (cite: SUN20GMCS; SUN22CLOUDS). This high $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ can be at least partially attributed to the importance of stellar gravity to molecular gas dynamics in the inner parts of galaxies. Observations suggest that the high stellar and gas mass densities lead to high gas pressures in the inner parts of massive galaxies. This pressure then turns the overwhelming bulk of gas molecular (cite: WONG02SFGAS; BLITZ06PRESS; LEROY08SFGAS; EIBENSTEINER2024RMOL). This can lead to the emergence of a “diffuse,” high velocity dispersion medium, in which the gas is bound by the larger-scale galactic potential. This large scale potential is dominated by stellar gravity, not by its own self-gravity. The high stellar densities in the inner regions of galaxies can rival the gas density even within molecular complexes, playing an important role in force balance (cite: MEIDT18GMCS; SUN20PRESS; LIU21GMCS). Moreover, observations suggest that stellar density correlates with molecular gas morphology, addition additional support to the view that stellar gravity exerts an important dynamical effect (cite: LIU21GMCS; DAVIS22GMCS).

The denser, inner regions of galaxies show high $\alpha_{\rm vir}$ because, following standard practice for molecular cloud studies, our $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ only accounts for gas self-gravity. In cases where the stellar gravity dominates, $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ will not capture the true dynamical state of the gas. The expectations mentioned in §[1](#sec:intro) and §[2](#sec:methods), including the blue line from (cite: PADOAN12EFF) in Fig. [7](#fig:tdep_vs_avir) emerge from theories of turbulent gas-only clouds, and do not typically account for a realistic galactic potential or conditions typical of dense inner galaxies.

Our result has the opposite sense of the trend measured in M51 by (cite: LEROY17SFGAS), where the expected correlation between $\tau_{\rm dep}^{\rm mol}$ and $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ was present. Our results finding no overall correlation between $\epsilon_{\rm ff}^{\rm mol}$ and $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ below do agree with their results in M51 and those of (cite: SCHRUBA19GMCS) studying molecular cloud populations in eight galaxies. M51 may be relatively rare in that the highest $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ are driven by streaming motions along the spiral arms, which correspond to regions of suppressed star formation (cite: MEIDT13SFGAS). This may represent a distinct physical case from the high $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ seen in the centers of late type galaxies, which are not generally associated with suppressed star formation. The high $\alpha_{\rm vir}^{\rm cloud}$ found in early-type galaxies, which *are* associated with suppressed star formation may represent yet a third regime (cite: WILLIAMS23GMCS; LU24GMCs)

A related effect where $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ misses the full picture has been discussed in the context of H I-dominated, low surface density parts of galaxies by (cite: SUN18CLOUDS; SUN20GMCS) and (cite: SCHRUBA19GMCS), following (cite: FIELD11GMCS). There, atomic gas may make significant contributions to the cloud mass, or molecular gas may represent simply the dense subset of a larger turbulent neutral medium. Our selection largely excludes such regions (see §[2.3](#sec:selection) and §[3.4](#sec:byrad)), because PHANGS–ALMA lacks the surface brightness sensitivity to achieve high flux completeness at high resolution in such environments. This represents an area for future investigation, and likely relates to why we find results with the opposite direction from the Milky Way work by (cite: EVANS21GMCS). Their analysis pivots on the behavior of gas at relatively large galactocentric radii and low $\Sigma_{\rm SFR}$ compared to what we study here and, as they discuss, depends sensitively on the metallicity dependence of $\alpha_{\rm CO}$.

## $\tau_{\rm dep}^{\rm mol}$, gas properties, and galactocentric radius

![](paper_props_vs_rgal.png)

As a general rule, high $\Sigma_{\rm mol}^{\rm kpc}$ can be found in the inner regions of galaxies, with the highest values at galaxy centers (cite: YOUNG91SFGAS; YOUNG95SFGAS; REGAN01SFGAS; KUNO07CO; QUEREJETA21). The same is true for $\Sigma_{\rm mol}^{\rm cloud}$ and $\sigma_{\rm mol}^{\rm cloud}$ (cite: JOGEE05SFGAS; SUN20GMCS; SUN22CLOUDS; henshaw2023). Figure [8](#fig:gasprops_vs_rad) shows the cloud-scale gas properties and $\tau_{\rm dep}^{\rm mol}$ as functions of galactocentric radius in our data set.

All these properties of interest show clear radial trends. The innermost $1.5$ kpc hexes show high $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, high $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$, high $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, and low $\tau_{\rm dep}^{\rm mol}$. The region-averaged $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, determined by the ratio of $(\sigma_{\rm mol}^{\rm cloud})^2 / \Sigma_{\rm mol}^{\rm cloud}$, shows a strong radial trend, declining with increasing radius out to radius $> 4$ kpc (cite: SUN20GMCS). In §[3.2](#sec:tdepvsprops) and [3.3](#sec:tdepvsavir) we noted that stellar gravity likely plays an important role in the behavior of $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$. Unresolved streaming or bulk motions may also affect $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ (cite: MEIDT13SFGAS; MEIDT18GMCS), though beam smearing is not expected to exert a large impact at the resolution of PHANGS–ALMA (cite: LANG20KINEMATICS; SUN20GMCS).

$\tau_{\rm dep}^{\rm mol}$ also shows a radial trend with lower values in galaxy centers. After normalization by the galaxy mean $\tau_{\rm dep}^{\rm mol}$, the strongest effect is lower central $\tau_{\rm dep}^{\rm mol}$ compared to the disk average. This radial trend in normalized $\tau_{\rm dep}^{\rm mol}$, which appears relatively flat with a moderate central depression and large scatter, is consistent with similar measurements for the HERACLES sample by (cite: LEROY13SFGAS) and analysis of the COMING survey by (cite: MURAOKA19COMING). The low central $\tau_{\rm dep}^{\rm mol}$ in PHANGS–ALMA has previously been shown by (cite: TENG24XCO), who also demonstrate that this result depends critically on the treatment of $\alpha_{\rm CO}$ (cite: LEROY13SFGAS; DENBROK23XCO). We expand on this in §[3.5](#sec:alphaco).

The regularity of the trends in Fig. [8](#fig:gasprops_vs_rad) reinforce that the cloud-scale gas properties couple to the overall disk structure. Over the last decade, observations have shown that the ${\sim}50{-}150$ pc resolution properties of molecular gas, including $\Sigma_{\rm mol}^{\rm cloud}$ and $P_{\rm int}^{\rm cloud} \propto \Sigma_{\rm mol} \sigma^2_{\rm mol}$, correlate with the large scale properties of the galaxy disk (cite: HUGHES13GMCS; SCHRUBA19GMCS; SUN18CLOUDS; SUN20PRESS; SUN20GMCS; SUN22CLOUDS; SCHINNERER24REVIEW). (cite: SUN22CLOUDS), in particular, provide an extensive series of scaling relations that link cloud-scale gas properties, measured using pixel statistics and cloud-finding methods, to the local kpc-scale conditions in the gas disk (cite: SCHINNERER24REVIEW).

This regularity in the variation of gas properties in disks means that the correlations between $\tau_{\rm dep}^{\rm mol}$ (or $\epsilon_{\rm ff}^{\rm mol}$) and any cloud-scale gas properties almost always have hidden variables related to galactic structure. To show this, Fig. [9](#fig:tdepbyrad) shows $\tau_{\rm dep}^{\rm mol}$ as a function of $\langle \tau_{\rm ff}^{\rm cloud} \rangle$ again (as Fig. [4](#fig:tdepvstff)), but now coloring the points as a function of galactocentric radius. A clear radial trend is visible in the plot, demonstrating that because of the link between gas properties and $\sim$kpc scale environment in real galaxies, this plot focused on small scale conditions in the gas cannot be easily separated from the rest of galactic structure. We return to this in §[4.3](#sec:densdisc).

Fig [8](#fig:gasprops_vs_rad) and [9](#fig:tdepbyrad) also highlight that the inner regions of galaxies are critical to achieve dynamic range in both $\tau_{\rm dep}^{\rm mol}$ and the cloud-scale gas properties. These are the source of our high $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, high $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$, high $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, low $\langle \tau_{\rm ff}^{\rm cloud} \rangle$, low $\tau_{\rm dep}^{\rm mol}$ points. As noted above, extreme conditions in inner galaxies are well established. In high mass, barred galaxies, the central regions often represent distinct dynamical environments with high surface and volume densities and deep stellar potential wells (cite: KORMENDY04REVIEW; MEIDT18GMCS; QUEREJETA21; DAVIS22GMCS; SCHINNERER24REVIEW). These regions also show enhanced CO emissivity (cite: SANDSTROM13XCO; TENG22XCO; TENG23XCO; DENBROK23XCO; CHIANG24XCO), which manifest as variations in $\alpha_{\rm CO}$. The nature of our sampling scheme, in which each region covers equal area in the galaxy disk, means that these key environments are covered by relatively few data points. It is worth keeping the importance of these scarcer low $\tau_{\rm dep}^{\rm mol}$, high $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, high $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ points in mind when examining the plots.

Note that the enhanced densities and shorter $\tau_{\rm dep}^{\rm mol}$ conditions observed in galaxy centers refer to the gas, which is often concentrated into bar-fed central molecular zones. Viewed more broadly, massive galaxies often show depressed specific star formation rates, SFR/$M_\star$, in their inner regions (cite: BELFIORE18RPROF; ELLISON18RPROF). In massive galaxies with bulges, this can reflect the presence of gas-free regions with low $\Sigma_{\rm SFR}$. In follow up work, (cite: PAN24SFGAS) do suggest a longer $\tau_{\rm dep}^{\rm mol}$ in the central regions of main sequence galaxies compared to their disks (cite: PAN22TIMES). As discussed in §[3.5](#sec:alphaco) and (cite: TENG24XCO) and (cite: LEROY13SFGAS), the treatment of $\alpha_{\rm CO}$ has a large impact on inferred $\tau_{\rm dep}^{\rm mol}$ for galaxy centers and we consider the evidence for low $\alpha_{\rm CO}$ in central molecular zones strong. Still, reconciling these measurements will be an area worth future investigation.

![image](paper_tdep_vs_tff_byrad.png) ![image](paper_tdepnorm_vs_tff_byrad.png)

## The key role of the CO-to-$H_2$ conversion factor

| $x$ | Rank. corr. | $m$ | $x_0$ | $b$ | $\sigma$ |
|:--:|:--:|:--:|:--:|:--:|:--:|
| — | — | — | — | $9.4$ | $0.28$ |
| $\log_{10} \left< \tau_{\rm ff}^{\rm cloud} \right>$ | $-0.18$ | $-0.21$ | $6.91$ | $9.37$ | $0.27$ |
| (normalized) | $0.01$ | $0.0$ | — | — | $0.16$ |
| $\log_{10} \left< \Sigma_{\rm mol}^{\rm cloud} \right>$ | $0.13$ | $0.08$ | $1.66$ | $9.38$ | $0.27$ |
| (normalized) | $-0.03$ | $-0.01$ | — | — | $0.16$ |
| $\log_{10} \left< \sigma_{\rm mol}^{\rm cloud} \right>$ | $0.14$ | $0.2$ | $0.74$ | $9.37$ | $0.27$ |
| (normalized) | $0.09$ | $0.07$ | — | — | $0.16$ |
| $\log_{10} \left< \alpha_{\rm vir}^{\rm cloud} \right>$ | $0.19$ | $0.1$ | $0.33$ | $9.37$ | $0.26$ |
| (normalized) | $0.18$ | $0.05$ | — | — | $0.16$ |

: $\tau_{\rm dep}^{\rm mol}$ and cloud-scale gas properties for fixed $\alpha_{\rm CO}$

Table notes: Results correlating $\tau_{\rm dep}^{\rm mol}$ with cloud-scale gas properties for our fiducial sample of regions with high gas surface density. Cloud scale properties measured at 150 pc resolution, and a fixed, Milky Way $\alpha_{\rm CO}$. Fit has form $y = m (x - x_0) + b$. Quantities defined in Table [1](#tab:experiment). Normalized results first normalize $\tau_{\rm dep}^{\rm mol}$ by the galaxy-average value.

As described in §[2](#sec:methods), we repeat our analysis using a fixed $\alpha_{\rm CO}$ instead of our best estimate. Fig. [10](#fig:tdep_alphaco) shows these results for the $\ensuremath{\tau_{\rm dep}^{\rm mol}}{-}\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$ relation and Table [4](#tab:fixaco) reports results of the correlation analysis between $\tau_{\rm dep}^{\rm mol}$ and all quantities for fixed $\alpha_{\rm CO}$. The fixed $\alpha_{\rm CO}$ leads to a nearly constant $\tau_{\rm dep}^{\rm mol}$, in contrast to the fiducial results with our best-estimate $\alpha_{\rm CO}$. This, in turn, leads to almost no correlation or even an anti-correlation between $\tau_{\rm dep}^{\rm mol}$ and $\langle \tau_{\rm ff}^{\rm cloud} \rangle$. Contrasting this with Table [3](#tab:tdep), all relationships show weaker correlations and slopes closer to 0.0 at fixed $\alpha_{\rm CO}$. Moreover, the actual sense of the correlation changes in most cases. With fixed $\alpha_{\rm CO}$, $\tau_{\rm dep}^{\rm mol}$ appears longer for high $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ and high $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$. The sense of the $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ trend also reverses compared to our fiducial case, with higher $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ corresponding to higher $\tau_{\rm dep}^{\rm mol}$, meaning less efficient star formation. All of these trends are weak, however, especially when considering the $\tau_{\rm dep}^{\rm mol}$ normalized by the galaxy average.

Our fiducial $\alpha_{\rm CO}$ treatment, adopted from (cite: SCHINNERER24REVIEW), accounts for variations in excitation and emissivity (sometimes referred to as the “starburst” term) and metallicity (the “CO-dark” term), similar to (cite: BOLATTO13REVIEW). For the present work, the excitation and emissivity variations represent the key terms. In our prescription, $\alpha_{\rm CO}^{1-0} \propto \Sigma_\star^{-0.25}$ where $\Sigma_\star > 100$ M$_\odot$ pc$^{-2}$ (cite: CHIANG24XCO), reflecting emissivity variations, and $\alpha_{\rm CO}^{2-1}$ also $\propto \Sigma_{\rm SFR}^{-0.125}$ (cite: LEROY22LINES; DENBROK21LINES; YAJIMA21LINES), reflecting excitation variations affecting the CO (2-1)/CO (1-0) line ratio $R_{21}$. Because our selection focuses on the high surface density parts of galaxies (e.g., Fig. [3](#fig:scaling)), these terms together significantly affect the estimated molecular gas mass across our sample. The metallicity term, which is critical to integrated galaxy measurements, has a weaker effect here that primarily affects the galaxy-to-galaxy scatter (e.g., Fig. [5](#fig:tdepbygal)).

The impact of $\alpha_{\rm CO}$ on $\tau_{\rm dep}^{\rm mol}$ in galaxy centers has been noted before (cite: LEROY13SFGAS; DENBROK23XCO; TENG23XCO). In particular, in PHANGS–ALMA, (cite: TENG24XCO) showed that accounting for the emissivity terms in $\alpha_{\rm CO}$ lead to much shorter $\tau_{\rm dep}^{\rm mol}$ in galaxy centers, and a much steeper, even multi-valued $\Sigma_{\rm SFR}{-}\Sigma_{\rm mol}$ relationship. (cite: SUN23SFGAS) show a similar effect when applying the (cite: BOLATTO13REVIEW) $\alpha_{\rm CO}$ prescription (which includes an emissivity term) to PHANGS–ALMA. They show that including this term steepens the molecular Kennicutt-Schmidt relation from $\Sigma_{\rm SFR} \propto \Sigma_{\rm mol}^{1.0}$ to $\Sigma_{\rm SFR} \propto \Sigma_{\rm mol}^{1.2}$.

It is worth emphasizing the strong evidence for a variable $\alpha_{\rm CO}$, and specifically for emissivity and excitation variations. Both independent dust-based $\alpha_{\rm CO}$ estimates (cite: SANDSTROM13XCO; CHIANG24XCO) and multi-transition, multi-species spectral line modeling (cite: ISRAEL20XCO; TENG22XCO; TENG23XCO; KEENAN24LINES) agree that the CO emission per unit molecular gas mass is higher in inner galaxies. Similarly, numerous observations agree that high $\Sigma_{\rm SFR}$, inner regions of galaxies show enhanced CO excitation (cite: HERACLES09SURVEY; LEROY13SFGAS; LEROY22LINES; DENBROK21LINES; DENBROK23XCO; YAJIMA21LINES). All of this matches physical expectations and the sense of variations inferred for merging galaxies with similar or even more extreme conditions (cite: BOLATTO13REVIEW).

![image](paper_tdep_vs_tff_alphaco.png) ![image](paper_tdepnorm_vs_tff_alphaco.png)

## Correlation of $\epsilon_{\rm ff}^{\rm mol}$ with cloud-scale gas properties

| $x$ | Rank. corr. | $m$ | $x_0$ | $b$ | $\sigma$ |
|:--:|:--:|:--:|:--:|:--:|:--:|
| — | — | — | — | $-2.41$ | $0.29$ |
| $\log_{10} \left< \tau_{\rm ff}^{\rm cloud} \right>$ | $0.25$ | $0.46$ | $6.94$ | $-2.37$ | $0.28$ |
| (normalized) | $0.11$ | $0.13$ | — | — | $0.18$ |
| $\log_{10} \left< \Sigma_{\rm mol}^{\rm cloud} \right>$ | $-0.16$ | $-0.15$ | $1.58$ | $-2.37$ | $0.29$ |
| (normalized) | $-0.14$ | $-0.07$ | — | — | $0.18$ |
| $\log_{10} \left< \sigma_{\rm mol}^{\rm cloud} \right>$ | $0.01$ | $0.04$ | $0.74$ | $-2.38$ | $0.29$ |
| (normalized) | $0.01$ | $-0.01$ | — | — | $0.18$ |
| $\log_{10} \left< \alpha_{\rm vir}^{\rm cloud} \right>$ | $0.24$ | $0.21$ | $0.3$ | $-2.39$ | $0.28$ |
| (normalized) | $0.11$ | $0.04$ | — | — | $0.18$ |

: $\epsilon_{\rm ff}^{\rm mol}$ and cloud-scale gas properties

Table notes: Results correlating $\epsilon_{\rm ff}^{\rm mol}$ with cloud-scale gas properties for our fiducial sample of regions with high gas surface density. Cloud scale properties measured at 150 pc resolution, and our best estimate $\alpha_{\rm CO}$. Fit has form $y = m (x - x_0) + b$. Quantities defined in Table [1](#tab:experiment). Normalized results first normalize $\epsilon_{\rm ff}^{\rm mol}$ by the galaxy-average value.

![image](paper_eff_vs_sd.png) ![image](paper_eff_vs_vdisp.png)

![](paper_eff_vs_avir.png)

We plot our estimated $\epsilon_{\rm ff}^{\rm mol}$ as functions of cloud-scale gas properties in Figs. [11](#fig:eff_vs_gasprops) and [12](#fig:eff_vs_avir) and report results of our correlation analysis in Tab. [5](#tab:eff). (cite: PADOAN12EFF), (cite: FEDERRATH12EFF; FEDERRATH13EFF), (cite: BURKHART18EFF), and others all make predictions about how $\epsilon_{\rm ff}^{\rm mol}$ should depend on cloud-scale gas properties for star formation in turbulent gas clouds.

Figure [11](#fig:eff_vs_gasprops) and Tab. [5](#tab:eff) show almost no relationship between $\epsilon_{\rm ff}^{\rm mol}$ and either $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ or $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$, with rank correlation coefficients and slopes both showing very small values. Put in another way, within any reasonable level of uncertainty, a fixed $\epsilon_{\rm ff}^{\rm mol}$ with $\pm 0.3$ dex (Table [5](#tab:eff)) scatter appears to be a sufficient description of our present data set. As with the $\tau_{\rm dep}^{\rm mol}$ results, this statement depends on our treatment of $\alpha_{\rm CO}$ and data selection, but Fig. [11](#fig:eff_vs_gasprops) and Tab. [5](#tab:eff) represent our current best estimates. For reference, the median $\epsilon_{\rm ff}^{\rm mol}$ in Table [5](#tab:eff) corresponds to $0.39\%$ of gas formed into stars per free-fall time, and we measure $\pm 0.29$ dex or a factor of $2$ scatter across the sample. This agrees well with earlier work on PHANGS–ALMA by (cite: UTOMO18EFF) and (cite: SUN23SFGAS). Indeed, this is almost, though not exactly, the same measurement made in (cite: SUN23SFGAS).

The dependence of $\epsilon_{\rm ff}^{\rm mol}$ on $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ has been of interest in the theoretical works mentioned above. These works predict an anti-correlation, such that high $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ leads to low $\epsilon_{\rm ff}^{\rm mol}$. Fig. [12](#fig:eff_vs_avir) shows this relationship for our data set, with the curved dashed line indicating a simple expectation from (cite: PADOAN12EFF) for the case of fixed $\langle \tau_{\rm ff}^{\rm cloud} \rangle$. As with $\tau_{\rm dep}^{\rm mol}$ and $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ (Fig. [7](#fig:tdep_vs_avir)), we do not find the predicted theoretical relationship. The data instead appear consistent with a nearly fixed $\epsilon_{\rm ff}^{\rm mol}$ over a relatively wide range of $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, or perhaps even a mild positive correlation between $\epsilon_{\rm ff}^{\rm mol}$ and $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$. As discussed in §[3.3](#sec:tdepvsavir), [3.4](#sec:byrad), and §[4.5](#sec:avirdisc), this likely reflects that our measured $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, which only accounts for gas self-gravity, does not capture the true dynamical state of the gas because it neglects stellar gravity.

Finally, we note that though theoretically convenient, treating $\epsilon_{\rm ff}^{\rm mol}$ as the dependent variable can be problematic from an observational perspective. This leads to correlated axes, with cloud-scale density or a closely related quantity now entering both axes. And the requirement to detect gas at cloud scales to estimate $\tau_{\rm ff}^{\rm mol}$ (required to calculate $\epsilon_{\rm ff}^{\rm mol}$) means any completeness or surface density cuts will introduce selection effects that affect both the $x$ and $y$ axes, as opposed to mostly only affecting the $x$ axes when considering $\tau_{\rm dep}^{\rm mol}$. Given that the same physics will manifest in analyses comparing cloud-scale gas properties to $\tau_{\rm dep}^{\rm mol}$, which already suffer from moderately correlated axes, we recommend those measurements as a cleaner point of comparison.

These correlated axes, along with our fairly narrow dynamic range in cloud properties and selection, explain why the $\tau_{\rm dep}^{\rm mol}$ vs. gas property measurements in Table [3](#tab:tdep) do not trivially transform into the $\epsilon_{\rm ff}^{\rm mol}$ vs. gas property measurements in Table [5](#tab:eff). That is, we find almost flat $\ensuremath{\epsilon_{\rm ff}^{\rm mol}}$ vs. $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ but the slope of the $\ensuremath{\tau_{\rm dep}^{\rm mol}}{-}\ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}$ relation is shallower than the $m=0.5$ expected for fixed $\epsilon_{\rm ff}^{\rm mol}$ (and similar for $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$). Again, we recommend to focus on the cleanly reproducible $\tau_{\rm dep}^{\rm mol}$ results when comparing to our data (see Appendix [7](#sec:stepbystep)).

# Discussion

## What this measurement is

We present a correlation analysis relating cloud-scale gas properties to the molecular gas depletion time across PHANGS–ALMA. We apply a simple selection criteria and use a reproducible methodology that aggregates high-resolution gas properties using a mass-weighting scheme. This yields measurements that average over large enough areas, such that we expect to sample star-forming clouds in all evolutionary stages and access the time-averaged molecular gas depletion time. PHANGS–ALMA does a good job of sampling the massive end of the $z=0$ star-forming main sequence (cite: PHANGSALMA21SURVEY), so our measurements should represent a definitive view of region-by-region correlations between $\ensuremath{\tau_{\rm dep}^{\rm mol}}$ and cloud properties for the molecular gas-dominated regions of $z=0$ massive star-forming disk galaxies.

We highlight our measurements of $\tau_{\rm dep}^{\rm mol}$ as a function of $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$, as these are closest to the empirical data and also capture the key trends. While we provide power-law fits (Tables [3](#tab:tdep) and [5](#tab:eff)), we encourage direct comparisons to our full measurement set (Table [2](#tab:data) and Appendix [8](#sec:resn)) as a more robust approach.

These measurements should be easy to reproduce from observations of other samples of galaxies or numerical simulations. It seems useful to apply this method to numerical simulations that track the time evolution and resolve the small-scale structure of the ISM (cite: GRISDALE18; AGERTZ21SIMS; RENAUD21; JEFFRESON22GMCS; JEFFRESON23GMCS; KIM23TIGRESS). On the one hand, our measurements offer a chance to benchmark such simulations against real disk galaxies. On the other hand, the higher physical detail and access to the time dimension and three dimensional geometry in simulations allow for both a clearer physical interpretation of this type of measurement and the chance to test how different physical prescriptions (e.g., different true $\epsilon_{\rm ff}^{\rm mol}$, dependence on $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, dependence on other phases or processes like cloud collisions) would manifest (or not) in our measurements.

## What this measurement is not

We do not measure the initial conditions and final outcomes for individual clouds. Our cloud scale measurements are population averages. These aggregate high-resolution measurements from PHANGS–ALMA but do not distinguish between clouds at different evolutionary stages. Most turbulence-regulated theories of star formation consider how the initial properties of clouds affect the mass of gravitationally bound, collapsing gas (cite: KRUMHOLZ05EFF; PADOAN12EFF; FEDERRATH12EFF; FEDERRATH13EFF). Using high resolution simulations, (cite: KIM21FEEDBACKSIMS) highlight that feedback from star formation alters the properties of a clouds, including the $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$. Without accounting for the full cloud life cycle, one should not expect the turbulence-regulated models, or any other model focused on initial conditions, to apply rigorously to our measurements.

Indeed, (cite: SEGOVIAOTERO24) demonstrated, using cosmological simulations of galaxy formation, that the underlying “input” $\epsilon_{\rm ff}^{\rm mol}$ (in their work the (cite: PADOAN12EFF) star formation model was adopted) is challenging to infer observationally. They argued that a mix of cloud evolutionary stages (cite: GRISDALE19), as well as the time lag from the onset of star formation to the resulting tracers of star formation, can wash out correlations with parameters such as $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ (see their Figure 4).

Despite this caveat, we emphasize that our presented relationships, their normalization, and their levels of scatter, should still be viewed as benchmarks that numerical simulations should be able to reproduce when our simple methodology is adopted. More, studies of the distribution functions of cloud-scale gas properties in PHANGS, including the gas column distribution function (cite: PATHAK24MIDIR) and beam-by-beam surface density and velocity dispersion measurements (cite: SUN18CLOUDS; SUN20GMCS) find relatively narrow (rms $\sim 0.3{-}0.4$ dex), often lognormal distributions of gas properties in each region. Systematic variations in the mean of these distributions appear mostly correlated with large-scale environment in coherent ways (cite: SUN22CLOUDS). Given this, we expect that region-to-region variations in the mean cloud-scale gas properties do map fairly directly to variations in the initial conditions for star formation. The impact of feedback seems more likely to represent a correction factor than to completely scramble our results. This would be an excellent topic to investigate further with simulations.

## Surface density, physical density, and resolution

![](paper_sd_vs_resn.png)

|                       |             |                        |         |
|:---------------------:|:-----------:|:----------------------:|:-------:|
|      Comparison       | Rank. corr. | Med. $\log_{10}$ Ratio | Scatter |
| (vs. $\ell = 150$ pc) |             |         (dex)          |  (dex)  |
|    $\ell = 120$ pc    |   $0.998$   |        $0.031$         | $0.016$ |
|    $\ell = 90$ pc     |   $0.99$    |        $0.069$         | $0.029$ |
|    $\ell = 60$ pc     |   $0.97$    |         $0.13$         | $0.050$ |

: $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ and Resolution

Table notes: Correlation between $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ measured at our fiducial scale, $\ell = 150$ pc resolution (treated as the $x$ variable), and measurements using higher resolution CO (2-1) data (treated as the $y$ variable) for regions that meet our selection criteria (Fig. [2](#fig:completeness)) Columns report: the nonparameteric rank correlation coefficient between $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ at the two scales; the median $\log_{10} y/x$ ratio, which captures the amount of beam dilution present; and the scatter in the $\log_{10}$ ratio. See also Fig. [13](#fig:sdresn).

We consider $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ an observational indicator of the gas volume density and use it to estimate $\langle \tau_{\rm ff}^{\rm cloud} \rangle$. For a weakly varying molecular gas scale height (cite: HEYER15REVIEW), $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ measures the mean density within the beam. It could be possible that this mean density estimated at 150 pc scales does not indicate the physical density within clouds or the density measured at smaller scales. For example, this could be the case if the molecular ISM consists of otherwise identical small clouds that vary in space density across galaxies (cite: BLITZ07GMCS; FUKUI10REVIEW).

Though our common resolution is $150$ pc, PHANGS–ALMA also represents the largest $120$, $90$, and $60$ pc resolution survey of CO emission from nearby galaxies. In Appendix [8](#sec:resn), we repeat the analysis comparing $\tau_{\rm dep}^{\rm mol}$ to $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ at each of these higher resolutions. Though the numbers of galaxies covered are smaller for these sharper resolutions, they show trends that are consistent with those we observe at 150 pc resolution data (Appendix [8](#sec:resn)).

Figure [13](#fig:sdresn) and Table [6](#tab:sdresn) directly compare $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ measured at different resolutions in our target regions. The figure shows that the physical resolution has a mild effect on the mass-weighted surface densities, with slightly higher $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ at higher resolution. This indicates some beam dilution or clumping, which is expected. Beyond the ratio, $\ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}$ at $150$ pc correlates stunningly well with $\ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}$ at $120$ pc, $90$ pc, and even $60$ pc resolution. Although many millimeter astronomers hold strongly-felt opinions about the true size of a molecular cloud, as far as we are aware there is no clear evidence for a specific scale where the surface density traces physical density. Instead, our $\ell = 150$ pc data provide an outstanding predictor of the $\ell = 60$ pc $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ despite $6\times$ difference in beam area. This is in good agreement with previous work examinging the scale dependence of $\Sigma_{\rm mol}$ by (cite: LEROY16GMCS), (cite: SUN18CLOUDS), and (cite: SUN20GMCS).

An important line of evidence reinforcing this view comes from mm-wave spectroscopic tracers of physical density. (cite: GALLAGHER18HCNCLOUD), (cite: NEUMANN23DENSE), and (cite: GARCIARODRIGUEZ23DENSE) showed that the HCN/CO ratio measured at $\sim$ kpc scales correlates with $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ (cite: TAFALLA23LINES). Though the precise density of gas traced by HCN emission is debated, the HCN/CO ratio should be sensitive to physical density (cite: KRUMHOLZ07DENSE; LEROY17DENSE), and represents one of the most accessible density-sensitive mm-wave line ratios. Reinforcing this view, (cite: JIMENEZ23DENSE) and (cite: STUBER23DENSE) both show that HCN/CO correlates well with the N$_2$H$^+$/CO line ratio, which is widely considered a gold standard tracer of the dense gas fraction in Milky Way studies. We refer the reader to (cite: SCHINNERER24REVIEW) for more discussion.

Together, the consistency of $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$-based results across scale and the link between spectroscopic and imaging-based tracers of density give us confidence that $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ does trace the physical gas density distribution in the beam. The fidelity of the tracer and the correct sub-beam geometry to assume certainly need more study, and these represent important areas for follow up work at higher resolution and simulation-based tests.

![image](paper_sfscaling_bysdmol.png) ![image](paper_sfscaling_byvdisp.png)

We also re-emphasize the point made in §[3.4](#sec:byrad). As demonstrated in (cite: SUN22CLOUDS), the cloud-scale gas properties vary in a regular way as a function of $\Sigma_{\rm mol}^{\rm kpc}$, $\Sigma_{\rm SFR}^{\rm kpc}$, the rotation curve and more. Here we observe relationships between $\tau_{\rm dep}^{\rm mol}$, $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$, and $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, which all then correlate with one another and with these larger-scale conditions. Purely from a data perspective, there is high covariance between these and many other relevant quantities (stellar surface density, the dynamical equilibrium pressure, etc.). $\tau_{\rm dep}^{\rm mol}$ *should* depend on the small scale gas properties, so we expect that the causal relationship likely flows (at least partially) from small to large scales. But a host of hidden variables lurk behind all of these plots.

This also means that as $\Sigma_{\rm mol}^{\rm kpc}$, galactocentric radius, or even global galaxy properties vary, these cloud-scale gas properties will also vary. To illustrate this in a parameter space of broad interest, Fig. [14](#fig:turtles) shows the $\Sigma_{\rm SFR}^{\rm mol}{-}\Sigma_{\rm mol}^{\rm kpc}$ molecular Kennicutt-Schmidt relation for our target regions (as Fig. [3](#fig:scaling)) but now coloring by the cloud-scale gas properties. These vary in regular ways across this space, particularly as a function of $\Sigma_{\rm mol}^{\rm kpc}$.

## The $\tau_{\rm dep}^{\rm mol}$–$\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ anti-correlation

![](paper_tdep_vs_sd_resid.png)

The anti-correlation between $\tau_{\rm dep}^{\rm mol}$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ mirrors the one relating $\tau_{\rm dep}^{\rm mol}$ to $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$. As discussed in §[3.2](#sec:tdepvsprops), this anti-correlation would be expected if (1) there is an underlying anti-correlation between density and $\tau_{\rm dep}^{\rm mol}$ and (2) clouds show approximately fixed dynamical state. In that case, the line width reflects the potential and so the density of the molecular gas. Then the $\tau_{\rm dep}^{\rm mol}$–$\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ and $\tau_{\rm dep}^{\rm mol}$–$\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ relations are manifestations of the same underlying physical correlation. To test this view, Fig. [15](#fig:vdispresid) shows the residual $\tau_{\rm dep}^{\rm mol}$ model as a function of $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ after subtracting our best-fit $\tau_{\rm dep}^{\rm mol}$–$\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ relation (Table [3](#tab:tdep)). Except at the very highest $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, most of the $\tau_{\rm dep}^{\rm mol}$–$\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ trend is removed by subtracting the $\tau_{\rm dep}^{\rm mol}$–$\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ trend.

This $\tau_{\rm dep}^{\rm mol}$–$\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ relation is worth more investigation. $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ has only a weak dependence on $\alpha_{\rm CO}$ (via the weighted average) and may depend less sensitively on resolution than $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$. The line width measurement certainly has its own complexities, however. As shown by J. Henshaw et al. (in preparation) studying PHANGS–ALMA, the inner parts of galaxies, which show low $\tau_{\rm dep}^{\rm mol}$ also tend to show complex spectral profiles. Our line width measure (effective width) is sensitive to the integrated width of all components, and it will be interesting to explore whether other methods (e.g., second moment, gaussian model fit) show more or less anti-correlation with $\tau_{\rm dep}^{\rm mol}$. Extending the analysis to well-resolved interacting galaxies, which also tend to show significant spectral complexity (cite: BRUNETTI21GMCS; BRUNETTI24GMCS) will provide another interesting counterpoint. Because the gas velocity dispersion may be sensitive to physical conditions even in small, unresolved clouds, this also might offer an interesting direction to study the fainter, smaller clouds in outer galaxy disks.

We have emphasized that the $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ should trace the gravitational potential and produce the sort of anti-correlation that we see, but the velocity dispersion is often physically interpreted in other ways that may be related to star formation. In the context of turbulence-regulated star formation, the velocity dispersion is often related to the Mach number, which plays an important role in setting the density distribution (cite: PADOAN02TURB; KRUMHOLZ05EFF; FEDERRATH12EFF; FEDERRATH13EFF). A variety of bulk motions that should influence the line width have also been invoked to explain enhanced or suppressed star formation efficiencies. These include suppression by streaming motions along spiral arms or bars (cite: MEIDT13SFGAS), star formation induced by cloud collisions (cite: FUKUI21COLLIDE), and star formation induced by spiral shocks (cite: QUEREJETA24SFGAS).

Perhaps most importantly, (cite: TENG24XCO) show that the observed CO line width also anti-correlates with $\alpha_{\rm CO}$. They use the (cite: CHIANG24XCO) $\alpha_{\rm CO}$ estimates, which also underpin the emissivity term in the $\alpha_{\rm CO}$ prescription that we use here. (cite: TENG24XCO) argue that the line width serves as a proxy for the inverse of the opacity, and that opacity variations drive a large fraction of the $\alpha_{\rm CO}$ emissivity variations. This agrees well with the spectral line modeling of (cite: TENG22XCO) and (cite: TENG23XCO; DENBROK24XCO). Since the $\tau_{\rm dep}^{\rm mol}$ variations that we observe depend on our adopted $\alpha_{\rm CO}$ (§[3.5](#sec:alphaco), Fig. [10](#fig:tdep_alphaco)), our measured $\ensuremath{\tau_{\rm dep}^{\rm mol}}{-}\ensuremath{\langle \sigma_{\rm mol}^{\rm cloud} \rangle}$ correlation is formally related to the $\alpha_{\rm CO}{-}\ensuremath{\langle \sigma_{\rm mol}^{\rm cloud} \rangle}$ correlation of (cite: TENG24XCO). It is entirely possible that the line width both traces the gas density (or another physical parameter related to the depletion) *and* drives variations in $\alpha_{\rm CO}$. But at a minimum, the results of (cite: TENG24XCO) are important to bear in mind because they imply a hidden correlation between the $\tau_{\rm dep}^{\rm mol}$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ axes.

## The lack of a $\tau_{\rm dep}^{\rm mol}$–$\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ correlation

Our results disfavor the interpretation that $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, considering only self-gravity and measured at $60{-}150$ pc scales, indicates the amount of self-gravitating, likely star-forming gas. Instead, the regions that show low $\tau_{\rm dep}^{\rm mol}$ also show high $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ and tend to occur in the inner parts of galaxies. This agrees with recent results arguing that the broader galactic potential, including significant contribution from stellar gravity, can contribute to the dynamical state of molecular clouds (cite: MEIDT18GMCS; LIU21GMCS).

In numerical modeling, (cite: SEMENOV17GMCS; SEMENOV18GMCS; SEMENOV21GMCS) find that accounting for the dynamical state of individual parcels of gas is key to reproduce observed $\tau_{\rm dep}^{\rm mol}$ and the decorrelation observed between CO and H$\alpha$ at high resolution. (cite: EVANS21GMCS) makes a similar argument for Milky Way clouds. It is tempting to ask whether $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ can be salvaged by a more sophisticated formulation that includes information, e.g., on the stellar distribution, rotation curve, or other gas phases. (cite: LIU21GMCS) argue that modeling the large-scale potential, combined with high ($\lesssim 10$ pc) resolution CO imaging may offer a chance to assess the dynamical state on scales that better access the presence of self-gravitating gas. Similarly, (cite: MEIDT18GMCS) argue that extragalactic velocity dispersion measurements can be explained by models that includes the full galactic potential. (cite: SCHRUBA19GMCS) make a similar argument. This may offer a way forward, but lies beyond the scope of this work.

We also note that the $\ensuremath{\tau_{\rm dep}^{\rm mol}}{-}\ensuremath{\langle \alpha_{\rm vir}^{\rm cloud} \rangle}$ trend almost disappears when the $\ensuremath{\tau_{\rm dep}^{\rm mol}}{-}\ensuremath{\langle \sigma_{\rm mol}^{\rm cloud} \rangle}$ or $\ensuremath{\tau_{\rm dep}^{\rm mol}}{-}\ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}$ trends are subtracted from the data, similar to Fig. [15](#fig:vdispresid). Given this, an explanation or simulation that matches the other two observed trends will likely capture the impact of dynamical state.

## Next steps

As we emphasize above, we consider comparison to numerical simulation a critical next step. PHANGS–ALMA has now measured cloud-scale gas properties across the local galaxy population and found regular patterns and links to $\tau_{\rm dep}^{\rm mol}$. We have adopted a deliberately simple methodology and tracked completeness, resolution, and other elements needed to make a fair comparison. An ideal next step will be to see how well numerical simulations match the basic distributions in (cite: SUN18CLOUDS; SUN20GMCS) (cite: PATHAK24MIDIR), the correlations with environment in (cite: SUN22CLOUDS), and the link to $\tau_{\rm dep}^{\rm mol}$ seen here. (cite: DOBBS19GMCS) shows promising results in this direction, finding excellent match between the cloud-scale gas properties measured their dwarf spiral simulation and observations of M33 in (cite: SUN18CLOUDS). We are eager to see future works comparing more simulations with more representative observational results.

From an observational perspective, ALMA is capable of pushing similar analysis down to $\lesssim 10$ pc resolution over whole galaxies, but this will require a significant commitment. Still, this seems like the qualitative leap in resolution needed to address any ambiguity in the interpretation of $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ and $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$. Fig. [13](#fig:sdresn) and Appendix [8](#sec:resn) suggest that simply increasing the resolution to $\ell \approx 60$ pc is unlikely to yield qualitatively different results. Meanwhile, improving the star formation rate tracer also represents an important next step. We use the best available option for all of PHANGs–ALMA, which is a combination of H$\alpha$ and mid-IR data following (cite: BELFIORE23SFRLARGE). But this limits the scales over which we can measure $\tau_{\rm dep}^{\rm mol}$ and still does not match the quality of an IFU-based H$\alpha$+H$\beta$ estimate (cite: BELFIORE23SFRLARGE). Coverage of the full sample, e.g., by VLT/MUSE would reduce a lingering source of uncertainty and allow us to average the data in much finer ways, e.g., by constructing averages along likely gas flow lines (cite: MEIDT15SFGAS; KODA21SFGAS) in more sharply defined distinct dynamical environments (cite: QUEREJETA21; QUEREJETA24SFGAS), and so on. They would also allow us to examine statistical distributions of matched resolution SFR and gas tracers rather than relying on region averages for $\tau_{\rm dep}^{\rm mol}$.

Finally, improved knowledge of $\alpha_{\rm CO}$ remains the single largest uncertainty. The field has made excellent observational and theoretical progress in this area, improving PDR models, building simulations with realistic chemistry and radiative transfer, and constraining line ratio variations, opacity, and expanding estimates based on independent gas tracers like dust. But the uncertainty on $\alpha_{\rm CO}$ in any given environment still dominates the error budget for this entire field.

# Summary

Using PHANGS–ALMA, we have measured how the molecular gas depletion time, $\ensuremath{\tau_{\rm dep}^{\rm mol}}$, and the star formation efficiency per free-fall time, $\ensuremath{\epsilon_{\rm ff}^{\rm mol}}$, correlate with cloud-scale gas properties. Following (cite: SUN22CLOUDS), we break galaxies into $1.5$ kpc diameter hexagonal regions, calculate the region-mean $\tau_{\rm dep}^{\rm mol}$ and $\epsilon_{\rm ff}^{\rm mol}$, and compare these to the mass-weighted mean molecular gas surface density ($\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$), velocity dispersion ($\langle \sigma_{\rm mol}^{\rm cloud} \rangle$), gravitational free-fall time ($\langle \tau_{\rm ff}^{\rm cloud} \rangle$), and virial parameter ($\langle \alpha_{\rm vir}^{\rm cloud} \rangle$; see Tab. [1](#tab:experiment)). We measure $150$ pc cloud-scale gas properties, $\tau_{\rm dep}^{\rm mol}$ and $\epsilon_{\rm ff}^{\rm mol}$ for $841$ independent regions in $67$ galaxies. In Appendix [8](#sec:resn) we also construct higher resolution data sets where we measure the gas properties at $120$, $90$, and $60$ pc resolution. We find substantially similar results varying the resolution, and emphasize that spectroscopic result also indicate that the 150 pc surface density tracks physical density variations across galaxies (§[4.3](#sec:densdisc)).

In constructing these measurements, the completeness of the CO data entering the gas property analysis represents an important consideration. We work only with regions where $> 50\%$ of the CO flux is captured by the high-resolution CO map. For PHANGS–ALMA this corresponds approximately to regions with $\ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}> 20$ M$_\odot$ pc$^{-2}$ (Fig. [2](#fig:completeness)). This selection yields a set of regions that show good dynamic range in large-scale $\Sigma_{\rm mol}^{\rm kpc}$, $\Sigma_{\rm SFR}^{\rm kpc}$, and cloud-scale gas properties (Fig. [3](#fig:scaling)). As expected, these regions obey the same large-scale $\Sigma_{\rm SFR}{-}\Sigma_{\rm mol}$ (molecular “Kennicutt-Schmidt”) and cloud-scale $\ensuremath{\langle \sigma_{\rm mol}^{\rm cloud} \rangle}{-}\ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}$ (“Heyer-Keto”) scalings measured for the overall PHANGS–ALMA data set (cite: SUN20GMCS; SUN22CLOUDS; SUN23SFGAS).

Analyzing these data, we reach the following main conclusions:

1.  We observe a positive correlation between $\tau_{\rm dep}^{\rm mol}$ and $\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$ (§[3.1](#sec:tdepvstff), Fig. [4](#fig:tdepvstff), Tab. [3](#tab:tdep)) as expected if density plays an important role in setting the rate at which gas forms stars. This correlation appears stronger after accounting for galaxy-to-galaxy variations in $\tau_{\rm dep}^{\rm mol}$ (Figs. [4](#fig:tdepvstff) and [5](#fig:tdepbygal)). Our best fit line is shallower than the $\ensuremath{\tau_{\rm dep}^{\rm mol}}\propto \ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$ relation expected for a fixed efficiency per free fall time, though we emphasize that the fit parameters depend on the adopted methodology. Though $\epsilon_{\rm ff}^{\rm mol}$ has been estimated for PHANGS–ALMA before (cite: UTOMO18EFF; SUN22CLOUDS; SUN23SFGAS; SCHINNERER24REVIEW), this result represents the most direct evidence for an actual correlation between $\langle \tau_{\rm ff}^{\rm cloud} \rangle$ and $\tau_{\rm dep}^{\rm mol}$ in our data set.

2.  We also observe significant anti-correlations between $\tau_{\rm dep}^{\rm mol}$ and $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ and between $\tau_{\rm dep}^{\rm mol}$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ (Fig. [6](#fig:tdep_vs_gasprops), Tab. [3](#tab:tdep)). Because $\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}\propto \langle \left(\Sigma_{\rm mol}^{\rm cloud}\right)^{-0.5} \rangle$ and $\ensuremath{\langle \sigma_{\rm mol}^{\rm cloud} \rangle}\propto \ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}^{0.5}$ for clouds with fixed dynamical state (as per Fig. [3](#fig:scaling)), correlations with this sense could all be expected from a single underlying dependence of $\tau_{\rm dep}^{\rm mol}$ on gas volume density. As with $\tau_{\rm dep}^{\rm mol}$ and $\langle \tau_{\rm ff}^{\rm cloud} \rangle$, the best-fit slopes that we find show shallower slopes than expected for $\ensuremath{\tau_{\rm dep}^{\rm mol}}\propto \ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}$ and self-gravitating gas. We consider these measurements more empirically robust and the best points for direct comparisons with other observations or simulations.

3.  The anti-correlation between $\tau_{\rm dep}^{\rm mol}$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ (Fig. [11](#fig:eff_vs_gasprops), Tab. [3](#tab:tdep), §[3.2](#sec:tdepvsprops), [4.4](#sec:vdispdisc)) appears interesting because the $x$-axis does not rely on $\alpha_{\rm CO}$ for the measurement of the cloud-scale gas properties and may be less sensitive to resolution than $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$. This may remove some of the built-in correlation present in other scaling relations. We emphasize that this anti-correlation between $\tau_{\rm dep}^{\rm mol}$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ will emerge from clouds with relatively uniform dynamical state with fixed $\epsilon_{\rm ff}^{\rm mol}$ regardless of any details related to interstellar turbulence. An important complication is that $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ may also have a significant impact on $\alpha_{\rm CO}$ (cite: TENG24XCO), which also affects $\tau_{\rm dep}^{\rm mol}$.

4.  We also observe an anti-correlation between $\tau_{\rm dep}^{\rm mol}$ and $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, and the latter should capture the balance of kinetic and self-gravitational potential energy for the gas (Fig. [7](#fig:tdep_vs_avir), Tab. [6](#fig:tdep_vs_gasprops)). In our measurements, gas that appears less bound by self-gravity forms stars more efficiently, which does not match naive physical expectations. Practically, this reflects that regions with high mean $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ often occur in the inner parts of galaxies, where a diffuse, bright molecular medium bound partially by stellar gravity appears common. These regions also appear efficient at forming stars. Both results have significant support from previous studies.

5.  Our results depend significantly on the adopted treatment of the CO-to-H$_2$ conversion factor, $\alpha_{\rm CO}$ (Fig. [10](#fig:tdep_alphaco), Tab. [4](#tab:fixaco), §[3.5](#sec:alphaco)). Specifically, the inclusion or omission of a term that accounts for enhanced CO emissivity and excitation in the inner, high surface density parts of galaxies has a large effect on our measurements. When such a term is included, the correlations between $\tau_{\rm dep}^{\rm mol}$, $\langle \tau_{\rm ff}^{\rm cloud} \rangle$, $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ discussed above become apparent. When omitting the term, we measure correlations with almost the opposite sense. Including this term represents our best estimate, as these corrections appear necessary based on extensive observational and theoretical work. Despite this previous good work, precise knowledge of $\alpha_{\rm CO}$ almost certainly remains the main obstacle to progress in this field.

6.  Recasting our results to consider $\epsilon_{\rm ff}^{\rm mol}$ as a function of cloud-scale gas properties, we see almost no correlation between $\epsilon_{\rm ff}^{\rm mol}$ and $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ or $\epsilon_{\rm ff}^{\rm mol}$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ (Fig. [11](#fig:eff_vs_gasprops), Tab. [5](#tab:eff)). Meanwhile, the appear consistent with a nearly fixed $\epsilon_{\rm ff}^{\rm mol}$over a relatively wide range of $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, or perhaps even a mild positive correlation between $\epsilon_{\rm ff}^{\rm mol}$and $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, in contrast to the theoretically expected anti-correlation for a turbulent cloud of pure gas. Given that these relations induce correlated axes without adding significant information, we suggest to view the measurements comparing $\tau_{\rm dep}^{\rm mol}$ to cloud-scale gas properties as more empirically grounded point of comparison.

7.  We present quantitative measurements for each region that should be easy to compare to simulations or other samples of galaxies with matched methodology (Table [2](#tab:data)). We implore the community conducting detailed physical simulations of galaxies to attempt such measurements. Applying these methods to cases with well-understood geometry and prescriptions for star formation and stellar feedback represents an important step that will allow us to chart next directions for the field. Appendix [7](#sec:stepbystep) suggests a simple procedure to construct such comparisons.

These results largely agree with those seen in work on individual galaxies or small samples by (cite: LEROY17SFGAS), (cite: SCHRUBA19GMCS), and (cite: QUEREJETA23SFGAS), but employing a much larger sample.

Finally, a general conclusion from our analysis is that the links between cloud-scale gas properties and $\ensuremath{\tau_{\rm dep}^{\rm mol}}$ fit naturally into the broader picture expected from simple scaling relations and our knowledge of galaxy structure (Fig. [9](#fig:tdepbyrad), [14](#fig:turtles), Appendix [8](#sec:resn)). After accounting for $\alpha_{\rm CO}$ variations, $\ensuremath{\tau_{\rm dep}^{\rm mol}}$ tends to be shorter in high surface density inner regions of galaxies (cite: LEROY13SFGAS; TENG24XCO; SUN23SFGAS). The cloud-scale $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ and $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$ also all tend to be higher in these regions, with $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ generally correlating with one another (cite: SUN18CLOUDS; SUN20GMCS; ROSOLOWSKY21GMCS) and the large-scale surface density in the galaxy disk (cite: SUN20PRESS; SUN22CLOUDS). We thus observe a set of predictable, self-consistent relationships among $\tau_{\rm dep}^{\rm mol}$, $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$, and $\langle \tau_{\rm ff}^{\rm cloud} \rangle$.

# Acknowledgments

We thank Neal Evans and Davide Elia for pointing out inconsistencies between the data and plots that led to correcting a significant mistake in the manuscript. We thank the anonymous referee for a constructive, timely report.

This work was carried out as part of the PHANGS collaboration.

A.K.L., S.S., and R.C. gratefully acknowledge support from NSF AST AWD 2205628, JWST-GO-02107.009-A, and JWST-GO-03707.001-A. A.K.L. also gratefully acknowledges support by a Humboldt Research Award.

J.S. acknowledges support by the National Aeronautics and Space Administration (NASA) through the NASA Hubble Fellowship grant HST-HF2-51544 awarded by the Space Telescope Science Institute (STScI), which is operated by the Association of Universities for Research in Astronomy, Inc., under contract NAS 5-26555.

M.C. gratefully acknowledges funding from the DFG through an Emmy Noether Research Group (grant number CH2137/1-1). COOL Research DAO is a Decentralized Autonomous Organization supporting research in astrophysics aimed at uncovering our cosmic origins.

JG gratefully acknowledges funding via STFC grant ST/Y001133/1 and financial support from the Swiss National Science Foundation (grant no CRSII5_193826).

HAP acknowledges support from the National Science and Technology Council of Taiwan under grant 110-2112-M-032-020-MY3.

SCOG acknowledges support from the European Research Council via the ERC Synergy Grant “ECOGAL” (project ID 855130) and from the German Excellence Strategy via the Heidelberg Cluster of Excellence (EXC 2181 - 390900948) “STRUCTURES”.

OA acknowledges support from the Knut and Alice Wallenberg Foundation, the Swedish Research Council (grant 2019-04659), and the Swedish National Space Agency (SNSA Dnr 2023-00164).

This paper makes use of the following ALMA data, which have been processed as part of the PHANGS–ALMA CO (2-1) survey:\
ADS/JAO.ALMA#2012.1.00650.S,\
ADS/JAO.ALMA#2013.1.00803.S,\
ADS/JAO.ALMA#2013.1.01161.S,\
ADS/JAO.ALMA#2015.1.00121.S,\
ADS/JAO.ALMA#2015.1.00782.S,\
ADS/JAO.ALMA#2015.1.00925.S,\
ADS/JAO.ALMA#2015.1.00956.S,\
ADS/JAO.ALMA#2016.1.00386.S,\
ADS/JAO.ALMA#2017.1.00392.S,\
ADS/JAO.ALMA#2017.1.00766.S,\
ADS/JAO.ALMA#2017.1.00886.L,\
ADS/JAO.ALMA#2018.1.01321.S,\
ADS/JAO.ALMA#2018.1.01651.S,\
ADS/JAO.ALMA#2018.A.00062.S,\
ADS/JAO.ALMA#2019.1.01235.S,\
ADS/JAO.ALMA#2019.2.00129.S,\
ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

natexlab

(ref: ACCURSO17XCO) Accurso, G., Saintonge, A., Catinella, B., et al. 2017, MNRAS, 470, 4750, doi: [`10.1093/mnras/stx1556`](http://doi.org/10.1093/mnras/stx1556)

(ref: AGERTZ21SIMS) Agertz, O., Renaud, F., Feltzing, S., et al. 2021, MNRAS, 503, 5826, doi: [`10.1093/mnras/stab322`](http://doi.org/10.1093/mnras/stab322)

(ref: ANAND21DISTANCES) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2021, MNRAS, 501, 3621, doi: [`10.1093/mnras/staa3668`](http://doi.org/10.1093/mnras/staa3668)

(ref: BALLESTEROS06GMCS) Ballesteros-Paredes, J. 2006, MNRAS, 372, 443, doi: [`10.1111/j.1365-2966.2006.10880.x`](http://doi.org/10.1111/j.1365-2966.2006.10880.x)

(ref: BELFIORE18RPROF) Belfiore, F., Maiolino, R., Bundy, K., et al. 2018, MNRAS, 477, 3014, doi: [`10.1093/mnras/sty768`](http://doi.org/10.1093/mnras/sty768)

(ref: BELFIORE23SFRLARGE) Belfiore, F., Leroy, A. K., Sun, J., et al. 2023, A&A, 670, A67, doi: [`10.1051/0004-6361/202244863`](http://doi.org/10.1051/0004-6361/202244863)

(ref: BERTOLDI92GMCS) Bertoldi, F., & McKee, C. F. 1992, ApJ, 395, 140, doi: [`10.1086/171638`](http://doi.org/10.1086/171638)

(ref: BIGIEL08SFGAS) Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846, doi: [`10.1088/0004-6256/136/6/2846`](http://doi.org/10.1088/0004-6256/136/6/2846)

(ref: BLITZ07GMCS) Blitz, L., Fukui, Y., Kawamura, A., et al. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 81, doi: [`10.48550/arXiv.astro-ph/0602600`](http://doi.org/10.48550/arXiv.astro-ph/0602600)

(ref: BLITZ06PRESS) Blitz, L., & Rosolowsky, E. 2006, ApJ, 650, 933, doi: [`10.1086/505417`](http://doi.org/10.1086/505417)

(ref: BOLATTO13REVIEW) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: BRUNETTI21GMCS) Brunetti, N., Wilson, C. D., Sliwa, K., et al. 2021, MNRAS, 500, 4730, doi: [`10.1093/mnras/staa3425`](http://doi.org/10.1093/mnras/staa3425)

(ref: BRUNETTI24GMCS) Brunetti, N., Wilson, C. D., He, H., et al. 2024, MNRAS, 530, 597, doi: [`10.1093/mnras/stae890`](http://doi.org/10.1093/mnras/stae890)

(ref: BURKHART18EFF) Burkhart, B. 2018, ApJ, 863, 118, doi: [`10.3847/1538-4357/aad002`](http://doi.org/10.3847/1538-4357/aad002)

(ref: CHEVANCE20TIMES) Chevance, M., Kruijssen, J. M. D., Hygate, A. P. S., et al. 2020, MNRAS, 493, 2872, doi: [`10.1093/mnras/stz3525`](http://doi.org/10.1093/mnras/stz3525)

(ref: CHIANG24XCO) Chiang, I.-D., Sandstrom, K. M., Chastenet, J., et al. 2024, ApJ, 964, 18, doi: [`10.3847/1538-4357/ad23ed`](http://doi.org/10.3847/1538-4357/ad23ed)

(ref: davis2014) Davis, T. A., Young, L. M., Crocker, A. F., et al. 2014, MNRAS, 444, 3427, doi: [`10.1093/mnras/stu570`](http://doi.org/10.1093/mnras/stu570)

(ref: DAVIS22GMCS) Davis, T. A., Gensior, J., Bureau, M., et al. 2022, MNRAS, 512, 1522, doi: [`10.1093/mnras/stac600`](http://doi.org/10.1093/mnras/stac600)

(ref: DENBROK24XCO) den Brok, J., Jiménez-Donaire, M. J., Leroy, A., et al. 2024, arXiv e-prints, arXiv:2410.21399, doi: [`10.48550/arXiv.2410.21399`](http://doi.org/10.48550/arXiv.2410.21399)

(ref: DENBROK21LINES) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS, 504, 3221, doi: [`10.1093/mnras/stab859`](http://doi.org/10.1093/mnras/stab859)

(ref: DENBROK23XCO) den Brok, J. S., Bigiel, F., Chastenet, J., et al. 2023, A&A, 676, A93, doi: [`10.1051/0004-6361/202245718`](http://doi.org/10.1051/0004-6361/202245718)

(ref: DOBBS19GMCS) Dobbs, C. L., Rosolowsky, E., Pettitt, A. R., et al. 2019, MNRAS, 485, 4997, doi: [`10.1093/mnras/stz674`](http://doi.org/10.1093/mnras/stz674)

(ref: EIBENSTEINER2024RMOL) Eibensteiner, C., Sun, J., Bigiel, F., et al. 2024, arXiv e-prints, arXiv:2407.01716, doi: [`10.48550/arXiv.2407.01716`](http://doi.org/10.48550/arXiv.2407.01716)

(ref: ELLISON18RPROF) Ellison, S. L., Sánchez, S. F., Ibarra-Medel, H., et al. 2018, MNRAS, 474, 2039, doi: [`10.1093/mnras/stx2882`](http://doi.org/10.1093/mnras/stx2882)

(ref: EVANS14DENSE) Evans, Neal J., I., Heiderman, A., & Vutisalchavakul, N. 2014, ApJ, 782, 114, doi: [`10.1088/0004-637X/782/2/114`](http://doi.org/10.1088/0004-637X/782/2/114)

(ref: EVANS21GMCS) Evans, Neal J., I., Heyer, M., Miville-Deschênes, M.-A., Nguyen-Luong, Q., & Merello, M. 2021, ApJ, 920, 126, doi: [`10.3847/1538-4357/ac1425`](http://doi.org/10.3847/1538-4357/ac1425)

(ref: FEDERRATH12EFF) Federrath, C., & Klessen, R. S. 2012, ApJ, 761, 156, doi: [`10.1088/0004-637X/761/2/156`](http://doi.org/10.1088/0004-637X/761/2/156)

(ref: FEDERRATH13EFF) —. 2013, ApJ, 763, 51, doi: [`10.1088/0004-637X/763/1/51`](http://doi.org/10.1088/0004-637X/763/1/51)

(ref: FIELD11GMCS) Field, G. B., Blackman, E. G., & Keto, E. R. 2011, MNRAS, 416, 710, doi: [`10.1111/j.1365-2966.2011.19091.x`](http://doi.org/10.1111/j.1365-2966.2011.19091.x)

(ref: FUKUI21COLLIDE) Fukui, Y., Habe, A., Inoue, T., Enokiya, R., & Tachihara, K. 2021, PASJ, 73, S1, doi: [`10.1093/pasj/psaa103`](http://doi.org/10.1093/pasj/psaa103)

(ref: FUKUI10REVIEW) Fukui, Y., & Kawamura, A. 2010, ARA&A, 48, 547, doi: [`10.1146/annurev-astro-081309-130854`](http://doi.org/10.1146/annurev-astro-081309-130854)

(ref: GALLAGHER18HCNCLOUD) Gallagher, M. J., Leroy, A. K., Bigiel, F., et al. 2018, ApJL, 868, L38, doi: [`10.3847/2041-8213/aaf16a`](http://doi.org/10.3847/2041-8213/aaf16a)

(ref: GAO04DENSE) Gao, Y., & Solomon, P. M. 2004, ApJ, 606, 271, doi: [`10.1086/382999`](http://doi.org/10.1086/382999)

(ref: GARCIABURILLO12DENSE) Garcı́a-Burillo, S., Usero, A., Alonso-Herrero, A., et al. 2012, A&A, 539, A8, doi: [`10.1051/0004-6361/201117838`](http://doi.org/10.1051/0004-6361/201117838)

(ref: GARCIARODRIGUEZ23DENSE) Garcı́a-Rodrı́guez, A., Usero, A., Leroy, A. K., et al. 2023, A&A, 672, A96, doi: [`10.1051/0004-6361/202244317`](http://doi.org/10.1051/0004-6361/202244317)

(ref: GONG20XCO) Gong, M., Ostriker, E. C., Kim, C.-G., & Kim, J.-G. 2020, ApJ, 903, 142, doi: [`10.3847/1538-4357/abbdab`](http://doi.org/10.3847/1538-4357/abbdab)

(ref: GRISDALE18) Grisdale, K., Agertz, O., Renaud, F., & Romeo, A. B. 2018, MNRAS, 479, 3167, doi: [`10.1093/mnras/sty1595`](http://doi.org/10.1093/mnras/sty1595)

(ref: GRISDALE19) Grisdale, K., Agertz, O., Renaud, F., et al. 2019, MNRAS, 486, 5482, doi: [`10.1093/mnras/stz1201`](http://doi.org/10.1093/mnras/stz1201)

(ref: henshaw2023) Henshaw, J. D., Barnes, A. T., Battersby, C., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 83, doi: [`10.48550/arXiv.2203.11223`](http://doi.org/10.48550/arXiv.2203.11223)

(ref: HENSHAW16GMCS) Henshaw, J. D., Longmore, S. N., Kruijssen, J. M. D., et al. 2016, MNRAS, 457, 2675, doi: [`10.1093/mnras/stw121`](http://doi.org/10.1093/mnras/stw121)

(ref: HENSHAW20SCOUSE) Henshaw, J. D., Kruijssen, J. M. D., Longmore, S. N., et al. 2020, Nature Astronomy, 4, 1064, doi: [`10.1038/s41550-020-1126-z`](http://doi.org/10.1038/s41550-020-1126-z)

(ref: HEYER15REVIEW) Heyer, M., & Dame, T. M. 2015, ARA&A, 53, 583, doi: [`10.1146/annurev-astro-082214-122324`](http://doi.org/10.1146/annurev-astro-082214-122324)

(ref: HEYER09GMCS) Heyer, M., Krawczyk, C., Duval, J., & Jackson, J. M. 2009, ApJ, 699, 1092, doi: [`10.1088/0004-637X/699/2/1092`](http://doi.org/10.1088/0004-637X/699/2/1092)

(ref: HEYER01GMCS) Heyer, M. H., Carpenter, J. M., & Snell, R. L. 2001, ApJ, 551, 852, doi: [`10.1086/320218`](http://doi.org/10.1086/320218)

(ref: HIROTA18GMCS) Hirota, A., Egusa, F., Baba, J., et al. 2018, PASJ, 70, 73, doi: [`10.1093/pasj/psy071`](http://doi.org/10.1093/pasj/psy071)

(ref: HOPKINS11SIMS) Hopkins, P. F., Quataert, E., & Murray, N. 2011, MNRAS, 417, 950, doi: [`10.1111/j.1365-2966.2011.19306.x`](http://doi.org/10.1111/j.1365-2966.2011.19306.x)

(ref: HU22XCO) Hu, C.-Y., Schruba, A., Sternberg, A., & van Dishoeck, E. F. 2022, ApJ, 931, 28, doi: [`10.3847/1538-4357/ac65fd`](http://doi.org/10.3847/1538-4357/ac65fd)

(ref: HUGHES13GMCS) Hughes, A., Meidt, S. E., Colombo, D., et al. 2013, ApJ, 779, 46, doi: [`10.1088/0004-637X/779/1/46`](http://doi.org/10.1088/0004-637X/779/1/46)

(ref: IBANEZMEJIA16GMCS) Ibáñez-Mejı́a, J. C., Mac Low, M.-M., Klessen, R. S., & Baczynski, C. 2016, ApJ, 824, 41, doi: [`10.3847/0004-637X/824/1/41`](http://doi.org/10.3847/0004-637X/824/1/41)

(ref: ISRAEL20XCO) Israel, F. P. 2020, A&A, 635, A131, doi: [`10.1051/0004-6361/201834198`](http://doi.org/10.1051/0004-6361/201834198)

(ref: JEFFRESON23GMCS) Jeffreson, S. M. R., Semenov, V. A., & Krumholz, M. R. 2023, arXiv e-prints, arXiv:2301.10251, doi: [`10.48550/arXiv.2301.10251`](http://doi.org/10.48550/arXiv.2301.10251)

(ref: JEFFRESON22GMCS) Jeffreson, S. M. R., Sun, J., & Wilson, C. D. 2022, MNRAS, 515, 1663, doi: [`10.1093/mnras/stac1874`](http://doi.org/10.1093/mnras/stac1874)

(ref: JIMENEZ19DENSE) Jiménez-Donaire, M. J., Bigiel, F., Leroy, A. K., et al. 2019, ApJ, 880, 127, doi: [`10.3847/1538-4357/ab2b95`](http://doi.org/10.3847/1538-4357/ab2b95)

(ref: JIMENEZ23DENSE) Jiménez-Donaire, M. J., Usero, A., Bešlić, I., et al. 2023, A&A, 676, L11, doi: [`10.1051/0004-6361/202347050`](http://doi.org/10.1051/0004-6361/202347050)

(ref: JOGEE05SFGAS) Jogee, S., Scoville, N., & Kenney, J. D. P. 2005, ApJ, 630, 837, doi: [`10.1086/432106`](http://doi.org/10.1086/432106)

(ref: KAINULAINEN09DENSE) Kainulainen, J., Beuther, H., Henning, T., & Plume, R. 2009, A&A, 508, L35, doi: [`10.1051/0004-6361/200913605`](http://doi.org/10.1051/0004-6361/200913605)

(ref: KATZ92SIMS) Katz, N. 1992, ApJ, 391, 502, doi: [`10.1086/171366`](http://doi.org/10.1086/171366)

(ref: KEENAN24LINES) Keenan, R. P., Marrone, D. P., & Keating, G. K. 2024, arXiv e-prints, arXiv:2409.03963, doi: [`10.48550/arXiv.2409.03963`](http://doi.org/10.48550/arXiv.2409.03963)

(ref: KENNICUTT12REVIEW) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: KIM23TIGRESS) Kim, C.-G., Kim, J.-G., Gong, M., & Ostriker, E. C. 2023, ApJ, 946, 3, doi: [`10.3847/1538-4357/acbd3a`](http://doi.org/10.3847/1538-4357/acbd3a)

(ref: KIM22TIMES) Kim, J., Chevance, M., Kruijssen, J. M. D., et al. 2022, MNRAS, 516, 3006, doi: [`10.1093/mnras/stac2339`](http://doi.org/10.1093/mnras/stac2339)

(ref: KIM21FEEDBACKSIMS) Kim, J.-G., Ostriker, E. C., & Filippova, N. 2021, ApJ, 911, 128, doi: [`10.3847/1538-4357/abe934`](http://doi.org/10.3847/1538-4357/abe934)

(ref: KIM14SIMS) Kim, J.-h., Abel, T., Agertz, O., et al. 2014, ApJS, 210, 14, doi: [`10.1088/0067-0049/210/1/14`](http://doi.org/10.1088/0067-0049/210/1/14)

(ref: KOCH18LINEWIDTH) Koch, E., Rosolowsky, E., & Leroy, A. K. 2018, Research Notes of the American Astronomical Society, 2, 220, doi: [`10.3847/2515-5172/aaf508`](http://doi.org/10.3847/2515-5172/aaf508)

(ref: KODA21SFGAS) Koda, J. 2021, Research Notes of the American Astronomical Society, 5, 222, doi: [`10.3847/2515-5172/ac2d34`](http://doi.org/10.3847/2515-5172/ac2d34)

(ref: KORMENDY04REVIEW) Kormendy, J., & Kennicutt, Robert C., J. 2004, ARA&A, 42, 603, doi: [`10.1146/annurev.astro.42.053102.134024`](http://doi.org/10.1146/annurev.astro.42.053102.134024)

(ref: KRUIJSSEN19TIMES) Kruijssen, J. M. D., Schruba, A., Chevance, M., et al. 2019, Nature, 569, 519, doi: [`10.1038/s41586-019-1194-3`](http://doi.org/10.1038/s41586-019-1194-3)

(ref: KRUMHOLZ14REVIEW) Krumholz, M. R. 2014, Phys. Rep., 539, 49, doi: [`10.1016/j.physrep.2014.02.001`](http://doi.org/10.1016/j.physrep.2014.02.001)

(ref: KRUMHOLZ05EFF) Krumholz, M. R., & McKee, C. F. 2005, ApJ, 630, 250, doi: [`10.1086/431734`](http://doi.org/10.1086/431734)

(ref: KRUMHOLZ07DENSE) Krumholz, M. R., & Thompson, T. A. 2007, ApJ, 669, 289, doi: [`10.1086/521642`](http://doi.org/10.1086/521642)

(ref: KUNO07CO) Kuno, N., Sato, N., Nakanishi, H., et al. 2007, PASJ, 59, 117, doi: [`10.1093/pasj/59.1.117`](http://doi.org/10.1093/pasj/59.1.117)

(ref: LADA12DENSE) Lada, C. J., Forbrich, J., Lombardi, M., & Alves, J. F. 2012, ApJ, 745, 190, doi: [`10.1088/0004-637X/745/2/190`](http://doi.org/10.1088/0004-637X/745/2/190)

(ref: LADA10DENSE) Lada, C. J., Lombardi, M., & Alves, J. F. 2010, ApJ, 724, 687, doi: [`10.1088/0004-637X/724/1/687`](http://doi.org/10.1088/0004-637X/724/1/687)

(ref: LANG20KINEMATICS) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122, doi: [`10.3847/1538-4357/ab9953`](http://doi.org/10.3847/1538-4357/ab9953)

(ref: LEROY08SFGAS) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782, doi: [`10.1088/0004-6256/136/6/2782`](http://doi.org/10.1088/0004-6256/136/6/2782)

(ref: HERACLES09SURVEY) Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137, 4670, doi: [`10.1088/0004-6256/137/6/4670`](http://doi.org/10.1088/0004-6256/137/6/4670)

(ref: LEROY13SFGAS) Leroy, A. K., Walter, F., Sandstrom, K., et al. 2013, AJ, 146, 19, doi: [`10.1088/0004-6256/146/2/19`](http://doi.org/10.1088/0004-6256/146/2/19)

(ref: LEROY16GMCS) Leroy, A. K., Hughes, A., Schruba, A., et al. 2016, ApJ, 831, 16, doi: [`10.3847/0004-637X/831/1/16`](http://doi.org/10.3847/0004-637X/831/1/16)

(ref: LEROY17SFGAS) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2017a, ApJ, 846, 71, doi: [`10.3847/1538-4357/aa7fef`](http://doi.org/10.3847/1538-4357/aa7fef)

(ref: LEROY17DENSE) Leroy, A. K., Usero, A., Schruba, A., et al. 2017b, ApJ, 835, 217, doi: [`10.3847/1538-4357/835/2/217`](http://doi.org/10.3847/1538-4357/835/2/217)

(ref: LEROY19Z0MGS) Leroy, A. K., Sandstrom, K. M., Lang, D., et al. 2019, ApJS, 244, 24, doi: [`10.3847/1538-4365/ab3925`](http://doi.org/10.3847/1538-4365/ab3925)

(ref: PHANGSALMA21SURVEY) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: LEROY22LINES) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2022, ApJ, 927, 149, doi: [`10.3847/1538-4357/ac3490`](http://doi.org/10.3847/1538-4357/ac3490)

(ref: LIN22SFGAS) Lin, L., Ellison, S. L., Pan, H.-A., et al. 2022, ApJ, 926, 175, doi: [`10.3847/1538-4357/ac4ccc`](http://doi.org/10.3847/1538-4357/ac4ccc)

(ref: LIU21GMCS) Liu, L., Bureau, M., Blitz, L., et al. 2021, MNRAS, 505, 4048, doi: [`10.1093/mnras/stab1537`](http://doi.org/10.1093/mnras/stab1537)

(ref: LU24GMCs) Lu, A., Haggard, D., Bureau, M., et al. 2024, MNRAS, 531, 3888, doi: [`10.1093/mnras/stae1395`](http://doi.org/10.1093/mnras/stae1395)

(ref: MACLOW04REVIEW) Mac Low, M.-M., & Klessen, R. S. 2004, Reviews of Modern Physics, 76, 125, doi: [`10.1103/RevModPhys.76.125`](http://doi.org/10.1103/RevModPhys.76.125)

(ref: MAIOLINO19REVIEW) Maiolino, R., & Mannucci, F. 2019, A&ARv, 27, 3, doi: [`10.1007/s00159-018-0112-2`](http://doi.org/10.1007/s00159-018-0112-2)

(ref: GALEX05) Martin, D. C., Fanson, J., Schiminovich, D., et al. 2005, ApJL, 619, L1, doi: [`10.1086/426387`](http://doi.org/10.1086/426387)

(ref: MCKEE07REVIEW) McKee, C. F., & Ostriker, E. C. 2007, ARA&A, 45, 565, doi: [`10.1146/annurev.astro.45.051806.110602`](http://doi.org/10.1146/annurev.astro.45.051806.110602)

(ref: MCKEE92GMCS) McKee, C. F., & Zweibel, E. G. 1992, ApJ, 399, 551, doi: [`10.1086/171946`](http://doi.org/10.1086/171946)

(ref: MEIDT13SFGAS) Meidt, S. E., Schinnerer, E., Garcı́a-Burillo, S., et al. 2013, ApJ, 779, 45, doi: [`10.1088/0004-637X/779/1/45`](http://doi.org/10.1088/0004-637X/779/1/45)

(ref: MEIDT15SFGAS) Meidt, S. E., Hughes, A., Dobbs, C. L., et al. 2015, ApJ, 806, 72, doi: [`10.1088/0004-637X/806/1/72`](http://doi.org/10.1088/0004-637X/806/1/72)

(ref: MEIDT18GMCS) Meidt, S. E., Leroy, A. K., Rosolowsky, E., et al. 2018, ApJ, 854, 100, doi: [`10.3847/1538-4357/aaa290`](http://doi.org/10.3847/1538-4357/aaa290)

(ref: MURAOKA19COMING) Muraoka, K., Sorai, K., Miyamoto, Y., et al. 2019, PASJ, 71, S15, doi: [`10.1093/pasj/psz015`](http://doi.org/10.1093/pasj/psz015)

(ref: NEUMANN23DENSE) Neumann, L., Gallagher, M. J., Bigiel, F., et al. 2023, MNRAS, 521, 3348, doi: [`10.1093/mnras/stad424`](http://doi.org/10.1093/mnras/stad424)

(ref: PADOAN12EFF) Padoan, P., Haugbølle, T., & Nordlund, Å. 2012, ApJL, 759, L27, doi: [`10.1088/2041-8205/759/2/L27`](http://doi.org/10.1088/2041-8205/759/2/L27)

(ref: PADOAN02TURB) Padoan, P., & Nordlund, Å. 2002, ApJ, 576, 870, doi: [`10.1086/341790`](http://doi.org/10.1086/341790)

(ref: PADOAN11EFF) —. 2011, ApJ, 730, 40, doi: [`10.1088/0004-637X/730/1/40`](http://doi.org/10.1088/0004-637X/730/1/40)

(ref: PAN22TIMES) Pan, H.-A., Schinnerer, E., Hughes, A., et al. 2022, ApJ, 927, 9, doi: [`10.3847/1538-4357/ac474f`](http://doi.org/10.3847/1538-4357/ac474f)

(ref: PAN24SFGAS) Pan, H.-A., Lin, L., Ellison, S. L., et al. 2024, ApJ, 964, 120, doi: [`10.3847/1538-4357/ad28c1`](http://doi.org/10.3847/1538-4357/ad28c1)

(ref: PATHAK24MIDIR) Pathak, D., Leroy, A. K., Thompson, T. A., et al. 2024, AJ, 167, 39, doi: [`10.3847/1538-3881/ad110d`](http://doi.org/10.3847/1538-3881/ad110d)

(ref: QUEREJETA21) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, A&A, 656, A133, doi: [`10.1051/0004-6361/202140695`](http://doi.org/10.1051/0004-6361/202140695)

(ref: QUEREJETA23SFGAS) Querejeta, M., Pety, J., Schruba, A., et al. 2023, A&A, 680, A4, doi: [`10.1051/0004-6361/202143023`](http://doi.org/10.1051/0004-6361/202143023)

(ref: QUEREJETA24SFGAS) Querejeta, M., Leroy, A. K., Meidt, S. E., et al. 2024, arXiv e-prints, arXiv:2405.05364, doi: [`10.48550/arXiv.2405.05364`](http://doi.org/10.48550/arXiv.2405.05364)

(ref: REGAN01SFGAS) Regan, M. W., Thornley, M. D., Helfer, T. T., et al. 2001, ApJ, 561, 218, doi: [`10.1086/323221`](http://doi.org/10.1086/323221)

(ref: RENAUD21) Renaud, F., Romeo, A. B., & Agertz, O. 2021, MNRAS, 508, 352, doi: [`10.1093/mnras/stab2604`](http://doi.org/10.1093/mnras/stab2604)

(ref: ROSOLOWSKY21GMCS) Rosolowsky, E., Hughes, A., Leroy, A. K., et al. 2021, MNRAS, 502, 1218, doi: [`10.1093/mnras/stab085`](http://doi.org/10.1093/mnras/stab085)

(ref: SAINTONGE22REVIEW) Saintonge, A., & Catinella, B. 2022, ARA&A, 60, 319, doi: [`10.1146/annurev-astro-021022-043545`](http://doi.org/10.1146/annurev-astro-021022-043545)

(ref: SAINTONGE11SFGAS) Saintonge, A., Kauffmann, G., Wang, J., et al. 2011, MNRAS, 415, 61, doi: [`10.1111/j.1365-2966.2011.18823.x`](http://doi.org/10.1111/j.1365-2966.2011.18823.x)

(ref: SAINTONGE17SFGAS) Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22, doi: [`10.3847/1538-4365/aa97e0`](http://doi.org/10.3847/1538-4365/aa97e0)

(ref: GSWLC16) Salim, S., Lee, J. C., Janowiecki, S., et al. 2016, ApJS, 227, 2, doi: [`10.3847/0067-0049/227/1/2`](http://doi.org/10.3847/0067-0049/227/1/2)

(ref: SANDSTROM13XCO) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5, doi: [`10.1088/0004-637X/777/1/5`](http://doi.org/10.1088/0004-637X/777/1/5)

(ref: SCHINNERER24REVIEW) Schinnerer, E., & Leroy, A. K. 2024, arXiv e-prints, arXiv:2403.19843, doi: [`10.48550/arXiv.2403.19843`](http://doi.org/10.48550/arXiv.2403.19843)

(ref: SCHINNERER19TIMES) Schinnerer, E., Hughes, A., Leroy, A., et al. 2019, ApJ, 887, 49, doi: [`10.3847/1538-4357/ab50c2`](http://doi.org/10.3847/1538-4357/ab50c2)

(ref: SCHRUBA19GMCS) Schruba, A., Kruijssen, J. M. D., & Leroy, A. K. 2019, ApJ, 883, 2, doi: [`10.3847/1538-4357/ab3a43`](http://doi.org/10.3847/1538-4357/ab3a43)

(ref: SCHRUBA10SFGAS) Schruba, A., Leroy, A. K., Walter, F., Sandstrom, K., & Rosolowsky, E. 2010, ApJ, 722, 1699, doi: [`10.1088/0004-637X/722/2/1699`](http://doi.org/10.1088/0004-637X/722/2/1699)

(ref: SCHRUBA11SFGAS) Schruba, A., Leroy, A. K., Walter, F., et al. 2011, AJ, 142, 37, doi: [`10.1088/0004-6256/142/2/37`](http://doi.org/10.1088/0004-6256/142/2/37)

(ref: SCHRUBA12XCO) —. 2012, AJ, 143, 138, doi: [`10.1088/0004-6256/143/6/138`](http://doi.org/10.1088/0004-6256/143/6/138)

(ref: SEGOVIAOTERO24) Segovia Otero, Á., Agertz, O., Renaud, F., et al. 2024, arXiv e-prints, arXiv:2410.08266, doi: [`10.48550/arXiv.2410.08266`](http://doi.org/10.48550/arXiv.2410.08266)

(ref: SEMENOV17GMCS) Semenov, V. A., Kravtsov, A. V., & Gnedin, N. Y. 2017, ApJ, 845, 133, doi: [`10.3847/1538-4357/aa8096`](http://doi.org/10.3847/1538-4357/aa8096)

(ref: SEMENOV18GMCS) —. 2018, ApJ, 861, 4, doi: [`10.3847/1538-4357/aac6eb`](http://doi.org/10.3847/1538-4357/aac6eb)

(ref: SEMENOV21GMCS) —. 2021, ApJ, 918, 13, doi: [`10.3847/1538-4357/ac0a77`](http://doi.org/10.3847/1538-4357/ac0a77)

(ref: S4GSURVEY) Sheth, K., Regan, M., Hinz, J. L., et al. 2010, PASP, 122, 1397, doi: [`10.1086/657638`](http://doi.org/10.1086/657638)

(ref: STUBER23DENSE) Stuber, S. K., Pety, J., Schinnerer, E., et al. 2023, A&A, 680, L20, doi: [`10.1051/0004-6361/202348205`](http://doi.org/10.1051/0004-6361/202348205)

(ref: SUN18CLOUDS) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860, 172, doi: [`10.3847/1538-4357/aac326`](http://doi.org/10.3847/1538-4357/aac326)

(ref: SUN20PRESS) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2020a, ApJ, 892, 148, doi: [`10.3847/1538-4357/ab781c`](http://doi.org/10.3847/1538-4357/ab781c)

(ref: SUN20GMCS) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020b, ApJL, 901, L8, doi: [`10.3847/2041-8213/abb3be`](http://doi.org/10.3847/2041-8213/abb3be)

(ref: SUN22CLOUDS) Sun, J., Leroy, A. K., Rosolowsky, E., et al. 2022, AJ, 164, 43, doi: [`10.3847/1538-3881/ac74bd`](http://doi.org/10.3847/1538-3881/ac74bd)

(ref: SUN23SFGAS) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2023, ApJL, 945, L19, doi: [`10.3847/2041-8213/acbd9c`](http://doi.org/10.3847/2041-8213/acbd9c)

(ref: TACCONI20REVIEW) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157, doi: [`10.1146/annurev-astro-082812-141034`](http://doi.org/10.1146/annurev-astro-082812-141034)

(ref: TAFALLA23LINES) Tafalla, M., Usero, A., & Hacar, A. 2023, A&A, 679, A112, doi: [`10.1051/0004-6361/202346136`](http://doi.org/10.1051/0004-6361/202346136)

(ref: TENG22XCO) Teng, Y.-H., Sandstrom, K. M., Sun, J., et al. 2022, ApJ, 925, 72, doi: [`10.3847/1538-4357/ac382f`](http://doi.org/10.3847/1538-4357/ac382f)

(ref: TENG23XCO) —. 2023, ApJ, 950, 119, doi: [`10.3847/1538-4357/accb86`](http://doi.org/10.3847/1538-4357/accb86)

(ref: TENG24XCO) Teng, Y.-H., Chiang, I.-D., Sandstrom, K. M., et al. 2024, ApJ, 961, 42, doi: [`10.3847/1538-4357/ad10ae`](http://doi.org/10.3847/1538-4357/ad10ae)

(ref: UTOMO18EFF) Utomo, D., Sun, J., Leroy, A. K., et al. 2018, ApJL, 861, L18, doi: [`10.3847/2041-8213/aacf8f`](http://doi.org/10.3847/2041-8213/aacf8f)

(ref: VAZQUEZ94TURB) Vazquez-Semadeni, E. 1994, ApJ, 423, 681, doi: [`10.1086/173847`](http://doi.org/10.1086/173847)

(ref: VAZQUEZ24EFF) Vázquez-Semadeni, E., Palau, A., Gómez, G. C., et al. 2024, arXiv e-prints, arXiv:2408.10406, doi: [`10.48550/arXiv.2408.10406`](http://doi.org/10.48550/arXiv.2408.10406)

(ref: WILLIAMS23GMCS) Williams, T. G., Bureau, M., Davis, T. A., et al. 2023, MNRAS, doi: [`10.1093/mnras/stad2455`](http://doi.org/10.1093/mnras/stad2455)

(ref: WONG02SFGAS) Wong, T., & Blitz, L. 2002, ApJ, 569, 157, doi: [`10.1086/339287`](http://doi.org/10.1086/339287)

(ref: WISE10) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868, doi: [`10.1088/0004-6256/140/6/1868`](http://doi.org/10.1088/0004-6256/140/6/1868)

(ref: YAJIMA21LINES) Yajima, Y., Sorai, K., Miyamoto, Y., et al. 2021, PASJ, 73, 257, doi: [`10.1093/pasj/psaa119`](http://doi.org/10.1093/pasj/psaa119)

(ref: YOUNG91SFGAS) Young, J. S., & Scoville, N. Z. 1991, ARA&A, 29, 581, doi: [`10.1146/annurev.aa.29.090191.003053`](http://doi.org/10.1146/annurev.aa.29.090191.003053)

(ref: YOUNG95SFGAS) Young, J. S., Xie, S., Tacconi, L., et al. 1995, ApJS, 98, 219, doi: [`10.1086/192159`](http://doi.org/10.1086/192159)

# Procedure to replicate these measurements for comparison to numerical simulations or other observations

We adopt a measurement scheme that can be easily implemented to allow rigorous, “apples to apples” comparison between PHANGS–ALMA and either numerical simulations or observations of other samples of galaxies.

1.  When working with CO data, first apply a local best-estimate $\alpha_{\rm CO}$ to convert the data into units of molecular gas mass. In a simulation estimate the mass in the CO-bright molecular gas phase likely to enter our analysis. CO bright emission visible to PHANGS–ALMA at 150 pc would be defined as $> 0.6$ K km s$^{-1}$, or about $3\times$ the typical rms integrated intensity noise.

2.  Convolve the CO or simulated molecular gas data to have a resolution of $150$ pc (FWHM). Estimate the surface density, $\Sigma_{\rm mol}$ and line width, $\sigma_{\rm mol}$ along each line of sight. Apply inclination corrections as in (cite: SUN22CLOUDS) to calculate face-on values of each quantity. In our framework the line width is the “effective width” line width as defined in (cite: SUN22CLOUDS) and references therein. From $\Sigma_{\rm mol}^{\rm cloud}$, $\sigma_{\rm mol}^{\rm cloud}$, and $R_{\rm pix}$ ($\equiv (\ell^2 H_{\rm mol} / (8 \cos i))^{1/3}$ with $H_{\rm mol} = 100$ pc and $\ell$ the resolution, here $150$ pc) calculate $\alpha_{\rm vir}$ and $\tau_{\rm ff}^{\rm mol}$.

3.  Divide the target region or galaxy into hexagonal apertures with diameter $1.5$ kpc. Within each aperture, calculate the mass-weighted expectation value of $\Sigma_{\rm mol}^{\rm cloud}$, $\sigma_{\rm mol}^{\rm cloud}$, and $\alpha_{\rm vir}^{\rm cloud}$. To do this, select all sightlines in the region and then for quantity $X$ calculate $\left< X \right> = \sum \Sigma_{\rm mol}^{\rm cloud} X / \sum \Sigma_{\rm mol}^{\rm cloud}$. In the case of $\tau_{\rm ff}^{\rm mol}$, calculate the average via $\left< \tau_{\rm ff}^{\rm cloud} \right> = \left( \sum \Sigma_{\rm mol} \left( \tau_{\rm ff}^{\rm cloud} \right)^{-1} / \sum \Sigma_{\rm mol} \right)^{-1}$ so that for a fixed efficiency per free fall time $\Sigma_{\rm SFR} = \epsilon_{\rm ff}^{\rm mol} \left< \tau_{\rm ff}^{\rm cloud} \right> \Sigma_{\rm mol}$.

4.  Estimate the molecular gas depletion time by convolving the $\Sigma_{\rm SFR}$ and $\Sigma_{\rm mol}$ maps to 1.5 kpc (FWHM) resolution. Divide them to estimate $\tau_{\rm dep}^{\rm mol}$ and sample the map at the center of each region to obtain the local $\tau_{\rm dep}^{\rm mol}$.

5.  Divide $\ensuremath{\langle \tau_{\rm ff}^{\rm cloud} \rangle}/ \ensuremath{\tau_{\rm dep}^{\rm mol}}$ to estimate the mean star formation efficiency per free fall time, $\epsilon_{\rm ff}^{\rm mol}$, in the region.

6.  Select regions with mass-weighted average molecular gas surface density $\ensuremath{\langle \Sigma_{\rm mol}^{\rm cloud} \rangle}> 20$ M$_\odot$ pc$^{-2}$ to match our completeness cut.

# PHANGS–ALMA at higher resolution

![](paper_props_vs_res.png)

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Galaxy | Radius | $\tau_{\rm dep}^{\rm mol}$ | $\frac{\tau_{\rm dep}^{\rm mol}}{\left< \tau_{\rm dep}^{\rm mol} \right>_{\rm gal}}$ | $\alpha_{\rm CO}^{2-1}$ | $i$ | $\log_{10} M_\star$ | $\log_{10} {\rm SFR}$ | $\left< \Sigma_{mol}^{\rm cloud} \right>$ | $\left< \tau_{ff}^{\rm cloud} \right>$ | $\left< \sigma_{mol}^{\rm cloud} \right>$ | $\left< \alpha_{vir}^{\rm cloud} \right>$ | $\epsilon_{\rm ff}^{\rm mol}$ | $\frac{\epsilon_{\rm ff}^{\rm mol}}{\left< \epsilon_{\rm ff}^{\rm mol} \right>_{\rm gal}}$ |
|  | (kpc) | (Gyr) | (norm.) | ($\frac{{\rm M}_\odot~{\rm pc}^{-2}}{{\rm K~km~s}^{-1}}$) | ($^\circ$) | (M$_\odot$) | (M$_\odot$ yr$^{-1}$) | (M$_\odot$ pc$^{-2}$) | (Myr) | (km s$^{-1}$) |  |  | (norm.) |
| IC1954 | 0.0 | 0.7 | 0.51 | 4.36 | 57.1 | 9.7 | -0.4 | 33.0 | 8.03 | 6.9 | 4.11 | 0.0115 | 1.66 |
| IC1954 | 1.22 | 1.44 | 1.06 | 6.57 | 57.1 | 9.7 | -0.4 | 26.0 | 9.08 | 4.9 | 2.37 | 0.0063 | 0.91 |
| IC1954 | 1.22 | 1.27 | 0.94 | 6.8 | 57.1 | 9.7 | -0.4 | 37.0 | 7.82 | 5.3 | 2.35 | 0.0062 | 0.89 |
| IC1954 | 1.31 | 1.61 | 1.18 | 7.05 | 57.1 | 9.7 | -0.4 | 35.0 | 7.95 | 5.2 | 2.41 | 0.0049 | 0.71 |
| IC1954 | 1.31 | 1.55 | 1.14 | 7.1 | 57.1 | 9.7 | -0.4 | 30.0 | 8.69 | 4.9 | 2.54 | 0.0056 | 0.81 |
| IC1954 | 1.74 | 1.97 | 1.45 | 8.23 | 57.1 | 9.7 | -0.4 | 21.0 | 10.13 | 4.1 | 2.07 | 0.0051 | 0.74 |
| IC1954 | 1.84 | 1.33 | 0.98 | 7.63 | 57.1 | 9.7 | -0.4 | 26.0 | 9.35 | 4.6 | 2.63 | 0.0071 | 1.02 |
| IC1954 | 2.95 | 1.23 | 0.91 | 9.53 | 57.1 | 9.7 | -0.4 | 23.0 | 9.61 | 4.4 | 2.08 | 0.0078 | 1.13 |
| IC5273 | 0.0 | 0.38 | 0.51 | 3.87 | 52.0 | 9.7 | -0.3 | 62.0 | 6.66 | 7.6 | 4.0 | 0.0177 | 1.1 |

: Measurements for individual regions at $\ell = 120$ pc in 1.0 kpc diameter regions

Table notes: This is a stub. The full table is available online as part of a machine readable table. Columns: (1) galaxy name, (2) galactocentric radius, (3) molecular gas depletion time, (4) molecular gas depeletion time normalized to galaxy average, (5) CO (2-1) to H$_2$ conversion factor, (6) galaxy inclination, (7) galaxy integrated stellar mass, (8) galaxy integrated star formation rate, region-averaged mass weighted molecular gas: (9) surface density, (10) gravitational free-fall time, (11) line width, and (12) virial parameter, (13) star formation efficiency per free fall time, (14) star formation efficiency per free fall time normalized to galaxy average.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Galaxy | Radius | $\tau_{\rm dep}^{\rm mol}$ | $\frac{\tau_{\rm dep}^{\rm mol}}{\left< \tau_{\rm dep}^{\rm mol} \right>_{\rm gal}}$ | $\alpha_{\rm CO}^{2-1}$ | $i$ | $\log_{10} M_\star$ | $\log_{10} {\rm SFR}$ | $\left< \Sigma_{mol}^{\rm cloud} \right>$ | $\left< \tau_{ff}^{\rm cloud} \right>$ | $\left< \sigma_{mol}^{\rm cloud} \right>$ | $\left< \alpha_{vir}^{\rm cloud} \right>$ | $\epsilon_{\rm ff}^{\rm mol}$ | $\frac{\epsilon_{\rm ff}^{\rm mol}}{\left< \epsilon_{\rm ff}^{\rm mol} \right>_{\rm gal}}$ |
|  | (kpc) | (Gyr) | (norm.) | ($\frac{{\rm M}_\odot~{\rm pc}^{-2}}{{\rm K~km~s}^{-1}}$) | ($^\circ$) | (M$_\odot$) | (M$_\odot$ yr$^{-1}$) | (M$_\odot$ pc$^{-2}$) | (Myr) | (km s$^{-1}$) |  |  | (norm.) |
| IC1954 | 0.0 | 0.7 | 0.51 | 4.36 | 57.1 | 9.7 | -0.4 | 35.0 | 7.04 | 6.2 | 3.82 | 0.0101 | 1.66 |
| IC1954 | 1.22 | 1.44 | 1.06 | 6.57 | 57.1 | 9.7 | -0.4 | 28.0 | 7.94 | 4.5 | 2.3 | 0.0055 | 0.91 |
| IC1954 | 1.22 | 1.27 | 0.94 | 6.8 | 57.1 | 9.7 | -0.4 | 38.0 | 6.92 | 5.0 | 2.31 | 0.0054 | 0.9 |
| IC1954 | 1.31 | 1.61 | 1.18 | 7.05 | 57.1 | 9.7 | -0.4 | 37.0 | 7.02 | 4.9 | 2.37 | 0.0044 | 0.72 |
| IC1954 | 1.31 | 1.55 | 1.14 | 7.1 | 57.1 | 9.7 | -0.4 | 31.0 | 7.66 | 4.6 | 2.39 | 0.005 | 0.82 |
| IC1954 | 1.74 | 1.97 | 1.45 | 8.23 | 57.1 | 9.7 | -0.4 | 22.0 | 8.97 | 3.7 | 1.99 | 0.0046 | 0.75 |
| IC1954 | 1.84 | 1.33 | 0.98 | 7.63 | 57.1 | 9.7 | -0.4 | 30.0 | 7.94 | 4.2 | 2.4 | 0.006 | 0.99 |
| IC1954 | 2.95 | 1.23 | 0.91 | 9.53 | 57.1 | 9.7 | -0.4 | 25.0 | 8.41 | 4.0 | 1.94 | 0.0068 | 1.13 |
| NGC0628 | 0.0 | 1.53 | 0.56 | 2.63 | 8.9 | 10.3 | 0.2 | 22.0 | 11.62 | 4.6 | 6.65 | 0.0076 | 1.82 |

: Measurements for individual regions at $\ell = 90$ pc in 1.0 kpc diameter regions

Table notes: This is a stub. The full table is available online as part of a machine readable table. Columns: (1) galaxy name, (2) galactocentric radius, (3) molecular gas depletion time, (4) molecular gas depeletion time normalized to galaxy average, (5) CO (2-1) to H$_2$ conversion factor, (6) galaxy inclination, (7) galaxy integrated stellar mass, (8) galaxy integrated star formation rate, region-averaged mass weighted molecular gas: (9) surface density, (10) gravitational free-fall time, (11) line width, and (12) virial parameter, (13) star formation efficiency per free fall time, (14) star formation efficiency per free fall time normalized to galaxy average.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Galaxy | Radius | $\tau_{\rm dep}^{\rm mol}$ | $\frac{\tau_{\rm dep}^{\rm mol}}{\left< \tau_{\rm dep}^{\rm mol} \right>_{\rm gal}}$ | $\alpha_{\rm CO}^{2-1}$ | $i$ | $\log_{10} M_\star$ | $\log_{10} {\rm SFR}$ | $\left< \Sigma_{mol}^{\rm cloud} \right>$ | $\left< \tau_{ff}^{\rm cloud} \right>$ | $\left< \sigma_{mol}^{\rm cloud} \right>$ | $\left< \alpha_{vir}^{\rm cloud} \right>$ | $\epsilon_{\rm ff}^{\rm mol}$ | $\frac{\epsilon_{\rm ff}^{\rm mol}}{\left< \epsilon_{\rm ff}^{\rm mol} \right>_{\rm gal}}$ |
|  | (kpc) | (Gyr) | (norm.) | ($\frac{{\rm M}_\odot~{\rm pc}^{-2}}{{\rm K~km~s}^{-1}}$) | ($^\circ$) | (M$_\odot$) | (M$_\odot$ yr$^{-1}$) | (M$_\odot$ pc$^{-2}$) | (Myr) | (km s$^{-1}$) |  |  | (norm.) |
| NGC0628 | 0.0 | 1.53 | 0.55 | 2.63 | 8.9 | 10.3 | 0.2 | 24.0 | 9.07 | 4.2 | 7.21 | 0.0059 | 1.95 |
| NGC0628 | 1.0 | 2.79 | 1.0 | 3.61 | 8.9 | 10.3 | 0.2 | 28.0 | 8.5 | 3.8 | 4.68 | 0.0031 | 1.0 |
| NGC0628 | 1.0 | 2.09 | 0.75 | 3.51 | 8.9 | 10.3 | 0.2 | 24.0 | 8.98 | 4.0 | 5.7 | 0.0043 | 1.41 |
| NGC0628 | 1.01 | 2.18 | 0.78 | 3.51 | 8.9 | 10.3 | 0.2 | 35.0 | 7.75 | 4.6 | 5.55 | 0.0036 | 1.17 |
| NGC0628 | 1.01 | 2.31 | 0.83 | 3.61 | 8.9 | 10.3 | 0.2 | 27.0 | 8.66 | 4.3 | 5.26 | 0.0038 | 1.23 |
| NGC0628 | 1.01 | 2.95 | 1.06 | 3.71 | 8.9 | 10.3 | 0.2 | 21.0 | 9.94 | 3.5 | 5.02 | 0.0034 | 1.11 |
| NGC0628 | 1.01 | 2.24 | 0.8 | 3.72 | 8.9 | 10.3 | 0.2 | 30.0 | 8.48 | 4.4 | 5.19 | 0.0038 | 1.24 |
| NGC0628 | 1.74 | 2.67 | 0.96 | 4.64 | 8.9 | 10.3 | 0.2 | 20.0 | 10.02 | 3.3 | 3.77 | 0.0038 | 1.23 |
| NGC0628 | 1.74 | 2.47 | 0.88 | 4.67 | 8.9 | 10.3 | 0.2 | 22.0 | 9.47 | 3.2 | 4.28 | 0.0038 | 1.26 |

: Measurements for individual regions at $\ell = 60$ pc in 1.0 kpc diameter regions

Table notes: This is a stub. The full table is available online as part of a machine readable table. Columns: (1) galaxy name, (2) galactocentric radius, (3) molecular gas depletion time, (4) molecular gas depeletion time normalized to galaxy average, (5) CO (2-1) to H$_2$ conversion factor, (6) galaxy inclination, (7) galaxy integrated stellar mass, (8) galaxy integrated star formation rate, region-averaged mass weighted molecular gas: (9) surface density, (10) gravitational free-fall time, (11) line width, and (12) virial parameter, (13) star formation efficiency per free fall time, (14) star formation efficiency per free fall time normalized to galaxy average.

In the main text, we present results at $\ell = 150$ pc resolution. PHANGS–ALMA also represents the largest survey of CO from galaxies at $120$ pc, $90$ pc, and $60$ pc resolution, though we have fewer galaxies at these higher resolutions. Tables [7](#tab:data120), [8](#tab:data90), and [9](#tab:data60) report results that measure cloud-scale properties at these higher resolutions. We apply the same completeness and surface density cuts, but work with $1$ kpc diameter hexagonal regions rather than the $1.5$ kpc diameter used for the main results. This is possible because the galaxies with higher physical resolution are also closer, meaning that our $\Sigma_{\rm SFR}$ estimates (which use lower resolution WISE data) can reach $1$ kpc resolution. Given this, our sample at $\ell = 120$ pc consists of $966$ 1 kpc regions in $41$ galaxies. At $\ell = 90$ pc we have 552 regions in $28$ galaxies, and at $\ell = 60$ pc we have 170 regions in $9$ galaxies. Figure [16](#fig:props_vs_res) show $\tau_{\rm dep}^{\rm mol}$ as a function of $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ and $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ for each of these resolutions, with our fiducial results overplotted as a black line. Overall all three resolutions show consistent results, though the number of galaxies centers with extreme conditions is lower for the smaller samples at higher linear resolution. Because radial variations in gas properties drive our dynamic range (§[3.4](#sec:byrad)), especially extreme conditions at galaxy centers, the trends are noisier for these high resolution data sets.

[^1]: Following, e.g., (cite: SCHINNERER24REVIEW) we refer to observations that match the beam to the size of a massive molecular cloud as “cloud-scale” imaging, in contrast to “resolved cloud” imaging or “resolved galaxy” imaging.

[^2]: Our $\alpha_{\rm CO}$ estimates are calculated region-by-region, so when we conduct region-averages we assume a fixed $\alpha_{\rm CO}$ within each region.

[^3]: Specifically, as in (cite: SUN23SFGAS), we convolve both $\Sigma_{\rm mol}$ and $\Sigma_{\rm SFR}$ to share a matched Gaussian kernel with FWHM equal to the hex diameter and then sample the value of those convolved maps at the hex center.

[^4]: This total flux is well-measured by summing the PHANGS–ALMA data, which include short- and zero-spacing data, without any aggressive high resolution masking.

[^5]: Our CO-to-H$_2$ conversion factor follows the prescription in (cite: SCHINNERER24REVIEW) while (cite: SUN23SFGAS) adopts the prescription by (cite: BOLATTO13REVIEW) among others. Fig. [3](#fig:scaling) shows that the two yield comparable results here.

[^6]: Here we discuss general scalings among cloud properties, not our specific observables, and so omit the averaging notation.

[^7]: Though note that there could be a subtle second-order effect due to variations in $\alpha_{\rm CO}$ within a region, which might affect the weighted averaging scheme.

</paper>

Write the methods card for this paper.