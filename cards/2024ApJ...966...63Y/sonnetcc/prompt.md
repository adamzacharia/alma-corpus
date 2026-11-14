# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...966...63Y\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...966...63Y",
 "title": "The First Spatially Resolved Detection of <SUP>13</SUP>CN in a Protoplanetary Disk and Evidence for Complex Carbon Isotope Fractionation",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Yoshida, Tomohiro C.",
 "n_authors": 10,
 "arxiv_id": "2403.00626",
 "doi": "10.3847/1538-4357/ad2fb4",
 "alma_projects_linked_by_archive": [
  "2016.1.01375.S",
  "2017.1.01199.S",
  "2018.A.00021.S"
 ]
}
```

Paper text:
<paper>
# The First Spatially-resolved Detection of $\rm ^{13}CN$ in a Protoplanetary Disk and Evidence for Complex Carbon Isotope Fractionation

## Abstract

Recent measurements of carbon isotope ratios in both protoplanetary disks and exoplanet atmospheres have suggested a possible transfer of significant carbon isotope fractionation from disks to planets. For a clearer understanding of the isotopic link between disks and planets, it is important to measure the carbon isotope ratios in various species. In this paper, we present a detection of the $\rm ^{13}CN$ $N=2-1$ hyperfine lines in the TW Hya disk with the Atacama Large Millimeter/submillimeter Array. This is the first spatially-resolved detection of $\rm ^{13}CN$ in disks, which enables us to measure the spatially resolved $\rm ^{12}CN$/$\rm ^{13}CN$ ratio for the first time. We conducted non-local thermal equilibrium modeling of the $\rm ^{13}CN$ lines in conjunction with previously observed $\rm ^{12}CN$ lines to derive the kinetic temperature, ${\rm H_2}$ volume density, and column densities of $\rm ^{12}CN$ and $\rm ^{13}CN$. The ${\rm H_2}$ volume density is found to range between $(4 - 10)\times10^7 \ {\rm cm^{-3}}$, suggesting that CN molecules mainly reside in the disk upper layer. The $\rm ^{12}CN$/$\rm ^{13}CN$ ratio is measured to be $70^{+9}_{-6}$ at $30 < r < 80$ au from the central star, which is similar to the $\rm ^{12}C/^{13}C$ ratio in the interstellar medium. However, this value differs from the previously reported values found for other carbon-bearing molecules (CO and HCN) in the TW Hya disk. This could be self-consistently explained by different emission layer heights for different molecules combined with preferential sequestration of $\rm ^{12}C$ into the solid phase towards the disk midplane. This study reveals the complexity of the carbon isotope fractionation operating in disks.

# Introduction

The physical and chemical structure of protoplanetary disks are now routinely well-studied using the unique capabilities of the Atacama Large Millimeter/submillimeter Array (ALMA). It is now clear that the rings and gaps are ubiquitous in the mm dust (cite: andr18; huan18_dsharp) and molecular gas distributions (cite: ober21maps; law21b) of large planet-forming disks. At least some of these sub-structures are thought to be related to ongoing planet formation in these disks.

The next question that we should focus on is *what kind of disk environment forms what kind of planetary system?* The link between disks and exoplanetary systems as well as our solar system is still not understood well.

To link disks to the composition of planets, chemical information is vital.

For example, (cite: ober11) proposed the carbon-to-oxygen elemental ratio (C/O) as a tracer of the birthplace of gas giant planets. Since the main carriers of carbon and oxygen, CO and H$_2$O, have different condensation temperatures, their snow lines are located at different distances from the central star in a disk. As a consequence, the gas-phase C/O ratio is expected to dramatically change as a function of radius. Therefore, it is predicted that planetary cores at different radii may accrete the disk gas with different C/O.

Similarly, isotopologue ratios are powerful material tracers in general.

In this paper, we target the carbon isotope ratio, $\rm ^{12}C/^{13}C$. Since carbon is the fourth most abundant element in the universe, and, one of the main ingredients of planetary bodies and ultimately organic molecules, it is essential to understand its behavior including the isotope chemistry during planet formation processes. In the local interstellar medium (ISM), $\rm ^{12}C/^{13}C$ is measured to be $\sim 69$ (cite: wils99). Despite its importance, the measurement of $\rm ^{12}C/^{13}C$ is quite sparse in both protoplanetary disks and planetary bodies. In the solar system comets, it is known that the $\rm ^{12}C/^{13}C$ ratio is almost constant at $91.0\pm3.6$, however, the available heliocentric radii are limited (cite: mumm11). There are a few measurements on exoplanetary atmospheres. For instance, (cite: yzha21a) observed a hot Jupiter and found a low $\rm ^{12}CO/^{13}CO$ ratio of $\sim 30$. On the other hand, (cite: line21) suggested that the $\rm ^{12}CO/^{13}CO$ ratio in a brown dwarf is enhanced compared to the ISM value.

Among protoplanetary disks, few sources have been as extensively studies as the TW Hya disk, which is the nearest disk to Earth (cite: gaia16; gaia21). (cite: zhan17) and (cite: yosh22) found a significantly low $\rm ^{12}CO/^{13}CO$ of $\sim 20-40$ at a similar radius from the central star. On the other hand, (cite: hily19) showed that the $\rm ^{12}C/^{13}C$ ratio in HCN is even higher than the ISM value.

To link the environment of disks and planets, we need to better understand the origins of such differences in measured carbon isotope ratios as well as map them spatially across the disks both radially and vertically. This requires more observational work.

In this paper, we report a measurement of the $\rm ^{12}CN/^{13}CN$ ratio using ALMA archival observations. In the next section, we describe the details of the archival observations. This is the first spatially-resolved detection of $\rm ^{13}CN$ in a disk. We use a non-LTE analysis to derive the $\rm ^{12}CN/^{13}CN$ ratio and show results in Section [3](#sec:ana). We discuss the results in Section [4](#sec:disc), and summarize this paper in Section [5](#sec:sum).

# Observations

We analyzed ALMA archival observations of the $\rm ^{13}CN$ and $\rm ^{12}CN$ lines in the TW Hya disk to derive the $\rm ^{12}CN/^{13}CN$ ratio. The following data reduction and imaging was performed with Common Astronomy Software Applications (cite: mcmu07) modular version 6.2.5 with the exception of the pipeline calibration which was performed in the CASA version used for the original publication. All images we used for analysis are convolved by an elliptical Gaussian to match the final beam to a circular Gaussian with an FWHM of $0.5\ensuremath{''}$ using the CASA tasks ` imsmooth`, which is the smallest common resolution we can achieve.

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Transition | Representative Freq. | Project ID | `robust` | Original Beam | Chan. Wid. | RMS | Int. Time |
|   | (GHz) |   |   |   | (${\rm km\ s^{-1}}$) | (${\rm mJy\ beam^{-1}}$) | ($\rm min$) |
| ${\rm ^{13}CN\ N=2-1}$ | 217.467150 | 2016.1.01375.S | 0.0 | $0.46\ensuremath{''} \times 0.44\ensuremath{''}, -88^\circ$ | 0.34 | 1.0 | 41 |
| ${\rm ^{12}CN\ N=2-1}$ | 226.874781 | 2018.A.00021.S | 1.0 | $0.42\ensuremath{''} \times 0.33\ensuremath{''}, 88^\circ$ | 0.10 | 0.89 | 228 |
| ${\rm ^{12}CN\ N=1-0}$ | 113.490970 | 2017.1.01199.S | 0.0 | $0.50\ensuremath{''} \times 0.45\ensuremath{''}, 42^\circ$ | 0.10 | 3.1 | 105 |

a The original CLEAN images were convolved a Gaussian to make the final beam to $0.5\ensuremath{''}\times0.5\ensuremath{''}$.

b Measured after matching the beam

We summarize the observation details in Table [\[tab:obs\]](#tab:obs) and describe in the following.

## $\rm ^{13}CN$

The ALMA archival data (ID: 2016.1.01375.S, PI: C. Rab) consists of two execution blocks (EBs). The first EB was observed on Nov.19, 2016 with 43 antennas, while the second EB was observed on Nov.20, 2016 with 42 antennas. For both EBs, the integration time was 41 minutes, and the baseline range was 15-704 m. For both EBs, the quasar J1037-2934 was used as the gain calibrator while J1107-4449 was used as a flux calibrator. As the bandpass calibrator, J1037-2934 and J1107-4449 were used for the first and second EBs, respectively.

The $\rm ^{13}CN$ $N=2-1$ lines were observed in the spectral window 1 of the baseband 1 with the spectral resolution of $\sim 0.67\ {\rm km\ s^{-1}}$ . Table.[\[tab:13cnlines\]](#tab:13cnlines) shows a full listing of the hyperfine lines that are covered in the archival data.

For data reduction, we first executed the pipeline calibration by running `scriptForPI.py`. Then, we CLEANed the continuum SPW using the CASA task `tclean` after flagging the detected emission lines. We performed five rounds of phase self-calibration with solution intervals of the duration of the EBs, 1200s, 600s, 300s, and 100s as well as one round of amplitude self-calibration with the duration of the EBs. The solutions were applied to the SPW containing $\rm ^{13}CN$ $N=2-1$ lines without flagging lines, and the continuum emission was subtracted by fitting a linear function to line-free channels on the visibility space using the `uvcontsub` task. Finally, the velocity channels that contain the $\rm ^{13}CN$ lines were imaged with a channel spacing of 0.34 $\rm km\ s^{-1}$ (half of the velocity resolution) and robust parameter of 0.5. For the CLEAN mask, a Keplerian mask made with a Python script `Keplerian_mask` (cite: kepmask) was used assuming the disk inclination angle of $5.8^\circ$, position angle of $151.6^\circ$, stellar mass of $0.81\ M_\odot$, the systemic velocity of $2.84\ \rm km\ s^{-1}$, following (cite: teag19). The outer radius of the mask was set to 3.0 arcsec to contain all emissions in the mask. The CLEAN image cube was then convolved by an elliptical Gaussian to match the final beam to a circular Gaussian with an FWHM of $0.5\ensuremath{''}$ using ` imsmooth `, and primary beam correction was applied with `impbcor`. The root mean square (RMS) noise level is estimated to be 1.0 mJy, which is calculated by averaging the RMS value of the first and last three line-free channels of the image cube before primary beam correction.

## $\rm ^{12}CN$

We also analyzed ALMA observations of the ${\rm ^{12}CN}\ N=2-1$ lines (ID:2018.A.00021.S, PI: R. Teague). The measurement sets include ${\rm CO}\ J=2-1$ and ${\rm CS}\ J=3-2$ lines as well.

Details about these observations are described in (cite: teag22). After downloading the data and running the pipeline calibration, we first imaged and self-calibrated the continuum only using the short baseline data. Then, the data was combined with the longer baseline EBs. We noticed that the amplitude as a function of the uv distance of one EB systemically deviates from others, therefore, that EB is totally flagged. We performed six rounds of phase self-calibration to the combined data. The solution interval is decreased from the duration of EBs to 30 seconds. Then, we ran one round of amplitude self-calibration with the duration of EBs. The solutions of the self-calibration were applied to the spectral windows containing the $\rm ^{12}CN$ lines. After subtracting the continuum emission, two SPWs that contain the $\rm ^{12}CN$ lines were CLEANed using `tclean` with a velocity channel width of $0.1\ {\rm km\ s^{-1}}$ and robust parameter of 1.0 using a CLEAN mask generated by a Python script, `Keplerian_mask`.

We also used the $\rm ^{12}CN\ N=1-0$ data from the archive (ID: 2017.1.01199.S, PI: R. Loomis). The details of these observations were described in (cite: teag20). We ran pipeline calibration and self-calibration in a similar way of (cite: teag20) and CLEANed with a robust parameter of 0. Both of the $\rm ^{12}CN$ data cubes were also re-convolved by a Gaussian that matches the final beam to the $0.5\ensuremath{''}$ circular Gaussian for consistency.

We also checked the absolute flux consistency among the three observation sets. We extracted a spectral energy distribution (SED) from the peak intensity of continuum images corresponding to the $\rm ^{12}CN$ $N=1-0,\ 2-1$ and $\rm ^{13}CN$ $N=2-1$ image cubes. The continuum images are also re-convolved and the beam is a circular Gaussian with a FWHM of $0.5\ensuremath{''}$. The SED can be well fitted by a power-law curve with an index of 2.13, which is consistent with the literature (cite: tsuk16; ueda20; maci21; tsuk22). The deviations from the best-fit curve are $\sim -0.3\%,\ 3.1\%$, and $-2.7\%$ for the continuum images corresponding to the $\rm ^{12}CN$ $N=1-0,\ 2-1$ and $\rm ^{13}CN$ $N=2-1$ images. Since these deviations are sufficiently small, we neglect the uncertainty on the absolute flux scaling in the following analysis.

| $J$ | $F_1$ | $F$ | Frequency \[GHz\] | $A\ [{\rm s^{-1}}]$ | $g_u$ | $E_{\rm up}\ {\rm [K]}$ |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 3/2-1/2 | 1-0 | 0-1 | 217.264639 | $6.05 \times 10^{-4}$ | 1 | $15.7$ |
| 3/2-1/2 | 2-1 | 1-2 | 217.276438 | $2.70 \times 10^{-5}$ | 3 | $15.6$ |
| 3/2-1/2 | 1-0 | 1-1 | 217.277680 | $5.80 \times 10^{-4}$ | 3 | $15.7$ |
| 3/2-1/2 | 2-1 | 2-2 | 217.286804 | $2.42 \times 10^{-4}$ | 5 | $15.6$ |
| 5/2-3/2 | 2-2 | 2-1 | 217.287543 | $3.08 \times 10^{-5}$ | 5 | $15.7$ |
| 5/2-3/2 | 2-2 | 3-2 | 217.289801 | $2.22 \times 10^{-5}$ | 7 | $15.7$ |
| 3/2-1/2 | 2-1 | 1-1 | 217.290823 | $4.00 \times 10^{-4}$ | 3 | $15.6$ |
| 5/2-3/2 | 2-2 | 1-1 | 217.294470 | $1.64 \times 10^{-4}$ | 3 | $15.7$ |
| 3/2-1/2 | 2-1 | 1-0 | 217.296605 | $5.30 \times 10^{-4}$ | 3 | $15.6$ |
| 5/2-3/2 | 2-2 | 2-2 | 217.298937 | $1.50 \times 10^{-4}$ | 5 | $15.7$ |
| 3/2-1/2 | 2-1 | 2-1 | 217.301175 | $7.16 \times 10^{-4}$ | 5 | $15.6$ |
| 3/2-1/2 | 2-1 | 3-2 | 217.303191 | $9.60 \times 10^{-4}$ | 7 | $15.6$ |
| 3/2-1/2 | 1-0 | 2-1 | 217.304927 | $5.31 \times 10^{-4}$ | 5 | $15.7$ |
| 5/2-3/2 | 2-2 | 1-2 | 217.305904 | $5.25 \times 10^{-5}$ | 3 | $15.7$ |
| 5/2-3/2 | 2-2 | 3-3 | 217.306117 | $1.88 \times 10^{-4}$ | 7 | $15.7$ |
| 5/2-3/2 | 2-2 | 2-3 | 217.315147 | $3.16 \times 10^{-5}$ | 5 | $15.7$ |
| 5/2-3/2 | 2-1 | 3-2 | 217.428563 | $7.67 \times 10^{-4}$ | 7 | $15.7$ |
| 5/2-3/2 | 2-1 | 2-1 | 217.436350 | $5.89 \times 10^{-4}$ | 5 | $15.7$ |
| 5/2-3/2 | 2-1 | 2-2 | 217.437702 | $1.76 \times 10^{-4}$ | 5 | $15.7$ |
| 5/2-3/2 | 2-1 | 1-1 | 217.443722 | $3.09 \times 10^{-4}$ | 3 | $15.7$ |
| 5/2-3/2 | 2-1 | 1-0 | 217.443722 | $4.35 \times 10^{-4}$ | 3 | $15.7$ |
| 5/2-3/2 | 2-1 | 1-2 | 217.444666 | $1.87 \times 10^{-5}$ | 3 | $15.7$ |
| 5/2-3/2 | 3-2 | 4-3 | 217.467150 | $1.01 \times 10^{-3}$ | 9 | $15.7$ |
| 5/2-3/2 | 3-2 | 3-2 | 217.467150 | $8.92 \times 10^{-4}$ | 7 | $15.7$ |
| 5/2-3/2 | 3-2 | 2-1 | 217.469151 | $8.43 \times 10^{-4}$ | 5 | $15.7$ |
| 5/2-3/2 | 3-2 | 2-2 | 217.480559 | $1.59 \times 10^{-4}$ | 5 | $15.7$ |
| 5/2-3/2 | 3-2 | 3-3 | 217.483606 | $1.14 \times 10^{-4}$ | 7 | $15.7$ |
| 5/2-3/2 | 3-2 | 2-3 | 217.496736 | $4.70 \times 10^{-6}$ | 5 | $15.7$ |

Notes. $J, F_1$ and $F$ are the quantum numbers. $A$ and $g_u$ are the Einstein A coefficients and upper state degeneracy. The data is taken from the CDMS database (cite: mull01; mull05; endr16).

# Analysis and Results

## The image of $\rm ^{13}CN$ and matched filter analysis

We created moment zero maps of the three brightest lines with the same Keplerian mask used in the CLEANing process using the CASA task `immoments` and then stacked each of these moment zero maps to maximize the signal-to-noise ratio. Figure [1](#fig:mom0) shows the resulting $\rm ^{13}CN$ $N=2-1$ moment maps. The $\rm ^{13}CN$ $N=2-1$ emission exhibits a ring-like morphology, which is similar to the $\rm ^{12}CN$ lines (cite: teag20). Also, the emission is extended beyond the continuum disk that is shown in the white dotted contour.

Although the $\rm ^{13}CN$ lines are clearly detected on the image plane, we also ran the matched filter analysis (cite: loom18). The Keplerian mask was used to generate the filter kernel. The mask is similar to that used for CLEANing of the $\rm ^{13}CN$ lines but with a smaller outer radius of 1.6 arcsec just to contain the emission of the brightest line (${\rm ^{13}CN}\ N=2-1\ J=5/2-3/2\ F_1=3-2\ F=4-3$). The cross-correlation between the observed visibilities and filter kernel was calculated by a Python script `VISIBLE` (cite: loom18). The response spectrum is shown in Figure [2](#fig:mf). Assuming the local thermal equilibrium (LTE), a predicted relative optical depth spectrum at $T=40$ K suggested by (cite: teag20) is also plotted. Five hyperfine lines are detected in a significance of $>5\sigma$, and the brightest line, ${\rm ^{13}CN}\ N=2-1\ J=5/2-3/2\ F_1=3-2\ F=4-3$, exceeds a $\sim 20 \sigma$ significance. This is the first spatially-resolved detection of $\rm ^{13}CN$ in a protoplanetary disk. Note that (cite: phuo21) reported a detection of $\rm ^{13}CN$ in the GG Tau A disk with $\sim 6-8\sigma$ significance. The MAPS project (cite: ober21maps) also observed the ${\rm ^{13}CN}\ N=2-1$ line but it was not detected. This is because they only covered the first seven hyperfine lines listed in Table [\[tab:13cnlines\]](#tab:13cnlines), whose Einstein A coefficients (times upper state degeneracy) are relatively smaller.

## Non-LTE modeling of azimuthally averaged spectra of $\rm ^{12}CN$ and $\rm ^{13}CN$ 

For further analysis, the spectra at each position were azimuthally stacked assuming Keplerian rotation using the python package `gofish` (cite: teag16).

We used the same disk geometric parameters as used for the CLEAN mask. We also specified the disk center position by fitting a 2D Gaussian to the corresponding continuum images. The resultant stacked spectra of the $\rm ^{12}CN$ and $\rm ^{13}CN$ lines as a function of the radius from the central star and velocity shift from the rest frame of the brightest lines in each hyperfine group are presented in Figure [3](#fig:gf).

For the $\rm ^{13}CN$ lines, we also present the disk integrated flux spectrum after stacking with `gofish` in Figure [4](#fig:integrated). Here, we adopted the disk outer radius of 3.0 arcsec.

To derive the physical quantities, we generated synthetic spectra and compared them with the azimuthally stacked spectra. (cite: teag20) previously found that the $\rm ^{12}CN$ lines are not in LTE by comparing independently derived kinetic and excitation temperatures. Therefore, we performed non-LTE modeling. The peak optical depth $\tau_{c, i}$ and excitation temperature $T_{{\rm ex}, i}$ of each hyperfine line $i$ are calculated in three-dimensional grids for each SPW by using a Python wrapper of the non-LTE radiative transfer code RADEX (cite: vand07), `SpectralRadex`[^1] (cite: hold21). We adopted publically available spectroscopic data (cite: klis95; thom68; kalu15) via the LAMDA database (cite: scho05) for the $\rm ^{12}CN$ lines.

For the $\rm ^{13}CN$ lines, we used the LAMDA format file in the EMAA database [^2] which is based on (cite: mull05) and (cite: flow15).

Note that the rate coefficients are available only for collision with para-$\rm H_2$, so we ignored ortho-$\rm H_2$ in our analysis. This may not be an issue if the rate coefficients against para- and ortho-$\rm H_2$ are similar as seen in CO since the ortho-to-para ratio of $\rm H_2$ at $30-50$ K is $0.031-0.30$ under the thermal equilibrium (cite: flow84; flow85) which is expected in disks (cite: aika18). However, as in the case of $\rm ^{12}CN$, these rate coefficients could be significantly different. New spectroscopic data for collision with ortho-$\rm H_2$ are required to model the $\rm ^{13}CN$ lines more robustly.

Each RADEX grid consists of the kinetic temperature $T_k$, column density of $\rm ^{12}CN$ or $\rm ^{13}CN$  $N({\rm ^{12}CN}), N({\rm ^{13}CN})$, and ${\rm H_2}$ volume density $n({\rm H_2})$. Here, we assumed that all lines share the same $T_k$ and $n({\rm H_2})$, and the line width is identical to the thermal width. We also adopted the background emission of the black body radiation at 2.73 K. Note that the dust continuum emission is similar to or fainter than 2.73 K at $100-200$ GHz at $R>40$ au. While $T_{\rm kin}$ is gridded linearly, $N$ and $n({\rm H_2})$ are sampled logarithmically. The parameter ranges are listed in Table [1](#tab:prior).

| Parameters | Ranges | Units |
|:--:|:--:|:--:|
| $\log_{10} n({\rm H_2})$ | $[6, 12]$ | $\rm cm^{-3}$ |
| $\log_{10} N({\rm ^{12}CN}), \log_{10} N({\rm ^{13}CN})$ | $[11, 16]$ | $\rm cm^{-2}$ |
| $T_k$ | $[10, 100]$ | $\rm K$ |
| $v_{\rm sys}$ | $[2.6, 3.0]$ | $\rm km\ s^{-1}$ |
| $\Delta v_{j}$ | $[0.02, 2.0]$ | $\rm km\ s^{-1}$ |

: Parameter ranges in our fitting

The number of the grid is 100 along each dimension.

Then, we generated synthetic spectra of all observed $\rm ^{12}CN$ and $\rm ^{13}CN$ lines at each radius using $\tau_{c, i}$ and $T_{{\rm ex}, i}$ calculated by `SpectralRadex` and fitted them to the observed spectra as the following. First, $T_k$, $n({\rm H_2})$, and $N({\rm ^{12}CN})$ (or $N({\rm ^{13}CN})$) are inputted to the model grids, and they return $\tau_{c, i}$ and $T_{{\rm ex}, i}$ for each hyperfine line $i$ by interpolation of the grids. Then, we calculated the optical depth profile $\tau_i(v)$ of each line by adopting thermal line width, where $v$ is the velocity with respect to the brightest line in each group. We assumed that the molecular and dust emitting regions are vertically distinct; while the dust grains are settled on the midplane, the molecular emission originates from higher altitude regions. The intensity coming from one-sided molecular layer $I_{\rm mol}$ is expressed as $$\begin{equation}
I_{\rm mol}(v) = \displaystyle \frac{\sum_i B(T_{{\rm ex}, i}) \displaystyle  \frac{\tau_i(v)}{2}  }{ \sum_i \displaystyle 
 \frac{\tau_i(v)}{2}   } \left\{ 1 - \exp\left( -\sum_i \displaystyle \frac{\tau_i(v)}{2}  \right) \right\},
\end{equation}$$ following (cite: hsie15), where $B(T_{{\rm ex}, i})$ is the Planck function at the temperature $T_{{\rm ex}, i}$ at the corresponding frequency. This formulation can treat the line overlapping approximately. Since we consider the three-layer (molecules in the backside, dust grains at the midplane, and molecules in the frontside) model along the line of sight, the resultant intensity $I_{\rm mod}$ after subtracting the continuum emission can be written as $$\begin{equation}
I_{\rm mod}(v) = \left\{  I_{\rm mol} \exp(-\tau_d) + I_c \right\} \exp\left( -\sum_i \displaystyle \frac{\tau_i(v)}{2}  \right)  + I_{\rm mol} - I_c,
\end{equation}$$ where $\tau_d$ and $I_c$ are the dust optical depth at each wavelength taken from (cite: maci21) and observed continuum emission, respectively. Note that the factors $\exp{(-\tau_d)}$ and $\exp({-\sum_i \tau_i(v)/2})$ express the continuum absorption at the midplane and molecular line absorption in the frontside, respectively. The model spectrum $I_{\rm mod}(v)$ is generated with a $15$ kHz interval, shifted by the systemic velocity $v_{\rm sys}$, and convolved by a Gaussian with a standard deviation of $\Delta v_j$ in each SPW ($j=1-4$), approximating any instrumental broadening effect due to the velocity resolution of the correlator and Keplerian shear in a beam (cite: berg21; muno23). As a result, we have nine free parameters at each radius, $n({\rm H_2}), T_k, N({\rm ^{12}CN}), N({\rm ^{13}CN}), v_{\rm sys}$ and $\Delta v_j$ for four SPWs. The generated synthetic spectra are compared with the observed spectra shown in Figure [3](#fig:gf) in terms of the log-likelihood function $$\begin{equation}
\log{ \mathcal{L} } = -\frac{1}{2} \sum_v \left( \frac{I_{\rm mod}(v) - I_{\rm obs}(v) }{ \sigma_{\rm obs} } \right)^2,
\end{equation}$$ where the summation is done over all velocity channels of the observations. $I_{\rm obs}(v)$ and $\sigma_{\rm obs}$ are the azimuthally stacked spectra and their standard deviation, respectively. $\sigma_{\rm obs}$ is calculated for independent velocity bins; for the $\rm ^{12}CN$ lines, since the original velocity resolution is narrower than the final channel width, the calculated standard deviations are directly used. On the other hand, the standard deviation calculated in the $\rm ^{13}CN$ spectra is multiplied by $\sqrt{2}$ because the channel width is half of the velocity resolution. In practice, with the uniform prior shown in Table [1](#tab:prior), we used `emcee` (cite: fore13) and sampled the posterior distribution by the Markov Chain Monte Carlo (MCMC) method. We set our MCMC chains with 64 walkers and 10,000 steps and a burn-in of the first 6,000 steps. The marginal posterior distributions are almost Gaussian for all parameters and radii. We present the representative corner plots in Appendix [\[appendix\]](#appendix).

## Fitting Results

We plot the fitting results in Figure [5](#fig:results).

Panel (a) shows the column density profiles of $\rm ^{12}CN$ and $\rm ^{13}CN$. The column density of $\rm ^{12}CN$ ranges $10^{14-15}\ {\rm cm^{-2}}$ at r = $30-120$ au. This value is broadly consistent with the disk averaged $\rm ^{12}CN$ column density of $(9.6\pm1.0) \times 10^{13}\ {\rm cm^{-2}}$ obtained from the data observed by the Atacama Pathfinder Experiment telescope (cite: kast14) and that of $\sim 10^{14} {\rm cm^{-2}}$ estimated by (cite: hily17) using ALMA observations. The slope of the column density profiles changes at $r\sim 80$ au, corresponding to the truncation radius of the mm-continuum disk (cite: ilee22).

The best-fit kinetic temperature (panel b) is lower than that derived from the brightness temperature of ${\rm ^{12}CO}\ J=3-2$ (cite: huan18) but higher than ${\rm ^{13}CO}\ J=3-2$ (cite: nomu21), suggesting that CN molecules exist at a higher altitude than most of CO molecules. This is also evident in the $n({\rm H_2})$ profile (panel c), which shows that $n({\rm H_2})$ at $r < 80$ au is $\sim 4\times10^7\ {\rm  cm^{-3}}$. The gas surface density and gas scale height at $r=60$ au are $\sim 4\ {\rm g\ cm^{-2}}$ and $\sim5$ au, respectively, in the fiducial TW Hya disk model of (cite: cala21). Assuming these values, a mean molecular weight of 2.37, and that vertical gas distribution follows a Gaussian, $n({\rm H_2}) = 4\times10^7\ {\rm cm^{-3}}$ corresponds to an altitude of $z/r\sim0.27$ in the model. Meanwhile, $n({\rm H_2})$ is gradually increasing toward the outer region and reaches $\sim 10^8\ {\rm cm^{-3}}$ at 100 au, which corresponds to $z/r\sim0.22$ in the fiducial model of (cite: cala21). The derived $n({\rm H_2})$ are roughly consistent with those found by (cite: muno23) from modeling of spatially-resolved multi-line DCN and DCO$^+$ observations. The derived kinetic temperature and $\rm H_2$ volume density are consistent with the previous analysis by (cite: teag20) as well as previous disk models (cite: clee15; lee21; nomu21).

We also derive the $\rm ^{12}CN$/$\rm ^{13}CN$ column density ratio (panel d). The ratio is consistent with the ISM value (cite: wils99) over $30 < r < 80$ au. We calculated the median and \[16, 84\] th percentiles of posteriors, and find $\rm ^{12}CN$/$\rm ^{13}CN$ $\simeq 70^{+9}_{-6}$ is a representative value. Also, it is likely that there is a dip of $\rm ^{12}CN$/$\rm ^{13}CN$ at $r \sim 100$ au, although its deviation from the ISM value is only $\sim 3 \sigma$. At the local minimum, $\rm ^{12}CN$/$\rm ^{13}CN$ is estimated to be $48^{+5}_{-4}$.

We also plot the best-fit systemic velocity and effective velocity resolutions for each SPW in panel (e) and (f). The stable systemic velocities as a function of radius verify that the shift-and-stack process was successful. The effective velocity resolutions for the $\rm ^{12}CN$ lines increase as the radius approaches the disk center. This is because the velocity gradient due to the Keplerian shear in one beam is larger near the disk center.

# Discussion

## Vertical distribution of CN

The derived kinetic temperature and $\rm H_2$ volume density imply that the CN emission mainly arises from the upper layer of the inner disk ($r \lesssim 80$ au) and relatively closer to the midplane in the outer disk ($r \gtrsim 80$ au). The estimated altitude of the CN emitting region of $z/r\sim0.2-0.3$ is consistent with the previous study on TW Hya (cite: teag20) as well as the MAPS targets (cite: berg21), but much lower than the Elias 2-27 disk (cite: pane22).

It has been suggested that the vertical distribution of CN is strongly affected by the UV attenuation in a disk (cite: aika06; cazz18). (cite: aika06) found that the location of the CN abundance peak in the vertical direction of the disks shifts toward the midplane when the UV attenuation by dust particles is weakened although the CN column density is not affected. Indeed, the mm-continuum emission truncates around $r\sim80$ au (cite: ilee22), and the infrared scattered light exhibits a gap at $r\sim80-100$ au (cite: boek17), implying that the UV attenuation is weakened in the outer disk. A recent chemical model dedicated of the TW Hya disk by (cite: nomu21) also shows that CN can exist near the midplane outside the dust disk, which is consistent with our results. The MAPS project suggested that the CN/HCN column density ratio is correlated with the mm-dust continuum gaps although it is not one-to-one correspondence (cite: berg21). Our results showing enhancement of CN near the midplane outside the mm-continuum disk are in line with their results.

##  Carbon isotope fractionation scenarios in the TW Hya disk 

The $\rm ^{12}CN$/$\rm ^{13}CN$ column density ratio between $30<r<80$ au is $70^{+9}_{-6}$, similar to the ISM ratio. The carbon isotope ratio in the TW Hya disk has also been measured in other carbon-bearing molecules. The carbon isotope fractionation pattern in the similar region of the TW Hya disk is quite complex.

A low $\rm ^{12}CO/^{13}CO$ ratio of $21\pm5$ is suggested by analyzing the $\rm ^{12}CO$ and ${\rm ^{13}CO}$ line wings at $r\sim70-110$ au (cite: yosh22). (cite: zhan17) also found a low $\rm ^{12}C^{18}O/^{13}C^{18}O$ ratio of $40^{+9}_{-6}$ at $r\sim21$ au. On the other hand, (cite: hily19) measured the $\rm H^{12}CN/H^{13}CN$ ratio to be $86\pm4$ at $r\sim20-55$ au. Although we should be cautious about differences in methods, it is clear that different molecules have different carbon isotope ratios.

To discuss carbon isotope fractionation in the TW Hya disk, it is necessary to estimate and compare column densities of carbon bearing molecules to understand which species is the major carbon carrier. The column densities of CN and HCN are much lower than that of CO (cite: zhan17; lee21). The averaged column density of the neutral atomic carbon can be estimated to be $\sim 7 \times 10^{15}\ {\rm cm^{-2}}$ from the observed value in (cite: kama16a) using equations in (cite: oka01) and (cite: tsuk15) assuming LTE and excitation temperature of 50 K. This value is also 1-2 orders of magnitude smaller than CO.

Hydrocarbons are other carbon bearing species in disks. The column density of $\rm C_2H$ at $r=100$ au from the central star is $\sim 10^{13} - 10^{14}\ {\rm cm^{-2}}$ according to models by (cite: berg16). In summary, it is likely that the main carbon carrier in the TW Hya disk gas is CO.

The fact that CO is the main carbon carrier means that the bulk gas $\rm ^{12}C/^{13}C$ is significantly low, $\sim 20-40$. In the gas of a protoplanetary disk, there are two mechanisms that can cause carbon isotope fractionation; isotope-selective photodissociation and isotope exchange reaction (cite: wood09; viss18). In both cases, however, the carbon isotope ratio in the bulk gas does not change. Therefore, carbon isotope fractionation between the gas and solid phase is needed to explain the observed isotopologue ratios. In other words, $\rm ^{12}C$ would be selectively incorporated in the solid phase. Future observations with the James Webb Space Telescope could find evidence of $\rm ^{13}C$-poor solid material.

So, what did make CO in the gas phase $\rm ^{13}C$-rich? It is suggested that the gas-phase CO is depleted within the timescale of a few Myr from the protostellar stage by observations and models ( e.g., (cite: zhan20; krij20; furu22), but cf. (cite: pasc23)). Simultaneously the gas-phase C/O ratio outside the CO snowline becomes even larger than unity (cite: ober11; krij20; bosm21b; cala23). Since the stellar age of TW Hya is estimated to be 3-10 Myr (cite: barr06; vacc11), it is possible that the high C/O ($>1$) ratio has been sustained for more than a few Myr in the past. In this case, the isotope exchange reaction $$\begin{equation}
\label{eq:CO}
{\rm ^{13}C^+ + ^{12}CO \rightleftharpoons ^{12}C^+ + ^{13}CO + 35\ K},
\end{equation}$$ can enhance the gas-phase $\rm ^{13}CO$ in a relatively low-temperature environment ($\lesssim 35$ K). Subsequent chemical reactions and physical processes such as dust coagulation could lock the molecules produced from $\rm ^{12}C^+$ to the dust grains, making the bulk gas $\rm ^{13}C$-rich. On the other hand, the carbon bearing molecules in the dust grains would be slightly $\rm ^{13}C$-poor compared to the ISM ratio.

Meanwhile, if CO is the main carbon carrier in the bulk gas, the current gas-phase C/O ratio should be almost unity or less; for instance, if there are only CO molecules except for $\rm H_2$ in the gas phase, the abundance of carbon equals that of oxygen, or, $\rm C/O=1$. However, (cite: berg16) suggested that a high gas-phase C/O ratio of $>1$ is needed to reproduce the bright $\rm C_2H$ emission. This apparent contradiction might be solved by the vertical stratification of C/O as predicted by in some models (cite: krij20). The CO isotopologue ratio measured by (cite: yosh22) reflects the region near the CO snow surface, which is located deeper in the disk, as they used the optically thin line wings, while $\rm C_2H$ mainly reside in the upper layer where C/O exceeds unity.

Our analysis shows that CN traces higher altitude than $\rm ^{13}CO$, where the $\rm C_2H$ emission may arise with $\rm C/O > 1$. The carbon isotopologue ratios in the upper layer could be modified by the in-situ reactions including reaction ([\[eq:CO\]](#eq:CO)). Therefore, the isotopologue ratios of CN and HCN may be explained in a way similar to the previous models (cite: wood09; viss18).

Another scenario to explain the low carbon isotope ratio in CO, which is less likely but cannot be ruled out, is that the bulk gas- and solid-phase $\rm ^{12}C/^{13}C$ deviates from the local ISM ratio. It is known that the $\rm ^{12}C/^{13}C$ in molecular clouds changes as a function of the distance from the Galactic center due to the chemical evolution of the galaxy. However, observations of carbon bearing species in molecular clouds show some scatter even at the similar distance (cite: mila05). Therefore, we cannot exclude the possibility that the prestellar cloud of TW Hya was an outlier from the local isotope abundance.

##  CN and HCN isotopologue ratios

The $\rm H^{12}CN/H^{13}CN$ ratio of $86\pm4$ (cite: hily19) is higher than $\rm ^{12}CN$/$\rm ^{13}CN$ of $70^{+9}_{-6}$. (cite: lois20) listed several isotope exchange reactions related to HCN and CN including $$\begin{eqnarray}
\label{eq:CN1} {\rm ^{13}C^+ + ^{12}CN} &\rightleftharpoons& {\rm ^{12}C^+ + ^{13}CN + 31.1\ K} \\
\label{eq:CN2} {\rm ^{13}C + ^{12}CN} &\rightleftharpoons& {\rm ^{12}C + ^{13}CN + 31.1\ K} \\
\label{eq:CN3} {\rm ^{13}C + H^{12}CN} &\rightleftharpoons& {\rm ^{12}C + H^{13}CN + 48.0\ K}.
\end{eqnarray}$$ Interestingly, reaction ([\[eq:CN3\]](#eq:CN3)) has a larger zero point energy difference than reaction ([\[eq:CN2\]](#eq:CN2)) with similar rate constants, which means that HCN should become more $\rm ^{13}C$-rich if there are only C, CN, and HCN. Indeed, in the TW Hya disk, the column density of the neutral carbon is comparable to or even larger than that of CN and HCN (Section [4.2](#sec42)). However, our results showed that CN is more $\rm ^{13}C$-rich than HCN. This implies that other reactions including reaction ([\[eq:CN1\]](#eq:CN1)) may play an important role.

More realistic models that consider both physical and chemical processes with a larger chemical reaction network are required to reveal the complex carbon isotope fractionation pattern (Lee et al., submitted).

We also note that a potential molecular stratification of CN and HCN (i.e. CN traces higher altitude than HCN) could also explain the isotopologue ratio that is inconsistent with the zero point energy differences.

##  The $\rm ^{12}CN$/$\rm ^{13}CN$ dip at $r\sim100$ au 

It is more difficult to explain the origin of the low $\rm ^{12}CN$/$\rm ^{13}CN$ ratio of $48^{+5}_{-4}$ at $r\sim100$ au. First, we can interpret this as a radial variation of $\rm ^{12}CN$/$\rm ^{13}CN$. Indeed, in the (cite: viss18) model, it is shown that the column density ratios of $\rm H^{12}CN/H^{13}CN$ and $\rm ^{12}CN/^{13}CN$ have a radial dependence with a dip $\sim150-200$ au, although it is not a source-specific model for TW Hya. In terms of a radial variation, (cite: yosh22) found a high value of $\rm ^{12}CO/^{13}CO > 84$ at $r\sim100$ au and they attributed it to the binding energy difference of $\rm ^{12}CO$ and $\rm ^{13}CO$ to ices. However, it is unclear if the low $\rm ^{12}CN$/$\rm ^{13}CN$ ratio at $r\sim100$ au is actually correlated to the high $\rm ^{12}CO/^{13}CO$ ratio beyond $r\sim100$ au since the spatial resolution of the data in (cite: yosh22) and this paper are both limited. The vertical variation of the $\rm ^{12}CN$/$\rm ^{13}CN$ ratio can be another explanation. In terms of the $\rm H_2$ volume density, the CN emission at $r\sim100$ au arises from a deeper region compared to $30 < r < 80$. Therefore, if the $\rm ^{12}CN$/$\rm ^{13}CN$ ratio near the midplane is lower than that in the upper layer, the observed profile could be reproduced without significant radial variation. We note that these two possibilities are not mutually exclusive; both radial and vertical differences in the $\rm ^{12}CN$/$\rm ^{13}CN$ ratio may contribute to it. In both cases, the physical structure such as the gap seen in the scattered light (cite: boek17) may be related to the variation of $\rm ^{12}CN$/$\rm ^{13}CN$.

##   Caveats 

There are some caveats for our analysis. First, our non-LTE modeling uses the RADEX code, which does not treat e.g. the overlap effect of emission lines. This might affect the excitation conditions as well as the resultant parameters. However, this effect is beyond the current radiative transfer capabilities.

We should also pay attention to the non-LTE spectra model fitting, where we assume that the kinetic temperature and $\rm H_2$ volume density are the same among all hyperfine lines. This means, in other words, we assume that the emission comes from a homogeneous medium along a line-of-sight. However, the temperature and density structures in protoplanetary disks have a vertical gradient in reality (cite: dull02; law21).

Therefore, if the kinetic temperature of the line emitting regions of $\rm ^{12}CN$ and $\rm ^{13}CN$ are different, it may be possible that the retrieved $\rm ^{13}CN$ column density is affected by the optically thick $\rm ^{12}CN$ hyper-fine lines. More detailed modeling is required to exclude this possibility. However, it is not only beyond the scope of this paper but also it needs deeper observations with multiple transitions of $\rm ^{13}CN$.

# Summary

We have analyzed archival ALMA data of the $\rm ^{13}CN$ lines in the TW Hya disk. Our findings are summarized as follows:

1.  The $\rm ^{13}CN$ $N=2-1$ hyperfine lines are detected. This is the first spatially-resolved detection of $\rm ^{13}CN$ in protoplanetary disks. The ring-like morphology of the emission resembles that of $\rm ^{12}CN$.

2.  In conjunction with the $\rm ^{12}CN$ lines, we conducted a non-LTE analysis to derive the kinetic temperature and ${\rm H_2}$ volume density of the line emitting regions, and $\rm ^{12}CN$ and $\rm ^{13}CN$ column densities at each disk radius. The derived low ${\rm H_2}$ density of $\sim 4\times10^7\ {\rm cm^{-3}}$ at $r < 80$ au suggests that the CN traces the disk upper layer ($z/r\sim 0.2-0.3$).

3.  The $\rm ^{12}CN$/$\rm ^{13}CN$ ratio is derived to be $70^{+9}_{-6}$ between $30 < r < 80$ au, which is similar to the ISM value but different from the previous measurements of carbon isotope ratios of CO and HCN in the TW Hya disk, motivating the following scenario. First, element oxygen in gas-phase was depleted with respect to carbon, which promoted the isotope exchange reaction ([\[eq:CO\]](#eq:CO)). This produced $\rm ^{12}C^{+}$ which was eventually locked to dust grains, making the gas phase $\rm ^{13}C$-rich. The relatively $\rm ^{13}C$-poor CN isotopologue ratio could be explained by the in-situ reactions including reactions ([\[eq:CO\]](#eq:CO))-([\[eq:CN3\]](#eq:CN3)).

4.  $\rm ^{12}CN$/$\rm ^{13}CN$ tentatively shows a low value of $48^{+5}_{-4}$ at $r\sim 100$ au. This different in ratio can be explained due to the CN lines tracing different altitudes at different radii, where the isotope chemistry differs.

5.  This study highlights that different carbon-bearing species have different carbon isotope ratios in protoplanetary disk gas. Such isotope fractionation patterns would affect the isotope composition of the planetary system material.

We would like to acknowledge the anonymous referees for their helpful remarks and comments. We also thank to Dr. Kaori Kobayashi for helpful discussion on the spectroscopic data. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01375.S, 2018.A.00021.S, and 2017.1.01199.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. This research has made use of spectroscopic and collisional data from the EMAA database (<https://emaa.osug.fr> and <https://dx.doi.org/10.17178/EMAA>). EMAA is supported by the Observatoire des Sciences de l’Univers de Grenoble (OSUG)

This work was supported by Grant-in-Aid for JSPS Fellows, JP23KJ1008 (T.C.Y.). This work was partially supported by Overseas Travel Fund for Students (2022) of Department of Astronomical Science, The Graduate University for Advanced Studies, SOKENDAI. T.C.Y. was also supported by the ALMA Japan Research Grant of NAOJ ALMA Project, NAOJ-ALMA-306. H.N. is supported by JSPS KAKENHI grant numbers 18H05441, 19K03910, 20H00182. K.F. is supported by JSPS KAKENHI grant numbers 20H05847 and 21K13967. S.L. is supported by a Korea Astronomy and Space Science Institute grant funded by the Korean government (MSIT) (Project No. 2024-1-841-00). Support for C.J.L. was provided by NASA through the NASA Hubble Fellowship grant No. HST-HF2-51535.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555. CHR acknowledge the support of the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) Research Unit “Transition discs” - 325594231. CHR is grateful for support from the Max Planck Society.

# Facilities

ALMA

# Software

astropy (cite: astropy:2013; astropy:2018; astropy:2022), CASA (cite: mcmu07), emcee (cite: fore13), Keplerian_mask (cite: kepmask), SpectralRadex (cite: hold21), gofish (cite: teag16)

The corner plots of the resultant marginal posterior distribution at $r=56$ au and $101$ au are shown in Figure [6](#fig:c1) and [7](#fig:c2), respectively.

natexlab

(ref: aika18) Aikawa, Y., Furuya, K., Hincelin, U., & Herbst, E. 2018, ApJ, 855, 119, doi: [`10.3847/1538-4357/aaad6c`](http://doi.org/10.3847/1538-4357/aaad6c)

(ref: aika06) Aikawa, Y., & Nomura, H. 2006, ApJ, 642, 1152, doi: [`10.1086/501114`](http://doi.org/10.1086/501114)

(ref: andr18) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: astropy:2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, apj, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: barr06) Barrado Y Navascués, D. 2006, A&A, 459, 511, doi: [`10.1051/0004-6361:20065717`](http://doi.org/10.1051/0004-6361:20065717)

(ref: berg16) Bergin, E. A., Du, F., Cleeves, L. I., et al. 2016, ApJ, 831, 101, doi: [`10.3847/0004-637X/831/1/101`](http://doi.org/10.3847/0004-637X/831/1/101)

(ref: berg21) Bergner, J. B., Öberg, K. I., Guzmán, V. V., et al. 2021, ApJS, 257, 11, doi: [`10.3847/1538-4365/ac143a`](http://doi.org/10.3847/1538-4365/ac143a)

(ref: bosm21b) Bosman, A. D., Alarcón, F., Bergin, E. A., et al. 2021, ApJS, 257, 7, doi: [`10.3847/1538-4365/ac1435`](http://doi.org/10.3847/1538-4365/ac1435)

(ref: cala21) Calahan, J. K., Bergin, E., Zhang, K., et al. 2021, ApJ, 908, 8, doi: [`10.3847/1538-4357/abd255`](http://doi.org/10.3847/1538-4357/abd255)

(ref: cala23) Calahan, J. K., Bergin, E. A., Bosman, A. D., et al. 2023, Nature Astronomy, 7, 49, doi: [`10.1038/s41550-022-01831-8`](http://doi.org/10.1038/s41550-022-01831-8)

(ref: cazz18) Cazzoletti, P., van Dishoeck, E. F., Visser, R., Facchini, S., & Bruderer, S. 2018, A&A, 609, A93, doi: [`10.1051/0004-6361/201731457`](http://doi.org/10.1051/0004-6361/201731457)

(ref: clee15) Cleeves, L. I., Bergin, E. A., Qi, C., Adams, F. C., & Öberg, K. I. 2015, ApJ, 799, 204, doi: [`10.1088/0004-637X/799/2/204`](http://doi.org/10.1088/0004-637X/799/2/204)

(ref: dull02) Dullemond, C. P., van Zadelhoff, G. J., & Natta, A. 2002, A&A, 389, 464, doi: [`10.1051/0004-6361:20020608`](http://doi.org/10.1051/0004-6361:20020608)

(ref: endr16) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95, doi: [`10.1016/j.jms.2016.03.005`](http://doi.org/10.1016/j.jms.2016.03.005)

(ref: flow15) Flower, D. R., & Lique, F. 2015, MNRAS, 446, 1750, doi: [`10.1093/mnras/stu2231`](http://doi.org/10.1093/mnras/stu2231)

(ref: flow84) Flower, D. R., & Watt, G. D. 1984, MNRAS, 209, 25, doi: [`10.1093/mnras/209.1.25`](http://doi.org/10.1093/mnras/209.1.25)

(ref: flow85) —. 1985, MNRAS, 213, 991, doi: [`10.1093/mnras/213.4.991`](http://doi.org/10.1093/mnras/213.4.991)

(ref: fore13) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: furu22) Furuya, K., Lee, S., & Nomura, H. 2022, ApJ, 938, 29, doi: [`10.3847/1538-4357/ac9233`](http://doi.org/10.3847/1538-4357/ac9233)

(ref: gaia16) Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1, doi: [`10.1051/0004-6361/201629272`](http://doi.org/10.1051/0004-6361/201629272)

(ref: gaia21) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2021, A&A, 649, A1, doi: [`10.1051/0004-6361/202039657`](http://doi.org/10.1051/0004-6361/202039657)

(ref: hily17) Hily-Blant, P., Magalhaes, V., Kastner, J., et al. 2017, A&A, 603, L6, doi: [`10.1051/0004-6361/201730524`](http://doi.org/10.1051/0004-6361/201730524)

(ref: hily19) Hily-Blant, P., Magalhaes de Souza, V., Kastner, J., & Forveille, T. 2019, A&A, 632, L12, doi: [`10.1051/0004-6361/201936750`](http://doi.org/10.1051/0004-6361/201936750)

(ref: hold21) Holdship, J., Viti, S., Martı́n, S., et al. 2021, A&A, 654, A55, doi: [`10.1051/0004-6361/202141233`](http://doi.org/10.1051/0004-6361/202141233)

(ref: hsie15) Hsieh, T.-H., Lai, S.-P., Belloche, A., Wyrowski, F., & Hung, C.-L. 2015, ApJ, 802, 126, doi: [`10.1088/0004-637X/802/2/126`](http://doi.org/10.1088/0004-637X/802/2/126)

(ref: huan18_dsharp) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018a, ApJL, 869, L42, doi: [`10.3847/2041-8213/aaf740`](http://doi.org/10.3847/2041-8213/aaf740)

(ref: huan18) Huang, J., Andrews, S. M., Cleeves, L. I., et al. 2018b, ApJ, 852, 122, doi: [`10.3847/1538-4357/aaa1e7`](http://doi.org/10.3847/1538-4357/aaa1e7)

(ref: ilee22) Ilee, J. D., Walsh, C., Jennings, J., et al. 2022, MNRAS, 515, L23, doi: [`10.1093/mnrasl/slac048`](http://doi.org/10.1093/mnrasl/slac048)

(ref: kalu15) Kalugina, Y., & Lique, F. 2015, MNRAS, 446, L21, doi: [`10.1093/mnrasl/slu159`](http://doi.org/10.1093/mnrasl/slu159)

(ref: kama16a) Kama, M., Bruderer, S., Carney, M., et al. 2016, A&A, 588, A108, doi: [`10.1051/0004-6361/201526791`](http://doi.org/10.1051/0004-6361/201526791)

(ref: kast14) Kastner, J. H., Hily-Blant, P., Rodriguez, D. R., Punzi, K., & Forveille, T. 2014, ApJ, 793, 55, doi: [`10.1088/0004-637X/793/1/55`](http://doi.org/10.1088/0004-637X/793/1/55)

(ref: klis95) Klisch, E., Klaus, T., Belov, S. P., Winnewisser, G., & Herbst, E. 1995, A&A, 304, L5

(ref: krij20) Krijt, S., Bosman, A. D., Zhang, K., et al. 2020, ApJ, 899, 134, doi: [`10.3847/1538-4357/aba75d`](http://doi.org/10.3847/1538-4357/aba75d)

(ref: law21b) Law, C. J., Loomis, R. A., Teague, R., et al. 2021a, ApJS, 257, 3, doi: [`10.3847/1538-4365/ac1434`](http://doi.org/10.3847/1538-4365/ac1434)

(ref: law21) Law, C. J., Teague, R., Loomis, R. A., et al. 2021b, ApJS, 257, 4, doi: [`10.3847/1538-4365/ac1439`](http://doi.org/10.3847/1538-4365/ac1439)

(ref: lee21) Lee, S., Nomura, H., Furuya, K., & Lee, J.-E. 2021, ApJ, 908, 82, doi: [`10.3847/1538-4357/abd633`](http://doi.org/10.3847/1538-4357/abd633)

(ref: line21) Line, M. R., Brogi, M., Bean, J. L., et al. 2021, arXiv e-prints, arXiv:2110.14821. [`https://arxiv.org/abs/2110.14821`](https://arxiv.org/abs/2110.14821)

