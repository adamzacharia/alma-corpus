# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020MNRAS.499.4940Z\sonnetcc\reply.txt

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
 "bibcode": "2020MNRAS.499.4940Z",
 "title": "Unravelling the enigmatic ISM conditions in Minkowski's object",
 "year": 2020,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Zovaro, Henry R. M.",
 "n_authors": 10,
 "arxiv_id": "2010.03139",
 "doi": "10.1093/mnras/staa3121",
 "alma_projects_linked_by_archive": [
  "2015.1.00570.S"
 ]
}
```

Paper text:
<paper>
# Unravelling the enigmatic ISM conditions in Minkowski’s Object

## Abstract

Local examples of jet-induced star formation lend valuable insight into its significance in galaxy evolution and can provide important observational constraints for theoretical models of positive feedback. Using optical integral field spectroscopy, we present an analysis of the ISM conditions in Minkowski’s Object ($z = 0.0189$), a peculiar star-forming dwarf galaxy located in the path of a radio jet from the galaxy NGC 541. Full spectral fitting with PPXF indicates that Minkowski’s Object primarily consists of a young stellar population $\sim 10\,\rm Myr$ old, confirming that the bulk of the object’s stellar mass formed during a recent jet interaction. Minkowski’s Object exhibits line ratios largely consistent with star formation, although there is evidence for a low level ($\lesssim 15 \,\rm per \, cent$) of contamination from a non-stellar ionising source. Strong-line diagnostics reveal a significant variation in the gas-phase metallicity within the object, with $\log\left( \rm O / H \right) + 12$ varying by $\sim 0.5\,\rm dex$, which cannot be explained by in-situ star formation, an enriched outflow from the jet, or enrichment of gas in the stellar bridge between NGC 541 and NGC 545/547. We hypothesise that Minkowski’s Object either (a) was formed as a result of jet-induced star formation in pre-existing gas clumps in the stellar bridge, or (b) is a gas-rich dwarf galaxy that is experiencing an elevation in its star formation rate due to a jet interaction, and will eventually redden and fade, becoming an ultra-diffuse galaxy as it is processed by the cluster.

galaxies: individual: Minkowski’s Object – galaxies: dwarf – galaxies: peculiar – galaxies: ISM – galaxies: jets – stars: formation

# Introduction

It has long been established that jets play a vital role in curbing star formation, by preventing cooling flows in cluster environments (cite: McNamaraNulsen2012), by driving powerful outflows (cite: Morganti2005; Holt2008; Schulz2018) and by rendering the interstellar medium (ISM) of their host galaxies turbulent (cite: Nesvadba2010; Nesvadba2011; Ogle2010). In comparison, the phenomenon of *positive feedback*, wherein jets enhance or trigger star formation, remains poorly understood, although it may make an important contribution to the star formation histories of galaxies across cosmic time (cite: Silk2005; Gaibler2012).

The observed alignment of jets with stellar components and enhanced emission from dense gas is strong evidence of positive feedback. Many radio galaxies at high redshifts exhibit extended stellar continua that are aligned with the axis of the radio jet, referred to as the ‘alignment effect’ (cite: Chambers1987; McCarthy1987; Best1996). Similar alignments have been observed in cluster environments at low redshift (cite: McNamara&O’Connell1993). More recent studies have also revealed alignment of molecular gas and radio jets in galaxies at high redshift (cite: Klamer2004; Emonts2014). Hydrodynamical simulations have shown that shocks generated by the passage of a jet through an ionised medium may induce runaway cooling, leading to the formation of both atomic and molecular gas, which may collapse to form stars (cite: Fragile2004; Fragile2017). However, the detailed workings of positive feedback remain elusive, largely due to the dearth of local examples of jet-induced star formation, severely limiting our ability to study this complex phenomenon with sufficient angular resolution to compare observations to detailed hydrodynamical simulations.

Minkowski’s Object (cite: Minkowski1958) is one of only three known examples of jet-induced star formation in the local Universe, the others being the string of OB associations in the jet of Centaurus A (cite: Blanco1975; Santoro2015; Santoro2016; Salome2016a; Salome2016b; Salome2017) and a star-forming region in the jet of 3C 285 (cite: Salome2015). Located in the cluster Abell 194, MO is a star-forming dwarf galaxy located along the path of a jet from the nearby elliptical galaxy NGC 541. Due to its low redshift (cite: Croft2006), MO presents a critical opportunity to study an object formed by positive feedback in high resolution.

Whilst past studies of MO have focused on broad-band photometry or slit spectroscopy, this work utilises integral field spectroscopy, enabling us to spatially resolve the ISM conditions in this object for the first time.

In this paper, we present a study of the stellar and gas properties of MO using optical integral field spectroscopy. In Section [2](#sec: paper 3: Minkowski's Object), we summarise the properties of MO, and in Section [3](#sec: paper 3: Properties of NGC 541 and Abell 194) we give an overview of NGC 541 and the cluster environment of MO. We present our observations and data reduction in Section [4](#sec: paper 3: Observations and data reduction), before detailing the stellar population analysis in Section [5](#sec: paper 3: Stellar population analysis) and our analysis of the emission-line gas in Section [6](#sec: paper 3: Emission line gas). We then consider the possible causes of the observed metallicity variation in MO in Section [7](#sec: paper 3: The cause of the metallicity variation), before discussing the origin of MO in Section [8](#sec: paper 3: On the formation of Minkowski's Object) and summarising our findings in Section [9](#sec: paper 3: Conclusion). For the remainder of this paper, we assume a cosmology with $H_0 = 70\rm\,km\,s^{-1}\,Mpc^{-1}$, $\Omega_M = 0.3$, and $\Omega_\Lambda = 0.7$.

# Minkowski’s Object

MO is a peculiar dwarf galaxy located in the cluster Abell 194, with properties summarised in Table [\[tab: paper 3: MO & NGC541 properties\]](#tab: paper 3: MO & NGC541 properties). MO lies in the path of an FR I-type (cite: Fanaroff&Riley1974) jet from the elliptical galaxy NGC 541 (cite: Smith2000) which lies $18~\rm kpc$ to the South-West, as shown in Fig. [1](#fig: paper 3: Abell 194).

As can be seen in Fig. [2](#fig: paper 3: HST overlay), MO has an irregular and filamentary structure, with the brightest clumps forming a ‘bar’ approximately perpendicular to the jet axis. estimated MO to have a stellar mass $M_* = 1.9 \times 10^{7} \,\rm M_\odot$, with a broad-band spectral energy distribution (SED) consistent with a stellar population resulting from a single starburst 7.5 Myr ago with a secondary population of stars older than 1 Gyr.

MO is embedded in a cloud of neutral gas with an estimated mass $M_{\rm H\,\textsc{i}} = 4.9 \times 10^{8} \,\rm M_\odot$ which is located along the path of the jet, extending downstream of MO (see their fig. 3). Molecular gas has been detected in four distinct clumps with intervening diffuse emission (cite: Lacy2017) with a total mass $M_{\rm H_2} = 3.0 \times 10^7 \rm M_\odot$ assuming a standard Milky Way (MW) CO-to-H~2~ conversion factor $\alpha_{\rm CO}$, or $M_{\rm H_2} = 1.8 \times 10^8 \rm M_\odot$ assuming an $\alpha_{\rm CO}$ appropriate for a galaxy with half-solar gas-phase metallicity.

Both the H I and molecular gas exhibit steep velocity gradients perpendicular to the jet axis, which attribute to a jet interaction. The velocity dispersion of the CO ($\lesssim 10~\rm km~s^{-1}$) is much lower than that of the H I in the same region ($25~\rm km~s^{-1}$); this may be caused by shocks generated by the jet passing through an inhomogeneous medium .

| **Property** | **Symbol** | **MO** | **NGC 541** |
|:--:|:--:|:--:|:--:|
| Stellar mass | $M_*$ | $1.9 \times 10^7 \,\rm M_\odot$^*a*^ | $4.7 \times 10^{11} \,\rm M_\odot$^*d*^ |
| H I mass | $M_{\rm H\,\textsc{i}}$ | $4.9 \times 10^8 \rm\, M_\odot$^*a*^ | — |
| Molecular gas mass | $M_{\rm H_2}$ | $3.0 \times 10^7 \rm\,  M_\odot$^*b*,$\dagger$^ | $1.7 \times 10^8 \,\rm M_\odot$^*d*,$\dagger$^ |
|  |  | $1.8 \times 10^8 \rm \, M_\odot$^*b*,$\ddagger$^ |  |
| Star formation rate | $\rm SFR$ | $(0.24 - 0.28) \pm 0.09 \,\rm M_\odot \, yr^{-1}$^*c*^ | $0.095 \,\rm M_\odot \, yr^{-1}$^*d*^ |
| Specific star formation rate | $\rm sSFR$ | $13 - 15 \rm \, Gyr^{-1}$^*c*^ | $0.0002 \,\rm Gyr^{-1}$^*d*^ |
| Depletion time (atomic gas) | $t_{\rm dep, \, H\,I}$ | $1.7 - 2.0 \,\rm Gyr$^*c*,§^ | — |
| Depletion time (molecular gas) | $t_{\rm dep, \,H_2}$ | $0.11 - 0.12 \,\rm Gyr$^*c*,$\dagger$^ | $1.79 \,\rm Gyr$^*d*,$\dagger$^ |
|  |  | $0.64 - 0.75 \,\rm Gyr$^*c*,$\ddagger$^ |  |

References: $^a$; $^b$; $^c$This work; $^d$(cite: Salome2015); ^§^Based on H I mass; ^$\dagger$^assuming a MW $\alpha_{\rm CO}$; ^$\ddagger$^assuming a half-solar metallicity $\alpha_{\rm CO}$.

![](fig1.pdf)

![image](fig2a.pdf) ![image](fig2b.pdf)

# Abell 194 and NGC 541

Abell 194 is a poor (cite: Abell1989) and cold (cite: Sakelliou2008) cluster with a linear morphology at $z = 0.018$ (cite: Struble1999). It hosts two powerful radio galaxies close to the cluster centre, NGC 541 and NGC 547, which is part of the interacting pair NGC 545/547 (cite: Smith2000). The Southern jet from NGC 547 is associated with an X-ray cavity (cite: Bogdan2011). As shown in Fig. [1](#fig: paper 3: Abell 194), NGC 541 and NGC 545/547 are separated by approximately 100 kpc in projection, and are connected by a faint stellar bridge, a remnant of a previous or ongoing interaction. Both radio galaxies host bent jets, which (cite: Sakelliou2008) attribute to the motion of the galaxies through the cluster. Abell 194 may be undergoing a significant merger event, in which both NGC 541 and NGC 545 are falling towards NGC 547 (cite: Bogdan2011).

NGC 541 is a massive elliptical galaxy, and is the brightest cluster galaxy (BCG) in Abell 194. It is extremely gas-poor, with a gas fraction of $0.4$ per cent and a star formation rate (SFR) of $0.095 \,\rm M_\odot \, yr^{-1}$ (cite: Salome2015). NGC 541 may harbour a disc or ring of molecular gas (cite: Salome2015), possibly a remnant of a previous interaction. The properties of NGC 541 are summarised in Table [\[tab: paper 3: MO & NGC541 properties\]](#tab: paper 3: MO & NGC541 properties).

## Properties of the radio jet

NGC 541 hosts an asymmetric FR I radio source with $P_{1.4~\textrm{GHz}} = 5.9 \times 10^{23}~\rm W~Hz^{-1}$ (cite: vanBreugel1985) which can be seen in Fig. [2](#fig: paper 3: HST overlay). The Eastern jet is aligned with the stellar bridge, and gradually broadens along its path from the host galaxy until it interacts with MO, at which point it decollimates. The Western jet is less extended and is sharply bent a short distance from the nucleus.

Using the ALMA 106 GHz continuum image of , we used the minimum energy method, as detailed in section 5.1 of (cite: Zovaro2019a), to estimate the power of the Eastern jet. The jet volume was approximated as a truncated cone, with length 21 kpc and end surface radii of 1.5 kpc and 6 kpc, and was assumed to have a constant flux density of $30 \,\rm \upmu Jy \, beam^{-1}$, with a spectral index $\alpha = 0.8$. A jet age of $10^7\,\rm yr$ was adopted, chosen to be consistent with the age of the stellar population of MO . Lower and upper Lorentz factors for the electrons were fixed to $10^2$ and $10^5$ respectively. These parameters yield a jet power of approximately $1.2 \times 10^{43}\,\rm erg \, s^{-1}$.

# Observations and data reduction

We observed MO with the Wide-Field Spectrograph (cite: Dopita2007; Dopita2010) on the Australian National University 2.3 m telescope at Siding Spring Observatory, NSW, Australia. WiFeS is an image slicer integral field spectrograph comprising 25 1”-width slices with 0.5” sampling along the image, binned to 1” to better match the seeing, providing 1” $\times$ 1” spaxels over a 25” $\times$ 38” field-of-view.

MO was observed on the 29th of November and 1st of December 2016 (PI Banfield, proposal ID 4160092) using the low-resolution B3000 (3200 Å–5000 Å, $R \sim 3000$, $\Delta v \approx 100 \,\rm km\,s^{-1}$) and the high-resolution R7000 (5290 Å–7060 Å, $R \sim 7000$, $\Delta v \approx 40 \,\rm km\,s^{-1}$) gratings with the RT560 beam splitter, using 1200 s exposures. Due to the large angular extent of MO, the observations were dithered in an E-W direction using an offset of 12”, as shown in the bottom panel of Fig. [2](#fig: paper 3: HST overlay). The total effective exposure time was 9600 s. The stars HD26169, HD16031, HD44007 and HD9051 were used as flux and telluric standards (cite: Bessell1999).

## Data reduction

The observations were reduced in the standard way using PYWIFES, the data reduction pipeline for WiFeS (cite: Childress2014). Cu-Ar and Ne-Ar arc lamp exposures were used to derive the wavelength solution, and exposures of the coronagraphic wire mask were used to calibrate the spatial alignment of the slits. Quartz lamp and twilight flat exposures were used to correct for wavelength and spatial variations in the instrument response respectively. Exposures of standard stars were used to correct for telluric absorption and for flux calibration. Two data cubes were generated for each exposure, corresponding to the blue (B3000) and red (R7000) arms of the spectrograph respectively.

To maximise time on-source, we did not take sky frames during our observing campaign. Regions within the field-of-view with no source signal were instead used to extract the sky spectrum which was then subtracted from the data cube. Sky subtraction residuals were minimised by scaling the flux of the sky spectrum to the measured intensity of a subset of sky lines in each spaxel.

The variety in atmospheric transmission and seeing conditions during our observing campaign led to subtle multiplicative offsets in the fluxes amongst individual exposures. Optimal scaling factors for each cube were computed using a least-squares minimisation technique between overlapping regions of the individual data cubes.

Mosaics were created by spatially shifting the scaled data cubes and combining them by taking the sigma-clipped median of each pixel. $1\sigma$ errors for each pixel value in the final mosaic were derived from the standard deviation of the pixels in the individual cubes.

Finally, the data cubes were corrected for Galactic extinction using the extinction map of (cite: Schlafly&Finkbeiner2011) which gives $A_V = 0.1198$. To apply the correction to our WiFeS data we used reddening curve of (cite: Fitzpatrick&Massa2007) with $R_V = 3.1$.

Fig. [3](#fig: paper 3: WiFeS spectra) shows 1D spectra extracted from the resulting data cubes.

![image](fig3a.pdf) ![image](fig3b.pdf)

# Stellar population analysis

We used the PYTHON implementation of Penalized Pixel Fitting (PPXF)[^2] (cite: Cappellari&Emsellem2004; Cappellari2017) to analyse the stellar population by fitting combinations of simple stellar population (SSP) templates to the stellar continuum. This is a refinement of the work of , who carried out a similar analysis using broad-band photometry.

Due to the predominantly young stellar population of MO , we used the SSP models of (cite: GonzalezDelgado2005) which have a fine age resolution at young stellar ages, with a resolution of 1 Myr for ages up to 10 Myr, 5 Myr for ages from 10 Myr to 100 Myr and 100 Myr from 100 Myr to 1 Gyr. The SSP templates were generated using both the Geneva and the Padova isochrones with a Salpeter IMF, spanning an age range 1 Myr to 10 Gyr divided into 46 bins with five metallicities for the Geneva isochrones ($0.05\rm Z_\odot$, $0.2\rm Z_\odot$, $0.4\rm Z_\odot$, $1\rm Z_\odot$ and $2 \rm Z_\odot$), and three for the Padova isochrones ($0.2\rm Z_\odot$, $0.4\rm Z_\odot$ and $0.95\rm Z_\odot$).

Because MO is thought to have a low gas-phase metallicity , we used the Geneva isochrones for which the stellar templates extend to lower metallicities than the Padova isochrones. Although the Geneva isochrones do not include stellar evolution along the red giant branch, we do not believe this to be of critical importance due to the predominantly young stellar population of MO. We confirmed that this did not bias our results by repeating our analysis using the Padova isochrones, which yielded very similar results (see Appendix [10](#appendix: Additional PPXF fits)).

As can be seen in Fig. [3](#fig: paper 3: WiFeS spectra), there are very few stellar absorption features in the R7000 wavelength range; hence we only analysed our B3000 data with PPXF. Due to the low continuum surface brightness of MO, our data cubes lacked the S/N to recover ages and metallicities in each spaxel. Because the line emission in MO has a young stellar population it is reasonable to assume that the majority of stars are located in the regions with bright emission line flux. We therefore created an integrated spectrum by summing the spaxels in which the H$\upalpha$ flux exceeded $1.5 \times 10^{-15} \rm \, erg\,s^{-1}\,cm^{-2}$. This flux limit was chosen as the resulting region is similar to the 8” aperture used by in their SSP analysis using SED fitting, enabling a direct comparison of our analysis to their results. The median S/N in the resulting spectrum was approximately 7.5 per spectral pixel.

To obtain the best-fit age and metallicity, the stellar continuum and the emission lines were fitted simultaneously, adopting independent velocity components for each, where emission lines were fit using Gaussian profiles. A 4th-order multiplicative polynomial was included in the fit to compensate for extinction and calibration errors. *Regularisation* was used to bias the best-fit template weights towards the smoothest solution consistent with the data. The regularisation parameter `regul` was determined using the standard method (cite: Boardman2017). We performed a fit firstly with `regul` $= 0$, and secondly where the noise on the input spectrum was multiplied by the reduced-$\chi^2$ of the first fit. `regul` was gradually increased until the difference in the reduced-$\chi^2$ for the regularised and non-regularised fits $\Delta \chi^2 \simeq \sqrt{2 N}$, where $\Delta \chi^2 = N \left(\chi^2/\textrm{DOF} - 1 \right)$, and $N$ is the number of data points in the input spectrum and $\textrm{DOF}$ is the number of degrees-of-freedom.

Fig. [4](#fig: paper 3: ppxf integrated fit, age & metallicity) shows the best-fit spectrum and template weights. There are two clear stellar populations in MO, with approximate ages of $4-5 \,\rm Myr$ and $1 \,\rm Gyr$. The younger population is directly associated with MO, whereas the older population may represent stars associated with the stellar bridge, or with the object itself. These results are consistent with the broad-band SED analysis of , who found the best-fit stellar population is dominated by a component approximately $7.5 \, \rm Myr$ old, with up to $20$ per cent of the light attributed to a component at $1 \,\rm Gyr$.

Simultaneously constraining both the age and metallicity of the stellar population is challenging due to the lack of strong metal absorption features in the stellar continuum. We therefore repeated our analysis using templates with fixed metallicities, yielding similar results, as detailed in Appendix [10](#appendix: Additional PPXF fits).

To further check whether MO is dominated by a young stellar population, we individually fitted each SSP template in age and metallicity (for both the Padova and Geneva isochrones), including Gaussian emission lines and a multiplicative polynomial to correct for calibration errors, and calculated the resulting reduced-$\chi^2$. For all template metallicities, the minimum reduced-$\chi^2$ occurs at ages $\lessapprox 15 \rm \, Myr$, with the $\chi^2$ gradually increasing with template age. Thus we conclude the stellar population in MO is indeed young.

![image](fig4a.pdf) ![image](fig4b.pdf)

# Emission line gas

## Emission line fitting

We used MPFIT (cite: Markwardt2009), a PYTHON implementation of the Levenberg-Marquardt algorithm (cite: More1978) developed by M. Rivers[^3] to estimate line fluxes in each spaxel by simultaneously fitting a single Gaussian profile to each emission line and a linear component to fit the stellar continuum. Each emission line was fitted over a small window centred on the systemic velocity of MO. All emission lines were fitted simultaneously and were constrained to have the same systemic velocity and velocity dispersion.

Due to the lack of prominent stellar absorption features and the high equivalent widths of the Balmer emission lines compared to the corresponding stellar absorption features (see Fig. [3](#fig: paper 3: WiFeS spectra)), and because we lacked the S/N to fit the stellar continuum in each spaxel, we did not subtract the best-fit stellar continuum from spaxels before fitting emission lines. To check whether this would effect our emission line fluxes, we used the equivalent width (EW) of the H$\upbeta$ line (approximately $7.6$ Å), estimated from our PPXF fit, to estimate the stellar absorption flux in each spaxel by measuring the continuum flux in two windows adjacent to the H$\upbeta$ line. In most spaxels, the stellar absorption is less than $10\,\rm per \, cent$ of the measured H$\upbeta$ emission line flux. To investigate the effect on the H$\upalpha$ absorption, we used a solar-metallicity STARBURST99 model (cite: Leitherer1999) with an instantaneous burst star formation history and a Salpeter IMF to estimate the H$\upalpha$ EW because it was not measured in our PPXF analysis. At an age of $10^7 \,\rm yr$ the H$\upalpha$ EW $\approx 16\,$Å. Using the same method as for H$\upbeta$, we again found the stellar absorption accounts for less than $10\,\rm per \, cent$ of the measured H$\upalpha$ emission line flux in most spaxels, confirming that this has a minimal effect on our reported emission line fluxes. As such, this systematic error has not been included in the reported line fluxes.

Unless specified otherwise, for the remainder of our analysis, we only include spaxels in which the fit has a reduced-$\chi^2 < 2$ and $\rm S/N > 3$ in the H$\upalpha$, H$\upbeta$, \[O II\], \[O III\], \[N II\] and \[S II\] lines. Upper limits for the weakest line used in our analysis, \[O I\]$\uplambda 6300$, were calculated in each spaxel assuming a Gaussian amplitude equal to $3\sigma$, where $\sigma$ is the standard deviation in a window centred on the emission line, and the same width as the other lines in that spaxel. In all quoted linewidths, the instrumental resolution was accounted for by subtracting the width of the line spread function (LSF) in quadrature from the width of the fitted Gaussian, where the width of the LSF was estimated by fitting Gaussian profiles to sky lines.

Integrated line fluxes for emission lines in MO are shown in Table [1](#tab: paper 3: emission line fluxes), which were estimated by summing the fluxes in each spaxel, except for very faint lines, such as He I $\uplambda3889$, for which fluxes were estimated by fitting a single Gaussian profile to the integrated spectrum.

+-----------------------------------------------------------------+-----------------------------------------------------------------+
| **Emission line**                                               | **Flux** ($\rm 10^{-15} \, erg \, s^{-1} \, cm^{-2}$)           |
+:===============================================================:+:===============================================================:+
| $\uplambda3726$                                                 | $15.1 \pm 0.3$                                                  |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| \[O II\]$\uplambda3729$                                         | $24.0 \pm 0.4$                                                  |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| H$\upbeta$                                                      | $17.3 \pm 0.2$                                                  |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| \[O III\]$\uplambda\uplambda4959,5007$                          | $64.8 \pm 0.6$                                                  |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| \[Ne II\]$\uplambda3869^\dagger$                                | $1.7 \pm 0.3$                                                   |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| He I $\uplambda3889^\dagger$                                    | $2.1 \pm 0.3$                                                   |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| H$\upvarepsilon$$^\dagger$                                      | $1.3 \pm 0.3$                                                   |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| H$\updelta$$^\dagger$                                           | $2.5 \pm 0.2$                                                   |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| H$\upgamma$$^\dagger$                                           | $5.3 \pm 0.2$                                                   |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| \[O I\]$\uplambda6300^\ddagger$                                 | $\leq 1.1$                                                      |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| H$\upalpha$                                                     | $47.9 \pm 0.1$                                                  |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| \[N II\]$\uplambda6548,6583$                                    | $5.60 \pm 0.06$                                                 |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| \[S II\]$\uplambda6716$                                         | $8.87 \pm 0.07$                                                 |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| \[S II\]$\uplambda6731$                                         | $5.79 \pm 0.06$                                                 |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| He I $\uplambda5876^\dagger$                                    | $1.13 \pm 0.05$                                                 |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| \[O I\]$\uplambda6364^\dagger$                                  | $0.39 \pm 0.05$                                                 |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
| ^$\dagger$^Flux estimated by fitting a single Gaussian profile to the integrated spectrum. ^$\ddagger$^$3\sigma$ upper limit.     |
+-----------------------------------------------------------------------------------------------------------------------------------+

: Total emission line fluxes. The $1\sigma$ errors shown represent the formal uncertainty on the emission line fit.

## Kinematics and morphology

Fig. [5](#fig: paper 3: Halpha kinematics and morphology) shows maps of the H$\upalpha$ flux, radial velocity and velocity dispersion. The radial velocities increase from South to North, which is consistent with those of the CO and H I . The velocity dispersion is low, with values around $15\,\rm km\,s^{-1}$ in most parts of the object, peaking in the West with $\sigma \approx 30 \,\rm km\,s^{-1}$.

The H$\upalpha$ emission appears to follow the stellar distribution, which can be seen in the bottom panel of Fig. [2](#fig: paper 3: HST overlay); the emission is concentrated along the central “bar” of the object running South-East to North-West, with fainter H$\upalpha$ emission visible along the extended filamentary structures. The two brightest CO clouds  are located along the filaments to the North-East, whereas the fainter two CO clouds overlap with the two bright H$\upalpha$ knots in the bar, perhaps indicating that star formation has been ongoing in the bar for a longer period than in the filaments. This scenario would be consistent with the jet triggering star formation as it propagates through the object from South-West to North-East. The bulk of the H I being located further downstream  also supports this hypothesis.

![image](fig5a.pdf) ![image](fig5b.pdf) ![image](fig5c.pdf)

## Reddening

After correcting for foreground extinction, we used the H$\upalpha$ and H$\upbeta$ fluxes to estimate the extinction. The $A_V$ in each spaxel is shown in the upper panel of Fig. [6](#fig: paper 3: reddening), where we have used the reddening curve of (cite: Fitzpatrick&Massa2007) with $R_V = 3.1$. Only spaxels in which the S/N in the H$\upalpha$/H$\upbeta$ ratio exceeds 3 are shown. The mean $A_V = 0.17 \pm 0.04$, which is slightly higher than the value of , who reported negligible reddening within MO. However, our spatially resolved extinction map reveals significantly higher values of $A_V$ in several clumpy regions to the East, although as discussed in Section [6.5](#subsec: paper 3: Excitation mechanism), this may be a result of an intrinsically enhanced Balmer decrement due to X-ray photoionisation.

Because the S/N was insufficient to measure $A_V$ in all spaxels in which line emission was detected, we repeated the above process after spatially binning the data cube by a factor of three; the resulting extinction map is shown in the lower panel of Fig. [6](#fig: paper 3: reddening). Emission line fluxes were corrected for intrinsic reddening by applying the $A_V$ estimated in the corresponding spaxel in the binned data cube; in those spaxels in which $A_V$ could not be measured or $A_V < 0$, no extinction correction was applied.

![image](fig6a.pdf) ![image](fig6b.pdf)

## Electron density

To estimate the electron density in each spaxel, we used the ratio $R$ of the emission lines in the \[S II\]$\uplambda\uplambda 6716,6731$ doublet and eqn. 3 of (cite: Proxauf2014). We detected no significant variation in $R$ across the object, with the mean $R  = 1.35 \pm 0.03$, placing MO on the cusp of the low-density limit ($n_e \lesssim 10 \,\rm cm^{-3}$), which is consistent with the findings of .

## Excitation mechanism

To determine the excitation mechanism of the emission line gas, we use optical diagnostic diagrams (cite: Baldwin1981; Veilleux&Osterbrock1987; Kewley2001; Kauffmann2003; Kewley2006), in which the \[O III\]$\uplambda 5007$/H$\upbeta$ ratio is plotted as a function of the \[N II\]$\uplambda 6583$/H$\upalpha$, \[S II\]$\uplambda\uplambda6716,6731$/H$\upalpha$ and \[O I\]$\uplambda 6300$/H$\upalpha$ ratios. ODDs for each spaxel in MO are shown in Fig. [7](#fig: paper 3: ODD diagrams).

There is a broad spread in the \[S II\]/H$\upalpha$ and \[O I\]/H$\upalpha$ ratios within the object, which is likely due to an intrinsic metallicity variation within the object. Indeed, inspection of the middle panel of Fig. [7](#fig: paper 3: ODD diagrams) shows that the metallicity calculated using the N2O2 diagnostic of (cite: KewleyNichollsSutherland2019) increases smoothly as a function of the \[N II\]/H$\upalpha$, \[S II\]/H$\upalpha$ and \[O I\]/H$\upalpha$ ratios, following a trajectory very similar to the metallicity sequence observed in SDSS galaxies (cite: Kewley2006).

![image](fig7a.pdf) ![image](fig7b.pdf) ![image](fig7c.pdf)

Although most spaxels lie beneath the line of maximal star formation, there are some spaxels that lie beyond this line, indicating a contribution from ionising sources other than star formation. In Fig. [8](#fig: paper 3: Line ratio diagrams w. Van Zee models) we present additional line ratio diagrams, where we include the sample of ‘typical’ H II regions in nearby spiral galaxies from (cite: vanZee1998). Grids from (cite: Kewley2019) representing MAPPINGS V (cite: Sutherland2018) H II region plane-parallel models with $\log(P/k) = 5.0$, varying in ionisation parameter and metallicity, are shown for comparison. Although the spaxels in MO are similar to the H II regions in the R23 ((\[O II\]$\uplambda \uplambda 3726,3729$ + \[O III\]$\uplambda \uplambda 4959,5007$)/H$\upbeta$) vs. N2O2 (\[N II\]$\uplambda\uplambda 6548,6583$/\[O II\]$\uplambda\uplambda 3726,3729$) and O3O2 (\[O III\]$\uplambda\uplambda 4959,5007$/\[O II\]$\uplambda\uplambda 3726,3729$) vs. N2O2 plots, a significant number of spaxels have S2 (\[S II\]$\uplambda\uplambda 6716,6731$/H$\upalpha$) ratios much higher than both the H II regions and MAPPINGS models, suggesting the presence of secondary excitation mechanisms.

![](fig8.pdf)

![](fig9.pdf)

As an additional check for whether the line ratios in MO are consistent with star formation alone, we used NEBULABAYES (cite: Thomas2018), a PYTHON package that uses a Bayesian method to estimate ISM conditions from observed emission line fluxes using input model grids. NEBULABAYES was used with the same H II region model grid generated using MAPPINGS, however with $\log(P/k)$ varying from $\log(P/k) = 4.0$ to $\log(P/k) = 9.0$. In most spaxels, the best fit model had a very poor reduced-$\chi^2$ and $\log(P/k) \approx 6.5$. Such a high pressure is inconsistent with both the estimated conditions within the jet plasma in MO (cite: vanBreugel1985), and with the low electron density predicted by the \[S II\] ratio ($n \lesssim 10 \,\rm cm^{-3}$, Section [6.4](#subsec: paper 3: Electron density)). Using NEBULABAYES with a log-normal prior on the ISM pressure centred on $\log(P/k) \leq 5.0$ yielded similarly poor reduced-$\chi^2$ values in most spaxels, providing further evidence for excitation mechanisms other than star formation.

In the following sections, we investigate shock excitation, diffuse ionised gas (DIG) and X-ray photoionisation from the nucleus of NGC 541 as possible ionising sources in MO.

### Shock excitation

Given that the jet appears to be passing through the centre of MO (Fig. [2](#fig: paper 3: HST overlay)), shocks are likely to be present. In Appendix [12](#appendix: Estimating the shock velocities in MO), we estimate the shock velocities induced by a typical transonic FR I-type jet interacting with an H I cloud to be $\leq 20 \, \rm km \, s^{-1}$. This is consistent with the observed H I velocity dispersion . Such slow shocks would not produce any detectable optical line emission; however, faster shocks may be present due to its inhomogeneous morphology.

To determine whether shocks could cause the enhanced \[S II\] and \[O I\] emission, in Figs. [\[fig: paper 3: ODD w. DS17 models\]](#fig: paper 3: ODD w. DS17 models) and [\[fig: paper 3: ODD w. A08 models\]](#fig: paper 3: ODD w. A08 models) we show ODDs overlaid with the slow and fast shock models of (cite: Dopita&Sutherland2017) and (cite: Allen2008) respectively. The slow shock models are shown for shock speeds $v_s = 70 - 170 \,\rm km\,s^{-1}$ and pre-shock densities $n = 1 - 10000 \,\rm cm^{-3}$. In these models, the shock propagates into a solar metallicity nebula with a fixed magnetic parameter of $B / \sqrt{n} = 3.23 \rm \, \upmu G \, cm^{3/2}$, corresponding to equipartition. The fast shock models are shown for shock speeds $v_s = 100 - 500 \,\rm km\,s^{-1}$ and magnetic field strengths $B = 0 - 10 \,\rm \upmu G$. These models correspond to a solar metallicity nebula with a pre-shock density $n = 1\,\rm cm^{-3}$, and include line emission from both the post-shock gas and the photoionised precursor.

Although the (cite: Dopita&Sutherland2017) models appear to overlap with the data in the ODDs, slow shocks with pre-shock densities of $n = 1-10 \, \rm cm^{-3}$ models (consistent with the observed electron density estimated in Section [6.4](#subsec: paper 3: Electron density)) would tend to reduce the \[S II\] and \[O I\] whilst enhancing the \[N II\], contrary to our observations. Furthermore, as shown in Fig. [11](#fig: paper 3: DS17 shock model line ratio diagrams), whilst the \[N II\]/\[S II\] ratio is consistent with shock speeds of $v_s \approx 55 \,\rm km\,s^{-1}$ and a pre-shock density of $n = 1\,\rm cm^{-3}$, shocks of this speed do not generate any measurable \[O III\] emission. Rather, the measured \[O III\]/H$\upbeta$ ratios are consistent with $v_s \gtrapprox 70 \,\rm km\,s^{-1}$; shocks of this speed over-predict the observed \[N II\]/\[S II\] ratios by a factor $\approx 2-3$. Similarly, none of the fast shock models of (cite: Allen2008) would produce the enhanced \[S II\]/H$\upalpha$ and \[O I\]/H$\upalpha$ line ratios whilst keeping the \[N II\]/H$\upalpha$ within the range of observed values.

![](fig11.pdf)

Although simultaneously low \[N II\]/H$\upalpha$ and high \[O III\]/H$\upbeta$ could theoretically arise from a mixture of shock speeds resulting from the shock passing through an inhomogeneous medium, any significant contribution from shocks sufficiently fast to cause detectable \[O III\] would produce much higher line widths than observed ($\sigma \lessapprox 30 \,\rm km\,s^{-1}$; see Fig [5](#fig: paper 3: Halpha kinematics and morphology)). We therefore conclude that shocks are highly unlikely to be the primary cause of the enhanced \[S II\]/H$\upalpha$ and \[O I\]/H$\upalpha$ ratios. However, we cannot rule out the presence of shocks that are too slow to contribute to the optical line emission. Further observations in the near-IR may reveal ro-vibrational H~2~ emission, which traces shocks too slow to dissociate molecular gas (cite: Flower&PineauDesForets2010; Zovaro2019a; Zovaro2019b).

### Diffuse Ionised Gas

We now investigate whether the line ratios in MO are consistent with contamination from diffuse ionised gas (DIG), the low-density ionised medium outside H II regions that is photoionised by escaped radiation from nearby star-forming regions. DIG is characterised by strong emission in low-ionisation species such as \[O I\], \[N II\] and \[S II\], and weak emission in high-ionisation species such as \[O III\] (cite: Rand1998; Haffner2009).

The diffuse structure of MO implies that DIG is highly likely to contribute to the line emission, particularly in the regions in between the filaments visible in *HST* imaging (see the bottom panel of Fig. [2](#fig: paper 3: HST overlay)). Indeed, as shown in Fig. [9](#fig: paper 3: S2 ratio spatial distribution), the spaxels with the highest \[S II\]/H$\upalpha$ ratios are located away from the brightest star forming regions, and in the areas away from the bar and in between the filaments, as expected of DIG.

In Fig. [12](#fig: paper 3: ODD w. DIG models) we present a ODD diagram overlaid with the DIG photoionisation models of (cite: Mathis1986), where the \[O I\]$\uplambda 6300$/H$\upalpha$ ratio has been replaced by the \[O II\]$\uplambda 3726$/H$\upbeta$ ratio because \[O I\]$\uplambda 6300$ is not included in the models. The DIG models are parametrised by the temperature $T_*$ of the central O-type star in the model H II region, and the parameter $q$, which is a proxy for the ionisation parameter; $q \approx 1$ in regular H II regions, whereas for the models used here, $-6 \leq q \leq -2$. The spaxels with line ratios most similar to the DIG models tend to have low H$\upalpha$ surface brightnesses and lie outside the main star-forming regions round the outskirts of the object, or in between the filaments (see Fig. [5](#fig: paper 3: Halpha kinematics and morphology)), as expected for DIG. However, the models are unable to explain the enhancement in the \[S II\] relative to the \[N II\] and \[O II\]. We therefore rule out DIG as the main contributor to the unusual line ratios in MO.

![](fig12.pdf)

### X-ray photoionisation

We now consider whether X-ray photoionisation from the nucleus of NGC 541 can explain the observed line ratios. X-ray photons produced via inverse Compton scattering in the corona of the AGN have a long mean-free-path length in the ISM, resulting in a very hard radiation field in the outskirts of the nebula that creates an extended, weakly ionised transition region (cite: Dopita&Sutherland2003). Although this region has a low ionisation parameter, inner-shell photoionisations from X-ray photons create high-energy electrons that trigger cascades of collisional excitations, leading to enhanced forbidden line emission in species with ionisation potentials lower that that of H I. In particular, \[S II\] and \[O I\] are enhanced, whereas \[N II\] and \[O III\] are relatively weak, as is the case in MO.

Due to enhanced collisional excitation, X-ray photoionisation results in a Balmer decrement larger than the case B recombination value of 2.85 (cite: Dopita&Sutherland2003). Therefore, if X-ray photoionisation from the AGN of NGC 541 is the dominant secondary excitation mechanism, the $A_V$, which was estimated assuming the case B recombination Balmer decrement, will be correlated with the S2 ratio, which is indeed observed (see Figs. [6](#fig: paper 3: reddening) and [9](#fig: paper 3: S2 ratio spatial distribution)).

Due to its significant distance from the AGN, existing AGN photoionisation models, which generally simulate nebulae close to the AGN in the host galaxy, cannot be applied to MO.

A program such as MAPPINGS (cite: Sutherland2018) can be used to simulate a photoionised nebula placed an arbitrary distance from the AGN, where the AGN SED can be simulated using existing models (cite: Jin2012). However, such models require numerous parameters to constrain the properties of the nebula and AGN SED, many of which cannot be reliably estimated from existing observations of MO and NGC 541.

Hence, determining whether AGN photoionisation can reproduce the observed line ratios in MO requires a detailed exploration of the model parameter space, which will be the subject of future work.

In conclusion, star formation most likely dominates the line emission in MO, but the enhanced \[S II\]/H$\upalpha$ and \[O I\]/H$\upalpha$ ratios indicate the presence of other additional ionising sources. Neither shock nor DIG models can simultaneously produce the enhanced \[S II\]/H$\upalpha$ and \[O I\]/H$\upalpha$ ratios whilst keeping the \[N II\]/H$\upalpha$ ratios within the range of observed values. X-ray photoionisation from the AGN of NGC 541 may contribute, but further modelling is required to confirm this. Given the unusual location and structure of MO, it is possible that the observed line ratios may be a result of gas photoionised by a combination of star formation, AGN and DIG, which is then shocked by the passage of the jet. Modelling such a complex system is beyond the scope of this paper; additional observations will be required to constrain the free parameters in such a model.

The presence of both an intrinsic metallicity variation, and possible ionisation from a range of sources other than star formation, makes MO too complex for us to quantify the contribution of shocks, DIG or AGN photoionisation to the line emission using a simple ‘mixing’ analysis (cite: Davies2017). However, (cite: Kewley&Ellison2008) found that only an AGN photoionisation contribution greater than $15 \,\rm per \, cent$ can produce line ratios lying above the maximum starburst line of (cite: Kewley2001) in all three ODDs shown in Fig. [7](#fig: paper 3: ODD diagrams). Since the harder radiation fields of AGN have a similar effect on the line ratios as shocks and DIG, and because there are very few spaxels with line ratios above the maximum starburst line by greater than $1\sigma$, we therefore place an upper limit of $15 \,\rm per \, cent$ on the contribution of non-stellar ionisation sources in MO.

## Star formation rate

We calculated the global SFR using the same calibration used by (${\rm SFR(H\upalpha)} = (7.0 - 7.9) \times 10^{-42}L( {\rm H\upalpha})$), which has a systematic uncertainty of approximately $30 \rm \, per \, cent$ due to uncertainty in the shape of the IMF at the high-mass end. Using the total H$\upalpha$ flux gives $\rm SFR = 0.28 \pm 0.09 \,\rm M_\odot\,yr^{-1}$. As discussed in Section [6.5](#subsec: paper 3: Excitation mechanism), the H$\upalpha$ flux is mildly contaminated by shocks, DIG and/or X-ray photoionisation; hence this should be treated as an upper limit. We therefore estimate a conservative lower limit by assuming 15 per cent of the H$\upalpha$ flux is due to ionisation sources other than star formation, yielding a SFR in the range $(0.24-0.28) \pm 0.09 \,\rm M_\odot\,yr^{-1}$.

This corresponds to a H I depletion time $t_{\rm dep, \, H\,I} \sim 1.7 - 2.0 \,\rm Gyr$ . Using the reported H~2~ masses of using $\alpha_{\rm CO}$ values appropriate for half-solar- and MW-like metallicity galaxies yields H~2~ depletion times of $t_{\rm dep, \, H_2} \sim 0.64 - 0.75 \, \rm Gyr$ and $t_{\rm dep, \, H_2} \sim 0.11 - 0.12 \, \rm Gyr$ respectively.

Our SFR estimate and total H$\upalpha$ flux ($\left(4.79 \pm 0.1\right) \times 10^{-14}\rm\,erg\,s^{-1}\,cm^{-2}$) are approximately half that of ($0.5 \,\rm M_\odot \, yr^{-1}$ and $8.6 \times 10^{-14}\rm\,erg\,s^{-1}\,cm^{-2}$ respectively). The reason for this discrepancy is unclear. Our flux estimate is closer to that of (cite: vanBreugel1985), who reported a combined H$\upalpha$+\[N II\] flux of $3.2 \times 10^{-14} \rm\, erg \, s^{-1} \, cm^{-2}$.

claimed that the recent type-II supernova (SN) explosion 2010ib (cite: 2010CBET.2464....1C; 2010CBET.2490....2G) is evidence that MO may have a top-heavy IMF due to the improbability of observing a SN explosion in an object with such a low SFR. However, the best-fit star formation history (SFH) from our PPXF analysis (Section [5](#sec: paper 3: Stellar population analysis)) indicates that the majority of the stellar mass formed during a period of $\sim 1-2 \,\rm Myr$ approximately $10^7 \,\rm yr$ ago, during which the SFR would have been much greater than the present-day value. Modelling MO as a solar metallicity $10^7\,\rm M_\odot$ SSP with an instantaneous burst SFH and a Salpeter IMF using STARBURST99 (cite: Leitherer1999), the expected SN rate at $10^7\,\rm yr$ is approximately $0.03 \,\rm yr^{-1}$, corresponding to one SN explosion every $\sim 30\,\rm yr$. Therefore, SN explosion 2010ib is consistent with MO having a conventional IMF.

## Metallicity and ionisation parameter

We followed the iterative method of (cite: Kewley&Dopita2002) to simultaneously estimate the gas-phase oxygen abundance $\log\left( \rm O / H \right) + 12$ (henceforth referred to as metallicity) and dimensionless ionisation parameter $\log\left(U\right)$ in each spaxel using the theoretical diagnostics provided by (cite: KewleyNichollsSutherland2019) assuming a constant pressure $\log(P/k) = 5.0$, which is appropriate for typical H II regions.

Strong-line abundance and ionisation parameter diagnostics are derived from models of standard H II regions, and may yield spurious results if the line emission is contaminated by processes other than star formation. As discussed in Section [6.5](#subsec: paper 3: Excitation mechanism), we estimate the contribution to the line emission from sources other than star formation to be less than $15 \,\rm per \, cent$. At this level, (cite: Kewley&Ellison2008) found that the N2O2 (\[N II\]$\uplambda\uplambda 6548,6583$/\[O II\]$\uplambda\uplambda 3726,3729$) metallicity diagnostic is robust to contamination from AGN photoionisation. We expect the harder radiation fields from shocks and DIG to have a similar effect on the \[N II\]/\[O II\] ratio. If this is the case, then the N2O2 diagnostic can be used reliably in MO; however, we note that our metallicity estimates are uncertain because we are unable to quantify the amount of contamination from sources other than star formation.

The bottom panel of Fig. [13](#fig: paper 3: metallicity & ionisation parameter) shows $\ensuremath{\log\left(U\right)}{}$ estimated using the O3O2 (\[O III\]$\uplambda\uplambda 4959,5007$/\[O II\]$\uplambda\uplambda 3726,3729$) diagnostic of (cite: KewleyNichollsSutherland2019). The typical uncertainty in each spaxel is $0.02 \,\rm dex$. In most parts of the object $\ensuremath{\log\left(U\right)}{} \approx -3.0$, which is consistent with the finding of ; however, $\ensuremath{\log\left(U\right)}{} \approx -2.0$ in some regions, exceeding the values found in typical H II regions.

The top panel of Fig. [13](#fig: paper 3: metallicity & ionisation parameter) shows the metallicity estimated using the N2O2 metallicity diagnostic. The typical uncertainty in each spaxel is $0.01 \,\rm dex$. There is significant variation in the metallicity across the object, with the lowest-metallicity regions lying near the Eastern and Western edges of the object, and $\ensuremath{\log\left( \rm O / H \right) + 12}{}$ increasing by up to $\sim 0.5\,\rm dex$ in the centre. Metallicity estimates using other diagnostics including the N2 (\[N II\]$\uplambda 6583$/H$\upalpha$), O2S2 (\[O II\]$\uplambda \uplambda 3726,3729$/\[S II\]$\uplambda \uplambda 6716,6731$), O3N2 ((\[O III\]$\uplambda 5007$/H$\upbeta$)/(\[N II\]$\uplambda 6583$/H$\upalpha$)) and R23 ((\[O II\]$\uplambda \uplambda 3726,3729$ + \[O III\]$\uplambda \uplambda 4959,5007$)/H$\upbeta$) are presented in Appendix [11](#appendix: Additional metallicity diagnostics), revealing similar metallicity variations within the object. The magnitudes of the measured metallicity variations for the N2O2, R23, O2S2, N2 and O3N2 diagnostics are 0.55 dex, 0.43 dex, 0.62 dex, 0.33 dex and 0.36 dex respectively; we note that diagnostics other than N2O2 are more susceptible to contamination from sources other than star formation, and may therefore under- or over-estimate the intrinsic variation in $\log\left( \rm O / H \right) + 12$.

We caution that strong-line diagnostics do not provide accurate estimates of the absolute metallicity due to systematic uncertainties associated with the models used to derive these diagnostics (cite: Kewley&Ellison2008; Kewley2019). This effect is apparent from the significant variations in the absolute metallicities produced by the different diagnostics. None the less, these diagnostics can be used to provide accurate estimates of the variation in $\log\left( \rm O / H \right) + 12$ within the object.

As noted previously, contamination from sources other than star formation may bias our metallicity estimates. As shown in Fig. [7](#fig: paper 3: ODD diagrams), the N2O2 metallicity is strongly correlated with the S2 ratio. Comparison of Fig. [9](#fig: paper 3: S2 ratio spatial distribution) and Fig. [13](#fig: paper 3: metallicity & ionisation parameter) also shows that the higher-metallicity and higher-S2 regions are located away from the main star-forming regions, and would therefore have line ratios more strongly contaminated by processes other than star formation. It is therefore possible that the metallicity is being over-estimated in these regions.

![image](fig13a.pdf) ![image](fig13b.pdf)

# Possible explanations for the metallicity variation

In this section, we explore several scenarios that could produce the large metallicity variation observed within MO.

## Enrichment from star formation

Star formation proceeding from SE-NW could potentially cause the metallicity variation, as regions with more recent star formation would have had less time to enrich the ISM with metals via supernova explosions and stellar winds. Although we were unable to spatially resolve MO in our PPXF analysis (Section [5](#sec: paper 3: Stellar population analysis)), the global best-fit stellar population is dominated by a young population $\lesssim 10\,\rm Myr$ old, with a spread of only $1-2$ Myr (Fig. [4](#fig: paper 3: ppxf integrated fit, age & metallicity)).

To determine whether an age spread of a few Myr in the stellar population could explain the observed metallicity variation, we used an SSP model to estimate the oxygen yield per stellar mass for stars of a given age and metallicity. The SSP model considers enrichment contributions from various channels. Yields from type II supernovae (cite: Kobayashi2004) are calculated as a function of age and metallicity, where the age determines the main-sequence turn off mass using the metallicity-dependent lifetimes of (cite: Kodama&Arimoto1997). A metallicity-dependent hypernova (HN) fraction is also included, with a greater contribution from HN at low metallicity (cite: Kobayashi&Nakasato2011). Winds from asymptotic giant branch stars further contribute (cite: Kobayashi2011). Type Ia supernovae are included in the model (cite: Kobayashi&Nomoto2009), but do not contribute on the short timescales considered here. We assume a (cite: Kroupa2001) IMF (slope $\alpha = 1.3$) in the range $0.01-120\,\rm M_\odot$, with an upper mass limit for core-collapse supernovae of $50\,\rm M_\odot$.

As shown in Fig. [14](#fig: paper 3: MO yield), for stellar metallicities $\geq 0.1 \,\rm Z_\odot$ (consistent with the gas-phase metallicity), the oxygen yield increases by only a factor of 2 over a period of 5 Myr, insufficient to explain the metallicity enhancement of $\sim 0.5 \,\rm dex$ in the centre of the object. Stellar enrichment alone is therefore unable to explain the metallicity variation.

![](fig14.pdf)

## An enriched jet-driven outflow from NGC 541

A metallicity variation in MO could have arisen if some of the gas from which it formed originated in a jet-driven outflow from NGC 541. X-ray studies of clusters have revealed metallicity enhancements of up to 0.2 dex occurring along the path of jets from BCGs (cite: Kirkpatrick2009; Kirkpatrick2011), indicating that jets can transport enriched material up to several $100\,\rm kpc$ from the host. Hence it is plausible for enriched gas to be found along the jet of NGC 541. However, it is highly unlikely that any metal-enriched gas from NGC 541 would become bound to MO given its very low stellar mass ($\sim 10^7 \,\rm M_\odot$). We therefore rule out this scenario.

## Pre-existing enriched gas in the stellar bridge

MO may have formed from dense clumps of gas residing in the stellar bridge connecting NGC 541 and NGC 545/547, as we discuss further in Section [8](#sec: paper 3: On the formation of Minkowski's Object). This gas will have been stripped from the interacting galaxies, and would therefore be enriched relative to the ICM. Moreover, the recent type Ia supernova explosion 2018ctv (cite: 2018ATel11762....1C; 2018ATel12313....1M; 2018ATel12315....1P) in the stellar bridge indicates ongoing stellar enrichment in the ICM of Abell 194.

To check whether this is plausible, we compared the gas-phase metallicities in MO and in NGC 541. (cite: Hamer2016) observed NGC 541 with VLT/VIMOS and obtained spatially resolved emission line fluxes, which we used to estimate the gas-phase metallicity.

Due to the limited number of emission lines in the wavelength range of their observations, we used the N2 diagnostic, adopting a fiducial $\ensuremath{\log\left(U\right)}{} = -3.0$, appropriate for normal H II regions. The metallicity in the outer regions of NGC 541 ($\ensuremath{\log\left( \rm O / H \right) + 12}\approx 8.8$) is approximately 0.2 dex higher than that observed in MO using the same diagnostic (see Appendix [11](#appendix: Additional metallicity diagnostics)), meaning that the ISM in NGC 541 is sufficiently enriched to explain the high observed metallicities in MO. However, this scenario cannot explain the metallicity variation of 0.5 within the object. Moreover, the N2 diagnostic is subject to contamination by the AGN; further observations of NGC 541 are therefore required to observe emission lines enabling us to apply a metallicity diagnostic more robust to AGN contamination, such as N2O2.

Having ruled out star formation, an enriched jet-driven outflow and enrichment of gas in the stellar bridge as the cause of the metallicity variation, its origin is uncertain, although we note that the magnitude of the variation may be over-estimated due to contamination from sources other than star formation.

# On the formation of Minkowski’s Object

Here, we discuss possible scenarios for the formation of MO.

suggest that MO formed from the hot, tenuous ICM that underwent runaway cooling due to shocks induced by the passage of the jet. However, simulations by (cite: Fragile2004) suggest that MO would have required a pre-collision cloud density of approximately $10 \,\rm cm^{-3}$ to form via a jet interaction. This density is substantially higher than estimated ICM densities in local clusters (cite: Mohr1999); it therefore appears unlikely that MO formed directly from the ICM. MO may instead have formed from pre-existing dense clouds in the path of the jet. As shown in Fig. [1](#fig: paper 3: Abell 194), Abell 194 harbours a stellar bridge connecting NGC 541 and NGC 545/547, which is aligned with the jet from NGC 541 in projection. The stellar bridge may contain H I stripped from the interacting galaxies, akin to the intra-group H I observed in groups such as Stephan’s Quintet (cite: Sulentic2001). MO is indeed associated with a large H I cloud with mass $4.9 \times 10^8 \,\rm M_\odot$; such pre-existing H I may have been sufficiently dense for jet-induced star formation to occur.

One of the only other known examples of jet-induced star formation, the string of OB associations in the Northern jet of Centaurus A, is believed to have formed due to a jet interaction with an H I cloud that drifted into the jet’s path. Crucially, this cloud has been detected *outside* the jet’s path, and appears to be part of a larger ring of H I clouds that may have formed during a past merger event (cite: Schiminovich1994; Oosterloo&Morganti2005), indicating that this gas existed prior to the jet interaction. In contrast, all of the H I associated with MO is spatially coincident with the jet; claim this is evidence that the jet triggered the formation of the cloud. However, remark that additional H I could exist at velocities outside the low bandwidth ($500 \,\rm km\,s^{-1}$) of their observations, and that the H I cloud may be part of a larger pre-existing H I complex.

We note that although MO harbours 2–10 times the molecular gas mass of the Cen A filaments ($1.4 \times 10^7 \,\rm M_\odot$ in the Cen A filaments, (cite: Charmandaris2000); $(0.3 - 1.8) \times 10^8 \,\rm M_\odot$ in MO, ), the Cen A filaments have a total $\rm SFR = 4 \times 10^{-3}\,\rm M_\odot \, yr^{-1}$ (cite: Salome2016a), almost 100 times lower than that of MO. It is unclear why the star-formation efficiency should differ so drastically between the two objects. Unfortunately, as discussed in Section [6.7](#subsec: paper 3: Metallicity and ionisation parameter), we are unable to further constrain the molecular gas of MO mass with an updated CO-to-H~2~ conversion factor because we cannot reliably estimate the absolute gas-phase metallicity from our observations. The true star formation efficiency of MO therefore remains unclear, although we note that our new SFR estimate, which is approximately half that of , places MO significantly closer to the Kennicutt-Schmidt relation (cite: Kennicutt1998) regardless of the assumed $\alpha_{\rm CO}$ .

A second possibility is that MO formed from pre-existing filaments in the ICM. H$\upalpha$-emitting filaments are regularly observed in cool-core clusters, and may trace cooling gas flowing into the BCG (cite: Heckman1989). Many filaments exhibit line emission with LINER-like line ratios, attributed to in-situ star formation and shocks (cite: McDonald2012). Jet-induced shocks could lead to enhanced star formation in these filaments. However, it seems unlikely that Abell 194 would harbour such filaments, because it lacks the localised, enhanced X-ray emission associated with cooling gas (cite: Nikogossyan1999; Sakelliou2008). Moreover, these filaments generally exhibit $\log($\[N II\]$\uplambda 6583$/H$\upalpha$$) \sim -0.5 - 0.5$, much higher than observed in MO ($\log($\[N II\]$\uplambda 6583$/H$\upalpha$$) \sim -1$), in addition to much broader line widths (cite: Heckman1989; Sabra2000; Farage2010; McDonald2012; Hamer2015). We therefore conclude that it is unlikely for MO to have formed from such filaments.

The final scenario we consider is that MO is a gas-rich dwarf galaxy that is currently falling into Abell 194, and has a temporarily elevated SFR due to the jet interaction. In recent years, a population of isolated H I-rich ultra-diffuse dwarf galaxies (HUDs) have been discovered, characterised by blue colours, extended ($\sim 10-30 \,\rm kpc$) clumpy morphologies and high gas fractions, with $M_{\rm H\,I} \sim 10^8 - 10^9 \,\rm M_\odot$ and $M_* \sim 10^7 - 10^8 \,\rm M_\odot$ (cite: Leisman2017), similar to MO. However, with a surface brightness $\mu_g = 21.8 \,\rm mag \, arcsec^{-2}$, MO is much brighter than most HUDs, which by definition have $\mu_g \geq 24 \,\rm mag \, arcsec^{-2}$. If MO truly originated from a HUD, its current surface brightness may be temporarily elevated due to jet-induced star formation.

Under this formation scenario, we may speculate on the fate of MO. As they fall into clusters, gas-rich dwarfs are predicted to rapidly lose their gas due to ram-pressure stripping or tidal interactions, eventually transforming into ultra-diffuse galaxies (cite: Leisman2017; Roman&Trujillo2017): extended, low surface-brightness, quiescent galaxies which are numerous in local clusters (cite: vanDokkum2015; Koda2015).

To model the quenching of MO as it falls into Abell 194, we used a STARBURST99 (cite: Leitherer1999) solar metallicity SSP model with a Salpeter IMF and an instantaneous SFH. Given the present-day $V$ band surface brightness of $\mu_V = 22.7 \,\rm mag \, arcsec^{-2}$, we predict MO to fade to $\mu_V = 24.2 \,\rm mag \, arcsec^{-2}$ and $\mu_V = 25.7 \,\rm mag \, arcsec^{-2}$ in approximately 100 Myr and 1 Gyr respectively, firmly placing MO into the surface brightness regime of ultra-diffuse galaxies. The correspondingly low stellar mass surface densities suggests that MO will eventually become disrupted as it falls into the cluster.

If MO is truly a gas-rich dwarf that has wandered into the path of the jet, we may be observing it during a brief phase where it is bright enough to see in shallow observations. It is therefore possible that there are many objects similar to MO that have now faded, and that MO is perhaps not as unique as is currently believed.

Establishing whether MO resides in its own dark matter (DM) halo would enable us to distinguish between these different formation scenarios. If MO formed from the ICM, then it would not be associated with a DM halo, whereas ultra-diffuse galaxies are known to span a range of DM halo masses (cite: Zaritsky2017). Unfortunately, the irregular morphology of MO makes it difficult to measure its inclination using our WiFeS observations, meaning we cannot constrain the gravitational mass of MO from its rotation curve. Further observations and modelling of MO and Abell 194 will be required to distinguish between these different formation scenarios.

# Conclusion

We conducted a study of Minkowski’s Object (MO), an peculiar star-forming dwarf galaxy located along the path of a jet from the nearby radio galaxy NGC 541, using optical integral field spectroscopy.

Analysis of the stellar continuum with PPXF confirms that MO is dominated by a predominantly young stellar population $\sim 10\,\rm Myr$ old, indicating that the bulk of its stellar mass formed during a recent jet interaction. A secondary population at $\sim 1 \,\rm Gyr$ is also present, and may represent stars in the stellar bridge between NGC 541 and NGC 545/547 or a pre-existing stellar population associated with MO.

In most parts of the object, the emission line ratios are consistent with star formation, although some regions exhibit enhanced \[S II\]/H$\upalpha$ and \[O I\]/H$\upalpha$ ratios suggesting the presence of non-stellar ionising sources. A complex combination of shocks, DIG and X-ray photoionisation from the AGN of NGC 541 may explain the line ratios, although further modelling is required to determine whether this is plausible.

Strong-line metallicity diagnostics indicate a gas-phase metallicity that varies by $\sim 0.5\,\rm dex$ across the object, which cannot be explained by enrichment from in-situ star formation, enriched gas entrained in the jet from NGC 541, nor the presence of pre-existing enriched gas in the stellar bridge, although we note the magnitude of the variation may be over-estimated due to contamination from sources other than star formation.

We explored several formation scenarios for MO, and concluded that it formed from either (a) pre-existing H I clouds in the stellar bridge between NGC 541 and NGC 545/547 that were stripped from these galaxies during an interaction or (b) a gas-rich dwarf galaxy that wandered into the path of the jet. Further observations and modelling may enable us to distinguish between these two scenarios.

# Acknowledgements

The authors would like to thank Julie Banfield for leading the initial observing programme, Adam D. Thomas for providing assistance with NEBULABAYES, and Chiaki Kobayashi for assistance with the SSP chemical enrichment modelling. We also thank the anonymous reviewer for their insightful comments and suggestions which have improved this work.

This research has made use of the NASA/IPAC Extragalactic Database, which is funded by the National Aeronautics and Space Administration and operated by the California Institute of Technology.

This research made use of QFitsView[^4], a software package for reducing astronomical data written by Thomas Ott, and the PYTHON packages NUMPY[^5] (cite: Harris2020), SCIPY[^6] (cite: Scipy2001), and ASTROPY,[^7] a community-developed core package for Astronomy (cite: Astropy2013; Astropy2018).

Model generated with SED@.0 code[^8] with the following inputs: IMF from (cite: Salpeter1955) in the mass range $0.1-120 \rm\, M_\odot$; High Resolution library from (cite: Martins2004; GonzalezDelgado2005) based on atmosphere models from PHOENIX (cite: Hauschildt&Baron1999; Allard2001), ATLAS9 (cite: Kurucz1991) computed with SPECTRUM (cite: Gray&Corbally1994), ATLAS9 library computed with SYNSPEC (cite: Hubeny&Lanz2011), and TLUSTY (cite: Lanz&Hubeny2003). Geneva isochrones computed with the isochrone program presented in (cite: Meynet1995) and following the prescriptions quoted in (cite: Cervino2001) from the evolutionary tracks from (cite: Schaller1992) at $Z=0.001$/$Z=0.020$; (cite: Charbonnel1993) at $Z=0.004$; (cite: Schaerer1993a) at $Z=0.008$ and (cite: Schaerer1993b) at $Z=0.040$. Padova isochrones presented in (cite: Girardi2002)[^9] based on the (solar scaled mixture) tracks from (cite: Girardi2000; Bertelli1994) that includes overshooting and a simple synthetic evolution of TP-AGB (cite: Girardi&Bertelli1998).

Parts of this research were supported by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. L. J. K. gratefully acknowledges the support of an ARC Laureate Fellowship (FL150100113).

# Data availability

The data underlying this article will be shared on reasonable request to the corresponding author.

# Additional PPXF fits

In Fig. [15](#fig: A4: ppxf integrated fit, age & metallicity (Padova)) we show the histogram and spectrum of the best-fit combination of stellar templates generated using PPXF with Padova isochrones. The results are very similar to those obtained using the Geneva isochrones.

We also repeated our analysis using stellar templates with constant metallicity using both the Geneva and Padova isochrones. The best-fit SFHs, shown in Fig. [16](#fig: A4: ppxf 1D fits), are similar regardless of the metallicity and isochrones used.

![image](figA1a.pdf) ![image](figA1b.pdf)

![image](figA2a.pdf) ![image](figA2b.pdf)

# Additional metallicity diagnostics

Fig. [17](#fig: A3: metallicity & U) shows the gas-phase metallicity (left column) and ionisation parameter (right column) estimated using the O2S2, R23, N2 and O3N2 metallicity diagnostics and the O3O2 ionisation parameter diagnostic of (cite: KewleyNichollsSutherland2019).

![image](figB1a.pdf) ![image](figB1b.pdf) ![image](figB1c.pdf) ![image](figB1d.pdf) ![image](figB1e.pdf) ![image](figB1f.pdf) ![image](figB1g.pdf) ![image](figB1h.pdf)

# Estimation of shock velocities

Because the jet impacting MO is an FR I jet, the usual approximations derived from a hypersonic or supersonic jet impacting a relatively dense medium (cite: Blandford&Rees1974) are not appropriate. In this appendix, we develop an estimate for the cloud shock velocity resulting from the impact of a transonic jet on a relatively dense cloud.

The dynamical setting, which is a classic shock tube configuration (cite: Landau1987) is indicated in Figure [18](#fig: A4: shock tube). The jet pressure and density are $p_1$ and $\rho_1$, and the cloud pressure and density are $p_2$ and $\rho_2$. The shock pressure for both the jet terminus and the shocked cloud is $p_3$, the shocked jet density is $\rho_3$ and the shocked cloud density is $\rho_3^\prime$. In the following we assume that, initially, both the cloud and jet are in pressure equilibrium with the interstellar medium so that $p_1 \approx p_2$. The pressure difference $p_3-p_1$ is denoted by $\Delta p$; we cannot assume that $\Delta p \gg p_1$. The polytropic indices for jet and cloud are $\gamma_1$ and $\gamma_2$ respectively, and the velocities of the jet and cloud in the frame of the contact discontinuity are $v_1$ and $v_2$, respectively.

![](figC1.pdf)

The frame-independent relative velocity between jet and cloud is $$\begin{equation}
\Delta v = v_{\rm jet} + v_{\rm infall}
\end{equation}$$ where $v_{\rm jet}$ and $v_{\rm infall}$ are respectively the jet velocity and infall velocity of MO in the frame of the radio galaxy NGC 541. For the shock tube analysis: $$\begin{equation}
\Delta v = v_1 - v_2
\end{equation}$$ where $v_1$ and $v_2$ are respectively the jet velocity and cloud velocity in the frame of the contact discontinuity separating the jet and cloud gas. We have: $$\begin{eqnarray}
\Delta v = v_1 - v_2 = && \left( \frac {2}{\rho_1} \right)^{1/2} \>
\frac {p_3-p_1}{\left[ (\gamma_1-1) p_1 + (\gamma_1+1)p_3 \right]^{1/2}} 
\nonumber \\
+ && \left( \frac {2}{\rho_2} \right)^{1/2} \>
\frac {p_3-p_2}{\left[ (\gamma_2-1) p_2 + (\gamma_2+1)p_3 \right]^{1/2}}
\end{eqnarray}$$ Because the cloud density $\rho_2$ is much greater than the jet density $\rho_1$, we neglect the second term in this expression and write: $$\begin{equation}
\Delta v = \left( \frac {2}{\rho_1} \right)^{1/2} \>
\frac {\Delta p}{\left[ 2 \gamma_1 p_1 + (\gamma_1+1) \Delta p \right]^{1/2}} 
\label{e:delta_v}
\end{equation}$$ Defining the Mach number, corresponding to $\Delta v$, by $M_1 = (\gamma_1 p_1/\rho_1)^{-1/2} \Delta v$ the solution of Eqn. [\[e:delta_v\]](#e:delta_v) for $\Delta p$ is $$\begin{equation}
\frac {\Delta p}{p_1} = \frac {\gamma_1 (\gamma_1+1)}{2} M_1^2 f(M_1) 
\label{delta_p}
\end{equation}$$ where $$\begin{eqnarray}
f(M_1) &=& \frac {1}{2} \left\lbrace 1 + \left[ 1 + \frac {16}{(\gamma_1+1)^2} M_1^{-2}  \right]^{1/2}\right\rbrace \label{f(M1)}\\
&\rightarrow& 1 \quad \hbox{for} M_1 \gg 1
\end{eqnarray}$$

It follows from the Rankine Hugoniot relations that the velocity of the shock propagating from region $3^\prime$ to region 2 (i.e. the cloud shock) is given by: $$\begin{equation}
v_{\rm sh,cl}^2 = \frac {1}{2 \rho_2} \left[  (\gamma_2-1)p_2 + (\gamma_2+1) p_3 \right] 
\end{equation}$$ and for $p_1=p_2$ $$\begin{equation}
v_{\rm sh}^2 = c_{\rm s,2}^2\left[ 1 + \frac{(\gamma_2+1)}{2 \gamma_2} \frac{\Delta p}{p_1} \right]
\end{equation}$$ where $c_{\rm s,2}$ is the adiabatic sound speed in the cloud.

Using Eqn. [\[delta_p\]](#delta_p) for $\Delta p$, we have for the velocity of the cloud shock $$\begin{equation}
v_{\rm sh,cl} = 
c_{\rm s,2} M_{\rm sh,cl} 
\label{v_shock}
\end{equation}$$ where the shock Mach number $$\begin{equation}
M_{\rm sh,cl} = \left[ 1 + \frac {\gamma_1 (\gamma_1 +1)(\gamma_2+1)}{4 \gamma_2}  M_1^2 f(M_1) \right]^{1/2}
\end{equation}$$ and $f(M_1)$ is given by Eqn. [\[f(M1)\]](#f(M1)) above. $M_{\rm sh,cl}$ is always greater than unity, but $\sim 1$, for low $M_1$.

In terms of the temperature, $T_2$, of the cloud, the shock velocity is $$\begin{eqnarray}
v_{\rm sh, cl}&=& \left( \frac {k T_2}{\mu m} \right)^{1/2}
M_{\rm sh,cl} \\
&\approx& 15 \> \left(\frac {T_2}{10^4}\right)^{1/2}
M_{\rm sh,cl} \quad \rm km \> s^{-1}
\end{eqnarray}$$ where $\mu \approx 0.62$ is the molecular weight and $m \approx 1.66 \times 10^{-24} \rm \> gm$ represents an atomic mass unit.

For jet Mach numbers $=(1,2,3)$ the values of $M_{\rm sh, cl} \approx (1.7, 2.6, 3.6)$. Hence, attributing the velocity dispersion in Minkowski’s Object to a population of shocks, driven by a transonic ($M_1 \sim 1-2$) jet, it is apparent that a velocity dispersion $\leqslant 20 \> \rm km \> s^{-1}$ would arise for cloud temperatures $\sim 10^3 - 10^4 \> \rm K$ and a jet Mach number $\sim 1-2$.

The velocity dispersion resulting from such slow shocks are consistent with those measured in the H I cloud associated with MO . Although they are also consistent with those observed in the ionised gas (see Fig. [5](#fig: paper 3: Halpha kinematics and morphology)), we note that the resultant velocity dispersions are similar to those of H II regions where the line widths are driven by internal processes (cite: Rozas2006). Hence we cannot attribute the observed line widths in our WiFeS observations to these shocks, although it does indicate that the jet does not significantly increase the turbulent velocities in the ionised gas.

[^1]: E-mail: henry.zovaro@anu.edu.au

[^2]: Available <https://www-astro.physics.ox.ac.uk/~mxc/software/#ppxf>.

[^3]: Available <http://cars9.uchicago.edu/software/python/mpfit.html>.

[^4]: <https://www.mpe.mpg.de/~ott/QFitsView/>

[^5]: <https://numpy.org/>

[^6]: <http://www.scipy.org/>

[^7]: <http://www.astropy.org>

[^8]: SED@ is a synthesis code included in the *Legacy Tool project* of the *Violent Star Formation Network*; see *SED@ Reference Manual* at <http://www.iaa.es/~mcs/sed@> for more information.

[^9]: Available at <http://pleiadi.pd.astro.it/>

</paper>

Write the methods card for this paper.