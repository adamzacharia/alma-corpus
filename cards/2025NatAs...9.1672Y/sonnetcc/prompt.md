# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025NatAs...9.1672Y\sonnetcc\reply.txt

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
 "bibcode": "2025NatAs...9.1672Y",
 "title": "Winding motion of spirals in a gravitationally unstable protoplanetary disk",
 "year": 2025,
 "journal": "Nature Astronomy",
 "first_author": "Yoshida, Tomohiro C.",
 "n_authors": 8,
 "arxiv_id": "2509.19761",
 "doi": "10.1038/s41550-025-02639-y",
 "alma_projects_linked_by_archive": [
  "2013.1.00226.S",
  "2013.1.00694.S",
  "2013.1.00798.S",
  "2016.1.00484.L",
  "2018.1.01055.L",
  "2023.1.00525.S"
 ]
}
```

Paper text:
<paper>
# Winding Motion of Spirals in a Gravitationally Unstable Protoplanetary Disk

\[1\],

2\], ,

3\],

4\], ,

5\], ,

6\],

7\], ,

# Introduction

Observations of exoplanets have revealed the existence of giant planets on orbits much wider than the Solar system planets (cite: akes13). For instance, in the HR 8799 system, four giant planets are detected at radii of 20-70 au from the central star (cite: maro08). The presence of the wide-orbit giant planets poses a challenge to planet formation theories. According to the conventional bottom-up core accretion scenario, where the small dust grains grow with coagulation to create a planetary core and then accrete the gas in a disk (cite: poll96), the formation timescale for giant planetary cores at these wide orbits is longer than the typical disk lifetime (cite: armitage2020). As an alternative mechanism, direct in-situ formation via disk fragmentation due to gravitational instability (GI) has been proposed (cite: boss97) although planet-planet/star scattering may be another possibility (cite: rode17). More recent simulations have suggested that full disk fragmentation is not necessarily required. Only marginally gravitationally unstable disks may efficiently form planetary cores, which could solve the time scale problem for the bottom-up core-accretion scenario (cite: rice04; bole10; baeh22; baeh23; long23a; long23b; rowt24). Therefore, it is critical to observationally reveal if GI can indeed happen in protoplanetary disks.

One of the most evident signatures of GI is spiral arms (cite: toom64; dong15). Indeed, such spiral arms have been observed in some protoplanetary disks (cite: muto12; huan18). However, spiral arms do not necessarily mean GI. Such spirals can also be induced by planet-disk interaction (cite: dong18), stellar flybys (cite: cuel19), and shadows cast by an inner disk (cite: mont16). Since their morphology resembles each other, it is generally challenging to distinguish those possibilities.

In particular, interpretations with GI or planet-disk interaction may result in different scenarios of planet formation. Planet-induced spirals indicate an already-formed planet at a large radius, requiring planet formation to occur at an early evolutionary stage of the protoplanetary disk. On the other hand, GI-induced spirals may suggest that the disk has enough gas for planet formation even at a relatively later stage, and planets can be formed there via GI. A robust way to distinguish the two mechanisms is to characterize the motion of spirals. Theories predict that the GI-induced spirals follow the local Keplerian motion (cite: coss09) (See also Method [4.3](#sec:theory) ), while the planet- (or flyby-) induced spirals follow the Keplerian motion at the companion’s radius (cite: dong16). Recently, thanks to the increasing number of high-quality observations, it is possible to observe the motion of the spirals. Indeed, efforts with high-resolution infrared imaging observations have been made (cite: ren20; xie23; ren24). However, they suggested that the major spirals in the studied disks are induced by a fairly massive planet (or low-mass companion). Another way to distinguish the scenarios is to investigate kinematical structures in spectral lines such as CO (cite: hall20; spee24). However, they trace the upper layer of the outer region in disks, which is different from the region where the wide-orbit exoplanets are detected.

In this article, we target a protoplanetary disk around IM Lup. IM Lup is classified as a classical T Tauri star with a mass of $M_\star {\sim} 1.1\ M_{\odot}$ (cite: teag21) and located at 158 pc (cite: gaia2022) from the Earth. The disk has been thoroughly studied, with numerous substructures characterized and stringent constraints on its physical properties being derived. In particular, the mm-continuum emission was resolved at a very high angular resolution (${\sim}7$ au) by the DSHARP ALMA Large program (cite: andr18; huan18), revealing grand-design spiral arms, and triggering follow-up studies to understand their origin. In the infrared image, there is no significant shadow (cite: aven18), excluding the shadow scenario. Analysis of the rotation curves retrieved from CO line observations conducted by the MAPS ALMA Large Program (cite: ober21) obtained a kinematically-constrained disk mass of 0.1 $M_{\odot}$ (cite: loda23). Such a large disk mass can be converted to Toomre’s Q (cite: toom64) ${\sim}1$, suggesting that the disk may be gravitationally unstable. Additionally, there are other supports of GI in the IM Lup disk. (cite: paneq24) found evidence for strong turbulence which can be induced by GI, although they used the CN lines tracing the elevated layer. A vertical extension of the dust disk is also suggested which may also suggest strong turbulence (cite: bosm23). Further, the assumption that GI controls the gas surface density profile is consistent with the polarimetric infrared and mm-continuum images (cite: ueda24). On the other hand, other studies report kinematical detections of embedded Jupiter-mass planets, making alternative explanations for the spirals (cite: pint20; verr22). By distinguishing the two scenarios, GI or planet-driven, we can benchmark our current understanding of planet formation; can wide-orbit giant planets be formed via GI in a relatively-evolved Class II disk? Otherwise, is there an already-formed giant planet? Furthermore, confirming one of the scenarios itself is important for characterizing the disk structure and physical processes (cite: ueda24).

Thanks to the high interest, this disk has been observed several times with relatively high spatial resolutions using ALMA, spanning a period large enough to investigate the motion of the spirals.

# Detection of spiral motion

## Observations

The IM Lup disk has been observed with a setup optimized for high angular resolution continuum observations in 2017, 2019, and 2024, resulting in a seven-year time baseline. These serve as the data used for this project. For the years of 2017 and 2019, we use the archival ALMA data delivered from the DSHARP (cite: andr18) and MAPS (cite: ober21) collaboration, respectively. The MAPS project observed two different frequency settings at 226 and 257 GHz in 2019. Although their time baseline is negligibly small, we treat the two images in 2019 separately as epochs of 2019a (226 GHz) and 2019b (257 GHz). The epoch of 2024, currently unpublished, was observed between Dec. 2023 and Aug. 2024 (PI: T. Yoshida, ID: #2023.1.00525.S). We describe the details of observations and data reduction in Methods. We determine the representative date of each epoch as the mean observation date of the long-baseline observations because they have higher positional accuracy than the more compact configurations. The key information of observations is summarized in Table [1](#tab1).

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Epoch | Representative Date \[MJD\] | Frequency | ALMA Band | Baselines | Project ID | Noise level |
|  |  | (GHz) |  | \(m\) |  | ($\rm \mu Jy\ beam^{-1}$) |
| 2017 | 2017 Oct 10 \[58036\] | 238.984 | Band 6 | 15-13894 | 2016.1.00484.L (cite: andr18) | 21 |
| 2019a | 2019 Aug 13 \[58708\] | 226.053 | Band 6 | 15-3638 | 2018.1.01055.L (cite: ober21) | 28 |
| 2019b | 2019 Aug 20 \[58715\] | 257.029 | Band 6 | 15-3396 | 2018.1.01055.L (cite: ober21) | 26 |
| 2024 | 2024 Mar 22 \[60391\] | 330.172 | Band 7 | 15-2517 | 2023.1.00525.S | 31 |
|  |  |  |  |  |  |  |

: Observation Details

By adjusting the visibility weighting and convoluting a Gaussian, the beam sizes of all images are arranged to $150 \times 101$ mas with a position angle of 144.5 deg so that a circular beam with an FWHM of $150$ mas is obtained when the images are deprojected to face-on. All the images used in the analysis are shown in Figure [1](#fig_all). In each epoch, spiral arms are robustly detected.

![](images.pdf)

## Dust rotation curve

![](deprojected.pdf)

![](deprojected_v3.pdf)

We deproject the images with known geometrical parameters (cite: ober21; teag21), correct the intensity difference among frequencies as explained in Methods, and plot in Figure [2](#deproj). In Figure [3](#deproj2), the same data as Figure [2](#deproj) is plotted, but the spirals are emphasized by partially subtracting the axisymmetric component (see Extended Data). Here, we plot the spiral ridges specified by (cite: huan18), which uses the original high-resolution DSHARP image taken in 2017, with the temporal variations of the ridges expected for the local Keplerian rotation. In addition, we add points following the local Keplerian rotation at $r=0\mbox{\ensuremath{.\!\!^{\prime\prime}}}12$ as a guide. It is clear that there is a temporal variation in the observed images, and they are visually consistent with the local Keplerian rotation, especially in the inner region. This can also be seen in an animation based on Figure [3](#deproj2) (Extended Data).

To quantitatively analyze the time variability of the three images, we introduce two approaches as described in detail in Methods. In the first approach (“Image-fitting analysis”, see Method [4.2.2](#image_fitting)), we assume a parametrized angular velocity profile, $\omega(r)$, where $\omega(r)$ is a power-law of a radius $r$ with a constant floor. The original high-resolution DSHARP image (cite: andr18) is azimuthally shifted according to the angular velocity profile and the time separation, and compared with the last three epochs after beam-convolution. On the other hand, in the second approach (“Radius-by-radius analysis”, see Method [4.2.3](#radius_radius)), we azimuthally shift the images radius-by-radius and find the optimal azimuthal shift between images. Although this approach may be affected by the limited spatial resolution, it is advantageous that no assumption of the angular velocity profile is needed.

The resultant dust rotation curve is plotted in Figure [4](#rot_curve).

![](rot_curve.pdf)

The motion of the spirals is successfully detected in both approaches, where they agree well with each other. The dust rotation curve exactly matches the local Keplerian rotation, while it is significantly different from the rigid body rotation. As described in the introduction, the detection of the local Keplerian motion of the spirals directly suggests that these spirals are being driven by GI.

# Implications and Future Direction

The spirals in the dust continuum image are evident from $r<20$ au up to $r {\sim} 200$ au (cite: huan18). This study suggests that GI can happen in the primary planet-forming region, where most planets are thought to be formed. GI happens if the gas surface density is sufficiently large and Toomre Q is comparable or smaller than unity (cite: toom64). Indeed, the disk mass measurement using the CO rotation curves implies $Q{\sim}1.0-2.5$ across the whole disk (cite: loda23).

The winding motion suggests that these spirals are transient. The pitch angle may soon become very small, diminishing the spirals in the Keplerian time scale. However, there are several spirals up to $r {\sim} 200$ au with moderate pitch angles of ${\sim}10-20^\circ$ (cite: huan18). Unless all spirals are formed very recently at the same time, it is more reasonable to consider that the spirals are continuously formed and diminished. This may indicate that the disk is gravitationally self-regulated, maintaining the marginally unstable state with $Q {\sim} \mathcal{O}(1)$. This scenario is also supported by the successful reproduction of multi-band continuum observations under the assumption of gravitational self-regulation (cite: ueda24). Gravitational self-regulation implies that the disk does not cause fragmentation on a short time scale, which is consistent with the fact that two-armed left-right symmetric spirals are evident in the IM Lup disk. This is in contrast to another disk with confirmed GI, AB Aur, where much more complex structures are observed (cite: spee24).

Such marginally (un)stable conditions may accelerate the formation of planetary cores (cite: rice04; bole10; baeh22; baeh23; long23a; long23b; rowt24). If this happens in this radius range, it can be directly compared with detected wide-orbit giant planets as seen in the HD 8799 system (cite: maro08). On the other hand, the direct formation of giant planets by disk fragmentation in the future requires a shorter cooling time scale and/or a more massive disk. This route may be possible if more material is supplied from the interstellar medium by late-stage infall as recently suggested in the Lupus star-forming region, where IM Lup resides (cite: wint24a; wint24b). Indeed, theoretical studies suggest that two-armed spirals can be more likely dominant when there is significant mass infall onto the disk (cite: hars11; tsuka11; tsuka15; tomi17)(see Methods [4.3](#sec:theory)), which is consistent with the IM Lup disk. Another system with a confirmed GI, AB Aur(cite: spee24), also exhibits infall streamers (cite: spee25). It is implied that late infall from the ISM may play a significant role in the evolution and dynamics of protoplanetary disks. It is notable that such disk fragmentation may also produce not only giant planets but also brown dwarf companions (cite: krat10).

Thanks to the growing number of archival data, time-domain astronomy is becoming available even in the field of planet formation (cite: teag22; debe23; kuo24). Regarding the IM Lup disk, although we already demonstrated that we can even model-independently determine the dust rotation curve for each radius, the accuracy becomes higher for a longer time baseline and higher spatial resolution. For example, in the next ALMA cycle 12 (2026), it is expected that spirals at $r=40$ au will have moved by ${\sim}15^\circ$ or $70$ mas compared to the DSHARP image. This can be perfectly resolved with the beam size of the original DSHARP image ($44$ mas). As the signal-to-noise ratio of the spiral arm contrast exceeds ${\sim}10$ at this radius (cite: huan18), the positional accuracy of ${\sim}5$ mas is achievable (cite: alma_tech). Therefore, if an image that has comparable quality to DSHARP is available, the spiral speed between the two epochs can be determined with an accuracy of ${\sim}10\%$. This kind of high-accuracy measurement of the dust rotation curve will bring a unique opportunity to investigate disk structure in detail. For example, we will be able to detect if the GI spiral propagation speed deviates from the Keplerian speed by more than 10 %, further constraining the disk mass (cite: coss09).

Overall, confirmation of GI makes the primary planet-forming region in the IM Lup disk an excellent laboratory for studying protoplanetary disks and planet formation.

# Methods

## Observation details, data reduction and imaging

### 2017 image

For the first epoch, we used the self-calibrated DSHARP measurement set available on their website (cite: andr18) and performed imaging by employing the CLEAN algorithm with the $\tt mtmfs$ deconvolver in the `tclean` task of the Common Astronomy Software Applications (CASA, version 6.5.5 (cite: CASA)). Since this epoch has larger baselines compared to other epochs (Supplementary Table [2](#tab:image)), for a fair comparison, we employed ${\tt uvtaper} = 0\mbox{\ensuremath{.\!\!^{\prime\prime}}}08$. Several weighting schemes were tested to reduce the noise level with the required beam size being kept. We found that the super-uniform weighting with ${\tt npixels=10}$ achieves this. As a CLEAN mask, we adopted an elliptical mask with a semi-major axis of $2.''0$ with the geometrical parameters of the IM Lup disk (the position angle of 144.5 deg and inclination angle of 47.5 deg (cite: ober21; teag21)), which were also used in other epochs. The resultant beam size was $81 \times 81$ mas with a position angle of $41$ deg and the RMS noise level was 18 ${\rm \mu Jy\ beam^{-1}}$. The image was re-convolved with a Gaussian to obtain a common beam size of $150 \times 101$ mas.

### 2019 images

The MAPS dataset was adopted for the epochs of 2019a and 2019b (cite: ober21; sier21). The original continuum visibility data were kindly provided by the MAPS collaboration. We made an image with a robust parameter of $0$, resulting in a beam size of $110 \times 80$ mas with a position angle of $-81$ deg. The RMS noise level was estimated to be $28$ and $27\ {\rm \mu Jy\ beam^{-1}}$ for 2019a and 2019b, respectively. We reconvolved these images in the same way as the 2017 image.

### 2024 image

In ALMA Cycle 10 (# 2023.1.00525.S, PI. T. Yoshida), the IM Lup disk was newly observed with two different spectral setups. The first setup was centered ${\sim}339$ GHz and observed on Dec. 9, 2023, Dec 15, 2023, Jun. 27, 2024, and Jul. 05 2024 with an extended configuration (C43-6), and on Apr. 30, 2024, and Aug. 24 2024 with a compact configuration (C43-3). The total integration time was 3.8 hours. The second setup was centered ${\sim}321$ GHz and observed on May. 29, 2024 with the configuration C43-4, totaling 1.4 hours of integration.

The two setups were separately self-calibrated after running the pipeline calibration. Note that we did not apply the automated self-calibration but manually performed it. For the first setup, the spectral windows were originally configured to observe the 331 GHz continuum emission, $\rm ^{12}CO\ J=3-2$, and $\rm ^{13}CO\ J=3-2$ lines. We used the 331 GHz continuum and $\rm ^{12}CO\ J=3-2$ spectral windows in the following analysis because they dominate the effective total bandwidth. Note that the $\rm ^{12}CO\ J=3-2$ line was flagged here and will be discussed in a future study. We performed five rounds of iterative phase-only self-calibration for the short-baseline data. Solution intervals were set to the duration of execution blocks in the first round, and shortened to $80$ s in the final round. Then, we combined the self-calibrated short-baseline with the long-baseline data. Additional eight rounds of phase-only self-calibration with solution intervals of the duration of the execution blocks to 20s, and one round of amplitude self-calibration with a solution interval of the execution block duration were applied. The RMS noise level was improved by a factor of 1.7 before and after self-calibration of the combined data set. The second setup targeted the 315 and 328 GHz continuum emission, $\rm C^{18}O\ J=3-2$, and $\rm ^{13}C^{18}O\ J=3-2$ lines. We used all spectral windows after flagging the lines. We performed seven rounds of phase-only self-calibration with the solution intervals from the execution block (EB) length to 15 s and one round of amplitude self-calibration with the solution intervals of the EB length.

After combining all the data, we additionally ran one round of the phase-only self-calibration to align the phase center. Finally, we CLEANed the data and obtained the image at a representative frequency of 330.172 GHz. We adopted a robust parameter of 0 to achieve the required beam size without significantly losing the sensitivity, while that of 0.5 was used during self-calibration. The resultant synthesized beam size was $110 \times 90$ mas with a position angle of $-77$ deg. The RMS noise level was estimated to be $29\ {\rm \mu Jy\ beam^{-1}}$. The image was reconvolved to have the common beam. Imaging parameters are summarized in Supplementary Table [2](#tab:image).

## Analysis

### Image normalization

The four images are observed at different frequencies. The longest time baseline images (2017 and 2024) have a frequency separation of ${\sim}30\%$. Additionally, the absolute flux uncertainty of ALMA might alter the intensity. Therefore, in advance of detailed analyses, we normalize the images to fairly compare the four images.

First, all images are positionally aligned by specifying the disk center by fitting an elliptical Gaussian to the central bright component. Then, we deproject the images by adopting the measured geometrical parameters of the IM Lup disk, which were also used as the CLEAN mask (the position angle of 144.5 deg and inclination angle of 47.5 deg (cite: ober21; teag21)). We azimuthally average the de-projected images and obtain the radial intensity profile. At each radius, the observed images are divided by a ratio of their azimuthally averaged profile to that of the 2017 image.

We then iteratively determine the disk center in the following way. First, we perform the image-fitting analysis (Sec [4.2.2](#image_fitting)), where we have parameters for a disk offset from the image center. The obtained offsets are then used to deproject the images again. The deprojected images are then repeatedly used for the image-fitting. We iterate this procedure four times and check the convergence of the offset parameters.

This normalization enables us to focus on only the azimuthal variation. The normalized images indeed resemble each other except for a small rotation of the pattern (Figures [2](#deproj) and [3](#deproj2)). An animation made from these normalized images is presented in Extended Data.

### Image-fitting analysis

In this analysis, we first prepare the original high spatial resolution ($44\times43$ mas, PA$=115^\circ$) DSHARP image that is available as a fits file on the official website as a reference image. The image is then convolved to have a circular beam with an FWHM of 65 mas after deprojection, which is more than twice as good as the common resolution, and deprojected using the geometrical parameters. Here, the disk center is specified by 2D-Gaussian fitting to the central bright component.

We assume that the disk pattern motion follows $$\begin{equation}
 \label{eq:omega}
    \omega(r) = \omega_0 \left( \frac{r}{1''} \right)^{-\gamma} + \omega_f,
\end{equation}$$ where $\omega_0$ and $\omega_f$ control the absolute value of angular velocity while $\gamma$ indicates the radial dependence of it. These quantities are treated as free parameters. This parametric form is an assumption, but can be fitted to both cases: GI- and/or planet-induced spirals. The deprojected reference image is rotated according to Equation ([\[eq:omega\]](#eq:omega)) and convolved with a Gaussian again to match the common beam size of 150 mas. Then, we compare them with the 2019a, 2019b, and 2024 images in terms of a log-likelihood function, $$\begin{equation}
 \label{eq:loglike}
    -\frac{1}{2} \sum_{i} \sum_{\rm image} \left( \frac{ I_i - I_{\rm ref} }{\sigma_{i - {\rm ref}}} \right)^2,
\end{equation}$$ where $I_i$ is the images in the epoch $i$, $I_{\rm ref}$ is the reference image after rotating and parallel-shifting by $(dx, dy)$ for each epoch. Although we spatially align the images in advance (Sec [4.2.1](#imnorm)), we can simultaneously treat the effect of the alignment accuracy by taking the offset $(dx, dy)$ as free parameters. The summation $\sum_{\rm image}$ is taken on the spatial domain. We only sum up the radial range of $r=0\mbox{\ensuremath{.\!\!^{\prime\prime}}}065-0\mbox{\ensuremath{.\!\!^{\prime\prime}}}7$, where the inner edge is limited by the beam size of the DSHARP image and the outer edge is limited by the spiral detection (cite: huan18). $\sigma_{i{\rm-ref}}$ is the standard deviation of a residual map between the epoch $i$ and the reference image. To sample the posterior distribution of the free parameters, we use a Python package `emcee` (cite: emcee) in practice. We adopt broad non-informative priors (Supplementary Table [3](#tab2)). We employ 128 walkers and 5000 steps, with the first 3000 steps discarded as burn-in.

The resulting percentiles and best-fit values that maximize the posterior probability are tabulated in Supplementary Table [3](#tab2). The rotation curve with uncertainties is estimated to be $$\begin{equation}
\omega(r) = 0.11^{+0.12}_{-0.06} \left( \frac{r}{1''} \right)^{-1.9^{+0.44}_{-0.49}}\ {\rm deg\ yr^{-1}}.
\end{equation}$$ The floor term ($\omega_f$) is not well constrained but only an upper limit is obtained, which is negligible at the radial region of interest (see Figure [4](#rot_curve)). Using the stellar mass of $1.1\ M_\odot$ and considering the stellar gravity, the Keplerian velocity profile is $$\begin{equation}
 \label{omega_kep}
\omega_{\rm kep}(r) \simeq 0.19 \left( \frac{r}{1''} \right)^{-1.5}\ {\rm deg\ yr^{-1}},
\end{equation}$$ which is consistent with the derived profile within the uncertainty. Note that we neglect the self-gravity of the disk. On the other hand, the rigid body rotation expected for the planet-induced spiral is $$\begin{equation}
 \label{omega_planet}
\omega_{\rm planet}(r) \simeq 0.30 \ {\rm deg\ yr^{-1}},
\end{equation}$$ which differs from the constrained rotation curve by at least $4\sigma$ in $\gamma$.

In Supplementary Figure [8](#fig:corner), we plot the marginal probability distributions. The case for GI is shown with the blue lines while the planet-induced case is marked with the orange lines (cite: pint20). We perform the kernel density estimate on the MCMC sample with `scipy.stats.gaussian_kde` (cite: scipy) and calculate the probability normalized by the maximum value. The parameters of the local Keplerian rotation (Eq. [\[omega_kep\]](#omega_kep)) and the Keplerian rotation at 117 au (Eq. [\[omega_planet\]](#omega_planet)) return $0.7$ and $7\times10^{-50}$, respectively. These correspond to 0.9$\sigma$ and 15$\sigma$, respectively, showing that the GI-induced scenario is significantly preferable compared to the planet-induced scenario.

### Radius-by-radius analysis

In the image-fitting analysis (Sec [4.2.2](#image_fitting)), we assumed that the radial rotation profile is described as Equation [\[eq:omega\]](#eq:omega). To check if there is a non-power-law motion, we performed an analysis for each radius in this subsection. As a function of radius $r$ and azimuthal angle of $\theta$, the intensity profile of the normalized epoch $i$ image can be expressed as $I_i(r, \theta)$. We consider all combinations in the four images and calculate a residual between a pair. In practice, we define a function $$\begin{eqnarray}
\chi^2(r, \omega) = \sum_{i<j} \sum_\theta \left( \frac{ I_i(r, \theta) - I_j(r, \theta - \omega \Delta T_{i,j} ) }{\sigma_{i,j}} \right)^2
\end{eqnarray}$$ where $\Delta T_{i,j}$ is a time separation between epoch $i$ and $j$, and $\omega$ is the angular velocity that we aim to constrain at each $r$. $\sigma_{i,j}$ is given as $$\begin{equation}
\sigma_{i,j} = \sqrt{ \sigma_i^2 + \sigma_j^2 },
\end{equation}$$ where $\sigma_i$ is the standard deviation of epoch $i$. At each $r$, we calculate $\chi^2$ for various $\omega$ and find an optimal $\omega$ that minimizes $\chi^2$. The optimal $\omega$ indicates the averaged angular velocity among three epochs. This method is straightforward, however, it is difficult to accurately estimate the uncertainty of $\omega$ if there is a signal correlation with intensity gradient across radii. Indeed, the spatial separation of the spiral in one epoch is similar to the beam size in our images, implying this is the case. However, it would be useful to calculate the $1\sigma$ uncertainty from the parameters where $|\chi^2 - {\rm min ( \chi^2 )|} = 1$, which is provided as error bars in Figure [4](#rot_curve). Here, the radial bin is taken logarithmically. In addition, we present the map of the normalized probability distribution for each pair and plot in Supplementary Figure [5](#fig:epcomp).

### The quantity we measured

In the methods presented in this paper, we measure the pattern speed using all azimuthal information at each radius. This means that we do not assume any radial structure such as disk-global spiral arms. Therefore, even if there is temporal variation in the radial structure such as disconnection of spirals (see Section [4.3](#sec:theory)), the pattern speed can be measured.

Still, we have to care about what we exactly trace. Since the observations have a limited spatial resolution, we might be biased to the spirals with low azimuthal modes ($m$) due to smoothing out (cite: dipi14). However, in the case of the IM Lup disk, the high spatial resolution image (cite: huan18) showed that the $m=2$ is likely the dominant mode because the detected number of spiral arms is only two even in the well-spatially resolved region ($r \gtrsim 50\ {\rm au}$). Therefore, what we measure in our analysis is the pattern speed of the dominant $m=2$ spiral arms.

## Comments on spiral pattern speed expected for GI

The speed of GI-induced spiral patterns has been investigated via hydrodynamic simulations. A three-dimensional simulation by (cite: coss09) showed that the spiral pattern speed is roughly Keplerian at each radius via Fourier analysis of all azimuthal modes. The small deviation from the Keplerian speed ($<15\%$) depends on the disk-to-stellar mass ratio $q$. (cite: beth21) performed a more detailed analysis of the temporal variability of the spiral structure in self-gravitating disks. Interestingly, in a run with $q=1/3$, they found that the spiral wakes radially disjoint and meet another wake as they rotate. This means that large-scale spirals only appear momentarily or stochastically (see their Fig. 10). In this case, we cannot define the pattern speed of individual spiral arms; observable large-scale spiral structures may continuously appear and disappear. However, their Fourier analysis suggested that the pattern speed computed from all azimuthal modes is roughly Keplerian as (cite: coss09) found. They also performed Fourier analysis by only focusing on the dominant modes of $2\leq m \leq6$, showing that the rotation profile is “piecewise” rigid body rotation. However, the deviation from the Keplerian speed is still moderate and up to $30\%$ (see their Fig.11). Additionally, they ran simulations with various $q$. In the case of $q=1$, they found that the dominant azimuthal mode is $m=2$ and their pattern speed is close to the Keplerian speed at every radius. It is notable that the dominant azimuthal mode is roughly scaled as $m{\sim}1/q$ (cite: dong15), implying that $q{\sim}0.5$ might be enough to see a similar situation. We also note that these results are somewhat different from the classical linear theory with many simplifications (cite: linshu64), where each spiral is specified with the mode numbers and rigidly rotates at a specific angular speed.

These simulations assume that the disk is well-isolated from the interstellar medium (ISM). However, it is known that material infall onto the disks may affect the GI-induced spirals. For example, (cite: hars11) found that infall makes low-order, global modes of spiral arms. Even in the case with a moderate $q$ of 0.1, low-order modes that are otherwise only seen for $q=0.2$ are observed. (cite: tsuka15) also showed that $m=2$ is the dominant mode of a disk with infall. (cite: tomi17) performed three-dimensional magneto-hydrodynamic simulations of a disk in a collapsing molecular cloud core and presented that grand design $m=2$ spiral arms are generated. Here, the mass accretion rate onto the disk from the envelope is one order of magnitude higher than that onto the star from the disk. They found that the spiral arms rotate at the local Keplerian speed. The spiral arms wind up on a Keplerian time scale but recurrently form because of the mass loading due to infall, resulting in a high spiral occurrence probability of ${\sim}50\%$. This picture can be clearly seen in an animation they provided.

In summary, these theoretical studies suggest that $m=2$ spiral arms moving at the local Keplerian speed should be observed when $m=2$ is the dominant mode. This is possible when the disk is massive and/or there is a significant infall onto the disk from the ISM. Note that, if a larger $m$ is dominant rather than $m=2$, the pattern speed of the $m=2$ spiral may deviate from the local Keplerian since the average speed of all modes is almost Keplerian (cite: coss09; beth21).

In the IM Lup disk, $m=2$ is likely the dominant mode (Sec [4.2.4](#sec:measured)). If we consider an isolated disk, this is inconsistent with the disk mass of $q\simeq0.1$ suggested by the CO rotation curve analysis (cite: loda23). There may be two ways to solve the paradox. First, the disk mass or surface density at the region we analyzed could be larger than a disk with $q\simeq0.1$, given that there might be some level of uncertainty on the kinematic measurement (cite: andr24). Second, there may be significant infall onto the IM Lup disk from the ISM, making low modes more dominant (cite: hars11).

The infall scenario is in line with the recently proposed paradigm, where significant mass infall due to the Bondi-Hoyle-Lyttleton (BHL) accretion is needed to explain disk characteristics even in the Class II stage (cite: pado24; wint24a). Indeed, (cite: wint24b) found that the stellar accretion rate is spatially correlated in the Lupus star-forming region where IM Lup resides, suggesting that mass accretion from the ISM is effective. Based on their estimate, the BHL accretion rate onto the disks can be ${\sim}10$ times higher than the stellar accretion rate, which may be a preferable condition for the GI induced by infall (cite: hars11; tomi17). In addition, it is theoretically suggested that GI-induced spiral arms are observable only in the first $10^4$ yrs in an isolated system (cite: hall19). Given the age of the Lupus star-forming region (${\sim}1-3\ {\rm Myr}$(cite: galli20)), it requires significant mass loading in the late stage.

Although there has been no direct evidence of infall onto the IM Lup disk itself, there is a possible infall motion detected in the CO line in the RU Lup disk which is located at just ${\sim}10$ arcmin or ${\sim}0.5$ pc from IM Lup on the plane of the sky (cite: huan20). In another system with a confirmed GI, AB Aur (cite: spee24), (cite: spee25) detected infalling gas and concluded that the infall induces GI. Future sensitive observations of gas around IM Lup are the key to testing this picture.

# Extended Data

We provide the animation of the spiral motion (Supplementary Video). For visibility purposes, the spiral structure is emphasized in the following way. First, we extracted the radial intensity profile by taking the azimuthal average of the normalized images. Then, original images with $20\%$ enhanced intensities are subtracted by axisymmetric images created using the radial profile so that we can easily see the non-axisymmetric structures together with the radial dependence of the intensity. We also plot the spiral ridges specified by (cite: huan18) with the temporal variations of the ridges expected for the local Keplerian rotation as in Figure [2](#deproj).

# Declarations

- Data availability: The data used for this study are available on the ALMA science archive (<https://almascience.nao.ac.jp/aq/>). The project IDs are 2016.1.00484.L, 2013.1.00226.S, 2013.1.00694.S, 2013.1.00798.S, 2018.1.01055.L, and 2023.1.00525.S.

- Code availability: The codes used for the analysis are available from the corresponding author upon reasonable request.

- Acknowledgements: We thank the anonymous referees for their helpful comments that improved the manuscript. We also thank Dr. Kengo Tomida for the helpful discussion on the spiral speed. We acknowledge Dr. Anibal Sierra for providing the calibrated MAPS continuum data. This paper makes use of the following ALMA data: 2016.1.00484.L, 2013.1.00226.S, 2013.1.00694.S, 2013.1.00798.S, 2018.1.01055.L, and 2023.1.00525.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work was supported by Grant-in-Aid for JSPS Fellows, JP23KJ1008 (T.C.Y.) and JSPS KAKENHI grant Nos. 19K03910, 20H00182 (H.N.).

- Author contribution: T.C.Y. led the observing proposal, data processing, analysis, and manuscript preparation. R.T. and M.B. were involved in the discussion of analysis and results as well as manuscript preparation. H.N., K.D., K.F., Y.Y., and T.T. were participants in writing the observing proposal and manuscript.

- Competing Interests: The authors declare no competing interests.

10 url urlprefix

(ref: akes13) Akeson, R. L. *et al.* . *Publ. Astron. Soc. Pac.* **125**, 989 (2013).

(ref: maro08) Marois, C. *et al.* . *Science* **322**, 1348 (2008).

(ref: poll96) Pollack, J. B. *et al.* . *Icarus* **124**, 62–85 (1996).

(ref: armitage2020) Armitage, P. J. *Astrophysics of planet formation* (Cambridge University Press, 2020).

(ref: boss97) Boss, A. P. *Science* **276**, 1836–1839 (1997).

(ref: rode17) Rodet, L. *et al.* . *Astron. Astrophys.* **602**, A12 (2017).

(ref: rice04) Rice, W. K. M., Lodato, G., Pringle, J. E., Armitage, P. J. & Bonnell, I. A. . *Mon. Not. R. Astron. Soc.* **355**, 543–552 (2004).

(ref: bole10) Boley, A. C. & Durisen, R. H. . *Astrophys. J.* **724**, 618–639 (2010).

(ref: baeh22) Baehr, H., Zhu, Z. & Yang, C.-C. . *Astrophys. J.* **933**, 100 (2022).

(ref: baeh23) Baehr, H. *Mon. Not. R. Astron. Soc.* **523**, 3348–3362 (2023).

(ref: long23a) Longarini, C., Lodato, G., Bertin, G. & Armitage, P. J. . *Mon. Not. R. Astron. Soc.* **519**, 2017–2029 (2023).

(ref: long23b) Longarini, C., Armitage, P. J., Lodato, G., Price, D. J. & Ceppi, S. . *Mon. Not. R. Astron. Soc.* **522**, 6217–6235 (2023).

(ref: rowt24) Rowther, S. *et al.* . *Mon. Not. R. Astron. Soc.* **528**, 2490–2500 (2024).

(ref: toom64) Toomre, A. *Astrophys. J.* **139**, 1217–1238 (1964).

(ref: dong15) Dong, R., Zhu, Z., Rafikov, R. R. & Stone, J. M. . *Astrophys. J. Lett.* **809**, L5 (2015).

(ref: muto12) Muto, T. *et al.* . *Astrophys. J. Lett.* **748**, L22 (2012).

(ref: huan18) Huang, J. *et al.* . *Astrophys. J. Lett.* **869**, L43 (2018).

(ref: dong18) Dong, R., Najita, J. R. & Brittain, S. *Astrophys. J.* **862**, 103 (2018).

(ref: cuel19) Cuello, N. *et al.* . *Mon. Not. R. Astron. Soc.* **483**, 4114–4139 (2019).

(ref: mont16) Montesinos, M. *et al.* . *Astrophys. J. Lett.* **823**, L8 (2016).

(ref: coss09) Cossins, P., Lodato, G. & Clarke, C. J. . *Mon. Not. R. Astron. Soc.* **393**, 1157–1173 (2009).

(ref: dong16) Dong, R., Fung, J. & Chiang, E. . *Astrophys. J.* **826**, 75 (2016).

(ref: ren20) Ren, B. *et al.* . *Astrophys. J. Lett.* **898**, L38 (2020).

(ref: xie23) Xie, C. *et al.* . *Astron. Astrophys.* **675**, L1 (2023).

(ref: ren24) Ren, B. B. *et al.* . *Astron. Astrophys.* **681**, L2 (2024).

(ref: hall20) Hall, C. *et al.* . *Astrophys. J.* **904**, 148 (2020).

(ref: spee24) Speedie, J. *et al.* . *Nature* **633**, 58–62 (2024).

(ref: teag21) Teague, R. *et al.* . *Astrophys. J. Suppl. Ser.* **257**, 18 (2021).

(ref: gaia2022) Gaia Collaboration *et al.* . *Astron. Astrophys.* **674**, A1 (2023).

(ref: andr18) Andrews, S. M. *et al.* . *Astrophys. J. Lett.* **869**, L41 (2018).

(ref: aven18) Avenhaus, H. *et al.* . *Astrophys. J.* **863**, 44 (2018).

(ref: ober21) Öberg, K. I. *et al.* . *Astrophys. J. Suppl. Ser.* **257**, 1 (2021).

(ref: loda23) Lodato, G. *et al.* . *Mon. Not. R. Astron. Soc.* **518**, 4481–4493 (2023).

(ref: paneq24) Paneque-Carreño, T. *et al.* . *Astron. Astrophys.* **684**, A174 (2024).

(ref: bosm23) Bosman, A. D., Appelgren, J., Bergin, E. A., Lambrechts, M. & Johansen, A. . *Astrophys. J. Lett.* **944**, L53 (2023).

(ref: ueda24) Ueda, T., Tazaki, R., Okuzumi, S., Flock, M. & Sudarshan, P. . *Nature Astronomy* **8**, 1148–1158 (2024).

(ref: pint20) Pinte, C. *et al.* . *Astrophys. J. Lett.* **890**, L9 (2020).

(ref: verr22) Verrios, H. J., Price, D. J., Pinte, C., Hilder, T. & Calcino, J. . *Astrophys. J. Lett.* **934**, L11 (2022).

(ref: ober15) Öberg, K. I. *et al.* . *Astrophys. J.* **810**, 112 (2015).

(ref: clee17) Cleeves, L. I. *et al.* *Astrophys. J. Lett.* **843**, L3 (2017).

(ref: pint18) Pinte, C. *et al.* . *Astron. Astrophys.* **609**, A47 (2018).

(ref: wint24a) Winter, A. J., Benisty, M. & Andrews, S. M. . *Astrophys. J. Lett.* **972**, L9 (2024).

(ref: wint24b) Winter, A. J., Benisty, M., Manara, C. F. & Gupta, A. . *arXiv e-prints* arXiv:2409.17220 (2024).

(ref: hars11) Harsono, D., Alexander, R. D. & Levin, Y. . *Mon. Not. R. Astron. Soc.* **413**, 423–433 (2011).

(ref: tsuka11) Tsukamoto, Y. & Machida, M. N. . *Mon. Not. R. Astron. Soc.* **416**, 591–600 (2011).

(ref: tsuka15) Tsukamoto, Y., Takahashi, S. Z., Machida, M. N. & Inutsuka, S. . *Mon. Not. R. Astron. Soc.* **446**, 1175–1190 (2015).

(ref: tomi17) Tomida, K., Machida, M. N., Hosokawa, T., Sakurai, Y. & Lin, C. H. . *Astrophys. J. Lett.* **835**, L11 (2017).

(ref: spee25) Speedie, J. *et al.* . *Astrophys. J. Lett.* **981**, L30 (2025).

(ref: krat10) Kratter, K. M., Murray-Clay, R. A. & Youdin, A. N. . *Astrophys. J.* **710**, 1375–1386 (2010).

(ref: teag22) Teague, R. *et al.* . *Astrophys. J.* **930**, 144 (2022).

(ref: debe23) Debes, J. *et al.* . *Astrophys. J.* **948**, 36 (2023).

(ref: kuo24) Kuo, I. H. G., Yen, H.-W. & Gu, P.-G. . *Astrophys. J. Lett.* **975**, L33 (2024).

(ref: alma_tech) Cortes, P. *et al.* *ALMA Cycle 10 Technical Handbook* (2023). URL .

(ref: CASA) CASA Team *et al.* . *Publ. Astron. Soc. Pac.* **134**, 114501 (2022).

(ref: sier21) Sierra, A. *et al.* . *Astrophys. J. Suppl. Ser.* **257**, 14 (2021).

(ref: emcee) Foreman-Mackey, D., Hogg, D. W., Lang, D. & Goodman, J. . *Publ. Astron. Soc. Pac.* **125**, 306 (2013).

(ref: scipy) Virtanen, P. *et al.* . *Nature Methods* **17**, 261–272 (2020).

(ref: dipi14) Dipierro, G., Lodato, G., Testi, L. & de Gregorio Monsalvo, I. . *Mon. Not. R. Astron. Soc.* **444**, 1919–1929 (2014).

(ref: beth21) Béthune, W., Latter, H. & Kley, W. . *Astron. Astrophys.* **650**, A49 (2021).

(ref: linshu64) Lin, C. C. & Shu, F. H. *Astrophys. J.* **140**, 646 (1964).

(ref: andr24) Andrews, S. M., Teague, R., Wirth, C. P., Huang, J. & Zhu, Z. . *Astrophys. J.* **970**, 153 (2024).

(ref: pado24) Padoan, P., Pan, L., Pelkonen, V.-M., Haugbølle, T. & Nordlund, Å. . *Nature Astronomy* **9**, 862–871 (2025).

(ref: hall19) Hall, C. *et al.* . *Astrophys. J.* **871**, 228 (2019).

(ref: galli20) Galli, P. A. B. *et al.* . *Astron. Astrophys.* **643**, A148 (2020).

(ref: huan20) Huang, J. *et al.* . *Astrophys. J.* **898**, 140 (2020).

# Supplementary Information

## Frequency effect

The analyzed images have different representative frequencies. Throughout the analyses, we assumed that the different frequencies trace the same dust surface density structure, and therefore, the apparent difference observed between different epochs is temporal variation. If this assumption were not valid, the frequency difference could artificially produce the temporal variation.

![](chi2maps.pdf)

To test this based on the data, we plot the normalized probability maps for each epoch in Supplementary Figure [5](#fig:epcomp). Although the uncertainties are different depending on the panels, the optimized $\omega$ curves are similar independently of the choice of epochs. In particular, for example, although the 2019b image has a frequency offset of $14\%$ compared to the 2019a image, the pairs of 2019a & 2024 and 2019b & 2024 are similar to 2017 & 2024. This means that the frequency effect is minimal.

In addition to the data-oriented approach, we theoretically investigate whether the assumption is valid or not in two different cases where the dust emission is optically thick or thin.

###  Optically thick case 

If the dust emission is optically thick and the disk has a non-zero inclination, the observed positional difference could be attributed to the different emitting surfaces between the two frequencies. This effect can be seen in a comparison of a spiral in infrared and millimeter wavelength images of a protoplanetary disk, where the emitting layers are significantly different (cite: brow21). However, given that our images are both in millimeter wavelengths, which trace the relatively large dust grains near the midplane, the effect should be small, as shown in the following. Assuming an extreme case where the longer wavelength image traces the midplane and the shorter wavelength one traces the upper layer at $z$ au from the midplane, the projected difference of the same surface density structure between the two wavelengths can be expressed as $\Delta X_{\rm emis} = z \tan i$, where $i$ is the inclination angle of the disk. $z$ can be approximated by the dust scale height, which is typically less than a few percent of the gas scale height (cite: vill20; vill22) and at most comparable to it (cite: doi21). If we assume the ultimate case where the dust scale height is similar to the gas scale height and set $z = 0.05r$ (cite: ueda24), we can estimate an upper limit of $\Delta X_{\rm emis}$ as $$\begin{equation}
    \Delta X_{\rm emis} = 0\mbox{\ensuremath{.\!\!^{\prime\prime}}}017 \left ( \frac{r}{50\ {\rm au}} \right ).
\end{equation}$$ This is sufficiently smaller than the observed positional difference at 30 au (${\sim}0\mbox{\ensuremath{.\!\!^{\prime\prime}}}05$), suggesting that the frequency effect is negligible. Furthermore, we note that this effect should make the positional difference in the same direction with respect to the disk’s major axis. This is different from what is expected for rotation and suggested observationally.

###  Optically thin case 

In the case where the dust emission is optically thin, the observed positional difference could be attributed to the different dust opacities if the dust size distribution is changed across a spiral due to e.g. shock waves.

![](dust_il.pdf)

To investigate this possibility, we consider a model with two homogeneous dust slabs behind and beyond a spiral, where dust size distributions are different as illustrated in Supplementary Figure [6](#fig:dust_il). Assuming that the dust size distribution is a power law with a cut off at the maximum dust size $a_{{\rm max}, i}$, where $i=1,2$ is the number of the slab behind and beyond the spiral, the optical depth from each dust slab can be described as $$\begin{equation}
    \tau_i(\nu_j) = \kappa(a_{{\rm max}, i}, {\nu_j}) \Sigma_i,
\end{equation}$$ where $\kappa(a_{{\rm max}, i}, {\nu_j})$ is the dust opacity at the frequency $\nu_j$ $(j={\rm I}, {\rm I\hspace{-1.2pt}I})$ and the maximum dust size $a_{{\rm max}, i}$, and $\Sigma_i$ is the dust surface density of slab $i$. Under the condition where the two dust slabs are spatially unresolved, which is the case for this study, the observed position of the emission from the two slabs is their centroid. If the two slabs are optically thin and have the same temperature, the centroid of the emission with respect to the position of the slab $i$ is given as $$\begin{equation}
    X_{\rm emis}(\nu_j) =  \frac{ \tau_2(\nu_j)}{ \tau_1(\nu_j) + \tau_2(\nu_j) } X_{\rm phys},
\end{equation}$$ where $X_{\rm phys}$ is the physical seperation of the two slabs. The centroid difference between the two frequencies can be expressed as $$\begin{equation}
 \label{eq:dXemis}
    \Delta X_{\rm emis} = X_{\rm emis}(\nu_{\rm {\rm I\hspace{-1.2pt}I}}) - X_{\rm emis}(\nu_{\rm I}) = \left\{ 
        \frac{ \tau_2(\nu_{\rm I\hspace{-1.2pt}I})}{ \tau_1(\nu_{\rm I\hspace{-1.2pt}I}) + \tau_2(\nu_{\rm I\hspace{-1.2pt}I}) } - \frac{ \tau_2(\nu_{\rm I})}{ \tau_1(\nu_{\rm I}) + \tau_2(\nu_{\rm I}) }    
    \right\} X_{\rm phys}.
\end{equation}$$ The ratio $\Delta X_{\rm emis}/X_{\rm phys}$ suggests how the centroid of the emission changes between the two frequencies with respect to the physical separation of the two slabs. Therefore, if this ratio can be as large as unity, the detected positional difference may also be interpreted as an opacity effect. On the other hand, if it is sufficiently small, the detected positional difference cannot be explained by the opacity effect but by the temporal variation. For any combination of the dust sizes, $\Delta X_{\rm emis}$ is maximized when $\Sigma_1 = \Sigma_2$, so we can further write the upper limit of the ratio as $$\begin{equation}
   \frac{\Delta X_{\rm emis}}{X_{\rm phys}} = \frac{ \kappa(a_{{\rm max}, 1}, {\nu_{\rm I}})  \kappa(a_{{\rm max}, 2}, {\nu_{\rm I\hspace{-1.2pt}I}}) - \kappa(a_{{\rm max}, 1}, {\nu_{\rm I\hspace{-1.2pt}I}})  \kappa(a_{{\rm max}, 2}, {\nu_{\rm I}}) }{ \{ \kappa(a_{{\rm max}, 1}, {\nu_{\rm I\hspace{-1.2pt}I}} ) + \kappa(a_{{\rm max}, 2}, {\nu_{\rm I\hspace{-1.2pt}I}}) \} \{ \kappa(a_{{\rm max}, 1}, {\nu_{\rm I}} )- \kappa(a_{{\rm max}, 2}, {\nu_{\rm I}}) \} },
\end{equation}$$ for a combination of the dust sizes and frequencies.

![](dust_size.pdf)

We calculated the ratio for the DSHARP dust opacity model (cite: birn2018) for various combinations of maximum dust sizes with $\nu_{\rm I}= 240$ GHz and $\nu_{\rm I\hspace{-1.2pt}I}= 330$ GHz, which are the representative frequencies of 2017 and 2024 images (the longest time base-line), and plotted the results in Supplementary Figure [7](#fig:dust-size). The ratio is smaller than $0.1$ for a broad range of dust sizes. For a limited parameter space, the ratio takes a somewhat large maximum of ${\sim}0.24$ when the maximum dust size of the two slabs are $(a_{\rm max, 1}, a_{\rm max, 2}) = ( 5.5, 0.21 )\ {\rm mm}$. This means that, even if there is such a significant difference in the maximum dust size between the two slabs (i.e. across a spiral), the opacity difference can only make a positional difference of $0.24$ times their physical separation.

Based on our analysis, the apparent positional difference is ${\sim} 0\mbox{\ensuremath{.\!\!^{\prime\prime}}}05$ at 30 au from the central star. If this were the frequency effect, the physical separation of the two dust components should be as large as ${\sim}0\mbox{\ensuremath{.\!\!^{\prime\prime}}}2$. However, with our spatial resolution of $0\mbox{\ensuremath{.\!\!^{\prime\prime}}}15$, such a large physical separation should be spatially resolved, which is not the case (Figure 1 in the Main text). In other words, the maximum physical separation that is possible for our spatial resolution only allows the frequency effect to be sufficiently smaller than actually observed. In addition, in the case of the frequency effect, it is required to satisfy very limited conditions, where the maximum dust sizes are fine-tuned and differ by a factor of ${\sim} 26$ with a comparable dust surface density. Therefore, we conclude that the apparent positional difference is not due to the frequency effect but to the temporal variation.

## Supplementary figures and tables

We summarize the parameters used for imaging (Methods [2.1](#obs)) in Supplementary Table [2](#tab:image). The image-fitting (Methods [4.2.2](#image_fitting)) results are listed in Supplementary Table [3](#tab2). The marginal probability distribution is presented in Supplementary Figure [8](#fig:corner).

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Epoch | Weighting | *uv*-taper | Original beam | Sensitivity before convolution |
|  |  |  |  | ($\rm \mu Jy\ {\rm beam^{-1}}$) |
| 2017 | Super-uniform, ${\rm \tt npixels} = 10$ | $0\mbox{\ensuremath{.\!\!^{\prime\prime}}}08$ | $0\mbox{\ensuremath{.\!\!^{\prime\prime}}}081 \times 0\mbox{\ensuremath{.\!\!^{\prime\prime}}}081,\ 41^\circ$ | 18 |
| 2019a | Briggs, ${\rm \tt robust} =0$ | N/A | $0\mbox{\ensuremath{.\!\!^{\prime\prime}}}11 \times 0\mbox{\ensuremath{.\!\!^{\prime\prime}}}08,\ -81^\circ$ | 28 |
| 2019b | Briggs, ${\rm \tt robust} =0$ | N/A | $0\mbox{\ensuremath{.\!\!^{\prime\prime}}}09 \times 0\mbox{\ensuremath{.\!\!^{\prime\prime}}}08,\ -88^\circ$ | 27 |
| 2024 | Briggs, ${\rm \tt robust} =0$ | N/A | $0\mbox{\ensuremath{.\!\!^{\prime\prime}}}11 \times 0\mbox{\ensuremath{.\!\!^{\prime\prime}}}09,\ -77^\circ$ | 29 |
|  |  |  |  |  |

: Imaging Details

| Parameter | Prior | Percentiles | Best-fit | GI | Planet at 117 au | Unit |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| $\log_{10} \omega_0$ | $\mathcal{U}(-4.7, 5.3)$ | $-0.97^{+0.32}_{-0.39}$ | $-0.82$ | $-0.72$ | $-\infty$ | ${\rm deg\ yr^{-1}}$ |  |
| $\log_{10} \omega_f$ | $\mathcal{U}(-4.7, 5.3)$ | $<0.04$ | $-3.19$ | $-\infty$ | $-0.53$ | ${\rm deg\ yr^{-1}}$ |  |
| $\gamma$ | $\mathcal{U}(-5, 5)$ | $1.9^{+0.49}_{-0.44}$ | $1.75$ | $1.5$ | $0$ |  |  |
|  |  |  |  |  |  |  |  |

: Parameters and fitting results

![](corner.pdf)

10

url urlprefix

(ref: brow21) Brown-Sevilla, S. B. *et al.* . *Astron. Astrophys.* **654**, A35 (2021).

(ref: vill20) Villenave, M. *et al.* . *Astron. Astrophys.* **642**, A164 (2020).

(ref: vill22) Villenave, M. *et al.* . *Astrophys. J.* **930**, 11 (2022).

(ref: doi21) Doi, K. & Kataoka, A. . *Astrophys. J.* **912**, 164 (2021).

(ref: birn2018) Birnstiel, T. *et al.* . *Astrophys. J. Lett.* **869**, L45 (2018).

</paper>

Write the methods card for this paper.