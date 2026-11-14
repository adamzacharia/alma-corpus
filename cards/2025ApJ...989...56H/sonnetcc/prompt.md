# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...989...56H\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...989...56H",
 "title": "ALMASOP. A Rotating Feature Rich in Complex Organic Molecules in a Protostellar Core",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Hsu, Shih-Ying",
 "n_authors": 28,
 "arxiv_id": "2506.15140",
 "doi": "10.3847/1538-4357/ade7fc",
 "alma_projects_linked_by_archive": [
  "2018.1.00302.S"
 ]
}
```

Paper text:
<paper>
# ALMASOP. A Rotating Feature Rich in Complex Organic Molecules in a Protostellar Core

## Abstract

Interstellar complex organic molecules (COMs) in solar-like young stellar objects (YSOs), particularly within protostellar disks, are of significant interest due to their potential connection to prebiotic chemistry in emerging planetary systems. We report the discovery of a rotating feature enriched in COMs, including CH$_3$OH, CH$_3$CHO, and NH$_2$CHO, in the protostellar core G192.12-11.10. By constructing a YSO model, we find that the COM-rich feature is likely located within or near the boundary of the Keplerian disk. The image synthesis results suggest that additional heating mechanisms leading to a warm ring or a warm inner disk are required to reproduce the observed emission. We discuss possible origins of the COM-rich feature, particularly accretion shocks as a plausible cause for a warm ring. Additionally, molecules such as C$^{18}$O, H$_2$CO, DCS, H$_2$S, and OCS exhibit distinct behavior compared to CH$_3$OH, indicating a range of physical and chemical conditions within the region. The observed kinematics of H$_2$S and OCS suggest that OCS resides in regions closer to the central protostar than H$_2$S, consistent with previous experimental studies.

UTF8bsmi

# Introduction

Interstellar complex organic molecules (COMs) in solar-like young stellar objects (YSOs) are of great interest due to their potential connection to prebiotic chemistry in emerging planetary systems. These COMs are thought to form on the icy mantles of dust grains via grain-surface reactions. During the protostellar stage, they are released into the gas phase primarily through thermal desorption, triggered when the temperature rises above the ice sublimation threshold of approximately 100 K (cite: 2009Herbst_COM_review; 2020Jorgensen_review). In addition, several non-thermal desorption mechanisms have been proposed to explain the presence of gas-phase COMs in colder environments (cite: 2010Oberg_B1b; 2013Vasyunin_reactive_desorption; 2016Jimenez-Serra_L1544; 2021Wakelam_non-thermal_desorption).

A major breakthrough in observational studies was the discovery of hot corinos, as named by (cite: 2004Ceccarelli_HotCorino), which are localized warm regions rich in COMs surrounding solar-like YSOs. In the first decade following the discovery of hot corinos, only a small number of protostellar cores were found to host warm COMs. Thanks to advances in technology and observatories such as the Atacama Large Millimeter/sub-millimeter Array (ALMA), recent survey-type studies have discovered a good number of protostellar cores harboring COMs (cite: 2020Belloche_CALYPSO; 2021Yang_PEACHES; 2020Hsu_ALMASOP; 2022Hsu_ALMASOP; 2022Bouvier_ORANGES). Moreover, (cite: 2023Hsu_ALMASOP) demonstrated that gas-phase COMs can be ubiquitous in protostellar cores, provided that the innermost envelope is sufficiently heated by the central protostar. Other mechanisms in addition to the heating from the central protostar can also contribute to COM desorption, resulting in a variety of morphologies and kinematics for the observed COM emission. To date, COMs have been detected in various YSO environments, including the innermost envelope (cite: 2019Jacobsen_L483_COM), outflow shock fronts (cite: 2008Arce_L1157-B1_COMs), jet bases (cite: 2024Hsu_ALMASOP), disk winds (cite: 2024DeSimone_IRAS4A2_COMdiskwind), and disk atmosphere (cite: 2017Lee_HH212; 2019Lee_HH212_COM_atm).

Particularly, the presence of COMs near disks is of considerable importance, as these disks serve as the nurseries for planets, comets, and asteroids. So far, only a handful of disks have reported the detection of COMs, such as those in a Class 0 protostellar core HH 212 (cite: 2016Codella_HH212_H2O_COM; 2017Lee_HH212; 2019Lee_HH212_COM_atm; 2022Lee_HH212_stratification), a Class I/II protostellar core V883 Ori (cite: 2018vantHoff_V883Ori_CH3OH; 2019Lee_V883-Ori_outburst; 2025Jeong_V883Ori_COM; 2025Fadul_V883Ori), a T Tauri star TW Hya (cite: 2016Walsh_TWHya_CH3OH), a T Tauri star DG Tau (cite: 2015Loomis_DMTau), a Herbig Ae star HD 163296 (cite: 2019Carney_HD163296_COM), a young star Oph IRS 48 (cite: 2021vanderMarel_OphIRS48_H2CO_CH3OH; 2022Brunken_OphIRS48_COM) and an A-type star HD 100546 (cite: 2021Booth_HD100546_COM). Since the presence of gas-phase COMs requires a desorption mechanism, studying these molecules also provides valuable insights into the physical processes occurring within disks. For example, in HH 212, some COMs near the disk edge are proposed to be released by heat from accretion shocks, while others farther from the edge may be desorbed by radiation from the central protostar or interactions with disk winds (cite: 2017Lee_HH212; 2017Tabone_HH212_cavity; 2022Lee_HH212_stratification). In V883 Ori, COMs were freshly desorbed due to a stellar outburst (cite: 2019Lee_V883-Ori_outburst; 2025Jeong_V883Ori_COM). To advance our understanding of organic chemistry in protostellar disks, it is crucial to investigate more protostellar systems.

Here, we report the discovery of a COM-rich rotating feature likely residing in the disk of the protostellar core G192.12-11.10 (05$^\mathrm{h}$32$^\mathrm{m}$19$^\mathrm{s}$ +12$\ensuremath{^\circ}$49$\hbox{$^\prime$}$40$\hbox{$^{\prime\prime}$}$), which is located in the $\lambda$-Orionis cloud (cite: 2011Lombardi_2MASS_extinction_IV). This protostellar core was previously identified as a source of warm COM emission in the ALMA Survey of Orion PGCCs (ALMASOP) project (cite: 2020Hsu_ALMASOP; 2022Hsu_ALMASOP). In this paper, we further reveal the rotating nature of the COM within the core. We introduce the observational programs in §[2](#sec:Obs) and present the observed morphologies and kinematics in §[3](#sec:results). Based on our observations, we construct a model for the YSO, which is described in §[4](#sec:model). In §[5](#sec:Disc), we discuss the possible origin of the COM-rich rotating feature and its implications. Finally, we summarize our conclusions in §[6](#sec:Conclusions).

![](figures/img_main.pdf)

# Observations

This study mainly uses data obtained from the ALMA Cycle 6 program #2018.1.00302.S, (PI: Tie Liu) in Band 6 (1.3 mm or 230 GHz) with the combination of both 12-m array (configurations C43–5 and C43–2) and 7-m array (also known as the Atacama Compact Array, ACA, or Morita Array). The projected baselines ranged from 6 to 965 k$\lambda$, and the resulting maximum recoverable scale was approximately 26$^{\prime\prime}$. The four spectral windows centered at 216.6, 218.9, 231.0, and 233.0 GHz have a uniform bandwidth of 1,875 MHz with a spectral resolution of 1.129 MHz (1.4  km s$^{-1}$ at 230 GHz).

We used `tclean` in CASA (cite: casa:2022) with a robust value of 0.5. The resulting angular resolution was $\sim$ 0$.\!\!^{\prime\prime}$42 (cite: 2011Lombardi_2MASS_extinction_IV). The sensitivities of the image reach $\sim$0.43  mJy beam$^{-1}$ (0.10 K) and $\sim$3.5  mJy beam$^{-1}$ (0.84 K) for the full–band continuum and each channel, respectively. For more details on the ALMASOP project, please refer to (cite: 2020Dutta_ALMASOP).

![](figures/PV_main.pdf)

# A First Look at the Observed Features

## Morphology

Figure [1](#fig:img_main)(a) and (b) show the integrated intensity images of CO $J=2-1$ and C$^{18}$O $J=2-1$ transitions, respectively, overlaid with 1.3 mm dust continuum. The CO $J=2-1$ integrated intensity image reveals wide and extended outflow lobes having a position angle (PA) of $25^\circ$ (i.e., oriented along a northeast-southwest axis). The presence of red-shifted outflow in both lobes suggests that the system is likely close to an almost edge-on system. The dust continuum is distinctly elongated in this northwest-southeast direction, perpendicular to the outflow axis. In Figure [1](#fig:img_main)(b), the C$^{18}$O $J=2-1$ emission is spatially extended, displaying two peaks aligned with the major axis of the dust continuum, each located on opposite sides of the outflow axis. The distance between the two peaks is roughly 0$.\!\!^{\prime\prime}$5 (or $\sim220$ au). These morphologies suggest that the continuum is illustrating the inner dense envelope-disk system, and C$^{18}$O is predominately tracing the circumstellar envelope.

Figure [1](#fig:img_main)(e) presents the integrated intensity images for the blue- and red-shifted channels separately. The extended C$^{18}$O gas exhibits rotation with an axis along the outflow. The western and eastern regions are red- and blue-shifted, respectively. Moreover, the blue and red peaks in Figure [1](#fig:img_main)(e) coincide with the two peaks in Figure [1](#fig:img_main)(b). Consistently, as implied by Figure [1](#fig:img_main)(d), the molecular outflow likely rotates around an axis directed toward the northeast. Additionally, in the northeast region, the significant overlap between the blue- and red-shifted outflows suggests that the system’s geometry is predominantly edge-on.

Interestingly, as shown in Figures [1](#fig:img_main)(c) and (f), CH$_3$OH appears to be rotating along an axis consistent with the envelope. Similar to C$^{18}$O, the blue- and red-shifted integrated intensity images of CH$_3$OH show distinct peaks; however, the separation between the blue and red peaks is significantly smaller than that of C$^{18}$O. A notable difference is that the integrated intensity image of CH$_3$OH across the full spectrum, as shown in Figure [1](#fig:img_main)(c), does not exhibit two peaks or significant elongation but instead remains compact. This suggests that CH$_3$OH gas is residing in the inner rotating regions near the central protostar, possibly the disk or the inner envelope.

![](figures/PV_formulae_main.pdf)

## Kinematics

To look at the kinematics of the envelope-disk system, we extracted position-velocity (PV) diagrams across the outflow axis (the major axis of the continuum, as illustrated by the dashed line in Figure [1](#fig:img_main)). Figure [2](#fig:PV_main) presents the PV diagrams for the C$^{18}$O $J=2-1$ and CH$_3$OH $5_{1,4}$ – $4_{2,4}$ transitions. Both diagrams show that the eastern region ($\Delta p > 0$) is blue-shifted, while the western region ($\Delta p < 0$) is red-shifted, indicating that C$^{18}$O and CH$_3$OH share the same rotation direction. Despite this similarity, the PV diagrams of C$^{18}$O and CH$_3$OH exhibit distinct features, emphasizing their differing physical origins.

C$^{18}$O shows a typical pattern associated with an infalling and rotating envelope (cite: 2014Sakai_L1527_envelope; 2014Oya_IRAS15398-3359; 2017Lee_HH212). On the one hand, the PV diagram features an elongated distribution close to the region where $\Delta v=0$. On the other hand, taking the red-shifted part as an example, as the relative position approaches the center, $|\Delta v|$ gradually increases before dropping at a specific relative position. This feature serves as an indicator of the disk-envelope interface, although its precise derivation depends on the specific model used.

In contrast, the velocity gradient of CH$_3$OH appears to be linear. This linear pattern indicates that CH$_3$OH is exhibiting rotation within a ring. The maximum relative speed ($|\Delta v|$) of CH$_3$OH exceeds that of C$^{18}$O, supporting that the former is tracing the more inner region than the latter. Also, the CH$_3$OH PV diagram tentatively shows a high-velocity tail at $\Delta v < -5$  km s$^{-1}$, hinting at its possible presence in the disk region. The linearity can be described as: $$\begin{equation}
    \label{eq:dp_dv}
    \left ( \frac{\Delta p}{0.20~\mathrm{arcsec}} \right )=\left ( \frac{\Delta v}{5~\mathrm{km~s^{-1}}} \right ). 
\end{equation}$$ Assuming that the disk mass is much smaller than the stellar mass and an edge-on geometry, the relative velocity along the line of sight ($\Delta v$) at a relative position ($\Delta p$) following of a ring with Keplerian rotation is: $$\begin{equation}
    \Delta v=\sqrt{\frac{GM_\star}{R_\mathrm{ring}}}\,\frac{\Delta p}{R_\mathrm{ring}}, 
\end{equation}$$ where $M_\mathrm{\star}$ and $R_\mathrm{ring}$ are the stellar mass and ring radius, respectively. Given a distance of 445 pc (cite: 2011Lombardi_2MASS_extinction_IV) and substituting the relation between $\Delta v$ and $\Delta p$ from Eq. [\[eq:dp_dv\]](#eq:dp_dv), this equation can be approximated as: $$\begin{equation}
    \label{eq:PV_CH3OH}
    M_\mathrm{*} = 3.56\,M_\odot \times \left ( \frac{R_\mathrm{ring}}{\mathrm{100~au}} \right )^3. 
\end{equation}$$ To further evaluate the size of the CH$_3$OH-rich feature, it is essential to constrain the stellar mass. This is addressed through YSO modeling, as discussed in Section [4](#sec:model).

## Molecular Diagnostics

In addition to CO, C$^{18}$O, and CH$_3$OH, our ALMASOP observations detected several other molecular species, including CH$_3$CHO, HNCO, NH$_2$CHO, H$_2$CO, DCN, H$_2$S, and OCS. Table [\[tab:molec\]](#tab:molec) provides details of the observed transitions, and Figure [11](#fig:img_appx) presents the corresponding integrated intensity images. For molecules with multiple detected transitions, as listed in Table [\[tab:molec\]](#tab:molec), we stacked the flux densities to improve the signal-to-noise ratio. As shown in Figure [11](#fig:img_appx), these molecules (CH$_3$OH, CH$_3$CHO, HNCO, NH$_2$CHO, H$_2$CO, DCN, H$_2$S, and OCS) exhibit a single-peaked morphology. Interestingly, although these molecules share this general spatial distribution, their kinematic properties display distinct patterns, suggesting different origins or underlying physical processes.

As shown in Figure [3](#fig:PV_formulae_main), the detected molecules can be broadly classified into two groups. The first group, illustrated in Figure [3](#fig:PV_formulae_main) (a)–(d), includes CH$_3$OH, CH$_3$CHO, HNCO, and NH$_2$CHO. These molecules all display linear distributions in the PV diagrams haveing similar slopes. This suggests that they are residing within the discovered CH$_3$OH-rich rotating feature, further indicating that this feature is not only abundant in CH$_3$OH but also in other COMs.

In contrast, as shown in Figure [3](#fig:PV_formulae_main) (e)–(h), H$_2$CO, H$_2$S, OCS, and DCN exhibit a different kinematic signature from the COMs above. First, at low velocities ($|\Delta v| < 2$ km s$^{-1}$), they all display extended emission ($|\Delta p| > 0\hbox{$.\!\!^{\prime\prime}$}{5}$), suggesting that these molecules are residing in the envelope. Meanwhile, in the inner region ($|\Delta p| < 0\hbox{$.\!\!^{\prime\prime}$}{5}$), the observed velocities significantly exceed the PV boundary derived from C$^{18}$O, and the emission shows two distinct peaks, one red-shifted and one blue-shifted. Such a pattern suggests that these molecules are located closer to the center. If C$^{18}$O traces perfectly the envelope, these molecules also reside within the disk.

# Young Stellar Object Modeling

In this section, we present the young stellar object (YSO) modeling. A typical YSO model consists of a central protostar, a rotating disk, an infalling envelope, and an outflow cavity. Developing a complete model requires numerous parameters, including the mass, temperature, and radius of the central protostar; the infall rate and size of the envelope; the mass, size, and shape of the disk; and the shape of the outflow cavity. We begin by deriving some of these parameters directly from our observations. For the remaining parameters, we perform spectral energy distribution (SED) fitting using a grid of models.

## Outflow Cavity

![](figures/best_cav.pdf)

We start by evaluating the inclination angle ($\varphi$) and the parameters describing the outflow cavity walls using the CO $J=2-1$ observations. The molecular CO outflow cavity was modeled as a radially expanding shell driven by an underlying wide-angle wind (cite: 2000Lee_jet_wind_model). First, the velocity components along the $R$ and $z$ directions can be expressed using a velocity factor ($\Tilde{v}$) as: $$\begin{equation}
    v_\mathrm{R} =\Tilde{v} \, R
\end{equation}$$ and $$\begin{equation}
    v_\mathrm{z} =\Tilde{v} \, z. 
\end{equation}$$ Considering an inclination angle ($\varphi$), the maximum projected blue- and red-shifted velocities along the line of sight at any point on the outflow axis $(R, z)$ is: $$\begin{equation}
    v_\mathrm{proj}^\mathrm{blue} = v_\mathrm{R}\sin\varphi + v_\mathrm{z}\cos\varphi, 
\end{equation}$$ and $$\begin{equation}
    v_\mathrm{proj}^\mathrm{red} = -v_\mathrm{R}\sin\varphi + v_\mathrm{z}\cos\varphi
\end{equation}$$ and the projected height of the cavity wall is: $$\begin{equation}
    z_\mathrm{proj} = z\sin\varphi. 
\end{equation}$$

To determine the the inclination angle ($\varphi$) as well as the velocity factor ($\Tilde{v}$), we selected characteristic PV data points from the CO $J=2-1$ PV diagram along the outflow axis, as shown in Figure [4](#fig:best_cav) (a). The characteristic PV data points were selected to trace the arm-like pattern, which is a feature of the wide-angle wind model (cite: 2000Lee_jet_wind_model). The $z_\mathrm{proj}$ in the model is the $\Delta p$ in the PV diagram, and the $v_\mathrm{proj}^\mathrm{blue}$ and $v_\mathrm{proj}^\mathrm{red}$ are the negative and positive boundaries of $\Delta v$ at a given $\Delta p$. We fit the outflow model parameters by minimizing the $\chi^2$ value at each $\Delta v$ of the selected characteristic points in Figure [4](#fig:best_cav).

Our best-fit parameters obtained through this process are $\varphi=93^{\circ}$ and $\Tilde{v}=1.7$ km au$^{-1}$s$^{-1}$. The angle of inclination of $93^{\circ}$ suggests that the system is nearly edge-on, with the northern lobe slightly tilted toward Earth (blue-shifted). In the following, we ignore this tiny inclination and assume that the system is purely edge-on.

Next, the cavity wall can be described in cylindrical coordinate $(R, \phi, z)$ with two parameters, $a_\mathrm{cav}$ and $b_\mathrm{cav}$, as: $$\begin{equation}
    \label{eq:cav_wall}
    (\frac{z}{\mathrm{1~au}}) = a_\mathrm{cav}\,(\frac{R}{\mathrm{1~au}})^{b_\mathrm{cav}}. 
\end{equation}$$ These parameters of the wall were estimated using the gradient map of the CO integrated intensity (moment-0) image. We computed the sum of the gradient map values along paths defined by a set of cavity walls, each characterized by sampled parameters $b_\mathrm{cav}$ and $a_\mathrm{cav}$. The combination yielding the highest total (i.e., best-matching between the model and the observed gradient structure) was selected as the best-fit solution. The parameter $b_\mathrm{cav}$ was sampled at three values: 1.00, 1.25, 1.50, and 1.75. For each value of $b_\mathrm{cav}$, $a_\mathrm{cav}$ was chosen such that the radius $R$ spans from 1$^{\prime\prime}$to 2$^{\prime\prime}$at a height of $z=3\hbox{$^{\prime\prime}$}$, assuming a distance of 445 pc, adopting Eq. [\[eq:cav_wall\]](#eq:cav_wall). The best-fit values, having the maximum sum, are $b_\mathrm{cav}$$=1.25$ with $a_\mathrm{cav}$$=0.4$, as shown in Figure [4](#fig:best_cav) (b). The derived exponent of 1.25 is smaller than the commonly assumed value of 1.5 (cite: 2016Furlan_HOPS), and the resulting wide cavity suggests that this source is more likely more evolved (cite: 2023Hsieh_outflow; 2024Dunham_outflow).

![](figures/best_env.pdf)

maps. The magenta curves in the top panel illustrate our best-fit models and the white lines in the bottom panel illustrate the disk size. The gold rectangle at the bottom left of the top panel represents the beam size and spectral resolution.

## Envelope-disk System

Two envelope models are commonly used to describe the dynamics of protostellar systems. The first is the Ulrich-Cassen-Moosman (UCM or CMU) model, which characterizes a three-dimensional, azimuthally symmetric flow of rotating and infalling gas (cite: 1976Ulrich_CMU; 1981Cassen_CMU; 2004Mendoza_UCM). The second is a simplified two-dimensional model introduced by (cite: 2014Sakai_L1527_envelope), based on the earlier work of (cite: 1997Ohashi_IRAS043682557), which assumes azimuthal symmetry and restricts all motion to the midplane (cite: 1997Ohashi_IRAS043682557; 2014Sakai_L1527_envelope; 2014Oya_IRAS15398-3359; 2022Oya_FERIA; 2024Mori_model_UCM). In this study, we adopt the former.

The radius at which the gravitational force balances the centrifugal force in the midplane is defined as the centrifugal radius ($R_\mathrm{C}$) and is expected to closely correspond to the disk radius. Within the disk radius, the velocity is described by Keplerian rotation.

We derived the relations between the line-of-sight velocity and the position on the midplane for an edge-on envelope-disk system. First, at the midplane of a UCM model under the spherical coordinate system ($r, \theta = 90^\circ, z=0$), the velocity components are: $$\begin{align}
    v_r &= -\left (\frac{GM}{r} \right )^\frac{1}{2} \\
    v_\theta &= 0 \\
    v_\phi &= \left (\frac{GM}{r} \right )^\frac{1}{2}, 
\end{align}$$ where $G$ is the gravitational constant and $M$ is the central mass ($M_\mathrm{cen}=M_* + M_\mathrm{disk}$). For an edge-on system, at a given point $(x, y)$, the velocity along the line of sight (x-direction, $v_\mathrm{los}$) is: $$\begin{align}
    v_\mathrm{los} &= v_r \cos\phi - v_\phi \sin\phi \\
    &= -\sqrt{GM} \, \left ( x^2+y^2 \right )^{-\frac{3}{4}}\,(y+x), 
\end{align}$$ where $\phi$ is the polar angle (i.e., $\sin\phi=y/r$ and $\cos\phi=x/r$). Given a position along the midplane ($y$), the two local $v_\mathrm{los}$ extrema occur at: $$\begin{equation}
x_\pm=\frac{-3\pm\sqrt{17}}{2}y\,\,\,.
\end{equation}$$ The two solutions represent the boundaries of the PV diagram at a given position y along the midplane. Each of them is replaced by $\pm\sqrt{R_C^2-y^2}$ if it is within the disk outer radius setting at the centrifugal radius $R_C$.

We assumed that the C$^{18}$O emission is dominated by the extended envelope and derived the envelope parameters with its PV diagram. The PV diagram for C$^{18}$O were extracted along the major axis (i.e., perpendicular to the outflow axis). We measured the velocity boundaries (i.e., the maxima of the red and blue velocity shifts) at each position and fit the PV diagram by varying the centrifugal radius ($R_C$) and the central mass ($M_\mathrm{cen} = M_* + M_\mathrm{disk}$) We then fit the envelope model by minimizing the $\chi^2$-value between the modeled and observed velocity boundaries.

The best-fit parameters obtained are $R_C=145~\mathrm{au}$ and $M_\mathrm{cen}=1.50~M_\odot$. In this envelope-disk model, the centrifugal radius ($R_C$) is the boundary between the envelope and the disk. As shown in Figure [5](#fig:best_env) (a), the modeled PV diagram (magenta curve) is well-matching the shape of the C$^{18}$O PV diagram. In Figure [5](#fig:best_env) (b), we show the modeled disk size (white lines) and the observed 1.3 mm dust continuum (black contours) on the observed C$^{18}$O integrated intensity map (rasters).

+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| Symbol                  | Description                           | Best-fit value                          | Sampled Value                                                          |   |
+:========================+:======================================+:========================================+:=======================================================================+:==+
| Protostar                                                                                                                                                                          |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $M_*$                   | Stellar mass                          | 1.3 $M_\odot$                           | $1.50M_\odot-M_\mathrm{disk}$                                          |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $T_*$                   | Stellar effective temperature         | 7000 K                                  | 5000, 6000, 7000, 8000 K                                               |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $r_*$                   | Stellar radius                        | 2 $R_\odot$                             | 1, 2, 3, 4, 5, 6 $R_\odot$                                             |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| Envelope                                                                                                                                                                           |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $r_\mathrm{env}$        | Envelope outer radius                 | 10,000 au                               |                                                                        |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $r_\mathrm{min}$        | Inner radius                          | $R_\mathrm{sub}$                        |                                                                        |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $\dot{M}_\mathrm{env}$  | Mass infall rate                      | $10^{-4.0}$ $M_\odot\,\mathrm{yr}^{-1}$ | $10^{-5.0}$, $10^{-4.5}$, $10^{-4.0}$, $10^{-3.5}$ $M_\odot$ yr$^{-1}$ |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| Disk                                                                                                                                                                               |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $M_\mathrm{disk}$       | Disk mass                             | 0.20 $M_\odot$                          | 0.05, 0.10, 0.15, 0.20, 0.25 $M_\odot$                                 |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $R_\mathrm{disk}$       | Disk outer radius                     | 145 au                                  |                                                                        |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $R_\mathrm{min}$        | Inner radius                          | $R_\mathrm{sub}$                        |                                                                        |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $\dot{M}_\mathrm{disk}$ | Mass accretion rate                   | $10^{-6.0}$ $M_\odot\,\mathrm{yr}^{-1}$ | $10^{-7.0}$, $10^{-6.5}$, $10^{-6.0}$, $10^{-5.5}$ $M_\odot$ yr$^{-1}$ |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $A_\mathrm{disk}$       | Radial exponent in disk density law   | 2.25                                    |                                                                        |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $B_\mathrm{disk}$       | Vertical exponent in disk density law | 1.25                                    |                                                                        |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $R_\mathrm{trunc}$      | Magnetospheric truncation radius      | $3R_*$                                  |                                                                        |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $f_\mathrm{spot}$       | Fractional area of the hot spots      | 0.01                                    |                                                                        |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| Cavity                                                                                                                                                                             |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $b_\mathrm{cav}$        | Cavity wall exponent                  | 1.25                                    |                                                                        |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+
| $a_\mathrm{cav}$        | Cavity opening angle factor           | 0.4                                     |                                                                        |   |
+-------------------------+---------------------------------------+-----------------------------------------+------------------------------------------------------------------------+---+

Table notes: The central mass ($M_\mathrm{cen} = M_* + M_\mathrm{disk}$) and centrifugal radius ($R_C$=$R_\mathrm{disk}$) are derived from fitting the C$^{18}$O PV diagram. The cavity wall component ($b_\mathrm{cav}$) and opening angle factor ($a_\mathrm{cav}$) are derived from fitting the CO PV diagram. The dust grain models are “www003” (cite: 2002Wood_dust) for the dense region of the disk, “kmh” (cite: 1994Kim_dust) for the diffuse region of the disk and the outflow, and “r400_ice095” (cite: 2003Whitney_HOCHUNK_II) for the envelope, referring to (cite: 2013_Whitney_HOCHUNK).

## Spectral Energy Distribution (SED) Fitting

For the remaining parameters, we applied spectral energy distribution (SED) fitting on the source, with the photometric datapoints collected from (cite: 2020Dutta_ALMASOP) and shown in Table [\[tab:SED\]](#tab:SED). The surveys include WISE (cite: 2010Wright_SED_WISE), AKARI (cite: 2010Ishihara_SED_AKARI_IRC), and JCMT SCUBA (cite: 2008Francesco_JCMTS_submm). The covered wavelength ranges from 3.4 $\mu$m to 850 $\mu$m.

![](figures/SED_best.pdf)

The tool used for calculating the SEDs of the YSO model grid is `HOCHUNK` (cite: 2003Whitney_HOCHUNK_I; 2003Whitney_HOCHUNK_II). Descriptions of the parameters are provided in Table [\[tab:params\]](#tab:params). The model grid was constructed by sampling five key parameters: stellar temperature ($T_\mathrm{\star}$), stellar radius ($r_\mathrm{\star}$), envelope mass infall rate ($\dot{M}_\mathrm{env}$), disk mass ($M_\mathrm{disk}$), disk mass accretion rate ($\dot{M}_\mathrm{disk}$). The stellar mass ($M_\mathrm{\star}$) was also sampled, as the central mass was fixed at $M_\mathrm{cen} = M_* + M_\mathrm{disk}$. To reduce computation time, certain parameters were manually assigned. The inner radii of both the disk and envelope were set to the dust sublimation radius ($R_\mathrm{sub}$). The disk height was limited to the disk scale height, which was defined as the hydrostatic equilibrium at the disk’s inner radius. The dust grain models used were “www003” (cite: 2002Wood_dust) for the dense regions of the disk, “kmh” (cite: 1994Kim_dust) for the outflow and the diffuse regions of the disk, and “r400_ice095” (cite: 2003Whitney_HOCHUNK_II) for the envelope, following (cite: 2013_Whitney_HOCHUNK).

`HOCHUNK` generates the density profile, computes the temperature profile, and produces the SEDs for the YSO models. For each SED, we additionally incorporated a scaling factor ($s$) ranging from 0.90 to 1.10 from (cite: 2016Furlan_HOPS).

To evaluate the goodness of fit, we adopted the method from (cite: 2007Robitaille_sedfitter), calculating the $\chi^2$ value between the observed and modeled photometric data points in logarithmic space. For each model, we first determined the best-fit values of $s$. We then ranked the combinations of YSO models and scaling factor ($s$) based on their $\chi^2$ values, identifying the best matches to the observed data.

The combination of sampled parameters having minimum $\chi^2$ value is: $T_\mathrm{\star}$$=7000$ K, $r_\mathrm{\star}$$=2$$R_\odot$, $\dot{M}_\mathrm{env}$$=10^{-4.0}$$M_\odot\,\mathrm{yr}^{-1}$, $M_\mathrm{disk}$$=0.2$ $M_\odot$, and $\dot{M}_\mathrm{disk}$$=10^{-6.0}$ $M_\odot\,\mathrm{yr}^{-1}$. Figure [6](#fig:SED_best) shows the corresponding SED overlaid with the observations. The derived stellar mass is $M_\mathrm{cen} - M_\mathrm{disk} = 1.30 M_\odot$, suggesting that this core is close to an intermediate-mass protostellar core. Substituting the stellar mass (1.30 $M_\odot$) in Eq. [\[eq:PV_CH3OH\]](#eq:PV_CH3OH), the estimated COM-rich feature size is around 71 au, within the disk size. Despite the disk mass (0.20 $M_\odot$) is not much smaller than the stellar mass (1.30 $M_\odot$), the uncertainty to the estimated size is less than 5 au.

![](figures/phys_sparx_best.pdf)

## Image Synthesis

![](figures/PV_sparx_main.pdf)

Next, we aimed to discover the CH$_3$OH extent model capable of producing the rotating feature in the observeations. We adopted the temperature maps exported by `HOCHUNK` of the best-fit YSO model and used `SPARX`[^1] (Simulation Package for Astronomical Radiative Xfer) to produce synthetic image cubes with the density, velocity, and temperature, assuming local-thermodynamic-equilibrium (LTE) and a relative abundance $X$ of $10^{-6}$ (cite: 2015Boogert_ice_review). The targeted transition, CH$_3$OH $5_{1,4}$ – $4_{2,4}$, has an upper energy level of 45 K.

Following the assumption that the gas-phase CH$_3$OH molecules are thermally desorbed, a temperature of 100 K was required to reach this abundance. However, while gas-phase CH$_3$OH is typically expected to arise from thermal desorption, the imported physical structure did not include a sufficiently warm feature at radius $\sim70$ au due to the disk shadowing effect (cite: 2022Nazari_model_diskshadow; 2023Hsu_ALMASOP). . To address this, we introduced a localized heating effect within the disk at radii between 60 and 80 au, raising the temperature for 100 K. As shown in Figure [7](#fig:phys_sparx_best) (a), two regions exceed the ice sublimation temperature of 100 K, where we assume the presence of CH$_3$OH. One region, shown in Figure [7](#fig:phys_sparx_best) (b), is an inner shell near the cavity wall, encompassing both the inner part of the envelope and the innermost part of the disk, and is primarily heated by the central protostar (“shell”). The other one, shown in Figure [7](#fig:phys_sparx_best) (c), corresponds to the localized heating we introduced around 70 au in the midplane (“ring”). We tested three spatial distribution models, where CH$_3$OH was assumed to reside either exclusively in the warm ring (“ring”), in the warm shell (“shell”), or in both regions (“ring+shell”), as marked in Figure [7](#fig:phys_sparx_best).

![](figures/schematic.pdf)

Figure [8](#fig:PV_sparx_main) (a)–(c) presents the simulated PV diagrams (orange rasters) for these three extent models overlaid with the observed PV diagrams (black contours). In the “shell” model, CH$_3$OH molecules reside in the inner warm region, producing velocity profiles with two peaks at $\Delta p\sim0\hbox{$^{\prime\prime}$}$, corresponding to the blue- and red-shifted infall motions. In contrast, as expected, the “ring” model exhibits a clear velocity gradient, closely matching our observations.

Despite these efforts, some discrepancies remain between the modeling results and observations. First, the “ring” model still tentatively exhibits two peaks in the PV diagram, whereas the observations show only a single peak. Second, if CH$_3$OH is ubiquitous within the icy mantles of dust grains, a model where CH$_3$OH exists in all warm regions–the “ring+shell” model–should better match the observations. However, the “shell” model produces stronger CH$_3$OH emission than the “ring” model, making the “ring+shell” model more similar to the “shell” model rather than aligning with the observed data. A more refined disk model and chemical simulation will be necessary to further address these discrepancies.

As an unresolved disk could also possibly exhibit a linear pattern in PV diagram, we further introduce another heating effect, which rises the temperature for 100 K within the disk inside a radius of 70 au. The resulting temperature profile and the two warm regions are shown in [7](#fig:phys_sparx_best) (d)-(f).

The resulting PV diagrams are shown in Figure [8](#fig:PV_sparx_main) (d)-(f). Overall, the “inndisk” model produces results very similar to those of the “ring” model, although the two-peak signature in the latter is slightly more discernible. hese results suggest that the observed rotating COM-rich feature could potentially be an unresolved Keplerian disk.

# Discussion

## The Origin of the Observed Rotating COM-rich Featrue

As shown in § [4.4](#sec:xclass), the observed COM-rich rotating feature may be either a warm ring (“ring”) or a compact warm disk (“inndisk”). In this section, we discuss possible scenarios for the origins of the observed COM-rich feature for the two distinct cases.

The presence of a warm ring could be explained by the “accretion shock” scenario, as shown in Fig. [9](#fig:schematic) (a). The “accretion shock" occurs at the boundary between the envelope and the outer disk, where material arrives from the former to the latter. Observational support for accretion shocks was first provided by (cite: 2002Velusamy_L1157), based on CH$_3$OH emission detected at the infall-disk interface in L1157. In L1527, (cite: 2014Sakai_L1527_envelope) identified a sharp change in chemistry at the disk edge, possibly due to the localized heating caused by accretion shocks. In IRAS 16293-2422 A, the accretion shock mechanism was proposed to explain the narrowly distributed COM emission (cite: 2016Oya_IRAS162932422) and the steep rise of the rotational temperature of H$_2$CS (cite: 2020Oya_IRAS16293-2422-A_few_au). Also, a ring-like warm structure in B335 was also suggested to be caused by the accretion shocks (cite: 2022Okoda_B335_few_au). In our case, the radius of the COM-rich feature ($\sim$70 au) is not comparable to the modeled disk size ($\sim$140 au), but rather about half of it. This suggests that the modeled disk size may be overestimated if the COM-rich feature is caused by accretion shocks. The disk size was derived by fitting the C$^{18}$O PV diagram under the assumption that C$^{18}$O perfectly traces the envelope. The observed discrepancy may indicate that C$^{18}$O emission is weaker in the inner envelope, thereby failing to reveal the high-velocity component in the inner region clearly. It is also possible that the disk edge does not lie at the centrifugal radius, but rather at half of it. This behavior is described by the “SB model,” in which the disk edge is located at the so-called centrifugal barrier, defined as half the centrifugal radius (cite: 2014Sakai_L1527_envelope; 2014Oya_IRAS15398-3359; 2022Oya_FERIA). In our case, the modeled centrifugal radius is 145 au, placing the centrifugal barrier at approximately 70 au, comparable to the size of the observed COM, rich feature. Alternatively, we note that, in contrast, if the COM-rich feature is indeed a ring inside the disk, this could possibly a localized desorption mechanism inside the disk.

In contrast, the presence of a warm inner disk could be explained by a stellar outburst, which has been proposed to account for the presence of COMs in the V883 Ori disk (cite: 2018vantHoff_V883Ori_CH3OH; 2019Lee_V883-Ori_outburst; 2025Jeong_V883Ori_COM). These outbursts result from episodic mass accretion events (cite: 2014Audard_PPVI; 2023Fischer_review), which can rapidly elevate the temperature of the inner disk and trigger the desorption of COMs. After such an event, the desorbed COM molecules can re-freeze onto icy grains when the temperature falls below the sublimation threshold. This re-freezing process can occur on timescales as short as one year (cite: 2004Lee_chem_evolution; 2019Lee_V883-Ori_outburst). Alternatively, in the case of HH 212 where such stellar outburst was not observed, radiation from the central protostar, or interactions with disk winds have been proposed for the presence of warm disks (cite: 2022Lee_HH212_stratification).

The accretion shock and the mechanism responsible for the warm disk may not be mutually exclusive, as illustrated in Figure [9](#fig:schematic)(c). For instance, in HH 212, some COMs near the disk edge may be released by heat generated from accretion shocks (cite: 2017Lee_HH212; 2017Tabone_HH212_cavity), even though the presence of a warm disk has also been suggested (cite: 2022Lee_HH212_stratification). In such cases, spatially resolved measurements of temperature and/or kinematics are necessary to further constrain the underlying physical processes.

## Comparisons with the COM-rich Disks and Implications

So far, only a handful of disks in protostellar cores have been reported to harbor COMs, incuding HH 212, V883 Ori, TW Hya, and DG Tau (cite: 2016Codella_HH212_H2O_COM; 2017Lee_HH212; 2019Lee_HH212_COM_atm; 2022Lee_HH212_stratification; 2018vantHoff_V883Ori_CH3OH; 2019Lee_V883-Ori_outburst; 2025Jeong_V883Ori_COM; 2025Fadul_V883Ori; 2016Walsh_TWHya_CH3OH; 2015Loomis_DMTau). Among them, G192.12-11.10 shares multiple similarities with HH 212. Both sources are solar-like protostellar cores located in the Orion molecular cloud and host nearly edge-on disks.

A key distinction between G192.12-11.10 and HH 212 is their evolutionary stage. HH 212 has been classified as a Class 0 protostellar core and is associated with a collimated molecular jet. In contrast, our non-detection of a SiO jet detection suggests that it G192.12-11.10 more evolved, probably Class I (cite: 2016Bally_review_jet). The wide cavity wall of the observed CO outflow also support that G192.12-11.10 is more evolved. The relatively low bolometric temperature ($T_\mathrm{bol}$$=44\pm15$ K) calculated by (cite: 2020Dutta_ALMASOP) may be explained by the nearly edge-on geometry. If the detected COMs exhibiting rotating motion in G192.12-11.10 indeed reside in the disk, as seen in HH 212, then this system represents a slightly later stage of disk chemistry at early phases (Class 0 and I). Comparing these two protostellar cores will provide critical insights into the evolution of COMs within protostellar disks over time.

## Molecular Diagnostics and Implications

![](figures/PV_stratification.pdf)

The stratified distribution of molecules was previously observed in the protostellar disk of HH 212 and the protoplanetary disk of DG Tau (cite: 2022Lee_HH212_stratification; 2020Podio_ALMADOT_interplay). Accurately measuring the spatial extent of different molecules not only constrains the chemical network but also provides insights into the physical properties of the disk. For instance, the agreement between molecular radii and their binding energies in HH 212 suggests that the detected species were thermally desorbed from ice.

We attempt to investigate the variations between the detected molecules in G192.12-11.10. As presented in §[3.3](#sec:molec) and shown in Figure [3](#fig:PV_formulae_main), the detected molecules can be broadly categorized into two groups: CH$_3$OH-like and H$_2$CO-like. In Figure [10](#fig:PV_stratification)(a) and (b), we overlay the PV diagrams of the molecules for the two groups individually. As seen in Figure [10](#fig:PV_stratification)(a), no significant slope differences are identified among the CH$_3$OH-like molecules, implying that they reside in rotating features of comparable radii. However, the limited spatial and spectral resolution prevents a more detailed examination of potential variations.

In contrast, as displayed in Figure [10](#fig:PV_stratification)(b), the differences between the H$_2$CO-like molecules (H$_2$CO, DCN, H$_2$S, and OCS) can be tentatively identified. H$_2$CO and OCS appear to be have larger $|\Delta v|$ at $|\Delta p| < 0\hbox{$.\!\!^{\prime\prime}$}{2}$, compared with DCN and H$_2$S. Considering that H$_2$CO reaches comparable velocities to CH$_3$OH at $\lvert \Delta p \rvert < 0\hbox{$.\!\!^{\prime\prime}$}{25}$, as shown in Figure [3](#fig:PV_formulae_main), it is possible that both H$_2$CO and OCS also reside within the COM-rich feature in addition to the envelope.

Among these molecules, H$_2$S serves as a precursor to OCS. Laboratory experiments suggest that ice-phase OCS can efficiently form from H$_2$S-ice mixtures through photodissociation by UV photons (cite: 2008Ferrante_model_OCS; 2010Garozzo_model_sulfur; 2015Chen_H2S_OCS). Consistently, our observations show that OCS resides in the inner regions compared to H$_2$S, where it is exposed to more intense stellar irradiation from the central protostar. A similar trend is observed in L1527, another protostellar core, where OCS is found to be more compact and concentrated near the protostar relative to other sulfur-bearing molecules such as SO, CS, and H$_2$CS (cite: 2024Zhang_L1527_sulfur). We note that OCS was also observed in various environment, such as outflow front and circumbinary disk (cite: 2007Benedettini_L1157; 2020Takakuwa_L1551).

Finally, our study identifies both the kinematic difference between NH$_2$CHO ad H$_2$CO and the kinematic similarity between NH$_2$CHO and HNCO. Similarly, based on the different morphology and kinematics of NH$_2$CHO and H$_2$CO, (cite: 2022Lee_HH212_stratification) questioned whether H$_2$CO could serve as a precursor to NH$_2$CHO. Additionally, the consistent spatial extent, kinematics, and temperature of HNCO and NH$_2$CHO led them to suggest that HNCO is a daughter species of desorbed NH$_2$CHO. Our findings support the conclusions of (cite: 2022Lee_HH212_stratification).

# Conclusions

Under the ALMASOP project, we investigated the morphology and kinematics of CO isotopologues and COMs in the protostellar core G192.12-11.10. Our key findings include:

1.  CO, C$^{18}$O, and CH$_3$OH appear to exhibit rotational motion and trace the outflow, envelope, and a rotating feature, respectively. The CH$_3$OH-rich feature is also enriched in CH$_3$CHO, HNCO, and NH$_2$CHO Our observations do not reveal any significant differences in their kinematics and radial distribution. In contrast, H$_2$CO, H$_2$S, OCS, and DCN appear to have different nature, while H$_2$CO and OCS are possibly residing in the COM-rich rotating feature as well. .

2.  We constructed a YSO model for the source by (1) fitting the CO and C$^{18}$O observations and (2) performing spectral energy distribution (SED) fitting. The resulting image synthesis suggests that an additional heating mechanism may be necessary to reproduce the observed COM emission. The modeling results suggest that the COM-rich feature has a size less than or comparable to the disk size.

3.  We explore two possible scenarios for the COM-rich feature: a warm ring and a warm inner disk, noting that these scenarios are not mutually exclusive. A more refined envelope-disk model together with observations at higher spatial resolution and with more accurate temperature measurements, will be crucial for further constraining the physical structure.

4.  The protostellar core G192.12-11.10 exhibits several similarities to HH 212. A thorough comparison of these two sources could offer valuable insights into the evolution of COMs in protostellar disks over time.

# Acknowledgments

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00302.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work made use of Astropy:[^2] a community-developed core Python package and an ecosystem of tools and resources for astronomy (cite: astropy:2013; astropy:2018; astropy:2022).

S.-Y. H. and C.-F.L. acknowledge grant from the National Science and Technology Council of Taiwan (112-2112-M-001- 039-MY3).

D.J. is supported by NRC Canada and by an NSERC Discovery Grant.

X.L. acknowledges the support of the Strategic Priority Research Program of the Chinese Academy of Sciences under Grant No. XDB0800303.

The work of MGR is supported by the international Gemini Observatory, a program of NSF NOIRLab, which is managed by the Association of Universities for Research in Astronomy (AURA) under a cooperative agreement with the U.S. National Science Foundation, on behalf of the Gemini partnership of Argentina, Brazil, Canada, Chile, the Republic of Korea, and the United States of America.

L. B. gratefully acknowledges support by the ANID BASAL project FB210003

PS was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI Number JP22H01271 and JP23H01221) of JSPS.

W.K. was supported by the National Research Foundation of Korea (NRF) grant funded by the Korea government (MSIT) (RS-2024-00342488).

MJ acknowledges the support of the Research Council of Finland Grant No. 348342.

D.S. acknowledges the support from Ramanujan Fellowship (SERB) and PRL, India.

# Software

Astropy (cite: astropy:2013; astropy:2018; astropy:2022), `CASA` (cite: casa:2022), `CARTA` (cite: 2021Comrie_CARTA), `HOCHUNk` (cite: 2003Whitney_HOCHUNK_I; 2003Whitney_HOCHUNK_II), `SPARX` https://charms.asiaa.sinica.edu.tw/sparx/), `XCLASS` (cite: 2017Moller_XCLASS),

# Molecular Diagnostics 

Table [\[tab:molec\]](#tab:molec) shows the transition information in this report. Figure [11](#fig:img_appx) displays the integrated intensity images of the molecular species.

|  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:--:|
| Formula | $f_\mathrm{rest}$ | $E_\mathrm{u}/k_\mathrm{B}$ | $g_\mathrm{u}$ | $\log_{10}(A_\mathrm{ij}/\mathrm{s}^{-1})$ | Quantum Numbers | Database |
|  | (MHz) | \(K\) |  |  |  |  |
| CO | 230538 | 17 | 5 | -6.1605 | J=2-1 | CDMS |
| C$^{18}$O | 219560 | 16 | 5 | -6.2210 | J=2-1 | CDMS |
| CH$_3$CHO | 216630 | 65 | 46 | -3.4503 | J=11-10; Ka=1; Kc=10-9; rovibSym=A | JPL |
| CH$_3$CHO | 216582 | 65 | 46 | -3.4503 | J=11-10; Ka=1; Kc=10-9; rovibSym=E | JPL |
| CH$_3$CHO | 231484 | 108 | 50 | -3.4093 | J=12-11; Ka=4; Kc=8-7; rovibSym=E | JPL |
| CH$_3$CHO | 231457 | 108 | 50 | -3.4093 | J=12-11; Ka=4; Kc=9-8; rovibSym=A | JPL |
| CH$_3$OH | 218440 | 45 | 36 | -4.3292 | J=4-3; Ka=2-1; Kc=3-2; rovibSym=E | CDMS |
| CH$_3$OH | 216946 | 56 | 44 | -4.9160 | J=5-4; Ka=1-2; Kc=4-3; rovibSym=E | CDMS |
| CH$_3$OH | 231281 | 165 | 84 | -4.7372 | J=10-9; Ka=2-3; Kc=9-6; rovibSym=A2 | CDMS |
| CH$_3$OH | 232419 | 165 | 84 | -4.7287 | J=10-9; Ka=2-3; Kc=8-7; rovibSym=A1 | CDMS |
| CH$_3$OH | 232945 | 190 | 84 | -4.6723 | J=10-11; Ka=3-2; Kc=7-9; rovibSym=E | CDMS |
| DCN | 217239 | 21 | 21 | -3.3396 | J=3-2; l2=0; kronigParity=e | CDMS |
| H$_2$CO | 218222 | 21 | 7 | -3.5501 | J=3-2; Ka=0; Kc=3-2 | CDMS |
| H$_2$CO | 218476 | 68 | 7 | -3.8037 | J=3-2; Ka=2; Kc=2-1 | CDMS |
| H$_2$CO | 218760 | 68 | 7 | -3.8020 | J=3-2; Ka=2; Kc=1-0 | CDMS |
| H$_2$CO | 216569 | 174 | 57 | -5.1413 | J=9; Ka=1; Kc=8-9 | CDMS |
| H$_2$S | 216710 | 84 | 5 | -4.3123 | J=2; Ka=2-1; Kc=0-1 | CDMS |
| HNCO | 219798 | 58 | 21 | -3.8329 | J=10-9; Ka=0; Kc=10-9 | CDMS |
| HNCO | 218981 | 101 | 21 | -3.8470 | J=10-9; Ka=1; Kc=10-9 | CDMS |
| NH$_2$CHO | 233897 | 94 | 23 | -3.0645 | J=11-10; Ka=3; Kc=9-8 | CDMS |
| NH$_2$CHO | 233735 | 115 | 23 | -3.0933 | J=11-10; Ka=4; Kc=8-7 | CDMS |
| NH$_2$CHO | 233746 | 115 | 23 | -3.0933 | J=11-10; Ka=4; Kc=7-6 | CDMS |
| NH$_2$CHO | 233594 | 142 | 23 | -3.1330 | J=11-10; Ka=5; Kc=6-5 | CDMS |
| NH$_2$CHO | 233594 | 142 | 23 | -3.1330 | J=11-10; Ka=5; Kc=7-6 | CDMS |
| NH$_2$CHO | 233528 | 174 | 23 | -3.1863 | J=11-10; Ka=6; Kc=5-4 | CDMS |
| NH$_2$CHO | 233528 | 174 | 23 | -3.1863 | J=11-10; Ka=6; Kc=6-5 | CDMS |
| OCS | 218903 | 100 | 37 | -4.5174 | J=18-17; | CDMS |
| OCS | 231061 | 111 | 39 | -4.4463 | J=19-18; | CDMS |

![](figures/img_appx.pdf)

# YSO Modeling 

The photometric data as well as the corresponding references are shown in Table [\[tab:SED\]](#tab:SED).

|       |           |          |                 |     |
|:------|----------:|---------:|:----------------|:----|
|       | $\lambda$ |  $F_\nu$ | $\sigma(F_\nu)$ |     |
|       |  ($\mu$m) |     (Jy) | (Jy)            |     |
| WISE  |       3.4 | 2.02e-04 | 1.23e-05        |     |
|       |       4.6 | 3.95e-03 | 9.43e-05        |     |
|       |        22 | 1.85e-01 | 4.41e-03        |     |
| AKARI |        65 | 1.23e+01 | 5.93e-01        |     |
|       |       140 | 4.32e+01 | 2.25e+00        |     |
|       |       160 | 4.00e+01 | 8.33e+00        |     |
| SCUBA |       850 | 1.91e+00 | 1.42e+00        |     |

Table notes: The SED flux data points were collected from (cite: 2020Dutta_ALMASOP).

WISE: (cite: 2010Wright_SED_WISE) AKARI PSC: (cite: 2010Ishihara_SED_AKARI_IRC); JCMT/SCUBA: (cite: 2008Francesco_JCMTS_submm);

natexlab

(ref: 2008Arce_L1157-B1_COMs) Arce, H. G., Santiago-Garcia, J., Jorgensen, J. K., Tafalla, M., & Bachiller, R. 2008, Astrophysical Journal Letters, 681, L21, doi: [`10.1086/590110`](http://doi.org/10.1086/590110)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy:2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: 2014Audard_PPVI) Audard, M., Ábrahám, P., Dunham, M. M., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 387–410, doi: [`10.2458/azu_uapress_9780816531240-ch017`](http://doi.org/10.2458/azu_uapress_9780816531240-ch017)

(ref: 2016Bally_review_jet) Bally, J. 2016, Annual Review of Astronomy and Astrophysics, 54, 491, doi: [`10.1146/annurev-astro-081915-023341`](http://doi.org/10.1146/annurev-astro-081915-023341)

(ref: 2020Belloche_CALYPSO) Belloche, A., Maury, A. J., Maret, S., et al. 2020, Astronomy and Astrophysics, 635, A198, doi: [`10.1051/0004-6361/201937352`](http://doi.org/10.1051/0004-6361/201937352)

(ref: 2007Benedettini_L1157) Benedettini, M., Viti, S., Codella, C., et al. 2007, Monthly Notices of the Royal Astronomical Society, 381, 1127, doi: [`10.1111/j.1365-2966.2007.12300.x`](http://doi.org/10.1111/j.1365-2966.2007.12300.x)

(ref: 2015Boogert_ice_review) Boogert, A. C. A., Gerakines, P. A., & Whittet, D. C. B. 2015, ARA&A, 53, 541, doi: [`10.1146/annurev-astro-082214-122348`](http://doi.org/10.1146/annurev-astro-082214-122348)

(ref: 2021Booth_HD100546_COM) Booth, A. S., Walsh, C., Terwisscha van Scheltinga, J., et al. 2021, Nature Astronomy, 5, 684, doi: [`10.1038/s41550-021-01352-w`](http://doi.org/10.1038/s41550-021-01352-w)

(ref: 2022Bouvier_ORANGES) Bouvier, M., Ceccarelli, C., López-Sepulcre, A., et al. 2022, The Astrophysical Journal, 929, 10, doi: [`10.3847/1538-4357/ac5904`](http://doi.org/10.3847/1538-4357/ac5904)

(ref: 2022Brunken_OphIRS48_COM) Brunken, N. G. C., Booth, A. S., Leemker, M., et al. 2022, Astronomy and Astrophysics, 659, A29, doi: [`10.1051/0004-6361/202142981`](http://doi.org/10.1051/0004-6361/202142981)

(ref: 2019Carney_HD163296_COM) Carney, M. T., Hogerheijde, M. R., Guzmán, V. V., et al. 2019, Astronomy and Astrophysics, 623, A124, doi: [`10.1051/0004-6361/201834353`](http://doi.org/10.1051/0004-6361/201834353)

(ref: casa:2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacific, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: 1981Cassen_CMU) Cassen, P., & Moosman, A. 1981, Icarus, 48, 353, doi: [`10.1016/0019-1035(81)90051-8`](http://doi.org/10.1016/0019-1035(81)90051-8)

(ref: 2004Ceccarelli_HotCorino) Ceccarelli, C. 2004, in Star Formation in the Interstellar Medium: In Honor of David Hollenbach, Chris McKee and Frank Shu, ASP Conference Proceeding, ed. D. Johnstone, F. Adams, D. Lin, D. Neufeld, & E. Ostriker, Vol. 323, San Francisco, Astronomical Society of the Pacific (ASP Conference Proceedings)

(ref: 2015Chen_H2S_OCS) Chen, Y. J., Juang, K. J., Nuevo, M., et al. 2015, The Astrophysical Journal, 798, 80, doi: [`10.1088/0004-637X/798/2/80`](http://doi.org/10.1088/0004-637X/798/2/80)

(ref: 2016Codella_HH212_H2O_COM) Codella, C., Ceccarelli, C., Cabrit, S., et al. 2016, A&A, 586, L3, doi: [`10.1051/0004-6361/201527424`](http://doi.org/10.1051/0004-6361/201527424)

(ref: 2021Comrie_CARTA) Comrie, A., Wang, K.-S., Hsu, S.-C., et al. 2021, Astrophysics Source Code Library, ascl:2103.031. <https://ui.adsabs.harvard.edu/abs/2021ascl.soft03031C>

(ref: 2024DeSimone_IRAS4A2_COMdiskwind) De Simone, M., Podio, L., Chahine, L., et al. 2024, arXiv e-prints, arXiv:2404.19690, doi: [`10.48550/arXiv.2404.19690`](http://doi.org/10.48550/arXiv.2404.19690)

(ref: 2008Francesco_JCMTS_submm) Di Francesco, J., Johnstone, D., Kirk, H., MacKenzie, T., & Ledwosinska, E. 2008, The Astrophysical Journal Supplement Series, 175, 277, doi: [`10.1086/523645`](http://doi.org/10.1086/523645)

(ref: 2024Dunham_outflow) Dunham, M. M., Stephens, I. W., Myers, P. C., et al. 2024, Monthly Notices of the Royal Astronomical Society, 533, 3828, doi: [`10.1093/mnras/stae2018`](http://doi.org/10.1093/mnras/stae2018)

(ref: 2020Dutta_ALMASOP) Dutta, S., Lee, C.-F., Liu, T., et al. 2020, ApJS, 251, 20, doi: [`10.3847/1538-4365/abba26`](http://doi.org/10.3847/1538-4365/abba26)

(ref: 2025Fadul_V883Ori) Fadul, A. M. A., Schwarz, K. R., van ’t Hoff, M. L. R., et al. 2025, arXiv e-prints, arXiv:2504.06005, doi: [`10.48550/arXiv.2504.06005`](http://doi.org/10.48550/arXiv.2504.06005)

(ref: 2008Ferrante_model_OCS) Ferrante, R. F., Moore, M. H., Spiliotis, M. M., & Hudson, R. L. 2008, The Astrophysical Journal, 684, 1210, doi: [`10.1086/590362`](http://doi.org/10.1086/590362)

(ref: 2023Fischer_review) Fischer, W. J., Hillenbrand, L. A., Herczeg, G. J., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 355, doi: [`10.48550/arXiv.2203.11257`](http://doi.org/10.48550/arXiv.2203.11257)

(ref: 2016Furlan_HOPS) Furlan, E., Fischer, W. J., Ali, B., et al. 2016, The Astrophysical Journal Supplement Series, 224, 5, doi: [`10.3847/0067-0049/224/1/5`](http://doi.org/10.3847/0067-0049/224/1/5)

(ref: 2010Garozzo_model_sulfur) Garozzo, M., Fulvio, D., Kanuchova, Z., Palumbo, M. E., & Strazzulla, G. 2010, Astronomy and Astrophysics, 509, A67, doi: [`10.1051/0004-6361/200913040`](http://doi.org/10.1051/0004-6361/200913040)

(ref: 2009Herbst_COM_review) Herbst, E., & van Dishoeck, E. F. 2009, ARA&A, 47, 427, doi: [`10.1146/annurev-astro-082708-101654`](http://doi.org/10.1146/annurev-astro-082708-101654)

(ref: 2023Hsieh_outflow) Hsieh, C.-H., Arce, H. G., Li, Z.-Y., et al. 2023, The Astrophysical Journal, 947, 25, doi: [`10.3847/1538-4357/acba13`](http://doi.org/10.3847/1538-4357/acba13)

(ref: 2020Hsu_ALMASOP) Hsu, S.-Y., Liu, S.-Y., Liu, T., et al. 2020, ApJ, 898, 107, doi: [`10.3847/1538-4357/ab9f3a`](http://doi.org/10.3847/1538-4357/ab9f3a)

(ref: 2022Hsu_ALMASOP) —. 2022, ApJ, 927, 218, doi: [`10.3847/1538-4357/ac49e0`](http://doi.org/10.3847/1538-4357/ac49e0)

(ref: 2023Hsu_ALMASOP) Hsu, S.-Y., Liu, S.-Y., Johnstone, D., et al. 2023, The Astrophysical Journal, 956, 120, doi: [`10.3847/1538-4357/acefcf`](http://doi.org/10.3847/1538-4357/acefcf)

(ref: 2024Hsu_ALMASOP) Hsu, S.-Y., Lee, C.-F., Liu, S.-Y., et al. 2024, The Astrophysical Journal, 976, 29, doi: [`10.3847/1538-4357/ad7e25`](http://doi.org/10.3847/1538-4357/ad7e25)

(ref: 2010Ishihara_SED_AKARI_IRC) Ishihara, D., Onaka, T., Kataza, H., et al. 2010, Astronomy and Astrophysics, 514, A1, doi: [`10.1051/0004-6361/200913811`](http://doi.org/10.1051/0004-6361/200913811)

(ref: 2019Jacobsen_L483_COM) Jacobsen, S. K., Jørgensen, J. K., Di Francesco, J., et al. 2019, A&A, 629, A29, doi: [`10.1051/0004-6361/201833214`](http://doi.org/10.1051/0004-6361/201833214)

(ref: 2025Jeong_V883Ori_COM) Jeong, J.-H., Lee, J.-E., Lee, S., et al. 2025, The Astrophysical Journal Supplement Series, 276, 49, doi: [`10.3847/1538-4365/ad9450`](http://doi.org/10.3847/1538-4365/ad9450)

(ref: 2016Jimenez-Serra_L1544) Jiménez-Serra, I., Vasyunin, A. I., Caselli, P., et al. 2016, The Astrophysical Journal, 830, L6, doi: [`10.3847/2041-8205/830/1/L6`](http://doi.org/10.3847/2041-8205/830/1/L6)

(ref: 2020Jorgensen_review) Jørgensen, J. K., Belloche, A., & Garrod, R. T. 2020, Annual Review of Astronomy and Astrophysics, 58, 727, doi: [`10.1146/annurev-astro-032620-021927`](http://doi.org/10.1146/annurev-astro-032620-021927)

(ref: 1994Kim_dust) Kim, S. H., Martin, P. G., & Hendry, P. D. 1994, Astrophysical Journal, 422, 164, doi: [`10.1086/173714`](http://doi.org/10.1086/173714)

(ref: 2022Lee_HH212_stratification) Lee, C. F., Codella, C., Ceccarelli, C., & Lopez-Sepulcre, A. 2022, Astrophysical Journal, 937, 10, doi: [`10.3847/1538-4357/ac8c28`](http://doi.org/10.3847/1538-4357/ac8c28)

(ref: 2019Lee_HH212_COM_atm) Lee, C.-F., Codella, C., Li, Z.-Y., & Liu, S.-Y. 2019a, ApJ, 876, 63, doi: [`10.3847/1538-4357/ab15db`](http://doi.org/10.3847/1538-4357/ab15db)

(ref: 2017Lee_HH212) Lee, C.-F., Li, Z.-Y., Ho, P. T. P., et al. 2017, ApJ, 843, 27, doi: [`10.3847/1538-4357/aa7757`](http://doi.org/10.3847/1538-4357/aa7757)

(ref: 2000Lee_jet_wind_model) Lee, C. F., Mundy, L. G., Reipurth, B., Ostriker, E. C., & Stone, J. M. 2000, Astrophysical Journal, 542, 925, doi: [`10.1086/317056`](http://doi.org/10.1086/317056)

(ref: 2004Lee_chem_evolution) Lee, J.-E., Bergin, E. A., & Evans, Neal J., I. 2004, The Astrophysical Journal, 617, 360, doi: [`10.1086/425153`](http://doi.org/10.1086/425153)

(ref: 2019Lee_V883-Ori_outburst) Lee, J.-E., Lee, S., Baek, G., et al. 2019b, Nature Astronomy, 3, 314, doi: [`10.1038/s41550-018-0680-0`](http://doi.org/10.1038/s41550-018-0680-0)

(ref: 2011Lombardi_2MASS_extinction_IV) Lombardi, M., Alves, J., & Lada, C. J. 2011, A&A, 535, A16, doi: [`10.1051/0004-6361/201116915`](http://doi.org/10.1051/0004-6361/201116915)

(ref: 2015Loomis_DMTau) Loomis, R. A., Cleeves, L. I., Öberg, K. I., Guzman, V. V., & Andrews, S. M. 2015, The Astrophysical Journal, 809, L25, doi: [`10.1088/2041-8205/809/2/L25`](http://doi.org/10.1088/2041-8205/809/2/L25)

(ref: 2004Mendoza_UCM) Mendoza, S., Canto, J., & Raga, A. C. 2004, Revista Mexicana De Astronomia Y Astrofisica, 40, 147

(ref: 2017Moller_XCLASS) Möller, T., Endres, C., & Schilke, P. 2017, A&A, 598, A7, doi: [`10.1051/0004-6361/201527203`](http://doi.org/10.1051/0004-6361/201527203)

(ref: 2024Mori_model_UCM) Mori, S., Aikawa, Y., Oya, Y., Yamamoto, S., & Sakai, N. 2024, The Astrophysical Journal, 961, 31, doi: [`10.3847/1538-4357/ad0634`](http://doi.org/10.3847/1538-4357/ad0634)

(ref: 2022Nazari_model_diskshadow) Nazari, P., Tabone, B., Rosotti, G. P., et al. 2022, Astronomy and Astrophysics, 663, A58, doi: [`10.1051/0004-6361/202142777`](http://doi.org/10.1051/0004-6361/202142777)

(ref: 1997Ohashi_IRAS043682557) Ohashi, N., Hayashi, M., Ho, P. T. P., & Momose, M. 1997, The Astrophysical Journal, 475, 211, doi: [`10.1086/303533`](http://doi.org/10.1086/303533)

(ref: 2022Okoda_B335_few_au) Okoda, Y., Oya, Y., Imai, M., et al. 2022, ApJ, 935, 136, doi: [`10.3847/1538-4357/ac7ff4`](http://doi.org/10.3847/1538-4357/ac7ff4)

(ref: 2022Oya_FERIA) Oya, Y., Kibukawa, H., Miyake, S., & Yamamoto, S. 2022, Publications of the Astronomical Society of the Pacific, 134, 094301, doi: [`10.1088/1538-3873/ac8839`](http://doi.org/10.1088/1538-3873/ac8839)

(ref: 2016Oya_IRAS162932422) Oya, Y., Sakai, N., Lopez-Sepulcre, A., et al. 2016, Astrophysical Journal, 824, 88, doi: [`10.3847/0004-637x/824/2/88`](http://doi.org/10.3847/0004-637x/824/2/88)

(ref: 2020Oya_IRAS16293-2422-A_few_au) Oya, Y., & Yamamoto, S. 2020, ApJ, 904, 185, doi: [`10.3847/1538-4357/abbe14`](http://doi.org/10.3847/1538-4357/abbe14)

(ref: 2014Oya_IRAS15398-3359) Oya, Y., Sakai, N., Sakai, T., et al. 2014, The Astrophysical Journal, 795, 152, doi: [`10.1088/0004-637X/795/2/152`](http://doi.org/10.1088/0004-637X/795/2/152)

(ref: 2020Podio_ALMADOT_interplay) Podio, L., Garufi, A., Codella, C., et al. 2020, Astronomy and Astrophysics, 644, A119, doi: [`10.1051/0004-6361/202038600`](http://doi.org/10.1051/0004-6361/202038600)

(ref: astropy:2018) Price-Whelan, A. M., Sipőcz, B. M., Günther, H. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2007Robitaille_sedfitter) Robitaille, T. P., Whitney, B. A., Indebetouw, R., & Wood, K. 2007, ApJS, 169, 328, doi: [`10.1086/512039`](http://doi.org/10.1086/512039)

(ref: 2014Sakai_L1527_envelope) Sakai, N., Sakai, T., Hirota, T., et al. 2014, Nature, 507, 78, doi: [`10.1038/nature13000`](http://doi.org/10.1038/nature13000)

(ref: 2017Tabone_HH212_cavity) Tabone, B., Cabrit, S., Bianchi, E., et al. 2017, A&A, 607, L6, doi: [`10.1051/0004-6361/201731691`](http://doi.org/10.1051/0004-6361/201731691)

(ref: 2020Takakuwa_L1551) Takakuwa, S., Saigo, K., Matsumoto, T., et al. 2020, The Astrophysical Journal, 898, 10, doi: [`10.3847/1538-4357/ab9b7c`](http://doi.org/10.3847/1538-4357/ab9b7c)

(ref: 1976Ulrich_CMU) Ulrich, R. K. 1976, ApJ, 210, 377, doi: [`10.1086/154840`](http://doi.org/10.1086/154840)

(ref: 2021vanderMarel_OphIRS48_H2CO_CH3OH) van der Marel, N., Booth, A. S., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021, Astronomy and Astrophysics, 651, L5, doi: [`10.1051/0004-6361/202141051`](http://doi.org/10.1051/0004-6361/202141051)

(ref: 2018vantHoff_V883Ori_CH3OH) van ’t Hoff, M. L. R., Tobin, J. J., Trapman, L., et al. 2018, The Astrophysical Journal, 864, L23, doi: [`10.3847/2041-8213/aadb8a`](http://doi.org/10.3847/2041-8213/aadb8a)

(ref: 2013Vasyunin_reactive_desorption) Vasyunin, A. I., & Herbst, E. 2013, The Astrophysical Journal, 769, 34, doi: [`10.1088/0004-637X/769/1/34`](http://doi.org/10.1088/0004-637X/769/1/34)

(ref: 2002Velusamy_L1157) Velusamy, T., Langer, W. D., & Goldsmith, P. F. 2002, The Astrophysical Journal, 565, L43, doi: [`10.1086/339246`](http://doi.org/10.1086/339246)

(ref: 2021Wakelam_non-thermal_desorption) Wakelam, V., Dartois, E., Chabot, M., et al. 2021, Astronomy and Astrophysics, 652, A63, doi: [`10.1051/0004-6361/202039855`](http://doi.org/10.1051/0004-6361/202039855)

(ref: 2016Walsh_TWHya_CH3OH) Walsh, C., Loomis, R. A., Öberg, K. I., et al. 2016, The Astrophysical Journal, 823, L10, doi: [`10.3847/2041-8205/823/1/L10`](http://doi.org/10.3847/2041-8205/823/1/L10)

(ref: 2013_Whitney_HOCHUNK) Whitney, B. A., Robitaille, T. P., Bjorkman, J. E., et al. 2013, The Astrophysical Journal Supplement Series, 207, 30, doi: [`10.1088/0067-0049/207/2/30`](http://doi.org/10.1088/0067-0049/207/2/30)

(ref: 2003Whitney_HOCHUNK_II) Whitney, B. A., Wood, K., Bjorkman, J. E., & Cohen, M. 2003a, Astrophysical Journal, 598, 1079, doi: [`10.1086/379068`](http://doi.org/10.1086/379068)

(ref: 2003Whitney_HOCHUNK_I) Whitney, B. A., Wood, K., Bjorkman, J. E., & Wolff, M. J. 2003b, ApJ, 591, 1049, doi: [`10.1086/375415`](http://doi.org/10.1086/375415)

(ref: 2002Wood_dust) Wood, K., Wolff, M. J., Bjorkman, J. E., & Whitney, B. 2002, The Astrophysical Journal, 564, 887, doi: [`10.1086/324285`](http://doi.org/10.1086/324285)

(ref: 2010Wright_SED_WISE) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, The Astronomical Journal, 140, 1868, doi: [`10.1088/0004-6256/140/6/1868`](http://doi.org/10.1088/0004-6256/140/6/1868)

(ref: 2021Yang_PEACHES) Yang, Y.-L., Sakai, N., Zhang, Y., et al. 2021, The Astrophysical Journal, 910, 20, doi: [`10.3847/1538-4357/abdfd6`](http://doi.org/10.3847/1538-4357/abdfd6)

(ref: 2024Zhang_L1527_sulfur) Zhang, Z. E., Sakai, N., Ohashi, S., et al. 2024, The Astrophysical Journal, 966, 207, doi: [`10.3847/1538-4357/ad3921`](http://doi.org/10.3847/1538-4357/ad3921)

(ref: 2010Oberg_B1b) Öberg, K. I., Bottinelli, S., Jørgensen, J. K., & van Dishoeck, E. F. 2010, The Astrophysical Journal, 716, 825, doi: [`10.1088/0004-637X/716/1/825`](http://doi.org/10.1088/0004-637X/716/1/825)

[^1]: https://charms.asiaa.sinica.edu.tw/sparx/

[^2]: http://www.astropy.org

</paper>

Write the methods card for this paper.