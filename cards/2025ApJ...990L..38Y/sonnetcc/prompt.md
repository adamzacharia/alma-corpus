# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...990L..38Y\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...990L..38Y",
 "title": "Unveiling a Population of Strong Galaxy─Galaxy Lensed, Faint Dusty Star-forming Galaxies",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Yang, Ting-Kai",
 "n_authors": 13,
 "arxiv_id": "2506.11601",
 "doi": "10.3847/2041-8213/adfa88",
 "alma_projects_linked_by_archive": [
  "2013.1.00118.S",
  "2013.1.01292.S",
  "2015.1.00055.S",
  "2016.1.00171.S",
  "2016.1.00463.S",
  "2016.1.00478.S",
  "2016.1.00726.S",
  "2016.1.00798.S",
  "2016.1.01208.S",
  "2017.1.00893.S",
  "2018.1.00231.S",
  "2018.1.01128.S",
  "2021.1.00225.S",
  "2021.1.01556.S"
 ]
}
```

Paper text:
<paper>
# Unveiling a Population of Strong Galaxy-Galaxy Lensed Faint Dusty Star-Forming Galaxies

## Abstract

The measurements of the number density of galaxy-galaxy strong lenses can be used to put statistical constraints on the foreground mass distributions. Dusty galaxies uncovered in submillimeter surveys are particularly useful in this regard because of the large volume probed by these surveys. Previous discoveries of strong galaxy-galaxy lensed dusty galaxies are predominantly the brightest in the sky discovered by Herschel, SPT, and Planck. However, models have also predicted a non-negligible fraction of strong galaxy-galaxy lensed faint dusty galaxies, which were difficult to confirm due to technical difficulties. Utilizing the deepest SCUBA-2 submillimeter survey, STUDIES, in both the COSMOS and the UDS fields, together with a red JWST color selection method, we discover a population of 13 strong galaxy-galaxy lensed faint dusty galaxies. The rich ancillary data allow us to confirm their strongly lensed nature via estimates of redshifts and lens modeling. Our systematic search has allowed us to construct the 450 $\ensuremath{\mu}m$ number counts of strongly lensed sources down to the flux levels about an order of magnitude fainter than previous measurements. The measured lensing fractions of $\sim$1% are consistent with predictions from models that also successfully produce the number density of the strong galaxy-galaxy lensed bright dusty galaxies. Future searches from Euclid and Roman are expected to discover orders of magnitude more strongly lensed faint dusty galaxies.

# Introduction

Strong galaxy-galaxy lensing is a powerful tool to probe dark matter by analyzing the foreground gravitational potential responsible for the lensing effect. Fluctuations in mass density along the line of sight significantly impact the gravitational lensing effect, and the spatial mass distribution of the lenses related to the content of dark matter and dark energy (cite: Kochanek1992; Mitchell2005; Grillo2008; Eales2015; Shajib2024). The number density of the strongly lensed sources hence become a crucial measurement in studying mass distribution in the Universe, as the detection of more strongly lensed galaxies implies a greater amount of foreground mass. Apart from studying the mass distribution, galaxy lensing studies also play a crucial role in other areas of research. For example, high-resolution data allows for the detailed examination of the morphology and substructure within the foreground lens galaxies (cite: Mao1998; Dalal2002; Vegetti2010; Hezaveh2016; Powell2023).

The Hubble constant $H_0$ can be independently constrained through time-delay measurements of strongly lensed quasars or supernovae (cite: Refsdal1964; Suyu2010; Wong2020; Treu2022; Kelly2023). The observations taken on the strongly amplified and stretched background lensed galaxies also allow investigations of galaxy properties to exquisite details that are otherwise difficult (cite: Muzzin2012; ALMAPartnership2015; Johnson2017; Canameras2017; Spilker2022).

Dusty star-forming galaxies (DSFGs) are characterized by their high star formation rate (SFR) and high luminosity in the far-infrared and submillimeter wavelengths (cite: Blain2002; 2014PhR...541...45C). These galaxies represent an essential population in the galaxy evolution with extreme star-forming activity. Since most of the DSFGs are located at cosmic noon ($z\sim2$) and beyond (cite: Chapman2005; Dudzeviciute2020; Lim2020; Chen2022), together with the large volume probed by submillimeter surveys thanks to the negative $k$-correction, DSFGs are particularly useful for constraining the foreground mass distribution with a higher probability aligning with other foreground galaxies along the line of sight.

In previous searches of the strongly lensed DSFGs, these sources have predominantly been found in wide and shallow submillimeter or millimeter surveys. In the Herschel Astrophysical Terahertz Large Area Survey (H-ATLAS), the largest submillimeter survey conducted by Herschel, a population of strongly lensed DSFG was identified with flux-limited selection (e.g., $S_{500\,\ensuremath{\mu}m}\gtrsim80-100$ mJy; (cite: 2010Sci...330..800N; 2017MNRAS.465.3558N; 2018MNRAS.473.1751B; 2022MNRAS.511.3017U)).

The same method was used to search for candidates in other Herschel surveys (cite: Wardlow2013; 2016ApJ...823...17N), as well as surveys from other facilities, such as the South Pole Telescope (SPT; (cite: 2013Natur.495..344V; 2020ApJ...902...78R)) and Planck (cite: 2016MNRAS.458.4383H; 2021A&A...653A.151T).

These surveys successfully put measurement constraints on the bright end of the strongly lensed DSFG number density. However, the constraints at the faint end are lacking, where the models have predicted that the fractions of strongly lensed sources to be at the level of $\sim1$% (cite: Cai2013; 2017MNRAS.465.3558N).

Recently, a few individual cases of strongly lensed faint DSFGs have started to be discovered thanks to the advent of deep surveys conducted by the James Webb Space Telescope (JWST; (cite: 2024NatAs...8..119V; 2024MNRAS.52712044P; 2024Mercier)).

To put constraints on the strongly lensed DSFG number density at the faint end, here we perform a systematic search based on the ultra-deep SCUBA-2 survey STUDIES (cite: 2017ApJ...850...37W), as well as recently established color selection methods.

In Section [2](#sec:obs) we describe the data we used. In Section [3](#sec:analyses) we present our search and the results. In Section [4](#sec:sum) we present the summary. We assume flat $\Lambda$CDM cosmology with $H_0=70$ km s$^{-1}$Mpc$^{-1}$, $\Omega_M=0.3$ and $\Omega_\Lambda=0.7$ throughout this paper.

# Observations and Data

## Infrared Data

The JWST imaging data used in this work are based on Near Infrared Camera (NIRCam) observations taken by the PRIMER (cite: 2021jwst.prop.1837D) and COSMOS-Web surveys (cite: 2023ApJ...954...31C). All the JWST data used in this paper can be found in MAST: . COSMOS and UDS field are targeted by PRIMER, using 8 bands NIRCam filters (F090W, F115W, F150W, F200W, F277W, F356W, F410M, and F444W), as well as two bands (F770W and F1800W) from the Mid-Infrared Instrument (MIRI). The total area PRIMER covered in COSMOS and UDS field is 144.72 square arcminutes and 255.88 square arcminutes, respectively. The NIRCam footprint of COSMOS-Web covers $\sim$0.54 square degrees in four bands (F115W, F150W, F277W, and F444W) with a 5$\sigma$ depth reaching down to around 27 magnitudes.

The JWST data products used in this study were processed using a customized data reduction pipeline, built upon the official pipeline (v1.13.4) within the context of `jwst_1237.pmap`. In addition to the official pipeline, our Stage 1 processing includes a snowball masking step, implemented with `snowblind`[^1]. In Stage 3, we introduce several additional steps to mitigate 1/f noise, correct for pedestals and artifacts, address guide star failures that lead to inaccurate world coordinate system (WCS) information, and optimize the outlier detection and mosaicking processes using algorithms specifically designed for large mosaics. For further details, please refer to Vijarnwannaluk et al. (in preparation) for NIRCam reduction and Gao et al. (in preparation) for MIRI reduction.

To facilitate the search of the red DSFGs, in this work, two catalogs derived from the NIRCam imaging data were used. The first catalog, referred to as the original catalog, contains sources extracted from the calibrated NIRCam images in the F277W and F444W filters, with flux values corrected from aperture to total. The second catalog, dubbed the threshold catalog, was specifically created to detect only redder sources and was made as the following. The F444W-F150W difference map was first generated by subtracting the F150W flux from the F444W flux.

Sources with a detection above 10$\sigma$ in this difference map were extracted to form the threshold catalog. This method effectively removed blue objects, producing a catalog optimized for searching red and dusty galaxies. In this threshold catalog, isophotal fluxes across multiple bands were measured in the same segmentation made in the detection process, providing more accurate color information for lensed and extended sources.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID$^{a}$ | RA | Dec | $z_\text{spec,lens}$$^{c}$ | $z_\text{phot,lens}$$^{d}$ | $z_\text{phot,source}$ | Lens model | $\mu$ | $m_I$$^{e}$ | $m_{F150W}$$^{f}$ |
|  | (deg) | (deg) |  |  |  |  |  |  |  |
| COSMOS-001$^{b}$ | 150.10031 | 1.89298 | \- | 1.17 | $3.1^{+3.1}_{-1.5}$ | SIE+shear | $8.1^{+0.1}_{-0.0}$ | 23.74 | 25.23$\pm$0.03 |
| COSMOS-002 | 150.19857 | 2.11697 | 0.6039 | 0.17 | $6.6^{+0.4}_{-4.4}$ | SIE+shear | $1.7^{+0.0}_{-0.1}$ | 22.17 | 24.15$\pm$0.03 |
| COSMOS-003 | 149.91412 | 2.54399 | 0.6778 | 0.64 | $3.5^{+3.0}_{-1.5}$ | SIE+shear | $1.9^{+0.0}_{-0.0}$ | 21.64 | 26.87$\pm$0.15 |
| COSMOS-004 | 150.02852 | 2.55205 | \- | 0.78 | $6.5^{+0.3}_{-4.2}$ | EPL+shear | $3.6^{+0.4}_{-1.4}$ | 19.99 | 23.64$\pm$0.02 |
| COSMOS-005 | 150.05630 | 2.57340 | 0.909 | 1.03 | $4.8^{+0.9}_{-3.2}$ | SIE | $2.4^{+0.0}_{-0.0}$ | 21.54 | 28.08$\pm$0.25 |
| COSMOS-006 | 149.82169 | 1.90706 | 1.3685 | 1.35 | $2.8^{+3.6}_{-0.9}$ | SIE | $4.2^{+0.0}_{-0.0}$ | 23.55 | 23.85$\pm$0.03 |
| COSMOS-007 | 150.44997 | 2.14277 | 0.8891 | 1.05 | $1.3^{+2.5}_{-0.3}$ | EPL | $1.5^{+0.0}_{-0.0}$ | 21.55 | 22.04$\pm$0.01 |
| COSMOS-008 | 149.88085 | 2.12090 | 0.6802 | 0.61 | $3.2^{+2.4}_{-2.1}$ | SIE | $1.4^{+0.0}_{-0.0}$ | 21.48 | 25.31$\pm$0.03 |
| COSMOS-009 | 150.27615 | 2.44736 | 0.22 | 0.22 | $3.0^{+3.1}_{-1.6}$ | EPL | $2.6^{+0.2}_{-0.2}$ | 20.03 | 24.70$\pm$0.03 |
| COSMOS-010 | 150.22805 | 2.55103 | 0.7331 | 0.69 | $3.1^{+0.4}_{-2.0}$ | SIE | $2.3^{+0.3}_{-0.4}$ | 20.97 | 23.63$\pm$0.02 |
| COSMOS-011 | 150.26621 | 2.04930 | 0.96 | 0.99 | $2.6^{+4.1}_{-0.5}$ | SIE+shear | $1.9^{+0.0}_{-0.0}$ | 21.19 | 23.51$\pm$0.02 |
| STUDIES-COS-019$^{b}$ | 150.09994 | 2.29731 | 0.3598 | 0.37 | $2.7^{+0.2}_{-0.7}$ | SIE | $5.4^{+0.0}_{-0.1}$ | 20.13 | 23.30$\pm$0.00 |
| STUDIES-COS-035 | 150.20925 | 2.35513 | 0.1656 | 0.16 | $2.5^{+0.2}_{-0.5}$ | SIE | $2.5^{+0.0}_{-0.0}$ | 18.21 | 21.87$\pm$0.00 |
| STUDIES-COS-049 | 150.16443 | 2.40885 | 0.991 | \- | $2.9^{+3.5}_{-1.0}$ | SIE | $2.4^{+0.0}_{-0.0}$ | 22.85 | 23.37$\pm$0.01 |
| STUDIES-COS-174 | 150.11834 | 2.29226 | 1.0995 | 1.15 | $1.6^{+1.6}_{-0.5}$ | SIE | $2.4^{+0.0}_{-0.0}$ | 22.06 | 21.97$\pm$0.00 |
| STUDIES-COS-195 | 150.09114 | 2.45861 | 0.5976 | \- | $1.3^{+1.8}_{-0.3}$ | SIE | $2.2^{+0.0}_{-0.0}$ | 21.12 | 22.35$\pm$0.00 |
| STUDIES-COS-218 | 150.05421 | 2.33949 | 0.3778 | 0.37 | $2.9^{+0.1}_{-1.5}$ | SIE+shear | $4.7^{+0.0}_{-0.0}$ | 19.44 | 22.23$\pm$0.00 |
| STUDIES-COS-232 | 150.11882 | 2.32435 | 0.6043 | 0.49 | $1.1^{+0.1}_{-0.1}$ | SIE | $2.7^{+0.0}_{-0.0}$ | 20.45 | 21.76$\pm$0.00 |

: Strongly lensed DSFG candidates in COSMOS field.

Table notes: $^{a}$ The IDs STUDIES-COS-XXX are shortened forms of STUDIES-COSMOS-450-XXX, as used in (cite: 2024ApJ...971..117G). $^{b}$ COSMOS-001 is the COSMOS-Web ring discovered by (cite: 2024NatAs...8..119V) and (cite: 2024Mercier). STUDIES-COSMOS-450-019 was identified by (cite: 2024MNRAS.52712044P). $^{c}$ Spectroscopic redshifts of the foreground lenses, obtained from hCOSMOS (cite: 2018ApJS..234...21D), zCOSMOS (cite: 2007ApJS..172...70L), zCOSMOS 20k (cite: 2014MNRAS.438..717K), DESI (cite: 2024AJ....168...58D); DEIMOS (cite: 2018ApJ...858...77H), COSMOS-XS (cite: 2016MNRAS.463..413W; 2017ApJS..233...19C; 2021ApJ...907....5V; 2023AA_673A_67G) $^{d}$ Photometric redshifts of the foreground lenses estimated from EAZY. The uncertainties are less than 1% $^{e}$ The I band AB magnitude of the foreground lenses, obtained from COSMOS2020 catalog (cite: 2022ApJS..258...11W) $^{f}$ The F150W AB magnitude of the background sources in our threshold catalog (Section [2.1](#sec:infrared)).

## Submillimeter Data

The submillimeter data used in this work include observations in COSMOS and UDS fields from the Atacama Large Millimeter Array (ALMA) and the Submillimeter Common-User Bolometer Array 2 (SCUBA-2) mounted on the James Clerk Maxwell Telescope (JCMT). The ultradeep 450 $\ensuremath{\mu}m$ image from SCUBA-2 was based on the SCUBA-2 Ultra Deep Imaging EAO Survey (cite: 2017ApJ...850...37W), where the latest release (cite: 2024ApJ...971..117G) has combined data from other surveys such as the SCUBA-2 Cosmology Legacy Survey (cite: 2013MNRAS.432...53G), the SCUBA-2 COSMOS survey (cite: 2019ApJ...880...43S), as well as smaller-scale surveys (e.g., (cite: 2013MNRAS.436.1919C)). The final STUDIES images have reached a noise level of $\sigma_{450}$=0.6 mJy beam$^{-1}$, detecting over 400 DSFGs that are up to one order of magnitude fainter than those detected by Herschel at 500 $\ensuremath{\mu}m$, making STUDIES an ideal venue to search for strongly lensed faint DSFGs. The JWST counterparts of STUDIES 450 $\ensuremath{\mu}m$ sources are identified by cross-matching our JWST catalogs with the positions reported in the existing ALMA (AS2COSMOS, A3COSMOS), VLA (1.4 and 3 GHz), or MIPS catalogs (Gao et al. in preparation).

In addition to the 450 $\ensuremath{\mu}m$ data, we also make use of the 850 $\ensuremath{\mu}m$ image from SCUBA-2, which was sourced from S2COSMOS (cite: 2019ApJ...880...43S). The ALMA imaging data were obtained from the ALMA Science Archive.

# Analyses and Results

## Identification of strongly lensed DSFGs

![](Figure1_position/Fig1_1.png)

Our method of identifying strongly lensed systems is the following; We first select strongly lensed candidates by visually inspecting the JWST r-g-b (F444W-F277W-F150W) false-color cutout images. Sources that have morphology resembling lensing arcs or rings, or configurations that are consistent with red emission located near foreground large bluer sources, are all selected. At this stage, we take a conservative approach that aims to select all sources that could potentially be lensed. These candidates are then passed to the second stage where we perform redshift analyses and lens modeling in order to confirm their strongly lensed nature.

The above method is applied to two sets of sources. The first is the STUDIES 450 $\ensuremath{\mu}m$ catalog, and seven candidates have been identified. Their associations with STUDIES sources are all confirmed via counterpart identifications of ALMA, VLA, or MIPS catalogs.

To allow the search of faint DSFG across the full COSMOS-Web field, including the regions outside the STUDIES footprint, the second set of sources are identified via a color selection method, where the F444W flux density is required to exceed 1 $\mu$Jy and a flux ratio between F444W and F150W is greater than 3.5 (cite: 2023ApJ...956...95B). The efficacy of these color and flux criteria for the selection of faint DSFGs is further verified recently by (cite: McKay:2025aa). To consider the color of the extended sources, we used the isophotal flux from the threshold catalog, which is measured in the same segmentation across different bands. The flux in F444W was taken from the original catalog, which were corrected to total. The cut of 10 $\sigma$ in the threshold catalog corresponds to the F444W-to-F150W flux ratio of about 1, meaning that the process of making the threshold catalog does not lead to missing red sources that satisfy the color criteria. Using these flux and color selection criteria, we identified 11,873 candidate dusty galaxies in the COSMOS-Web field and 1,425 in the PRIMER-UDS field. We visually inspect them to identify candidate strong lensing systems, following the same approach as we did for the STUDIES sources.

To confirm the dusty nature of these red sources, we performed a stacking analysis of submillimeter data. The weighted mean stacking shows a flux density of 0.79$\pm$0.04 mJy/beam at 850 $\ensuremath{\mu}m$, and 3.08$\pm$0.16 mJy/beam at 450 $\ensuremath{\mu}m$ in the COSMOS-Web field, indicating submillimeter detections with high signal-to-noise ratios. The stacking in the PRIMER-UDS field has yielded consistent results, and stacking instead in the median also does not change the results significantly. Eventually, in this second set of red sources, we identify 13 strongly lensed candidates, again all in the COSMOS field.

Therefore, in total, we identified 18 potential strongly lensed sources in the COSMOS field. Of these, 13 were selected from the red JWST sources, and 7 were identified from the STUDIES 450 $\ensuremath{\mu}m$ catalog, with two of the sources overlapped. The source coordinates are given in Table [\[table1\]](#table1), and the overview of their locations on the COSMOS-Web footprint is shown in Figure [1](#fig:position). Note that none of the candidates are found in the PRIMER-UDS field, which could be attributed to the 10 times smaller footprint and possibly field-to-field variations.

Among the selected sources, COSMOS-001 and STUDIES-COSMOS-450-019 (cite: 2024A&A...690L..16J) have been found and confirmed as strongly lensed in previous studies (cite: 2024MNRAS.52712044P; 2024NatAs...8..119V; 2024Mercier). The latter source had also been identified as a potential lensing candidate in earlier studies (cite: 2018ApJ...864...56J; 2021ApJ...913....6H). (cite: 2018ApJ...864...56J) also mentioned the other two lensing candidates, one of which is found in our work as COSMOS-005 (ID85004261, AzTEC/C10), but the other lies outside the COSMOS-Web area.

![](Figure2_cutouts_photz/019.png)

For these 18 lensed candidates, we checked their individual submillimeter detections using SCUBA-2 and ALMA data. Seven of the 18 show individual detections over 3$\sigma$ in the SCUBA-2 850$\ensuremath{\mu}m$ data, and 450 $\ensuremath{\mu}m$ detections are only found from the STUDIES sources. Looking at ALMA archival data, we found that 15 sources had been observed and three of them exhibit detections above 3$\sigma$. The rest of the non-detection in ALMA can be attributed to too low of sensitivity. An example source with SCUBA-2 450 $\ensuremath{\mu}m$ and JWST cutout images is shown in Figure [2](#fig:cutout_photz), and the rest of the source cutouts are shown in the Appendix.

## Photometric redshift

For the strongly gravitational lensed sources and their foreground lenses, we obtained photometric redshifts (photo-$z$) using EAZY (cite: 2008ApJ...686.1503B). The spectral energy distribution (SED) of the lensed sources was fitted using the EAZY template set from (cite: 2008ApJ...686.1503B) that accounts for dusty galaxies, with photometry from the four JWST bands (F115W, F150W, F277W, and F444W). For the foreground galaxies, SED fitting was performed with also EAZY template in 36 to 38 bands, including the four JWST bands and additional photometry listed in the COSMOS2020 catalog (cite: 2022ApJS..258...11W). An example set of SED fitting results and the probability distributions of photometric redshifts for one system is shown in Figure [2](#fig:cutout_photz), and the redshifts are given in Table [\[table1\]](#table1).

In our 18 potential lensing systems, 16 lenses have spectroscopic redshifts, which are obtained from past studies (cite: 2024AJ....168...58D; 2023AA_673A_67G; 2021ApJ...907....5V; 2018ApJ...858...77H; 2018ApJS..234...21D; 2017ApJS..233...19C; 2016MNRAS.463..413W; 2014MNRAS.438..717K; 2007ApJS..172...70L). Our photo-$z$ results are consistent with spectroscopic redshifts for most lenses. Two lenses do not have good photo-$z$ solutions, however they do have spectroscopic redshifts.

Recently, a study estimated the photometric redshift of 019 (COSBO-7) to be greater than 7 by fitting 10 NIRCam bands using four independent SED fitting codes (cite: 2024ApJ...969L..28L). However, this estimate was soon refuted by the spectroscopic redshift of z = 2.625, confirmed by robust lines detected by ALMA (cite: 2024A&A...690L..16J). Our photometric redshift estimation for this source aligns with the spectroscopic redshift for both lens and source in the 019 lensing system, again validating our redshift analyses.

Although the photometric redshifts of the background sources have large uncertainties, all lensed sources exhibit higher photo-$z$ values compared to their foreground lenses, confirming the necessary conditions for gravitational lensing.

## Lens modeling

To confirm the strongly lensed nature of the selected systems, which is typically defined as having a lensing magnification greater than 2, we performed detailed foreground lens modeling using Lenstronomy (cite: 2021JOSS....6.3283B; 2018PDU....22..189B), a multi-purpose gravitational lens modeling software package based on (cite: 2015ApJ...813..102B). We first mask the observed 6$''\times6''$ images using the segmentation map to isolate the relevant components, minimizing contamination from unrelated sources.

In the modeling process, we input the mass distribution for the foreground lens and the light profiles for both the lens and the source. By constructing a model image, we were able to fit the observed data and obtain the best-fit parameters. For the model of foreground mass distribution, we tried Singular Isothermal Ellipse (SIE) and Elliptical Power Law (EPL), with and without cosmic shear, and selected the best fit model for each system. Sérsic ellipse is considered as the light profile for both lens and source. For COSMOS-005, which has a more complex foreground, we considered 2 Sérsic ellipse to obtain a better fitting result. The fitting was performed simultaneously on images from two bands, F444W and F150W, using Particle Swarm Optimization (PSO) and Markov Chain Monte Carlo (MCMC) methods. An example of the constructed model image and the residual is shown in Figure [3](#fig:lens_modeling). The modeling results of the best-fit mass distribution models and magnification factors for each system are exhibited in Table [\[table1\]](#table1). Among the 18 candidates, 13 are confirmed strong lensing systems with magnifications greater than 2. These 13 sources are then passed to the next stage for the construction of number counts.

Recently, over 100 candidates of strong galaxy-galaxy lensing have been reported in the COSMOS-Web field by (cite: Nightingale:2025aa), and we find that nine of our sources can be matched to theirs, where five are matched to STUDIES sources and four to the color-selected sources. Since both our work and that of (cite: Nightingale:2025aa) rely on visual inspection, it is possible that the mismatch is caused by some level of incompleteness.

For the nine matches, we find a good agreement in the reported lensing magnification, with a median ratio of 1.2$\pm$0.3, where the values reported by (cite: Nightingale:2025aa) are slightly higher. This confirms our lens modeling method and the strong lensing nature of our sample.

![](Figure3_lens_modeling/019.png)

## Number counts of strongly lensed faint DSFGs

The cumulative number counts of strongly lensed STUDIES sources are calculated following the well-established methods for constructing counts outlined in the original SCUBA-2 survey (cite: 2024ApJ...971..117G), where corrections for spurious fraction, flux boosting, and completeness are properly taken into account via extensive simulations. We note that the total area considered is the combined area of STUDIES footprint in both COSMOS and UDS. The results are given in Table 2 in the Appendix and plotted in Figure [4](#fig:density-flux), together with the counts in the literature and model prediction. Our measurements follow the extrapolation of the bright counts and extend to a flux limit about seven times fainter than the previous limit. Our counts are slightly higher than the pilot search within the STUDIES footprint (cite: 2024MNRAS.52712044P) due to more sources discovered. Our results are higher than the model predictions from (cite: Sedgwick:2025aa) but consistent with those from (cite: 2017MNRAS.465.3558N), which appears to be successful in reproducing the observed counts, both lensed and unlensed, across two orders of magnitude in fluxes. The different predictions from the two models highlight the need to conduct more extensive search of faint lensed DSFGs in order to perform more rigorous tests.

It is worth mentioning that while the JWST counterparts of the STUDIES sources are confirmed via higher resolution images from ALMA, VLA, and MIPS, two systems that do not have ALMA data, STUDIES-COSMOS-450-035 and STUDIES-COSMOS-450-218, appear to have their MIPS or VLA emissions located closer to the foreground lens. The blue nature of the lenses suggests that they are not likely to be the origin of the 450 $\ensuremath{\mu}m$ emissions. What is more likely is that the background lensed dusty sources have a second lensed image that is closer to the foreground lens. This can be seen in STUDIES-COSMOS-450-019 and STUDIES-COSMOS-450-232. However, in order to definitely rule out the possibility of 450 $\ensuremath{\mu}m$ emissions coming from the foreground lenses, follow-up observations are needed.

![](Figure4_density-flux/Fig4.png)

For the red DSFGs identified in the wider COSMOS-Web footprint, we calculated the number density based on the survey area of both COSMOS-Web and PRIMER-UDS and plotted the result in Figure [4](#fig:density-flux) at the weighted stacked submillimeter flux density. The counts appear lower than the model prediction. However, the red color selection method, while proven efficient, is likely incomplete. In fact, in the latest study by (cite: McKay:2025aa), they found that the completeness of the color-base method to be about 80% for DSFGs selected at 870 $\mu$m or 1.1/1.2 mm. Among the seven strongly lensed DSFGs identified in STUDIES, only two meet the color selection criteria, confirming incompleteness. We therefore treat the color-base measurement as a lower limit, implying that our results are consistent with the model.

Lastly, the number density of strongly lensed DSFGs in our results exhibited field-to-field variation. All strongly lensed DSFGs in our sample are located in the COSMOS-Web field, which is approximately 10 times larger than the PRIMER-UDS field. Assuming the same number density as in the COSMOS field, we would expect to find one or two strongly lensed DSFGs in the PRIMER-UDS field; however, none has been found. The difference is more apparent when we consider only the STUDIES footprint, which is comparable between COSMOS and UDS. One possibility is that the STUDIES footprint in the COSMOS field covers overdense foreground. Indeed, the weak lensing analyses have shown that the STUDIES-COSMOS field exhibits enhanced E-mode shear correlation signals, suggesting a region of stronger lensing (cite: Massey:2007aa).

# Summary

We have conducted a systematic search of strongly lensed submillimeter-faint dusty galaxies using SCUBA-2 and JWST data in the COSMOS and UDS fields. In the COSMOS field, we identified 18 strongly lensed candidates, including seven sources individually detected in STUDIES and 11 JWST flux- and color-selected DSFGs. To confirm their lensing nature, we derived photometric redshifts for both the foreground lenses and background sources and performed foreground lens modeling with high-resolution JWST imaging data. Among the 18 candidates, 13 are confirmed strong lensing with magnification greater than 2. Our findings provide an observational constraint on the number density of strongly lensed faint DSFGs, which is about 1% relative to the unlensed sources at the same flux range. Comparing our results with theoretical predictions, we find an agreement within $\rm \pm\,1-\sigma$ uncertainty, particularly constraining the faint end of the model. However, no strongly lensed DSFGs were found in the PRIMER-UDS field, suggesting a field-to-field variation.

The discovery of these systems offers a unique opportunity to probe the early universe and study dusty galaxies. The lensing magnification allows us to investigate the physical properties of intrinsically faint galaxies that could otherwise remain undetected. Detailed follow-up observations with JWST NIRSpec or ALMA could provide spectroscopic confirmation of redshifts and further characterize the properties of these galaxies.

The unparalleled imaging capabilities of JWST in both depth and resolution have recently allowed the discovery of over 100 strong galaxy-galaxy lenses (cite: Nightingale:2025aa). In addition, the Euclid mission has begun to produce candidates for strong galaxy-galaxy lensing (cite: Nagam2025; Euclid:2025aa), with the prospect of detecting more than 10,000 faint DSFGs in its full survey (cite: Sedgwick:2025aa). Indeed, considering the depths that Euclid will reach (e.g., $I_{\rm E}$ = 26.3 and $Y_{\rm E}$/$J_{\rm E}$/$H_{\rm E}$ = 24.5; (cite: Euclid:2022aa)), all foreground lenses and most background lensed DSFGs of our sample are expected to be detected. It is therefore expected that the statistical constraint on strongly lensed DSFGs will improve by orders of magnitude in the coming years.

# Acknowledgments

T.-K.Y and C.-C.C. and acknowledge support from the National Science and Technology Council of Taiwan (111-2112-M-001-045-MY3), as well as Academia Sinica through the Career Development Award (AS-CDA-112-M02). We are grateful to the maintenance and administrative staff of our institutions, whose efforts to support our day-to-day work environment make our scientific discoveries possible. This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with program #1727 and #1837. The James Clerk Maxwell Telescope is operated by the East Asian Observatory on behalf of The National Astronomical Observatory of Japan; Academia Sinica Institute of Astronomy and Astrophysics; the Korea Astronomy and Space Science Institute; the National Astronomical Research Institute of Thailand; Center for Astronomical Mega-Science (as well as the National Key R&D Program of China with No. 2017YFA0402700). Additional funding support is provided by the Science and Technology Facilities Council of the United Kingdom and participating universities and organizations in the United Kingdom and Canada. Additional funds for the construction of SCUBA-2 were provided by the Canada Foundation for Innovation. The authors wish to recognize and acknowledge the very significant cultural role and reverence that the summit of Maunakea has always had within the indigenous Hawaiian community. We are most fortunate to have the opportunity to conduct observations from this mountain. This paper makes use of the following ALMA data: ADS/JAO.ALMA 2021.1.00225.S, 2021.1.01556.S, 2018.1.00231.S, 2018.1.01128.S, 2017.1.00893.S, 2016.1.00171.S, 2016.1.00463.S, 2016.1.00478.S, 2016.1.00726.S, 2016.1.00798.S, 2016.1.01208.S, 2015.1.00055.S, 2013.1.00118.S, 2013.1.01292.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. JP and SS are supported by the ACME, ELSA, and OSCARS projects. "ACME: Astrophysics Centre for Multimessenger studies in Europe", "ELSA: Euclid Legacy Science Advanced analysis tools", and "OSCARS: Open Science Clusters’ Action for Research and Society" are funded by the European Union under grant agreement no. 101131928, 101135203, and 101129751, respectively; ELSA is also funded by Innovate UK grant 10093177. Views and opinions expressed are however those of the authors only and do not necessarily reflect those of the European Union.

# Facilities

JWST (NIRCam), JCMT (SCUBA-2), ALMA

# Software

astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A), EAZY (cite: 2008ApJ...686.1503B), Lenstronomy (cite: 2021JOSS....6.3283B; 2018PDU....22..189B)

Source Extractor (cite: Bertin1996)

|  |  |
|:--:|:--:|
| ![image](Figure2_cutouts_photz/001.png) | ![image](Figure2_cutouts_photz/006.png) |
| ![image](Figure2_cutouts_photz/002.png) | ![image](Figure2_cutouts_photz/007.png) |
| ![image](Figure2_cutouts_photz/003.png) | ![image](Figure2_cutouts_photz/008.png) |
| ![image](Figure2_cutouts_photz/004.png) | ![image](Figure2_cutouts_photz/009.png) |
| ![image](Figure2_cutouts_photz/005.png) | ![image](Figure2_cutouts_photz/010.png) |

|  |  |
|:--:|:--:|
| ![image](Figure2_cutouts_photz/011.png) | ![image](Figure2_cutouts_photz/174.png) |
| ![image](Figure2_cutouts_photz/019.png) | ![image](Figure2_cutouts_photz/195.png) |
| ![image](Figure2_cutouts_photz/035.png) | ![image](Figure2_cutouts_photz/218.png) |
| ![image](Figure2_cutouts_photz/049.png) | ![image](Figure2_cutouts_photz/232.png) |

|  |  |
|:--:|:--:|
| ![image](Figure3_lens_modeling/001.png) | ![image](Figure3_lens_modeling/008.png) |
| ![image](Figure3_lens_modeling/002.png) | ![image](Figure3_lens_modeling/009.png) |
| ![image](Figure3_lens_modeling/003.png) | ![image](Figure3_lens_modeling/010.png) |
| ![image](Figure3_lens_modeling/004.png) | ![image](Figure3_lens_modeling/011.png) |
| ![image](Figure3_lens_modeling/005.png) | ![image](Figure3_lens_modeling/019.png) |
| ![image](Figure3_lens_modeling/006.png) | ![image](Figure3_lens_modeling/035.png) |
| ![image](Figure3_lens_modeling/007.png) | ![image](Figure3_lens_modeling/049.png) |

|  |  |
|:--:|:--:|
| ![image](Figure3_lens_modeling/174.png) | ![image](Figure3_lens_modeling/218.png) |
| ![image](Figure3_lens_modeling/195.png) | ![image](Figure3_lens_modeling/232.png) |

|           |                           |
|:---------:|:-------------------------:|
| S$_{450}$ |          N($>$S)          |
|   (mJy)   |       (deg$^{-2}$)        |
|   18.46   |   8.4$_{-6.9}^{+19.3}$    |
|   17.22   |  17.0$_{-14.0}^{+39.0}$   |
|   7.50    |  28.4$_{-23.5}^{+65.3}$   |
|   6.26    |  42.0$_{-34.7}^{+96.6}$   |
|   5.91    |  56.6$_{-46.8}^{+130.2}$  |
|   4.23    |  84.2$_{-69.6}^{+193.7}$  |
|   3.68    | 121.2$_{-100.2}^{+278.8}$ |

: STUDIES strongly lensed cumulative number count at 450 $\mu$m

natexlab

(ref: ALMAPartnership2015) ALMA Partnership, Vlahakis, C., Hunter, T. R., et al. 2015, ApJL, 808, L4, doi: [`10.1088/2041-8205/808/1/L4`](http://doi.org/10.1088/2041-8205/808/1/L4)

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2024MNRAS.527.8865B) Bakx, T. J. L. C., Gray, B. S., González-Nuevo, J., et al. 2024, MNRAS, 527, 8865, doi: [`10.1093/mnras/stad3759`](http://doi.org/10.1093/mnras/stad3759)

(ref: 2018MNRAS.473.1751B) Bakx, T. J. L. C., Eales, S. A., Negrello, M., et al. 2018, MNRAS, 473, 1751, doi: [`10.1093/mnras/stx2267`](http://doi.org/10.1093/mnras/stx2267)

(ref: 2023ApJ...956...95B) Barger, A. J., & Cowie, L. L. 2023, ApJ, 956, 95, doi: [`10.3847/1538-4357/acedae`](http://doi.org/10.3847/1538-4357/acedae)

(ref: Bertin1996) Bertin, E., & Arnouts, S. 1996, A&AS, 117, 393, doi: [`10.1051/aas:1996164`](http://doi.org/10.1051/aas:1996164)

(ref: 2018PDU....22..189B) Birrer, S., & Amara, A. 2018, Physics of the Dark Universe, 22, 189, doi: [`10.1016/j.dark.2018.11.002`](http://doi.org/10.1016/j.dark.2018.11.002)

(ref: 2015ApJ...813..102B) Birrer, S., Amara, A., & Refregier, A. 2015, ApJ, 813, 102, doi: [`10.1088/0004-637X/813/2/102`](http://doi.org/10.1088/0004-637X/813/2/102)

(ref: 2021JOSS....6.3283B) Birrer, S., Shajib, A., Gilman, D., et al. 2021, The Journal of Open Source Software, 6, 3283, doi: [`10.21105/joss.03283`](http://doi.org/10.21105/joss.03283)

(ref: Blain2002) Blain, A. W., Smail, I., Ivison, R. J., Kneib, J. P., & Frayer, D. T. 2002, Phys. Rep., 369, 111, doi: [`10.1016/S0370-1573(02)00134-5`](http://doi.org/10.1016/S0370-1573(02)00134-5)

(ref: 2008ApJ...686.1503B) Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, ApJ, 686, 1503, doi: [`10.1086/591786`](http://doi.org/10.1086/591786)

(ref: Canameras2017) Cañameras, R., Nesvadba, N., Kneissl, R., et al. 2017, A&A, 604, A117, doi: [`10.1051/0004-6361/201630186`](http://doi.org/10.1051/0004-6361/201630186)

(ref: Cai2013) Cai, Z.-Y., Lapi, A., Xia, J.-Q., et al. 2013, ApJ, 768, 21, doi: [`10.1088/0004-637X/768/1/21`](http://doi.org/10.1088/0004-637X/768/1/21)

(ref: 2014PhR...541...45C) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45, doi: [`10.1016/j.physrep.2014.02.009`](http://doi.org/10.1016/j.physrep.2014.02.009)

(ref: 2013MNRAS.436.1919C) Casey, C. M., Chen, C.-C., Cowie, L. L., et al. 2013, MNRAS, 436, 1919, doi: [`10.1093/mnras/stt1673`](http://doi.org/10.1093/mnras/stt1673)

(ref: 2023ApJ...954...31C) Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023, ApJ, 954, 31, doi: [`10.3847/1538-4357/acc2bc`](http://doi.org/10.3847/1538-4357/acc2bc)

(ref: 2017ApJS..233...19C) Chang, Y.-Y., Le Floc’h, E., Juneau, S., et al. 2017, ApJS, 233, 19, doi: [`10.3847/1538-4365/aa97da`](http://doi.org/10.3847/1538-4365/aa97da)

(ref: Chapman2005) Chapman, S. C., Blain, A. W., Smail, I., & Ivison, R. J. 2005, ApJ, 622, 772, doi: [`10.1086/428082`](http://doi.org/10.1086/428082)

(ref: 2013ApJ...776..131C) Chen, C.-C., Cowie, L. L., Barger, A. J., et al. 2013, ApJ, 776, 131, doi: [`10.1088/0004-637X/776/2/131`](http://doi.org/10.1088/0004-637X/776/2/131)

(ref: Chen2022) Chen, C.-C., Liao, C.-L., Smail, I., et al. 2022, ApJ, 929, 159, doi: [`10.3847/1538-4357/ac61df`](http://doi.org/10.3847/1538-4357/ac61df)

(ref: Dalal2002) Dalal, N., & Kochanek, C. S. 2002, ApJ, 572, 25, doi: [`10.1086/340303`](http://doi.org/10.1086/340303)

(ref: 2018ApJS..234...21D) Damjanov, I., Zahid, H. J., Geller, M. J., Fabricant, D. G., & Hwang, H. S. 2018, ApJS, 234, 21, doi: [`10.3847/1538-4365/aaa01c`](http://doi.org/10.3847/1538-4365/aaa01c)

(ref: 2024AJ....168...58D) DESI Collaboration, Adame, A. G., Aguilar, J., et al. 2024, AJ, 168, 58, doi: [`10.3847/1538-3881/ad3217`](http://doi.org/10.3847/1538-3881/ad3217)

(ref: Dudzeviciute2020) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828, doi: [`10.1093/mnras/staa769`](http://doi.org/10.1093/mnras/staa769)

(ref: 2021jwst.prop.1837D) Dunlop, J. S., Abraham, R. G., Ashby, M. L. N., et al. 2021, PRIMER: Public Release IMaging for Extragalactic Research, JWST Proposal. Cycle 1, ID. #1837

(ref: Eales2015) Eales, S. A. 2015, MNRAS, 446, 3224, doi: [`10.1093/mnras/stu2214`](http://doi.org/10.1093/mnras/stu2214)

(ref: Euclid:2022aa) Euclid Collaboration, Scaramella, R., Amiaux, J., et al. 2022, A&A, 662, A112, doi: [`10.1051/0004-6361/202141938`](http://doi.org/10.1051/0004-6361/202141938)

(ref: Euclid:2025aa) Euclid Collaboration, Walmsley, M., Holloway, P., et al. 2025, arXiv e-prints, arXiv:2503.15324. [`https://arxiv.org/abs/2503.15324`](https://arxiv.org/abs/2503.15324)

