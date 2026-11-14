# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2023ApJ...956..135W\sonnetcc\reply.txt

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
 "bibcode": "2023ApJ...956..135W",
 "title": "Deep Search for Molecular Oxygen in TW Hya",
 "year": 2023,
 "journal": "The Astrophysical Journal",
 "first_author": "Williams, Becky J.",
 "n_authors": 4,
 "arxiv_id": "2309.04521",
 "doi": "10.3847/1538-4357/acf717",
 "alma_projects_linked_by_archive": [
  "2019.1.01177.S"
 ]
}
```

Paper text:
<paper>
# Deep Search for Molecular Oxygen in TW Hya

## Abstract

The dominant form of oxygen in cold molecular clouds is gas-phase carbon monoxide (CO) and ice-phase water (H$_2$O). Yet, in planet-forming disks around young stars, gas-phase CO and H$_2$O are less abundant relative to their ISM values, and no other major oxygen-carrying molecules have been detected. Some astrochemical models predict that gas-phase molecular oxygen (O$_2$) should be a major carrier of volatile oxygen in disks. We report a deep search for emission from the isotopologue $^{16}$O$^{18}$O ($N_J=2_1-0_1$ line at 233.946 GHz) in the nearby protoplanetary disk around TW Hya. We used imaging techniques and matched filtering to search for weak emission but do not detect $^{16}$O$^{18}$O. Based on our results, we calculate upper limits on the gas-phase O$_2$ abundance in TW Hya of $(6.4-70)\times10^{-7}$ relative to H, which is $2-3$ orders of magnitude below solar oxygen abundance. We conclude that gas-phase O$_2$ is not a major oxygen-carrier in TW Hya. Two other potential oxygen-carrying molecules, SO and SO$_2$, were covered in our observations, which we also do not detect. Additionally, we report a serendipitous detection of the C$^{15}$N $N_J = 2_{5/2}-1_{3/2}$ hyperfine transitions, $F = 3 - 2$ and $F = 2 - 1$, at 219.9 GHz, which we found via matched filtering and confirm through imaging.

# Introduction

Protoplanetary disks provide a critical link in understanding the chemical evolution from the interstellar medium (ISM) to planetary systems (including our own solar system). By studying these environments, we can understand how molecular abundances change as stars, and later planets, form. Such observations are helpful to put our own solar system into context. So far, there have been about 300 unique molecules (not including isotopologues) detected in the ISM. Within protoplanetary disks, only 25 unique molecules have been detected (cite: McGuire2022). This low detection rate is not due to decreased chemistry in disks, but because we do not know some of the key tracers of the most abundant elements, such as oxygen.

Oxygen is the third most abundant element in the Universe, with a solar oxygen abundance of $4.9 \times 10^{-4}$ relative to hydrogen (cite: Asplund2009; Asplund2021). The vast majority of oxygen in the Universe is incorporated into gas-phase molecules, ice-phase molecules, or refractory dust. (cite: Whittet2010) considered the incorporation of oxygen into silicates and oxides and estimated that the amount of oxygen in dust is $(0.9-1.4)\times10^{-4}$ relative to hydrogen in different ISM environments.

(cite: vanDishoeck2021) discuss the oxygen budget of ISM environments, assuming a total oxygen abundance of $5.8 \times 10^{-4}$ relative to hydrogen (cite: Przybilla2008). They note that about $20\%$ of the total abundance of oxygen is unaccounted for in diffuse clouds, increasing to $50\%$ in dense regions. Two of the most common molecules in the ISM and protoplanetary disks are carbon monoxide (CO) and water (H$_2$O). In warm gas in the interstellar medium, gas-phase CO has an abundance of about $10^{-4}$ relative to hydrogen (cite: Ripple2013), but is observed to be less abundant in protoplanetary disks (cite: Dutrey1994; Ansdell2016; Long2017). Similarly, water ice has an abundance of H$_2$O/H$_2$ $\approx 10^{-4}$ in dense clouds (cite: vanDishoeck2013), but water vapor has been detected in low abundance in only a few disks (cite: Du2017). It is possible that a large amount of oxygen is in frozen species, such as water ice, that are difficult to observe. Another possibility is that oxygen is in other gas-phase molecules, such as molecular oxygen (O$_2$).

O$_2$ has been observed in low abundances in two molecular clouds: O$_2$/H$_2$ $\approx (0.3-7.3) \times 10^{-6}$ in Orion (cite: Goldsmith2011) and O$_2$/H$_2$ $\approx 5 \times 10^{-8}$ in $\rho$ Oph A (cite: Liseau2012). O$_2$ is a reactive molecule, and its most common form, $^{16}$O$^{16}$O, is difficult to detect due to a lack of a permanent dipole moment. The less-abundant isotopologue $^{16}$O$^{18}$O does, however, have a dipole moment. Through this isotopologue, O$_2$ was tentatively detected in the protostellar system IRAS 16293-2422 B (cite: Taquet2018). There have been no other reported detections of O$_2$ in protoplanetary disks.

Interestingly, O$_2$ has been detected in our own solar system in comets, which we do not expect to have undergone much chemical evolution since their formation in the pre-solar nebula. For example, O$_2$ was detected in the coma of comet 67P/Churyumov-Gerasimenko (67P) by the ROSINA (cite: Balsiger2007) instrument on ESA’s Rosetta spacecraft. (cite: Bieler2015) found an unexpectedly high average O$_2$ to water ratio of $3.80 \pm 0.85\%$, making O$_2$ the fourth most abundant species in the coma. O$_2$ was also detected in comet 1P/Halley at an abundance of $3.7 \pm 1.7\%$ relative to water (cite: Rubin2015). In both cases, O$_2$ and H$_2$O abundance appear to be correlated. As described in (cite: LuspayKuti2018), there have been many proposed origins for O$_2$ in comets, ranging from *in situ* processes to origins in the ISM prior to formation of the solar nebula. Recent analysis by (cite: LuspayKuti2022) shows that, farther from the Sun, O$_2$ abundance in 67P is more strongly correlated with CO and CO$_2$ than with H$_2$O. They suggest that 67P has two reservoirs of O$_2$: a deep primordial nucleus of CO and CO$_2$ ice, and a surface layer of H$_2$O ice that formed later.

If O$_2$ in comets is not formed *in situ*, then it must have been present in the protoplanetary disk from whence the comet formed. This scenario is supported by chemical models that predict a large amount of oxygen is in gas-phase O$_2$ in the inner regions of disks. For example, O$_2$ ice can be produced on dust grain surfaces and under certain conditions desorbs faster than it reacts to form other molecules. (cite: Eistrup2018) predict that this process occurs in the midplane of disks, resulting in a build-up of gas-phase O$_2$ between the H$_2$O and O$_2$ ice lines (between 0.7 and 10 au after 8 million years). (cite: Walsh2015) meanwhile predict that gas-phase O$_2$ builds up in the atmosphere of T Tauri disks, produced via gas-phase neutral-neutral reactions of O $+$ OH. They predict that O$_2$ may carry 50$\%$ of the total oxygen in the disk’s atmosphere, and 10$\%$ when including the midplane.

In this paper, we present a deep search for $^{16}$O$^{18}$O emission in ALMA observations of TW Hya, a well-studied T Tauri protoplanetary disk. TW Hya’s relatively gas-rich disk and nearby proximity make it a good candidate for searching for faint emission. There have been many observations of gas emission lines in TW Hya, and previous observations have shown that CO gas is 1-2 orders of magnitude less abundant than in the ISM (cite: Favre2013; Cleeves2015co). Water vapor has a maximum observed abundance of H$_2$O/H$_2$ $\approx10^{-7}$ in TW Hya (cite: Hogerheijde2011). Evidently, gas-phase CO and H$_2$O do not account for the majority of oxygen in TW Hya. Could oxygen be hiding in gas-phase O$_2$?

# Observations

Observations of the $^{16}$O$^{18}$O $N_J=2_1-0_1$ line at 233.946 GHz toward TW Hya were carried out as part of ALMA program 2019.1.01177.S (PI: Eistrup). Observations occurred on two nights in 2021, April 4 and April 6, for a combined time of 91 minutes on source. On April 4, there were 44 antennas and baselines of 15-1398 meters, and on April 6, 45 antennas and baselines of 15-1263 meters. J1058+0133 was adopted as the amplitude and bandpass calibrator, while J1037-2934 was used for phase calibration. The data were calibrated using the standard ALMA pipeline.

We searched for $^{16}$O$^{18}$O emission in both the image plane and the visibility plane, as described in more detail in the following section. Subsequent imaging and analysis were carried out using the Common Astronomy Software Applications (CASA) version 6.4 (cite: CASA2007). Continuum emission was subtracted using the task *uvcontsub*, applying a fit order of 1 and excluding edge channels. The data were imaged using *tclean*, initially with a natural weighting scheme to improve line sensitivity. The resulting beam is $0.59''$ by $0.50''$ with a position angle of $-88\degree$, equivalent to a spatial resolution of 30 to 35 au at a distance of 60.1 pc (cite: BailerJones2018). The rms noise is 2.59 mJy beam$^{-1}$ for a channel width of 0.235 km s$^{-1}$. For the matched filtering analysis, Earth’s rotation was first corrected for using the CASA task *cvel*.

# Methods

We first created a Keplerian mask (cite: TeagueKepMask) to use with the CASA *tclean* task. Due to the rotation of disks, we observe some emission to be shifted to higher or lower frequencies, so certain regions of the disk will be brighter in different channels. A Keplerian mask traces this emission pattern, based on the parameters of the disk, to improve the signal to noise of the integrated intensity (cite: Salinas2017; Teague2022). We assumed a systemic velocity of 2.86 km s$^{-1}$ (cite: Favre2013), distance of 60.1 pc (cite: BailerJones2018), inclination $= 5.8\degree$, position angle $=151\degree$, and stellar mass $= 0.81$ M$_\odot$ (cite: Teague2019). The mask was created using CO $J=3-2$ emission data for TW Hya from (cite: Huang2018), and parameters optimized to fully trace the CO emission. Specifically, we set the *target_res* = 0.4, which convolves the mask with a circular beam of 0.4 arcsec FWHM, and *dV0* = 500 m s$^{-1}$, which affects the radially varying line width of emission. Two masks were then created for the O$_2$ data, one with a radius set to 100 au (convolved to 120 au), and a second with a radius set to 240 au (convolved to 260 au, covering the extent of the CO emission). Both masks were used separately in cleaning, using a $5\sigma$ threshold. The resulting image was the same in both cases because there were no values above $5\sigma$ within either mask.

The *tclean* task has several parameters that can be varied to bring out faint emission. For example, the choice of weighting scheme and uvtaper can be tuned to give a higher weighting to shorter baselines to increase sensitivity, at the expense of a lower resolution. Because we were mainly interested in looking at the disk integrated flux, we did not need the full spatial resolution of the observations. We imaged the data with several combinations of the Briggs weighting robust parameter (cite: Briggs1995) and uvtaper. We used channel averaging as another method of revealing faint emission. The original channel width of the data was 0.078 km s$^{-1}$, and we experimented with averaging 2, 3, and 5 channels together.

![](im_channels_0419.pdf)

Matched filtering is a technique to detect weak emission in observational data (cite: Loomis2018). Matched filtering is applied in the visibility plane and therefore does not involve any imaging. It requires a filter that models the expected pattern of emission across velocity channels. The filter is Fourier transformed to generate a kernel that is then cross-correlated with the data. The result is an impulse response spectrum, with peaks indicating possible emission. For matched filtering, we used both Keplerian masks as filters (one with a 120 au radius, and one with a 260 au radius). It is possible that O$_2$ emission covers a smaller area than these radii and could be hidden in the noise. However, Keplerian masks cover less area in edge channels, so a smaller mask is below the resolution of the images.

# Results

## Imaging Results

Figure [1](#fig:channels) shows the data imaged with natural weighting and velocity averaging to a channel size of 0.235 km s$^{-1}$. For all attempted combinations of imaging parameters, no significant detection was found within either choice of mask. A spectrum, calculated within 260 au, is shown in Figure [2](#fig:o2_spec). The average rms noise level per channel in Figure [1](#fig:channels) is 2.59 mJy beam$^{-1}$. We calculated a disk integrated flux (for a velocity range of 4.69 km s$^{-1}$) of $-11.8 \pm 14.2$ mJy km s$^{-1}$ within 120 au, and $7.4 \pm 18.0$ mJy km s$^{-1}$ within 260 au; i.e., at the noise level of the data, we do not detect $^{16}$O$^{18}$O $N_J=2_1-0_1$ emission.

![](o2spec_260au_0819.pdf)

## Matched Filter Results

While we cannot see emission in the image plane, if there is emission just below the noise level, matched filtering has previously been successful at finding the signatures of line emission in other sources (cite: Loomis2020), including when using a Keplerian mask as a template (cite: Loomis2018). By applying the Keplerian mask as our template, we provide an expectation for where rotating gas emission should appear spatially in our data. Since we do not know the extent of the O$_2$, we try both the 120 au and 260 au masks as templates. The results of matched filtering the data with these templates are presented in Figure [3](#fig:matfil). A $3\sigma$ response at 0 km s$^{-1}$ would indicate emission from $^{16}$O$^{18}$O. Neither filter resulted in a $3\sigma$ impulse response. We can conclusively say that the $^{16}$O$^{18}$O 233.946 GHz line is not detected at the sensitivity of the present measurements.

![](im_matfil_0419.pdf)

## O$_2$ Upper Limits

How much oxygen could be hiding within our upper limit on $^{16}$O$^{18}$O emission? To estimate the total number of O$_2$ atoms from a single line, we explore a range of temperatures and assume its emission is in local thermodynamic equilibrium (LTE). Using the image-plane disk integrated flux limits from Section [4.1](#imresult), we calculate the 1$\sigma$ upper limit on the maximum number of O$_2$ molecules that could be present in TW Hya, using the following adapted from (cite: Bergin2013).

$$\begin{equation}
\label{eq1}
 F_l = \frac{\mathcal{N}_{^{16}O^{18}O}A_{20}h \nu f_u}{4 \pi D^2}
 
\end{equation}$$ $F_l$ is the 1$\sigma$ flux calculated from our images, $\mathcal{N}_{^{16}O^{18}O}$ is the number of $^{16}$O$^{18}$O molecules, $A_{20}=1.33\times10^{-8}$ s$^{-1}$ is the Einstein A coefficient of the $N_J=2_1-0_1$ transition (cite: Marechal1997), $\nu=233.94618$ GHz is the frequency of the $N_J=2_1-0_1$ transition, and $D=60.1$ pc is the distance to TW Hya (cite: BailerJones2018). The fraction of molecules in the upper state is given by $f_u = 3.0 \exp(-11.23$ K$/T) / Q(T)$, where 3 is the upper state degeneracy, 11.23 K is the upper state energy (cite: Marechal1997), $T_{\rm gas}$ is the gas temperature, and $Q(T)$ is the partition function from the JPL spectral line catalog (cite: Pickett1998; Mizushima1991; Crownover1990; Steinbach1975; Amano1974). These partition functions are given for temperatures ranging from 9.4 K to 300.0 K, so this is the temperature range we use in our calculations. To get an upper limit on the total number of $^{16}$O$^{16}$O molecules, we assumed a $^{16}$O$^{16}$O/$^{16}$O$^{18}$O ratio of 280 (cite: Taquet2018; Wilson1994). We obtained an upper limit of $(1.1-10.4)\times10^{49}$ O$_2$ molecules within 120 au, and $(1.4-13.2)\times10^{49}$ molecules within 260 au, for a temperature range of 9.4 K to 300.0 K.

To give our result context, we also estimate the disk-averaged abundance of O$_2$ relative to hydrogen. To estimate the total hydrogen mass in the disk, we adopt the disk mass reported in (cite: Calahan2021), but we note that there are a wide range of mass values for the TW Hya disk in the literature (cite: Miotello2022). We adopt the (cite: Calahan2021) value of $2.5\times10^{-2}$ M$_\odot$ since it uses the HD line and multiple CO isotopologues to constrain the temperature structure. Assuming a molecular mass per hydrogen molecule of 2.8 (cite: Kauffman2008), this equates to $2.1\times10^{55}$ hydrogen atoms in the whole disk. Within 120 au, we use the surface density profile from (cite: Calahan2021) to calculate a disk mass of $1.8\times10^{-2}$ M$_\odot$, which equates to $1.5\times10^{55}$ hydrogen atoms. Using these values, we estimate an O$_2$/H abundance of $(7.2-70)\times10^{-7}$ within 120 au, and $(6.4-62)\times10^{-7}$ within 260 au, for temperatures ranging from 9.4 K to 300.0 K. We will return to the implications of these results in Section [5](#sec:discussion).

## Constraints from Serendipitous Molecular Lines

The SO $N_J=5_6-4_5$ and SO$_2$ $N_J=4_{(2,2)}-3_{(1,3)}$ lines at 219.949 GHz and 235.152 GHz, respectively, were also included in the observational set-up. Given that these molecules might be prominent oxygen carriers, we searched for emission from these lines using similar techniques as for $^{16}$O$^{18}$O. Neither line was detected above $3\sigma$ with imaging or matched filtering (see Appendix [7](#appendix)). The disk integrated flux for the SO line is $-0.05 \pm 12.5$ mJy km s$^{-1}$ within 120 au and $-21.4 \pm 21.2$ mJy km s$^{-1}$ within 260 au (covering a range of 4.99 km s$^{-1}$). For SO$_2$, the flux is $24.4 \pm 14.8$ mJy km s$^{-1}$ within 120 au and $34.3 \pm 24.5$ mJy km s$^{-1}$ within 260 au (covering a range of 4.67 km s$^{-1}$). We modified Equation [\[eq1\]](#eq1) for SO and SO$_2$, using values from LAMDA (cite: Schoier2005) and CDMS (cite: Muller2001), and partition functions from the JPL spectral line catalog (cite: Pickett1998; Amano1974; Clark1976; Helminger1985; Lovas1985; Alekseev1996). We calculate a 1$\sigma$ upper limit of SO/H = $(2.4-10)\times10^{-13}$ within 120 au and $(2.9-12)\times10^{-13}$ within 260 au, and SO$_2$/H = $(7.9-197)\times10^{-13}$ within 120 au and $(9.1-229)\times10^{-13}$ within 260 au, for a temperature range of 9.4 K to 300.0 K.

We also report a serendipitous detection of the C$^{15}$N $N_J = 2_{5/2}-1_{3/2}$ hyperfine transitions, $F = 2 - 1$ and $F = 3 - 2$, at 219.93404 GHz and 219.93482 GHz, respectively. Using matched filtering with the 120 au Keplerian mask, we obtained a 7$\sigma$ filter response. The emission is visible in images (not shown), with an integrated flux of $113.5 \pm 17.0$ mJy km s$^{-1}$ for a range of 2.33 km s$^{-1}$, calculated within a 200 au circular region covering visible emission. For these images, we used Briggs weighting (robust = 2) and a uvtaper of 0.3 arcsec. The flux per channel is shown in Figure [4](#fig:c15n). C$^{15}$N has previously been detected in TW Hya through its $N = 3-2$ transition (cite: HilyBlant2017). They used two methods to calculate an integrated flux of $150 \pm 20$ mJy km s$^{-1}$ and $160 \pm 13$ mJy km s$^{-1}$, the first of which is consistent with our value.

![](c15n_1201.pdf)

# Discussion

How does O$_2$ stack up compared to other known oxygen carriers? Figure [5](#fig:uplim) shows our upper limits on O$_2$ abundance as a function of temperature, compared to the solar oxygen abundance and known abundances of other major oxygen-carrying species in the ISM and in TW Hya. Since CO and H$_2$O each contain one oxygen atom, their abundances relative to hydrogen can be directly compared to the solar oxygen abundance (e.g., if all oxygen were in CO, then the CO/H abundance would equal the O/H value). O$_2$, on the other hand, contains two oxygen atoms, so should be multiplied by two to compare with the solar oxygen abundance.

![](im_upperlim_0709.pdf)

In TW Hya, both CO gas and H$_2$O gas are several orders of magnitude below solar oxygen abundance; neither molecule is a major reservoir of oxygen. Our upper limit shows that gas-phase O$_2$ is also not a major carrier of oxygen. Other oxygen-carrying molecules that have been detected in TW Hya include HCO$^{+}$ (cite: vanDishoeck2003), H$_2$CO (cite: Oberg2017), CH$_3$OH (cite: Walsh2016), and HCOOH (cite: Favre2018), but these molecules were all detected at too low an abundance to complete the oxygen budget relative to solar values. The majority of oxygen in TW Hya has not been detected, leading to several possibilities, which we discuss further.

Our upper limits on gas-phase O$_2$ are not constraining enough to rule out protoplanetary disks as the origin of O$_2$ in comets, as water vapor in TW Hya is detected in low abundance (cite: Zhang2013). Comets 67P and 1P/Halley were observed to have high O$_2$/H$_2$O ratios of about 0.04 (cite: Bieler2015; Rubin2015), whereas our upper limits on gas-phase O$_2$ are about two orders of magnitude more abundant than detected water vapor in TW Hya (see Figure [5](#fig:uplim)).

One possibility for the low detections of gas-phase oxygen carriers is that oxygen is frozen out, so it cannot be detected easily. Due to the low temperatures of disks, we expect many molecules (like H$_2$O) to exist mostly in the ice-phase, but several processes can return molecules to the gas-phase throughout the entire disk. Photodesorption occurs when ultraviolet photons strike a molecule on the surface of a grain, causing the molecule to break off from the grain. It depends on the photon flux, as well as the binding energy of the molecule. (cite: Oberg2009) studied the photodesorption yield of H$_2$O and found that the main products are H$_2$O and OH. They also found that at high temperatures (100 K), up to $20\%$ of the ice desorbs as O$_2$. (cite: Du2017) searched for cold water vapor in 13 protoplanetary disks, only detecting it in low abundance in two disks, and in the stacked spectrum of four other disks. They model the disk chemistry and find that, to match observations, the abundance of gas-phase oxygen must be reduced by a factor of 100 or more. They propose that oxygen (in the form of H$_2$O and CO) freezes onto dust grains, which then settles to the midplane (cite: Hogerheijde2011; Bergin2016). This process primarily occurs in the outer disk; in the inner disk (within 15 au), temperatures are higher and frozen molecules may return to the gas phase. Grain size may also play a role in molecular abundances. (cite: Eistrup2022) modeled disk chemistry, taking into account grain size. They found that larger grain sizes result in a lower gas-phase O$_2$ abundance and a higher H$_2$O ice abundance, relative to the abundances produced using a fiducial 0.1$\mu$m grain size. As grain size increases, the surface area decreases, which decreases the number of grain surface-reactions and gas-grain interactions that can occur.

Another possibility is that there is a large amount of oxygen in gas-phase molecules that we have not yet observed. Overall, the most abundant molecules detected in comets are H$_2$O, CO$_2$, and CO (cite: Rubin2020). As discussed already, H$_2$O and CO have been detected in disks in low abundance. Models by (cite: Eistrup2018) predict CO$_2$/H abundances of up to $\approx10^{-4}$ in disks. CO$_2$ gas is difficult to observe in disks because, like O$_2$, it is symmetric and lacks a permanent dipole moment. CO$_2$ has been detected in the disk within 3 au of AA Tauri (cite: Carr2008), using Spitzer Space Telescope observations in the mid-infrared. JWST, however, can detect ice absorption features in the infrared, including CO$_2$ and H$_2$O ices, and is already providing insight into oxygen-carrying molecules in disks (cite: Yang2022; Grant2023; McClure2023).

# Conclusions

We searched for but did not detect emission from gas-phase $^{16}$O$^{18}$O in the protoplanetary disk around TW Hya. We used various imaging techniques along with matched filtering, and used our results to determine an upper limit on gas-phase O$_2$ in TW Hya.

- The isotopologue $^{16}$O$^{18}$O was not detected in TW Hya, leading to an upper limit on the abundance of O$_2$ of $(7.2-70)\times10^{-7}$ relative to H if the emission is contained within 120 au. For the whole disk, the upper limit is $(6.4-62)\times10^{-7}$. This limit is 2-3 orders of magnitude lower than the solar oxygen abundance, so gas-phase O$_2$ is not a major reservoir for oxygen in TW Hya. Taking into account other existing molecular detections in TW Hya, the main oxygen-carrier(s) remain undetected.

- We place sensitive upper limits on the SO and SO$_2$ lines at 219.949 GHz and 235.152 GHz, respectively. We calculated an upper limit of SO/H = $(2.4-10)\times10^{-13}$ within 120 au and $(2.9-12)\times10^{-13}$ within 260 au, and of SO$_2$/H = $(7.9-197)\times10^{-13}$ within 120 au and $(9.1-229)\times10^{-13}$ within 260 au. These results suggest oxygen is not bound up with sulfur either.

- We detect the isotopologue C$^{15}$N at the 7$\sigma$ level using matched filtering, and calculate an integrated flux of $113.5 \pm 17.0$ mJy km s$^{-1}$.

It is difficult to determine the main reservoir of oxygen in disks because of the many solid and gaseous forms oxygen may take (e.g. frozen H$_2$O, CO, CO$_2$; gas-phase O$_2$, CO$_2$). More observations of disks are necessary to search for this missing reservoir. Focusing on TW Hya, future searches for other gas-phase molecules, such as isotopologues of CO$_2$, would provide more insight on oxygen. Alternatively, searches for gas-phase $^{16}$O$^{18}$O in other disks, could prove interesting. Observations of ices, especially with JWST, will also be helpful.

# Acknowledgments

B.J.W. acknowledges support from the Virginia Initiative on Cosmic Origins (VICO). L.I.C. acknowledges support from the David and Lucile Packard Foundation, Research Corporation for Science Advancement Cottrell Fellowship, NASA ATP 80NSSC20K0529, NSF grant no. AST-2205698, and SOFIA Award 09-0183. C.E. acknowledges support from VICO. J.P.R. acknowledges support from the NASA Astrophysics Theory Program under grant no. 80NSSC20K0533, from the National Science Foundation (NSF) under grant nos. AST-1910106 and AST-1910675, and from the Virginia Initiative on Cosmic Origins. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01177.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# Facilities

ALMA

# Software

Astropy (cite: Astropy2013), CASA (cite: CASA2007), Keplerian Mask (cite: TeagueKepMask), VISIBLE (cite: LoomisVISIBLE)

# Matched Filter Results: Other Transitions

The matched filtering response for the data containing the SO$_2$ and SO transitions is shown in Figure [6](#fig:soso2). In both cases, the 120 au filter was used, and neither SO$_2$ nor SO were detected at the 3$\sigma$ level or above. The 7$\sigma$ peak at about 20 km s$^{-1}$ in the SO spectrum is the C$^{15}$N detection.

![](im_matfil_soso2_0419.pdf)

natexlab

(ref: Alekseev1996) Alekseev, E. A., Dyubko, S. F., Ilyushin, V. V., & Podnos, S. V. 1996, Journal of Molecular Spectroscopy, 176, 316, doi: [`10.1006/jmsp.1996.0092`](http://doi.org/10.1006/jmsp.1996.0092)

(ref: Amano1974) Amano, T., & Hirota, E. 1974, Journal of Molecular Spectroscopy, 53, 346, doi: [`10.1016/0022-2852(74)90071-X`](http://doi.org/10.1016/0022-2852(74)90071-X)

(ref: Ansdell2016) Ansdell, M., Williams, J. P., van der Marel, N., et al. 2016, ApJ, 828, 46, doi: [`10.3847/0004-637X/828/1/46`](http://doi.org/10.3847/0004-637X/828/1/46)

(ref: Asplund2021) Asplund, M., Amarsi, A. M., & Grevesse, N. 2021, A&A, 653, A141, doi: [`10.1051/0004-6361/202140445`](http://doi.org/10.1051/0004-6361/202140445)

(ref: Asplund2009) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481, doi: [`10.1146/annurev.astro.46.060407.145222`](http://doi.org/10.1146/annurev.astro.46.060407.145222)

(ref: Astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: BailerJones2018) Bailer-Jones, C. A. L., Rybizki, J., Fouesneau, M., Mantelet, G., & Andrae, R. 2018, AJ, 156, 58, doi: [`10.3847/1538-3881/aacb21`](http://doi.org/10.3847/1538-3881/aacb21)

(ref: Balsiger2007) Balsiger, H., Altwegg, K., Bochsler, P., et al. 2007, Space Sci. Rev., 128, 745, doi: [`10.1007/s11214-006-8335-3`](http://doi.org/10.1007/s11214-006-8335-3)

(ref: BerginCleeves2018) Bergin, E. A., & Cleeves, L. I. 2018, in Handbook of Exoplanets, ed. H. J. Deeg & J. A. Belmonte, 137, doi: [`10.1007/978-3-319-55333-7_137`](http://doi.org/10.1007/978-3-319-55333-7_137)

(ref: Bergin2016) Bergin, E. A., Du, F., Cleeves, L. I., et al. 2016, ApJ, 831, 101, doi: [`10.3847/0004-637X/831/1/101`](http://doi.org/10.3847/0004-637X/831/1/101)

(ref: Bergin2013) Bergin, E. A., Cleeves, L. I., Gorti, U., et al. 2013, Nature, 493, 644, doi: [`10.1038/nature11805`](http://doi.org/10.1038/nature11805)

(ref: Bieler2015) Bieler, A., Altwegg, K., Balsiger, H., et al. 2015, Nature, 526, 678, doi: [`10.1038/nature15707`](http://doi.org/10.1038/nature15707)

(ref: Briggs1995) Briggs, D. S. 1995, in American Astronomical Society Meeting Abstracts, Vol. 187, American Astronomical Society Meeting Abstracts, 112.02

(ref: Calahan2021) Calahan, J. K., Bergin, E., Zhang, K., et al. 2021, ApJ, 908, 8, doi: [`10.3847/1538-4357/abd255`](http://doi.org/10.3847/1538-4357/abd255)

(ref: Carr2008) Carr, J. S., & Najita, J. R. 2008, Science, 319, 1504, doi: [`10.1126/science.1153807`](http://doi.org/10.1126/science.1153807)

(ref: Clark1976) Clark, W. W., & De Lucia, F. C. 1976, Journal of Molecular Spectroscopy, 60, 332, doi: [`10.1016/0022-2852(76)90136-3`](http://doi.org/10.1016/0022-2852(76)90136-3)

(ref: Cleeves2015co) Cleeves, L. I., Bergin, E. A., Qi, C., Adams, F. C., & Öberg, K. I. 2015, ApJ, 799, 204, doi: [`10.1088/0004-637X/799/2/204`](http://doi.org/10.1088/0004-637X/799/2/204)

(ref: Crownover1990) Crownover, R. L., De Lucia, F. C., & Herbst, E. 1990, ApJL, 349, L29, doi: [`10.1086/185643`](http://doi.org/10.1086/185643)

(ref: Du2017) Du, F., Bergin, E. A., Hogerheijde, M., et al. 2017, ApJ, 842, 98, doi: [`10.3847/1538-4357/aa70ee`](http://doi.org/10.3847/1538-4357/aa70ee)

(ref: Dutrey1994) Dutrey, A., Guilloteau, S., & Simon, M. 1994, A&A, 286, 149

(ref: Eistrup2022) Eistrup, C., Cleeves, L. I., & Krijt, S. 2022, A&A, 667, A121, doi: [`10.1051/0004-6361/202243981`](http://doi.org/10.1051/0004-6361/202243981)

(ref: Eistrup2018) Eistrup, C., Walsh, C., & van Dishoeck, E. F. 2018, A&A, 613, A14, doi: [`10.1051/0004-6361/201731302`](http://doi.org/10.1051/0004-6361/201731302)

(ref: Favre2013) Favre, C., Cleeves, L. I., Bergin, E. A., Qi, C., & Blake, G. A. 2013, ApJL, 776, L38, doi: [`10.1088/2041-8205/776/2/L38`](http://doi.org/10.1088/2041-8205/776/2/L38)

(ref: Favre2018) Favre, C., Fedele, D., Semenov, D., et al. 2018, ApJL, 862, L2, doi: [`10.3847/2041-8213/aad046`](http://doi.org/10.3847/2041-8213/aad046)

(ref: Goldsmith2011) Goldsmith, P. F., Liseau, R., Bell, T. A., et al. 2011, ApJ, 737, 96, doi: [`10.1088/0004-637X/737/2/96`](http://doi.org/10.1088/0004-637X/737/2/96)

(ref: Grant2023) Grant, S. L., van Dishoeck, E. F., Tabone, B., et al. 2023, ApJL, 947, L6, doi: [`10.3847/2041-8213/acc44b`](http://doi.org/10.3847/2041-8213/acc44b)

(ref: Helminger1985) Helminger, P. A., & De Lucia, F. C. 1985, Journal of Molecular Spectroscopy, 111, 66, doi: [`10.1016/0022-2852(85)90069-4`](http://doi.org/10.1016/0022-2852(85)90069-4)

(ref: HilyBlant2017) Hily-Blant, P., Magalhaes, V., Kastner, J., et al. 2017, A&A, 603, L6, doi: [`10.1051/0004-6361/201730524`](http://doi.org/10.1051/0004-6361/201730524)

(ref: Hogerheijde2011) Hogerheijde, M. R., Bergin, E. A., Brinch, C., et al. 2011, Science, 334, 338, doi: [`10.1126/science.1208931`](http://doi.org/10.1126/science.1208931)

(ref: Huang2018) Huang, J., Andrews, S. M., Cleeves, L. I., et al. 2018, ApJ, 852, 122, doi: [`10.3847/1538-4357/aaa1e7`](http://doi.org/10.3847/1538-4357/aaa1e7)

(ref: Kauffman2008) Kauffmann, J., Bertoldi, F., Bourke, T. L., Evans, N. J., I., & Lee, C. W. 2008, A&A, 487, 993, doi: [`10.1051/0004-6361:200809481`](http://doi.org/10.1051/0004-6361:200809481)

(ref: Liseau2012) Liseau, R., Goldsmith, P. F., Larsson, B., et al. 2012, A&A, 541, A73, doi: [`10.1051/0004-6361/201118575`](http://doi.org/10.1051/0004-6361/201118575)

(ref: Long2017) Long, F., Herczeg, G. J., Pascucci, I., et al. 2017, ApJ, 844, 99, doi: [`10.3847/1538-4357/aa78fc`](http://doi.org/10.3847/1538-4357/aa78fc)

(ref: Loomis2018) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2018a, AJ, 155, 182, doi: [`10.3847/1538-3881/aab604`](http://doi.org/10.3847/1538-3881/aab604)

(ref: LoomisVISIBLE) Loomis, R. A., Oberg, K. I., Andrews, S. M., et al. 2018b, VISIBLE: VISIbility Based Line Extraction, Astrophysics Source Code Library, record ascl:1802.006. [`http://ascl.net/1802.006`](http://ascl.net/1802.006)

