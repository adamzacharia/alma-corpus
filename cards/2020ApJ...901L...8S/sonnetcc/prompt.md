# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...901L...8S\sonnetcc\reply.txt

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
 "bibcode": "2020ApJ...901L...8S",
 "title": "Molecular Gas Properties on Cloud Scales across the Local Star-forming Galaxy Population",
 "year": 2020,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Sun, Jiayi",
 "n_authors": 37,
 "arxiv_id": "2009.01842",
 "doi": "10.3847/2041-8213/abb3be",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2017.1.00392.S",
  "2017.1.00886.L",
  "2018.1.01321.S",
  "2018.1.01651.S"
 ]
}
```

Paper text:
<paper>
# Molecular Gas Properties on Cloud Scales Across the Local Star-forming Galaxy Population

## Abstract

Using the PHANGS-ALMA CO$\,(2\text{--}1)$ survey, we characterize molecular gas properties on ${\sim}100$ pc scales across $102\,778$ independent sightlines in 70 nearby galaxies. This yields the best synthetic view of molecular gas properties on cloud scales across the local star-forming galaxy population obtained to date. Consistent with previous studies, we observe a wide range of molecular gas surface densities (3.4 dex), velocity dispersions (1.7 dex), and turbulent pressures (6.5 dex) across the galaxies in our sample. Under simplifying assumptions about sub-resolution gas structure, the inferred virial parameters suggest that the kinetic energy of the molecular gas typically exceeds its self-gravitational binding energy at ${\sim}100$ pc scales by a modest factor (1.3 on average). We find that the cloud-scale surface density, velocity dispersion, and turbulent pressure (1) increase towards the inner parts of galaxies, (2) are exceptionally high in the centers of barred galaxies (where the gas also appears less gravitationally bound), and (3) are moderately higher in spiral arms than in inter-arm regions. The galaxy-wide averages of these gas properties also correlate with the integrated stellar mass, star formation rate, and offset from the star-forming main sequence of the host galaxies. These correlations persist even when we exclude regions with extraordinary gas properties in galaxy centers, which contribute significantly to the inter-galaxy variations. Our results provide key empirical constraints on the physical link between molecular cloud populations and their galactic environment.\
 \

# Introduction

Observations indicate that the physical properties of giant molecular clouds (GMCs) vary systematically with their location in a galaxy. This result is obtained in the Milky Way (cite: Rice_etal_2016; Roman-Duval_etal_2016; Miville-Deschenes_etal_2017; Colombo_etal_2019) and in other galaxies (cite: DonovanMeyer_etal_2013; Hughes_etal_2013a; Colombo_etal_2014a; Leroy_etal_2016; Schruba_etal_2019). This suggests that GMCs are connected to their galactic context, which affects their formation, structure, or evolution (cite: Field_etal_2011; Hughes_etal_2013a; Jeffreson_Kruijssen_2018; Meidt_etal_2018; Meidt_etal_2020; Schruba_etal_2019; Sun_etal_2020).

Understanding this cloud–environment connection has been a challenge because it requires comprehensive, observationally expensive mapping of GMC demographics across the local galaxy population. This challenge is being addressed by PHANGS-ALMA[^1], a large $\mathrm{CO}\,(2\text{--}1)$ line survey covering essentially all ALMA-visible, nearby, massive, star-forming galaxies (A. K. Leroy et al. 2020a, in preparation). PHANGS-ALMA well samples the local star-forming main sequence across two decades in stellar mass ($10^9{-}10^{11}\,\mbox{$\rm M_{\odot}$}$). The high resolution and sensitivity of the PHANGS-ALMA data offer an unprecedented opportunity to characterize molecular gas properties on $50{-}150$ pc “cloud scales”, and the cloud–environment connection across typical star-forming environments in the local universe.

In this Letter, we report measurements of the cloud-scale molecular gas surface density and velocity dispersion, as well as estimates of the turbulent pressure and the virial parameter. Following our analysis of the PHANGS-ALMA pilot sample of $11$ galaxies (cite: Sun_etal_2018), we derive these measurements on fixed $90$ pc and $150$ pc scales using the full PHANGS-ALMA survey, which increases our sample size to 70 galaxies. The derived measurements constitute a benchmark data set that can be readily compared with observations of other types of galaxies or numerical simulations reaching similar spatial resolutions (cite: Semenov_etal_2018; Dobbs_etal_2019; Fujimoto_etal_2019; Jeffreson_etal_2020).

# Data and Measurements

*Overview:* We carry out a pixel-by-pixel analysis of molecular gas properties at fixed $90$ pc and $150$ pc scales. This method provides a simple, reproducible characterization of all detected emission (cite: Sawada_etal_2012; Hughes_etal_2013b; Leroy_etal_2016). Complementary analyses decomposing the same CO data into individual objects (E. Rosolowsky et al. 2020, in preparation; A. Hughes et al., in preparation) yield qualitatively similar conclusions.

*Galaxy sample:* We include the 70 PHANGS-ALMA galaxies that had fully-processed ALMA data by December 2019[^2]. They consist of $67$ out of the $74$ galaxies in the ALMA Large Program and pilot samples and three nearby galaxies from the extended PHANGS-ALMA sample. Table [2](#tab:sample) lists the galaxy sample together with their global properties (columns 1–9).

*Data characteristics:* The PHANGS-ALMA $\mathrm{CO}\,(2\text{--}1)$ data have native spatial resolutions of $50{-}150$ pc at the distances of the target galaxies, and $1\sigma$ noise levels of $0.2{-}0.3$ K per $2.5$ $\rm km\,s^{-1}$ channel. They combine ALMA interferometric array and single dish observations to recover emission across the full range of spatial scales (see A. K. Leroy et al. 2020b, in preparation).

*Data homogenization:* We convolve the data cubes to a common $150$ pc spatial resolution to allow direct comparison between all 70 galaxies. For a subset of 35 galaxies, we are also able to convolve the cubes to $90$ pc resolution to investigate trends with spatial resolution .

*Product creation:* We mask the data cubes to only include voxels that contain emission detected with high confidence[^3]. We integrate the masked cubes along the spectral axis to produce the integrated intensity ($I_\mathrm{CO}$) and effective line width ($\sigma_\mathrm{CO}$) maps. The latter quantity is derived as $\sigma_\mathrm{CO}= I_\mathrm{CO}/ (\sqrt{2\pi}\, T_\mathrm{peak})$ following (cite: Heyer_etal_2001)[^4], where $T_\mathrm{peak}$ is the brightness temperature at the line peak, and is subsequently corrected for the instrumental line broadening following (see equation 5 therein). We produce associated uncertainty maps via error propagation from the estimated noise in the cube. This product creation scheme closely follows and is detailed in A. K. Leroy et al. (2020b, in preparation).

Our masking scheme guarantees high S/N ratio CO line measurements at the expense of excluding faint CO emission, especially from sightlines with low $I_\mathrm{CO}$ and high $\sigma_\mathrm{CO}$. The resultant data censoring function is shown in Figure [1](#fig:overview) (see formula in Appendix [7](#apdx:censoring)). We report in Table [2](#tab:sample) (column 12) the CO flux completeness for each galaxy (the flux within the mask divided by the total flux in the data cube, or $f_\mathrm{CO}$).

*Resampling:* We resample the two-dimensional maps of $I_\mathrm{CO}$, $\sigma_\mathrm{CO}$, and their uncertainties with hexagonal pixels matching the beam size. This ensures that the resampled measurements are nearly mutually independent. We list the number of independent measurements (sightlines) in each galaxy in Table [2](#tab:sample) (column 13).

*Conversion to physical quantities:* We use $\sigma_\mathrm{CO}$ as a tracer of the molecular gas velocity dispersion, $\sigma_\mathrm{mol}$. We derive molecular gas surface density, $\Sigma_\mathrm{mol}$, via $$\begin{equation}
    \Sigma_\mathrm{mol}= \alpha_\mathrm{CO}\;R_{21}^{-1}\;I_\mathrm{CO}~. \label{eq:Sigmol}
\end{equation}$$ Here $R_{21}=0.65$ is the adopted $\mathrm{CO}\,(2\text{--}1)$-to-$\mathrm{CO}\,(1\text{--}0)$ line ratio (cite: Leroy_etal_2013b; denBrok_etal_2020b) and $\alpha_\mathrm{CO}$ is the CO-to-H$_2$ conversion factor. We adopt a metallicity-dependent $\alpha_\mathrm{CO}$ (cite: Accurso_etal_2017): $$\begin{equation}
    \alpha_\mathrm{CO}= 4.35\,Z'^{-1.6}\;\mbox{$\rm M_{\odot}\,pc^{-2}$}\,(\mbox{$\rm K\,km\,s^{-1}$})^{-1}~,
    \label{eq:alphaCO}
\end{equation}$$ where $Z'$ refers to the local metallicity in units of the solar value. Following (cite: Sun_etal_2020), we estimate $Z'$ based on galaxy global stellar mass and effective radius (see Table [2](#tab:sample) for values and data sources), assuming a galaxy global mass–metallicity relation (cite: Sanchez_etal_2019) and a fixed radial metallicity gradient within a galaxy (cite: Sanchez_etal_2014).

We use $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$ to estimate the mean turbulent pressure in the molecular gas, $P_\mathrm{turb}\approx\rho_\mathrm{mol}\,\sigma_\mathrm{mol}^2$, and the virial parameter, $\alpha_\mathrm{vir}$, via $$\begin{align}
    P_\mathrm{turb}=\;& 3.3\times10^4\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}\;\times \nonumber\\
    &\left(\frac{\Sigma_\mathrm{mol}}{10^2\;\mbox{$\rm M_{\odot}\,pc^{-2}$}}\right) \left(\frac{\sigma_\mathrm{mol}}{10\;\mbox{$\rm km\,s^{-1}$}}\right)^2 \left(\frac{D_\mathrm{beam}}{150\;\mathrm{pc}}\right)^{-1}~, \label{eq:P_turb}\\
    \alpha_\mathrm{vir}=\;& 3.1\;\times \nonumber\\
    &\left(\frac{\Sigma_\mathrm{mol}}{10^2\;\mbox{$\rm M_{\odot}\,pc^{-2}$}}\right)^{-1} \left(\frac{\sigma_\mathrm{mol}}{10\;\mbox{$\rm km\,s^{-1}$}}\right)^2 \left(\frac{D_\mathrm{beam}}{150\;\mathrm{pc}}\right)^{-1}~. \label{eq:alpha_vir}
\end{align}$$ Here $D_\mathrm{beam}$ denotes the beam full-width-half-maximum and is assumed to be the depth along the line of sight[^5]. Both equations assume a single, spherical gas structure filling each beam . The second equation assumes in addition that the gas structures have a density profile of $\rho(r) \propto r^{-1}$ (cite: Rosolowsky_Leroy_2006).

# Results

We measure $\Sigma_\mathrm{mol}$, $\sigma_\mathrm{mol}$, $P_\mathrm{turb}$, and $\alpha_\mathrm{vir}$ on cloud scales in a homogeneous way across our sample. This yields 102 778 independent measurements at $150$ pc resolution in 70 galaxies, and 79 840 measurements at $90$ pc resolution in 35 galaxies. These measurements are published in Table [3](#tab:product) in a machine-readable form. We focus on the $150$ pc scale measurements, which are available for all 70 galaxies, while occasionally referencing to the $90$ pc scale measurements to illustrate resolution dependencies.

In the following data analysis and presentation, we omit measurements from four galaxies (NGC 4207, NGC 4424, NGC 4694, and NGC 4826). These galaxies have edge-on orientation (NGC 4207) and/or peculiar gas kinematics due to ram-pressure stripping (NGC 4424), a strong nuclear outflow (NGC 4694), or represent a recent merger event (NGC 4826). We still report results for these galaxies in the tables, but below we focus on the remaining 102 295 sightlines in 66 galaxies for data presentation.

## Statistics of Cloud-scale Molecular Gas Properties

Figure [1](#fig:overview) shows the distributions of $I_\mathrm{CO}$, $\Sigma_\mathrm{mol}$, and $\sigma_\mathrm{mol}$, measured at $150$ pc resolution. This figure encapsulates molecular gas properties on cloud scales across a wide range of star-forming environments at $z \approx 0$. Table [1](#tab:stats) provides area-weighted statistics treating each sightline equally, and $\Sigma_\mathrm{mol}$-weighted statistics treating each quantum of molecular gas mass equally.

We observe median $I_\mathrm{CO}$, $\Sigma_\mathrm{mol}$, and $\sigma_\mathrm{mol}$ values similar to the results of previous studies (cite: Bolatto_etal_2008; Colombo_etal_2019), but with a large spread. Across the full sample at $150$ pc resolution, we find mass-weighted median $\Sigma_\mathrm{mol}=110\;\mbox{$\rm M_{\odot}\,pc^{-2}$}$ and mass-weighted median $\sigma_\mathrm{mol}=9.1\;\mbox{$\rm km\,s^{-1}$}$ (see Table [1](#tab:stats)). Given the broad sample selection and coverage, these can be taken as typical values across the local star-forming galaxy population. We also see that the $\pm3\sigma$ (i.e., $99.7$%) range of the mass-weighted $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$ distributions is large, $3.4$ and $1.7$ dex respectively. Given that data censoring hinders the detection of low $I_\mathrm{CO}$ signals (to the left of the brown curves in Figure [1](#fig:overview)), the true ranges of $I_\mathrm{CO}$ and $\Sigma_\mathrm{mol}$ are likely even wider.

We find a strong and statistically significant[^6] correlation between $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$ (Spearman’s rank correlation coefficient $\rho=0.77$). This correlation results in even stronger variations in $P_\mathrm{turb}\approx\rho_\mathrm{mol}\,\sigma_\mathrm{mol}^2$ than those in $\Sigma_\mathrm{mol}$ or $\sigma_\mathrm{mol}$ alone. Indeed, $P_\mathrm{turb}$ varies by $\gtrsim6$ dex at $\pm3\sigma$ across our sample (Figure [1](#fig:overview) and Table [1](#tab:stats)).

We further compare the observed $\Sigma_\mathrm{mol}{-}\sigma_\mathrm{mol}$ distribution to the expected relations for beam-filling, spherical clouds with fixed virial parameters $\alpha_\mathrm{vir}$ (black diagonal lines in Figure [1](#fig:overview); see Equation [\[eq:alpha_vir\]](#eq:alpha_vir)). These relations capture the overall trend in the data, with the $\alpha_\mathrm{vir}=1$ line lying near their lower envelope. Across our full sample, $\alpha_\mathrm{vir}$ has a mass-weighted median value of $2.7$ and a $1\sigma$ scatter of $0.7$ dex (Table [1](#tab:stats)). This means that the kinetic energy in the molecular gas on average slightly exceeds its gravitational binding energy by a factor of $1.3$ on $150$ pc scales. This is consistent with the conclusion in (cite: Sun_etal_2020) that the observed molecular gas velocity dispersion at ${\sim}100$ pc scales mainly reflects gas motions due to self-gravity and, to a lesser degree, to external gravity and ambient pressure.

The calculation of $P_\mathrm{turb}$ and $\alpha_\mathrm{vir}$ assumes an idealized sub-beam gas distribution (see Section [2](#sec:method)). In reality, the molecular gas remains clumpy on $\lesssim100$ pc spatial scales (cite: Leroy_etal_2013a), and the small-scale density distribution may vary from place to place. These variations in sub-beam density distribution may introduce systematic uncertainties in our inferred $P_\mathrm{turb}$ and $\alpha_\mathrm{vir}$ values. Nevertheless, our $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$ measurements should still capture the true distribution of molecular gas properties at the fixed $150$ pc spatial scale.

To further illustrate the effect of resolution on our analysis, we compare our measurements at $150$ pc scales with those at $90$ pc scales for the 32 galaxies that have data at both resolutions (see Table [1](#tab:stats) for the statistics at $90$ pc). This includes 79 156 independent sightlines at $90$ pc scales or 40 641 sightlines at $150$ pc scales. We find the mass-weighted medians of $I_\mathrm{CO}$, $\Sigma_\mathrm{mol}$, and $P_\mathrm{turb}$ at $90$ pc scales to be moderately higher than the $150$ pc scale values by factors of $1.5$, $1.5$, and $2.0$, respectively. However, we see little difference in the median values of $\sigma_\mathrm{mol}$ and $\alpha_\mathrm{vir}$ at the two resolutions, and the observed dynamic ranges of all quantities is essentially the same at both spatial scales. This suggests that the gas is moderately clumped below our resolution, but that our qualitative conclusions are not sensitive to resolution-related biases and robustly reflect typical molecular gas properties at ${\sim}100$ pc scales.

## Correlation with Galactocentric Radius

The variations in $I_\mathrm{CO}$, $\Sigma_\mathrm{mol}$, and $\sigma_\mathrm{mol}$ correlate with location in the host galaxy. To illustrate this, we color-code all data points in Figure [1](#fig:overview) by their galactocentric radii ($r_\mathrm{gal}$), normalized to the effective radii of their host galaxies ($R_\mathrm{eff}$; see Table [2](#tab:sample) for values and data sources). Both $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$ tend to increase towards smaller $r_\mathrm{gal}/R_\mathrm{eff}$. Additionally, the gas in the inner regions ($r_\mathrm{gal}/R_\mathrm{eff}<0.5$) frequently shows enhanced $\sigma_\mathrm{mol}$ at a given $\Sigma_\mathrm{mol}$.

These radial trends are partly driven by the structure of galaxy disks. Most star-forming galaxies show increasing gas and stellar mass surface densities towards their central regions. This leads to a similar radial trend on the mean pressure in the interstellar medium (ISM) required to keep it in vertical dynamical equilibrium (cite: Elmegreen_1989; Blitz_Rosolowsky_2004; Ostriker_etal_2010). We expect the same trend to hold for the turbulent pressure in the molecular gas, $P_\mathrm{turb}$, which correlates with the mean ISM pressure (cite: Sun_etal_2020). This expectation matches well with the trend of decreasing $r_\mathrm{gal}/R_\mathrm{eff}$ with increasing $P_\mathrm{turb}$ values in Figure [1](#fig:overview).

The expectation from ISM dynamical equilibrium does not by itself explain all the trends in Figure [1](#fig:overview)—for fixed $\Sigma_\mathrm{mol}$, we also find excess $\sigma_\mathrm{mol}$ at smaller $r_\mathrm{gal}/R_\mathrm{eff}$. At face value, this suggests that molecular gas in the inner galaxy tends to be more weakly bound (higher $\alpha_\mathrm{vir}$) than the gas in the outer galaxy. Such a trend is expected from the larger contribution of the external (mostly stellar) potential to the dynamical equilibrium at smaller radii (cite: Meidt_etal_2018; Gensior_etal_2020). However, the observed trend could instead suggest that the gas is more clumpy in the inner parts of galaxies, or that our prescription over-predicts $\alpha_\mathrm{CO}$ in the outer disks of galaxies.

The trend with galactocentric radius at fixed $\Sigma_\mathrm{mol}$ may also reflect biases in the line width measurement. Using the CO rotation curves from (cite: Lang_etal_2020), we verified that unresolved rotation often represents a minor contribution to our measured line width at $90{-}150$ pc scales in the inner parts of galaxies. However, unresolved non-circular motions may still play an important role (cite: Colombo_etal_2014b; Meidt_etal_2018; Meidt_etal_2020; Henshaw_etal_2020).

## Correlation with Galaxy Bars and Spiral Arms

We investigate whether galaxy morphological features, i.e., stellar bars and spiral arms, have an impact on the molecular gas properties on cloud scales. We classify each target galaxy as barred or unbarred (see Table [2](#tab:sample)), and divide the PHANGS-ALMA CO footprint into a central region and a disk region based on near infrared images. The central regions often correspond to distinct structures (e.g., nuclear rings) showing extra light at near infrared wavelengths. For galaxies with strong spiral arms, we further identify arm regions and the corresponding inter-arm regions covering the same $r_\mathrm{gal}$ range. The methodology closely follows (cite: Salo_etal_2015) and (cite: Herrera-Endoqui_etal_2015) and is detailed in M. Querejeta et al. (2020, in preparation).

The left panel of Figure [2](#fig:regions) compares molecular gas properties in the central regions and the disk regions of our galaxies. Motivated by previous studies (cite: Sakamoto_etal_1999; Jogee_etal_2005), we indicate the centers of 43 galaxies classified as barred and 13 galaxies classified as unbarred separately[^7]. The centers of barred galaxies show ${\sim}20$ times higher mass-weighted median $\Sigma_\mathrm{mol}$ and ${\sim}5$ times higher mass-weighted median $\sigma_\mathrm{mol}$ compared to the disk regions (Table [1](#tab:stats)). These central regions of barred galaxies mostly host molecular gas with $\Sigma_\mathrm{mol}\gtrsim100\;\mbox{$\rm M_{\odot}\,pc^{-2}$}$ and $\sigma_\mathrm{mol}\gtrsim10\;\mbox{$\rm km\,s^{-1}$}$ A small fraction of the gas in the centers of unbarred galaxies also shows high $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$, but the majority resembles the gas in the disk regions. This sharp contrast between barred and unbarred galaxies indicates that the high $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$ frequently found in star-forming galaxy centers is linked to the presence of stellar bars.

Our measurements in galaxy centers can be affected by uncertainty related to $\alpha_\mathrm{CO}$ and $R_\mathrm{21}$. (cite: Sandstrom_etal_2013) and (cite: denBrok_etal_2020b) find evidence for low $\alpha_\mathrm{CO}$ and high $R_\mathrm{21}$ in star-forming galaxy centers. If our prescription also accounted for these effects, the $\Sigma_\mathrm{mol}$ enhancement would be reduced in galaxy centers, but the excess in $\sigma_\mathrm{mol}$ at a given $\Sigma_\mathrm{mol}$ would be even more extreme relative to disks.

The observed extreme gas properties in barred galaxy centers are consistent with existing knowledge about the role of stellar bars in regulating ISM properties. Stellar bars can drive large-scale gas inflows, boosting the central gas reservoir and leading to high $\Sigma_\mathrm{mol}$ (cite: Pfenniger_Norman_1990; Sakamoto_etal_1999; Sheth_etal_2002; Jogee_etal_2005; Tress_etal_2020a). Meanwhile, the released gravitational energy from gas inflow as well as the stronger local stellar and AGN feedback together enhance the local turbulence (cite: Kruijssen_etal_2014; Armillotta_etal_2019; Sormani_etal_2019). Complex gas streaming motions that are unresolved in our data could also bias $\sigma_\mathrm{mol}$ higher than the turbulent velocity dispersion (cite: Henshaw_etal_2016).

The right panel in Figure [2](#fig:regions) compares the distribution of $\Sigma_\mathrm{mol}$ at fixed $r_\mathrm{gal}/R_\mathrm{eff}$ in spiral arm regions and inter-arm regions for 28 galaxies with identifiable spiral structures in their stellar distribution. Molecular gas in the arm regions shows typically $1.5{-}2$ times higher $\Sigma_\mathrm{mol}$ relative to the gas in the inter-arm regions at fixed $r_\mathrm{gal}/R_\mathrm{eff}$.

We further find (not shown in Figure [2](#fig:regions)) that the gas in spiral arms shows ${\sim}20\%$ higher $\sigma_\mathrm{mol}$, ${\sim}2{-}3$ times higher $P_\mathrm{turb}$, and ${\sim}15$% lower $\alpha_\mathrm{vir}$ at fixed $r_\mathrm{gal}/R_\mathrm{eff}$. Consistent with previous studies examining individual galaxies (cite: Hughes_etal_2013b; Colombo_etal_2014a; Hirota_etal_2018), these results support the idea that spiral arms harbor more high surface density, turbulent, bound molecular clouds.

Though statistically significant, the measured contrast in $\Sigma_\mathrm{mol}$ between arms and inter-arm gas may seem lower than what one would expect from visual inspection of the PHANGS-ALMA CO maps (e.g., figure 12 in ). There the spiral arms typically appear replete with bright emission, while the inter-arm regions show only sporadic, faint signal with a large portion of the area lacking significant CO detection. We note that our quantitative analysis focuses solely on the gas securely detected in CO without accounting for the area covering fraction of the CO detection. Had we included map pixels with non- or low-significance detections in our analysis, measurements in the inter-arm regions would be more severely diluted than measurements in the arm regions, and the arm versus inter-arm contrast would be considerably larger than the factor of $1.5{-}2$ measured above (also see M. Querejeta et al. 2020, in preparation).

To summarize, our measurements based on significant detections of CO emission reveal moderate differences between the molecular gas properties in spiral arm versus inter-arm regions. In addition to this, the spatial density of secure CO detections is much lower in the inter-arm regions than in the spiral arms of galaxies. Together, these two observations suggest that spiral arms not only accumulate molecular gas but also lightly modify the properties of the gas (cite: Dobbs_Bonnell_2008; Tress_etal_2020).

## Correlation with Integrated Galaxy Properties

We find that molecular gas properties on cloud scales correlate with integrated properties of the host galaxies. In Figure [3](#fig:MS), the top left panel shows the mass-weighted median $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$ values on $150$ pc scale within each galaxy, with each point colored by the galaxy global star formation rate (SFR). The top right panel shows how the galaxy-wide, mass-weighted median $\Sigma_\mathrm{mol}$ varies among galaxies across the galaxy global $M_\star{-}\text{SFR}$ space.

Across our sample, the mass-weighted median $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$ vary by $2$ dex and $1$ dex from galaxy to galaxy, respectively. These cloud scale gas properties also show statistically significant correlations with host galaxy global $M_\star$ (Spearman’s $\rho=0.64$ and $0.53$), global SFR ($\rho=0.72$ and $0.58$), and offset in SFR from the local star-forming main sequence ($\Delta\text{MS}$; $\rho=0.45$ and $0.35$). We also find positive correlations between the mass-weighted median $P_\mathrm{turb}$ and the same galaxy global properties (not shown in Figure [3](#fig:MS)). The mass-weighted median of $\alpha_\mathrm{vir}$, however, shows an anti-correlation with the galaxy’s SFR ($\rho=-0.44$) and $\Delta\text{MS}$ ($\rho=-0.41$). Figure [3](#fig:MS) only shows the $150$ pc results, but we see similar trends using data at $90$ pc resolution.

The pronounced galaxy-to-galaxy variations in these mass-weighted median quantities is partly explained by galaxies in our sample that host a distinct central concentration of CO-bright molecular gas. This is especially true of barred galaxies, where the central regions host a substantial fraction of the galaxy’s molecular gas mass. In these galaxies, the exceptional gas properties in the central region bias the galaxy-wide mass-weighted median measurements toward high $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$. In light of this bias, we also calculate and compare the mass-weighted median properties for all the CO emission *outside* the central region in each galaxy. As shown in the bottom panels in Figure [3](#fig:MS), excluding the central regions reduces the level of galaxy-to-galaxy variations in the mass-weighted median $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$. Nevertheless, the overall trends persist, and the rank correlation remain significant.

Across the local star-forming galaxy population, we thus conclude that the molecular gas in more massive and actively star-forming galaxies is systematically denser (as traced by $\Sigma_\mathrm{mol}$), more turbulent (as tracked by $\sigma_\mathrm{mol}$ and $P_\mathrm{turb}$), and more strongly self-gravitating (as expressed by $\alpha_\mathrm{vir}$) on ${\sim}100$ pc scales. We speculate that these trends arise because galaxy global properties correlate with the structural properties on a more *local* scale (e.g., local stellar mass distribution, galaxy dynamical features). In turn, molecular gas properties on cloud scales are linked to these local structural properties (cite: Hughes_etal_2013a; Meidt_etal_2018; Meidt_etal_2020; Schruba_etal_2019; Chevance_etal_2020a; Sun_etal_2020). We plan to investigate this topic in more detail in a future round of PHANGS-ALMA analysis.

# Summary

Using the full PHANGS-ALMA $\mathrm{CO}\,(2\text{--}1)$ data set, we measure molecular gas surface density, velocity dispersion, turbulent pressure, and virial parameter on cloud scales in 70 nearby, massive, star-forming galaxies. We publish the resultant 102 778 independent measurements at $150$ pc scales and 79 840 measurements at $90$ pc scales in Table [3](#tab:product) and summarize their statistics in Table [1](#tab:stats) and Section [3.1](#sec:result:stats).

Consistent with observations in the PHANGS-ALMA pilot sample and other galaxies (cite: Hughes_etal_2013b; Egusa_etal_2018), we find that molecular gas properties on ${\sim}100$ pc scales vary substantially and correlate with location in the host galaxy. Specifically, our key results are:

1.  Molecular gas surface density, velocity dispersion, and turbulent pressure vary dramatically (by $3.4$, $1.7$, and $6.5$ dex, respectively) across our full sample. The correlation between surface density and velocity dispersion suggests that the gas motions on ${\sim}100$ pc scales are mainly responding to gas self-gravity, though they do also react to external gravity and/or ambient pressure in some regions. The inferred virial parameter has a median value of $2.7$ and a $1\sigma$ range of $0.7$ dex (Figure [1](#fig:overview) and Section [3.1](#sec:result:stats)).

2.  The cloud scale gas surface density, velocity dispersion, and turbulent pressure all increase toward small galactocentric radii, consistent with expectations from vertical dynamical equilibrium and the structure of galaxy disks (Figure [1](#fig:overview) and Section [3.2](#sec:result:rgal)).

3.  The centers of barred galaxies display exceptionally high molecular gas surface densities and velocity dispersions. The high surface densities are likely fueled by gas inflows induced by the stellar bars. The observed excess velocity dispersion at fixed surface density in these regions suggests less bound gas or enhanced bulk flow motions (Figure [2](#fig:regions) and Section [3.3](#sec:result:regions)).

4.  Molecular gas in spiral arm regions shows moderately higher surface densities and appears more turbulent and more bound than the molecular gas detected in the inter-arm regions. This suggests that spiral arms accumulate molecular gas and further mildly alter the gas properties (Figure [2](#fig:regions) and Section [3.3](#sec:result:regions)).

5.  The properties of molecular gas at cloud scale resolution correlate with the properties of the host galaxy. Galaxies with higher stellar mass and more active star formation tend to host molecular gas with higher surface density, higher velocity dispersion, and lower virial parameter (Figure [2](#fig:regions) and Section [3.4](#sec:result:global)).

These observations provide a first comprehensive view of the the properties of molecular gas at cloud scales across the local star-forming galaxy population. They provide strong evidence that molecular cloud properties are closely coupled to the galactic environment, likely through dynamical processes and stellar feedback. The empirical relations presented in this work establish the groundwork for unveiling the physics that underpins the molecular cloud–environment connection.

+-------------------------------+----------------------------------------+--------------------------------------------------------------------------+--------------------------------------------------------------------------+
| Quantity                      | Unit                                   | Area-weighted                                                            | Mass-weighted                                                            |
+:==============================+:======================================:+:====================:+:=======================:+:=======================:+:====================:+:=======================:+:=======================:+
| 3-5 (lr)6-8                   |                                        | Median               | $1\sigma$ Range (68.3%) | $3\sigma$ Range (99.7%) | Median               | $1\sigma$ Range (68.3%) | $3\sigma$ Range (99.7%) |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| Full sample at 150 pc scales (102 295 sightlines across 66 galaxies; see Section [3.1](#sec:result:stats))                                                                                                                   |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $I_\mathrm{CO,\,150pc}$       | $\mbox{$\rm K\,km\,s^{-1}$}$           | $3.4\times10^0$      | 0.9 dex                 | 3.2 dex                 | $1.9\times10^1$      | 1.6 dex                 | 3.6 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\Sigma_\mathrm{mol,\,150pc}$ | $\mbox{$\rm M_{\odot}\,pc^{-2}$}$      | $2.2\times10^1$      | 0.9 dex                 | 2.9 dex                 | $1.1\times10^2$      | 1.5 dex                 | 3.4 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\sigma_\mathrm{mol,\,150pc}$ | $\mbox{$\rm km\,s^{-1}$}$              | $5.0\times10^0$      | 0.4 dex                 | 1.7 dex                 | $9.1\times10^0$      | 0.8 dex                 | 1.7 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $P_\mathrm{turb,\,150pc}$     | $\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ | $1.8\times10^4$      | 1.6 dex                 | 6.1 dex                 | $3.0\times10^5$      | 3.0 dex                 | 6.5 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\alpha_\mathrm{vir,\,150pc}$ | –                                      | 3.5                  | 0.6 dex                 | 1.9 dex                 | 2.7                  | 0.7 dex                 | 2.0 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| Gas in galaxy disks at 150 pc scales (99 765 sightlines across 66 galaxies; see Section [3.3](#sec:result:regions) and [3.4](#sec:result:global))                                                                            |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $I_\mathrm{CO,\,150pc}$       | $\mbox{$\rm K\,km\,s^{-1}$}$           | $3.3\times10^0$      | 0.9 dex                 | 2.7 dex                 | $1.2\times10^1$      | 1.1 dex                 | 3.0 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\Sigma_\mathrm{mol,\,150pc}$ | $\mbox{$\rm M_{\odot}\,pc^{-2}$}$      | $2.1\times10^1$      | 0.9 dex                 | 2.5 dex                 | $7.1\times10^1$      | 1.0 dex                 | 2.8 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\sigma_\mathrm{mol,\,150pc}$ | $\mbox{$\rm km\,s^{-1}$}$              | $4.9\times10^0$      | 0.4 dex                 | 1.6 dex                 | $7.5\times10^0$      | 0.5 dex                 | 1.6 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $P_\mathrm{turb,\,150pc}$     | $\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ | $1.7\times10^4$      | 1.6 dex                 | 5.4 dex                 | $1.3\times10^5$      | 1.9 dex                 | 5.6 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\alpha_\mathrm{vir,\,150pc}$ | –                                      | 3.4                  | 0.6 dex                 | 1.9 dex                 | 2.7                  | 0.7 dex                 | 2.0 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| Gas in the centers of barred galaxies at 150 pc scales (1 715 sightlines across 43 galaxies; see Section [3.3](#sec:result:regions))                                                                                         |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $I_\mathrm{CO,\,150pc}$       | $\mbox{$\rm K\,km\,s^{-1}$}$           | $6.5\times10^1$      | 1.3 dex                 | 3.4 dex                 | $3.0\times10^2$      | 0.9 dex                 | 2.6 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\Sigma_\mathrm{mol,\,150pc}$ | $\mbox{$\rm M_{\odot}\,pc^{-2}$}$      | $2.8\times10^2$      | 1.3 dex                 | 3.4 dex                 | $1.3\times10^3$      | 0.9 dex                 | 2.6 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\sigma_\mathrm{mol,\,150pc}$ | $\mbox{$\rm km\,s^{-1}$}$              | $2.3\times10^1$      | 0.5 dex                 | 1.7 dex                 | $3.4\times10^1$      | 0.4 dex                 | 1.2 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $P_\mathrm{turb,\,150pc}$     | $\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ | $5.1\times10^6$      | 2.1 dex                 | 6.5 dex                 | $5.0\times10^7$      | 1.3 dex                 | 4.3 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\alpha_\mathrm{vir,\,150pc}$ | –                                      | 6.0                  | 0.8 dex                 | 2.1 dex                 | 2.7                  | 0.7 dex                 | 2.1 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| Full sample at 90 pc scales (79 156 sightlines across 32 galaxies; see Section [3.1](#sec:result:stats))                                                                                                                     |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $I_\mathrm{CO,\,90pc}$        | $\mbox{$\rm K\,km\,s^{-1}$}$           | $4.2\times10^0$      | 0.9 dex                 | 2.9 dex                 | $1.5\times10^1$      | 1.2 dex                 | 3.3 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\Sigma_\mathrm{mol,\,90pc}$  | $\mbox{$\rm M_{\odot}\,pc^{-2}$}$      | $2.6\times10^1$      | 0.8 dex                 | 2.6 dex                 | $8.7\times10^1$      | 1.1 dex                 | 3.1 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\sigma_\mathrm{mol,\,90pc}$  | $\mbox{$\rm km\,s^{-1}$}$              | $4.5\times10^0$      | 0.4 dex                 | 1.6 dex                 | $7.0\times10^0$      | 0.6 dex                 | 1.7 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $P_\mathrm{turb,\,90pc}$      | $\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ | $2.9\times10^4$      | 1.5 dex                 | 5.5 dex                 | $2.3\times10^5$      | 2.2 dex                 | 6.3 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\alpha_\mathrm{vir,\,90pc}$  | –                                      | 3.8                  | 0.6 dex                 | 1.8 dex                 | 3.1                  | 0.6 dex                 | 1.8 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| Gas in galaxy disks at 90 pc scales (76 500 sightlines across 32 galaxies)                                                                                                                                                   |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $I_\mathrm{CO,\,90pc}$        | $\mbox{$\rm K\,km\,s^{-1}$}$           | $4.1\times10^0$      | 0.8 dex                 | 2.6 dex                 | $1.2\times10^1$      | 1.0 dex                 | 2.8 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\Sigma_\mathrm{mol,\,90pc}$  | $\mbox{$\rm M_{\odot}\,pc^{-2}$}$      | $2.6\times10^1$      | 0.8 dex                 | 2.4 dex                 | $7.1\times10^1$      | 1.0 dex                 | 2.6 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\sigma_\mathrm{mol,\,90pc}$  | $\mbox{$\rm km\,s^{-1}$}$              | $4.4\times10^0$      | 0.4 dex                 | 1.5 dex                 | $6.3\times10^0$      | 0.4 dex                 | 1.4 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $P_\mathrm{turb,\,90pc}$      | $\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ | $2.7\times10^4$      | 1.5 dex                 | 5.0 dex                 | $1.6\times10^5$      | 1.8 dex                 | 5.0 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+
| $\alpha_\mathrm{vir,\,90pc}$  | –                                      | 3.7                  | 0.6 dex                 | 1.8 dex                 | 2.9                  | 0.6 dex                 | 1.8 dex                 |
+-------------------------------+----------------------------------------+----------------------+-------------------------+-------------------------+----------------------+-------------------------+-------------------------+

: Statistics of Cloud Scale Molecular Gas Properties

Table notes: The area-weighted statistics are derived from percentiles weighted by sightline number counts, whereas the mass-weighted statistics from percentiles weighted by molecular gas mass (equivalent to $\Sigma_\mathrm{mol}$ in our measurement scheme).

This work was carried out as part of the PHANGS collaboration. The work of J.S., A.K.L., and D.U. is partially supported by the National Science Foundation (NSF) under Grants No. 1615105, 1615109, and 1653300, as well as by the National Aeronautics and Space Administration (NASA) under ADAP grants NNX16AF48G and NNX17AF39G. E.S., D.L., T.S., and T.G.W. acknowledge funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343). E.R. acknowledges the support of the Natural Sciences and Engineering Research Council of Canada (NSERC), funding reference number RGPIN-2017-03987. A.U. acknowledges support from the Spanish funding grants AYA2016-79006-P (MINECO/FEDER) and PGC2018-094671-B-I00 (MCIU/AEI/FEDER). J.M.D.K., M.C, and J.J.K. gratefully acknowledge funding from the DFG through an Emmy Noether Research Group (grant number KR4801/1-1) and the DFG Sachbeihilfe (grant number KR4801/2-1). J.M.D.K. gratefully acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme via the ERC Starting Grant MUSTANG (grant agreement No. 714907). F.B. acknowledges funding from the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 726384/EMPIRE). R.S.K. and S.C.O.G. acknowledge financial support from the German Research Foundation (DFG) via the collaborative research centre (SFB 881, Project-ID 138713538) ‘The Milky Way System’ (subprojects A1, B1, B2, and B8). They also acknowledge funding from the Heidelberg Cluster of Excellence STRUCTURES in the framework of Germany’s Excellence Strategy (grant EXC-2181/1 - 390900948) and from the European Research Council via the ERC Synergy Grant ECOGAL (grant 855130) and the ERC Advanced Grant STARLIGHT (grant 339177). K.K. gratefully acknowledges funding from the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) in the form of an Emmy Noether Research Group (grant number KR4598/2-1, PI Kreckel). A.E.S. is supported by an NSF Astronomy and Astrophysics Postdoctoral Fellowship under award AST-1903834.

This paper makes use of the following ALMA data:\
ADS/JAO.ALMA#2012.1.00650.S,\
ADS/JAO.ALMA#2013.1.01161.S,\
ADS/JAO.ALMA#2015.1.00925.S,\
ADS/JAO.ALMA#2015.1.00956.S,\
ADS/JAO.ALMA#2017.1.00392.S,\
ADS/JAO.ALMA#2017.1.00886.L,\
ADS/JAO.ALMA#2018.1.01321.S,\
ADS/JAO.ALMA#2018.1.01651.S.\
ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

We acknowledge the usage of the Extragalactic Distance Database[^8] (cite: Tully_etal_2009) and the SAO/NASA Astrophysics Data System[^9].

# Facilities

ALMA

# Software

`CASA` (cite: McMullin_etal_2007), `Astropy` (cite: AstropyCollaboration_etal_2018), `spectral-cube` (cite: spectral-cube-v0.4.5), `SpectralCubeTools` (<https://github.com/astrojysun/SpectralCubeTools>)

# Galaxy Sample

|  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|---:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Galaxy | Bar | Arm | $d$ | $i$ | $\theta_\mathrm{PA}$ | $M_\star$ | SFR | $R_\mathrm{eff}$ | $T_\mathrm{noise,\,150pc}$ | $r_\mathrm{ch,\,150pc}$ | $f_\mathrm{CO,\,150pc}$ | $N_\mathrm{los,\,150pc}$ |
|  |  |  | \[$\mathrm{Mpc}$\] | \[$\deg$\] | \[$\deg$\] | \[$10^9\,\mathrm{M_\odot}$\] | \[$\mathrm{M_\odot/yr}$\] | \[$\mathrm{kpc}$\] | \[$\mathrm{K}$\] |  |  |  |
| Circinus$^{$\dagger$}$ | ? | N | 4.21 | 64.3 | 36.7 | 18.2 | 3.85 | 2.5 | 0.048 | 0.072 | 83% | 456 |
| IC 1954 | Y | Y | 15.2 | 57.2 | 63.7 | 6.6 | 0.48 | 3.0 | 0.026 | 0.059 | 79% | 1054 |
| IC 5273 | Y | N | 14.7 | 48.5 | 235.2 | 5.5 | 0.56 | 2.3 | 0.022 | 0.055 | 64% | 750 |
| NGC 253$^{$\dagger$}$ | Y | N | 3.68 | 75.0 | 52.5 | 38.0 | 4.90 | 4.4 | 0.031 | 0.072 | 88% | 2203 |
| NGC 300$^{$\dagger$}$ | N | N | 2.08 | 39.8 | 11.4 | 1.7 | 0.14 | 2.2 | 0.011 | 0.123 | 41% | 127 |
| NGC 628 | N | Y | 9.77 | 8.7 | 20.8 | 18.3 | 1.67 | 4.6 | 0.031 | 0.061 | 83% | 3239 |
| NGC 685 | Y | N | 16.0 | 32.7 | 99.9 | 7.0 | 0.26 | 4.0 | 0.029 | 0.058 | 41% | 615 |
| NGC 1087 | Y | N | 14.4 | 40.5 | 357.4 | 6.6 | 1.05 | 3.0 | 0.040 | 0.055 | 75% | 1165 |
| NGC 1097 | Y | Y | 14.2 | 48.6 | 122.8 | 60.8 | 5.08 | 5.4 | 0.032 | 0.062 | 85% | 3093 |
| NGC 1300 | Y | Y | 26.1 | 31.8 | 276.9 | 71.9 | 2.06 | 9.1 | 0.096 | 0.054 | 48% | 1037 |
| NGC 1317 | Y | N | 19.0 | 24.5 | 221.5 | 36.6 | 0.40 | 4.4 | 0.032 | 0.063 | 105%$^{$\star$}$ | 575 |
| NGC 1365 | Y | Y | 18.1 | 55.4 | 202.4 | 66.8 | 14.34 | 11.8 | 0.067 | 0.191 | 88% | 2073 |
| NGC 1385 | ? | Y | 22.7 | 45.4 | 179.6 | 16.6 | 3.50 | 4.9 | 0.072 | 0.054 | 67% | 1796 |
| NGC 1433 | Y | N | 16.8 | 28.6 | 198.0 | 52.9 | 0.81 | 8.3 | 0.057 | 0.055 | 58% | 684 |
| NGC 1511 | ? | N | 15.6 | 73.5 | 296.9 | 7.6 | 2.27 | 2.8 | 0.038 | 0.063 | 89% | 778 |
| NGC 1512 | Y | Y | 16.8 | 42.5 | 263.8 | 38.3 | 0.91 | 7.2 | 0.052 | 0.057 | 61% | 689 |
| NGC 1546 | N | N | 18.0 | 70.1 | 147.8 | 22.8 | 0.80 | 3.2 | 0.030 | 0.057 | 97% | 972 |
| NGC 1559 | Y | N | 19.8 | 58.7 | 245.9 | 21.3 | 3.72 | 3.5 | 0.056 | 0.056 | 75% | 2218 |
| NGC 1566 | Y | Y | 18.0 | 30.5 | 216.5 | 53.3 | 4.49 | 8.4 | 0.057 | 0.058 | 97% | 3944 |
| NGC 1637 | Y | Y | 9.77 | 31.1 | 20.6 | 7.7 | 0.66 | 1.1 | 0.012 | 0.054 | 91% | 1360 |
| NGC 1672 | Y | Y | 11.9 | 43.8 | 135.9 | 17.7 | 2.73 | 5.1 | 0.052 | 0.064 | 82% | 1291 |
| NGC 1792 | N | N | 12.8 | 64.7 | 318.9 | 23.3 | 2.21 | 3.2 | 0.028 | 0.066 | 94% | 1468 |
| NGC 2090 | N | Y | 11.8 | 64.4 | 192.4 | 11.1 | 0.32 | 2.5 | 0.042 | 0.061 | 80% | 516 |
| NGC 2283 | Y | Y | 10.4 | 44.2 | 356.2 | 3.6 | 0.26 | 2.1 | 0.036 | 0.061 | 44% | 287 |
| NGC 2566 | Y | Y | 23.7 | 48.5 | 312.0 | 40.6 | 8.47 | 5.7 | 0.072 | 0.064 | 79% | 1978 |
| NGC 2835 | Y | Y | 10.1 | 41.1 | 0.2 | 5.9 | 0.76 | 2.8 | 0.056 | 0.060 | 28% | 182 |
| NGC 2903 | Y | N | 8.47 | 67.0 | 205.4 | 28.9 | 2.08 | 4.5 | 0.026 | 0.065 | 90% | 2390 |
| NGC 2997 | ? | Y | 11.3 | 31.9 | 109.3 | 31.2 | 2.79 | 5.0 | 0.026 | 0.063 | 86% | 5380 |
| NGC 3137 | ? | N | 14.9 | 70.1 | 358.9 | 5.8 | 0.41 | 4.6 | 0.033 | 0.056 | 70% | 488 |
| NGC 3351 | Y | N | 10.0 | 45.1 | 193.2 | 20.8 | 1.09 | 3.1 | 0.039 | 0.062 | 74% | 991 |
| NGC 3507 | Y | Y | 20.9 | 24.2 | 55.6 | 27.3 | 0.75 | 3.5 | 0.067 | 0.060 | 45% | 1090 |
| NGC 3511 | Y | N | 9.95 | 75.0 | 256.7 | 5.1 | 0.42 | 3.0 | 0.020 | 0.058 | 87% | 769 |
| NGC 3521 | N | N | 11.2 | 69.0 | 343.0 | 66.3 | 2.59 | 5.6 | 0.023 | 0.056 | 90% | 3770 |
| NGC 3596 | N | N | 10.1 | 21.6 | 78.1 | 3.5 | 0.23 | 1.7 | 0.052 | 0.060 | 72% | 495 |
| NGC 3621 | N | N | 6.56 | 65.4 | 343.8 | 9.2 | 0.79 | 2.9 | 0.013 | 0.063 | 91% | 1487 |
| NGC 3626 | Y | N | 20.0 | 46.6 | 165.2 | 27.5 | 0.23 | 3.3 | 0.084 | 0.057 | 57% | 150 |
| NGC 3627 | Y | Y | 10.57 | 56.5 | 174.0 | 53.1 | 3.24 | 5.2 | 0.033 | 0.061 | 89% | 2933 |
| NGC 4207$^{$\ddagger$}$ | ? | N | 16.8 | 62.5 | 120.5 | 5.1 | 0.22 | 1.3 | 0.062 | 0.067 | 91% | 147 |
| NGC 4254 | N | Y | 16.8 | 35.3 | 68.5 | 37.8 | 4.95 | 3.6 | 0.053 | 0.056 | 84% | 6438 |
| NGC 4293 | Y | N | 16.0 | 65.0 | 48.3 | 30.6 | 0.60 | 3.8 | 0.061 | 0.075 | 81% | 164 |
| NGC 4298 | N | N | 16.8 | 59.6 | 314.1 | 13.0 | 0.56 | 2.7 | 0.025 | 0.056 | 93% | 2328 |
| NGC 4303 | Y | Y | 17.6 | 20.0 | 310.6 | 50.4 | 5.63 | 6.2 | 0.066 | 0.061 | 82% | 3945 |
| NGC 4321 | Y | Y | 15.2 | 39.1 | 157.7 | 49.4 | 3.41 | 6.2 | 0.058 | 0.058 | 77% | 4923 |
| NGC 4424$^{$\ddagger$}$ | ? | N | 16.4 | 58.2 | 88.3 | 8.3 | 0.31 | 3.3 | 0.060 | 0.071 | 103%$^{$\star$}$ | 123 |
| NGC 4457 | Y | N | 15.6 | 17.4 | 78.7 | 25.7 | 0.34 | 3.1 | 0.041 | 0.060 | 93% | 645 |
| NGC 4496A | Y | N | 14.9 | 55.3 | 49.7 | 4.2 | 0.61 | 3.1 | 0.057 | 0.058 | 29% | 168 |
| NGC 4535 | Y | Y | 15.8 | 42.1 | 179.3 | 32.3 | 2.07 | 5.8 | 0.053 | 0.059 | 75% | 2433 |
| NGC 4536 | Y | Y | 15.2 | 64.8 | 307.4 | 20.0 | 2.99 | 4.2 | 0.025 | 0.059 | 88% | 2025 |
| NGC 4540 | Y | N | 16.8 | 38.3 | 14.3 | 6.8 | 0.19 | 1.8 | 0.059 | 0.063 | 65% | 428 |
| NGC 4548 | Y | Y | 16.2 | 38.3 | 138.0 | 45.6 | 0.53 | 5.1 | 0.035 | 0.060 | 49% | 1027 |
| NGC 4569 | Y | N | 16.8 | 70.0 | 18.0 | 67.2 | 1.54 | 8.9 | 0.038 | 0.058 | 85% | 2544 |
| NGC 4571 | N | N | 14.9 | 31.9 | 217.4 | 11.6 | 0.30 | 3.3 | 0.058 | 0.059 | 42% | 711 |
| NGC 4579 | Y | Y | 16.8 | 37.3 | 92.5 | 83.1 | 1.08 | 5.7 | 0.039 | 0.057 | 70% | 3078 |
| NGC 4689 | N | N | 16.8 | 39.0 | 164.3 | 17.0 | 0.52 | 4.2 | 0.060 | 0.058 | 72% | 1827 |
| NGC 4694$^{$\ddagger$}$ | N | N | 16.8 | 60.7 | 143.3 | 7.8 | 0.15 | 3.0 | 0.055 | 0.056 | 38% | 76 |
| NGC 4731 | Y | Y | 12.4 | 64.0 | 255.4 | 3.3 | 0.42 | 4.0 | 0.017 | 0.052 | 56% | 261 |
| NGC 4781 | Y | N | 15.3 | 56.4 | 288.1 | 8.0 | 0.84 | 2.4 | 0.022 | 0.055 | 79% | 1411 |
| NGC 4826$^{$\ddagger$}$ | N | N | 4.36 | 58.6 | 293.9 | 16.0 | 0.20 | 1.7 | 0.014 | 0.068 | 97% | 147 |
| NGC 4941 | ? | N | 14.0 | 53.1 | 202.6 | 12.4 | 0.36 | 3.4 | 0.020 | 0.054 | 80% | 1196 |
| NGC 4951 | N | N | 12.0 | 70.5 | 92.0 | 3.9 | 0.21 | 2.5 | 0.034 | 0.063 | 71% | 214 |
| NGC 5042 | ? | N | 12.6 | 51.4 | 190.1 | 4.7 | 0.33 | 2.9 | 0.035 | 0.056 | 35% | 300 |
| NGC 5068 | Y | N | 5.16 | 27.0 | 349.0 | 2.2 | 0.28 | 2.1 | 0.037 | 0.065 | 46% | 222 |
| NGC 5134 | Y | N | 18.5 | 22.7 | 311.6 | 21.6 | 0.37 | 4.2 | 0.047 | 0.059 | 59% | 538 |
| NGC 5248 | ? | Y | 12.7 | 49.5 | 106.2 | 17.0 | 1.54 | 3.2 | 0.049 | 0.065 | 87% | 1190 |
| NGC 5530 | ? | N | 11.8 | 61.9 | 305.4 | 9.4 | 0.31 | 2.8 | 0.046 | 0.057 | 70% | 798 |
| NGC 5643 | Y | Y | 11.8 | 29.9 | 318.7 | 18.2 | 2.14 | 3.5 | 0.034 | 0.058 | 83% | 2667 |
| NGC 6300 | Y | N | 13.1 | 49.3 | 105.5 | 29.2 | 2.39 | 4.0 | 0.050 | 0.059 | 81% | 2120 |
| NGC 6744 | Y | Y | 11.6 | 53.2 | 14.3 | 48.8 | 2.28 | 9.7 | 0.065 | 0.065 | 66% | 2511 |
| NGC 7456 | ? | N | 7.94 | 63.7 | 12.9 | 1.2 | 0.06 | 2.2 | 0.011 | 0.057 | 48% | 133 |
| NGC 7496 | Y | N | 18.7 | 34.7 | 196.4 | 9.8 | 2.16 | 3.3 | 0.029 | 0.056 | 79% | 1557 |

: Galaxy Sample

Table notes: (2–3) If the galaxy has identifiable stellar bars and spiral arms (? – ambiguous; see M. Querejeta et al. 2020, in preparation); (4) Distance (cite: Tully_etal_2009); (5–6) Galaxy inclination and position angle (cite: Lang_etal_2020); (7–9) Galaxy global stellar mass, SFR, and the effective (half-mass) radius estimated from the measured stellar scale length (cite: Leroy_etal_2019); (10–11) CO data rms noise and channel-to-channel correlation at $150$ pc resolution; (12) CO flux completeness at $150$ pc resolution; (13) Number of independent sightlines at $150$ pc resolution.\
(A machine readable version of this table is available in the [PHANGS CADC storage](https://www.canfar.net/storage/list/phangs/RELEASES/Sun_etal_2020b).) $^{\dagger}$ These three very nearby galaxies are only observed by the ACA 7-m and total power telescopes. Because of their proximity, the data still have linear resolutions matched to the other galaxies in the sample. $^{\ddagger}$ Measurements in these four galaxies are not presented in Section [3](#sec:result). $^{\star}$ The estimated CO flux completeness exceeds $100$% for these two targets. This is due to either low S/N data (NGC 4424) or calibration mismatch between the interferometric and single dish data (NGC 1317).

# Data Product

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Galaxy | Resolution | $r_\mathrm{gal}$ | Center | Arm | Inter-arm | $\I_\mathrm{CO(2\text{-}1)}$ | $\Sigma_\mathrm{mol}$ | $\sigma_\mathrm{mol}$ | $P_\mathrm{turb}$ | $\alpha_\mathrm{vir}$ |
|  | \[$\mathrm{pc}$\] | \[$\mathrm{kpc}$\] |  |  |  | \[$\mbox{$\rm K\,km\,s^{-1}$}$\] | \[$\mbox{$\rm M_{\odot}\,pc^{-2}$}$\] | \[$\mbox{$\rm km\,s^{-1}$}$\] | \[$\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$\] |  |
| Circinus | 150 | 0.000 | 1 | 0 | 0 | 7.680e+02 | 3.423e+03 | 7.664e+01 | 6.574e+08 | 5.280e+00 |
| Circinus | 150 | 0.154 | 1 | 0 | 0 | 4.755e+02 | 2.161e+03 | 4.053e+01 | 1.160e+08 | 2.339e+00 |
| Circinus | 150 | 0.154 | 1 | 0 | 0 | 3.649e+02 | 1.659e+03 | 4.124e+01 | 9.228e+07 | 3.154e+00 |
| Circinus | 150 | 0.290 | 1 | 0 | 0 | 3.433e+02 | 1.596e+03 | 4.595e+01 | 1.101e+08 | 4.071e+00 |
| Circinus | 150 | 0.290 | 1 | 0 | 0 | 5.191e+02 | 2.398e+03 | 7.411e+01 | 4.305e+08 | 7.048e+00 |
| Circinus | 150 | 0.307 | 1 | 0 | 0 | 2.265e+02 | 1.053e+03 | 2.411e+01 | 2.001e+07 | 1.698e+00 |
| Circinus | 150 | 0.307 | 1 | 0 | 0 | 2.698e+02 | 1.252e+03 | 2.277e+01 | 2.121e+07 | 1.275e+00 |
| Circinus | 150 | 0.322 | 1 | 0 | 0 | 3.209e+02 | 1.493e+03 | 4.636e+01 | 1.049e+08 | 4.430e+00 |
| Circinus | 150 | 0.322 | 1 | 0 | 0 | 3.470e+02 | 1.624e+03 | 5.172e+01 | 1.420e+08 | 5.068e+00 |
| Circinus | 150 | 0.334 | 1 | 0 | 0 | 1.989e+02 | 9.334e+02 | 3.261e+01 | 3.244e+07 | 3.505e+00 |
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |

: Table of Key Measurements

Table notes: (This table is available in its entirety in the [PHANGS CADC storage](https://www.canfar.net/storage/list/phangs/RELEASES/Sun_etal_2020b).)

# Data Censoring Function

As mentioned in Section [2](#sec:method), our data cube masking scheme introduces a censoring effect that excludes sightlines with low $I_\mathrm{CO}$ and high $\sigma_\mathrm{CO}$. Here we provide the analytic expression for this censoring function.

We consider a generic masking scheme requiring $N$ consecutive channels with $\text{S/N}>X_\mathrm{th}$. The intrinsic CO line profile is assumed to be Gaussian, with a peak brightness temperature of $T_\mathrm{peak}$ and a 1$\sigma$ line width of $\sigma_\mathrm{CO}$. We also assume the line peak is located right at the center of the $N$ consecutive channels, each of which has a channel width $v_\mathrm{ch}$. If the CO intensity in the “edge” channels (i.e., $\pm N/2$ channels away from the line center) exceeds $X_\mathrm{th}\,T_\mathrm{noise}\,v_\mathrm{ch}$, then all channels in between also exceed this threshold, and thus this CO line should enter the signal mask. Following this argument, we can get an expression for the censoring function by integrating the line profile within that “edge” channel: $$\begin{equation}
    \int^{(N/2)\,v_\mathrm{ch}}_{(N/2-1)\,v_\mathrm{ch}} T_\mathrm{peak}\exp(-v^2/2\sigma_\mathrm{CO}^2)\,\mathrm{d}v > X_\mathrm{th}\,T_\mathrm{noise}\,v_\mathrm{ch}~ \label{eq:threshold}.
\end{equation}$$ Recasting this integral by the error function and re-expressing $T_\mathrm{peak}$ with line-integrated intensity $I_\mathrm{CO}=\sqrt{2\pi}\,T_\mathrm{peak}\,\sigma_\mathrm{CO}$, we have $$\begin{align}
    I_\mathrm{CO}>\;&\frac{1}{2}X_\mathrm{th}\,T_\mathrm{noise}\,v_\mathrm{ch} \nonumber\\ &\left[\text{erf}\!\left(\frac{N}{2}\frac{v_\mathrm{ch}}{\sqrt{2}\,\sigma_\mathrm{CO}}\right) - \text{erf}\!\left(\frac{N-2}{2}\frac{v_\mathrm{ch}}{\sqrt{2}\,\sigma_\mathrm{CO}}\right)\right]^{-1}~. \label{eq:censoring}
\end{align}$$

The above derivation assumes an infinitely sharp spectral response curve, which is inconsistent with the non-zero channel-to-channel correlation estimated for our data (see Table [2](#tab:sample)). To address this, we introduce a three-element Hann kernel of the shape $[k,\;1-2k,\;k]$ to model the spectral response curve. Here the value $k$ is determined so that the resultant channel-to-channel correlation matches the estimated $r_\mathrm{ch}$ for our data (cite: Leroy_etal_2016). Convolving the left hand side of Equation [\[eq:threshold\]](#eq:threshold) with this kernel and recasting the formula into a similar form as Equation [\[eq:censoring\]](#eq:censoring), we get a modified censoring function that accounts for the realistic spectral response curve[^10]: $$\begin{align}
    I_\mathrm{CO}>\;&\frac{1}{2}X_\mathrm{th}\,T_\mathrm{noise}\,v_\mathrm{ch} \nonumber\\
    &\left[
    k\cdot\text{erf}\!\left(\frac{N+2}{2}\frac{v_\mathrm{ch}}{\sqrt{2}\,\sigma_\mathrm{CO}}\right) + \right. \nonumber\\
    &\;\;\;(1-3k)\cdot\text{erf}\!\left(\frac{N}{2}\frac{v_\mathrm{ch}}{\sqrt{2}\,\sigma_\mathrm{CO}}\right) - \nonumber\\
    &\;\;\;(1-3k)\cdot\text{erf}\!\left(\frac{N-2}{2}\frac{v_\mathrm{ch}}{\sqrt{2}\,\sigma_\mathrm{CO}}\right) - \nonumber\\
    &\;\;\;\left.k\cdot\text{erf}\!\left(\frac{N-4}{2}\frac{v_\mathrm{ch}}{\sqrt{2}\,\sigma_\mathrm{CO}}\right)
    \right]^{-1}~. \label{eq:real-censoring}
\end{align}$$ Taking $N=2$, $X_\mathrm{th}=2$, $v_\mathrm{ch}=2.5\,\mbox{$\rm km\,s^{-1}$}$, and the corresponding $T_\mathrm{noise}$ and $k$ values for each galaxy in Equation [\[eq:real-censoring\]](#eq:real-censoring), we recover the censoring function shown in Figure [1](#fig:overview).

natexlab

(ref: Accurso_etal_2017) Accurso, G., Saintonge, A., Catinella, B., et al. 2017, MNRAS, 470, 4750

(ref: Armillotta_etal_2019) Armillotta, L., Krumholz, M. R., Di Teodoro, E. M., & McClure-Griffiths, N. M. 2019, MNRAS, 490, 4401

(ref: AstropyCollaboration_etal_2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Blitz_Rosolowsky_2004) Blitz, L., & Rosolowsky, E. 2004, ApJL, 612, L29

(ref: Bolatto_etal_2008) Bolatto, A. D., Leroy, A. K., Rosolowsky, E., Walter, F., & Blitz, L. 2008, ApJ, 686, 948

(ref: Chevance_etal_2020a) Chevance, M., Kruijssen, J. M. D., Hygate, A. P. S., et al. 2020, MNRAS, 493, 2872

(ref: Colombo_etal_2014a) Colombo, D., Hughes, A., Schinnerer, E., et al. 2014a, ApJ, 784, 3

(ref: Colombo_etal_2014b) Colombo, D., Meidt, S. E., Schinnerer, E., et al. 2014b, ApJ, 784, 4

(ref: Colombo_etal_2019) Colombo, D., Rosolowsky, E., Duarte-Cabral, A., et al. 2019, MNRAS, 483, 4291

(ref: denBrok_etal_2020b) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2020, MNRAS submitted

(ref: Dobbs_Bonnell_2008) Dobbs, C. L., & Bonnell, I. A. 2008, MNRAS, 385, 1893

(ref: Dobbs_etal_2019) Dobbs, C. L., Rosolowsky, E., Pettitt, A. R., et al. 2019, MNRAS, 485, 4997

(ref: DonovanMeyer_etal_2013) Donovan Meyer, J., Koda, J., Momose, R., et al. 2013, ApJ, 772, 107

(ref: Egusa_etal_2018) Egusa, F., Hirota, A., Baba, J., & Muraoka, K. 2018, ApJ, 854, 90

(ref: Elmegreen_1989) Elmegreen, B. G. 1989, ApJ, 338, 178

(ref: Field_etal_2011) Field, G. B., Blackman, E. G., & Keto, E. R. 2011, MNRAS, 416, 710

(ref: Fujimoto_etal_2019) Fujimoto, Y., Chevance, M., Haydon, D. T., Krumholz, M. R., & Kruijssen, J. M. D. 2019, MNRAS, 487, 1717

(ref: Gensior_etal_2020) Gensior, J., Kruijssen, J. M. D., & Keller, B. W. 2020, MNRAS, 495, 199

(ref: spectral-cube-v0.4.5) Ginsburg, A., Koch, E., Robitaille, T., et al. 2019, radio-astro-tools/spectral-cube, vv0.4.5, Zenodo, doi:10.5281/zenodo.3558614

(ref: Henshaw_etal_2016) Henshaw, J. D., Longmore, S. N., Kruijssen, J. M. D., et al. 2016, MNRAS, 457, 2675

(ref: Henshaw_etal_2020) Henshaw, J. D., Kruijssen, J. M. D., Longmore, S. N., et al. 2020, Nature Astronomy, doi:10.1038/s41550-020-1126-z

(ref: Herrera-Endoqui_etal_2015) Herrera-Endoqui, M., Dı́az-Garcı́a, S., Laurikainen, E., & Salo, H. 2015, A&A, 582, A86

(ref: Heyer_etal_2001) Heyer, M. H., Carpenter, J. M., & Snell, R. L. 2001, ApJ, 551, 852

(ref: Hirota_etal_2018) Hirota, A., Egusa, F., Baba, J., et al. 2018, PASJ, 70, 73

(ref: Hughes_etal_2013a) Hughes, A., Meidt, S. E., Colombo, D., et al. 2013a, ApJ, 779, 46

(ref: Hughes_etal_2013b) Hughes, A., Meidt, S. E., Schinnerer, E., et al. 2013b, ApJ, 779, 44

(ref: Jeffreson_Kruijssen_2018) Jeffreson, S. M. R., & Kruijssen, J. M. D. 2018, MNRAS, 476, 3688

(ref: Jeffreson_etal_2020) Jeffreson, S. M. R., Kruijssen, J. M. D., Keller, B. W., Chevance, M., & Glover, S. C. O. 2020, MNRAS, doi:10.1093/mnras/staa2127

(ref: Jogee_etal_2005) Jogee, S., Scoville, N., & Kenney, J. D. P. 2005, ApJ, 630, 837

(ref: Kruijssen_etal_2014) Kruijssen, J. M. D., Longmore, S. N., Elmegreen, B. G., et al. 2014, MNRAS, 440, 3370

(ref: Lada_Dame_2020) Lada, C. J., & Dame, T. M. 2020, ApJ, 898, 3

(ref: Lang_etal_2020) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122

(ref: Leroy_etal_2013b) Leroy, A. K., Walter, F., Sandstrom, K., et al. 2013a, AJ, 146, 19

(ref: Leroy_etal_2013a) Leroy, A. K., Lee, C., Schruba, A., et al. 2013b, ApJL, 769, L12

(ref: Leroy_etal_2016) Leroy, A. K., Hughes, A., Schruba, A., et al. 2016, ApJ, 831, 16

(ref: Leroy_etal_2019) Leroy, A. K., Sandstrom, K. M., Lang, D., et al. 2019, ApJS, 244, 24

(ref: McMullin_etal_2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in ASP Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, 127. <http://ui.adsabs.harvard.edu/abs/2007ASPC..376..127M>

(ref: Meidt_etal_2018) Meidt, S. E., Leroy, A. K., Rosolowsky, E., et al. 2018, ApJ, 854, 100

(ref: Meidt_etal_2020) Meidt, S. E., Glover, S. C. O., Kruijssen, J. M. D., et al. 2020, ApJ, 892, 73

(ref: Miville-Deschenes_etal_2017) Miville-Deschênes, M.-A., Murray, N., & Lee, E. J. 2017, ApJ, 834, 57

(ref: Ostriker_etal_2010) Ostriker, E. C., McKee, C. F., & Leroy, A. K. 2010, ApJ, 721, 975

(ref: Pfenniger_Norman_1990) Pfenniger, D., & Norman, C. 1990, ApJ, 363, 391

(ref: Rice_etal_2016) Rice, T. S., Goodman, A. A., Bergin, E. A., Beaumont, C., & Dame, T. M. 2016, ApJ, 822, 52

(ref: Roman-Duval_etal_2016) Roman-Duval, J., Heyer, M., Brunt, C. M., et al. 2016, ApJ, 818, 144

(ref: Rosolowsky_Leroy_2006) Rosolowsky, E., & Leroy, A. 2006, PASP, 118, 590

(ref: Sakamoto_etal_1999) Sakamoto, K., Okumura, S. K., Ishizuki, S., & Scoville, N. Z. 1999, ApJ, 525, 691

(ref: Salo_etal_2015) Salo, H., Laurikainen, E., Laine, J., et al. 2015, ApJS, 219, 4

(ref: Sanchez_etal_2014) Sánchez, S. F., Rosales-Ortega, F. F., Iglesias-Páramo, J., et al. 2014, A&A, 563, A49

(ref: Sanchez_etal_2019) Sánchez, S. F., Barrera-Ballesteros, J. K., López-Cobá, C., et al. 2019, MNRAS, 484, 3042

(ref: Sandstrom_etal_2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5

(ref: Sawada_etal_2012) Sawada, T., Hasegawa, T., & Koda, J. 2012, ApJL, 759, L26

(ref: Schruba_etal_2019) Schruba, A., Kruijssen, J. M. D., & Leroy, A. K. 2019, ApJ, 883, 2

(ref: Semenov_etal_2018) Semenov, V. A., Kravtsov, A. V., & Gnedin, N. Y. 2018, ApJ, 861, 4

(ref: Sheth_etal_2002) Sheth, K., Vogel, S. N., Regan, M. W., et al. 2002, AJ, 124, 2581

(ref: Sormani_etal_2019) Sormani, M. C., Treß, R. G., Glover, S. C. O., et al. 2019, MNRAS, 488, 4663

(ref: Sun_etal_2018) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860, 172

(ref: Sun_etal_2020) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2020, ApJ, 892, 148

(ref: Tress_etal_2020) Tress, R. G., Smith, R. J., Sormani, M. C., et al. 2020a, MNRAS, 492, 2973

(ref: Tress_etal_2020a) Tress, R. G., Sormani, M. C., Glover, S. C. O., et al. 2020b, MNRAS submitted, arXiv:2004.06724

(ref: Tully_etal_2009) Tully, R. B., Rizzi, L., Shaya, E. J., et al. 2009, AJ, 138, 323

[^1]: “*P*hysics at *H*igh *A*ngular resolution in *N*earby *G*alaxie*S* with the *A*tacama *L*arge *M*illimeter *A*rray.” For more information, see [www.phangs.org](www.phangs.org).

[^2]: Internal data release v3.4.

[^3]: For the release that we use, the masks begin with all regions with $\text{S/N}>3.5$ in three consecutive channels. These masks are then expanded to include all adjacent regions with $\text{S/N}>2$ in two successive channels. The `Python` realization of this signal identification scheme is available at <https://github.com/astrojysun/SpectralCubeTools>.

[^4]: Note that for a Gaussian line profile, $\sigma_\mathrm{CO}$ equals its dispersion.

[^5]: This differs from the assumptions adopted in the complementary cloud identification analysis (E. Rosolowsky et al. 2020, in preparation): in that paper, a gas cloud’s extent along the line of sight is limited to $<100$ pc.

[^6]: Here and in subsequent sections “statistically significant” means $p\text{-value} \ll 0.001$.

[^7]: The remaining 10 galaxies have ambiguous classifications (see Table [2](#tab:sample)). Measurements in their central regions are omitted in Figure [2](#fig:regions).

[^8]: <http://edd.ifa.hawaii.edu/index.html>

[^9]: <http://www.adsabs.harvard.edu>

[^10]: The `Python` realization of this censoring function calculation is available at: <https://github.com/astrojysun/SpectralCubeTools>.

</paper>

Write the methods card for this paper.