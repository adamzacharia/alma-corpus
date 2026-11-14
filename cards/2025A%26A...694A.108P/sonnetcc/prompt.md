# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...694A.108P\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...694A.108P",
 "title": "The two-dimensional pressure structure of the HD 163296 protoplanetary disk as probed by multi-molecule kinematics",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Pezzotta, V.",
 "n_authors": 5,
 "arxiv_id": "2501.05517",
 "doi": "10.1051/0004-6361/202451307",
 "alma_projects_linked_by_archive": [
  "2018.1.01055.L"
 ]
}
```

Paper text:
<paper>
# The two-dimensional pressure structure of the HD 163296 protoplanetary disk as probed by multi-molecule kinematics

# Introduction

In recent years, high spatial and spectral resolution gas observations from the Atacama Large Millimeter/submillimeter Array (ALMA) have provided detailed insights into the kinematics and velocity fields of planet-forming disks (cite: pinte2023). Rotation curves (i.e., the azimuthally averaged radial profiles of the gas rotation velocity) are a direct probe of gas kinematics in protoplanetary disks, and they are crucial to improving our knowledge of several disk properties. First, the gas rotation velocity at different heights is determined by the balance between the stellar gravity, the disk self-gravity, and the pressure gradients. As a consequence, accurate rotation curves allow us to dynamically measure the fundamental properties of young star–disk systems, as stellar mass $M_\star$, disk mass $M_\text{d}$, and disk scale radius $R_\text{c}$. Dynamical masses of protostars were previously estimated by (cite: guilloteau2014; simon2017; yen2018; braun2021); dynamical measurements of $M_\text{d}$ were instead provided through rotation curves fitting by (cite: veronesi2021) for Elias 2-27, by (cite: lodato) for IM Lup and GM Aur, by (cite: martire) for the whole MAPS sample, and by (cite: andrews2024) for MWC 480. In addition, this methodology was benchmarked and further investigated with models and simulations in recent works by (cite: veronesi2024) and (cite: andrews2024). These quantities, especially $M_\text{d}$ and $R_\text{c}$, are not trivial to measure; rotation curves provide complementary accurate estimates via a methodology that is completely independent of line fluxes or continuum flux densities (cite: miotello2023). Moreover, disks are known to host both radial and vertical gradients in their temperature and density structure (cite: oberg2023), which jointly determine the pressure structure. With sets of molecular lines originating from different vertical layers, due to a range of abundances, optical depths, and excitation conditions (cite: van; aikawa; dartois; semenov; henning; dutrey), the rotation curves of these same transitions can be leveraged to extract precious information on the pressure structure of disks at different heights.

A first simple approach that we consider in this paper is to verify that the vertical and radial (2D) temperature structure estimated by other means is directly imprinted in the rotation curves of an ensemble of molecular lines spanning a wide range of vertical layers. We focus on temperature rather than density since the former is more directly determined observationally. Historically, observations of both spectral energy distributions and spatially unresolved gas lines in the far-infrared (FIR) and millimeter regimes have been successfully forward-modeled by radiative transfer and sophisticated thermo-chemical codes to infer the thermal structure of the outer regions ($>5-10$ au) of protoplanetary disks (cite: miotello2023; oberg2023). In recent years, the unique capabilities of ALMA have provided direct stringent constraints on the 2D temperature structure of disks. In particular, with high angular and spectral resolution observations, molecular emitting layers can be reconstructed using geometric arguments from channel maps (cite: pinte2018a). In the assumption of optically thick and geometrically thin emission, thermalized lines can thus be used to measure the temperature along their emission layer (cite: pinte2018a; maps4; paneque). Using a set of lines originating from different layers, it is thus possible to fit for parameterized 2D ($T(r,z)$) temperature distributions (cite: maps4; law2023; law2024; paneque).

Recently, the effect of vertical temperature gradients in rotation curves has been analyzed by (cite: martire). The authors showed that differences in the rotation velocities of and are not explainable through classical vertically isothermal disk models, but instead must be traced back to vertical stratification in temperature.

For this work we took a step forward in the analysis of gas kinematics, following a multi-molecule approach. We simultaneously analyzed the rotation velocities of seven molecular tracers emitting from a wide range of disk layers. In this way, our aim is to provide an accurate estimate of the disk mass and scale radius, based on a multi-molecule fit of the curves with a thermally stratified model. From this fit we also investigated the impact of thermal structure on gas kinematics, testing whether vertical stratification can be detected in the kinematic structure of the disk, probed through multiple tracers located at different heights above the midplane. We focused on the very bright disk of HD 163296 and selected exquisite quality multi-molecule data from the Molecules with ALMA at Planet-forming Scales (MAPS) Large Program (cite: maps1).

This paper is organized as follows. In Sect. [2](#sec:2_observations) we illustrate in detail the selected data and targeted molecular lines. In Sect. [3](#sec:3_methods) we explain the methodology we followed for our analysis. First, we discuss the extracted molecular optical depth profiles that we used as a complementary test to verify the location of the emitting layers. Then, we present the adopted routine for the rotation curves extraction; we describe the new multi-Gaussian methods we implemented to fit the hyperfine structured spectra of , and the corresponding rotation curves. We also highlight a possible observational bias in the rotation curves, arising from beam smearing in the presence of emission gaps. Finally, we describe the model including thermal stratification that we used for the multi-molecule fit of the data. In Sect. [4](#sec:4_results) we show our results from the multi-molecule fit of multiple rotation curves we performed with the thermally stratified model, and we discuss its impact on gas kinematics. From the fit, we derive dynamical estimates of stellar mass $M_\star$, disk mass $M_\text{d}$, and disk scale radius $R_\text{c}$, and we map the 2D pressure structure of the disk. We also discuss the dependence of our results on the assumed emitting surfaces. We finally draw the main conclusions of this work in Sect. [5](#sec:5_discussion_conclusions).

# Observations

## The source

In this work we focus our analysis on HD 163296: thanks to its relative proximity and massive disk, this is one of the most studied Herbig Ae star-disk systems. This protoplanetary disk presents multiple features pointing at ongoing planet formation, such as dust rings, azimuthal asymmetries, deviations from Keplerian velocities, kinks in CO emission, and meridional flows (cite: isella2016; andrews2018; isella2018; teague2019; pinte2018b; izquierdo2022). Observations in scattered light at optical and infrared wavelengths also show radial substructures (cite: rich). HD 163296 has been observed in CO and other molecular tracers at millimeter wavelengths in several single-dish and interferometric projects (cite: thi2004; degregorio-mosalvo2013; pegues2020; maps1). The HD 163296 disk is thought to be hosting two planets in formation, identified by kinematic detections, at 94 au (cite: izquierdo2022) and 260 au (cite: teague2018a; maps18; pinte2018b). HD 163296 presents extremely bright and radially extended molecular emission, which is pivotal to extract precise and accurate gas kinematics by leveraging the high signal-to-noise ratio (S/N) of specific lines.

## Targeted emission lines

To extract information on molecular gas dynamics, we based our work on the publicly available high spatial and spectral resolution data provided by the MAPS ALMA Large Program (cite: maps1). The survey investigated more than 50 emission lines from different chemical species: in Table [\[tab:lines\]](#tab:lines) we report the molecules and the corresponding emission lines that we considered for this analysis. An initial visual datacube exploration was performed for each molecule in order to select suitable lines: the candidates were chosen according to their brightness and high signal-to-noise ratio.

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| **Molecule** | **Quantum Numbers** | **Rest Frequency** | **ALMA Band** | **Resolution** |
|  |  | **\[GHz\]** |  | **\[$\prime \prime$\]** |
| $^{12}$CO | J=$2-1$ | 230.538000 | 6 | 0.15 |
| $^{13}$CO | J=$2-1$ | 220.398684 | 6 | 0.15 |
| C$^{18}$O | J=$2-1$ | 219.560354 | 6 | 0.15 |
| HCN | J=$3-2$, F=$3-2$ | 265.886434 | 6 | 0.15 |
| H$_2$CO | J$_\mathrm{K_a,K_b}$=$3_{03}-2_{02}$ | 218.222192 | 6 | 0.3 |
| HCO$^+$ | J=$1-0$ | 89.188525 | 3 | 0.3 |
| C$_2$H | N=$3-2$, J=$\frac{5}{2}-\frac{3}{2}$, F=$3-2$ | 262.064986 | 6 | 0.15 |

Table notes: For each molecule we report the quantum numbers of the transition, the emission rest frequency, the corresponding ALMA band, and the spatial resolution of the available observations.

# Methods

In this section we give an overview of the general workflow of our analysis and describe in detail the methodology we followed. Our main aim is to explore the kinematics of the HD 163296 disk through a multi-molecule approach: as different molecules emit at slightly different physical and thermal conditions, considering different emission lines is essential to trace the gas dynamics along the vertical extent of the disk. So far, HD 163296 has been kinematically analyzed through its brightest gas emission (cite: pinte2018b; teague2018a; casassus2019; maps4; maps18; izquierdo2023) – and lines; as for abundant tracers with a high signal-to-noise ratio, it is more straightforward to perform a reliable reconstruction of the emitting layer and an exhaustive kinematic analysis. In this work, we expand the extraction of rotation curves and the following kinematic considerations also to different tracers, to obtain a more complete picture of gas dynamics in the disk. We show a schematic summary of the workflow:

- To extract and fit the rotation curves with a thermally stratified model, we assume the 2D thermal structure of the disk from (cite: maps4) and the molecular emitting layers $z(R)$ from (cite: paneque). We then perform a complementary test to verify the solidity of the extracted emitting layers, given the assumed thermal structure. The validation test consists of the extraction of molecular optical depth profiles $\tau (R)$ from the data: as optical depth is easily related to the height $z(R)$, checking that we obtain reasonable $\tau$ profiles is a good way to validate the solidity of the assumed emitting layers. To extract $\tau$ profiles, we proceed as follows: we consider the temperature structure $T(R,z)$ computed in (cite: maps4) through CO isotopologs and the molecular emitting layers from (cite: paneque); we extract the molecular optical depth profiles by comparing the surface brightness profile from the data with the expected profile in case of optical thick emission, considering the full Planck law. We assess that our test provides the expected results, in agreement with optical depth estimates obtained with independent methods;

- Once we have verified that the assumed $z(R)$ are reasonable using the optical depth profiles as benchmark, we extract rotation curves from the considered molecules, taking into account the corresponding emitting layers. Considering the large uncertainties on the assumed $z(R)$ from (cite: paneque) (for the faintest lines we consider, $\Delta z/z$ can be as high as $\approx 50\%$), we also check that rotation curves are not significantly influenced by the exact location of the emitting layers, so that the lack of accuracy in $z(R)$ does not severely impact our rotation curves analysis. For the hyperfine lines in our sample (i.e., and ), we extend existing methodologies to more efficiently fit the spectra and obtain improved rotation curves. We also analyze beam smearing effects on curves, verifying that it causes deviations opposite to pressure gradients;

- We fit the obtained rotation curves all together with an extended model, including contributions from the star, the disk self-gravity, the pressure gradient and vertical thermal stratification; from this fit we obtain a dynamical estimate for stellar mass, disk mass, and scale radius. Knowing these parameters and the 2D thermal structure, we show the retrieved 2D pressure structure of the disk. Finally, we compare the predictions from the stratified model and a simple isothermal disk structure, to recover which one can best describe the differences in rotation velocity between the considered molecules. In this way, we show the impact of the pressure structure on the kinematics of molecules different from and , and the improvement induced by the implementation of the vertical stratification, with respect to the isothermal model.

## Molecular optical depth profiles

(cite: maps4) retrieved the emission layers of the three CO isotopologs - , , and - within the radial extent where they are optically thick. In the optically thick regime, the gas temperature along the emitting layers can be easily measured from the peak surface brightness of the emission lines (cite: weaver2018); thus, from the lines profiles in each pixel it is possible to extract the gas kinetic temperature along the CO surfaces, assuming LTE conditions. They fitted the obtained temperature values with the 2D parametric expression for the kinetic temperature of the gas by (cite: dullemond2020), which depends on the radius $R$ and the height above the midplane $z$: $$\begin{equation}
    T^4(R,z)=T^4_\mathrm{mid}(R)+\frac{1}{2} \left[ 1+\tanh{\left(\frac{z-\alpha z_q(R)}{z_q(R)}\right)}\right] T_\mathrm{atm}^4(R).
    \label{eq:T_law}
\end{equation}$$ Here $z_q(R)=z_0 (R/100\mathrm{\ au})^\beta$, $T_\mathrm{atm}=T_\mathrm{atm,0}(R/100\mathrm{\ au})^{q_\mathrm{atm}}$, and $T_\mathrm{mid}=T_\mathrm{mid,0}(R/100\mathrm{\ au})^{q_\mathrm{mid}}$. They fitted seven parameters using data from the three CO optically thick isotopologs: $T_\mathrm{atm,0}$, $q_\mathrm{atm}$, $T_\mathrm{mid,0}$, $q_\mathrm{mid}$, $\alpha$, $z_0$, and $\beta$. We report the best-fit parameters obtained by (cite: maps4) in Table [1](#table:law_parameters). In this work, we use the kinetic temperature by (cite: maps4) and the observed brightness temperature from the data to derive radial profiles for the molecular optical depth.

|                            |       |
|:--------------------------:|:-----:|
| *$T_\mathrm{atm,0}$* \[K\] |  63   |
|     *$q_\mathrm{atm}$*     | -0.61 |
| *$T_\mathrm{mid,0}$* \[K\] |  24   |
|     *$q_\mathrm{mid}$*     | -0.18 |
|         *$\alpha$*         | 3.01  |
|       *$z_0$* \[au\]       |   9   |
|         *$\beta$*          | 0.42  |

: Best-fit values for the seven parameters found in Eq. [\[eq:T_law\]](#eq:T_law), as fitted by (cite: maps4) through CO optically thick isotopologs.

We also consider ($3_{03}-2_{02}$), ($J=1-0$), HCN ($J=3-2, F=3-2$), and ($N=3-2, J=5/2-3/2, F=3-2$). We adopt the molecular emitting layers by (cite: paneque) into Eq. [\[eq:T_law\]](#eq:T_law), to find the kinetic temperature of the gas at the specific layers. With the obtained temperature profile, we calculate the expected surface brightness profile $I_\mathrm{Planck}$ at the emitting layer, under the assumption of optically thick emission, through the Planck law: $$\begin{equation}
    I_\mathrm{Planck}(\nu, T) = \frac{2h\nu^3}{c^2} \frac{1}{e^{\frac{h\nu}{k_\mathrm{B}T(R,z)}}-1}.
\end{equation}$$ Here $\nu$ is the rest frequency of the considered line and $T(R,z)$ is the temperature on the emitting surface computed from Eq. [\[eq:T_law\]](#eq:T_law). Then, we extract the effective surface brightness $I_\mathrm{data}$ from the data, using the GoFish (cite: Teague_GoFish) function radial\_profile, where we set a $30$° wedge along the disk major axis. At this point, we know that the two obtained profiles for the surface brightness are linked by the following relation: $$\begin{equation}
    I_\mathrm{data}(R) = I_\mathrm{Planck}(R) \left[ 1-e^{-\tau(R)}\right].
    \label{eq:tau}
\end{equation}$$ By inverting Eq. [\[eq:tau\]](#eq:tau), we can compute the optical depth radial profile $\tau (R)$ as $$\begin{equation}
    \tau(R) = - \ln{\left(1-\frac{I_\mathrm{data}(R)}{I_\mathrm{Planck}(R)}\right)}.
\end{equation}$$

![](images/HD_163296_tau.pdf)

In Fig. [1](#fig:tau_profiles) we show the optical depth profiles of , , HCN, and we obtained following this method. We calculated uncertainties on the $\tau$ profiles (shaded profiles in Fig. [1](#fig:tau_profiles)) propagating the errors on the extracted surface brightness. Uncertainties are generally larger for and , the two lines with lower resolution data ($0.3''$).

First of all, we observe that and lines result in an optically thin emission along the whole radial extent of the disk, reaching maximum peaks at $\tau \sim 0.11$ and $\tau \sim 0.45$ respectively. emission becomes marginally thick, with a value for $\tau$ approaching to 1, at the radii corresponding to intensity peaks. HCN emission is mostly optically thick within $\sim 130$ au, with higher values in the inner $\sim 60$ au and a local maximum around the radius of the intensity peak ($R=109$ au); it then evolves into optically thin emission, with $\tau$ decreasing by an order of magnitude. As expected, and HCN result in a marginally thick emission at the rings locations, as previously observed in other disks (cite: maps1; oberg2023). We also find that in the innermost tens au we measure a general decrease of the optical depth for all the molecules. This decrease is an observational artifact and is due to the beam dilution effect (cite: weaver2018): at smaller scales, the beam size may be larger than the spatial dimension of the considered emitting region of the disk. As a consequence, the measured surface brightness is underestimated by a beam dilution factor, proportional to the ratio of the emitting area to the beam size (lower than 1 at small radii).

The obtained estimates for $\tau$ are compatible with existent optical depth values measured for the same molecules in this (cite: maps11) and other disks (cite: bergner2019; facchini2021), and are in line with the expected optical depth values that can be retrieved from column density profiles in (cite: maps6) and from the brightness temperature profiles computed by (cite: paneque) for HD 163296. Therefore, the consistent results of this preliminary test guarantee that, given the thermal structure for the disk by (cite: maps4), the emitting layers by (cite: paneque) are suitable for the rotation curves extraction. Considered the large errors on the assumed molecular emitting layers, we also verified that the rotation curves obtained with eddy are not significantly affected by the emitting layers choice, varying them within the given uncertainties. Thus the assumed layers are suitable to extract reliable curves, without the need to rely on deeply accurate measurements of $z(R)$, whose extraction procedure shows high systematic uncertainties and is thus intrinsically difficult.

Finally, we note that this is an efficient and straightforward method to easily extract optical depth and column density profiles of the considered line, relying only on thermal structure $T(R,z)$ and emitting height $z(R)$ of one single transition. This is an independent method that does not require complicated chemical studies about excitation temperatures and represents a valid alternative to approaches applied to hyperfine lines (cite: maps6) for systems where a precise and accurate 2D temperature structure is known.

## Rotation curves extraction

Once we have verified with the optical depth complementary test described in the previous section that the assumed emitting layers are consistent, we proceed to the rotation curves extraction. In order to extract the velocity radial profiles of the HD 163296 disk, we used the eddy Python package (cite: teague_eddy), following the method presented in (cite: teague2018a) and (cite: teague2018b). First of all, we have to know the geometry of the disk (i.e., inclination $i$, position angle $PA$, possible disk center offsets in declination and right ascension) and the emitting layers of each considered molecule, to deproject the data from projected location in the sky to disk-frame coordinates. We assumed $i=46.7$°, $PA=313.3$° from (cite: maps1) (the $PA$ is shifted by $180$° according to its definition in eddy) and center offsets equal to zero. For the molecular emission layers we assumed an exponentially tapered power law $$\begin{equation}
    z(R) = Z_0 \left(\frac{R}{100\text{au}}\right)^\phi \exp\left[-\left(\frac{R}{R_{\mathrm{taper}}}\right)^{\psi}\right],
\end{equation}$$ with best-fit values by (cite: paneque), listed in Table [2](#table:emitting_layers), for $Z_0, \phi, r_{\mathrm{taper}}$, and $\psi$. In addition, we also performed our analysis adopting nonparametric emitting layers for all the molecules, and we show the results we obtained in Appendix [10](#app:nonpar_layers). In Sect. [4.2](#subsec:layers_dependency) we discuss these results, showing how the choice of using parametric emitting surfaces for the considered lines has no substantial effect on the qualitative results and trends we obtain from our analysis.

|  | **$Z_0$ \[au\]** | **$\phi$** | **$r_{\mathrm{taper}}$ \[au\]** | **$\psi$** |
|:--:|:--:|:--:|:--:|:--:|
| **$^{12}$CO** | 25.08 | 1.35 | 426.44 | 4.21 |
| **$^{13}$CO** | 11.88 | 1.4 | 343.88 | 5.36 |
| **C$^{18}$O** | 6.02 | 1.47 | / | / |
| **H$_2$CO** | 19.2 | 1.0 | 462.85 | 0.07 |
| **HCO$^+$** | 6.45 | 0.59 | / | / |
| **HCN** | 8.45 | 2.14 | 342.11 | 3.75 |
| **C$_2$H** | 38.13 | 5.41 | 95.38 | 3.78 |

: Best-fit parameters for the molecular emitting layers for HD 163296 fitted by (cite: paneque).

Table notes: For C$^{18}$O and HCO$^+$ a simple power law is assumed as parameterization for the emitting layer, so only $Z_0$ and $\phi$ are reported.

We note that taking into account the molecular emitting layers in the data deprojection does not influence the extracted curves in a dramatic way, for molecules emitting close to the midplane. Especially we are interested in testing the molecules with lower S/N emission, for which it is more difficult to extract reliable rotation curves (i.e., ). To test this, we computed the rotation curves of these molecules assuming flat emission (i.e., originating at the disk midplane) and we obtained that the differences between the two scenarios are compatible with zero within: $0.6\sigma$ for , $4.5\sigma$ for (and $3\sigma$ for ). For thoroughness, we did the same test for all the molecules: as expected, for the other lines the discrepancy is above $6\sigma$, as these molecules are well known to emit from very elevated layers. For every line, we show the difference between the extracted rotation curves in case of flat and elevated emission in Fig. [11](#fig:flat_emission_diff). We also note that the curves would be even more compatible if we had more realistic estimates for the uncertainties on the rotation curves, as the errors on the curves are underestimated, as we explain in Sect. [4.1](#subsec:multimol_fit). This test guarantees a reliable extraction of rotation curves for lower S/N lines emitting close to the midplane, even if the available parameterizations for their emitting heights have large uncertainties, without affecting the quality of the results. In Sect. [4.2](#subsec:layers_dependency) we show the results on the stellar and disk parameters we obtain from the multi-molecule fit of the rotation curves in case of flat emission for all the considered molecules.

To extract the rotation curves, we used the *SHO (Simple Harmonic Oscillator)* method in eddy, that assumes axisymmetric disks. Following this approximation, emission line spectra that arise from the same radial distance from the disk center are expected to exhibit the same profile, as they trace the same physical and chemical conditions. The line centroids are expected to be shifted by $v_\theta \cos(\theta)$, an offset with respect to the systemic velocity due to the azimuthal location of the emission in the disk ($\theta$ represents the polar angle, measured from the redshifted major axis). With this method, the best-fit rotation velocity at a specific radius is determined as the one that best aligns the deprojected spectra from the same annulus. Mathematically, we fit the set of line centroids of the same annulus with a cosine function. In order to align the spectra, in our analysis we fit each spectrum with a Gaussian curve to identify the intensity peak and the corresponding velocity, and then we proceed to the fit of the line centroids with the harmonic function. For each tracer we repeat the extraction of the rotation curve $20$ times, considering different independent samples of spectra inside each annulus for different iterations and we compute the uncertainties on the velocity values as their weighted standard deviation. A similar approach is followed in (cite: maps18) to extract the rotation curve for the HD 163296 disk with GoFish: in that case, the best-fit velocity values are selected as those that best align the spectra, as quantified by fitting a Gaussian processes mean-model to the averaged spectra.

If we want to consider also the radial contribution to the line-of-sight velocity $v_{\mathrm{los}}$, in eddy we can fit the azimuthal and radial velocities together, and fitting every set of line centroids with a double harmonic oscillator. We note that for molecules other than the CO, the MAPS quality of data is not sufficient to provide reliable kinematical estimates of the radial and vertical velocity components. Nevertheless, in our analysis we are interested in the azimuthal velocity profiles. We decided not to focus on $v_R$ and $v_z$, considering them negligible with respect to the difference in azimuthal velocities between data and an axisymmetric model, as shown by (cite: teague2019) and (cite: izquierdo2023).

### Limitations of the method

As explained in Sect. [3.2](#subsec:curves_extraction), the extraction of rotation curves is based on the identification and fit of line centroids in each pixel of the data cube. Besides requiring a high signal-to-noise ratio, this methodology relies on a few assumptions. First, we assumed that the disks are azimuthally symmetric and that the spectra along each annulus vary only by a phase $\cos \theta$, but maintain the same profile. This hypothesis might be inadequate for highly perturbed line emission morphologies. Second, eddy does not distinguish the upper and lower surfaces of disks, and assumes that the front side dominates over the back side. However, an important contamination from the back side of the disks can complicate the spectra alignment and so the goodness of the fit. In some cases (such as GM Aur in the MAPS sample, see (cite: lodato)) the signals arising from the two surfaces are comparable and thus the procedure results in a quite inefficient alignment of the spectra. In these cases, the lower surface can shift the line centroids in the observed intensity spectra, inducing a wrong derivation of the best-fit velocities. We note that the level of contamination from the back side depends on the considered disk and molecule: for example, line emission coming from lower layers is generally less contaminated by the back side with respect to the emission from the upper layers, since its emission surface is closer to the disk midplane (cite: lodato).

To quantify the effects of these limitations on our analysis, we quantitatively compared the rotation curves we extracted with eddy with the ones obtained by (cite: martire) with the `discminer` tool (cite: izquierdo2021) for and , considering also the back side of the disk. We measure very low differences, which are $<4\%$ for and $<5\%$ for , confirming that the limitations of this method are not our primary source of systematic effects.

### Multi-Gaussian methods for hyperfine transitions kinematics: C$_2$H and HCN rotation curves

In this work, we developed a new method to extract rotation curves from molecules that have hyperfine transitions. In fact, in our analysis molecules such as C$_2$H and HCN do exhibit a hyperfine structure (see Table [\[tab:lines\]](#tab:lines) for details about the transitions). Hyperfine structure is typically characterized by energy shifts that are orders of magnitude smaller than fine-structure ones. Therefore, for these molecules, it is possible to detect two (or more) emission lines in the same frequency channel (i.e., in the same channel map).

Typically, a spectrum from molecules with hyperfine lines shows two or more different intensity peaks (one for each transition) instead of one, as clearly shown by teardrop plots in Fig. [2](#fig:teardrops), where the color scale represents the averaged intensity of the considered emission line along separate annuli. The intensity of each visible transition depends on its Einstein coefficient: for , in each spectral channel we see two similar transitions, roughly equal in intensity. This reflects in double-peaked spectra with two maxima at the same intensity. For HCN, instead, we can clearly detect a central dominant transition, which is the strongest one, alongside with two fainter lines nearly of the same intensity. Therefore, the standard extraction methods (that fit a quadratic or Gaussian function to the spectrum) are not adequate to fit these multi-peaked spectra, and they fail to return reliable velocity profiles.

![image](images/C2H_teardrop.pdf) ![image](images/HCN_teardrop.pdf)

For this reason, we implemented in eddy a new fitting procedure for hyperfine lines using multiple Gaussian components (two or three, depending on the number of hyperfine transitions), where the width of the multiple Gaussians is assumed to be the same, as the hyperfine components are expected to emit under the same conditions of temperature, density, and turbulence.

For , we fit each spectrum with a double-Gaussian function $$\begin{equation}
    I = I_0\ \exp \left[{\left( \frac{v-v_0}{\sigma}\right) ^2}\right] + I_0 \ \xi \ \exp \left[ {\left( \frac{v-(v_0-\Delta v)}{\sigma}\right) ^2}\right],
\end{equation}$$ where $\xi$ is the ratio of the two intensity peaks and $\Delta v$ is the velocity difference between the two transitions. We fit four free parameters: the center of the Gaussian $v_0$, which represents the line centroid, the width of the Gaussians $\sigma$, the intensity corresponding to the first peak $I_0$, and the peak intensity ratio $\xi$.

For , we fit each spectrum with a triple-Gaussian function $$\begin{equation}
\begin{split}
    I = &\ I_0 \ \xi_\mathrm{blue}\ \exp \left[{\left( \frac{v-(v_0-\Delta v_\mathrm{blue})}{\sigma}\right) ^2}\right] + I_0\ \exp \left[{\left( \frac{v-v_0}{\sigma}\right) ^2}\right] \\ 
    &+ I_0 \ \xi_\mathrm{red} \ \exp \left[ {\left( \frac{v-(v_0+\Delta v_\mathrm{red})}{\sigma}\right) ^2}\right],
\end{split}
\end{equation}$$ where $\xi_\mathrm{blue}$ ($\xi_\mathrm{red}$) is the ratio of the blueshifted (redshifted) intensity peak to the central dominant peak and $\Delta v_\mathrm{blue}$ ($\Delta v_\mathrm{red}$) is the velocity difference between the central and the blueshifted (redshifted) peak. In this case we fit five free parameters: the center of the middle Gaussian $v_0$, which represents the line centroid, the width of the Gaussians $\sigma$, the intensity corresponding to the central peak $I_0$, and the peak intensity ratios $\xi_\mathrm{blue}$ and $\xi_\mathrm{red}$.

The velocity shifts $\Delta v$ (between the two hyperfine lines), $\Delta v_\mathrm{blue}$, and $\Delta v_\mathrm{red}$ (between the weaker hyperfine lines and the central one of HCN) are fixed parameters, given the known frequency shifts $\Delta \nu = 2.5$ MHz (between the two transitions), $\Delta \nu_\mathrm{blue} = 2.09$ MHz, and $\Delta \nu_\mathrm{red} = 1.54$ MHz (between the HCN transitions) as taken from *the Cologne Database for Molecular Spectroscopy (CDMS)* ((cite: sastry1981; muller2000) for and (cite: ahrens2002) for HCN). We set priors for some parameters:

- Intensities must be positive: $I_0,\ \xi,\ \xi_\mathrm{blue},\ \xi_\mathrm{red} >0$;

- $\xi \in [0.2,\ 1.5]$ for and $\xi_\mathrm{blue},\ \xi_\mathrm{red} \in [0.1,\ 1.]$ for HCN: we choose a reasonably large interval centered on the expected value for the ratio between the intensity peaks, considering the Einstein coefficients and upper state degeneracies of the considered transitions ($\xi \sim A_{ij}^1g_1/A_{ij}^2g_2 \approx 0.65$ for and $\xi \sim A_{ij}^1g_1/A_{ij}^2g_2 \approx 0.13$ for HCN);

- $\sigma \in [0,\ \Delta v /2]$ for and $\sigma \in [0,\ \Delta v_\mathrm{blue} /2]$ for HCN: the width of the Gaussians is not larger than half of the distance in velocity between the two considered transitions, as the expected thermal broadening of the line is below $\sim 1$ km/s (cite: izquierdo2023) and thus much smaller than $\Delta v$.

For , we set reasonable starting positions for the parameter space exploration, to ease the convergence of the fit. In particular, we computed the Keplerian velocity at each radius $R$ and azimuthal angle $\theta$ as $$\begin{equation}
    v_{\mathrm{rot, K}} = \Biggl(\frac{GM_{\filledstar}}{R}\Biggr)^{1/2} \sin i \ \cos \theta + v_\mathrm{sys},
\end{equation}$$ where $M_{\filledstar}$ is the stellar mass computed fitting the curve with a Keplerian model, and used it as starting position for the line centroid $v_0$ fit.

In Fig. [3](#fig:hyper_spectra) we show the fit of the hyperfine spectra of both and HCN with, respectively, the double- and triple-Gaussian methods, compared to the single-Gaussian one originally implemented in eddy. These methods lead to a remarkable improvement in the extraction of the rotation curves of hyperfine structured lines. In Fig. [4](#fig:hyperfine_curves), for both molecules we show the comparison between the rotation curve extracted with the multi-Gaussian method and the curve previously obtained with the single-Gaussian method already implemented in eddy.

![image](images/gau_vs_doublegau_fit.pdf) ![image](images/gau_vs_triplegau_fit.pdf)

![image](images/C2H_curve_cfr_singlevsdouble.pdf) ![image](images/HCN_curve.pdf)

These methods prove very efficient in fitting the multi-peaked spectra in both cases. For , the remarkable upgrade in the peak fitting procedure leads to the most significant improvement in the azimuthal velocity profile: fitting the spectra with a double-Gaussian, we obtain a smooth curve with small errors, a more reliable result than the one obtained using a single-Gaussian. In that case, since the two peaks in the spectra are mostly equal in intensity, a single-Gaussian model leads to a fragmented curve affected by high variance. For HCN, by fitting three Gaussian components to each spectrum we maximize the exploitation of the available data, taking into account also the two minor intensity peaks. Nevertheless, the two curves do not differ substantially and the observed differences in the selected radial range are small: as the central peak is dominant, also the standard single-Gaussian method, even if less accurate than the triple-Gaussian, could still fit the central prominent peak providing the correct value of the line centroids, neglecting the hyperfine splitting visible in the two minor peaks.

### Beam smearing effect

Among the considered molecules, and HCN show strong intensity gradients in their emission. Since the extraction of velocity profiles comes from molecular line emission, the presence of gradients in the emission intensity of these lines can affect the corresponding rotation curves. In Fig. [5](#fig:anticorr), we show these observational effects for ; we show the same effect for HCN in Appendix [7](#app:HCN).

We find a strong anticorrelation between the two following measurable quantities as a function of radius (evaluated at the same radii), in agreement with the results from (cite: keppler2019):

- $\dd\ {(\int{Idv})}/\dd{R}$: the intensity gradient of molecular emission line, computed from the radial intensity profile[^1];

- $v_\mathrm{C_2H}-v_{\mathrm{^{12}CO}}$: the difference between the rotation velocities of and $^{12}$CO (shown separately in panel (b) of Fig. [5](#fig:anticorr)). In this case, the $^{12}$CO curve was chosen as reference because it exhibits a typical smooth Keplerian profile, and it does not show any strong gradient in the intensity radial profile.

These two quantities display an opposite modulation, as shown in panel (c) of Fig. [5](#fig:anticorr). In particular, the difference in rotation velocity $v_{\ce{C2H}}-v_{\ce{^12CO}}$ is positive at the inner edge of an emission gap, while it becomes negative at its outer edge. This effect is shown in the comparison between the curves reported in panel (b) of Fig. [5](#fig:anticorr).

![](images/HD_C2H_anticorr_whole.pdf)

This particular modulation can be explained by a beam smearing effect. When a source is observed at a given angular resolution, every extracted spectrum is the intensity weighted average of all the spectra that fall inside the beam area. For this reason, a strong intensity gradient across the beam would bias the recovered spectrum and, consequently, the extracted velocity. In our results we are biased to see velocities corresponding to higher intensity values inside the beam, that do not correspond to the beam center. For instance, in correspondence of the inner edge of the emission gap we are affected by a strong negative intensity gradient. So in this region, the extracted spectrum weighs more the velocities corresponding to the higher intensities, which are the ones from the inner radii, and we measure an artificially higher rotation velocity. On the contrary, at the outer edge of the emission gap the strong intensity gradient is positive, and velocities corresponding to the outer radii are weighted more and we measure an artificially lower rotation.

Beam smearing can also explain the flattening at small radii we see in the rotation curve in panel (b) of Fig. [5](#fig:anticorr), since this molecule shows a central cavity in emission, followed by an intensity peak. In the internal cavity, the signal inside the beam is dominated by the higher intensities found at larger radii: as a consequence, we measure lower velocities in correspondence of the cavity, leading to a flattening of the curve.

This observational effect has important consequences: we have observed that beam smearing triggers apparent velocity deviations in rotation curves, that are linked to strong intensity gradients of the emission line. Nevertheless, if any substructure (such as rings or gaps) is present in the gas surface density, then also the pressure profile undergoes alterations induced by the change in density, causing similar velocity deviations. Therefore, it is important to distinguish rotation curve modulations that are due to this observational bias from effective deviations linked to pressure gradients, that could be signs of the presence of gas density substructures. However, we note that beam smearing works in an opposite way to pressure gradients, as we show in Fig. [6](#fig:sketch_beam_smearing): assuming that intensity peaks trace pressure peaks (and analogously with gaps), pressure gradients are expected to induce velocity deviations that are of opposite sign with respect to the ones deriving from intensity gradients that we observe. This means that the apparent difference in velocity induced by beam smearing in correspondence of an intensity gap could be incorrectly interpreted as a pressure maximum, not as a pressure gap as expected if intensity and pressure peaks correspond. Conversely, if we observe kinematic evidence of a pressure gap in correspondence of an intensity gap, we can immediately conclude that it cannot have been artificially generated by beam smearing, since this effect would have induced the opposite behavior (and analogously for a pressure peak). This different impact that beam smearing and pressure gradients have on rotation curves may help distinguish these effects; nevertheless, this may be not straightforward, since both of them can be present and influence data in different ways.

![](images/sketch_beam_smearing_arrows.pdf)

## Vertically stratified model

We extract and analyze multiple molecular lines emitting from different layers to investigate how disk kinematics is affected by height above the midplane across the vertical extent of the disk. Recent high resolution gas observations have shown differences in the rotation velocity of the CO isotopologs, that could not be correctly explained with simple vertically isothermal disk models. In (cite: martire), the authors show that a thermal stratified model can better explain the velocity discrepancies between the and rotation curves, and that vertical stratification should be considered when building a solid model to adequately describe them. Therefore, we choose to simultaneously fit our seven rotation curves including the contribution from vertical thermal stratification, in order to provide a complete picture of the several contributions that can affect the disk kinematics. From this fit we derive dynamical estimates for the disk and stellar masses, and the disk scale radius; we also compare our results with a simple vertically isothermal model, showing that it is not adequate to describe the complexity of the data.

We consider a disk surface density as described by the self-similar solution of (cite: lyndenbell): $$\begin{equation}
\label{eq:surf_density}
    \Sigma = \frac{(2-\gamma)M_\text{d}}{2\pi R_\text{c}^2} \Bigg(\frac{R}{R_ \text{c}}\Bigg)^{-\gamma}\exp\Bigg[-\Bigg(\frac{R}{R_\text{c}}\Bigg)^{2-\gamma}\Bigg].
\end{equation}$$ Here $M_\text{d}$ and $R_\text{c}$ are the disk mass and the scale radius, $R$ is the cylindrical radius, and $\gamma$ is the index that describes the steepness of the surface density (we adopt $\gamma=1$). On the midplane we have that the temperature can be described by a power law as $T_\mathrm{mid}(R) \propto R^{\ q_\mathrm{mid}}$ and consequently the sound speed is $c_{\text{s, mid}} \propto \sqrt{T_\text{mid}} \propto R^{\ q_\mathrm{mid}/2}$. To account for the thermal vertical stratification of the disk, following the method and parameterization described in (cite: martire), we can define two functions $f$ and $g$ that determine the vertical dependence of the disk temperature, sound speed, and density: $$\begin{gather}
    \label{eq:temp} T(R,z)=T_\text{mid}(R)f(R,z),\\ \label{eq:cs} c_\text{s}^2(R,z)=c_{\text{s, mid}}^2(R)f(R,z), \\ \rho(R,z)=\rho_\text{mid}(R)g(R,z).
\end{gather}$$ As a consequence, considering a barotropic fluid, the 2D pressure in the disk is given by $$\begin{equation}
    \label{eq:pressure} P(R,z)=P_\text{mid}(R)f(R,z)g(R,z) = c_{\text{s, mid}}^2(R) \rho_\text{mid}(R)fg(R,z).
\end{equation}$$ We note that $g(R,z)$ is a function that only depends on $f(R,z)$ as a consequence of the hydrostatic equilibrium (see (cite: martire)).

We adopt the model for our rotation curves fit from (cite: martire), given by $$\begin{equation}
\label{eq:rotationcurve_strat}
\begin{split}
    v_\theta^2(R,z) = &v_\text{k}^2 \left\{ \left[1+\left(\frac{z}{R}\right)^2\right]^{-3/2} - \left[ \gamma^\prime + (2-\gamma)\left(\frac{R}{R_\mathrm{c}}\right)^{2-\gamma} \right. \right. \\
    &\left. \left. - \frac{\text{d}\log(fg)}{\text{d}\log R}\right]\left(\frac{H}{R}\right)_\text{mid}^2 f(R,z) \right\} \\
    &+ G \int^\infty_0 \Bigg[K(k) - \frac{1}{4}\Bigg(\frac{k^2}{1-k^2}\Bigg)\times \\
    &\Bigg(\frac{r}{R}-\frac{R}{r}+\frac{z^2}{Rr}\Bigg) E(k)\Bigg]\sqrt{\frac{r}{R}} k\Sigma(r) \,dr,
\end{split}
\end{equation}$$ where $v_\text{k}=\sqrt{GM_\star/R}$ is the Keplerian velocity, $\gamma^\prime = \gamma + (3+q)/2$, $r=\sqrt{R^2+z^2}$ is the spherical radius, $K(k)$ and $E(k)$ are complete elliptical integrals (cite: abramowitz), and $k^2=4Rr/[(R+r)^2+z^2]$. In this expression we can distinguish the different contributions of the stellar gravity, the pressure gradient, the thermal stratification (the term depending on $f$ and $g$), and the self-gravity (cite: bertin). For further details on this model, see (cite: martire). The adopted expression for the isothermal model is explained in (cite: lodato), Eqs. 12-14.

To perform the simultaneous fit of the rotation curves, we use the code DySc[^2]: given the data, the thermal structure of the disk, and the geometry of the emitting layers, the code performs the fit of the data to the model by maximizing the likelihood of the model, with the posterior distribution explored by Monte Carlo Markov Chains, as implemented in emcee[^3]. As output, we obtain the probability distributions of the fitted parameters, their best-fit values, and corresponding uncertainties. We implemented the possibility to fit multiple ($>2$) rotation curves in the code. We fit our seven rotation curves obtained from data with a single model for the rotation velocity described in Eq. [\[eq:rotationcurve_strat\]](#eq:rotationcurve_strat). From this multi-molecule fit, we can extract accurate best-fit values for some fundamental parameters: stellar mass $M_\star$, disk mass $M_\text{d}$, and scale radius $R_\text{c}$.

# Results and discussion

## Multi-molecule fit with thermal stratification: dynamical estimates and pressure structure

We extended the code DySc to perform a multi-molecule fit with seven different molecules and we fitted the obtained molecular rotation curves simultaneously with one single model, including contributions from the stellar and the disk gravity, the pressure gradient and thermal stratification, as described by Eq. [\[eq:rotationcurve_strat\]](#eq:rotationcurve_strat). We ran the MCMC exploration using 200 walkers, 1000 burn-in steps and 2000 steps to determine the final posterior distribution of the fitted parameters. To evaluate the contributions of vertical structure, we took into account the molecular emitting layers found by (cite: paneque). For the thermal structure to use in our fit, we considered the parameterization for the temperature presented by (cite: dullemond2020) and reported in Eq. [\[eq:T_law\]](#eq:T_law), with the parameters obtained by (cite: maps4) reported in Table [1](#table:law_parameters). In this work we did not account for the uncertainties in the temperature structure of the disk. (cite: andrews2024) analyzed the systematic uncertainties driven by the disk thermal structure, with related uncertainties that are of the same order of surfaces mis-specifications.

We report the multi-molecule fit in Fig. [7](#fig:multimolecular_fit): we show the fit of each molecular rotation curve with the recovered best-fit model. It is clear that the model well reproduces the seven curves, with the exception of a short range of radii in around $R \sim 150$ au: in a short interval around this radius, which represents an emission gap for , the reconstruction of the rotation curve with eddy is not accurate, since the signal-to-noise ratio is too low to allow an efficient extraction of the rotation velocity (see Appendix [8](#app:H2CO) for further details). As for HCN and , the differences with respect to the model are due to the apparent deviations in the rotation curves caused by beam smearing, as explained in Sect. [3.2.3](#subsec:beam_smearing). It is important to note that the inclusion of several molecules different from the CO isotopologs, with their corresponding emitting heights, does not hinder the successful outcome of the fit, but rather it contributes to its accuracy.

The uncertainties on the rotation curves are very small: this is an underestimate as we are taking into account only the statistical errors on the values, but no systematic errors. To provide a more exhaustive estimate of the uncertainties, it would be necessary to implement in eddy the systematic component of the errors on the derived rotation curves associated with the uncertainty on the geometrical parameters of the disk (inclination, position angle, and centering), the thermal structure, and the molecular emitting layers. (cite: andrews2024) discuss an efficient way forward in the determination of systematic uncertainties in kinematic measurements.

![image](images/fit_7mol_12CO.pdf) ![image](images/fit_7mol_13CO.pdf) ![image](images/fit_7mol_C18O.pdf) ![image](images/fit_7mol_HCO.pdf) ![image](images/fit_7mol_H2CO.pdf) ![image](images/fit_7mol_HCN.pdf)

![](images/fit_7mol_C2H.pdf)

From the multi-molecule fit, we are able to find the best-fit values for the stellar mass $M_\star$, the disk mass $M_\text{d}$, and scale radius $R_\text{c}$. We note the potential of detailed kinematical analysis in extracting dynamical estimates of these crucial quantities, whose estimate may be very difficult with other methods. For each parameter, we compute a 95% credibility interval (that is the Bayesian counterpart of the confidence level) as the range of values that contains 95% of the probability density in the posterior distribution and we consider the extremes of these intervals as estimates of the best-fit parameters uncertainties. We summarize the best-fit values we obtained from the multi-molecule fit, including the thermal stratification contribution, in Table [3](#table:dyn_estimates); for completeness, we report the corresponding corner plots in Appendix [\[app:cornerplot\]](#app:cornerplot). We compare these estimates with the values extracted from a multi-molecule fit, this time assuming an isothermal temperature profile $T(R) \propto R^{\ q}$ with $H/R=0.084$ and $q=-0.84$ (cite: maps5). We also compare our results with the ones obtained by (cite: martire): the authors retrieve the rotation curves using `discminer` [^4], and use only and for the fit, including thermal stratification contribution.

|  |  |  |  |
|:--:|:--:|:--:|:--:|
|  | stratified - 2 mol | stratified - 7 mol | isothermal - 7 mol |
|  | (cite: martire) | (this work) | (this work) |
| **M$_\filledstar$** \[M$_\odot$\] | $1.948 \pm 0.002$ | $1.8905 \pm 0.0002$ | $1.8905 \pm 0.0002$ |
| **M$_\mathrm{d}$** \[M$_\odot$\] | $0.134 \pm 0.001$ | $0.1161 \pm 0.0003$ | $0.1565 \pm 0.0003$ |
| **R$_\mathrm{c}$** \[au\] | $91 \pm 1$ | $143.1 \pm 0.1$ | $48.1 \pm 0.1$ |

: Comparison of best-fit values.

Table notes: Comparison between best-fit values for $M_\star$, $M_\text{d}$, and $R_\text{c}$ with the corresponding uncertainties obtained by (cite: martire) and from this work, with the thermally stratified and the isothermal models.

We note that in our work the estimate of the stellar mass does not change between the isothermal and stratified fits, while the disk mass appears slightly lower in the second scenario. What changes the most is the disk scale radius, as expected: in the isothermal case, we obtain $R_\mathrm{c}=48.1$ au, a very low value for the scale radius and a clear sign that we are probably underestimating it. On the contrary, with the thermally stratified model we provide a more accurate characterization of the thermal structure of the disk and this leads to $R_\mathrm{c}=143.1$ au. This value is more consistent with the best-fit estimates of $R_\mathrm{c}$ obtained with complementary methods by (cite: degregorio-mosalvo2013) and (cite: maps5). When comparing our results for the thermally stratified scenario with the ones from (cite: martire), we find that they obtain slightly higher values for both the stellar and the disk masses, and a lower estimate of the disk scale radius. We point out that the fitting procedure in the two works is the same; the main differences are represented by the rotation curves to fit (the authors use `discminer` by (cite: izquierdo2021) to extract the velocity profiles, while we use eddy) and the number of considered emission lines (they use and while we use seven different molecules). We also observe that we obtain uncertainties on the best-fit parameters that are an order of magnitude smaller than the ones obtained by (cite: martire). This is understandable considering that eddy and `discminer` are based on different methods to provide rotation curves, so we do not expect to obtain the same order of magnitude for the uncertainties a priori. Error bars on the determined velocity values affect the simultaneous fit performed on the curves with DySc: as we are underestimating the uncertainties on the rotation curves with eddy, consequently we obtain low estimates of the errors on the best-fit parameters.

To emphasize the importance of the multi-molecule approach, we fitted the rotation curves starting with two molecules and then progressively adding one molecule at a time. All the fits were performed with the same number of walkers, burn-in steps, and steps (200, 1000, 2000). To quantify the goodness of the fit, we show in Fig. [8](#fig:chi2) the $\chi^2_\text{red}$ obtained from all the fits, increasing one by one the number of fitted molecules. We normalized the $\chi^2_\text{red}$ to the maximum value, since the uncertainties on the extracted rotation curves are systematically underestimated (as explained above in this section).

![](images/chi2_7mol.pdf)

As we can see from Fig. [8](#fig:chi2), the most significant improvement is achieved with the inclusion of in the fit, going from two to three molecules. This addition also induces the largest improvement in the dynamical estimates of the disk mass and scale radius: the values we obtain by fitting two and three molecules differ by $\lesssim 10\%$ and $\lesssim 6\%$ respectively for $M_\text{d}$ and $R_\mathrm{c}$. Moreover, the $\chi^2_\text{red}$ keeps decreasing with the further inclusion of lines in the multi-molecule fit. We added as last, since their rotation curves are the most affected by the beam smearing effect, as shown in Sect. [3.2.3](#subsec:beam_smearing). We also found that the width of the posterior distribution shrinks as expected when fitting more rotation curves together, but our error bars on the velocity profiles are so small that they are still dominated by the systematics.

Knowing the disk mass and scale radius from the multi-molecule fit, and considering the thermal structure of the disk by (cite: maps4), we can show the normalized 2D pressure structure of the disk in Fig. [9](#fig:pressure_plot), following Eq. [\[eq:pressure\]](#eq:pressure). We note that the shape of the $P(R,z)$ profile is given by the assumed disk temperature $T(R,z)$, while the normalization term $P_\mathrm{mid}(R)$ is determined by the values for the disk mass and scale radius obtained by the fit of the rotation curves. We also show the location of the emitting layers of the tracers considered in the disk: the selected molecules probe the 2D pressure structure of the disk across its $(R,z)$ extent, from the upper surface down to the midplane.

![](images/pressure_plot_Pa.pdf)

(cite: martire) showed that thermal stratification plays an important role in explaining the discrepancies between and rotation curves. To do so, they compute the difference in the squared rotation velocities of the two molecules, with a proper normalization; this quantity strongly depends on the different heights of the tracers, and it is thus very useful to assess the relevance of thermal structure in disks. Hence, they show the expected behavior of this quantity according to both the isothermal and the stratified models, to see which one can better reproduce the observed data. In this work, we perform the same calculation for all the considered molecules at different emitting heights, using our multi-molecule stratified model, to establish if thermal stratification has a strong impact on gas kinematics across the vertical extent of the disk. We compare squared rotation velocities of each molecule with the one, and we illustrate the expected behavior of their normalized difference in the isothermal and in the vertically stratified scenarios. We show in Fig. [10](#fig:vel_diff_C18O) the results we obtained for , while in Appendix [11](#app:vel_diff_others) we report the results for the other five molecules.

![](images/hd163296_diff_7mol_C18O.pdf)

From our results, it is clear that the thermally stratified prediction is more appropriate to describe the observed differences between the two rotation curves, while the isothermal model cannot reproduce the observed behavior. We observe that the effect of thermal stratification is important also in the lower layers located closer to the disk midplane, as shown in Figs. [10](#fig:vel_diff_C18O) and [17](#fig:vel_diff_others). Temperature leaves a clear imprint in the kinematics of molecular lines originating from the whole vertical extent of the disk, in the upper layers (as proved by (cite: martire)) and in the layers close to the midplane. Once this is included in the model, this further large-scale modification to the pressure can be distinguished and measured efficiently.

Considering Fig. [10](#fig:vel_diff_C18O), we point out that the difference in rotation velocity between the two isotopologs increases with radius and then starts decreasing at $\sim 200$ au; this trend is well reproduced by the stratified model, contrarily to the isothermal one. This discrepancy between the two models we considered for the rotation curves lies in the pressure gradient term, which includes an additional contribution depending on the height above the midplane when accounting for thermal vertical structure: $$\begin{equation}
\begin{aligned}
    \frac{R}{\rho}\frac{dP}{dR}(R,z) 
    
    &= -v_\text{k}^2 \left[ \gamma^\prime + (2-\gamma)\left(\frac{R}{R_\mathrm{c}}\right)^{2-\gamma} - \right. \\
    &\quad\left. - \frac{\text{d}\log(fg)}{\text{d}\log R}\right]\left(\frac{H}{R}\right)_\text{mid}^2 f(R,z).
\end{aligned}
\end{equation}$$ In particular it can be verified that, for the thermal structure we assumed (i.e., the selected functions $f$ and $g$ in Eqs. [\[eq:temp\]](#eq:temp), [\[eq:cs\]](#eq:cs)), this term remains negative across the whole radial extent of the disk and it decreases faster for than for as a function of radius, up to $\sim 200$ au. From this point onward, the pressure contribution keeps decreasing only for while it remains approximately constant for . Physically, this translates into a stronger effect of the pressure gradient in the higher layers with respect to the lower ones, when vertical thermal stratification is taken into account. For this reason, the gas rotation is slowed down at elevated heights more than near the midplane, because of the larger negative contribution of the pressure gradient. This behavior depends on the thermal structure of the disk and we only tested it for the temperature prescription we considered; nevertheless, we expect to observe the same result when describing the disk thermal structure with a similar function, both radially and vertically monotonic.

The difference between the predictions of the two models becomes less significant when the emitting layer of the considered molecule is closer to the one: this is clear from the results for HCN shown in Appendix [11](#app:vel_diff_others).

In Fig. [10](#fig:vel_diff_C18O) we also see an oscillating behavior of the difference of the velocities squared. These modulations are likely correlated to the radial pressure substructure exhibiting peaks and troughs, as imprinted in molecular rotation curves (cite: teague2019; izquierdo2023). As we are not accounting for pressure modulated substructures in our model, we are not able to recover the oscillating behavior of the measured velocity difference. An important improvement would be to include these small-scale pressure oscillations in order to perform a more exhaustive fit of the curves. It is worth highlighting that these additional pressure effects are seen in the difference of the velocities squared, extracted from two different emission heights, which thus suggests different amplitudes of the pressure substructure at distinct heights in the disk. This indicates that rotation curves can be a powerful tool to characterize the 3D structure of gaps, which should be further investigated in the future.

In summary, we can use multi-molecule emission to investigate and directly probe the 2D pressure structure of disks, one of the main physical properties that shape disks dynamics; we can measure the pressure effects on a global scale (i.e., extended pressure gradients along the radial and vertical range) and on a local scale (i.e., localized pressure-modulated substructures).

## Dependence on the emitting layers

In this section we analyze how changing the considered molecular emitting layers can impact our results on the dynamical estimates of $M_\star$, $M_\text{d}$, and $R_\text{c}$.

As a first test, we repeated the whole identical routine of rotation curves extraction and multi-molecule fit of the curves, considering flat emission for all the molecules. We note that this scenario is extreme and does not well represent the real system, as we are assuming that all the molecules emit from the midplane, which is clearly not realistic as are known to emit from very elevated layers. In this case, we obtain the following best-fit estimates: $M_\star=1.7827\pm 0.0003$ M$_\odot$, $M_\text{d}=0.1396\pm 0.0003$ M$_\odot$, and $R_\text{c}=174.8\pm 0.3$ au. Thus, the differences in the final dynamical estimates of the parameters are within 10% for M$_\star$, 18% for $M_\text{d}$, and 20% for $R_\text{c}$. We note that these differences are mainly driven by the overestimation of the rotation curve of in the outer regions of the disk; in fact, we fit a lower value for M$_\star$ and a higher value for $M_\text{d}$, which is strongly related to the disk outer regions. However, in this case we are assuming is emitting from the midplane and we know that this scenario is unrealistic. However, a much more realistic scenario where we consider flat emission only for lower S/N lines and/or molecules emitting close to the midplane () would impact the results far less, as the extracted curves in the flat and nonflat scenarios are compatible (as explained in Sect. [3.2](#subsec:curves_extraction) and shown in Fig. [11](#fig:flat_emission_diff)).

As a second test, we repeated the whole analysis adopting nonparametric emitting layers for all the molecules, as retrieved by (cite: paneque). In Appendix [10](#app:nonpar_layers) we show the corner plot obtained from the multi-molecule fit, with the dynamical estimates of the stellar mass, disk mass, and scale radius. The best-fit values we obtain from the fit in the nonparametric case differ from the parametric case results by $\lesssim 1\%$ for $M_\star$, $\lesssim 30\%$ for $M_\text{d}$, and $\lesssim 13\%$ for $R_\text{c}$. We see that the shape of the emitting surface has an impact mainly on the disk mass, that is affected by the systematics described by (cite: veronesi2024) and (cite: andrews2024). The difference we measure for the disk mass estimate is in agreement with the results by (cite: veronesi2024) and (cite: andrews2024), predicting an uncertainty close to $\sim 25 \%$. Also, in Appendix [10](#app:nonpar_layers) we show the same plot as Fig. [10](#fig:vel_diff_C18O) for the nonparametric case, in which we recover exactly the same trends as the parametric case; thus, the same conclusions we drew in Sect. [4.1](#subsec:multimol_fit) also apply to the nonparametric scenario.

# Conclusions

In this work we explored the potential of a multi-molecule approach to gas kinematics to accurately characterize the 2D ($R,z$) pressure structure of disks. We focused our analysis on the HD 163296 protoplanetary disk, and investigated the 2D structure by analyzing seven molecular tracers originating at different heights across the disk vertical extent to gain insights into the physical properties across the distinct disk layers. Considering the disk 2D temperature structure as estimated through the optically thick emission layering by (cite: maps4) and the emission heights by (cite: paneque), we extended existent tools to extract the rotation curves along these layers. We then simultaneously fitted all the curves for the first time with a multi-molecule ($\geq 2$) model of a disk including thermal stratification. Our results show the following:

- The 2D pressure structure leaves a measurable kinematical imprint in the gas rotation curves that is important across the whole disk vertical extent, also close to the midplane. Therefore, thermal stratification must be included in models to correctly reproduce the measured velocity differences at distinct heights, extending the approach by (cite: martire) closer to the midplane.

- There are pressure substructures linked to the existence of dust gaps (not considered in our model) that can be seen from the rotation curves analysis and clearly exhibit a vertical dependence.

- A multi-molecule fit ($\geq 2$) of the rotation curves including the contribution from vertical stratification can be performed efficiently and dynamical estimates can be constrained more accurately (within the limits of our parametric method) for the stellar mass ($M_\star=1.89$ M$_\odot$), disk mass ($M_\text{d}=0.12$ M$_\odot$), and disk scale radius ($R_\text{c}=143$ au), in agreement with (cite: martire).

- The main results we obtain do not depend significantly on the chosen parameterization for the molecular emitting layers. The disk mass is the parameter that is more affected by these systematics ($\lesssim 30\%$).

- We can retrieve the 2D pressure structure of the disk by knowing the 2D temperature profile, the disk mass, and the scale radius from the rotation curves fit.

- Spectra from molecular lines with hyperfine splitting can be efficiently leveraged by extending standard methodologies to enhance precision and accuracy in the retrieved rotation curves.

- Optical depth profiles can be easily constrained knowing the 2D temperature and the molecular emitting layers only, with reasonable accuracy. These results are comparable to estimates from other independent and more complicated methods.

A first interesting development of this work would be to extract the temperature field directly from the rotation curves instead of assuming it from (cite: law2021), by fitting for the temperature structure as imprinted in the vertically separated rotation curves. With this method it would be possible to characterize the 2D temperature field $T(r,z)$ directly from molecular rotation curves without the restriction to optically thick emitters. We leave this analysis to subsequent work.

We also emphasize that the simultaneous characterization of the 2D pressure structure and temperature scalar field has the potential to reveal the 2D gas density structure in disks. A multi-molecule kinematical analysis could then represent a solid further step toward a more comprehensive physical and chemical view of the 2D structure of disks.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01055.L ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. V.P. and S.F. are funded by the European Union (ERC, UNVEIL, 101076613). Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council. Neither the European Union nor the granting authority can be held responsible for them. S.F. acknowledges financial contribution from PRIN-MUR 2022YP5ACE. CL has been supported by the UK Science and Technology research Council (STFC) via the consolidated grant ST/W000997/1. GL acknowledges the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska-Curie Grant Agreement No 823823 (DUSTBUSTERS). The authors thank the anonymous referee for valuable comments that improved the scientific value of this work.

58 natexlab

(ref: abramowitz) Abramowitz, M. & Stegun, I. A. 1970, Handbook of mathematical functions : with formulas, graphs, and mathematical tables

(ref: ahrens2002) Ahrens, V., Lewen, F., Takano, S., et al. 2002, Zeitschrift Naturforschung Teil A, 57, 669

(ref: aikawa) Aikawa, Y., van Zadelhoff, G. J., van Dishoeck, E. F., & Herbst, E. 2002, A&A, 386, 622

(ref: andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41

(ref: andrews2024) Andrews, S. M., Teague, R., Wirth, C. P., Huang, J., & Zhu, Z. 2024, arXiv e-prints, arXiv:2405.19574

(ref: bergner2019) Bergner, J. B., Öberg, K. I., Bergin, E. A., et al. 2019, ApJ, 876, 25

(ref: maps11) Bergner, J. B., Öberg, K. I., Guzmán, V. V., et al. 2021, ApJS, 257, 11

(ref: bertin) Bertin, G. & Lodato, G. 1999, A&A, 350, 694

(ref: braun2021) Braun, T. A. M., Yen, H.-W., Koch, P. M., et al. 2021, ApJ, 908, 46

(ref: casassus2019) Casassus, S. & Pérez, S. 2019, ApJL, 883, L41

(ref: dartois) Dartois, E., Dutrey, A., & Guilloteau, S. 2003, A&A, 399, 773

(ref: degregorio-mosalvo2013) de Gregorio-Monsalvo, I., Ménard, F., Dent, W., et al. 2013, A&A, 557, A133

(ref: dullemond2020) Dullemond, C. P., Isella, A., Andrews, S. M., Skobleva, I., & Dzyurkevich, N. 2020, A&A, 633, A137

(ref: dutrey) Dutrey, A., Semenov, D., Chapillon, E., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 317–338

(ref: facchini2021) Facchini, S., Teague, R., Bae, J., et al. 2021, AJ, 162, 99

(ref: emcee) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: guilloteau2014) Guilloteau, S., Simon, M., Piétu, V., et al. 2014, A&A, 567, A117

(ref: maps6) Guzmán, V. V., Bergner, J. B., Law, C. J., et al. 2021, ApJS, 257, 6

(ref: henning) Henning, T. & Semenov, D. 2013, Chemical Reviews, 113, 9016

(ref: isella2016) Isella, A., Guidi, G., Testi, L., et al. 2016, , 117, 251101

(ref: isella2018) Isella, A., Huang, J., Andrews, S. M., et al. 2018, ApJL, 869, L49

(ref: izquierdo2022) Izquierdo, A. F., Facchini, S., Rosotti, G. P., van Dishoeck, E. F., & Testi, L. 2022, ApJ, 928, 2

(ref: izquierdo2021) Izquierdo, A. F., Testi, L., Facchini, S., Rosotti, G. P., & van Dishoeck, E. F. 2021, A&A, 650, A179

(ref: izquierdo2023) Izquierdo, A. F., Testi, L., Facchini, S., et al. 2023, A&A, 674, A113

(ref: keppler2019) Keppler, M., Teague, R., Bae, J., et al. 2019, A&A, 625, A118

(ref: law2024) Law, C. J., Benisty, M., Facchini, S., et al. 2024, ApJ, 964, 190

(ref: law2021) Law, C. J., Loomis, R. A., Teague, R., et al. 2021a, ApJS, 257, 3

(ref: maps4) Law, C. J., Teague, R., Loomis, R. A., et al. 2021b, ApJS, 257, 4

(ref: law2023) Law, C. J., Teague, R., Öberg, K. I., et al. 2023, ApJ, 948, 60

(ref: lodato) Lodato, G., Rampinelli, L., Viscardi, E., et al. 2023, MNRAS, 518, 4481

(ref: lyndenbell) Lynden-Bell, D. & Pringle, J. E. 1974, MNRAS, 168, 603

(ref: martire) Martire, P., Longarini, C., Lodato, G., et al. 2024, A&A, 686, A9

(ref: miotello2023) Miotello, A., Kamp, I., Birnstiel, T., Cleeves, L. C., & Kataoka, A. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 501

(ref: muller2000) Müller, H. S. P., Klaus, T., & Winnewisser, G. 2000, A&A, 357, L65

(ref: oberg2023) Öberg, K. I., Facchini, S., & Anderson, D. E. 2023, ARA&A, 61, 287

(ref: maps1) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1

(ref: paneque) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., et al. 2023, A&A, 669, A126

(ref: pegues2020) Pegues, J., Öberg, K. I., Bergner, J. B., et al. 2020, ApJ, 890, 142

(ref: pinte2018a) Pinte, C., Ménard, F., Duchêne, G., et al. 2018a, A&A, 609, A47

(ref: pinte2018b) Pinte, C., Price, D. J., Ménard, F., et al. 2018b, ApJL, 860, L13

(ref: pinte2023) Pinte, C., Teague, R., Flaherty, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 645

(ref: rich) Rich, E. A., Wisniewski, J. P., Currie, T., et al. 2019, ApJ, 875, 38

(ref: sastry1981) Sastry, K. V. L. N., Helminger, P., Charo, A., Herbst, E., & De Lucia, F. C. 1981, ApJL, 251, L119

(ref: semenov) Semenov, D., Pavlyuchenkov, Y., Henning, T., Wolf, S., & Launhardt, R. 2008, ApJL, 673, L195

(ref: simon2017) Simon, M., Guilloteau, S., Di Folco, E., et al. 2017, ApJ, 844, 158

(ref: teague_eddy) Teague, R. 2019, The Journal of Open Source Software, 4, 1220

(ref: Teague_GoFish) Teague, R. 2019, The Journal of Open Source Software, 4, 1632

(ref: maps18) Teague, R., Bae, J., Aikawa, Y., et al. 2021, ApJS, 257, 18

(ref: teague2019) Teague, R., Bae, J., & Bergin, E. A. 2019, Nature, 574, 378

(ref: teague2018a) Teague, R., Bae, J., Bergin, E. A., Birnstiel, T., & Foreman-Mackey, D. 2018a, ApJL, 860, L12

(ref: teague2018b) Teague, R., Bae, J., Birnstiel, T., & Bergin, E. A. 2018b, ApJ, 868, 113

(ref: thi2004) Thi, W. F., van Zadelhoff, G. J., & van Dishoeck, E. F. 2004, A&A, 425, 955

(ref: van) van Zadelhoff, G. J., van Dishoeck, E. F., Thi, W. F., & Blake, G. A. 2001, A&A, 377, 566

(ref: veronesi2024) Veronesi, B., Longarini, C., Lodato, G., et al. 2024, A&A, 688, A136

(ref: veronesi2021) Veronesi, B., Paneque-Carreño, T., Lodato, G., et al. 2021, ApJL, 914, L27

(ref: weaver2018) Weaver, E., Isella, A., & Boehler, Y. 2018, ApJ, 853, 113

(ref: yen2018) Yen, H.-W., Koch, P. M., Manara, C. F., Miotello, A., & Testi, L. 2018, A&A, 616, A100

(ref: maps5) Zhang, K., Booth, A. S., Law, C. J., et al. 2021, ApJS, 257, 5

# Flat emission scenario

For every considered line, in Fig. [11](#fig:flat_emission_diff) we show the difference between the extracted rotation curves in case of flat and elevated emission, where the error on each point is evaluated as the sum in quadrature of the errors on the two curves. The errors are generally small, as the uncertainties on the curves are in the first place underestimated, as explained in Sect. [4.1](#subsec:multimol_fit). The largest discrepancies not compatible within the error bars are obtained for , , and HCN, for which the flat assumption is clearly incorrect, as these molecules emit from elevated layers in the disk. This was expected, and these molecules do not represent an issue as their emission has a high S/N and their emitting layer is well-constrained. As expected, we obtain a large discrepancy for , especially at larger radii: in case of flat emission, the curve is overestimated in the outer regions of the disk ($R>200$ au), leading in turn to an overestimate of the disk mass, as described in Sect. [4.2](#subsec:layers_dependency).

![](images/abs_err_profiles.pdf)

# Sample extension: Beam smearing effect

We show in Fig. [12](#fig:anticorr_HCN) the beam smearing effects for HCN, as previously shown in Fig. [5](#fig:anticorr) for in Sect. [3.2.3](#subsec:beam_smearing).

![](images/HD_HCN_anticorr_whole.pdf)

# : A complicated case

As mentioned in Sect. [4.1](#subsec:multimol_fit), the rotation curve extraction with eddy does not provide reliable results for a small range of radii around $R\sim 150$ au, as the signal-to-noise in correspondence of this emission gap is too low to allow an efficient reconstruction of the profile. We note that the extraction in this region is not reliable by looking at the river plots at the corresponding radii and at how efficiently they are aligned. We show in Fig. [13](#fig:river_plots_H2CO) the river plots, before and after the alignment with the SHO method, at two different radii: $R\sim 240$ au and $R\sim 160$ au. We see that in the first case the alignment procedure works perfectly and the aligned spectra form a straight line, while in the second case (corresponding to the emission gap radius) the method fails in aligning the intensity peaks.

![image](images/river_right.pdf) ![image](images/river_right_aligned.pdf) ![image](images/river_wrong.pdf) ![image](images/river_wrong_aligned.pdf)

# Thermally stratified fit: Corner plot

We show in Fig. [14](#fig:cornerplot) the corner plot for the simultaneous multi-molecule fit performed with DySc on our seven extracted rotation curves.

![](images/cornerstrat_hd_7_cutRIGHT_light.jpg)

# Nonparametric emitting layers

We show in Fig. [16](#fig:corner_7mol_nonpar) the corner plot obtained from the multi-molecule fit assuming nonparametric emitting layers for all the molecules, with the dynamical estimates of the stellar mass, disk mass, and scale radius. We also show in Fig. [15](#fig:diff_C18O_nonpar) the same plot as Fig. [10](#fig:vel_diff_C18O) for the nonparametric case.

![](images/squared_diff_7mol_C18O.png)

![](images/corner_HD_7mol_nonpar.png)

# Complete sample: Thermally stratified versus isothermal model

Here we show in Fig. [17](#fig:vel_diff_others) the normalized difference between the squared rotation velocities of respectively , , , HCN, and with respect to the . We do not discuss in detail , since the rotation curve extraction proved to be quite difficult and we do not have the necessary accuracy to draw a reasonable conclusion. We also do not recover any significant difference between the two considered models for what concerns .

On the contrary, we find a significant improvement in the fit for , when considering thermal structure: in this case, as for , the stratified model better reproduces the measured velocity difference. This is the case also for HCN and , even if the difference between the two models is less appreciable here because in the considered range of radii their emitting layers are closer to the with respect to the . Moreover, for these two molecules we can clearly see a global oscillation in the observations that can be traced back to the distortion of the rotation curves due to the beam smearing effect, as explained in Sect. [3.2.3](#subsec:beam_smearing). Finally, for we find small-scale pressure modulated oscillations similar to what we see for .

We observe that, especially in the case, for some radial ranges ($130-210$ au, $>330$ au) even the stratified model struggles to reproduce the data. This can be traced back to the inflexibility of the model in this case, caused by the not complete suitability of the temperature parameterization from (cite: dullemond2020) we are assuming, as the thermal structure might be more complex.

![image](images/hd163296_diff_7mol_13CO.pdf) ![image](images/hd163296_diff_7mol_HCO.pdf) ![image](images/hd163296_diff_7mol_H2CO.pdf) ![image](images/hd163296_diff_7mol_HCN.pdf) ![image](images/hd163296_diff_7mol_C2H.pdf)

[^1]: Radial intensity profiles are available in the MAPS database at <https://alma-maps.info/data.html>.

[^2]: The code is publicly available at <https://github.com/crislong/DySc>.

[^3]: For details, we refer to (cite: emcee).

[^4]: See (cite: izquierdo2021) for details.

</paper>

Write the methods card for this paper.