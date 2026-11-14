# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...984L..12B\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...984L..12B",
 "title": "exoALMA. VII. Benchmarking Hydrodynamics and Radiative Transfer Codes",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Bae, Jaehan",
 "n_authors": 32,
 "arxiv_id": "2504.18643",
 "doi": "10.3847/2041-8213/adc436",
 "alma_projects_linked_by_archive": [
  "2021.1.01123.L"
 ]
}
```

Paper text:
<paper>
# exoALMA VII: Benchmarking Hydrodynamics and Radiative Transfer Codes

## Abstract

Forward modeling is often used to interpret substructures observed in protoplanetary disks. To ensure the robustness and consistency of the current forward modeling approach from the community, we conducted a systematic comparison of various hydrodynamics and radiative transfer codes. Using four grid-based hydrodynamics codes (`FARGO3D`, `Idefix`, `Athena++`, `PLUTO`) and a smoothed particle hydrodynamics code (`Phantom`), we simulated a protoplanetary disk with an embedded giant planet. We then used two radiative transfer codes (`mcfost`, `RADMC-3D`) to calculate disk temperatures and create synthetic $^{12}$CO cubes. Finally, we retrieved the location of the planet from the synthetic cubes using `DISCMINER`. We found strong consistency between the hydrodynamics codes, particularly in the density and velocity perturbations associated with planet-driven spirals. We also found a good agreement between the two radiative transfer codes: the disk temperature in `mcfost` and `RADMC-3D` models agrees within $\lesssim 3~\%$ everywhere in the domain. In synthetic $^{12}$CO channel maps, this results in brightness temperature differences within $\pm1.5$ K in all our models. This good agreement ensures consistent retrieval of planet’s radial/azimuthal location with only a few % of scatter, with velocity perturbations varying $\lesssim 20~\%$ among the models. Notably, while the planet-opened gap is shallower in the `Phantom` simulation, we found that this does not impact the planet location retrieval. In summary, our results demonstrate that any combination of the tested hydrodynamics and radiative transfer codes can be used to reliably model and interpret planet-driven kinematic perturbations.

# Introduction

Recent high-resolution observations have revealed a range of substructures in protoplanetary disks, including gaps, rings, crescents, and spirals in dust continuum and velocity kinks in molecular line channel maps. While unequivocally connecting these substructures to their cause(s) is not straightforward (cite: andrews2020; bae2023), one exciting possibility is that embedded protoplanets have created the observed substructures.

As protoplanets grow, they perturb their natal protoplanetary disks, producing observable signatures. While these perturbations manifest in various forms, in this paper we focus on kinematic perturbations observable with radio interferometric molecular line observations. In the vicinity of a protoplanet, spiral arms launched by the protoplanet induce strong perturbations in the density, temperature, and velocity of the background disk. These perturbations can manifest as velocity kinks in channel maps and/or Doppler flips in velocity centroid maps (see review by (cite: pinte2023) and references therein). Because these perturbations are generally strongest near protoplanets, velocity kinks and Doppler flips offer an opportunity to locate the protoplanet. In a more global scale, spirals launched by a protoplanet exchange angular momentum with the disk gas, causing an annular gap to open around the protoplanet’s orbit (cite: lin1993). The radially varying pressure gradient associated with the gap modulates the azimuthal velocity of the disk gas. As a result, inward to the protoplanet’s orbit, the gas rotates at a sub-Keplerian speed while outward to the orbit, the gas rotate’s at a super-Keplerian speed (cite: kanagawa2015). Because the width and depth of a planet-opened gap depend on the mass of the embedded protoplanet, the observed azimuthal velocity of the disk gas can be used to infer the protoplanet’s mass (cite: zhang2018; yun2019).

Hydrodynamic planet-disk interaction simulations, combined with radiative transfer calculations, can give us deeper understanding of the nature of observed substructures. For example, this forward modeling approach enables one to infer the location and mass of the planet responsible for observed substructures (cite: pinte2018; bae2019; bae2021), which can offer crucial insights into planet formation processes. However, while there had been previous efforts to compare properties of the gap a planet opens and the gravitational torque a planet exerts on its protoplanetary disks using various hydrodynamics codes (cite: devalborro2006), to date, no systematic hydrodynamics or radiative transfer benchmark tests comparing kinematic perturbations induced by planets embedded in their birth protoplanetary disks have been carried out. To this end, in this paper we tested if various hydrodynamics and radiative transfer codes produce consistent results. We benchmarked five hydrodynamics codes, namely `FARGO3D` (cite: fargo3d), `Idefix` (cite: idefix), `Athena++` (cite: athena), `PLUTO` (cite: pluto), and `Phantom` (cite: Phantom), and two radiative transfer codes, `mcfost` (cite: Pinte2006; Pinte2009) and `RADMC-3D` (cite: radmc), which are some of the most widely used codes from the community. Our benchmark test considered a protoplanetary disk with an embedded giant planet having a mass that is $10^{-3}$ of the central star, which corresponds to about a Jupiter mass in a system with a solar-mass central star.

This paper is organized as follows. In Section [2](#sec:hydro), we describe the planet-disk interaction simulation setup and compare the hydrodynamics simulation results. In Section [3](#sec:RT), we describe the radiative transfer simulation setup and compare disk temperatures and synthetic $^{12}$CO cubes. We retrieve the planet location in the synthetic cubes using `DISCMINER` and present the results in Section [4](#sec:discminer). We summarize our findings and conclude in Section [5](#sec:conclusion).

# Hydrodynamic Simulations

## Grid-based Hydrodynamics Simulation Setup

Grid-based simulations were carried out using four hydrodynamics codes: `FARGO3D` version 2.01[^1] (cite: fargo3d), `Idefix` version 1.1.0[^2] (cite: idefix), `Athena++` version 21.0[^3] (cite: athena), and `PLUTO` version 4.3[^4] (cite: pluto). While we refer the reader to the relevant papers listed above for technical details of these codes, we emphasize their fundamental differences in solving hydrodynamic equations. Among the grid-based codes, `FARGO3D` employs a finite-difference scheme, which directly approximates derivatives in the differential form of conservation equations. The other three codes, namely `Idefix`, `Athena++`, and `PLUTO`, utilize a finite-volume scheme, which works with the integral form of conservation equations and computes inter-cell fluxes through Riemann solvers. These methodological differences can influence how each code handles discontinuities between grid cells and conserves physical quantities. It is thus crucial to verify that results obtained with these codes agree with each other.

For all the grid-based simulations presented in this paper, we used the orbital advection algorithm FARGO (cite: fargo), which enables us to have a much larger time step by subtracting the azimuthally-averaged velocity, although we ran additional simulations without implementing FARGO and confirmed that the outcome of the simulations do not depend on the use of the FARGO algorithm.

### Simulation Domain & Numerical Resolution

We used three-dimensional spherical coordinates $(r, \theta, \phi)$. Throughout this paper, we use $r$, $\theta$, and $\phi$ to denote the spherical radius, meridional angle, and azimuthal angle in spherical coordinates, while we use $R \equiv r \sin \theta$ and $Z \equiv r \cos \theta$ to denote the cylindrical radius and height in cylindrical coordinates. The simulation domain extends from $r_{\rm in} = 0.3$ to $r_{\rm out} = 3.0$ in $r$ in the code unit, from $\theta_{\rm min} = \pi/2 - \arctan(0.5)$ to $\theta_{\rm max} = \pi/2 + \arctan(0.5)$ in $\theta$, and from $\phi_{\rm min} = -\pi$ to $\phi_{\rm max} = \pi$ in $\phi$. We used 288 logarithmically-spaced grid cells in $r$, 128 linear grid cells in $\theta$, and 784 linear grid cells in $\phi$, respectively. With this setup, we achieved $\Delta r \simeq r \Delta\theta \simeq r \Delta \phi  \simeq  0.008$ at the radial location of the planet ($r=1$), a numerical resolution allowing about 12 grid cells per scale height, which was shown to be sufficient for numerical convergence (cite: chen2024).

### Initial Disk Setup

The disk temperature has a power-law profile as a function of the cylindrical radius $R$, with a slope $q=-0.5$: $$\begin{equation}
\label{eqn:temp}
T(R) = T_p \left( R / R_p \right)^q.
\end{equation}$$ Here, $R_p$ is the radial distance between the star and the planet and $T_p$ is the temperature at $R=R_p$. We chose $T_p$ such that the disk aspect ratio $H/R$ at $R=R_p$ is 0.1, where $H$ denotes the disk scale height. This disk aspect ratio is close to the aspect ratio at the radial location of the planetary candidates identified in (cite: Pinte_exoALMA) when we adopt the temperature profile inferred in (cite: Galloway_exoALMA). We assumed that the disk is vertically isothermal and adopted an isothermal equation of state. Under this assumption, the gas pressure $P$, gas density $\rho$, and sound speed $c_s$ satisfy $P = \rho c_s^2$.

In reality, temperature structure of protoplanetary disks is more complex than the simplified temperature structure we adopted. The disk temperature is vertically stratified as the stellar irradiation diminishes toward the disk midplane (cite: chiang1997; dalessio1998). In addition, spirals driven by a forming planet can produce shock/compressional heating (cite: richert2015; lyra2016) and/or can cast shadows, modifying the stellar radiation field (cite: muley2024), all of which can alter the underlying temperature structure. However, we expect the difference in the velocity perturbations at the vicinity of the planet in isothermal simulations and those in more realistic simulations to be rather minor as shown in (cite: pinte2019) where planet-driven velocity perturbations are compared between an isothermal simulation and one where the disk temperature is regularly updated by running radiative transfer calculations.

We initialized the gas density to satisfy the vertical force balance: $$\begin{equation}
\label{eqn:density}
    \rho(R,Z) = \rho_p \left( {R \over R_p} \right)^p \exp\left({{GM_* \over c_s^2}\left[ {1 \over \sqrt{R^2+Z^2}}- {1 \over R}\right]}\right).
\end{equation}$$ Here, $G$ is the gravitational constant and $M_*$ is the stellar mass. We chose $\rho_p$ such that the total initial disk mass is $0.01~M_\odot$. Note however that the hydrodynamic simulations we carried out are scalable and the outcome does not depend on the choice of the disk mass; the disk mass only becomes relevant in radiative transfer calculations. We adopted $p=-2.25$ such that the surface density follows $\Sigma \propto R^{-1}$.

The angular velocity $\Omega$ was initialized to satisfy the radial force balance: $$\begin{equation}
    \Omega (R,Z) = \Omega_K \left[ (p+q) \left( {H \over R} \right)^2  + (1+q) - {qR \over \sqrt{R^2 + Z^2}} \right]^{1/2},
\end{equation}$$ where $\Omega_K = \sqrt{GM_*/R^3}$ is the Keplerian angular velocity. The initial azimuthal velocity was set to $v_\phi = R \Omega$. The initial radial and meridional velocities were set to zero ($v_r = v_\theta = 0$).

We adopted kinematic viscosity characterized by $\nu = 10^{-5}$. In terms of the Shakura–Sunyaev viscosity parameter $\alpha$ (cite: shakura1973), this kinematic viscosity is equivalent to $\alpha=10^{-3}$ at the radial location of the planet.

### Planet Potential

We considered a planet having a mass $M_p = 10^{-3}M_*$. For a solar-mass star, this planet mass corresponds to about a Jupiter mass, which is close to the lower limit we expect to detect in exoALMA-quality data (cite: Pinte_exoALMA). The planet potential $\Phi_p$ is smoothed following $$\begin{equation}
    \Phi_p = -{G M_p \over d} \left[ \left( {d \over \epsilon} \right)^4 -2 \left( {d \over \epsilon} \right)^3 +2 \left( {d \over \epsilon} \right) \right]
\end{equation}$$ when $d \leq \epsilon$, where $d$ is the distance between the planet and the grid cell in question, and $\epsilon = 3\Delta r \simeq 0.024$, where $\Delta r \simeq 0.008$ is the size of the grid cell at the location of the planet. When $d > \epsilon$, $\Phi_p = - GM_p/d$.

The mass of the planet was ramped up following $$\begin{equation}
    M_p(t) = M_{p,{\rm final}} \sin^2 \left( {t \over \tau_{\rm ramp}} {\pi \over 2} \right),
\end{equation}$$ where $M_{p, {\rm final}}=10^{-3}~M_*$ and $\tau_{\rm ramp} = 100$ orbits at the radial location of the planet. No gas accretion onto the planet is allowed, so the planet mass is fixed to $10^{-3}~M_*$ after 100 orbits. We fixed the planet on a circular orbit and did not allow orbital migration.

### Boundary Conditions

At the inner and outer radial boundaries, we adopted the symmetric boundary condition, although the choice of radial boundary condition should not have a significant impact on the outcome because we implemented a wave-killing zone at the radial boundaries (cite: devalborro2006). The damping function was written as $$\begin{equation}
    {dX(r) \over dt} = -\left( {{X(r)-X_0(r)} \over \tau_{\rm damp}} \right) f(r),
\end{equation}$$ where $X$ is density or velocity and $X_0$ is the initial value of the variable $X$. The inner damping zone was located between $r_1 = r_{\rm in} = 0.3$ and $r_2 = 0.357$, where we set the function $f(r)$ at the inner radial boundary $f_{\rm in}(r)$ to $$\begin{equation}
    f_{\rm in}(r) = 1-\sin^2\left[ {\pi \over 2} {(r-r_1) \over (r_2-r_1)}\right].
\end{equation}$$ The outer damping zone was located between $r_1 = 2.52$ and $r_2 = r_{\rm out} = 3.0$. The function $f(r)$ at the outer radial boundary, $f_{\rm out}(r)$, is given by $$\begin{equation}
    f_{\rm out}(r) = \sin^2\left[ {\pi \over 2} {(r-r_1) \over (r_2-r_1)}\right].
\end{equation}$$ The damping timescale $\tau_{\rm damp}$ at the inner/outer radial boundary was given by $1\%$ of the orbital timescale at the inner/outer edge of the domain.

At the meridional boundaries $\theta = \theta_{\rm min}$ and $\theta = \theta_{\rm max}$, we adopted the symmetric boundary condition for $v_r$ and $v_\phi$. We adopted the anti-symmetric boundary condition for $v_\theta$ such that $v_\theta = 0$ at the meridional boundary and that the meridional velocity in the active zone and the meridional velocity in the ghost zone, referring to a few extra cells beyond the boundary of the simulation domain, satisfy $v_\theta({\rm ghost}) = -v_\theta({\rm active})$. The density in the ghost zone was set to satisfy the vertical hydrostatic equilibrium (cite: bae2016): $$\begin{equation}
\label{eqn:boundary}
    {1 \over \rho} {\partial \over \partial \theta} (\rho c_s^2) = {v_\phi^2 \over \tan \theta}.
\end{equation}$$

## Smoothed Particle Hydrodynamics Simulation Setup

The smoothed particle hydrodynamics (SPH) simulation was carried out using the code `Phantom` version 2022.0.1[^5] (cite: Phantom). `Phantom` solves the equations of hydrodynamics in Lagrangian form. The fluid is discretized onto a set of particles of mass and thus `Phantom` is mesh-free by construction. We refer the reader to (cite: Phantom) for further details on the code.

We initialized the disk based on the grid-based simulation setup described in Section [2.1.2](#sec:initial_setup). However, due to the intrinsic differences between grid-based and SPH codes, the exact setup differs inevitably and we focus on describing these differences below. We used 10 million SPH particles, initially placed between $r=0.3$ and $r=3$. Compared to grid-based simulations, SPH simulations do not define a mesh, so particles can freely pass the initial inner/outer radii. We employed a fixed inner boundary at $r=0.2$ inside of which particles are removed from the simulation. This, and the spreading of the outer disk, means that the mass (and resolution) enclosed between $r=0.3$ and $r=3$ depletes with time, in contrast to the damping boundary conditions employed in the grid-based codes where arbitrary amounts of mass are continuously injected or removed in the damping zones to maintain the initial density profile in the damping zone. We found that about 30% of the initial disk mass is lost through the inner boundary after 500 orbits. Unlike some previous `Phantom` simulations where the mass lost from the disk is added to the star, we fixed the stellar mass to be consistent with grid-based simulations. Another difference compared with grid-based simulations is that the numerical resolution of SPH simulations depends on the local density and thus varies across the simulation domain and over time. This density dependency allows the best numerical resolution in the regions of high density, such as the disk midplane, while the decrease in the density, which can happen near the surface or within a planet-carved gap, results in poor numerical resolution.

We embedded a planet in the disk orbiting at $r=1$, having a mass $M_p = 10^{-3}M_*$. The potential of the planet was ramped up over the initial 100 orbits, consistently with grid-based simulations. The planet was implemented as a prescribed potential consistently with grid-based simulations; however, note that this is different from the usual approach in `Phantom` simulations where sink particles are used to model planets in a way that explicitly conserves momentum (cite: bate1995). Using a prescribed potential fixes the planet on a circular orbit and does not allow for orbital migration.

We added a fixed kinematic viscosity of $\nu = 10^{-5}$ in code units, following the ‘two first derivatives’ formulation of the Navier Stokes terms outlined in Section 3.2.4 of (cite: lodato2010). This is in addition to the usual shock capturing terms which are implemented with the (cite: cullen2010) switch with $\alpha_{\rm av} \in [0,1]$ and $\beta_{\rm av} = 2$ as outlined in (cite: Phantom).

## Results

In Figures [1](#fig:dens2d) – [4](#fig:vtheta2d), we present two-dimensional contour plots in a $\phi - r$ plane, showing the gas density, radial velocity, azimuthal velocity, and meridional velocity at three different heights after 500 planetary orbits of evolution: $Z/R=0, 0.1$, and 0.3. These heights are chosen to cover a range of vertical layers which various molecular lines having different optical depths probe ((cite: Galloway_exoALMA); see also review by (cite: miotello2023) and references therein). For a more quantitative comparison, we present one-dimensional azimuthal distributions of the gas density, radial velocity, azimuthal velocity, and meridional velocity in Appendix [7](#sec:1dplots).

![](./figures/dens2d_unstratified.png)

![](./figures/vrad2d_unstratified.png)

![](./figures/vphi2d_unstratified.png)

![](./figures/vtheta2d_unstratified.png)

![](./figures/radial_profiles.png)

Looking first at the perturbed density presented in Figure [1](#fig:dens2d), all the grid-based simulations show an excellent agreement with each other although the level of density perturbation may differ by up to a few percent in the upper layers. Because particles can freely flow through the inner and outer boundary, the `Phantom` simulation shows lower density near the radial boundaries. At the inner disk in particular, the low density results in a higher numerical viscosity. Together with strong shock dissipation in the inner disk, this leads to a rapid depletion which in turn flattens the surface density profile and makes the planet-opened gap shallower. We caution that inferring the mass of gap-opening planet based on the gap shape from `Phantom` simulations could result in an overestimation. Nevertheless, we emphasize that the overall morphology of the spirals driven by the planet and the level of density perturbation associated with the spirals seen in the `Phantom` simulation agree well with those seen in grid-based simulations, presumably because they are not sensitive to the underlying surface density profile (cite: ogilvie2002; rafikov2002; baezhu2018).

Similarly to the density perturbation, velocity perturbations associated with the spirals show agreement among grid-based simulations (Figures [2](#fig:vrad2d) – [4](#fig:vtheta2d)). In the `Phantom` simulation, the perturbation in the azimuthal velocity across the gap is of the order of $1\%$ of the Keplerian speed, much smaller than that in grid-based simulations (Figure [5](#fig:radial_profiles)), due to the shallower gap. However, the velocity perturbations along the spirals in the `Phantom` simulation are comparable to those in grid-based simulations. Because the strength of velocity kinks and Doppler flips is closely related to the level of velocity perturbations along the spirals, the consistency across all five hydrodynamics codes is important in the retrieval of the location of the planet, as we will show later in Section [4](#sec:discminer).

For a more quantitative comparison of the gap structure between the models, in Figure [5](#fig:radial_profiles) we present azimuthally averaged radial profiles of the surface density and azimuthal velocity. In grid-based simulations, the surface density at the center of the gap opened by a Jupiter-mass planet is suppressed by $\simeq 70~\%$. On the other hand, in the `Phantom` simulation, the surface density is decreased by only $\simeq 10~\%$. The shallow gap results in an azimuthal velocity variation across the gap of $\sim1~\%$, much smaller than $\sim6~\%$ seen in grid-based codes.

# Radiative Transfer Calculations

Radiative transfer calculations were carried out using `mcfost` version 4.1.08[^6] (cite: Pinte2006; Pinte2009) and `RADMC-3D` version 2.0[^7](cite: radmc), using the outputs at 500 planetary orbits from the hydrodynamic simulations introduced in the previous Section. As part of the exoALMA collaboration, the `mcfost` code was updated to natively read the output files from all hydrodynamic codes. We tested all the combinations between hydrodynamic and radiative transfer codes, except for the `Phantom` + `RADMC-3D` combination because at the time we write this paper, there is no `RADMC-3D` module which allows one to read in `Phantom` outputs and map SPH particles onto a structured `RADMC-3D` grid. This results in nine total combinations.

![](./figures/temperature_comparison.pdf)

## Radiative Transfer Calculation Setup

We set the radiative transfer grid to be identical to that of grid-based hydrodynamic simulations described in Section [2.1.1](#sec:simulation_domain). For `Phantom` outputs, we used a Voronoi tessellation where each `mcfost` cell corresponds to a SPH particle in order to avoid interpolating the density structure between the SPH and radiative transfer codes.

To convert physical quantities from dimensionless hydrodynamic simulations into physical units for radiative transfer calculations, we placed the planet at 100 au from the solar-mass central star. The total initial gas mass in the disk was set to $0.01~M_\odot$. With this conversion, the initial gas surface density at the radial location of the planet is $0.52~{\rm g~cm}^{-2}$, which is broadly consistent with the gas surface density inferred for exoALMA disks (cite: Rosotti_exoALMA). The star was placed at 140 parsecs from the observer.

To generate synthetic $^{12}$CO $J=3-2$ line cubes, we first determined the dust temperature by running Monte Carlo simulations. We placed a solar-mass star having a radius of $2~R_\odot$ and a temperature of 4000 K at the center of the domain, which emits a total of $10^9$ photons that interacts with dust grains. Dust opacities were calculated assuming a power-law grain size distribution following d$n(a)/{\rm d}a \propto a^{-3.5}$, between $a_{\rm min} = 0.03~\mu$m and $a_{\rm max} = 1$ mm. The total dust mass was assumed to be $1\%$ of the gas mass in each grid cell. Grain composition was assumed to be astrosilicates (cite: Weingartner2001). We computed the dust optical properties using the Mie theory, considering isotropic scattering only. The same opacities were used for both `mcfost` and `RADMC-3D` Monte Carlo simulations.

We assumed that the gas and dust are in local thermodynamic equilibrium, sharing the same temperature. We adopted a $^{12}$CO abundance of $10^{-4}$ relative to the total gas (by number) when the temperature is higher than 20 K. Below 20 K, we assumed that all CO molecules are frozen onto grains and no gas phase CO is present. We made an assumption that the local line width is set by thermal broadening only and ignored any non-thermal broadening.

The disk inclination was set to 45 degrees, with a position angle of 90 degree (from north to east). The disk was placed at 140 pc and positioned such that the planet is located 45 degrees west of south.

## Results

### Temperature

The left panels of Figure [6](#fig:temp_comp) present azimuthally averaged temperature distributions of the five `mcfost` models in a $r-\theta$ plane. The overall temperature structure exhibits a radially decreasing temperature profile, with a hotter atmosphere and a colder midplane, which is consistent with disk models where stellar irradiation is the dominating heating source (cite: chiang1997; dalessio1998).

![](./figures/RT_comparison.pdf)

The temperature distributions show an excellent agreement within the four `mcfost` models using outputs from the grid-based hydrodynmics codes. When the azimuthally averaged two-dimensional temperature distributions are compared grid by grid, no two models have a temperature difference greater than 0.84 K (between `Idefix` + `mcfost` and `Athena++` + `mcfost`), with a domain-averaged mean difference ranging from 0.013 K (between `FARGO3D` + `mcfost` and `PLUTO` + `mcfost`) to 0.18 K (between `Idefix` + `mcfost` and `Athena++` + `mcfost`). In terms of fractional difference $\Delta T/T$, no two models have a difference greater than $2.7~\%$ (between `Idefix` + `mcfost` and `Athena++` + `mcfost`) when compared grid by grid, with a domain-averaged mean difference ranging from $0.04~\%$ (between `FARGO3D` + `mcfost` and `Idefix` + `mcfost`) to $0.65~\%$ (between `Idefix` + `mcfost` and `Athena++` + `mcfost`).

Similarly, an excellent agreement was found among the `RADMC-3D` models. Based on grid-by-grid comparisons, we found no two models have a difference greater than 0.51 K (between `FARGO3D` + `RADMC-3D` and `Athena++` + `RADMC-3D`). In terms of fractional difference, no two models have a difference greater than $1.8~\%$ (between `FARGO3D` + `RADMC-3D` and `Athena++` + `RADMC-3D`).

When `mcfost` models are compared with `RADMC-3D` models, we found a strong consistency between the models. `Idefix` and `PLUTO` models show an excellent agreement in particular; when the temperatures are compared grid by grid, these models differ by only $\lesssim 0.08~\%$ on average. The `Athena++` models show the largest differences, but even in this case the fractional temperature difference is smaller than $3~\%$ everywhere in the domain. It is certainly worthwhile further investigating why `Athena++` models show larger differences but as we will show in the next section, the corresponding differences in $^{12}$CO channel maps are smaller than the typical noise in the exoALMA data and we defer such an investigation to a future study.

Lastly, we compared the `Phantom` + `mcfost` model to other `mcfost` models. As an example, we present the difference between the temperature profiles from the `Phantom` + `mcfost` model and `FARGO3D` + `mcfost` model in the bottom right panel of Figure [6](#fig:temp_comp). As shown, the `Phantom` model shows noticeable differences from other models, up to $\pm 15~\%$ in individual grid cells, with a domain-averaged mean difference of about $5~\%$. Given the differences in the density structure we discussed in Section [2.3](#sec:hydro_results), this difference is not too surprising. Yet, this temperature difference results in only small differences in $^{12}$CO channel maps and may not be noticeable in exoALMA-quality data, as we will show now.

### Channel Maps

Figure [7](#fig:rt_comp) shows synthetic $^{12}$CO emission at a representative velocity channel. Overall, the brightness temperature at the surface shows visually negligible differences among the models. In addition, all synthetic cubes show clear and consistent velocity kinks in the vicinity of the planet, which is crucial for retrieving planet mass and location. In the bottom right panel of Figure [7](#fig:rt_comp), we present the brightness temperature of each model relative to the reference model (`FARGO3D` + `mcfost`), along the iso-velocity contour shown in the top left panel. As can be seen from the figure, all models agree with each other within $\pm 1.5$ K, with the largest difference seen from the `Phantom` + `mcfost` model (lavender color). At the location of the planet (offset $\simeq -0.5\ensuremath{''}$), the difference among the models is $<0.5$ K. Given that the typical level of noise in the exoALMA molecular line images is about 1.5 K (cite: Teague_exoALMA), we argue that the small, sub-Kelvin differences in brightness temperature among our models should not be a concern when it comes to modeling/finding embedded protoplanets.

![](./figures/discminer.png)

![](./figures/discminer_comparison.pdf)

# Retrieval of Planet Location using `DISCMINER`

We used `DISCMINER`[^8] to retrieve the planet location in synthetic cubes. To do so, we convolved the raw synthetic cubes with a $0.15\ensuremath{''}$ Gaussian beam and added random noises with a standard deviation of 1.5 K in each $100~{\rm m~s}^{-1}$ channel; these are the beamsize and level of noise of fiducial exoALMA molecular line images (cite: Teague_exoALMA). For the detailed workflow of the retrieval, we refer the reader to (cite: discminer; izquierdo2023).

In Figure [8](#fig:discminer_mcfost), we present a folded velocity residual map for the $^{12}$CO synthetic cube generated with `FARGO3D` and `mcfost`, along with peak residual velocity profile as a function of azimuthal angle and radius. `DISCMINER` found a peak in the folded velocity residual map with a $3.64\sigma$ significance, and inferred the planet to be at 107.8 au in radius and $-45.25$ degrees in azimuth, which are in a good agreement with the true planet location: 100 au and $-45$ degrees.

To compare the inferred location of the planet and the associated peak velocity residual, we plot these quantities in Figure [9](#fig:discminer_comparison). Overall, the radial and azimuthal locations of the planet are consistent across the models and agree well with the true planet location. However, we found that the inferred radial locations are systematically biased toward slightly large radial distances with a mean distance of 109.0 au, a minimum distance of 105.0 au (`Idefix` + `RADMC-3D`), and a maximum distance of 116.2 au (`Phantom` + `mcfost`). This bias in radial location was previously noted in (cite: discminer), too, and we speculate that this bias is because the peak residual is generally more sensitive to the outer spiral arm. Note, however, that the mean retrieved radial location is within one beam ($0.15\ensuremath{''}$, or 21 au at 140 pc) from the true location. In case of the inferred azimuthal location, they are clustered around the true location with a mean azimuthal angle of $-45.92$ degrees, a minimum azimuthal angle of $-48.97$ degrees (`PLUTO` + `mcfost`), and a maximum azimuthal angle of $-41.49$ degrees (`PLUTO` + `RADMC-3D`). Lastly, we found that the peak residual velocity is broadly consistent within about $20~\%$ variations among the models, with a mean of $0.074~{\rm km~s}^{-1}$, a minimum of $0.054~{\rm km~s}^{-1}$ (`Idefix` + `RADMC-3D`), and a maximum of $0.088~{\rm km~s}^{-1}$ (`Athena++` + `mcfost`).

In summary, synthetic observations produced by any combination of the hydrodynamics and radiative transfer codes tested in this work exhibit broadly consistent localized perturbations near the true planet location.

# Conclusion

To demonstrate the consistency of the codes used for forward modeling protoplanetary disks from the community, we conducted a systematic comparison of various hydrodynamics and radiative transfer codes. To do so, we first carried out three-dimensional planet-disk interaction simulations using four grid-based hydrodynamics codes (`FARGO3D`, `Idefix`, `Athena++`, `PLUTO`) and a smoothed particle hydrodynamics code (`Phantom`). Overall, we found an excellent agreement between grid-based codes, in terms of the density and velocity structure. However, due to the different boundary conditions in the `Phantom` simulation, we found that the planet-opened gap is shallower than those in grid-based simulations, which results in smaller azimuthal velocity deviations from the Keplerian rotation. Despite the difference in the gap depth, the overall morphology of the planet-driven spirals and the level of density/velocity perturbations associated with the spirals in the `Phantom` simulation are in a good agreement with those in other hydrodynamics codes.

We used two radiative transfer codes (`mcfost`, `RADMC-3D`) to calculate the disk temperature and generate synthetic $^{12}$CO cubes. The disk temperatures showed a good agreement within `mcfost` cubes and `RADMC-3D` cubes separately, as well as between `mcfost` and `RADMC-3D` models based on the same hydrodynamic simulation. Due to the different density structure, the disk temperature in the `Phantom` + `mcfost` model is different from other models up to $\pm15~\%$ in individual grid cells, with a domain-averaged mean difference of about $5~\%$. However, the corresponding difference in $^{12}$CO emission is $\leq 1.5$ K, within the typical noise in the exoALMA data.

Using `DISCMINER`, we retrieved the location of the planet from the synthetic cubes. Despite some differences in the hydrodynamics and/or radiative transfer calculation results, the retrieved planet locations are consistent across all cubes and agree well with the true planet location. This is because the density and velocity perturbations along the planet-driven spirals, which determines the location and strength of the velocity kink in channel maps, are consistent across all the codes we tested.

In summary, our findings suggest that any combination of the hydrodynamics and radiative transfer codes we tested in this paper could be used to model and interpret planet-driven kinematic perturbations. Admittedly, we only considered a single base hydrodynamics model. Future studies are needed to confirm that the consistency across all codes holds when changes are made to the model, such as planet mass, orbital eccentricity/migration, vertical temperature stratification, finite gas cooling time, disk viscosity, and the presence/strength of disk’s magnetic fields.

# Acknowledgments

This Letter makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.01123.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. We thank the North American ALMA Science Center (NAASC) for their generous support including providing computing facilities and financial support for student attendance at workshops and publications. Part of the calculations were performed on the OzSTAR national facility at Swinburne University of Technology. The OzSTAR program receives funding in part from the Astronomy National Collaborative Research Infrastructure Strategy (NCRIS) allocation provided by the Australian Government, and from the Victorian Higher Education State Investment Fund (VHESIF) provided by the Victorian Government. JB acknowledges support from NASA XRP grant No. 80NSSC23K1312. MB, DF, JS have received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (PROTOPLANETS, grant agreement No. 101002188). Computations by JS have been performed on the ‘Mesocentre SIGAMM’ machine, hosted by Observatoire de la Cote d’Azur. PC acknowledges support by the Italian Ministero dell’Istruzione, Università e Ricerca through the grant Progetti Premiali 2012 – iALMA (CUP C52I13000140001) and by the ANID BASAL project FB210003. NC has received funding from the European Research Council (ERC) under the European Union Horizon Europe research and innovation program (grant agreement No. 101042275, project Stellar-MADE). SF is funded by the European Union (ERC, UNVEIL, 101076613), and acknowledges financial contribution from PRIN-MUR 2022YP5ACE. MF is supported by a Grant-in-Aid from the Japan Society for the Promotion of Science (KAKENHI: No. JP22H01274). CH acknowledges support from NSF AAG grant No. 2407679. IH is supported by an Australian Government Research Training Program (RTP) Scholarship. Support for AFI was provided by NASA through the NASA Hubble Fellowship grant No. HST-HF2-51532.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555. GL has received funding from the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska-Curie grant agreement No. 823823 (DUSTBUSTERS). CL has received funding from the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska-Curie grant agreement No. 823823 (DUSTBUSTERS) and by the UK Science and Technology research Council (STFC) via the consolidated grant ST/W000997/1. CP acknowledges Australian Research Council funding via FT170100040, DP18010423, DP220103767, and DP240103290. DP acknowledges Australian Research Council funding via DP18010423, DP220103767, and DP240103290. GR acknowledges funding from the Fondazione Cariplo, grant no. 2022-1217, and the European Research Council (ERC) under the European Union’s Horizon Europe Research & Innovation Programme under grant agreement no. 101039651 (DiscEvol). GWF acknowledges support from the European Research Council (ERC) under the European Union Horizon 2020 research and innovation program (Grant agreement no. 815559 (MHDiscs)). GWF was granted access to the HPC resources of IDRIS under the allocation A0120402231 made by GENCI. TCY acknowledges support by Grant-in-Aid for JSPS Fellows JP23KJ1008. Views and opinions expressed by ERC-funded scientists are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council. Neither the European Union nor the granting authority can be held responsible for them.

# Software

`FARGO3D` (cite: fargo3d), `Idefix` (cite: idefix), `Athena++` (cite: athena), `PLUTO` (cite: pluto), `Phantom` (cite: Phantom), `mcfost` (cite: mcfost), `RADMC-3D` (cite: radmc), `DISCMINER` (cite: discminer)

# Azimuthal Density and Velocity Profiles

In Figures [10](#fig:dens1d) – [13](#fig:vtheta1d), we present azimuthal distributions of the density, radial velocity, azimuthal velocity, and meridional velocity at $R=0.7$ and $R=  1.3$. In each figure, we present the azimuthal distributions at three different heights, $Z/R=0, 0.1$, and 0.3.

![](./figures/dens1d_phi_unstratified.png)

![](./figures/vrad1d_phi_unstratified.png)

![](./figures/vphi1d_phi_unstratified.png)

![](./figures/vtheta1d_phi_unstratified.png)

natexlab

(ref: andrews2020) Andrews, S. M. 2020, ARA&A, 58, 483, doi: [`10.1146/annurev-astro-031220-010302`](http://doi.org/10.1146/annurev-astro-031220-010302)

(ref: bae2023) Bae, J., Isella, A., Zhu, Z., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 423, doi: [`10.48550/arXiv.2210.13314`](http://doi.org/10.48550/arXiv.2210.13314)

(ref: bae2016) Bae, J., Nelson, R. P., & Hartmann, L. 2016, ApJ, 833, 126, doi: [`10.3847/1538-4357/833/2/126`](http://doi.org/10.3847/1538-4357/833/2/126)

(ref: bae2021) Bae, J., Teague, R., & Zhu, Z. 2021, ApJ, 912, 56, doi: [`10.3847/1538-4357/abe45e`](http://doi.org/10.3847/1538-4357/abe45e)

(ref: baezhu2018) Bae, J., & Zhu, Z. 2018, ApJ, 859, 118, doi: [`10.3847/1538-4357/aabf8c`](http://doi.org/10.3847/1538-4357/aabf8c)

(ref: bae2019) Bae, J., Zhu, Z., Baruteau, C., et al. 2019, ApJL, 884, L41, doi: [`10.3847/2041-8213/ab46b0`](http://doi.org/10.3847/2041-8213/ab46b0)

(ref: bate1995) Bate, M. R., Bonnell, I. A., & Price, N. M. 1995, MNRAS, 277, 362, doi: [`10.1093/mnras/277.2.362`](http://doi.org/10.1093/mnras/277.2.362)

(ref: fargo3d) Benı́tez-Llambay, P., & Masset, F. S. 2016, ApJS, 223, 11, doi: [`10.3847/0067-0049/223/1/11`](http://doi.org/10.3847/0067-0049/223/1/11)

(ref: chen2024) Chen, K., & Dong, R. 2024, ApJ, 976, 49, doi: [`10.3847/1538-4357/ad83d0`](http://doi.org/10.3847/1538-4357/ad83d0)

(ref: chiang1997) Chiang, E. I., & Goldreich, P. 1997, ApJ, 490, 368, doi: [`10.1086/304869`](http://doi.org/10.1086/304869)

(ref: cullen2010) Cullen, L., & Dehnen, W. 2010, MNRAS, 408, 669, doi: [`10.1111/j.1365-2966.2010.17158.x`](http://doi.org/10.1111/j.1365-2966.2010.17158.x)

(ref: dalessio1998) D’Alessio, P., Cantö, J., Calvet, N., & Lizano, S. 1998, ApJ, 500, 411, doi: [`10.1086/305702`](http://doi.org/10.1086/305702)

(ref: devalborro2006) de Val-Borro, M., Edgar, R. G., Artymowicz, P., et al. 2006, MNRAS, 370, 529, doi: [`10.1111/j.1365-2966.2006.10488.x`](http://doi.org/10.1111/j.1365-2966.2006.10488.x)

(ref: radmc) Dullemond, C. P., Juhasz, A., Pohl, A., et al. 2012, RADMC-3D: A multi-purpose radiative transfer tool, Astrophysics Source Code Library, record ascl:1202.015

(ref: Galloway_exoALMA) Galloway-Sprietsma, M., Bae, J., Izquierdo, A. F., et al. 2025, arXiv e-prints, arXiv:2504.19902. [`https://arxiv.org/abs/2504.19902`](https://arxiv.org/abs/2504.19902)

