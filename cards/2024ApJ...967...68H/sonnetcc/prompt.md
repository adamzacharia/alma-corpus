# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...967...68H\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...967...68H",
 "title": "Radial and Vertical Constraints on the Icy Origin of H<SUB>2</SUB>CO in the HD 163296 Protoplanetary Disk",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Hernández-Vera, Claudio",
 "n_authors": 9,
 "arxiv_id": "2404.06133",
 "doi": "10.3847/1538-4357/ad3cdb",
 "alma_projects_linked_by_archive": [
  "2016.1.00884.S",
  "2018.1.01055.L"
 ]
}
```

Paper text:
<paper>
# Radial and vertical constraints on the icy origin of H$_2$CO in the HD 163296 Protoplanetary Disk

## Abstract

H$_2$CO is a small organic molecule widely detected in protoplanetary disks. As a precursor to grain-surface formation of CH$_3$OH, H$_2$CO is considered an important precursor of O-bearing organic molecules that are locked in ices. Still, since gas-phase reactions can also form H$_2$CO, there remains an open question on the channels by which organics form in disks, and how much the grain versus the gas pathways impact the overall organic reservoir. We present spectrally and spatially resolved Atacama Large Millimeter/submillimeter Array observations of several ortho- and para-H$_2$CO transitions toward the bright protoplanetary disk around the Herbig Ae star HD 163296. We derive column density, excitation temperature, and ortho-to-para ratio (OPR) radial profiles for H$_2$CO, as well as disk-averaged values of $N_{\mathrm{T}}\sim4\times 10^{12}$ cm$^{-2}$, $T_{\mathrm{ex}}\sim20$ K, and $\mathrm{OPR}\sim2.7$, respectively. We empirically determine the vertical structure of the emission, finding vertical heights of $z/r\sim0.1$. From the profiles, we find a relatively constant $\mathrm{OPR}\sim2.7$ with radius, but still consistent with $3.0$ among the uncertainties, a secondary increase of $N_{\mathrm{T}}$ in the outer disk, and low $T_{\mathrm{ex}}$ values that decrease with disk radius. Our resulting radial, vertical, and OPR constraints suggest an increased UV penetration beyond the dust millimeter edge, consistent with an icy origin but also with cold gas-phase chemistry. This Herbig disk contrasts previous results for the T Tauri disk, TW Hya, which had a larger contribution from cold gas-phase chemistry. More observations of other sources are needed to disentangle the dominant formation pathway of H$_2$CO in protoplanetary disks.

# Introduction

Planets are formed in disks made of dust and gas around young stars, known as protoplanetary disks. Since part of their composition is thought to be incorporated into nascent planets, they are considered a material reservoir for planetary assembly (cite: Williams2011; Andrews2020; Miotello2023). Hence, the chemical composition of protoplanetary disks is crucial when disentangling what kind of planets can be formed around other stars (cite: Oberg2023).

Among the variety of molecules detected in disks, a significant portion are organic species (cite: McGuire2022), ranging from small organics to complex organic molecules (COMs) composed of six or more atoms (cite: Herbst2009). COMs have been broadly studied across interstellar and circumstellar environments (cite: Jorgensen2020; Oberg2021; Ceccarelli2023), as they can potentially be precursors of prebiotic species (cite: Garrod2013; Rivilla2019). Tracing the organic inventory in protoplanetary disks is therefore considered a critical factor in estimating the potential habitability of other planetary systems (cite: Booth2021; Oberg2021) and disentangling the origins of life in our planetary system (cite: Altwegg2019; Ceccarelli2023).

Although complex hydrocarbons and N-bearing COMs are commonly detected in protoplanetary disks, O-bearing COMs detections are scarce (cite: Oberg2023) because most of them are expected to be locked in the ice mantles on the surface of dust grains (cite: Oberg2011; Boogert2015). Even methanol (CH$_3$OH), one of the simplest O-bearing COMs and considered a building block in forming more complex species (cite: Oberg2009), has had relatively few detections in disks. Except for TW Hya (cite: Walsh2016), the closest protoplanetary disk, CH$_3$OH detections are typically restricted to peculiar sources with specific warm conditions (cite: vantHoff2018; Lee2019; Podio2020) or cavities directly exposed to the radiation of the host star (cite: Booth2021; vanderMarel2021; Booth2023), consistent with an icy origin. Thus, the need arises for an abundant gas-phase molecule capable of tracing the O-rich organic content in protoplanetary disks.

According to previous work (cite: Walsh2014; Oberg2017), the small organic molecule formaldehyde (H$_2$CO) has the potential to be a tracer of the frozen content in dust grains since it can efficiently form on ices by the successive hydrogenation of CO, which also leads to the formation of CH$_3$OH and other COMs (cite: Watanabe2002; Chuang2017) and is more accessible to detect in the gas-phase due to lower desorption energies compared to CH$_3$OH (cite: Carney2019). Still, H$_2$CO can also be formed through gas-phase reactions (cite: Fockenberg2002; Atkinson2006), and thus, it cannot be used as a direct tracer of dust-grain chemical products if there are no constraints on the contribution from each formation pathway (cite: Loomis2015; TvS2021).

Consequently, H$_2$CO has been extensively studied in multiple protoplanetary disks, mostly around low-mass T Tauri stars. As different regions of the disk are expected to have distinct types of chemistry (cite: Oberg2021), most studies have focused on resolving the radial distribution of H$_2$CO (cite: Loomis2015; Oberg2017; Kastner2018; Podio2019; Garufi2020; Guzman2021; Booth2023). Nevertheless, the disk vertical structure also has an important role in H$_2$CO chemistry, which can be constrained by observing edge-on sources (cite: Podio2020), using geometrical methods (cite: Paneque-Carreno2023), or determining the excitation conditions by observing multiple H$_2$CO lines (cite: Pegues2020).

| Parameter | Value | Reference |
|:--:|:--:|:--:|
| Distance | $101$ pc | (cite: Gaia2018) |
| Inclination$^{\scriptsize{a}}$ | $46.7$ deg | (cite: Huang2018) |
| P.A.$^{\scriptsize{a}}$ | $133.3$ deg | (cite: Huang2018) |
| $M_{*}$ | $2.0$ $M_{\ensuremath{\odot}}$ | (cite: Teague2021) |
| $L_{*}$ | $17.0$ $L_{\ensuremath{\odot}}$ | (cite: Fairlamb2015) |
| Stellar type | A1 | (cite: Fairlamb2015) |
| $v_{\mathrm{sys}}$ | $5.8$ km s$^{-1}$ | (cite: Teague2019) |

: Stellar and disk parameters of HD 163296

Table notes: Values reproduced from (cite: Oberg2021I), where additional source properties are included. $^{\scriptsize{a}}$ The geometric parameters of the disk are derived from the dust millimeter continuum.

Moreover, H$_2$CO has two isomeric forms depending on the hydrogen nuclei spin alignment: ortho-H$_2$CO (parallel alignment) and para-H$_2$CO (antiparallel alignment). The ratio of the two isomers, known as the ortho-to-para ratio (OPR), has also been considered a possible way to discriminate between H$_2$CO formation pathways (cite: Guzman2011). However, the interpretation of derived OPRs is still a matter of discussion (cite: Guzman2018; TvS2021). Currently, the excitation conditions and the OPR of H$_2$CO have been well-resolved only for the T Tauri disk TW Hya (cite: TvS2021), thanks to the Atacama Large Millimeter/submillimeter Array (ALMA) high angular resolution observations of several ortho and para lines of H$_2$CO. Therefore, further multiple-line, spatially resolved studies of p-H$_2$CO and o-H$_2$CO are needed to gain a representative understanding of H$_2$CO chemistry in protoplanetary disks.

Due to its large size (cite: Law2021III), proximity, and high luminosity (see Table [\[table:disk-params\]](#table:disk-params)), the Herbig Ae disk HD 163296 is an ideal source for a detailed study of H$_2$CO chemistry. Currently, only two p-H$_2$CO transitions have been spatially resolved in HD 163296 (cite: Carney2017; Pegues2020; Guzman2021). Still, additional bright p-H$_2$CO and o-H$_2$CO lines can be potentially resolved (cite: Guzman2018), thus covering a broad range of excitation energies to obtain well-constrained estimates of the excitation conditions and the OPR of H$_2$CO. The disk also contains a well-defined CO snowline (cite: Qi2015) and dust millimeter edge (cite: Law2021III), which makes HD 163296 a perfect target to see how H$_2$CO chemistry works in more massive Herbig Ae/Be sources and compare it to the chemistry in the colder T Tauri, TW Hya disk.

In this work, we analyze the emission of multiple o-H$_2$CO and p-H$_2$CO transitions in HD 163296 resolved at $0\hbox{$.\!\!^{\prime\prime}$}6$ angular resolution with ALMA. We determine empirically the radial and vertical distribution of H$_2$CO, as well as its excitation conditions and OPR as a function of radius. The observations and data reduction are described in Section [2](#sec:Obs). The results on the spatial distribution, excitation conditions, and OPR are presented in Section [3](#sec:Results), while their implications in the formation of H$_2$CO in protoplanetary disks are discussed in Section [4](#sec:Discussion). The conclusions are summarized in Section [5](#sec:Conclusions).

+:--------------------------------------------:+:---------:+:-------------:+:-----------------------:+-----------:+:----------------------------:+:--------------------------------:+:------------------------------------:+
| H$_2$CO Line                                 | Baselines | Chan. Width   | Beam$^{\scriptsize{a}}$ | Beam PA    | Chan. rms$^{\scriptsize{b}}$ | Mom. Zero rms$^{\scriptsize{c}}$ | Int. Flux Density$^{\scriptsize{d}}$ |
+----------------------------------------------+-----------+---------------+-------------------------+------------+------------------------------+----------------------------------+--------------------------------------+
|                                              | \(m\)     | (km s$^{-1}$) | ($^{\prime\prime}$)     | ($^\circ$) | (mJy beam$^{-1}$)            | (mJy beam$^{-1}$ km s$^{-1}$)    | (mJy km s$^{-1}$)                    |
+----------------------------------------------+-----------+---------------+-------------------------+------------+------------------------------+----------------------------------+--------------------------------------+
| ALMA Band 3                                                                                                                                                                                                              |
+----------------------------------------------+-----------+---------------+-------------------------+------------+------------------------------+----------------------------------+--------------------------------------+
| o-H$_2$CO $6_{15}-6_{16}$$^{\scriptsize{1}}$ | $15-3638$ | $0.5$         | $0.6 \times 0.6$        | $-41.20$   | $0.70$                       | $0.38$                           | $<26$                                |
+----------------------------------------------+-----------+---------------+-------------------------+------------+------------------------------+----------------------------------+--------------------------------------+
| ALMA Band 6                                                                                                                                                                                                              |
+----------------------------------------------+-----------+---------------+-------------------------+------------+------------------------------+----------------------------------+--------------------------------------+
| p-H$_2$CO $3_{03}-2_{02}$$^{\scriptsize{1}}$ | $15-3638$ | $0.2$         | $0.6 \times 0.6$        | $47.71$    | $1.20$                       | $0.48$                           | $1011 \pm 13$                        |
+----------------------------------------------+-----------+---------------+-------------------------+------------+------------------------------+----------------------------------+--------------------------------------+
| o-H$_2$CO $3_{12}-2_{11}$$^{\scriptsize{2}}$ | $15-1039$ | $0.2$         | $0.6 \times 0.6$        | $45.21$    | $1.52$                       | $0.54$                           | $1595 \pm 13$                        |
+----------------------------------------------+-----------+---------------+-------------------------+------------+------------------------------+----------------------------------+--------------------------------------+
| ALMA Band 7                                                                                                                                                                                                              |
+----------------------------------------------+-----------+---------------+-------------------------+------------+------------------------------+----------------------------------+--------------------------------------+
| p-H$_2$CO $4_{04}-3_{03}$$^{\scriptsize{2}}$ | $9-460$   | $0.2$         | $0.6 \times 0.6$        | $-46.72$   | $2.47$                       | $0.83$                           | $1519 \pm 11$                        |
+----------------------------------------------+-----------+---------------+-------------------------+------------+------------------------------+----------------------------------+--------------------------------------+
| p-H$_2$CO $4_{23}-3_{22}$$^{\scriptsize{2}}$ | $9-460$   | $0.2$         | $0.6 \times 0.6$        | $-71.43$   | $2.51$                       | $0.79$                           | $137 \pm 11$                         |
+----------------------------------------------+-----------+---------------+-------------------------+------------+------------------------------+----------------------------------+--------------------------------------+
| p-H$_2$CO $4_{22}-3_{21}$$^{\scriptsize{2}}$ | $9-460$   | $0.2$         | $0.6 \times 0.6$        | $52.56$    | $2.61$                       | $0.84$                           | $141 \pm 11$                         |
+----------------------------------------------+-----------+---------------+-------------------------+------------+------------------------------+----------------------------------+--------------------------------------+
| o-H$_2$CO $4_{13}-3_{12}$$^{\scriptsize{2}}$ | $9-460$   | $0.2$         | $0.6 \times 0.6$        | $3.84$     | $2.53$                       | $0.81$                           | $2541 \pm 13$                        |
+----------------------------------------------+-----------+---------------+-------------------------+------------+------------------------------+----------------------------------+--------------------------------------+

: Observational parameters of formaldehyde transitions in HD 163296

Table notes: ALMA project codes: $^{\scriptsize{1}}$ 2018.1.01055.L, $^{\scriptsize{2}}$ 2016.1.00884.S $^{\scriptsize{a}}$ The robust parameter used for Briggs weighting and a UV taper, both applied in the CLEAN process, were computed independently for each transition to obtain a common circularized beam of $0\hbox{$.\!\!^{\prime\prime}$}6 \times 0\hbox{$.\!\!^{\prime\prime}$}6$ for all lines (see Appendix [6](#sec:Appendix_imaging)). $^{\scriptsize{b}}$ The channel rms is calculated using the central $50\%$ of the pixels in the first and last five channels of the data cubes. $^{\scriptsize{c}}$ The moment zero rms is defined by the bootstrapping procedure described in Section [3.2](#subsec:spatial-distrib). $^{\scriptsize{d}}$ The integrated flux density is measured within an outer radius of $4\hbox{$.\!\!^{\prime\prime}$}5$ and integrating the emission between $-1.8$ and $13.4$ km s$^{-1}$. The uncertainties do not include the $10\%$ calibration uncertainty.

# Observations

## Observational Details

We present ALMA observations of several H$_2$CO lines in Bands 3, 6, and 7 in the protoplanetary disk HD 163296[^1]. A detailed description of the Band 6 and 7 observations (project 2016.1.00884.S, PI: V.V. Guzmán) is given in (cite: Carney2019). In summary, the Band 6 observations were carried out with the 12 m array in two different configurations between 2016 November and 2017 March, whereas in the case of Band 7, the short baselines executions were observed with the Atacama Compact Array on 2016 October and the long baselines executions were done with the 12m array on 2017 April. Two different spectral setups were used: one targeting the o-H$_2$CO $J=3_{12}-2_{11}$ rotational transition centered at $225.698$ GHz (Band 6), and other targeting several p-H$_2$CO and o-H$_2$CO $J=4-3$ rotational transitions ($J=4_{04}-3_{03}$, $4_{23}-3_{22}$, $4_{22}-3_{21}$, and $4_{13}-3_{12}$) centered at $300.837$ GHz (Band 7). Transitions of other molecules were also covered within the above setups, such as CH$_3$OH (cite: Carney2019) and CN (cite: Bergner2021).

Additionally, these observations were complemented with publicly available data from the MAPS ALMA Large Program (project 2018.1.01055.L, PI: K.I. Öberg). All the observational details of these data can be found in (cite: Oberg2021I). In particular, we used the detected p-H$_2$CO $J=3_{03}-2_{02}$ rotational transition at $218.222$ GHz (Band 6) presented by (cite: Guzman2021), and the nondetected o-H$_2$CO $J=6_{15}-6_{16}$ rotational line at $101.333$ GHz (Band 3). All the transitions used in this work are summarized in Table [\[table:obs-params\]](#table:obs-params) along with their respective project codes.

![](H2CO_brightest_channelmaps.pdf)

## Data Reduction

The data reduction and posterior imaging were performed using the Common Astronomy Software Application (`CASA`)[^2] version 6.5.2.26 (cite: McMullin2007; CASA2022). The data from 2016.1.00884.S were initially processed through the standard pipeline provided by the Joint ALMA Observatory (JAO), and then self-calibrated to improve the signal-to-noise ratio following a methodology similar to that used in the DSHARP ALMA Large Program (cite: Andrews2018). Essentially, we created pseudo-continuum visibilities by flagging the line emission in the observed spectral windows, and then we aligned the different measurement sets (short and long baselines separately) into a common phase center by using the `CASA` functions `fixvis` and `fixplanets`. Afterward, the self-calibration procedure can be summarized as follows: we first applied the phase-only self-calibration to the short baseline visibilities, followed by a phase-amplitude self-calibration. Finally, we repeated the same procedures for the combined measurement sets (short + long baselines).

The different calibrations were applied to the data by using the `CASA` tasks `gaincal` and `applycal`. Depending on the band (Band 6 or 7) and the baseline length (only short baselines or combined), we applied between two and seven iterations of phase-only self-calibration using different solution interval steps (“inf," 360, 180, 60, 30, 18, and 6 s) and only one round of phase-amplitude self-calibration using a solution interval of “inf." The final solutions were then applied to the line data by restoring the flagged spectral line channels, and the continuum was subtracted using the `uvcontsub` task. In the case of the MAPS data, we downloaded from the large program webpage[^3] the measurement sets already self-calibrated and continuum-subtracted with the procedure described in (cite: Oberg2021I).

![](H2CO_maps_grid)

The calibrated visibilities were imaged through the CLEAN algorithm (cite: Hogbom1974) implemented by the `tclean` task. We used a Briggs weighting and multiscale deconvolver (cite: Cornwell2008) with scales of 0, 5, 15, and 25 pixels, where the pixel size corresponds to approximately one-seventh of the beam size. The CLEAN mask was defined using the `keplerian``_``mask` package (cite: Teague2020KepMask) to account for the Keplerian rotation of the disk, using the same stellar and disk parameters of HD 163296 as in MAPS (cite: Oberg2021I), ensuring that we covered all disk emission at different velocities. Regarding continuum images, we used the same elliptical mask as for the self-calibration procedure. Following the same cleaning strategy used in MAPS (cite: Czekala2021), we defined the robust parameter jointly with a UV taper of the visibilities in order to obtain a common circularized beam of $0\hbox{$.\!\!^{\prime\prime}$}6 \times 0\hbox{$.\!\!^{\prime\prime}$}6$ for each transition (see Table [\[table:imaging_parameters\]](#table:imaging_parameters)). The images were CLEANed up to a threshold defined as four times the estimated rms of unmasked regions, and subsequently, were corrected for the *JvM effect* (cite: JvM1995). The JvM correction is applied by the $\epsilon$ parameter, defined as the ratio between the CLEAN and the dirty beam volumes (cite: Czekala2021), whose main effect is a correct accounting of the extended source flux, but which also suppresses the point-source noise in the resulting images. Our derived $\epsilon$ values are listed in Table [\[table:imaging_parameters\]](#table:imaging_parameters), where the closer $\epsilon$ is to $1.0$, the smaller its effect.

The observational parameters of the final JvM-corrected images are summarized in Table [\[table:obs-params\]](#table:obs-params). All the final cubes have a channel width of $0.2$ km s$^{-1}$, with the exception of the Band 3 transition, whose native resolution is about $0.5$ km s$^{-1}$. The same procedures where applied then to the continuum measurement sets to obtain the dust continuum images. According to the ALMA Technical Handbook[^4], the reported flux measurements should include an absolute flux calibration uncertainty of approximately $10\%$.

# Results

## Disk-integrated Emission

Figure [1](#fig:brightest-lines) shows some representative emission channels of the brightest H$_2$CO transitions and the Keplerian mask used in this work, where we can clearly identify a disk velocity structure consistent with Keplerian rotation. Using the `integrated``_``spectrum` function from the Python package `GoFish` (cite: Teague2019GoFish), we extracted the disk-integrated spectrum within the Keplerian mask for each transition to obtain their corresponding integrated flux densities, which are listed in Table [\[table:obs-params\]](#table:obs-params). Following the same bootstrapping procedure described in detail by (cite: Bergner2018) and (cite: Pegues2020), we defined the uncertainty associated with the integrated flux density as the standard deviation of the integrated fluxes measured within 1000 off-source Keplerian masks.

![](H2CO_profiles_grid_keplerianmask.pdf)

## Spatial Distribution of H$_2$CO Emission

To analyze the spatial distribution of H$_2$CO in HD 163296, we collapse the spectral cubes into integrated intensity, or *zeroth-moment*, maps using the Python package `bettermoments`[^5]. The line emission was integrated into velocity using the same Keplerian mask for all transitions (see Figure [1](#fig:brightest-lines)). We did not apply a threshold clipping to recover accurate fluxes. As the number of selected pixels within a Keplerian mask varies with the different velocity channels, then the associated rms is not uniform across the zeroth-moment map (cite: Bergner2018; Pegues2020). Thus, we estimated the zeroth-moment rms also using a bootstrapping procedure. We created 1000 zeroth-moment maps, using the same Keplerian mask but centered at different off-source positions. Then, to compute the rms of each pixel, we took the standard deviation of these off-source zeroth-moment maps. Finally, the median value of these standard deviations is considered as the zeroth-moment rms reported in Table [\[table:obs-params\]](#table:obs-params).

Figure [2](#fig:h2co-maps) shows the gallery of zeroth-moment maps, including the dust continuum emission at $225$ and $300$ GHz with the same angular resolution for comparison. The brightest detected lines correspond to transitions with relatively low upper-state energies ($E_u < 50$ K), which are more radially extended than those with higher energies ($E_u \gtrsim 80$ K) and the dust continuum emission. The $6_{15}-6_{16}$ integrated map is not shown since there is no substantial line emission larger than $3\sigma$ neither in the channel maps nor the unmasked zeroth-moment map. Therefore, we use only the six detected transitions for the rest of the analysis.

## Radial Distribution of H$_2$CO Emission

To have a more precise characterization of the spatial distribution of the emission, we deproject the zeroth-moment maps using the `radial``_``profile` function implemented in `GoFish`. The resulting deprojected and azimuthally averaged radial intensity profiles are shown in Figure [3](#fig:deproj-profiles), where the continuum profiles are in logarithmic scales to identify the outer edge of the millimeter continuum ($R_{\mathrm{edge}}$) more clearly. We defined $R_{\mathrm{edge}}$ as the radius where the emission falls below $5\sigma$. Considering the two continuum-deprojected radial profiles, we estimated an $R_{\mathrm{edge}}$ value of $\sim$$260$ au, consistent with previous results at higher angular resolution (cite: Carney2017; Law2021III). On the other hand, the radial profiles of the emission lines are generally more extended than those of the continuum, reaching distances up to $\sim$$450$ au in the case of the four brightest transitions (i.e., $3_{03}-2_{02}$, $3_{12}-2_{11}$, $4_{04}-3_{03}$, and $4_{13}-3_{12}$).

In terms of morphology, most of the profiles replicate the more prominent radial substructures already witnessed in previous high angular resolution studies of H$_2$CO in HD 163296 (cite: Pegues2020; Guzman2021): a central depression followed by a bright peak at $\sim$$60$ au that then decreases with radius but undergoes two less prominent ring-like structures located at $\sim$$250$ au (spatially coincident with $R_{\mathrm{edge}}$) and $\sim$$380$ au. Regarding continuum morphology, a well-known set of rings and gaps has been previously characterized in the innermost $\sim$$160$ au by higher angular resolution maps (cite: Huang2018; Law2021III), which, unfortunately, are not resolved by our observations.

## H$_2$CO Excitation Conditions and OPR

Since we have multiple ortho and para transitions that cover a wide range of upper-state energies ($E_u \sim 20-80$ K), we simultaneously model the emission of each line to determine the excitation temperature, the total (ortho + para) column density, and the OPR of H$_2$CO. Using the Planck function $B_\nu$, the line intensity can be estimated from the excitation temperature, $T_{\mathrm{ex}}$, and the line optical depth, $\tau_\nu$, as follows:

$$\begin{equation}
\label{eq:I_nu}
    I_{\nu} = (B_\nu(T_{\mathrm{ex}}) - B_\nu(T_{\mathrm{bg}}))[1-e^{-\tau_\nu}],
\end{equation}$$

where $T_{\mathrm{bg}}$ is the background temperature defined as the maximum between the dust continuum brightness temperature and the cosmic microwave background (CMB) temperature ($T_{\mathrm{CMB}} = 2.73$ K).

+:---------------------:+:---------:+:-------------------:+:-------:+:------:+:-------------------:+
| H$_2$CO Line          | Frequency | $\log_{10}(A_{ul})$ | $E_u$   | $g_u$  | $n_{\mathrm{crit}}$ |
+-----------------------+-----------+---------------------+---------+--------+---------------------+
|                       | (GHz)     | (s$^{-1}$)          | \(K\)   |        | (cm$^{-3}$)         |
+-----------------------+-----------+---------------------+---------+--------+---------------------+
| ALMA Band 3                                                                                      |
+-----------------------+-----------+---------------------+---------+--------+---------------------+
| \(o\) $6_{15}-6_{16}$ | $101.333$ | $-5.80408$          | $87.56$ | $13$   | $3.93\times10^4$    |
+-----------------------+-----------+---------------------+---------+--------+---------------------+
| ALMA Band 6                                                                                      |
+-----------------------+-----------+---------------------+---------+--------+---------------------+
| \(p\) $3_{03}-2_{02}$ | $218.222$ | $-3.55037$          | $20.96$ | $7$    | $2.56\times10^6$    |
+-----------------------+-----------+---------------------+---------+--------+---------------------+
| \(o\) $3_{12}-2_{11}$ | $225.698$ | $-3.55754$          | $33.45$ | $7$    | $4.47\times10^6$    |
+-----------------------+-----------+---------------------+---------+--------+---------------------+
| ALMA Band 7                                                                                      |
+-----------------------+-----------+---------------------+---------+--------+---------------------+
| \(p\) $4_{04}-3_{03}$ | $290.623$ | $-3.16132$          | $34.90$ | $9$    | $5.75\times10^6$    |
+-----------------------+-----------+---------------------+---------+--------+---------------------+
| \(p\) $4_{23}-3_{22}$ | $291.238$ | $-3.28334$          | $82.07$ | $9$    | $1.02\times10^7$    |
+-----------------------+-----------+---------------------+---------+--------+---------------------+
| \(p\) $4_{22}-3_{21}$ | $291.948$ | $-3.28024$          | $82.12$ | $9$    | $9.37\times10^6$    |
+-----------------------+-----------+---------------------+---------+--------+---------------------+
| \(o\) $4_{13}-3_{12}$ | $300.837$ | $-3.14420$          | $47.89$ | $9$    | $8.75\times10^6$    |
+-----------------------+-----------+---------------------+---------+--------+---------------------+

: Spectroscopic constants of the observed lines

Table notes: The rest frequency and Einstein $A$ coefficient are taken from the JPL database (cite: Pickett1998), while the upper-state energy, the upper-state degeneracy, and the collisional coefficients to compute the critical densities are extracted from the Leiden Atomic and Molecular Database (cite: Schöier2005).

![](H2CO_fitted_disk-averaged_spectra_gauss.pdf)

At the velocity center of the line, $\tau_\nu$ is defined as

$$\begin{equation}
\label{eq:tau}
    \tau_0 = \frac{A_{ul}c^3 N_{u}}{8\pi\nu^3\Delta v}(e^{h\nu/kT_{\mathrm{ex}}} - 1),
\end{equation}$$

where $\nu$ is the rest frequency of the line, $A_{ul}$ is the Einstein coefficient, $\Delta v$ is the velocity line width define as the FWHM of the line profile, and $N_u$ is the column density of the molecule in the upper state of the transition. If we assume that the line emission occurs under local thermodynamic equilibrium (LTE), then

$$\begin{equation}
\label{eq:Boltzmann-eq}
    N_u = \frac{N_{\mathrm{T}}}{Q(T_{\mathrm{ex}})}g_u e^{-E_u/kT_{\mathrm{ex}}},
\end{equation}$$

where $N_{\mathrm{T}}$ is the total column density, $Q$ is the partition function of H$_2$CO, and $E_u$ with $g_u$ are the energy and the degeneracy associated to the upper-state level of each transition, respectively (see Table [\[table:spec-constants\]](#table:spec-constants)). This should be a reasonable assumption for HD 163296 since the critical densities of the observed transitions ($n_{\mathrm{crit}} \lesssim 10^{7}$ cm$^{-3}$, see Table [\[table:spec-constants\]](#table:spec-constants)) are lower than the typical gas densities estimated by models (cite: Qi2011; Zhang2021) at those vertical heights where we expect to find H$_2$CO (cite: Paneque-Carreno2023). In that sense, the excitation temperature can be used as a direct tracer of the kinetic gas temperature in those disk layers where H$_2$CO is emitting.

![](H2CO_fitted_radial_spectra.pdf)

We defined separate partition functions for the ortho and para isomers. Using the same convention adopted by (cite: TvS2021), we defined

$$\begin{eqnarray}
\label{eq:Qortho}
    Q(T_{\mathrm{rot}})^{\mathrm{ortho}} & = & \sum_i^{\mathrm{ortho}} g_i e^{-E_i/kT_{\mathrm{rot}}}, \: \text{and}\\
\label{eq:Qpara}
    Q(T_{\mathrm{rot}})^{\mathrm{para}} & = & \sum_i^{\mathrm{para}} g_i e^{-E_i/kT_{\mathrm{rot}}},
\end{eqnarray}$$

where $g_i$ and $E_i$ are the upper-state degeneracy and energy of a state. The sum in Equations ([\[eq:Qortho\]](#eq:Qortho)) and ([\[eq:Qpara\]](#eq:Qpara)) is performed over the rotational ground states of a specific isomer (ortho or para) taken from the ExoMol database (cite: Al-Refaie2015; Wang2020) but using state degeneracies consistent with the ones from LAMDA (cite: Schöier2005) since the former assumes an OPR of $3.0$ (cite: TvS2021).

By putting Equations ([\[eq:tau\]](#eq:tau)) and ([\[eq:Boltzmann-eq\]](#eq:Boltzmann-eq)) into Equation ([\[eq:I_nu\]](#eq:I_nu)), and assuming a Gaussian line profile centered at $v_{\mathrm{sys}}=5.8$ km s$^{-1}$ (cite: Teague2019) with a certain $\Delta v$, we can model the line intensity as a function of $T_{\mathrm{ex}}$ and $N_{\mathrm{T}}$. As we have different partition functions, and $T_\mathrm{rot}^{\mathrm{ortho}}$ is not necessarily equal to $T_\mathrm{rot}^{\mathrm{para}}$, we could in principle do a separate line modeling for each isomer and then obtain the ortho-to-para ratio $\mathrm{OPR} = N_{\mathrm{T}}^{\mathrm{ortho}}/N_{\mathrm{T}}^{\mathrm{para}}$. However, in this work, we assume the same excitation temperature since we detected only two o-H$_2$CO lines. Hence, we fitted simultaneously the detected ortho and para transitions using the following relations:

$$\begin{eqnarray}
    N_{\mathrm{T}}^{\mathrm{ortho}} = \frac{N_{\mathrm{T}}\times\mathrm{OPR}}{1+\mathrm{OPR}}, \: \text{and}\: N_{\mathrm{T}}^{\mathrm{para}} = \frac{N_{\mathrm{T}}}{1+\mathrm{OPR}},
\end{eqnarray}$$

where $N_{\mathrm{T}} = N_{\mathrm{T}}^{\mathrm{ortho}} + N_{\mathrm{T}}^{\mathrm{para}}$ is the total column density of H$_2$CO considering both isomers. Thus, the free parameters to fit are $N_{\mathrm{T}}$, $T_\mathrm{rot}$, $\mathrm{OPR}$, and $\Delta v$. To fit the excitation conditions and the line width, we construct a likelihood function from Equation ([\[eq:I_nu\]](#eq:I_nu)) and use the `emcee` package (cite: Foreman-Mackey2013) to explore the parameter space and get the posterior probability distributions.

### Disk-averaged Analysis

We first model the line emission averaged over the full radial extent of H$_2$CO ($\sim$$450$ au) in order to derive the disk-averaged excitation conditions. To account for the velocity structure of the disk, we used the `average``_``spectrum` function from `GoFish`, which corrects the spectrum for Keplerian rotation before averaging by using the stellar mass and the distance to the disk. For simplicity, we assume that the emitting layer is in the midplane ($z/r = 0$), which should be reasonable based on the estimates of the vertical height of H$_2$CO in HD 163296 (see Section [3.5](#subsec:vertical-distrib) for further details). The retrieved disk-averaged spectra are shown in Figure [4](#fig:fitted_disk-averaged_spectra), where the best-fit Gaussian models are overlaid with different colors for each H$_2$CO isomer. The best-fit excitation conditions and their corresponding uncertainties are deduced from the 16th, 50th, and 84th percentiles of the posterior distributions, whose results are $N_{\mathrm{T}} = 3.89_{-0.18}^{+0.18} \times 10^{12}$ cm$^{-2}$, $T_{\mathrm{ex}} = 19.42_{-1.51}^{+1.59}$ K, and $\mathrm{OPR} = 2.70_{-0.19}^{+0.20}$ for a Gaussian line width of $\Delta v = 0.80_{-0.03}^{+0.03}$ km s$^{-1}$. The disk-averaged line optical depths are between $\tau_\nu = 0.003$ and $0.074$, verifying an optically thin regime. We also checked that these excitation conditions are consistent with the nondetection of the $6_{15}-6_{16}$ line, as its predicted line intensity is lower than the sensitivity of the observations.

As shown in Figure [4](#fig:fitted_disk-averaged_spectra), the LTE predictions underestimate the disk-averaged emission from the line wings, indicating that the line profiles are probably more Lorentzian than pure Gaussian. Consequently, we performed the same analysis but using a Voigt profile. We find an improvement in the fit quality for the line wings, and recover slightly higher values for $N_{\mathrm{T}}$ and the OPR, although consistent with the results from the Gaussian fitting when considering the uncertainties (see Appendix [7](#sec:Appendix_voigt)). A similar line profile behavior was found in TW Hya using $^{12}$CO $J=3-2$ line observations, that were attributed to pressure broadening (cite: Yoshida2022). Our H$_2$CO results may hint at something similar, but further analysis is needed to investigate the origin of the non-Gaussian profiles in HD 163296.

Previous efforts have been made to constrain the distribution of H$_2$CO across HD 163296. For the disk-integrated column density, (cite: Carney2019) estimated a value of about $N_{\mathrm{T}} = 2.1 \times 10^{12}$ cm$^{-2}$, which is lower by a factor of $\sim$$2$ than our derived value. However, it is still consistent, considering that they assumed a higher excitation temperature of $T_{\mathrm{ex}} = 25$ K. Moreover, to compute the total column density, they used integrated flux measurements of a single line from Submillimeter Array (SMA) observations with lower angular resolution (cite: Qi2013). Thus, the differences between the disk-averaged $N_{\mathrm{T}}$ estimates could be due to choosing a different area of integration, or filtering out more extended emission (either in ALMA or the SMA).

Regarding the excitation temperature, (cite: Carney2017) estimated a lower limit of $>$$20$ K on the kinetic temperature using three p-H$_2$CO $J=3-2$ rotational transitions. Nevertheless, as they did not have higher energy transitions (e.g., $J=4-3$), and their two weakest lines were detected only through a matched filter analysis (cite: Loomis2018matchedfilter), the temperature estimation was uncertain. Later, a similar result was found by (cite: Guzman2018), where a rotational temperature of $T_{\mathrm{rot}} = 24.3 \pm 13.5$ K was obtained using three o-H$_2$CO transitions with lower angular resolution SMA data, consistent with our results considering the uncertainties.

In the case of the ortho-to-para ratio, the only known determination for HD 163296 was also made by (cite: Guzman2018), who complemented the three o-H$_2$CO transitions mentioned above with three p-H$_2$CO transitions and estimated an ortho-to-para ratio between $\mathrm{OPR} = 1.8$ and $2.8$, depending on the vertical height of the emission. This range of values agrees with our OPR determination. However, since the derived uncertainties are purely statistical and do not consider the assumptions mentioned in Section [3.4](#subsec:excitation-conditions), we cannot rule out a disk-averaged OPR value consistent with $3.0$ in HD 163296 (see Section [4.2.3](#subsubsec:OPR)).

### Radially Resolved Analysis

![](H2CO_excitation-conditions.pdf)

Since we can resolve the variation of the H$_2$CO emission with the disk radius (see Figure [3](#fig:deproj-profiles)), we repeat the same line fitting procedure but use the deprojected radial spectra instead of the disk-averaged one to derive the excitation conditions as a function of radius. Using `GoFish`, we applied the `radial``_``spectra` function to deproject the spectra into different radial bins. Similarly to the disk-averaged case, the emission is shifted and stacked according to the Keplerian motion. However, it is now azimuthally averaged over different radial annuli whose width corresponds to one-quarter of the beam’s major axis. In this case, we construct a likelihood function for each radial bin to determine the best-fit models at different radii, as shown in Figure [5](#fig:fitted_radial_spectra).

Figure [6](#fig:excitation-conds) shows the resulting deprojected radial profiles of the excitation conditions and the disk-averaged values for comparison, whereas $\tau_{\nu}$ radial profiles are shown in Appendix [8](#sec:Appendix_tauprofiles). In general, the mean values of each profile are compatible with the disk-averaged results, and we confirmed that the emission is optically thin throughout the disk (see Figure [9](#fig:tau_profiles)). The derived $N_{\mathrm{T}}$ profile behaves similarly to those from previous studies where the emission of H$_2$CO was resolved in HD 163296 (cite: Pegues2020; Guzman2021). Total column density values range from $\sim 2.0 \times 10^{13} - 1.3\times 10^{12}$ cm$^{-2}$ within a radius of $\sim450$ au, displaying two remarkable features: a central gap followed by a global peak close to the CO snowline located at $75$ au (cite: Qi2015) and a secondary ring or plateau near $R_{\mathrm{edge}}\sim 260$ au, as defined by our continuum observations.

Regarding the excitation temperature, this is the first time it has been resolved for H$_2$CO in HD 163296 since, previously, it was computed through a disk-averaged analysis (cite: Carney2017; Guzman2018) or assumed uniform across the disk (cite: Pegues2020; Guzman2021) either due to a lack of sufficient angular resolution or multiple-line observations. We find that the $T_{\mathrm{ex}}$ profile decreases smoothly from $50$ to $10$ K, where a temperature of $\sim$$30$ K is reached close to CO snowline and $\sim$$20$ K at $R_{\mathrm{edge}}$.

On the other hand, the ortho-to-para ratio profile is relatively constant across the disk, mostly centered at $\mathrm{OPR}\sim 2.7$ but with uncertainties that remain compatible with the statistically expected value of $\mathrm{OPR}=3.0$. Nevertheless, the profile exhibits small modulations that are apparently consistent with some of the H$_2$CO radial substructures witnessed by (cite: Law2021III) that are spatially resolved by our observations, which could be linked with changes in the chemistry.

## Vertical Height of the Emission

Although the radial distribution of the excitation conditions gives us valuable clues about the formation of H$_2$CO in protoplanetary disks, the latter has a three-dimensional structure where the vertical distribution of the emission is also an essential factor to having a complete understanding of the contribution of the different formation pathways. To complement our radially resolved analysis, we used the Python package `ALFAHOR`[^6] to constrain empirically the vertical height of H$_2$CO in HD 163296 from the observations (cite: Paneque-Carreno2023).

By having the stellar and geometrical properties of the disk, `ALFAHOR` computes a vertical profile based on a geometrical method (cite: Pinte2018) that relies on the location of the emission maxima inside a user-defined mask for each channel (cite: Paneque-Carreno2023). Using the stellar and disk parameters from Table [\[table:disk-params\]](#table:disk-params), and masking manually the channel emission for each H$_2$CO transition, we derived the vertical profiles shown in Figure [7](#fig:vertical_height). Since this empirical method requires an appropriate combination of angular resolution and signal-to-noise ratio to distinguish the near and far *wings* of the channel emission (cite: Paneque-Carreno2023), we applied this analysis only to the four brightest transitions in our sample.

H$_2$CO is apparently tracing an emission surface close to $z/r \sim 0.1$. Still, as the lines used in this work have $\tau_\nu \ll 1$, we cannot discard the presence of H$_2$CO at higher disk layers since optically thin emission makes it challenging to isolate surfaces due to back- and front-side confusion across the disk. Thus, the determined value should be interpreted as a lower limit. We did not notice remarkable differences in the height predicted from different lines, which agrees with the LTE assumption where all transitions have the same excitation temperature since the disk gas temperature changes with the radius and the height. Similar to the integrated intensities (see Figure [3](#fig:deproj-profiles)), the vertical profiles present radial modulations, as previously reported by (cite: Paneque-Carreno2023), where the lowest heights are spatially coincident with the H$_2$CO rings. This suggests that the structures seen from the radial profiles are likely related to changes in the H$_2$CO chemistry, which could be related to the slight radial variations of the OPR (see Section [4.2](#subsec:H2CO_HD163296) for further discussion).

# Discussion

## The chemistry of H$_2$CO in Protoplanetary Disks

The reliability of H$_2$CO as a tracer of the icy O reservoir in protoplanetary disks will depend on its dominant formation pathway since, at typical disk conditions, it could be formed by gas-phase and grain-surface chemistry (cite: Walsh2014). According to laboratory experiments (cite: Fockenberg2002; Atkinson2006) and chemical modeling (cite: vanderMarel2014; Loomis2015), H$_2$CO is formed efficiently in the gas phase at low temperatures ($<$$100$ K) by the following neutral-neutral reaction:

$$\begin{equation}
    \mathrm{CH}_3 + \mathrm{O} \rightarrow \mathrm{H}_2\mathrm{CO} + \mathrm{H},
\end{equation}$$

which is expected to dominate in warm environments such as the inner disk (cite: Loomis2015; Oberg2017) or surface layers away from the midplane at relatively large normalized heights (cite: TvS2021).

On the other hand, in those cold regions where most of the O-containing carriers are frozen, H$_2$CO and other more complex species (e.g., CH$_3$OH) are expected to form by the successive hydrogenation of CO on dust grains (cite: Watanabe2002; Fuchs2009):

$$\begin{equation}
\label{eq:CO-hydrogenation}
    \mathrm{CO} \xrightarrow{\mathrm{H}} \mathrm{HCO} \xrightarrow{\mathrm{H}} \mathrm{H}_2\mathrm{CO} \xrightarrow{\mathrm{H}} \mathrm{H}_2\mathrm{COH} \xrightarrow{\mathrm{H}}\mathrm{CH}_3\mathrm{OH},
\end{equation}$$

which should be relevant in the vicinity and inside the regions with abundant CO ices, delimited by the CO snowline and the CO snow surface (cite: Oberg2017; Guzman2021). Since thermal desorption of H$_2$CO occurs at warmer conditions than the CO freeze-out temperature (cite: Pegues2020; TvS2021), nonthermal processes are required to desorb the grain-surface H$_2$CO into the gas-phase.

Based on the above, the key takeaway from previous works is that probably a combination of gas-phase and grain-surface formation pathways is needed to explain the emission morphologies deduced from H$_2$CO observations (cite: Pegues2020; Guzman2021), which is supported by predictions from chemical models that include both kinds of chemistry (cite: Loomis2015; Oberg2017) but also by empirical measurements of vertical stratification in disks (cite: Podio2020; Paneque-Carreno2023). Still, most previous studies lack multiple transitions and different isomer observations, and therefore, the excitation conditions with the OPR, which are directly related to H$_2$CO formation, are barely constrained.

In fact, there are only two disks where the above quantities are now well-resolved. (cite: TvS2021) recently resolved the excitation conditions and the OPR of H$_2$CO in the protoplanetary disk around TW Hya. They found that H$_2$CO emits from a relatively warm ($30-40$ K) layer, and a decreasing OPR with radius, going from values consistent with 3 within 60 au (which corresponds to the extent of the pebble disk) and values of 2 beyond this radius. The relatively uniform excitation conditions and OPR gradient suggest a single gas-phase formation pathway dominates the formation of H$_2$CO across the TW Hya disk, although a contribution from grain-surface chemistry cannot be completely ruled out (cite: TvS2021). The other case is HD 163296, with the observations presented in this work.

![](H2CO_vertical_height.pdf)

## Constraints on H$_2$CO Formation in HD 163296

### Radial Distribution of H$_2$CO

From Figure [6](#fig:excitation-conds), we deduce a clear correlation between the substructures of the $N_{\mathrm{T}}$ profile with the CO snowline and $R_{\mathrm{edge}}$, which is likely connected with changes in the chemistry. The same spatial coincidence observed in previous work of H$_2$CO toward HD 163296 (cite: Carney2017; Guzman2021) and other disks (cite: Oberg2017; Kastner2018; Pegues2020) has been interpreted as an indicator of active H$_2$CO grain-surface production. Nevertheless, although less efficient at larger radii, the contribution from the gas-phase formation route may not be negligible.

Despite warm temperatures ($T_{\mathrm{ex}} \gtrsim 30$ K, see middle panel in Figure [6](#fig:excitation-conds)), there is a substantial amount of H$_2$CO in the inner disk ($\lesssim$$100-150$ au). Particularly, within the CO snowline, we would not expect to have the formation of abundant CO ices that could form H$_2$CO on dust grains. This warm H$_2$CO component is generally ascribed to warm gas-phase formation (cite: Loomis2015; Oberg2017), but this could be complemented by an inward drift of ices with H$_2$CO already formed at slightly larger radii (cite: Pegues2020).

In the outer disk ($\gtrsim$$150$ au), CO is expected to be abundant on ices, and therefore, the reaction represented by Equation [\[eq:CO-hydrogenation\]](#eq:CO-hydrogenation) could become more efficient. In addition, the shielding from UV radiation is expected to decrease toward the outskirts of the disk, as suggested by previous DCO$^{+}$ observations toward HD 163296 with a similar radial distribution (cite: Salinas2017; Salinas2018). Thus, the photodesorption of H$_2$CO (cite: Carney2017; Oberg2017) and some CO (cite: Oberg2015b; Huang2016) from grains could increase, which could explain the bump of $N_{\mathrm{T}}$ observed close to $R_{\mathrm{edge}}$. However, the above can also be associated with an enhancement in the production of radicals and atomic O due to the photodissociation of CO in the upper layers, which would favor the gas-phase formation of H$_2$CO in the outer disk (cite: Carney2017).

Regarding the central depression in the integrated emission, although it is apparently correlated to a decrease in the column density, the results should be treated with caution as we are on a region that cannot be resolved with the current angular resolution, and the quality of the fit is not as good. Alternative explanations are the presence of optically thick dust (cite: Carney2017) or the use of lines with low upper-state energies that do not trace the warmer gas in the inner disk (cite: Guzman2021). Since the lines detected in this work with high $E_u$ values also show an inner hole, as well as CO isotopologues (cite: Law2021III), the scenario of a drop in the emission due to an optically thick continuum seems more likely.

In contrast to the $N_\mathrm{T}$ and OPR profiles, $T_{\mathrm{ex}}$ does not present significant radial substructures, which could imply the dominance of a single formation mechanism throughout the disk, similar to was found in TW Hya (cite: TvS2021). However, the temperature gradient in the inner disk is steeper than in the outer disk, rapidly decreasing from $\sim$$50$ K to values around the disk-averaged $T_{\mathrm{ex}} \sim 20$ K, and then decreasing gently at larger radii. This distinction could support the previously suggested two-component H$_2$CO model, with a warm inner region with predominant gas-phase formation and a cold component beyond the CO snowline with contribution from both formation pathways (cite: Loomis2015; Carney2017; Oberg2017; Pegues2020).

(cite: Qi2015) estimated a CO freeze-out midplane temperature of $\sim$$25$ K for HD 163296, which is a bit smaller than our derived value of $T_{\mathrm{ex}} \sim 30$ K at $\sim$$75$ au (the location of the CO snowline). Instead, typical CO freeze-out temperatures (cite: Oberg2015b; Qi2015; Pinte2018) are reached in the outer disk, close to $R_{\mathrm{edge}}$, where we expect to have more H$_2$CO from dust grains. The above is a consequence that disk temperature depends on the radius and the vertical height. Thus, even if the H$_2$CO emission comes from a radius outside the CO snowline, this same emission may have originated in a region where CO is not frozen out, emphasizing the importance of complementing our radial analysis with constraints on the vertical height.

### Vertical Distribution of H$_2$CO

We complemented our radial temperature measurements with the vertical distribution of the emission obtained with `ALFAHOR`, as shown in Figure [7](#fig:vertical_height). For consistency, we compared our vertical and radial constraints with predictions of the temperature structure in HD 163296 (see background maps in Figure [7](#fig:vertical_height)). For the inner disk, $T_{\mathrm{ex}}$ values are more consistent with the empirical temperature structure (see left panel in Figure [7](#fig:vertical_height)), while in the outer disk, $T_{\mathrm{ex}}$ resembles that predicted from thermochemical models (see right panel in Figure [7](#fig:vertical_height)). These disparities align with the fact that thermochemical models can underpredict the temperature deduced from observations in the inner disk because they do not include mechanisms like accretion heating or CO depletion (cite: Zhang2021). Moreover, in the outer disk, temperature predictions from CO observations could be more uncertain as the emission from optically thin CO isotopologues is less extended (cite: Law2021IV).

Empirical measurements of the vertical height and predictions of the temperature structure agree that H$_2$CO is mostly tracing a cold region relatively close to the midplane ($z/r \gtrsim 0.1$). The intersection of the CO snow surface ($T_{\mathrm{kin}} = 25$ K) with the $z/r = 0.1$ surface is expected at $100-150$ au, depending on the assumed temperature structure (see dash-dotted lines in Figure [7](#fig:vertical_height)). This spatial feature is consistent with our delineation of the inner and outer disk, based on the column density profile, and could explain why the gas temperature traced by H$_2$CO has different behavior in these two regions, supporting different H$_2$CO formation pathways.

Interestingly, the four analyzed transitions present modulations on the computed vertical height at similar positions as the integrated line intensity. (cite: Paneque-Carreno2023) resolved a similar structure in HD 163296 using the $3_{03}-2_{02}$ line but with higher angular resolution. They discarded the possibility of an effect of the line emission morphology in determining the vertical structure, linking it to actual changes in the vertical location of the H$_2$CO emitting region. The association of the local minimum heights with H$_2$CO emission rings (at $230$ and $378$ au, see Figure [6](#fig:excitation-conds)) could be related to an increased penetration of UV photons in the outer disk that would enhance the formation of H$_2$CO. Actually, vertical heights predicted in this work are near those layers with active photochemistry traced by HCN and C$_2$H (cite: Law2021IV; Paneque-Carreno2023). Still, the above would be consistent with the grain-surface chemistry (photodesorption of H$_2$CO), but also the cold gas-phase chemistry due to increased production of radicals.

### Ortho-to-para Ratio of H$_2$CO

The OPR has been proposed as an indicator of the conditions under which H$_2$CO is formed, based on its relation with the spin temperature (cite: Guzman2018). Owing to the large timescales involved in the ortho-para nuclear-spin conversion by nonreactive collisions in the gas phase, $T_{\mathrm{spin}}$ is expected to resemble the formation temperature of H$_2$CO (cite: Tudorie2006). According to the Boltzmann distribution, higher OPR values are associated with higher spin temperatures (cite: Guzman2018). Hence, a statistical value of $3.0$ was initially expected for the gas-phase chemistry, while lower values were thought to result when H$_2$CO forms on the surface of dust grains (cite: Kahane1984; Guzman2011). Nevertheless, the latter began to be questioned by laboratory experiments where water desorption from ice resulted in an OPR consistent with $3.0$ (cite: Hama2016; Hama2018). Recent results suggest that the same behavior could occur for H$_2$CO desorption (cite: Yocum2023), and previous work has discussed the possibility of low OPR values being associated with a cold gas-phase formation from radicals produced at low temperatures (cite: Guzman2018; TvS2021). It is, therefore, unclear how OPRs are related to the formation pathways of molecules.

From our disk-averaged and resolved analysis, we derived a relatively constant value of OPR$\sim2.7$ across the disk, which could still be consistent with 3.0, considering the uncertainties. Similar to the integrated intensity and the vertical height, the OPR seems to have some radial modulations that could be related to changes in the chemistry[^7]. The lowest OPR values are found close to the H$_2$CO rings and at lower disk altitudes; thus, they are likely associated with a rise in UV penetration as well. We also extracted the $T_{\mathrm{spin}}$ radial profile from the resolved OPR values (see Fig. [10](#fig:Tspin_profile)), and found a coincidence between $T_{\mathrm{spin}}$ and $T_{\mathrm{ex}}$ values, mainly in the outer disk, which could indicate that the formation temperature of H$_2$CO is preserved. However, laboratory experiments have shown that $T_{\mathrm{spin}}$ does not correspond to the ice formation temperature when H$_2$CO is formed on ices by the UV photolysis of CH$_3$OH (cite: Yocum2023). Still, it is also possible that $T_{\mathrm{spin}}$ could reflect the formation temperature if H$_2$CO forms more quiescently through the hydrogenation of CO ices.

Therefore, our results are consistent with both the cold gas-phase and grain-surface formation scenarios in HD 163296. Indeed, more in-depth studies of dust-grain-related processes are needed to discern if grain-surface chemistry is critical for H$_2$CO formation in HD 163296, as well as its role in setting the OPR value. Since gas-phase products may also contribute to the formation of H$_2$CO on grains (cite: TvS2021), chemical models considering both mechanisms are an alternative but, unfortunately, the physical parameters involved in grain-surface chemistry are poorly constrained (cite: Guzman2013). Modeling only gas-phase chemistry (cite: Loomis2015; Loomis2018) could be a more straightforward approach, but it is beyond the scope of this work.

## H$_2$CO in T Tauri versus Herbig Ae/Be disks

Thanks to ALMA, H$_2$CO has been currently resolved in $\sim$20 protoplanetary disks (cite: Pegues2020; TvS2021). From this sample, only five correspond to Herbig Ae/Be disks: the cold disks HD 163296 (this work) and MWC 480 (cite: Pegues2020; Guzman2021), and the warm disks IRS 48 (cite: vanderMarel2021; Booth2024II), HD 100546 (cite: Booth2021; Booth2024I), and HD 169142 (cite: Booth2023).

MWC 480 has similar $N_{\mathrm{T}}$ and $T_{\mathrm{ex}}$ values to HD 163296, while higher $T_{\mathrm{ex}}$ values and radial substructures of $N_{\mathrm{T}}$ correlated with the dust continuum characterize IRS 48, HD 100546, and HD 169142. These differences reflect how H$_2$CO chemistry acts under different physical conditions since, typically, warm Herbig Ae/Be disks are characterized by dust cavities, which prevent the in situ formation of CO ices, and by the presence of CH$_3$OH detections (cite: Booth2023; Booth2024II; Booth2024I). In these cases, H$_2$CO formation is probably dominated by warm gas-phase chemistry and/or thermal desorption from inherited ices, as suggested by the low OPR of $1.2$ deduced in IRS 48 (cite: vanderMarel2021).

Instead, the morphology of $N_{\mathrm{T}}$ and the disk-averaged $T_{\mathrm{ex}}$ of H$_2$CO in cold Herbig Ae/Be disks are more similar to those observed in T Tauri disks (cite: Pegues2020). Still, the $N_{\mathrm{T}}$ values of cold Herbig Ae/Be disks are systematically lower than those of T Tauri disks, which has been explained as a consequence of the higher temperatures expected around more massive stars that limit the CO freeze-out (cite: Pegues2020), in line with the two-component H$_2$CO model discussed in Section [4.2.2](#subsubsec:Vertical_distrib). To verify this possibility of similar chemistry, we can analyze the radial behavior of the OPR, where the only comparison that can be made is with the T Tauri disk TW Hya. Interestingly, unlike the relatively constant OPR observed in HD 163296, the OPR profile of TW Hya has an apparent decreasing behavior (cite: TvS2021), thus suggesting a different formation process. Further experiments of the OPR in H$_2$CO ices and more determinations of the OPR around both T Tauri and Herbig Ae/Be protoplanetary disks are needed to confirm this scenario.

TW Hya is a relatively peculiar source. It is relatively old compared to other T Tauri stars, and it is the only T Tauri disk with known detections of CH$_3$OH (cite: Walsh2016). Also, in terms of H$_2$CO, it has a relatively high and nearly constant excitation temperature ($T_{\mathrm{ex}} \sim 30 - 40$ K) and a different column density morphology (no rings in the outer disk), in comparison with other T Tauri disks and HD 163296. Moreover, constraints on the vertical structure have placed the emitting surface of H$_2$CO in TW Hya at higher heights (cite: Oberg2017; TvS2021) than in other disks with empirical determinations (cite: Paneque-Carreno2023). These differences align with the fact that TW Hya is one of the few disks where H$_2$CO is proposed to be predominantly formed by gas phase rather than a combination of both formation pathways (cite: TvS2021). Observations toward other disks are needed to better understand the dominant formation pathway of H$_2$CO.

Curiously, even though it has no efficient gas-phase formation pathways, CH$_3$OH is relatively abundant in TW Hya (CH$_3$OH/H$_2$CO $=1.27$) but not so in HD 163296 (CH$_3$OH/H$_2$CO $< 0.24$), according to the upper limits derived by (cite: Carney2019). One possibility to address this counterintuitive behavior could be a difference in the UV radiation field. UV photons can photodesorb intact CH$_3$OH from ices, but also photofragments of H$_2$CO (cite: Guzman2013; Bertin2016; Yocum2023). Because massive Herbig Ae/Be disks have stronger UV fluxes than T Tauri disks (cite: Walsh2015), maybe CH$_3$OH tends to be more fragmented for sources like HD 163296, thus contributing to H$_2$CO emission instead of the gas-phase CH$_3$OH, as supposed in TW Hya.

Furthermore, laboratory experiments have demonstrated that X-ray photodesorption is also an efficient mechanism to release CH$_3$OH into the gas phase, even more than UV photodesorption (cite: Basalgete2021I; Basalgete2021II). The above could also contribute to differences in the CH$_3$OH/H$_2$CO ratio since T Tauri sources have larger X-ray luminosities than Herbig Ae/Be (cite: Ryspaeva2023), and therefore, the X-ray-induced chemistry is predicted to be more significant (cite: Walsh2015). More complementary detections of H$_2$CO and upper limits for CH$_3$OH (if not detected) in protoplanetary disks are needed to clarify this behavior.

# Conclusions

We have presented the analysis of multiple spectrally and spatially resolved transitions for the para and ortho isomers of H$_2$CO toward the Herbig Ae disk around HD 163296. The main conclusions can be summarized as follows:

1.  The line emission, extended up to $\sim$$450$ au, is characterized by the presence of a central depression and a global peak at $\sim$$60$ au in the inner disk, whereas in the outer disk, two ring-like structures are located at $\sim$$250$ and $\sim$$380$ au.

2.  According to LTE predictions, we determine the column density of H$_2$CO as a function of disk radius, and for the first time, we resolve the excitation temperature and the ortho-to-para ratio of H$_2$CO in HD 163296.

3.  The column density values range from $\sim 2.0\times 10^{13}$ to $\sim 1.3\times 10^{12}$ cm$^{-2}$, showing a peak in the inner disk and a plateau in the outer disk, likely related to the positions of the CO snowline and the dust millimeter edge, respectively.

4.  The excitation temperature, which is expected to trace the temperature of the emitting gas, decreases smoothly from $\sim$$50$ to $\sim$$10$ K throughout the disk. Still, the slope of the profile in the inner disk is steeper than in the outer disk.

5.  The temperature profile was complemented with empirical measurements of the vertical height of H$_2$CO emission. By comparing with predictions of the temperature structure in HD 163296, we find that H$_2$CO is tracing a cold region near the midplane ($z/r \gtrsim 0.1$).

6.  An ortho-to-para ratio close to 2.7 remains relatively constant across the disk, which is still consistent with the statistical value of 3.0, considering the uncertainties. However, the OPR profile presents radial modulations, where the lowest OPR values are coincident with H$_2$CO emission rings and lower vertical heights.

7.  Constraints from the excitation conditions and the ortho-to-para ratio are consistent with the formation of H$_2$CO by both gas-phase and by grain-surface chemistry, especially in the outer disk, where there is an apparent increase in the UV penetration that would favor the photodesorption of H$_2$CO from dust grains, but also the formation of radicals due to CO photodissociation.

8.  Our results suggest that the formation of H$_2$CO in relatively cold Herbig Ae/Be disks (e.g., HD 163296 and MWC 480) is different from that in their warmer analogs characterized by dust cavities and CH$_3$OH detections (e.g., IRS 48, HD 100546, and HD 169142). In contrast, the morphology of $N_\mathrm{T}$ and the disk-averaged $T_{\mathrm{ex}}$ of H$_2$CO in HD 163296 shares similarities with the results in T Tauri disks.

9.  Regarding the OPR, the only source where a comparison can be made is TW Hya, a T Tauri disk where H$_2$CO is thought to be predominantly formed by gas-phase chemistry. Although the OPR values are consistent with $3.0$ in the inner disk of both sources, TW Hya exhibits a monotonic decrease at the outer radius that is not seen for HD 163296, suggesting differences in the chemistry. Dissimilarities in the column density and excitation temperature profiles also support the above. Further multiple-line observations toward more T Tauri and Herbig Ae/Be sources are needed to disentangle the dominant formation pathway of H$_2$CO in protoplanetary disks.

# Acknowledgments

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00884.S and ADS/JAO.ALMA#2018.1.01055.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

We thank the anonymous reviewer for providing useful comments and suggestions. C.H.-V. acknowledges support from the National Agency for Research and Development (ANID) – Scholarship Program through the Doctorado Nacional grant No. 2021-21212409. V.V.G gratefully acknowledges support from FONDECYT Regular 1221352, and ANID CATA-BASAL project FB210003. L.I.C. acknowledges support from NASA ATP 80NSSC20K0529. L.I.C. also acknowledges support from NSF grant no. AST-2205698, the David and Lucille Packard Foundation, and the Research Corporation for Scientific Advancement Cottrell Scholar Award.

# Software

`ALFAHOR` (cite: Paneque-Carreno2023), Astropy (cite: Astropy2013; Astropy2018; Astropy2022), `bettermoments` (cite: Teague2018bettermoments), `CASA` (cite: McMullin2007; CASA2022), `emcee` (cite: Foreman-Mackey2013), `GoFish` (cite: Teague2019GoFish), Matplotlib (cite: Hunter2007), NumPy (cite: vanderWalt2011), SciPy (cite: Virtanen2020).

# Observational details

Table [\[table:imaging_parameters\]](#table:imaging_parameters) summarizes the imaging parameters to obtain a common circularized beam of $0\hbox{$.\!\!^{\prime\prime}$}6 \times 0\hbox{$.\!\!^{\prime\prime}$}6$ for all transitions used in this work and the $\epsilon$ parameter to account for the *JvM effect*.

+:-------------------------:+:------:+:----------------------------:+:--------------:+
| H$_2$CO Line              | Robust | UV taper                     | JvM $\epsilon$ |
+---------------------------+--------+------------------------------+----------------+
|                           |        | ($^{\prime\prime}$)          |                |
+---------------------------+--------+------------------------------+----------------+
| ALMA band 3                                                                        |
+---------------------------+--------+------------------------------+----------------+
| o-H$_2$CO $6_{15}-6_{16}$ | $0.5$  | $0.556 \times 0.433, -2.287$ | $0.80$         |
+---------------------------+--------+------------------------------+----------------+
| ALMA band 6                                                                        |
+---------------------------+--------+------------------------------+----------------+
| p-H$_2$CO $3_{03}-2_{02}$ | $0.5$  | $0.520 \times 0.571, 71.583$ | $0.92$         |
+---------------------------+--------+------------------------------+----------------+
| o-H$_2$CO $3_{12}-2_{11}$ | $0.5$  | $0.146 \times 0.417, 79.759$ | $0.59$         |
+---------------------------+--------+------------------------------+----------------+
| ALMA band 7                                                                        |
+---------------------------+--------+------------------------------+----------------+
| p-H$_2$CO $4_{04}-3_{03}$ | $0.0$  | $0.167 \times 0.476, 80.301$ | $0.98$         |
+---------------------------+--------+------------------------------+----------------+
| p-H$_2$CO $4_{23}-3_{22}$ | $0.0$  | $0.194 \times 0.473, 85.875$ | $0.99$         |
+---------------------------+--------+------------------------------+----------------+
| p-H$_2$CO $4_{22}-3_{21}$ | $0.0$  | $0.126 \times 0.489, 73.735$ | $0.99$         |
+---------------------------+--------+------------------------------+----------------+
| o-H$_2$CO $4_{13}-3_{12}$ | $0.25$ | $0.001 \times 0.435, 83.675$ | $0.97$         |
+---------------------------+--------+------------------------------+----------------+

: Imaging parameters

# Voigt profile line modeling

Following the analysis described in Section [3.4](#subsec:excitation-conditions), we model the disk-averaged emission using Voigt profiles instead of Gaussian to better characterize the line wings. The retrieved disk-averaged spectra and the best-fit parameters are shown in Figure [8](#fig:fitted_disk-averaged_spectra_voigt), where the best-fit models are overlaid with different colors for each H$_2$CO isomer. A similar approach was applied in TW Hya for $^{12}$CO observations likely affected by line pressure broadening (cite: Yoshida2022), which enabled the estimation of its gas surface density. Therefore, the presence of non-Gaussian profiles in HD 163296 could have some implications in constraining its physical conditions, but this is beyond the scope of this work.

![](H2CO_fitted_disk-averaged_spectra_voigt.pdf)

# Optical depth radial profiles

Figure [9](#fig:tau_profiles) shows the deprojected radial profiles of the line optical depth for all H$_2$CO transitions used in this work, resulting from the analysis described in Section [3.4.2](#subsubsec:Resolved_analysis). Each color represents a different transition. The two weakest p-H$_2$CO lines ($4_{22}-3_{21}$ and $4_{23}-3_{22}$) have very similar values for $\tau_{\nu}$; hence, the two curves are overlapping.

![](H2CO_tau_profiles.pdf)

# H$_2$CO formation temperature

Figure [10](#fig:Tspin_profile) shows the deprojected radial profiles of the excitation temperature (see middle panel in Figure [6](#fig:excitation-conds)) and the spin temperature derived from the radially resolved OPR values (see bottom panel in Figure [6](#fig:excitation-conds)). As a consequence of the asymptotic behavior of the OPR as a function of $T_\mathrm{spin}$ (cite: Guzman2018), the arrows represent lower limits in the upper uncertainties of $T_\mathrm{spin}$ for those radii where the OPR upper uncertainties are consistent with $\mathrm{OPR} \geq 3.0$.

![](H2CO_Tspin.pdf)

natexlab

(ref: Al-Refaie2015) Al-Refaie, A. F., Yachmenev, A., Tennyson, J., & Yurchenko, S. N. 2015, MNRAS, 448, 1704, doi: [`10.1093/mnras/stv091`](http://doi.org/10.1093/mnras/stv091)

(ref: Altwegg2019) Altwegg, K., Balsiger, H., & Fuselier, S. A. 2019, ARA&A, 57, 113, doi: [`10.1146/annurev-astro-091918-104409`](http://doi.org/10.1146/annurev-astro-091918-104409)

(ref: Andrews2020) Andrews, S. M. 2020, ARA&A, 58, 483, doi: [`10.1146/annurev-astro-031220-010302`](http://doi.org/10.1146/annurev-astro-031220-010302)

(ref: Andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: Astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Astropy2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Atkinson2006) Atkinson, R., Baulch, D. L., Cox, R. A., et al. 2006, Atmospheric Chemistry & Physics, 6, 3625, doi: [`10.5194/acp-6-3625-2006`](http://doi.org/10.5194/acp-6-3625-2006)

(ref: Basalgete2021I) Basalgète, R., Dupuy, R., Féraud, G., et al. 2021a, A&A, 647, A35, doi: [`10.1051/0004-6361/202039676`](http://doi.org/10.1051/0004-6361/202039676)

(ref: Basalgete2021II) —. 2021b, A&A, 647, A36, doi: [`10.1051/0004-6361/202040117`](http://doi.org/10.1051/0004-6361/202040117)

(ref: Bergner2018) Bergner, J. B., Guzmán, V. G., Öberg, K. I., Loomis, R. A., & Pegues, J. 2018, ApJ, 857, 69, doi: [`10.3847/1538-4357/aab664`](http://doi.org/10.3847/1538-4357/aab664)

(ref: Bergner2021) Bergner, J. B., Öberg, K. I., Guzmán, V. V., et al. 2021, ApJS, 257, 11, doi: [`10.3847/1538-4365/ac143a`](http://doi.org/10.3847/1538-4365/ac143a)

(ref: Bertin2016) Bertin, M., Romanzin, C., Doronin, M., et al. 2016, ApJL, 817, L12, doi: [`10.3847/2041-8205/817/2/L12`](http://doi.org/10.3847/2041-8205/817/2/L12)

(ref: Boogert2015) Boogert, A. C. A., Gerakines, P. A., & Whittet, D. C. B. 2015, ARA&A, 53, 541, doi: [`10.1146/annurev-astro-082214-122348`](http://doi.org/10.1146/annurev-astro-082214-122348)

(ref: Booth2023) Booth, A. S., Law, C. J., Temmink, M., Leemker, M., & Macı́as, E. 2023, A&A, 678, A146, doi: [`10.1051/0004-6361/202346974`](http://doi.org/10.1051/0004-6361/202346974)

(ref: Booth2021) Booth, A. S., Walsh, C., Terwisscha van Scheltinga, J., et al. 2021, Nature Astronomy, 5, 684, doi: [`10.1038/s41550-021-01352-w`](http://doi.org/10.1038/s41550-021-01352-w)

(ref: Booth2024II) Booth, A. S., Temmink, M., van Dishoeck, E. F., et al. 2024a, AJ, 167, 165, doi: [`10.3847/1538-3881/ad26ff`](http://doi.org/10.3847/1538-3881/ad26ff)

(ref: Booth2024I) Booth, A. S., Leemker, M., van Dishoeck, E. F., et al. 2024b, AJ, 167, 164, doi: [`10.3847/1538-3881/ad2700`](http://doi.org/10.3847/1538-3881/ad2700)

(ref: Carney2017) Carney, M. T., Hogerheijde, M. R., Loomis, R. A., et al. 2017, A&A, 605, A21, doi: [`10.1051/0004-6361/201629342`](http://doi.org/10.1051/0004-6361/201629342)

(ref: Carney2019) Carney, M. T., Hogerheijde, M. R., Guzmán, V. V., et al. 2019, A&A, 623, A124, doi: [`10.1051/0004-6361/201834353`](http://doi.org/10.1051/0004-6361/201834353)

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Ceccarelli2023) Ceccarelli, C., Codella, C., Balucani, N., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 379

(ref: Chuang2017) Chuang, K. J., Fedoseev, G., Qasim, D., et al. 2017, MNRAS, 467, 2552, doi: [`10.1093/mnras/stx222`](http://doi.org/10.1093/mnras/stx222)

(ref: Cornwell2008) Cornwell, T. J. 2008, IEEE Journal of Selected Topics in Signal Processing, 2, 793, doi: [`10.1109/JSTSP.2008.2006388`](http://doi.org/10.1109/JSTSP.2008.2006388)

(ref: Czekala2021) Czekala, I., Loomis, R. A., Teague, R., et al. 2021, ApJS, 257, 2, doi: [`10.3847/1538-4365/ac1430`](http://doi.org/10.3847/1538-4365/ac1430)

(ref: Fairlamb2015) Fairlamb, J. R., Oudmaijer, R. D., Mendigutı́a, I., Ilee, J. D., & van den Ancker, M. E. 2015, MNRAS, 453, 976, doi: [`10.1093/mnras/stv1576`](http://doi.org/10.1093/mnras/stv1576)

(ref: Fockenberg2002) Fockenberg, C., & Preses, J. M. 2002, Journal of Physical Chemistry A, 106, 2924, doi: [`10.1021/jp0141880`](http://doi.org/10.1021/jp0141880)

(ref: Foreman-Mackey2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: Fuchs2009) Fuchs, G. W., Cuppen, H. M., Ioppolo, S., et al. 2009, A&A, 505, 629, doi: [`10.1051/0004-6361/200810784`](http://doi.org/10.1051/0004-6361/200810784)

(ref: Gaia2018) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1, doi: [`10.1051/0004-6361/201833051`](http://doi.org/10.1051/0004-6361/201833051)

(ref: Garrod2013) Garrod, R. T. 2013, ApJ, 765, 60, doi: [`10.1088/0004-637X/765/1/60`](http://doi.org/10.1088/0004-637X/765/1/60)

(ref: Garufi2020) Garufi, A., Podio, L., Codella, C., et al. 2020, A&A, 636, A65, doi: [`10.1051/0004-6361/201937247`](http://doi.org/10.1051/0004-6361/201937247)

(ref: Guzman2011) Guzmán, V., Pety, J., Goicoechea, J. R., Gerin, M., & Roueff, E. 2011, A&A, 534, A49, doi: [`10.1051/0004-6361/201117257`](http://doi.org/10.1051/0004-6361/201117257)

(ref: Guzman2018) Guzmán, V. V., Öberg, K. I., Carpenter, J., et al. 2018, ApJ, 864, 170, doi: [`10.3847/1538-4357/aad778`](http://doi.org/10.3847/1538-4357/aad778)

(ref: Guzman2013) Guzmán, V. V., Goicoechea, J. R., Pety, J., et al. 2013, A&A, 560, A73, doi: [`10.1051/0004-6361/201322460`](http://doi.org/10.1051/0004-6361/201322460)

(ref: Guzman2021) Guzmán, V. V., Bergner, J. B., Law, C. J., et al. 2021, ApJS, 257, 6, doi: [`10.3847/1538-4365/ac1440`](http://doi.org/10.3847/1538-4365/ac1440)

(ref: Hama2016) Hama, T., Kouchi, A., & Watanabe, N. 2016, Science, 351, 65, doi: [`10.1126/science.aad4026`](http://doi.org/10.1126/science.aad4026)

(ref: Hama2018) —. 2018, ApJL, 857, L13, doi: [`10.3847/2041-8213/aabc0c`](http://doi.org/10.3847/2041-8213/aabc0c)

(ref: Herbst2009) Herbst, E., & van Dishoeck, E. F. 2009, ARA&A, 47, 427, doi: [`10.1146/annurev-astro-082708-101654`](http://doi.org/10.1146/annurev-astro-082708-101654)

(ref: Hogbom1974) Högbom, J. A. 1974, A&AS, 15, 417

(ref: Huang2016) Huang, J., Öberg, K. I., & Andrews, S. M. 2016, ApJL, 823, L18, doi: [`10.3847/2041-8205/823/1/L18`](http://doi.org/10.3847/2041-8205/823/1/L18)

(ref: Huang2018) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJL, 869, L42, doi: [`10.3847/2041-8213/aaf740`](http://doi.org/10.3847/2041-8213/aaf740)

(ref: Hunter2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Jorgensen2020) Jørgensen, J. K., Belloche, A., & Garrod, R. T. 2020, ARA&A, 58, 727, doi: [`10.1146/annurev-astro-032620-021927`](http://doi.org/10.1146/annurev-astro-032620-021927)

(ref: JvM1995) Jorsater, S., & van Moorsel, G. A. 1995, AJ, 110, 2037, doi: [`10.1086/117668`](http://doi.org/10.1086/117668)

(ref: Kahane1984) Kahane, C., Frerking, M. A., Langer, W. D., Encrenas, P., & Lucas, R. 1984, A&A, 137, 211

(ref: Kastner2018) Kastner, J. H., Qi, C., Dickson-Vandervelde, D. A., et al. 2018, ApJ, 863, 106, doi: [`10.3847/1538-4357/aacff7`](http://doi.org/10.3847/1538-4357/aacff7)

(ref: Law2021III) Law, C. J., Loomis, R. A., Teague, R., et al. 2021a, ApJS, 257, 3, doi: [`10.3847/1538-4365/ac1434`](http://doi.org/10.3847/1538-4365/ac1434)

(ref: Law2021IV) Law, C. J., Teague, R., Loomis, R. A., et al. 2021b, ApJS, 257, 4, doi: [`10.3847/1538-4365/ac1439`](http://doi.org/10.3847/1538-4365/ac1439)

(ref: Lee2019) Lee, J.-E., Lee, S., Baek, G., et al. 2019, Nature Astronomy, 3, 314, doi: [`10.1038/s41550-018-0680-0`](http://doi.org/10.1038/s41550-018-0680-0)

(ref: Loomis2018) Loomis, R. A., Cleeves, L. I., Öberg, K. I., et al. 2018a, ApJ, 859, 131, doi: [`10.3847/1538-4357/aac169`](http://doi.org/10.3847/1538-4357/aac169)

(ref: Loomis2015) Loomis, R. A., Cleeves, L. I., Öberg, K. I., Guzman, V. V., & Andrews, S. M. 2015, ApJL, 809, L25, doi: [`10.1088/2041-8205/809/2/L25`](http://doi.org/10.1088/2041-8205/809/2/L25)

(ref: Loomis2018matchedfilter) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2018b, AJ, 155, 182, doi: [`10.3847/1538-3881/aab604`](http://doi.org/10.3847/1538-3881/aab604)

(ref: McGuire2022) McGuire, B. A. 2022, ApJS, 259, 30, doi: [`10.3847/1538-4365/ac2a48`](http://doi.org/10.3847/1538-4365/ac2a48)

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Miotello2023) Miotello, A., Kamp, I., Birnstiel, T., Cleeves, L. C., & Kataoka, A. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 501, doi: [`10.48550/arXiv.2203.09818`](http://doi.org/10.48550/arXiv.2203.09818)

(ref: Oberg2021) Öberg, K. I., & Bergin, E. A. 2021, Phys. Rep., 893, 1, doi: [`10.1016/j.physrep.2020.09.004`](http://doi.org/10.1016/j.physrep.2020.09.004)

(ref: Oberg2023) Öberg, K. I., Facchini, S., & Anderson, D. E. 2023, ARA&A, 61, 287, doi: [`10.1146/annurev-astro-022823-040820`](http://doi.org/10.1146/annurev-astro-022823-040820)

(ref: Oberg2015b) Öberg, K. I., Furuya, K., Loomis, R., et al. 2015, ApJ, 810, 112, doi: [`10.1088/0004-637X/810/2/112`](http://doi.org/10.1088/0004-637X/810/2/112)

(ref: Oberg2009) Öberg, K. I., Garrod, R. T., van Dishoeck, E. F., & Linnartz, H. 2009, A&A, 504, 891, doi: [`10.1051/0004-6361/200912559`](http://doi.org/10.1051/0004-6361/200912559)

(ref: Oberg2011) Öberg, K. I., Murray-Clay, R., & Bergin, E. A. 2011, ApJL, 743, L16, doi: [`10.1088/2041-8205/743/1/L16`](http://doi.org/10.1088/2041-8205/743/1/L16)

(ref: Oberg2017) Öberg, K. I., Guzmán, V. V., Merchantz, C. J., et al. 2017, ApJ, 839, 43, doi: [`10.3847/1538-4357/aa689a`](http://doi.org/10.3847/1538-4357/aa689a)

(ref: Oberg2021I) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1, doi: [`10.3847/1538-4365/ac1432`](http://doi.org/10.3847/1538-4365/ac1432)

(ref: Paneque-Carreno2023) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., et al. 2023, A&A, 669, A126, doi: [`10.1051/0004-6361/202244428`](http://doi.org/10.1051/0004-6361/202244428)

(ref: Pegues2020) Pegues, J., Öberg, K. I., Bergner, J. B., et al. 2020, ApJ, 890, 142, doi: [`10.3847/1538-4357/ab64d9`](http://doi.org/10.3847/1538-4357/ab64d9)

(ref: Pickett1998) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883, doi: [`10.1016/S0022-4073(98)00091-0`](http://doi.org/10.1016/S0022-4073(98)00091-0)

(ref: Pinte2018) Pinte, C., Ménard, F., Duchêne, G., et al. 2018, A&A, 609, A47, doi: [`10.1051/0004-6361/201731377`](http://doi.org/10.1051/0004-6361/201731377)

(ref: Podio2019) Podio, L., Bacciotti, F., Fedele, D., et al. 2019, A&A, 623, L6, doi: [`10.1051/0004-6361/201834475`](http://doi.org/10.1051/0004-6361/201834475)

(ref: Podio2020) Podio, L., Garufi, A., Codella, C., et al. 2020, A&A, 642, L7, doi: [`10.1051/0004-6361/202038952`](http://doi.org/10.1051/0004-6361/202038952)

(ref: Qi2011) Qi, C., D’Alessio, P., Öberg, K. I., et al. 2011, ApJ, 740, 84, doi: [`10.1088/0004-637X/740/2/84`](http://doi.org/10.1088/0004-637X/740/2/84)

(ref: Qi2015) Qi, C., Öberg, K. I., Andrews, S. M., et al. 2015, ApJ, 813, 128, doi: [`10.1088/0004-637X/813/2/128`](http://doi.org/10.1088/0004-637X/813/2/128)

(ref: Qi2013) Qi, C., Öberg, K. I., & Wilner, D. J. 2013, ApJ, 765, 34, doi: [`10.1088/0004-637X/765/1/34`](http://doi.org/10.1088/0004-637X/765/1/34)

(ref: Rivilla2019) Rivilla, V. M., Martı́n-Pintado, J., Jiménez-Serra, I., et al. 2019, MNRAS, 483, L114, doi: [`10.1093/mnrasl/sly228`](http://doi.org/10.1093/mnrasl/sly228)

(ref: Ryspaeva2023) Ryspaeva, E., Kholtygin, A., & Lyutikov, M. 2023, MNRAS, 521, 2427, doi: [`10.1093/mnras/stad629`](http://doi.org/10.1093/mnras/stad629)

(ref: Salinas2017) Salinas, V. N., Hogerheijde, M. R., Mathews, G. S., et al. 2017, A&A, 606, A125, doi: [`10.1051/0004-6361/201731223`](http://doi.org/10.1051/0004-6361/201731223)

(ref: Salinas2018) Salinas, V. N., Hogerheijde, M. R., Murillo, N. M., et al. 2018, A&A, 616, A45, doi: [`10.1051/0004-6361/201731745`](http://doi.org/10.1051/0004-6361/201731745)

(ref: Schöier2005) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369, doi: [`10.1051/0004-6361:20041729`](http://doi.org/10.1051/0004-6361:20041729)

(ref: Teague2019GoFish) Teague, R. 2019, The Journal of Open Source Software, 4, 1632, doi: [`10.21105/joss.01632`](http://doi.org/10.21105/joss.01632)

(ref: Teague2020KepMask) —. 2020, richteague/keplerian_mask: Initial Release, 1.0, Zenodo, Zenodo, doi: [`10.5281/zenodo.4321137`](http://doi.org/10.5281/zenodo.4321137)

(ref: Teague2019) Teague, R., Bae, J., & Bergin, E. A. 2019, Nature, 574, 378, doi: [`10.1038/s41586-019-1642-0`](http://doi.org/10.1038/s41586-019-1642-0)

(ref: Teague2018bettermoments) Teague, R., & Foreman-Mackey, D. 2018, Research Notes of the American Astronomical Society, 2, 173, doi: [`10.3847/2515-5172/aae265`](http://doi.org/10.3847/2515-5172/aae265)

(ref: Teague2021) Teague, R., Bae, J., Aikawa, Y., et al. 2021, ApJS, 257, 18, doi: [`10.3847/1538-4365/ac1438`](http://doi.org/10.3847/1538-4365/ac1438)

(ref: TvS2021) Terwisscha van Scheltinga, J., Hogerheijde, M. R., Cleeves, L. I., et al. 2021, ApJ, 906, 111, doi: [`10.3847/1538-4357/abc9ba`](http://doi.org/10.3847/1538-4357/abc9ba)

(ref: Tudorie2006) Tudorie, M., Cacciani, P., Cosléou, J., et al. 2006, A&A, 453, 755, doi: [`10.1051/0004-6361:20064952`](http://doi.org/10.1051/0004-6361:20064952)

(ref: vanderMarel2021) van der Marel, N., Booth, A. S., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021, A&A, 651, L5, doi: [`10.1051/0004-6361/202141051`](http://doi.org/10.1051/0004-6361/202141051)

(ref: vanderMarel2014) van der Marel, N., van Dishoeck, E. F., Bruderer, S., & van Kempen, T. A. 2014, A&A, 563, A113, doi: [`10.1051/0004-6361/201322960`](http://doi.org/10.1051/0004-6361/201322960)

(ref: vanderWalt2011) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science and Engineering, 13, 22, doi: [`10.1109/MCSE.2011.37`](http://doi.org/10.1109/MCSE.2011.37)

(ref: vantHoff2018) van ’t Hoff, M. L. R., Tobin, J. J., Trapman, L., et al. 2018, ApJL, 864, L23, doi: [`10.3847/2041-8213/aadb8a`](http://doi.org/10.3847/2041-8213/aadb8a)

(ref: Virtanen2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Walsh2014) Walsh, C., Millar, T. J., Nomura, H., et al. 2014, A&A, 563, A33, doi: [`10.1051/0004-6361/201322446`](http://doi.org/10.1051/0004-6361/201322446)

(ref: Walsh2015) Walsh, C., Nomura, H., & van Dishoeck, E. 2015, A&A, 582, A88, doi: [`10.1051/0004-6361/201526751`](http://doi.org/10.1051/0004-6361/201526751)

(ref: Walsh2016) Walsh, C., Loomis, R. A., Öberg, K. I., et al. 2016, ApJL, 823, L10, doi: [`10.3847/2041-8205/823/1/L10`](http://doi.org/10.3847/2041-8205/823/1/L10)

(ref: Wang2020) Wang, Y., Tennyson, J., & Yurchenko, S. N. 2020, Atoms, 8, 7, doi: [`10.3390/atoms8010007`](http://doi.org/10.3390/atoms8010007)

(ref: Watanabe2002) Watanabe, N., & Kouchi, A. 2002, ApJL, 571, L173, doi: [`10.1086/341412`](http://doi.org/10.1086/341412)

(ref: Williams2011) Williams, J. P., & Cieza, L. A. 2011, ARA&A, 49, 67, doi: [`10.1146/annurev-astro-081710-102548`](http://doi.org/10.1146/annurev-astro-081710-102548)

(ref: Yocum2023) Yocum, K. M., Wilkins, O. H., Bardwell, J. C., Milam, S. N., & Gerakines, P. A. 2023, ApJL, 958, L41, doi: [`10.3847/2041-8213/ad0bee`](http://doi.org/10.3847/2041-8213/ad0bee)

(ref: Yoshida2022) Yoshida, T. C., Nomura, H., Tsukagoshi, T., Furuya, K., & Ueda, T. 2022, ApJL, 937, L14, doi: [`10.3847/2041-8213/ac903a`](http://doi.org/10.3847/2041-8213/ac903a)

(ref: Zhang2021) Zhang, K., Booth, A. S., Law, C. J., et al. 2021, ApJS, 257, 5, doi: [`10.3847/1538-4365/ac1580`](http://doi.org/10.3847/1538-4365/ac1580)

[^1]: HD 163296 protoplanetary disk coordinates are $\alpha(2000) = 17^\mathrm{h}56^\mathrm{m}21.280^\mathrm{s}$; $\delta(2000) = -21^\circ57^\prime22.441^{\prime\prime}$.

[^2]: https://casa.nrao.edu/

[^3]: https://alma-maps.info/data.html

[^4]: https://almascience.eso.org/documents-and-tools/cycle10/alma-technical-handbook

[^5]: https://github.com/richteague/bettermoments

[^6]: https://github.com/teresapaz/alfahor

[^7]: We cannot discard the possibility that the tentative variations observed in the OPR profile could be due to slight deviations from the assumptions made to derive $N_\mathrm{T}$ (e.g., LTE emission, same $T_{\mathrm{ex}}$ for both isomers and the same emitting region for all the lines).

</paper>

Write the methods card for this paper.