# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...905L..23M\sonnetcc\reply.txt

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
 "bibcode": "2020ApJ...905L..23M",
 "title": "Where's the Dust?: The Deepening Anomaly of Microwave Emission in NGC 4725 B",
 "year": 2020,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Murphy, E. J.",
 "n_authors": 8,
 "arxiv_id": "2011.03060",
 "doi": "10.3847/2041-8213/abc7c8",
 "alma_projects_linked_by_archive": [
  "2018.1.01826.S"
 ]
}
```

Paper text:
<paper>
# Where’s the Dust?: The Deepening Anomaly of Microwave Emission in NGC 4725 B

## Abstract

We present new Atacama Large Millimeter Array (ALMA) observations towards NGC 4725 B, a discrete, compact, optically-faint region within the star-forming disk of the nearby galaxy NGC 4725 that exhibits strong anomalous microwave emission (AME). These new ALMA data include continuum observations centered at 92, 133, 203, and 221 GHz accompanied by spectral observations of the $^{12}$CO ($J=2\rightarrow1$) line. NGC 4725 B is detected in the continuum at all frequencies, although the detection at 203 GHz is marginal. While molecular gas is not detected at the exact location of NGC 4725 B, there is molecular gas in the immediate vicinity (i.e., $\lesssim 100$ pc) along with associated diffuse 8 $\mu$m emission. When combined with existing Very Large Array continuum data at 1.5, 3, 5.5, 9, 14, 22, 33, and 44 GHz, the spectrum is best fit by a combination of AME, synchrotron, and free-free emission that is free-free absorbed below $\sim6$ GHz. Given the strength of the AME, there is surprisingly no indication of millimeter dust emission associated with NGC 4725 B on $\lesssim$6$''$ spatial scales at the sensitivity of the ALMA interferometric data.

Based on the properties of the nearest molecular gas complex and the inferred star formation rate, NGC 4725 B is consistent with being an extremely young ($\sim$3–5 Myr) massive ($\lesssim 10^{5}\,M_{\odot}$) cluster that is undergoing active cluster feedback. However, the lack of millimeter thermal dust emission is difficult to reconcile with a spinning dust origin of the 30 GHz emission. On the other hand, modeling NGC 4725 B as a new class of background radio galaxy is also unsatisfactory.

# Introduction

It has been over 20 years since the initial discovery of excess $\sim30$ GHz ($\sim 1\,$cm), dust-correlated emission in cosmic microwave background experiments (cite: ak96b; eml97), yet our current understanding of the physical mechanism and environmental conditions powering anomalous microwave emission (AME) remains highly incomplete (cite: AME18). The leading explanation for AME is “spinning dust," in which rapidly rotating ultrasmall (radius $a \lesssim 1$ nm) grains with a non-zero electric dipole moment produce a peaked microwave emission spectrum in the frequency range spanning $\approx 10 - 60$ GHz (cite: wce57; dl98b; ahd09; hoang11; hd17).

To date, AME has been observed in a wide variety of astrophysical environments, indicating that it is truly a ubiquitous emission component in the interstellar medium (ISM) of galaxies, and that a complete model may significantly impact our understanding of the astrophysics of the ISM. For instance, investigations within the Galaxy have uncovered strong detections of AME in molecular clouds (cite: plsd11) along with discrete locations adjacent to larger H ii complexes (cite: cd09; tibbs11), consistent with the theoretical expectation that it is a common emission component in galaxies.

Most recently, detection of AME has been reported in proto-planetary disks around Herbig Ae stars (cite: greaves18). Although seemingly a common phenomenon from Galactic sources, AME has been observed in surprisingly few extragalactic sources, with only NGC 6946 (cite: ejm10; as10; bh15), NGC 4725 (cite: ejm18c), and M 31 (cite: Battistelli_2019) having firm detections. This dearth of extragalactic detections likely arises from the lack of deep, wide-field observations of nearby extragalactic sources at $\sim30$ GHz, the insensitivity of interferometers to large angular scale emission, and the need for multi-frequency data (cite: bh15; stl20).

In this letter, we revisit the recent detection of AME from an optically-faint region within the star-forming galaxy NGC 4725 from 33 GHz Karl G. Jansky Very Large Array (VLA) observations carried out as part of the Star Formation in Radio Survey (cite: ejm18a; stl20). This source, NGC 4725 B, was studied by (cite: ejm18c), who concluded that it was consistent with a highly-embedded ($A_V > 5$ mag) nascent star-forming region, in which young ($\lesssim 3$ Myr) massive stars are still enshrouded by their natal cocoons of gas and dust, lacking enough supernovae to produce measurable synchrotron emission. In light of our new Atacama Large Millimeter Array (ALMA) continuum and molecular gas observations of NGC 4725 B, along with additional archival VLA data, this scenario remains largely viable. However, the ALMA data raise a new and unexpected question regarding the origin of the AME—how can such a strong 30 GHz excess be produced without an accompanying millimeter dust continuum?

This letter is organized as follows: The data and analysis procedures are presented in Section [2](#sec:data). The results are then presented in Section [3](#sec:results). A brief discussion of our findings and main conclusions is given in Section [4](#sec:summary).

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Freq. | Synthesized | $\sigma$ | $\sigma_{T_{b}}$ | $S_{*}^{\dagger}$ |
| (GHz) | Beam | ($\mu$Jy bm$^{-1}$) | (mK) | ($\mu$Jy) |
| 1.50 | $1.32\ensuremath{''} \times 1.09\ensuremath{''}$ | 31.1 | 11697\. | $<$ 106. |
| 3.00 | $1.85\ensuremath{''} \times 1.76\ensuremath{''}$ | 13.7 | 569.37 | $157.\pm   14.$ |
| 5.50 | $0.36\ensuremath{''} \times 0.31\ensuremath{''}$ | 12.2 | 4387.4 | $299.\pm   19.$ |
| 9.00 | $0.25\ensuremath{''} \times 0.21\ensuremath{''}$ | 10.8 | 3125.6 | $248.\pm   22.$ |
| 14.0 | $0.15\ensuremath{''} \times 0.12\ensuremath{''}$ | 10.1 | 3478.4 | $210.\pm   19.$ |
| 22.0 | $1.50\ensuremath{''} \times 0.89\ensuremath{''}$ | 20.5 | 38.340 | $297.\pm   23.$ |
| 33.0 | $0.91\ensuremath{''} \times 0.58\ensuremath{''}$ | 21.4 | 45.310 | $359.\pm   31.$ |
| 44.0 | $0.63\ensuremath{''} \times 0.50\ensuremath{''}$ | 32.9 | 66.700 | $214.\pm   51.$ |
| 92.0 | $0.54\ensuremath{''} \times 0.37\ensuremath{''}$ | 8.88 | 7.4800 | $139.\pm   15.$ |
| 133\. | $0.48\ensuremath{''} \times 0.29\ensuremath{''}$ | 14.8 | 8.1000 | $106.\pm   33.$ |
| 203\. | $0.69\ensuremath{''} \times 0.40\ensuremath{''}$ | 17.2 | 1.9800 | $53.7\pm   32.$ |
| 221\. | $0.51\ensuremath{''} \times 0.34\ensuremath{''}$ | 13.4 | 1.8000 | $84.3\pm   28.$ |
| $^{12}$CO ($J=2\rightarrow1$) Emission Line |  |  |  |  |
|  |  | (Jy bm$^{-1}$ km s$^{-1}$) | (K km s$^{-1}$) | (Jy km s$^{-1}$) |
| 229.6 | $0.61\ensuremath{''} \times 0.46\ensuremath{''}$ | 0.038 | 3.15 | $<$ 0.820 |

: Observational Data

Table notes: $^{\dagger}$ Photometry measured after convolving all data to match the synthesized beam of the 3 GHz data.

# Data and Analysis

We refer the reader to (cite: ejm18c) for detailed information on NGC 4725 and NGC 4725 B, along with the associated data and analysis procedures presented in that paper. In this letter we simply summarize key details of that work and present the new ALMA and archival VLA data, associated analysis procedures, and discuss how these new data affect the previous interpretation.

NGC 4725 is a nearby (cite: hkp01) barred ringed spiral galaxy that hosts an AGN (Sy2) nucleus (cite: jm10). Located at J2000 $\alpha =12^\mathrm{h}50^\mathrm{m}28.48s, \delta =+25\ensuremath{^\circ}30\ensuremath{'}22.5\ensuremath{''}$ (at a galactocentric radius of $\approx$1.9 kpc), NGC 4725 B was first detected at 33 GHz as part of SFRS (cite: ejm18a), comprising nuclear and extranuclear star-forming regions in 56 nearby galaxies ($d_{L} < 30$ Mpc) observed as part of the *Spitzer* Infrared Nearby Galaxies Survey (cite: rck03) and Key Insights on Nearby Galaxies: a Far-Infrared Survey with *Herschel* (cite: kf11) legacy programs.

## VLA Data Reduction and Imaging

Radio data were obtained as part of multiple campaigns using the VLA covering the S- ($2-4$ GHz), Ku- ($12-18$ GHz), K- ($18-26.5$ GHz), Ka- ($26.5-40$ GHz, and Q- ($40-50$ GHz) bands, which are summarized in Table [1](#tbl-1). Details on the data reduction and imaging procedures can be found in (cite: ejm18a; ejm18c; stl20). To summarize, we followed standard calibration procedures, using the VLA calibration pipeline built on the Common Astronomy Software Applications (cite: casa) versions 4.6.0 and 4.7.0. After each initial pipeline run, we manually inspected the calibration tables and visibilities for signs of instrumental problems (e.g., bad deformatters) and RFI, flagging correspondingly. After flagging, we re-ran the pipeline, and repeated this process until we could not detect any further signs of bad data.

As with the data calibration, a detailed description of the imaging procedure used here can be found in (cite: ejm18a; stl20). To summarize, calibrated VLA measurement sets for each source were imaged using the task TCLEAN in CASA version 4.7.0. The synthesized beam, point source rms, and surface brightness rms for each final image is given in Table [1](#tbl-1). Employing the ALMA Cycle 4 handbook definition of the largest angular scale (LAS), we find that the LAS these images are sensitive to are $\theta_{\rm LAS} \approx 31.5\ensuremath{''}, 23.5\ensuremath{''}, 16.9\ensuremath{''}, 11.3\ensuremath{''}$, and 8.44$''$ at 3, 15, 22, 33 and 44 GHz, respectively, where the calculations have been done with the CASA Analysis Utilities task ESTIMATEMRS.

We additionally make use of archival VLA data (VLA/12B-191) that included observations toward the nucleus of NGC 4725 in the L- ($1-2$ GHz), C- ($4-8$ GHz, X- ($8-12$), and Ku-bands. These data were taken in the A-configuration and made use of the 8-bit samplers. The L-band data had a maximum instantaneous bandwidth of 1 GHz with a central frequency of 1.5 GHz. The data of the remaining frequency bands had a maximum of 2 GHz of bandwidth with central frequencies of 5.5, 9, and 14 GHz for the C-, X-, and Ku-band imaging, respectfully.

These data were reduced using the VLA calibration pipeline built on CASA version 5.3.0. The synthesized beam, point source rms, and surface brightness rms for each final image is given in Table [1](#tbl-1). Again, using the task ESTIMATEMRS, the LAS that these images are sensitive to are $\theta_{\rm LAS} \approx 19.2\ensuremath{''}, 5.26\ensuremath{''}, 3.19\ensuremath{''}$, and 2.05$''$ at 1.5, 5.5, 9, and 14 GHz, respectively.

Calibrated data were imaged using the task TCLEAN in CASA version 5.6.1. The mode of TCLEAN was set to multi-frequency synthesis (cite: mfs1; mfs2). We chose to use *Briggs* weighting with ROBUST=0.5. Given that the fractional bandwidth is $>10\%$ for each band, we set the variable NTERMS=2, which allows the cleaning procedure to also model the spectral index variations on the sky. For the L-band imaging, we additionally made use of the w-projection algorithm to help deal with bright sources far from the phase center. Unlike the 14 GHz data, the 15 GHz data delivered a non-optimal calibration, which was evident in the data of the phase calibrator source itself. The resulting 14 GHz image created from these archival data is therefore used exclusively in the present analysis.

## ALMA Data Reduction and Imaging

ALMA data were obtained during Cycle 6 (Project Code: 2018.1.01826.S) in Bands 3, 4, 5, and 6 and are summarized in Table [1](#tbl-1). Observations at Bands 3, 4, and 5 were centered at 92, 133, and 203 GHz, respectively, for dedicated continuum imaging; observations at each band used 4 spectral windows with a bandwidth of 1.875 GHz and 31.250 MHz spectral channels. For Band 6 observations, three spectral windows were set up for dedicated continuum imaging similar to Bands 3, 4, and 5 observations. However, the fourth spectral window was tuned to 229.612 GHz with a bandwidth of 1.875 GHz and spectral resolution of 1938.477 kHz (2.531 km s$^{-1}$) to detect $^{12}$CO ($J=2\rightarrow1$) at a rest frequency of 230.5424 GHz. The corresponding continuum image created from the line-free Band 6 data is centered at 221 GHz.

Like the VLA data, the ALMA data were reduced and calibrated using CASA following standard procedures as part of the ALMA quality assurance process. The ALMA data were reduced using both the ALMA calibration pipeline with CASA version 5.4.0, as well as prepared manual reduction and imaging scripts. Calibrated data were imaged using the task TCLEAN in CASA version 5.6.1. The mode of TCLEAN was set to multi-frequency synthesis (cite: mfs1; mfs2). We chose to use *Briggs* weighting with ROBUST=0.5. For Bands 3 and 4, where the fractional bandwidth was $>10\%$, we set the variable NTERMS=2, which allows the cleaning procedure to also model the spectral index variations on the sky. For continuum imaging of Bands 5 and 6, we instead set the variable NTERMS=1; in the case of Band 6, we imaged the 3 dedicated continuum spectral windows and the line-free portion of the fourth spectral window. In all cases of the continuum imaging, we do not make use of the multiscale clean option (cite: msclean; msmfs). The synthesized beam, point source rms, and surface brightness rms for each final image is given in Table [1](#tbl-1). Based on the task ESTIMATEMRS, the LAS that these images are sensitive to are $\theta_{\rm LAS} \approx 6.64\ensuremath{''}, 5.10\ensuremath{''}, 5.76\ensuremath{''}$, and 4.76$''$ at 92, 133, 203, and 221 GHz respectively.

In Figure [1](#fig:radpan), $15\ensuremath{''} \times 15\ensuremath{''}$ ($\approx 900\,{\rm pc} \times 900$ pc) cutouts centered on the location of NGC 4725 B are shown for all radio and millimeter data.

Similar to the continuum imaging, the $J=2\rightarrow1$ CO line data were imaged using TCLEAN, but instead setting the mode to “cube." Unlike the ALMA continuum emission for NGC 4725 B, the molecular gas appears extended (see Figure [2](#fig:COextent)). Consequently, we also made use of the multiscale clean option (cite: msclean; msmfs) to help deconvolve extended low-intensity line emission and to search for structures with scales $\approx$1 and 3 times the FWHM of the synthesized beam. The moment 0 map was then created by integrating the spectral cube at each pixel limited to the portion of velocity space associated with line emission.

The synthesized beam and rms of the $J=2\rightarrow1$ CO moment 0 map is given in Table [1](#tbl-1). The $J=2\rightarrow1$ CO moment 0 contours are overlaid on each radio and millimeter continuum image in Figure [1](#fig:radpan).

## Photometry

Photometry was carried out at all frequencies before applying a primary beam correction. To measure the flux densities of the source at each frequency, we first beam-match the data to the lowest resolution beam among all images (i.e., the 3 GHz data) using the CASA task IMSMOOTH. We elect to exclude the much lower resolution 2013 March 33 GHz data included in (cite: ejm18c), since it is significantly (i.e., a factor of $\sim$30) coarser than the ALMA data (i.e., $2.89\ensuremath{''}\times1.97\ensuremath{''}$); convolving the data to such a low angular resolution typically reduces/removes the statistical significance of a detection in the higher frequency ALMA bands. Further, we make use of the archival VLA 14 GHz data only rather than the newer 15 GHz data given the much better calibration and imaging quality of the final map.

Next, the CASA task IMFIT was used to fit an elliptical Gaussian to the emission within a circular aperture having a radius equal to the FWHM of the synthesized beam major axis of the beam matched images (i.e., 1.85$''$). Given the proximity of NGC 4725 B to the phase center of each observation, primary beam corrections

were negligible (i.e., $<1$%) at all frequencies except 5.5, 9, and 14 GHz, where correction factors of 1.011, 1.032, 1.079 were applied to the reported peak brightnesses and integrated flux densities (along with their errors), respectively.

These factors were obtained via the frequency-dependent primary beam correction given in EVLA Memo# 195 (Perley 2016)[^1].

The source is unresolved in all of the native resolution images using the criterion that the fitted major axis $\phi_{\rm M}$ be at least $2\sigma_{\phi_{\rm M}}$ larger than the FWHM of the synthesized beam major axis. Similarly, the source appears unresolved in the beam-matched images at all frequencies. Consequently, we take the total flux density ($S_{*}$) for the unresolved cases to be the geometric mean of the peak brightness and integrated flux density reported by IMFIT. We choose this value as it provides the most accurate measurement for the flux density of a weak source given that the uncertainties on the peak brightness and integrated flux density from the elliptical Gaussian fitting are anti-correlated (cite: jc97).

The total flux densities, along with their uncertainties, are given in Table [1](#tbl-1) at each frequency.

While IMFIT formally reported a statistically significant detection at 1.5 GHz (i.e., $S_{*} = 134\pm30$), it is clear from that map (see Figure [1](#fig:radpan)) that there is nothing co-spatial with NGC 4725 B and that a nearby noise feature is being fit. Consequently, we consider this as a non-detection and report the 3$\sigma$ rms upper limit in Table [1](#tbl-1) and exclude this data point from fits. There are no significant (i.e., signal-to-noise ratio $> 3$) detections in the beam-matched 203 GHz continuum image or in the $J=2\rightarrow1$ CO line towards NGC 4725 B. For the 203 GHz continuum, we report the IMFIT results in Table [1](#tbl-1), as the fitting function converged and there does appear to be a source at the location of NGC 4725 B in the image. For the $J=2\rightarrow1$ CO line, IMFIT failed to converge, so we therefore report the 3$\sigma$ rms upper limit in Table [1](#tbl-1).

The radio-to-millimeter spectrum of NGC 4725 B is shown in Figure [3](#fig:spec).

We note that in (cite: ejm18c) they report the integrated 15 GHz flux density as $S_{*}$ since the source was found to be marginally resolved (i.e., $2.3\sigma$ significance) after convolving all VLA images to the much lower resolution of their 2013 March 33 GHz. Even with differing resolutions and treatment of the source as resolved rather than unresolved, their 15 GHz flux density is consistent with the 14 GHz flux density reported in the present study.

# Results

In the following Section, we combine the new ALMA continuum and molecular gas imaging with the existing VLA continuum imaging for NGC 4725 B and perform a parametric fit to the data.

## Parametric Models of the Radio-to-Millimeter Spectrum

We employ a simple parametric model to fit the NGC 4725 B spectrum presented in Figure [3](#fig:spec). The first component in the model is free-free emission, which has flux density

$$\begin{equation}
    S_\nu^{\rm ff} = B_\nu\left(T_e\right)\left(1-e^{-\tau_\nu^{\rm ff}}\right)\pi\left(\frac{D}{2d_L}\right)^2
    ~~~,
\end{equation}$$ where $T_e$ is the electron temperature, $B_\nu\left(T\right)$, is the Planck function, $D$ is the diameter of the emitting region, $d_L = 11.9$ Mpc is the distance to NGC 4725, and $\tau_\nu^{\rm ff}$ is the free-free optical depth. We model the frequency dependence of $\tau_\nu^{\rm ff}$ in the low-frequency limit ($h\nu \ll kT_e$) following (cite: draine2011):

$$\begin{equation}
    \tau_\nu^{\rm ff} = \frac{4}{3}\left(\frac{2\pi}{3}\right)^{1/2} \frac{q_e^6 g_{\rm ff} EM}{\left(m_e k T_e\right)^{3/2}c\nu^2}
    ~~~,
\end{equation}$$ where $q_e$, $m_e$, $k$, $c$ are, respectively, the electron charge (note Gaussian units), electron mass, Boltzmann constant, and speed of light, and $EM$ is the emission measure. We approximate the Gaunt factor $g_{\rm ff}$ as an analytic function of frequency and electron temperature following (cite: draine2011):

$$\begin{equation}
    g_{\rm ff}\left(\nu, T_e\right) = {\rm ln}\Bigg\{{\rm exp} \left[5.960 - \frac{\sqrt{3}}{\pi}{\rm ln}\left(\nu_9 T_4^{-3/2}\right)\right] + e\Bigg\}
    ~~~,
\end{equation}$$ where $\nu_9 \equiv \nu/10^9\,$Hz and $T_4 \equiv T_e/10^4\,$K. Given the limited number of data points and the relative insensitivity of the spectrum to $T_e$, we fix $T_e = 10^4$ K. It should be noted, however, that the fit value of $D$ is sensitive to our choice of $T_e$, with higher assumed $T_e$ resulting in smaller fit $D$, and vice-versa.

The spectral slope between 5 and 15 GHz suggests the presence of an optically-thin synchrotron component, while the sharp decline in emission toward lower frequencies is indicative of free-free absorption. We model the optically-thin synchrotron emission as a power law and the absorption as pure free-free absorption, yielding a spectrum

$$\begin{equation}
    S_\nu^{\rm sync} = A_s \left(\frac{\nu}{20\,{\rm GHz}}\right)^\alpha e^{-\tau_\nu^{\rm ff}}
    ~~~,
\end{equation}$$ where $A_s$ is the 20 GHz flux density in the optically thin limit. We find that the synchrotron component dominates the emission only over a narrow range of frequencies, providing little constraining power on the spectral index. We therefore adopt $\alpha = -0.83$, consistent with similar observations for star-forming galaxies (cite: nkw97; ejm11b).

While the AME component could in principle be modeled using the detailed physical prescription implemented in the `SpDust` software (cite: ahd09; sah11), we pursue instead a simple functional description. (cite: cepeda2020) found that the canonical spinning dust spectra in the representative Galactic environments defined by (cite: dl98b) were well-described by

$$\begin{equation}
\label{eq:ame_sed}
    S_\nu^{\rm AME} = A_{\rm AME}\ {\rm exp}\Big\{-\frac{1}{2}\left[\frac{{\rm ln}\left(\nu/\nu_p\right)}{W_{\rm AME}}\right]^2 - \tau_\nu^{\rm ff}\Big\}
    ~~~,
\end{equation}$$ in general agreement with the more detailed parameterization derived by (cite: stevenson2014). Note that, for completeness, we have included a free-free absorption term, even though the effects are small at frequencies where the AME dominates. Here $\nu_p$ is the peak frequency, $A_{\rm AME}$ is the flux density at $\nu_p$, and $W_{\rm AME}$ governs the width of the spectrum. (cite: cepeda2020) found that both the theoretical spectra generated by `SpDust` and the radio observations of $\lambda$ Ori yielded $W_{\rm AME}$ in the range of 0.4 to 0.7. We caution that this function provides a convenient representation of the spinning dust spectrum near its peak, but is unlikely to accurately represent the low or high frequency tails.

Finally, the high-frequency thermal dust emission is parameterized by a modified blackbody, i.e.,

$$\begin{equation}
    S_\nu^d = A_d \left(\frac{\nu}{353\,{\rm GHz}}\right)^\beta \frac{B_\nu\left(T_d\right)e^{-\tau_\nu^{\rm ff}}}{B_{353\,{\rm GHz}}\left(T_d\right)}
\end{equation}$$ where $A_d$ is the flux density at 353 GHz, $T_d$ is the dust temperature, and $B_\nu\left(T\right)$ is the Planck function. Given the lack of high-frequency data at the requisite angular resolution and the apparent lack of strong signal in the $\nu > 100$ GHz data, we fix $\beta = 1.55$ and $T_d = 19.6$ K, which are representative values for dust emission in the Galaxy (cite: Planck_Int_XXII; Planck_2018_XI). As with AME, the free-free absorption term is added only for completeness and has little effect on the spectrum at millimeter wavelengths.

## Model Fits

![image](fit_synch.pdf) ![image](fit_synch_dust.pdf)

To fit the model described in the previous section to the observed flux densities, we employ the `emcee` Markov Chain Monte Carlo software (cite: emcee) to sample the seven parameters $EM$, $D$, $A_s$, $A_{\rm AME}$, $W_{\rm AME}$, $\nu_p$, and $A_d$. We use broad, uninformative priors, requiring only that $EM$, $D$, $A_s$, $A_{\rm AME}$, and $A_d$ be positive, that $10 < \nu_p/{\rm GHz} < 50$, and that $0 < W_{\rm AME} < 1$.

The full seven parameter fit yields bimodal posteriors corresponding to two distinct scenarios, which we illustrate in Figure [3](#fig:spec). In the first scenario (Figure [3](#fig:spec), left panel), the millimeter dust emission is consistent with zero and the AME is sharply peaked near 30 GHz. In the second scenario (Figure [3](#fig:spec), right panel), thermal dust and free-free emission contribute roughly equally to the emission in the ALMA bands, the AME component is significantly broader and shifted to higher frequencies ($\nu_p = 38$ GHz), and the synchrotron emission dominates the low frequency spectrum. The model without millimeter dust emission is the maximum likelihood solution, and so we consider this our default model and quote parameter constraints from a six parameter fit fixing $A_d = 0$. Inclusion of a small amount of dust emission does not qualitatively alter this fit and cannot be ruled out; this model should be considered as representative of the scenario in which emission in the ALMA bands is mostly free-free. As we discuss in greater detail in Section [4.1.3](#subsub:ame_constraints), the alternate scenario with significant thermal dust emission at millimeter wavelengths does not modify our principal conclusions, including the fact that the millimeter emission is much weaker than anticipated if the 30 GHz excess is attributed to spinning dust. The full posterior distributions are presented in Figure [4](#fig:triangle) in the Appendix.

Despite the simplicity of the model with no millimeter dust emission (i.e., $A_d = 0$), it provides an excellent description of the data ($\chi^2 = 9.0$ for a six parameter fit to eleven data points). To match the turnover at low frequencies, free-free absorption is required. We find that the free-free emission can be explained by a region with $EM = \left(1.46\pm0.15\right)\times10^{26}\,$cm$^{-5}$ and physical size $D = 2.30^{+0.30}_{-0.49}$ pc. The free-free optical depth is unity at 3.7 GHz. In general agreement with the analysis of (cite: ejm18c), we find that free-free accounts for only $25\%$ of the 30 GHz emission, with AME dominating at this frequency. We differ in our analysis by the inclusion of synchrotron emission, which contributes 18% of the 30 GHz emission in this model. The 30 GHz excess is well fit with an AME component described by Equation [\[eq:ame_sed\]](#eq:ame_sed) and having peak frequency of $\nu_p = 31.6^{+6.5}_{-3.0}\,$GHz and a rather narrow width of $W_{\rm AME} = 0.32^{+0.20}_{-0.11}$. For completeness, the remaining model parameters have fit values of $A_s = 95^{+21}_{-17}$ $\mu$Jy and $A_{\rm AME} = 209^{+47}_{-37}\,\mu$Jy.

The greatest discrepancy between the data and the model is at 92 GHz, where the model is 1.9$\sigma$ too low, but this may also be an indication that the simple functional form used to fit the AME component (Equation [\[eq:ame_sed\]](#eq:ame_sed)) falls off too rapidly at high frequencies. More observations are needed to better constrain the shape of the spectrum, particularly at frequencies above 30 GHz.

The alternative solution with nonzero millimeter dust emission differs significantly in the relative importance of the emission mechanisms. The observed 30 GHz emission is accounted for by 202 $\mu$Jy of AME (62% of the total), 87 $\mu$Jy of synchrotron (27%), and only 37 $\mu$Jy of free-free (11%) in this model. The greatly reduced free-free emission allows for the incorporation of dust emission at higher frequencies. In this scenario, the millimeter dust continuum and free-free emission contribute equally at 228 GHz. The 95% upper limit on dust emission at 353 GHz is 167 $\mu$Jy. The AME component is much broader ($W_{\rm AME} = 0.5$) and the peak frequency is shifted to 38 GHz. However, the quality of the fit is poorer even with the addition of the extra fitting parameter ($\chi^2 = 10.3$ fitting seven parameters to eleven data points). On the other hand, it would be surprising for NGC 4725B to lack millimeter dust emission entirely.

## Associated Molecular Gas: $^{12}$CO ($J=2\rightarrow1$)

In Figure [2](#fig:COextent), the $J=2\rightarrow1$ CO moment 0 contours are plotted on a *Spitzer*/IRAC 8 $\mu$m colorscale image extending out to the 20% level of the primary beam response, indicating a significant amount of molecular gas present in this vicinity of the star-forming disk. This is consistent with expectations based on existing lower resolution (i.e., $\theta_{1/2} \approx 13.4\ensuremath{''}$) $J=2\rightarrow1$ CO data (cite: heracles09). The molecular gas distribution loosely follows the 8 $\mu$m brightness, which is a tracer of small dust grains and polycyclic aromatic hydrocarbons (PAHs). Figure [1](#fig:radpan) shows a zoom-in of the $J=2\rightarrow1$ CO moment 0 contours overlaid on each of the radio and millimeter colorscale images.

The fact that the CO ($J=2\rightarrow1$) does not peak exactly at the location of continuum emission from NGC 4725 B on $\lesssim100$ pc scales is not surprising (cite: ejm15) given that the molecular gas has already been converted into stars, with plenty of additional gas nearby available for future star formation. The integrated line luminosity of the nearest CO feature $\approx260$ pc to the west of NGC 4725 B is $L_{\rm CO}^{\prime}\approx (2.2\pm0.23)\times10^{5}$ K km s$^{-1}$ pc$^{2}$. Assuming both a CO ($J=2\rightarrow1$)/CO ($J=1\rightarrow0$) brightness temperature ratio of $\sim$0.8 (cite: heracles09; lzk18) and $\alpha_{\rm CO} \approx 4.3$ $M_{\odot}\,{\rm (K\,km\,s^{-1}\,pc^{2})}^{-1}$ (cite: svb05; bwl13), the total nearby molecular gas reservoir is measured to be $M_{\rm H2}\gtrsim 1.2\times10^{6}\,M_{\odot}$.

For comparison, given the 3$\sigma$ upper-limit of $\lesssim 7.1 \times 10^{4}$ K km s$^{-1}$ pc$^{2}$ at the location of NGC 4725 B, the corresponding upper limit on the molecular gas mass is $M_{\rm H_{2}}\lesssim 3.8\times10^5\,M_{\odot}$.

# Discussion and Conclusions

We discuss here the possible origins of the emission observed from NGC 4725 B, including spinning dust emission in a massive cluster and synchrotron emission in a background radio source. Neither provides a completely satisfactory explanation of the spectrum and the apparent compactness.

## A Forming Massive Cluster?

### Cluster Properties

The new ALMA data presented in this study appear consistent with the conclusion of (cite: ejm18c) that NGC 4725 B is a nascent star-forming region, where massive stars are still highly enshrouded by their natal cocoons of gas and dust. The archival VLA data suggest the presence of synchrotron emission in addition to a significant amount of free-free emission, and thus an age of $\sim 3-5$ Myr.

Assuming that $\approx 50$% of the 14 GHz flux density arises from free-free emission, based on the best-fit model in the left panel of Figure [3](#fig:spec), suggests an ionizing photon rate of $Q(H^{0}) \approx 1.4\times10^{51}\,$s$^{-1}$ (cite: ejm11b), or $\approx 125$ O7V stars, where $Q(H^{0}) \approx 10^{49}\,$s$^{-1}$ per 37.7 $M_{\odot}$ O7V star (cite: sternberg03). Using a Kroupa initial mass function (cite: pk01) fully populated between 0.1 and 100 $M_{\odot}$ implies a total stellar mass of $M_{\star} \approx 6.4\times10^{4}\,M_{\odot}$ for NGC 4725 B. It is worth stressing that our results and conclusions remain qualitatively the same even if we were to instead use the best-fit model in the right panel of Figure [3](#fig:spec). In that case, the fraction of free-free emission at 14 GHz reduces to $\approx$20% of the total flux density, which in turn reduces the associated ionizing photon rate and stellar mass estimate by $\approx40\%$ \[i.e., $Q(H^{0}) \approx 5.9 \times 10^{50}\,$s$^{-1}$ and $M_{\star} \approx 2.6\times10^{4}\,M_{\odot}$\].

With a stellar mass of $\lesssim 10^{5}\,M_{\odot}$ located in a $\sim 2$ pc region, NGC 4725 B is best defined as a young massive star cluster (cite: pz10). In that context, we find that the mass NGC 4725 B is consistent with the upper-end of star cluster masses derived for other nearby galaxies (e.g., NGC 628 and M 51) as part of the Legacy Extragalactic UV Survey (cite: dc15). Further, the estimated cluster radius of $\sim 1$pc agrees with observations of the youngest YMCs studied in the LEGUS sample (cite: ryon17).

Finally, radial gradients in the maximum cluster mass have been observed for several nearby spiral galaxies, such that clusters with $M_{\star} \gtrsim 10^{4}\,M_{\odot}$ are found predominately within the central $\sim 2$ kpc (cite: aa17; mm18a). This is consistent with NGC 4725 B which is located at $\sim 1.9$ kpc from the nucleus of NGC 4725.

Using a combination of ALMA, *HST*, and VLA observations of the Antennae Galaxies, (cite: bcm14) developed a classification system for YMCs such that the presence and strength of different multiwavelength tracers of star formation activity can be used as an independent metric to age date star clusters. With bright and compact radio emission, a large inferred value for the dust attenuation, and the presence of nearby diffuse/faint CO (see Section [\[sec:molgas\]](#sec:molgas)), NGC 4725 B is classified as a stage 3 “emerging cluster," which places an upper-limit on the inferred cluster age of $\lesssim 3-5$ Myr. This is consistent with the age inferred from the radio emission alone.

During this phase of cluster evolution, the natal gas and dust surrounding the cluster is actively removed via feedback from stellar winds and UV radiation (cite: ll03). In this context, the lack of CO gas and millimeter dust emission observed is perhaps not that surprising or unexpected. Furthermore, while there is not a significant detection at the exact location of NGC 4725 B, the molecular gas appears to be in the immediate vicinity of NGC 4725 B (i.e., $\lesssim100$ pc) and could have fueled the nascent star formation in NGC 4725 B.

Assuming an age of $\sim 5$ Myr for the star formation and a distance of $\sim$100 pc to the nearby molecular gas reservoir suggests an asymmetric drift velocity of $\sim$20 km s$^{-1}$ between NGC 4725 B and the CO gas, which seems completely plausible (cite: Quirk19).

(cite: miura12) used CO observations of M 33 to classify giant molecular clouds (GMCs) into different evolutionary stages. Given the number of O7V stars estimated above, NGC 4725 B and the associated GMC would be classified as a stage “C" star-forming region with an age of $\sim 3-5$ Myr and a mean CO ($J=2\rightarrow1$) flux of $L_{\rm CO}^{\prime} \sim 7.2 \times 10^{4}$ K km s$^{-1}$ pc$^{2}$ with an associated standard deviation of $\sigma_{L^{\prime}_{\rm CO}} \sim 4.6\times 10^{4}$ K km s$^{-1}$ pc$^{2}$. Given the large dispersion, this value is consistent with our non-detection (i.e., $L_{\rm CO}^{\prime} \lesssim 7.1 \times 10^{4}$ K km s$^{-1}$ pc$^{2}$) at the location of NGC 4725 B.

### Molecular Gas Properties 

Let us assume that NGC 4725 B formed from a cloud of similar mass in the nearby molecular gas reservoir to the west (i.e., $M_{\rm H2} \approx 1.2\times10^{6}\,M_{\odot}$; see Section [3.3](#subsec:assoc_gas)) . Using (cite: ejm11b), we convert the value of $Q(H^{0})$ given above to a star formation rate of 0.010 $M_\odot$ yr$^{-1}$ for NGC 4725 B.

This implies a gas depletion time of $t_{\rm dep} \gtrsim 113$ Myr.

The gas depletion time inferred here is a factor of $\approx$4 shorter than that for starburst galaxies in the Great Observatories All-Sky LIRG Survey (cite: lee09; rhi19) and a factor of $\approx$16 shorter than that derived for resolved measurements on $60-120$ pc scales for normal star-forming galaxies included the Physics at High Angular Resolution in nearby Galaxies (PHANGS)-ALMA sample (cite: utomo18).

Assuming a constant 100 pc thickness of the molecular gas layer for this CO complex suggests a gravitational free-fall time of $t_{\rm ff}\sim 6$ Myr and a star formation efficiency per gravitational free-fall time of $\epsilon_{\rm ff}\sim 5\%$. The inferred values of $\tau_{\rm ff}$ and $\epsilon_{\rm ff}$ for the CO feature near NGC 4725 B are a factor of $\approx$2 shorter and a factor of $\approx$8 larger than the corresponding average values reported for the PHANGS-ALMA sample (cite: utomo18), respectively, suggesting relatively efficient star formation. This high star formation efficiency per gravitational free-fall time is further supported by taking the ratio of estimated stellar mass in NGC 4575 B to the nearby total molecular gas mass, which implies that $\lesssim 5\%$ of the gas has recently been converted into stars.

Simulations of turbulent, magnetized star-forming clouds (i.e., with a mass of $\sim 10^{5}\,M_{\odot}$) that include stellar radiation and outflow feedback predict a full range of $\epsilon_{\rm ff}$ spanning $\lesssim 1-100\%$. In these simulations $\epsilon_{\rm ff}$ is small at low densities. As mass flows rapidly into higher density regions within the cloud, $\epsilon_{\rm ff}$ approaches unity (cite: khullar19) with little time spent at intermediate densities. Therefore, the $\epsilon_{\rm ff}$ derived for NGC 4725 B may suggest that this object is being observed in a short-lived phase of its evolution.

In this context, it may not be unexpected that the AME signatures in this region are unique relative to the AME seen in our Galaxy. The Galaxy contains no YMCs with masses $\gtrsim 10^{5}\,M_{\odot}$, and if these particular properties of the AME are indeed associated with a short-lived period of massive cluster evolution, we would not expect to observe such interstellar medium conditions in our Galaxy.

### Physical Constraints on AME

Surprisingly, even with the addition of ALMA data at 92, 133, 203, and 221 GHz, there is no evidence for high-frequency thermal dust emission at these sensitivities. As discussed in Section [3.1](#subsec:model), we derive an upper limit (95% confidence) on the 353 GHz flux density from dust emission of 167 $\mu$Jy. To place this limit in context, we note that the Galaxy has a typical ratio of 30 GHz AME specific intensity to 353 GHz optical depth $\tau_{353}$ of 200 MJy sr$^{-1}$, whether in the diffuse interstellar medium or in cloud complexes like Perseus (cite: bh16; AME18). For an assumed dust temperature of 20 K and 1.85$''$ beam, our fit suggests $\tau_{353} < 4\times10^{-5}$. Combining this with a peak AME flux density of 208 $\mu$Jy yields a ratio of $6\times10^4$ MJy sr$^{-1}$, roughly 300 times larger than typically seen in the Galaxy. The maximum likelihood solution (left panel of Figure [3](#fig:spec)) invokes no dust emission at all, greatly exacerbating this discrepancy.

Given the surprising lack of millimeter dust emission inferred from the full model fit, we quantify the maximum permitted by the ALMA data without accounting for other emission mechanisms. Fitting just the 203 and 221 GHz ALMA observations with the modified blackbody dust model, we derive a 95% upper limit of 520 $\mu$Jy at 353 GHz. Even in this maximally conservative scenario, the ratio of AME to millimeter dust emission exceeds Galactic values by a factor of 100.

### Lack of Millimeter Dust Continuum

Emission from $\sim20\,$K grains is almost certainly present in the region based on much coarser far-infrared data, however it may be present only on much larger spatial scales that are invisible to the ALMA interferometric observations (i.e., $\gtrsim6\ensuremath{''}$). For instance, there is clearly widespread diffuse *Spitzer*/IRAC 8 $\mu$m emission all around the vicinity of NGC 4725 B (see Figure [2](#fig:COextent)), indicating the presence of small dust grains and PAHs. As was shown in (cite: ejm18c), there appear to be counterparts at the location of NGC 4725 B detected in IRAC maps both at 3.6 and 4.5 $\mu$m, indicating the presence of small/hot dust grains that could be powering the observed AME.

We measure a 3.6 $\mu$m flux density of 974 $\mu$Jy integrating in a $2.4\ensuremath{''}$ aperture and applying an aperture correction factor of 1.215 as given in Table 4.7 of the IRAC instrument handbook. In the 3.5 $\mu$m DIRBE band, (cite: Dwek1997) measured a typical dust emission per H-atom of $1.18\times10^{-23}$ MJy sr$^{-1}$ H$^{-1}$ while (cite: Planck_Int_XVII) measured a value of $6.7\times10^{-24}$ MJy sr$^{-1}$ H$^{-1}$ at 100 GHz. If this ratio of mid-infrared to millimeter emission holds for NGC 4725 B, we would expect 550 $\mu$Jy of dust emission at 100 GHz, well in excess of the total observed emission ($\sim130\,\mu$Jy). The differing resolutions of the *Spitzer* and ALMA data and the imperfect correspondence between the IRAC and DIRBE bandpasses may account for some of this discrepancy. However, it is likely that the radiation field is stronger in NGC 4725B than on a typical diffuse Galactic sightline. A factor of $\sim 5$ difference in the ratio of PAH to submillimeter emission could be accommodated by a factor of $\sim 5$ difference in the strength of the intensity of starlight heating the grains. Thus, the lack of submillimeter continuum at the current sensitivity limits is not implausible given the observed PAH emission in the vicinity of this region.

NGC 4725B lacks not only dust continuum detectable at these sensitivities, but also any appreciable CO emission. In Section [3.3](#subsec:assoc_gas), we found that the upper limit on $^{12}$CO ($J=2\rightarrow1$) implies $M_{{\rm H}_2} \lesssim 3.8\times10^5\,$M$_\odot$. At 230 GHz, the (cite: dl07) dust model emits $2.1\times10^{-27}$ erg s$^{-1}$ H$^{-1}$ when illuminated by starlight characteristic of the diffuse Galactic ISM. Using this emissivity, $4\times10^5\,$M$_\odot$ of gas at a distance of 11.9 Mpc corresponds to only 26 $\mu$Jy of continuum emission at 230 GHz. Thus, the upper limit on the gas mass implied by the non-detection of CO is completely consistent with the lack of observed dust emission.

On the basis of these arguments, the lack of millimeter dust continuum is completely consistent with the observed synchrotron, free-free, CO, and PAH emission in NGC 4725 B, supporting the interpretation that this object is a massive cluster within the galaxy disk. However, this scenario does not readily explain the peaked 30 GHz emission. If it is attributed to spinning dust grains, then the millimeter dust continuum should be roughly two orders of magnitude brighter than observed.

## A Background Source?

The compact nature of NGC 4725 and extreme ratio of 30 GHz AME relative to 353 GHz dust emission are clearly at odds with expectations from spinning dust emission. However, as discussed in (cite: ejm18c), attributing NGC 4725 B to a chance background galaxy is also problematic, though cannot be completely ruled out. First, there are no known submillijansky radio sources that peak at such high frequencies. And, while the submillijansky extragalacitc sky at $\gtrsim 30$ GHz is not well known, naively extrapolating from existing number counts (cite: massardi11; ejm18b) suggest that finding a source with a rising spectrum between 5 and 20 GHz given the SFRS survey area is unlikely (cite: ejm18c). This is a conservative upper limit given that this estimate both assumes uniform noise in the SFRS survey area and uses the full sample of (cite: massardi11), which also finds that the fraction of sources with rising spectra decreases with decreasing flux density. For example, applying an average primary beam correction to the SFRS noise and extrapolating from the fraction of sources with rising spectra between 5 and 20 GHz in their lowest flux density bin (i.e., $40 \leq S_{\rm 20\,GHz} < 100$ mJy, which is still more than 100$\times$ brighter than NGC 4725 B) decreases the likelihood of finding such a source to $<10$%. Assuming this trend continues, this would then suggest an even lower likelihood of finding such a source given the 22 GHz flux density of NGC 4725 B (i.e., $S_{\rm 22\,GHz} \approx 300\,\mu$Jy).

The spectrum of NGC 4725 B also seems much too sharply peaked to be explained by a “classical" (synchrotron-self absorbed) gigahertz-peaked spectrum (GPS) radio galaxy (cite: ERA). Furthermore, if the source were a GPS source at redshift $z\approx1$ with a turnover frequency of 31.6 GHz (i.e., 63.2 GHz in the source frame) and a corresponding flux density of $\sim365\,\mu$Jy, the empirical turnover-size relation given by (cite: Orienti14) suggests a physical diameter of $D \approx 0.4$ pc. This would then imply an internal magnetic field strength of $\sim6\times10^{5}$ G (cite: ERA), which is extraordinarily large. Assuming a spherical source, the corresponding magnetic energy \[$E_{B} = U_{B}V$, where $U_{B} = B^2/(8\pi)$ is the magnetic energy density and $V$ is the source volume\] would be $\sim 1.1 \times 10^{64}$ erg, exceeding the gravitational binding energy ($E_{G} \approx 2GM^2/D$) unless the enclosed mass was $M > 1.6\times10^{11}\,M_{\odot}$! While this empirical turnover-size relation was derived for sources with typical flux densities as large as $\sim100\,$mJy (i.e., $\sim$300$\times$ larger than NGC 4725 B), by locating it at $z\approx1$, its rest-frame 5 GHz spectral luminosity would be consistent with the low luminosity end of the core emission in that sample (i.e., $L_{\rm 5\,GHz} \sim 1.1\times 10^{24}$ W Hz$^{-1}$). Thus, such a scenario seems implausible.

Although it remains possible that NGC 4725 B is a new class of compact, optically-faint, $\sim30$ GHz peaking radio galaxy, on the basis of these arguments it still seems most likely that it is located in the disk of NGC 4725. Future high resolution (i.e., $\lesssim 0.01\ensuremath{''}$) radio imaging may be able to discriminate between these scenarios.

## Final Thoughts

While the expectation was that these new ALMA data would help definitively characterize the physical conditions of NGC 4725 B and explain why there is such a strong presence of AME, they have in fact raised further questions. It is extraordinary that NGC 4725 B has strongly peaked emission at $\approx1$ cm without any detectable dust emission at millimeter wavelengths.

If the excess 30 GHz emission is being produced by spinning ultrasmall grains, the extreme ratio of 30 GHz AME relative to 353 GHz dust emission suggests, at minimum, substantial differences in the small grain population in this region with respect to those in Galactic AME regions. Models of Galactic dust that reproduce both far-infrared emission and AME require at least $\sim$5% of the dust mass to reside in grains $\lesssim1$ nm in size (cite: dl98b; Hoang16; hd17). Thus, a factor of $\sim$300 enhancement in the 30 GHz emissivity relative to diffuse Galactic sightlines could not be achieved even if 100% of the dust mass were in nanoparticles. Other factors would be required, such as grains having much larger typical electric dipole moments while maintaining comparable rotation frequencies. Another possibility might be a scenario in which all of the grains were reduced to a sufficiently small size ($\lesssim 5\,$nm) as not to emit efficiently at long wavelengths. While not completely implausible, these considerations cast doubt on a spinning dust origin of the 30 GHz emission.

Alternatively, an emission mechanism such as thermal magnetic dipole emission (cite: dl99; dh13) might produce elevated 30 GHz relative to 353 GHz emission through systematic changes in the physical properties of the grains. However, such an explanation would require significant fine-tuning of the dust optical properties and aspect ratios to achieve such strong ferromagnetic resonance behavior, and we thus consider it unlikely.

At this point, it seems that more observations are required to make further progress on determining the true physical nature of this source and why there appears to be such strong AME. For instance, significantly deeper, high angular resolution VLA/VLBA and ALMA data should help to better constrain the spectrum (e.g., determine if the ALMA measurements are completely dominated by pure free-free emission) and angular extent of NGC 4725 B. Looking toward the future, next-generation ground- and space-based facilities should contribute substantially to such studies. A next-generation VLA (cite: ngvla-sci; ngvla-astro2020), delivering an order of magnitude improvement and in sensitivity and angular resolution than the existing VLA, will be highly optimized in studying faint sources like NGC 4725 B at frequencies spanning $\sim1.2-116$ GHz.

While future far-infrared measurements at a high enough angular resolution to constrain the total infrared emission from NGC 4725 B will need to wait a decade or more for a space-based telescope, such as the currently conceived *Origins Space Telescope*, observing the 3.3 and 3.4 $\mu$m hydrocarbon features with the Near-Infrared Spectrograph on board the *James Webb Space Telescope* could help shed critically needed light on potential AME carriers.

# Acknowledgments

We would like to thank the anonymous referee for comments that helped to improve the content and presentation of this letter. E.J.M thanks J.J. Condon for useful discussions that helped improve the paper. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01826.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# Software

APLpy (cite: aplpy2012; aplpy2019), CASA (cite: casa), `corner` (cite: corner), `emcee` (cite: emcee), Matplotlib (cite: Matplotlib), NumPy (cite: NumPy)

natexlab

(ref: aa17) Adamo, A., Ryon, J. E., Messa, M., et al. 2017, ApJ, 841, 131, doi: [`10.3847/1538-4357/aa7132`](http://doi.org/10.3847/1538-4357/aa7132)

(ref: ahd09) Ali-Haïmoud, Y., Hirata, C. M., & Dickinson, C. 2009, MNRAS, 395, 1055, doi: [`10.1111/j.1365-2966.2009.14599.x`](http://doi.org/10.1111/j.1365-2966.2009.14599.x)

(ref: lee09) Armus, L., Mazzarella, J. M., Evans, A. S., et al. 2009, PASP, 121, 559, doi: [`10.1086/600092`](http://doi.org/10.1086/600092)

(ref: Battistelli_2019) Battistelli, E. S., Fatigoni, S., Murgia, M., et al. 2019, ApJL, 877, L31, doi: [`10.3847/2041-8213/ab21de`](http://doi.org/10.3847/2041-8213/ab21de)

(ref: bwl13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: dc15) Calzetti, D., Lee, J. C., Sabbi, E., et al. 2015, AJ, 149, 51, doi: [`10.1088/0004-6256/149/2/51`](http://doi.org/10.1088/0004-6256/149/2/51)

(ref: cepeda2020) Cepeda-Arroita, R., Harper, S., Dickinson, C., et al. 2020, arXiv e-prints, arXiv:2001.07159. [`https://arxiv.org/abs/2001.07159`](https://arxiv.org/abs/2001.07159)