(ref: discminer) Izquierdo, A. F., Testi, L., Facchini, S., Rosotti, G. P., & van Dishoeck, E. F. 2021, A&A, 650, A179, doi: [`10.1051/0004-6361/202140779`](http://doi.org/10.1051/0004-6361/202140779)

(ref: izquierdo2023) Izquierdo, A. F., Testi, L., Facchini, S., et al. 2023, A&A, 674, A113, doi: [`10.1051/0004-6361/202245425`](http://doi.org/10.1051/0004-6361/202245425)

(ref: Izquierdo_exoALMA) Izquierdo, A. F., Stadler, J., Galloway-Sprietsma, M., et al. 2025, arXiv e-prints, arXiv:2504.19986. [`https://arxiv.org/abs/2504.19986`](https://arxiv.org/abs/2504.19986)

(ref: kanagawa2015) Kanagawa, K. D., Tanaka, H., Muto, T., Tanigawa, T., & Takeuchi, T. 2015, MNRAS, 448, 994, doi: [`10.1093/mnras/stv025`](http://doi.org/10.1093/mnras/stv025)

(ref: idefix) Lesur, G. R. J., Baghdadi, S., Wafflard-Fernandez, G., et al. 2023, A&A, 677, A9, doi: [`10.1051/0004-6361/202346005`](http://doi.org/10.1051/0004-6361/202346005)

(ref: lin1993) Lin, D. N. C., & Papaloizou, J. C. B. 1993, in Protostars and Planets III, ed. E. H. Levy & J. I. Lunine, 749

(ref: lodato2010) Lodato, G., & Price, D. J. 2010, MNRAS, 405, 1212, doi: [`10.1111/j.1365-2966.2010.16526.x`](http://doi.org/10.1111/j.1365-2966.2010.16526.x)

(ref: lyra2016) Lyra, W., Richert, A. J. W., Boley, A., et al. 2016, ApJ, 817, 102, doi: [`10.3847/0004-637X/817/2/102`](http://doi.org/10.3847/0004-637X/817/2/102)

(ref: fargo) Masset, F. 2000, A&AS, 141, 165, doi: [`10.1051/aas:2000116`](http://doi.org/10.1051/aas:2000116)

(ref: pluto) Mignone, A., Bodo, G., Massaglia, S., et al. 2007, ApJS, 170, 228, doi: [`10.1086/513316`](http://doi.org/10.1086/513316)

(ref: miotello2023) Miotello, A., Kamp, I., Birnstiel, T., Cleeves, L. C., & Kataoka, A. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 501, doi: [`10.48550/arXiv.2203.09818`](http://doi.org/10.48550/arXiv.2203.09818)

(ref: muley2024) Muley, D., Melon Fuksman, J. D., & Klahr, H. 2024, A&A, 687, A213, doi: [`10.1051/0004-6361/202449739`](http://doi.org/10.1051/0004-6361/202449739)

(ref: ogilvie2002) Ogilvie, G. I., & Lubow, S. H. 2002, MNRAS, 330, 950, doi: [`10.1046/j.1365-8711.2002.05148.x`](http://doi.org/10.1046/j.1365-8711.2002.05148.x)

(ref: Pinte2006) Pinte, C., Ménard, F., Duchêne, G., & Bastien, P. 2006, A&A, 459, 797, doi: [`10.1051/0004-6361:20053275`](http://doi.org/10.1051/0004-6361:20053275)

(ref: pinte2023) Pinte, C., Teague, R., Flaherty, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 645, doi: [`10.48550/arXiv.2203.09528`](http://doi.org/10.48550/arXiv.2203.09528)

(ref: Pinte2009) Pinte, C., et al. 2009, A&A, 498, 967, doi: [`10.1051/0004-6361/200811555`](http://doi.org/10.1051/0004-6361/200811555)

(ref: pinte2018) Pinte, C., Price, D. J., Ménard, F., et al. 2018, ApJL, 860, L13, doi: [`10.3847/2041-8213/aac6dc`](http://doi.org/10.3847/2041-8213/aac6dc)

(ref: pinte2019) Pinte, C., van der Plas, G., Ménard, F., et al. 2019, Nature Astronomy, 3, 1109, doi: [`10.1038/s41550-019-0852-6`](http://doi.org/10.1038/s41550-019-0852-6)

(ref: mcfost) Pinte, C., Ménard, F., Duchêne, G., et al. 2022, MCFOST: Radiative transfer code, Astrophysics Source Code Library, record ascl:2207.023

(ref: Pinte_exoALMA) Pinte, C., Ilee, J. D., Huang, J., et al. 2025, arXiv e-prints, arXiv:2504.18717. [`https://arxiv.org/abs/2504.18717`](https://arxiv.org/abs/2504.18717)

(ref: Phantom) Price, D. J., Wurster, J., Tricco, T. S., et al. 2018, PASA, 35, e031, doi: [`10.1017/pasa.2018.25`](http://doi.org/10.1017/pasa.2018.25)

(ref: rafikov2002) Rafikov, R. R. 2002, ApJ, 572, 566, doi: [`10.1086/340228`](http://doi.org/10.1086/340228)

(ref: richert2015) Richert, A. J. W., Lyra, W., Boley, A., Mac Low, M.-M., & Turner, N. 2015, ApJ, 804, 95, doi: [`10.1088/0004-637X/804/2/95`](http://doi.org/10.1088/0004-637X/804/2/95)

(ref: Rosotti_exoALMA) Rosotti, G. P., Longarini, C., Paneque-Carreño, T., et al. 2025, arXiv e-prints, arXiv:2504.20012. [`https://arxiv.org/abs/2504.20012`](https://arxiv.org/abs/2504.20012)

(ref: shakura1973) Shakura, N. I., & Sunyaev, R. A. 1973, A&A, 24, 337

(ref: athena) Stone, J. M., Tomida, K., White, C. J., & Felker, K. G. 2020, ApJS, 249, 4, doi: [`10.3847/1538-4365/ab929b`](http://doi.org/10.3847/1538-4365/ab929b)

(ref: Teague_exoALMA) Teague, R., Benisty, M., Facchini, S., et al. 2025, arXiv e-prints, arXiv:2504.18688. [`https://arxiv.org/abs/2504.18688`](https://arxiv.org/abs/2504.18688)

(ref: Weingartner2001) Weingartner, J. C., & Draine, B. T. 2001, ApJ, 548, 296, doi: [`10.1086/318651`](http://doi.org/10.1086/318651)

(ref: yun2019) Yun, H.-G., Kim, W.-T., Bae, J., & Han, C. 2019, ApJ, 884, 142, doi: [`10.3847/1538-4357/ab3fab`](http://doi.org/10.3847/1538-4357/ab3fab)

(ref: zhang2018) Zhang, S., Zhu, Z., Huang, J., et al. 2018, ApJL, 869, L47, doi: [`10.3847/2041-8213/aaf744`](http://doi.org/10.3847/2041-8213/aaf744)

[^1]: <https://github.com/FARGO3D/fargo3d>

[^2]: <https://github.com/idefix-code/idefix/releases/tag/v1.1>

[^3]: <https://github.com/PrincetonUniversity/athena/releases/tag/v21.0-dev>

[^4]: <https://plutocode.ph.unito.it>

[^5]: <https://github.com/danieljprice/phantom/releases/tag/v2022.0.1>

[^6]: <https://github.com/cpinte/mcfost/releases/tag/v4.1.08>

[^7]: <https://github.com/dullemond/radmc3d-2.0> (git commit ID: d80a15e)

[^8]: <https://github.com/andizq/discminer>

</paper>

Write the methods card for this paper.