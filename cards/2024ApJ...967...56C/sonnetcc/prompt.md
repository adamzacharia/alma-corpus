# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...967...56C\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...967...56C",
 "title": "Investigations of Massive Filaments and Star Formation (INFANT). I. Core Identification and Core Mass Function",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Cheng, Yu",
 "n_authors": 19,
 "arxiv_id": "2404.03858",
 "doi": "10.3847/1538-4357/ad3c41",
 "alma_projects_linked_by_archive": [
  "2017.1.00526.S"
 ]
}
```

Paper text:
<paper>
# INvestigations of massive Filaments ANd sTar formation (INFANT). I. Core Identification and Core Mass Function

## Abstract

Filamentary structures are ubiquitously found in high-mass star-forming clouds. To investigate the relationship between filaments and star formation, we carry out the INFANT (INvestigations of massive Filaments ANd sTar formation) survey, a multi-scale, multi-wavelength survey of massive filamentary clouds with ALMA band 3/band 6 and VLA K band. In this first paper, we present the ALMA band 6 continuum observations toward a sample of 8 high-mass star forming filaments. We covered each target with approximately rectangular mosaic field of view with two 12-m array configurations, achieving an angular resolution of $\sim$0$''$6 (2700 AU at 4.5 kpc) and a continuum rms of $\sim$0.1 mJy beam$^{-1}$($\sim$0.06 $M_\odot$ in gas mass assuming 15 K). We identify cores using the *getsf* and *astrodendro* and find the former is more robust in terms of both identification and measuring flux densities. We identify in total 183 dense cores (15–36 cores in each cloud) and classify their star formation states via outflow and warm gas tracers. The protostellar cores are statistically more massive than the prestellar cores, possibly indicating further accretion onto cores after formation of protostars. For the high-mass end ($M_\text{core}$ $>$ 1.5  $M_\odot$) of the core mass function (CMF) we derive a power-law index of $-$1.15 $\pm$ 0.12 for the whole sample, and $-$1.70 $\pm$ 0.25 for the prestellar population. We also find a steepening trend in CMF with cloud evolution ($-$0.89 $\pm$ 0.15 for the young group v.s. $-$1.44 $\pm$ 0.25 for the evolved group) and discuss its implication for cluster formation.

UTF8gbsn

# Introduction

Filamentary structures pervade the interstellar medium over a wide range of scales (cite: Hacar23). Within star-forming molecular gas, the presence of parsec-scale filamentary structures and their potential importance for star formation have been recognized for decades. Observations towards nearby clouds such as Taurus and Orion revealed prominent filamentary structures in spectral line and dust continuum emission (cite: Bally87; Abergel94). The Galactic wide surveys carried out with the *Herschel* Space Observatory have demonstrated the ubiquity of filaments throughout the Galactic plane (cite: Molinari10), and facilitated a detailed characterization of filaments in nearby clouds with characteristic length of a few parsecs and a width of $\sim$0.1 pc when observed at resolutions of the *Herschel* Space Telescope (cite: Andre10; Arzoumanian11; Arzoumanian19; Konyves20). When observed at high enough resolutions, these filaments are often shown to contain fibrous substructures, which are velocity coherent “fibres” with sub-parsec lengths, small characteristic widths of 0.02–0.1 pc, and (tran-)sonic velocity dispersions (cite: Hacar13; Hacar18; Fernandez-Lopez14; Schmiedeke21; Li22).

The relationship between filaments and star formation is still being intensively studied (cite: Andre14; Hacar23). In nearby clouds filaments make up more than 80% of the dense gas mass at $N_{H_2}$ $\rm >7\times 10^{21} cm^{-2}$ (cite: Arzoumanian19), and harbor most prestellar cores (cite: Konyves15; Konyves20). Fragmentation in filaments set the initial condition for the formation and evolution of cores, and may potentially regulate their mass distributions (cite: Andre19). Based on the Hi-GAL project (cite: Molinari10), (cite: Schisano14) found that cores with surface densities in excess of the expected critical values for high-mass star formation are only found on the filaments. The conjunction of several filaments, or a “hub”, where the density can be greatly enhanced, have been frequently observed to be the formation sites of high-mass stars or young clusters (cite: Myers09; Galvn10; Liu12a; Liu12; Kumar20). Many hub-filament systems appear to be highly dynamic, with converging longitude flows feeding their central hubs at a high accretion rate of order $10^{-4}$–$10^{-3}$  $M_\odot$ yr$^{-1}$(cite: Kirk13; Peretto13; Peretto14; Hacar17; Chen19; Sanhueza21; Zhou22).

While a significant step forward, our detailed knowledge of internal filament properties is still largely limited to the solar neighborhood. Systematic surveys to characterize massive filaments in distant high-mass star forming clouds are still rare. These filaments are likely different from their low-mass counterparts (cite: Lu18). Although a large number of high-mass star forming filaments have been catalogued (cite: Carey00; Wang16), high angular resolution studies that are able to resolve them down to dense cores scales $\lesssim$0.02 pc are mostly case studies (cite: Wang14; Zhang15; Li20). In light of this we carried out the INFANT (INvestigations of massive Filaments ANd sTar formation) survey, a multi-wavelength, multi-scale survey of 8 massive filamentary clouds with the Atacama Large Millimeter/submillimeter Array (ALMA) band 3/band 6 and Very Large Array (VLA) K band, aimed at investigating the relationship between filaments and star formation across a range of evolutionary stages. This first paper will focus on the ALMA band 6 continuum and properties of dense cores. The paper is organized as follows: a description of the sample and observations is given in [2](#sec:sample) and [3](#sec:observation), respectively; we then present the continuum map and core identification and characterization results in [4](#sec:results), followed by a comparison of the core extraction methods in [5](#sec:core_iden_comp). Further discussions are made in [6](#sec:discussion); and a summary is given in [7](#sec:summary).

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target | R.A. | Decl. | Distance$^{a}$ | $V_{\rm sys}$$^{a}$ | Luminosity$^{b}$ | Mass$^{b}$ | L/M$^{b}$ |
|  | (J2000) | (J2000) | (kpc) | (km s$^{-1}$) | ($10^4L_\odot$) | ($10^3$ $M_\odot$) | ($L_\odot$/ $M_\odot$) |
| IRAS 18308$-$0841 | 18:33:33.30 | $-$08:38:57.0 | 4.6 | 77 | $2.5_{-0.9}^{+0.7}$ | $2.7_{-0.7}^{+0.5}$ | $9.3_{-0.7}^{+0.8}$ |
| IRAS 18310$-$0825 | 18:33:47.60 | $-$08:23:50.0 | 4.8 | 84 | $2.9_{-1.1}^{+0.6}$ | $2.5_{-0.8}^{+0.4}$ | $11.6_{-0.3}^{+0.4}$ |
| IRAS 18337$-$0743 | 18:36:41.00 | $-$07:39:27.0 | 3.8 | 60 | $1.2_{-0.4}^{+0.3}$ | $2.5_{-0.5}^{+0.4}$ | $4.9_{-0.6}^{+0.5}$ |
| IRAS 18460$-$0307 | 18:48:38.30 | $-$03:03:53.0 | 4.8 | 85 | $1.1_{-0.3}^{+0.2}$ | $1.5_{-0.4}^{+0.4}$ | $7.6_{-0.2}^{+0.2}$ |
| IRAS 18530$+$0307 | 18:55:32.70 | $+$02:19:03.0 | 4.6 | 76 | $2.9_{-0.6}^{+0.6}$ | $2.6_{-0.7}^{+0.5}$ | $11.2_{-0.1}^{+0.5}$ |
| IRAS 19074$+$0752 | 19:09:54.00 | $+$07:57:15.0 | 3.8 | 56 | $0.7_{-0.1}^{+0.1}$ | $0.6_{-0.2}^{+0.1}$ | $11.4_{-0.5}^{+0.8}$ |
| IRAS 19220$+$1432 | 19:24:21.00 | $+$14:38:08.0 | 5.4 | 70 | $1.7_{-0.3}^{+0.3}$ | $1.3_{-0.2}^{+0.2}$ | $12.7_{-0.1}^{+0.3}$ |
| IRAS 19368$+$2239 | 19:38:58.20 | $+$22:46:44.0 | 4.4 | 37 | $0.3_{-0.1}^{+0.1}$ | $1.6_{-0.4}^{+0.3}$ | $2.1_{-0.1}^{+0.1}$ |

: Summary of the INFANT sample

Table notes: $^{a}$ Taken from (cite: Lu18). $^{b}$ Estimated from *Herschel* SED fitting. The uncertainties refer to the variation when the region selected for calculation varies by 30% in area.

# Sample

The eight clouds in this survey have been previously studied with the Submillimeter Array (SMA) (cite: Lu18). They are carefully selected from a VLA $\rm NH_3$ survey toward 62 high-mass star-forming regions in (cite: Lu14) with the following criteria (cite: Lu18):

1.  The VLA $\rm NH_3$ emission exhibits filamentary structures with aspect ratios of $>$5 in the moment 0 map.

2.  They are luminous ($\gtrsim$ 5$\times$10$^3$ $L_\odot$) and massive ($\gtrsim$ 10$^3$ $M_\odot$), with sufficient mass reservoir for high-mass star formation. The only exception is IRAS 19074$+$0752, which is associated with an H ii region and its molecular gas has been largely consumed or dispersed, leading to a smaller mass. It is included here as a representative for a protocluster in a much more evolved environment.

3.  The distances of the eight targets range from 3.8 to 5.4 kpc, thus enabling a relatively uniform spatial resolutions in a single observational setup.

The properties of the targets are listed in [1](#table:info_sample). We take the distance and systematic velocity from (cite: Lu18). We revised the estimation of masses and luminosities based on spectral energy distribution (SED) fitting of *Herschel* data from 70 $\mu$m to 500 $\mu$m, as described in [8](#sec:app_sed). We find that the resulting masses or luminosities largely depend on how the region is defined. Thus we give a typical range by calculating the limits when the region area varies by 30%. For the fiducial case we adopt the boundary defined by the primary beam correction equal to 0.5 in our ALMA band 6 observations, which are designed to cover the $\rm NH_3$ emission and SMA 1.3 mm continuum in (cite: Lu14) and (cite: Lu18).

(cite: Lu18) identified and characterized 50 massive dense cores in these clouds with the SMA and revealed a strong relationship between filaments and high-mass star formation, through (i) filamentary fragmentation in very early evolutionary phases to form dense cores, (ii) accretion flows along filaments that are important for the growth of dense cores and protostars, and (iii) enhancement of nonthermal motion in the filaments by the feedback or accretion during star formation. Nevertheless, the SMA observations had relatively limited spatial resolution ($\sim$3$''$) and sensitivity ($\sim$1 mJy beam$^{-1}$) and hence were unable to probe low to intermediate mass dense cores ($\lesssim$5  $M_\odot$) and further fragmentation on $\lesssim$0.05 pc scales.

# Observations

## ALMA band 6 observations

The observations were conducted with ALMA in Cycle 5 (Project ID 2017.1.00526.S, PI: Lu, X.), over a period from 2018 March to 2018 August. All the targets were observed at band 6 using two 12-m array configurations, i.e., C43-1 and C43-4. This combination allows us to achieve a spatial resolution of $\sim$0$''$6 (2700 au at a typical distance of 4.5 kpc) and the maximum recoverable angular scales of 12$''$4 ($\sim$0.27 pc at 4.5 kpc). We covered each cloud using 30 to 40 mosaic fields in the C43-1 and C43-4 array configurations, respectively. For each source the on source time is at least 8 minutes in C43-1 and 20 minutes in C43-4. The detailed information, including the baseline ranges, numbers of effective antennas, and weather conditions, is listed in [2](#table:info_obs).

We set the central frequency of the four correlator sidebands to be 218.500, 217.100, 230.438, 231.420 GHz, respectively. Each baseband has a bandwidth of 937.5 MHz and a uniform spectral resolution of 0.488 MHz. This allows for an aggregate bandwidth of 3.75 GHz and also covers lines including $\rm H_2CO~(3_{0,3}-2_{0,2})$, $\rm H_2CO~(3_{2,2}-2_{2,1})$, $\rm H_2CO~(3_{2,1}-2_{2,0})$, $\rm SiO~(5-4)$, $\rm CO~(2-1)$, and $\rm N_2D^+~(3-2)$, with a velocity resolution of 0.63 – 0.67 km s$^{-1}$.

The raw data were calibrated with the data reduction pipeline using CASA 5.4.0 (cite: Mcmullin07). We constructed the continuum visibility with all line-free channels. The effecitve aggregated continuum bandwidth is typically 70%–85% of our overall bandwidth for different sources. The imaging was carried out using CASA 6.5.0. We used the tclean task in CASA, with Briggs weighting and a robust parameter of 0.5, and a multiscale algorithm with scales of \[0, 5, 15, 50\] and a pixel size of 0$''$15. The resultant synthesized beam size and root mean square (rms) noise of the 1.3 mm continuum for each target are listed in [3](#table:info_cont). The angular resolutions are 0$''$5 – 0$''$7, while the rms noise ranges from 0.06 to 0.12 mJy beam$^{-1}$.

| Schedule block | Sources | Configuration | Execution date | Number of effective antennas | Baseline | PWV(mm) | Time on source (min)$^{a}$ |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| I18308_TM1 | I18308, I18310, I18337 | C43-4 | 2018-03-13 | 40 | 14m–783m | 1.79 | 37 |
|  |  |  | 2018-03-16 | 41 | 14m–783m | 1.92 | 37 |
| I18308_TM2 | I18308, I18310, I18337 | C43-1 | 2018-06-09 | 41 | 14m–313m | 1.02 | 37 |
| I19220_TM1 | I19220, I19368 | C43-4 | 2018-03-11 | 41 | 14m–919m | 0.57 | 37 |
|  |  |  | 2018-03-11 | 42 | 14m–783m | 1.93 | 37 |
|  |  |  | 2018-08-28 | 44 | 14m–781m | 1.16 | 37 |
|  |  |  | 2018-08-29 | 44 | 14m–781m | 1.39 | 37 |
| I19220_TM2 | I19220, I19368 | C43-1 | 2018-06-09 | 48 | 14m–313m | 1.11 | 20 |
| I19074_TM1 | I19074 | C43-4 | 2018-03-22 | 46 | 14m–783m | 1.03 | 22 |
| I19074_TM2 | I19074 | C43-1 | 2018-06-06 | 45 | 14m–313m | 0.68 | 8 |
| I18460_TM1 | I18460, I18530 | C43-4 | 2018-03-16 | 41 | 14m–783m | 1.80 | 40 |
| I18460_TM2 | I18460, I18530 | C43-1 | 2018-06-09 | 49 | 14m–313m | 1.14 | 20 |

: Summary of the ALMA band 6 observations

Table notes: $^{a}$ Time on source is the time per exception block (EB) that is distributed among the different science targets in the EB.

## VLA K band observations

The VLA observations were performed in the C and D configurations, respectively, under the project codes of 20A-405 and 21A-210 (PI: Y. Cheng). The correlator setup included 16 128-MHz-wide spectral windows to cover continuum emission with a total bandwidth of 2 GHz, as well as narrow spectral windows to cover the metastable $\rm NH_3$ lines from ($J$,$K$) = (1,1) to (5,5), the H$_2$O maser line, four non-metasable $\rm NH_3$ lines, as well as several other lines that will be discussed in a future publication. Here we only focus on the $\rm NH_3$ ($J$,$K$) = (1,1) and (2,2) lines.

The data were manually calibrated using CASA 5.6.1 and 6.2.0. Continuum baseline was estimated by fitting a linear function to the visibility data including only line-free channels along the frequency axis. The data were also binned by two channels, to achieve a velocity resolution of 0.4 km s$^{-1}$. Then, the two datasets from the two array configurations were concatenated and imaged, using CASA 5.7.2. We used the *tclean* task in CASA, with Briggs weighting and a robust parameter of 0.5, and a multiscale algorithm with scales of \[0, 5, 15, 50, 150\] and a pixel size of 0$''$2. The synthesized beam sizes are different among targets and lines, but are 1$''$2 $\times$ 1$''$0 in general. The rms noise in the 0.4 km s$^{-1}$ channel ranges from 1.3 to 1.5 mJy beam$^{-1}$ (2.4–2.7 K).

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target | Synthesized beam | Physical resolution | RMS | Mass sensitivity | $M_{\rm complete}$ | $M_{\rm max}$ | $N_{\rm core}$ | $N_{\rm pre}$ | $N_{\rm proto}$ | $N_{\rm outflow}$ |
|  | ($''$$\times$$''$) | (AU) | (mJy beam$^{-1}$) | ( $M_\odot$) |  $M_\odot$ |  $M_\odot$ |  |  |  |  |
| I18308 | 0.71$\times$0.59 | 2840 | 0.12 | 0.08 | 0.89 | 37.6 | 22 | 7 | 15 | 9 |
| I18310 | 0.71$\times$0.60 | 2870 | 0.10 | 0.06 | 0.73 | 9.7 | 27 | 19 | 8 | 2 |
| I18337 | 0.72$\times$0.59 | 2870 | 0.12 | 0.07 | 0.52 | 17.0 | 36 | 21 | 15 | 10 |
| I18460 | 0.74$\times$0.67 | 3110 | 0.11 | 0.07 | 0.71 | 9.3 | 15 | 9 | 6 | 4 |
| I18530 | 0.75$\times$0.71 | 3210 | 0.12 | 0.08 | 0.79 | 12.9 | 35 | 21 | 14 | 9 |
| I19074 | 0.60$\times$0.58 | 2600 | 0.08 | 0.05 | 0.53 | 4.8 | 15 | 9 | 6 | 3 |
| I19220 | 0.53$\times$0.51 | 2300 | 0.06 | 0.04 | 0.79 | 4.2 | 17 | 13 | 4 | 3 |
| I19368 | 0.68$\times$0.58 | 2770 | 0.10 | 0.06 | 0.71 | 6.8 | 16 | 9 | 7 | 3 |

: Summary of the 1.3 mm continuum and core detection

Table notes: The mass sensitiviey is calculated assuming a temperature of 15 K. $M_{\rm complete}$ refers to the mass for which the detection for a point source is 90% complete as estimated by the artificial core insertion experiment. $M_{\rm max}$ is the maxium core mass. $N_{\rm outflow}$ refers to the number of cores that are associated with molecular outflows. $N_{\rm proto}$ refers to the number of cores that are associated with molecular outflows or compact feature in warm core tracers (including $\rm H_2CO$ ($3_{2,2}-2_{2,1}$), ($3_{2,1}-2_{2,0}$) or $\rm CH_3OH$ ($4_{2,2}-3_{1,2}$). $N_{\rm pre}$ indicates number of cores that are absent in both outflows and warm core tracers.

![](fmap_cont.pdf)

# Results

## Dust Continuum Emission

In [1](#fig:cont) we present the ALMA 1.3 mm continuum maps of the INFANT sample. Overall ALMA recovers 18%–36% of the total flux densities measured with IRAM 30m telescope/MAMBO bolometer array at 1.2 mm (cite: Beuther02). We have scaled the MAMBO fluxes by $(\nu_{\rm eff,ALMA}/\nu_{\rm eff,MAMBO})^4$ to account for the slightly different effective frequencies, i.e., assuming optically thin thermal emission and an opacity law for the dust emission of $\kappa \sim v^2$ (cite: Ossenkopf94). This fraction reflects different levels of dense gas concentration at smaller scales ($<$12$''$, or $\sim$0.25 pc) among the sample.

As discussed in [2](#sec:sample), the sample is selected based on an extended morphology in $\rm NH_3$ moment 0 maps. These sources appear to retain similar filamentary emission in the high resolution ALMA 1.3 mm maps, e.g., I18308, I18337, and I19368 being the best examples. In some cases the dust continuum emission does not present prominent filamentary morphology as seen in $\rm NH_3$ in (cite: Lu18), likely due to spatial filtering effect. For example, I18460 appears as a couple of sparsely distributed dense cores, although these cores are still embedded and connected with relatively diffuse emissions.

## Core Identification

We employ the *getsf* method to identify and extract properties of dense cores from the 1.3 mm continuum images. A comparison of the performance of *getsf* and another commonly used algorithm *astrodendro* is further discussed in [5](#sec:core_iden_comp). *Getsf* is a method for extracting sources and filaments in astronomical images based on separation of multiscale structural components (cite: Men21). In this algorithm the relatively round sources and elongated filaments are separated from each other and from the background. In this work we focus on dense cores, i.e., the sources returned by *getsf*. This method has a single free parameter, i.e., the maximum size of the sources to be extracted, for which we adopt 10$''$, i.e., $\sim$0.2 pc at a typical distance of 4.5 kpc. The core identification is based on maps that are not corrected for primary beam response; the fluxes returned by *getsf* are corrected by the beam response factor for further analysis.

[2](#fig:map_iden) shows examples of the identification results towards I18308 and I18337. *Getsf* returns an estimation of source sizes and flux densities, as listed in [4](#table:info_core). The final catalogue includes 183 cores that pass the recommended optimal selection criteria based on benchmark tests (equation 1 in (cite: Men21b)), including an aspect ratio lower than 2, peak and integrated flux signal-to-noise ratios above 2, etc. The core numbers for different targets in our sample range from 15 to 36, with a median of 21. I18460 and I19074 has the smallest number of cores (15), while I18337 has the largest core number of 36.

To estimate the completeness level, we run experiments of artificial core insertion by generating artificial cores of certain flux densities, randomly putting them in the original image, and running *getsf* again to check whether they can be picked out. For simplicity, the artificial cores are assumed to have the same shape as the synthesized beam, i.e., the limiting case appropriate for small, unresolved cores. In each experiment, we insert 10 cores of a given total flux, and repeat this for 10 times. The results are shown in [3](#fig:complete). The 90% completeness levels range from 0.8 to 1.3 mJy, i.e., around 10 $\times$ overall image rms as listed in [3](#table:info_cont).

## Properties of dense cores

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Region | Index | $\alpha$(J2000) | $\delta$(J2000) | $\rm FWHM$ | PA | Flux Density | Mass | $T_{\rm NH_3}$ | $\sigma_{\rm NH_3}$ | outflow | pre/proto |
|  |  | (hh:mm:ss) | (dd:mm:ss) | ($''$$\times$$''$) | ($^{\circ}$) | (mJy) | ( $M_\odot$) | \(K\) | (km s$^{-1}$) |  |  |
| I18308 | 1 | 18:33:33.16 | $-$08:39:15.0 | 0.96$\times$0.64 | 84 | 90.7 | 37.61 | 21.7$\pm$0.9 | 1.07$\pm$0.04 | outflow | protostellar |
| I18308 | 2 | 18:33:34.29 | $-$08:38:43.0 | 0.74$\times$0.63 | 90 | 25.3 | 24.81 | 11.7$\pm$0.8 | 0.57$\pm$0.04 | outflow | protostellar |
| I18308 | 3 | 18:33:33.27 | $-$08:39:16.0 | 1.58$\times$1.17 | 127 | 20.1 | 9.40 | 19.8$\pm$0.6 | 0.82$\pm$0.03 | no outflow | protostellar |
| I18308 | 4 | 18:33:32.95 | $-$08:39:04.0 | 1.59$\times$1.33 | 31 | 16.1 | 13.19 | 13.2$\pm$0.6 | 0.54$\pm$0.03 | no outflow | protostellar |
| I18308 | 5 | 18:33:33.10 | $-$08:38:59.0 | 1.24$\times$1.21 | 177 | 11.3 | 10.69 | 12.0$\pm$0.4 | 0.45$\pm$0.03 | outflow | protostellar |
| I18308 | 6 | 18:33:33.47 | $-$08:38:46.0 | 0.74$\times$0.64 | 90 | 9.9 | 5.76 | \- | \- | outflow | protostellar |
| I18308 | 7 | 18:33:32.70 | $-$08:39:14.0 | 2.79$\times$2.02 | 128 | 9.8 | 5.85 | 16.5$\pm$0.7 | 0.62$\pm$0.03 | no outflow | prestellar |
| I18308 | 8 | 18:33:34.35 | $-$08:38:42.0 | 0.86$\times$0.68 | 82 | 7.9 | 4.58 | \- | \- | no outflow | protostellar |
| I18308 | 9 | 18:33:33.07 | $-$08:39:15.0 | 0.88$\times$0.82 | 58 | 6.9 | 2.98 | 21.1$\pm$1.0 | 1.02$\pm$0.04 | outflow | protostellar |
| I18308 | 10 | 18:33:32.52 | $-$08:39:09.0 | 0.91$\times$0.72 | 97 | 6.1 | 2.35 | 23.0$\pm$1.6 | 0.67$\pm$0.04 | outflow | protostellar |
| I18308 | 11 | 18:33:32.39 | $-$08:39:09.0 | 0.94$\times$0.69 | 103 | 6.0 | 3.01 | 18.7$\pm$1.1 | 0.36$\pm$0.02 | outflow | protostellar |
| I18308 | 12 | 18:33:33.14 | $-$08:39:13.0 | 1.07$\times$0.84 | 130 | 5.5 | 2.66 | 19.2$\pm$0.9 | 0.84$\pm$0.04 | no outflow | prestellar |
| I18308 | 13 | 18:33:33.26 | $-$08:38:54.0 | 1.17$\times$1.00 | 100 | 4.8 | 5.31 | 10.9$\pm$0.4 | 0.28$\pm$0.02 | no outflow | prestellar |
| I18308 | 14 | 18:33:32.97 | $-$08:39:08.0 | 1.67$\times$1.49 | 95 | 4.4 | 2.88 | 15.3$\pm$0.9 | 0.43$\pm$0.03 | no outflow | prestellar |
| I18308 | 15 | 18:33:34.27 | $-$08:38:41.0 | 0.88$\times$0.67 | 134 | 3.9 | 3.68 | 11.9$\pm$0.8 | 0.57$\pm$0.04 | outflow | protostellar |
| I18308 | 16 | 18:33:33.18 | $-$08:39:17.0 | 1.04$\times$0.76 | 74 | 3.7 | 2.13 | 16.8$\pm$0.7 | 0.80$\pm$0.03 | no outflow | prestellar |
| I18308 | 17 | 18:33:32.82 | $-$08:39:17.0 | 1.10$\times$0.86 | 89 | 3.0 | 1.45 | 19.0$\pm$1.3 | 0.47$\pm$0.03 | no outflow | protostellar |
| I18308 | 18 | 18:33:32.98 | $-$08:39:06.0 | 1.03$\times$0.98 | 7 | 2.8 | 2.41 | 12.9$\pm$0.6 | 0.58$\pm$0.03 | no outflow | prestellar |
| I18308 | 19 | 18:33:32.93 | $-$08:39:17.0 | 0.99$\times$0.81 | 103 | 2.8 | 1.01 | 24.4$\pm$1.8 | 0.60$\pm$0.04 | no outflow | protostellar |
| I18308 | 20 | 18:33:33.05 | $-$08:39:18.0 | 1.33$\times$0.86 | 99 | 2.5 | 1.23 | 19.0$\pm$1.5 | 0.79$\pm$0.06 | no outflow | protostellar |
| I18308 | 21 | 18:33:34.22 | $-$08:38:32.0 | 0.77$\times$0.65 | 72 | 1.9 | 1.13 | \- | \- | no outflow | prestellar |
| I18308 | 22 | 18:33:31.56 | $-$08:39:01.0 | 0.96$\times$0.76 | 91 | 1.3 | 1.24 | 12.2$\pm$1.0 | 0.48$\pm$0.04 | outflow | protostellar |

: Core properties extracted by *getsf*

Table notes: Table 4 is published in its entirety in the machine-readable format. Results for I18308 are shown here for guidance regarding its form and content.

We estimate gas temperatures of the cores with the VLA $\rm NH_3$ (1,1) and (2,2) lines following the routine in (cite: Lu18). A full account of the VLA observations will be published in other papers in the series. In summary, for each core we extract the average $\rm NH_3$ (1,1) and (2,2) spectra within the FWHM returned by *getsf* and model the spectra assuming local thermodynamic equilibrium (LTE) conditions. We require a line detection $>$4 $\sigma$ for $\rm NH_3$ (1,1) and $>$2.5 $\sigma$ for (2,2) for the fitting, and 125 cores out of 183 satisfy this criterion. The free parameters in the fit are the core velocity, rotational temperature, $\rm NH_3$ column density, and velocity dispersion (see [9](#sec:app_nh3)). During the fitting we assume a uniform filling factor of 1 for all transitions and hyperfine components. As illustrated in [4](#fig:Tgas), the measured $T_\mathrm{NH_3}$ ranges from 9.9 to 32.2 K, with a median of 16.5 K. The distribution for each region also varies. I18308, I18310, I18337, and I19220 have a lower median $T_\mathrm{NH_3}$ of 14–17 K, while I18460, I18530, I19074, and I19368 show a higher median $T_\mathrm{NH_3}$ of 22–23 K.

The core mass is then estimated assuming that the emission purely comes from optically thin isothermal dust emission, enabling us to use the equation $$\begin{equation}
    M_{\rm dust} = \frac{d^2F_\nu}{\kappa_\nu B_\nu (T_{\rm dust})}.
\end{equation}$$ where $d$ is the distance to the source, $F_\nu$ is the observed flux density, $B_\nu$ is the Planck function, $T_{\rm dust}$ is the dust temperature and $\kappa_\nu$ is the dust opacity at the observed frequency $\nu$. We adopt $\kappa_{\rm 1.3 mm}$ = 0.899 $\rm cm^2g^{-1}$ from (cite: Ossenkopf94) (thin ice mantles, $\rm 10^6~cm^{-3}$ density). We multiply the calculated dust mass by 100, assuming a dust-to-gas mass ratio of 1:100 (cite: Bohlin78), to obtain the gas mass. In the absence of high resolution dust temperature measurements, we adopt the gas temperature derived with $\rm NH_3$. For those without valid $\rm NH_3$ temperature measurements due to insufficient signal to noise ratio, we adopt the median $\rm NH_3$ temperature for each region.

The determination of the evolutionary stages of dense cores, i.e., prestellar or protostellar, is essential to study their accretion history and interpret the observed mass distribution of core populations. This is, however, a difficult task in distant massive protoclusters. We first search for molecular outflows using CO 2–1, SiO 5-4 as well as SO, $\rm H_2CO$ and $\rm CH_3OH$ lines, and classify the associated dense cores as protostellar (Cheng et al. in prep.). Forty-three cores (43/183) are found to host evident molecular outflows. This is most likely a lower limit of protostellar cores since we will miss outflows orientated close to the plane of sky, and the outflow emission is often blended and confused in clustered environments. In light of this we follow (cite: Sanhueza19) and complement the identification of star forming cores by searching for associated line emission from “warm core” tracers, i.e., two $\rm H_2CO$ warm transitions ($3_{2,2}-2_{2,1}$) (218.475632 GHz, $E_u/k$=68.09 K), ($3_{2,1}-2_{2,0}$) (218.760066 GHz, $E_u/k$=68.11 K) and $\rm CH_3OH$ ($4_{2,2}-3_{1,2}$) (218.440063 GHz, $E_u/k$=45.56 K). Cores detected in these lines are likely to have been internally heated from star formation activities and hence they can be used as a star formation indicator. In practice we examine both the morphology of the integrated line emission and the spectra for each core within the FWHM returned by *getsf*. If a peak above 4 $\sigma$ is found in any of the three spectral lines, and the emission has a centrally peaked compact morphology associated with dense cores, we define it as a warm core. This criterion gives 70 warm cores, of which 38 cores are also associated with outflows. Cores that are absent in both molecular outflows and warm core tracers are then classified as prestellar candidates. In summary, out of 183 cores in our sample, 108 are prestellar candidates and 75 cores are protostellar, including those identified by outflows (43/75) and warm core tracers (70/75). The fraction of prestellar cores significantly vary among the sample, with I18308 hosting a lowest fraction of prestellar population of 32% (7/22) and I19220 a highest fraction of 76% (13/17).

[4](#fig:Tgas) also reveals the difference in gas temperature of cores in the two populations. Overall the protostellar cores have a higher median $\rm T_{NH_3}$ of 17.5 K, compared to 15.8 K for the prestellar candidate cores. The $\rm T_{NH_3}$ distribution of both prestellar and protostellar cores appear to exhibit a bimodal shape, with one peak around 13 K and the other around 22 K, but the prestellar population has more cores in the lower temperature regime.

# Comparison of core identification algorithms: *getsf* v.s. *astrodendro*

Since the core identification results lay the foundation for further analysis of properties of the core population, it is necessary to review the algorithms adopted for core extraction. Cores, i.e., self-gravitating entities of gas and dust, usually manifest as local peaks in 2-D continuum or column density maps. There is a plethora of core extraction algorithms used in the literature, e.g., *gaussclump* (cite: Stutzki90), *clumpfind* (cite: Williams94), *astrodendro* (cite: Rosolowsky08), *blobcat* (cite: Hales12), *fellwalker* (cite: Berry15), and *getsf* (cite: Men21), etc. A complete assessment of the performance of all these algorithms is clearly beyond the scope of this paper. In this section we compare the performance of *getsf* and *astrodendro* in detecting and extracting properties of cores. Both are very widely used in the literature: *astrodendro* is designed for identifying hierarchical structures in continuum or line data (cite: Ginsburg16; Sanhueza19; ONeill21; Takemura22). *getsf* (or its predecessor algorithms *getsources*, *getfilaments*, and *getimages*, (cite: Menshchikov12; Menshchikov13; Menshchikov17)), is the fiducial method in this paper and also commonly used in other works for multi-scale multi-wavelength source-extraction, including the ALMA-IMF large program survey (cite: Motte22; Pouteau22). Therefore, when putting in context the statistical analysis of the INFANT core population, e.g., the core mass function, it is important to understand the systematic differences that may arise from different methodologies.

In [2](#fig:map_iden) we show the core identification results for I18308 and I18337 using both *dendrogram* and *getsf* methods. The same plot for other regions are shown in [12](#sec:app_comp_method). For *getsf* the setup is described in [4.2](#sec:core_iden). For *dendrogram* we set the base flux density threshold to 4$\sigma$, the minimum significance for structures to 1$\sigma$, and the minimum area to half the synthesized beam. This choice of parameter setup has been used and works reasonably well in a series of CMF works (cite: Cheng18; Liu18; ONeill21).

Inspection of the image allows one to assess how different algorithms operate on the imaging data. *astrodendro* appears to identify more cores compared to *getsf*. While most bright, high contrast cores are identified in both methods, *astrodendro* also includes some relatively weak cores that often exhibit irregular boundaries, which are not picked up by *getsf*. In fact for all the eight clouds *astrodendro* returns a total of 382 cores, about twice the core number by *getsf*. Another feature is that for the brightest and most massive cores *getsf* tends to return more fragments.

To quantitatively evaluate the performance of the two algorithms, we run experiments of artificial core insertion. This is the same as done in [4.2](#sec:core_iden) for *getsf* but here we check the detection rate and also recovery of core fluxes for both algorithms. The number recovery is shown in [5](#fig:complete_comp). If the artificial cores are randomly inserted in the original image (i.e., 50% primary beam response, the same criterion with which we identify cores), the 90% completeness limit is estimated to be 1.5 mJy (or S/N = 12.5) for *astrodendro*, and 1.2 mJy (S/N = 9.8) for *getsf*. Therefore, *getsf* is slightly more efficient than *astrodendro* in detecting weak sources.

We also test the case with artificial cores restricted to the spatial range defined by a flux density threshold, e.g., $\sim$1 mJy beam$^{-1}$ level, which means they preferably show up in crowded environments. Blending and confusion make it more challenging to pick up cores. The 90% completeness limit increases to be 2.1 mJy (S/N = 17.7) for *astrodendro* and 1.9 mJy (S/N = 15.5) for *getsf*. It is worth noting that for *astrodendro* the detection completeness for low S/N ($\sim$2–6) cores is significantly higher than that in the random insertion case. By definition a local peak has to be greater than 5$\sigma$ in order to be identified by *astrodendro* with our parameter setup. The enhanced detection fraction for low S/N (2–6) cores reflects the fact that these cores lie on strong background emission in clustered regions, thus having a larger ($>5\sigma$) peak value, and *astrodendro* does not distinguish the large scale emission from the locally condensed structures. This also partly explains why *astrodendro* returns much more cores than *getsf* while having a larger 90% completeness limit flux in the random insertion case. We do not take this as a merit for *astrodendro* (in terms of core identification) since the detection of cores in isolation or crowded fields (with strong large scale emission) may essentially have been treated with different significance threshold, and the false detection rate could also be elevated when background emission is strong. For example, artificial fragments/substructures with low or moderate S/N could be produced when a smooth flux distribution is observed with interferometers (cite: Hodge16; Caselli19).

In [6](#fig:complete_flux_comp) we show how well the core fluxes are recovered with two methods. *astrodendro* is an algorithm based on pixel assignment, and the flux of a leaf is the sum of fluxes in all leaf pixels in an isophotal boundary defined by input base value (in case of an isolated leaf). When this flux is directly interpreted as the core flux, there will be two factors that lead to deviation from the true value. First, pixels below the base level (4 $\sigma$) are not assigned to any core structures, rendering the core flux underestimated. This underestimation fraction is greater for lower flux cores, which is analytically tractable for point sources with peak flux density $f_{\rm peak}$, $$\begin{equation}
\label{equ:reco}
\frac{F_{\rm measure}}{F_{\rm true}} = 1-\frac{f_{\rm base}}{f_{\rm peak}},
\end{equation}$$ where $f_{\rm base} = 4\sigma$ is our case. This type of flux underestimation is dominating in the random insertion case for *astrodendro*, as illustrated in panel (a) of [6](#fig:complete_flux_comp). On the other hand, the pixels assigned to a leaf structure may well contain fluxes contributed by larger scale emission, especially in clustered regions. As seen in panel (b), this effect will result in a systematically higher measured flux and also a larger scattering since the measured values are dependent on emission level of the background, which often varies in different locations. In comparison, the fluxes returned by *getsf* are in general more robust and show less scattering.

In summary, *getsf* has a better treatment of the varying background levels in identification of dense cores, and gives more robust flux measurements. Cautions should be made when directly interpreting the leaf structures given by *astrodendro* as cores. Note that the comparison here only concerns the performance of algorithms in detecting point-like sources in a 2-D map. In principle, it is likely that these 2-D cores do not always correspond to real physical dense cores when taking account the effects of projection and other observational complications (radiative transfer effects, interferometric artifacts, instrumental noise, etc.) (cite: Padoan23). Hereafter the discussion on the INFANT core population is based on the core catalog with the *getsf* method, but we also discuss in [12](#sec:app_comp_method) about the potential influence on the statistical results if *astrodendro* is used, such as the core mass function (CMF).

# Discussion

## Evolutionary status of the protocluster

Complete census of dense cores in protoclusters requires high sensitivity and high spatial resolution observations covering a large area ($\gtrsim$1 pc$^2$) and being able to resolve the cloud down to a few 1000 au scale at the same time. Even in the ALMA era, large sample surveys of protoclusters that could achieve statistically significant conclusion are still challenging. Surveys to date include ASHES (cite: Sanhueza19), ALMA-IRDC (cite: Barnes21), and ALMA-IMF (cite: Motte22), etc.

Different from surveys that focuses on the very early evolutionary stages in infrared dark clouds, our INFANT survey covers a range of evolutionary phases. Overall our targets are more evolved compared to the 70 $\mu$m dark clouds in (cite: Sanhueza19) given the overall higher luminosity and the fact that all the targets already host bright point sources in the near- and mid infrared (see [8](#sec:app_sed)), indicating ongoing protostellar activities. But still a significant portion of the cloud can be dark at wavelengths up to 24 $\mu$m, i.e., for I18308, I18310, I18337, I18460, or 8 $\mu$m for I18530 and I19220, where the star formation has not yet begun or is still in an early phase. This is expected as a parcsec scale cloud may well contain star formation sites in various stages. In I18530, 19074 and I19220, compact 1.3 cm continuum emission is detected (Cheng et al. in prep.), suggesting the protostars have evolved into the ultracompact (UC) H II region phase. An even more evolved phase is found in I19074, where a parsec-scale H II region traced by an infrared bubble is detected ((cite: Churchwell06), see also (cite: Lu18)), thus the observed dust/gas content could be the adjacent material compressed by the HII region and/or the remnant after the cloud complex has been destructed by feedback.

In [1](#table:info_sample) we have listed the luminosity-to-mass ratio $L/M$, which is often used as a proxy for the evolution of parsec scale clumps (cite: Ma13; Liu16; Molinari16). More evolved sources in general produce more infrared emission and have consumed more gas material, thus leading to higher luminosity-to-mass ratios. The mass and luminosity are derived with the temperature and column density map from *Herschel* SED fitting (see [8](#sec:app_sed)), and the measurement is made for the spatial range used for ALMA imaging. The $L/M$ ratios range from 2.1 $L_\odot/M_\odot$ (I19368) to 12.7 $L_\odot/M_\odot$ (I19220). According to this ratio, the sample can be roughly divided into two groups, i.e., I19368, I18337, I18460, I18308 that are in a relatively early stage, while I18310, I18530, I19220 and I19074 that are relatively evolved. This is broadly consistent with other evolution indicators such as infrared emission, and UCH II/HII regions.

Two exceptions are I19368 and I18310. The I19368 region has the lowest $L/M$ ratio, but widespread protostellar activity is seen in the infrared images. I18310 is included in the more evolved group, but part of the cloud is still infrared dark for wavelengths up to 24 $\mu$m. This may reflect the limitation of $L/M$ as an evolution indicator for a parsec-scale cloud, especially when the difference in $L/M$ is not significant. For example, a newly formed high mass young stellar object could rapidly boost the observed $L/M$ considering a typical luminosity–mass relation for main sequence stars (cite: Eker15). Therefore, the relatively low $L/M$ of I19368 compared to other regions, but widespread infrared emission, may arise from a lack of high mass young stars in this region. Since the $L/M$ indicator alone is subject to the inherent stochasticity of the sampling of protostellar masses across the star forming cloud, we only consider sources with consistent evolution classifications using either $L/M$ and other evolution indicators for following discussions, i.e., the young group includes I18308, I18337 and I18460; and the evolved group includes I18530, I19074 and I19220.

## Absence of high-mass prestellar core and mass growth of cores

| Sample | 1.3 mm Flux density |  | Mass |  |
|:---|:--:|:--:|:--:|:--:|
| (All)         prestellar v.s. protostellar | 1.5$\times10^{-8}$ |  | 4.0$\times10^{-7}$ |  |
| (Young)    prestellar v.s. protostellar | 5.0$\times10^{-5}$ |  | 1.4$\times10^{-4}$ |  |
| (Evolved) prestellar v.s. protostellar | 3.6$\times10^{-3}$ |  | 4.7$\times10^{-3}$ |  |

: Mann-Whitney U test for comparison between core populations $^{a}$

Table notes: $^{a}$ $p$ values of the Mann-Whitney U test (cite: Mann47) for the samples for a single-sided (less) test, i.e., the null hypothesis is that the protostellar flux/mass is equal or smaller than that of the prestellar population.

Theories to explain high mass star formation can be broadly categorized into “core-fed” and “clump-fed”, each predicting distinct initial conditions and spatial scales for the mass reservoir that serves as the source for accretion (cite: Wang10). One way to test different formation theories is to characterize the initial conditions, and in particular, to examine whether there exist high mass, gravitationally bound, pre-stellar cores as predicted by the core accretion theories (cite: Mckee03). A handful of candidates have been identified (cite: Cyganowski14; Kong18; Barnes23), but none of them has been confirmed as bona-fide high-mass prestellar cores. In this survey the most massive prestellar core, namely c2 in I18337, has a mass of only $\sim$10.3  $M_\odot$, and in other regions the most massive prestellar core are all below 10  $M_\odot$. Even when adopting a high core-to-star efficiency of 50% (cite: Tanaka17), and assuming no multiplicity, a core with an initial mass of approximately 16  $M_\odot$ is necessary to give rise to an 8  $M_\odot$ star. Thus, there are no high-mass prestellar cores in this survey. This negative outcome is similar to those found in other surveys (cite: Sanhueza19; Mori23), suggesting that high-mass prestellar cores, if they do exist, are very rare.

A possible scenario to form massive stars without invoking a high-mass prestellar core entails substantial growth in core mass after their initial formation. To investigate this scenario we compare the mass distribution of the prestellar and prostellar core populations. [7](#fig:comp_mass)(a) shows the 1.3 mm flux distribution of two populations combining cores from all clouds. The protostellar cores tend to have larger 1.3 mm fluxes, with a median of 5.51 mJy, compared to 2.56 mJy of the prestellar cores. We further plot in [7](#fig:comp_mass)(d) the distributions of masses derived assuming the $\rm NH_3$ temperatures. The median mass of protostellar cores (2.81  $M_\odot$) is also larger than that of the prestellar population (1.34  $M_\odot$).

We carry out a Mann-Whitney U test (cite: Mann47) to statistically examine the result, as shown in [5](#table:mass_comp). It is a nonparametric test for the ranking between two samples. For panel (a) the null hypothesis that protostellar cores have equally or smaller fluxes than prestellar cores can be rejected with a confidence greater than 99.99% ($p$ = 1.5$\times 10^{-8}$). Similarly for panel (d) the null hypothesis that protostellar cores have equal or smaller masses than prestellar cores can also be rejected with a high confidence ($p$ = 4.0$\times 10^{-7}$). Therefore the protostellar cores are statistically more massive. We also show in [10](#sec:app_virial) that the same conclusion also applies for the gravitationally bound core population with virial parameters smaller than 2, where the virial parameters are estimated using the $\rm NH_3$ line width.

Note that the core sample is flux limited and a temperature is needed to convert the flux to mass. Thus our observations are more sensitive for protostellar cores compared to prestellar cores, since the former class has on average a higher temperature, thus a lower mass limit accordingly. For example, a 90% completeness flux of 1.2 mJy (typical value for our sample) translates into a mass of 0.55  $M_\odot$ assuming 20 K, but 1.5  $M_\odot$ assuming 10 K, i.e., a factor of 2.7 larger. Therefore, it is likely that we are missing more prestellar cores in the lower mass regime.

We further check sub samples of clouds in different evolutionary stages, as shown in [7](#fig:comp_mass)(e) and (f). For the young group (I18308, I18337, I18460), the protostellar cores are clearly more massive than prestellar cores (3.29  $M_\odot$ v.s. 1.16  $M_\odot$ in median mass). The null hypothesis that protostellar cores have equal or smaller masses can be rejected with a confidence greater than 99.9% ($p$=1.4$\times 10^{-4}$). On the other hand, for the more evolved group (I18530, I19220, I19074), the difference between two populations is smaller (2.31  $M_\odot$ v.s. 1.37  $M_\odot$ in median mass), but still a $p$ value of 4.7$\times 10^{-3}$ suggests the protostellar population is more massive than the prestellar population with a confidence greater than 99%. This trend would be reinforced when taking into account the different completeness levels for the two populations.

Similar to our results, larger masses for protostellar cores have also been observed in other star forming regions, i.e., IRDCs, Orion A, and W43 (cite: Peretto20; Kong21; Takemura23; Nony23; Li23), and interpreted as evidence for continuous mass accretion during the protostellar phase. Such mass growth is expected in the clump-fed models of star formation (cite: Smith09), such as competitive accretion (cite: Bonnell06), global hierarchical collapse model (cite: Vazquez19), or the inertial-inflow model (cite: Padoan20), and provides a pathway to form massive stars without previously existing massive prestellar cores. The accretion onto cores could be filament-mediated as shown in some case studies, i.e., the gas flow along filaments feeds the embedded cores and protostars with additional mass (cite: Lu18). In our case, protostellar cores have a median mass about twice as large as prestellar cores. To make two distributions indistinguishable, e.g., $p$ $\sim$0.1 in a single-side Mann-Whitnery U test, the prestellar masses need to be multiplied by a factor greater than 3.2 and 1.8 for the young and evolved group, respectively. In a core growth scenario, this suggests a core has to gain a significant fraction of its total mass via further accretion during its lifetime. If this happens in the protostellar phase, the rate at which a core accretes from its surroundings must be on average larger than the protostellar accretion rate onto the accretion disk.

## Core mass function

The distribution of stellar masses in young clusters, i.e., the initial mass function (IMF), is a fundamental outcome of star formation. The shape of the IMF and whether it is universal are important topics in modern astrophysics. Observations in nearby clusters have revealed remarkably universal IMFs (cite: Bastian10), which appear to follow a power law index above 1  $M_\odot$, $$\begin{equation}
\frac{dN}{d\log M} \propto M^{-\alpha},
\end{equation}$$ where $\alpha=$1.35 (cite: Salpeter55), with a peak near 0.25  $M_\odot$. The physical origin of the IMF is unclear. A promising way to advance our understanding is to look at the dense core mass function, where a core can be defined theoretically to be a self-gravitating structure that collapses to form a single star or small multiple system. The CMF in nearby, $\lesssim$1 kpc regions is similar in shape to the IMF (cite: Motte98; Alves07). Studies with ALMA have shed more light on the CMF in more distant regions (cite: Zhang15; Csengeri17; Cheng18; Liu18; Motte18; Kong19; Sanhueza19; Lu20; Sadaghiani20; ONeill21; Suarez21; Pouteau22; Pouteau23). Some of these measurements, which compile a sample of single pointing observations towards massive clumps (cite: Liu18; ONeill21), are likely biased due to potential mass segregation effect (cite: Plunkett18; Dib19), thus it is necessary to map the protocluster over their full extent. In this section we examine the CMF of the INFANT sample.

In [8](#fig:cmf)(a) we show the CMF of 183 cores identified by *getsf*. The CMF of 108 prestellar cores is shown in blue.

As shown in [4.2](#sec:core_iden), the 90% completeness limit is estimated to be 0.53–0.89  $M_\odot$ (for $T=$15 K), which is lower than the mass range where CMF starts to peak or flatten, i.e., 1 – 3  $M_\odot$. But considering cores with a lower temperature of 10 K, the 90% completeness limit can be higher, i.e., 1.0 – 1.5  $M_\odot$, thus we can not say with certainty whether the turnover seen in the CMF is physically real or due to incompleteness. We fit the high-mass end of the CMFs (M $>$ 1.5  $M_\odot$) with a power-law function as in [\[equ:imf\]](#equ:imf) using the the maximum likelihood estimation (MLE) method in (cite: Clauset09) implemented with the *plfit* package. The results are labeled in [8](#fig:cmf).

The fit gives an power law index $\alpha$ = 1.15 $\pm$ 0.12. This slope is similar to that found in the IRDC sample in (cite: Sanhueza19) (1.07 $\pm$ 0.09 for all cores, or 1.17 $\pm$ 0.10 for prestellar cores), and shallower than the Salpeter value of 1.35. For the (candidate) prestellar core population, the power law index is measured to be $\alpha = 1.70 \pm 0.25$, slightly steeper than the Salpeter value. Thus the slightly top-heavy form measured for the global CMF is due to the protostellar population. Similar behavior is also observed in the W43 cloud, where the global CMF has a high-mass slope significantly shallower than the prestellar CMF (0.96$\pm$0.09 v.s. 1.46$_{-0.19}^{+0.12}$) (cite: Nony23). This flattening trend could be explained by core mass growth in clump-fed models if high-mass cores accrete more efficiently than low-mass cores (cite: Nony23).

To investigate the possible dependence on the overall cloud evolutionary status we plot the CMF for the young and evolved cloud groups, respectively, in [8](#fig:cmf) (b) and (c). For the young group, we get a top heavy power-law index $\alpha$ = 0.89 $\pm$ 0.15, while for the evolved group, the slope is steeper $\alpha$ = 1.44 $\pm$ 0.25, consistent with the Salpeter value. Thus we see a trend of the global CMF becoming steeper at the high mass end as the protocluster evolves, resembling more the IMF shape at later stages. We also fit the prestellar CMF for these sub samples, the slopes are steeper compared to the global CMF but less well constrained due to limited number statistics in the high mass end.

This steepening trend with cloud evolution is seemingly in contradiction to the speculation that protostellar core growth could flatten the CMF. Combined with our analysis of core growth in [6.2](#sec:core_growth), this evolutionary variation in CMF could be explained in a dynamic cluster formation picture. If the prestellar cores, which constantly form over time and evolve into the protostellar population, all share the same mass distribution as the “parent” prestellar core population, then in order to make a shallower slope, high-mass cores need to have a larger fractional mass growth rate than low-mass cores. Precisely, the net mass accretion rate $\dot{M}$ should scale with mass with an power-law index significantly larger than 1. This agrees with observations in some hub-filament systems, where global infall results in continuous gas inflow from the clump scale to the core scale and efficiently feeds the most massive core(s) early in the evolution, leading to a high mass concentration fraction of the massive cores (cite: Anderson21; Zhou22; Xu23). Therefore, in the very early stage, which is not captured by our sample, the CMF originated from fragmentation could be Salpeter-like, or slightly top-heavy as suggested in (cite: Sanhueza19), but rapid accretion from the clump then produces a shallower global CMF, as we see for the young group. In a later stage, the clump-fed accretion will be reduced as protostellar feedback becomes stronger, rendering it difficult to continue forming more massive cores. The ongoing formation of low- and intermediate mass cores leads to a steeper, Salpeter-like slope as we observe for the evolved group.

To confirm or refute this interpretation, it is necessary to conduct a systematic study of the core accretion rate for different core masses and different cloud evolutionary stages. We intend to further explore this using our ALMA band 3 data. As previously mentioned there are numerous measurements of power-law indices of the CMF in massive clumps, with a range of CMF slopes at high-mass end ($>$1  $M_\odot$) from a top heavy value of $\sim$0.7 to a Salpeter-like one of 1.35. Here we do not attempt to reconcile these measurements in the literature, since the core identification and mass estimation methods vary. In order to make a meaningful comparison with our work we consider studies that (i) image the protocluster in its full extent; (ii) include temperature measurements at the core scale; and (iii) adopt a similar core detection algorithm as *getsf*. There are very a few works that satisfy these criteria. (cite: Motte18) found $\alpha$ = $-$0.90 $\pm$ 0.06 for masses M $>$ 1.6$\mbox{\,$M_\odot$}$ from a sample of 105 cores in the massive cloud W43-MM1. More recent results from the ALMA-IMF survey also revealed a top heavy index $\alpha$ = $-$0.95 $\pm$ 0.04 for in a sample of 294 cores in W43-MM2&MM3 (cite: Pouteau22). In the scenario proposed here, these measurements in W43 could represent the relatively early, active accreting phase in the cluster evolution.

A caveat in this survey is concerning the classification of two groups with different evolutionary phases. As discussed in [6.1](#sec:evolution), It is difficult to unambiguously define and determine the relative evolutionary phase for a parsec-scale protocluster. In addition, since each group contains only three clouds, it is likely that the observed differences in CMF may (partly) arise from other systematic differences of the protoclusters, instead of evolution. For example, the targets in the young group also have relatively higher masses. A larger sample with similar spatial resolution is needed to disentangle the coupling.

# Conclusions

We present the first results of the INFANT (INvestigations of massive Filaments ANd sTar formation) survey, aimed at investigating the relationship between filaments and star formation across a range of evolutionary stages. In this first paper of the series, we report the ALMA Band 6 continuum observations of eight carefully selected massive filamentary clouds that have been characterized in previous SMA and VLA observations (cite: Lu14; Lu18). Each cloud was mosaiced in 30 to 40 pointings in 12 m array (5000 – 6000 arcsec$^2$), with a sensitivity of $\sim$0.1 mJy beam$^{-1}$ and a spatial resolution of $\sim$3000 au. The main findings are summarized as follows:

- We compare the performance of two widely used core identification algorithms, *getsf* and *astrodendro*, via artificial core insertion experiments. We find that *getsf* gives more robust identification results for identification of compact cores and flux measurements in both isolated and clustered region. Cautions should be taken when directly interpreting the leaf structures given by astrodendro as cores.

- We detect in total 183 dense cores for the INFANT sample, with each cloud having 15 – 36 cores. Each core is classified as either protostellar if it is associated with molecular outflows and/or warm gas tracers including $\rm H_2CO$ ($3_{2,2}-2_{2,1}$), ($3_{2,1}-2_{2,0}$), $\rm CH_3OH$ ($4_{2,2}-3_{1,2}$), or prestellar candidates if not. Out of 183 cores 108 are classified as prestellar and 75 are prototellar, including those identified by outflows (43/75) and warm core tracers (70/75). The fraction of prestellar cores varys among the sample, with I18308 hosting a lowest fraction of prestellar population of 32% (7/22) and I19220 a highest fraction of 76% (13/17).

- Our INFANT targets cover different cluster evolutionary stages based on presence of infrared emission and UCHII/HII regions. We divided the INFANT sample into two groups with different evolutionary stages, young group (I18337, I18460, I18308) and evolved group (I18530, I19220, I19074) based on the $L/M$ ratio, as well as other evolution indicators. Two targets, I19368 and I18310, are not included since we cannot assign them an evolution group confidently.

- We estimate the gas temperature of cores using the $\rm NH_3$(1,1) and (2,2) lines obtained with JVLA following a spectral line fitting routine in (cite: Lu18). The measured $T_\mathrm{NH_3}$ ranges from 9.9 to 32.2 K, with a median of 16.5 K. The protostellar cores have a higher median $\rm T_{NH_3}$ of 17.5 K, compared to 15.8 K for the prestellar candidate cores.

- With masses derived with the 1.3 mm continuum emission and $\rm NH_3$ temperatures, we compare the mass distribution between protostellar and prestellar populations. We find that the protostellar cores are statistically more massive than the prestellar cores. This provides evidence that cores continue to gain mass from the surroundings after the formation of protostars.

- The most massive prestellar core in this sample has a mass of 10.3  $M_\odot$. We have not detected high-mass ($\gtrsim$20–30  $M_\odot$) prestellar cores.

- For the INFANT sample we derive a powerlaw index of 1.15 $\pm$ 0.12 for the global CMF, and 1.70 $\pm$ 0.25 for the prestellar CMF in the high mass end (M $>$ 1.5  $M_\odot$). We also find a trend for steeper power-law index in global CMF with cloud evolution (1.44 $\pm$ 0.25 for the evolved group v.s. 0.89 $\pm$ 0.15 for the young group). An explanation is that cores could continuously grow by acquiring infalling material from larger scale after their formation. This process is particularly strong in the relative early stage of cluster formation, leading to a shallower CMF as more massive cores accrete more efficiently. At a later point when core accretion is reduced due to protostellar feedback, it is more difficult to continue forming more massive cores, thus ongoing formation of low- and intermediate mass cores results in a steeper, Salpeter-like slope.

Identifying the core population is the first step towards understanding the importance of filaments in high-mass star formation. In the subsequent papers of this series, we will utilize molecular line data to delve into the significance of filamentary morphology. This will involve examining phenomena such as gas flows and accretion along the filaments, as well as comparing gas kinematics in star-forming filaments with those in more quiescent filaments.

# Acknowledgments

This work has been supported by the National Key R&D Program of China (No. 2022YFA1603101). This work has been sponsored by Natural Science Foundation of Shanghai (No. 23ZR1482100). X.L. acknowledges support from the National Natural Science Foundation of China (NSFC) through grant No. 12273090, and the Chinese Academy of Sciences (CAS) ‘Light of West China’ Program (No. xbzg-zdsys-202212). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00526.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. R.G.-M. acknowledges support from UNAM-PAPIIT project IN108822. H. B. L. acknowledges the support from the National Science and Technology Council (NSTC) of Taiwan (Grant No. 111-2112-M-110-022-MY3). P. S. was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI Number 22H01271) of JSPS.

# Software

CASA (cite: Mcmullin07; casa22), APLpy (cite: Aplpy12), Astropy (cite: Astropy13; astropy18; astropy22)

# Multi-wavelength images of the INFANT sample

We present in [9](#fig:multi1) the infrared images of the INFANT targets including *Spitzer* 3.6/8.0 $\mu$m, WISE 12/22 $\mu$m as well as the column density/dust temperature maps derived with *Herschel* data (70$\mu$m, 160$\mu$m from PACS and 250$\mu$m, 350$\mu$m, 500$\mu$m from SPIRE). For the SED fits we assume a single-component, modified black-body spectral energy distribution fits to each pixel of input images. Before performing SED fitting, we smoothed all images to a common angular resolution of the largest telescope beam ($\sim$37$''$ for SPIRE 500$\mu$m image) and all images were re-gridded to have the same pixel size. The flux density is given by $$\begin{equation}
S_\nu = \Omega_mB_\nu(T_\mathrm{d})(1-e^{-\tau_\nu}),
\end{equation}$$ and the column density is $$\begin{equation}
N_\mathrm{H_2} = \frac{\tau_\nu M_g}{\kappa_\nu \mu m_\mathrm{H}M_d},
\end{equation}$$ where $B(T_d)$ is the Planck function at $T_d$ and $\kappa$=$\kappa_{230}(\nu/230GHz)^\beta$, $\Omega_{m}$ is the solid angle. We adopt $\kappa_{230}$ = 0.899 g cm$^{-2}$ as in (cite: Ossenkopf94) for the moderately coagulated thin ice mentle model and a gas to dust ratio $M_g/M_d$ = 100 (cite: Bohlin78).

We performed least-squares fits of the 70/160/250/350/500$\mu$m spectral energy distributions weighted by the squares of the measured noise levels to derive the pixel-to-pixel distributions of the column density/dust temperature maps with an angular resolution of $\sim$37$''$.

# Temperature derivation with the $\rm NH_3$ lines

In [10](#fig:nh3_example) we present an example of fitting $\rm NH_3$ (1,1) and (2,2) lines with the routine in (cite: Lu18). The errors displayed in the plot only account for the uncertainties in the fitting.

# Virial states of cores

The virial parameters of dense cores can be estimated by $$\begin{equation}
\alpha = \frac{5 \sigma_{in}^2R}{GM_{\rm core}},
\end{equation}$$ where $\sigma_{\rm in}$ is the intrinsic 1D velocity dispersion of the molecule of mean mass and $R$ is the core radius (cite: Bertoldi92). We use the velocity dispersion $\sigma_{\rm NH_3}$ of $\rm NH_3$ lines to estimate $\sigma_{\rm in}$. This is done by first subtracting the channel width 0.4 km s$^{-1}$ quadratically, i.e., $$\begin{equation}
\sigma_{\rm deconv,NH_3} = \sqrt{ \sigma_{\rm NH_3}^2 - (0.4~{\rm km\ s^{-1}}/2\sqrt{2{\rm ln2}} )^2   }   ,
\end{equation}$$ and then $$\begin{equation}
\sigma_{\rm in} =  \sqrt{\sigma_{\rm nth}^2+\sigma_{\rm th}^2} \\
             =  \sqrt{\sigma_{\rm deconv,NH_3}^2-\frac{k_BT_{\rm rot}}{\mu_{\rm NH_3} m_p}+\frac{k_BT_{\rm rot}}{\mu_p m_p}}.
\end{equation}$$ where $\mu_p$ = 2.33 is the mean molecular weight assuming $n_{\rm He}=0.1 n_{\rm H}$ and $\mu_{\rm NH_3}$ is the molecular weight of $\rm NH_3$. For the radius we adopt half of the deconvolved FWHM, i.e., $$\begin{equation}
{\rm FWHM_{ decov}} = \sqrt{{\rm FWHM_{ major}}\times {\rm FWHM_{ minor}} - {\rm Beam_{ major}} \times {\rm Beam_{ minor}}  } .
\end{equation}$$ We set a minimum deconvolved size of half the beam, to limit deconvolution effects that may give excessively small and thus unrealistic sizes. Thus the virial parameters are estimated for 104 cores with valid radius and velocity dispersion estimation. For a self-gravitating, unmagnetized core without rotation, a virial parameter above a critical value $\alpha_{\rm cr}= 2$ (assuming a constant radial density profile) indicates that the core is unbound and may expand, while one below 2 suggests that the core is bound and may collapse. In [11](#fig:virial) we plot the virial parameters against the core mass. There is a trend for more massive cores having smaller virial parameters. 61 cores have virial parameters smaller than 2, suggesting they are gravitational bound. If we compare the mass distribution of prestellar and protostellar cores for the gravitational bound population, which is shown in [11](#fig:virial), we find the conclusion in [6.2](#sec:core_growth) still holds, i.e., the protostellar cores are statistically more massive. The null hypothesis that protostellar cores have equally or smaller fluxes than prestellar cores can be rejected with a confidence greater than 99% ($p$ = 0.0028).

# Comparison of CMFs derived by *astrodendro* and *getsf*

In [12](#fig:map_iden_other) we show the core identification results with *astrodendro* and *getsf* for targets that are not shown in [2](#fig:map_iden). We present in [13](#fig:cmf_comp) the CMFs derived with both algorithms, where the fluxes are converted to masses assuming a uniform temperature of 20 K. *Astrodendro* gives a larger number of cores (382) compared to *getsf* (183). A power law fit for the high mass end (M $>$ 1.5  $M_\odot$) gives a shallower slope $\alpha$=0.98$\pm$0.11 for *astrodendro*. We further check the CMF for 146 commonly detected cores in both algorithms, defined as a consistent position within 0$''$3. The power law fit for the same range gives $\alpha$=0.87$\pm$0.10 for *astrodendro*, shallower than *getsf* ($\alpha$=1.26$\pm$0.15). But for *astrodendro* the CMF appears as a broken powerlaw with a separation point around $\sim$4  $M_\odot$. If the fit only accounts for M $>$ 4  $M_\odot$, then it gives $\alpha$=1.44$\pm$0.23. From inspection of this plot *astrodendro* appears to give more massive cores than *getsf* (e.g., M $>$ 4  $M_\odot$), and more low mass cores (e.g., M $<$ 0.8  $M_\odot$) but a deficit of cores in the intermediate mass range. We speculate the larger mass estimation of high mass cores for *astrodendro* is mainly due to the fact that these cores often lie on strong background emission and (at least in a few cases) *astrodendro* fails to identify the fragmentation in the extension wing of massive cores (see [12](#fig:map_iden_other)). A comparison of the fluxes for commonly detected cores are shown in [14](#fig:flux_comp). It can be seen that the fluxes from two algorithms are correlated but the difference can be very large for individual cores, and *astrodendro* does return larger fluxes for the more massive cores. For *astrodendro* we also attempted to remove the background using a median filtering method with a Gaussian Kernel of 5$''$. This mitigates the differences in fluxes and results in a better correlation between the fluxes obtained from the two methods.

# Slopes of CMFs and cloud evolution

We test the robustness of the conclusion in [6.3](#sec:cmf) by varying the classification of cloud evolution stages. In [6](#table:slope_evo) we list the MLE power law fit results for different subgroups of the sample based on different classification schemes. Case 1 is the fiducial evolution classification adopted in [6.3](#sec:cmf) by combining information from the $L/M$ ratio and other evolution indicators (see discussion [6.1](#sec:evolution)). For case 2 we include all eight regions and classify the four regions (I18308, I18310, I18337, and I18460) as young group since a significant portion of these clouds are still infrared dark (for wavelengths up to 24 $\mu$m), and the rest four regions are classified as evolved group. For case 3 we split the eight regions into two groups purely based on their $L/M$ ratio listed in [1](#table:info_sample). For case 4 we selected from the fiducial case two sources with lowest $L/M$ ratios for the young group, and two sources with highest $L/M$ ratios for the evolved group, respectively. In these cases, the young group exhibits a high mass slope ranging from $\sim$0.9 to $\sim$1.1, while the evolved group has a slope from $\sim$1.4 to $\sim$1.6. In all cases the power-law index $\alpha$ for the evolved group is slightly steeper. For case 4 the $\alpha$ of two groups are consistent within 1$\sigma$ uncertainty mainly due to limited number statistics.

| Classification | Young | $\alpha$ | Evolved | $\alpha$ |
|:--:|:--:|:--:|:--:|:--:|
| 1 | I18308, I18337, I18460 | 0.89$\pm$0.15 | I18530, I19220, I19074 | 1.44$\pm$0.25 |
| 2 | I18308, I18310, I18337, I18460 | 1.01$\pm$0.14 | I18530, I19220, I19074, I19368 | 1.44$\pm$0.21 |
| 3 | I18308, I18337, I18460, I19368 | 1.00$\pm$0.14 | I18310,I18530, I19220, I19074 | 1.39$\pm$0.19 |
| 4 | I18337, I18460 | 1.06$\pm$0.23 | I19220, I19074 | 1.55$\pm$0.49 |

: Power-law index $\alpha$ (M$>$1.5  $M_\odot$) for subgroups of the INFANT sample

natexlab

(ref: Abergel94) Abergel, A., Boulanger, F., Mizuno, A., & Fukui, Y. 1994, ApJL, 423, L59, doi: [`10.1086/187235`](http://doi.org/10.1086/187235)

(ref: Alves07) Alves, J., Lombardi, M., & Lada, C. J. 2007, A&A, 462, L17, doi: [`10.1051/0004-6361:20066389`](http://doi.org/10.1051/0004-6361:20066389)

(ref: Anderson21) Anderson, M., Peretto, N., Ragan, S. E., et al. 2021, MNRAS, 508, 2964, doi: [`10.1093/mnras/stab2674`](http://doi.org/10.1093/mnras/stab2674)

(ref: Andre19) André, P., Arzoumanian, D., Könyves, V., Shimajiri, Y., & Palmeirim, P. 2019, A&A, 629, L4, doi: [`10.1051/0004-6361/201935915`](http://doi.org/10.1051/0004-6361/201935915)

(ref: Andre14) André, P., Di Francesco, J., Ward-Thompson, D., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 27

(ref: Andre10) André, P., Men’shchikov, A., Bontemps, S., et al. 2010, A&A, 518, L102, doi: [`10.1051/0004-6361/201014666`](http://doi.org/10.1051/0004-6361/201014666)

(ref: Arzoumanian11) Arzoumanian, D., André, P., Didelon, P., et al. 2011, A&A, 529, L6, doi: [`10.1051/0004-6361/201116596`](http://doi.org/10.1051/0004-6361/201116596)

(ref: Arzoumanian19) Arzoumanian, D., André, P., Könyves, V., et al. 2019, A&A, 621, A42, doi: [`10.1051/0004-6361/201832725`](http://doi.org/10.1051/0004-6361/201832725)

(ref: Astropy13) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy18) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: astropy22) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Bally87) Bally, J., Langer, W. D., Stark, A. A., & Wilson, R. W. 1987, ApJL, 312, L45, doi: [`10.1086/184817`](http://doi.org/10.1086/184817)

(ref: Barnes21) Barnes, A. T., Henshaw, J. D., Fontani, F., et al. 2021, MNRAS, 503, 4601, doi: [`10.1093/mnras/stab803`](http://doi.org/10.1093/mnras/stab803)

(ref: Barnes23) Barnes, A. T., Liu, J., Zhang, Q., et al. 2023, A&A, 675, A53, doi: [`10.1051/0004-6361/202245668`](http://doi.org/10.1051/0004-6361/202245668)

(ref: Bastian10) Bastian, N., Covey, K. R., & Meyer, M. R. 2010, ARA&A, 48, 339, doi: [`10.1146/annurev-astro-082708-101642`](http://doi.org/10.1146/annurev-astro-082708-101642)

(ref: Berry15) Berry, D. S. 2015, Astronomy and Computing, 10, 22, doi: [`10.1016/j.ascom.2014.11.004`](http://doi.org/10.1016/j.ascom.2014.11.004)

(ref: Bertoldi92) Bertoldi, F., & McKee, C. F. 1992, ApJ, 395, 140, doi: [`10.1086/171638`](http://doi.org/10.1086/171638)

(ref: Beuther02) Beuther, H., Schilke, P., Menten, K. M., et al. 2002, ApJ, 566, 945, doi: [`10.1086/338334`](http://doi.org/10.1086/338334)

(ref: Bohlin78) Bohlin, R. C., Savage, B. D., & Drake, J. F. 1978, ApJ, 224, 132, doi: [`10.1086/156357`](http://doi.org/10.1086/156357)

(ref: Bonnell06) Bonnell, I. A., & Bate, M. R. 2006, MNRAS, 370, 488, doi: [`10.1111/j.1365-2966.2006.10495.x`](http://doi.org/10.1111/j.1365-2966.2006.10495.x)

(ref: Carey00) Carey, S. J., Feldman, P. A., Redman, R. O., et al. 2000, ApJL, 543, L157, doi: [`10.1086/317270`](http://doi.org/10.1086/317270)

(ref: casa22) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Caselli19) Caselli, P., Pineda, J. E., Zhao, B., et al. 2019, ApJ, 874, 89, doi: [`10.3847/1538-4357/ab0700`](http://doi.org/10.3847/1538-4357/ab0700)

(ref: Chen19) Chen, H.-R. V., Zhang, Q., Wright, M. C. H., et al. 2019, ApJ, 875, 24, doi: [`10.3847/1538-4357/ab0f3e`](http://doi.org/10.3847/1538-4357/ab0f3e)

(ref: Cheng18) Cheng, Y., Tan, J. C., Liu, M., et al. 2018, ApJ, 853, 160, doi: [`10.3847/1538-4357/aaa3f1`](http://doi.org/10.3847/1538-4357/aaa3f1)

(ref: Churchwell06) Churchwell, E., Povich, M. S., Allen, D., et al. 2006, ApJ, 649, 759, doi: [`10.1086/507015`](http://doi.org/10.1086/507015)

(ref: Clauset09) Clauset, A., Shalizi, C. R., & Newman, M. E. J. 2009, SIAM Review, 51, 661, doi: [`10.1137/070710111`](http://doi.org/10.1137/070710111)

(ref: Csengeri17) Csengeri, T., Bontemps, S., Wyrowski, F., et al. 2017, A&A, 600, L10, doi: [`10.1051/0004-6361/201629754`](http://doi.org/10.1051/0004-6361/201629754)

(ref: Cyganowski14) Cyganowski, C. J., Brogan, C. L., Hunter, T. R., et al. 2014, ApJL, 796, L2, doi: [`10.1088/2041-8205/796/1/L2`](http://doi.org/10.1088/2041-8205/796/1/L2)

(ref: Dib19) Dib, S., & Henning, T. 2019, A&A, 629, A135, doi: [`10.1051/0004-6361/201834080`](http://doi.org/10.1051/0004-6361/201834080)

(ref: Eker15) Eker, Z., Soydugan, F., Soydugan, E., et al. 2015, AJ, 149, 131, doi: [`10.1088/0004-6256/149/4/131`](http://doi.org/10.1088/0004-6256/149/4/131)

(ref: Fernandez-Lopez14) Fernández-López, M., Arce, H. G., Looney, L., et al. 2014, ApJL, 790, L19, doi: [`10.1088/2041-8205/790/2/L19`](http://doi.org/10.1088/2041-8205/790/2/L19)

(ref: Galvn10) Galván-Madrid, R., Zhang, Q., Keto, E., et al. 2010, ApJ, 725, 17, doi: [`10.1088/0004-637X/725/1/17`](http://doi.org/10.1088/0004-637X/725/1/17)

(ref: Ginsburg16) Ginsburg, A., Henkel, C., Ao, Y., et al. 2016, A&A, 586, A50, doi: [`10.1051/0004-6361/201526100`](http://doi.org/10.1051/0004-6361/201526100)

(ref: Hacar17) Hacar, A., Alves, J., Tafalla, M., & Goicoechea, J. R. 2017, A&A, 602, L2, doi: [`10.1051/0004-6361/201730732`](http://doi.org/10.1051/0004-6361/201730732)

(ref: Hacar23) Hacar, A., Clark, S., Heitsch, F., et al. 2022, arXiv e-prints, arXiv:2203.09562, doi: [`10.48550/arXiv.2203.09562`](http://doi.org/10.48550/arXiv.2203.09562)

(ref: Hacar18) Hacar, A., Tafalla, M., Forbrich, J., et al. 2018, A&A, 610, A77, doi: [`10.1051/0004-6361/201731894`](http://doi.org/10.1051/0004-6361/201731894)

(ref: Hacar13) Hacar, A., Tafalla, M., Kauffmann, J., & Kovács, A. 2013, A&A, 554, A55, doi: [`10.1051/0004-6361/201220090`](http://doi.org/10.1051/0004-6361/201220090)

(ref: Hales12) Hales, C. A., Murphy, T., Curran, J. R., et al. 2012, MNRAS, 425, 979, doi: [`10.1111/j.1365-2966.2012.21373.x`](http://doi.org/10.1111/j.1365-2966.2012.21373.x)

(ref: Hodge16) Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016, ApJ, 833, 103, doi: [`10.3847/1538-4357/833/1/103`](http://doi.org/10.3847/1538-4357/833/1/103)

(ref: Kirk13) Kirk, H., Myers, P. C., Bourke, T. L., et al. 2013, ApJ, 766, 115, doi: [`10.1088/0004-637X/766/2/115`](http://doi.org/10.1088/0004-637X/766/2/115)

(ref: Kong19) Kong, S. 2019, ApJ, 873, 31, doi: [`10.3847/1538-4357/aaffd5`](http://doi.org/10.3847/1538-4357/aaffd5)

(ref: Kong21) Kong, S., Arce, H. G., Shirley, Y., & Glasgow, C. 2021, ApJ, 912, 156, doi: [`10.3847/1538-4357/abefe7`](http://doi.org/10.3847/1538-4357/abefe7)

(ref: Kong18) Kong, S., Tan, J. C., Arce, H. G., et al. 2018, ApJL, 855, L25, doi: [`10.3847/2041-8213/aab151`](http://doi.org/10.3847/2041-8213/aab151)

(ref: Konyves15) Könyves, V., André, P., Men’shchikov, A., et al. 2015, A&A, 584, A91, doi: [`10.1051/0004-6361/201525861`](http://doi.org/10.1051/0004-6361/201525861)

(ref: Konyves20) Könyves, V., André, P., Arzoumanian, D., et al. 2020, A&A, 635, A34, doi: [`10.1051/0004-6361/201834753`](http://doi.org/10.1051/0004-6361/201834753)

(ref: Kumar20) Kumar, M. S. N., Palmeirim, P., Arzoumanian, D., & Inutsuka, S. I. 2020, A&A, 642, A87, doi: [`10.1051/0004-6361/202038232`](http://doi.org/10.1051/0004-6361/202038232)

(ref: Li20) Li, S., Zhang, Q., Liu, H. B., et al. 2020, ApJ, 896, 110, doi: [`10.3847/1538-4357/ab84f1`](http://doi.org/10.3847/1538-4357/ab84f1)

(ref: Li22) Li, S., Sanhueza, P., Lee, C. W., et al. 2022, ApJ, 926, 165, doi: [`10.3847/1538-4357/ac3df8`](http://doi.org/10.3847/1538-4357/ac3df8)

(ref: Li23) Li, S., Sanhueza, P., Zhang, Q., et al. 2023, ApJ, 949, 109, doi: [`10.3847/1538-4357/acc58f`](http://doi.org/10.3847/1538-4357/acc58f)

(ref: Liu12a) Liu, H. B., Jiménez-Serra, I., Ho, P. T. P., et al. 2012a, ApJ, 756, 10, doi: [`10.1088/0004-637X/756/1/10`](http://doi.org/10.1088/0004-637X/756/1/10)

(ref: Liu12) Liu, H. B., Quintana-Lacaci, G., Wang, K., et al. 2012b, ApJ, 745, 61, doi: [`10.1088/0004-637X/745/1/61`](http://doi.org/10.1088/0004-637X/745/1/61)

(ref: Liu18) Liu, M., Tan, J. C., Cheng, Y., & Kong, S. 2018, ApJ, 862, 105, doi: [`10.3847/1538-4357/aacb7c`](http://doi.org/10.3847/1538-4357/aacb7c)

(ref: Liu16) Liu, T., Kim, K.-T., Yoo, H., et al. 2016, ApJ, 829, 59, doi: [`10.3847/0004-637X/829/2/59`](http://doi.org/10.3847/0004-637X/829/2/59)

(ref: Lu20) Lu, X., Cheng, Y., Ginsburg, A., et al. 2020, ApJL, 894, L14, doi: [`10.3847/2041-8213/ab8b65`](http://doi.org/10.3847/2041-8213/ab8b65)

(ref: Lu14) Lu, X., Zhang, Q., Liu, H. B., Wang, J., & Gu, Q. 2014, ApJ, 790, 84, doi: [`10.1088/0004-637X/790/2/84`](http://doi.org/10.1088/0004-637X/790/2/84)

(ref: Lu18) Lu, X., Zhang, Q., Liu, H. B., et al. 2018, ApJ, 855, 9, doi: [`10.3847/1538-4357/aaad11`](http://doi.org/10.3847/1538-4357/aaad11)

(ref: Ma13) Ma, B., Tan, J. C., & Barnes, P. J. 2013, ApJ, 779, 79, doi: [`10.1088/0004-637X/779/1/79`](http://doi.org/10.1088/0004-637X/779/1/79)

(ref: Mann47) Mann, H. B., & Whitney, D. R. 1947, The Annals of Mathematical Statistics, 18, 50 , doi: [`10.1214/aoms/1177730491`](http://doi.org/10.1214/aoms/1177730491)

(ref: Mckee03) McKee, C. F., & Tan, J. C. 2003, ApJ, 585, 850, doi: [`10.1086/346149`](http://doi.org/10.1086/346149)

(ref: Mcmullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell (San Francisco, CA: ASP), 127

(ref: Menshchikov13) Men’shchikov, A. 2013, A&A, 560, A63, doi: [`10.1051/0004-6361/201321885`](http://doi.org/10.1051/0004-6361/201321885)

(ref: Menshchikov17) —. 2017, A&A, 607, A64, doi: [`10.1051/0004-6361/201730925`](http://doi.org/10.1051/0004-6361/201730925)

(ref: Men21) —. 2021a, A&A, 649, A89, doi: [`10.1051/0004-6361/202039913`](http://doi.org/10.1051/0004-6361/202039913)

(ref: Men21b) —. 2021b, A&A, 654, A78, doi: [`10.1051/0004-6361/202141533`](http://doi.org/10.1051/0004-6361/202141533)

(ref: Menshchikov12) Men’shchikov, A., André, P., Didelon, P., et al. 2012, A&A, 542, A81, doi: [`10.1051/0004-6361/201218797`](http://doi.org/10.1051/0004-6361/201218797)

(ref: Molinari10) Molinari, S., Swinyard, B., Bally, J., et al. 2010, A&A, 518, L100, doi: [`10.1051/0004-6361/201014659`](http://doi.org/10.1051/0004-6361/201014659)

(ref: Molinari16) Molinari, S., Schisano, E., Elia, D., et al. 2016, A&A, 591, A149, doi: [`10.1051/0004-6361/201526380`](http://doi.org/10.1051/0004-6361/201526380)

(ref: Mori23) Morii, K., Sanhueza, P., Nakamura, F., et al. 2023, ApJ, 950, 148, doi: [`10.3847/1538-4357/acccea`](http://doi.org/10.3847/1538-4357/acccea)

(ref: Motte98) Motte, F., Andre, P., & Neri, R. 1998, A&A, 336, 150

(ref: Motte18) Motte, F., Nony, T., Louvet, F., et al. 2018, Nature Astronomy, 2, 478, doi: [`10.1038/s41550-018-0452-x`](http://doi.org/10.1038/s41550-018-0452-x)

(ref: Motte22) Motte, F., Bontemps, S., Csengeri, T., et al. 2022, A&A, 662, A8, doi: [`10.1051/0004-6361/202141677`](http://doi.org/10.1051/0004-6361/202141677)

(ref: Myers09) Myers, P. C. 2009, ApJ, 700, 1609, doi: [`10.1088/0004-637X/700/2/1609`](http://doi.org/10.1088/0004-637X/700/2/1609)

(ref: Nony23) Nony, T., Galvan-Madrid, R., Motte, F., et al. 2023, arXiv e-prints, arXiv:2301.07238, doi: [`10.48550/arXiv.2301.07238`](http://doi.org/10.48550/arXiv.2301.07238)

(ref: ONeill21) O’Neill, T. J., Cosentino, G., Tan, J. C., Cheng, Y., & Liu, M. 2021, ApJ, 916, 45, doi: [`10.3847/1538-4357/ac062d`](http://doi.org/10.3847/1538-4357/ac062d)

(ref: Ossenkopf94) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: Padoan20) Padoan, P., Pan, L., Juvela, M., Haugbølle, T., & Nordlund, Å. 2020, ApJ, 900, 82, doi: [`10.3847/1538-4357/abaa47`](http://doi.org/10.3847/1538-4357/abaa47)

(ref: Padoan23) Padoan, P., Pelkonen, V.-M., Juvela, M., Haugbølle, T., & Nordlund, Å. 2023, arXiv e-prints, arXiv:2301.07398, doi: [`10.48550/arXiv.2301.07398`](http://doi.org/10.48550/arXiv.2301.07398)

(ref: Peretto13) Peretto, N., Fuller, G. A., Duarte-Cabral, A., et al. 2013, A&A, 555, A112, doi: [`10.1051/0004-6361/201321318`](http://doi.org/10.1051/0004-6361/201321318)

(ref: Peretto14) Peretto, N., Fuller, G. A., André, P., et al. 2014, A&A, 561, A83, doi: [`10.1051/0004-6361/201322172`](http://doi.org/10.1051/0004-6361/201322172)

(ref: Peretto20) Peretto, N., Rigby, A., André, P., et al. 2020, MNRAS, 496, 3482, doi: [`10.1093/mnras/staa1656`](http://doi.org/10.1093/mnras/staa1656)

(ref: Plunkett18) Plunkett, A. L., Fernández-López, M., Arce, H. G., et al. 2018, A&A, 615, A9, doi: [`10.1051/0004-6361/201732372`](http://doi.org/10.1051/0004-6361/201732372)

(ref: Pouteau22) Pouteau, Y., Motte, F., Nony, T., et al. 2022, A&A, 664, A26, doi: [`10.1051/0004-6361/202142951`](http://doi.org/10.1051/0004-6361/202142951)

(ref: Pouteau23) —. 2023, A&A, 674, A76, doi: [`10.1051/0004-6361/202244776`](http://doi.org/10.1051/0004-6361/202244776)

(ref: Aplpy12) Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python, Astrophysics Source Code Library. [`http://ascl.net/1208.017`](http://ascl.net/1208.017)

