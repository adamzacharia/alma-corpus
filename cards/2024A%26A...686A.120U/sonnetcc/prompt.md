# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...686A.120U\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...686A.120U",
 "title": "Vertical and radial distribution of atomic carbon in HD 163296",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Urbina, F.",
 "n_authors": 4,
 "arxiv_id": "2403.05042",
 "doi": "10.1051/0004-6361/202348523",
 "alma_projects_linked_by_archive": [
  "2011.0.00531.S",
  "2013.1.00226.S",
  "2013.1.00366.S",
  "2013.1.00498.S",
  "2013.1.00527.S",
  "2013.1.00601.S",
  "2013.1.00694.S",
  "2013.1.00798.S",
  "2015.1.00486.S",
  "2015.1.00964.S",
  "2016.1.00484.L"
 ]
}
```

Paper text:
<paper>
# Vertical and radial distribution of atomic carbon in HD 163296

In protoplanetary disks, atomic carbon is expected to originate from the PDR at the disk surface where CO is dissociated by UV photons coming from the stellar, or external interstellar, radiation field. Even though atomic carbon has been detected in several protoplanetary disks, there is a lack of spatially resolved observations of it.

For HD 163296 protoplanetary disk, we aim to obtain both radial and vertical structure of \[CI\]$={^3}{P_1} - {^3}{P_0}$ line emission and perform the first direct comparison of this tracer with optically thick line emission $^{12}$CO $J=2-1$.

We used archival ALMA data for \[CI\]$={^3}{P_1} - {^3}{P_0}$ and previously published ${^{12}}$ CO $J=2-1$ data in HD 163296. Through the software of disksurf we extracted the vertical structure, meanwhile radial profiles were obtained directly from imaging. Brand new DALI modelling was employed to perform direct comparison to the data.

We found that these tracers are collocated radially but not vertically, where $^{12}$CO $J=2-1$ emission is, on average, located at higher altitudes, as it is also the case for other tracers in the same disk.

Due to this difference in vertical height of the emission, the optically thick $^{12}$CO $J=2-1$ emission line appears to trace the highest altitudes, despite the expected formation mechanism of \[CI\] in the disk. The latter phenomena may be due to efficient mixing of the upper layers of the disk, or UV photons penetrating deeper than we expected.

# Introduction

Our knowledge about protoplanetary disks compositions and structure has been greatly expanded by high resolution observations of the Atacama Large Millimeter and sub-millimeter Array (ALMA). For example, the DSHARP project (cite: DSHARP), unveiled disks’ dust substructures using high resolution observations. Meanwhile the MAPS large program investigated the gas in protoplanetary disks in order to study their chemical structure (cite: MAPS). As well as investigating the radial structure of disks, we now have the instrumental capability to enable studies of the vertical structure, for which different approaches have been taken. For dust, observing nearly edge-on systems (cite: villenave2020observations) or analyzing scattered light observations (see (cite: avenhaus2018disks) for an example) are both methods for assessing the vertical structure of disks. Meanwhile, for the gas, given sufficient spectral and spatial resolution, it is possible to infer the vertical structure from the displacement of the emission relative to the perfectly flat disk case (cite: 2021A&A...650A.179I). One way is to fit velocity curves, as done with ConeRot (cite: casassus2019kinematic), which places the emission in a conical surface and makes use of it to define average velocity curves which are then use to fit the geometry of such conical surface, enabling vertical structure detection. A method that is non-model dependent and well suited for mid-inclination disks was first presented in (cite: pintemethod). In a similar fashion as in ConeRot, this method uses a geometrical approach by placing the channel maps emission in a conical surface ,where the position of the emission is estimated by the local maximum of it, and has been successfully applied to constrain, for example, carbon monoxide vertical structure in several systems (cite: law2022co).

Atomic carbon, \[CI\], is a useful tracer for studying the carbon content in protoplanetary disks. Typical models for \[CI\] in circumstellar disks consider it as a product of the photo dissociation of carbon monoxide by UV photons, therefore, it is expected for atomic carbon to trace the upper layers of the disk, where the ionizing radiation is abundant (cite: kama2016observations). As a consequence, \[CI\] should act as a reliable tracer for the vertical height in protoplanetary disks. Some observations towards debris disks suggest \[CI\] has an important shielding effect on CO protecting it from UV photons and forming a layer close to it in the photo dissociation region (PDR), sharing a similar phenomenology as the interstellar medium (cite: van1988photodissociation). In spatially resolved observations of debris disks, \[CI\] appears to be co-located radially though not vertically (cite: higuchi2019first; kral2019imaging).

|  | **\[CI\] channel maps** | **\[CI\] zeroth moment map** | **Continuum** |
|:--:|:--:|:--:|:--:|
| Noise RMS (Jy Beam$^{-1}$) | 2.16$\times 10^{-2}$ | 2.63 $\times 10^{-2}$ (km/s) | $6.62 \times 10^{-4}$ |
| Peak SNR | 14.26 | 17.81 | 1324.93 |
| Integrated flux | \- | 7.24 $\pm$ $0.02$ (Jy km/s) | 3.51 $\pm$ $0.04 \times 10^{-2}$ (Jy) |

\[CI\] has been detected towards protoplanetary disks in emission using single dish observations by APEX (cite: kama2016observations). There, 6 out 12 disks showed \[CI\]$={^3}{P_1} - {^3}{P_0}$ line emission detection, meanwhile the \[CI\]$={^3}P_2 - {^3}P_1$ line turned out to be fainter as only 1 system out the 33 surveyed were detected at that frequency. For systems like TW Hya and HD 100546 it was suggested that carbon is under-abundant (cite: bruderer2012warm; du2015volatile; kama2016volatile), due to processes like freeze-out of molecules in the mid plane of the formation of complex organic molecules in cold regions. Nevertheless these unresolved observations were not able to precisely constrain the gas-phase \[C\]/\[H\] ratio due to lack of sensitivity. To test the vertical structure, spatially resolved observations for \[CI\]$={^3}{P_1} - {^3}{P_0}$ are needed but there is still a lack of them. To the authors knowledge, there are only two published examples of spatially resolved imaging of \[CI\] towards a Class II protoplanetary disks. In (cite: Imlup_recent), IM Lup \[CI\] emission was examined, finding this emission is tracing the upper layers of the disk, even at higher altitudes relative to CO. Meanwhile in (cite: https://doi.org/10.48550/arxiv.2211.16531) a kinematic bipolar structure was detected in the \[CI\] emission of HD 163296, possibly associated with a planet candidate, but no further analysis to the radial and vertical structure of the emission was done.

HD 163296 protoplanetary disk has been exhaustively studied, it has a rich dust structure showing gaps, rings and a crescent (cite: isella2018disk). Its vertical structure has been studied for several tracers such as CO and its isotopologues and other molecules (cite: Tere). To date, the most prominent vertical structure found is detected for $^{12}$CO $J=2-1$ line emission, even when compared to its isotopologues and other different tracers, which is explained by the fact emission lines from molecules such as HCN, CN or isotopologues of CO are optically thin.

In this work, we aim to test our current knowledge about the expected location of atomic carbon within protoplanetary disks by directly comparing the radial and vertical location of \[CI\] and CO in HD 163296. The paper is organized as follows. In Section [2](#sec:observations), we describe the procedure for reduction and imaging of the archival ALMA data used in this work. The analysis tools and results are presented in Section [3](#sec:results). In Section [4](#sec:disucussions) we compare the observed structure as indicated by \[CI\] and CO emission to modelling. Finally, section [5](#sec:summary) summarizes the important analyzes and discussions from this work.

# Observations and data reduction

We used archival ALMA band 8 observations of HD163296 from the project 2013.1.00527.S (PI: M. Kama). These observations were obtained in a single pointing on May 2, 2015, affected by an average precipitable water vapor of 0.536 mm. A configuration of 37 antennas of 12 m where the projected baselines 5th and 80th percentile are 9.92 m and 127.36 m respectively was used, which resulted in a synthesizing beam for the continuum images of 0.675$\times$0.296" when constructing images with natural weighting. This weighting was chosen to compensate for the low sensitivity of the observations as the emission is expected to be faint and the total integration time on source was only 13.1 minutes. Dust continuum was observed in 2 spectral windows, each one with a bandwidth of 2 GHz, 128 channels and central frequencies of 480.24 and 482.05 GHz respectively. \[CI\] $={^3}P_1 - {^3}P_0$ line emission was observed in a single spectral window of 3840 channels of spacing 488.28 KHz, with a central frequency of 492.22 GHz. Calibration sources were the quasars J1256-0547 (bandpass) and J1733-1304 (phase) and Titan (flux).

![](figures/line_emission.png)

![](figures/continuum.png)

![](figures/pv_self_cal_CI.png)

![](figures/CO_pv_diagram.png)

All data sets were calibrated and flagged using *Common Astronomy Software Applications* (CASA) (cite: 2007ASPC..376..127M) using the pipeline script delivered with the data. Self calibration was carried out reaching a final solution interval of 30s for phase calibration. Amplitude self calibration was also applied, with the solutions applied to line imaging which increased the final SNR by 20% compared to non-selfcalibrated products. Line imaging of \[CI\] was achieved after subtracting the continuum and averaging the spectral windows to a width of 0.3 km/s. The synthesised beam of the CI cube is $0.78" \times 0.49"$ with a PA of 74.46°.

The data we present here is complemented by observations of $^{12}$CO $J=2-1$ towards HD 163296, which where directly obtained from the publically available DSHARP data release (cite: DSHARP; isella2018disk).

# Analysis and results

## Imaging

In Fig. [\[fig:channels\]](#fig:channels) atomic carbon line emission channel maps are shown following the typical wing shape for gas rotating in a Keplerian fashion. Fig [1](#fig:zeroth) presents the results of using the software **bettermoments** (cite: bettermoments) for obtaining the zeroth moment map of the emission by integrating from 1.3 to 10.6 km/s and masking all pixels with values lower than $2\sigma$. In the moment 0 map more emission is observed towards the NE side of the disk as highlighted by the $15\sigma$ contours in the image. Fig. [2](#fig:continuum) shows dust continuum imaging achieved by combining both dedicated spectral windows, with an achieved synthesized beam FWHM dimensions of $0.67" \times 0.40"$ and a PA of 76.60°. Table [\[tab:table measurements\]](#tab:table measurements) summarizes the noise levels and integrated fluxes.

The asymmetry in the zeroth moment map is also shown in Fig. [\[fig:channels\]](#fig:channels) where the northern side is brighter at channels around 5.5 km/s where we highlight region A showing an asymmetric peak. The NE of the disk is thought to be the near side of the disk as scattered light imaging indicates (cite: 2019ApJ...875...38R). To further investigate, spectra from the near and far side of the disk are extracted. This is achieved by dividing each channel along the major axis of the disk. Only emission above 3$\sigma$ is used and Keplerian masking is applied by using the (cite: rich_teague_2020_4321137) implementation. The extracted spectra can be seen in Fig. [4](#fig:assymetry) where an overall flux excess is observed from 5.2 to 7.3 km/s. The maximum excess comes from the channel at 5.5 km/s that can be due to the previously mentioned region A.

![](figures/assymetry.png)

An apparent flux surplus coming from the far side of the disk is also measured towards the channels at velocities of 4.0 and 7.6 km/s. At those channels, the emissions wings are no longer spatially separated, and so distinguishing the near and far side in images becomes more difficult for the achieved angular resolution. Close to the major axis, the area of one synthesized beam can easily include emission from both the near and far side (and potentially the upper and lower side, see (cite: rosenfeld2013spatially)). We defer interpretation of the asymmetry in these specific channels until in depth modelling of CI emission processes applied to HD 163296 can be achieved. A well defined vertical height will be crucial for enabling these efforts.

## Radial analysis

Figure [3](#fig: PV diagrams) show Position-Velocity (PV) diagrams for both CO and \[CI\] emissions in HD 163296 obtained along the major axis of the disk. For gas following Keplerian motion, a symmetric diagram around the origin is expected, as it is the case for the CO emission. The PV diagram of \[CI\] shows a minor asymmetry in the emission along the major axis, in which channels at velocities of 7.6-7.9 km/s are brighter than their symmetric counterparts at 3.7-4.0 km/s as can be seen in Fig. ([\[fig:channels\]](#fig:channels)), notice this is not the same asymmetry from the near-far side of the disk previously discussed and it is not related to the region A, as the latter does not belong to the major axis of the disk.

The inner and outer radii can be constrained by assuming Keplerian rotation of the gas (see (cite: matra2017exocometary) for an example). The maximum radial velocity measured along the line of sight is

$$\begin{equation}
    v_{max} = \sqrt{\frac{GM_{*}}{x}} \sin(i)
    \label{max vel},
\end{equation}$$ where $x$ is the distance measured along the major axis of the disk, $i$ is the inclination of the disk, $M_*$ is the mass of the star and $G$ is the gravitational constant. Also, the radial velocity is

$$\begin{equation}
    v_{rad} = \sqrt{\frac{GM_{*}}{R^3}} \sin(i)x,
    \label{radial vel}
\end{equation}$$ where $R$ is the radial distance from the star to the gas. With this method we find an inner radius of 40 au for both tracers and an outer radius of 600 au and 500 au for CO and \[CI\] respectively. The outer radius for CO is in good agreement with the value of 560 au reported in (cite: isella2018disk). Notice the inner and outer radii for \[CI\] should be taken as an upper and lower limits for the actual values respectively, as these measurements are affected by the low sensitivity of the observations its effects cannot be ruled out with the current available data.

For comparing the radial extent of dust, atomic carbon and carbon monoxide, an azimuthal average profile is obtained for dust and line emissions moment 0 maps, as shown in Fig. [5](#fig:radial avg). A radial cutoff ($R_{90}$) is defined as the radius where 90% of the total integrated profile value is reached. $R_{90}$ is measured for all three datasets studied. By sampling the radial profiles at each radius, several profiles are obtained for which the calculation is repeated. Their respective 68% confidence interval is estimated. For \[CI\] and CO it is found $R_{90C} = 309.6^{+6.1}_{-12.1}$au and $R_{90CO} = 323.0^{+3.9}_{-2.7}$ au and for dust continuum $R_{90 dust}= 115.14^{+6.1}_{-0.0}$ au. Therefore we obtain a ratio of $R_{90C}/R_{90dust} = 2.63^{+0.11}_{-0.13}$ and $R_{90CO}/R_{90dust} = 2.78^{+0.03}_{-0.05}$, suggesting dust drift, as expected for this system.

![](figures/radial_avg.png)

![](figures/average_surface_fixed.png)

![](figures/gauss_sampling_profiles.png)

## Vertical analysis

As \[CI\] observations are spatially resolved, we attempt to extract properties of the vertical structure by using **disksurf** (cite: disksurf) implementation of the method first presented in (cite: pintemethod). We use **disksurf** iterative approach that for each run updates a mask to better constrain the emission and better identify the peaks, in particular we used 5 and 10 iterations for obtaining CO and \[CI\] surface emission respectively. Because of the low resolution of the \[CI\] observations the bottom side of the disk is not resolved, therefore this method in only applied to the upper surface of the disk. The same is done for carbon monoxide, in a similar fashion as in (cite: Tere).

Figure [6](#fig: surface heigth) left shows the obtained surface height for both \[CI\] and CO. \[CI\] has a ratio $z/r \sim 0.2$ up to 300 au, for greater radii it shows a drastic fall. CO is located in the interval $z/r$ from 0.2 to 0.3, showing carbon monoxide tracing, on average, a higher layer of the surface, which seems to contradict our assumption that \[CI\] should be found close to the PDR at the surface of the disk. CO surface height shows a double peaked shape, also recovered by (cite: Tere). The local minimum in the height of the CO emission is located at the same radial position with the maximum in the \[CI\] emission.

Given this method is depends on the spatial resolution (see section [4.2](#sec:angular res)), we repeated the vertical analysis in images produced using Brights weighting instead of natural. We were not able to recover the emission surface for values of robust parameter lower than 1 due to the low S/N. All profiles obtained with robust greater than 1 agreed with Fig. [6](#fig: surface heigth).

# Discussions

Figure [4](#fig:assymetry) shows an excess flux coming from the velocity channels from 5.2 to 7.3 km/s, also observed in the emission enclosed by the 15$\sigma$ contours in the zeroth moment map shown in Fig. [1](#fig:zeroth), that extends up to approximately 100 au from the central star.

In (cite: https://doi.org/10.48550/arxiv.2211.16531) a 2 km/s red-shifted component was first detected in \[CI\] observations at a location of 0.5" to the SW of the central star and was proposed to be due to inflow of gas into the midplane. We were not able to measure the same asymmetry in the line even though an excess towards the high velocity channels was shown in Fig. [4](#fig:assymetry), but we note that in (cite: https://doi.org/10.48550/arxiv.2211.16531) they also included data from an additional, shorter integration observations as part of project 2015.1.01137.S (PI: T. Tsukagoshi).

As modelled in (cite: kama2016observations), atomic carbon is expected to be located in the upper layers of the disk, tracing the PDR. We expect carbon monoxide and atomic carbon to be collocated radially, though not necessarily vertically, where atomic carbon may be tracing higher layers in the PDR.

Results shown in Fig. [3](#fig: PV diagrams) suggest a radial co-location of \[CI\] and CO from 40 au to 500 au. CO is extended up to 600 au. The difference of 100 au may be explained by a lack of sensitivity to the weak \[CI\] emission in the outer disk in comparison to the deep CO observations. Notice equation ([\[radial vel\]](#radial vel)) assumes a flat circular disk in Keplerian rotation, which is a good approximation at low ($r< 50$ au )and high radii ($r >$ 400 au) as shown in Fig. [6](#fig: surface heigth), making the method valid for the purposes of constraining gas radial extent.

Regarding the surfaces shown in Fig. [6](#fig: surface heigth) left, we fitted both surface emissions by using exponentially tapered power law function defined by

$$\begin{equation}
    z(r) = z_0\left(\frac{r}{r_0}\right)^{\psi} \times \exp\left(-\left[\frac{r}{r_{t}}\right]^{q_t}\right),
\label{eq: exponentially tapered}
\end{equation}$$

where $r_0$ is just a constant fixed for units to match. For CO, given its double peaked shape, we followed a similar approach as in (cite: law2021molecules), but we considered a baseline model given by eq. [\[eq: exponentially tapered\]](#eq: exponentially tapered) and employed a Gaussian function for modelling the local minimum at $\sim 270$ au, therefore, for CO the parameter space consists on a total of 7 parameters, 4 from the baseline model and 3 more for the Gaussian feature to model the local minimum. By using **emcee** package (cite: 2013PASP..125..306F), Markov chain Monte Carlo sampling is performed to explore the distribution of parameters whose posterior distributions are shown in Figs. [\[fig:MCMC CO\]](#fig:MCMC CO) and [10](#fig:MCMC CI).

Figure [6](#fig: surface heigth) right shows the best fitted models. In Fig. [11](#fig: residuals and data points) we show results of this fit, relative to the data points, and residuals of the model. The residuals range for \[CI\] goes from -40 to 40 au, which is within the ranges of the synthesized beam major axis. Both the modelling and the data shown in Fig. [6](#fig: surface heigth) suggest atomic carbon to be, on average, located at lower altitudes compared to CO optically thick emission line with ratio $z/r$ similar as other optically thin tracers like CN or HCN (see (cite: Tere) Fig. 2), with the first also matching \[CI\] maximum height at the same radius. This is consistent with CN being also an external UV exposed regions tracer (see (cite: bergner2021molecules) for a recent work about it). Notice HD 163296 is a Hearbig Ae star, system for which its disk \[CI\] line emission was predicted to be optically thin (see (cite: kama2016observations) for general analysis in Hearbig Ae/Be systems), which may be able to explain the difference.

Now, we set to explore this unexpected result by comparing it with physical-chemical models and proposing 3 different effects that can contribute to the apparent non-vertical co-location of CO and \[CI\] emissions.

![](figures/hd163296_co_sim.png)

![](figures/hd163296_ci_sim.png)

## DALI modelling of \[CI\] and CO in HD 163296

To compare our current understanding about the formation of \[CI\] and its relation to CO in HD 163296, we make use of the **DALI** physical-chemical modelling code (cite: bruderer2012warm; 2013A&A...559A..46B) to obtain CO and \[CI\] abundance vertical profiles as well as their expected emission layers. Starting with a parameterized gas and dust density distribution and an input stellar spectrum, the code utilizes Monte Carlo radiative transfer to calculate the UV radiation field and dust temperature. This establishes an initial guess for the gas temperature, which serves as the starting point for an iterative process to solve gas-grain chemistry (time-dependently or in equilibrium). Spectral image cubes, line profiles, and disk-integrated line fluxes are then be obtained using the ray-tracing module. In appendix [9](#appendix: dali vs disksurf), we show how the image cubes emission surface , extracted with **disksurf**, compares to the **DALI** emission contours to test how well this method is able the extract the vertical structure of the gas.

The model is fit following the procedure outlined in (cite: kama2016volatile) and (cite: keyte_2023), see those works for a full description of the fitting process. In short, the physical structure and total dust mass is first determined by fitting the continuum spectral energy distribution using a large grid of models. The parameters $R_\text{gap}$, $\psi$, $h_\text{c}$, $\delta_\text{dust}$, and $\Delta_\text{g/d}$ are varied, while $\Sigma_\text{c}$ is kept fixed at an arbitrary value such that changes in $\Delta_\text{g/d}$ are equivalent to changes only in the total dust mass. Having determined $M_\text{dust}$, we adopt a gas-to-dust ratio of $\Delta_\text{g/d}=100$, and fix $\Sigma_\text{c}$ such that the best-fit dust mass is maintained. The total elemental carbon and oxygen abundances are then constrained by fitting the spatially unresolved CO rotational ladder and resolved CO 3-2 observations. Final molecular abundances are obtained using a chemical network based on subset of the UMIST 06 network (cite: woodall_umist), which consists of 118 species and 1675 individual reactions. We run the chemistry time-dependently to a chemical age of 1 Myr, which is typical of such systems. A summary of the derived parameters is reported in Table [1](#table:modelparameters).

From the image cubes we were not able to reproduce the asymmetry in the emission that enhanced the near side of the disk, therefore, we can exclude radiative transfer effects creating the profile showed in Fig. [4](#fig:assymetry). Notice this phenomena can’t be explained by geometry as we have projected the emission with the same inclination and PA as the data.

Figure [7](#fig: abundance maps) shows the results for the modelling in HD 163296. There CO emission seems to follow the curve of $\tau=1$ as expected. For \[CI\] we overlaid the curve of $\tau =0.1$ as higher optical depths are obtained only at the midplane and therefore its line emission is optically thin as previous modelling of Herbig Ae/Be systems suggested (cite: kama2016observations).

Figure [8](#fig: DALI comparison) shows the comparison of the 75% emission contour with our derived surface emission for CO and \[CI\]. The DALI model agrees with derived \[CI\] surface emission but for CO it strongly disagrees as the predicted emission surface is located at much lower heights from radii higher than 100 au.

We would like to stress that the **DALI** model reflects our current understanding about the PDR in protoplanetary disks as it predicts \[CI\] being in higher altitudes compared to CO where we expected UV radiation is the most efficient in protoplanetary disks.

![](figures/dali_comparison.png)

![](figures/convolved_v2.png)

![](figures/vertical_height_withdust.png)

## Angular resolution effects

The method employed in the present work for deriving vertical height depends on the correct location of local maxima from each channel. When the angular resolution is not enough to resolver both the upper and lower part of the disk, mixing of both emissions would be the observed. This effect could shift the local maximum towards the major axis of the disk which will result in a lower height measurement (see (cite: rosenfeld2013spatially) Fig. 4 for visualization of this effect).

To test whether angular resolution can explain the observed discrepancy, the CO data is convolved with a 2D elliptical Gaussian with the same PA, minor and major axis as the synthesized beam of the \[CI\] observations in an attempt of mimicking the low angular resolution of the latter. Then, the vertical analysis is repeated and results are shown in Fig. [\[fig: surface heigth appendix\]](#fig: surface heigth appendix) left.

From the convolved data we were not able to detect any point at radii minor than 100 au, which is also seen in the \[CI\] profile, indicating that it is not possible to resolve inner structure as expected from a low angular resolution case. The vertical profile of CO decreases on average a 10% to 15% diminishing the difference between CO and \[CI\]. We employed a Welch’s t-test to examine the null hypothesis that the convolved CO and \[CI\] data have the same average height within the 100 to 300 au range. The analysis yielded a p-value lower than $10^{-10}$ and therefore rejecting the hypothesis with a certainty higher than $6\sigma$, suggesting that resolution effects alone may not be sufficient to explain this difference.

## $\mu$m dust grains vertical non co-location with CO

In gas and dust rich environments such as protoplanetary disks, the shielding from high energy photons is usually provided by $\mu$m dust grains (cite: henning2013chemistry). If dust grains and CO are vertically co-located, we expect the PDR to be a thin structure tracing the surface of the disk. In this case we also expect \[CI\] to trace the same surface as the optically thick CO line. This lead us to hypothesize that the discrepancy observed may be due to $\mu$m dust grains being vertically non co-located with gaseous CO. This non co-location would produce a wedge like PDR region and the optically thin \[CI\] line would trace the transition from the shielded to non-shielded part of the disk. Notice that in this UV-exposed region we still need a high abundance of CO such that the $J=2-1$ line remains optically thick or a high enough accumulation of \[CI\] such that CO gets shielded by the latter.

A recent work from (cite: rich2021investigating) tried to constrain the vertical profile small dust grains in 3 different protoplanetary disks, HD 163296, IM Lup and CU Cha, finding that for the first two, small grains were located below the CO gas height, which may be produced by a large gas-to-dust ratio that lowers the scattering surface heights. For comparison purposes, in Fig. [\[fig: surface heigth appendix\]](#fig: surface heigth appendix) right, we added to our height profiles the power law fitting of dust grains as well as the data points from the same study. Even though the vertical profile for the dust grains in HD 163296 is constrained by only two data points, it matches the \[CI\] profile providing direct observational evidence in favor of our hypothesized PDR wedge like structure.

Furthermore, under the assumption the PDR vertical structure depends primarily on $\mu$m dust grains position, systems like IM Lup and CU Cha offer a unique opportunity to test its diversity by using future high angular resolution \[CI\] observations. For CU Cha, as both CO and dust grains profiles show a good agreements, we expect a the \[CI\] and CO to also agree in their vertical profile. From (cite: rich2021investigating) work, IM Lup vertical profiles show an even more drastic difference between CO and small dust grains compared to HD 163296, therefore if the main mechanism for UV shielding in IM Lup came from $\mu m$ dust grains, we would have expected this system to show a similar vertical location of \[CI\] emission relative to CO as the one observed in this work for HD 163296, but in (cite: Imlup_recent) it was observed exactly the opposite phenomena in which \[CI\] appears to trace upper layers with $z/r \geq 0.5$, higher than for CO with $z/r \approx 0.3-0.4$. This difference may come from the gas abundance and gas-to-dust ratio of both systems as IM Lup was found to be a massive disk with mass of $\sim 0.1 M_{\odot}$ (cite: 2008A&A...489..633P), in contrast, HD 163296 has gaseous content with mass of $\sim 0.06 M_{\odot}$ as reported in Table [1](#table:modelparameters).

## Mixing of upper layers

Finally, \[CI\] may be located at a lower altitude than CO due to an efficient mechanism of mixing in the upper layers of the disk, making \[CI\] on average, to be located at a lower height and not exclusively at the surface of the disk. One way in which this may happen is through meridional flows which are expected to arise in the early stages of planet formation (cite: morbidelli2014meridional). This would be dependent on the mixing time and the destruction timescale of CO.

In (cite: teague2019meridional), high precision velocity signatures, resembling meridional flows, were detected in HD 163296. These flows match the position of previously detected continuum ring gaps and a kinematic feature detected in CO observations, postulated to be due to the presence of a 2 Jupiter-mass planet (cite: pinte2018kinematic). As this phenomena seems to be localized at certain locations within the disk, its effects get diluted by the method employed in this work which assumes an azimuthal symmetry of the disk. Therefore, we expect this effect to contribute the less compared to the other two we explored before .

# Conclusions

By using spatially resolved, archival ALMA observations of the \[CI\]$={^3}{P_1} - {^3}{P_0}$ emission line towards HD 163296, we have made the first analysis of both the radial and vertical location of atomic carbon in a class II protoplanetary disk and performed the first direct comparison of this tracer with carbon monoxide by using observations of $^{12}$CO $J=2-1$ optically thick emission line. We found \[CI\] shows an excess of flux towards the near side of the disk with a radial extension of 100 au which may be related to planets candidates. CO and \[CI\] are collocated radially up to a radius of 500 au, with first being more radially extended, this difference may be explained by the low sensitivity achieved in \[CI\] observations.

With radial average profiles of both dust continuum and the zeroth moment map of \[CI\], we were able to compare the radial extent of the \[CI\] emission with dust continuum finding the first is 2.6 times more radially extended than dust emission, in good agreement with the fact HD 163296 is a gas rich protoplanetary disk.

Regarding the vertical structure of the selected tracers, CO shows a double peaked surface emission, whose ratio $z/r$ lies in the interval $0.3 - 0.2$ before decreasing towards the outer disk at a radius of 350 au. For \[CI\], despite only 13.1 minutes of integration time were used to obtain the data, a vertical structure with a ratio $z/r \sim 0.2$ is measured up to 300 au, comparable to tracers like CN or HCN, but located, on average, at lower altitude than CO.

Brand new **DALI** models were obtained for HD 163296 and its CO and \[CI\] abundances and emission. The model shows CO emission follows closely the $\tau = 1$ curve as expected in contrast to \[CI\], whose emission is optically thin. The derived surface emission of \[CI\] agrees with the model but CO emission surface is heavily underestimated by it. Three different effects were explored in order to explain the unexpected low heights of \[CI\] emission compared to CO. First, low angular resolution of \[CI\] data may have decreased the measured profile, but it is not able to completely explain the discrepancy as the CO convolved data profile still showed a significant difference. Second, a wedge-like PDR structure instead of a thin surface towards the outer part of the disk may be able to explain the difference, which is supported by observational evidence of $\mu$m dust grains being non co-located vertically with CO as the latter account for most of the shielding in dust-gas rich environments. Finally, mixing of the upper layers may also contribute which could be done by the meridional flows observed in HD 163296.

Future observations of \[CI\] towards protoplanetary disks will enable exploring the PDR in detail, where targets like IM Lup and CU Cha offer a good starting points. New theoretical modelling for the PDR of protoplanetary disks will also be needed ideally including the effects of dust distribution, mixing and shielding.

# Acknowledgements

Francisco Urbina acknowledges Subdirection of Human Capital ANID for providing fundings for his MSc program (national MSc 2023/22231861). Mihkel Kama gratefully acknowledges funding from the European Union’s Horizon Europe research and innovation programme under grant agreement No. 101079231 (EXOHOST), and from UK Research and Innovation (UKRI) under the UK government’s Horizon Europe funding guarantee (grant number 10051045). Luke Keyte acknowledges funding via a Science and Technology Facilities Council (STFC) studentship. We thank the referee as the comments and questions during the revision process made the article significantly better.

38 natexlab

(ref: https://doi.org/10.48550/arxiv.2211.16531) Alarcón, F., Bergin, E., & Teague, R. 2022, A localized kinematic structure detected in atomic carbon emission spatially coincident with a proposed protoplanet in the HD 163296 disk

(ref: DSHARP) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41

(ref: avenhaus2018disks) Avenhaus, H., Quanz, S. P., Garufi, A., et al. 2018, The Astrophysical Journal, 863, 44

(ref: bergner2021molecules) Bergner, J. B., Öberg, K. I., Guzmán, V. V., et al. 2021, The Astrophysical Journal Supplement Series, 257, 11

(ref: 2013A&A...559A..46B) Bruderer, S. 2013, A&A, 559, A46

(ref: bruderer2012warm) Bruderer, S., van Dishoeck, E. F., Doty, S. D., & Herczeg, G. J. 2012, Astronomy & Astrophysics, 541, A91

(ref: casassus2019kinematic) Casassus, S. & Pérez, S. 2019, The Astrophysical Journal Letters, 883, L41

(ref: du2015volatile) Du, F., Bergin, E. A., & Hogerheijde, M. R. 2015, The Astrophysical Journal Letters, 807, L32

(ref: 2013PASP..125..306F) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: henning2013chemistry) Henning, T. & Semenov, D. 2013, Chemical Reviews, 113, 9016

(ref: higuchi2019first) Higuchi, A. E., Saigo, K., Kobayashi, H., et al. 2019, The Astrophysical Journal, 883, 180

(ref: isella2018disk) Isella, A., Huang, J., Andrews, S. M., et al. 2018, The Astrophysical Journal Letters, 869, L49

(ref: 2021A&A...650A.179I) Izquierdo, A. F., Testi, L., Facchini, S., Rosotti, G. P., & van Dishoeck, E. F. 2021, A&A, 650, A179

(ref: kama2016observations) Kama, M., Bruderer, S., Carney, M., et al. 2016a, Astronomy & Astrophysics, 588, A108

(ref: kama2016volatile) Kama, M., Bruderer, S., Van Dishoeck, E., et al. 2016b, Astronomy & Astrophysics, 592, A83

(ref: keyte_2023) Keyte, L., Kama, M., Booth, A. S., et al. 2023, Nature Astronomy, 7, 684

(ref: kral2019imaging) Kral, Q., Marino, S., Wyatt, M. C., Kama, M., & Matra, L. 2019, Monthly Notices of the Royal Astronomical Society, 489, 3670

(ref: Imlup_recent) Law, C. J., Alarcón, F., Cleeves, L. I., Öberg, K. I., & Paneque-Carreño, T. 2023, ApJL, 959, L27

(ref: law2022co) Law, C. J., Crystian, S., Teague, R., et al. 2022, The Astrophysical Journal, 932, 114

(ref: law2021molecules) Law, C. J., Teague, R., Loomis, R. A., et al. 2021, The Astrophysical Journal Supplement Series, 257, 4

(ref: matra2017exocometary) Matrà, L., Dent, W., Wyatt, M., et al. 2017, Monthly Notices of the Royal Astronomical Society, 464, 1415

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: morbidelli2014meridional) Morbidelli, A., Szulágyi, J., Crida, A., et al. 2014, Icarus, 232, 266

(ref: MAPS) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1

(ref: Tere) Paneque-Carreño, Miotello, A., van Dishoeck, E. F., et al. 2023, A&A, 669, A126

(ref: pintemethod) Pinte, C., Ménard, F., Duchêne, G., et al. 2018, A&A, 609, A47

(ref: 2008A&A...489..633P) Pinte, C., Padgett, D. L., Ménard, F., et al. 2008, A&A, 489, 633

(ref: pinte2018kinematic) Pinte, C., Price, D., Ménard, F., et al. 2018, The Astrophysical Journal Letters, 860, L13

(ref: rich2021investigating) Rich, E. A., Teague, R., Monnier, J. D., et al. 2021, The Astrophysical Journal, 913, 138

(ref: 2019ApJ...875...38R) Rich, E. A., Wisniewski, J. P., Currie, T., et al. 2019, ApJ, 875, 38

(ref: rosenfeld2013spatially) Rosenfeld, K. A., Andrews, S. M., Hughes, A. M., Wilner, D. J., & Qi, C. 2013, The Astrophysical Journal, 774, 16

(ref: rich_teague_2020_4321137) Teague, R. 2020, richteague/keplerian_mask: Initial Release

(ref: teague2019meridional) Teague, R., Bae, J., & Bergin, E. A. 2019, Nature, 574, 378

(ref: bettermoments) Teague, R. & Foreman-Mackey, D. 2018, Research Notes of the American Astronomical Society, 2, 173

(ref: disksurf) Teague, R., Law, C. J., Huang, J., & Meng, F. 2021, Journal of Open Source Software, 6, 3827

(ref: van1988photodissociation) Van Dishoeck, E. F. & Black, J. H. 1988, The Astrophysical Journal, 334, 771

(ref: villenave2020observations) Villenave, M., Ménard, F., Dent, W., et al. 2020, Astronomy & Astrophysics, 642, A164

(ref: woodall_umist) Woodall, J., Agúndez, M., Markwick-Kemper, A. J., & Millar, T. J. 2007, A&A, 466, 1197

# Channel maps \[CI\] emission

\
![image](figures/channel_maps_A.png)

# exponential taper modeling residuals and posterior distribution of parameters

\
![image](figures/MCMC_CO_gauss.png)

![](figures/MCMC_CI_updatedformat.png)

![](figures/residuals_CO_gauss.png)

![](figures/residuals_CI.png)

# DALI model parameters

| Parameter | Description | Value |
|:---|:---|:---|
| $R_\text{sub}$ | Sublimation radius | 0.41 au |
| $R_\text{gap}$ | Inner disk size | 3.66 au |
| $R_\text{cav}$ | Cavity radius | 3.67 au |
| $R_c$ | Critical radius for surface density | 125 au |
| $R_\text{out}$ | Disk outer radius | 1000 au |
| $\delta_\text{gas}$ | Gas depletion factor inside cavity | 1.0 |
| $\delta_\text{dust}$ | Dust depletion factor inside cavity | 0.01 |
| $\gamma$ | Power law index of surface density profile | 0.9 |
| $\chi$ | Dust settling parameter | 0.2 |
| $f$ | Large-to-small dust mixing parameter | 0.9 |
| $\Sigma_c$ | $\Sigma_\text{gas}$ at $R_c$ | 6.8 g cm$^{-2}$ |
| $h_c$ | Scale height at $R_c$ | 0.075 |
| $\psi$ | Power law index of scale height | 0.05 |
| $\Delta_\text{gd}$ | Gas-to-dust mass ratio | 100 |
| $L_X$ | Stellar X-ray luminosity | $3.98 \times 10^{29} \text{ erg s}^{-1}$ |
| $T_X$ | X-ray plasma temperature | $5.7 \times 10^{5}$ K |
| $\zeta_\text{cr}$ | Cosmic ray ionization rate | $1.7 \times 10^{-17}$ s$^{-1}$ |
| $M_\text{gas}$ | Disk gas mass | $6.7 \times 10^{-2}M_{\odot}$ |
| $M_\text{dust}$ | Disk dust mass | $6.6 \times 10^{-4}M_{\odot}$ |
| $t_\text{chem}$ | Timescale for time-dependent chemistry |  |

: Fiducial HD HD169296 disk model parameters.

# Simulated image cubes surface emission

To test how well **disksurf** tool traces the surface emission of the gas, we repeated the vertical analysis in the simulated image cubes obtained with the DALI modelling. The results, compared to DALI 75% emission contours, are shown in Fig. [12](#fig: DALI vs simulated cubes) in the appendix. There we notice that both the \[CI\] profile is located at a higher altitude from radii $>100$ au, but the difference is not as drastic as the DALI contours suggest. This is an effect of the emission being optically thin. The CO emission surface follows the DALI contours, which corresponds approximately to the $\tau = 1$ surface for the line.

![](figures/simulated_cubes_profiles.png)

</paper>

Write the methods card for this paper.