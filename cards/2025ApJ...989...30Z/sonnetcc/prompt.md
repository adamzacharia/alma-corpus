# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...989...30Z\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...989...30Z",
 "title": "SO Emission in the Dynamically Perturbed Protoplanetary Disks around CQ Tau and MWC 758",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Zagaria, Francesco",
 "n_authors": 28,
 "arxiv_id": "2506.16481",
 "doi": "10.3847/1538-4357/ade683",
 "alma_projects_linked_by_archive": [
  "2013.1.00498.S",
  "2016.A.00026.S",
  "2017.1.00940.S",
  "2017.1.01404.S"
 ]
}
```

Paper text:
<paper>
# SO emission in the dynamically perturbed protoplanetary disks around CQ Tau and MWC 758

## Abstract

We report the serendipitous detection of the SO $J_N=6_5-5_4$ (219.949 GHz) rotational transition in archival Atacama Large Millimeter/submillimeter Array (ALMA) observations of the spiral hosting protoplanetary disks around CQ Tau (with $\approx4.9\sigma$ significance) and MWC 758 (with $\approx3.4\sigma$ significance). In the former, the SO emission comes in the shape of a ring, arises from the edge of the continuum cavity, and is qualitatively consistent, at the currently available spectral resolution, with being in Keplerian rotation. In the latter, instead, while arising primarily from inside the continuum cavity , the SO emission also extends to the continuum ring(s) and its morphology and kinematics are less clear. We put these sources in the context of the other protoplanetary disks where SO detections have been previously reported in the literature and discuss the possible origins of SO in terms of (thermal) desorption or formation in the gas phase. We argue that these processes might be fostered by dynamical perturbations caused by unseen embedded massive companions, shadows, or late-time infall, thus suggesting a possible link between perturbed dynamics and SO emission in (these) protoplanetary disks. If confirmed, our interpretation would imply that chemical evolution timescales could be significantly shorter in these systems than is commonly assumed,

indicating that dynamical perturbations might influence the composition of newborn (proto-)planets by altering the volatile makeup of their formation environment.

# Introduction

High angular resolution observations of protoplanetary disks have revealed a wide variety of structures, offering indirect constraints on the physical mechanisms shaping them, such as planet-disk interactions (cite: BaeEtal2023) or (magneto-)hydrodynamical instabilities (cite: LesurEtal2023). At (sub-)mm wavelengths, the most common features in the dust continuum are concentric gaps and rings (cite: AndrewsEtal2018b; LongEtal2018f; Andrews2020). Molecular line observations often show analogous annular morphologies, reflecting a combination of temperature and abundance gradients that influence line intensities (cite: OebergBergin2021; OebergEtal2021; FacchiniEtal2021). Sophisticated thermochemical models can reproduce many observed molecular line features, providing constraints on molecular abundances and the formation/destruction pathways of volatile species (see (cite: OebergEtal2023) and references therein). However, besides a few notable exceptions (e.g. (cite: IleeEtal2011; YonedaEtal2016)), these models most often considered disks to be dynamically unperturbed environments in a quasi-steady state, where chemical evolution occurs on secular timescales much longer than the Keplerian orbital timescale (cf. (cite: OebergEtal2023)).

In reality, it is increasingly evident that even in the Class II stage protoplanetary disks might experience significant dynamical perturbations (cite: BaeEtal2023; PinteEtal2023a) that can take place on short-enough timescales to give rise to (locally) active chemical processing. Additionally, even if chemical evolution were able to respond fast enough to such dynamical perturbations, thus relaxing back to a quasi-steady state, the local physical and chemical conditions under which chemical evolution would take place might still be substantially different from those typically assumed to forward-model the data (cite: CleevesEtal2015; EvansEtal2015; EvansEtal2019; JiangEtal2023).

Observationally, some of the best examples of dynamically perturbed disks are those with spiral structures. In Class II protoplanetary disks, spirals have been detected in dust thermal continuum, scattered-light emission, and in bright CO rotational line emission (cite: PerezEtal2016; HuangEtal2018c; TeagueEtal2022; WoelferEtal2023; BenistyEtal2023). Interestingly, spirals in scattered-light are often associated with azimuthally asymmetric structures in (sub-)mm continuum emission (cite: TangEtal2017; PinedaEtal2019; YangEtal2023h), possibly linked to long-lived anticyclonic vortices or horseshoes able to trap dust particles (cite: vanderMarelEtal2021a).

Several hypotheses have been proposed to explain the possible origins of these spirals. A class of young sources, including IM Lup, Elias 2-27 (cite: Paneque-CarrenoEtal2021; HuangEtal2018c), and AB Aur (cite: SpeedieEtal2024), are often regarded as self-gravitating or undergoing gravitational instability (GI, (cite: KratterLodato2016)), as is supported by indirect kinematic evidence, such as (1) high dynamical masses (cite: VeronesiEtal2021), (2) GI-wiggles (cite: HallEtal2020; LongariniEtal2024; SpeedieEtal2024), in addition to, when present, (3) prominent continuum spirals, expected to be a telltale of self-gravity (cite: KratterLodato2016).

Another popular interpretation involves (sub-)stellar companions launching Lindblad spirals that propagate at sonic velocities within the disk (cite: DongEtal2015a; BaeZhu2018). However, while clear connections between the presence of close companions and spiral features can be made in some cases (e.g., HD 100543 and HD 142527, (cite: GonzalezEtAl2020; GargEtal2021)), most of the planet-mass companions proposed to explain prominent spiral structures (such as those in MWC 758 and HD 169142, e.g., (cite: DongEtal2018a; RenEtal2020; HammondEtal2023)) remain debated. Conversely, PDS 70, the only disk with confirmed planet-mass companions (cite: KepplerEtal2018; HaffertEtal2019), does not show any clear spiral features.

Alternative explanations involve azimuthal disk temperature variations, such as those caused by shadows induced by a misaligned inner component or a warped disk (cite: MontesinosEtal2016; SuBai2024; ZiamprasEtal2025; ZhuEtal2025),

or infalling material from the surrounding environment

(cite: GinskiEtal2021; MesaEtal2022; HuangEtal2023), that can generate spiral-like structures within disks (cite: LesurEtal2015; HennebelleEtal2017; KuffmeierEtal2020; KuznetsovaEtal2022; CalcinoEtal2025).

All these mechanisms are expected to generate strong dynamical perturbations that can lead to (1) local temperature enhancement via viscous heating or the generation of shocks/compression (cite: OnoEtal2025), (2) an increase in the relative dust particle velocities, which makes ice-coated grains more susceptible to (potentially destructive) collisions (cite: ErikssonEtal2025), and (3) enhanced local turbulence that stirs solids into the warm, UV-illuminated upper disk layers (cite: BiEtal2021; BinkertEtal2023). These processes create favorable conditions for the release of volatiles, such as H$_2$CO, SO, and other oxygen-bearing species, into the gas phase through direct thermal desorption or dust shattering, and their formation in the gas-phase via chemical reactions driven by energetic radiation (cite: AotaEtal2015). More generally, these perturbations would break the quasi-steady state of the disk, fostering active chemical processing. In this sense, it is no surprise that tracers like SO have been robustly identified in several spiral- and candidate-planet-hosting protoplanetary disks, such as HD 100546 (cite: BoothEtal2021b; BoothEtal2024a), AB Aur (cite: DutreyEtal2024; SpeedieEtal2025), HD 169142 (cite: LawEtal2023; BoothEtal2023b), and TW Hya (cite: YoshidaEtal2024).

In this work, we explore the possible link between the dynamical state of the disk and

SO chemistry.

We report the serendipitous detection of SO in archival Atacama Large Millimeter/submillimeter Array (ALMA) observations of the dynamically perturbed protoplanetary disks around CQ Tau and MWC 758. We put them in the context of the other Class II sources where SO detections were previously published, discussing different possible origins for SO emission. In [2](#sec:2_data) we introduce these two systems, describe the available datasets that cover the SO $J_N=6_5-5_4$ transition, and their self-calibration. Our new SO detections, their morphology, kinematics, and connections with scattered light observations are presented in [3](#sec:3_results). Our results are discussed in the broader context of the other SO-bearing Class II protoplanetary disks in [4](#sec:4_discussion). In [5](#sec:5_summary) we summarize our results and draw our conclusions.

# Sources, data, self-calibration

## The perturbed CQ Tau and MWC 758 disks

CQ Tau – $M_\star=1.47\pm0.18\ M_\odot$ (cite: VioqueEtal2018), $d=149.4\pm1.3$ pc (cite: GaiaCollaboration2020), SpT F2 (cite: GarciaLopezEtal2006) – and MWC 758 – $M_\star=1.56\pm0.11\ M_\odot$ (cite: VioqueEtal2018), $d=155.9\pm0.8$ pc (cite: GaiaCollaboration2020), SpT A8 (cite: VieiraEtal2003) – are two Herbig stars located in the nearby HD 35187 association,

near the Taurus star-forming region (cite: LuhmanEtal2023a).

Thanks to their close proximity and high luminosity, the planet-forming disks around CQ Tau and MWC 758 are among the best studied ones across a broad range of frequencies. Observations at (sub-)millimeter wavelengths, first with the Submillimeter Array (SMA, (cite: IsellaEtal2010; TripathiEtal2017)) and later with the Atacama Large Millimeter/submillimeter Array (ALMA), revealed the presence of (1) extended ($R_{\rm 1.3mm}\approx66$ au and 92 au, respectively) continuum emission with a ring-like morphology around wide ($R_{\rm cav,mm}\approx50$ to 60 au) and dust-depleted cavities (cite: BoehlerEtal2018; DongEtal2018a; UbeiraGabelliniEtal2019; CuroneEtal2025), and (2) larger-scale ($R_{\rm CO}\approx200$ au and 300 au, respectively, (cite: Galloway-SprietsmaEtal2025)) CO emission with smaller but still well resolved ($R_{\rm cav,CO}\approx30$ to 50 au) cavities in $^{13}$CO and C$^{18}$O emission (cite: BoehlerEtal2018; UbeiraGabelliniEtal2019; WoelferEtal2021; WoelferEtal2023).

Both sources show telltale signatures of ongoing dynamical perturbations, as evidenced by their prominent scattered-light spiral structures, characterized by a dominant two-arm pattern with additional smaller-scale features (cite: BenistyEtal2015; HammondEtal2022; RenEtal2023b), and their highly asymmetric (sub-)mm continuum emission with two prominent bright arcs on top of a highly substructured wide ring on opposite sides of their cavity rims (cite: BoehlerEtal2018; DongEtal2018a; UbeiraGabelliniEtal2019), roughly aligning with the bases of the scattered-light spirals. Moreover, the cavity of MWC 758 shows a significant eccentricity of $e\approx0.1$ (cite: DongEtal2018a; KuoEtal2022), further suggesting active dynamical sculpting.

Additionally, $^{12}$CO observations revealed strong spiral structures in the kinematics of CQ Tau (cite: WoelferEtal2021; WoelferEtal2023) and MWC 758 (cite: WoelferEtal2025). These spirals are evident in the velocity residuals obtained after subtracting a Keplerian model from the line centroid maps (as done by (cite: IzquierdoEtal2022), see (cite: WoelferEtal2025); Benisty et al., in prep.). Their magnitude is comparable to the local sound speed, consistently with the expectations for propagating sound waves, albeit likely a lower limit, due to the limited angular and spectral resolution of the available data.

## Data and self-calibration

We collected from the ALMA archive all the publicly available data of CQ Tau and MWC 758 that cover the SO $J_N=6_5-5_4$ rotational transition at 219.949 GHz (Band 6). CQ Tau observations were conducted in Cycles 2, 4, and 5 between Aug. 2015 and Nov. 2017, as part of the programs 2013.1.00498.S (PI: L. Pérez), 2016.A.00026.S (PI: L. Testi), and 2017.1.01404.S (PI: L. Testi). MWC 758 was observed in Cycle 5 as part of the program 2017.1.00940.S (PI: L. Ricci) between Oct. and Dec. 2017. The observational setup details are summarized in [6](#app:data).

The data were first pipeline-calibrated by the ESO node of the European ALMA Regional Centre (ARC), and then self-calibrated using the software CASA (Common Astronomy Software Applications, see (cite: CASATeamEtal2022)) `v6.6.5-31`, following the procedure adopted by the [DSHARP](https://almascience.eso.org/almadata/lp/DSHARP/) (cite: AndrewsEtal2018b), [MAPS](https://alma-maps.info/overview.html) (cite: CzekalaEtal2021), and [exoALMA](https://www.exoalma.com/) (cite: LoomisEtal2025) collaborations. A detailed description of the self-calibration procedure can be found in [7](#app:self-cal). We measured a peak signal-to-noise ratio (SNR) of $\approx90$ and $\approx170$ in our fiducial continuum images of CQ Tau and MWC 758. Their root mean square (RMS) noise is within 24.3% and 91.6% of the expected thermal noise (as estimated using the [`apparentsens`](https://casadocs.readthedocs.io/en/stable/api/tt/casatasks.imaging.apparentsens.html) CASA task), indicative of some residual phase noise at high angular resolution. The self-calibrated and continuum-subtracted datasets were used to generate SO emission cubes (at the highest achievable spectral resolution of 0.7 km s$^{-1}$ for CQ Tau, and 1.4 km s$^{-1}$ for MWC 758) and moment maps, as is detailed in [8](#app:imaging).

# Results

#### Continuum emission

The continuum emission maps reconstructed with our fiducial imaging parameters ([8](#app:imaging) for the details) are shown in panels a and b of [1](#fig:1_continuum). Here and in the following figures, the brightness temperature is computed in the Rayleigh-Jeans approximation. The dotted gray lines display the $[5,65]\times\sigma$ and the $[5,40]\times\sigma$ emission contours. These values were chosen to highlight the location of the cavity rim and the continuum crescents. As previously discussed by (cite: UbeiraGabelliniEtal2019; BoehlerEtal2018; DongEtal2018a; CuroneEtal2025), in both sources the continuum morphology is characterized by (1) a deep, almost empty (and, in MWC 758, also clearly eccentric) cavity with a faint inner disk, and (2) bright crescent-like asymmetries on top of a wide, potentially substructured, continuum ring, suggestive of strong dynamical perturbations (as is highlighted in the highpass continuum and scattered-light images shown in [8](#app:imaging)).

![](figures/summary_continuum_vert.pdf)

![](figures/summary_SO_spectra.pdf)

#### SO emission

SO emission is detected both in CQ Tau and in MWC 758 as is clear from the shifted and stacked spectra (blue lines, panels 2a and 2c) and teardrop plots (panels 2b and 2d) displayed in [2](#fig:2_spectra), both generated using `gofish` (cite: Teague2019), from our fiducial cubes ([8](#app:imaging) for details), with fluxes of $72.4\pm14.6$ ($4.9\sigma$ detection) and $31.4\pm9.3$ ($3.4\sigma$ detection) mJy km s$^{-1}$, respectively. These line intensities were measured by integrating the shifted and stacked spectra extracted from a circular mask with a radius of $0.33\ensuremath{''}$ (CQ Tau) and $0.80\ensuremath{''}$ (MWC 758). These apertures correspond to the disk radius where the cumulative distribution of the SO emission, obtained integrating the shifted and stacked spectra extracted from progressively larger circular masks, flattens out (cf. the arrows in the teardrop plots in panels b and d of [2](#fig:2_spectra)). The flux uncertainties, instead, were estimated as the standard deviation of the fluxes measured by integrating the shifted and stacked spectra in non-overlapping spectral ranges as wide as those used to measure the line intensities (to take into account the spectral correlation across channels induced by line shifting and stacking), but not covering the SO transition, extracted from the same disk region.

![](figures/summary_SO_images_new.pdf)

[3](#fig:3_summary) displays the SO integrated intensity (panels 3a and 3e), peak intensity (panels 3b and 3f), and velocity (“moment 1”, panels 3c and 3g) maps, generated using `bettermoments` (cite: TeagueForeman-Mackey2018), without applying any channel or threshold clipping, for our fiducial CLEANing parameters. In addition, a comparison between SO peak intensity and scattered-light morphology is displayed in panels 3d and 3h. Some relevant channel maps, reconstructed with the same fiducial parameters, are shown in [8](#app:imaging).

In CQ Tau, SO is detected with high (5 to $10\sigma$) significance across several independent channels (see [8](#app:imaging)). The integrated intensity map indicates that SO emission primarily arises from the edge of the continuum cavity (as is suggested by the teardrop plot in [2](#fig:2_spectra)) in the form of a ring, with a small inner gap and a bright spot in the direction of the south-east crescent (on the far side of the disc). The SO peak intensity map is also brighter at the cavity rim. However, its morphology is not ring-like, but asymmetric and brighter along the disk major axis and azimuthally closer to the continuum crescents. The comparison between the SO peak intensity emission morphology and the $K_{\rm s}$ band $Q_\phi$ polarized differential image of (cite: RenEtal2023b), displayed in panel 3d, suggests that the SO emission is preferentially co-located with the innermost regions of the scattered light spiral wakes. While, at a first glance, this alignment might suggest a common dynamical origin for the scattered-light spirals and the SO emission, we caution that their co-location is not necessarily physical, as is indicated by the morphological differences between integrated and peak intensity maps, and could be a consequence of limb brightening. In fact, due to a combination of the potentially low optical depth of SO (cf., e.g., the C$^{18}$O integrated intensity map in PDS 70, (cite: LawEtal2024)) and the limited resolution and sensitivity of our dataset (e.g., (cite: WoelferEtal2021)), emission from the higher velocity channels could be artificially enhanced along the disk minor axis. Finally, the SO velocity map ([3](#fig:3_summary), panel 3c), indicates that, at the currently-available spectral resolution (of $\approx0.7$ km s$^{-1}$) the SO emission is qualitatively compatible with Keplerian rotation. However, we cannot exclude lower-amplitude velocity perturbations (e.g., due to the presence of spirals; cf. e.g., the CO velocity residuals published by (cite: IzquierdoEtal2023), typically of order $\leq0.4$ km s$^{-1}$).

In MWC 758, SO is detected only in few independent channels with $>3\sigma$ significance ([8](#app:imaging)), not only because of the lower source inclination, but also possibly because SO emission is more extended but overall fainter. Both the SO integrated intensity and peak intensity maps (panels e and f of [3](#fig:3_summary)) display two bright spots along the disk major axis and along the main ring, close to the continuum cavity edge (as was hinted by the teardrop plot in [2](#fig:2_spectra)). Similarly to CQ Tau, the SO emission velocity of MWC 758 (panel 3g) is qualitatively consistent with being Keplerian. Finally, the comparison between SO peak intensity and the $K_{\rm s}$ band $Q_\phi$ polarized differential image of (cite: RenEtal2023b), displayed in panel 3h, does not show any connections between SO emission and scattered-light spirals.

# Discussion

## Comparison with the other SO-bearing Class II disks

We detected emission from the SO $J_N=6_5-5_4$ transition in CQ Tau and MWC 758. With these two new sources, SO detections have been so far reported in nine Class II disks: UY Aur (cite: TangEtal2014), HD 100546 (cite: BoothEtal2018; BoothEtal2023; BoothEtal2024a), IRS 48 (cite: BoothEtal2021b; BoothEtal2024b), HD 169142 (cite: LawEtal2023; BoothEtal2023b), AB Aur (cite: FuenteEtal2010; Pacheco-VazquezEtal2016; Riviere-MarichalarEtal2020; DutreyEtal2024; SpeedieEtal2025), DR Tau (cite: HuangEtal2023; HuangEtal2024), TW Hya (cite: YoshidaEtal2024), and CQ Tau and MWC 758.

Remarkably, six of these systems, including CQ Tau and MWC 758, (1) are around Herbig stars and (2) show large inner cavities in their ALMA continuum, $^{13}$CO, and C$^{18}$O emission. Moreover, their detected SO emission is consistently located inside or near the edge of these cavities.

We first checked for any correlations between SO emission and stellar properties in our sample of Class II disks with SO detections. For disks lacking SO $J_N=6_5-5_4$ observations, we estimated its flux based on the line flux of the detected transition with the closest upper state energy to the $J_N=6_5-5_4$ one, and rescaled the fluxes to a common distance of 140 pc. Both the optically thin and thick regimes were considered, with the conversion process detailed in [9](#app:SO_flux). We note that different assumptions on the excitation temperature do not qualitatively change our results, as the derived flux differences are relatively small. The stellar and disk parameters of interest and the converted SO fluxes are summarized in [\[tab:1_parameters\]](#tab:1_parameters) and [9](#app:SO_flux).

+:----------+:-----------------------+:------------------------+:---------------------+:------+:---------------+:-----------------------------+:----------+:------------------+:-----------------------+
| Source    | $M_\star$              | $\log_{10}L_\star$      | $t_\star$            | SpT   | $M_{\rm dust}$ | $\log_{10}\dot{M}_{\rm acc}$ | SO tran.s | $F_{\rm SO}$      | Ref.s                  |
|           +------------------------+-------------------------+----------------------+       +----------------+------------------------------+           +-------------------+                        |
|           | ($M_\odot$)            | ($L_\odot$)             | (Myr)                |       | ($M_\oplus$)   | ($M_\odot$ yr$^{-1}$)        |           | (mJy km s$^{-1}$) |                        |
+-----------+------------------------+-------------------------+----------------------+-------+----------------+------------------------------+-----------+-------------------+------------------------+
| \(1\)     | \(2\)                  | \(3\)                   | \(4\)                | \(5\) | \(6\)          | \(7\)                        | \(8\)     | \(9\)             | \(10\)                 |
+-----------+------------------------+-------------------------+----------------------+-------+----------------+------------------------------+-----------+-------------------+------------------------+
| TW Hya    | $0.9^{+0.1}_{-0.2}$    | $-0.54^{+0.13}_{-0.10}$ | $9.8^{+6.2}_{-1.4}$  | M0.5  | $57.1\pm0.1$   | $-8.65\pm0.22$               | $7_8-6_7$ | $13\pm3$          | $1,1,1,2,3,1,4$        |
+-----------+------------------------+-------------------------+----------------------+-------+----------------+------------------------------+-----------+-------------------+------------------------+
| HD 100546 | $2.06^{+0.10}_{-0.12}$ | $1.37^{+0.07}_{-0.05}$  | $5.5^{+1.4}_{-0.8}$  | A0    | $38.0\pm3.9$   | $-6.95\pm0.36$               | $7_8-6_7$ | $343\pm26$        | $5,5,5,6,7,8,9$        |
+-----------+------------------------+-------------------------+----------------------+-------+----------------+------------------------------+-----------+-------------------+------------------------+
| AB Aur    | $2.15^{+0.36}_{-0.21}$ | $1.61^{+0.19}_{-0.21}$  | $4.0^{+1.4}_{-1.5}$  | A0    | $11.8\pm1.2$   | $-6.13\pm0.27$               | $6_5-5_4$ | $330\pm10$        | $5,5,5,10,7,11,12$     |
+-----------+------------------------+-------------------------+----------------------+-------+----------------+------------------------------+-----------+-------------------+------------------------+
| IRS 48    | 2.5                    | 1.62                    | 4.1                  | A0    | 7.8            | $-8.40\pm0.50$               | $7_8-6_7$ | $1063\pm23$       | $13,13,13,14,15,16,17$ |
+-----------+------------------------+-------------------------+----------------------+-------+----------------+------------------------------+-----------+-------------------+------------------------+
| HD 169142 | $2.00\pm0.13$          | $1.31^{+0.12}_{-0.22}$  | $9.0^{+11.0}_{-3.9}$ | F1    | $22.9\pm2.4$   | $-7.09\pm0.21$               | $8_8-7_7$ | $120\pm10$        | $5,5,5,6,7,11,18$      |
+-----------+------------------------+-------------------------+----------------------+-------+----------------+------------------------------+-----------+-------------------+------------------------+
| UY Aur A  | 0.60                   | $-0.49\pm0.2$           | 5.13                 | M0    | $11.2\pm0.6$   | $-7.64$                      | $6_5-5_4$ | N/A               | $19,19,19,19,20,19,21$ |
+-----------+------------------------+-------------------------+----------------------+-------+----------------+------------------------------+-----------+-------------------+------------------------+
| UY Aur B  | 0.34                   | $-0.77\pm0.2$           | 3.89                 | M2.5  | $4.4\pm0.1$    | $-7.70$                      | $6_5-5_4$ | N/A               | $19,19,19,19,20,19,21$ |
+-----------+------------------------+-------------------------+----------------------+-------+----------------+------------------------------+-----------+-------------------+------------------------+
| DR Tau    | $0.83^{+0.34}_{-0.24}$ | $-0.54\pm0.20$          | $3.2^{+2.7}_{-1.4}$  | K4    | $70.4\pm0.1$   | $-7.93\pm0.40$               | $6_5-5_4$ | $195\pm9$         | $22,22,22,22,20,22,23$ |
+-----------+------------------------+-------------------------+----------------------+-------+----------------+------------------------------+-----------+-------------------+------------------------+
| CQ Tau    | $1.47^{+0.19}_{-0.11}$ | $0.87^{+0.18}_{-0.12}$  | $8.9^{+2.8}_{-2.5}$  | F2    | $44.2\pm4.8$   | $<-8.33$                     | $6_5-5_4$ | $72.4\pm14.6$     | $5,5,5,24,7,8,25$      |
+-----------+------------------------+-------------------------+----------------------+-------+----------------+------------------------------+-----------+-------------------+------------------------+
| MWC 758   | $1.56^{+0.11}_{-0.08}$ | $1.04^{+0.12}_{-0.08}$  | $8.3^{+0.4}_{-1.4}$  | A8    | $18.8\pm2.0$   | $-7.32\pm0.40$               | $6_5-5_4$ | $31.4\pm9.3$      | $5,5,5,26,7,8,25$      |
+-----------+------------------------+-------------------------+----------------------+-------+----------------+------------------------------+-----------+-------------------+------------------------+

With the caveats of a higher detection occurrence towards Herbig stars and our small sample size, we did not detect any correlations between SO luminosity and stellar mass, luminosity, accretion rate, or (sub-)mm continuum luminosity. However, we identified a tentative anti-correlation between SO luminosity and individual stellar age (cf., [10](#app:correlations) for a more quantitative discussion on the correlations), suggesting that younger systems in our sample have stronger SO emission, perhaps reflecting its intrinsic origin. This tentative trend is qualitatively consistent with the evidence that SO is commonly detected in young embedded protostars. In fact, 76% of the 21 Class 0 sources part of the CALYPSO survey (cite: PodioEtal2021), 86% of the Class 0 and 57% of the Class I sources targeted by the PEACHES survey (cite: ArturdelaVillarmoisEtal2023), as well as several protostars observed by the eDisk (cite: van’tHoffEtal2023; YamatoEtal2023; FloresEtal2023) and FAUST (cite: Codella2024; ZhangEtal2024_SO; OyaEtal2025) ALMA Large Programs show clear evidence of SO emission. Still, in many of these young sources SO is primarily tracing stellar outflows or disk winds, rather than the disk itself or shocks at the interface between the disk and its surrounding infalling envelope. Moreover, we acknowledge that age estimates of young stellar objects are highly uncertain (cite: SoderblomEtal2014) and our sample size is too small to draw a definitive conclusion. In fact, the lack of dependence of the SO flux on the other stellar and disk parameters might simply indicate that multiple SO origins coexist.

## Potential origins of SO emission

The production of SO in the gas-phase comes from two groups of processes: (1) (thermal) desorption or sputtering (cite: AotaEtal2015), and (2) gas-phase SO formation chemistry (cite: vanGelderEtal2021), driven by the production of (2.1) the OH radical, either with endothermic reactions between H$_2$ and atomic oxygen, or by photodissociation of H$_2$O (cite: HartquistEtal1980), or (2.2) the SH radical, by desorption of H$_2$S, which is expected to be the major sulfur carrier in the ices (cite: VidalEtal2017). For both these processes to work, an excess heating or UV source is required, thus explaining why SO is often suggested as a shock tracer. However, this might also explain the higher occurrence of SO towards Herbig stars in our sample as a consequence of their stronger radiation field, especially in the presence of continuum cavities, where direct irradiation of the cavity walls can create favorable condition, both in terms of temperature and UV irradiation, for SO desorption or gas-phase formation. We discuss the possible origins of the detected gas-phase SO as follows.

### Direct desorption of SO at the inner cavity edge

The morphology of some sources in our sample, characterized by deep continuum cavities and SO emission arising primarily from or within their rims, suggests that the detected SO could simply be SO vapor sublimated from the icy pebbles trapped at the edge of these cavities. Indeed, detailed modeling has shown that the gas temperature can rise steeply inside continuum cavities, where the gas is exposed to the direct heating and UV irradiation from the host star (e.g., (cite: LeemkerEtal2022), and (cite: UbeiraGabelliniEtal2019) in the case of CQ Tau). This “passive” desorption mechanism has been proposed as an explanation for SO emission in IRS 48 (cite: BoothEtal2021b) and HD 100546 (cite: BoothEtal2023), and may also account for the SO emission morphology of CQ Tau.

However, whether “direct” thermal desorption can be an explanation for SO emission also in other sources is less straightforward. Additionally, this mechanism cannot explain the diversity of SO emission morphologies in our sample. For example, while SO in MWC 758 ([3](#fig:3_summary)) and HD 169142 (cite: BoothEtal2023b) still arises close to the inner edge of the continuum cavity, it is too patchy to yield robust conclusions on its morphology. In AB Aur, instead, the SO emission peaks slightly beyond, and not inside, the continuum ring (cite: DutreyEtal2024; SpeedieEtal2025). Finally, for the T Tauri stars in our sample, they are either not known to host continuum cavities (DR Tau and UY Aur), or their SO emission is not co-located with such cavities when present (TW Hya, (cite: YoshidaEtal2024)).

Similar considerations apply to the desorption of other S-bearing volatiles, such as H$_2$S, that are needed to explain the observed SO emission via gas-phase formation.

### Spirals and companions

Similar to CQ Tau and MWC 758, almost all Class II disks with SO detection in our sample show prominent spirals in near-infrared scattered light images: DR Tau (cite: MesaEtal2022), AB Aur (cite: HashimotoEtal2011; BoccalettiEtal2020), UY Aur (cite: TangEtal2014), IRS 48 (cite: FolletteEtal2015), HD 100546 (cite: FolletteEtal2017), and HD 169142 (possibly triggered by the protoplanet candidate HD 169142 b, (cite: HammondEtal2023)). Furthermore, these disks exhibit significantly non-Keplerian gas kinematics (cite: CalcinoEtal2019; GargEtal2022; CasassusEtal2022; SpeedieEtal2024; WoelferEtal2023; WoelferEtal2025; TeagueEtal2025), where spiral-like features have been identified in $^{12}$CO observations through residuals in line width, centroid velocity, and brightness temperature. Spirals are also present in the CO line emission of TW Hya (cite: TeagueEtal2022), which is otherwise seemingly unperturbed in (sub-)mm continuum (cite: AndrewsEtal2016) and near-infrared imaging ((cite: vanBoekelEtal2017), but notice that (cite: DebesEtal2017) identified clear asymmetries moving with non-Keplerian velocity in their scattered-light observations).

This consistent association between disk spirals and SO emission suggests a plausible link between complex gas dynamics and SO chemistry. Indeed, spiral structures in protoplanetary disks are potential drivers of dynamical and chemical activity (cite: IleeEtal2011): as they propagate through the disk, spirals can compress gas, creating shocks that locally increase temperature and density (cite: OnoEtal2025), favoring the direct thermal desorption of SO, or its gas-phase formation.

While the origin of the spirals detected in CQ Tau and MWC 758 remains uncertain, (sub-)stellar companions are promising candidates to explain their origins (cite: GoldreichTremaine1979; ZhuEtal2015b). In fact, several companions have been proposed based on their disk morphology or claimed through high-contrast imaging (cite: DongEtal2015a; ReggianiEtal2018; UbeiraGabelliniEtal2019; HammondEtal2022; WagnerEtal2019b; WagnerEtal2023). If these companions were responsible for exciting the spirals by launching Lindblad waves, their Keplerian orbital frequencies should reflect in the spiral motion. However, the current measurements of the spiral motion in these two sources suggest significantly lower angular velocities than those expected from companions inside their cavities (cite: RenEtal2018; SafonovEtal2022), and at the time of writing, no such companions have been confirmed (cite: UyamaEtal2020b; WagnerEtal2019b; WagnerEtal2024).

As an alternative explanation, these spirals might have been excited by the shadow of a misaligned inner disk (cite: MontesinosEtal2016; ZiamprasEtal2025). In this scenario, the spiral motion would follow the precession of the inner disk rather than the Keplerian velocity at the spiral’s radial location (cite: ZhuEtal2025), thus leaving open the possibility that unseen inner disk companions could indirectly generate the spiral features detected in the outer disk by misaligning the inner disk through gravitational interactions (cite: FacchiniEtal2018a; NealonEtal2018).

Finally, we note that accreting companions themselves could also act as an excess heating source, either through accretion heating (cite: CleevesEtal2015; JiangEtal2023) or viscous heating around the circum-companion disks (cite: CridlandEtal2025). However, while this process could lead to the desorption and/or gas-phase formation of SO and was proposed to be at the origin of SO emission in HD 100546 and HD 169142 (cite: BoothEtal2023; LawEtal2023), its morphology is expected to be potentially more azimuthally localized than what is observed e.g., in CQ Tau and MWC 758.

All in all, we argue that by locally heating up a disk, dynamical perturbations, made evident by the presence of spiral-like features in scattered light observations or gas kinematics, potentially driven by the presence of (yet unseen) companions, could foster the production of gas-phase SO by thermal desorption or gas-phase chemistry. However, we stress that our hypothesis is based on the concurrent presence of SO emission and dynamical perturbations in a small sample with a significant fraction of bright early type stars, thus making it more difficult to disentangle whether the formation of SO is driven by direct stellar irradiation or excess heating fostered by dynamical perturbations.

### Environmental interactions and infall

Another possibility is that the observed SO emission is due to environmental interactions, i.e., slow shocks occurring at the interface between the disk and the infalling material (cite: AotaEtal2015; vanGelderEtal2021). This interpretation has been proposed to explain the SO emission detected in the Class I disks around DG Tau and HL Tau (cite: GarufiEtal2022a), IRS 63 (cite: FloresEtal2023), and the Class II disks around DR Tau (cite: HuangEtal2024) and AB Aur (cite: Riviere-MarichalarEtal2020; DutreyEtal2024; SpeedieEtal2025), where prominent gas streamers traced by CO emission on scales of hundreds of au were detected in Northern Extended Millimeter Array (NOEMA) and ALMA observations (cite: HuangEtal2023; SpeedieEtal2025).

Curiously, both sources with newly-reported SO detection introduced in the paper, CQ Tau and MWC 758, are located near the Taurus star-forming region in close proximity to four other disks, HL Tau, DG Tau, DR Tau, and AB Aur, where SO emission was also observed. Interestingly, the VLT/SPHERE GTO and DESTINYS surveys detected signs of ambient material in about a third of the sources in Taurus (cite: GarufiEtal2024), highlighting the importance of environmental interactions in disk evolution as suggested by recent theoretical studies (cite: WinterEtal2024; PadoanEtal2024).

While there is no direct evidence for ongoing infall in CQ Tau nor MWC 758, a kilo-au-scale optical reflection nebulosity was detected by HST around CQ Tau (cite: GradyEtal2005). In fact, by searching the vicinity of disks hosting large-scale gaseous structures in ALMA data, (cite: GuptaEtal2023) found that all such sources have near-infrared and/or optical reflection nebulae in their vicinity, suggesting a strong correlation between large-scale nebulae and late-infall events. This raises the possibility that environmental interactions, although not directly visible in the current kinematic data, may have played a critical role in shaping the chemical and morphological properties of these disks in the past.

We note that companion-, spiral-, and infall-induced SO formation are not mutually exclusive. For instance, the infall of material from the surrounding environment has been proposed as a promising mechanism to generate spirals (cite: HennebelleEtal2017; KuffmeierEtal2019; KuffmeierEtal2020). In this scenario, the observed spirals could be remnants of past infall events, which can persist on viscous timescales up to $>10^4$ yr in the outer region of disks (cite: CalcinoEtal2025). If Bondi-Hoyle accretion onto disks is frequent (cite: WinterEtal2024; PadoanEtal2024), disks may never fully evolve in isolation, providing a continuous source of perturbations to sustain SO production.

Meanwhile, infall-driven SO formation can explain the tentative anti-correlation between SO flux and system age. In a word, younger disks with more active dynamical environments, higher infall frequency and pre-shock gas density will have stronger detectable SO emission, and the decaying trend of SO could serve as a signal of cloud density dissipation.

However, this could well be a consequence of our very small sample sizes and inherent higher occurrence rate towards more massive stars and brighter disks. Indeed, the anti-correlation between SO flux and system age might simply reflect the different origins of SO emission in our sample: infall-driven in younger sources and excited by companions or shadows in more evolved systems.

## Implications for disk evolution and planet formation

The possible link between SO emission and dynamical perturbations underscores the critical role of disk dynamics and environmental interactions in shaping disk chemistry. In this picture, SO serves as a valuable tracer of excess heating induced by spiral density waves, thus providing insights into the mechanisms driving disk evolution and potentially supporting the hypothesis that this process does not take place in isolation.

The presence of potentially frequent dynamical perturbations raises two concerns. On the one hand, these disks may not always reach (quasi-)equilibrium chemistry, since the relatively long chemical timescales can be comparable to or even longer than the local dynamical timescale (cite: SemenovWiebe2011; OebergEtal2023). On the other hand, these perturbations lead to significant azimuthal asymmetries, which will change the local material and energy sources for chemical reactions. Both could have major implications for the interpretation of the disk chemistry, as most works assume a static disk over the simulation time and set up the thermo-chemical model as azimuthally symmetric. For example, the CS/SO ratio may not be a robust indicator of the C/O ratio when CS and SO are forward modeled with static and passively irradiated disk models (cite: LeGalEtal2019a; KeyteEtal2023; HuangEtal2024).

If confirmed, this link between SO formation and dynamical perturbations might have profound implications for planet formation. First, it shows that dynamical perturbations can significantly influence the distribution of volatiles, challenging the traditional view that planets inherit their composition solely from unperturbed disks (cite: OebergEtal2011; EistrupEtal2016). In addition, the presence of SO near the rims of continuum disk cavities highlights these regions as chemically active zones, potentially influencing the composition of protoplanets forming within the rings (cite: vanderMarelEtal2021b; RampinelliEtal2024). Future observations mapping the chemical inventory of CQ Tau and MWC 758, such as those performed for IRS 48 and HD 100546 (cite: BoothEtal2024a; BoothEtal2024b), will be crucial to assess the relationship between SO chemistry and dynamical perturbations and to better understand the composition of the planet-forming material.

# Summary and conclusions

We report the serendipitous detection of the SO $J_N=6_5-5_4$ rotational line transition in archival ALMA observations of the planet-forming disks around CQ Tau and MWC 758, two dynamically perturbed systems known for their prominent spiral structures in scattered-light observations. SO emission is detected with $4.9\sigma$ significance in CQ Tau and $3.4\sigma$ significance in MWC 758. In both cases, it arises preferentially from the edge of the continuum cavity, but while in CQ Tau it comes in the shape of a ring and is qualitatively compatible with Keplerian rotation, the SO emission is more extended, with a less clear morphology and kinematics in MWC 758.

These results add to the growing sample of SO-bearing Class II disks, which now includes nine systems, six of which are Herbig stars with large inner cavities. We argue that the detection of SO in these dynamically perturbed disks suggests a possible link between disk dynamical perturbations and sulfur chemistry. In this picture, strong additional heating and/or turbulence-driven dust collisions, whether caused by yet unseen massive companions, spirals (due to companions themselves or shadows), or infall, can foster the thermal desorption of SO or its production in the gas phase. However, we stress that, since our sample is small and made up by a significant fraction of bright and massive Herbig stars, “direct” thermal desorption due to passive stellar irradiation remains a possible explanation for the origin of SO emission in at least some of these systems.

We found no statistically significant correlations between SO flux and stellar or disk parameters other than a tentative anti-correlation between SO flux and system age, either suggesting that younger disks, with more active dynamical environments, are likely to have stronger SO emission, or different origins for SO emission. This could be infall driven in younger sources and due to “passive” irradiation or “active” spiral-driven thermal desorption/dust shattering in older perturbed systems.

The detection of SO in such dynamically active systems raises the possibility that chemical evolution might take place on significantly shorter timescales than those commonly assumed in disk evolution and planet formation models. Our results have important implications for interpreting disk chemistry and predicting the composition of forming planets, since tracers such as the CS/SO ratio might not be reliably used to infer the C/O ratio in dynamically perturbed and chemically active disks if forward models are not representative of the out-of-equilibrium environment conditions, and emphasize the need for future studies to consider chemical and dynamical evolution simultaneously.

Future higher resolution and sensitivity observations will be crucial to unravel the detailed mechanisms linking disk dynamics, chemistry, and planet formation in these systems. In particular, a larger sample of SO bearing disks, combined with detailed kinematic studies on both large and small scales, will help to clarify the role of environmental interactions and dynamical perturbations in shaping disk chemistry.

This paper makes use of the following ALMA data:

ADS/JAO.ALMA#2013.1.00498.S,

ADS/JAO.ALMA#2016.A.00026.S,

ADS/JAO.ALMA#2017.1.01404.S, and

ADS/JAO.ALMA#2017.1.00940.S.

ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We are grateful to the anonymous referee for their insightful comments. F.Z. is grateful to Marta De Simone, Carlo F. Manara, and Anna Miotello for insightful discussions. This project has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (PROTOPLANETS, grant agreement No. 101002188). S.F. is funded by the European Union (ERC, UNVEIL, 101076613), and acknowledges financial contribution from PRIN-MUR 2022YP5ACE. Y.A. acknowledges the support by JSPS KAKENHI grant No. 24K00674. P.C. acknowledges support by the ANID BASAL project FB210003. J.D.I. acknowledges support from an STFC Ernest Rutherford Fellowship (ST/W004119/1) and a University Academic Fellowship from the University of Leeds. G.L. received funding from the European Union, Next Generation EU, CUP: G53D23000870006. F.Me. has received funding from the European Research Council (ERC) under the European Union’s Horizon Europe research and innovation program (grant agreement No. 101053020, project Dust2Planets). G.R. is funded by the European Union under the European Union’s Horizon Europe Research & Innovation Programme No.101039651 (DiscEvol) and by the Fondazione Cariplo, grant No. 2022-1217. Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them.

# Facilities

ALMA, VLT/SPHERE

# Software

`CASA` (cite: CASATeamEtal2022), `gofish` (cite: Teague2019) `bettermoments` (cite: TeagueForeman-Mackey2018) `numpy` (cite: HarrisEtal2020), `matplotlib` (cite: Hunter2007), `scipy` (cite: VirtanenEtal2020), `astropy` (cite: AstropyCollaborationEtal2013)

# Data

We introduce the archival observations underlying our analysis. Key information is summarized in [\[tab:A1\]](#tab:A1).

+:-------:+:--------------:+:-----:+:----------:+:------:+:-----:+:-------:+:----------:+:----------:+:------:+:------:+
| Source  | Project code   | PI    | Obs. date  | ToS    | MBL   | \# ant. | Phase cal. | Flux cal.  | PWV    | MRS    |
|         |                |       +------------+--------+-------+         |            |            +--------+--------+
|         |                |       | (dd/mm/yy) | (min)  | (km)  |         |            |            | \(mm\) | ($''$) |
+---------+----------------+-------+------------+--------+-------+---------+------------+------------+--------+--------+
| \(1\)   | \(2\)          | \(3\) | \(4\)      | \(5\)  | \(6\) | \(7\)   | \(8\)      | \(9\)      | \(10\) | \(11\) |
+---------+----------------+-------+------------+--------+-------+---------+------------+------------+--------+--------+
| CQ Tau  | 2013.1.00498.S | Pérez | 30/08/15   | 15.817 | 1.5   | 35      | J0550+2326 | J0510+1800 | 1.18   | 2.9    |
|         +----------------+-------+------------+--------+-------+---------+------------+------------+--------+--------+
|         | 2016.A.00026.S | Testi | 07/08/17   | 19.656 | 3.7   | 41      | J0547+2721 | J0510+1800 | 0.93   | 1.3    |
|         +----------------+-------+------------+--------+-------+---------+------------+------------+--------+--------+
|         | 2017.1.01404.S | Testi | 20/11/17   | 29.083 | 8.5   | 44      | J0521+2112 | J0510+1800 | 0.53   | 0.8    |
|         |                |       +------------+--------+-------+---------+            |            +--------+--------+
|         |                |       | 23/11/17   | 29.050 | 8.5   | 48      |            |            | 0.46   | 1.0    |
+---------+----------------+-------+------------+--------+-------+---------+------------+------------+--------+--------+
| MWC 758 | 2017.1.00940.S | Ricci | 10/10/17   | 44.633 | 16.2  | 47      | J0521+2112 | J0510+1800 | 0.40   | 0.3    |
|         |                |       +------------+--------+-------+---------+            |            +--------+--------+
|         |                |       | 10/10/17   | 44.617 | 16.2  | 47      |            |            | 0.41   | 0.3    |
|         |                |       +------------+--------+-------+---------+            |            +--------+--------+
|         |                |       | 11/10/17   | 44:600 | 16.2  | 47      |            |            | 1.31   | 0.3    |
|         |                |       +------------+--------+-------+---------+            |            +--------+--------+
|         |                |       | 15/10/17   | 44:667 | 16.2  | 52      |            |            | 2.45   | 0.4    |
|         |                |       +------------+--------+-------+---------+            |            +--------+--------+
|         |                |       | 16/10/17   | 44.717 | 16.2  | 52      |            |            | 2.74   | 0.4    |
|         |                |       +------------+--------+-------+---------+            |            +--------+--------+
|         |                |       | 09/10/17   | 38.500 | 3.1   | 44      |            |            | 2.24   | 1.6    |
|         |                |       +------------+--------+-------+---------+            |            +--------+--------+
|         |                |       | 17/10/17   | 38.517 | 2.5   | 45      |            |            | 2.18   | 2.4    |
|         |                |       +------------+--------+-------+---------+            |            +--------+--------+
|         |                |       | 27/10/17   | 38.550 | 2.5   | 46      |            |            | 2.38   | 2.3    |
|         |                |       +------------+--------+-------+---------+            |            +--------+--------+
|         |                |       | 28/10/17   | 38.517 | 2.5   | 45      |            |            | 1.04   | 2.5    |
+---------+----------------+-------+------------+--------+-------+---------+------------+------------+--------+--------+

#### CQ Tau

The observations were conducted in Cycles 2, 4, and 5 between Aug. 2015 and Nov. 2017, as part of the programs 2013.1.00498.S (PI: L. Pérez), 2016.A.00026.S (PI: L. Testi), and 2017.1.01404.S (PI: L. Testi). These programs used only Band 6 receivers and the data were correlated from eight spectral windows (SPWs) in dual polarization mode. Six SPWs were set in frequency division mode (FDM), one with 1920 channels 244.1 kHz-wide centered at 230.7 GHz, two with 960 channels 448.3 kHz-wide centered at 219.7 and 220.2 GHz, two with 60 channels 7.8 MHz-wide centered at 218.8 and 219.3 GHz, one with 120 channels 3.9 MHz-wide centered at 231.2 GHz, all spanning a total bandwidth of 468.8 MHz. The remaining two SPWs, centered at 217.0 (2013.1.00498.S), 217.6 (2016.A.00026.S and 2017.1.01404.S) and 232.4 GHz, were set in time division mode (TDM), with 128 channels 15.6 MHz-wide, and spanned a total bandwidth of 2.0 GHz.

For the program 2013.1.00498.S, the observations used an array with baseline lengths from 15.1 m to 1.5 km (resolution of $\approx0.260\ensuremath{''}$) and 35 antennas in the C34-7 configuration. The total integration time on the science target was $\approx15$ min. The bandpass calibrator J0423-0120 and the flux calibrator J0510+1800 were observed at the beginning of the observing block, the phase calibrator J0550+2326 and an additional delay calibrator J0547+2721 were observed in an alternating sequence with the science target, every $\approx10$ and 15 min.

For the program 2016.A.00026.S the observations used an array with baseline lengths from 81.0 m to 3.7 km (resolution of $\approx0.110\ensuremath{''}$) and 41 antennas in the C40-7 configuration. The total integration time on the science target was $\approx20$ min. The bandpass and flux calibrator J0510+1800 was observed at the beginning of the observing block, the phase calibrator J0547+2721 was observed in an alternating sequence with the science target, every $\approx1$ to 2 min. An additional “check” calibrator, J0521+2112, was observed every $\approx7$ min to assess the quality of the phase transfer.

For the program 2017.1.01404.S, the observations used an array with baseline lengths from 92.1 m to 8.5 km (resolution of $\approx0.060\ensuremath{''}$). Two execution blocks (EBs) were scheduled, with 44 and 48 antennas, respectively, in the C43-8 configuration. The total integration time on the science target was $\approx30$ min for each EB. The bandpass, flux, and “check” calibrator J0510+1800 was observed at the beginning of the observing block, then every $\approx10$ min to assess the quality of phase transfer, the phase calibrator J0521+2112 was observed in an alternating sequence with the science target, every $\approx1$ to 2 min.

#### MWC 758

The observations were conducted in Cycle 5 between Oct. and Dec. 2017 as part of the program 2017.1.00940.S (PI: L. Ricci). The data were correlated from four SPWs in dual polarization mode. Two SPWs were set in FDM each with 1920 channels 976.6 kHz-wide centered at 219.5 and 231.5 GHz and spanning a total bandwidth of 1.9 GHz. The remaining SPWs, centered at 217.5 and 234.2 GHz, was set in TDM, with 128 channels 15.6 MHz-wide, and spanning a total bandwidth of 2.0 GHz. The target was observed in the more compact C43-6 configuration (short baselines, four scheduled EBs), and the more extended C43-10 configuration (long baselines, five scheduled EBs).

The observations at short baselines used an array with baseline lengths from 15.1 m to 2.5 or 3.1 km (resolution of $\approx0.130\ensuremath{''}$) and between 44 and 46 antennas. The total integration time on the science target was $\approx40$ min for each EB. The bandpass and flux calibrator J0510+1800 was observed at the beginning of each EB, while the phase calibrator J0521+2112 was observed in an alternating sequence with the science target, every $\approx10$ min. An additional “check” calibrator, J0519+2744, was observed every $\approx30$ min to assess the quality of the phase transfer.

The observations at long baselines used an array with baseline lengths from 41.4 or 233.0 m to 16.2 km (resolution of $\approx0.020\ensuremath{''}$) and between 47 and 52 antennas. Five EBs were scheduled. The total integration time on the science target was $\approx45$ min for each of them. The bandpass and flux calibrator J0510+1800 was observed at the beginning of each EB, while the phase calibrator J0521+2112 was observed in an alternating sequence with the science target, every $\approx1$ to 2 min. An additional “check” calibrator, J0518+2054, was observed every $\approx15$ min to assess the quality of the phase transfer.

# Self-calibration

To begin with, we created pseudo-continuum datasets flagging channels within $\pm15$ km s$^{-1}$ of the systematic velocity around the rest frequencies of the $^{12}$CO ($J=2-1$ at 230.5380 GHz), $^{13}$CO ($J=2-1$ at 220.3986 GHz), C$^{18}$O ($J=2-1$ at 219.5603 GHz), DCN ($J=3-2$ at 217.2385 GHz), SO ($J_N=6_5-5_4$ at 219.9494 GHz), and H$_2$CO ($N_{K_a,K_c}=3_{0,3}-2_{0,2}$, $3_{2,1}-2_{2,0}$, $3_{2,2}-2_{2,1}$, and $9_{1,8}-9_{1,9}$ at 218.2221, 218.7601, 218.4756, and 216.5686 GHz) transitions.

These pseudo-continuum EBs were channel-averaged ensuring a $<1\%$ reduction in peak response to a point source at the edge of the primary beam to avoid bandwidth smearing, according to the criterion of (cite: BridleSchwab1999), and imaged (separately) over the entire primary beam, using the task `tclean`. CLEANing was performed over a user-defined elliptical mask (of $0.85\ensuremath{''}\times0.72\ensuremath{''}$, ${\rm PA}=55$ deg for CQ Tau and $0.80\ensuremath{''}\times0.80\ensuremath{''}$, ${\rm PA}=62$ deg for MWC 758 that covers all the continuum emission, with a threshold of $\approx6\sigma$, where $\sigma$ is the root mean squared (RMS) noise calculated over an emission-free annular region between 4$\ensuremath{''}$ and 6$\ensuremath{''}$ centered on the source phase center and larger than the continuum emission extent, and $\approx8$ pixels along the synthesized beam minor axis. We adopted the `multiscale` deconvolver (cite: Cornwell2008), with scales including a point source and some (sub-)multiples of the synthesized beam that could be accommodated within the user-defined mask (\[0, 2, 4, 8, 12\] for short baseline and \[0, 2, 4, 8, 16, 24\] for long baseline observations), with preference for smaller ones (`smallscalebias=0.6`), `cycleniter=300`, `gain=0.3`, and a `briggs` weighting scheme with `robust=0.5` (cite: Briggs1995). For CQ Tau, since some of the data were taken in early ALMA cycles, we recomputed the weights using the task `statwt` combining different polarisations, scans, and SPWs.

Subsequently, a round of phase-only self-calibration was performed on each EB (separately) to increase their signal-to-noise ratio (SNR) prior to alignment. The gain solutions were computed using the task `gaincal` over an infinite solution interval, for both polarisations together, combining all the available SPWs and time scans, and rejecting those gain solutions corresponding to antennas with $<3$ baselines and ${\rm SNR}<4$. We then shifted the phase centers of these self-calibrated EBs to a common direction chosen to be that of the phase center of the long baseline EB with the highest peak SNR. The alignment was performed in visibility space, minimizing the phase differences between EBs in the widest continuum SPW, and checked for by comparing the ratio images (reconstructed using the same parameters described above) of each dataset to the reference EB (see (cite: CasassusCarcamo2022; LoomisEtal2025)). While in the case of CQ Tau the peak SNR of each self-calibrated EB was high-enough ($\gtrsim65$) to provide a significant reduction of the amount of structures in the ratio images, indicative of an accurate alignment, for MWC 758, the much lower peak SNR, especially for the long baseline EBs ($\lesssim15$), often led to a (marginal) worsening of the EB alignment. Thus, since the direct inspection of the images suggested that the EBs were already almost perfectly aligned, for MWC 758 we chose not to shift the EBs.

For both sources, we inspected the EBs for amplitude-scale offsets, plotting the ratio of their projected visibilities to those of a reference EB. For CQ Tau, the EB with highest peak SNR shows flux offsets $>30\%$ compared to the others. Thus, we adopted as a reference EB the one taken on Nov. 23, 2017, because of its lower phase RMS (22.58 deg) and higher peak SNR compared to the remaining ones. Instead, for MWC 758, we selected as a reference EB the one taken on Dec. 28, 2017, because its peak SNR is the highest among the available EBs, and its phase RMS (16.72 deg) is lower than for the other SBs. For both sources, most EBs show a (sometimes significant) dependence of the visibility amplitude ratio on the deprojected baselines, which we interpreted as an indication of phase-decoherence. For this reason, although for some EBs flux-scale offsets $>4\%$ were estimated, at this stage we chose not to rescale their amplitudes. Instead, we performed a first iteration of phase-only self-calibration, first on the concatenated short-baseline observations and then combining short- and long-baseline data to correct for decoherence and identify more accurate flux-scale offsets.

Self-calibration was performed iteratively, first on the short-baseline observations and then on the combined short- and long-baseline EBs (e.g., (cite: AndrewsEtal2018b)). The images were reconstructed after each step adopting the same fiducial parameters described above, except for the long-baseline observations of MWC 758, whose best trade-off between angular resolution and peak SNR was obtained for `robust=1.0`. For the short-baseline data, the gain solutions were first computed separately for each polarization on an infinite solution interval, combining different SPWs and time scans. Then, on progressively shorter solution intervals of 360, 120, 60, and 20 s, for both polarisations together, combining different SPWs and time scans (but no scans were combined for solution intervals shorter than the average scan length). The gain solutions for antennas with $<4$ baselines and ${\rm SNR}<3$ were flagged. Visual inspection led to further manual flagging of too large phase-gain solutions. For the long-baseline data, we followed a similar procedure, with solution intervals decreasing from the full EB, to 360, 120, 60, 30, and 18 s[^1], rejecting gain solutions corresponding to antennas with $<4$ baselines and ${\rm SNR}<2$ (for CQ Tau) or 3 (for MWC 758). For CQ Tau, the peak SNR increased from 112.77 to 151.32 ($\approx34\%$) after self-calibration of the short-baseline data and from 138.88 to 181.98 ($\approx31\%$) after self-calibration of the combined short and long baseline EBs. For MWC 758, the peak SNR increased from 317.43 to 442.55 ($\approx39\%$) after self-calibration of the short-baseline observations and from 171.13 to 186.57 ($\approx9\%$) after self-calibration of the combined short and long baseline EBs.

We re-inspected the amplitude ratios between different EBs and the reference ones after each self-calibration step, finding that the flux offsets were progressively reduced and decoherence decreased in most cases. Then, we re-scaled those EBs that showed flux ratios $>4\%$ and performed a new self-calibration iteration. For CQ Tau the peak SNR increased from 148.65 to 201.44 ($\approx36\%$) after self-calibration of the short-baseline data and from 164.87 to 222.13 ($\approx35\%$) after self-calibration of the combined short and long baseline EBs. For MWC 758, the peak SNR increased from 322.03 to 450.81 ($\approx40\%$) after self-calibration of the short-baseline observations and from 167.33 to 176.44 ($\approx5\%$) after self-calibration of the combined short and long baseline EBs.

We then performed two cycles of amplitude and phase self-calibration. The solutions were obtained with an infinite solution interval, first combining all the available SPWs and scans, then only the SPWs, for both polarisations together. Images were reconstructed with the same fiducial parameters described above and a CLEANing threshold of $\approx1\sigma$. In all cases, gain solutions for antennas with $<4$ baselines and ${\rm SNR}<5$ were flagged. Amplitude gains $>20\%$ were also flagged, and phase-gain solutions were further visually inspected and manually flagged when too large. For CQ Tau both steps were successful and led to an improvement in the peak SNR from 222.35 to 224.17 ($\lesssim1\%$), while for MWC 758 the peak SNR improved from 167.98 to 179.98 ($\approx7\%$) after the first step and no second iteration was performed[^2].

Finally, we applied the phase shifts, flux scaling, and gain solutions to the original datasets (i.e., those including the previously flagged line emission channels) and time-binned the self-calibrated measurement sets by 30 s to reduce the data volume. Then, using the CASA `v6.2.1-7` implementation of the `uvcontsub` task, with `solint=1`, `fitorder=1`, and excluding the same channels used to create the pseudo-continuum datasets, these measurement sets were continuum-subtracted and independent datasets for each relevant rotational transition were created.

The calibration and imaging scripts are available [here](https://github.com/fzagaria/selfcal_CQTau_and_MWC758).

# Imaging and summary plots

The continuum images were reconstructed from the measurement sets obtained after the last step of phase and amplitude self-calibration, time-averaged by 30 s. These (line-flagged) datasets were CLEANed with the same fiducial parameters described in [7](#app:self-cal), `robust=0.0` for CQ Tau and `robust=1.0` for MWC 758, a noise threshold of $\approx1\sigma$ (the RMS was measured on an emission-free circular annulus between $4\ensuremath{''}$ and $6\ensuremath{''}$ centered on the source phase center using the task `imstat`), and `gain=0.02` (to minimize any artifacts in the continuum cavities). Our fiducial images are displayed in [1](#fig:1_continuum), while [\[tab:A2\]](#tab:A2) summarizes their imaging parameters and continuum properties.

+:-------:+:------:+:-----:+:------------------:+:------:+:-------------------:+:-----------------:+:--------:+:---------------:+
| Source  | Wav.   | Rob.  | Beam size          | PA     | RMS noise           | Peak intensity    | Peak SNR | Integrated flux |
|         +--------+       +--------------------+--------+---------------------+-------------------+          +-----------------+
|         | \(mm\) |       | ($''^2$)           | (deg)  | (mJy beam$^{-1}$)   | (mJy beam$^{-1}$) |          | (mJy)           |
+---------+--------+-------+--------------------+--------+---------------------+-------------------+----------+-----------------+
| \(1\)   | \(2\)  | \(3\) | \(4\)              | \(5\)  | \(6\)               | \(7\)             | \(8\)    | \(9\)           |
+---------+--------+-------+--------------------+--------+---------------------+-------------------+----------+-----------------+
| CQ Tau  | 1.33   | 0.0   | $0.055\times0.039$ | $-4.1$ | $1.43\times10^{-3}$ | 1.29              | 90.04    | $146.80\pm0.37$ |
+---------+--------+-------+--------------------+--------+---------------------+-------------------+----------+-----------------+
| MWC 758 | 1.33   | 1.0   | $0.066\times0.044$ | $8.5$  | $6.46\times10^{-3}$ | 1.11              | 172.33   | $58.01\pm0.30$  |
+---------+--------+-------+--------------------+--------+---------------------+-------------------+----------+-----------------+

As is commented on in [3](#sec:3_results), the continuum emission from both sources shows significant evidence of ongoing dynamical perturbations in the form of high-contrast asymmetries. Such asymmetries show up more distinctly in panels a and c of [4](#fig:A1_continuum), that display the highpass-filtered continuum emission from both sources. These highpass-filtered maps were obtained by subtracting to the images reconstructed with `robust=0.5` and `1.5` their convolution with Gaussian kernels with a standard deviation of 5 and 8 pixels, respectively. In the case of MWC 758, (cite: DongEtal2018a) had already reported the presence of an azimuthally-wide arc, co-located with one of the scattered-light spirals (cf. panel d, that shows the $K_{\rm s}$ band $Q_\phi$ polarized differential image published by (cite: RenEtal2023b)), that connects the cavity rim with a bright annular structure. For CQ Tau, the higher SNR and angular resolution of our combined dataset allowed detecting, for the first time, three arcs veering from the continuum ring towards the central cavity. One of them (labeled “Arc 1” in panel a) is connected with one of the spirals detected in scattered light (cf. panel b, that also shows the $K_{\rm s}$ band $Q_\phi$ polarized differential image published by (cite: RenEtal2023b)), suggesting that they might be tracing the same physical disk structure.

![](figures/summary_continuum_highpass.pdf)

For SO, the continuum-subtracted measurement sets were imaged using `tclean` with `specmode=‘cube’`, 23 channels of 0.7 km s$^{-1}$ (corresponding to absolute velocities from $-1.3$ to 13.9 km s$^{-1}$ in the LSRK reference frame) for CQ Tau and 7 channels of 1.4 km s$^{-1}$ (corresponding to absolute velocities from 1.7 to 10.1 km s$^{-1}$ in the LSRK reference frame) for MWC 758 (plum area in the spectra in [2](#fig:2_spectra)), a `multiscale` deconvolver and scales including a point source and sub-multiples of the synthesized beam (i.e., \[0, 2, 4, 8\]). CLEANing was performed with a common restoring beam across different channels, $\approx8$ pixels along the synthesized beam minor axis, a $1\sigma$ threshold (the RMS was estimated as for the continuum), and a conservative `gain=0.01`, over a user-defined mask, either the same one used for the continuum (equally across all the channels), or a Keplerian mask (generated using the code of (cite: Teague2020) and the geometric parameters of (cite: CuroneEtal2025) and (cite: IzquierdoEtal2025), listed in [\[tab:A3\]](#tab:A3)). For MWC 758 some differences between the images reconstructed with the continuum and Keplerian masks can be seen due to clear non-Keplerian emission features (see e.g., teardrop plot in [2](#fig:2_spectra)). Different weighting schemes, `robust` parameters, and Gaussian $uv$-tapers were tested.

Our fiducial images were reconstructed with `natural` weighting scheme and a Gaussian $uv$-taper with $0.05\ensuremath{''}$ (CQ Tau) and $0.25\ensuremath{''}$ (MWC 758) full width at half maximum. Some relevant channel maps are displayed in [5](#fig:A2_channels) and their imaging parameters and emission properties are summarized in [\[tab:A4\]](#tab:A4). These same fiducial images were also used to generate the integrated intensity, peak intensity, and velocity maps displayed in [3](#fig:3_summary), using [`bettermoments`](https://bettermoments.readthedocs.io/en/latest/index.html), a python package that collapses (smoothed and spatially or spectrally masked) image cubes along the velocity axis to generate moment maps (cite: TeagueForeman-Mackey2018). Because of the moderate detection significance of SO, we did not apply any channel or noise clipping. No clear signs of spacial noise correlations can be seen in any of the moment maps, nor in any channel map, for all weighting schemes.

+:-------:+:-------:+:-----:+:-----------:+:-----:+:-------------:+
| Source  | $i$     | PA    | $M_\star$   | $d$   | $v_{\rm sys}$ |
|         +---------+-------+-------------+-------+---------------+
|         | (deg)   | (deg) | ($M_\odot$) | (pc)  | (km s$^{-1}$) |
+---------+---------+-------+-------------+-------+---------------+
| \(1\)   | \(2\)   | \(3\) | \(4\)       | \(5\) | \(6\)         |
+---------+---------+-------+-------------+-------+---------------+
| CQ Tau  | $-36.3$ | 235.1 | 1.40        | 149.4 | 6.19          |
+---------+---------+-------+-------------+-------+---------------+
| MWC 758 | $19.4$  | 240.3 | 1.40        | 155.9 | 5.89          |
+---------+---------+-------+-------------+-------+---------------+

+:-------:+:---------:+:-------------:+:------------------:+:--------:+:-------------------:+:-----------------:+:--------:+
| Source  | Weighting | $uv$-tapering | Beam size          | PA       | Avg. RMS noise      | Peak intensity    | Peak SNR |
|         |           +---------------+--------------------+----------+---------------------+-------------------+          |
|         |           | ($''$)        | ($''^2$)           | (deg)    | (mJy beam$^{-1}$)   | (mJy beam$^{-1}$) |          |
+---------+-----------+---------------+--------------------+----------+---------------------+-------------------+----------+
| \(1\)   | \(2\)     | \(3\)         | \(4\)              | \(5\)    | \(6\)               | \(7\)             | \(8\)    |
+---------+-----------+---------------+--------------------+----------+---------------------+-------------------+----------+
| CQ Tau  | `natural` | 0.05          | $0.159\times0.133$ | $-6.76$  | $7.44\times10^{-1}$ | 7.67              | 10.31    |
+---------+-----------+---------------+--------------------+----------+---------------------+-------------------+----------+
| MWC 758 | `natural` | 0.25          | $0.428\times0.326$ | $-11.73$ | $6.61\times10^{-1}$ | 4.39              | 6.65     |
+---------+-----------+---------------+--------------------+----------+---------------------+-------------------+----------+

![](figures/summary_SO_channels.pdf)

To assess the SO detection significance, a set of images were reconstructed with these same fiducial parameters, but across a much wider velocity range ($\gtrsim200$ km s$^{-1}$), essential to accurately determine the background noise in line free channels. We used [`gofish`](https://fishing.readthedocs.io/en/latest/index.html) (cite: Teague2019), a python package that extracts and averages spectra from an image cube across a given disk region and, under the assumption of a Keplerian velocity field, corrects for the known disk rotation by shifting such spectra to a common line center (cf., (cite: YenEtal2016)), to stack our SO emission lines and increase their peak SNR, adopting the physical and geometrical parameters in [\[tab:A3\]](#tab:A3). Such an improvement can be seen by comparing the gray and blue spectra in the insert in panel a and c of [2](#fig:2_spectra).

# Flux conversion between SO transitions

To fairly compare the SO emission detected in different transitions, we estimated the SO $J_N=6_5-5_4$ flux for disks that do not have SO $J_N=6_5-5_4$ observations, based on the line flux from the detected transition. We considered two regimes: optically thin and optically thick. This estimation depends on the excitation conditions, energy levels, and line properties. Our conversion results are summarized in [\[tab:SO_fluxes\]](#tab:SO_fluxes).

In the optically thin regime, assuming local thermodynamic equilibrium (LTE) and a constant excitation temperature ($T=30$, 50, and 70 K), we calculated the flux ratio of the known line $F_1$ to the desired line flux $F_2$ by (cite: Goldsmith&Langer1999) $$\begin{equation}
    \frac{F_2}{F_1} = \frac{\nu_2}{\nu_1} \cdot \frac{A_{ul}^{(2)} g_{u}^{(2)} e^{-E_{u}^{(2)}/kT}}{A_{ul}^{(1)} g_{u}^{(1)} e^{-E_{u}^{(1)}/kT}},
\end{equation}$$ where $k$ is the Boltzmann constant, $\nu_1$, $\nu_2$ are the line frequencies, $A_{ul}^{(1)}$, $A_{ul}^{(2)}$ the Einstein $A_{ul}$ coefficients, $g_{u}^{(1)}$, $g_{u}^{(2)}$ the statistical weights of the upper levels, and $E_{u}^{(1)}$, $E_{u}^{(2)}$ the upper-level energies of the two transitions.

In the optically thick case, the line becomes saturated, and the intensity depends primarily on the excitation temperature and source size, $F \propto B_\nu(T) \cdot \Omega$,

where $B_{\nu}(T)$ is the Planck function at the excitation temperature $T$ and frequency $\nu$, and $\Omega$ is the solid angle of the emitting region. Assuming the same excitation temperature and emitting area for both transitions, we have $$\begin{equation}
    \frac{F_2}{F_1} \approx \frac{B_{\nu_2}(T)}{B_{\nu_1}(T)}\approx \frac{\nu_2^2}{\nu_1^2}
\end{equation}$$ where the last step follows from the Rayleigh-Jeans approximation.

+:----------+:--------------+:--------------+:-------------------+:--------------+:------+:-----------------------+
| Source    | $d$           | SO transition | $F_{\rm SO}$ obsv. | Optical depth | $T$   | $F_{\rm SO}$ at 140 pc |
|           +---------------+               +--------------------+               +-------+------------------------+
|           | (pc)          |               | (mJy km s$^{-1}$)  |               | \(K\) | (mJy km s$^{-1}$)      |
+-----------+---------------+---------------+--------------------+---------------+-------+------------------------+
| \(1\)     | \(2\)         | \(3\)         | \(4\)              | \(5\)         | \(6\) | \(7\)                  |
+-----------+---------------+---------------+--------------------+---------------+-------+------------------------+
| TW Hya    | $60.1\pm0.1$  | $7_8-6_7$     | $13\pm3$           | –             | –     | 2.4                    |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thin          | 30    | 1.7                    |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thin          | 50    | 0.9                    |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thin          | 70    | 0.7                    |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thick         | –     | 1.0                    |
+-----------+---------------+---------------+--------------------+---------------+-------+------------------------+
| HD 100546 | $108.1\pm0.4$ | $7_8-6_7$     | $343\pm26$         | –             | –     | 204.6                  |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thin          | 30    | 143.0                  |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thin          | 50    | 77.2                   |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thin          | 70    | 59.3                   |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thick         | –     | 85.3                   |
+-----------+---------------+---------------+--------------------+---------------+-------+------------------------+
| AB Aur    | $155.9\pm0.9$ | $6_5-5_4$     | $330\pm10$         | –             | –     | 409.4                  |
+-----------+---------------+---------------+--------------------+---------------+-------+------------------------+
| IRS 48    | $136.3\pm1.9$ | $7_8-6_7$     | $1063\pm23$        | –             | –     | 1007.9                 |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thin          | 30    | 704.4                  |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thin          | 50    | 380.5                  |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thin          | 70    | 292.2                  |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thick         | –     | 420.0                  |
+-----------+---------------+---------------+--------------------+---------------+-------+------------------------+
| HD 169142 | $114.9\pm0.3$ | $8_8-7_7$     | $120\pm10$         | –             | –     | 80.8                   |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thin          | 30    | 58.5                   |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thin          | 50    | 29.0                   |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thin          | 70    | 21.5                   |
|           |               +---------------+--------------------+---------------+-------+------------------------+
|           |               | $6_5-5_4$     | –                  | Thick         | –     | 33.0                   |
+-----------+---------------+---------------+--------------------+---------------+-------+------------------------+
| UY Aur AB | $152.3\pm0.9$ | $6_5-5_4$     | N/A                | –             | –     | N/A                    |
+-----------+---------------+---------------+--------------------+---------------+-------+------------------------+
| DR Tau    | $193.0\pm1.2$ | $6_5-5_4$     | $195\pm9$          | –             | –     | 370.5                  |
+-----------+---------------+---------------+--------------------+---------------+-------+------------------------+
| CQ Tau    | $149.4\pm1.3$ | $6_5-5_4$     | $72.4\pm14.6$      | –             | –     | 82.4                   |
+-----------+---------------+---------------+--------------------+---------------+-------+------------------------+
| MWC 758   | $155.9\pm0.8$ | $6_5-5_4$     | $31.4\pm9.3$       | –             | –     | 38.9                   |
+-----------+---------------+---------------+--------------------+---------------+-------+------------------------+

# Correlation test

We visualize the stellar and disk parameters of interest and the converted SO fluxes summarized from [\[tab:1_parameters\]](#tab:1_parameters) and [\[tab:SO_fluxes\]](#tab:SO_fluxes) in the pair plot in [6](#fig:pairplot_thin). We adopted the Pearson Correlation Coefficient (PCC) and the corresponding $p$-values to quantitatively assess how the SO fluxes correlate with other parameters, which are labeled in the pair plots. While no statistically significant ($p<0.05$) correlations are found with stellar mass, luminosity, accretion rate, and disk mass, the SO fluxes show a tentative anti-correlation with system age, with a PCC of $-0.82$ when SO flux is in logarithmic space and age is in linear space.

![](figures/pairplot_thin.pdf)

natexlab

(ref: Andrews2020) Andrews, S. M. 2020, ARA&A, 58, 483, doi: [`10.1146/annurev-astro-031220-010302`](http://doi.org/10.1146/annurev-astro-031220-010302)

(ref: AndrewsEtal2016) Andrews, S. M., Wilner, D. J., Zhu, Z., et al. 2016, ApJL, 820, L40, doi: [`10.3847/2041-8205/820/2/L40`](http://doi.org/10.3847/2041-8205/820/2/L40)

(ref: AndrewsEtal2018b) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: AotaEtal2015) Aota, T., Inoue, T., & Aikawa, Y. 2015, ApJ, 799, 141, doi: [`10.1088/0004-637X/799/2/141`](http://doi.org/10.1088/0004-637X/799/2/141)

(ref: ArturdelaVillarmoisEtal2023) Artur de la Villarmois, E., Guzmán, V. V., Yang, Y. L., Zhang, Y., & Sakai, N. 2023, A&A, 678, A124, doi: [`10.1051/0004-6361/202346728`](http://doi.org/10.1051/0004-6361/202346728)

(ref: AstropyCollaborationEtal2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: BaeEtal2023) Bae, J., Isella, A., Zhu, Z., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 423

(ref: BaeZhu2018) Bae, J., & Zhu, Z. 2018, ApJ, 859, 118, doi: [`10.3847/1538-4357/aabf8c`](http://doi.org/10.3847/1538-4357/aabf8c)

(ref: BenistyEtal2015) Benisty, M., Juhasz, A., Boccaletti, A., et al. 2015, A&A, 578, L6, doi: [`10.1051/0004-6361/201526011`](http://doi.org/10.1051/0004-6361/201526011)

(ref: BenistyEtal2023) Benisty, M., Dominik, C., Follette, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 605, doi: [`10.48550/arXiv.2203.09991`](http://doi.org/10.48550/arXiv.2203.09991)

(ref: BiEtal2021) Bi, J., Lin, M.-K., & Dong, R. 2021, ApJ, 912, 107, doi: [`10.3847/1538-4357/abef6b`](http://doi.org/10.3847/1538-4357/abef6b)

(ref: BinkertEtal2023) Binkert, F., Szulágyi, J., & Birnstiel, T. 2023, MNRAS, 523, 55, doi: [`10.1093/mnras/stad1405`](http://doi.org/10.1093/mnras/stad1405)

(ref: BoccalettiEtal2020) Boccaletti, A., Di Folco, E., Pantin, E., et al. 2020, A&A, 637, L5, doi: [`10.1051/0004-6361/202038008`](http://doi.org/10.1051/0004-6361/202038008)

(ref: BoehlerEtal2018) Boehler, Y., Ricci, L., Weaver, E., et al. 2018, ApJ, 853, 162, doi: [`10.3847/1538-4357/aaa19c`](http://doi.org/10.3847/1538-4357/aaa19c)

(ref: BoothEtal2023) Booth, A. S., Ilee, J. D., Walsh, C., et al. 2023a, A&A, 669, A53, doi: [`10.1051/0004-6361/202244472`](http://doi.org/10.1051/0004-6361/202244472)

(ref: BoothEtal2023b) Booth, A. S., Law, C. J., Temmink, M., Leemker, M., & Macı́as, E. 2023b, A&A, 678, A146, doi: [`10.1051/0004-6361/202346974`](http://doi.org/10.1051/0004-6361/202346974)

(ref: BoothEtal2021b) Booth, A. S., van der Marel, N., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021, A&A, 651, L6, doi: [`10.1051/0004-6361/202141057`](http://doi.org/10.1051/0004-6361/202141057)

(ref: BoothEtal2018) Booth, A. S., Walsh, C., Kama, M., et al. 2018, A&A, 611, A16, doi: [`10.1051/0004-6361/201731347`](http://doi.org/10.1051/0004-6361/201731347)

(ref: BoothEtal2024a) Booth, A. S., Leemker, M., van Dishoeck, E. F., et al. 2024a, AJ, 167, 164, doi: [`10.3847/1538-3881/ad2700`](http://doi.org/10.3847/1538-3881/ad2700)

(ref: BoothEtal2024b) Booth, A. S., Temmink, M., van Dishoeck, E. F., et al. 2024b, AJ, 167, 165, doi: [`10.3847/1538-3881/ad26ff`](http://doi.org/10.3847/1538-3881/ad26ff)

(ref: BridleSchwab1999) Bridle, A. H., & Schwab, F. R. 1999, in Astronomical Society of the Pacific Conference Series, Vol. 180, Synthesis Imaging in Radio Astronomy II, ed. G. B. Taylor, C. L. Carilli, & R. A. Perley, 371

(ref: Briggs1995) Briggs, D. S. 1995, PhD thesis, New Mexico Institute of Mining and Technology

(ref: BrownEtal2012) Brown, J. M., Herczeg, G. J., Pontoppidan, K. M., & van Dishoeck, E. F. 2012, ApJ, 744, 116, doi: [`10.1088/0004-637X/744/2/116`](http://doi.org/10.1088/0004-637X/744/2/116)

(ref: CalcinoEtal2025) Calcino, J., Price, D. J., Hilder, T., et al. 2025, MNRAS, 537, 2695, doi: [`10.1093/mnras/staf135`](http://doi.org/10.1093/mnras/staf135)

(ref: CalcinoEtal2019) Calcino, J., Price, D. J., Pinte, C., et al. 2019, MNRAS, 490, 2579, doi: [`10.1093/mnras/stz2770`](http://doi.org/10.1093/mnras/stz2770)

(ref: CASATeamEtal2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: CasassusCarcamo2022) Casassus, S., & Cárcamo, M. 2022, MNRAS, 513, 5790, doi: [`10.1093/mnras/stac1285`](http://doi.org/10.1093/mnras/stac1285)

(ref: CasassusEtal2022) Casassus, S., Cárcamo, M., Hales, A., Weber, P., & Dent, B. 2022, ApJL, 933, L4, doi: [`10.3847/2041-8213/ac75e8`](http://doi.org/10.3847/2041-8213/ac75e8)

(ref: Clark&DeLucia1976) Clark, W. W., & De Lucia, F. C. 1976, Journal of Molecular Spectroscopy, 60, 332, doi: [`10.1016/0022-2852(76)90136-3`](http://doi.org/10.1016/0022-2852(76)90136-3)

(ref: CleevesEtal2015) Cleeves, L. I., Bergin, E. A., & Harries, T. J. 2015, ApJ, 807, 2, doi: [`10.1088/0004-637X/807/1/2`](http://doi.org/10.1088/0004-637X/807/1/2)

(ref: Codella2024) Codella, C., Podio, L., De Simone, M., et al. 2024, MNRAS, 528, 7383, doi: [`10.1093/mnras/stae472`](http://doi.org/10.1093/mnras/stae472)

(ref: Cornwell2008) Cornwell, T. J. 2008, IEEE Journal of Selected Topics in Signal Processing, 2, 793, doi: [`10.1109/JSTSP.2008.2006388`](http://doi.org/10.1109/JSTSP.2008.2006388)

(ref: CridlandEtal2025) Cridland, A. J., Lega, E., & Benisty, M. 2025, A&A, 693, A86, doi: [`10.1051/0004-6361/202451140`](http://doi.org/10.1051/0004-6361/202451140)

(ref: CuroneEtal2025) Curone, P., Facchini, S., Andrews, S. M., et al. 2025, ApJL, 984, L9, doi: [`10.3847/2041-8213/adc438`](http://doi.org/10.3847/2041-8213/adc438)

(ref: CzekalaEtal2021) Czekala, I., Loomis, R. A., Teague, R., et al. 2021, ApJS, 257, 2, doi: [`10.3847/1538-4365/ac1430`](http://doi.org/10.3847/1538-4365/ac1430)

(ref: DebesEtal2017) Debes, J. H., Poteet, C. A., Jang-Condell, H., et al. 2017, ApJ, 835, 205, doi: [`10.3847/1538-4357/835/2/205`](http://doi.org/10.3847/1538-4357/835/2/205)

(ref: DongEtal2015a) Dong, R., Zhu, Z., Rafikov, R. R., & Stone, J. M. 2015, ApJL, 809, L5, doi: [`10.1088/2041-8205/809/1/L5`](http://doi.org/10.1088/2041-8205/809/1/L5)

(ref: DongEtal2018a) Dong, R., Liu, S.-y., Eisner, J., et al. 2018, ApJ, 860, 124, doi: [`10.3847/1538-4357/aac6cb`](http://doi.org/10.3847/1538-4357/aac6cb)

(ref: DutreyEtal2024) Dutrey, A., Chapillon, E., Guilloteau, S., et al. 2024, A&A, 689, L7, doi: [`10.1051/0004-6361/202451299`](http://doi.org/10.1051/0004-6361/202451299)

(ref: EistrupEtal2016) Eistrup, C., Walsh, C., & van Dishoeck, E. F. 2016, A&A, 595, A83, doi: [`10.1051/0004-6361/201628509`](http://doi.org/10.1051/0004-6361/201628509)

(ref: ErikssonEtal2025) Eriksson, L. E. J., Yang, C.-C., & Armitage, P. J. 2025, MNRAS, 537, L26, doi: [`10.1093/mnrasl/slae110`](http://doi.org/10.1093/mnrasl/slae110)

(ref: EvansEtal2019) Evans, M. G., Hartquist, T. W., Caselli, P., et al. 2019, MNRAS, 483, 1266, doi: [`10.1093/mnras/sty2765`](http://doi.org/10.1093/mnras/sty2765)

(ref: EvansEtal2015) Evans, M. G., Ilee, J. D., Boley, A. C., et al. 2015, MNRAS, 453, 1147, doi: [`10.1093/mnras/stv1698`](http://doi.org/10.1093/mnras/stv1698)

(ref: FacchiniEtal2018a) Facchini, S., Juhász, A., & Lodato, G. 2018, MNRAS, 473, 4459, doi: [`10.1093/mnras/stx2523`](http://doi.org/10.1093/mnras/stx2523)

(ref: FacchiniEtal2021) Facchini, S., Teague, R., Bae, J., et al. 2021, AJ, 162, 99, doi: [`10.3847/1538-3881/abf0a4`](http://doi.org/10.3847/1538-3881/abf0a4)

(ref: FloresEtal2023) Flores, C., Ohashi, N., Tobin, J. J., et al. 2023, ApJ, 958, 98, doi: [`10.3847/1538-4357/acf7c1`](http://doi.org/10.3847/1538-4357/acf7c1)

(ref: FolletteEtal2015) Follette, K. B., Grady, C. A., Swearingen, J. R., et al. 2015, ApJ, 798, 132, doi: [`10.1088/0004-637X/798/2/132`](http://doi.org/10.1088/0004-637X/798/2/132)

(ref: FolletteEtal2017) Follette, K. B., Rameau, J., Dong, R., et al. 2017, AJ, 153, 264, doi: [`10.3847/1538-3881/aa6d85`](http://doi.org/10.3847/1538-3881/aa6d85)

(ref: FuenteEtal2010) Fuente, A., Cernicharo, J., Agúndez, M., et al. 2010, A&A, 524, A19, doi: [`10.1051/0004-6361/201014905`](http://doi.org/10.1051/0004-6361/201014905)

(ref: GaiaCollaboration2020) Gaia Collaboration. 2020, VizieR Online Data Catalog: Gaia EDR3 (Gaia Collaboration, 2020), VizieR On-line Data Catalog: I/350. Originally published in: 2021A&amp;A...649A...1G, doi: [`10.26093/cds/vizier.1350`](http://doi.org/10.26093/cds/vizier.1350)

(ref: Galloway-SprietsmaEtal2025) Galloway-Sprietsma, M., Bae, J., Izquierdo, A. F., et al. 2025, ApJL, 984, L10, doi: [`10.3847/2041-8213/adc437`](http://doi.org/10.3847/2041-8213/adc437)

(ref: GangiEtal2022) Gangi, M., Antoniucci, S., Biazzo, K., et al. 2022, A&A, 667, A124, doi: [`10.1051/0004-6361/202244042`](http://doi.org/10.1051/0004-6361/202244042)

(ref: GarciaLopezEtal2006) Garcia Lopez, R., Natta, A., Testi, L., & Habart, E. 2006, A&A, 459, 837, doi: [`10.1051/0004-6361:20065575`](http://doi.org/10.1051/0004-6361:20065575)

(ref: GargEtal2021) Garg, H., Pinte, C., Christiaens, V., et al. 2021, MNRAS, 504, 782, doi: [`10.1093/mnras/stab800`](http://doi.org/10.1093/mnras/stab800)

(ref: GargEtal2022) Garg, H., Pinte, C., Hammond, I., et al. 2022, MNRAS, doi: [`10.1093/mnras/stac3039`](http://doi.org/10.1093/mnras/stac3039)

(ref: GarufiEtal2022a) Garufi, A., Podio, L., Codella, C., et al. 2022, A&A, 658, A104, doi: [`10.1051/0004-6361/202141264`](http://doi.org/10.1051/0004-6361/202141264)

(ref: GarufiEtal2024) Garufi, A., Ginski, C., van Holstein, R. G., et al. 2024, A&A, 685, A53, doi: [`10.1051/0004-6361/202347586`](http://doi.org/10.1051/0004-6361/202347586)

(ref: GinskiEtal2021) Ginski, C., Facchini, S., Huang, J., et al. 2021, ApJL, 908, L25, doi: [`10.3847/2041-8213/abdf57`](http://doi.org/10.3847/2041-8213/abdf57)

(ref: GoldreichTremaine1979) Goldreich, P., & Tremaine, S. 1979, ApJ, 233, 857, doi: [`10.1086/157448`](http://doi.org/10.1086/157448)

(ref: Goldsmith&Langer1999) Goldsmith, P. F., & Langer, W. D. 1999, ApJ, 517, 209, doi: [`10.1086/307195`](http://doi.org/10.1086/307195)

(ref: GonzalezEtAl2020) Gonzalez, J.-F., van der Plas, G., Pinte, C., et al. 2020, MNRAS, 499, 3837, doi: [`10.1093/mnras/staa2938`](http://doi.org/10.1093/mnras/staa2938)

(ref: GradyEtal2005) Grady, C. A., Woodgate, B. E., Bowers, C. W., et al. 2005, ApJ, 630, 958, doi: [`10.1086/430731`](http://doi.org/10.1086/430731)

(ref: GrantEtal2022) Grant, S. L., Espaillat, C. C., Brittain, S., Scott-Joseph, C., & Calvet, N. 2022, ApJ, 926, 229, doi: [`10.3847/1538-4357/ac450a`](http://doi.org/10.3847/1538-4357/ac450a)

(ref: Gray2017) Gray, R. O., Riggs, Q. S., Koen, C., et al. 2017, AJ, 154, 31, doi: [`10.3847/1538-3881/aa6d5e`](http://doi.org/10.3847/1538-3881/aa6d5e)

(ref: GuptaEtal2023) Gupta, A., Miotello, A., Manara, C. F., et al. 2023, A&A, 670, L8, doi: [`10.1051/0004-6361/202245254`](http://doi.org/10.1051/0004-6361/202245254)

(ref: HaffertEtal2019) Haffert, S. Y., Bohn, A. J., de Boer, J., et al. 2019, Nature Astronomy, 3, 749, doi: [`10.1038/s41550-019-0780-5`](http://doi.org/10.1038/s41550-019-0780-5)

(ref: HallEtal2020) Hall, C., Dong, R., Teague, R., et al. 2020, ApJ, 904, 148, doi: [`10.3847/1538-4357/abac17`](http://doi.org/10.3847/1538-4357/abac17)

(ref: HammondEtal2023) Hammond, I., Christiaens, V., Price, D. J., et al. 2023, MNRAS, 522, L51, doi: [`10.1093/mnrasl/slad027`](http://doi.org/10.1093/mnrasl/slad027)

(ref: HammondEtal2022) —. 2022, MNRAS, 515, 6109, doi: [`10.1093/mnras/stac2119`](http://doi.org/10.1093/mnras/stac2119)

(ref: HarrisEtal2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: HartiganKenyon2003) Hartigan, P., & Kenyon, S. J. 2003, ApJ, 583, 334, doi: [`10.1086/345293`](http://doi.org/10.1086/345293)

(ref: HartquistEtal1980) Hartquist, T. W., Dalgarno, A., & Oppenheimer, M. 1980, ApJ, 236, 182, doi: [`10.1086/157731`](http://doi.org/10.1086/157731)

(ref: HashimotoEtal2011) Hashimoto, J., Tamura, M., Muto, T., et al. 2011, ApJL, 729, L17, doi: [`10.1088/2041-8205/729/2/L17`](http://doi.org/10.1088/2041-8205/729/2/L17)

(ref: HennebelleEtal2017) Hennebelle, P., Lesur, G., & Fromang, S. 2017, A&A, 599, A86, doi: [`10.1051/0004-6361/201629779`](http://doi.org/10.1051/0004-6361/201629779)

(ref: Herczeg&Hillenbrand2014) Herczeg, G. J., & Hillenbrand, L. A. 2014, ApJ, 786, 97, doi: [`10.1088/0004-637X/786/2/97`](http://doi.org/10.1088/0004-637X/786/2/97)

(ref: HerczegEtal2023) Herczeg, G. J., Chen, Y., Donati, J.-F., et al. 2023, ApJ, 956, 102, doi: [`10.3847/1538-4357/acf468`](http://doi.org/10.3847/1538-4357/acf468)

(ref: Hildebrand1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: HuangEtal2023) Huang, J., Bergin, E. A., Bae, J., Benisty, M., & Andrews, S. M. 2023, ApJ, 943, 107, doi: [`10.3847/1538-4357/aca89c`](http://doi.org/10.3847/1538-4357/aca89c)

(ref: HuangEtal2024) Huang, J., Bergin, E. A., Le Gal, R., et al. 2024, ApJ, 973, 135, doi: [`10.3847/1538-4357/ad6447`](http://doi.org/10.3847/1538-4357/ad6447)

(ref: HuangEtal2018c) Huang, J., Andrews, S. M., Pérez, L. M., et al. 2018, ApJL, 869, L43, doi: [`10.3847/2041-8213/aaf7a0`](http://doi.org/10.3847/2041-8213/aaf7a0)

(ref: Hunter2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: IleeEtal2011) Ilee, J. D., Boley, A. C., Caselli, P., et al. 2011, MNRAS, 417, 2950, doi: [`10.1111/j.1365-2966.2011.19455.x`](http://doi.org/10.1111/j.1365-2966.2011.19455.x)

(ref: IsellaEtal2010) Isella, A., Carpenter, J. M., & Sargent, A. I. 2010, ApJ, 714, 1746, doi: [`10.1088/0004-637X/714/2/1746`](http://doi.org/10.1088/0004-637X/714/2/1746)

(ref: IzquierdoEtal2022) Izquierdo, A. F., Facchini, S., Rosotti, G. P., van Dishoeck, E. F., & Testi, L. 2022, ApJ, 928, 2, doi: [`10.3847/1538-4357/ac474d`](http://doi.org/10.3847/1538-4357/ac474d)

(ref: IzquierdoEtal2023) Izquierdo, A. F., Testi, L., Facchini, S., et al. 2023, A&A, 674, A113, doi: [`10.1051/0004-6361/202245425`](http://doi.org/10.1051/0004-6361/202245425)

(ref: IzquierdoEtal2025) Izquierdo, A. F., Stadler, J., Galloway-Sprietsma, M., et al. 2025, ApJL, 984, L8, doi: [`10.3847/2041-8213/adc439`](http://doi.org/10.3847/2041-8213/adc439)

(ref: JiangEtal2023) Jiang, H., Wang, Y., Ormel, C. W., Krijt, S., & Dong, R. 2023, A&A, 678, A33, doi: [`10.1051/0004-6361/202346637`](http://doi.org/10.1051/0004-6361/202346637)

(ref: KepplerEtal2018) Keppler, M., Benisty, M., Müller, A., et al. 2018, A&A, 617, A44, doi: [`10.1051/0004-6361/201832957`](http://doi.org/10.1051/0004-6361/201832957)

(ref: KeyteEtal2023) Keyte, L., Kama, M., Booth, A. S., et al. 2023, Nature Astronomy, 7, 684, doi: [`10.1038/s41550-023-01951-9`](http://doi.org/10.1038/s41550-023-01951-9)

(ref: KratterLodato2016) Kratter, K., & Lodato, G. 2016, ARA&A, 54, 271, doi: [`10.1146/annurev-astro-081915-023307`](http://doi.org/10.1146/annurev-astro-081915-023307)

(ref: KuffmeierEtal2019) Kuffmeier, M., Calcutt, H., & Kristensen, L. E. 2019, A&A, 628, A112, doi: [`10.1051/0004-6361/201935504`](http://doi.org/10.1051/0004-6361/201935504)

(ref: KuffmeierEtal2020) Kuffmeier, M., Goicovic, F. G., & Dullemond, C. P. 2020, A&A, 633, A3, doi: [`10.1051/0004-6361/201936820`](http://doi.org/10.1051/0004-6361/201936820)

(ref: KuoEtal2022) Kuo, I. H. G., Yen, H.-W., Gu, P.-G., & Chang, T.-E. 2022, ApJ, 938, 50, doi: [`10.3847/1538-4357/ac9228`](http://doi.org/10.3847/1538-4357/ac9228)

(ref: KuznetsovaEtal2022) Kuznetsova, A., Bae, J., Hartmann, L., & Low, M.-M. M. 2022, ApJ, 928, 92, doi: [`10.3847/1538-4357/ac54a8`](http://doi.org/10.3847/1538-4357/ac54a8)

(ref: LawEtal2023) Law, C. J., Booth, A. S., & Öberg, K. I. 2023, ApJL, 952, L19, doi: [`10.3847/2041-8213/acdfd0`](http://doi.org/10.3847/2041-8213/acdfd0)

(ref: LawEtal2024) Law, C. J., Benisty, M., Facchini, S., et al. 2024, ApJ, 964, 190, doi: [`10.3847/1538-4357/ad24d2`](http://doi.org/10.3847/1538-4357/ad24d2)

(ref: LeGalEtal2019a) Le Gal, R., Öberg, K. I., Loomis, R. A., Pegues, J., & Bergner, J. B. 2019, ApJ, 876, 72, doi: [`10.3847/1538-4357/ab1416`](http://doi.org/10.3847/1538-4357/ab1416)

(ref: LeemkerEtal2022) Leemker, M., Booth, A. S., van Dishoeck, E. F., et al. 2022, A&A, 663, A23, doi: [`10.1051/0004-6361/202243229`](http://doi.org/10.1051/0004-6361/202243229)

(ref: LesurEtal2015) Lesur, G., Hennebelle, P., & Fromang, S. 2015, A&A, 582, L9, doi: [`10.1051/0004-6361/201526734`](http://doi.org/10.1051/0004-6361/201526734)

(ref: LesurEtal2023) Lesur, G., Flock, M., Ercolano, B., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 465

(ref: LongEtal2018f) Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17, doi: [`10.3847/1538-4357/aae8e1`](http://doi.org/10.3847/1538-4357/aae8e1)

(ref: LongEtal2019) Long, F., Herczeg, G. J., Harsono, D., et al. 2019, ApJ, 882, 49, doi: [`10.3847/1538-4357/ab2d2d`](http://doi.org/10.3847/1538-4357/ab2d2d)

(ref: LongariniEtal2024) Longarini, C., Lodato, G., Clarke, C. J., et al. 2024, A&A, 686, L6, doi: [`10.1051/0004-6361/202450187`](http://doi.org/10.1051/0004-6361/202450187)

(ref: LoomisEtal2025) Loomis, R. A., Facchini, S., Benisty, M., et al. 2025, ApJL, 984, L7, doi: [`10.3847/2041-8213/adc43a`](http://doi.org/10.3847/2041-8213/adc43a)

(ref: LuhmanEtal2023a) Luhman, K. L. 2023, AJ, 165, 37, doi: [`10.3847/1538-3881/ac9da3`](http://doi.org/10.3847/1538-3881/ac9da3)

(ref: MaciasEtal2021) Macı́as, E., Guerra-Alvarado, O., Carrasco-González, C., et al. 2021, A&A, 648, A33, doi: [`10.1051/0004-6361/202039812`](http://doi.org/10.1051/0004-6361/202039812)

(ref: ManaraEtal2023) Manara, C. F., Ansdell, M., Rosotti, G. P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 539, doi: [`10.48550/arXiv.2203.09930`](http://doi.org/10.48550/arXiv.2203.09930)

(ref: ManaraEtal2019) Manara, C. F., Tazzari, M., Long, F., et al. 2019, A&A, 628, A95, doi: [`10.1051/0004-6361/201935964`](http://doi.org/10.1051/0004-6361/201935964)

(ref: MesaEtal2022) Mesa, D., Ginski, C., Gratton, R., et al. 2022, A&A, 658, A63, doi: [`10.1051/0004-6361/202142219`](http://doi.org/10.1051/0004-6361/202142219)

(ref: MontesinosEtal2016) Montesinos, M., Perez, S., Casassus, S., et al. 2016, ApJL, 823, L8, doi: [`10.3847/2041-8205/823/1/L8`](http://doi.org/10.3847/2041-8205/823/1/L8)

(ref: Mooley2013) Mooley, K., Hillenbrand, L., Rebull, L., Padgett, D., & Knapp, G. 2013, ApJ, 771, 110, doi: [`10.1088/0004-637X/771/2/110`](http://doi.org/10.1088/0004-637X/771/2/110)

(ref: NealonEtal2018) Nealon, R., Dipierro, G., Alexander, R., Martin, R. G., & Nixon, C. 2018, MNRAS, 481, 20, doi: [`10.1093/mnras/sty2267`](http://doi.org/10.1093/mnras/sty2267)

(ref: OebergBergin2021) Öberg, K. I., & Bergin, E. A. 2021, Phys. Rep., 893, 1, doi: [`10.1016/j.physrep.2020.09.004`](http://doi.org/10.1016/j.physrep.2020.09.004)

(ref: OebergEtal2023) Öberg, K. I., Facchini, S., & Anderson, D. E. 2023, ARA&A, 61, 287, doi: [`10.1146/annurev-astro-022823-040820`](http://doi.org/10.1146/annurev-astro-022823-040820)

(ref: OebergEtal2011) Öberg, K. I., Murray-Clay, R., & Bergin, E. A. 2011, ApJL, 743, L16, doi: [`10.1088/2041-8205/743/1/L16`](http://doi.org/10.1088/2041-8205/743/1/L16)

(ref: OebergEtal2021) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1, doi: [`10.3847/1538-4365/ac1432`](http://doi.org/10.3847/1538-4365/ac1432)

(ref: OhashiEtal2020) Ohashi, S., Kataoka, A., van der Marel, N., et al. 2020, ApJ, 900, 81, doi: [`10.3847/1538-4357/abaab4`](http://doi.org/10.3847/1538-4357/abaab4)

(ref: OnoEtal2025) Ono, T., Okamura, T., Okuzumi, S., & Muto, T. 2025, PASJ, 77, 149, doi: [`10.1093/pasj/psae106`](http://doi.org/10.1093/pasj/psae106)

(ref: OyaEtal2025) Oya, Y., Saiga, E., Miotello, A., et al. 2025, ApJ, 980, 263, doi: [`10.3847/1538-4357/adabe7`](http://doi.org/10.3847/1538-4357/adabe7)

(ref: Pacheco-VazquezEtal2016) Pacheco-Vázquez, S., Fuente, A., Baruteau, C., et al. 2016, A&A, 589, A60, doi: [`10.1051/0004-6361/201527089`](http://doi.org/10.1051/0004-6361/201527089)

(ref: PadoanEtal2024) Padoan, P., Pan, L., Pelkonen, V.-M., Haugboelle, T., & Nordlund, A. 2024, arXiv e-prints, arXiv:2405.07334, doi: [`10.48550/arXiv.2405.07334`](http://doi.org/10.48550/arXiv.2405.07334)

(ref: Paneque-CarrenoEtal2021) Paneque-Carreño, T., Pérez, L. M., Benisty, M., et al. 2021, ApJ, 914, 88, doi: [`10.3847/1538-4357/abf243`](http://doi.org/10.3847/1538-4357/abf243)

(ref: PerezEtal2016) Pérez, L. M., Carpenter, J. M., Andrews, S. M., et al. 2016, Science, 353, 1519, doi: [`10.1126/science.aaf8296`](http://doi.org/10.1126/science.aaf8296)

(ref: PinedaEtal2019) Pineda, J. E., Szulágyi, J., Quanz, S. P., et al. 2019, ApJ, 871, 48, doi: [`10.3847/1538-4357/aaf389`](http://doi.org/10.3847/1538-4357/aaf389)

(ref: PinteEtal2023a) Pinte, C., Teague, R., Flaherty, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 645

(ref: PodioEtal2021) Podio, L., Tabone, B., Codella, C., et al. 2021, A&A, 648, A45, doi: [`10.1051/0004-6361/202038429`](http://doi.org/10.1051/0004-6361/202038429)

(ref: RampinelliEtal2024) Rampinelli, L., Facchini, S., Leemker, M., et al. 2024, A&A, 689, A65, doi: [`10.1051/0004-6361/202449698`](http://doi.org/10.1051/0004-6361/202449698)

(ref: ReggianiEtal2018) Reggiani, M., Christiaens, V., Absil, O., et al. 2018, A&A, 611, A74, doi: [`10.1051/0004-6361/201732016`](http://doi.org/10.1051/0004-6361/201732016)

(ref: RenEtal2018) Ren, B., Dong, R., Esposito, T. M., et al. 2018, ApJL, 857, L9, doi: [`10.3847/2041-8213/aab7f5`](http://doi.org/10.3847/2041-8213/aab7f5)

(ref: RenEtal2020) Ren, B., Dong, R., van Holstein, R. G., et al. 2020, ApJL, 898, L38, doi: [`10.3847/2041-8213/aba43e`](http://doi.org/10.3847/2041-8213/aba43e)

(ref: RenEtal2023b) Ren, B. B., Benisty, M., Ginski, C., et al. 2023, A&A, 680, A114, doi: [`10.1051/0004-6361/202347353`](http://doi.org/10.1051/0004-6361/202347353)

(ref: Riviere-MarichalarEtal2020) Rivière-Marichalar, P., Fuente, A., Le Gal, R., et al. 2020, A&A, 642, A32, doi: [`10.1051/0004-6361/202038549`](http://doi.org/10.1051/0004-6361/202038549)

(ref: SafonovEtal2022) Safonov, B. S., Strakhov, I. A., Goliguzova, M. V., & Voziakova, O. V. 2022, AJ, 163, 31, doi: [`10.3847/1538-3881/ac36cb`](http://doi.org/10.3847/1538-3881/ac36cb)

(ref: SalykEtal2013) Salyk, C., Herczeg, G. J., Brown, J. M., et al. 2013, ApJ, 769, 21, doi: [`10.1088/0004-637X/769/1/21`](http://doi.org/10.1088/0004-637X/769/1/21)

(ref: SchworerEtal2017) Schworer, G., Lacour, S., Huélamo, N., et al. 2017, ApJ, 842, 77, doi: [`10.3847/1538-4357/aa74b7`](http://doi.org/10.3847/1538-4357/aa74b7)

(ref: SemenovWiebe2011) Semenov, D., & Wiebe, D. 2011, ApJS, 196, 25, doi: [`10.1088/0067-0049/196/2/25`](http://doi.org/10.1088/0067-0049/196/2/25)

(ref: SoderblomEtal2014) Soderblom, D. R., Hillenbrand, L. A., Jeffries, R. D., Mamajek, E. E., & Naylor, T. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 219–241, doi: [`10.2458/azu_uapress_9780816531240-ch010`](http://doi.org/10.2458/azu_uapress_9780816531240-ch010)

(ref: SpeedieEtal2024) Speedie, J., Dong, R., Hall, C., et al. 2024, Nature, 633, 58, doi: [`10.1038/s41586-024-07877-0`](http://doi.org/10.1038/s41586-024-07877-0)

(ref: SpeedieEtal2025) Speedie, J., Dong, R., Teague, R., et al. 2025, arXiv e-prints, arXiv:2503.01957, doi: [`10.48550/arXiv.2503.01957`](http://doi.org/10.48550/arXiv.2503.01957)

(ref: StapperEtal2022) Stapper, L. M., Hogerheijde, M. R., van Dishoeck, E. F., & Mentel, R. 2022, A&A, 658, A112, doi: [`10.1051/0004-6361/202142164`](http://doi.org/10.1051/0004-6361/202142164)

(ref: SuBai2024) Su, Z., & Bai, X.-N. 2024, ApJ, 975, 126, doi: [`10.3847/1538-4357/ad7581`](http://doi.org/10.3847/1538-4357/ad7581)

(ref: TangEtal2014) Tang, Y.-W., Dutrey, A., Guilloteau, S., et al. 2014, ApJ, 793, 10, doi: [`10.1088/0004-637X/793/1/10`](http://doi.org/10.1088/0004-637X/793/1/10)

(ref: TangEtal2017) Tang, Y.-W., Guilloteau, S., Dutrey, A., et al. 2017, ApJ, 840, 32, doi: [`10.3847/1538-4357/aa6af7`](http://doi.org/10.3847/1538-4357/aa6af7)

(ref: Teague2019) Teague, R. 2019, The Journal of Open Source Software, 4, 1632, doi: [`10.21105/joss.01632`](http://doi.org/10.21105/joss.01632)

(ref: Teague2020) —. 2020, richteague/keplerian_mask: Initial Release, 1.0, Zenodo, doi: [`10.5281/zenodo.4321137`](http://doi.org/10.5281/zenodo.4321137)

(ref: TeagueForeman-Mackey2018) Teague, R., & Foreman-Mackey, D. 2018, Research Notes of the American Astronomical Society, 2, 173, doi: [`10.3847/2515-5172/aae265`](http://doi.org/10.3847/2515-5172/aae265)

(ref: TeagueEtal2022) Teague, R., Bae, J., Andrews, S. M., et al. 2022, ApJ, 936, 163, doi: [`10.3847/1538-4357/ac88ca`](http://doi.org/10.3847/1538-4357/ac88ca)

(ref: TeagueEtal2025) Teague, R., Benisty, M., Facchini, S., et al. 2025, ApJL, 984, L6, doi: [`10.3847/2041-8213/adc43b`](http://doi.org/10.3847/2041-8213/adc43b)

(ref: TripathiEtal2017) Tripathi, A., Andrews, S. M., Birnstiel, T., & Wilner, D. J. 2017, ApJ, 845, 44, doi: [`10.3847/1538-4357/aa7c62`](http://doi.org/10.3847/1538-4357/aa7c62)

(ref: UbeiraGabelliniEtal2019) Ubeira Gabellini, M. G., Miotello, A., Facchini, S., et al. 2019, MNRAS, 486, 4638, doi: [`10.1093/mnras/stz1138`](http://doi.org/10.1093/mnras/stz1138)

(ref: UyamaEtal2020b) Uyama, T., Muto, T., Mawet, D., et al. 2020, AJ, 159, 118, doi: [`10.3847/1538-3881/ab7006`](http://doi.org/10.3847/1538-3881/ab7006)

(ref: vanBoekelEtal2017) van Boekel, R., Henning, T., Menu, J., et al. 2017, ApJ, 837, 132, doi: [`10.3847/1538-4357/aa5d68`](http://doi.org/10.3847/1538-4357/aa5d68)

(ref: vanderMarelEtal2021b) van der Marel, N., Booth, A. S., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021a, A&A, 651, L5, doi: [`10.1051/0004-6361/202141051`](http://doi.org/10.1051/0004-6361/202141051)

(ref: vanderMarelEtal2021a) van der Marel, N., Birnstiel, T., Garufi, A., et al. 2021b, AJ, 161, 33, doi: [`10.3847/1538-3881/abc3ba`](http://doi.org/10.3847/1538-3881/abc3ba)

(ref: vanGelderEtal2021) van Gelder, M. L., Tabone, B., van Dishoeck, E. F., & Godard, B. 2021, A&A, 653, A159, doi: [`10.1051/0004-6361/202141591`](http://doi.org/10.1051/0004-6361/202141591)

(ref: van’tHoffEtal2023) van’t Hoff, M. L. R., Tobin, J. J., Li, Z.-Y., et al. 2023, ApJ, 951, 10, doi: [`10.3847/1538-4357/accf87`](http://doi.org/10.3847/1538-4357/accf87)

(ref: VeronesiEtal2021) Veronesi, B., Paneque-Carreño, T., Lodato, G., et al. 2021, ApJL, 914, L27, doi: [`10.3847/2041-8213/abfe6a`](http://doi.org/10.3847/2041-8213/abfe6a)

(ref: VidalEtal2017) Vidal, T. H. G., Loison, J.-C., Jaziri, A. Y., et al. 2017, MNRAS, 469, 435, doi: [`10.1093/mnras/stx828`](http://doi.org/10.1093/mnras/stx828)

(ref: VieiraEtal2003) Vieira, S. L. A., Corradi, W. J. B., Alencar, S. H. P., et al. 2003, AJ, 126, 2971, doi: [`10.1086/379553`](http://doi.org/10.1086/379553)

(ref: VioqueEtal2018) Vioque, M., Oudmaijer, R. D., Baines, D., Mendigutı́a, I., & Pérez-Martı́nez, R. 2018, A&A, 620, A128, doi: [`10.1051/0004-6361/201832870`](http://doi.org/10.1051/0004-6361/201832870)

(ref: VirtanenEtal2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: WagnerEtal2019b) Wagner, K., Stone, J. M., Spalding, E., et al. 2019, ApJ, 882, 20, doi: [`10.3847/1538-4357/ab32ea`](http://doi.org/10.3847/1538-4357/ab32ea)

(ref: WagnerEtal2023) Wagner, K., Stone, J., Skemer, A., et al. 2023, Nature Astronomy, 7, 1208, doi: [`10.1038/s41550-023-02028-3`](http://doi.org/10.1038/s41550-023-02028-3)

(ref: WagnerEtal2024) Wagner, K., Leisenring, J., Cugno, G., et al. 2024, AJ, 167, 181, doi: [`10.3847/1538-3881/ad11d5`](http://doi.org/10.3847/1538-3881/ad11d5)

(ref: WichittanakomEtal2020) Wichittanakom, C., Oudmaijer, R. D., Fairlamb, J. R., et al. 2020, MNRAS, 493, 234, doi: [`10.1093/mnras/staa169`](http://doi.org/10.1093/mnras/staa169)

(ref: WinterEtal2024) Winter, A. J., Benisty, M., & Andrews, S. M. 2024, ApJL, 972, L9, doi: [`10.3847/2041-8213/ad6d5d`](http://doi.org/10.3847/2041-8213/ad6d5d)

(ref: WoelferEtal2021) Wölfer, L., Facchini, S., Kurtovic, N. T., et al. 2021, A&A, 648, A19, doi: [`10.1051/0004-6361/202039469`](http://doi.org/10.1051/0004-6361/202039469)

(ref: WoelferEtal2023) Wölfer, L., Facchini, S., van der Marel, N., et al. 2023, A&A, 670, A154, doi: [`10.1051/0004-6361/202243601`](http://doi.org/10.1051/0004-6361/202243601)

(ref: WoelferEtal2025) Wölfer, L., Barraza-Alfaro, M., Teague, R., et al. 2025, ApJL, 984, L22, doi: [`10.3847/2041-8213/adc42c`](http://doi.org/10.3847/2041-8213/adc42c)

(ref: YamatoEtal2023) Yamato, Y., Aikawa, Y., Ohashi, N., et al. 2023, ApJ, 951, 11, doi: [`10.3847/1538-4357/accd71`](http://doi.org/10.3847/1538-4357/accd71)

(ref: YangEtal2023h) Yang, H., Fernández-López, M., Li, Z.-Y., et al. 2023, ApJL, 948, L2, doi: [`10.3847/2041-8213/acccf8`](http://doi.org/10.3847/2041-8213/acccf8)

(ref: YenEtal2016) Yen, H.-W., Koch, P. M., Liu, H. B., et al. 2016, ApJ, 832, 204, doi: [`10.3847/0004-637X/832/2/204`](http://doi.org/10.3847/0004-637X/832/2/204)

(ref: YonedaEtal2016) Yoneda, H., Tsukamoto, Y., Furuya, K., & Aikawa, Y. 2016, ApJ, 833, 105, doi: [`10.3847/1538-4357/833/1/105`](http://doi.org/10.3847/1538-4357/833/1/105)

(ref: YoshidaEtal2024) Yoshida, T. C., Nomura, H., Law, C. J., et al. 2024, ApJL, 971, L15, doi: [`10.3847/2041-8213/ad654c`](http://doi.org/10.3847/2041-8213/ad654c)

(ref: ZhangEtal2024_SO) Zhang, Z. E., Sakai, N., Ohashi, S., et al. 2024, ApJ, 966, 207, doi: [`10.3847/1538-4357/ad3921`](http://doi.org/10.3847/1538-4357/ad3921)

(ref: ZhuEtal2015b) Zhu, Z., Dong, R., Stone, J. M., & Rafikov, R. R. 2015, ApJ, 813, 88, doi: [`10.1088/0004-637X/813/2/88`](http://doi.org/10.1088/0004-637X/813/2/88)

(ref: ZhuEtal2025) Zhu, Z., Zhang, S., & Johnson, T. M. 2025, ApJ, 980, 259, doi: [`10.3847/1538-4357/adae0d`](http://doi.org/10.3847/1538-4357/adae0d)

(ref: ZiamprasEtal2025) Ziampras, A., Dullemond, C. P., Birnstiel, T., Benisty, M., & Nelson, R. P. 2025, MNRAS, doi: [`10.1093/mnras/staf785`](http://doi.org/10.1093/mnras/staf785)

[^1]: For MWC 758 we only considered `solint` parameters $\geq60$ s. For shorter solution intervals the peak SNR leveled off and the phase gain solutions obtained for the EBs taken on Dec. 15 and 16, 2017 became very extreme ($>150$ or $<-150$ deg) and heavily time-dependent for most antennas, leading to substantial flux-scale offset variations among the long-baseline EBs.

[^2]: Because the too short solution intervals (scan length $\approx30$ to 60 s) led to too high gain solutions for most of the antennas.

</paper>

Write the methods card for this paper.