(ref: 2024ApJ...971..117G) Gao, Z.-K., Lim, C.-F., Wang, W.-H., et al. 2024, ApJ, 971, 117, doi: [`10.3847/1538-4357/ad53c1`](http://doi.org/10.3847/1538-4357/ad53c1)

(ref: 2013MNRAS.432...53G) Geach, J. E., Chapin, E. L., Coppin, K. E. K., et al. 2013, MNRAS, 432, 53, doi: [`10.1093/mnras/stt352`](http://doi.org/10.1093/mnras/stt352)

(ref: 2023AA_673A_67G) Georgantopoulos, I., Pouliasis, E., Mountrichas, G., et al. 2023, A&A, 673, A67, doi: [`10.1051/0004-6361/202244875`](http://doi.org/10.1051/0004-6361/202244875)

(ref: Grillo2008) Grillo, C., Lombardi, M., & Bertin, G. 2008, A&A, 477, 397, doi: [`10.1051/0004-6361:20077534`](http://doi.org/10.1051/0004-6361:20077534)

(ref: 2016MNRAS.458.4383H) Harrington, K. C., Yun, M. S., Cybulski, R., et al. 2016, MNRAS, 458, 4383, doi: [`10.1093/mnras/stw614`](http://doi.org/10.1093/mnras/stw614)

(ref: 2018ApJ...858...77H) Hasinger, G., Capak, P., Salvato, M., et al. 2018, ApJ, 858, 77, doi: [`10.3847/1538-4357/aabacf`](http://doi.org/10.3847/1538-4357/aabacf)

(ref: Hezaveh2016) Hezaveh, Y. D., Dalal, N., Marrone, D. P., et al. 2016, ApJ, 823, 37, doi: [`10.3847/0004-637X/823/1/37`](http://doi.org/10.3847/0004-637X/823/1/37)

(ref: 2024ApJ...964L..32H) Hsu, Q.-N., Cowie, L. L., Chen, C.-C., & Barger, A. J. 2024, ApJL, 964, L32, doi: [`10.3847/2041-8213/ad3421`](http://doi.org/10.3847/2041-8213/ad3421)

(ref: 2021ApJ...913....6H) Hwang, Y.-H., Wang, W.-H., Chang, Y.-Y., et al. 2021, ApJ, 913, 6, doi: [`10.3847/1538-4357/abf11a`](http://doi.org/10.3847/1538-4357/abf11a)

(ref: 2018ApJ...864...56J) Jin, S., Daddi, E., Liu, D., et al. 2018, ApJ, 864, 56, doi: [`10.3847/1538-4357/aad4af`](http://doi.org/10.3847/1538-4357/aad4af)

(ref: 2024A&A...690L..16J) Jin, S., Sillassen, N. B., Hodge, J., et al. 2024, A&A, 690, L16, doi: [`10.1051/0004-6361/202451445`](http://doi.org/10.1051/0004-6361/202451445)

(ref: Johnson2017) Johnson, T. L., Rigby, J. R., Sharon, K., et al. 2017, ApJL, 843, L21, doi: [`10.3847/2041-8213/aa7516`](http://doi.org/10.3847/2041-8213/aa7516)

(ref: Kelly2023) Kelly, P. L., Rodney, S., Treu, T., et al. 2023, Science, 380, abh1322, doi: [`10.1126/science.abh1322`](http://doi.org/10.1126/science.abh1322)

(ref: Kochanek1992) Kochanek, C. S. 1992, ApJ, 384, 1, doi: [`10.1086/170845`](http://doi.org/10.1086/170845)

(ref: 2014MNRAS.438..717K) Kovač, K., Lilly, S. J., Knobel, C., et al. 2014, MNRAS, 438, 717, doi: [`10.1093/mnras/stt2241`](http://doi.org/10.1093/mnras/stt2241)

(ref: 2007ApJS..172...70L) Lilly, S. J., Le Fèvre, O., Renzini, A., et al. 2007, ApJS, 172, 70, doi: [`10.1086/516589`](http://doi.org/10.1086/516589)

(ref: Lim2020) Lim, C.-F., Wang, W.-H., Smail, I., et al. 2020, ApJ, 889, 80, doi: [`10.3847/1538-4357/ab607f`](http://doi.org/10.3847/1538-4357/ab607f)

(ref: 2024ApJ...969L..28L) Ling, C., Sun, B., Cheng, C., et al. 2024, ApJL, 969, L28, doi: [`10.3847/2041-8213/ad59a3`](http://doi.org/10.3847/2041-8213/ad59a3)

(ref: Mao1998) Mao, S., & Schneider, P. 1998, MNRAS, 295, 587, doi: [`10.1046/j.1365-8711.1998.01319.x`](http://doi.org/10.1046/j.1365-8711.1998.01319.x)

(ref: Massey:2007aa) Massey, R., Rhodes, J., Leauthaud, A., et al. 2007, ApJS, 172, 239, doi: [`10.1086/516599`](http://doi.org/10.1086/516599)

(ref: McKay:2025aa) McKay, S. J., Barger, A. J., Cowie, L. L., & Nicandro Rosenthal, M. J. 2025, arXiv e-prints, arXiv:2503.00102, doi: [`10.48550/arXiv.2503.00102`](http://doi.org/10.48550/arXiv.2503.00102)

(ref: 2024Mercier) Mercier, W., Shuntov, M., Gavazzi, R., et al. 2024, A&A, 687, A61, doi: [`10.1051/0004-6361/202348095`](http://doi.org/10.1051/0004-6361/202348095)

(ref: Mitchell2005) Mitchell, J. L., Keeton, C. R., Frieman, J. A., & Sheth, R. K. 2005, ApJ, 622, 81, doi: [`10.1086/427910`](http://doi.org/10.1086/427910)

(ref: Muzzin2012) Muzzin, A., Labbé, I., Franx, M., et al. 2012, ApJ, 761, 142, doi: [`10.1088/0004-637X/761/2/142`](http://doi.org/10.1088/0004-637X/761/2/142)

(ref: Nagam2025) Nagam, B. C., Acevedo Barroso, J. A., Wilde, J., et al. 2025, arXiv e-prints, arXiv:2502.09802, doi: [`10.48550/arXiv.2502.09802`](http://doi.org/10.48550/arXiv.2502.09802)

(ref: 2016ApJ...823...17N) Nayyeri, H., Keele, M., Cooray, A., et al. 2016, ApJ, 823, 17, doi: [`10.3847/0004-637X/823/1/17`](http://doi.org/10.3847/0004-637X/823/1/17)

(ref: 2010Sci...330..800N) Negrello, M., Hopwood, R., De Zotti, G., et al. 2010, Science, 330, 800, doi: [`10.1126/science.1193420`](http://doi.org/10.1126/science.1193420)

(ref: 2017MNRAS.465.3558N) Negrello, M., Amber, S., Amvrosiadis, A., et al. 2017, MNRAS, 465, 3558, doi: [`10.1093/mnras/stw2911`](http://doi.org/10.1093/mnras/stw2911)

(ref: Nightingale:2025aa) Nightingale, J., Mahler, G., McCleary, J., et al. 2025, arXiv e-prints, arXiv:2503.08777, doi: [`10.48550/arXiv.2503.08777`](http://doi.org/10.48550/arXiv.2503.08777)

(ref: 2024MNRAS.52712044P) Pearson, J., Serjeant, S., Wang, W.-H., et al. 2024, MNRAS, 527, 12044, doi: [`10.1093/mnras/stad3916`](http://doi.org/10.1093/mnras/stad3916)

(ref: Powell2023) Powell, D. M., Vegetti, S., McKean, J. P., et al. 2023, MNRAS, 524, L84, doi: [`10.1093/mnrasl/slad074`](http://doi.org/10.1093/mnrasl/slad074)

(ref: Refsdal1964) Refsdal, S. 1964, MNRAS, 128, 307, doi: [`10.1093/mnras/128.4.307`](http://doi.org/10.1093/mnras/128.4.307)

(ref: 2020ApJ...902...78R) Reuter, C., Vieira, J. D., Spilker, J. S., et al. 2020, ApJ, 902, 78, doi: [`10.3847/1538-4357/abb599`](http://doi.org/10.3847/1538-4357/abb599)

(ref: Sedgwick:2025aa) Sedgwick, C., Serjeant, S., & Weiner, C. 2025, MNRAS, doi: [`10.1093/mnras/staf414`](http://doi.org/10.1093/mnras/staf414)

(ref: Shajib2024) Shajib, A. J., Vernardos, G., Collett, T. E., et al. 2024, Space Sci. Rev., 220, 87, doi: [`10.1007/s11214-024-01105-x`](http://doi.org/10.1007/s11214-024-01105-x)

(ref: 2019ApJ...880...43S) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2019, ApJ, 880, 43, doi: [`10.3847/1538-4357/ab23ff`](http://doi.org/10.3847/1538-4357/ab23ff)

(ref: Spilker2022) Spilker, J. S., Hayward, C. C., Marrone, D. P., et al. 2022, ApJL, 929, L3, doi: [`10.3847/2041-8213/ac61e6`](http://doi.org/10.3847/2041-8213/ac61e6)

(ref: Suyu2010) Suyu, S. H., Marshall, P. J., Auger, M. W., et al. 2010, ApJ, 711, 201, doi: [`10.1088/0004-637X/711/1/201`](http://doi.org/10.1088/0004-637X/711/1/201)

(ref: Treu2022) Treu, T., Suyu, S. H., & Marshall, P. J. 2022, A&ARv, 30, 8, doi: [`10.1007/s00159-022-00145-y`](http://doi.org/10.1007/s00159-022-00145-y)

(ref: 2021A&A...653A.151T) Trombetti, T., Burigana, C., Bonato, M., et al. 2021, A&A, 653, A151, doi: [`10.1051/0004-6361/202140830`](http://doi.org/10.1051/0004-6361/202140830)

(ref: 2022MNRAS.511.3017U) Urquhart, S. A., Bendo, G. J., Serjeant, S., et al. 2022, MNRAS, 511, 3017, doi: [`10.1093/mnras/stac150`](http://doi.org/10.1093/mnras/stac150)

(ref: 2021ApJ...907....5V) van der Vlugt, D., Algera, H. S. B., Hodge, J. A., et al. 2021, ApJ, 907, 5, doi: [`10.3847/1538-4357/abcaa3`](http://doi.org/10.3847/1538-4357/abcaa3)

(ref: 2024NatAs...8..119V) van Dokkum, P., Brammer, G., Wang, B., Leja, J., & Conroy, C. 2024, Nature Astronomy, 8, 119, doi: [`10.1038/s41550-023-02103-9`](http://doi.org/10.1038/s41550-023-02103-9)

(ref: Vegetti2010) Vegetti, S., Koopmans, L. V. E., Bolton, A., Treu, T., & Gavazzi, R. 2010, MNRAS, 408, 1969, doi: [`10.1111/j.1365-2966.2010.16865.x`](http://doi.org/10.1111/j.1365-2966.2010.16865.x)

(ref: 2013Natur.495..344V) Vieira, J. D., Marrone, D. P., Chapman, S. C., et al. 2013, Nature, 495, 344, doi: [`10.1038/nature12001`](http://doi.org/10.1038/nature12001)

(ref: 2017ApJ...850...37W) Wang, W.-H., Lin, W.-C., Lim, C.-F., et al. 2017, ApJ, 850, 37, doi: [`10.3847/1538-4357/aa911b`](http://doi.org/10.3847/1538-4357/aa911b)

(ref: 2022MNRAS.510.2261W) Ward, B. A., Eales, S. A., Pons, E., et al. 2022, MNRAS, 510, 2261, doi: [`10.1093/mnras/stab3300`](http://doi.org/10.1093/mnras/stab3300)

(ref: Wardlow2013) Wardlow, J. L., Cooray, A., De Bernardis, F., et al. 2013a, ApJ, 762, 59, doi: [`10.1088/0004-637X/762/1/59`](http://doi.org/10.1088/0004-637X/762/1/59)

(ref: 2013ApJ...762...59W) —. 2013b, ApJ, 762, 59, doi: [`10.1088/0004-637X/762/1/59`](http://doi.org/10.1088/0004-637X/762/1/59)

(ref: 2022ApJS..258...11W) Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022, ApJS, 258, 11, doi: [`10.3847/1538-4365/ac3078`](http://doi.org/10.3847/1538-4365/ac3078)

(ref: 2016MNRAS.463..413W) Wilson, S., Hilton, M., Rooney, P. J., et al. 2016, MNRAS, 463, 413, doi: [`10.1093/mnras/stw1947`](http://doi.org/10.1093/mnras/stw1947)

(ref: Wong2020) Wong, K. C., Suyu, S. H., Chen, G. C. F., et al. 2020, MNRAS, 498, 1420, doi: [`10.1093/mnras/stz3094`](http://doi.org/10.1093/mnras/stz3094)

(ref: 2017MNRAS.464.3369Z) Zavala, J. A., Aretxaga, I., Geach, J. E., et al. 2017, MNRAS, 464, 3369, doi: [`10.1093/mnras/stw2630`](http://doi.org/10.1093/mnras/stw2630)

[^1]: https://github.com/mpi-astronomy/snowblind/

</paper>

Write the methods card for this paper.