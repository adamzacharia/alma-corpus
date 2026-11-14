# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026ApJ..1004..194F\sonnetcc\reply.txt

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
 "bibcode": "2026ApJ..1004..194F",
 "title": "ALMA Observations of [O I] 145 μm and [N II] 205 μm Emission Lines from Star-forming Galaxies at z ∼ 7",
 "year": 2026,
 "journal": "The Astrophysical Journal",
 "first_author": "Fudamoto, Yoshinobu",
 "n_authors": 25,
 "arxiv_id": "2504.03831",
 "doi": "10.3847/1538-4357/ae5bad",
 "alma_projects_linked_by_archive": [
  "2021.1.00247.S",
  "2022.1.00446.S",
  "2022.1.00999.S",
  "2022.1.01384.S"
 ]
}
```

Paper text:
<paper>
# ALMA Observations of \[O i\] $145\,{\rm \mu m}$ and \[N ii\] $205\,{\rm \mu m}$ Emission lines from Star-Forming Galaxies at $z\sim7$

## Abstract

We present results of new observations of \[O i\] $145\,{\rm \mu m}$ and \[N ii\] $205\,{\rm \mu m}$ emission lines from four star-forming galaxies at redshifts between $z=6.58$ and $7.68$ that have previous detections of \[C ii\] $158\,{\rm \mu m}$ and dust continua. Using ALMA, we successfully detect \[O i\] $145\,{\rm \mu m}$ emission from all targets at $>4\,\sigma$ significance. However, \[N ii\] $205\,{\rm \mu m}$ emission is undetected in all galaxies (SNR $<3.5\,\sigma$) except for a tentative detection from A1689-zD1. From the observed high \[C ii\]/\[N ii\] emission line ratios ($\gtrsim20 - 80$), we find that most of the \[C ii\] $158\,{\rm \mu m}$ emission arise from neutral gas regions ($3\,\sigma$ lower limits of $\gtrsim 74 - 96\%$). From \[O i\] $145\,{\rm \mu m}$, \[C ii\] $158\,{\rm \mu m}$ lines, and infrared luminosities, we estimate the neutral gas densities of $n_{\rm H}=10^{3.5}$ - $10^6\,{\rm cm^{-3}}$ and the far-ultraviolet (FUV) radiation strengths of $G_0\sim10^{2.5}$-$10^{3}$. While the neutral gas densities are similar to those of high-redshift starburst galaxies, the FUV strengths are lower compared to both local and high-redshift starbursts. Finally, we estimate atomic hydrogen masses using \[O i\] $145\,{\rm \mu m}$ emission lines and the oxygen abundances measured from recent JWST observations. We find gas mass ratios of $f_{\rm gas}\sim0.3$ - $0.8$, which are similar to earlier studies using \[C ii\] $158\,{\rm \mu m}$. Starting from this pilot observation, future large \[O i\] $145\,{\rm \mu m}$ emission line surveys will provide us with currently little-known neutral gas properties of star-forming galaxies in the early Universe.

# Introduction

Studying how star-forming galaxies evolved in the epoch of reionization (EoR; e.g., at $z>6$) has crucial implications for our understanding of the cosmic reionization (cite: Dayal2018; Robertson2022) as well as for our understanding of the galaxy evolution in the later epochs (cite: Madau2014). Deep observations using the Hubble Space Telescope, the recent observations using the James Webb Space Telescope (JWST), and several ground-based optical/near-infrared (NIR) facilities have completely revolutionized our view of galaxy evolution in the high-redshift Universe through their extremely high sensitivity and high resolution in the rest-frame ultraviolet (UV) and/or optical wavelengths (cite: Bouwens2015; Oesch2018; Naidu2022; Oesch2023; Cameron2023; Finkelstein2023; Fujimoto2023; Harikane2023; Robertson2023; Rieke2023; Williams2023; Wang2024; Carniani2024). While these rest-frame UV/optical observations enabled access to the galaxies’ star-formation activities through the observations of ionized gas, the cold neutral and the molecular gas – the direct fuel for star formation activities – is challenging to probe in emission at the rest-frame UV/optical wavelengths. This is because cooling lines from the neutral gas emits most of its energy at far-infrared (FIR) wavelength range (however, see e.g., (cite: Heintz2023) for probing the neutral gas in absorption).

The unprecedented sensitivity and high spatial resolution of the Atacama Large Millimeter/submillimeter Array (ALMA) has largely improved studies of galaxy formation and evolution by enabling to probe dust continuum and emission lines in the far-infrared (FIR) wavelength from galaxies in the EoR (see (cite: Hodge2020) for a review). In particular, recent ALMA observations detected \[C ii\] $158\,{\rm \mu m}$ emission lines from a statistically significant number of EoR galaxies (cite: Smit2018; Hashimoto2019; Carniani2020; Bouwens2022; Wong2022; Schouws2023; Fujimoto2022; Heintz2023b; 2024A&A...682A.166F). Observations of the \[C ii\] emission line and studies of the interstellar medium (ISM) by combining multiple emission lines provide crucial diagnostics for the physical properties and galaxies’ star formation rates (cite: Harikane2020; Schaerer2020; Sugahara2022; Schouws2022; Witstok2022; Algera2023; Killi2023; Vallini2021; Vallini2024). However, multiple FIR emission line observations of high-redshift galaxies are limited to extremely IR luminous galaxies such as submillimeter galaxies (cite: DeBreuck2019; Meyer2022) and the numerous more representative star-forming galaxies were typically not targeted at high redshift. To change this situation, in this paper, we study the ISM properties using multiple FIR emission lines of typical star-forming galaxies in the EoR.

Firstly, we examine the fraction of \[C ii\] $158\,{\rm \mu m}$ originating from either ionized gas or neutral gas (both atomic and molecular) using observations of the \[N ii\] $205\,{\rm \mu m}$ emission line. C$^+$ ions exist in both ionized and neutral gas because their ionization potential is $11.3\,{\rm eV}$, while N$^+$ is found only in ionized gas due to its higher ionization potential of $14.5\,{\rm eV}$, which exceeds that of hydrogen. Because \[N ii\] $205\,{\rm \mu m}$ and \[C ii\] $158\,{\rm \mu m}$ have similar critical densities ($n_{\rm crit}\sim 40\,{\rm cm^{-3}}$ and $n_{\rm crit}\sim 50\,{\rm cm^{-3}}$ with electrons, respectively) and excitation temperatures ($\sim 70\,{\rm K}$ for \[N ii\] $205\,{\rm \mu m}$ and $\sim 50\,{\rm K}$ for \[C ii\] $158\,{\rm \mu m}$), both lines are produced with comparable luminosities inside ionized gas clouds where ionized nitrogen is present. Thus, the line ratio between \[C ii\] $158\,{\rm \mu m}$ and \[N ii\] $205\,{\rm \mu m}$ for ionized region can be estimated based on their assumed abundance and emissivity and the excess \[C ii\] $158\,{\rm \mu m}$ luminosity would originate from neutral gas.

As several previous studies performed for local and high-redshift IR luminous galaxies, the luminosity ratio between \[N ii\] $205\,{\rm \mu m}$ and \[C ii\] $158\,{\rm \mu m}$ indeed works as an indicator for constraining the origin of \[C ii\] $158\,{\rm \mu m}$ emission line for low- and high-redshift star-forming galaxies (cite: Malhotra2001; Oberst2011; Decarli2014; Bethermin2016; Pavesi2016; Croxall2017; Lee2021; Witstok2022; Pensabene2021; Decarli2023).

Secondly, we study the neutral gas properties of star-forming galaxies in the EoR using the \[O i\] $145\,{\rm \mu m}$ observations. Having similar ionization potential as that of hydrogen ($13.62\,{\rm eV}$ for Oxygen), neutral oxygen, O$^0$, is an ideal probe for the neutral star-forming gas. The \[O i\] $145\,{\rm \mu m}$ emission line ($\lambda_{\rm rest}= 145.53\,{\rm \mu m}$) is one of the important coolants in neutral gas, trace up to dense gas as it has a high critical densities of ${\rm n^{H}_{crit}} \sim 10^5\,{\rm cm^{-3}}$, and is optically thin unlike \[O i\]$\,63\,{\rm \mu m}$ (cite: Tielens1985; Kaufman1999). The \[O i\] $145\,{\rm \mu m}$ line has been observed in the local Universe (cite: Diaz-Santos2017; Herrera-Camus2018) as well as from high-redshift starbursts and active galactic nuclei (cite: DeBreuck2019; Yang2019; Novak2020; Lee2021; Pensabene2021; Meyer2022; Litke2023). These studies showed that the combination of \[C ii\] $158\,{\rm \mu m}$ and \[O i\] $145\,{\rm \mu m}$ emission lines is sensitive to the neutral gas density ($n$), and far-UV radiation field ($G_0$), enabling a measurement of these essential ISM parameters. While several studies have highlighted the importance of \[O i\] $145\,{\rm \mu m}$ emission lines in high-redshift SMGs and QSO hosts (cite: DeBreuck2019; Lee2021; Meyer2022), no observations of \[O i\] have been performed for star-forming galaxies that are more representative of the typical galaxy population in the EoR. In this study, we present the analyses and results of the first pilot observations for the \[O i\] $145\,{\rm \mu m}$ emission lines in \[C ii\] bright star-forming galaxies in the EoR.

This paper is organized as follows: in §[2](#sec:obs) we describe our target galaxies and the ALMA observations used in this study. In §[3](#sec:analysis), we present our data analysis and measurements for the \[O i\] $145\,{\rm \mu m}$ and \[N ii\] $205\,{\rm \mu m}$ emission lines. In §[4](#sec:results), we present the results of the study. In §[5](#sec:discussion), we compare to previous studies and discuss our results. Finally, we conclude with the summary in §[6](#sec:conclusion). Throughout this paper, we assume a cosmology with $(\Omega_m,\Omega_{\Lambda},h)=(0.3,0.7,0.7)$, and the (cite: Chabrier2003) initial mass function (IMF) with stellar masses ranging from $0.1$ to $300\,{\rm M_{\odot}}$, where applicable.

# Observation

+----------------------+----------------------------+----------------------------+----------------------+-----------------------+------------------------------------------+---------------------------------------+----------------------------------+
| Source               | $\alpha_{\rm J2000}$ (deg) | $\delta_{\rm J2000}$ (deg) | $z_{\rm spec}$       | Magnification ($\mu$) | $L_{\rm UV}\,(10^{11}\,{\rm L_{\odot}})$ | $M_{\ast}\,(10^{9}\,{\rm M_{\odot}})$ | SFR (${\rm M_{\odot}\,yr^{-1}}$) |
+:=====================+:==========================:+:==========================:+:====================:+:=====================:+:========================================:+:=====================================:+:================================:+
| REBELS-38            | 150.725208                 | 2.703333                   | 6.577                | –                     | $1.2\pm0.3$                              | $3.8^{+1.7}_{-3.6}$                   | $116\pm45$                       |
+----------------------+----------------------------+----------------------------+----------------------+-----------------------+------------------------------------------+---------------------------------------+----------------------------------+
| A1689-zD1            | 197.874708                 | -1.321861                  | 7.132                | $4.14\pm 0.36$        | $0.63\pm 0.05$$^{\dagger}$               | $3.7^{+1.6}_{-1.1}$$^{\dagger}$       | $83\pm 8^{\dagger}$              |
+----------------------+----------------------------+----------------------------+----------------------+-----------------------+------------------------------------------+---------------------------------------+----------------------------------+
| REBELS-25            | 150.134667                 | 1.742028                   | 7.307                | –                     | $1.0\pm0.2$                              | $7.7^{+3.2}_{-2.6}$                   | $200\pm83$                       |
+----------------------+----------------------------+----------------------------+----------------------+-----------------------+------------------------------------------+---------------------------------------+----------------------------------+
| REBELS-18            | 149.449583                 | 2.345472                   | 7.675                | –                     | $1.5\pm0.2$                              | $3.1^{+8.1}_{-2.5}$                   | $72\pm20$                        |
+----------------------+----------------------------+----------------------------+----------------------+-----------------------+------------------------------------------+---------------------------------------+----------------------------------+
| $\dagger$ Values are corrected by scaling with the updated gravitational lensing magnification factor of $\mu=4.14$.                                                                                             |                                  |
+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
| (see Appendix [7](#sec:lens))                                                                                                                                                                                    |                                  |
+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+

+:-----------------------:+:----------------------------------------:+:-----------------------:+:-----------------------:+:-----------------------:+:--------------------------------------------:+:-----------------------:+:------------------------:+:-----------------------:+
| Source                  | Emission Line                            | $\nu_{\rm obs}^{\ast}$  | $t_{\rm int}$           | PVW                     | Beam FWHM                                    | RMS$_{\rm cont.}$       | RMS$_{\rm line, 25km/s}$ | ALMA project ID         |
+-------------------------+------------------------------------------+-------------------------+-------------------------+-------------------------+----------------------------------------------+-------------------------+--------------------------+-------------------------+
|                         |                                          | (GHz)                   | (hrs)                   | $\rm{(mm)}$             |                                              | ($\rm{\mu Jy/beam}$)    | ($\rm{mJy/beam}$)        |                         |
+-------------------------+------------------------------------------+-------------------------+-------------------------+-------------------------+----------------------------------------------+-------------------------+--------------------------+-------------------------+
| REBELS-38               | \[N ii\] $205\,{\rm \mu m}$              | $192.8$                 | $1.5$                   | 0.749                   | $1.2\ensuremath{''}\times0.9\ensuremath{''}$ | $11$                    | $0.17$                   | #2022.1.01384.S         |
+-------------------------+------------------------------------------+-------------------------+-------------------------+-------------------------+----------------------------------------------+-------------------------+--------------------------+-------------------------+
|                         | \[O i\] $145\,{\rm \mu m}$               | $271.9$                 | $1.2$                   | $0.322$                 | $1.3\ensuremath{''}\times1.0\ensuremath{''}$ | $11$                    | $0.24$                   | #2022.1.00446.S         |
+-------------------------+------------------------------------------+-------------------------+-------------------------+-------------------------+----------------------------------------------+-------------------------+--------------------------+-------------------------+
| A1689-zD1               | \[N ii\] $205\,{\rm \mu m}$$^{\ast\ast}$ | $179.7$                 | $2.3$                   | $0.503$                 | $1.5\ensuremath{''}\times1.2\ensuremath{''}$ | $6.5$                   | $0.10$                   | #2021.1.00247.S         |
+-------------------------+------------------------------------------+-------------------------+-------------------------+-------------------------+----------------------------------------------+-------------------------+--------------------------+-------------------------+
|                         | \[O i\] $145\,{\rm \mu m}$               | $252.3$                 | $0.2$                   | $0.587$                 | $1.3\ensuremath{''}\times1.0\ensuremath{''}$ | $25$                    | $0.44$                   | #2022.1.00446.S         |
+-------------------------+------------------------------------------+-------------------------+-------------------------+-------------------------+----------------------------------------------+-------------------------+--------------------------+-------------------------+
| REBELS-25               | \[N ii\] $205\,{\rm \mu m}$              | $175.9$                 | $1.5$                   | 0.682                   | $1.5\ensuremath{''}\times1.0\ensuremath{''}$ | $8.8$                   | $0.28$                   | #2022.1.01384.S         |
+-------------------------+------------------------------------------+-------------------------+-------------------------+-------------------------+----------------------------------------------+-------------------------+--------------------------+-------------------------+
|                         | \[O i\] $145\,{\rm \mu m}$               | $248.0$                 | $0.8$                   | $1.470$                 | $0.6\ensuremath{''}\times0.5\ensuremath{''}$ | $14$                    | $0.27$                   | #2022.1.00999.S         |
+-------------------------+------------------------------------------+-------------------------+-------------------------+-------------------------+----------------------------------------------+-------------------------+--------------------------+-------------------------+
| REBELS-18               | \[O i\] $145\,{\rm \mu m}$               | $237.5$                 | $2.6$                   | $0.352$                 | $1.3\ensuremath{''}\times1.2\ensuremath{''}$ | $6.5$                   | $0.12$                   | #2022.1.00446.S         |
+-------------------------+------------------------------------------+-------------------------+-------------------------+-------------------------+----------------------------------------------+-------------------------+--------------------------+-------------------------+
| $\ast$ Target frequency of observations. See Table [\[tab:ALMAmeasurements\]](#tab:ALMAmeasurements) for measured redshifts of each emission line.                                                                                                                             |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $\ast\ast$ \[N ii\] $205\,{\rm \mu m}$ observation of A1689-zD1 is further presented and discussed in detail in Fujimoto et al. in preparation.                                                                                                                                |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

## Target Galaxies

Table [\[tab:targets\]](#tab:targets) summarizes our target galaxies and their basic properties. Below, we details our sample selection criteria.

Our targets are star-forming galaxies at $z>6.5$, i.e., those that have star-formation rates and stellar masses consistent with the main-sequence of star-forming galaxies at $z\sim7$ (cite: Topping2022). To select targets, we searched all previous \[C ii\] emission line observations including the cycle-7 ALMA large program Reionization Era Bright Emission Line Survey (REBELS; (cite: Bouwens2022)) as well as previously published \[C ii\] emission line observations (cite: Smit2018; Hashimoto2019; Carniani2020; Akins2022; Schouws2022; Schouws2025). Individual studies have their own selection methods based on the estimated accuracy of photometric redshifts as well as based on detections of Ly$\alpha$ emission lines. However, these galaxies were originally all selected based on their bright rest-frame UV luminosities (typically $M_{\rm UV} < -21\,{\rm mag}$; (cite: Bouwens2022)).

We further selected galaxies based on their expected luminosities of \[O i\] $145\,{\rm \mu m}$ and \[N ii\] $205\,{\rm \mu m}$ emission based on previously detected \[C ii\] $158\,{\rm \mu m}$ line emission luminosities. In particular, we performed flux limited selection of galaxies with their apparent \[C ii\] luminosity of $L_{\rm [CII]}>1.1\times10^{9}\,{\rm L_{\odot}}$. Using these criteria, we selected four \[C ii\] luminous star-forming galaxies; REBELS-38 at $z=6.577$ (cite: Bouwens2022; Algera2023), A1689-zD1 at $z=7.132$ (cite: Watson2015; Bakx2021; Akins2022; Killi2023), REBELS-25 at $z=7.307$ (cite: Bouwens2022; Hygate2023; Algera2023; Rowland2024), and REBELS-18 at $z=7.675$ (cite: Bouwens2022).

## ALMA Observations

Observation conditions, integration times, and beam sizes of these observations are summarized in Table [\[tab:ALMAobs\]](#tab:ALMAobs). In the following, we present details of these observations.

### \[O i\] $145\,{\rm \mu m}$ and \[N ii\] $205\,{\rm \mu m}$ Emission Line

Observations of \[O i\] $145\,{\rm \mu m}$ emission lines of target galaxies were newly performed during ALMA Cycle-9 #2022.1.00446.S (PI: Fudamoto) and #2022.1.00999.S (PI: De Looze). \[N ii\] $205\,{\rm \mu m}$ emission lines were newly observed in Cycle-9 #2022.1.01384.S (PI: Fudamoto) for REBELS-38 and REBELS-25. \[N ii\] $205\,{\rm \mu m}$ data of A1689-zD1 were retrieved from the ALMA archive #2021.1.00247.S (PI: Fujimoto). \[N ii\] $205\,{\rm \mu m}$ emission line observations of REBELS-38 and A1689-zD1 were fully executed. On the other hand, \[N ii\] $205\,{\rm \mu m}$ observations of REBELS-25 were only partially performed.

## ALMA data reduction

In this study, we present newly obtained ALMA data for the \[O i\] and \[N ii\] emission lines from the target galaxies. \[C ii\] $158\,{\rm \mu m}$ and \[O iii\] $88\,{\rm \mu m}$ emission line data are adopted from (cite: Watson2015; Akins2022; Bouwens2022; Killi2023; Wang2024; Algera2024).

The observed ALMA data of \[O i\] $145\,{\rm \mu m}$ and \[N ii\] $205\,{\rm \mu m}$ were reduced and analyzed using the Common Astronomy Software Application (CASA) version 6.2.1 (cite: Bean2022). ALMA observations for \[O i\] $145\,{\rm \mu m}$ and \[N ii\] $205\,{\rm \mu m}$ emission lines were calibrated using the second stage quality assurance (QA2) pipeline codes (i.e., ) without further flagging and editing.

To examine and analyze emission lines, we created data cubes using spectral windows (SPWs) that include the sky frequencies of each emission line, accounting for the target’s spectroscopic redshift. To create data cubes using the task of CASA, we applied a fixed velocity channel binning of $25\,{\rm km/s}$ for all data cubes. Rest-frame frequencies of each data cube were set to the sky frequency of each emission line observation based on the \[C ii\] emission line detections (table [\[tab:ALMAmeasurements\]](#tab:ALMAmeasurements)). Underlying dust continua of the target galaxies were subtracted using CASA task by fitting flat continua for the SPWs that do not include emission lines. Dust continuum maps of all observations were made using the continuum SPWs and using the task of CASA and using the multi-frequency synthesis () imaging mode.

When we created data cubes and dust continuum maps, we performed synthesized beam deconvolutions using the by setting stopping thresholds to be $3\times$ the pixel-by-pixel root-mean-square (RMS) of the dirty images and by setting the maximum number of iterations to 500 times. For data cubes, the background RMS was calculated as averages of RMS of all channels. The threshold and parameters did not affect final data quality as there were no particularly bright sources in the fields of views. All data cubes and continuum maps were imaged using the weighting scheme to maximize point source sensitivity. The achieved sensitivity of pixel-by-pixel RMS of the cleaned cubes and continuum maps are presented in table [\[tab:ALMAobs\]](#tab:ALMAobs).

# Analysis

![](Cutouts-C2O1.v5.pdf)

+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| Name                                                | REBELS-38              | A1689-zD1                    | REBELS-25                 | REBELS-18             |
+:====================================================+:======================:+:============================:+:=========================:+:=====================:+
| Magnification factor                                | –                      | $4.14 \pm 0.36 ^{\ast}$      | –                         | –                     |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $z_{\rm [OIII]88}$                                  | –                      | $7.132^{a}$                  | $7.3052 \pm 0.0004^{i}$   | –                     |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| FWHM$_{\rm [OIII]88}$ (${\rm km/s}$)                | –                      | $182\pm31^{a}$               | $203\pm 38^{i}$           | –                     |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| f$_{\rm [OIII]88}$ (${\rm Jy\,km/s}$)               | –                      | $53.3 \pm 3.5^{b}$           | $896^{+234,i}_{-207}$     | –                     |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $L_{\rm [OIII]88}$ ($\times 10^8\,{\rm L_{\odot}}$) | –                      | $124\pm 8^{b}$               | $20.0^{+5.1,i}_{-4.6}$    | –                     |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $S_{\rm 88}$ (${\rm \mu Jy}$)                       | $334\pm 63^{e}$        | $1757\pm 279^{f}$            | $486\pm 122^{e}$          | –                     |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $z_{\rm [CII]158}$                                  | $6.5770\pm0.0001$      | $7.132^{a}$                  | $7.3065\pm0.0002$         | $7.6750\pm0.0001$     |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| FWHM$_{\rm [CII]158}$ (${\rm km/s}$)                | $204\pm13$             | $323\pm8^{c}$                | $322\pm12$                | $209\pm11$            |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| f$_{\rm [CII]158}$ (${\rm Jy\,km/s}$)               | $1.58\pm0.12$          | $3.56\pm0.07^{b}$            | $1.28\pm0.04$             | $0.81\pm0.05$         |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $L_{\rm [CII]158}$ ($\times 10^8\,{\rm L_{\odot}}$) | $16.8\pm1.6$           | $45.0\pm1.0^{b}$             | $15.9\pm1.0$              | $10.8\pm0.9$          |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $S_{\rm 158}$ (${\rm \mu Jy}$)                      | $163\pm 23^{d}$        | $558\pm 102^{g}$             | $260\pm 22^{d}$           | $53\pm 10^{d}$        |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $T_{\rm d}$ (${\rm K}$)                             | $46^{+18}_{-11}$$^{j}$ | $42^{+13}_{-7}$$^{h}$        | $32^{+9}_{-7}$$^{i}$      | $39^{+12}_{-7}$$^{j}$ |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $\beta_{\rm d}$                                     |                        | $1.61^{+0.60}_{-0.75}$$^{e}$ | $2.5\pm0.4$$^{i}$         |                       |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $L_{\rm IR}$ ($\times 10^{11}\,{\rm L_{\odot}}$)    | $8.0^{+4.4}_{-2.9}$    | $20.1\pm0.7^{a}$             | $5.0^{+2.9}_{-1.0}$$^{i}$ | $3.5^{+2.0}_{-1.3}$   |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| This Work                                                                                                                                                       |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $z_{\rm [OI]145}$                                   | $6.5774\pm0.0003$      | $7.134\pm0.0006$             | $7.308\pm0.001$           | $7.676\pm0.0006$      |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| FWHM$_{\rm [OI]145}$ (${\rm km/s}$)                 | $112\pm24$             | $278\pm51$                   | $440\pm95$                | $165\pm38$            |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| f$_{\rm [OI]145}$ (${\rm Jy\,km/s}$)                | $0.110 \pm 0.022$      | $0.556 \pm 0.137$            | $0.394 \pm 0.082$         | $0.107 \pm 0.028$     |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $L_{\rm [OI]145}$ ($\times 10^8\,{\rm L_{\odot}}$)  | $1.3 \pm 0.3$          | $7.3 \pm 1.8$                | $5.3\pm1.1$               | $1.6 \pm 0.4$         |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $S_{\rm 145}$ (${\rm \mu Jy}$)                      | $220\pm28$             | $705\pm76$                   | $270\pm41$                | $116\pm12$            |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| f$_{\rm [NII]205}$ (${\rm Jy\,km/s}$)               | $<0.045$ ($3\,\sigma$) | $<0.059$ ($3\,\sigma$)       | $< 0.076$ ($3\,\sigma$)   | –                     |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $L_{\rm [NII]205}$ ($\times 10^8\,{\rm L_{\odot}}$) | $<0.37$ ($3\,\sigma$)  | $< 0.55$ ($3\,\sigma$)       | $<0.73$ ($3\,\sigma$)     | –                     |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $S_{\rm 205}$ (${\rm \mu Jy}$)                      | $131\pm39$             | $269\pm15$                   | $94\pm12$                 | –                     |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+
| $f_{\rm [CII]}^{\rm PDR}$                           | $>0.92$                | $>0.96$                      | $>0.83$                   | –                     |
+-----------------------------------------------------+------------------------+------------------------------+---------------------------+-----------------------+

a\. (cite: Akins2022), b. (cite: Killi2023), c. (cite: Wong2022), d. (cite: Inami2022), e. (cite: Algera2023), f. (cite: Inoue2020), g. (cite: Watson2015). h. (cite: Bakx2021), i. (cite: Algera2024). j. (cite: Sommovigo2022).

$^{\ast}$ See Appendix [7](#sec:lens) for the discussion of the magnification factor. All the measurements from A1689-zD1 are not corrected for the lensing magnification.

## Emission Line Detections

For the \[O i\] $145\,{\rm \mu m}$ emission line data, we find clear detections of emission lines at the expected frequencies from all targets. For the detected \[O i\] lines, we created moment-0 images by determining the appropriate frequency widths that capture \[O i\] $145\,{\rm \mu m}$ emission using an iterative method. First, we performed 1D Gaussian fits on the extracted spectra and re-integrated the data cube using frequency ranges that encompass the $2\,\sigma$ line widths. Next, we re-extracted spectra from regions in the moment-0 images where pixel values exceeded $2\,\sigma$, further refining the emission line spectra. We then repeated the 1D Gaussian fitting to update the frequency width and generate new moment-0 images. This process was repeated until the selected channels for moment-0 image creation converged.

For the \[N ii\] $205\,{\rm \mu m}$ emission line data of REBELS-38 and REBELS-25, we did not identify any emission lines from the extracted spectra. To further examine the \[N ii\] lines, we created moment-0 images by using velocity widths fixed to those of \[C ii\] $158\,{\rm \mu m}$ emission lines ($1\times$ FWHMs and $2\times$ FWHMs). We only found signals $\lesssim3\,\sigma$ at the expected source position. We thus concluded that all the \[N ii\] $205\,{\rm \mu m}$ emission lines were non-detected.

For \[N ii\] $205\,{\rm \mu m}$ emission line of A1689-zD1, we found a weak $\lesssim 3\sigma$ signal in its moment-0 map integrated over the same velocity FWHM as the \[C ii\] $158\,{\rm \mu m}$ emission line (cite: Wong2022). However, we treated the \[N ii\] $205\,{\rm \mu m}$ of A1689-zD1 as an upper limit based on the following reasons. In the spectra (bottom panels in figure [1](#fig:cutouts)), the positive signal has two peaks that are slightly off from the expected frequency from the \[C ii\] emission detection. As clumpy structures of A1689-zD1 was reported (cite: Wong2022) and the spectra have a non-Gaussian shape, the positive signal might arise from some of the clumps distributed in a line of sight in the A1689-zD1 and the \[N ii\] emitting region do not overlap with that of \[C ii\] emission line. As our current observations of \[N ii\] $205\,{\rm \mu m}$ and \[O i\] $145\,{\rm \mu m}$ does not have enough spatial resolution to resolve the clumps and as the detection signals are marginal, we treat the \[N ii\] $205\,{\rm \mu m}$ signal of A1689-zD1 as an upper limit. However, even if we treat the \[N ii\] $205\,{\rm \mu m}$ as detection, our results do not change.

We measured line fluxes (for the detected lines) and flux upper limits (for non-detections) using the moment-0 images. For the detected \[O i\] $145\,{\rm \mu m}$ emission lines, we performed 2-D Gaussian fittings using CASA task . For non-detected \[N ii\] $205\,{\rm \mu m}$ emission lines, we measured $3\,\sigma$ upper limit fluxes by calculating the $3\times$ pixel-by-pixel RMSs of moment-0 maps integrated over the FWHMs of \[C ii\] emission lines. All emission line images are shown in figure [1](#fig:cutouts) and our ALMA measurements are listed in table [\[tab:ALMAmeasurements\]](#tab:ALMAmeasurements).

## Dust Continuum Detection

Dust continua were all clearly detected from all targets with $>4.5\,\sigma$ significance at the source positions. We measured continuum fluxes by 2-D Gaussian fittings using the CASA task . Measured continuum fluxes are listed in table [\[tab:ALMAmeasurements\]](#tab:ALMAmeasurements). Appendix [8](#sec:dust) shows dust continuum images.

![](C2N2_LIR.v7_mod.pdf)

# Results

Here we present the results of our observations, with particular focus on the inferred FIR line luminosities and the physics implied by their intrinsic ratios.

## IR Luminosity and FIR SED

The FIR spectral energy distribution (SED) and IR luminosities[^1] of A1689-zD1 and REBELS-25, REBELS-38 have already been studied in detail by (cite: Bakx2021) and (cite: Algera2023). We adopt dust temperatures ($T_{\rm d}$), emissivity indexes ($\beta_{\rm d}$), and IR luminosities ($L_{\rm IR}$) measured in these previous studies.

REBELS-18 does not have direct FIR SED measurements as only low-spatial resolution $\lambda=158\,{\rm \mu m}$ continuum observations were obtained so far. With the new $\lambda=145$ and $205\,{\rm \mu m}$ continuum observations, the dust temperatures are challenging to constrain as these wavelengths only cover the Rayleigh–Jeans tail of the emission and the accurate constraints of dust temperatures require higher frequency (cite: Faisst2020) or higher spatial resolution observations (cite: Inoue2020; Fudamoto2023). In this study, thus we rely on the dust temperature and IR luminosity estimations for REBELS-18 inferred from the \[C ii\] emission lines (cite: Sommovigo2022).

## \[N ii\] $205\,{\rm \mu m}$ and \[C ii\] $158\,{\rm \mu m}$ line luminosity ratio

Using the non- or tentative-detections of the \[N ii\] $205\,{\rm \mu m}$ emission lines for our target galaxies, we calculated $3\,\sigma$ lower limit luminosity ratio $L_{\rm[CII]158}/L_{\rm [NII]205}$ ranging from $\gtrsim21$ to $\gtrsim87$ (left panel of figure [2](#fig:C2N2ratio)). The observed line ratios of these EoR star-forming galaxies are generally much higher than the average distributions of local IR luminous galaxies observed by GOALS (cite: Diaz-Santos2017) and high-redshift SMGs at $z\sim4-6$ (cite: Cunningham2020). Also, these high \[N ii\] $205\,{\rm \mu m}$/\[C ii\] $158\,{\rm \mu m}$ line ratios are consistent with the ${\rm SFR}>30\,{\rm M_{\odot}\,yr^{-1}}$ sample of simulated galaxies at $z=7.7$ from the SERRA simulation (cite: pallottini:2022). The $3\,\sigma$ lower limits of A1689-zD1 and REBLES-38 show the highest line luminosity ratios, which strongly indicate that the \[C ii\] $158\,{\rm \mu m}$ emission lines are dominated by those from the PDR and not from HII regions (see §5.1).

![](O3O1_C2O1.v3_mod.pdf)

## \[O i\] $145\,{\rm \mu m}$, \[C ii\] $158\,{\rm \mu m}$, and \[O iii\] $88\,{\rm \mu m}$ line luminosity ratio

From the observed \[O i\] $145\,{\rm \mu m}$ emission line luminosity, we measure the \[O i\] $145\,{\rm \mu m}$ to \[C ii\] $158\,{\rm \mu m}$ emission line ratios to be in a range between $0.08\pm0.02$ and $0.33\pm0.07$ with a median of $0.16$ (figure [3](#fig:O1C2-LIR)). The range of the \[O i\]/\[C ii\] ratio is similar to that of $z>4$ QSOs/SMGs. Most of our observation results are distributed at around the higher edge of local galaxy distribution at a fixed IR luminosity range. The high \[O i\]/\[C ii\] line ratio indicate high density of neutral gas regions. High neutral gas density in high-redshift galaxies have been reported in previous observational studies (cite: Bothwell2017), although the emission line used and the neutral gas regions investigated would differ from those in our study. We will discuss the implications of these \[O i\] $145\,{\rm \mu m}$ observations in detail in §[5.2](#sec:ISM)

We also investigated \[C ii\] $158\,{\rm \mu m}$/\[O i\] $145\,{\rm \mu m}$ luminosity ratio versus \[O iii\] $88\,{\rm \mu m}$/\[O i\] $145\,{\rm \mu m}$ luminosity ratio (right panel of Figure [3](#fig:O1C2-LIR)) for REBELS-25 and A1689-zD1 as these galaxies have \[O iii\] $88\,{\rm \mu m}$ emission line observations reported in previous studies. In this diagram REBELS-25 is located at the lower left corner i.e., the lowest ranges of \[O iii\] $88\,{\rm \mu m}$/\[O i\] $145\,{\rm \mu m}$ ratio as well as \[C ii\] $158\,{\rm \mu m}$/\[O i\] $145\,{\rm \mu m}$ ratio. In contrast, A1689-zD1 shows a higher \[O iii\] $88\,{\rm \mu m}$/\[O i\] $145\,{\rm \mu m}$ ratio compared to most local galaxies/AGNs, similar to the local dwarf galaxies studied by (cite: Cormier2015). The \[O iii\] $88\,{\rm \mu m}$/\[O i\] $145\,{\rm \mu m}$ line ratio is correlated with the volume filling factor of ionized oxygen, which in turn is related to the ionization parameter ($U_{\rm ion}$) (cite: DeBreuck2019).

Previous studies have shown that the high \[OIII\]/\[CII\] line ratio in high-redshift galaxies is due to a high $U_{\rm ion}$ and/or lower PDR covering factors (cite: Hashimoto2019; Harikane2020; Witstok2022). REBELS-25 and A1689-zD1 have \[OIII\]/\[CII\] ratios of 1.3 (cite: Algera2023) and 2.1 (cite: Wong2022), respectively. The \[OIII\]/\[CII\] ratio of REBELS-25 is among the lowest values observed for $z > 6$ star-forming galaxies. The low \[O iii\] $88\,{\rm \mu m}$/\[O i\] $145\,{\rm \mu m}$ line ratio of REBELS-25, suggesting low $U_{\rm ion}$, is consistent with its relatively low \[O iii\] $88\,{\rm \mu m}$/\[C ii\] $158\,{\rm \mu m}$ line ratio. In contrast, the higher \[O iii\] $88\,{\rm \mu m}$/\[O i\] $145\,{\rm \mu m}$ line ratio of A1689-zD1 suggests a higher $U_{\rm ion}$, which is generally consistent with its higher \[O iii\] $88\,{\rm \mu m}$/\[C ii\] $158\,{\rm \mu m}$ ratio. Although sample size is currently too small, these line ratios suggest the potential for using multiple FIR emission lines to diagnose gas properties.

## Origin of \[O i\] and \[C ii\] emission lines of REBELS-38

Most of the target galaxies have \[O i\] $145\,{\rm \mu m}$ emission lines that spatially coincide and have profiles consistent with those of \[CII\] emission lines. However, \[O i\] emission line of REBELS-38 has significantly ($>2\,\sigma$) narrower emission line profile compared with \[C ii\] emission line (i.e., ${\rm FWHM_{[OI]}=112\pm 24}$ vs ${\rm FWHM_{[CII]}}=204\pm 13\,{\rm km/s}$). The difference of the emission line profile suggests that the \[O i\] and \[C ii\] of REBELS-38 are originated from different ISM components. In such case, analysis and discussions using \[O i\]/\[C ii\] of REBELS-38 may breaks down. To study this problem in detail, higher resolution observations of both \[O i\] and \[C ii\] emission lines are necessary. Thus, we only remark on this potential issue for REBELS-38.

# Discussion

## Origins of \[C ii\] $158\,{\rm \mu m}$ Emission Lines

Following previous studies (cite: Decarli2023), we describe the fraction of \[C ii\] $158\,{\rm \mu m}$ emission originated from PDR using \[C ii\] and \[N ii\] luminosity ratio as: $$\begin{equation}
    f^{\rm PDR}_{\rm [C\sc{II}]} = 1 - R_{\rm ion}\,(\frac{L_{\rm{[N\sc{II}]205\,\mu m}}}{L_{\rm{[C\sc{II}]158\,\mu m}}})\\
\end{equation}$$ where $R_{\rm ion}$ is the expected \[C ii\] over \[N ii\] emission line luminosity ratio when \[C ii\] is originating entirely from H ii regions. Due to the similar emission properties of \[C ii\] $158\,{\rm \mu m}$ and \[N ii\] $205\,{\rm \mu m}$ (e.g., their critical density and excitation temperature), $R_{\rm ion}$ was found to have a tight range between $2.5$ to $3$ assuming an electron density of the range $n_{\rm e} = 10$ - $100\,{\rm cm^{-3}}$ (cite: Croxall2017). Using wider ranges of parameters (metallicity, ionization field strength, gas density), (cite: Witstok2022) found a wider range of $R_{\rm ion}=1.5$ - $5.7$ by incorporating various metallicities, ionization parameters, hydrogen densities, and elemental abundances (blue band in Figure [2](#fig:C2N2ratio)). In this study, we use $R_{\rm ion}=3.6$ as our fiducial value by taking an average of $R_{\rm ion}$ found in the analysis of (cite: Witstok2022). Later, we will discuss how the results change by using a higher value of $R_{\rm ion}=5.7$.

With the measured luminosity ratio between \[C ii\] $158\,{\rm \mu m}$ and \[N ii\] $205\,{\rm \mu m}$ of the target galaxies, we find $3\,\sigma$ lower limits of $f_{\rm [CII]}^{\rm PDR} > 0.92$, $>0.96$, and $>0.83$ using $R_{\rm ion}=3.6$ for REBELS-38, A1689-zD1, and REBELS-25, respectively. We also estimated the PDR fraction of \[C ii\] of B14-65666 at $z=7.15$ where \[N ii\] $205\,{\rm \mu m}$ line luminosity is estimated from \[N ii\]$122\,{\rm \mu m}$ line (cite: Hashimoto2019; Sugahara2021). With the estimated \[N ii\] $205\,{\rm \mu m}$ line luminosity assuming $n_{\rm e}=200\,{\rm cm^{-3}}$, we find $3\,\sigma$ lower limit of $f_{\rm [CII]}^{\rm PDR}>0.94$ for $R_{\rm ion}=3.6$, respectively. These $f_{\rm [CII]}^{\rm PDR}$ are thus similarly high as our \[N ii\] $205\,{\rm \mu m}$ observed samples. Even using the large value of $R_{\rm ion}=5.7$, we find $f_{\rm [CII]}^{\rm PDR} > 0.87$, $>0.93$, $>0.74$, and $>0.91$ for REBELS-38, A1689-zD1, REBELS-25, and B14-65666, respectively.

These inferred PDR fractions of \[C ii\] are high $f_{\rm [CII]}^{\rm PDR}$ compared with those of lower-redshift star-forming galaxies in the similar IR luminosity range and higher than those explained by ionized gas dominated emissions (left panel of figure [2](#fig:C2N2ratio)).

![](Cloudy_G0_nH.v3.pdf)

Previous studies of local IR luminous galaxies find that the dust temperature and the $f_{\rm [CII]}^{\rm PDR}$ correlate well (cite: Malhotra2001; Diaz-Santos2017). Our target galaxies are consistent with the correlation found in (cite: Diaz-Santos2017) except for the fact that most of the high-redshift and high-$T_{\rm d}$ galaxies studied here have saturated $f_{\rm [CII]}^{\rm PDR}$ (right panel of figure [2](#fig:C2N2ratio)). (cite: Diaz-Santos2017) discussed that the correlation is due to the increase of the gas density in the star-forming region, which result in the increase of dust temperatures, in turn, which enhance the collisional de-excitation or the thermalization of \[C ii\] and makes \[C ii\] $158\,{\rm \mu m}$ emission faint especially in ionized region where the critical density of \[C ii\] $158\,{\rm \mu m}$ emission is much lower than that in the neutral gas[^2]. As a result, high density and high temperature environment of ionized gas would make their contribution to the total \[C ii\] $158\,{\rm \mu m}$ luminosity low.

On the other hand, recent studies find an increase in dust temperature as a function of redshift for normal star-forming galaxies (cite: Schreiber2018; Faisst2020; Sommovigo2022). These studies find that the typical dust temperature of star-forming galaxies at $z\sim6-7$ to be $T_{\rm d}\sim40-60\,\rm{K}$. If the correlation of $f_{\rm [CII]}^{\rm PDR}$ and $T_{\rm d}$ exist for the $z\gtrsim6$ galaxies and the dust temperature of star-forming galaxies systematically increase as a function of redshift, the high-redshift star-forming galaxies should have very high or saturated $f_{\rm [CII]}^{\rm PDR}$ by combining these two correlations. Our finding of the high $f_{\rm [CII]}^{\rm PDR}$ from our target galaxies are consistent with the scenario in which high-redshift galaxies have the high $f_{\rm [CII]}^{\rm PDR}$ due to high gas densities and/or high dust temperatures.

These features show that \[C ii\] $158\,{\rm \mu m}$ emission lines from star-forming galaxies in the epoch of reionization are more dominated by PDR regions compared with lower redshift galaxies, as also suggested by (cite: Heintz22; Heintz23c). Thus, we conclude that the origin of \[C ii\] $158\,{\rm \mu m}$ emission lines of these star-forming galaxies studied here are neutral gas. This is in line with simulations (cite: Pallottini2017) and theoretical predictions (cite: Vallini2017; Ferrara2019). These results indicate that \[C ii\] $158\,{\rm \mu m}$ emission is an excellent tracer of neutral ISM.

We hereafter treat all the \[C ii\] emissions from our targets are all come from their neutral gases, and no corrections are applied to study when combining with \[O i\] $145\,{\rm \mu m}$ emission line luminosity in the following sections.

## ISM properties

### CLOUDY settings and grids

To analyze the neutral gas conditions of our sample, we used (cite: Ferland2017) with the observed ratios of fine structure lines. In this analysis, we focus on modeling emission only from neutral gas (i.e., PDR and molecular gas) and we treat \[C ii\] $158\,{\rm \mu m}$ emission lines fully arising from neutral gas as we find in Section [5.1](#sec:C2origin). To make models of neutral gas emission using , we removed ionizing photons from impinging radiation fields[^3].

We fixed the impinging radiation to blackbody radiation with a temperature of $T=50000\,\rm{\rm K}$ by setting `blackbody 5e4 K` in the input, following previous studies (cite: Pensabene2021; Decarli2023). The FUV radiation field intensity was defined using Habing flux in the unit of $\rm{G_0}$ where $1\,{\rm G_0}$ corresponds to $1.6\times10^{-3}\,{\rm erg\,s^{-1}\,cm^{-2}}$ over $6<h\nu<13.6\,{\rm eV}$ (cite: Habing1968). We then made a grid of $G_0$ ranging $1<{\rm log}\,G_0<6$ and the ${\rm log}\, G_0$ is spaced by $0.29\,{\rm dex}$. Cosmic rays are added as a background, which works for the ionization balance in deep neutral-molecular gas regions. We used the ’s default setting by using the command: `cosmic rays, background`. We used the plane-parallel geometry with a constant hydrogen density by setting `constant density`. The elemental and the dust grain abundance is adopted using ’s default set for ISM by setting `abundance ISM`. The polycyclic aromatic hydrocarbons (PAHs) abundance is then set by using `grains PAH`. The grain and gas metallicity is scaled to values based on the oxygen abundance mesurements by recent JWST observations; $12+{\rm log(O/H)}= 8.45$, $8.05$, $8.63$, and $8.50$ for REBELS-38, A1689-zD1, REBELS-25, and REBELS-18, respectively ((cite: Rowland2025) and Carmen Blanco-Prieto; private communications). Finally, we set a stopping criteria of reaching a gas column density of $\rm{log(}N_{\rm H}/{\rm cm^{-2}})=23$. We executed all the run until it converges using `iterate to converge`. The neutral gas density ranges $2<{\rm log}\,n_{\rm H}/{\rm cm^3}<7$ spaced by $0.29\,{\rm dex}$.

With the above setups, we made a grid of emission line models by varying hydrogen density $n_{\rm H}\,{\rm cm^{-3}}$ and radiation field strength. We then calculated emission ratios of \[C ii\]/$L_{\rm IR}$, and \[C ii\]/\[O i\] for all $n_{\rm H}\,{\rm cm^{-3}}$ and FUV radiation field strength[^4].

### Gas densities and FUV field strengths of star-forming galaxies in the EoR

Figure [4](#fig:pdrt) shows our results of the modelings with measured \[O i\] $145\,{\rm \mu m}$/\[C ii\] $158\,{\rm \mu m}$ and \[C ii\]/$L_{\rm IR}$ emission ratios. All galaxies except for REBELS-25 have solutions of $G_0$ and $n_{\rm H}$ that explain the observed line ratios. We find that radiation field strengths have similar values ranging around ${\rm log}\,G_0\sim2.5 - 3.0$. This range of radiation field strength is a factor of a few to up to an order of magnitude lower than those found in high-redshift SMGs or quasars (cite: Bothwell2017; DeBreuck2019; Novak2019; Pensabene2021; Meyer2022). On the other hand, the gas densities range ${\rm log}\,n_{\rm H}\,{\rm cm^{-3}}\sim 3.5$ to $\sim6$ that are $\times10$ to $\times1000$ higher than those of local main-sequence galaxies and that are similar to those of local, high-redshift starbursts, or SMGs , which is consistent with the finding of (cite: Markov2022). Overall, compared with high-redshift ($z\sim4-6$) SMGs, our target star-forming galaxies in the EoR have a similar range of gas densities and lower FUV radiation field strengths (figure [5](#fig:nG0)).

![](n_G0.v2_mod.pdf)

The lower $G_0$ and similar $n_{\rm H}$ compared with SMGs could be simply explained by the lower SFRs of our targets than those of SMGs and similar gas densities. Assuming a spherical distribution of neutral gas at a fixed gas density, the mass of the neutral gas (and thus star-formation rates) scales as $\propto r^{3}$. By defining $f$ as the mass ratio between starbursts and star-forming galaxies, output intensity from star-forming activities scale as $\propto f^{(1/3)}$ (see footnote[^5]). Typically, dusty star-forming galaxies found by SPT survey have much larger SFRs (e.g., a few $\times 100\,{\rm M_{\odot}\,yr^{-1}}$) which is $\sim 5$ - $10\times$ larger than those of galaxies studied here. Thus, in this simple estimation, we expect $\sim5^{1/3}$ - $10^{1/3} \sim 2\times$ (or $\sim0.3\,{\rm dex}$) lower FUV intensity , if we fix a gas density, which is consistent with our results that show starbursts and star-forming galaxies in the EoR have a similar range of $n_{\rm H}$ and lower $G_0$. Thus, our PDR analysis suggests the picture that \[C ii\] bright star-forming galaxies in the EoR have similarly high gas densities with simply scaled-down star formation activities than those of SMGs.

The difficulty of explaining REBELS-25’s emission line ratios is likely due to the uncertainty of the gas-phase metallicity of the neutral gas as we do find that clear solution for $G_0$ and $n_{\rm H}$ if we assume lower metallicity (e.g., $12+{\rm log(O/H)}=8.05$) rather than higher metallicity of $12+{\rm log(O/H)}=8.63$. Since our metallicity is estimated using ionized gas emission lines observed using JWST (cite: Rowland2025), we assumed that same metallicity for ionized gas and neutral gas. If this assumptions is not the case and the majority of neutral gas of REBELS-25 has lower metallicity (e.g., due to infalling pristine gas) than ionized gas, our model may explain the \[O i\]/\[C ii\] and \[C ii\]/$L_{\rm IR}$ with $G_0\sim 10^{2.5}$ and $n_{\rm H}\sim 10^{6}\,{\rm cm^{-3}}$. While the $n_{\rm H}$ and $G_0$ for REBELS-25 are uncertain, the high \[O i\]/\[C ii\]and high \[C ii\]/$L_{\rm IR}$ indicate that REBELS-25 has low $G_0$ with high $n_{\rm H}$. In the following we thus assume $G_0\sim 10^{2.5}$ and $n_{\rm H}\sim 10^{6.5}\,{\rm cm^{-3}}$ as the likely parameters for REBELS-25.

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | FUV strength | $n_{\rm H}$ | $M_{\rm O, T_{\rm ex}=50\,{\rm K}}$ | $M_{\rm H\_[OI]145}$ |  |
|  | (${\rm G_0})$ | (${\rm cm^3}$) | ($\times 10^8\,{\rm M_{\odot}}$) | ($\times10^{9}\,{\rm M_{\odot}}$) |  |
| REBELS-38 | $10^{2.8\pm0.2}$ | $10^{3.8\pm0.2}$ | $1.0\pm 0.2$ | $1.4\pm 0.3$ |  |
| A1689-zD1 | $10^{2.76\pm0.02}$ | $10^{4.57\pm0.03}$ | $1.4\pm 0.4 \times (4.14/\mu)$ | $4.9\pm 0.4 \times (4.14\mu$) |  |
| REBELS-25 | $\sim10^{2.5}$ | $\sim10^{6.5}$ | $4.2\pm 0.9$ | $3.9\pm 0.8$ |  |
| REBELS-18 | $\sim10^{2.6}$ | $>10^{4.3}$ | $1.3\pm 0.3$ | $25\pm 6$ |  |

## Hydrogen and Oxygen Mass

### Oxygen mass

In the optically thin limit[^6], the oxygen atom masses of galaxies can be derived using \[O i\] $145\,{\rm \mu m}$ luminosity and the following formula

$$\begin{equation}
    M_{\rm O}/{\rm M_{\odot}} = 6.19 \times 10^{-5}\,Q(T_{\rm ex})\,e^{329\,{\rm K}/T_{\rm ex}}\,L^{\prime}_{\rm [OI]145}
\end{equation}$$ where $Q(T_{\rm ex})$ is the partition function and $Q(T_{\rm ex})=5+3\,e^{-329\,{\rm K}/T_{\rm ex}}+e^{-228\,{\rm K}/T_{\rm ex}}$ for the oxygen atom, $L^{\prime}_{\rm [OI]145}/{\rm K\,km\,s^{-1}\,pc^{2}}$ is the integrated \[O i\] $145\,{\rm \mu m}$brightness temperature in units of , and $T_{\rm ex}/{\rm K}$ is the excitation temperature (cite: Weiss2003; Weiss2005; Meyer2022).

For the calculation, we assume an excitation temperature of $T_{\rm ex} = 50\,{\rm K}$, which is derived by CO emission line observations (cite: Riechers2009). We estimated neutral oxygen masses of our targets between $1.0\times 10^8\,{\rm M_{\odot}}$ and $4.2\times 10^8\,{\rm M_{\odot}}$ (table [\[tab:mass\]](#tab:mass)).

We note that if we assume a higher $T_{\rm ex}$ the estimated atomic oxygen masses become smaller: e.g., $M_{\rm O, 150\,{\rm K}}=1.4\times 10^{6}$ assuming $T_{\rm ex}=150\,{\rm K}$ for REBELS-38. Thus, there would be a large systemic uncertainty to the estimated atomic oxygen masses from the assumed excitation temperature.

### Hydrogen masses of EoR star-forming galaxies

With the estimated atomic oxygen masses, we estimate hydrogen masses of our target galaxies. To do this, we used oxygen abundances recently estimated using optical \[O iii\] with H$\beta$ lines from JWST observations ((cite: Rowland2025), Stefanon et al., 2024 in prep. and Blanco-Prieto et al., 2024 in prep). For this purpose, we applied oxygen abundances from JWST observations that are assumed during the `CLOUDY` calculations[^7]. By applying the oxygen abundance to the derived oxygen mass, we find $M_{\rm H}$ between $1.4\pm 0.3\times 10^{9}\,{\rm M_{\odot}}$ and $2.5\pm 0.6\times 10^{10}\,{\rm M_{\odot}}$ (table [\[tab:mass\]](#tab:mass)). With the estimated hydrogen mass, we estimate gas mass fractions of $M_{\rm H}/(M_{\ast} + M_{\rm H})\sim 0.3-0.9$, that are similar ranges recently derived from high-redshift galaxy studies using \[C ii\] $158\,{\rm \mu m}$ lines (cite: 2010ApJ...714L.162H; Dessauges2020; Heintz22; Aravena2023; Heintz2023).

(cite: Wilson2023) reported a tight correlation between \[O i\] $145\,{\rm \mu m}$ emission line luminosities and H i gas masses in $z\sim2$ - $6$ star-forming galaxies using gamma-ray bursts as a probe, and supported by local galaxy observations and hydro-dynamical simulations. Using the correlation, we find H i gas masses of $5.9\times10^{9}$, $1.6\times 4.14/\mu \times10^{10}$, $2.3\times10^{10}$, $6.9\times10^{9}\,{\rm M_{\odot}}$ for REBELS-38, A1689-zD1, REBELS-25, and REBELS-18, respectively. These derived values are in good agreements with our estimated hydrogen masses derived from the oxygen abundances and oxygen masses assuming $T_{\rm ex}=50\,{\rm K}$, while there is a relatively large scatter likely arising from the uncertainties of assumed $T_{\rm ex}$.

We also compared the estimated hydrogen masses with molecular gas masses estimated using \[C ii\] $158\,{\rm \mu m}$ emission lines. To do this comparison, we used the relation found in (cite: 2010ApJ...714L.162H), who employed constraints on PDR models to derive the atomic gas mass of a hyperluminous ($L_{\rm IR}\sim 10^{13}\,{\rm L_{\odot}}$) starburst galaxy at $z = 1.3$. Using the equation (1) of (cite: 2010ApJ...714L.162H) and applying estimated gas density and gas temperature of $50\,{\rm K}$, we find atomic gas masses are $7.0\times 10^9$, $4.0\times 10^9$, $5.0\times 10^9$, and $3.7\times 10^9$ for REBELS-38, A1689-zD1, REBELS-25, and REBELS-18, respectively. We find the results are in good agreement with our estimations, although there are uncertainties of the ionization correction factor and the true C abundance.

We also used correlation found in (cite: Zanella2018). From the correlation, we found molecular gas masses of $M_{\rm H_2}=5.2\times10^{10}$, $3.4\times10^{10}\times(4.14/\mu)$, $5.0\times10^{10}$, and $3.3\times10^{10}\,{\rm M_{\odot}}$ for REBELS-38, A1689-zD1, REBELS-25, and REBELS-38, respectively. This molecular gas masses are generally consistent but an order of magnitude higher than hydrogen mass we derived using \[O i\] $145\,{\rm \mu m}$ emission above. Given the relatively large scatter of the \[C ii\]-to-$M_{\rm H_2}$ conversion, these two estimation might still be consistent. However, these excess might represent some of the unaccounted oxygen mass exist in molecular phase or variations of conversion factor, $\alpha_{\rm [CII]}$ in our sample. Further detailed analysis is, however, beyond the scope of this paper.

# Conclusion

In this paper, we presented results of multiple FIR emission line observations and analysis of four main-sequence star-forming galaxies in the epoch of reionization at $z>6.5$. The target galaxies were selected based on their previous detections of luminous \[C ii\] $158\,{\rm \mu m}$ emission lines ($L_{\rm [CII]}>10^{9}\,{\rm L_{\odot}}$). We performed follow-up observations of \[O i\] $145\,{\rm \mu m}$ and \[N ii\] $205\,{\rm \mu m}$ emission lines of the target galaxies. As results of the follow-up ALMA observations and analysis, we find the following:

$\bullet$ From the \[N ii\] $205\,{\rm \mu m}$ emission line observations, we only find non-detections and a tentative detections, showing that \[N ii\] $205\,{\rm \mu m}$ emission lines are much fainter than \[C ii\] $158\,{\rm \mu m}$ emission lines ($3\,\sigma$ upper limit of $L_{\rm{[CII]158}}/L_{\rm [NII]205} >21$ to $>87$). From these high $L_{\rm{[CII]158}}/L_{\rm [NII]205}$ ratio, we estimate the fraction of \[C ii\] $158\,{\rm \mu m}$ emission arising from ionized gas and find that the dominant fraction of \[C ii\] $158\,{\rm \mu m}$ emission lines arise from neutral gas with $f^{\rm PDR} > 0.74$ to $>0.96$ ($3\,\sigma$ lower limits). These results indicate that \[C ii\] $158\,{\rm \mu m}$ emission is an excellent tracer of neutral ISM.

$\bullet$ We detect \[O i\] $145\,{\rm \mu m}$ emission lines from all the target galaxies and find \[O i\] $145\,{\rm \mu m}$/\[C ii\] $158\,{\rm \mu m}$ luminosity ratio of $0.08$ - $0.33$ (median $0.16$). The observations marks the first detections of \[O i\] $145\,{\rm \mu m}$ emission lines and these are the first emission lines obtained purely neutral medium from \[C ii\] bright star-forming galaxies in the epoch of reionization at $z>6.5$. These observations show that \[O i\] $145\,{\rm \mu m}$ emission line observations would be feasible for larger samples of galaxies to constrain neutral gas properties of high-redshift galaxies.

$\bullet$ Using spectral synthesis calculations of , we model neutral gas conditions of the target galaxies. By calculating FIR emissions in a grid of gas densities and FUV radiation field strengths, we find that the target galaxies have similarly moderate FUV radiation field strength of $G_0\sim10^{2.5}-10^{3.0}$. We also find high PDR gas densities of $n_{\rm PDR}\sim10^4$ to $\sim10^{6}\,{\rm cm^{-3}}$ that spans a similar range with high-redshift ($z\sim4-6$) SMGs. Overall, the neutral ISM of \[C ii\] bright star-forming galaxies studied here is characterized by having high gas densities and moderately strong FUV radiation fields: a lower $G_0$ version of high-redshift SMGs. These features suggest that these star-forming galaxies similar gas density to SMGs but smaller sizes.

$\bullet$ We estimate neutral atomic oxygen masses using observed \[O i\] $145\,{\rm \mu m}$ emission luminosities while the derived values have large uncertainties of unknown individual $T_{\rm ex}$. Then, by combining oxygen abundances recently obtained in recent JWST spectroscopy, we derive the mass of neutral hydrogen that resides in the same region (atomic and molecular gas) as neutral atomic oxygen. The derived hydrogen masses are generally consistent with those derived using \[C ii\] $158\,{\rm \mu m}$ emission lines. The estimated gas mass ratios ($M_{\rm H}/(M_{\ast}+M_{\rm H})$) range from 0.3 to 0.8, which is consistent with those derived in other studies at $4<z<8$. These observations and analyses show that directly converting oxygen masses to hydrogen masses using JWST-derived oxygen abundances might be possible and could be a direct method to derive hydrogen masses in neutral gas regions.

The rapid progress of JWST observations opened a new era for galaxy studies in the EoR by finding large numbers of galaxies in the heart of cosmic reionization and by enabling observations of their rest-frame optical wavelength. To fully understand galaxy growth at high redshift, however, observations of neutral gas and cold ISM tracers are essential and such observations are only possible using mm/submm facilities such as ALMA. Through the first detections of \[O i\] $145\,{\rm \mu m}$ from star-forming galaxies in the EoR that are more representative of the typical galaxy population than SMGs or QSOs, our pilot observations demonstrate how multi-line observations in FIR wavelength enable our access to gas properties in neutral gas regions. Future surveys at FIR wavelengths, particularly \[O i\] emission lines, in conjunction with JWST observations will allow us to analyze multiple phases of gas, stars, and dust directly in high-redshift galaxies.

We thank Carmen Blanco-Prieto, Javier Arvarez-Marquez, Luis Colina, and the team of JWST observation (GO-1840) for important discussions about the JWST observations of A1689-zD1. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.00446.S ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. YF, YS, and AKI acknowledge support from NAOJ ALMA Scientific Research Grant number 2020-16B. This work was supported by JSPS KAKENHI Grant Numbers JP22K21349 and JP23K13149. PD acknowledges support from the NWO grant 016.VIDI.189.162 (“ODIN") and from the European Commission’s and University of Groningen’s CO-FUND Rosalind Franklin program. HI and HSBA acknowledge support from the NAOJ ALMA Scientific Research Grant Code 2021-19A. HI acknowledges support from JSPS KAKENHI Grant Number JP19K23462. RAAB acknowledges support from an STFC Ernest Rutherford Fellowship \[grant number ST/T003596/1\]. S.F. akcnowledges the funding from NASA through the NASA Hubble Fellowship grant #HST-HF2-51505.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Incorporated, under NASA contract NAS5-26555. MA is supported by FONDECYT grant number 1252054, and gratefully acknowledges support from ANID Basal Project FB210003 and ANID MILENIO NCN2024_112

# Facilities

ALMA, VISTA, HST

# Software

astropy (cite: Astropy), Cloudy (cite: Ferland2017)

# Gravitational Lens Model of Abell 1689

Within the selected targets, A1689-zD1 is strongly lensed by the foreground galaxy cluster the Abell 1689. The magnification factor of A1689-zD1 is presented in (cite: Watson2015) using the pioneering mass modeling of the Abell 1689 (cite: Broadhurst2005; Limousin2007). Since then, new spectroscopy data are published and redshifts of several multiple images are updated (cite: Bina2016). Thus, we re-analyze the mass model of Abell 1689 using the updated multiple image data and using an updated lens modeling code.

Using the public code (cite: Oguri2010; Oguri2021), we estimate the mass model of the Abell 1689 cluster using the public multiple image catalogs (cite: Coe2010; Ghosh2023) removing unsecure multiple images.

Some of the spectroscopic redshifts of the multiple images are obtained using the MUSE observation results (cite: Bina2016). We used 130 multiple images of 40 source galaxies, 14 of which have spectroscopic redshifts. The cluster is modeled with the five Navarro-Frenk-White (NFW) components with a fast approximation (cite: Oguri2021), cluster galaxies (cite: Coe2010), and external shear, and $m=3$ and $4$ multipole perturbations (cite: Oguri2010). We then run software to find the minimum $\chi^2$ assuming positional errors of $0.8\ensuremath{''}$ for multiple image positions. The relatively large positional errors reflect the fact that Abell 1689 is one of the most massive clusters in the Universe with the highly complex mass distribution. The root-mean-square of differences between observed and model-predicted multiple image positions is $0.64\ensuremath{''}$ for the best-fitting model.

From the updated mass model, we find a magnification factor for A1689-zD1 to be $\mu=4.14 \pm 0.36$, which is smaller than that previously reported (cite: Broadhurst2005; Watson2015). The error is calculated using MCMC calculation around the best-fit solutions.

Although the magnification factor is relatively uncertain due to the complex structure of the Abell 1689 cluster, we applied a gravitational lensing magnification of $\mu=4.14$ as our fiducial value throughout this study. The exact value of the magnification factor does not strongly affect our conclusion, as the main focus of this study is line ratios.

# Dust continuum detections

Here, we summarize images of dust continuum map of the $\lambda_{\rm rest}=145\,{\rm \mu m}$ and $\lambda_{\rm rest}=205\,{\rm \mu m}$ data of the target galaxies. All the dust continua are detected with $>8\,\sigma$ (Figure [6](#fig:continuum)). Measured fluxes are summarized in Table [\[tab:ALMAmeasurements\]](#tab:ALMAmeasurements).

![](Continuum.v1.pdf)

natexlab

(ref: Akins2022) Akins, H. B., Fujimoto, S., Finlator, K., et al. 2022, ApJ, 934, 64, doi: [`10.3847/1538-4357/ac795b`](http://doi.org/10.3847/1538-4357/ac795b)

(ref: Algera2023) Algera, H. S. B., Inami, H., Sommovigo, L., et al. 2023, MNRAS, doi: [`10.1093/mnras/stad3111`](http://doi.org/10.1093/mnras/stad3111)

(ref: Algera2024) —. 2024, MNRAS, 527, 6867, doi: [`10.1093/mnras/stad3111`](http://doi.org/10.1093/mnras/stad3111)

(ref: Aravena2023) Aravena, M., Heintz, K. E., Dessauges-Zavadsky, M., et al. 2023, arXiv e-prints, arXiv:2309.15948, doi: [`10.48550/arXiv.2309.15948`](http://doi.org/10.48550/arXiv.2309.15948)

(ref: Astropy) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Bakx2021) Bakx, T. J. L. C., Sommovigo, L., Carniani, S., et al. 2021, MNRAS, 508, L58, doi: [`10.1093/mnrasl/slab104`](http://doi.org/10.1093/mnrasl/slab104)

(ref: Bethermin2016) Béthermin, M., De Breuck, C., Gullberg, B., et al. 2016, A&A, 586, L7, doi: [`10.1051/0004-6361/201527739`](http://doi.org/10.1051/0004-6361/201527739)

(ref: Bina2016) Bina, D., Pelló, R., Richard, J., et al. 2016, A&A, 590, A14, doi: [`10.1051/0004-6361/201527913`](http://doi.org/10.1051/0004-6361/201527913)

(ref: Bothwell2017) Bothwell, M. S., Aguirre, J. E., Aravena, M., et al. 2017, MNRAS, 466, 2825, doi: [`10.1093/mnras/stw3270`](http://doi.org/10.1093/mnras/stw3270)

(ref: Bouwens2015) Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2015, ApJ, 803, 34, doi: [`10.1088/0004-637X/803/1/34`](http://doi.org/10.1088/0004-637X/803/1/34)

(ref: Bouwens2022) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931, 160, doi: [`10.3847/1538-4357/ac5a4a`](http://doi.org/10.3847/1538-4357/ac5a4a)

(ref: Bradley2008) Bradley, L. D., Bouwens, R. J., Ford, H. C., et al. 2008, ApJ, 678, 647, doi: [`10.1086/533519`](http://doi.org/10.1086/533519)

(ref: Brauher2008) Brauher, J. R., Dale, D. A., & Helou, G. 2008, ApJS, 178, 280, doi: [`10.1086/590249`](http://doi.org/10.1086/590249)

(ref: Broadhurst2005) Broadhurst, T., Benı́tez, N., Coe, D., et al. 2005, ApJ, 621, 53, doi: [`10.1086/426494`](http://doi.org/10.1086/426494)

(ref: Cameron2023) Cameron, A. J., Saxena, A., Bunker, A. J., et al. 2023, A&A, 677, A115, doi: [`10.1051/0004-6361/202346107`](http://doi.org/10.1051/0004-6361/202346107)

(ref: Carilli2013) Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105, doi: [`10.1146/annurev-astro-082812-140953`](http://doi.org/10.1146/annurev-astro-082812-140953)

(ref: Carniani2020) Carniani, S., Ferrara, A., Maiolino, R., et al. 2020, MNRAS, 499, 5136, doi: [`10.1093/mnras/staa3178`](http://doi.org/10.1093/mnras/staa3178)

(ref: Carniani2024) Carniani, S., Hainline, K., D’Eugenio, F., et al. 2024, arXiv e-prints, arXiv:2405.18485, doi: [`10.48550/arXiv.2405.18485`](http://doi.org/10.48550/arXiv.2405.18485)

(ref: Bean2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Coe2010) Coe, D., Benı́tez, N., Broadhurst, T., & Moustakas, L. A. 2010, ApJ, 723, 1678, doi: [`10.1088/0004-637X/723/2/1678`](http://doi.org/10.1088/0004-637X/723/2/1678)

(ref: Cormier2015) Cormier, D., Madden, S. C., Lebouteiller, V., et al. 2015, A&A, 578, A53, doi: [`10.1051/0004-6361/201425207`](http://doi.org/10.1051/0004-6361/201425207)

(ref: Croxall2017) Croxall, K. V., Smith, J. D., Pellegrini, E., et al. 2017, ApJ, 845, 96, doi: [`10.3847/1538-4357/aa8035`](http://doi.org/10.3847/1538-4357/aa8035)

(ref: Cunningham2020) Cunningham, D. J. M., Chapman, S. C., Aravena, M., et al. 2020, MNRAS, 494, 4090, doi: [`10.1093/mnras/staa820`](http://doi.org/10.1093/mnras/staa820)

(ref: Davies2003) Davies, R. I., Sternberg, A., Lehnert, M., & Tacconi-Garman, L. E. 2003, ApJ, 597, 907, doi: [`10.1086/378634`](http://doi.org/10.1086/378634)

(ref: Dayal2018) Dayal, P., & Ferrara, A. 2018, Phys. Rep., 780, 1, doi: [`10.1016/j.physrep.2018.10.002`](http://doi.org/10.1016/j.physrep.2018.10.002)

(ref: DeBreuck2019) De Breuck, C., Weiß, A., Béthermin, M., et al. 2019, A&A, 631, A167, doi: [`10.1051/0004-6361/201936169`](http://doi.org/10.1051/0004-6361/201936169)

(ref: Decarli2014) Decarli, R., Walter, F., Carilli, C., et al. 2014, ApJL, 782, L17, doi: [`10.1088/2041-8205/782/2/L17`](http://doi.org/10.1088/2041-8205/782/2/L17)

(ref: Decarli2023) Decarli, R., Pensabene, A., Diaz-Santos, T., et al. 2023, A&A, 673, A157, doi: [`10.1051/0004-6361/202245674`](http://doi.org/10.1051/0004-6361/202245674)

(ref: Dessauges2020) Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643, A5, doi: [`10.1051/0004-6361/202038231`](http://doi.org/10.1051/0004-6361/202038231)

(ref: Diaz-Santos2017) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32, doi: [`10.3847/1538-4357/aa81d7`](http://doi.org/10.3847/1538-4357/aa81d7)

(ref: Faisst2020) Faisst, A. L., Fudamoto, Y., Oesch, P. A., et al. 2020, MNRAS, 498, 4192, doi: [`10.1093/mnras/staa2545`](http://doi.org/10.1093/mnras/staa2545)

(ref: Farrah2013) Farrah, D., Lebouteiller, V., Spoon, H. W. W., et al. 2013, ApJ, 776, 38, doi: [`10.1088/0004-637X/776/1/38`](http://doi.org/10.1088/0004-637X/776/1/38)

(ref: Ferland2017) Ferland, G. J., Chatzikos, M., Guzmán, F., et al. 2017, , 53, 385, doi: [`10.48550/arXiv.1705.10877`](http://doi.org/10.48550/arXiv.1705.10877)

(ref: 2024A&A...682A.166F) Fernández Aranda, R., Dı́az Santos, T., Hatziminaoglou, E., et al. 2024, A&A, 682, A166, doi: [`10.1051/0004-6361/202347869`](http://doi.org/10.1051/0004-6361/202347869)

(ref: Fernandez-Ontiveros2016) Fernández-Ontiveros, J. A., Spinoglio, L., Pereira-Santaella, M., et al. 2016, ApJS, 226, 19, doi: [`10.3847/0067-0049/226/2/19`](http://doi.org/10.3847/0067-0049/226/2/19)

(ref: Ferrara2019) Ferrara, A., Vallini, L., Pallottini, A., et al. 2019, MNRAS, 489, 1, doi: [`10.1093/mnras/stz2031`](http://doi.org/10.1093/mnras/stz2031)

(ref: Finkelstein2023) Finkelstein, S. L., Bagley, M. B., Ferguson, H. C., et al. 2023, ApJL, 946, L13, doi: [`10.3847/2041-8213/acade4`](http://doi.org/10.3847/2041-8213/acade4)

(ref: Fudamoto2023) Fudamoto, Y., Inoue, A. K., & Sugahara, Y. 2023, MNRAS, 521, 2962, doi: [`10.1093/mnras/stad743`](http://doi.org/10.1093/mnras/stad743)

(ref: Fujimoto2022) Fujimoto, S., Ouchi, M., Nakajima, K., et al. 2022, arXiv e-prints, arXiv:2212.06863, doi: [`10.48550/arXiv.2212.06863`](http://doi.org/10.48550/arXiv.2212.06863)

(ref: Fujimoto2023) Fujimoto, S., Arrabal Haro, P., Dickinson, M., et al. 2023, ApJL, 949, L25, doi: [`10.3847/2041-8213/acd2d9`](http://doi.org/10.3847/2041-8213/acd2d9)

(ref: Ghosh2023) Ghosh, A., Adams, D., Williams, L. L. R., et al. 2023, MNRAS, 525, 2519, doi: [`10.1093/mnras/stad2418`](http://doi.org/10.1093/mnras/stad2418)

(ref: Habing1968) Habing, H. J. 1968, , 19, 421

(ref: 2010ApJ...714L.162H) Hailey-Dunsheath, S., Nikola, T., Stacey, G. J., et al. 2010, ApJL, 714, L162, doi: [`10.1088/2041-8205/714/1/L162`](http://doi.org/10.1088/2041-8205/714/1/L162)

(ref: Harikane2020) Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ, 896, 93, doi: [`10.3847/1538-4357/ab94bd`](http://doi.org/10.3847/1538-4357/ab94bd)

(ref: Harikane2023) Harikane, Y., Ouchi, M., Oguri, M., et al. 2023, ApJS, 265, 5, doi: [`10.3847/1538-4365/acaaa9`](http://doi.org/10.3847/1538-4365/acaaa9)

(ref: Hashimoto2019) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, PASJ, 71, 71, doi: [`10.1093/pasj/psz049`](http://doi.org/10.1093/pasj/psz049)

(ref: Heintz22) Heintz, K. E., Oesch, P. A., Aravena, M., et al. 2022, ApJL, 934, L27, doi: [`10.3847/2041-8213/ac8057`](http://doi.org/10.3847/2041-8213/ac8057)

(ref: Heintz2023) Heintz, K. E., Watson, D., Brammer, G., et al. 2023a, arXiv e-prints, arXiv:2306.00647, doi: [`10.48550/arXiv.2306.00647`](http://doi.org/10.48550/arXiv.2306.00647)

(ref: Heintz2023b) Heintz, K. E., Giménez-Arteaga, C., Fujimoto, S., et al. 2023b, ApJL, 944, L30, doi: [`10.3847/2041-8213/acb2cf`](http://doi.org/10.3847/2041-8213/acb2cf)

(ref: Heintz23c) Heintz, K. E., Shapley, A. E., Sanders, R. L., et al. 2023c, A&A, 678, A30, doi: [`10.1051/0004-6361/202346573`](http://doi.org/10.1051/0004-6361/202346573)

(ref: Herrera-Camus2018) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018, ApJ, 861, 94, doi: [`10.3847/1538-4357/aac0f6`](http://doi.org/10.3847/1538-4357/aac0f6)

(ref: Hodge2020) Hodge, J. A., & da Cunha, E. 2020, Royal Society Open Science, 7, 200556, doi: [`10.1098/rsos.200556`](http://doi.org/10.1098/rsos.200556)

(ref: Hygate2023) Hygate, A. P. S., Hodge, J. A., da Cunha, E., et al. 2023, MNRAS, 524, 1775, doi: [`10.1093/mnras/stad1212`](http://doi.org/10.1093/mnras/stad1212)

(ref: Inami2022) Inami, H., Algera, H. S. B., Schouws, S., et al. 2022, MNRAS, 515, 3126, doi: [`10.1093/mnras/stac1779`](http://doi.org/10.1093/mnras/stac1779)

(ref: Inoue2020) Inoue, A. K., Hashimoto, T., Chihara, H., & Koike, C. 2020, MNRAS, 495, 1577, doi: [`10.1093/mnras/staa1203`](http://doi.org/10.1093/mnras/staa1203)

(ref: Kaufman1999) Kaufman, M. J., Wolfire, M. G., Hollenbach, D. J., & Luhman, M. L. 1999, ApJ, 527, 795, doi: [`10.1086/308102`](http://doi.org/10.1086/308102)

(ref: Killi2023) Killi, M., Watson, D., Fujimoto, S., et al. 2023, MNRAS, 521, 2526, doi: [`10.1093/mnras/stad687`](http://doi.org/10.1093/mnras/stad687)

(ref: Lee2021) Lee, M. M., Nagao, T., De Breuck, C., et al. 2021, ApJ, 913, 41, doi: [`10.3847/1538-4357/abe7ea`](http://doi.org/10.3847/1538-4357/abe7ea)

(ref: Li2020) Li, J., Wang, R., Cox, P., et al. 2020, ApJ, 900, 131, doi: [`10.3847/1538-4357/ababac`](http://doi.org/10.3847/1538-4357/ababac)

(ref: Limousin2007) Limousin, M., Richard, J., Jullo, E., et al. 2007, ApJ, 668, 643, doi: [`10.1086/521293`](http://doi.org/10.1086/521293)

(ref: Litke2023) Litke, K. C., Marrone, D. P., Aravena, M., et al. 2023, ApJ, 949, 87, doi: [`10.3847/1538-4357/acc93a`](http://doi.org/10.3847/1538-4357/acc93a)

(ref: Lupi2020) Lupi, A., & Bovino, S. 2020, MNRAS, 492, 2818, doi: [`10.1093/mnras/staa048`](http://doi.org/10.1093/mnras/staa048)

(ref: Madau2014) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: Malhotra2001) Malhotra, S., Kaufman, M. J., Hollenbach, D., et al. 2001, ApJ, 561, 766, doi: [`10.1086/323046`](http://doi.org/10.1086/323046)

(ref: Markov2022) Markov, V., Carniani, S., Vallini, L., et al. 2022, A&A, 663, A172, doi: [`10.1051/0004-6361/202243336`](http://doi.org/10.1051/0004-6361/202243336)

(ref: McCracken2012) McCracken, H. J., Milvang-Jensen, B., Dunlop, J., et al. 2012, A&A, 544, A156, doi: [`10.1051/0004-6361/201219507`](http://doi.org/10.1051/0004-6361/201219507)

(ref: Meyer2022) Meyer, R. A., Walter, F., Cicone, C., et al. 2022, ApJ, 927, 152, doi: [`10.3847/1538-4357/ac4e94`](http://doi.org/10.3847/1538-4357/ac4e94)

(ref: Naidu2022) Naidu, R. P., Oesch, P. A., van Dokkum, P., et al. 2022, ApJL, 940, L14, doi: [`10.3847/2041-8213/ac9b22`](http://doi.org/10.3847/2041-8213/ac9b22)

(ref: Novak2019) Novak, M., Bañados, E., Decarli, R., et al. 2019, ApJ, 881, 63, doi: [`10.3847/1538-4357/ab2beb`](http://doi.org/10.3847/1538-4357/ab2beb)

(ref: Novak2020) Novak, M., Venemans, B. P., Walter, F., et al. 2020, ApJ, 904, 131, doi: [`10.3847/1538-4357/abc33f`](http://doi.org/10.3847/1538-4357/abc33f)

(ref: Oberst2011) Oberst, T. E., Parshley, S. C., Nikola, T., et al. 2011, ApJ, 739, 100, doi: [`10.1088/0004-637X/739/2/100`](http://doi.org/10.1088/0004-637X/739/2/100)

(ref: Oesch2018) Oesch, P. A., Bouwens, R. J., Illingworth, G. D., Labbé, I., & Stefanon, M. 2018, ApJ, 855, 105, doi: [`10.3847/1538-4357/aab03f`](http://doi.org/10.3847/1538-4357/aab03f)

(ref: Oesch2023) Oesch, P. A., Brammer, G., Naidu, R. P., et al. 2023, MNRAS, 525, 2864, doi: [`10.1093/mnras/stad2411`](http://doi.org/10.1093/mnras/stad2411)

(ref: Oguri2010) Oguri, M. 2010, PASJ, 62, 1017, doi: [`10.1093/pasj/62.4.1017`](http://doi.org/10.1093/pasj/62.4.1017)

(ref: Oguri2021) —. 2021, PASP, 133, 074504, doi: [`10.1088/1538-3873/ac12db`](http://doi.org/10.1088/1538-3873/ac12db)

(ref: Pallottini2017) Pallottini, A., Ferrara, A., Bovino, S., et al. 2017, MNRAS, 471, 4128, doi: [`10.1093/mnras/stx1792`](http://doi.org/10.1093/mnras/stx1792)

(ref: pallottini:2022) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2022, MNRAS, 513, 5621, doi: [`10.1093/mnras/stac1281`](http://doi.org/10.1093/mnras/stac1281)

(ref: Pavesi2019) Pavesi, R., Riechers, D. A., Faisst, A. L., Stacey, G. J., & Capak, P. L. 2019, ApJ, 882, 168, doi: [`10.3847/1538-4357/ab3a46`](http://doi.org/10.3847/1538-4357/ab3a46)

(ref: Pavesi2016) Pavesi, R., Riechers, D. A., Capak, P. L., et al. 2016, ApJ, 832, 151, doi: [`10.3847/0004-637X/832/2/151`](http://doi.org/10.3847/0004-637X/832/2/151)

(ref: Pensabene2021) Pensabene, A., Decarli, R., Bañados, E., et al. 2021, A&A, 652, A66, doi: [`10.1051/0004-6361/202039696`](http://doi.org/10.1051/0004-6361/202039696)

(ref: Riechers2009) Riechers, D. A., Walter, F., Bertoldi, F., et al. 2009, ApJ, 703, 1338, doi: [`10.1088/0004-637X/703/2/1338`](http://doi.org/10.1088/0004-637X/703/2/1338)

(ref: Rieke2023) Rieke, M. J., Robertson, B., Tacchella, S., et al. 2023, ApJS, 269, 16, doi: [`10.3847/1538-4365/acf44d`](http://doi.org/10.3847/1538-4365/acf44d)

(ref: Robertson2023) Robertson, B., Johnson, B. D., Tacchella, S., et al. 2023, arXiv e-prints, arXiv:2312.10033, doi: [`10.48550/arXiv.2312.10033`](http://doi.org/10.48550/arXiv.2312.10033)

(ref: Robertson2022) Robertson, B. E. 2022, ARA&A, 60, 121, doi: [`10.1146/annurev-astro-120221-044656`](http://doi.org/10.1146/annurev-astro-120221-044656)

(ref: Rosenberg2015) Rosenberg, M. J. F., van der Werf, P. P., Aalto, S., et al. 2015, ApJ, 801, 72, doi: [`10.1088/0004-637X/801/2/72`](http://doi.org/10.1088/0004-637X/801/2/72)

(ref: Rowland2024) Rowland, L. E., Hodge, J., Bouwens, R., et al. 2024, arXiv e-prints, arXiv:2405.06025, doi: [`10.48550/arXiv.2405.06025`](http://doi.org/10.48550/arXiv.2405.06025)

(ref: Rowland2025) Rowland, L. E., Stefanon, M., Bouwens, R., et al. 2025, arXiv e-prints, arXiv:2501.10559, doi: [`10.48550/arXiv.2501.10559`](http://doi.org/10.48550/arXiv.2501.10559)

(ref: Schaerer2020) Schaerer, D., Ginolfi, M., Béthermin, M., et al. 2020, A&A, 643, A3, doi: [`10.1051/0004-6361/202037617`](http://doi.org/10.1051/0004-6361/202037617)

(ref: Schouws2022) Schouws, S., Stefanon, M., Bouwens, R., et al. 2022, ApJ, 928, 31, doi: [`10.3847/1538-4357/ac4605`](http://doi.org/10.3847/1538-4357/ac4605)

(ref: Schouws2023) Schouws, S., Bouwens, R., Smit, R., et al. 2023, ApJ, 954, 103, doi: [`10.3847/1538-4357/ace10c`](http://doi.org/10.3847/1538-4357/ace10c)

(ref: Schouws2025) Schouws, S., Bouwens, R. J., Algera, H., et al. 2025, arXiv e-prints, arXiv:2502.01610, doi: [`10.48550/arXiv.2502.01610`](http://doi.org/10.48550/arXiv.2502.01610)

(ref: Schreiber2018) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30, doi: [`10.1051/0004-6361/201731506`](http://doi.org/10.1051/0004-6361/201731506)

(ref: Schreiber2021) Schreiber, C., Glazebrook, K., Papovich, C., et al. 2021, A&A, 650, C2, doi: [`10.1051/0004-6361/201936460e`](http://doi.org/10.1051/0004-6361/201936460e)

(ref: Smit2018) Smit, R., Bouwens, R. J., Carniani, S., et al. 2018, Nature, 553, 178, doi: [`10.1038/nature24631`](http://doi.org/10.1038/nature24631)

(ref: Sommovigo2022) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022, MNRAS, 513, 3122, doi: [`10.1093/mnras/stac302`](http://doi.org/10.1093/mnras/stac302)

(ref: Spinoglio2015) Spinoglio, L., Pereira-Santaella, M., Dasyra, K. M., et al. 2015, ApJ, 799, 21, doi: [`10.1088/0004-637X/799/1/21`](http://doi.org/10.1088/0004-637X/799/1/21)

(ref: Stacey1991) Stacey, G. J., Geis, N., Genzel, R., et al. 1991, ApJ, 373, 423, doi: [`10.1086/170062`](http://doi.org/10.1086/170062)

(ref: Stacey2010) Stacey, G. J., Hailey-Dunsheath, S., Ferkinhoff, C., et al. 2010, ApJ, 724, 957, doi: [`10.1088/0004-637X/724/2/957`](http://doi.org/10.1088/0004-637X/724/2/957)

(ref: Sugahara2022) Sugahara, Y., Inoue, A. K., Fudamoto, Y., et al. 2022, ApJ, 935, 119, doi: [`10.3847/1538-4357/ac7fed`](http://doi.org/10.3847/1538-4357/ac7fed)

(ref: Sugahara2021) Sugahara, Y., Inoue, A. K., Hashimoto, T., et al. 2021, ApJ, 923, 5, doi: [`10.3847/1538-4357/ac2a36`](http://doi.org/10.3847/1538-4357/ac2a36)

(ref: Tielens1985) Tielens, A. G. G. M., & Hollenbach, D. 1985, ApJ, 291, 722, doi: [`10.1086/163111`](http://doi.org/10.1086/163111)

(ref: Topping2022) Topping, M. W., Stark, D. P., Endsley, R., et al. 2022, MNRAS, 516, 975, doi: [`10.1093/mnras/stac2291`](http://doi.org/10.1093/mnras/stac2291)

(ref: Vallini2021) Vallini, L., Ferrara, A., Pallottini, A., Carniani, S., & Gallerani, S. 2021, MNRAS, 505, 5543, doi: [`10.1093/mnras/stab1674`](http://doi.org/10.1093/mnras/stab1674)

(ref: Vallini2017) Vallini, L., Ferrara, A., Pallottini, A., & Gallerani, S. 2017, MNRAS, 467, 1300, doi: [`10.1093/mnras/stx180`](http://doi.org/10.1093/mnras/stx180)

(ref: Vallini2024) Vallini, L., Witstok, J., Sommovigo, L., et al. 2024, MNRAS, 527, 10, doi: [`10.1093/mnras/stad3150`](http://doi.org/10.1093/mnras/stad3150)

(ref: Wang2024) Wang, B., Leja, J., Labbé, I., et al. 2024, ApJS, 270, 12, doi: [`10.3847/1538-4365/ad0846`](http://doi.org/10.3847/1538-4365/ad0846)

(ref: Watson2015) Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327, doi: [`10.1038/nature14164`](http://doi.org/10.1038/nature14164)

(ref: Weaver2023) Weaver, J. R., Davidzon, I., Toft, S., et al. 2023, A&A, 677, A184, doi: [`10.1051/0004-6361/202245581`](http://doi.org/10.1051/0004-6361/202245581)

(ref: Weiss2003) Weiß, A., Henkel, C., Downes, D., & Walter, F. 2003, A&A, 409, L41, doi: [`10.1051/0004-6361:20031337`](http://doi.org/10.1051/0004-6361:20031337)

(ref: Weiss2005) Weiß, A., Walter, F., & Scoville, N. Z. 2005, A&A, 438, 533, doi: [`10.1051/0004-6361:20052667`](http://doi.org/10.1051/0004-6361:20052667)

(ref: Williams2023) Williams, C. C., Alberts, S., Ji, Z., et al. 2023, arXiv e-prints, arXiv:2311.07483, doi: [`10.48550/arXiv.2311.07483`](http://doi.org/10.48550/arXiv.2311.07483)

(ref: Wilson2023) Wilson, S. N., Heintz, K. E., Jakobsson, P., et al. 2023, arXiv e-prints, arXiv:2305.05213, doi: [`10.48550/arXiv.2305.05213`](http://doi.org/10.48550/arXiv.2305.05213)

(ref: Witstok2022) Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS, 515, 1751, doi: [`10.1093/mnras/stac1905`](http://doi.org/10.1093/mnras/stac1905)

(ref: Wong2022) Wong, Y. H. V., Wang, P., Hashimoto, T., et al. 2022, ApJ, 929, 161, doi: [`10.3847/1538-4357/ac5cc7`](http://doi.org/10.3847/1538-4357/ac5cc7)

(ref: Yang2019) Yang, J., Venemans, B., Wang, F., et al. 2019, ApJ, 880, 153, doi: [`10.3847/1538-4357/ab2a02`](http://doi.org/10.3847/1538-4357/ab2a02)

(ref: Zanella2018) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976, doi: [`10.1093/mnras/sty2394`](http://doi.org/10.1093/mnras/sty2394)

[^1]: Throughout this work, $L_{\rm IR}$ are calculated using the rest-frame wavelength range of $8-1000\,{\rm \mu m}$.

[^2]: The critical density of \[C ii\] $158\,{\rm \mu m}$ emission is $\sim50\,{\rm cm^{-3}}$ and $\sim3\times10^{3}\,{\rm cm^{-3}}$ when the collision pair is the electron and the hydrogen atom/molecule, respectively (cite: Stacey2010; Carilli2013).

[^3]: We allowed the ionizing radiation fully absorbed by a large column of gas ($N{\rm(H)}=10^{24}\,{\rm cm^{-2}}$) without any leakage using the input of `extinguish by 24 leakage=0`.

[^4]: We publish input files and output grids of our cloudy run:<https://github.com/yfudamoto/Fudamoto_OI_cloudy.git>

[^5]: FUV intensity ($G_0$) and gas density ($n$) scales as $G_{\rm 0}\propto L/R^2$ and $n\propto M/R^3$, respectively, where $M$, $L$, and $R$ are the mass, the luminosity, and the size of the system. Assuming $L\propto M$ and assuming that $M$ and $L$ of starburst galaxies and star-forming galaxies are different by a factor of $f$ and the gas densities are same (i.e., $n_{\rm SB} = n_{\rm SFG}$, $L_{\rm SB}=f\,L_{\rm SFG}$, and $M_{\rm SB}=f\,M_{\rm SFG}$), we can find that $G_0$ scales as $f^{1/3}$.

[^6]: \[O i\] $145\,{\rm \mu m}$ emission is optically thin in a wide range of parameter space (cite: Kaufman1999).

[^7]: $12+{\rm log(O/H)}= 8.45$, $8.05$, $8.63$, and $8.53$ for REBELS-38, A1689-zD1, REBELS-25, and REBELS-18, respectively

</paper>

Write the methods card for this paper.