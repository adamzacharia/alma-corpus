# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020MNRAS.498.4256C\sonnetcc\reply.txt

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
 "bibcode": "2020MNRAS.498.4256C",
 "title": "The observational impact of dust trapping in self-gravitating discs",
 "year": 2020,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Cadman, James",
 "n_authors": 5,
 "arxiv_id": "2008.09826",
 "doi": "10.1093/mnras/staa2596",
 "alma_projects_linked_by_archive": [
  "2011.0.00531.S",
  "2013.1.00226.S",
  "2013.1.00366.S",
  "2013.1.00498.S",
  "2013.1.00601.S",
  "2013.1.00694.S",
  "2013.1.00798.S",
  "2015.1.00486.S",
  "2015.1.00964.S",
  "2016.1.00484.L"
 ]
}
```

Paper text:
<paper>
# The observational impact of dust trapping in self-gravitating discs

## Abstract

We present a 3D semi-analytic model of self-gravitating discs, and include a prescription for dust trapping in the disc spiral arms. Using Monte-Carlo radiative transfer we produce synthetic ALMA observations of these discs. In doing so we demonstrate that our model is capable of producing observational predictions, and able to model real image data of potentially self-gravitating discs. For a disc to generate spiral structure that would be observable with ALMA requires that the disc’s dust mass budget is dominated by millimetre and centimetre-sized grains. Discs in which grains have grown to the grain fragmentation threshold may satisfy this criterion, thus we predict that signatures of gravitational instability may be detectable in discs of lower mass than has previously been suggested. For example, we find that discs with disc-to-star mass ratios as low as $0.10$ are capable of driving observable spiral arms. Substructure becomes challenging to detect in discs where no grain growth has occurred or in which grain growth has proceeded well beyond the grain fragmentation threshold. We demonstrate how we can use our model to retrieve information about dust trapping and grain growth through multi-wavelength observations of discs, and using estimates of the opacity spectral index. Applying our disc model to the Elias 27, WaOph 6 and IM Lup systems we find gravitational instability to be a plausible explanation for the observed substructure in all 3 discs, if sufficient grain growth has indeed occurred.

planets and satellites: formation – accretion, accretion discs – gravitation – instabilities – (stars:) circumstellar matter – stars: formation

# Introduction

Discs around very young stars are typically heavily embedded and optically thick to optical wavelengths (cite: dunhametal14). They will, however, emit thermal infrared (IR) radiation and may be resolved by high-resolution, sub-mm observations with the Atacama Large Millimeter/submillimeter Array (ALMA). Thanks to recent observational advances, spiral substructure, characteristic of massive self-gravitating protoplanetary discs, is now within our observing capabilities. (cite: perezetal16; dsharp1; dsharp2).

Non-axisymmetric structure will manifest as spiral density perturbations when (cite: durisenetal07), $$\begin{equation}
\label{eq:Q}
    Q=\frac{c_{\rm s}\kappa}{\pi \mathrm{G} \Sigma} \lesssim 1.5-1.7,
\end{equation}$$ where $Q$ is the Toomre parameter (cite: toomre64), $c_{\rm s}$ is the disc sound speed, $\kappa$ is the epicyclic frequency (equal to the angular frequency, $\Omega$, in a Keplerian disc), G is the gravitational constant and $\Sigma$ is the disc surface density.

From inspection of $Q$, it is clear that more massive discs (higher $\Sigma$) will be susceptible to gravitational instabilities (hereafter GI), and it is likely that in the earliest stages of a protoplanetary disc’s lifetime they may be massive enough to generate prominent spiral structure (cite: linpringle87; linpringle90; riceetal10). The mass accretion rate in these massive discs is likely to be high (cite: riceetal10) and, hence, once a disc is no longer being replenished by envelope infall, it will be rapidly depleted. Consequently, unless the envelope is optically thin at the relevant observing wavelengths, signatures of GI will only be detectable for about $10^4$ years after accretion through the disc begins to dynamically dominate over infall from the envelope (cite: halletal19).

The Disk Substructures at High Angular Resolution Project (DSHARP) ALMA survey recently performed an in depth analysis of 20 nearby protoplanetary discs, 3 of which exhibit possible spiral substructure reminiscent of GI (cite: perezetal16; dsharp1; dsharp3).

Non-axisymmetric disc features are not unique to GI, and may be explained through alternative mechanisms such as planet-disc interactions (cite: linpapaloizou86; tanakaetal02). It may be possible to distinguish between planet and GI induced spiral structure through scattered light vs. sub-mm observations, as dust trapping in spiral regions is likely to be more effective in gravitationally unstable discs (cite: riceetal04; dongetal15b; juhaszetal15).

Spiral density perturbations in self-gravitating discs act as pressure traps for dust grains, which will radially migrate and concentrate at the pressure maxima (cite: riceetal04). Due to the negative outward gas pressure gradient, in a smooth, laminar disc, gas particles orbit with slightly sub-Keplerian velocities compared to solids at the same radii. Since the outward gas pressure gradient doesn’t directly influence the solids, this can produce a significant gas drag on the faster orbiting dust grains, resulting in their radial migration. Micron-sized grains, however, will typically be strongly coupled to the gas, hence will orbit with the same, sub-Keplerian velocities and will closely trace the gas distribution. Metre-sized, and larger, objects will be largely decoupled and will orbit with approximately Keplerian velocities. Intermediate, $\sim$mm-sized grains will however experience a large radial drift.

In smooth, laminar discs radial drift results in migration toward the disc centre where gas pressure is maximum. However, the propagation of GI induced spiral density perturbations will generate a non-axisymmetric pressure gradient, resulting in significant concentration of mm-sized grains at the peaks of the spiral density waves. This will have important consequences; producing enhanced emission in these regions as well as potentially accelerating planetesimal growth (cite: riceetal04; riceetal06). (cite: dipierro14; dipierro15) have previously shown that GI induced spiral structure should be detectable with ALMA at moderate distances ($d\sim140$ pc), and that dust migration as a result of self-gravitating disc structure will produce detectable signatures in their observed spectral index maps.

In this paper we build on previous work by (cite: halletal16) who developed a semi-analytic formalism for determining the structure of self-gravitating protostellar discs, performed 3D Monte Carlo radiative transfer on these models and produced synthetic disc images using the ALMA simulator. We add to this by including a prescription for the effects of dust grain enhancement in the spiral density waves. These models allow us to produce a suite of discs at little computational expense when compared to approaches such as Smoothed Particle Hydrodynamics (SPH). Therefore, we are able to efficiently explore a wide range of disc parameter space and produce observational predictions for telescopes such as ALMA.

In Sections [2](#sec:discmodel) and [3](#sec:casa) we present our disc model setup, and describe the radiative transfer approach as well as how we used the ALMA simulator in our analysis. In Section [4](#sec:sphdust) we use SPH to model the extent to which we might expect grains to be enhanced in self-gravitating discs, allowing us to inform our semi-analytic prescription. In Section [5](#sec:grainsizes) we discuss grain growth and the fragmentation threshold. In Section [6](#sec:discparams) we discuss our disc parameter setup and in Section [7](#sec:taurusdiscresults) we apply our disc models to discs comparable to those in the Taurus star-forming region, presenting observational predictions for observing self-gravitating discs at distance $\sim140$ pc. In Section [8](#sec:dsharp) we apply our models to three discs from the DSHARP survey, analysing whether or not their observed substructure may be the result of self-gravity. In Section [9](#sec:discussion) we discuss and draw conclusions.

# Disc Models: Setup

We setup our discs using the 1D models introduced by (cite: clarkeetal09) (cite: ricearmitage09; forganrice2013) and further developed by (cite: halletal16) to include 3D structure such as the spiral density waves characteristic of self-gravitating discs. These models are described in detail in (cite: halletal16) and summarised in Section [2.1](#sec:sgdiscmodels). We refer the reader to (cite: halletal16) for a comparison of this simple functional formailsm’s ability to accurately reproduce self-gravitating spiral shape and amplitudes from SPH simulations. Dust grain enhancement is imposed semi-analytically, in line with what we might expect from spiral density structure in self-gravitating discs, and is described in Section [2.2](#sec:dustconc).

## Self-gravitating Disc Models

We expect an accretion disc to settle into a quasi-steady state (cite: paczynski78; gammie01; ricearmitage09) with a constant mass accretion rate, $\dot{M}$, given by (cite: pringle81), $$\begin{equation}
\label{eq:mdot}
    \dot{M} = \frac{3\pi\alpha c_s^2\Sigma}{\Omega} = \rm constant,
\end{equation}$$ where $c_s$ is the local sound speed, $\Sigma$ is the disc surface density, $\alpha$ is the dimensionless viscosity parameter (cite: shakurasunyaev73), and $\Omega$ is the Keplerian angular frequency. Strictly speaking, a self-gravitating disc is not actually viscous, but the stresses can still be represented by an effective viscous-$\alpha$ parameter (cite: balbus99; gammie01; lodato04). Assuming local angular momentum transport, and that the disc is in thermal equilibrium, this can be expressed as (cite: gammie01), $$\begin{equation}
\label{eq:alpha}
    \alpha = \frac{4}{9\gamma(\gamma - 1)t_{\rm cool}\Omega},
\end{equation}$$ where $\gamma$ is the ratio of specific heats and $t_{\rm cool}$ is the local cooling timescale.

Cooling is modelled in terms of a local cooling rate, $\Lambda$. In the presence of external irradiation that we express as a temperature, $T_{\rm irr}$, the local cooling rate can be expressed as (cite: hubney90), $$\begin{equation}
\label{eq:lambda}
    \Lambda = \frac{8\sigma(T^4 - T_{\rm irr}^4)}{3\tau},
\end{equation}$$ where $\sigma$ is the Stefan-Boltzmann constant, $T$ is the midplane disc temperature and $\tau$ represents the optical depth. For all the models considered here we assume that irradiation leads to a constant background temperature, $T_{\rm irr}=10$ K. The local cooling timescale is then the thermal energy per unit area divided by this cooling rate, which we can write as, $$\begin{equation}
\label{eq:tcool}
    t_{\rm cool} = \frac{1}{\Lambda}\frac{c_s^2 \Sigma}{\gamma(\gamma -1)}.
\end{equation}$$

Disc instability is characterised by the Toomre $Q$ parameter (cite: toomre64) where a disc will be susceptible to non-axisymmetric perurbations when $Q < 1.5-1.7$ (cite: durisenetal07). Here we assume the disc to be marginally unstable with $Q=2$ at all radii. We can then use equations [\[eq:Q\]](#eq:Q), [\[eq:mdot\]](#eq:mdot), [\[eq:alpha\]](#eq:alpha) and [\[eq:tcool\]](#eq:tcool) to self-consistently determine values for $\alpha$, $\Sigma$ and $c_s$. This then allows for calculation of the local scale height, $H = c_s/\Omega$, and the midplane volume density, $\rho = \Sigma/2H$. Values for $T$, $\gamma$ and the local optical depth, $\tau = \Sigma\kappa(\rho,c_s)$, are determined from $\rho$ and $c_s$ using the equation of state from (cite: stamatellosetal07). Temperature and surface density profiles are thus determined self-consistently in these discs, as for any given $\dot{M}$ and disc size there is only one possible combination of $T$ and $\Sigma$ that will satisfy equations [\[eq:mdot\]](#eq:mdot)$-$[\[eq:tcool\]](#eq:tcool). In this way we are able to construct 3D axisymmetric discs for any desired $\dot{M}$ and disc size.

We then impose spiral density structure as described in (cite: halletal16). This is done by assuming logarithmic spirals with azimuthal position, $$\begin{equation}
\label{eq:spiraltheta}
    \theta_{\rm spiral} = \frac{1}{b} {\rm log}\Big(\frac{r}{a}\Big),
\end{equation}$$ where $a$ and $b$ are constants defining the shape of the spirals. Here we use $a=13.5$ and $b=0.38$, in line with that used in (cite: halletal16).

At each azimuthal location in the disc, $\theta_{\rm x,y}$, we calculate a fractional over-density, $\delta\Sigma/\Sigma$, characterised by a spiral amplification factor, $S$, such that (cite: cossinslodatoclarke), $$\begin{equation}
\label{eq:dsigma/sigma}
    \frac{\langle\delta\Sigma\rangle}{\langle\Sigma\rangle} = S\alpha^{1/2},
\end{equation}$$ where here we define $S=2$, and $\alpha$ is the effective viscous alpha from Equation [\[eq:alpha\]](#eq:alpha) which is determined self-consistently.

This fractional over-density is imposed sinusoidally at each azimuthal location in the disc, $\theta_{\rm x,y}$ such that, $$\begin{equation}
\label{eq:dsigmamax}
    \delta\Sigma(\phi)=\langle\delta\Sigma\rangle {\rm cos}(m\phi).
\end{equation}$$ Here, $m$ is the azimuthal wavenumber (i.e. the number of spiral arms) and $\phi$ is the phase difference between the location of the spiral arms and each azimuthal position in the disc, $$\begin{equation}
    \phi=\theta_{\rm spiral} - \theta_{\rm x,y}.
\end{equation}$$ We expect that the azimuthal wavenumber will be roughly related to the disc-to-star mass ratio, $q$, as (cite: cossinslodatoclarke; dongetal15), $$\begin{equation}
\label{eq:namrs}
    m \approx 1/q. 
\end{equation}$$ We use this in equation [\[eq:dsigmamax\]](#eq:dsigmamax) to impose an azimuthal wavenumber in a disc of mass-ratio, $q$, assuming a symmetrical response (with $m=2,4,8...$) and rounding $m$ to the nearest appropriate value.

Finally, we model the vertical density profile of the disc as (cite: spitzer42), $$\begin{equation}
    \rho(z)=\rho_0\Bigg[\frac{1}{{\rm cosh}^2\Big(\frac{z}{H_{\rm sg}}\Big)}\Bigg],
\end{equation}$$ where $H_{\rm sg}$ is the self-gravitating scale height given as, $$\begin{equation}
    H_{\rm sg}=\frac{c_s^2}{\pi G\Sigma}.
\end{equation}$$

## Grain Concentration

In the presence of spiral density waves, dust grains will radially migrate and concentrate at their density maxima (cite: riceetal04). The extent of this radial migration will be strongly dependent on grain size, $a$. Small grains of $\sim \rm \mu m$ scale will be strongly coupled to the gas in the disc, will experience very little radial drift and will closely trace the gas distribution. The largest particles of $\sim \rm m$ scale will be decoupled and will be unaffected by the disc gas pressure, therefore orbiting with approximately Keplerian velocities.

For intermediate-sized dust grains of $\sim {\rm mm-cm}$ scale, the impact of the gas drag will be significant. Radial drift velocities will be large and, hence, grain concentration at spiral pressure maxima will be high. The gas-dust coupling is characterised by the Stokes number, $$\begin{equation}
    {\rm St}=\frac{a\rho_{\rm s}\Omega}{\rho c_{\rm s}},
\end{equation}$$ where $\rho_{\rm s}$ is the internal density of the dust grains and $\rho$ is the local gas density.

The solution of the momentum equation suggests that the radial drift velocity has a $1/({\rm St} + {\rm St^{-1}})$ relation (cite: weidenschilling77). We therefore propose a grain enhancement factor of the form, $$\begin{equation}
\label{eq:epsilon}
    \eta_i = 1 + \frac{2d}{{\rm St}_i + {\rm St}_i^{-1}} - \frac{{\rm St}_i}{200},
\end{equation}$$ where $d$ is a constant, to be determined later, that represents the peak dust concentration factor in spirals. Here, $\eta_i$ is defined as the local grain enhancement factor relative to the mean dust-to-gas ratio in the disc for the $i$th grain size. The local dust surface density for the $i$th grain size, $\Sigma_{{\rm d},i}$, will then be enhanced as, $$\begin{equation}
    \Sigma_{{\rm d},i} = \langle\epsilon_i\rangle(\Sigma_0 + \eta_i\delta\Sigma),
\end{equation}$$ where $\langle\epsilon_i\rangle$ is the average dust-to-gas ratio for each grain size in the disc. Here we use the canonical value of $\langle\epsilon\rangle=0.01$ to represent the total dust-to-gas ratio over all grain sizes.

Particles with ${\rm St}_i \ll 1$ will be strongly coupled to the gas, experience minimal radial drift and will therefore have $\eta_i \approx 1$. The dust surface density will exactly trace the gas distribution in this case, with $\Sigma_{{\rm d},i} = \langle\epsilon_i\rangle(\Sigma_0 + \delta\Sigma)$. Large solids with ${\rm St}_i \gg 1$ will be entirely decoupled from the gas and will have constant surface density across the disc, with $\eta_i \approx 0$ and $\Sigma_{{\rm d},i} = \langle\epsilon_i\rangle\Sigma_0$. Note that we set a lower limit of $\eta_i = 0$ here. Intermediate sized grains with ${\rm St}_i \approx 1$ will generate peak enhancement factors of $\eta_i \approx 1 + d$, and therefore dust surface densities, $\Sigma_{{\rm d},i} = \langle\epsilon_i\rangle(\Sigma_0 + (1 + d)\delta\Sigma)$.

In Equation [\[eq:dsigmamax\]](#eq:dsigmamax), regions coincident with the spiral peaks, where $m\phi = 0^{\circ}$, will experience maximum enhancement by a factor $\Sigma_0 + \eta_i\langle\delta\Sigma\rangle$, as $\delta\Sigma = \langle\delta\Sigma\rangle$ in these regions. Dust surface density in inter-arm regions, where $m\phi=180^{\circ}$, will equally be depleted by a factor $\Sigma_0 - \eta_i\langle\delta\Sigma\rangle$, as $\delta\Sigma = -\langle\delta\Sigma\rangle$ here.

To avoid $\Sigma_{{\rm d},i}$ becoming negative in inter-arm regions, we employ a correction factor, $$\begin{equation}
  \Sigma_{{\rm d},i,{\rm corr}} = 
  \begin{cases}
      \eta_i\langle\delta\Sigma\rangle - \Sigma_0, & \text{if } \Sigma_0 + \eta_i\delta\Sigma < 0 \\
      0, & \text{otherwise}.
    \end{cases} 
\end{equation}$$ Thus our resultant dust surface density becomes, $$\begin{equation}
    \Sigma_{{\rm d},i} = \frac{\langle\epsilon_i\rangle(\Sigma_0 + \eta_i\delta\Sigma + \Sigma_{{\rm d},i,{\rm corr}})\Sigma_0}{\Sigma_0 + \Sigma_{{\rm d},i,{\rm corr}}}.
\end{equation}$$

This ensures $\Sigma_{\rm d} > 0$ by increasing our dust distribution by a factor $\Sigma_{\rm d,i,corr}$ in cases where $\Sigma_0 + \eta_i\delta\Sigma < 0$. The denominator is a normalisation which ensures our mean dust surface density remains unchanged by $\Sigma_{\rm d,i,corr}$, thus ensuring mass conservation.

## Monte Carlo Radiative Transfer: TORUS

Our disc is constructed within a mesh of grid cells, where initially we begin with a parent cell centred on the disc centre. We repeatedly subdivide parent cells into $2^D$ child cells based on some mass resolution criteria, where $D$ is the dimensions of our domain (3 dimensional here). If the mass in a cell exceeds $1\times 10^{-4}$ M$_{\odot}$ then we further subdivide each cell into $2^D$ child cells such that child cells then become parent cells. This continues until the mass in each cell is less than or equal to our mass resolution criteria.

The dust temperatures are then calculated using the TORUS radiation transfer code (cite: harriesetal19). Radiative equilibrium is calculated using the Monte Carlo technique originally described in (cite: lucy99). Our discs are illuminated by a central star, whose radiation field is here represented by $10^9$ photon packets. These photon packets are emitted from the star isotropically and proceed to undergo a random walk through the grid, experiencing both absorption and scattering, until they escape the computational domain and the dust temperatures can be calculated assuming radiative equilibrium. Another cycle of $10^9$ photon packets are then emitted, now with these updated temperatures, until the dust temperatures are found to converge and continuum images can be produced.

# ALMA Simulations: CASA

The output continuum images from TORUS are then used as inputs to the ALMA simulator in the Common Astronomy Software Application (CASA) package (version 5.1) (cite: casa) to produce realistic synthetic ALMA images from our disc models. We use ALMA cycle 7 array configurations to produce these images, exploring various array sizes and resolutions in order to find optimal configurations for each observing frequency.

We apply unsharp image masking (cite: malin77) to generate residual images from our synthetic observations by subtracting a smoothed radial profile of the image flux from itself. This technique highlights any non-axisymmetric features in our images, specifically spiral arms, by reducing the image flux range without reducing its dynamical range. We subtract a 2D Gaussian profile of FWHM closely matched to the beam size of our simulated images (we use 0.05"x0.05" here), and scaled with the peak image flux.

![](discinit.png)

![](multi.pdf)

![](grainconc.pdf)

# SPH Models: Determining Peak Grain Enhancement

Our semi-analytic prescription of dust trapping in Equation [\[eq:epsilon\]](#eq:epsilon) requires that we determine the expected peak dust concentration factor, $d$, in disc spiral arms. To do this we employ the 3D SPH code PHANTOM (cite: priceetal18) to numerically model the behaviour of dust particles in self-gravitating discs.

We set up three sets of discs with mass ratios $q=0.2$, $0.3$ and $0.4$ around a central star of mass $M_*=1$ M$_{\odot}$. Each disc has initial inner and outer radii $R_{\rm in} = 1$ AU and $R_{\rm out}=100$ AU, and are set up with initial surface density profiles $\Sigma \propto R^{-1.5}$ and initial temperature profiles $T \propto R^{-0.5}$. We use artificial viscosity terms $\alpha_{\rm SPH}=0.1$ and $\beta_{\rm SPH}=0.2$. Cooling is modelled using the radiative transfer method introduced in (cite: stamatellosetal07).

We use 500,000 SPH particles to represent the disc gas and we initially evolve the discs for 5 outer orbital periods with the gas only. We then inject a population of 125,000 dust SPH particles and allow the discs to evolve for a further orbital period. The final states of the gas-only discs are shown in Figure [1](#fig:discinit). For each set of discs we run 20 separate simulations for 20 different grain sizes distributed log-normally between $0.1$ ${\rm \mu m}$ and $200$ cm. To minimise computational expense, we neglect the self-gravity of these dust particles and treat them as test particles only.

Dust-gas mixtures are modelled using two evolution models; the two-fluid method where the dust and gas are represented by two distinct particle populations coupled by a drag term (cite: laibeprice12a; laibeprice12b), and the one-fluid method where the mixture is represented by gas particles only and the grain fraction is evolved along with the gas density for each particle (cite: pricelaibe15). The one-fluid method is implemented for smaller particle sizes at which the terminal velocity approximation is valid (cite: youdingoodman05), thus it is not appropriate for modelling larger grains. We find an appropriate grain size boundary at which to switch between these two methods at $a\approx2$ mm, therefore modelling all discs with $a \leq 2$ mm using the one-fluid method, and discs with $a > 2$ mm using the two-fluid method.

After evolving the dusty discs for a further orbital period, peak dust-to-gas ratios are determined by taking a radial slice of the disc, of azimuthal width $5^\circ$, and fitting a Gaussian distribution to the dust mass fraction at the spiral location. A demonstration of this is shown in Figure [2](#fig:sphgrainconcdemo); we fit curves to a radial slice of the $q=0.4$ disc, where the spiral is located at $\approx60-70$ AU. In Figure [3](#fig:grainconc) we fit log-normal curves to the best-fit dust-to-gas ratio peaks from the $q=0.3$ and $q=0.4$ discs. We exclude the $q=0.2$ disc from the remainder of this analysis as only weak spiral structure develops, therefore we observe only moderate grain enhancement.

Grain enhancement generally increases with increasing disc mass, primarily due to stronger spiral structure as we increase the disc-to-star mass ratio. This results in larger density gradients, greater radial drift velocities, and stronger concentration of grains. It is possible that grain concentration may continue to increase with increasing disc mass above $q=0.4$. However, for mass ratios $q \gtrsim 0.5$ discs become susceptible to fragmentation for the stellar mass considered here. This will act to disrupt any spiral arm structure thus limiting grain concentration. We therefore only model disc masses up to $q=0.4$.

Grains become most concentrated for sizes $a\approx200-500$ mm, with peak dust-to-gas ratios $\epsilon\approx0.06$ and $\epsilon\approx0.07$ in the $q=0.3$ and $q=0.4$ discs respectively, giving values of $d\approx5$ and $d\approx6$ for equation [\[eq:epsilon\]](#eq:epsilon). For the discs generated in Section [6](#sec:discparams), with disc masses $q \lesssim 0.3$, we assume a maximum value of $d=5$ in our models.

# Grain Growth and the Fragmentation Threshold

Appropriate grain size distributions for the equations in Section [2](#sec:discmodel) can be obtained using models of grain growth in protoplanetary discs. Grain growth proceeds through steady coagulation and accumulation during grain-grain collisions (cite: testi14). The tendency for grains to stick together and grow during these collisions will depend on their collisional velocities. Particles with ${\rm St}<1$ (i.e. smaller grains) have smaller relative azimuthal velocities, hence when they collide they will likely coalesce in a so-called *hit-and-stick* process (cite: chokshietal93; dominiktielens97).

Larger particles will have higher relative azimuthal velocities, reaching a constant maximum value for ${\rm St}\geq 1$. (cite: kotheetal13) find a power-law mass dependence for the affinity of solids, $v_{\rm th}\propto m^{-3/4}$, with less massive solids having a greater threshold velocity for sticking. As particles grow, their impact velocities will increase accordingly and collisions will result in particles either bouncing off each other, compacting their densities in the process (cite: guttleratal10; zsometal10), or shattering into several smaller fragments. These two growth barriers, known as the *bouncing barrier* and the *fragmentation threshold* respectively, may consequently limit the maximum size to which grains are able to grow through collisional accumulation, therefore limiting our value of $a_{\rm max}$.

The particle size at which the bouncing barrier is reached will depend on a number of factors such as particle porosity, density and material, and is therefore non-trivial to calculate analytically. Instead, we reason that the wealth of smaller, micron-sized solids dominating the dust-mass budget in discs (cite: williams11) requires regular replenishment through a cycle of growth and fragmentation, as otherwise these smaller grain sizes would quickly be depleted as they grow (cite: dullemondetal08; braueretal08; birnstielatal11). This indicates that particles are able to grow to at least as large as the fragmentation threshold, and we therefore use this to define $a_{\rm max}$ in our models.

The fragmentation threshold velocity, $v_{\rm frag}$, is the maximum relative velocity that particles can withstand before collisions result in shattering. Relative azimuthal velocities scale with Stokes number, and for large Stokes’ numbers particle’s relative velocities will be dominated by turbulence. We can therefore calculate a maximum, threshold Stokes number for particles as (cite: birnstieletal10; birnstieletal12), $$\begin{equation}
    {\rm St_{max}} \propto \frac{v_{\rm frag}^2}{\alpha c_{\rm s}^2},
\end{equation}$$ giving a maximum grain size of (cite: dipierro15), $$\begin{equation}
\label{eq:afrag}
    a_{\rm max} = \frac{4\langle\Sigma_{\rm g}\rangle}{3\pi\alpha\rho_{\rm s}}\frac{v_{\rm frag}^2}{\langle c_{\rm s}\rangle^2},
\end{equation}$$ where we use the azimuthally averaged gas surface density, $\langle\Sigma_{\rm g}\rangle$, and sound speed, $\langle c_{\rm s}\rangle$, as spiral features are short lived and grain growth timescales typically exceed these. We can estimate the viscous$-\alpha$ here by assuming that in a quasi-steady, self-gravitating disc dominated by turbulent motion, the viscous stress will saturate at a maximum value $\alpha=0.06$ (cite: riceetal05), therefore defining the limiting maximum grain size.

We use this to set our value of $a_{\rm max}$ in our disc models assuming two cases of $v_{\rm frag}=10$ ms$^{-1}$ and $v_{\rm frag}=30$ ms$^{-1}$. The mid-plane distributions of $a_{\rm frag}$ are plotted in Figures [4](#fig:afrag10) and [5](#fig:afrag30) for discs of outer radius, $R_{\rm out}=100$ AU, and mass accretion rates ranging from $\dot{\rm M}=1 \times 10^{-8}$ M${_{\odot}}$ yr$^{-1}$ to $\dot{\rm M} = 1 \times 10^{-6}$ M${_{\odot}}$ yr$^{-1}$.

![](afrag10ms.png)

![](afrag30ms.png)

The fragmentation threshold decreases with increasing $\dot{\rm M}$ (i.e. with increasing disc mass), and becomes smallest in the outer disc where $a_{\rm frag}$ is comparable for all disc masses. In the most massive discs when $v_{\rm frag}=10$ ms$^{-1}$, grains can only grow to $\sim$ mm sizes before collisions become destructive, with this maximum grain size in the inner disc decreasing by a factor of $\sim 5$ as we increase the disc mass from $q=0.1$ to $q=0.31$. For the higher threshold of $v_{\rm frag}=30$ ms$^{-1}$ the value of $a_{\rm frag}$ increases by a factor $v_{\rm frag}^2$ for all disc masses (a factor 9), and grains can grow to $a_{\rm max}\sim$ cm sizes here.

# Disc Models: Parameters

With the additional information from Sections [4](#sec:sphdust) and [5](#sec:grainsizes), it is now possible to use our models to efficiently predict for which disc parameters we expect self-gravitating disc substructure to be observable with ALMA. We setup discs as described in Section [2](#sec:discmodel) exploring a range of parameter space in disc masses, grain sizes and observing frequencies.

Our central star is modelled with $M_{*}=1$ M$_{\odot}$, $R_{*}=2.325$ R$_{\odot}$ and $T_{\rm eff}=4350$ K. We assume a canonical dust-to-gas ratio of 0.01, and represent our grains as (cite: drainelee) silicates with size distribution, $$\begin{equation}
    n(a) \propto a^{-q},
\end{equation}$$ distributed between minimum and maximum grain sizes $a_{\rm min}$ and $a_{\rm max}$, and assume $q=q_{\rm ism}=3.5$ (cite: mathisetal77). We set here $a_{\rm min}=0.1$ $\mu$m and vary the value of $a_{\rm max}$ to represent different stages of grain growth, using values $a_{\rm max}=10$ ${\rm \mu}$m (minimal grain growth), $1$ mm, $10$ cm, $100$ cm, $a_{\rm frag, 10ms^{-1}}$ and $a_{\rm frag, 30ms^{-1}}$ (the grain fragmentation thresholds as described in Section [5](#sec:grainsizes)). We use 50 dust grain sizes distributed logarithmically between $0.1$ $\mu$m and $2\times10^{6}$ ${\rm \mu}$m, and set the grain fraction for any grain size greater than $a_{\rm max}$ in each case to be zero.

We generate discs with 9 different mass accretion rates (equation [\[eq:mdot\]](#eq:mdot)), where an increase in $\dot{M}$ roughly corresponds to an increase in disc mass. We use values of $\dot{M} = [1\times10^{-6}, 5\times10^{-7},2.81\times10^{-7},1.58\times10^{-7},1\times10^{-7},5\times10^{-8},2.81\times10^{-8},1.58\times10^{-8},1\times10^{-8}]$ M$_{\odot}$yr$^{-1}$, which correspond to disc-to-star mass ratios, $q \approx 0.31,0.25,0.22,0.19,0.16,0.14,0.12,0.11$ and $0.10$ respectively. Using the relation between mass ratio and the number of spiral modes in equation [\[eq:namrs\]](#eq:namrs), and assuming a symmetrical response where we have an even number of modes, each of these discs are set up with $m=4$ and $m=8$ for the more massive and less massive cases respectively. A summary of these disc setups is laid out in Table [1](#tab:discsetup).

+:----------------------:+:------------------:+:-----:+
| $\dot{M}$\             | $M_{\rm disc}/M_*$ | $m$   |
| (M$_{\odot}$yr$^{-1}$) |                    |       |
+------------------------+--------------------+-------+
| \(1\)                  | \(2\)              | \(3\) |
+------------------------+--------------------+-------+
| $1\times10^{-6}$       | 0.31               | 4     |
+------------------------+--------------------+-------+
| $5\times10^{-7}$       | 0.25               | 4     |
+------------------------+--------------------+-------+
| $2.81\times10^{-7}$    | 0.22               | 4     |
+------------------------+--------------------+-------+
| $1.58\times10^{-7}$    | 0.19               | 4     |
+------------------------+--------------------+-------+
| $1\times10^{-7}$       | 0.16               | 8     |
+------------------------+--------------------+-------+
| $5\times10^{-8}$       | 0.14               | 8     |
+------------------------+--------------------+-------+
| $2.81\times10^{-8}$    | 0.12               | 8     |
+------------------------+--------------------+-------+
| $1.58\times10^{-8}$    | 0.11               | 8     |
+------------------------+--------------------+-------+
| $1\times10^{-8}$       | 0.10               | 8     |
+------------------------+--------------------+-------+

: (1) Mass accretion rates used for the discs setup in Section [6](#sec:discparams) and analysed in Section [7](#sec:taurusdiscresults). (2) Calculated disc-to-star mass ratios. (3) Number of input spiral modes for each disc.

Continuum images of these discs are generated for observing frequencies $115$ GHz (${\rm \lambda=2.6}$ mm), $230$ GHz (${\rm \lambda=1.3}$ mm) and $690$ GHz (${\rm \lambda=0.4}$ mm), corresponding to ALMA observing bands 3, 6 and 9 respectively. We consider discs at a distance of 140pc, comparable to those in the Taurus star forming region. Example TORUS output images produced in this way are shown in Figure [6](#fig:ds9discs) for discs with $a_{\rm max}=1$ mm and accretion rates from Table [1](#tab:discsetup).

We then use these continuum disc images as inputs to the CASA tasks SIMOBSERVE and SIMANALYZE and generate synthetic ALMA observations. Observing times, antenna configurations and PWV values used as inputs to CASA are laid out in Table [2](#tab:casa). Unsharp image masking is applied to these synthetic observations in order to highlight any non-axisymmetric disc features present, as described in Section [3](#sec:casa). We demonstrate the process of generating synthetic ALMA observations and then unsharp masked residual images from TORUS continuum profiles in Figure [7](#fig:casademo).

|               |               |                |           |
|:-------------:|:-------------:|:--------------:|:---------:|
| $f_{\rm obs}$ | $t_{\rm obs}$ | Antenna Config | PWV Level |
|     \(1\)     |     \(2\)     |     \(3\)      |   \(4\)   |
|               |               |                |           |
|    115 GHz    |    1800 s     | alma.cycle7.8  | 5.186 mm  |
|               |               |                |           |
|    230 GHz    |    1800 s     | alma.cycle7.8  | 1.796 mm  |
|               |               |                |           |
|    690 GHz    |    1800 s     | alma.cycle7.6  | 0.472 mm  |
|               |               |                |           |

: Input parameters used here for generating synthetic images with CASA. (1) ALMA observing frequency. (2) Simulated observing time. (3) ALMA antenna configuration used. (4) Precipitable Water Vapour (PWV) level.

|  |  |  |
|:--:|:--:|:--:|
| ![image](230GHz_1E-6_ds9_text.png) | ![image](230GHz_5E-7_ds9_text.png) | ![image](230GHz_281E-7_ds9_text.png) |
| ![image](230GHz_158E-7_ds9_text.png) | ![image](230GHz_1E-7_ds9_text.png) | ![image](230GHz_5E-8_ds9_text.png) |
| ![image](230GHz_281E-8_ds9_text.png) | ![image](230GHz_158E-8_ds9_text.png) | ![image](230GHz_1E-8_ds9_text.png) |

![image](5E-7_amax1mm_image115GHz_cbar.png) ![image](5E-7_amax1mm_finalimage115GHz_cbar.png)

# Disc Models: Results

Our focus here is to analyse the parameter space in which self-gravitating disc structure may be observable with ALMA. We present our results in this section considering the effects of varying disc mass, grain size distribution and observing frequency on our ability to distinguish spiral structure in our disc model. Galleries of unsharp masked synthetic disc images where we explore this parameter space can be found in Appendix [10](#appendix:gallery).

## Analysing the impact of grain enhancement

We begin this section by first demonstrating the impact of grain enhacement on observability. We showed in Section [4](#sec:sphdust) that dust trapping of $\sim$cm sized grains significantly enhances dust-to-gas ratios in spiral arm regions, therefore equally acting to remove dust from interarm regions. Spiral structure consequently becomes sharper and more distinct, producing higher flux ratios between arm and interarm regions due to enhanced and depleted emission at these locations respectively.

We illustrate our grain enhancement prescription in Figure [8](#fig:grainsizedist) by plotting how dust-to-gas ratio varies across our disc model for grains with sizes of $a=10$ ${\rm \mu}$m, $1$ mm and $10$ cm, in a disc with $\dot{M}=1\times10^{-6}$ M$_{\odot}$yr$^{-1}$, $R_{\rm out}=100$ AU and grain size distribution $n(a) \propto a^{-3.5}$ with $a_{\rm min}=0.1\mu$m and $a_{\rm max}=100$ cm. Grains of $a=10{\rm \mu}$m with ${\rm St} \ll 1$ exactly trace the gas distribution and display an entirely uniform dust-to-gas ratio across the disc. The Stokes number, and therefore also grain concentration factor, $\eta$, scales with grain size up to ${\rm St}=1$. As we consider larger grain sizes up to $a=10$ cm, grains become enhanced in the spirals arms and clear non-axisymmetric dust-to-gas ratios start to emerge.

![image](grainfrac10um.png) ![image](grainfrac1mm.png) ![image](grainfrac10cm.png)

![image](fluxvsq_115GHz_SA_runs.pdf) ![image](fluxvsq_230GHz_SA_runs.pdf) ![image](fluxvsq_690GHz_SA_runs.pdf)

![image](fluxvsq_115GHz_SA_runs_nodustconc.pdf) ![image](fluxvsq_230GHz_SA_runs_nodustconc.pdf) ![image](fluxvsq_690GHz_SA_runs_nodustconc.pdf)

It is useful here to quantify observability of spiral structure in terms of the ratio of the RMS fluxes in the disc arm and interarm regions (i.e. $F_{\rm RMS,arm} /F_{\rm RMS,iarm}$). Arm and interarm regions in our resultant disc images can be located using equation [\[eq:spiraltheta\]](#eq:spiraltheta), and we calculate the RMS fluxes between radii $70-100$ AU where we find spiral structure to be most prominent. In Figure [9](#fig:fluxvs.q) we plot how these flux ratios vary with mass accretion rate, and show comparison plots for models that do not include dust grain enhancement in Figure [10](#fig:fluxvs.q-noconc). Flux ratios are calculated using the synthetic ALMA observations prior to unsharp masking. Example like-for-like unsharp masked disc images are also included for reference in Figure [11](#fig:concvs.noconc).

For the same disc parameters we calculate considerably higher flux ratios when including dust trapping in our model, most notably when the dust mass budget is dominated by millimetre/centimetre grains (i.e. when $a_{\rm max}=$ mm$-$cm sizes). Previously blurred arm and interarm regions become distinct as millimetre emission is concentrated in the spiral peaks. The key implication here is that with grain enhancement generating stronger spiral structure for the same mass discs, we should expect to detect self-gravitating disc structure for lower disc masses than previously predicted, if sufficient grain growth has occurred. In discs with no grain growth, or in which grains have grown well beyond centimetre sizes, the lack of dust mass in millimetre/centimetre aggregates becomes detrimental to the observability of disc substructure.

Given the short potential lifetime of a disc’s self-gravitating phase its important to note how fast grains can actually grow, and thus what likely maximum grain size would be present in young, self-gravitating discs. Models of grain growth predict that millimetre and centimetre-sized grains form rapidly on timescales $\lesssim10^5$ yrs (cite: dullemondetal05; laibetal08). It therefore seems reasonable to expect grains to have grown to at least as large as the fragmentation threshold before the end of a disc’s self-gravitating phase, and that enhanced emission in spiral regions from these larger grains may be significant.

![image](1E-6_amaxfrag30_115GHz_nodustconc.png) ![image](1E-6_amaxfrag30_115GHz.png) ![image](cbar_115GHz.png) ![image](1E-6_amaxfrag30_230GHz_nodustconc.png) ![image](1E-6_amaxfrag30_230GHz.png) ![image](cbar_230GHz.png) ![image](1E-6_amaxfrag30_690GHz_nodustconc.png) ![image](1E-6_amaxfrag30_690GHz.png) ![image](cbar_690GHz.png)

Multi-wavelength observations of discs allow us to probe grain growth and dust trapping through calculation of the disc opacity spectral index, $\beta$ (cite: dipierro15). In the Rayleigh-Jeans limit of an optically thin disc the dust opacity at sub-mm wavelengths will approximately scale as $\kappa \propto \nu^\beta$, where for interstellar dust grains $\beta_{\rm ism}\approx1.7$. Observations of discs show $\beta_{\rm disc} < \beta_{\rm ism}$ (cite: testietal03; riccietal10) which can be naturally accounted for by the presence of larger grains in the disc and therefore grain growth (cite: draine06). In Figure [12](#fig:beta10cm) we calculate the $\beta$-parameter from our synthetic ALMA observations, considering fluxes $\nu_1=460$ GHz and $\nu_2=100$ GHz, and discs with $\dot{M}=5\times10^{-7}$ M$_{\odot}$yr$^{-1}$ and $a_{\rm max}=1$ mm and $10$ cm. The pixelwise $\beta$ can be calculated as, $$\begin{equation}
\label{eq:beta}
    \beta = \frac{{\rm ln}F_1 - {\rm ln}F_2}{{\rm ln}\nu_1 - {\rm ln}\nu_2} - 2,
\end{equation}$$ where $F_1$ and $F_2$ are the pixelwise fluxes at frequencies $\nu_1$ and $\nu_2$ respectively. Spiral regions display the lowest $\beta$ values due to dust trapping of larger grains, whilst depletion of these same grains in inter-spiral regions produces comparatively higher $\beta$ values. Inner disc regions are optically thick and consequently also display low $\beta$ values. We calculate mean $\beta$-values 1.197 and 0.525 for $a_{\rm max}=1$ mm and $a_{\rm max}=10$ cm respectively, where the higher $\beta$ value is consequence of less grain growth in the $a_{\rm max}=1$ mm disc. Note that both of these discs display $\beta_{\rm disc} < \beta_{\rm ism}$.

Through calculation of the $\beta-$parameter in our disc model we therefore demonstrate how it is possible to retrieve information about the underlying grain distribution in discs, and how our model may be used to probe grain properties in discs which have been observed at multiple wavelengths.

![image](beta_5E-7_amax1mm.pdf) ![image](beta_5E-7_amax10cm.pdf)

## Observing self-gravitating discs in Taurus

We now wish to make observational predictions of self-gravitating discs, considering those at a distance $d\sim140$ pc comparable to the Taurus star-forming region. We setup a suite of discs as described in Section [6](#sec:discparams) and refer the reader to the unsharp masked disc images presented in Appendix [10](#appendix:gallery) for this discussion.

Spiral amplitude in our models increases as $\delta\Sigma/\Sigma \propto \alpha^{-1/2}$ (equation [\[eq:dsigma/sigma\]](#eq:dsigma/sigma)), hence is an increasing function of accretion rate (see equation [\[eq:mdot\]](#eq:mdot)). This is illustrated in Figure [13](#fig:discsvs.mdot) for discs with $a_{\rm max}=1$ mm observed at $f_{\rm obs}=115$ GHz. Low $\dot{M}$ discs generally exhibit no observable substructure for any grain size distribution, whilst the most massive discs tend to be capable of generating detectable spirals at all frequencies considered here. This does however depend on how much grain growth has occurred, as we require that the dust mass budget is dominated by millimetre/centimetre grains ($a_{\rm max}=\rm mm-cm$ sizes) if we are to resolve any spirals.

![image](5E-8_amax1mm_115GHz.png) ![image](158E-7_amax1mm_115GHz.png) ![image](1E-6_amax1mm_115GHz.png) ![image](cbar_115GHz.png)

Dust emissivity peaks for $\lambda \approx 2\pi a$ (cite: armitage09), therefore emission from millimetre grains will peak at $\approx$ millimetre wavelengths. The corresponding wavelengths to the observing frequencies considered here are 2.6mm, 1.3mm and 0.4mm for frequencies of 115GHz, 230GHz and 690GHz respectively. When the dust mass budget is dominated by micron grains or metre-sized objects (i.e. $a_{\rm max}=10$ ${\rm \mu m}$ or $a_{\rm max}=100$ cm) disc substructure becomes invisible at the ALMA bands considered here as the arm-interarm contrast is low. We illustrate this in Figure [14](#fig:discvs.amax) which shows how emission from spiral regions varies with grain size distribution in discs with $\dot{M}=5\times10^{-7}$ M$_{\odot}$yr$^{-1}$ observed at $f_{\rm obs}=115$ GHz. Substructure only becomes recognisable in discs with unfavourable grain size distributions when we observe at shorter wavelengths ($f_{\rm obs}=690$ GHz, $\lambda=0.4$ mm), but only in the most highly accreting cases.

![image](5E-7_amax10um_115GHz.png) ![image](5E-7_amax1mm_115GHz.png) ![image](5E-7_amax10cm_115GHz.png) ![image](5E-7_amax100cm_115GHz.png) ![image](cbar_115GHz.png)

Without including dust trapping in their model, (cite: halletal16) previously found a narrow region of parameter space within which self-gravitating discs would display spirals observable with ALMA. They predicted a $100$ AU disc must be accreting in the range $1\times10^{-7}$ M$_{\odot}$yr$^{-1} \lesssim \dot{M} \lesssim 1\times10^{-6}$ M$_{\odot}$yr$^{-1}$, where the maximum accretion rate here is set by the limit at which discs become susceptible to fragmentation. We suggest that in fact spiral emission may be distinct for lower accretion rates than previously predicted, if sufficient grain growth has occurred. The discs in Figures [20](#fig:230gallery) and [21](#fig:690gallery) observed at $230$ GHz and $690$ GHz respectively continue to display detectable spiral structure down to the lowest $\dot{M}$ considered here, as long as the dust mass budget is dominated by millimetre/centimetre grains. Note however that we are observing these discs face-on and therefore in favourable conditions for resolving spiral features. Inclining and rotating these discs may well obscure them. However, we would still expect to be able to detect spirals to lower $\dot{M}$ than previously suggested.

It is also intriguing that we calculate the fragmentation threshold to fall almost exactly coincident with the ideal $a_{\rm max}$ values for detecting spirals (see Figures [4](#fig:afrag10) and [5](#fig:afrag30)). We should therefore not be surprised if we find that in fact the grain size distributions of self-gravitating discs fall within this ideal region of parameter space.

# Analysing discs from the DSHARP sample

We now turn our model to analysing real observational data of potential self-gravitating discs. The recent DSHARP survey studied 20 nearby protoplanetary discs using ALMA, with 3 of these discs exhibiting spiral substructure (cite: dsharp1; dsharp3). The ALMA continuum images from this survey of the Elias 27, WaOph 6 and IM Lup discs are shown in Figure [15](#fig:dsharp).

We use our models to investigate if the observed substructure in these 3 systems can be explained through the gravitational instability, or if instead they require an alternative explanation.

Although well within the capability of our models, a complete examination of the potential parameter space of these discs is beyond the scope of the work presented here. Instead, we simply model these 3 systems using the disc parameters derived in (cite: dsharp1) and (cite: dsharp3), and make predictions as to whether we should expect these systems to produce self-gravitating spiral substructure observable with ALMA. The disc parameters used are laid out in Table [\[tab:dsharp\]](#tab:dsharp). We setup these discs with dust size distribution $n(a) \propto a^{-3.5}$, with $a_{\rm min}=0.1\mu$m and set $a_{\rm max}$ as the fragmentation threshold where $v_{\rm frag}=10$ ms$^{-1}$ (equation [\[eq:afrag\]](#eq:afrag)), and use the canonical dust-to-gas ratio of 0.01.

Residual images in (cite: dsharp3) are produced by deprojecting the discs and subtracting their median axisymmetric radial profiles. We do the same here by binning each disc into $1$ AU-wide radial bins and subtracting the median azimuthal fluxes. We re-derive the residual images for each of the original DSHARP observations in this way, as well as for our disc models. For each disc observation and model, we show deprojected continuum and residual images (with ${\rm PA}=0^{\circ}$ and $i=0^{\circ}$), presenting our results in Figures [16](#fig:elias), [17](#fig:waoph) and [18](#fig:imlup). In each case we provide reference colorbars for direct comparison between the fluxes of the disc models and observations, and each disc model and counterpart observation is plotted between the same flux range for ease of comparison.

Logarithmic spiral structure is imposed in each disc model using values of $a$ and $b$ (equation [\[eq:spiraltheta\]](#eq:spiraltheta)) derived by (cite: dsharp3). Best-fit values of $a$ and $b$ that we find from those quoted in (cite: dsharp3) are laid out in Table [\[tab:dsharp\]](#tab:dsharp).

We produce synthetic observations of each disc using CASA with observing setups consistent with those outlined in (cite: dsharp1). We observe each disc for $t_{\rm obs}=3600$ s using array configuration C40-8. For each observation we use PWV values at the upper bound of the quoted range in (cite: dsharp1), setting values 1.35mm, 1.30mm and 1.05mm for Elias 27, IM Lup and WaOph 6 respectively. Input parameters for CASA used for each disc are laid out in Table [3](#tab:dsharpcasa).

![image](Elias27_og.pdf) ![image](WaOph6_og.pdf) ![image](IMLup_og.pdf)

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Disc | log$M_*$ $^{[1]}$ | $R_*$ | log$T_{\rm eff}$ $^{[1]}$ | $R_{\rm spirals}$ $^{[2]}$ | log$\dot{M}$ $^{[1]}$ | d $^{[2]}$ | $i$ $^{[2]}$ | PA $^{[2]}$ | a $^{[2]}$ | b $^{[2]}$ |
|  | (M$_{\odot}$) | (AU) | \(K\) | (AU) | (M$_{\odot}$ yr$^{-1}$) | (pc) | ($^{\circ}$) | ($^{\circ}$) | (AU) |  |
|  |  |  |  |  |  |  |  |  |  |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) | \(9\) | \(10\) | \(11\) |
|  |  |  |  |  |  |  |  |  |  |  |
| Elias 27 | $-0.31^{+0.15}_{-0.11}$ | 2.3 | $3.59\pm0.03$ | 50-230 | $-7.2\pm0.5$ | 116$^{+19}_{-10}$ | 56.2 | 118.8 | 110.9 | -0.282 |
|  |  |  |  |  |  |  |  |  |  |  |
| WaOph 6 | $-0.17^{+0.17}_{-0.09}$ | 3.2 | $3.62\pm0.03$ | 25-75 | $-6.6\pm0.5$ | 123$\pm$2 | 47.3 | 174.2 | 45.9 | 0.238 |
|  |  |  |  |  |  |  |  |  |  |  |
| IM Lup | $-0.05^{+0.09}_{-0.13}$ | 2.5 | $3.63\pm0.03$ | 25-110 | $-7.9\pm0.4$ | 158$\pm$3 | 47.5 | 144.5 | 43 | -0.181 |
|  |  |  |  |  |  |  |  |  |  |  |

+:--------:+:-------------:+:-------------:+:--------:+:---------:+
| Disc     | $f_{\rm obs}$ | $t_{\rm obs}$ | Antenna\ | PWV Level |
|          |               |               | Config   |           |
+----------+---------------+---------------+----------+-----------+
|          | \(1\)         | \(2\)         | \(3\)    | \(4\)     |
+----------+---------------+---------------+----------+-----------+
|          |               |               |          |           |
+----------+---------------+---------------+----------+-----------+
| Elias 27 | 240 GHz       | 3600 s        | C40-8    | 1.35 mm   |
+----------+---------------+---------------+----------+-----------+
|          |               |               |          |           |
+----------+---------------+---------------+----------+-----------+
| WaOph 6  | 240 GHz       | 3600 s        | C40-8    | 1.30 mm   |
+----------+---------------+---------------+----------+-----------+
|          |               |               |          |           |
+----------+---------------+---------------+----------+-----------+
| IM Lup   | 240 GHz       | 3600 s        | C40-8    | 1.05 mm   |
+----------+---------------+---------------+----------+-----------+
|          |               |               |          |           |
+----------+---------------+---------------+----------+-----------+

: Input parameters used here for generating synthetic images with CASA for the modelled DSHARP discs. (1) ALMA observing frequency. (2) Simulated observing time. (3) ALMA antenna configuration used. (4) Precipitable Water Vapour (PWV) level.

## Elias 27

Elias 27 is a 0.8 Myr M0 star located in the $\rho$ Oph star forming region at a distance $d=116^{+19}_{-10}$ pc (cite: gaiaDR2; dsharp1). The residual profile of the Elias 27 continuum image (Figure [16](#fig:elias)) shows two symmetric spiral arms extending from $R_{\rm in}\sim50$ AU to $R_{\rm out}\sim230$ AU, with ${\rm PA}=118.8^{\circ}$ and $i=56.2^{\circ}$ (cite: dsharp3).

The spiral structure of Elias 27 is probably the most well-studied of the three discs here. The system has previously been modelled using both both grid-based and SPH simulations, with authors such as (cite: meruetal17), (cite: tomidaetal17) and (cite: halletal18) all finding GI to be a plausible explanation for the observed morphology. Estimates of the Toomre parameter in the disc however suggest that Elias 27 should be gravitationally stable at all radii (cite: perezetal16), but this comes with the caveat that estimates of $Q$ are subject to high levels of uncertainty. Further research where the constraints on the disc mass and temperature are improved may lead to different conclusions.

We set up our disc model with ${\rm log}M_* {\rm(M_\odot)}=-0.31$, $R_*=2.3$ AU, ${\rm log}T_{\rm eff}{\rm(K)}=3.59$ and ${\rm log}\dot{M}{\rm(M_{\odot}yr^{-1})}=-7.2$ (cite: dsharp1; dsharp3). Logarithmic spiral structure is imposed with $a=76.0$ AU and $b=-0.29$ extending from $R=50-230$ AU, where we use a mask to remove the inner $50$ AU from our observations to avoid the spirals being washed out by the brighter central region.

Our model calculates Elias 27 to have a disc mass $M_{\rm disc}=0.13$ M$_{\odot}$ inside $R_{\rm out}=230$ AU, and therefore $q=0.27$. Figure [16](#fig:elias) shows the resultant synthetic observations generated from our models, exhibiting clear self-gravitating spiral structure in both the deprojected continuum and residual images.

![image](Elias27_og_deproj.pdf) ![image](Elias27_og_deproj_residuals.pdf) ![image](Elias27_deproj.pdf) ![image](Elias27_deproj_residuals.pdf)

## WaOph 6

WaOph 6 is a 0.3 Myr K6 star located in the $\rho$ Oph star forming region at a distance $d=123\pm2$ pc (cite: gaiaDR2; dsharp1). After subtracting the axisymmetric radial profile, two compact spiral arms are revealed which extend from $R_{\rm in}\sim25$ AU to $R_{\rm out}\sim75$ AU, with ${\rm PA}=174.2^{\circ}$ and $i=47.3^{\circ}$ (cite: dsharp3).

In their analysis of the morphology of gravitationally unstable discs, (cite: dongetal15) suggest that for a disc to be gravitationally unstable it must be compact ($R\leq100$ AU) and highly accreting at a rate $\dot{M}\geq10^{-6}$ M$_{\odot}$yr$^{-1}$. WaOph 6 has the highest accretion rate and the most compact spiral structure of the 3 discs in question here, both of which are close to matching these suggested criteria.

We setup our disc model with ${\rm log}M_*{\rm(M_\odot)}=-0.17$, $R_*=3.2$ AU, ${\rm log}T_{\rm eff}{\rm(K)}=3.62$ and ${\rm log}\dot{M}{\rm(M_{\odot}yr^{-1})}=-6.6$ (cite: dsharp1; dsharp3). Logarithmic spirals are imposed with $a=34.0$ AU and $b=0.24$ extending from $R=25-75$ AU, where again we mask the inner $25$ AU of the disc images.

We calculate WaOph 6 to have a disc mass $M_{\rm disc}=0.16$ M$_{\odot}$ and therefore $q=0.24$. Our models reproduce distinct observable, self-gravitating spiral structure in both the deprojected continuum and residual images shown in Figure [17](#fig:waoph).

![image](WaOph6_og_deproj.pdf) ![image](WaOph6_og_deproj_residuals.pdf) ![image](WaOph6_deproj.pdf) ![image](WaOph6_deproj_residuals.pdf)

## IM Lup

IM Lup is a 0.5Myr K5 star in the Lupus II cloud at a distance $d=158\pm3$ pc (cite: gaiaDR2; dsharp1). Residual profiles of the IM Lup continuum images reveal two spirals extending from $R_{\rm in}\sim25$ AU to $R_{\rm out}=110$ AU, with PA$=144.5^{\circ}$ and $i=47.5^{\circ}$ (cite: dsharp3).

Previous detection of any spiral structure in the IM Lup system has been minimal, with observed substructures being classified as two concentric rings at $R\approx95$ AU and $R\approx320$ AU, and only tenuous reports of the possibility of tightly wound spirals (cite: avenhausetal18). (cite: cleevesetal16) report a massive, gravitationally stable disc with a minimum Toomre parameter $Q_{\rm min}=3.7$ at $R=70$ AU and an extended CO disc to $R=970$ AU, making IM Lup one of the largest protoplanetary discs detected to date.

We model the disc here out to $R_{\rm out}=110$ AU, consistent with the radial extent of the observed spiral structure reported in (cite: dsharp3). Our disc model is setup with ${\rm log}M_*{\rm(M_{\odot})}=-0.05$, $R_*=2.5$ AU, ${\rm log}T_{\rm eff}{\rm(K)}$ and ${\rm log}\dot{M}{\rm(M_{\odot}yr^{-1})}=-7.9$ (cite: dsharp1; dsharp3). We impose logarithmic spiral structure with $a=59.0$ AU and $b=0.18$ extending from $R=25-110$ AU.

We calculate IM Lup to have a disc mass $M_{\rm disc}=0.098$ M$_{\odot}$ and $q=0.11$ within $R=110$ AU, and therefore the lowest disc-to-star mass ratio of the three discs modelled here. The deprojected disc images in Figure [18](#fig:imlup) show tightly wound spiral structure in the continuum and residual images, with geometry and spiral fluxes closely matching those observed in the inner disc of the IM Lup system.

![image](IMLup_og_deproj.pdf) ![image](IMLup_og_deproj_residuals.pdf) ![image](IMLup_deproj.pdf) ![image](IMLup_deproj_residuals.pdf)

## Conclusions on DSHARP sample

We present the results of our semi-analytic analysis of the observed spiral structure in the Elias 27, WaOph 6 and IM Lup systems. We note again that the purpose of this simple functional formalism is not to exactly reproduce, but to approximate, the likely spiral morphologies and fluxes of the 3 systems in question, and to investigate whether systems of their quoted disc and stellar properties should be capable of generating detectable non-axisymmetric substructure when observed with ALMA. We do this by imposing logarithmic spiral structure characteristic of GI, with self-consistently calculated amplitudes and realistic grain distributions. All 3 of the models presented here produce detectable spirals of comparable structure and fluxes to their observed DSHARP counterparts, indicating that GI may be the dominant mechanism responsible for the observed substructure in these discs.

For Elias 27, WaOph 6 and IM Lup we derive disc masses $M_{\rm disc}=0.13$ M$_{\odot}, 0.16$ M$_{\odot}$ and $0.098$ M$_{\odot}$ and disc-to-star mass ratios $q=0.27, 0.24$ and $0.11$ within their respective outer radii. Common assumption is that GI requires $q\gtrsim0.5$, therefore rendering these discs too low mass to generate prominent self-gravitating structure. However it may be possible for discs to display self-gravitating spirals for much lower mass ratios than previously thought, with the critical mass ratio having a strong dependence on the host star mass and disc opacity (cite: veronesietal19; cadmanetal20; haworthetal20). We therefore should caution against discarding GI as a plausible mechanism based off this simple mass criterion alone.

It is important to note here that whilst we shouldn’t be surprised that our models accurately reproduce the spiral form of the systems considered here, as the geometry is imposed in equation [\[eq:spiraltheta\]](#eq:spiraltheta), we should be more concerned with how accurately our models are able the reproduce the spiral flux amplitudes of the observed systems, as these are determined self-consistently from the disc mass accretion rate and the viscous-$\alpha$. The self-consistently calculated spiral amplitudes in our models all generate comparable fluxes to their counterpart observations, indicating that self-gravity may be a plausible explanation to these 3 systems.

In our model we assume that some grain growth has occurred up to the fragmentation threshold. We note again here that models of grain growth generally suggest that centimeter aggregates form rapidly on timescales $\sim10^5$ yrs (cite: dullemondetal05; laibetal08), therefore given the ages of these 3 systems our assumption seems reasonable. If, however, we modelled these systems assuming no grain growth, it is likely that we would not find any signatures of GI. Therefore, if these discs are indeed gravitationally unstable, our models suggest that significant grain growth must have also occurred. Future multi-wavelength observations of these systems, and derivation of the discs’ $\beta$-parameter (equation [\[eq:beta\]](#eq:beta)), will help to establish if this is the case.

An alternative explanation for the observed spiral structure in the DSHARP discs may be the presence of a stellar or planetary-mass companion. Planet-disc gravitational interactions can generate disc perturbations, and massive companions may be capable of triggering two-armed symmetric spiral responses similar to those observed in DSHARP (cite: dongetal15b; dongetal16; baezhu2018a; baezhu2018b; dsharp4). However in order to drive the spiral modes observed, for example in the Elias 27 system, would require a wide-orbit companion of potentially tens of Jupiter masses, thus rendering any companion likely detectable at sub-mm/IR wavelengths (cite: meruetal17). To our knowledge no companion has as yet been detected in any of the 3 discs observed here. More commonly associated features of planet-disc interactions are the presence of annular substructures such as rings and planet-driven gaps. Elias 27, WaOph 6 and IM Lup all display these features, as do a total of 18 discs in the DSHARP sample (cite: dsharp2). The DSHARP collaboration report no companion detections in any of these 18 discs despite many of the observed features being suggestive of massive companions which ought to be observable at such high angular resolution. It may then be the case that either massive planets are fainter than previously thought (cite: dongetal18), or that the observed rings are driven by lower mass, fainter planets which remain invisible to the DSHARP survey. If the latter, then these lower mass companions may not be capable of driving the observed spiral structure in Elias 27, WaOph 6 and IM Lup alone, but a combination of both GI and planet-disc interactions may be a plausible scenario (cite: perezetal16).

More detailed analysis of these systems, investigating the effect of varying accretion rate, disc irradiation, the dominant spiral mode and grain size distribution will be the subject of future work.

# Summary and Conclusion

We present our updated self-consistent, semi-analytic model of self-gravitating discs that also includes a prescription for dust trapping. We capitalise on the efficient nature of the model by generating a suite of disc models at little computational expense, and examine the parameter space within which we predict self-gravitating discs will generate spiral structure that can be resolved when imaged with ALMA. Monte-Carlo radiative transfer is employed here to produce synthetic observations of these model discs, allowing us to make realistic predictions about the strength of the perturbations and the grain size distribution required to generate observable spiral structure.

Realistic dust trapping is modelled using a semi-analytic prescription in which particles with $\rm St=1$ may reach grain concentration factor $\eta \approx 6$ at the density peaks of the spiral perturbations, where $\eta$ represents the local dust enhancement relative to the mean dust-to-gas ratio in the disc, assumed to be 0.01 in all the models considered here. We find that particles of millimetre and centimetre sizes concentrate most strongly in spiral arms resulting in significantly enhanced millimetre emission in these regions. When the dust mass budget is dominated by these millimetre and centimetre sized grains we find self-gravitating structure to be observable in much lower mass discs than previously predicted. Through calculation of the grain fragmentation threshold in the discs modelled here we find that grains may only grow to as large as a few centimetres before grain-grain collisions become destructive. Therefore it may be the case that grain size distributions in self-gravitating discs satisfy this dust mass budget criterion.

Our synthetic unsharp masked images of discs in the Taurus star forming region ($d\sim140$ pc) exhibit distinguishable spiral structure for disc masses as low as $q=0.1$ given sufficient grain growth. These images are generated using realistic ALMA observing setups with reasonable observing times and PWV levels. We do however note that we only consider face-on discs during this evaluation and that inclining and rotating them may well obscure any substructure, likely most adversely in low mass discs with the weakest spirals.

Through multi-wavelength observations and derivation of the $\beta-$parameter we show how it is possible to retrieve information about grain growth and the dust-to-gas ratio distribution from our model discs. Through comparison of our predicted $\beta-$values to those calculated from future multi-wavelength observations of self-gravitating discs, it may be possible to utilise our disc model to examine grain distributions in the observed discs.

Applying our disc model to systems from the DSHARP sample, we find the quoted disc parameters for Elias 27, WaOph 6 and IM Lup suggest that they are all capable of driving observable, self-gravitating spiral structure providing that grains have grown to as large as the fragmentation threshold. We calculate disc-to-star mass ratios $q=0.27, 0.24$ and $0.11$, within their published outer radii, respectively for the 3 systems. A more detailed analysis exploring the potential parameter space of the DSHARP sample will be left to future work.

# Acknowledgements

We thank the anonymous referee for their insightful comments which have improved the clarity of this paper. CH is a Winton Fellow and this work has been supported by Winton Philanthropies / The David and Claudia Harding Foundation. This work used the Cirrus UK National Tier-2 HPC service at EPCC (http://www.cirrus.ac.uk) funded by The University of Edinburgh and EPSRC (EP/P020267/1).

# Gallery of Discs

![](gallery115.pdf)

![](gallery230.pdf)

![](gallery690.pdf)

[^1]: E-mail: `cadman@roe.ac.uk`

</paper>

Write the methods card for this paper.