(ref: Loomis2020) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2020, ApJ, 893, 101, doi: [`10.3847/1538-4357/ab7cc8`](http://doi.org/10.3847/1538-4357/ab7cc8)

(ref: Lovas1985) Lovas, F. J. 1985, Journal of Physical and Chemical Reference Data, 14, 395, doi: [`10.1063/1.555729`](http://doi.org/10.1063/1.555729)

(ref: LuspayKuti2018) Luspay-Kuti, A., Mousis, O., Lunine, J. I., et al. 2018, Space Sci. Rev., 214, 115, doi: [`10.1007/s11214-018-0541-2`](http://doi.org/10.1007/s11214-018-0541-2)

(ref: LuspayKuti2022) Luspay-Kuti, A., Mousis, O., Pauzat, F., et al. 2022, Nature Astronomy, 6, 724, doi: [`10.1038/s41550-022-01614-1`](http://doi.org/10.1038/s41550-022-01614-1)

(ref: Marechal1997) Marechal, P., Viala, Y. P., & Pagani, L. 1997, A&A, 328, 617

(ref: McClure2023) McClure, M. K., Rocha, W. R. M., Pontoppidan, K. M., et al. 2023, Nature Astronomy, 7, 431, doi: [`10.1038/s41550-022-01875-w`](http://doi.org/10.1038/s41550-022-01875-w)

(ref: McGuire2022) McGuire, B. A. 2022, ApJS, 259, 30, doi: [`10.3847/1538-4365/ac2a48`](http://doi.org/10.3847/1538-4365/ac2a48)

(ref: CASA2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Miotello2022) Miotello, A., Kamp, I., Birnstiel, T., Cleeves, L. I., & Kataoka, A. 2022, arXiv e-prints, arXiv:2203.09818. [`https://arxiv.org/abs/2203.09818`](https://arxiv.org/abs/2203.09818)

(ref: Mizushima1991) Mizushima, M., & Yamamoto, S. 1991, Journal of Molecular Spectroscopy, 148, 447, doi: [`10.1016/0022-2852(91)90400-5`](http://doi.org/10.1016/0022-2852(91)90400-5)

(ref: Muller2001) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49, doi: [`10.1051/0004-6361:20010367`](http://doi.org/10.1051/0004-6361:20010367)

(ref: Oberg2009) Öberg, K. I., Linnartz, H., Visser, R., & van Dishoeck, E. F. 2009, ApJ, 693, 1209, doi: [`10.1088/0004-637X/693/2/1209`](http://doi.org/10.1088/0004-637X/693/2/1209)

(ref: Oberg2017) Öberg, K. I., Guzmán, V. V., Merchantz, C. J., et al. 2017, ApJ, 839, 43, doi: [`10.3847/1538-4357/aa689a`](http://doi.org/10.3847/1538-4357/aa689a)

(ref: Pickett1998) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883, doi: [`10.1016/S0022-4073(98)00091-0`](http://doi.org/10.1016/S0022-4073(98)00091-0)

(ref: Przybilla2008) Przybilla, N., Nieva, M.-F., & Butler, K. 2008, ApJL, 688, L103, doi: [`10.1086/595618`](http://doi.org/10.1086/595618)

(ref: Ripple2013) Ripple, F., Heyer, M. H., Gutermuth, R., Snell, R. L., & Brunt, C. M. 2013, MNRAS, 431, 1296, doi: [`10.1093/mnras/stt247`](http://doi.org/10.1093/mnras/stt247)

(ref: Rubin2015) Rubin, M., Altwegg, K., van Dishoeck, E. F., & Schwehm, G. 2015, ApJL, 815, L11, doi: [`10.1088/2041-8205/815/1/L11`](http://doi.org/10.1088/2041-8205/815/1/L11)

(ref: Rubin2020) Rubin, M., Engrand, C., Snodgrass, C., et al. 2020, Space Sci. Rev., 216, 102, doi: [`10.1007/s11214-020-00718-2`](http://doi.org/10.1007/s11214-020-00718-2)

(ref: Salinas2017) Salinas, V. N., Hogerheijde, M. R., Mathews, G. S., et al. 2017, A&A, 606, A125, doi: [`10.1051/0004-6361/201731223`](http://doi.org/10.1051/0004-6361/201731223)

(ref: Schoier2005) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369, doi: [`10.1051/0004-6361:20041729`](http://doi.org/10.1051/0004-6361:20041729)

(ref: Steinbach1975) Steinbach, W., & Gordy, W. 1975, , 11, 729, doi: [`10.1103/PhysRevA.11.729`](http://doi.org/10.1103/PhysRevA.11.729)

(ref: Taquet2018) Taquet, V., van Dishoeck, E. F., Swayne, M., et al. 2018, A&A, 618, A11, doi: [`10.1051/0004-6361/201833175`](http://doi.org/10.1051/0004-6361/201833175)

(ref: TeagueKepMask) Teague, R. 2020, richteague/keplerian_mask: Initial Release, 1.0, Zenodo, doi: [`10.5281/zenodo.4321137`](http://doi.org/10.5281/zenodo.4321137)

(ref: Teague2019) Teague, R., Bae, J., Huang, J., & Bergin, E. A. 2019, ApJL, 884, L56, doi: [`10.3847/2041-8213/ab4a83`](http://doi.org/10.3847/2041-8213/ab4a83)

(ref: Teague2022) Teague, R., Bae, J., Andrews, S. M., et al. 2022, ApJ, 936, 163, doi: [`10.3847/1538-4357/ac88ca`](http://doi.org/10.3847/1538-4357/ac88ca)

(ref: vanDishoeck2013) van Dishoeck, E. F., Herbst, E., & Neufeld, D. A. 2013, Chemical Reviews, 113, 9043, doi: [`10.1021/cr4003177`](http://doi.org/10.1021/cr4003177)

(ref: vanDishoeck2003) van Dishoeck, E. F., Thi, W. F., & van Zadelhoff, G. J. 2003, A&A, 400, L1, doi: [`10.1051/0004-6361:20030091`](http://doi.org/10.1051/0004-6361:20030091)

(ref: vanDishoeck2021) van Dishoeck, E. F., Kristensen, L. E., Mottram, J. C., et al. 2021, A&A, 648, A24, doi: [`10.1051/0004-6361/202039084`](http://doi.org/10.1051/0004-6361/202039084)

(ref: Walsh2015) Walsh, C., Nomura, H., & van Dishoeck, E. 2015, A&A, 582, A88, doi: [`10.1051/0004-6361/201526751`](http://doi.org/10.1051/0004-6361/201526751)

(ref: Walsh2016) Walsh, C., Loomis, R. A., Öberg, K. I., et al. 2016, ApJL, 823, L10, doi: [`10.3847/2041-8205/823/1/L10`](http://doi.org/10.3847/2041-8205/823/1/L10)

(ref: Whittet2010) Whittet, D. C. B. 2010, ApJ, 710, 1009, doi: [`10.1088/0004-637X/710/2/1009`](http://doi.org/10.1088/0004-637X/710/2/1009)

(ref: Wilson1994) Wilson, T. L., & Rood, R. 1994, ARA&A, 32, 191, doi: [`10.1146/annurev.aa.32.090194.001203`](http://doi.org/10.1146/annurev.aa.32.090194.001203)

(ref: Yang2022) Yang, Y.-L., Green, J. D., Pontoppidan, K. M., et al. 2022, ApJL, 941, L13, doi: [`10.3847/2041-8213/aca289`](http://doi.org/10.3847/2041-8213/aca289)

(ref: Zhang2013) Zhang, K., Pontoppidan, K. M., Salyk, C., & Blake, G. A. 2013, ApJ, 766, 82, doi: [`10.1088/0004-637X/766/2/82`](http://doi.org/10.1088/0004-637X/766/2/82)

</paper>

Write the methods card for this paper.