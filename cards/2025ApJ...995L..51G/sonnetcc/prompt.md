# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...995L..51G\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...995L..51G",
 "title": "The CO-to-H<SUB>2</SUB> Conversion Factor in the Milky Way's Central Parsec",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Gorski, Mark D.",
 "n_authors": 2,
 "arxiv_id": "2511.16720",
 "doi": "10.3847/2041-8213/ae211f",
 "alma_projects_linked_by_archive": [
  "2016.1.00870.S",
  "2017.1.00040.S",
  "2017.1.00995.S",
  "2019.1.01559.S"
 ]
}
```

Paper text:
<paper>
# The CO–to–H$_{2}$ conversion factor in the Milky Way’s central parsec

## Abstract

Carbon monoxide (CO) emission is a widely used tracer of molecular hydrogen (H$_{2}$) in the interstellar medium (ISM), owing to its abundance, low excitation energy, and ease of detection in cold molecular environments, in contrast to H$_{2}$  itself. While the CO-to-H$_{2}$  conversion factor is often assumed to be constant across the disks of galaxies, deviations are observed in extreme environments such as the central molecular zone (CMZ) in galactic nuclei. Here we present the first estimate of the CO-to-H$_{2}$ conversion factor on sub-kpc scales. We calculate CO-to-H$_{2}$ conversion in the Milky Way’s Circumnuclear Disk/Ring (CND/CNR) at $\sim 1$ pc radius around the Galactic Center black hole. We derive a conversion factor of $\alpha_\mathrm{CO} \simeq 4.5\pm2.5$ M$_{\odot}$(K km s$^{-1}$ pc$^{2}$)$^{-1}$ or X\[CO\] $\simeq (2.1\pm1.1)\times 10^{20}$ cm$^{-2} (\mathrm{K \, km \, s^{-1}})^{-1}$. This value is consistent with the Galactic disk but higher than CMZ.

show\]mark.gorski@northwestern.edu

# Introduction

Carbon monoxide (CO) is the most commonly used tracer of the molecular gas in the interstellar medium (ISM) (cite: Bolatto2013b). It has a relatively high abundance in the molecular ISM, a low excitation energy ($\sim5$ K), a low critical density, and can be excited even in cold $\sim10$ K ISM. In contrast, molecular hydrogen (H$_{2}$), while much more common, has its lowest energy transition is in the far-infrared at $\sim500$ K. As a result, estimates of the total molecular gas mass in both local and distant galaxies and their substructures often rely on the CO–to–H$_{2}$ conversion factor.

The CO–to–H$_{2}$ conversion factor is commonly denoted as either a scaling relation between CO luminosity measured in K km s$^{-1}$ pc$^{2}$  and the mass of molecular gas measured in M$_{\odot}$  ($\alpha_\mathrm{CO}$), or a scaling relation between the integrated CO intensity measured in $\mathrm{K} \,\mathrm{km \,s}^{-1}$ and the H$_2$ column density measured in $\mathrm{cm}^{-2}$ ($X_\mathrm{CO}$).

The CO–to–H$_{2}$ conversion factor is often assumed to be constant throughout galactic disks. Several have shown this to be generally true regardless of the CO abundance or radiative transfer effects (cite: Sandstrom2013; Bolatto2013b). However, in some environments a deviation from the galactic mean is expected, e.g., high-density, low-metallicity, high-temperature, and increased velocity dispersion environments. For example, in the Milky Way’s central molecular zone (CMZ), located in the inner 300 pc of the Galactic center, the CO–to–H$_{2}$ is a factor of $3-10$ lower than the galactic disk (cite: Kohno2024; Oka1998).

In this work we used observations conducted with the Atacama Large Millimeter/submillimeter Array (ALMA) of a section of the Galactic Center Circumnuclear Disk/Ring (CND/CNR) in the $^{12}{\rm
CO}(J=2-1)$ line at 230.538 GHz. These are the first observations of this region in this line since (cite: Marshall1994). Combined with known properties of the CND deduced from observations in a multitude of lines (cite: James2021; Hsieh2018; Tsuboi2018; Requena-Torres2012; Lau2013; Liu2013; Oka2011; Etxaluze2011), we deduce the CO–to–H$_{2}$ conversion factor in the Milky Way’s CND without relying on the traditional assumption of virialization.

This paper is organized as follows. In Section [2](#sec:observations) we describe the observations and summarize the data processing techniques. In Section [3](#sec:co2mh) we calculate CO–to–H$_{2}$ conversion factor in the Milky Way’s CND in two different ways and discuss the uncertainties. In Section [5](#sec:assume) we summarize the results and give the final estimates for $\alpha_\textrm{CO}$ and $X_\mathrm{CO}$.

![](CO21_mom0_reg.pdf)

# Observations

## Calibration and Image quality

We combined data from ALMA Band 6 observations of the Milky Way’s central black hole Sgr A$^*$ from projects 2016.1.00870.S, 2017.1.00995.S, and 2019.1.01559.S (PI: Murchikova). All observations are conducted at around 230 GHz and capture the $^{12}{\rm
CO}(J=2-1)$ line at 230.538 GHz. Every observation used J1924-2914 ($\sim$2 Jy) for flux/bandpass calibration and J1744-3116 (0.27$\pm$0.03 Jy) for complex gain calibration. We adopt ALMA’s standard Band 6 calibration uncertainty of 10% on the flux values. The data have a half-power primary beam width (i.e., limitation of the telescope’s field of view due to the size of 12 m antennas) of 22.7$^{\prime\prime}$  at 230.538 GHz.

Calibration of the $^{12}{\rm
CO}(J=2-1)$ data was conducted in several steps. Sgr A$^*$ varies on timescales of seconds and the flux can change by $\sim1$ Jy within half hour (e.g., (cite: Murchikova2021)). We used `UVmultifit` (cite: marti-vidal2014) to fit the variability of Sgr A$^*$  at uv-level. We then used the time-dependent lightcurve to self-calibrate the data. Finally, we removed the continuum emission of the black hole from the data at the uv-level to improve the quality of imaging. The imaging was conducted with the Common Astronomy Software Applications (CASA) using task `tclean` with multiscale deconvolution (scales: 0, 7, 42, 126 pixels; and Briggs weighting: 0.5). The primary beam’s first null is at 27.1$^{\prime\prime}$  from the center of the image. The produced image has 0.02$^{\prime\prime}$pixels and a diameter of about 54$^{\prime\prime}$ or $\sim$2 pc at the approximate distance to the Galactic Center of $D=8.3$ kpc. The produced image covers the primary beam nearly completely.

![](HCN10_mom0_reg.pdf)

The absolute shortest projected baseline in the observations has a length of 12.4 m for a maximum recovered scale of 26.4$^{\prime\prime}$. $^{12}{\rm
CO}(J=2-1)$ data cubes have 25 $\mathrm{km \, s}^{-1}$ spectral resolution and 80 $\mu$Jy rms noise, smoothed to a common beam size of 0.256$^{\prime\prime}$×0.235$^{\prime\prime}$  with a postilion angle of 60.3$^{\circ}$. Integrated intensity maps are made using pixels with values $>5\sigma$. Velocities are in the LSRK frame (radio convention). Continuum subtraction of Sgr A West was done in the image domain via linear fitting to line-free channels. The inner 0.5$^{\prime\prime}$  (0.002 pc) radius around the Sgr A$^*$  is masked due to residual (i.e., not fully removed at the uv-level) black hole emission.

We also adopt ${\rm
HCN}(J=1-0)$ data cubes from the dataset of (cite: Hsieh2021). ${\rm
HCN}(J=1-0)$ data is included in their ${\rm CS}(J=2\to1)$ observations (ALMA project 2017.1.00040.S). The synthesized beam for ${\rm
HCN}(J=1-0)$ data is 3.69$^{\prime\prime}$×2.33$^{\prime\prime}$ with a position angle of 85.1$^{\circ}$, the cube has an rms of 0.11 Jy/beam, and a spectral resolution of 0.8 km s$^{-1}$.

## Flux recovery

An incomplete sampling of the uv-plane particularly at short spacings, can lead to resolved-out flux. To mitigate this issue, we (i) restrict our flux measurements to regions that are well resolved (see Figure [1](#fig:CNDreg) white contours); and (ii) compare the recovered flux to $^{12}{\rm
CO}(J=1-0)$ measurements with the Nobeyama 45 m single-dish telescope (cite: Tokuyama2019), assuming a ${^{12}{\rm CO}(J=2-1)}/ {^{12}{\rm CO}(J=1-0)}$ ratio of 0.85 with an uncertainty of $\pm$0.2. We adopt this value because it is the mean between the optically thick limit (a ratio of 1) and the value of 0.7 that is commonly measured in the local universe (cite: Sandstrom2013). The uncertainty of $\pm$0.2 includes both conditions. We estimate the filling factor from the maximum linear size (34$^{\prime\prime}$) of the individual regions captured within the white contours in Figure [1](#fig:CNDreg). The resolution of the Nobeyama data is 15$^{\prime\prime}$. The filling factor is thus the ratio of the an individual area in Figure [1](#fig:CNDreg) and the 15$^{\prime\prime}$$\times$34$^{\prime\prime}$ region sampled by Nobeyama. The respective values for the west side and east side are 0.436 and 0.444. The expected $^{12}{\rm
CO}(J=2-1)$ integrated flux density would be 14,300$\pm$3000 Jy km s$^{-1}$. We find that the flux recovered in our ALMA observations is $88\pm21$% of the flux observed by the single-dish Nobeyama 45 m telescope and thus consistent with all flux being recovered.

# CO–to–H$_{2}$ conversion factor in Milky Way’s Galactic Center

## Caculating by area

Consider the total integrated $^{12}{\rm
CO}(J=2-1)$ emission of the CND captured within the white contour on our map (Figure [1](#fig:CNDreg)). The total integrated flux in this region is 12,400 Jy km s$^{-1}$. The area of the CND captured in the image and used for calculation is 460.6 $\text{arcsec}^{2}.$ As the model for the full CND, we adopt an ellipse with a semi-major axis of 58$^{\prime\prime}$, an inclination of 30$^{\circ}$, and the area of 5284.2 $\text{arcsec}^{2}$ (dotted line in Figure [2](#fig:CNDwhole), (cite: Tsuboi2018)). The fraction of the full CND captured in $^{12}{\rm
CO}(J=2-1)$ map (see white contours in Figure [2](#fig:CNDwhole)) is about 8.7%. The total molecular mass of the CND is usually estimated to be a few $10^4$ M$_{\odot}$  but the exact value varies (cite: James2021; Hsieh2018; Tsuboi2018; Requena-Torres2012; Lau2013; Liu2013; Oka2011; Etxaluze2011). Here we adopt the value of $3.0 \pm 1.5\times10^4$ M$_{\odot}$, which is closest to the estimate of (cite: Tsuboi2018). In the calculation of the CO-to-H$_{2}$ conversion factor below, the errorbars are dominated by the uncertainties on the mass of the CND.

Here we use a purely geometrical approach and assume that the fraction of the captured area corresponds to the fraction of mass in this region. So we expect about 8.7% of the mass of the CND to be within the selected regions in Figure [1](#fig:CNDreg). This gives the value of the CO-to-H$_{2}$ conversion factor at $$\begin{eqnarray*}

\alpha_{\rm{CO}}\big|_\mathrm{by \, area }&\simeq& 4.3\pm2.3 \, M_\odot (\mathrm{K \, km \, s^{-1} \, pc^2})^{-1}.
\end{eqnarray*}$$

This approach does not take into account density variations in the CND. We consider density variations below.

## Calculating by fraction of HCN emission

Let us assume that the density variations in the CND are relatively well represented by the variations of the integrated ${\rm
HCN}(J=1-0)$ flux, and calculate the ratio of the integrated ${\rm
HCN}(J=1-0)$ flux within selected regions on Figure [1](#fig:CNDreg) to the whole CND. We use ${\rm
HCN}(J=1-0)$ as it is probably the best studied CND map (cite: Hsieh2021).

The total ${\rm
HCN}(J=1-0)$ integrated flux density of the CND is 3700 Jy km s$^{-1}$(Figure [2](#fig:CNDwhole)). The fraction of ${\rm
HCN}(J=1-0)$ emission captured within the white contours in Figures [1](#fig:CNDreg)-[2](#fig:CNDwhole) is about 350$\pm$35 Jy km s$^{-1}$, i.e., 9.7%, implying that H$_2$ mass in this region is $2.9\pm1.4\times10^3~M_\odot$. So this gives the value of the CO-to-H$_{2}$ conversion factor at $$\begin{eqnarray*}

\alpha_{\rm{CO}}\big|_\mathrm{by \, HCN \, fraction }&\simeq& 4.7\pm2.6 \, M_\odot (\mathrm{K \, km \, s^{-1} \, pc^2})^{-1}.
\end{eqnarray*}$$ We see that calculations of the $\alpha_{\rm{CO}}$ conversion factor by the captured area or by the fraction of the ${\rm
HCN}(J=1-0)$ emission of the CND give nearly the same result.

# Foreground Absorption

Line-of-sight absorption towards the Galactic Center has a potential to effect the calculations of the of $\alpha$\[CO\] and X\[CO\]. The absorption is significant at velocities of -150 to -30 km s$^{-1}$ for the southern lobe of the CND, and 80 to 150 km s$^{-1}$ for the northern lobe of the CND, as a result of the presence of the Galactic spiral arms and other foreground (cite: Christopher2005; Requena-Torres2012).

To estimate the absorption, we use the radiative transfer code RADEX (cite: vanderTak2007) to estimate the expected brightness temperature of the CND, $T_0$, from its known average properties. The CND has an average temperature of 100 K, CO column density of 10$^{18}$ ${\rm
cm}^{-2}$, H$_{2}$ density of 10$^5$ ${\rm
cm}^{-3}$, and line width of 15 km s$^{-1}$ (cite: Hsieh2021; Requena-Torres2012), resulting in an estimated average ${T_0}=$700 K km s$^{-1}$. The observed integrated intensity (Figure [1](#fig:CNDreg)) in radio units is 695K km s$^{-1}$.

For the foreground, we assume there are six absorption features from the spiral arms and other orbits crossing the line-of-sight toward the Galactic center, with an average brightness temperature of $T_\mathrm{foreground} = 29$ K km s$^{-1}$. For RADEX, we assume an average H$_{2}$ density of 10$^3$ ${\rm
cm}^{-3}$, velocity widths of $\sim$20 km s$^{-1}$, temperatures of 10 K, and column CO densities 10$^{17}$ ${\rm
cm}^{-2}$ per feature, resulting in the total column density of $6\times10^{17}{{\rm cm}^{-2}}$ (cite: Bieging1980; Binney1991; Liszt1978; Scoville1972; Oort1977; Menon1970).

To estimate the absorption, we use the radiative transfer formula $$\begin{eqnarray*}
    \rm{T_{obs}= T_{foreground}(1-e^{-\tau}) + T_0(e^{-\tau})}.
\end{eqnarray*}$$ Here $\rm{T_{obs}}$ is the observed integrated intensity, $\rm{T_{foreground}}$ is the foreground integrated intensity, $\rm{T_0}$ is the integrated intensity of the CND, and $\tau$ is the optical depth of the foreground obscuring material.

We obtain $\tau\simeq0.007$ and the foreground absorption of just $\lesssim1\%.$ This is not surprising, as the most significant absorption affects -135, -50, and -30 km s$^{-1}$ features of the blue shifted lobe of the CND (cite: Christopher2005; Requena-Torres2012), and by selecting a sub-region near the middle of the CND, we avoid the most significant effects.

# Summary

We have provided the first estimate of the CO–to–H$_{2}$ conversion factor in the 1 pc scale nuclear region of the Milky Way. We calculated the $\alpha_{\rm{CO}}$ value in two ways, which produced close values. We report the average as the final result: $$\begin{eqnarray*}
\alpha_{\rm{CO}}&\simeq& 4.5\pm2.5 \, M_\odot (\mathrm{K \, km \, s^{-1} \, pc^2})^{-1}, 
\end{eqnarray*}$$ which is equivalent to $$\begin{eqnarray*}

\mathrm{X[CO]}^{} &\simeq& 2.1\pm1.1\times 10^{20} \, \mathrm{cm}^{-2} (\mathrm{K \, km \, s^{-1}})^{-1}.
\end{eqnarray*}$$

The value of the CO–to–H$_{2}$ conversion factor in the inner $\sim 1$ pc of the black hole Sgr A$^*$  found is to be slightly higher but consistent within the uncertainties with that found for the disk of the Milky Way $\alpha_{\rm{CO}} \big|_{\mathrm{MW\,disk}}=4.3\pm1.3$ M$_{\odot}$(K km s$^{-1}$ pc$^{2}$)$^{-1}.$ However, it is higher than what is known of the larger central molecular zone $\alpha_{\rm{CO}} \big|_{\mathrm{MW \,CMZ}}=1.0\pm0.3~M_\odot (\mathrm{K \, km \, s^{-1} \, pc^2})^{-1}$ (cite: Kohno2024). This suggests that the CND may not inherit the properties of the larger CMZ. The amount of molecular gas is, of course, expected to greatly decrease closer to the black hole. The uncertainties are large due to the wide variations in the estimated mass of the molecular gas in the Galactic Center’s CND, on which we rely in our calculations. However, it is also possible, if the optical depth of the circumnuclear disk (CND) for the $^{12}{\rm
CO}(J=2-1)$/$^{12}{\rm
CO}(J=1-0)$  emission is on the order of a few, then the observed $^{12}{\rm
CO}(J=2-1)$/$^{12}{\rm
CO}(J=1-0)$ emission originates primarily from the surface of the CND rather than probing its full depth. This would lead to an overestimation of the CO–to–H$_{2}$ conversion factor by a similar factor as the optical depth.

We are grateful to Claire J. Chandler for advice on data processing, and to Ivan Marti-Vidal, Anna Ciurlo, Mark Morris, Shoko Sakai, Tuan Do, Roger Blandford, Nick Scoville, Rick Perley, and Elizabeth Mills for comments and discussions, and to Jurgen Ott, Jin Koda, Eliot Quataert, and Sean Ressler for contribution to writing ALMA proposals, and to the anonymous referee for their helpful comments.

M.D.G. is supported by the CIERA Postdoctoral Fellowship from the Center for Interdisciplinary Exploration and Research in Astrophysics at Northwestern University.

This paper makes use of the following ALMA data: ADS/JAO.ALMA #2016.1.00870.S, #2017.1.00995.S, #2017.1.00040.S, and #2019.1.01559.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This work used computing resources provided by Northwestern University and the Center for Interdisciplinary Exploration and Research in Astrophysics (CIERA). This research was supported in part through the computational resources and staff contributions provided for the Quest high performance computing facility at Northwestern University which is jointly supported by the Office of the Provost, the Office for Research, and Northwestern University Information Technology.

# Facilities

ALMA

# Software

astropy (cite: Astropy2013; Astropy2018; Astropy2022), UVmultifit (cite: marti-vidal2014), CASA (cite: CASATeam2022PASP)

natexlab

(ref: Astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Astropy2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Bieging1980) Bieging, J., Downes, D., Wilson, T. L., Martin, A. H. M., & Guesten, R. 1980, A&AS, 42, 163

(ref: Binney1991) Binney, J., Gerhard, O. E., Stark, A. A., Bally, J., & Uchida, K. I. 1991, MNRAS, 252, 210, doi: [`10.1093/mnras/252.2.210`](http://doi.org/10.1093/mnras/252.2.210)

(ref: Bolatto2013b) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: CASATeam2022PASP) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacifc, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Christopher2005) Christopher, M. H., Scoville, N. Z., Stolovy, S. R., & Yun, M. S. 2005, ApJ, 622, 346, doi: [`10.1086/427911`](http://doi.org/10.1086/427911)

(ref: Etxaluze2011) Etxaluze, M., Smith, H. A., Tolls, V., Stark, A. A., & González-Alfonso, E. 2011, AJ, 142, 134, doi: [`10.1088/0004-6256/142/4/134`](http://doi.org/10.1088/0004-6256/142/4/134)

(ref: Hsieh2018) Hsieh, P.-Y., Koch, P. M., Kim, W.-T., et al. 2018, The Astrophysical Journal, 862, 150, doi: [`10.3847/1538-4357/aacb27`](http://doi.org/10.3847/1538-4357/aacb27)

(ref: Hsieh2021) Hsieh, P.-Y., Koch, P. M., Kim, W.-T., et al. 2021, ApJ, 913, 94, doi: [`10.3847/1538-4357/abf4cd`](http://doi.org/10.3847/1538-4357/abf4cd)

(ref: James2021) James, T. A., Viti, S., Yusef-Zadeh, F., Royster, M., & Wardle, M. 2021, ApJ, 916, 69, doi: [`10.3847/1538-4357/abfd99`](http://doi.org/10.3847/1538-4357/abfd99)

(ref: Kohno2024) Kohno, M., & Sofue, Y. 2024, PASJ, 76, 579, doi: [`10.1093/pasj/psae033`](http://doi.org/10.1093/pasj/psae033)

(ref: Lau2013) Lau, R. M., Herter, T. L., Morris, M. R., Becklin, E. E., & Adams, J. D. 2013, ApJ, 775, 37, doi: [`10.1088/0004-637X/775/1/37`](http://doi.org/10.1088/0004-637X/775/1/37)

(ref: Liszt1978) Liszt, H. S., & Burton, W. B. 1978, ApJ, 226, 790, doi: [`10.1086/156660`](http://doi.org/10.1086/156660)

(ref: Liu2013) Liu, H. B., Ho, P. T. P., Wright, M. C. H., et al. 2013, ApJ, 770, 44, doi: [`10.1088/0004-637X/770/1/44`](http://doi.org/10.1088/0004-637X/770/1/44)

(ref: Marshall1994) Marshall, J., & Lasenby, A. N. 1994, MNRAS, 269, 619, doi: [`10.1093/mnras/269.3.619`](http://doi.org/10.1093/mnras/269.3.619)

(ref: marti-vidal2014) Martí-Vidal, I., Vlemmings, W. H. T., Muller, S., & Casey, S. 2014, A&A, 563, A136, doi: [`10.1051/0004-6361/201322633`](http://doi.org/10.1051/0004-6361/201322633)

(ref: Menon1970) Menon, T. K., & Ciotti, J. E. 1970, Nature, 227, 579, doi: [`10.1038/227579a0`](http://doi.org/10.1038/227579a0)

(ref: Murchikova2021) Murchikova, L., & Witzel, G. 2021, ApJL, 920, L7, doi: [`10.3847/2041-8213/ac2308`](http://doi.org/10.3847/2041-8213/ac2308)

(ref: Oka1998) Oka, T., Hasegawa, T., Sato, F., Tsuboi, M., & Miyazaki, A. 1998, ApJS, 118, 455, doi: [`10.1086/313138`](http://doi.org/10.1086/313138)

(ref: Oka2011) Oka, T., Nagai, M., Kamegai, K., & Tanaka, K. 2011, ApJ, 732, 120, doi: [`10.1088/0004-637X/732/2/120`](http://doi.org/10.1088/0004-637X/732/2/120)

(ref: Oort1977) Oort, J. H. 1977, ARA&A, 15, 295, doi: [`10.1146/annurev.aa.15.090177.001455`](http://doi.org/10.1146/annurev.aa.15.090177.001455)

(ref: Requena-Torres2012) Requena-Torres, M. A., Güsten, R., Weiß, A., et al. 2012, A&A, 542, L21, doi: [`10.1051/0004-6361/201219068`](http://doi.org/10.1051/0004-6361/201219068)

(ref: Sandstrom2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5, doi: [`10.1088/0004-637X/777/1/5`](http://doi.org/10.1088/0004-637X/777/1/5)

(ref: Scoville1972) Scoville, N. Z. 1972, ApJL, 175, L127, doi: [`10.1086/181000`](http://doi.org/10.1086/181000)

(ref: Tokuyama2019) Tokuyama, S., Oka, T., Takekawa, S., et al. 2019, PASJ, 71, S19, doi: [`10.1093/pasj/psy150`](http://doi.org/10.1093/pasj/psy150)

(ref: Tsuboi2018) Tsuboi, M., Kitamura, Y., Uehara, K., et al. 2018, PASJ, 70, 85, doi: [`10.1093/pasj/psy080`](http://doi.org/10.1093/pasj/psy080)

(ref: vanderTak2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

</paper>

Write the methods card for this paper.