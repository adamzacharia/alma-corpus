# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...985..148L\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...985..148L",
 "title": "L1448 IRS3B: Dust Polarization Aligned with Spiral Features, Tracing Gas Flows",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Looney, Leslie W.",
 "n_authors": 14,
 "arxiv_id": "2503.07787",
 "doi": "10.3847/1538-4357/adcb9f",
 "alma_projects_linked_by_archive": [
  "2021.1.00276.S"
 ]
}
```

Paper text:
<paper>
# L1448 IRS3B: Dust Polarization Aligned with Spiral Features, Tracing Gas Flows

## Abstract

Circumstellar disk dust polarization in the (sub)millimeter is, for the most part, not from dust grain alignment with magnetic fields but rather indicative of a combination of dust self-scattering with a yet unknown alignment mechanism that is consistent with mechanical alignment. While the observational evidence for scattering has been well established, that for mechanical alignment is less so. Circum-multiple dust structures in protostellar systems provide a unique environment to probe different polarization alignment mechanisms. We present ALMA Band 4 and Band 7 polarization observations toward the multiple young system L1448 IRS3B. The polarization in the two Bands is consistent with each other, presenting multiple polarization morphologies. On the size scale of the inner envelope surrounding the circum-multiple disk, the polarization is consistent with magnetic field dust grain alignment. On the very small scale of compact circumstellar regions, we see polarization that is consistent with scattering around source $a$ and $c$, which are likely the most optically thick components. Finally, we see polarization that is consistent with mechanical alignment of dust grains along the spiral dust structures, which would suggest that the dust is tracing the relative gas flow along the spiral arms. If the gas-flow dust grain alignment mechanism is dominant in these cases, disk dust polarization may provide a direct probe of the small-scale kinematics of the gas flow relative to the dust grains.

# Introduction

Dust continuum polarization was first unequivocally detected in a circumstellar disk a decade ago (cite: Stephens2014). Dust polarized emission is routinely used to infer the magnetic field morphology in star formation regions down to the scale of the inner envelopes of young protostars (cite: Hull2014; Cox2018; Galametz2018; LeGouellec2020; Maury2022; Huang2024), but over the last few years it has become clear that the polarization in circumstellar disks has multiple mechanisms, including dust self-scattering (cite: Kataoka2015; Yang2016) and some yet unknown dust grain alignment mechanism (cite: Yang2019; Mori2021; Hoang2022; Tang2023; Lin2024a). In fact, direct magnetic field alignment appears to be unlikely in the vast majority of circumstellar disk cases with the possible exceptions of some circumbinary disks, such as BHB 07-11 (cite: Alves2018), VLA 1623 (cite: Sadavoy2018), HD 142527 (cite: Ohashi2018; Ohashi2025), and GG Tau (cite: Tang2023), and the single system TMC1A (cite: Aso2021), given that toroidal magnetic field models generally reproduce the observed polarization for those sources. However, higher resolution observations are critical to model the polarization emission uniquely (cite: Dent2019; Lin2020; Stephens2023).

Observed polarization due to dust self-scattering is possible if the dust grains are comparable in size to the observing wavelength, there is some optical depth, and there is some anisotropy of the radiation field (cite: Kataoka2015). When observed in inclined circumstellar disks, the polarization morphology from scattering will be along the minor axis of the disk with fractional polarizations (polarized emission / Stokes I emission) of $\sim$1% (cite: Kataoka2015; Yang2016).

Elongated dust grains may be aligned in the disk, which can also produce polarized emission. The most commonly accepted alignment mechanism in the ISM is grain alignment from magnetic fields via Radiative Alignment Torques (cite: Dolginov1976; Draine1997), which typically has fractional polarizations of $\sim$5-15%. However, recent work has suggested that it is unlikely for $\gtrapprox$100 $\mu$m dust grains, as may be expected in disks, to be aligned by magnetic fields (cite: Yang2021).

Dust grain alignment due to purely Radiative Alignment Torques is often called k-RAT with expected fractional polarizations $\sim$1% (cite: Tazaki2017; Hoang2022), but purely radiative alignment was shown to likely be a less important mechanism in circumstellar disks (cite: Yang2019; Mori2019).

In addition to magnetic and radiative torques, dust grains can be aligned by mechanical torques. For helical dust grains, if the Larmor precession time is shorter than the mechanical precession time, then the grains can still become aligned to the B-field even if the origin of the torques was completely from mechanical torques, often called B-MET (cite: Hoang2016). If the Larmor precession time is longer than the mechanical precession time, then the grains can become aligned with their short axis to the gas flow, often called v-MET (or v-MAT) (cite: Lazarian2007; Hoang2018; Hoang2022). In some cases, the dust helicity allows the dust grains to be rotated up suprathermally with only subsonic drift (cite: Hoang2018). In addition, dust grains with or without helicity may be aligned by mechanical alignment with their long axis aligned to the gas flow (cite: Gold1952), although this is a stochastic torque and not as strongly driven as in the v-MET case. On the other hand, recent work by (cite: Lin2024b) suggests that gas drag alone can align dust grains through relative gas-dust motion, without the supersonic requirement of (cite: Gold1952), when the dust grain’s center of mass is slightly offset from its geometric center, which they call badminton birdie alignment. In other words, there are many possible dust grain alignment mechanisms that can cause dust polarization in disks, in addition to scattering, and observations are beginning to constrain the dominant polarization origins in disks.

Circumstellar disks with multiwavelength observations have shown interesting variations in some disk polarization observations with the emission being consistent with dust self-scattering at the short wavelengths of ALMA (i.e., polarization angles aligned with the disk minor axis), smoothly transitioning to an azimuthal pattern at longer wavelengths (cite: Kataoka2017; Harrison2019; Ohashi2023; Lin2024a). For example, in the cases of HL Tau and DG Tau, the disks have both a higher polarization fraction and a more azimuthal polarization orientation at the longer wavelength of Band 3 than at Band 7 (cite: Kataoka2017; Ohashi2023), which is not possible from self-scattering polarization alone. Note that radiative grain alignment does not match the azimuthal pattern observations as k-RAT would produce a circular morphology (like a bulls-eye) whereas the observations at long wavelengths instead produce elliptical patterns (cite: Yang2019; Mori2019). On the other hand, some disks show polarization that is dominated by dust self-scattering at both ALMA bands 3 and 7 (cite: Harrison2019; Harrison2024).

Recent models have shown that the polarization across ALMA bands may be explained as an optical depth effect. At high optical depth, the polarization is dominated by scattering, while at lower optical depth, the polarization is dominated by aligned grains, with a smooth transition between the two limits (cite: Stephens2017; Mori2019; Lin2022; Lin2024a). High resolution Band 7 observations of HL Tau with its gaps and rings have reinforced this viewpoint as the rings, which have higher optical depth, are dominated by dust self-scattering, while the gaps are dominated by aligned grains (cite: Stephens2023). However, the dust scattering of the HL Tau rings still places constraints on the maximum dust grains size (assuming a spheroidal, non-porous power-law dust grain distribution) of $\sim$100$\mu$m, which is hard to reconcile with the maximum dust grain size of a few millimeters from dust continuum emission modeling (cite: Kwon2011; Carrasco-Gonzalez2019).

In order to explore the polarization of disks, we use the young multiple protostellar system L1448 IRS3, as circumbinary disks to date are among the few sources with posited combinations of magnetic field and scattering polarization mechanisms. The L1448 IRS3 system is at a distance of 288 pc based on recent constraints (cite: Ortiz2018; Zucker2019). The system consists of three distinct sources at $\sim$1$''$ resolution (cite: Looney2000), the brightest of these in the (sub)millimeter dust continuum is L1448 IRS3B, which is projected in the northern blushifted lobe of the outflow cavity of the source L1448-mm. In addition, the protostar L1448 IRS3A, which is $\sim$2300 au to the north, is interacting gravitationally with L1448 IRS3B (cite: Kwon2006; Nick2021; Reynolds2023; Gieser2024).

L1448 IRS3B has long thought to be a young (likely $<$150 kyrs) Class 0 protostar (cite: Dunham2015; Podio2021; Reynolds2023). This is consistent with the recently compiled SED from the eHOPS catalog[^1], which gives a combined bolometeric temperature for L1448 IRS3A and B of 25.6 K (cite: Pokhrel2023). L1448 IRS3A is considered to be less embedded, perhaps being Class I (cite: Reynolds2023). L1448 IRS3C (L1448 NW) is 17$\ensuremath{''}$ to the northwest of IRS3B and has a bolometeric temperature of 21.8 K (cite: Pokhrel2023), which also suggests a Class 0 source (cite: Enoch2009). IRS3C is a close binary (separation 72 au) with the two protostars having their own disks (cite: Reynolds2023).

The L1448 IRS3B protostellar multiple source has a circum-multiple disk caught in the act of fragmenting creating at least three and likely four protostars (cite: John2016; Nick2021; Reynolds2023). There are three compact dust emission peaks detected in ALMA Bands 6 and 7 that are thought to be three protostellar sources. Source $c$, to the east of the central region, is the brightest in the dust continuum, but it is thought to be the youngest protostar with an upper limit on the protostellar mass of 0.2 M$_\odot$ whereas the combined mass of sources $a$ and $b$, near the center, is $\sim$1.2 M$_\odot$ (cite: Nick2021). The circum-multiple disk has a Keplerian rotation pattern that places the kinematic center of the system near source $a$. Recent high resolution observations in Band 6 detect a fourth compact source (source $d$) near the kinematic center of the system surrounded by a ring of material, implying that this may be a quadruple protostellar system (cite: Reynolds2023). Note that these stellar masses are still comparable to other Class 0 source masses seen in multiple low-mass systems such as Ced110 IRS4A/B or R CrA IRAS 32A/B (cite: Yen2024).

Previous polarization observations of L1448 IRS3B (cite: Kwon2006) showed $\lambda$ = 1.3 mm linear dust polarization on the scale of $\sim$5$\ensuremath{''}$ in the inner envelope that was $\sim$5% polarized with a polarization angle of -70$^\circ$ (east of north), if only the central vectors are considered, which was also consistent with larger scale ($\sim$13$\ensuremath{''}$ resolution) James Clerk Maxwell Telescope (JCMT) SCUBAPOL $\lambda$ = 850 $\mu$m dust linear polarization observations (cite: Kwon2006). More recent JCMT POL-2 observations with increased sensitivity are also consistent with the BIMA and SCUBAPOL observations (Kim et al., in prep). With $\lambda$ = 870 $\mu$m Submillimeter Array (SMA) dust observations at $\sim$3$\ensuremath{''}$ resolution, a dust polarization fraction of $\sim$3% with a polarization angle of -67$^\circ$ (east of north) has been observed (cite: Galametz2018). In all cases, the polarization is generally consistent with dust grains in the inner envelope of L1448 IRS3B aligned with an inferred large scale magnetic field at a PA of 23$^\circ$, although it has yet to be directly proven.

In this paper, we present ALMA Band 4 and 7 dust polarization observations of the L1448 IRS3B system. We use the dust polarization to infer possible polarization mechanisms in the circum-multiple disk and inner envelope of L1448 IRS3B, finding evidence of three polarization mechanisms. In §2, we present the observations and data reduction, in §3, we present the results of the observations, in §4, we discuss the results and place constraints on the polarization mechanisms, in §5, we present our conclusions, and in the Appendix, we provide our observations of other sources in the field: images of L1448 IRS3A, L1448 IRS3C (or L1448 NW), and a newly detected point source in Band 4 that is likely a background galaxy.

# Observations and Data Reduction

The Atacama Large Millimeter/submillimeter Array (ALMA) observations in full polarization at continuum Band 4 and Band 7 (i.e. $\lambda$ = 2.1 mm and 873 $\mu$m, respectively) were obtained as part of project 2021.1.00276.S. The observational details are described in Table [\[tab:obs\]](#tab:obs). The observations were calibrated by the National Radio Astronomy Observatory staff (since polarization is a non-standard observing mode) within CASA, Common Astronomy Software Applications (cite: casa2022), version 6.4.1.12.

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Band | Robust | Beam | $\sigma_I^a$ | $\sigma_Q$ | $\sigma_U$ | $\sigma_P$ |  |
|  |  |  | ($\mu$Jy/bm) | ($\mu$Jy/beam) | ($\mu$Jy/bm) | ($\mu$Jy/bm) |  |
| 4 | 0.5 | 0.25$''$ $\times$ 0.18$''$, 1.9$^{\circ}$ | 16.7 | 7.3 | 7.5 | 7.4 |  |
| 4 | 1.0 | 0.30$''$ $\times$ 0.22$''$, 0.2$^{\circ}$ | 26.7 | ... | ... | ... |  |
| 7 | 0.5 | 0.15$''$ $\times$ 0.10$''$, 11.7$^{\circ}$ | 114.0 | 25.0 | 26.0 | 25.5 |  |
| 7$^b$ | 0.5 | 0.25$''$ $\times$ 0.18$''$, 1.9$^{\circ}$ | 307.1 | 34.2 | 38.6 | 36.5 |  |

After the data were calibrated, we further performed self-calibration using the `auto-selfcal`[^2] script with `refantmode=‘strict’`. The Band 4 observations were iteratively self-calibrated, phase only, with intervals of `inf-EB`, `inf`, 26.21s, 8.06s, 4.03s, and `int`. The `inf-EB` interval averages the entire execution block (when combined with `combine=’scan,spw’` during the `gaincal` step of applying the derived gains to the visibilities) and corrects the time invariant phase errors in the data. At the shorter time step, `int` does not do any time averaging and corrects time variant phase errors down to the integration time.

Afterwards, a round of amplitude and phase self-calibration was performed with an interval of 300s to further improve the calibration. The Band 7 observations were self-calibrated, phase only, with intervals of `inf-EB`, `inf`, and finally 48.38s. Afterwards, a round of amplitude and phase self-calibration was performed with an interval of `inf` to further improve the calibration.

The Stokes I, Q, and U maps were then created using the CASA task `tclean` with a `Briggs` weighting `Robust` weighting of 0.5, which is a good compromise between resolution and sensitivity (cite: Briggs1995). The measured linear polarization intensity map is created using $P_m = \sqrt{Q^{2} + U^{2}}$. The linear polarized intensity noise is defined as $\sigma_{P} = \sqrt{(\sigma_{Q}^{2} + \sigma_{U}^{2})} / 2$, where $\sigma_{Q}$ and $\sigma_{U}$ are the noises in the Stokes Q and I maps given in Table [\[tab:maps\]](#tab:maps). Following (cite: Wardle1974; Vaillancourt2006; Hull2015), the linear polarization at low S/N ($<$ 3$\sigma_P$) was debiased using the probability density function (PDF)

$$\begin{align}
    \text{PDF}(P | P_{m}, \sigma_{P}) = 
    \frac{P}{ \sigma_{P}^{2} } I_{0} 
    \bigg(\frac{ P P_{m} }{ \sigma_{P}^{2} } \bigg) 
    \exp{ \bigg[ - \frac{ ( P_{m}^{2} + P^{2})}
    {2 \sigma_{P}^{2}} \bigg]},
\end{align}$$ which provides the true linear polarized intensity $P$ given our measured linear polarized intensity and the noise level $\sigma_{P}$, using a zeroth-order modified Bessel function of the first kind $I_{0}$. For higher S/N, the approximation $P = \sqrt{ Q^{2} + U^{2} -  \sigma_{P}^{2}}$ was used to debias the linear polarization. The polarization angle is calculated using $\chi = \frac{1}{2} \arctan (\frac{U}{Q})$, where $\sigma_{\chi} = \frac{1}{2} \frac{ \sigma_{P} }{ P }$.

As suggested in the ALMA handbook, the absolute flux calibration accuracy is adopted to be $\sim$10%.

# Results

## L1448 IRS3B Results

![](L1448_I_nocont_IRS3B_abcd.pdf)

In Figure [1](#stokesI), we present the dust continuum images of L1448 IRS3B in Band 4 and Band 7. These are the highest resolution continuum observations of the system at Band 4 to date. Band 4 is more sensitive to larger structures due to its shorter baselines (see Table [\[tab:obs\]](#tab:obs)). Nonetheless, the Band 4 map overall matches the continuum structures seen in Band 7. The Band 7 image is consistent with the slightly higher resolution dust continuum Band 7 observations in (cite: Nick2021). We detect at both wavelengths the arcs or spiral structures and the three compact sources defined by (cite: John2016), labeled $a$, $b$, and $c$ in Figure [1](#stokesI).

The spiral structures are very clear in both Bands. However, the C$^{17}$O (3-2) velocity field measured at 0.2$''$ spatial resolution reveals Keplerian motion around a location near source $a$ without any clear perturbations caused by the spiral structures (cite: Nick2021). On the northwest of the disk, there is a sharp decrease in dust emission at both Bands that is nearly opposite of source $c$.

Higher resolution ($\sim$8 au) Band 6 ALMA observations of IRS3B detected a fourth compact source, named source $d$, near the kinematic center of the system (cite: Reynolds2023), also labeled in Figure [1](#stokesI). They also resolved a ring (whose outer edges can be seen near the center of Band 7 in Figure [1](#stokesI)) surrounding source $d$ and enclosing source $a$; source $a$ is just inside the ring, and source $b$ is just outside the ring. In fact in the Band 7 map, source $a$ is slightly extended to the northeast, which is perhaps a hint of source $d$ or more likely a blending of the ring and source $a$.

![](BrightnessTemp.full.pdf)

This central ring is more noticeable in Figure [2](#TB), which presents the Band 4 and 7 continuum brightness temperature maps (made without using the Rayleigh-Jeans approximation). The brightness temperature is the temperature required for a blackbody to match the observed intensity. In Band 7 of Figure [2](#TB), the central ring, in which source $a$ is located, is more clearly seen.

In general the brightness temperatures are higher at Band 7, typically by factors of 1.25 for the central region and 1.5 near the compact sources and around the east-north-west edge of the outer spiral (as traced by the 10-$\sigma$ contour in Band 7 of Figure [2](#TB)). This is likely an optical depth effect due to the shorter wavelength Band 7 being more optically thick, which yields a brightness temperature closer to the physical temperature at its $\tau=1$ surface that should be at a higher vertical height where the temperature is likely higher.

However, the comparison between the two brightness temperatures may be affected by the observations. In particular, Band 4 is more sensitive to the envelope structure, as is evident by the substantially larger detected dust emission region in Band 4 compared to Band 7 (as suggested by the 10-$\sigma$ contours in Figure [2](#TB) and the maximum recovery scale listed in Table [\[tab:obs\]](#tab:obs)). As Band 4 has more envelope emission detected (i.e., it is less resolved out), this will decrease the relative flux of the disk in Band 7, since Band 7 observations are not on top of the envelope emission plateau. This will also only allow lower-limits on any estimate of the spectral index, see §[4](#sec:disc) for more discussion.

Figure [3](#LPI) presents the linearly polarized emission and polarization angle in both Bands. The polarization morphology is similar at both Bands, as is best illustrated in Figure [4](#BothPol), which overlays the polarization angles at both Bands without any scaling for polarization fraction (Figure [4](#BothPol), left) and the difference between the two Bands when smoothed to the same spatial resolution (Figure [4](#BothPol), right). It is important to note that the two wavelengths generally have the same polarization orientations in most locations in the source with a few exceptions that are likely due to differences in the *u,v* sampling of the two observations or differences in optical depth. The measured polarization angles in Figure [4](#BothPol) (left) extend further out than the ones in Figure [3](#LPI) since the Stokes I cutoff is 3-$\sigma$ in the former and 10-$\sigma$ in the latter. This was done to make the polarization angles easier to view since the angles on the outskirts of the disk have very high polarization fractions (i.e. more than 10%), which may be due to observational biases.

When observing deeply embedded protostars, the measurement of the envelope polarization is driven by the sensitivity to the larger spatial scale of the envelope structures. With interferometeric observations, if the polarization feature of the envelope is smaller or less smooth (i.e. more clumpy) than the envelope continuum emission, one may observe envelope polarization although the envelope itself may be mostly resolved out, which then results in a very high polarization fraction since the continuum measurement is low. This is likely the origin of the high polarization fractions seen around the outer edge of the circumbinary disk in Figure [3](#LPI) (cite: LeGouellec2020).

In addition, when we compare Figures [1](#stokesI) and [3](#LPI), the peak Stokes I locations and the peak polarization locations are in general offset. In the case of source $a$, there is not a specific polarization peak in either Band. For source $b$, the polarization peak is just to the north of the Stokes I peak at both Bands. For source $c$, the polarization peak is to the north of the Stokes I peak in Band 4 but to the south of the Stokes I peak in Band 7. These offsets are similar to what has been seen in other Class 0 sources such as VLA 1623 (cite: Harris2018) whereas older sources such as HL Tau or IM Lup do not have clear offsets (cite: Stephens2023; Hull2018). This is likely due to scattering polarization from disks with large scale-heights having more polarization on the near side compared to the far-side (cite: Yang2017), and the older disks are more settled. Indeed, recent observations of Class 0/I disks suggest that their dust is less settled than Class II disks (cite: Lin2023; Villenave2023). However, in the case of L1448 IRS3B, it is unclear if these peak polarization offsets are due to scale-heights or some other mechanism

In any case, the polarization observed in L1448 IRS3B is different than what is observed in other sources, either single disks or circumbinary disks. Morphologically, there are three notable features in the polarization seen in Figures [3](#LPI) and [4](#BothPol). The most striking is that the polarized emission generally follows along the spiral structures (best seen in Figure [4](#BothPol)). Second, around source $c$, the polarization angles wrap in an azimuthal pattern with clear nulls seen at the higher resolution of Band 7, but on the other hand, directly at source $c$ (and also the ring surrounding source $a$) there are uniformly aligned polarization angles, particularly seen in the higher resolution Band 7 observations. Finally, around the edges of the disk, the polarization has a much higher percent polarization (i.e., $P/I$) and is aligned similarly on both sides and at both wavelengths, although more pronounced in Band 4. We will investigate various polarization mechanisms below to better explain the observations.

![](L1448_Vector_IRS3B.pdf)

## Other Sources in the Field

In addition to L1448 IRS3B, there were other sources in the field. In Appendix A we show the maps for these sources: L1448 IRS3A, L1448 IRS3C (L1448 NW), and an unknown point source in Band 4 that is likely a background galaxy.

# Discussion

As discussed in §[1](#sec:intro) above, linear dust continuum polarization observations in circumstellar disks can arise from multiple mechanisms, but in most cases in circumstellar disks to date (and mostly in older Class II sources) dust polarization is likely dominated by scattering in the shorter ALMA wavelength Bands and likely some sort of mechanical alignment in the longer ALMA wavelength Bands (cite: Gold1952; Lazarian2007b; Kataoka2019; Mori2019; Mori2021; Hoang2022; Reissl2023; Stephens2023; Tang2023; Lin2024a; Harrison2024). However, this has not been generally true for circumbinary disks, which have been posited to have polarization due to magnetic fields in several cases (cite: Alves2018; Sadavoy2018; Harris2018; Tang2023). Indeed, with the diversity of morphology in L1448 IRS3B, we should investigate the various polarization mechanisms more closely.

First of all, we place constraints on the optical depth of the dust emission, as this can play an important role in which type of polarization mechanism dominates (cite: Yang2017; Mori2019; Hoang2022; Lin2022; Lin2024a). With two wavelengths, one typically measures the spectral index ($\alpha$) to assess the optical depth of emission structures, which typically assumes optical thin emission, an incorrect assumption when observing deeply embedded protostars. However, the estimate of $\alpha$ can be even more complicated with interferometric observations of deeply embedded protostars with bright envelopes as more than beam matching is required, again for the same reasons as the brightness temperature map has systemic issues in §[3.1](#IRS3B Results), more sensitivity of the Band 4 map to larger scale structure due to different *u,v* sampling.

We attempted to mitigate the difference in *u,v* sampling with various techniques beyond simple image smoothing to match beams, which will increase surface brightness sensitivity but not add sensitivity to structures that are not represented in the image. For example, we tried using other techniques such as (1) the *mtmfs* option in tclean and (2) restricting the *u,v* range to where the two datasets had the most overlapping data, between 50 and 1000 k$\lambda$ coupled with a *u,v* taper that resulted in beams whose areas were within a few percent of each other. However, in both cases, the Band 4 observations were more sensitive to the envelope, which make the spiral arm structures brighter (as they are on a plateau of emission). The bright compact sources are less affected as the envelope plateau is a smaller contamination to the total intensity. The bright compact emission had lower-limit spectral indices of $\alpha$ = 2 with the spiral arms being 1.5. A spectral index less than 2 requires high optical depth and scattering. However, due to the contamination, these are only lower limits to the spectral index. In addition, the lower brightness temperature of the spiral arms in Figure [2](#TB) also may suggest lower optical depth in the spiral arms as we are seeing deeper into the disk. In any case, to do better than these lower spectral index limits would require different observations or detailed radiative transfer modeling of a complex source, both of which are outside of the scope for this paper.

With only weak constraints on the spectral index, we have very little knowledge of the optical depth in the source, which will make it more difficult to determine the polarization mechanisms. Nonetheless, below we compare the different mechanisms and assess their contribution to the polarization seen in Figures [3](#LPI) and [4](#BothPol).

## Magnetic Field Alignment

Magnetic fields are the most common mechanism evoked for elongated dust grain alignment in astrophysics using mainly magnetic radiative alignment torques to align the dust grains perpendicularly to the field (cite: Andersson2015; Hoang2016). In general, the magnetic field is commonly thought to be responsible for the polarization seen in the inner envelope of embedded protostars (cite: Hull2013; Hull2014; Hull2017; Cox2018; Galametz2018; Sadavoy2018; Maury2018; LeGouellec2019; LeGouellec2020; Hull2020; Huang2024; Encalada2024) but not yet clearly in a Class 0 disk (outside of multiple systems), although there is a possible detection in a Class I disk (cite: Aso2021). Even in the rare disk cases, other mechanism explanations and more complex models have not been exhaustively attempted.

Previously, the highest resolution polarization observations of the inner envelope of L1448 IRS3B, which had a fractional polarization of 2.7% (cite: Galametz2018), were argued to be due to magnetic field alignment. In that case, the field has a direction that is approximately perpendicular to the east-west outflow (cite: Galametz2018) that mostly originates from source $c$ (cite: Nick2021).

As already mentioned, our observations at higher resolution show a much more complicated morphology than the previous polarization observations. Nonetheless, the outer disk region polarization in Figure [3](#LPI) (i.e. around the edges in the Band 4 maps) is in general consistent with the inner envelope polarization angles from (cite: Galametz2018) (-67$^\circ$). The percent polarization for the inner envelope polarization is higher than the low resolution observations, at 8% in Band 4 and Band 7, even higher at the edges of Band 4. The reason for the high polarization fraction is, as discussed above, likely due to the partially resolved out Stokes I envelope, especially in Band 4 (compare the two images of Figure [3](#LPI)), although an intrinsically higher polarization fraction in the inner envelope than in the disk is also possible (indeed expected to some extent), as indicated by, e.g., the ALMA dust polarization survey of Perseus and Orion protostellar systems (cite: Cox2018; Huang2024).

In Figure [5](#Regions), we highlight different regions of polarization. Those highlighted in a tan color are those we posit are generally consistent with the low-resolution observations, coming from the inner envelope and likely due to magnetic field dust grain alignment. The region was chosen using a combination of polarization fraction and location (off the circum-multiple disk). There are regions to the north and south that are ambiguous in both Bands so they were not included in the posited region. In addition, there are regions in the circum-multiple disk, particularly to the southwest of source $c$ (i.e., bottom middle of Figure [5](#Regions)), that are generally comparable to the low resolution angles so may also be associated with the magnetically aligned dust grains.

The significant difference between the lower resolution observed morphology and the higher resolution observation morphology is that the outer region (around the circum-multiple disk) polarization generally trends radially toward the the system center. This is best seen in Band 4 in Figures [3](#LPI) and [4](#BothPol) (left) in the upper left of the Figures. It is important to note that magnetic field alignment results in polarization that is rotated by 90$^\circ$ to the magnetic field of the plane of the sky, which in this case would suggest a somewhat toroidal field morphology (i.e. the polarization direction is for the most part radially oriented). To show this possible field orientation, we also display Figure [5](#Regions) with the polarization angle rotated by 90$^\circ$ for the possible inferred magnetic field in the plane of the sky in the Appendix (Figure [16](#RegionsRotated)).

A combination of toroidal and poloidal fields are commonly evoked in simulations of disks (cite: Balbus1991) while observationally toroidal fields are typically consistent with the observations at the inner envelope scale (cite: Kwon2019). We posit that these highlighted observations also may be generally consistent with a predominantly toroidal field in the inner envelope, although there are many vectors that are not in agreement with a pure toroidal field.

Inside of the regions with high polarization fraction in Figure [3](#LPI), the polarization morphology in many cases switches dramatically, frequently with $\sim$90$^\circ$ rotation, and the mean polarization fraction drops to 1.2$\pm$0.6% and 2.4$\pm$1.1% in Band 4 and Band 7, respectively. In addition, there is an azimuthal morphology around source $c$ and a general alignment of the polarization with the spiral arms, specifically seen in Figure [4](#BothPol) (left). In both of those cases, it would be difficult to suggest that the polarization is due to magnetic field alignment as the implied magnetic field direction would be radial around source $c$ and perpendicular to the spiral arm structures, both of which are not expected field morphologies since the magnetic field is expected to be wrapped by differential rotation into a predominantly toroidal configuration around source $c$ and an orientation approximately parallel to the spirals.

![](Compare_Vectors_Regions.pdf)

If the dust grain sizes are comparable to the observing wavelength, it has been shown that the polarization could be along the minor axis of the dust grains, perpendicular to the often adopted orientation (cite: Kirchschlager2019). For the multi-wavelength polarization observations toward BHB\[2007\]-11 (cite: Alves2018), (cite: Guillet2020) used this polarization flip as a possible explanation for the observations using a dust model with 1 mm dust grains in a log normal distribution and suggested that the actual magnetic field may be dominated by a toroidal field instead of poloidal, assuming the grains are aligned by magnetic fields. The inner region of the L1448 IRS3B circum-multiple disk has similar spiral structures with polarization aligned along them; if large dust grains exist in the disk and there are magnetic fields along the spirals, then it is possible to match the observed polarization morphology using a similar model. However, the polarization in the Guillet et al. (2020) model also predicts that the Band 4 polarization fraction is larger than Band 7 (see their Figure 1) which, while consistent with the data for BHB\[2007\]-11, is inconsistent for L1448 IRS3B. The Guillet et al. (2020) model used a very specific dust size distribution, grain aspect ratio, and angle between the grains’ minor axis and the line-of-sight for the BHB\[2007\]-11 fit, so more modeling is needed to draw firm conclusions. However, as the existence of large dust grains (i.e., $\sim$1 mm) in the circum-multiple disk of L1448 IRS3B is unclear and as the Band 4 polarization fraction is smaller than Band 7, we posit that the magnetic alignment of dust grains in the spiral structures is less favorable than mechanical alignment (see discussion below).

##  Polarization from Self-Scattering

When dust grains are comparable to the observing wavelength, the dust grains can self-scatter their thermal emission creating a linear polarization continuum on the order of 1% (cite: Kataoka2015). The scattering polarization mechanism results in a distinctive polarization angle morphology in an inclined disk with the polarization direction being parallel to the disk minor axis (cite: Kataoka2016; Yang2016). This morphology is typically seen in disks in the shorter wavelength ALMA Bands, especially Band 7 (cite: Stephens2014; Segura-Cox2015; Hull2018; Bacciotti2018; Dent2019; Harrison2024).

However, when disks are observed at longer wavelengths (e.g., ALMA Band 3), the polarization mechanism is often, but not always, dominated by another mechanism that changes the observed polarization morphology, likely due to a decrease in optical depth, which reduces the contribution from self-scattering and allows the polarized emission from other mechanisms to dominate without being excessively extincted (cite: Kataoka2017; Harris2018; Mori2019; Mori2021; Lin2022).

Although, this shift in polarization morphology is commonly observed in disks, there are also sources where the polarization morphology is consistent with scattering at all ALMA Bands (cite: Harrison2019). On the other hand, polarization due to dust self-scattering is highly dependent on the maximum dust grain size, falling quickly with increasing wavelength (cite: Kataoka2015). In fact, to match the polarization observations of MWC 480 and RY Tau, (cite: Harrison2024) require either high optical depth or, in the case of MWC 480, segregation of a large grain distribution (near the midplane) and small grain distribution (above and below the midplane).

In the case of L1448 IRS3B, the overall circum-multiple disk does not generally exhibit a polarization direction that matches a scattering morphology since the majority of the polarization vectors are not aligned with the minor axis of the circum-multiple disk nor is the polarization direction uniform. However, there are two regions in the circum-multiple disk that broadly match the polarization morphology aligned with a minor axis for scattering dominated polarization: around source $c$ and the disk/ring of the central source, called source $d$ in (cite: Reynolds2023), see Figure [5](#Regions), cyan. These two regions do have polarization that is generally aligned with the circum-multiple disk minor axis.

In (cite: Reynolds2023) at higher resolution, they fit source $c$ with a Gaussian in the *u,v* plane and find an extended source of 0.2$''$ $\times$ 0.175$''$ with a PA of 25$^\circ$. The average dust polarization direction in Band 7 of the region around source $c$, highlighted in Figure [5](#Regions), has an angle of 126$^\circ$, which is comparable to being along the minor axis of the compact source $c$ emission. This type of polarization morphology shift to scattering-like dominant on the smaller scale is consistent with other sources, such as VLA 1623 (cite: Harris2018; Sadavoy2018) and many Perseus protostars (cite: Cox2018).

Similarly, in (cite: Reynolds2023) they note a dust ring around source $d$ with an estimated PA of 45$^\circ$ PA. The average dust polarization direction in Band 7 of the region around source $a$, highlighted in Figure [5](#Regions), has an angle of 220$^\circ$, which is comparable to being along the minor axis of the ring emission. Note that the region highlighted is centered on source $a$ and not source $d$. The polarization emission around source $c$ is much higher than the polarization emission around source $a$ (see Figure [3](#LPI)), which may suggest differences in dust grain sizes that might be expected if the source $c$ structure formed recently from more evolved dust through fragmentation of a gravitational unstable circum-multiple disk (cite: Reynolds2023).

## Radiative Alignment

When dust grains spin with a precession rate from radiative torques that is faster than the Larmor precession rate around the magnetic field then the dust grains can align with an anisotropic radiation field (cite: Lazarian2007; Tazaki2017). For dust in disks, this means that the dust grains have their long axis aligned perpendicular to the local radiation flux, i.e. the direction of the local radiation anisotropy, which results in an azimuthal polarization pattern. At first glance, this mechanism was thought to explain the polarization morphology detected in circumstellar disks at the longer wavelength ALMA Bands, but this is likely incorrect. Radiation alignment polarization produces a circular polarization morphology at all disk inclinations and not the elliptical morphology that is detected (cite: Yang2019).

The morphology of radiative dust alignment is not a good match for the L1448 IRS3B polarization. Although the radiation field is much more complicated than a single system, the large scale polarization curvature that one sees along the spiral arm structures is not circular from any collection of radiation sources. On smaller scales, the most noticeable circular or elliptical polarization morphology is the polarization surrounding source $c$, away from the central region. However, that polarization morphology is not circular (as expected for radiative dust alignment) either; it is very elongated or elliptical, which is inconsistent with radiative dust alignment. In other words, we do not see strong evidence of radiative dust alignment in L1448 IRS3B.

## Mechanical Alignment

As discussed above, azimuthally aligned effectively prolate grains are needed to explain the longer ALMA Band polarization morphology observations around most circumstellar disks (cite: Kataoka2017; Yang2019; Mori2019; Harrison2019; Ohashi2023; Lin2022). In HL Tau, for example, most wavelength observations require a mixture of azimuthally aligned, prolate dust grains with self-scattering (cite: Lin2024a). The mechanism that is aligning the dust grains is still not known, but it is thought to be similar to the Gold mechanism (cite: Gold1952), where dust grains are aligned mechanically by the relative difference in the gas and dust motion, but without the requirement for supersonic relative velocities. The current best models for this are the v-MET and Badminton Birdie alignment mechanisms (cite: Lazarian2007; Hoang2016; Hoang2018; Lin2024b). In any case, without knowing the details of the physical process, studies have suggested that such alignment, along with dust scattering, can explain the multi-wavelength polarization observations toward HL Tau (cite: Lin2024a), as well as the high-resolution HL Tau observations with resolved rings and gaps at Band 7 (cite: Stephens2023). In the latter example, the models specifically require effectively prolate dust grains.

In the case of L1448 IRS3B, the dust is not generally aligned azimuthally as found in single sources like HL Tau, likely due to multiple sources and the complicated spiral arm structure of the circumbinary disk. Nonetheless, polarization in both Bands demonstrate smaller-scale azimuthal morphology around source $c$ and, more remarkably, show an overall alignment with the spiral arm structures.

Around the vicinity of source $c$, the polarization morphology at Bands 4 and 7 broadly resembles the azimuthal morphological transition of HL Tau. As mentioned earlier, near the source center (cyan region in Figure [5](#Regions)), the polarization at both Band 4 and 7 appears parallel to the disk minor axis with the shorter wavelength exhibiting a larger polarization fraction, which is consistent with scattering. However, near the outskirts of source $c$ (within 2 beams outside of the cyan region in Figure [5](#Regions)), the polarization morphology changes and becomes azimuthally oriented for Band 7. For Band 4, only the southeast portion appears consistent with azimuthally oriented polarization. Nonetheless, both bands show two polarization holes that are almost along the disk minor axis, see the Figure [4](#BothPol) colormap around source $c$, at slightly different locations between Band 4 and 7. The change of these features from the shorter to the longer wavelength, and from near the protostar to farther away, may be explained by decreasing the optical depth of scattering of azimuthally aligned, prolate grains (cite: Lin2022; Lin2024a) and a difference in the beam resolution. A drop in polarization from Band 7 to Band 3 or 4 at the center of the disk was also observed in HL Tau (cite: Stephens2017; Lin2024a).

A notable difference between the polarization from source $c$ and HL Tau is in the orientation of the polarization holes. For perfectly azimuthally aligned prolate grains, the polarization holes should be along the circumstellar disk minor axis where the scattering polarization cancels out the thermal polarization from prolate grains whose long axes are parallel to the circumstellar disk major axis.

However, the polarization holes around source $c$ in Band 7 (Figure [3](#LPI)) appear rotated by $\sim 20^{\circ}$ east-of-north. Such a rotation can be explained by the scattering of prolate grains aligned azimuthally but with an inward spiral toward the center ((cite: Lin2022); see their Figure 16), surrounding the source $c$ disk. Based on this rotated direction, we can infer that the alignment direction of the prolate grains should be clockwise and inward towards source $c$. The direction coincides with the direction of rotation of the main disk (cite: Nick2021). The observed polarization morphology inspiral behavior around the disk of source $c$ is consistent with polarization morphological spirals from two other sources, AS 209 and GG Tau (cite: Mori2019; Tang2023). Following the arguments from those two sources, the inspiral polarization could trace the inward accretion flow onto the central source if the alignment mechanism is the same for all three targets.

As discussed above, the polarization near the vicinity of source $c$ has an azimuthal morphology that is similar to the observations of an isolated source like HL Tau. From that similarity, we suspect that the underlying alignment mechanism must be dominated by some physical property or condition near source $c$, which includes the possibility of a Keplerian flow with accretion, as is suggested in HL Tau (cite: Lin2024a). However, the northwest portion of the disk from source $c$, in both Bands but particularly clear in Band 4, does not resemble the curvature expected from azimuthally aligned prolate grains. Given that the polarization angles curve toward sources $a$ and $b$, the alignment direction could be “disturbed” by influences beyond source $c$. This may be consistent with the fact that source $c$ is not as massive compared to sources $a$ and $b$ (cite: Nick2021).

Beyond the vicinity of source $c$, the most remarkable aspect of the observations is that the polarization patterns closely align with the spiral arm structures. The polarization directions at both wavelengths are similar and are generally aligned with the Stokes I arc (Figure [4](#BothPol)). This is suggestive that the underlying alignment mechanism may be dominated by the motion of the flows and disk material. Using the Stokes I continuum, we can create a simple model to compare the spiral arms with the polarization to make a more direct comparison.

### Simple Model of Polarization Morphology

Under the assumption that the spiral arms are creating a drift velocity of the dust relative to the gas (and traced by the dust continuum), we can make a simple model of the polarization morphology just using the spine of the continuum spiral structure. The polarization may be due to v-MET (cite: Lazarian2007), Badminton Birdie alignment (cite: Lin2024b), or another, yet unknown, alignment mechanism. To compare the polarization direction with the spiral structures, we need to define the spiral structure more quantitatively.

We use a simple mask to define the spiral structures in the Stokes I maps, then fit cubic splines to the emission using `UnivariateSpline` in `SciPy` with a smoothing factor = 5. Using Band 7, we show the results of this fit in 4 segments in Figure [6](#splinefits). The 4 segments are required due to the `UnivariateSpline` constraint of monotonically increasing input values. Band 4 gives a similar result, but we use Band 7 since the higher resolution provides a more accurate fit to the substructure (see Figure [1](#stokesI)).

![](L1448.BAND7.ModelSpine.pdf)

For every pixel in the Stokes I map, we use the nearest fitted spline pixel to calculate that pixel’s polarization vector, which is essentially the arctangent of the instantaneous slope of the spline fit. The slopes are obtained via the `UnivariateSpline` computed derivative attribute. The results for Band 7 are shown in Figure [7](#modelvectors). The vectors of the model are very similar to the observations without shading in Figure [5](#Regions).

![](L1448.Model.Vectors.pdf)

We can further quantify the comparison by taking the difference between the model in Figure [7](#modelvectors) with the observations for Band 7. Figure [8](#ModelDiffMap) shows the difference angle for all pixels and Figure [9](#ModelHisto) the histogram of those differences. In Figure [9](#ModelHisto), the standard deviation of the distribution is 18.5$^\circ$ with the distribution centered around 0$^\circ$, both of which are good for such a simple model. Thus, in both Bands, this simple model can broadly describe the observations, which implies that the polarization mechanism could be a gas-flow alignment of the dust grains.

![](L1448.BAND7.ModelDiff.pdf)

![](L1448.hist.pdf)

We measure the mean fractional polarization along the spiral arms (one measurement per beam along the feature shown in Figure [6](#splinefits)), 1.5$\pm$0.7% and 2.5$\pm$1.3%, for Band 4 and Band 7, respectively, which are consistent with the values in the inner region overall. This again suggests that using the model of (cite: Guillet2020), discussed above, would not be appropriate for this source.

### Model Implications

This polarization alignment with the dust continuum spiral structure in L1448 IRS3B has not been shown before. If the dust grain alignment mechanism traces the gas flow, the polarization suggests a possible flow along the spiral arm. The inward spiral angle of the polarization is in the same direction as the spiral angle from polarization in the vicinity of source $c$ which hints at a common alignment mechanism, likely of mechanical origin, at least in these two regions. While the kinematic motion traced in C$^{17}$O (at only a slightly lower angular resolution of 0.2$''$) is largely Keplerian without any clear deviations (cite: Nick2021), the C$^{17}$O emission is possibly not tracing the dense spiral structures. Further investigation into the system kinematics is warranted. Simulations of spiral structure in a gravitational unstable disk, such as L1448 IRS3B (cite: Nick2021), show that once the dust drifts into the spiral arms, the dust will move along the spiral arms (cite: Rowther2024), which may explain the observations. In other words, if there are spiral arms in the gas, the dust should drift to the pressure maxima, then once trapped at the pressure bump, the dust will move along the spiral arms. If the dust polarization is tracing the dust drift, such observations may provide a direct probe of the kinematics on small scales that may be difficult to trace with molecular tracers.

The polarization fraction in the main disk is between 1% to $2\%$, which is similar to HL Tau at ALMA wavelengths and at low resolution (cite: Stephens2017; Lin2024a). However, high-resolution Band 7 and long wavelength (VLA Q-Band at $\lambda=7.1$ mm) observations of HL Tau suggest an intrinsic polarization of $\sim$10% (cite: Lin2024a). The lower level of polarization at the lower resolution in the mechanically aligned dust grains is thought to be due to beam averaging of optically thick substructure that lowers the inferred intrinsic polarization.

With the current observation of L1448 IRS3B, it is unclear if the percent-level polarization is also due to a similar resolution effect or an actual lower level of intrinsic polarization. The latter scenario is particularly interesting since the decreased polarization can be due to less elongated grains or poorer alignment efficiency, which may be reasonable given the highly dynamic conditions in a multiple stellar system compared to an isolated system.

As mentioned previously, there appears to be a sharp transition from the outer region with high polarization to the disk region with lower polarization and a dramatic switch in polarization angle (Figure [5](#Regions)). The transition appears to coincide where the Stokes $I$ increases as part of the main disk. We suspect that the switch in polarization is because the density rapidly increases, which prevents alignment with the magnetic field but benefits mechanical alignment. Alignment with the magnetic field (determined by the Larmor precession timescale) needs to occur faster than the gaseous damping timescale (cite: Tazaki2017) and the high-density conditions in disks easily shorten the gas damping time (cite: Lam2021). This implies that mechanical alignment, which relies on gas bombardment to provide alignment, should be more efficient in higher-density regions.

# Conclusions

We present ALMA dust continuum linear polarization observations of the proto-multiple source L1448 IRS3B in Band 4 and Band 7, $\lambda$ = 2.1 mm and 873 $\mu$m, respectively. We detect the polarization in the inner envelope, circum-multiple disk, spiral structures, and compact structures around individual stellar components. The circum-multiple circumstellar disk is clearly complex and provides important clues into the formation of young, close multiple protostellar systems. With polarization observations, we open a new window into the physics of multiple protostellar formation. In particular, it is surprising to find a source with multiple polarization mechanisms (as suggested by the polarization morphology), so exploring this source, and others like it, provide a unique view of star formation. The main conclusions from these observations are:

- The dust continuum is consistent with previous observations of the circum-multiple disk, the spiral structures and the compact sources (cite: John2016; Nick2021; Reynolds2023). This is the first time that the spiral structures have been resolved in Band 4.

- The brightness temperatures of the dust in the two wavelength bands are very consistent with slightly higher temperatures for Band 7, indicating that Band 7 is less optically thin than Band 4. The estimation of optical depth is hampered by differences in the *u,v* sampling.

- The linear dust polarization morphology is consistent with each other across both Bands. In single circumstellar disk systems, the polarization often changes morphology across the ALMA Bands, but in this source the morphology does not present much deviation in polarization angle. Although this is seen in a few single sources (cite: Harrison2024) and binary sources (cite: Alves2018), it is suggestive of a single type of dominating polarization in each region with a weak optical depth dependence for most of the polarized emission.

- On the other hand, the linear dust polarization morphology is different in the different structures of L1448 IRS3B. In the inner protostellar envelope, the observations are possibly due to dust grains aligned by magnetic fields, which could be due to a generally toroidal field surrounding the circum-multiple disk. Around source $a$ and $c$, the observations are possibly due to polarization from dust self-scattering, which suggest high optical depth. Along the spiral arms, the observations are possibly due to polarization arising from mechanical alignment of the dust grains due to the relative difference in the velocities of the gas and dust. In the last case, this would suggest that the local dust drift velocity field is along the spiral structures.

- L1448 IRS3B is one of the few sources with more than 2 polarization mechanisms occurring at the same time, making it an ideal testbed for modeling, although the complication of the triple or quadruple system makes this very challenging. In addition, the possible detection of mechanical alignment with the gas flows along the spiral structures offers a unique probe of the relative gas and dust flows in these young multiple systems that needs to be better understood.

- Finally, polarization is also detected toward L1448 IRS3A and L1448 IRS3C (L1448 NW), and a point source is detected in Band 4 that is likely a background galaxy.

L.W.L. acknowledges support from NSF AST-1910364 and NSF AST-2307844. Z.-Y.D.L. acknowledges support from NASA 80NSSC18K1095, the Jefferson Scholars Foundation, the NRAO ALMA Student Observing Support (SOS) SOSPA8-003, the Achievements Rewards for College Scientists (ARCS) Foundation Washington Chapter, the Virginia Space Grant Consortium (VSGC), and UVA research computing (RIVANNA). Z.-Y.L. is supported in part by NASA 80NSSC20K0533, NSF AST-2307199, and the Virginia Institute of Theoretical Astronomy. W.K. was supported by the National Research Foundation of Korea (NRF) grant funded by the Korea government (MSIT) (RS-2024-00342488). We thank Eli Sofovich for early data analysis.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00276.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

The final maps and the scripts used to make them (as well as the selfcal script) are available in the Illinois Data Bank (cite: illinoisdatabankIDB-5442905). The ALMA data and reduction scripts are available from the ALMA archive.

# Facilities

ALMA

# Software

astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A; Astropy2022) and SciPy (cite: SciPy).

# Other sources in the Field

Figure [10](#stokesI_IRS3A) presents the L1448 IRS3A dust continuum (Stokes I) at the two wavelengths. L1448 IRS3A is a likely Class I source that is $\sim$7$''$ to the northeast of L1448 IRS3B (cite: Looney2000; Pokhrel2023; Reynolds2023). It is a wide-binary with a clear dust disk well detected that is consistent with the disk detected in (cite: Nick2021) and further resolved into a ring and a compact source in (cite: Reynolds2023) that suggests a disk with a large gap.

Furthermore, Figure [11](#stokesI_IRS3-lowres) is a zoom out of the emission, showing both L1448 IRS3A and IRS3B in Band 4 only (since it has a larger spatial scale sensitivity). We used Robust weighting of 1.0 as a compromise between sensitivity and larger spatial scale sensitivity. IRS3A has clear spiral arms at the edges of the disk (cite: Gieser2024) with IRS3B having hints of spiral structure, suggesting an interaction as part of a bridge of material linking IRS3A and IRS3B (cite: Gieser2024).

Figure [12](#LPI_A) presents the polarization and polarization angle of the L1448 IRS3A dust continuum at Band 4 and Band 7. The polarization is detected in an area equal to a few beams in each case, but unlike L1448 IRS3B, the morphology in the two Bands are different. Band 4 has a polarization hole toward the center with a hint of azimuthal polarization morphology, which may be consistent with mechanical alignment, but the data are not clear. Band 7, on the other hand, has a peak polarization at the center and a polarization morphology that is aligned with the major axis. This is not consistent with polarization due to scattering. If the polarization is due to magnetic field alignment, it would suggest a poloidal magnetic field that is parallel to the minor axis.

Figure [13](#stokesI_IRS3C) presents the dust emission from the Class 0 source L1448 IRS3C (cite: Looney2000; Pokhrel2023), which is 17$\ensuremath{''}$ to the northwest from IRS3B. The source is also often called L1448 NW (cite: Terebey1997). L1448 IRS3C is a Class 0 close binary system with a separation of $\sim$0.25$''$ (cite: Reynolds2023; Pokhrel2023). The two disks are nearly north-south. The structure seen in Figure [13](#stokesI_IRS3C) is either a flattened envelope or a circumbinary disk embedded in a flattened filamentary structure.

Figure [14](#LPI_C) presents the polarization intensity and polarization angle of IRS3C. The polarization is not consistent with scattering, which is common for either envelopes or circumbinary disks. The polarization angle is aligned with the flattened envelope structure, which if due to magnetic field dust alignment, would suggest a poloidal magnetic field that is parallel to the minor axis. However, it is important to note that the polarization detected here is outside of the ALMA 1/3 primary beam (actually just outside the 1/2 power point), making the detection less conclusive.

Finally, Figure [15](#stokesI_newsource) presents a 6-$\sigma$ continuum point source detection in Band 4 toward the north of the field of view (17.5$''$ away from IRS3B) that we label L1448 IRS3-ALMA. L1448 IRS3-ALMA is undetected in the Perseus VANDAM survey of (cite: Tobin2016) in the VLA Ka Band ($\lambda$ = 8 mm and 1 cm) with RMS values of 0.012 and 0.01 mJy/beam, respectively. In our Band 4 observations, the total flux is 221 $\pm$25 $\mu$Jy/beam (primary beam corrected), which means the emission is falling, consistent with dust emission. L1448 IRS3-ALMA is also not detected in the VANDAM ALMA Band 6 observations ($\lambda$ = 1.3 mm) from (cite: Tobin2018) with an RMS of 0.33 mJy/beam (since the source is near the half-power point in their observations), which implies a spectral index, $\alpha <$ 3.2, which is also consistent with dust emission. We could not find any source known at the L1448 IRS3-ALMA position; it is most likely a background dusty galaxy.

![](L1448_I_IRS3A.pdf)

![](L1448_I_IRS3-lowres.pdf)

![](L1448_Vector_IRS3A.pdf)

![](L1448_I_IRS3C_cor.pdf)

![](L1448_Vector_IRS3C_cor.pdf)

# IRS3B Polarization Rotated by 90$^\circ$

In addition to the polarization angle observations of Figure [5](#Regions), we also show the same overlay of both Band 4 and 7, at the same resolution, with their polarization angles rotated by 90$^\circ$ in Figure [16](#RegionsRotated). This provides a plane of the sky inferred magnetic field for polarization due to magnetic field alignment. We posit that the tan region is likely dominated by magnetic field dust grain alignment, which would infer a magnetic field in the plane of the sky to have a more toroidal morphology.

![](Compare_Vectors_Regions_rotated.pdf)

natexlab

(ref: Alves2018) Alves, F. O., Girart, J. M., Padovani, M., et al. 2018, A&A, 616, A56, doi: [`10.1051/0004-6361/201832935`](http://doi.org/10.1051/0004-6361/201832935)

(ref: Andersson2015) Andersson, B. G., Lazarian, A., & Vaillancourt, J. E. 2015, ARA&A, 53, 501, doi: [`10.1146/annurev-astro-082214-122414`](http://doi.org/10.1146/annurev-astro-082214-122414)

(ref: Aso2021) Aso, Y., Kwon, W., Hirano, N., et al. 2021, ApJ, 920, 71, doi: [`10.3847/1538-4357/ac15f3`](http://doi.org/10.3847/1538-4357/ac15f3)

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Astropy2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Bacciotti2018) Bacciotti, F., Girart, J. M., Padovani, M., et al. 2018, ApJL, 865, L12, doi: [`10.3847/2041-8213/aadf87`](http://doi.org/10.3847/2041-8213/aadf87)

(ref: Balbus1991) Balbus, S. A., & Hawley, J. F. 1991, ApJ, 376, 214, doi: [`10.1086/170270`](http://doi.org/10.1086/170270)

(ref: Briggs1995) Briggs, D. S. 1995, PhD thesis, New Mexico Institute of Mining and Technology

(ref: Carrasco-Gonzalez2019) Carrasco-González, C., Sierra, A., Flock, M., et al. 2019, ApJ, 883, 71, doi: [`10.3847/1538-4357/ab3d33`](http://doi.org/10.3847/1538-4357/ab3d33)

(ref: Cox2018) Cox, E. G., Harris, R. J., Looney, L. W., et al. 2018, ApJ, 855, 92, doi: [`10.3847/1538-4357/aaacd2`](http://doi.org/10.3847/1538-4357/aaacd2)

(ref: Dent2019) Dent, W. R. F., Pinte, C., Cortes, P. C., et al. 2019, MNRAS, 482, L29, doi: [`10.1093/mnrasl/sly181`](http://doi.org/10.1093/mnrasl/sly181)

(ref: Dolginov1976) Dolginov, A. Z., & Mitrofanov, I. G. 1976, Ap&SS, 43, 291, doi: [`10.1007/BF00640010`](http://doi.org/10.1007/BF00640010)

(ref: Draine1997) Draine, B. T., & Weingartner, J. C. 1997, ApJ, 480, 633, doi: [`10.1086/304008`](http://doi.org/10.1086/304008)

(ref: Dunham2015) Dunham, M. M., Allen, L. E., Evans, Neal J., I., et al. 2015, ApJS, 220, 11, doi: [`10.1088/0067-0049/220/1/11`](http://doi.org/10.1088/0067-0049/220/1/11)

(ref: Encalada2024) Encalada, F. J., Looney, L. W., Novak, G., et al. 2024, arXiv e-prints, arXiv:2405.08118, doi: [`10.48550/arXiv.2405.08118`](http://doi.org/10.48550/arXiv.2405.08118)

(ref: Enoch2009) Enoch, M. L., Evans, II, N. J., Sargent, A. I., & Glenn, J. 2009, ApJ, 692, 973, doi: [`10.1088/0004-637X/692/2/973`](http://doi.org/10.1088/0004-637X/692/2/973)

(ref: Galametz2018) Galametz, M., Maury, A., Girart, J. M., et al. 2018, A&A, 616, A139, doi: [`10.1051/0004-6361/201833004`](http://doi.org/10.1051/0004-6361/201833004)

(ref: Gieser2024) Gieser, C., Pineda, J. E., Segura-Cox, D. M., et al. 2024, A&A, 692, A55, doi: [`10.1051/0004-6361/202450653`](http://doi.org/10.1051/0004-6361/202450653)

(ref: Gold1952) Gold, T. 1952, Monthly Notices of the Royal Astronomical Society, 112, 215, doi: [`10.1093/mnras/112.2.215`](http://doi.org/10.1093/mnras/112.2.215)

(ref: Guillet2020) Guillet, V., Girart, J. M., Maury, A. J., & Alves, F. O. 2020, A&A, 634, L15, doi: [`10.1051/0004-6361/201937314`](http://doi.org/10.1051/0004-6361/201937314)

(ref: Harris2018) Harris, R. J., Cox, E. G., Looney, L. W., et al. 2018, ApJ, 861, 91, doi: [`10.3847/1538-4357/aac6ec`](http://doi.org/10.3847/1538-4357/aac6ec)

(ref: Harrison2024) Harrison, R. E., Lin, Z.-Y. D., Looney, L. W., et al. 2024, ApJ, 967, 40, doi: [`10.3847/1538-4357/ad39ec`](http://doi.org/10.3847/1538-4357/ad39ec)

(ref: Harrison2019) Harrison, R. E., Looney, L. W., Stephens, I. W., et al. 2019, ApJL, 877, L2, doi: [`10.3847/2041-8213/ab1e46`](http://doi.org/10.3847/2041-8213/ab1e46)

(ref: Hoang2018) Hoang, T., Cho, J., & Lazarian, A. 2018, ApJ, 852, 129, doi: [`10.3847/1538-4357/aa9edc`](http://doi.org/10.3847/1538-4357/aa9edc)

(ref: Hoang2016) Hoang, T., & Lazarian, A. 2016, ApJ, 831, 159, doi: [`10.3847/0004-637X/831/2/159`](http://doi.org/10.3847/0004-637X/831/2/159)

(ref: Hoang2022) Hoang, T., Tram, L. N., Minh Phan, V. H., et al. 2022, AJ, 164, 248, doi: [`10.3847/1538-3881/ac9af5`](http://doi.org/10.3847/1538-3881/ac9af5)

(ref: Huang2024) Huang, B., Girart, J. M., Stephens, I. W., et al. 2024, ApJL, 963, L31, doi: [`10.3847/2041-8213/ad27d4`](http://doi.org/10.3847/2041-8213/ad27d4)

(ref: Hull2020) Hull, C. L. H., Le Gouellec, V. J. M., Girart, J. M., Tobin, J. J., & Bourke, T. L. 2020, ApJ, 892, 152, doi: [`10.3847/1538-4357/ab5809`](http://doi.org/10.3847/1538-4357/ab5809)

(ref: Hull2015) Hull, C. L. H., & Plambeck, R. L. 2015, Journal of Astronomical Instrumentation, 4, 1550005, doi: [`10.1142/S2251171715500051`](http://doi.org/10.1142/S2251171715500051)

(ref: Hull2013) Hull, C. L. H., Plambeck, R. L., Bolatto, A. D., et al. 2013, ApJ, 768, 159, doi: [`10.1088/0004-637X/768/2/159`](http://doi.org/10.1088/0004-637X/768/2/159)

(ref: Hull2014) Hull, C. L. H., Plambeck, R. L., Kwon, W., et al. 2014, ApJS, 213, 13, doi: [`10.1088/0067-0049/213/1/13`](http://doi.org/10.1088/0067-0049/213/1/13)

(ref: Hull2017) Hull, C. L. H., Mocz, P., Burkhart, B., et al. 2017, ApJL, 842, L9, doi: [`10.3847/2041-8213/aa71b7`](http://doi.org/10.3847/2041-8213/aa71b7)

(ref: Hull2018) Hull, C. L. H., Yang, H., Li, Z.-Y., et al. 2018, ApJ, 860, 82, doi: [`10.3847/1538-4357/aabfeb`](http://doi.org/10.3847/1538-4357/aabfeb)

(ref: SciPy) Jones, E., Oliphant, T., Peterson, P., et al. 2001–, SciPy: Open source scientific tools for Python. <http://www.scipy.org/>

(ref: Kataoka2016) Kataoka, A., Muto, T., Momose, M., Tsukagoshi, T., & Dullemond, C. P. 2016, ApJ, 820, 54, doi: [`10.3847/0004-637X/820/1/54`](http://doi.org/10.3847/0004-637X/820/1/54)

(ref: Kataoka2019) Kataoka, A., Okuzumi, S., & Tazaki, R. 2019, ApJL, 874, L6, doi: [`10.3847/2041-8213/ab0c9a`](http://doi.org/10.3847/2041-8213/ab0c9a)

(ref: Kataoka2017) Kataoka, A., Tsukagoshi, T., Pohl, A., et al. 2017, ApJL, 844, L5, doi: [`10.3847/2041-8213/aa7e33`](http://doi.org/10.3847/2041-8213/aa7e33)

(ref: Kataoka2015) Kataoka, A., Muto, T., Momose, M., et al. 2015, ApJ, 809, 78, doi: [`10.1088/0004-637X/809/1/78`](http://doi.org/10.1088/0004-637X/809/1/78)

(ref: Kirchschlager2019) Kirchschlager, F., Bertrang, G. H. M., & Flock, M. 2019, MNRAS, 488, 1211, doi: [`10.1093/mnras/stz1763`](http://doi.org/10.1093/mnras/stz1763)

(ref: Kwon2006) Kwon, W., Looney, L. W., Crutcher, R. M., & Kirk, J. M. 2006, ApJ, 653, 1358, doi: [`10.1086/508920`](http://doi.org/10.1086/508920)

(ref: Kwon2011) Kwon, W., Looney, L. W., & Mundy, L. G. 2011, ApJ, 741, 3, doi: [`10.1088/0004-637X/741/1/3`](http://doi.org/10.1088/0004-637X/741/1/3)

(ref: Kwon2019) Kwon, W., Stephens, I. W., Tobin, J. J., et al. 2019, ApJ, 879, 25, doi: [`10.3847/1538-4357/ab24c8`](http://doi.org/10.3847/1538-4357/ab24c8)

(ref: Lam2021) Lam, K. H., Chen, C.-Y., Li, Z.-Y., et al. 2021, MNRAS, 507, 608, doi: [`10.1093/mnras/stab2105`](http://doi.org/10.1093/mnras/stab2105)

(ref: Lazarian2007) Lazarian, A., & Hoang, T. 2007a, ApJL, 669, L77, doi: [`10.1086/523849`](http://doi.org/10.1086/523849)

(ref: Lazarian2007b) —. 2007b, MNRAS, 378, 910, doi: [`10.1111/j.1365-2966.2007.11817.x`](http://doi.org/10.1111/j.1365-2966.2007.11817.x)

(ref: LeGouellec2019) Le Gouellec, V. J. M., Hull, C. L. H., Maury, A. J., et al. 2019, ApJ, 885, 106, doi: [`10.3847/1538-4357/ab43c2`](http://doi.org/10.3847/1538-4357/ab43c2)

(ref: LeGouellec2020) Le Gouellec, V. J. M., Maury, A. J., Guillet, V., et al. 2020, A&A, 644, A11, doi: [`10.1051/0004-6361/202038404`](http://doi.org/10.1051/0004-6361/202038404)

(ref: Lin2020) Lin, Z.-Y. D., Li, Z.-Y., Yang, H., et al. 2020, MNRAS, 496, 169, doi: [`10.1093/mnras/staa1499`](http://doi.org/10.1093/mnras/staa1499)

(ref: Lin2024b) —. 2024a, MNRAS, 534, 3713, doi: [`10.1093/mnras/stae2248`](http://doi.org/10.1093/mnras/stae2248)

(ref: Lin2022) —. 2022, MNRAS, 512, 3922, doi: [`10.1093/mnras/stac753`](http://doi.org/10.1093/mnras/stac753)

(ref: Lin2023) Lin, Z.-Y. D., Li, Z.-Y., Tobin, J. J., et al. 2023, ApJ, 951, 9, doi: [`10.3847/1538-4357/acd5c9`](http://doi.org/10.3847/1538-4357/acd5c9)

(ref: Lin2024a) Lin, Z.-Y. D., Li, Z.-Y., Stephens, I. W., et al. 2024b, MNRAS, 528, 843, doi: [`10.1093/mnras/stae040`](http://doi.org/10.1093/mnras/stae040)

(ref: illinoisdatabankIDB-5442905) Looney, L. 2025, Dust continuum ObservL1448 IRS3B: Dust Polarization Aligned with Spiral Features, Tracing Gas Flows, University of Illinois Urbana-Champaign. <https://doi.org/>

(ref: Looney2000) Looney, L. W., Mundy, L. G., & Welch, W. J. 2000, ApJ, 529, 477, doi: [`10.1086/308239`](http://doi.org/10.1086/308239)

(ref: Maury2022) Maury, A., Hennebelle, P., & Girart, J. M. 2022, Frontiers in Astronomy and Space Sciences, 9, 949223, doi: [`10.3389/fspas.2022.949223`](http://doi.org/10.3389/fspas.2022.949223)

(ref: Maury2018) Maury, A. J., Girart, J. M., Zhang, Q., et al. 2018, MNRAS, 477, 2760, doi: [`10.1093/mnras/sty574`](http://doi.org/10.1093/mnras/sty574)

(ref: Mori2021) Mori, T., & Kataoka, A. 2021, ApJ, 908, 153, doi: [`10.3847/1538-4357/abd08a`](http://doi.org/10.3847/1538-4357/abd08a)

(ref: Mori2019) Mori, T., Kataoka, A., Ohashi, S., et al. 2019, ApJ, 883, 16, doi: [`10.3847/1538-4357/ab3575`](http://doi.org/10.3847/1538-4357/ab3575)

(ref: Ohashi2025) Ohashi, S., Muto, T., Tsukamoto, Y., et al. 2025, Nat Astron, doi: [`10.1038/s41550-024-02454-x`](http://doi.org/10.1038/s41550-024-02454-x)

(ref: Ohashi2018) Ohashi, S., Kataoka, A., Nagai, H., et al. 2018, ApJ, 864, 81, doi: [`10.3847/1538-4357/aad632`](http://doi.org/10.3847/1538-4357/aad632)

(ref: Ohashi2023) Ohashi, S., Momose, M., Kataoka, A., et al. 2023, ApJ, 954, 110, doi: [`10.3847/1538-4357/ace9b9`](http://doi.org/10.3847/1538-4357/ace9b9)

(ref: Ortiz2018) Ortiz-León, G. N., Loinard, L., Dzib, S. A., et al. 2018, ApJ, 865, 73, doi: [`10.3847/1538-4357/aada49`](http://doi.org/10.3847/1538-4357/aada49)

(ref: Podio2021) Podio, L., Tabone, B., Codella, C., et al. 2021, A&A, 648, A45, doi: [`10.1051/0004-6361/202038429`](http://doi.org/10.1051/0004-6361/202038429)

(ref: Pokhrel2023) Pokhrel, R., Megeath, S. T., Gutermuth, R. A., et al. 2023, ApJS, 266, 32, doi: [`10.3847/1538-4365/acbfac`](http://doi.org/10.3847/1538-4365/acbfac)

(ref: Reissl2023) Reissl, S., Meehan, P., & Klessen, R. S. 2023, A&A, 674, A47, doi: [`10.1051/0004-6361/202142528`](http://doi.org/10.1051/0004-6361/202142528)

(ref: Nick2021) Reynolds, N. K., Tobin, J. J., Sheehan, P., et al. 2021, ApJL, 907, L10, doi: [`10.3847/2041-8213/abcc02`](http://doi.org/10.3847/2041-8213/abcc02)

(ref: Reynolds2023) Reynolds, N. K., Tobin, J. J., Sheehan, P. D., et al. 2024, ApJ, 963, 164, doi: [`10.3847/1538-4357/ad151d`](http://doi.org/10.3847/1538-4357/ad151d)

(ref: Rowther2024) Rowther, S., Nealon, R., Meru, F., et al. 2024, MNRAS, 528, 2490, doi: [`10.1093/mnras/stae167`](http://doi.org/10.1093/mnras/stae167)

(ref: Sadavoy2018) Sadavoy, S. I., Myers, P. C., Stephens, I. W., et al. 2018, ApJ, 859, 165, doi: [`10.3847/1538-4357/aac21a`](http://doi.org/10.3847/1538-4357/aac21a)

(ref: Segura-Cox2015) Segura-Cox, D. M., Looney, L. W., Stephens, I. W., et al. 2015, ApJL, 798, L2, doi: [`10.1088/2041-8205/798/1/L2`](http://doi.org/10.1088/2041-8205/798/1/L2)

(ref: Stephens2014) Stephens, I. W., Looney, L. W., Kwon, W., et al. 2014, Nature, 514, 597, doi: [`10.1038/nature13850`](http://doi.org/10.1038/nature13850)

(ref: Stephens2017) Stephens, I. W., Yang, H., Li, Z.-Y., et al. 2017, ApJ, 851, 55, doi: [`10.3847/1538-4357/aa998b`](http://doi.org/10.3847/1538-4357/aa998b)

(ref: Stephens2023) Stephens, I. W., Lin, Z.-Y. D., Fernández-López, M., et al. 2023, Nature, 623, 705, doi: [`10.1038/s41586-023-06648-7`](http://doi.org/10.1038/s41586-023-06648-7)

(ref: Tang2023) Tang, Y.-W., Dutrey, A., Koch, P. M., et al. 2023, ApJL, 947, L5, doi: [`10.3847/2041-8213/acc45b`](http://doi.org/10.3847/2041-8213/acc45b)

(ref: Tazaki2017) Tazaki, R., Lazarian, A., & Nomura, H. 2017, ApJ, 839, 56, doi: [`10.3847/1538-4357/839/1/56`](http://doi.org/10.3847/1538-4357/839/1/56)

(ref: casa2022) Team, T. C., Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacific, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Terebey1997) Terebey, S., & Padgett, D. L. 1997, in Herbig-Haro Flows and the Birth of Stars, ed. B. Reipurth & C. Bertout, Vol. 182, 507–514

(ref: John2016) Tobin, J. J., Kratter, K. M., Persson, M. V., et al. 2016a, Nature, 538, 483, doi: [`10.1038/nature20094`](http://doi.org/10.1038/nature20094)

(ref: Tobin2016) Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2016b, ApJ, 818, 73, doi: [`10.3847/0004-637X/818/1/73`](http://doi.org/10.3847/0004-637X/818/1/73)

(ref: Tobin2018) —. 2018, ApJ, 867, 43, doi: [`10.3847/1538-4357/aae1f7`](http://doi.org/10.3847/1538-4357/aae1f7)

(ref: Vaillancourt2006) Vaillancourt, J. E. 2006, PASP, 118, 1340, doi: [`10.1086/507472`](http://doi.org/10.1086/507472)

(ref: Villenave2023) Villenave, M., Podio, L., Duchêne, G., et al. 2023, ApJ, 946, 70, doi: [`10.3847/1538-4357/acb92e`](http://doi.org/10.3847/1538-4357/acb92e)

(ref: Wardle1974) Wardle, J. F. C., & Kronberg, P. P. 1974, ApJ, 194, 249, doi: [`10.1086/153240`](http://doi.org/10.1086/153240)

(ref: Yang2021) Yang, H. 2021, ApJ, 911, 125, doi: [`10.3847/1538-4357/abebde`](http://doi.org/10.3847/1538-4357/abebde)

(ref: Yang2016) Yang, H., Li, Z.-Y., Looney, L., & Stephens, I. 2016, MNRAS, 456, 2794, doi: [`10.1093/mnras/stv2633`](http://doi.org/10.1093/mnras/stv2633)

(ref: Yang2017) Yang, H., Li, Z.-Y., Looney, L. W., Girart, J. M., & Stephens, I. W. 2017, MNRAS, 472, 373, doi: [`10.1093/mnras/stx1951`](http://doi.org/10.1093/mnras/stx1951)

(ref: Yang2019) Yang, H., Li, Z.-Y., Stephens, I. W., Kataoka, A., & Looney, L. 2019, MNRAS, 483, 2371, doi: [`10.1093/mnras/sty3263`](http://doi.org/10.1093/mnras/sty3263)

(ref: Yen2024) Yen, H.-W., Williams, J. P., Sai, J., et al. 2024, ApJ, 969, 125, doi: [`10.3847/1538-4357/ad4c6b`](http://doi.org/10.3847/1538-4357/ad4c6b)

(ref: Zucker2019) Zucker, C., Speagle, J. S., Schlafly, E. F., et al. 2019, ApJ, 879, 125, doi: [`10.3847/1538-4357/ab2388`](http://doi.org/10.3847/1538-4357/ab2388)

[^1]: https://irsa.ipac.caltech.edu/data/Herschel/eHOPS\
    /ehops_perseus_seds_protostars.html

[^2]: https://github.com/jjtobin/auto_selfcal

</paper>

Write the methods card for this paper.