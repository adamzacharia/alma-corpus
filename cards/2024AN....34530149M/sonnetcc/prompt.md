# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024AN....34530149M\sonnetcc\reply.txt

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
 "bibcode": "2024AN....34530149M",
 "title": "Calculated brightness temperatures of solar structures compared with ALMA and Metsähovi measurements",
 "year": 2024,
 "journal": "Astronomische Nachrichten",
 "first_author": "Matković, Filip",
 "n_authors": 9,
 "arxiv_id": "2402.18978",
 "doi": "10.1002/asna.20230149",
 "alma_projects_linked_by_archive": []
}
```

Paper text:
<paper>
# Calculated brightness temperatures of solar structures compared with ALMA and Metsähovi measurements

# Introduction

The chromosphere is possibly the least observed and studied part of the solar atmosphere in the radio wavelength range. Therefore, it is crucial to study this layer of the atmosphere and to construct theoretical models that best describe the (radio) observations. An important opportunity to compare the results of theoretical models with measurements and to check their reliability is provided by the Atacama Large Millimeter/submillimeter Array (ALMA)[^1]$^{\rm ,}$[^2], which enable the observation of the solar chromosphere in the mm and sub-mm range (Bastian et al. (cite: Bastian2018); Loukitcheva (cite: Loukitcheva2019)). ALMA observations provide a good basis for discrimination between various models and assessment of physical parameters of solar structures.

In the present analysis, we use the semiempirical modeling, in which a solar atmosphere model (electron density and temperature as a function of height) is constructed from the observed spectral lines of various elements, usually in the extreme-ultraviolet (EUV) and infrared parts of the spectrum. The model is used as is or modified for specific solar structures. The radiative transfer equation is then solved giving brightness temperature predictions. The first widely used atmospheric model of this type was the Vernazza$-$Avrett$-$Loeser (VAL) model (Vernazza et al. (cite: Vernazza1981)) and in each subsequent decade new and improved models have been published: the Fontenla$-$Avrett$-$Loeser (FAL) model (Fontenla et al. (cite: Fontenla1993)), the Avrett$-$Loeser (AL) model (Avrett & Loeser (cite: Avrett2008)), and the Avrett$-$Tian$-$Landi$-$Curdt$-$Wülser (ATLCW) model (Avrett et al. (cite: Avrett2015)). In addition, a modification of this class of models was developed by Selhorst et al. ((cite: selhorst2005)) specifically to include spicules and to cover radio frequencies in the 2$-$400 GHz range (Selhorst$-$Silva$-$Costa (SSC) model).

In multiwavelength radio observations, the semiempirical models were used mostly to describe the quiet sun (QS). One such example is the earlier study by Benz et al. ((cite: Benz1997)), which used a modified and extended FAL model to interpret the radio emission from the quiet corona observed with the Very Large Array (VLA) at the wavelengths of 13 mm, 20 mm, and 36 mm. That study found that, at constant electron temperature in the FAL model, an rms fluctuation in density of 10.2%, 17.6%, and 16.4% is required to produce the standard deviations in the QS brightness observed at the three wavelengths, respectively. Benz et al. ((cite: Benz1997)) also point out that the VAL model significantly exceeds the observed QS brightness temperature and deviates more from the observations than the FAL model.

The semiempirical QS models can also be used to study mm and sub-mm features of other solar structures. In previous studies, a similar modeling of the solar atmosphere using the FAL model was utilized to analyze the 8-mm radio emission from coronal holes (CHs), prominences (PRs) on the solar disc, and active regions (ARs) (Brajša et al. (cite: Brajsa2007), (cite: Brajsa2009)). Various models were constructed for a given solar structure by modifying the density and temperature of the FAL model, with thermal bremsstrahlung taken as the dominant radiation mechanism. An important result of those studies was that the assumed thermal bremsstrahlung explains well the observed radio emission of the given solar structures. The FAL model was further developed to calculate the brightness temperature of the QS, ARs, and CHs in the wavelength range of 0.3$-$10 mm (Brajša et al. (cite: Brajsa2018a)). Various models were created and compared with the ALMA observations at the wavelength of 1.21 mm, and the properties (e.g., brightness, density, etc.) of the given structures were determined. In addition to previous studies, the SSC model was used to successfully interpret polar brightening observations at the wavelengths of 1.2, 3, and 18 mm on the Sun (Selhorst et al. (cite: selhorst2017), (cite: Selhorst2019)).

The two newer AL and ATLCW models are based on similar or more accurate observations and better treatment of the structure of the solar atmosphere. The AL model is based primarily on atlases of the EUV solar spectrum from data collected by the Solar Ultraviolet Measurement of Emitted Radiation (SUMER) instrument aboard the Solar and Heliospheric Observatory (SOHO), as well as data from the High Resolution Telescope and Spectrograph (HRTS). The chromospheric part of the model is semiempirical with a temperature distribution adjusted to achieve optimal agreement between the calculated and observed continuum intensities, line intensities, and line profiles. The transition region model is theoretically determined from a balance between radiative losses and downward energy flow from the corona due to thermal conduction and particle diffusion. The boundary conditions at the base of the transition region were determined at the top of the chromosphere from the semi-empirical model.

On the other hand, the ATLCW model is an upgrade of the AL model with the main difference in the treatment of the transition region, where the temperature is adjusted to fit the H, He I, and He II observations and the slope of the Lyman continuum. The profile of the Mg II k line observed with the Interface Region Imaging Spectrograph (IRIS) was also calculated and taken into account when adjusting the calculated atmospheric temperature to the observations.

We now briefly describe the procedure performed in the present analysis. The starting point is the semiempirical ATLCW model of the QS atmosphere, giving density and temperature as a function of height. Such model is then used in its original form or modified for a specific solar structure, in our case AR and CH, as the input model. The modification is performed by multiplying the density and temperature by a numerical factor for the defined height range. Then the radiation mechanism is chosen, in this case thermal bremsstrahlung, and the radiative transfer equation is numerically solved for each input model. The output of the calculation is the radiation intensity (expressed by the brightness temperature) as a function of wavelength. This result is then compared with ALMA and other measurements, and the input model is modified again by changing the numerical factors, if necessary. The cycle is repeated until the best correspondence between calculated and measured brightness temperatures is reached. The final results are the best-fitting model and the goodness of the model fit. The main idea of this work is to compare the predictions of AL and ATLCW models with QS measurements from ALMA and Metsähovi observatories, using thermal bremsstrahlung as the dominant radiation mechanism and improved values of the Gaunt factor. Then, the better model (in our case ATLCW model) is modified to fit the observations of three different solar regions (QS, AR, and CH) returning their estimated electron temperatures and densities.

# The models and the brightness temperature calculation

The main radiation mechanism of the quiet and active chromosphere at mm and sub-mm wavelengths is thermal bremsstrahlung (Zirin (cite: Zirin1988); Hurford (cite: Hurford1992); Brajša (cite: Brajsa1993); White (cite: White2002); Benz (cite: Benz2009); Wedemeyer et al. (cite: Wedemeyer2016)) and it is assumed here for interpretation and calculations. In radio astronomy, the measured radiation intensities are usually expressed in terms of the brightness temperature. Following, for example, Wilson et al. ((cite: Wilson2013)), the brightness temperature can be derived starting from the radiation transfer equation: $$\begin{equation}
\label{Eq_radiative_transfer1}
I_\lambda=\int_{0}^{\infty}B_\lambda e^{-\tau_\lambda}{\rm d}\tau_\lambda,
\end{equation}$$ where $\lambda$ is the measuring wavelength, $\tau_\lambda$ is the optical depth, and $I_\lambda$ is the measured radiation intensity. If we assume that the source function $B_\lambda$ in Equation ([\[Eq_radiative_transfer1\]](#Eq_radiative_transfer1)) follows Planck’s law and we take the Rayleigh$-$Jeans approximation ($hc/\lambda\ll k_\mathrm{B}T_\mathrm{e}$) into account, we can write the source function in the form: $$\begin{equation}
\label{Planck}
B_\lambda=\frac{2hc^2}{\lambda^5\left(e^{\frac{hc}{\lambda k_\mathrm{B}T_\mathrm{e}}}-1\right)}\approx\frac{2ck_\mathrm{B}T_\mathrm{e}}{\lambda^4},
\end{equation}$$ where $h$ is the Planck’s constant, $k_\mathrm{B}$ is the Boltzmann’s constant, $c$ is the speed of light, and $T_\mathrm{e}$ is the electron temperature. If we substitute the $B_\lambda$ function in Equation ([\[Eq_radiative_transfer1\]](#Eq_radiative_transfer1)) with the last expression in Equation ([\[Planck\]](#Planck)) and take into account that the brightness temperature is the solution of the radiative transfer equation, we now write Equation ([\[Eq_radiative_transfer1\]](#Eq_radiative_transfer1)) in a new form (e.g., Brajša et al. (cite: Brajsa2018a)): $$\begin{equation}
\label{Eq_radiative_transfer}
T_\mathrm{b}(\lambda)=\int_{0}^{\infty}T_\mathrm{e}e^{-\tau_\lambda}{\rm d}\tau_\lambda,
\end{equation}$$ where $T_\mathrm{b}(\lambda)=\lambda^4I_\lambda/(2ck_\mathrm{B})$ is the brightness temperature. In the present work, we use Equation ([\[Eq_radiative_transfer\]](#Eq_radiative_transfer)) when calculating the brightness temperature as a function of wavelength. As the wavelength decreases, $\tau_\lambda$ reaches $\tau_\lambda=1$ at lower heights in the solar atmosphere where the temperature is lower. The optical depth d$\tau_\nu$ for the observing frequency $\nu$ of bremsstrahlung for solar abundances and distance d$s$ neglecting the magnetic field is given by (e.g., Benz (cite: Benz2002)): $$\begin{equation}
\label{Eq_optical_depth}
{\rm d}\tau_\nu=\frac{0.01146\;\mathrm{cm^{5}Hz^{2}K^{3/2}}\times\ln\Lambda n^{2}_{e}}{\left(1-8.06\times 10^{7}\;\mathrm{cm^3Hz^{2}}\times n_{e}/\nu^{2}\right)^{1/2}\nu^{2}T_{e}^{3/2}} {\rm d} s  .
\end{equation}$$ The Gaunt factor, $\ln\Lambda$, is a slowly varying function of electron density, $n_{e}$, and temperature, $T_e$ (Rybicki & Lightman (cite: Rybicki1985); Weinberg (cite: Weinberg2020)). In the present work, the Gaunt factor for the observed frequency is calculated using the accurate interpolation method recently developed by van Hoof et al. ((cite: vanHoof2014)) and implemented in the solar context by Simões et al. ((cite: Simoes2017)) and Selhorst et al. ((cite: Selhorst2019)).

## Obtaining theoretical models

As a reference model of the solar atmosphere, we use the ATLCW QS model in its original form. To obtain the brightness temperature profile, we calculate the brightness temperature for a given wavelength using the input $T_{e}$ and $n_{e}$ values from the ATLCW model and store its increase per unit height in an array. These contributions are integrated over all heights defined for a given solar structure, yielding the total brightness temperature for a given wavelength (Equation [\[Eq_radiative_transfer\]](#Eq_radiative_transfer)). This procedure is repeated for all given wavelengths. We note that the calculation procedure in the present work is similar to that used by Brajša et al. ((cite: Brajsa2018a)), but with important differences. Brajša et al. ((cite: Brajsa2018a)) used the FAL model (Fontenla et al. (cite: Fontenla1993)) and the Gaunt factor calculation according to Bekefi ((cite: Bekefi1966)) and Benz ((cite: Benz2002)) and here we use the ATLCW model and the Gaunt factor according to van Hoof et al. ((cite: vanHoof2014)) and Selhorst et al. ((cite: Selhorst2019)).

In order to use the ATLCW QS model as input for the brightness temperature calculation of a given solar structure, it must be modified by scaling the $n_\mathrm{e}$ and $T_\mathrm{e}$ values of the model with multiplicative factors, $f_\mathrm{n}$ and $f_\mathrm{T}$, defined as: $$\begin{equation}
\label{multi_factors}
f_\mathrm{n}=\frac{n_\mathrm{e}\mathrm{(modified)}}{n_\mathrm{e}\mathrm{(original)}},\; f_\mathrm{T}=\frac{T_\mathrm{e}\mathrm{(modified)}}{T_\mathrm{e}\mathrm{(original)}},
\end{equation}$$ where $n_\mathrm{e}$ and $T_\mathrm{e}$ denote electron densities and temperatures of the original and modified models. The model is modified only in the height range defined for a given solar structure. For ARs, we assumed a minimum height of 400 km and a maximum of 57 km (maximum height value available in the ATLCW QS model). For CHs, we assumed the height range of 2$-$57 km, where the minimum height of 2 km was chosen because at about this height the transition region for the used QS model ($T = 2.4 \times 10^5$ K) ends. For QS on the other hand, the entire height range from the photosphere to the maximum available height in the ATLCW QS model was considered.

## Fitting theoretical models to observational data

In order to compare the brightness temperature from the theoretical model and actual measurements, we use the standard $\chi^2$-minimization technique (e.g., Ivezić et al. (cite: Ivezic2014)) to fit the theoretical model on the measured data. The resulting brightness temperature profile obtained from the calculation procedure described above is compared with the observed values and a dimensionless $\chi^2$ analysis is performed, where we calculate the sum of $\chi^2$ values for all the observed wavelengths $\lambda$ using the following form: $$\begin{equation}
\label{chi_squared}
\chi^2=\sum_\lambda{\left(\frac{x_{\mathrm{obs}} - x_{\mathrm{exp}}}{\Delta x_{\mathrm{obs}}}\right)^2},
\end{equation}$$ where $x_{\mathrm{obs}}$ and $x_{\mathrm{exp}}$ correspond to the observed brightness temperature and the prediction of a theoretical model, respectively, and $\Delta x_{\mathrm{obs}}$ is the measurement uncertainty of the observed brightness temperature. The best-fitting brightness temperature profile minimizes the above sum. This is done by varying values of the multiplicative factors $f_\mathrm{n}$ and $f_\mathrm{T}$ (Equation [\[multi_factors\]](#multi_factors)) and for each pair of the two multiplicative factors the brightness temperature calculation is repeated until the global minimum of Equation ([\[chi_squared\]](#chi_squared)) is found. The range of values within which the two multiplicative factors are varied is set so that the input model’s combination of $n_\mathrm{e}$ and $T_\mathrm{e}$ matches observations within the corresponding height range. As a result, we obtain the best-fitting brightness temperature profile with the corresponding $f_\mathrm{n}$ and $f_\mathrm{T}$ factors. The uncertainties of the $f_\mathrm{n}$ and $f_\mathrm{T}$ factors are calculated from the $\chi^2$ function where the $\chi^2$ value reaches $\Delta\chi^2=1$ above the minimum ($\chi^2_\mathrm{min}$), which corresponds to 1$\sigma$ uncertainty.

# Observational results

## ALMA data

ALMA provides single-dish (White et al. (cite: White2017)) and interferometric (Shimojo et al. (cite: Shimojo2017)) observations of the full solar disc and a smaller area on the Sun, respectively. The wavelength bands most frequently used by ALMA are Band 3 and 6, which are centered around the wavelengths of 3 mm and 1.21 mm, respectively. These two bands cover the solar atmosphere in the height range of 600$-$1 km for Band 3 and 400$-$1 km for Band 6, with the highest sensitivity at around 960 km for Band 3 and at around 730 km for Band 6 (see Figure 5 in Wedemeyer et al. (cite: Wedemeyer2016)). In Brajša et al. ((cite: Brajsa2018b)), the results of the first analysis of solar structures in the Band 6 full-disc ALMA image ($\lambda=1.21$ mm, beam size = 26 arcsec) are presented. The measurements of the brightness temperature of various structures (QS, AR, and CH) for December 18, 2015 are given in Table 1 in that paper. These results are repeated here in Table [\[Table_2\]](#Table_2) in a slightly modified form.

+:---------:+:----------:+:------------------:+:---------------:+:---------:+:------------------:+:-------------------------:+:---------------------:+:------------------------------------------------:+
| Structure | Instrument | Date               | $\lambda$/$\nu$ | Beam size | $T_\mathrm{b}$(QS) | $T_\mathrm{b}$(Structure) | $\Delta T_\mathrm{b}$ | Reference                                        |
+-----------+------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
| (name)    | (name)     | (y:m:d)            | (mm)/(GHz)      | (arcsec)  | \(K\)              | \(K\)                     | \(K\)                 | (citation)                                       |
+-----------+------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
| QS        | ALMA       | 2020-08-01         | 0.86/347        | 21        | 5985               | 5985                      | 0                     | Alissandrakis et al. ((cite: Alissandrakis2023)) |
|           +------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
|           | ALMA       | 2015-12-18         | 1.21/248        | 26        | 6040               | 6040                      | 0                     | Brajša et al. ((cite: Brajsa2018b))              |
|           +------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
|           | ALMA       | 2020-01-04         | 1.50/198        | $29$      | 6467               | 6467                      | 0                     | Alissandrakis et al. ((cite: Alissandrakis2023)) |
|           +------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
|           | ALMA       | 2015-12-17         | 2.80/107        | 58        | 7114               | 7114                      | $0$                   | Present work                                     |
|           +------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
|           | Metsähovi  | 1994-10-18 (start) | 3.40/87         | 60        | 7200               | 7200                      | 0                     | Urpo et al. ((cite: Urpo1997))                   |
|           |            +--------------------+                 |           |                    |                           |                       |                                                  |
|           |            | 1995-10-15 (end)   |                 |           |                    |                           |                       |                                                  |
|           +------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
|           | Metsähovi  | 1994-10-18 (start) | 3.90/77         | 72        | 7250               | 7250                      | 0                     | Urpo et al. ((cite: Urpo1997))                   |
|           |            +--------------------+                 |           |                    |                           |                       |                                                  |
|           |            | 1995-10-15 (end)   |                 |           |                    |                           |                       |                                                  |
|           +------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
|           | Metsähovi  | 2018-03-17 (start) | 8.10/37         | 144       | 8100               | 8100                      | 0                     | Kallunki & Tornikoski ((cite: Kallunki2018))     |
|           |            +--------------------+                 |           |                    |                           |                       |                                                  |
|           |            | 2018-05-16 (end)   |                 |           |                    |                           |                       |                                                  |
+-----------+------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
| AR        | ALMA       | 2015-12-18         | 1.21/248        | 26        | 6240               | 7250                      | $+1010$               | Brajša et al. ((cite: Brajsa2018b))              |
|           +------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
|           | ALMA       | 2015-12-17         | 2.80/107        | 58        | 7303               | 7928                      | $+625$                | Present work                                     |
|           +------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
|           | Metsähovi  | 2015-12-19         | 8.10/37         | 144       | 8100               | 8580                      | $+480$                | Present work                                     |
+-----------+------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
| CH        | ALMA       | 2015-12-18         | 1.21/248        | 26        | 6590               | 6540                      | $-50$                 | Brajša et al. ((cite: Brajsa2018b))              |
|           +------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
|           | ALMA       | 2015-12-17         | 2.80/107        | 58        | 7543               | 7398                      | $-145$                | Present work                                     |
|           +------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+
|           | Metsähovi  | 2015-12-19         | 8.10/37         | 144       | 8100               | 8020                      | $-80$                 | Present work                                     |
+-----------+------------+--------------------+-----------------+-----------+--------------------+---------------------------+-----------------------+--------------------------------------------------+

In the present work, we extend the analysis of Brajša et al. ((cite: Brajsa2018b)) by including an analysis of the same solar structures in the Band 3 ALMA full-disc map ($\lambda=2.80$ mm, beam size = 58 arcsec) taken on the previous day, December 17, 2015. Following the procedure described in Brajša et al. ((cite: Brajsa2018b)), we determine the brightness temperature of the QS region in the center of the solar disc for the Band 3 data by averaging the values of all pixels within a radius of about 15 pixels. The size of a single pixel of the Band 3 full-disc map is 6 arcsec on the Sun. For CH, which is a southern polar CH, and thus at the solar limb, the brightness temperature is measured by averaging the value within an area of a radius of 10 pixels within the visible CH structure, but away from the solar limb. Next, the entire AR, which is observed near the central region of the solar disk, is selected based on a numerical criterion by setting the lower threshold for the brightness temperature. The brightness temperature is then averaged over all pixels brighter than this threshold. In this way, sunspots are automatically excluded from the AR and do not contribute to the measurement of the AR brightness temperature.

Limb brightening was taken into account by comparing the brightness temperature measurements of each non-QS structure with the brightness temperature values averaged over a 10-pixel radius QS region located at the same radial distance from the solar center as the observed non-QS structure. Unlike earlier studies by Alissandrakis et al. ((cite: Alissandrakis2017)), Selhorst et al. ((cite: Selhorst2019)), and Sudar et al. ((cite: Sudar2019)), we applied the limb brightening correction to the measured brightness temperatures before the modeling was done. The measurements of the brightness temperature are listed in Table [\[Table_2\]](#Table_2).

In addition to the ALMA Band 3 and Band 6 measurements, we also included the observational results of Alissandrakis et al. ((cite: Alissandrakis2022)) for the Band 7 mode ($\lambda=0.86$ mm, beam size = 21 arcsec) and an estimate for the Band 5 mode ($\lambda=1.50$ mm, beam size = 29 arcsec) also from that paper. Here we use the brightness temperature values from the corrigendum Alissandrakis et al. ((cite: Alissandrakis2023)), in which, unlike the original paper Alissandrakis et al. ((cite: Alissandrakis2022)), the frequency variation of the Gaunt factor was taken into account. The results for Band 5 and 7, available only for QS, are shown in Table [\[Table_2\]](#Table_2).

## Metsähovi data

Due to the current unavailability of the ALMA measurements above the wavelength of 3 mm, we are missing a large part of the mm range reachable for ALMA, which could be important for theoretical modeling of the observed solar features. For this reason, we extend the currently observed ALMA wavelength range to longer wavelengths by including observations from the Metsähovi 14-m diameter radio telescope[^3]. The Cassegrain telescope system of the Metsähovi radio telescope can be used to obtain full-disc and partial maps of the Sun in the wavelength range of 3 mm$-$3 cm (Urpo et al. (cite: Urpo1997)).

In this work, we use full-disc Metsähovi observations of the mentioned solar structures at 3.40 mm (beam size = 60 arcsec), 3.90 mm (beam size = 72 arcsec), and 8.10 mm (beam size = 144 arcsec). The Metsähovi results for the brightness temperature were obtained using a similar procedure as described for ALMA, but with the limb brightening effect already accounted for, are shown in Table [\[Table_2\]](#Table_2).

# Modeling results and comparison with observations

Following the procedure described in Section [2](#Calculation), we obtained the best-fitting brightness temperature profiles using the modified ATLCW QS atmosphere model as the input model in our calculations. In the following subsections, we present the modeling results separately for three different solar structures: QS region in the center of the solar disc, AR devoid of sunspots, and a CH region.

## Quiet sun

![](QS_best_fit.pdf)

The first solar structure is the quiet sun (QS), which is regarded as the region with a diffuse emission devoid of highly active structures (e.g., AR). Due to being the largest and widespread solar structure with similar properties throughout it, for measurements and modeling analysis of the brightness temperature, for the QS structure only a small part of the QS region in the center of the solar disk is considered (see Section [3](#observational_results)).

The calculated best-fitting QS brightness temperature profile (blue dotted curve) obtained for the ALMA and Metsähovi measurements of the central QS structure in Table [\[Table_2\]](#Table_2) using the modified ATLCW QS model is shown for the ALMA wavelength range in Figure [1](#Fig_1). We note that the error bars for the ALMA and Metsähovi data in all figures refer to measurement errors and not the distribution of the mean values of all data points. These measurement errors are estimated to be about 5%$-$10% (Shimojo et al. (cite: Shimojo2017); White et al. (cite: White2017)). Other earlier and much older observational results for the QS compiled by Loukitcheva et al. ((cite: Loukitcheva2004)) and by Benz ((cite: Benz2009)), which have low spatial, spectral, and temporal resolutions, are added here for comparison only.

We see that the original ATLCW QS model (black solid curve) reproduces well the ALMA and Metsähovi observations over the entire ALMA wavelength range. Even the best-fitting QS model does not differ significantly from the original one (to be distinguished from the modified ones), confirming the accuracy of the ATLCW QS model and justifying our use of it as a reference model. In comparison, the profile resulting from the older original AL QS model (black dashed curve) differs significantly from both the measurements and the profile from the original ATLCW QS model already after a wavelength of 2 mm. Moreover, the observations reviewed by Loukitcheva et al. ((cite: Loukitcheva2004)) and by Benz ((cite: Benz2009)) also appear to be in better agreement with the original ATLCW model than with the original AL model. Here the measurements compiled by Loukitcheva et al. ((cite: Loukitcheva2004)) follow both the original and modified ATLCW models well over the entire ALMA wavelength range, while those of Benz ((cite: Benz2009)) agree well only up to a wavelength of 6 mm and begin to depart upward from the ATLCW models at longer wavelengths.

The density and temperature multiplicative factors, $f_\mathrm{n}$ and $f_\mathrm{T}$ respectively (QS_best in Table [\[Table_3\]](#Table_3)), correspond to the best fit of the QS brightness temperature profile. The resulting value of the $f_\mathrm{T}$ factor differs from unity by only 1%, which shows an excellent prediction of the original ATLCW model for the electron temperature of the QS. On the other hand, the resulting $f_\mathrm{n}$ factor shows that the QS density is 13% higher than the value predicted by the original ATLCW model. However, this small deviation in density did not result in any significant change in the best-fitting brightness temperature profile within the ALMA wavelength range, indicating the validity of the original ATLCW QS model.

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Structure | Input atm. model | Height range | $f_\mathrm{n}$ range | $f_\mathrm{T}$ range | Procedure | $f_\mathrm{n}$ best fit | $f_\mathrm{T}$ best fit | $\chi^2_{\mathrm{min}}$ | Ref. name |
| (name) | (name) | (km) | (value) | (value) | (index) | (value) | (value) | (value) | (name) |
| QS | ATLCW QS | $0-57\;797$ | $0.5-1.5$ | $0.5-1.5$ | a | $1.13^{+0.14}_{-0.13}$ | $0.99^{+0.02}_{-0.02}$ | $1.19$ | QS_best |
| AR | ATLCW QS | $400-57\;797$ | $1-3$ | $1-3$ | a | $1.09^{+0.18}_{-0.16}$ | $1.10^{+0.04}_{-0.03}$ | $0.76$ | AR_best |
|  |  |  |  |  | b | $1.13^{+0.17}_{-0.16}$ | $1.09^{+0.03}_{-0.04}$ | $1.71$ |  |
| CH | ATLCW QS | $2\;100-57\;797$ | $1/5-1/0.5$ | $1/25-1/0.5$ | a | $1/\left(1.34^{+1.34}_{-0.33}\right)$ | $1/\left(5.40^{+>20}_{-5.00}\right)$ | $0.49$ | CH1_best |
|  |  |  |  |  | b | $1/\left(1.67^{+3.84}_{-0.75}\right)$ | $1/\left(5.76^{+>20}_{-5.66}\right)$ | $0.18$ |  |
| 4-10 |  |  | $1/5-1/0.5$ | $1/5-1/0.5$ | a | $1/\left(1.08^{+1.07}_{-0.40}\right)$ | $1/\left(1.36^{+>4}_{-1.22}\right)$ | $0.49$ | CH2_best |
|  |  |  |  |  | b | $1/\left(1.33^{+3.08}_{-0.63}\right)$ | $1/\left(1.35^{+>4}_{-1.24}\right)$ | $0.18$ |  |
| 4-10 |  |  | $1/5-1/0.5$ | $1$ | a | $1/\left(1.02^{+1.01}_{-0.25}\right)$ | $1$ | $0.49$ | CH3_best |
|  |  |  |  |  | b | $1/\left(1.26^{+1.23}_{-0.56}\right)$ |  | $0.18$ |  |

## Active region

The second structure is the active region (AR), and it is the region with the highest activity on the Sun with a very enhanced radiation emission in comparison with other regions. In this work, sunspots present inside an AR are considered as a separate structure and are excluded from the AR as described in Section [3](#observational_results). However, unlike the QS, the entire AR structure, with exclusion of sunspots, is considered in our analysis.

The modeling of ARs was similar to that of QS presented in the previous section, but compared with QS, the ALMA and Metsähovi brightness temperature of ARs is determined using two measurement procedures. In the first procedure, which corresponds to the actual measurement, the brightness temperature of AR is determined by adding the difference $\Delta T_\mathrm{b}$ from Table [\[Table_2\]](#Table_2) to the measured brightness temperature of the central QS (QS structure in Table [\[Table_2\]](#Table_2)), while in the second procedure, the difference $\Delta T_\mathrm{b}$ is added to the value given by the profile from the original ATLCW QS model (black curve in Figure [2](#Fig_2)) for the corresponding wavelength. The results for both procedures are indicated by index a and b, respectively, in Figure [2](#Fig_2) and Table [\[Table_3\]](#Table_3). This approach was chosen to investigate whether a small change in the measurements would lead to a significant change in the output brightness temperature profile. A similar approach was also used for CH (Figure [3](#Fig_5)).

The best-fitting AR profiles in Figure [2](#Fig_2) fit the ALMA and Metsähovi measurements well, with no significant differences between the profiles of the two types of measurement a and b over the entire ALMA wavelength range. We should note that the Metsähovi measurement is somewhat lower than predicted by, but still within errors from the AR profile. Moreover, both the observations and the AR profiles lie significantly higher than the brightness temperature profile for the original ATLCW QS model, indicating higher temperatures than the QS values. Assuming thermal bremsstrahlung as the main radiation mechanism higher brightness temperatures in ARs are mainly a consequence of enhanced density in the chromosphere and corona. This shifts the $\tau = 1$ layer to higher altitudes where the temperature is higher, as shown in Figure [2](#Fig_2).

![](AR_best_fit.pdf)

Both measurement procedures also resulted in very similar $f_\mathrm{n}$ and $f_\mathrm{T}$ factors (AR_best in Table [\[Table_3\]](#Table_3)), as expected from the appearance of the output AR profiles. Based on the resulting $f_\mathrm{n}^{\mathrm{a,b}}$ best fit factors, the density of the AR is 9%$-$13% higher than the QS level. This is consistent with the previously mentioned higher brightness of the ARs due to the enhanced plasma density of the ARs compared to the surrounding regions. In the case of $f_\mathrm{T}^{\mathrm{a,b}}$ best fit factors, the results show that the temperature of AR is 9%$-$10% higher than that of QS.

## Coronal hole

Finally, we come to coronal hole (CH), a region of lower temperature and density in the solar atmosphere, which gives it a darker appearance in comparison to the surrounding regions. The CH in question was a southern polar CH (see Figure 1 in Brajša et al. (cite: Brajsa2018b)), whose entire structure was not visible, so only a part of the CH structure away from the solar limb was considered for the CH brightness temperature analysis, as described in Section [3](#observational_results).

Given the observed lack of temperature enhancements in the chromosphere and transition region, it is sufficient that the atmosphere models differ only in density at the transition region and coronal heights. As the coronal radiation is optically thin, a change in coronal temperature would not result in a significant change in brightness temperature. Here we investigate three cases, in which the same $f_\mathrm{n}$ factor range is chosen based on the hybrid network model of Gabriel ((cite: Gabriel1992)), with modification and upgrade taking into account, and its various studies of the solar corona (Stix (cite: Stix1989); Hara et al. (cite: Hara1994); Doschek et al. (cite: Doschek1997); Golub & Pasachoff (cite: Golub1997); Gallagher et al. (cite: Gallagher1999); Avrett (cite: Avrett2000); Koutchmy (cite: Koutchmy2000); Lang (cite: Lang2000); Aschwanden (cite: Aschwanden2004)). For the first case, however, a wide range of $f_\mathrm{T}$ factors is chosen with no a priori assumption, but in two other cases, we restrict that range to values closer to 1 (second case) or fix the factor value to exactly 1 (third case).

![](CH_best_fit.pdf)

All three cases (CH1_best, CH2_best, and CH3_best in Table [\[Table_3\]](#Table_3)) resulted in similar CH brightness temperature profiles, as shown in Figure [3](#Fig_5). Here, the CH profiles follow all measurements well. The measurements lie nearly at or slightly below the QS level from the original ATLCW model (black solid curve), indicating that CH is slightly darker than the surrounding QS atmosphere in the ALMA wavelength range. In addition, the measurement Procedures a and b show no significant difference in the output CH profile. However, the profile for Procedure a is essentially at the QS level, indicating no difference in the brightness temperature between CH and QS, while for Procedure b there is a small but increasing difference between CH and QS toward longer wavelengths.

Moreover, the fact that all three cases of $f^{\mathrm{a,b}}_\mathrm{T}$ best fit factors (Table [\[Table_3\]](#Table_3)) give the same CH profile and that the uncertainty of those factors is higher than the actual factor value, but decreasing as it approaches 1, indicates that the CH brightness temperature does not depend on the electron temperature. If we would set the measurement uncertainties to lower values than they are given in this work, the density factor uncertainty becomes much smaller, but the uncertainty of the temperature factor still remains significantly high and going outside the considered value range. Therefore, a significant change in electron temperature does not result in a significant change in the CH brightness temperature, as is predicted. One can then simply set the temperature factor to 1 like in the third case. Between cases, the $f^{\mathrm{a,b}}_\mathrm{n}$ best fit factors (Table [\[Table_3\]](#Table_3)) do not change significantly for both Procedures a and b. Procedure b yields a slightly lower density than Procedure a. However, the same resulting $f_\mathrm{n}$ and $f_\mathrm{T}$ factors of the best fit show that CH is less dense than QS, but also slightly colder, which is in good agreement with the expected appearance of CHs in the solar atmosphere (Baranovskii et al. (cite: Baranovskii2019); Gopasyuk et al. (cite: Gopasyuk2020)).

# Discussion and conclusions

A comparison of the QS brightness temperature profiles calculated from the ATLCW QS atmosphere model with the recent ALMA and Metsähovi observations (Figure [1](#Fig_1)) reveals general agreement over the entire ALMA wavelength range. The best-fitting QS model showed no significant deviation from the original ATLCW model in both density and temperature. These results show that the original ATLCW QS model is sufficient for describing the QS atmosphere and no additional modifications are needed in the model at this time.

In the ALMA and Metsähovi full-disc images, the ARs appear significantly brighter than the measured surrounding QS atmosphere, but also brighter than the ATLCW QS level (Figure [2](#Fig_2)). At mm and sub-mm wavelengths, ARs are bright primarily due to increased density, and our AR models appear to be in a good agreement with this statement. We note that the electron temperature was also higher for ARs. The excess temperature of ARs compared to QS is consistent with the expected AR features where a strong magnetic field could lead to an increase in temperature, for example, due to dissipation in current sheets (da Silva Santos et al. (cite: daSilvaSantos2022)).

Using the SSC atmosphere model for the QS, de Oliveira e Silva et al. ((cite: deOliveiraeSilva2022)) modeled the density and temperature for different parts of an AR (umbra, penumbra, and plage) up to 6 000 km above the photosphere. The AR in question is the same as the one observed in the present work and in Brajša et al. ((cite: Brajsa2018b)). Devoid of sunspot structures (umbra and penumbra), in the chromosphere, de Oliveira e Silva et al. ((cite: deOliveiraeSilva2022)) obtained the average AR density about 47% higher and a temperature about 7% higher than the SSC QS values. Our results for the AR $f_\mathrm{T}$ best fit factor (Table [\[Table_3\]](#Table_3)) somewhat agree with the results by de Oliveira e Silva et al. ((cite: deOliveiraeSilva2022)), while our $f_\mathrm{n}$ best fit factors (Table [\[Table_3\]](#Table_3)) seem to be in the lower range of their model. However, their value of 47% higher density would still produce an AR profile within the measurement errors and also close to the AR profiles we obtained.

The last structure we analyzed were CHs. The ALMA and Metsähovi measurements reveal that the CHs have slightly lower brightness temperatures than the measured QS (Table [\[Table_2\]](#Table_2)) and the ATLCW QS model (Figure [3](#Fig_5)). All output CH brightness temperature profiles indicate very little or almost no difference from the ATLCW QS level over the entire ALMA wavelength range, resulting in the CH being slightly darker than the QS at ALMA wavelengths. Moreover, our results also provide clear evidence that the brightness temperature of the CHs depends on their electron density rather than their temperature, which is consistent with the results of earlier observational and modeling studies by Brajša et al. ((cite: Brajsa2007), (cite: Brajsa2018a)).

Considering the CH density, out of three cases, the CH1_best has significantly lower density when compared with the QS. Because the CH is at the solar limb, where more higher atmospheric layers are observed on average, one would expect to see a higher contrast in density, as well as temperature between a CH and the surrounding QS. The CH1_best results for both the electron density and temperature could indicate just that. For a similar temperature, as is the situation with the three cases (CH1_best, CH2_best, and CH3_best) individually, a lower density means that the CH profile shifts downward toward lower brightness temperatures. This is true for all three cases. However, having both lower density and temperature, one would expect a profile to have a larger downward shift, but all cases give similar profiles despite different output densities and temperatures. This could indicate that the chromospheric appearance of a CH visible in the ALMA wavelength range is not too sensitive to the density changes. Similarly, temperature changes as those seen among the three cases also do not affect the chromospheric appearance of a CH significantly. If there is any significant difference between the investigated cases, it might be at the coronal heights, outside the observed height range of the current measurements. To single out the more physical case for the given CH, we would first need to get measurements at even more wavelengths, which would increase the number of data points used in the profile fitting. Also, the current observed wavelength range might need to be extended to even coronal heights to constrain more the possible density and temperature parameters, for which the nonlinear Equation ([\[Eq_radiative_transfer\]](#Eq_radiative_transfer)) gives the best-fitting profile (future work).

Using the He I observations from the Solar tower telescope BST-2 and H$\alpha$ observations from the Global Oscillations Network Group (GONG) of a polar CH in the solar chromosphere, Baranovskii et al. ((cite: Baranovskii2019)) found the temperature of CHs to be in the range of 4$-$8 K, which is 500$-$1 K lower than the QS level. This results in a CH temperature about 1.12$-$1.23 times lower than that of the surrounding QS. Also, based on the polar and equatorial CHs, Gopasyuk et al. ((cite: Gopasyuk2020)) found the CH temperatures to be 1.29$-$1.33 times lower than the QS value. The results of these two studies agree well with our results, especially with CH2_best in Table [\[Table_3\]](#Table_3). In addition, Baranovskii et al. ((cite: Baranovskii2019)) found that the density of observed CHs in the solar chromosphere is 2$-$3 times lower than that of QS. Our results (Table [\[Table_3\]](#Table_3)) give a CH density 1$-$1.7 times lower than the QS value, being below the minimum value found by Baranovskii et al. ((cite: Baranovskii2019)). When the uncertainties in the density factors are taken into account, the upper limit of our results falls inside the value range determined by these authors. This small difference between our results and those of Baranovskii et al. ((cite: Baranovskii2019)) could be because different CHs were observed, but also due to different spatial resolutions in the two studies.

It should be noted that the ATLCW, AL, and similar atmosphere models are hydrostatic models. This means that, for example, a modified temperature would change the pressure scale height, and thus the density profile. The obtained brightness temperature profiles for the observed AR and CH appear not to follow this trend because the profiles for both solar structures are less sensitive to the temperature changes and more sensitive to the density changes. From one aspect, when observing the brightness temperature of the solar atmosphere, more than one atmospheric layer in the observer’s line-of-sight contributes to the overall measured brightness temperature. In the case of AR and CH, this means that a non-negligible change in density in the observed column of plasma in the solar atmosphere would cause a significant change in the observed brightness temperature. The change, significant or not, in only temperature in the observed plasma column by itself might not be enough to make as significant change in the measured intensity as the change in density would have. From another aspect, having different sensitivities on the density and temperature changes, the AR and CH structures as a whole might not be governed by hydrostatic laws, but rather some other laws or mechanisms, most likely related to magnetic field structure and its properties. If in fact the hydrostatic case is valid for AR and CH structures, it would not be applicable for a structure as a whole, but instead only within specific layers of a given structure.

Furthermore, we compare the current modeling results based on the modified ATLCW model presented in this work with earlier efforts by Brajša et al. ((cite: Brajsa2018a)) based on the modified FAL model:

\(i\) The QS brightness temperature profiles based on the ATLCW models are systematically higher than for the modified FAL models. The functional dependence of brightness temperature on wavelength is also different for the two models.

\(ii\) The QS brightness temperature as a function of wavelength based on the ATLCW solar atmosphere model agrees much better with observations, both from ALMA, Metsähovi, and from other studies, than the models presented by Brajša et al. ((cite: Brajsa2018a)).

\(iii\) The models of ARs in the present work are more realistic and closer to the observational results than in the previous study (Brajša et al. (cite: Brajsa2018a)).

\(iv\) The results for CHs are consistent at the qualitative level (no obvious difference from the QS level for wavelengths 0.3$-$4 mm and slightly lower emission of CHs for wavelengths 4$-$10 mm), but the functional dependence of brightness temperature on wavelength is different compared with the previous models.

It should be noted that for structures other than QS we had only three observed wavelengths on which to base our analysis and conclusions. Therefore, more observations, especially above the wavelength of 3 mm, are needed to improve the current models, obtain more precise values of the density and temperature factors with lower uncertainties than the current results, and get a better picture of the physical properties of the solar structures. Moreover, depending on the spatial resolution (beam size), single-dish measurements could potentially lead to incorrect conclusions about the solar structure depending on how much of the surrounding region is included in the average brightness temperature measurement. For this reason, a comparison between the results of single-dish (as in this work) and interferometric observations could be useful to see if a model based on one type of observation is also valid for the other type (future work).

A similar analysis, as presented in this work, can also be applied to other solar structures such as prominences and sunspots. However, we should note that both prominences and sunspots are not background structures as QS, ARs, and CHs are. Prominences have complex three-dimensional structures that extend from the chromosphere to the corona, while sunspots are relatively small structures in the low solar atmosphere and single-dish observations are often not able to resolve them. This represents a challenge when modeling these two solar structures, so they should be treated differently than the solar structures analyzed in the present article. In future work, we plan to analyze both prominences and sunspots using a similar modeling as in this work, but including special treatments in order to study their complex two-dimensional and three-dimensional structures and properties in more details.

The results of this work and their comparison with earlier studies suggest that the approach of using one-dimensional models based on the semi-empirical ATLCW model proved to be a good basis for modeling solar structures and sufficient for obtaining realistic brightness temperature values of those structures. We plan to extend the current analysis of this work by testing this approach for other solar structures not yet addressed in this work. However, the one-dimensional approach has a significant disadvantage compared to multidimensional models. For a given wavelength, the one-dimensional models only give the mean value of the brightness temperature of a given solar structure as a whole, without any details about the substructure. The next step would therefore be to extend the current one-dimensional model to a two-dimensional model, and later three-dimensional model. Using the procedure described in this work, one can further extend this procedure to obtain a two-dimensional brightness temperature map, together with corresponding electron density and temperature maps, of a given solar structure for different observing wavelengths (heights). We would then be able to study the cross-section of a solar structure and the variation of brightness temperature, and other physical properties within the structure. This will be addressed in future work.

# Acknowledgments

This work was supported by the Croatian Science Foundation as part of the "Young Researchers’ Career Development Project - Training New Doctorial Students" under the project 7549 "Millimeter and submillimeter observations of the solar chromosphere with ALMA". Support from the Austrian-Croatian Bilateral Scientific Projects ”Comparison of ALMA observations with MHD-simulations of coronal waves interacting with coronal holes” and ”Multi-Wavelength Analysis of Solar Rotation Profile” is also acknowledged. It has also received funding from the Horizon 2020 project SOLARNET (824135, 2019–2023). In this paper, ALMA data ADS/JAO.ALMA#2011.0.00020.SV were used. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. We thank the ALMA project for enabling solar observations with ALMA. This publication also uses data from the Metsähovi Radio Observatory, operated by the Aalto University (Aalto University (cite: Aalto2019)). RB acknowledges financial support from the Alexander von Humboldt Foundation. HGL acknowledges financial support from the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation)$-$Project-ID 138713538$-$SFB 881 ("The Milky Way System”, subproject A04). CLS acknowledges financial support from the São Paulo Research Foundation (FAPESP), grant number 2019/03301-8. We would also like to thank Manuela Temmer for critical reading of the manuscript.

(ref: Aalto2019)

Aalto University.

  , *Metsähovi Radio Observatory public solar database*, Espoo, Finland: Aalto University, Metsähovi Radio Observatory., <http://urn.fi/urn:nbn:fi:att:f371cb6d-f84c-4d76-99e4-c39c639fd0de>.

(ref: Alissandrakis2022)

Alissandrakis, CE. , Bastian, TS.   Nindos, A.

  , .

(ref: Alissandrakis2023)

Alissandrakis, CE. , Bastian, TS.   Nindos, A.

  , .

(ref: Alissandrakis2017)

Alissandrakis, CE. , Patsourakos, S. , Nindos, A.   Bastian, TS.

  , .

(ref: Aschwanden2004)

Aschwanden, MJ.

  , *Physics of the Solar Corona. An Introduction*, Chichester, UK: Praxis Publishing Ltd.

(ref: Avrett2000)

Avrett, E.

  , *Photospheric-Chromospheric Model*. *Allen’s Astrophysical Quantities*, ed. A. N. Cox, Springer (New York).

(ref: Avrett2015)

Avrett, E. , Tian, H. , Landi, E. , Curdt, W.   Wülser, JP.

  , .

(ref: Avrett2008)

Avrett, EH.   Loeser, R.

  , .

(ref: Baranovskii2019)

Baranovskii, EA. , Gopasyuk, OS.   Shtertser, NI.

  , .

(ref: Bastian2018)

Bastian, TS. , Bárta, M. , Brajša, R.  et al.

  , .

(ref: Bekefi1966)

Bekefi, G.

  , *Radiation processes in Plasmas*, New York, London, Sydney: John Wiley and Sons, Inc.

(ref: Benz2002)

Benz, AO.

  , *Plasma Astrophysics*, Astrophysics and Space Science Library, 2nd ed., Vol. 279, Kluwer (Dordrecht).

(ref: Benz2009)

Benz, AO.

  , *Radio Emission of the Quiet Sun*. In: Trümper J. (ed.), *Landolt Börnstein*, Springer-Verlag (Berlin), 103 – 117.

(ref: Benz1997)

Benz, AO. , Krucker, S. , Acton, LW.   Bastian, TS.

  , .

(ref: Brajsa1993)

Brajša, R.

  , .

(ref: Brajsa2007)

Brajša, R. , Benz, AO. , Temmer, M. , Jurdana-Šepić, R. , Šaina, B.   Wöhl, H.

  , .

(ref: Brajsa2018a)

Brajša, R. , Kuhar, M. , Benz, AO.  et al.

  , .

(ref: Brajsa2009)

Brajša, R. , Romštajn, I. , Wöhl, H. , Benz, AO. , Temmer, M.   Roša, D.

  , .

(ref: Brajsa2018b)

Brajša, R. , Sudar, D. , Benz, AO.  et al.

  , .

(ref: daSilvaSantos2022)

da Silva Santos, JM. , Danilovic, S. , Leenaarts, J.  et al.

  , .

(ref: deOliveiraeSilva2022)

de Oliveira e Silva, AJ. , Selhorst, CL. , Costa, JER.  et al.

  , .

(ref: Doschek1997)

Doschek, GA. , Warren, HP. , Laming, JM.  et al.

  , .

(ref: Fontenla1993)

Fontenla, JM. , Avrett, EH.   Loeser, R.

  , .

(ref: Gabriel1992)

Gabriel, A.

  , *The Solar Corona*. *NATO Advanced Science Institutes (ASI) Series C*, eds. J. T. Schmelz & J. C. Brown, Dordrecht: Springer,  373.

(ref: Gallagher1999)

Gallagher, PT. , Mathioudakis, M. , Keenan, FP. , Phillips, KJH.   Tsinganos, K.

  , .

(ref: Golub1997)

Golub, L.   Pasachoff, JM.

  , *The Solar Corona*, Cambridge University Press (Cambridge).

(ref: Gopasyuk2020)

Gopasyuk, OS. , Baranovskii, EA. , Tarashchuk, VP.   Shtertser, NI.

  , .

(ref: Hara1994)

Hara, H. , Tsuneta, S. , Acton, LW. , Bruner, ME. , Lemen, JR.   Ogawara, Y.

  , .

(ref: Hurford1992)

Hurford, G.

  , *Solar Radio Observations*. *NATO Advanced Science Institutes (ASI) Series C*, eds. J. T. Schmelz & J. C. Brown, Dordrecht: Springer,  373.

(ref: Ivezic2014)

Ivezić, Ž. , Connolly, AJ. , VanderPlas, JT.   Gray, A.

  , *Statistics, Data Mining, and Machine Learning in Astronomy: A Practical Python Guide for the Analysis of Survey Data* ( ). .

(ref: Kallunki2018)

Kallunki, J.   Tornikoski, M.

  , .

(ref: Koutchmy2000)

Koutchmy, S.

  , *Solar Corona*. *Allen’s Astrophysical Quantities*, ed. A. N. Cox, Springer (New York).

(ref: Lang2000)

Lang, KR.

  , The sun from space, Berlin, Heidelberg: Springer-Verlag.

(ref: Loukitcheva2019)

Loukitcheva, M.

  , .

(ref: Loukitcheva2004)

Loukitcheva, M. , Solanki, SK. , Carlsson, M.   Stein, RF.

  , .

(ref: Rybicki1985)

Rybicki, GB.   Lightman, AP.

  , *Radiative Processes in Astrophysics*, Weinheim, Germany: Wiley-VCH.

(ref: selhorst2005)

Selhorst, CL. , Silva, AVR.   Costa, JER.

  , .

(ref: Selhorst2019)

Selhorst, CL. , Simões, PJA. , Brajša, R.  et al.

  , .

(ref: selhorst2017)

Selhorst, CL. , Simões, PJA. , Oliveira e Silva, AJ. , Giménez de Castro, CG. , Costa, JER.   Valio, A.

  , .

(ref: Shimojo2017)

Shimojo, M. , Bastian, T. , Hales, A.  et al.

  , .

(ref: Simoes2017)

Simões, PJA. , Kerr, GS. , Fletcher, L. , Hudson, HS. , Giménez de Castro, CG.   Penn, M.

  , .

(ref: Stix1989)

Stix, M.

  , *The Sun. An Introduction*, Springer-Verlag (Berlin, Heidelberg, New York).

(ref: Sudar2019)

Sudar, D. , Brajša, R. , Skokić, I.   Benz, AO.

  , .

(ref: Urpo1997)

Urpo, S. , Pohjolainen, S. , Heikkilä, J.   Wiik, K.

  , *Solar Observations at Metsähovi in 1994-1995*, Espoo, Finland: Hels. Univ. Technol., Metsähovi Radio Res. Stn., Rep. Ser. A, No. 26.

(ref: vanHoof2014)

van Hoof, PAM. , Williams, RJR. , Volk, K.  et al.

  , .

(ref: Vernazza1981)

Vernazza, JE. , Avrett, EH.   Loeser, R.

  , .

(ref: Wedemeyer2016)

Wedemeyer, S. , Bastian, T. , Brajša, R.  et al.

  , .

(ref: Weinberg2020)

Weinberg, S.

  , *Lectures on Astrophysics*, Cambridge University Press (Cambridge).

(ref: White2002)

White, SM.

  , *The Solar Atmosphere at Radio Wavelengths*. *Stellar Coronae in the Chandra and XMM-NEWTON Era*, eds. F. Favata & J. J. Drake, San Francisco, CA: Astronomical Society of the Pacific,  277,  299.

(ref: White2017)

White, SM. , Iwai, K. , Phillips, N.  et al.

  , .

(ref: Wilson2013)

Wilson, TL. , Rohlfs, K.   Hüttemeister, S.

  , *Tools of Radio Astronomy* ( ). .

(ref: Zirin1988)

Zirin, H.

  , *Astrophysics of the Sun*, Cambridge University Press (Cambridge).

[^1]: <http://www.almaobservatory.org>

[^2]: <https://www.eso.org/sci/facilities/alma.html>

[^3]: <https://www.aalto.fi/en/metsahovi-radio-observatory>

</paper>

Write the methods card for this paper.