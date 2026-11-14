# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...701A.141L\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...701A.141L",
 "title": "Sulfur oxides tracing streamers and shocks at low-mass protostellar disk─envelope interfaces",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Liu, X.-C.",
 "n_authors": 11,
 "arxiv_id": "2507.22870",
 "doi": "10.1051/0004-6361/202554186",
 "alma_projects_linked_by_archive": [
  "2013.1.00708.S",
  "2019.A.00034.S",
  "2022.1.01411.S",
  "2023.1.00592.S"
 ]
}
```

Paper text:
<paper>
# Sulfur oxides tracing streamers and shocks at low mass protostellar disk-envelope interfaces

Accretion shocks are thought to play a crucial role in the early stages of star and planet formation, but their direct observational evidence remains elusive, particularly regarding the molecular tracers of these processes. In this work, we searched for features of accretion shocks by observing the emission of SO and SO$_2$ using ALMA in Band 6 towards nearby Class I protostars. We analyze the SO and SO$_2$ emission from Oph IRS 63, DK Cha, and L1527, which have different disk inclination angles, ranging from nearly face-on to edge-on. SO emission is found to be concentrated in rings at the centrifugal barriers of the infalling envelopes. These rings are projected onto the plane of the sky as ellipses or parallel slabs, depending on the inclination angles. Spiral-like streamers with SO emission are also common, with warm ($T_{\rm ex} > 50$ K) and even hot ($T_{\rm ex} \gtrsim 100$ K) spots or segments of SO$_2$ observed near the centrifugal barriers. Inspired by these findings, we present a model that consistently explains the accretion shock traced by SO and SO$_2$, where the shock occurs primarily in two regions: (1) the centrifugal barriers, and (2) the surface of the disk-like inner envelope outside the centrifugal barrier. The outer envelope gains angular momentum through outflows, causing it to fall onto the midplane at or outside the centrifugal barrier, leading to a disk-like inner envelope that is pressure-confined by the accretion shock and moves in a rotating-and-infalling motion. We classify the streamers into two types—those in the midplane and those off the midplane. These streamers interact with the inner envelopes in different ways, resulting in different patterns of shocked regions. We suggest that the shock-related chemistry at the surfaces of the disk and the disk-like inner envelope warrants further special attention.

# Introduction

Protostars, the progenitors of the central stars in new solar systems, arise from the gravitational collapse of gas and dust in their natal clouds (cite: 1969MNRAS.145..271L; 1977ApJ...214..488S). Due to angular momentum, mass accretion leads to the development of a rotating, infalling envelope and a rotation-dominated disk (cite: 1976ApJ...210..377U; 1987ApJ...312..788A). One of the major questions is to what extent the chemical composition is preserved from cloud to disk (referred to as ‘inheritance’), or whether it is modified along the way (referred to as ‘modification’) (cite: 1999ApJ...519..705A; 2009A&A...495..881V; 2010A&A...519A..28V; 2014MNRAS.445..913D; 2023ApJ...956..120H). The strong similarity between interstellar and cometary ices suggests that at least some inheritance from the interstellar medium (ISM) occurs (cite: 2000A&A...353.1101B; 2004come.book..391B; 2011ARA&A..49..471M; 2019MNRAS.490...50D). At the same time, there is growing evidence that planetesimal formation begins early, even during the embedded phase of star formation (cite: 2010A&A...510A..72F; 2018A&A...618L...3M; 2020A&A...640A..19T). This process may preserve the original chemical composition by trapping molecules in large icy bodies that no longer participate in the chemistry on small dust grains (cite: 2016ApJ...823L..41M; 2016MNRAS.462S..99T; 2019A&A...621A..75E). A key uncertainty in this process, however, is whether most of the material undergoes a strong accretion shock before or as it enters the disk, which could potentially ‘reset’ the chemical composition.

The infall of material in the envelope can cause a shock when it collides with/around the disk, raising the temperatures of gas and dust to levels much higher than those produced by stellar photon heating alone (cite: 1983ApJ...264..485D; 1994ApJ...428..170N). However, to date, there is limited definitive observational evidence confirming the existence of strong accretion shocks. Typical shock tracers in the optical and infrared wavelengths (e.g., \[O I\] 6300 Å, \[S II\] 6731 Å, \[S I\] 25 $\mu$m, \[O I\] 63 $\mu$m, (cite: 2011A&A...527A..13P; 2019ApJ...870...76B; 2015ApJ...801..121N; 2016A&A...594A..59R)) are more sensitive to high-velocity shocks (10 km s$^{-1}$ or higher). These tracers are often contaminated by outflows and/or suffer from high extinction due to the surrounding envelope. Furthermore, outflows and jets are very common in protostars, even during the very early first hydrostatic core (FHSC) phase (cite: 2015A&A...577L...2G; 2020A&A...633A.126B), making it unclear whether or not they prevent the direct accretion of material onto the inner regions of the disks.

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:---|:--:|:--:|
| Mol. | Trans.$^{(b)}$ | Freq. | $S_{ij}\mu^2$ | $E_{\rm up}$ | ALMA Projects and targets$^{(c)}$ | Peak S/N$^{(d)}$ | Total flux$^{(f)}$ |
|  | $N_J$ ($J_{K_a,K_c}$) | GHz | ${\rm D}^2$ | K |  |  | mJy km s$^{-1}$ |
| SO | $5_5 - 4_4$ | 215.22065 | 11.5 | 44.1 | 2023.1.00592.S (L1527) | 20 | 1030$\pm$16 |
|  | $1_2-2_1$ | 236.45229 | 0.03 | 15.8 | 2022.1.01411.S (IRS 63, DK Cha) | – | – |
|  | $5_6-4_5$ | 251.82577 | 11.6 | 50.6 | 2022.1.01411.S (IRS 63, DK Cha) | 27, 26 | 6200$\pm$50, 6300$\pm$80 |
| SO$_2$ | $16_{3,13}-16_{2,14}$ | 214.68938 | 28.4 | 148 | 2023.1.00592.S (L1527) | 3 | 87$\pm$10 |
|  | $16_{1,15}-15_{2,14}$ | 236.21668 | 16.1 | 131 | 2022.1.01411.S (IRS 63, DK Cha) | 3, 3 | 105$\pm$11, 480$\pm$30 |
|  | $_{\ }12_{3,9}-12_{2,10}$ | 237.06887 | 18.4 | 93.9 | 2022.1.01411.S (IRS 63, DK Cha) | 3.5, 4 | 290$\pm$25, 590$\pm$35 |
|  | $15_{2,14}-15_{1,15}$ | 248.05740 | 14.1 | 119 | 2022.1.01411.S (IRS 63, DK Cha) | 2.5, 3 | 42$\pm$6, 510$\pm$32 |
|  | $13_{1,13}-12_{0,12}$ | 251.19967 | 25.7 | 82.2 | 2022.1.01411.S (IRS 63, DK Cha) | 7, 7 | 640$\pm$25, 1020$\pm$30 |
|  | $8_{3,5}-8_{2,6}$ | 251.21058 | 11.0 | 55.2 | 2022.1.01411.S (IRS 63, DK Cha) | 5, 4 | 600$\pm$23, 750$\pm$30 |

\

$^{(a)}$ The transition parameters are quoted from the JPL (cite: 1998JQSRT..60..883P) and CDMS (cite: 2016JMoSp.327...95E) database through Splatalogue .

The columns from the left to right list the names of molecules (Mol.), transition quantum numbers (Trans.), rest frequency (Freq.), line strengths ($S_{ij}\mu^2$), upper-level energies ($E_{\rm up}$) and some notes (Note). The unit of $S_{ij}\mu^2$ is Debye$^2$ (denoted as ${\rm D}^2$). Note that transitions of molecules that have been covered by the observations but were not used in this work are not listed. $^{(b)}$ For both the upper and lower levels, the transition labels for SO and SO$_2$ are $N_J$ and $J_{K_a,K_c}$, respectively.

$^{(c)}$ Only the targets relevant to this work are listed. IRS 63 represents Oph IRS 63. $^{(d)}$ The signal-to-noise ratios (S/Ns) are measured from spectra extracted at the emission peaks for the corresponding targets listed in the sixth column, under the native angular and spectral resolution, when cleaned with a *robust* parameter of 0.5. The S/Ns can be improved through smoothing. The symbol ‘–’ indicates non-detection. $^{(f)}$ The total fluxes and their uncertainties for the corresponding targets listed in the sixth column, obtained by applying Gaussian fitting to the integrated spectrum over the whole emission region.

Sulfur oxides (SO and SO$_2$) are commonly used as molecular tracers of shocks (cite: 1997ApJ...487L..93B; 2007ApJ...659..499L; 2022A&A...658A.104G; 2022ApJS..263...13L; 2024A&A...682A..78V). At typical shock speeds (ranging from several to $\sim10$ km s$^{-1}$) for impacting gas with densities greater than $10^7$ cm$^{-3}$, the molecules largely survive, but the gas temperatures just behind the shock can reach thousands of Kelvin, which can drive most of the oxygen into OH and H$_2$O (cite: 2009A&A...495..881V). This, in turn, leads to enhanced abundances of molecules like SO and SO$_2$ (cite: 1994ApJ...428..170N; 2017ApJ...839...47M; 2021A&A...653A.159V). SO and SO$_2$ produced by outflows are expected to exist on scales much larger than the disk size (cite: 2005A&A...437..149W; 2020ApJ...896...37F; 2021ApJ...912..148L), and it should be possible to distinguish these from molecular enhancements induced by accretion shocks. Sulfur-bearing molecules appear to be particularly promising as tracers of energetic processes at the disk-envelope interface (cite: 2014Natur.507...78S; 2021A&A...646A..72H; 2022A&A...658A.104G; 2024A&A...689L...7D).

Advanced interferometers, especially the Atacama Large Millimeter/submillimeter Array (ALMA), offer unprecedented opportunities to uncover systems of envelopes, disks, and outflows with exceptional spatial resolution, i.e., tens of AU (cite: 2012Natur.492...83T; 2015ApJ...808L...3A; 2016Natur.540..406B; 2019FrASS...6....3H; 2023ApJ...951....8O). This capability enables the detection of shock-related sulfur-bearing molecules around disks. (cite: 2014Natur.507...78S; 2017MNRAS.467L..76S) detected a parallel slab of SO toward L1527, an edge-on low-mass system, which shows a strong decreasing trend in the position-velocity map and interpreted it as shock tracers occurring around and inside the centrifugal barrier. At the inner radius of the SO ring of AB Aurigae, a Herbig Ae star with a nearly face-on protoplanetary disk, was found to trace gas located, in part, beyond the dust ring (cite: 2024A&A...689L...7D). The merging zone of the spiral structures and the disk of AB Aurigae may trigger gravitational instability, potentially leading to planet formation (cite: 2025ApJ...981L..30S). In addition to SO, strong SO$_2$ emission has also been detected on disk scales or in the infalling streamers of young protostars (cite: 2022A&A...667A..12V; 2022A&A...658A.104G; 2024A&A...682A..78V). These observations suggest that SO and SO$_2$ may be strongly linked to accretion shocks (cite: 2019A&A...626A..71A; 2022A&A...667A..20A). However, other studies have found that SO can also trace the volatile reservoir during the epoch of planet and comet formation (cite: 2023A&A...669A..53B; 2023NatAs...7..684K; 2024AJ....167..165B). The detailed origin of SO and its relation to SO$_2$ remain unclear. Furthermore, a unified model that explains the accretion shock at the interface between the envelope and the disk is still lacking.

Overall, high-resolution observations of the emission lines from both SO and SO$_2$ are crucial for assessing whether their emission can be attributed to accretion shocks and for investigating the details of how and where this process occurs. To address these issues, we carried out ALMA observations of SO and SO$_2$ towards several disk-hosting protostars with varying inclination angles. We examined the low-mass data for signatures of accretion shocks and sought to explain the observational results for shock tracers (especially SO and SO$_2$) in this study, as well as those in the literature, within the framework of a consistent model of disk-envelope interface. This work is structured as follows: The ALMA observations are described in Sect. [2](#sec_obs); the observational results and relevant analyses are presented in Sect. [3](#sec_obsresults); these data trigger the development of a new semi-analytic model to explain the observations, which is presented in Sect. [4](#sec_model); and the discussion and brief summary are presented in Sects. [5](#sec_discussion) and [6](#sec_summary), respectively.

# Observations and data

## Observations

### ALMA observational set up

The ALMA data analyzed in this paper are primarily from programs 2022.1.01411.S and 2023.1.00592.S (PI: M. L. van Gelder), which aim to search for signatures of accretion shocks in protostars. This study examines three nearby protostars (see Sect. [2.3](#sec_sample) for details) from the two projects. Both programs covered several transitions of SO and SO$_2$ in ALMA Band 6, but with different frequency setups (Table [\[tab_transitions\]](#tab_transitions)). The rest frequencies ($f_{\rm rest}$) of the lines targeted by program 2022.1.01411.S are within 233–252 GHz, while program 2023.1.00592.S targets lines within a slightly lower range of 215–232 GHz. The channel width is 0.141 MHz, corresponding to a velocity resolution of 0.17 km s$^{-1}$ at 250 GHz and 0.19 km s$^{-1}$ at 220 GHz. Each spectral window (SPW) has a bandwidth of 58.59 MHz (corresponding to $\sim$70 km s$^{-1}$ at 250 GHz). Note that the two SO$_2$ lines ($8_{3,5}-8_{2,6}$ and $13_{1,13}-12_{0,12}$) are separated by only $\sim$11 MHz ($\sim$13 km s$^{-1}$) and are therefore covered within the same SPW.

Two 12-m array configurations, C6 and C3, were employed for both programs. The maximum recoverable scales (MRS) are $\sim$2.5$''$ and $\sim$7$''$ for the C6 and C3 configurations, respectively. The data were pipeline-calibrated and imaged using the Common Astronomy Software Applications[^1] (cite: 2007ASPC..376..127M) version 6.4.1.12. To resolve disk-scale structures while maintaining sensitivity, we combined the 12-meter array data using Briggs weighting with a robust parameter of 0.5 — the default in CASA’s tclean task, as it offers an optimal balance between resolution and sensitivity. For L1527, to enhance the signal-to-noise ratio (S/N) of its large-scale SO emission associated with the outflow (Sect. [3.3](#sec_L1527)), we additionally applied *natural* weighting, which resulted in a lower noise level but poorer resolution. In CASA’s `tclean`, *Briggs* weighting with a *robust* parameter of 2 is effectively equivalent to natural weighting. The multiscale deconvolver was adopted with *auto-multithresh* masking, using `sidelobethreshold` of 2.0 and `noisethreshold` of 4.25. The Full Width at Half Maximum (FWHM) of the synthesized beams depends on the declination of the targets and the weighting schemes used during the cleaning process. It has values of $\sim 0.15\ensuremath{''}$–$0.2\ensuremath{''}$ for *robust* = 0.5 and $\sim 0.35\ensuremath{''}$ for *robust* = 2. The 1-$\sigma$ noise level at the native spectral resolution (0.141 MHz), when cleaned with a *robust* parameter of 0.5, is approximately 2.5 mJy beam$^{-1}$ and 2.0 mJy beam$^{-1}$ for programs 2022.1.01411.S and 2023.1.00592, respectively. A flux calibration uncertainty of 5% was assumed (cite: 2020AJ....160..270F). The main data used for this work are the ALMA observations of three young protostars (Oph IRS 63, DK Cha, and L1527) with different inclination angles (see details in Sect. [2.3](#sec_sample)). Note that an angular resolution of 0.15$''$ corresponds to a spatial resolution of approximately 23 au, 27 au, and 22 au for IRS 63, DK Cha, and L1527, respectively.

![](IRS63_colorimages.pdf)

![](IRS63_SO_mom12.pdf)

![](IRS63_pvmaps_ring_and_S.pdf)

![](IRS63_model_streamers.pdf)

![](IRS63_SO2_mom0.pdf)

### VLT MUSE

We utilized the VLT/MUSE data (PI: M. L. van Gelder) to study the outflow direction of DK Cha (Sect. [3.2](#sec_dkcha)). The Multi Unit Spectroscopic Explorer (cite: 2010SPIE.7735E..08B), is a panoramic integral-field spectrograph on the Very Large Telescope (VLT). The observations were conducted during the night of May 3rd, 2019, in the narrow field mode, with an angular resolution of $\sim 0.15\ensuremath{''}$ and a resolving power of $R\sim 2500$ at $\sim$7000 Å. The spectra cover an optical wavelength range of 4800$-$9300 Å. The data were reduced and calibrated using the ESO Reflex pipeline (cite: 2013A&A...559A..96F). Dithering and pipeline calibration were performed to improve the quality of the data.

## ALMA archival data

We utilize archival data of DK Cha from the ALMA program 2013.1.00708.S (PI: F. Ménard). CO (2-1) was observed in this program with a spectral resolution of $\sim 0.16$ km s$^{-1}$ and a synthesized beam resolution of $0.5\ensuremath{''} \times 0.25\ensuremath{''}$. The observations were conducted on August 27, 2015. We retrieved the spectral cube, processed and cleaned by CASA 5.6.1 as part of the Additional Representative Images for Legacy (cite: 2021PASP..133h5001M), from the ALMA archive for further analysis. The 1-$\sigma$ noise level at the spectral resolution of 0.16 km s$^{-1}$ is 35 mJy beam$^{-1}$.

We also utilize archival data of L1527 from ALMA program 2019.A.00034.S (PI: J. Tobin). CO (2-1) was observed in this program with a spectral resolution of $\sim 0.63$ km s$^{-1}$ and a synthesized beam resolution of $0.32\ensuremath{''} \times 0.21\ensuremath{''}$ (cite: 2023ApJ...951...10V). The observations were conducted on July 3, 2022. These data were used solely to determine the boundaries of CO outflows. The spectral cube from the pipeline products downloaded from the ALMA archive was used without additional processing. The 1-$\sigma$ noise level at a spectral resolution of 0.63 km s$^{-1}$ is 2.1 mJy beam$^{-1}$.

## Target protostars

The two ALMA programs (2022.1.01411.S and 2023.1.00592; Sect. [2.1.1](#sec_obssetup)) both targeted nearby low-mass protostars, but their samples do not overlap. Some observations of the proposed sources have not been fully completed. This work focuses on three of the sources, selected based on the following criteria: (1) the observations for these sources have been completed; (2) they show resolved signatures of SO and SO$_2$ emission; and (3) their disks have different inclination angles ($\theta_{\rm view}$). Table [\[tab_transitions\]](#tab_transitions) lists the ALMA projects and corresponding targets studied in this work. A brief overview of each target is provided below.

IRAS 16285–2355, commonly known as Oph IRS 63, is a Class I source. The observations are centered at RA (J2000) = 16$^{\rm h}$31$^{\rm m}$35.70$^{\rm s}$ and Dec (J2000) = $-24^{\rm d}$01$^{\rm m}$29.6$^{\rm s}$. Located in L1709 within the Ophiuchus star-forming region (cite: 2006AJ....131.2921R), it is at a distance of 132$\pm$6 pc (cite: 2020A&A...633A..51Z). Oph IRS 63 has a bolometric temperature ($T_{\rm bol}$) of 348 K and a bolometric luminosity ($L_{\rm bol}$) of 1.3 $L_\ensuremath{\odot}$ (cite: 2022ApJ...925...12S; 2023ApJ...951....8O). It is one of the brightest Class I protostars, younger than 500 000 years (cite: 2020Natur.586..228S). Multiple annular substructures have been found in the protoplanetary disk of Oph IRS 63, with a scale of $\sim$150 au and an inclination angle ($\theta_{\rm view}$) of $\sim$45$\ensuremath{^\circ}$ (cite: 2020Natur.586..228S). The SO emission from Oph IRS 63 shows a centrally depleted pattern, with a size comparable to that of the protoplanetary dust disk, surrounded by three spiral structures with a size of several hundred au (cite: 2023ApJ...958...98F). In the literature, the protostellar mass ($M_\star$) of Oph IRS 63 is typically estimated to be 0.5 $M_\odot$ (cite: 2007A&A...461.1037B; 2013A&A...559A..82B; 2023ApJ...958...98F).

|  |  |  |  |
|:--:|:--:|:--:|:--:|
| Structure | $\theta_0$ ($\ensuremath{^\circ}$) | $\phi_0$ ($\ensuremath{^\circ}$) | $R_{\rm C}$ |
| S1 | 50 | 130 | 1$\ensuremath{''}$ ($\sim 130$ au) |
| S2 | 80 | 200 | 0.6$\ensuremath{''}$ ($\sim 80$ au) |
| S3 | 125 | -63 | 0.6$\ensuremath{''}$ ($\sim 80$ au) |
| S4 | 80 | -10 | 0.6$\ensuremath{''}$ ($\sim 80$ au) |

: Model parameters of the streamers in Oph IRS 63 (Sect. [3.1](#sec_irs63)).

\

The radius of centrifugal barrier ($R_{\rm C}$) of the globally infalling envelope is adopted as $30\ensuremath{''}$ ($\sim$65 au), the length of the semi-major axis of the SO ring (Fig. [1](#fig_irs63_color_maps)).

IRAS 12496-7650, also known as DK Cha, is a Herbig Ae star and the most luminous IRAS source in the Chamaeleon II star-forming region, located at a distance of 178 pc (cite: 1997A&A...327.1194W). It is transitioning from Class I to Class II, with an accretion luminosity of 9 $L_\ensuremath{\odot}$, derived from hydrogen infrared lines (cite: 2011A&A...534A..99G; 2015A&A...575A..19R). Observations of its outflows (cite: 2015A&A...576A.109Y; 2023ApJ...945...63H) suggest that DK Cha is a nearly face-on system with a small inclination angle. However, no ALMA long-baseline observations[^2] with a resolution better than 0.1$\ensuremath{''}$ have been obtained, and its disk has not been resolved. Consequently, there remains some uncertainty regarding the inclination angle of its disk. The observations of DK Cha are centered at RA (J2000) = 12$^{\rm h}$53$^{\rm m}$17.07$^{\rm s}$, Dec (J2000) = $-$77$^{\rm d}$07$^{\rm m}$10.8$^{\rm s}$.

IRAS 04368+2557, also known as L1527, is a Class 0 low-mass protostar embedded in a protostellar core within the Taurus molecular cloud, located at a distance of 144 pc (cite: 2007ApJ...671.1813T; 2012Natur.492...83T). It features a nearly edge-on disk (cite: 2014Natur.507...78S; 2018ApJ...861...91H; 2023ApJ...951...10V; 2024ApJ...966..207Z). The central mass of L1527 was initially estimated to be $\sim 0.2$ $M_\ensuremath{\odot}$ (cite: 2012Natur.492...83T; 2016MNRAS.463.3563T), but recent observations suggest a value of $\sim 0.5$ $M_\ensuremath{\odot}$ (cite: 2023ApJ...951...10V). The SO emission from L1527 exhibits a structure resembling parallel slabs (cite: 2017MNRAS.467L..76S), which has been interpreted as a ring formed by the centrifugal barrier of infalling gas (cite: 2014Natur.507...78S; 2017MNRAS.467L..76S). The target center of L1527 is located at RA (J2000) = 04$^{\rm h}$39$^{\rm m}$53.87$^{\rm s}$ and DEC (J2000) = $+$26$^{\rm d}$03$^{\rm m}$09.5$^{\rm s}$.

# Streamers and accretion shock traced by SO/SO$_2$

## Oph IRS 63

In Oph IRS 63, a low-mass protostar, distinct signatures of accretion shocks have been observed, including ring-like structures and spiral-like streamers in the SO and SO$_2$ emission. These features provide compelling evidence for the presence of shocks at/around the disk-envelope interface during the early stages of star formation. To better understand these shock-related structures, we first examine the detailed morphology and kinematics of the SO emission, beginning with the ring-like component.

### SO ring

Among the two observed SO lines (Table [\[tab_transitions\]](#tab_transitions)), only SO ($5_6-4_5$) is detected in Oph IRS 63. SO ($5_6-4_5$) displays a ring-like structure with multiple spiral-like features (see panels (a) and (b) of Fig. [1](#fig_irs63_color_maps)). The morphology is similar to that revealed by (cite: 2023ApJ...958...98F) using the SO ($6_5-5_4$) emission at a resolution of 0.3–0.4$''$. Due to the higher resolution of this study ($\sim 0.2\ensuremath{''}$), we are able to observe the SO ring in greater detail and identify that the inner edge of the SO ring resembles an elliptical shape. The elliptical inner boundary of SO has a size comparable to that of the second (outer) dust ring of the protoplanetary disk, as revealed by (cite: 2020Natur.586..228S) using the ALMA long-baseline data (see also Fig. [1](#fig_irs63_color_maps)).

We fit the ring-like SO emission using an elliptical ring model, following the algorithm described in Appendix [7](#sec_fit_ring). The azimuthal angle of the major axis ($\phi_{\rm view}$) and the inclination angle ($\theta_{\rm view}$) are fitted to be $53\pm1^\circ$ and $40.5\pm1^\circ$, respectively. The fitted value of $\theta_{\rm view}$ is close to that reported by (cite: 2020Natur.586..228S) ($45^\circ$). The small discrepancy may result from deviations from a perfect elliptical shape, or from a possible misalignment between the disk and the SO ring. In this work, we define $\phi_{\rm view}=0$ for a structure whose major axis lies in the east-to-west direction, with $\phi_{\rm view}$ increasing as the major axis rotates counterclockwise. Note that in some studies, the position angle (PA) is defined starting from the north direction. During the follow-up fitting, we fixed $\theta_{\rm view}$ to 45$^\circ$.

The moment 1 map of SO (Fig. [2](#fig_irs63_SO_mom12)(a)) reveals an hourglass-shaped structure composed of blue- and redshifted components aligned along the major axis of the ring. In the moment 2 map (Fig. [2](#fig_irs63_SO_mom12)(b)), an S-shaped broad-line feature is apparent (see also Fig. [19](#fig_irs63_Smark) in Appendix [8](#sec_ectraimage)). This S-shaped structure corresponds to the southeast–northwest margin of the hourglass seen in the moment 1 map and exhibits a steeper velocity gradient than the southwest–northeast margin. The position–velocity (PV) diagram extracted along the S-shaped feature (panel (a) of Fig. [3](#fig_irs63_pvmaps_ringandS)) shows distinct velocity components, which we will discuss further in Sect. [5.2](#sec_beyonddis).

Here, we focus on analyzing the dynamics of the SO ring itself. We fit the velocity distribution along the ring (panel (a) of Fig. [2](#fig_irs63_SO_mom12)) assuming pure rotation, following Eqs. [\[eq_ellip_arclength\]](#eq_ellip_arclength) and [\[eq_ellip_vproj\]](#eq_ellip_vproj). The fitting results are shown in panel (b) of Fig. [3](#fig_irs63_pvmaps_ringandS). The rotational velocity ($V_{\rm rot}$) and systemic velocity ($V_{\rm sys}$) are fitted to be approximately 2.2 km s$^{-1}$ and 3 km s$^{-1}$, respectively. Assuming Keplerian rotation at a radius of 65 au, this corresponds to a central mass of $\sim 0.35\ M_\ensuremath{\odot}$, slightly smaller than the $\sim 0.5\ M_\ensuremath{\odot}$ reported in the literature (Sect. [2.3](#sec_sample)).

### SO spiral-like streamers of different types

While the ring-like SO structure reveals rotation at the disk-envelope interface (Sect. [3.1.1](#sec_irs63_ring_steamer)), additional substructures are present in the form of spiral-like extensions. We now turn to these features, which appear to trace dynamically distinct infalling motions. Four spiral-like structures, denoted as S1 to S4, are identified in the SO emission, with their feet located around the SO ring and their tails extending outward. Among these, S1 to S3 correspond to the three arms reported by (cite: 2023ApJ...958...98F), while the S4 structure was not resolved in their work due to slightly lower resolution and sensitivity. In the moment 0 map of SO ($5_6$–$4_5$) shown in Fig. [1](#fig_irs63_color_maps), the western tail and the foot of S4 exhibit an overall S/N exceeding 4, although the emission at the connection between them is weaker (S/N $\lesssim$ 3). Given the symmetric distribution of the four feet S1–S4 (Fig. [18](#fig:ringfit)), we consider the presence of S4 to be plausible.

To interpret the origin of the spiral structures, we model them as gas streamers undergoing ballistic free-fall toward the disk. Their three-dimensional trajectories are computed and then projected onto the plane of the sky, following the procedure outlined in Appendix [9](#sec_parabolic_trajectory). The free-falling gas, characterized by zero mechanical energy and non-zero specific angular momentum, follows a parabolic trajectory in 3D space. This trajectory is parameterized by the initial polar angle ($\theta_0$), azimuthal angle ($\phi_0$), and centrifugal radius ($R_{\rm C}$) within the disk coordinate system. For a free-fall stream with a given specific angular momentum $J$, the centrifugal radius $R_{\rm C}$ represents the radius of an equivalent circular orbit conserving the same angular momentum. Geometrically, $R_{\rm C}$ also corresponds to twice the distance between the focus and the vertex of the parabola. Streams originating from different directions are expected to intersect at or beyond $R_{\rm C}$, preventing material from freely falling all the way to the vertex of the parabolic path. Additionally, $R_{\rm C}$ equals the distance between the parabola’s focus and its directrix (see Sect. [4.1](#sec_cmu) for details). When projected onto a two-dimensional plane defined by viewing angles $\theta_{\rm view}$ and $\phi_{\rm view}$, the trajectory remains parabolic, although the central star may no longer lie exactly at the focus (see Sect. [4](#sec_model) and Appendix [9](#sec_parabolic_trajectory)).

To model the trajectories of the observed spiral-like features, we adopt a simplified, hand-drawn, illustrative approach aimed at qualitatively matching the observed morphology. As a first step, we assess whether the observed structures can be explained by free-fall streamers confined strictly to the disk midplane. According to Eq. [\[eq_phi_incre\]](#eq_phi_incre) in Appendix [10](#sec_eq_details), such midplane-confined streamers (corresponding to $\theta_0 = \pi/2$) can span an azimuthal angle on the plane of the sky ($\theta_{\rm proj}$) of less than $110^\circ$. However, some features—such as S1 in Fig. [1](#fig_irs63_color_maps)—have $\Delta \theta_{\rm proj} > 110^\circ$, indicating that their trajectories cannot be explained by midplane infall alone. Motivated by this, we fix the viewing angles $\theta_{\rm view}$ and $\phi_{\rm view}$ to match the inclination and azimuth of the SO ring (and thus the protoplanetary disk; (cite: 2020Natur.586..228S)), and manually adjust only the model parameters—$\theta_0$, $\phi_0$, and $R_{\rm C}$—to better reproduce the observed spiral shapes. The uncertainty of $\theta_0$ is approximately $10^\circ$.

We define the off-midplane angle as $\theta_0^{\rm off\,disk} = |90^\circ - \theta_0|$, which quantifies the deviation of a streamer’s initial direction from the disk midplane. In this convention, $\theta_0^{\rm off\,disk} = 0^\circ$ corresponds to a trajectory lying exactly in the midplane, while $\theta_0^{\rm off\,disk} = 90^\circ$ corresponds to infall along the polar axis. For S1 and S4, we find $\theta_0^{\rm off\,disk} \gtrsim 30^\circ$, whereas for S2, it is approximately $10^\circ$. The off-midplane angle for S4 is not well constrained; therefore, given the morphological similarity between S1 and S3, we adopt the $\theta_0^{\rm off\,disk}$ value of S3 for S4. The modeled trajectories are illustrated in Fig. [4](#fig_IRS63_model_streamers), and their parameters are summarized in Table [1](#tab_fourspiral_models).

The above fitting assumes a central stellar mass of 0.35 $M_\ensuremath{\odot}$ (Sect. [3.1.1](#sec_irs63_ring_steamer)). Even after accounting for projection effects, the modeled free-fall velocities are found to be slightly higher than the observed values. To reconcile this discrepancy, we manually scale down the free-fall velocities by a factor of approximately 1.5. This adjustment is justifiable, as the observed velocities correspond to line-center measurements rather than the full velocity span. As demonstrated by (cite: 2023ApJ...958...98F), central stellar masses derived from fitting the ridge versus the outer boundary of emission in position-velocity diagrams can differ by a factor of $\sim 3$. Furthermore, the free-fall assumption may not be strictly applicable to all streamers, particularly in cases where interactions with the inner envelope alter their dynamics (see Sects. [3.1.4](#sec_irs63_envelope) and [4.2.3](#sec_streamer_onoff)).

Based on these results, we classify the spiral-like structures as streamers, supported by several key considerations. First, their large off-midplane angles ($\theta_0^{\rm off\,disk}$) indicate significant deviation from the disk midplane. This distinguishes them from typical spiral arms, which are generally confined to the midplane and shaped primarily by disk or inner envelope dynamics (Sect. [4](#sec_model)). Second, two distinct SO emission spots are observed at the bases of S1 and S3—located near the endpoints of the SO ring’s major axis. These spots are clearly resolved in our data (Fig. [1](#fig_irs63_color_maps)) and may mark the locations where the associated off-midplane streamers appear to intersect the disk surface. Finally, all identified streamers originate from beyond the centrifugal radius (see Sect. [4.1](#sec_cmu) for the definition of centrifugal radius), where they likely interact with the rotating and infalling inner envelope (see Sect. [3.1.4](#sec_irs63_envelope) for the observational evidence of the inner envelope). These interactions may play an important dynamical role, producing localized heating and chemical enhancement where streamers impact the disk or envelope surface. In the next subsection, we explore such evidence by examining SO$_2$ emission associated with the base of one prominent streamer (Sect. [3.1.3](#sec_warmspot)).

To account for the diversity in observed morphologies and infall geometries, we further classify the streamers into two distinct types: in-midplane and off-midplane, corresponding to relatively small (e.g., $\lesssim 30^\circ$) and large (e.g., $\gtrsim 30^\circ$) values of $\theta_0^{\rm off\,disk}$, respectively. Additional evidence for both in-midplane and off-midplane streamers will be presented for other observational targets in Sect. [3.2](#sec_dkcha). Their differing interactions with the disk and envelope structures will be discussed in our modeling framework in Sect. [4](#sec_model).

![](IRS63_warmspot_spectra.pdf)

![](IRS63_pv.pdf)

### SO$_2$ ring and warm spot

All five SO$_2$ lines (Table [\[tab_transitions\]](#tab_transitions)) are detected toward Oph IRS 63 (Figs. [1](#fig_irs63_color_maps) and [5](#fig_irs63_3lines_so2)). Among these, the SO$_2$ ($8_{3,5} - 8_{2,6}$) transition has the lowest upper-level energy and the highest S/N. Its moment 0 map shows an S/N of approximately 6 (Fig. [1](#fig_irs63_color_maps)). The emission from SO$_2$ ($13_{1,13} - 12_{0,12}$) (Fig. [5](#fig_irs63_3lines_so2)) resembles that of SO$_2$ ($8_{3,5} - 8_{2,6}$) (right panel of Fig. [1](#fig_irs63_color_maps)), although with a slightly lower S/N of $\sim$5 in its moment 0 map. As with SO, the moment 0 maps of these two SO$_2$ lines reveal a ring-like structure (Figs. [1](#fig_irs63_color_maps) and [5](#fig_irs63_3lines_so2)). The SO$_2$ ring appears to be comparable in size to, or possibly slightly smaller than, the SO ring. However, due to the current resolution and sensitivity limits, we cannot definitively distinguish between the SO and SO$_2$ rings. We therefore refer to them collectively as the sulfur-oxide rings of Oph IRS 63.

The feet of the streamers are located near the sulfur-oxide ring (Sect. [3.1.2](#sec_streamer_irs63)). At these feet, the emission of SO$_2$ ($8_{3,5}-8_{2,6}$) and SO$_2$ ($12_{3,9}-12_{2,10}$) is typically enhanced (Figs. [1](#fig_irs63_color_maps) and [5](#fig_irs63_3lines_so2)). In particular, an emission spot of SO$_2$ ($15_{2,14}-15_{1,15}$) is only marginally detected at the foot of S3 (see Fig. [5](#fig_irs63_3lines_so2)), with a S/N of $\sim$3 in the moment 0 map. However, the average spectrum of SO$_2$ ($15_{2,14} - 15_{1,15}$) at this spot shows a clear detection, with a S/N greater than 5 (Fig. [6](#fig_so2_spectra)). This SO$_2$ spot is spatially close to the SO spot in the same region. The SO$_2$ emission appears more extended than the SO spot and seems to stretch toward the bases of S2 and S3 (Fig. [5](#fig_irs63_3lines_so2)), though this interpretation remains tentative due to the relatively low S/N. Notably, the SO$_2$ ($15_{2,14}-15_{1,15}$) transition has a high upper-level energy of $E_u \sim 120$ K (Table [\[tab_transitions\]](#tab_transitions)), suggesting that the spot at the foot of S3 traces gas that is warmer and/or denser than the average conditions in the sulfur-oxide ring. This may result from the interaction between S3 and the inner envelope or disk near the centrifugal barrier. The large off-midplane angle $\theta_0^{\rm off\,disk}$ of S3 allows it to fall directly onto the midplane in the vicinity of the sulfur-oxide ring (Sect. [4.2.3](#sec_streamer_onoff)), potentially generating strong shocks that excite and produce warm SO$_2$ emission. These findings support the interpretation of the spiral-like structures as gas streamers associated with the inner envelope, where their infall motions play a dynamically and chemically significant role near the centrifugal barrier. Our results suggest that the sulfur-oxide ring is likely induced by shocks around the centrifugal barrier, with SO$_2$ serving as a more sensitive tracer of strong shocks than SO (cite: 2021A&A...653A.159V).

To further test this interpretation and assess the thermochemical state of the gas, we analyze the SO$_2$ line profiles and construct a rotational diagram of the warm spot (Fig. [6](#fig_so2_spectra)). The excitation temperature ($T_{\rm ex}$) and column density ($N$) of SO$_2$ are determined to be 53 K and $3.3 \times 10^{14}$ cm$^{-2}$, respectively, using the method described in Appendix [11](#sec_cal_rtdiagram). These results confirm that the SO$_2$ spot is indeed warm, with a gas temperature $\gtrsim 50$ K—typical of post-shock molecular gas (cite: 2015A&A...578A..63F; 2021A&A...653A.159V). The SO spectrum at the warm spot exhibits a line width of 1.5 km s$^{-1}$, a peak brightness temperature of 15 K, and an integrated intensity of 23.4 K km s$^{-1}$. The main uncertainty in the derived column densities stems from the excitation temperature, which is estimated to be accurate within 20% (Fig. [6](#fig_so2_spectra)). Adopting the same $T_{\rm ex}$ as for SO$_2$, the SO column density is calculated to be $5 \times 10^{14}$ cm$^{-2}$, corrected for optical depth effects ($\tau \lesssim 0.3$; Appendix [11](#sec_cal_rtdiagram)). The resulting column density ratio $N$(SO$_2$)/$N$(SO) is approximately 0.6—significantly higher than the value of 0.03 predicted by the fiducial shock model of (cite: 2021A&A...653A.159V). Both SO and SO$_2$ can be efficiently formed through reactions of atomic S with OH in high-velocity ($>$4 km s$^{-1}$) shocks in moderately dense environments (cite: 2021A&A...653A.159V). To account for the observed high SO$_2$/SO ratio, a shock velocity exceeding 4 km s$^{-1}$ is required, which is consistent with the velocity range observed in the SO ring (see color bar in panel (a) of Fig. [2](#fig_irs63_SO_mom12)). A streamer impacting the centrifugal barrier can generate such a strong shock, enhancing SO$_2$ production. In contrast, streamers that co-rotate with the inner envelope are less likely to experience this level of shock interaction (Sect. [4.2.2](#sec_shockedsurface)). We therefore conclude that the observed SO$_2$ emission at the foot of S3 is likely induced by strong accretion shocks.

Knowing the excitation temperature allows us to estimate the density of the shocked gas. Assuming a warm spot size of 0.2$\ensuremath{''}$ (or $L_{\rm spot} \sim 26$ au) and a post-shock SO abundance ($X_{\rm SO}$) of $10^{-8}$ (cite: 2021A&A...653A.159V), the number density ($n_{\rm H_2}$) at the warm spot can be estimated as: $$\begin{equation}
n_{\rm H_2} = \frac{N_{\rm SO}}{X_{\rm SO} L_{\rm spot}} \sim 10^8\ {\rm cm}^{-3}. \label{eq_nh2_spot}
\end{equation}$$ Free-fall envelope models—such as the classical CMU model (cite: 1976ApJ...210..377U; 1981Icar...48..353C) and the constant-$J$ model (see Sect. [4.2.1](#sec_hardsurface) for a brief introduction)—predict a divergent density at the centrifugal radius ($R_{\rm C}$) due to the neglect of pressure (e.g., Eq. [\[eq_rhoenv\]](#eq_rhoenv)). Given that both the radial thickness of the SO ring and the size of the warm spot are approximately $0.4\,R_{\rm C}$, we adopt the density at $1.4\,R_{\rm C}$ from the constant-$J$ model as a representative value for the inner envelope. Assuming an accretion rate of $10^{-6}$ $M_\ensuremath{\odot}$ yr$^{-1}$ (cite: 2023ApJ...958...98F), this yields a typical density of $\sim 10^7$ cm$^{-3}$ for the inner envelope—slightly lower than the estimated density at the warm spot (Eq. [\[eq_nh2_spot\]](#eq_nh2_spot)). This discrepancy may arise from (1) a higher density in the streamers compared to the surrounding envelope, and/or (2) accumulation of material in the post-shock gas.

![](DK_Cha_moms.pdf)

### Inner envelope motion

In addition to the SO rings and spiral-like structures, weak extended SO emission is detected outside the ring. Along the minor axis, the northeast region shows a slight redshift, while the southwest region is slightly blueshifted (panel (b) of Fig. [2](#fig_irs63_SO_mom12)). Because pure rotational motion would produce zero projected velocity along the minor axis, this pattern indicates the presence of both rotational and infalling motions. Given that this extended emission lies primarily outside the centrifugal barrier, we interpret it as tracing the surface of a disk-like envelope confined by an accretion shock. This interpretation is developed based on our combined observational results and is presented in detail in Sect. [4](#sec_model), particularly in Sect. [4.2.2](#sec_shockedsurface). In other words, we interpret this emission as likely originating from the rotating and infalling inner envelope.

To support the above hypothesis, we first examine the rotational motion of the extended structure. The rotational and infalling velocity components may be coupled; however, the projection of the infalling velocity component along the major axis of the disk and inner envelope is expected to be zero (assuming negligible envelope flare). Therefore, the position-velocity (PV) map of SO along the major axis of the SO ring (panel (a) of Fig. [7](#fig_pv_irs63)) primarily reflects the rotational velocity component. The rotational velocity of the inner envelope is expected to follow a power-law with radius, characterized by an index $\beta$ that can range from 0 (free fall with zero angular momentum) to $-1/2$ (Keplerian rotation), or even $-1$ (free fall with conserved angular momentum). This framework is further detailed in Eq. [\[eq_mod_vphi\]](#eq_mod_vphi) and Sect. [4.2.2](#sec_shockedsurface). If the motion of the post-shock surface traced by the extended SO emission is fully governed by the underlying gas flows, one would anticipate a velocity index close to $\beta = -1$. However, given the current sensitivity, we cannot conclusively distinguish between $\beta = -1$ and $\beta = -1/2$. Thus, while both pure rotational and rotating–infalling motions remain consistent with the velocity distribution along the major axis, our combined kinematic analysis confirms the presence of infalling motion in the extended structure.

Furthermore, we modeled the 2D distribution of the projected velocity for a rotating and infalling inner envelope (see panel (b) of Fig. [7](#fig_pv_irs63)), using Eqs. [\[eq_mod_vr\]](#eq_mod_vr) and [\[eq_mod_vphi\]](#eq_mod_vphi). The rotation follows a power-law with an index ($\beta$) of $-1$, while the infall velocity is fixed. We adjusted the ratio of these velocities to match the observations. The modeled velocity distribution reproduces key features of the observed data (Fig. [2](#fig_irs63_SO_mom12)), including: (1) the slight offset between the major axis of the SO ring (represented by the blank ellipse in panel (b) of Fig. [7](#fig_pv_irs63)) and the symmetry axis of the moment-1 map; and (2) the S-shaped structure in the moment-1 map, extending from the lower left to the upper right of panel (b) in Fig. [7](#fig_pv_irs63) (see panel (a) of Fig. [2](#fig_irs63_SO_mom12) for the observed S-shape). This confirms that the extended SO emission outside the ring can be explained by emission from a disk-like inner envelope, potentially originating from its surface, with its rotating–infalling motion tracing the continuation of the free-fall streams with non-zero angular momentum.

These modeling results provide a physical basis for interpreting the structure and dynamics of the inner envelope, which plays a critical role in mediating accretion from large scales. Building on this, we now turn to the interaction between the streamers and the envelope. The inner envelope offers a valuable window into accretion processes near the disk and the behavior of gas streamers. Conceptually, off-midplane streamers are expected to have a strong dynamical impact on the envelope at their collision sites, while in-midplane streamers may gradually merge with the inner envelope and effectively serve as part of it. This distinction provides a qualitative framework for understanding the varying shock activity associated with different types of streamers. A more detailed discussion of these interactions is developed in the context of the disk–envelope framework in Sects. [4.2.2](#sec_shockedsurface) and [4.2.3](#sec_streamer_onoff).

![](DK_Cha_pv.pdf)

### Tentative features in the SO$_2$ line profiles

At the warm spot, the SO$_2$ spectra with higher $E_{\rm u}$ appear to be more blueward skewed (Fig. [6](#fig_so2_spectra)). SO$_2$ ($15_{2,14}-15_{1,15}$) exhibits the most prominent characteristic with a blue shoulder, albeit with a S/N of only $\sim 2.5$. We tentatively interpret this as evidence that S3 has a large $\theta_0^{\rm off\ disk}$ and impacts the midplane with a blueshifted velocity (see Fig. [4](#fig_IRS63_model_streamers)). Near the emission line of SO$_2$ ($12_{3,9}-12_{2,10})$, there is a weak ($2\sigma$) line feature at $\sim 8.5$ km s$^{-1}$ with respect to the rest frequency of SO$_2$ ($12_{3,9}-12_{2,10}$). This feature has a frequency close to the rest frequency of the transition $26_{3,23}-25_{4,22}$ of SO$_2$ $v_2=1$. This transition has a very high $E_{\rm u}$ value of $>1117$ K. The ground-level energy of SO$_2$ $v_2=1$ is $\sim745$ K (cite: 2005JMoSp.232..213M), and this transition has an $E_{\rm u}$ of 372 K with respect to the ground level of SO$_2$ $v_2=1$. If the emission line of this transition has a velocity shift similar to that of SO$_2$ ($12_{3,9}-12_{2,10}$), its peak should appear at $\sim 10$ km s$^{-1}$. The location of this line feature on the velocity axis is consistent with the blueward skewing trend observed for the high-$E_{\rm u}$ lines of SO$_2$ at the warm spot. Considering that the $T_{\rm ex}$ given by the rotational diagram of SO$_2$ (Fig. [6](#fig_so2_spectra)) is only a few tens of Kelvin, this transition would be unlikely to be excited if it originates from the same gas component traced by the relatively low-$E_{\rm u}$ lines. One possibility is the presence of a hotter gas component that allows for the excitation of vibrational states of SO$_2$ $v_2=1$, via processes such as infrared pumping (cite: 2024A&A...682A..78V). While we cannot entirely rule out this scenario, we consider it more likely that this line feature is a random observational spike, given its low S/N in Oph IRS 63 and the lack of a corresponding detection in DK Cha, an object with much stronger emission of sulfur-bearing molecules and warmer SO$_2$ spots (Sect. [3.2](#sec_dkcha)).

![](DKCha_warmspot.pdf)

## DK Cha

While clear signatures of accretion shocks, such as ring-like features and spiral streamers in SO and SO$_2$ emission, were observed in Oph IRS 63, the situation for DK Cha, an intermediate-mass protostar, is less straightforward. Nevertheless, its likely more face-on orientation and the limited resolution of the available data still provide valuable insights into how shock features might manifest in a different mass regime.

### Inclination angle of the disk continuum

There are no ALMA long-baseline data (with a beam resolution better than $0.1\ensuremath{''}$) available for this object in the archive. Fig. [8](#fig_moms_dkcha) shows the moment maps of SO and SO$_2$ for DK Cha, overlaid with its dust continuum at a resolution of $\sim 0.2\ensuremath{''}$. Although our data do not fully resolve the disk, the nearly round morphology of the continuum emission suggests that DK Cha has a nearly face-on disk. The 2D Gaussian fitting of the continuum gives a major-axis FWHM of $0.44\ensuremath{''} \pm 0.01\ensuremath{''}$, a minor-axis FWHM of $0.38\ensuremath{''} \pm 0.11\ensuremath{''}$, and a position angle ($\phi_{\rm view}$) of $43^\circ\pm 10^\circ$. The values for the synthesis beam are $0.22\ensuremath{''}$, $0.15\ensuremath{''}$, and $65^\circ$, respectively. The beam-deconvolved[^3] major-to-minor axis ratio of the continuum emission gives a $\theta_{\rm view}$ of $\sim 20^\circ$ . This result is consistent with the findings from the analysis of the multi-cone outflows of DK Cha by (cite: 2023ApJ...945...63H), who reported a $\theta_{\rm view}$ of $19^\circ$. The \[S ii\] 6731 Å data from VLA MUSE (Sect. [2.1.2](#sec_obs_vlt)) show an outflow lobe in the north-east direction of DK Cha (panel (a) of Fig. [8](#fig_moms_dkcha)). This is likely the blueshifted lobe, while the redshifted one is not visible due to extinction. This confirms that the disk of DK Cha is nearly face-on with a small $\theta_{\rm view}$. Therefore, we adopt a $\theta_{\rm view}$ of $20^\circ$ for the disk of DK Cha in this work. Similar to Oph IRS 63, the emission of SO and SO$_2$ is absent in the disk region of DK Cha, as traced by the dust continuum. The nearly face-on geometry of DK Cha and the absence of SO and SO$_2$ emission within the disk region, similar to Oph IRS 63, suggest that this chemical differentiation is intrinsic rather than a projection effect, reinforcing the importance of geometry when interpreting molecular tracers in protostellar environments.

### Streamers and warm spots

Building on the clear identification of spiral-like streamers in Oph IRS 63, we detect analogous features in DK Cha, although with differing morphologies and S/Ns that likely reflect the influence of its more face-on orientation and varying shock activity (Fig. [8](#fig_moms_dkcha)). Three spiral-like structures can be identified on the moment 0 map of SO (S1–S3; Fig. [8](#fig_moms_dkcha)). The stronger heads of S1 and S2 have S/Ns greater than 10, while the weaker tails of S1–S3 have S/Ns of approximately 5. As observed in Oph IRS 63, we interpret these as accretion streamers of DK Cha. It is evident that the south-east tail of S2 exhibits very narrow line widths ($\Delta V \sim$ 0.5 km s$^{-1}$; Fig. [9](#fig_dkcha_pv)). The line width of S2 increases dramatically when it intersects with P1, a broad-line (FWHM $\sim$ 3 km s$^{-1}$) and SO-bright segment with a projected length of $\sim 300$ au. P1 is also bright in SO$_2$ emission (panels d–f of Fig. [8](#fig_moms_dkcha)). The inner end of P1 is located at the boundary of the disk traced by the dust continuum. There is no obvious velocity gradient along S2 and P1, which may be due to projection effects, given that DK Cha is nearly face-on and S2 lies along the major axis in the plane of the sky. In addition to S2, a short streamer, S3, is also connected to P1. The intersection between S3 and P1 produces a compact spot (with a size comparable to the beam), which is very broad in line width (FWHM $\sim$ 4 km s$^{-1}$). Below, this spot is denoted as $\rm S3\perp P1$. We interpret that both S2 and S3 are falling onto the inner envelope: the falling gas forms the streamer P1, and P1 continuously feeds material to the central disk. A warm spot is created when S3 hits P1. P1 continuously endures shocks as it passes through the inner disk, leading to a long segment of emission of SO and SO$_2$ (Sect. [4.2.3](#sec_streamer_onoff)).

![](DK_Cha_CO2-1.pdf)

S1, the north streamer, is connected to a compact spot (denoted as P2 in the PV maps; Fig. [8](#fig_moms_dkcha)), which has both emission of SO and SO$_2$. P2 has a line width comparable to that of $\rm S3\perp P1$. The excitation temperatures of SO$_2$ of the two spots (P2, and $\rm S3\perp P1$) are calculated through drawing the rotation diagrams of SO$_2$ (Fig. [10](#fig_dkcha_warmspots)). P2 has a higher excitation temperature of SO$_2$ than $\rm S3\perp P1$ (Sect. [3.2.3](#sec_hotspot)). We interpret that S1 is a off-midplane streamer (Sect. [4.2.3](#sec_streamer_onoff)), and it directly hits the inner envelope near the centrifugal barrier, creating the hot spot P2. The warm spots in DK Cha are generally hotter than those in Oph IRS 63, which is expected due to DK Cha’s more massive central star. Furthermore, DK Cha’s higher gas density, compared to Oph IRS 63, aids in detecting the high-$E_{\rm u}$ lines.

### A hot SO$_2$ spot of DK Cha?

Compared to the warm spot of $\rm S3\perp P1$, which has $T_{\rm ex} \sim 70$ K, the spot P2 exhibits an even higher temperature of $T_{\rm ex} > 100$ K (Fig. [10](#fig_dkcha_warmspots)). Therefore, P2 can be considered a hot spot. We examined the spectrum of SO$_2$ $16_{1,15}-15_{2,14}$, which has the highest $E_{\rm u}$ (131 K) among the observed lines toward DK Cha at P1 (Fig. [20](#fig_dkcha_spw33spe)), and it shows a S/N higher than 5, confirming that the high fitted temperature is not caused by noise or spikes. The temperature difference between the two spots can be explained by the differences in $\theta_{\rm view}$ and the specific angular momentum of the streamers that produce them. S1 directly interacts with the midplane at P2, which is significantly closer to the center of mass compared to $\rm S3\perp P1$. Because S1 is off the midplane, it experiences less slowing down from the inner envelope before the strong shock occurs (Sect. [4.2.3](#sec_streamer_onoff)), leading to a hotter spot at P2. The presence of multiple streamers interacting with the inner envelope and producing warm spot/segment—characterized by excitation temperatures notably higher than those in Oph IRS 63—highlights the influence of stellar mass and polar angle in governing the nature and detectability of shock signatures.

### Streamers traced from archived CO data

Consistent with the SO and SO$_2$ maps, archival CO (2-1) observations provide additional — albeit lower-resolution — confirmation of the streamer structures (Fig. [11](#fig_dkcha_co)). Two of the three streamers identified in SO (S1 and S2; Fig. [8](#fig_moms_dkcha)) are marginally visible in the moment 0 map of the archived CO (2-1) data. To reduce contamination from outflows, we integrated a narrow velocity interval (1–5 km s$^{-1}$) around DK Cha’s systemic velocity (cite: 2012A&A...542A...8K). The CO emission generally lies on the convex sides of the SO-traced streamers, suggesting outward forces acting upon them (Sect. [4](#sec_model)). Within the disk region traced by the ALMA continuum, CO (2-1) spectra show strong absorption near the systemic velocity. Moreover, the CO data have lower spatial resolution than the SO data (Sect. [2](#sec_obs)), so the moment 1 map of CO (panel (b) of Fig. [11](#fig_dkcha_co)) only roughly traces the disk’s velocity gradient (Sect. [3.2.5](#sec_dkcha_rotdirec)). A bright CO arc is visible at the southeastern disk margin, potentially marking the centrifugal barrier or the interaction between streamer/segment P1 and the inner envelope (Figs. [8](#fig_moms_dkcha) and [12](#fig_dkcha_cartoon)), although contamination from low-velocity outflow components cannot be excluded (cite: 2023ApJ...945...63H). Together, the CO data offer important complementary insights into the dynamics and external influences governing the infalling gas streams.

![](dk_cha_cartoon-crop.pdf)

### Discussion of the direction of rotation

Extended SO emission features P3 and P4 (Fig. [8](#fig_moms_dkcha)) appear at blueshifted and redshifted velocities, respectively, but their origins are challenging to interpret (Fig. [12](#fig_dkcha_cartoon)). One possibility is that P4 represents the inner part of a streamer similar to S2 and S3, infalling onto the inner envelope rather than onto P1. P3 might simply be part of P2. Alternatively, these features could trace warm molecular gas influenced by outflows (cite: 2006A&A...454L..75V), or be shaped by the disk’s rotation.

Despite the wealth of spatial and spectral information, the exact rotational direction of DK Cha’s disk remains uncertain. The morphology of S1 and the velocities observed in P1 and P2 suggest that DK Cha’s disk rotates clockwise (Fig. [12](#fig_dkcha_cartoon)), a scenario supported by the velocity distribution of CO (2–1) within the disk region (Fig. [11](#fig_dkcha_co)). However, this interpretation does not fully explain the morphology of S2. The radial velocity gradient of S2 (panel (b) of Fig. [8](#fig_moms_dkcha)) differs from that expected in a simple rotational scenario, which may point to additional factors influencing its trajectory. One possibility—though speculative—is that S2 is affected by external pressure on larger scales (on the order of thousands of AU), perhaps from east to west, leading to reduced specific angular momentum. The angular momentum of S2 appears to decrease further as the gas enters P1, likely due to interactions between P1 and the inner envelope (Sects. [4.2.2](#sec_shockedsurface) and [4.2.3](#sec_streamer_onoff)). Consequently, P1 moves inward toward the central mass with low specific angular momentum, and continuous shocks are expected as it propagates through the inner envelope. This scenario may explain the linear morphology and broad SO and SO$_2$ emission observed along P1. A schematic illustrating the connections between these streamers and features in DK Cha is provided in Fig. [12](#fig_dkcha_cartoon).

Previous observations have revealed multi-cone outflows in DK Cha with highly complex morphology (cite: 2023ApJ...945...63H). These intricate dynamical interactions, combined with external pressure and the multi-cone outflow structure, likely reflect the effects of variable angular momentum accretion and intermittent shock-driven phenomena, consistent with scenarios proposed for other protostellar systems (cite: 2009ApJ...694.1045Z; 2020A&A...636A..38N).

![](L1527_SO_SO2.pdf)

![](L1527_cavity_streamer.pdf)

## L1527

In contrast to Oph IRS 63 and DK Cha, L1527, an edge-on Class 0 protostar, provides a different perspective on accretion shocks. The presence of accretion shocks in L1527, as traced by SO and SO$_2$ emission, offers valuable insights into how these features manifest in an edge-on system, shedding light on the dynamics of accretion in protostellar disks and envelopes.

### Parallel slabs of SO

The SO emission from L1527 measured in this work (Fig. [13](#fig_L1527_mompv)) reveals two parallel slabs, nearly identical to those observed in different SO transitions in (cite: 2014Natur.507...78S; 2017MNRAS.467L..76S). This supports the interpretation that SO emission arises from the surface of a disk or disk-like structure (see also Sects. [3.1.4](#sec_irs63_envelope) and [4.2.2](#sec_shockedsurface)). We only cover one SO$2$ transition for L1527 (Table [\[tab_transitions\]](#tab_transitions)), which is marginally detected (Fig. [21](#fig_L1527_SO2)). Between the parallel slabs of SO, there is a compact region, approximately 50 au in size, that exhibits SO$2$ $16{3,13}-16{2,14}$ emission ($E_u = 148$ K), as shown by the black contours in Fig. [13](#fig_L1527_mompv) (see also Fig. [21](#fig_L1527_SO2)). Due to the limited data (only one transition), the temperature of the SO$_2$-emitting region cannot be well constrained. The SO$_2$ emission also appears to show two parallel slabs, but the low S/N prevents further analysis. Given that the SO$_2$ transition has a high excitation energy ($E_u \sim 150$ K, Table [\[tab_transitions\]](#tab_transitions)), it likely traces a region that is warmer compared to the average temperature of the SO emission region.

### Two rings of SO at the disk scale

The PV map of SO along the major axis of L1527 (panel (c) of Fig. [13](#fig_L1527_mompv)) reveals an X-shaped morphology composed of two linear strips, each showing a distinct velocity gradient. Note that each linear strip corresponds to the projection of a rotating ring seen edge-on. This is because the projected velocity ($v_{\rm proj}$) and projected distance ($r_{\rm proj}$) vary with the sine of the azimuthal angle ($\phi$): $$\begin{equation}
    v_{\rm proj} \propto r_{\rm proj} \propto \sin(\phi).
\end{equation}$$ The longer and brighter strip with the smaller velocity gradient corresponds to the outer ring (the parallel slab), which has been previously reported and interpreted as the centrifugal barrier of the envelope (cite: 2014Natur.507...78S; 2017MNRAS.467L..76S). In contrast, the fainter strip exhibits a much steeper velocity gradient (Fig. [13](#fig_L1527_mompv)) and likely traces a newly identified inner ring of SO emission located inside the centrifugal barrier. We refer to these features as the outer and inner rings, respectively.

The radii of the two SO rings inferred from the PV map are approximately $r_{\rm out} \sim 150$ au (or $\sim$1$''$) for the outer ring and $r_{\rm in} \sim 35$ au for the inner ring. The inner SO ring has a size comparable to the SO$_2$ emission region (Fig. [13](#fig_L1527_mompv)). The corresponding velocity gradients observed on the PV map are $V_{\rm grad}^{\rm out} = 1.5$ km s$^{-1}$ arcsec$^{-1}$ and $V_{\rm grad}^{\rm in} = 15$ km s$^{-1}$ arcsec$^{-1}$, respectively. These values approximately obey the relation: $$\begin{equation}
    \frac{V_{\rm grad}^{\rm out}}{V_{\rm grad}^{\rm in}} \sim \left( \frac{r_{\rm out}}{r_{\rm in}} \right)^{-1.5},
\end{equation}$$ suggesting that both rings are in Keplerian rotation. This follows because, for Keplerian motion, the rotational velocity satisfies $$\begin{equation}
    v_{\rm rot} = \sqrt{\frac{GM_\star}{r}} \propto r^{-0.5}, \label{eq_keprot}
\end{equation}$$ and the corresponding velocity gradient scales as $$\begin{equation}
    V_{\rm grad} \sim \frac{v_{\rm rot}}{r} \propto r^{-1.5}.
\end{equation}$$ Using Equation [\[eq_keprot\]](#eq_keprot), the central mass of L1527 is estimated to be $\sim$0.5 $M_\odot$, consistent with the recent dynamical mass measurement (including the star and disk) by (cite: 2023ApJ...951...10V) (see Sect. [2.3](#sec_sample)).

A similarly steep linear structure was also observed in the PV map of H$_2$CO in L1527, corresponding to a radius of $\sim$25 au (cite: 2023ApJ...951...10V), which is consistent with the inner SO ring found in this work. That study interpreted the H$_2$CO structure as marking the snowline of H$_2$CO, located at a temperature of $\sim$70 K. By analogy, the inner SO ring may represent the snowline of SO. The sublimation temperature of a molecular species depends on its binding energy, which remains uncertain (cite: 2013A&A...550A..36M; 2017ApJ...844...71P). According to the UMIST database (cite: 2013A&A...550A..36M), the binding energy of SO is 2600 K, which is somewhat higher than that of H$_2$CO (2050 K), though other studies suggest a lower SO binding energy of $\sim$1800 K (cite: 2017ApJ...844...71P). This implies that the inner SO ring may indeed trace the SO snowline. In this interpretation, SO is initially enhanced at the centrifugal barrier (outer ring), then depleted or destroyed within the outer disk, and re-enhanced near the snowline (inner ring). Similarly, SO$_2$ is also enhanced in the vicinity of the inner SO ring.

![](L1527_so_co_offset.pdf)

### Infalling layer of SO along the outflow boundary

We now turn to the large-scale SO emission. No obvious streamers of SO are visible in the data cube cleaned using the *Briggs* *robust* = 0.5 weighting scheme (Sect. [2.1.1](#sec_obssetup)). Compared to this weighting scheme, the *natural* weighting (*robust* = 2) assigns equal weight to all samples, resulting in lower noise levels and a larger synthesized beam. Thus, the *natural* weighting enhances the S/N of large-scale emission. We examined the data cube of L1527, cleaned using *natural* weighting, to search for large-scale SO structures. Surprisingly, linear SO emission structures, referred to as SO strips, are visible along the boundaries of CO outflows (Fig. [14](#fig_L1527_cavity)). The most prominent SO strip lies along the southwestern (SW) outflow boundary, extending over 12$''$ (1700 au) from the central protostar, with a S/N (at the emission peak) exceeding 5 in the moment 0 map. The emission along the SW boundary is even more pronounced in the PV map, where the S/N exceeds 7. The SO spectrum stacked along the SW direction exhibits a very narrow linewidth of approximately 0.44 km s$^{-1}$ (see Appendix [12](#sect_lw_sw) for details), confirming that the SO emission along the outflow boundaries is only partially resolved spectrally. Along the northwestern (NW) and southeastern (SE) outflow boundaries, SO emission is only marginally detected in the moment 0 map (panel (b) of Fig. [14](#fig_L1527_cavity)). However, in the PV map (panel (d) of Fig. [14](#fig_L1527_cavity)), narrow-line SO emission is clearly observed along these boundaries, with S/Ns of $\sim 5$.

A notable feature of the SO strips, particularly along the SW boundary, is that the SO emission peak is spatially offset from the CO emission peak, lying on the convex (outer) side of the outflow boundaries. To quantify this spatial offset between the two tracers, we present the averaged transverse emission profiles of SO and CO along the outflow boundaries in Fig. [15](#fig_so_co_offset). For the SW boundary, a significant offset is found between the Gaussian fits of the SO and CO profiles, with a $t$-statistic exceeding 15 (Table [2](#tab_L1527_offset)), indicating a highly significant separation. The SO emission is shifted by approximately $0.7\ensuremath{''} \pm 0.01\ensuremath{''}$ relative to the CO emission in the transverse direction, suggesting that SO traces the convex side of the hourglass-shaped CO cavity walls. The FWHMs of the Gaussian fits are $1.3 \pm 0.1\ensuremath{''}$ for SO and $0.9 \pm 0.1\ensuremath{''}$ for CO. Note that the CO and SO images (with natural weighting) have similar beam sizes of $0.32\ensuremath{''}$ and $0.35\ensuremath{''}$, respectively. The narrow transverse profiles confirm the presence of well-defined strips in the moment 0 maps, with the CO boundary appearing sharper than the SO strip. Similar spatial offsets between CO and SO are also observed along the NE and NW boundaries (Fig. [15](#fig_so_co_offset)). Since the transverse directions differ for each boundary, these systematic offsets cannot be attributed to image misalignment between the CO and SO data. This supports the interpretation that the SO emission originates from a conical layer that is either geometrically thicker or located farther from the outflow axis than the CO-emitting surface.

The SO spectra along the strips (outflow boundaries) exhibit central velocities close to the systemic velocity at large scales (6 km s$^{-1}$), with their velocity offset (relative to the systemic velocity) increasing significantly as the distance from the central protostar decreases (Fig. [14](#fig_L1527_cavity)). This behavior suggests that the SO layer may be undergoing infalling motion rather than outflowing. To test this hypothesis, we model the strips in the PV maps using free-fall trajectories, following a similar approach to that in Fig. [4](#fig_IRS63_model_streamers) (see details in Appendix [9](#sec_parabolic_trajectory)). In the model, we adopt a central mass of $M_\star = 0.5\ M_\odot$ (Sect. [3.3.2](#sec_L1527_2rings)), a centrifugal barrier radius of $R_{\rm C} = 1\ensuremath{''}$, and viewing angles $\theta_{\rm view} = 90\ensuremath{^\circ}$, $\phi_{\rm view} = 90\ensuremath{^\circ}$, with initial trajectory angles $\theta_0 = 45\ensuremath{^\circ}$ and $\phi_0 = 0\ensuremath{^\circ}$. Remarkably, the free-fall trajectories reproduce the observed strips very well (panels (c) and (d) of Fig. [14](#fig_L1527_cavity)). From the PV maps, it is evident that the southern strips along SE and SW do not directly connect to the southern blue part of the SO ring, but rather to its northern part. Similarly, the northern strip along NW appears connected to the southern blue part of the SO ring. This supports the interpretation that the SO strips do not move along straight paths but instead follow curved (possibly parabolic) trajectories wrapping around the outflow cone as they move inward.

Observations of protostars such as HH 211 and IRAS 16293$-$2422 A1 reveal that SO emission can exhibit velocity gradients perpendicular to the outflow axes, which have been interpreted as signatures of twisted magnetic fields (cite: 2021ApJ...907L..41L; 2021ApJ...921...12O). Due to the limited S/N in our data, we are unable to place meaningful constraints on any velocity gradient perpendicular to the outflow axis in L1527.

Based on the preceding results, we propose the presence of a mildly shocked, conical SO-emitting layer undergoing downward-spiraling infall, which warps the outflow cavity. The observed SO emission pattern may result from interactions between the outflow and the infalling envelope, suggesting that angular momentum transfer from the outflow to the envelope is non-negligible (Sect. [4.2.1](#sec_hardsurface)). We interpret the infalling SO layer as tracing the surface of the outer envelope on large scales (hundreds to over a thousand astronomical units). An increase in angular momentum leads to an outward expansion of the centrifugal radius. As a result, on smaller scales (from hundreds to several thousand au), the outflow boundary does not necessarily make direct contact with the inner envelope (Sect. [4.2.1](#sec_hardsurface)).

# Shock confined outer and inner envelopes?

In the previous sections, we have shown that SO and SO$_2$ emissions primarily trace shocks located near the centrifugal barrier and at the bases of infalling gas streamers. These observational features indicate that shocks play a significant role in shaping both the envelope structures and the disk-envelope interface. Furthermore, the spatial and kinematic patterns of SO emission near the outflow boundaries suggest possible interactions between the infalling envelope and the outflow. Although this evidence remains tentative, such interactions may contribute to compressing the outer envelope and consequently influence the motions of the inner envelope. The interaction between streams/streamers and envelope/disk serves as a key factor in the patterns of shock-related emission. Motivated by these observational insights, we constructed a self-consistent model of the disk-envelope system and the streamers to explore these possibilities further and to better understand the physical mechanisms driving the observed features.

![](model_multipanels.pdf)

![](shockedenvelope_model.png)

## CMU model

We begin by considering the classical “CMU” model of a protostellar envelope (cite: 1976ApJ...210..377U; 1981Icar...48..353C). In this model, the gas moves in free fall with zero total energy (the sum of kinetic and gravitational potential energy). For a gas stream initially infalling with a polar angle $\theta_0$ (measured from the system’s rotation axis, which is typically defined by the angular momentum of the protostar and its surroundings), the specific angular momentum is given by $$\begin{equation}
J = j(\theta_0) J_{\rm mid}.
\end{equation}$$ Here, $\theta_0$ is the initial polar angle of the gas trajectory relative to the rotation axis. By convention, $\theta_0 = 0$ corresponds to the rotation axis (pole), and $\theta_0 = \pi/2$ corresponds to the midplane (equator). At the midplane, $j(\pi/2) = 1$, meaning the specific angular momentum is largest there.

Ignoring gas pressure, the gas stream follows a parabolic trajectory. The radius of the centrifugal barrier—defined as the distance from the focus to where the parabolic path crosses the midplane—is $$\begin{equation}
R_{\rm C}(\theta_0) = \frac{J^2}{GM_\star} = j^2(\theta_0) R_{\rm C}^{\rm mid},
\label{eq_rc}
\end{equation}$$ where $$\begin{equation}
R_{\rm C}^{\rm mid} = \frac{J_{\rm mid}^2}{GM_\star}.
\end{equation}$$ This $R_{\rm C}^{\rm mid}$ is the centrifugal barrier radius for gas falling exactly in the midplane.

Under the gravity of the central star (ignoring the envelope’s self-gravity), the parabolic trajectory is described by (cite: 1976ApJ...210..377U) $$\begin{equation}
\frac{r}{R_{\rm C}^{\rm mid}} = \frac{j^2(\theta_0) \cos(\theta_0)}{\cos(\theta_0) - \cos(\theta)},
\label{eq_sl}
\end{equation}$$ where $r$ and $\theta$ are the radius and polar angle at a given point along the streamline.

The radial infall velocity (velocity component along $r$) is (cite: 1981Icar...48..353C) $$\begin{equation}
v_r = -\left(\frac{GM_\star}{r}\right)^{1/2} \left(1 + \frac{\cos(\theta)}{\cos(\theta_0)}\right)^{1/2}.
\label{eq_velo_r}
\end{equation}$$ Although $v_r$ depends on $r$, $\theta_0$, and $\theta$, substituting Equation [\[eq_sl\]](#eq_sl) removes the explicit dependence on $\theta$.

Assuming the accretion rate at large distances is spherically symmetric, mass conservation implies the gas density can be expressed as (cite: 1981Icar...48..353C) $$\begin{equation}
\begin{aligned}
\rho &= \frac{\dot{M}_{\rm tot}}{4\pi r^2 v_r} \left(\frac{\partial \theta}{\partial \theta_0}\right)^{-1} \frac{\sin(\theta_0)}{\sin(\theta)} \\
&= \frac{\dot{M}_{\rm tot}}{4\pi r^2 v_r} \left( \left(1 - \frac{R_{\rm C}}{r}\right) + \frac{\cos(\theta_0)}{\sin(\theta_0)} \frac{d R_{\rm C}}{r d \theta_0} \right)^{-1}.
\label{eq_rho_raw}
\end{aligned}
\end{equation}$$ The original CMU model assumes $$\begin{equation}
j(\theta_0) = \sin(\theta_0),
\end{equation}$$ which leads to $$\begin{equation}
\rho = \frac{\dot{M}_{\rm tot}}{4\pi r^2 v_r} \left(1 + \frac{R_{\rm C}^{\rm mid}}{r} \left(2 - 3 \sin^2(\theta_0)\right)\right)^{-1}.
\label{eq_rho_cmu}
\end{equation}$$ The density depends on both radius $r$ and polar angle $\theta$ (see panel (a) of Fig. [16](#fig_model_multipanel)). Taking $R_{\rm C}^{\rm mid}$ as the disk radius, the mass infall rate from the envelope onto the disk within radius $R < R_{\rm C}^{\rm mid}$ is $$\begin{equation}
 \label{eq_Mdot_cmu}
\dot{M}(R) = \left(1 - \sqrt{1 - \frac{R}{R_{\rm C}^{\rm mid}}}\right) \dot{M}_{\rm tot}.
\end{equation}$$

Eq. [\[eq_Mdot_cmu\]](#eq_Mdot_cmu) leads to that half of the envelope’s mass falls onto the disk within $0.75\, R_{\rm C}^{\rm mid}$. However, this conflicts with observations showing that shock tracers such as SO and SO$_2$ are lacking in the central disk region (Sect. [3](#sec_obsresults)). One possible explanation is that stellar radiation destroys these molecules during infall. But since the SO/SO$_2$ snowline is expected to lie very close to the star in low-mass protostars (see Sect. [3.3](#sec_L1527) and references therein), radiation may not fully destroy these species. A more likely explanation is that some mechanism prevents envelope gas from directly falling onto the inner disk regions.

## constant-$J$ case

The model of (cite: 1976ApJ...210..377U) requires a gas stream with a small $\theta_0$ (initially from near the pole) to have very little angular momentum. This may not hold under the influence of stellar feedback. Outflows and jets are common in protostars and are believed to clear the polar region, forming a cavity (cite: 2016ARA&A..54..491B; 2020ApJ...900...15L). The cavity would exert continuous pressure on the gas stream originating near the pole during the early stages of accretion, efficiently increasing the stream’s angular momentum. This is supported by the infalling layers of SO closely tracing the outer edges of the CO outflow boundaries (see example of L1527 in Sect. [3.3.3](#sec_L1527_infalllayer)). Thus, $j(\theta_0)$ is not necessarily required to be an increasing function of $\theta_0$. Note that a stream with a larger $j(\theta_0)$ will have a larger $R_{\rm C}$ (Eq. [\[eq_rc\]](#eq_rc)). If $j(\theta_0)$ is a decreasing function of $\theta_0$, the streamlines from different $\theta_0$ values will interact with each other before reaching their centrifugal barriers. However, considering that the inner pressure of the outflow could influence the system at a large scale (e.g., thousands of au), there is enough time for the pressure gradient within the envelope to adjust the angular momentum of different streams. Therefore, we adopt a constant-$J$ case with $$\begin{equation}
j(\theta_0) = 1,
\label{eq_constj}
\end{equation}$$ and denote it as the constant-$J$ model.

### Hard-surface envelope by stellar feedback

In the constant-$J$ model, the centrifugal barrier radius $R_{\rm C}$ is constant and does not depend on the initial polar angle $\theta_0$. Ignoring pressure effects, gas streams originating from different $\theta_0$ values will converge and interact at the same radius $R_{\rm C}$ (Eq. [\[eq_rc\]](#eq_rc)). The density of the infalling gas can then be expressed as $$\begin{equation}
\rho = \frac{\dot{M}}{4\pi r^2 v_r} \frac{\cos{\theta_0}}{\cos{\theta}}, \label{eq_rhoenv}
\end{equation}$$ and using Eqs. [\[eq_sl\]](#eq_sl) and [\[eq_constj\]](#eq_constj), one obtains the relation $$\begin{equation}
\label{eq_theta_r}
\frac{\cos(\theta)}{\cos(\theta_0)} = \frac{r - R_{\rm C}}{r}.
\end{equation}$$ Substituting Eq. [\[eq_theta_r\]](#eq_theta_r) into Eq. [\[eq_rhoenv\]](#eq_rhoenv) gives a simplified expression for the density: $$\begin{equation}
\rho = \frac{\dot{M}}{4\pi r^2 v_r} \frac{r}{r - R_{\rm C}}. \label{eq_rhoenv_final}
\end{equation}$$ This is equivalent to Eq. [\[eq_rho_raw\]](#eq_rho_raw) when a constant $R_{\rm C}$ is assumed. Note that in the constant-$J$ model, $\rho$ explicitly depends only on $r$ and not on $\theta$ or $\theta_0$. Physically, this implies that at a given radius $r$, the infalling gas is uniformly compressed in the polar angle ($\theta$) direction for $\theta > \theta(r)|_{\theta_0=0}$, while the density sharply drops to zero for $\theta < \theta(r)|_{\theta_0=0}$. This discontinuity defines a "hard surface" for the envelope (panel (b) of Fig. [16](#fig_model_multipanel)). Note that external pressure sources, such as outflows, may only become significant at large radii. At smaller radii, the envelope surface does not need to be in direct contact with or confined by stellar feedback. Recent near-infrared JWST observations support the presence of an empty region between the outflow cavity and the inner envelope surface (cite: 2023ApJ...951L..32H).

Similarly, substituting Eq. [\[eq_theta_r\]](#eq_theta_r) into Eq. [\[eq_velo_r\]](#eq_velo_r) yields $$\begin{equation}
v_r = -\left(\frac{GM_\star}{r}\right)^{1/2} \left( \frac{2r - R_{\rm C}}{r} \right)^{1/2}.
\end{equation}$$ Thus, the radial infall velocity $v_r$ also becomes independent of both $\theta$ and $\theta_0$. Therefore, in the constant-$J$ model, both $v_r$ and $\rho$ explicitly depend only on the radius $r$ (see panel (b) of Fig. [16](#fig_model_multipanel)). For a stream lying in the midplane, the azimuthal velocity is given by $$\begin{equation}
v_{\phi} = \left(\frac{2GM_\star}{r} - v_r^2\right)^{1/2} = \sqrt{GM_\star R_{\rm C}} \, r^{-1}, \label{eq_vphi}
\end{equation}$$ where $v_r$ is given by Eqs. [\[eq_velo_r\]](#eq_velo_r) and [\[eq_theta_r\]](#eq_theta_r).

### Disk-like inner envelope confined by accretion shocks

The model above considers only the streams in free fall. As $r$ approaches the centrifugal barrier, the density increases drastically. When the streams reach the centrifugal barrier, shocks occur. A pressure gradient will develop due to the accumulation of material and the rise in temperature. As a result, the inner region of the envelope will swell (panel (d) of Fig. [16](#fig_model_multipanel)).

For the stream with $\theta_0 = 0$ (initially from the pole), when it enters the swell-up region, it will experience two types of decelerating forces: one from the ram pressure and the other from the thermal pressure gradient. The ram pressure force is aligned with the direction of gas motion ($-V_{\rm infall}$). The thermal pressure gradient, on the other hand, is directed along $r$, since $\rho$ is constant as a function of $\theta$ at a fixed $r$ (see Sect. [4.2.1](#sec_hardsurface)). We denote $h = z(r, \theta) = r \cos(\theta)$ as the height of the stream above the midplane, and $v_h$ as the velocity of the stream approaching the midplane. According to the geometric properties of a parabola (panel (c) of Fig. [16](#fig_model_multipanel)), at a given point on the streamline ($r, \theta$), $$\begin{equation}
v_r \equiv v_h
\end{equation}$$ and $$\begin{equation}
h = r - R_{\rm C}.
\end{equation}$$ The ram pressure will decelerate both $v_r$ and $v_h$ equally, allowing the stream to continue moving toward the centrifugal barrier. In contrast, the thermal pressure gradient exerts a stronger decelerating effect on $v_r$ than on $v_h$, causing the stream to fall onto the midplane before reaching the centrifugal barrier. Shocks will occur between the stream and the swell-up region if the residual of $v_h$ (denoted as $v_h^{\rm diff}$), $$\begin{equation}
v_h^{\rm diff} = \max(v_h - v_r),
\end{equation}$$ exceeds the sound speed.

Confined in the $h$ direction by shocks at its surface, the swell-up region will then be shaped into a flattened disk-like envelope (as qualitatively represented by the green area in panel (d) of Fig. [16](#fig_model_multipanel)). The detailed distribution of the velocity of the disk-like inner envelope is complex. For simplicity, we propose the following for a stream in the midplane: $$\begin{align}
   & v_\phi \propto r^{-1}, \label{eq_mod_vphi}\\
   & v_r \propto r^0 \propto \text{const.} \label{eq_mod_vr}
\end{align}$$ That is, $v_r$ is constrained to a constant value (with a power-law index $\beta = 0$), while $v_\phi$ remains largely unaffected compared to Eq. [\[eq_vphi\]](#eq_vphi). This results in a rotating-and-infalling disk-like inner envelope, with a steeper decrease in $v_\phi$ ($\beta = -1$) as $r$ increases, compared to Keplerian motion ($\beta = -1/2$). The surface of the disk-like inner envelope, where shocks occur, experiences shear forces from the gas beneath it. Consequently, the exact value of $\beta$ is challenging to predict, falling within the range of 0 to $-1$. If the motion of the post-shock surface is entirely governed by the gas below it, then Eqs. [\[eq_mod_vphi\]](#eq_mod_vphi) and [\[eq_mod_vr\]](#eq_mod_vr) provide a reasonable description of the velocity distribution at the post-shock surface. This scenario is supported by our observations (Figs. [2](#fig_irs63_SO_mom12) and [7](#fig_pv_irs63)).

The proposed shock-confined disk-like envelope shares some similarities with the so-called ‘pseudodisk’ supported by the $B$ field (cite: 2016ApJ...822...12H). However, there are significant differences. We do not incorporate the $B$ field in our model, as recent simulations (cite: 2019MNRAS.489.1719W) suggest that magnetic braking may not be crucial for the formation of low-mass disks. The disk-like envelope is located at $R > R_{\rm C}$, rather than wrapping around the disk from all sides. We highlight the role of shocks at the surface of the disk-like envelope in both the formation of the inner disk-like envelope and the associated shock-related chemistry. The shock tracers will appear as a ring at a radius of $\sim R_{\rm C}$ in the face-on view, and as a parallel slab in the edge-on view, consistent with observations (Sect. [3](#sec_obsresults)).

### Streamers dropping within/onto the disk-like envelope

In recent years, increasing observations have suggested that gas streamers, which connect the envelope to the disk, exist in protostars at various stages of development (cite: 2020NatAs...4.1158P; 2022A&A...667A..12V). (cite: 2020NatAs...4.1158P) first confirmed that these streamers can be explained as freely infalling gas toward the protostar. Consequently, it is natural to interpret streamers as a special class of streams that coexist with the globally infalling envelope. Streamers may also be linked to larger-scale filaments outside the envelope (cite: 2023A&A...677A..92V) and to smaller-scale spiral-like structures on the disk (cite: 2019Sci...366...90A). A free-fall streamer and the projection of its parabolic trajectory can be modeled as described in Sect. [9](#sec_parabolic_trajectory). However, when an in-midplane streamer interacts with the disk-like envelope, its infall velocity is decelerated, resulting in a spiral-like structure with a large $\Delta \phi$ (see definition in Sect. [4.2.1](#sec_hardsurface)). The slim morphology and much higher density of streamers in the inner few hundred au, compared to the global envelope, reflect the non-isotropic accretion characteristics of a young star as it interacts with its natal environment (cite: 2020A&A...635A..67H).

A streamer does not necessarily have the same specific angular momentum as the streams in the global envelope. Based on the different patterns of interaction between the streamers and the global envelope, we divide the streamers into two types: the in-midplane streamer and the off-midplane streamer (see panel (f) of Fig. [16](#fig_model_multipanel) for illustration). Before it hits the centrifugal barrier, the in-midplane streamer will experience continuous interaction with the disk-like envelope. Relatively slow shocks occur during the descent of the streamer within the inner envelope, resulting in a shock-endured slim segment. Shock tracers such as SO will be enhanced and excited on this shock-enduring segment (e.g., the P1 of DK Cha shown in Fig. [8](#fig_moms_dkcha)). This process increases the angle of incidence, thereby reducing the collision velocity when the streamer strikes the centrifugal barrier. The warm spot of SO$_2$, which requires stronger shocks than SO for excitation, will not necessarily appear at the foot of an in-midplane streamer.

In contrast, the off-midplane streamer will freely hit the surface of the disk or disk-like envelope near the centrifugal barrier. The angle of incidence tends to be small (panels (e–f) of Fig. [16](#fig_model_multipanel)), corresponding to a nearly head-on collision. There will be no SO-enhanced segment. Instead, a warm and compact spot of SO$_2$ is expected at its foot (see Sects. [3.1.3](#sec_warmspot) and [3.2.3](#sec_hotspot) for examples).

Overall, the constant-$J$ model offers a useful framework that highlights the key role of angular momentum in driving gas stream convergence and shock formation at/around the centrifugal barrier, leading to the formation of a flattened, disk-like inner envelope. The interactions between infalling streams and this structure influence mass transport and chemical processes around the disks of protostellar systems. This model provides a coherent interpretation consistent with our observations, helping to illuminate the complex dynamics of protostellar environments.

# Discussion

## Links between observations and models

The preceding sections have explored connections between models and observations; here, we examine this relationship in more detail. The introduction of a disk-like inner envelope is motivated by several considerations: (1) SO emission within the disk, inside the centrifugal ring, is very weak, whereas a weak but extended SO component is observed beyond the centrifugal ring; (2) Some streamers undergo significant deceleration before reaching the centrifugal barrier; (3) Certain streamers impact the midplane, producing warm spots outside the centrifugal barrier; (4) Long segments exhibiting broad SO and low-energy SO$_2$ emission exist beyond the centrifugal barrier, indicative of continuous shocks; (5) Outflows, common in protostellar systems, make it unlikely for gas flowing from the pole with very low angular momentum to directly collide with the inner disk; (6) An infalling SO layer may have been observed along the outflow boundary.

The original CMU model (Sect. [4.1](#sec_cmu)) proposed accretion shocks at the centrifugal barrier and on the disk surface inside it. In contrast, our model (Sect. [4.2](#sec_warpmodel)) suggests that shocks also occur at the surface of a disk-like inner envelope beyond the centrifugal barrier (Fig. [17](#fig_compare_models)). The actual scenario likely lies between these models, with some material flowing inward above the inner disk surface. Our model highlights the important role of shocks in structure formation at the disk/envelope scales, complementing scenarios observed at both larger scales (cite: 1998ApJ...504..223G; 2025arXiv250210897L; 2025arXiv250220458L) and smaller scales (cite: 2022ApJ...934L..20B). Although the specific manifestations may differ (e.g., accretion, outflow, turbulence), shocks are fundamental in shaping astrophysical environments across a wide range of scales.

Besides helping shape the disk-envelope structure, accretion shocks could also play a key role in resetting the chemistry of gas accreting onto the disk (Sect. [1](#sec_intro)). The shock location—whether inside or outside the centrifugal barrier—does not fundamentally alter this chemical “reset” concept, but it may affect the composition of the post-shock gas. Gas accreting onto the inner envelope likely experiences shocks under relatively weak UV radiation, while accretion shocks and stellar feedback (e.g., heating, UV radiation) may occur at separate stages. This is supported by the two rings seen in L1527’s SO PV map (Sect. [3.3](#sec_L1527)). In contrast, gas falling directly onto the disk may encounter shocks and stellar feedback simultaneously, potentially leading to different chemical outcomes (cite: 2021A&A...653A.159V; 2023A&A...675A..86K). Importantly, under the CMU model, most material undergoes strong shocks before entering the disk, whereas in our model, a significant fraction flows through the inner envelope and may avoid strong shocks. Observations of the edge-on source L1527 support this, with strong SO emission confined to disk surfaces (cite: 2014Natur.507...78S; 2017MNRAS.467L..76S). This is consistent with simulations showing that much of the envelope material may accrete smoothly without strong discontinuities (cite: 2024A&A...686A.253M). Thus, material entering the disk via the inner envelope may be a mixture of both “modified” and “reset” gas (Sect. [1](#sec_intro)). While a detailed chemical study is beyond the scope of this work, these findings provide a foundation for future investigations into how much the chemistry of infalling gas is reset before incorporation into planet-forming disks.

## Beyond the observations and models

Observationally, this work focuses on the disk-envelope scale. Gas in the inner envelope shows significant infall motion (Sect. [3.1.4](#sec_irs63_envelope)), resulting in a surface density much lower than that of the disk traced by millimeter continuum emission dominated by Keplerian rotation. This likely explains why the millimeter continuum size approximately coincides with the inner boundary of the centrifugal barrier traced by the SO ring. While CO (2–1) and SO lines effectively trace emission near the outflow boundaries, probing the inner envelope regions beneath the surface remains challenging. Observations of lower-$J$ transitions, such as CO ($J=1$–$0$) and N$_2$H$^+$, may better constrain these inner layers (cite: 2021ApJ...908..108F), motivating future studies to focus on such tracers.

As discussed in Sect. [4.2.3](#sec_streamer_onoff), streamers can exhibit specific angular momenta that differ significantly from the global envelope, with some possibly accreting directly onto the disk inside the centrifugal barrier. Due to limited spatial resolution and sample size, this work primarily focuses on shock-related SO and SO$_2$ emission at and beyond the centrifugal barrier. In Oph IRS 63, the SO moment 2 map reveals a spiral-like, broad-line ‘S’ shape (Fig. [19](#fig_irs63_Smark)), which lacks a clear counterpart in the moment 0 map (Fig. [1](#fig_irs63_color_maps)). The PV diagram along this ‘S’ structure (Fig. [3](#fig_irs63_pvmaps_ringandS)a) shows two velocity components in the southeast segment, consistent with shocks confined to the inner envelope surface (Sect. [3](#sec_obsresults)). Given the similarity in clockwise spiraling between this ‘S’ shape and the streamers, this feature may trace accretion flows funneling material from the inner envelope onto the disk (cite: 2016A&A...590A..22H; 2019Sci...366...90A; 2020NatAs...4..142L).

Turning to the modeling aspect, this study does not include the effects of magnetic fields on streamer and envelope dynamics (cite: 2016ApJ...822...12H; 2019MNRAS.489.1719W; 2020MNRAS.491.2180M; 2023ASPC..534..317T; 2023ASPC..534..465L), nor does it explore the detailed nature of shock types (cite: 2015A&A...578A..63F). These factors could influence interpretations, especially given the current lack of B-field tracer data. Additionally, the sources examined here are primarily low- to intermediate-mass protostars. For massive young stellar objects, stronger stellar feedback and clustered environments (cite: 2019A&A...632A..57C; 2023ASPC..534..275O; 2024RAA....24b5009L) may expose infalling material to intense radiation before it reaches the centrifugal barrier, altering its dynamics and chemistry.

Despite these limitations, the good agreement between observations and our descriptive model suggests that the accretion shock framework remains a valid approach for understanding the disk-envelope interface in low- and intermediate-mass protostars. Moving forward, expanding observations to larger and more diverse samples—utilizing a variety of shock tracers and targeting protostars with different masses and inclination angles—will be essential for fully characterizing the physical and chemical processes associated with accretion shocks.

# Summary

In this work, we searched for and explained signatures of accretion shocks by examining the spectral line emission of SO and SO$_2$ observed by ALMA toward several nearby protostars at different inclination angles ($\theta_{\rm view}$). Streamers are commonly observed in these sources (Oph IRS 63 and DK Cha). SO emission tends to concentrate at the centrifugal barrier of the envelope, forming a ring-like structure (Oph IRS 63 and L1527). Outside the centrifugal barrier, SO emission is widely distributed or associated with streamers interacting with the envelopes. Warm spots or segments of SO$_2$ were detected at the feet of the streamers. We proposed a disk-like inner envelope model to consistently explain the locations and mechanisms of SO/SO$_2$-related accretion shocks. Below, we summarize the key conclusions of this work:

- In Oph IRS 63 ($\theta_{\rm view} \sim 45\ensuremath{^\circ}$), we found an SO$_2$ ring associated with the SO ring surrounding the inner protoplanetary disk. The SO/SO$_2$ ring traces the centrifugal barrier of the infalling envelope at a radius of $\sim 80$ au. Outside the SO/SO$_2$ rings, the velocity distribution of the weak and extended SO emission can be explained by a rotating-and-infalling inner envelope. Four spiral-like streamers are visible in the SO emission (denoted as S1 to S4). A warm spot of SO$_2$ (with $T_{\rm ex} \gtrsim 50$ K) is found at the foot of S3, and we suggest that S3 is an off-midplane streamer that violently hits the centrifugal barrier.

- In DK Cha ($\theta_{\rm view} \sim 20\ensuremath{^\circ}$), a long segment of $\sim 300$ au with broad-line (FWHM $\sim$ 4 km s$^{-1}$) emission of SO and SO$_2$ is observed. Two streamers are falling onto the segment, and we speculate that the interaction between the segment and the inner envelope is responsible for the enhancement of SO/SO$_2$. The segment and another streamer feed material into the central disk. A warm spot ($\sim 70$ K) and a possible hot spot ($\gtrsim 100$ K) of SO$_2$ are found at the feet of the streamers. The streamers are also visible in CO emission, located along the outer edges of the SO emission.

- In L1527 ($\theta_{\rm view} \sim 90\ensuremath{^\circ}$), the SO emission is consistent with prior observations (cite: 2014Natur.507...78S; 2017MNRAS.467L..76S), showing the shape of parallel slabs. This supports the idea that SO emission occurs in ring-like patterns at the surface of a disk or disk-like structure. An ‘X’ shape is seen in the SO PV map, which we interpret as two rings. The velocities of the two rings can be explained by Keplerian motion around a central mass of $\sim$0.5 $M_\ensuremath{\odot}$. The outer ring corresponds to the centrifugal barrier, as noted in the literature. The inner ring may trace the SO snowline. We also detect SO strips along the outer edges of the CO outflow boundaries, which can be reasonably modeled by free-fall trajectories, indicating likely interaction between the outflows and the large-scale envelope surfaces. We propose that there may be an infalling layer warping the outflow cavity, which endures mild shocks.

- The model proposed in this work suggests the presence of a disk-like inner envelope outside the centrifugal barrier, formed by the compression of constant-$J$ streams that partly acquire their angular momentum from outflows. While the centrifugal barrier follows Keplerian motion, the disk-like inner envelope exhibits both rotation and infall. Shocks at its surface contribute to the weak, extended SO emission observed beyond the centrifugal barrier. Streamers interacting with this inner envelope deviate from free-fall trajectories, enhancing SO and SO$_2$ emission in their inner regions. Midplane streamers experience continuous shocks, forming warm segments, whereas off-midplane streamers tend to create warm or hot spots due to more violent collisions. The model is consistent with various observational evidences presented in this work (e.g., sulfur ring, SO streamers, warm spots/segments, envelope motion, infalling layers around outflows).

Overall, SO and SO$_2$ are excellent tracers of accretion shocks around disks. The shock-related chemistry at the surfaces of the disk, the centrifugal barrier ring, and the disk-like inner envelope warrants special attention when studying the chemical and physical properties of protoplanetary disks.

X.L. acknowledges the support of the Strategic Priority Research Program of the Chinese Academy of Sciences under Grant No. XDB0800303, and the National Key R&D Program of China under Grant No. 2022YFA1603100. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.01411.S, #2023.1.00592.S, #2013.1.00708.S, #2019.A.00034.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We thank the anonymous referee for the constructive comments, which helped strengthen this work.

117 natexlab

(ref: 1987ApJ...312..788A) Adams, F. C., Lada, C. J., & Shu, F. H. 1987, ApJ, 312, 788

(ref: 1999ApJ...519..705A) Aikawa, Y., Umebayashi, T., Nakano, T., & Miyama, S. M. 1999, ApJ, 519, 705

(ref: 2015ApJ...808L...3A) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3

(ref: 2019Sci...366...90A) Alves, F. O., Caselli, P., Girart, J. M., et al. 2019, Science, 366, 90

(ref: 2022A&A...667A..20A) Artur de la Villarmois, E., Guzmán, V. V., Jørgensen, J. K., et al. 2022, A&A, 667, A20

(ref: 2019A&A...626A..71A) Artur de la Villarmois, E., Jørgensen, J. K., Kristensen, L. E., et al. 2019, A&A, 626, A71

(ref: 1997ApJ...487L..93B) Bachiller, R. & Pérez Gutiérrez, M. 1997, ApJL, 487, L93

(ref: 2010SPIE.7735E..08B) Bacon, R., Accardo, M., Adjali, L., et al. 2010, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7735, Ground-based and Airborne Instrumentation for Astronomy III, ed. I. S. McLean, S. K. Ramsay, & H. Takami, 773508

(ref: 2022ApJ...934L..20B) Bae, J., Teague, R., Andrews, S. M., et al. 2022, ApJL, 934, L20

(ref: 2016ARA&A..54..491B) Bally, J. 2016, ARA&A, 54, 491

(ref: 2019ApJ...870...76B) Banzatti, A., Pascucci, I., Edwards, S., et al. 2019, ApJ, 870, 76

(ref: 2016Natur.540..406B) Bjerkeli, P., van der Wiel, M. H. D., Harsono, D., Ramsey, J. P., & Jørgensen, J. K. 2016, Nature, 540, 406

(ref: 2004come.book..391B) Bockelée-Morvan, D., Crovisier, J., Mumma, M. J., & Weaver, H. A. 2004, in Comets II, ed. M. C. Festou, H. U. Keller, & H. A. Weaver, 391

(ref: 2000A&A...353.1101B) Bockelée-Morvan, D., Lis, D. C., Wink, J. E., et al. 2000, A&A, 353, 1101

(ref: 2023A&A...669A..53B) Booth, A. S., Ilee, J. D., Walsh, C., et al. 2023, A&A, 669, A53

(ref: 2024AJ....167..165B) Booth, A. S., Temmink, M., van Dishoeck, E. F., et al. 2024, AJ, 167, 165

(ref: 2007A&A...461.1037B) Brinch, C., Crapsi, A., Hogerheijde, M. R., & Jørgensen, J. K. 2007, A&A, 461, 1037

(ref: 2013A&A...559A..82B) Brinch, C. & Jørgensen, J. K. 2013, A&A, 559, A82

(ref: 2020A&A...633A.126B) Busch, L. A., Belloche, A., Cabrit, S., Hennebelle, P., & Commerçon, B. 2020, A&A, 633, A126

(ref: 1981Icar...48..353C) Cassen, P. & Moosman, A. 1981, Icarus, 48, 353

(ref: 1997ApJ...490..368C) Chiang, E. I. & Goldreich, P. 1997, ApJ, 490, 368

(ref: 2019A&A...632A..57C) Csengeri, T., Belloche, A., Bontemps, S., et al. 2019, A&A, 632, A57

(ref: 1983ApJ...264..485D) Draine, B. T., Roberge, W. G., & Dalgarno, A. 1983, ApJ, 264, 485

(ref: 2019MNRAS.490...50D) Drozdovskaya, M. N., van Dishoeck, E. F., Rubin, M., Jørgensen, J. K., & Altwegg, K. 2019, MNRAS, 490, 50

(ref: 2014MNRAS.445..913D) Drozdovskaya, M. N., Walsh, C., Visser, R., Harsono, D., & van Dishoeck, E. F. 2014, MNRAS, 445, 913

(ref: 2024A&A...689L...7D) Dutrey, A., Chapillon, E., Guilloteau, S., et al. 2024, A&A, 689, L7

(ref: 2019A&A...621A..75E) Eistrup, C. & Walsh, C. 2019, A&A, 621, A75

(ref: 2016JMoSp.327...95E) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95

(ref: 2010A&A...510A..72F) Fedele, D., van den Ancker, M. E., Henning, T., Jayawardhana, R., & Oliveira, J. M. 2010, A&A, 510, A72

(ref: 2020ApJ...896...37F) Feng, S., Codella, C., Ceccarelli, C., et al. 2020, ApJ, 896, 37

(ref: 2023ApJ...958...98F) Flores, C., Ohashi, N., Tobin, J. J., et al. 2023, ApJ, 958, 98

(ref: 2021ApJ...908..108F) Flores-Rivera, L., Terebey, S., Willacy, K., et al. 2021, ApJ, 908, 108

(ref: 2015A&A...578A..63F) Flower, D. R. & Pineau des Forêts, G. 2015, A&A, 578, A63

(ref: 2020AJ....160..270F) Francis, L., Johnstone, D., Herczeg, G., Hunter, T. R., & Harsono, D. 2020, AJ, 160, 270

(ref: 2013A&A...559A..96F) Freudling, W., Romaniello, M., Bramich, D. M., et al. 2013, A&A, 559, A96

(ref: 2011A&A...534A..99G) Garcia Lopez, R., Nisini, B., Antoniucci, S., et al. 2011, A&A, 534, A99

(ref: 2022A&A...658A.104G) Garufi, A., Podio, L., Codella, C., et al. 2022, A&A, 658, A104

(ref: 2015A&A...577L...2G) Gerin, M., Pety, J., Fuente, A., et al. 2015, A&A, 577, L2

(ref: 1999ApJ...517..209G) Goldsmith, P. F. & Langer, W. D. 1999, ApJ, 517, 209

(ref: 1998ApJ...504..223G) Goodman, A. A., Barranco, J. A., Wilner, D. J., & Heyer, M. H. 1998, ApJ, 504, 223

(ref: 2023ApJ...945...63H) Harada, N., Tokuda, K., Yamasaki, H., et al. 2023, ApJ, 945, 63

(ref: 2018ApJ...861...91H) Harris, R. J., Cox, E. G., Looney, L. W., et al. 2018, ApJ, 861, 91

(ref: 2023ApJ...951L..32H) Harsono, D., Bjerkeli, P., Ramsey, J. P., et al. 2023, ApJL, 951, L32

(ref: 2021A&A...646A..72H) Harsono, D., van der Wiel, M. H. D., Bjerkeli, P., et al. 2021, A&A, 646, A72

(ref: 2020A&A...635A..67H) Hennebelle, P., Commerçon, B., Lee, Y.-N., & Charnoz, S. 2020, A&A, 635, A67

(ref: 2016A&A...590A..22H) Hennebelle, P., Lesur, G., & Fromang, S. 2016, A&A, 590, A22

(ref: 2016ApJ...822...12H) Hincelin, U., Commerçon, B., Wakelam, V., et al. 2016, ApJ, 822, 12

(ref: 2023ApJ...956..120H) Hsu, S.-Y., Liu, S.-Y., Johnstone, D., et al. 2023, ApJ, 956, 120

(ref: 2019FrASS...6....3H) Hull, C. L. H. & Zhang, Q. 2019, Frontiers in Astronomy and Space Sciences, 6, 3

(ref: 2023NatAs...7..684K) Keyte, L., Kama, M., Booth, A. S., et al. 2023, Nature Astronomy, 7, 684

(ref: 2023A&A...675A..86K) Kristensen, L. E., Godard, B., Guillard, P., Gusdorf, A., & Pineau des Forêts, G. 2023, A&A, 675, A86

(ref: 2012A&A...542A...8K) Kristensen, L. E., van Dishoeck, E. F., Bergin, E. A., et al. 2012, A&A, 542, A8

(ref: 1969MNRAS.145..271L) Larson, R. B. 1969, MNRAS, 145, 271

(ref: 2007ApJ...659..499L) Lee, C.-F., Ho, P. T. P., Hirano, N., et al. 2007, ApJ, 659, 499

(ref: 2020NatAs...4..142L) Lee, C.-F., Li, Z.-Y., & Turner, N. J. 2020, Nature Astronomy, 4, 142

(ref: 2021ApJ...907L..41L) Lee, C.-F., Tabone, B., Cabrit, S., et al. 2021, ApJL, 907, L41

(ref: 2023ASPC..534..465L) Lesur, G., Flock, M., Ercolano, B., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 465

(ref: 2020ApJ...900...15L) Liang, L., Johnstone, D., Cabrit, S., & Kristensen, L. E. 2020, ApJ, 900, 15

(ref: 2025arXiv250220458L) Liu, X. 2025, arXiv e-prints, arXiv:2502.20458

(ref: 2025arXiv250210897L) Liu, X., Liu, T., Li, P.-S., et al. 2025, arXiv e-prints, arXiv:2502.10897

(ref: 2022ApJS..263...13L) Liu, X., Liu, T., Shen, Z., et al. 2022, ApJS, 263, 13

(ref: 2024RAA....24b5009L) Liu, X., Liu, T., Zhu, L., et al. 2024, Research in Astronomy and Astrophysics, 24, 025009

(ref: 2021ApJ...912..148L) Liu, X. C., Wu, Y., Zhang, C., et al. 2021, ApJ, 912, 148

(ref: 2020MNRAS.491.2180M) Machida, M. N., Hirano, S., & Kitta, H. 2020, MNRAS, 491, 2180

(ref: 2018A&A...618L...3M) Manara, C. F., Morbidelli, A., & Guillot, T. 2018, A&A, 618, L3

(ref: 2015PASP..127..266M) Mangum, J. G. & Shirley, Y. L. 2015, PASP, 127, 266

(ref: 2021PASP..133h5001M) Massardi, M., Stoehr, F., Bendo, G. J., et al. 2021, PASP, 133, 085001

(ref: 2024A&A...686A.253M) Mauxion, J., Lesur, G., & Maret, S. 2024, A&A, 686, A253

(ref: 2013A&A...550A..36M) McElroy, D., Walsh, C., Markwick, A. J., et al. 2013, A&A, 550, A36

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2017ApJ...839...47M) Miura, H., Yamamoto, T., Nomura, H., et al. 2017, ApJ, 839, 47

(ref: 2016ApJ...823L..41M) Mousis, O., Ronnet, T., Brugger, B., et al. 2016, ApJL, 823, L41

(ref: 2005JMoSp.232..213M) Müller, H. S. P. & Brünken, S. 2005, Journal of Molecular Spectroscopy, 232, 213

(ref: 2001A&A...370L..49M) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49

(ref: 2011ARA&A..49..471M) Mumma, M. J. & Charnley, S. B. 2011, ARA&A, 49, 471

(ref: 1994ApJ...428..170N) Neufeld, D. A. & Hollenbach, D. J. 1994, ApJ, 428, 170

(ref: 2015ApJ...801..121N) Nisini, B., Santangelo, G., Giannini, T., et al. 2015, ApJ, 801, 121

(ref: 2020A&A...636A..38N) Nony, T., Motte, F., Louvet, F., et al. 2020, A&A, 636, A38

(ref: 2023ASPC..534..275O) Offner, S. S. R., Moe, M., Kratter, K. M., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 275

(ref: 2023ApJ...951....8O) Ohashi, N., Tobin, J. J., Jørgensen, J. K., et al. 2023, ApJ, 951, 8

(ref: chatgpt2024) OpenAI. 2024, ChatGPT: A Conversational Language Model, <https://chat.openai.com/>, accessed: 2024-10-08

(ref: 2021ApJ...921...12O) Oya, Y., Watanabe, Y., López-Sepulcre, A., et al. 2021, ApJ, 921, 12

(ref: 2017ApJ...844...71P) Penteado, E. M., Walsh, C., & Cuppen, H. M. 2017, ApJ, 844, 71

(ref: 1998JQSRT..60..883P) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: 2020NatAs...4.1158P) Pineda, J. E., Segura-Cox, D., Caselli, P., et al. 2020, Nature Astronomy, 4, 1158

(ref: 2011A&A...527A..13P) Podio, L., Eislöffel, J., Melnikov, S., Hodapp, K. W., & Bacciotti, F. 2011, A&A, 527, A13

(ref: 2006AJ....131.2921R) Ridge, N. A., Di Francesco, J., Kirk, H., et al. 2006, AJ, 131, 2921

(ref: 2015A&A...575A..19R) Riviere-Marichalar, P., Bayo, A., Kamp, I., et al. 2015, A&A, 575, A19

(ref: 2016A&A...594A..59R) Riviere-Marichalar, P., Merı́n, B., Kamp, I., Eiroa, C., & Montesinos, B. 2016, A&A, 594, A59

(ref: 2022ApJ...925...12S) Sai, J., Ohashi, N., Maury, A. J., et al. 2022, ApJ, 925, 12

(ref: 2017MNRAS.467L..76S) Sakai, N., Oya, Y., Higuchi, A. E., et al. 2017, MNRAS, 467, L76

(ref: 2014Natur.507...78S) Sakai, N., Sakai, T., Hirota, T., et al. 2014, Nature, 507, 78

(ref: 2020Natur.586..228S) Segura-Cox, D. M., Schmiedeke, A., Pineda, J. E., et al. 2020, Nature, 586, 228

(ref: 1977ApJ...214..488S) Shu, F. H. 1977, ApJ, 214, 488

(ref: 2025ApJ...981L..30S) Speedie, J., Dong, R., Teague, R., et al. 2025, ApJL, 981, L30

(ref: 2016MNRAS.462S..99T) Taquet, V., Furuya, K., Walsh, C., & van Dishoeck, E. F. 2016, MNRAS, 462, S99

(ref: 2012Natur.492...83T) Tobin, J. J., Hartmann, L., Chiang, H.-F., et al. 2012, Nature, 492, 83

(ref: 2007ApJ...671.1813T) Torres, R. M., Loinard, L., Mioduszewski, A. J., & Rodrı́guez, L. F. 2007, ApJ, 671, 1813

(ref: 2023ASPC..534..317T) Tsukamoto, Y., Maury, A., Commercon, B., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 317

(ref: 2016MNRAS.463.3563T) Tuan-Anh, P., Nhung, P. T., Hoai, D. T., et al. 2016, MNRAS, 463, 3563

(ref: 2020A&A...640A..19T) Tychoniec, Ł., Manara, C. F., Rosotti, G. P., et al. 2020, A&A, 640, A19

(ref: 1976ApJ...210..377U) Ulrich, R. K. 1976, ApJ, 210, 377

(ref: 2022A&A...667A..12V) Valdivia-Mena, M. T., Pineda, J. E., Segura-Cox, D. M., et al. 2022, A&A, 667, A12

(ref: 2023A&A...677A..92V) Valdivia-Mena, M. T., Pineda, J. E., Segura-Cox, D. M., et al. 2023, A&A, 677, A92

(ref: 2024A&A...682A..78V) van Gelder, M. L., Ressler, M. E., van Dishoeck, E. F., et al. 2024, A&A, 682, A78

(ref: 2021A&A...653A.159V) van Gelder, M. L., Tabone, B., van Dishoeck, E. F., & Godard, B. 2021, A&A, 653, A159

(ref: 2006A&A...454L..75V) van Kempen, T. A., Hogerheijde, M. R., van Dishoeck, E. F., et al. 2006, A&A, 454, L75

(ref: 2023ApJ...951...10V) van’t Hoff, M. L. R., Tobin, J. J., Li, Z.-Y., et al. 2023, ApJ, 951, 10

(ref: 2010A&A...519A..28V) Visser, R. & Dullemond, C. P. 2010, A&A, 519, A28

(ref: 2009A&A...495..881V) Visser, R., van Dishoeck, E. F., Doty, S. D., & Dullemond, C. P. 2009, A&A, 495, 881

(ref: 2005A&A...437..149W) Wakelam, V., Ceccarelli, C., Castets, A., et al. 2005, A&A, 437, 149

(ref: 1997A&A...327.1194W) Whittet, D. C. B., Prusti, T., Franco, G. A. P., et al. 1997, A&A, 327, 1194

(ref: 2019MNRAS.489.1719W) Wurster, J., Bate, M. R., & Price, D. J. 2019, MNRAS, 489, 1719

(ref: 2015A&A...576A.109Y) Yıldız, U. A., Kristensen, L. E., van Dishoeck, E. F., et al. 2015, A&A, 576, A109

(ref: 2024ApJ...966..207Z) Zhang, Z. E., Sakai, N., Ohashi, S., et al. 2024, ApJ, 966, 207

(ref: 2009ApJ...694.1045Z) Zhu, Z., Hartmann, L., & Gammie, C. 2009, ApJ, 694, 1045

(ref: 2020A&A...633A..51Z) Zucker, C., Speagle, J. S., Schlafly, E. F., et al. 2020, A&A, 633, A51

# Fitting an elliptical ring

We modeled the ring-like emission as an elliptical Gaussian ring characterized by the intensity profile $$\begin{equation}
I(x,y) =  H \exp\left[-\frac{1}{2}\left(\frac{r(x,y) - 1}{\sigma}\right)^2\right] + C,
\end{equation}$$ where $C$ is the average background intensity, $H$ is the peak intensity of the ring, and $\sigma$ represents the ring width normalized by the semi-major axis. The normalized elliptical radius $r(x,y)$ is defined as $$\begin{equation}
r(x,y) = \sqrt{\left(\frac{x'}{a}\right)^2 + \left(\frac{y'}{b}\right)^2},
\end{equation}$$ where $a$ and $b$ are the semi-major and semi-minor axes of the ellipse, respectively. The rotated coordinates $(x', y')$ are obtained by rotating the pixel coordinates $(x,y)$ about the ring center $(x_0,y_0)$ by an azimuth angle $\phi_{\rm view}$: $$\begin{equation}
\begin{pmatrix} x' \\ y' \end{pmatrix}
= 
\begin{pmatrix}
\cos \phi_{\rm view} & \sin \phi_{\rm view} \\
-\sin \phi_{\rm view} & \cos \phi_{\rm view}
\end{pmatrix}
\begin{pmatrix}
x - x_0 \\
y - y_0
\end{pmatrix}.
\end{equation}$$ The parameter set $\mathbf{p} = (x_0, y_0, a, b, \phi_{\rm view}, \sigma, H, C)$ was determined by fitting the model to the observed 2D emission map using a non-linear least squares optimization method. Initial guesses were based on visual inspection of the data. Fitting was performed using the `curve_fit` routine from the `scipy` Python package, and uncertainties on the fitted parameters were estimated from the covariance matrix, with errors reported as one standard deviation (1$\sigma$).

Applying this procedure to the moment 0 map of the SO emission in Oph IRS 63 yields the following best-fit parameters: semi-major axis $a = 0.50 \pm 0.01$ arcsec, semi-minor axis $b = 0.38 \pm 0.01$ arcsec, azimuth angle $\phi_{\rm view} = 52.93^\circ \pm 1.14^\circ$, normalized ring width $\sigma = 0.52 \pm 0.01$, peak intensity $H = 50 \pm 0.5$ mJy beam$^{-1}$ km s$^{-1}$, and background intensity $C = 20 \pm 0.5$ mJy beam$^{-1}$ km s$^{-1}$. The fitted model (Figure [18](#fig:ringfit)) successfully reproduces the elliptical morphology of the ring emission, enabling quantitative characterization of its geometric and intensity structure. The inclination angle is estimated as $\theta_{\rm view} = \arccos(b/a) \approx 40.5^\circ \pm 1^\circ$. We note, however, that the presence of streamers and deviations from a perfectly elliptical ring may introduce systematic uncertainties not captured in the formal error estimates. The interaction between the spiral-like features—particularly S4—and the SO ring becomes more evident in the residual map after subtracting the fitted ring component (bottom panel of Fig. [18](#fig:ringfit)).

![](IRS63_ellipsefit.pdf)

# Extra images

Images of observations referenced in this work but not included in the main figures will be presented here (Figs. [19](#fig_irs63_Smark), [20](#fig_dkcha_spw33spe), and [21](#fig_L1527_SO2)).

![](IRS63_mom2_Smark.pdf)

![](DK_Cha_hotspot_spw33_spe.pdf)

![](L1527_so2.pdf)

# Projection of parabolic trajectories

The parallel projection of a parabolic curve in 3D space onto a 2D plane still results in a parabolic curve. In the simplest case ($\theta_0 = \theta_{\rm view} = \phi_0 = \theta_{\rm view} = 0^\circ$, see Fig. [22](#fig_stream_cartoon)), the standard parabolic trajectory of a free-fall stream can be expressed as $$\begin{equation}
    \frac{x}{R_{\rm C}} = \frac{1}{2} \left( \frac{y}{R_{\rm C}} \right)^2
\end{equation}$$ with $z=0$, $y < -R_{\rm C}$ in the clockwise case, and $y > R_{\rm C}$ in the counterclockwise case. The free-fall velocity at $R_{\rm C}$ along the parabolic curve is $$\begin{equation}
    v_{\rm C} = \left( \frac{2GM_\star}{R_{\rm C}} \right)^{1/2}.
\end{equation}$$ At any given point on the standard parabolic trajectory, the projected velocities along the $x$ and $y$ directions are given by $$\begin{equation}
    v_x = \frac{y}{\sqrt{y^2 + R_{\rm C}^2}} \left( \frac{r}{R_{\rm C}} \right)^{-1/2} v_{\rm C}
\end{equation}$$ and $$\begin{equation}
    v_y = \frac{R_{\rm C}}{\sqrt{y^2 + R_{\rm C}^2}} \left( \frac{r}{R_{\rm C}} \right)^{-1/2} v_{\rm C},
\end{equation}$$ respectively, with $r = \sqrt{x^2 + y^2}$, and $v_z = 0$.

Denote $\mathcal{M}^{j,k}$ as the value at the $j_{\rm th}$ row and $k_{\rm th}$ column of a matrix $\mathcal{M}$. Here, we define three matrices $\mathcal{R}_i$ for $i = 1, 2, 3$. For $i = 2$, the matrix is given by $$\begin{equation}
\mathcal{R}_i(x) = \left|
\begin{array}{ccc}
\cos(x) & 0 & -\sin(x)  \\
0 & 1 & 0 \\
\sin(x) & 0 & \cos(x)
\end{array} \right|.
\end{equation}$$ That is, $R_i^{i,k} = R_i^{k,i} = 0$ for $k \neq i$, and $R_i^{i,i} = 1$. Similarly, $R_1$ and $R_3$ can be constructed. Denote $\mathcal{A} = (x, y, z)$ as the points along the parabolic trajectory defined above. Let $$\begin{equation}
\mathcal{R} = \mathcal{R}_3(\phi_{\rm view}) \cdot \mathcal{R}_1\left(\theta_{\rm view}\right) \cdot \mathcal{R}_3(\phi_0) \cdot \mathcal{R}_2\left(\frac{\pi}{2}-\theta_0\right).
\end{equation}$$ The transformation matrix $\mathcal{R}$ can generate the projection of any parabolic trajectory in 3D space through $$\begin{equation}
\mathcal{A}_{\rm view}^{\rm T} = \mathcal{R} \cdot \mathcal{A}^{\rm T}.
\end{equation}$$ Similarly, the projection of the velocity along a parabolic trajectory, denoted as $\mathcal{V} = (v_x, v_y, v_z)$, can be expressed as $$\begin{equation}
   \mathcal{V}_{\rm view}^{\rm T} = \mathcal{R} \cdot \mathcal{V}^{\rm T}.
\end{equation}$$ The observable parameters are the projected components $x$, $y$, and $v_z$.

![](envelope_stream_cartoon.pdf)

For fixed values of $\theta_{\rm view}$ and $\phi_{\rm view}$, the free parameters of the trajectory ($\mathcal{A}_{\rm view}$) are $\theta_0$, $\phi_0$, and $R_{\rm C}$. The values of $\theta_{\rm view}$ and $\phi_{\rm view}$ can typically be determined from the morphology of the disk. Note that these values constrain the trajectory to intersect the midplane at a radius of $R_{\rm C}$. To obtain a parabolic curve without any constraints imposed by the morphology of the disk, the values of $\theta_{\rm view}$ and $\phi_{\rm view}$ may vary. Only four free parameters are needed to describe all parabolic curves with a fixed focus in 3D space: two parameters to define the plane of the curve, one to specify the axis of the parabola within the plane, and one to determine the focal length. By adopting different values for $(\theta_0, \phi_0, R_{\rm C}, \theta_{\rm view})$, we can generate all such parabolic curves. Fortunately, there are relatively simple methods for determining $\phi_{\rm view}$, such as measuring the large-scale velocity gradient or the direction of the outflows.

# Details of equations

For the CMU model (cite: 1976ApJ...210..377U; 1981Icar...48..353C), to calculate the density $\rho$ (Eq. [\[eq_rho_cmu\]](#eq_rho_cmu)) at a given point $(r, \theta)$, the initial inclination angle of the streamline, $\theta_0$, should first be calculated from Eq. [\[eq_sl\]](#eq_sl). This is a cubic equation in one variable. To solve Eq. [\[eq_sl\]](#eq_sl), ChatGPT (cite: chatgpt2024) provides the solution $$\begin{equation}
\mu_0 = \left\{ 
\begin{aligned}
&2\sqrt{\frac{-p}{3}}\cos\left(\arccos\left( \frac{3q}{2p\sqrt{-p/3}}
\right)/3\right)\ {\rm for}\ D<0, \\
&\left(-\frac{q}{2}+\sqrt{\frac{D}{108}}\right)^{\frac{1}{3}}+\left(-\frac{q}{2}-\sqrt{\frac{D}{108}}\right)^{\frac{1}{3}} \ {\rm for}\ D>0.
\end{aligned}
\right.  
\end{equation}$$ Here, $\mu=\cos(\theta)$, $\mu_0=\cos(\theta_0)$, $p=r/R_{\rm C}^{\rm mid}-1$, $q=-\mu r/R_{\rm C}^{\rm mid}$, and $D=4p^3+27q^2$.

For the constant-$J$ model (Sect. [4.2.1](#sec_hardsurface)), along a trajectory with $\theta_0 \neq 0\ensuremath{^\circ}$, the azimuthal angle ($\phi$) can be expressed as a function of $r$ as $$\begin{equation}
 \label{eq_phi}
\phi = \phi_0 \pm \arctan\left(  \frac{\sqrt{2r/R_{\rm C}-1}}{(r/R_{\rm C}-1)\sin(\theta_0)} \right).
\end{equation}$$ For any parabolic trajectory, when viewed from the pole, the increment of the azimuthal angle of the trajectory ($\Delta(\phi) = |\phi_0 - \phi|$) will always be $\leq 90^\circ$. However, when the line of sight is offset from the pole (even with a small $\theta_{\rm view}$), the increment of the projected azimuthal angle ($\Delta(\phi_{\rm proj})$) in some cases can be $\sim 180^\circ$ for a streamline with a small $\theta_0$. Therefore, in principle, $\Delta(\phi)$ can have an arbitrary value. Fortunately, if we constrain the trajectory to the midplane ($\theta_0 = 90^\circ$), we obtain the following constraint on $\Delta(\phi_{\rm proj})$: $$\begin{equation}
\Delta(\phi_{\rm proj})  \leq 2\arctan\left( \frac{1}{\cos(\theta_{\rm view})}\right).
\label{eq_phi_incre}
\end{equation}$$ This can help quickly check whether a curved structure can be explained by a free-fall stream that flows in the midplane of the disk (Sect. [3.1.1](#sec_irs63_ring_steamer)).

In panel (b) of Fig. [3](#fig_irs63_pvmaps_ringandS), the PV curve of a rotating ring is given by the following equations. The arc length of an ellipse is $$\begin{equation}
L(\phi) = a \cdot E\left(\phi + \frac{\pi}{2}, k\right) - a \cdot E\left(\frac{\pi}{2}, k\right). \label{eq_ellip_arclength}
\end{equation}$$ Here, $k = \sin(\theta_{\rm view})$, $a$ is the semi-major axis length, $E$ is the incomplete elliptic integral of the second kind, and $\phi$ is the azimuthal angle starting from one of the endpoints of the major axis. The projected velocity is expressed as $$\begin{equation}
V_{\rm proj} = V_{\rm rot} \cos(\phi) \sin(\theta_{\rm view}) + V_{\rm sys}. \label{eq_ellip_vproj}
\end{equation}$$ Here, $V_{\rm rot}$ is the rotational speed, and $V_{\rm sys}$ is the systemic velocity of the ring.

# Calculation of column density

The column density of a species in the upper-level state ($N_u$) of a transition is (cite: 2015PASP..127..266M) $$\begin{equation}
    \frac{N_{\rm u}}{g_{\rm u}} = \frac{3k}{8\pi^3f_{\rm rest} S_{ij}\mu^2} \int T_{r} dV
\end{equation}$$ in the optically thin limit. Here, $k$ is the Boltzmann constant, $T_{r}$ is the brightness temperature, $g_{\rm u}$ is the upper-level degeneracy, and Debye$^2$ can be expressed in cgs unit as $10^{-36}\ \rm cm{^5} g^1\ s^{-2}$. If $T_{r}$ is not small in comparison to the excitation temperature ($T_{\rm ex}$), a correction factor ($f_{\tau}$) should be applied, $$\begin{equation}
    f_{\tau} = \frac{\tau}{1-\exp(-\tau)}
\end{equation}$$ with $$\begin{equation}
    \tau = -\ln\left(1-\frac{T_r^{\rm peak}}{T_{\rm ex}} \right).
\end{equation}$$ Here, $T_r^{\rm peak}$ is the peak value of the spectrum in brightness temperature. The total column density of the species can be calculated through $$\begin{equation}
    N = N_{\rm u} \frac{Q(T_{\rm ex})}{g_{\rm u}} \exp\left( \frac{E_{\rm u}}{T_{\rm ex}} \right). \label{Eq_N_total}
\end{equation}$$ Here, $Q(T_{\rm ex})$ is the partition function, which can be interpolated from the tabulated values available online (cite: 2001A&A...370L..49M), and $E_{\rm u}$ is the upper-level energy. Eq. [\[Eq_N_total\]](#Eq_N_total) yields (cite: 1999ApJ...517..209G) $$\begin{equation}
    \ln\left( \frac{N_{\rm u}}{g_{\rm u}} \right)=\ln\left( \frac{N}{Q(T_{\rm Tex})} \right) - \frac{E_{\rm u}}{T_{\rm ex}}. 
\end{equation}$$ If multiple transitions are available, the data in the $(E_{\rm u},\ \ln\left( \frac{N_{\rm u}}{g_{\rm u}} \right))$ space represent the rotational diagram. Linear fitting of the data yields the values of $N$ and $T_{\rm ex}$.

# Emission along outflow boundaries

![](L1527_pv_meanspec.pdf)

The outflow boundaries are manually drawn on the moment 0 map of CO (2–1) of L1527 (Fig. [14](#fig_L1527_cavity)). To obatin smoothed boundary lines, cubic interpolation is then applied to the manually selected points along the boundaries (see the resultant black lines in Fig. [14](#fig_L1527_cavity)).

## Narrow-line characteristics

The upper panel of Fig. [23](#fig:lw_sw) is identical to Fig. [14](#fig_L1527_cavity), showing the SO emission along the SW boundary of L1527 in the PV map. We denote $V_0(r)$ as the fitted free-fall stream velocity in PV space. For each radius $r$ within the main body of the SW region, enclosed by the black rectangle in the upper panel of Fig. [23](#fig:lw_sw), the spectrum along velocity $V$ is resampled by subtracting $V_0(r)$ from the velocity axis. This resampled spectrum is denoted as $S_r$. The spectrum $S_r$ is very narrow in line width (FWHM $\sim 0.44$ km s$^{-1}$), confirming the narrow-line feature of the SO strip and the good match with the modeled velocity distribution (dotted white line in Fig. [23](#fig:lw_sw)). The stacked spectrum along the SW direction is obtained by combining all $S_r$ over the radius $r$. The lower panel of Fig. [23](#fig:lw_sw) displays the stacked spectrum and its Gaussian fit, yielding a line width (FWHM) of $0.44 \pm 0.05$ km s$^{-1}$. The SO emission along the SE–NW direction (Fig. [14](#fig_L1527_cavity)) is also clearly visible in the PV map (Fig. [24](#fig:lw_se_nw)), showing similarly narrow line widths.

![](L1527_pv_meanspec_segments.pdf)

## Emission along transverse direction

A line on a 2-D map, such as the outflow boundary, is denoted by a series of points $(x_i, y_i)$. The transverse direction at the $i_{\rm th}$ point along this line is computed as $$\begin{equation}
    \phi_{\rm trans} = \arctan\left( \frac{y_{i+1} - y_{i-1}}{x_{i+1} - x_{i-1}} \right) + \frac{n}{2}\pi,
\end{equation}$$ where $n = 1$ or $3$ is chosen to ensure that the transverse arrows point inward toward a specific direction, such as the outflow cavity (Fig. [14](#fig_L1527_cavity)).

For the outflow boundary lines of L1527, we first calculate the transverse direction using the method described above. Emission profiles are then extracted along these transverse directions from the moment 0 maps. For both SO and CO, the resulting profiles—averaged over all transverse cuts—exhibit clearly spatially separated Gaussian components. We denote the mean transverse offset of each Gaussian component as $\mu$, with its associated uncertainty represented by $\sigma_\mu$. To quantify the significance of the spatial separation between the CO and SO emission, we compute the $t$-statistic as $$\begin{equation}
    t{\rm -stat} = \frac{\left| \mu^{\rm CO} - \mu^{\rm SO} \right|}{ \sqrt{  \sigma^{2}_{\mu^{\rm CO}} + \sigma^{2}_{\mu^{\rm SO}} } }.
\end{equation}$$ Table [2](#tab_L1527_offset) lists the measured transverse separations between the SO and CO emission for the four outflow boundaries in L1527, as illustrated in Fig. [15](#fig_so_co_offset).

| Region | $\mu^{\mathrm{SO}}$ ($\ensuremath{''}$) | $\mu^{\mathrm{CO}}$ ($\ensuremath{''}$) | $\mu^{\mathrm{CO}} - \mu^{\mathrm{SO}}$ ($\ensuremath{''}$) | $t$-stat |
|:---|:--:|:--:|:--:|:--:|
| NE | $-0.18 \pm 0.03$ | $0.60 \pm 0.04$ | $0.78 \pm 0.05$ | 15.3 |
| NW | $-0.09 \pm 0.06$ | $0.75 \pm 0.03$ | $0.84 \pm 0.06$ | 14.2 |
| SE | $0.14 \pm 0.13$ | $0.63 \pm 0.03$ | $0.48 \pm 0.13$ | 3.7 |
| SW | $-0.46 \pm 0.03$ | $0.30 \pm 0.04$ | $0.75 \pm 0.05$ | 15.0 |

: Separation between the SO and CO emission along the transverse directions of the outflow boundaries in L1527 (Fig. [15](#fig_so_co_offset)).

*Note.* See Appendix [12.2](#sect_appendix_separation) for the definitions of $\mu$ and the $t$-statistic.

[^1]: <https://casa.nrao.edu/>

[^2]: <https://almascience.eso.org/aq>

[^3]: The deconvolution of 2D Gaussians can be performed using the Python package *radio_beam* (<https://radio-beam.readthedocs.io/en/latest/>).

</paper>

Write the methods card for this paper.