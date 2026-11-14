# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...687A.308S\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...687A.308S",
 "title": "Constraining the stellar masses and origin of the protostellar VLA 1623 system",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Sadavoy, Sarah I.",
 "n_authors": 9,
 "arxiv_id": "2406.12984",
 "doi": "10.1051/0004-6361/202348859",
 "alma_projects_linked_by_archive": [
  "2018.1.01089.S"
 ]
}
```

Paper text:
<paper>
# Constraining the stellar masses and origin of the protostellar VLA 1623 system

# Introduction

Stellar mass is perhaps the most fundamental stellar property. Nevertheless, measuring stellar masses for the youngest protostars remains difficult because these objects are deeply embedded in an infalling core and envelope and cannot be observed directly in optical or near-infrared wavelengths (cite: difran07; Tychoniec21). Detections of Keplerian rotation in the protostellar disks around protostars are paramount for constraining the stellar masses of these systems. Historically, Keplerian rotation has been difficult to detect (1) because bright molecular lines such as CO tend to become optically thick within the envelope, obscuring the disk, and (2) due to a lack of high-spatial resolutions needed to disentangle the disk from the envelope (cite: Ohashi97; Schreyer06; Jorgensen07prosac; Murillo13; vantHoff18).

The Atacama Large Millimeter/submillimeter Array (ALMA) can provide the high-resolution molecular line observations that are necessary to make detections of Keplerian rotation in young disks possible. Moreover, the significant improvements in sensitivity with ALMA have opened the possibility of observing fainter and optically thin isotopologues, which allows us to detect disks through the envelope (cite: Murillo13; Yen14; Ohashi14; Aso15; Ginsburg18; Reynolds21). ALMA is even capable of exploring deviations from pure Keplerian rotation that could be due to planets (cite: Pinte18; Pinte20; Teague19; Teague21), though primarily in older protoplanetary disks where the envelope is less of a confounding factor. Nevertheless, despite the improvements afforded by ALMA, well-constrained stellar masses have only been measured for a limited number of low-mass protostars to date (cite: Murillo13; Ohashi14; Aso17; Aso23; Ohashi23; Flores23; Thieme23).

VLA 1623 is in the $\rho$ Oph A star-forming region at 140 pc (cite: OrtizLeon18) and is one of the rare protostellar systems with detected Keplerian rotation. Specifically, VLA 1623 is the canonical Class 0 protostellar object (cite: Andre93) and a hierarchical multiple system, with sources VLA 1623A and VLA 1623B (separated by $\sim$ 140 au) located towards the centre of the core and VLA 1623W roughly 1500 au west of the pair[^1] (cite: BontempsAndre97; Looney00; MurilloLai13). VLA 1623A is itself a compact binary, with its Aa and Ab components separated by $\sim 14$ au (cite: Harris18) and surrounded by a large ($R \approx 180$ au) circumbinary disk (cite: Murillo13). Molecular line observations of the circumbinary disk show evidence of Keplerian rotation and yield a combined stellar mass of between 0.2 and 0.5 M$_{\odot}$ (cite: Murillo13; Hsieh20). Measuring the masses of the other stellar components, however, has been challenging due to confusion with the circumbinary disk and insufficient sensitivity to robustly detect and resolve the disks in gas tracers.

Constraining the stellar masses is an important step towards examining the origins of the VLA 1623 system. Observations suggest that the B and W components may be more evolved (non-coeval) due to a lack of outflow and the shape of their spectral energy distributions (SEDs), which imply a later evolutionary stage (cite: Murillo18). (cite: Harris18) examined the proper motion of the stars and propose that VLA 1623W may have been ejected. An ejection scenario could explain the lack of envelope detected towards VLA 1623W (cite: Michel22) as well as the large velocity streamers in the system (cite: Hsieh20; Mercimek23). Conversely, previous molecular line observations have been used to estimate the other stellar masses (cite: Ohashi22; Mercimek23), and those estimations, even if not concrete measurements, indicate that VLA 1623B and VLA 1623W may be relatively massive compared with VLA 1623A. If confirmed, these masses would pose difficulties for the ejection scenario (cite: Reipurth10).

Here we present new molecular line observations of C$^{17}$O (3 – 2) of the VLA 1623 system from ALMA. We used these data and radiative transfer models of rotating disks to constrain the stellar masses for the stellar components in VLA 1623. C$^{17}$O is a rarer species that is less optically thick within the envelope than the line tracers that have previously been observed, thereby making it easier for us to disentangle the Keplerian rotating disks of the protostars from each other. The paper is organized as follows: Section [2](#data) details the observations, Section [3](#results) shows that the C$^{17}$O traces the disk and the other lines trace outflows or infall, Section [4](#modeling) describes the radiative transfer models, Section [5](#discussion) discusses the stellar masses and the possible origins of the VLA 1623 system, and finally Section [6](#summary) gives our conclusions.

# Data

ALMA observed VLA 1623 in Band 7 on 20 and 22 April 2019 for project 2018.1.01089.S in the C-4 configuration with baselines of 15 m – 740 m. The phase calibrator was J1650-2943, and the flux/bandpass calibrator was J1924-2914 (20 April) and J1517-2422 (22 April). The data phase centre was at 16:26:26.35 -24:24:30.55, between VLA 1623A and VLA 1623B, meaning that VLA 1623W is outside of the primary beam full width at half maximum (FWHM)[^2]. The time on source was 52.74 minutes in total. The observations were set up with spectral windows on C$^{17}$O (3 – 2) at 337.061 GHz, H$^{13}$CO$^+$ (4 – 3) at 346.998 GHz, SO$_2$ ($8_{2,6}-7_{4,4}$) at 334.673 GHz, and H$^{13}$CN (4 – 3) and SO$_2$ ($13_{2,12}-12_{1,11}$) at 345.34 GHz. There was also one continuum window with a central frequency of 348.2227 GHz and bandwidth of 1.85 GHz.

We applied self-calibration to the continuum window and the three line windows using line-free channels. We used three rounds of phase-only self-calibration, starting with a shallow clean and a long solution interval and progressing to deeper cleans with shorter solution intervals. Due to the high ($> 1000$) source signal-to-noise ratio (S/N), we also used two rounds of phase and amplitude self-calibration using long integration times. We used solution intervals of 3 min, 60.6 s, and 30.3 s for the phase-only self-calibration and 3 min and 90.9 s for the amplitude and phase self-calibration. The clean depths for the five rounds were 0.92, 0.45, 0.20, 0.17, and 0.13 mJy beam$^{-1}$. The final continuum map including all line-free channels have a sensitivity of 95 $\mu$Jy beam$^{-1}$ at 341.8541 GHz for a beam of $0.3\ensuremath{''} \times 0.24\ensuremath{''}$ with Briggs weighting and $\mbox{\texttt{robust}}=-0.5$. The maximum recoverable scale for the data is 3.8$''$ using the 5th percentile baseline.

The self-calibration gain solutions were applied to each of the line spectral windows. We applied continuum subtraction using a fit order of 1. The final line cubes are made using `tclean` interactively with $\mbox{\texttt{robust}}=0.5$. Table [\[line_info\]](#line_info) gives the rest frequency, channel width, sensitivity per channel, and beam size for each detected line. For C$^{17}$O (3 – 2), we report the rest frequency of the main hyperfine component only. The H$^{13}$CN (4 – 3) and SO$_2$ (13$_{2,12}$ – 12$_{1,11}$) lines may be blended. Hereafter, we refer to these data as (blended) H$^{13}$CN to distinguish these data from the other detected lines. Table [\[line_info\]](#line_info) also lists the velocity range used to make all moment maps (unless a different range is specified).

| Transition | $\nu$ (GHz) | $\Delta v^a$ (km/s) | $\sigma$ (mJy beam$^{-1}$ per chan) | beam ($a \times b, \theta$) | $v_{range}^b$(km/s) |
|:---|:---|:---|:---|:---|:---|
| SO$_2$ ($8_{2,6}-7_{4,4}$) | 334.673 | 0.219 | 3.1 | $0.413\ensuremath{''} \times 0.336\ensuremath{''}, -84\degree$ | $2.8 - 4.8$ |
| C$^{17}$O (3 – 2) | 337.061 | 0.109 | 3.1 | $0.415\ensuremath{''} \times 0.337\ensuremath{''}, -87\degree$ | $1.0 - 6.5$ |
| SO$_2$ ($13_{2,12}-12_{1,11}$)$^c$ | 345.338 | 0.106 | 2.9 | $0.401\ensuremath{''} \times 0.329\ensuremath{''}, -86\degree$ | $2.3 - 5.5$ |
| H$^{13}$CN(4 – 3)$^c$ | 345.340 | $\cdots$ | $\cdots$ | $\cdots$ | $\cdots$ |
| H$^{13}$CO$^+$(4 – 3) | 346.998 | 0.106 | 3.1 | $0.402\ensuremath{''} \times 0.327\ensuremath{''}, -85\degree$ | $2.4 - 5.8$ |

$^a$ Channel width.

$^b$ Range of velocities used for the moment maps in Figure [2](#mom0).

$^c$ These two lines are blended.

# Results

## Overview

Figure [1](#b7_cont) shows the dust continuum data for VLA 1623 with the main components labelled. We recover the circumbinary disk around the protobinary, Aa and Ab, but we do not resolve the protobinary itself (labelled as A). Hereafter, we refer to the protobinary as VLA 1623A. The circumstellar disks for B and W are also labelled.

![](vla1623_b7_cont_log_plot.eps)

Figure [2](#mom0) shows the Moment 0 data for each line with contours of dust continuum. For the sake of clarity, the Moment 0 maps have not been primary-beam-corrected. C$^{17}$O and H$^{13}$CO$^+$ have extended emission, where both molecules trace the circumbinary disk and inner envelope around A and B. At the locations of the circumstellar disks for A and B, we see a relative deficit (absorption) in C$^{17}$O and H$^{13}$CO$^+$ that is consistent with the circumstellar disks shadowing the brighter circumbinary disk material or self-absorption (cite: Murillo13; Hara21). The circumstellar material is bright in SO$_2$ and (blended) H$^{13}$CN, and both lines also show compact emission within the circumbinary disk towards the south-west.

![](vla1623_line_mom0_plot.eps)

Finally, although faint, we also find hints ($\sim 2.5\sigma$) of the vertical streamer passing through VLA 1623W in C$^{17}$O (3 – 2) that matches what (cite: Mercimek23) found in C$^{18}$O (2 – 1) observations (labelled S in Figure [2](#mom0)). VLA 1623W is only detected in C$^{17}$O (see Section [3.3](#circumdisk)), with a system velocity of about 1.8 km s$^{-1}$. The system velocities of VLA 1623A and VLA 1623B are roughly 4 km s$^{-1}$ and 2.3 km s$^{-1}$, respectively.

## Outflows and infall

The C$^{17}$O data show a large X-shaped pattern centred on the VLA 1623A/B system (see Figure [2](#mom0)). Weaker emission along this pattern is also seen in SO$_2$ and (blended) H$^{13}$CN, indicating that this emission may be associated with the outflow and not the inner envelope. VLA 1623A has overlapping outflows with position angles of $\sim 125$ (cite: Murillo18gas; Hara21; Ohashi22) in good agreement with the orientation of the extended C$^{17}$O data. We find no C$^{17}$O gas within the outflow itself, however, suggesting that C$^{17}$O is tracing the outflow cavity walls only, likely due to higher densities in the walls over the outflow itself and higher temperatures leading to more sublimation of CO isotopologues. We note that (cite: Hsieh20) instead identify similar structures in C$^{18}$O (2 – 1) as gas streams in the envelope. To distinguish between these cases, Figure [3](#cavitywall) compares the C$^{17}$O integrated intensity data with contours of c-C$_3$H$_2$ at 217.8 GHz from (cite: Murillo18gas). Hydrocarbons like c-C$_3$H$_2$ are excellent tracers of outflow cavities (cite: Sakai14; Tychoniec21; Ohashi22). Broadly, we find good agreement between c-C$_3$H$_2$ and the X-shaped extended emission in C$^{17}$O, which is why we attribute this material to the outflow wall rather than a gas streamer.

![](vla1623_c17o_outflowC3H2_plot.eps)

Emission from SO$_2$ has also been associated with jets and outflows of protostellar sources (cite: Wakelam05; Feng20). Figure [4](#gradientBso2) shows the high velocity red- and blueshifted gas from SO$_2$ (8$_{2,6}$ – 7$_{4,4}$) for VLA 1623B (a similar trend is seen for the (blended) H$^{13}$CN data). Both line data show a gradient aligned with the disk minor axis, which matches expectations for high velocity material associated with the jet or outflow and not a rotating disk. Due to confusion with the circumbinary disk, we cannot identify a clear gradient for VLA 1623A.

Alternatively, the SO$_2$ emission could be tracing infalling gas rather than outflowing gas. (cite: Sakai14) find that sulfur-bearing species can trace the centrifugal barrier, a transition layer in disks with weak shocks due to infalling gas hitting the disk. In these cases the sulfur-bearing gas is confined near the disk (cite: Sakai17). (cite: Codella24) also find a large streamer extending south from VLA 1623B in C$^{18}$O (2-1) and several transitions of SO, which they interpret as an accretion flow. While we do not see this streamer in our SO$_2$ gas, it is detected faintly in the (blended) H$^{13}$CN data towards the southern part of the primary beam. Therefore, the SO$_2$ and (blended) H$^{13}$CN data may be tracing a mix of both infall and outflow.

![](vla1623b_cont_so2_mom1_plot.eps)

## Circumstellar disks

Circumstellar disks around protostars are often well detected using rare isotopologues of CO like C$^{17}$O (cite: Tychoniec21). While C$^{17}$O appears to trace the outflow cavity walls on larger scales (see Figure [3](#cavitywall)), we find that the high velocity gas towards the circumstellar disks have velocity gradients consistent with Keplerian rotation indicating that the compact emission indeed arises from the circumstellar disk.

Figure [5](#c17o_mom1) shows C$^{17}$O (3 – 2) Moment 1 maps of all three disks. To ensure a good signal-to-noise, we spectrally smoothed the data to 0.4 km s$^{-1}$ channels and we calculated the Moment 1 velocities using `immoments` in CASA with strict channel selections to avoid lower velocity gas that could be confused with emission outside of the disks. The velocity ranges used were $0.8-3.2$ km s$^{-1}$ and $5.6-7.2$ km s$^{-1}$ for VLA 1623A, $(-5.2)-(-2.4)$ km s$^{-1}$ and $6.8-9.6$ km s$^{-1}$ for VLA 1623B, and $(-2.0)-5.2$ km s$^{-1}$ for VLA 1623W. Moreover, we masked each map using thresholds in Moment 0 and dust continuum to isolate the Moment 1 data for each disk.

![image](vla1623_c17o_mom1_vla1623a.eps)\
![image](vla1623_c17o_mom1_vla1623b.eps)\
![image](vla1623_c17o_mom1_vla1623w.eps)

All three disks show blue-red gradients indicative of rotation. For VLA 1623A, the gradient is for the circumbinary disk as we lack the spatial resolution to resolve any gradients in the circumstellar disks of Aa and Ab. For VLA 1623B, the C$^{17}$O emission is complicated by gas emanating from the circumbinary disk (see Figure [2](#mom0)). Nevertheless, Figure [5](#c17o_mom1) shows that we can use high velocity (e.g. $> 4$ km s$^{-1}$ from the systemic velocity) C$^{17}$O emission to help isolate its circumstellar material. The velocity gradient seen in VLA 1623B aligns well with the major axis of the disk. (cite: Ohashi22) find a similar gradient in VLA 1623B with high-velocity CS (5 – 4) data. While they found that the CS data traced both the disk and outflows, the high velocity CS gas formed a gradient that was perpendicular to the outflow direction. Thus, we conclude that the high velocity C$^{17}$O (3 – 2) emission is similarly tracing rotation in the disk.

Figure [5](#c17o_mom1) also shows a clear velocity gradient for VLA 1623W going from the northern to the southern part of the disk along the major axis as expected with disk rotation. This gradient agrees well with the C$^{18}$O (2 – 1) gradient presented by (cite: Mercimek23). We lack sensitivity in the C$^{17}$O data to detect a velocity gradient in the streamers like Mercimek et al., but the broad centroid velocities of the two streamers in C$^{17}$O (3 – 2) match those seen in C$^{18}$O (2 – 1).

In the next section, we model the C$^{17}$O (3 – 2) emission using disk models with Keplerian rotation. Broadly, we found that the emission from the highest velocity channels (greatest deviation from the systemic velocity) follow a $r^{-0.5}$ profile, as expected for Keplerian rotation in disks. Nevertheless, other dynamical processes such as infall from the envelope or streamers can produce gradients. While such features can be tested using rotation curves (cite: Ohashi14; Aso15; Maret20), the disks are sufficiently resolved or confused with circumbinary material such that the centroid position becomes unreliable. For simplicity with our modelling, we assumed that the C$^{17}$O (3 – 2) emission solely traces the rotationally supported disks and that any potential contributions from the surrounding envelope or gas streamers are negligible. To ensure this assumption is appropriate, we employed velocity cuts similar to Figure [5](#c17o_mom1) to exclude the low-velocity emission that could be dominated by these components (see Section [4](#modeling) for details).

# Modelling

We modelled the C$^{17}$O (3 – 2) data for VLA 1623A, VLA 1623B and VLA 1623W using the `pdspy` code, which fits Keplerian rotating disk models to spectral line datasets directly in the $uv$ plane (cite: Sheehan19). `pdspy` uses radiative transfer codes and Bayesian sampling to identify a best-fit disk model and the full posterior distributions for the parameters given a set of observations. Full details of how the code works can be found in (cite: SheehanEisner18), but we describe the technique briefly here, including any differences from what has previously been documented. In short, `pdspy` generates a 2D axisymmetric model of a protostellar disk. The surface density is described by a power-law function, $$\begin{equation}
    \Sigma = \Sigma_0 \left(\frac{R}{R_{disk}}\right)^{-\gamma},
\end{equation}$$ where $\Sigma_0$ is the surface density normalization, $R$ is the radial distance from the star in cylindrical coordinates, $R_{disk}$ is the radius where the disk is truncated, and $\gamma$ is the surface density power-law exponent. For VLA 1623B and VLA 1623W, we fixed $R_{in}$, the inner radius where the disk is truncated, to 0.1 au. As VLA 1623A is a close separation binary with evidence of a cavity (cite: Harris18), we left $R_{in}$ as a free parameter. Rather than fitting for $\Sigma_0$, we instead integrated the surface density to calculate the total (gas and dust) mass, $M_{disk}$, and used that as a free parameter in our fits. We assumed the temperature follows a power law profile in radius, $T(R) = T_0 \left(R \, / \, 1\  \mathrm{au}\right)^{-q}$, and that the disk is vertically isothermal. The scale height of the disk as a function of radius could then be derived from the temperature at a given radius and the equations of hydrostatic equilibrium, and similarly the volume density follows from the surface density and scale height. We modelled the C$^{17}$O (3 – 2) emission (no dust) assuming a constant C$^{17}$O abundance with a factor of 1/2240 relative to CO and a fixed CO abundance of $10^{-4}$ relative to molecular hydrogen (cite: Czekala15). We also adopted a constant turbulent velocity, $a_{turb}$, throughout the disk but leave its value as a free parameter. `pdspy` then uses the radiative transfer modelling code `RADMC-3D` and ray tracing to generate synthetic channel maps of the model disk with a given inclination ($i$) and position angle (p.a.), and then Fourier transforms the synthetic channel maps into the $uv$ plane using the `galario` code (cite: Tazzari18). This last step ensures that the synthetic model data match the spatial scales covered by the observations. We note that the position angle is defined based on the direction of the angular momentum vector of the disk, east of north, following (cite: Czekala15).

The model parameter values as well as the source system velocity, $v_{sys}$, and location in the field ($x_0$, $y_0$) are optimized to the observations. Unlike in (cite: Sheehan19), we use the `dynesty` code (cite: Speagle20) instead of a Monte Carlo Markov chain (MCMC) to find the best-fit values. `dynesty` uses nested sampling to integrate the likelihood function and calculate the Bayesian evidence and the posteriors for each parameter. We opted to use `dynesty` here because we find nested sampling to be more robust with multi-modal posteriors and it also has well-defined stopping criteria.

Since the C$^{17}$O (3 – 2) observations include emission from VLA 1623A, B, and W, we applied additional constraints on the model and data to ensure that we fit each source separately. First, we provided `pdspy` with relatively strict priors on the location of the source and allowed that position to vary minimally (by $< \pm 0.3\ensuremath{''}$ in either direction) so that the code is forced to fit the emission from the target of interest. Second, we restricted the channels and $uv$ ranges to select emission where the target source is dominant or at least clearly separable from all other sources as well as from the envelope and outflows. For the channel restrictions, we excluded velocities between 3.25 and 5.5 km s$^{-1}$ from the fit to A and between -2.5 and 6.75 km s$^{-1}$ from the fit to B. For the $uv$ restriction, we excluded baselines with $uv <100$ k$\lambda$ ($\gtrsim2\ensuremath{''}$) for B and $uv <200$ k$\lambda$ ($\gtrsim1\ensuremath{''}$) for W. The $uv$ cuts are less severe for B because there is less extended emission in the vicinity of B once the channel cuts previously described are taken into account. For VLA 1623A, we are fitting the extended circumbinary disk and as such, the velocity channel cuts are sufficient to exclude the envelope-scale without additional restrictions in the $uv$ range. To ensure that these choices do not affect the fit quality, we carefully check the results of the models.

Table [1](#table:best_fits) lists the best-fit model parameters for VLA 1623A, B and W. The best-fit values are determined from the maximum likelihood models from the posterior and the uncertainties are calculated as the range around the best-fit values that include 68% of the posterior samples. We also added a 10% uncertainty in quadrature to most parameters to represent additional uncertainties on those values imparted by systematic errors in, for example, flux calibration and source distance. We excluded this additional uncertainty from $x_0$, $y_0$, $i$, $p.a.$, and $v_{sys}$ as they are primarily geometric and are therefore less likely to be impacted by the aforementioned systematics. There may be additional systematic effects such as the choice of model that lead to larger errors on the measured values than those presented here (cite: Premnath20). We further note that several of the best-fit parameters are not well constrained or have unusually low or high values. For example, some of the best-fit models have very low power-law exponents for $q$ and $\gamma$, implying flat profiles for temperature or surface density. We caution against over-interpreting the value of these disk parameters given that we had to impose strict velocity and $uv$ limits. These cuts will limit the spatial extent of the disk, which will affect our ability to constrain the radial profiles (e.g. power-law indices). We focus instead on the results for the stellar mass, which we can reasonably constrain with the high-velocity gas, but we present the best-fit values for the other disk parameters for completeness.

| Parameters | A | B | W |
|:---|:--:|:--:|:--:|
| $M_{*}$ (M$_{\odot}$) | $0.27^{+0.03}_{-0.03}$ | $1.9^{+0.3}_{-0.2}$ | $0.64^{+0.06}_{-0.06}$ |
| $M_{disk}$ ($10^{-3}$ M$_{\odot}$) | $54^{+5}_{-5}$ | $>1$ | $1.7^{+0.2}_{-0.2}$ |
| $R_{in}$ (au) | $48^{+5}_{-5}$ | 0.1 | 0.1 |
| $R_{disk}$ (au) | $316^{+32}_{-32}$ | $43^{+5}_{-5}$ | $108^{+11}_{-11}$ |
| $\gamma$ | $2.0^{+0.2}_{-0.2}$ | $0.1^{+1.0}_{-0.5}$ | $0.1^{+0.1}_{-0.1}$ |
| $T_0$ (K) | $148^{+15}_{-25}$ | $34^{+56}_{-9}$ | $898^{+116}_{-173}$ |
| $q$ | $0.38^{+0.04}_{-0.05}$ | $0.06^{+0.26}_{-0.05}$ | $0.83^{+0.09}_{-0.10}$ |
| $a_{turb}$ (km s$^{-1}$) | $0.68^{+0.07}_{-0.07}$ | $0.19^{+0.24}_{-0.08}$ | $0.56^{+0.07}_{-0.07}$ |
| $i$ ($^{\circ}$) | $58.9^{+0.6}_{-0.3}$ | $91^{+16}_{-2}$ | $74.8^{+0.5}_{-0.5}$ |
| p.a. ($^{\circ}$) | $296.27^{+0.01}_{-0.12}$ | $136^{+1}_{-2}$ | $281.1^{+0.4}_{-0.5}$ |
| $v_{sys}$ (km s$^{-1}$) | $3.998^{+0.002}_{-0.002}$ | $2.31^{+0.09}_{-0.09}$ | $1.75^{+0.02}_{-0.01}$ |
| $x_0$ (mas) | $-39.4^{+1.3}_{-0.7}$ | $52^{+7}_{-6}$ | $-82^{+3}_{-3}$ |
| $y_0$ (mas) | $-90.3^{+1.1}_{-0.8}$ | $-23^{+5}_{-5}$ | $-11^{+3}_{-3}$ |

: Best-fit Model Parameters

Note: An additional 10% uncertainty has been added in quadrature to the best-fit values for all parameters except $i$, $p.a.$, $v_{sys}$, $x_0$, and $y_0$ (see text for details).

Figures [6](#fig:vla1623a-best-fit-channels), [7](#fig:vla1623b-best-fit-channels), and [8](#fig:vla1623w-best-fit-channels) compare the channel maps from the observations with the synthetic channel maps of the best-fit model to demonstrate the fit quality for each source. We find that the models fit the data well, with little or no contours above the $5\sigma$ level appearing in the residual channel maps associated with the target disk. Emission that exceeds $5\sigma$ in the residuals generally arises from structures not included in the model but are present in the field of view. For example, Figure [7](#fig:vla1623b-best-fit-channels) shows significant redshifted residual emission above the 5$\sigma$ level in the channel maps of VLA 1623B, but this residual emission comes from the circumbinary disk, which is not included in the model of VLA 1623B. This broad agreement between the observations and the model indicates that our simple model of Keplerian rotation was indeed reasonable and that other dynamical processes such as infall are either negligible or limited to larger scales than that of the disk.

![](VLA1623A_C17O3-2_short.pdf)

![](VLA1623B_C17O3-2_short_with_cuts.pdf)

![](VLA1623W_C17O3-2_short_with_cuts.pdf)

Figure [9](#fig:pvdiagram-best-fits) compares the observed position-velocity data along the disk major axis (background colour) with the synthetic position-velocity data (contours) from the best-fit models of VLA 1623A, B, and W. Though position-velocity diagrams represent a reduction of the dimensionality of the data, they can be a useful tool for by-eye comparison with Keplerian rotation. Figure [9](#fig:pvdiagram-best-fits) shows simple Keplerian rotation curves for fixed stellar masses to demonstrate that the masses derived from our fitting are consistent with what might be obtained from such a simple comparison.

![image](VLA1623A_C17O3-2_pvdiagram.pdf) ![image](VLA1623B_C17O3-2_pvdiagram.pdf) ![image](VLA1623W_C17O3-2_pvdiagram.pdf)

# Discussion

## Stellar masses

Previously, Keplerian rotation modelling had only been done for VLA 1623A. (cite: Murillo13) determine a (combined) stellar mass of $M_\star \sim 0.2$ M$_{\odot}$ using models of Keplerian rotation with infall and early (Cycle 0) ALMA C$^{18}$O (2 – 1) data. With more sensitive data, (cite: Hsieh20) measure a combined stellar mass of $M_\star \sim 0.3-0.5$ M$_{\odot}$ for VLA 1623A. In both cases, the mass values for VLA 1623A are a total mass for the tight binary, VLA 1623Aa and VLA 1623Ab (cite: Harris18). The remaining stellar components, VLA 1623W and VLA 1623B, have estimated masses from the velocity gradient assuming Keplerian rotation, rather than fitting the Keplerian motion itself. For VLA 1623B, (cite: Ohashi22) measure a mass of $M_{\star} \lesssim 1.7$ M$_{\odot}$ from CS (5 – 4) data with $v_{rot} = 7.8$ km s$^{-1}$ at $R = 27$ au, and for VLA 1623W, (cite: Mercimek23) estimate a mass of $M_{\star} \approx 0.45$ M$_{\odot}$ from C$^{18}$O (2 – 1) data with $v_{rot} \approx 3$ km s$^{-1}$ at $R \approx 50$ au.

Broadly, our measured stellar masses from the radiative transfer models agree well with the previously inferred dynamical masses. We find best-fit stellar masses of $M_\star = 0.64 \pm 0.06$ M$_{\odot}$ for VLA 1623W and $M_\star = 1.9^{+0.3}_{-0.2}$ M$_{\odot}$ for VLA 1623B, and a combined stellar mass of $M_\star = 0.27 \pm 0.03$ for VLA 1623A (see Table [1](#table:best_fits)). Since these masses are measured from C$^{17}$O (3 – 2), we have a rarer isotopologue of carbon monoxide than C$^{18}$O and less confusion with the infalling envelope and streamers (cite: Murillo13; Mercimek23). Moreover, our modelling process fits the full 3D (position, position, velocity) dataset with physically motivated models rather than estimating the mass from the peak line emission in a few channels at a radius offset from the disk centre. In addition, `pdspy` fits visibility data. The visibility plane encodes information at several times smaller spatial scales than is recovered by deconvolution (cite: Jennings20), and as such we are not limited by the beam resolution and can better constrain the models on sub-beam scales.

These measurements put constraints on the stellar masses for all the components (with VLA 1623A combined) and indicate a hierarchy. VLA 1623B has the highest mass, with more than twice the mass of the other two stellar components combined. VLA 1623W is second in mass with VLA 1623A in third. These more accurate stellar masses yield valuable insights into the physical conditions of VLA 1623, and its formation and evolution. We discuss individual scenarios in Section [5.2](#sec:origin).

## Origin of the VLA 1623 system

The detection of Keplerian rotation towards both VLA 1623W and VLA 1623B indicates that these sources are genuine protostars (cite: Ohashi22; Mercimek23). Nevertheless, the VLA 1623 system is a complex environment and its origin is not straightforward. Here, we consider different scenarios to explain the formation and evolution of VLA 1623.

### Dynamical interactions

One theory to explain the VLA 1623 system is that VLA 1623W was ejected. An ejection scenario has been proposed because the proper motions of VLA 1623W indicate that it points back to the VLA 1623A/B protostars (cite: Harris18). A dynamical interaction could also explain the counter-rotating disks between VLA 1623A and VLA 1623B (cite: Takaishi21; Ohashi22), the lack of envelope emission around VLA 1623W, and the large gas streamers (cite: Murillo13; Mercimek23).

Nevertheless, there are challenges to explaining VLA 1623W as an ejected object. First, multi-body interactions generally result in the ejection of the lowest-mass object (cite: Reipurth10). From our stellar mass measurements, VLA 1623A has the lowest mass by more than a factor of two even if the circumbinary disk is included. Second, a dynamical interaction leading to ejection is expected to produce a spiral structure in the circumbinary disk (cite: Takaishi21), which is not observed, although a spiral structure caused by dynamical interactions could dissipate quickly (cite: Cuello22). Third, VLA 1623W does not appear to get close enough to VLA 1623A/B for a dynamical ejection to be likely. In Appendix [7](#app_proper), we extrapolate the proper motion of VLA 1623W and VLA 1623B back in time to find a closest plane-of-sky encounter of about 650 au. (cite: Reipurth10) simulated dynamical interactions of triple systems of protostars in dense cores at separations between 50 au and 400 au and found that ejections were weaker and less common at 400 au than at 50 au (cite: Cuello22). Our analysis shows that the closest separation only becomes $< 100$ au at the 6th percentile, whereas the closest separation is $\gtrsim 400$ au at the 25th percentile (see Appendix [7](#app_proper)). For such wide projected separations, we would expect that the stars would be too distant to have a substantial gravitational effect on their relative orbits (cite: SadavoyStahler17). As a result, a dynamical ejection scenario appears unlikely to explain the VLA 1623 system.

### Chance alignment

Since VLA 1623W has a different system velocity relative to VLA 1623A and B, it may be an unrelated young stellar object (YSO) that happens to have a chance alignment with the VLA 1623A/B system. (cite: MurilloLai13) identify VLA 1623 as having non-coeval YSO components based on their SEDs (cite: Murillo18). VLA 1623W also lacks envelope emission and an outflow (cite: Murillo13; Santangelo15; Hara21), which could indicate that it is a more evolved YSO that formed separately.

Following (cite: Tobin22), we estimated the probability that VLA 1623W is a companion source using Bayes theorem, $$\begin{equation}
    P(c|d) = \frac{P(d|c)P(c)}{P(d)}
,
\end{equation}$$ where $P(d|c)$ is the probability we would detect a true companion source, $P(c)$ is the probability of having a companion at a given separation, and $P(d)$ is the probability of a detection of any YSO. We adopted $P(d|c) = 0.75$, similar to (cite: Tobin22). (cite: Tobin22) measured their companion detection probability based on a dust mass sensitivity of $\sim 1$ M$_\oplus$ for dusty disks. Since we have higher sensitivity observations of $\sim 0.01$ M$_\oplus$ for source detection (cite: Sadavoy19), our adopted value of $P(d|c)$ should be considered a lower limit. We also used $P(c) = 0.2$ from (cite: Tobin22), which is based on companion statistics from Perseus and Orion for a separations $\lesssim 1000$ au. Finally, we calculated the probability of having a detection, $P(d)$, with $$\begin{equation}
    P(d) = 0.75P(c) + \left[1 - e^{-0.75\Sigma\pi r^2}\right]\left[1 - 0.75P(c)\right]\label{eq.Pd}
,
\end{equation}$$ where $\Sigma$ is the stellar surface density and $r$ is the separation being considered. Equation [\[eq.Pd\]](#eq.Pd) gives the probability of detecting any source at the observed sensitivity. The first term is the likelihood of detecting a true companion, assuming 75% are detectable at our sensitivity, and the second term is the likelihood of detecting an unrelated source in a specified area for a given YSO stellar density (cite: Tobin22). We used $r = 10\ensuremath{''}$ for the area. To estimate the YSO stellar density, we calculated the 11th nearest neighbour at the position of VLA 1623 from the *Gaia*-corrected YSO catalogue of (cite: Grasser21). The 11th nearest neighbour gives $\Sigma_{11} = 1470$ YSO pc$^{-2}$. This stellar density is slightly below the peak YSO stellar density for L1688 of 2000 YSOs pc$^{-2}$ from (cite: Gutermuth09), but VLA 1623 is located off the cluster centre and so the 11th nearest neighbour should be more representative.

With our assumed values, we calculate a probability that VLA 1623W is a companion protostar of VLA 1623 of $P(c|d) = 0.55$, which suggests that VLA 1623W has nearly equal chances to being a member or an unrelated YSO. Nevertheless, this probability of 55% is likely a lower limit. First, VLA 1623W appears protostellar in nature (see Section [5.2.3](#dis:insitu)), and the stellar surface densities from both (cite: Gutermuth09) and (cite: Grasser21) are dominated by Class II sources. Since protostars (embedded YSOs) are less common than Class II YSOs (cite: Gutermuth09; Dunham15), the probability that VLA 1623W is a companion object should be higher than our current estimate. Second, the streamers towards VLA 1623W indicate that it is interacting with the dense core itself and therefore is likely within the dense core and not completely unrelated to the VLA 1623 system. These factors increase the likelihood that VLA 1623W is a true companion source, so we consider VLA 1623W to be a member YSO.

### In situ formation

Here, we define objects that formed out of the same natal core environment as forming in situ. In general, there are two main mechanisms that have been proposed to produce multiple stellar systems: disk fragmentation and turbulent fragmentation (cite: Offner23). Briefly, disk fragmentation occurs when a circumstellar disk becomes unstable to gravity and fragments to form additional stars, primarily at small ($\lesssim 100$ au) separations (cite: Bonnell94; Kratter10). Turbulent fragmentation occurs when density perturbations within the natal dense core become massive enough for self-gravity, allowing them to collapse and form independent objects at a wide range of separations (cite: Offner10; Offner16; Kuffmeier19). Although the separation distributions can broadly indicate the formation mechanism, simulations show that wide binary systems can shrink to smaller orbits on timescales of $\lesssim 0.1$ Myr (cite: Offner12), which is less than the protostellar lifetime. As a result, differences in angular momentum vectors may be more illuminating, as disk fragmentation predicts aligned vectors and turbulent fragmentation implies random vectors (cite: Offner23).

VLA 1623A and VLA 1623B have a projected separation of roughly 200 au, whereas VLA 1623W is over 1000 au away from the pair. The wide separation for VLA 1623W would indicate that it formed via turbulent fragmentation, but from separation alone, it is difficult to conclude the origins of A or B, especially given the size of the circumbinary disk. Nevertheless, VLA 1623A and VLA 1623B have misaligned velocity gradients indicative of counter-rotation (cite: Ohashi22) and the disk inclinations and positions angles do not agree as well (see Table [1](#table:best_fits)). Both of these factors are consistent with turbulent fragmentation. Moreover, since VLA 1623B is more massive than VLA 1623A and its circumbinary disk, it seems unlikely that it was formed via disk fragmentation and then was later perturbed through dynamical interactions to have a misaligned rotation axis.

Turbulent fragmentation does not require that all stellar components formed at the same time. (cite: MurilloLai13) and (cite: Murillo18) compared the SEDs and circumstellar material for the VLA 1623 components and concluded that VLA 1623W appeared more evolved than VLA 1623A and VLA 1623B. Indeed, there is a strong, collimated outflow coming from the VLA 1623A/B system, whereas VLA 1623W has no detected outflows or envelope (cite: Murillo13; Santangelo15; Hara21; Michel22), in agreement with this protostar being older. Thus, VLA 1623W may have formed first through turbulent fragmentation and then VLA 1623A/B formed later.

Although the protostars in VLA 1623 may not be entirely coeval, this does not mean that VLA 1623W must be an evolved YSO (e.g. Flat or pre-main sequence). First, VLA 1623W is detected in C$^{18}$O (cite: Mercimek23) and C$^{17}$O. Protostellar disks are generally warmer, which favour the detection of rare isotopologues in the gas phase, and these disks also tend to be more massive and optically thick, which will shield the molecules from being selectively photo-dissociated as seen in older protoplanetary disks (cite: Miotello17; vantHoff18; Zhang20; ArturV19). Some protoplanetary disks have been detected in C$^{17}$O (cite: Zhang21), but these observations are generally towards the inner radii, whereas we detect C$^{17}$O towards the entire disk of VLA 1623W (e.g. beyond the dust disk; see Figure [5](#c17o_mom1)). Younger protostars tend to be brighter with warmer disks, which means that rare CO isotopologues will be detected in the gas phase out to larger radii (cite: vantHoff18). Second, VLA 1623W appears to be flared at 0.87 mm and 1.3 mm (cite: Michel22), indicating that larger dust grains have not yet had time to settle to the midplane. Protoplanetary disks tend to be geometrically thin at those wavelengths (cite: Villenave20), whereas flaring has been detected towards some protostellar disks (cite: Sheehan22_l1527; Ohashi23). Finally, VLA 1623W is an optically thick, relatively massive disk (cite: Harris18; Sadavoy19; Michel22), and disk mass tends to decrease with evolutionary stage for a given star-forming region (cite: Tobin20). Table [1](#table:best_fits) gives an equivalent disk dust mass of 6 M$_{\oplus}$, assuming a gas-to-dust mass ratio of 100. This dust mass places VLA 1623W in the upper half of disk masses from the Ophiuchus disk survey, ODISEA, and is consistent with Class I (or Flat) disks (cite: Williams19). Although there are more massive disks around evolved YSOs in other clouds, the ODISEA survey shows that disk masses in Ophiuchus tend to be lower than other nearby systems, making the mass of VLA 1623W significant relative to the other Ophiuchus disks.

Even though it has a youthful disk, VLA 1623W lacks an envelope component typical of protostellar sources. Since VLA 1623W is located along the collimated outflow axis (in projection), its envelope could have been stripped (cite: deGouveia05; Ladd11). In this case, we would observe a less embedded SED and the protostar would have less accretion to drive an outflow. Currently, there is no evidence of shocked gas towards VLA 1623W (e.g. it is not detected in SO$_2$), although we could lack the sensitivity. While we cannot clearly classify VLA 1623W given the uncertainties from its SED and challenges with its high disk inclination, we believe that VLA 1623W is more likely to be a protostellar source and less likely to be a more evolved (e.g. Class II) object.

For the origin of the VLA 1623 protostellar system, we propose that the main stellar components, VLA 1623A, VLA 1623B, and VLA 1623W, formed via turbulent fragmentation, whereas the tight VLA 1623A binary system (Aa and Ab) at the centre of a large circumbinary disk may have formed via disk fragmentation given their small separation, although we cannot rule out that all the stellar components formed via core fragmentation and migrated. A full origin picture must account for the wide range of stellar masses for each of the stars, explain why the circumbinary disk formed around the lowest-mass stellar companion, and determine the stability of the stellar system and the circumbinary disk.

## VLA 1623 stability

In this section, we consider the gravitationally stability of the protostellar disks and the VLA 1623 system. For disk stability, we used the disk-to-star mass ratio to assess the gravitational stability of the circumstellar and circumbinary disks. Systems with low disk-to-star mass ratios should be more stable to fragmentation, whereas higher ratios would be unstable (cite: Vorobyov10). (cite: MercerStamatellos20) find that typical ratios of $\gtrsim 30\%$ favour fragmentation in disks based on a sample of low-mass stars. This cutoff matches what is seen in the L1448 IRS3 system, where the fragmenting circumbinary disk of L1448 IRS3B has a large disk-to-star mass ratio of 25% and the gravitationally stable disk around L1448 IRS3A has a smaller disk-to-star mass ratio of 3% (cite: Reynolds21). Gravitational stability in L1448 IRS3 was independently assessed using a Toomre Q analysis and the presence or absence of spiral structures and fragments in the disks themselves (cite: Tobin16l1448; Reynolds21).

From our best-fit models in Table [1](#table:best_fits), we calculate ratios of $M_{disk}/M_\star \approx 20$% for the circumbinary disk around VLA 1623A and $M_{disk}/M_\star \approx 0.3$% for both VLA 1623B and VLA 1623W. These results imply that the stellar disks are likely stable under their own self-gravity, even with the uncertainties on the disk masses from the models. The circumbinary disk, however, has an intermediate ratio, which could indicate that it is close to being unstable and may undergo fragmentation in the future. Nevertheless, there is no evidence of ongoing spiral structure or fragmentation in the circumbinary disk (cite: Sadavoy18b; Harris18), both of which are considered signposts of gravitational instabilities (cite: Kratter10) and are detected in L1448 IRS3B (cite: Tobin16l1448). We cannot rule out that the circumbinary disk fragmented in the past (e.g. to form the tight VLA 1623Aa and VLA 1623Ab binary) and has since reached a more stable point.

In the case of the circumbinary disk, spiral structure could also arise due to dynamical interactions with its close companion, VLA 1623B, rather than gravitational instabilities. It is interesting that we see no evidence of perturbations in the circumbinary disk given the close (in projection) separation between VLA 1623A and VLA 1623B. Specifically, VLA 1623B is the most massive YSO in the system (e.g. its stellar mass exceeds the estimated combined mass of VLA 1623A and the circumbinary disk by a factor of six) and the projected separation of VLA 1623A and VLA 1623B is approximately equal to the minimum value given their disk sizes. The circumbinary disk, however, is well fit by an isolated disk model with no significant residuals indicating deviations from Keplerian rotation. Moreover, both disks have low gas temperatures (cite: Murillo18gas), which suggest no dynamical interactions or perturbations are taking place. Both factors imply that VLA 1623B may have a large line-of-sight separation and is not physically close enough to VLA 1623A to perturb or heat the gas in the circumbinary disk. A large line-of-sight separation could also indicate that VLA 1623B is an unrelated YSO, but given their close separation in projection, they are more likely to be true companion. Using the same probability definitions as Section [5.2.2](#dis:chance), we find $P(c|d) = 0.95$ for VLA 1623A and VLA 1623B to be companion YSOs, assuming $P(c) = 0.14$ for separations $<500$ au (cite: Tobin22) and a distance of $r = 1.5\ensuremath{''}$. With such a high probability, VLA 1623B should be considered a companion protostar.

Finally, we considered whether VLA 1623W is itself gravitationally bound to the VLA 1623A/B YSOs, assuming it is a true companion source (see Section [5.2.2](#dis:chance)). For simplicity, we ignored any contributions from the surrounding dense core, and calculated the potential energy between VLA 1623W and VLA 1623A/B using the star and disk masses in Table [1](#table:best_fits) and a projected separation of $r=10$$''$, and we calculated a kinetic energy based on the relative 3D motions of the A/B and W from their system velocities (assuming 3 km s$^{-1}$ for A/B and 1.75 km s$^{-1}$ for W) and proper motions (see also Appendix [7](#app_proper)). The resulting energies are $\Omega = -GM_{AB}M_W/r \approx -0.2 \times 10^{37}$ J for the gravitational energy and $K = \frac{1}{2}M_W\sigma_{3D}^2 \approx 1 \times 10^{37}$ J for the kinetic energy. These back-of-the-envelope calculations imply that the turbulent kinetic energy is roughly a factor of five larger than the gravitational energy from the YSOs alone. Moreover, the calculated gravitational energy is an upper limit, since we only have a projected separation between VLA 1623A/B and VLA 1623W, and the true 3D distance could be much larger. Thus, the kinetic energy appears several times larger than the gravitational energy, indicating that VLA 1623W is unlikely to be bound to the VLA 1623A/B system and could disperse, although the source may still be bound to the dense core.

# Conclusions

We present new ALMA molecular line observations of the VLA 1623 system. We primarily focused on C$^{17}$O (3 – 2) observations, which trace the disks of the protostars and show velocity gradients consistent with Keplerian rotation. We used the radiative transfer modelling code `pdspy` to model the C$^{17}$O (3 – 2) emission for VLA 1623A, VLA 1623B, and VLA 1623W, obtaining constraints for their stellar masses. Our main conclusions are:

1.  We measure stellar masses of 0.27 M$_{\odot}$, 1.9 M$_{\odot}$, and 0.64 M$_{\odot}$ for VLA 1623A (Aa and Ab combined), VLA 1623B, and VLA 1623W, respectively. These masses are in good agreement with previous estimates that used different tracers and techniques.

2.  Based on the new mass measurements and an analysis of the proper motion of the stars, we disfavour a scenario where VLA 1623W was ejected from the central core.

3.  Following (cite: Tobin22), we estimate a probability of VLA 1623W being a companion source of nearly 55%, which means we cannot rule out that it is an unrelated YSO along the line of sight. Nevertheless, based on the apparent youth of the disk and the presence of gas streamers connecting VLA 1623W to the VLA 1623A/B protostars, we favour it being a genuine companion source.

4.  We propose a scenario where VLA 1623A, VLA 1623B, and VLA 1623W formed initially from turbulent fragmentation, although VLA 1623A may have undergone disk fragmentation to produce the tight binary, Aa and Ab. The protostars may not be entirely coeval with each other, but differences in age should not exceed the protostellar lifetime.

5.  The disks around VLA 1623B and VLA 1623W appear gravitationally stable based on very low disk-to-star mass fractions. The circumbinary disk has an intermediate fraction of 20%, which could indicate instability and future fragmentation. Nevertheless, we see no evidence of spiral structure in the circumbinary disk, either from gravitational instability or dynamical interactions.

We also find that VLA 1623W appears to be unbound to the other protostars, suggesting that it may disperse. As such, these observations represent a rare snapshot in time of a multiple-protostellar system prior to its diffusion or strong dynamical interactions. While the presence of streamers towards VLA 1623W (cite: Mercimek23) indicates that some interactions between the stars and envelope may be occurring, we do not see disturbed gas motions in the envelope or circumbinary disk. Moreover, given the mass of VLA 1623B and its projected separation, we would expect it to influence the circumbinary disk, although we detect no evidence of perturbations with the current data. Future analyses that model the circumbinary disk may yet discover deviations from Keplerian rotation due to gravitational perturbations from the more massive VLA 1623B, which would show the onset of dynamical interactions in action.

# Acknowledgements

We thank the anonymous referee for valuable comments that improved the publication. The authors thank the NAASC for support with the ALMA observations and data processing. The authors would also like to thank Ewine van Dishoeck for valuable discussions. SIS acknowledges the support for this work provided by the Natural Science and Engineering Research Council of Canada (NSERC), RGPIN-2020-03981, RGPIN-2020-03982, and RGPIN-2020-03983. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01089.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This research has made use of the SIMBAD database, operated at CDS, Strasbourg, France.

80 natexlab

(ref: Andre93) André, P., Ward-Thompson, D., & Barsony, M. 1993, ApJ, 406, 122

(ref: ArturV19) Artur de la Villarmois, E., Jørgensen, J. K., Kristensen, L. E., et al. 2019, A&A, 626, A71

(ref: Aso23) Aso, Y., Kwon, W., Ohashi, N., et al. 2023, ApJ, 954, 101

(ref: Aso17) Aso, Y., Ohashi, N., Aikawa, Y., et al. 2017, ApJ, 849, 56

(ref: Aso15) Aso, Y., Ohashi, N., Saigo, K., et al. 2015, ApJ, 812, 27

(ref: Bonnell94) Bonnell, I. A. & Bate, M. R. 1994, MNRAS, 271, 999

(ref: BontempsAndre97) Bontemps, S. & Andre, P. 1997, in IAU Symposium, Vol. 182, Herbig-Haro Flows and the Birth of Stars, ed. B. Reipurth & C. Bertout, 63

(ref: Chen13) Chen, X., Arce, H. G., Zhang, Q., et al. 2013, ApJ, 768, 110

(ref: Codella24) Codella, C., Podio, L., De Simone, M., et al. 2024, MNRAS, 528, 7383

(ref: Cuello22) Cuello, N., Ménard, F., & Price, D. J. 2023, European Physical Journal Plus, 138, 11

(ref: Czekala15) Czekala, I., Andrews, S. M., Jensen, E. L. N., et al. 2015, ApJ, 806, 154

(ref: deGouveia05) de Gouveia Dal Pino, E. M. 2005, Advances in Space Research, 35, 908

(ref: difran07) Di Francesco, J., Evans, II, N. J., Caselli, P., et al. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 17–32

(ref: Dunham15) Dunham, M. M., Allen, L. E., Evans, II, N. J., et al. 2015, ApJS, 220, 11

(ref: Feng20) Feng, S., Codella, C., Ceccarelli, C., et al. 2020, ApJ, 896, 37

(ref: Flores23) Flores, C., Ohashi, N., Tobin, J. J., et al. 2023, ApJ, 958, 98

(ref: Ginsburg18) Ginsburg, A., Bally, J., Goddi, C., Plambeck, R., & Wright, M. 2018, ApJ, 860, 119

(ref: Grasser21) Grasser, N., Ratzenböck, S., Alves, J., et al. 2021, A&A, 652, A2

(ref: Gutermuth09) Gutermuth, R. A., Megeath, S. T., Myers, P. C., et al. 2009, ApJS, 184, 18

(ref: Hara21) Hara, C., Kawabe, R., Nakamura, F., et al. 2021, ApJ, 912, 34

(ref: Harris18) Harris, R. J., Cox, E. G., Looney, L. W., et al. 2018, ApJ, 861, 91

(ref: Hsieh20) Hsieh, C.-H., Lai, S.-P., Cheong, P.-I., et al. 2020, ApJ, 894, 23

(ref: Jennings20) Jennings, J., Booth, R. A., Tazzari, M., Rosotti, G. P., & Clarke, C. J. 2020, MNRAS, 495, 3209

(ref: Jorgensen07prosac) Jørgensen, J. K., Bourke, T. L., Myers, P. C., et al. 2007, ApJ, 659, 479

(ref: Kratter10) Kratter, K. M., Matzner, C. D., Krumholz, M. R., & Klein, R. I. 2010, ApJ, 708, 1585

(ref: Kuffmeier19) Kuffmeier, M., Calcutt, H., & Kristensen, L. E. 2019, A&A, 628, A112

(ref: Ladd11) Ladd, E. F., Wong, T., Bourke, T. L., & Thompson, K. L. 2011, ApJ, 743, 108

(ref: Looney00) Looney, L. W., Mundy, L. G., & Welch, W. J. 2000, ApJ, 529, 477

(ref: Maret20) Maret, S., Maury, A. J., Belloche, A., et al. 2020, A&A, 635, A15

(ref: Maury12) Maury, A., Ohashi, N., & André, P. 2012, A&A, 539, A130

(ref: MercerStamatellos20) Mercer, A. & Stamatellos, D. 2020, A&A, 633, A116

(ref: Mercimek23) Mercimek, S., Podio, L., Codella, C., et al. 2023, MNRAS, 522, 2384

(ref: Michel22) Michel, A., Sadavoy, S. I., Sheehan, P. D., Looney, L. W., & Cox, E. G. 2022, ApJ, 937, 104

(ref: Miotello17) Miotello, A., van Dishoeck, E. F., Williams, J. P., et al. 2017, A&A, 599, A113

(ref: Murillo18) Murillo, N. M., Harsono, D., McClure, M., Lai, S. P., & Hogerheijde, M. R. 2018a, A&A, 615, L14

(ref: MurilloLai13) Murillo, N. M. & Lai, S.-P. 2013, ApJL, 764, L15

(ref: Murillo13) Murillo, N. M., Lai, S.-P., Bruderer, S., Harsono, D., & van Dishoeck, E. F. 2013, A&A, 560, A103

(ref: Murillo18gas) Murillo, N. M., van Dishoeck, E. F., van der Wiel, M. H. D., et al. 2018b, A&A, 617, A120

(ref: Offner12) Offner, S. S. R., Capodilupo, J., Schnee, S., & Goodman, A. A. 2012, MNRAS, 420, L53

(ref: Offner16) Offner, S. S. R., Dunham, M. M., Lee, K. I., Arce, H. G., & Fielding, D. B. 2016, ApJL, 827, L11

(ref: Offner10) Offner, S. S. R., Kratter, K. M., Matzner, C. D., Krumholz, M. R., & Klein, R. I. 2010, ApJ, 725, 1485

(ref: Offner23) Offner, S. S. R., Moe, M., Kratter, K. M., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 275

(ref: Ohashi97) Ohashi, N., Hayashi, M., Ho, P. T. P., & Momose, M. 1997, ApJ, 475, 211

(ref: Ohashi14) Ohashi, N., Saigo, K., Aso, Y., et al. 2014, ApJ, 796, 131

(ref: Ohashi23) Ohashi, N., Tobin, J. J., Jørgensen, J. K., et al. 2023, ApJ, 951, 8

(ref: Ohashi22) Ohashi, S., Codella, C., Sakai, N., et al. 2022, ApJ, 927, 54

(ref: OrtizLeon18) Ortiz-León, G. N., Loinard, L., Dzib, S. A., et al. 2018, ApJL, 869, L33

(ref: Pinte20) Pinte, C., Price, D. J., Ménard, F., et al. 2020, ApJL, 890, L9

(ref: Pinte18) Pinte, C., Price, D. J., Ménard, F., et al. 2018, ApJL, 860, L13

(ref: Premnath20) Premnath, P. H., Wu, Y.-L., Bowler, B. P., & Sheehan, P. D. 2020, Research Notes of the American Astronomical Society, 4, 100

(ref: Reipurth10) Reipurth, B., Mikkola, S., Connelley, M., & Valtonen, M. 2010, ApJL, 725, L56

(ref: Reynolds21) Reynolds, N. K., Tobin, J. J., Sheehan, P., et al. 2021, ApJL, 907, L10

(ref: Sadavoy18b) Sadavoy, S. I., Myers, P. C., Stephens, I. W., et al. 2018, ApJ, 859, 165

(ref: SadavoyStahler17) Sadavoy, S. I. & Stahler, S. W. 2017, MNRAS, 469, 3881

(ref: Sadavoy19) Sadavoy, S. I., Stephens, I. W., Myers, P. C., et al. 2019, ApJS, 245, 2

(ref: Sakai17) Sakai, N., Oya, Y., Higuchi, A. E., et al. 2017, MNRAS, 467, L76

(ref: Sakai14) Sakai, N., Sakai, T., Hirota, T., et al. 2014, Nature, 507, 78

(ref: Santangelo15) Santangelo, G., Murillo, N. M., Nisini, B., et al. 2015, A&A, 581, A91

(ref: Schreyer06) Schreyer, K., Semenov, D., Henning, T., & Forbrich, J. 2006, ApJL, 637, L129

(ref: SheehanEisner18) Sheehan, P. D. & Eisner, J. A. 2018, ApJ, 857, 18

(ref: Sheehan22_l1527) Sheehan, P. D., Tobin, J. J., Li, Z.-Y., et al. 2022, ApJ, 934, 95

(ref: Sheehan19) Sheehan, P. D., Wu, Y.-L., Eisner, J. A., & Tobin, J. J. 2019, ApJ, 874, 136

(ref: Speagle20) Speagle, J. S. 2020, MNRAS, 493, 3132

(ref: Takaishi21) Takaishi, D., Tsukamoto, Y., & Suto, Y. 2021, PASJ, 73, L25

(ref: Tazzari18) Tazzari, M., Beaujean, F., & Testi, L. 2018, MNRAS, 476, 4527

(ref: Teague21) Teague, R., Bae, J., Aikawa, Y., et al. 2021, ApJS, 257, 18

(ref: Teague19) Teague, R., Bae, J., & Bergin, E. A. 2019, Nature, 574, 378

(ref: Thieme23) Thieme, T. J., Lai, S.-P., Ohashi, N., et al. 2023, ApJ, 958, 60

(ref: Tobin16l1448) Tobin, J. J., Kratter, K. M., Persson, M. V., et al. 2016, Nature, 538, 483

(ref: Tobin22) Tobin, J. J., Offner, S. S. R., Kratter, K. M., et al. 2022, ApJ, 925, 39

(ref: Tobin20) Tobin, J. J., Sheehan, P. D., Megeath, S. T., et al. 2020, ApJ, 890, 130

(ref: Tychoniec21) Tychoniec, Ł., van Dishoeck, E. F., van’t Hoff, M. L. R., et al. 2021, A&A, 655, A65

(ref: vantHoff18) van’t Hoff, M. L. R., Tobin, J. J., Harsono, D., & van Dishoeck, E. F. 2018, A&A, 615, A83

(ref: Villenave20) Villenave, M., Ménard, F., Dent, W. R. F., et al. 2020, A&A, 642, A164

(ref: Vorobyov10) Vorobyov, E. I. 2010, ApJ, 723, 1294

(ref: Wakelam05) Wakelam, V., Ceccarelli, C., Castets, A., et al. 2005, A&A, 437, 149

(ref: Williams19) Williams, J. P., Cieza, L., Hales, A., et al. 2019, ApJL, 875, L9

(ref: Yen14) Yen, H.-W., Takakuwa, S., Ohashi, N., et al. 2014, ApJ, 793, 1

(ref: Zhang21) Zhang, K., Booth, A. S., Law, C. J., et al. 2021, ApJS, 257, 5

(ref: Zhang20) Zhang, K., Schwarz, K. R., & Bergin, E. A. 2020, ApJL, 891, L17

# Proper motion and closest approach

This appendix outlines the calculations for the proper motions for VLA 1623B and VLA 1623W. We excluded VLA 1623A from these calculations since the combination of it being a tight binary and having a circumbinary disk can confuse its centroid position. We took positions of VLA 1623B and VLA 1623W from the literature that present high-resolution data ($\lesssim 1\ensuremath{''}$) and where the epoch of observations could be identified. Table [\[tab_pm\]](#tab_pm) lists the corresponding archival data, where Column 1 gives the reference, Column 2 gives the epoch of observation, Column 3 gives the observing frequency, Columns 4 and 5 give the source right ascension and its adopted error, Columns 6 and 7 give the source declination and its adopted error, Column 8 gives the geometric mean size of the synthesized beam, and Column 9 gives the phase calibrator for the observations. We follow (cite: Sadavoy18b) in using the map resolution scaled by the source peak S/N to estimate the position uncertainties. For the present study and those of (cite: Sadavoy19) and (cite: Harris18), both sources had peak S/N $>100$, so we adopted a minimum error of 5 mas.

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:---|:--:|:---|:--:|:--:|:---|
| Reference$^{a}$ | Epoch | Freq | $\alpha$ | $\sigma_{\alpha}$ | $\delta$ | $\sigma_{\delta}$ | FWHM$^{b}$ | Phase Calibrator |
|  |  | (GHz) | (h:m:s) | (mas) | (d:am:as) | (mas) | (arcsec) |  |
| This study | 2019.3 | 342 | 16:26:25.6295 | 5 | -24:24:29.6258 | 5 | 0.27 | J1650-2943 |
| Sadavoy19 (1) | 2017.5 | 233 | 16:26:25.6315 | 5 | -24:24:29.6185 | 5 | 0.24 | J1625-2527 |
| Harris18 (2) | 2016.3 | 344 | 16:26:25.6316 | 5 | -24:24:29.5866 | 5 | 0.18 | J1625-2527, J1633-2557 |
| Murillo13$^{c}$ (3) | 2012.33 | 230 | 16:26:25.636 | 16 | -24:24:29.488 | 16 | 0.65 | J1733-1304 |
| Maury12$^{c}$ (4) | 2009.58 | 225 | 16:26:25.63 | 100 | -24:24:29.5 | 100 | 0.53 | J1625-2527, J1517-2422 |
| Chen13$^{c}$ (5) | 2007.5 | 230 | 16:26:25.64 | 200 | -24:24:29.3 | 200 | 0.88 | J1626-2951 |

$^a$References for positions are: (1) (cite: Sadavoy19), (2) (cite: Harris18), (3) (cite: Murillo13), (4) (cite: Maury12), (5) (cite: Chen13).

$^b$ The geometric mean FWHM ($= \sqrt{ab}$).

$^c$ Position offsets are estimated using total flux

Figure [10](#fig_pm) shows the relative position of VLA 1623W compared to the epoch in (cite: Sadavoy19). We show the VLA 1623W results only as an example as the corresponding plot for VLA 1623B is very similar. The dashed line shows our adopted proper motion, which we measured using the data from (cite: Sadavoy19), (cite: Harris18), (cite: Murillo13), and (cite: Chen13) only. We excluded the data point from (cite: Maury12), because they did not provide sufficient precision for a proper motion analysis (cite: Sadavoy18b). We further excluded our new measurement presented here due to a noticeable offset of roughly 15 mas in RA and 30 mas in Dec compared to the general trend (dashed line), which we found for both VLA 1623W and VLA 1623B. As such, this 15 – 30 mas offset appears to be systematic for the entire map.

![](proper_motion_ra_vla1623w.eps)

A systematic offset in position could be explained by the present study using different calibrators. Table [\[tab_pm\]](#tab_pm) lists the phase calibrator for each observation. Most studies used J1625-2527, but this work used J1650-2943. From the ALMA Technical Handbook, we can expect a 1 $\sigma$ pointing accuracy of $\sim 15$ mas, which is of comparable order to the systematic offsets. To address possible astrometry uncertainties from the calibrators themselves, we added in quadrature a 15 mas position error to the position errors from Table [\[tab_pm\]](#tab_pm) before fitting for the proper motion using linear least squares.

We find a proper motion for VLA 1623W of $$\begin{eqnarray}
\mu_\alpha\cos{\delta} &=& -12.4\pm5.1\ \mbox{mas\ yr$^{-1}$}\\
\mu_\delta &=& -25.6\pm6.3\ \mbox{mas\ yr$^{-1}$}
,
\end{eqnarray}$$

which are slightly different from (cite: Harris18) but within errors. (cite: Harris18) measured a proper motion of VLA 1623W using their data and those of (cite: Murillo13) only. There is a possibility that the position of VLA 1623W may also have differences due to wavelength since VLA 1623W is viewed nearly edge-on and shows evidence of flaring (cite: Michel22). There is a slight difference in RA position between (cite: Harris18) at 870 $\mu$m and the 1.3 mm measurements from (cite: Murillo13) and (cite: Sadavoy19), whereas their Dec positions are in good agreement. VLA 1623W appears nearly vertical in Dec, which would make any temperature variations with disk scale height appear only in RA. Nevertheless, (cite: Murillo13) have a different phase calibrator, which could also induce an offset. Therefore, we cannot conclude that the shift in RA from (cite: Harris18) is due to temperature stratification.

We also re-measured the proper motion of VLA 1623B from (cite: Sadavoy18b) using our revised errors that include adopting 15 mas pointing uncertainties. The revised proper motion for VLA 1623B is $$\begin{eqnarray}
\mu_\alpha\cos{\delta} &=& -7.8\pm2.9\ \mbox{mas\ yr$^{-1}$}\\
\mu_\delta &=& -29.0\pm3.4\ \mbox{mas\ yr$^{-1}$}
,
\end{eqnarray}$$ which is nearly identical in RA and has a slight difference in Dec within errors compared to (cite: Sadavoy18b).

We combined the above proper motions for VLA 1623W and VLA 1623B to determine when the two objects had their closest approach in the plane of the sky, assuming constant velocities. Figure [11](#fig_pm_time) shows the extrapolation of both nominal proper motions with black circles showing look-back times in 500 yr intervals. The closest approach is shown with open circles at a time of $\sim$ 1400 years, when the two sources were separated by $\sim$ 4.6 arcsec ($\sim$ 650 au) in the plane of the sky.

![](vla1623_wide_pm_lookback_plot.eps)

Nevertheless, the proper motions for both sources have large error bars ($> 10\%$), which make uncertainties on the closest approach difficult to constrain analytically. We used a Monte Carlo error analysis for the proper motions for VLA 1623B and VLA 1623W to estimate the error in closest separation. We assumed that the proper motion uncertainties given above correspond to the FWHM of a Gaussian distribution and then draw 10000 random values to add to the nominal proper motions. For each new set of proper motions, we re-evaluated the closest approach. Figure [12](#fig_errhist_pm) shows histograms from this Monte Carlo analysis for the distribution of closest approach and the time since closest approach. In both cases, we excluded roughly 200 data points for which the closest approach was given by the current epoch (e.g. in the case where the two sources are moving towards each other rather than away) as this case slightly skewed the statistics. From the error analysis, we find a median minimum separation of 4.9 arcsec (first and third quartiles are 2.7 arcsec and 6.6 arcsec) and a median time of 1150 years (first and third quartiles are 830 years and 1590 years). These results are in good agreement with the nominal case using the best-fit proper motions (without the errors). Moreover, this analysis indicates that VLA 1623W was unlikely to have a very close encounter as a plane of sky separation of $<$ 100 au is only at the 6th percentile.

![image](minimum_sep_hist_fwhm.eps) ![image](minimum_sep_time_hist_fwhm.eps)

[^1]: An additional source, VLA 1623NE, is 2700 au north-east of the central pair, but we exclude this source as a more evolved, unrelated Class II object (cite: Sadavoy19).

[^2]: The primary beam response is 0.4 at the position of VLA 1623W.

</paper>

Write the methods card for this paper.