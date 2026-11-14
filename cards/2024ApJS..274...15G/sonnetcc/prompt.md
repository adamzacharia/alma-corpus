# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJS..274...15G\sonnetcc\reply.txt

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
 "bibcode": "2024ApJS..274...15G",
 "title": "ALMA-IMF. XIV. Free─Free Templates Derived from H41α and Ionized Gas Content in 15 Massive Protoclusters",
 "year": 2024,
 "journal": "The Astrophysical Journal Supplement Series",
 "first_author": "Galván-Madrid, Roberto",
 "n_authors": 28,
 "arxiv_id": "2407.07359",
 "doi": "10.3847/1538-4365/ad61e6",
 "alma_projects_linked_by_archive": [
  "2017.1.01355.L"
 ]
}
```

Paper text:
<paper>
# ALMA-IMF XIV: Free-Free Templates Derived from H$41\alpha$\
and Ionized Gas Content in Fifteen Massive Protoclusters

## Abstract

We use the H$41\alpha$ recombination line to create templates of the millimeter free-free emission in the ALMA-IMF continuum maps, which allows to separate it from dust emission. This method complements spectral-index information and extrapolation from centimeter wavelength maps. We use the derived maps to estimate the properties of up to 34 HII regions across the ALMA-IMF protoclusters. The hydrogen ionizing-photon rate $Q_0$ and spectral types follow the evolutionary trend proposed by Motte et al. The youngest protoclusters lack detectable ionized gas, followed by protoclusters with increasing numbers of OB stars. The total $Q_0$ increases from $\sim 10^{45}$ s$^{-1}$ to $> 10^{49}$ s$^{-1}$. We used the adjacent He$41\alpha$ line to measure the relative number abundances of helium, finding values consistent with the Galactic interstellar medium, although a few outliers are discussed. A search for sites of maser amplification of the H$41\alpha$ line returned negative results. We looked for possible correlations between the electron densities ($n_e$), emission measures (EM), and $Q_0$ with HII region size $D$. The latter are the better correlated, with $Q_0 \propto D^{2.49\pm0.18}$. This favors interpretations where smaller ultracompact HII regions are not necessarily the less dynamically evolved versions of larger ones, but rather are ionized by less massive stars. Moderate correlations were found between dynamical width $\Delta V_\mathrm{dyn}$ with $D$ and $Q_0$. $\Delta V_\mathrm{dyn}$ increases from about one to two times the ionized-gas sound speed. Finally, an outlier HII region south of W43-MM2 is discussed. We suggest that this source could harbor an embedded stellar or disk wind.

# Introduction

The ALMA-IMF Large Program targeted fifteen of the most massive star-forming clumps within 5 kpc from the Sun (cite: Csengeri17), based on the larger ATLASGAL sample across the Galaxy (cite: Schuller09; Csengeri14). The survey description has been presented in (cite: Motte22), including a proposed evolutionary scheme for the sample based on their activity in the mid- and far-infrared, as well as the presence of hydrogen recombination line emission. The ALMA-IMF consortium has provided science-ready data products to the community, including 12m-array continuum images, together with an imaging and self-calibration pipeline (cite: Ginsburg22), a combination with single-dish bolometer images (cite: DiazGonzalez23), and full-bandwidth line cubes (cite: Cunningham2023). The two-band (3 mm and 1 mm), two-configuration, mosaic observing mode allows to map the extent of these protocluster clumps with excellent imaging quality (cite: Ginsburg22).

The main scientific driver of the project is to measure the Core Mass Function (CMF) in a statistically significant ($> 500$) sample of cores that spans the full range of gas masses, from sub-solar to $\gtrsim 100~M_\odot$ (cite: Motte18_NatAs), something that can only be achieved by observing massive protocluster clumps at different evolutionary stages. The more evolved protocluster clumps in the sample have increasingly important feedback by ionisation from ultracompact (UC) and hypercompact (HC) HII regions (cite: Kurtz94; Churchwell02; Hoare07; Purcell13; Klaassen18). The corresponding free-free continuum emission can be an important “contaminant” for the otherwise dust-only ALMA millimeter continuum maps. The separation of dust and free-free contributions is therefore a necessary step for the correct interpretation of the origin of the emission and derived quantities (cite: GM09; Zhang22). First results on the evolution of the CMF in young protoclusters mostly devoid of HII regions are presented in (cite: Pouteau22; Pouteau23) and (cite: Nony2023). The CMF of the evolved protocluster G012.80 is presented in (cite: Armante24), who used the results presented in this paper. The CMFs of the global sample, and also as a function of evolution class, are reported in Louvet et al. (subm.).

ALMA-IMF has been designed to include tools to separate the free-free contribution. The first one is the use of spectral index information (cite: Pouteau22; Nony2023; DiazGonzalez23). However, it is desirable to have an alternative marker that also provides an estimation of the free-free contribution in intensity units, i.e., as a map. Recombination lines are useful tools to detect and characterize the HII regions produced by massive star and cluster formation (cite: Rugel19; Anderson21). Lines in the (sub)millimeter are brighter than their centimeter counterparts and mostly free from collisional (“pressure”) broadening, thus they are useful to characterize the denser HII regions (cite: KZK08; Quang17; Kim17). Moreover, their brightness has been shown to be globally consistent with local thermodynamic equilibrium (LTE) in massive star formation regions (cite: Kim18). Therefore, the velocity-integrated line intensity can be used to estimate the underlying free-free continuum (cite: Liu19). This method offers several advantages, namely: covering the whole survey, having approximately the same uv-coverage and beamsize as the corresponding continuum images, and providing the estimate of the free-free contribution directly at a similar frequency to the continuum. The latter decreases the potential effect of assuming a wrong free-free spectral index, as could be the case if a extrapolation from centimeter wavelength data is employed. However, the method is not without its caveats, mainly that the line can be out of LTE under certain conditions (cite: Walmsley90; Peters12), and molecular line contamination.

In this paper, we propose to use the H$41\alpha$ line data within the same ALMA-IMF data set. In Section [2](#sec:data) we describe the data. In Section [3](#sec:ff-estimations) we explain the procedure to obtain the free-free estimation and error maps, the products that we make available, and a validation of the procedure and its limitations. In Section [4](#sec:hiis) we derive physical properties for the HII regions in the ALMA-IMF protoclusters. In Section [5](#sec:line_params) we use the hydrogen and helium $41\alpha$ line parameters to derive relative He abundances in the ionized gas. In Section [6](#sec:disc) we discuss the benefits and caveats of our proposed technique, look for candidates of recombination line masers, and further discuss the evolution of photoionization within the ALMA-IMF sample.

# Data

For each of the 15 ALMA-IMF protoclusters, we created cubes that cover the $41\alpha$ recombination lines of hydrogen (H$41\alpha$), helium (He$41\alpha$), and carbon (C$41\alpha$). The rest frequencies of the targeted lines are respectively 92.034434, 92.071938, and 92.080355 GHz, which correspond to velocity offsets of the He and C lines with respect to H41$\alpha$ of $-122.165$ and $-149.583$ km s$^{-1}$. All the cubes were made covering a total width of 270 km s$^{-1}$. The reference velocities for the cube construction were set to the LSR systemic velocities of each protocluster reported in Table 1 of (cite: Motte22). The cubes were created in `CASA` version 6.3.0 (cite: CASA2022) using the ALMA-IMF data pipeline (cite: Ginsburg22). We followed the procedures developed for the imaging of cubes as described in (cite: Cunningham2023).

Each cube is cleaned down to a residual level of $\times 3$ to $\times 5$ the rms noise ($\sigma_\mathrm{rms}$) of channels with H$41\alpha$ emission. This is defined using the `threshold` parameter of the `tclean` task. Also, a `startmodel` is used based on the continuum images published in (cite: Ginsburg22). This permits `tclean` to run significantly faster because the Fourier Transform of the `startmodel` is subtracted from the visibilities at the beginning of the cleaning process (cite: Cunningham2023). Multi-scale cleaning is used by setting the `deconvolver` and `scales` parameters in `tclean`. The scales are selected to clean model components of size zero (point source), the beamsize, and multiples of $\times 2$ the beamsize until reaching $\sim 8$ arcsec, or about half of the largest recoverable scale in the data (cite: DiazGonzalez23). The `gain` parameter was set to 0.08 for all the cubes, which is slightly slower than the default (0.1) in `CASA`. This can be afforded for the case of line-specific cubes. Finally, the JvM correction (cite: JvM95) is applied to the `CASA`-generated cubes in order to correct the flux scale of the residuals and of the restored image due to the fact that the volumes of the clean and dirty beams are not equal.[^1] The cleaning parameters are available in the `imaging_parameters.py` script in the public repository of the ALMA-IMF data processing pipeline.[^2]

# Free-free estimations

## Procedure

We use the H$41\alpha$ line to create maps of the free-free emission at the frequencies of the ALMA-IMF continuum images in Bands 3 and 6. Using a recombination line within the ALMA-IMF data sets ensures to have a similar $(u,v)$ coverage and angular resolution as the continuum images.

The free-free estimations are useful to the main scientific case of the ALMA-IMF project of characterizing the dust emission of the dense-core population in the target protoclusters. For this science case the free-free component is mainly considered as a contaminant of the dust continuum emission, but it can also be used to estimate the properties of the HII regions produced by the young ($\sim$ ZAMS) stellar population.

![](flowchart)

Figure [1](#fig:flowchart) summarizes the procedure that we execute for each protocluster and band. First, three input images for a given protocluster are read in: the H$41\alpha$ line cube and one continuum image for each band. Then, a velocity-integrated intensity (moment 0) map $\sum I_{\mathrm{H}41} \, \Delta \mathrm{v}$ in units of Jy beam$^{-1}$ km s$^{-1}$ is created for each field. The velocity range is optimized by visual inspection to cover only channels where the line is detected. A default value of $\pm 10$ km s$^{-1}$ from the cloud systemic velocity is used for the protoclusters where the line is faint or non-detected (see below). After this, the free-free estimation map $I_\mathrm{ff}$ in units of Jy beam$^{-1}$ is constructed using the following equation (cite: Wilson09; Wenger19):

$$\begin{equation}
I_\mathrm{ff} = 1.432 \times 10^{-4} \bigl( \nu_0^{-1.1} \, T_e^{1.15} \bigr ) \bigl( 1+N_\mathrm{He}/N_\mathrm{H} \bigr ) \sum I_{\mathrm{H}41} \, \Delta \mathrm{v}, 
\label{eq:ff_map}
\end{equation}$$

where the electron temperature $T_e = 7000$ K, the helium to hydrogen number ratio $N_\mathrm{He}/N_\mathrm{H} = 0.08$, and $\nu_0$ is the central frequency of the H$41\alpha$ line. Equation [\[eq:ff_map\]](#eq:ff_map) assumes LTE conditions, and we found a posteriori that this assumption is generally valid (see Section [6.2](#sec:LTE-validity)). $T_e$ in HII regions is expected to have values from $\gtrsim 5000$ K to $\approx 10^4$ K (cite: Osterbrock89). Our selection is close to the middle of this range and minimized regions of oversubtraction of the free-free emission in the continuum maps. The selected value of $N_\mathrm{He}/N_\mathrm{H}$ is appropriate for the Milky Way ISM (cite: MendezDelgado20), and later we show that the HII regions in our sample are mostly consistent with it (see Section [5](#sec:line_params)). Further updates in $N_\mathrm{He}/N_\mathrm{H}$ only change $I_\mathrm{ff}$ by a few percent (see Eq. [\[eq:ff_map\]](#eq:ff_map)). We consider a $20\%$ error in $T_e$ and propagate it through our measurements to acknowledge the possibility of spatial variations in this quantity. In many of the derived quantities this uncertainty is dominates the errors.

At millimeter wavelengths it is expected that free-free emission will be optically thin (spectral index $\alpha_\mathrm{ff} = -0.1$) in all HII regions except possibly in the densest ones (cite: Keto02; GM09; Rosero19). The actual detection of H$41\alpha$ guarantees that the underlying free-free continuum is not opaque, otherwise the line would be absorbed. For a homogeneous HII region, the transition or turn-over frequency between the optically thick and thin regimes is in the range from 50 GHz to 60 GHz for an emission measure EM (see Section [4](#sec:hiis)) as high as $10^{10}$ cm$^{-6}$ pc (cite: Kurtz05), although HII regions with density gradients could be partially optically thick ($\alpha_\mathrm{ff} \sim 1$) at frequencies $\gtrsim 100$ GHz (cite: KZK08; GM09). In our procedure, the output free-free map at the frequency of H$41\alpha$ (92.03 GHz) is rescaled to the desired frequency of the continuum image assuming $\alpha_\mathrm{ff} = -0.1$. The flux scalings to the Band 3 (98.6 GHz) and Band 6 (224.6 GHz) continuum frequencies are then 0.99 and 0.92, respectively. If the correct free-free spectral index in those spots were $\alpha=1$ all the way to Band 6, the continuum scaling factors should instead be 1.07 and 2.44. It is possible that in Band 3 the optically-thin assumption breaks in a few compact spots with very dense HII regions, but this is highly unlikely in Band 6.

Maps of the error of the free-free intensity $\sigma_\mathrm{ff}$ are also generated. These are approximated by the noise in the moment 0 map $\sigma_\mathrm{m0}$ and the error in the assumed electron temperature $\sigma_{T_e}$ as in: $$\begin{equation}
 \label{eq:err_ff}
\sigma_\mathrm{ff} \approx I_\mathrm{ff} \Bigl[ \Bigl( \frac{\sigma_\mathrm{m0}}{\sum I_{{\rm H}41} \Delta \mathrm{v}} \Bigr)^2 + \Bigl( \frac{\sigma_{T_e}}{T_e} \Bigr)^2 \Bigr]^{0.5}.  
\end{equation}$$

The $I_\mathrm{ff}$ and $\sigma_\mathrm{ff}$ maps are regridded to the pixel geometry of the input continuum images, which in turn are convolved to the slightly larger beamsize (cite: Cunningham2023) of the line cube and moment 0 maps. A subtraction is then performed of the convolved continuum image minus the regridded free-free map, resulting in an estimated map of pure-dust emission $I_\mathrm{dust}$. Finally, the primary-beam (PB) correction is applied to the regridded free-free estimation map and the associated error map, as well as to the pure dust map. Performing the PB correction as a last step has the advantage of working with images with spatially uniform noise levels in the intermediate steps.

|  |  |  |  |
|:--:|:--:|:--:|:--:|
| Protocluster | HPBW, PA | \[$v_\mathrm{min}$,$v_\mathrm{max}$\] | $\sigma_\mathrm{m0}$ |
|  | \[$\ensuremath{''} \times \ensuremath{''},~\deg$\] | \[km s$^{-1}$\] | \[mJy beam$^{-1}$ km s$^{-1}$\] |
| G008.67 | $0.95\times0.66$, 66.7 | \[6.8,84.0\] | 20 |
| G010.62 | $0.57\times0.45$, $-67.9$ | \[-39.1,41.9\] | 14 |
| G012.80 | $2.28\times1.93$, 84.9 | \[-5.8,84.4\] | 83 |
| G327.29 | $0.71\times0.61$, 57.2 | \[-63.4,-19.2\] | 9 |
| G328.25$\dagger$ | $0.99\times0.93$, 75.0 | \[-53.0,-33.0\] | 9 |
| G333.60 | $0.78\times0.74$, 28.2 | \[-103.3,5.2\] | 19 |
| G337.92 | $0.80\times0.75$, $-77.5$ | \[-52.8,-8.7\] | 9 |
| G338.93$\dagger$ | $0.66\times0.63$, 4.7 | \[-72.0,-52.0\] | 5 |
| G351.77 | $2.20\times1.90$, 89.8 | \[-29.0,20.6\] | 42 |
| G353.41 | $2.18\times1.85$, 73.6 | \[-46.7,19.5\] | 55 |
| W43-MM1$\dagger$ | $0.92\times0.52$, $-81.9$ | \[80.3,115.3\] | 6 |
| W43-MM2 | $0.43\times0.33$, $-77.8$ | \[61.9,122.6\] | 5 |
| W43-MM3 | $0.61\times0.43$, $-84.0$ | \[61.1,120.0\] | 7 |
| W51-E | $0.39\times0.35$, $-73.0$ | \[22.8,100.0\] | 11 |
| W51-IRS2 | $0.41\times0.37$, $-68.8$ | \[8.7,93.4\] | 11 |

: H$41\alpha$ cube and moment 0 parameters. Columns: (1) protocluster name; (2) cube half-power beamwidth and position angle; (3) visually determined velocity range of the moment 0 integration (a default $\pm 10$ km s$^{-1}$ is used for the non-detections marked with a $\dagger$); (4) MAD standard deviation of the moment 0 image.

## Products

Figure [2](#fig:ff-maps) shows the PB-corrected free-free estimation maps for the 12 ALMA-IMF protoclusters with a detection of H$41\alpha$ emission. Figure [10](#fig:comparison-maps-app) in Appendix [8](#app:pure-dust) gives a comparison between the original continuum maps, the free-free estimations, and the pure-dust maps at 1.3 mm.

The free-free estimation is only performed in pixels of the moment 0 maps above a threshold of $5\sigma$, where $\sigma$ is defined as the robust standard deviation using the median absolute deviation (MAD) implemented in `astropy.stats.mad_std`. Table [1](#tab:H41_params) lists the basic parameters for the preparation of the free-free estimation images. Two protoclusters were clear non-detections in H$41\alpha$ (G338.93 and W43-MM1). One protocluster (G328.25) was a tentative detection, but further inspection showed the spectrum was dominated by molecular-line contamination. The free-free estimation maps of these three protoclusters originally contained a few pixels with values larger than zero due to molecular lines in the moment 0 integration, therefore, we manually set their free-free maps to zero.

The data products are further described in Appendix [9](#app:products). The scripts associated with this paper[^3] permit the user to easily recalculate any free-free estimation image by editing `ffsub.py`, which makes use of the functions defined in `ff_tools.py`. The code can also be easily applicable to other data sets (cite: Nony24). We caution the user against blindly using the calculated free-free templates in regions where it dominates the total continuum emission, or at the position of line rich hot molecular cores. In the former case, the generated error maps ($\sigma_\mathrm{ff}$) become particularly useful to weigh in the relative contributions of dust and free-free. In the latter, molecular lines can dominate over the recombination line emission.

![image](G008.67_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff98.6GHz_5.0sigma.regr.pbcor.png)  ![image](G010.62_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff98.6GHz_5.0sigma.regr.pbcor.png) \
![image](G012.80_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff98.6GHz_5.0sigma.regr.pbcor.png)  ![image](G327.29_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff98.6GHz_5.0sigma.regr.pbcor.png) \
![image](G333.60_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff98.6GHz_5.0sigma.regr.pbcor.png)  ![image](G337.92_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff98.6GHz_5.0sigma.regr.pbcor.png) 

![image](G351.77_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff98.6GHz_5.0sigma.regr.pbcor.png)  ![image](G353.41_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff98.6GHz_5.0sigma.regr.pbcor.png) \
![image](W43-MM2_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff98.6GHz_5.0sigma.regr.pbcor.png)  ![image](W43-MM3_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff98.6GHz_5.0sigma.regr.pbcor.png) \
![image](W51-E_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff98.6GHz_5.0sigma.regr.pbcor.png)  ![image](W51-IRS2_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff98.6GHz_5.0sigma.regr.pbcor.png) 

## Validation

![](W51ff_validation.png)

A typical method to separate the contributions of dust and free-free in (sub)millimeter continuum maps is to use a centimeter continuum map dominated by free-free and extrapolate it to shorter wavelengths, assuming an appropriate spectral index (cite: CG2012; Zhang22). However, for a survey such as ALMA-IMF, using the H41$\alpha$ line within the same data set has several advantages, namely: i) that the assumed $\alpha_\mathrm{ff} = -0.1$ is more likely to be correct when the scaling is done within millimeter wavelengths, and not from the centimeter to the millimeter, also, the scaling is smaller; ii) that the $(u,v)$ coverages of the continuum and line maps are very similar, thus their beamsizes and largest recoverable scales are also quite similar; iii) that there are no extra induced flux-calibration or astrometric errors from using different instruments; and iv) that ten out of fifteen ALMA-IMF protoclusters have declinations $< -15^\circ$, which makes them difficult to observe with the VLA, at least with a good synthesized beam.[^4] Actually, five out of ten protoclusters are unobservable with the VLA.

To cross-validate our method, we compare the H$41\alpha$-derived free-free estimation $I_\mathrm{ff,H41}$ at 98 GHz for the W51 protoclusters to an independent estimation $I_\mathrm{ff,2cm}$ derived from the Ku-band (2.2 cm, 13.4 GHz) VLA image presented in (cite: Ginsburg16). The beamsize and position angle of the original 2-cm image are $\mathrm{BMAJ}=0.342$ arcsec, $\mathrm{BMIN}=0.332$ arcsec, and $\mathrm{BPA}=14.83$ deg. We convolve this image to the beam of the H$41\alpha$-derived free-free map: $\mathrm{BMAJ}=0.408$ arcsec, $\mathrm{BMIN}=0.374$ arcsec, and $\mathrm{BPA}=-68.77$ deg, and regrid it to the same pixel geometry. Next, we assume that the 2-cm free-free emission is optically thin and rescale the cm map by a factor $(98.6/13.4)^{-0.1}$ to estimate the free-free intensity in the ALMA-B3 map. Finally, we mask out all pixels below $5\sigma = 5 \times 92~\mu$Jy beam$^{-1}$, where $\sigma$ is defined as in Section [3.2](#sec:products).

Figure [3](#fig:validation) shows a comparison of the free-free maps at 98.6 GHz derived using the H$41\alpha$ line and the 2-cm continuum. The comparison is done for those pixels with a valid measurement (i.e., $> 5\sigma$) in both images. It is seen that the vast majority of pixels follow the line where the ratio of the estimations $I_\mathrm{ff,H41}/I_\mathrm{ff,2cm} = 1$. From 145,862 pixels in the left panel of Fig. [3](#fig:validation), $96.8~\%$ are within $3\sigma$ of the one-to-one relation, where $\sigma$ is determined for each pixel using the H$41\alpha$ free-free error map. The outlier pixels can be separated into two categories, bright and faint. The bright outliers (red points), those pixels with $I_\mathrm{ff,H41} > 0.025$ Jy beam$^{-1}$ and beyond $3\sigma$ from $I_\mathrm{ff,H41}/I_\mathrm{ff,2cm} = 1$, are only 328 pixels, or 4.7 times the beam area. Further inspection reveals that these pixels are located exactly at the position of the two well known UC HII regions: d2 in W51-IRS2 and e2 W51-E (cite: Zhang98; Goddi16).

![image](W51-E_B3_spw1_12M_spw1.JvM.image.fits.ch3cn.m0.e2.png)  ![image](W51e2-bmask-spectrum.png) \
![image](W51-IRS2_B3_spw1_12M_spw1.JvM.image.fits.ch3cn.m0.d2.png)  ![image](W51d2-bmask-spectrum.png)

Figure [4](#fig:bright-H41) shows the two previously mentioned regions overlaid on the integrated emission of CH$_3$CN in Band 3. The red contours mark the location of the bright-outliers (central panel of Fig. [3](#fig:validation)). In the literature, the e2 region (top row of Fig. [4](#fig:bright-H41)) is subdivided into the bright UC HII region e2-west (e2w) and the hot-core emission peaks e2e and e2nw (cite: Shi10; Ginsburg17). The bright-outlier region matches mostly with e2w. The underlying continuum of this HII region is bright enough to absorb the CH$_3$CN line. The recombination line spectrum within this mask (top-right panel of Fig. [4](#fig:bright-H41)) shows a clear detection of the H$41\alpha$ and He$41\alpha$ lines, without evidence of significant contamination from molecular lines. The bottom row of Fig. [4](#fig:bright-H41) shows the second region with bright outliers, which matches the position of the UC HII region W51 d2. The situation is very similar to that of e2, except that the background continuum is not bright-enough to produce absorption of the CH$_3$CN line.

From the previous analysis, we conclude that the origin of the H41$\alpha$ bright-outlier areas could either be: i) a true yet moderate enhancement of the recombination line compared to LTE conditions; or ii) the optically-thin free-free extrapolation from 13 GHz to 98 GHz being invalid, i.e., having partially optically-thick free-free emission with a spectral index $-0.1 < \alpha_\mathrm{ff} < 2$; or a combination of the two. For the case of W51, the spots of bright outlier H$41\alpha$ emission do not appear to have significant contamination from molecular lines (in W51-E and W51-IRS2 we integrated the velocity ranges \[22.8,100\] and \[8.7,93.4\] km s$^{-1}$, respectively, see Table [1](#tab:H41_params)). We have inspected the correspondence of the 76 sources in the hot molecular core (HMC) catalogue of (cite: Bonfand24_arxiv) with our recombination line maps. Eighteen HMCs overlap with valid pixels in our free-free estimation maps. Analysis of the spectra around their positions shows that recombination line emission dominates in all cases except for G327 HMC 1 and G337 HMCs 1 and 4. These areas are not labeled as HII regions in Fig. [2](#fig:ff-maps), and are therefore excluded from our analysis.

# HII region properties

We use the derived 3 mm free-free maps to estimate the average properties of HII regions in the ALMA-IMF protoclusters. For this, we first define apertures of distinct HII emission in each of the 12 protoclusters with recombination line detection (see Section [3.2](#sec:products)). The apertures are marked in Fig. [2](#fig:ff-maps) and provided in the data release (`.reg` files) associated with this paper. We then used the following equations (cite: Wilson09; RS20) to derive their average emission measures (EM, pc cm$^{-6}$), electron densities ($n_e$, cm$^{-3}$), and hydrogen ionizing-photon rates ($Q_0$, s$^{-1}$):

$$\begin{equation}
 \label{eq:tauff}
\tau_\mathrm{ff} = \ln \biggl [ \biggl ( 1 - \frac{I_\nu}{B_\nu(T_e)} \biggr )^{-1} \biggr ],
\end{equation}$$

$$\begin{equation}
 \label{eq:EM}
\mathrm{EM} = 12.143\tau_\mathrm{ff} \Bigl[ \frac{\nu}{\mathrm{GHz}} \Bigr ]^{2.1}\Bigl [ \frac{T_e}{\mathrm{K}} \Bigl ]^{1.35} =  \int n_e^2 dl,
\end{equation}$$

$$\begin{equation}
 \label{eq:Q0}
Q_0 = \frac{\pi}{6} \alpha_\mathrm{B} n_e^2 D^3 = \frac{\pi}{6} \alpha_\mathrm{B} D^2 \mathrm{EM},   
\end{equation}$$

where $\tau_\mathrm{ff}$ is the free-free continuum optical depth, $I_\nu$ is the average intensity of the pixels within the aperture, $B_\nu(T_e)$ is the Planck function at the electron temperature $T_e$, and $\alpha_\mathrm{B} = 2\times10^{-13}$ cm$^{-3}$ s$^{-1}$ is the case-B hydrogen recombination coefficient. The optical depth $\tau_\mathrm{ff}$ is almost a direct observable that depends only on the intensity and the assumed $T_e$. However, in equations (4) and (5) the EM, $Q_0$, and $n_e$ are not independent quantities. By definition, EM is integrated in the line of sight across the ionized object, thus under spherical geometry the diameter of the emitting HII region is $\int dl = D$. In practice, EM is calculated first from $\tau_\mathrm{ff}$ using Eq. (4), and then $n_e$ and $Q_0$ are calculated using Eqs. (4) and (5). Our spherical approximation will be good for HII regions that are isolated and round. For example, for the central HII region in G010.6, from 3D radiative transfer modelling of the H$30\alpha$ line, the inferred $Q_0$ is 6 to $7\times10^{48}$ s$^{-1}$ (cite: GM23), which is consistent the spherical value reported here: $5.1\pm1.4 \times10^{48}$ s$^{-1}$.

Table [\[tab:cont_params\]](#tab:cont_params) lists the average physical parameters derived for the HII regions in the ALMA-IMF protoclusters, ordered by the sum of the $Q_0$ of the HII regions in each protocluster. The spectral types of the ionizing stars are determined using the calibrations of (cite: Martins05) for O-type, and of (cite: Panagia73) for B-type. A single ionizing star is assumed. For reference, Table [\[tab:cont_params\]](#tab:cont_params) also lists the evolutionary stage (young, intermediate, or evolved) of the ALMA-IMF protoclusters determined by (cite: Motte22) from a combination of mid- and far-IR emission, and also considering the H$41\alpha$ surface brightness in preliminary cubes. Our measurements of the ionized gas are overall consistent with this classification, both in terms of EM and $Q_0$. The earliest spectral type and amount of OB stars in each protocluster is also consistent with the proposed evolutionary picture: the youngest regions are devoid of massive stars, followed by regions with a few B-type stars, and then the most active protoclusters harbor from a few to several massive stars, including O-type. However, a few sources deserve a special mention. The ALMA-IMF mosaics of W43-MM2 also cover the region known as MM13 (cite: Motte2003), which corresponds to HII region 2 at the southern border of the field of view. Therefore, only HII region 1 is considered for the total $Q_0$ of MM2. After this consideration, MM2 is the young protocluster with the lowest rate of ionizing photons detected in the sample. Also, G351.77 and G327.29 have very similar values for $Q_0 \approx 0.5\times10^{47}$ s$^{-1}$. In (cite: Motte22), G327.29 (young) and G351.77 (intermediate) are at the limit between these two evolutionary cathegories, so their similar ionizing phothon rates are consistent with the proposed classification. W51-E is found to have the second largest $Q_0$ ($7.4\pm1.7\times10^{48}$ s$^{-1}$) among the ALMA-IMF protoclusters. Since free-free emission is produced by a collisional process, the number of ionizing photons necessary to generate the observed radiation depends on the density squared rather than on the total amount of ionized gas. Therefore, the prevalence of bright and very small ($\sim 10^{-2}$ pc) HII regions in W51-E raises its rank among the evolved protoclusters when $Q_0$ is considered. The opposite situation occurs to G012.80, which has the second largest free-free flux after G333.60. However, this emission is distributed over a rather large area, therefore the required photoionization rate is the smallest among the evolved protoclusters. We note that the absolute evolutionary stage of a protocluster should not be only determined by its ionizing-photon rate, but also by its remaining gas reservoir and substructure (cite: Pouteau23; DiazGonzalez23).

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Protocluster | $d$ | $S_\mathrm{ff,3mm}$ | EM | $n_e$ | $D$ | $Q_0$ | SpT | Evol |
| HII region | \[kpc\] | \[mJy\] | \[$\times10^7$ pc cm$^{-6}$\] | \[$\times10^4$ cm$^{-3}$\] | \[pc\] | \[$10^{47}$ s$^{-1}$\] |  |  |
| W43-MM1 | 5.5 | – | – | – | – | – | – | Y |
| G338.93 | 3.9 | – | – | – | – | – | – | Y |
| G328.25 | 2.5 | – | – | – | – | – | – | Y |
| W43-MM2$^\dagger$ | 5.5 | – | – | – | – | $0.0227\pm0.0081$ | – | Y |
| 1 | $5.5$ | $1.38\pm0.30$ | $0.40\pm0.14$ | $1.72\pm0.31$ | $0.014$ | $0.0227\pm0.0081$ | B1 | – |
| 2 | $5.5$ | $25.5\pm1.7$ | $0.61\pm0.18$ | $1.14\pm0.16$ | $0.047$ | $0.42\pm0.12$ | B0.5 | – |
| G337.92 | 2.7 | – | – | – | – | $0.0363\pm0.0097$ | – | Y |
| 1 | $2.7$ | $7.68\pm0.94$ | $0.144\pm0.045$ | $0.74\pm0.11$ | $0.026$ | $0.0304\pm0.0094$ | B1 | – |
| 2 | $2.7$ | $1.48\pm0.41$ | $0.141\pm0.056$ | $1.10\pm0.22$ | $0.012$ | $0.0059\pm0.0023$ | B2 | – |
| G327.29 | 2.5 | – | – | – | – | $0.49\pm0.14$ | – | Y |
| 1 | $2.5$ | $144.4\pm3.9$ | $0.199\pm0.057$ | $0.472\pm0.067$ | $0.089$ | $0.49\pm0.14$ | B0.5 | – |
| G351.77 | 2.0 | – | – | – | – | $0.52\pm0.15$ | – | I |
| 1 | $2.0$ | $230\pm17$ | $0.37\pm0.11$ | $0.75\pm0.11$ | $0.066$ | $0.50\pm0.15$ | B0.5 | – |
| 2 | $2.0$ | $8.9\pm2.3$ | $0.135\pm0.051$ | $0.79\pm0.15$ | $0.022$ | $0.0194\pm0.0074$ | B1 | – |
| G353.41 | 2.0 | – | – | – | – | $1.54\pm0.33$ | – | I |
| 1 | $2.0$ | $6.0\pm2.0$ | $0.123\pm0.055$ | $0.82\pm0.18$ | $0.018$ | $0.0130\pm0.0058$ | B1 | – |
| 2 | $2.0$ | $240\pm13$ | $0.158\pm0.046$ | $0.391\pm0.056$ | $0.103$ | $0.52\pm0.15$ | B0.5 | – |
| 3 | $2.0$ | $461\pm34$ | $0.81\pm0.24$ | $1.13\pm0.17$ | $0.063$ | $1.00\pm0.29$ | B0 | – |
| G008.67 | 3.4 | – | – | – | – | $5.5\pm1.5$ | – | I |
| 1 | $3.4$ | $834\pm32$ | $2.40\pm0.68$ | $1.69\pm0.24$ | $0.084$ | $5.2\pm1.5$ | O9.5 | – |
| 2 | $3.4$ | $41.9\pm3.3$ | $0.338\pm0.099$ | $0.82\pm0.12$ | $0.050$ | $0.263\pm0.077$ | B0.5 | – |
| W43-MM3 | 5.5 | – | – | – | – | $12.0\pm3.4$ | – | I |
| 1 | $5.5$ | $733\pm12$ | $0.99\pm0.28$ | $0.71\pm0.10$ | $0.199$ | $12.0\pm3.4$ | O8.5 | – |
| G012.80 | 2.4 | – | – | – | – | $46\pm12$ | – | E |
| 1 | $2.4$ | $13490\pm230$ | $1.12\pm0.32$ | $0.567\pm0.080$ | $0.349$ | $42\pm12$ | O7 | – |
| 2 | $2.4$ | $113\pm11$ | $0.221\pm0.066$ | $0.554\pm0.083$ | $0.072$ | $0.36\pm0.11$ | B0.5 | – |
| 3 | $2.4$ | $1231\pm62$ | $0.90\pm0.26$ | $0.87\pm0.13$ | $0.118$ | $3.9\pm1.1$ | O9.5 | – |
| G010.62 | 5.0 | – | – | – | – | $57\pm14$ | – | E |
| 1 | $5.0$ | $3823\pm64$ | $5.3\pm1.5$ | $1.73\pm0.25$ | $0.177$ | $51\pm14$ | O7 | – |
| 2 | $5.0$ | $89.2\pm4.5$ | $0.94\pm0.27$ | $1.22\pm0.17$ | $0.064$ | $1.19\pm0.34$ | B0 | – |
| 3 | $5.0$ | $344.4\pm9.8$ | $1.24\pm0.35$ | $1.06\pm0.15$ | $0.110$ | $4.6\pm1.3$ | O9.5 | – |
| W51-IRS2 | 5.4 | – | – | – | – | $63\pm18$ | – | E |
| 1 | $5.4$ | $3969\pm36$ | $2.53\pm0.72$ | $0.94\pm0.13$ | $0.284$ | $63\pm18$ | O6.5 | – |
| 2 | $5.4$ | $1.85\pm0.49$ | $0.65\pm0.25$ | $2.32\pm0.45$ | $0.012$ | $0.029\pm0.011$ | B1 | – |
| W51-E | 5.4 | – | – | — | – | $74\pm17$ | – | I |
| 1 | $5.4$ | $675\pm31$ | $13.3\pm3.8$ | $5.10\pm0.73$ | $0.051$ | $10.7\pm3.1$ | O8.5 | – |
| 2 | $5.4$ | $106.4\pm5.0$ | $1.98\pm0.57$ | $1.94\pm0.28$ | $0.053$ | $1.69\pm0.48$ | B0 | – |
| 3 | $5.4$ | $3717\pm27$ | $1.52\pm0.43$ | $0.653\pm0.092$ | $0.355$ | $59\pm17$ | O6.5 | – |
| 4 | $5.4$ | $15.4\pm2.5$ | $3.7\pm1.2$ | $5.02\pm0.82$ | $0.015$ | $0.244\pm0.080$ | B0.5 | – |
| 5 | $5.4$ | $182.6\pm6.3$ | $1.36\pm0.39$ | $1.28\pm0.18$ | $0.083$ | $2.89\pm0.82$ | O9.5 | – |
| G333.60 | 4.2 | – | – | – | – | $341\pm95$ | – | E |
| 1 | $4.2$ | $10.0\pm1.6$ | $0.34\pm0.11$ | $1.06\pm0.17$ | $0.030$ | $0.095\pm0.031$ | B0.5 | – |
| 2 | $4.2$ | $4.8\pm1.0$ | $0.33\pm0.12$ | $1.23\pm0.22$ | $0.021$ | $0.046\pm0.016$ | B1 | – |
| 3 | $4.2$ | $71.2\pm4.5$ | $0.53\pm0.15$ | $0.91\pm0.13$ | $0.065$ | $0.68\pm0.20$ | B0 | – |
| 4 | $4.2$ | $35200\pm190$ | $2.38\pm0.67$ | $0.592\pm0.084$ | $0.679$ | $338\pm95$ | O4 | – |
| 5 | $4.2$ | $10.9\pm1.7$ | $0.33\pm0.10$ | $1.00\pm0.16$ | $0.032$ | $0.104\pm0.034$ | B0.5 | – |
| 6 | $4.2$ | $78.5\pm4.5$ | $0.46\pm0.13$ | $0.79\pm0.11$ | $0.073$ | $0.75\pm0.22$ | B0 | – |
| 7 | $4.2$ | $79.2\pm4.4$ | $0.39\pm0.11$ | $0.69\pm0.10$ | $0.080$ | $0.76\pm0.22$ | B0 | – |
| 8 | $4.2$ | $67.2\pm4.1$ | $0.326\pm0.094$ | $0.637\pm0.092$ | $0.080$ | $0.64\pm0.19$ | B0 | – |

![](fitplots_merged_main.png)

![](He_abundances_individual.png)

# Helium abundances

Compared to optical and IR lines, radio recombination lines are free of obscuration and their excitation is simpler (cite: GS02). As mentioned in Section [2](#sec:data), the H$41\alpha$ cubes cover the frequencies of the neighboring He$41\alpha$ line. Abundances of helium with respect to hydrogen can be derived under the assumption that for a given quantum number the recombination lines of the different atoms trace the same gas (cite: Wilson09). The main caveat to this method is that the first ionization potentials of these elements are $\chi = 13.6$ and 24.6 eV, respectively. Therefore, this assumption is valid only for massive stars. We calculate the number abundance of singly-ionized He to ionized H using the following equation (cite: RoelfsemaGoss92):

$$\begin{equation}
\frac{N_\mathrm{H^+}}{N_\mathrm{He^+}} = \frac{\int {\rm H}_{41\alpha} dv}{\int {\rm He}_{41\alpha} dv} \approx \frac{N_\mathrm{H}}{N_\mathrm{He}}. 
\end{equation}$$

Given the very large potential for the second ionization of Helium $\chi_\mathrm{He^+} = 54.40$ eV, this equation also assumes that in the HII gas the number ratio of ionized hydrogen to singly-ionized helium is approximately equal to their total elemental abundance ratio.

For each protocluster, we calculated average abundances in the masks used to define the HII regions shown in Fig. [2](#fig:ff-maps), and with properties reported in Table [\[tab:cont_params\]](#tab:cont_params). We performed Gaussian fitting using `Pyspeckit` (cite: Ginsburg22_pyspeckit). The spectra were converted to units of brightness temperature as a function of LSR velocity prior to the fitting. We use the H$41\alpha$ cubes without primary-beam correction to have a noise closer to spatially uniform. This means that the brightness scale of the fitted lines (see Fig. [5](#fig:H_He_fitplots)) is not corrected, but this does not affect the measured abundances, which depend on the line ratio within the mask. An initial round of fitting included only the hydrogen recombination line, and helium was added later using as initial guesses the parameters of the first fitting. For the relative He-to-H brightness, we took as initial guess a helium-to-hydrogen number abundance $N_\mathrm{He}/N_\mathrm{H} = 0.08$ (see Eq. [\[eq:ff_map\]](#eq:ff_map)), characteristic of the ISM in the Milky Way (cite: MendezDelgado20).

The intrinsically fainter He$41\alpha$ line at 92.071938 GHz can be more easily affected by molecular-line contamination. If present, the main contaminants are lines of CH$_3$OCHO at 92.07402 GHz (ortho) and 92.073101 GHz (para). To avoid this contamination in the results, we rejected He$41\alpha$ fits with a peak brightness $> 0.3$ of the hydrogen peak. Additionally, we rejected results with a He$41\alpha$ centroid outside a range of $\pm10$ km s$^{-1}$ of its theoretical position at $-122.17$ km s$^{-1}$ from the H$41\alpha$. These criteria were found empirically (see Figs. [5](#fig:H_He_fitplots) and [11](#fig:H_He_fitplots_app1)). We also attempted fits with the C$41\alpha$ component. Valid fits including C$41\alpha$ were found occasionally, but the extra fitted parameters had low S/N and did not improve the overall fit quality. The carbon line is expected to be fainter, and is only blueshifted by $-27.42$ km s$^{-1}$ with respect to helium. Also, its smaller ionization potential (11.3 eV) compared to hydrogen causes this line to be preferentially detected in photon-dominated regions (cite: Wyrowski97; Roshi05), and not necessarily in HII regions. The final fits only consider hydrogen and helium lines. These are shown in Figure [5](#fig:H_He_fitplots) for the HII region in each of the 12 detected protoclusters with the highest average brightness. Fig. [11](#fig:H_He_fitplots_app1) in Appendix [10](#app:fitting) shows the rest of the HII regions.

It is worth mentioning that although a Gaussian is a good model for most spectra, a few lines show excess or line wings. In the higher S/N spectra (peak $T_\mathrm{B} > 1$ K), G333.60 HII 4 (blueshifted) and W51-E HII 1 (redshifted) show the clearest wings. G10.62 HII 1 (redshifted), G12.80 HII 1 (redshifted), G333.60 HII 6 (blueshifted), and W51-IRS2 HII 1 (blueshifted) also how milder wings. Apart from these, W43-MM2 HII 2 (MM13) is a double-peaked line.

Figure [6](#fig:H_He_abund) shows the helium-to-hydrogen number abundance ratio $N_\mathrm{He} / N_\mathrm{H}$ derived for the 25 HII regions in the 11 protoclusters where $N_\mathrm{He} / N_\mathrm{H}$ was measured (see Table [\[tab:H41_fits\]](#tab:H41_fits)). Note that the values that we report are relative number abundances. Appendix [11](#app:Y) clarifies the relation between our measurements and the often used relative He abundance per unit mass $Y$. A recent analysis using optical recombination lines of HII regions in the Milky Way reports typical values of the quantity $12 + \log (N_\mathrm{He} / N_\mathrm{H})$ in the range from 10.9 to 11.0 (cite: MendezDelgado20), or $N_\mathrm{He} / N_\mathrm{H} \approx$ 0.08 to 0.1. This range is broadly consistent with our measurements in the UC HII regions within the ALMA-IMF protoclusters.

A few massive star formation regions have been reported to have number He abundances significantly offset from $0.1$, from $\sim~0.01$ to $\gtrsim 0.3$ (cite: RoelfsemaGoss92; DePree1997). However, previous determinations have been usually done at cm-wavelengths with less sensitive observations[^5]. Within our sample, there are 2 clear outliers with $N_\mathrm{He} / N_\mathrm{H}$ beyond $3\sigma$ of the 0.08 to 1 range, both of them on the lower abundance side: HII region 2 in G010.62 with $0.028\pm0.012$, and HII region 3 in G012.80 with $0.045\pm0.005$ (region 2 is at $2.2\sigma$). Their faint He$41\alpha$ emission compared to hydrogen can be seen in Fig. [11](#fig:H_He_fitplots_app1) for the former and Fig. [5](#fig:H_He_fitplots) for the latter. A proposed explanation for the apparent detection of small He abundances is a geometric effect, in which the He-ionized gas occupies a smaller volume than the H-ionized gas due to the larger ionization potential of helium (cite: RoelfsemaGoss92; DePree1997). This effect is less pronounced in resolved observations such as ours, but it could still be relevant. The derived spectral types for the ionizing stars of these HII regions are O9.5 or later (see Table [\[tab:cont_params\]](#tab:cont_params)), therefore, it is plausible that a softer stellar spectrum in these regions is responsible for the comparatively smaller amounts of ionized helium.

On the high end of the helium abundances, only HII region 2 in W43-MM2 (also known as W43-MM13, see Section [4](#sec:hiis)) is above $1\sigma$ from 0.1, with $N_\mathrm{He} / N_\mathrm{H} = 0.187\pm0.058$. We consider this region as a large He-abundance candidate, also considering its other special characteristics. The spectrum of this source also has the broadest H$41\alpha$ line among the sample ($43.0\pm1.7$ km s$^{-1}$, see Table [\[tab:H41_fits\]](#tab:H41_fits)), and it is clearly double peaked (see Fig. [5](#fig:H_He_fitplots)). We propose that the ionized gas in this source could be produced by a stellar wind enriched by nuclear-processed products. It is known that massive stars can enrich the ISM with extra amounts of He and metals via powerful stellar winds (cite: Crowther07_review), but it is unclear if these phenomena can exist at the $\sim$ ZAMS stages that we are probing. Finally, we note that HII regions 1 and 2 in W51-E have a bright line at the expected position of He$41\alpha$ (see Fig. [11](#fig:H_He_fitplots_app1)). Our fitting procedure rejected it as due to molecular-line contamination, most likely from CH$_3$OCHO lines (see the previous explanation in this Section).

|  |  | H$41\alpha$ |  |  | He$41\alpha$ |  | $N_\mathrm{He}/N_\mathrm{H}$ |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Protocluster | $A$ | $v_\mathrm{LSR}$ | FWHM | $A$ | $v_\mathrm{LSR}$ | FWHM |  |
| HII region | \[K\] | \[km s$^{-1}$\] | \[km s$^{-1}$\] | \[K\] | \[km s$^{-1}$\] | \[km s$^{-1}$\] |  |
| G008.67 1 | $6.64\pm0.023$ | $44.954\pm0.048$ | $28.45\pm0.11$ | $0.678\pm0.026$ | $-76.51\pm0.42$ | $22.20\pm0.98$ | $0.0797\pm0.0047$ |
| G008.67 2 | $0.930\pm0.016$ | $41.05\pm0.19$ | $22.52\pm0.44$ | $0.093\pm0.017$ | $-79.1\pm1.7$ | $18.4\pm3.9$ | $0.082\pm0.023$ |
| G010.62 1 | $13.764\pm0.049$ | $-0.073\pm0.050$ | $28.69\pm0.12$ | $1.216\pm0.054$ | $-122.35\pm0.51$ | $23.4\pm1.2$ | $0.0722\pm0.0049$ |
| G010.62 2 | $2.451\pm0.021$ | $5.916\pm0.089$ | $21.34\pm0.21$ | $0.076\pm0.022$ | $-117.5\pm2.7$ | $19.1\pm6.4$ | $0.028\pm0.012$ |
| G010.62 3 | $4.451\pm0.017$ | $-0.874\pm0.041$ | $22.002\pm0.096$ | $0.337\pm0.018$ | $-123.38\pm0.50$ | $19.1\pm1.2$ | $0.0656\pm0.0054$ |
| G012.80 1 | $3.162\pm0.012$ | $36.752\pm0.058$ | $30.48\pm0.14$ | $0.233\pm0.013$ | $-86.13\pm0.75$ | $27.6\pm1.8$ | $0.0665\pm0.0056$ |
| G012.80 2 | $1.020\pm0.012$ | $36.44\pm0.12$ | $19.56\pm0.28$ | $0.084\pm0.016$ | $-85.7\pm1.1$ | $11.6\pm2.6$ | $0.049\pm0.014$ |
| G012.80 3 | $3.256\pm0.013$ | $29.781\pm0.046$ | $23.68\pm0.11$ | $0.206\pm0.015$ | $-93.93\pm0.61$ | $16.9\pm1.4$ | $0.0452\pm0.0051$ |
| G327.29 1 | $0.6933\pm0.0077$ | $-39.04\pm0.11$ | $19.50\pm0.25$ | $0.0469\pm0.0091$ | $-160.3\pm1.3$ | $14.1\pm3.1$ | $0.049\pm0.014$ |
| G333.60 1 | $0.685\pm0.021$ | $-46.45\pm0.41$ | $27.40\pm0.96$ | – | – | – | – |
| G333.60 2 | $0.593\pm0.015$ | $-47.09\pm0.29$ | $22.94\pm0.68$ | $0.050\pm0.015$ | $-169.0\pm3.5$ | $23.5\pm8.2$ | $0.086\pm0.040$ |
| G333.60 3 | $1.961\pm0.022$ | $-44.77\pm0.11$ | $20.43\pm0.27$ | $0.158\pm0.025$ | $-163.9\pm1.3$ | $16.4\pm3.0$ | $0.065\pm0.016$ |
| G333.60 4 | $5.609\pm0.033$ | $-45.446\pm0.090$ | $31.52\pm0.21$ | $0.485\pm0.037$ | $-167.92\pm0.91$ | $24.4\pm2.2$ | $0.0670\pm0.0078$ |
| G333.60 5 | $0.5027\pm0.0092$ | $-33.13\pm0.18$ | $20.54\pm0.44$ | $0.041\pm0.013$ | $-154.6\pm1.6$ | $10.3\pm3.8$ | $0.041\pm0.020$ |
| G333.60 6 | $0.953\pm0.017$ | $-50.49\pm0.22$ | $24.85\pm0.52$ | $0.072\pm0.025$ | $-173.4\pm2.1$ | $12.1\pm4.8$ | $0.037\pm0.019$ |
| G333.60 7 | $0.913\pm0.017$ | $-45.54\pm0.20$ | $21.86\pm0.47$ | $0.048\pm0.017$ | $-166.9\pm3.9$ | $22.2\pm9.1$ | $0.053\pm0.029$ |
| G333.60 8 | $0.679\pm0.010$ | $-44.61\pm0.17$ | $22.47\pm0.39$ | $0.082\pm0.011$ | $-166.1\pm1.3$ | $20.9\pm3.1$ | $0.113\pm0.022$ |
| G337.92 1 | $0.2997\pm0.0051$ | $-34.78\pm0.17$ | $20.82\pm0.41$ | $0.0347\pm0.0069$ | $-156.8\pm1.1$ | $11.5\pm2.6$ | $0.064\pm0.019$ |
| G337.92 2 | $0.2190\pm0.0063$ | $-32.74\pm0.30$ | $21.23\pm0.71$ | – | – | – | – |
| G351.77 1 | $1.392\pm0.015$ | $-1.67\pm0.11$ | $21.19\pm0.27$ | – | – | – | – |
| G351.77 2 | $0.561\pm0.083$ | $-9.8\pm1.2$ | $16.5\pm2.8$ | – | – | – | – |
| G353.41 1 | $0.3239\pm0.0073$ | $-17.00\pm0.22$ | $20.38\pm0.53$ | $0.046\pm0.010$ | $-137.1\pm1.1$ | $10.3\pm2.6$ | $0.072\pm0.025$ |
| G353.41 2 | $0.5077\pm0.0079$ | $-16.11\pm0.20$ | $25.50\pm0.46$ | $0.0366\pm0.0082$ | $-139.6\pm2.6$ | $23.7\pm6.2$ | $0.067\pm0.023$ |
| G353.41 3 | $1.847\pm0.012$ | $-14.335\pm0.095$ | $30.82\pm0.22$ | – | – | – | – |
| W43-MM2 1 | $0.96\pm0.17$ | $92.0\pm2.3$ | $26.6\pm5.5$ | – | – | – | – |
| W43-MM2 2 | $0.471\pm0.016$ | $95.57\pm0.71$ | $43.0\pm1.7$ | $0.070\pm0.014$ | $-27.2\pm5.4$ | $54\pm13$ | $0.187\pm0.058$ |
| W43-MM3 1 | $3.0781\pm0.0093$ | $90.944\pm0.036$ | $24.018\pm0.084$ | $0.289\pm0.010$ | $-31.86\pm0.34$ | $19.31\pm0.80$ | $0.0755\pm0.0041$ |
| W51-E 1 | $16.81\pm0.13$ | $59.17\pm0.10$ | $27.13\pm0.25$ | – | – | – | – |
| W51-E 2 | $3.794\pm0.052$ | $56.35\pm0.15$ | $21.87\pm0.34$ | – | – | – | – |
| W51-E 3 | $2.802\pm0.011$ | $57.908\pm0.054$ | $27.44\pm0.13$ | $0.299\pm0.012$ | $-63.81\pm0.46$ | $22.7\pm1.1$ | $0.0882\pm0.0056$ |
| W51-E 4 | $1.485\pm0.045$ | $51.79\pm0.42$ | $27.95\pm0.98$ | – | – | – | – |
| W51-E 5 | $2.458\pm0.017$ | $67.307\pm0.076$ | $21.93\pm0.18$ | $0.273\pm0.021$ | $-53.68\pm0.56$ | $15.0\pm1.3$ | $0.0758\pm0.0089$ |
| W51-IRS2 1 | $5.519\pm0.027$ | $56.907\pm0.067$ | $27.55\pm0.16$ | $0.704\pm0.030$ | $-64.22\pm0.47$ | $22.2\pm1.1$ | $0.1030\pm0.0069$ |
| W51-IRS2 2 | $1.144\pm0.038$ | $48.90\pm0.46$ | $28.1\pm1.1$ | $0.256\pm0.067$ | $-71.5\pm1.2$ | $9.1\pm2.8$ | $0.072\pm0.029$ |

# Discussion

## On the subtraction of free-free contamination in (sub)mm observations of dust continuum

Any millimeter survey aimed at studying dust continuum emission has the issue of potential free-free contamination. This becomes more relevant with the availability of sensitive observations of the innermost parts of star-forming cores and young stellar objects, where free-free emission from ionized jets, photoevaporating disks, and the birth of HII regions are expected to contribute to the observed flux (cite: vdTM05; CG2012; Rota24).

There are three main observational methods to estimate the free-free contribution in millimeter maps: i) the most common method is using centimeter-wavelength images taken with, e.g., the VLA, and extrapolate them to the millimeter assuming a spectral index $\alpha_\mathrm{ff}$ for the free-free emission. This method usually assumes $\alpha_\mathrm{ff}=-0.1$, characteristic of the optically-thin regime (see Section [3.3](#sec:validation)); ii) creating spectral index $\alpha$ maps between two continuum bands, or measuring $\alpha$ within a given aperture. Free-free emission has a spectral index $\alpha_\mathrm{ff}$ that changes from 2 to $-0.1$ as frequency increases and the emission transitions from optically thick to thin. In contrast, the spectral index of dust emission in the radio and (sub)mm $\alpha_\mathrm{dust}$ has the opposite behavior with frequency, it changes from $\lesssim 4$ (optically thin) to 2 (thick) with increasing frequency. These opposite trends with frequency enable to create spectral index masks to exclude dust cores that are significantly contaminated by free-free (cite: Pouteau22). (cite: DiazGonzalez23) provided spectral index maps sensitive to extended emission between 3 mm and 1 mm, using their combination of the ALMA-IMF continuum maps and single-dish surveys. This method, however, does not provide an estimate of the free-free emission in intensity units, but rather serve as rejection filter to separate contaminated from non-contaminated areas; and iii) the method that is systematically used in this paper.

The main advantages of estimating the free-free contribution with our method are that all the surveyed protoclusters are observed with a $(u,v)$ coverage and beamsize close to the continuum images, and that the subsequent frequency scaling factor of the free-free estimation is more accurate and numerically closer to 1 (see Section [3.3](#sec:validation)).

However, our proposed method has its own caveats, namely: i) the free-free map derived from the recombination line is less sensitive than the corresponding millimeter continuum image. Therefore, it is not able to detect the faintest ionized emission that could be present in the continuum maps; ii) the H$41\alpha$ emission is assumed to be in local thermodynamic equilibrium (LTE). This is a good assumption for most conditions; and iii) molecular line contamination of the recombination line emission can be an issue in a few very line-rich objects objects (cite: Law2021; Brouillet22).

## A search for sites with excess recombination line emission

In this section, we look for regions within the ALMA-IMF images where the H$41\alpha$ line could be brighter than the LTE expectation. There is evidence for the rare occurrence of (mostly weak) recombination line masers in massive star formation regions. The massive young star MonR2-IRS2 has a (sub)mm maser with an amplification factor in the range 2 to 3 with respect to LTE (cite: JS20). This type of maser is expected to occur in the (sub)mm range if the density conditions are appropriate (cite: Walmsley90; Peters12; Zhu22).

We looked for areas in our maps which could be the sites of amplification of the H$41\alpha$ line. For this, we inspected the pure dust estimation maps (total intensity minus free-free maps after convolution and regridding, see Section [3.1](#sec:proc)) and looked for areas that are significantly negative, i.e., that have negative “potholes”. A naive interpretation of those potholes would be that they are regions where the H$41\alpha$ is brighter than the LTE assumption in Equation [\[eq:ff_map\]](#eq:ff_map). We applied the following criteria for our search: i) that the pothole is clearly visible both in the Band 3 and Band 6 subtraction (pure dust) maps; ii) that the Band 3 and Band 6 potholes have an area larger than one beamsize (this is to avoid negative fluctuations of a few pixels in size); and iii) that the absolute value of the pothole minimum be larger than the respective error in the free-free estimation, both in Band 3 and Band 6.

We found that when the respective error maps are taken into account (third criterion above), all the cases potholes are consistent with zero. Therefore, we do not consider them of high significance. Fig. [7](#fig:potholes-maser) shows the case of G010.62, where a clear “pothole” is seen at the position of the well-known UC HII region at the center (cite: KetoWood2006; GM23). This target was our clearest candidate, yet the central hole is within $1\sigma$ of the free-free estimation error at that position. We conclude that there is no significant evidence for H$41\alpha$ masers in the ALMA-IMF data, and that the areas where the continuum appears to be oversubtracted, notably in the 3 mm maps, are due to the inherent uncertainties in the derivation of the free-free estimations (see Eqs. [\[eq:ff_map\]](#eq:ff_map) and [\[eq:err_ff\]](#eq:err_ff)).

![](G010.62_potholes)

## Evolution of the HII regions in the ALMA-IMF sample

The ALMA-IMF targets were selected to sample the evolutionary stages of massive star formation in clusters, from quiescent clumps that are faint in the infrared bands and lack ionized gas, to active clumps with prominent HII regions (cite: Motte22). Using H$41\alpha$ cubes, we calculated the basic physical properties of their HII regions, such as their emission measure (EM), electron density ($n_e$), and hydrogen-ionizing photon rate ($Q_0$). For the HII regions reported in Table [\[tab:cont_params\]](#tab:cont_params), Figure [8](#fig:HIIprops_2) shows these properties as a function of the effective diameter $D$ of the emission. $Q_0$ is well correlated with $D$, with a Pearson correlation coefficient $r$ and p-value $(r,p) = (0.89,1.6\times10^{-12})$. In contrast, the correlations between $n_e$ and EM with $D$ are not as clear, with $(r,p) = (-0.25,0.15)$ and $(0.12,0.50)$, respectively. A weighted least-squares fit to the $Q_0$ vs $D$ relation gives $\log [Q_0 / \mathrm{s}^{-1}] = (2.49\pm0.18) \times \log [D/\mathrm{pc}] + (49.89\pm0.23)$.

From Eq. (5), the observed $Q_0 \propto D^{2.5}$ relation falls in between the expected relations if $n_e$ or EM were constant among the sample of HII regions ($Q_0 \propto D^3$ or $Q_0 \propto D^2$, respectively). Motivated by this, we fit a posteriori the $n_e$ vs $D$ and EM vs $D$ relations in logarithmic space and find that their respective slope and intercept, with $1\sigma$ errors, are ($-0.23\pm0.08$, $3.70\pm0.10$) and ($0.52\pm0.17$, $7.39\pm0.22$). Taking $Q_0 \propto D^{2.5}$ as valid, it is indeed expected that $n_e \propto D^{-0.25}$ and $\mathrm{EM} \propto D^{0.5}$.

Previous authors have reported inverse correlations between $n_e$ and $D$ in samples of UC HII regions, with power-law slopes $\approx -1$ (cite: GarayLizano99; KimKoo01). If the ionizing stars had constant $Q_0$ across the sample, then $n_e \propto D^{-1.5}$ is expected. However, there is no reason to think that all UC HII regions will be ionized by stars of the same mass at the moment of observation, and to follow the same path on the $n_e$ vs $D$ diagram as they expand and rarefy. A possible cause for our differing results with respect to previous surveys is that those have focused on the brightest UC HII regions within rather evolved targets, selected from their mid-IR colors (cite: WC89; Kurtz94). In contrast, the UC HII regions in our sample are distributed in a broad range of protocluster evolutionary stages, and in different locations within a given protocluster. A homogeneous analysis of a larger sample could help to understand this issue. As pointed out by (cite: GarayLizano99), a positive correlation in the $Q_0$ vs $D$ diagram (bottom panel of Fig. [8](#fig:HIIprops_2)) indicates that the smallest UC HII regions are on average ionized by less massive stars. Therefore, it could be that the smaller HII regions in our sample are not necessarily dynamically younger, or at least that the effect of the ionizing spectral type is larger than the effect of age. A lack of a direct relation between UC HII region size and other measured properties has been previously proposed as a solution to the apparent (excess) lifetime “problem” of UC HII regions (cite: Peters2010a; Peters2010b; DePree2014). Another possible explanation for differing results in the $n_e$ vs $D$ relation is environment. For example, the recent study by (cite: Meng22) of the UC HII regions in the extreme protocluster Sgr B2 found that $n_e$ and $D$ follow an inverse relation, but with significant scatter and at higher densities than previous studies in other regions. Similarly, (cite: Yang21) analyzed several samples of UC HII regions and found that their physical properties probably shift with evolution. Finally, the presence or absence of ionized haloes around UC HII regions and the ability of interferometric observations to recover them might have an effect too (cite: KimKoo01). Fig. [8](#fig:HIIprops_2) labels the outliers from the fitted relations. The most notable ones with an excess in $n_e$, EM, or $Q_0$ are HII regions 1 and 4 in W51-E, followed by HII region 1 in W43-MM2, 1 in G008.67, and 2 in W51-E. The UC HII regions in the north-south dust ridge of W51-E (which we label 1 and 2) are known to have active infall signatures (cite: Zhang98; Goddi16).

![image](ne_individual.png)\
![image](EM_individual.png)\
![image](Q0_individual.png)

We now calculate the corresponding H$41\alpha$ dynamical linewidths $\Delta V_\mathrm{dyn}$. The total recombination linewidth is a non-linear sum of collissional (“pressure”), thermal, and dynamical widths (cite: GS02; KZK08). Following the equations in the appendix of (cite: GM12), we estimate that collisional broadening is about $0.05$ km s$^{-1}$ for densities as high as $10^5$ cm$^{-3}$, therefore it can be neglected. The thermal FWHM linewidth at $T_e=7000$ K $\pm 20~\%$ is $17.9\pm1.8$ km s$^{-1}$. Supersonic recombination lines have been suggested to be a signpost of ultracompact and “hypercompact” HII regions with additional physical ingredients beyond the classical hydrodynamical expansion (cite: DePree04; GM09; Sandell09). However, these objects appear to be very rare, including in our survey. Interestingly, $\Delta V_\mathrm{dyn}$ appears to be weakly correlated both with HII region size (Fig. [9](#fig:linewQ0), top panel) and ionizing-photon rate $Q_0$ (bottom panel), with $(r,p) = (0.34, 0.05)$ and $(0.33,0.06)$, respectively. As shown before, HII region size and $Q_0$ are well correlated, therefore the trend of increasing dynamical linewidth with size likely reflects the same underlying physical process. The hydrodynamical expansion velocity of an HII region is expected to be $\lesssim c_s$ (cite: Spitzer78; Bisbas15), where the speed of sound of ionized gas is $c_s \approx 10$ km s$^{-1}$. Therefore, an optically-thin HII region is expected to have an observed dynamical linewidth $\lesssim 2c_s$. Most of the objects in our sample satify this, as shown in Fig. [9](#fig:linewQ0). However, the trend of increasing $\Delta V_\mathrm{dyn}$ with $Q_0$ (spectral type), as well as the small excess linewidth above $2c_s$ at high $Q_0$, suggest that other acceleration mechanisms could play a role at high luminosities. Photoevaporative flows in density gradients, such as those in structured clouds, are able to accelerate HII gas to a few tens of km s$^{-1}$ (cite: ArthurHoare2006; Zamora19). Faster velocities would require the presence of stellar winds. We suggest that this is the case for the HII region south of W43-MM2 (MM13). This HII region stands out with $\Delta V_\mathrm{dyn} = 39.1\pm2.0$ km s$^{-1}$. An embedded stellar or disk wind (cite: Guzman20; GM23) could produce the observed large linewidth in this region, as well as in the other outlier objects with $\Delta V_\mathrm{dyn} > 2c_s$, which are labeled in Fig. [9](#fig:linewQ0). Finally, we keep in mind that our analysis of helium abundances (see Section [5](#sec:line_params)) revealed that the HII region MM13 also has the largest helium abundance $N_\mathrm{He}/N_\mathrm{H} = 0.187\pm0.058$, and that the line in this source is the only one which is clearly double-peaked. A full investigation of the ionizing sources requires the observation and modelling of more recombination lines.

![](linewQ0_indiv)

# Conclusions

We made tailored H$41\alpha$ cubes using the ALMA-IMF pipeline (cite: Ginsburg22; Cunningham2023) to create template maps, and their associated errors, of the free-free emission in the 3 mm and 1.3 mm continuum maps. With this paper we distribute the input cubes, the derived data products, and associated scripts, which can be used to separate the free-free “contamination” from dust emission in ALMA continuum maps for other projects.

We validated our procedure against the more common approach of extrapolating the free-free emission from centimeter maps to millimeter wavelengths. For our benchmark region, we found that both approaches give the same result within the errors for the vast majority of the pixels with emission in both tracers, but that they do not necessarily match in a few UC HII regions where either the recombination line can have excess brightness, or the optically thin ($\propto \nu^{-1}$) extrapolation from the centimeter to the millimeter is underestimation. Another possible issue is molecular line contamination, which we found to be important only in three hot molecular cores.

We used the derived free-free maps to estimate the properties of HII regions across the ALMA-IMF protoclusters. We defined 34 regions of HII emission and measured their photometry. Then, we derived their physical properties such as emission measure (EM), electron density ($n_e$), hydrogen ionizing-photon rate ($Q_0$), and spectral type (SpT) of the (single) ionizing star. $Q_0$ and SpT follow a trend consistent with the evolutionary picture proposed by (cite: Motte22). The youngest protoclusters (W43-MM1, G338.93, G328.25) lack detectable emission from ionized gas. W43-MM2 and G337.92 harbor B-type stars with $Q_0$ of few $\times10^{45}$ s$^{-1}$ (the MM13 region south of MM2 also contains a more luminous B-type star). G351.77 abd G327.29 contain early B-type stars with a total $Q_0$ of few $\times10^{46}$ s$^{-1}$. G353.41 and G008.67 have early B to late O-type stars with $Q_0\sim10^{47}$ s$^{-1}$. The following ALMA-IMF protoclusters (W43-MM3, G012.80, G010.62, W51-IRS2, and W51-E) contain from a few to several O and B-type stars, with $Q_0$ rising from $\sim 1\times$ to $7\times10^{48}$ s$^{-1}$. Finally, G333.60 contains the brightest and largest HII region in the sample, as well as the largest number of OB stars, totalling $Q_0\approx3\times10^{49}$ s$^{-1}$.

We performed measurements of the number abundance of He$^+$ with respect to H$^+$, which is a proxy to the total He-to-H abundance $N_\mathrm{He}/N_\mathrm{H}$ in HII regions. Most of the 25 regions with He$^+$ measurement (see Table [\[tab:H41_fits\]](#tab:H41_fits)) have values consistent with the expected $N_\mathrm{He}/N_\mathrm{H} \approx 0.08$ in the Galactic ISM. Two HII regions appear to have helium abundances significantly below this value. We propose that this is due the relatively late spectral type of their ionizing stars, which produces He$^+$ regions which are smaller than their respective H$^+$ regions. Only one HII region (W43 MM13, south of MM2) appears to have $N_\mathrm{He}/N_\mathrm{H}$ above the standard value.

We looked for sites of significant amplification of the H$41\alpha$ with respect to LTE. This search returned negative results when the errors of the free-free estimation maps are considered.

We investigated the possible correlations between the measured HII region properties in the sample. The correlations $n_e$ and equivalent diameter $D$ and between EM and $D$ are weak. In contrast, $Q_0$ and $D$ are well correlated and have a linear dependence in log-log space with an exponent $\approx 2.5$. This favors an interpretation where the smaller UC HII regions are not necessarily the less dynamically evolved versions of the larger ones, but that rather they are on average ionized by less massive stars. Finally, the dynamical width $\Delta V_\mathrm{dyn}$ of the HII regions in the sample was deconvolved from the thermal and collisional widths, the latter of which is totally negligible. Moderate positive correlations were found between $\Delta V_\mathrm{dyn}$ and $D$, and between $\Delta V_\mathrm{dyn}$ and $Q_0$. Dynamical widths vary from approximately the speed of sound of ionized gas $c_s$ to $\gtrsim 2c_s$, with MM13 being again an outlier with $\Delta V_\mathrm{dyn} \approx 4c_s$. The trend among the sample of increasing $\Delta V_\mathrm{dyn}$ with $Q_0$ suggests that, in the HII regions ionized by the most massive stars, further mechanisms such as disk or stellar winds could play a role in their kinematics.

# Acknowledgements

We thank the anonymous referee for a detailed report, which helped to many aspects of this paper. R.G.M., D.D.G., and R.R.S. acknowledge support from UNAM-PAPIIT project IN108822 and from CONACyT Ciencia de Frontera project ID 86372. A.G. acknowledges support from the NSF under grants AST 2008101 and CAREER 2142300. T.Cs. has received financial support from the French State in the framework of the IdEx Université de Bordeaux Investments for the future Program. A.M.S. gratefully acknowledges support by the Fondecyt Regular (project code 1220610), and ANID BASAL project FB210003. R.A.G. gratefully acknowledges support from ANID Beca Doctorado Nacional 21200897. L.B. gratefully acknowledges support by the ANID BASAL project FB210003.

# Software

`Astropy` (cite: Astropy2013; Astropy2018), `PySpecKit` (cite: Ginsburg22_pyspeckit), `CASA` (cite: CASA2022), APLpy (cite: APLpy)

# Comparison of original, free-free, and pure-dust maps

Fig. [10](#fig:comparison-maps-app) shows comparison plots, covering the areas with free-free emission, of the original 1.3 mm continuum maps and the corresponding free-free and pure-dust estimations.

![image](G008.67_orig_ff_dust.png) \
![image](G010.62_orig_ff_dust.png) \
![image](G012.80_orig_ff_dust.png) \
![image](G327.29_orig_ff_dust.png) 

![image](G333.60_orig_ff_dust.png) \
![image](G337.92_orig_ff_dust.png) \
![image](G351.77_orig_ff_dust.png) \
![image](G353.41_orig_ff_dust.png) 

![image](W43-MM2_orig_ff_dust.png) \
![image](W43-MM3_orig_ff_dust.png) \
![image](W51-E_orig_ff_dust.png) \
![image](W51-IRS2_orig_ff_dust.png) 

# Filenames and data products

We make available the following FITS images in the following url, hosted by the Harvard Dataverse service:\
<https://doi.org/10.7910/DVN/LWILNE>

- The image cubes containing the hydrogen and helium $41\alpha$ lines, prior to primary-beam correction (see Section [3.1](#sec:proc)): `FIELD_B3_spw1_12M_h41a.JvM.image.contsub.fits`.

- The regridded free-free estimation $I_{\mathrm{ff},\nu}$ for each protocluster at the standard ALMA-IMF `cleanest` continuum frequencies of 98.5 and 224.5 GHz. The filenames start with the basename `FIELD_B3_spw1_12M_h41a.JvM.image.contsub`, which is standard naming within the ALMA-IMF data reduction pipeline (cite: Ginsburg22). The filenames are then followed by `.m0.ffXXX.XGHz_Y.Ysigma.regr`, which denotes the fact that they are obtained from a moment 0 map, the frequency of the calculation, the threshold in the moment 0 map above which Eq. [\[eq:ff_map\]](#eq:ff_map) is applied, and the applied regridding. Finally, the filenames end with either `.pbcor.fits` or just with `.fits`, depending on whether primary-beam correction is applied or not at the end of the procedure (see Fig. [1](#fig:flowchart)). An example filename with PB correction is `W51-IRS2_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff224.5GHz_5.0sigma.regr.pbcor.fits`.

- The error $\sigma_\mathrm{ff}$ of the free-free estimation. Following the same nomenclature as above but with `.err` in the filename, e.g., `W51-IRS2_B3_spw1_12M_h41a.JvM.image.contsub.m0.ff224.5GHz_5.0sigma.err.regr.pbcor.fits`.

- The `cleanest` continuum image from the release of (cite: Ginsburg22) convolved to the beamsize of the H$41\alpha$ cube. The filename is the same as in the ALMA-IMF data release, but ending with `.conv.fits`. For example:\
  `W51-IRS2_B6_uid___A001_X1296_X187_continuum_merged_12M_robust0_selfcal9_finaliter.image.tt0.conv.fits`

- Estimates of pure dust continuum emission, from the subtraction of the original continuum images minus the free-free estimations, with and without PB correction. The basename of these images is the same as for the original continuum images, but ending with `.conv.ffsub_Y.Ysigma.fits`.

# Hydrogen and helium $41\alpha$ fitting in the rest of the HII regions

Below we show the H$41\alpha$ and He$41\alpha$ fitting in the rest of the HII regions defined in Section [4](#sec:hiis), and not shown Fig. [5](#fig:H_He_fitplots).

![](fitplots_merged_app1.png)

![](fitplots_merged_app2.png)

# Abundance and metallicity definitions

In most contexts within astronomy, such as in stellar astrophysics and nucleosynthesis, elemental abundances are given in mass units relative to the total mass $M$ as in: $$\begin{equation}
X + Y + Z = 1, 
\end{equation}$$

where $X$, $Y$, and $Z$ refer to the hydrogen, helium, and “metals” respectively.

Therefore, the relative mass abundance of helium is given by: $$\begin{equation}
Y = 1 - Z - \frac{m_\mathrm{H} N_\mathrm{H}}{M},     
\end{equation}$$

where $m_\mathrm{H}$ is the mass of atomic hydrogen, $N_\mathrm{H}$ is the total number of hydrogen atoms.

Rearranging in terms of observables we have: $$\begin{equation}
Y = (1-Z) \biggl( 1 - \frac{1}{1+(N_\mathrm{He} / N_\mathrm{H}) (m_\mathrm{He} / m_\mathrm{H})}   \biggr),     
\end{equation}$$

where the atomic He-to-H mass ratio is $4.002062 / 1.00784 = 3.97147$.

The solar metallicity is often quoted as $Z_\odot = 0.02$, but recent revisions have taken the value down to $Z_\odot = 0.0153$ (cite: Caffau2011), a value which is used in modern stellar models (cite: Bressan12). Excluding the low- and high-outliers G353.41 and W43-MM2, our typical measured values for $N_\mathrm{He} / N_\mathrm{H}$ in the ALMA-IMF HII regions are in the range from 0.065 to 0.104, with typical errors of $\pm 0.005$. Using $Z_\odot$ from (cite: Caffau2011), this translates into $Y = 0.202\pm0.012$ to $Y = 0.288\pm0.010$. These values are consistent with the inferred value $Z_\odot/X_\odot = 0.0209$, $Y_\odot = 0.2526$ by (cite: Caffau2011). Increasing $Z_\odot$ to 0.02 decreases the inferred values of $Y$ by $\sim 0.001$.

natexlab

(ref: Anderson21) Anderson, L. D., Luisi, M., Liu, B., et al. 2021, ApJS, 254, 28, doi: [`10.3847/1538-4365/abef65`](http://doi.org/10.3847/1538-4365/abef65)

(ref: Armante24) Armante, M., Gusdorf, A., Louvet, F., et al. 2024, A&A, 686, A122, doi: [`10.1051/0004-6361/202347595`](http://doi.org/10.1051/0004-6361/202347595)

(ref: ArthurHoare2006) Arthur, S. J., & Hoare, M. G. 2006, ApJS, 165, 283, doi: [`10.1086/503899`](http://doi.org/10.1086/503899)

(ref: Astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Bisbas15) Bisbas, T. G., Haworth, T. J., Williams, R. J. R., et al. 2015, MNRAS, 453, 1324, doi: [`10.1093/mnras/stv1659`](http://doi.org/10.1093/mnras/stv1659)

(ref: Bonfand24_arxiv) Bonfand, M., Csengeri, T., Bontemps, S., et al. 2024, arXiv e-prints, arXiv:2402.15023, doi: [`10.48550/arXiv.2402.15023`](http://doi.org/10.48550/arXiv.2402.15023)

(ref: Bressan12) Bressan, A., Marigo, P., Girardi, L., et al. 2012, MNRAS, 427, 127, doi: [`10.1111/j.1365-2966.2012.21948.x`](http://doi.org/10.1111/j.1365-2966.2012.21948.x)

(ref: Brouillet22) Brouillet, N., Despois, D., Molet, J., et al. 2022, A&A, 665, A140, doi: [`10.1051/0004-6361/202243669`](http://doi.org/10.1051/0004-6361/202243669)

(ref: Caffau2011) Caffau, E., Ludwig, H. G., Steffen, M., Freytag, B., & Bonifacio, P. 2011, Sol. Phys., 268, 255, doi: [`10.1007/s11207-010-9541-4`](http://doi.org/10.1007/s11207-010-9541-4)

(ref: CG2012) Carrasco-González, C., Galván-Madrid, R., Anglada, G., et al. 2012, ApJL, 752, L29, doi: [`10.1088/2041-8205/752/2/L29`](http://doi.org/10.1088/2041-8205/752/2/L29)

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Churchwell02) Churchwell, E. 2002, ARA&A, 40, 27, doi: [`10.1146/annurev.astro.40.060401.093845`](http://doi.org/10.1146/annurev.astro.40.060401.093845)

(ref: Crowther07_review) Crowther, P. A. 2007, ARA&A, 45, 177, doi: [`10.1146/annurev.astro.45.051806.110615`](http://doi.org/10.1146/annurev.astro.45.051806.110615)

(ref: Csengeri17) Csengeri, T., Bontemps, S., Wyrowski, F., et al. 2017, A&A, 601, A60, doi: [`10.1051/0004-6361/201628254`](http://doi.org/10.1051/0004-6361/201628254)

(ref: Csengeri14) Csengeri, T., Urquhart, J. S., Schuller, F., et al. 2014, A&A, 565, A75, doi: [`10.1051/0004-6361/201322434`](http://doi.org/10.1051/0004-6361/201322434)

(ref: Cunningham2023) Cunningham, N., Ginsburg, A., Galván-Madrid, R., et al. 2023, A&A, 678, A194, doi: [`10.1051/0004-6361/202245429`](http://doi.org/10.1051/0004-6361/202245429)

(ref: DePree1997) De Pree, C. G., Mehringer, D. M., & Goss, W. M. 1997, ApJ, 482, 307, doi: [`10.1086/304119`](http://doi.org/10.1086/304119)

(ref: DePree04) De Pree, C. G., Wilner, D. J., Mercer, A. J., et al. 2004, ApJ, 600, 286, doi: [`10.1086/379755`](http://doi.org/10.1086/379755)

(ref: DePree2014) De Pree, C. G., Peters, T., Mac Low, M. M., et al. 2014, ApJL, 781, L36, doi: [`10.1088/2041-8205/781/2/L36`](http://doi.org/10.1088/2041-8205/781/2/L36)

(ref: DiazGonzalez23) Dı́az-González, D. J., Galván-Madrid, R., Ginsburg, A., et al. 2023, ApJS, 269, 55, doi: [`10.3847/1538-4365/ad029c`](http://doi.org/10.3847/1538-4365/ad029c)

(ref: GM12) Galván-Madrid, R., Goddi, C., & Rodrı́guez, L. F. 2012, A&A, 547, L3, doi: [`10.1051/0004-6361/201220330`](http://doi.org/10.1051/0004-6361/201220330)

(ref: GM09) Galván-Madrid, R., Keto, E., Zhang, Q., et al. 2009, ApJ, 706, 1036, doi: [`10.1088/0004-637X/706/2/1036`](http://doi.org/10.1088/0004-637X/706/2/1036)

(ref: GM23) Galván-Madrid, R., Zhang, Q., Izquierdo, A., et al. 2023, ApJL, 942, L7, doi: [`10.3847/2041-8213/aca9cb`](http://doi.org/10.3847/2041-8213/aca9cb)

(ref: GarayLizano99) Garay, G., & Lizano, S. 1999, PASP, 111, 1049, doi: [`10.1086/316416`](http://doi.org/10.1086/316416)

(ref: Ginsburg22_pyspeckit) Ginsburg, A., Sokolov, V., de Val-Borro, M., et al. 2022a, AJ, 163, 291, doi: [`10.3847/1538-3881/ac695a`](http://doi.org/10.3847/1538-3881/ac695a)

(ref: Ginsburg16) Ginsburg, A., Goss, W. M., Goddi, C., et al. 2016, A&A, 595, A27, doi: [`10.1051/0004-6361/201628318`](http://doi.org/10.1051/0004-6361/201628318)

(ref: Ginsburg17) Ginsburg, A., Goddi, C., Kruijssen, J. M. D., et al. 2017, ApJ, 842, 92, doi: [`10.3847/1538-4357/aa6bfa`](http://doi.org/10.3847/1538-4357/aa6bfa)

(ref: Ginsburg22) Ginsburg, A., Csengeri, T., Galván-Madrid, R., et al. 2022b, A&A, 662, A9, doi: [`10.1051/0004-6361/202141681`](http://doi.org/10.1051/0004-6361/202141681)

(ref: Goddi16) Goddi, C., Ginsburg, A., & Zhang, Q. 2016, A&A, 589, A44, doi: [`10.1051/0004-6361/201527855`](http://doi.org/10.1051/0004-6361/201527855)

(ref: GS02) Gordon, M. A., & Sorochenko, R. L. 2002, Radio Recombination Lines. Their Physics and Astronomical Applications, Vol. 282, doi: [`10.1007/978-0-387-09604-9`](http://doi.org/10.1007/978-0-387-09604-9)

(ref: Guzman20) Guzmán, A. E., Sanhueza, P., Zapata, L., Garay, G., & Rodrı́guez, L. F. 2020, ApJ, 904, 77, doi: [`10.3847/1538-4357/abbe09`](http://doi.org/10.3847/1538-4357/abbe09)

(ref: Hoare07) Hoare, M. G., Kurtz, S. E., Lizano, S., Keto, E., & Hofner, P. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 181. [`https://arxiv.org/abs/astro-ph/0603560`](https://arxiv.org/abs/astro-ph/0603560)

