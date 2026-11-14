# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...690A.255D\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...690A.255D",
 "title": "Carbon envelopes around merging galaxies at z ∼ 4.5",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Di Cesare, C.",
 "n_authors": 6,
 "arxiv_id": "2401.03020",
 "doi": "10.1051/0004-6361/202449164",
 "alma_projects_linked_by_archive": [
  "2017.1.00428.L"
 ]
}
```

Paper text:
<paper>
# Carbon envelopes around merging galaxies at z $\sim$ 4.5

Galaxies evolve through a dynamic exchange of material with their immediate surrounding environment, the so-called circumgalactic medium (CGM). Understanding the physics of gas flows and the nature of the CGM is thus fundamental to studying galaxy evolution, especially at $4 \leq z \leq 6$ (i.e. at post-Reionization Epoch) when galaxies rapidly assembled their masses and reached their chemical maturity. Galactic outflows are predicted to enrich the CGM with metals, although gas stripping in systems undergoing a major merger has also been suggested to play a role.

In this work, we explore the metal enrichment of the medium around merging galaxies at $z \sim 4.5$, observed by the ALMA Large Program to INvestigate \[CII\] at Early times (ALPINE). To do so, we study the nature of the \[CII\]158 $\mu$m emission in the CGM around these systems, using simulations to help disentangle the mechanisms contributing to the CGM metal pollution.

By adopting an updated classification of major merger systems in the ALPINE survey, we select and analyze merging galaxies whose components can be spatially and/or spectrally resolved in a robust way. Thus, we can distinguish between the \[CII\] emission coming from the single components of the system and that coming from the system as a whole. We also make use of the `dustyGadget` cosmological simulation to select synthetic analogs of observed galaxies and guide the interpretation of the observational results.

We find a large diffuse \[CII\] envelope ($\gtrsim 20$ kpc) embedding all the merging systems, with at least $25 \%$ of the total \[CII\] emission coming from the medium *between* the galaxies. Using predictions from `dustyGadget` we suggest that this emission has a multi-fold nature, with dynamical interactions between galaxies playing a major role in stripping the gas and enriching the medium with heavy elements.

# Introduction

The circumgalactic medium (CGM) is a buffer medium between interstellar and intergalactic media (ISM, IGM). It regulates gas flows, stellar feedback and, consequently, star formation activity and galaxy growth. Generally, one refers to the CGM as the gas outside the galaxy, but indicatively within one virial radius $R_{vir}$ of its dark matter (DM) halo. However, it is important to keep in mind that some of the processes involving the CGM, for example galactic outflows, can reach larger radii (cite: Tumlinson+2017; Faucher+Oh2023). The CGM is a fundamental component in galaxy evolution, and studying it, both in emission and absorption provides hints on how galaxies assemble their masses through cosmic time. To understand the cycle of baryons between the ISM and the CGM we need observations of the stellar component and of the multiple gas phases both within and around galaxies (see (cite: CelineHowk2020) for a review on the baryon and metal cycles in galaxies). In this context, the Atacama Large Millimeter/submillimeter Array (ALMA) has recently opened a window to explore the cold neutral and molecular gas in early galaxies with unprecedented levels of detail (cite: Capak+2015; LeFevre+2020; Bouwens+2022). On the other hand, we need simulations able to resolve the characteristic scales of CGM/ISM, which usually adopt zoom-in refinement schemes[^2] (see (cite: Pallottini+2017; Lupi+2020; Lupi+2020b; Pallottini+2022)), or cosmological boxes with a moderate ($\sim 100$ pc) spatial resolution (see, for example, (cite: Katz+2017) where the authors include on-the-fly radiative transfer and detailed non-equilibrium chemistry, to model self-consistently the ISM of high redshift galaxies). Finally, see (cite: Faucher+Oh2023) for a recent general review of the key physical processes that operate in the CGM from a theoretical point of view.

In the last decades, theories of galaxy evolution and cosmological numerical simulations have predicted that high-$z$ galaxies assemble their masses via both cold gas accretion from the IGM (cite: Dekel+2009; Topping+2022) and major mergers i.e. dynamical interactions between galaxies of nearly equal stellar masses (cite: Hopkins+2010; Schaye+2015; Duncan+2019; Romano+2021). In particular, dynamical interactions between galaxies can drive a significant amount of gas towards the center of the interacting system boosting the efficiency of star formation - up to a factor 2 for major mergers - and also trigger starburst and active galactic nuclei (AGN) activity ((cite: Oser+2012; LopezSanjuan2012; Kaviraj+2014; Behroozi+2015; Reeves+2023)). Moreover, ongoing and post-mergers episodes can disturb and change the morphology of the galaxies involved, leading to tails of stripped material (i.e. tidal tails), irregular shapes, and disturbed velocity fields (cite: Conselice+2003; Conselice+2008; Casteels+2014). Tidal tails are challenging to observe at high redshift because of the diffuse and faint nature of the stripped gas. However, thanks to ALMA we can study the efficiency of gas stripping and circumgalactic gas mixing in the early Universe, by mapping the morphology and the kinematics of the CGM around merging galaxies using bright far-infrared (FIR) lines such as the singly ionized carbon (hereafter \[CII\]) at 158 $\mu$m, which is generally the brightest FIR emission line for star-forming galaxies (cite: CarilliWalter2013).

\[CII\] 158 $\mu$m is an important tracer of the ISM in the local and high-$z$ galaxies and, thanks to the low ionization potential (11.26 eV) of the neutral carbon, it is abundant in both the cold and warm ISM, as well as in the molecular one. Via its fine structure emission line at 158 $\mu$m ($\rm {}^2P_{3/2}^0  \rightarrow  \rm {}^2P_{1/2}^0$), it acts as a coolant in the cold ISM, then, it is considered as one of the main tracer of cold gas in galaxies, star-forming regions and molecular clouds. As a consequence, many studies focused on the investigation of the \[CII\] emission and, in particular, the \[CII\] - star formation rate (SFR) relation in the local Universe and at high-redshift, using both observations (cite: DeLooze+2014; Herrera-Camus+2015; Herrera-Camus+2018; Carniani+2018; Schaerer+2020; Romano+2022) and simulations (cite: Katz+2017; Popping+2019; Ferrara+2019; Lupi+2020; Vallini+2020; Schimek+2023).

Observations of \[CII\] in early main-sequence galaxies led to the discovery of extended \[CII\] *envelopes* (up to 10 kpc) around these systems. These envelopes were at first found by stacking the \[CII\] emission in 18 ALMA-detected star-forming galaxies at 5 \< $z$ \< 7 (cite: Fujimoto+2019) and in a large sample of normal star-forming galaxies at 4 \< $z$ \< 6 (cite: Ginolfi+2020b), and later confirmed, on an individual basis, by (cite: Fujimoto+2020) and (cite: Lambert+2023). These extended emissions have been found also at higher redshifts, up to $z \sim 7$, see for example (cite: Herrera-Camus+2021; Fudamoto+2022; Akins+2022). However, see (cite: Posses+2023) for an example of a normal star-forming galaxy at $z \sim 7$ in which no extended \[CII\] has been detected.

In this paper, we present a study on the properties of \[CII\] emission around major merging systems at $z \sim 4.5$, with the aim of characterizing the metal enrichment of their inner CGM and investigating its dependence on the dynamical interaction between the galaxies. Our target systems are drawn from the ALMA Large Program to INvestigate \[CII\] at Early times (ALPINE), an ALMA large program that observed \[CII\] and thermal dust continuum emission for a large sample of main-sequence galaxies in the redshift range $4.4 < z < 5.9$. The interested reader can find more information on the detection strategy, the data processing, and the ancillary data of the ALPINE sample in (cite: LeFevre+2020; Bethermin+2020; Faisst+2020), respectively. The analysis of the \[CII\] emission has revealed a diverse distribution of morphological and kinematical properties in the ALPINE sample (cite: Faisst+2020; Jones+2021), with the detection of signatures of metal-enriched gas outflows powered by star formation activity in the high-velocity tails of the stacked \[CII\] emission spectrum (cite: Ginolfi+2020b). Also, a detailed morpho-spectral decomposition analysis in one of the ALPINE systems undergoing major merging has revealed the presence of a widespread \[CII\] emission component, extending to scales of a few tens of kpc, which has been interpreted as a possible signature of processed ISM stripped by the strong gravitational interaction, suggesting that mergers could be an efficient mechanism of metal enrichment and gas mixing in the CGM around high-$z$ galaxies (cite: Ginolfi+2020a; Jones+2020).

Motivated by these findings, we apply a similar morpho-spectral decomposition analysis on additional systems classified as mergers in the ALPINE sample. To this aim, we make use of the merger classification of ALPINE galaxies carried out by (cite: Romano+2021). The observational part of this work is complemented with predictions from cosmological simulations run with the hydrodynamical code `dustyGadget` (cite: Graziani+2020), which guide our interpretation of the results. We would like to clarify that throughout the paper when presenting results based on simulations, we use the mass of carbon in the cold ISM medium (T $\lesssim 10^4$ K) as a proxy to estimate the expected \[CII\] emission. Thus, we do not employ any radiative transfer code to predict the \[CII\] luminosity, and we do not assume any empirical relation to link the physical properties of galaxies with the expected \[CII\] luminosity.

The paper is organized as follows: in Section [2](#sec:observations) we describe the selected observational sample and the analysis we carried out; Section [3](#sec:diffEmission) presents the \[CII\] diffuse emission that we find in the observed candidates, and its interpretation; in Section [4](#sec:simulations) we introduce the hydrodynamical code `dustyGadget`, explain the adopted procedure to identify synthetic major mergers, their time evolution, and their gas distribution. Finally, we exploit the predictions from `dustyGadget` to interpret the observed \[CII\] diffuse emission, in Section [5](#sec:discussion). Our conclusions are drawn in Section [6](#sec:conclusion).

Throughout the paper, we assume a flat $\Lambda$CDM cosmology with cosmological parameters from (cite: PLANK+2016) consistent with that assumed by `dustyGadget` simulation (see Section [4](#sec:simulations)) and adopt a (cite: Salpeter+1955) initial mass function (IMF). All the stellar masses and star formation rates in this paper have been converted to a (cite: Salpeter+1955) IMF following the conversion factors from (cite: Madau&Dickinson2014). At $z \sim 4.6$ - that is the mean redshift of our sample - 1 arcsecond corresponds to 6.69 proper kpc.

# Observational sample and data processing

In this section we first briefly introduce the ALPINE survey and the properties of the target galaxy sample; and then discuss the classification done by (cite: Romano+2021) on merging systems, and how we selected - among these - major mergers needed for the aim of this work. Finally, we describe the ALMA data reduction procedure and the analysis we performed on our sample of major merging galaxies.

| source ID | $z_1$ | $z_2$ | $\Delta v \: [\rm km/s]$ | $r_p \: [\rm kpc]$ | $\mu _{\rm [CII]}$ | $\mu _{\rm K}$ | Log($\rm M_\star / M_\odot$) | Log($\rm SFR / M_\odot yr^{-1}$) |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| DC_818760 | 4.5626 | 4.5609 | 92.3 | 9.9 | 1.3 | 2.6 | 10.85$^{+0.11}_{-0.10}$ | 2.88$^{+0.19}_{-0.25}$ |
| DC_873321 | 5.1545 | 5.1544 | 4.5 | 6.5 | 1.2 | 3.1 | 10.18$^{+0.13}_{-0.16}$ | 2.16$^{+0.22}_{-0.17}$ |
| vc_5100541407 | 4.5628 | 4.5628 | 1.9 | 13.8 | 1.6 | 1.4 | 10.33$^{+0.14}_{-0.15}$ | 1.74$^{+0.26}_{-0.23}$ |
| vc_5100822662 | 4.5210 | 4.5205 | 22.3 | 10.9 | 1.6 | 1.7 | 10.39$^{+0.13}_{-0.14}$ | 2.02$^{+0.23}_{-0.24}$ |
| vc_5101209780 | 4.5724 | 4.5684 | 217.3 | 10.8 | 4.1 | 2.5 | 10.27$^{+0.12}_{-0.12}$ | 1.79$^{+0.25}_{-0.21}$ |
| vc_5180966608 | 4.5294 | 4.5293 | 8.9 | 7.2 | 3.0 | 3.7 | 11.04$^{+0.12}_{-0.13}$ | 2.35$^{+0.27}_{-0.25}$ |

## Targets selection

The ALPINE survey is designed to detect the \[CII\] line at 158 $\mu$m rest-frame and the surrounding FIR continuum emission for a sample of 118 normal galaxies at $4.4 < z < 5.9$. Its targets are selected from the Cosmic Evolution Survey (COSMOS; (cite: Scoville+2007a; Scoville+2007b)) and Extended Chandra Deep Field South (E-CDFS; (cite: Giavalisco+2004; Cardamone+2010)) fields. In the following, we use "vc" and "DC" to respectively refer to vuds_cosmos and DEIMOS_COSMOS sources. Since these fields have been targeted by several observational campaigns, a wealth of ancillary multi-wavelength photometric data (from rest-frame UV to FIR) is available, which made it possible to recover physical properties such as stellar masses ($\rm M_\star$) and SFR through spectral energy distribution (SED)-fitting; these estimates have been performed adopting a Chabrier IMF ((cite: Chabrier2003), see (cite: Faisst+2020) for a detailed description). With stellar masses in the range $9 \leq \rm Log(M_\star/M_\odot) \leq 11$ and star formation rates of $1 \leq \rm Log(SFR/M_\odot yr^{-1}) \leq 3$, ALPINE galaxies lie on the so-called main sequence of star-forming galaxies (cite: Rodighiero+2011; Tasca+2015), being thus representative of the underlying galaxy population at $\rm z \sim 5$ (cite: Speagle+2014).

To study the metal enrichment of the CGM around high-$z$ merging galaxies we exploit the work of (cite: Romano+2021), who combined the morpho-kinematic information provided by the \[CII\] emission with archival multi-wavelength photometry to identify merging systems in the ALPINE sample, and the fraction of major mergers within this subset (see also (cite: LeFevre+2020; Jones+2021)). According to their classification criteria, (cite: Romano+2021) found that the ALPINE sample is composed of 31% of mergers (23 out of 75 [^3]), leading to a major merger fraction of $f_{\rm MM} \sim 0.44$ (0.34) at $z \sim 4.5$ (5.5). This result is in good agreement with morphological studies by (cite: Conselice+2009) at the same redshift and, when combined with other works down to the Local Universe, suggests a rapid increase in the cosmic merger fraction from $z = 0$ to $z \sim 2$, a peak at $z \sim 2-3$ and a possible slow decline for $z \geq 3$.

For the aim of this study, starting from the classification by (cite: Romano+2021), we selected major merging systems that are spatially and/or spectrally separated in a robust way. In particular, we looked for merging systems with:

1.  a velocity separation $\Delta v \leq 500 \: \rm km/s$, so that the two systems can be considered as gravitationally bound (see (cite: Patton+2000; Lin+2008; Ventou+2017));

2.  a projected distance $r_{\rm p} > 4 \:$kpc, where $r_{\rm p} = \theta \times d_{\rm A}(z_m)$, $\theta$ is the angular separation in arcsec in the sky between the two galaxies, and $d_{\rm A}(z_m)$ is the angular diameter distance (in $\rm kpc \: arcsec^{-1}$) calculated at the mean redshift $z_{\rm m}$ of the two sources (see (cite: Romano+2021) for more details). With this condition, the projected distance between the merging systems is larger than the typical \[CII\] size of individual galaxies, which on average is estimated to be $\sim 2.1$ kpc for ALPINE galaxies at these redshifts (cite: Fujimoto+2020; Romano+2021). Indeed, closer components could just be clumps of star formation within the same galaxy, affecting the morphology and kinematics of \[CII\] emission;

3.  a relative stellar mass ratio of $\rm 1 < \mu _{\rm K} < 4$. Here $\mu _{\rm K}$ is defined as the ratio between the UltraVista $\rm K_s$-band fluxes of the merging components[^4], which is used as a proxy for the mass ratio of galaxies (hereafter, $\mu _K \equiv \mu _\star$) since the $\rm K_s$-band flux is a good tracer of the stellar mass of galaxies up to $\rm z \sim 4$ (cite: Laigle+2016).

By applying these criteria to the 23 merging systems selected by (cite: Romano+2021), we end up with a sample of six targets. We shall note that the $\rm K_s$-band ratio is available for 9 out of 23 merging systems; for the other 14 systems, only the \[CII\] flux ratio, $\mu_{\rm [CII]}$, is available, from which (cite: Romano+2021) cannot draw conclusions about the nature of the merger (see their Section 4 for more details). Table [\[tab:OBStargets\]](#tab:OBStargets) lists the 6 observational targets selected for our study, and summarizes their merging properties ($\Delta v$, $r_{\rm p}$, $\mu_{\rm [CII]}$, $\mu_{\rm K}$; (cite: Romano+2021)) and their M$_\star$ and SFR as estimated by (cite: Faisst+2020).

![](figures/CII_mom0maps.pdf)

![](figures/exampleAll.pdf)

![](figures/spectra.pdf)

## Observational analysis

In this section, we describe processing and analysis performed on the major merging systems whose properties have been reported in Table [\[tab:OBStargets\]](#tab:OBStargets).

Firstly, we reduce the ALMA data for these targets using the Common Astronomy Software Applications (CASA; (cite: McMullin+2007)) pipeline. Each data cube is continuum-subtracted using the CASA task `uvcontsub` over the line-free visibilities in all spectral windows to obtain line-only cubes. The \[CII\] datacubes are generated from the continuum-subtracted visibilities using the task `tclean` until we reach a S/N \< 2 for the residuals. We choose a natural weighting of the visibilities to maximize the sensitivity, a common pixel size of 0.15", and a common spectral bin of $25 \, \rm km \: s^{-1}$ (beam size of $\sim 1 "$).

Secondly, we visually inspect ALMA datacubes, looking for \[CII\] emissions coming from the components of each merging system. Every time we find such an emission, we adopt a $1"$ aperture centered on the emitting galaxy to extract a preliminary \[CII\] spectrum, which is then fitted using a single 1D Gaussian model.

Finally, we consider the $2\sigma$ confidence interval of the Gaussian fit to get the min-max frequency range that we collapse to generate the moment-0 (i.e. velocity integrated) maps of each merging component (dubbed as #A, #B, etc) using the CASA `immoments` task. The moment-0 map of the entire system is then obtained by collapsing the absolute minimum and maximum of the previously obtained frequency (i.e. $min [\rm min_{freq}^A,\rm min_{freq}^B]$ and $max[\rm max_{freq}^A,\rm max_{freq}^B]$).

Figure [1](#fig:mom0_maps) shows the total velocity-integrated \[CII\] maps for our sample; white contours indicate the 2$\sigma$ region[^5] and black crosses are the centers of each emitting component (see procedure in the following), and all the S/N are consistent with those of the ALPINE survey (cite: Bethermin+2020). Having the moment-0 maps we then fit a single 2D Gaussian model to each merging component, masking it, and retrieving morphological information such as the coordinates of the \[CII\] emission peak, the full-width half maximum (FWHM) of the major and minor axis of the Gaussian and its position angle (PA). For one system, DC_873321, we had to perform a two 2D Gaussian components fit, because of the little spatial separation and similar \[CII\] luminosity ($\mu_{[ \rm CII]} \sim 1$; see Table [\[tab:OBStargets\]](#tab:OBStargets)) of the merging galaxies, which prevent us from fitting single 2D Gaussian models. Once we estimate the coordinates of the \[CII\] emission peaks of each source, we use it to center different size apertures. In particular, we employ a $1"$ aperture, a 2x2 pixel square aperture [^6] (hereafter "*peak*"), and $\rm FWHM_x \times \rm FWHM_y$ aperture (hereafter "*FWHM-based*") - with x and y being respectively the major and minor axis of the 2D Gaussian model. From these apertures, we extracted the \[CII\] fluxes in $mJy \; km / s$. In this analysis, we assume that all the \[CII\] emission coming from the apertures is associated with the merging galaxies, while that coming from the 2$\sigma$ contour is the total emission (galaxies + diffuse \[CII\] emission).

Figure [2](#fig:example) shows, in the upper panels, the total velocity-integrated \[CII\] maps for two systems highlighting the FWHM-based apertures for each merging component (dashed black lines), the center of each galaxy (black crosses) and the 2$\sigma$ regions (white contours) and, in the lower panels, the \[CII\] flux density. In particular, different line styles correspond to each merging component, while different colors (orange, green, and pink) to line spectra extracted considering $1"$, *FWHM-based* and *peak* apertures respectively. Looking at the spectra we note that the brightest emission is the one coming from the *peak* aperture (pink) i.e. the center of each galaxy, while $1"$ and *FWHM-based* apertures in some cases have comparable emissions (see for example component #A of both DC_818760 and vc_5101209780).

The merging system DC_818760 is the only triple merger in our sample. The bottom left panel of Figure [2](#fig:example) shows that the emission coming from component #C is $\sim$ 4 and 5 times dimmer than the one coming from components #A and #B respectively. The major merger is indeed happening between galaxies #A and #B, which are closely associated both spatially and in velocity, while #C is identified as an upcoming minor merger (see (cite: Jones+2020) for a detailed discussion about this system).

Finally, Figure [3](#fig:spectra) shows the \[CII\] emission arising from the total system (black) together with the sum of the emissions arising from each component of the merging system when we adopt the *FWHM-based* aperture (green). The difference between these two emissions (green hatched area) can be interpreted as due to the diffuse \[CII\] envelope around the galaxies. Already in (cite: Ginolfi+2020a) the authors analyzed in detail the merging system vc_5101209780, finding that about 50% of the total \[CII\] emission arises from a gaseous envelope distributed between the individual components of the system.

From the analysis of the observational sample used in this work, we find that a consistent fraction of the total \[CII\] emission arises from the diffuse gas *between* the galaxies, as qualitatively shown in Figure [3](#fig:spectra).

DC_873321 is the system with the least \[CII\] emission associated with the diffuse component, according to Figure [3](#fig:spectra) (top right panel), and it is also the only system where we had to perform a two components 2D Gaussian fit instead of two *single* component 2D Gaussian models (see previous discussion). Because of the difficulty in separating the emission from the galaxies and that of the surrounding medium, it is likely that part of the \[CII\] emission from the diffuse halo is associated with the individual components of the system. Note that, systems in which it is more difficult to separate the components may be in a more advanced phase of the merger (i.e. a closer interaction).

In Appendix [7](#app:vel_shift) we test the presence, if any, of a velocity shift among the diffuse and galactic components of the \[CII\] emission.

# \[CII\] emission from the CGM

In this section, we investigate the amount of \[CII\] emission arising from the diffuse halo in a more quantitative way, in order to identify possible trends between the diffuse emission and the physical properties of the merging galaxies, such as their \[CII\] luminosity ($\rm L_{[CII]}$), stellar mass (M$_\star$) and SFR. We also explore possible trends between the fraction of \[CII\] emission associated with the diffuse component, or inner CGM of the galaxies, and the relative properties of the merging systems, such as $r_{\rm p}$, $\rm \mu_{\star}$ and $\rm \mu_{[CII]}$. Indeed, these trends can give us hints about the nature of the diffuse \[CII\] envelope we observe, helping us to understand if this originates from metal-enriched gas outflows, from tidally stripped material during the gravitational interaction between the merging galaxies, and/or it pertains to small satellites lying around the merging galaxies (see discussion in (cite: Ginolfi+2020a)).

![](figures/figures_rev1/diffuse_corrected.pdf)

In order to estimate the *total* \[CII\] fluxes ­ in $\rm Jy \: km/s$ ­ we extract the emission from the 2$\sigma$ region and fit it using a single Gaussian model. We then convert the measured fluxes in \[CII\] luminosity following the relation (cite: Solomon+1992; CarilliWalter2013):

$$\begin{equation}
\label{eq:lumFreq}
{\rm L_{[CII]}} = 1.04 \times 10^{-3} \; {\rm F_{[CII]}} \; D_{L}^2(z) \; \nu _{obs}(z)
\end{equation}$$ where $\rm L_{\rm [CII]}$ is in $\rm L_\odot$, $D_{L}(z)$ is the luminosity distance (in Mpc) at the redshift of the merging system and $\nu _{obs}(z)$ is the observed frequency of the \[CII\] line (in GHz). We dub the total luminosity of the merging system $\rm L^{2\sigma}_{[CII]}$, and we estimate the error associated with this luminosity as $\rm \sqrt N \times rms$ of the moment-0 map, where $N$ is the number of ALMA beams enclosed in that region. To quantify the emission associated with the individual merging galaxies, we extract the spectra of each component using three different apertures centered on each galaxy (see Section [2.2](#sec:OBSanalysis) for a description of the adopted method). For a fixed aperture, we sum together the spectrum of each component and integrate it into the 2$\sigma$ confidence interval found before. Using Equation [\[eq:lumFreq\]](#eq:lumFreq), we obtain the luminosity from the galaxies for each of the three apertures (1", FWHM-based, peak). We use the formalism $\rm L^{i}_{\rm [CII]}$, with i = {1$"$, FWHM-based, peak}. The error associated with the flux coming from these apertures is consistent with the rms of the moment-0 map since the apertures are comparable to the ALMA beam.

Having estimated the total \[CII\] luminosity of the merging system and the luminosity coming from the galaxies, we compute the \[CII\] emission coming from the diffuse medium as: $$\begin{equation}
\rm    L^{\rm diff,i} \equiv L^{2\sigma} - L^{i}
\end{equation}$$ where we have dropped the subscript \[CII\]. We also define the fraction of \[CII\] emission coming from the inner CGM of the merging system (hereafter, $\rm f_{[CII]}$) as: $$\begin{equation}
\rm    f_{\rm [CII]}^i \equiv \frac{L^{\rm diff,i}}{L^{2\sigma}}.
    \label{eq:fcgm}
\end{equation}$$ Figure [4](#fig:diffuseCGM) shows the relation between $\rm L^{\rm diff}$ and some integrated properties of the system, such as the total \[CII\] luminosity associated with galaxies, the star formation rate, and the stellar mass of the entire merging system listed in Table [\[tab:OBStargets\]](#tab:OBStargets) (see (cite: Faisst+2020) for the discussion on photometry and SED fitting procedure). For each of these relations, we compute the Spearman coefficient, $\rho$, to see how reliable the suggested trend is: if $\rho \sim 1$ a strong correlation between the quantities is present, while for $\rho \sim -1$ there is a strong anti-correlation. Although we report the results obtained for each of the three apertures, we primarily base our conclusions on the more appropriate FWHM-based method. However, this method needs to be revised to account for possible contamination of the ALMA beam, as discussed below. In detail, we apply a correction to address the potential flux loss (associated with individual galaxies) that might be located in the tails of the ALMA beam during the 2D Gaussian fit on the velocity-integrated maps to define the FWHM-based aperture (see Figures [2](#fig:example) and [3](#fig:spectra)). This effect could enhance the \[CII\] emission linked to the diffuse envelope. To address this, we simulate artificial velocity-integrated maps of point-like sources by injecting the ALMA beams and the measured noise of the ALPINE observations, thereby matching the depth of the observed maps and replicating the same peak S/N and separations as in the observations. We then perform the same analysis on these simulated maps as we do for the FWHM-based case in the observations. Our findings indicate that the tails of the PSF indeed enhance the \[CII\] emission from the diffuse medium. Consequently, our FWHM-based results need to be corrected by a factor of 0.58 (i.e., on average, about 58% of the extended emission can be attributed to the tails of the PSF). The revised values are shown as filled green pentagons in Figures [4](#fig:diffuseCGM) and [5](#fig:CGMfraction). We note that this results in a conservative correction as it is based on the moment-0 maps of the entire emitting regions (Figure [1](#fig:mom0_maps)) which are not optimized for the extended emission.

![](figures/figures_rev1/fraction_corrected.pdf)

Figure [4](#fig:diffuseCGM) shows that there is a strong positive correlation ($\rho = 0.8$) between the \[CII\] luminosity of the diffuse medium and that of the merging components. This suggests that the objects with higher L$_{\rm [CII]}$ result in a more carbon-polluted medium (i.e. higher values of diffuse L$_{\rm [CII]}$). This is not unexpected, as more massive (luminous) galaxies are more star-forming and gas-rich, resulting in stronger outflows (cite: Ginolfi+2020a). Moreover, as most of the points in the L$^{\rm diff}$-L$^{ \rm gal}$ plane, place themselves above the 1:1 relation (black dot-dashed line) we can conclude that most of the \[CII\] emission is associated with the diffuse medium.

We also find a tentative ($\rho = 0.3$) relation between the diffuse \[CII\] luminosity and the SFR of the system, and a stronger positive correlation ($\rho = 0.5$) between $\rm L^{ diff}$ and the stellar mass of the system (see the middle and right panels of Figure [4](#fig:diffuseCGM)). These results provide some tentative indications of the origin of the metal-enriched gas powering the diffuse \[CII\] luminosity. In fact, stronger gas outflows are expected in more star-forming systems (cite: Ginolfi+2020a), while more massive galaxies trace the possible presence of small unresolved satellite galaxies and/or a stronger dynamical interaction between the merging components and are associated with more star forming (SF) galaxies resulting in a greater outflows activity. The tentative trends found so far suggest that the inner CGM is polluted with heavy elements by means of outflows, dynamical interactions, and small star-forming satellites. In particular, stripping mechanisms seem to have an important role in this scenario as we observe more extended \[CII\] envelopes in interacting systems compared to non-interacting galaxies with similar SFR - thus with comparable outflow activity (see for example \[CII\] size estimates in (cite: Fujimoto+2020)). This is also supported by the relation between f$_{\rm [CII]}$ and $\mu _\star$ (see Figure [5](#fig:CGMfraction) and its discussion) which suggests that systems with the strongest gravitational interaction, i.e. $\mu _\star$ closer to unity, have a higher fraction of \[CII\] emission coming from the diffuse envelope.

In Figure [5](#fig:CGMfraction) we further explore the dependence of the fraction of \[CII\] emission coming from the inner CGM of the merging systems, $\rm f_{[CII]}$, and the properties of the merging pairs, such as $r_{\rm p}$ between the galaxies, $\mu _\star$, and $\mu _{\rm [CII]}$. In each panel, the green solid line and shaded areas are respectively the linear fit and the associated error when considering the ALMA PSF tails contribution to the diffuse emission. In Figure [5](#fig:CGMfraction) we do not include the peak aperture as we obtain $\rm f_{[CII]} \sim 0.95$ in all the systems given that, in this case (i.e. unresolved merging galaxies), most of the \[CII\] emission is associated with the inner CGM.

From this figure, we note that the fraction of \[CII\] emission coming from the inner CGM of the merging systems is in the range $\rm f_{[CII]} \simeq 0.14 - 0.30$ ($\sim 25 \%$, on average) when accounting for the possible effect of the PSF broadening as discussed in Section [3](#sec:diffEmission). The black horizontal line corresponds to $\rm f_{[CII]} = 0.50$.

The left panel of Figure [5](#fig:CGMfraction) indicates that there is a strong positive correlation ($\rho = 0.9$) between $\rm f_{[CII]}$ and $r_{\rm p}$, meaning that merging systems with larger projected separations appear to have a larger $\rm f_{[CII]}$ compared to systems with smaller $r_{\rm p}$, where a clear separation between the emission coming from the diffuse component and that coming from the galaxies is more challenging. However, it could also be that galaxies that are interacting for a longer period of time result in a more carbon-rich envelope (see Appendix [9](#app:B)). To investigate this possibility we need to have information on the time evolution of the system, which is beyond the scope of the present work.

We also find an anti-correlation ($\rho = -0.8$) between the fraction of \[CII\] emission coming from the inner CGM and the mass ratio of the galaxies: the larger $\mu_\star$ the smaller $\rm f_{[CII]}$. This may suggest that the dynamical interaction between mergers where galaxies have similar masses ($\mu_\star \sim 1$) results in stronger tidal stripping and, as a consequence, in a more polluted CGM. Finally, we analyzed the relation between $\rm f_{[CII]}$ and $\mu _{[\rm CII]}$ (right panel), finding a mild correlation, $\rho = 0.5$, which suggests that the fraction of \[CII\] emission from the diffuse envelope does not depend on the ratio between the $\rm L_{[CII]}$ associated with the galaxies.

The system highlighted in gray in Figures [4](#fig:diffuseCGM) and [5](#fig:CGMfraction), is DC_873321. It is the only one for which we had to perform a two 2D Gaussian components fit instead of two *single* 2D Gaussian models (see Section [2.2](#sec:OBSanalysis)), because of the difficulty in separating the emission from the galaxies and that of the diffuse envelope.

To summarize, our observational analysis shows that a consistent part ($\sim 25 \%$, at least) of the \[CII\] emission of major merging galaxies identified in the ALPINE survey originates from a diffuse gas envelope around the merging galaxies or inner CGM. Also, we find tentative trends between the emission arising from the diffuse envelope and the physical properties of the merging systems, which provide some indication of the possible mechanisms that are responsible for the presence of a diffuse metal-enriched cold gas component surrounding these galaxies, such as small satellite companions, gravitational interaction resulting in tidal stripping and outflows activity.

In the next section, we compare the above findings and observational sample with synthetic merging systems at similar redshift selected from a cosmological hydrodynamical simulation, to gain a more in-depth understanding of the physical processes shaping the origin and metal enrichment of their inner CGM.

# Comparison with simulations

Intrigued by the results obtained from ALMA observations, which suggest that a fraction of the \[CII\] emission originates from the gas between merging galaxies and that different mechanisms (i.e. outflows, star-forming satellites, and tidal interactions) can be responsible for such emission, we employ cosmological simulations to gain more insights into the nature of \[CII\] emission. In what follows, we first provide a brief presentation of the simulations that will be used for our analysis. These have been thoroughly presented in (cite: DiCesare+2023) and have been run using the hydrodynamical code `dustyGadget` (cite: Graziani+2020). We then illustrate our analysis of the simulation results aimed at interpreting the nature of the observed \[CII\] envelopes. To this aim, we identify simulated galaxies with properties similar to the observed systems, and we use the carbon mass in their cold ISM medium (T $\lesssim 10^4$ K) as a proxy for their \[CII\] emission. Our goal is to investigate whether the simulated galaxies follow the relations presented in Section [3](#sec:diffEmission). We remark here that our qualitative analysis[^7] is meant to provide *indications* on the physical processes that may be responsible for the extended emission in merging systems, supporting the interpretation of ALMA observations.

## `dustyGadget`

In this section, we provide a synthetic summary of the key features of the cosmological hydrodynamical code `dustyGadget`, and we refer the interested reader to (cite: Graziani+2020) for a detailed description of the code, and to (cite: DiCesare+2023; Venditti+2023b; Venditti+2023) for its latest results.

`dustyGadget` is an extension of the particle-based Smoothed Particle Hydrodynamics (SPH) code `Gadget-2/3` (cite: Springel2005; Springel+2021) which provides a self-consistent implementation of dust production and evolution, on top of the improvements to the chemical evolution module by (cite: Tornatore+2007a; Tornatore+2007b), and to molecular chemistry and cooling by (cite: Maio+2007). In particular, the gas chemical evolution scheme is inherited from (cite: Tornatore+2007a) (see also (cite: Maio+2010)): it follows the metal release from stars of different masses, metallicity, and lifetimes. Yields depending on mass and metallicity are implemented for both PopII and PopI stars and stars with masses $\ge 40 \: \rm{M_{\odot}}$ are assumed to collapse into black holes and do not contribute to metal enrichment. PopIII stars with masses inside the range $140 \: \rm{M_{\odot}} \le \rm M_{\star} \le 260 \: \rm{ M_{\odot}}$ are expected to explode as pair-instability SNe (PISN), while those with masses outside the PISN range are assumed to collapse into black holes. We warn the reader that the formation of AGN is not modeled in our simulations, thus we do not account for mechanical or radiative feedback from accreting nuclear black holes. Moreover, as already stated, \[CII\] emission is not followed in the simulation, hence we use the carbon mass in the cold gas phase as a proxy for the emission (see discussion in Section [4.4](#sec:2systems)). Following (cite: Maio+2007), the chemical network in `dustyGadget` also includes the evolution of both H and H$^+$, He, D, and primordial molecules by relying on the standard `Gadget` implementation of the cosmic UV background as a photo-heating mechanism, first introduced by (cite: Madau1996). Star formation occurs in the cold gas phase, once the gas density exceeds a value of $n_{\rm th} = 132 \, h^{-2} \rm cm^{-3}$ (physical). The IMF of the stellar populations, each represented by stellar particles, is assigned according to their metallicity $\rm{Z_\star}$, given a gas critical metallicity $\rm{Z_{\rm crit}} = 10^{-4} \: \rm{Z_\odot}$, where $\rm{Z_\odot} = 0.02$ (cite: Grevesse&Anders1989). When $\rm{Z_\star < Z_{\rm crit}}$ we adopt a Salpeter IMF (cite: Salpeter+1955) in the mass range $[100 - 500]\: \rm{M_\odot}$; otherwise, the stars are assumed to form according to a Salpeter IMF in the mass range $[0.1 - 100] \: \rm{M_\odot}$.

The production of dust grains by stars in SNe explosion and Asymptotic Giant Branch (AGB) stellar winds is described by means of a set of mass- and metallicity-dependent yields (cite: BianchiSchneider2007; Marassi+2014; Marassi+2015; Bocchio+2016; Ginolfi+2018; Graziani+2020; Pizzati+2020; Romano+2023), which closely follow the chemical network adopted for metal yields (cite: Tornatore+2007a). Once the grains produced by stars are released in the ISM, they can undergo diverse physical processes that can alter their mass, relative abundances, chemical properties, charge, and temperature. Generally, it is assumed that the dust-to-light interactions (e.g. photo-heating, grain charging) change the thermodynamic and electrical properties of the grains (see for example (cite: Glatzle+2019; Glatzle+2022)), but these processes have a negligible impact on the total dust mass ($\rm M_{dust}$) unless the grain temperatures reach the sublimation threshold ($\rm{T_{\rm d,s}} \gtrsim 10^{3}$ K). Other physical processes (i.e. sputtering and grain growth) can alter the total dust mass and the grain size distribution (cite: Draine+2011; Aoyama+2020). In the version of `dustyGadget` that we adopt in this work, we only consider physical processes which alter the dust mass (i.e. grain growth, destruction by interstellar shocks, and sublimation)[^8] in the hot and cold phases of the ISM (cite: SpringelHernquist2003). The spreading of dust grains and atomic metals in the ISM, CGM, and IGM is done through galactic winds, which are modeled with a fixed initial velocity following the implementation of (cite: Tornatore+2010) - see (cite: Maio+2011) for the interplay between chemical and mechanical feedback in simulations. In `dustyGadget`, the initial velocity is fixed to 500 km/s, following typical outflow velocities observed in main sequence galaxies at $z\gtrsim4$ (cite: Gallerani+2018; Sugahara+2019; Ginolfi+2020b). Finally, the identification of DM halos and their substructures is performed in post-processing with the AMIGA halo finder (AHF, (cite: Knollmann+2009)).

In this work we make use of *one* of the eight statistically independent cosmological simulations (U6-U13) which have been analyzed in (cite: DiCesare+2023), where we have investigated the redshift evolution of the SFR, stellar mass density, stellar mass function, and galaxy scaling relations, at $z \geq 4$, comparing our results with observational data.

The physical setup of the runs and simulated cosmic volumes are the same as in (cite: DiCesare+2023); in particular, we consider a cubic volume with $50\; h^{-1}$ cMpc ($\sim$ 74 cMpc) side length, with $2 \times 672^3$ particles, corresponding to a mass resolution of $5.2 \times 10^7 \, \rm M_\odot$ for DM particles, and of $8.2 \times 10^6 \, \rm M_\odot$ for gas particles. Using the current version of `dustyGadget` we can resolve down to the scale of a giant molecular cloud (a few tens up to hundreds pc), but for the purpose of this work, we are only interested in scales of the order of tens kpc.

Finally, the simulations adopt a flat $\Lambda$CDM cosmology with $\Omega _{\Lambda} = 0.6911$, $\Omega_{\rm m} = 0.3089$, $\Omega _{\rm b} = 0.0486$ and $h=0.6774$ (cite: PLANK+2016). The simulations start at $z=100$ assuming neutral pristine gas and evolve all particle components down to $z = 4$. In the following, whenever we refer to units we mean *physical* one, unless otherwise stated.

## Identifying galaxy mergers

![](figures/MTree_sketch.png)

+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+
| system ID | $z$    | $r_m$ \[kpc\] | $\mu _C$ | $\mu _\star$ | Log($\rm M_\star/M_\odot$) | Log($\rm SFR/ M_\odot yr^{-1}$) |
+:=========:+:======:+:=============:+:========:+:============:+:==========================:+:===============================:+
| merging galaxies                                                                                                            |
+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+
| H2        | 4.495  | 11.3          | 2.0      | 4.1          | 10.44                      | 1.84                            |
+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+
| H4        | 4.495  | 16.3          | 2.3      | 1.5          | 10.55                      | 1.96                            |
+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+
| H5        | 4.495  | 6.3           | 1.3      | 1.9          | 10.49                      | 1.83                            |
+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+
| H6        | 4.495  | 5.3           | 1.3      | 1.9          | 10.43                      | 1.81                            |
+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+
| H10       | 4.495  | 10.3          | 3.2      | 1.3          | 10.51                      | 1.90                            |
+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+
| H25       | 4.495  | 40.3          | 2.8      | 2.3          | 10.30                      | 1.70                            |
+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+
| H28       | 4.495  | 32.3          | 3.6      | 4.1          | 10.27                      | 1.74                            |
+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+
| H0        | 4.988  | 13.3          | 4.6      | 1.5          | 10.58                      | 2.17                            |
+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+
| non-interacting galaxies                                                                                                    |
+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+
| H7        | 4.495  | \-            | \-       | \-           | 10.43                      | 1.84                            |
+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+
| H29       | 4.495  | \-            | \-       | \-           | 10.58                      | 1.85                            |
+-----------+--------+---------------+----------+--------------+----------------------------+---------------------------------+

(cite: DiCesare+2023) already compared the integrated properties (SFR, $\rm M_\star$, $\rm M_{dust}$) of synthetic galaxies from `dustyGadget` with those observed in the ALPINE survey, finding a remarkable agreement between the two (see for example their Figure 3 and Figure 8).

In this work, we start from the galaxy catalogs generated by the simulation and select synthetic merging galaxies whose physical, integrated properties resemble the observed ones, as described in Section [2.1](#targets). We analyze the simulation snapshots (hereafter referred as snap) from snap = 041 ($z = 4.495$) to snap = 035 ($z = 5.098$), which encompass the redshift range of the observed systems ($z = 4.5 - 5.1$, see Table [\[tab:OBStargets\]](#tab:OBStargets)), and a physical time interval of $\Delta \rm t_{H} = (1.338 - 1.145)$ Gyr = 193 Myr, for our assumed cosmology. Hence, we end up having six galaxy catalogs, with $\Delta z$ = 0.1, containing simulated systems with masses in the range M$_\star \sim 10^8 - 10^{11} \, \rm M_\odot$ ($\sim$ 14000 objects at snap = 041, and $\sim 9400$ at snap = 035). Among these, we consider only galaxies with stellar mass M$_\star \geq 10^{10} \, \rm M_\odot$, to match the properties of the observed systems (see Table [\[tab:OBStargets\]](#tab:OBStargets)), ending up with $\sim$ 40 galaxies at snap = 041 and $\sim$ 15 galaxies at snap = 035. Within these smaller samples of objects, which match the observed systems in terms of redshift and stellar mass, we must identify possible galaxy mergers.

Mergers are identified considering galaxies at $z \simeq 4.5$ and reconstructing their merger trees (i.e. their past assembly histories in gas, dark matter, and stellar particles) up to $z \simeq 5.1$. Figure [6](#fig:MTree_sketch) shows a schematic view of a merger tree reconstruction: we start at $z$ = 4.495 (snap = 041) with a galaxy dubbed "a", and go backward in time up to $z$ = 5.1 (snap = 035); at each intermediate redshift step, we identify the ancestors of "a" (i.e. halos "b" and "c" contributing particles to "a" at $z$ = 4.6). Once we have reconstructed the merger tree of each galaxy, we can then follow its evolution forward in time and characterize the origin of its mass assembly, whether this is the result of a major merger, smooth accretion, or minor mergers.

In particular, we follow the same criterion adopted for the observed systems, and we assume that two ancestors undergo a major merger when their relative stellar mass ratio (defined as the ratio between the most massive and the least massive) is $1 < \mu_\star < 4$.

After applying this condition and checking that we are not double counting merging episodes[^9], we end up with 8 unique candidates (7 at $z \simeq 4.5$ and one at $z \simeq 5.0$), which undergo major mergers during their history. In Table [\[tab:simGal\]](#tab:simGal), we provide a summary of their physical properties, where each row corresponds to one of these synthetic major mergers. In particular, we report their IDs, redshift, the mean projected (r$_{ m}$)[^10] distance in kpc, the relative carbon mass ratio of the merging pair ($\mu _C$), the relative stellar mass ratio of the merging pair, $\mu _\star$, the total M$_\star$ in M$_\odot$ and the SFR in M$_\odot$ yr$^{-1}$.

Compared to the observed sample (see Table [\[tab:OBStargets\]](#tab:OBStargets)), the simulated systems appear to span a similar range of properties and can be considered as good synthetic analogs of the systems that we have analyzed in Section [2](#sec:observations). This sample of synthetic galaxies can help us interpret the observed trends that we presented in Section [3](#sec:diffEmission). As an illustrative example, in the next section, we discuss the time evolution of the simulated system H4 at $z = 4.495$, which provides the best synthetic analog of vc_5100822662.

![](figures/MTree_example.pdf)

## Time evolution of a representative merger

The simulated system H4 at $z = 4.495$ and the observed system vc_5100822662 (hereafter, vc_662) at $z = 4.5210$ have stellar mass and SFR which are consistent within the errors: Log($\rm M_\star/M_\odot$) = 10.6 (H4) and Log($\rm M_\star/M_\odot$) = 10.4$^{+0.1}_{-0.1}$ (vc_662); Log($\rm SFR / M_\odot \; yr^{-1}$) = 2.0 and Log($\rm SFR / M_\odot \; yr^{-1}$) = 2.0$^{+0.2}_{-0.2}$, respectively. Moreover, H4 and vc_662 have similar stellar mass ratios $\mu _{\rm H4}$=1.5 and $\mu _{\rm vc\_662}$=1.7, and projected distance of 16 kpc and 11 kpc respectively. It is important to keep in mind that from the simulation, we not only have information on projected distances but also on the physical (3D) distance between the merging galaxies, which we compute to be $r$ = 21 kpc for this synthetic system.

Figure [7](#fig:MTree_example) shows the merger tree reconstruction for H4 (see Table [\[tab:simGal\]](#tab:simGal) for its integrated physical properties) from $z = 4.5$ to $z = 5.1$, together with maps (80 $\times$ 80) kpc and (60 $\times$ 60) kpc showing respectively the (x,y) projection of the dark matter particles and stellar particles. These maps are centered respectively in the center of mass of the dark matter halo and of the baryonic component. Here we dubbed the merging galaxies H4 and H98 at $z = 4.5$ as "a" and "b", respectively, so that it is easier to follow their past history along the merger tree reconstruction. In the illustration provided, we connect with solid black lines each component of the merging pair to its main galaxy progenitor at the preceding redshift[^11]: as an example, the galaxy dubbed as "a" at $z = 4.6$ (H3) is considered as the main progenitor of galaxy "a" at $z = 4.5$ (H4). At each redshift, we also indicate the $\mu _\star$ of the galaxies undergoing the major merger. For the sake of clarity, the projections of the dark matter and baryonic components in the middle and right panels of Figure [7](#fig:MTree_example) are shown only at four redshifts, and particles belonging to each merging component are color-coded to match those in the corresponding merger tree. In the following section, we discuss how the spatial distribution of the gaseous component is generated.

Looking at the dark matter and baryonic matter visualizations in the middle and right panels of Figure [7](#fig:MTree_example), it is interesting to note how dark matter halos merge and coalesce in a shorter time compared to galaxies themselves (i.e. to the baryonic components). Indeed, by $z = 4.5$, the dark matter halos of the two systems can be considered as a single virialized object, while the baryonic components are still largely spatially segregated, and undergoing the merger. Moreover, as soon as the gravitational interaction between galaxies becomes stronger (i.e. they move closer), galaxies appear to be more clumpy and rich in satellites and undergo disruption events which lead to filamentary structures by $z = 4.5$. In addition to this, we also have to consider that the merger between the dark matter halos of the galaxies may lead to the formation of overdense regions which result in dense clouds where star formation can be triggered.

All this qualitative information coming from the simulation provides us with fundamental indications on the evolution of merging pairs, inaccessible using only observations, and helps us interpret the results from the observational part of this work. In fact, simulated galaxies have higher spatial resolution compared to ALPINE observations, and we are able to resolve small satellite galaxies and filamentary structures. This allows us to infer the origin of the enriched diffuse gas surrounding the galaxies, which powers the observed \[CII\] emission coming from the inner CGM of merging galaxies: whether this is due to unresolved satellites galaxies, filamentary structures, outflows or maybe a combination of the three. In the following, we will explore these options in a more quantitative way.

## Dependence of galaxy properties and their CGM on the mass ratio of merging pairs

![](figures/figures_rev2/starsCsmooth.pdf)

In this section, we focus on two synthetic candidates (H2 and H10) at $z = 4.5$ which have been selected as their merging pairs are characterized respectively by the highest ($\mu _\star = 4.1$) and lowest ($\mu _\star = 1.3$) stellar mass ratios in our sample. Our aim is to investigate whether systems with extreme $\mu _\star$ may be characterized by different morphological properties of the stellar and gas components, on scales comparable to the diffuse \[CII\] emission component quantified in Section [3](#sec:diffEmission).

Figure [8](#fig:stars+C) shows the stellar particle distributions (first row) and carbon surface density maps ($\Sigma _{\rm C}$, second and third rows) for H2 and H10 projected on the plane perpendicular to the line-of-sight along the $x$-axis. Specifically, in orange/violet tones is the carbon in regions with gas temperature T $< 5 \times 10^4$ K, used as a proxy for L$_{\rm [CII]}$ - see following discussion.

In general, to characterize the gas and metals spatial distributions we project gas and metal particles onto Cartesian grids with 256 or 512 cells/side, and each particle contribution is weighted with the SPH kernel adopted in `dustyGadget`. These maps are centered either in the halo mass center (H2, H4, H5, H6, H10, H0) or in the center of mass of the merging system (H25, H28), depending on how diverse these two values are, while the side of the Cartesian grid is chosen to capture the whole merging system. Specifically, we chose a box side of 60 kpc (256 cells/side) for all the synthetic candidates but for H25 and H28 for which we adopted a side length of 100 kpc (512 cells/side). Both grids have a spatial resolution (pixel dimension) of $\sim$0.2 kpc, thus a factor of $\sim$ 20-30 more resolved than the ALPINE-ALMA beam.

As for the panels showing stellar particles (scatter plots), color-coded in red are their ages, while, we highlight in dark blue stellar populations with ages $\leq$ 10 Myr and in light blue those with ages $\leq$ 100 Myr. This is done in order to characterize younger populations and star-forming regions (blue) in contrast to more mature stellar populations in red. Observations interpreted with photo-ionization models suggest that the bulk of \[CII\] emission is coming from neutral atomic gas clouds in photo-dissociation regions (PDRs) surrounding young stars (cite: Hollenbach+1999), thus we expect that a consistent part of the carbon mass predicted by `dustyGadget` simulations will be associated with young stellar populations (ages $\leq$ 10 Myr) - see discussion in Section [5](#sec:discussion).

In the second row of Figure [8](#fig:stars+C), we color in blue/green tones the *total* carbon surface density, while in orange/violet the carbon surface density found in regions with gas temperature T $< 5 \times 10^4$ K [^12]. This cut has been done as the \[CII\] emission is expected to be associated with cold-warm gas phases, and at higher temperatures we expect the C atoms to be in higher ionization states.

The third row of Figure [8](#fig:stars+C) shows the surface density distribution of the carbon associated with gas at a temperature below the adopted cut (hereafter "cold" gas phase) once it is convolved with the ALMA PSF (i.e. we applied a Gaussian smoothing with FWHM $\sim 1"$). This step is needed since we want to compare the results from simulations with those from observations (see Section [4.5](#sec:statProperties)). The black crosses mark the center of the two interacting galaxies and the gray circle in the bottom left corner shows a reference beam of $\sim 1 "$.

The comparison among two merging systems in Figure [8](#fig:stars+C) highlights the different environments these systems belong to. In fact, H2 is characterized by a dominant component and several smaller satellites ($\mu _\star \sim 4$), while H10 is characterized by an almost equal mass merging pair ($\mu _\star \sim 1$). This translates into different stellar and metal-enriched gas spatial distributions in the two cases.

Also, it is interesting to note how diverse scenarios appear when comparing carbon maps with and without the convolution with ALMA PSF, with the latter lacking the detailed spatial distribution inferred from the simulation.

![](figures/diffuse_sim.pdf)

![](figures/fraction_sim.pdf)

## Statistical properties

Here we analyze the relations between the carbon mass - in the cold phase - present in the diffuse envelope around merging galaxies and the integrated properties of such systems, to identify possible trends. The aim is to derive scaling relations that can be compared to the observational ones (see Figure [4](#fig:diffuseCGM) and Figure [5](#fig:CGMfraction)) using the carbon in the cold gas phase as a proxy for \[CII\] luminosity. In fact, once similar relations are recovered, predictions from `dustyGadget` can help us interpret the observations and help us gain insights into the nature of the extended emission.

From now on, whenever we talk about the carbon mass we refer to the M$_C$ in the cold phase, T $< 5 \times 10^4$ K, orange/violet tones in Figure [8](#fig:stars+C). As previously stated, this cut in temperature is necessary in order to highlight the regions from which we expect \[CII\] emission to be more likely. Briefly, we generate the gas and carbon 3D distributions, apply the cut in temperature to these cubes, and then project this result on planes perpendicular to the lines of sight parallel to the $z$, $y$, and $x$-axis. We repeat this procedure to all our selected synthetic galaxies (see Table [\[tab:simGal\]](#tab:simGal)) and, once we have an image for each candidate and its three plane projections, we convolve the image with the ALMA PSF and fit a 2D Gaussian model to it, retrieving morphological information such as the coordinate of the main M$_C$ clumps that are associated with the major merging galaxies. Then, we use the mean value of all the FWHM-based apertures adopted for the observational part as the standard aperture to be used in simulations (black dashed circles in Figure [8](#fig:stars+C), last row) and associate all the carbon inside the aperture as belonging to the galaxy.

Knowing the coordinates of the center and the dimensions of all the apertures, for each 2D projection (lines of sight, $i = z,y,x$), we can distinguish between the carbon mass associated with the galaxies - sum of the carbon mass inside the apertures - and the total one - sum over the entire plane projection. At this point, we can define the M$_C$ associated with the diffuse halo as :

$$\begin{equation}
\rm    M^{\rm diff, i} \equiv M^{\rm total} - M^i
\end{equation}$$

where we dropped the subscript C. The fraction of M$_{C}$ in the envelope around merging systems (hereafter, $\rm f_{C}$) is:

$$\begin{equation}
   \rm f_{C}^i \equiv \frac{M^{\rm diff, i}}{ M^{\rm total}}.
\end{equation}$$

Figure [9](#fig:diffuse_sim) shows the relation between M$^{\rm diff}$ and some integrated properties of the systems, such as the total carbon mass, SFR, and stellar mass. For each relation, we calculate the Spearman coefficient to understand how reliable the suggested trend is. Moreover, different colors correspond to projected quantities along lines of sight parallel to the $z$ (blue), $y$ (pink), and $x$ (red) axis, and projections associated with the same system are connected by gray vertical lines quantifying the variation of M$^{\rm diff}$.

The black dashed line is the result of the linear fit once we consider the carbon mass value in the diffuse halo averaged on the three projections (hereafter, $\rm M^{avg}$ shown as white dots in the figures) and the corresponding x-axis quantity. Finally, highlighted in gray are H2 which has a peculiar morphological structure rich in clumps and satellites (see left panels of Figure [8](#fig:stars+C)), and H6 whose galaxies are closely interacting (see Appendix [8](#app:A)). For these reasons, they are considered as not belonging to the fiducial simulated sample and have not been included in the fit.

The figure shows a positive $\rho =$ 0.4 and strong positive $\rho =$ 0.8, 0.9 correlations respectively in the first, second, and third panels. These results suggest that their inner CGM is characterized by a significant carbon mass, which appears to be well correlated with the SFR and stellar mass of the systems, indicating the important role that current and past star formation activity has in enriching the inner CGM with outflows from the merging pairs and smaller satellite systems. This conclusion strengthens the tentative trends between diffuse \[CII\] emission and star formation rate/stellar mass of merging systems ($\rho$ = 0.3 and 0.5, respectively) we found in Section [3](#sec:diffEmission).

In Figure [10](#fig:fraction_sim) we explore the dependence between the fraction of carbon mass in the diffuse halo ($\rm f_C$) and r$_m$, $\mu _\star$ and $\mu _C$. In the middle and right panels, different colors correspond to different projections, with those associated with the same system connected by gray vertical lines. In each panel we specify the Spearman coefficient of the corresponding relation and the black dashed line is the linear fit once we consider the fraction of carbon in the diffuse envelope averaged on the three projections ($\rm f^{avg}$) and the corresponding x-axis quantity. $\rm f^{avg}$ is shown with a violet square/star in the left panel and with white dots in the middle and right panels. The synthetic galaxy H2 has not been included in these plots being considered an outlier with $\rm f_C \sim 0.8$, then out of scale; H6, instead, has been highlighted in gray and not considered in the fits and computation of the Spearman coefficients.

On average, we find that, when considering the entire simulated sample, $\sim 59$% of carbon mass resides in the envelope around merging systems. By excluding H2 which has been considered as an outlier being particularly rich in star-forming satellites (see left panels of Figure [8](#fig:stars+C)) this value becomes $\sim57$%. Both cases are indicative of the presence of carbon in the cold gas phase in the inner CGM of the merging systems, according to `dustyGadget`.

In the left panel of Figure [10](#fig:fraction_sim) we show $\rm f^{avg}$ as a function of the mean projected distance (violet square) and physical distance (violet stars) between merging galaxies, with the physical distance being larger than the projected one in all the systems. The Spearman coefficient for the $\rm f^{avg}$ - r$_m$ relation is $\rho = -0.5$ suggesting a correlation with negative trend between these two quantities. This result, which points out a negative trend among $\rm f^{avg}$ - r$_m$, seems to disagree with what has been found in observations - see Figure [5](#fig:CGMfraction). However, in simulations we are considering systems with mean distances r$_m$ up to $\sim 50$ kpc while, in the ALPINE sample, the projected distance goes up to $\sim 16$ kpc. This is further discussed in Appendix [9](#app:B), where we show that a positive correlation among $\rm f^{avg}$ - r$_m$, similar to that found in observations, is recovered when we consider galaxies with $r_m \lesssim 16$ kpc, highlighting the role of interactions in polluting the diffuse medium.

The middle panel suggests an anti-correlation between the fraction of carbon mass in the diffuse halo and the stellar mass ratio of the merging galaxies, indicating that systems with $\mu _\star$ closer to unity have stronger interactions which result in more metal-enriched inner CGM. This may be a clue that dynamical interaction at high-$z$ can be an efficient mechanism for extracting material out of galaxies and mixing it in the CGM. Finally, the right panel shows $\rm f_C$ as a function of $\mu _C$, suggesting that there is not a correlation between the amount of $\rm M_C$ found in the diffuse halo and the ratio between carbon masses of each merging component.

![](figures/starFraction_sim.pdf)

# Discussion

In this section, we interpret the observations using our simulated galaxies and discuss the results obtained from the analyzed merging systems at $z \sim$ 4-6. First and foremost, it is important to bear in mind that the comparison between the results from observations and those from simulations is not straightforward. In fact, in simulations we consider the *carbon mass* in the cold gas phase which is more likely to emit in \[CII\], but not the actual \[CII\] luminosity. In fact, to recover luminosity information from simulations we would need to couple our result with radiative transfer codes, such as `Cloudy` (for line transfer, (cite: Ferland2017)) and `SKIRT` (for dust continuum, (cite: Baes+2015)). These features will be implemented as a follow-up work. Thus, preliminarily, we assume that the carbon mass in the cold gas phase (T \< $5 \times 10^4$ K) can be considered as a good proxy for \[CII\] luminosity, to guide the interpretation of the observational results illustrated in Section [3](#sec:diffEmission).

On one hand, \[CII\] envelopes have been observed at first in non-interacting galaxies (e.g. (cite: Fujimoto+2019; Ginolfi+2020b; Fujimoto+2020; Herrera-Camus+2021)), where they extend up to $\sim$ 10-15 kpc outside the galaxies. A possible explanation has been provided by (cite: Pizzati+2020; Pizzati+2023), who adopt a semi-analytical model to interpret the presence of \[CII\] halos in high-$z$ galaxies concluding that they can be produced by ongoing (or past) starburst-driven outflows which transport carbon and other heavy elements in the CGM. Recently, (cite: Romano+2023; Romano+2024) analyzed *Herschel* (cite: Pilbratt+2010) data of local dwarf galaxies finding that the observed \[CII\] emission - which size agrees with that measured for star-forming galaxies at $z > 4$ - can be attributed to the presence of galactic outflows. On the other hand, (cite: Ginolfi+2020a) found an even more extended (\> 20 kpc) emission in one interacting system from the ALPINE sample, arguing that most of the detected circumgalactic emission is a consequence of the effect of gas stripping induced by strong gravitational interaction.

In this work, by analyzing major merging systems in the ALPINE survey, we confirm the presence of extended \[CII\] envelopes around interacting galaxies, finding that around 25% of the total \[CII\] emission comes from the medium between the galaxies. All the analyzed systems have an extended emission (mean value of $\sim$ 27 kpc) suggesting that the gravitational interaction between galaxies, which results in tidal tails, is responsible for their extended carbon-enriched envelope. This scenario has been investigated using the hydrodynamical simulation `dustyGadget` and comparing merging and not merging systems (see discussion in the following). Specifically, the anti-correlation between f$_C$ and $\mu _\star$ shown in Figure [10](#fig:fraction_sim) indicate that systems that interact more strongly result in a more enriched halo (i.e. higher f$_C$) - supporting the conclusion from (cite: Ginolfi+2020a). Starburst-driven outflows, which spread metals outside the galaxies, are still at work in interacting systems. In fact, as shown in the middle panel of Figure [9](#fig:diffuse_sim), there is a correlation between the carbon in the diffuse medium and the SFR of galaxies which can be associated with outflows. To quantify the importance of that mechanism compared to the others we need to look at galactic winds of interacting galaxies, which is something outside the aims of this paper.

Predictions from `dustyGadget` not only helped us corroborate and interpret the observational results, but we also used them to disentangle the different mechanisms that contribute to metal enrichment of the inner CGM of interacting galaxies. To do so, we consider SFR, $\rm M_\star$, and $\mu _\star$ as proxies for outflows, SF clumps, and tidal interactions, respectively, and study their contribution to the carbon-enriched envelope.

As already mentioned, H2 is considered an outlier in the synthetic sample, because of its high f$_C$ which is due to its peculiar morphology rich in satellites/star-forming clumps. To further investigate this hypothesis (i.e. that star-forming clumps play a role in the observed \[CII\] diffuse emission), we study the relation among f$_C$ and the fraction of young, age $\leq$ 10 Myr, stellar populations (f$_\star$) that reside in the inner CGM of the systems. This quantity is defined as : $$\begin{equation}
   \rm f_\star^i \equiv \frac{N_\star^{\rm total} - N_\star^i}{ N_\star^{\rm total}}.
\end{equation}$$ with $\rm N_\star^{\rm total}$ being the total number of young stellar populations and $\rm N_\star^i$ the sum of stellar particles associated with merging galaxies for each projection ($i = z,y,x$).

In Figure [11](#fig:starF) we show mean values for f$_\star$ and f$_C$ for interacting, in orange, and non-interacting, in green, systems; error bars on both axes give us an idea of the variations of f$_\star$ and f$_C$ among different projections. This figure shows a linear relation and positive trend between the fraction of carbon and that of young stellar populations in the diffuse halo, suggesting that clumps of star-forming regions, unresolved by ALMA, can play a role in enriching the gas envelope with carbon. Moreover, as shown in Figure [7](#fig:MTree_example), the merger between dark matter halos happens on smaller timescales compared to those needed for the merger in the baryonic component and may lead to the formation of overdense regions at the periphery of merging systems triggering star formation and enriching their surrounding medium with carbon and other heavy elements.

In addition to the previous analysis, by comparing results from major merging systems (dubbed as "interacting") with those from systems which are not in major mergers (dubbed as "non-interacting/single"[^13]) we can have an estimate of the importance of gravitational interactions, which result in tidal stripping, for the enrichment of the inner CGM. To do so, we select two non-interacting galaxies with stellar masses and SFRs similar to the interacting synthetic candidates - see Table [\[tab:simGal\]](#tab:simGal). These two galaxies are also representative of other synthetic single galaxies at the same redshift that we find in our simulation.

In the single-galaxy case, we recover an extended carbon-rich envelope going up to $\sim$ 10 kpc, in agreement with what has been estimated by (cite: Fujimoto+2019; Fujimoto+2020; Ginolfi+2020b; Herrera-Camus+2021). This is shown in Figure [12](#fig:singleInter), and confirms that the diffuse halo in non-interacting galaxies is less extended than the one estimated for interacting systems (\> 20 kpc).

In Figure [9](#fig:diffuse_sim) we compare M$^{\rm diff}$ in interacting (colored pentagons) and non-interacting (green triangles) galaxies. In general, we note that single galaxies have lower M$^{\rm diff}$ values than interacting systems, and also that they result in similar diffuse carbon masses no matter the adopted line-of-sight, indicating a more compact and regular morphology i.e. not disturbed by dynamical interactions. The first panel of Figure [9](#fig:diffuse_sim) suggests that both interacting and non-interacting systems follow a similar trend when comparing M$^{\rm diff}$ and the total carbon mass. On the one hand, the relation between the diffuse carbon mass and the SFR (second panel) shows that for non-interacting systems, the ongoing SFR is not a good proxy for the amount of carbon mass in the inner CGM. We also note that H6, which is an interacting system in an advanced phase of the merger, places itself close to non-interacting systems on the M$^{\rm diff}$-SFR relation. On the other hand, looking at the third panel which shows M$^{\rm diff}$ as a function of M$_\star$, we see that interacting systems have $\sim1.4\times$ more carbon mass in the diffuse halo than single galaxies. This result suggests that stripping mechanisms seem to be responsible for bringing metals into the CGM of the analyzed systems. This conclusion is further corroborated by the fact that the fraction of SF clumps and carbon mass present in the diffuse halo of non-interacting galaxies is comparable to that of interacting galaxies, as shown in Figure [11](#fig:starF).

![](figures/singleInter.png)

In summary, it seems that for the interacting systems analyzed in this work, stripping mechanisms are responsible not only for bringing carbon into larger scales but also for enhancing \[CII\] emission possibly via shocks (see also (cite: Ginolfi+2020a)).

The interacting systems that we have analyzed could be considered as high-$z$ analogs of circumgalactic stripped carbon and shock-induced \[CII\] emission in local studies (cite: Appleton+2013; VelusamyLanger2014). These are qualitative conclusions, based on a comparison between the properties of the inner CGM found around single and major merging galaxies in our simulation, and need to be reinforced by performing a more quantitative analysis of the specific effects of all feedback processes at play, both mechanical and radiative, which is beyond the scope of the present work.

# Summary and conclusions

In this paper, we analyze a sample of merging galaxies observed by the ALMA-ALPINE survey at redshift 4.5 \< $z$ \< 5.1, to investigate the \[CII\] emission coming from the gas *between* the galaxies. We complement the observational analysis with cosmological simulations, specifically the hydrodynamical code `dustyGadget`, looking for synthetic merging systems that helped us interpret the nature of such emission. Our main results can be summarized as follows:

1.  We analyze major merging systems in the ALPINE survey and confirm the presence of an extended (\> 20 kpc) \[CII\] halo in interacting galaxies. This extended halo is larger than the one observed in isolated galaxies as a consequence of the dynamic interaction between galaxies.

2.  We find that at least 25 % of the total \[CII\] emission associated with these systems comes from the medium surrounding the merging system, thus between the galaxies.

3.  We establish the presence of correlations, either strong or tentative, between the amount (fraction) of \[CII\] emission from the diffuse halo and integrated (relative) properties of galaxies.

4.  We find that an extended carbon-rich envelope is present in interacting systems selected from the `dustyGadget` simulation as well. In particular, extended emissions of around 10 kpc and larger than 20 kpc have been found in non-interacting and interacting systems respectively. Also, we find strong correlations between diffuse carbon in the cold gas phase - used as a proxy for \[CII\] emission - and the physical properties of galaxies, in particular, with their total carbon mass, SFR, and stellar mass, suggesting that different mechanisms reside behind \[CII\] emission.

5.  Using `dustyGadget` we investigate the nature of the metal-enriched envelope, which, apart from outflow mechanisms, can be attributed to dynamical interaction between merging galaxies, that extract carbon-rich gas out of galaxies, and the presence of star-forming satellites, that enrich the inner CGM with newborn stellar populations. We argue that most of the \[CII\] emission observed in the ALPINE systems originates from gas stripping mechanisms in turbulent collisional environments (see discussion in Section [5](#sec:discussion)), in analogy with broad \[CII\] emission observations of tidal tails of shock-excited carbon in local groups (cite: Appleton+2013).

Altogether our findings suggest that dynamical interactions and star-forming clumps at high-$z$ can be an efficient mechanism for extracting gas out of galaxies and enriching the CGM with chemically evolved material. Deeper and higher resolution ALMA data and state-of-the-art simulations with refined sub-grids models are necessary to study more in detail the key role of mergers in the baryon cycle of distant galaxies and to understand the specific role of outflows, tidal interactions, and star-forming satellites in the observed \[CII\] diffuse emission. Concerning the observations, the first results from the ALMA-CRISTAL survey (PI: Herrera-Camus) have already provided us with great details on the extended \[CII\] emission from high-$z$ galaxies (see for example (cite: Solimano+2024; Posses+2024)) laying the ground for even more in-depth observations and analyses. Moreover, ALMA observations together with future sub-mm information from single-antenna telescopes (e.g. AtLAST; (cite: Mroczkowski+2024; vanKampen+2024; Lee+2024)) would considerably improve our knowledge of the CGM and of the \[CII\] emission in the high-$z$ Universe.

# Acknowledgements

The authors would like to thank the anonymous referee for the useful suggestions which improved this article. This paper is based on data obtained with the ALMA Observatory, under Large Program 2017.1.00428.L. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. CDC would like to thank the GESO group at the European Southern Observatory (ESO) for the useful discussions while preparing this manuscript. The simulated data underlying this article will be shared on reasonable request to the corresponding author. CDC acknowledged support from Sapienza University of Rome program "Bando per la mobilità individuale all’estero" (DR n. 1607 del 14 June 2021) during the visiting period (June-November 2022) at ESO Garching, Germany. LG and RS acknowledge support from the PRIN 2022 MUR project 2022CB3PJ3 - First Light And Galaxy aSsembly (FLAGS) funded by the European Union – Next Generation EU, and from the Amaldi Research Center funded by the MIUR program "Dipartimento di Eccellenza" (CUP:B81I18001170001). MR acknowledges support from the Narodowe Centrum Nauki (UMO-2020/38/E/ST9/00077) and support from the Foundation for Polish Science (FNP) under the program START 063.2023. We have benefited from the publicly available software CASA and CARTA and programming language `Python`, including the `numpy` (<https://numpy.org>), `matplotlib` (<https://matplotlib.org>), `scipy` (<https://scipy.org>) and `astropy` (<http://www.astropy.org>) packages.

112 natexlab

(ref: Akins+2022) Akins, H. B., Fujimoto, S., Finlator, K., et al. 2022, ApJ, 934, 64

(ref: Aoyama+2020) Aoyama, S., Hirashita, H., & Nagamine, K. 2020, MNRAS, 491, 3844

(ref: Appleton+2013) Appleton, P. N., Guillard, P., Boulanger, F., et al. 2013, ApJ, 777, 66

(ref: Baes+2015) Baes, M. & Camps, P. 2015, Astronomy and Computing, 12, 33

(ref: Behroozi+2015) Behroozi, P. S., Zhu, G., Ferguson, H. C., et al. 2015, MNRAS, 450, 1546

(ref: Bethermin+2020) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2

(ref: BianchiSchneider2007) Bianchi, S. & Schneider, R. 2007, MNRAS, 378, 973

(ref: Bocchio+2016) Bocchio, M., Marassi, S., Schneider, R., et al. 2016, A&A, 587, A157

(ref: Bouwens+2022) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931, 160

(ref: Capak+2015) Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455

(ref: Cardamone+2010) Cardamone, C. N., van Dokkum, P. G., Urry, C. M., et al. 2010, ApJS, 189, 270

(ref: CarilliWalter2013) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: Carniani+2018) Carniani, S., Maiolino, R., Smit, R., & Amorı́n, R. 2018, ApJL, 854, L7

(ref: Casteels+2014) Casteels, K. R. V., Conselice, C. J., Bamford, S. P., et al. 2014, MNRAS, 445, 1157

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Conselice+2009) Conselice, C. J. & Arnold, J. 2009, MNRAS, 397, 208

(ref: Conselice+2003) Conselice, C. J., Bershady, M. A., Dickinson, M., & Papovich, C. 2003, AJ, 126, 1183

(ref: Conselice+2008) Conselice, C. J., Rajgor, S., & Myers, R. 2008, MNRAS, 386, 909

(ref: DeLooze+2014) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62

(ref: Dekel+2009) Dekel, A., Sari, R., & Ceverino, D. 2009, ApJ, 703, 785

(ref: DiCesare+2023) Di Cesare, C., Graziani, L., Schneider, R., et al. 2023, MNRAS, 519, 4632

(ref: Draine+2011) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium (Princeton University Press)

(ref: Duncan+2019) Duncan, K., Conselice, C. J., Mundy, C., et al. 2019, ApJ, 876, 110

(ref: Faisst+2020) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, The Astrophysical Journal Supplement Series, 247, 61

(ref: Faucher+Oh2023) Faucher-Giguère, C.-A. & Oh, S. P. 2023, ARA&A, 61, 131

(ref: Ferland2017) Ferland, G. J., Chatzikos, M., Guzmán, F., et al. 2017, , 53, 385

(ref: Ferrara+2019) Ferrara, A., Vallini, L., Pallottini, A., et al. 2019, MNRAS, 489, 1

(ref: Fudamoto+2022) Fudamoto, Y., Smit, R., Bowler, R. A. A., et al. 2022, ApJ, 934, 144

(ref: Fujimoto+2019) Fujimoto, S., Ouchi, M., Ferrara, A., et al. 2019, ApJ, 887, 107

(ref: Fujimoto+2020) Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, ApJ, 900, 1

(ref: Gallerani+2018) Gallerani, S., Pallottini, A., Feruglio, C., et al. 2018, MNRAS, 473, 1909

(ref: Giavalisco+2004) Giavalisco, M., Ferguson, H. C., Koekemoer, A. M., et al. 2004, ApJL, 600, L93

(ref: Ginolfi+2018) Ginolfi, M., Graziani, L., Schneider, R., et al. 2018, MNRAS, 473, 4538

(ref: Ginolfi+2020a) Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020a, A&A, 643, A7

(ref: Ginolfi+2020b) Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020b, A&A, 633, A90

(ref: Glatzle+2019) Glatzle, M., Ciardi, B., & Graziani, L. 2019, MNRAS, 482, 321

(ref: Glatzle+2022) Glatzle, M., Graziani, L., & Ciardi, B. 2022, MNRAS, 510, 1068

(ref: Graziani+2020) Graziani, L., Schneider, R., Ginolfi, M., et al. 2020, MNRAS, 494, 1071

(ref: Grevesse&Anders1989) Grevesse, N. & Anders, E. 1989, in American Institute of Physics Conference Series, Vol. 183, Cosmic Abundances of Matter, ed. C. J. Waddington, 1–8

(ref: Madau1996) Haardt, F. & Madau, P. 1996, ApJ, 461, 20

(ref: Herrera-Camus+2015) Herrera-Camus, R., Bolatto, A. D., Wolfire, M. G., et al. 2015, ApJ, 800, 1

(ref: Herrera-Camus+2021) Herrera-Camus, R., Förster Schreiber, N., Genzel, R., et al. 2021, A&A, 649, A31

(ref: Herrera-Camus+2018) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018, ApJ, 861, 95

(ref: Hollenbach+1999) Hollenbach, D. J. & Tielens, A. G. G. M. 1999, Reviews of Modern Physics, 71, 173

(ref: Hopkins+2010) Hopkins, P. F., Bundy, K., Croton, D., et al. 2010, ApJ, 715, 202

(ref: Hummels+2019) Hummels, C. B., Smith, B. D., Hopkins, P. F., et al. 2019, ApJ, 882, 156

(ref: Jones+2020) Jones, G. C., Béthermin, M., Fudamoto, Y., et al. 2020, MNRAS, 491, L18

(ref: Jones+2021) Jones, G. C., Vergani, D., Romano, M., et al. 2021, MNRAS, 507, 3540

(ref: Katz+2017) Katz, H., Kimm, T., Sijacki, D., & Haehnelt, M. G. 2017, MNRAS, 468, 4831

(ref: Kaviraj+2014) Kaviraj, S., Huertas-Company, M., Cohen, S., et al. 2014, MNRAS, 443, 1861

(ref: Knollmann+2009) Knollmann, S. R. & Knebe, A. 2009, ApJS, 182, 608

(ref: Laigle+2016) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24

(ref: Lambert+2023) Lambert, T. S., Posses, A., Aravena, M., et al. 2023, MNRAS, 518, 3183

(ref: LeFevre+2020) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1

(ref: Lee+2024) Lee, M. M., Schimek, A., Cicone, C., et al. 2024, arXiv e-prints, arXiv:2403.00924, submitted to Open Research Europe

(ref: Lin+2008) Lin, L., Patton, D. R., Koo, D. C., et al. 2008, ApJ, 681, 232

(ref: LopezSanjuan2012) López-Sanjuan, C., Le Fèvre, O., Ilbert, O., et al. 2012, A&A, 548, A7

(ref: Lupi+2020) Lupi, A. & Bovino, S. 2020, MNRAS, 492, 2818

(ref: Lupi+2020b) Lupi, A., Pallottini, A., Ferrara, A., et al. 2020, MNRAS, 496, 5160

(ref: Madau&Dickinson2014) Madau, P. & Dickinson, M. 2014, ARA&A, 52, 415

(ref: Maio+2010) Maio, U., Ciardi, B., Dolag, K., Tornatore, L., & Khochfar, S. 2010, MNRAS, 407, 1003

(ref: Maio+2007) Maio, U., Dolag, K., Ciardi, B., & Tornatore, L. 2007, MNRAS, 379, 963

(ref: Maio+2011) Maio, U., Khochfar, S., Johnson, J. L., & Ciardi, B. 2011, MNRAS, 414, 1145

(ref: Marassi+2014) Marassi, S., Chiaki, G., Schneider, R., et al. 2014, ApJ, 794, 100

(ref: Marassi+2015) Marassi, S., Schneider, R., Limongi, M., et al. 2015, MNRAS, 454, 4250

(ref: McMullin+2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mroczkowski+2024) Mroczkowski, T., Gallardo, P. A., Timpe, M., et al. 2024, arXiv e-prints, arXiv:2402.18645, submitted to A&A

(ref: Oser+2012) Oser, L., Naab, T., Ostriker, J. P., & Johansson, P. H. 2012, ApJ, 744, 63

(ref: Pallottini+2022) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2022, MNRAS, 513, 5621

(ref: Pallottini+2017) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2017, MNRAS, 465, 2540

(ref: Patton+2000) Patton, D. R., Carlberg, R. G., Marzke, R. O., et al. 2000, ApJ, 536, 153

(ref: Peeples+2019) Peeples, M., Behroozi, P., Bordoloi, R., et al. 2019, BAAS, 51, 368

(ref: CelineHowk2020) Péroux, C. & Howk, J. C. 2020, ARA&A, 58, 363

(ref: Pilbratt+2010) Pilbratt, G. L., Riedinger, J. R., Passvogel, T., et al. 2010, A&A, 518, L1

(ref: Pizzati+2020) Pizzati, E., Ferrara, A., Pallottini, A., et al. 2020, MNRAS, 495, 160

(ref: Pizzati+2023) Pizzati, E., Ferrara, A., Pallottini, A., et al. 2023, MNRAS, 519, 4608

(ref: PLANK+2016) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 594, A13

(ref: Popping+2019) Popping, G., Narayanan, D., Somerville, R. S., Faisst, A. L., & Krumholz, M. R. 2019, MNRAS, 482, 4906

(ref: Posses+2024) Posses, A., Aravena, M., González-López, J., et al. 2024, arXiv e-prints, arXiv:2403.03379, submitted to A&A

(ref: Posses+2023) Posses, A. C., Aravena, M., González-López, J., et al. 2023, A&A, 669, A46

(ref: Reeves+2023) Reeves, A. M. M. & Hudson, M. J. 2024, MNRAS, 527, 2037

(ref: Rodighiero+2011) Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, ApJL, 739, L40

(ref: Romano+2021) Romano, M., Cassata, P., Morselli, L., et al. 2021, A&A, 653, A111

(ref: Romano+2024) Romano, M., Donevski, D., Junais, et al. 2024, A&A, 683, L9

(ref: Romano+2022) Romano, M., Morselli, L., Cassata, P., et al. 2022, A&A, 660, A14

(ref: Romano+2023) Romano, M., Nanni, A., Donevski, D., et al. 2023, A&A, 677, A44

(ref: Salpeter+1955) Salpeter, E. E. 1955, ApJ, 121, 161

(ref: Schaerer+2020) Schaerer, D., Ginolfi, M., Béthermin, M., et al. 2020, A&A, 643, A3

(ref: Schaye+2015) Schaye, J., Crain, R. A., Bower, R. G., et al. 2015, MNRAS, 446, 521

(ref: Schimek+2023) Schimek, A., Decataldo, D., Shen, S., et al. 2024, A&A, 682, A98

(ref: Scoville+2007a) Scoville, N., Abraham, R. G., Aussel, H., et al. 2007a, ApJS, 172, 38

(ref: Scoville+2007b) Scoville, N., Aussel, H., Brusa, M., et al. 2007b, ApJS, 172, 1

(ref: Solimano+2024) Solimano, M., González-López, J., Aravena, M., et al. 2024, arXiv e-prints, arXiv:2401.04919, submitted to A&A

(ref: Solomon+1992) Solomon, P. M., Downes, D., & Radford, S. J. E. 1992, ApJL, 398, L29

(ref: Speagle+2014) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15

(ref: Springel2005) Springel, V. 2005, MNRAS, 364, 1105

(ref: SpringelHernquist2003) Springel, V. & Hernquist, L. 2003, MNRAS, 339, 289

(ref: Springel+2021) Springel, V., Pakmor, R., Zier, O., & Reinecke, M. 2021, MNRAS, 506, 2871

(ref: Sugahara+2019) Sugahara, Y., Ouchi, M., Harikane, Y., et al. 2019, ApJ, 886, 29

(ref: Tasca+2015) Tasca, L. A. M., Le Fèvre, O., Hathi, N. P., et al. 2015, A&A, 581, A54

(ref: Topping+2022) Topping, M. W., Stark, D. P., Endsley, R., et al. 2022, MNRAS, 516, 975

(ref: Tornatore+2007a) Tornatore, L., Borgani, S., Dolag, K., & Matteucci, F. 2007a, MNRAS, 382, 1050

(ref: Tornatore+2010) Tornatore, L., Borgani, S., Viel, M., & Springel, V. 2010, MNRAS, 402, 1911

(ref: Tornatore+2007b) Tornatore, L., Ferrara, A., & Schneider, R. 2007b, MNRAS, 382, 945

(ref: Tumlinson+2017) Tumlinson, J., Peeples, M. S., & Werk, J. K. 2017, ARA&A, 55, 389

(ref: Vallini+2020) Vallini, L., Ferrara, A., Pallottini, A., Carniani, S., & Gallerani, S. 2020, MNRAS, 495, L22

(ref: vandeVorrt+2019) van de Voort, F., Springel, V., Mandelker, N., van den Bosch, F. C., & Pakmor, R. 2019, MNRAS, 482, L85

(ref: vanKampen+2024) van Kampen, E., Bakx, T., De Breuck, C., et al. 2024, arXiv e-prints, arXiv:2403.02806, submitted to Open Research Europe

(ref: VelusamyLanger2014) Velusamy, T. & Langer, W. D. 2014, A&A, 572, A45

(ref: Venditti+2023b) Venditti, A., Bromm, V., Finkelstein, S. L., Graziani, L., & Schneider, R. 2024, MNRAS, 527, 5102

(ref: Venditti+2023) Venditti, A., Graziani, L., Schneider, R., et al. 2023, MNRAS, 522, 3809

(ref: Ventou+2017) Ventou, E., Contini, T., Bouché, N., et al. 2017, A&A, 608, A9

# \[CII\] velocity shifts

In this section we test the presence, in any, of a velocity shift among the diffuse \[CII\] component and that associated with the merging galaxies. Figure [13](#fig:vel_shift) shows the \[CII\] flux density as a function of velocity for our sample: the diffuse component (after accounting for the possible effect of the PSF broadening, see discussion in Section [3](#sec:diffEmission)) is shown in dark green while that associated to galaxies in light green. We fit these emissions with a 1D-Gaussian function and look for any shift among its central values. The velocity shift ($\Delta v_{\rm [CII]}$) is reported in the top right corner of each panel. In general, we find $\Delta v_{\rm [CII]}$ $\lesssim 19$ km/s which suggests a small difference in the kinematics of the \[CII\] emission associated with the diffuse medium and that coming from the galaxies. This result is in line with what has been found previously for ALMA-ALPINE galaxies (see for example (cite: Ginolfi+2020b) for merging systems and (cite: Fujimoto+2020) for individual galaxies), and suggests that these two regions have a similar bulk motion.

![](figures/figures_rev1/emission_v.pdf)

# The merging system H6

![](figures/H6.png)

The synthetic merging system H6 has been considered as a peculiar system and excluded from the statistical analysis previously performed, as the two interacting galaxies are very close to each other (mean distance value: r$_m$ = 5.3 kpc, see Table [\[tab:simGal\]](#tab:simGal)) resulting in a smaller fraction of carbon associated to the diffuse envelope. Indeed, it is difficult to distinguish the two merging galaxies, as shown by the x-projection in the smoothed case (see the bottom right panel in Figure [14](#fig:H6)). For this reason, we do not consider it as belonging to the "fiducial sample" of galaxies. In this system the interaction between galaxies is in such an advanced phase that the carbon mass belonging/associated to the galaxies and that of the diffuse envelope are mixed together, leading to a tricky analysis and interpretation. Moreover, the system appears differently depending on the chosen projection, resulting in large error bars (see Figures [9](#fig:diffuse_sim) and [10](#fig:fraction_sim)). This peculiar system, which can be considered as the synthetic counterpart of DC_873321 (see Section [3](#sec:diffEmission)) needs to be treated and interpreted with care.

# Carbon fraction versus average distance between galaxies

In the left panel of Figure [10](#fig:fraction_sim) we show the correlation between the fraction of carbon in the cold gas phase that resides in the diffuse envelope and the mean distance between the merging galaxies ($r_m$, averaged between three projections). The relation between these two quantities leads to a correlation with $\rho = -0.5$ and a negative trend which seems to disagree with what has been found from the analysis of the observational sample ($\rho$ = 0.9). However, by further investigating this trend we find that the positive or negative correlation depends on the considered range of values for $r_m$. In fact, as shown in Figure [15](#fig:FcR), if we only consider $r_m$ up to $\sim 16$ kpc (maximum value for the projected distance in the ALPINE sample), we recover the positive trend ($\rho = 0.8$) found in observations. This result highlights that the distance between the galaxies, thus the amount of time galaxies have been interacting, plays a fundamental role in the pollution of their inner CGM, suggesting that systems in their early phase of interaction (at larger distances) have less carbon-rich envelopes.

![](figures/fraction_r.pdf)

[^1]:

[^2]: Such as Adaptive Mesh Refinement (cite: Hummels+2019; Peeples+2019) and moving mesh codes (cite: vandeVorrt+2019).

[^3]: Among the 118 main sequence galaxies of the ALPINE sample, 75 are detected in \[CII\] at S/N \> 3.5 (cite: Bethermin+2020).

[^4]: In general, $\mu$ can be defined as : $$\begin{equation}
        \mu = X^{i}_1 / X^{i}_2
    \end{equation}$$ where $X^{i}_1$ and $X^{i}_2$ are the physical properties ($X^i$ = stellar mass; \[CII\] fluxes; $\rm K_s$-band fluxes) of the primary and secondary galaxy, with $X^{i}_1 > X^{i}_2$.

[^5]: The 2$\sigma$ region is computed as the standard deviation in the total moment-0 map once we mask the source.

[^6]: In this case, the flux is the mean Jy/beam for 2x2 pixels region.

[^7]: Radiative transfer codes are indeed needed to estimate the proper \[CII\] luminosity from synthetic galaxies, see discussion in Section [5](#sec:discussion).

[^8]: We do not consider the evolution of grain sizes, and the grains are assumed to be spherical, with a static, average size of 0.1 $\mu$m (cite: Graziani+2020).

[^9]: Double counting can happen if we count as different mergers those happening during the evolution of the same galaxy among the same ancestors across different redshift steps of its merger tree.

[^10]: This distance has been calculated averaging over the projected distances between the merging galaxies on the x,y,z planes.

[^11]: Main progenitor is the galaxy which contributes the most, in terms of stellar mass, to the descendant at the subsequent redshift.

[^12]: This temperature is the hydrodynamical one, thus it does not take into account cooling effects which may arise once we apply radiative transfer codes.

[^13]: For simplicity we dubbed systems which are not undergoing major merger as "non-interacting/single", but it is important to keep in mind that these systems are interacting with their surrounding environments and other satellite galaxies, i.e. they are not isolated.

</paper>

Write the methods card for this paper.