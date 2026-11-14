# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026A%26A...706A.292S\sonnetcc\reply.txt

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
 "bibcode": "2026A&A...706A.292S",
 "title": "Dissecting the dust distribution and polarization around two B213 young stellar objects with ALMA",
 "year": 2026,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Sato, Asako",
 "n_authors": 7,
 "arxiv_id": "2601.04091",
 "doi": "10.1051/0004-6361/202557300",
 "alma_projects_linked_by_archive": [
  "2019.1.01209.S",
  "2021.1.01420.S"
 ]
}
```

Paper text:
<paper>
# Dissecting the dust distribution and polarization around two B213 young stellar objects with ALMA

The pristine stages of disk formation during the protostellar phase and the processes of dust evolution in young disks remain largely unconstrained. Dust thermal emission at millimeter wavelengths and its polarization offer key insights into the physical processes and spatial distribution of material at the envelope-disk interface, as well as on early dust evolution around solar-type protostars. We characterize the dust properties and polarization mechanisms from envelope to disk scales in two young stellar objects (YSOs), IRAS 04166+2706 (K04166) and IRAS 04169+2702 (K04169) embedded in the same Taurus filament. We explore the nature of the dust polarization across scales and investigate their stage of evolution. We present deep ($\sim$1.4 mm and $\sim$3 mm) polarimetric observations sampling the dust emission from 25 au to 3000 au using the Atacama Large Millimeter/submillimeter Array (ALMA). We modeled Stokes $I$ emission to characterize disk and envelope contributions, while the polarization properties were analyzed to identify the dominant polarization mechanisms. Finally, in this work, we discuss the physical properties of both sources across scales. K04166 shows extended Stokes $I$ and polarized emission tracing a tentative hourglass magnetic field morphology in its envelope. In the inner envelope and disk (\<100 au), the properties of the polarized emission change, suggesting the presence of a toroidal magnetic field around the disk or the presence of large grains in the inner envelope. K04169 exhibits compact Stokes $I$ and polarized emission, consistent with self-scattering from the disk. Both disks are extremely compact, yet K04166 retains a substantial envelope while the one of K04169 is largely dissipated. Our multiscale ALMA polarimetric observations reveal a transition from magnetically aligned grains in envelopes to self-scattering in disks within the transition region of 20–50 au. These results provide important clues on dust grain growth and magnetic field morphology at the disk-envelope scales. The two sources, separated by $<0.5$ pc and embedded in a common filament, display striking differences, indicating that K04166 is a young embedded object with a substantial envelope threaded by relatively organized magnetic fields. Meanwhile, K04169 is more evolved, likely to be a young T-Tauri star. However, in both disks, the presence of large grains already suggest a scenario of early dust evolution in disks of the Class 0 stage.

# Introduction

Magnetic fields are thought to play a crucial role in the star formation process. In particular, they could play a role in regulating the formation and fragmentation of dense cores, affecting angular momentum transport during collapse, and ultimately setting the conditions for disk formation through magnetic braking (cite: Shu1987; Hennebelle_2008A&A...477....9H; Machida_2008ApJ...676.1088M; Wurster2018; Maury_2022FrASS...9.9223M; Tsukamoto_2023ASPC..534..317T). These questions are particularly relevant during the earliest protostellar stages. Class 0 protostars, with ages of only $\sim 10^{4}$ years, represent the phase when most of the final stellar mass is assembled, while young disks build up from the infalling material of the dense surrounding envelopes (cite: AWB2000; Looney2000; Jorgensen2007; Maury_2011A&A...535A..77M). Thus, understanding the magnetic field topology down to the disk-forming scales in young protostellar cores is key to constraining models of core evolution and disk formation.

Observing magnetic fields in the early stages of the star formation process helps to improve our understanding of how they redistribute angular momentum, regulate disk formation, and drive outflows (cite: Maury_2022FrASS...9.9223M). Dust polarization has long been the primary observational tracer of magnetic fields in star-forming regions. It is widely accepted that nonspherical dust grains can align with local magnetic fields via radiative torque (RAT) alignment, leading to polarized thermal emission (cite: Lazarian_2007JQSRT.106..225L; Andersson_2015ARA&A..53..501A). This technique has been successfully used from cloud scales down to dense cores, revealing mostly organized and dynamically relevant magnetic fields in the vicinity of solar-type low-mass protostars (cite: Girart_2006Sci...313..812G; Kwon_2019ApJ...879...25K; Takahashi_2019ApJ...872...70T; Huang_2024ApJ...963L..31H).

However, recent ALMA observations have demonstrated that on disk scales, polarized emission at millimeter wavelengths can also arise from self-scattering of dust thermal emission (cite: Kataoka_2015ApJ...809...78K; Stephens_2017ApJ...851...55S). This mechanism, due to the scattering of photons emitted by local thermal dust emission by the neighboring dust grains, occurs in high-density conditions in phases when grains approach sizes comparable to the observing wavelength (cite: Kataoka_2017ApJ...844L...5K; Yang_2017MNRAS.472..373Y). While self-scattering complicates the interpretation of dust polarization as a magnetic-field tracer, especially in disks where it seems to dominate in many cases, it could serve as a useful tool for measuring the sizes of dust grains in the high-density regions of inner envelopes at the disk-envelope transition, in addition to placing constraints on the dust evolution processes from submicron solid particles toward millimeter-sized ones during the disk building stage. However, young disks are very compact (cite: Maury_2019A&A...621A..76M; Sheehan2022) and, as a result, there have not been many observations that have been capable of probing the scales from envelopes to disks in polarized emission. Additionally, the required sensitivity to analyze both the magnetic field topology in the envelopes and the polarization due to self-scattering in and around the disks is very challenging. A promising way forward is to jointly study the polarized emission at envelope and disk scales around young nearby protostars. By probing both the regions where magnetic fields are expected to dominate the dynamics and those where scattering may emerge, we can hope to directly trace how dust physics and magnetic field structure evolve during the earliest stages of star formation.

In Taurus, the B213 region ($d=156 \pm 1$  pc, (cite: Gaia_Krolikowski_2021AJ....162..110K)) provides an ideal laboratory for such a study. Embedded within the L1495 complex, B213 is a $\sim 0.5$ pc -long filament, forming stars since $\lower.5ex\hbox{$\; \buildrel > \over \sim \;$}$3 Myr ago (cite: Soler2023), has been extensively studied, and stands as a classic example of a star-forming filament (cite: Schmalzl2010; Palmeirim_2013A&A...550A..38P). It consists of 35 velocity-coherent filaments traced by molecular line emission (cite: Hacar_2013A&A...554A..55H) and also shows faint dust emission striations. These striations are perpendicular to the filament and generally oriented along the magnetic field direction of the cloud, as indicated by optical and far-infrared (FIR) polarization datasets (cite: Chapman_2011ApJ...741...21C; Soler2019; Chakali_2021ApJ...912L..27E). B213 hosts several young stellar objects (YSOs) across a range of evolutionary stages, sharing a common origin and pristine environment but spanning different evolutionary stages, including two self-gravitating prestellar cores (Miz-2 and Miz-8b; (cite: Mizuno_1994Natur.368..719M; Tatematsu_2004ApJ...606..333T)), one T-Tauri star (J04194148+2716070; (cite: Davis_2010MNRAS.405..759D)), and two protostellar cores (IRAS 04166+2706 and IRAS 04169+2702; (cite: Motte2001; Rebull_2010; Marsh_2016MNRAS.459..342M)) presented in Fig. [1](#fig:NIKA-ALMA). The two protostars, IRAS 04166+2706 (K04166, Class 0) and IRAS 04169+2702 (K04169, Class I), have bolometric luminosities of 0.40 $L_\odot$and 1.46 $L_\odot$, and bolometric temperatures of 61 K and 163 K, respectively (cite: Motte2001; Ohashi_2023ApJ...951....8O). An ALMA large program, eDisk, kinematically estimated their central stellar mass to be 0.27$\pm$0.12 $M_\odot$for K04166 and 1.312$\pm$0.044 $M_\odot$for K04169 (cite: Phuong_2025ApJ...992...18P; Han_2025ApJ...993..120H). These two sources are separated by $<0.5$ pc and show parallel molecular outflows along with the magnetic field showing an organized pattern perpendicular to the elongation of filament at $\sim$0.1 pc scale (cite: Bontemps_1996A&A...311..858B; Tafalla_2004A&A...423L..21T; Narayanan_2012MNRAS.425.2641N; Goldsmith_2008ApJ...680..428G; Palmeirim_2013A&A...550A..38P). However, recent observations probing down to the core scales (\< 0.1 pc), have shown magnetic fields do not always remain aligned with the large-scale configuration: for example, the magnetic field line segments (hereafter, B-field vectors) toward K04166 and K04169 are found to be nearly orthogonal between the two cores (cite: Chakali_2021ApJ...912L..27E).

These innate similarities coupled with striking differences make K04166 and K04169 excellent test cases for studying the magnetic field and dust evolution in systems born from similar environments. In this paper, we present new multiscale polarization observations of both objects, from $\sim$900 au down to 25 au. We analyze dust properties across wavelengths and physical scales to disentangle the contributions of magnetic alignment and scattering, investigate dust evolution within the common natal environment, and study the magnetic field morphology from envelope to disk scales.

The paper is organized as follows. In Sect. [2](#sec_2), we introduce ALMA observations and our data reduction process. Sect. [3](#sec_3) presents Stokes $I$ maps and identifications of disks and envelopes in the continuum images and visibilities, along with our investigation of the polarization mechanisms for both sources. In Sect. [4](#sec_4), we discuss the nature of the polarized emission in both sources and evolutionary differences among these "twins." Finally, we present our conclusions in Sect. [5](#sec_5).

# ALMA observations and data reductions

The two ALMA projects (#2019.1.01209.S, #2021.1.01420.S, PI A. Maury) analyzed here have provided deep full-polarization observations of B213 protostars at 95 GHz and 218 GHz, utilizing both the ACA 7-m array (the 7-m array) and the ALMA 12-m array (the 12-m array) across three array configurations. While full completion of the observational program was not achieved, the datasets obtained at each band probe contrasting spatial scales. The highest resolution dataset has enabled the most detailed mapping to date of dust polarized emission in these systems, sampling spatial scales two orders of magnitude finer than in prior studies (cite: Chakali_2021ApJ...912L..27E).

This work focuses on the 3 mm and 1.4 mm dust continuum emission (the $^{12}$CO outflow maps are shown for discussion purposes in Fig. [7](#fig:outflow_polari), along with more details in Sect. [4.2](#sub:discussion-K66), yet molecular line emission is not analyzed in this study). The data reduction was conducted with CASA version 6.4.0 (cite: CASA_2022PASP..134k4501C), employing three rounds of phase self-calibration (cite: Pearson1984) for each dataset to minimize image noise and enhance fidelity. This process typically improved the quality of the 1.4 mm data from the 12-m array by a factor of approximately 7.0, for instance. Bright spectral lines were excluded during continuum extraction. The continuum maps were then produced using the `tclean` task in CASA.

We present the ALMA dataset for each of the two sources as a set of three maps sampling different scales and frequencies: 3mm (the 12-m array, Band 3), 1mm-high (the 12-m array, Band 6), and 1mm-combine (combined the 7-m and 12-m arrays, Band 6). Imaging parameters are detailed in Tables [1](#obs_para) and [2](#tab:para-continuum).

The debiased polarized intensity is defined as $P = (Q^2 + U^2 - \sigma^2_{QU})^{1/2}$, where $\sigma_{QU} = \sqrt{(\sigma_Q^2 + \sigma_U^2)/2}$, $\sigma_{Q}$ is Stokes $Q$ error, and $\sigma_{U}$ is the Stokes $U$ error (cite: Vaillancourt2006PASP..118.1340V; Hull2015JAI.....450005H). We note that we call this the debiased polarized intensity the polarized intensity in this paper and polarization maps presented here are derived with the debiased polarized intensity. We then calculate the fractional linear polarization of $P_{\mathrm{frac}} = P/I$. The position angle (P.A.) of polarization is also defined as $\chi = 1/2 \arctan(U/Q)$. To ensure robust positional sampling, we applied Super-Nyquist sampling, with pixels sampling the polarization direction (position angles) at approximately one-third of the major axis of the beam (cite: Hull_2020PASP..132i4501H). We adopted a 3$\sigma$ cutoff in total intensity 2$\sigma$ cutoff in polarized intensity for polarization fraction mapping and a 3$\sigma$ threshold on the polarized intensity for the polarization vector maps.

# Results

## Stokes $I$ dust continuum emission: an overview

![](260107_StokesI_overview.pdf)

Figure [1](#fig:NIKA-ALMA) presents a multiscale overview of the Stokes $I$ dust continuum emission in B213 from cloud-to-core scales probed by single dish observations (NIKA 2 mm map; (cite: Bracco2017A&A...604A..52B), panel a) to the core and disk scales sampled by our ALMA observations. In the data probing the core scales (NIKA map), similar dust thermal emission is associated with both protostars. However, at the smaller scale shown by our ALMA data, the emission morphology diverges between the two sources. The 1mm-combine (blue contours in panels b and d) and 3mm (magenta, panels b–e) maps reveal the dense, inner envelope ($\sim16\hbox{$^{\prime\prime}$}$ $\sim$ 2500 au) around K04166, while in K04169 the emission is dominated by a compact component with hints of filtered extended emission (ring-like structure at a very low S/N).

Finally, our highest resolution data (1mm-high; yellow contours, rightmost panels) highlight the dramatic difference between the two protostars: while K04166 is still associated with resolved emission, whose extent spans up to $\sim4\hbox{$^{\prime\prime}$}$ ($\sim$624 au) at a 5$\sigma$ level, K04169 shows solely a compact component, with a size $\lower.5ex\hbox{$\; \buildrel < \over \sim \;$}1\hbox{$^{\prime\prime}$}$ ($\sim$156 au) at a 5$\sigma$ level. In Sect. [3.2](#sec:contmodel), we describe our modeling of the dust Stokes $I$ emission from both sources to quantify the typical spatial extent of the emission, along with the respective contributions to the dust thermal emission from the disk component and from the envelope component.

## Disentangling disk and envelope contributions in the Stokes $I$ dust continuum emission

We quantified the spatial extent and origin of dust emission in both sources by modeling both the image and visibility data. In the image domain, we performed 2D Gaussian fits with CASA `imfit`, for each of the three datasets in each source and Table [\[tab:imfit_results\]](#tab:imfit_results) lists the results. The 3mm data show unresolved emission for K04169 within the $\sim1.5 \hbox{$^{\prime\prime}$}$ beam, but K04166 remains resolved, indicating distinct underlying density structures. In the table, dust emission sizes derived from the 1mm-high dataset are $21 \times 15$ au for K04166 and $30 \times 22$ au for K04169: these sizes are consistent with the dust disk radii reported by the eDisk collaboration, using similar estimation methods (cite: Ohashi_2023ApJ...951....8O; Phuong_2025ApJ...992...18P; Han_2025ApJ...993..120H).

|  |  |  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| Source | Data | Peak position | Major axis $^{a}$ | Minor axis $^{a}$ | P.A. $^{a}$ | Flux | Peak flux | Reference freq. | Inc. $^{b}$ |
|  |  | \[$04^{\mathrm{h}}19^{m}..$, $+27^\circ..$\] | (mas) | (mas) | (deg) | (mJy) | ($\text{mJy beam}^{-1}$) | (GHz) | (deg) |
| K04166 | 3mm | ${\mathrm{..}}42^{\mathrm{s}}.504,\, \mathrm{..}13'35''.89$ | $729 \pm 13$ | $554 \pm 13$ | $127$ | $12.50 \pm 0.03$ | $10.96 \pm 0.02$ | 100.748 | 41 |
| K04166 | 1mm-combine | ${\mathrm{..}}42^{\mathrm{s}}.509,\, \mathrm{..}13'35''.84$ | $402.0 \pm 5.6$ | $353.0 \pm 6.0$ | $119$ | $84.19 \pm  0.17$ | $73.27 \pm 0.09$ | 231.796 | 45 |
| K04166 | 1mm-high | ${\mathrm{..}}42^{\mathrm{s}}.509,\, \mathrm{..}13'35''.84$ | $136.6 \pm 0.5$ | $96.0 \pm  0.4$ | $125$ | $68.93 \pm  0.07$ | $50.76 \pm 0.03$ | 225.601 | 45 |
| K04169 | 3mm | ${\mathrm{..}}58^{\mathrm{s}}.474,\, {\mathrm{..}}09'56''.82$ | Unresolved | Unresolved | \- | $13.13 \pm 0.03$ | $13.15 \pm 0.02$ | 100.748 | \- |
| K04169 | 1mm-combine | ${\mathrm{..}}58^{\mathrm{s}}.478,\, {\mathrm{..}}09'56''.80$ | $169 \pm 11$ | $136 \pm 14$ | $128$ | $98.30 \pm 0.21$ | $95.97 \pm 0.12$ | 231.796 | 36 |
| K04169 | 1mm-high | ${\mathrm{..}}58^{\mathrm{s}}.477,\, {\mathrm{..}}09'56''.83$ | $195.0 \pm 0.3$ | $143.0 \pm 0.2$ | $139$ | $93.65 \pm 0.08$ | $54.132 \pm 0.030$ | 225.601 | 43 |

Table notes: Parameters obtained by minimizing an elliptical Gaussian model to the dust continuum emission maps, using the CASA task `imfit`.

![](K04166_K04169_PG_ind.pdf)

However, modeling the spatial distribution of the flux density in the maps with a Gaussian model does not allow us to disentangle the emission due to the inner envelope from the one due to the disk, if the source is embedded. Establishing the characteristics of different structures in complex objects (e.g., embedded protostars), such as the size and flux of the disk while it is embedded in its parent envelope, requires a methodology that can discriminate between the objects on a given line of sight, as well as the respective contributions of both (e.g., disk and envelope emission). It has been demonstrated that the best method to measure disk sizes in embedded protostars is to directly model the data in the Fourier space, where the power at each spatial scale is directly measured in a unambiguous way; rather than in the emission maps, where all scales are contributing to the reconstructed emission (cite: Maury_2019A&A...621A..76M; Tung2024). Thus, we carried out a modeling of the visibility amplitudes for both sources, following (cite: Maury_2019A&A...621A..76M). The uv-data used to perform the modeling include both the 7-m and 12-m arrays continuum visibility datasets obtained in Band 6, listed as 1mm-combine data in Table [1](#obs_para). The analytical models were used alone or combined, then minimized to reproduce the azimuthally averaged amplitude profiles of each source. Table [\[tab:uvmodel_all_am\]](#tab:uvmodel_all_am) summarizes the results from modeling the visibility amplitudes with Plummer envelopes, both including and not including Gaussian disks and uniform disks components.

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | Model $^{a}$ | Envelope flux | Envelope $p+q$ | Envelope $R_{in}$ | Envelope $R_{out}$ | Disk flux | Disk radius $^{b}$ | $\chi^2$ $^{c}$ | Best model? $^{d}$ |  |
|  |  | (mJy) |  | (arcsec) | (arcsec) | (mJy) | (milliarcsec - au) |  |  |  |
| K04166 | P | 247 (41) | 2.5 (0.2) | 0.001 (0.007) | 6 (2) | \- | \- | 1298 | no |  |
| K04166 | G | \- | \- | \- | \- | 74 (1) | 109 (7) - 17 | 72 | no |  |
| K04166 | D | \- | \- | \- | \- | 73 (1) | 85 (5) - 13 | 82 | no |  |
| K04166 | PG | 153 (2) | 2.2 (0.1) | 0.01 (0.05) | 15 (1) | 67 (2) | 100 (2) - 16 | 2 | yes |  |
| K04166 | PD | 150 (3) | 2.3 (0.1) | 0.01 (0.03) | 15 (1) | 65 (3) | 80 (2) - 12 | 5 | no |  |
| K04169 | P | 293 (20) | 2.5 (0.2) | 0.001 (0.008) | 6 (3) | \- | \- | 1087 | no |  |
| K04169 | G | \- | \- | \- | \- | 99 (1) | 158 (3) - 25 | 7 | no |  |
| K04169 | D | \- | \- | \- | \- | 97 (1) | 121 (2) - 19 | 15 | no |  |
| K04169 | PG | 126 (5) | 1.3 (0.5) | 0.01 (7) | 13 (3) | 98 (1) | 157 (3) - 24 | 5.7 | yes |  |
| K04169 | PD | 115 (4) | 2.8 (0.3) | 0.01 (0.6) | 15 (2) | 86 (1) | 120 (2) - 19 | 9 | no |  |

Table notes: Best-fit parameters for the four models of disk and/or envelope explored to reproduce the emission of K04166 and K04169 at 1.4 mm. he disk radius reported is either the Gaussian FWHM for the Gaussian disk model, or the radius from the uniform disk model. The radii in astronomical units are given, using a distance of 156 pc.

The best models obtained for both sources are shown in Fig. [2](#fig:uvfit_result_best). We stress that while K04166 requires a disk and a significant contribution from a dense envelope to be modeled satisfactorily (models with a Plummer envelope and a disk show reduced $\chi^2$ 2 to 3 orders of magnitude better than models including only a disk or an envelope, see Table [\[tab:uvmodel_all_am\]](#tab:uvmodel_all_am)), K04169 is satisfactorily described by models including only a disk component although models including a diffuse envelope contribution slightly improve the reduced $\chi^2$ (from 7.1 to 5.7). Our modeling estimates the disk radii to be 16 au for K04166 and 24 au for K04169. Most ($\sim 70\%$) of the flux in the 1mm-combined data comes from the disk component in K04169, while only $\lower.5ex\hbox{$\; \buildrel < \over \sim \;$}40\%$ of the total flux is due to the disk contribution in K04166, barely resolved with our data (see Fig. [2](#fig:uvfit_result_best)). We note the presence of a $\sim 5$ mJy unresolved component at the longest baselines ($> 1000 \,k\lambda$) in K04169, which was not modeled by our combination of envelope and disk components. This component could be tracing an optically thick inner disk or a disk substructure. Similarly, in K04166, our simple analytical disk model does not reproduce a feature seen as a flattening at small disk radii \< 15 au (\>1000 $\mathrm{k\lambda}$), most likely due to a constant brightness region where dust emission becomes optically thick.

Finally, we note that these models cannot faithfully characterize the properties of the outer envelope(s) at scales $\lower.5ex\hbox{$\; \buildrel > \over \sim \;$}3000$ au, as the data are intrinsically not probing any scale beyond $\sim12 \hbox{$^{\prime\prime}$}$, despite the use of the ACA data in the modeling. Nevertheless, no peaked density profile suggestive of the presence of an envelope was found around K04169 at the scales (i.e., 20-3000 au) probed by our data. Moreover, we find that the disk radius in K04166 ($\simeq 16$ au) is tentatively smaller than the K04169 one ($\simeq 24$ au), and smaller than the extent of the continuum emission probed with imfit, in the 1mm-combine map that was built from the same visibilities as those modeled here.

## Polarized dust emission in K04166

In Fig. [3](#result_K66_polari), we present the polarized dust emission observed toward K04166 across our three datasets, spanning large (left panel) to small scales (right panel). At large scales (leftmost panels), the 3 mm map appears to exhibit an elongated structure in Stokes $I$ from northeast to southwest (panel a); whereas the polarized intensity exhibits a double-peaked structure, offset from the Stokes $I$ peak, suggesting a decrease in polarized intensity along the southeastern equatorial plane (panel d).

In the 3 mm map, the polarization vectors are neither aligned with the outflow axis nor the disk major axis. Instead, the inferred B-vectors (obtained by rotating the polarization vectors by $90\ensuremath{^\circ}$) display roughly an hourglass-shaped morphology (cite: Girart_2006Sci...313..812G; Frau_2011A&A...535A..44F).

The 1mm-combine and 1mm-high maps reveal extended polarized emission elongated toward the northeast from the total intensity peak. Here, B-vectors almost align with the outflow axis in the outer regions, while (most significantly in the 1mm-high map), they are perpendicular to the disk minor axis in the inner regions. The histogram of polarization position angles (Fig. [5](#fig:PA_histogram), left panel), fitted with a two-component Gaussian, shows peaks separated by 90$^\circ$, at $43.8\ensuremath{^\circ}$ and $131.0\ensuremath{^\circ}$, indicating the inner and outer regions, respectively.

In the bottom row of Fig. [3](#result_K66_polari), the polarization fraction in the 3 mm maps is below 20% for regions above $3\sigma$ of the polarized intensity. The 1mm-combine and 1mm-high maps show polarization fractions ranging from $\sim$5 to 20% in the outer region (second Gaussian component in the histogram), and below $\sim$3% in the inner region (the first component).

Additionally, in all bottom-row maps, the peak of polarized intensity is offset from the peak of total intensity. In the 3 mm map, the two polarized peaks are offset by $\sim1.1\hbox{$^{\prime\prime}$}\pm0.1\hbox{$^{\prime\prime}$}$ and $\sim1.2\hbox{$^{\prime\prime}$}\pm 0.1\hbox{$^{\prime\prime}$}$ from the total intensity peak, and in the 1mm-combine map, the shift is $0.20\hbox{$^{\prime\prime}$}\pm 0.09\hbox{$^{\prime\prime}$}$. Finally, the 1mm-high map shows its peak polarized intensity is offset from the Stokes $I$ peak by $0.040\hbox{$^{\prime\prime}$}\pm 0.004\hbox{$^{\prime\prime}$}$, along the outflow axis [^1]. An interpretation of the origin of the polarized emission in K04166 is provided in the discussion in Sect. [4.2](#sub:discussion-K66).

## Polarized dust emission in K04169

In Fig. [4](#result_K69_polari), we can see that all the maps exhibit more compact structures than K04166 in the total intensity (the top row), and both the 3 mm and 1mm-combine polarized emission are basically unresolved, peaking roughly at the disk position. In contrast, the 1mm-high polarized emission is extended, with a size of $\sim0.6\hbox{$^{\prime\prime}$}$ at $3\sigma$, and its peak is within the disk, as shown in the bottom row. This suggests that the polarized emission in the three maps comes from the disk. The polarization fraction in the three maps is also below 2%.

The polarization angle distribution in the 1mm-high map peaks at a position angle of $56\pm 1$$^\circ$  and it shows a narrow distribution, almost parallel to the disk minor axis (see right panel of Fig. [5](#fig:PA_histogram)). The polarization angles from the 1mm-combine and 3 mm polarization maps, at the polarized peak intensity, are measured to be $55.41\ensuremath{^\circ} \pm 1.15\ensuremath{^\circ}$ and $35.38\ensuremath{^\circ} \pm 4.78\ensuremath{^\circ}$, respectively. Within the uncertainties, the position angle of the polarization vector in the 1mm-combine maps is roughly in agreement with the 1mm-high angle distribution; however, the 3 mm position angle stands out. [^2]

Additionally, all bottom-row maps show a positional offset between the peaks of total and polarized intensity, oriented roughly perpendicular to the outflow axis, although the offset is within the disk size. All the offsets are significant, as measured to be $0.04\hbox{$^{\prime\prime}$}\pm 0.005\hbox{$^{\prime\prime}$}$ for the 1mm-high map, $0.50\hbox{$^{\prime\prime}$}\pm 0.16\hbox{$^{\prime\prime}$}$ for the 3mm map, and $0.06\hbox{$^{\prime\prime}$}\pm 0.02\hbox{$^{\prime\prime}$}$ for the 1mm-combine map. An interpretation of the origin of the polarized emission in K04169 is provided in the discussion in Sect. [4.3](#sub:discussion-K69).

![](251223_twins_K66_overview.pdf)

![](251223_twins_K69_overview.pdf)

![](251223_result_histogram_2.pdf)

# Discussion

## Optical depths of the dust thermal emission

We calculated the brightness temperatures at the peak of the dust continuum emission from the 1mm-high maps, following $$\begin{equation}
      T_B = 1.222 \times 10^3 \, 
      \left[ \frac{I}{\rm mJy \, beam^{-1}} \right] \,
      \left[ \frac{\nu}{\rm GHz} \right] ^{-2} \,
      \left[ \frac{\theta_\mathrm{maj}}{''} \right]^{-1} \,
      \left[ \frac{\theta_\mathrm{min}}{''} \right]^{-1} \,
 ,
\end{equation}$$ where $T_B$ is the brightness temperature, $I$ is the peak intensity, $\nu$ is the frequency (218.4 GHz here), and $\theta_\mathrm{maj}$ and $\theta_\mathrm{min}$ are the half-power beam widths along the major and minor axes, respectively. We find brightness temperatures at the peak of the dust continuum emission of 30.7 K for K04166 and 33.8 K for K04169. However, the disks are only partially resolved, since their deconvolved FWHM (see Table [\[tab:imfit_results\]](#tab:imfit_results)) are slightly smaller than the 1mm-high beam. That means that the estimated brightness temperature values are beam diluted. For a Gaussian, the filling factor is defined as $f \, = \, \theta_\mathrm{src}^2/(\theta_\mathrm{src}^2+\theta_\mathrm{bm}^2)$, where $\theta_\mathrm{src}$ and $\theta_\mathrm{bm}$ are the geometrical FWHM average of the disks and of the beam, respectively. After correcting for filling factor, we found the brightness temperature of 90 K for K04166 and 47 K for K04169. These are lower than peak brightness temperatures obtained at higher angular resolution, 133 K and 64 K, respectively (cite: Ohashi_2023ApJ...951....8O). Furthermore, given their bolometric luminosities, the expected dust temperatures at their disk radius (Table [\[tab:uvmodel_all_am\]](#tab:uvmodel_all_am)) are $\sim$75 K and 80 K for K04166 and K04169, respectively. This indicates that the dust emission is fully optically thick for K04166 and moderately optically thick for K04169. According to (cite: Yang_2017MNRAS.472..373Y), a dust optical depth of $\sim$1–2 is sufficient to produce 1–2$\%$ levels of polarized emission from self-scattering. Thus, at the beam scales characterizing our data, the polarized emission should be interpreted on the basis of this hypothesis.

## Nature of the polarized emission in K04166

![](251130_K66_selfscaterring_envelope.pdf)

Our observations of K04166 reveal tentative evidence for a scale-dependent transition in the dominant dust polarization mechanism. The 3mm maps indicate an extended component of the polarization, beyond 500 au scales, with a tentative hourglass-shaped magnetic field (see panel a of Fig. [3](#result_K66_polari)): this polarized emission has relatively high polarization fraction values ($\gtrsim 5$%), suggesting that in these regions, polarized dust emission traces magnetically aligned grains. Our observations are consistent with previous observations tracing magnetic field lines pinched by gravitational infall in protostellar envelopes, commonly referred to as the “hourglass” magnetic field morphology (cite: LeGouellec_2019ApJ...885..106L; Huang_2024ApJ...963L..31H).

In contrast, the 1mm-high and 1mm-combine maps (panels b and c of Fig. [3](#result_K66_polari)) still trace this large-scale component, but also reveal the polarization vectors differing from the large-scale component by 90$^\circ$ in the inner regions (the left panel of Fig. [5](#fig:PA_histogram)). Previous studies have shown that self-scattering-induced polarization is characterized by the polarization vectors parallel to the disk minor axis and low polarization fractions, supporting our interpretation (cite: Kataoka_2015ApJ...809...78K; Huang_2024ApJ...963L..31H; Liu_2024ApJ...963..104L). Thus, our observations could be interpreted as a transition, in K04166, from polarization due to self-scattering at disk scales to magnetically aligned grains at envelope scales.

To distinguish the possible different origin of the polarized emission, we adopt a 3% polarization fraction threshold on the highest resolution 1mm-high map, to either (i) rotate by 90$^\circ$ the polarization angles if the polarization fraction is larger than this threshold or (ii) keep the polarization angle below this threshold, which occurs around or within the disk. In this latter case, the polarization angle is, on average, parallel to the disk’s minor axis. This is a strong indication of self-scattering (cite: Kataoka_2015ApJ...809...78K; Brunngraber2021A&A). In Fig. [6](#fig:K66_dis_1), we see the spatial distribution obtained between these two regimes assuming this ad hoc, simple threshold. We note that at the boundary where the polarization vectors switch to B vectors, the polarization fraction drops to nearly zero on the northern side of the disk. This coincides with a steady increase in total intensity, which could be interpreted as a result of cancellation between the self-scattering polarization component and the magnetic alignment polarization component.

Additionally, the area in which the polarization fraction stays low exceeds that of the disk’s extent (orange ellipse in Fig. [6](#fig:K66_dis_1)), which could either be due to a beam effect spreading the polarized signal from the disk, or to some polarized emission due to self-scattering produced in the inner envelope. However, we stress that the precise location of the transition between polarization mechanisms depends on how both mechanisms are discriminated, which is itself sensitive to model assumptions. In our data, the 3mm map, with its tentative hourglass morphology and large polarization fraction, strongly suggests the presence of elongated grains because only elongated grains would be able to align with the local magnetic field. This interpretation leads to two possibilities for the observed transition between the envelope and the disk, where the polarization angle appears to be parallel to the disk minor axis, but with two distinct regions, one with low polarization fraction, $\lesssim 2$%, and the other with high values,$\gtrsim 4$% (orange and green segments, respectively, in Fig. [6](#fig:K66_dis_1)). First, the observed pattern may trace a toroidal magnetic field in the envelope, close to the disk’s outer radius. If this is the case, the large polarization fraction at the large envelope densities expected at disk’s scales could be explained by recent theoretical studies, where mechanical and enhanced radiative torque alignment may be important (cite: Hoang2022; Giang2024; Giang2025). Alternatively, the emission results from self-scattering in both cases, indicating that large grains exist outside the disk, in the inner envelope. Theoretical studies suggest that self-scattering by spherical grains can produce polarization fractions of up to a few percent (cite: Kataoka_2015ApJ...809...78K), but models with nonspherical grains allow for larger values (cite: Kirchschlager_2020A&A...638A.116K) of the polarization fraction.

If the detection of self-scattering were eventually confirmed in the envelope of K04166, this could provide an additional strong observational evidence for the presence of significantly grown dust grains in the innermost regions of protostellar envelopes, which would be in agreement with the small emissivity indices of dust sometimes measured at millimeter wavelengths in these environments (cite: Galametz2019; Cacciapuoti2025). However, we stress that the typical grain size needed to produce the self-scattering signal is subject to large uncertainties, as self-scattering depends not solely on grain size but also on the dust structure and optical properties, as discussed above. These findings may motivate future theoretical work to refine predictions regarding the polarization mechanisms at play when physical conditions allow both magnetically aligned grains and self-scattering to produce polarized emission. These findings could also support the enhanced presence of large, millimeter-sizes, grains lifted from the disk. For example, (cite: Cacciapuoti_2024) reported an anti-correlation between the dust opacity index ($\beta$) in the inner envelope and the mass-loss rate of jets and outflows. This suggests that grains with large sizes detected in envelopes could come from dust uplifted from the disk via outflows. This scenario is supported by both analytical and MHD models (cite: Wong_2016_10.1093/pasj/psw066; Lebreuilly_2020A&A...641A.112L; Tsukamoto_2021; Bhandare2024) and it could also explain the observed polarization patterns in the transition region. Future observations with ALMA at different frequencies (Bands 1 and 10), at comparable resolution, will be crucial to disentangling the contributions of self-scattering and magnetic alignment, while also linking them to measurements of the dust $\beta$. Such multifrequency, high-angular resolution data will provide new constraints on the processes responsible for dust evolution, dust transport, and the robustness of millimeter polarized dust emission to trace the magnetic field structure down to very small scales in protostellar systems.

Finally, Fig. [7](#fig:outflow_polari) shows the gas tracing the outflows for both sources from our data. The left panel of Fig. 7 exhibits that, in the high-resolution data (1mm-high and 1mm-combine), the polarized emission is highly asymmetric, with the detection of B-vectors seen mostly toward the blue-shifted outflow lobe. In this region, the polarization is enhanced along outflow cavity walls; in addition, its magnetic field direction at these 500–1000 au scales has a similar orientation as the large-scale B-field threading the B213 filament (cite: Palmeirim_2013A&A...550A..38P). Such enhanced polarized emission has been reported before in high angular resolution observations of protostars; for instance, in B335 and Serpens (cite: Maury2018; LeGouellec_2019ApJ...885..106L). It is also occasionally associated with the locations where molecular tracers indicate high ionization fractions. Thus, it has been interpreted as enhanced dust alignment efficiency along the magnetic field lines in these regions, which receive larger fluxes of ultraviolet and optical photons able to align the small grains, owing to the opening of the outflow cavity where photons from the central protostar can propagate further than along the high-density sightlines through the equatorial plane (cite: LeGouellec_2023A&A...675A.133L).

## Nature of the polarized emission in K04169

In Sect. [3.4](#ResultsK04166), we described how K04169 exhibits compact polarized emission, low polarization fractions, and the polarization vectors approximately parallel to the disk minor axis. Furthermore, the polarized intensity peak in K04169 is offset from the peak of the dust thermal emission (Stokes $I$). These features suggest that the polarization at 1 mm is dominated by self-scattering of dust grains from the disk (cite: Kataoka_2015ApJ...809...78K). We note that the polarization fractions at radii $> 30$ au show high values in the map (see Fig. [4](#result_K69_polari)f), whereas the polarized intensity has an extent larger (deconvolved size of 64 au, see Table [\[tab:imfit_pol_app\]](#tab:imfit_pol_app)) than the thermal dust continuum emission extent (deconvolved size 30 au). This could stem from a true difference in the spatial extents of the polarized and Stokes I emission or from intrinsically high polarization fractions at such scales.

The 3 mm polarization from K04169, on the other hand, exhibits a weak compact detection, and the peak of polarized intensity is significantly offset from the peak of Stokes $I$ from the high-resolution 1 mm data. Moreover, the polarization angle is not consistent with the polarization angle measured in the 1mm maps: the differences are significant between both the 3 mm and 1mm-high maps ($35.4\pm4.8$$^\circ$ and $56.0\pm1.0$$^\circ$, respectively). Despite a low signal-to-noise ratio (S/N of 6 at the peak for the 3 mm map), these may indicate the presence of another component contributing to the detected polarized emission at 3 mm, either magnetically aligned grains from the surrounding material, or optical depth effects affecting the disk polarization differently at 1 mm and 3 mm. In addition, higher sensitivity and angular-resolution observations are necessary to characterize the origin of the 3 mm polarization signal in K04169. In such a case, the orientation of the polarization vectors suggests either magnetically aligned dust grains along a toroidal B-field, or polarization due to self-scattering which would tentatively suggest some dust growth in the inner envelope where high-density materials surround the disk. The detection of polarized emission due to self-scattering in disks has been reported, either in Class II YSO (cite: Bacciotti_2018ApJ...865L..12B; Dent2019MNRAS.482L..29D), or in embedded protostars (cite: Harris2018; Sadavoy2019; CFLee2021; Huang_2024ApJ...963L..31H). It has been interpreted as evidence of the presence of large grains in these young disks. Following computations from the literature, our detection of self-scattering at the disk scales in K04169 could suggest dust grains as large as hundreds of micrometers. However, as discussed before, large uncertainties remain when attempting to compute a maximum grain size from the detection of millimeter polarized emission associated with self-scattering.

Interestingly, previous 850 $\mu$m JCMT observations (probing $\sim$0.01 pc scales) display a polarization angle of $59\pm7$$^\circ$ (cite: Chakali_2021ApJ...912L..27E), which is similar to the ALMA 1 mm polarization angles, $\simeq56$$^\circ$. Furthermore, the polarization fraction from JCMT data at this position is $0.8\pm0.2\%$, consistent with the ALMA 1mm value ($\sim$0.5%). This indicates that the JCMT polarization signal is likely dominated by self-scattering from the compact disk mapped by ALMA and, thus, it might not trace magnetic fields toward K04169. This is also supported by the fact that the orientation of polarization vectors from the single-dish is almost perpendicular to the B-field lines at the filament scale (cite: Palmeirim_2013A&A...550A..38P). Thus, we stress that the magnetic-field strength estimate proposed from the JCMT data toward K04169 might have to be revised.

The right panel of Fig. [7](#fig:outflow_polari) shows the $\mathrm{^{12}CO}$ line emission tracing the outflow associated with K04169. We note that the $\mathrm{^{12}CO}$ outflow detected in our high angular resolution observations of K04169 shows a different orientation than the large-scale outflow reported by (cite: Narayanan_2012MNRAS.425.2641N) ($\sim$30$^\circ$), and more in agreement with the orientation reported by (cite: Tokuda_2020ApJ...899...10T) with the ACA observations sampling the 1000 au scales ($\sim$64$^\circ$). We did not further analyze the molecular line emission; however, the dynamical time of the outflow detected in our data (a few $10^3$ yr) is estimated to be shorter than that of the outflow identified by (cite: Narayanan_2012MNRAS.425.2641N) ($\sim7\times10^4$ yr). These different outflow position angles and different dynamical times may indicate precession, suggesting a possible link between polarization orientation, dust evolution, and toroidal B-field structure.

## Evolution: Comparing the twin protostars

![](251115_outflow_polari_K66_K69.pdf)

![](251222_near-far_asymmetry.pdf)

K04166 and K04169 are both embedded in the B213 filament of Taurus and it is often assumed they are similarly young protostars formed from the same parent molecular structure, thus sharing similar large-scale environments and initial conditions. At the core scale ($\sim$0.1 pc), single-dish IRAM 30m and NIKA observations show that both sources are associated with extended dust emission (cite: Bracco2017A&A...604A..52B). Yet, the maps reveal that K04169 exhibits a more compact dust continuum emission than K04166, despite both sources showing similarly extended emission at the $\sim$0.1 pc scale in the single-dish filament map (Fig. [1](#fig:NIKA-ALMA)). Our analysis of the visibility reveals that there is no significant envelope emission associated with K04169 in the ALMA/ACA data; rather, there is a contribution from a diffuse extended component present, which does not contribute to the flux at scales 100-1000 au around the disk. This behavior is more characteristic of cloud emission than envelope emission. This suggests that the surrounding material in K04169 has largely been accreted or dispersed, while K04166 remains embedded within its natal envelope. We also evaluated the flux recovered by our ALMA 1mm-combine continuum map, from the single-dish peak flux measured by the IRAM 30 m/MAMBO data at 240 GHz (12$^{\prime\prime}$resolution, (cite: Motte2001)). We find 90.0% and 57.2% of the MAMBO peak flux is recovered at the scales probed by ALMA ($1-7\hbox{$^{\prime\prime}$}$), for K04166 and K04169 respectively.[^3] A comparison of Fig. [1](#fig:NIKA-ALMA) (b) and (d) indicates that the emission associated with K04169 is very compact, while the extended emission recovered by ALMA in the 1mm-combine maps toward K04166 almost fills the 12-arcsec single-dish beam. This suggests that the missing flux toward K04169 does not originate from its immediate surroundings, but instead from the dust present on a larger scale ($\gtrsim 1000$ au), likely stemming from the B123 filament. Consequently, a substantial portion of the spectral energy distribution (SED) for K04169 at FIR wavelengths may not be linked to this YSO (cite: Ohashi_2023ApJ...951....8O). In summary, the dust distribution at the envelope scales indicates that K04166 is a true protostar, while K04169 is significantly more evolved. The lack of an envelope suggests that it is likely in a late Class I or an early Class II stage.

The protostellar nature of K04166 is also supported by the facts that the envelope is threaded by a well-organized, hourglass-shaped magnetic field, extending down to approximately the 20 au disk level, and that it shows a notable alignment with the large-scale magnetic field of its surrounding cloud (Fig. [3](#result_K66_polari)a). Another protostellar signature is the single collimated outflow and jet toward K04166; while the outflow opening angle at small scales for K04169 is much wider (see Fig. [7](#fig:outflow_polari); (cite: Tafalla_2004A&A...423L..21T)). This is consistent with a later evolutionary phase for K04169, as it has been suggested that the molecular outflows become less collimated when the protostar evolves from the Class 0 to I stage (cite: Hsieh_2023ApJ...947...25H; Dunham_2024MNRAS.533.3828D). Finally, while SiO emission is a good tracer of high-velocity shocked gas (cite: Mikami_1992ApJ...392L..87M; Sato_2023ApJ...958..102S), only K04166 has indicated the presence of an SiO jet so far (cite: Phuong_2025ApJ...992...18P). All these properties point toward an interpretation of K04166 being significantly younger than K04169. Finally, at disk scales, both the polarized and total intensities show a pronounced nearside-farside asymmetry along the disk minor axis (Fig. [8](#fig:dis_near_far)). The asymmetry in the total intensity occurs due to geometric effects, as seen in both K04166 and K04169 maps (cite: Takakuwa_2024ApJ...964...24T). In contrast, only the K04166 map displays the asymmetry of the polarized intensity along the disk minor axis. This occurs due to the difference in the local inclination angle of the disk surface to the line of sight in optically thick disks, characterizing younger and less settled dusty disks (cite: Yang_2017MNRAS.472..373Y; Bacciotti_2018ApJ...865L..12B).

In the case of K04169, it might be unexpected to find it associated with a molecular flow if it is a Class II YSO. Still, ALMA data has revealed a gas "streamer" that connects the disk of K04169 to the larger cloud structures (cite: Han_2025ApJ...993..120H). This could explain the late, yet significant accretion onto the disk and the ensuing presence of the observed active outflow. Such late accretion systems are frequently observed now that low surface brightness gas can be mapped at high angular resolution in local star-forming regions (see, e.g., the T-Tauri disks harboring streamers in (cite: Huang_DOtau_2022ApJ...930..171H; Garufi_DGtau_2022A&A...658A.104G; Gupta_2023A&A...670L...8G; Huang_DRtau_2023ApJ...943..107H)). Interestingly, the extent of the disk from the 1mm dust thermal emission is found to be larger for K04169 than for K04166, while the star is more evolved, and both probably formed in similar conditions. We stress that this is not what would be expected by disk evolution models, where large dust grains drift rapidly toward the inner radii, producing smaller dusty disk sizes as the disk evolves (cite: Sanchis_2021A&A...649A..19S; Trapman_2025ApJ...989...10T). It has been suggested that a significant fraction of Class I protostars in Taurus may be embedded Class II (cite: Carney2016). If K04169 is a T-Tauri formed elsewhere, considering typical proper motions of T-Tauri objects (a few km/s), it could have traveled up to 2pc in 1Myrs and thus could have been formed anywhere in the filament, independently of K04166. The age and spatial extent of B213 (cite: Gaia_Krolikowski_2021AJ....162..110K) would thus allow for different evolutionary stages to be found within the local environment. However, both YSOs are embedded in the B213 filament: they may thus have been formed locally from the same filamentary material. The both large-scale outflows are aligned with the magnetic field lines threading the filament (see (cite: Palmeirim_2013A&A...550A..38P; Narayanan_2012MNRAS.425.2641N)) and the disks planes show a similar orientation with respect to the surrounding filament (P.A. (125$^\circ$ for K04166 and 139$^\circ$ for K04169, see Table [\[tab:imfit_results\]](#tab:imfit_results)), roughly parallel to the filament elongation and perpendicular to the filament-scale magnetic field. These observed properties further support a scenario of local formation for both YSOs. We note that the antiparallel character of the red and blue lobes results from a difference in the inclination angles of the disks (see the inclination angles derived from aspect ratios in Table [\[tab:imfit_results\]](#tab:imfit_results)), generating different projections of the outflowing gas velocities on the line of sight. This could also be due to the initial magnetic field at disk scales being misaligned with the disk rotation axis (cite: Hirano_2019MNRAS.485.4667H). Hence, our data are consistent with a scenario of sequential star formation where B213 had fragmented into cores (cite: Hacar_2013A&A...554A..55H); however, this process did not occur all at once: K04169 was formed first and is now in a stage of late Class I or early Class II, while K04166 formed second and is now still a Class 0 protostar in its main accretion phase. We note that between the two YSOs, there is a prestellar core, which is possibly the next protostar to be formed in B213, likely within a few $10^4$ years, strengthening the plausibility of a scenario of sequential star formation in B213.

# Conclusions

In this paper, we present high-angular resolution ALMA polarimetric observations of two YSOs in the B213 filament of Taurus, K04166 and K04169, probing disk and envelope scales to study the dust thermal emission, polarization mechanisms, and magnetic field morphologies. These deep observations were obtained in Band 3 (3 mm) and Band 6 (1.4 mm), using both ACA 7-m and ALMA 12-m arrays to sample spatial scales from $\sim$25 au to 3000 au. We modeled the Stokes $I$ emission with 2D Gaussian fits and by directly fitting visibility profiles to disentangle disk and envelope contributions. Polarization fractions and orientations were analyzed to distinguish between magnetically aligned grains and self-scattering mechanisms across scales. While K04166 and K04169 are two known examples for studying how protostars with similar birth environments can grow and evolve, our data shed light on very different small-scale properties for these two neighboring sources. We summarize our main findings below.

- Disk and envelope evolution distinguishes the twin sources: detailed visibility modeling reveals that K04166 retains a massive envelope and a small disk, consistent with a young, actively accreting protostar. K04169 exhibits no significant envelope at scales of 20–3000 au, and its emission is disk-dominated, indicating that it is likely a late Class I or early Class II object. Despite sharing a similar environment, K04166 and K04169 display striking differences, suggesting different episodes of star formation or a different in the delay resulting from the effect of the local magnetic fields on the collapse of dense cores into YSOs (even close by, i.e., within a single filament).

- Multiscale transition in polarization mechanisms: K04166 shows a clear transition from magnetically aligned grain polarization in the envelope (suggesting an hourglass-shaped magnetic field) to self-scattering-induced polarization at disk scales, while K04169 is dominated by self-scattering consistent with large dust grains in its compact disk. We show tentative evidence that some of the 1 mm polarized emission in K04166, outside the disk radius, might either be due to self-scattering coming from the inner envelope or it traces a toroidal magnetic field surrounding the disk, at scales $\lower.5ex\hbox{$\; \buildrel < \over \sim \;$}100$ au.

- Evidence for early dust grain growth: while we refrained from interpreting these data to propose an associated dust grain size, as the relationship between grain size and self-scattering signature at mm wavelengths is subject to large uncertainties, we stress that large grains are already present in both disks, confirming the scenario of early dust evolution in disks from the Class 0 stage. Moreover, no self-scattering is detected at 3mm from the young K04166 disk, while compact polarization, probably due to self-scattering, is detected at 3mm from K04169, suggesting a more advanced dust evolution in the K04169 disk.

# Acknowledgements

This work is funded by the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation program (grant agreement No. 101098309 - PEBBLES). AS acknowledges support by the grant CNS2023-145240 (Consolida). JMG and AS acknowledge support by the grant PID2023-146675NB-I00 (MCI-AEI-FEDER, UE). This work is also partially supported by the program Unidad de Excelencia María de Maeztu CEX2020-001058-M. Andrea Bracco acknowledges financial support from the INAF initiative "IAF Astronomy Fellowships in Italy" (grant name MEGASKAT).

95 natexlab

(ref: Andersson_2015ARA&A..53..501A) Andersson, B. G., Lazarian, A., & Vaillancourt, J. E. 2015, ARA&A, 53, 501

(ref: AWB2000) André, P., Ward-Thompson, D., & Barsony, M. 2000, in Protostars and Planets IV, ed. V. Mannings, A. P. Boss, & S. S. Russell, 59

(ref: Bacciotti_2018ApJ...865L..12B) Bacciotti, F., Girart, J. M., Padovani, M., et al. 2018, ApJL, 865, L12

(ref: Bhandare2024) Bhandare, A., Commerçon, B., Laibe, G., et al. 2024, A&A, 687, A158

(ref: Bontemps_1996A&A...311..858B) Bontemps, S., Andre, P., Terebey, S., & Cabrit, S. 1996, A&A, 311, 858

(ref: Bracco2017A&A...604A..52B) Bracco, A., Palmeirim, P., André, P., et al. 2017, A&A, 604, A52

(ref: Brunngraber2021A&A) Brunngräber, R. & Wolf, S. 2021, A&A, 648, A87

(ref: Cacciapuoti2025) Cacciapuoti, L., Testi, L., Maury, A. J., et al. 2025, A&A, 700, A188

(ref: Cacciapuoti_2024) Cacciapuoti, L., Testi, L., Podio, L., et al. 2024, The Astrophysical Journal, 961, 90

(ref: Carney2016) Carney, M. T., Yıldız, U. A., Mottram, J. C., et al. 2016, A&A, 586, A44

(ref: CASA_2022PASP..134k4501C) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Chapman_2011ApJ...741...21C) Chapman, N. L., Goldsmith, P. F., Pineda, J. L., et al. 2011, ApJ, 741, 21

(ref: Cutri_2003yCat.2246....0C) Cutri, R. M., Skrutskie, M. F., van Dyk, S., et al. 2003, VizieR Online Data Catalog: 2MASS All-Sky Catalog of Point Sources (Cutri+ 2003), VizieR On-line Data Catalog: II/246. Originally published in: University of Massachusetts and Infrared Processing and Analysis Center, (IPAC/California Institute of Technology) (2003)

(ref: Cutri_2012wise.rept....1C) Cutri, R. M., Wright, E. L., Conrow, T., et al. 2012, Explanatory Supplement to the WISE All-Sky Data Release Products, Explanatory Supplement to the WISE All-Sky Data Release Products

(ref: Davis_2010MNRAS.405..759D) Davis, C. J., Chrysostomou, A., Hatchell, J., et al. 2010, MNRAS, 405, 759

(ref: Dent2019MNRAS.482L..29D) Dent, W. R. F., Pinte, C., Cortes, P. C., et al. 2019, MNRAS, 482, L29

(ref: Dunham_2024MNRAS.533.3828D) Dunham, M. M., Stephens, I. W., Myers, P. C., et al. 2024, MNRAS, 533, 3828

(ref: Chakali_2021ApJ...912L..27E) Eswaraiah, C., Li, D., Furuya, R. S., et al. 2021, ApJL, 912, L27

(ref: Frau_2011A&A...535A..44F) Frau, P., Galli, D., & Girart, J. M. 2011, A&A, 535, A44

(ref: Galametz2019) Galametz, M., Maury, A. J., Valdivia, V., et al. 2019, A&A, 632, A5

(ref: Garufi_DGtau_2022A&A...658A.104G) Garufi, A., Podio, L., Codella, C., et al. 2022, A&A, 658, A104

(ref: Giang2024) Giang, N. C. & Hoang, T. 2024, MNRAS, 530, 984

(ref: Giang2025) Giang, N. C., Le Gouellec, V. J. M., Hoang, T., Maury, A. J., & Hennebelle, P. 2025, ApJ, 980, 105

(ref: Girart_2006Sci...313..812G) Girart, J. M., Rao, R., & Marrone, D. P. 2006, Science, 313, 812

(ref: Goldsmith_2008ApJ...680..428G) Goldsmith, P. F., Heyer, M., Narayanan, G., et al. 2008, ApJ, 680, 428

(ref: Gudel_2007A&A...468..353G) Güdel, M., Briggs, K. R., Arzner, K., et al. 2007, A&A, 468, 353

(ref: Gupta_2023A&A...670L...8G) Gupta, A., Miotello, A., Manara, C. F., et al. 2023, A&A, 670, L8

(ref: Hacar_2013A&A...554A..55H) Hacar, A., Tafalla, M., Kauffmann, J., & Kovács, A. 2013, A&A, 554, A55

(ref: Han_2025ApJ...993..120H) Han, I., Kwon, W., Aso, Y., et al. 2025, ApJ, 993, 120

(ref: Harris2018) Harris, R. J., Cox, E. G., Looney, L. W., et al. 2018, ApJ, 861, 91

(ref: Hennebelle_2008A&A...477....9H) Hennebelle, P. & Fromang, S. 2008, A&A, 477, 9

(ref: Hirano_2019MNRAS.485.4667H) Hirano, S. & Machida, M. N. 2019, MNRAS, 485, 4667

(ref: Hoang2022) Hoang, T., Tram, L. N., Minh Phan, V. H., et al. 2022, AJ, 164, 248

(ref: Hsieh_2023ApJ...947...25H) Hsieh, C.-H., Arce, H. G., Li, Z.-Y., et al. 2023, ApJ, 947, 25

(ref: Huang_2024ApJ...963L..31H) Huang, B., Girart, J. M., Stephens, I. W., et al. 2024, ApJL, 963, L31

(ref: Huang_DRtau_2023ApJ...943..107H) Huang, J., Bergin, E. A., Bae, J., Benisty, M., & Andrews, S. M. 2023, ApJ, 943, 107

(ref: Huang_DOtau_2022ApJ...930..171H) Huang, J., Ginski, C., Benisty, M., et al. 2022, ApJ, 930, 171

(ref: Hull_2020PASP..132i4501H) Hull, C. L. H., Cortes, P. C., Gouellec, V. J. M. L., et al. 2020, PASP, 132, 094501

(ref: Hull2015JAI.....450005H) Hull, C. L. H. & Plambeck, R. L. 2015, Journal of Astronomical Instrumentation, 4, 1550005

(ref: Jorgensen2007) Jørgensen, J. K., Bourke, T. L., Myers, P. C., et al. 2007, ApJ, 659, 479

(ref: Kataoka_2015ApJ...809...78K) Kataoka, A., Muto, T., Momose, M., et al. 2015, ApJ, 809, 78

(ref: Kataoka_2017ApJ...844L...5K) Kataoka, A., Tsukagoshi, T., Pohl, A., et al. 2017, ApJL, 844, L5

(ref: Kirchschlager_2020A&A...638A.116K) Kirchschlager, F. & Bertrang, G. H. M. 2020, A&A, 638, A116

(ref: Gaia_Krolikowski_2021AJ....162..110K) Krolikowski, D. M., K1raus, A. L., & Rizzuto, A. C. 2021, AJ, 162, 110

(ref: Kwon_2019ApJ...879...25K) Kwon, W., Stephens, I. W., Tobin, J. J., et al. 2019, ApJ, 879, 25

(ref: Lazarian_2007JQSRT.106..225L) Lazarian, A. 2007, JQSRT, 106, 225

(ref: LeGouellec_2019ApJ...885..106L) Le Gouellec, V. J. M., Hull, C. L. H., Maury, A. J., et al. 2019, ApJ, 885, 106

(ref: LeGouellec_2023A&A...675A.133L) Le Gouellec, V. J. M., Maury, A. J., Hull, C. L. H., et al. 2023, A&A, 675, A133

(ref: Lebreuilly_2020A&A...641A.112L) Lebreuilly, U., Commerçon, B., & Laibe, G. 2020, A&A, 641, A112

(ref: CFLee2021) Lee, C.-F., Li, Z.-Y., Yang, H., et al. 2021, ApJ, 910, 75

(ref: Liu_2024ApJ...963..104L) Liu, Y., Takahashi, S., Machida, M., et al. 2024, ApJ, 963, 104

(ref: Looney2000) Looney, L. W., Mundy, L. G., & Welch, W. J. 2000, ApJ, 529, 477

(ref: Machida_2008ApJ...676.1088M) Machida, M. N., Inutsuka, S.-i., & Matsumoto, T. 2008, ApJ, 676, 1088

(ref: Marsh_2014MNRAS.439.3683M) Marsh, K. A., Griffin, M. J., Palmeirim, P., et al. 2014, MNRAS, 439, 3683

(ref: Marsh_2016MNRAS.459..342M) Marsh, K. A., Kirk, J. M., André, P., et al. 2016, MNRAS, 459, 342

(ref: Maury_2022FrASS...9.9223M) Maury, A., Hennebelle, P., & Girart, J. M. 2022, Frontiers in Astronomy and Space Sciences, 9, 949223

(ref: Maury_2011A&A...535A..77M) Maury, A. J., André, P., Men’shchikov, A., Könyves, V., & Bontemps, S. 2011, A&A, 535, A77

(ref: Maury_2019A&A...621A..76M) Maury, A. J., André, P., Testi, L., et al. 2019, A&A, 621, A76

(ref: Maury2018) Maury, A. J., Girart, J. M., Zhang, Q., et al. 2018, MNRAS, 477, 2760

(ref: Mikami_1992ApJ...392L..87M) Mikami, H., Umemoto, T., Yamamoto, S., & Saito, S. 1992, ApJL, 392, L87

(ref: Mizuno_1994Natur.368..719M) Mizuno, A., Onishi, T., Hayashi, M., et al. 1994, Nature, 368, 719

(ref: Motte2001) Motte, F. & André, P. 2001, A&A, 365, 440

(ref: Naghizadeh-Khouei_1993A&A...274..968N) Naghizadeh-Khouei, J. & Clarke, D. 1993, A&A, 274, 968

(ref: Narayanan_2012MNRAS.425.2641N) Narayanan, G., Snell, R., & Bemis, A. 2012, MNRAS, 425, 2641

(ref: Ohashi_2023ApJ...951....8O) Ohashi, N., Tobin, J. J., Jørgensen, J. K., et al. 2023, ApJ, 951, 8

(ref: Palmeirim_2013A&A...550A..38P) Palmeirim, P., André, P., Kirk, J., et al. 2013, A&A, 550, A38

(ref: Pearson1984) Pearson, T. J. & Readhead, A. C. S. 1984, ARA&A, 22, 97

(ref: Phuong_2025ApJ...992...18P) Phuong, N. T., Lee, C. W., Tobin, J. J., et al. 2025, ApJ, 992, 18

(ref: Rebull_2010) Rebull, L. M., Padgett, D. L., McCabe, C.-E., et al. 2010, The Astrophysical Journal Supplement Series, 186, 259

(ref: Sadavoy2019) Sadavoy, S. I., Stephens, I. W., Myers, P. C., et al. 2019, ApJS, 245, 2

(ref: Sanchis_2021A&A...649A..19S) Sanchis, E., Testi, L., Natta, A., et al. 2021, A&A, 649, A19

(ref: Sato_2023ApJ...958..102S) Sato, A., Tokuda, K., Machida, M. N., et al. 2023, ApJ, 958, 102

(ref: Schmalzl2010) Schmalzl, M., Kainulainen, J., Quanz, S. P., et al. 2010, ApJ, 725, 1327

(ref: Serkowski_1958AcA.....8..135S) Serkowski, K. 1958, , 8, 135

(ref: Sheehan2022) Sheehan, P. D., Tobin, J. J., Looney, L. W., & Megeath, S. T. 2022, ApJ, 929, 76

(ref: Shu1987) Shu, F. H., Adams, F. C., & Lizano, S. 1987, ARA&A, 25, 23

(ref: Soler2019) Soler, J. D. 2019, A&A, 629, A96

(ref: Soler2023) Soler, J. D., Zucker, C., Peek, J. E. G., et al. 2023, A&A, 675, A206

(ref: Stephens_2017ApJ...851...55S) Stephens, I. W., Yang, H., Li, Z.-Y., et al. 2017, ApJ, 851, 55

(ref: Tafalla_2004A&A...423L..21T) Tafalla, M., Santiago, J., Johnstone, D., & Bachiller, R. 2004, A&A, 423, L21

(ref: Tafalla_2017A&A...597A.119T) Tafalla, M., Su, Y. N., Shang, H., et al. 2017, A&A, 597, A119

(ref: Takahashi_2019ApJ...872...70T) Takahashi, S., Machida, M. N., Tomisaka, K., et al. 2019, ApJ, 872, 70

(ref: Takakuwa_2024ApJ...964...24T) Takakuwa, S., Saigo, K., Kido, M., et al. 2024, ApJ, 964, 24

(ref: Takakuwa_2018ApJ...865...51T) Takakuwa, S., Tsukamoto, Y., Saigo, K., & Saito, M. 2018, ApJ, 865, 51

(ref: Tatematsu_2004ApJ...606..333T) Tatematsu, K., Umemoto, T., Kandori, R., & Sekimoto, Y. 2004, ApJ, 606, 333

(ref: position_accuracy) The ALMA Proposer’s. Guide, Section A.9.5 and ALMA Technical Handbook, Chapter 10.5.2 Astrometric Observations., <https://almascience.eso.org/documents-and-tools/documents-and-tools>, accessed: 2025-07-15

(ref: Tokuda_2020ApJ...899...10T) Tokuda, K., Fujishiro, K., Tachihara, K., et al. 2020, ApJ, 899, 10

(ref: Trapman_2025ApJ...989...10T) Trapman, L., Vioque, M., Kurtovic, N. T., et al. 2025, ApJ, 989, 10

(ref: Tsukamoto_2021) Tsukamoto, Y., Machida, M. N., & Inutsuka, S.-i. 2021, The Astrophysical Journal Letters, 920, L35

(ref: Tsukamoto_2023ASPC..534..317T) Tsukamoto, Y., Maury, A., Commercon, B., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 317

(ref: Tung2024) Tung, N.-D., Testi, L., Lebreuilly, U., et al. 2024, A&A, 684, A36

(ref: Vaillancourt2006PASP..118.1340V) Vaillancourt, J. E. 2006, PASP, 118, 1340

(ref: Wong_2016_10.1093/pasj/psw066) Wong, Y. H. V., Hirashita, H., & Li, Z.-Y. 2016, Publications of the Astronomical Society of Japan, 68, 67

(ref: Wurster2018) Wurster, J. & Li, Z.-Y. 2018, Frontiers in Astronomy and Space Sciences, 5, 39

(ref: Yang_2017MNRAS.472..373Y) Yang, H., Li, Z.-Y., Looney, L. W., Girart, J. M., & Stephens, I. W. 2017, MNRAS, 472, 373

# Observations and map-making

The details of the observations carried out are presented in Table [1](#obs_para). The imaging parameters used to produce the maps presented in this analysis are summarized in Table [2](#tab:para-continuum).

| Project code | 2019.1.01209.S | 2021.1.01420.S | 2021.1.01420.S |
|:---|:--:|:--:|:--:|
| Band | 3 | 6 | 6 |
| Array | ALMA 12-m array | ACA 7-m array | ALMA 12-m array |
| Configuration | C43-3 | \- | C43-6 |
| Representative frequency (GHz) | 93.17 | 219.55 | 219.55 |
| Number of executions | 3 | 6 | 2 |
| Observation date (YYYY-MM-DD) | 2019-11-02 | 2022-05-18 – 2022-07-03 | 2022-07-13 |
| Number of antennas | 41 – 42 | 9 – 10 | 37 – 41 |
| Phase center for K04166 (ICRS) | $04^{\mathrm{h}}19^{\mathrm{m}}42.50^{\mathrm{s}}$, $+27^\circ13'13.38''$ | $04^{\mathrm{h}}19^{\mathrm{m}}42.50^{\mathrm{s}}$, $+27^\circ13'36.10''$ | $04^{\mathrm{h}}19^{\mathrm{m}}42.50^{\mathrm{s}}$, $+27^\circ13'36.10''$ |
| Phase center for K04169 (ICRS) | $04^{\mathrm{h}}19^{\mathrm{m}}58.46^{\mathrm{s}}$, $+27^\circ09'56.90''$ | $04^{\mathrm{h}}19^{\mathrm{m}}58.46^{\mathrm{s}}$, $+27^\circ09'56.90''$ | $04^{\mathrm{h}}19^{\mathrm{m}}58.46^{\mathrm{s}}$, $+27^\circ09'56.90''$ |
| HPBW primary beam (arcsec) | 49.7 | 40.8 | 21.6 |
| Mean PWV (mm) | 3.17 – 3.43 | 0.53 – 1.56 | 0.51, 0.61 |
| Baseline ($k\lambda$) | 4 - 151 | 5 - 30 | 10 - 1744 |
| Maximum recoverable size (arcsec) | 17.1 | 21.3 – 30.5 | 2.7 |

: Observation parameters for the analyzed data.

Table notes: HPBW (full width at half power) of the primary beam is defined as $\sim1.13 \lambda / D$ (ALMA technical handbook).

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | Project | Dataset | Array | Rest frequency | Robust | Synthesized beam, P.A. | Stokes | Noise level |
|  |  |  |  | (GHz) |  | (arcsec $\times$ arcsec, deg.) |  | ($\mathrm{{\mu Jy\,beam}^{-1}}$) |
| K04166 | #2019.1.01209.S | 3mm | 12-m | 94.5 | 0.5 | $1.96 \times 1.52$, $-$23 | $I$ | 17 |
|  |  |  |  |  |  |  | $Q$ | 16 |
|  |  |  |  |  |  |  | $U$ | 16 |
| 2-9 | #2021.1.01420.S | 1mm-combine | 12-m + 7-m | 230.8 | 0.5 | $1.01 \times 0.95$, $-$27 | $I$ | 89 |
|  |  |  |  |  |  |  | $U$ | 69 |
|  |  |  |  |  |  |  | $Q$ | 44 |
| 3-9 |  | 1mm-high | 12-m | 218.4 | 0.5 | $0.24 \times 0.16$, $-$27 | $I$ | 25 |
|  |  |  |  |  |  |  | $Q$ | 21 |
|  |  |  |  |  |  |  | $U$ | 21 |
|  |  | 1mm-high | 12-m | 218.4 | $+$2.0 | $0.38 \times 0.23$, $-$24 | $I$ | 33 |
|  |  |  |  |  |  |  | $Q$ | 18 |
|  |  |  |  |  |  |  | $U$ | 18 |
| K04169 | #2019.1.01209.S | 3mm | 12-m | 94.5 | 0.5 | $1.97 \times 1.51$, $-$26 | $I$ | 18 |
|  |  |  |  |  |  |  | $Q$ | 16 |
|  |  |  |  |  |  |  | $U$ | 16 |
| 2-9 | #2021.1.01420.S | 1mm-combine | 12-m + 7-m | 230.8 | 0.5 | $1.02 \times 0.95$, $-$27 | $I$ | 116 |
|  |  |  |  |  |  |  | $Q$ | 71 |
|  |  |  |  |  |  |  | $U$ | 45 |
| 3-9 |  | 1mm-high | 12-m | 218.4 | 0.5 | $0.24 \times 0.16$, $-$27 | $I$ | 28 |
|  |  |  |  |  |  |  | $Q$ | 21 |
|  |  |  |  |  |  |  | $U$ | 21 |

: Continuum imaging parameters.

Table notes: The dataset of 1mm-combine was obtained by combining the ACA 7-m array and ALMA 12-m array data in Band 6. For the 1mm-high data of K04166, we used the maps with the natural weighting in the result section to clearly distinguish the characteristics of the polarized emission in the inner and outer regions, such as the position angle of the polarization vectors, by imaging the extended emission. In contrast, we used the maps with Briggs weighting in the discussion section to investigate the transition region (borderline) between the inner and outer regions, which corresponds to the disk size. In addition, the visibility fitting requires us to average the channels with similar frequencies for the 1mm-combine data. We, thus, extracted two spectral windows that have similar rest frequencies out of the three spectral windows to make the required visibility. That is why their rest frequency is different from that in the 1mm-high data.

# imfit to the polarized intensity maps (K04169)

To compare the morphologies in the polarized intensity with those in total intensity, we implemented the image-based fitting to the polarization maps of K04169. Table [\[tab:imfit_pol_app\]](#tab:imfit_pol_app) presents the results obtained from 2D Gaussian fitting on the polarization maps for K04169 using `imfit`.

|  |  |  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| Data | Peak position | Major axis $^{a}$ | Minor axis $^{a}$ | P.A. $^{a}$ | Flux | Peak flux |  |  |  |
|  | R.A., Dec. (ICRS) | (mas) | (mas) | (deg) | ($\mathrm{\mu Jy}$) | ($\mathrm{\mu Jy\,beam}^{-1}$) |  |  |  |
| 1mm-high | $04^{\mathrm{h}}19^{\mathrm{m}}58^{\mathrm{s}}.478, +27^\circ09'56''.85$ | $413 \pm 88$ | $351 \pm 84$ | $133$ | $994 \pm 160$ | $208 \pm 28$ |  |  |  |
| 1mm-combine | $04^{\mathrm{h}}19^{\mathrm{m}}58^{\mathrm{s}}.472, +27^\circ09'56''.73$ | Unresolved | Unresolved | \- | $417 \pm 24$ | $448 \pm 15$ |  |  |  |
| 3mm | $04^{\mathrm{h}}19^{\mathrm{m}}58^{\mathrm{s}}.490, +27^\circ09'56''.77$ | Unresolved | Unresolved | \- | $47 \pm 25$ | $78\pm18$ |  |  |  |

Table notes: These results were obtained using the CASA task `imfit`. We note that we did not identify polarized structures for K04166 due to its complicated geometry.

[^1]: Note: the errors stem from the ALMA relative positional accuracy between the positions of two sources or features in a map, as given by $\sim0.5\times \mathrm{beam_{FWHM} / SNR}$ (cite: position_accuracy).

[^2]: Note: the position angle errors are estimated as $28.65\ensuremath{^\circ}$/SNR, with S/N as the signal-to-noise ratio of the polarized intensity, from (cite: Serkowski_1958AcA.....8..135S; Naghizadeh-Khouei_1993A&A...274..968N).

[^3]: (cite: Motte2001) measured the peak flux to be $180\pm8\,\mathrm{mJy\,beam^{-1}}$ for K04166 and $190\pm9\,\mathrm{mJy\,beam^{-1}}$ for K04169 at 240 GHz in the MAMBO map. We scaled the MAMBO flux to the ALMA frequency (231.8 GHz) using a spectral index $\alpha = 3$ (as measured at large scales in the NIKA data; see (cite: Bracco2017A&A...604A..52B)). Note: the ALMA integrated fluxes ($\geq 3\sigma$) come from scales smaller than the 12$^{\prime\prime}$single-dish beam.

</paper>

Write the methods card for this paper.