(ref: Rosolowsky08) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ, 679, 1338, doi: [`10.1086/587685`](http://doi.org/10.1086/587685)

(ref: Sadaghiani20) Sadaghiani, M., Sánchez-Monge, Á., Schilke, P., et al. 2020, A&A, 635, A2, doi: [`10.1051/0004-6361/201935699`](http://doi.org/10.1051/0004-6361/201935699)

(ref: Salpeter55) Salpeter, E. E. 1955, ApJ, 121, 161, doi: [`10.1086/145971`](http://doi.org/10.1086/145971)

(ref: Sanhueza19) Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886, 102, doi: [`10.3847/1538-4357/ab45e9`](http://doi.org/10.3847/1538-4357/ab45e9)

(ref: Sanhueza21) Sanhueza, P., Girart, J. M., Padovani, M., et al. 2021, ApJL, 915, L10, doi: [`10.3847/2041-8213/ac081c`](http://doi.org/10.3847/2041-8213/ac081c)

(ref: Schisano14) Schisano, E., Rygl, K. L. J., Molinari, S., et al. 2014, ApJ, 791, 27, doi: [`10.1088/0004-637X/791/1/27`](http://doi.org/10.1088/0004-637X/791/1/27)

(ref: Schmiedeke21) Schmiedeke, A., Pineda, J. E., Caselli, P., et al. 2021, ApJ, 909, 60, doi: [`10.3847/1538-4357/abd6ef`](http://doi.org/10.3847/1538-4357/abd6ef)

(ref: Smith09) Smith, R. J., Longmore, S., & Bonnell, I. 2009, MNRAS, 400, 1775, doi: [`10.1111/j.1365-2966.2009.15621.x`](http://doi.org/10.1111/j.1365-2966.2009.15621.x)

(ref: Stutzki90) Stutzki, J., & Guesten, R. 1990, ApJ, 356, 513, doi: [`10.1086/168859`](http://doi.org/10.1086/168859)

(ref: Suarez21) Suárez, G., Galván-Madrid, R., Aguilar, L., et al. 2021, ApJ, 921, 48, doi: [`10.3847/1538-4357/ac1bb9`](http://doi.org/10.3847/1538-4357/ac1bb9)

(ref: Takemura22) Takemura, H., Nakamura, F., Arce, H. G., et al. 2022, arXiv e-prints, arXiv:2211.10215. [`https://arxiv.org/abs/2211.10215`](https://arxiv.org/abs/2211.10215)

(ref: Takemura23) —. 2023, ApJS, 264, 35, doi: [`10.3847/1538-4365/aca4d4`](http://doi.org/10.3847/1538-4365/aca4d4)

(ref: Tanaka17) Tanaka, K. E. I., Tan, J. C., & Zhang, Y. 2017, ApJ, 835, 32, doi: [`10.3847/1538-4357/835/1/32`](http://doi.org/10.3847/1538-4357/835/1/32)

(ref: Vazquez19) Vázquez-Semadeni, E., Palau, A., Ballesteros-Paredes, J., Gómez, G. C., & Zamora-Avilés, M. 2019, MNRAS, 490, 3061, doi: [`10.1093/mnras/stz2736`](http://doi.org/10.1093/mnras/stz2736)

(ref: Wang16) Wang, K., Testi, L., Burkert, A., et al. 2016, ApJS, 226, 9, doi: [`10.3847/0067-0049/226/1/9`](http://doi.org/10.3847/0067-0049/226/1/9)

(ref: Wang14) Wang, K., Zhang, Q., Testi, L., et al. 2014, MNRAS, 439, 3275, doi: [`10.1093/mnras/stu127`](http://doi.org/10.1093/mnras/stu127)

(ref: Wang10) Wang, P., Li, Z.-Y., Abel, T., & Nakamura, F. 2010, ApJ, 709, 27, doi: [`10.1088/0004-637X/709/1/27`](http://doi.org/10.1088/0004-637X/709/1/27)

(ref: Williams94) Williams, J. P., de Geus, E. J., & Blitz, L. 1994, ApJ, 428, 693, doi: [`10.1086/174279`](http://doi.org/10.1086/174279)

(ref: Xu23) Xu, F.-W., Wang, K., Liu, T., et al. 2023, arXiv e-prints, arXiv:2301.01895, doi: [`10.48550/arXiv.2301.01895`](http://doi.org/10.48550/arXiv.2301.01895)

(ref: Zhang15) Zhang, Q., Wang, K., Lu, X., & Jiménez-Serra, I. 2015, ApJ, 804, 141, doi: [`10.1088/0004-637X/804/2/141`](http://doi.org/10.1088/0004-637X/804/2/141)

(ref: Zhou22) Zhou, J.-W., Liu, T., Evans, N. J., et al. 2022, MNRAS, 514, 6038, doi: [`10.1093/mnras/stac1735`](http://doi.org/10.1093/mnras/stac1735)

</paper>

Write the methods card for this paper.