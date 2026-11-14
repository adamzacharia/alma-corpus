# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...968L..11G\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...968L..11G",
 "title": "A Broad Line-width, Compact, Millimeter-bright Molecular Emission Line Source near the Galactic Center",
 "year": 2024,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Ginsburg, Adam",
 "n_authors": 40,
 "arxiv_id": "2404.07808",
 "doi": "10.3847/2041-8213/ad47fa",
 "alma_projects_linked_by_archive": [
  "2012.1.00080.S",
  "2017.1.01185.S",
  "2021.1.00172.L"
 ]
}
```

Paper text:
<paper>
# A broad linewidth, compact, millimeter-bright molecular emission line source near the Galactic Center

## Abstract

A compact source, G0.02467-0.0727, was detected in ALMA 3 mm observations in continuum and very broad line emission. The continuum emission has a spectral index $\alpha\approx3.3$, suggesting that the emission is from dust. The line emission is detected in several transitions of CS, SO, and SO$_2$ and exhibits a line width FWHM $\approx160$ $\mathrm{km~s}^{-1}$. The line profile appears Gaussian. The emission is weakly spatially resolved, coming from an area on the sky $\lesssim1"$ in diameter ($\lesssim10^4$ au at the distance of the Galactic Center; GC). The centroid velocity is $v_{LSR}\approx40$-$50$ $\mathrm{km~s}^{-1}$, which is consistent with a location in the Galactic Center. With multiple SO lines detected, and assuming local thermodynamic equilibrium (LTE) conditions, $T_\mathrm{LTE} = 13$ K, which is colder than seen in typical GC clouds, though we cannot rule out low-density, subthermally excited, warmer gas. Despite the high velocity dispersion, no emission is observed from SiO, suggesting that there are no strong ($\gtrsim10~\ensuremath{\mathrm{km~s}^{-1}}$) shocks in the molecular gas. There are no detections at other wavelengths, including X-ray, infrared, and radio.

We consider several explanations for the Millimeter Ultra-Broad Line Object (MUBLO), including protostellar outflow, explosive outflow, collapsing cloud, evolved star, stellar merger, high-velocity compact cloud, intermediate mass black hole, and background galaxy. Most of these conceptual models are either inconsistent with the data or do not fully explain it. The MUBLO is, at present, an observationally unique object.

# Introduction

The center of our Galaxy contains billions of stars, tens of millions of solar masses of gas, a supermassive black hole, a tenth of our Galaxy’s ongoing star formation, and an extensive graveyard of stellar remnants (cite: Morris1996; Henshaw2023). It is therefore the likeliest place to find new classes of objects. We present one such object in this work.

The following will describe observations (§[2](#sec:observations)), measurements (§[3](#sec:measurements)) of spectral (§[3.1](#sec:spectralmeasurements)), spatial (§[3.2](#sec:spatialmeasurements)), spatio-spectral (§[3.3](#sec:spatio-spectral)), and continuum (§[3.4](#sec:continuum)) data followed by analysis and modeling (§[4](#sec:analysis)) of the excitation conditions (§[4.1](#sec:LTE), [4.2](#sec:nonlte)), chemistry (§[4.3](#sec:chemistry)), and dust (§[4.4](#sec:weirddust)). We then discuss the location of the source (§[5](#sec:where)), both along the line-of-sight (§[5.1](#sec:los)) and on the sky (§[5.2](#sec:spatiallocation)). We engage in extended discussion of the similarities and differences between this object and other classes of objects (§[6](#sec:WhatIsIt)) before concluding that we do not know exactly what this object is (§[7](#sec:conclusion)). Several appendices present additional spectra (§[8](#appendix:totalpowerspectra)), detailed chemical models (§[9](#appendix:chemistry)), and RADEX non-LTE models (§[10](#appendix:radex)).

# Observations

The ACES (ALMA CMZ Exploration Survey) large program (2021.1.00172.L; PI Longmore) observed the Central Molecular Zone (CMZ) with ALMA (the Atacama Large Millimeter/Submillimeter Array) in Band 3. In brief, these data cover six windows: two medium-width covering 86–86.5 and 86.7–87.1 GHz, two broad covering 97.66–99.54 and 99.56–101.44 GHz, and two narrow windows covering 60 MHz centered on HNCO 4–3 ($\nu_\mathrm{rest}=87.925238$ GHz) and HCO$^{+}$ ($\nu_\mathrm{rest}=89.18852$ GHz). The latter two in particular were shifted to try to cover the full range of velocities of CMZ clouds, since their full bandwidth is only $\sim200$ $\mathrm{km~s}^{-1}$. The ACES project covers the whole molecular component of the Galactic center, spanning roughly $-0.6\ensuremath{^{\circ}}<\ell<0.9\ensuremath{^{\circ}}$ and $-0.3\ensuremath{^{\circ}}<b<0.2\ensuremath{^{\circ}}$ with a total area 1200 square arcminutes, though in this work we focus only on the few arcsecond region around the MUBLO. Details of the observational setup are given in Table [\[tab:data_props\]](#tab:data_props).

The measurement sets were produced by the ALMA pipeline using CASA 6.4.1.12 pipeline 2022.2.0.64; these data were retrieved from the ALMA archive and restored on disk. The data were imaged using CASA 6.4.3-2, adopting the same parameters as used in the original ALMA-delivered pipeline products, but with modifications as needed to fix bad cleans (specifically, iterative clean runs that diverged and produced spurious signals), to image windows that were left un-imaged because of size mitigation (the two broad-band windows were often excluded), or to image those said windows with full spectral resolution for the same reason. The continuum data were imaged using the default parameters from the ALMA pipeline, including continuum identification in the UV domain from the ALMA pipeline’s `findcont` task. We have combined the ACES 3 mm data with MUSTANG images from (cite: Ginsburg2020) for display purposes in several figures, but all measurements given below are from the ALMA data alone. The full ACES data are still being processed, so as of this publication, we do not yet have a complete census of the broader context.

In this paper, we focus only on field `aa`, with MOUS (member observation unit set) ID `A001_X15a0_X13c`. During the quality assessment process for the ACES data reduction, we discovered an object with surprisingly large line width in several spectral lines. We label this a Millimeter Ultra Broad Line Object, or MUBLO, since we do not know its nature beyond its observational properties.

To verify that this feature was not an image artifact (though there was no particular reason to suspect it was), we searched the ALMA archive for overlap with this object. Two programs observing the 50 $\mathrm{km~s}^{-1}$ cloud, a molecular cloud centered at roughly $\ell=0.02\ensuremath{^{\circ}}$, $b=-0.08\ensuremath{^{\circ}}$ $v_{LSR}=50$ $\mathrm{km~s}^{-1}$(cite: Tsuboi2009), covered this source. Project 2012.1.00080.S (PI: Tsuboi) in Band 3, which overlaps with the ACES spectral coverage, and 2017.1.01185.S (PI: Mills) in Band 7 with only the 7m array, both cover the MUBLO, though it is at the edge of the field in the latter and subject to high noise. We re-imaged the archival data from both programs using the ACES pipeline. We note that, while images and cubes were obtained from the 2012.1.00080.S project, and the results below are reasonable, there are some artifacts that persist in that data set that lead us to assign lower credence to differences between those and the ACES data. The problems with the 2012 data set are severe enough that we choose not to show any of the images and strongly caution against interpreting the measurements of these data based only on their statistical errors. Nevertheless, the spectral line measurements from the 2012 data show a few additional detections (see §[3.1](#sec:spectralmeasurements)), and the consistent detections of overlapping lines gives us high confidence that the ACES detections are not spurious.

The relevant observational parameters, including uncertainties and beam sizes, are given in Table [\[tab:data_props\]](#tab:data_props).

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Data Type | Observation Date | Major | Minor | PA | RMS | Jy/K | $\nu_{min}$ | $\nu_{max}$ |
|  |  | $\mathrm{{}^{\prime\prime}}$ | $\mathrm{{}^{\prime\prime}}$ | $\mathrm{{}^{\circ}}$ | $\mathrm{mJy\,beam^{-1}}$ |  | $\mathrm{GHz}$ | $\mathrm{GHz}$ |
| Continuum |  |  |  |  |  |  |  |  |
| (2012.1.00080.S) | 2013-05-31T09:52:50.256001 | 2.359 | 1.397 | 86.991 | 0.4 | 44.0 | 85.2491 | 98.4496 |
| Continuum |  |  |  |  |  |  |  |  |
| (2017.1.01185.S) | 2018-09-27T21:30:24.144000 | 4.337 | 2.519 | 88.344 | 8.8 | 0.9 | 342.2384 | 357.9871 |
| Continuum spw33+35 |  |  |  |  |  |  |  |  |
| (2021.1.00172.L) | 2022-09-15T00:26:52.128000 | 1.538 | 1.306 | -59.907 | 0.2 | 61.4 | 97.6648 | 101.4321 |
| Continuum spw25+27 |  |  |  |  |  |  |  |  |
| (2021.1.00172.L) | 2022-09-15T00:26:52.128000 | 1.837 | 1.468 | -70.832 | 0.2 | 60.5 | 85.9664 | 87.1328 |
| spw25 | 2022-09-16T00:31:34.272000 | 1.926 | 1.573 | -71.850 | 3.1 | 54.3 | 85.9664 | 86.4328 |
| spw27 | 2022-09-16T00:31:34.272000 | 1.945 | 1.566 | -72.502 | 3.2 | 53.1 | 86.6665 | 87.1328 |
| spw33 | 2022-09-15T00:26:52.128000 | 1.626 | 1.440 | -52.088 | 3.4 | 53.7 | 97.6648 | 99.5394 |
| spw35 | 2022-09-16T00:31:34.272000 | 1.570 | 1.293 | -67.596 | 2.6 | 59.6 | 99.5619 | 101.4321 |

The data types labeled spw`nn` (spw is an abbreviation of spectral window) are from the ACES 2021.1.00172.L data. The 2017.1.01185.S data are from the 7m array at ALMA, while the other data sets are from the 12m array.

# Measurements

We report measurements of the spectral lines (§[3.1](#sec:spectralmeasurements)), the spatial location of both the lines and continuum (§[3.2](#sec:spatialmeasurements)), the spatial-spectral structure (§[3.3](#sec:spatio-spectral)), and the continuum (§[3.4](#sec:continuum)) in this section.

## Spectral

We detect lines of CS, SO, and SO$_2$ listed in Table [\[tab:spectral_measurements\]](#tab:spectral_measurements). We fitted Gaussian line profiles to the detected lines, and for CS 2-1 and SO 2(3)-1(2), we included foreground absorption components in our models (Figure [1](#fig:fittedspectra)). The line widths are $\sigma=60$–70 $\mathrm{km~s}^{-1}$(FWHM $\sim160$ $\mathrm{km~s}^{-1}$).

![image](f1) ![image](f2)

Figures [2](#fig:coarse_spectra) and [3](#fig:other_spectra) show spectra of many candidate lines smoothed to 5 $\mathrm{km~s}^{-1}$ resolution. These spectra are extracted from the peak emission location, i.e., ICRS equatorial coordinates 17h45m57.75s $-28\ensuremath{^{\circ}} 57'10.77"$.

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Species | Rest Freq | Amp | $\sigma_{A}$ | Center | $\sigma_{\nu,cen}$ | $v_{cen}$ | $\sigma_{v,cen}$ | FWHM | $\sigma_{FWHM}$ |
|  | $\mathrm{GHz}$ | $\mathrm{K}$ | $\mathrm{K}$ | $\mathrm{GHz}$ | $\mathrm{GHz}$ | $\mathrm{km\,s^{-1}}$ | $\mathrm{km\,s^{-1}}$ | $\mathrm{km\,s^{-1}}$ | $\mathrm{km\,s^{-1}}$ |
| CS 2-1 | 97.980950 | 1.032 | 0.044 | 97.9656 | 0.0010 | 47.1 | 3.1 | 164.5 | 6.7 |
| SO 2(3)-1(2) | 99.299870 | 1.748 | 0.025 | 99.2866 | 0.0004 | 40.1 | 1.1 | 161.2 | 2.6 |
| $^{34}$SO 2(3)-1(2) | 97.715317 | 0.216 | 0.024 | 97.7039 | 0.0026 | 34.9 | 8.0 | 146.8 | 19.7 |
| SO 2(2)-1(1) | 86.093950 | 0.383 | 0.026 | 86.0829 | 0.0015 | 38.5 | 5.3 | 159.6 | 12.6 |
| SO$_2$ 2(2,0)-3(1,3) | 100.878105 | 0.172 | 0.029 | 100.8748 | 0.0048 | 9.9 | 14.3 | 173.9 | 33.6 |
|  |  |  |  |  |  |  |  |  |  |
| 2012 |  |  |  |  |  |  |  |  |  |
| C$^{34}$S 2-1 | 96.412951 | 0.139 | 0.021 | 96.3966 | 0.0034 | 50.8 | 10.6 | 139.8 | 24.9 |
| CS 2-1 | 97.980950 | 0.538 | 0.027 | 97.9676 | 0.0011 | 40.7 | 3.5 | 158.6 | 7.7 |
| $^{34}$SO 2(3)-1(2) | 97.715317 | 0.129 | 0.015 | 97.6974 | 0.0031 | 54.8 | 9.4 | 168.8 | 22.1 |

The columns with $\sigma$ values give the uncertainty on their neighbors (e.g., $\sigma_A$ is the uncertainty on the amplitude). All values are from Gaussian fits to the line profile, so the widths are the Gaussian width parameter, not the FWHM.

![image](f3) ![image](f4)

![image](f5) ![image](f6)

## Spatial

We fitted 2D Gaussian profiles to the continuum and integrated intensity images in all three data sets. The fit parameters from both the continuum and spectral line fits are in Table [\[tab:spatial_measurements\]](#tab:spatial_measurements). The uncertainties in this table give only the statistical errors, but all of the spatial measurements are likely affected by systematic errors that are larger; we expect the dominant systematic uncertainty to be from separation between the structured background brightness and the compact Gaussian. While the statistical errors appear to show significant offsets between the different measurements, we regard these as unlikely to be real given the systematic uncertainty. Figure [4](#fig:continuumandmom0) shows the 3 mm continuum image from the ACES data alongside the integrated intensity (moment-0) images of CS 2-1 and SO 2(3)-1(2).

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:---|:---|:---|
| Image | Amp | Amp\[mJy\] | RA off | Dec. off | Major | Minor | PA |
|  | $\mathrm{K}$ | $\mathrm{mJy}$ | $\mathrm{marcsec}$ | $\mathrm{marcsec}$ | $\mathrm{{}^{\prime\prime}}$ | $\mathrm{{}^{\prime\prime}}$ | $\mathrm{{}^{\circ}}$ |
| SO 2(3)-1(2) m0 | 148.3 (1.1) | 2795.0 (21.0) | -149 (5) | 4 (5) | 1.549 (0.012) | 1.816 (0.014) | 205.1 (1.9) |
|  |  |  |  |  | 0.85 | 0.51 | -81.16 |
| CS 2-1 m0 | 55.65 (0.76) | 1021.0 (14.0) | -22 (14) | -6 (11) | 2.555 (0.035) | 1.928 (0.026) | 86.0 (1.9) |
|  |  |  |  |  | 2.04 | 1.17 | 80.22 |
| CS 2-1 2012 m0 | 39.36 (0.46) | 1459.0 (17.0) | 411 (21) | 96 (16) | 4.34 (0.051) | 3.299 (0.039) | 95.9 (1.7) |
|  |  |  |  |  | 3.38 | 2.80 | -78.42 |
| Continuum spw33+35 | 0.1036 (0.0029) | 1.77 (0.05) | 20 (20) | 62 (18) | 1.73 (0.049) | 1.499 (0.043) | 85.3 (8.0) |
|  |  |  |  |  | 0.99 | 0.43 | 60.15 |
| Continuum spw25+27 | 0.1077 (0.0022) | 1.758 (0.035) | -55 (16) | 149 (15) | 1.971 (0.04) | 1.783 (0.036) | 62.4 (8.2) |
|  |  |  |  |  | 1.22 | 0.21 | 33.67 |
| Continuum 2012 cont | 0.0906 (0.0031) | 1.479 (0.05) | -34 (27) | 304 (18) | 1.958 (0.066) | 1.245 (0.042) | 436.3 (2.9) |
|  |  |  |  |  | \- | \- | \- |
| Continuum B7 | 0.0896 (0.0037) | 98.2 (4.0) | 371 (53) | 569 (40) | 1.3 (0.13) | 0.993 (0.096) | 88.3 (6.1) |
|  |  |  |  |  | \- | \- | \- |

The Amp and Amp\[mJy\] values are in K $\mathrm{km~s}^{-1}$ and Jy/beam $\mathrm{km~s}^{-1}$ for the spectral lines. The RA off and Dec. off columns give offsets from the coordinate 17h45m57.753s -28d57m10.769s. Under the Major, Minor, and PA columns, the alternating rows with no errorbars give the beam-deconvolved sizes.

## Spatio-Spectral

The integrated and peak intensity maps of the detected emission lines are spatially weakly resolved. The deconvolved size is $\sim1\ensuremath{''}\times0.5\ensuremath{''}$ (see Table [\[tab:spatial_measurements\]](#tab:spatial_measurements)).

There is a weak sign of a spatial velocity gradient. We fitted 2D Gaussian profiles to each channel in the SO 2(3)-1(2) cube, but found that the fits were too unreliable at the modest S/N in each channel. We therefore collapsed the red (64 to 152 $\mathrm{km~s}^{-1}$) and blue ($-68$ to 34 $\mathrm{km~s}^{-1}$) sides of the cube into moment-0 images, excluding an extended cloud that created narrow absorption and emission features around 45 $\mathrm{km~s}^{-1}$. Figure [5](#fig:SOredblue) shows the result of this fitting. We find that the red and blue sides of the spectrum are spatially separated at $\sim10\sigma$ significance (and unlike the measurements in [3.2](#sec:spatialmeasurements), the systematic uncertainties in the red and blue measurements are expected to cancel out). The separation is 2000$\pm200$ au assuming $d=8$ kpc over a 112 $\mathrm{km~s}^{-1}$ difference, resulting in a gradient of 11,000 $\mathrm{km~s}^{-1}$ pc$^{-1}$. Repeating the same measurement with CS 2-1 shows a gradient in the same direction, but with a much larger amplitude and lower signal-to-noise ratio; the CS measurement was more affected by contamination from extended CMZ clouds.

![image](f10) ![image](f11)

## Continuum

We detect continuum emission in bands 3 and 7. Assuming the continuum comes from a single point source, which is consistent with the measurements in Table [\[tab:spatial_measurements\]](#tab:spatial_measurements), the spectral index is $\alpha=3.25\pm0.06$ (statistical) $\pm0.17$ (systematic, adopting 10% calibration uncertainty), indicating that the emission is coming from dust that is mostly optically thin. Adopting a standard dust opacity for protostellar cores (cite: Ossenkopf1994), assuming T=20 K and gas-to-dust mass ratio 100 (so the mass in $\kappa$ is the total gas+dust mass), we estimate the mass from both frequencies: $$\begin{equation}
    M=47~\ensuremath{\mathrm{M}_\odot}\left(\frac{S_\mathrm{102 GHz}}{1.8 \mathrm{mJy}}\right) \left(\frac{T}{20\mathrm{~K}}\right)^{-1} \left(\frac{\kappa}{0.002\mathrm{~cm^{2}~ g^{-1}}}\right)^{-1} \left(\frac{D}{8 \mathrm{~kpc}}\right)^2,
\end{equation}$$ $$\begin{equation}
M=35~\ensuremath{\mathrm{M}_\odot}\left(\frac{S_\mathrm{350 GHz}}{98 \mathrm{mJy}}\right) \left(\frac{T}{20\mathrm{~K}}\right)^{-1} \left(\frac{\kappa}{0.018\mathrm{~cm^{2}~ g^{-1}}}\right)^{-1} \left(\frac{D}{8 \mathrm{~kpc}}\right)^2.
\end{equation}$$ The millimeter dust opacity is low, $\tau<0.01$, at both frequencies. The column density, $N(H_2)\sim4\times10^{23}$ $\mathrm{cm}^{-2}$, corresponds to extinction $A_K\approx20$. For the Band 3 (B3) source size of $r\approx5000$ au, assuming spherical symmetry, the molecular number density is $n(\mathrm{H}_2)\sim10^7$ $\mathrm{cm}^{-3}$. Combining the dust mass with the CS and SO line widths, the energy in the gas is very large, $E_{kin} = 5\times10^{48}\mathrm{~erg} \left(\frac{M}{50 \ensuremath{\mathrm{M}_\odot}}\right) \left(\frac{\sigma_v}{70 \ensuremath{\mathrm{km~s}^{-1}}}\right)^2$.

We caution that the dust properties assumed above might not be appropriate for all of the types of sources considered in the explanations for the MUBLO discussed in §[6](#sec:WhatIsIt). Some aspects of non-standard dust properties are discussed in §[4.4](#sec:weirddust).

To further constrain the dust properties, we extract limits from multiwavelength data. From the Spitzer (cite: Ramirez2008; Carey2009) and Herschel (cite: Traficante2011) data, we adopt the surface brightness at the position of the source as an upper limit, since in all wavelengths, there is significant extended emission. Table [\[tab:sed\]](#tab:sed) gives the upper limits we determine at each wavelength. Figure [6](#fig:SED) shows the SED with modified blackbody models overlaid. The modified blackbodies are labeled with the adopted temperature in K and column density in $\mathrm{cm}^{-2}$ assuming $\beta=1.5$. For a modified blackbody with a power law opacity function, $\kappa\propto\nu^\beta$, the allowed range of dust temperatures is $15 \lesssim T \lesssim 50$ K: the 850 $\mathrm{\mu m}$ data point sets the temperature lower limit, while the 24 $\mathrm{\mu m}$ and 70 $\mathrm{\mu m}$ upper limits from Spitzer and Herschel data set the temperature upper limits (Figure [6](#fig:SED)).

![](f12)

|                  |                         |               |               |
|:----------------:|:-----------------------:|:-------------:|:-------------:|
|    Wavelength    |   Surface Brightness    |   Beam Area   |     Flux      |
| $\mathrm{\mu m}$ | $\mathrm{MJy\,sr^{-1}}$ | $\mathrm{sr}$ | $\mathrm{Jy}$ |
|       3.6        |         51.613          |   1.065e-10   |    0.0055     |
|       4.5        |         62.788          |   1.065e-10   |    0.00669    |
|       5.8        |         211.374         |   1.065e-10   |    0.0225     |
|       8.0        |         492.624         |   1.065e-10   |    0.0525     |
|       24.0       |        1304.027         |   9.588e-10   |     1.25      |
|       70.0       |        26726.094        |   2.764e-09   |     73.9      |
|      160.0       |        26034.621        |   4.887e-09   |      127      |
|      250.0       |        12025.196        |   1.451e-08   |      175      |
|      350.0       |        4771.450         |   2.442e-08   |      117      |
|      500.0       |        1484.628         |   4.794e-08   |     71.2      |
|      850.0       |         299.154         |   3.283e-10   |    0.0982     |
|      2939.1      |         18.810          |   9.412e-11   |    0.00177    |
|     60000.0      |          1.481          |   7.484e-11   |   0.000111    |
|     200000.0     |         12.638          |   4.261e-10   |    0.00539    |

Except for the ALMA measurements at 3 mm and 850 $\mathrm{\mu m}$, these values are upper limits.

# Analysis

In this section, we attempt to measure the gas temperature by modeling the SO lines under simple conditions (§[4.1](#sec:LTE)). We then allow for greater complexity in the excitation (§[4.2](#sec:nonlte)) and chemistry (§[4.3](#sec:chemistry)). Finally, we explore the possibility that the dust has atypical properties (§[4.4](#sec:weirddust)).

## LTE Modeling

We detect two transitions of SO with different energy levels and obtain an upper limit on a third, allowing us to make a rotational diagram and fit the temperature and column density assuming local thermodynamic equilibrium (LTE) conditions, which is reasonable assuming the above density. The temperature from the SO 2(3)-1(2) to 2(2)-1(1) line ratio is $T=14.1\pm 1.4$ K (Figure [7](#fig:LTErotationdiagram); however, see [4.2](#sec:nonlte)).

![](f13)

We overplot a model emission spectrum based on the LTE fit on the spectral data. Figure [8](#fig:LTEmodel)a shows the best-fit model for SO overlaid on the ACES data, and Figure [8](#fig:LTEmodel)b shows the model on the 2012 data. In both figures, the CS and SO$_2$ column densities are scaled to fit the data while assuming the fitted SO rotational temperature. Lines of C$^{34}$S and $^{34}$SO are also detected, giving a ratio $^{32}$S/$^{34}$S $\approx$ 8, consistent with some measurements in the Galactic center (cite: Yu2020) but inconsistent with others that find $^{32}$S/$^{34}$S$=16\pm4$ (cite: Humire2020) or $=19\pm2$ (cite: Yan2023). The column density is $\mathrm{N(SO)}=4\times10^{15}$ $\mathrm{cm}^{-2}$. Assuming the same temperature for the other molecules, we obtain column densities N(CS)=$10^{15}$ $\mathrm{cm}^{-2}$, N(C$^{34}$S)=$1.2\times10^{14}$ $\mathrm{cm}^{-2}$, N(SO$_2$)=$2\times10^{16}$ $\mathrm{cm}^{-2}$, and N($^{34}$SO)=$5\times10^{14}$ $\mathrm{cm}^{-2}$. These estimates are dominated by systematic uncertainty in the excitation temperature, which may be more than an order of magnitude. At these column densities, the peak line optical depth is $\tau \sim 0.1$, so the lines are still well-approximated as optically thin.

In these same figures (Fig. [8](#fig:LTEmodel)), we show model emission lines with the same centroid, linewidth, and excitation temperature for non-detected lines that we would expect to see in typical molecular and/or shocked gas: $\mathrm{H}^{13}\mathrm{CO}^+$, H$^{13}$CN, and SiO. The models correspond to parts of the spectrum with no detection, so they give a rough upper limit on the column densities of these molecules. For $\mathrm{H}^{13}\mathrm{CO}^+$, the figure appears to show a detection, but this emission comes from the diffuse medium, not the MUBLO.

SO and CS appear to be $\gtrsim100\times$ more abundant than H$^{13}$CO$^{+}$, H$^{13}$CN, HC$_3$N, and SiO. If we adopt the dust-derived column density $N(\mathrm{H
}_2)\approx4\times10^{23}$ $\mathrm{cm}^{-2}$, the abundances relative to H$_2$ are $X_\mathrm{SO}\approx10^{-8}$, $X_\mathrm{CS}\approx2\times10^{-9}$, $X_\mathrm{H^{13}CO^+} \sim X_\mathrm{H^{13}CN} < 5\times10^{-11}$, $X_\mathrm{SiO}<10^{-10}$, and $X_\mathrm{HC_3N} < 1\times10^{-10}$.

## Non-LTE conditions?

If our mass measurement above is overestimated, the SO lines could be out of LTE, which could significantly change the above abundance and column density calculations.

Non-LTE models confirm the LTE column density estimate. We ran a grid of RADEX (cite: vanderTak2007) models to test whether non-LTE conditions can match the data. The most useful constraint on the non-LTE physical conditions comes from the intensity ratio of SO 2(3)-1(2)/2(2)-1(1), since this ratio should be mostly unaffected by the unknown filling factor of the emission. Using this measured ratio, $R_{32}=4.6\pm0.3$, and the lower limit on the SO 2(3)-1(2) intensity $S_{32} > 1.75$ K from the filling factor $ff\leq1$, only a narrow range of parameter space is allowed in LTE models: $5\ensuremath{\times 10^{15}} < N(\mathrm{SO}) < 2\ensuremath{\times 10^{16}}$ $\mathrm{cm}^{-2}$ and $5< T < 13$ K. RADEX one-zone models, adopting $dv=70$ $\mathrm{km~s}^{-1}$, give a wide range of solutions for different temperatures. For example, for T=50 K, the H$_2$ density can be $10^{2.5} < n(\mathrm{H}_2) < 10^5$ $\mathrm{cm}^{-3}$ for $10^{16} > N(\mathrm{SO}) > 10^{15}$ $\mathrm{cm}^{-2}$(see Appendix [10](#appendix:radex)). Values of column density $>0.5$ dex from the LTE model are not allowed even under non-LTE conditions, though the temperature is essentially unconstrained by the RADEX models. However, if we incorporate our estimate of the H$_2$ number density based on the dust, the non-LTE models are ruled out: all of the high-temperature ($T\gtrsim20$ K) models require low densities ($n(\mathrm{H}_2)<10^{5.5}$ $\mathrm{cm}^{-3}$). Additionally, the Meudon PDR models that match the low HCN/CS upper limit and the CS/SO ratio require high density ($n(\mathrm{H}_2)\gtrsim10^7$ $\mathrm{cm}^{-3}$); see §[4.3](#sec:chemistry) below and Appendix [9](#appendix:chemistry). We therefore disfavor the non-LTE, low-density model, but additional observations to further test this hypothesis by imaging other SO lines are straightforward and should be performed.

## Chemical Modeling

We have run chemical models to search for physical parameter space consistent with the observations. We ran both Meudon PDR (cite: LePetit2006) and UCLCHEM (cite: Holdship2017) models.

Using the time-dependent gas grain open-source chemical code UCLCHEM[^1] (cite: Holdship2017), we ran models of a collapsing cloud that varied in final densities, UV irradiation, cosmic ray ionization rate, and temperatures. The complete description of the models can be found in Appendix [9.2](#sec:uclchem). In brief, there is ample room in radiation field-temperature-density-cosmic ray ionization rate parameter space that produces high SO/SiO ratios (SO/SiO$>100$). This ratio is produced by more models for longer time periods at higher densities ($n\gtrsim10^6$ $\mathrm{cm}^{-3}$) and temperatures ($T\sim50$ K). With the present data set, these chemical models do not rule out any of the physical models considered below, but they point in constructive directions for what can be observed next to better understand the MUBLO.

We ran Meudon PDR[^2] (cite: LePetit2006) models spanning a range of extinction, cosmic ray ionization rate, density, and UV field (see Appendix [9](#appendix:chemistry)). The Meudon model predicts line intensities in addition to abundances, so we compare to the predicted intensities for these models. The observed line ratio SO 3(2)$-$2(1) / CS 2$-$1 can be reproduced at high density ($n_\mathrm{H}\sim10^7$ $\mathrm{cm}^{-3}$) for a wide range of cosmic ray ionization rates (CRIR, $10^{-17} < \zeta_\mathrm{CR} < 10^{-15}$ $\mathrm{s}^{-1}$). At lower density, $n_\mathrm{H}\sim10^5$, the intensity ratio is at least an order of magnitude below what we observe. The Meudon models therefore favor higher densities and support adopting LTE conditions for SO excitation modeling.

## Weird dust?

Since we do not know that the dust is protostellar, we evaluate other possibilities. (cite: Bianchi2007) adopt a simple power law for dust in supernovae, which becomes $\kappa_\mathrm{100 GHz}=0.4\left(\frac{100\ensuremath{\mathrm{\mu m}}}{3 \mathrm{mm}}\right)^{1.4}=0.0034$ cm$^2$ g$^{-1}$, a factor of two larger than we assumed; supernova dust would be only marginally different from our assumptions. Following (cite: Kaminski2019), who modeled dust in the circumstellar envelope of evolved star VY CMa, we extrapolate the (cite: Draine1984) opacities to be $\kappa_\mathrm{102 GHz}=0.00032$ and $\kappa_\mathrm{350 GHz}=0.0040$. If the dust is like that in VY CMa, the mass is substantially ($\sim5\times$) larger than we reported. (cite: Draine2006) gives a range of dust opacities from $0.0003<\kappa_\mathrm{102 GHz} < 0.03$ cm$^2$ g$^{-1}$, where the large end of this range corresponds to carbonaceous dust (pyrolized cellulose) that is too opaque to comprise a significant amount of the ISM. If the dust is comprised primarily of carbon, the mass may be as much as $15\times$ smaller than we reported, a mere 2 $\mathrm{M}_\odot$ of gas, though this possibility is especially unlikely given the large column density of SO and SO$_2$ detected, which indicate that the medium is not especially carbon-rich.

In all of the above measurements, we have adopted a standard gas-to-dust ratio of 100. If we were looking at a hydrogen-free object, comprised entirely of dust, the mass would be quite small, merely $\sim0.5$ $\mathrm{M}_\odot$. Such tötally mëtal objects have been suggested to be possible to assemble in the turbulent ISM (cite: Hopkins2014), but there is no immediate reason to expect it to exhibit extreme line widths.

Reservoirs with $\sim{}0.5\,\ensuremath{\mathrm{M}_\odot}$ in dust alone have been inferred in some supernova remnants and evolved stars. (cite: Kaminski2019) suggests that the envelope of VY CMa might contain $0.5\,\ensuremath{\mathrm{M}_\odot}$ of dust (see also §[6.2](#sec:evolvedstars) below), but (as (cite: Kaminski2019) points out) this value is uncertain because of the substantial optical depths involved in this calculation. (cite: Chawner2019) infer dust reservoirs of 0.3–$0.5\,\ensuremath{\mathrm{M}_\odot}$ in pulsar wind nebulae based on Herschel data. Given stellar masses $\ll10^2\,\ensuremath{\mathrm{M}_\odot}$ that produced these quantities of dust, there must be gas-to-dust mass ratios $\ll10^2$, higher dust opacities than assumed in the respective analysis, or both. Such work demonstrates that, under certain conditions, continuum emission at an intensity seen in the MUBLO can be produced by gas reservoirs well below the nominal value of $M_\mathrm{gas}\sim{}50\,\ensuremath{\mathrm{M}_\odot}$ from §[3.4](#sec:continuum).

# Where is it?

While the MUBLO is seen in projection close to the Galactic Center, only 5$'$ from Sgr A\*, its line-of-sight location has to be determined. In this section, we cover the evidence that it is genuinely in the Galactic Center, likely 10-100 pc from Sgr A\*.

## Line-of-Sight Location

The line-of-sight velocity $v_\mathrm{LSR} \approx 40-50$ $\mathrm{km~s}^{-1}$ is similar to other Galactic Center objects. There are absorption lines seen in front of the broad lines, and these are clearly from Galactic Center gas based on their continuity with clouds that are definitely in the CMZ (the “three little pigs” and the 50 $\mathrm{km~s}^{-1}$ cloud). Assuming these are genuine absorption features and not interferometric artifacts (it remains difficult to be entirely certain that all interferometric artifacts have been removed, even when working with combined 12m + 7m + TP data), the source cannot be in the foreground of the CMZ. These absorption features are discussed further in Appendix [8](#appendix:totalpowerspectra), which shows the ACES single-dish “Total Power” data extracted from the same position overlaid on the spectrum we have already shown from the 12m data. While it is clear that the MUBLO is behind these Galactic Center clouds, it is possible that it could be in the far side expanding 3 kpc arm (cite: Dame2008), which exists at a similar velocity.

![image](f16) ![image](f17)

## Spatial Location

Figure [9](#fig:bigcontext) shows where the MUBLO resides in the large-scale context of the CMZ, showing both CO and 3 mm continuum images. On these larger scales, the MUBLO resides in an underdensity or cavity in the CO gas (cite: Tokuyama2019). Figure [10](#fig:sourceoncloud) shows the object in its local context from the ACES data, indicating that there is surrounding molecular gas but that this gas is not particularly associated with the MUBLO. The gas seen in Figure [10](#fig:sourceoncloud) is sparser than in the neighboring dense clouds seen in Figure [9](#fig:bigcontext); it is the wispy edge of the clouds seen on the larger scales.

![image](f18) ![image](f19)

We next check multiwavelength archival data for any counterparts to this source. Figure [11](#fig:nircontinuum) shows contours from the ACES data overlaid on high-resolution NIR images from the GALACTICNUCLEUS (cite: Nogueras-Lara2018; Nogueras-Lara2019) and HST (cite: Dong2011) surveys. No source is evident in the NIR data at the location of the MUBLO. If anything, there is a hint of a deficit of flux at the position of the MUBLO in the HST images, which could be caused by the dust extinguishing background sources. Archival images from the Hubble Legacy Archive in the F127M, F139M, and F153M filters show this feature more distinctly (cite: Whitmore2016). We also checked the surrounding sources from (cite: Shahzamanian2022) within $r<10\ensuremath{''}$ and saw no obvious pattern in the proper motions of nearby sources that might indicate a recent runaway or a particularly deep potential well. We searched Vizier (cite: Ochsenbein2000) for any public catalogs with a source at this location at any wavelength and found no compelling counterparts. The closest sources listed in any catalog are $>1$$''$  away, and these can readily be seen to be outside the contours of the MUBLO in Figure [11](#fig:nircontinuum).

![image](f23) ![image](f24)

We further checked longer-wavelength data. Figure [12](#fig:contcutouts) shows this source in context, with cutouts of the GLIMPSE (cite: Churchwell2009), MIPSGAL (cite: Carey2009), HiGal (cite: Molinari2010), VLA C-band (cite: Lu2019), and MEERKAT (cite: Heywood2022) surveys. The only detections are with ALMA at 3 mm and 0.85 mm. This source is unfortunately not covered by the mm-wavelength survey CMZoom (cite: Battersby2020).

![](f25)

No X-ray sources are present at this location. The closest cataloged source is $>7\ensuremath{''}$ away (cite: Muno2009). We have examined recently taken Chandra X-ray data (Vikhlinin et al. in prep.) comprising 708 ksec effective integration at this location. The 3$\sigma$ upper limit is $<2.8\times10^{-5}$ counts/s in the 3-8 keV band, equivalent to $S_{X}<7\times10^{-16}$ erg $\mathrm{s}^{-1}$$\mathrm{cm}^{-2}$ assuming a $\gamma=2$ power-law spectrum.

# What is it?

We have demonstrated the existence of a dusty, broad-linewidth source that is detected only at millimeter wavelengths. Given this limited information, we now attempt to classify the object.

We consider many options. Plausible mechanisms include: protostellar outflow, explosive outflow, protostellar inflow, ejecta from an evolved star, (pre)-planetary nebula, stellar collision, high-velocity compact cloud (HVCC), intermediate-mass black hole (IMBH), galaxy, or supernova. We evaluate each of these hypotheses in the following sections, but find that none satisfactorily explain the data.

## Something associated with star formation

Star formation is prevalent in the Galactic Center, with roughly 10% of the Galaxy’s star formation occurring in the central $r<100$ pc (cite: Longmore2013; Barnes2017; Henshaw2023). We therefore evaluate several hypotheses associated with star formation. Star-forming regions are naturally dust- and molecule-rich. We consider whether the MUBLO is a protostar (§[6.1.1](#sec:protostar)), a typical protostellar outflow (§[6.1.2](#sec:protostellaroutflow)), an explosive outflow (§[6.1.3](#sec:explosion)), a protostellar inflow (§[6.1.4](#sec:inflow)), a protostar collision (§[6.1.5](#sec:protostarcollision)), or a prestellar core collision (§[6.1.6](#sec:corecollision)). While these hypotheses can explain some of the bulk properties of the MUBLO, they all fail in the details, particularly energetics, morphology, and chemistry.

### Protostar

Before digging into the specific models to explain the gas, we evaluate what kind of central source is allowed by the observed dust SED described in §[3.4](#sec:continuum). Using the (cite: Richardson2024) update to the (cite: Robitaille2017) grid, we searched for models consistent with either of the two ALMA millimeter detections (we did not require that both measurements match the models since the model grid does not allow for a varying $\beta$ parameter). We search for models that have flux density within $5000$ au apertures matching the ALMA measurements to within 25% and falling below the 24 and 70 $\mathrm{\mu m}$ upper limits. There is a narrow range of parameter space compatible with the ALMA measurements and Herschel and Spitzer upper limits, all with $10^4 < L < 10^{4.7}~\ensuremath{\mathrm{L}_\odot}$ and $3<M_{\mathrm{gas}}(<5000~\mathrm{au})<28$ $\mathrm{M}_\odot$. While these objects are part of the model grid, they are not compatible with most models of star formation, since the implied central source is an $M\gtrsim10\ensuremath{\mathrm{M}_\odot}$ star that is surrounded by a comparable amount of cold gas in a stable envelope-plus-disk configuration. Instead, these models demonstrate that there exist solutions in which high-luminosity, but still $L<10^5$ $\mathrm{L}_\odot$, stars may be embedded in dusty envelopes that produce enough millimeter-wavelength emission while not exceeding the short-wavelength limits.

### Protostellar outflow

The hypothesis that the object is a protostellar outflow from a previously-unknown star-forming region is plausible. However, there is a good deal of evidence that suggests this is not the correct interpretation:

1.  The limited number of emission lines detected, and especially the lack of SiO, would make this outflow unlike any others in the Galaxy. Admittedly, our sensitivity to CO is limited, since it was only covered in the coarse spatial resolution B7 data such that diffuse molecular gas along the line of sight is confused with and may absorb any compact emission associated with the MUBLO.

2.  It is surprisingly compact, $<10^4$ au, which suggests that it is almost perfectly face-on (any angle would produce an extended, red/blue bipolar signature). Similarly, the small value of the spatial gradient with velocity suggests that it is face-on. This situation is unlikely, but possible.

3.  The line profile is Gaussian. Such a profile is unexpected for a straight-on outflow, which would more likely include some sharper features or flattening from the high velocity tails. However, if the material we observe is entirely entrained ISM, a Gaussian profile is not impossible.

4.  Assuming this is a face-on outflow-driving source, we would expect to see the central YSO (young stellar object) at infrared wavelengths. The nondetection at wavelengths short of 850 $\mu$m suggests either that there is a very optically thick dust envelope or that the driving source is low-mass and low-luminosity.

5.  The source appears isolated, with no surrounding sources at any wavelength, and very little surrounding cloud material. YSOs are not often found in such environments.

6.  High-velocity outflows are expected to produce high-velocity shocks in the dense interstellar medium gas. The lack of SiO emission and the low inferred temperature both imply that there are no high-velocity shocks. This evidence is the most problematic for the protostellar outflow hypothesis.

7.  Such massive (50 $\mathrm{M}_\odot$), compact ($<10^4$ au) cores are rarely observed and are generally much hotter (cite: Bonfand2017; Bonfand2024; Jeff2024; Budaiev2024).

A protostellar source is not strictly ruled out, but is very unlikely.

### Explosive outflow

Could this be an explosive outflow at an early stage analogous to Orion BN/KL (cite: Bally2015; Bally2017)?

For this hypothesis to hold, the explosion must be very young, with $t\approx 10^4$ au / 70$\mathrm{km~s}^{-1}$$\approx$700 yr. An isotropic explosion is consistent with the line profile.

This hypothesis has several problems in common with the protostellar outflow hypothesis: there is little surrounding interstellar medium, there is no associated infrared emission (especially near-infrared H$_2$ and \[Fe II\], which would show up in K-band), there is no shocked SiO emission, and the excitation temperature is very low. The Orion BN/KL outflow is bright in all of these features that are not detected toward the MUBLO.

### Protostellar Inflow

Could this be a site where large amounts of material are inflowing toward a central, collapsing source? This hypothesis explains the lack of infrared detection, but otherwise fails to explain all the main observables. In particular, the huge linewidth is unexpected for a collapsing source unless it is extremely massive (see §[6.4](#sec:imbh)). We would also expect to see an accretion shock, which might be expected to produce hot line emission.

### Protostellar Collision

Protostars are likelier to collide than their main-sequence counterparts. They are bloated during their early phases as they radiate away their gravitational energy, and they reside in a dissipative medium that can result in multiple systems inspiraling. A protostellar collision would appear similar to a later-stage stellar merger as described in §[6.2.2](#sec:merger). We defer further discussion to that section.

### Prestellar Core Collision

Gas falls in along the Galactic bar at high velocity, impacting the central molecular zone at high speeds (cite: Sormani2019; Gramze2023). If dense prestellar cores were to form along the Galactic bar’s dust lanes and impact one another in the center of the Galaxy, the high observed velocity dispersion could be produced. However, in doing so, extremely strong shocks should occur, and therefore we would expect to see bright SiO emission. Furthermore, this scenario is intrinsically unlikely, as the free-fall timescale for a prestellar core with half the mass of the MUBLO (assuming two equal-mass cores, the most conservative limit) is only 25 kyr, so these cores would have had to have formed extremely recently.

## Evolved Star

Could this be some sort of evolved star, such as an asymptotic giant branch or red supergiant star with an extreme wind? These mass-losing stars are generally detected in emission from sulfur-bearing species (cite: Omont1993). The main evidence against this hypothesis is the lack of an infrared source, though the lack of an SiO $v$=1 maser in the ACES data is also weak evidence against the MUBLO being an evolved star (cite: Verheyen2012)). These end-of-life stars are generally extremely luminous; the known red supergiants in the Galactic center have observed K-band magnitudes $m_K < 6$ (cite: Schultheis2020).

It is theoretically possible that one could be hidden by a very high column density of dust produced in its own wind, similar to the R Coronae Borealis stars and OH/IR red supergiants like VY CMa (cite: Humphreys2024), or episodic mass loss leading to events like Betelgeuse’s Great Dimming (cite: Montarges2021; Levesque2020), but the high column density required for this mechanism to completely block the star’s infrared light would make the MUBLO unique. The required local extinction must be $A_K>10$ for an $m_K=6$ star to be undetected in the GALACTICNUCLEUS data (cite: Nogueras-Lara2019); while this amount of dust is compatible with the observed millimeter-derived column density (§[3.4](#sec:continuum)), a $10^5$ $\mathrm{L}_\odot$ star would heat the dust well above the upper limit of $T_D<50$ K (the protostar models discussed in §[6.1](#sec:starformation) demonstrate this point).

VY CMa is a helpful reference case as perhaps the most extreme mass-losing supergiant star in the Galaxy. It is a $L\sim2\times10^5$ $\mathrm{L}_\odot$(cite: Monnier1999) star with $M>2.5\times10^{-4}$ $\mathrm{M}_\odot$ of circumstellar dust (cite: O’Gorman2015). If we were to consider VY CMa as only a millimeter continuum source, it is similar to the MUBLO: its 350 GHz flux, scaled to a distance of 8 kpc, is 40 mJy (cite: O’Gorman2015; Kaminski2013), within a factor of two of the MUBLO. Similarly, its 100 GHz flux (which we extrapolate from Figure B.1 of (cite: O’Gorman2015)) scaled is 2 mJy, about what we measure. However, the dust temperatures they measure are $>10\times$ hotter than allowed by our observational limits. VY CMa is a bright IRAS source, with $S_{25\ensuremath{\mathrm{\mu m}}}=149$ Jy (cite: 1988iras....7.....H; Matsuura2014), which is $>100\times$ the Spitzer MIPS upper limit.

Additionally, the stars that produce the most dust in their winds tend to drive slower winds, while hotter stars that drive faster winds, compatible with the $>70$ $\mathrm{km~s}^{-1}$ we observe, tend to have less massive winds (cite: Kemper2003; Quintana-Lacaci2023). Most of the mass is in lower-velocity material, with $v_{max} < 40~ \ensuremath{\mathrm{km~s}^{-1}}$ (cite: Quintana-Lacaci2023). The molecular winds in these sources are bright in SO, like the MUBLO, but comparably bright in SiO, which the MUBLO is not (cite: Kaminski2013; Matsuura2014; Quintana-Lacaci2023).

The dust mass we infer requires a truly extreme star to reproduce. The only star we know of that has ejected $\sim10\ensuremath{\mathrm{M}_\odot}$ of matter outside of a supernova is $\eta$ Carinae, whose great eruption produced $\sim10~\ensuremath{\mathrm{M}_\odot}$ in only a few years. However, $\eta$ Car bears no observational similarities to the MUBLO. It has narrow molecular lines (cite: Bordiu2022) because most of the ejecta are ionized. The system is also far too bright; its distance-scaled flux is $S_{\mathrm{100 GHz}}\approx3$ Jy (cite: Morris2020), over $10^3\times$ greater than the MUBLO.

### (Pre-)Planetary Nebula

Following along the evolved star route, could this be a star that has evolved past the point of nuclear burning, traveling into the pre- or planetary nebula phase? The planetary nebula hypothesis is unlikely, since there is no sign of ionized gas, but pre-planetary nebulae can be much higher density and cooler. The limited number of molecules detected could be a consequence of some peculiar enrichment process in the star, though we have no model for such a process.

The line width is one possible problem with this hypothesis. In observed PNe/PPNe, the core line width in molecular gas is generally small (cite: Lee2013a; Lee2013b). There are examples of broad lines, though: the Boomerang nebula has $\sim100$ $\mathrm{km~s}^{-1}$ wide absorption from its fastest-expanding material seen in CO (cite: Sahai2017). There are also many $\sim$150 $\mathrm{km~s}^{-1}$ molecular jets detected among (P)PNe (cite: Guerrero2020; Sahai2015). These jets tend to be much fainter broad-wing components next to a central, more massive component, and in at least some cases they have coincident SiO, so the MUBLO would still stand out as unique, but there are analogues.

In one of the most extreme molecular PPN examples, I08005, which has 200 $\mathrm{km~s}^{-1}$ wide CO and SiO lines, no continuum was detected at an upper limit of 1 mJy at 870$\mu$m at a distance of 3 kpc (cite: Sahai2015). The detection of the MUBLO at 90 mJy at 8 kpc at the same wavelength makes it $>400\times$ brighter in the mm continuum than this PPN. This difference suggests that the MUBLO is too dust-rich to be a PPN.

The lack of a detected continuum source at short wavelengths is again a problem for the PPN hypothesis. For a PN, we would not necessarily expect a central continuum source to be detectable in the infrared, but PPN usually have fairly large stellar photospheres and are luminous in the infrared.

While there are some similarities between (P)PN and the MUBLO, most of the evidence suggests that these are not the same class of object.

### Stellar Merger: A Luminous Red Nova

Could the object be the result of stellar merger? Luminous Red Novae (LRN) are a class of transients thought to be associated with stellar mergers, and the MUBLO shares some observational features with the remnants of these events. Stellar mergers are expected to be more common in the high-density inner Galaxy, and may even be the origin of the G objects near the Galactic Center (cite: Ciurlo2020). Stellar mergers that produce luminous red novae are often accompanied by high-velocity, cold molecular outflows (cite: Kaminski2018). The energy released in stellar merger events can be $\sim10^{48}$ erg (cite: Retter2006), comparable to the energy in the MUBLO (§[3.4](#sec:continuum)), though the component in the molecular remnant of these mergers is $\sim10^{46}$ erg (cite: Kaminski2018). The very large energy in the molecular gas in the MUBLO, $E\sim5\times10^{48}$ erg, suggests that a complete merger rather than a glancing collision is more likely; the gravitational energy in a merger of two solar-mass objects is $4\times10^{48}$ erg.

Among the handful of known Galactic LRN, four with mm/submm spectral line observations exhibit SO/SiO ratios ranging from 1 to 7, as reported in studies by (cite: Kaminski2015; Kaminski2018; Kaminski2020). These ratios are notably two orders of magnitude lower than the ratio observed towards MUBLO. Gas temperature estimates from SiO, SO, and SO$_2$ for three of these four sources exceed $T>50$ K, with (cite: Kaminski2018) identifying temperatures above 200 K in SO$_2$, which is substantially higher than the temperature estimates for MUBLO. CK Vul, the oldest RN, stands out as the only exception, with a temperature of 12 K. Therefore, the chemistry and excitation conditions of MUBLO are different from the handful of known RNs.

We explore two examples, V838 Mon and CK Vul, in more detail.

#### V838 Monocerotis

V838 Mon exhibits some similarities to the MUBLO. ALMA observations of V838 Mon 17 years after outburst reveal broad line widths, $v_{\mathrm{fwhm}} \approx 150~\ensuremath{\mathrm{km~s}^{-1}}$, in lines of CO, SO, SiO, and AlOH spread over $\sim 700$ au (cite: Kaminski2021). The integrated intensity of the SO 5(6)-4(5) line in their data is $S\sim9$ Jy $\mathrm{km~s}^{-1}$, which, if converted to a distance of 8 kpc, would drop to $\sim4$ Jy $\mathrm{km~s}^{-1}$($d_{V838}=5.9$ kpc), comparable to the observed integrated intensity of SO 2(3)-1(2) in the MUBLO (Table [\[tab:spatial_measurements\]](#tab:spatial_measurements)). However, they observe an SiO 5-4 / SO 5(6)-4(5) ratio $>2$, while our object has SiO 2-1 / SO 2(3)-1(2) $<0.02$, implying a dramatically different chemistry is present. The continuum observed toward V838 Mon at 1mm is $S\approx2$ mJy (1 mJy at 8 kpc); for comparison, interpolating our observed flux between the B3 and B7 observations, the expected flux of the MUBLO is $S_{1mm}=30$ mJy, so about 30 times brighter.

V838 Mon is also a notably bright infrared source. From 2010 to 2020, it remained at $m_K \lesssim 5$ (cite: Woodward2021), which would be roughly $m_K<6$ at d=8 kpc. The K-band upper limit from GALACTICNUCLEUS is about $m_K > 16$ (cite: Nogueras-Lara2020), so $A_K>10$ would be required to hide a central source like V838 Mon in the MUBLO (and extinction along the Galactic plane is only $A_K\sim3$ toward the Galactic Center). In the mid-infrared, V838 Mon is bright, $S_{19.7 \ensuremath{\mathrm{\mu m}}}=38$ Jy (18 Jy at $d_{\mathrm{GC}}$), while the upper limit from Spitzer 24 $\mathrm{\mu m}$ toward the MUBLO is about 1.3 Jy, which requires $A_{24 \ensuremath{\mathrm{\mu m}}}\approx3$ to hide. At longer wavelengths, V838 Mon is fainter and the limits from Herschel are less stringent.

#### CK Vulpecula

A second comparison source of interest is CK Vulpecula, a LRN that occurred in 1670. Unlike V838 Mon, its SED is a reasonable match to that of the MUBLO. It has long-wavelength fluxes that are comparable to those of the MUBLO; assuming $d_{\mathrm{CK}}=3.2$ kpc (cite: Banerjee2020; Kaminski2021_CKII), its fluxes scaled to $d=8$ kpc are $S_{\mathrm{100 GHz}}\approx2$ mJy, $S_{350 GHz}\approx20$ mJy, $S_{24 \ensuremath{\mathrm{\mu m}}}=1.5$ mJy, and $S_{6 GHz}=0.2$ mJy (cite: Kaminski2015). The millimeter measurements are within a factor of a few of the MUBLO’s measurements, and the others are consistent with the upper limits: CK Vul does not have a detected central source at infrared ($<24$ $\mathrm{\mu m}$) wavelengths. The preferred SED model in (cite: Kaminski2015) has dust with $T=15$ K and $\beta=1$, with inferred central source luminosity[^3] $L\approx20$ $\mathrm{L}_\odot$, and these authors infer a total gas mass of $M=1 \ensuremath{\mathrm{M}_\odot}$ from their CO observations (they do not report a dust mass).

The key differences between CK Vul and the MUBLO are in its emission lines. All of the molecules seen in the MUBLO, SO, SO$_2$, and CS, are detected in CK Vul (cite: Kaminski2020_CKI). However, the SO and SO$_2$ lines in CK Vul are $\gtrsim10\times$ fainter than the SiO lines that are not detected in the MUBLO, and several lines of SO seen in the MUBLO are not detected in CK Vul because they are swamped by transitions from other molecules, e.g., HC$^{15}$N, that are not present in the MUBLO (cite: Kaminski2017). While there is significant emission in CK Vul with FWHM$\sim100-200~\ensuremath{\mathrm{km~s}^{-1}}$ seen in CO and CS, the SO$_2$ lines are narrow, $\lesssim50~\ensuremath{\mathrm{km~s}^{-1}}$ (cite: Kaminski2020_CKI). The abundances of SO, SO$_2$, CS, SiO, and HC$_3$N are all roughly the same (equal within errorbars) in CK Vul (cite: Kaminski2020_CKI), in contrast to the MUBLO, where SO and SO$_2$ are much more abundant than SiO and HC$_3$N. In summary, while CK Vul is quite similar to the MUBLO in the continuum, it is dramatically different in molecular lines.

The stellar merger / luminous red nova hypothesis seems quite plausible, but there remain several features that distinguish the MUBLO from other LRN. The dust mass is substantially larger, by more than an order of magnitude, than observed toward any other merger remnant. There is no hint of a central source at infrared wavelengths, making the MUBLO much more obscured than any previous LRN except CK Vul. The chemistry is dramatically different, with the MUBLO characterized by a lack of SiO. Together, these arguments imply that if the MUBLO is a merger remnant, it was from a merger of more massive stars than previously-observed LRN (to account for the extra mass), and it occurred $>10$ years ago to account for the re-freezeout of SiO (but in old LRN, like CK Vul, SiO has not frozen out). The nova itself should have been extremely luminous, then, and have driven light echoes comparable to those created by V838 Mon - these might then be detectable in scattered light in the infrared if the event was recent enough.

## High Velocity Compact Cloud

There have been many high-velocity compact clouds (HVCCs) reported in the Galactic Center region. These are peculiar clouds characterized by their compact sizes ($d\lesssim 5$ pc) and broad velocity widths ($\Delta V\gtrsim 50$ $\mathrm{km~s}^{-1}$). These have been explained as either material accelerated by supernova explosions, a connecting bridge between colliding clouds, or gas orbiting around invisible massive objects (cite: Oka2014; Oka2016; Oka2022; Iwata2023). The MUBLO shares some properties with HVCCs, specifically the broad line width, but it is much smaller than the known HVCCs. All reported HVCCs have been found with single-dish telescopes, and thus are extended over parsec scales, while the MUBLO has a radius smaller than $r<5000$ au ($r<0.02$ pc). Recent ALMA observations toward two HVCCs detected several unresolved ultracompact clumps (UCCs) with broad velocity width (cite: Takekawa2019; Iwata2023). These differ from the MUBLO in a few observational respects: their line widths are somewhat narrower, they are detected in different lines (CO, CH$_3$OH, SiO, HCN), they do not contain compact millimeter continuum sources, and they are surrounded by and connected to extended high-velocity-dispersion gas. They are therefore unlikely to be the same class of object.

## Intermediate-Mass Black Hole (IMBH)

Given the broad linewidth, it is possible that the MUBLO is comprised of gas in orbit around a very deep potential well. Because of the nondetection at multiple wavelengths, that potential well is dark, so a cluster of stars is an unlikely explanation. We therefore consider whether the object may be an intermediate-mass (of order $10^4$ $\mathrm{M}_\odot$) black hole.

There have been many previous claims of IMBH detections in the CMZ (cite: Oka2016; Tsuboi2017; Takekawa2019; Takekawa2020). These have been hard to confirm, since there exist many alternative explanations for broad-linewidth gas (cite: Ballone2018; Oka2017; Ravi2018; Tanaka2018). We therefore approach this hypothesis cautiously, recognizing that significant evidence is required to claim that a black hole is the only acceptable explanation.

The velocity profile observed has a width that could be produced by an orbit around a central potential. An orbital velocity of 70-80 $\mathrm{km~s}^{-1}$(roughly the half-width of the MUBLO’s line profile) would occur at $10^3-10^4$ au for a few $10^4$ $\mathrm{M}_\odot$ black hole (see Figure [13](#fig:imbhorbit)). However, a disk with a pure Keplerian orbit seen edge-on should not produce a Gaussian profile, but should instead produce a double-peaked profile with peaks corresponding to the disk’s outermost radii. The peak of the SO profile is a key limit on this model, since it appears consistent with a smooth Gaussian (e.g., Figure [2](#fig:coarse_spectra)). In order for the double-peak profile to be obscured, the purported disk would either need to be face-on, which would reduce the observed line width, or the gas would need to be very turbulent. A very high degree of turbulence is plausible, but would likely produce significant shocks, and therefore we would expect to see SiO emission.

Alternatively, a lower mass object would produce this broad linewidth at smaller radii. The apparent low optical depth of the SO and CS lines sets a lower limit on the radius: if we assume the lines are optically thin, the filling factor must be $ff>0.1$ (§[3.1](#sec:spectralmeasurements)), limiting the radius to $r>1400$ au, which implies a lower mass limit $M_{BH}>8000$ $\mathrm{M}_\odot$ following Figure [13](#fig:imbhorbit). This is not a strict limit, however, as the line profile would not necessarily appear non-Gaussian for moderate optical depth; more detailed modeling would be needed to produce a firm lower limit.

Despite the apparent problems with a disk model, we explore it a bit further. We assume a central mass $M=10^4$ $\mathrm{M}_\odot$ such that the orbital velocity reaches $\sim70$ $\mathrm{km~s}^{-1}$ at around $2000$ au. We adopt a simple viscous disk model with $\alpha=0.001$ and total mass 50 $\mathrm{M}_\odot$, which results in surface density $\Sigma=7\times10^{25}\ensuremath{\mathrm{cm}^{-2}}$, and Planck mean opacity $\kappa=3$ cm$^{2}$ g$^{-1}$. The midplane temperature is then (cite: Krumholz2015) $$\begin{equation}
    T_m = \left[\frac{27  \alpha k_B  \Sigma^2 \kappa \Omega}{64 m \sigma_{SB}}\right]^{1/3}
\end{equation}$$ which we parameterize as $$\begin{equation}
\label{eqn4}
T_m = 7.3 \mathrm{~K~}
        \left[\frac{M}{50~\mathrm{M}_\odot}\right]^{2/3}
        \left[\frac{\kappa}{3~\mathrm{~cm^2~g^{-1}}}\right]^{1/3}
        \left[\frac{\alpha}{10^{-3}}\right]^{1/3}
        \left[\frac{r}{2000~\mathrm{au}}\right]^{-4/3}
\end{equation}$$ This temperature is within a plausible range to explain the observed $T_\mathrm{LTE}\approx13$ K, though it may imply either higher $\alpha$, a smaller emitting radius, or perhaps some other heating source is present (e.g., cosmic rays). We also compute the inner radius $r_\mathrm{min}=9$ au by inverting Equation [\[eqn4\]](#eqn4) and assuming $T_\mathrm{max} < 10^4$ K, since there is no detected ionized gas in the cm continuum or in recombination lines. The inner radius at which we would expect to detect molecular lines is roughly the dust destruction radius, $T\approx2000$ K, at $r=30$ au.

![](f26)

Additionally, we checked the stellar kinematics in the vicinity of our target source. (cite: Shahzamanian2022) reported proper motions measured using the GALACTICNUCLEUS data. Within a few arcseconds of this object, there are several measured proper motions, but there is no apparent trend; in particular, there is no increase of PM closer to the source. This lack is not evidence for or against the IMBH hypothesis, though, as most stars in the field-of-view are likely at large physical distance from the MUBLO despite their small projected distance.

While there are several appealing features of the IMBH model, in its simplest form, it does not explain all of the observed features of the MUBLO. We regard it as a possible explanation, but do not favor it above other models.

## Galaxy

Could this object be a background galaxy?

Assuming we have correctly identified the spectral lines in §[3.1](#sec:spectralmeasurements), the line-of-sight velocity of 40 $\mathrm{km~s}^{-1}$ makes a background galaxy hypothesis very unlikely. There are few galaxies at this redshift (i.e., near zero) and these galaxies occupy a low density on the sky. If the MUBLO were a galaxy, we would be observing a very compact component of it, perhaps the center. Assuming a size scale of the center of $r\sim100$ pc, in order to be unresolved at $1\ensuremath{''}$ resolution, it would need to be at $D\gtrsim20$ Mpc. At that distance, the expected redshift is $H_0 D \sim 1400$ $\mathrm{km~s}^{-1}$, such that the required peculiar velocity for this to be a galaxy would be $\sim-1300$ $\mathrm{km~s}^{-1}$, much larger than expected in the local neighborhood.

The observed chemistry also is evidence against this being a galaxy. We compare the MUBLO to the CMZ as a whole: taking the average over the whole observations of the GC from ACES Total Power observations, our CMZ has an average CS 2-1 brightness of 53 K $\mathrm{km~s}^{-1}$ and SO 2(3)-1(2) brightness 10 K $\mathrm{km~s}^{-1}$. Table [\[tab:spectral_measurements\]](#tab:spectral_measurements) shows that the MUBLO has SO 2(3)-1(2)/CS 2-1 of about 1.8, while the CMZ has a ratio of 0.19, about a 10$\times$ difference. This other hypothetical CMZ would have to exhibit a dramatically different chemistry to our own. The HC$_3$N/CS brightness ratio in the MUBLO is $R<0.04$, while the measured value in the CMZ is 0.11 both from our measurements and (cite: Jones2012), which is also a discrepancy, but not quite as difficult to reconcile as the SO/CS ratio.

Given that a correct identification of the lines essentially rules out a background galaxy, could we have misidentified the lines? This possibility is entirely ruled out, as we have identified several lines of SO and its $^{34}$S isotopologue in addition to a CS and C$^{34}$S line. While any one line could be misidentified, a grouping of five different lines redshifting exactly on top of the rest frequencies of lines of another species is exceedingly unlikely.

## Supernova

Could this be the remnant of a star that went supernova, or perhaps even a failed supernova? A supernova would readily explain the lack of an infrared source, since the purported source would have exploded.

There is at least one recent example of a ‘failed supernova’ candidate in which a source remained afterward, but was highly reddened and fainter (cite: Adams2017; Beasor2023; Kochanek2024). As far as we are aware, though, there are no millimeter-wavelength observations of N6946-BH1, so we cannot (yet) make a direct comparison between it and the MUBLO.

The presence of molecules is somewhat compatible with a supernova. SN1987A exhibits molecular emission in CO and SiO with widths $\sim1000$ $\mathrm{km~s}^{-1}$(cite: Cigan2019). If the MUBLO is a supernova remnant (SNR), it is both much narrower in linewidth and chemically distinct from SN1987A. Under the SNR hypothesis, we should probably adopt a much lower gas-to-dust ratio such that the total mass of the MUBLO is $\lesssim1$ $\mathrm{M}_\odot$. As explained in § [4.4](#sec:weirddust), recent work suggests the presence of dust mass reservoirs $\sim{}0.5\,\ensuremath{\mathrm{M}_\odot}$ in some supernova remnants, underlining this point.

There is weak circumstantial evidence from the morphology of the surrounding material that there was an explosive event at the MUBLO’s location. The gap between the 50 $\mathrm{km~s}^{-1}$ cloud and the Three Little Pigs (Figure [9](#fig:bigcontext)) could be produced by a supernova, in principle. The MEERKAT and Chandra images of the area give no hint of a supernova remnant, though, so if this was a supernova-driven cavity, its hot gas has already disappeared. Additionally, the size scale of the apparent gap is several parsecs, while the MUBLO’s molecular emission is only a few thousand au, which is difficult to reconcile.

Supernovae are comprised of fast-moving ejecta, and therefore should expand over time. The line width and the molecular and dust continuum intensity have all stayed roughly constant from 2012 to 2022 (§[3.4](#sec:continuum)). It is not clear how a supernova scenario would explain the steadiness of the observed dispersion over this $\sim10$ year period. It is possible that we are seeing only the inner remnant that has been confined by the reverse shock.

In summary, we cannot rule out a supernova remnant as an explanation for the MUBLO, but such a model does not account for all of its features.

# Conclusion

We found a source exhibiting extremely high velocity dispersion, which we title a Millimeter Ultra-Broad Line Object (MUBLO). We do not have a conclusive classification of this source. Several hypotheses produce many of the observed features, but none explain them all.

The key observational features of the MUBLO are:

- It has large linewidth ($FWHM=160~\ensuremath{\mathrm{km~s}^{-1}}$, $\sigma=70$ $\mathrm{km~s}^{-1}$) in molecular lines (SO and CS).

- It is likely in the Galactic Center, since the broad lines show absorption from Galactic Center clouds.

- It is compact, $\theta_{FWHM,maj}<1\ensuremath{''}$ ($\lesssim8000$ au assuming a distance 8 kpc)

- Its chemistry is unlike that of other known objects: the ratio of SO to CS, and SO and CS to other molecules, is different from other Galactic Center and Galactic disk clouds and from evolved stars and stellar merger remnants. Most significant is the nondetection of SiO, which is a strong indication that there are no shocks in the MUBLO.

- It is dusty, as evidenced by the spectral index of its continuum emission from 3 mm to 850 $\mathrm{\mu m}$, $\alpha=3.25$.

- It is likely massive, with $M_\mathrm{gas}\sim 50 \ensuremath{\mathrm{M}_\odot}$ assuming typical ISM dust and a gas-to-dust ratio of 100, and therefore dense.

- It is cold, $T_\mathrm{gas}\sim15$ K and $T_\mathrm{dust} < 50$ K.

- No counterpart is found at other wavelengths for which comparable resolution data exist, including infrared (1-25 $\mathrm{\mu m}$), radio ($\lambda > 3$ mm), and X-ray (2-10 keV).

Given these observational features, we considered many physical explanations of the MUBLO. Among the most promising for followup are the stellar merger and intermediate mass black hole hypotheses. There are no exact analogs to the MUBLO among known astronomical objects. Future mid-infrared and millimeter observations will be needed to determine what this object is.

**Acknowledgements:** We thank the anonymous referee for a helpful and constructive review. We thank Brett McGuire, Andres Izquierdo, Joel Kastner, and Elias Aydi for conversations about chemistry, disks, evolved stars, and novae that motivated some of the discussion sections. AG acknowledges support from the NSF under grants AAG 2008101, 2206511, and CAREER 2142300. The authors acknowledge University of Florida Research Computing for providing computational resources and support that have contributed to the research results reported in this publication. KMD and SV are funded by the European Research Council (ERC) Advanced Grant MOPPEX 833460.vii. XL acknowledges support from the National Key R&D Program of China (No. 2022YFA1603101), the Natural Science Foundation of Shanghai (No. 23ZR1482100), the National Natural Science Foundation of China (NSFC) through grant Nos. 12273090 & 12322305, and the Chinese Academy of Sciences (CAS) ‘Light of West China’ Program (No. xbzgzdsys-202212). LC, IJS, and VMR acknowledge funding from grants No. PID2019-105552RB-C41 and PID2022-136814NB-I00 by the Spanish Ministry of Science, Innovation and Universities/State Agency of Research MICIU/AEI/10.13039/501100011033 and by ERDF, UE. V.M.R. also acknowledges support from the grant number RYC2020-029387-I funded by MICIU/AEI/10.13039/501100011033 and by "ESF, Investing in your future", and from the Consejo Superior de Investigaciones Científicas (CSIC) and the Centro de Astrobiología (CAB) through the project 20225AT015 (Proyectos intramurales especiales del CSIC). RSK acknowledges financial support from the European Research Council via the ERC Synergy Grant “ECOGAL” (project ID 855130), from the German Excellence Strategy via the Heidelberg Cluster of Excellence (EXC 2181 - 390900948) “STRUCTURES”, and from the German Ministry for Economic Affairs and Climate Action in project “MAINN” (funding ID 50OO2206). A.S.-M. acknowledges support from the RyC2021-032892-I grant funded by MCIN/AEI/10.13039/501100011033 and by the European Union ‘Next GenerationEU’/PRTR, as well as the program Unidad de Excelencia María de Maeztu CEX2020-001058-M, and support from the PID2020-117710GB-I00 (MCI-AEI-FEDER, UE). C. Battersby gratefully acknowledges funding from National Science Foundation under Award Nos. 1816715, 2108938, 2206510, and CAREER 2145689, as well as from the National Aeronautics and Space Administration through the Astrophysics Data Analysis Program under Award No. 21-ADAP21-0179 and through the SOFIA archival research program under Award No. 09$\_$0540. Q. Zhang acknowledges the support of National Science Foundation under award No. 2206509.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00172.L, ADS/JAO.ALMA#2012.1.00080.S, ADS/JAO.ALMA#2017.1.01185.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Total Power Spectra

Figure [14](#fig:coarse_spectra_withTP) shows the ACES 12m spectra with spectra from the total power (TP; 12m single-dish) array overlaid. The TP peaks coincide with the dips in the 12m spectra, indicating that the dips are caused either by absorption lines from foreground clouds or from interferometric imaging artifacts from resolved-out clouds. It is not possible to tell from the images whether the absorption is real or not, despite the clear absorption-line profile seen in Figure [1](#fig:fittedspectra).

![image](f27) ![image](f28)

# Chemical Modeling

To guide our interpretation of the chemistry of the MUBLO, we use two types of astrochemical modeling codes: Meudon PDR (cite: LePetit2006) and UCLCHEM (cite: Holdship2017). The former is a photochemical model of a one-dimensional stationary PDR and the latter is a zero-dimensional model that tracks the time evolution of the chemistry of a cloud.

The Meudon PDR code computes abundances of atoms and molecules and level excitation of any number of species at each position in the cloud (a stationary plane-parallel slab of gas and dust illuminated by radiation field). The code solves the FUV radiative transfer at each point of the cloud, taking into account absorption in the continuum by dust and in discrete transitions by H and H$_2$. This model computes the thermal balance taking into account heating processes (cosmic rays, photoelectric effect on grains, H$_2$ formation on grains, chemistry, grain-gas coupling, turbulence, photons: photodissociation and photoionization, and secondary photons) and cooling from discrete radiative transitions in IR and mm lines of various species following collisional excitation, free-free emission and H$_2$ dissociation. A post-processor code computes the line intensities and column densities.

The UCLCHEM code is a zero-dimensional model that follows the time evolution of the chemistry of a cloud. We use it to predict chemical abundances rather than intensities.

## FUV and CR irradiation models

We use the Meudon PDR code to model the MUBLO as a constant density cloud illuminated by the FUV radiation field ($G_0$). We adopt enhanced (compared to that in Galactic disk GMCs) H$_2$ cosmic-ray ionization rates (cite: Indriolo2015). Table [\[tab:MeudonPDR\]](#tab:MeudonPDR) shows the input parameters. We accounted for sulfur depletion usually needed in starless cores (a factor $>$100) and that estimated in hot cores or bipolar outflows (cite: Fuente2023).

Figure [15](#fig:SO-CS_Meudon) shows the model predictions of the SO to CS column density ratio, $N$(SO)/$N$(CS), and the $I$(SO 3$_2$–2$_1$)/$I$(CS 2$-$1) intensity ratio as function of the cosmic ray ionization rate ($\zeta_\mathrm{CR}$). The blue shaded area represents the estimated and observed ratios, respectively (see Sect. [4.1](#sec:LTE) and Table [\[tab:spectral_measurements\]](#tab:spectral_measurements)). The estimated region comes from LTE modeling (§[4.1](#sec:LTE)), while the Meudon model performs non-LTE modeling of the line ratio, which is why the blue shaded regions are different for these two panels - i.e., the Meudon model suggests that the line ratio is not in LTE. These models show that a high density ($n_\mathrm{H}\gtrsim10^7$ $\mathrm{cm}^{-3}$) is required to match the observations: when $n_\mathrm{H}$=2$\times$10$^5$ $\mathrm{cm}^{-3}$, $N$(SO)/$N$(CS) is larger than 20 for all $\zeta_\mathrm{CR}$. Hence, the computed intensity and column density ratios never overlap with the estimated ratio from Sect. [4.1](#sec:LTE).

Figure [16](#fig:AV_SO-CS_Meudon) shows the abundance and gas temperature profiles of a model with $n_\mathrm{H}$=2$\times$10$^{7}$ $\mathrm{cm}^{-3}$, $\zeta_\mathrm{CR}$=3$\times$10$^{-15}$ s$^{-1}$ per H$_2$ molecule, and sulfur abundance depleted a factor 10. The gas temperature at large $A_\mathrm{V}$ is $T_\mathrm{k}$$\sim$10-15 K, which agrees with the measured $T_{LTE}=T_{ex}(\mathrm{SO})$.

In Sect. [3.1](#sec:spectralmeasurements) we show that this source has $I$(SO 3$_2$–2$_1$)/$I$(CS 2$-$1) ratio of about 1.8, while it has $N$(SO)/$N$(CS) of about 4, though the estimated $N$(CS) value is dominated by systematic uncertainty in $T_\mathrm{ex}$. The model predictions result in a narrow range of parameters consistent with the observed SO/CS intensity ratio and estimated SO/CS column density ratio, $n_\mathrm{H}$$\sim$2$\times$10$^7$ $\mathrm{cm}^{-3}$ and 10$^{-16}$$\lesssim$$\zeta_{CR}$$\lesssim$5$\times$10$^{-15}$ s$^{-1}$.

| Parameter | Unit | Value | Note |
|:---|:---|:--:|:--:|
| $n_\mathrm{H}$ | cm$^{-3}$ | 2$\times$10$^5$, 2$\times$10$^7$ | $n_\mathrm{H}$=$n$(H)+2$n$(H$_2$), (1) |
| $A_\mathrm{V,max}$ | mag | 20, 200, 800 | (2), $L$$\sim$125, 1250, 5000 au |
| FUV radiation field, $G_0$ | – | 10$^3$ | \(3\) |
| Cosmic ray ionization rate, $\zeta_\mathrm{CR}$ | s$^{-1}$ per H$_2$ | \[2$\times$10$^{-17}$, 2$\times$10$^{-14}$\] | (4), (5) |
| Dust extinction curve |  | Galaxy | \(6\) |
| $R_\mathrm{V}$ |  | 3.1 | \(6\) |
| $N_\mathrm{H}$/$E$(B-V) = $C_\mathrm{D}$ | cm$^{-2}$ | 5.8$\times$10$^{21}$ | \(7\) |
| $\left [\mathrm{S}  \right ]$ | – | $\left [\mathrm{S}  \right ]_0  \times$ (1, 0.1, 0.01) | $\left [\mathrm{S}  \right ]_0$=1.4$\times$10$^{-5}$ (8), (9), (10) |
|  |  |  |  |

\(1\) See Sect.[4.2](#sec:nonlte); (2) The relation between $A_\mathrm{V, max}$ and the size of the computed cloud, $L$, in cm is $L=N_\mathrm{H}/n\mathrm{_H}=(C_\mathrm{D}/n_\mathrm{H})\,(A_\mathrm{V}/R_\mathrm{V})$; (3) Scaling parameter to the ISRF, (cite: Mathis1983); (4) (cite: Indriolo2015); (5) (cite: LePetit2016); (6) (cite: Fitzpatrick2007); (7) (cite: Bohlin1978); (8) (cite: Asplund2009); (9) (cite: Goicoechea2021); (10) (cite: Fuente2023).

![image]({f29}.pdf) ![image]({f30}.pdf) ![image]({f31}.pdf)

![](f32)

## UCLCHEM models

We describe the UCLCHEM models run in this section. Table [\[tab:UCLCHEM\]](#tab:UCLCHEM) shows the parameter grid we ran. We accounted for the observed depletion of silicon (cite: Savage1996) and sulfur (cite: Palumbo1997) abundances by evaluating both a model with solar initial abundances and a model with a depletion of a factor 10 for S and 100 for Si. For models with gas and dust temperatures set to 15 K (see Fig. [17](#fig:UCLCHEM-15)), we find that the observed ratio SO/SiO $\gtrsim100$ is predicted for densities $\leq10^6\,\mathrm{cm}^{-3}$, while for the 50 K models (see Fig. [18](#fig:UCLCHEM-50)), the ratio can be recovered for all considered densities. SO/SiO$>100$ is reachable for all considered cosmic ray ionization rates and UV field strengths regardless of the gas and dust temperatures, however, in the case of the lowest density scenario ($n=10^5$ $\mathrm{cm}^{-3}$) for the 50 K models, the ratio only is recovered after more than $10^7$ years. For the medium density scenario, the ratio is quickly achieved and persists over a long chemical timescale. For the highest density scenario, the ratio increases rapidly during the collapse, but once the final density is reached both SiO and SO quickly freeze out.

Moreover, (cite: DutkowskaVermarien2024) explored a wide range of continuous shock model parameters, covering shock velocity $5-30\,\mathrm{km\,s}^{-1}$, pre-shock medium temperature $15-35$ K, pre-shock density $10^4-10^6\,\mathrm{cm}^{-3}$, magnetic field $10^{1}-10^{3}\,\mu\mathrm{G}$, cosmic ray ionization rate $1.31\times10^{-16}-1.31\times10^{-13}\,\mathrm{s}^{-1}$, and UV irradiation $10^0-10^4$ Habing. In these models, SO/SiO ratios are low, $<100$, during and shortly after the shock. The high SO/SiO ratio in the MUBLO is therefore either inherited from the collapse/quiescent cloud stage, or it is achieved long after the shock has passed. Shocks with a velocity of $\leq 5\,\mathrm{km\,s}^{-1}$ are the only ones capable of maintaining a ratio above 100. For a higher shock velocity, the SO/SiO ratio stays below 100, though given enough time after the shock, the SO/SiO ratio can eventually exceed 100 again.

Lastly, models at higher temperatures of $100$K and $150$K were simulated, since these higher temperatures are observed in the CMZ (cite: ginsburgDenseGasGalactic2016; millsDetectionWidespreadHot2013; zengComplexOrganicMolecules2018a). For these models an identical grid of models was run. These models reproduce the SO/SiO ratio only for high cosmic ray ionization rates, under which conditions the SiO is quickly destroyed and the SO reaches a steady state.

From these time dependent gas-grain simulations, we conclude that a shock-free medium is favored to reproduce the high SO/SiO ratios. The ratios can be reproduced sufficiently by dense and possibly quiescent environments.

| Parameter | Unit | Values | Notes |
|:---|:---|:---|:---|
| $n_\mathrm{H,\,final}$ | cm$^{-3}$ | $10^5, 10^6, 10^7$ | $n_\mathrm{H} = n(\mathrm{H}) + 2n(\mathrm{H}_2)$; $n_\mathrm{H,\, init} = 10^2\,\mathrm{cm}^{-3}$ |
| $T_\mathrm{gas,\,dust}$ | K | $15, 50$ | ... |
| $\zeta / \zeta_0$ | $-$ | $10^1, 10^2, 10^3$ | $\zeta_0 = 1.310\times10^{-17}\,\mathrm{s}^{-1}$ |
| $F_\mathrm{UV}$ | Habing | $10^0, 10^2, 10^3$ | ... |
| $X(\mathrm{Si})$ | $-$ | $1.78^{-8}, 1.78^{{-6}\dag}$ | $^\dag X(\mathrm{Si})_\odot$ (cite: Jenkins2009) |
| $X(\mathrm{S})$ | $-$ | $3.51^{-7}, 3.51^{{-6}\dag}$ | $^\dag X(\mathrm{S})_\odot$ (cite: Jenkins2009) |

![](f33)

![](f34)

# RADEX models

We show parameter slices from the grid of RADEX models described in §[4.2](#sec:nonlte). The models use the large velocity gradient (LVG) approximation with $dv=70$ $\mathrm{km~s}^{-1}$. Figure [19](#fig:radexgrids) shows these model grids.

![image]({f35}.pdf) ![image]({f36}.pdf) ![image]({f37}.pdf) ![image]({f38}.pdf)

natexlab

(ref: Adams2017) Adams, S. M., Kochanek, C. S., Gerke, J. R., Stanek, K. Z., & Dai, X. 2017, MNRAS, 468, 4968, doi: [`10.1093/mnras/stx816`](http://doi.org/10.1093/mnras/stx816)

(ref: Asplund2009) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481, doi: [`10.1146/annurev.astro.46.060407.145222`](http://doi.org/10.1146/annurev.astro.46.060407.145222)

(ref: Ballone2018) Ballone, A., Mapelli, M., & Pasquato, M. 2018, MNRAS, 480, 4684, doi: [`10.1093/mnras/sty2139`](http://doi.org/10.1093/mnras/sty2139)

(ref: Bally2017) Bally, J., Ginsburg, A., Arce, H., et al. 2017, ApJ, 837, 60, doi: [`10.3847/1538-4357/aa5c8b`](http://doi.org/10.3847/1538-4357/aa5c8b)

(ref: Bally2015) Bally, J., Ginsburg, A., Silvia, D., & Youngblood, A. 2015, A&A, 579, A130, doi: [`10.1051/0004-6361/201425073`](http://doi.org/10.1051/0004-6361/201425073)

(ref: Banerjee2020) Banerjee, D. P. K., Geballe, T. R., Evans, A., et al. 2020, ApJL, 904, L23, doi: [`10.3847/2041-8213/abc885`](http://doi.org/10.3847/2041-8213/abc885)

(ref: Barnes2017) Barnes, A. T., Longmore, S. N., Battersby, C., et al. 2017, MNRAS, 469, 2263, doi: [`10.1093/mnras/stx941`](http://doi.org/10.1093/mnras/stx941)

(ref: Battersby2020) Battersby, C., Keto, E., Walker, D., et al. 2020, ApJS, 249, 35, doi: [`10.3847/1538-4365/aba18e`](http://doi.org/10.3847/1538-4365/aba18e)

(ref: Beasor2023) Beasor, E. R., Hosseinzadeh, G., Smith, N., et al. 2023, arXiv e-prints, arXiv:2309.16121, doi: [`10.48550/arXiv.2309.16121`](http://doi.org/10.48550/arXiv.2309.16121)

(ref: Bianchi2007) Bianchi, S., & Schneider, R. 2007, MNRAS, 378, 973, doi: [`10.1111/j.1365-2966.2007.11829.x`](http://doi.org/10.1111/j.1365-2966.2007.11829.x)

(ref: Bohlin1978) Bohlin, R. C., Savage, B. D., & Drake, J. F. 1978, ApJ, 224, 132, doi: [`10.1086/156357`](http://doi.org/10.1086/156357)

(ref: Bonfand2017) Bonfand, M., Belloche, A., Menten, K. M., Garrod, R. T., & Müller, H. S. P. 2017, A&A, 604, A60, doi: [`10.1051/0004-6361/201730648`](http://doi.org/10.1051/0004-6361/201730648)

(ref: Bonfand2024) Bonfand, M., Csengeri, T., Bontemps, S., et al. 2024, arXiv e-prints, arXiv:2402.15023, doi: [`10.48550/arXiv.2402.15023`](http://doi.org/10.48550/arXiv.2402.15023)

(ref: Bordiu2022) Bordiu, C., Rizzo, J. R., Bufano, F., et al. 2022, ApJL, 939, L30, doi: [`10.3847/2041-8213/ac9b10`](http://doi.org/10.3847/2041-8213/ac9b10)

(ref: Budaiev2024) Budaiev, N., Ginsburg, A., Jeff, D., et al. 2024, ApJ, 961, 4, doi: [`10.3847/1538-4357/ad0383`](http://doi.org/10.3847/1538-4357/ad0383)

(ref: Carey2009) Carey, S. J., Noriega-Crespo, A., Mizuno, D. R., et al. 2009, PASP, 121, 76, doi: [`10.1086/596581`](http://doi.org/10.1086/596581)

(ref: Chawner2019) Chawner, H., Marsh, K., Matsuura, M., et al. 2019, MNRAS, 483, 70, doi: [`10.1093/mnras/sty2942`](http://doi.org/10.1093/mnras/sty2942)

(ref: Churchwell2009) Churchwell, E., Babler, B. L., Meade, M. R., et al. 2009, PASP, 121, 213, doi: [`10.1086/597811`](http://doi.org/10.1086/597811)

(ref: Cigan2019) Cigan, P., Matsuura, M., Gomez, H. L., et al. 2019, ApJ, 886, 51, doi: [`10.3847/1538-4357/ab4b46`](http://doi.org/10.3847/1538-4357/ab4b46)

(ref: Ciurlo2020) Ciurlo, A., Campbell, R. D., Morris, M. R., et al. 2020, Nature, 577, 337, doi: [`10.1038/s41586-019-1883-y`](http://doi.org/10.1038/s41586-019-1883-y)

(ref: Dame2008) Dame, T. M., & Thaddeus, P. 2008, ApJL, 683, L143, doi: [`10.1086/591669`](http://doi.org/10.1086/591669)

(ref: Dong2011) Dong, H., Wang, Q. D., Cotera, A., et al. 2011, MNRAS, 417, 114, doi: [`10.1111/j.1365-2966.2011.19013.x`](http://doi.org/10.1111/j.1365-2966.2011.19013.x)

(ref: Draine2006) Draine, B. T. 2006, ApJ, 636, 1114, doi: [`10.1086/498130`](http://doi.org/10.1086/498130)

(ref: Draine1984) Draine, B. T., & Lee, H. M. 1984, ApJ, 285, 89, doi: [`10.1086/162480`](http://doi.org/10.1086/162480)

(ref: DutkowskaVermarien2024) Dutkowska, K. M., Vermariën, G., Viti, S., & ACES collaboration. in prep., in prep.

(ref: Fitzpatrick2007) Fitzpatrick, E. L., & Massa, D. 2007, ApJ, 663, 320, doi: [`10.1086/518158`](http://doi.org/10.1086/518158)

(ref: Fuente2023) Fuente, A., Rivière-Marichalar, P., Beitia-Antero, L., et al. 2023, A&A, 670, A114, doi: [`10.1051/0004-6361/202244843`](http://doi.org/10.1051/0004-6361/202244843)

(ref: ginsburgDenseGasGalactic2016) Ginsburg, A., Henkel, C., Ao, Y., et al. 2016, A&A, 586, A50, doi: [`10.1051/0004-6361/201526100`](http://doi.org/10.1051/0004-6361/201526100)

(ref: Ginsburg2020) Ginsburg, A., Anderson, L. D., Dicker, S., et al. 2020, ApJS, 248, 24, doi: [`10.3847/1538-4365/ab8b5c`](http://doi.org/10.3847/1538-4365/ab8b5c)

(ref: Goicoechea2021) Goicoechea, J. R., & Cuadrado, S. 2021, A&A, 647, L7, doi: [`10.1051/0004-6361/202140517`](http://doi.org/10.1051/0004-6361/202140517)

(ref: Gramze2023) Gramze, S. R., Ginsburg, A., Meier, D. S., et al. 2023, ApJ, 959, 93, doi: [`10.3847/1538-4357/ad01be`](http://doi.org/10.3847/1538-4357/ad01be)

(ref: Guerrero2020) Guerrero, M. A., Suzett Rechy-Garcı́a, J., & Ortiz, R. 2020, ApJ, 890, 50, doi: [`10.3847/1538-4357/ab61fa`](http://doi.org/10.3847/1538-4357/ab61fa)

(ref: 1988iras....7.....H) Helou, G., & Walker, D. W., eds. 1988, Infrared Astronomical Satellite (IRAS) Catalogs and Atlases.Volume 7: The Small Scale Structure Catalog., Vol. 7

(ref: Henshaw2023) Henshaw, J. D., Barnes, A. T., Battersby, C., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 83, doi: [`10.48550/arXiv.2203.11223`](http://doi.org/10.48550/arXiv.2203.11223)

(ref: Heywood2022) Heywood, I., Rammala, I., Camilo, F., et al. 2022, ApJ, 925, 165, doi: [`10.3847/1538-4357/ac449a`](http://doi.org/10.3847/1538-4357/ac449a)

(ref: Holdship2017) Holdship, J., Viti, S., Jiménez-Serra, I., Makrymallis, A., & Priestley, F. 2017, AJ, 154, 38, doi: [`10.3847/1538-3881/aa773f`](http://doi.org/10.3847/1538-3881/aa773f)

(ref: Hopkins2014) Hopkins, P. F. 2014, ApJ, 797, 59, doi: [`10.1088/0004-637X/797/1/59`](http://doi.org/10.1088/0004-637X/797/1/59)

(ref: Humire2020) Humire, P. K., Thiel, V., Henkel, C., et al. 2020, A&A, 642, A222, doi: [`10.1051/0004-6361/202038216`](http://doi.org/10.1051/0004-6361/202038216)

(ref: Humphreys2024) Humphreys, R. M., Richards, A. M. S., Davidson, K., et al. 2024, AJ, 167, 94, doi: [`10.3847/1538-3881/ad1dd7`](http://doi.org/10.3847/1538-3881/ad1dd7)

(ref: Indriolo2015) Indriolo, N., Neufeld, D. A., Gerin, M., et al. 2015, ApJ, 800, 40, doi: [`10.1088/0004-637X/800/1/40`](http://doi.org/10.1088/0004-637X/800/1/40)

(ref: Iwata2023) Iwata, Y., Oka, T., Takekawa, S., Tsujimoto, S., & Enokiya, R. 2023, ApJ, 950, 25, doi: [`10.3847/1538-4357/acc9b0`](http://doi.org/10.3847/1538-4357/acc9b0)

(ref: Jeff2024) Jeff, D., Ginsburg, A., Bulatek, A., et al. 2024, arXiv e-prints, arXiv:2401.09749, doi: [`10.48550/arXiv.2401.09749`](http://doi.org/10.48550/arXiv.2401.09749)

(ref: Jenkins2009) Jenkins, E. B. 2009, ApJ, 700, 1299, doi: [`10.1088/0004-637X/700/2/1299`](http://doi.org/10.1088/0004-637X/700/2/1299)

(ref: Jones2012) Jones, P. A., Burton, M. G., Cunningham, M. R., et al. 2012, MNRAS, 419, 2961, doi: [`10.1111/j.1365-2966.2011.19941.x`](http://doi.org/10.1111/j.1365-2966.2011.19941.x)

(ref: Kaminski2019) Kamiński, T. 2019, A&A, 627, A114, doi: [`10.1051/0004-6361/201935408`](http://doi.org/10.1051/0004-6361/201935408)

(ref: Kaminski2013) Kamiński, T., Gottlieb, C. A., Young, K. H., Menten, K. M., & Patel, N. A. 2013, ApJS, 209, 38, doi: [`10.1088/0067-0049/209/2/38`](http://doi.org/10.1088/0067-0049/209/2/38)

(ref: Kaminski2015) Kamiński, T., Menten, K. M., Tylenda, R., et al. 2015, Nature, 520, 322, doi: [`10.1038/nature14257`](http://doi.org/10.1038/nature14257)

(ref: Kaminski2017) —. 2017, A&A, 607, A78, doi: [`10.1051/0004-6361/201731287`](http://doi.org/10.1051/0004-6361/201731287)

(ref: Kaminski2020) —. 2020a, A&A, 644, A59, doi: [`10.1051/0004-6361/202038648`](http://doi.org/10.1051/0004-6361/202038648)

(ref: Kaminski2020_CKI) —. 2020b, A&A, 644, A59, doi: [`10.1051/0004-6361/202038648`](http://doi.org/10.1051/0004-6361/202038648)

(ref: Kaminski2021_CKII) Kamiński, T., Steffen, W., Bujarrabal, V., et al. 2021a, A&A, 646, A1, doi: [`10.1051/0004-6361/202039634`](http://doi.org/10.1051/0004-6361/202039634)

(ref: Kaminski2018) Kamiński, T., Steffen, W., Tylenda, R., et al. 2018, A&A, 617, A129, doi: [`10.1051/0004-6361/201833165`](http://doi.org/10.1051/0004-6361/201833165)

(ref: Kaminski2021) Kamiński, T., Tylenda, R., Kiljan, A., et al. 2021b, A&A, 655, A32, doi: [`10.1051/0004-6361/202141526`](http://doi.org/10.1051/0004-6361/202141526)

(ref: Kemper2003) Kemper, F., Stark, R., Justtanont, K., et al. 2003, A&A, 407, 609, doi: [`10.1051/0004-6361:20030701`](http://doi.org/10.1051/0004-6361:20030701)

(ref: Kochanek2024) Kochanek, C. S., Neustadt, J. M. M., & Stanek, K. Z. 2024, ApJ, 962, 145, doi: [`10.3847/1538-4357/ad18d7`](http://doi.org/10.3847/1538-4357/ad18d7)

(ref: Krumholz2015) Krumholz, M. R. 2015, arXiv e-prints, arXiv:1511.03457, doi: [`10.48550/arXiv.1511.03457`](http://doi.org/10.48550/arXiv.1511.03457)

(ref: LePetit2006) Le Petit, F., Nehmé, C., Le Bourlot, J., & Roueff, E. 2006, ApJS, 164, 506, doi: [`10.1086/503252`](http://doi.org/10.1086/503252)

(ref: LePetit2016) Le Petit, F., Ruaud, M., Bron, E., et al. 2016, A&A, 585, A105, doi: [`10.1051/0004-6361/201526658`](http://doi.org/10.1051/0004-6361/201526658)

(ref: Lee2013b) Lee, C.-F., Sahai, R., Sánchez Contreras, C., Huang, P.-S., & Hao Tay, J. J. 2013a, ApJ, 777, 37, doi: [`10.1088/0004-637X/777/1/37`](http://doi.org/10.1088/0004-637X/777/1/37)

(ref: Lee2013a) Lee, C.-F., Yang, C.-H., Sahai, R., & Sánchez Contreras, C. 2013b, ApJ, 770, 153, doi: [`10.1088/0004-637X/770/2/153`](http://doi.org/10.1088/0004-637X/770/2/153)

(ref: Levesque2020) Levesque, E. M., & Massey, P. 2020, ApJL, 891, L37, doi: [`10.3847/2041-8213/ab7935`](http://doi.org/10.3847/2041-8213/ab7935)

(ref: Longmore2013) Longmore, S. N., Bally, J., Testi, L., et al. 2013, MNRAS, 429, 987, doi: [`10.1093/mnras/sts376`](http://doi.org/10.1093/mnras/sts376)

(ref: Lu2019) Lu, X., Mills, E. A. C., Ginsburg, A., et al. 2019, ApJS, 244, 35, doi: [`10.3847/1538-4365/ab4258`](http://doi.org/10.3847/1538-4365/ab4258)

(ref: Mathis1983) Mathis, J. S., Mezger, P. G., & Panagia, N. 1983, A&A, 128, 212

(ref: Matsuura2014) Matsuura, M., Yates, J. A., Barlow, M. J., et al. 2014, MNRAS, 437, 532, doi: [`10.1093/mnras/stt1906`](http://doi.org/10.1093/mnras/stt1906)

(ref: millsDetectionWidespreadHot2013) Mills, E. A. C., & Morris, M. R. 2013, ApJ, 772, 105, doi: [`10.1088/0004-637X/772/2/105`](http://doi.org/10.1088/0004-637X/772/2/105)

(ref: Molinari2010) Molinari, S., Swinyard, B., Bally, J., et al. 2010, A&A, 518, L100, doi: [`10.1051/0004-6361/201014659`](http://doi.org/10.1051/0004-6361/201014659)

(ref: Monnier1999) Monnier, J. D., Tuthill, P. G., Lopez, B., et al. 1999, ApJ, 512, 351, doi: [`10.1086/306761`](http://doi.org/10.1086/306761)

(ref: Montarges2021) Montargès, M., Cannon, E., Lagadec, E., et al. 2021, Nature, 594, 365, doi: [`10.1038/s41586-021-03546-8`](http://doi.org/10.1038/s41586-021-03546-8)

(ref: Morris1996) Morris, M., & Serabyn, E. 1996, ARA&A, 34, 645, doi: [`10.1146/annurev.astro.34.1.645`](http://doi.org/10.1146/annurev.astro.34.1.645)

(ref: Morris2020) Morris, P. W., Charnley, S. B., Corcoran, M., et al. 2020, ApJL, 892, L23, doi: [`10.3847/2041-8213/ab784a`](http://doi.org/10.3847/2041-8213/ab784a)

(ref: Muno2009) Muno, M. P., Bauer, F. E., Baganoff, F. K., et al. 2009, ApJS, 181, 110, doi: [`10.1088/0067-0049/181/1/110`](http://doi.org/10.1088/0067-0049/181/1/110)

(ref: Nogueras-Lara2018) Nogueras-Lara, F., Gallego-Calvente, A. T., Dong, H., et al. 2018, A&A, 610, A83, doi: [`10.1051/0004-6361/201732002`](http://doi.org/10.1051/0004-6361/201732002)

(ref: Nogueras-Lara2019) Nogueras-Lara, F., Schödel, R., Gallego-Calvente, A. T., et al. 2019, A&A, 631, A20, doi: [`10.1051/0004-6361/201936263`](http://doi.org/10.1051/0004-6361/201936263)

(ref: Nogueras-Lara2020) —. 2020, Nature Astronomy, 4, 377, doi: [`10.1038/s41550-019-0967-9`](http://doi.org/10.1038/s41550-019-0967-9)

(ref: Ochsenbein2000) Ochsenbein, F., Bauer, P., & Marcout, J. 2000, A&AS, 143, 23, doi: [`10.1051/aas:2000169`](http://doi.org/10.1051/aas:2000169)

(ref: O’Gorman2015) O’Gorman, E., Vlemmings, W., Richards, A. M. S., et al. 2015, A&A, 573, L1, doi: [`10.1051/0004-6361/201425101`](http://doi.org/10.1051/0004-6361/201425101)

(ref: Oka2016) Oka, T., Mizuno, R., Miura, K., & Takekawa, S. 2016, ApJL, 816, L7, doi: [`10.3847/2041-8205/816/1/L7`](http://doi.org/10.3847/2041-8205/816/1/L7)

(ref: Oka2014) Oka, T., Tanaka, K., Matsumura, S., et al. 2014, in The Galactic Center: Feeding and Feedback in a Normal Galactic Nucleus, ed. L. O. Sjouwerman, C. C. Lang, & J. Ott, Vol. 303, 202–204, doi: [`10.1017/S1743921314000568`](http://doi.org/10.1017/S1743921314000568)

(ref: Oka2017) Oka, T., Tsujimoto, S., Iwata, Y., Nomura, M., & Takekawa, S. 2017, Nature Astronomy, 1, 709, doi: [`10.1038/s41550-017-0224-z`](http://doi.org/10.1038/s41550-017-0224-z)

(ref: Oka2022) Oka, T., Uruno, A., Enokiya, R., et al. 2022, ApJS, 261, 13, doi: [`10.3847/1538-4365/ac6bfc`](http://doi.org/10.3847/1538-4365/ac6bfc)

(ref: Omont1993) Omont, A., Lucas, R., Morris, M., & Guilloteau, S. 1993, A&A, 267, 490

(ref: Ossenkopf1994) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: Palumbo1997) Palumbo, M. E., Geballe, T. R., & Tielens, A. G. G. M. 1997, ApJ, 479, 839, doi: [`10.1086/303905`](http://doi.org/10.1086/303905)

(ref: Quintana-Lacaci2023) Quintana-Lacaci, G., Velilla-Prieto, L., Agúndez, M., et al. 2023, A&A, 669, A56, doi: [`10.1051/0004-6361/202244396`](http://doi.org/10.1051/0004-6361/202244396)

(ref: Ramirez2008) Ramı́rez, S. V., Arendt, R. G., Sellgren, K., et al. 2008, ApJS, 175, 147, doi: [`10.1086/524015`](http://doi.org/10.1086/524015)

(ref: Ravi2018) Ravi, V., Vedantham, H., & Phinney, E. S. 2018, MNRAS, 478, L72, doi: [`10.1093/mnrasl/sly077`](http://doi.org/10.1093/mnrasl/sly077)

(ref: Retter2006) Retter, A., Zhang, B., Siess, L., & Levinson, A. 2006, MNRAS, 370, 1573, doi: [`10.1111/j.1365-2966.2006.10585.x`](http://doi.org/10.1111/j.1365-2966.2006.10585.x)

(ref: Richardson2024) Richardson, T., Ginsburg, A., Indebetouw, R., & Robitaille, T. P. 2024, ApJ, 961, 188, doi: [`10.3847/1538-4357/ad072d`](http://doi.org/10.3847/1538-4357/ad072d)

(ref: Robitaille2017) Robitaille, T. P. 2017, A&A, 600, A11, doi: [`10.1051/0004-6361/201425486`](http://doi.org/10.1051/0004-6361/201425486)

(ref: Sahai2015) Sahai, R., & Patel, N. A. 2015, ApJL, 810, L8, doi: [`10.1088/2041-8205/810/1/L8`](http://doi.org/10.1088/2041-8205/810/1/L8)

(ref: Sahai2017) Sahai, R., Vlemmings, W. H. T., & Nyman, L. Å. 2017, ApJ, 841, 110, doi: [`10.3847/1538-4357/aa6d86`](http://doi.org/10.3847/1538-4357/aa6d86)

(ref: Savage1996) Savage, B. D., & Sembach, K. R. 1996, ARA&A, 34, 279, doi: [`10.1146/annurev.astro.34.1.279`](http://doi.org/10.1146/annurev.astro.34.1.279)

(ref: Schultheis2020) Schultheis, M., Rojas-Arriagada, A., Cunha, K., et al. 2020, A&A, 642, A81, doi: [`10.1051/0004-6361/202038327`](http://doi.org/10.1051/0004-6361/202038327)

(ref: Shahzamanian2022) Shahzamanian, B., Schoedel, R., Nogueras-Lara, F., et al. 2022, VizieR Online Data Catalog, J/A+A/662/A11, doi: [`10.26093/cds/vizier.36620011`](http://doi.org/10.26093/cds/vizier.36620011)

(ref: Sormani2019) Sormani, M. C., & Barnes, A. T. 2019, MNRAS, 484, 1213, doi: [`10.1093/mnras/stz046`](http://doi.org/10.1093/mnras/stz046)

(ref: Takekawa2019) Takekawa, S., Oka, T., Iwata, Y., Tsujimoto, S., & Nomura, M. 2019, ApJL, 871, L1, doi: [`10.3847/2041-8213/aafb07`](http://doi.org/10.3847/2041-8213/aafb07)

(ref: Takekawa2020) —. 2020, ApJ, 890, 167, doi: [`10.3847/1538-4357/ab6f6f`](http://doi.org/10.3847/1538-4357/ab6f6f)

(ref: Tanaka2018) Tanaka, K. 2018, ApJ, 859, 86, doi: [`10.3847/1538-4357/aabd77`](http://doi.org/10.3847/1538-4357/aabd77)

(ref: Tokuyama2019) Tokuyama, S., Oka, T., Takekawa, S., et al. 2019, PASJ, 71, S19, doi: [`10.1093/pasj/psy150`](http://doi.org/10.1093/pasj/psy150)

(ref: Traficante2011) Traficante, A., Calzoletti, L., Veneziani, M., et al. 2011, MNRAS, 416, 2932, doi: [`10.1111/j.1365-2966.2011.19244.x`](http://doi.org/10.1111/j.1365-2966.2011.19244.x)

(ref: Tsuboi2017) Tsuboi, M., Kitamura, Y., Tsutsumi, T., et al. 2017, ApJL, 850, L5, doi: [`10.3847/2041-8213/aa97d3`](http://doi.org/10.3847/2041-8213/aa97d3)

(ref: Tsuboi2009) Tsuboi, M., Miyazaki, A., & Okumura, S. K. 2009, PASJ, 61, 29, doi: [`10.1093/pasj/61.1.29`](http://doi.org/10.1093/pasj/61.1.29)

(ref: Uehara2019) Uehara, K., Tsuboi, M., Kitamura, Y., Miyawaki, R., & Miyazaki, A. 2019, ApJ, 872, 121, doi: [`10.3847/1538-4357/aafee7`](http://doi.org/10.3847/1538-4357/aafee7)

(ref: vanderTak2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: Verheyen2012) Verheyen, L., Messineo, M., & Menten, K. M. 2012, A&A, 541, A36, doi: [`10.1051/0004-6361/201118265`](http://doi.org/10.1051/0004-6361/201118265)

(ref: Whitmore2016) Whitmore, B. C., Allam, S. S., Budavári, T., et al. 2016, AJ, 151, 134, doi: [`10.3847/0004-6256/151/6/134`](http://doi.org/10.3847/0004-6256/151/6/134)

(ref: Woodward2021) Woodward, C. E., Evans, A., Banerjee, D. P. K., et al. 2021, AJ, 162, 183, doi: [`10.3847/1538-3881/ac1f1e`](http://doi.org/10.3847/1538-3881/ac1f1e)

(ref: Yan2023) Yan, Y. T., Henkel, C., Kobayashi, C., et al. 2023, A&A, 670, A98, doi: [`10.1051/0004-6361/202244584`](http://doi.org/10.1051/0004-6361/202244584)

(ref: Yu2020) Yu, H. Z., Zhang, J. S., Henkel, C., et al. 2020, ApJ, 899, 145, doi: [`10.3847/1538-4357/aba8f1`](http://doi.org/10.3847/1538-4357/aba8f1)

(ref: zengComplexOrganicMolecules2018a) Zeng, S., Jiménez-Serra, I., Rivilla, V. M., et al. 2018, MNRAS, 478, 2962, doi: [`10.1093/mnras/sty1174`](http://doi.org/10.1093/mnras/sty1174)

[^1]: <https://uclchem.github.io>

[^2]: <https://pdr.obspm.fr/>

[^3]: (cite: Kaminski2015) reported $L=1\ensuremath{\mathrm{L}_\odot}$, but that work adopted $d_{CK}=0.7$ kpc; later works have all confirmed that it is more distant (cite: Banerjee2020; Kaminski2021_CKII)

</paper>

Write the methods card for this paper.