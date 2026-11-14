# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025MNRAS.538.1481M\sonnetcc\reply.txt

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
 "bibcode": "2025MNRAS.538.1481M",
 "title": "FAUST-XXII. Deuteration in the VLA1623-2417 protostellar hot-corinos, cavities, and streamers",
 "year": 2025,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Mercimek, S.",
 "n_authors": 16,
 "arxiv_id": "2502.18675",
 "doi": "10.1093/mnras/staf367",
 "alma_projects_linked_by_archive": [
  "2018.1.01205.L"
 ]
}
```

Paper text:
<paper>
# FAUST – XXII. Deuteration in the VLA1623-2417 protostellar hot-corinos, cavities, and streamers.

[^1]: E-mail: seyma.mercimek@manchester.ac.uk

# Abstract

The study of deuterium fractionation is a valuable tool for reconstructing our chemical history from the early prestellar stages to the formation of planets. In the context of the ALMA Large Programme FAUST, we observed formaldehyde, H$_2$CO, and its singly and doubly deuterated forms, HDCO and D$_2$CO, towards the protostellar cluster VLA1623–2417, on scales of $\sim2000-50$ au.

Formaldehyde probes the inner envelopes of the protostars VLA1623A, B, and W, the rotating cavities opened by the VLA1623A outflow, and several streamers. The HDCO and D$_2$CO emissions are observed towards VLA1623A, in its outflow cavities, and in one of the streamers. We estimate the gas temperature from the HDCO lines: T$\sim125$ K towards VLA1623A, indicating hot-corino emission, lower temperatures in the outflow cavities ($20-40$ K), and in the streamers ($\le15$ K). The D$_2$CO lines also trace the flattened envelope of VLA1623A, where H$_2$CO and HDCO are fainter. This may be due to D$_2$CO formation on dust grains in the cold prestellar phase, and subsequent photodesorption caused by the enhanced UV flux from two nearby B stars. We inferred the molecular deuteration: \[HDCO\]/\[H$_2$CO\] $\sim0.16$, $\sim0.07-0.13$, and $\sim0.3$; \[D$_2$CO\]/\[H$_2$CO\] $\sim0.003$, $\sim0.05-0.13$, and $\sim0.03$ in the hot corino, in the outflow cavities, and in the streamer, respectively. The spatial distribution of D$_2$CO, which points to formation on dust grains, and the similar values of \[HDCO\]/\[H$_2$CO\] and \[D$_2$CO\]/\[H$_2$CO\] in the components of the system, suggest that deuterium fractionation occurs at the prestellar stage and is then inherited, mostly unaltered, in the protostellar phase.

Stars: formation – Protoplanetary disks – ISM: individual objects: VLA1623–2417

# Introduction

Observing how molecular complexity evolves in Sun-like star-forming regions is mandatory to comprehend whether the chemical composition of the protostellar stages is inherited by protoplanetary disks and, possibly, newly formed planets (cite: Caselli2012). In this context, the deuterium-bearing species are a powerful tool to investigate the chemical evolution along the star formation process (cite: Ceccarelli2014; Ceccarelli2023). The deuterium fraction, as observed in the early (prestellar, protostellar) stages of the star-forming process, can be much larger than the deuterium elemental abundance (D/H $\sim$ 2.5$\times$10$^{-5}$, (cite: Cooke2018).

Significant deuteration fraction is seen in the cold ($\leq$ 10 K), dense ($\geq$ 10$^{5}$ cm$^{-3}$) prestellar cores where most of the species freeze out onto the cold surfaces of the dust grains (cite: Caselli2002; Bacmann2003; Crapsi2005; Sabatini2020). When CO is heavily depleted, as in prestellar cores (cite: Caselli1999; Bacmann2002; Sabatini2022), H$^{+}_{3}$ can efficiently react with HD via the following exothermic reaction to form its single-deuterated form (cite: Gerlich2002; Ceccarelli2014):

$$\begin{equation}
        H^{+}_{3} + HD \rightarrow H_{2}D^{+} + H_{2} + 232 K.
\end{equation}$$

H$_{2}$D$^{+}$ can further reacts with HD to form first D$_{2}$H$^{+}$, and then D$_{3}^{+}$ (cite: vastel2004). Once the protostar forms, the accretion of envelope material, the temperature of the protostellar envelope increases, and molecules such as CO and N$_2$ are released back in the gas phase and react with the deuterated ions, producing an increase in the D/H ratio of several species (cite: Emprechtinger2009). This applies to both the so-called Class 0 (age $\geq$ 10$^4$ yr), and Class I ($\geq$ 10$^5$ yr) stages (cite: Andre1990).

Typical examples of species where D/H shows a dramatic enhancement, up to several orders of magnitude, are water, methanol, and formaldehyde (cite: Loinard2001; vastel2004; Ceccarelli2007; Caselli2012; Persson2018; Taquet2019; Podio2024; Chahine2024). More specifically, the fractional deuteration of formaldehyde (H$_{2}$CO) is an excellent probe to investigate the chemical evolution along the star formation process, being detected from cold prestellar cores (cite: Chacon2019) to protoplanetary disks with ages larger than 10$^5$ yr (cite: Podio2024). Formaldehyde can be considered an intermediate species in the process of forming complex organic molecules. It can be formed either in the gas phase or on grains. Gas-phase reactions start with C$^{+}$ to form CH$_{3}^{+}$ followed by oxidation (cite: roberts2000; Turner2001; Roueff2007). On the other hand, grain surface formation occurs via multiple hydrogenation of frozen CO (cite: Tielens1983; Fuchs2009; Garrod2022). The deuterated forms of H$_{2}$CO are either formed in gas-phase or stored in the grain mantles, where they remain until the protostar is formed and the grain mantles are heated and gradually evaporated (cite: Ceccarelli2007).

Gas-phase formaldehyde deuterium fraction has been studied towards low-mass star-forming objects using single-dish antennas (cite: Bacmann2003; Parise2006; Bianchi2017; Mercimek2022) and more recently interferometric observations taken in the context of the ALMA programs PILS and FAUST (cite: Persson2018; Manigand2019; Evans2023; Podio2024). These observations lead to D/H values $>$ 10$^{-2}$ and $>$ 10$^{-3}$ for HDCO, and D$_2$CO, respectively. In addition, what has been found so far shows no statistically significant difference in the deuteration fractions in prestellar cores, Class 0 protostars, and Class I/II disks. This suggests that the deuterated molecules in protostars and disks are inherited from the prestellar phase, with little or no reprocessing (cite: Drozdovskaya2021). However, the available estimates are obtained mainly by using single-dish observations. Therefore, the inferred deuteration is an average over the various structures (hot-corinos, outflows, streamers, envelopes) covered by the beam. Interferometric observations are therefore mandatory to minimise beam dilution and disentangle the inner region (less than 100 au) around protostars from the other physical components such as envelopes, outflows, and infalling streamers.

In this paper, we present observations of formaldehyde and its single- and doubly-deuterated isotopologues toward the prototypical VLA1623–2417 protostellar cluster (Sect. [2](#VLA1623)). The observations are taken as part of the ALMA Large Program (LP) Fifty AU STudy of the chemistry in the disk/envelope system of Solar-like protostars (FAUST, http://faust-alma.riken.jp, PI: S. Yamamoto; (cite: Codella2021)) (Sect. [3](#observations)). We analyse the spatial distribution of H$_2$CO, HDCO, and D$_2$CO from scales of $\sim 2000$ au down to scales of 50 au (Sect. [4](#results)). We then estimate the gas temperature and the molecular column densities and deuteration towards the detected emission components, i.e. the VLA1623 A hot-corino, the outflow cavities, and the accretion streamers (Sect. [\[D2\]](#D2)). Finally we discuss the formation mechanism of deuterated molecules and compare our estimates of deuteration in the different components of VLA1623 with values from the literature (Sects. [\[comparison\]](#comparison) and [\[D1\]](#D1)). We summarize our conclusions in Sect. [\[conclusions\]](#conclusions).

# The VLA1623-2417 protostellar cluster

VLA1623-2417 (hereafter VLA1623) is a protostellar cluster located in Ophiuchus A at a distance of 131$\pm$1 pc (cite: Gagne2018). The multiple system has been studied at different wavelengths (cite: Andre1990; Looney2000; Ward2011; Murillo2013disk; Murillo2018L; Murillo2018; Harris2018; Hsieh2020; Ohashi2022; Codella2022; Mercimek2023), revealing four protostars: VLA1623 A, which in turn is a Class 0 binary protostar (A1 and A2) with a separation of $\sim$30 au, and surrounded by a circumbinary disk (CBD); VLA1623 B, a Class 0 protostar at $\sim$130 au from VLA1623 A; VLA1623 W, a Class I protostar located at $\sim$1300 au west of the VLA1623 A1+A2+B system.

Complex gas kinematics characterize VLA1623. The VLA1623 A binary system drives blue- and red-shifted outflows revealed in CO and H$_{2}$ emission (cite: Andre1990; Hsieh2020; Hara2021) along the NW-SE direction. A rotating cavity opened by the mass loss process has been imaged in CS, CCH, and H$^{13}$CO$^+$ by (cite: Ohashi2022). (cite: Santangelo2015) detected a fast jet driven by VLA1623 B. (cite: Murillo2018) and (cite: Ohashi2022) mapped a cold rotating cloud enveloping VLA1623 A and B in several simple species (e.g. DCO$^{+}$ and H$^{13}$CO$^{+}$). Recent ALMA studies imaged also molecular streamers infalling towards the A+B system in SO and C$^{18}$O lines (cite: Hsieh2020; Mercimek2023). In the context of FAUST, (cite: Codella2022) mapped complex organic molecules, such as methanol (CH$_{3}$OH) and methyl formate (HCOOCH$_{3}$), which probe the circumstellar rotating gas around VLA1623 A1 and B. The detected rotation signatures suggest that the VLA1623 system is unstable: VLA1623 B counter-rotates with respect to the disk/envelope of VLA1623 A (cite: Ohashi2022; Codella2022). Moreover, (cite: Murillo2013disk) and (cite: Mercimek2023) discuss the possibility that the protostellar source VLA1623 W, which is located $\sim 1300$ au West to the A1+A2+B system and shows a systemic velocity which differs by 2.2 km s$^{-1}$, has been ejected from the close triple system.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Species | Transition $^{a}$ | $\nu$ $^{a}$ | $E_{\rm up}$ $^{a}$ | $S\mu^2$ $^{a}$ | rms | ${\delta} V$ | Beam size | Beam PA | FoV$^{b}$ |
|  |  | (MHz) | \(K\) | (D$^{2}$) | (mJy beam$\rm ^{-1}$) | (km s$^{-1}$) | ($\ensuremath{''} \times \ensuremath{''}$) | ($\rm ^{\circ})$ | $(\ensuremath{''}$) |
| p-H$_{2}$CO | 3$_{0,3}$ – 2$_{0,2}$ | 218222.2 | 21 | 16 | 4.4 | 0.2 | 0.55 $\times$ 0.45 | –74 | 24 |
| HDCO | 4$_{1,4}$ – 3$_{1,3}$ | 246924.6 | 38 | 20 | 0.7 | 1.2 | 0.50 $\times$ 0.47 | –77 | 21 |
| HDCO | 4$_{2,2}$ – 3$_{2,1}$ | 259034.9 | 63 | 16 | 2.0 | 0.2 | 0.50 $\times$ 0.47 | –95 | 20 |
| o-D$_{2}$CO | 4$_{0,4}$ – 3$_{0,3}$ | 231410.2 | 28 | 43 | 2.3 | 0.2 | 0.50 $\times$ 0.43 | –72 | 23 |
| o-D$_{2}$CO | 4$_{2,3}$ – 3$_{2,2}$ | 233650.4 | 50 | 33 | 1.0 | 0.6 | 0.51 $\times$ 0.42 | –75 | 23 |

# Observations

The VLA1623 protostellar system was observed between December 2018 and March 2020 by ALMA using Band 6 observations (216–234 GHz) in the context of the FAUST Large program (2018.1.01205.L; PI: Satoshi Yamamoto). Observations were conducted using two setups in Band 6 and one in Band 3. We used the 7-m array of the Atacama Compact Array (ACA) and the 12-m C43-4 and C43-1 configurations centering the observations at $\alpha_{\rm 2000}$ = 16${^h}$26${^m}$26${^s}$.392, $\delta_{\rm 2000}$ = –24$^\circ$24$'$30$''$.69. In this paper, we analyse only the observations in Band 6, i.e. in Setup 1 (214.0–219.0 GHz and 229.0–234.0 GHz) and Setup 2 (242.5–247.5 GHz and 257.2–262.5 GHz). Table [\[tab:lines\]](#tab:lines) reports the spectral parameters (transition, frequency, $\nu$, upper-level energy $E_{\rm up}$, and line strengths, $S\mu^2$) of the lines analysed in this paper: p-H$_2$CO (3$_{0,3}$ – 2$_{0,2}$) (hereafter H$_2$CO), HDCO (4$_{1,4}$ – 3$_{1,3}$), HDCO (4$_{2,2}$ – 3$_{2,1}$), o-D$_{2}$CO (4$_{0,4}$ – 3$_{0,3}$), and o-D$_{2}$CO (4$_{2,3}$ – 3$_{2,2}$) (hereafter D$_2$CO).

The molecular lines were observed with a bandwidth of 59 MHz (76-80 km s$^{-1}$) and a resolution of 122 kHz ($\sim$ 0.17 km s$^{-1}$), with the exception of the HDCO (4$_{1,4}$ – 3$_{1,3}$) and o-D$_{2}$CO (4$_{2,3}$ – 3$_{2,2}$) lines which were observed at lower spectral resolution in the broad spectral windows for the continuum (bandwidth of 1.9 GHz, and resolution of $1.2$ and $0.6$ km s$^{-1}$, respectively).

For each configuration, line-free continuum emission was used for self-calibration. We subtracted the continuum model derived from the self-calibration to produce continuum-subtracted line data. The quasars J1427-4206, J1517-2422, J1625-2527, J1924-2914, and J1626-2951 were used to calibrate the data, with a final absolute flux calibration uncertainty of $\sim$10%. We used a modified version of the calibration pipeline[^2] within CASA 5.6.1-8 (cite: CASA2022), including an additional calibration routine to correct for $T_{\rm sys}$ issues and spectral data normalization[^3].

After merging the 12m and 7m configurations, continuum subtracted line cubes were cleaned using the task $tclean$. We adopted Briggs robustness parameter of 0.5 for molecular lines, while the parameter is -2.0 for the bright continuum to obtain the highest angular resolution. Primary beam corrections were also applied. The size and position angle (PA) of the synthesized beam, and the root mean square noise (r.m.s.) of the continuum maps in Setup 1 and Setup 2 are respectively: 0.42$''$ $\times$ 0.32$''$, PA=$-65^\circ$, 0.26 mJy beam$^{-1}$ and 0.38$''$ $\times$ 0.34$''$, PA=$67^\circ$, 0.27 mJy beam$^{-1}$. The details of the continuum-subtracted line datacubes are listed in Table [\[tab:lines\]](#tab:lines): the r.m.s., the spectral resolution (${\delta} V$), the synthesized beam size and PA, and the field of view (FoV).

# Results

We detected emission from all the transitions of H$_2$CO and its isotopologues listed in Table [\[tab:lines\]](#tab:lines).

Figure [\[spectra\]](#spectra) shows the spectra of the detected transitions (in brightness temperature scale, $T_{\rm B}$) obtained by integrating the emission over the FoV.

Figure [1](#Mom0MAPS) shows moment 0 maps, i.e., the spatial distribution of the lines emission integrated over the emitting velocity range. The continuum emission at 1.3 mm is shown by magenta contours to pinpoint the positions of the A1 and A2 sources (not disentangled at the FAUST spatial resolution), their circumbinary disk, and the B and W protostars (cite: Codella2022; Codella2024; Mercimek2023).

In the following subsections, we analyse the H$_{2}$CO, HDCO, and D$_{2}$CO emission and identify the structures probed by these species.

## H$_{2}$CO emission

![](NEW_MOMENTS.pdf)

Figure [1](#Mom0MAPS) (Upper-Left) shows the moment 0 map of H$_{2}$CO (3$_{0,3}$ – 2$_{0,2}$) emission. We detect compact H$_2$CO emission towards all the protostars in the field, i.e. VLA1623 A, B, and W. In addition, formaldehyde probes extended structures: the envelope of the VLA1623 A+B system, the cavities opened by the outflow driven by VLA1623 A and first imaged in CS $5-4$ by (cite: Ohashi2022), and a bright elongated structure south of VLA1623 W. In the following, we discuss the properties of both compact and extended emissions by focusing on the channel maps of H$_{2}$CO emission on both small scales (Sect. [4.1.1](#sec:smallscale)), and large scales ([4.1.2](#sec:largescale)).

### Compact H$_{2}$CO emission towards VLA1623 A, B, and W

The inspection of the channel maps of H$_{2}$CO allows us to reveal structures emitting only in selected velocity ranges, otherwise diluted in the moment 0 map. Figure [2](#H2CO_disk_AB) shows a zoom-in of the H$_{2}$CO (3$_{0,3}$ – 2$_{0,2}$) emission on the $\sim$ 300 au region around the VLA1623 A and B sources. The emission towards the A and B protostars is compact and spatially unresolved ($\leq$ 50 au) at high-velocity, i.e. at blue- and red-shifted velocities larger than 2 km s$^{-1}$ with respect to the systemic velocity of the A and B sources, (cite: Ohashi2022) and shows velocity gradients, suggestive of rotation. In particular, VLA1623 A shows red-shifted compact emission SW to the continuum peak (at \[$+5.8$, $+6.8$\] km s$^{-1}$, i.e. up to $+3$ km s$^{-1}$ with respect to $V_{\rm sys}$), and blue-shifted emission on the opposite side (\[$+0.4$, $+1.8$\] km s$^{-1}$, i.e. up to $-4.2$ km s$^{-1}$ with respect to $V_{\rm sys}$). The velocity gradient towards VLA1623 B is roughly along the same direction but is inverted (redshifted on the NE, and blue-shifted on the SW), and reach higher radial velocities, up to +10.0 km s$^{-1}$, and –5.2 km s$^{-1}$ (i.e. up to $+6.2$ km s$^{-1}$ and $-9$ km s$^{-1}$ with respect to $V_{\rm sys}$). Remarkably, the velocity gradients observed towards VLA1623 A and VLA1623 B are along the PA of their disks ($\sim 48-49^\circ$ for VLA1623 A1 and A2, and $\sim 42^\circ$ for VLA1623 B, from the high-resolution continuum maps by (cite: Harris2018)), and are consistent with those shown in CS $5-4$ (cite: Ohashi2022). (cite: Codella2022) observed the same velocity gradients in CH$_3$OH lines towards A and B, suggesting that methanol probes the hot corinos (where dust mantles are sublimated at temperatures $\geq$ 100 K) or the outer regions of the protostellar disks, where infalling gas from the envelope causes low-velocity shocks sputtering the dust (cite: Sakai2014a; Sakai2014b). However, the maximum radial velocities of H$_2$CO emission are smaller than those observed using CH$_3$OH (up to $+7$ km s$^{-1}$ and $-2$ km s$^{-1}$ for VLA1623 A, and $+14$ km s$^{-1}$ and $-10$ km s$^{-1}$ for VLA1623 B), suggesting that formaldehyde emission originates from a more extended portion of the envelopes/disks associated with the A and B sources, with respect to methanol.

To conclude, the high-velocity H$_2$CO emission traces the counter-rotating envelopes around the A1+A2 binary system, and VLA1623 B. Note that Fig. [2](#H2CO_disk_AB) shows absorption towards the continuum peak of VLA1623 A and B, at velocities close to $V_{\rm sys}$, plausibly due to line absorption along the line of sight and optically thick dust (see Sect. [\[D2\]](#D2)).

Finally, Fig. [3](#disk_sourceW) shows the H$_{2}$CO (3$_{0,3}$ – 2$_{0,2}$) channel maps in the $\sim$ 300 au region centered at the position of the VLA1623 W protostar. The maps show spatially unresolved ($\leq$ 50 au) blue-shifted emission north of source W, up to velocities of –3 km s$^{-1}$ with respect to the systemic velocity of VLA1623 W (cite: Mercimek2023). This emission is consistent with the blue side of the inner envelope rotating along the N-S direction revealed by (cite: Mercimek2023) using the C$^{18}$O 2-1 line. The non-detection of the southern red-shifted side in H$_2$CO is consistent with the C$^{18}$O emission, which is brighter in the blue-shifted lobe than in the red-shifted one.

The compact H$_2$CO emissions towards the three protostars VLA1623 A, B, and W (labeled as A, B, and W), and the velocity ranges of emission are summarized in Table [\[flows\]](#flows).

![](H2CO_smallscale_channelmaps_A_B.pdf)

![](H2CO_smallscale_channelmaps_W.pdf)

### Streamers and Outflow Cavities in H$_{2}$CO emission

Figure [4](#channel_large_H2CO) shows the H$_{2}$CO (3$_{0,3}$ – 2$_{0,2}$) velocity channel maps over a larger region ($\sim  24\ensuremath{''} \times 24\ensuremath{''}$) with respect to what reported in Sect. [4.1.1](#sec:smallscale). As references, we draw in magenta the outflow cavity walls probed by CS(5–4) emission (cite: Ohashi2022), and the dust continuum emission at 1.3 mm. Several extended structures are detected in H$_{2}$CO. Table [\[flows\]](#flows) lists these structures, and the velocity ranges over which they are detected in the channel maps, moving from blue-shifted to red-shifted velocities, and labeling them from I to VII:

- **(I)** in the \[+0.8, +2.2\] km s$^{-1}$ velocity channels, we detect H$_2$CO emission at the northern edge of the circumbinary disk surrounding VLA1623 A1+A2. This component has already been detected in SO lines by (cite: Hsieh2020) and (cite: Codella2024). They suggested that this feature is associated with an accretion shock produced by a blue-shifted streamer infalling onto the circumbinary disk (component V, see below);

- **(II)** the emission on the \[+1.4 and +2.2\] km s$^{-1}$ velocity range reveals an extended structure located south to VLA1623 A. This component, already imaged in SO lines by (cite: Codella2024), is a blue-shifted streamer infalling on the VLA1623 B protostar. Although the position of the streamer (projected on the plane of the sky) could suggest its association with the southern outflow cavity of VLA1623 A, this is excluded by the fact that the accretion streamer is blue-shifted while the southern cavity side is red-shifted;

- **(III)** a streamer connecting the southern region around A+B with the VLA1623 W protostar is detected in the \[+1.8, +3.2\] km s$^{-1}$ velocity range. The streamer is red-shifted with respect to the systemic velocity of the W object (cite: Mercimek2023).

  This streamer has been previously detected in C$^{18}$O by (cite: Mercimek2023). The H$_{2}$CO emission traces the streamer without the contamination of the A+B envelope emitting in C$^{18}$O;

- **(IV)** the \[+2.4, +3.2\] km s$^{-1}$ velocity range shows an additional elongated structure SW of VLA1623 W. This structure is detected close to the half-power point of the primary beam, therefore no reliable conclusion on its origin can be drawn;

- **(V)** a slightly blue-shifted streamer extending from the North edge of the FoV to NW and then pointing towards VLA1623 A is imaged in the \[+2.8, + 3.6\] km s$^{-1}$ velocity range. This emission likely traces a streamer infalling onto the circumbinary system and causing an accretion shock, whose emission is labeled as I. This scenario has already been suggested by (cite: Hsieh2020) based on SO and C$^{18}$O lines.

- **(VI)** at velocities close to the systemic velocity of VLA1623 A and B, i.e. in the \[+3.4, +4.4\] km s$^{-1}$ velocity range, H$_2$CO emission probes the region encompassed by the rotating outflow cavities first imaged in CS $5-4$ by (cite: Ohashi2022). The association with the outflow cavity is confirmed by kinematics: the northern side is blue-shifted, while the southern side is red-shifted, in agreement with CS emission. The H$_2$CO emission as a probe of outflow cavities has been reported also by (cite: sabatini24) for the outflow associated with the IRS7B protostellar system in the Corona Australis.

- **(VII)** a red-shifted elongated structure south of VLA1623 A is detected at \[+4.4, +5.0\] km s$^{-1}$ velocities, which is not coincident with the southern outflow cavities.

  Thie emission component is perpendicular to the outflow direction, and is plausibly associated with a streamer infalling onto the VLA1623 A and B protostars. (cite: Hsieh2020) has previously reported this structure, proposing the occurrence of an accretion streamer feeding the (red-shifted) southern side of the circumbinary disk around VLA1623 A.

![image](H2CO_largescale_part1.pdf) ![image](H2CO_largescale_part2.pdf)

+:------+:---------------------------------------------:+:-------------------:+:------------------:+:------------------:+:-------------------:+
| Label | Component                                     | H$_2$CO             | HDCO               | D$_2$CO            | Spectrum Position   |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
|       |                                               | (km s$^{-1}$)       | (km s$^{-1}$)      | (km s$^{-1}$)      | ($''$, $''$)        |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
| COMPACT                                                                                                                                     |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
| A     | inner rotating envelope of A                  | \[$+0.4$, $+1.8$\]  | \[$+0.8$, $+2.6$\] | –                  | (0, 0)              |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
|       |                                               | \[$+5.8$, $+6.8$\]  | \[$+5.0$, $+6.8$\] | –                  |                     |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
| B     | inner rotating envelope of B                  | \[$-5.2$, $-1.0$\]  | –                  | –                  | ($-1.16$, $+0.11$)  |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
|       |                                               | \[$+6.6$, $+10.0$\] | –                  | –                  |                     |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
| W     | inner rotating envelope of W                  | \[$-1.2$, $+1.6$\]  | –                  | –                  | ($-10.32$, $+1.26$) |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
|       |                                               | –                   | –                  | –                  |                     |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
| EXTENDED                                                                                                                                    |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
| I     | accretion shock at the northern edge of A CBD | \[$+0.8$, $+2.2$\]  | –                  | –                  | –                   |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
| II    | southern blue-shifted streamer towards B      | \[$+1.4$, $+2.2$\]  | –                  | –                  | –                   |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
| III   | southern red-shifted streamer towards W       | \[$+1.8$, $+3.2$\]  | –                  | –                  | –                   |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
| IV    | SE elongated emission associated with W       | \[$+2.4$, $+3.2$\]  | –                  | –                  | –                   |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
| V     | northern blue-shifted streamer towards A      | \[$+2.8$, $+3.6$\]  | \[$+2.6$, $+3.8$\] | \[$+3.2$, $+3.6$\] | –                   |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
| VI    | outflow cavities driven by A                  | \[$+3.4$, $+4.4$\]  | \[$+2.6$, $+5.0$\] | \[$+3.4$, $+4.4$\] | ($+1.49$, $-3.78$)  |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+
| VII   | southern red-shifted streamer towards A       | \[$+4.4$, $+5.0$\]  | \[$+3.8$, $+5.0$\] | \[$+4.4$, $+5.0$\] | ($-2.01$, $-3.78$)  |
+-------+-----------------------------------------------+---------------------+--------------------+--------------------+---------------------+

## HDCO emission

The moment 0 maps of the HDCO (4$_{1,4}$ – 3$_{1,3}$) and (4$_{2,2}$ – 3$_{2,1}$) lines are shown in Fig. [1](#Mom0MAPS), while the channel maps over a small ($\sim 3\ensuremath{''} \times 2\ensuremath{''}$) and large ($\sim 19\ensuremath{''} \times 16\ensuremath{''}$) region are shown in Fig. [\[HDCO_38K_APPENDIX\]](#HDCO_38K_APPENDIX) and [\[HDCO_63K_APPENDIX\]](#HDCO_63K_APPENDIX). The maps show no HDCO emission detected toward VLA1623 B and W, while the emission towards VLA1623 A consists of several components.

In Figure [\[2HDCO\]](#2HDCO) we show the HDCO emission integrated over selected velocity intervals, i.e. at systemic velocity ($V_{\rm sys}$ = +3.8 km s$^{-1}$, left panels); at low-velocity (up to $\pm$ 1.2 km s$^{-1}$ with respect to $V_{\rm sys}$, middle panels); and at high velocity (up to $\pm3.0$ km s$^{-1}$ with respect to $V_{\rm sys}$, right panels). The figure shows that some of the components identified in the analysis of the H$_2$CO channel maps are also associated with HDCO emission, namely:

- **(A)** the high-velocity HDCO emission is compact around the A1+A2 binary system, and show a velocity gradient along the NE-SW direction, in agreement with H$_2$CO (see Fig. [2](#H2CO_disk_AB)), and CH$_3$OH (cite: Codella2022). As for H$_2$CO, the HDCO compact emission is at lower velocities than methanol, thus it probes a more extended region of the rotating envelope around VLA1623 A (see Sect. [4.1.1](#sec:smallscale));

- **(VI)** the HDCO emission at systemic velocity and low blue- and red-shifted velocities traces the rotating outflow cavities driven by VLA1623 A, in agreement with CS and H$_2$CO emission (cite: Ohashi2022);

- **(V, VII)** the lower excitation HDCO (4$_{1,4}$ – 3$_{1,3}$) line ($E_{\rm u}$ = 38 K), which is brighter, also shows low-velocity emission north and south of VLA1623 A, which is not associated with the outflow cavities. Despite the low S/N ($\sim$ 3$\sigma$) of the HDCO channel maps, we identify that the low-velocity emission is associated with the northern blue-shifted and southern red-shifted streamers infalling on VLA1623 A and revealed by H$_2$CO (components V and VII, see Table [\[flows\]](#flows)).

## D$_2$CO emission

The moment 0 map of the D$_2$CO lower excitation line (4$_{0,4}$ – 3$_{0,3}$) is shown in Fig. [1](#Mom0MAPS), while Figure [\[channel_D2CO\]](#channel_D2CO) shows the velocity channel maps, with overplot the outflow cavities revelead by CS emission (cite: Ohashi2022), and the dust continuum emission at 1.3 mm. Table [\[flows\]](#flows) lists the detected structures, moving along the velocity channel maps from blue-shifted to red-shifted velocities, and labeling them from V to VII. As for HDCO, D$_{2}$CO shows no emission towards the VLA1623 B and W protostars (components B and W in Table [\[flows\]](#flows)), while faint emission from the inner envelope of VLA1623 A is recovered in the spectrum extracted at the source continuum peak (see Sect. [\[D2\]](#D2)). Surprisingly, the D$_{2}$CO moment 0 map and channel maps reveal a spatial distribution which is different than that of HDCO and H$_2$CO: the D$_{2}$CO emission close to systemic velocity ($V_{\rm sys}$ $\pm$ 1 km s$^{-1}$) extends out to the edges of the field of view, and probe a region which does not coincide with the wide-angle outflow cavities outlined by the CS emission.

Figure [\[flows_D2CO_H2CO\]](#flows_D2CO_H2CO) compares the spatial distributions of H$_{2}$CO and D$_{2}$CO in selected velocity ranges, and allows us to identify some of the structures detected in H$_2$CO and reported in Table [\[flows\]](#flows). More specifically, D$_2$CO probes the following components:

- **(V)** on the \[+3.2, +3.6\] km s$^{-1}$ velocity range (Panel a) the D$_2$CO emission is partially coincident with the northern blue-shifted streamer revealed by H$_2$CO. However, the peak of the D$_2$CO emission is at the edges of the H$_2$CO structure;

- **(VI)** the D$_2$CO emission on the \[+3.4, +4.4\] km s$^{-1}$ velocity range (Panel b) traces the outflow cavities detected in H$_2$CO. Note that the D$_2$CO emission at low velocities looks more contaminated by extended emission plausibly associated with the large-scale envelope;

- **(VII)** the D$_2$CO emission on \[+4.4, +5.0\] km s$^{-1}$ velocity range (Panel c) appears associated with the southern red-shifted streamer labeled as VII in the H$_2$CO channel maps. Figure [\[D2CO_Mom1and2\]](#D2CO_Mom1and2) shows the intensity-weighted mean velocity (moment 1) map of D$_2$CO (4$_{0,4}$ – 3$_{0,3}$) emission, where the red-shifted streamer infalling on the VLA1623 A system from the SE is clearly outlined. However, also in this case, the emission peaks of H$_2$CO and D$_2$CO are not colocated, with H$_2$CO mainly associated with the eastern side of the VII structure and D$_2$CO mainly emitted from the western side.

The higher excitation D$_{2}$CO (4$_{2,3}$ – 3$_{2,2}$) line ($E_{\rm up} \sim 50$ K) is also marginally detected. The channel maps (Fig. [\[channel_D2CO_50K\]](#channel_D2CO_50K)) show emission at very low S/N ($\sim$ 2–3$\sigma$), but tentatively suggest a spatial distribution consistent with that of the brighter lower-excitation D$_{2}$CO line (4$_{0,4}$ – 3$_{0,3}$). The maps show signatures of the outflow cavities at systemic velocity ($+3.8$ km s$^{-1}$), and of the southern red-shifted streamer at $+4.4$ km s$^{-1}$ (labeled as VI and VII in Table [\[flows\]](#flows)). Despite the low S/N, the D$_{2}$CO (4$_{2,3}$ – 3$_{2,2}$) line is clearly detected in the spectrum obtained by integrating the emission over a 10$\ensuremath{''}$ region centered on VLA1623 A (see Fig. [\[D2CO-233\]](#D2CO-233)). The line profile is in agreement with the profile of the lower excitation (4$_{0,4}$ – 3$_{0,3}$) line (see Fig. [\[superspectra\]](#superspectra)), peaking in the same velocity range (3.8 – 4.4 km s$^{-1}$).\

# Discussion

The analysis of the channel maps presented in Sect. [4](#results) showed that H$_2$CO and its deuterated isotopologues trace several components of the VLA1623 protostellar system: the inner protostellar envelopes, the outflow cavities, and the accretion streamers. VLA1623 is therefore an excellent laboratory to study the D/H ratio in these different components. The derivation of the D/H values is reported in Sect. [\[D2\]](#D2), while in Sect. [\[comparison\]](#comparison) we compare the estimated D/H ratios with values derived for other sources in the literature.

In addition, within a fixed emitting velocity range, H$_2$CO, HDCO, and D$_2$CO do not always show the same spatial distribution. The origin of this difference will be discussed in Sect. [\[D1\]](#D1).

[^1]: E-mail: seyma.mercimek@manchester.ac.uk

[^2]: https://github.com/autocorr/faust$\_$line$\_$imaging; Chandler et al. (in preparation)

[^3]: https://help.almascience.org/kb/articles/what-errors-could-originate-from-the-correlator-spectral-normalization-and-tsys- calibration; Moellenbrock et al. (in preparation)

![image](HDCO38K_channel.pdf) ![image](HDCO63K_channel.pdf)

![](D2CO_channel.pdf)

![](d2co-1line-10arcsec.pdf)

## Deuteration in the inner envelope, in the outflow cavities, and in the streamers

Figure [4](#superspectra) shows the spectra (in $T_{\rm B}$ scale) of the observed H$_2$CO, HDCO, and D$_2$CO lines (see Tab. [\[tab:lines\]](#tab:lines)), extracted in five selected positions representative of the compact and extended components identified towards the VLA1623-2417 cluster: at the dust continuum peaks of the protostellar sources VLA1623 A, B, and W (components A, B, and W in Table [\[flows\]](#flows)); at a representative position of the SE outflow cavity (VI component); and at a representative position of the red-shifted southern streamer (VII component). The R.A. and Dec. offset of the selected positions are listed in Tab. [\[flows\]](#flows), and marked in Figs. [\[channel_large_H2CO\]](#channel_large_H2CO), [1](#2HDCO), [2](#channel_D2CO).

Different positions are associated with different line profiles, reflecting the kinematical components shown by the channel maps analysed in Sect. [\[results\]](#results):

- The spectra extracted at the position of the VLA1623 A continuum peak exhibit a narrow absorption feature at systemic velocity detected in the lower excitation H$_2$CO and D$_2$CO lines ($E_{\rm up}$ = 21 K, and 28 K). This is due to absorption by the cold gas along the line of sight and by the optically thick dust continuum emission.

  The spectra shows blue-shifted and red-shifted emission, which probe the inner rotating envelope of A. In additon, the lines profiles are asymmetric with the blue-shifted emission more intense than the red-shifted one, suggestive of infall.

- The H$_2$CO spectrum toward VLA1623 B shows symmetric red-shifted and blue-shifted emission out to $\sim \pm 10$ km s$^{-1}$ with respect to the systemic velocity (+3.8 km s$^{-1}$), which probes the inner portion of the rotating envelope of B, consistently with the H$_2$CO channel maps (Fig. [\[H2CO_disk_AB\]](#H2CO_disk_AB)).

  As for the spectra towards VLA1623 A, the lower excitation H$_2$CO and D$_2$CO lines exhibit a narrow absorption feature at systemic velocity due to absorption by the cold gas along the line of sight and by the optically thick dust continuum emission. This absorption feature has been also observed in the CS, CCH, and H$^{13}$CO$^{+}$ low excitation lines ($E_{\rm up}$ = 25-35 K) toward VLA1623 B (cite: Ohashi2022). In addition, the H$_2$CO spectrum shows a red-shifted excess, also observed in HDCO, which originates from the NW red-shifted side of the rotating outflow cavity associated with VLA1623 A (labeled as NW Outflow Cavity in Table [\[temperatures\]](#temperatures)).

- The H$_2$CO spectrum towards VLA1623 W shows blue-shifted emission, unveiling the blue-shifted northern side of the inner rotating envelope of W, as illustrated in Fig. [\[H2CO_disk_AB\]](#H2CO_disk_AB), which is brighter than the red-shifted one consistent with the observations of C$^{18}$O by (cite: Mercimek2023). No emission is detected in HDCO and D$_2$CO.

- The H$_2$CO spectrum extracted at the position along the SE outflow cavity (component VI) peak at systemic velocity and shows a counterpart in the HDCO and D$_2$CO spectra. In addition, the spectrum shows a blue-shifted emission component, which probes the southern blue-shifted streamer (component II), which spatially overlaps with the cavity. This component is also detected in HDCO.

- The spectra extracted at the position of the southern red-shifted streamer (component VII) exhibits a narrow (0.6–0.8 km s$^{-1}$) nearly Gaussian emission component at red-shifted velocities in H$_2$CO, HDCO, and D$_2$CO.

Despite the narrow range of upper-level energies of the detected HDCO lines (38 K and 63 K), we used the intensity ratio of the two HDCO lines to determine the excitation temperature ($T_{\rm ex}$) of the gas in the different components. Local thermodynamic equilibrium (LTE) and optically thin emission have been assumed. To properly measure the line intensities from the spectra extracted at the position of the continuum peaks of A and B and avoid the effect of absorption at systemic velocity, we integrated the emission on the blue-shifted and red-shifted velocity ranges highligthed in Fig. [4](#superspectra) by yellow bands. Table [\[temperatures\]](#temperatures) reports, for each component, the velocity ranges used for integration, the obtained line integrated intesities, and the excitation temperature estimated from the HDCO line ratio.

The excitation temperature towards VLA1623 A is $125\pm$60 K, supporting the association of the observed line emission with the inner envelope heated by the VLA1623 A binary system. The excitation temperature in the SE outflow cavity is lower 37$\pm$19 K. Low $T_{\rm ex}$ is obtained also towards VLA1623 B (28$\pm$12 K), confirming that the HDCO emission detected towards B plausibly probes the redshifted side of the rotating outflow cavity as suggested by the maps in Fig. [1](#2HDCO). Finally, the excitation temperature estimated in the streamers (II and VII) is an upper limit, due to the non-detection of the higher excitation HDCO line, and is $\le15$ K. This is consistent with the expected temperatures at a separation of $\sim600$ au from the protostars (see Tab. [\[flows\]](#flows)).

To determine the column densities of H$_2$CO, HDCO, and D$_2$CO, we assumed LTE and optically thin emission and adopted the excitation temperature ($T_{\rm ex}$) estimated from the HDCO lines. This is based on the assumption that the three species probe the same component, an hypothesis reinforced by the similarity of the extracted line profiles at each position. As reported in Tab. [\[temperatures\]](#temperatures), the HDCO column density towards VLA1623 A is 5$\pm$3 $\times$ 10$^{13}$ cm$^{-2}$, an order of magnitude higher than that measured in the VLA1623 B red-shifted and SE cavities, $N_{\rm HDCO}$ $\simeq$ 5–6 $\times$ 10$^{12}$ cm$^{-2}$. The HDCO column densities in the streamers II and VII are $\geq$ 10$^{12}$ cm$^{-2}$. The formaldehyde column densities are $\simeq$ 3 $\times$ 10$^{14}$ cm$^{-2}$ (VLA1623 A), and 3–8 $\times$ 10$^{13}$ cm$^{-2}$ for the other positions. Finally, the D$_2$CO column densities are $\geq$ 10$^{12}$ cm$^{-2}$ in all the positions listed in Tab. [\[flows\]](#flows).

Table [\[temperatures\]](#temperatures) reports, for each position, the abundance ratios between the deuterated isotopologue and the main species, H$_2$CO, which are equal to the column densities ratios. Then, following (cite: Manigand2019), the deuterium fractions, D/H, are obtained from the abundance ratios: D/H = 0.5 $\times$ $N_{\rm HDCO}$/$N_{\rm H_2CO}$, and D/H = $\sqrt{N_{\rm D_2CO}/N_{\rm H_2CO}}$.

The D-fraction of H$_{2}$CO in the inner envelope of VLA1623 A is 8% for HDCO, and 6% for D$_2$CO. Remarkably, we report the first estimate of D/H in the cavities opened by the protostellar outflow. Namely, D/H is 6% (HDCO), and 35% (D$_2$CO) in the SE outflow cavity; and 4% (HDCO), and $\leq$ 22% (D$_2$CO) in the NW outflow cavity. Finally, the estimate of D/H in the streamers is not accurate because we only have an upper limit of the excitation temperature, hence a lower limit of the column densities of the three species. However, assuming that H$_2$CO, HDCO, and D$_2$CO are excited at the inferred $T_{\rm ex}$ upper limit, we obtain an estimate of the D/H in the streamers: D/H is 3%–15% (for HDCO), and 17% (for D$_2$CO).

We show the intensity ratio maps of HDCO/H$_2$CO and D$_2$CO/H$_2$CO in Fig. [\[RatioMaps\]](#RatioMaps). The maps are integrated taking into account the velocity ranges imaging the V (orthern blue-shifted streamer towards A), VII (outflow cavities driven by A ), and VII (southern red-shifted streamer towards A) components listed in Table [\[flows\]](#flows) to be consistent with the deuteration derived in the system. The distribution of the ratio maps is consistent with that found in Table [\[temperatures\]](#temperatures).

![](superspectra2.pdf)

## Comparison with previous results on H$_2$CO deuteration

![](deut_vla1623.pdf)

Figure [5](#deut_vla1623) compares the D/H values estimated for VLA1623 with previous interferometric measurements obtained for Class 0 hot-corinos and disks either in the context of the FAUST LP (cite: Evans2023; Podio2024) or in previous ALMA studies (cite: Persson2018; Manigand2020; vandermarel21b; Brunken2022). The range of D/H values found in the envelope, outflow cavities, and infalling streamer of VLA1623 A agrees with earlier findings.

Interestingly, both the \[HDCO\]/\[H$_2$CO\] and \[D$_2$CO\]/\[H$_2$CO\] abundance ratios in the streamer are in agreement with those found by (cite: Podio2024) in the Class I disk IRS 63. They report a significant increase of the abundance of D$_2$CO at the location where the infalling streamer collides with the disk, causing a shock and leading to the release in gas-phase of the molecules trapped in the dust mantles. The accretion shock thus reveal the composition of the ices in the disk of IRS 63. However, they cannot determine if the ice composition is inherited from the prestellar stage, or if ices are formed and/or reprocessed in the disk itself. Our observations of VLA1623 shows D$_2$CO-enriched mantles in the streamer, with D/H ratios similar to those in the Class I disk of IRS 63, thus suggesting that deuteration is mostly set at the prestellar stage, and inherited by the disk at its formation and/or through streamers. The comparison within each class of regions and between types of regions is difficult because of the inherent differences that are already known. These variations can be driven by local physical conditions. Hence the present data call for further observations of other star-forming regions to look for differences in D/H within the same structure (such as along streamers or cavities) which may share similar conditions such as timescale, evolution, and physical conditions.

+:-----------+:------------:+:--------------:+:-------------------------------------:+:-----------------------:+:-------------------:+:----------:+
| Species    | $T_{\rm ex}$ | Velocity range | Intensity                             | $N$                     | \[X\]/\[H$_{2}$CO\] | D/H        |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
|            | \(K\)        | (km s$^{-1}$)  | (K km s$^{-1}$)                       | (cm$^{-2}$)             |                     | $\%$       |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| VLA1623 A                                                                                                                                       |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| H$_2$CO    | $125$        | –1.0 – +2.0    | 5.9$\pm$0.2                           | $3\times10^{14}$        | –                   | –          |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| HDCO       | $125 (60)$   | –1.0 – +2.0    | 6.1$\pm$0.2 (38K) / 4.0$\pm$0.1 (63K) | $5(3)\times10^{13}$     | 0.160               | 8          |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| D$_2$CO    | $125$        | –1.0 – +2.0    | 0.4$\pm$0.1                           | $1\times10^{12}$        | 0.003               | 6          |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| NW Outflow Cavity (VLA1623 B position)                                                                                                          |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| H$_2$CO    | $28$         | +5.0 – +13.0   | 8.6$\pm$0.2                           | $8\times10^{13}$        | –                   | –          |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| HDCO       | $28 (12)$    | +5.0 – +13.0   | 0.9 (38K) / 0.3 (63K)                 | $6(4)\times10^{12}$     | 0.075               | 4          |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| D$_2$CO    | $28$         | +5.0 – +13.0   | $\le0.7\pm$0.1                        | $\leq$ $4\times10^{12}$ | $\leq$ 0.050        | $\leq$ 22  |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| SE Outflow Cavity, VI                                                                                                                           |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| H$_2$CO    | $37$         | +3.1 – +5.0    | 3.7$\pm$0.1                           | $4\times10^{13}$        | –                   | –          |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| HDCO       | $37 (19)$    | +3.1 – +5.0    | 0.7 (38K) / 0.3 (63K)                 | $5(4)\times10^{12}$     | 0.125               | 6          |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| D$_2$CO    | $37$         | +3.1 – +5.0    | 1.1$\pm$0.1                           | $5\times10^{12}$        | 0.125               | 35         |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| Streamer II (SE Outflow Cavity position)                                                                                                        |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| H$_2$CO    | $\leq$ 15    | +0.8 – +2.1    | 3.8$\pm$0.1                           | $\geq$ $3\times10^{13}$ | –                   | –          |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| HDCO       | $\leq$ 15    | +0.8 – +2.1    | 0.7$\pm$0.1 (38 K)                    | $\geq$ $2\times10^{12}$ | 0.067               | 3          |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| D$_2$CO    | –            | –              | –                                     | –                       | –                   | –          |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| Streamer VII                                                                                                                                    |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| H$_2$CO    | $\leq$ 10    | +2.5 – +6.1    | 4.1$\pm$0.1                           | $\geq$ $3\times10^{13}$ | –                   | –          |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| HDCO       | $\leq$ $10$  | +2.5 – +6.1    | 0.5$\pm$0.1 (38 K)                    | $\geq$ $9\times10^{12}$ | 0.300               | 15         |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+
| D$_2$CO    | $\leq$ 10    | +2.5 – +6.1    | 1.4$\pm$0.1                           | $\geq$ $1\times10^{12}$ | 0.030               | 17         |
+------------+--------------+----------------+---------------------------------------+-------------------------+---------------------+------------+

## On the origin of D$_2$CO extended emission

ALMA-FAUST interferometric observations show extended emission of D$_{2}$CO toward the multiple system VLA1623-2417 for the first time. As reported in Sect. [\[results\]](#results), D$_{2}$CO emission reveals a puzzling spatial distribution, which does not match that of H$_2$CO and HDCO. While H$_2$CO and HDCO emissions have their peak in the hot corino toward VLA1623 A, in the outflow cavities, and in the redshifted southern streamer, D$_2$CO probes mostly the flattened envelope perpendicular to the outflow direction (see Fig. [\[Mom0MAPS\]](#Mom0MAPS)), which is fainter in H$_2$CO and HDCO. A different spatial distribution of D$_2$CO with respect to that of H$_2$CO and HDCO has also been found towards another FAUST protostellar source, the disk-streamer system of IRS 63, and has been interpreted as due to a different chemical origin of D$_2$CO, with respect to H$_2$CO and HDCO (cite: Podio2024).

More specifically, formaldehyde and its deuterated isotopologues can form both in the gas phase and on the surface of dust grains. In warm gas (cite: Parise2009) H$_2$CO, HDCO, and D$_2$CO follow a similar formation path, starting from CH$_3^+$ which reacts either with H$_2$ (to form H$_2$CO), or with HD (to form CH$_2$D$^+$ and CHD$_2^+$, and from the latter HDCO and D$_2$CO) (cite: Roueff2007; Roueff2013-CH2D+). However, the different spatial distribution of D$_2$CO points to its formation on the surface of dust grains, following the scheme presented in Fig. 4 by (cite: Podio2024). The processes occurring on the grains may cause an enhancement of the D$_2$CO abundance with respect to that of HDCO and H$_2$CO on the ices. Then, when the ice mantles are released in the gas phase due to shocks (as in the case of IRS 63) or to a radiation field, we may observe an enhancement of D$_2$CO emission, with respect to HDCO and H$_2$CO.

Following the above reasoning, we propose that in the case of the VLA1623 protostellar cluster, the fact that D$_2$CO is detected in an extended region where HDCO and H$_2$CO emission is faint, is due to deuterated molecules formation on the grains in the cold prestellar phase and release in the gas phase due to irradiation within a dense photodissociation region (PDR).

Figure [\[D2CO_Mom1and2\]](#D2CO_Mom1and2) shows the moment 2 (velocity dispersion) map of D$_2$CO (4$_{0,4}$ – 3$_{0,3}$) emission, which indicates that the extended emission partially traces the outflow cavities and the streamer as listed in Table [\[flows\]](#flows). The extended D$_2$CO emission shows a narrow velocity dispersion between 0.3 and 1.2 km s$^{-1}$. This is not consistent with the release of D$_2$CO molecules in shocks, which would produce large line profiles. Thus, we investigate whether the observed D$_2$CO emission can be caused by the release of the icy mantles in gas-phase due to a PDR. (cite: Rawlings2013) presented infrared observations taken with WISE (Wide-field Infrared Survey Explorer), *Herschel*, and 2MASS (Two Micron All-Sky Survey), and visual extinction maps towards the VLA1623-2417 region in the Ophiuchus cloud. These maps show that VLA1623-2417 is illuminated by two nearby B stars (HD147889 and $\rho$ Oph AB). Their study suggests high irradiation and an increased emission of PAHs (polycyclic aromatic hydrocarbons). The 2MASS catalog also indicate high visual extinction ($A_{\rm v}$ \> 30 mag) towards VLA1623-2417. In addition, polarisation studies with JCMT SCUBA by (cite: Pattle2019) showed evidence of an external radiation field which may cause dust grain alignment.

In summary, the VLA1623-2417 protostellar cluster could be affected by a locally stronger radiation field. Thus, the narrow velocity dispersion of D$_2$CO emission (Fig. [\[D2CO_Mom1and2\]](#D2CO_Mom1and2)) could trace the front of the radiation field caused by the massive B stars and OB association in the Oph A core. If this is the case, D$_2$CO molecules are photo-desorbed from the grains.

[^1]: E-mail: seyma.mercimek@manchester.ac.uk

# Summary and Conclusions

The FAUST ALMA Large Program has imaged deuterated formaldehyde emission in the VLA1623-2417 protostellar cluster down to the spatial scale of 50 au. Emission from H$_2$CO (3$_{0,3}$ – 2$_{0,2}$), HDCO (4$_{1,4}$ – 3$_{1,3}$), HDCO (4$_{2,2}$ – 3$_{2,1}$), D$_2$CO (4$_{0,4}$ – 3$_{0,3}$), and D$_2$CO (4$_{2,3}$ – 3$_{2,2}$) has been detected and shows both extended and compact structures. The main findings are summarised as follows:

1.  The binary system VLA1623 A is associated with formaldehyde and its deuterated isotopologues. Conversely, the VLA1623 B and W protostars have been detected in H$_2$CO but not in HDCO and D$_2$CO. High-velocity formaldehyde emissions trace the two counter-rotating, spatially unresolved cores ($\leq$ 50 au) of VLA1623 A and VLA1623 B, and the brightest blue-shifted side of the envelope of VLA1623 W;

2.  H$_2$CO, HDCO, and D$_2$CO also probe extended structures, including the symmetric and rotating cavities created by the VLA1623 A outflow, and two extended (approximately 1000 au) accretion streamers feeding the VLA1623 A+B system.

3.  Based on the ratio of the HDCO lines, we estimate the gas temperature to be approximately 125 K towards the VLA1623 A hot-corino, between 20-40 K in the cavities, and $\leq$ 15 K in the streamers;

4.  D$_2$CO reveals an extended component, which is fainter in H$_2$CO and HDCO, that probes the flattened envelope perpendicular to the outflow direction. We suggest that the extended D$_2$CO emission results from D$_2$CO formation on grains during the cold prestellar phase and its release into the gas phase due to the photo-dissociation region caused by two nearby B stars (HD147889 and $\rho$ Oph AB);

5.  The D-fraction of formaldehyde in the hot-corino, outflow cavities, and infalling streamers of VLA1623 A lies in the following ranges: \[HDCO\]/\[H$_2$CO\] $\sim 0.07-0.3$, and \[D$_2$CO\]/\[H$_2$CO\] $\sim 0.003-0.13$. These values are comparable to those previously obtained for other Class 0 hot-corinos, as well as for Class I and II disks.

Our results support the hypothesis that deuterated species primarily form during the cold prestellar stage and are subsequently inherited by the forming protostar.

# Acknowledgements

We are grateful to the referee P.T.P. Ho for his instructive report. We also thank N. Balucani for precious discussions on the chemistry of formaldehyde isotopologues. This project has received funding from the EC H2020 research and innovation programme for: (i) the project "Astro-Chemical Origins” (ACO, No 811312), and (ii) the European Research Council (ERC) project “The Dawn of Organic Chemistry” (DOC, No 741002). LP, GS, and ClCo acknowledge the PRIN-MUR 2020 BEYOND-2p (Astrochemistry beyond the second period elements, Prot. 2020AFB3FX), the project ASI-Astrobiologia 2023 MIGLIORA (Modeling Chemical Complexity, F83C23000800005), the INAF-GO 2023 fundings PROTO-SKA (Exploiting ALMA data to study planet forming disks: preparing the advent of SKA, C13C23000770005), the INAF Mini-Grant 2022 “Chemical Origins” (PI: L. Podio), and financial support under the National Recovery and Resilience Plan (NRRP), Mission 4, Component 2, Investment 1.1, Call for tender No. 104 published on 2.2.2022 by the Italian Ministry of University and Research (MUR), funded by the European Union – NextGenerationEU– Project Title 2022JC2Y93 Chemical Origins: linking the fossil composition of the Solar System with the chemistry of protoplanetary disks – CUP J53D23001600006 - Grant Assignment Decree No. 962 adopted on 30.06.2023 by the Italian Ministry of University and Research (MUR). G.S. also acknowledges the INAF-Minigrant 2023 TRIESTE ("TRacing the chemIcal hEritage of our originS: from proTostars to planEts"; PI: G. Sabatini). D.J. is supported by NRC Canada and by an NSERC Discovery Grant. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01205.L. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under a cooperative agreement by Associated Universities, Inc.\

# Data Availability

The raw data are available on the ALMA archive at the end of the proprietary period (ADS/JAO.ALMA#2018.1.01205.L).

[^1]: E-mail: seyma.mercimek@manchester.ac.uk

[^1]: E-mail: seyma.mercimek@manchester.ac.uk

# Additional Material

## Integrated spectra towards VLA1623–2417

Figure [\[spectra\]](#spectra) reports the spectra (in brightness temperature, $T_{\rm B}$, scale) obtained integrating the line emission over the FoV of the VLA1623–2417 observations (see Table [\[tab:lines\]](#tab:lines)).

[^1]: E-mail: seyma.mercimek@manchester.ac.uk

![](LAS_spectra.pdf)

## Channel maps of the HDCO lines

We report the channel maps of the HDCO 4$_{1,4}$ – 3$_{1,3}$ (Fig. [2](#HDCO_38K_APPENDIX)), and 4$_{2,2}$ – 3$_{2,1}$ (Fig. [3](#HDCO_63K_APPENDIX)) emission. We show both high-velocity emission on small spatial scale (upper panels), and low-velocity emission on large spatial scales (lower panels).

![](channel_map_HDCO_38K_DISK1.pdf)

![image](disk_channelmaps_HDCO_63K) ![image](HDCO_63K_large_scale_schannelMAPS.pdf)

## Integrated intensity (moment 0) maps of D$_{2}$CO (4$_{0,4}$ – 3$_{0,3}$)

We present the integrated intensity maps (moment 0) of D$_2$CO (4$_{0,4}$ – 3$_{0,3}$) towards VLA1623–2417 integrated on different velocity ranges in Fig. [4](#flows_D2CO_H2CO).

## Channel maps of the D$_{2}$CO (4$_{2,3}$ – 3$_{2,2}$) 

Figure [5](#channel_D2CO_50K) shows the channel maps of the D$_{2}$CO (4$_{2,3}$ – 3$_{2,2}$) emission in VLA1623-2417.

## Intensity ratio maps of HDCO/H$_2$CO and D$_2$CO/H$_2$CO

Figure [6](#RatioMaps) shows the Intensity ratio maps of HDCO(4$_{1,4}$ – 3$_{1,3}$)/p-H$_2$CO(3$_{0,3}$ – 2$_{0,2}$) (upper rows) and o-D$_2$CO(4$_{0,4}$ – 3$_{0,3}$)/p-H$_2$CO(3$_{0,3}$ – 2$_{0,2}$) (bottom rows) towards the VLA1623-2417. region. In particular, three components are imaged: (see Tab. [\[flows\]](#flows)): northern blue-shifted streamer towards A (label V), outflow cavities driven by A (VI), and southern red-shifted streamer towards A (VII).

## Intensity-weighted mean velocity and velocity-dispersion maps of D$_{2}$CO (4$_{0,4}$ – 3$_{0,3}$)

We present the intensity-weighted mean velocity (moment 1) and velocity–dispersion (moment 2) maps of D$_2$CO (4$_{0,4}$ – 3$_{0,3}$) emission spanning the velocity range from +3.0 km s$^{-1}$ to +5.2 km s$^{-1}$ towards VLA1623–2417 in Fig. [7](#D2CO_Mom1and2)

![](D2CO_H2CO_flows_NEW.pdf)

![](D2CO_50K_channelmaps.pdf)

![](RATIO_MAP.pdf)

![image](D2CO_MOM1.pdf) ![image](D2CO_MOM2.pdf)

[^1]: E-mail: seyma.mercimek@manchester.ac.uk

</paper>

Write the methods card for this paper.