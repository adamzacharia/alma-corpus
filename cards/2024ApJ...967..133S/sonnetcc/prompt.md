# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...967..133S\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...967..133S",
 "title": "Hidden Gems on a Ring: Infant Massive Clusters and Their Formation Timeline Unveiled by ALMA, HST, and JWST in NGC 3351",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Sun, Jiayi",
 "n_authors": 41,
 "arxiv_id": "2401.14453",
 "doi": "10.3847/1538-4357/ad3de6",
 "alma_projects_linked_by_archive": [
  "2013.1.00634.S",
  "2021.1.00059.S",
  "2022.1.00159.S"
 ]
}
```

Paper text:
<paper>
# Hidden Gems on a Ring: Infant Massive Clusters and Their Formation Timeline\
Unveiled by ALMA, HST, and JWST in NGC 3351

## Abstract

We study young massive clusters (YMCs) in their embedded “infant” phase with $\sim0.1\ensuremath{''}$ ALMA, HST, and JWST observations targeting the central starburst ring in NGC 3351, a nearby Milky Way analog galaxy. Our new ALMA data reveal 18 bright and compact (sub-)millimeter continuum sources, of which 8 have counterparts in JWST images and only 6 have counterparts in HST images. Based on the ALMA continuum and molecular line data, as well as ancillary measurements for the HST and JWST counterparts, we identify 14 sources as infant star clusters with high stellar and/or gas masses (${\sim}10^5\;\mathrm{M_\odot}$), small radii (${\lesssim}\,5\;\mathrm{pc}$), large escape velocities ($6{-}10\;\mathrm{km/s}$), and short free-fall times ($0.5{-}1\;\mathrm{Myr}$). Their multiwavelength properties motivate us to divide them into four categories, likely corresponding to four evolutionary stages from starless clumps to exposed H II region–cluster complexes. Leveraging age estimates for HST-identified clusters in the same region, we infer an evolutionary timeline going from $\sim$1–2 Myr before cluster formation as starless clumps, to $\sim$4–6 Myr after as exposed H II region–cluster complexes. Finally, we show that the YMCs make up a substantial fraction of recent star formation across the ring, exhibit an non-uniform azimuthal distribution without a very coherent evolutionary trend along the ring, and are capable of driving large-scale gas outflows.

# Introduction

Massive star clusters ($M_\star\gtrsim10^4\,\mbox{$\rm M_\odot$}$) form in dense, turbulent, high-pressure environments (cite: PortegiesZwart_etal_2010; Longmore_etal_2014; Krumholz_etal_2019). This process appears distinct from star formation under lower gas density conditions, with the massive clusters quickly and efficiently convert their gas content into stars before the newly formed stellar population exerts strong feedback (cite: Krumholz_etal_2014). Understanding the formation of massive clusters can thus provide unique constraints on theoretical models of star formation and stellar feedback. It can also shed light on how the majority of stellar populations were built up earlier in the cosmic history, when high gas density and turbulence conditions were prevalent (cite: Madau_Dickinson_2014).

To achieve a more complete, observation-grounded understanding of massive cluster formation, it is critical to probe the earliest (“infant”) phase, during which star formation and feedback processes are still ongoing. This has been challenging for several reasons. The relevant physical processes happen on a short timescale (cite: Krumholz_etal_2014), making it hard to catch forming YMCs in the infant phase. Those YMCs that *are* in this phase are still deeply embedded in their natal gas and dust “cradles” and thus remain basically invisible at short wavelengths (cite: Kornei_McCrady_2009; Leroy_etal_2018). Last but not least, the physical conditions required for creating YMCs (high gas density, turbulence, and pressure) are rare in the Milky Way and the nearest extragalactic systems (cite: PortegiesZwart_etal_2010). Building a sizable sample of infant YMCs thus necessitates obtaining sensitive and resolved observations for these compact objects in more distant galaxies, which can be a tall order even with the latest facilities.

Recent studies based on deep, long-baseline, targeted observations with the Atacama Large Millimeter Array (ALMA) have identified a promising avenue for addressing these challenges. With its exquisite sensitivity and resolving power in (sub-)millimeter bands, ALMA can detect extinction-free tracers of star formation (via free-free continuum and radio recombination lines) *as well as* the associated gas reservoir (via molecular lines and dust continuum) for YMCs even at extragalactic distances. Thanks to these unique capabilities, we have already identified and characterized individual forming YMCs or entire YMC populations in our Galaxy (cite: Schmiedeke_etal_2016; Ginsburg_etal_2018) and a handful of nearby galaxies (e.g., the Large Magellanic Cloud: (cite: Nayak_etal_2019); NGC 5253: (cite: Turner_etal_2017); NGC 253: (cite: Leroy_etal_2018; Levy_etal_2021; Mills_etal_2021); NGC 4945: (cite: Emig_etal_2020); Henize 2-10: (cite: Costa_etal_2021); and the Antennae: (cite: Finn_etal_2019; He_etal_2022)).

Building on these pioneering studies, the logical next steps are to connect the infant YMCs identified in the (sub-)millimeter bands with more evolved clusters visible at shorter wavelengths, and to put them into the larger-scale context of the host galaxy. Doing so requires multiwavelength observations of a sizable YMC population at matched spatial resolution, supported by rich ancillary data for the host galaxy. It is also important that the host galaxy is at a favorable viewing angle for source localization and cross-wavelength source matching, which have proven difficult in edge-on systems including our Galaxy, NGC 253, and NGC 4945 (cite: Stolte_etal_2014; Emig_etal_2020; Levy_etal_2022).

In this paper, we use nearly matched-resolution ALMA, HST, and JWST observations to examine a population of forming YMCs in a nearby Milky Way analog galaxy, NGC 3351 (a.k.a. M95, see Table [1](#tab:M95) for its basic properties). This galaxy features a prominent, dusty, inner ring structure, which is likely fed by large-scale gas inflows induced by a strong stellar bar (cite: Regan_etal_2006). This “starburst ring” hosts a large number of optically-visible massive clusters, and previous IR observations show signs of embedded YMC formation as well (cite: Ma_etal_2018; Calzetti_etal_2021; Turner_etal_2021). Its favorable viewing angle ($i\approx45^\circ$, Table [1](#tab:M95)) and clean orbital configurations (Figure [1](#fig:wide_field)) enable cross-wavelength source matching as well as examinations of systematic trends along the ring.

The structure of this paper is as follows. Section [2](#sec:data) describes the ALMA, HST, and JWST datasets used in this paper. Section [3](#sec:analyses) details our source identification, characterization, and cross-matching schemes. Section [4](#sec:results) presents a set of key physical properties measured for all ALMA-identified YMC candidates. Section [5](#sec:discuss) synthesizes the observational results from ALMA, JWST, and HST, constructs an evolutionary timeline for YMC formation, and puts the YMC population in the large-scale context of the starburst ring in NGC 3351. We summarize all our findings in Section [6](#sec:conclusion).

|  |  |
|---:|:---|
|  |  |
| Galaxy name | NGC 3351 (M95) |
| Galaxy type | SB(r)b |
| Center coordinates | ($\rm10^h43^m57.73^s$, $\rm+11^\circ42^\prime13.3^{\prime\prime}$) |
| Distance | $9.96\,(\pm0.01)$ Mpc \[1\] |
| Systemic velocity | $775\,(\pm5)\rm\;km/s$ \[2\] |
| Inclination angle | $45\,(\pm6)$ deg \[2\] |
| Position angle | $193\,(\pm2)$ deg \[2\] |
| Stellar mass | $2.3\,(\pm0.6){\times}10^{10}\;\mbox{$\rm M_\odot$}$ \[3\] |
| SFR | $1.3\,(\pm0.3)\;\mbox{$\rm M_\odot~yr^{-1}$}$ \[3\] |

: Basic Properties of the Target Galaxy

Table notes: \[1\] (cite: Anand_etal_2021); \[2\] (cite: Lang_etal_2020); \[3\] (cite: Leroy_etal_2021a).

# Data

We use a new set of very high resolution ALMA observations in this work. Here we lay out the observational design, reduction procedures, and data characteristics for this new ALMA dataset (Section [2.1](#sec:data:ALMA)). We then briefly describe ancillary HST and JWST images and data products used in this work (Section [2.2](#sec:data:HST)).

## ALMA Data

We acquired ALMA Band 3 and 7 observations in Cycle 8 (2021.1.00059.S; PI: J. Sun) to highly resolve the central starburst region of NGC 3351 (Figure [1](#fig:wide_field) and [2](#fig:alma-zoom)). These observations capture (sub-)millimeter continuum emission and molecular line emission at $0.1\ensuremath{''}$–$0.2\ensuremath{''}$ resolution (5–10 pc at 9.96 Mpc), which matches the typical size of YMCs (cite: Ryon_etal_2017).

Our Band 3 observations employ the most extended 12-m array configuration offered in Cycle 8 (C-8) to reach our desired resolution of $0.1\ensuremath{''}$–$0.2\ensuremath{''}$. These long-baseline data are supplemented by shorter-spacing data acquired in C-5 (same Cycle 8 project) and C-2 configurations (cite: Gallagher_etal_2018a) to extend the maximal recoverable scale (MRS) to the size of the entire central starburst region ($\sim20\ensuremath{''}$). The Cycle 8 observations cover a $\sim60\ensuremath{''}$ field-of-view (FoV) with a single 12-m pointing and reach on-source integration times of 1.2 h (C-8) and 0.3 h (C-5). The Band 3 spectral tuning covers the 85–101 GHz continuum and the $\mathrm{HCN}\,(1\text{--}0)$, $\mathrm{HCO^+}\,(1\text{--}0)$, and $\mathrm{CS}\,(2\text{--}1)$ lines at a native velocity resolution of $3.4\;\mbox{$\rm km~s^{-1}$}$.

Our Band 7 data combine C-6 and C-3 configurations of the 12-m array and supplementary 7-m array observations (all from the same Cycle 8 project) to achieve a similar resolution and MRS as our Band 3 observations. The 12-m observations cover a $\sim30\ensuremath{''}$ FoV using a 7-pointing mosaic and reach on-source integration times of 0.4 h (C-6) and 0.2 h (C-3); the 7-m observations use a 3-pointing mosaic to cover a similar FoV, with 0.5 h of on-source integration. The Band 7 spectral tuning covers the 342–357 GHz continuum and the $\mathrm{CO}\,(3\text{--}2)$, $\mathrm{HCO^+}\,(4\text{--}3)$, and $\mathrm{CS}\,(7\text{--}6)$ lines at a native velocity resolution of $0.95\;\mbox{$\rm km~s^{-1}$}$.

+:---------------------------------+:------:+:--------:+:------------------------------:+:--------------------:+:----------------------------------------:+
| Product                          | Band   | Arrays   | Beam FWHM                      | Channel Width        | 1$\sigma$ Noise Level (at mosaic center) |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
|                                  |        |          |                                |                      |                                          |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
|                                  |        |          |                                |                      |                                          |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
| Continuum Images                                                                                                                                        |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
| 93 GHz                           | 3      | C8+C5+C2 | $0.17\ensuremath{''}$ (8.2 pc) | –                    | 6.5$\mu$Jy/beam                          |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
| 350 GHz                          | 7      | C6+C3+7m | $0.17\ensuremath{''}$ (8.2 pc) | –                    | 83$\mu$Jy/beam                           |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
| Molecular Line Data Cubes                                                                                                                               |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
| $\mathrm{CO}\,(3\text{--}2)$     | 7      | C6+C3+7m | $0.10\ensuremath{''}$ (4.8 pc) | 0.85$\rm km~s^{-1}$  | 1.9K                                     |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
| $\mathrm{CO}\,(3\text{--}2)$     | 7      | C6+C3+7m | $0.10\ensuremath{''}$ (4.8 pc) | 5$\rm km~s^{-1}$     | 0.9K                                     |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
| $\mathrm{HCN}\,(1\text{--}0)$    | 3      | C8+C5+C2 | $0.19\ensuremath{''}$ (9.2 pc) | 10$\rm km~s^{-1}$    | 1.1K                                     |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
| $\mathrm{HCO^+}\,(1\text{--}0)$  | 3      | C8+C5+C2 | $0.19\ensuremath{''}$ (9.2 pc) | 10$\rm km~s^{-1}$    | 1.1K                                     |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
| $\mathrm{CS}\,(2\text{--}1)$     | 3      | C8+C5+C2 | $0.19\ensuremath{''}$ (9.2 pc) | 10$\rm km~s^{-1}$    | 1.0K                                     |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
| $\mathrm{HCO^+}\,(4\text{--}3)$  | 7      | C6+C3+7m | $0.12\ensuremath{''}$ (5.8 pc) | 10$\rm km~s^{-1}$    | 0.4K                                     |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+
| $\mathrm{CS}\,(7\text{--}6)$     | 7      | C6+C3+7m | $0.12\ensuremath{''}$ (5.8 pc) | 10$\rm km~s^{-1}$    | 0.3K                                     |
+----------------------------------+--------+----------+--------------------------------+----------------------+------------------------------------------+

: ALMA Data Products and Characteristics

Table notes: The Band 3 C-2 data come from an archival project (cite: Gallagher_etal_2018a). All other data are newly acquired in Cycle 8 (2021.1.00059.S; PI: J. Sun).

### Calibration and Imaging

We calibrate the raw visibility data with observatory-supplied scripts and the appropriate version of CASA pipeline (6.2.1 for Cycle 8). The calibrated data show no obvious pathologies upon visual inspection.

From the calibrated measurement sets, we extract and image a relevant subset of visibility data for each molecular line and continuum using a modified version of the PHANGS–ALMA imaging pipeline (cite: Leroy_etal_2021b). Here, we outline the workflow and highlight a few deviations from the original pipeline.

To prepare for continuum imaging, we extract all line-free channels from the calibrated measurement set and regrid them into a small number of channels per spectral window (SPW). Here, rather than collapsing each SPW into one channel (default behavior of the PHANGS pipeline), we manually choose a small enough output channel width to prevent bandwidth smearing. We then combine the continuum-only data from all array configurations (now on a common spectral grid) to make a joint dataset for the continuum in each band.

To prepare for line imaging, we model the continuum emission with a 1st-order polynomial based on all line-free channels across all SPWs of a particular band. We then subtract this model off from the calibrated measurement set, extract the subset of channels within the velocity range of interest ($\pm300\,\mbox{$\rm km~s^{-1}$}$ around the systemic velocity of $778\,\mbox{$\rm km~s^{-1}$}$) for each emission line, and regrid the line spectrum to a desired channel width. Here, we choose a $10\,\mbox{$\rm km~s^{-1}$}$ channel width for all high critical density molecular lines (HCN, HCO$^+$, CS) to ensure a reasonable signal-to-noise (S/N) ratio per channel; we keep the native $0.85\,\mbox{$\rm km~s^{-1}$}$ channel width for $\mathrm{CO}\,(3\text{--}2)$ as S/N ratio is not a concern there. We similarly combine the continuum-subtracted line data from all array configurations (now on a common spectral grid) to make a joint dataset for each emission line.

We image the joint, calibrated visibility dataset for each emission line and continuum following broadly the PHANGS imaging scheme (cite: Leroy_etal_2021b). We first run a shallow, multiscale `tclean` to identify both compact and extended emission across the entire FoV down to $\mathrm{S/N}=4$. After this step, we run a deeper, singlescale `tclean` to pick up remaining emission down to $\mathrm{S/N}=1$ for the $\mathrm{CO}\,(3\text{--}2)$ line and $\mathrm{S/N}=2$ for all other lines and continua. To avoid divergence, we restrict this second step to within a cleaning mask, which is constructed based on archival, lower-resolution $\mathrm{CO}\,(2\text{--}1)$ data (cite: Sun_etal_2020a; Leroy_etal_2021a) and only includes $ppv$ locations with significant $\mathrm{CO}\,(2\text{--}1)$ emission. In both `tclean` calls, we weigh the visibility data using the *Briggs* method with a robustness parameter of 1.0, which offers the best trade-off between sensitivity and resolution for our science goal (i.e., discerning individual YMCs). This *robust* weighting is applied to all continua and lines except for $\mathrm{CO}\,(3\text{--}2)$, which is bright enough to afford a *uniform* weighting that minimizes side-lobes and facilitates high dynamic range imaging.

### Postprocessing and Data Characteristics

After obtaining the cleaned continuum images and line data cubes, we correct them for the primary beam response pattern and then mildly convolve them so that the beam shapes become round. We also convert all line data cubes to brightness temperature units (K) according to the corresponding line frequencies.

The output Band 3 and 7 continuum images have circularized beam sizes of $0.17\ensuremath{''}$ and $0.13\ensuremath{''}$, respectively[^1]. To facilitate rigorous comparisons between them, we further convolve the Band 7 continuum image to $0.17\ensuremath{''}$ resolution to match the Band 3 image. These final continuum images have noise levels of $\sim$6.5–6.8 $\mu$Jy/beam (Band 3) and $\sim$80–100 $\mu$Jy/beam (Band 7) across the central starburst region (also see Table [2](#tab:data)).

The output data cube for the $\mathrm{CO}\,(3\text{--}2)$ line reaches a spatial resolution of $0.10\ensuremath{''}$ thanks to the *uniform* weighting. The noise level at the native $0.85\;\mbox{$\rm km~s^{-1}$}$ channel width is 1.9–2.5 K, which already enables detection of $\mathrm{CO}\,(3\text{--}2)$ emission across a large number of channels at high significance in most regions. To further increase the image dynamic range, we also generate another version of the $\mathrm{CO}\,(3\text{--}2)$ cube by rebinning to a $5\;\mbox{$\rm km~s^{-1}$}$ channel width, which lowers the noise down to 0.9–1.2 K and allows us to pick up more diffuse emission (Table [2](#tab:data)).

The output data cubes for the other high critical density molecular lines \[$\mathrm{HCO^+}\,(4\text{--}3)$ and $\mathrm{CS}\,(7\text{--}6)$ in Band 7; $\mathrm{CS}\,(2\text{--}1)$, $\mathrm{HCO^+}\,(1\text{--}0)$, and $\mathrm{HCN}\,(1\text{--}0)$ in Band 3\] have beam sizes of $0.12\ensuremath{''}$–$0.19\ensuremath{''}$. The noise levels are 0.3–0.5 K (Band 7) and 1.0–1.2 K (Band 3) per 10 $\mbox{$\rm km~s^{-1}$}$ channel (Table [2](#tab:data)).

## HST Data

We make use of multi-band *Hubble Space Telescope* (HST) images of NGC 3351 acquired by the LEGUS (cite: Calzetti_etal_2015) and PHANGS–HST (cite: Lee_etal_2022) surveys. These are broad-band imaging data obtained with the Wide Field Camera 3 (WFC3), together covering the full galaxy from UV to optical wavelengths (Figure [1](#fig:wide_field) left panel; also see Figure 1 in (cite: Turner_etal_2021) for the sky footprint covered by each survey). The point spread functions (PSFs) of these data are $\lesssim0.1\ensuremath{''}$ in FWHM, slightly better than the beam sizes achieved with our ALMA observations.

To facilitate source cross-matching with ALMA, we take advantage of an updated PHANGS-HST star cluster catalog presented in (cite: Maschmann_etal_2024) and (cite: Thilker_etal_2024). This new catalog builds upon the previous PHANGS-HST catalog release (cite: Lee_etal_2022). Aside from improved cluster classification schemes (cite: Hannon_etal_2023), a major improvement is in the spectral energy distribution (SED) fitting, for which a physically motivated “decision tree” has been introduced to help address photometric degeneracies between age, extinction, and metallicity (cite: Turner_etal_2021; Whitmore_etal_2023a). Specifically, this decision tree uses source morphology, broadband color information, and location relative to H$\alpha$-bright complexes (based on ground-based narrowband H$\alpha$ observations; A. Razza et al., in preparation) to pre-select candidates of young reddened clusters. Their SEDs are subsequently fit with a separate set of stellar population models with young ages (${\leq}6$ Myr) and potentially higher extinction (up to $\rm E(B{-}V)=3.0$). This refined scheme results in more complete identification and better age estimates for young clusters with associated H$\alpha$ emission throughout the PHANGS–HST sample. We refer interested readers to (cite: Thilker_etal_2024) for more thorough descriptions of the rationale, implementation, and results of this new SED fitting scheme.

In this work, we use this updated cluster catalog to cross-match with sources detected in the ALMA data and compare their estimated physical properties. Within our region of interest (i.e., the central region of NGC 3351), the new SED fitting scheme gives refined age estimates for ${\sim}65\%$ of clusters. This fraction is higher than typical due to the dusty and crowded nature of this region, which makes SED fitting with older methods particularly challenging. Further inspection suggests that the new age estimates are either similar to or more reasonable than the old solutions in ${\sim}80{-}90\%$ of the cases (cite: Thilker_etal_2024). The remainder are mostly caused by incorrect association of H$\alpha$ emission to slightly older clusters (due to the much coarser ${\sim}1.2\ensuremath{''}$ PSF of the ground-base H$\alpha$ data used in the decision tree), which affect the accuracy of cluster age estimates primarily between $1{-}10$ Myr. To mitigate this minor issue, we generally avoid using age estimates for individual clusters and only rely on more robust aggregate statistics, such as the *total number* of clusters younger than $10$ Myr. We anticipate future works based on higher-resolution HST narrowband H$\alpha$ observations (PIs: F. Belfiore, R. Chandar, D. Thilker) to thoroughly address this issue.

## JWST Data

We make use of multi-band JWST NIRCam/MIRI images of NGC 3351 acquired as part of the PHANGS–JWST Cycle 1 Treasury survey (cite: Lee_etal_2023). These broad- and medium-band images are available from the PHANGS DR1.0.1 public image release (cite: Williams_etal_2024). This work primarily uses data in the 2.0–11.3 $\ensuremath{\mu}m$ wavelength range, with PSFs ranging from $0.066\ensuremath{''}$ (F200W with NIRCam) to $0.38\ensuremath{''}$ (F1130W with MIRI) in FWHM.

For source cross-matching with ALMA, we also use a catalog of compact 3.35 $\ensuremath{\mu}m$ sources constructed by J. Rodríguez et al. (in preparation) following the methodology of (cite: Rodriguez_etal_2023). In short, the sources are identified in the F335M image as local maxima above three times the estimated background level in the neighboring ${<}100$ pc area. This is done with a peak-finding algorithm *find_peaks* in `PHOTUTILS` (cite: Bradley_etal_2022). In more crowded regions, the software `SExtractor` (cite: Bertin_Arnouts_1996) is also employed to deblend the sources with a Mexican-hat filter. This F335M-based source identification scheme allows for more systematic detections of embedded star clusters (cite: Rodriguez_etal_2023), which is especially important for cross-matching with ALMA sources in this work.

# Analyses

From the rich ALMA data set (see Table [2](#tab:data)), we identify compact (sub-)millimeter continuum sources, characterize their observable properties, and cross-match them with sources in the HST and JWST data. We detail these analyses in the following subsections.

## Identifying ALMA Sources

We identify bright, compact sources in the 93 GHz and 350 GHz continuum images as YMC candidates, following (cite: Leroy_etal_2018) and (cite: Emig_etal_2020). These sources are selected based on a minimum $\mathrm{S/N}=5$ at peak brightness. Considering the number of independent measurements (beams) across the region of interest ($r\,{<}\,500$ pc, Figure [2](#fig:alma-zoom)), this detection threshold corresponds to a false positive rate of $<0.01$, i.e., there is ${<}1\%$ chance for *any* of our selected sources to be spurious. We choose this rather stringent criterion to ensure sample purity, which is critical for following analysis based on the source number counts (Section [5.2](#sec:discuss:timescale)). This is however at the expense of a higher false negative rate, i.e., missing many potentially real sources with lower peak brightness (as can be seen in Figure [2](#fig:alma-zoom)).

We identify 15 sources at 93 GHz and 11 at 350 GHz. Among these, 8 sources at 93 GHz coincide spatially with counterparts at 350 GHz. These are likely the same objects seen at both frequencies. Considering these as duplicates, we identify in total 18 ALMA sources, all of which are marked and labeled in Figure [2](#fig:alma-zoom) (lower panels; also see Table [3](#tab:YMC_obs)). Almost all sources appear to be compact and well-isolated, with a single peak and a relatively round shape. The only exceptions are two closely connected sources in the 93 GHz image (sources #6 and #7 in Figure [2](#fig:alma-zoom)), which we separate by visual inspection.

All the 350 GHz sources and the majority of the 93 GHz sources are located in regions with bright $\mathrm{CO}\,(3\text{--}2)$ emission (see contours in Figure [2](#fig:alma-zoom) bottom panels), consistent with forming YMCs surrounded by substantial molecular gas reservoir. There are however four 93 GHz-only sources (#1, #4, #13, #16) that are located in regions with no detectable $\mathrm{CO}\,(3\text{--}2)$ emission. We will discuss the nature of these sources in Section [5.1](#sec:discuss:nature).

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | Coordinate | $S_\mathrm{93}$ | $R_\mathrm{hl,\,93}$ | $S_\mathrm{350}$ | $R_\mathrm{hl,\,350}$ | $L'_\mathrm{HCN\,1-0}$ | $\sigma_\mathrm{HCN\,1-0}$ |
|  | \[$^\circ$\] | \[mJy\] | \[pc\] | \[mJy\] | \[pc\] | $[10^3\,\mbox{$\rm K~km~s^{-1}~pc^2$}]$ | $[\mbox{$\rm km~s^{-1}$}]$ |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) |
|  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |
| 1 | $160.990061,\,+11.703993$ | $0.037\pm0.012$ | $(4.3\pm0.6)$ | $<$$0.33$ | $\cdots$ | $\cdots$ | $\cdots$ |
| 2 | $160.989812,\,+11.704463$ | $0.053\pm0.016$ | $2.9\pm1.5$ | $<$$0.34$ | $\cdots$ | $4.7\pm1.5$ | $8.6\pm3.0$ |
| 3 | $160.990040,\,+11.704893$ | $0.034\pm0.009$ | $(3.7\pm0.4)$ | $1.23\pm0.22$ | $2.9\pm1.0$ | $7.4\pm1.9$ | $9.5\pm2.9$ |
| 4 | $160.990317,\,+11.704807$ | $0.029\pm0.008$ | $(3.3\pm0.3)$ | $<$$0.34$ | $\cdots$ | $\cdots$ | $\cdots$ |
| 5 | $160.990521,\,+11.705508$ | $0.058\pm0.016$ | $1.4\pm3.4$ | $1.85\pm0.44$ | $6.6\pm1.4$ | $<$$12.7$ | $\cdots$ |
| 6 | $160.990601,\,+11.705601$ | $0.134\pm0.018$ | $3.5\pm0.6$ | $1.87\pm0.37$ | $5.4\pm1.0$ | $23.4\pm4.3$ | $15.8\pm4.2$ |
| 7 | $160.990644,\,+11.705525$ | $0.140\pm0.028$ | $6.0\pm1.0$ | $1.29\pm0.30$ | $4.1\pm1.2$ | $12.3\pm3.2$ | $9.2\pm2.8$ |
| 8 | $160.990779,\,+11.705358$ | $0.040\pm0.014$ | $(4.6\pm0.7)$ | $<$$0.35$ | $\cdots$ | $6.2\pm1.9$ | $7.9\pm2.8$ |
| 9 | $160.990925,\,+11.705318$ | $<$$0.033$ | $\cdots$ | $0.98\pm0.29$ | $4.1\pm1.2$ | $9.9\pm2.8$ | $11.6\pm4.3$ |
| 10 | $160.991335,\,+11.705510$ | $<$$0.033$ | $\cdots$ | $0.81\pm0.23$ | $2.6\pm1.1$ | $<$$5.5$ | $\cdots$ |
| 11 | $160.991393,\,+11.705557$ | $<$$0.033$ | $\cdots$ | $1.07\pm0.32$ | $4.0\pm1.6$ | $<$$6.5$ | $\cdots$ |
| 12 | $160.991685,\,+11.705156$ | $0.035\pm0.013$ | $(4.5\pm0.7)$ | $2.72\pm0.40$ | $6.2\pm0.8$ | $15.0\pm3.6$ | $10.6\pm3.1$ |
| 13 | $160.992590,\,+11.704243$ | $0.041\pm0.014$ | $(4.5\pm0.7)$ | $<$$0.37$ | $\cdots$ | $\cdots$ | $\cdots$ |
| 14 | $160.990905,\,+11.702250$ | $0.056\pm0.017$ | $2.9\pm1.3$ | $0.62\pm0.24$ | $3.3\pm1.4$ | $<$$6.5$ | $\cdots$ |
| 15 | $160.990434,\,+11.701863$ | $0.152\pm0.020$ | $4.0\pm0.6$ | $3.17\pm0.48$ | $7.6\pm0.9$ | $20.7\pm5.5$ | $8.6\pm2.6$ |
| 16 | $160.990357,\,+11.701448$ | $0.026\pm0.008$ | $(3.4\pm0.4)$ | $<$$0.37$ | $\cdots$ | $\cdots$ | $\cdots$ |
| 17 | $160.990040,\,+11.701785$ | $0.083\pm0.022$ | $4.2\pm1.7$ | $<$$0.36$ | $\cdots$ | $10.5\pm2.6$ | $12.0\pm3.9$ |
| 18 | $160.989975,\,+11.701884$ | $0.153\pm0.028$ | $5.9\pm0.9$ | $1.44\pm0.35$ | $5.3\pm1.3$ | $<$$8.2$ | $\cdots$ |

: Observed Properties of the ALMA Sources

Table notes: (1) source ID as appeared in Figure [2](#fig:alma-zoom); (2) source RA and Dec coordinates; (3) continuum flux density at 93 GHz; (4) half-light radius at 93 GHz, defined as the geometric mean of the beam-deconvolved semi-major and semi-minor axes (for sources with unsuccessful beam deconvolution, we report the original values in parentheses); (5) continuum flux density at 350 GHz; (6) half-light radius at 350 GHz (note that all detected sources have successful beam deconvolution); (7) $\mathrm{HCN}\,(1\text{--}0)$ line integrated luminosity (sources without CO 3–2 emission appear as “$\cdots$” due to the lack of prior information for determining velocity range; §[3.2](#sec:analyses:characterize)); (8) $\mathrm{HCN}\,(1\text{--}0)$ line velocity dispersion (i.e., effective width; §[3.2](#sec:analyses:characterize)).

## Characterizing ALMA Sources

We measure fluxes and sizes of the 18 sources in the 93 GHz and 350 GHz continua using the CASA task `imfit`. This task fits a 2D Gaussian function to the flux distribution within a user-defined region. First, we define a circular aperture around each identified source with a diameter of $0.34\ensuremath{''}$, which is twice the beam FWHM[^2]. We then perform the `imfit` task on the continuum image within the circular aperture for each source. Note that we set the `imfit` parameter `dooff=True` in order to fit for and subtract a smooth background that may be present at the location of some sources. We also ask `imfit` to try deconvolving the beam size from the best-fit 2D Gaussian profile so that we can recover the intrinsic size of each source. We have visually inspected all `imfit` results to ensure reliability.

From the `imfit` results, we record the measured fluxes and radii (original or deconvolved) for all sources and list them in Table [3](#tab:YMC_obs). The source fluxes range over $S_{93}=0.03{-}0.15$ mJy at 93 GHz and $S_{350}=0.6{-}1.9$ mJy at 350 GHz. The beam-deconvolved source half-light radii (calculated as the geometric mean of the semi-major and semi-minor axes) ranges over $R_\mathrm{hl,\,93}=1.4{-}6.0$ pc and $R_\mathrm{hl,\,350}=2.6{-}7.6$ pc. We note that the deconvolution is unsuccessful for several 93 GHz sources because their observed major/minor axis lengths are smaller than the beam size, whereas none of the 350 GHz sources has similar issues. For the unsuccessful cases, we report the original 2D Gaussian sizes in Table [3](#tab:YMC_obs) and treat these numbers as upper limits on the intrinsic source radii.

In addition to the continuum measurements, we also extract for each source a set of molecular line spectra (see Table [2](#tab:data) for a list of included lines). We define elliptical apertures for spectra extraction based on the best-fit 2D Gaussian for the continuum sources. For sources with both 93 GHz and 350 GHz detections, we use the apertures determined from the 350 GHz detections, as we expect molecular line emission to be more spatially associated with thermal dust emission than free-free emission.

We also perform background subtraction on the extracted line spectra. To do this, we define a “background annulus” around the source, calculate the mean emission spectrum within that annulus, and subtract this mean spectrum from the extracted spectrum at the location of the source. For isolated sources, the background annuli are set to have inner/outer radii of $2\times$/$3\times$ the aperture radii for source extraction. For clustered sources, we manually draw an annulus safely enclosing all the sources and set the outer radius to be $2\times$ the inner radius. For source #2 that is in between two $\mathrm{CO}\,(3\text{--}2)$ blobs (Figure [2](#fig:alma-zoom)), we omit background subtraction since there is no obvious way to reliably determine the local background level in this case, and that level can be zero for some choices of the background aperture.

After extracting the emission line spectra and subtracting the local background, we measure the line integrated luminosities and line widths for all sources and all lines. We use the brightest line in our sample, $\mathrm{CO}\,(3\text{--}2)$, as a prior to determine the velocity range of each source and then measure line integrated flux and effective width (cite: Heyer_etal_2001; Sun_etal_2018) for all high critical density lines. This work mainly uses measurements for the $\mathrm{HCN}\,(1\text{--}0)$ line, which we report in Table [3](#tab:YMC_obs). The spectra of all molecular lines are presented in Appendix [7](#apdx:spectra).

## Cross-matching ALMA–JWST–HST Sources

+:---+:-------:+:-------:+:------------------------:+:--------:+
| ID | ALMA    | ALMA    | JWST                     | HST      |
+----+---------+---------+--------------------------+----------+
|    | 350 GHz | 93 GHz  | 3.35 $\ensuremath{\mu}m$ | clusters |
+----+---------+---------+--------------------------+----------+
|    |         |         |                          |          |
+----+---------+---------+--------------------------+----------+
|    |         |         |                          |          |
+----+---------+---------+--------------------------+----------+
| 1  |         | $\circ$ |                          |          |
+----+---------+---------+--------------------------+----------+
| 2  |         | $\circ$ | $\circ$                  | $\circ$  |
+----+---------+---------+--------------------------+----------+
| 3  | $\circ$ | $\circ$ |                          |          |
+----+---------+---------+--------------------------+----------+
| 4  |         | $\circ$ |                          |          |
+----+---------+---------+--------------------------+----------+
| 5  | $\circ$ | $\circ$ |                          |          |
+----+---------+---------+--------------------------+----------+
| 6  | $\circ$ | $\circ$ | $\circ$                  |          |
+----+---------+---------+--------------------------+          |
| 7  | $\circ$ | $\circ$ | $\circ$                  |          |
+----+---------+---------+--------------------------+----------+
| 8  |         | $\circ$ | $\circ$                  | $\circ$  |
+----+---------+---------+--------------------------+----------+
| 9  | $\circ$ |         |                          |          |
+----+---------+---------+--------------------------+----------+
| 10 | $\circ$ |         |                          |          |
+----+---------+---------+--------------------------+----------+
| 11 | $\circ$ |         |                          |          |
+----+---------+---------+--------------------------+----------+
| 12 | $\circ$ | $\circ$ |                          |          |
+----+---------+---------+--------------------------+----------+
| 13 |         | $\circ$ |                          |          |
+----+---------+---------+--------------------------+----------+
| 14 | $\circ$ | $\circ$ | $\circ$                  |          |
+----+---------+---------+--------------------------+----------+
| 15 | $\circ$ | $\circ$ | $\circ$                  |          |
+----+---------+---------+--------------------------+----------+
| 16 |         | $\circ$ |                          |          |
+----+---------+---------+--------------------------+----------+
| 17 |         | $\circ$ | $\circ$                  | $\circ$  |
+----+---------+---------+--------------------------+----------+
| 18 | $\circ$ | $\circ$ | $\circ$                  | $\circ$  |
+----+---------+---------+--------------------------+----------+

: Source Cross-matching Results

Table notes: Meaning of various markers used above:\
$\circ$ – unique, unambiguous cross-match;\
– a close ALMA source pair (#6 and #7) cross-matched to the same HST cluster.

For the 18 sources detected in the (sub-)millimeter ALMA observations, we further check if they have counterparts in the UV–optical HST images and the near- to mid-IR JWST images. The presence or absence of each source at different wavelengths can inform us the presence or absence of various components in a forming cluster (e.g., gas versus stars) as well as the level of dust extinction towards that cluster. Such qualitative information is especially important for inferring the time evolution of YMCs, which we will discuss in depth below in Section [5.1](#sec:discuss:nature).

For ALMA–HST source cross-matching, we take the star cluster catalog generated from the multi-band HST images (cite: Lee_etal_2022) and focus on class 1 and 2 objects (i.e., compact clusters). As the HST images have higher resolution (sharper PSF) than the ALMA continuum images, we consider an HST cluster to be cospatial with an ALMA source if the distance between their central coordinates is smaller than the major axis half width at half maximum (HWHM) of the ALMA source. This cross-matching scheme yields six ALMA sources with HST cluster counterparts (Figure [3](#fig:hst-zoom) and Table [4](#tab:crossmatch)). These HST clusters have SED fitting-based mass estimates ranging over $5{\times}10^4{-}4{\times}10^5\,\mbox{$\rm M_\odot$}$ and ages ranging over 1–4 Myr, though the ages for some clusters may be underestimated for the reasons described in Section [2.2](#sec:data:HST).

For ALMA–JWST source cross-matching, we first rely on the 3.35 $\ensuremath{\mu}m$ source catalog (cite: Rodriguez_etal_2023). Similar to the ALMA–HST source matching criterion, the center-to-center distance between a JWST 3.35 $\ensuremath{\mu}m$ source and an ALMA source needs to be within the major axis HWHM of the ALMA source to be considered a match. For ALMA sources with multiple matched 3.35 $\ensuremath{\mu}m$ sources, we use the one with a smaller separation.

One caveat with using only the 3.35 $\ensuremath{\mu}m$ source catalog for cross-matching is that it misses a small number of sources that are only visible in other IR bands, partly due to different PSF sizes and sensitivity. To address this issue, we also visually inspect the multi-band JWST images (Figure [4](#fig:jwst-zoom)) near the location of each ALMA source to determine (1) if an IR counterpart is clearly visible in other bands but not included in the 3.35 $\ensuremath{\mu}m$ source catalog, and (2) if a cross-matched 3.35 $\ensuremath{\mu}m$ source is consistently present across other IR bands. We find the F200W data particularly helpful in this regard, thanks to its smaller PSF (FWHM 0.066$''$ versus 0.11$''$) and longer integration time (1200s versus 390s). Combining the catalog matching and visual inspection procedures, we find in total eight unique cross-matched sources (Table [4](#tab:crossmatch)).

# Physical Properties of the Young Massive Cluster Candidates

From the measured YMC candidate sizes and flux densities in the ALMA (sub-)millimeter continua, their molecular line fluxes and line widths, as well as ancillary information available for their HST and JWST counterparts (if any), we estimate their gas masses (Section [4.1](#sec:results:Mgas)), stellar masses (Section [4.2](#sec:results:Mstar)), sizes (Section [4.3](#sec:results:size)), and other key properties (Sections [4.4](#sec:results:Mtot_fgas)–[4.8](#sec:results:Sigmagas)). We detail the derivations below and summarize key quantitative results in Table [5](#tab:YMC_phys).

## Gas Mass

We use the 350 GHz continuum emission as a dust tracer, from which we infer the masses and sizes of the YMC gas reservoirs. Generally speaking, the 350 GHz continuum includes not only thermal dust emission, but also free-free and potentially synchrotron emission. To estimate the fractional contribution of these components, we assume the 93 GHz and 350 GHz flux densities for each object are a mixture of thermal dust and free-free emission, with intrinsic spectral indices of $\alpha=4.0$ (dust) and $\alpha=-0.15$ (free-free), consistent with what previous studies adopted for similar systems (cite: Emig_etal_2020). With this simple, two-component decomposition, we derive the fractional contribution of dust and free-free emission at each frequency and find that thermal dust contribution indeed dominates the 350 GHz continuum for all identified objects (see Figure [5](#fig:check_flux)). This conclusion agrees with previous YMC studies in other galaxies (cite: Leroy_etal_2018; Emig_etal_2020), for which the free-free contribution to the 350 GHz continuum was also found to be $<10$% in most cases.

The above analysis ignores the contribution of synchrotron emission, which may be non-negligible at 93 GHz (cite: Emig_etal_2020; Mills_etal_2021). Qualitatively, we expect the inclusion of a synchrotron component to lower the estimated fraction of free-free at 93 GHz and raise the fraction of thermal dust at 350 GHz. On the one hand, this makes it even more reasonable to assume the 350 GHz continuum is dust-dominated for all our sources. On the other hand, it becomes an issue when interpreting the 93 GHz continuum, as discussed below in Section [4.2](#sec:results:Mstar).

After verifying that the 350 GHz continuum is dominated by thermal dust emission, we convert the 350 GHz flux density into a gas mass in two steps. First, we calculate the dust optical depth at 350 GHz via $$\begin{align}
\tau_{350} \approx \frac{S_{350}}{\Omega_{350}\,B_\nu(T_\mathrm{dust})}~.
\label{eq:tau350}
\end{align}$$ Here $\Omega_{350}$ is the solid angle extended by the 350 GHz source on the sky, and $B_\nu(T_\mathrm{dust})$ the blackbody function for a given dust temperature $T_\mathrm{dust}$. We use a dust temperature of $T_\mathrm{dust}=130$ K following (cite: Leroy_etal_2018), but there can be a $\sim$50% uncertainty on this value. We note that Equation [\[eq:tau350\]](#eq:tau350) is a good approximation only in the optically thin limit. Nonetheless, our estimated optical depths of $\tau_{350}\approx0.001\text{--}0.005$ for all sources make this approximation appropriate.

We then estimate the gas mass associated with each source via $$\begin{align}
M_\mathrm{gas} = \Sigma_\mathrm{gas}\,A_\mathrm{350} = \frac{\tau_{350}}{\kappa_{350}\,\mathrm{D/G}}\,\Omega_{350}\,d^2~.
\label{eq:Mgas}
\end{align}$$ Here $\kappa_{350}=1.9\;\mathrm{cm^2/g}$ is the adopted dust opacity at 350 GHz (cite: Ossenkopf_Henning_1994), and $\mathrm{D/G}=1/100$ the adopted dust-to-gas ratio (cite: Draine_etal_2007). Both values are chosen for consistency with previous YMC studies (cite: Leroy_etal_2018; Emig_etal_2020), but they can introduce systematic uncertainties on the order of $\sim$0.3 dex. $A_\mathrm{350}=\Omega_{350}\,d^2$ is the physical area of the 350 GHz source, which is needed to convert gas surface density into a total gas mass. The $\Omega_{350}$ term effectively cancels out when combining Equations [\[eq:tau350\]](#eq:tau350) and [\[eq:Mgas\]](#eq:Mgas).

We find gas masses of $3\times10^4{-}2\times10^5\;\mbox{$\rm M_\odot$}$ for the 11 YMCs detected at 350 GHz. For the non-detections, we put 5$\sigma$ upper limits of $\approx2\times10^4\;\mbox{$\rm M_\odot$}$ (see Table [5](#tab:YMC_phys)). These gas masses are consistent with expectations for YMC progenitors or the gas reservoir associated with forming YMCs (cite: PortegiesZwart_etal_2010). Considering uncertainties on the adopted parameters in Equations [\[eq:tau350\]](#eq:tau350) and [\[eq:Mgas\]](#eq:Mgas), we expect an overall systematic uncertainty of $\sim$0.5 dex on these gas mass estimates.

As an independent sanity check, we also derive alternative gas masses from the $\mathrm{HCN}\,(1\text{--}0)$ line luminosities (Section [3.2](#sec:analyses:characterize) and Table [3](#tab:YMC_obs)) with a commonly-adopted HCN-to-H$_2$ conversion factor of $\alpha_\mathrm{HCN}\approx10\,\mbox{$\rm M_\odot~pc^{-2}\ (K~km~s^{-1})^{-1}$}$ (cite: Gao_Solomon_2004), although lower values have been advocated for systems with more extreme conditions (cite: Garcia-Burillo_etal_2012; Shimajiri_etal_2017) that in part resemble the local conditions in YMCs. Our HCN-based gas masses show clear correlation and broad agreement with the 350 GHz-based estimates (Figure [6](#fig:check_Mgas)). Although the former tend to yield slightly higher values, the observed discrepancy is attributable to the large systematic uncertainties on the adopted $\alpha_\mathrm{HCN}$ and several coefficients in Equations [\[eq:tau350\]](#eq:tau350) and [\[eq:Mgas\]](#eq:Mgas).

## Stellar Mass

We use the 93 GHz continuum to constrain the free-free emission from ionized gas in H II regions, from which we infer the ionizing photon production rate and subsequently the mass of the stellar population associated with the YMC candidates. As mentioned in Section [4.1](#sec:results:Mgas), the 93 GHz continuum may also include contribution from thermal dust and synchrotron emission. Our simple two-component modelling (dust+free-free; Figure [5](#fig:check_flux)) suggests that the dust contribution at 93 GHz is less than $20\%$ for all but one source (#12). However, the issue of ignoring synchrotron emission in the modelling becomes more concerning at 93 GHz, as synchrotron may have a non-trivial contribution to the observed 93 GHz flux density (e.g., (cite: Emig_etal_2020) reported a median synchrotron fraction of 0.36 for YMCs in NGC 4945, (cite: Mills_etal_2021) found similar values for those in NGC 253).

It is possible to better constrain the synchrotron fraction at 93 GHz given sensitive, lower frequency observations at similar angular resolution. For NGC 3351, previous observations at 1.4 GHz with the Multi-Element Radio Linked Interferometer Network (MERLIN) provide the best lever arm for this purpose (cite: Hagele_etal_2010). With no point source detected in the central region at $0.29\ensuremath{''}\times0.17\ensuremath{''}$ resolution, they put a $6\sigma$ upper limit of $0.30\,\mbox{$\rm mJy$}$ for any compact source at 1.4 GHz. Adopting a characteristic spectral index of $-0.75$ for synchrotron emission, this translates to an upper limit of $\sim$0.013 $\mbox{$\rm mJy$}$ at 93 GHz. In this case, the synchrotron fraction is constrained to be $\lesssim10\%$ for the brightest sources at 93 GHz ($S_{93}\approx0.15\,\mbox{$\rm mJy$}$) and $\lesssim40\%$ for the fainter ones ($S_{93}\approx0.03\,\mbox{$\rm mJy$}$, Table [3](#tab:YMC_obs)).

Considering the lack of more sensitive low-frequency data to further constrain the synchrotron spectral index and fraction, we choose to use our observed 93 GHz flux densities directly as free-free flux densities, which may introduce a bias of at most $40\%$ per our estimates. We convert the 93 GHz free-free flux densities into ionizing photon production rates, following (cite: Emig_etal_2020): $$\begin{equation}
Q_0 \approx 
1.6\times10^{52}\,\mathrm{s}^{-1}
\left(\frac{S_{93}}{\mbox{$\rm mJy$}}\right)
\left(\frac{d}{10\,\mathrm{Mpc}}\right)^2
\left(\frac{T_\mathrm{e}}{6000\,\mathrm{K}}\right)^{-0.51}~.
\label{eq:Q0}
\end{equation}$$ Here we use a characteristic electron temperature of $T_\mathrm{e}=6000\,\mathrm{K}$ that is typical of galaxy centers (cite: Bendo_etal_2016; Emig_etal_2020; Henshaw_etal_2023). Equation [\[eq:Q0\]](#eq:Q0) also implicitly assumes that the escape fraction of ionizing photons from the YMCs are negligible, which should be a reasonable assumption for the young, deeply embedded clusters studied in this work.

We further infer a stellar mass from the ionizing photon production rate via $$\begin{equation}
M_\mathrm{\star} \approx \frac{Q_0}{2.2\times10^{46}\,\mathrm{s}^{-1}}\,\mbox{$\rm M_\odot$}~.
\label{eq:Mstar}
\end{equation}$$ This conversion is based on a Starburst99 simulation (cite: Leitherer_etal_1999) of a 3 Myr old stellar population with a (cite: Kroupa_2001) initial mass function and solar metallicity (cite: Williams_etal_2022). If we had assumed a zero-age stellar population (cite: Leroy_etal_2018), the estimated masses would be 2$\times$ smaller; an age of 5 Myr would instead yield 5$\times$ larger values (cite: Emig_etal_2020). Our adopted 3 Myr is consistent with the 1–4 Myr age range given by UV–optical photometric SED fitting for the few sources with HST counterparts (Section [3.3](#sec:analyses:crossmatch), modulo caveats described in Section [2.2](#sec:data:HST)). Such young ages seem reasonable since most 93 GHz sources are deeply embedded and have substantial gas reservoirs around them (Section [4.1](#sec:results:Mgas)), which suggests that supernova explosions have not gone off (i.e., age $\lesssim4$ Myr). The adopted 3 Myr is also consistent with our inferred YMC evolutionary timeline below in Section [5.2](#sec:discuss:timescale).

With Equations [\[eq:Q0\]](#eq:Q0) and [\[eq:Mstar\]](#eq:Mstar), we find stellar masses of $2\times10^4{-}1\times10^5\;\mbox{$\rm M_\odot$}$ for the 15 YMCs with detectable 93 GHz emission. For non-detections, the 5$\sigma$ upper limit on the 93 GHz flux translates to $\approx2.5\times10^4\;\mbox{$\rm M_\odot$}$ under the same assumptions (see Table [5](#tab:YMC_phys)). These stellar mass estimates are consistent with typical definition of YMCs (cite: PortegiesZwart_etal_2010). The main source of systematic uncertainty is the adopted stellar age for Equation [\[eq:Mstar\]](#eq:Mstar), which can introduce 0.3–0.6 dex of variations as discussed above.

For the few 93 GHz sources with HST counterparts, we find that the 93 GHz-based stellar mass estimates are systematically lower than the HST SED-based mass estimates (median offset ${\sim}0.5$ dex, Table [5](#tab:YMC_phys)). On the one hand, these sources are less embedded (visible in HST data), so it is possible that (1) they tend to be slightly older than 3 Myr on average, and (2) a non-negligible fraction of the ionizing photons do escape from the clusters. Both of these would lead to underestimated stellar masses via Equation [\[eq:Q0\]](#eq:Q0). On the other hand, the UV–optical SED-based mass estimates also have non-negligible uncertainties as discussed in Section [2.2](#sec:data:HST). We aim to address this issue in a follow-up study by modelling the full UV–optical–IR SED for all clusters identified in the joint HST+JWST dataset, potentially including the ALMA measurements whenever available.

## Size

We use the estimated (sub-)millimeter source sizes as indicators of the YMC candidate physical sizes. At the distance of NGC 3351, the (beam-deconvolved) half-light radii correspond to 2–8 pc for the 11 sources detected at 350 GHz (Table [3](#tab:YMC_obs)). This range broadly overlaps the typical range of radii measured for YMCs in the Milky Way (cite: PortegiesZwart_etal_2010) and in other extragalactic systems (cite: Ryon_etal_2017).

For the YMCs that are only detected at 93 GHz, we instead use their estimated sizes from the 93 GHz image, which spans a similar range (1–6 pc). To be more precise, the 93 GHz free-free source sizes should reflect the sizes of the H II regions associated with the YMCs rather than the star clusters themselves. Nonetheless, for the eight sources detected in both bands, we find reasonable agreement between their 93 GHz and 350 GHz sizes (Table [3](#tab:YMC_obs)), which justifies this choice.

We note that the YMC size estimates may be affected by systematic effects due to finite data resolution (in addition to the statistical uncertainties quoted in Table [3](#tab:YMC_obs)). Our estimated source sizes are all within a factor of three of the beam size, as seen in similar studies for other galaxies over a range of data resolution (cite: Leroy_etal_2018; Emig_etal_2020; Levy_etal_2021; Levy_etal_2022; He_etal_2022). When examining our 350 GHz image at the $0.13\ensuremath{''}\sim6$ pc native resolution, we also find tentative evidence for substructures *within* some sources identified at the $0.17\ensuremath{''}\sim8$ pc working resolution. These observations suggest that the estimated source sizes may become smaller as one pushes to smaller beam sizes, which was indeed the case with studies of YMCs in NGC 253 (cite: Leroy_etal_2018; Levy_etal_2021). That being said, the differences between our 350 GHz images at $0.13\ensuremath{''}$ and $0.17\ensuremath{''}$ are only marginal, so we choose to work with the latter for more straightforward flux and size comparisons with the 93 GHz data. We expect to test the resolution effect in a follow-up study with ALMA Cycle 9 observations (partially executed, PI: J. Sun), which will improve the data resolution by a factor of three.

## Total Mass & Gas Fraction

Adding together the stellar and gas mass estimates (or upper limits) for each YMC candidate, we find total masses of $M_\mathrm{tot} \equiv M_\mathrm{gas}+M_\star \approx 0.3{-}3\times10^5\;\mbox{$\rm M_\odot$}$ (Table [5](#tab:YMC_phys)). The estimated gas fraction, $f_\mathrm{gas} \equiv M_\mathrm{gas} / (M_\mathrm{gas}+M_\star)$, ranges from $\lesssim$25% to $\gtrsim$70%. This suggests that the YMC candidates identified from our ALMA data span a wide range of evolutionary stages, from the gas mass-dominated early phase to the stellar mass-dominated late phase of cluster formation.

It is worth emphasizing that the total mass and gas fraction estimates can be affected by the ${\sim}0.5$ dex systematic uncertainties on $M_\mathrm{gas}$ and $M_\star$ mentioned in Section [4.1](#sec:results:Mgas) & [4.2](#sec:results:Mstar). For example, because $M_\star$ as calculated from Equation [\[eq:Mstar\]](#eq:Mstar) can vary by a factor of 2–5 depending on the assumed stellar age, the $f_\mathrm{gas}$ estimates should be similarly sensitive to this assumption. Indeed, (cite: Leroy_etal_2018) and (cite: Mills_etal_2021) assumed zero-age stellar population for the YMCs in NGC 253 and found comparable stellar and gas masses (modulo synchrotron contamination); in contrast, (cite: Emig_etal_2020) assumed a 5 Myr age for the YMCs in NGC 4945 and found them to be stellar mass-dominated. While the different ages assumed in these works are well motivated by known differences of the host galaxies, it is still possible that these different assumptions may partly cause the differing results between studies. This underlines the importance of accurate YMC stellar age estimates, which we expect to improve with the joint HST+JWST SED fitting.

## Virial Mass

We use the measured radius ($R_\mathrm{hl}$; see Section [4.3](#sec:results:size)) and gas velocity dispersion (HCN–0 line width, $\sigma_\mathrm{HCN}$; see Section [3.2](#sec:analyses:characterize)) to derive the virial mass for each object: $$\begin{align}
M_\mathrm{vir} 
&\equiv \frac{5 \,\sigma_\mathrm{HCN}^2\,R_\mathrm{hl}}{f\,G}\nonumber\\
&\approx 7.0\times10^4\,\mbox{$\rm M_\odot$}\left(\frac{\sigma_\mathrm{HCN}}{10\,\mathrm{km/s}}\right)^2 \left(\frac{R_\mathrm{hl}}{1\,\mathrm{pc}}\right) \left(\frac{f}{5/3}\right)^{-1}~.
\label{eq:Mvir}
\end{align}$$ Here the geometrical factor $f$ depends on the density profile of the YMCs (cite: Bertoldi_McKee_1992). We adopt a density profile of $\rho \propto r^{-2}$ following (cite: Leroy_etal_2018), which corresponds to $f = 5/3$.

We find virial masses of $10^5{-}10^6\,\mbox{$\rm M_\odot$}$ for the 12 YMC candidates with $\mathrm{HCN}\,(1\text{--}0)$ line measurements available (Table [5](#tab:YMC_phys)). Most of them have $M_\mathrm{vir} \gtrsim 2\,M_\mathrm{tot}$, which seems to imply their gas reservoirs are not gravitationally bound or only marginally bound (Figure [8](#fig:Mtot_vs_Mvir)). However, the estimated virial masses have large statistical and systematic uncertainties due to the uncertain size and velocity dispersion measurements, and they also tend to be overestimated because (1) the actual YMC sizes may be smaller than those measured at our data resolution (Section [4.3](#sec:results:size)), and (2) the HCN velocity dispersion may also be biased high due to contamination by diffuse emission from the lower-density ambient gas, despite our best attempt in removing them (Section [3.2](#sec:analyses:characterize)). With these caveats in mind, we conclude that the measured sizes and gas velocity dispersion for the YMC candidates are consistent with them having high total masses of $\gtrsim10^5\,\mbox{$\rm M_\odot$}$.

## Escape Velocity

We estimate the escape velocity for all YMC candidates from their total masses and radii: $$\begin{align}
v_\mathrm{esc} = \sqrt{\frac{2 G (M_\mathrm{tot}/3.4)}{R_\mathrm{hl}}}~.
\label{eq:vesc}
\end{align}$$ The factor of 3.4 in the numerator accounts for the fraction of mass inside the FWHM of a 3D Gaussian (cite: Leroy_etal_2018), which is appropriate since we are using $R_\mathrm{hl}$ (i.e., the deconvolved source HWHM; see Section [3.2](#sec:analyses:characterize)) in the denominator.

We find escape velocities of $6{-}10\;\mbox{$\rm km~s^{-1}$}$ among all YMC candidates (Table [5](#tab:YMC_phys)). These estimates are uncertain by ${\sim}0.3$ dex due to systematic errors on the mass estimates; they may also be biased low if $R_\mathrm{hl}$ is overestimated at the current data resolution. Considering these factors, the true escape velocities are likely comparable to, if not larger than, the characteristic sound speed of photoionized gas ($\sim$10$\;\mbox{$\rm km~s^{-1}$}$). In this case, we expect photoionization feedback from massive stars to be not as effective in removing gas and stopping star formation in these dense structures as they would be in less dense structures (cite: Bressert_etal_2012). In addition, the estimated $v_\mathrm{esc}$ almost certainly exceed the previously estimated threshold of $\sim$1$\;\mbox{$\rm km~s^{-1}$}$ for effective gas ejection by protostellar outflows (cite: Matzner_Jumper_2015), in line with the notion that this particular feedback channel has limited impact on cluster formation (cite: Nakamura_Li_2014). These arguments imply relatively high star formation efficiency during the birth of these YMCs and the need for other feedback mechanisms to remove the remaining gas (cite: Levy_etal_2021; Menon_etal_2023; Polak_etal_2023).

|  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | $R_\mathrm{hl}$ | $M_\mathrm{gas,\,350}$ | $M_\mathrm{gas,\,HCN}$ | $M_\mathrm{\star,\,93}$ | $M_\mathrm{\star,\,HST}$ | $f_\mathrm{gas}$ | $M_\mathrm{tot}$ | $M_\mathrm{vir}$ | $v_\mathrm{esc}$ | $t_\mathrm{ff}$ | $\Sigma_\mathrm{gas}$ |  |
|  | \[pc\] | $\log\,[\mbox{$\rm M_\odot$}]$ | $\log\,[\mbox{$\rm M_\odot$}]$ | $\log\,[\mbox{$\rm M_\odot$}]$ | $\log\,[\mbox{$\rm M_\odot$}]$ |  | $\log\,[\mbox{$\rm M_\odot$}]$ | $\log\,[\mbox{$\rm M_\odot$}]$ | \[km/s\] | \[Myr\] | $[\mbox{$\rm M_\odot~pc^{-2}$}]$ |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) | \(9\) | \(10\) | \(11\) | \(12\) |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| 1$^*$ | $<$$4.3$ | $<$$4.3$ | $\cdots$ | $4.4$ | $\cdots$ | $<$$0.40$ | $4.4$–$4.7$ | $\cdots$ | $>$$4.0$ | $<$$1.7$ | $<$$240$ |  |
| 2 | $2.9$ | $<$$4.3$ | $4.7$ | $4.6$ | $4.7$ | $<$$0.32$ | $4.6$–$4.8$ | $5.2$ | $5.8$–$7.0$ | $0.64$–$0.78$ | $<$$240$ |  |
| 3 | $2.9$ | $4.8$ | $4.9$ | $4.4$ | $\cdots$ | $0.73$ | $5.0$ | $5.3$ | $8.9$ | $0.51$ | $1710$ |  |
| 4$^*$ | $<$$3.3$ | $<$$4.3$ | $\cdots$ | $4.3$ | $\cdots$ | $<$$0.46$ | $4.3$–$4.6$ | $\cdots$ | $>$$4.0$ | $<$$1.3$ | $<$$240$ |  |
| 5 | $6.6$ | $5.0$ | $<$$5.1$ | $4.6$ | $\cdots$ | $0.70$ | $5.2$ | $\cdots$ | $7.4$ | $1.4$ | $510$ |  |
| 6 | $5.4$ | $5.0$ | $5.4$ | $5.0$ | $5.6$ | $0.51$ | $5.3$ | $6.0$ | $9.7$ | $0.86$ | $760$ |  |
| 7 | $4.1$ | $4.8$ | $5.1$ | $5.0$ | $5.6$ | $0.41$ | $5.2$ | $5.4$ | $10.4$ | $0.60$ | $940$ |  |
| 8 | $<$$4.6$ | $<$$4.3$ | $4.8$ | $4.5$ | $5.3$ | $<$$0.40$ | $4.5$–$4.7$ | $<$$5.3$ | $>$$4.0$ | $<$$1.8$ | $<$$250$ |  |
| 9 | $4.1$ | $4.7$ | $5.0$ | $<$$4.4$ | $\cdots$ | $>$$0.69$ | $4.7$–$4.9$ | $5.6$ | $5.7$–$6.9$ | $0.92$–$1.1$ | $690$ |  |
| 10 | $2.6$ | $4.6$ | $<$$4.7$ | $<$$4.4$ | $\cdots$ | $>$$0.64$ | $4.6$–$4.8$ | $\cdots$ | $6.6$–$8.2$ | $0.48$–$0.60$ | $1480$ |  |
| 11 | $4.0$ | $4.8$ | $<$$4.8$ | $<$$4.4$ | $\cdots$ | $>$$0.70$ | $4.8$–$4.9$ | $\cdots$ | $6.1$–$7.2$ | $0.85$–$1.0$ | $800$ |  |
| 12 | $6.2$ | $5.2$ | $5.2$ | $4.4$ | $\cdots$ | $0.85$ | $5.2$ | $5.7$ | $8.4$ | $1.1$ | $850$ |  |
| 13$^*$ | $<$$4.5$ | $<$$4.3$ | $\cdots$ | $4.5$ | $\cdots$ | $<$$0.40$ | $4.5$–$4.7$ | $\cdots$ | $>$$4.1$ | $<$$1.7$ | $<$$260$ |  |
| 14 | $3.3$ | $4.5$ | $<$$4.8$ | $4.6$ | $\cdots$ | $0.45$ | $4.9$ | $\cdots$ | $7.5$ | $0.68$ | $670$ |  |
| 15 | $7.6$ | $5.2$ | $5.3$ | $5.0$ | $\cdots$ | $0.61$ | $5.5$ | $5.6$ | $9.8$ | $1.2$ | $670$ |  |
| 16$^*$ | $<$$3.4$ | $<$$4.3$ | $\cdots$ | $4.3$ | $\cdots$ | $<$$0.51$ | $4.3$–$4.6$ | $\cdots$ | $>$$3.8$ | $<$$1.4$ | $<$$270$ |  |
| 17 | $4.2$ | $<$$4.3$ | $5.0$ | $4.8$ | $5.3$ | $<$$0.24$ | $4.8$–$4.9$ | $5.6$ | $6.0$–$7.0$ | $0.94$–$1.1$ | $<$$260$ |  |
| 18 | $5.3$ | $4.9$ | $<$$4.9$ | $5.1$ | $5.4$ | $0.41$ | $5.3$ | $\cdots$ | $9.6$ | $0.84$ | $630$ |  |

: Physical Properties of the ALMA YMC Candidates

Table notes: (2) half-light radius (or upper limit in case of unsuccessful beam deconvolution; §[4.3](#sec:results:size)); (3) gas mass based on 350 GHz continuum detections and upper limits (§[4.1](#sec:results:Mgas)); (4) gas mass based on $\mathrm{HCN}\,(1\text{--}0)$ line detections and upper limits (§[3.2](#sec:analyses:characterize), §[4.1](#sec:results:Mgas)); (5) stellar mass based on 93 GHz continuum detections and upper limits (§[4.2](#sec:results:Mstar)); (6) stellar mass from UV–optical SED fitting for sources with cross-matched HST clusters (§[3.3](#sec:analyses:crossmatch)); (7) gas mass fraction (or upper/lower limit for non-detection at 350/93 GHz; §[4.4](#sec:results:Mtot_fgas)); (8) total mass (or 5$\sigma$ range for non-detection in either band; §[4.4](#sec:results:Mtot_fgas)); (9) virial mass (for those with measured gas velocity dispersion, §[4.5](#sec:results:Mvir)); (10) escape velocity (or 5$\sigma$ range / lower limit according to columns 2 & 8; §[4.6](#sec:results:Vesc)); (11) free-fall time (or 5$\sigma$ range / upper limit according to columns 2 & 8; §[4.7](#sec:results:rho_tff)); (12) gas surface density (or upper limit based on 350 GHz continuum sensitivity, §[4.8](#sec:results:Sigmagas)). We note that most quantities reported here have large systematic uncertainties. The YMC radii are likely affected by finite data resolution (§[4.3](#sec:results:size)); the gas and stellar mass estimates have ${\sim}0.5$ dex systematic error from the assumptions involved in their derivations (§[4.1](#sec:results:Mgas)–[4.2](#sec:results:Mstar)); other columns are also affected by the propagation of these uncertainties (§[4.4](#sec:results:Mtot_fgas)–[4.8](#sec:results:Sigmagas)). $^{*}$ These four sources are detected only in 93 GHz continuum. They may be supernova remnants with strong synchrotron emission rather than YMCs (see §[5.1](#sec:discuss:nature)), in which case the $M_{\star,\,93}$ values and subsequent calculations would not be reliable.

## Volume Density & Free-fall Time

We also derive the volume density and gravitational free-fall time from the YMC total masses and radii: $$\begin{align}
\rho_\mathrm{tot} &= \frac{M_\mathrm{tot}/3.4}{\frac{4}{3} \pi R_\mathrm{hl}^3}~, \label{eq:rho}\\
t_\mathrm{ff} &= \sqrt{\frac{3\pi}{32 G \rho_\mathrm{tot}}}~. \label{eq:tff}
\end{align}$$ We similarly include a factor of 3.4 in Equation [\[eq:rho\]](#eq:rho) as in Equation [\[eq:vesc\]](#eq:vesc). That is, we are calculating the mean mass volume density within a sphere defined by the (deconvolved) FWHM of each source, and then the free-fall time corresponding to that volume density.

We find volume densities of $50{-}200\,\mbox{$\rm M_\odot~pc^{-3}$}$, which is equivalent to hydrogen nuclei number densities of $1.5{-}6\times10^3\,\mathrm{cm^{-3}}$. The corresponding free-fall times are $0.5{-}1$ Myr (Table [5](#tab:YMC_phys)), with ${\sim}0.3$ dex of systematic uncertainty coming from the mass estimates and a potential bias towards larger values due to marginally resolved sizes (see Section [4.3](#sec:results:size)). Given that the YMC formation process can last a couple of free-fall times (cite: Skinner_Ostriker_2015), it is possible that these YMCs are still forming and possess a substantial gas reservoir at ages of $\sim$3 Myr (also see related discussions in Sections [4.6](#sec:results:Vesc)–[4.8](#sec:results:Sigmagas)). Moreover, the short free-fall time relative to the typical supernova explosion delay time ($\gtrsim$3 Myr) means that the initial gravitational collapse may be too fast for supernova feedback to play a role (cite: Fall_etal_2010). This inference again supports fairly high star formation efficiencies when forming these dense YMCs.

## Gas Surface Density

We calculate the gas surface density near the center of each YMC candidate via: $$\begin{align}
\Sigma_\mathrm{gas} = \frac{M_\mathrm{gas}}{A_\mathrm{eff}} = \frac{M_\mathrm{gas}}{\pi R_\mathrm{hl}^2/\ln{2}}~.
\label{eq:Sigmagas}
\end{align}$$ Here $A_\mathrm{eff}=2\pi\sigma_\mathrm{xy}^2=\pi R_\mathrm{hl}^2/\ln{2}$ is the effective area of the 2D Gaussian fit for each detected YMC in 350 GHz (Section [3.2](#sec:analyses:characterize)). The second equality follows from the conversion between the Gaussian HWHM (i.e., $R_\mathrm{hl}$) and dispersion: $\sigma_\mathrm{xy}=R_\mathrm{hl}/\sqrt{2\ln{2}}$.

We find gas surface densities of $500{-}2000\,\mbox{$\rm M_\odot~pc^{-2}$}$ for the YMC candidates with 350 GHz continuum detections (Table [5](#tab:YMC_phys)), with a ${\sim}0.5$ dex systematic uncertainty associated with $M_\mathrm{gas}$ and a potential bias towards lower values due to possibly overestimated sizes at current data resolution. The estimated as surface densities are much higher than typical values of giant molecular clouds (cite: Heyer_Dame_2015; Rosolowsky_etal_2021; Sun_etal_2022) and also higher than the median value for dense clumps in the Milky Way (cite: Urquhart_etal_2018). However, they are close to surface density thresholds above which one expects high star formation efficiency, as shown by analytical and numerical studies (cite: Fall_etal_2010; KimJG_etal_2018; Menon_etal_2023).

The gas surface density can play a key role in regulating the star formation efficiency because it determines the effectiveness of various forms of feedback in destroying the natal molecular clouds (cite: Chevance_etal_2022a). In particular, radiation pressure is believed to be the most important feedback process at high surface densities. For direct (UV) radiation pressure, one can derive an Eddington ratio, or the ratio of radiation pressure force to gravitational force, from the gas surface density and gas mass fraction $$\begin{align}
f_\mathrm{Edd} \approx \frac{4\Psi\,(1-f_\mathrm{gas})}{3\pi G c\,\Sigma_\mathrm{gas}\,(4-3f_\mathrm{gas})}~,
\label{eq:fEdd}
\end{align}$$ where $\Psi\approx10^3\,L_\odot/M_\odot$ is the light-to-mass ratio of a central stellar population with a Kroupa IMF and an age of ${\lesssim}\,3$ Myr (based on a Starburst99 simulation). The above is derived for a uniform gas sphere with a central star cluster, but other spatial distributions give similar results (cite: Raskutti_etal_2017; Reissl_etal_2018; Krumholz_etal_2019). From this equation, we estimate $f_\mathrm{Edd}\sim0.2{-}0.7$ for the YMC candidates with associated gas, which implies that their direct radiation pressure may not (yet) be enough to expel the gas (cite: Thompson_Krumholz_2016; Raskutti_etal_2016; Raskutti_etal_2017).

Furthermore, at $\Sigma_\mathrm{gas}\gtrsim10^3\,\mbox{$\rm M_\odot~pc^{-2}$}$, the star formation efficiency is expected to exceed $50\%$ when limited only by direct FUV radiation pressure on dust in combination with the rocket effect and photoevaporation from EUV (cite: KimJG_etal_2018; HeCC_etal_2019). Stellar winds, since they have a similar momentum flux to that from radiation, would not significantly change the expected star formation efficiency (cite: Lancaster_etal_2021; Polak_etal_2023). Unless the mass function is top-heavy or the dust abundance is enhanced, reprocessed infrared radiation has $f_\mathrm{Edd} = \kappa_\mathrm{IR} \Psi/(4 \pi G c) < 1$ and therefore does not aid in limiting star formation either (cite: Skinner_Ostriker_2015; Menon_etal_2022). To conclude, the high gas surface densities found for many of our YMC candidates suggest that the remaining gas may continue to feed star formation, leading to an overall high star formation efficiency.

Other than the implications on feedback and star formation efficiency, the measured gas surface densities also imply $V$-band extinctions of $\sim$30–110 mag (cite: Draine_2011), or $\sim$15–55 mag if half of the gas is in front of the stellar body. Such high extinction helps explain the lack of optical (or even IR) counterparts for many of our ALMA sources, as was found for YMCs in other systems (cite: Leroy_etal_2018; He_etal_2022).

# Discussion

In Section [4](#sec:results), we report the measured physical properties for the 18 YMC candidates identified from our new ALMA data and complemented by JWST and HST data. Our measurements suggest that most of these objects are massive, compact, in the early phase of formation, and likely associated with high star formation efficiency. Here we build on the quantitative results and address a few key remaining questions: (1) What do the rich multiwavelength measurements tell us about the nature and evolutionary stages of the YMC candidates? (2) How do the ALMA-identified YMCs relate to the exposed, more evolved clusters? (3) How do the YMCs fit in the large-scale context of the central starburst ring in NGC 3351?

## Nature and Evolutionary Stages of the ALMA-identified YMC Candidates

Based on the multiwavelength observational properties of the 18 ALMA sources and their cross-matching results with the JWST and HST data, we can classify most of them into four categories. These categories are inspired by the classification schemes for star clusters introduced in (cite: Johnson_2005) and (cite: Whitmore_etal_2014) as well as a similar scheme for molecular clouds used in (cite: Kawamura_etal_2009).

1.  *Type 1: Starless Clumps (#9, #10, #11).* These objects have substantial gas reservoirs indicated by thermal dust emission at 350 GHz, yet they show no signs of star formation through UV–optical stellar photospheric emission or 93 GHz free-free emission from H II regions. They are likely dense gas clumps on their way to becoming YMCs, representing the earliest phase of YMC formation.

2.  *Type 2: Clump–H II region complexes (#3, #5, #12):* These objects have both gas reservoirs producing dust emission at 350 GHz and associated H II regions producing free-free emission at 93 GHz, but the stellar content remains largely invisible in UV-to-IR bands due to high extinction. They represent the deeply embedded phase of YMC formation, when a substantial stellar body (including massive stars) has formed but the gas reservoir is neither expelled nor exhausted.

3.  *Type 3: Clump–H II region–cluster complexes (#6, #7, #14, #15, #18):* These objects are detected simultaneously in 350 GHz dust emission, 93 GHz free-free emission, as well as PAH and stellar photospheric emission in the near- to mid-IR; three out of five are also visible in optical bands. These are exposed but still forming clusters as they still have ample gas left and H II regions glowing around massive stars.

4.  *Type 4: Exposed H II region–cluster complexes (#2, #8, #17):* These objects no longer have detectable 350 GHz emission, suggesting that much of the local gas reservoir has been expelled or exhausted. They are still visible in both 93 GHz free-free emission and UV-to-IR stellar photospheric emission. These are emerging young clusters that have stopped forming and likely survived the violent gas expulsion process near the end of their formation process.

There are four ALMA sources (#1, #4, #13, and #16) that do not belong in any of the above categories. They are visible at 93 GHz but almost completely missing in all other wavelengths. Considering the stringent upper limits we can put on the gas surface density based on non-detections of the 350 GHz continuum, the $\mathrm{HCN}\,(1\text{--}0)$ line, and even the $\mathrm{CO}\,(3\text{--}2)$ line (see Appendix [7](#apdx:spectra)), these objects cannot be deeply embedded and should be visible at least in the near-IR if they are indeed forming YMCs with H II regions glowing intensely in free-free emission.

One possible explanation is that these 93 GHz-only sources are not forming YMCs, but rather supernovae remnants (SNRs) with their 93 GHz emission dominated by synchrotron radiation. As mentioned in Section [4.2](#sec:results:Mstar), previous 1.4 GHz MERLIN observations (cite: Hagele_etal_2010) put an upper limit of $0.3\;\mbox{$\rm mJy$}$ for any source more compact than the $\sim$10 pc MERLIN beam. Combining this constraint at 1.4 GHz with the measured 93 GHz flux density of $0.03{-}0.04\;\mbox{$\rm mJy$}$ for the four ALMA sources in qustion, the implied radio spectral index is ${\gtrsim-}0.5$. This is consistent with a synchrotron spectrum that turns over at an intermediate frequency due to synchrotron self-absorption, which is very probable given the small sizes and strong magnetic field of SNRs (e.g., see (cite: Lenc_Tingay_2009) for spectra of SNRs in NGC 4945 with turnover frequencies of ${\sim}5$ GHz). Furthermore, (cite: Hagele_etal_2010) showed that a SNR at their detection threshold of $0.3\;\mbox{$\rm mJy$}$ is expected to have a diameter of $\sim$2 pc. SNRs slightly fainter and larger in size would remain undetected in the MERLIN observations, while they can be detected but unresolved in our ALMA observations, just like the four 93 GHz-only sources. We thus suggest that these sources may actually be SNRs with synchrontron emission dominating the 93 GHz continuum. Future observations with the Karl G. Jansky Very Large Array (VLA) at 3–30 GHz with matched resolution can help verify this hypothesis.

## YMCs versus Evolved Clusters

In the previous section, we classified YMCs into four categories, which likely correspond to four evolutionary stages in the cluster formation process. However, there is a fifth stage, i.e., evolved clusters without associated gas or H II regions, that has been omitted from the discussion above. This omission is obviously due to our target selection based on ALMA data – older clusters without 93 GHz free-free or 350 GHz dust emission should not be in our list of ALMA-identified sources to begin with. These older clusters can nonetheless be identified with the HST and JWST data; they are also of great interest as they represent the end products of the cluster formation process. Here, we explicitly connect the ALMA-identified YMCs to more evolved clusters included in the HST cluster catalog (Section [2.2](#sec:data:HST)) to fill in the last missing piece.

One important consideration for such cross-dataset comparison is the difference in data sensitivity, which maps into different mass sensitivity for cluster detection. The ALMA continuum observations were designed to probe forming YMCs down to $\sim10^{4.5}\,\mbox{$\rm M_\odot$}$ in both gas and stellar mass. The HST broad-band observations, in contrast, can detect exposed clusters with much lower masses (cite: Lee_etal_2022). In order to compare the cluster populations detectable by these datasets in a sensible way, we choose to focus on HST clusters above some matching mass threshold. Given the systematic uncertainties in the mass estimates from both sides, we use two thresholds to bracket a sensible range: one at $10^{4.5}\,\mbox{$\rm M_\odot$}$ to directly match the nominal sensitivity limit of the ALMA data, the other at $10^{5}\,\mbox{$\rm M_\odot$}$ to account for the median ${\sim}0.5$ dex offsets between the 93 GHz-based and UV–optical SED-based stellar mass estimates for the ALMA-HST cross-matched sources (see Table [5](#tab:YMC_phys)).

The HST cluster catalog includes in total 42 star clusters in the central region of NGC 3351 ($r_\mathrm{gal}$ $<$ 500 pc). The vast majority (37) of them have SED-based ages$\,<\,$10 Myr and are located between $r_\mathrm{gal}=200{-}400$ pc (Figure [9](#fig:young_old) right panel). The same $r_\mathrm{gal}$ range covers all 14 ALMA-identified YMCs (including the six ALMA-HST cross-matches and excluding the four sources that are possibly SNRs) and almost all gas structures associated with the starburst ring. Since the orbital period along this ring is also $\sim$10 Myr (cite: Rubin_etal_1975; Hagele_etal_2007; Leaman_etal_2019), we do not expect much radial migration for these $<$10 Myr clusters. We thus view these young HST clusters along the ring as either counterparts or direct descendants of the ALMA YMCs (modulo caveats with mass range matching).

From the number counts of ALMA YMCs and young HST clusters within the matched mass range, we can further infer the timescales of the various evolutionary stages during YMC formation (cite: Kawamura_etal_2009). Here we assume that (1) the SFR of the starburst ring does not change drastically over a 10 Myr timescale; (2) the combined ALMA+HST YMC sample is complete over the matched mass range up to an age of ${\sim}10$ Myr; and (3) there is no substantial loss of YMCs over this period. Under these assumptions, the number count of YMCs in each evolutionary stage should be proportional to the average duration of that stage. Furthermore, the combined sample of ALMA YMCs with observable signs of active star formation (i.e., Types 2–4 with free-free emission) plus HST clusters with age ${\leq}10$ Myr should span a full 10 Myr window from the onset of star formation. This latter inference provides a necessary reference timescale for converting the relative duration of all stages to absolute values in Myr unit.

We show our inferred evolutionary timeline of YMC formation in Figure [10](#fig:timeline). Depending on the mass range of HST clusters ($\geq$$10^{4.5}\,\mbox{$\rm M_\odot$}$ or $\geq$$10^{5}\,\mbox{$\rm M_\odot$}$) used as the reference sample, we find that the typical duration of the four stages (mapping to Types 1–4) are 1–1.7 Myr, 1–1.7 Myr, 1.8–2.8 Myr, and 1–1.7 Myr, respectively. That is, a starless clump lasts $\sim$1–2 Myr (or ${\sim}2\,t_\mathrm{ff}$) before forming the first massive stars capable of creating H II regions. From that point on, it takes $\sim$1–2 Myr for the star cluster to become visible in the near-IR and $\sim$2–3 Myr to become visible in the optical. The cold gas reservoir disappears over $\sim$3–4 Myr (or 4–6 $t_\mathrm{ff}$), and the associated H II region fades away in $\sim$4–6 Myr. Overall, these timescales agree well with previous observations and simulations of various types of star-forming regions giving birth to star clusters (cite: Whitmore_Zhang_2002; Tan_etal_2006; Reggiani_etal_2011; Whitmore_etal_2014; Whitmore_etal_2023; Skinner_Ostriker_2015; Grasha_etal_2018; Grasha_etal_2019; KimJG_etal_2018; KimJG_etal_2019; Hannon_etal_2019; Hannon_etal_2022; Kruijssen_etal_2019b; LiH_etal_2019; Chevance_etal_2020a; Grudic_etal_2021a; KimJY_etal_2021; KimJY_etal_2023).

We would like the emphasize that there are substantial uncertainties on the inferred timescales, such that they should be viewed as preliminary, order-of-magnitude estimates. For example, it is possible that some of the assumptions mentioned above are not appropriate for the starburst ring in NGC 3351. The 10 Myr orbital period of this system means that the SFR can fluctuate moderately on a similar timescale (see observational constraints by (cite: Calzetti_etal_2021); also see demonstrations of such behavior in simulations by (cite: Armillotta_etal_2019; Sormani_etal_2020; Moon_etal_2022)). Star clusters may also get destroyed within 10 Myr due to either violent gas removal at the end of their formation process or mass loss due to stellar evolution (cite: Krumholz_etal_2019). These concerns could be addressed, in theory, by choosing even younger HST clusters (e.g., ${<}5$ Myr) as the reference sample, but various sources of systematic effects on the cluster age estimates especially at ${\lesssim}10$ Myr (Section [2.2](#sec:data:HST)) would render such analysis unreliable in practice. On this front, follow-up studies probing more diverse environments (e.g., those with longer dynamical timescales) will be crucial to verify our results in different physical conditions and to improve the currently limited statistics.

The reliability of the inferred timeline is also fundamentally tied to the reliability of the HST cluster measurements themselves. As discussed in Section [2.2](#sec:data:HST), the revised SED fitting scheme presented in (cite: Thilker_etal_2024) reflects the latest and by-far the most systematic efforts in dealing with photometric degeneracies, but we expect follow-up studies to further refine the fitting results and address remaining issues (especially with the youngest clusters). For example, these goals can be achieved by employing HST H$\alpha$ narrowband and JWST IR data to complement the HST broadband photometry (e.g., K. Henny et al., in preparation). Additional narrowband Pa$\alpha$ imaging with JWST in Cycle 3 (PI: A Leroy) and/or radio continuum observations with ALMA and VLA in the future would also provide unique constraints to help pin down the ages.

## YMCs in Large-scale Context

After examining the plausible evolutionary phases and timescales of the ALMA YMCs, we now put their properties in the context of the large-scale environment, i.e., the central starburst ring in NGC 3351.

$\bullet$ *Star formation rate contributed by the YMCs:* The central region in NGC 3351 is long known to be intensely star-forming, with an estimated SFR surface density of $\sim$0.5–0.8$\;\mbox{$\rm M_\odot~yr^{-1}~kpc^{-2}$}$ and a total SFR of $\sim$0.2–0.5$\;\mbox{$\rm M_\odot~yr^{-1}$}$ (cite: Elmegreen_etal_1997; Planesas_etal_1997; Ma_etal_2018; Calzetti_etal_2021; Song_etal_2021). In such an extreme condition, the cluster formation efficiency is expected to be high, with 30–60% of stellar mass formed in clusters (cite: Goddard_etal_2010; Adamo_etal_2011; LiH_etal_2018; Mills_etal_2021; Grudic_etal_2022).

We can use the estimated masses and timescales for the ALMA-identified YMCs to estimate the fractional SFR contributed by these sources alone. The total stellar mass of all YMCs (excluding the four sources that are possibly SNRs) is $7\times10^5\,\mbox{$\rm M_\odot$}$, and the inferred duration of the 93 GHz-bright phase is 4–6 Myr (Section [5.2](#sec:discuss:timescale)). Dividing these two numbers gives us an instantaneous SFR of 0.1–0.2 $\mbox{$\rm M_\odot~yr^{-1}$}$, which is already $\sim$50% of the total SFR of the starburst ring. Such a high fraction is consistent with similar estimates for the central starburst regions in NGC 253 and NGC 4945 (cite: Leroy_etal_2018; Emig_etal_2020). Note that this simple calculation ignores the considerable gas mass associated with the YMCs, and a fraction of that gas may be converted into stars in the future. Nor does it include the contribution from less massive clusters below our detection threshold. Given these omissions, the actual fraction of stars formed in clusters may be even higher.

$\bullet$ *Testing ring star formation models with the YMCs:* Another noteworthy feature of NGC3351’s starburst ring is its clean orbital configuration at a favorable viewing angle (see Figure [11](#fig:azimuthal) left panel), which stands out among all systems whose YMC populations have been studied by ALMA so far. As an iconic bar-fed nuclear ring with unambiguous orbital streamlines, this system offers an opportunity to test existing models of star formation in similar systems.

There are at least two influential theoretical models of star-forming rings in the literature (cite: Boker_etal_2008). A first scenario, dubbed the “popcorn model”, considers star formation triggered by gravitational instability as gas accumulates on the ring and reaches a critical density (cite: Elmegreen_1994). As star formation happens stochastically across the system, there may not be any preferable locations along the ring or systematic azimuthal trends in the properties of the young star clusters.

A second scenario, namely the “pearls on a string model” (cite: Boker_etal_2008), suggests that star formation is mostly triggered near or slightly downstream from the contact points, where the gas inflow enters the ring. An alternative model proposed for the Galactic Central Molecular Zone (CMZ) argues that star formation should be triggered by gas tidal compression near the pericenters of the ring orbit (cite: Longmore_etal_2013). In either case, an evolutionary sequence is expected downstream from the triggering positions, with progressively older clusters further down the orbit.

As the YMCs identified in our ALMA observations probably have ages younger than the orbital period (see Section [5.2](#sec:discuss:timescale)), their distribution and azimuthal trends may be particularly helpful for differentiating the competing scenarios described above. We find that the ALMA YMCs appear to concentrate near the two contact points (Figure [11](#fig:azimuthal) left), though with a slight preference towards their upstream side. When examining trends with the deprojected azimuthal angle $\phi$ (Figure [11](#fig:azimuthal) right), we *do not* see a clear, coherent trend when considering all YMCs along the ring. There may be tentative evidence for a progression in YMC evolutionary stages from $\phi=-180^\circ$ to 0$^\circ$ (i.e., the Eastern side of the ring), with Type 1 sources located right at the Northern contact point and subsequent types further down the ring orbit; a similar trend could be argued for the YMC gas to stellar mass ratio. Nonetheless, these trends become less clear on the other (Western) side of the ring. There is no clear trend or preferential distribution in the HST clusters either.

A subset of our observational results, especially the concentration of YMCs near the contact points and the possible azimuthal trends, seems to favor the “pearls on a string” model. Notably, the apparent progression from Type 1 to Type 4 YMCs spans half of the ring orbit from the Northern to the Southern contact point, and our estimated 4–5 Myr timescale for such progression (Section [5.2](#sec:discuss:timescale)) does agree with the $\sim$5 Myr orbital time across half of the ring (cite: Leaman_etal_2019). Nonetheless, these trends are only based on a small number ($\sim$8) of ALMA YMCs and do not show up consistently across the entire ring or in the (more evolved) HST clusters.

We can partly make sense of the somewhat mixed results in light of recent numerical studies of star-forming rings. For example, (cite: Seo_Kim_2013) showed that the presence or absence of a cluster age sequence may depend on the total SFR of the ring. (cite: Sormani_etal_2020) found that the instantaneous distribution of clusters can vary substantially with time due to stochasticity of star formation along the ring, and that one may only see clear azimuthal age trends either through time-averaging or when focusing on the youngest clusters ($\leq$0.25 Myr in their system with $\sim$5 Myr orbital period). (cite: Moon_etal_2021; Moon_etal_2022) showed that local concentration of young clusters upstream from contact points can happen following a temporary, asymmetric boost of gas inflow rate. Such asymmetry and non-steadiness can naturally arise from clumpiness in bar-driven inflows as well as varying accretion efficiency onto the ring (cite: Sormani_Barnes_2019; Hatchfield_etal_2021). Together, these studies highlighted key aspects of star-forming rings that are not entirely captured by the simple “popcorn” or the “pearls on a string” models, but can help explain some of the observed behaviors in NGC 3351’s central ring and its YMC population.

We anticipate more sensitive observations in the future (including partially executed ALMA Cycle 9 observations) to improve the statistics especially for the youngest clusters and allow for more detailed comparisons with simulations. Studying a large sample of star-forming ring systems (with favorable viewing angles) will be critical for differentiating time-varying effects from persistent trends.

$\bullet$ *YMCs as potential drivers of large-scale gas outflows:* Central starburst rings are believed to be powerful drivers of multi-phase galactic winds and outflows (cite: Armillotta_etal_2019; Nguyen_Thompson_2022), and there are indications of such outflows from NGC 3351’s central ring from existing multiwavelength observations. By analyzing Chandra X-ray imaging data, (cite: Swartz_etal_2006) found evidence of hot gas expanding beyond the starburst ring and likely above the plane of the galaxy. This hot gas is estimated to contain thermal energy of ${\sim}f^{1/2}10^{54}\,$erg (here $f\gtrsim10^{-4}$ is the volume filling factor of the gas). A more recent study based on VLT/MUSE data (cite: Leaman_etal_2019) identified and modelled a stream of warm ionized gas outflow, with a radial velocity of ${\sim}70\,\mbox{$\rm km~s^{-1}$}$ and kinetic energy of ${\sim}6\times10^{52}\,$erg. Both studies highlighted a dust lane visible in optical images to the southeast of the ring (see Figure [1](#fig:wide_field) left panel, right outside the white box) and interpreted it as a gas shell confining the outflow. The new JWST/MIRI images (Figure [1](#fig:wide_field) right panel) clearly show that a similarly shaped gas shell exists on the opposite side, even though it is less obvious from the optical image. Therefore, gas outflow may be present on all sides of the ring and contain more kinetic energy than estimated before.

The YMCs studied in this work are likely too young to be the main energy source for driving these hot and warm gas outflows. With our inferred timeline of $\lesssim$4 Myr after birth, most of them have not produced many supernovae to heat the hot X-ray emitting gas; their arrival was also too late to accelerate the aforementioned gas shell to its current location (cite: Leaman_etal_2019). Besides, we do not see clear evidence of localized outflow around the YMCs in their molecular line spectra either (see Appendix [7](#apdx:spectra)), unlike those found for some of the YMCs in NGC 253 (cite: Levy_etal_2021).

Nonetheless, it is still interesting to compare the wind-driving capability of the YMCs to the multi-phase gas outflow seen at the moment. Our Starburst99 simulation suggests that the YMCs can together produce a mechanical luminosity of ${\sim}2\times10^{40}\;\mathrm{erg\;s^{-1}}$, or a total deposited mechanical energy of ${\sim}3\times10^{54}\,$erg over 4 Myr. A mere 2% energy retention factor (cite: KimCG_etal_2020; Sirressi_etal_2024) would be enough to power the ionized gas outflow reported by (cite: Leaman_etal_2019) and to heat the X-ray emitting gas studied by (cite: Swartz_etal_2006). These order-of-magnitude calculations suggest that the current population of YMCs will be more than capable of drive gas outflow at a similar level in the future. Therefore, the multi-phase gas outflow may get enhanced over the next $\sim$10 Myr and become closer to those seen in NGC 253 and NGC 4945 (cite: Westmoquette_etal_2011; Krieger_etal_2019; Bolatto_etal_2021).

# Conclusions

In this paper, we examine a population of embedded YMCs in the central $1{\times}1$ kpc region of the nearby galaxy NGC 3351. This system features a prominent central starburst ring fed by stellar bar-driven gas inflows from the outer disk (cite: Regan_etal_2006; Leaman_etal_2019). The proximity (cite: Anand_etal_2021), favorable viewing angle (cite: Lang_etal_2020), and clean orbital configuration of this system (Figure [1](#fig:wide_field) and [2](#fig:alma-zoom)) make it ideal for a multiwavelength YMC study in the full context of the large-scale host galaxy properties.

To this end, we acquire new ALMA data in Band 3 and 7 (project code 2021.1.00059.S; PI: J. Sun), targeting the 93 GHz and 350 GHz continua along with various molecular lines. The long-baseline observations ensure that the ALMA images reach similarly high resolution ($0.1\ensuremath{''}{-}0.2\ensuremath{''}$, equivalent to $5{-}10$ pc) as existing HST and JWST images (cite: Lee_etal_2022; Lee_etal_2023), while the shorter-baseline observations guarantee robust imaging by recovering emission on larger spatial scales. The jointly-imaged ALMA data are sensitive enough to detect thermal dust continuum and molecular line emission from the gas reservoir of individual forming YMCs, as well as free-free emission from H II regions created by the YMCs. By cross-matching ALMA sources with those in JWST and HST data, we probe the (often embedded) YMC stellar population, thereby achieving a complete, multiwavelength view of YMC formation.

Our joint analyses of the ALMA, HST, and JWST datasets yield the following key results:

1.  We find 18 bright, compact sources in the ALMA continuum images, with 15 detected at 93 GHz and 11 detected at 350 GHz (Figure [2](#fig:alma-zoom)). Subsequent source cross-matching shows that only 8 of them have potential counterparts in JWST images (Figure [4](#fig:jwst-zoom)) and 6 have counterparts in HST images (Figure [3](#fig:hst-zoom); also see Table [4](#tab:crossmatch)).

2.  Based on the ALMA continuum and molecular line measurements (Table [3](#tab:YMC_obs)), we estimate for all sources their half-light radii ($1{-}8$ pc), stellar masses ($0.2{-}1{\times}10^5\,\mbox{$\rm M_\odot$}$), gas masses ($0.3{-}2{\times}10^5\,\mbox{$\rm M_\odot$}$), and gas velocity dispersion ($8{-}16\;\mbox{$\rm km~s^{-1}$}$). These estimates are comparable to typical values found for YMCs in the Milky Way and in other systems.

3.  The estimated size, mass, and velocity dispersion also imply high total mass (${\gtrsim}10^5\,\mbox{$\rm M_\odot$}$), a wide range of gas fractions (from ${\lesssim}25\%$ to ${\gtrsim}70\%$), large escape velocity ($6{-}10\;\mbox{$\rm km~s^{-1}$}$), short free-fall time ($0.5{-}1\;$Myr), and high gas surface density ($500{-}2000\;\mbox{$\rm M_\odot~pc^{-2}$}$), as summarized in Table [5](#tab:YMC_phys). The last three quantities suggest that various forms of feedback (photoionization, supernova, and radiation pressure) may be less effective in regulating star formation for sources with such extreme conditions (see Sections [4.6](#sec:results:Vesc)–[4.8](#sec:results:Sigmagas)).

4.  The multiwavelength properties of these ALMA-identified sources motivate a classification scheme in which most of them belong to one of the following categories: starless clumps ($N=3$), clump–H II region complexes (3), clump–H II region–cluster complexes (5), and exposed H II region–cluster complexes (3). These four categories likely represent four phases of YMC formation. The remaining 4 sources (detected only by ALMA at 93 GHz) are possibly supernova remnants with strong synchrotron emission rather than forming YMCs, though follow-up observations are necessary to verify this interpretation.

5.  Comparing the number counts of ALMA-identified YMCs versus young HST clusters in a matched mass range, we infer an evolutionary timeline for forming YMCs (Figure [10](#fig:timeline)). Modulo various sources of uncertainty, we estimate a duration of ${\sim}1{-}2$ Myr (or ${\sim}2$ free-fall times) for the starless clump phase. It then takes ${\sim}1{-}2$ Myr and ${\sim}2{-}3$ Myr for the newly formed cluster to become visible in the IR and optical bands, respectively. The cold gas reservoir disappears over ${\sim}3{-}4$ Myr (or $4{-}6$ free-fall times), and the H II region disappears over ${\sim}4{-}6$ Myr. These numbers represent our best constraints on YMC formation timeline in an extragalactic, starburst-like environment. They also agree quantitatively with previous estimates by observational and numerical studies of various types of cluster-forming environments.

6.  Putting the YMCs in the context of the entire central starburst region of NGC 3351, we find that the YMCs alone can account for at least 30–50% of the total SFR of the ring ($0.3{-}0.5\,\mbox{$\rm M_\odot~yr^{-1}$}$). While the YMCs exhibit an uneven azimuthal distribution and concentrate towards the two “contact points,” there is no consistent azimuthal trend in the inferred YMC evolutionary stages or other properties, as one may naively expect if YMC formation is only triggered by colliding flows near the “contact points.” Last but not least, the estimated total mechanical luminosity of the YMCs is large enough to power the previously reported multi-phase gas outflow from this system.

The quantitative measurements presented in this study will likely be improved in follow-up studies based on existing and/or future observations. For example, we plan to revisit the cluster selection and SED fitting by jointly analyzing the HST and JWST broad- and medium-band data shown in this work as well as archival HST narrow-band H$\alpha$ data (cite: Calzetti_etal_2021). The inclusion of deeper 93 GHz continuum observations with ALMA (partly executed in Cycle 9), lower frequency observations with VLA, or narrow-band imaging targeting IR recombination lines with JWST will certainly provide much better constraints on stellar age and extinction, eliminating a major source of uncertainty.

Beyond the YMCs, we also expect our rich ALMA dataset to support many other science goals. The deep, highly resolved $\mathrm{CO}\,(3\text{--}2)$ image makes it possible to characterize the complex, multi-scale gas structures present throughout NGC 3351’s central region. Detailed analysis of the gas kinematics may also shed light on the baryonic cycle across this system, from the large-scale gas inflow, to gas depletion and expulsion due to star formation and feedback, to the feeding (or lack thereof) of the central supermassive black hole.

We appreciate helpful discussions with Blake Ledger, Mark Krumholz, Sumit Sarbadhicary, and Todd Thompson.

JS acknowledges support by the National Aeronautics and Space Administration (NASA) through the NASA Hubble Fellowship grant HST-HF2-51544 awarded by the Space Telescope Science Institute (STScI), which is operated by the Association of Universities for Research in Astronomy, Inc., under contract NAS 5-26555. JS also acknowledges support by the Natural Sciences and Engineering Research Council of Canada (NSERC) \[funding reference number 568580\] through a CITA National Fellowship. The research of HH and CDW is supported by grants from NSERC and the Canada Research Chairs program. The research of KB is supported by a Mitacs Globalink Research Award. RCL acknowledges support for this work provided by the National Science Foundation (NSF) Astronomy and Astrophysics Postdoctoral Fellowship under award AST-2102625. The work of AKL is partially supported by the NSF under Grants No. 1615105, 1615109, and 1653300. ECO acknowledges support from grant 510940 from the Simons Foundation. MC gratefully acknowledges funding from the DFG through an Emmy Noether Research Group (grant number CH2137/1-1). COOL Research DAO is a Decentralized Autonomous Organization supporting research in astrophysics aimed at uncovering our cosmic origins. KG is supported by the Australian Research Council through the Discovery Early Career Researcher Award Fellowship (project number DE220100766) funded by the Australian Government. KG is supported by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. JDH gratefully acknowledges financial support from the Royal Society (University Research Fellowship; URF/R1/221620). MJJD and MQ acknowledge support from the Spanish grant PID2022-138560NB-I00, funded by MCIN/AEI/10.13039/501100011033/FEDER, EU. RSK acknowledges funding from the European Research Council in the ERC Synergy Grant ECOGAL (grant 855130), from the German Excellence Strategy in the Heidelberg Cluster of Excellence STRUCTURES (EXC-2181/1 - 390900948), and from the German Ministry for Economic Affairs and Climate Action in project MAINN (funding ID 50OO2206). MCS acknowledges financial support of the Royal Society (URF\R1\221118).

This paper makes use of the following ALMA data:\
ADS/JAO.ALMA#2013.1.00634.S,\
ADS/JAO.ALMA#2015.1.00956.S,\
ADS/JAO.ALMA#2021.1.00059.S,\
ADS/JAO.ALMA#2022.1.00159.S.\
ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of NSF operated under cooperative agreement by Associated Universities, Inc.

This paper uses observations made with the NASA/ESA Hubble Space Telescope (HST) and the NASA/ESA/CSA James Webb Space Telescope (JWST). The data were obtained from the Mikulski Archive for Space Telescopes at the STScI, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-26555 for HST and NAS 5-03127 for JWST. The JWST observations are associated with program 2017. All the HST and JWST data used in this paper are available at MAST: , , .

We acknowledge the usage of the SAO/NASA Astrophysics Data System.

# Facilities

ALMA, HST, JWST

# Software

`NumPy` (cite: NumPy_2020), `SciPy` (cite: SciPy_2020), `Matplotlib` (cite: Matplotlib_2007), `Astropy` (cite: Astropy_2013; Astropy_2018), `CASA` (cite: CASA_2022), `CARTA` (cite: CARTA_2.0.0), `APLpy` (cite: APLpy_2012), `adstex` (<https://github.com/yymao/adstex>).

# Molecular Line Spectra for the ALMA Continuum Sources

We show the molecular line spectra for the ALMA continuum sources in Figure [12](#fig:spectra).

natexlab

(ref: Adamo_etal_2011) Adamo, A., Östlin, G., & Zackrisson, E. 2011, MNRAS, 417, 1904

(ref: Anand_etal_2021) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2021, MNRAS, 501, 3621

(ref: Armillotta_etal_2019) Armillotta, L., Krumholz, M. R., Di Teodoro, E. M., & McClure-Griffiths, N. M. 2019, MNRAS, 490, 4401

(ref: Astropy_2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Astropy_2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Barnes_etal_2020a) Barnes, A. T., Kauffmann, J., Bigiel, F., et al. 2020, MNRAS, 497, 1972

(ref: Bendo_etal_2016) Bendo, G. J., Henkel, C., D’Cruze, M. J., et al. 2016, MNRAS, 463, 252

(ref: Bertin_Arnouts_1996) Bertin, E., & Arnouts, S. 1996, A&AS, 117, 393

(ref: Bertoldi_McKee_1992) Bertoldi, F., & McKee, C. F. 1992, ApJ, 395, 140

(ref: Boker_etal_2008) Böker, T., Falcón-Barroso, J., Schinnerer, E., Knapen, J. H., & Ryder, S. 2008, AJ, 135, 479

(ref: Bolatto_etal_2021) Bolatto, A. D., Leroy, A. K., Levy, R. C., et al. 2021, ApJ, 923, 83

(ref: Bradley_etal_2022) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2022, astropy/photutils: 1.5.0, Zenodo, v1.5.0, Zenodo, doi:10.5281/zenodo.6825092

(ref: Bressert_etal_2012) Bressert, E., Ginsburg, A., Bally, J., et al. 2012, ApJL, 758, L28

(ref: Callanan_etal_2021) Callanan, D., Longmore, S. N., Kruijssen, J. M. D., et al. 2021, MNRAS, 505, 4310

(ref: Calzetti_etal_2015) Calzetti, D., Lee, J. C., Sabbi, E., et al. 2015, AJ, 149, 51

(ref: Calzetti_etal_2021) Calzetti, D., Battisti, A. J., Shivaei, I., et al. 2021, ApJ, 913, 37

(ref: CASA_2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Chandar_etal_2017) Chandar, R., Fall, S. M., Whitmore, B. C., & Mulia, A. J. 2017, ApJ, 849, 128

(ref: Chandar_etal_2023a) Chandar, R., Caputo, M., Mok, A., et al. 2023, ApJ, 949, 116

(ref: Chevance_etal_2022a) Chevance, M., Krumholz, M. R., McLeod, A. F., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 1

(ref: Chevance_etal_2020a) Chevance, M., Kruijssen, J. M. D., Hygate, A. P. S., et al. 2020, MNRAS, 493, 2872

(ref: CARTA_2.0.0) Comrie, A., Wang, K.-S., Hsu, S.-C., et al. 2021, CARTA: The Cube Analysis and Rendering Tool for Astronomy, Zenodo, v2.0.0, Zenodo, doi:10.5281/zenodo.4905459

(ref: Costa_etal_2021) Costa, A. H., Johnson, K. E., Indebetouw, R., et al. 2021, ApJ, 918, 76

(ref: Draine_2011) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium, Princeton Series in Astrophysics (Princeton University Press)

(ref: Draine_etal_2007) Draine, B. T., Dale, D. A., Bendo, G., et al. 2007, ApJ, 663, 866

(ref: Elmegreen_1994) Elmegreen, B. G. 1994, ApJL, 425, L73

(ref: Elmegreen_etal_1997) Elmegreen, D. M., Chromey, F. R., Santos, M., & Marshall, D. 1997, AJ, 114, 1850

(ref: Emig_etal_2020) Emig, K. L., Bolatto, A. D., Leroy, A. K., et al. 2020, ApJ, 903, 50

(ref: Fall_etal_2010) Fall, S. M., Krumholz, M. R., & Matzner, C. D. 2010, ApJL, 710, L142

(ref: Finn_etal_2019) Finn, M. K., Johnson, K. E., Brogan, C. L., et al. 2019, ApJ, 874, 120

(ref: Gallagher_etal_2018a) Gallagher, M. J., Leroy, A. K., Bigiel, F., et al. 2018, ApJ, 858, 90

(ref: Gao_Solomon_2004) Gao, Y., & Solomon, P. M. 2004, ApJ, 606, 271

(ref: Garcia-Burillo_etal_2012) Garcı́a-Burillo, S., Usero, A., Alonso-Herrero, A., et al. 2012, A&A, 539, A8

(ref: Ginsburg_etal_2018) Ginsburg, A., Bally, J., Barnes, A., et al. 2018, ApJ, 853, 171

(ref: Goddard_etal_2010) Goddard, Q. E., Bastian, N., & Kennicutt, R. C. 2010, MNRAS, 405, 857

(ref: Grasha_etal_2018) Grasha, K., Calzetti, D., Bittle, L., et al. 2018, MNRAS, 481, 1016

(ref: Grasha_etal_2019) Grasha, K., Calzetti, D., Adamo, A., et al. 2019, MNRAS, 483, 4707

(ref: Grudic_etal_2022) Grudić, M. Y., Guszejnov, D., Offner, S. S. R., et al. 2022, MNRAS, 512, 216

(ref: Grudic_etal_2021a) Grudić, M. Y., Kruijssen, J. M. D., Faucher-Giguère, C.-A., et al. 2021, MNRAS, 506, 3239

(ref: Hagele_etal_2007) Hägele, G. F., Dı́az, Á. I., Cardaci, M. V., Terlevich, E., & Terlevich, R. 2007, MNRAS, 378, 163

(ref: Hagele_etal_2010) Hägele, G. F., Ascasibar, Y., Richards, A. M. S., et al. 2010, MNRAS, 406, 1675

(ref: Hannon_etal_2019) Hannon, S., Lee, J. C., Whitmore, B. C., et al. 2019, MNRAS, 490, 4648

(ref: Hannon_etal_2022) —. 2022, MNRAS, 512, 1294

(ref: Hannon_etal_2023) Hannon, S., Whitmore, B. C., Lee, J. C., et al. 2023, MNRAS, 526, 2991

(ref: NumPy_2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: Hassani_etal_2023) Hassani, H., Rosolowsky, E., Leroy, A. K., et al. 2023, ApJL, 944, L21

(ref: Hatchfield_etal_2021) Hatchfield, H. P., Sormani, M. C., Tress, R. G., et al. 2021, ApJ, 922, 79

(ref: HeCC_etal_2019) He, C.-C., Ricotti, M., & Geen, S. 2019, MNRAS, 489, 1880

(ref: He_etal_2022) He, H., Wilson, C., Brunetti, N., et al. 2022, ApJ, 928, 57

(ref: Henshaw_etal_2023) Henshaw, J. D., Barnes, A. T., Battersby, C., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 83

(ref: Heyer_Dame_2015) Heyer, M., & Dame, T. M. 2015, ARA&A, 53, 583

(ref: Heyer_etal_2001) Heyer, M. H., Carpenter, J. M., & Snell, R. L. 2001, ApJ, 551, 852

(ref: Matplotlib_2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90

(ref: Johnson_2005) Johnson, K. E. 2005, in Massive Star Birth: A Crossroads of Astrophysics, ed. R. Cesaroni, M. Felli, E. Churchwell, & M. Walmsley, Vol. 227, 413–422

(ref: Kawamura_etal_2009) Kawamura, A., Mizuno, Y., Minamidani, T., et al. 2009, ApJS, 184, 1

(ref: KimCG_etal_2020) Kim, C.-G., Ostriker, E. C., Somerville, R. S., et al. 2020, ApJ, 900, 61

(ref: KimJY_etal_2021) Kim, J., Chevance, M., Kruijssen, J. M. D., et al. 2021, MNRAS, 504, 487

(ref: KimJY_etal_2023) —. 2023, ApJL, 944, L20

(ref: KimJG_etal_2018) Kim, J.-G., Kim, W.-T., & Ostriker, E. C. 2018, ApJ, 859, 68

(ref: KimJG_etal_2019) —. 2019, ApJ, 883, 102

(ref: Kornei_McCrady_2009) Kornei, K. A., & McCrady, N. 2009, ApJ, 697, 1180

(ref: Krieger_etal_2019) Krieger, N., Bolatto, A. D., Walter, F., et al. 2019, ApJ, 881, 43

(ref: Kroupa_2001) Kroupa, P. 2001, MNRAS, 322, 231

(ref: Kruijssen_etal_2019b) Kruijssen, J. M. D., Schruba, A., Chevance, M., et al. 2019, Nature, 569, 519

(ref: Krumholz_etal_2019) Krumholz, M. R., McKee, C. F., & Bland-Hawthorn, J. 2019, ARA&A, 57, 227

(ref: Krumholz_etal_2014) Krumholz, M. R., Bate, M. R., Arce, H. G., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 243–266

(ref: Lancaster_etal_2021) Lancaster, L., Ostriker, E. C., Kim, J.-G., & Kim, C.-G. 2021, ApJL, 922, L3

(ref: Lang_etal_2020) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122

(ref: Leaman_etal_2019) Leaman, R., Fragkoudi, F., Querejeta, M., et al. 2019, MNRAS, 488, 3904

(ref: Lee_etal_2022) Lee, J. C., Whitmore, B. C., Thilker, D. A., et al. 2022, ApJS, 258, 10

(ref: Lee_etal_2023) Lee, J. C., Sandstrom, K. M., Leroy, A. K., et al. 2023, ApJL, 944, L17

(ref: Leitherer_etal_1999) Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999, ApJS, 123, 3

(ref: Lenc_Tingay_2009) Lenc, E., & Tingay, S. J. 2009, AJ, 137, 537

(ref: Leroy_etal_2018) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2018, ApJ, 869, 126

(ref: Leroy_etal_2021a) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021a, ApJS, 257, 43

(ref: Leroy_etal_2021b) Leroy, A. K., Hughes, A., Liu, D., et al. 2021b, ApJS, 255, 19

(ref: Levy_etal_2021) Levy, R. C., Bolatto, A. D., Leroy, A. K., et al. 2021, ApJ, 912, 4

(ref: Levy_etal_2022) —. 2022, ApJ, 935, 19

(ref: LiH_etal_2018) Li, H., Gnedin, O. Y., & Gnedin, N. Y. 2018, ApJ, 861, 107

(ref: LiH_etal_2019) Li, H., Vogelsberger, M., Marinacci, F., & Gnedin, O. Y. 2019, MNRAS, 487, 364

(ref: Longmore_etal_2013) Longmore, S. N., Kruijssen, J. M. D., Bally, J., et al. 2013, MNRAS, 433, L15

(ref: Longmore_etal_2014) Longmore, S. N., Kruijssen, J. M. D., Bastian, N., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 291–314

(ref: Ma_etal_2018) Ma, C., de Grijs, R., & Ho, L. C. 2018, ApJ, 857, 116

(ref: Madau_Dickinson_2014) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415

(ref: Maschmann_etal_2024) Maschmann, D., Lee, J., Thilker, D., et al. 2024, ApJ, submitted

(ref: Matzner_Jumper_2015) Matzner, C. D., & Jumper, P. H. 2015, ApJ, 815, 68

(ref: Menon_etal_2022) Menon, S. H., Federrath, C., & Krumholz, M. R. 2022, MNRAS, 517, 1313

(ref: Menon_etal_2023) —. 2023, MNRAS, 521, 5160

(ref: Mills_etal_2021) Mills, E. A. C., Gorski, M., Emig, K. L., et al. 2021, ApJ, 919, 105

(ref: Moon_etal_2021) Moon, S., Kim, W.-T., Kim, C.-G., & Ostriker, E. C. 2021, ApJ, 914, 9

(ref: Moon_etal_2022) —. 2022, ApJ, 925, 99

(ref: Nakamura_Li_2014) Nakamura, F., & Li, Z.-Y. 2014, ApJ, 783, 115

(ref: Nayak_etal_2019) Nayak, O., Meixner, M., Sewiło, M., et al. 2019, ApJ, 877, 135

(ref: Nguyen_Thompson_2022) Nguyen, D. D., & Thompson, T. A. 2022, ApJL, 935, L24

(ref: Ossenkopf_Henning_1994) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: Planesas_etal_1997) Planesas, P., Colina, L., & Perez-Olea, D. 1997, A&A, 325, 81

(ref: Polak_etal_2023) Polak, B., Mac Low, M.-M., Klessen, R. S., et al. 2023, arXiv e-prints, arXiv:2312.06509

(ref: PortegiesZwart_etal_2010) Portegies Zwart, S. F., McMillan, S. L. W., & Gieles, M. 2010, ARA&A, 48, 431

(ref: Raskutti_etal_2016) Raskutti, S., Ostriker, E. C., & Skinner, M. A. 2016, ApJ, 829, 130

(ref: Raskutti_etal_2017) —. 2017, ApJ, 850, 112

(ref: Regan_etal_2006) Regan, M. W., Thornley, M. D., Vogel, S. N., et al. 2006, ApJ, 652, 1112

(ref: Reggiani_etal_2011) Reggiani, M., Robberto, M., Da Rio, N., et al. 2011, A&A, 534, A83

(ref: Reissl_etal_2018) Reissl, S., Klessen, R. S., Mac Low, M.-M., & Pellegrini, E. W. 2018, A&A, 611, A70

(ref: APLpy_2012) Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python, Astrophysics Source Code Library, ascl:1208.017

(ref: Rodriguez_etal_2023) Rodrı́guez, M. J., Lee, J. C., Whitmore, B. C., et al. 2023, ApJL, 944, L26

(ref: Rosolowsky_etal_2021) Rosolowsky, E., Hughes, A., Leroy, A. K., et al. 2021, MNRAS, 502, 1218

(ref: Rubin_etal_1975) Rubin, V. C., Ford, W. K., J., & Peterson, C. J. 1975, ApJ, 199, 39

(ref: Ryon_etal_2017) Ryon, J. E., Gallagher, J. S., Smith, L. J., et al. 2017, ApJ, 841, 92

(ref: Schmiedeke_etal_2016) Schmiedeke, A., Schilke, P., Möller, T., et al. 2016, A&A, 588, A143

(ref: Seo_Kim_2013) Seo, W.-Y., & Kim, W.-T. 2013, ApJ, 769, 100

(ref: Shimajiri_etal_2017) Shimajiri, Y., André, P., Braine, J., et al. 2017, A&A, 604, A74

(ref: Sirressi_etal_2024) Sirressi, M., Adamo, A., Hayes, M., et al. 2024, arXiv e-prints, arXiv:2402.10270

(ref: Skinner_Ostriker_2015) Skinner, M. A., & Ostriker, E. C. 2015, ApJ, 809, 187

(ref: Song_etal_2021) Song, Y., Linden, S. T., Evans, A. S., et al. 2021, ApJ, 916, 73

(ref: Sormani_Barnes_2019) Sormani, M. C., & Barnes, A. T. 2019, MNRAS, 484, 1213

(ref: Sormani_etal_2020) Sormani, M. C., Tress, R. G., Glover, S. C. O., et al. 2020, MNRAS, 497, 5024

(ref: Stolte_etal_2014) Stolte, A., Hußmann, B., Morris, M. R., et al. 2014, ApJ, 789, 115

(ref: Sun_etal_2018) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860, 172

(ref: Sun_etal_2020a) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020, ApJL, 901, L8

(ref: Sun_etal_2022) Sun, J., Leroy, A. K., Rosolowsky, E., et al. 2022, AJ, 164, 43

(ref: Swartz_etal_2006) Swartz, D. A., Yukita, M., Tennant, A. F., Soria, R., & Ghosh, K. K. 2006, ApJ, 647, 1030

(ref: Tan_etal_2006) Tan, J. C., Krumholz, M. R., & McKee, C. F. 2006, ApJL, 641, L121

(ref: Thilker_etal_2024) Thilker, D., Lee, J., Whitmore, B., et al. 2024, ApJS, submitted

(ref: Thilker_etal_2022) Thilker, D. A., Whitmore, B. C., Lee, J. C., et al. 2022, MNRAS, 509, 4094

(ref: Thompson_Krumholz_2016) Thompson, T. A., & Krumholz, M. R. 2016, MNRAS, 455, 334

(ref: Turner_etal_2021) Turner, J. A., Dale, D. A., Lee, J. C., et al. 2021, MNRAS, 502, 1366

(ref: Turner_etal_2017) Turner, J. L., Consiglio, S. M., Beck, S. C., et al. 2017, ApJ, 846, 73

(ref: Urquhart_etal_2018) Urquhart, J. S., König, C., Giannetti, A., et al. 2018, MNRAS, 473, 1059

(ref: SciPy_2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: Westmoquette_etal_2011) Westmoquette, M. S., Smith, L. J., & Gallagher, J. S., I. 2011, MNRAS, 414, 3719

(ref: Whitmore_Zhang_2002) Whitmore, B. C., & Zhang, Q. 2002, AJ, 124, 1418

(ref: Whitmore_etal_2014) Whitmore, B. C., Brogan, C., Chandar, R., et al. 2014, ApJ, 795, 156

(ref: Whitmore_etal_2021) Whitmore, B. C., Lee, J. C., Chandar, R., et al. 2021, MNRAS, 506, 5294

(ref: Whitmore_etal_2023a) Whitmore, B. C., Chandar, R., Lee, J. C., et al. 2023a, MNRAS, 520, 63

(ref: Whitmore_etal_2023) Whitmore, B. C., Chandar, R., Rodrı́guez, M. J., et al. 2023b, ApJL, 944, L14

(ref: Williams_etal_2024) Williams, T., Lee, J., Larson, K., et al. 2024, ApJS, submitted

(ref: Williams_etal_2022) Williams, T. G., Kreckel, K., Belfiore, F., et al. 2022, MNRAS, 509, 1303

[^1]: The quoted beam sizes are the beam full width at half maximum (FWHM) throughout this paper.

[^2]: For clustered sources (#5, #6, #7 and #10, #11), we manually draw a bigger aperture that encircles all the clustered sources and ask `imfit` to perform a multi-component Gaussian fitting.

</paper>

Write the methods card for this paper.