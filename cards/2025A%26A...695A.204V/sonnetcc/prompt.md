# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...695A.204V\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...695A.204V",
 "title": "Quantifying the detection likelihood of faint peaks in interferometric data through jackknifing: Test application on finding z &gt; 10 galaxy candidates",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "van Marrewijk, Joshiwa",
 "n_authors": 9,
 "arxiv_id": "2501.03150",
 "doi": "10.1051/0004-6361/202451927",
 "alma_projects_linked_by_archive": [
  "2021.A.00020.S",
  "2021.A.00023.S",
  "2021.A.00031.S",
  "2023.A.00017.S",
  "2023.A.00037.S"
 ]
}
```

Paper text:
<paper>
# Quantifying the detection likelihood of faint peaks in interferometric data through jackknifing

# Introduction

+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Archival ALMA observations of $z>10$ galaxy candidates**                                                                                                                                                                                                                     |
+:==================================+:=====================================================================================================================:+:========================================================:+:=======================================================:+
| **ID**                            | GLASS-z12                                                                                                             | GLASS-z10                                                | S5-z17-1                                                |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| RA \[deg\]                        | 3.4990                                                                                                                | 3.5119                                                   | 339.0160                                                |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| DEC \[deg\]                       | -30.3248                                                                                                              | -30.3719                                                 | 33.9046                                                 |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| ALMA source name                  | GLASS-z13 \[GLASS-z12\]                                                                                               | GLz11                                                    | S5-z17-1                                                |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| PI                                | T. Bakx \[J. Zavala\]                                                                                                 | I. Yoon                                                  | S. Fujimoto                                             |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| ALMA Project Code                 | 2021.A.00020.S \[2023.A.00017.S\]                                                                                     | 2021.A.00023.S                                           | 2021.A.00031.S                                          |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| ALMA Band                         | 6 \[6\]                                                                                                               | 7                                                        | 7                                                       |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| Beam \[$''$\]                     | $0.32\ensuremath{''}\times0.29\ensuremath{''}, 46^\circ$ \[$0.45\ensuremath{''}\times0.40\ensuremath{''}, 73^\circ$\] | $0.77\ensuremath{''}\times0.59\ensuremath{''}, 81^\circ$ | $0.78\ensuremath{''}\times0.45\ensuremath{''}, 3^\circ$ |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| Channel width \[MHz\]             | 31 \[31\]                                                                                                             | 31                                                       | 31                                                      |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| On source time \[h\]              | 8.1 \[1.6\]                                                                                                           | 6.9                                                      | 0.5                                                     |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| **Reported tentative detections** |                                                                                                                       |                                                          |                                                         |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| Ref. for initial identification   | (cite: Castellano2022),(cite: Naidu2022)                                                                              | (cite: Naidu2022)                                        | (cite: Harikane2023)                                    |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| Reference for ALMA data           | (cite: Bakx2023), (cite: Zavala2024b; Zavala2024)$^\dagger$                                                           | (cite: Yoon2023)                                         | (cite: Fujimoto2023)                                    |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| $z_\mathrm{phot}$                 | $12.2\pm 0.2$                                                                                                         | $10.4\pm 0.5$                                            | $16.7^{+1.9}_{-0.3}$                                    |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| $\Delta z$ covered                | $11.9 - 13.5$                                                                                                         | $10.1 - 11.1$                                            | $16.1 - 17.3$                                           |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| S/N (\[O III\] 88 μm )$^{*}$      | 5.8, 3                                                                                                                | 4.4                                                      | 5.1                                                     |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| Offset                            | $0.5\ensuremath{''}$, \[$0.0\ensuremath{''}$\]                                                                        | $0.17\ensuremath{''}$                                    | –                                                       |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| $z_\mathrm{spec}^{ALMA}$          | $12.117 \pm 0.001$, \[$12.3327 \pm 0.0035$\]                                                                          | 10.38                                                    | 16.01                                                   |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| $z_\mathrm{spec}^{JWST}$          | $12.33 \pm 0.02$                                                                                                      | –                                                        | –                                                       |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| Freq \[GHz\]                      | 258.7 , \[$254.487 \pm 0.019$\]                                                                                       | 298.25                                                   | 338.726                                                 |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+
| $\Delta \nu$ \[km s$^{-1}$\]      | $400\pm 70$, \[$186\pm 58$\]                                                                                          | 225                                                      | 118                                                     |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+---------------------------------------------------------+

Assessing the reliability of faint astronomical signals is essential for all areas of astrophysics and cosmology. To understand the entirety of a population, the astronomical community is always attempting to characterize sources at the limits of what can be observed with the current generation of facilities. Interferometers such as the Atacama Large Millimeter/Submillimeter Array (ALMA) and the Very Large Array (VLA) have enabled the efficient study of faint, distant sources in the mm/cm-wave regime. However, images generated from interferometric data are highly complex; their underlying noise distribution is challenging to quantify, leading to potential biases at low $S/N$ and difficulties in interpreting the data. This can have profound consequences, for example, when determining the existence, redshift, and physical properties of faint galaxies.

Correctly determining the likelihood of faint peaks in interferometric data has become relevant in the context of studies of the interstellar medium in the first galaxies ($z>10$). Over the past two years, six ALMA Director’s Discretionary Time (DDT) programs[^1] were approved and executed to follow up $z>10$ galaxy candidates. These galaxies were initially identified from optical and near-infrared photometry, mostly including data from the JWST. However, modeling the spectral line energy distribution of these photometric data resulted in a wide redshift probability distribution, including several potential solutions. Capitalizing on the broad spectral coverage of ALMA, these DDT programs aimed to confirm the redshifts of the galaxy candidates by targeting the \[O III\] 88 μm line. But, obtaining robust line detections with an accurate $S/N$ estimate has proven challenging.

So far, ALMA DDT observations of $z>10$ candidates have resulted in a handful of potential upper limits on the targeted line emission (cite: Popping2023; Kaasinen2023) and marginal, low $S/N$ ($3-4\sigma$) detections of \[O III\] 88 μm (see, (cite: Harikane2022; Yoon2023; Bakx2023; Fujimoto2023)), with the exception of one source, JADES-GS-z14, for which a $6\sigma$ detection of the \[O III\] 88 μm line was recently reported (cite: Carniani2024b; Carniani2024; Schouws2024). Some of these marginal detections have since been proven not to correspond to actual emission lines, with follow-up JWST/MRS and JWST/NIRSpec spectra revealing at least two of these galaxies to be at a different redshift to that implied by the initial false positive \[O III\] 88 μm  detection (cite: Zavala2024; Harikane2024b). This highlights a broader issue: false positive identifications of emission lines lead to biases in the derived physical properties. In the case of incorrect redshift solutions, this has profound implications for the number counts of the earliest galaxies, thereby impacting our understanding of both cosmology and galaxy evolution.

In this work, we present a straightforward and effective technique to quantify the detection level and underlying noise distribution in interferometric data sets. We build upon the approach used in (cite: Kaasinen2023); by differencing the visibilities, we generate various noise realizations of the observation-specific ALMA measurement set. Then, by applying line-finding algorithms on both the real and source-free image cubes, we sample the likelihood of a marginal detection being real without needing to assume an underlying noise distribution. We make our technique readily available to the community in the form of the public tool `jackknify`, along with clear, step-by-step tutorials.[^2] Although we implement and optimize the tool for ALMA data, `jackknify` is compatible with any type of interferometric observations that use the *Common Astronomy Software Applications for Radio Astronomy* (cite: CASA2022). For example, this jackknifing technique may be useful for characterizing the faint HI emission from $z>1$ galaxies using Squared Kilometer Array (cite: Dewdney2009) and its precursors (cite: Baker2024),[^3] or quantifying the faint molecular line emission from quiescent galaxies with ALMA. In this work, we apply `jackknify` to three archival DDT observations targeting $z>10$ galaxy candidates. We will test two scenarios: one in which no prior knowledge regarding the source’s redshift is available and one in which we can use a prior from JWST on the frequency location of the line.

The paper is outlined as follows. Section [2](#sec:observations) describes which interferometric data sets we use, Section [3](#sec:jack_knife) provides the overview of how `jackknify` is built, Section [4](#sec:results_sims) describes the performance of the tool via simulated observations, Section [5](#sec:results) contains the results of applying `jackknify` to the ALMA observations of $z>10$ galaxy candidates, and Section [6](#sec:summary) provides an overview and summary of this work. For all calculations, the assumed cosmology is based on (cite: Planck2014_XIII), a spatially flat, $\Lambda$ cold dark matter ($\Lambda$CDM) model with $H_0=67.7$  kms$^{-1}$ Mpc$^{-1}$ and $\Omega_{\rm m} = 0.307$.

# The archival ALMA observations

We test and validate our jackknifing tool, `jackknify`, on three sets of ALMA DDT observations targeting $z>10$ galaxy candidates pre-identified from photometry (cite: Castellano2022; Naidu2022; Harikane2023). All of these DDT observations (cite: Bakx2023; Yoon2023; Fujimoto2023) aimed to detect the \[O III\] 88 μm emission line over a wide redshift probability range. To maximize the redshift coverage, each spectral setup consisted of four adjacent tunings, covering a large, $\approx 30$ GHz bandwidth. A comprehensive overview of the literature results and observational specifics is presented in Table [\[tab:observations\]](#tab:observations).

Calibrated measurement sets were provided by the European ALMA Regional Centre network (cite: Hatziminaoglou2015) through the calMS service (cite: Petry2020) using CASA v5.4.0. To reduce the data size, we performed two additional operations on the calibrated data, applying a time averaging of 30 seconds and spectral averaging of the visibilities in $\approx 30$ MHz bins. The frequency binning was conducted in a manner that avoided interpolation over the frequency axis. We used `uvcontsub` to manually continuum subtract a first-order polynomial from the measurement sets to remove any potential continuum emitters. We omitted the frequency channels where tentative features might be present in the data based on the previously reported detections. Finally, we imaged all measurement sets using the TCLEAN task with natural weighting.

# Methodology

## Jackknifing

![](figures/noise.pdf)

In the narrow-field approximation, interferometers measure the 2D Fourier transform of the intensity distribution of an astronomical source over a sparse collection of Fourier modes. Such measurement modes, called visibilities, have units of wavenumbers and are expressed in terms of *uv*-distances, where $u$ and $v$ are the orthogonal vector bases of the Fourier space. Assuming proper calibration[^4], noise in the Fourier domain, unlike in the image plane, is additive and Gaussian. This occurs because the individual pulses from electrons are so numerous that they blend into an indistinguishable, continuous Gaussian random process with a mean of zero (cite: Thompson2017).

In this work, we use jackknifing to characterize the noise properties of the data. Jackknifing is a common technique used to retrieve the noise properties from bolometric measurements taken with mm-wave single-dish facilities. It is most commonly employed on Cosmic Microwave Background (CMB)/Single dish experiment observations (cite: Weiss2009; Romero2018; Naess2020); however, it has also been used extensively to characterize radio/mm-wave interferometric data (cite: Padin2001; Readhead2004; Sharp2010; Keating2015). Since interferometric data has uncorrelated, additive, and Gaussian noise with a mean of zero, we can retrieve the uncorrelated noise distribution, $n$, from the data, $d$, by jackknifing – by randomly multiplying half of the real and imaginary amplitudes of the visibilities by -1 and then rebinning, thereby averaging out the signal, $s$ (cite: Kitayama2020; GonzalezL2020; Kaasinen2023; DiMascolo2023).

When visibilities are imaged, the $uv$-data is automatically rebinned and averaged since all imaging and deconvolution tools, including `tclean`, grid the $uv$-coordinates before Fourier transforming. Any artifacts caused by the imaging, such as spatially correlated noise, are captured by performing the jackknifing in the visibility plane and performing the inference in the image plane. Jackknifing in the visibility plane is thus essential, rather than splitting in the image plane, to avoid removing any correlated noise induced by the Fourier transform present in the data.

To generate various noise realizations, we change the seeding of the randomization process. This allows us to sample the noise distribution, $n$, until convergence. Once $n$ is adequately sampled, we use the distribution to infer the likelihood of false detection. Figure [1](#fig:schematic) shows schematically how this type of detection inference works. Given that the data, $d$, is a linear combination of the noise distribution, $n$, plus the signal, $s$, we can define the likelihood of detection $\mathcal{L_{\rm D}}(\gamma)$ by integrating from an arbitrary $S/N$ threshold, $\gamma$, onward, as indicated with the shaded area in Figure [1](#fig:schematic). By nullifying $s$ through jackknifing of $d$, we recover $n$ in the visibility plane and thus are able to compute the likelihood of a false positive detection $\mathcal{L_{\rm FD}}(\gamma)$. The ratio of the two likelihoods provides the significance of detection.

Resampling the noise distributions requires that the cubes are re-imaged at every iteration. We ensure that `jackknify` interfaces with `CASA` and `tclean` to retain similar metadata for the spectral cubes, such that it is compatible with most line-finding algorithms. Because of this, `jackknify` can become computationally intensive, particularly for large data sets. As we will show in this paper, the analysis of ALMA spectral scans is computationally feasible. Large mosaics, however, might be more problematic. Therefore, we have created another implementation named *jaxknify*, which utilizes the `jax` implementation of the `iFFT` as a substitute for `tclean`. The output of the Fourier Transform is, however, not compatible with existing line-find methods. Hence, for the remainder of this work, we used the `CASA`-compatible version of `jackknify`.[^5]

## Line finding

### Traditional empirical methods

To date, most approaches to finding emission-line sources in (sub-)mm interferometric data have been based on determining the significance of an emission line (a positive peak) via the line “fidelity” or “reliability” (cite: Walter2016; Pavesi_2018; GL2019; Westmeier_2021). The fidelity (or reliability) function is defined as,

$$\begin{equation}
\label{eq:fidelity}
                \mathrm{fidelity (\gamma)} = 1 - \dfrac{N_\mathrm{neg} (\mathrm{\gamma})}{N_\mathrm{pos} (\mathrm{\gamma})}~,
            
\end{equation}$$

where $N_\mathrm{neg} (\mathrm{\gamma})$ and $N_\mathrm{pos} (\mathrm{\gamma})$ are the number of negative and positive peaks, respectively, above a given detection threshold $\gamma$. The value of $\gamma$ is usually a function of the $S/N$ but can be arbitrarily chosen.

The fidelity function empirically estimates the likelihood ratio of the false detection, $\mathcal{L_{\rm FD}}(\gamma)$, over the detection, $\mathcal{L_{\rm D}}(\gamma)$ by taking the integral over the Probability Density Functions (PDFs) of their respective probability distributions, $\mathcal{P_{\rm FD}}(x)$ and $\mathcal{P_{\rm D}}(x)$. $\mathcal{P_{\rm FD}}(x)$ and $\mathcal{P_{\rm D}}(x)$ are sampled by searching for negative and positive peaks, respectively. Therefore, the following relation of the likelihood ratio between detection and false detection holds: $$\begin{equation}
\label{eq:ratio}
                \Lambda(\gamma) = \dfrac{N_\mathrm{pos} (\mathrm{\gamma})}{N_\mathrm{neg}(\mathrm{\gamma})} = \dfrac{\mathcal{L_{\rm D}}(\gamma)}{\mathcal{L_{\rm FD}}(\gamma)} = \dfrac{ \int_{\gamma}^{\infty} \mathcal{P}_{\rm D}(x | \Delta v)~\mathrm{d}x}{ \int_{\gamma}^{\infty} \mathcal{P}_{\rm FD}(x | \Delta v)~\mathrm{d}x}~.
            
\end{equation}$$

This relationship is a function of the kernel width used to determine the linewidth, $\Delta v$. For example, to characterize the line emission in the ALMA Spectroscopic Survey of the Hubble Ultra Deep Field (ASPECS) (cite: GL2019) chose the detection threshold $\gamma$ such that $\mathrm{fidelity (\gamma)}$ = 0.9. This resulted in $\gamma \simeq 6.4\sigma$ for the ASPECS sample, assuming that Eq. [\[eq:fidelity\]](#eq:fidelity) is well described by an error function (cite: Decarli2020).

The other assumption made while employing the fidelity function is that the flux distribution of negative peak values is a proper estimator for $\mathcal{P}_{\rm FD}(x)$. However, this does not hold when absorption with respect to the CMB or a bright background source leads to negative line fluxes, contaminating the noise statistics. Additionally, since the method is applied in the image domain, any bright line or continuum flux will also create a negative signal through the dirty beam patterns. Bright sources can be “cleaned” (if they fall within the imaged part of the sky), but the fainter ones will create correlated spatial noise (cite: Tsukui2022). Furthermore, ALMA has a limited data volume along the spectral axis; hence, $\mathcal{P}_{\rm FD}(x)$ is not fully sampled over the $\delta\nu$ space, making these empirical approaches inaccurate.

### Line detection inference through jackknifing

Here, we describe how we perform the line detection throughout this work by utilizing the jackknifed data sets. To determine the likelihood of detection, we first quantify the likelihood of false detection, for which we need the underlying PDF. The distribution of false positive detections is set by the distribution of peak values in a data cube that only contains noise (Section [3.2.1](#sec:trad)). The distribution of positive or negative peaks is a subset of the pixel-value distribution in the data cube (cite: Vio2016). The number, location, and amplitude of peak values depend on the realization of the total pixel-value distribution, which for interferometric data in the image plane, can be approximated as a smoothed random Gaussian field. By jackknifing the visibilities, we effectively shuffle the noise distribution, altering the noise realization and creating another subsample of the pixel-value distribution, namely another peak distribution. This allows us to increase the sample statistics of $\mathcal{P}_{\rm FD}(x)$ while using the same data set.

Figure [2](#fig:convergence) shows that for an increasing number of realizations, we better probe the tail of the distribution at high $S/N$. The cumulative distribution function (CDF) $\Phi_{\rm FD}$ of $\mathcal{P}_{\rm FD}(x)$ is smooth till $S/N\approx4.5$ and reaches a $S/N = 5$ within a hundred realizations. Specifically, each CDF incrementally includes data from additional jackknife realizations. For example, the CDF for $35\times$ jackknife realizations contains all the data from the $34\times$ realization set. Furthermore, the jackknifed data only includes peaks within a $0.6\ensuremath{''}$ aperture of the center of the data cube (chosen so that this test is consistent with the discussion in section [5](#sec:results)). Figure [2](#fig:convergence) extends to a hundred realizations in total. Since there is a trade-off between sampling more realizations and computation time and from $\approx$ 50 realizations onward we recover the high-$S/N$ tail of the distribution; we decided to use 50 jackknife realizations throughout this work.

![](figures/convergence_v3.pdf)

The difference between the sampled PDF of the false positives, $\mathcal{P_{\rm FD}}(x)$, coming from the negative peak distribution (e.g., one noise realization) in the real data versus that from 50 jackknife realizations is shown in Figure [3](#fig:pdf_noise). For the jackknifed realizations, we show the inner 95% confidence interval per bin. Again, for both the real and jackknifed data, we only consider peaks within a $0.6\ensuremath{''}$ aperture of the center of the data cube. Since we do not expect a negative signal in this data set, the two distributions should be equivalent. However, our method provides better sampling (as also shown in Figure [2](#fig:convergence)) and thus better statistics, particularly at higher $S/N$. Furthermore, the scatter in the jackknife realizations within the 95% confidence interval is consistent with the Poisson uncertainty in the real data for each bin, except for a potential outlier at $S/N\approx 4$. This indicates that the various realizations are consistent with each other.

As shown in Figures [2](#fig:convergence) & [3](#fig:pdf_noise), jackknifing allows for a more complete sampling of the noise distribution without the need for complex models or computationally intensive four-dimensional covariance estimates (cite: Vio2016; Tsukui2022). By leveraging `jackknify`, we can obtain a more reliable and efficient measure of the probability of false detection, $\mathcal{P_{\rm FD}}(x)$, and take the likelihood ratio, $\Lambda(\gamma)$ with $\mathcal{L_{\rm D}}(\gamma)$ according to Eq. [\[eq:ratio\]](#eq:ratio) to estimate a feature being real or not. Then,

- if $\Lambda(\gamma) > 1$, the observed data is more likely to fall under the hypothesis that a signal is present, whereas

- if $\Lambda(\gamma) \leq 1$, the observed data falls under the null hypothesis and is thus better described as being drawn from the underlying noise distribution.

Finally, an excess in the ratio is considered significant if the likelihood ratio exceeds a critical value $k$, such that:

- if $\Lambda(\gamma) \geq k$, one can reject the null hypothesis that no signal is present in the data, whereas

- if $\Lambda(\gamma) < k$, one cannot reject the null hypothesis.

![](figures/neg_vs_pos_withscatter.pdf)

# Application to simulated ALMA data

![](figures/simulated_noise.pdf)

To validate our method, we simulated mock ALMA data using `CASA`’s `simobserve` task. We simulated a one-hour-long execution block centered at an RA and Dec of zero degrees. The simulated data contained six channels centered at a frequency of $\nu = 279$ GHz with a channel width of 31 MHz. We created the simulated $uv$-coverage using configuration 4 from cycle 7, leading to a resolution of $0.6\ensuremath{''}$ when `cleaning` using natural weighting. The setup of the simulations was designed to be similar to the observational setup of GLASS-z12 (Table [\[tab:observations\]](#tab:observations)). Using this setup, we simulated several datasets containing continuum and line emission from two separate sources with various integrated $S/N$ values. We incremented the flux of the sources, maintaining the same $uv$-coverage for every observation. The line flux was simulated using a 3D Gaussian model. One dimension corresponds to the spectral flux distribution; its flux is constrained as described above – so that the integral over the Gaussian equals the respective $S/N$ – and has an FWHM equal to $\sim73$ MHz, corresponding to a line with an FWHM of 80 km s$^{-1}$. The second and third dimensions of the Gaussian correspond to the spatial dimensions and are used to generate a blob in each channel map, with its amplitude set by the first Gaussian and an FWHM of 2.355 pixels (1 pixel = $0.01\ensuremath{''}$). Hence, the observation is considered unresolved. The same angular size on the sky is used for the continuum source.

Using the simulated data, we checked how well `jackknify` removes the signal. Figure [4](#fig:sims) shows the moment-0 maps of the $S/N = 5$ observation (*Left*), the corresponding noise map (*Middle*), and the map resulting from jackknifing the visibilities (*Right*).

We created the noise-only map by subtracting the noise-free dirty map (which is an output of `simobserve`) from the noisy output. Thus, the noise-only map is representative of the noise in a “perfectly `cleaned`” map. The simulated noise map and jackknifed realization exhibit the same noise structure, validating our jackknifing approach.

We tested how well jackknifing performs as a function of the sources’ $S/N$, as the randomization process might not fully remove the signal, leaving residuals in the generated noise realization. We initially noticed a difference between the standard deviation from the single cleaned map and the mean of the 50 jackknife realizations (see Appendix [7](#app:sim)). This bias depended on the seeding used in `simobserve`, which is the result of the inherent variance of `simobserve`, combined with the fact that the standard deviation is estimated from maps with a finite size. Due to the limited representation of the chosen image domain, large- and intermediate-scale modes can induce non-negligible biases in the measured noise variance compared to the underlying truth distribution. To explicitly test for this, we create jackknifed realizations over a large set of `simobserve` runs without a source, each assuming a different input random seed (Fig. [5](#fig:test_simobs)). All the resulting marginalized jackknife distributions are found to be consistent with the same normal distribution, which is characteristic of the noise probability function. The `simobserve` variance estimates are scattered according to the same distribution, implying that the `simobserve` output itself shows the same statistical properties of the result of an individual jackknifing cycle. Therefore, jackknifing can be used to better describe the underlying distribution function independent of the noise realization used in `simobserve`.

![](figures/test_simobs.pdf)

![](figures/jackknifing_works_.pdf)

We test how the measured standard deviations from the jackknife realizations evolve with S/N in Figure [6](#fig:sims_vs_snr). To this end, we simulated the sources as Gaussians that are off-centered from the phase reference point. This setup allows the signal to leak from the real to the imaginary components, testing the effectiveness of the jackknife routines without assuming the source to be at the phase reference – an assumption often made in interferometric data analysis tools (such as `uvcontsub`). We compare the mean and standard error of the standard deviation values measured for the jackknifed realizations vs the observations simulated with `simobserve`.

We find that our jackknifing approach is perfectly reliable for $S/N \lesssim 50$. That is, the jackknife realizations of simulated observations with sources at $S/N \lesssim 50$ are perfectly consistent with the cleaned noise maps. The observations simulated with a peak $S/N\gtrsim50$, however, indicate a stronger deviation from the cleaned noise estimate. We note that this does not manifest as a residual of the source but as an overall larger standard deviation throughout the map. We therefore advise that before applying `jackknify` to the measurement set, one should remove extremely bright continuum and line-emitting sources (e.g., $S/N>50$) from the data set in the visibility plane, as is common practice with other line-finding methods (cite: Walter2016). Overall though, the tests we have performed with simulated data (Figures [5](#fig:test_simobs) & [6](#fig:sims_vs_snr)), show that jackknifing allows for an accurate estimation of the underlying noise distribution.[^6]

![](figures/sims_snr5.pdf)

The final validation we performed with the simulated data was to test the accuracy of the line-finding method. Since jackknifed data cubes have an output identical to the original dataset, we apply the same tools to the real and noise realizations. Therefore, we use the simulation for which the sources have an integrated $S/N = 5$. We sample the distribution of false positive detections, $\mathcal{P}_{\rm FD}(x)$, by applying the line finding algorithm to the jackknifed data and use the `FindClump` algorithm[^7] to search for lines in the jackknifed data cubes (see Section [5.1](#sec:setup) for a description on how `FindClump` is setup). The average distribution of the peak values in the 50 jackknife realizations is shown by the blue histogram in Figure [7](#fig:sim_linefinding). This histogram reveals a smooth peak distribution, declining from $S/N=2.5$ to $S/N \approx 5.5$.[^8] Given the number of peaks `FindClump` detected in a single realization ($\rm N_{\rm peaks} = 70$), and a likelihood of $\mathcal{L}_{\rm FD}(\gamma = 4.5) = 0.0021$, we expect to find on average $0.1 \pm 0.4$ peaks above $S/N=4.5$ in the simulated observation. By applying the line-finding algorithm to the real data (orange histogram), we recover the simulated continuum and lines sources, both with a $S/N = 4.9$.

Compared to the underlying noise distribution (in blue), the likelihood ratio tests yield $\Lambda(\gamma = 4.0) = 13$. We also find a small excess at $S/N\approx3.6$ and check if our likelihood ratio test indicates this to be real or not (we know it is not). We find that the number of peaks, expected from jackknifing, at the $S/N$ range of $3<\gamma<4$ ($3.5<\gamma<4$) is $14.6 \pm 3.8$ ($2.1 \pm 1.5$), while we find $16 \pm 4$ ($5.0 \pm 2.2$) in the simulated data, resulting in a $\Lambda(3<\gamma<4) = 1.1$ ($\Lambda(3.5<\gamma<4) = 2.4$). Thus, our statistical tests indeed find these peaks to be consistent with being noise, meaning we recover the simulated sources while the noise is correctly characterized as such.

# Application to $z>10$ galaxy candidates

![](figures/pdfs.pdf)

Our tool, `jackknify`, can be applied to various science cases, including ones involving blind line searches in deep fields (i.e., without known counterparts), targeted searches around candidates identified at other wavelengths (e.g., following up $z>10$ candidates) and searches for companions around known sources. Here, we apply our method to three sets of ALMA observations targeting the $z>10$ galaxy candidates GLASS-z12, GLASS-z10, and S5-z17-1 ((cite: Bakx2023), (cite: Yoon2023), and (cite: Fujimoto2023), respectively). There was also a DDT program targeting the $z\sim 13$ candidate HD1, but we exclude these observations here as more recent work by (cite: Harikane2024b) spectroscopically confirmed the object to be a passive galaxy at $z=4.0$ and a similar jackknifing analysis was already performed in (cite: Kaasinen2023). Furthermore, we note that during the referee process, two additional ALMA observations targeting $z > 10$ galaxies were reported. Specifically, these include observations on GL-z14 (cite: Carniani2024b; Schouws2024) and a deeper observation targeting GLASS-z12 (cite: Zavala2024b). These observations are not included in this work but underscore how rapidly the field is advancing.

In Section [5.1](#sec:setup), we describe the experimental setups, in Section [5.2](#sec:without_prior), we detail the results of the blind line search across the entire spectral axis and, in Section [5.3](#sec:with_prior), we summarize the line finding results for GLASS-z12, incorporating an additional redshift prior based on spectroscopic JWST/MRS measurements of the H$\alpha$ line (cite: Zavala2024).

## Specific experiment set up

To quantify the detection significance of a line along the full spectral axis, we adopt the following procedure.

1.  We jackknife each observation set 50 times, creating 50 different noise realizations. Each jackknifing iteration includes differing visibilities and imaging of the full spectral scan and takes $\approx 9$ minutes on a 2019 MacBook Pro with a 2.6 GHz 6-Core Intel Core i7 processor. A tenfold improvement in performance speed was found when using a MacBook Pro with the M3 chip.

2.  We use `FindClump` (cite: Walter2016), as implemented in the `interferopy` package (cite: interferopy), to sample the distribution of positive peak values from both the real and jackknifed data.

3.  We mask out features outside a $0.6\ensuremath{''}$ radius of the optically derived center. This corresponds to a physical radius of $\approx 2$ kpc at $z=12$ and is $\approx2\times$ the size of the beam for all four datasets. We chose a radius of $r=0.6\ensuremath{''}$ to include the tentative detection previously reported in our analysis (cite: Bakx2023), but be able to exclude serendipitous detections of interlopers.

4.  We calculate the likelihood ratio of the respective distributions to infer if there is an excess in the peak distribution in the real data compared to the sampled noise distribution.

5.  We consider a detection to be significant if the excess of peaks in the real data with respect to the noise has at least a significance of $2\sigma$ based on Poisson statistics. Therefore, we require $\Lambda(\gamma) k$, with $k=3$.

In step 2, we configure `FindClump` to search for emission lines with widths between $100 - 500$ km s$^{-1}$, corresponding to $3-11$ times the channel width. The velocity width varies slightly across different observation sets as we are examining galaxies at various redshifts. With `FindClump`, we identify peaks that exceed a signal-to-noise ratio ($S/N$) of 0, and we crop “identical” peaks if they are found within $0.2\ensuremath{''}$ of each other spatially (approximately $1/3$ of the beam width) and within 0.2 GHz spectrally (roughly $4-5$ channels apart). Additionally, we have modified the default settings in `SExtractor` (cite: Bertin1996), specifically the analysis and detection thresholds which we both set to 2 to better detect low $S/N$ clumps.

## Results on blind line searches

We check for any real signal by comparing the distribution of positive peaks in the real and jackknifed data (Fig. [8](#fig:pdf_compare)). According to Eq. [\[eq:ratio\]](#eq:ratio), this comparison translates to the ratio of the probability distribution of a detection, $\mathcal{P}_{\rm D}(x)$, versus a false detection, $\mathcal{P}_{\rm FD}(x)$. Thus, any excess of positive features in the real data relative to the noise distribution indicates a true positive line detection. Table [1](#tab:significances) provides an overview of the likelihood of previously reported tentative detections being real. In the following section, we will discuss the results for each source, one by one.

|  |  |  |  |
|:---|:--:|:--:|:--:|
|  | GLASS-z12 | GLASS-z10 | S5-z17-1 |
| Reported significance | $5.8\sigma$ | $4.4\sigma$ | $5.1\sigma$ |
| Found highest significance$^\dagger$ | $4.2\sigma$ | $4.3\sigma$ | $4.3\sigma$ |
| $\mathcal{L}_{\rm FD}(\gamma = 4)$ | 0.0011 | 0.0054 | 0.0032 |
| $\mathcal{L}_{\rm FD}(\gamma = 4) \times {\rm N_{\rm peaks}}$ | $1.3 \pm 1.1$ | $1.5 \pm 1.2$ | $0.7 \pm 0.8$ |
| $\rm N_{\rm peaks}$ found | 1 | 2 | 1 |
| $\Lambda(\gamma = 4)$ | 0.80 | 1.4 | 1.4 |

: Significances of Detected Peaks

Table notes: In this table, we quote the individual likelihoods of false detections for the three DDT-ALMA data sets on $z>10$ galaxies. Multiplied with the number of peaks in the real dataset (${\rm N_{\rm peaks}}$), this leads to the expected number of peaks above $S/N>4$ in a purely noisy dataset. We compare this with the found number of peaks in the real data and the likelihood ratio test as defined in Eq. [\[eq:ratio\]](#eq:ratio).$^\dagger$ We note that the peaks with the highest significance are not the same peaks as the ones that correspond to the reported significance (top row). See section [5.2](#sec:without_prior) for more detail.

For GLASS-z12 (left panel, Fig. [8](#fig:pdf_compare)), we find no excess of positive peaks in the real data compared to the underlying noise distribution. We integrated the probability of a false detection from the detection threshold of $\gamma = 4\sigma$ onward. Considering the total number of peaks in the real data ($\rm N_{\rm peaks} = 1150$), we estimated the expected number of peaks due to noise fluctuations. We found $\mathcal{L}_{\rm FD}(\gamma = 4\sigma) \times {\rm N_{\rm peaks}} = 0.0011 \times 1150 = 1.3 \pm 1.1$. In the real data, we recover one peak above $S/N > 4$, which is consistent with being noise. This is also indicated by the likelihood ratio test (Eq. [\[eq:ratio\]](#eq:ratio)), which results in $\Lambda(4\sigma) = \mathcal{L}_{\rm D}(4\sigma) / \mathcal{L}_{\rm FD}(4\sigma) = 0.80$. We note that the $S/N = 4.2$ peak discussed here is not the same peak found by (cite: Bakx2023). The peak we have recovered is at a frequency of $\nu = 246.6106$ GHz and coordinates RA, Dec $= (3.49895, -30.32469)$, which differs from their reported $5.8\sigma$ peak over 400 km s$^{-1}$, offset $0.5\ensuremath{''}$ from the JWST position (Table [\[tab:observations\]](#tab:observations)). We recover a peak at the same location but at a lower significance of $2.9\sigma$ for a linewidth of 280 km s$^{-1}$ (the maximum S/N peak over any linewidth at this position). The difference in S/N and linewidth is due to the difference in how the data were imaged. Whereas we imaged these data using natural weighting and using a channel width of 46 km s$^{-1}$, (cite: Bakx2023) tapered the data to $0.3\ensuremath{''}$ and used a channel width of 150 km s$^{-1}$. This highlights the importance of imaging the jackknifed data in the same way as the real data.

For GLASS-z10 (middle panel, Fig. [8](#fig:pdf_compare)), we find a small excess of peaks in the real versus the jackknifed (noise-only) data at $S/N=4.1-4.3$. Given the noise distribution and the total number of peaks in the real data ($\rm N_{\rm peaks} = 271$), we expect to find $1.5 \pm 1.2$ peaks at $\gamma > 4\sigma$. In the real data, we find two peaks at $\gamma > 4\sigma$. The likelihood ratio resulted in $\Lambda(\gamma = 4\sigma) = 1.4$. This does not exceed our detection threshold of $k = 3$, meaning that the two tentative features[^9] are consistent with being noise at a likelihood of $\mathcal{L}_{\rm FD}(\gamma= 4\sigma)$ = 0.0054. Neither peak was previously reported by (cite: Yoon2023). We also recover the previously reported detection at $2.7\sigma$ with a linewidth of 235 km s$^{-1}$. This line has a false detection likelihood of $\mathcal{L}_{\rm FD}(\gamma=2.7\sigma) = 0.19$ and a likelihood ratio test resulting in $\Lambda(\gamma = 2.7\sigma) = 0.9$.

For S5-z17-1 (right panel, Fig. [8](#fig:pdf_compare)),the expected number of peaks is $\mathcal{L}_{\rm FD}(\gamma = 4\sigma) \times {\rm N_{\rm peaks}} = 0.0032 \times 221= 0.7 \pm 0.8$. Given that we find one peak above $S/N>4$ and since $\Lambda(\gamma=4\sigma) = 1.4$, we conclude that these data are also consistent with being noise. We recover the peak reported in (cite: Fujimoto2023), albeit with a significance of $3.9\sigma$ instead of the reported $5.1\sigma$. This line has a false detection likelihood of $\mathcal{L}_{\rm FD}(\gamma=3.9\sigma) = 0.0060$ and a likelihood ratio test resulting in $\Lambda(\gamma = 3.9\sigma) = 2.2$.

In conclusion, our analysis of the GLASS-z12, GLASS-z10, and S5-z17-1 datasets reveals no significant detections of any of these (candidate) $z > 10$ galaxies in the ALMA data. All of the peaks identified in the real data are consistent with noise, as indicated by the likelihood ratio tests and comparison with the jackknifed noise distributions. Given the number of peaks per data set, the detection significance does not follow a Gaussian distribution. Since a $4\sigma$ detection should reflect that only one in fifteen thousand random draws should be a false detection, we reach a $5\sigma$ fluke already within a sample size of $\approx 200-1000$ peaks. This highlights the importance of rigorous noise analysis in confirming potential astronomical signals.

## Quantifying detection significance with known redshifts

![](figures/pos_vs_pos_freq.pdf)

So far, we have presented the jackknifing plus line-finding approach for the case of a blind detection experiment and the case where the approximate position of the source is known but where we have no strong prior on the central frequency. We now extend the analysis for cases where the redshift and, hence, the line frequency are known from other observations. To provide an example, (cite: Zavala2024) detected bright nebular emission lines of GLASS-z12 with JWST, constraining the redshift to be $z_{\rm spec} = 12.33 \pm 0.02$. With this prior knowledge, we will reanalyze the data reported in (cite: Bakx2023)

at the expected location (spatially and spectrally) of the \[O III\] 88 μm line. Notably, this feature is spectrally and spatially offset from the earlier reported tentative detection of (cite: Bakx2023).

The redshift uncertainty ($\Delta z = \pm 0.02$) derived from the JWST/MRS spectrum of GLASS-z12 translates to a frequency width of $\Delta \nu_{\rm obs} = \pm 0.4$ GHz at the expected \[O III\] 88 μm frequency of $\nu_{\rm obs} = 254.54$ GHz. We compute the frequency uncertainty from, $$\begin{equation}
\label{eq:redshift_to_freq}
            \left|\dfrac{\Delta z}{1+z}\right| = \left| \dfrac{\Delta\nu_{\rm obs}}{\nu_{\rm obs}}\right| = \left|\dfrac{\Delta v}{c}\right|~,
        
\end{equation}$$

where $\Delta z$ is the redshift range probed, $\Delta \nu_{\rm obs}$ is the corresponding frequency width centered on the frequency $\nu_{\rm obs}$, $\Delta v$ is the corresponding velocity width, and $c$ is the speed of light. This frequency uncertainty is roughly equivalent to the maximum correlated bandwidth of a single ALMA spectral window. Even with better redshift constraints, astrophysical processes like outflows and differing dust geometries could lead to both spatial and spectral offsets, as observed in the \[C II\] 158 μm and \[O III\] 88 μm lines reported by (cite: Fujimoto2024). Therefore, the likelihood of false detections, $\mathcal{L_{\rm FD}}(\gamma)$, is still determined by the probability density function similar to the blind search scenario, albeit with the addition of a relatively wide prior of $\pm 0.4$ GHz from the JWST/MRS observations.

To incorporate the redshift prior from auxiliary data sets into our line-finding routine, we adopt a Bayesian approach using Bayes theorem, $$\begin{equation}
\label{eq:bayes}
            P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}~.
        
\end{equation}$$ where $P(B|A)$ is the general expression for a probability function—in our case, the probability of a detection,$\mathcal{P}_{\rm D}(x)$, and false detection, $\mathcal{P}_{\rm FD}(x)$—, $P(A)$ is the prior, and $P(B)$ is the Bayesian evidence. For the detection inference of GLASS-z12, we adopt a Gaussian prior on the redshift, $\mathcal{G}\left(\mu = 12.33, \sigma = 0.02\right)$. We also use a uniform prior on the radial distance, $\mathcal{U}\left(0, 0.6\ensuremath{''}\right)$, and a uniform prior on the $S/N$ of the peak, $\mathcal{U}\left(2.5, \infty\right)$, thereby only counting peaks with $S/N > 2.5$.

After multiplying the probability distribution by the priors to obtain the posterior distribution, we normalize it such that the integral over the bins of $S/N$, frequency, and radial distance equals one.

Unlike methods such as Markov Chain Monte Carlo, which directly sample the posterior distribution, we first sampled the PDFs using `FindClumps` without applying any priors. We then applied Bayes theorem in post-processing to determine which feature is most likely to correspond to GLASS-z12. This approach assumes no correlation between the $S/N$ of a candidate (since the intrinsic flux of the source is unknown) and its location along the RA, Dec, and frequency axes. This is a reasonable assumption, as there should be no correlation between the $S/N$ of the line detection and these parameters for non-primary-beam-corrected maps.

We visualize our approach to determining the likelihood of a positive peak being real, given the redshift prior, in Figure [9](#fig:pdf_GLASSz12). The posterior distributions for both the real and jackknifed observations are shown in the frequency domain. We also show the prior from JWST/MRS observations and the initial PDF of the probability of false detections without applying the prior. The latter indicates that the PDF has a flat distribution with respect to frequency, thus supporting the assumption that there is no correlation between the $S/N$ of a peak and its location along frequency axes. We find a slight excess of detection peaks at a frequency of $\nu = 254.0$ GHz, corresponding to two peaks located at ${\rm RA}, {\rm Dec}, \nu= 3.49892^\circ, -30.32469^\circ, 253.92$ GHz and ${\rm RA}, {\rm Dec}, \nu= 3.49918^\circ, -30.32469^\circ, 253.92$ GHz. These peaks have $S/N$ values of 2.7 and 2.6, and linewidths of 230 km s$^{-1}$ and 140 km s$^{-1}$, respectively. Given the probability of false detection and the number of peaks found in the real data, the likelihood ratio test results in $\Lambda(\gamma=2.5\sigma)= 1.64$. This does not exceed our detection threshold of $k>3$, set in Section [5.1](#sec:setup).

For illustrative purposes, Figure [10](#fig:moments) shows a moment-0 map with a tentative feature alongside three jackknife realizations. In one of these realizations, we observe a similar spatial flux distribution as in the real data. The moment-0 maps and the posterior distribution clearly indicate that there is no detection of GLASS-z12 in the ALMA data (Project code: 2021.A0020.S, PI: Bakx). Even including a prior from JWST, the ALMA data is statistically consistent with being noise. To reiterate, we did not include in our analysis the newer observations targeting GLASS-z12 that were recently published (cite: Zavala2024b). That work showed a $\approx 4.5-5.2\sigma$ detection of the \[O III\] 88 μm line when the new observations were combined with the older data.

![](figures/moments.png)

# Summary & Implications

In this study, we introduce an easy-to-use framework for determining the likelihood of faint emission in interferometric data bring real. By jackknifing the visibilities, we generate noise realizations of the measurement set. Line-finding tools can then be applied to both the noise and the original data set to quantify the level of false detections. In this work, we have tested our approach using `FindClumps` (cite: Walter2016), but there are several other line-finding tools, which may be more appropriate for interferometric data, including `SoFiA` (cite: Serra2014; Westmeier_2021), `LineSeeker` (cite: GonzalezL2020) or `MF3D` (cite: Pavesi_2018). Our entire analysis procedure, modulo the user’s choice of line-finding algorithm, is publicly available at <https://joshiwavm.github.io/jackknify/>, and the tool, `jackknify`, is installable using pip[^10] (cite: jackknify2024).

We applied this methodology to three ALMA-DDT observations targeting galaxy candidates at $z>10$ to recover the likelihood of peaks at a certain S/N being real.

Given the number of peaks in each dataset and their respective distribution of peak values, the likelihood ratio test using a minimum detection threshold of $\gamma=4\sigma$—as formalized in Eq. [\[eq:ratio\]](#eq:ratio)— resulted in $\Lambda(\gamma=4\sigma) = 0.80, 1.4, 1.4$, respectively (see Table [1](#tab:significances)). Since we set the detection threshold to $\Lambda(\gamma)>k$ with $k=3$ (see Section [5.1](#sec:setup)), we conclude that none of the previously reported tentative detections could be distinguished from noise, even when incorporating additional prior information from JWST/MRS slit measurements in the inference.

Our analysis shows that, given the current data volumes ($\rm N_{\rm peaks} \approx 200-1000$), we expect to find approximately $3 \pm 2$ line features with $S/N \sim 4-5$ in broad ALMA line scans based on the underlying noise distribution. Ensuring a secure detection is therefore challenging, requiring $>5\sigma$ detections when performing a blind line search in a cube probing 30 GHz of bandwidth and targeting a single line. Detecting two lines at matching redshifts would strengthen the significance; however, even then, the likelihood of detecting two noise features within a reasonable spatial and frequency offset needs to be accounted for. Even when probing multiple lines in different bandwidths, spurious features can arise at a significance of $\approx 4\sigma$ at the right frequency and realistic spatial offset in both data sets (cite: Kaasinen2023).

While the elegance of `jackknify` lies in its straightforward implementation, new approaches are needed to optimize line searches computationally and to increase fidelity. There is currently no publicly available line-finding algorithm implemented in $uv$-space for extragalactic sources (see, for instance, (cite: Loomis2018) with the code `VISIBLE`, which they used for finding isotopes in protoplanetary disks in high spatial and spectral resolution observations). Operations in $uv$-space are not affected by side lobes or other sources of correlated noise to which analyses in the image plane are susceptible, but they come at the cost of computational efficiency. The flux of the source is not concentrated within a resolution element but rather spread over a large number of visibilities. Additionally, ongoing ALMA studies – albeit still in the image plane – are exploring the use of unsupervised machine learning to identify faint emission lines (cite: Baronchelli2021; Baronchelli2024). Although these methodologies are in the early stages of development, their implementation could drastically increase computation speed and efficiency.

Improving current line-finding methods is important in the context of several upcoming surveys and telescope upgrades. For example, the Wideband Sensitivity Upgrade of ALMA ((cite: WSU2023)) will increase the bandwidth and sensitivity by a factor of 2–4. This upgrade will greatly increase the efficiency of line-finding experiments, especially at high frequencies, and is, therefore, critical for identifying $z>7$ galaxies. Looking to the more distant future, significant advances are expected from major new submillimeter-to-centimeter facilities, such as the proposed 50 m single dish, named the Atacama Large Aperture Submillimeter Telescope (AtLAST; (cite: Booth2024)) and SKA (cite: Dewdney2009). AtLAST would enable large, unbiased surveys of cosmological volumes in multiple bands through the use of on-chip spectrometers (cite: Endo2012) and its large $2^\circ$ field of view, providing secure line identifications for large samples of high-$z$ galaxies. Although splitting in the visibility plane will not be possible for single-dish facilities, a similar approach in which the differencing is done in the time domain will still be useful (cite: Weiss2009). At centimeter wavelengths, deep HI surveys are already revealing new HI detections up to $z\sim0.4$ (e.g., (cite: Baker2024); (cite: Xi_2024); (cite: Kazemi-Moridani2024)), with the full SKA likely to push this to $z\sim 1$. With the increase in data volume associated with these new and upgraded facilities comes the increased potential for spurious line detections. Thus, it is crucial that the community accurately identifies the probability of false detections using statistically motivated approaches like the one we presented in this work.

# Acknowledgements

We want to thank Dr. Seiji Fujimoto for his efforts as PI in requesting the ALMA data used in this project and for his helpful discussions, which greatly improved the quality of the interpretation of the data herein.

The project leading to this publication has received support from ORP, which is funded by the European Union’s Horizon 2020 research and innovation program under grant agreement No 101004719 \[ORP\].

TM acknowledges support from the AtLAST project, which has received funding from the European Union’s Horizon 2020 research and innovation program under grant agreement No 951815.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.A.00020.S, ADS/JAO.ALMA#2021.A.00023.S, and ADS/JAO.ALMA#2021.A.00031.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

JvM acknowledges support from R. Willems for making ‘jackknify‘ publicly accessible.

53 natexlab

(ref: Baker2024) Baker, A., Blyth, S., Holwerda, B., et al. 2024, in American Astronomical Society Meeting Abstracts, Vol. 243, American Astronomical Society Meeting Abstracts, 346.07

(ref: Bakx2023) Bakx, T. J. L. C., Zavala, J. A., Mitsuhashi, I., et al. 2023, MNRAS, 519, 5076

(ref: Baronchelli2024) Baronchelli, I., Bonato, M., De Zotti, G., et al. 2024, Galaxies, 12, 26

(ref: Baronchelli2021) Baronchelli, I., Scarlata, C. M., Rodrı́guez-Muñoz, L., et al. 2021, ApJS, 257, 67

(ref: Bertin1996) Bertin, E. & Arnouts, S. 1996, A&AS, 117, 393

(ref: interferopy) Boogaard, L., Meyer, R. A., & Novak, M. 2021, Interferopy: analysing datacubes from radio-to-submm observations

(ref: Booth2024) Booth, M., Klaassen, P., Cicone, C., et al. 2024, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 13102, Millimeter, Submillimeter, and Far-Infrared Detectors and Instrumentation for Astronomy XII, ed. J. Zmuidzinas & J.-R. Gao, 1310206

(ref: Carniani2024b) Carniani, S., D’Eugenio, F., Ji, X., et al. 2024a, arXiv e-prints, arXiv:2409.20533

(ref: Carniani2024) Carniani, S., Hainline, K., D’Eugenio, F., et al. 2024b, Nature, 633, 318

(ref: WSU2023) Carpenter, J., Brogan, C., Iono, D., & Mroczkowski, T. 2023, in Physics and Chemistry of Star Formation: The Dynamical ISM Across Time and Spatial Scales, ed. V. Ossenkopf-Okada, R. Schaaf, I. Breloy, & J. Stutzki, 304

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Castellano2022) Castellano, M., Fontana, A., Treu, T., et al. 2022, ApJL, 938, L15

(ref: Decarli2020) Decarli, R., Aravena, M., Boogaard, L., et al. 2020, ApJ, 902, 110

(ref: Dewdney2009) Dewdney, P. E., Hall, P. J., Schilizzi, R. T., & Lazio, T. J. L. W. 2009, IEEE Proceedings, 97, 1482

(ref: DiMascolo2023) Di Mascolo, L., Saro, A., Mroczkowski, T., et al. 2023, Nature, 615, 809

(ref: Endo2012) Endo, A., Werf, P., Janssen, R. M. J., et al. 2012, Journal of Low Temperature Physics, 167, 341

(ref: Fudamoto2024) Fudamoto, Y., Oesch, P. A., Walter, F., et al. 2024, MNRAS, 530, 340

(ref: Fujimoto2023) Fujimoto, S., Finkelstein, S. L., Burgarella, D., et al. 2023, ApJ, 955, 130

(ref: Fujimoto2024) Fujimoto, S., Ouchi, M., Nakajima, K., et al. 2024, ApJ, 964, 146

(ref: GL2019) González-López, J., Decarli, R., Pavesi, R., et al. 2019, ApJ, 882, 139

(ref: GonzalezL2020) González-López, J., Novak, M., Decarli, R., et al. 2020, ApJ, 897, 91

(ref: Harikane2024b) Harikane, Y., Inoue, A. K., Ellis, R. S., et al. 2024, arXiv e-prints, arXiv:2406.18352

(ref: Harikane2022) Harikane, Y., Inoue, A. K., Mawatari, K., et al. 2022, ApJ, 929, 1

(ref: Harikane2023) Harikane, Y., Ouchi, M., Oguri, M., et al. 2023, ApJS, 265, 5

(ref: Hatziminaoglou2015) Hatziminaoglou, E., Zwaan, M., Andreani, P., et al. 2015, The Messenger, 162, 24

(ref: Kaasinen2023) Kaasinen, M., van Marrewijk, J., Popping, G., et al. 2023, A&A, 671, A29

(ref: Kazemi-Moridani2024) Kazemi-Moridani, A., Baker, A. J., Verheijen, M., et al. 2024, arXiv e-prints, arXiv:2412.11426

(ref: Keating2015) Keating, G. K., Bower, G. C., Marrone, D. P., et al. 2015, ApJ, 814, 140

(ref: Kitayama2020) Kitayama, T., Ueda, S., Akahori, T., et al. 2020, PASJ, 72, 33

(ref: Loomis2018) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2018, AJ, 155, 182

(ref: Naess2020) Naess, S., Aiola, S., Austermann, J. E., et al. 2020, JCAP, 2020, 046

(ref: Naidu2022) Naidu, R. P., Oesch, P. A., van Dokkum, P., et al. 2022, ApJL, 940, L14

(ref: Padin2001) Padin, S., Cartwright, J. K., Mason, B. S., et al. 2001, ApJL, 549, L1

(ref: Pavesi_2018) Pavesi, R., Sharon, C. E., Riechers, D. A., et al. 2018, ApJ, 864, 49

(ref: Petry2020) Petry, D., Stanke, T., Biggs, A., et al. 2020, The Messenger, 181, 16

(ref: Planck2014_XIII) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2014, A&A, 561, A97

(ref: Popping2023) Popping, G. 2023, A&A, 669, L8

(ref: Readhead2004) Readhead, A. C. S., Myers, S. T., Pearson, T. J., et al. 2004, Science, 306, 836

(ref: Romero2018) Romero, C., McWilliam, M., Macı́as-Pérez, J. F., et al. 2018, A&A, 612, A39

(ref: Schouws2024) Schouws, S., Bouwens, R. J., Ormerod, K., et al. 2024, arXiv e-prints, arXiv:2409.20549

(ref: Serra2014) Serra, P., Westmeier, T., Giese, N., et al. 2014, SoFiA: Source Finding Application, Astrophysics Source Code Library, record ascl:1412.001

(ref: Sharp2010) Sharp, M. K., Marrone, D. P., Carlstrom, J. E., et al. 2010, ApJ, 713, 82

(ref: Thompson2017) Thompson, A. R., Moran, J. M., & Swenson, George W., J. 2017, Interferometry and Synthesis in Radio Astronomy, 3rd Edition

(ref: Tsukui2022) Tsukui, T., Iguchi, S., Mitsuhashi, I., & Tadaki, K. 2022, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 12190, Millimeter, Submillimeter, and Far-Infrared Detectors and Instrumentation for Astronomy XI, ed. J. Zmuidzinas & J.-R. Gao, 121901C

(ref: jackknify2024) van Marrewijk, J. & Di Mascolo, L. 2024, Joshiwavm/jackknify: Release Jackknify 1.0.0

(ref: Vio2016) Vio, R. & Andreani, P. 2016, A&A, 589, A20

(ref: Walter2016) Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67

(ref: Weiss2009) Weiß, A., Kovács, A., Coppin, K., et al. 2009, ApJ, 707, 1201

(ref: Westmeier_2021) Westmeier, T., Kitaeff, S., Pallot, D., et al. 2021, MNRAS, 506, 3962

(ref: Xi_2024) Xi, H., Peng, B., Staveley-Smith, L., et al. 2024, ApJL, 966, L36

(ref: Yoon2023) Yoon, I., Carilli, C. L., Fujimoto, S., et al. 2023, ApJ, 950, 61

(ref: Zavala2024b) Zavala, J. A., Bakx, T., Mitsuhashi, I., et al. 2024a, ApJL, 977, L9

(ref: Zavala2024) Zavala, J. A., Castellano, M., Akins, H. B., et al. 2024b, arXiv e-prints, arXiv:2403.10491

# Further comparison between the simulated noise and jackknifed realizations

Figure [11](#fig:bias_simobserve) shows the difference between the standard deviation from the cleaned map of the first, single simulated observation (i.e., one seed used for `simobserve` visualized with the orange point) and the distribution of standard deviations obtained from the various jackknife realizations (blue dotted line). We find that the jackknifed realizations follow the average distribution of standard deviations, obtained with various `simobserve` seeds (solid line, Fig. [5](#fig:test_simobs)), but their median clearly differs from the first single `simobserve` estimate. This shows that jackknifing can be used to better describe the underlying distribution function than a single noise realization used in `simobserve`.

![](figures/test_simobs_182.pdf)

[^1]: Additionally, one 80+ hour NOEMA observation on GN-z11 (cite: Fudamoto2024)

[^2]: see <https://joshiwavm.github.io/jackknify/>

[^3]: However, we do note that our tools are validated only on data where the $w$-term was neglected.

[^4]: In the case of incorrect calibration, such as when one of the 44 online ALMA antennas has an erroneous gain solution, the noise in the visibility plane becomes multiplicative rather than additive to the signal. The effects of jackknifing in such a situation are not thoroughly tested. However, the assumption of well-calibrated data without antenna calibration errors is reasonable, as it is common practice to check the calibration accuracy before imaging to ensure there are no spurious signals that could result in imaging artifacts.

[^5]: `jaxknify` was only used to compute the many realizations which are visualized in Figure [5](#fig:test_simobs) as described in Section [4](#sec:results_sims).

[^6]: We note that we did not evaluate the performance of jackknifing the visibilities in cases of large extended bright emission such as in molecular clouds within low-redshift galaxies.

[^7]: We note that this is an arbitrary choice and other algorithms may be better suited

[^8]: We note that the drop-off at lower $S/N$ is due to the cropping of peaks and the way *Source Extractor* catalogs its findings.

[^9]: Both features have a $S/N = 4.3$, a spatial offset of $0.35\ensuremath{''}$ and $0.39\ensuremath{''}$ from the optical counterpart, and are found at $\nu = 291.58$ and $\nu = 296.12$ GHz. Both have a linewidth of 170 km s$^{-1}$.

[^10]: <https://pypi.org/project/jackknify/>

</paper>

Write the methods card for this paper.