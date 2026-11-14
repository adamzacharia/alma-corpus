# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...682A..61C\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...682A..61C",
 "title": "A dusty streamer infalling onto the disk of a class I protostar. ALMA dual-band constraints on grain properties and the mass-infall rate",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Cacciapuoti, L.",
 "n_authors": 18,
 "arxiv_id": "2311.13723",
 "doi": "10.1051/0004-6361/202347486",
 "alma_projects_linked_by_archive": [
  "2019.1.00951.S",
  "2019.1.01813.S",
  "2022.1.00126.S"
 ]
}
```

Paper text:
<paper>
# A dusty streamer infalling onto the disk of a class I protostar.

Observations of interstellar material infalling onto star- and planet-forming systems have become increasingly common thanks to recent advancements in radio interferometry. These structures have the potential to significantly alter the dynamics of protoplanetary disks, triggering the formation of substructures, inducing shocks, and modifying their physical and chemical properties. Moreover, the protoplanetary disks are replenished with new material, increasing the overall mass budget for planet formation.

In this study, we combine new ALMA band 3 and archival band 6 observations to characterize the dust content and infall rate of a 4,000 au arc-like structure infalling onto \[MGM2012\] 512 (hereafter M512), a class I young stellar object located in the Lynds 1641 region of the Orion A molecular cloud.

We detect the extended dust emission from this structure in both ALMA bands. We test whether the streamer’s velocity pattern is consistent with infalling trajectories by means of analytical streamline models. We measure for the first time spectral index maps and derive a dust opacity index profile along a streamer. We constrain its grain properties and mass.

We find that the arc structure is consistent with infalling motions. We measure a spectral index $\alpha \sim$ 3.2 across the entire structure, and a dust opacity index $\beta \sim$ 1.6. Given grain properties consistent with the measured $\beta$, the structure can host up to 245 M$_{\oplus}$ of dust, exceeding or being comparable to the mass of the inner, unresolved 600 au, which contains the protoplanetary disk of M512. Assuming typical ISM dust-to-gas ratio of 1%, free-fall timescales (50 kyr) imply total mass infall rates up to 1.5 $\cdot$ 10$^{-6}$ M$_{\odot}$/yr. M512 has been classified as an outbursting source with multi-epoch WISE photometry, representing an interesting case study to explore the possible connection between infalling streamers and accretion outbursts.

M512 is one-of-a-kind source, for which dust continuum emission of an arc-like streamer extending out to 4,000 au can be characterized in a dual-band analysis. The dust properties results ISM-like, implying a large dust mass. Such a massive streamer can strongly affect the evolution of the star- and planet-forming inner system.

# Introduction

Star and planet formation takes place in highly dynamical environments in which their accretion history can be far from being driven by the traditionally assumed symmetric collapse. Young stellar objects experience episodic, anisotropic accretion as they travel through the interstellar medium and gravitationally interact with it (cite: Lebreuilly2021; Kuffmeier2023). Modern radiointerferometers have recently revealed large-scale gaseous structures extending from young stars and their protoplanetary disks, at various evolutionary stages. These structures are more commonly observed in near-infrared (NIR) scattered light (cite: Ginski2021) or submillimeter molecular lines, such as CO (cite: Yen2019), HCO$^+$ (cite: akiyama2019), H$_2$CO (cite: Valdivia-Mena2022), HC$_3$N (cite: Valdivia-Mena2023), among others. Some of them are associated with infall of material, as a stream from the surrounding environment (cite: Tobin2010; Alves2020; Yen2014; Yen2019; Garufi2022; Pineda2022), via gravitational capture of a nearby cloud fragment during a close encounter (cite: Scicluna2014; Dullemond2019; Ginski2021; Gupta2023), or as the result of stripping of material due to stellar flyby events (cite: Cabrit2006; Dai2015; Kurtovic2018; Winter2018; menard2020; Dong2022).

These so called "streamers" have earned significant interest due to their potential impact on the inner star- and planet-forming system. Infalling material might induce perturbations in the disk, triggering instabilities (e.g., (cite: Bae2015), (cite: Hennebelle2017), (cite: Kuznetsova2022)). These instabilities could then generate exponentially growing vortices, which act as traps for dust particles, where efficient planetesimal formation might begin (cite: Barge1995). Massive infall can also induce inner-to-outer disk misalignments (cite: Kuffmeier2018; Kuffmeier2021; Ginski2021), generate spiral waves (cite: Thies2011; Hennebelle2017), induce accretion outbursts (cite: Bonnell1992; Aspin2003) and can result in shocks with the disk material, leading to localized and significant alterations in the physical and chemical conditions of the disk (cite: Garufi2022; Kuznetsova2022). These variations, in turn, can have a substantial impact on the structural and chemical evolution of the disk. Moreover, the infall of interstellar material can deliver significant amounts of mass to the central protostar and its protoplanetary disk, possibly helping in reconciling the discrepancy between protoplanetary disk masses and exoplanet masses ((cite: Manara2018), (cite: Mulders2021)). The simulations of (cite: Kuffmeier2023) provide an example of how protostars can sweep up material while moving through their natal clouds, and accrete substantial fractions of their final mass in regions even tens of thousands au away from the positions at which we observe them today.

In summary, infalling streamers are expected to dramatically influence the evolution of the star- and planet-forming systems involved. However, detecting and characterzing examples of such events is critical to constrain their frequency and magnitude, about which little is known so far.

![](total_maps.png)

Recently, (cite: grant2021) reported the detection of extended continuum and molecular millimeter emission around \[MGM12\] 512 (RA $=$ 05h40m13.789s, Dec $=$ -07d32m16.02s). Hereafter, we will refer to the source as M512, consistently with (cite: grant2021). This young source is located in the Lynds 1641 region of the Orion A molecular cloud at a distance of $\sim$ 420 pc, based on the Gaia DR3 parallax p $\sim$ 2.379$''$ (cite: Gaia2022). This distance is consistent with very long baseline interferometry estimates for Orion Nebula Cluster (e.g., 414$\pm$7 pc, (cite: Menten2007)). In this work, we assume d = 420 pc. The source has been classified as class I based on the 2$-$25$\mu$m slope of the spectral energy distribution, $\alpha_{2-25\mu m}\sim0.33$ ((cite: Caratti2012) and (cite: Megeath2012)). Finally, its main physical properties have been reported by (cite: Caratti2012) based on near-infrared spectroscopic measurements and we summarize them in Table [1](#tab:m512).

|                         |                 |     |     |
|:------------------------|:---------------:|:---:|:---:|
| Alternative ID          | IRAS 05377-0733 |     |     |
| RA                      |  05h40m13.789s  |     |     |
| Dec                     |  -07d32m16.02s  |     |     |
| SpT                     | M7.5 $\pm$ 1.5  |     |     |
| T$_{eff}$ \[K\]         | 2800 $\pm$ 200  |     |     |
| R$_{*}$ \[R$_{\odot}$\] |      3.71       |     |     |
| M$_{*}$ \[M$_{\odot}$\] |      0.15       |     |     |
| L$_{*}$ \[L$_{\odot}$\] |       0.9       |     |     |

: Stellar parameters of M512 as reported by (cite: Caratti2012), based on its spectral energy distribution and SofI near-infrared spectra.

Here, we present new ALMA Band 3 (B3) observations M512 and combine them with archival ALMA Band 6 (B6) data to constrain the dust properties and mass of the extended structure. In Sect. [2](#sec:obs), we describe the observations; in Sect. [3](#sec:kinematics) we discuss the infalling nature of the extended arc around M512; and in Sect. [4](#sec:spectral_index), we measure the spectral index and derive a profile of the dust opacity spectral index. We discuss the results and the possible origins of this structure in Sect. [5](#sec:discuss) and summarize our conclusions in Sect. [6](#sec:conc).

# Observations

M512 was observed with ALMA in B6 on 2019/11/27 (2019.1.01813.S, PI: van Terwisga, S.) and on 2019/12/12 (2019.1.00951.S, PI: Grant, S.). Both programs achieved a resolution of approximately 1.14$''$, and a reported maximum recoverable scale of roughly 11.7$''$. We refer the reader to (cite: grant2021) and (cite: vanterwisga2022) for further details and report the main characteristics of their observations in Tab. [\[table:1\]](#table:1).

We here present new ALMA B3 observations of M512 taken on 2023/01/16 (program 2022.1.00126.S, PI: Wendeborn, J.). These were designed to retrieve the 3 mm continuum flux of the extended emission around M512, first reported by (cite: grant2021) at 1.3 mm, with a similar resolution. The bandpass and flux calibrator is J0423-0120, the phase calibrator is J0542-0913 (see Tab. [\[table:1\]](#table:1)).

The B3 data were initially calibrated by ALMA staff using the Cycle 9 ALMA interferometric pipeline (cite: Hunter2023) within Common Astronomical Software Applications (CASA; version 6.4.1-12). The B6 data were instead calibrated by the ALMA staff using CASA version 5.6.1-8 for both programs. We carried out further data reduction and calibration steps in both bands using CASA version 6.2.1.7. First, the ALMA cubes for each execution block were inspected and additional flagging was applied when necessary, i.e. to mask out all spectral lines. Among these, we note that the same arc-like structure is clearly detected in DCO+ (216.11 GHz) and N$_2$D+ (231.32 GHz). These lines are not spectrally resolved and thus could not be used in our kinematic analysis (Sect. [3](#sec:kinematics)).

We then channel-averaged the spectral windows of every execution block. First, we imaged the channel-averaged visibilities with the *tclean* CASA task and fitted a Gaussian with *imfit* to identify the emission peak. Next, we used the *fixvis* function to shift the phase center to the position of the peak of M512 at the epoch of every observation. Since we are interested in measuring spectral indices, we checked for potential offsets among the visibility amplitudes of different execution blocks and found none above 3%.

We then phase-selfcalibrated the data. We computed the phase corrections on the continuum spectral windows of each execution block using *gaincal* and applied them with *applycal*. This step aimed to correct phase errors between executions and between spectral windows. We repeated this procedure three times, progressively shortening the solution interval. In the first round, we set the solution interval of *gaincal* to *inf*, combined the scans within each execution block and set gaintype $=$ "G", i.e. the gains were determined for each polarization and spectral window. In the second and third rounds, we combined the spectral windows of each block, shortened the solution intervals to 60 and 10 seconds, respectively, and set gaintype $=$ "T", to obtain one solution for both polarizations. At each round, we split and apply the table computed at the previous steps to each execution block. The selfcalibration yielded peak S/N improvements of about 15% as the phase of the visibilities were already well constrained. We did not find any appreciable improvement in the noise and signal-to-noise properties for phase-only selfcalibration steps with even smaller time intervals. The final peak signal-to-noise ratio of the B3 image is 355, and it is 218 for the B6 one.

Finally, we imaged the visibilities to carry out the rest of the analysis. Since the emission is extended, we ran the *tclean* routine setting *pbcor = True*, in order to correct for the primary beam attenuation. We deconvolved the images using the "hogbom" algorithm (cite: hogbom74) with the "briggs" weighting scheme, and we tried a number of "robust" parameter choices to find the optimal balance between resolution and sensitivity. We have finally carried out the analysis on images with robust $=$ 1, a pixel size of 0.2$''$ (84 au at the distance of M512, one seventh of the synthesized beam) and an image size of 300 pixels. When running *tclean*, we manually masked the emission, comprising of both the bright inner disc and the extended streamer, and CLEANed down to 1.5 times the image rms. Since we want to compare emission tracing the same physical scales, we used a *uvtaper* to weight the visibilities in order to obtain similar synthesized beams for the two bands (1.5$''$ x 1.2$''$, PA = 72$^{
\circ}$). Finally, we smoothed the images to the same resolution of 1.6$''$, roughly equal to the width of the extended emission at 3$\sigma$ level recovered by (cite: grant2021) with robust = 0.5 (see their Fig. 13). We recover an arc-like structure radially extending out to about 4,000 au. We note that that the length of the streamer, as observed in this study, is to be considered a lower limit since the interferometric observations might have filtered out larger-scale emission. Moreover, we report a C$^{18}$O $J = 2-1$ transition moment-one map of M512 obtained with the observations of ALMA program 2019.1.00951.S (Fig. [2](#fig:moment1)). In what follows, we focus on characterizing the kinematics and the dust content of this extended structure, to which we will refer as "streamer" hereafter.

# Streamer’s kinematics

Whether extended structures such as the one linked to M512 are actually infalling on the central protoplanetary disks is a problem that requires precise constraints on the system’s geometry and physical properties. In our case, the unknown details of the geometry of the inner disk, due to somewhat limited spatial resolution, introduce uncertainties in what regards the interpretation of the velocity structure around the source. To complicate the problem further, both the mass and system velocity are uncertain. The former is affected by the precision to which spectral types are determined by near infrared spectra (cite: Caratti2012), the high extinction of this region (e.g., (cite: Gutermuth2011)) and the contribution of the inner embedding material connected to an envelope remnant or to the streamer itself. Furthermore, the limited spectral resolution and the potentially high optical depth of the CO isotopologues limits the accuracy of estimation of the system velocity.

![](tipsy_model.png)

In this section, we analyse the C$^{18}$O J=2-1 transition already presented in (cite: grant2021). Among the other isotopologues, we chose this transition as its emission is optically thinner than the one of $^{12}$CO and $^{13}$CO and less affected by foreground absorption. We imaged the spectral cube containing the line’s spectral window with the same scheme of the continuum dataset. During the cleaning, we masked the emission manually, channel-by-channel, in order to capture its complex morphology.

The moment-one map shows an arc-like feature consistent with the 1.3mm dust continuum emission region, and it is characterized by a progression from lower to higher velocities when approaching the protostar from afar (Fig. [2](#fig:moment1)). This gradient may be indicative of infalling motions towards the inner object (as observed in e.g., Per-emb 2 (cite: Pineda2020), Per-emb 50 (cite: Valdivia-Mena2022)). The velocity transition between streamer and inner material might also indicate rotation of the innermost embedding material. We attempted to model the C$^{18}$O kinematics to constrain whether the data is consistent with infalling motion. We analysed the spectral cube with the *Trajectory of Infalling Particles in Streamers around Young stars* (TIPSY, Gupta et al., subm.). The input for the code are the mass of the central object and its line-of-sight velocity (v$_{sys}$). For the former, we set to 0.15 M$_{\odot}$, as reported in Table [1](#tab:m512). We note that the inner envelope mass, and even the streamer’s mass, might contribute significantly to influence the ballistic motion of a particle. For the latter, we explored a range of systemic velocities consistent with the observed C$^{18}$O spectral line, between 2.9 and 3.9 km/s. Based on these constraints, TIPSY solves analytical kinematics equations for an infalling parcel of gas that feels the gravity of a central source from (cite: Mendoza2009) and computes its trajectory along the region over which we detect emission, as well as the kinetic, gravitational (and thus total E$_{tot}$) energy of the parcel and its infall time scale. We overplot a TIPSY fit model to the moment-one map in Fig.[2](#fig:moment1) to show how the arc-like feature around M512 is consistent with the infall of material. The available data is consistent with infall for velocities in the explored range of v$_{sys}$, albeit the material results only loosely bound (E$_{tot} \lesssim$ 0) for v$_{sys} \gtrsim 3.7 km/s$. The TIPSY model constraints the infall time scales to about 50 kyr. We overplot the radial velocities as fitted by TIPSY in a position-velocity diagram (PVD, Fig.[2](#fig:moment1)) obtained using pvextractor (cite: Ginsburg2016). The PVD is extracted along the infalling trajectory shown in Fig.[2](#fig:moment1), and including the inner region. The width of the selected path is equivalent to the beam, 1.6$''$. The TIPSY model is consistent with the radial velocities of the observed emission. New observations will be key to constrain the geometry, system velocity and streamer’s mass effects on the infall trajectories.

In Sect. [5](#sec:discuss), we discuss further qualitative arguments that support the infall scenario against alternatives such as stripping due to a flyby, or the cavity wall of an outflow. We thus tentatively suggest that the arc-like structure detected around M512 is an infalling streamer.

# Spectral index

The slope of the radio spectrum: $$\begin{equation}
\mathrm{\alpha} = \frac{\log_{10}{\mathrm{F}(\nu_2)}-\log_{10}{\mathrm{F}(\nu_1)}}{\log_{10}{\nu_2}-\log_{10}{\nu_1}},
\label{eq:alpha}
\end{equation}$$ where $\nu_i$ are the observed frequencies, can provide valuable insights on the properties of interstellar dust grains. Given that the dust opacity follows a power law relation $\kappa \propto \nu^{\beta}$ in the millimeter end of the spectrum, in the optically thin regime and if the Rayleigh-Jeans (RJ) approximation holds, $\beta = \alpha-2$ (e.g., (cite: draine2006), (cite: BeckwithSargent1991), (cite: MiyakeNakagawa1993), (cite: Natta2007)). The typical dust opacity index observed for the interstellar medium, $\beta\sim1.6$, is usually interpreted in terms of maximum grain sizes of the dust population ranging from 100 Å to 0.3 $\mu$m (cite: Weingartner2001). On the contrary, a value $\beta<1$, which is often measured in class II objects, indicates the presence of larger grains, with sizes $a \geq 1$ mm in more evolved disks ((cite: BeckwithSargent1991), (cite: Ricci2010), (cite: Testi2014), (cite: Macias2021)).

In the following analysis, we present maps of the spectral index $\alpha$ and the profile of the dust opacity spectral index $\beta$ across the emission region of M512 and its streamer.

## Spectral index maps

![](sub_maps.png)

Using the ALMA B3 and B6 maps, we calculate the spectral index $\alpha$ at each pixel in our smoothed maps. This procedure yields the spectral index map shown in Fig. [1](#fig:m512). Within the inner $\sim$600 au region, centered on the protoplanetary disk of this young source, the spectral index is approximately $\alpha\sim2$, indicating optically thick emission (cite: BeckwithSargent1991). The high optical depth of this compact region suggests an optically thick disk, diluted on a more extended sky area by the finite resolution of the observations. To ensure that the spectral index of the inner end of the streamer is not contaminated by this central emission, we model and subtract the contribution of the latter. We fit a 2D Gaussian to the inner region in the image plane. The fitting results are provided in Table [\[tab:gaussfit\]](#tab:gaussfit), and the model and residuals are displayed in Appendix [8](#app:gaussfit). The compact emission extends for 1.4$''$ (2$\sigma$, 574 au), possibly comprising a combination of the inner end of the streamer, remnants of the original envelope of M512 and a more compact protoplanetary disk. Higher resolution observations will be key to discern the extent of the inner disk. We then subtract the Gaussian model from the image to isolate the contribution of the streamer (Fig. [3](#fig:streamer)). Finally, we compute the spectral index of the streamer emission, $\alpha_{S}$ (refer to Fig. [1](#fig:m512) and Fig. [3](#fig:streamer)). We observe a spectral index of approximately $\alpha_{S}\sim3.2$ along the entire streamer, which indicates optically thin emission. Given the dust temperature profile we consider to derive the dust opacity spectral index (see later Eq.[\[eq:alpha\]](#eq:alpha)), we derive $\tau = -\ln(1 - I_{\nu}/B_{\nu}(T)) < 0.05$ in B6 along the full arc. As a sanity check, we ran a similar analysis in the uv plane, where we subtracted a point source from the visibilities and then computed the spectral index as a function of uv-distance. We obtain consistent results (see Appendix [8](#app:gaussfit)).

## Dust opacity index profile

To investigate if and how dust optical properties change along the extended arc of M512, we divide the streamer in spatial bins and derive the dust opacity spectral index $\beta$ within each bin. In order to select the bins, we use a logarithmic spiral with manually-tuned parameters to adapt it to the shape of the extended emission. We then select points along the spiral as centers for circular apertures as large as the streamer’s width (see Fig. [4](#fig:beta_profile)). The aperture’s radius is twice the beam’s one and each aperture contains roughly 160 pixels. If we assume that the main heating mechanism for the dust is the irradiation from the central source, we can use to a first approximation the radial temperature profile that (cite: Motte2001) derived for spherical dusty envelopes: $$\begin{equation}
    \mathrm{T(r)} =  38 \mathrm{K} \Bigg( \frac{\mathrm{L}}{\mathrm{L}_{\odot}} \Bigg)^{0.2} \Bigg( \frac{\mathrm{r}}{100 \mathrm{au}} \Bigg)^{-0.4}.
    \label{eq:temp}
\end{equation}$$ This equation yields temperatures in a range of 21 to 8 K across the scales of the streamer, that is 600 to 4,000 au. We note that these distances from the central source assume the streamer lays in the plane of the sky. At $\lambda =$ 1.3 mm, a temperature T = 8 K implies that the RJ approximation is not valid ($h\nu$/k$_B$T $\sim$ 1). We thus introduce a correction to the simple $\alpha = \beta - 2$ case for the low temperatures which would otherwise artificially lower the derived $\beta$, that we then derive as: $$\begin{equation}
   \mathrm{\beta} = \frac{\log \Bigg[ \Big(\mathrm{F}_{\nu_2}(r)/\mathrm{F}_{\nu_1}(r) \Big) / \Big(\mathrm{B}_{\nu_1}(\mathrm{T}_{\mathrm{d}}(r))/\mathrm{B}_{\nu_2}(\mathrm{T}_{\mathrm{d}}(r)) \Big) \Bigg]}{\log(\nu_2 / \nu_1)},
    \label{eq:beta}
\end{equation}$$ where the ALMA B6 and B3 representative frequecies are $\nu_2 = 230$ GHz, $\nu_1 = 100$ GHz, T$_d$ is the temperature of the dust and B$_{\nu_i}$(T$_d$) is the Planck function value at the two frequencies.

Finally, we compute the statistical error on the spectral index as: $$\begin{equation}
    \delta  \mathrm{\alpha}^2 (= \delta \mathrm{\beta}^2) = \Bigg(\frac{1}{ln{\nu_2}-ln{\nu_1}}\Bigg)^2 \Bigg(\frac{\sigma_1^2}{\mathrm{F}_{\nu_1}^2} + \frac{\sigma_2^2}{\mathrm{F}_{\nu_2}^2}  \Bigg),
\end{equation}$$ where $\sigma_i$, $F_{\nu_i}^2$ are the primary beam corrected rms and fluxes in each distance bin for the two bands. We consider the same error for $\beta$ since we assume an exact value for the temperature in Eq. [\[eq:beta\]](#eq:beta). On top of the statistical error, one should consider ALMA’s systematic calibration uncertainty on B3 and B6 fluxes of 1$\sigma$ = 5% (cite: Remijan2019). Within the same bins, we also compute $\alpha$ using Eq. [\[eq:alpha\]](#eq:alpha) and show the resulting $\beta = \alpha-2$ proxy and the $\beta$(T) profile in Fig. [4](#fig:beta_profile).

We find a mean $\beta = 1.62 \pm 0.04$ along the whole structure. Finally, we have tested the two extreme scenarios in which the temperature is fixed at 21 or 8 K across the whole structure. In fact, it could be that the arc self-shields against the internal radiation, thus being colder on average or, on the contrary, that significant external irradiation from Orion OB stars could lead to higher temperatures in the outer arc (cite: Haworth2021)[^1]. In any case, the $\beta$ measured with both fixed temperatures only changes by $<$10% with respect to the one obtained using the temperature profile.

# Discussion

Here, we discuss the interpretation of the derived dust opacity index, we estimate the mass of the surrounding material, and weigh the implications such an event can bear on a planet-forming system, as well as its possible origins.

## Streamer’s dust properties

The retrieved continuum flux of the streamer around M512 implies a relatively large dust mass, that can be distributed either in large amounts of small grains or in smaller amounts of large grains. It is thus important to constrain the maximum grain size of the distribution in order to constrain its mass content.

In the case of a distribution of spherical compact grains, the Mie scattering theory predicts that the derived $\beta\sim$1.6 (Fig. [4](#fig:beta_profile)) is consistent with a dust population for which the maximum grain size is submicron (cite: draine2006). If the grains were instead porous, $\beta\sim$1.6 could be consistent with a dust distribution where the maximum grain size lays in a smoother range from submicron to a millimeter (e.g. (cite: Birnstiel2018)).

Recently, it has been suggested that dust can grow up to millimeter sizes even in protostellar envelopes. In fact, $\beta$ values lower than $\sim$1.6 have been measured in the inner envelopes of a sample of class 0/I objects (cite: Kwon09; Miotello2014; Galametz2019; Cacciapuoti2023). However, models show that dust cannot grow more than a few $\mu$m in more diffuse molecular clouds cores (cite: Ormel2009; Lebreuilly2023a), where the submillimeter dust opacity spectral index $\beta \sim$1.6 (cite: draine2006). Scattering light observations of these environments have also been independently interpreted as the presence of grains up to only $\sim$ 10 $\mu$m (cite: Steinacker2010; Steinacker2014; Steinacker2015). Thus, the $\beta = 1.6$ measured along the streamer of M512 is consistent with the properties of ISM-like dust grains.

![](beta_profile_streamer.png)

## Mass constraints and infall rate

The delivery rate of mass onto M512 is critical to assess the implications that the event might have for the subsequent evolution of the system. In the optically thin regime, the dust mass of the observed streamer can be derived as (cite: Hildebrand1983): $$\begin{equation}
    \mathrm{M} = \frac{\mathrm{d}^2 \mathrm{F}_{\nu}}{\kappa_{\nu} \mathrm{B}_{\nu}\mathrm{(T_d)}}
    \label{eq:mass}
\end{equation}$$ where d is the distance to the source, F$_{\nu}$ the flux density of the structure, $\kappa_{\nu}$ is the dust opacity and B$_{\nu}$(T$_d$) the value of the Planck function at frequency $\nu$. We consider a distance of 420 pc (see Section [1](#sec:intro)), and the temperature is given by Eq. [\[eq:temp\]](#eq:temp). In order to measure the mass of the streamer taking into account the expected temperature variation along the arc, we consider the logarithmic spiral we mentioned in Sect. [5.1](#sec:discuss_dust) and shown in Fig. [4](#fig:beta_profile). For each selected aperture on the spiral, we assign each pixel above the 3$\sigma$ threshold to the closest aperture center, measure the total flux in the bin so defined, and compute the temperature with Eq. [\[eq:temp\]](#eq:temp), where $r$ is the projected radial distance of each aperture center from the source.

Assuming DSHARP dust properties (cite: Birnstiel2018), the absorption opacity of a dust grains distribution characterized by ISM-like spectral indices as the one we measure for the streamer of M512, and a typical power-law $n(a) \propto a^{-3.5}$,

is $\kappa_{1.3mm} = 0.4$ g/cm$^{-2}$. The solid mass of the streamer thus amounts

to M$_{dust}^{streamer} =$ 245 $\pm$ 25 M$_{\oplus}$.

On the other hand, considering usual assumptions for protoplanetary disks to derive the mass of the inner region (e.g. (cite: Andrews2013), (cite: Pascucci2016), (cite: Ansdell2016)), i.e. a temperature of 20 K and an absorption opacity $\kappa_{1.3mm} =$ 2.25 g/cm$^{-2}$, we obtain M$_{dust}^{inner} =$ 58 $\pm$ 6 M$_{\oplus}$, given the integrated flux in Tab. [\[tab:gaussfit\]](#tab:gaussfit). The reported uncertainties on the derived masses only reflect the dominant flux calibration error of 10%. We note that since the compact, inner emission is optically thick, mass estimations for the inner region can be wrong by a factor up to $\sim$5 ((cite: Ballering2019), (cite: Ribas2020), (cite: Macias2021), (cite: Xin2023), (cite: Rilinger2023)) and that further underestimation of the millimeter-derived mass can be due to scattering effects in the very inner, optically thick region ((cite: Zhu2019), (cite: Liu2019)). Taking all of this into account, we find that the mass of the streamer seems to exceed or be comparable to the mass of the inner region. Given the resolution of the observations, this mass does not correspond to the mass of the protoplanetary disk alone but also accounts for contribution from the inner infalling material.

Finally, we can constrain the infall rate onto M512 and its disk. Considering the typical free-fall timescale, t$_{ff} \propto \sqrt{{r^3}/{G M}}$, a particle with null initial velocity would fall from 4000 au onto the 0.15 $M_{\odot}$ protostar in roughly 50 kyr. This estimate is consistent with the TIPSY outputs ran in Sect. [3](#sec:kinematics). Thus, assuming the whole streamer will infall onto the inner system, and a typical dust-to-gas ratio of 0.01, the total mass infall rate

is $\dot M$ = 1.5 $\cdot$ 10$^{-6}$ M$_{\odot}$/yr.

However, it is imperative to bear in mind that the infall rate may be lower if the streamer will not interact in its entirety with the inner protoplanetary disk. Consequently, while we undertake a discussion of the implications of our study under the assumption that the entire streamer will ultimately infall on the inner disk, we emphasize the sensitivity of these outcomes on the mass that will actually be captured by the source. Observations with higher spatial and spectral resolution are needed to clear the remaining sources of uncertainty in the analysis: the geometry of the inner system, the line-of-sight velocity of the star, and the impact of the infall via shock tracers such as SO (e.g., (cite: Garufi2022)).

It is noteworthy that outbursts observed for young stellar objects have been proposed to be triggered by massive accretion events (cite: Bonnell1992; Aspin2003). M512 might represent a rare case for which we witness a late infall event that is delivering mass at a significantly high rate.

Assuming infall of the entire structure, and outbursts durations of $\sim$100 yr, this rates would imply a possible future accretion event of 7.5$\cdot$10$^{-4}$ M$_{\odot}$/yr, or a series of smaller ones. For example, if accretion would build up material in the disk for 10 kyr[^2], this would imply FUOr-like accretion ($\sim$10$^{-4}$ M$_{\odot}$/yr, (cite: Kenyon1988)), which might then cause outbursts. The accretion rate of M512 has been characterized to be in a quite ordinary accretion state, i.e. L$_{acc} <$ L$_*$, with $\dot M \sim 2 \cdot 10^{-7}$ M$_{\odot}$/yr, based on single epoch observations (cite: Caratti2012). However, M512 has been classified as a bursting source based on multi-epoch WISE 3.4$\mu$m and 4.6$\mu$m photometry by (cite: Park2021). Over the course of 6.5 yr and with a time resolution of 0.5 yr, they observed three sharp increases of the flux by a factor $\sim$2.5 in both bands. This source represents an exciting testbed to explore the possible link between infalling streamers and accretion outbursts.

Furthermore, the mass infall rate onto M512 is similar to the one used by, e.g., (cite: Bae2015) and (cite: Kuznetsova2022) in their simulations, in which they found that material infalling at these high rates on protoplanetary disks has the power to drive significant substructures. M512 thus represents a unique source to probe whether infall can drive substructures, which are often regarded as birthplaces of planets.

We note that an additional source of uncertainty for the derived masses comes from the choice of dust opacities. While we have so far considered DSHARP opacities, other works have made use of different prescriptions, such as the DIANA opacities (cite: Min2016) or opacities constrained from solar system observations (cite: Pollack1994). These alternative choices would imply absorption opacities systematically larger in the submillimeter regime, up to $\sim$3 or 10 times the DSHARP ones, respectively. Thus the mass derived through them would be up to ten times lower both for the streamer and the inner disk. We point out that consistent choices of opacities imply the same ratio between the streamer and the disk’s mass.

## Origins and frequency

The origin of streamers is still a matter of debate. Some authors have proposed that they are a channelled inflow of material from protostellar envelopes or even from beyond the prestellar core scales (e.g., (cite: Yen2014), (cite: Yen2019), (cite: Pineda2020)). The extended emission in the surroundings of M512 discussed here, however, is not reminiscent of irregular envelopes and it is infalling in a seemingly ordered, arc-like manner (see Sect. [3](#sec:kinematics)). Moreover, CO observations seem to indicate that M512 lost most of its initial envelope (cite: grant2021). Other explanations involve the interaction of M512 with closeby objects, such as a flyby with another stellar object or interactions with close interstellar clouds.

Flyby events might be quite common in star-forming regions, especially during the protostellar stages, where stars form close to each other in clusters ((cite: Pfalzner2013), (cite: Winter2018b), (cite: Lebreuilly2021), (cite: offner2022)). In this sense, the morphology of M512 is reminiscent of the ones observed for RW Aurigae ((cite: Cabrit2006), (cite: Dai2015), (cite: Rodriguez2018)), AS 205 (cite: Kurtovic2018), UX Tau (cite: menard2020), and Z CMa (cite: Dong2022)), binary star systems for which a long molecular arm extends from the primary star and points toward a secondary object.

In Appendix [9](#app:flyby) we discuss how a close encounter might have occurred between M512 and another source a few hundreds kyr ago. This is much longer than most flyby events for which we still observe stripped material. Indeed, simulations suggest that the re-circularization of material happens in a few kyr (e.g., (cite: Cuello2023)), making the observation of such an event extremely unlikely. Moreover, spirals excited due to stellar flybys are usually of the same order of magnitue of the outer radius of the stripped disk ($\lesssim$ 3 R$_{out}$, (cite: Smallwood2023)), while the arc we observe extends for thousands of astronomical units. The flyby scenario is thus hard to reconcile with our observations. We expand on our arguments in Appendix [9](#app:flyby).

The velocity gradient we observe in the arc of M512 (see Fig.[2](#fig:moment1)) is also consistent with the capture of material from a nearby cloud with a non-zero initial velocity. The material is then accelerated toward the central star. (cite: Scicluna2014) and (cite: Dullemond2019) explored the possibility that forming protostars might capture material from nearby small clouds as they travel within their natal environment. In this scenario, due to its non-null initial angular momentum, the material does not fall directly on the protostar but feeds the disk, or even forms a new one. This capture process has been proposed to explain the observed infrared excess around very evolved, $\geq$10 Myr old stars (cite: Beccari2010; DeMarchi2013a; DeMarchi2013b) and the $M_* - \dot M$ correlation in pre-main-sequence stars (cite: Padoan2005; ThroopBally2008; Padoan2014). Examples of objects that might be undergoing such scenarios are AB Aur (cite: Nakajima1995; Grady1999) and HD 100546 (cite: Ardila2007). The hydrodynamics simulations of (cite: Dullemond2019) and (cite: Kuffmeier2020) demonstrate how the capture of cloud fragments would lead to the formation of arc-shaped structures, much like the one observed in M512 ((cite: Scicluna2014), (cite: Dullemond2019)). Additionally, (cite: Scicluna2014) computed the probability of cloudlet capture by a stellar object in different environment density conditions. They found that for a region in which dense clumps occupy a fraction f$_V$ of the total volume, the number of stars that one expects to observe as cloudlet capture accretors at a given time is an order of magnitude larger than the volume filling-factor of dense clumps. Thus, if dense clumps only occupy a volume fraction as small as f$_V =$10$^{-4}$, we expect one in a thousand objects to show late accretion. We note that M512 is one of three objects showing extended continuum emission in the Survey of Orion Disks with ALMA (SODA) (cite: vanterwisga2022), that includes 873 objects. The overall median accreted mass in all the simulation grids they explored is 0.01$M{_\odot}$. They also demonstrated that the structures formed due to capture can last even for 10$^4$-10$^5$ yr (see their Section 2). These values are comparable to M512’s streamer mass and free-fall timescale. Furthermore, we note that dust grains in ISM clouds should not exceed a few tenths of microns (e.g., (cite: Mathis1977)), thus further supporting a scenario for which the $\beta \sim 1.6$ measured in Sect. [5.1](#sec:discuss_dust) indicates ISM-like grains. Larger-scale maps than available at present would be helpful in linking the streaming material around M512 with the neighboring environment, and to understand whether the observed streamer presented in this work is replenished by the surrounding environment or represent the full extent of the mass that will be delivered on the disk of M512.

Lastly, continuum emission has sometimes been detected along the cavity walls of protostellar outflows where, due to higher temperatures, the dust might be brighter (e.g., (cite: Maury2018), (cite: LeGouellec2023)). In the case of M512, however, the arc-like emission is quite bent and not reminiscent of more cone-like outflow cavities (e.g., (cite: garufi2021), (cite: hsieh2023)). Additionally, CO emission is optically thick and the C$^{18}$O line profile indicates low velocities, about 500-700 m/s, and we observe both redshifted and blueshifted emission within the same arc (Fig. [2](#fig:moment1)). Finally, M512 is a class I, very low mass star, implying such a large outflow would be unlikely. It is thus not straightforward to reconcile our observations with the outflow scenario. We also note that our mass estimates would still be valid with the caveat that, at the cavity wall of a low velocity outflow, temperatures would be slightly higher than what we assumed for the cold streamer case (e.g., (cite: Droz2015), (cite: Flores-Rivera2021)). This would imply a mass a factor of a few lower, and thus still a significantly high dust mass (M$_{dust}$ $\gtrsim$ 50 M$_{\oplus}$). Considering typical class I outflows mass loss rates of a few 10$^{-8}$ M$_{\odot}$/yr (cite: Fiorellino2021), it would take over 1 Myr yr to lift M$_{dust}$ $\gtrsim$ 50 M$_{\oplus}$, while the mass loss rates quickly decline over the first $\sim 10^5$ yr of star formation. We thus tentatively discard this scenario. However, non-isotropic accretion from the envelope to the central source has been suggested to happen along the cavity walls of outflows ((cite: LeGouellec2019), (cite: Cabedo2021)). Observations of bright and optically thin outflow tracers will help clear out this case together with higher resolution observations of the central source to resolve the geometry of the disc and thus the direction along which an outflow could be launched.

In summary, given the constraints of Sect. [3](#sec:kinematics), and the qualitative arguments laid in this section, we reinforce our suggestion that the arc-like structure around M512 is an infalling streamer, possibly caused by a cloudlet capture event.

## Implications for planet formation

Streamers can have significant implications for planet formation and protoplanetary disk evolution. M512 represents a unique case for which dust continuum emission is detected in two ALMA bands, thus enabling us to better constrain its dust properties and mass content. The structure we observe is delivering a substantial amount of mass to the inner disk of M512, carrying several significant implications that we discuss in what follows. In what follows, we assume the whole streamer will infall on the central disk, consistently with the bound solutions found in the kinematical analysis we lay out in Sect. [3](#sec:kinematics). However, it is possible that only a fraction of the detected structure will infall on the inner system, thus the infall rate could be a factor of a few lower.

To begin with, the streamer is replenishing the system with an amount of mass that exceeds or is comparable to the mass of the protoplanetary disk. If the infalling dust were captured by a nearby cloudlet where maximum grain sizes are 1-10 $\mu$m (see [5.1](#sec:discuss_dust)), a total mass of up to 0.075 M$_{\odot}$ may infall on the disk of M512. The infall can potentially double the available mass for planet formation in the system. The mass budget problem, i.e. the apparent lack of necessary mass to form known exoplanetary systems starting from the class II protoplanetary disks we observe in the Galaxy (e.g., (cite: Testi2016), (cite: Manara2018), (cite: Williams2019), (cite: Sanchis2020), (cite: Tychoniec2020)), could thus be partially bridged by late infall of material on evolved disks. Additionally, the supply of material around low mass stars such as M512 could represent a possibility for the formation of gas giants around these kind of objects. While such exoplanets are, at least rarely, detected (e.g., (cite: Morales2019), (cite: Bryant2023)), their formation pathways remain unclear (cite: Liu2020).

Additionally, M512 represents a candidate to study the origin of substructures in evolved disks. In fact, infall of material onto disks has been proposed to be among the mechanisms that can trigger such substructures (cite: Thies2011; Hennebelle2017; Kuffmeier2018; Ginski2021). (cite: Bae2015) and (cite: Kuznetsova2022) demonstrated how infall can drive the formation of rings and gaps in disks with infall rates consistent with what we find for M512. A possible instance of this process was detected by (cite: Segura-Cox2020), who observed rings and gaps in in the protoplanetary disk around Oph IRS63, recently shown to be subject to anisotropic infall (cite: Flores2023). Another example is HL Tau, where both disk structures and an infalling streamer were observed ((cite: AlmaPartenership2015), (cite: Yen2019)). Studying the impact of streamers on disks that display substructures can inform us about the necessity, or lack thereof, to invoke planets to carve such structures at early stages of star and planet formation. Moreover, the formation of substructures and the induction of turbulence in the disk can alter the timescales of grain growth since clumping of grains is more efficient where these conditions are present. Higher-resolution observations of M512 will be key to unveil the geometry of its inner disk and search for potential substructures.

Lastly, the infalling material will impact the disk at some radius, and will potentially shock with its surroundings. In the vicinity of the shock, the disk temperature will rise (cite: Garufi2022). Thus, the streamer will change the physical and chemical properties of the disk, as shown for e.g, HL Tau in (cite: Garufi2022). M512 is known to undergo outbursts (cite: Park2021) that can greatly alter the physical and chemical properties of protoplanetary disks influencing both the evolution of dust (cite: Houge2023) and gas (cite: Owen2014; Wiebe2019). Whether these are linked to the infalling streamer or not will be an exciting matter for further studies.

# Conclusions

We have presented new ALMA B3 observations of M512 in the Lynds 1641 region of the Orion A molecular cloud and combined them with archival ALMA B6 data to constrain the dust properties of a 4,000 au arc-like structure extending from the central source. We find that:

- The structure is characterized by a velocity gradient consistent with infall (see Fig. [2](#fig:moment1)). The morphology of the extended emission and the velocity gradient are consistent with the capture and infall of material from a nearby cloudlet.

- The compact ($\sim$ 600 au) region surrounding M512 is optically thick at the wavelengths considered here ($\alpha\sim2$). Higher resolution observations will be key to study this inner region and constrain its geometry and the impact of the infall event, which we cannot probe with current observations.

- The streamer is optically thin with $\alpha_{S}\sim3.2$ along the whole structure. Accounting for the low temperatures expected at its scales, we obtain a dust opacity spectral index $\beta$ = 1.62$\pm$0.04, typical of ISM-like dust (Sect. [5.1](#sec:discuss_dust)).

- We constrain the dust mass of the streamer to be $\sim 250 M_{\oplus}$[^3] (see Sect. [5.2](#discuss:mass)). Given typical free-fall timescales, the streamer could be delivering up to 1.5 $\cdot$ 10$^{-6}$ M$_{\odot}$/yr onto the inner disk and last about 50 kyr. We note this estimates assume the whole structure will infall.

- We discuss the possible origins and impact that this event can have on the planet-forming disk of M512, including the replenishment of mass, the formation of substructures, and changes in the physical and chemical conditions due to shocks and/or accretion outbursts (Sect. [5.4](#discuss:implications)).

Streamers observations represent a new window on star and planet formation, reminding us how this process is not isolated and is highly dynamic within star forming regions. Further observations will be necessary to both link streamers to their potential large-scale progenitors and test the impact they have on planet-forming disks on the smaller scales. M512 is a quite unique source that will play a crucial role in these studies. This target is a rare opportunity to study both gas and dust, their physical properties and dynamics, thus enabling an all-around comparison to state-of-the-art models.

# Acknowledgements

This work was partly supported by the Italian Ministero dell’Istruzione, Università e Ricerca through the grant Progetti Premiali 2012-iALMA (CUP C52I13000140001), by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) - Ref no. 325594231 FOR 2634/2 TE 1024/2-1, by the DFG Cluster of Excellence Origins (www.origins-cluster.de). This project has received funding from the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska- Curie grant agreement No 823823 (DUSTBUSTERS) and from the European Research Council (ERC) via the ERC Synergy Grant ECOGAL (grant 855130). Funded by the European Union (ERC, WANDA, 101039452). Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them. This work benefited from the Core2disk-III residential program of Institut Pascal at Université Paris-Saclay, with the support of the program “Investissements d’avenir” ANR-11-IDEX-0003-01. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01813.S, ADS/JAO.ALMA#2019.1.00951.S, ADS/JAO.ALMA#2022.1.00126.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We thank the entire ALMA team for their dedication to provide us with the data we used for this work. We thank Nicolas Cuello for helpful insights and discussion. We thank the referee for their insightful comments, which helped us to improve the quality of this work.

122 natexlab

(ref: akiyama2019) Akiyama, E., Vorobyov, E. I., Liu, H. B., et al. 2019, AJ, 157, 165

(ref: AlmaPartenership2015) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3

(ref: Alves2020) Alves, F. O., Cleeves, L. I., Girart, J. M., et al. 2020, ApJL, 904, L6

(ref: Andrews2013) Andrews, S. M., Rosenfeld, K. A., Kraus, A. L., & Wilner, D. J. 2013, ApJ, 771, 129

(ref: Ansdell2016) Ansdell, M., Williams, J. P., van der Marel, N., et al. 2016, ApJ, 828, 46

(ref: Ardila2007) Ardila, D. R., Golimowski, D. A., Krist, J. E., et al. 2007, ApJ, 665, 512

(ref: Aspin2003) Aspin, C. & Reipurth, B. 2003, AJ, 126, 2936

(ref: Bae2015) Bae, J., Hartmann, L., & Zhu, Z. 2015, ApJ, 805, 15

(ref: Ballering2019) Ballering, N. P. & Eisner, J. A. 2019, AJ, 157, 144

(ref: Barge1995) Barge, P. & Sommeria, J. 1995, A&A, 295, L1

(ref: Beccari2010) Beccari, G., Spezzi, L., De Marchi, G., et al. 2010, ApJ, 720, 1108

(ref: BeckwithSargent1991) Beckwith, S. V. W. & Sargent, A. I. 1991, ApJ, 381, 250

(ref: Birnstiel2018) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45

(ref: Bonnell1992) Bonnell, I. & Bastien, P. 1992, ApJL, 401, L31

(ref: Bryant2023) Bryant, E. M., Bayliss, D., & Van Eylen, V. 2023, MNRAS, 521, 3663

(ref: Cabedo2021) Cabedo, V., Maury, A., Girart, J. M., & Padovani, M. 2021, A&A, 653, A166

(ref: Cabrit2006) Cabrit, S., Pety, J., Pesenti, N., & Dougados, C. 2006, A&A, 452, 897

(ref: Cacciapuoti2023) Cacciapuoti, L., Macias, E., Maury, A. J., et al. 2023, arXiv e-prints, arXiv:2306.02852

(ref: Caratti2012) Caratti o Garatti, A., Garcia Lopez, R., Antoniucci, S., et al. 2012, A&A, 538, A64

(ref: Cuello2019) Cuello, N., Dipierro, G., Mentiplay, D., et al. 2019, MNRAS, 483, 4114

(ref: Cuello2023) Cuello, N., Ménard, F., & Price, D. J. 2023, European Physical Journal Plus, 138, 11

(ref: Dai2015) Dai, F., Facchini, S., Clarke, C. J., & Haworth, T. J. 2015, MNRAS, 449, 1996

(ref: DeMarchi2013a) De Marchi, G., Beccari, G., & Panagia, N. 2013a, ApJ, 775, 68

(ref: DeMarchi2013b) De Marchi, G., Panagia, N., Guarcello, M. G., & Bonito, R. 2013b, MNRAS, 435, 3058

(ref: Dong2022) Dong, R., Liu, H. B., Cuello, N., et al. 2022, Nature Astronomy, 6, 331

(ref: draine2006) Draine, B. T. 2006, ApJ, 636, 1114

(ref: Droz2015) Drozdovskaya, M. N., Walsh, C., Visser, R., Harsono, D., & van Dishoeck, E. F. 2015, MNRAS, 451, 3836

(ref: Dullemond2019) Dullemond, C. P., Küffmeier, M., Goicovic, F., et al. 2019, A&A, 628, A20

(ref: Fiorellino2021) Fiorellino, E., Manara, C. F., Nisini, B., et al. 2021, A&A, 650, A43

(ref: Flores2023) Flores, C., Ohashi, N., Tobin, J. J., et al. 2023, arXiv e-prints, arXiv:2310.14617

(ref: Flores-Rivera2021) Flores-Rivera, L., Terebey, S., Willacy, K., et al. 2021, ApJ, 908, 108

(ref: Gaia2022) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2022, arXiv e-prints, arXiv:2208.00211

(ref: Galametz2019) Galametz, M., Maury, A. J., Valdivia, V., et al. 2019, A&A, 632, A5

(ref: garufi2021) Garufi, A., Podio, L., Codella, C., et al. 2021, A&A, 645, A145

(ref: Garufi2022) Garufi, A., Podio, L., Codella, C., et al. 2022, A&A, 658, A104

(ref: Ginsburg2016) Ginsburg, A., Robitaille, T., & Beaumont, C. 2016, pvextractor: Position-Velocity Diagram Extractor, Astrophysics Source Code Library, record ascl:1608.010

(ref: Ginski2021) Ginski, C., Facchini, S., Huang, J., et al. 2021, ApJL, 908, L25

(ref: Grady1999) Grady, C. A., Woodgate, B., Bruhweiler, F. C., et al. 1999, ApJL, 523, L151

(ref: grant2021) Grant, S. L., Espaillat, C. C., Wendeborn, J., et al. 2021, ApJ, 913, 123

(ref: Gupta2023) Gupta, A., Miotello, A., Manara, C. F., et al. 2023, A&A, 670, L8

(ref: Gutermuth2011) Gutermuth, R. A., Pipher, J. L., Megeath, S. T., et al. 2011, ApJ, 739, 84

(ref: Haworth2021) Haworth, T. J. 2021, MNRAS, 503, 4172

(ref: Hennebelle2017) Hennebelle, P., Lesur, G., & Fromang, S. 2017, A&A, 599, A86

(ref: Hildebrand1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: hogbom74) Högbom, J. A. 1974, A&AS, 15, 417

(ref: Houge2023) Houge, A. & Krijt, S. 2023, Monthly Notices of the Royal Astronomical Society, 521, 5826

(ref: hsieh2023) Hsieh, C.-H., Arce, H. G., Li, Z.-Y., et al. 2023, ApJ, 947, 25

(ref: Hunter2023) Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023, arXiv e-prints, arXiv:2306.07420

(ref: Kenyon1988) Kenyon, S. J., Hartmann, L., & Hewett, R. 1988, ApJ, 325, 231

(ref: Kuffmeier2021) Kuffmeier, M., Dullemond, C. P., Reissl, S., & Goicovic, F. G. 2021, A&A, 656, A161

(ref: Kuffmeier2018) Kuffmeier, M., Frimann, S., Jensen, S. S., & Haugbølle, T. 2018, MNRAS, 475, 2642

(ref: Kuffmeier2020) Kuffmeier, M., Goicovic, F. G., & Dullemond, C. P. 2020, A&A, 633, A3

(ref: Kuffmeier2023) Kuffmeier, M., Jensen, S. S., & Haugbølle, T. 2023, European Physical Journal Plus, 138, 272

(ref: Kurtovic2018) Kurtovic, N. T., Pérez, L. M., Benisty, M., et al. 2018, ApJL, 869, L44

(ref: Kuznetsova2022) Kuznetsova, A., Bae, J., Hartmann, L., & Mac Low, M.-M. 2022, ApJ, 928, 92

(ref: Kwon09) Kwon, W., Looney, L. W., Mundy, L. G., Chiang, H.-F., & Kemball, A. J. 2009, ApJ, 696, 841

(ref: LeGouellec2019) Le Gouellec, V. J. M., Hull, C. L. H., Maury, A. J., et al. 2019, ApJ, 885, 106

(ref: LeGouellec2023) Le Gouellec, V. J. M., Maury, A. J., & Hull, C. L. H. 2023, A&A, 671, A167

(ref: Lebreuilly2021) Lebreuilly, U., Hennebelle, P., Colman, T., et al. 2021, ApJL, 917, L10

(ref: Lebreuilly2023a) Lebreuilly, U., Vallucci-Goy, V., Guillet, V., Lombart, M., & Marchand, P. 2023, MNRAS, 518, 3326

(ref: Liu2020) Liu, B., Lambrechts, M., Johansen, A., Pascucci, I., & Henning, T. 2020, A&A, 638, A88

(ref: Liu2019) Liu, H. B. 2019, ApJL, 877, L22

(ref: Macias2021) Macı́as, E., Guerra-Alvarado, O., Carrasco-González, C., et al. 2021, A&A, 648, A33

(ref: Manara2018) Manara, C. F., Morbidelli, A., & Guillot, T. 2018, A&A, 618, L3

(ref: Mathis1977) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425

(ref: Maury2018) Maury, A. J., Girart, J. M., Zhang, Q., et al. 2018, MNRAS, 477, 2760

(ref: Megeath2012) Megeath, S. T., Gutermuth, R., Muzerolle, J., et al. 2012, AJ, 144, 192

(ref: menard2020) Ménard, F., Cuello, N., Ginski, C., et al. 2020, A&A, 639, L1

(ref: Mendoza2009) Mendoza, S., Tejeda, E., & Nagel, E. 2009, MNRAS, 393, 579

(ref: Menten2007) Menten, K. M., Reid, M. J., Forbrich, J., & Brunthaler, A. 2007, A&A, 474, 515

(ref: Min2016) Min, M., Rab, C., Woitke, P., Dominik, C., & Ménard, F. 2016, A&A, 585, A13

(ref: Miotello2014) Miotello, A., Testi, L., Lodato, G., et al. 2014, A&A, 567, A32

(ref: MiyakeNakagawa1993) Miyake, K. & Nakagawa, Y. 1993, Icarus, 106, 20

(ref: Morales2019) Morales, J. C., Mustill, A. J., Ribas, I., et al. 2019, Science, 365, 1441

(ref: Motte2001) Motte, F. & André, P. 2001, A&A, 365, 440

(ref: Mulders2021) Mulders, G. D., Pascucci, I., Ciesla, F. J., & Fernandes, R. B. 2021, ApJ, 920, 66

(ref: Nakajima1995) Nakajima, T. & Golimowski, D. A. 1995, AJ, 109, 1181

(ref: Natta2007) Natta, A., Testi, L., Calvet, N., et al. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 767

(ref: offner2022) Offner, S. S. R., Moe, M., Kratter, K. M., et al. 2022, arXiv e-prints, arXiv:2203.10066

(ref: Ormel2009) Ormel, C. W., Paszun, D., Dominik, C., & Tielens, A. G. G. M. 2009, A&A, 502, 845

(ref: Owen2014) Owen, J. E. & Jacquet, E. 2014, Monthly Notices of the Royal Astronomical Society, 446, 3285

(ref: Padoan2014) Padoan, P., Haugbølle, T., & Nordlund, Å. 2014, ApJ, 797, 32

(ref: Padoan2005) Padoan, P., Kritsuk, A., Norman, M. L., & Nordlund, Å. 2005, ApJL, 622, L61

(ref: Park2021) Park, W., Lee, J.-E., Contreras Peña, C., et al. 2021, ApJ, 920, 132

(ref: Pascucci2016) Pascucci, I., Testi, L., Herczeg, G. J., et al. 2016, ApJ, 831, 125

(ref: Pfalzner2013) Pfalzner, S. 2013, A&A, 549, A82

(ref: Pfalzner2005) Pfalzner, S., Vogel, P., Scharwächter, J., & Olczak, C. 2005, A&A, 437, 967

(ref: Pineda2022) Pineda, J. E., Arzoumanian, D., André, P., et al. 2022, arXiv e-prints, arXiv:2205.03935

(ref: Pineda2020) Pineda, J. E., Segura-Cox, D., Caselli, P., et al. 2020, Nature Astronomy, 4, 1158

(ref: Pollack1994) Pollack, J. B., Hollenbach, D., Beckwith, S., et al. 1994, ApJ, 421, 615

(ref: Remijan2019) Remijan, A., Biggs, A., Cortes, P. A., et al. 2019, ALMA Technical Handbook,ALMA Doc. 7.3, ver. 1.1, 2019, ALMA Technical Handbook,ALMA Doc. 7.3, ver. 1.1ISBN 978-3-923524-66-2

(ref: Ribas2020) Ribas, Á., Espaillat, C. C., Macı́as, E., & Sarro, L. M. 2020, A&A, 642, A171

(ref: Ricci2010) Ricci, L., Testi, L., Natta, A., & Brooks, K. J. 2010, A&A, 521, A66

(ref: Rilinger2023) Rilinger, A. M., Espaillat, C. C., Xin, Z., et al. 2023, ApJ, 944, 66

(ref: Rodriguez2018) Rodriguez, J. E., Loomis, R., Cabrit, S., et al. 2018, ApJ, 859, 150

(ref: Sanchis2020) Sanchis, E., Testi, L., Natta, A., et al. 2020, A&A, 633, A114

(ref: Scholz2013) Scholz, A., Froebrich, D., & Wood, K. 2013, MNRAS, 430, 2910

(ref: Scicluna2014) Scicluna, P., Rosotti, G., Dale, J. E., & Testi, L. 2014, A&A, 566, L3

(ref: Segura-Cox2020) Segura-Cox, D. M., Schmiedeke, A., Pineda, J. E., et al. 2020, Nature, 586, 228

(ref: Smallwood2023) Smallwood, J. L., Yang, C.-C., Zhu, Z., et al. 2023, MNRAS, 521, 3500

(ref: Steinacker2015) Steinacker, J., Andersen, M., Thi, W. F., et al. 2015, A&A, 582, A70

(ref: Steinacker2014) Steinacker, J., Ormel, C. W., Andersen, M., & Bacmann, A. 2014, A&A, 564, A96

(ref: Steinacker2010) Steinacker, J., Pagani, L., Bacmann, A., & Guieu, S. 2010, A&A, 511, A9

(ref: Testi2014) Testi, L., Birnstiel, T., Ricci, L., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 339

(ref: Testi2016) Testi, L., Natta, A., Scholz, A., et al. 2016, A&A, 593, A111

(ref: Thies2011) Thies, I., Kroupa, P., Goodwin, S. P., Stamatellos, D., & Whitworth, A. P. 2011, MNRAS, 417, 1817

(ref: ThroopBally2008) Throop, H. B. & Bally, J. 2008, AJ, 135, 2380

(ref: Tobin2010) Tobin, J. J., Hartmann, L., Looney, L. W., & Chiang, H.-F. 2010, ApJ, 712, 1010

(ref: Tychoniec2020) Tychoniec, Ł., Manara, C. F., Rosotti, G. P., et al. 2020, A&A, 640, A19

(ref: Valdivia-Mena2022) Valdivia-Mena, M. T., Pineda, J. E., Segura-Cox, D. M., et al. 2022, A&A, 667, A12

(ref: Valdivia-Mena2023) Valdivia-Mena, M. T., Pineda, J. E., Segura-Cox, D. M., et al. 2023, A&A, 677, A92

(ref: vanTerwisga2023) van Terwisga, S. E. & Hacar, A. 2023, A&A, 673, L2

(ref: vanterwisga2022) van Terwisga, S. E., Hacar, A., van Dishoeck, E. F., Oonk, R., & Portegies Zwart, S. 2022, A&A, 661, A53

(ref: Weingartner2001) Weingartner, J. C. & Draine, B. T. 2001, ApJ, 548, 296

(ref: Wiebe2019) Wiebe, D. S., Molyarova, T. S., Akimkin, V. V., Vorobyov, E. I., & Semenov, D. A. 2019, MNRAS, 485, 1843

(ref: Williams2019) Williams, J. P., Cieza, L., Hales, A., et al. 2019, ApJL, 875, L9

(ref: Winter2018) Winter, A. J., Booth, R. A., & Clarke, C. J. 2018, MNRAS, 479, 5522

(ref: Winter2018b) Winter, A. J., Clarke, C. J., Rosotti, G., et al. 2018, Monthly Notices of the Royal Astronomical Society, 478, 2700

(ref: Xin2023) Xin, Z., Espaillat, C. C., Rilinger, A. M., Ribas, Á., & Macı́as, E. 2023, ApJ, 942, 4

(ref: Yen2019) Yen, H.-W., Gu, P.-G., Hirano, N., et al. 2019, ApJ, 880, 69

(ref: Yen2014) Yen, H.-W., Takakuwa, S., Ohashi, N., et al. 2014, ApJ, 793, 1

(ref: Zhu2019) Zhu, Z., Zhang, S., Jiang, Y.-F., et al. 2019, ApJL, 877, L18

# Datasets

We report a summary of the datasets utilized in this work in Table [\[table:1\]](#table:1).

| Project Code | P.I. | Date | Integration (s) | Resolution (arcsec) | Frequency (GHz) | CASA version |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  |  |
|  |  |  | Band 3 |  |  |  |
| 2022.1.00126.S | Wendeborn, J. | 2023/01/16 | 7529 | 1.05 | 89-105 | 6.4.1-12 |
|  |  |  |  |  |  |  |
|  |  |  | Band 6 |  |  |  |
| 2019.1.01813.S | van Terwisga, S. | 2019/11/27 | 32 | 1.13 | 223-243 | 5.6.1-8 |
| 2019.1.00951.S | Grant, S, | 2019/12/12 | 72 | 1.15 | 216-233 | 5.6.1-8 |

# Compact emission modelling

In order to measure $\alpha$ and $\beta$ along the streamer free of flux contamination from the inner optically thick region, we have subtracted the compact contribution centered on the source, in two ways.

First, we fitted a gaussian model to the central region in the image plane. Figures [5](#fig:gauss_fit3) and [6](#fig:gauss_fit6) show the data, the model, and the residuals of the fit. Table [\[tab:gaussfit\]](#tab:gaussfit) summarizes the fitted parameters for the models in the two bands. The spectral index $\alpha$ and dust opacity spectral index $\beta$ have been measured once the optically thick region has been modelled out (Sect. [4](#sec:spectral_index)). As a robustness check, we have tested whether our results are robust against a different modelling scheme. We have used the *uvmodelfit* CASA routine to fit a point source component to the visibilities, since the disc is unresolved at the resolution of our observations. The function fits for an offset from the phase center and the flux of the point source. We find the same offset from center as for the gaussian fit and a total integrated flux density of 16.1 mJy in B6 and 2.6 mJy in B3. We then subtracted this contribution from the visibility amplitudes (A = $\sqrt{Re^2 + Im^2}$) at all scales, and binned them. In each bin, the uncertainty is given by the combined uncertainties on the real and imaginary parts of the visibilities, together with the ALMA calibration error (1$\sigma$ = 5%, (cite: Remijan2019)). We finally computed the spectral and dust opacity indices using Eq. [\[eq:alpha\]](#eq:alpha) and [\[eq:beta\]](#eq:beta) as a function of uv-distance after the subtraction, as shown in Fig. [7](#fig:betauv). A bump at the short uv-distances is caused by the combination of the asymmetric shape of the streamer with the uv-coverage of the observations. The large scatter in amplitude at these scales also results in a larger error around the mean and thus on a larger uncertainty on $\alpha$ and $\beta$. The very first bin (at the shortest common uv-distance) shows $\beta \sim 2$, because of a raise in the B6 visibility amplitudes that is not observed in B3 due to uv-coverage. Shorter baselines, and thus larger recoverable scales observations, are needed to more robustly measure $\beta$ in the outskirts of the streamer. The higher $\beta$ would still be in agreement with the conclusion of small, ISM-like grains. Finally, both azimuthally averaged spectral indices are consistent with what found in the image plane: $\alpha_S = 3.1 \pm 0.1$, and $\beta = 1.55 \pm 0.05$.

| Band | Shift from source coordinates (arcsec) | Integrated flux density (mJy) | $\sigma_x$ x $\sigma_y$ (arcsec) |
|:--:|:--:|:--:|:--:|
|  |  |  |  |
| 3 | (0.060 $\pm$ 0.003, 0.080 $\pm$ 0.003) | 2.8 $\pm$ 0.1 | (0.696 $\pm$ 0.002) x (0.691 $\pm$ 0.002) |
| 6 | (0.020 $\pm$ 0.008, 0.020 $\pm$ 0.008) | 19.4 $\pm$ 0.2 | (0.740 $\pm$ 0.008) x (0.723 $\pm$ 0.007) |

![](gauss_b3.png)

![](gauss_b6.png)

![](beta_from_uvplane.png)

# Any flyby candidates?

We here note the presence of a class II YSO ($\alpha_{2-25\mu m} = -1$; (cite: Megeath2012)) at projected distance of 100$\ensuremath{''}$ (41,000 au) from M512. This source, 2MASS J05401156-0730409, was studied in continuum by (cite: vanterwisga2022), who reported a integrated 1.3mm flux of 1.65 $\pm$ 0.06 mJy and a dust mass estimate of 8.1 $\pm$ 0.3 M$_{\oplus}$, assuming optically thin emission, a dust temperature of 20 K, and a dust absorption opacity of 2.3 cm$^2$/g. Gaia DR3 (cite: Gaia2022) reported a parallax of 2.54 $\pm$ 0.18 for the latter, indicating it is at a distance consistent (however different) with M512, whose Gaia DR3 parallax is 2.37 $\pm$ 0.12. The secondary object has a measured Gaia DR3 proper motion in declination of pmDec $= -$0.18 $\pm$ 0.15 mas/yr and a proper motion in right ascension of pmRA $=$ 0.14 $\pm$ 0.16 mas/yr. M512 moves in the sky with pmDec $= -$0.50 $\pm$ 0.10 mas/yr and pmRA $=$ 0.15 $\pm$ 0.11. Considering that the sources have $-$0.32 $\pm$ 0.18 mas/yr relative motion in declination and $\delta$pmRA = 0.01 $\pm$ 0.19 in right ascension.

The relative proper motions are consistent with a close encounter the two objects between 200 and 700 kyr ago (1$\sigma$ range), on the plane of the sky. However, considering the error bars on the Gaia proper motion and parallax measurements, it’s possible that no flyby occurred at all. We report the 2MASS sky map in Figure [8](#fig:flyby).

Both spatial and time scales yield major counter arguments to this scenario. For a disc of size R$_{disc}$ perturbed by a star during a close encounter R$_{flyby}$ $\sim$ R$_{disc}$, simulations suggest that induced arc-like spirals would have a spatial extent of the order of three times R$_{disc}$ at most (see (cite: Cuello2019)). The streamer around M512, however, is 4,000 au or longer (depending on projection effects and interferometric filtering), and would require an unreasonably extended protoplanetary disk that we would have resolved with our observations. Additionally, even in the earliest case compatible with Gaia constraints, a close encounter could have occurred between 200-700kyr ago, within 1sigma confidence. The typical free fall timescale t$_{ff} \propto \sqrt{r^3/Gm}$ for a particle infalling from 4,000 au onto a 0.15 M$_{\odot}$ star is roughly 50 kyr, thus the material should have already fallen onto the star. If the observed streamer were a flyby-induced spiral, its survival time would be at most a few times the orbital period at the outer edge of the disc (cite: Smallwood2023), thus it would have been dispersed in a few kyr, making its observation very improbable. Lastly, the derived masses for the streamer around M512 and its inner region suggests that a flyby should have stripped away a significant portion of the disk (see Sect. [5.2](#discuss:mass)). (cite: Pfalzner2005) demonstrated how even encounters with a similar mass object and with a periastron of the order of the disk radius would only strip up to about 50% of the perturbed disk’s mass[^4]. Finally, we inspected ALMA archival data for this nearby source (ID 2019.1.01813.S) and found no evidence for extended emission.

As a cautionary argument, however, we note that flybys for which the stripped material has been observed in a structure exceeding 3 times R$_{disc}$ (RW Aur), and for which re-circularization timescales seem to exceed a few kyrs (HV Tau and DO Tau) have been observed in (cite: Rodriguez2018) and (cite: Winter2018), respectively. Overall, we suggest that a flyby of M512 with 2MASS J05401156-0730409 appears harder to reconcile with the observed extended and massive arc than the streamer scenario, but cannot be completely ruled out at this stage.

![](flyby.001.jpeg)

[^1]: However, M512 lays in a region where the UV irradiation field is too low to induce such an effect (cite: vanTerwisga2023).

[^2]: The typical duration interval between subsequent outbursts for FUOr events (cite: Scholz2013).

[^3]: This value is obtained when considering the opacities for ISM-like grains of (cite: Birnstiel2018), thus $\kappa_{1.3mm} = 0.4$ g/cm$^{-2}$, and the temperature profile give in Eq.[\[eq:temp\]](#eq:temp).

[^4]: Although this argument relies on the systematically uncertin dust mass constraints.

</paper>

Write the methods card for this paper.