(ref: lois20) Loison, J.-C., Wakelam, V., Gratier, P., & Hickson, K. M. 2020, MNRAS, 498, 4663, doi: [`10.1093/mnras/staa2700`](http://doi.org/10.1093/mnras/staa2700)

(ref: loom18) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2018, AJ, 155, 182, doi: [`10.3847/1538-3881/aab604`](http://doi.org/10.3847/1538-3881/aab604)

(ref: maci21) Macı́as, E., Guerra-Alvarado, O., Carrasco-González, C., et al. 2021, A&A, 648, A33, doi: [`10.1051/0004-6361/202039812`](http://doi.org/10.1051/0004-6361/202039812)

(ref: mcmu07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mila05) Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005, ApJ, 634, 1126, doi: [`10.1086/497123`](http://doi.org/10.1086/497123)

(ref: muno23) Muñoz-Romero, C. E., Öberg, K. I., Law, C. J., et al. 2023, ApJ, 943, 35, doi: [`10.3847/1538-4357/aca765`](http://doi.org/10.3847/1538-4357/aca765)

(ref: mull05) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215, doi: [`10.1016/j.molstruc.2005.01.027`](http://doi.org/10.1016/j.molstruc.2005.01.027)

(ref: mull01) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49, doi: [`10.1051/0004-6361:20010367`](http://doi.org/10.1051/0004-6361:20010367)

(ref: mumm11) Mumma, M. J., & Charnley, S. B. 2011, ARA&A, 49, 471, doi: [`10.1146/annurev-astro-081309-130811`](http://doi.org/10.1146/annurev-astro-081309-130811)

(ref: nomu21) Nomura, H., Tsukagoshi, T., Kawabe, R., et al. 2021, ApJ, 914, 113, doi: [`10.3847/1538-4357/abfb6a`](http://doi.org/10.3847/1538-4357/abfb6a)

(ref: ober21maps) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1, doi: [`10.3847/1538-4365/ac1432`](http://doi.org/10.3847/1538-4365/ac1432)

(ref: oka01) Oka, T., Yamamoto, S., Iwata, M., et al. 2001, ApJ, 558, 176, doi: [`10.1086/321536`](http://doi.org/10.1086/321536)

(ref: pane22) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., et al. 2022, A&A, 666, A168, doi: [`10.1051/0004-6361/202142693`](http://doi.org/10.1051/0004-6361/202142693)

(ref: pasc23) Pascucci, I., Skinner, B. N., Deng, D., et al. 2023, ApJ, 953, 183, doi: [`10.3847/1538-4357/ace4bf`](http://doi.org/10.3847/1538-4357/ace4bf)

(ref: phuo21) Phuong, N. T., Dutrey, A., Chapillon, E., et al. 2021, A&A, 653, L5, doi: [`10.1051/0004-6361/202141881`](http://doi.org/10.1051/0004-6361/202141881)

(ref: scho05) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369, doi: [`10.1051/0004-6361:20041729`](http://doi.org/10.1051/0004-6361:20041729)

(ref: kepmask) Teague, R. 2020, richteague/keplerian_mask: Initial Release, 1.0, Zenodo, doi: [`10.5281/zenodo.4321137`](http://doi.org/10.5281/zenodo.4321137)

(ref: teag19) Teague, R., Bae, J., Huang, J., & Bergin, E. A. 2019, ApJL, 884, L56, doi: [`10.3847/2041-8213/ab4a83`](http://doi.org/10.3847/2041-8213/ab4a83)

(ref: teag20) Teague, R., & Loomis, R. 2020, ApJ, 899, 157, doi: [`10.3847/1538-4357/aba956`](http://doi.org/10.3847/1538-4357/aba956)

(ref: teag16) Teague, R., Guilloteau, S., Semenov, D., et al. 2016, A&A, 592, A49, doi: [`10.1051/0004-6361/201628550`](http://doi.org/10.1051/0004-6361/201628550)

(ref: teag22) Teague, R., Bae, J., Andrews, S. M., et al. 2022, ApJ, 936, 163, doi: [`10.3847/1538-4357/ac88ca`](http://doi.org/10.3847/1538-4357/ac88ca)

(ref: thom68) Thomson, R., & Dalby, F. W. 1968, Canadian Journal of Physics, 46, 2815, doi: [`10.1139/p68-652`](http://doi.org/10.1139/p68-652)

(ref: tsuk15) Tsukagoshi, T., Momose, M., Saito, M., et al. 2015, ApJL, 802, L7, doi: [`10.1088/2041-8205/802/1/L7`](http://doi.org/10.1088/2041-8205/802/1/L7)

(ref: tsuk16) Tsukagoshi, T., Nomura, H., Muto, T., et al. 2016, ApJL, 829, L35, doi: [`10.3847/2041-8205/829/2/L35`](http://doi.org/10.3847/2041-8205/829/2/L35)

(ref: tsuk22) —. 2022, ApJ, 928, 49, doi: [`10.3847/1538-4357/ac5111`](http://doi.org/10.3847/1538-4357/ac5111)

(ref: ueda20) Ueda, T., Kataoka, A., & Tsukagoshi, T. 2020, ApJ, 893, 125, doi: [`10.3847/1538-4357/ab8223`](http://doi.org/10.3847/1538-4357/ab8223)

(ref: vacc11) Vacca, W. D., & Sandell, G. 2011, ApJ, 732, 8, doi: [`10.1088/0004-637X/732/1/8`](http://doi.org/10.1088/0004-637X/732/1/8)

(ref: boek17) van Boekel, R., Henning, T., Menu, J., et al. 2017, ApJ, 837, 132, doi: [`10.3847/1538-4357/aa5d68`](http://doi.org/10.3847/1538-4357/aa5d68)

(ref: vand07) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: viss18) Visser, R., Bruderer, S., Cazzoletti, P., et al. 2018, A&A, 615, A75, doi: [`10.1051/0004-6361/201731898`](http://doi.org/10.1051/0004-6361/201731898)

(ref: wils99) Wilson, T. L. 1999, Reports on Progress in Physics, 62, 143, doi: [`10.1088/0034-4885/62/2/002`](http://doi.org/10.1088/0034-4885/62/2/002)

(ref: wood09) Woods, P. M., & Willacy, K. 2009, ApJ, 693, 1360, doi: [`10.1088/0004-637X/693/2/1360`](http://doi.org/10.1088/0004-637X/693/2/1360)

(ref: yosh22) Yoshida, T. C., Nomura, H., Furuya, K., Tsukagoshi, T., & Lee, S. 2022, ApJ, 932, 126, doi: [`10.3847/1538-4357/ac6efb`](http://doi.org/10.3847/1538-4357/ac6efb)

(ref: zhan17) Zhang, K., Bergin, E. A., Blake, G. A., Cleeves, L. I., & Schwarz, K. R. 2017, Nature Astronomy, 1, 0130, doi: [`10.1038/s41550-017-0130`](http://doi.org/10.1038/s41550-017-0130)

(ref: zhan20) Zhang, K., Schwarz, K. R., & Bergin, E. A. 2020, ApJL, 891, L17, doi: [`10.3847/2041-8213/ab7823`](http://doi.org/10.3847/2041-8213/ab7823)

(ref: yzha21a) Zhang, Y., Snellen, I. A., Bohn, A. J., et al. 2021a, Nature, 595, 370

(ref: ober11) Öberg, K. I., Murray-Clay, R., & Bergin, E. A. 2011, The Astrophysical Journal Letters, 743, L16, doi: [`10.1088/2041-8205/743/1/L16`](http://doi.org/10.1088/2041-8205/743/1/L16)

[^1]: <https://github.com/uclchem/SpectralRadex>

[^2]: <https://emaa.osug.fr>

</paper>

Write the methods card for this paper.