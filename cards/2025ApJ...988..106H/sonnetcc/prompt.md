# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...988..106H\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...988..106H",
 "title": "Grand Design Spiral Arms in the Compact, Embedded Protoplanetary Disk of Haro 6-13",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Huang, Jane",
 "n_authors": 9,
 "arxiv_id": "2506.06433",
 "doi": "10.3847/1538-4357/ade1d8",
 "alma_projects_linked_by_archive": [
  "2016.1.01042.S",
  "2022.1.01365.S"
 ]
}
```

Paper text:
<paper>
# Grand Design Spiral Arms in the Compact, Embedded Protoplanetary Disk of Haro 6-13

## Abstract

Millimeter continuum spiral arms have so far only been detected in a handful of protoplanetary disks, and thus we have a limited understanding of the circumstances in which they can form. In particular, substructures in small disks ($R\lessapprox 50$ au) have not been well-characterized in comparison with large disks. We present ALMA 1.3 mm continuum observations of the disk around the T Tauri star Haro 6-13 at a resolution of $\sim0.04\ensuremath{''}$ ($\sim5$ au). A pair of low-contrast spiral arms are detected at disk radii from $\sim10-35$ au. They can be approximated as Archimedean spirals with pitch angles ranging from $\sim10-30^\circ$. The low value of the disk-averaged spectral index between 1.3 and 3 mm ($\alpha=2.1$) and the high brightness temperatures suggest that the millimeter continuum is likely optically thick and thus may hide sufficient mass for the disk to become gravitationally unstable and form spiral arms. CO observations have shown that Haro 6-13 is surrounded by an envelope, raising the possibility that infall is facilitating spiral arm formation.

UTF8gbsn

# Introduction

In the past decade, high resolution millimeter continuum observations have unveiled complex dust emission morphologies in numerous protoplanetary disks (cite: 2018ApJ...869L..41A; 2018ApJ...869...17L; 2021MNRAS.501.2934C; 2024ApJ...976..132H). Axisymmetric gaps and rings are the most frequently detected type of substructure, and are commonly (though not universally) hypothesized to be due to planet-disk interactions (cite: 2018ApJ...869L..42H; 2023ASPC..534..423B). Millimeter continuum spiral arm detections are comparatively rare; they have been observed in a handful of young, embedded Class 0/I disks (cite: 2014ApJ...796....1T; 2016Natur.538..483T; 2020ApJ...898...10T; 2020NatAs...4..142L; 2023ApJ...954..190X) and older Class II disks (cite: 2016Sci...353.1519P; 2018ApJ...860..124D; 2018ApJ...869L..43H; 2018ApJ...869L..44K; 2020MNRAS.491.1335R; 2021ApJ...916...51A).

In addition to millimeter continuum, spiral arms have also been observed in disks in scattered light and molecular emission (cite: 2004ApJ...605L..53F; 2012ApJ...748L..22M; 2014ApJ...785L..12C; 2017ApJ...840...32T; 2023ASPC..534..605B; 2023ASPC..534..423B). Scattered light and molecular emission trace surface and intermediate-height layers in the disk, whereas millimeter continuum emission originates from the dense midplane, where planet formation can take place. Spiral arms observed in one tracer do not necessarily have counterparts in others, suggesting that multiple spiral arm formation processes may be operating in disks, with varying influence in different vertical layers (cite: 2018AA...620A..94G; 2018ApJ...869L..43H; 2023ASPC..534..423B).

Diverse origins have been proposed for spiral arms associated with protostellar/protoplanetary disks. The dynamical influence of binary interactions or stellar flybys may be responsible for some observed spiral structures (cite: 2014ApJ...796....1T; 2016ApJ...816L..12D; 2018ApJ...869L..44K; 2020ApJ...896..132Z; 2020MNRAS.491.1335R), but most disks with reported detections of spiral arms have no known companions (cite: 2023ASPC..534..423B). Along similar lines, spiral arms in Class II disks are commonly hypothesized to be associated with a planetary perturber (cite: 2012ApJ...748L..22M; 2017ApJ...839L..24M; 2022ApJ...934L..11V), with directly imaged (candidate) companions reported in the HD 100546, AB Aur, HD 169142, and MWC 758 systems (cite: 2013ApJ...766L...1Q; 2022NatAs...6..751C; 2023MNRAS.522L..51H; 2023NatAs...7.1208W). Some systems have extended non-Keplerian spiral structures that appear to trace material infalling onto their disks (cite: 2017AA...603L...3A; 2021ApJ...908L..25G; 2022ApJ...930...91D). Several disks with spiral arms have been inferred to be gravitationally unstable either based on disk mass estimates and/or non-Keplerian kinematics (cite: 2016Natur.538..483T; 2020NatAs...4..142L; 2021ApJ...914...88P; 2023MNRAS.518.4481L; 2023ApJ...954..190X; 2024Natur.633...58S). In the Class 0 system L1448 IRS3B, gravitational instability (GI) has resulted in disk fragmentation to form a multiple star system. Meanwhile, for the detections in Class I and II disks, GI is of interest because it has been proposed as a pathway for forming planets either via fragmentation (cite: 1998ApJ...503..923B; 2004ApJ...609.1045M) or by enhancing the formation rate of large solids by trapping dust grains in spiral arms (cite: 2023MNRAS.519.2017L; 2024MNRAS.528.2490R). Identifying where and how spiral arms form is thus key for understanding what processes shape the structure and evolution of disks and set the conditions for planet formation.

Haro 6-13 (ICRS coordinates RA=04:32:15.417, DEC= +24:28:59.58) is a K5.5 T Tauri star located $127.7\substack{+1.7\\-1.6}$ pc away in the Taurus Molecular Cloud complex (cite: 2014ApJ...786...97H; 2021AA...649A...1G; 2021AJ....161..147B). Classifications of this source based on its spectral energy distribution have varied. It was designated as a Class I/II young stellar object (YSO) by (cite: 1995ApJS..101..117K), a flat spectrum YSO by (cite: 2010ApJS..186..259R), and a Class II YSO by (cite: 2010ApJS..186..111L), who did not use the flat spectrum category. In any case, ALMA CO observations have shown that Haro 6-13 has an envelope (cite: 2021AA...645A.145G). (cite: 2019ApJ...882...49L) estimated an age of $2.6\substack{+2.1\\-1.1}$ Myr based on comparisons of its stellar luminosity and effective temperature to evolutionary models. While age estimates of individual pre-main sequence stars are highly uncertain, Haro 6-13’s estimated age suggests that it could be an example of a system undergoing “late infall,” wherein a relatively evolved disk continues to accrete material from a remnant natal envelope or from encounters with nearby cloud material (cite: 2019AA...628A..20D; 2023EPJP..138..272K). Models have predicted that infall may facilitate the formation of different kinds of disk substructures, including gaps and rings, spiral arms, and vortices (cite: 2010ApJ...713.1143Z; 2015ApJ...805...15B; 2015AA...582L...9L; 2022ApJ...928...92K). Recent scattered light and molecular line observations of other systems provide some support for a connection between late infall and spiral formation in the disk upper layers (cite: 2021ApJ...908L..25G; 2021ApJS..257...19H; 2022AA...658A..63M), but the effect on the disk midplane has been less explored.

(cite: 2019ApJ...882...49L) previously observed the millimeter continuum of Haro 6-13 at a resolution of $0.1\ensuremath{''}$ (13 au) as part of a survey of Class II disks in the Taurus star-forming region. No clear substructure was identified in their image, and thus they characterized Haro 6-13 as a “smooth,” compact disk with an estimated effective radius of $R_\mathrm{95}=34$ au, where $R_\mathrm{95}$ is the radius enclosing 95% of the flux (cite: 2019ApJ...882...49L). At the resolution of their survey, the smaller disks appear to be generally more substructure-poor in comparison with the larger disks, and no spiral detections were reported for any system. However, non-axisymmetric residuals become apparent after they subtracted an axisymmetric intensity profile from the Haro 6-13 continuum. Based on 1D parametric visibility modeling of the same data, (cite: 2023ApJ...952..108Z) inferred that the millimeter continuum of Haro 6-13 has a gap at 16 au and ring at 20 au. Meanwhile, using super-resolution imaging of this data, (cite: 2024PASJ...76..437Y) inferred an inflection point, but not a gap (i.e., a local minimum) at a radius of 14 au. To investigate the nature of the substructures in the Haro 6-13 disk, we used ALMA to obtain high angular resolution 1.3 mm continuum observations. The observations are described in Section [2](#sec:observations). Models and analysis of the system are presented in Section [3](#sec:analysis). We discuss the results in Section [4](#sec:discussion) and close with a summary in Section [5](#sec:summary).

# Observations and Data Reduction

Long-baseline 1.3 mm continuum observations of Haro 6-13 were obtained as part of ALMA program 2022.1.01365.S (PI: J. Huang). The correlator was configured with four spectral windows (SPWs) centered at 224, 226, 240, and 242 GHz, each of which had 128 channels across a bandwidth of 2 GHz. Details of the observing setup are listed in Table [1](#tab:observations). A calibrated measurement set was produced by ALMA staff using the `CASA 6.4.1` pipeline (cite: 2022PASP..134k4501C)

| Program ID | Date | Baseline lengths | Number of antennas | Time on source | Calibrators |
|:---|:--:|:--:|:--:|:--:|:--:|
| 2016.1.01042.S | 2016 November 28 | 15.1 m - 704.1 m | 47 | 1.2 min | J0510+1800, J0438+3004 |
| 2016.1.01042.S | 2017 August 02 | 54.5 m - 3.3 km | 44 | 3 min | J0510+1800, J0423-0120, J0426+2327 |
| 2022.1.01365.S | 2023 July 19 | 230.2 m - 15.2 km | 47 | 32 min | J0429+2724, J0433+2905, J0510+1800 |

: Observational setup

Observations in a more compact antenna configuration were requested as part of the same program but ultimately were not taken. To provide coverage on shorter baselines, we retrieved 1.3 mm observations of Haro 6-13 from program 2016.1.01042.S (PI: C. Chandler) via the ALMA archive. Details of the observing setup are listed in Table [1](#tab:observations). The correlator was configured with 8 SPWs. Two SPWs were centered at 232.4 and 217.0 GHz, respectively, each with bandwidths of 2 GHz and 128 channels. The other SPWs each had bandwidths of 468.75 MHz. They were centered at 231.2 GHz (120 channels), 230.7 GHz (960 channels, covering $^{12}$CO $J=2-1$), 218.8 GHz and 219.3 GHz (60 channels each), and 219.7 and 220.2 GHz (480 channels each, covering C$^{18}$O and $^{13}$CO $J=2-1$, respectively). The raw data from 2016 November 28 were calibrated with the `CASA 4.7.2` pipeline, while the data from 2017 August 02 were processed using manual calibration scripts from the archive.

Further processing of the datasets was performed with `CASA` 6.5. We began by flagging the channels covered by CO isotopologue line emission in the short-baseline measurement sets from program 2016.1.01042.S and averaged the channels in each SPW to generate pseudo-continuum visibilities. Separate continuum images were generated for the two execution blocks (EBs) using `tclean`. Following the procedure described in (cite: 2018ApJ...869L..41A), we used the `imfit` task in `CASA` to fit a 2D Gaussian to each continuum image in order to locate the disk center, then used the `phaseshift` task to shift the disk center to the phase center and `fixplanets` to match the coordinates of the two execution blocks (EBs). We combined the two EBs and performed three rounds of phase self-calibration with intervals corresponding to the scan length, 60 s, and 15 s, and then one round of amplitude self-calibration with a scan-length solution interval. The full spectral resolution data were spatially aligned in the same manner as the continuum observations, and the self-calibration tables derived from the continuum data were applied. Continuum subtraction was performed in the $uv$ plane using `uvcontsub`. Multiscale CLEAN (cite: 2008ISTSP...2..793C) was used to image $^{12}$CO at a velocity resolution of 0.65 km s$^{-1}$ and $^{13}$CO and C$^{18}$O at a resolution of 1.35 km s$^{-1}$ (reflecting the lower native resolution of the latter two lines). We used a robust value of 0.5 and applied a $uv$-taper of $0.3''$ to improve the signal-to-noise ratio of the fainter, larger-scale emission. Since the emission morphology is irregular, the `auto-multithresh` algorithm (cite: 2020PASP..132b4505K) was used to create the CLEAN masks. After applying a primary beam correction to the image cubes, we produced integrated intensity maps of $^{12}$CO by summing up emission at LSRK velocities between 0.2 and 10.6 km s$^{-1}$ and of $^{13}$CO and C$^{18}$O by summing emission between 2.75 and 8.15 km s$^{-1}$, with negative pixels clipped to minimize artifacts from spatial filtering. The velocity ranges were chosen based on the detection of emission above the $3\sigma$ level. Intensity-weighted velocity maps were then produced using a 4$\sigma$ clip.

Next, we channel-averaged the SPWs from the long-baseline measurement set from 2022.1.01365.S and performed one round of phase self-calibration with a solution interval spanning the length of the observation. Then, the long-baseline observations were spatially aligned with the self-calibrated short-baseline continuum observations using the same procedure described above. The combined data were imaged with multiscale CLEAN and a robust value of 0.5. We performed two rounds of phase self-calibration on the combined data with scan-length and 30 s intervals, and then one round of amplitude self-calibration with a scan-length interval. Finally, a primary beam correction was applied. Image properties are listed in Table [2](#tab:imageproperties).[^1]

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| Image | Frequency | Synthesized beam | rms$^{a}$ |  |
|  | (GHz) | (arcsec $\times$ arcsec (deg)) | (mJy beam$^{-1}$) |  |
| Continuum | 229.496 | $0.037\ensuremath{''}\times0.022\ensuremath{''}$ $(19.08\ensuremath{^\circ})$ | 0.019 |  |
| $^{12}$CO $J=2-1$ | 230.538 | $0.47\ensuremath{''}\times0.42\ensuremath{''}$ $(-31.62\ensuremath{^\circ})$ | 7.5 |  |
| $^{13}$CO $J=2-1$ | 220.3986842 | $0.48\ensuremath{''}\times0.42\ensuremath{''}$ $(-32.99\ensuremath{^\circ})$ | 4.9 |  |
| C$^{18}$O $J=2-1$ | 219.5603541 | $0.47\ensuremath{''}\times0.42\ensuremath{''}$ $(-32.20\ensuremath{^\circ})$ | 4.0 |  |

: Image properties

Table notes: $^{a}$ Measured from line-free channels for the image cubes ($\Delta v = 0.65$ km s$^{-1}$ for $^{12}$CO and 1.35 km s$^{-1}$ for $^{13}$CO and C$^{18}$O), and from an off-source region for the continuum emission.

# Analysis

## Overview of continuum morphology

![](continuumoverview.pdf)

The 1.3 mm continuum image and corresponding intensity plot as a function of disk radius $R$ and azimuthal angle $\theta$ are shown in Figure [1](#fig:continuumoverview). The derivation of the position angle (P.A.) and inclination ($i$) used for deprojection is described in Section [\[sec:spiralproperties\]](#sec:spiralproperties). An angle of $\theta = 90^\circ$ corresponds to the side of the major axis that defines the position angle (east of north), and the angles increase in the clockwise direction. The continuum emission exhibits a faint pair of spiral arms. To enhance the spiral arm contrast, we applied unsharp masking, which subtracts a smoothed version of an image from the original image and then adds a scaled version of the difference image back to the original image. We used the implementation from `scikit-image`, specifying a scale factor of 2 and a Gaussian filter with a sigma parameter of $0.06\ensuremath{''}$. The resulting image and intensity plot in $R$ and $\theta$ are also shown in Figure [1](#fig:continuumoverview).

Figure [2](#fig:radialprofile) shows the azimuthally averaged, deprojected radial intensity profile made from the original CLEAN image of Haro 6-13’s continuum emission. The intensity profile drops steeply from the center of the disk until it flattens out at $R\approx15$ au, then drops steeply again beyond $R\approx25$ au. No clear gaps, rings, or cavities are visible, but it is possible that the slope change at $R\sim15$ au traces an unresolved gap. Beyond $R\approx40$ au, very faint emission is visible out to $R\approx70$ au. Without azimuthal averaging, this emission only appears as scattered $3\sigma$ peaks in the image, so it is not clear whether it originates from the Keplerian disk or from the envelope. Previous molecular line observations indicate that the Keplerian gas disk extends to a radius of 150 au (cite: 2021AA...645A.145G).

![](radialprofile.pdf)

## Spiral arm properties

To isolate the spiral structures from the disk background, we estimated and subtracted an axisymmetric intensity profile using the publicly available code `protomidpy`[^2], which implements the algorithm from (cite: 2024MNRAS.532.1361A). (We do not use the version of the image with unsharp masking for quantitative analysis because the process truncates the outer disk emission, which may bias spiral measurements). In brief, `protomidpy` assumes that the disk is axisymmetric and geometrically thin and models the 1D radial intensity profile $I(r)$ as a Fourier-Bessel series. The radial intensity profile model is regularized by a radial basis function kernel with hyperparameters $\alpha$ (which controls the weight of this prior) and $\gamma$ (which controls the spatial scale of the kernel). Model visibilities are calculated from the 1D radial intensity profile given the disk P.A., $i$, and offsets from the phase center ($\Delta x$ and $\Delta y$). `protomidpy` uses the affine invariant Markov Chain Monte Carlo (MCMC) code `emcee` (cite: 2013PASP..125..306F) to sample the posteriors for P.A., $i$, $\Delta x$, $\Delta y$, $\alpha$, and $\gamma$ while simultaneously estimating $I(r)$. The non-parametric modeling framework of `protomidpy` shares some similarities with the `frank` code (cite: 2020MNRAS.495.3209J), but the latter requires the user to specify the disk orientation, offset, and regularization hyperparameters.

Before modeling the visibilities with `protomidpy`, we used the `visread` package (cite: ian_czekala_2021_4432520), which implements the method described in (cite: 2023PASP..135f4503Z), to correct the absolute scaling of the weights in our measurement sets on a per-SPW basis. For the various observations, the weights were ultimately downscaled by factors ranging from $\sim1$ (weights were essentially correct) to $\sim5$.

We set flat priors with bounds of $[0,1]$ for $\cos i$, $[0^\circ, 180^\circ]$ for P.A., $[-0.1\ensuremath{''}, 0.1\ensuremath{''}]$ for $\Delta x$ and $\Delta y$, $[0.01\ensuremath{''}, 0.15\ensuremath{''}]$ for $\gamma$, and $[-4,5]$ for $\log\alpha$. The MCMC modeling was performed using 24 walkers over 15000 steps. The length of the chains was chosen to ensure that they were at least $50\times$ longer than the integrated autocorrelation time.[^3] After discarding the first 1000 steps for each walker as burn-in, we computed the medians and the 68% confidence interval. The parameter values are given in Table [3](#tab:protomidpy). Samples of the resulting $I(r)$ profiles inferred by `protomidpy` are plotted in Figure [3](#fig:protomidpy).

|            Parameter             |      Value      |
|:--------------------------------:|:---------------:|
|         $\Delta x$ (mas)         |  $3.61\pm0.06$  |
|         $\Delta y$ (mas)         |  $0.81\pm0.08$  |
|            P.A. (deg)            | $154.09\pm0.14$ |
|            $i$ (deg)             | $39.47\pm0.09$  |
| Hyperparameter $\gamma$ (arcsec) | $0.079\pm0.003$ |
|   Hyperparameter $\log \alpha$   |   $0.5\pm0.2$   |

: Inferred `protomidpy` parameter values

![](protomidpymodel.pdf)

We then CLEANed the model visibilities generated by `protomidpy` from its *maximum a posteriori* estimate of $I(r)$ in the same manner as the observations shown in Figure [1](#fig:continuumoverview). Next, we CLEANed the residual visibilities created by subtracting the model visibilities from the observed visibilities, employing a $uv$ taper of $0.02\ensuremath{''}$ to improve the signal-to-noise ratio of the residual emission. The resulting synthesized beam is $0.046\ensuremath{''}\times0.030\ensuremath{''}$ $(15.9\ensuremath{^\circ})$. The CLEAN image of the axisymmetric `protomidpy` model, comparison of the radial profiles calculated from the CLEAN images of the model and observations, CLEAN image of the residual visibilities, and corresponding intensity plots in $R$ and $\theta$ coordinates are also presented in Figure [3](#fig:protomidpy). The spiral that terminates on the southwestern side of the disk is labelled S1, while the one that terminates on the northeastern side of the disk is labelled S2. S2 appears to have both a greater inward and outer radial extent compared to S1. In addition, S2 appears to be connected to a bar-like structure at the center of the disk. However, tests on synthetic data from (cite: 2024MNRAS.532.1361A) show that spiral structure can appear significantly distorted within a beam or so from the disk center, so higher resolution observations should be obtained to confirm whether a bar is genuinely present.

Next, we used `filfinder` (cite: 2015MNRAS.452.3435K; 2016ascl.soft08009K) to extract the sky coordinates of the spiral arms from the `protomidpy` residual image. While `filfinder` was originally designed to identify filaments in maps of molecular clouds, (cite: 2022ApJ...928....2I) demonstrated its utility in a protoplanetary disk context by identifying spiral structures in CO velocity residuals. After some experimentation, we set a smoothing size of 2 pixels (corresponding to $0.006\ensuremath{''}$), an intensity threshold of 0.03 mJy beam$^{-1}$, a threshold of 4 pixels (corresponding to $0.012\ensuremath{''}\sim1.5$ au) for the width of the adaptive thresholding mask, a size threshold of 300 au$^2$, and a minimum length of 3 synthesized beams. As shown in Figure [3](#fig:protomidpy), `filfinder` identifies one structure corresponding to S1 and another structure that corresponds to S2 and the central bar-like residual.

The spiral coordinates identified by `filfinder` were then converted to disk polar coordinates $R$ and $\theta$, as shown in Figure [4](#fig:spiralfits). The $\theta$ values are unwrapped to avoid jumps of $2\pi$, so for portions of the spirals, their values may differ by $2\pi$ from Figure [3](#fig:protomidpy). For S2, the points identified by `filfinder` with $R<10$ au are not plotted because they are associated with the central bar-like residual. The pitch angle $\beta$ of a spiral arm can be calculated from $\tan \beta = \left| \frac{d\ln R}{d\theta} \right|$. Thus, in a $\ln R$-$\theta$ plot, a spiral with constant pitch angle (a logarithmic spiral) will appear as a straight line, a spiral with a pitch angle that increases with $R$ will have a derivative with an absolute value that increases with $R$, while a spiral with a pitch angle that decreases with $R$ will have a derivative with an absolute value that decreases with $R$. S1 is only detected over a relatively small polar angle range (from $\theta\sim1-3$ radians), for which it is difficult to distinguish whether the pitch angle is varying (cite: 2018ApJ...869L..43H; 2018ApJ...869L..44K). However, S2 can be traced over a wider range, from $\theta\sim-3.5$ to 1 radian. S2 flattens out as $R$ increases, indicating that the pitch angle is decreasing with radius. We thus model S1 and S2 as Archimedean spirals, which take the form $R(\theta) = a-b\theta$.

Adjacent pixels are not independent because the synthesized beam is oversampled. To account for correlated noise in our measurements of the spiral arm positions, we used the `george` package (cite: 2015ITPAM..38..252A) to perform Gaussian process regression. The elements of the covariance matrix are modelled as the sum of a white noise component and a squared exponential kernel:

$$\begin{equation}
K_{ij} = \sigma^2 \delta_{ij}+A\exp\left[-\frac{(\theta_i-\theta_j)^2}{2C}\right]
\end{equation}$$ The squared exponential kernel specifies high covariance for datapoints that are close to one another and low covariance for datapoints that are far away from each other, which is qualitatively consistent with the behavior of pixels in an image with finite resolution.

Each of the arms were fit independently for the spiral geometry parameters $\ln a$ and $\ln b$ and the hyperparameters $\ln(\sigma^2)$, $\ln A$, and $\ln C$. The fit is performed in log space because $a$, $b$, $\sigma^2$, $A$, and $C$ must all be positive. For $\ln a$, we set a flat prior with bounds of $[3,5]$ for S1 and $[1,4]$ for S2. For both arms, we set flat priors with bounds of $[1,3]$ for $\ln b$, $[-5, 5]$ for $\ln \sigma^2$, $[-4,4]$ for $\ln A$, and $[-10, 0]$ for $\ln C$.

![](spiralfits.pdf)

We used `emcee` to sample the posterior distributions. To model each arm, an ensemble of 30 walkers was evolved for 5,000 burn-in steps and then an additional 10,000 steps. Table [4](#tab:spiralparameters) lists the median and the $68\%$ confidence interval for each parameter. Figure [4](#fig:spiralfits) compares the data with the model Archimedean spirals, which appear to reasonably reproduce the observations. We then calculated the pitch angles as a function of radius from the spiral models (Figure [5](#fig:pitchangle)). For S1, the pitch angle ranges from $25^\circ$ at $R=15$ au to $13^\circ$ at $R=31$ au. For S2, the pitch angle ranges from $33^\circ$ at $R=10$ au to $10^\circ$ at $R=38$ au. S1 appears to have a slightly larger pitch angle than S2 at the same radii, but the pitch angles of the two arms are consistent within the uncertainties.

| Parameter | S1 | S2 |
|:--:|:--:|:--:|
| $a$ (au) | $37.6\pm0.7$ | $14.6\pm0.5$ |
| $b$ (au) | $7.2\pm0.3$ | $6.4\pm0.2$ |
| $\ln (\sigma^2/\text{au}^2)$ | $-3.8\pm0.2$ | $-3.2\pm0.1$ |
| $\ln (A/\text{au}^2)$ | $-0.7\substack{+0.5\\-0.4}$ | $0.8\substack{+0.3\\-0.2}$ |
| $\ln (C)$ | $-4.7\substack{+0.8\\-0.2}$ | $-4.9\pm0.1$ |

: Spiral model parameters

We then measured the contrast of each spiral arm. The spiral arm intensities were extracted from the original CLEAN image of the disk (shown in Figure [1](#fig:continuumoverview)) along the coordinates of the best-fit Archimedean spiral arms. The “background” was estimated by measuring the minimum intensity of the disk in radial bins of 1 au and then interpolating at the radial locations of the pixels that fall along the model spiral arms. The contrast of each arm is then the spiral arm intensity divided by the “background” intensity. The uncertainty on the spiral arm and background intensity measurements was assumed to be the rms of the image. The contrasts are plotted in Figure [5](#fig:pitchangle). Over the radii where both arms are detected, their contrasts are similar to one another and generally low ($<1.5$). The contrasts are nearly flat between radii of 10 and 30 au, but appear to rise for S2 beyond 30 au. This rise roughly coincides with the radius at which the radial intensity profile drops steeply. The increase in contrast is likely due to some combination of lower optical depths at larger radii as well as having a larger number of resolution elements along the azimuthal direction.

![](pitchangle.pdf)

Our spiral geometry measurements assume that the millimeter continuum disk is geometrically thin. While millimeter wavelength observations indicate that the large dust grains in Class II disks are often well-settled (cite: 2022ApJ...930...11V; 2023MNRAS.524.3184P), observations of younger Class 0 and I systems suggest that the millimeter wavelength emission sometimes comes from more elevated heights due to a lesser degree of settling (cite: 2023ApJ...946...70V; 2023ApJ...951....8O). Models have shown that infall can lead to enhanced turbulence levels in disks (cite: 2022ApJ...928...92K; 2024ApJ...972L...9W), which may inhibit vertical settling. (cite: 2021ApJ...916...51A) demonstrated that for disks with elevated emission surfaces, subtracting a geometrically thin axisymmetric emission model leaves antisymmetric residuals on opposide sides of the major axis. This may contribute to the apparent difference in the extents of S2 and S1, as well as the bar-like residual near the disk center.

## Evidence for high millimeter continuum optical depths

From our observations, we measure a flux of 144.8 mJy at 229.5 GHz (1.3 mm) inside a circular region with a $1''$ radius. This value is consistent with the 1.3 mm flux from (cite: 2019ApJ...882...49L). Given the high SNR of our data, the dominant source of uncertainty is the 10% systematic flux calibration uncertainty. Meanwhile, (cite: 2019ApJ...877L...2H) reported a flux of 24.96 mJy at 97.5 GHz (3 mm). The flux measurements at 229.5 and 97.5 GHz yield a disk-averaged spectral index of $\alpha = \ln\frac{I_{\nu_1}}{I_{\nu_2}}/\ln{\frac{\nu_1}{\nu_2}} = 2.1\pm0.2$. Because the 3 mm observations from (cite: 2019ApJ...877L...2H) only marginally resolve the disk, we cannot meaningfully estimate a radially resolved spectral index profile. Using CARMA, (cite: 2015ApJ...808..102K) measured disk fluxes of 111.2 mJy at 229 GHz and 28.7 mJy at 113 GHz. Again assuming a 10% systematic flux calibration uncertainty, their measurements yield a disk-averaged $\alpha = 1.9\pm0.2$, which is consistent with our estimate from ALMA.

Low spectral index values (near $\alpha\approx2$) can result from optically thick dust emission (cite: 2012AA...540A...6R; 2019ApJ...877L..22L; 2019ApJ...877L..18Z). Assuming a standard power-law grain size distribution and a DSHARP dust composition (cite: 2018ApJ...869L..45B), optically thin emission from large dust grains (maximum sizes of several millimeters or greater) can yield spectral index values as low as $\sim2.5$ (cite: 2019ApJ...877L..18Z). Our low spectral index value is compatible with the disk being optically thick, but given the uncertainties, optically thin emission from large dust grains is not ruled out based on spectral index alone.

However, the high brightness temperatures of our 1.3 mm continuum emission also point to high optical depths. In the absence of scattering, the brightness temperature should saturate at the dust temperature. With scattering, the observed intensity $I_\nu$ will saturate below blackbody values, with $\chi \equiv \frac{I_\nu}{B_\nu}$ as low as $\sim0.6$ for the DSHARP dust composition (cite: 2019ApJ...877L..18Z). We use the following analytic formula for a passively irradiated disk from (cite: 2018ApJ...869L..46D) to estimate the dust temperature: $$\begin{equation}
\label{eq:Tdust}
T_d(R)  = \left( \frac{\varphi L_\ast}{8\pi R^2\sigma_\mathrm{SB}}\right)^{0.25}.
\end{equation}$$ As in (cite: 2018ApJ...869L..46D), we set the flaring angle $\varphi$ to 0.02. The luminosity of Haro 6-13 is $L_\ast = 0.79$ $L_\odot$ (cite: 2019ApJ...882...49L). Figure [6](#fig:brightnesstemps) compares the observed brightness temperatures (calculated from the CLEAN image using the full Planck function) to the brightness temperatures corresponding to our calculated dust temperatures for the cases of 1) optically thick emission with no scattering and 2) optically thick emission with $\chi=0.6$. Throughout most of the region in which spiral arms are detected, the observed brightness temperature is marginally below the estimated dust temperature and above the corresponding brightness temperature for the case with $\chi=0.6$ (high scattering). Interior to the spiral arms, the analytic dust temperature formula actually underestimates the brightness temperature, except in the inner few au, where beam dilution leads to an artificially low brightness temperature. In any case, while we only have a crude estimate of the dust temperature, it serves to demonstrate that the observed brightness temperatures are in the range of brightness temperatures expected when optical depths are high.

![](brightnesstemps.pdf)

## CO isotopologue emission

![](COmaps.pdf)

The integrated intensity maps, intensity-weighted velocity maps, and spectra of the CO isotopologues are shown in Figure [7](#fig:COmaps). The $^{12}$CO and $^{13}$CO spectra were extracted from circular apertures centered on the disk with radii of $6''$ (770 au). Meanwhile, the spectrum of C$^{18}$O, which is detected over a smaller spatial extent, was extracted with a circular aperture with a radius of $1.5\ensuremath{''}$. $^{12}$CO and $^{13}$CO are dominated by envelope emission extending to hundreds of au south and west of the star. The spectra show that the bulk of the observed emission is blueshifted with respect to the systemic velocity of 5.9 km s$^{-1}$ (cite: 2021AA...645A.145G), with much of the redshifted emission absorbed and/or resolved out, leading to the sharp drop in emission around the systemic velocity. The optically thinner C$^{18}$O emission is more symmetric about the systemic velocity, with a hint of a double-peaked Keplerian profile. Its intensity-weighted velocity map shows redshifted emission to the northwest of the star and blueshifted emission southeast of the star, consistent with the Keplerian disk rotation pattern observed in higher spectral resolution H$_2$CO and CS observations by (cite: 2021AA...645A.145G). However, as with $^{12}$CO and $^{13}$CO, the C$^{18}$O integrated intensity map also shows more extended blueshifted emission south of the star. Given the coarse spectral resolution of the data, it is not straightforward to distinguish disk and envelope contributions to the C$^{18}$O emission. However, the CS observations from (cite: 2021AA...645A.145G) show a non-Keplerian blueshifted component south of the star, suggesting that envelope emission is also contributing to the C$^{18}$O emission asymmetry. The C$^{18}$O spectrum also shows a small spike in emission at $\sim11$ km s$^{-1}$ that is not observed in either $^{13}$CO or $^{12}$CO. Inspection of the image cube does not reveal any obvious coherent structure at this velocity, so this is likely to be a noise fluctuation.

# Discussion

## Assessing possible explanations for Haro 6-13’s spiral arms

### Gravitational instability

Spiral arms can form in disks when the Toomre $Q$ parameter (cite: 1964ApJ...139.1217T) is $\lessapprox$2 (cite: 2004MNRAS.351..630L; 2009MNRAS.393.1157C). For a Keplerian disk, $$\begin{equation}
Q = \frac{c_s \Omega_K}{\pi G \Sigma},
\end{equation}$$ where $c_s =\sqrt{\frac{kT}{\mu m_H}}$ is the sound speed, $\mu=2.37$ is the mean molecular weight, $\Omega_K = \sqrt{\frac{GM_\ast}{R^3}}$ is the angular velocity at disk radius $R$, $G$ is the gravitational constant, and $\Sigma$ is the disk surface density. GI thus requires high disk surface densities, and is more readily maintained through the ongoing delivery of material via infall (cite: 2010ApJ...713.1143Z; 2011MNRAS.413..423H; 2014ApJ...795...61B). In addition, 3D hydrodynamical (cite: 2016SciA....2E0875L) and magnetohydrodynamical zoom-in simulations (cite: 2018MNRAS.475.2642K) demonstrated that infalling material can locally trigger GI in the disk. The presence of envelope material around Haro 6-13 therefore motivates the consideration of GI as the origin of its spiral arms. As noted in Section [\[sec:spiralproperties\]](#sec:spiralproperties), the observations of Haro 6-13 suggest that the millimeter continuum is likely optically thick. At high optical depths, the disk dust surface density cannot be well-constrained, but we can estimate a lower bound for the dust surface density and thus an upper bound for Q.

In the absence of scattering, the dust surface density is given by

$$\begin{equation}
\Sigma_\mathrm{dust}(R) = \frac{\tau_\nu(R)}{\kappa_\nu^\mathrm{abs}},
\end{equation}$$ where $\kappa_\nu^\mathrm{abs}$ is the dust absorption coefficient. The optical depth is given by $$\begin{equation}
\label{eq:tau}
\tau_\nu(R) = -\cos i  \ln \left(1-\frac{I_\nu(R)}{B_\nu(T_d)} \right), 
\end{equation}$$ where $B_\nu(T_d)$ is the Planck function.

The dust temperature at each value of $R$ is calculated by taking the maximum of either the observed brightness temperature or the dust temperature calculated with Equation [\[eq:Tdust\]](#eq:Tdust), since the observed brightness temperature must set the lower bound for the dust temperature. We restrict the estimate of $\tau$ to $R>5$ au because beam dilution leads to artificially low estimates of $\tau$ in the inner disk. For the regions in the inner disk where the observed brightness temperature exceeds the dust temperature calculated from Equation [\[eq:Tdust\]](#eq:Tdust), we set $\tau=4$ under the assumption that $\tau$ is no lower than the values calculated outside this region. Then, $\Sigma_\mathrm{dust}$ is calculated using values of $\kappa_\nu^\mathrm{abs} = 0.4$, $1.9$, and $1.0$ cm$^{2}$ g$^{-1}$. These values correspond to the DSHARP dust opacities at a wavelength of 1.3 mm, calculated for a grain size distribution of $n(a)\,da\propto a^{-3.5}\,da$ and maximum grain sizes of $a_\mathrm{max} = 0.1$, $1$, and $10$ mm, respectively (cite: 2018ApJ...869L..45B; 2018zndo...1495277B). Finally, $Q$ is calculated assuming that $M_\ast = 0.91$ $M_\odot$ (cite: 2019ApJ...882...49L) and the gas-to-dust ratio is 100. The results are plotted in Figure [8](#fig:Qplots). Over the radial range in which the spiral arms are detected, the Toomre Q parameter values are generally low ($<4$). For certain choices of grain properties ($a_\mathrm{max}$ = 100 $\mu$m and $a_\mathrm{max}$ = 1 cm), $Q$ dips into the gravitationally unstable regime ($\lessapprox2$). In the optically thick regime, the derived value of $Q$ is highly sensitive to the temperature profile, which is not well-constrained by our data. Nevertheless, these calculations indicate that the dust optical depths do not need to be extremely high for the disk to become gravitationally unstable. In addition, multi-frequency studies of scattering in other disks have shown that absorption-only estimates of dust surface densities at millimeter wavelengths can lead to underestimates by a factor of a few (cite: 2019ApJ...883...71C; 2021AA...648A..33M), so the Toomre Q values for Haro 6-13 could be significantly lower than our estimates. Spatially-resolved observations of Haro 6-13 at multiple longer wavelengths would probe optically thinner emission and can therefore aid in inferring the dust grain properties and improve estimates of the dust surface density.

![](Qplots.pdf)

Alternatively, one might seek to estimate a disk mass from the low-resolution C$^{18}$O $2-1$ observations (the spiral arm region is not resolved in these data). The flux measured within a circle centered on the disk with a $1''$ radius (130 au) is 460 mJy km s$^{-1}$. Based on the grid of thermochemical models of compact disks presented in (cite: 2021AA...651A..48M), which assume an ISM-like CO:H$_2$ abundance, the C$^{18}$O flux translates to a maximum disk mass of $\sim10^{-2}$ $M_\odot$, corresponding to a disk-to-stellar mass ratio of $\sim0.01$. Gravitationally unstable disks are expected to have disk-to-stellar mass ratios exceeding 0.1 (cite: 2016ARAA..54..271K). However, higher resolution observations of H$_2$CO and CN exhibit negative fluxes in the inner disk, which (cite: 2021AA...645A.145G) attribute to a combination of foreground absorption and high continuum optical depth. If C$^{18}$O is similarly afflicted, then it would not be a reliable probe of the surface density in the spiral arm region of the disk.

Simulations of spiral arms excited by GI have yielded different predictions for pitch angle behavior. (cite: 2009MNRAS.393.1157C) and (cite: 2018ApJ...860L...5F) found that the pitch angles were approximately constant, which would be at odds with our observations (under the assumption that the vertical thickness of the disk does not significantly distort the apparent geometry). However, (cite: 2021ApJ...906...19C) found that for sufficiently massive and cold disks, the pitch angle could decrease with radius, similar to our observations.

### Infall

Perturbations due to infalling material can also directly excite spiral arms in a non-self-gravitating protoplanetary disk and thus influence angular momentum transport through the disk (cite: 2015AA...582L...9L; 2017AA...599A..86H; 2025MNRAS.537.2695C). Given the presence of an envelope around Haro 6-13, it is plausible that its spiral arms are infall-related. In the case of infall-induced spiral arms, the pitch angles are expected to increase toward the site of interaction between the disk and infalling material (cite: 2025MNRAS.537.2695C). Searching for tracers of accretion shocks, such as SO or SO$_2$ (cite: 2021AA...653A.159V; 2022AA...658A.104G), would provide insight into where the Haro 6-13 disk is being directly perturbed.

Among the six Class I and II disks now known to have millimeter continuum spiral arms but no identified stellar or planetary companions (Elias 27, WaOph 6, IM Lup, TMC 1A, Haro 6-13, HD 143006), at least three of these (Elias 27, TMC 1A, and Haro 6-13) are known to be associated with envelope material (cite: 2016Sci...353.1519P; 2020NatAs...4..142L; 2023ApJ...954..190X; 2021AA...645A.145G). HH 111 VLA 1 is an embedded disk at a projected separation of 1200 au from another star, but (cite: 2020NatAs...4..142L) argue that the spiral arms of HH 111 VLA 1 are not likely to be associated with the other source due to their large separation. CO observations of IM Lup suggest that it may also have a remnant envelope (cite: 2016ApJ...832..110C). This hints that the conditions found in embedded disks and disks that are emerging from their envelopes may be facilitating the formation of millimeter continuum spiral arms.

### Planetary or stellar companions

Planetary or stellar companions can trigger spiral density waves in protoplanetary disks, with the pitch angle increasing toward the perturber (cite: 1986ApJ...307..395L; 2002ApJ...565.1257T; 2018ApJ...859..119B). However, Haro 6-13 has no known companions. (cite: 2007ApJ...662..413K) used 2MASS (cite: 1990AJ.....99.1187S) to catalog wide binary systems in Taurus. No binary companions were identified for Haro 6-13 at separations between 1 and $30''$ ($\sim130-3800$ au.) Haro 6-13 is separated by $31''$ ($\sim4000$ au) from 2MASS J04321327+2429107. The former is thus sometimes referred to as Haro 6-13E in the literature, and the latter as Haro 6-13W. Nevertheless, Haro 6-13 generally has been classified as a single star because of the rarity of binaries at such wide separation (cite: 2004AJ....127.1747H; 2007ApJ...662..413K; 2008AJ....135.2496C). Even if Haro 6-13W were a bona fide companion, any spirals in the disk would be expected to be very tightly wound due to the extremely wide separation of the two stars, contrary to what is observed (cite: 2018ApJ...859..118B). Meanwhile, high values of the Gaia renormalized unit weight error statistic (RUWE) can be checked for evidence of an unresolved companion within $1''$ (cite: 2018AJ....156..259Z). Haro 6-13’s RUWE value is 2.4 (cite: 2023AA...674A...1G), within the range expected for single disk-bearing stars (cite: 2022RNAAS...6...18F).

(cite: 2020MNRAS.498.1382W) conducted a high-contrast imaging survey of disks in Taurus in the L’ filter, including Haro 6-13, placing constraints on the presence of companions out to 3” ($\sim400$ au at the distance of Haro 6-13). The survey reached a $5\sigma$ contrast of $\Delta m=6$ at $0.2\ensuremath{''}$ and $\Delta m\gtrapprox8$ at separations above $0.5\ensuremath{''}$. Assuming a hot start model and ignoring circumstellar extinction, they estimated that the median mass limit of the survey was 15 $M_J$ at 20 au and 3 $M_J$ at 150 au. Extinction from the envelope around Haro 6-13, though, may make it challenging to detect planetary or stellar mass companions from the ground. Mid-IR observations (i.e., with the James Webb Space Telescope) would be useful for searching for a companion. The Haro 6-13 disk also does not feature any clear gaps or rings that may be indicative of an embedded companion, although high optical depths at 1.3 mm may hide substructures that could be detectable in high-resolution images at longer wavelengths with the Next Generation Very Large Array (ngVLA).

### Stellar flybys

Spiral arms in disks may also result from stellar flybys (cite: 1993MNRAS.261..190C; 2019MNRAS.483.4114C). The spiral arms induced by flybys are only expected to survive for a few thousand years (cite: 2019MNRAS.483.4114C), so the perturbing star would be expected to still be nearby if the spiral arms are visible. As noted in the above discussion of stellar companions, Haro 6-13 does not have any known nearby stellar-mass perturbers. Furthermore, in systems that have been identified as likely having undergone a recent flyby, prominent extended structures that appear to be tidally induced have typically been detected in CO emission (cite: 2006AA...452..897C; 2018ApJ...869L..44K; 2020ApJ...896..132Z; 2022NatAs...6..331D). Similar structures have not been identified in molecular line observations of Haro 6-13 (cite: 2021AA...645A.145G).

## Implications for compact protoplanetary disks

Sensitive, high spatial resolution (better than $\sim10$ au) observations of protoplanetary disks have primarily targeted large disks with millimeter continuum emission extending to radii of at least 50 au and have shown that these disks are usually highly structured (cite: 2018ApJ...869L..41A; 2021MNRAS.501.2934C). However, the majority of millimeter continuum disks, including Haro 6-13, appear to be more compact (cite: 2019ApJ...882...49L; 2020ApJ...895..126H). The faint, extended emission observed in the Haro 6-13 disk (Figure [2](#fig:radialprofile)) may bring into question how disk sizes should be defined (conventionally based on the radius enclosing some percentage of the flux), but this could also be an issue for many other disks that have been described as “compact” because most have only been observed at moderate sensitivity. Several recent studies have targeted compact disks with ALMA’s long baselines in order to examine to what extent the kinds of substructures commonly detected in large disks are also present in small disks, generally turning up a mixture of ringed and apparently featureless disks (cite: 2019AA...626L...2F; 2024AA...682A..55M; 2025AA...696A.232G).

If the Haro 6-13 disk is determined to be gravitationally unstable, it would be the smallest such disk identified to date. The other Class I and II disks for which gravitational instability has been suggested as a possible origin for their millimeter continuum spiral arms (IM Lup, Wa Oph 6, Elias 27, TMC 1A, HH 111 VLA 1, MWC 758) have had disk emission detected at large radii, beyond 100 au (cite: 2016Sci...353.1519P; 2018ApJ...860..124D; 2018ApJ...869L..43H; 2020NatAs...4..142L; 2023ApJ...954..190X). Alternatively, if Haro 6-13’s spiral arms result from stellar flybys or direct perturbations from infall in the absence of GI, their radial extent would suggest that external perturbations can affect disk dynamics in the midplane on scales comparable to the semi-major axes of the Solar System giant planets. Millimeter continuum spiral arms have seldom been resolved inside compact disks (although some compact disks are known to have spiral arms surrounding them in extended circumbinary material (cite: 2014ApJ...796....1T; 2020ApJ...898...10T; 2022ApJ...930...91D)). The notable exceptions are the HT Lup A, AS 205 N, and HD 100453 disks, which have millimeter continuum radii of $\sim30-60$ au and stellar companions that are orbiting outside the spiral arms at projected separations ranging from $\sim25-170$ au (cite: 2018ApJ...869L..44K; 2020MNRAS.491.1335R). The small sizes of these disks may be due to truncation by the companions (cite: 1993MNRAS.261..190C; 1994ApJ...421..651A). After DSHARP, which detected two of the known cases of millimeter continuum spiral arms inside compact disks, high resolution millimeter continuum disk surveys have generally been at lower sensitivity (cite: 2021MNRAS.501.2934C; 2024ApJ...966...59S; 2025AA...696A.232G). While gaps and rings can be high-contrast enough to be detectable at relatively low sensitivities, millimeter continuum spiral arms typically have low contrasts (cite: 2018ApJ...869L..43H). The detection of spiral arms in our new observations of the Haro 6-13 disk, which is not known to have a companion, motivates further deep, high resolution imaging of the compact disk population without known companions to ensure that searches for spiral arms are appropriately inclusive and to improve our understanding of the kinds of systems in which they are prevalent.

High-resolution studies of several disks have found evidence that they are optically thick in their inner 20-30 au at millimeter wavelengths (cite: 2021AA...648A..33M; 2023AA...673A..77R; 2024NatAs...8.1148U). Haro 6-13 likewise appears to be optically thick interior to 30 au. It has been questioned whether there is a discrepancy between protoplanetary disk masses and exoplanet masses (cite: 2014MNRAS.445.3315N; 2018AA...618L...3M). However, high optical depths can lead to significant underestimates of disk masses and greater difficulties in detecting substructures. This problem points to a use case for the ngVLA, which would be able to obtain high resolution images of disks at longer wavelengths, where the optical depth is lower and the dust surface density profiles can therefore be measured more accurately. However, free-free contamination may pose a challenge to characterizing dust properties at these longer wavelengths.

## Haro 6-13 as a (mild) cautionary tale

Given the lengthy integration times and good weather required to obtain high signal-to-noise long-baseline ALMA observations, it has been popular to explore how to maximize the information that can be extracted from lower-resolution observations. Visibility modeling and super-resolution imaging techniques have proven to be successful in discerning the presence of disk substructures that are not readily apparent in the CLEAN images (cite: 2016ApJ...818L..16Z; 2020MNRAS.495.3209J; 2023PASP..135f4503Z).

Our new Haro 6-13 observations, though, also highlight some of the limitations of the aforementioned techniques. Searches for substructures via visibility modeling have mostly assumed that the disk is axisymmetric (cite: 2016ApJ...818L..16Z; 2020MNRAS.495.3209J; 2023ApJ...952..108Z). High-resolution disk images suggest that this assumption is reasonable most of the time (cite: 2018ApJ...869L..42H; 2021MNRAS.501.2934C). However, when azimuthally averaged, disks with spiral arms may appear as though they have (additional) gaps and rings (cite: 2022MNRAS.509.2780J). Consequently, the presence of protoplanets may be erroneously inferred if one is not aware of the spiral arms. In addition, Haro 6-13’s spiral structures appear ring-like in super-resolution images made from observations with baselines up to $\sim3700$ km and $\sim4$ minutes on source (cite: 2024PASJ...76..437Y). Hence, our sensitive ALMA observations with $4\times$ longer baselines have been essential for understanding the true morphology of the Haro 6-13 disk. As noted by (cite: 2018ApJ...869L..41A), a spatial resolution of 5 au or better is desirable for investigating disk substructures because it is comparable to the expected pressure scale height at several tens of au. Models indicate that the scale height is closely linked to the characteristic size scales of substructures (cite: 1999ApJ...514..344B; 2009ApJ...697.1269J). Nevertheless, even if visibility modeling and super-resolution imaging do not capture the exact nature of the substructures present, they can still be useful for identifying systems that would be interesting for follow-up at higher resolution and sensitivity.

# Summary

We present the highest resolution millimeter continuum observations to date of the Haro 6-13 protoplanetary disk. A pair of low-contrast spiral arms is detected, making the Haro 6-13 disk one of the smallest disks in which millimeter continuum spiral arms have been observed. The arms can be modelled as Archimedean spirals with pitch angles ranging from $\sim10-30^\circ$. The low value of the $229.5-97.5$ GHz (1.3-3 mm) spectral index ($\alpha=2.1$) and the high brightness temperatures provide evidence that the millimeter continuum is optically thick. The evidence for high optical depths and the presence of envelope material motivate further exploration of GI as an explanation for the spiral arms. In the absence of GI, perturbations from infall may still contribute to spiral arm formation. The Haro 6-13 disk helps to demonstrate that diverse substructures can be found in compact protoplanetary disks and points to the need for further observations of spatially resolved, optically thin disk tracers in order to probe the mass reservoir in the inner tens of au.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.01365.S and #2016.1.01042.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We also thank our contact scientist Ryan Loomis for his assistance. MB has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (PROTOPLANETS, grant agreement No. 101002188). SF is funded by the European Union (ERC, UNVEIL, 101076613), and acknowledges financial contribution from PRIN-MUR 2022YP5ACE. Views and opinions expressed, however, are those of the author(s) only and do not necessarily reflect those of the European Union or the ERC. Neither the European Union nor the granting authority can be held responsible for them. The research of MK is funded by a Reintegration fellowship of the Carlsberg Foundation (CF22-1014).

# Facilities

ALMA

# Software

`analysisUtils` (cite: 2023zndo...7502160H), `AstroPy` (cite: 2013AA...558A..33A; 2018AJ....156..123A; 2022ApJ...935..167A), `CASA` (cite: 2022PASP..134k4501C), `cmasher` (cite: cmasher), `dsharp_opac` (cite: 2018zndo...1495277B),

`emcee` (cite: 2013PASP..125..306F), `filfinder` (cite: 2015MNRAS.452.3435K; 2016ascl.soft08009K), `george` (cite: 2015ITPAM..38..252A), `matplotlib` (cite: Hunter:2007), `protomidpy` ((cite: 2024MNRAS.532.1361A), <https://github.com/2ndmk2/protomidpy>), `scikit-image` (cite: scikit-image), `visread` (cite: ian_czekala_2021_4432520), `SciPy` (cite: 2020SciPy-NMeth)

natexlab

(ref: 2024MNRAS.532.1361A) Aizawa, M., Muto, T., & Momose, M. 2024, MNRAS, 532, 1361, doi: [`10.1093/mnras/stae1549`](http://doi.org/10.1093/mnras/stae1549)

(ref: 2017AA...603L...3A) Alves, F. O., Girart, J. M., Caselli, P., et al. 2017, A&A, 603, L3, doi: [`10.1051/0004-6361/201731077`](http://doi.org/10.1051/0004-6361/201731077)

(ref: 2015ITPAM..38..252A) Ambikasaran, S., Foreman-Mackey, D., Greengard, L., Hogg, D. W., & O’Neil, M. 2015, IEEE Transactions on Pattern Analysis and Machine Intelligence, 38, 252, doi: [`10.1109/TPAMI.2015.2448083`](http://doi.org/10.1109/TPAMI.2015.2448083)

(ref: 2018ApJ...869L..41A) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: 2021ApJ...916...51A) Andrews, S. M., Elder, W., Zhang, S., et al. 2021, ApJ, 916, 51, doi: [`10.3847/1538-4357/ac00b9`](http://doi.org/10.3847/1538-4357/ac00b9)

(ref: 1994ApJ...421..651A) Artymowicz, P., & Lubow, S. H. 1994, ApJ, 421, 651, doi: [`10.1086/173679`](http://doi.org/10.1086/173679)

(ref: 2013AA...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2022ApJ...935..167A) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: 2015ApJ...805...15B) Bae, J., Hartmann, L., & Zhu, Z. 2015, ApJ, 805, 15, doi: [`10.1088/0004-637X/805/1/15`](http://doi.org/10.1088/0004-637X/805/1/15)

(ref: 2014ApJ...795...61B) Bae, J., Hartmann, L., Zhu, Z., & Nelson, R. P. 2014, ApJ, 795, 61, doi: [`10.1088/0004-637X/795/1/61`](http://doi.org/10.1088/0004-637X/795/1/61)

(ref: 2023ASPC..534..423B) Bae, J., Isella, A., Zhu, Z., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 423

(ref: 2018ApJ...859..119B) Bae, J., & Zhu, Z. 2018a, ApJ, 859, 119, doi: [`10.3847/1538-4357/aabf93`](http://doi.org/10.3847/1538-4357/aabf93)

(ref: 2018ApJ...859..118B) —. 2018b, ApJ, 859, 118, doi: [`10.3847/1538-4357/aabf8c`](http://doi.org/10.3847/1538-4357/aabf8c)

(ref: 2021AJ....161..147B) Bailer-Jones, C. A. L., Rybizki, J., Fouesneau, M., Demleitner, M., & Andrae, R. 2021, AJ, 161, 147, doi: [`10.3847/1538-3881/abd806`](http://doi.org/10.3847/1538-3881/abd806)

(ref: 2023ASPC..534..605B) Benisty, M., Dominik, C., Follette, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 605, doi: [`10.48550/arXiv.2203.09991`](http://doi.org/10.48550/arXiv.2203.09991)

(ref: 2018zndo...1495277B) Birnstiel, T. 2018, birnstiel/dsharp_opac: revised release of package, v1.1.0, Zenodo, doi: [`10.5281/zenodo.1495277`](http://doi.org/10.5281/zenodo.1495277)

(ref: 2018ApJ...869L..45B) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45, doi: [`10.3847/2041-8213/aaf743`](http://doi.org/10.3847/2041-8213/aaf743)

(ref: 1998ApJ...503..923B) Boss, A. P. 1998, ApJ, 503, 923, doi: [`10.1086/306036`](http://doi.org/10.1086/306036)

(ref: 1999ApJ...514..344B) Bryden, G., Chen, X., Lin, D. N. C., Nelson, R. P., & Papaloizou, J. C. B. 1999, ApJ, 514, 344, doi: [`10.1086/306917`](http://doi.org/10.1086/306917)

(ref: 2006AA...452..897C) Cabrit, S., Pety, J., Pesenti, N., & Dougados, C. 2006, A&A, 452, 897, doi: [`10.1051/0004-6361:20054047`](http://doi.org/10.1051/0004-6361:20054047)

(ref: 2025MNRAS.537.2695C) Calcino, J., Price, D. J., Hilder, T., et al. 2025, MNRAS, 537, 2695, doi: [`10.1093/mnras/staf135`](http://doi.org/10.1093/mnras/staf135)

(ref: 2019ApJ...883...71C) Carrasco-González, C., Sierra, A., Flock, M., et al. 2019, ApJ, 883, 71, doi: [`10.3847/1538-4357/ab3d33`](http://doi.org/10.3847/1538-4357/ab3d33)

(ref: 2022PASP..134k4501C) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: 2021ApJ...906...19C) Chen, E., Yu, S.-Y., & Ho, L. C. 2021, ApJ, 906, 19, doi: [`10.3847/1538-4357/abc7c5`](http://doi.org/10.3847/1538-4357/abc7c5)

(ref: 2014ApJ...785L..12C) Christiaens, V., Casassus, S., Perez, S., van der Plas, G., & Ménard, F. 2014, ApJL, 785, L12, doi: [`10.1088/2041-8205/785/1/L12`](http://doi.org/10.1088/2041-8205/785/1/L12)

(ref: 2021MNRAS.501.2934C) Cieza, L. A., González-Ruilova, C., Hales, A. S., et al. 2021, MNRAS, 501, 2934, doi: [`10.1093/mnras/staa3787`](http://doi.org/10.1093/mnras/staa3787)

(ref: 1993MNRAS.261..190C) Clarke, C. J., & Pringle, J. E. 1993, MNRAS, 261, 190, doi: [`10.1093/mnras/261.1.190`](http://doi.org/10.1093/mnras/261.1.190)

(ref: 2016ApJ...832..110C) Cleeves, L. I., Öberg, K. I., Wilner, D. J., et al. 2016, ApJ, 832, 110, doi: [`10.3847/0004-637X/832/2/110`](http://doi.org/10.3847/0004-637X/832/2/110)

(ref: 2008AJ....135.2496C) Connelley, M. S., Reipurth, B., & Tokunaga, A. T. 2008, AJ, 135, 2496, doi: [`10.1088/0004-6256/135/6/2496`](http://doi.org/10.1088/0004-6256/135/6/2496)

(ref: 2008ISTSP...2..793C) Cornwell, T. J. 2008, IEEE Journal of Selected Topics in Signal Processing, 2, 793, doi: [`10.1109/JSTSP.2008.2006388`](http://doi.org/10.1109/JSTSP.2008.2006388)

(ref: 2009MNRAS.393.1157C) Cossins, P., Lodato, G., & Clarke, C. J. 2009, MNRAS, 393, 1157, doi: [`10.1111/j.1365-2966.2008.14275.x`](http://doi.org/10.1111/j.1365-2966.2008.14275.x)

(ref: 2019MNRAS.483.4114C) Cuello, N., Dipierro, G., Mentiplay, D., et al. 2019, MNRAS, 483, 4114, doi: [`10.1093/mnras/sty3325`](http://doi.org/10.1093/mnras/sty3325)

(ref: 2022NatAs...6..751C) Currie, T., Lawson, K., Schneider, G., et al. 2022, Nature Astronomy, 6, 751, doi: [`10.1038/s41550-022-01634-x`](http://doi.org/10.1038/s41550-022-01634-x)

(ref: ian_czekala_2021_4432520) Czekala, I., Loomis, R., Andrews, S., Huang, J., & Rosenfeld, K. 2021, MPoL-dev/visread, v0.0.1, Zenodo, doi: [`10.5281/zenodo.4432501`](http://doi.org/10.5281/zenodo.4432501)

(ref: 2022ApJ...930...91D) Diaz-Rodriguez, A. K., Anglada, G., Blázquez-Calero, G., et al. 2022, ApJ, 930, 91, doi: [`10.3847/1538-4357/ac3b50`](http://doi.org/10.3847/1538-4357/ac3b50)

(ref: 2016ApJ...816L..12D) Dong, R., Zhu, Z., Fung, J., et al. 2016, ApJ, 816, L12, doi: [`10.3847/2041-8205/816/1/L12`](http://doi.org/10.3847/2041-8205/816/1/L12)

(ref: 2018ApJ...860..124D) Dong, R., Liu, S.-y., Eisner, J., et al. 2018, ApJ, 860, 124, doi: [`10.3847/1538-4357/aac6cb`](http://doi.org/10.3847/1538-4357/aac6cb)

(ref: 2022NatAs...6..331D) Dong, R., Liu, H. B., Cuello, N., et al. 2022, Nature Astronomy, 6, 331, doi: [`10.48550/arXiv.2201.0561710.1038/s41550-021-01558-y`](http://doi.org/10.48550/arXiv.2201.0561710.1038/s41550-021-01558-y)

(ref: 2019AA...628A..20D) Dullemond, C. P., Küffmeier, M., Goicovic, F., et al. 2019, A&A, 628, A20, doi: [`10.1051/0004-6361/201832632`](http://doi.org/10.1051/0004-6361/201832632)

(ref: 2018ApJ...869L..46D) Dullemond, C. P., Birnstiel, T., Huang, J., et al. 2018, ApJL, 869, L46, doi: [`10.3847/2041-8213/aaf742`](http://doi.org/10.3847/2041-8213/aaf742)

(ref: 2019AA...626L...2F) Facchini, S., van Dishoeck, E. F., Manara, C. F., et al. 2019, A&A, 626, L2, doi: [`10.1051/0004-6361/201935496`](http://doi.org/10.1051/0004-6361/201935496)

(ref: 2022RNAAS...6...18F) Fitton, S., Tofflemire, B. M., & Kraus, A. L. 2022, Research Notes of the American Astronomical Society, 6, 18, doi: [`10.3847/2515-5172/ac4bb7`](http://doi.org/10.3847/2515-5172/ac4bb7)

(ref: 2013PASP..125..306F) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, Publications of the Astronomical Society of the Pacific, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: 2018ApJ...860L...5F) Forgan, D. H., Ilee, J. D., & Meru, F. 2018, ApJ, 860, L5, doi: [`10.3847/2041-8213/aac7c9`](http://doi.org/10.3847/2041-8213/aac7c9)

(ref: 2004ApJ...605L..53F) Fukagawa, M., Hayashi, M., Tamura, M., et al. 2004, ApJL, 605, L53, doi: [`10.1086/420699`](http://doi.org/10.1086/420699)

(ref: 2021AA...649A...1G) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2021, A&A, 649, A1, doi: [`10.1051/0004-6361/202039657`](http://doi.org/10.1051/0004-6361/202039657)

(ref: 2023AA...674A...1G) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1, doi: [`10.1051/0004-6361/202243940`](http://doi.org/10.1051/0004-6361/202243940)

(ref: 2018AA...620A..94G) Garufi, A., Benisty, M., Pinilla, P., et al. 2018, A&A, 620, A94, doi: [`10.1051/0004-6361/201833872`](http://doi.org/10.1051/0004-6361/201833872)

(ref: 2021AA...645A.145G) Garufi, A., Podio, L., Codella, C., et al. 2021, A&A, 645, A145, doi: [`10.1051/0004-6361/202039483`](http://doi.org/10.1051/0004-6361/202039483)

(ref: 2022AA...658A.104G) —. 2022, A&A, 658, A104, doi: [`10.1051/0004-6361/202141264`](http://doi.org/10.1051/0004-6361/202141264)

(ref: 2021ApJ...908L..25G) Ginski, C., Facchini, S., Huang, J., et al. 2021, ApJL, 908, L25, doi: [`10.3847/2041-8213/abdf57`](http://doi.org/10.3847/2041-8213/abdf57)

(ref: 2025AA...696A.232G) Guerra-Alvarado, O. M., van der Marel, N., Williams, J. P., et al. 2025, A&A, 696, A232, doi: [`10.1051/0004-6361/202453338`](http://doi.org/10.1051/0004-6361/202453338)

(ref: 2004AJ....127.1747H) Haisch, Karl E., J., Greene, T. P., Barsony, M., & Stahler, S. W. 2004, AJ, 127, 1747, doi: [`10.1086/381952`](http://doi.org/10.1086/381952)

(ref: 2023MNRAS.522L..51H) Hammond, I., Christiaens, V., Price, D. J., et al. 2023, MNRAS, 522, L51, doi: [`10.1093/mnrasl/slad027`](http://doi.org/10.1093/mnrasl/slad027)

(ref: 2019ApJ...877L...2H) Harrison, R. E., Looney, L. W., Stephens, I. W., et al. 2019, ApJL, 877, L2, doi: [`10.3847/2041-8213/ab1e46`](http://doi.org/10.3847/2041-8213/ab1e46)

(ref: 2011MNRAS.413..423H) Harsono, D., Alexander, R. D., & Levin, Y. 2011, MNRAS, 413, 423, doi: [`10.1111/j.1365-2966.2010.18146.x`](http://doi.org/10.1111/j.1365-2966.2010.18146.x)

(ref: 2020ApJ...895..126H) Hendler, N., Pascucci, I., Pinilla, P., et al. 2020, ApJ, 895, 126, doi: [`10.3847/1538-4357/ab70ba`](http://doi.org/10.3847/1538-4357/ab70ba)

(ref: 2017AA...599A..86H) Hennebelle, P., Lesur, G., & Fromang, S. 2017, A&A, 599, A86, doi: [`10.1051/0004-6361/201629779`](http://doi.org/10.1051/0004-6361/201629779)

(ref: 2014ApJ...786...97H) Herczeg, G. J., & Hillenbrand, L. A. 2014, ApJ, 786, 97, doi: [`10.1088/0004-637X/786/2/97`](http://doi.org/10.1088/0004-637X/786/2/97)

(ref: 2024ApJ...976..132H) Huang, J., Ansdell, M., Birnstiel, T., et al. 2024, ApJ, 976, 132, doi: [`10.3847/1538-4357/ad84df`](http://doi.org/10.3847/1538-4357/ad84df)

(ref: 2018ApJ...869L..42H) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018a, ApJL, 869, L42, doi: [`10.3847/2041-8213/aaf740`](http://doi.org/10.3847/2041-8213/aaf740)

(ref: 2018ApJ...869L..43H) Huang, J., Andrews, S. M., Pérez, L. M., et al. 2018b, ApJL, 869, L43, doi: [`10.3847/2041-8213/aaf7a0`](http://doi.org/10.3847/2041-8213/aaf7a0)

(ref: 2021ApJS..257...19H) Huang, J., Bergin, E. A., Öberg, K. I., et al. 2021, ApJS, 257, 19, doi: [`10.3847/1538-4365/ac143e`](http://doi.org/10.3847/1538-4365/ac143e)

(ref: Hunter:2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: 2023zndo...7502160H) Hunter, T. R., Petry, D., Barkats, D., Corder, S., & Indebetouw, R. 2023, analysisUtils, 2.6, Zenodo, Zenodo, doi: [`10.5281/zenodo.7502160`](http://doi.org/10.5281/zenodo.7502160)

(ref: 2022ApJ...928....2I) Izquierdo, A. F., Facchini, S., Rosotti, G. P., van Dishoeck, E. F., & Testi, L. 2022, ApJ, 928, 2, doi: [`10.3847/1538-4357/ac474d`](http://doi.org/10.3847/1538-4357/ac474d)

(ref: 2022MNRAS.509.2780J) Jennings, J., Booth, R. A., Tazzari, M., Clarke, C. J., & Rosotti, G. P. 2022, MNRAS, 509, 2780, doi: [`10.1093/mnras/stab3185`](http://doi.org/10.1093/mnras/stab3185)

(ref: 2020MNRAS.495.3209J) Jennings, J., Booth, R. A., Tazzari, M., Rosotti, G. P., & Clarke, C. J. 2020, MNRAS, 495, 3209, doi: [`10.1093/mnras/staa1365`](http://doi.org/10.1093/mnras/staa1365)

(ref: 2009ApJ...697.1269J) Johansen, A., Youdin, A., & Klahr, H. 2009, ApJ, 697, 1269, doi: [`10.1088/0004-637X/697/2/1269`](http://doi.org/10.1088/0004-637X/697/2/1269)

(ref: 1995ApJS..101..117K) Kenyon, S. J., & Hartmann, L. 1995, ApJS, 101, 117, doi: [`10.1086/192235`](http://doi.org/10.1086/192235)

(ref: 2020PASP..132b4505K) Kepley, A. A., Tsutsumi, T., Brogan, C. L., et al. 2020, PASP, 132, 024505, doi: [`10.1088/1538-3873/ab5e14`](http://doi.org/10.1088/1538-3873/ab5e14)

(ref: 2015MNRAS.452.3435K) Koch, E. W., & Rosolowsky, E. W. 2015, MNRAS, 452, 3435, doi: [`10.1093/mnras/stv1521`](http://doi.org/10.1093/mnras/stv1521)

(ref: 2016ascl.soft08009K) —. 2016, FilFinder: Filamentary structure in molecular clouds, Astrophysics Source Code Library, record ascl:1608.009

(ref: 2016ARAA..54..271K) Kratter, K., & Lodato, G. 2016, Annual Review of Astronomy and Astrophysics, 54, 271, doi: [`10.1146/annurev-astro-081915-023307`](http://doi.org/10.1146/annurev-astro-081915-023307)

(ref: 2007ApJ...662..413K) Kraus, A. L., & Hillenbrand, L. A. 2007, ApJ, 662, 413, doi: [`10.1086/516835`](http://doi.org/10.1086/516835)

(ref: 2018MNRAS.475.2642K) Kuffmeier, M., Frimann, S., Jensen, S. S., & Haugbølle, T. 2018, MNRAS, 475, 2642, doi: [`10.1093/mnras/sty024`](http://doi.org/10.1093/mnras/sty024)

(ref: 2023EPJP..138..272K) Kuffmeier, M., Jensen, S. S., & Haugbølle, T. 2023, European Physical Journal Plus, 138, 272, doi: [`10.1140/epjp/s13360-023-03880-y`](http://doi.org/10.1140/epjp/s13360-023-03880-y)

(ref: 2018ApJ...869L..44K) Kurtovic, N. T., Pérez, L. M., Benisty, M., et al. 2018, ApJL, 869, L44, doi: [`10.3847/2041-8213/aaf746`](http://doi.org/10.3847/2041-8213/aaf746)

(ref: 2022ApJ...928...92K) Kuznetsova, A., Bae, J., Hartmann, L., & Low, M.-M. M. 2022, ApJ, 928, 92, doi: [`10.3847/1538-4357/ac54a8`](http://doi.org/10.3847/1538-4357/ac54a8)

(ref: 2015ApJ...808..102K) Kwon, W., Looney, L. W., Mundy, L. G., & Welch, W. J. 2015, ApJ, 808, 102, doi: [`10.1088/0004-637X/808/1/102`](http://doi.org/10.1088/0004-637X/808/1/102)

(ref: 2020NatAs...4..142L) Lee, C.-F., Li, Z.-Y., & Turner, N. J. 2020, Nature Astronomy, 4, 142, doi: [`10.1038/s41550-019-0905-x`](http://doi.org/10.1038/s41550-019-0905-x)

(ref: 2015AA...582L...9L) Lesur, G., Hennebelle, P., & Fromang, S. 2015, A&A, 582, L9, doi: [`10.1051/0004-6361/201526734`](http://doi.org/10.1051/0004-6361/201526734)

(ref: 1986ApJ...307..395L) Lin, D. N. C., & Papaloizou, J. 1986, ApJ, 307, 395, doi: [`10.1086/164426`](http://doi.org/10.1086/164426)

(ref: 2019ApJ...877L..22L) Liu, H. B. 2019, ApJ, 877, L22, doi: [`10.3847/2041-8213/ab1f8e`](http://doi.org/10.3847/2041-8213/ab1f8e)

(ref: 2016SciA....2E0875L) Liu, H. B., Takami, M., Kudo, T., et al. 2016, Science Advances, 2, e1500875, doi: [`10.1126/sciadv.1500875`](http://doi.org/10.1126/sciadv.1500875)

(ref: 2004MNRAS.351..630L) Lodato, G., & Rice, W. K. M. 2004, MNRAS, 351, 630, doi: [`10.1111/j.1365-2966.2004.07811.x`](http://doi.org/10.1111/j.1365-2966.2004.07811.x)

(ref: 2023MNRAS.518.4481L) Lodato, G., Rampinelli, L., Viscardi, E., et al. 2023, MNRAS, 518, 4481, doi: [`10.1093/mnras/stac3223`](http://doi.org/10.1093/mnras/stac3223)

(ref: 2018ApJ...869...17L) Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17, doi: [`10.3847/1538-4357/aae8e1`](http://doi.org/10.3847/1538-4357/aae8e1)

(ref: 2019ApJ...882...49L) Long, F., Herczeg, G. J., Harsono, D., et al. 2019, ApJ, 882, 49, doi: [`10.3847/1538-4357/ab2d2d`](http://doi.org/10.3847/1538-4357/ab2d2d)

(ref: 2023MNRAS.519.2017L) Longarini, C., Lodato, G., Bertin, G., & Armitage, P. J. 2023, MNRAS, 519, 2017, doi: [`10.1093/mnras/stac3653`](http://doi.org/10.1093/mnras/stac3653)

(ref: 2010ApJS..186..111L) Luhman, K. L., Allen, P. R., Espaillat, C., Hartmann, L., & Calvet, N. 2010, ApJS, 186, 111, doi: [`10.1088/0067-0049/186/1/111`](http://doi.org/10.1088/0067-0049/186/1/111)

(ref: 2021AA...648A..33M) Macı́as, E., Guerra-Alvarado, O., Carrasco-González, C., et al. 2021, A&A, 648, A33, doi: [`10.1051/0004-6361/202039812`](http://doi.org/10.1051/0004-6361/202039812)

(ref: 2018AA...618L...3M) Manara, C. F., Morbidelli, A., & Guillot, T. 2018, A&A, 618, L3, doi: [`10.1051/0004-6361/201834076`](http://doi.org/10.1051/0004-6361/201834076)

(ref: 2004ApJ...609.1045M) Mayer, L., Quinn, T., Wadsley, J., & Stadel, J. 2004, ApJ, 609, 1045, doi: [`10.1086/421288`](http://doi.org/10.1086/421288)

(ref: 2017ApJ...839L..24M) Meru, F., Juhász, A., Ilee, J. D., et al. 2017, ApJ, 839, L24, doi: [`10.3847/2041-8213/aa6837`](http://doi.org/10.3847/2041-8213/aa6837)

(ref: 2022AA...658A..63M) Mesa, D., Ginski, C., Gratton, R., et al. 2022, A&A, 658, A63, doi: [`10.1051/0004-6361/202142219`](http://doi.org/10.1051/0004-6361/202142219)

(ref: 2024AA...682A..55M) Miley, J. M., Carpenter, J., Booth, R., et al. 2024, A&A, 682, A55, doi: [`10.1051/0004-6361/202347135`](http://doi.org/10.1051/0004-6361/202347135)

(ref: 2021AA...651A..48M) Miotello, A., Rosotti, G., Ansdell, M., et al. 2021, A&A, 651, A48, doi: [`10.1051/0004-6361/202140550`](http://doi.org/10.1051/0004-6361/202140550)

(ref: 2012ApJ...748L..22M) Muto, T., Grady, C. A., Hashimoto, J., et al. 2012, ApJL, 748, L22, doi: [`10.1088/2041-8205/748/2/L22`](http://doi.org/10.1088/2041-8205/748/2/L22)

(ref: 2014MNRAS.445.3315N) Najita, J. R., & Kenyon, S. J. 2014, MNRAS, 445, 3315, doi: [`10.1093/mnras/stu1994`](http://doi.org/10.1093/mnras/stu1994)

(ref: 2023ApJ...951....8O) Ohashi, N., Tobin, J. J., Jørgensen, J. K., et al. 2023, ApJ, 951, 8, doi: [`10.3847/1538-4357/acd384`](http://doi.org/10.3847/1538-4357/acd384)

(ref: 2021ApJ...914...88P) Paneque-Carreño, T., Pérez, L. M., Benisty, M., et al. 2021, ApJ, 914, 88, doi: [`10.3847/1538-4357/abf243`](http://doi.org/10.3847/1538-4357/abf243)

(ref: 2016Sci...353.1519P) Pérez, L. M., Carpenter, J. M., Andrews, S. M., et al. 2016, Science, 353, 1519, doi: [`10.1126/science.aaf8296`](http://doi.org/10.1126/science.aaf8296)

(ref: 2023MNRAS.524.3184P) Pizzati, E., Rosotti, G. P., & Tabone, B. 2023, MNRAS, 524, 3184, doi: [`10.1093/mnras/stad2057`](http://doi.org/10.1093/mnras/stad2057)

(ref: 2013ApJ...766L...1Q) Quanz, S. P., Amara, A., Meyer, M. R., et al. 2013, ApJL, 766, L1, doi: [`10.1088/2041-8205/766/1/L1`](http://doi.org/10.1088/2041-8205/766/1/L1)

(ref: 2010ApJS..186..259R) Rebull, L. M., Padgett, D. L., McCabe, C. E., et al. 2010, ApJS, 186, 259, doi: [`10.1088/0067-0049/186/2/259`](http://doi.org/10.1088/0067-0049/186/2/259)

(ref: 2023AA...673A..77R) Ribas, Á., Macı́as, E., Weber, P., et al. 2023, A&A, 673, A77, doi: [`10.1051/0004-6361/202245637`](http://doi.org/10.1051/0004-6361/202245637)

(ref: 2012AA...540A...6R) Ricci, L., Trotta, F., Testi, L., et al. 2012, A&A, 540, A6, doi: [`10.1051/0004-6361/201118296`](http://doi.org/10.1051/0004-6361/201118296)

(ref: 2020MNRAS.491.1335R) Rosotti, G. P., Benisty, M., Juhász, A., et al. 2020, MNRAS, 491, 1335, doi: [`10.1093/mnras/stz3090`](http://doi.org/10.1093/mnras/stz3090)

(ref: 2024MNRAS.528.2490R) Rowther, S., Nealon, R., Meru, F., et al. 2024, MNRAS, 528, 2490, doi: [`10.1093/mnras/stae167`](http://doi.org/10.1093/mnras/stae167)

(ref: 2024ApJ...966...59S) Shi, Y., Long, F., Herczeg, G. J., et al. 2024, ApJ, 966, 59, doi: [`10.3847/1538-4357/ad2e94`](http://doi.org/10.3847/1538-4357/ad2e94)

(ref: 1990AJ.....99.1187S) Skrutskie, M. F., Dutkevitch, D., Strom, S. E., et al. 1990, AJ, 99, 1187, doi: [`10.1086/115407`](http://doi.org/10.1086/115407)

(ref: 2024Natur.633...58S) Speedie, J., Dong, R., Hall, C., et al. 2024, Nature, 633, 58, doi: [`10.1038/s41586-024-07877-0`](http://doi.org/10.1038/s41586-024-07877-0)

(ref: 2014ApJ...796....1T) Takakuwa, S., Saito, M., Saigo, K., et al. 2014, ApJ, 796, 1, doi: [`10.1088/0004-637X/796/1/1`](http://doi.org/10.1088/0004-637X/796/1/1)

(ref: 2020ApJ...898...10T) Takakuwa, S., Saigo, K., Matsumoto, T., et al. 2020, ApJ, 898, 10, doi: [`10.3847/1538-4357/ab9b7c`](http://doi.org/10.3847/1538-4357/ab9b7c)

(ref: 2002ApJ...565.1257T) Tanaka, H., Takeuchi, T., & Ward, W. R. 2002, ApJ, 565, 1257, doi: [`10.1086/324713`](http://doi.org/10.1086/324713)

(ref: 2017ApJ...840...32T) Tang, Y.-W., Guilloteau, S., Dutrey, A., et al. 2017, ApJ, 840, 32, doi: [`10.3847/1538-4357/aa6af7`](http://doi.org/10.3847/1538-4357/aa6af7)

(ref: 2016Natur.538..483T) Tobin, J. J., Kratter, K. M., Persson, M. V., et al. 2016, Nature, 538, 483, doi: [`10.1038/nature20094`](http://doi.org/10.1038/nature20094)

(ref: 1964ApJ...139.1217T) Toomre, A. 1964, ApJ, 139, 1217, doi: [`10.1086/147861`](http://doi.org/10.1086/147861)

(ref: 2024NatAs...8.1148U) Ueda, T., Tazaki, R., Okuzumi, S., Flock, M., & Sudarshan, P. 2024, Nature Astronomy, 8, 1148, doi: [`10.1038/s41550-024-02308-6`](http://doi.org/10.1038/s41550-024-02308-6)

(ref: cmasher) van der Velden, E. 2020, Journal of Open Source Software, 5, 2004, doi: [`10.21105/joss.02004`](http://doi.org/10.21105/joss.02004)

(ref: scikit-image) van der Walt, S., Schönberger, J. L., Nunez-Iglesias, J., et al. 2014, PeerJ, 2, e453, doi: [`10.7717/peerj.453`](http://doi.org/10.7717/peerj.453)

(ref: 2021AA...653A.159V) van Gelder, M. L., Tabone, B., van Dishoeck, E. F., & Godard, B. 2021, A&A, 653, A159, doi: [`10.1051/0004-6361/202141591`](http://doi.org/10.1051/0004-6361/202141591)

(ref: 2022ApJ...934L..11V) Verrios, H. J., Price, D. J., Pinte, C., Hilder, T., & Calcino, J. 2022, ApJL, 934, L11, doi: [`10.3847/2041-8213/ac7f44`](http://doi.org/10.3847/2041-8213/ac7f44)

(ref: 2022ApJ...930...11V) Villenave, M., Stapelfeldt, K. R., Duchêne, G., et al. 2022, ApJ, 930, 11, doi: [`10.3847/1538-4357/ac5fae`](http://doi.org/10.3847/1538-4357/ac5fae)

(ref: 2023ApJ...946...70V) Villenave, M., Podio, L., Duchêne, G., et al. 2023, ApJ, 946, 70, doi: [`10.3847/1538-4357/acb92e`](http://doi.org/10.3847/1538-4357/acb92e)

(ref: 2020SciPy-NMeth) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: 2023NatAs...7.1208W) Wagner, K., Stone, J., Skemer, A., et al. 2023, Nature Astronomy, 7, 1208, doi: [`10.1038/s41550-023-02028-3`](http://doi.org/10.1038/s41550-023-02028-3)

(ref: 2020MNRAS.498.1382W) Wallace, A. L., Kammerer, J., Ireland, M. J., et al. 2020, MNRAS, 498, 1382, doi: [`10.1093/mnras/staa2434`](http://doi.org/10.1093/mnras/staa2434)

(ref: 2024ApJ...972L...9W) Winter, A. J., Benisty, M., & Andrews, S. M. 2024, ApJL, 972, L9, doi: [`10.3847/2041-8213/ad6d5d`](http://doi.org/10.3847/2041-8213/ad6d5d)

(ref: 2023ApJ...954..190X) Xu, W., Ohashi, S., Aso, Y., & Liu, H. B. 2023, ApJ, 954, 190, doi: [`10.3847/1538-4357/aced4c`](http://doi.org/10.3847/1538-4357/aced4c)

(ref: 2024PASJ...76..437Y) Yamaguchi, M., Muto, T., Tsukagoshi, T., et al. 2024, PASJ, 76, 437, doi: [`10.1093/pasj/psae022`](http://doi.org/10.1093/pasj/psae022)

(ref: 2020ApJ...896..132Z) Zapata, L. A., Rodrı́guez, L. F., Fernández-López, M., et al. 2020, ApJ, 896, 132, doi: [`10.3847/1538-4357/ab8fac`](http://doi.org/10.3847/1538-4357/ab8fac)

(ref: 2023PASP..135f4503Z) Zawadzki, B., Czekala, I., Loomis, R. A., et al. 2023, PASP, 135, 064503, doi: [`10.1088/1538-3873/acdf84`](http://doi.org/10.1088/1538-3873/acdf84)

(ref: 2016ApJ...818L..16Z) Zhang, K., Bergin, E. A., Blake, G. A., et al. 2016, ApJL, 818, L16, doi: [`10.3847/2041-8205/818/1/L16`](http://doi.org/10.3847/2041-8205/818/1/L16)

(ref: 2023ApJ...952..108Z) Zhang, S., Kalscheur, M., Long, F., et al. 2023, ApJ, 952, 108, doi: [`10.3847/1538-4357/acd334`](http://doi.org/10.3847/1538-4357/acd334)

(ref: 2010ApJ...713.1143Z) Zhu, Z., Hartmann, L., & Gammie, C. 2010, ApJ, 713, 1143, doi: [`10.1088/0004-637X/713/2/1143`](http://doi.org/10.1088/0004-637X/713/2/1143)

(ref: 2019ApJ...877L..18Z) Zhu, Z., Zhang, S., Jiang, Y.-F., et al. 2019, ApJL, 877, L18, doi: [`10.3847/2041-8213/ab1f8c`](http://doi.org/10.3847/2041-8213/ab1f8c)

(ref: 2018AJ....156..259Z) Ziegler, C., Law, N. M., Baranec, C., et al. 2018, AJ, 156, 259, doi: [`10.3847/1538-3881/aad80a`](http://doi.org/10.3847/1538-3881/aad80a)

[^1]: The visibilities and images can be downloaded from Zenodo: doi:[10.5281/zenodo.15002753](https://zenodo.org/records/15002753)

[^2]: <https://github.com/2ndmk2/protomidpy>

[^3]: <https://emcee.readthedocs.io/en/stable/tutorials/autocorr/>

</paper>

Write the methods card for this paper.