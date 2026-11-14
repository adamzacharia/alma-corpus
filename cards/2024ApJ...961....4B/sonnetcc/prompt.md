# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...961....4B\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...961....4B",
 "title": "Protostellar Cores in Sagittarius B2 N and M",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Budaiev, Nazar",
 "n_authors": 9,
 "arxiv_id": "2309.14407",
 "doi": "10.3847/1538-4357/ad0383",
 "alma_projects_linked_by_archive": [
  "2013.1.00269.S",
  "2016.1.00550.S"
 ]
}
```

Paper text:
<paper>
# Protostellar cores in Sagittarius B2 N and M

## Abstract

We present 500 AU and 700 AU resolution 1 mm and 3 mm ALMA observations, respectively, of protostellar cores in protoclusters Sagittarius B2 (Sgr B2) North (N) and Main (M), parts of the most actively star-forming cloud in our Galaxy. Previous lower resolution (5000 AU) 3 mm observations of this region detected $\sim$150 sources inferred to be young stellar objects (YSOs) with $M>8M\ensuremath{_\odot}$. With a tenfold increase in resolution, we detect 371 sources at 3 mm and 218 sources in the smaller field of view at 1 mm. The sources seen at low resolution are observed to fragment into an average of two objects. About a third of the observed sources fragment. Most of the sources we report are marginally resolved and are at least partially optically thick. We determine that the observed sources are most consistent with Stage 0/I YSOs, i.e., rotationally supported disks with an active protostar and an envelope, that are warmer than those observed in the solar neighborhood. We report source-counting-based inferred stellar mass and the star formation rate of the cloud: 2800M$_\odot$, 0.0038M$_\odot$ yr$^{-1}$ for Sgr B2 N and 6900M$_\odot$, 0.0093M$_\odot$ yr$^{-1}$ for Sgr B2 M respectively.

# Introduction

Many stars in our Galaxy were formed around cosmic noon (cite: Madau2014) under conditions rarely seen today. To study the conditions under which an average Galactic star formed, we need to identify star-forming regions which are analogous to those present during cosmic noon. One such local environment analogue is present in the high-density, turbulent, and overall extreme Central Molecular Zone (cite: Henshaw2022). This is the only environment with such conditions where we can resolve disk scales (cite: Lu2022).

The distribution of stellar masses, the initial mass function (IMF), is one outcome of star formation that may change under extreme gas conditions. In young star clusters near the center of the Galaxy, such as the Arches and Quintuplet, there is evidence of a top-heavy IMF (cite: Hosek2019a; Gallego-Calvente2022). By peering into early stages of star formation in the CMZ, we will investigate whether the IMF varies systematically with local environment (cite: Li2023) and is thus shallower in the early universe (cite: Zhang2018). In this work, we examine the most actively star-forming cloud in the CMZ – Sagittarius B2 (Sgr B2). Through investigating dust structures at $<1000$ AU scales, we can probe the core mass function – the precursor to the IMF.

The Galactic Center is located at a distance of $8.127\pm0.031$ kpc (cite: GRAVITYCollaboration2018) and Sgr B2 is $\sim$100 pc away from the Galactic Center in projection. Throughout this paper, we assume a distance to Sgr B2 of 8.4 kpc to remain consistent with the similar work by (cite: Ginsburg2018). The molecular cloud is split into several smaller, concentrated regions of star formation: North (N), Main (M), South (S), and Deep South (DS). A large fraction ($\sim$25-50%) of the current star formation in this cloud occurs in the N and M regions, with many stars forming in bound clusters (cite: Ginsburg2018; Schmiedeke2016). Half of the total star formation in the CMZ occurs in Sgr B2, despite containing $\sim$10% of the mass ($8 \times 10^6$M$_\odot$) and $<1\%$ of the volume (cite: Ginsburg2018; Barnes2017; Schmiedeke2016).

Sgr B2 appears to be forming stars preferentially in dense, bound clusters (cite: Ginsburg2018; Ginsburg2018CFE). Since other Galactic Center star clusters have excesses of high-mass stars (cite: Hosek2019a; Gallego-Calvente2022), Sgr B2 is likely also forming extra massive stars. 3500 AU resolution observations towards Sgr B2 N and M suggest the presence of an excess of massive stars in the region (cite: Sanchez-Monge2017). If this excess is present, it indicates a systematic variation of the stellar IMF with gas conditions, with a shallower IMF under conditions prevalent in galaxies with rapid star formation.

We report follow-up ALMA observations to ALMA project 2013.1.00269.S, which covered a $15\times15$ pc area around the Sgr B2 complex at 3 mm (cite: Ginsburg2018) with $\sim$5000 AU resolution. Our data covers Sgr B2 N and M at 3 mm and at 1 mm. We establish the possible nature and evolutionary stage of the sources. We place lower limits on cores’ masses in the attempt to understand whether the core mass function is top-heavy in young cluster and varies with the surrounding conditions.

In Section [2](#sec:data) we describe the observations, imaging, and self-calibration procedures. We then explain the source extraction approach in Section [3](#sec:analysis), make a comparison with previous low-resolution observations, and explain the way the spectral index was calculated between 3 mm and 1 mm. In Section [4](#sec:disc) we show that our sources are consistent with Stage 0/I YSOs by ruling out other possible options. We also present calculations of the inferred stellar mass of the cloud and the star formation rate and present the multiplicity function. The paper is summarized in Section [5](#sec:sum). In the appendices we quantify the line contribution to the continuum images, discuss the details of cleaning and self-calibration, and present the radial core distribution for each protocluster.

# Observations and data reduction

This paper utilizes the data from ALMA Cycle 4 project 2016.1.00550.S. The observations consist of two pointings centered on Sgr B2 N (ICRS 17:47:19.925; -28:22:18.608) and Sgr B2 M (ICRS 17:47:20.174; -28:23:04.788) with the 12m antennas. Both locations were observed in Band 3 and Band 6 with resolution of 0.096" $\times$ 0.073" ($\sim$700 AU) and 0.083" $\times$ 0.038" ($\sim$500 AU), respectively. The pointings cover $6.5\times4.5$ pc at 3 mm and roughly $1.75\times3.75$ pc at 1 mm out to primary beam level of 0.1. The spectral setup for each Band consists of 4 spectral windows with 1920 channels each and channel frequency width of 976.6 kHz (1.875 GHz bandwidth), which corresponds to spectral resolution of $\sim$1.3 km/s at 226 GHz and $\sim$3.2 km/s at 92 GHz. The central spectral window frequencies are 217.84, 219.79, 231.80, and 233.67 GHz for Band 6 and 85.47, 87.37, 97.42, and 99.42 GHz for Band 3.

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Central frequency | Date | $t_{science}$ | Baseline length range | \# of antennas |
| GHz |  | seconds | meters |  |
| 92.45 | 18-Sep-2017 | 2642 | 41-12100 | 43 |
| 92.45 | 18-Sep-2017 | 2644 | 41-12100 | 43 |
| 225.76 | 07-Sep-2017 | 2977 | 41-7600 | 46 |
| 225.76 | 16-Sep-2017 | 2973 | 41-12100 | 46 |

The data were imaged using CASA version 5.7.0-134.el7 `tclean` with robust parameter set to 0.5 (cite: McMullin2007). We found that for the majority of sources the line contribution was insignificant and thus no line subtraction or flagging was performed. We measure the contribution of emission and absorption lines in Appendix [6](#sec:line_sub). Each of the four pointings were imaged separately. Despite the overlap between the Band 3 pointings, we used the standard gridder instead of the mosaic gridder. A detailed explanation of the imaging choices is presented in Appendix [7.2](#sec:imaging).

The initial cleaned images contained many imaging artifacts, such as radial streaks, circular patterns, and parallel “wavy" streaks. Therefore, we decided to self-calibrate the data to improve the quality of the final image. We made sure that the phase self-calibration does not introduce spatial shifts and amplitude self-calibration does not change the flux erroneously. A detailed explanation of the tested approaches is presented in Appendix [7](#sec:testing). In summary, our standard self-calibration procedure consisted of the following steps:

1.  Use one of the fully calibrated images from prior testing to estimate the lowest noise in the image. We measured the RMS in a box around an emission-free region close to the center of the image.

2.  Use the same previously cleaned image to create a “strict" contour mask at six-$\sigma$ threshold.

3.  Using the same image, draw a “broad" mask that covers all regions where signal is present, even if it includes some artifacts or noise.

4.  Clean the image with the `tclean` threshold parameter set to six times the noise from step 1, and using the “strict" mask from step 2.

5.  Complete a phase self-calibration with `solint` set to `inf`.

6.  Repeat the clean from step 4.

7.  Self-calibrate the image with `solint` set to `int`.

8.  Clean the image with the `tclean` threshold parameter set to three times the noise from step 1 and using the “broad" mask from step 3.

9.  Complete a round of phase and amplitude self-calibration with `solint` set to `inf`.

10. Repeat the clean from step 8.

However, some of the fields required further tuning to achieve better results. The Sgr B2 N Band 6 pointing suffered from divergence at the selected threshold values. Thus, we opted to increase the cleaning threshold up to ten times the noise until the amplitude self-calibration step was completed. After, we cleaned to three times the noise and added an extra amplitude and phase self-calibration step with `solint` set to 15 s, which we found to produce the best results. The extra self-calibration step improved the image significantly. Running this extra self-calibration step on the other pointings did not reduce the noise in the images. The Sgr B2 N Band 3 pointing did not benefit from the amplitude self-calibration step and introduced additional minor artifacts. Thus, we used the pre-amplitude-self-calibration image for our analysis. The final images for each Band are shown in Figures [1](#fig:B3) and [2](#fig:B6). The FITS files of the self-calibrated data were published in a Zenodo repository at [doi:10.5281/zenodo.8377186](https://doi.org/10.5281/zenodo.8377186).

The final average RMS in an emission-free region close to the center the image for each of the pointings is 0.033 mJy for N Band 3, 0.05 mJy for M Band 3, 0.35 mJy for N Band 6, and 0.25 mJy for M Band 6. The RMS measurements for each calibration step are presented in Table [1](#tab:RMS).

![](B3_image_full_K.png)

![](B6_image_full_K.png)

# Analysis

## Source extraction

We strove to make the catalog as reproducible as possible, while minimizing the number of false positives. Automating source extraction presents numerous problems in a region like Sgr B2. The images have high dynamic range ($\sim$5000), contain complex extended structures, and like all interferometric single-pointing data, have radially varying noise. Combining this with the irregular structure of the observed objects makes fully automated source detection inefficient. Therefore, we utilized the automated source-finding dendrogram algorithm (cite: Rosolowsky2008) augmented with a by-hand approach described below.

The imaged areas of Band 3 fields have a slight overlap. Since the noise is not uniform and has structure depending on the location relative to the center of the pointing, we crop the overlapping parts instead of weighted averaging. The cut was made close to equidistant from the centers of the pointing, while not breaking up any regions with signal – just south of (below) region Sgr B2 Z10.24. Band 6 images do not overlap and thus do not require cropping. We divide each primary-beam corrected image in 30 concentric annuli out to the edge of the image, primary beam response of 0.1, and a circle at the center. The width of the concentric annuli is $\sim$$7.8$$''$ and $1.1''$ for Band 3 and Band 6 respectively. We then use 7-sigma clipping to remove most of the signal from each of the annuli and calculate the standard deviation for each region. This noise measurement is then used as `astrodendro` input parameters.

The central part of the pointings are signal-dominated, which, even after sigma clipping, results in a higher measured noise. The calculated noise as a function of radius rapidly drops beyond the central clusters and then gradually increases due to primary beam attenuation. We replace the estimated noise of the central part of the pointing with the lowest calculated value in the whole image such that the noise never decreases with radius.

Then, we perform source detection on the primary-beam-corrected images using the `astrodendro` source-finding algorithm. Because of the extremely bright emission at the center of the pointings, the central region of the image is dominated by artifacts. Thus, the noise is not uniform in the non-primary-beam-corrected images. We generate a separate dendrogram for each concentric annulus using noise estimation for input parameters. We run the dendrogram on the full image and then exclude any sources with centers outside of the annulus. We set *min_value* to be equal to four times the noise estimate, *min_delta* to be 0.7 times the estimated noise, and *min_npix* to be 3 pixels.[^1] The final source extraction thresholds are $\sim$0.15 mJy at 3 mm and $\sim$1.2 mJy at 1 mm within the inner 40% of the observed area, and $\sim$0.5 mJy at 3 mm and $\sim$4 mJy at 1 mm within the inner 90% of the imaged area. The exact values can be found in Table [1](#tab:RMS).

We then closely examine by eye parts of the image that contain extended structure and no compact emission, primarily regions. We draw polygons[^2] around these locations by hand so that any detections within them can be excluded. In a few cases, we found core-like sources within the regions. We drew the polygons in a way that would include such sources in the final catalog.

Finally, we review each of the cataloged sources in both pointings and frequencies by hand. We rank every source as not-a-core (0), core candidate (1), or core (2). We inspect each source twice: first, zoomed-in closely to examine the shape and the background features and then using the whole image to get context on the source morphology based on location and proximity to other sources.

For example, if a source with a score of 1 that resembles a filamentary structure is located close to an area with extended emission, such as an region, we mark it as a false detection and adjust the score accordingly. If such a source is located in a cluster of other sources with a score of 2 and is not visibly a part of any extended structure, we change its score to 2. We further investigate each source with a score of 1 by comparing their structure in the 1 mm and 3 mm data. If a potential source is part of a filamentary structure at 3 mm, but no local peak is observed at 1 mm, we score such a source as a 0. Such a filamentary structure at 3 mm without a strong counterpart at 1 mm is indicative of free-free emission.

All of the extended regions are excluded manually using polygons as described above. In addition, we cross-match our detections with (cite: DePree1998) and (cite: Meng2022) to remove known compact regions from our core sample and label them as known regions. We find that VLA-detected regions do not perfectly align with region candidates in our data, especially in Sgr B2 M: our sources are generally located at a greater declination. The most likely cause is the wrong positional coordinates of the phase calibrator J1744-3116 in VLA catalogs. When compared to other catalogs (cite: Lanyi2010), the location of J1744-3116 is offset by $\sim$0.29$''$ primarily in declination. The erroneous coordinates of the VLA phase calibrator has likely affected many of the previous observations of Sgr B2.

When it is not possible to establish a confident one-to-one match between catalogs, we label the source as an region candidate. Some of the previously known regions appear to have multiple peaks within their areas. We label these “fragmented" sources as region candidates.

To further identify regions based on their spectral properties, we create a 1 mm to 3 mm spectral index map of the central, most dense parts of Sgr B2 N and M. We find that the central region of the Sgr B2 M, being more evolved compared to Sgr B2 N, has spectral indexes close to 0, which is typical for optically thin regions. Considering the high density of regions in the same area described in (cite: Schmiedeke2016) we mark all previously uncategorized sources in the close vicinity of region candidates and give them a score of 0. Only a few sources are removed in Sgr B2 N with this method due to the high error values of the spectral index map in the region. We label the sources that morphologically resemble regions (e.g. a source with a dim center but bright edges) as region candidates. Finally, we mark sources that are extremely bright at 3 mm as region candidates. Every region candidate that is not a previously known region, cannot be assigned to a previously known region

, and is not a part of a “fragmented" known region is marked as a new region detection. In total, our catalog contains 17 known hyper-compact and ultra-compact regions, 16 region candidates, and 8 new hyper-compact regions. 5 of the new regions are detected due to increase in resolution compared to VLA-based observations. The other 3 new regions are located within Sgr B2(N)-SMA2 hot core (cite: Qin2011).

Having two criteria for core identification, strict and lax, allows for separate “robust" and “complete" catalogs to co-exist. We note that the difference between a score of 1 and 2 is subjective. After performing the analysis described in the following section, we do not find any significant differences when comparing the results between the two catalogs. Thus, we report and use only the “complete" catalog in the rest of this work. Our catalog contains 371 cores at 3 mm and 218 cores at 1 mm, of which 179 have a 3 mm counterpart. Thus, the total number of individual cores identified at at least one wavelength is 410.

The described approach has some caveats. Even after extensive self-calibration and cleaning, the data still include local artifacts such as negative bowls around bright sources and wave-like patterns on different scales. The high source density and the presence of extended emission (e.g. Figure [3](#fig:zoomin)), complicates the estimation of the local noise for each source.

![](zoom_in.png)

Excluding detections within polygons that were drawn by eye can potentially exclude true positives. While it is unlikely for cores to be present inside regions, they might appear to be so due to projection effects. Less than a few percent of the total pointing area is excluded by the polygons. Potentially missed sources should not affect the conclusions of this paper as there would be no biases for the excluded sources.

## Photometry

We use the integrated flux within the dendrogram structure contour and the brightest pixel within the contour as the primary observables. We present the two measurements of source flux in the catalog, a sample of which is shown in Table [2](#tab:catalog). The full catalog is available in machine-readable format. The source brightness temperatures are shown in Figure [4](#fig:brightness_T) as a cumulative distribution function (CDF). The total source flux is the sum of the pixel values in Jy in the dendrogram-defined contour referred to as a “leaf". The peak is the value of the brightest pixel in Jy/beam. These numbers are expected to be the same for a point source and the peak-derived value should be smaller for a resolved source. Dendrogram-based flux underestimates the flux of the very faint sources because the lowest possible contour is set at a given threshold level, in our case 4$\sigma$.

![](brightness_T.png)

During testing, we attempted to perform 2D Gaussian photometry using the `gaussfit_catalog` python package. We inspected each fit by hand and found that fewer than 10% of the sources had a satisfactory fit for the central object. We found that many of the fits were affected by the presence of non-uniform extended envelopes around the centrally peaked sources, like in Figure [3](#fig:zoomin). Furthermore, high source density and imaging artifacts also contributed to some of the failed fits. Thus, we concluded that our sources are not well-represented by simple 2D Gaussians and decided to use dendrogram contours to define sources.

### Photometry comparison

As a part of Cycle 2 ALMA project 2013.1.00269.S, (cite: Ginsburg2018) obtained Band 3 observations of the extended Sgr B2 cloud at 0.5" resolution.

![](2018vs2022.png)

We investigate the impact of the differences between ours and G18 observations. Compared to G18, the catalog derived in this work has a factor of 10 better spatial resolution and is a factor of two more sensitive. The distribution of source fluxes is shown in Figure [5](#fig:fluxes). The data from G18 were centered at 96.36 GHz with each of the four spectral windows having a bandwidth of 1.875 GHz, while our observations are centered at 92.45 GHz with four spectral windows of the same bandwidth. Since the central frequencies of the data are not the same, we perform a frequency correction. Assuming that the majority of the flux within the G18 beam is coming from the optically thick part of the core or an region and it has an average spectral index of two, the frequency correction factor is $\sim$0.92. For a positive spectral index, the flux measured from our data within the defined aperture is expected to be dimmer. Depending on the source, the correction factor can range from 1.05 at spectral index of -1 to 0.87 at spectral index of 3.5 which would correspond to about 15% flux correction error. As shown in Section [3.4](#sec:spectral_indexes), many of the cataloged sources have spectral indexes between 2 and 3.

We compare our and G18 images by performing aperture photometry on G18 data. We apply an elliptical aperture equivalent to 1-$\sigma$ of the G18 Gaussian beam (0.230" $\times$ 0.197") on the locations of G18 detections on our data and compare it to the “peak" (brightest pixel) flux from G18. However, an elliptical aperture does not capture all the flux counted in the brightest pixel of an unresolved source. While the brightest pixel is representative of the sum of the Gaussian distribution of the signal, an elliptical aperture cuts off the edges of the distribution. We calculate the aperture correction factor as the fraction of the Gaussian distribution that is cut off after using a 1-$\sigma$-sized aperture to be 1.465. Finally, we convert the summed flux from Jy/beam to Jy. We compare this quantity with the brightest pixel of G18 sources. The ratio of flux at the location of each G18 source is shown in Figure [6](#photometry). There is a slight trend of higher-resolution sources having less flux. A smaller fraction of sources are above the line. Low-flux sources exhibit larger scatter, which is consistent with measured noise. The somewhat large scatter can be partially explained by the presence of imaging artifacts in the images, primarily negative bowls. All data points with flux ratio of over 10 are due to negative bowls in the high-resolution data..

![](photometry.png)

## Source sizes

![](source_size.png)

For each source we recorded the total flux within the dendrogram object contour and the brightest pixel value within the contour. If a source is not resolved, then the brightest pixel should contain all the flux from the source. If a source is resolved, the brightest pixel will contain only part of the flux. Thus, we use a ratio of brightest pixel flux and summed flux within dendrogram structure to serve as a metric of whether a source is resolved or not. As shown in Figure [7](#source_size), we find that $20\%$ of 1 mm and $30\%$ of 3 mm sources have effective areas smaller than the beam area and peak flux larger than the dendrogram contour flux, which means that the sources are unresolved. On the other hand, only a handful of sources are more than two resolution elements across – 23 sources at 1 mm and 8 sources at 3 mm are well resolved.

The sources with $S_{peak} / S_{contour}$ $<$ 1 and dendrogram contour area larger than the beam size are marginally resolved. There are 45$\%$ of such sources at each wavelength.

## Spectral indexes

In order to measure the spectral indexes, we need to convolve the data to a common beam. The common beam between the two bands is equivalent to the Band 3 beam. Thus, we convolve the Band 6 data to the Band 3 beam, accounting for the beam area change as our data are in units of Jy/beam. To calculate the spectral index, we take the brightest pixel values for detections at 3 mm and take the corresponding positions on the sky at 1 mm. The brightest pixel contains information about at least the inner, most dense part of the source in its 2D projection. The mean offset between the locations of the brightest pixels at 3 mm and 1 mm is less than a quarter of the beam, which is equivalent to $\sim$1 pixel and is never more than one common beam apart. We find that using the 1 mm data’s brightest pixel locations produces very similar individual measurements, much less than the calculated errors. We check for systematic errors that could be caused by this approach and find no trends in the measurements of the two distributions. In addition to calculating spectral indexes for sources present in both bands, we are also able to place upper and lower limits for sources detected only at 3 mm and 1 mm respectively. We show the distribution of spectral indexes with the corresponding source fluxes in Figure [8](#fig:SI), indicating physical and observational constraints.

We calculate the spectral index errors only for sources with SNR over 10 in both bands. For sources with SNR below 10 in either band, the errorbars are not necessarily representative of the uncertainty because the error distribution function is no longer Gaussian (the distribution function for the ratio of two Gaussians with mean zero is a Cauchy distribution, for which the standard deviation and mean are undefined). We therefore show data points without error bars for these sources in Figure [8](#fig:SI). All sources in our catalog have the SNR $>$ 4.

Convolving Band 6 data to the common beam decreases the SNR for compact sources. To maximize the number of included Band 6 sources, we perform the 10$\sigma$ and 4$\sigma$ cuts based on the original SNR. We then use convolved data to calculate individual source uncertainties.

We investigated whether we could use the alpha-maps produced by the `tclean` algorithm to estimate the in-band spectral indexes. Fewer than a dozen sources had errors below $50\%$. Thus, our data is not sensitive enough to produce in-band spectral indexes.

We explore the potentially misclassified sources in our catalog. The “core" classification was done based on the morphology, proximity to other sources, relative brightness, and surrounding emission. The spectral index values can then be used to identify potential catalog contaminants such as regions. As shown in Figure [9](#fig:SI_hist), there are five sources that have statistically significant spectral indexes below 2, which are probably misclassified regions.

![](SI_hist.png)

However, at least three of these sources are located in the negative bowls in Band 6 data. Since our cataloged fluxes are not background subtracted, being located in the negative bowl causes a lower 1 mm flux and underestimates the spectral index. Similarly, being located in a negative bowl at 3 mm artificially increases the spectral index. A known region Sgr B2 F10.30 is the most prominent example of a source in a 3 mm negative bowl, having $\alpha$ = 2.7. Thus, some of the detections near negative bowls might have been misclassified; as shown in Figure [8](#fig:SI), there are some region candidates that have $\alpha >$ 2 and cores with $\alpha < 2$. Fewer than 1% of sources are located in a of negative bowl.

We also note that just above 60% of our 3 mm detections fall within the field-of-view of 1 mm pointings. We extrapolate the derived spectral-index-based conclusions to the rest of the 3 mm sources. While the distance from the central regions of the clusters might have some impact on core temperature and age, it does not impact the conclusions of this paper.

## Source masses

Using a number of assumptions about the properties of a core, including that the dust is optically thin, we can derive the mass of such a core. We start from a modified blackbody equation: $$\begin{equation}
    B^{'}_{\nu} = \frac{2 h\nu^3}{c^2} \left(e^{h \nu / k_B T}-1\right)^{-1}\left(1-e^{-\kappa_\nu\Sigma}\right),
\label{eqn:mbbe}
\end{equation}$$

where $B^{'}_{\nu}$ is the spectral brightness of a modified blackbody, $h$ is the Planck constant, $\nu$ is the frequency, $c$ is the speed of light, $k_B$ is the Boltzmann constant, $T$ is the kinetic temperature of the source, $\kappa_\nu$ is the dust opacity index, and $\Sigma$ is the surface density. Given an area $A$, the mass $M$ is $$\begin{equation}
    M = \Sigma A = \Sigma \pi r^2,
\end{equation}$$ where $r$ is the source radius.

Converting the spectral brightness $B^{'}_{\nu}$ to the observed spectral flux density $S_\nu$ and applying the optically thin dust assumption ($\tau = \kappa_\nu \Sigma << 1$): $$\begin{equation}
    S_\nu = \frac{2 h\nu^3}{c^2}\left(e^{h \nu / k_B T}-1\right)^{-1}\frac{\kappa_\nu M}{\pi r^2} \frac{\pi r^2}{d^2},
\end{equation}$$ where $S_\nu$ is the observed flux density, $d$ is the distance to Sgr B2, and $M$ is the source mass. Simplifying using the Planck’s law and solving for mass yields: $$\begin{equation}
    M = \frac{S_\nu d^2}{B_\nu\kappa_\nu},
\end{equation}$$ where $B_\nu$ is the spectral brightness of a blackbody. Adopting the Rayleigh-Jeans approximation and expressing in terms of brightness temperature: $$\begin{equation}
 \label{eqn:mass}
    
    M = \frac{T_B d^2}{\kappa_\nu T_{KE}},
\end{equation}$$ where $T_B$ is the brightness temperature and $T_{KE}$ is the kinetic temperature of the source. Extrapolating the (cite: Ossenkopf1994) opacity models for dust grains with thin ice mantles, gas density of $10^6\ \mathrm{cm}^{-3}$, and age of $10^5$ years as a power law, assuming $\beta_{\text{dust}} = 1.75$, we obtain $\kappa_{92 GHz} = 0.0017\ \frac{cm^2}{g}$ and $\kappa_{226 GHz} = 0.0083\ \frac{cm^2}{g}$. Further assuming a uniform core temperature $T_{KE} = 50$ K and a distance[^3] of 8.4 kpc we can calculate source masses.

Here, we utilize the total dendrogram “leaf" flux instead of the source’s brightest pixel value to account for the sources that are partially resolved. We then incorporate an aperture correction factor for the source flux. The `astrodendro` algorithm excludes any emission that is below the specified `min_value`, in our case 4$\sigma$. Since the majority of our sources are unresolved or marginally resolved, we can assume 2D Gaussian flux distribution and account for the cut-off flux. For very crowded regions, `astrodendro` leaves might not extend to the minimum flux value. Thus, even with this correction some masses might be underestimated. In addition, since the cores are at least partially optically thick, we can obtain only a lower limit on their dust masses. Other variables being constant, an optically thick source contains more mass than an optically thin source. The calculated core masses are presented in Figure [10](#fig:masses).

![](Masses.png)

Both the individual mass measurements and mass distributions based on the 1 mm and 3 mm observed flux do not match. We attribute this to the erroneous assumption of optically thin dust used for this calculation. Such an assumption underestimates the masses at 1 mm more than at 3 mm as dust has longer mean free path at longer wavelengths and thus flux is emitted from more of the material before reaching optically thick regime. Thus, we use the masses based on the 3 mm data as the lower limits in the rest of the paper. The core mass distributions have the turnover point around our completeness threshold over the whole imaged area at 6$\sigma$ (13.5 M$_\odot$). Using `plfit`, a Python implementation of the general power law fitting algorithm (cite: Clauset2009), we fit a power law to the masses above the completeness limit. The resulting fit of 191 sources is $\alpha = 2.4\pm 0.1$, which is consistent with the Kroupa IMF $\alpha = 2.35$. If we increase the fitting threshold to 8$\sigma$ (18 M$_\odot$), the 144 sources produce a slightly steeper fit $\alpha = 2.6\pm 0.1$.

Using 50 K uniform core temperature gives an understanding of possible mass ranges and shows the general shape of the core mass distribution. As shown by (cite: Bonfand2019), some cores can have average temperatures close to or above 150 K, usually referred to as hot cores. We detect sources at the locations of at least several such hot cores. Such sources are most likely the hot cores’ central disks as our largest recoverable scale of $\sim$7500 AU is on the lower side of the typical hot core sizes in Sgr B2 (Jeff et al., in prep). At such high temperatures, the ice mantles surrounding the dust will start to sublimate. Such physical changes would decrease the emissivity by a factor of a few. We also do not expect a significant change to the gas-to-dust ratio based on freeze-out studies (cite: Caselli2022).

# Discussion

## Nature of the observed sources

### Protostellar cores: Stage 0/I YSOs

Our “core" catalog consists primarily of compact dusty sources with sizes between 200 AU and 1000 AU. Based on basic modeling, we show in this section that our cores are most consistent with an average temperature $\sim$50 K. Such objects are, given the lower limit on their densities, unlikely to be in pressure equilibrium. We therefore identify these as rotationally-supported disks consistent with Stage 0/I YSOs[^4]. We show the arguments in favor of this conclusion below.

In contrast to many studies of cores in nearby star-forming regions that assume a constant disk temperature of 20 K to make consistent comparisons between the works (cite: Eisner2018; Otter2021) we show that the core temperatures in Sgr B2 are more consistent with T = 50 K. Average dust temperatures based on *Herschel* line-of-sight observations (cite: Etxaluze2013) and theoretical models of external dust heating due to stars (cite: Schmiedeke2016) both produce $\sim$20 K average temperature in the moderate-density dust ($n\lesssim10^5\ \mathrm{cm}^{-3}$) in Sgr B2 region. However, the denser regions have gas temperatures that are substantially higher (cite: Ginsburg2016; Krieger2017). The modeled dust temperatures towards the centers of Sgr B2 N and M can go as high as 350 K and 600 K respectively (cite: Schmiedeke2016). Since we are observing cores, which are local overdensities, we expect temperatures higher than 20 K.

If we assume, very simplistically, that all of our observed cores are optically thick beam-sized spheres, about 50% of the cores at 3 mm and fewer than 20% of the cores at 1 mm can have $T_{KE} < 20$ K based on the expected and observed fluxes, as shown in Figure [11](#fig:BB). In reality, it is extremely unlikely that all of the cores are close to beam-sized. Sources smaller than the beam size would need to be warmer to produce the same flux. Furthermore, Figure [8](#fig:SI) shows that most of the cores are not completely optically thick, which requires the assumed temperatures to be even higher. About 75% of 1 mm detections are consistent with average temperatures of at least 50 K with the remaining 25% being hotter. Thus, in this work we take the average core temperature to be 50 K.

To test our assumptions, we create a simple model of our observed sources. It consists of an optically thick sphere of radius $R$ that is surrounded by optically thin dust of a certain surface density. This model mimics a face-on optically thick disk embedded in dust and is intended to confirm that we are able to detect dusty disks. Since many of our sources are calculated to be slightly optically thick, we also use this to test the expected spectral indexes for optically thick sources embedded in optically thin dust.

Assuming a gas-to-dust ratio of 100, we represent the dust surface density using gas column density, with an average over the Sgr B2 N and M cluster of around $3\times10^{24}$ $\mathrm{cm}^{-2}$ (cite: Sanchez-Monge2017). As discussed above, we assume a dust temperature of 50 K. Figure [12](#alpha_model) shows the expected spectral indexes of such sources as a function of the radius of the central optically thick sphere and the gas surface number density. We further indicate the region on the plot that will not be detectable in either of our bands at our sensitivity as the whited out region on the bottom left. The unshaded region of the plot corresponds to the parameters of our simplified model that can explain the observed sources.

![](alpha_model.png)

Using this model, for an optically thick face-on disk with an average temperature of 50 K we conclude that: a) in lower column density regions $(< 10^{24}$ $\mathrm{cm}^{-2})$ we are sensitive to sources that are larger than $\sim$300 AU in diameter and b) as the density of the surrounding dust increases past the average density in Sgr B2 (and up to $10^{26}$ $\mathrm{cm}^{-2}$ where the

dust becomes optically thick) the optically thin dust becomes the dominant source of emission.

The sources in our catalog are also much brighter than in any of the nearby star-forming regions. In the Orion molecular cloud only four of the brightest disks would be detectable at Sgr B2’s distance (cite: Tobin2020). Only a few of the disks in Orion are larger than 200 AU with corresponding masses of 0.2M$_\odot$. The sources in our catalog are most likely larger, more massive, and warmer than the ones in Orion.

### regions?

We evaluate whether the sources with $\alpha \approx 2$ could be regions and conclude that they are most likely not. At brightness temperatures of $10^4$ K, in order to match the range of recorded fluxes in our catalog, an optically thick region would have to be between 30 AU and 80 AU in diameter. Using a Strömgren sphere as an approximation, we know that: $$\begin{equation}
    Q(H^0) = \frac{4}{3}\pi R^3 N (H)^2\alpha_B,
\end{equation}$$ where $Q(H^0)$ is the number of ionizing photons, $R$ is the radius of the ionized sphere, $N(H)$ is hydrogen number density, and $\alpha_B$ is the recombination rate to all levels excluding the ground level, $\approx 3 \times 10^{-13}$ cm$^3$ s$^{-1}$ (cite: Draine2011). Taking $Q(H^0)$ between $5\times10^{47}$ s$^{-1}$ and $1.5\times10^{49}$ s$^{-1}$, equivalent to B0-O6 stars, we find that 30-80 AU, hyper-compact regions can potentially exist in densities between $10^{7}$ and $10^{9}$ cm$^{-3}$. These densities are reasonable for Sgr B2 (cite: Meng2022). However, any optically thick region larger than 80 AU in diameter should be detected with our sensitivity. No such sources are present in our catalog. Roughly 100 sources in our catalog have $\alpha \approx 2$. By making several assumptions, such as higher region metallicity (which will lower its electron temperature) and the right amount of high-mass stars embedded in higher-than-previously-measured gas densities, many of the observed optically thick sources can be attributed to 30-80 AU regions. At the same time, there exists a population of regions larger than 500 AU (cite: Meng2022). Assuming that the regions evolve continuously, the absence of 80-500 AU scale regions indicate that there was an abrupt period with no stars being formed. A short, temporary, and complete interruption of star-forming processes would be extremely unusual. Thus, we claim that there are very few to none regions contaminating our catalog. Additional observations, e.g. radio recombination lines, could help determine the nature of these sources definitively.

### Prestellar cores?

As described in Section [3.5](#sec:source_masses), we can place a lower limit on the masses of our sources by assuming each is a beam-sized uniform sphere with a dust optical depth of 1. Free-fall time of a spherically-symmetric core is: $$\begin{equation}
    t_{ff} = \sqrt{\frac{3\pi}{32G\rho}} = \sqrt{\frac{3\pi V}{32Gm}} = \sqrt{\frac{\pi^2 R^3}{8Gm}},
\end{equation}$$ where $G$ is the gravitational constant and $V$, $m$, and $R$ are the volume, mass, and radius of a core. Taking the least massive source in our catalog ($\sim$1M$_\odot$) to be beam-sized ($\sim$700 AU) would result in free-fall times of 1200 years, while the most massive core of the same size would have a free-fall time of 40 years – extremely short on star formation scales. Thus, it is unlikely that any of our sources (at least on $\sim$700 AU scales) are still undergoing free-fall collapse, indicating that there are no prestellar cores in our sample. While this is an extreme approximation, the higher mass, heterogeneous nature of the source, and the influence of the surrounding environment would speed up the infall of the material and result in even shorter collapse timescales.

We can further estimate the effects of the high-pressure environment using the Bonnor-Ebert mass: $$\begin{equation}
    M_{BE} = 1.18 \frac{c_s^4}{G^{3/2}p_{BE}^{1/2}},
\end{equation}$$ where $c_s$ is the speed of sound, 0.4 km/s (T = 50 K), $G$ is the gravitational constant, and $p_{BE}$ is the pressure ($P/k_B = 10^{8} - 10^{13} \mathrm{\ K\ cm}^{-3}$ (cite: Myers2022)). The maximum Bonnor-Ebert mass for the sources in Sgr B2 is then $\sim$$10^{-3}$$-10^0$M$_\odot$. Only two cores in our catalog have mass lower limits below 1M$_\odot$. Thus, the majority of the cores are not pressure supported.

Presently, there is not enough observational evidence to determine the impact of magnetic fields in the collapse of massive cores (cite: Pattle2023). The observed randomness of the core’s magnetic field orientation relative to the large-scale magnetic fields in Cygnus X suggests that on small scales, gravity plays a more important role compared to magnetic field (cite: Ching2017). Thus, in this work we assume that the magnetic fields do not contribute to the core collapse support. Having ruled out the free-fall collapse and pressure support, and the improbable magnetic field support, the remaining option is the rotational support of disks.

### Stage II and III YSOs?

To test whether the stars are Stage II YSOs, we check what stellar mass would be predicted by extrapolating local relations.

We extrapolate the ratio of the dust mass and the central star of $\sim$1% (cite: Williams2011) one order of magnitude for more massive objects to calculate the possible mass of the central star for the least massive sources in our catalog. The faintest source in our data is 1.2 mJy at 1.3 mm, which would correspond to a central star with a mass of at least 30M$_\odot$. If all of our observed sources are Stage II YSOs, the median star mass would be around 300M$_\odot$, which is on the order of the largest stars ever detected.

Current disk demographic samples (cite: Andrews2018; Williams2011) are limited to M $\lesssim2$M$_\odot$.

If we assume an optically thick, face-on dusty disk with an average temperature of 50 K, the disk would have to be at least 200 AU in size to be detectable with our sensitivity, which is similar in size to the largest disks in the Solar neighborhood. All of our targets, if they are disks, must be larger and more massive than any disks observed in the local neighborhood (cite: Andrews2018). Stage III YSOs do not have infrared excess and thus could not possibly be detected in our data.

## Inferred stellar mass

We estimate the total stellar mass of Sgr B2 N and M using direct source counting down to 1M$_\odot$. We take the calculated masses from Section [3.5](#sec:source_masses) and extrapolate the low-mass end of the Kroupa initial mass function (cite: Kroupa2001) to obtain the core-based inferred stellar mass. We count the known regions to add the high-mass sources. We report the total observed ($M_{\Sigma obs}$) and inferred ($M_{\Sigma inf}$) stellar masses for Sgr B2 N and M in Table [\[tab:inferred_mass\]](#tab:inferred_mass).

Using individual core masses provides more accurate mass estimation, compared to lower-resolution studies, where an average core mass is assigned. To allow for direct comparison with previous works, we take the radii of Sgr B2 N and M clusters to be 0.4 pc and 0.5 pc, respectively. We further assume that roughly one third of a core mass will end up in a star (cite: Lada2003). We take 6$\sigma$ as our completeness limit within the cluster boundaries – 0.3 mJy for Sgr B2 M and 0.2 mJy for Sgr B2 N, which corresponds to 1.5M$_\odot$ and 1M$_\odot$ stellar mass respectively (equivalent to 4.5M$_\odot$ and 3M$_\odot$ core mass). We exclude all the sources below this completeness limit. Since the massive cores rapidly evolve into regions, we also set an upper limit of 20M$_\odot$. Thus:

$$\begin{equation}
    M_{core,inf} = M_{core,obs} \frac{\int_{0.3M\ensuremath{_\odot}}^{120M\ensuremath{_\odot}}f \mathrm{d}m}{\int_{6\sigma}^{20M\ensuremath{_\odot}}f \mathrm{d}m},
\end{equation}$$ where $M_{core,inf}$ is the inferred core-based stellar mass, $M_{core,obs}$ is the sum of the core masses above our completeness limit divided by 3, and $f$ is the Kroupa IMF. Compared to G18 we detect $\sim$10 times more cores in Sgr B2 N and $\sim$4 times more cores in Sgr B2 M. With the larger number of sources and augmented stellar mass calculation, we observe a 60% higher core-based stellar mass in Sgr B2 N, but 30% lower in Sgr B2 M.

To account for the high-mass sources, we count the number of regions from (cite: DePree1998) and (cite: Meng2022) and add the newly discovered regions in this work. Assuming that each region is powered by a $>$ 20M$_\odot$ star, the IMF-weighted average mass of such star is 45M$_\odot$. Combining the core-based stellar mass with the region-based stellar mass: $$\begin{equation}
    M_{\Sigma inf} = \left( M_{core,obs} + M_{\hii,obs} \right) \frac{\int_{0.3M\ensuremath{_\odot}}^{120M\ensuremath{_\odot}}f \mathrm{d}m}{\int_{6\sigma}^{120M\ensuremath{_\odot}}f \mathrm{d}m},
\end{equation}$$ where $M_{\Sigma inf}$ is the total inferred stellar mass and $M_{\hii,obs} = N(\hii) \times 45.5 M\ensuremath{_\odot}$. Taking the star-forming age of the cloud as 0.74 Myr (cite: Kruijssen2015), we estimate the star formation rate (SFR) for each cluster. Compared to G18 we find that the total inferred stellar mass in Sgr B2 N increased by more than a factor of two, but is slightly lower for Sgr B2 M.

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | $N(core)$ | $M_{core,obs}$ | $M_{core,inf}$ | $M_{core,inf}^{G18}$ | $N(\hii)$ | $M_{\Sigma obs}$ | $M_{\Sigma inf}$ | $M_{\Sigma inf}^{G18}$ | $M_{\Sigma inf}^{S16}$ | SFR |
|  |  | M$_\odot$ | M$_\odot$ | M$_\odot$ |  | M$_\odot$ | M$_\odot$ | M$_\odot$ | M$_\odot$ | M$_\odot$ yr$^{-1}$ |
| N | 105 | 1010 | 2400 | 1500 | 11 | 1500 | 2800 | 1200 | 2400 | 0.0038 |
| M | 68 | 550 | 1600 | 2300 | 57 | 3100 | 6900 | 8800 | 20700 | 0.0093 |

With the high-resolution data, it is evident that the historically defined sizes of Sgr B2 North and Main in (cite: Goldsmith1990) do not necessarily represent which sources are part of the clusters. Both N and M have a continuous “chain" of sources in projection in the eastward direction, as visible in Figures [1](#fig:B3) and [2](#fig:B6). The defined sizes cut through these “chains" of sources. Further kinematics studies of the region that extended beyond the centers of the clusters (cite: Schworer2019) are needed to determine which sources belong to which protocluster and would allow for more accurate count-based cluster mass estimation.

## Core fragmentation

We compare our core catalog with G18, which observed Sgr B2 N and M at 10 times coarser resolution. For each low-resolution detection, we find the number of high-resolution detections within 1.5 $\times$ beam FWHM of the source center. We exclude sources from the G18 catalog that would not be detectable in our data, specifically at the pointing edges where the sensitivity is lower. Of the 94 potentially detectable G18 sources, only 77 are detected at high-resolution. Out of 371 detections at 3 mm in our catalog, 109 cores are contained within

low-resolution sources, 42 are one-to-one match, and the remaining 220 are new detections with no corresponding detections in G18.

Of the G18 sources that are not detected in the high-resolution data, some are most likely false detections, but some may be resolved-out extended structures. Our shortest baseline length of 41 m is longer than the 15 m in G18 data. On average, our images are made weighting longer baselines. As a

result, some of the previous detections may

be resolved out. We find that over a dozen sources from the low-resolution catalog do not have a counterpart in the high-resolution catalog. The high-resolution data’s largest recoverable scale is 0.9", or $\sim$7500 AU.

We find that over half of the low resolution detections “fragment" into two or more sources, with one of the sources fragmenting into ten, as shown in Figure [3](#fig:zoomin). The distribution is shown in Figure [13](#fig:highperlow). We do not find any pattern in the locations of the cores that fragment vs those that do not. Figure [14](#fig:comparison) shows the spatial distribution of the cross-matched and resolved-out sources as well as the new detections.

On average, each detected G18 source fragments into 2 cores. If we take the one third of the sources that fragment, then there is an average of 3.4 cores per G18 fragmenting source. In general, source fragmentation changes the shape of the core mass function (and if these fragments represent individual systems – the IMF), making it steeper.

Because cores previously inferred to contain single, very massive star are broken into many lower-mass objects, increasing the total number of sources, the total expected luminosity of these sources reduces significantly.

We find that any source from G18’s catalog, at 5000 AU resolution, with flux above 20 mJy ended up being fragmented at 700 AU resolution. It is not possible to place meaningful lower limits on the fragmentation function at low flux: the sources are more likely to be close to the sensitivity limit of the higher-resolution data.

![](sps.png)

![](sources_per_new_detections.png)

# Summary

We presented $\sim$700 AU follow-up continuum observations of a massive molecular cloud in the CMZ – Sagittarius B2. We detected 410 unique cores: 371 at 3 mm, a twofold increase compared to (cite: Ginsburg2018), and 218 at 1 mm. Most of the newly detected sources are due to the increased sensitivity, while about a fifth come from resolving fragmented sources. We find most sources to be marginally resolved and have a spectral index consistent with ${2<\alpha\lesssim3}$. We infer that the dusty objects we observe must be disks that are warmer than those in the rest of the Galaxy.

Because of their high temperatures, these sources are unlikely to be prestellar cores. Because of their high column densities, they are unlikely to be Stage II or later YSOs. We therefore conclude that the sample is comprised primarily of Stage 0/I YSOs. We find that the core mass function of our sample is consistent with the Kroupa IMF. Using direct source counting, we infer the total stellar mass of 2800M$_\odot$ for Sgr B2 N and 6900M$_\odot$ for Sgr B2 M. The resulting star formation rate is 0.0038M$_\odot$ yr$^{-1}$ for Sgr B2 N and 0.0093M$_\odot$ yr$^{-1}$ for Sgr B2 M totalling 0.013M$_\odot$ yr$^{-1}$, which is similar to previous estimates.

# Acknowledgments

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00550.S, ADS/JAO.ALMA#2013.1.00269.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. AG acknowledges support from the NSF under CAREER 2142300 and AST 2008101 and 2206511. NB and DJ were supported by NRAO Student Observing Support grants SOSPA8-010 and SOSPA6-026.

# Facilities

ALMA

# Software

Image reduction and final catalogs are available on GitHub: <https://github.com/nbudaiev/SgrB2_ALMA_continuum/releases/tag/Accepted-15-Sep-2023>. This work utilized the following tools: `astropy` (cite: astropy:2013; astropy:2018), CASA version 5.7.0-134.el7 (cite: McMullin2007), `astrodendro` (cite: Rosolowsky2008), `plfit` (<https://github.com/keflavich/plfit>) , `dendrocat`, `radiobeam`.

natexlab

(ref: Andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Barnes2017) Barnes, A. T., Longmore, S. N., Battersby, C., et al. 2017, MNRAS, 469, 2263, doi: [`10.1093/mnras/stx941`](http://doi.org/10.1093/mnras/stx941)

(ref: Bonfand2019) Bonfand, M., Belloche, A., Garrod, R. T., et al. 2019, A&A, 628, A27, doi: [`10.1051/0004-6361/201935523`](http://doi.org/10.1051/0004-6361/201935523)

(ref: Caselli2022) Caselli, P., Pineda, J. E., Sipilä, O., et al. 2022, ApJ, 929, 13, doi: [`10.3847/1538-4357/ac5913`](http://doi.org/10.3847/1538-4357/ac5913)

(ref: Ching2017) Ching, T.-C., Lai, S.-P., Zhang, Q., et al. 2017, ApJ, 838, 121, doi: [`10.3847/1538-4357/aa65cc`](http://doi.org/10.3847/1538-4357/aa65cc)

(ref: Clauset2009) Clauset, A., Shalizi, C. R., & Newman, M. E. J. 2009, SIAM Review, 51, 661, doi: [`10.1137/070710111`](http://doi.org/10.1137/070710111)

(ref: DePree1998) De Pree, C. G., Goss, W. M., & Gaume, R. A. 1998, ApJ, 500, 847, doi: [`10.1086/305782`](http://doi.org/10.1086/305782)

(ref: Draine2011) Draine, B. T. 2011, ApJ, 732, 100, doi: [`10.1088/0004-637X/732/2/100`](http://doi.org/10.1088/0004-637X/732/2/100)

(ref: Eisner2018) Eisner, J. A., Arce, H. G., Ballering, N. P., et al. 2018, ApJ, 860, 77, doi: [`10.3847/1538-4357/aac3e2`](http://doi.org/10.3847/1538-4357/aac3e2)

(ref: Etxaluze2013) Etxaluze, M., Goicoechea, J. R., Cernicharo, J., et al. 2013, A&A, 556, A137, doi: [`10.1051/0004-6361/201321258`](http://doi.org/10.1051/0004-6361/201321258)

(ref: Gallego-Calvente2022) Gallego-Calvente, A. T., Schödel, R., Alberdi, A., et al. 2022, A&A, 664, A49, doi: [`10.1051/0004-6361/202141895`](http://doi.org/10.1051/0004-6361/202141895)

(ref: Ginsburg2018CFE) Ginsburg, A., & Kruijssen, J. M. D. 2018, ApJL, 864, L17, doi: [`10.3847/2041-8213/aada89`](http://doi.org/10.3847/2041-8213/aada89)

(ref: Ginsburg2016) Ginsburg, A., Henkel, C., Ao, Y., et al. 2016, A&A, 586, A50, doi: [`10.1051/0004-6361/201526100`](http://doi.org/10.1051/0004-6361/201526100)

(ref: Ginsburg2018) Ginsburg, A., Bally, J., Barnes, A., et al. 2018, ApJ, 853, 171, doi: [`10.3847/1538-4357/aaa6d4`](http://doi.org/10.3847/1538-4357/aaa6d4)

(ref: Goldsmith1990) Goldsmith, P. F., Lis, D. C., Hills, R., & Lasenby, J. 1990, ApJ, 350, 186, doi: [`10.1086/168372`](http://doi.org/10.1086/168372)

(ref: GRAVITYCollaboration2018) GRAVITY Collaboration, Abuter, R., Amorim, A., et al. 2018, A&A, 615, L15, doi: [`10.1051/0004-6361/201833718`](http://doi.org/10.1051/0004-6361/201833718)

(ref: Henshaw2022) Henshaw, J. D., Barnes, A. T., Battersby, C., et al. 2022, arXiv e-prints, arXiv:2203.11223, doi: [`10.48550/arXiv.2203.11223`](http://doi.org/10.48550/arXiv.2203.11223)

(ref: Hosek2019a) Hosek, Matthew W., J., Lu, J. R., Anderson, J., et al. 2019, ApJ, 870, 44, doi: [`10.3847/1538-4357/aaef90`](http://doi.org/10.3847/1538-4357/aaef90)

(ref: Krieger2017) Krieger, N., Ott, J., Beuther, H., et al. 2017, ApJ, 850, 77, doi: [`10.3847/1538-4357/aa951c`](http://doi.org/10.3847/1538-4357/aa951c)

(ref: Kroupa2001) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: Kruijssen2015) Kruijssen, J. M. D., Dale, J. E., & Longmore, S. N. 2015, MNRAS, 447, 1059, doi: [`10.1093/mnras/stu2526`](http://doi.org/10.1093/mnras/stu2526)

(ref: Lada2003) Lada, C. J., & Lada, E. A. 2003, ARA&A, 41, 57, doi: [`10.1146/annurev.astro.41.011802.094844`](http://doi.org/10.1146/annurev.astro.41.011802.094844)

(ref: Lanyi2010) Lanyi, G. E., Boboltz, D. A., Charlot, P., et al. 2010, AJ, 139, 1695, doi: [`10.1088/0004-6256/139/5/1695`](http://doi.org/10.1088/0004-6256/139/5/1695)

(ref: Li2023) Li, J., Liu, C., Zhang, Z.-Y., et al. 2023, Nature, 613, 460, doi: [`10.1038/s41586-022-05488-1`](http://doi.org/10.1038/s41586-022-05488-1)

(ref: Lu2022) Lu, X., Li, G.-X., Zhang, Q., & Lin, Y. 2022, Nature Astronomy, 6, 837, doi: [`10.1038/s41550-022-01681-4`](http://doi.org/10.1038/s41550-022-01681-4)

(ref: Madau2014) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Meng2022) Meng, F., Sánchez-Monge, Á., Schilke, P., et al. 2022, A&A, 666, A31, doi: [`10.1051/0004-6361/202243674`](http://doi.org/10.1051/0004-6361/202243674)

(ref: Myers2022) Myers, P. C., Hatchfield, H. P., & Battersby, C. 2022, ApJ, 929, 34, doi: [`10.3847/1538-4357/ac5906`](http://doi.org/10.3847/1538-4357/ac5906)

(ref: Ossenkopf1994) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: Otter2021) Otter, J., Ginsburg, A., Ballering, N. P., et al. 2021, ApJ, 923, 221, doi: [`10.3847/1538-4357/ac29c2`](http://doi.org/10.3847/1538-4357/ac29c2)

(ref: Pattle2023) Pattle, K., Fissel, L., Tahani, M., Liu, T., & Ntormousi, E. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 193

(ref: Qin2011) Qin, S. L., Schilke, P., Rolffs, R., et al. 2011, A&A, 530, L9, doi: [`10.1051/0004-6361/201116928`](http://doi.org/10.1051/0004-6361/201116928)

(ref: Richards2022) Richards, A. M. S., Moravec, E., Etoka, S., et al. 2022, arXiv e-prints, arXiv:2207.05591, doi: [`10.48550/arXiv.2207.05591`](http://doi.org/10.48550/arXiv.2207.05591)

(ref: Robitaille2006) Robitaille, T. P., Whitney, B. A., Indebetouw, R., Wood, K., & Denzmore, P. 2006, ApJS, 167, 256, doi: [`10.1086/508424`](http://doi.org/10.1086/508424)

(ref: Rosolowsky2008) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ, 679, 1338, doi: [`10.1086/587685`](http://doi.org/10.1086/587685)

(ref: Sanchez-Monge2017) Sánchez-Monge, Á., Schilke, P., Schmiedeke, A., et al. 2017, A&A, 604, A6, doi: [`10.1051/0004-6361/201730426`](http://doi.org/10.1051/0004-6361/201730426)

(ref: Schmiedeke2016) Schmiedeke, A., Schilke, P., Möller, T., et al. 2016, A&A, 588, A143, doi: [`10.1051/0004-6361/201527311`](http://doi.org/10.1051/0004-6361/201527311)

(ref: Schworer2019) Schwörer, A., Sánchez-Monge, Á., Schilke, P., et al. 2019, A&A, 628, A6, doi: [`10.1051/0004-6361/201935200`](http://doi.org/10.1051/0004-6361/201935200)

(ref: Tobin2020) Tobin, J. J., Sheehan, P. D., Megeath, S. T., et al. 2020, ApJ, 890, 130, doi: [`10.3847/1538-4357/ab6f64`](http://doi.org/10.3847/1538-4357/ab6f64)

(ref: Williams2011) Williams, J. P., & Cieza, L. A. 2011, ARA&A, 49, 67, doi: [`10.1146/annurev-astro-081710-102548`](http://doi.org/10.1146/annurev-astro-081710-102548)

(ref: Zhang2018) Zhang, Z.-Y., Romano, D., Ivison, R. J., Papadopoulos, P. P., & Matteucci, F. 2018, Nature, 558, 260, doi: [`10.1038/s41586-018-0196-x`](http://doi.org/10.1038/s41586-018-0196-x)

# Line contribution to continuum

It has been shown that sources towards the central subclusters Sgr B2 N and M are line-rich (cite: Sanchez-Monge2017). We inspected the full cubes of Sgr B2 N Band 3 and Band 6 pointings to evaluate the relative line contribution to the sources in our catalog. We extracted spectra at the location of the brightest pixels of the cores cataloged in this work. We removed line emission and absorption from the spectra using the `astropy’s` implementation of sigma clipping with `sigma`=2 and `maxiters`=5. First, we calculated the mean of spectra before and after line removal for each core. Then, to estimate the proportional flux change, we calculate the difference between the two spectra and divide by the brightest pixel’s flux in the non-line-subtracted continuum image used to generate the catalogs. We find that the mean relative line contribution for all cores is $-4.4\%$ for Band 3 and $-1.2\%$ for Band 6. The scaled mean average deviation is 5.2% for Band 3 and 11.2% for Band 6. All sources with significant flux change due to line subtraction had SNR $<$ 10. Thus, we conclude that on average emission and absorption lines do not contribute to the continuum level significantly for the cataloged objects.

# Cleaning and self-calibration testing

Sgr B2 region is one of the most complex regions that ALMA can observe. Pointing Band 3 beam at one of the two largest cores N or M places the other of the two just on the edge of the beam, significantly contributing to the artifacts in the image. We tested different cleaning approaches with special focus on masking and choosing the right cleaning threshold.

We found that the choice of mask significantly affects the quality of the final image. Generally, it is recommended to mask the images conscientiously, only including the real emission (cite: Richards2022). At first, we tried to use RMS-based masks. We went through the calibration process using $5\sigma$, $3\sigma$, and $2\sigma$ masks based on the noise in the inner, signal-free region of the image. The resulting residuals contained very sharp edges around the mask contours. We then switched to a less restrictive approach: we drew polygons around visually identified emission regions. The resulting mask covered more emission, but also included some of the artifact-rich regions. After cleaning, the images ended up with several factors lower noise than with RMS-based masks and the residual did not have any abrupt features. To minimize the effect of including the artifacts in the cleaning mask, especially in the first few iterations where they are the most prominent, we decided to use the “strict" mask for the first two iterations and then use the more broad mask for the remainder of the cleaning and calibration process. This time, we drew two sets of masks for each pointing: one containing just the brightest emission similar to the 5$\sigma$ mask, but also including significant sources of emission further away from the center of the image, and a more broad mask where polygons surround any regions with visible emission. The use of a combination of a strict and broad masks resulted in a few percent lower RMS than using only the broad mask.

Generally, we used $6\sigma$ cleaning threshold for the first two cleaning iterations and $3\sigma$ for the remainder of the cleaning and calibration. However, the Band 6 pointing of Sgr B2 N suffered from divergence at these thresholds. Using higher-threshold cleaning, we determined that the image significantly improves after amplitude and phase calibration. After testing different cleaning thresholds, we found that the deepest we can clean the image without the clean diverging is $\sim$$10\sigma$ until the amplitude and phase calibration and then the 3$\sigma$ cleans will not diverge. The lowest measured RMS for each pointing is presented in Table [1](#tab:RMS). The self-calibration progress images highlighting different regions are shown in Figure [15](#fig:calibration).

## Intrinsic uncertainty of interferometric imaging

The choice of parameters during imaging and self-calibration can have a significant influence on the final result, especially for bright, extended sources. We explored possible approaches to create a more robust version of the final image and evaluated the possible systematic and random uncertainties introduced in the process. We used the Band 6 Sgr B2 N pointing for the testing and compared the brightest pixel for each of our cataloged source between different versions of the image. The observations for each pointing were split into two measurement sets that were observed on different days; we were modifying each measurement set separately and combining them for the final comparison.

### Problematic baselines

As visible on Figure [1](#fig:B3) and especially on Figure [2](#fig:B6), there are large-scale parallel ripples. The impact of these artifacts is especially visible in Figure [15](#fig:calibration)(c) between panels 3 and 4, where the artifacts become less prominent during amplitude self-calibration. A possible approach to remove these artifacts is to identify and flag the problematic baselines that are causing the ripples. Using the separation between the wave peaks and the relative orientation of the ripples, we iteratively removed problematic baselines until further removal resulted in diminishing returns. We removed ten most severe baselines. Since the removed baselines were all very short baselines, we also lost the large-scale structures. The removal of individual baselines had very little effect on self-calibration solutions. Removing short baselines introduced individual source flux scatter of up to 50%, primarily for dim sources, but no systematic flux changes were present.

### QA-flagged data

We discovered that one of the measurement sets for Sgr B2 N Band 6 pointing had 16 ID-sequential antennas flagged during the very first stages of ALMA pipeline run prior to the delivery to the user. The flagging starts about two-thirds into the observing run, right after the water vapor calibration scan. Based on the limited information, we attribute this flagging to a fault in the correlator. Suddenly dropping almost a third of antennas results in a discontinuity in amplitude self-calibration solutions for some antennas. We chose not to flag the rest of the data past the time when the partial flagging begins, as it would result in losing over ten percent of observations. Instead, we attempt to improve the amplitude self-calibration solutions as described in the next section.

### Poor self-calibration solutions

We found that excluding solutions from short baselines (that usually have the largest unweighted amplitudes) would result in smaller amount of discontinuities in amplitude self-calibration solutions. We used `uvrange` parameter in `gaincal` task to limit the baseline lengths used to calculate the calibration solutions. After testing different values, we found that setting `uvrange` at $> 240$ m results in the least amount of discontinuities in the solutions. To further mitigate the possible erroneous flux changes from the amplitude self-calibration, we chose not to apply any antenna solutions that have discontinuities or sharp changes.

### Final result

We combined the approaches described in the subsections above to create as conservative image as possible. We started with the same phase self-calibration process as the original reduction with the exception of excluding the problematic baselines. During the first round of amplitude self-calibration we used `uvrange > 240m` in `gaincal` task for the measurement set with flagged data. In addition, we normalized the solutions and increased the solution SNR requirement from 3 to 5 compared to the original imaging parameters. We then inspected the amplitude self-calibration solutions, and very conservatively excluded any solution that might lead to erroneous corrections. Specifically, if there was a discontinuity of more than 0.15 in amplitude or rapid changes of more than 0.5 in amplitude, the corresponding antenna solutions were flagged. We then repeat the same process, now with `solint` set to 15 s. We then compared the brightest pixel in each cataloged source between the originally reduced data and using the conservative approach. The flux ratios are shown in Figure [16](#fig:reduction_tests). We find that there is a scatter in flux ratios of up to 40%, especially for dim sources and the average ratio is very close to 1. This indicates that we can expect a large flux uncertainty for individual sources due to radiointerferometric imaging, but there is no systematic error in the approach we used to create the final catalogs, at least when comparing to a “more robust" approach. With the self-calibration approach used in this paper, we are able to achieve 20% lower noise compared to the more conservative self-calibration.

![](reduction_tests.png)

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Pointing | Uncalibrated | Phase, inf | Phase, int | Phase+amp, inf | Phase+amp, 15s | $4\sigma$-$40\%_{image}$ | $4\sigma$-$90\%_{image}$ |
|  | mJy | mJy | mJy | mJy | mJy | mJy | mJy |
| N, 3 mm | 0.047 | 0.044 | 0.032 | – | – | 0.13 | 0.43 |
| M, 3 mm | 0.105 | 0.068 | 0.054 | 0.051 | – | 0.20 | 0.61 |
| N, 1 mm | 1.37 | 1.35 | 1.35 | 0.47 | 0.35 | 1.41 | 4.62 |
| M, 1 mm | 0.55 | 0.40 | 0.30 | 0.25 | – | 1.00 | 3.27 |

: Lowest RMS within the inner, signal-free region of each pointing during different calibration stages. The cleaning thresholds for the first two cleaning iterations were $\sim$$6\sigma$ and $\sim$$3\sigma$ for the remainder of the self-calibration process. The last two columns show the source extraction threshold values within the inner 40% and 90% of the imaged area. The noise was calculated within the concentric annuli described in Section [3.1](#sec:source_extraction).

## Imaging overlapping pointings

At 3 mm (Band 3), pointings centered on Sgr B2 N and M have an overlap in the imaged area, such that the center of one pointing appears at the edge of the other pointing when imaged beyond primary-beam-response of $\sim$0.2. We tested three possible ways to image and reduce these pointings: imaging both pointings together using mosaic gridder, imaging each pointing separately and taking a weighted average of the overlapping region, and imaging and reducing each pointing separately. In this work, we use the latter method where we crop the two imaged pointings based on the achieved noise.

We find no significant benefit of imaging the two pointings together with mosaic gridder when compared to using standard gridder on each pointing individually. For these data, the main benefit of mosaic gridder is to make a better model of the image that accounts for more of the bright emission that otherwise might have been outside of the imaged area of a single pointing. In a single pointing, the flux from outside of the imaged area ends up spread over the whole image resulting in higher observed flux. However, we choose the primary-beam-response level of 0.1 such that most of the bright flux, in this case the central clusters N and M, are included in both pointings. When comparing the jointly- and separately-imaged pointings, the reduction in the intensity of artifacts is minimal. Furthermore, the two pointings have a different final cleaning threshold, as shown in Table [1](#tab:RMS). Mosaicing the two pointings would result in either undercleaning or overcleaning of one of the pointings. Finally, computationally the cleaning of Band 3 mosaic requires close to maximum computing resources available; this would not allow for testing of enough of the imaging parameter space to achieve the desired result.

An alternative approach that benefits from the overlapping pointings is to take a weighted average of the separately reduced images. This method works best when the noise is isotropic and we would expect a factor of $\sqrt{2}$ reduction in noise. However, as seen in Figure [1](#fig:B3) interferometric artifacts are highly structured, with a combination of concentric waves, radial streaks, and negative bowls. For the area that would theoretically benefit the most, around Sgr B2 Z10.24, we see less than 10 percent decrease in noise with source flux remaining the same.

None of the methods described above would change the results of this work or have a meaningful impact on reported fluxes. Other sources of uncertainty, such as self-calibration process or the choice of source extraction method play a more significant role. Thus, in this work we reduce each pointings separately, splitting the overlapping area between the two pointings based on the distance from the center of the pointing and the source clustering.

## Evaluation using unsharp masking

We attempted to use unsharp masking to evaluate at what value lowering cleaning threshold no longer improves the image on small scales. To create a sharpened image, the original image is first smoothed using a Gaussian kernel. Smoothing removes “blurs" small scale structures effectively removing them while keeping the large scale structures mostly intact. Different size of the smoothing kernel can be chosen to effect different size-scales. Typically, the sharpened image is: $$\begin{equation}
    \mathrm{Sharpened} = \mathrm{Original} \times A - \mathrm{Smoothed} \times (A - 1),
\label{eqn:unsharp}
\end{equation}$$ where $A$ determines how strong the effect is.

Generally, cleaning to a lower threshold results in “better" images. However, cleaning too deep results in the `tclean` model including artifacts. In highly complex, high-dynamic-range images some of the artifacts will be present in the model unless an extremely shallow clean is performed. We strove to achieve a balance between cleaning depth and the amount of artifacts in the image model. We found that decreasing the cleaning threshold always decreases the measured RMS, which consequently could not be used to determine the “best" cleaning threshold.

The majority of the artifacts in our images are small-scale: concentric rings and radial streaks with scale-length smaller than the beam size. We used a simplified version of unsharp masking, $\mathrm{Sharpened} = \mathrm{Original} - \mathrm{Smoothed}$, to create large-scale-structure-free versions of our images at different cleaning thresholds. If there exists a cleaning threshold at which small-scale artifacts are no longer removed by cleaning, we should be able to detect it by measuring the RMS of these sharpened images. However, we found no such correlation and the measured noise in sharpened images steadily decreased with the cleaning depth.

During the unsharp masking investigation we made sharpened versions of the final images. Upon inspection, we identified a core-like source close to Sgr B2 S region as shown in Figure [17](#fig:unsharp_masking). Because of the core’s proximity to the bright region, the chosen source extraction parameters are not able to identify it as a separate source. Thus, this source is not included in our final catalog. While unsharp masking is a viable method to identify such otherwise “hidden" sources, the sharpened images cannot be used for data analysis as the flux is not conserved during the transformation.

# Source catalog

We present an excerpt from Sgr B2 N core catalog at 3 mm in Table [2](#tab:catalog). The full catalogs are available in machine-readable format and on GitHub: <https://github.com/nbudaiev/SgrB2_ALMA_continuum>.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | $S_{\nu,flux}$ | $S_{\nu,peak}$ | $S_{\nu, err}$ | FWHM$_{maj}$ | FWHM$_{min}$ | RA (ICRS) | Dec (ICRS) | Score | Source | ID$_{\mathrm{Band 3}}$ | $T_B$ | $\alpha$ | $\alpha_{err}$ | Mass |
|  | $\mathrm{mJy}$ | $\mathrm{mJy\,beam^{-1}}$ | $\mathrm{mJy\,beam^{-1}}$ | $\mathrm{{}^{\prime\prime}}$ | $\mathrm{{}^{\prime\prime}}$ |  |  |  |  |  | $\mathrm{K}$ |  |  | $\mathrm{M_{\odot}}$ |
| 1 | 13.4 | 7.2 | 0.353 | 0.11 | 0.043 | 17:47:19.9296 | -28:22:19.272 | 2 | core | 6 | 53 | 2.3 | 0.1 | 7.5 |
| 4 | 17.9 | 5.2 | 0.353 | 0.307 | 0.048 | 17:47:19.9608 | -28:22:18.624 | 1 | core | 11 | 39 | 1.5 | 0.2 | 10.4 |
| 7 | 5.6 | 11.9 | 0.353 | 0.046 | 0.018 | 17:47:19.8744 | -28:22:18.588 | 1 | HII_cand | 14 | 89 | -1.01 | 0.05 |  |
| 8 | 76.7 | 16.5 | 0.353 | 0.134 | 0.087 | 17:47:19.884 | -28:22:18.3 | 1 | HII_cand | 17 | 123 | 1.08 | 0.03 |  |
| 11 | 11.7 | 6.1 | 0.353 | 0.065 | 0.064 | 17:47:19.9464 | -28:22:19.956 | 2 | core | 2 | 45 | 2.18 | 0.08 | 6.7 |
| 15 | 11.3 | 6.3 | 0.353 | 0.078 | 0.041 | 17:47:19.9368 | -28:22:19.812 | 2 | core | 3 | 47 | 2.5 | 0.08 | 6.4 |
| 23 | 7.5 | 6.0 | 0.353 | 0.064 | 0.036 | 17:47:19.9152 | -28:22:19.632 | 1 | core |  | 45 | 2.82 | 0.09 | 4.3 |
| 25 | 6.7 | 5.6 | 0.353 | 0.056 | 0.039 | 17:47:19.9056 | -28:22:19.596 | 1 | core |  | 42 | 2.66 | 0.09 | 3.9 |
| 26 | 17.3 | 6.8 | 0.353 | 0.103 | 0.049 | 17:47:19.8936 | -28:22:19.524 | 1 | core |  | 51 | 1.8 | 0.07 | 9.7 |
| 27 | 7.4 | 5.1 | 0.353 | 0.066 | 0.04 | 17:47:19.8744 | -28:22:19.524 | 1 | core |  | 38 | 1.41 | 0.09 | 4.3 |
| 28 | 5.5 | 8.0 | 0.353 | 0.044 | 0.027 | 17:47:19.92 | -28:22:19.56 | 1 | core |  | 59 | 2.68 | 0.06 | 3.1 |
| 31 | 20.9 | 12.9 | 0.353 | 0.091 | 0.033 | 17:47:19.9104 | -28:22:19.452 | 1 | core | 4 | 96 | 2.0 | 0.04 | 11.3 |
| 55 | 10.7 | 6.8 | 0.353 | 0.12 | 0.031 | 17:47:19.8336 | -28:22:18.3 | 2 | core | 18 | 50 | 1.9 | 0.09 | 6.0 |
| 59 | 51.6 | 8.4 | 0.353 | 0.2 | 0.077 | 17:47:19.836 | -28:22:18.012 | 1 | core | 22 | 62 | 2.53 | 0.06 | 28.6 |
| 64 | 8.2 | 8.9 | 0.353 | 0.05 | 0.031 | 17:47:19.8888 | -28:22:17.94 | 1 | core |  | 66 | 1.57 | 0.05 | 4.5 |
| 68 | 4.2 | 5.0 | 0.353 | 0.054 | 0.027 | 17:47:19.8456 | -28:22:17.904 | 1 | core | 26 | 37 | 2.1 | 0.1 | 2.5 |
| 71 | 10.1 | 9.4 | 0.353 | 0.052 | 0.035 | 17:47:19.8864 | -28:22:17.832 | 1 | core |  | 70 | 1.27 | 0.04 | 5.5 |
| 74 | 5.2 | 4.2 | 0.353 | 0.055 | 0.046 | 17:47:19.9056 | -28:22:17.76 | 1 | core | 29 | 31 | 2.5 | 0.1 | 3.2 |
| 75 | 35.1 | 8.9 | 0.353 | 0.115 | 0.067 | 17:47:19.872 | -28:22:17.688 | 1 | HII_new | 30 | 66 | 1.48 | 0.05 |  |
| 77 | 4.6 | 5.8 | 0.353 | 0.048 | 0.03 | 17:47:19.9416 | -28:22:17.724 | 1 | core | 27 | 43 | 2.16 | 0.08 | 2.6 |
| 81 | 12.2 | 9.8 | 0.353 | 0.09 | 0.027 | 17:47:19.98 | -28:22:17.58 | 1 | core | 31 | 73 | 2.06 | 0.05 | 6.7 |
| 85 | 20.2 | 7.9 | 0.353 | 0.088 | 0.058 | 17:47:19.872 | -28:22:17.472 | 2 | core | 33 | 59 | 2.59 | 0.06 | 11.2 |
| 86 | 18.7 | 5.9 | 0.353 | 0.122 | 0.062 | 17:47:19.8936 | -28:22:17.472 | 1 | core |  | 44 | 2.52 | 0.09 | 10.7 |
| 87 | 40.5 | 13.7 | 0.353 | 0.106 | 0.056 | 17:47:19.9872 | -28:22:17.436 | 1 | core | 32 | 102 | 1.89 | 0.03 | 21.8 |
| 88 | 35.5 | 6.3 | 0.353 | 0.148 | 0.1 | 17:47:19.9392 | -28:22:17.328 | 1 | core | 35 | 47 | 1.91 | 0.08 | 20.2 |

: First 25 entries of the Sgr B2 N catalog at 1 mm. The full catalogs for each pointing are available in machine-readable format.

# Radial core distribution

We show the core volume number density distribution as a function of distance from the center of each of the two main clusters in Figure [18](#radial_distribution). The distributions follow a power law with a slope of 2 near the center and increases to 3 at the very edges. This distribution calculation does not take into account the radial decrease in sensitivity of our data, thus the core number density at large distances is underestimated. A sudden increase in the core number density for Sgr B2 M at $7\times10^4$ AU is caused by a large number of sources in the vicinity of Sgr B2 South.

![](radial_distribution.png)

[^1]: We tested a variety of combination of number of concentric annuli (10, 15, 20, 30), *min_value* (3$\sigma$, 4$\sigma$, 5$\sigma$), *min_delta* (0.5, 0.7, 1.0), and *min_npix* (2, 3, 5). We inspected each combination by hand to find a compromise between reducing the number of false positives due to artifacts and noise and increasing the number of likely positives.

[^2]: The polygon regions are available on GitHub with the rest of the reduction code: <https://github.com/nbudaiev/SgrB2_ALMA_continuum>

[^3]: Using the most recently measured distance of 8.127 kpc (cite: GRAVITYCollaboration2018) would result in 7% lower masses.

[^4]: We extrapolate the original luminosity-accretion-based definition of stages for low-mass sources to their high-mass analogues from (cite: Robitaille2006).

</paper>

Write the methods card for this paper.