# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...902L..33G\sonnetcc\reply.txt

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
 "bibcode": "2020ApJ...902L..33G",
 "title": "A Tale of Two Transition Disks: ALMA Long-baseline Observations of ISO-Oph 2 Reveal Two Closely Packed Nonaxisymmetric Rings and a ∼2 au Cavity",
 "year": 2020,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "González-Ruilova, Camilo",
 "n_authors": 15,
 "arxiv_id": "2010.03650",
 "doi": "10.3847/2041-8213/abbcce",
 "alma_projects_linked_by_archive": [
  "2016.1.00545.S",
  "2018.1.00028.S"
 ]
}
```

Paper text:
<paper>
# A Tale of Two Transition Disks: ALMA long-baseline observations of ISO-Oph 2 reveal two closely packed non-axisymmetric rings and a $\sim$2 au cavity [^1]

## Abstract

ISO-Oph 2 is a wide-separation (240 au) binary system where the primary star harbors a massive (M$_{\rm dust}$ $\sim$40 M$_{\oplus}$) ring-like disk with a dust cavity $\sim$50 au in radius and the secondary hosts a much lighter (M$_{\rm dust}$ $\sim$0.8 M$_{\oplus}$) disk.

As part of the high-resolution follow-up of the “Ophiuchus Disk Survey Employing ALMA” (ODISEA) project,

we present 1.3 mm continuum and $^{12}$CO molecular line observations of the system at 0.02$''$ (3 au) resolution.

We resolve the disk around the primary into two non-axisymmetric rings and find that the disk around the secondary is only $\sim$7 au across and also has a dust cavity (r $\sim$2.2 au).

Based on the infrared flux ratio of the system and the M0 spectral type of the primary, we estimate the mass of the companion to be close to the brown dwarf limit.

Hence, we conclude that the ISO-Oph 2 system contains the largest and smallest cavities, the smallest measured disk size, and the resolved cavity around the lowest mass object (M$_{\star}$ $\sim$0.08 M$_\odot$) in Ophiuchus.

From the $^{12}$CO data, we find a bridge of gas connecting both disks.

While the morphology of the rings around the primary might be due to an unseen disturber within the cavity,

we speculate that the bridge might indicate an alternative scenario in which the secondary has recently flown by the primary star causing the azimuthal asymmetries in its disk.

The ISO-Oph 2 system is therefore a remarkable laboratory to study disk evolution, planet formation, and companion-disk interactions.

# Introduction

The Atacama Large Millimeter/submillimeter Array (ALMA) is revolutionizing the field of disk evolution and planet formation by studying large populations of protoplanetary disks in nearby molecular clouds and individual objects in unprecedented detail. On one hand, disk demographic surveys provide information on fundamental disk properties such as mass and size as a function of stellar mass (cite: Pascucci2016; Barenfeld2016), age (cite: Ansdell2017; Ruiz2018), and multiplicity (cite: Cox2017; Manara2019; Zurlo2020). On the other hand, detailed high-resolution studies can deliver images at 3-4 au resolution at the distance of nearby star-forming regions (140–200 pc) such as Taurus, Lupus, Ophiuchus, and Chamaeleon in order to study their substructures (cite: ALMA2015; Andrews2018).

With almost 300 targets, the “Ophiuchus Disk Survey Employing ALMA” (ODISEA) project (cite: Cieza2019; Williams2019) is so far the largest of the disk demography surveys in nearby clouds and has identified several interesting objects for high-resolution follow-up observations.

One of the most interesting targets identified by ODISEA is ISO-Oph 2, a binary system with a projected separation of 240 au and a flux ratio of 0.08 in the K-band (cite: Ratzka2005).

The primary star has an M0 spectral type and an accretion rate typical of Classical T Tauri stars (10$^{-8.7}$ M$_{\odot}$yr$^{-1}$; (cite: Gatti2006) and hosts a massive (M$_{\rm dust}$ $\sim$40 M$_{\oplus}$) disk with the largest dust cavity ($\sim$50 au in radius) seen in the Ophiuchus cloud (cite: Cieza2019). The secondary star, which lacks a spectral classification in the literature, arbors a much lighter (M$_{\rm dust}$ $\sim$ 0.8 M$_{\oplus}$) disk that remained unresolved at 30 au resolution (cite: Cieza2019).

ISO-Oph 2 was observed with ALMA as part of the high-resolution follow-up of the 10 brightest ODISEA targets that were not included in the ALMA Cycle-4 Large Program DSHARP (cite: Andrews2018). The full sample of ODISEA targets observed at high-resolution is discussed in Cieza et al. (in prep.). Here we present the initial results of this long-baseline program and show that the ISO-Oph 2 system displays several exceptional properties when observed at 0.02$''$ (3 au) resolution.

# Observations and data analysis

## ALMA observations

The long-baseline data of ISO-Oph 2 were obtained during ALMA Cycle 6 under program 2018.1.00028.S. The source was observed in Band-6 (1.3 mm/230 GHz) in two different epochs with baselines up to 16.2 km. The correlator setup was chosen to maximize the continuum bandwidth (7.5 GHz). Three spectral windows were configured in Time Division Mode, with spectral resolution of 43  km s$^{-1}$, and overlap the continuum frequency from the Cycle 4 ODISEA observations at $\sim$217, 219, and 233 GHz. A fourth baseband was centered in the $^{12}$CO J = 2-1 line (230.538 GHz) and delivers a modest resolution of 1.5 km s$^{-1}$, enough to isolate the line (line width $\sim$5  km s$^{-1}$) and trace the spatial distribution of the gas. The observing log of the Cycle-6 long-baseline observations are shown in Table 1, together with relevant information on Cycle 4 data at lower spatial resolutions ((cite: Cieza2019), PID = 2016.1.00545.S) that we use to complement our new $^{12}$CO observations (see Section 3.3).

| UTC Date | 2019-06-21/02:07 | 2019-06-12/02:15 | 2018-05-26/06:44 | 2017-07-13/03:29 |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Config | C43-8/9 | C43-8/9 | C40-2 | C40-5 |  |  |  |  |  |  |
| Baselines | 82 m - 16.2 km | 82 m - 16.2 km | 14 m - 313 m | 16 m - 2.6 km |  |  |  |  |  |  |
| Mean PWV (mm) | 0.85 | 1.19 | 1.07 | 1.8 |  |  |  |  |  |  |
| Calibrators | J1517-2422, J1633-2557, | J1517-2422, J1633-2557, | J1517-2422, Ganymede, | J1517-2422, J1517-2422, |  |  |  |  |  |  |
|  | J1642-2849 | J1642-2849 | J1625-2527 | J1625-2527 |  |  |  |  |  |  |
| Beam size ($''$)$^a$ | 0.02 $\times$ 0.03 | 0.02 $\times$ 0.03 | 1.1 $\times$ 1.1 | 0.2 $\times$ 0.3 |  |  |  |  |  |  |
| Spectral resolution (km s$^{-1}$) | 1.5 | 1.5 | 0.08 | 0.08 |  |  |  |  |  |  |
| Continuum rms (mJy beam$^{-1}$) | 3.6$\times$10$^{-2}$ | 2.7$\times$10$^{-2}$ | 2.4$\times$10$^{-1}$ | 3.7$\times$10$^{-1}$ |  |  |  |  |  |  |
| Line rms (mJy beam$^{-1}$ km s$^{-1}$) | 26.5 | 18.7 | 89.5 | 53.4 |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |

: ALMA observations of the ISO-Oph 2 system

Table notes: $^{a}$ beam size corresponds to Briggs weighting and robust parameter of 0.5.

## Data analysis

All data sets were calibrated using the ALMA Science Pipeline which includes Water Vapor Radiometer and system temperature correction, as well as bandpass, phase, and amplitude calibration.

Continuum and line imaging was performed using the TCLEAN task in CASA v.5.6.1 (cite: McMullin2007), with Briggs weighting and robust parameter of 0.5.

Continuum images were produced using the continuum spectral windows of the high resolution data only, yielding an image with synthesized beam of 0.02$''$ $\times$ 0.03$''$ centered at 225 GHz.

Since there are two sources in the field of view, manual masks around each source were defined during the CLEANing process. Two iterations of phase-only self-calibration were conducted on each epoch separately using a mask covering both sources. Self calibration improved the signal-to-noise ratio of the final image by a factor of 1.7. The resulting image is shown in Figure 1, and its properties are described in Table 1.

Line imaging of the $^{12}$CO gas was performed combining the datasets with 0.02$'',$0.2$''$, and 1.1$''$ resolution.

The datasets at 0.02$''$ and 0.2$''$ resolution (2019 and 2017 epochs) were recentered using the location of the secondary disc at 0.02$''$ resolution in the continuum as reference point. The coordinates of the 1.1$''$ images (2018 epoch) were taken at face value as the secondary disc is only barely detected.

Self-calibration of the line data from all epochs and resolutions was done by applying the self-calibration solutions derived from the respective continuum datasets. We used the UVCONTSUB task to substract the continuum from the line data, after which the data was CLEANed using an auto-masking process (for regions up to 3$\times$rms) in TCLEAN to generate line cubes with 1.5 km s$^{-1}$ resolution.

To obtain an optimal balance between spatial resolution and sensitivity, we applied an uvtaper with an uppertaper = 0.1arcsec.

# Results

## (Sub)stellar masses

In order to estimate the mass of each component in the binary system, we first use the spectral type of the primary star (M0, (cite: Gatti2006)) and the infrared photometry to estimate its extinction, mass and age, and then use the flux ratio in the K-band to estimate the mass of the secondary object assuming the same age and extinction. We assume that the observed J-K color from 2MASS (cite: Cutri2003) is photospheric and calculate the extinction in K-band as $A_{K} = 0.53 \times    \left[\left(J -K\right)
-\left(J-K\right)_O\right]$, where $\left(J-K\right)_O$ is the photospheric color of an M0 star.

This assumption is supported by the fact that the ALMA data place an upper limit of 0.1 M$_{\oplus}$ for the mass of an inner disk around ISO-Oph 2A (see Section [3.2](#s:continuum)), but we note that the presence of K-band excess can not be ruled out for neither the A or B component in the system.

This approach gives A$_K$ = 1.3 mag and A$_V$ = 14.5 mag. Adopting the BT-Settl models (cite: Allard2012) and a distance of 144 pc (cite: Gaia2018), we estimate that the primary is a $\sim$1 Myr old star with a mass of 0.5 M$_\odot$ based on its spectral type and extinction corrected absolute K-band magnitude, 2.45.

Similarly, the flux ratio indicates that the secondary has a extinction-corrected K-band absolute magnitude of 5.2, corresponding to a T$_{eff}$ of 2900 K and a mass of 0.08 M$_\odot$, right at the stellar/substellar boundary. However, we note that stellar masses and ages of low-mass stars and brown dwarfs are model-dependent and notoriously difficult to estimate for individual objects (cite: Gonzales2020), and hence that these values must be taken with caution.

## Continuum

### Primary disk

The disk around the primary star shows a large cavity devoid of millimeter emission and a narrow and structured continuum outer disk (see Fig. 1).

The outer region is bright and breaks into substructure in the form of two narrow rings, which show spectacular azimuthal asymmetries. The outermost structure peaks toward South of the star and presents a prominent decrement to the North-West.

On the other hand, the innermost structure peaks toward the North-West and becomes nearly undetectable toward the South-East.

We do not detect emission near the center of the cavity, placing strong constraints on the mass of a putative inner disk. Based on the 5-$\sigma$ noise (0.18 mJy/beam) of the continuum observations and adopting the same basic assumptions as in (cite: Cieza2019), this limit corresponds to a dust mass of 0.1 M$_{\oplus}$ for an unresolved inner disk.

In order to highlight the substructure in the disk, a process of unsharp-masking was applied (cite: Perez2020A), which accentuates the narrow rings.

This sharper image is obtained by convolving the image with a circular Gaussian kernel to produce a smoothed version of the disk which is later subtracted from the original image.

In Fig. 2, we show the unsharp image of the disk around the primary deprojected to a Position Angle ($PA$) and an inclination ($i$) of 0.0 deg (panel a) and the corresponding radial profile (panel b).

To perform the deprojection, we explored a grid of different $PA$, $i$, and centers. We find that a $PA$ = 1.0 deg (E of N), and an $i$ = 36.4 deg, together with the coordinates from the Gaia Data Release 2 (cite: Gaia2018) corrected for proper motions[^2] provide the most circular deprojected image.

This suggests that the primary star is likely to be located at the center of the disk to within $\sim$15 mas or 2 au).

Both rings show azimuthal variations in intensity and/or width, which are difficult to disentangle, but as shown in panel b, when averaged over azimuth, the inner ring extends from a radius of $\sim$0.3$''$ to $\sim$0.4$''$ (43 to 58 au), while the outer one does from a radius of $\sim$0.4$''$ to $\sim$0.6$''$ (58 to 86 au).

Fig. 2 (panel b) additionally includes the K-band 5-$\sigma$ contrast as a function of radius (dashed-line) corresponding to the VLT-NACO image of ISO-Oph 2 presented in Fig. 6 of (cite: Zurlo2020).

While the 2.2 $\mu$m NACO data is not particularly deep, it allow us to rule out the presence of an equal brightness binary at the resolution limit of the observations 0.05$''$ (7 au) and of a 0.08 M$_{\odot}$ brown dwarf (K-band contrast $\sim$0.08) at distances larger than 50 au from the primary.

In Fig. 2, we also show the deprojected profile in polar coordinates (panel c), which we also average over the radial range of each ring, 0.3$''$ – 0.4$''$ for the inner ring and 0.4$''$ – 0.6$''$ for the outer ring (panel d).

These radially-averaged azimuthal profiles allow us to better characterize the azimuthal asymmetries.

The outer disk has a minimum at a $PA$ of $\sim$50 deg West of North, but emission is detected at all azimuths. The inner ring is fainter and radially narrower. It has an azimuthal extension of $\sim$260 deg (from $PA$ = 100 deg East of North to 160 deg West of North), peaking close to the minimum seen in the outer disk.

### Secondary disk

The disk around the secondary star is only 1.3 mJy and remained unresolved in our 0.2$''$ resolution observations (cite: Cieza2019).The long-baseline data shows that the disk is very compact, 0.05$''$ (7 au)

across (FWHM measured with the IMFIT routine within CASA) and exhibits the double peak (Fig. 1, panel b) characteristic of a transition disk with a marginally resolved inner dust cavity.

Given the small flux and angular size of the disk, which push the limit of ALMA’s capabilities, we estimate the size of the dust cavity adopting an analytical approach based on deprojecting the visibilities to 0.0 deg $i$ and 0.0 deg $PA$ in the $u-v$ plane.

In particular, the Real component of the visibilities as a function of deprojected $u-v$ distance for a face-on narrow ring is a zeroth-order Bessel function and the imaginary flux components of such a ring is 0.0 at all spatial frequencies. Following (cite: Hughes2007), the location of the first null on the Bessel function, $R_{null}$, is related to the cavity radius, $R_{cav}$, as follows:

$$\begin{equation}
R_{null} (k\lambda) = \frac{77916}{\pi^2} \left(
\frac{Distance}{100~pc}\right)\left(\frac{1~au}{R_{cav}}\right) 
\end{equation}$$

The deprojected *u-v*-distances are given by

$R=\sqrt{d^2_a+d_b^2}$, where $d_a =  \sqrt{u^2+v^2}\,  \sin\,  \phi$ and $d_b =  \sqrt{u^2+v^2}\,  \cos\,  \phi \,  \cos \, i$,

$\phi = \arctan(v/u) - PA$ (cite: Lay1997).

In order to construct the visibility profile of the disk around the secondary star, we first subtracted the visibilities of the CLEAN model of the disk around the primary from the visibility data, following (cite: Perez2020B).

We also changed the phase center to the position of the secondary as measured with IMFIT in CASA, which also provided initial approximations for the $i$ and $PA$ of the secondary disk. More precise values were obtained by minimizing the imaginary components in the imaginary part of the visibility profile. The resulting visibility profile corresponding to an $i$ = 10 deg and $PA$ = 122 deg is shown in Fig. 3. A null is seen at 5000 $\pm$ 500 k$\lambda$, which according to Equation 1 corresponds to cavity radius of 2.2$\pm$ 0.25 au.

Given the small size of the outer disk (FWHM/2 = 3.5 au), we conclude that the secondary disk also shows a ring-like morphology like the primary (e.g., with a width smaller than its inner radius).

## Molecular gas ($^{12}$CO) data

We find that the molecular line data of ISO-Oph 2 system exhibits interesting features as well.

The $^{12}$CO line peaks inside the cavity, but the emission is shifted toward the south, reaching the secondary (Fig. 4, panel a). As shown in the Position-Velocity (P-V) diagram (panel b), the disk around the primary is mostly detected at $\sim$1 and $\sim$4 km/s, while there is significant cloud contamination at velocities between 2 and 3 km/s.

The secondary, on the other hand, is mostly detected at $\sim$1.5 km/s. At velocities between 0 and 2 km/s, the P-V diagram also shows what seems to be a bridge of gas connecting both disks.

This bridge becomes even more evident in the channel map containing emission between 0.25 and 1.75 km/s (panel c).

Finally, in panel d of Fig. 4, we show the intensity-weighted mean velocity (moment-1) map of the $^{12}$CO data. This map is consistent with Keplerian motion as the extreme velocities are observed along the major axis of the disk. We therefore conclude that there is no indication of an inner cavity in the gas, which is consistent with the relatively high accretion rate of the system (10$^{-8.7}$ M$_{\odot}$yr$^{-1}$; (cite: Gatti2006)). We also note that the kinematic center of the disk (where the minimum and maximum velocities converge) coincides with the expected location of the star based on the position and proper motions from Gaia.

# Discussion

ALMA observations at 3-30 au resolution have shown that protoplanetary disks in general, and transition disks in particular, have diverse substructures.

The DSHARP project, the largest long-baseline survey of disks thus far (cite: Andrews2018) has revealed that narrow rings and gaps are the most common substructure in protoplanetary disks. Unfortunately that project does not include transition objects. More recently, (cite: Francis2020) collected a large sample of $\sim$40 of disks with large (r $>$ 25 au) dust cavities.

Around half of the stars in that sample have dusty inner disks detected, something that is not seen in ISO-Oph 2 A.

Most transition disks are azimuthally symmetric, but several examples with azimuthal asymmetries do exist such as IRS-Oph 48 (cite: vanderMarel2013), HD 142527 (cite: Casassus2013), HD 135344B (cite: Cazzoletti2018), SR 21 (cite: Muro2020), CIDA 9, RY Lup and HD 34282 (cite: Long2019; Francis2020).

These asymmetries are most likely dynamical in nature and can be planet-induced vortices (cite: Hammer2019.482.3609H) or be produced by stellar companions (cite: Price2018; Calcino2019).

However, the disk around ISO-Oph 2 A is particularly rare because it shows not one, but two closely packed and azimuthally asymmetric rings, resembling other very complex systems such as MWC 758 (cite: 2018ApJ...860..124D).

As demonstrated by (cite: Perez2019), a single migrating planet can produce multiple rings, but it remains to be established by future hydrodynamic modeling if the rings produces this way can be as non-axisymmetric as seen in ISO-Oph 2 A.

The possible bridge of gas connecting both disks in the system (Fig. 4) might indicate a different origin for the complex structure of the disk around the primary. At its current location, the secondary itself is too far away (240 au) to disturb the primary disc significantly.

However, if ISO-Oph 2 is a very eccentric binary system or an unbound flyby, it is possible that some of the structure seen in the primary disk is the result of the recent close approach of ISO-Oph 2 B.

Stellar flybys are rare but still statistically possible in low-mass star-forming regions (cite: Cuello2020).

Possible disk flybys reported in the literature include RW Aur (cite: Dai2015), HV Tau and DO Tau (cite: Winter2018), AS 205 (cite: Kurtovic2018) and UX Tau A (cite: Menard2020).

These flybys typically exhibit arcs of gas hundreds of au long connecting the disks in the system, in agreement with the results of hydrodynamic models (e.g. (cite: Cuello2020)).

The same models show that flybys also trigger spiral arms within the disks. Therefore, we speculate that, *if the initial configuration are two narrow rings*, a close approach could result in azimuthal asymmetries similar to the ones observed in the disc around the ISO-Oph 2 A disk.

Unfortunately the Gaia Data Release 2 only provides proper motions for the primary star and is not possible to constrain the relative motion of ISO-Oph 2 A and ISO-Oph 2 B with enough precision to assess the likelihood of the flyby scenario.

However, we note that, assuming the closest encounter occurred 500 yr ago, as in the simulation presented by Cuello et el. (2020), the relative proper motion between the primary an the secondary would be expected to be $\sim$3.4 mas/yr.

The flyby hypothesis could also be tested in the future with hydrodynamic modeling tailored to the system.

The disk around ISO-Oph 2 B is also very interesting as it has one of the smallest cavities ever resolved at (sub)mm wavelengths. With a radius of just $\sim$2.2 au, the cavity size is at the limit of ALMA’s resolution at the distance of the closest molecular clouds (d $\sim$ 140 pc).

Interestingly, TW Hydra, one of the closest stars to Earth with a protoplanetary disk (d = 60 pc) also hosts a transition disk with a very small cavity, only $\sim$1 au in radius (cite: Andrews2016).

However, unlike TW Hydra, ISO-Oph 2 B has a disc that seems to be narrow (width/radius $<$ 1.0), resembling the structures of other disks such as ISO-Oph 2 A, Sz 91 (cite: Canovas2016), and T Cha (cite: Hendler2018), but in a much smaller scale (by a factor of 15-40 in radius).

Furthermore, ISO-Oph 2 B also is the lowest-mass object with a resolved dust cavity in the Ophiuchus molecular cloud, and possible in any region

Based on the age ($\sim$1 Myr) and mass (0.08 $M_{\odot}$) estimates discussed in Section 3.1, ISO-Oph 2 B should have an M6.5 spectral type. However, all the 7 objects that have resolved cavities in the ODISEA sample have earlier spectral types (Ruiz-Rodriguez et al. in prep). That is also the case for all pre-main-sequence stars with transition disks identified in Ophiuchus based on their IR SEDs (cite: Cieza2010; Merin2010); and all the transition objects with mm data (from all regions) recently compiled by (cite: Francis2020), and (cite: Pinilla2020).

# Summary and Conclusions

We present new 1.3 mm ALMA long-baseline data of the ISO-Oph 2 system at 3 au resolution. Our main results and conclusions are as follow:

1\) The ring-like structure of the primary disk is resolved into two non-axysimmetric rings, suggesting dynamical disturbances. Future hydrodynamic modeling could help explaining the origin of these substructures and establish whether they are due to an internal or an external disturber.

2\) The high-resolution continuum observations reveal the disk around the secondary is 7 au across (FHWM) and has an inner cavity just 2.2 au in radius.

This implies that ISO-Oph 2 B has the smallest (transition) disk ever imaged in Ophiuchus and likely has a ring-like morphology (width $<$ inner radius).

3\) The flux ratio in the of ISO-Oph 2 system at 2.2 $\mu$m (0.08) and the spectral type of the primary (M0) implies the secondary is at the brown dwarf mass limit, rendering ISO-Oph 2 B the lowest mass object in the cloud with a resolved dust cavity in its disk.

4\) The $^{12}$CO observations indicate that there is significant gas within the large cavity in the primary disk and suggest that the two disks might be connected by bridge of gas. This bridge might indicate that the secondary object recently flew by the primary and provides an alternative scenario for the origin of the azimuthal asymmetries in the disk around the primary.

# Acknowledgments

We thank the anonymous referee for the helpful comments, and constructive remarks on this article.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00728.S and ADS/JAO.ALMA#2018.1.00028.S.

ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile.

M.F. has received funding from the European Research Council (grant 757957).

A.Z. acknowledges support from the ANID-FONDECYT grant 11190837.

S.P acknowledges support from ANID-FONDECYT grant 1191934 and the ESO-Chile Joint Committee.

P.P. acknowledges support provided by the Alexander von Humboldt Foundation.

D.P. acknowledges support from Australian Research Council grants DP180104235 and FT130100034

natexlab

(ref: Allard2012) Allard, F., Homeier, D., & Freytag, B. 2012, Philosophical Transactions of the Royal Society of London Series A, 370, 2765, doi: [`10.1098/rsta.2011.0269`](http://doi.org/10.1098/rsta.2011.0269)

(ref: ALMA2015) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3, doi: [`10.1088/2041-8205/808/1/L3`](http://doi.org/10.1088/2041-8205/808/1/L3)

(ref: Andrews2016) Andrews, S. M., Wilner, D. J., Zhu, Z., et al. 2016, ApJL, 820, L40, doi: [`10.3847/2041-8205/820/2/L40`](http://doi.org/10.3847/2041-8205/820/2/L40)

(ref: Andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: Ansdell2017) Ansdell, M., Williams, J. P., Manara, C. F., et al. 2017, AJ, 153, 240, doi: [`10.3847/1538-3881/aa69c0`](http://doi.org/10.3847/1538-3881/aa69c0)

(ref: Barenfeld2016) Barenfeld, S. A., Carpenter, J. M., Ricci, L., & Isella, A. 2016, The Astrophysical Journal, 827, 142, doi: [`10.3847/0004-637x/827/2/142`](http://doi.org/10.3847/0004-637x/827/2/142)

(ref: Calcino2019) Calcino, J., Price, D. J., Pinte, C., et al. 2019, MNRAS, 490, 2579, doi: [`10.1093/mnras/stz2770`](http://doi.org/10.1093/mnras/stz2770)

(ref: Canovas2016) Canovas, H., Caceres, C., Schreiber, M. R., et al. 2016, MNRAS, 458, L29, doi: [`10.1093/mnrasl/slw006`](http://doi.org/10.1093/mnrasl/slw006)

(ref: Casassus2013) Casassus, S., van der Plas, G. M., Perez, S., et al. 2013, Nature, 493, 191, doi: [`10.1038/nature11769`](http://doi.org/10.1038/nature11769)

(ref: Cazzoletti2018) Cazzoletti, P., van Dishoeck, E. F., Pinilla, P., et al. 2018, A&A, 619, A161, doi: [`10.1051/0004-6361/201834006`](http://doi.org/10.1051/0004-6361/201834006)

(ref: Cieza2010) Cieza, L. A., Schreiber, M. R., Romero, G. A., et al. 2010, ApJ, 712, 925, doi: [`10.1088/0004-637X/712/2/925`](http://doi.org/10.1088/0004-637X/712/2/925)

(ref: Cieza2019) Cieza, L. A., Ruı́z-Rodrı́guez, D., Hales, A., et al. 2019, MNRAS, 482, 698, doi: [`10.1093/mnras/sty2653`](http://doi.org/10.1093/mnras/sty2653)

(ref: Cox2017) Cox, E. G., Harris, R. J., Looney, L. W., et al. 2017, ApJ, 851, 83, doi: [`10.3847/1538-4357/aa97e2`](http://doi.org/10.3847/1538-4357/aa97e2)

(ref: Cuello2020) Cuello, N., Louvet, F., Mentiplay, D., et al. 2020, MNRAS, 491, 504, doi: [`10.1093/mnras/stz2938`](http://doi.org/10.1093/mnras/stz2938)

(ref: Cutri2003) Cutri, R. M., Skrutskie, M. F., van Dyk, S., et al. 2003, 2MASS All Sky Catalog of point sources.

(ref: Dai2015) Dai, F., Facchini, S., Clarke, C. J., & Haworth, T. J. 2015, MNRAS, 449, 1996, doi: [`10.1093/mnras/stv403`](http://doi.org/10.1093/mnras/stv403)

(ref: 2018ApJ...860..124D) Dong, R., Liu, S.-y., Eisner, J., et al. 2018, ApJ, 860, 124, doi: [`10.3847/1538-4357/aac6cb`](http://doi.org/10.3847/1538-4357/aac6cb)

(ref: Francis2020) Francis, L., & van der Marel, N. 2020, ApJ, 892, 111, doi: [`10.3847/1538-4357/ab7b63`](http://doi.org/10.3847/1538-4357/ab7b63)

(ref: Gaia2018) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1, doi: [`10.1051/0004-6361/201833051`](http://doi.org/10.1051/0004-6361/201833051)

(ref: Gatti2006) Gatti, T., Testi, L., Natta, A., Randich, S., & Muzerolle, J. 2006, A&A, 460, 547, doi: [`10.1051/0004-6361:20066095`](http://doi.org/10.1051/0004-6361:20066095)

(ref: Gonzales2020) Gonzales, E. J., Crepp, J. R., Bechter, E. B., et al. 2020, ApJ, 893, 27, doi: [`10.3847/1538-4357/ab71fb`](http://doi.org/10.3847/1538-4357/ab71fb)

(ref: Hammer2019.482.3609H) Hammer, M., Pinilla, P., Kratter, K. M., & Lin, M.-K. 2019, MNRAS, 482, 3609, doi: [`10.1093/mnras/sty2946`](http://doi.org/10.1093/mnras/sty2946)

(ref: Hendler2018) Hendler, N. P., Pinilla, P., Pascucci, I., et al. 2018, MNRAS, 475, L62, doi: [`10.1093/mnrasl/slx184`](http://doi.org/10.1093/mnrasl/slx184)

(ref: Hughes2007) Hughes, A. M., Wilner, D. J., Calvet, N., et al. 2007, ApJ, 664, 536, doi: [`10.1086/518885`](http://doi.org/10.1086/518885)

(ref: Kurtovic2018) Kurtovic, N. T., Pérez, L. M., Benisty, M., et al. 2018, ApJL, 869, L44, doi: [`10.3847/2041-8213/aaf746`](http://doi.org/10.3847/2041-8213/aaf746)

(ref: Lay1997) Lay, O. P., Carlstrom, J. E., & Hills, R. E. 1997, ApJ, 489, 917, doi: [`10.1086/304815`](http://doi.org/10.1086/304815)

(ref: Long2019) Long, F., Herczeg, G. J., Harsono, D., et al. 2019, ApJ, 882, 49, doi: [`10.3847/1538-4357/ab2d2d`](http://doi.org/10.3847/1538-4357/ab2d2d)

(ref: Manara2019) Manara, C. F., Tazzari, M., Long, F., et al. 2019, A&A, 628, A95, doi: [`10.1051/0004-6361/201935964`](http://doi.org/10.1051/0004-6361/201935964)

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Menard2020) Ménard, F., Cuello, N., Ginski, C., et al. 2020, A&A, 639, L1, doi: [`10.1051/0004-6361/202038356`](http://doi.org/10.1051/0004-6361/202038356)

(ref: Merin2010) Merı́n, B., Brown, J. M., Oliveira, I., et al. 2010, ApJ, 718, 1200, doi: [`10.1088/0004-637X/718/2/1200`](http://doi.org/10.1088/0004-637X/718/2/1200)

(ref: Muro2020) Muro-Arena, G. A., Ginski, C., Dominik, C., et al. 2020, A&A, 636, L4, doi: [`10.1051/0004-6361/202037656`](http://doi.org/10.1051/0004-6361/202037656)

(ref: Pascucci2016) Pascucci, I., Testi, L., Herczeg, G. J., et al. 2016, The Astrophysical Journal, 831, 125, doi: [`10.3847/0004-637x/831/2/125`](http://doi.org/10.3847/0004-637x/831/2/125)

(ref: Perez2019) Pérez, S., Casassus, S., Baruteau, C., et al. 2019, AJ, 158, 15, doi: [`10.3847/1538-3881/ab1f88`](http://doi.org/10.3847/1538-3881/ab1f88)

(ref: Perez2020A) Pérez, S., Casassus, S., Hales, A., et al. 2020a, ApJL, 889, L24, doi: [`10.3847/2041-8213/ab6b2b`](http://doi.org/10.3847/2041-8213/ab6b2b)

(ref: Perez2020B) Pérez, S., Hales, A., Liu, H. B., et al. 2020b, ApJ, 889, 59, doi: [`10.3847/1538-4357/ab5c1b`](http://doi.org/10.3847/1538-4357/ab5c1b)

(ref: Pinilla2020) Pinilla, P., Pascucci, I., & Marino, S. 2020, A&A, 635, A105, doi: [`10.1051/0004-6361/201937003`](http://doi.org/10.1051/0004-6361/201937003)

(ref: Price2018) Price, D. J., Cuello, N., Pinte, C., et al. 2018, MNRAS, 477, 1270, doi: [`10.1093/mnras/sty647`](http://doi.org/10.1093/mnras/sty647)

(ref: Ratzka2005) Ratzka, T., Köhler, R., & Leinert, C. 2005, A&A, 437, 611, doi: [`10.1051/0004-6361:20042107`](http://doi.org/10.1051/0004-6361:20042107)

(ref: Ruiz2018) Ruı́z-Rodrı́guez, D., Cieza, L. A., Williams, J. P., et al. 2018, MNRAS, 478, 3674, doi: [`10.1093/mnras/sty1351`](http://doi.org/10.1093/mnras/sty1351)

(ref: vanderMarel2013) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2013, Science, 340, 1199, doi: [`10.1126/science.1236770`](http://doi.org/10.1126/science.1236770)

(ref: Williams2019) Williams, J. P., Cieza, L., Hales, A., et al. 2019, ApJL, 875, L9, doi: [`10.3847/2041-8213/ab1338`](http://doi.org/10.3847/2041-8213/ab1338)

(ref: Winter2018) Winter, A. J., Booth, R. A., & Clarke, C. J. 2018, MNRAS, 479, 5522, doi: [`10.1093/mnras/sty1866`](http://doi.org/10.1093/mnras/sty1866)

(ref: Zurlo2020) Zurlo, A., Cieza, L. A., Pérez, S., et al. 2020, Monthly Notices of the Royal Astronomical Society, 496, 5089, doi: [`10.1093/mnras/staa1886`](http://doi.org/10.1093/mnras/staa1886)

[^1]: Released on June, 10th, 2019

[^2]: Ra = 246.408838 deg; Dec = $-$24.376830 deg; Epoch = 2015.5; pmra = $-$5.4 mas yr$^{-1}$; pmdec = $-$25.2 mas yr$^{-1}$

</paper>

Write the methods card for this paper.