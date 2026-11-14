# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...995...16Z\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2025ApJ...995...16Z",
 "title": "Measuring Dust Masses of Protoplanetary Disks in Serpens and L1641/L1647 with ALMA",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Zamudio-Ruvalcaba, Luisa F.",
 "n_authors": 4,
 "arxiv_id": "2511.20817",
 "doi": "10.3847/1538-4357/ae1588",
 "alma_projects_linked_by_archive": [
  "2019.1.00218.S",
  "2019.1.01813.S"
 ]
}
```

Paper text:
<paper>
# Measuring Dust Masses of Protoplanetary Disks in Serpens & L1641/L1647 with ALMA

## Abstract

Protoplanetary disks are an essential component of the planet-formation process. The amount of dust and gas in the disk constrains the number and size of planets that can form in a system. We analyze 178 T-Tauri stars, 18 in Serpens and 160 in L1641/L1647, and measure their disk dust masses using spectral energy distribution (SED) modeling and multiwavelength data, including 1.3 mm (ALMA band 6) fluxes from the literature. The disk masses calculated in this work are up to $\sim$2 times higher than those previously reported. We conclude that this is because disks may be partially optically thick at millimeter wavelengths while most calculations of the disk mass assume that the disk is optically thin at 1.3 mm. We calculate optical depths at 1.3 and 7 mm for a subset of the Serpens and L1641/L1647 disk sample and show that the vast majority of disks become optically thin at longer millimeter wavelengths; thus, observations at 7 mm (i.e., ALMA band 1) are vital to better characterize disk dust masses.

# Introduction

Stars form from collapsing molecular cloud cores (cite: 1993Goodman) and, due to angular momentum conservation, develop a disk of gas and dust (i.e., a protoplanetary disk). The total mass of the disk dictates the number of resulting planets and the timescale for the planet formation process (cite: 2020Tychoniec). A common assumption is that protoplanetary disks have a gas-to-dust ratio of 100 (cite: 1987Shu; 2010Birnstiel). Although dust makes up only a small fraction of the disk’s mass, it dominates the disk’s opacity and tends to be more easily observed than gas. By studying the thermal emission from dust grains, we can infer the dust mass and gain insight into the conditions under which planets form.

Disk dust masses can be calculated with different methods (cite: 2018BerginWilliams), but a common method is using millimeter-wavelength flux measurements. Some of the typical values measured for disk dust masses are $\sim0.2 - 0.4\ M_{\oplus}$, which are insufficient to support ongoing planet formation (cite: 2016Ansdell; 2016Pascucci; 2018Manara) since it implies a planet formation efficiency rate close to 100$\%$ (cite: 2021Mulders). This is called the “missing mass” problem (also known as the “mass budget” problem), and different solutions have been proposed. Planet formation may start much earlier than previously assumed, even during the first Myr of the disk lifetime (cite: 2014NajitaKenyon; 2018Manara; 2021Mulders), which is supported by the detection of disk substructures (cite: 2015ALMApartnership; 2018Andrews; 2020SeguraCox) and the presence of the “missing mass” problem in young regions such as Taurus (1-2 Myr). Alternatively, disk dust masses may be underestimated when using the millimeter flux method, which assumes that the disk is optically thin, whereas disks are unlikely to be optically thin throughout all millimeter wavelengths (cite: 2019BalleringEisner; 2020Ribas; 2023Xin; 2023Rilinger). Significant mass may also be “hidden” in optically thick dust traps (cite: 2024Savvidou). Lastly, protoplanetary disks may replenish their material by accreting additional material from their surroundings (cite: 2008ThroopBally; 2017Kuffmeier; 2021Ginski).

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Object | Parallax | SpT | $T_{eff}$ | $A_v$ | $L_*$ | $R_*$ | $M_*$ | Reference |
| 2MASS | mas |  | K |  | $L_{\odot}$ | $R_{\odot}$ | $M_{\odot}$ |  |
| J18264598-0344306 | $2.21 \pm 0.21$ | M1 | $3730 \pm 100$ | $5.54 \pm 0.13$ | $0.04 \pm 0.03$ | $0.50 \pm 0.23$ | $0.50 \pm 0.28$ | 4 |
| J18264973-0355596 | $2.26 \pm 0.16$ | K4 | $4800 \pm 100$ | $8.53 \pm 0.03$ | $0.20 \pm 0.17$ | $0.7 \pm 0.3$ | $0.7 \pm 0.4$ | 4 |
| J18273709-0349385 | $2.63 \pm 0.11$ | K7 | $4234 \pm 100$ | $9.972 \pm 0.028$ | $0.10 \pm 0.08$ | $0.63 \pm 0.29$ | $0.6 \pm 0.4$ | 4 |
| J18274426-0329519 | $2.48 \pm 0.17$ | M0 | $3890 \pm 100$ | $7.85 \pm 0.10$ | $0.07 \pm 0.06$ | $0.59 \pm 0.27$ | $0.6 \pm 0.3$ | 4 |
| J18274445-0356016 | $2.29 \pm 0.07$ | F9.5 | $6008 \pm 100$ | $7.890 \pm 0.019$ | $4.21 \pm 0.22$ | $1.89 \pm 0.05$ | $1.22 \pm 0.04$ | 4 |
| J18275383-0002335 | $2.37 \pm 0.04$ | K2 | $4900 \pm 500$ | $1.000 \pm 0.019$ | $2.0 \pm 1.8$ | $2.0 \pm 1.0$ | $1.6 \pm 0.4$ | 1 |
| J18281519-0001408 | $2.58 \pm 0.22$ | M8 | $2640 \pm 330$ | $2.00 \pm 0.04$ | $0.11 \pm 0.07$ | $1.6 \pm 0.6$ | $0.12 \pm 0.12$ | 2 |
| J18290088+0029312 | $2.37 \pm 0.04$ | K7 | $4060 \pm 220$ | $5.00 \pm 0.09$ | $1.0 \pm 0.9$ | $2.0 \pm 0.9$ | $1.14 \pm 0.20$ | 2 |
| J18290394+0020212 | $2.322 \pm 0.027$ | K5 | $4400 \pm 300$ | $7.00 \pm 0.13$ | $5.0 \pm 3.0$ | $4.0 \pm 1.5$ | $1.6 \pm 0.4$ | 2 |
| J18290935-0203503 | $2.02 \pm 0.16$ | K6 | $4360 \pm 100$ | $9.987 \pm 0.020$ | $0.14 \pm 0.11$ | $0.7 \pm 0.3$ | $0.7 \pm 0.4$ | 4 |
| J18291969+0018030 | $2.23 \pm 0.21$ | M0 | $3850 \pm 100$ | $6.00 \pm 0.11$ | $0.6 \pm 0.4$ | $1.7 \pm 0.6$ | $0.90 \pm 0.10$ | 2 |
| J18293084+0101071 | $2.37 \pm 0.06$ | F7 | $6290 \pm 120$ | $6.17 \pm 0.05$ | $2.5 \pm 2.0$ | $1.3 \pm 0.6$ | $1.2 \pm 0.7$ | 4 |
| J18294147+0107378 | $2.33 \pm 0.04$ | K5 | $4400 \pm 300$ | $3.30 \pm 0.06$ | $0.9 \pm 0.4$ | $1.6 \pm 0.4$ | $0.7 \pm 0.3$ | 3 |
| J18295360+0117017 | $1.99 \pm 0.10$ | K6 | $4200 \pm 200$ | $4.60 \pm 0.08$ | $0.52 \pm 0.22$ | $1.4 \pm 0.3$ | $0.7 \pm 0.3$ | 3 |
| J18295820+0115216 | $2.43 \pm 0.14$ | K5.5 | $4300 \pm 200$ | $5.50 \pm 0.10$ | $0.31 \pm 0.12$ | $1.02 \pm 0.20$ | $0.8 \pm 0.4$ | 3 |
| J18300545+0101022 | $2.39 \pm 0.22$ | M3 | $3440 \pm 100$ | $4.41 \pm 0.09$ | $0.016 \pm 0.013$ | $0.36 \pm 0.17$ | $0.37 \pm 0.20$ | 4 |
| J18300610+0106170 | $2.37 \pm 0.08$ | M0 | $3800 \pm 210$ | $3.70 \pm 0.07$ | $0.51 \pm 0.21$ | $1.6 \pm 0.3$ | $0.42 \pm 0.20$ | 3 |
| J18302240+0120439 | $2.33 \pm 0.05$ | M1 | $3630 \pm 130$ | $1.80 \pm 0.03$ | $0.26 \pm 0.12$ | $1.3 \pm 0.3$ | $0.41 \pm 0.19$ | 3 |
| J18314416-0216182 | $1.99 \pm 0.10$ | F5 | $6650 \pm 100$ | $9.630 \pm 0.027$ | $3.6 \pm 0.9$ | $1.47 \pm 0.11$ | $1.33 \pm 0.08$ | 4 |
| J18321676-0223167 | $1.91 \pm 0.16$ | K6 | $4409 \pm 100$ | $7.27 \pm 0.07$ | $0.14 \pm 0.11$ | $0.7 \pm 0.3$ | $0.7 \pm 0.4$ | 4 |
| J18321707-0229531 | $2.12 \pm 0.22$ | K3 | $4850 \pm 100$ | $9.13 \pm 0.05$ | $0.28 \pm 0.23$ | $0.8 \pm 0.4$ | $0.8 \pm 0.4$ | 4 |
| J18370677+0011479 | $1.89 \pm 0.21$ | M1 | $3690 \pm 100$ | $5.30 \pm 0.06$ | $0.04 \pm 0.03$ | $0.50 \pm 0.23$ | $0.50 \pm 0.28$ | 4 |
| J18382267+0023093 | $2.22 \pm 0.20$ | M4.5 | $3187 \pm 100$ | $2.06 \pm 0.24$ | $0.004 \pm 0.003$ | $0.13 \pm 0.06$ | $0.18 \pm 0.1$ | 4 |

: Stellar parameters of the Serpens sample.

Table notes: $^{*}$ All parallax values are from *Gaia* DR3. $R_*$ is calculated here using literature values. Additional parameters are obtained from various sources as follows: (1,2,3) spectral type, $T_{eff}$, $A_v$, $L_*$, and $M_*$ are compiled from (cite: 2009Oliveira), (cite: 2013Oliveira), and (cite: 2015Erickson), respectively; (4) spectral type is from (cite: 2013PecautMamajek) using the $T_{eff}$ available in the literature; $T_{eff}$ and $A_v$ are gathered from the derived values from GSP-Phot using BP/RP spectra (cite: GaiaDR3). The General Stellar Parametrizer for Photometry (GSP-Phot) derives stellar parameters ($T_{eff}$, $\log g$, $A_G$, distance, etc.) from BP/RP spectra down to G=19, assuming all sources are stars. It infers these parameters using Gaia’s low-resolution BP/RP spectra, astrometry, and photometry. We refer the reader to consult (cite: GaiaDR3) and (cite: 2023Andrae) for further details on the GSP-Phot methodology. $L_*$ and $M_*$ are estimated here using the MassAge code following (cite: 2023Hernandez). In short, $L_*$ is calculated using extinction-corrected J magnitudes (cite: 2020LuhmanEsplin), bolometric corrections from (cite: 2013PecautMamajek), and distances derived from parallaxes (*Gaia* DR3). $M_*$ is derived using the MIST (cite: 2016Dotter) evolutionary models.

Here, we use SED modeling to measure dust masses for a sample of disks in the Serpens and L1641/L1647 star-forming regions. We focus on disks around T-Tauri stars (TTS) which are pre-main sequence, low-mass (cite: 1945Joy; 1962Herbig), cool (late spectral types K-M) stars exhibiting photometric variability as well as characteristic emission and absorption lines (e.g., H$\alpha$ and Li 6707 Å, respectively). We use ALMA 1.3 mm continuum observations from the Serpens star-forming region (cite: 2022Anderson) and the Orion A cloud in the L1641 and L1647 regions (cite: 2022vanTerwisga). We incorporate broad-band photometry and low-resolution *Spitzer* Infrared Spectrograph (IRS) spectra from CASSIS (cite: 2004IRS). The SED model fitting adopts the technique developed by (cite: 2020Ribas), which employs an Artificial Neural Network (ANN) trained with the D’Alessio Irradiated Accretion Disk models (cite: 1998Dalessio; 1999Dalessio; 2001Dalessio; 2005Dalessio; 2006Dalessio). This paper’s structure is as follows: we describe the sample selection in Section [2](#sec:sample), we present analysis and results from the SED modeling in Section [3](#sec:analysis and results), we discuss our results in Section [4](#sec:discussion), and finally we provide conclusions in Section [5](#sec:summary).

# Sample selection

The sample used in this work comprises TTS with disks in the Serpens, L1641, and L1647 regions. (Sub)millimeter observations are necessary to constrain the disk’s dust mass, so we compiled our sample using (sub)millimeter surveys of these regions. We selected our Serpens sample from (cite: 2022Anderson), a continuum and $^{12}CO\ (J=2-1)$ line survey spread over an area of $\sim$10 square degrees in Serpens which observed 320 objects studied by the *Spitzer* From Molecular Cores to Planet-Forming Disks C2D Overview (cite: SpitzerEvans; 2009Evans) and the Gould Belt Survey (cite: 2015Dunham). The L1641 and L1647 sample is obtained from the Survey of Orion Disks with ALMA (cite: 2022vanTerwisga), which observed 873 protoplanetary disks identified by *Spitzer* (cite: 2009Evans; 2015Dunham). Both (cite: 2022Anderson) $\&$ (cite: 2022vanTerwisga) use the ALMA 1.3 mm band (centered at 241.1 GHz and 225 GHz, respectively).

The original sample of 320 Serpens sources (cite: 2022Anderson) comes down to 23 objects, and the 873 L1641/L1647 sources (cite: 2022vanTerwisga) to 188 objects after considering several criteria. They must belong to the Serpens or L1641/L1647 star-forming regions and be identified as Class II YSOs. Each source must have been detected by ALMA and have at least two 2MASS measurements, two mid-infrared (*WISE* or c2d) measurements, and one (sub)millimeter (ALMA) measurement. Sources known to be transitional disks (TDs), exhibit flat spectra, or belong to binary or multiple systems were excluded. Additionally, the sources must not have a (sub)mm measurement within 2”.5 of another (sub)mm detection of at least 3$\sigma$. Only sources with ALMA detections of at least 3$\sigma$ were included. To ensure reliable astrometric data (e.g., parallax), the selected sources must display good *Gaia* astrometric quality. Finally, all sources must be classified as T Tauri stars and have stellar parameters available in the literature. The $T_{eff}$, $R_{*}$, $M_{*}$, and parallaxes listed in Tables [1](#table:parameters_serpens) and [\[table:parameters_SODA\]](#table:parameters_SODA) are used in the SED fitting as described in Section [3.2.1](#subsec:sed modeling ANN) and [3.2.2](#subsubsec:sed modeling MCMC), and the rest of the parameters are listed for completeness. We note that for $T_{eff}$, we adopted an uncertainty of 100 K for those objects with reported uncertainties below 100 K, following (cite: 2020Ribas).

We refer the reader to Appendix [6](#sec:appendixA) for a more detailed review of the selection criteria. This results in an overall sample of 211 objects.

# Analysis and Results

Below, we compile the SEDs for the 211 sources in Serpens, L1641, and L1647 selected in Section [2](#sec:sample). A subset of 41 sources from L1641 were modeled in (cite: 2023Rilinger) and we incorporate their model results here. We provide an overview of the SED modeling methodology using the ANN developed by (cite: 2020Ribas), which applies a Bayesian approach and is trained with DIAD models. We end with the resulting model fits and further reduce our sample to 178 sources (18 from Serpens and 160 from L1641/L1647) based on the quality of the fits.

## SEDs

We compile the SEDs using multiwavelength photometry gathered for each object from the Vizier catalog access tool (cite: 2000Vizier), using a search radius of 2”. Table [\[table:photometry\]](#table:photometry) lists all photometry sources used. We also include low-resolution *Spitzer* IRS spectra for each object, if available, which were obtained from the Combined Atlas of Sources with *Spitzer* IRS Spectra (cite: 2011CASSIS).

## SED modeling

To fit our objects’ SEDs, we use a model that relies on the ANN developed by (cite: 2020Ribas), and trained on the D’Alessio Irradiated Accretion Disk models (cite: 1998Dalessio; 1999Dalessio; 2001Dalessio; 2005Dalessio; 2006Dalessio). We follow a Bayesian approach as detailed in (cite: 2020Ribas) and (cite: 2023Xin) to estimate our sample of disks’ posterior probability density functions based on their respective SEDs.

### The model

The work by (cite: 2020Ribas) presents a novel approach to fit samples of protoplanetary disks, combining physically motivated models with a neural network to speed the process of model fitting; the ANN takes a few milliseconds to evaluate the SEDs, compared to the 1-2 hours that the DIAD models require, which, as previously discussed, makes the model fitting considerably time-consuming for large samples. We direct the reader to Section 4 and Figure 2 of (cite: 2020Ribas) for a detailed description of the model and a summary of the steps, which are also summarized below.

The ANN comprises two artificial neural networks: ANN$_{SED}$ for SED estimates and ANN$_{diskmass}$ for disk mass estimates. The ANN provides SED estimates based on input parameters. Each of the models computed in the fitting procedure goes through the following steps:

1.  Stellar age and $M_*$ are taken as free parameters of the model, and for each pair, $T_*$ and $R_*$ are estimated from the MESA Isochrones and Stellar Tracks (cite: 2011Paxton; 2013Paxton; 2015Paxton; 2016Dotter; 2016Choi). This process ensures that our model explores combinations of stellar age, $M_*$, $R_*$, and $T_*$ that are physically realistic, which is required because these parameters are used to evaluate the SEDs. Likewise, $L_*$ is not a free parameter in the model but is derived from MIST. We point the reader to Section [3.2.2](#subsubsec:sed modeling MCMC) for more details about how literature information about the stellar parameters is used in the modeling.

2.  The ANN uses $M_*$, $T_*$, and $R_*$ as well as the following disk and dust parameters:

    - Mass accretion rate $\dot{M}$

    - Disk viscosity $\alpha$ (cite: 1973Shakura).

    - Dust settling $\epsilon$ (adimensional)

    - Maximum grain sizes in the disk atmosphere $a_{max,upper}$ and midplane $a_{max,midplane}$

    - Disk size $R_{disk}$

    - Inclination $i$

    - Dust sublimation temperature $T_{wall}$

    - Scaling factor of the inner wall $z_{wall}$

    Consequently, the ANN generates the corresponding SED for a reference distance of 100 pc in the absence of extinction to the source. We refer the reader to the DIAD papers (cite: 1998Dalessio; 1999Dalessio; 2001Dalessio; 2005Dalessio; 2006Dalessio) for further details on these disk and dust parameters.

3.  The SED output is scaled to the source’s distance (based on the corresponding parallax, which is another free parameter in our model) and reddened by $A_v$, applying the (cite: 2009McClure) extinction law (cite: 2017Ribas). Here, $A_v$ denotes the interstellar extinction and does not include the self-extinction contributed by the disk, which is already incorporated in DIAD.

Some caveats need to be taken into account for this methodology. As discussed in Section [2](#sec:sample), the objects that make up our sample must comply with specific selection criteria. Some physical properties remain fixed (e.g. dust composition, gas-to-dust ratio) or not considered in the modeling (i.e. the presence of substructures in the disk). Refer to (cite: 2020Ribas) for an in-depth discussion of the caveats of this methodology. Most importantly, this sample is only made up of sources detected in the (sub)mm range. This would bias the analysis towards massive disks and underrepresented low-mass disks, which are less luminous, smaller in radius, and thus harder to detect.

### Markov Chain Monte Carlo (MCMC)

We implement a Bayesian analysis framework as a Markov Chain Monte Carlo (MCMC) fitting process to probe the large parameter space and estimate posterior distributions for the model parameters. Following (cite: 2023Rilinger), we adopted the likelihood functions from (cite: 2020Ribas) and (cite: 2023Xin), as well as the `ptemcee` (cite: 2016Vousden) parallel-tempering version of the `emcee` MCMC code (cite: 2013Foreman-Mackey). Our photometry points were divided into two groups:

- critical: includes 2MASS and ALMA photometry (cite: 2022Anderson)

- general: includes all other photometry

The division allows us to provide further weight to the 2MASS and ALMA photometry, which are vital for accurately scaling the stellar photosphere and calculating the disk mass, respectively. Four standard Gaussian likelihood functions are used, each for the critical photometry data, the spectral data (i.e., IRS Spectra), the $T_*$, and the $R_*$. To account for possible systematic uncertainties that may be present in the data from different instruments, (cite: 2023Xin) scaled all of the uncertainties in the flux densities according to the free parameter, *f*. Some photometric points may differ significantly from the rest of the SEDs and are problematic in the fitting process. (cite: 2023Xin) employed a mixture model approach, following the methodology described by (cite: 2010Hogg). This approach was applied to the general photometry data, enabling the overall likelihood to incorporate information from both the photometric and spectral data. We note that Gaussian priors are used for the $M_{*}$ and parallaxes listed in Tables [1](#table:parameters_serpens) and [\[table:parameters_SODA\]](#table:parameters_SODA) to represent pre-existing information on these parameters, using their values as the centers and their uncertainties as the standard deviations, while flat priors are used when literature values are absent (e.g., inclination). We refer the reader to consult (cite: 2023Xin) and (cite: 2023Rilinger) for more details.

Hence, the model has 13 free parameters: Stellar age, $M_*$, DIAD parameters (i.e. $\dot{M}$, $\alpha$, $\epsilon$, $a_{max,upper}$, $a_{max,midplane}$, $R_{disk}$, $i$, $T_{wall}$, and $z_{wall}$), parallax, and $A_v$ of the source, all of them determined using the MCMC fitting process. Finally, since we are compiling the SEDs from multiple catalogs, it is likely that some of the data points may be affected by undetected issues (i.e., source blending, saturation, artifacts). In order to reduce the impact of these outliers on the modeling, we include four additional parameters to mitigate the influence of such uncertainties during the fitting process: three of these account for possible outlier photometric points, and one, the *f* parameter, accounts for potential systematic uncertainties inherent in the data acquired from different instruments. This results in a total of 17 free parameters, which are varied during the fitting to compute posterior probability distributions.

For an in-depth exploration and discussion of the MCMC process on which the ANN operates, we refer to the following works by (cite: 2020Ribas), (cite: 2023Rilinger), and (cite: 2023Xin).

## Model results

Figures [1](#fig:SED_models_serpens) $\&$ [2](#fig: SED models_SODA) display the modeling results for Serpens and L1641/L1647, respectively. We identified successful and unsuccessful model fits for both samples; see (cite: 2023Rilinger) for examples and further discussion on unsuccessful model fits.

![](FIGURE1.pdf)

![](FIGURE2.pdf)

For the Serpens sample, six sources have unsuccessful fits, which may be due to incorrect stellar parameters, unknown substructures, or the potential presence of companions, as well as processes not taken into account by the methodology of (cite: 2020Ribas). These include the following sources: 2MASS J18273709-0349385 (model does not fit the *Spitzer* photometry), 2MASS J18290394+0020212 (exhibits variability between the infrared IRS spectra and *Spitzer* photometry), 2MASS J18290935-0203503 (model does not fit infrared photometry, *Spitzer* and *WISE*, as well as the millimeter photometry), 2MASS J18370677+0011479 (the model does not fit the 2MASS photometry and infrared structure of the SED), 2MASS J18382267+0023093 (the model does not fit the infrared structure of the SED), 2MASS J18373580+0019053 (the photometry has very large scatter and is difficult to fit). Thus, the Serpens sample consists of 18 successfully modeled disks.

For the L1641/L1647 region, 28 sources were discarded based on failed fits. We arrive at a sample of 160 successfully modeled sources in L1641/L1647.

Results from the model fits for individual sources and ensemble distributions are shown in Figures [3](#fig: individual_ensemble_serpens_distributions) and [4](#fig: individual_ensemble_SODA_distributions) for Serpens and L1641/L1647, respectively. Similarly, Table [2](#table: ANN_posteriors_Serpens_stellar) display the median values and corresponding errors (calculated from the 16th and 84th percentiles of the distribution) for the posterior distributions of stellar and disk parameters, respectively, obtained from the model fitting for Serpens. Meanwhile, Table [3](#tab: ANN_posteriors_SODA_stellar) lists those for L1641/L1647. An assessment of the consistency between the stellar parameters ($M_*$, $R_*$, parallax, and $T_{\mathrm{eff}}$; as listed in Tables [1](#table:parameters_serpens) and [\[table:parameters_SODA\]](#table:parameters_SODA), and their respective posterior distributions in Tables [2](#table: ANN_posteriors_Serpens_stellar) and [3](#tab: ANN_posteriors_SODA_stellar)) is conducted to validate the robustness of the ANN fitting methodology. We refer the reader to Appendix [7](#sec:appendixB) for a more detailed review of this validation procedure. The corresponding corner plots generated from the MCMC process for all 178 disks are hosted within the designated [Zenodo](https://zenodo.org/records/17203297?token=eyJhbGciOiJIUzUxMiJ9.eyJpZCI6IjAwMTFmM2YzLTgxZDgtNGVhMy05NzUwLTA5MGZhZWZjNWQ3MCIsImRhdGEiOnt9LCJyYW5kb20iOiJlMmI1YTRlMGJiYzQ0NGExOGY5YTUwZWM4M2ZiYmQ1ZCJ9.mjCth0bpYmepMixe0paJy4MM67Z2mXDiXHJzJoYzOFLeTxjK16C2yLh80Mfe9qsVxD8yjVOy2Ann9UHTfLI73w) repository.

Figures [3](#fig: individual_ensemble_serpens_distributions) & [4](#fig: individual_ensemble_SODA_distributions) show some similarities in trends of the physical parameters. Disk mass depends on the disk viscosity ($\alpha$) and the mass accretion rate ($\dot{M}$), as both parameters determine the surface density profile of the disk $\Sigma \propto {\dot{M}}/{\alpha}$. These parameters are relatively well-constrained for both samples compared to the other parameters. The $R_{disk}$ and $a_{max,midplane}$ (i.e., the maximum grain size in the midplane) are not well constrained, consistent with the results of (cite: 2020Ribas) and (cite: 2023Xin), which use the same method. The $\epsilon$ parameter, which measures the dust settling in the disk, shows a preference towards lower values in both samples (i.e., $\epsilon < 10^{-2}$), indicating that the studied disk populations have already undergone significant settling. This agrees with previous works where high degrees of dust settling are observed in L1641/L1647 (cite: 2018Grant; 2019Grossschedl) and Serpens (cite: 2023Liu). For $a_{max,upper}$, the maximum grain size in the upper layers of the disk, some objects in both samples are well-constrained while others are not. This may be due to the availability of IRS spectra for each object, as the size of the upper layer dust grains is determined from mid-IR, in particular from the shape of the silicate feature at 10-20 $\mu$m. This reinforces the importance of having mid-IR spectra to better constrain dust population characteristics in the disk. Further discussion of a similar analysis of these posterior distributions for different populations can be found in (cite: 2020Ribas) for Taurus-Auriga and in (cite: 2023Xin) for Lupus.

![](FIGURE3a.pdf)

![](FIGURE3b.pdf)

![](FIGURE4a.pdf)

![](FIGURE4b.pdf)

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Object | $T_{eff}$ | Radius | Mass | Parallax | $log_{10}(\dot{M})$ | $log_{10}(\alpha)$ | $log_{10}(\epsilon)$ | $R_{disk}$ | $\mathbf{a_{\max,\;upper}}$ | $\mathbf{a_{\max,\;midplane}}$ | $T_{wall}$ | Inclination | $M_{dust}$ |  |
| 2MASS | K | $R_{\odot}$ | $M_{\odot}$ | mas | $M_{\odot}/yr$ |  |  | au | $\mu$m | mm | K | deg | $M_{\oplus}$ |  |
| J18264598-0344306 | $3720_{-90}^{+80}$ | $1.02_{-0.09}^{+0.14}$ | $0.54_{-0.07}^{+0.08}$ | $2.3_{-0.2}^{+0.2}$ | $-7.50_{-0.12}^{+0.13}$ | $-2.1_{-0.9}^{+0.3}$ | $-2.4_{-0.9}^{+1.3}$ | $100_{-60}^{+120}$ | $0.86_{-0.09}^{+0.21}$ | $1000_{-810}^{+4000}$ | $1400_{-40}^{+50}$ | $59_{-12}^{+6}$ | $200_{-90}^{+700}$ |  |
| J18264973-0355596 | $4800_{-100}^{+100}$ | $1.93_{-0.16}^{+0.17}$ | $1.37_{-0.09}^{+0.08}$ | $2.48_{-0.14}^{+0.14}$ | $-8.7_{-0.7}^{+0.5}$ | $-3.1_{-0.6}^{+0.6}$ | $-2.9_{-0.5}^{+0.6}$ | $150_{-93}^{+100}$ | $0.51_{-0.14}^{+0.22}$ | $1000_{-700}^{+3000}$ | $1420_{-50}^{+50}$ | $20_{-10}^{+30}$ | $70_{-20}^{+50}$ |  |
| J18274426-0329519 | $3880_{-90}^{+90}$ | $1.25_{-0.16}^{+0.21}$ | $0.66_{-0.08}^{+0.08}$ | $2.58_{-0.17}^{+0.17}$ | $-7.50_{-0.13}^{+0.12}$ | $-2.3_{-0.5}^{+0.2}$ | $-3.3_{-0.4}^{+0.5}$ | $169_{-100}^{+92}$ | $0.62_{-0.06}^{+0.07}$ | $1000_{-800}^{+3000}$ | $1440_{-40}^{+40}$ | $59_{-8}^{+6}$ | $300_{-90}^{+200}$ |  |
| J18274445-0356016 | $5860_{-50}^{+60}$ | $1.85_{-0.04}^{+0.04}$ | $1.450_{-0.012}^{+0.013}$ | $2.31_{-0.07}^{+0.07}$ | $-9.1_{-0.6}^{+0.7}$ | $-2.6_{-0.6}^{+0.7}$ | $-3.6_{-0.3}^{+0.6}$ | $180_{-100}^{+80}$ | $0.76_{-0.18}^{+0.50}$ | $1000_{-500}^{+3000}$ | $1420_{-50}^{+50}$ | $22_{-9}^{+21}$ | $11_{-4}^{+8}$ |  |
| J18275383-0002335 | $4400_{-300}^{+300}$ | $1.57_{-0.12}^{+0.15}$ | $1.03_{-0.27}^{+0.16}$ | $2.36_{-0.04}^{+0.04}$ | $-9.6_{-0.3}^{+0.5}$ | $-2.9_{-0.4}^{+0.6}$ | $-3.7_{-0.2}^{+0.3}$ | $180_{-100}^{+90}$ | $0.36_{-0.07}^{+0.10}$ | $1000_{-1100}^{+4000}$ | $1400_{-50}^{+50}$ | $68_{-4}^{+1}$ | $12_{-6}^{+10}$ |  |

: Posteriors for Serpens stellar and disk parameters

Table notes: This table is published in its entirety in the machine-readable format. A portion is shown here for guidance regarding its form and content.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Object | $T_{eff}$ | Radius | Mass | Parallax | $log_{10}(\dot{M})$ | $log_{10}(\alpha)$ | $log_{10}(\epsilon)$ | $R_{disk}$ | $\mathbf{a_{\max,\;upper}}$ | $\mathbf{a_{\max,\;midplane}}$ | $T_{wall}$ | Inclination | $M_{dust}$ |  |
| 2MASS | K | $R_{\odot}$ | $M_{\odot}$ | mas | $M_{\odot}/yr$ |  |  | au | $\mu$m | mm | K | deg | $M_{\oplus}$ |  |
| J05334160-0606074 | $3360_{-90}^{+90}$ | $0.96_{-0.10}^{+0.10}$ | $0.29_{-0.06}^{+0.06}$ | $2.43_{-0.14}^{+0.15}$ | $-8.9_{-0.6}^{+0.4}$ | $-2.4_{-0.7}^{+0.5}$ | $-1.7_{-0.8}^{+0.9}$ | $140_{-100}^{+110}$ | $2.7_{-2.4}^{+5.0}$ | $1100_{-900}^{+4000}$ | $1390_{-50}^{+50}$ | $50_{-23}^{+10}$ | $8_{-3}^{+6}$ |  |
| J05340108-0602268 | $3940_{-40}^{+40}$ | $1.47_{-0.09}^{+0.09}$ | $0.67_{-0.03}^{+0.03}$ | $2.601_{-0.018}^{+0.019}$ | $-8.12_{-0.10}^{+0.11}$ | $-1.14_{-0.18}^{+0.10}$ | $-3.7_{-0.2}^{+0.3}$ | $60_{-42}^{+120}$ | $3.9_{-2.4}^{+4.0}$ | $800_{-700}^{+4300}$ | $1440_{-40}^{+40}$ | $10_{-5}^{+10}$ | $2_{-1}^{+2}$ |  |
| J05340495-0623469 | $3440_{-50}^{+50}$ | $1.22_{-0.13}^{+0.11}$ | $0.33_{-0.04}^{+0.04}$ | $2.61_{-0.05}^{+0.05}$ | $-9.75_{-0.19}^{+0.40}$ | $-2.5_{-0.5}^{+1.0}$ | $-3.7_{-0.2}^{+0.5}$ | $160_{-90}^{+90}$ | $2.1_{-1.7}^{+5.0}$ | $1000_{-600}^{+3000}$ | $1420_{-50}^{+50}$ | $65_{-12}^{+3}$ | $3_{-2}^{+5}$ |  |
| J05342043-0631150 | $3100_{-100}^{+100}$ | $0.89_{-0.12}^{+0.12}$ | $0.15_{-0.04}^{+0.05}$ | $2.43_{-0.15}^{+0.14}$ | $-9.7_{-0.2}^{+0.4}$ | $-3.1_{-0.3}^{+0.4}$ | $-3.7_{-0.3}^{+0.5}$ | $170_{-100}^{+90}$ | $3.2_{-2.7}^{+4.0}$ | $1000_{-700}^{+3000}$ | $1420_{-50}^{+50}$ | $57_{-20}^{+10}$ | $9_{-5}^{+11}$ |  |
| J05343360-0611194 | $3020_{-30}^{+50}$ | $1.04_{-0.10}^{+0.08}$ | $0.122_{-0.011}^{+0.014}$ | $2.58_{-0.07}^{+0.07}$ | $-9.3_{-0.4}^{+0.7}$ | $-2.6_{-0.5}^{+0.6}$ | $-3.2_{-0.5}^{+0.7}$ | $160_{-100}^{+100}$ | $0.7_{-0.4}^{+4.0}$ | $1000_{-800}^{+3000}$ | $1400_{-40}^{+50}$ | $10_{-9}^{+30}$ | $5_{-2}^{+4}$ |  |

: Posteriors for L1641/L1647 stellar and disk parameters

Table notes: This table is published in its entirety in the machine-readable format. A portion is shown here for guidance regarding its form and content.

# Discussion

Here, we discuss the importance of considering optical depth when calculating disk dust masses, particularly for massive disks, which tend to be more affected. We follow by comparing our dust mass measurements (based on SED modeling) with those from the literature (cite: 2022Anderson; 2022vanTerwisga), and show that our values become more discrepant with the values from the literature as we move toward more massive disks. Next, we compare Serpens and L1641/L1647 to 10 other star-forming regions with ages less than 10 Myr and confirm that both samples follow the observed trends for disk dust mass in other regions. We conclude by discussing how our dust masses are greater than those calculated from mm fluxes, but this does not fully solve the “missing mass” problem as our values are still lower when compared to exoplanet systems.

## The importance of optical depth when deriving disk masses

We compare our sample’s model-derived disk dust masses with those found in the literature in Figure [5](#fig: comparison with lit). The literature values in Figure [5](#fig: comparison with lit) are from (cite: 2022Anderson) & (cite: 2022vanTerwisga), and are recalculated using *Gaia* DR3 parallaxes and using the (cite: 1983Hildebrand) equation:

$$\begin{equation}
M_d = \frac{F_{\nu}d^2}{\kappa_{\nu}B_{\nu}(T_d)}
\label{eq: Hildebrand}
\end{equation}$$

where $M_d$ is the dust mass in the disk; $F_{\nu}$ is the millimeter flux density at the observing frequency, here 1.3 mm (241 GHz); $\kappa_{\nu}$ is the dust opacity coefficient at the observing frequency, and following (cite: 2022Anderson), we adopt $\kappa_{\nu} = (\nu/100$ GHz) (cite: 1990Bekwith) resulting in $2.41\ cm^2g^{-1}$ while assuming $\beta = 1$; $B_{\nu}(T_d)$ is the Planck function evaluated at the dust temperature $T_d$, which is typically assumed to be constant with a value of $T_d = 20\ K$ for a Class II object (cite: 2005AndrewsWilliams; 2016Ansdell; 2017Ansdell; 2018RuizRodriguez; 2019Cazzoletti; 2019Williams; 2022Anderson); $d$ is the distance calculated from *Gaia* DR3 parallaxes. The recalculated disk dust masses for Serpens and L1641/L1647 are listed in Tables [4](#tab: recalculated dust masses serpens) $\&$ [5](#tab: recalculated dust masses SODA), respectively.

|                   |                |
|:------------------|:--------------:|
| Object            |   $M_{dust}$   |
| 2MASS             |  $M_{\oplus}$  |
| J18264598-0344306 |  $61 \pm 12$   |
| J18264973-0355596 |   $66 \pm 9$   |
| J18274426-0329519 |  $90 \pm 12$   |
| J18274445-0356016 | $10.8 \pm 1.3$ |
| J18275383-0002335 | $6.3 \pm 1.4$  |
| J18281519-0001408 |   $22 \pm 4$   |
| J18290088+0029312 |  $100 \pm 10$  |
| J18291969+0018030 |   $27 \pm 6$   |
| J18293084+0101071 | $4.1 \pm 1.7$  |
| J18294147+0107378 |   $50 \pm 6$   |
| J18295360+0117017 |   $14 \pm 4$   |
| J18295820+0115216 |  $130 \pm 20$  |
| J18300545+0101022 | $10.3 \pm 2.9$ |
| J18300610+0106170 |   $20 \pm 3$   |
| J18302240+0120439 |   $17 \pm 3$   |
| J18314416-0216182 | $9.3 \pm 2.2$  |
| J18321676-0223167 | $15.9 \pm 2.9$ |
| J18321707-0229531 |   $13 \pm 4$   |

: Recalculated literature dust masses for the Serpens sample.

|                   |                |
|:------------------|:--------------:|
| Object            |   $M_{dust}$   |
| 2MASS             |  $M_{\oplus}$  |
| J05334160-0606074 | $4.1 \pm 0.4$  |
| J05340108-0602268 | $1.9 \pm 0.4$  |
| J05340495-0623469 | $1.5 \pm 0.4$  |
| J05341574-0636046 | $42.0 \pm 2.0$ |
| J05342043-0631150 | $1.8 \pm 0.4$  |
| J05343360-0611194 | $2.0 \pm 0.4$  |
| J05343614-0605346 | $25.2 \pm 0.4$ |
| J05344765-0619401 | $7.6 \pm 0.3$  |
| J05344833-0630268 | $20.1 \pm 0.4$ |
| J05345404-0623507 | $82.1 \pm 0.4$ |

: Recalculated literature dust masses for L1641/L1647.

Table notes: $^{*}$ This table is published in its entirety in the machine-readable format. A portion is shown here for guidance regarding its form and content.

![](FIGURE5.pdf)

![](FIGURE6.pdf)

In Figure [5](#fig: comparison with lit), the calculated disk dust masses from the literature are consistently lower than in this work, especially when assuming a constant temperature profile. We find that, on average, our masses are a factor of about 2.0 higher for both Serpens and L1641/L1647. In most cases, the discrepancy is even higher for the higher-mass objects.

The discrepancy between disk dust masses when using the (cite: 1983Hildebrand) equation versus SED modeling has been reported in other works. (cite: 2019BalleringEisner) find that the masses derived with their SED modeling are $\sim1 - 5$ higher. The same is seen in (cite: 2020Ribas), where the estimated $M_{dust}$ from SED modeling is $\sim3$ higher than that reported in (cite: 2013Andrews). Other works such as (cite: 2021Macias; 2022Liu) find masses $\sim3 - 5$ higher, respectively. Recent work by (cite: 2023Xin; 2023Rilinger) shows that the SED modeling-derived masses are, respectively, $\sim1.5 - 6\ \& \sim1.5 - 5$ times higher than those obtained from the literature. Using values from (cite: 2023Rilinger) and this work for the Serpens and L1641/L1647 samples, Figure [6](#fig: mdust comparison all regions) compares all 12 regions and shows the mass ratio between disk mass derived from SED modeling and those calculated from literature fluxes. The discrepancy factor, given as $M_{dust, DIAD} / M_{dust, lit}$, has a median of $\sim$1.74 for all regions and shows a slight increase toward the most massive disks. For younger regions (i.e., $<$2 Myr; Ophiuchus, Taurus, Cha II, L1641/L1647, Serpens, and Lupus) the discrepancy factor is greater than the populations’ average (i.e., 2.0), while for older regions (i.e., $>$2 Myr; Cha I, IC 348, Corona Australis, $\sigma$ Ori, $\lambda$ Ori, and Upper Sco) the discrepancy factor is lower (i.e., 1.2). Taurus has the biggest discrepancy factor (4.09), and Upper Sco has the lowest (0.72). It is important to note that these regions have different sample sizes, so it is likely that these values are influenced by the number of objects.

The explanation that has been proposed for the discrepancy in disk masses seen above is that Equation [\[eq: Hildebrand\]](#eq: Hildebrand) assumes that the disk emission is optically thin at the reference frequency, and this may not be true in all cases. For example, there are cases where the spectral index of the inner regions drops below 2 (i.e., TW Hya (cite: 2018Huang; 2021Macias), Elias 2-27 (cite: 2021Paneque-Carreno), and MP Mus (cite: 2023Ribas)), indicating that the emission is optically thick. If the disk is optically thick at certain wavelengths, the observed flux will not be sensitive to the total dust mass of the disk, and so Equation [\[eq: Hildebrand\]](#eq: Hildebrand) will underestimate $M_d$.

We demonstrate that our larger dust mass estimates – when compared with flux-based dust mass estimates – are mostly driven by high optical depths at (sub-)mm wavelengths in Figure [7](#fig: optical depth). Following the same methodology detailed in (cite: 2023Xin), we used the median values obtained from the ANN as input parameters to generate DIAD models from which we calculate the structure of the disk and the optical depth along the line of sight as a function of the radius at 225 GHz (1.3 mm). This is followed by computing a flux-weighted mean optical depth where the flux at each radius is used as the weight for the optical depth corresponding to that radius. These weights are calculated based on the intensity, disk radius, and inclination angle, which are further computed by considering the area difference between adjacent radii and the flux at each point, accounting for the inclination angle. The single average optical depth results from the mean of the optical depths weighted by the flux-derived weights. Panels (a) and (b) display the flux-weighted mean optical depths versus disk dust masses and disk sizes (respectively) for the samples of Taurus, Serpens, Lupus, Cha I, and Upper Sco, while for L1641/L1647, we include 10% of the sample to avoid overpopulating the plots. The marker size indicates disk radius (in au), and the black broken line denotes $\tau_{\omega} = 1$. Panel (a) shows that as we move toward greater disk dust masses, the mean optical depth tends to increase. Panel (b) shows that a similar trend of increasing mean optical depths occurs for smaller disk sizes, since the disk total mass gets concentrated in a smaller area, hence increasing the optical depth. Panel (c) displays again the mean optical depth, plotted against a disk dust mass ratio, i.e., the disk dust mass estimated from DIAD divided by the disk dust mass estimated from the (sub-)mm flux using Equation [\[eq: Hildebrand\]](#eq: Hildebrand). In addition, panel (c) also shows the disk dust mass derived from DIAD in the color scale, and the disk size as shown by the marker size (like in panels (a) and (b)). Panel (c) clearly demonstrates that higher disk dust mass discrepancy factors are caused by high optical depths. The three panels together show that these high optical depths are mostly driven by high disk dust masses and small disk sizes. In other words, flux-based disk dust masses are underestimated to a greater extent for disks that are more massive and/or more compact. These results highlight the importance of properly accounting for the optical depth of the disk, as high optical depths at (sub-)mm wavelengths can cause underestimation of disk mass when relying solely on flux-based estimates assuming optically thin emission.

![](FIGURE7.pdf)

## Comparison of Serpens $\&$ L1641/L1647 with other Star-Forming Regions

Here, we compare the results obtained for Serpens and L1641/L1647 with the 10 other star-forming regions studied in (cite: 2023Rilinger). These regions span an age range from $\sim$0.5-10 Myr.[^1] Figure [8](#fig: comparison with SFR) shows how the Serpens and L1641/L1647 dust mass distributions compare to the star-forming regions studied in (cite: 2023Rilinger). The peak of the mass distribution tends to shift to lower masses for older regions. Regions such as Serpens, Taurus, and L1641/L1647 (i.e., $<$ 3 Myr) have median dust masses above the overall median ($\sim$9.28 $M_{\oplus}$), while older regions such as Upper Sco and $\lambda$ Ori (i.e., $>$ 3 Myr) have dust masses that are below the overall median. Figure [9](#fig: dust depletion) is also consistent with the finding that disk dust mass generally decreases with age (cite: 2016Ansdell; 2016Barenfeld; 2016Pascucci; 2019Cieza; 2019vanTerwisga; 2021Villenave; 2022vanTerwisga; 2023Rilinger). We note that the objects included in each region are biased towards higher masses as we only include sources with millimeter-wavelength detections. Additionally, each survey adopts a different detection limit (cite: 2022vanTerwisga; 2022Anderson; 2023Rilinger).

![](FIGURE8.pdf)

![](FIGURE9.pdf)

## The “missing mass” problem

One possible solution to the “missing mass” problem is that disk dust masses are underestimated. In this work, as in other works (cite: 2019BalleringEisner; 2020Ribas; 2023Xin; 2023Rilinger), we find that disk dust masses can be underestimated when using millimeter fluxes alone. To further explore whether this can solve the “missing mass” problem, we compare observed exoplanet systems and the available dust mass in protoplanetary disks.

Figure [10](#fig: CDF) compares the cumulative distribution function (CDF) for the dust mass content in Serpens and L1641/L1647 from this work (i.e., SED model derived; red line and blue line, respectively), the dust mass content using (cite: 2022Anderson) & (cite: 2022vanTerwisga) millimeter fluxes (light red line and light blue line, respectively), and the mass content observed in currently known exoplanets (gray line). The masses of presently known and confirmed exoplanets were gathered from the [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/docs/counts_detail.html), amounting to a sample of 3401 exoplanets with known masses and respective errors. The black cumulative distribution function denotes the masses of exoplanet systems, which are normalized to the observed fraction of gaseous planets (cite: 2008Cumming). Based on observations, gaseous planets are rarer than rocky low-mass planets. As shown in (cite: 2011Mayor), about 50$\%$ of solar-type stars host planets with a mass upper limit $<$ 30 M$_{\oplus}$. (cite: 2008Cumming) estimates that about 17$\%$-19$\%$ of stars host gas giants within 20 au. Following the methodology detailed in (cite: 2020Tychoniec), we restrict our sample to only systems containing at least one planet with a total mass $>$ 0.3 $M_{Jup}$, as detectability increases for objects with periods as large as 2000 days (cite: 2008Cumming). We normalize these systems by setting the 18$\%$ value of the CDF at the estimated solid fraction of the gaseous planet of 0.3 $M_{Jup}$ (i.e., 27.8 $M_{\oplus}$). Thus, we limit our sample to only those objects that are detectable and have a known solid material content (cite: 2016Thorngren). Figure [10](#fig: CDF) shows how, despite accounting for disk mass underestimation, the “missing mass" issue persists, implying that the problem is more complicated and may involve multiple factors.

As mentioned in Section [1](#sec:intro), the “lack" of mass can also be explained by earlier planet formation (i.e., happening as early as the Class 0 and Class I stages), as discussed in (cite: 2020Tychoniec) where they compare Class 0, Class I, and Class II objects from the Perseus and Orion star-forming regions. In both instances, the CDF for Class II objects does not follow the CDF for exoplanets at greater masses. If planet formation occurs earlier (i.e., during the Class O and/or Class I stages), then the dust masses we are measuring for Class II objects may only represent that of the remnant material of planet formation.

It is also possible that we are still underestimating the dust masses. First, we are not sensitive to grains $> 1$ mm. In addition, there may be significant dust in optically thick disk substructures (cite: 2024Savvidou). To more accurately measure disk dust masses, observations at longer wavelengths are necessary. (cite: 2023Xin) showed that disks become optically thinner at 3 mm relative to 1.3 mm. In Figure [11](#fig: optical_depth_7mm), we calculate the optical depth at a longer reference wavelength of 7mm corresponding to ALMA band 1 for Serpens and L1641/L1647. We find that the vast majority of objects become optically thin at 7 mm. Thus, observations at longer mm wavelengths (i.e., ALMA band 3 and band 1) are essential to better characterize the dust content of disks.

![](FIGURE10.pdf)

![](FIGURE11.pdf)

# Summary

We calculated disk dust masses for a sample of 178 TTS, 18 located in the Serpens star-forming region and 160 in the L1641 & L1647 regions, using multi-wavelength photometry and *Spitzer* IRS spectra (when available) and an ANN trained with DIAD models (following (cite: 2020Ribas)). The sample was obtained from ALMA 1.3 mm continuum band surveys of Serpens (cite: 2022Anderson) and the L1641 & L1647 regions of the Orion A cloud (cite: 2022vanTerwisga). Our work measured disk dust masses using SED modeling and the key findings are as follows:

- Disk dust masses calculated from SED modeling are, on average, a factor of 2.0 times higher for both Serpens and L1641/L1647 than those computed using mm-fluxes at 1.3mm. This is consistent with previous work done in other regions by (cite: 2020Ribas; 2023Xin; 2023Rilinger), where a similar methodology was followed. We conclude that this is because most disk dust masses calculated using mm-fluxes assume that the disk is optically thin, whereas we find that many disks are still optically thick at 1.3mm.

- When compared to 10 other star-forming regions that range from $\sim$0.5 to $\sim$10 Myr (cite: 2023Rilinger), Serpens and L1641/L1647 follow the tendency of younger regions (e.g., Taurus, Cha II, $\sigma$ Ori) to display a greater median disk dust mass than the overall average. Serpens’ median disk dust mass is $\sim$55.3 $M_{\oplus}$, and L1641/L1647’s median disk dust mass is $\sim$17.9 $M_{\oplus}$; whereas the median for all 12 star-forming regions is $\sim$9.28 $M_{\oplus}$.

- Dust masses for Serpens and L1641/L1647 follow the observed relation between dust mass and age (i.e., $M_{dust} \propto t^{-1}$).

- We calculated the optical depths of a subset of disks in Serpens and L1641/L1647 at 1.3mm and 7mm and found that most disks are optically thick at 1.3mm while the vast majority are optically thin at 7 mm.

Future ALMA surveys are needed at longer wavelengths where the disk is more likely to be optically thin (e.g., band 1) to more accurately measure disk dust masses. This will allow for a more detailed view of disk evolution and planet formation as well as comparison with exoplanet populations.

# Acknowledgments

This work was funded by NASA ADAP 80NSSC20K0451. Álvaro Ribas has been supported by the UK Science and Technology Facilities Council (STFC) via the consolidated grant ST/W000997/1 and by the European Union’s Horizon 2020 research and innovation programme under the Marie Sklodowska-Curie grant agreement No. 823823 (RISE DUSTBUSTERS project). We thank Alexa R. Anderson, Jesús Hernández, Kevin Luhman, Anneliese M. Rilinger, and Zihua Xin for insightful discussions. This paper utilizes the D’Alessio Irradiated Accretion Disk (DIAD) code. We acknowledge the important work carried out by Paola D’Alessio, who passed away in 2013. Without her, works like these could not have been achieved.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00218.S and ADS/JAO.ALMA#2019.1.01813.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This research has made use of the NASA Exoplanet Archive, which is operated by the California Institute of Technology, under contract with the National Aeronautics and Space Administration under the Exoplanet Exploration Program. This work has made use of the interactive graphical viewer and editor for tabular data TOPCAT (cite: 2005TOPCAT). This research has made use of the VizieR catalogue access tool, CDS, Strasbourg, France (DOI : 10.26093/cds/vizier). The original description of the VizieR service was published in (cite: 2000Vizier). This research has made use of the SIMBAD database (cite: 2000SIMBAD), operated at CDS, Strasbourg, France. This work has made use of data from the European Space Agency (ESA) mission [*Gaia*](https://www.cosmos.esa.int/gaia), processed by the [*Gaia* Data Processing and Analysis Consortium](https://www.cosmos.esa.int/web/gaia/dpac/consortium) (DPAC).

# Software

`AstroPy` (cite: 2013Astropy; 2018AJ....156..123A; 2022ApJ...935..167A), `NumPy` (cite: 2020Numpy), `SciPy` (cite: 2020Scipy), `lifelines` (cite: 2022lifelines), `matplotlib` (cite: 2007matplotlib), `pandas` (cite: 2022pandas)

natexlab

(ref: 2023Abdurro) Abdurro’Uf, & et al. 2023, VizieR Online Data Catalog: APOGEE-2 DR17 final allStar catalog (Abdurro’uf+, 2022), VizieR On-line Data Catalog: III/286. Originally published in: 2022ApJS..259...35A

(ref: SDSS) Ahumada, R., Allende Prieto, C., Almeida, A., et al. 2020, ApJS, 249, 3, doi: [`10.3847/1538-4365/ab929e`](http://doi.org/10.3847/1538-4365/ab929e)

(ref: 2019Akeson) Akeson, R. L., Jensen, E. L. N., Carpenter, J., et al. 2019, ApJ, 872, 158, doi: [`10.3847/1538-4357/aaff6a`](http://doi.org/10.3847/1538-4357/aaff6a)

(ref: 2015ALMApartnership) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3, doi: [`10.1088/2041-8205/808/1/L3`](http://doi.org/10.1088/2041-8205/808/1/L3)

(ref: 2022Anderson) Anderson, A. R., Williams, J. P., van der Marel, N., et al. 2022, ApJ, 938, 55, doi: [`10.3847/1538-4357/ac8ff0`](http://doi.org/10.3847/1538-4357/ac8ff0)

(ref: 2018Andrae) Andrae, R., Fouesneau, M., Creevey, O., et al. 2018, A&A, 616, A8, doi: [`10.1051/0004-6361/201732516`](http://doi.org/10.1051/0004-6361/201732516)

(ref: 2023Andrae) Andrae, R., Fouesneau, M., Sordo, R., et al. 2023, A&A, 674, A27, doi: [`10.1051/0004-6361/202243462`](http://doi.org/10.1051/0004-6361/202243462)

(ref: 2013Andrews) Andrews, S. M., Rosenfeld, K. A., Kraus, A. L., & Wilner, D. J. 2013, ApJ, 771, 129, doi: [`10.1088/0004-637X/771/2/129`](http://doi.org/10.1088/0004-637X/771/2/129)

(ref: 2005AndrewsWilliams) Andrews, S. M., & Williams, J. P. 2005, ApJ, 631, 1134, doi: [`10.1086/432712`](http://doi.org/10.1086/432712)

(ref: 2018Andrews) Andrews, S. M., Wilner, D. J., Macı́as, E., Carrasco-González, C., & Isella, A. 2018, in Astronomical Society of the Pacific Conference Series, Vol. 517, Science with a Next Generation Very Large Array, ed. E. Murphy, 137

(ref: 2017Ansdell) Ansdell, M., Williams, J. P., Manara, C. F., et al. 2017, AJ, 153, 240, doi: [`10.3847/1538-3881/aa69c0`](http://doi.org/10.3847/1538-3881/aa69c0)

(ref: 2016Ansdell) Ansdell, M., Williams, J. P., van der Marel, N., et al. 2016, ApJ, 828, 46, doi: [`10.3847/0004-637X/828/1/46`](http://doi.org/10.3847/0004-637X/828/1/46)

(ref: 1994Artymowicz) Artymowicz, P., & Lubow, S. H. 1994, ApJ, 421, 651, doi: [`10.1086/173679`](http://doi.org/10.1086/173679)

(ref: 2013Astropy) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2022ApJ...935..167A) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: 2013BailerJones) Bailer-Jones, C. A. L., Andrae, R., Arcay, B., et al. 2013, A&A, 559, A74, doi: [`10.1051/0004-6361/201322344`](http://doi.org/10.1051/0004-6361/201322344)

(ref: 2019BalleringEisner) Ballering, N. P., & Eisner, J. A. 2019, AJ, 157, 144, doi: [`10.3847/1538-3881/ab0a56`](http://doi.org/10.3847/1538-3881/ab0a56)

(ref: 2016Barenfeld) Barenfeld, S. A., Carpenter, J. M., Ricci, L., & Isella, A. 2016, ApJ, 827, 142, doi: [`10.3847/0004-637X/827/2/142`](http://doi.org/10.3847/0004-637X/827/2/142)

(ref: 2019Barenfeld) Barenfeld, S. A., Carpenter, J. M., Sargent, A. I., et al. 2019, ApJ, 878, 45, doi: [`10.3847/1538-4357/ab1e50`](http://doi.org/10.3847/1538-4357/ab1e50)

(ref: 1990Bekwith) Beckwith, S. V. W., Sargent, A. I., Chini, R. S., & Guesten, R. 1990, AJ, 99, 924, doi: [`10.1086/115385`](http://doi.org/10.1086/115385)

(ref: 2018BerginWilliams) Bergin, E. A., & Williams, J. P. 2018, arXiv e-prints, arXiv:1807.09631, doi: [`10.48550/arXiv.1807.09631`](http://doi.org/10.48550/arXiv.1807.09631)

(ref: 2010Birnstiel) Birnstiel, T., Dullemond, C. P., & Brauer, F. 2010, A&A, 513, A79, doi: [`10.1051/0004-6361/200913731`](http://doi.org/10.1051/0004-6361/200913731)

(ref: 2024Cacciapuoti) Cacciapuoti, L., Testi, L., Podio, L., et al. 2024, The Astrophysical Journal, 961, 90, doi: [`10.3847/1538-4357/ad0f17`](http://doi.org/10.3847/1538-4357/ad0f17)

(ref: 2019Cazzoletti) Cazzoletti, P., Manara, C. F., Liu, H. B., et al. 2019, A&A, 626, A11, doi: [`10.1051/0004-6361/201935273`](http://doi.org/10.1051/0004-6361/201935273)

(ref: PANSTARRS) Chambers, K. C., Magnier, E. A., Metcalfe, N., et al. 2016, arXiv e-prints, arXiv:1612.05560, doi: [`10.48550/arXiv.1612.05560`](http://doi.org/10.48550/arXiv.1612.05560)

(ref: 2016Choi) Choi, J., Dotter, A., Conroy, C., et al. 2016, ApJ, 823, 102, doi: [`10.3847/0004-637X/823/2/102`](http://doi.org/10.3847/0004-637X/823/2/102)

(ref: 2009Cieza) Cieza, L. A., Padgett, D. L., Allen, L. E., et al. 2009, ApJL, 696, L84, doi: [`10.1088/0004-637X/696/1/L84`](http://doi.org/10.1088/0004-637X/696/1/L84)

(ref: 2019Cieza) Cieza, L. A., Ruı́z-Rodrı́guez, D., Hales, A., et al. 2019, MNRAS, 482, 698, doi: [`10.1093/mnras/sty2653`](http://doi.org/10.1093/mnras/sty2653)

(ref: 2017Cox) Cox, E. G., Harris, R. J., Looney, L. W., et al. 2017, ApJ, 851, 83, doi: [`10.3847/1538-4357/aa97e2`](http://doi.org/10.3847/1538-4357/aa97e2)

(ref: 2008Cumming) Cumming, A., Butler, R. P., Marcy, G. W., et al. 2008, PASP, 120, 531, doi: [`10.1086/588487`](http://doi.org/10.1086/588487)

(ref: ALLWISECutri) Cutri, R. M., Wright, E. L., Conrow, T., et al. 2021, VizieR Online Data Catalog, II/328

(ref: 2016DaRio) da Rio, N., Tan, J. C., Covey, K. R., et al. 2016, VizieR Online Data Catalog: IN-SYNC. IV. YSOs in Orion A (Da Rio+, 2016), VizieR On-line Data Catalog: J/ApJ/818/59. Originally published in: 2016ApJ...818...59D, doi: [`10.26093/cds/vizier.18180059`](http://doi.org/10.26093/cds/vizier.18180059)

(ref: 2001Dalessio) D’Alessio, P., Calvet, N., & Hartmann, L. 2001, ApJ, 553, 321, doi: [`10.1086/320655`](http://doi.org/10.1086/320655)

(ref: 2006Dalessio) D’Alessio, P., Calvet, N., Hartmann, L., Franco-Hernández, R., & Servı́n, H. 2006, ApJ, 638, 314, doi: [`10.1086/498861`](http://doi.org/10.1086/498861)

(ref: 1999Dalessio) D’Alessio, P., Calvet, N., Hartmann, L., Lizano, S., & Cantó, J. 1999, ApJ, 527, 893, doi: [`10.1086/308103`](http://doi.org/10.1086/308103)

(ref: 1998Dalessio) D’Alessio, P., Cantö, J., Calvet, N., & Lizano, S. 1998, ApJ, 500, 411, doi: [`10.1086/305702`](http://doi.org/10.1086/305702)

(ref: 2005Dalessio) D’Alessio, P., Hartmann, L., Calvet, N., et al. 2005, ApJ, 621, 461, doi: [`10.1086/427490`](http://doi.org/10.1086/427490)

(ref: 2022lifelines) Davidson-Pilon, C. 2022, lifelines, survival analysis in Python, v0.27.4, Zenodo, doi: [`10.5281/zenodo.7329096`](http://doi.org/10.5281/zenodo.7329096)

(ref: 2016Dotter) Dotter, A. 2016, ApJS, 222, 8, doi: [`10.3847/0067-0049/222/1/8`](http://doi.org/10.3847/0067-0049/222/1/8)

(ref: 2015Dunham) Dunham, M. M., Allen, L. E., Evans, Neal J., I., et al. 2015, ApJS, 220, 11, doi: [`10.1088/0067-0049/220/1/11`](http://doi.org/10.1088/0067-0049/220/1/11)

(ref: 2015Erickson) Erickson, K. L., Wilking, B. A., Meyer, M. R., et al. 2015, AJ, 149, 103, doi: [`10.1088/0004-6256/149/3/103`](http://doi.org/10.1088/0004-6256/149/3/103)

(ref: SpitzerEvans) Evans, Neal J., I., Allen, L. E., Blake, G. A., et al. 2003, PASP, 115, 965, doi: [`10.1086/376697`](http://doi.org/10.1086/376697)

(ref: 2009Evans) Evans, N. J., Dunham, M. M., Jorgensen, J. K., et al. 2009, VizieR Online Data Catalog, J/ApJS/181/321, doi: [`10.26093/cds/vizier.21810321`](http://doi.org/10.26093/cds/vizier.21810321)

(ref: 2013FangA) Fang, M., Kim, J. S., van Boekel, R., et al. 2013, ApJS, 207, 5, doi: [`10.1088/0067-0049/207/1/5`](http://doi.org/10.1088/0067-0049/207/1/5)

(ref: 2009Fang) Fang, M., van Boekel, R., Wang, W., et al. 2009, A&A, 504, 461, doi: [`10.1051/0004-6361/200912468`](http://doi.org/10.1051/0004-6361/200912468)

(ref: 2018Fang) Fang, M., Kim, J. S., Pascucci, I., et al. 2018, VizieR Online Data Catalog: Spectroscopy of the foreground population in Orion A (Fang+, 2017), VizieR On-line Data Catalog: J/AJ/153/188. Originally published in: 2017AJ....153..188F, doi: [`10.26093/cds/vizier.51530188`](http://doi.org/10.26093/cds/vizier.51530188)

(ref: 2013Foreman-Mackey) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: 2018GaiaDR2) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1, doi: [`10.1051/0004-6361/201833051`](http://doi.org/10.1051/0004-6361/201833051)

(ref: GaiaDR3) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1, doi: [`10.1051/0004-6361/202243940`](http://doi.org/10.1051/0004-6361/202243940)

(ref: 2021Ginski) Ginski, C., Facchini, S., Huang, J., et al. 2021, ApJL, 908, L25, doi: [`10.3847/2041-8213/abdf57`](http://doi.org/10.3847/2041-8213/abdf57)

(ref: 1993Goodman) Goodman, A. A., Benson, P. J., Fuller, G. A., & Myers, P. C. 1993, ApJ, 406, 528, doi: [`10.1086/172465`](http://doi.org/10.1086/172465)

(ref: 2018Grant) Grant, S. L., Espaillat, C. C., Megeath, S. T., et al. 2018, ApJ, 863, 13, doi: [`10.3847/1538-4357/aacda7`](http://doi.org/10.3847/1538-4357/aacda7)

(ref: 2021Grant) Grant, S. L., Espaillat, C. C., Wendeborn, J., et al. 2021, ApJ, 913, 123, doi: [`10.3847/1538-4357/abf432`](http://doi.org/10.3847/1538-4357/abf432)

(ref: 2019Grossschedl) Großschedl, J. E., Alves, J., Teixeira, P. S., et al. 2019, A&A, 622, A149, doi: [`10.1051/0004-6361/201832577`](http://doi.org/10.1051/0004-6361/201832577)

(ref: 2021Guzman-Diaz) Guzmán-Dı́az, J., Mendigutı́a, I., Montesinos, B., et al. 2021, A&A, 650, A182, doi: [`10.1051/0004-6361/202039519`](http://doi.org/10.1051/0004-6361/202039519)

(ref: 2020Numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: 2012Harris) Harris, R. J., Andrews, S. M., Wilner, D. J., & Kraus, A. L. 2012, ApJ, 751, 115, doi: [`10.1088/0004-637X/751/2/115`](http://doi.org/10.1088/0004-637X/751/2/115)

(ref: 2007Harvey) Harvey, P., Merı́n, B., Huard, T. L., et al. 2007, ApJ, 663, 1149, doi: [`10.1086/518646`](http://doi.org/10.1086/518646)

(ref: 2016Henden) Henden, A. A., Templeton, M., Terrell, D., et al. 2016, VizieR Online Data Catalog, II/336

(ref: 1962Herbig) Herbig, G. H. 1962, Advances in Astronomy and Astrophysics, 1, 47, doi: [`10.1016/B978-1-4831-9919-1.50006-6`](http://doi.org/10.1016/B978-1-4831-9919-1.50006-6)

(ref: 2023Hernandez) Hernández, J., Zamudio, L. F., Briceño, C., et al. 2023, AJ, 165, 205, doi: [`10.3847/1538-3881/acc467`](http://doi.org/10.3847/1538-3881/acc467)

(ref: 1983Hildebrand) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: 2010Hogg) Hogg, D. W., Bovy, J., & Lang, D. 2010, arXiv e-prints, arXiv:1008.4686, doi: [`10.48550/arXiv.1008.4686`](http://doi.org/10.48550/arXiv.1008.4686)

(ref: 2004IRS) Houck, J. R., Roellig, T. L., van Cleve, J., et al. 2004, ApJS, 154, 18, doi: [`10.1086/423134`](http://doi.org/10.1086/423134)

(ref: 2012Hsu) Hsu, W.-H., Hartmann, L., Allen, L., et al. 2012, ApJ, 752, 59, doi: [`10.1088/0004-637X/752/1/59`](http://doi.org/10.1088/0004-637X/752/1/59)

(ref: 2013Hsu) —. 2013, ApJ, 764, 114, doi: [`10.1088/0004-637X/764/2/114`](http://doi.org/10.1088/0004-637X/764/2/114)

(ref: 2018Huang) Huang, J., Andrews, S. M., Cleeves, L. I., et al. 2018, ApJ, 852, 122, doi: [`10.3847/1538-4357/aaa1e7`](http://doi.org/10.3847/1538-4357/aaa1e7)

(ref: 2007matplotlib) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: 1945Joy) Joy, A. H. 1945, ApJ, 102, 168, doi: [`10.1086/144749`](http://doi.org/10.1086/144749)

(ref: 2013Kim) Kim, K. H., Watson, D. M., Manoj, P., et al. 2013, ApJ, 769, 149, doi: [`10.1088/0004-637X/769/2/149`](http://doi.org/10.1088/0004-637X/769/2/149)

(ref: 2016Kim) —. 2016, VizieR Online Data Catalog: Spitzer/IRS survey of Class II objects in Orion A. I. (Kim+, 2016), VizieR On-line Data Catalog: J/ApJS/226/8. Originally published in: 2016ApJS..226....8K, doi: [`10.26093/cds/vizier.22260008`](http://doi.org/10.26093/cds/vizier.22260008)

(ref: 2016Kounkel) Kounkel, M., Megeath, S. T., Poteet, C. A., Fischer, W. J., & Hartmann, L. 2016, VizieR Online Data Catalog: NIR survey of Spitzer YSOs in Orion Mol. Cloud (Kounkel+, 2016), VizieR On-line Data Catalog: J/ApJ/821/52. Originally published in: 2016ApJ...821...52K, doi: [`10.26093/cds/vizier.18210052`](http://doi.org/10.26093/cds/vizier.18210052)

(ref: 2012Kraus) Kraus, A. L., Ireland, M. J., Hillenbrand, L. A., & Martinache, F. 2012, ApJ, 745, 19, doi: [`10.1088/0004-637X/745/1/19`](http://doi.org/10.1088/0004-637X/745/1/19)

(ref: 2017Kuffmeier) Kuffmeier, M., Haugbølle, T., & Nordlund, Å. 2017, ApJ, 846, 7, doi: [`10.3847/1538-4357/aa7c64`](http://doi.org/10.3847/1538-4357/aa7c64)

(ref: GSC2.3Lasker) Lasker, B. M., Lattanzi, M. G., McLean, B. J., et al. 2008, AJ, 136, 735, doi: [`10.1088/0004-6256/136/2/735`](http://doi.org/10.1088/0004-6256/136/2/735)

(ref: 2011CASSIS) Lebouteiller, V., Barry, D. J., Spoon, H. W. W., et al. 2011, ApJS, 196, 8, doi: [`10.1088/0067-0049/196/1/8`](http://doi.org/10.1088/0067-0049/196/1/8)

(ref: 2021Lindegren) Lindegren, L., Bastian, U., Biermann, M., et al. 2021, A&A, 649, A4, doi: [`10.1051/0004-6361/202039653`](http://doi.org/10.1051/0004-6361/202039653)

(ref: 2023Liu) Liu, M., He, J., Ge, J., et al. 2023, ApJ, 943, 39, doi: [`10.3847/1538-4357/aca658`](http://doi.org/10.3847/1538-4357/aca658)

(ref: 2022Liu) Liu, Y., Linz, H., Fang, M., et al. 2022, A&A, 668, A175, doi: [`10.1051/0004-6361/202244505`](http://doi.org/10.1051/0004-6361/202244505)

(ref: 2020Luhman) Luhman, K. L. 2020, AJ, 160, 186, doi: [`10.3847/1538-3881/abb12f`](http://doi.org/10.3847/1538-3881/abb12f)

(ref: 2020LuhmanEsplin) Luhman, K. L., & Esplin, T. L. 2020, AJ, 160, 44, doi: [`10.3847/1538-3881/ab9599`](http://doi.org/10.3847/1538-3881/ab9599)

(ref: 2021Macias) Macı́as, E., Guerra-Alvarado, O., Carrasco-González, C., et al. 2021, A&A, 648, A33, doi: [`10.1051/0004-6361/202039812`](http://doi.org/10.1051/0004-6361/202039812)

(ref: 2018Manara) Manara, C. F., Morbidelli, A., & Guillot, T. 2018, A&A, 618, L3, doi: [`10.1051/0004-6361/201834076`](http://doi.org/10.1051/0004-6361/201834076)

(ref: 2017Herschel) Marton, G., Calzoletti, L., Perez Garcia, A. M., et al. 2017, arXiv e-prints, arXiv:1705.05693, doi: [`10.48550/arXiv.1705.05693`](http://doi.org/10.48550/arXiv.1705.05693)

(ref: 2011Mayor) Mayor, M., Marmier, M., Lovis, C., et al. 2011, arXiv e-prints, arXiv:1109.2497, doi: [`10.48550/arXiv.1109.2497`](http://doi.org/10.48550/arXiv.1109.2497)

(ref: 2009McClure) McClure, M. 2009, ApJL, 693, L81, doi: [`10.1088/0004-637X/693/2/L81`](http://doi.org/10.1088/0004-637X/693/2/L81)

(ref: 2012Megeath) Megeath, S. T., Gutermuth, R., Muzerolle, J., et al. 2012, AJ, 144, 192, doi: [`10.1088/0004-6256/144/6/192`](http://doi.org/10.1088/0004-6256/144/6/192)

(ref: 2021Mulders) Mulders, G. D., Pascucci, I., Ciesla, F. J., & Fernandes, R. B. 2021, ApJ, 920, 66, doi: [`10.3847/1538-4357/ac178e`](http://doi.org/10.3847/1538-4357/ac178e)

(ref: 2014NajitaKenyon) Najita, J. R., & Kenyon, S. J. 2014, MNRAS, 445, 3315, doi: [`10.1093/mnras/stu1994`](http://doi.org/10.1093/mnras/stu1994)

(ref: 2000Vizier) Ochsenbein, F., Bauer, P., & Marcout, J. 2000, A&AS, 143, 23, doi: [`10.1051/aas:2000169`](http://doi.org/10.1051/aas:2000169)

(ref: 2022Offner) Offner, S. S. R., Taylor, J., Markey, C., et al. 2022, MNRAS, 517, 885, doi: [`10.1093/mnras/stac2734`](http://doi.org/10.1093/mnras/stac2734)

(ref: 2013Oliveira) Oliveira, I., Merı́n, B., Pontoppidan, K. M., & van Dishoeck, E. F. 2013, ApJ, 762, 128, doi: [`10.1088/0004-637X/762/2/128`](http://doi.org/10.1088/0004-637X/762/2/128)

(ref: 2009Oliveira) Oliveira, I., Merı́n, B., Pontoppidan, K. M., et al. 2009, ApJ, 691, 672, doi: [`10.1088/0004-637X/691/1/672`](http://doi.org/10.1088/0004-637X/691/1/672)

(ref: 2021Paneque-Carreno) Paneque-Carreño, T., Pérez, L. M., Benisty, M., et al. 2021, ApJ, 914, 88, doi: [`10.3847/1538-4357/abf243`](http://doi.org/10.3847/1538-4357/abf243)

(ref: 2016Pascucci) Pascucci, I., Testi, L., Herczeg, G. J., et al. 2016, ApJ, 831, 125, doi: [`10.3847/0004-637X/831/2/125`](http://doi.org/10.3847/0004-637X/831/2/125)

(ref: 2011Paxton) Paxton, B., Bildsten, L., Dotter, A., et al. 2011, ApJS, 192, 3, doi: [`10.1088/0067-0049/192/1/3`](http://doi.org/10.1088/0067-0049/192/1/3)

(ref: 2013Paxton) Paxton, B., Cantiello, M., Arras, P., et al. 2013, ApJS, 208, 4, doi: [`10.1088/0067-0049/208/1/4`](http://doi.org/10.1088/0067-0049/208/1/4)

(ref: 2015Paxton) Paxton, B., Marchant, P., Schwab, J., et al. 2015, ApJS, 220, 15, doi: [`10.1088/0067-0049/220/1/15`](http://doi.org/10.1088/0067-0049/220/1/15)

(ref: 2013PecautMamajek) Pecaut, M. J., & Mamajek, E. E. 2013, ApJS, 208, 9, doi: [`10.1088/0067-0049/208/1/9`](http://doi.org/10.1088/0067-0049/208/1/9)

(ref: 2022pandas) Reback, J., Jbrockmendel, McKinney, W., et al. 2022, pandas-dev/pandas: Pandas 1.4.4, v1.4.4, Zenodo, doi: [`10.5281/zenodo.7037953`](http://doi.org/10.5281/zenodo.7037953)

(ref: 2020Ribas) Ribas, Á., Espaillat, C. C., Macı́as, E., & Sarro, L. M. 2020, A&A, 642, A171, doi: [`10.1051/0004-6361/202038352`](http://doi.org/10.1051/0004-6361/202038352)

(ref: 2017Ribas) Ribas, Á., Espaillat, C. C., Macı́as, E., et al. 2017, ApJ, 849, 63, doi: [`10.3847/1538-4357/aa8e99`](http://doi.org/10.3847/1538-4357/aa8e99)

(ref: 2023Ribas) Ribas, Á., Macı́as, E., Weber, P., et al. 2023, A&A, 673, A77, doi: [`10.1051/0004-6361/202245637`](http://doi.org/10.1051/0004-6361/202245637)

(ref: 2023Rilinger) Rilinger, A. M., Espaillat, C. C., Xin, Z., et al. 2023, ApJ, 944, 66, doi: [`10.3847/1538-4357/aca905`](http://doi.org/10.3847/1538-4357/aca905)

(ref: 2023Zuniga) Roman-Zuniga, C. G., Kounkel, M., Hernandez, J., et al. 2023, VizieR Online Data Catalog: Stellar properties in SFRs from SDSS APOGEE-2 (Roman-Zuniga+, 2023), VizieR On-line Data Catalog: J/AJ/165/51. Originally published in: 2023AJ....165...51R

(ref: 2022Rota) Rota, A. A., Manara, C. F., Miotello, A., et al. 2022, A&A, 662, A121, doi: [`10.1051/0004-6361/202141035`](http://doi.org/10.1051/0004-6361/202141035)

(ref: 2016RuizRodriguez) Ruı́z-Rodrı́guez, D., Ireland, M., Cieza, L., & Kraus, A. 2016, MNRAS, 463, 3829, doi: [`10.1093/mnras/stw2297`](http://doi.org/10.1093/mnras/stw2297)

(ref: 2018RuizRodriguez) Ruı́z-Rodrı́guez, D., Cieza, L. A., Williams, J. P., et al. 2018, MNRAS, 478, 3674, doi: [`10.1093/mnras/sty1351`](http://doi.org/10.1093/mnras/sty1351)

(ref: 2024Savvidou) Savvidou, S., & Bitsch, B. 2024, arXiv e-prints, arXiv:2407.08533, doi: [`10.48550/arXiv.2407.08533`](http://doi.org/10.48550/arXiv.2407.08533)

(ref: 2020SeguraCox) Segura-Cox, D. M., Schmiedeke, A., Pineda, J. E., et al. 2020, Nature, 586, 228, doi: [`10.1038/s41586-020-2779-6`](http://doi.org/10.1038/s41586-020-2779-6)

(ref: 2023Serna) Serna, J., Hernandez, J., Kounkel, M., et al. 2023, VizieR Online Data Catalog: TESS obs. & rotational periods of T Tauri in Orion (Serna+, 2021), VizieR On-line Data Catalog: J/ApJ/923/177. Originally published in: 2021ApJ...923..177S

(ref: 1973Shakura) Shakura, N. I., & Sunyaev, R. A. 1973, A&A, 24, 337

(ref: 1987Shu) Shu, F. H., Adams, F. C., & Lizano, S. 1987, ARA&A, 25, 23, doi: [`10.1146/annurev.aa.25.090187.000323`](http://doi.org/10.1146/annurev.aa.25.090187.000323)

(ref: 2MASSSkrutskie) Skrutskie, M. F., Cutri, R. M., Stiening, R., et al. 2006, AJ, 131, 1163, doi: [`10.1086/498708`](http://doi.org/10.1086/498708)

(ref: 2005TOPCAT) Taylor, M. B. 2005, in Astronomical Society of the Pacific Conference Series, Vol. 347, Astronomical Data Analysis Software and Systems XIV, ed. P. Shopbell, M. Britton, & R. Ebert, 29

(ref: 2022Testi) Testi, L., Natta, A., Manara, C. F., et al. 2022, A&A, 663, A98, doi: [`10.1051/0004-6361/202141380`](http://doi.org/10.1051/0004-6361/202141380)

(ref: 2016Thorngren) Thorngren, D. P., Fortney, J. J., Murray-Clay, R. A., & Lopez, E. D. 2016, ApJ, 831, 64, doi: [`10.3847/0004-637X/831/1/64`](http://doi.org/10.3847/0004-637X/831/1/64)

(ref: 2008ThroopBally) Throop, H. B., & Bally, J. 2008, in AAS/Division of Dynamical Astronomy Meeting, Vol. 39, AAS/Division of Dynamical Astronomy Meeting #39, 17.01

(ref: 2020Tychoniec) Tychoniec, Ł., Manara, C. F., Rosotti, G. P., et al. 2020, A&A, 640, A19, doi: [`10.1051/0004-6361/202037851`](http://doi.org/10.1051/0004-6361/202037851)

(ref: 2016vanderMarel) van der Marel, N., Verhaar, B. W., van Terwisga, S., et al. 2016, VizieR Online Data Catalog, J/A+A/592/A126, doi: [`10.26093/cds/vizier.35920126`](http://doi.org/10.26093/cds/vizier.35920126)

(ref: 2022vanTerwisga) van Terwisga, S. E., Hacar, A., van Dishoeck, E. F., Oonk, R., & Portegies Zwart, S. 2022, A&A, 661, A53, doi: [`10.1051/0004-6361/202141913`](http://doi.org/10.1051/0004-6361/202141913)

(ref: 2019vanTerwisga) van Terwisga, S. E., van Dishoeck, E. F., Cazzoletti, P., et al. 2019, A&A, 623, A150, doi: [`10.1051/0004-6361/201834257`](http://doi.org/10.1051/0004-6361/201834257)

(ref: 2021Villenave) Villenave, M., Ménard, F., Dent, W. R. F., et al. 2021, A&A, 653, A46, doi: [`10.1051/0004-6361/202140496`](http://doi.org/10.1051/0004-6361/202140496)

(ref: 2020Scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: 2016Vousden) Vousden, W. D., Farr, W. M., & Mandel, I. 2016, MNRAS, 455, 1919, doi: [`10.1093/mnras/stv2422`](http://doi.org/10.1093/mnras/stv2422)

(ref: 2000SIMBAD) Wenger, M., Ochsenbein, F., Egret, D., et al. 2000, A&AS, 143, 9, doi: [`10.1051/aas:2000332`](http://doi.org/10.1051/aas:2000332)

(ref: 2019Williams) Williams, J. P., Cieza, L., Hales, A., et al. 2019, ApJL, 875, L9, doi: [`10.3847/2041-8213/ab1338`](http://doi.org/10.3847/2041-8213/ab1338)

(ref: 2011WilliamsCieza) Williams, J. P., & Cieza, L. A. 2011, ARA&A, 49, 67, doi: [`10.1146/annurev-astro-081710-102548`](http://doi.org/10.1146/annurev-astro-081710-102548)

(ref: 2023Xin) Xin, Z., Espaillat, C. C., Rilinger, A. M., Ribas, Á., & Macı́as, E. 2023, ApJ, 942, 4, doi: [`10.3847/1538-4357/aca52b`](http://doi.org/10.3847/1538-4357/aca52b)

(ref: 2018Yao) Yao, Y., Meyer, M. R., Covey, K. R., Tan, J. C., & Da Rio, N. 2018, ApJ, 869, 72, doi: [`10.3847/1538-4357/aaec7a`](http://doi.org/10.3847/1538-4357/aaec7a)

# Sample selection criteria

The original samples of 320 Serpens sources (cite: 2022Anderson) and 873 L1641/L1647 sources (cite: 2022vanTerwisga) are reduced to samples of 23 and 188 objects, respectively, after considering the following selection criteria:

- The sources must belong to the Serpens or L1641/L1647 star-forming regions.

  (cite: 2022Anderson) selected their sources by inspecting the *Spitzer* c2d and Gould Belt surveys, which consisted of 1546 YSOs identified towards the Serpens region. They selected a sample of 320 objects for their ALMA survey by choosing only those sources with infrared slopes less than 1.6 (cite: 2011WilliamsCieza). In their observation results table (cite: 2022Anderson), the **G** flag is employed to denote sources that are situated beyond the probable distance range of Serpens members. This reduces the reported observed sample from 320 to 302 likely members of the Serpens region. For further information regarding the process of membership selection, we refer the reader to (cite: 2015Dunham) and (cite: 2022Anderson).

  The SODA sample from (cite: 2022vanTerwisga) consists of 873 objects that belong to the L1641 and L1647 regions, located in the Orion A cloud at $<$ -6$\degree$ deg in declination. These were selected from the *Spitzer* survey of YSOs in the Orion A and B molecular clouds performed by (cite: 2012Megeath). The 41 objects in L1641, already modeled in (cite: 2023Rilinger), are included in our sample (see Section [4.2](#subsec: comparing serpens-l1641-l1647 with other sfr)). For consistency, we use the same source identifier as in (cite: 2012Megeath) and (cite: 2022vanTerwisga), abbreviating with \[MGM2012\] and the number of the object in the catalog.

- The sources must be identified as Class II.

  For the Serpens sample, we used the YSO class flag included in the (cite: 2022Anderson) results table (cite: 2011WilliamsCieza), reducing the sample to 235 objects. The (cite: 2022vanTerwisga) sample is comprised entirely of Class II YSOs from (cite: 2012Megeath), so no sources were discarded from the L1641/L1647 sample based on this criterion.

- The sources must have been detected by ALMA.

  Non-detections were included in the (cite: 2022Anderson) table for completeness. Discarding these sources reduces the sample to 182 objects, while for the L1641/L1647 sample, we only selected resolved sources, reducing the number of objects to 502.

- The sources must have at least two 2MASS measurements, two mid-IR (*WISE* or cd2) measurements, and one (sub)mm (ALMA) measurement.

  A photometric point at $\geq$ 500$\mu$m ensures coverage up to the (sub)mm regime, ideal for constraining the disk mass. As our models have many parameters, we require a minimum number of photometric points to obtain an appropriate fit and prevent degeneracies at the moment of SED modeling. 2MASS provides information on stellar properties, while the mid-IR traces the disk’s emission. Applying this criterion does not alter the size of the Serpens sample, as all sources have measurements; meanwhile, the L1641/L1647 sample is affected and reduced to 442 objects.

- The source is not known to be a transitional disk (TD), have a flat spectrum, or be in a binary/multiple system.

  The ANN omits TDs in its training sample (cite: 2020Ribas). Binary and multiple systems are avoided since they cause confusion when compiling their SED data, and in cases of low spatial resolution, this leads to inaccurate photometry. We discarded sources with companions $<$1000 au, based on the literature, as binarity can impact protoplanetary disk properties, structure, and evolution (cite: 1994Artymowicz; 2009Cieza; 2012Kraus; 2012Harris; 2016Kounkel; 2016RuizRodriguez; 2017Cox; 2019Akeson; 2019Barenfeld; 2019Cazzoletti; 2021Villenave; 2022Rota). We refer the reader to (cite: 2022Offner), for a recent review on the effects of binarity on disk systems.

  For the Serpens sample, we identified objects as TDs following (cite: 2016vanderMarel), and used the provided flag **T** in (cite: 2022Anderson), or used visual inspection of the SED to identify a “dip” in the mid-IR range (e.g., 2MASS J18300893+0047219 shows a SED characteristic of a TD). This reduces the Serpens sample to 163 objects.

  For the L1641/L1647 sample, we consulted the (cite: 2013Kim) infrared spectroscopic survey of Orion A on transitional disks, finding 19 objects in our sample identified as a type of TD (ranging from classical TD, weak-excess TD, and pre-TD). From the (cite: 2013FangA) L1641 study, we identified 23 objects as TD or Flat spectrum. Visually we identified and discarded \[MGM2012\] 128, 828, and 1066 as they show a “dip” around the mid-IR range, characteristic of the SED structure of a TD. From the (cite: 2009Fang) catalog, six objects are identified as TD: \[MGM2012\] 339, 365, 377, 395, 481, 971. We exclude five objects associated with extended millimeter-continuum emission from the envelope (\[MGM2012\] 56, 227, 421, 714, and 975; (cite: 2022vanTerwisga)). We also discard compact (visual) systems with companions within $<$10" (4000 au) (e.g., \[MGM2012\] 129, 754, 1000, 1090, and 1094). This reduces the L1641/L1647 sample to 381 objects.

- The sources must not have a (sub)mm measurement within 2”.5 of another (sub)mm detection of at least 3$\sigma$.

  For the Serpens sample, we used the provided flag **B** in (cite: 2022Anderson), which indicates that an object is detected in a binary system, with a 3$\sigma$ mm detection within 2”.5 ($\sim$1000 au) of the central source. This reduces the sample to 162 after discarding 2MASS J18311972-0201115. For the L1641/L1647 sample, we discarded one class II source (\[MGM2012\] 512) associated with extended millimeter-continuum emission (cite: 2021Grant; 2024Cacciapuoti), reducing the sample to 380 objects.

- The sources must have an ALMA detection of at least 3$\sigma$

  This reduces the Serpens sample to 70 objects while it keeps the L1641/L1647 sample unchanged.

- The sources must display good *Gaia* astrometric quality.

  To satisfy this, we select sources with *Gaia* DR3 astrometry. This reduces the Serpens sample to 42 sources. Although 2MASS 18314182-0207590 is included as a *Gaia* DR3 object, it is discarded as it does not have parallax values. We follow (cite: 2021Lindegren), which recommends the use of the renormalized unit weight error (RUWE, the uncertainty in measurements) to evaluate the quality of the astrometric solution. We apply two criteria for good astrometric fits: a parallax error below 20$\%$, and a RUWE $<$1.4. This reduces the Serpens sample to 29 sources, while the L1641/L1647 sample is reduced to 205 objects.

- The sources must be T Tauri stars.

  The ANN training is optimized with DIAD models that cover an estimated stellar mass in the range from 0.1 - 2.0 $M_{\odot}$ (cite: 2020Ribas). This generally corresponds to the range of masses associated with T Tauri stars, and so we discard objects classified as Herbig Ae/Be stars to ensure that no stars outside the stellar mass range covered by the ANN are included. From the Serpens sample, 2MASS J18295533+0049391 was discarded as it is identified as a Herbig Ae/Be star in (cite: 2009Oliveira). This results in the reduction of the Serpens sample to 28 objects. In the L1641/L1647 sample, we identified four sources as Herbig Ae/Be following (cite: 2021Guzman-Diaz): \[MGM2012\] 612, 760, 838, 1031. This reduces the L1641/L1647 sample to 201 objects.

- The sources must have stellar parameters in the literature.

  Stellar parameters are listed in Tables [1](#table:parameters_serpens) & [\[table:parameters_SODA\]](#table:parameters_SODA). For Serpens, we use (cite: 2007Harvey; 2009Oliveira; 2013Oliveira; 2015Erickson) for the star’s mass, radius, effective temperature, spectral type, and visual extinction. For the L1641/L1647 sources, we use (cite: 2009Fang; 2013FangA; 2018Fang; 2012Hsu; 2013Hsu; 2016DaRio; 2016Kounkel; 2016Kim; 2018Yao; 2023Zuniga; 2023Serna; 2023Abdurro). Tables [1](#table:parameters_serpens) & [\[table:parameters_SODA\]](#table:parameters_SODA) also include parallaxes and their respective error values obtained from *Gaia* DR3. These are all parameters later used as priors for the ANN.

  After inspecting all objects, we found that 5 objects from Serpens did not have parameters available in any catalog: \[2MASS\] 18274937-0353404, 18314002-0205339, 18314616-0153493, 18314791-0211559, 18325715-0245162. For L1641/L1647, 13 objects do not have available parameters: \[MGM 2012\] 102, 108, 121, 132, 146, 152, 168, 171, 229, 249, 260, 683, 974. These sources were discarded, reducing the Serpens sample to 23 and the L1641/L1647 sample to 188.

# Priors vs Posteriors

An evaluation of the consistency between the stellar parameters $M_*$, $R_*$, parallax, and $T_{\mathrm{eff}}$ (as listed in Tables [1](#table:parameters_serpens) and [\[table:parameters_SODA\]](#table:parameters_SODA) and used as priors in our modeling) and their corresponding posterior distributions (in Tables [2](#table: ANN_posteriors_Serpens_stellar) and [3](#tab: ANN_posteriors_SODA_stellar)) is performed to check for sources where our modeling suggests significant discrepancies with literature measurements. Figures [12](#fig: serpens_posteriors_priors) and [13](#fig: L1641_L1647_posteriors_priors) illustrate the comparison between existing literature measurements and the posterior probability distributions obtained via the ANN. As expected, the posterior distribution for the disks’ stellar parameters are in general consistent with literature measurements. This suggests that the literature values used as priors are not problematic, and our methodology allows us to incorporate the uncertainty on these stellar parameters in the posterior distributions of the disk parameters (cite: 2020Ribas).

![](FIGURE12.pdf)

![](FIGURE13.pdf)

[^1]: We remove the following eight objects from the Lupus sample adopted in (cite: 2023Rilinger) due to their uncertain membership: 2MASS J15450634-3417378 and 2MASS J16075475-3915446 are not detected in *Gaia* DR3; 2MASS J16070384-3911113 is detected in *Gaia* DR3 but has no parallax measurement; 2MASS J15560210-3655282, 2MASS J16030548-4018254, and 2MASS J16124373-3815031 have kinematics consistent with Lupus, but also Sco-Cen (cite: 2020Luhman), making their membership unlikely; 2MASS J15592523-4235066 has kinematics inconsistent with Lupus and instead indicative of Upper Centaurus–Lupus and Lower Centaurus–Crux; and Sz 90, which has *Gaia* DR2 astrometry that supports membership in Lupus, but *Gaia* DR3 data does not support it.

</paper>

Write the methods card for this paper.