(ref: JS20) Jiménez-Serra, I., Báez-Rubio, A., Martı́n-Pintado, J., Zhang, Q., & Rivilla, V. M. 2020, ApJL, 897, L33, doi: [`10.3847/2041-8213/aba050`](http://doi.org/10.3847/2041-8213/aba050)

(ref: JvM95) Jorsater, S., & van Moorsel, G. A. 1995, AJ, 110, 2037, doi: [`10.1086/117668`](http://doi.org/10.1086/117668)

(ref: Keto02) Keto, E. 2002, ApJ, 580, 980, doi: [`10.1086/343794`](http://doi.org/10.1086/343794)

(ref: KetoWood2006) Keto, E., & Wood, K. 2006, ApJ, 637, 850, doi: [`10.1086/498611`](http://doi.org/10.1086/498611)

(ref: KZK08) Keto, E., Zhang, Q., & Kurtz, S. 2008, ApJ, 672, 423, doi: [`10.1086/522570`](http://doi.org/10.1086/522570)

(ref: KimKoo01) Kim, K.-T., & Koo, B.-C. 2001, ApJ, 549, 979, doi: [`10.1086/319447`](http://doi.org/10.1086/319447)

(ref: Kim18) Kim, W. J., Urquhart, J. S., Wyrowski, F., Menten, K. M., & Csengeri, T. 2018, A&A, 616, A107, doi: [`10.1051/0004-6361/201732330`](http://doi.org/10.1051/0004-6361/201732330)

(ref: Kim17) Kim, W. J., Wyrowski, F., Urquhart, J. S., Menten, K. M., & Csengeri, T. 2017, A&A, 602, A37, doi: [`10.1051/0004-6361/201629764`](http://doi.org/10.1051/0004-6361/201629764)

(ref: Klaassen18) Klaassen, P. D., Johnston, K. G., Urquhart, J. S., et al. 2018, A&A, 611, A99, doi: [`10.1051/0004-6361/201731727`](http://doi.org/10.1051/0004-6361/201731727)

(ref: Kurtz05) Kurtz, S. 2005, in Massive Star Birth: A Crossroads of Astrophysics, ed. R. Cesaroni, M. Felli, E. Churchwell, & M. Walmsley, Vol. 227, 111–119, doi: [`10.1017/S1743921305004424`](http://doi.org/10.1017/S1743921305004424)

(ref: Kurtz94) Kurtz, S., Churchwell, E., & Wood, D. O. S. 1994, ApJS, 91, 659, doi: [`10.1086/191952`](http://doi.org/10.1086/191952)

(ref: Law2021) Law, C. J., Zhang, Q., Öberg, K. I., et al. 2021, ApJ, 909, 214, doi: [`10.3847/1538-4357/abdeb8`](http://doi.org/10.3847/1538-4357/abdeb8)

(ref: Liu19) Liu, H. B., Chen, H.-R. V., Román-Zúñiga, C. G., et al. 2019, ApJ, 871, 185, doi: [`10.3847/1538-4357/aaf6b4`](http://doi.org/10.3847/1538-4357/aaf6b4)

(ref: Martins05) Martins, F., Schaerer, D., & Hillier, D. J. 2005, A&A, 436, 1049, doi: [`10.1051/0004-6361:20042386`](http://doi.org/10.1051/0004-6361:20042386)

(ref: MendezDelgado20) Méndez-Delgado, J. E., Esteban, C., Garcı́a-Rojas, J., Arellano-Córdova, K. Z., & Valerdi, M. 2020, MNRAS, 496, 2726, doi: [`10.1093/mnras/staa1705`](http://doi.org/10.1093/mnras/staa1705)

(ref: Meng22) Meng, F., Sánchez-Monge, Á., Schilke, P., et al. 2022, A&A, 666, A31, doi: [`10.1051/0004-6361/202243674`](http://doi.org/10.1051/0004-6361/202243674)

(ref: Motte2003) Motte, F., Schilke, P., & Lis, D. C. 2003, ApJ, 582, 277, doi: [`10.1086/344538`](http://doi.org/10.1086/344538)

(ref: Motte18_NatAs) Motte, F., Nony, T., Louvet, F., et al. 2018, Nature Astronomy, 2, 478, doi: [`10.1038/s41550-018-0452-x`](http://doi.org/10.1038/s41550-018-0452-x)

(ref: Motte22) Motte, F., Bontemps, S., Csengeri, T., et al. 2022, A&A, 662, A8, doi: [`10.1051/0004-6361/202141677`](http://doi.org/10.1051/0004-6361/202141677)

(ref: Quang17) Nguyen-Luong, Q., Anderson, L. D., Motte, F., et al. 2017, ApJL, 844, L25, doi: [`10.3847/2041-8213/aa7d48`](http://doi.org/10.3847/2041-8213/aa7d48)

(ref: Nony2023) Nony, T., Galván-Madrid, R., Motte, F., et al. 2023, A&A, 674, A75, doi: [`10.1051/0004-6361/202244762`](http://doi.org/10.1051/0004-6361/202244762)

(ref: Nony24) Nony, T., Galván-Madrid, R., Brouillet, N., et al. 2024, A&A, 687, A84, doi: [`10.1051/0004-6361/202449279`](http://doi.org/10.1051/0004-6361/202449279)

(ref: Osterbrock89) Osterbrock, D. E. 1989, Astrophysics of gaseous nebulae and active galactic nuclei

(ref: Panagia73) Panagia, N. 1973, AJ, 78, 929, doi: [`10.1086/111498`](http://doi.org/10.1086/111498)

(ref: Peters2010a) Peters, T., Banerjee, R., Klessen, R. S., et al. 2010a, ApJ, 711, 1017, doi: [`10.1088/0004-637X/711/2/1017`](http://doi.org/10.1088/0004-637X/711/2/1017)

(ref: Peters12) Peters, T., Longmore, S. N., & Dullemond, C. P. 2012, MNRAS, 425, 2352, doi: [`10.1111/j.1365-2966.2012.21676.x`](http://doi.org/10.1111/j.1365-2966.2012.21676.x)

(ref: Peters2010b) Peters, T., Mac Low, M.-M., Banerjee, R., Klessen, R. S., & Dullemond, C. P. 2010b, ApJ, 719, 831, doi: [`10.1088/0004-637X/719/1/831`](http://doi.org/10.1088/0004-637X/719/1/831)

(ref: Pouteau22) Pouteau, Y., Motte, F., Nony, T., et al. 2022, A&A, 664, A26, doi: [`10.1051/0004-6361/202142951`](http://doi.org/10.1051/0004-6361/202142951)

(ref: Pouteau23) —. 2023, A&A, 674, A76, doi: [`10.1051/0004-6361/202244776`](http://doi.org/10.1051/0004-6361/202244776)

(ref: Purcell13) Purcell, C. R., Hoare, M. G., Cotton, W. D., et al. 2013, ApJS, 205, 1, doi: [`10.1088/0067-0049/205/1/1`](http://doi.org/10.1088/0067-0049/205/1/1)

(ref: RS20) Rivera-Soto, R., Galván-Madrid, R., Ginsburg, A., & Kurtz, S. 2020, ApJ, 899, 94, doi: [`10.3847/1538-4357/aba749`](http://doi.org/10.3847/1538-4357/aba749)

(ref: APLpy) Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python, Astrophysics Source Code Library, record ascl:1208.017

(ref: RoelfsemaGoss92) Roelfsema, P. R., & Goss, W. M. 1992, A&ARv, 4, 161, doi: [`10.1007/BF00874056`](http://doi.org/10.1007/BF00874056)

(ref: Rosero19) Rosero, V., Hofner, P., Kurtz, S., et al. 2019, ApJ, 880, 99, doi: [`10.3847/1538-4357/ab2595`](http://doi.org/10.3847/1538-4357/ab2595)

(ref: Roshi05) Roshi, D. A., Balser, D. S., Bania, T. M., Goss, W. M., & De Pree, C. G. 2005, ApJ, 625, 181, doi: [`10.1086/429313`](http://doi.org/10.1086/429313)

(ref: Rota24) Rota, A. A., Meijerhof, J. D., van der Marel, N., et al. 2024, A&A, 684, A134, doi: [`10.1051/0004-6361/202348387`](http://doi.org/10.1051/0004-6361/202348387)

(ref: Rugel19) Rugel, M. R., Rahner, D., Beuther, H., et al. 2019, A&A, 622, A48, doi: [`10.1051/0004-6361/201834068`](http://doi.org/10.1051/0004-6361/201834068)

(ref: Sandell09) Sandell, G., Goss, W. M., Wright, M., & Corder, S. 2009, ApJL, 699, L31, doi: [`10.1088/0004-637X/699/1/L31`](http://doi.org/10.1088/0004-637X/699/1/L31)

(ref: Schuller09) Schuller, F., Menten, K. M., Contreras, Y., et al. 2009, A&A, 504, 415, doi: [`10.1051/0004-6361/200811568`](http://doi.org/10.1051/0004-6361/200811568)

(ref: Shi10) Shi, H., Zhao, J.-H., & Han, J. L. 2010, ApJ, 710, 843, doi: [`10.1088/0004-637X/710/1/843`](http://doi.org/10.1088/0004-637X/710/1/843)

(ref: Spitzer78) Spitzer, L. 1978, Physical processes in the interstellar medium, doi: [`10.1002/9783527617722`](http://doi.org/10.1002/9783527617722)

(ref: vdTM05) van der Tak, F. F. S., & Menten, K. M. 2005, A&A, 437, 947, doi: [`10.1051/0004-6361:20052872`](http://doi.org/10.1051/0004-6361:20052872)

(ref: Walmsley90) Walmsley, C. M. 1990, A&AS, 82, 201

(ref: Wenger19) Wenger, T. V., Balser, D. S., Anderson, L. D., & Bania, T. M. 2019, ApJ, 887, 114, doi: [`10.3847/1538-4357/ab53d3`](http://doi.org/10.3847/1538-4357/ab53d3)

(ref: Wilson09) Wilson, T. L., Rohlfs, K., & Hüttemeister, S. 2009, Tools of Radio Astronomy, doi: [`10.1007/978-3-540-85122-6`](http://doi.org/10.1007/978-3-540-85122-6)

(ref: WC89) Wood, D. O. S., & Churchwell, E. 1989, ApJS, 69, 831, doi: [`10.1086/191329`](http://doi.org/10.1086/191329)

(ref: Wyrowski97) Wyrowski, F., Schilke, P., Hofner, P., & Walmsley, C. M. 1997, ApJL, 487, L171, doi: [`10.1086/310893`](http://doi.org/10.1086/310893)

(ref: Yang21) Yang, A. Y., Urquhart, J. S., Thompson, M. A., et al. 2021, A&A, 645, A110, doi: [`10.1051/0004-6361/202038608`](http://doi.org/10.1051/0004-6361/202038608)

(ref: Zamora19) Zamora-Avilés, M., Vázquez-Semadeni, E., González, R. F., et al. 2019, MNRAS, 487, 2200, doi: [`10.1093/mnras/stz1235`](http://doi.org/10.1093/mnras/stz1235)

(ref: Zhang98) Zhang, Q., Ho, P. T. P., & Ohashi, N. 1998, ApJ, 494, 636, doi: [`10.1086/305243`](http://doi.org/10.1086/305243)

(ref: Zhang22) Zhang, Y., Tanaka, K. E. I., Tan, J. C., et al. 2022, ApJ, 936, 68, doi: [`10.3847/1538-4357/ac847f`](http://doi.org/10.3847/1538-4357/ac847f)

(ref: Zhu22) Zhu, F. Y., Wang, J. Z., Zhu, Q. F., & Zhang, J. S. 2022, A&A, 665, A94, doi: [`10.1051/0004-6361/202142305`](http://doi.org/10.1051/0004-6361/202142305)

[^1]: The scripts to apply the JvM correction that were used for the imaging presented in this paper and in (cite: Cunningham2023) can be found in <https://github.com/radio-astro-tools/beam-volume-tools>

[^2]: <https://github.com/ALMA-IMF/reduction>

[^3]: <https://github.com/ALMA-IMF/h41a-freefree>

[^4]: In the ancillary VLA continuum data for the observable ALMA-IMF protoclusters, the synthesized beam is usually larger and always more elliptical than in the ALMA images (Rivera-Soto et al., in prep.).

[^5]: The brightness of radio and (sub)mm recombination lines scales almost linearly with frequency (cite: Peters12).

</paper>

Write the methods card for this paper.