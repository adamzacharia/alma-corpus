# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...904..125S\sonnetcc\reply.txt

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
 "bibcode": "2020ApJ...904..125S",
 "title": "Spiral-arm Substructures in the Asymmetrical Dust Rings of the Circumstellar Disk MWC 758",
 "year": 2020,
 "journal": "The Astrophysical Journal",
 "first_author": "Shen, Bo-Ting",
 "n_authors": 3,
 "arxiv_id": "2010.05488",
 "doi": "10.3847/1538-4357/abbd9f",
 "alma_projects_linked_by_archive": [
  "2012.1.00725.S"
 ]
}
```

Paper text:
<paper>
# Spiral-Arm Sub-Structures in the Asymmetrical Dust Rings of the Circumstellar Disk MWC 758

## Abstract

Asymmetrical features in disks provide indirect evidences of embedded objects, such as planets.

Observed with the Atacama Large Millimeter/submillimeter Array (ALMA), the circumstellar disk in MWC 758 traced with thermal dust continuum emission at wavelengths of 0.9 mm with an angular resolution up to 0.1$''$ (15 au) exhibits an asymmetrical dust ring with additional features.

In order to analyze the structures azimuthally and radially, we split the dust ring into small segments in azimuth. For each segment, we fit two-Gaussian functions to the radial intensity profile. The obtained best-fit parameters as a function of azimuth are analyzed.

Three spiral-like arm structures are identified.

When fitting the 0.9 mm features with the spiral density wave theory using the WKB approximation, two sets of disk aspect ratios are found: one solution gives relatively low values ($\sim$0.03) while the other solution is at the upper bound of the free parameter ($\sim$0.2). The planet locations suggested by the upper-bound result are similar to the ones determined by (cite: 2015Benisty) for the NIR polarized intensity image.

Comparing the reported spiral-like structures with the higher angular-resolution (0.04$''$) ALMA image in (cite: 2018Dong), we identify different structures in the West of the disk due to differences in the adopted analysis methods and the respective resolutions of the images.

# Introduction

Observationally, several asymmetrical features have recently been found in protoplanetary disks. The unprecedented sensitivity and angular resolution achieved by ALMA observations have allowed us to study the sub-structures of protoplanetary disks in detail. The ALMA large program Disk Substructures at High Angular Resolution ($\sim$0.04$''$) Project (cite: 2018Andrews) reveals 20 protoplanetary disks at 240 GHz (wavelengths around 1.3 mm) with disk morphologies showing a wide variety of structures, such as concentric rings and gaps, arcs, and spirals. (cite: 2018Long) report half of a survey of 32 disks in the Taurus molecular cloud at 1.33 mm wavelengths with an angular resolution of 0.12$''$ and find that all the gaps in disks could be explained by low-mass planets in low-viscosity disks. Around HD135344B, where a ring and an arc are detected at 0.9 mm wavelengths with 0.16$''$ resolution, two planets at different locations are a possible scenario to form the vortices and the features seen in the scattered light image (cite: 2016vanderMarel). With the gap locations and widths, the mass of the planets can be estimated (cite: 2015Kanagawa). In the V1247 Orionis system an asymmetrical ring and a crescent structure are detected in the continuum image obtained by ALMA with a 0.04$''$ resolution at 0.9 mm wavelengths (cite: 2017Kraus), and based on hydrodynamics simulations a planet at 100 au is suggested to produce the gap and trigger two vortices, the crescent and the asymmetry in the ring (cite: 2017Kraus). Additionally, several systems with spirals are revealed by ALMA in both continuum at submm wavelengths in, for example, HD 135344 (cite: 2016vanderMarel), and also in CO line emission in AB Aurigae (cite: 2017Tang) and HD 142527 (cite: 2014Christiaens).

Theoretically, embedded planets are expected to perturb disks through gravitational interaction and produce asymmetrical structures such as vortices, spirals, and gaps (cite: 2014Zhu).

Such observed structures can constrain the physical quantities of an embedded planet, such as its mass and its location. A spiral feature can be explained by the density wave excited by an embedded object (cite: 1964Lin&Shu; 2002Ogilvie). This method was used in the disks of SAO 206462 (cite: 2012Muto), V1247 Orionis (cite: 2017Kraus) and MWC 758 (cite: 2015Benisty) to explain their spiral features.

These asymmetrical structures provide the indirect evidences for the embedded objects, and therefore, they are the keys to understand where and when planets are formed.

MWC 758 is a Herbig A5 star (cite: 2001Thi) located at a distance of 151$^{+9}_{-8}$ pc (cite: 2018GAIA).

The inclination of its disk is 21$\ensuremath{^\circ} \pm$2$\ensuremath{^\circ}$ with a position angle of the major axis of 65$\ensuremath{^\circ} \pm$7$\ensuremath{^\circ}$ east from north (cite: 2010Isella). The mass of the central star is estimated to be 1.4$\pm$0.3 $M_\odot$. The disk mass is around 0.01 $M_\odot$ (cite: 2011Andrews).

The asymmetrical features of the MWC 758 disk have been detected in several wavelegnths. At submm, an asymmetrical emission located $\sim$70 au northwest from the central star is found after subtracting a symmetrical model (cite: 2010Isella). At near-infrared (NIR), two spiral features are reported both by (cite: 2013Grady) and (cite: 2015Benisty). Using the peak intensity image of the molecular emission $^{13}$CO 3-2, (cite: 2018Boehler) report a spiral structure, which is associated with one of the spirals seen at NIR. A point-like structure and a third spiral are reported for the first time at L’ band (3.8 $\mu$m wavelengths) by (cite: 2018Reggiani) using the vector vortex coronagraph at the Keck II telescope. (cite: 2019Casassus) resolved a dust trapping vortex at the northern clump with VLA (33 GHz) observations.

Based on much higher angular resolution ($0.04\ensuremath{''}$) 0.9 mm-wavelength ALMA data, (cite: 2018Dong) reported an eccentric cavity, triple rings, one spiral arm, and double clumps in the MWC 758 disk. A model with two giant planets can produce the dust trapping vortices in the mm wavelengths detected with ALMA and the VLA, together with the spirals in the NIR scattered-light image based on gas and dust hydrodynamical simulations (cite: 2019Baruteau).

Here, we report a detailed analysis on the dust emission at wavelengths of 0.9 mm with an angular resolution up to 0.1$''$ observed with ALMA toward the MWC 758 disk. We analyze the 0.9 mm continuum emission as a function of azimuth and characterize the features accordingly. In section [2](#sec:obs), we outline the observations and imaging parameters. Our analysis is described in section [3](#sec:ana). We discuss and compare our results with the results in the literature in section [4](#sec:dis). In section [5](#sec:con), we summarize our findings.

| Parameter | Value | Reference |
|:---|:--:|:--:|
| Right Ascension | 05:30:27.53 | \(1\) |
| Declination | +25:19:56.67 | \(1\) |
| Distance | 151$^{+9}_{-8}$ pc | \(2\) |
| Stellar mass | 1.4$\pm$0.3 $M_{\odot}$ | \(3\) |
| Disk inclination | 21$\ensuremath{^\circ} \pm$2$\ensuremath{^\circ}$ | \(4\) |
| Disk-plane position angle | 65$\ensuremath{^\circ} \pm$7$\ensuremath{^\circ}$ | \(4\) |
| Disk mass | 0.01 $M_{\odot}$ | \(5\) |

: Main parameters of MWC 758

Table notes: Reference: (1) SIMBAD, (2) GAIA (cite: 2016Gaia1; 2016Gaia2), (3) (cite: 2018Boehler), (4) (cite: 2010Isella), (5) (cite: 2011Andrews).

# Observations and Imaging

The reported observations were carried out with ALMA in Cycle 2, band 7 (project "2012.1.00725.S") on Sep. 1 and Sep. 24, 2015, with an on-source integration time of 29 and 24 mins, respectively. The array included 44 12-m antennas with baselines ranging from 15.1 m to 1.5 km. The bandpass calibrators were J0610+1800 and J0423-0120. J0510+1800 was used as a flux calibrator, and J0521+2112 and J0510+1800 were adopted as gain calibrators. The calibration was done using pipeline. After standard calibration, we additionally applied self-calibration to the measurements in order to improve the images.

The phase center of MWC 758 was at ($\alpha$, $\delta$)= (05:30:27.53, +25:19:56.67).

![image](cont_rob.pdf) ![image](cont_su.pdf) ![image](cont_su_nir.pdf)

The continuum emission is well detected and resolved. In the following, we present images produced with both robust and super-uniform[^1] (SU) weighting of visibilities. The resulting angular resolutions of these continuum images are 0.19$''$$\times$0.17$''$ with a position angle of 37.73$\ensuremath{^\circ}$ and 0.13$''$$\times$0.11$''$ with a position angle of 35.02$\ensuremath{^\circ}$ for robust and SU weighting. The corresponding sensitivities (noise levels) are 92 $\mu$Jy beam$^{-1}$ and 0.4 mJy beam$^{-1}$ for the images with robust and SU weighting, respectively.

Figure [1](#fig:cont)a shows the image with robust weighting. The total flux is 240 mJy.

The brightest emission is located in the northwest with an intensity of 23.8 mJy beam$^{-1}$ (18.8 K) and with a signal-to-noise (SN) ratio of 259.

The second brightest emission with 18.1 mJy beam$^{-1}$ (15.8 K) and an SN of 197 is located southwest, forming an extended arc from west to east, extending clockwise to almost north. Between this arc and the brightest emission are two fainter regions.

Figure [1](#fig:cont)b displays the MWC 758 continuum map with SU weighting. Here, the brightest emission is 13.6 mJy beam$^{-1}$ (21.5 K) with an SN of 34, located northwest with a stretched structure extending over a range in azimuth of $\sim$ 90$\ensuremath{^\circ}$.

The second brightest emission is 12.6 mJy beam$^{-1}$ (20.4 K) with an SN of 32, located again southwest with an arc that extends $\sim$180$\ensuremath{^\circ}$ from south to north counterclockwise, connecting to the inner edge of the brightest emission. Unlike the robust-weighted image, this map reveals a minimum in intensity in the south at a position angle around 150$\ensuremath{^\circ}$. This minimum separates a new arc (extending clockwise) that remained connected in the robust-weighted image (see section [\[sec:three_features\]](#sec:three_features) for the identification of these features).

As a result, the image with SU weighting more clearly reveals the structures in the southeast and enhances the variation between the stretched structure at the brightest emission and the southwestern arc with a clear separation.

![](Ellipse_Robust.jpg)

# Analysis

## Large-Scale Continuum Disk Geometry?

The detected dust emission exhibits large variations both radially and azimuthally. We first use the image with robust weighting to probe the large-scale (about 100 au) disk geometry in continuum. With this we are introducing our analysis method (which we will refine in the later section [\[sec:three_features\]](#sec:three_features)) while at the same time probing whether the relatively coarse resolution of 0.18$''$ can possibly still be used in our approach to consistently derive the known large-scale disk geometry (cite: 2010Isella). Our analysis approach is as follows.

With a resolution of 0.18$''$ – which corresponds to 25$\ensuremath{^\circ}$ in azimuth at a radius of 0.4$''$ – we split the continuum emission in segments of 10$\ensuremath{^\circ}$ in azimuth to have a sufficient sampling rate. This will result in 36 segments.

We note that we have compared this analysis for different numbers of segments, and the results are consistent (within the uncertainties) with the ones presented in the following. The profile of intensity versus radius for each segment can be fit with one Gaussian function. Appendix [6](#app:G1) shows the result of the fittings. We use the amplitude and its position from this Gaussian fit to represent the intensity and the peak location of each segment.

Subsequently, an ellipse is fit to the peak locations, which allows us to determine the disk geometry assuming that the disk is circular.

We find that the center of the fitted ellipse is shifted by 0.002$''$ $''$$in right ascension and by$0.071$''$ $''$$in declination with respect to the stellar location. 
Figure \ref{fig:cont-inclined-ellipse} presents the result.
The derived inclination is 36.0$ $^\circ$$and the P.A. is 150.5$ $^\circ$$. 
However, the inclination angle and the major axis derived from the gas kinematics are 21$$^\circ$$and 65$$^\circ$$, respectively (cite: 2010Isella).

Hence, 
we conclude that, using our approach of a single-Gaussian fit to identify a single radial maximum in each azimuth segment,
the inclination and the P.A. calculated from the inclined dust ellipse clearly deviate from the known gas disk geometry. This suggests that 

the continuum emission observed at 0.9 mm is not tracing a circular structure.
This conclusion is not surprising as it confirms the earlier results in (cite: 2018Boehler) and (cite: 2018Dong) which demonstrated that the two brightest mm continuum structures are located at different radii, and therefore, they cannot be used to infer the large-scale disk geometry.

\begin{figure*}[htpb!]
\centering
\includegraphics[width=\textwidth,trim={0 6cm 0 0},clip]{Fig3.pdf}
\caption{(a): Continuum emission at 0.9 mm wavelengths with SU-weighting after correcting for inclination (i.e. de-projecting) in color scale.
The peak positions (black squares and red dots) and the best-fit uncertainties ($\pm$2$\sigma$) marked in segments are determined by the two-Gaussian fits to the profiles of intensity versus radius in each segment. 
Grey circles mark the radii at 0.2\ensuremath{''}, 0.4\ensuremath{''}, 0.6\ensuremath{''}, and 0.8\ensuremath{''}. Azimuth angles in units of degree are labelled at the 0.8\ensuremath{''} radius.
(b): identical to panel (a) without the de-projected image of the 0.9 mm continuum emission. 
(c): identical to panel (a) with the three structural features (arm 1, arm 2, and arm 3) marked as white arcs.
(d, e, f): three parameters (amplitude in panel (d), position in panel (e) and FWHM in panel (f)) from the two-Gaussian fits as a function of azimuth.  
In panel b,d,e,f, the symbol sizes are weighted with the intensity (larger symbols denote data with higher intensity) in 4 intensity groups, being $<$2, 2 to 4, 4 to 6 and $>$6 mJy beam$^{-1}$.
The red, green, and blue segments mark the extensions in azimuth of arm 1, arm 2, and arm 3, respectively.
In all panels, the positions of the inner and outer Gaussians are marked with red dots and black squares, respectively. 
For a better display of the continuity of structures, the azimuth range is extended and repeated beyond 360$\ensuremath{^\circ}$.
}\label{fig:gauss2}
\end{figure*}

\subsection{Three Structural Continuum Features}\label{sec:three_features}
We further analyze the SU-weighted continuum image with a focus on extracting key structural features which show a radial dependence as a function of azimuth (e.g., clockwise / counter-clockwise spirals, eccentric features, elliptical rings) in the MWC 758 disk. While focused on radial dependence along azimuth, our approach will equally well capture any structure symmetric in azimuth.
We first de-project the continuum image with the major axis of the disk-plane of 62$$^\circ$$, which is consistent with the value used in (cite: 2018Boehler), and the inclination of 21$$^\circ$$, and we apply the analysis method described in the above section \ref{sec:geometry}. 
With the SU-weighted higher angular resolution (0.12\ensuremath{''}), we split the continuum emission into 72 segments where every segment is 5$$^\circ$$in azimuth.
Unlike the robust-weighted image, 

the radial profiles of the segments in the de-projected SU-weighted image are better described by two-Gaussian functions, one 

inner and one outer Gaussian (see figure \ref{fig:cont-profile-super},\ref{fig:cont-profile-270},\ref{fig:az120to180} in appendix \ref{app:G2}).

Although most segments are well described by two Gaussians, the uncertainties in their positions and/or amplitudes are relatively larger in a few locations, as shown in figure \ref{fig:gauss2}.
The results of all these Gaussian-fit parameters are plotted in figure \ref{fig:gauss2}d,e,f with$$2$$error bars covering the 95\% confidence level.

Around the northern clump (azimuth 325$$^\circ$$- 365$$^\circ$$), the error bars of the positions of the inner Gaussians are larger.
Here, the profiles exhibit a Gaussian-like function with a tail toward smaller radii without a clear additional peak (figure \ref{fig:cont-profile-super}). 
This also results in larger uncertainties in position and width for the inner Gaussian.
With larger uncertainties for the widths of the inner Gaussians, the uncertainties of the amplitudes of the outer Gaussians also become larger.
The profiles at azimuth 210$$^\circ$$- 220$$^\circ$$and for some segments between 55$$^\circ$$- 100$$^\circ$$also have larger uncertainties in the positions and widths of the outer Gaussians and in the amplitude of the inner Gaussians. 
This is due to the insignificance of the second peaks. 

For the following analysis, we use the amplitudes and the positions of the two Gaussians to represent the intensities and the peak positions in each segment.
These best-fit positions are overlaid on the continuum image in figure \ref{fig:gauss2}a. 
It is apparent from panel \ref{fig:gauss2}b that
these peak positions move in radius as a function of azimuth. Based on this, 
three key structural continuum features (arm 1, 2, 3; panel \ref{fig:gauss2}c)
are identified. They are described and characterized by several criteria in the following paragraphs. 
We note that the identification of the structural features as detailed out in the following is not based on weak or marginal features in low SN data, but it remains robust for a high threshold of$10$for the regions where the uncertainties of the best-fit are relatively large.

{\it Brightness and Radial Trends.} There are three bright components above 10$$($1\~$0.4 mJy beam$\^-1$) in the amplitude panel \ref{fig:gauss2}d.
The first component corresponds to the brightest emission located in the northwest, identified by outer Gaussians around azimuth$\~330$^\circ$$.
The second component is matched by the second brightest emission located in the southwest, found from inner Gaussians around azimuth$\~220$^\circ$$.
The third component is in the southeast, extending over a range of 70$$^\circ$$to 210$$^\circ$$in azimuth, identified together from both inner and outer Gaussians.
We note that its tail drops to about$6$in the end.

Investigating further 
this third component with the help of the position panel \ref{fig:gauss2}e, it appears that the inner Gaussian is moving outward until about 130$$^\circ$$in azimuth, and 
close to this location around 140$$^\circ$$, 
the outer Gaussian seems to connect and pick up this trend, moving further outward in radius.

Both inner and outer Gaussian show a similar trend in how their positions move with azimuth, while at the same time they occur where their amplitudes increase (before dropping again) and emission gets brighter.
Consequently, we argue that the inner and outer Gaussian are connecting here
between 130$$^\circ$$and 140$$^\circ$$.
Figure \ref{fig:az120to180} shows the radial plots from azimuth 120$$^\circ$$to 180$$^\circ$$.

{\it Delineation of Features.} In order to identify the starting and ending of a feature, we compare positions and amplitudes (figure \ref{fig:gauss2}d,e).
The identified features are labeled in figure \ref{fig:gauss2}c.

For the first feature (arm 3), the brightest emission is associated with a stretched structure located in the northwest from 250$$^\circ$$to 365$$^\circ$$in azimuth at radii larger than 0.5\ensuremath{''}.

The starting point is around 250$$^\circ$$, where the outer Gaussian shows a local minimum in its amplitude (panel \ref{fig:gauss2}d) while at the same time also being
at the smallest radius locally (panel \ref{fig:gauss2}e). 
The ending point is around 365$$^\circ$$in the north, where the radius has moved to a 
maximum outer location, and the amplitude has dropped again to a local minimum. 
Beyond 365$$^\circ$$counterclockwise, the locations of the outer Gaussians show 
a different trend with their radii decreasing again as a function of azimuth.

This first structural continuum feature is characterized by its peak positions 
moving outward from about 0.45\ensuremath{''} to 0.60\ensuremath{''} over a range in azimuth of 115$$^\circ$$with a pitch angle of about 7$$^\circ$$. 

The second feature (arm 2) is an arc in the northwest, located between about 250$$^\circ$$and 365$$^\circ$$in azimuth at inner radii.
As the second brightest emission peak does not show any dependence along azimuth in
its locations of Gaussians, it is not included in this second feature.

The starting point is around 250$$^\circ$$in the West, which is at the edge of the symmetric profile (figure \ref{fig:gauss2}c) of the second brightest emission. 
The ending point is around 365$$^\circ$$, where -- identical to the above first structural feature -- the position of the Gaussian has moved to a maximum radius. 
Over a range of 115$$^\circ$$in azimuth, the peak positions move outward from 0.3\ensuremath{''} to 0.4\ensuremath{''} with a pitch angle of$\~$9$$^\circ$$. 

The third feature (arm 1) is an arc in the southeast,

from about 70$$^\circ$$to 130$$^\circ$$in azimuth along the peaks of the inner Gaussians, and subsequently connecting to the outer Gaussians from about 140$$^\circ$$to 210$$^\circ$$. 
Here, the starting point is around 70$$^\circ$$, where the intensities are above$10$and then continuously grow.
Following with the brighter emission and comparing with the position panel, the third feature moves from the inner Gaussian (at 130$$^\circ$$) to the outer Gaussian (at 140$$^\circ$$). 
The ending point is the local minimum at 210$$^\circ$$. 
Along this third structural feature, the inner and then the outer Gaussian peak positions move outward from about 0.34\ensuremath{''} to 0.49\ensuremath{''} over a range of$\~140$^\circ$$in azimuth with a pitch angle of$\~$10$$^\circ$$.

\begin{figure*}[ht!]
\includegraphics[width=0.99\textwidth]{Fig4.jpeg}
\caption{
Panels a and b are identical to the panels \ref{fig:gauss2}d and e, superimposed with two black boxes that localize the two spiral regions. 
The southeastern spiral (arm 1) is from about 70$\ensuremath{^\circ}$ to 210$\ensuremath{^\circ}$ in azimuth.
Arm 2 stretches from about 250$\ensuremath{^\circ}$ to 365$\ensuremath{^\circ}$. 
Blue circles mark the section in arm 1 which is identified from inner Gaussians.
Green squares are the subsequent section identified from outer Gaussians.
Connecting the blue circles and the green squares forms the arm 1. 
Panels c and d show the aligned amplitudes and positions after a shift of 160$\ensuremath{^\circ}$ in azimuth, i.e., aligning the black boxes in the upper panels.
The shifts in amplitude and position are 0.6 mJy beam$^{-1}$ and 0.04\ensuremath{''}, respectively.
The black and red axes are for arm 1 and arm 2, respectively.
After shifting, aligning and overlaying arm 1 and arm2, it is illustrated that these two have similar patterns.
}\label{fig:overlay}
\end{figure*}

{\it Similar Spiral Patterns.} It is striking that two structural features identified above -- arm 1 and arm 2 in figure \ref{fig:gauss2}c -- display similar patterns in amplitude and position which resemble spiral-like patterns. 
Although arm 3 has also a similar pattern in position to arm 1 and arm 2, it has a much higher amplitude and thus, here we do not compare it further to the other two arms.
The amplitude profile of arm 3 is most likely composed of a dust trapping vortex and a spiral, which gives the radial dependence feature.
The common spiral nature in all three arms is further explored in section \ref{sec:model_spiral}.

Figure \ref{fig:overlay} illustrates the similar pattern seen in arm 1 and arm 2 further.
The black boxes in the upper panels localize the two spiral regions in amplitude and position.
They are separated by about 160$$^\circ$$in azimuth. 
In order to further demonstrate their similarities, 
we shift, align, and overlay the black boxes to further check the patterns of these two spiral arms.  
In figure \ref{fig:overlay}c, both spiral features display a gradual decrease in intensity with a small bump.

The position panel shown in figure \ref{fig:overlay}d makes manifest that the two spiral arms are moving outward with a very similar pitch angle, i.e. after aligning there is a common shift in radial position of about 0.1\ensuremath{''} and 0.15\ensuremath{''} over a range in azimuth angle of about 100$$^\circ$$.

\subsection{Gravitational Stability and Turbulence}
\label{sec:stability}
We investigate the gravitational stability of the MWC 758 disk using the Toomre Q parameter (Toomre 1964): 

\begin{equation}
Q = \frac{c_{s} \Omega}{\pi {\rm G} \Sigma},
\end{equation}
where$c\_s$is the sound speed,$$is the orbital frequency, G is the gravitational constant, and$$is the disk surface density. 
For the brightest and the second brightest emission in the SU-weighted continuum image, the brightness temperatures are 21.5 K and 20.4 K, respectively. 
With gas temperatures of 34 K and 78 K (cite: 2018Boehler), the optical depths are estimated to be 0.54 and 0.19 at the locations of the brightest and second brightest emission. 
Their surface densities are 0.198 g cm$\^-2$and 0.070 g cm$\^-2$,

assuming a dust opacity of 2.74 cm$\^2$g$\^-1$(cite: 1994Ossenkopf).
The sound speed is$\~$0.5 km s$\^-1$and the orbital frequency is$\~$10$\^-11$s$\^-1$.
The resulting Toomre Q parameters, considering only the dust component at the two locations of the brightest emission, are 232 and 2612, respectively. 
Adopting a gas-to-dust ratio of 100, the values for Q are reduced to 2 and 26.

We remark that gas-to-dust ratios in protoplanetary disks can vary significantly. 
For a similar system, such as HD142527, the gas-to-dust ratios at the locations of peak emission are$\~$3 in the northern clump and$\~$30 in the southern clump, where the overall ratios range from$\~$10 to$\~$30 (cite: 2015Muto).
The gas-to-dust ratio for MWC 758 is reported to be about 10 for the brightest emission in (cite: 2018Boehler).

Given these gas-to-dust ratios of the order of 10, values for Q at the two brightest emission locations remain larger than 1, suggesting that these two locations are gravitationally stable. 

The level of turbulence at the locations of the two brightest emission peaks is tested by comparing their linewidths of$\^13$CO with their sound speeds.

The linewidths at the southwestern and northwestern peak are 0.5 and 0.4 km s$\^-1$, respectively. 
The corresponding sound speeds are 0.5 and 0.3 km s$\^-1$, respectively.
Consequently, there appears to be no significant difference in the ratios of  linewidths and the sound speeds at these two positions.

\begin{figure*}[htpb!]
\centering
\includegraphics[width=0.49\textwidth]{Fig5a.jpg}
\includegraphics[width=0.49\textwidth]{Fig5b.jpg}\\
\includegraphics[width=0.49\textwidth]{Fig5c.jpg}
\includegraphics[width=0.49\textwidth]{Fig5d.jpg}\\
\includegraphics[width=0.49\textwidth]{Fig5e.jpg}
\includegraphics[width=0.49\textwidth]{Fig5f.jpg}
\caption{
Spiral wave fitting results for arm 3 (upper panels), arm 2 (middle panels) and arm 1 (bottom panels). 
In the left panels, the color scale is the deprojected continuum emission at 0.9 mm with SU weighting. 
The magenta dots indicate peak positions.
The cyan lines are the density waves launched by the predicted planet locations (diamonds) with a 95\% confidence level interval shown with the black arcs. 
The predicted planet positions are at
(r$_c$, $\theta$) = (0.45\ensuremath{''} \pm 0.04\ensuremath{''}$, 255$\ensuremath{^\circ} \pm 20\ensuremath{^\circ}$), (0.35\ensuremath{''} \pm 0.01\ensuremath{''}$, 311$\ensuremath{^\circ} \pm 12\ensuremath{^\circ}$) and (0.42\ensuremath{''} \pm 0.01\ensuremath{''}$, 154$\ensuremath{^\circ} \pm 10\ensuremath{^\circ}$) for arm 3, arm 2 and arm 1, respectively.
The disk aspect ratios ($h_c$) for the three spiral features are 0.03$ \pm $0.02 for arm 3, 0.018$ \pm $0.003 for arm 2, and 0.026$ \pm $0.003 for arm 1. 
The right panels show the spiral features (selected peak positions with uncertainties in magenta) with best-fit spiral models (cyan lines) in radius versus azimuth phase plots.
}\label{fig:spiral}
\end{figure*}

\subsection{Modeling of Spiral Features}
\label{sec:model_spiral}
Our analysis in the previous section suggests that the peak positions in all three spiral features move in radius as a function of azimuth.
Here, we adopt a spiral model to explain these features. 
This method was already used in the disks of SAO 206462 (cite: 2012Muto), V1247 Orionis (cite: 2017Kraus) and for the polarized intensity image of MWC 758 (cite: 2015Benisty) to discuss their observed spiral structures. 
The model is based on the spiral density wave theory, where a planet embedded in the disk launches spiral waves (cite: 1964Lin&Shu; 2002Ogilvie).
The model was first introduced by (cite: 2002Rafikov), using a WKB approximation. 
The resulting spiral pattern can be described with the following equation:

\begin{equation}
\begin{split}
\theta(r) & = \theta  _{0} \\
& + \frac{sgn(r-r_{c})}{h_{c}} (\frac{r}{r_{c}})^{1+\beta }[\frac{1}{1+\beta } -\frac{1}{1-\alpha +\beta}(\frac{r}{r_{c}})^{-\alpha}]\\
& -\frac{sgn(r-r_{c})}{h_{c}}(\frac{1}{1+\beta } -\frac{1}{1-\alpha +\beta}).
\end{split}
\end{equation}

This equation has five parameters.$r\_c$and$\_0$are the radius and the position angle of the launching point (i.e., the predicted planet location in polar coordinates).$$is related to the disk's rotation,$$(r)$$r$\^-$.$$is linked to the sound speed (i.e., temperature)$c_s$(r)$$r$\^-$.$h_c$is the disk aspect ratio, which is the ratio of the scale height (the ratio of the sound speed to the Keplerian angular speed) 
and$r_c$:$h\_c$=$$(cite: 2012Muto; 2015Benisty). 

We fix$$=1.5 (i.e., we assume that the disk is in Keplerian rotation) and$$=0.45 following (cite: 2011Andrews). 
The remaining three free parameters ($\_0, r_c, h_c$) are determined by a best-fit via a downhill simplex method to each of the three features identified in section \ref{sec:three_features} with the spiral wave model.

We find two sets of best-fit results which fit the data similarly well. Here, we show the first set which gives low$h_c$values.
Fig. \ref{fig:spiral} exhibits the result for the northwestern arm (arm 3; upper panel), the southwestern arm (arm 2; middle panel), and the southeastern arm (arm 1; bottom panel).

Diamonds indicate the predicted planet location with its uncertainties marked as black segments at
($r_c$,$\_0$) = (0.45\ensuremath{''} \pm 0.04\ensuremath{''}$, 255$\ensuremath{^\circ} \pm 20\ensuremath{^\circ}$), (0.35$''$ $''$$, 311$$^\circ$ $^\circ$$) and (0.42\ensuremath{''} \pm 0.01\ensuremath{''}$, 154$\ensuremath{^\circ} \pm 10\ensuremath{^\circ}$) for arm 3, arm 2, and arm 1, respectively. The disk aspect ratios ($h_c$) of the three features are 0.03$\pm$0.02 for arm 3, 0.018$\pm$0.003 for arm 2, and 0.026$\pm$0.003 for arm 1.

Observationally, $h_c$ is found to range from 0.05 to 0.25 using scatter light images of disks (cite: 2015Andrews).

A low value of $h_c$ indicates a colder disk, where it is more difficult to launch a spiral. Typical lower limits for $h_c$ are $\sim$0.01-0.03 (cite: 2012Muto). Our fitting results yield small values for h$_c$, approaching the lower limits to detect spirals in colder disks. Comparing this to an independent estimate – adopting the derived sound speed in section [\[sec:stability\]](#sec:stability) and a central mass of $1.4 M_{\ensuremath{\odot}}$ –

values for $h_c$ become larger with $\sim$0.07 to 0.09 across the MWC 758 disk. Hence, aspect ratios obtained from the spiral model fitting appear lower in this comparison.

One possible reason for this is that the spiral wave model is only suitable for the linear and weakly non-linear regime. However, taking into account the upper uncertainties of the parameters obtained for the best-fit spirals, an $h_c$ of $0.03+0.02$ is within the expected disk aspect ratio of 0.05.

Our second set of solutions gives higher $h_c$ values of 0.2. At NIR wavelengths, the disk aspect ratio obtained from the spiral wave model to the observed spirals of MWC 758 is suggested to be 0.18 (cite: 2013Grady) and 0.2 (cite: 2015Benisty). We note that if the upper bound value of $h_c$ increases, our best-fit will follow the largest $h_c$. However, $h_c$ larger than 0.2 would produce too much infrared flux for the SED fitting of MWC758 (cite: 2011Andrews), and consequently, the models with $h_c$ larger than 0.2 are discarded. The planet locations of our arm 1 and arm 2 suggested in the case of $h_c$ fixed to 0.2 are similar to the ones determined by (cite: 2015Benisty).

Following the WKB approximation in (cite: 2002Rafikov), the above results for the possible planet locations can also set limits to the embedded planet masses $M_p$. In the linear and weakly non-linear regime the analysis is applicable only for small planet masses, $M_p \lesssim M_l$, where $M_l$ is a characteristic mass given by $M_l = c_s^3 / (|2A|G)$ (cite: 2002Rafikov). $A$ is the Oort’s constant, $A(r) = (r/2)d\Omega/dr$ where $\Omega$ is the disk orbital frequency. Assuming a Keplerian disk, $\Omega(r)\sim r^{-1/2}$, and a sound speed of 0.5 km s$^{-1}$ (see section [\[sec:stability\]](#sec:stability)), the limit for the planet mass is 1 to 1.4 $M_{\textrm{J}}$ for r between 53 and 68 au.

Finally, we note that a different approach is taken in (cite: 2019Baruteau) where, instead of the analytical solution of the spiral patterns, complex 2D gas and dust hydrodynamical simulations are carried out to search for embedded planets in MWC 758.

(cite: 2019Baruteau) propose a scenario with two giant planets in their simulations in order to reproduce the observed structures, and two dust-trapping vortices at submm wavelengths and two spirals in the NIR emission. One planet is located at 35 au (inside the cavity), and the other planet is at 140 au (outside the disk). In our scenario, we suggest three planet locations for the three spirals detected in the submm wavelengths based on our analytical results.

# Discussion

![](nir_loc_draw_g.pdf)

## Submm versus NIR Emission

Two spiral features have been reported in MWC 758 at NIR wavelengths (cite: 2013Grady; 2015Benisty).

We overlay the peak locations obtained from our submm analysis on the NIR image in Figure [3](#fig:NIR+Gauss2) in order to compare the spatial locations of structures traced with these two wavelengths. In general, the features traced in these two different wavelength regimes are very similar. The spirals detected at NIR by (cite: 2015Benisty), namely their southeastern and northwestern spiral, are also seen at submm and correspond to our arm 1 and arm 2, respectively, although there is a radial shift. The submm arm 1 partly matches the location of the southeastern spiral seen in the NIR image, while it is partly shifted to the outer rim of the NIR spiral between about $200\ensuremath{^\circ}$ and $140\ensuremath{^\circ}$ in azimuth (Figure [3](#fig:NIR+Gauss2)). The submm arm 2 is located at larger radii than its counterpart in the NIR image (the northwestern spiral).

The most prominent feature seen at submm is the additional outer spiral in the northwest (arm 3; Figure [\[fig:gauss2\]](#fig:gauss2)c). The nearest NIR spiral, which possibly might be a counterpart to the submm arm 3, would be feature 4 identified in (cite: 2015Benisty). This, nevertheless, appears to imply a larger separation between the spirals identified at submm and NIR.

The differences in radial locations among the two wavelength regimes

can be explained by the disk geometry. With the trailing sense of the NIR spirals and a major axis of 65$\ensuremath{^\circ}$, the northwestern side is the near side. As the NIR emission is scattered on the submm dust grains, it is located at the inner edge of the submm structures, which then explains the differences between the two wavelengths seen at arm 2.

The additional faint NIR arc (cite: 2015Benisty) located adjacent to their northwestern spiral is closer to submm arm 2 and is at the inner edge of submm arm 3 with an $\sim0.2\ensuremath{''}$ offset in radius. This faint NIR arc might also be scattered emission by the tail of submm arm 2 but at the bottom side of the disk. In the southeast, at the far side of the disk, the NIR southeastern spiral is also at the inner edge of the submm arm 1 but with a smaller shift due to the projection effect.

## Correspondance with 9mm Dust Trapping Vortices?

MWC 758 was also observed with the VLA at 33 GHz (cite: 2015Marino; 2019Casassus). A clump in the north was resolved with a resolution of 0.1$''$ and was interpreted as a dust trapping vortex (cite: 2019Casassus).

This clump seen at 9 mm is at the northern tip of arm 3 seen at 0.9 mm. We note that at the location of this clump, there is a radial shift of about 0.06$''$ over an azimuthal range of $300\ensuremath{^\circ}$ to $365\ensuremath{^\circ}$ seen at 0.9 mm (see section [\[sec:three_features\]](#sec:three_features) and figure [\[fig:gauss2\]](#fig:gauss2)). An additional clump detected with the VLA 9 mm observations in the south, likely coinciding with the 0.9mm clump, was found to be less efficient to trap large dust grains (cite: 2019Casassus). Unlike for the northern clump with efficient dust grain trapping, we do not find a clear azimuthal dependence in radius near this southern clump at 0.9 mm. Given this absence of radial shift, our arm 2 does not include the southern clump.

## Rings and Spirals?

(cite: 2018Dong) reported observational results in MWC 758 with a higher angular resolution (0.04$''$) using ALMA at wavelengths of 0.9 mm. In order to obtain a better SN ratio, (cite: 2018Dong) averaged four regions of the disk covering a range of azimuth angles to obtain four averaged radial profiles. In the averaged radial profile of the western ring region (260$\ensuremath{^\circ}$ to 300$\ensuremath{^\circ}$ in azimuth), three bumps located at radii of $\sim$0.29$''$, $\sim$0.4$''$ and $\sim$0.51$''$ are found, suggesting that the continuum emission in MWC 758 consists of triple rings with a tentative eccentricity of 0.1 (cite: 2018Dong).

In contrast to their findings, using the analyses reported in section [3](#sec:ana) and with the lower angular resolution (0.11$''$) image, we identify three spirals (Sec. [\[sec:three_features\]](#sec:three_features)) in the continuum emission of the MWC 758 disk. In the scenario reported in (cite: 2018Dong), the regions which we identify as spirals are part of their ellipsoidal inner ring and part of their middle ring, where the middle ring is located at the end of the reported arm 2 in this paper at $\sim$0.4$''$ in radius and $\sim$300$\ensuremath{^\circ}$ in azimuth. As can be seen in figure [\[fig:gauss2\]](#fig:gauss2)b, the peak positions continuously move outward from 250$\ensuremath{^\circ}$ to 365$\ensuremath{^\circ}$ in azimuth with a shift of 0.1$''$ in radius.

We note that the inner ring identified in the western profile in figure 3a in (cite: 2018Dong) has a width of about 0.12$''$ (estimated from peak to the minimum flux between the inner and middle ring). This is roughly consistent with the radial shift of our arm 2 of 0.1$''$ in the same region.

Figure [4](#fig:compare) shows the continuum emission with a 0.04$''$ resolution (cite: 2018Dong) in two panels. Overlaid are the three structural features and the peak positions identified in this paper.

It is obvious that arm 2 at $\sim250\ensuremath{^\circ}$ clearly deviates from the elliptical inner ring. It extends to the inner edge of the northern clump at azimuth of 330$\ensuremath{^\circ}$ while also reaching the middle ring.

The right panel in Figure [4](#fig:compare) illustrates that the spiral arms identified in this work are also visible in the image from (cite: 2018Dong).

We note that some intensity profiles, in particular between azimuth 140$\ensuremath{^\circ}$ to 165$\ensuremath{^\circ}$ (see figure [8](#fig:az120to180)), might be better fit by three Gaussians. We have further compared the best-fit results between two and three Gaussians, because these fitting results might affect our identification of submm arm 1.

The 3-Gaussian fits are shown in figure [9](#fig:3gauss). Here, the best fits have much larger uncertainties for the 2nd and 3rd brightest Gaussian in most locations, except at azimuth 140$\ensuremath{^\circ}$ to 165$\ensuremath{^\circ}$. The locations of the brightest Gaussian component have overall negligible shifts in radius, as compared to the 2-Gaussian fitting. The second brightest Gaussian component, which would be the one to be taken for the identification of features relevant for submm arm 1, displays a shift of $\sim$ 0.03$''$ outward between azimuth 140 to 165$\ensuremath{^\circ}$. As a consequence of this 3-Gaussian fitting, the data points in panel [\[fig:overlay\]](#fig:overlay)d would shift upward between 140$\ensuremath{^\circ}$ and 160$\ensuremath{^\circ}$. This leads to an even smoother connection to the data around azimuth 160$\ensuremath{^\circ}$ and onward, and the original identification of submm arm 1 based on the 2-Gaussian fit would not be affected by this. Despite the resulting larger jump around 140$\ensuremath{^\circ}$, the connecting structure (submm arm 1) shown in a transparent mask in figure 7 remains unaffected. While the uncertainties in radial positions for the outer Gaussian (2-Gaussian fit) and the second brightest component (3-Gaussian fit) are comparable for the 140 to 165$\ensuremath{^\circ}$ range, the additional third Gaussian component has positional uncertainties up to about twice as large. Hence, the main conclusions in this paper remain based on the 2-Gaussian fits while acknowledging the possibility of a 3-Gaussian structure in this azimuth range.

Finally, we note that submm arm 1 was identified as part of the inner ring from azimuth 80$\ensuremath{^\circ}$ to 130$\ensuremath{^\circ}$ and an outer spiral starting from r$>$0.4$\ensuremath{''}$ in (cite: 2018Dong). With the above 2- versus 3-Gaussian comparison we are not able to unambiguously distinguish this scenario from a single continuous spiral with a twist around azimuth 140$\ensuremath{^\circ}$ (the scenario proposed in this paper).

We stress that – instead of averaging along azimuthal direction (which can erase radial trends) to get the radial profile – our analysis relies on splitting the disk into segments by azimuth, so that we can obtain information on the azimuthal structure of the disk and precisely track any possible change along the azimuthal direction.

![image](Analysis_Dong_v2_010.jpeg) ![image](Analysis_Dong_v2_011.jpeg)

# Summary and Conclusion

We search for continuum structural features in the MWC 758 disk with the goal of identifying possible asymmetrical structures that can be signposts for planet formation. ALMA Band 7 (0.9 mm) archival data are analyzed with different weightings. Our main results are summarized in the following.

1.  *Single-Gaussian Fits, Large-Scale Continuum Disk Geometry, and Asymmetrical Structures.* The robust-weighted continuum map with a resolution of 0.18$''$ and a sensitivity of 92 $\mu$Jy beam$^{-1}$ shows asymmetrical structures. The disk is split into segments along azimuth and single-Gaussians are fit to their radial intensity profiles. The resulting best-fit parameters are analyzed as a function of azimuth. An ellipse is fit to the Gaussians’ single peak positions in order to probe the disk geometry assuming a circular ring. In agreement with earlier work we find that single-Gaussian fits to the 0.9 mm robust-weighted continuum map with a resolution of 0.18$''$ cannot correctly infer the large-scale disk geometry as found from gas kinematics.

    This suggests that the 0.9 mm continuum emission traces more complex structures which are additionally influenced by forces other than the central gravity.

2.  *Two-Gaussian Fits, Isolating Spiral Arms.* The super-uniform-weighted continuum map with a resolution of 0.12$''$ and a sensitivity of 0.4 mJy beam$^{-1}$ provides a sharper image revealing additional important features. Here, each disk segment in azimuth (every 5$\ensuremath{^\circ}$) is fit to a two-Gaussian function along its radial direction. Based on the variations and trends of the locations of the inner and the outer Gaussians, we identify three spirals. The first spiral structure extends along the northern clump at a larger radius (arm 3). The second spiral structure (arm 2) consists of a tail-like extension connecting to the southern clump. The third spiral structure is the southeastern spiral (arm 1).

3.  *Analysis of Spirals and Planets.* The three spiral arms extracted in this work can be explained by and fit to the patterns of spiral density waves induced by planets. This yields three planet locations. A stability analysis shows that the two locations with brightest submm emission are gravitationally stable and without any significant level of turbulence.

4.  *Comparison with NIR.* We compare the submm spirals with the spirals in NIR in (cite: 2015Benisty). While two of the submm spirals (arm 1 and arm 2) have counterparts in the NIR image, the third one (arm 3) is absent at NIR wavelengths. Generally, a spatial offset between the arms in submm and NIR is observed, being larger in the northwest and smaller in the southeast. This offset can be well explained by the scattering of the NIR emission off the inner submm edge and projection effects between the near and far side. Assuming a disk aspect ratio $h_c$ of 0.2, the two planet locations for arm 1 and arm 2, determined from the spiral density wave with WKB approximation, are similar to the ones determined using the spirals seen at NIR by (cite: 2015Benisty).

5.  *Analysis Approach, Spirals, and Rings.* We compare our findings with the results from a higher-resolution 0.04$''$ ALMA image at 0.9 mm in (cite: 2018Dong). Based on averaging over azimuth in four sectors in order to get averaged radial profiles, (cite: 2018Dong) report a system of triple rings. Different from their approach, our analysis identifies three spiral arms based on tracking continuous changes of intensity peak locations along radial directions over a large range in azimuth. This is achieved by fitting profiles along radial directions in small azimuthal segments. We also identify spiral arms in the higher-resolution data. This comparison indicates that results can depend on the adopted analysis approach as well as on the resolution of the observations.

# Acknowledgments

This project is supported by the Ministry of Science and Technology (MoST) in Taiwan. YWT acknowledges support through MoST grant 108-2112-M-001-004-MY2. PMK and BTS acknowledge support from MoST 108-2112-M-001-012 and MoST 109-2112-M-001-022, and PMK acknowledges support from an Academia Sinica Career Development Award.

This paper makes use of the following ALMA data ADS/JAO. ALMA2012.1.00725.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

# Intensity profiles for each segment (robust)

![image](Gauss1_robust_5deg.jpg) ![image](Gauss1_robust_35deg.jpg) ![image](Gauss1_robust_65deg.jpg)\
![image](Gauss1_robust_95deg.jpg) ![image](Gauss1_robust_125deg.jpg) ![image](Gauss1_robust_155deg.jpg)\
![image](Gauss1_robust_185deg.jpg) ![image](Gauss1_robust_215deg.jpg) ![image](Gauss1_robust_245deg.jpg)\
![image](Gauss1_robust_275deg.jpg) ![image](Gauss1_robust_305deg.jpg) ![image](Gauss1_robust_335deg.jpg)

# Intensity profiles for each segment (SU)

![image](Gauss2_super_de_in21_3deg.jpg) ![image](Gauss2_super_de_in21_33deg.jpg) ![image](Gauss2_super_de_in21_63deg.jpg)\
![image](Gauss2_super_de_in21_93deg.jpg) ![image](Gauss2_super_de_in21_123deg.jpg) ![image](Gauss2_super_de_in21_153deg.jpg)\
![image](Gauss2_super_de_in21_183deg.jpg) ![image](Gauss2_super_de_in21_213deg.jpg) ![image](Gauss2_super_de_in21_243deg.jpg)\
![image](Gauss2_super_de_in21_273deg.jpg) ![image](Gauss2_super_de_in21_303deg.jpg) ![image](Gauss2_super_de_in21_333deg.jpg)

# Intensity profiles from 270$\ensuremath{^\circ}$ to 330$\ensuremath{^\circ}$ (SU)

![image](Gauss2_super_de_in21_273deg.jpg) ![image](Gauss2_super_de_in21_278deg.jpg) ![image](Gauss2_super_de_in21_283deg.jpg)\
![image](Gauss2_super_de_in21_288deg.jpg) ![image](Gauss2_super_de_in21_293deg.jpg) ![image](Gauss2_super_de_in21_298deg.jpg)\
![image](Gauss2_super_de_in21_303deg.jpg) ![image](Gauss2_super_de_in21_308deg.jpg) ![image](Gauss2_super_de_in21_313deg.jpg)\
![image](Gauss2_super_de_in21_318deg.jpg) ![image](Gauss2_super_de_in21_323deg.jpg) ![image](Gauss2_super_de_in21_328deg.jpg)

# Intensity profiles from 120$\ensuremath{^\circ}$ to 180$\ensuremath{^\circ}$ (SU)

![image](Gauss2_super_de_in21_123deg.jpg) ![image](Gauss2_super_de_in21_128deg.jpg) ![image](Gauss2_super_de_in21_133deg.jpg) ![image](Gauss2_super_de_in21_138deg.jpg) ![image](Gauss2_super_de_in21_143deg.jpg) ![image](Gauss2_super_de_in21_148deg.jpg) ![image](Gauss2_super_de_in21_153deg.jpg) ![image](Gauss2_super_de_in21_158deg.jpg) ![image](Gauss2_super_de_in21_163deg.jpg) ![image](Gauss2_super_de_in21_168deg.jpg) ![image](Gauss2_super_de_in21_173deg.jpg) ![image](Gauss2_super_de_in21_178deg.jpg)

# INTENSITY PROFILES FOR SEGMENTS at azimuth 120$\ensuremath{^\circ}$ to 165$\ensuremath{^\circ}$ (SU) with 3-Gaussian fits

![image](Gauss3_super_de_in21_123deg.jpg) ![image](Gauss3_super_de_in21_128deg.jpg) ![image](Gauss3_super_de_in21_133deg.jpg) ![image](Gauss3_super_de_in21_138deg.jpg) ![image](Gauss3_super_de_in21_143deg.jpg) ![image](Gauss3_super_de_in21_148deg.jpg) ![image](Gauss3_super_de_in21_153deg.jpg) ![image](Gauss3_super_de_in21_158deg.jpg) ![image](Gauss3_super_de_in21_163deg.jpg) ![image](Gauss3_para1.jpg) ![image](Gauss3_para2.jpg) ![image](Gauss3_para3.jpg)\

[^1]: Super-uniform weighting is similar to uniform weighting with an additional sub-parameter ’npixels’. ’npixels’ changes the number of uv-cell on a side to redefine the uv-plane. Neighboring cells share their weights which count visibilities in a larger area. We adopt npixels = 4 which optimizes the flux density among npixels = 2, 4, 6.

</paper>

Write the methods card for this paper.