(ref: jc97) Condon, J. J. 1997, PASP, 109, 166, doi: [`10.1086/133871`](http://doi.org/10.1086/133871)

(ref: ERA) Condon, J. J., & Ransom, S. M. 2016, Essential Radio Astronomy

(ref: mfs1) Conway, J. E., Cornwell, T. J., & Wilkinson, P. N. 1990, MNRAS, 246, 490

(ref: msclean) Cornwell, T. J. 2008, IEEE Journal of Selected Topics in Signal Processing, 2, 793, doi: [`10.1109/JSTSP.2008.2006388`](http://doi.org/10.1109/JSTSP.2008.2006388)

(ref: cd09) Dickinson, C., Davies, R. D., Allison, J. R., et al. 2009, ApJ, 690, 1585, doi: [`10.1088/0004-637X/690/2/1585`](http://doi.org/10.1088/0004-637X/690/2/1585)

(ref: AME18) Dickinson, C., Ali-Haïmoud, Y., Barr, A., et al. 2018, New A Rev., 80, 1, doi: [`10.1016/j.newar.2018.02.001`](http://doi.org/10.1016/j.newar.2018.02.001)

(ref: draine2011) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium (Princeton, NJ: Princeton University Press)

(ref: dh13) Draine, B. T., & Hensley, B. 2013, ApJ, 765, 159, doi: [`10.1088/0004-637X/765/2/159`](http://doi.org/10.1088/0004-637X/765/2/159)

(ref: dl98b) Draine, B. T., & Lazarian, A. 1998, ApJ, 508, 157, doi: [`10.1086/306387`](http://doi.org/10.1086/306387)

(ref: dl99) —. 1999, ApJ, 512, 740, doi: [`10.1086/306809`](http://doi.org/10.1086/306809)

(ref: dl07) Draine, B. T., & Li, A. 2007, ApJ, 657, 810, doi: [`10.1086/511055`](http://doi.org/10.1086/511055)

(ref: Dwek1997) Dwek, E., Arendt, R. G., Fixsen, D. J., et al. 1997, ApJ, 475, 565, doi: [`10.1086/303568`](http://doi.org/10.1086/303568)

(ref: wce57) Erickson, W. C. 1957, ApJ, 126, 480, doi: [`10.1086/146421`](http://doi.org/10.1086/146421)

(ref: corner) Foreman-Mackey, D. 2016, The Journal of Open Source Software, 1, 24, doi: [`10.21105/joss.00024`](http://doi.org/10.21105/joss.00024)

(ref: emcee) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: hkp01) Freedman, W. L., Madore, B. F., Gibson, B. K., et al. 2001, ApJ, 553, 47, doi: [`10.1086/320638`](http://doi.org/10.1086/320638)

(ref: greaves18) Greaves, J. S., Scaife, A. M. M., Frayer, D. T., et al. 2018, Nature Astronomy, 2, 662, doi: [`10.1038/s41550-018-0495-z`](http://doi.org/10.1038/s41550-018-0495-z)

(ref: bh15) Hensley, B., Murphy, E., & Staguhn, J. 2015, MNRAS, 449, 809, doi: [`10.1093/mnras/stv287`](http://doi.org/10.1093/mnras/stv287)

(ref: hd17) Hensley, B. S., & Draine, B. T. 2017, ApJ, 836, 179, doi: [`10.3847/1538-4357/aa5c37`](http://doi.org/10.3847/1538-4357/aa5c37)

(ref: bh16) Hensley, B. S., Draine, B. T., & Meisner, A. M. 2016, ApJ, 827, 45, doi: [`10.3847/0004-637X/827/1/45`](http://doi.org/10.3847/0004-637X/827/1/45)

(ref: rhi19) Herrero-Illana, R., Privon, G. C., Evans, A. S., et al. 2019, A&A, 628, A71, doi: [`10.1051/0004-6361/201834088`](http://doi.org/10.1051/0004-6361/201834088)

(ref: hoang11) Hoang, T., Lazarian, A., & Draine, B. T. 2011, ApJ, 741, 87, doi: [`10.1088/0004-637X/741/2/87`](http://doi.org/10.1088/0004-637X/741/2/87)

(ref: Hoang16) Hoang, T., Vinh, N.-A., & Quynh Lan, N. 2016, ApJ, 824, 18, doi: [`10.3847/0004-637X/824/1/18`](http://doi.org/10.3847/0004-637X/824/1/18)

(ref: Matplotlib) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: kf11) Kennicutt, R. C., Calzetti, D., Aniano, G., et al. 2011, PASP, 123, 1347, doi: [`10.1086/663818`](http://doi.org/10.1086/663818)

(ref: rck03) Kennicutt, Jr., R. C., Armus, L., Bendo, G., et al. 2003, PASP, 115, 928, doi: [`10.1086/376941`](http://doi.org/10.1086/376941)

(ref: khullar19) Khullar, S., Krumholz, M. R., Federrath, C., & Cunningham, A. J. 2019, MNRAS, 488, 1407, doi: [`10.1093/mnras/stz1800`](http://doi.org/10.1093/mnras/stz1800)

(ref: ak96b) Kogut, A., Banday, A. J., Bennett, C. L., et al. 1996, ApJL, 464, L5, doi: [`10.1086/310072`](http://doi.org/10.1086/310072)

(ref: pk01) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: ll03) Lada, C. J., & Lada, E. A. 2003, ARA&A, 41, 57, doi: [`10.1146/annurev.astro.41.011802.094844`](http://doi.org/10.1146/annurev.astro.41.011802.094844)

(ref: eml97) Leitch, E. M., Readhead, A. C. S., Pearson, T. J., & Myers, S. T. 1997, ApJL, 486, L23, doi: [`10.1086/310823`](http://doi.org/10.1086/310823)

(ref: heracles09) Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137, 4670, doi: [`10.1088/0004-6256/137/6/4670`](http://doi.org/10.1088/0004-6256/137/6/4670)

(ref: stl20) Linden, S. T., Murphy, E. J., Dong, D., et al. 2020, ApJS, 248, 25, doi: [`10.3847/1538-4365/ab8a4d`](http://doi.org/10.3847/1538-4365/ab8a4d)

(ref: massardi11) Massardi, M., Ekers, R. D., Murphy, T., et al. 2011, MNRAS, 412, 318, doi: [`10.1111/j.1365-2966.2010.17917.x`](http://doi.org/10.1111/j.1365-2966.2010.17917.x)

(ref: ngvla-astro2020) McKinnon, M., Beasley, A., Murphy, E., et al. 2019, in BAAS, Vol. 51, 81

(ref: casa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mm18a) Messa, M., Adamo, A., Calzetti, D., et al. 2018, MNRAS, 477, 1683, doi: [`10.1093/mnras/sty577`](http://doi.org/10.1093/mnras/sty577)

(ref: miura12) Miura, R. E., Kohno, K., Tosaki, T., et al. 2012, ApJ, 761, 37, doi: [`10.1088/0004-637X/761/1/37`](http://doi.org/10.1088/0004-637X/761/1/37)

(ref: jm10) Moustakas, J., Kennicutt, Jr., R. C., Tremonti, C. A., et al. 2010, ApJS, 190, 233, doi: [`10.1088/0067-0049/190/2/233`](http://doi.org/10.1088/0067-0049/190/2/233)

(ref: ejm18b) Murphy, E. J., & Chary, R.-R. 2018, ApJ, 861, 27, doi: [`10.3847/1538-4357/aac2b6`](http://doi.org/10.3847/1538-4357/aac2b6)

(ref: ejm18a) Murphy, E. J., Dong, D., Momjian, E., et al. 2018a, ApJS, 234, 24, doi: [`10.3847/1538-4365/aa99d7`](http://doi.org/10.3847/1538-4365/aa99d7)

(ref: ejm18c) Murphy, E. J., Linden, S. T., Dong, D., et al. 2018b, ApJ, 862, 20, doi: [`10.3847/1538-4357/aac5f5`](http://doi.org/10.3847/1538-4357/aac5f5)

(ref: ejm10) Murphy, E. J., Helou, G., Condon, J. J., et al. 2010, ApJL, 709, L108, doi: [`10.1088/2041-8205/709/2/L108`](http://doi.org/10.1088/2041-8205/709/2/L108)

(ref: ejm11b) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67, doi: [`10.1088/0004-637X/737/2/67`](http://doi.org/10.1088/0004-637X/737/2/67)

(ref: ejm15) Murphy, E. J., Dong, D., Leroy, A. K., et al. 2015, ApJ, 813, 118, doi: [`10.1088/0004-637X/813/2/118`](http://doi.org/10.1088/0004-637X/813/2/118)

(ref: ngvla-sci) Murphy, E. J., Bolatto, A., Chatterjee, S., et al. 2018c, in Astronomical Society of the Pacific Conference Series, Vol. 517, Science with a Next Generation Very Large Array, ed. E. Murphy, 3. [`https://arxiv.org/abs/1810.07524`](https://arxiv.org/abs/1810.07524)

(ref: nkw97) Niklas, S., Klein, U., & Wielebinski, R. 1997, A&A, 322, 19

(ref: Orienti14) Orienti, M., & Dallacasa, D. 2014, MNRAS, 438, 463, doi: [`10.1093/mnras/stt2217`](http://doi.org/10.1093/mnras/stt2217)

(ref: plsd11) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2011, A&A, 536, A20, doi: [`10.1051/0004-6361/201116470`](http://doi.org/10.1051/0004-6361/201116470)

(ref: Planck_Int_XVII) Planck Collaboration Int. XVII. 2014, A&A, 566, A55, doi: [`10.1051/0004-6361/201323270`](http://doi.org/10.1051/0004-6361/201323270)

(ref: Planck_Int_XXII) Planck Collaboration Int. XXII. 2015, A&A, 576, A107, doi: [`10.1051/0004-6361/201424088`](http://doi.org/10.1051/0004-6361/201424088)

(ref: Planck_2018_XI) Planck Collaboration XI. 2018, arXiv e-prints, arXiv:1801.04945. [`https://arxiv.org/abs/1801.04945`](https://arxiv.org/abs/1801.04945)

(ref: pz10) Portegies Zwart, S. F., McMillan, S. L. W., & Gieles, M. 2010, ARA&A, 48, 431, doi: [`10.1146/annurev-astro-081309-130834`](http://doi.org/10.1146/annurev-astro-081309-130834)

(ref: Quirk19) Quirk, A., Guhathakurta, P., Chemin, L., et al. 2019, ApJ, 871, 11, doi: [`10.3847/1538-4357/aaf1ba`](http://doi.org/10.3847/1538-4357/aaf1ba)

(ref: msmfs) Rau, U., & Cornwell, T. J. 2011, A&A, 532, A71, doi: [`10.1051/0004-6361/201117104`](http://doi.org/10.1051/0004-6361/201117104)

(ref: aplpy2019) Robitaille, T. 2019, APLpy v2.0: The Astronomical Plotting Library in Python, doi: [`10.5281/zenodo.2567476`](http://doi.org/10.5281/zenodo.2567476)

(ref: aplpy2012) Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python, Astrophysics Source Code Library. [`http://ascl.net/1208.017`](http://ascl.net/1208.017)

(ref: ryon17) Ryon, J. E., Gallagher, J. S., Smith, L. J., et al. 2017, ApJ, 841, 92, doi: [`10.3847/1538-4357/aa719e`](http://doi.org/10.3847/1538-4357/aa719e)

(ref: mfs2) Sault, R. J., & Wieringa, M. H. 1994, A&AS, 108, 585

(ref: as10) Scaife, A. M. M., Nikolic, B., Green, D. A., et al. 2010, MNRAS, 406, L45, doi: [`10.1111/j.1745-3933.2010.00878.x`](http://doi.org/10.1111/j.1745-3933.2010.00878.x)

(ref: sah11) Silsbee, K., Ali-Haïmoud, Y., & Hirata, C. M. 2011, MNRAS, 411, 2750, doi: [`10.1111/j.1365-2966.2010.17882.x`](http://doi.org/10.1111/j.1365-2966.2010.17882.x)

(ref: svb05) Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677, doi: [`10.1146/annurev.astro.43.051804.102221`](http://doi.org/10.1146/annurev.astro.43.051804.102221)

(ref: sternberg03) Sternberg, A., Hoffmann, T. L., & Pauldrach, A. W. A. 2003, ApJ, 599, 1333, doi: [`10.1086/379506`](http://doi.org/10.1086/379506)

(ref: stevenson2014) Stevenson, M. A. 2014, ApJ, 781, 113, doi: [`10.1088/0004-637X/781/2/113`](http://doi.org/10.1088/0004-637X/781/2/113)

(ref: tibbs11) Tibbs, C. T., Flagey, N., Paladini, R., et al. 2011, MNRAS, 418, 1889, doi: [`10.1111/j.1365-2966.2011.19605.x`](http://doi.org/10.1111/j.1365-2966.2011.19605.x)

(ref: utomo18) Utomo, D., Sun, J., Leroy, A. K., et al. 2018, ApJL, 861, L18, doi: [`10.3847/2041-8213/aacf8f`](http://doi.org/10.3847/2041-8213/aacf8f)

(ref: NumPy) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science and Engineering, 13, 22, doi: [`10.1109/MCSE.2011.37`](http://doi.org/10.1109/MCSE.2011.37)

(ref: bcm14) Whitmore, B. C., Brogan, C., Chandar, R., et al. 2014, ApJ, 795, 156, doi: [`10.1088/0004-637X/795/2/156`](http://doi.org/10.1088/0004-637X/795/2/156)

(ref: lzk18) Zschaechner, L. K., Bolatto, A. D., Walter, F., et al. 2018, ApJ, 867, 111, doi: [`10.3847/1538-4357/aadf32`](http://doi.org/10.3847/1538-4357/aadf32)

In Figure [4](#fig:triangle), we present the full posteriors for all seven parameters in the model described in Section [3.1](#subsec:model).

![](triangle_opticallythick_synch_dust.pdf)

[^1]: <http://library.nrao.edu/public/memos/evla/EVLAM_195.pdf>

</paper>

Write the methods card for this paper.