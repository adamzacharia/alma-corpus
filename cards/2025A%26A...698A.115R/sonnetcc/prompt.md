# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...698A.115R\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...698A.115R",
 "title": "Radial variations in the nitrogen, carbon, and hydrogen fractionation in the PDS 70 planet-hosting disk",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Rampinelli, L.",
 "n_authors": 11,
 "arxiv_id": "2504.03833",
 "doi": "10.1051/0004-6361/202554172",
 "alma_projects_linked_by_archive": [
  "2019.1.01619.S",
  "2022.1.01695.S"
 ]
}
```

Paper text:
<paper>
# Radial variations in nitrogen, carbon, and hydrogen fractionation in the PDS 70 planet-hosting disk

# Introduction

The process of planet formation is expected to leave imprints on the natal environment, i.e. the protoplanetary disk, such as dust substructures (cite: andrews2018disk; sierra2021molecules; benisty2022optical), kinematic deviations in the rotation pattern of the gas (cite: perez2015planet; pinte2022kinematic; izquierdo2023maps), or chemical signatures (cite: cleeves2015indirect; law2023so; booth2023sulphur). Thanks to the incredible capabilities of both ground based facilities and space missions, a large variety of indirect evidence of ongoing planet formation in protoplanetary disks has been presented, including the first multi-wavelength direct detection of two accreting gas giants in the transition disk around PDS 70 (cite: keppler2018discovery; haffert2019two; benisty2021circumplanetary; zhou2021hubble).

The first chemical inventory of the PDS 70 disk (cite: bib:facchini2021chemical) and recent high resolution line emission observations (cite: rampinelli2024) showed a complex structured emission morphology of molecular tracers, highlighting the strong link between forming planets and their natal environment. In particular, most of the molecules show a ring-shaped emission co-located with the cavity wall and the peak in the scattered light from $\mu$m dust (cite: keppler2018discovery), which is consistent with the presence of a deep gas gap in the PDS 70 disk (cite: keppler2019highly; portilla2023constraining; law2024mapping), and feeds back into the chemical makeup of the planets that are forming (cite: cridland2023planet; leemker2024chemistry; Hsu2024pds70b).

![](images/M0_contours_HCN.png)

Multiple aspects of disk chemistry are linked to the process of planet formation (cite: oberg2021astrochemistry; oberg2023protoplanetary), such as location of snowlines (cite: oberg2011effect; okuzumi2019nonsticky), ratios of the main elements H, C, O, and N (cite: cridland2020connecting; drazkowska2023planet; jiang2023chemical), or isotopic ratios (cite: altwegg2019cometary; nomura2022isotopic). The latter can be an efficient tool to trace back the origin of planetary material, as it stores important markings of the history of gas and solids from the molecular cloud, down to rocky cores and planetary atmospheres building in protoplanetary disks (cite: nomura2022isotopic). Isotopic levels in solids and gas have been used to reconstruct the origin of volatiles in Solar System objects (cite: morbidelli2000source; aleon2010multiple; marty2012earth; ceccarelli2014deuterium; albertsson2014chemodynamical; altwegg2019cometary). Isotopic ratios of molecules are primarily set when molecules form, but various environmental conditions during the timeline of planet formation can reset or alter these values: this is highlighted by the large range spanned by isotopic ratios in different Solar System bodies, particularly for D/H and / (cite: nomura2022isotopic). The first measurement of / ratio for a brown dwarf atmosphere was presented by (cite: barrado2023), showing a value of $\sim670$, which is consistent with star-like formation by gravitational collapse. This result is also carving the path towards direct isotopologue ratios measurements in exoplanetary atmospheres. In particular, a measurement of / has been presented for the first time for exoplanetary atmospheres (cite: zhang202113co; gandhi2023), showing values lower than the ISM one.

These recent breakthroughs show the potential of isotopic imprints not only to trace the origins of the solar system, but also of exoplanets. In this context, direct constraints on the isotopic ratios in the protoplanetary disk stage, where planets build their cores, and accrete their atmospheres, are fundamental. Disk-integrated isotopologue ratios have been achieved in a variety of molecular tracers, including CO, HCN, CN, , and (cite: smith2009high; oberg2012evidence; guzman2015cyanide; zhang2017mass; huang2017alma; guzman2017; hily-blant2017; hily-blant2019multiple; hily2019multiple; yoshida2022; yoshida2024; bergin2024). These results provided first insights on the main chemical processes driving fractionation in disks: for example, both warm and cold gas-phase deuteration pathways were suggested to take place in disks, while isotope selective photodissociation was proposed to play a crucial role for the nitrogen fractionation (see (cite: nomura2022isotopic) for a recent review). Moreover, a first comparison with earlier and later stages of star and planet formation revealed the importance of comparing isotopologue ratios extracted from the same molecule, since fractionation processes can lead to very different isotope ratios in different tracers (cite: bergin2024). Finally, these disk-integrated results already show important deviations from the ISM isotopic ratios.

On the other hand, disk-integrated ratios do not fully capture the chemical complexity of protoplanetary disks, which is expected to induce spatial variations of isotopic ratios as different fractionation processes dominate at different scales and disk regions. Radially resolved isotopologue ratios were extracted in the MAPS sample for DCN/HCN (cite: cataldi2021molecules), for / in the TW Hya (cite: hily2019multiple), and the V4046 Sgr ((cite: nomura2022isotopic), Guzmán et al. in prep.) disks, and for / in the TW Hya disk (cite: furuya2022detection).

In this work we present the radial profile of nitrogen, carbon, and hydrogen fractionation of the HCN molecule in the PDS 70 disk, where two protoplanets are accreting their atmospheres. In Section [2](#sec:observations) we present ALMA line emission observations we analyzed. In Section [3](#sec:column) we describe how we reconstructed the radial profiles of the column density of the HCN isotopologues, and the related isotopologue ratios. We discuss the results in Section [4](#sec:discussion), and summarize our conclusions in Section [5](#sec:conclusion).

# Observations

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Transition | Frequency | $E_\mathrm{u}$ | log(A$_\mathrm{ul}$) | $g_\mathrm{u}$ | Q(18.75K) | Q(37.50K) | Q(75K) | $\Delta \mathrm{v}$ | Beam | RMS | $\Delta \mathrm{v}_{\mathrm{M}0}$ |
|  | \[GHz\] | \[K\] | \[s$^{-1}$\] |  |  |  |  | \[km s$^{-1}$\] | bmaj $\times$ bmin (PA) | \[mJy beam$^{-1}$\] | \[km s$^{-1}$\] |
| H$^{13}$CN (3-2) | 259.0117 | 24.9 | $-3.11$ | 21 | 28.17 | 55.31 | 109.6 | 0.4 | $0.20\ensuremath{''} \times 0.15\ensuremath{''} \,(95^\circ)$ | 0.55 | 1.5 - 9.5 |
| H$^{13}$CN (4-3) | 345.3398 | 41.4 | $-2.72$ | 27 | 28.17 | 55.31 | 109.6 | 0.4 | $0.13\ensuremath{''} \times 0.12\ensuremath{''}\,(100^\circ)$ | 0.70 | 1.85 - 9.5 |
| HC$^{15}$N (3-2) | 258.1571 | 24.8 | $-3.11$ | 7 | 9.421 | 18.50 | 36.66 | 0.4 | $0.20\ensuremath{''} \times 0.15\ensuremath{''}\,(94^\circ)$ | 0.65 | 2.3 - 8.7 |
| HC$^{15}$N (4-3) | 344.2001 | 41.3 | $-2.73$ | 9 | 9.421 | 18.50 | 36.66 | 0.9 | $0.13\ensuremath{''} \times 0.12\ensuremath{''}\,(101^\circ)$ | 0.75 | 1.9 - 9.1 |
| DCN (3-2) | 217.2386 | 20.9 | $-3.33$ | 21 | 33.39 | 65.75 | 130.5 | 0.9 | $0.29\ensuremath{''} \times 0.23\ensuremath{''}\,(83^\circ)$ | 0.73 | 2.3 - 9.1 |
| HCN ($J$=4-3,$F$=4-4) | 354.50387 | 42.5 | $-3.89$ | 9 | 27.47 | 53.91 | 106.8 |  |  |  |  |
| HCN ($J$=4-3,$F$=3-2) | 354.50537 | 42.5 | $-2.72$ | 7 | 27.47 | 53.91 | 106.8 |  |  |  |  |
| HCN ($J$=4-3,$F$=4-3) | 354.50548 | 42.5 | $-2.72$ | 9 | 27.47 | 53.91 | 106.8 | 0.9 | $0.37\ensuremath{''} \times 0.34\ensuremath{''}\,(134^\circ)$ | 1.03 | 0.1 - 10 |
| HCN ($J$=4-3,$F$=5-4) | 354.50552 | 42.5 | $-2.69$ | 11 | 27.47 | 53.91 | 106.8 |  |  |  |  |
| HCN ($J$=4-3,$F$=3-4) | 354.50585 | 42.5 | $-5.58$ | 7 | 27.47 | 53.91 | 106.8 |  |  |  |  |
| HCN ($J$=4-3,$F$=3-3) | 354.50745 | 42.5 | $-3.78$ | 7 | 27.47 | 53.91 | 106.8 |  |  |  |  |

Quantum numbers are formatted as $J$ (cite: fuchs2004high; cazzoli2005lamb; maiwald2000pure; fuchs2004high; cazzoli2005lamb; brunken2004sub; ahrens2002HCN).

Cubes are imaged with natural weighting.

Velocity ranges over which data cubes where collapsed to extract integrated intensity, chosen after visual inspection of the data.

Channel width, beam size, and RMS are indicated only for the main HCN component for reference.

Only HCN hyperfine component spectrally resolved by the presented observations.

In this work we used ALMA Band 6 and 7 line emission observations from projects #2019.1.01619.S (PI S. Facchini) and #2022.1.01695.S (PI M. Benisty). The observations include various lines of HCN isotopologues: HCN ($4-3$), ($3-2$), ($4-3$), ($3-2$), ($4-3$), DCN ($3-2$).

The Band 7 observations consist of four execution blocks (EBs): one short-baseline (SB, ALMA configuration C-4, max baseline 0.8 km) and three long-baseline (LB, configuration C-7, max baseline 3.6 km) configurations. The spectral setup includes four spectral windows (spws) initially intended for continuum observations, each with a bandwidth of 1.875 GHz, 1920 channels, and a resolution of 977 kHz. The spws cover the same frequency ranges across all EBs: 342.483-344.358 GHz for spw 0, 344.379-346.254 GHz for spw 1, 354.483-356.358 GHz for spw 2, and 356.441-358.316 GHz for spw 3. Each EB had 35 minutes of on-source time, for a total of 2.33 hours. All the EBs were initially calibrated using the ALMA pipeline, followed by self-calibration based on the pipeline designed by the exoALMA Large Program (Loomis et al., subm.), using the software CASA (cite: CASA2022), version 6.2. We first flagged the lines present in our frequency range (see Table [\[tab:lines_b6b7\]](#tab:lines_b6b7)): ($7-6$, $\nu=342.88\,\mathrm{GHz}$), ($4-3$, $\nu=344.20\,\mathrm{GHz}$), ($4-3$, $\nu=345.34\,\mathrm{GHz}$), ($3-2$, $\nu=345.80\,\mathrm{GHz}$), ($4-3$, $\nu=354.51\,\mathrm{GHz}$), ($4-3$, $\nu=356.73\,\mathrm{GHz}$), and ($8_8-7_7$, $\nu=344.31\,\mathrm{GHz}$). We flagged the range between -30 km/s to +30 km/s around each line center. The remaining unflagged data were averaged into 250 MHz-wide channels. A first round of phase-only self-calibration was performed on each EB separately, combining both scans and spws on time intervals over the full EB duration. The EBs were then aligned by regridding them to a common uv-grid with natural weighting, retaining only overlapping grid cells, and applying phase shifts to minimize visibility differences (Loomis et al., subm.). No flux rescaling was necessary, as flux offsets between EBs were minimal ($<1\%$). Next, phase-only self-calibration was applied to the SB EB using models created with the task `tclean`, cleaning down to $6\sigma$ at each round. Multiple rounds with progressively shorter solution intervals were used (EB-long, 360s, 120s, 60s, 20s), stopping when SNR and noise structure began to degrade. The self-calibrated SB EB was then concatenated with the three LB EBs, and phase-only self-calibration was repeated on the combined dataset. Similar to before, we cleaned down to $6\sigma$ at each step, with progressively shorter solution intervals (EB-long, 360s, 120s, 60s, 30s, 18s). After this, the data were cleaned down to $1\sigma$, and two rounds of amplitude and phase self-calibration were performed, combining polarizations and spws. The first round used EB-long intervals, while the second used scan-long intervals. Gain solutions and phase shifts were then applied to the full spectral data including line emission channels, following exactly the same order. To reduce dataset size, the full spectral data were binned into 30s intervals. Finally, continuum subtraction was performed on all datasets using the `uvcontsub` task. Self-calibration of Band 6 data was performed as described in (cite: law2024mapping; rampinelli2024).

We imaged the lines using the `tclean` task (cite: hogbom1974aperture; cornwell2008) implemented in the `CASA` software (cite: CASA2022) `v6.65`. In particular, we used a `multiscale` deconvolver with scales \[0,5,10,20,30\] pixels, where the pixel size is $\sim0.02\ensuremath{''}$, and a flux threshold of 3.5$\sigma$. We performed a first CLEANing without applying any mask, and a second CLEANing iteration using a mask built by selecting the signal $> 7\sigma$ in the previous iteration (Loomis et al., subm.). We applied the so-called JvM correction (cite: jorsater1995high), following (cite: czekala2021molecules), by rescaling the residual map by the ratio between areas of the CLEAN and DIRTY beams ($\epsilon$), to correct for the units mismatch between the model and residuals image (see Table [\[tab:imaging_molecules_2\]](#tab:imaging_molecules_2) for the $\epsilon$ values corresponding to each cube). More details on the CLEANing strategies can be found in (cite: rampinelli2024). The following analysis was performed on continuum subtracted cubes, and JvM corrected cubes, except for uncertainty evaluation, which could be underestimated by the JvM correction (cite: casassus2022variable), as residuals are rescaled. In the following analysis we also assumed the geometrical parameters~~,~~ $M_\ast = 0.875$ M$_\odot$, $i = 51.7^\circ$, PA$=160.4^\circ$, and $v_\mathrm{sys}=5.5$ km s$^{-1}$ (in LSRK frame), as they were obtained by (cite: keppler2019highly), and a distance of $113$ pc (cite: brown2018gaia).

We first imaged all lines with natural weighting. Table  [\[tab:imaging_molecules\]](#tab:imaging_molecules) lists the image properties, including channel width, beam size, and RMS, and properties of the molecular transitions. RMS is evaluated as standard deviation in the first and last 5 channels of each cube. A list of detected lines, with corresponding line fluxes is listed in Table [\[tab:lines_b6b7\]](#tab:lines_b6b7), which also includes Band 6 lines previously presented by (cite: rampinelli2024), for comparison. Line fluxes where obtained as described in Appendix [6](#appendix:fluxes) (Band 7) and (cite: rampinelli2024) (Band 6).

In order to perform the analysis outlined in Sect. [3](#sec:column), we imaged all the cubes with two different sets of parameters to maximize the sensitivity of Band 6 and 7 observations, respectively. Each time $uv$-taper and/or robust were chosen to obtain cubes with the same spatial resolution. In particular, cubes imaged to maximize Band 6 and Band 7 sensitivity correspond to beam major axes of $\sim0.20\ensuremath{''}$ ($\sim$23 au) and $\sim0.14\ensuremath{''}$ ($\sim$15 au), respectively. Corresponding weighting, $uv$-taper, beam size, beam area, and RMS for the two imaging rounds are listed in Table [\[tab:imaging_molecules_2\]](#tab:imaging_molecules_2).

We calculated integrated intensity maps of the imaged cubes using the `bettermoments` package (cite: teague2019bettermoments), integrating data cubes over a velocity range where each line shows emission in the channel maps. Figure [1](#fig:M0) shows an example of the obtained maps for each line (see last column of Table [\[tab:imaging_molecules\]](#tab:imaging_molecules)). The map in the bottom right panel of Fig. [1](#fig:M0) is obtained from SB observations only, which completely cover the HCN (4-3) line, while LB observations spectrally cover only half of the line, allowing the reconstruction of half of the azimuthal extent of the disk. In this work we analyzed the cube covering half of the HCN (4-3) line, obtained from combined SB and LB observations, as high angular resolution is needed to separate the hyperfine component (see Appendix [7](#appendix:imaging) for more details).

# Results

## Radial rotational diagram

![](images/rot_diagram_combined_tau_profiles_dTb.png)

From the integrated intensity maps in Fig. [1](#fig:M0), we extracted the radial profiles of the integrated intensity of each line, using the `GoFish` package (cite: teague2019gofish). In order to limit beam dilution when performing the azimuthal average, we tried to extract the radial profiles of the integrated intensity only from a wedge of $\pm30^\circ$ along the disk major axis. However, the resulting signal-to-noise ratio for DCN and in particular was too low to allow for the analysis presented in this paper. We therefore extracted the integrated intensity profiles by performing a complete azimuthal average over $0.1\ensuremath{''}$ wide annuli. The resulting profiles are plotted in the top panels in Fig. [2](#fig:profiles_rotdiagr). The dashed black line shows the integrated intensity profile of the 855 $\mu$m continuum observations (cite: isella2019detection; benisty2021circumplanetary).

As two lines are detected for both and , with upper energies ranging from $\sim25$ to 41 K, we could apply the rotational diagram (cite: goldsmith1999population) analysis to extract their molecular column density $N_\mathrm{t}$ and excitation temperature $T_\mathrm{ex}$, as follows: $$\begin{equation}
\label{eq:rot_diag}
    \ln{\frac{N_\mathrm{u}}{g_\mathrm{u}}} = \ln{N_\mathrm{t}} -\ln{Q(T_\mathrm{ex})} - \frac{E_\mathrm{u}}{\mathrm{k_\mathrm{B}}T_\mathrm{ex}},
\end{equation}$$ where $N_\mathrm{u}$, $g_\mathrm{u}$, and $E_\mathrm{u}$ are the upper state column density, degeneracy, and energy, respectively, $N_\mathrm{t}$ is the total molecular column density, k$_\mathrm{B}$ is the Boltzman constant, $T_\mathrm{ex}$ is the excitation temperature, and $Q(T_\mathrm{ex})$ is the partition function. In the optically thin assumption, $N_\mathrm{u}$ depends on the integrated flux density $S_\nu \Delta \mathrm{v}$: $$\begin{equation}
 \label{eq:Nu}
    N_\mathrm{u} = \frac{4 \pi S_\nu \Delta \mathrm{v}}{A_\mathrm{ul} \Omega \mathrm{hc}},
\end{equation}$$ where $\Omega$ is the emitting area.

If the optically thin assumption is not valid, i.e. $\tau \not\ll 1$, Eq. [\[eq:rot_diag\]](#eq:rot_diag) can be corrected for the optical depth $\tau$ through the following factor: $$\begin{equation}
\label{eq:Ctau}
    C_\tau = \frac{\tau}{1-e^{-\tau}},
\end{equation}$$ resulting in the following rotational diagram equation (cite: loomis2018distribution): $$\begin{equation}
 \label{eq:Ctau_rotdiag}
        \ln{\frac{N_\mathrm{u}}{g_\mathrm{u}}} = \ln{N_\mathrm{t}} - \ln{C_\tau} -\ln{Q(T_\mathrm{ex})} - \frac{E_\mathrm{u}}{\mathrm{k_\mathrm{B}}T_\mathrm{ex}}.
\end{equation}$$

We computed the rotational diagram correcting for the optical depth factor $C_\tau$. We applied a radial rotational diagram, to retrieve the radial profiles of $N_\mathrm{t}$ and $T_\mathrm{ex}$ for the and molecules, using Eq. [\[eq:Nu\]](#eq:Nu) and [\[eq:Ctau_rotdiag\]](#eq:Ctau_rotdiag), and cubes with the same beam sizes.

We accounted for the optical depth of each line included in the rotational diagram, evaluating $\tau$ as follow: $$\begin{equation}
\label{eq:tau}
    \tau(R) = - \ln{\biggl(1-\frac{T_\mathrm{b}(R)}{T_\mathrm{ex}(R)}\biggr)},
\end{equation}$$ where $T_\mathrm{b}(R)$ is the radial profile of the brightness temperature, taken as the azimuthal average of the peak brightness temperature over each annulus in which we applied the rotational diagram, and $T_\mathrm{ex}(R)$ is the radial profile of the sampled excitation temperature.

Another important limitation of using the peak brightness temperature comes from the finite spectral resolution of the observations, and thus in spectral smearing which results in underestimating the peak brightness temperature in a specific velocity bin. We therefore used cubes imaged with the smallest width of the velocity channel allowed by the spectral resolution of the observations. We explored the effect of spectral smearing on the peak brightness temperature in Appendix [8](#appendix:B), which we evaluated to be negligible in our case, and thus did not include in the analysis.

We sampled the posterior distribution of $T_\mathrm{ex}(R)$ and $N_\mathrm{t}(R)$ through a Markov-Chain Monte Carlo (MCMC) method with the `emcee` package (cite: foreman2013emcee), with 128 walkers, 3000 burn-in steps, and 500 steps. We considered a uniform prior with $T_\mathrm{ex}\in (10,100)$ K and $N_\mathrm{t} \in (10^{10}, 10^{16})$ cm$^{-2}$. The propagated uncertainty on the integrated intensity, on the brightness temperature and a 10% absolute flux calibration uncertainty were considered (sum in quadrature) when generating the likelihood. Moreover, we sampled the posterior distribution of the optical depth starting from random samples from the $T_\mathrm{ex}$ posterior distribution, and from a normal distribution of $T_\mathrm{b}$, centered around its median value, with standard deviation given by its statistical uncertainty.

We first applied the rotational diagram separately to and , since two lines are available for each of the molecules. As the excitation temperatures obtained for the two molecules are consistent, we applied a final rotational diagram analysis fitting for a single excitation temperature for both and . The bottom panels in Fig. [2](#fig:profiles_rotdiagr) show the results of the radially-resolved rotational diagram, including $N_\mathrm{t}$, $T_\mathrm{ex}$, and $\tau$. The solid lines show the 50th percentile of the resulting distributions, while ribbons show the 16th and 84th percentiles.

Figure [2](#fig:profiles_rotdiagr) shows the result obtained from cubes imaged maximizing the sensitivity of Band 6 observations, while Appendix [9](#appendix:C) shows the same result but from cubes imaged to maximize the sensitivity of Band 7 observations, with the latter corresponding to a higher spatial resolution ($\sim0.15\ensuremath{''}$) with respect to the former ($\sim0.20\ensuremath{''}$). Imaging procedures and details on the resulting imaged cubes are presented in Appendix [7](#appendix:imaging) and Table [\[tab:imaging_molecules_2\]](#tab:imaging_molecules_2). The two results are consistent, and were both used to extract the radial profiles of N, C, and H fractionation of HCN, as described in the following Section.

## Isotopologue ratios

from fixed $^{12}C/^{13}C$

![](images/fractionation_deuteration_tau.png)

DCN/HCN and HCN/ ratios in disks are usually extracted from instead of the main isotopologue HCN, as the latter is typically optically thick (cite: guzman2017). We also extracted the deuteration and nitrogen fractionation profiles by assuming a radially constant $\ce{^12C}/\ce{^13C}=69$ ratio (cite: wilson1999isotopes) to convert the into an HCN column density. We therefore used the results of the rotational diagram analysis shown in Fig. [2](#fig:profiles_rotdiagr), obtained from cubes maximizing the sensitivity of Band 6 observations (see the second section of Table [7](#appendix:imaging) for imaging specifics).

The posterior distributions of the $69\times N(\ce{H^13CN})/N(\ce{HC^15N})$ and $N(\ce{DCN})/[69\times N(\ce{H^13CN})]$ ratios were built from the posterior distributions of the column density of , , and DCN. We reconstructed the posterior distribution of $N$(DCN) from Eq. [\[eq:Ctau_rotdiag\]](#eq:Ctau_rotdiag), by randomly sampling the excitation temperature from the rotational diagram result, assuming DCN has the same excitation temperature as and . The uncertainty on the DCN flux was accounted for in the posterior distribution of the isotopologue ratio, by randomly sampling the flux of the DCN (3-2) line from a normal distribution centered around the median value, with a standard deviation given by its statistical uncertainty. As for and , we extracted the radial profile of the DCN column density correcting for its optical depth, using Eq. [\[eq:tau\]](#eq:tau). The bottom row in Fig. [9](#fig:profiles_rotdiagr_b7res) in Appendix [9](#appendix:C) shows the radial profiles of the DCN column density and optical depth, compared to the other isotopologues.

The resulting radial profiles of the isotopologue ratios are presented in Fig. [3](#fig:N_D_frac), and are also compared to the radial profile of the continuum integrated intensity (dashed dark line), which do not show any clear correlation with the fractionation profiles. The nitrogen fractionation profile is decreasing and below the ISM value from $\sim40$ to 100 au, while the deuteration profile is mostly constant between $\sim40$ au 100 au, and significantly above the ISM D/H value of $\sim10^{-5}$ (cite: linsky2006).

## Radial profile of HCN column density

![](images/hyperfine_fit_gaussian_convolved.png)

The radial profile of the HCN column density is needed to extract the HCN/ ratio, or the HCN/ and DCN/HCN ratios without assuming a fixed ratio. HCN column density, optical depth, and excitation temperature could be retrieved leveraging the HCN hyperfine components, which are needed as the main component is typically optically thick, as previously presented by (cite: guzman2021molecules) for the MAPS sample, or by (cite: hily2019multiple) for the TW Hya disk.

However, the spatial resolution of SB observations of the HCN (4-3) line does not allow to separate the two hyperfine components, since beam smearing leads to spatial blending of the hyperfine components. LB+SB observations of the analyzed data, on the other hand, allow to spatially resolve the hyperfine component at 354.5075 GHz, centered at 3.8 km s$^{-1}$ (main component $v_\mathrm{sys}=5.5$ km s$^{-1}$). As LB observations spectrally cover only one of the two hyperfine components, and only half of the main component (see Fig. [4](#fig:hyperfine_fit)), we could not apply the rotational diagram to simultaneously extract HCN column density and excitation temperature. We therefore computed the radial profile of the HCN column density, assuming the same excitation temperature obtained from the rotational diagram of and , through Eq. [\[eq:rot_diag\]](#eq:rot_diag).

In particular, we reconstructed the HCN column density from the flux of the hyperfine component at 3.8 km s$^{-1}$ by assuming it is optically thin, which is valid since $\tau\lesssim0.02$ from Eq. [\[eq:tau\]](#eq:tau). To extract the radial profile of the flux of the hyperfine component, we applied a double-Gaussian fit to the spectrum in multiple radial bins. We fixed the center of the two Gaussian components to be at 3.8 km s$^{-1}$ (hyperfine component) and at the systemic velocity of 5.5 km s$^{-1}$ (main component), and we fit for the two widths and peaks. From the result of the Gaussian fit presented in Fig. [4](#fig:hyperfine_fit), we then reconstructed the posterior distribution of the hyperfine flux, as outlined in Appendix [9](#appendix:C) in more details.

We then reconstructed the posterior distributions of $N$(HCN) using Eq. [\[eq:rot_diag\]](#eq:rot_diag) and [\[eq:Nu\]](#eq:Nu), from the reconstructed posterior distributions of the flux of the HCN hyperfine component, and of the excitation temperature of and . In particular, we randomly sampled the excitation temperature from the rotational diagram result, and the hyperfine flux from the posterior distribution obtained from the double-Gaussian fit.

We were unable to smooth the HCN cube to match the spatial resolution of $\sim0.20\ensuremath{''}$ of and cubes used in the rotational diagram shown in Fig. [2](#fig:profiles_rotdiagr), as a worse spatial resolution would deteriorate the hyperfine fitting procedure, due to spectral blending of the hyperfine components, as we previously outlined. We therefore used the result from the rotational diagram shown in Appendix [9](#appendix:C), obtained from cubes with a higher spatial resolution of $\sim0.15\ensuremath{''}$ (see also Appendix [7](#appendix:imaging)). The bottom left panel of Fig. [9](#fig:profiles_rotdiagr_b7res) in Appendix [9](#appendix:C) shows the radial profiles of the HCN column density, in comparison to the other isotopologues.

## Isotopologue ratios using HCN column density

From the HCN column density retrieved from the hyperfine fitting procedure, we extracted the radial profiles of the isotopologue ratios HCN/, HCN/, and DCN/HCN, shown in Fig. [5](#fig:12C13C), by the light blue, red, and purple profiles, respectively. Similarly to the previous case where we fixed the ratio, the posterior distributions of the ratios were built from the posterior distributions of the column density of , (taken from the rotational diagram result shown in Fig. [9](#fig:profiles_rotdiagr_b7res)), DCN, and HCN. As we already outlined in Sect. [3.3](#subsec:HCN_column), we used cubes imaged to maximize the sensitivity of Band 7 observations (see the first section of Table [\[tab:imaging_molecules_2\]](#tab:imaging_molecules_2) in Appendix [7](#appendix:imaging) for imaging specifics), as a higher angular resolution is needed to perform the hyperfine fitting procedure.

As shown in the middle panel of Fig. [5](#fig:12C13C), the carbon fractionation profile is consistent with the ISM value between $\sim50$ and 100 au, within the errorbars, which also justifies the previous assumption we made of a radially constant to extract the deuteration and nitrogen fractionation profiles in Sect. [\[subsec:fixed12C13C\]](#subsec:fixed12C13C), from the isotopologue. Moreover, the isotopologue ratios obtained by assuming a radially constant $\ce{^12C/^13C}=69$ (dark blue and pink profiles in Fig. [5](#fig:12C13C)), or from the radial profile of the HCN column density directly (light blue and purple profiles), are consistent within the errorbars.

The hyperfine fitting procedure presented above and in Appendix [9](#appendix:C) is strongly limited by the fact that only half of the HCN (4-3) line is covered by LB observations, by the low spectral resolution of $\sim0.9$ km s$^{-1}$, and the lower signal to noise ratio. This consequently results in large error bars for the profiles of isotopologue ratios obtained from the main isotopologue HCN, and does not allow to robustly extract the ratios inside $\sim40$ au and beyond $\sim100$ au.

# Discussion

## Nitrogen

Isotope fractionation in disks is mainly driven by two processes: isotope exchange reactions and isotope selective photodissociation (cite: nomura2022isotopic). For the specific case of nitrogen fractionation, the former can enhance the abundance of and at low temperatures $T\lesssim20$ K (cite: terzieva2000possibility). On the other hand, isotope selective photodissociation of over the self-shielding is favored in strongly irradiated regions (cite: heays2014isotope; visser2018nitrogen), allowing free to enhance the abundance. This fractionation process is enhanced in strongly irradiated regions of the disk, such as the disk atmosphere or cavities of transition disks. Evidence of an efficient illumination of the PDS 70 cavity was presented by (cite: law2024mapping), along with its impact on line emission morphology of various molecular tracers (cite: rampinelli2024). In this context, radial profiles of isotope fractionation can reveal how different fractionation processes dominate at different planet forming scales.

In particular, radial profiles of / have been extracted for the disks around TW Hya (from CN and HCN isotopologues, (cite: hily-blant2017; hily2019multiple)) and V4046 Sgr (from HCN isotopologues, (cite: nomura2022isotopic), Guzmán et al. in prep.). The profiles are reconstructed up to $\sim$60 au, and they are both increasing with radius, as shown in the left panel of Fig [6](#fig:frac_disks). This has been interpreted as the result of isotope selective photodissociation: the higher gas density and stronger UV field at smaller radii result in an efficient self-shielding of , and efficient photodissociation of , thus resulting in enhanced in the inner region of the disks. These observational results also agree with fractionation models (cite: visser2018nitrogen; lee2021modeling), and are consistent with the result we found for PDS 70 (see left panel in Fig. [6](#fig:frac_disks)). However, we highlight that the spatial resolution and sensitivity make the profiles shown in Fig. [3](#fig:N_D_frac), [5](#fig:12C13C), [6](#fig:frac_disks) highly uncertain for radii $\lesssim 25$ au, and therefore need to be interpreted with caution.

While radial profiles of HCN/ for TW Hya and V4046 Sgr are only probing the increasing trend inside $\sim 60$ au, we could extract the isotopologue ratio out to $\sim120$ au for the PDS 70 disk. The / ratio shows a turnover at $\sim60$ au, and it decreases below the ISM value at larger radii. This trend agrees with the predictions from the thermo-chemical models presented by (cite: visser2018nitrogen) for a typical disk around a T Tauri star (full disk). As they show in their Fig. 12, the HCN/ column density ratio is expected to increase up to $\sim 400$ out to $\sim30$ au and then decrease down to $\sim260$ between $\sim30$ and $100$ au. (cite: visser2018nitrogen) showed that both the inner increase and the outer decrease in the HCN/ column density ratio are the result of isotope selective photodissociation of , as low-temperature isotope exchange reactions alone do not produce any important radial variations. This qualitative agreement between the result directly extracted from ALMA observations in this work, and the prediction from thermo-chemical models obtained assuming a typical disk around a T-Tauri star (cite: visser2018nitrogen), suggests that regardless of the physical structure of the individual source which is analyzed, isotope selective photodissociation plays a fundamental role in changing the HCN fractionation during the protoplanetary disk stage. This is also consistent with the fact that the decrease of HCN/ in the outer disk is always predicted from thermo-chemical models by (cite: visser2018nitrogen), even when varying disk parameters, such as the disk mass, flaring angle, large grain fraction, stellar type, or accretion rate.

The ratio of small to large grains has the largest quantitative impact on the isotopologue ratio (cite: visser2018nitrogen), as it affects the attenuation of UV photons, which are responsible both for the production and fractionation of HCN in the gas phase. The presence of an inner disk in the PDS 70 system, observed both in IR and sub-mm observations, and the large mm-dust cavity ($\sim75$ au) can therefore have a role in setting the fractionation levels of HCN, and the radial location of the turn over in the HCN/ profile (see the left panel in Fig. [6](#fig:frac_disks)). In this context, both TW Hya and V4046 Sgr also show a dust cavity of $\sim2.5$ au (cite: andrews2016ringed) and $\sim13$ au (cite: martinez2022high), respectively, smaller with respect to the PDS 70 one, which is also showing a deep gas gap. The location of the layer where isotope selective photodissociation dominates is also related to the distribution of the $\mu$m dust, which attenuates the UV flux. However, our attempt of extracting the HCN emitting layer from the radial profile of its excitation temperature, to compare it to the $\mu$m dust surface, is inconclusive (see Appendix [10](#appendix:layer_HCN)). Specific thermo-chemical models for the PDS 70 disk are therefore needed to quantitatively reproduce the observed radial profile of the HCN/ ratio.

Eventually, we highlight that low-temperature isotope exchange reactions, even if less efficient than isotope selective photodissociation (cite: roueff2015isotopic; wirstrom2018; loison2019chemical), cannot be completely ruled out at low layers over the midplane or in the cold outer disk, outside the CO snowline ($\sim70$ au for the PDS 70 disk as estimated by (cite: law2024mapping).)

![](images/fractionation_hyperfine_12C13C_N+H_tau_b7res_dTb.png)

## Carbon

The nitrogen fractionation of HCN shown in Fig. [3](#fig:N_D_frac) is extracted assuming a radially constant / equal to the ISM value, which makes the above interpretation only speculative, as the role of nitrogen and carbon fractionation in determining the decreasing trend cannot be robustly distinguished with current observations. Nevertheless, our attempt of leveraging the HCN hyperfine component covered by the analysed observations (see Appendix [9](#appendix:C)) suggests that the HCN/ ratio is slightly increasing between $\sim$40 and 100 au, but the profile is consistent with the ISM value within the errorbars. In this picture, the assumption of $\ce{^12C/^13C}=69$ to convert the into and HCN column density is justified, as the HCN/ profile still shows a decreasing trend between $\sim$40 and 90 au, which is consistent with the $69\times\ce{H^13CN}/\ce{HC^15N}$ profile.

To the best of our knowledge, the carbon isotopic ratio has been extracted only for one other disk, i.e. the disk around TW Hya, for CO (cite: zhang2017mass; yoshida2022), HCN (cite: hily-blant2019multiple), CN (cite: yoshida2024), and CCH (cite: bergin2024). These results show that the value of can vary between $\sim20$ to $\sim90$ depending on the molecule used to extract it, and evidence for two separate carbon isotopic reservoirs (cite: bergin2024). The ratio extracted from HCN in TW Hya is shown in the middle panel of Fig. [6](#fig:frac_disks), with / being mostly constant and above the ISM value up to $\sim60$ au.

On the other hand, our result for the PDS 70 disk shows that carbon fractionation may become relevant beyond $\sim$90 au (see middle panel of Fig. [5](#fig:12C13C)), which could be linked to the onset of the low-temperature isotope exchange reaction $\ce{^13C} + \ce{CO} \rightleftarrows \ce{C^+} + \ce{^13CO} + \mathrm{35}$ K in the cold outer disk, depleting in favor of and increasing the HCN/ ratio (cite: visser2018nitrogen; oberg2021astrochemistry). This result qualitatively agrees also with predictions from fractionation models performed by (cite: visser2018nitrogen) for HCN/. This can also affect the result we presented for nitrogen and hydrogen fractionation in Fig. [3](#fig:N_D_frac), which was extracted assuming a radially constant ratio. The low values of the and ratios (dark blue and pink profiles in Fig. [3](#fig:N_D_frac) respectively) outside $\sim 100$ au could be an artificial result of the assumption of a radially constant , instead of nitrogen or hydrogen fractionation in the outer disk.

However, the picture of carbon fractionation is complex: reactions producing HCN can start either from or , depending on the region in the disk (cite: visser2018nitrogen). Therefore, both low temperature isotope exchange reactions and isotope selective photodissociation can play a crucial role in determining carbon fractionation of HCN. Moreover, these reactions primarily depend on the main C-carrier, i.e. CO, whose isotopic ratio should be inferred to better interpret the result for HCN. In this context, further thermochemical modeling specifically tuned on the transition disk of PDS 70, and higher spectral resolution observations fully covering also the main and hyperfine components of the HCN (4-3) transition are needed to interpret the result for HCN fractionation and robustly disentangle carbon and nitrogen fractionation.

![](images/frac_compare_disks_tau_dTb.png)

## Hydrogen

As for nitrogen fractionation, we extracted the deuteration profile of HCN, either by $N(\ce{DCN})/[N(\ce{H^13CN})\times 69]$, or by $N(\ce{DCN})/N(\ce{HCN})$ (pink and purple line in the right panel of Fig. [5](#fig:12C13C), respectively), leveraging the resolved hyperfine component of the HCN line (see Appendix [9](#appendix:C)). The deuteration profile is almost flat (around $\sim0.02$, for radii between 40 and 100 au. The increase at $\sim$100 au in the pink profile in the right panel of Fig. [5](#fig:12C13C) could indicate a more efficient deuteration pathway in the cold outer disk, but the profile may be affected by carbon fractionation. The / profile shown in Fig. [5](#fig:12C13C)~~)~~ has large uncertainties outside $\sim90$ au, and thus does not allow to robustly conclude on the contribution of carbon fractionation in the outer disk. Similarly to nitrogen fractionation, in order to definitely disentangle the effect of carbon fractionation, new high spectral resolution observations covering the two hyperfine components of the HCN line are needed.

The deuteration level of the HCN molecule in the PDS 70 disk is significantly above the ISM value of $\sim 10^{-5}$ (cite: linsky2006; nomura2022isotopic), which suggests that there are efficient deuteration processes enriching HCN with deuterium. The main deuteration pathway in protoplanetary disks is through isotope exchange reactions involving HD at low temperatures ($T\lesssim25$ K) or at higher temperatures ($T\lesssim300$ K) (cite: millar1989deuterium; aikawa1999; stark1999), which produce and , respectively. Deuterium from and can be transferred to other molecules through proton transfer such as HNC + $\rightarrow$ + , which can subsequently produce DCN through dissociative recombination + $\rightarrow$ DCN + H (cite: cataldi2021molecules).

Given the different gas temperatures at which these reactions set, we expect them to dominate in different regions in the disk. The radial profile of DCN/HCN ratio is mostly constant at $\sim0.02$ between $\sim40$ and 100 au, which suggests that both reactions are important in setting the deuteration level of HCN, even if at different radial scales.

![](images/C_frac_N_frac_HCN.png)

The right panel of Fig. [6](#fig:frac_disks) shows the comparison between the radial profile of HCN deuteration in the PDS 70 disk (red profile) and the MAPS survey (cite: cataldi2021molecules). The D/H values show a large scatter among different sources, but they are systematically above the elemental ISM value (dashed black horizontal line). This suggests that in situ fractionation processes are actively resetting the original ISM value in a source-dependent way, which is strongly affected by different physical conditions set in different disks, such as gas temperature or ionization structure. In particular, as resulting from the MAPS survey (cite: cataldi2021molecules), the DCN/HCN profile in disks around Herbig stars show a steeper decreasing profile of DCN/HCN at small radii with respect to T Tauri disks (see the right panel of Fig. [6](#fig:frac_disks)). This has been interpreted as the effect of an higher temperature at small radii for Herbig with respect to T Tauri disks, thus inhibiting the deuteration reaction. This picture is consistent with the fact that the radial profile of the DCN/HCN ratio inside $\sim100$ au for the T Tauri disk of PDS 70 is compatible with the ones for T Tauri disks in the MAPS sample.

## Comparison with early and later stages

Fig. [7](#fig:frac_stages) shows a summary of nitrogen, carbon, and hydrogen fractionation in various astronomical objects across different evolutionary stages of star and planet formation from the literature. The red and dark blue markers indicate isotopic ratios of the HCN molecule for the PDS 70 disk (at different radii) and in other sources (prestellar/protostellar cores, class 0/I sources, comets), respectively. Light blue markers refer to isotopic ratios measured in the ISM and the sun, with the exception of the solar measured from CO (green marker in the middle panel). Appendix [11](#appendix:other_stages) lists all the references for the values presented in Fig. [7](#fig:frac_stages) and some details on the adopted methodologies.

The isotopologue ratios of HCN across early stages of the star formation history, i.e. in prestellar cores and class 0/I Young Stellar Objects (YSOs), are in most of the cases consistent with the results presented in this work for the PDS 70 disk. This is suggesting either a conservation of the original gas phase isotopologue fractionation, or that if gas phase fractionation processes are fast and the physical conditions in each stage are similar, the resulting isotopologue ratios are consistent. On the other hand, both HCN/ and DCN/HCN ratios in prestellar/protostellar cores show a large spread, possibly highlighting the strong dependence of fractionation processes on the local physical condition in different sources, such as the gas temperature for isotope exchange reactions and radiation field for isotope selective photodissociation. Moreover, HCN/ values extracted for early stages presented in Fig. [7](#fig:frac_stages) include both direct and indirect methods relying on various assumptions such as the conversion factor, or the lines opacities (cite: hily-blant2020; jensen2024fractionation). (cite: hily-blant2020) highlighted how indirect methods result in more scattered values compared to direct methods. In particular, the first direct estimates of HCN/ and HCN/ for a prestellar core were presented by (cite: magalhaes2018nitrogen), showing deviations from indirect methods pointing to a enrichment. Similarly, (cite: jensen2024fractionation) presented both direct and indirect measurements of the HCN/ ratio towards six starless and prestellar cores, showing significant difference (as also visible from Fig. [7](#fig:frac_stages)). Consistent with what we previously highlighted, (cite: jensen2024fractionation) also showed that there is no evident trend among different stages of star formation when considering direct estimates. It is also important to highlight that in the YSOs phase there could be a gas-phase contribution of HCN directly released from icy grains, even if gas-phase formation of HCN is thought to be dominant (cite: bergner2020deuteration). The gas-phase origin of HCN in YSOs is supported by single dish observations where the HCN sublimation region (HCN desorption temperature of $\sim3370$ K, (cite: noble2012desorption),(cite: bergner2022HCN)) is unresolved (cite: cataldi2021molecules). Finally, as shown in Fig. [7](#fig:frac_stages), (cite: evans2022fractionation) presented the HCN/ ratio measured in different regions of the protocluster OMC-2 FIR4, showing consistent results for the central region and a higher ratio for the East region, which is more distant from the protocluster center. This highlights again the importance of studying spatial variations of fractionation levels in the same source, since fractionation processes are strongly affected by the local physical conditions.

A spread of and DCN/HCN ratios is also observed in protoplanetary disks (PPDs) (cite: huang2017alma; guzman2017; hily-blant2019multiple), with HCN/ values in agreement with measurements both for early and later stages. DCN/HCN ratios show approximately an order of magnitude difference between disks around T Tauri and Herbig stars (cite: huang2017alma), with the lowest deuteration levels measured in Herbig disks, possibly due to their higher temperature with respect to T Tauri disks, as already mentioned in Sect. [4.3](#subsec:disc:H). The T Tauri disk of V4046 Sgr is an exception in this picture, with its low value of $\ce{DCN/HCN}\sim50$, which is also only a factor $\sim2$ higher than the DCN/HCN ratio measured for the Hale-Bopp comet (cite: meier1998deuteration). In this context, we highlight that V4046 Sgr is the oldest disk in the sample, being $\sim 23$ Myr old (cite: mamajek2014), which could also affect its deuteration level. Moreover, we highlight that HCN isotopologue ratios presented in Fig. [7](#fig:frac_stages) for protoplanetary disks are only disk integrated, while radial variations presented in Fig. [6](#fig:frac_disks) reveal how the local environment affects fractionation processes.

HCN/ ratios seem to suggest an increasing evolutionary trend, with ratios in early stages and comets matching the HCN/ values at small and large radii in the PDS 70 disk, respectively. On the other hand, the large uncertainties on the HCN/ radial profile in the PDS 70 disk do not allow to assess the robustness of this trend. Both richer statistics on carbon fractionation for early and later stages of star and planet formation and higher spectral resolution observations for the PDS 70 disk could shed light on the origin of this possible trend.

Moving to the comparison with later stages, we compare the HCN isotopologue ratios extracted for the PDS 70 disk with cometary values, both for Jupiter Family (JF) and Oort Family (OF). The and ratios are in good agreement with the values we found in the PDS 70 disk, especially with the outer disk region outside $\sim70$ au, which seems to suggest a correlation between the cometary material and the gas phase composition in the outer disk (cite: bockelee2008HCNcomets; cordiner2019carbon). On the other hand, this picture is not consistent with the only measurement of DCN/HCN in the Hale-Bopp comet which is approximately one order of magnitude lower than the PDS 70 disk values (cite: meier1998deuteration). Moreover, both the DCN/HCN and HCN/ ratios in comets are not consistent with the corresponding ratios measured in prestellar/protostellar cores.

The low value of DCN/HCN in Hale-Bopp is suggesting that the HCN ice observed in the comet may not be probing the same gas phase HCN reservoir observed in prestellar/protostellar cores. In particular, the ice component could originate from the early phases of star and planet formation. Due to the low formation efficiency of HCN ice, it is undetected in the ISM though a low abundance is expected (cite: gerakines2004ultraviolet; mumma2011; gerakines2022direct; mcclure2023ice). The cometary HCN deuteration could have also been altered once HCN was already incorporated on the ice. In particular, thermally- or radiation-induced exchange reactions on the ices were shown to play an important role in altering the deuteration of a variety of ices, such as hydrocarbons- or methanol-water ices (cite: mousis200deuterium; weber2009hydrogen; faure2015methanol).

In summary, we highlight that this is still a very uncertain picture, requiring further investigation. In particular, better statistics on the DCN/HCN in comets could help understanding if the value measured for the Hale-Bopp comet is an outlier or typical for comets. HCN fractionation is generally poorly constrained in comets, thus making it difficult to speculate on the origin. Similarly, it is important to probe HCN carbon fractionation in more objects throughout the star and planet formation timeline, to assess the suggested evolutionary trend. Moreover, further theoretical modeling and laboratory studies on HCN ices are needed to shed light on the role of deuteration in the ice phase.

Finally, we highlight that we could not directly compare our results with the recent measurements of isotopologue ratios in exoplanetary atmospheres (cite: zhang202113co; gandhi2023), as the latter are not obtained from the same tracers ( and CO) as the former (HCN), and could therefore be driven by very different fractionation processes from the ones we are probing with observations used in this work.

# Conclusion

In this work we present radial profiles of carbon, nitrogen, and hydrogen fractionation of the HCN molecule in the planet-hosting disk around PDS 70, showing how local fractionation pathways can alter isotopologue ratios. We summarize the main results as follow:

- We show spatially resolved emission of HCN ($4-3$), ($3-2$), ($4-3$), ($3-2$), ($4-3$), and DCN ($3-2$) in the PDS 70 disk.

- We present a decreasing trend of the / isotopic ratio of HCN, outside the disk cavity wall, which we suggest to be linked to isotope selective photodissociation of .

- We show that the D/H profile of HCN is almost flat throughout the disk extent and slightly decreasing in the outer disk. The deuteration profile does not show any correlation with the nitrogen fractionation one, which is consistent with the fact that deuteration is thought to be mainly driven by gas-phase isotope-exchange reactions in the cold midplane/outer disk.

- We retrieve the radial profile of the / ratio, by extracting the HCN column density leveraging the spatially and spectrally resolved hyperfine component of HCN (4-3). The extracted / ratio is consistent with the ISM value. This suggests that the decreasing trend in / is primarily driven by local nitrogen fractionation pathways.

Radial variations of the gas-phase isotopologue ratios reveal local fractionation pathways in the PDS 70 disk, which could leave an imprint on the gas accreted by the two forming planets. This highlights the potential of isotopic ratios to reconstruct the journey of planetary material. Higher spectral resolution observations, also covering the high velocity hyperfine component of the HCN line are needed to robustly confirm our results. Moreover, comparison with thermochemical models specifically tuned on PDS 70 could help interpret observations in light of possible fractionation pathways, and in particular better constrain the role of carbon fractionation in the main C-carrier, i.e. CO.

This work adds to the list of the few protoplanetary disks with a detailed analysis of their fractionation profiles, with PDS 70 being the only target where the photospheres of embedded protoplanets can be observed and characterized. Even though modelling is needed to connect the fractionation of different molecular or atomic species that best trace individual evolutionary steps in the star and planet formation process, promoting a direct comparison of isotopologue ratios in exoplanetary atmospheres and protoplanetary disks is of primary importance to build a bridge between formed planets and their natal environment.

# Acknowledgements

We thank V.V. Guzmán, P. Hily-Blant, and G. Cataldi for their availability in sharing results particularly important for the purpose of this work.

This paper makes use of the following ALMA data:

ADS/JAO.ALMA#2019.1.01619.S,

ADS/JAO.ALMA#2022.1.01695.S.

ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

L.R., S.F., and M.L. are funded by the European Union (ERC, UNVEIL, 101076613). Views and opinions expressed are however those of the authors only and do not necessarily reflect those of the European Union or the European Research Council. Neither the European Union nor the granting authority can be held responsible for them. S.F. also acknowledges financial contribution from PRIN-MUR 2022YP5ACE.

P.C. acknowledges support by the ANID BASAL project FB210003.

M.B. has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (PROTOPLANETS, grant agreement No. 101002188).

Support for C.J.L. was provided by NASA through the NASA Hubble Fellowship grant No. HST-HF2-51535.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555.

B.P.R. is supported by NASA STScI grant JWST-GO-01759.002-A. The Center for Exoplanets and Habitable Worlds is supported by the Pennsylvania State University and the Eberly College of Science.

The PI acknowledges the use of computing resources from the Italian node of the European ALMA Regional Center, hosted by INAF-Istituto di Radioastronomia.

136 natexlab

(ref: agundez2019carbon) Agúndez, M., Marcelino, N., Cernicharo, J., Roueff, E., & Tafalla, M. 2019, A&A, 625, A147

(ref: ahrens2002HCN) Ahrens, V., Lewen, F., Takano, S., et al. 2002, Zeitschrift Naturforschung Teil A, 57, 669

(ref: ahrens1999pure) Ahrens, V. & Winnewisser, G. 1999, Zeitschrift für Naturforschung A, 54, 131

(ref: aikawa1999) Aikawa, Y. & Herbst, E. 1999, ApJ, 526, 314

(ref: albertsson2014chemodynamical) Albertsson, T., Semenov, D., & Henning, T. 2014, ApJ, 784, 39

(ref: aleon2010multiple) Aléon, J. 2010, ApJ, 722, 1342

(ref: altwegg2019cometary) Altwegg, K., Balsiger, H., & Fuselier, S. A. 2019, ARA&A, 57, 113

(ref: andrews2018disk) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41

(ref: andrews2016ringed) Andrews, S. M., Wilner, D. J., Zhu, Z., et al. 2016, ApJL, 820, L40

(ref: barrado2023) Barrado, D., Mollière, P., Patapis, P., et al. 2023, Nature, 624, 263

(ref: benisty2021circumplanetary) Benisty, M., Bae, J., Facchini, S., et al. 2021, ApJL, 916, L2

(ref: benisty2022optical) Benisty, M., Dominik, C., Follette, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 605

(ref: bergin2024) Bergin, E. A., Bosman, A., Teague, R., et al. 2024, ApJ, 965, 147

(ref: bergner2020deuteration) Bergner, J. B., Öberg, K. I., Bergin, E. A., et al. 2020, ApJ, 898, 97

(ref: bergner2022HCN) Bergner, J. B., Rajappan, M., & Öberg, K. I. 2022, ApJ, 933, 206

(ref: bockelee2008HCNcomets) Bockelée-Morvan, D., Biver, N., Jehin, E., et al. 2008, ApJL, 679, L49

(ref: bogey1981millimeter) Bogey, M., Demuynck, C., & Destombes, J. 1981, Chemical Physics Letters, 81, 256

(ref: bogey1986centrifugal) Bogey, M., Demuynck, C., & Destombes, J. 1986, Chemical physics letters, 125, 383

(ref: booth2023sulphur) Booth, A. S., Ilee, J. D., Walsh, C., et al. 2023, A&A, 669, A53

(ref: brunken2004sub) Brünken, S., Fuchs, U., Lewen, F., et al. 2004, Journal of Molecular Spectroscopy, 225, 152

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: casassus2022variable) Casassus, S. & Cárcamo, M. 2022, MNRAS, 513, 5790

(ref: cataldi2021molecules) Cataldi, G., Yamato, Y., Aikawa, Y., et al. 2021, ApJS, 257, 10

(ref: cazzoli2005lamb) Cazzoli, G. & Puzzarini, C. 2005, Journal of Molecular Spectroscopy, 233, 280

(ref: cazzoli2004precise) Cazzoli, G., Puzzarini, C., & Lapinov, A. V. 2004, ApJ, 611, 615

(ref: ceccarelli2014deuterium) Ceccarelli, C., Caselli, P., Bockelée-Morvan, D., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 859–882

(ref: chardon1973structure) Chardon, J. & Guichon, D. 1973, Journal de Physique, 34, 791

(ref: cleeves2015indirect) Cleeves, L. I., Bergin, E. A., & Harries, T. J. 2015, ApJ, 807, 2

(ref: cordiner2019carbon) Cordiner, M. A., Palmer, M. Y., de Val-Borro, M., et al. 2019, ApJL, 870, L26

(ref: cornwell2008) Cornwell, T. J. 2008, IEEE Journal of Selected Topics in Signal Processing, 2, 793

(ref: cridland2023planet) Cridland, A. J., Facchini, S., van Dishoeck, E. F., & Benisty, M. 2023, A&A, 674, A211

(ref: cridland2020connecting) Cridland, A. J., van Dishoeck, E. F., Alessi, M., & Pudritz, R. E. 2020, A&A, 642, A229

(ref: czekala2021molecules) Czekala, I., Loomis, R. A., Teague, R., et al. 2021, ApJS, 257, 2

(ref: daniel2013) Daniel, F., Gérin, M., Roueff, E., et al. 2013, A&A, 560, A3

(ref: drazkowska2023planet) Drazkowska, J., Bitsch, B., Lambrechts, M., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 717

(ref: evans2022fractionation) Evans, L., Fontani, F., Vastel, C., et al. 2022, A&A, 657, A136

(ref: bib:facchini2021chemical) Facchini, S., Teague, R., Bae, J., et al. 2021, AJ, 162, 99

(ref: faure2015methanol) Faure, A., Faure, M., Theulé, P., Quirico, E., & Schmitt, B. 2015, A&A, 584, A98

(ref: foreman2013emcee) Foreman-Mackey, D., Conley, A., Meierjurgen Farr, W., et al. 2013, emcee: The MCMC Hammer, Astrophysics Source Code Library, record ascl:1303.002

(ref: fuchs2004high) Fuchs, U., Bruenken, S., Fuchs, G. W., et al. 2004, Zeitschrift Naturforschung Teil A, 59, 861

(ref: furuya2022detection) Furuya, K., Tsukagoshi, T., Qi, C., et al. 2022, ApJ, 926, 148

(ref: brown2018gaia) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1

(ref: gandhi2023) Gandhi, S., de Regt, S., Snellen, I., et al. 2023, ApJL, 957, L36

(ref: gerakines2004ultraviolet) Gerakines, P., Moore, M., & Hudson, R. 2004, Icarus, 170, 202

(ref: gerakines2022direct) Gerakines, P. A., Yarnall, Y. Y., & Hudson, R. L. 2022, Monthly Notices of the Royal Astronomical Society, 509, 3515

(ref: gerner2015deuteration) Gerner, T., Shirley, Y. L., Beuther, H., et al. 2015, A&A, 579, A80

(ref: goldsmith1999population) Goldsmith, P. F. & Langer, W. D. 1999, ApJ, 517, 209

(ref: gregersen2001erratum) Gregersen, E. M. & Evans, Neal J., I. 2001, ApJ, 553, 1042

(ref: guzman2015cyanide) Guzmán, V., Öberg, K., Loomis, R., & Qi, C. 2015, The Astrophysical Journal, 814, 53

(ref: guzman2021molecules) Guzmán, V. V., Bergner, J. B., Law, C. J., et al. 2021, ApJS, 257, 6

(ref: guzman2017) Guzmán, V. V., Öberg, K. I., Huang, J., Loomis, R., & Qi, C. 2017, ApJ, 836, 30

(ref: haffert2019two) Haffert, S. Y., Bohn, A. J., de Boer, J., et al. 2019, Nature Astronomy, 3, 749

(ref: hatchell1998) Hatchell, J., Millar, T. J., & Rodgers, S. D. 1998, A&A, 332, 695

(ref: heays2014isotope) Heays, A. N., Visser, R., Gredel, R., et al. 2014, A&A, 562, A61

(ref: hily-blant2013nitrogen) Hily-Blant, P., Bonal, L., Faure, A., & Quirico, E. 2013, Icarus, 223, 582

(ref: hily-blant2017) Hily-Blant, P., Magalhaes, V., Kastner, J., et al. 2017, A&A, 603, L6

(ref: hily-blant2019multiple) Hily-Blant, P., Magalhaes de Souza, V., Kastner, J., & Forveille, T. 2019a, A&A, 632, L12

(ref: hily2019multiple) Hily-Blant, P., Magalhaes de Souza, V., Kastner, J., & Forveille, T. 2019b, A&A, 632, L12

(ref: hily-blant2020) Hily-Blant, P., Pineau des Forêts, G., Faure, A., & Flower, D. R. 2020, A&A, 643, A76

(ref: hogbom1974aperture) Högbom, J. A. 1974, A&AS, 15, 417

(ref: Hsu2024pds70b) Hsu, C.-C., Wang, J. J., Blake, G. A., et al. 2024, ApJL, 977, L47

(ref: huang2017alma) Huang, J., Öberg, K. I., Qi, C., et al. 2017, ApJ, 835, 231

(ref: Ikeda2002nitrogen) Ikeda, M., Hirota, T., & Yamamoto, S. 2002, ApJ, 575, 250

(ref: ilee2021molecules) Ilee, J. D., Walsh, C., Booth, A. S., et al. 2021, ApJS, 257, 9

(ref: isella2019detection) Isella, A., Benisty, M., Teague, R., et al. 2019, ApJL, 879, L25

(ref: izquierdo2023maps) Izquierdo, A. F., Testi, L., Facchini, S., et al. 2023, A&A, 674, A113

(ref: jensen2024fractionation) Jensen, S. S., Spezzano, S., Caselli, P., et al. 2024, A&A, 685, A149

(ref: jiang2023chemical) Jiang, H., Wang, Y., Ormel, C. W., Krijt, S., & Dong, R. 2023, A&A, 678, A33

(ref: jorsater1995high) Jorsater, S. & van Moorsel, G. A. 1995, AJ, 110, 2037

(ref: keppler2018discovery) Keppler, M., Benisty, M., Müller, A., et al. 2018, A&A, 617, A44

(ref: keppler2019highly) Keppler, M., Teague, R., Bae, J., et al. 2019, A&A, 625, A118

(ref: klapper2000sub) Klapper, G., Lewen, F., Gendriesch, R., Belov, S., & Winnewisser, G. 2000, Journal of Molecular Spectroscopy, 201, 124

(ref: lattanzi2007rotational) Lattanzi, V., Walters, A., Drouin, B. J., & Pearson, J. C. 2007a, ApJ, 662, 771

(ref: lattanzi2007hcop) Lattanzi, V., Walters, A., Drouin, B. J., & Pearson, J. C. 2007b, ApJ, 662, 771

(ref: law2024mapping) Law, C. J., Benisty, M., Facchini, S., et al. 2024, ApJ, 964, 190

(ref: law2023so) Law, C. J., Booth, A. S., & Öberg, K. I. 2023, ApJL, 952, L19

(ref: legal2020nitrogen) Le Gal, R., Öberg, K. I., Huang, J., et al. 2020, ApJ, 898, 131

(ref: lee2021modeling) Lee, S., Nomura, H., Furuya, K., & Lee, J.-E. 2021, ApJ, 908, 82

(ref: leemker2024chemistry) Leemker, M., Booth, A. S., van Dishoeck, E. F., Wölfer, L., & Dent, B. 2024, A&A, 687, A299

(ref: linsky2006) Linsky, J. L., Draine, B. T., Moos, H. W., et al. 2006, ApJ, 647, 1106

(ref: lodders2003sun) Lodders, K. 2003, ApJ, 591, 1220

(ref: loison2019chemical) Loison, J.-C., Wakelam, V., Gratier, P., & Hickson, K. M. 2019, MNRAS, 484, 2747

(ref: loomis2018distribution) Loomis, R. A., Cleeves, L. I., Öberg, K. I., et al. 2018, ApJ, 859, 131

(ref: lovas1992microwave) Lovas, F. J., Suenram, R., Ogata, T., & Yamamoto, S. 1992, Astrophysical Journal, Part 1 (ISSN 0004-637X), vol. 399, no. 1, p. 325-329., 399, 325

(ref: lyons2018carbon) Lyons, J. R., Gharib-Nezhad, E., & Ayres, T. R. 2018, in 49th Annual Lunar and Planetary Science Conference, Lunar and Planetary Science Conference, 2907

(ref: magalhaes2018nitrogen) Magalhães, V. S., Hily-Blant, P., Faure, A., Hernandez-Vera, M., & Lique, F. 2018, A&A, 615, A52

(ref: maiwald2000pure) Maiwald, F., Lewen, F., Ahrens, V., et al. 2000, Journal of Molecular Spectroscopy, 1, 166

(ref: mamajek2014) Mamajek, E. E. & Bell, C. P. M. 2014, MNRAS, 445, 2169

(ref: martinez2022high) Martinez-Brunner, R., Casassus, S., Pérez, S., et al. 2022, MNRAS, 510, 1248

(ref: marty2012earth) Marty, B. 2012, Earth and Planetary Science Letters, 313, 56

(ref: mcclure2023ice) McClure, M. K., Rocha, W., Pontoppidan, K., et al. 2023, Nature astronomy, 7, 431

(ref: meier1998deuteration) Meier, R., Owen, T. C., Jewitt, D. C., et al. 1998, Science, 279, 1707

(ref: millar1989deuterium) Millar, T. J., Bennett, A., & Herbst, E. 1989, ApJ, 340, 906

(ref: morbidelli2000source) Morbidelli, A., Chambers, J., Lunine, J. I., et al. 2000, Meteoritics & Planetary Science, 35, 1309

(ref: mousis200deuterium) Mousis, O., Gautier, D., Bockelée-Morvan, D., et al. 2000, Icarus, 148, 513

(ref: muller2005cologne) Müller, H. S., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: muller2000submillimeter) Müller, H. S. P., Klaus, T., & Winnewisser, G. 2000, A&A, 357, L65

(ref: muller2017submillimeter) Müller, H. S. P. & Lewen, F. 2017, Journal of Molecular Spectroscopy, 331, 28

(ref: mumma2011) Mumma, M. J. & Charnley, S. B. 2011, ARA&A, 49, 471

(ref: noble2012desorption) Noble, J. A., Theule, P., Mispelaer, F., et al. 2012, A&A, 543, A5

(ref: nomura2022isotopic) Nomura, H., Furuya, K., Cordiner, M. A., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 1075

(ref: oberg2021astrochemistry) Öberg, K. I. & Bergin, E. A. 2021, Phys. Rep., 893, 1

(ref: oberg2023protoplanetary) Öberg, K. I., Facchini, S., & Anderson, D. E. 2023, ARA&A, 61, 287

(ref: oberg2011effect) Öberg, K. I., Murray-Clay, R., & Bergin, E. A. 2011, ApJL, 743, L16

(ref: oberg2012evidence) Öberg, K. I., Qi, C., Wilner, D. J., & Hogerheijde, M. R. 2012, ApJ, 749, 162

(ref: okuzumi2019nonsticky) Okuzumi, S. & Tazaki, R. 2019, ApJ, 878, 132

(ref: padovani2009c2h) Padovani, M., Walmsley, C., Tafalla, M., Galli, D., & Müller, H. 2009, Astronomy & Astrophysics, 505, 1199

(ref: perez2015planet) Perez, S., Dunhill, A., Casassus, S., et al. 2015, ApJL, 811, L5

(ref: pinte2022kinematic) Pinte, C., Teague, R., Flaherty, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 645

(ref: portilla2023constraining) Portilla-Revelo, B., Kamp, I., Facchini, S., et al. 2023, A&A, 677, A76

(ref: rampinelli2024) Rampinelli, L., Facchini, S., Leemker, M., et al. 2024, A&A, 689, A65

(ref: ritchey2015) Ritchey, A. M., Federman, S. R., & Lambert, D. L. 2015, ApJL, 804, L3

(ref: roueff2015isotopic) Roueff, E., Loison, J. C., & Hickson, K. M. 2015, A&A, 576, A99

(ref: sastry1981laboratory) Sastry, K., Helminger, P., Charo, A., Herbst, E., & De Lucia, F. 1981, Astrophysical Journal, Part 2-Letters to the Editor, vol. 251, Dec. 15, 1981, p. L119, L120., 251, L119

(ref: sierra2021molecules) Sierra, A., Pérez, L. M., Zhang, K., et al. 2021, ApJS, 257, 14

(ref: smith2009high) Smith, R. L., Pontoppidan, K. M., Young, E. D., Morris, M. R., & van Dishoeck, E. F. 2009, ApJ, 701, 163

(ref: stark1999) Stark, R., van der Tak, F. F. S., & van Dishoeck, E. F. 1999, ApJL, 521, L67

(ref: teague2019gofish) Teague, R. 2019, The Journal of Open Source Software, 4, 1632

(ref: teague2019bettermoments) Teague, R. & Foreman-Mackey, D. 2019, bettermoments: Line-of-sight velocity calculation, Astrophysics Source Code Library, record ascl:1901.009

(ref: terzieva2000possibility) Terzieva, R. & Herbst, E. 2000, MNRAS, 317, 563

(ref: tinti2007hcop) Tinti, F., Bizzocchi, L., Degli Esposti, C., & Dore, L. 2007, ApJL, 669, L113

(ref: visser2018nitrogen) Visser, R., Bruderer, S., Cazzoletti, P., et al. 2018, A&A, 615, A75

(ref: vrtilek1987laboratory) Vrtilek, J., Gottlieb, C., & Thaddeus, P. 1987, Astrophysical Journal, Part 1 (ISSN 0004-637X), vol. 314, March 15, 1987, p. 716-725., 314, 716

(ref: wampfler2014nitrogen) Wampfler, S. F., Jørgensen, J. K., Bizzarro, M., & Bisschop, S. E. 2014, A&A, 572, A24

(ref: wang2021constraining) Wang, J. J., Vigan, A., Lacour, S., et al. 2021, AJ, 161, 148

(ref: weber2009hydrogen) Weber, A. S., Hodyss, R., Johnson, P. V., Willacy, K., & Kanik, I. 2009, The Astrophysical Journal, 703, 1030

(ref: wilson1999isotopes) Wilson, T. L. 1999, Reports on Progress in Physics, 62, 143

(ref: winnewisser1997sub) Winnewisser, G., Belov, S., Klaus, T., & Schieder, R. 1997, Sub-Doppler measurements on the rotational transitions of carbon monoxide

(ref: winnewisser1985millimeter) Winnewisser, M., Winnewisser, B. P., & Winnewisser, G. 1985, in NATO Advanced Study Institute (ASI) Series C, Vol. 157, NATO Advanced Study Institute (ASI) Series C, ed. G. H. F. Diercksen, W. F. Huebner, & P. W. Langhoff, 375–402

(ref: wirstrom2018) Wirström, E. S. & Charnley, S. B. 2018, MNRAS, 474, 3720

(ref: yoshida2019nitrogen) Yoshida, K., Sakai, N., Nishimura, Y., et al. 2019, PASJ, 71, S18

(ref: yoshida2024) Yoshida, T. C., Nomura, H., Furuya, K., et al. 2024, ApJ, 966, 63

(ref: yoshida2022) Yoshida, T. C., Nomura, H., Furuya, K., Tsukagoshi, T., & Lee, S. 2022, ApJ, 932, 126

(ref: zhang2017mass) Zhang, K., Bergin, E. A., Blake, G. A., Cleeves, L. I., & Schwarz, K. R. 2017, Nature Astronomy, 1, 0130

(ref: zhang202113co) Zhang, Y., Snellen, I. A. G., Bohn, A. J., et al. 2021, Nature, 595, 370

(ref: zhou2021hubble) Zhou, Y., Bowler, B. P., Wagner, K. R., et al. 2021, AJ, 161, 244

# Fluxes of Band 6 and 7 molecular lines

The spectral set up of Band 7 data (#2022.1.01695.S, PI M. Benisty) includes other molecular lines in addition to the HCN isotopologues ones: (3-2), CS (7-6), (4-3), and SO ($8_8-7_7$). Rest frequencies, imaging parameters, and line fluxes of the detected molecular transitions are listed in Table [\[tab:lines_b6b7\]](#tab:lines_b6b7). Cubes were obtained using natural weighting. Line fluxes are obtained by spatially integrating the integrated intensity maps of each line inside a de-projected circle with radius 3$^{\prime\prime}$ for the most extended , and 2$^{\prime\prime}$ for the others. The uncertainty is evaluated as the standard deviation of the flux measured in 26 de-projected circles, outside the emitting area of the integrated intensity maps, with the same radius used to extract the flux. We took the maximum number of circles that was possible to place on the image without overlap, and used not primary beam corrected images, to ensure uniform noise (cite: rampinelli2024). Table [\[tab:lines_b6b7\]](#tab:lines_b6b7) lists also detected lines in Band 6 data (#2019.1.01619.S, PI S. Facchini): the reader is referred to (cite: rampinelli2024) for more details on imaging strategies and line flux evaluation.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Species | Transition | Frequency | $\Delta \mathrm{v}$ | Beam | RMS | Flux |
|  |  | \[GHz\] | \[km s$^{-1}$\] |  | \[mJy beam$^{-1}$\] | \[mJy km s$^{-1}$\] |
| $^{12}$CO | 2-1 | 230.5380 | 0.1 | $0.28\ensuremath{''} \times 0.22\ensuremath{''}$ | 0.54 | 6175 $\pm$ 23 |
| $^{13}$CO | 2-1 | 220.3986 | 0.2 | $0.30\ensuremath{''} \times 0.24\ensuremath{''}$ | 0.42 | 1859 $\pm$ 12 |
| C$^{18}$O | 2-1 | 219.5603 | 0.2 | $0.31\ensuremath{''} \times 0.24$ | 0.33 | 466 $\pm$ 7 |
| H$_2$CO | 3$_{0,3}$-2$_{0,2}$ | 218.2221 | 0.4 | $0.29\ensuremath{''} \times 0.23\ensuremath{''}$ | 0.19 | 708 $\pm$ 7 |
| H$_2$CO | 3$_{2,1}$-2$_{2,0}$ | 218.7600 | 0.4 | $0.29\ensuremath{''} \times 0.23\ensuremath{''}$ | 0.20 | 57 $\pm$ 6 |
| C$_2$H | $3_{7/2, 4}$-$2_{5/2, 3}$ | 262.0042 | 0.4 | $0.20\ensuremath{''} \times 0.15\ensuremath{''}$ | 0.16 | 723 $\pm$ 10 |
| C$_2$H | $3_{7/2, 3}$-$2_{5/2, 2}$ | 262.0064 | 0.4 | $0.20\ensuremath{''} \times 0.15\ensuremath{''}$ | 0.16 | 577 $\pm$ 10 |
| H$^{13}$CN | 3-2 | 259.0117 | 0.4 | $0.20\ensuremath{''} \times 0.15\ensuremath{''}$ | 0.13 | 360 $\pm$ 8 |
| HC$^{15}$N | 3-2 | 258.1571 | 0.4 | $0.20\ensuremath{''} \times 0.15\ensuremath{''}$ | 0.15 | 176 $\pm$ 7 |
| DCN | 3-2 | 217.2386 | 0.4 | $0.29\ensuremath{''} \times 0.23\ensuremath{''}$ | 0.22 | 230 $\pm$ 6 |
| H$^{13}$CO$^+$ | 3-2 | 260.2553 | 0.4 | $0.21\ensuremath{''} \times 0.15\ensuremath{''}$ | 0.16 | 372 $\pm$ 7 |
| CS | 5-4 | 244.9355 | 1.4 | $0.22\ensuremath{''} \times 0.15\ensuremath{''}$ | 0.06 | 445 $\pm$ 6 |
|  | 3$_{2,1}$-2$_{1,2}$ | 244.2221 | 1.4 | $0.22\ensuremath{''} \times 0.16\ensuremath{''}$ | 0.07 | 16 $\pm$ 2 |
|  | 7$_{1,6}$-7$_{0,7}$ | 218.7327 | 0.4 | $0.29\ensuremath{''} \times 0.23\ensuremath{''}$ | 0.20 | 10 $\pm$ 3 |
|  | 7$_{2,6}$-7$_{1,7}$ | 218.7327 | 0.4 | $0.29\ensuremath{''} \times 0.23\ensuremath{''}$ | 0.69 | 10 $\pm$ 3 |
| $^{12}$CO | 3-2 | 345.7960 | 0.9 | $0.13\ensuremath{''} \times 0.12\ensuremath{''}$ | 0.76 | 13632 $\pm$ 42 |
| CS | 7-6 | 342.8829 | 0.9 | $0.13\ensuremath{''} \times 0.12\ensuremath{''}$ | 0.80 | 407 $\pm$ 31 |
|  | 4-3 | 356.7342 | 0.9 | $0.13\ensuremath{''} \times 0.11\ensuremath{''}$ | 0.96 | 5470 $\pm$ 31 |
|  | 4-3 | 345.3398 | 0.9 | $0.13\ensuremath{''} \times 0.11\ensuremath{''}$ | 0.70 | 530 $\pm$ 21 |
|  | 4-3 | 344.2003 | 0.9 | $0.13\ensuremath{''} \times 0.12\ensuremath{''}$ | 0.75 | 234 $\pm$ 34 |
|  | 4-3 | 354.5055 | 0.9 | $0.37\ensuremath{''} \times 0.34\ensuremath{''}$ | 1.82 | 5902 $\pm$ 45 |

Quantum numbers are formatted for (cite: chardon1973structure; muller2017submillimeter), (cite: bogey1986centrifugal; vrtilek1987laboratory; lovas1992microwave) as $N_{K_a, K_c}$, for C$_2$H as $N_{J, F_1}$ (cite: sastry1981laboratory; muller2000submillimeter; padovani2009c2h), for (cite: winnewisser1997sub), (cite: klapper2000sub; cazzoli2004precise), (cite: winnewisser1985millimeter), (cite: fuchs2004high; cazzoli2005lamb; maiwald2000pure), (cite: fuchs2004high; cazzoli2005lamb), (cite: brunken2004sub), (cite: gregersen2001erratum; lattanzi2007rotational), (cite: muller2005cologne; bogey1981millimeter; ahrens1999pure), (cite: tinti2007hcop; lattanzi2007hcop) as $J$.

The uncertainty does not include the 10% absolute flux calibration.

The value refers to the total flux of the blended (218 GHz) lines.

Listed beam size, RMS, and flux are obtained from SB observations only.

# Imaging procedure

To retrieve the radial profiles of nitrogen, carbon, and hydrogen fractionation of HCN, we performed two rounds of imaging to match the spatial resolution of Band 6 and 7 observations, respectively. We chose the robust and/or Gaussian $uv$-taper which resulted in cubes with beam areas as close as possible in the two cases. The imaging parameters used in the two cases, resulting beam sizes and areas, and RMS are listed in Tab. [\[tab:imaging_molecules_2\]](#tab:imaging_molecules_2). For the first case, only , , and DCN were imaged for the purpose of the analysis, while in the second case we also imaged the combined SB and LB observations of HCN. The resulting cube, with the corresponding beam size, beam area, and RMS listed in Tab. [\[tab:imaging_molecules_2\]](#tab:imaging_molecules_2) only covers half of the HCN (4-3) line.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Transition | robust | $uv$-taper | Beam | Beam area | $\epsilon$ | RMS |
|  |  |  |  | \[arcseconds$^2$\] |  | \[mJy beam$^{-1}$\] |
| H$^{13}$CN (3-2) | 0.67 | – | $0.15\ensuremath{''} \times 0.11\ensuremath{''}$ | 0.0178 | 0.45 | 0.60 |
| H$^{13}$CN (4-3) | 2.00 | – | $0.13\ensuremath{''} \times 0.12\ensuremath{''}$ | 0.018 | 0.24 | 0.70 |
| HC$^{15}$N (3-2) | 0.67 | – | $0.15\ensuremath{''} \times 0.11\ensuremath{''}$ | 0.018 | 0.45 | 0.71 |
| HC$^{15}$N (4-3) | 2.00 | – | $0.13\ensuremath{''} \times 0.12\ensuremath{''}$ | 0.0178 | 0.24 | 0.75 |
| DCN (3-2) | 0.30 | – | $0.14\ensuremath{''} \times 0.11\ensuremath{''}$ | 0.018 | 0.6 | 0.94 |
| HCN (4-3) | 2.00 | – | $0.13\ensuremath{''} \times 0.11\ensuremath{''}$ | 0.017 | – | 0.86 |
| H$^{13}$CN (3-2) | 2.00 | – | $0.20\ensuremath{''} \times 0.15\ensuremath{''}$ | 0.035 | 0.22 | 0.55 |
| H$^{13}$CN (4-3) | 2.00 | $0.064\ensuremath{''}$ | $0.19\ensuremath{''} \times 0.17\ensuremath{''}$ | 0.035 | 0.37 | 0.75 |
| HC$^{15}$N (3-2) | 2.00 | – | $0.20\ensuremath{''} \times 0.15\ensuremath{''}$ | 0.035 | 0.22 | 0.65 |
| HC$^{15}$N (4-3) | 2.00 | $0.064\ensuremath{''}$ | $0.19\ensuremath{''} \times 0.17\ensuremath{''}$ | 0.036 | 0.37 | 0.79 |
| DCN (3-2) | 0.80 | – | $0.19\ensuremath{''} \times 0.15\ensuremath{''}$ | 0.033 | 0.36 | 0.78 |

# Spectral smearing effect on brightness temperature

In this work we evaluated the optical depth of the analysed lines starting from their peak brightness temperature and excitation temperature (see Eq. [\[eq:tau\]](#eq:tau) in Sect. [3](#sec:column)). However, the brightness temperature may be underestimated due to spectral smearing related to a finite spectral resolution. To quantitatively estimate the effect of spectral smearing we imaged the same cube of the (3-2) line twice, with a different channel width, and we extracted the radial profile of the peak brightness temperature, as shown in Fig. [8](#fig:test_specsmearing). We compared the profiles starting from a cube with a channel width of 0.4 km s$^{-1}$ (blue profile), which is the smallest channel width allowed by the spectral resolution, and of 0.8 km s$^{-1}$ (red profile). As visible from Fig. [8](#fig:test_specsmearing), a lower peak brightness temperature corresponds to a larger channel width. Moreover, spectral smearing dominates at larger radii, which is expected by the decreasing line width. At smaller radii the effect is smaller, and also negligible with respect to statistical uncertainties. We highlight that even at larger radii a 10% variation in the peak brightness temperature corresponds to roughly 1% variation in the upper level population, for an excitation temperature of $\sim$30 K. This effect is thus negligible in the rotational diagram analysis we performed in this work.

![](images/Test_spectral_smearing.png)

# $^{12}$C/$^{13}$C ratio from the HCN hyperfine component

The / ratio of the HCN molecule in disks is typically extracted from and , assuming a fixed / ratio to convert the column density into an HCN column density, as the main isotopologue HCN is generally optically thick (cite: guzman2017). On the other hand, when hyperfine components of HCN are spectrally resolved, the HCN column density, optical depth and excitation temperature can be inferred, together with their radial profiles if hyperfine components are also spatially resolved (cite: hily2019multiple; guzman2021molecules). Long baseline observations of the HCN (4-3) line in the data we analysed only cover half of the main component spectrum, but they allow to resolve the hyperfine component at 354.5075 GHz. Figure [4](#fig:hyperfine_fit) shows the HCN spectra (dark blue line) extracted averaging over annuli at different radii (indicated on the top right of each panel), corrected for the Keplerian rotation of the disk using the `GoFish` package (cite: teague2019gofish). Only half of the main component is covered ($v_\mathrm{sys}=5.5$ km s$^{-1}$), but the hyperfine component at 354.5075 GHz is marginally spectrally resolved (peak at $v=3.8$ km s$^{-1}$), even with a spectral resolution of $\sim0.9$ km s$^{-1}$. We extracted the flux associated with the hyperfine component by fitting a double Gaussian to the spectrum, stopping at 5.5  km s$^{-1}$. We fixed the center of the two Gaussian components to 3.8 km s$^{-1}$ for the hyperfine and to 5.5 km s$^{-1}$ for the main component respectively, and fit for the two widths and peaks. We sampled the posterior distribution using an MCMC sampler through the `emcee` package (cite: foreman2013emcee). In order to take into account the spectral response, particularly critical for low spectral resolution, we spectrally over-sampled the Gaussian profiles and took the average value inside a spectral bin, to fit the observed spectrum. We applied the MCMC sampling to each annulus in which we divided the disk, with 128 walkers, 500 burn-in steps, and 500 steps, assuming a uniform prior of (0,5) km s$^{-1}$ for the two widths, of (0,10) mJy beam$^{-1}$ for the peak of the hyperfine component, and of (0,30) mJy beam$^{-1}$ for the peak of the main component.

Figure [4](#fig:hyperfine_fit) shows the result of the MCMC sampling, for each annulus (the radius is indicated on the top right of each panel). The dashed light blue line is the sum of the two best fit Gaussian profiles, the dashed orange line shows the best fit Gaussian for the hyperfine component, the solid orange lines are 100 random samples of the posterior distribution, while the dark blue profile is the observed spectrum with the related uncertainty. The uncertainty for each spectrum was evaluated as standard deviation of the spectrum in a signal-free spectral range. We extracted the flux by integrating the Gaussian profiles of the hyperfine component obtained from the posterior distribution, with the best fit value being the 50th percentile of the posterior distribution of such fluxes, and the related uncertainty evaluated from the 16th and the 84th percentiles. From the flux of the hyperfine component, and the related uncertainty, we extracted the radial profile of the column density of HCN, assuming that the hyperfine component is optically thin, and the same excitation temperature inferred from the rotational diagram analysis of and . The fiducial radial range is between $\sim50$ and 120 au, because for small radii the two components are blended, and the fit is poorly constrained, while for large radii the fit converges towards larger line widths, which are not physical. On the other hand, in the fiducial range the Gaussian fit to the hyperfine component is consistent with a radially constant line width. In this radial range, we extracted the / profile shown in the middle panel of fig. [5](#fig:12C13C), taking the ratio between the HCN and the column densities.

We could not smooth the HCN cube to match the spatial resolution of and Band 6 observations, as a worse spatial resolution would deteriorate the hyperfine fitting procedure (see also Sect. [3.3](#subsec:HCN_column)). We therefore imaged the Band 6 and cubes again with Briggs weighting and a robust parameter of 0.67 to match the spatial resolution of Band 7 observations. We then applied again the rotational diagram analysis, as shown in Sect. [3](#sec:column) and Fig. [2](#fig:profiles_rotdiagr): the new result of the column density profiles and excitation temperatures are shown in Fig. [9](#fig:profiles_rotdiagr_b7res). Similarly, we re-imaged the DCN cube with a robust parameter of 0.3 to match the beam size of Band 7 observations, and extract the column density profile. Figure [5](#fig:12C13C) shows the corresponding fractionation profiles.

![](images/rot_diagram_combined_tau_profiles_b7res_dTb.png)

# HCN emitting layer from the excitation temperature

As we mentioned in Sect. [4.1](#subsec:disc:N), the distribution of the $\mu$m dust can influence the efficiency of isotope selective photodissociation of , as it attenuates UV photons. It could be therefore important to constrain the emitting layer height of HCN with respect to the small dust. We tried to retrieve the emitting layer, by comparing the radial profile of the excitation temperature in Fig. [2](#fig:profiles_rotdiagr) with the 2D temperature structure of the PDS 70 disk, extracted by (cite: law2024mapping), from CO isotopologues and . The rotational diagram assumes that the excitation temperature $T_\mathrm{ex}(r)$ is equal to the kinetic temperature $T(r,z)$ (LTE). We therefore inverted the $T(r,z)$ relation (cite: law2024mapping) to extract the emitting layer $z(r)$ (cite: ilee2021molecules; rampinelli2024), assuming a geometrically thin emitting layer, and that the HCN excitation temperature is the same as the one obtained for and . The result is presented in Fig. [10](#fig:layer_hcn) (pink line), but the large uncertainties make it inconclusive.

![](images/layer_hcn_CO.png)

# HCN fractionation across the timeline of star and planet formation

A summary of the hydrogen, carbon, and nitrogen fractionation of HCN in various astronomical objects at different stages of star and planet formation is presented in Fig. [7](#fig:frac_stages).

**DCN/HCN**: The solar and ISM isotopic ratios are obtained from atomic hydrogen (cite: lodders2003sun; linsky2006). Hot core DCN/HCN ratios were extracted from observations taken with the Arizona Radio Observatory Submillimeter Telescope (SMT) (cite: gerner2015deuteration). Column densities were extracted by correcting for the line optical depth, assuming the best-fit excitation temperature obtained from a 1D physico-chemical model with time-dependent D-chemistry (cite: gerner2015deuteration). We highlight that these results are in tension with DCN/HCN ratios previously extracted for the same sources by (cite: hatchell1998), from DCN and observations taken with the James Clerk Maxwell Telescope, which result in DCN/HCN values up to approximately an order of magnitude lower than the ones presented by (cite: gerner2015deuteration). The five DCN/HCN values presented for class 0/I sources (cite: bergner2020deuteration) were obtained from ALMA observations, evaluating HCN column densities from , assuming an ISM , $T_\mathrm{ex}=30$ K, and co-spatial emission from the different isotopologues. Disk integrated values of DCN/HCN were extracted for the protoplanetary disks of AS 209, IM Lup, V4046 Sgr, LkCa 15, and HD 163296 from ALMA observations of and DCN (cite: huang2017alma). The only DCN/HCN ratio measured for comets was obtained from James Clerk Maxwell Telescope observations of the Hale-Bopp comet (cite: meier1998deuteration). The deuteration level was measured from the line ratios of DCN and , assuming a solar , but also directly from the main isotopologue HCN, by correcting for its optical depth through the hyperfine components, leading to consistent results.

**HCN/**: The ISM isotope ratio was obtained from atomic carbon (cite: wilson1999isotopes), while the solar value was obtained from CO (cite: lyons2018carbon). HCN/ ratios were extracted for the prestellar core Bernard 1b (cite: daniel2013), L1498 (cite: magalhaes2018nitrogen), the six starless and prestellar cores CB23, TMC2, L1495, L1495AN, L1512, and L1517B (cite: jensen2024fractionation) and the class 0 YSO L483 (cite: agundez2019carbon) from IRAM observations. The HCN/ value for the disk around TW Hya was extracted from ALMA observations (cite: hily-blant2019multiple). Cometary HCN/ ratios were obtained for Hale-Bopp (cite: bockelee2008HCNcomets) from Harlan J. Smith Telescope observations, and for C/2012 S1 ISON (cite: cordiner2019carbon) from ALMA observations leveraging the hyperfine components of the observed HCN line.

**HCN/**: The solar and ISM isotopic ratios were obtained from atomic nitrogen (cite: marty2012earth; ritchey2015). The prestellar/protostellar values are taken from (cite: hily-blant2020). The first direct measurement of HCN/ was extracted for the prestellar core L1498 (cite: magalhaes2018nitrogen) and subsequently for the six starless and prestellar cores CB23, TMC2, L1495, L1495AN, L1512, and L1517B (cite: jensen2024fractionation), using a 1D radiative transfer code handling hyperfine overlap. The remaining HCN/ values for prestellar cores L183, L1544 (cite: hily-blant2013nitrogen), L1521E (cite: Ikeda2002nitrogen), protocluster OMC-2 FIR4 (cite: evans2022fractionation), and class 0/I YSOs FIR3 (cite: evans2022fractionation), L1527 (cite: yoshida2019nitrogen), IRAS 16293A, OMC-3, R CrA IRS7B (cite: wampfler2014nitrogen), I-04365, I-04016, I-04166, I-04169, I-04181 (cite: legal2020nitrogen), Ser-emb 1, 7, 8, 15, 17 (cite: bergner2020deuteration) were obtained from a so-called double-isotope indirect method, assuming a fixed ratio. The only direct measurement of the HCN/ ratio in protoplanetary disks was obtained for the disk around TW Hya (cite: hily-blant2019multiple), while for the disks around AS 209, LkCa 15, and V4046 Sgr it was obtained from ALMA observations of and and assuming an ISM ratio (cite: guzman2017). Cometary HCN/ were presented for 17P/Holmes and Hale-Bopp (cite: bockelee2008HCNcomets) from IRAM, Harlan J. Smith, and Keck telescopes observations, and leveraging the hyperfine components of the observed HCN line.

</paper>

Write the methods card for this paper.