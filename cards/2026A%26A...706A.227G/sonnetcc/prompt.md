# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026A%26A...706A.227G\sonnetcc\reply.txt

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
 "bibcode": "2026A&A...706A.227G",
 "title": "The CON-quasar stage of IRAS 07251−0248 E",
 "year": 2026,
 "journal": "Astronomy and Astrophysics",
 "first_author": "González-Alfonso, Eduardo",
 "n_authors": 5,
 "arxiv_id": "2602.04997",
 "doi": "10.1051/0004-6361/202556762",
 "alma_projects_linked_by_archive": [
  "2023.1.00942.S"
 ]
}
```

Paper text:
<paper>
# The CON-quasar stage of IRAS 07251$-$0248 E

# Introduction

Compact obscured nuclei (cite: fal21), are bright $<100$ pc galaxy nuclei with extremely high column densities ($N_{\mathrm{H_2}}\gtrsim10^{25}$ cm$^{-2}$). They have been mostly identified via the detection of HCN vibrational emission in the millimeter (cite: aal15; fal19), by molecular lines in absorption in the far-infrared (cite: gon04; gon15), and through the PAH equivalent width method (cite: gber22b; gber25b). Their power source is however hard to establish due to the high nuclear extinction. Even the luminosity arising from these nuclei is difficult to establish from millimeter continuum and lines observed with high-resolution, because trapping of dust emitted photons increases the dust temperature ($T_d$) within the nucleus (cite: gon19) and the luminosity depends on $T_d$ at the nuclear surface (the “photosphere”), which is better probed with molecular absorption lines. Nevertheless, there is growing evidence that CONs typically harbor an active galactic nucleus (AGN) based on the extremely compact millimeter continuum emission as compared with the more extended gas mass distribution, as observed with ALMA (cite: per21). Still, accurate IR to millimeter continuum models together with detailed analysis of the hottest dust mid-IR emission from CONs are scarce.

Here we combine ALMA, *James Webb Space Telescope (JWST)*, and *Herschel* observations of the eastern (E) nucleus of IRAS 07251$-$0248 to model its continuum emission from the mid-IR to submillimeter (submm) wavelengths. IRAS 07251$-$0248 is a merging ultraluminous infrared galaxy (ULIRG) with an IR (6-1500 $\mu$m) luminosity of $10^{12.45}\,L_{\odot}$ and nuclear separation of $\sim1.8$ kpc (cite: lam22); its E-nucleus dominates the total luminosity, contributing 91% (cite: per21). There are no reported observations of HCN vibrational emission from the galaxy, but there are other significant indications that it harbors a CON from the strong absorption in the OH 65 $\mu$m doublet (cite: gon15), the 6.2/3.3 $\mu$m PAH equivalent-width ratio (cite: gber25b), and the absorption below the continuum in the blueshifted wing of the CO 2-1 line (cite: lam22). IRAS 07251$-$0248 is very faint in the *Chandra* soft X-ray band ($0.5-2$ keV) and undetected in the hard bands of *Chandra* (cite: iwa11) and *NuSTAR* (cite: ric21). On the other hand, *JWST* observations have recently shown that the source has a nuclear cosmic-ray dominated chemistry as derived from the high abundances of H$_3^+$ (cite: per24), hydrocarbons (cite: gber25), and molecular cations (cite: spe25). We adopt luminosity and angular distances of $D_L=400$ Mpc and $D_A=339$ Mpc (scale of $1.64\,\mathrm{pc/mas}$), respectively.

![](alma_data_07251-0248E_gp.pdf)

![](iras07251_sed_isel20.pdf)

# Observations and results

## ALMA observations of the 667 $\mu$m continuum and model

+-------------------+-----------------+-------+---+---+---+---+---+---+
| Parameter         | Value           | Units |   |   |   |   |   |   |
+:==================+:===============:+:=====:+:=:+:=:+:=:+:=:+:=:+:=:+
| R.A. $^{a}$       | 7h27m37.5368s   |       |   |   |   |   |   |   |
+-------------------+-----------------+-------+---+---+---+---+---+---+
| Dec. $^{a}$       | $-$2d54m54.267s |       |   |   |   |   |   |   |
+-------------------+-----------------+-------+---+---+---+---+---+---+
| $\chi^2$          | 1.20            |       |   |   |   |   |   |   |
+-------------------+-----------------+-------+---+---+---+---+---+---+
| Point-source                                |   |   |   |   |   |   |
+-------------------+-----------------+-------+---+---+---+---+---+---+
| Flux density      | 18.4 $\pm$ 1.0  | mJy   |   |   |   |   |   |   |
+-------------------+-----------------+-------+---+---+---+---+---+---+
| Gaussian                                    |   |   |   |   |   |   |
+-------------------+-----------------+-------+---+---+---+---+---+---+
| FWHM major $^{b}$ | 89 $\pm$ 4      | mas   |   |   |   |   |   |   |
+-------------------+-----------------+-------+---+---+---+---+---+---+
| FWHM minor $^{b}$ | 86 $\pm$ 5      | mas   |   |   |   |   |   |   |
+-------------------+-----------------+-------+---+---+---+---+---+---+
| P.A.              | $\cdots$        |       |   |   |   |   |   |   |
+-------------------+-----------------+-------+---+---+---+---+---+---+
| Flux density      | 20.8 $\pm$ 0.7  | mJy   |   |   |   |   |   |   |
+-------------------+-----------------+-------+---+---+---+---+---+---+

: Best-fit parameters for the nuclear 667 $\mu$m emission of IRAS 07251$-$0248 E using a point-source $+$ Gaussian model

Table notes:

ALMA observations at $\nu_{\mathrm{obs}}=413.11$ GHz (Band 8, $\lambda_{\mathrm{rest}}=667\,\mu$m) of IRAS 07251$-$0248 E (program 2023.1.00942.S, PI: M. Pereira-Santaella) were carried out on 2023 November 28$^{\mathrm{th}}$ using the 12 m array with high angular resolution ($75\times67\,\mathrm{mas}^2=123\times110$ pc$^2$) and sensitivity (0.2 mJy/beam). Details of the reduction process are given in Appendix [5](#cont667). The map of the $667\,\mu$m continuum (Fig. [1](#almacont)) shows a very bright (peak of $\approx25$ mJy/beam) and compact emission. To derive its size and flux, we used the method described in (cite: per21) and attempted to fit the observed emission with a point-source, a Gaussian, and a point-source and a Gaussian (pG). The best fit, shown in Fig. [1](#almacont)b, was found for the pG model with parameters listed in Table [1](#tab:cont). Appendix [5](#cont667) shows that the point-source and the Gaussian fits can be disregarded.

Owing to the high signal-to-noise ratio of the $667\,\mu$m emission ($>120$), the unresolved source of the pG model could be constrained to have an upper limit for the deconvolved size of $\mathrm{FWHM}\leq21\,\mathrm{mas}=34$ pc, assuming a Gaussian light distribution. Conservatively using the equivalence between a Gaussian source and a disk of uniform brightness (cite: sak08), an upper limit for the nuclear source radius is $R\lesssim27$ pc, yielding a brightness of $T_{\mathrm{B}}\gtrsim190$ K. The $667\,\mu$m emission is entirely attributed to dust, with the optical depth given by $$\begin{equation}
  \tau_{667\mu m}=\ln\left(1-\frac{10^{-22}\lambda_0^2D_L^2\,F_{667\mu m}}{2\pi k (1+z) T_d R^2}\right)^{-1}
  =\ln\left(1-\frac{7546\,F_{667\mu m}}{T_d R^2}\right)^{-1},
\label{eq:tau667}  
\end{equation}$$ where $k$ is the Boltzman constant (in cgs units), $\lambda_0=667$ $\mu$m, $D_L=400$ Mpc, $F_{667\mu m}$ is in mJy, $T_d$ is the dust temperature in K, and the source radius $R$ is in pc. Using $T_d=500$ K, eq. ([\[eq:tau667\]](#eq:tau667)) gives $\tau_{667\mu m}=0.5$ for $R=27$ pc, and has no solution for $R\leq16$ pc. Therefore, the ALMA observations reveal an extremely compact source with a very high column density of hot dust, and will be denoted to as the “hot component” ($H_C$).

For the Gaussian (resolved) continuum source, a size of $\mathrm{FWHM}=89\times86\,\mathrm{mas^2}$ is found, corresponding to a source (most likely a disk or a torus) seen nearly face-on with a radius of $R\approx75$ pc. Equation ([\[eq:tau667\]](#eq:tau667)) gives $\tau_{667\mu m}\approx0.26$ for an adopted $T_d=123$ K (Section [3.1](#contin)). This component will be denoted to as the “warm component” ($W_C$).

The spectral energy distribution (SED) of IRAS 07251$-$0248 E from near-IR to millimeter wavelengths, including *JWST* (Section [2.2](#jwstobs)), *Spitzer*, *Herschel*/PACS and SPIRE, and ALMA data, is shown in Fig. [2](#sed). At 667 $\mu$m, we plot separately the flux densities for the $H_C$ (blue) and $W_C$ (light-blue); the black filled circle is the sum of both and lies below the extrapolation of the *Herschel*/SPIRE data indicating that a fraction of the total 667 $\mu$m emission from the merger is resolved out by ALMA. The continuum measurements at 1.2 mm are included (cite: per21), where the black open circle indicates the unresolved emission ($R<82$ pc, which is large enough to include the emission from the $H_C$ and $W_C$) and the cross indicates the resolved emission ($\sim500\times300$ pc$^2$).

## *JWST* observations of the mid-IR continuum and molecular bands

The *JWST* observations of IRAS 07251$-$0248 E, recently presented by (cite: gber25) and (cite: spe25), were carried out as part of the *JWST* GO Cycle 2 Large Program #ID:3368 (P.I. L. Armus and A. Evans) including NIRSpec and MIRI/MRS integral field spectroscopy of the nucleus. Details of the reduction process are given in Appendix [6](#reduc).

The *JWST* spectrum (Fig. [2](#sed)) is characterized by deep absorption of both solid- and gas-phase bands. Besides the silicate 9.7 $\mu$m and 18 $\mu$m features, there are deep absorption features due to H$_2$O ice at 3 (stretching), 6 (bending), and 13 $\mu$m (libration), and due to hydrogenated amorphous carbon (a-C:H) grains at 6.85 and 7.25 $\mu$m. Superposed on this absorbed continuum, strong gas-phase absorption bands due to CO, CO$_2$, H$_2$O, HCN, and C$_2$H$_2$ are detected, as well as additional weaker bands mostly associated with hydrocarbons (cite: gber25) and molecular cations (cite: spe25). In this absorption-dominated mid-IR spectrum, no high ionization lines directly probing an AGN are detected (cite: spo22). Here we focus on the H$_2$O $\nu_2=1-0$ band at $\sim5.2-7.0$ $\mu$m displayed in Fig. [3](#h2oband), although the HCN, C$_2$H$_2$, CH$_4$, and CO$_2$ bands are also modeled in Appendix [10](#hcnc2h2bands). The H$_2$O $\nu_2=1-0$ band has been previously reported in extragalactic sources by (cite: gber24; gber25; gon24; bui24; bui25). We used the H$_2$O spectroscopic parameters tabulated in the HITRAN2020 database (cite: gor22).

![](iras07251_h2o_isel20.pdf)

The H$_2$O band in IRAS 07251$-$0248 E shows some similarities with, but also important differences from that observed towards the lower luminosity LIRG VV 114 E SW-s2 (cite: gon24). In both sources, the bands are in pure absorption (cite: gber24). However, the continuum-normalized absorption due to low-excitation H$_2$O lines in IRAS 07251$-$0248 E is stronger than in VV 114 (see, e.g., the blended feature at $\approx6.05$ $\mu$m absorbing $\approx70$% of the continuum in IRAS 07251$-$0248 but only $\approx35$% in VV 114). The opposite happens with the very high-excitation H$_2$O lines, which are strong in VV 114 but most of them (above $\sim1500$ K) undetected in IRAS 07251$-$0248 (see also Fig. [8](#h2oprof)), indicating significantly lower excitation in this ULIRG (cite: gber25). Interestingly, both sources show the H$_2$O lines blueshifted by $\sim160$ km s$^{-1}$ relative to the emission lines (Fig. [7](#redshift)), but the blueshift in VV 114 increases with higher line excitation while the opposite happens in IRAS 07251$-$0248 E. Close inspection of the H$_2$O line profiles in Figs. [7](#redshift) and [8](#h2oprof) indicates the presence of two kinematic components, and the most blueshifted one (with absorption at velocities up to $-500$ km s$^{-1}$) is only seen in the low excitation lines.

# A model for the mid-IR to millimeter continuum

## The continuum model

Since ALMA observations at 667 $\mu$m reveal an $H_C$ with an extreme column density of hot dust that is expected to emit in the mid-IR, and *JWST* indeed indicates the presence of a mid-IR component with a high enough column density to generate strong absorption in the molecular bands, our hypothesis here is that both observations trace the same continuum nuclear component (with $R_h\lesssim27$ pc as derived from ALMA). Additional support to this assumption is found in the CO 2-1 230 GHz rotational line profile displayed in Fig. [7](#redshift) (cite: lam22), which shows an asymmetric profile with apparent blueshifted absorption between $-500$ and $-350$ km s$^{-1}$ falling below the continuum: assuming that this absorption is produced by the same gas responsible for the low-excitation H$_2$O absorption found at similar velocities, the continuum behind both CO and H$_2$O line absorption, at $1.3$ mm and $\sim6$ $\mu$m, should arise from the same physical source. In the following, we further explore and test this scenario.

The high optical depth of the $H_C$ in the submm indicates that trapping of continuum photons will raise $T_d$ within the hot nucleus, and we have thus generated a grid of “greenhouse” models using the method described in . AGN models are used here, together with an absorption coefficient of dust at $<10$ $\mu$m similar to that obtained by (cite: fri11) towards the galactic center and an absolute calibration in terms of total hydrogen column density ($N_{\mathrm{H}}$, see Appendix [7](#kabs)) consistent with the results by (cite: pla11). In our continuum models, we include the absorption due to solid-phase silicates, but not due to ices or a:C-H, so that we aim to fit the envelope of the $2.6-8$ $\mu$m continuum (see Fig. [2](#sed)). For simplicity, flat density profiles are used.

The grid of greenhouse models for the $H_C$ covers $\log N_{\mathrm{H}}(\mathrm{cm^{-2}})=24.0-25.6$ and unattenuated luminosities $\log L_{\mathrm{unatt}}(L_{\odot})=11.0-12.6$, both with logarithmic steps of $0.2$[^1]. A set of mid-IR $2.6-11$ $\mu$m continuum points unaffected by ice, a:C-H, or gas-phase bands, together with the flux density at 667 $\mu$m of the $H_C$, are used to find the best-fit model. The unattenuated nuclear emission is extinguished by a layer of foreground cold dust, which is required because the predicted silicate $9.7$ $\mu$m absorption generated by any relevant greenhouse model is found to be much shallower than the observed feature. The fitted parameters are, besides the properties of the greenhouse model ($N_{\mathrm{H}}$ and $L_{\mathrm{unatt}}$), its radius $R_h$ and the optical depth of the foreground layer evaluated at $6$ $\mu$m, $\tau_{6\mu m}^{\mathrm{fg}}$. Our best-fit model for the $H_C$, with parameters listed in Table [\[tab\]](#tab), is shown with a solid-blue line in Fig. [2](#sed); the dashed-blue line indicates the unattenuated emission (i.e., the emission that would be observed without the foreground layer).

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Component | $\log L_{\mathrm{unatt}}$$^{a}$ | $T_{d}$$^{b}$ | $\tau_{\mathrm{6\mu m}}^{\mathrm{int}}$$^{c}$ | $R$$^{d}$ | $\tau_{6\mu m}^{\mathrm{fg}}$$^{e}$ | $\log L_{\mathrm{att}}$$^{f}$ | $\log N_{\mathrm{H_2}}$$^{g}$ | $X_{\mathrm{H_2O}}$$^{h}$ | $\log M_{\mathrm{H_2}}$$^{i}$ | $\log L_{\mathrm{int}}$$^{j}$ |
|  | ($L_{\odot}$) | \(K\) |  | (pc) |  | ($L_{\odot}$) | (cm$^{-2}$) | ($\times10^{-5}$) | ($M_{\odot}$) | ($L_{\odot}$) |
| $H_C$ | $12.0(0.10)$ | $\geq200$ | $390(70)$ | $13.2(0.2)$ | $1.16(0.02)$ | $11.4(0.10)$ | $25.3(0.10)$ | $8(2)$ | $8.44(0.10)$ | $11.9-12.2$ |
| $W_C$ | $12.3(0.12)$ | $123(4)$ | $98(22)$ | $71(7)$ | $1.16(0.02)$ | $11.9(0.12)$ | $24.6(0.12)$ | $-$ | $9.13(0.12)$ | $11.7-12.1$ |
| $C_C$$^{k}$ | $12.1(0.12)$ | $45(5)$ | $-$ | $-$ | 0 | $12.1(0.12)$ | $-$ | $-$ | $9.57(0.12)$ | $11.5-11.8$ |

Table notes: . Estimated uncertainties are given in parenthesis.

Once the best fit model for the $H_C$ is obtained, the $W_C$ is fitted by using *JWST* continuum points at $11.5-26$ $\mu$m together with the flux density at 667 $\mu$m of the resolved component. A graybody (single-$T_d$) extincted by the same foreground layer as for the $H_C$ (i.e., with the same $\tau_{6\mu m}^{\mathrm{fg}}$) is adopted. We add to this graybody an extincted blackbody at 230 K primarily contributing at $<10$ $\mu$m, which has the effect of producing a better match to the H$_2$O band (see Section [3.2](#sech2oband)). The fitted parameters for the $W_C$ are $T_d$, the intrinsic optical depth evaluated at 6 $\mu$m ($\tau_{\mathrm{6\mu m}}^{\mathrm{int}}$), and the source radius $R_w$. The resulting “warm” continuum, with $T_d=123$ K, is complemented with a “hidden” component (discussed in Section [3.2](#sech2oband)) and shown in light-blue in Fig. [2](#sed). The fitted parameters are listed in Table [\[tab\]](#tab). Finally, a graybody “cold” ($T_d=45$ K) component ($C_C$) is added to the model to account for the remaining far-IR emission that cannot be explained with the $H_C$ and $W_C$ (orange curve in Fig. [2](#sed)). The $C_C$ also includes the fraction of the 667 $\mu$m emission that is resolved out by ALMA.

The fit to the SED of IRAS 07251$-$0248 E indicates that the mid-IR ($<10$ $\mu$m) continuum envelope and the 667 $\mu$m unresolved emission can indeed be matched with a single foreground-extincted nuclear component with unattenuated luminosity $L_{\mathrm{unatt}}\approx10^{12}$ $L_{\odot}$. The sizes obtained for this $H_C$ ($R_h=13.2$ pc) and for the $W_C$ ($R_w=71$ pc) are consistent with the ALMA 667 $\mu$m measurements for the unresolved and resolved components. Our dust-to-gas mass ratio calibration (Appendix [7](#kabs)) yields a gas mass ($M_{\mathrm{H_2}}$ in Table [\[tab\]](#tab)) dominated by the $C_C$. The total $M_{\mathrm{H_2}}=5.3\times10^9$ $M_{\odot}$ is comparable with the value obtained from CO $1-0$ (cite: gon15) and CO $2-1$ (cite: lam22), while the CO $2-1$ value for the central ($r<250$ pc) region is consistently lower (cite: per21). The inserts in Fig. [2](#sed) indicate extreme mid-IR optical depths for the $H_C$ and also for the $W_C$, as well as hot dust ($>500$ K) within the bulk of the $H_C$. Nevertheless, the surface temperature of the $H_C$ is much more moderate ($\approx200-250$ K) owing to the nearly complete conversion of the luminosity into blackbody emission from the nuclear photosphere ($T_d\approx (L_{\mathrm{unatt}}/(4\pi R_h^2 \sigma_{\mathrm{SB}}))^{1/4}=240$ K).

## The $6$ $\mu$m photosphere traced by the H$_2$O $\nu_2=1-0$ band

The nuclear $H_C$, with extreme column densities and accounting for the bulk of the mid-IR $<8$ $\mu$m continuum, will naturally generate strong mid-IR absorption in the gas-phase molecular bands. If the H$_2$O excitation is due to radiative pumping, the H$_2$O $\nu_2=1-0$ band is key to check whether the inferred $T_d$ profile can reproduce the observed line ratios, and will also provide valuable information on the gas-phase H$_2$O abundance and on the kinematics of the nuclear region.

Using the $T_d$ profile obtained from our best-fit continuum model for the $H_C$ (Fig. [2](#sed)), we have generated a grid of non-LTE, non-local radiative transfer models for H$_2$O (cite: gon24) by varying only the H$_2$O abundance relative to H$_2$ ($X_{\mathrm{H_2O}}$, assumed uniform) and the gas velocity field. Dust and gas are uniformly mixed within the nucleus, and owing to the extreme nuclear mid-IR extinction only the $6$ $\mu$m photosphere can be traced with the H$_2$O $\nu_2=1-0$ band. With the redshift obtained from emission lines (cite: spe25), we interpret the blueshift of the H$_2$O lines as an expansion of the nuclear surface, and apply across the nuclear photosphere an outflow velocity increasing linearly from 75 to 170 km s$^{-1}$. Absorption at higher velocities (up to $\sim-500$ km s$^{-1}$) is also observed in low-excitation lines (Section [2.2](#jwstobs)), and thus an additional H$_2$O shell flowing with velocities of $150-400$ km s$^{-1}$ was placed in front of the nucleus.

Due to the strong absorption associated with H$_2$O ice around 6 $\mu$m and a:C-H grains at 6.85 $\mu$m, the model predictions are better compared with the continuum-normalized spectrum in Fig. [3](#h2oband)b,d. However, the models that give a good match to most lines systematically overestimate the absorption lines located close to the absorption troughs, particularly at 6.85 $\mu$m. This specific model departure indicates the presence of an additional mid-IR component, unaffected by ice-mantle and H$_2$O absorption, that dilutes the H$_2$O line absorption at wavelengths where its strength is comparable to the observed continuum. Specifically, the flux density at frequency $\nu$ can be written as $$\begin{equation}
    F_{\nu} = F_{\nu}^{H_C} \, f_{\mathrm{\nu,norm}}^{\mathrm{H_2O}} 
    + \sum_{i\ne H_C} F_{\nu}^{i},  
    \label{fluxdens}
  
\end{equation}$$ where $F_{\nu}^{H_C}$ and $F_{\nu}^{i}$ are the (attenuated) flux densities from the $H_C$ and all other components $i$ (including the additional mid-IR component), and $f_{\mathrm{\nu,norm}}^{\mathrm{H_2O}}$ is the continuum-normalized H$_2$O absorption predicted by our model for the $H_C$. Since the observed continuum $F_{\nu}^{cont}$ has the same expression as eq. ([\[fluxdens\]](#fluxdens)) but excluding the $f_{\mathrm{\nu,norm}}^{\mathrm{H_2O}}$ factor, the continuum-normalized spectrum is given by $$\begin{equation}
  \frac{F_{\nu}}{F_{\nu}^{cont}} = 1+ f_{\mathrm{hot}} \left(f_{\mathrm{\nu,norm}}^{\mathrm{H_2O}}-1\right),
  \label{eq:contnorm}
\end{equation}$$ where we have defined a $\lambda-$dependent covering factor for the $H_C$, which is the fractional contribution by the $H_C$ to the observed continuum: $$\begin{equation}
  f_{\mathrm{hot}} = 1-\frac{\sum_{i\ne H_C} F_{\nu}^{i}}{F_{\nu}^{cont}}
  \label{fhot}
\end{equation}$$ We use eqs. ([\[eq:contnorm\]](#eq:contnorm)) and ([\[fhot\]](#fhot)) to compare the H$_2$O models with the observed continuum-normalized spectrum in Fig. [3](#h2oband)b,d. At wavelengths where $f_{\mathrm{hot}}$ becomes significantly lower than unity, because the $H_C$ continuum is severely attenuated by ice or a:C-H and thus the expected $F_{\nu}^{i}$ from any other component $i$ becomes comparable to $F_{\nu}^{cont}$, the continuum normalized absorption due to any H$_2$O line in front of the $H_C$ will be reduced according to eq. ([\[eq:contnorm\]](#eq:contnorm)). The 123 K component for the $W_C$ in Table [\[tab\]](#tab) yields negligible emission below 10 $\mu$m, and we find that a blackbody of 230 K, attenuated in the same way as the $H_C$ and $W_C$ (green dotted-dashed curve in Fig. [2](#sed)), is required to successfully correct the mentioned discrepancies. This 230 K component does not dominate the continuum emission at any wavelength, so that we will denote it as the “hidden” component. While its origin is uncertain, we tentatively associate it with the $W_C$ (and add it to the $W_C$; light blue curve in Fig. [2](#sed)). $f_{\mathrm{hot}}$ is shown as black dashed lines in Fig. [3](#h2oband)b,d.

Our best-fit model for the H$_2$O band (Fig. [3](#h2oband)b,d) is obtained for $X_{\mathrm{H_2O}}=8\times10^{-5}$ within the nucleus and $N_{\mathrm{H_2O}}\approx1.6\times10^{18}$ cm$^{-2}$ for the surrounding H$_2$O shell. A more detailed comparison between the observed line profiles and model predictions is shown in Fig. [8](#h2oprof) and discussed in Appendix [8](#h2olines), but here we emphasize the following points: first, that ground-vibrational levels of H$_2$O are excited through the pumping of the $\nu_2=1$ state by the strong mid-IR radiation that bathes the nuclear region and its surroundings. Second, that the high $X_{\mathrm{H_2O}}\sim10^{-4}$ is in line with chemical models of hot regions where H$_2$O ice has been vaporized and nearly all gas-phase oxygen not locked into CO is converted into H$_2$O (cite: nom04), as well as with models of C-type shocks (cite: kau96b). And third, in spite of the very high $T_d$ within the bulk of the $H_C$, the model captures the observed moderate H$_2$O excitation owing to the moderate $T_d$ values of the nuclear photosphere (lower insert in Fig. [2](#sed)), which is the only region the absorption band can probe due to extinction. We also show in Appendix [10](#hcnc2h2bands) that the HCN, C$_2$H$_2$, CH$_4$, and CO$_2$ bands are also reproduced with our model.

# Discussion and conclusions

![](IRAS07251-0248_sketch-4.pdf)

The schematic illustration of the model source shown in Fig. [4](#sketch) reflects the structure inferred from the observations of IRAS 07251$-$0248 E and model: the expanding nuclear region ($H_C$), is surrounded by outflowing gas (the high velocity foreground shell seen in H$_2$O), and a nearly face-on torus ($W_C$). The $H_C$ and the $W_C$ are both embedded in an envelope representing the $C_C$, which dominates the far-IR emission between 50 and 300 $\mu$m. In our illustration, the $C_C$ lies in front of the $H_C$ and $W_C$, and thus the $C_C$ also represents the foreground layer that extinguishes the continuum emission from the $H_C$ and the $W_C$ and is responsible for the $9.7$ and $18$ $\mu$m silicate absorption. The alternative, that the $W_C$ is a spherical shell surrounding the $H_C$, as Fig. [1](#almacont) might suggest, and is thus responsible for the foreground extinction of the $H_C$, is slightly disfavored because the high optical depth of the $W_C$ (right insert in Fig. [2](#sed)) would totally extinguish the mid-IR continuum emission from the $H_C$. Nevertheless, it is still possible that the high-velocity outflow has cleared the path to the $H_C$ along the line of sight and the extinction is caused by the residual material of the $W_C$ or by the outflowing material. The $C_C$ should include the far-IR emission from the western galaxy of the merger, with $9$% contribution to the overall luminosity (cite: per21). Regardless of the origin of the foreground extinction layer, it will probably have spatially varying chemical properties as it is fed by outflowing material from the direction of the nucleus, generating the observed H$_2$O ice and a:C-H absorption as the gas-phase H$_2$O freezes out and the hydrocarbons attach to carbonaceous grains (cite: gber25).

The $W_C$ is a very optically thick structure (right insert in Fig. [2](#sed)) surrounding the compact nucleus. Its far-IR emission is much stronger than the $H_C$ due to its larger size, which is similar to the size of the warm and optically thick regions that in other ULIRGs generate the far-IR absorption in rotational lines of OH, H$_2$O, and other molecular species (cite: gon12; gon14b). The far-IR continuum emission from these regions is usually diluted within the emission from colder regions that also contribute to the far-IR, which is the reason why (together with re-emission in the line) the far-IR optically thick lines absorb only a fraction ($\lesssim20\%$) of the total continuum (cite: gon15). A similar situation applies to IRAS 07251$-$0248, as the $C_C$ dominates the far-IR and the continuum from the $W_C$ should be diluted (Fig [2](#sed)). The *Herschel*/PACS spectra around the wavelengths of the OH doublets at 119, 79, and 65 $\mu$m, shown in Fig. [9](#pacs), exhibit optically thick absorption in the OH doublets and also in lines of H$_2$O, CH$^+$, and CH, so that their absorption strengths are sensitive to the fractional contribution of the $W_C$ to the far-IR. We show in Appendix [9](#farir) a model for these lines that reasonably fits the absorption troughs, indicating that the modeled $65-120$ $\mu$m continuum level generated by the $W_C$ is consistent with the available far-IR spectroscopic data. All far-IR lines are blueshifted by $\sim150$ km s$^{-1}$ (Fig. [9](#pacs)), indicating that the $W_C$ is also expanding.

## Uncertainties in the inferred parameters

The extreme $N_{\mathrm{H_2}}$ and $M_{\mathrm{H_2}}$ inferred in the $H_C$ (Table [\[tab\]](#tab)) could still be lower limits, because the adopted inner radius of the source is $0.15\times R_{\mathrm{out}}$ enabling high $T_d>1000$ K for $r<8$ pc (left insert in Fig. [2](#sed)). If the dust is however concentrated in a thinner shell close to the photosphere, as suggested by the outflow observed in the mid-IR molecular bands, or if the greenhouse effect in our models overestimates the actual $T_d$ values , both $N_{\mathrm{H_2}}$ and $M_{\mathrm{H_2}}$ would increase because of the overall lower $T_d$.

As shown in Table [\[tab\]](#tab), the apparent luminosities ($L_{\mathrm{att}}$) of the three components yield a total output power of $2.3\times10^{12}\,L_{\odot}$, but the combined unattenuated luminosities ($L_{\mathrm{unatt}}$) obviously give a higher value. This indicates that the values of $L_{\mathrm{unatt}}$ are, for both the $W_C$ and the $C_C$, in part re-emission from more inner components, i.e. they are not only due to the power sources located within their physical regions (cite: gon04). The $W_C$ surrounds the $H_C$ and part of its emission will be an effect of the $H_C$ illumination. Likewise, if the $C_C$ surrounds both the $W_C$ and the $H_C$, a fraction of its emission will be an effect of heating by the innermost components. Defining the “intrinsic luminosity” $L_{\mathrm{int}}$ of a component as the unattenuated luminosity generated by only the power sources within the physical region, and under the assumption that isotropic emission is applicable to the optically thick $H_C$ and $W_C$ components, the values of $L_{\mathrm{int}}$ would be $10^{12}$, $\sim10^{12}$, and $\sim3\times10^{11}\,L_{\odot}$ for the $H_C$, $W_C$, and $C_C$, respectively. These estimates also assume that nearly the entire luminosity from the $H_C$ is absorbed and re-emitted by the $W_C$, which would then intrinsically generate only half of its $L_{\mathrm{unatt}}$ value; the $C_C$ would then produce the remaining emission that accounts for the total output power, including the emission from the western galaxy.

Nevertheless, isotropic emission must not necessarily apply to the optically thick $H_C$ and/or $W_C$ components, in which case their $L_{\mathrm{int}}$ will depart from the isotropic values quoted above (cite: efs14; efs22). If the morphology of the $W_C$ was a flat disk seen nearly face-on, $L_{\mathrm{unatt}}(W_C)=2\pi R_W^2 \sigma_{\mathrm{SB}}T_d^4\sim10^{12}\,L_{\odot}$ for $R_W=71$ pc and $T_d=123$ K (Table [\[tab\]](#tab)). The actual scenario is most likely intermediate between the spherical and flat morphologies (Fig. [4](#sketch)). Likewise, if the $H_C$ possesses a structure elongated along the line of sight, its $L_{\mathrm{int}}$ would exceed $10^{12}\,L_{\odot}$, and the $W_C$ emission would be predominantly attributable to external heating. This possibility is supported by the fact that, rather than representing a separate physical structure, the $W_C$ appears to be connected to the $H_C$, since both exhibit high column densities and similar kinematics (Appendix [9](#farir)) although quite different brightnesses. In Table [\[tab\]](#tab) we provide plausible ranges for $L_{\mathrm{int}}$, taking these uncertainties into consideration.

## A CON hidding a quasar, surrounded by a starburst

From a comparative perspective, the high brightness of the $H_C$ favors the dominant contribution to the luminosity by an AGN. The luminosity surface density, $\Sigma_{\mathrm{bol}}\approx4.6\times10^8$ $L_{\odot}$ pc$^{-2}$, is $\sim1$ dex higher than the values found in other CONs with comparable sizes and gas mass surface densities ($\Sigma_{\mathrm{H_2}}\approx5\times10^5$ $M_{\odot}$ pc$^{-2}$), such as NGC 4418 (cite: sak13; gon12), IC 860 ($(1-8)\times10^7$ $L_{\odot}$ pc$^{-2}$, (cite: aal19); ) or Arp 220 W [^2]. Our model for the $H_C$ yields an unattenuated SED that peaks in the mid-IR (Fig. [2](#sed)), while the continuum models in consider lower values of $\Sigma_{\mathrm{bol}}$ and the corresponding SEDs peak in the far-IR.

Nevertheless, the enormous accumulation of gas in the $H_C$ requires consideration of the role of a potential transitory burst of star formation. We first note that the H$_2$O absorption line shapes do not show any distinct feature at central velocities (Figs. [7](#redshift) and [8](#h2oprof)), meaning that the whole mid-IR photosphere of the $H_C$ is outflowing and suggesting the entire expulsion of the gas from the nuclear region. If responsible for the outflowing gas, a nuclear starburst could not have a duration much longer than the outflow dynamical timescale of $t_{\mathrm{dyn}}\sim R_h/v=8\times10^4$ yr, and indeed the free-fall time, $t_{\mathrm{ff}}= (3\pi/32G\rho)^{1/2}=4.1\times10^4$ yr (calculated from the averaged $n_{\mathrm{H_2}}=5.8\times10^5$ cm$^{-3}$), accomplishes this constraint. With these short timescales, however, a pure starburst scenario would imply that most stars are actually in the protostar phase with the luminosity arising from gas accretion, while expelling the inflowing material that feeds them.

(cite: tho05) argued that for an optically thick starburst disk radiating at its Eddington limit for dust, a characteristic maximum $\Sigma_{\mathrm{bol}}\sim10^7$ $L_{\odot}$ pc$^{-2}$ is attained that is independent of $\Sigma_{\mathrm{gas}}$ ($\approx1.36\times \Sigma_{\mathrm{H_2}}$). This limit for $\Sigma_{\mathrm{bol}}$ falls too short to explain the inferred value in the $H_C$, and an AGN would then be responsible for the bulk of the luminosity. (cite: and11) postulated the possibility of hot starbursts with extreme values of $\Sigma_{\mathrm{bol}}\sim5\times10^8$ $L_{\odot}$ pc$^{-2}$ for $\Sigma_{\mathrm{gas}}\sim5\times10^5$ $M_{\odot}$ pc$^{-2}$, but attributed them to the parsec-scale region fueling a bright AGN.

More recently, (cite: gru18) proposed that for sufficiently high $\Sigma_{\mathrm{H_2}}>\Sigma_{\mathrm{crit}}\sim3\times10^3$ $M_{\odot}$ pc$^{-2}$, feedback fails due to the strong gravitational force and an extraordinary burst of star formation converts most of the gas into stars within a few $t_{\mathrm{ff}}$. The key feature of these models is that the momentum deposition per stellar mass is assumed to be independent of environment; that is, the “$\tau_{\mathrm{IR}}$ boost” characteristic of radiation pressure in optically thick components is neglected owing to presumable leakage of photons along optically thin paths. We note that the maximum $\Sigma_{\mathrm{gas}}\sim1.3\times10^4$ $M_{\odot}$ pc$^{-2}$ considered in their simulations is $\sim40\times$ lower than the value of the $H_C$, but here we assume that their results can be extrapolated to our more extreme conditions. Adopting a zero-age main sequence (ZAMS) population with $3\times10^3$ erg s$^{-1}$ g$^{-1}$, a stellar mass of $M_*=6.3\times10^8\,M_{\odot}$ is required to account for $10^{12}\,L_{\odot}$. The current star-formation efficiency would then be $\mathrm{SFE}=M_*/(M_*+M_{\mathrm{gas}})\sim0.63$ and, with a formation timescale of $\sim2\,t_{\mathrm{ff}}$, the star-formation rate would be $\mathrm{SFR}\sim7.7\times10^3$ $M_{\odot}$ yr$^{-1}$ with a per-freefall SFE of $\epsilon_{\mathrm{ff}}\sim0.6$. Within the uncertainties, the values of SFE and $\epsilon_{\mathrm{ff}}$ agree with results of (cite: gru18) simulations.

Nevertheless, the above pure-starburst scenario faces serious drawbacks in the case of the $H_C$ in IRAS 07251$-$0248. First, the implied values of $\Sigma_*\sim10^6$ $M_{\odot}$ pc$^{-2}$ are found in a few very dense nuclear star clusters (NSCs), but on smaller spatial scales ($\lesssim5$ pc) and with lower $M_*$ (cite: gru19; neu20). Second, the concentration of the observed gas mass in the $H_C$ would be hard to explain with such a burst of star formation, because accretion of $\sim10^9$ $M_{\odot}$ onto a volume with radius $R_h\sim13$ pc would also have to be achieved within $\sim1\,t_{\mathrm{ff}}$ (cite: gru19), requiring unrealistic accretion rates. Third, protostars do not efficiently generate the cosmic rays (CRs) required to explain the observed H$_3^+$, CR-dominated chemistry, and carbonaceous grain erosion in the $H_C$ (cite: per24; spe25; gber25). Fourth, the H$_2$O line profiles strongly suggest a collective motion of the whole ISM that is better explained by a single feedback event rather than by the effect of many individual protostars. Finally, the “greenhouse effect” required to explain the high submm brightness of the $H_C$ translates into the “$\tau_{\mathrm{IR}}$ boost”, which cannot be neglected for the extreme $\Sigma_{\mathrm{gas}}$ in the $H_C$, and the observed feedback would be hard to explain without this effect.

Conversely, an AGN burst responsible for the observed luminosity and feedback would have enabled smoother gas accretion onto the nuclear region, owing to the different spatial scales and solid angles of AGN feedback and nuclear gas accretion and the stochastic nature of the former. While the previous formation of a NSC in IRAS 07251$-$0248 E is a natural outcome of the highly concentrated ISM, the extreme $\Sigma_{\mathrm{bol}}$ strongly suggests a limited star-formation efficiency within a compact obscured nucleus (CON) that is powered by an AGN currently emitting at quasar level, in agreement with (cite: per21).

With the uncertainties related to geometry in optically thick sources, it appears that the $W_C$ is forming stars at high rates equivalent to at least $\sim5\times10^{11}\,L_{\odot}$, supporting the view of the composite nature of ULIRGs (cite: vei09) with the specificity that the $W_C$ is a nuclear starburst characterized by high column densities. The high gas mass accumulation at the center of the galaxy both drives a starburst in situ, and thus the formation of a NSC, and efficiently feeds the central supermassive black hole (cite: neu20), exemplifying the black hole and star formation co-evolution in its most extreme form. The transition from star formation to black hole accretion in the $H_C$ may be smooth in these conditions and tidal disruption and capture of (proto)stars close to the black hole may be an efficient black hole growth channel (cite: str09).

## Outflow energetics: a hot bubble driving the $H_C$ expansion?

With the values of $M_{\mathrm{H_2}}$ and $R$ from Table [\[tab\]](#tab) and a velocity of $160$ km s$^{-1}$, the mass outflow rate associated with the $H_C$ is estimated as $\dot{M}=\mu M_{\mathrm{H_2}} v/R=2.9\times10^3$ $M_{\odot}$ yr$^{-1}$, where $\mu=1.36$ accounts for species other than hydrogen. Here we have assumed that the entire nuclear source is expanding, although we can only probe the kinematics of its mid-IR photosphere. The momentum rate is then $\dot{P}=\dot{M} v=2.7\times10^{36}\,\mathrm{dyn}=21.5\,L_{\mathrm{AGN}}/c$ and the energy flux is $\dot{E}=0.5 \dot{M} v^2=2.05\times10^{43}\,\mathrm{erg\,s^{-1}}=5.4\times10^{-3}\,L_{\mathrm{AGN}}$, where we have adopted $L_{\mathrm{AGN}}=10^{12}\,L_{\mathrm{\odot}}$ (Table [\[tab\]](#tab)).

Radiation pressure on dust grains could in principle drive the observed outflow, if it can overcome the opposite effect of (self-)gravitation on the gas (cite: ish15). Taking into account the backpressure effects in optically thick environments and with a gas mass of $\mu\,M_{\mathrm{H_2}}=3\times10^8$ $M_{\odot}$ within the $H_C$ (Table [\[tab\]](#tab)), the gravitational force would however balance the force due to radiation pressure at the $H_C$ surface as long as the combined black hole and stellar mass attains $\sim2.5\times10^8$ $M_{\odot}$. This is plausible, and thus the effect of radiation pressure in driving the outflow is uncertain.

Another possibility consists of an inner hot bubble inflating the nucleus, such that the molecular outflow is generated as the bubble swepts up the concentrated nuclear ISM. We have explored this point using the analytic self-similar solutions developed by (cite: fau12) (their Appendix A), assuming that the hot shocked wind conserves energy. We first constrain the swept out gas mass to $\mu\,M_{\mathrm{H_2}}=3\times10^8$ $M_{\odot}$ at 13.2 pc with a flat density profile, and assumed that $1/2$ of the mechanical energy injected by the AGN ($v_{\mathrm{wind}}\,L_{\mathrm{AGN}}/2c$, where $v_{\mathrm{wind}}$ is the inner wind velocity and $L_{\mathrm{AGN}}=10^{12}\,L_{\odot}$) goes into kinetic motion of the swept-up gas. Then, for $v_{\mathrm{wind}}=2\times10^4$ km s$^{-1}$, a shock velocity driven into the ambient gas of $170$ km s$^{-1}$ at 13.2 pc is obtained -in agreement with the blueshift of the peak absorption observed in the molecular lines. However, the flow time of $\sim5\times10^4$ yr is about half the proton cooling time calculated using the two-temperature effects derived from thermal uncoupling of e$^-$ and protons (cite: fau12), and thus a *partially* energy-conserving phase is not ruled out.

This hot bubble scenario is an ultracompact version of the (partially) energy-conserving phase of outflows driven by AGN (cite: tom15; fer15), with much lower shock velocities that are a consequence of the enormous gas masses that are being swept-up at small radii. The bulk of the gas will not escape from the potential well of the galaxy, and thus a series of CON phases are expected to occur over longer timescales, while holes in the structure will be increasingly opened generating in later times more extended and faster OH and CO outflows. The interesting feature of the proposed hot bubble scenario is that the inner wind shock presumably accelerates cosmic-ray particles (cite: zub12), a key ingredient of the strong H$_3^+$ absorption (cite: per24) and unique carbon-rich (cite: gber25) and molecular cation (cite: spe25) chemistry observed in IRAS 07251$-$0248 E. The strength of linking kinematics and chemistry may favor this scenario over radiation pressure as the origin of the observed outflow.

# Acknowledgements

We thank the referee for the constructive comments that helped improve the clarity of the manuscript, and acknowledge the DD-ERS teams for developing their observing program with a zero–exclusive–access period. EG-A thanks the Spanish MICINN for support under projects PID2022-137779OB-C41 and PID2023-146667NB-I00. MPS acknowledges support under grants RYC2021-033094-I, CNS2023-145506 and PID2023-146667NB-I00 funded by MCIN/AEI/10.13039/501100011033 and the European Union NextGenerationEU/PRTR. IGB is supported by the Programa Atracción de Talento Investigador “César Nombela” via grant 2023-T1/TEC-29030 funded by the Community of Madrid. This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST; and from the European JWST archive (eJWST) operated by the ESAC Science Data Centre (ESDC) of the European Space Agency. These observations are associated with program #3368. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2023.1.00942.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

71 natexlab

(ref: aal15) Aalto, S., Martı́n, S., Costagliola, F., et al. 2015, A&A, 584, A42

(ref: aal19) Aalto, S., Muller, S., König, S., et al. 2019, A&A, 627, A147

(ref: and11) Andrews, B. H. & Thompson, T. A. 2011, ApJ, 727, 97

(ref: bok22) Böker, T., Arribas, S., Lützgendorf, N., et al. 2022, A&A, 661, A82

(ref: bui24) Buiten, V. A., van der Werf, P. P., Viti, S., et al. 2024, ApJ, 966, 166

(ref: bui25) Buiten, V. A., van der Werf, P. P., Viti, S., et al. 2025, A&A, 699, A312

(ref: chu20) Chubb, K. L., Tennyson, J., & Yurchenko, S. N. 2020, MNRAS, 493, 1531

(ref: cos11) Costagliola, F., Aalto, S., Rodriguez, M. I., et al. 2011, A&A, 528, A30

(ref: dav01) Davidson, S. A., Evenson, K. M., & Brown, J. M. 2001, ApJ, 546, 330

(ref: dra84) Draine, B. T. & Lee, H. M. 1984, ApJ, 285, 89

(ref: efs22) Efstathiou, A., Farrah, D., Afonso, J., et al. 2022, MNRAS, 512, 5183

(ref: efs14) Efstathiou, A., Pearson, C., Farrah, D., et al. 2014, MNRAS, 437, L16

(ref: ehr97) Ehrenfreund, P., Boogert, A. C. A., Gerakines, P. A., Tielens, A. G. G. M., & van Dishoeck, E. F. 1997, A&A, 328, 649

(ref: fal21) Falstad, N., Aalto, S., König, S., et al. 2021, A&A, 649, A105

(ref: fal19) Falstad, N., Hallqvist, F., Aalto, S., et al. 2019, A&A, 623, A29

(ref: fau12) Faucher-Giguère, C.-A. & Quataert, E. 2012, MNRAS, 425, 605

(ref: fer15) Feruglio, C., Fiore, F., Carniani, S., et al. 2015, A&A, 583, A99

(ref: fri11) Fritz, T. K., Gillessen, S., Dodds-Eden, K., et al. 2011, ApJ, 737, 73

(ref: gber24b) Garcı́a-Bernete, I., Alonso-Herrero, A., Rigopoulou, D., et al. 2024a, A&A, 681, L7

(ref: gber25b) Garcı́a-Bernete, I., Donnan, F. R., Rigopoulou, D., et al. 2025a, A&A, 696, A135

(ref: gber25) Garcı́a-Bernete, I., Pereira-Santaella, M., González-Alfonso, E., & et al. 2025b, Nature Astronomy

(ref: gber24) Garcı́a-Bernete, I., Pereira-Santaella, M., González-Alfonso, E., et al. 2024b, A&A, 682, L5

(ref: gber22b) Garcı́a-Bernete, I., Rigopoulou, D., Aalto, S., et al. 2022a, A&A, 663, A46

(ref: gber22) Garcı́a-Bernete, I., Rigopoulou, D., Alonso-Herrero, A., et al. 2022b, A&A, 666, L5

(ref: gon14b) González-Alfonso, E., Fischer, J., Graciá-Carpio, J., et al. 2014, A&A, 561, A27

(ref: gon12) González-Alfonso, E., Fischer, J., Graciá-Carpio, J., et al. 2012, A&A, 541, A4

(ref: gon15) González-Alfonso, E., Fischer, J., Sturm, E., et al. 2015, ApJ, 800, 69

(ref: gon24) González-Alfonso, E., Garcı́a-Bernete, I., Pereira-Santaella, M., et al. 2024, A&A, 682, A182

(ref: gon19) González-Alfonso, E. & Sakamoto, K. 2019, ApJ, 882, 153

(ref: gon04) González-Alfonso, E., Smith, H. A., Fischer, J., & Cernicharo, J. 2004, ApJ, 613, 247

(ref: gor22) Gordon, I. E., Rothman, L. S., Hargreaves, R. J., et al. 2022, JQSRT, 277, 107949

(ref: gru18) Grudić, M. Y., Hopkins, P. F., Faucher-Giguère, C.-A., et al. 2018, MNRAS, 475, 3511

(ref: gru19) Grudić, M. Y., Hopkins, P. F., Quataert, E., & Murray, N. 2019, MNRAS, 483, 5548

(ref: ima09) Imanishi, M., Nakanishi, K., Tamura, Y., & Peng, C.-H. 2009, AJ, 137, 3581

(ref: ish15) Ishibashi, W. & Fabian, A. C. 2015, MNRAS, 451, 93

(ref: iwa11) Iwasawa, K., Sanders, D. B., Teng, S. H., et al. 2011, A&A, 529, A106

(ref: izu16) Izumi, T., Kohno, K., Aalto, S., et al. 2016, ApJ, 818, 42

(ref: jak22) Jakobsen, P., Ferruit, P., Alves de Oliveira, C., et al. 2022, A&A, 661, A80

(ref: kau96b) Kaufman, M. J. & Neufeld, D. A. 1996, ApJ, 456, 611

(ref: kri08) Krips, M., Neri, R., Garcı́a-Burillo, S., et al. 2008, ApJ, 677, 262

(ref: lab16) Labiano, A., Azzollini, R., Bailey, J., et al. 2016, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9910, Observatory Operations: Strategies, Processes, and Systems VI, ed. A. B. Peck, R. L. Seaman, & C. R. Benn, 99102W

(ref: lam22) Lamperti, I., Pereira-Santaella, M., Perna, M., et al. 2022, A&A, 668, A45

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mul05) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: mul01) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49

(ref: neu20) Neumayer, N., Seth, A., & Böker, T. 2020, A&ARv, 28, 4

(ref: nis24) Nishimura, Y., Aalto, S., Gorski, M. D., et al. 2024, A&A, 686, A48

(ref: nom04) Nomura, H. & Millar, T. J. 2004, A&A, 414, 409

(ref: per22) Pereira-Santaella, M., Álvarez-Márquez, J., Garcı́a-Bernete, I., et al. 2022, A&A, 665, L11

(ref: per21) Pereira-Santaella, M., Colina, L., Garcı́a-Burillo, S., et al. 2021, A&A, 651, A42

(ref: per24) Pereira-Santaella, M., González-Alfonso, E., Garcı́a-Bernete, I., et al. 2024, A&A, 689, L12

(ref: per17) Pereira-Santaella, M., González-Alfonso, E., Usero, A., et al. 2017, A&A, 601, L3

(ref: pic98) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: pla11) Planck Collaboration, Abergel, A., Ade, P. A. R., et al. 2011, A&A, 536, A25

(ref: pri20) Privon, G. C., Ricci, C., Aalto, S., et al. 2020, ApJ, 893, 149

(ref: ric21) Ricci, C., Privon, G. C., Pfeifle, R. W., et al. 2021, MNRAS, 506, 5935

(ref: rie15) Rieke, G. H., Wright, G. S., Böker, T., et al. 2015, PASP, 127, 584

(ref: roc22) Rocha, W. R. M., Rachid, M. G., Olsthoorn, B., et al. 2022, A&A, 668, A63

(ref: ros00) Rosenthal, D., Bertoldi, F., & Drapatz, S. 2000, A&A, 356, 705

(ref: sak13) Sakamoto, K., Aalto, S., Costagliola, F., et al. 2013, ApJ, 764, 42

(ref: sak08) Sakamoto, K., Wang, J., Wiedner, M. C., et al. 2008, ApJ, 684, 957

(ref: spe25) Speranza, G., Pereira-Santaella, M., Agúndez, M., & et al. 2025, MNRAS

(ref: spo22) Spoon, H. W. W., Hernán-Caballero, A., Rupke, D., et al. 2022, ApJS, 259, 37

(ref: str09) Strubbe, L. E. & Quataert, E. 2009, MNRAS, 400, 2070

(ref: tho05) Thompson, T. A., Quataert, E., & Murray, N. 2005, ApJ, 630, 167

(ref: tom15) Tombesi, F., Meléndez, M., Veilleux, S., et al. 2015, Nature, 519, 436

(ref: vei09) Veilleux, S., Rupke, D. S. N., Kim, D. C., et al. 2009, ApJS, 182, 628

(ref: wel15) Wells, M., Pel, J. W., Glasse, A., et al. 2015, The mid-infrared instrument for the James Webb Space Telescope, VI: The medium resolution spectrometer, Technical Report JWST-STScI-000006

(ref: wri15) Wright, G. S., Wright, D., Goodson, G. B., et al. 2015, PASP, 127, 595

(ref: yur24) Yurchenko, S. N., Owens, A., Kefala, K., & Tennyson, J. 2024, MNRAS, 528, 3719

(ref: zub12) Zubovas, K. & King, A. 2012, ApJL, 745, L34

# ALMA observations and models for the 667 $\mu$m continuum

![image](alma_data_07251-0248E_p.pdf) ![image](alma_data_07251-0248E_g.pdf)

We obtained high angular resolution ALMA observations of IRAS 07251$-$0248 E in Band 8 at $\sim$410 GHz (rest-frame $\sim$667$\mu$m; program 2023.1.00942.S, PI: M. Pereira-Santaella). Four 1.875 GHz bandwidth spectral windows with 10 km s$^{-1}$ channels were defined for these observations. In this paper, we focus on the continuum detected after combining all the line-free channels in the spectral windows. We used the ALMA reduction software CASA (v6.5.4; (cite: McMullin2007)) to calibrate and clean the data using the standard pipeline. For the cleaning, we applied the Briggs weighting with a robustness parameter of 1.0. To improve the quality of the continuum image, we applied a round of phase self-calibration using the emission from the bright H$_2$O 448 GHz line (cite: per17). The final continuum image was corrected for the primary beam. The synthesized beam full-width half-maximum (FWHM) for the combined continuum image is 75$\times$67 mas$^2$ and the sensitivity is 0.20 mJy beam$^{-1}$. For Band 8, the absolute flux accuracy is $\sim$20% (ALMA Technical Handbook).

Similar to (cite: per21), we modeled the continuum of IRAS 07251$-$0248 E to determine the flux, size, and position of the detected emission. Briefly, we used three simple models consisting of a point-source, a Gaussian, and a point-source $+$ Gaussian (pG model). These models were convolved with the beam and their parameters varied to minimize the $\chi^2$ obtained from the comparison with the observed image. Figure [5](#almacontalter) shows the results of the fit for the point-source and Gaussian model, both showing significant residual structures indicating that they fail to reproduce the nuclear emission of this object. Instead, the fit is much better for the pG model, which shows no evident residuals (Fig. [1](#almacont)).

# *JWST* observations and data reduction

The *JWST* observations of IRAS 07251$-$0248 E have been described in detail by (cite: gber25) and (cite: spe25). Data were taken with the integral-field spectrograph NIRSpec, using the grating filter pair G395H (cite: jak22; bok22), and MIRI MRS (cite: rie15; wel15; wri15). The data were reduced following the standard MRS pipeline procedure (cite: lab16), additionally using extra steps to identify and correct hot and cold pixels (cite: per24; gber24b). The spectrum was extracted according with the method described in (cite: per22) and (cite: gber22; gber24b; gber24).

# The absorption coefficient of dust

![](iras07251_kabs_isel20.pdf)

Our adopted 6 $\mu$m-normalized absorption coefficient of dust from mid-IR to submm wavelengths is shown in Fig. [6](#figkabs) and compared with the mid-IR values inferred towards the Galactic Center (GC) by (cite: fri11). The latter includes mid-IR features due to ices and aliphatic hydrocarbons that we have ignored, but otherwise our curve fits the overall GC curve for $\lambda <10$ $\mu$m. However, we have modified the GC curve for $\lambda=10-20$ $\mu$m according to (cite: ros00), which is in turn based on the work by (cite: dra84). This modification gives a better fit to the IRAS 07251$-$0248 spectrum at the quoted wavelengths. At $\lambda >20$ $\mu$m, we use an emissivity index similar to that of the GC curve ($\beta=1.85$) all the way to millimeter wavelengths.

(cite: pla11) have given an absolute calibration of $\tau_{250\mu m}/N_{\mathrm{H}}=2.32\times10^{-25}$ cm$^{2}$, which for $\beta=1.85$ yields $\mu \times \mathrm{DGR} \times k_{670\mu m}=2.2\times10^{-2}$ cm$^{2}$ g$^{-1}$, where DGR is the dust-to-gas ratio by mass and $\mu=1.36$ corrects for all species other than hydrogen. We have adopted this calibration to calculate the H$_2$ masses in Table [\[tab\]](#tab), which roughly agree with independent methods based on CO emission (Section [3.1](#contin)). This indicates a suitable calibration for at least the $C_C$ component that dominates the gas mass budget, but results are more uncertain for the $W_C$ and mostly for the $H_C$. At $6$ $\mu$m we obtain $\tau_{6\mu m}/N_{\mathrm{H}}=1.3\times10^{-23}$ cm$^{2}$, which is used to calculate the molecular abundances in our models where dust and molecules are evenly mixed. The hydrogen column density in terms of the optical depth at 667 $\mu$m is $N_{\mathrm{H}}=2.6\times10^{25}\,\tau_{667\mu m}$ cm$^{-2}$.

# Details of the H$_2$O band

![](iras07251_redshift.pdf)

![](iras07251_h2oprof_isel20.pdf)

Figure [7](#redshift) clearly illustrates the blueshift of the H$_2$O $\nu_2$ absorption lines relative to several emission lines detected with MIRI/MRS. (Note that the absorption features close to some emission lines are due to R branch lines of the also blueshifted HCN $2\nu_2$ band.) The CO 2-1 rotational line (cite: lam22) shows an asymmetric shape with the blueshifted part of the profile weaker than the redshifted part. In view of the absorption of the continuum detected in the velocity range \[$-570$,$-350$\] km s$^{-1}$, the asymmetry of the line core is also attributable to the absorption of the continuum by the outflowing approaching CO gas, most likely on spatial scales of the $W_C$. In the lower two panels of Fig. [7](#redshift), the profiles correspond to low-excitation H$_2$O lines that also display absorption up to $\sim-600$ km s$^{-1}$; other more excited lines do not show this high-velocity absorption (Fig. [8](#h2oprof)).

A detailed comparison between a number of observed H$_2$O line shapes and the best-fit model predictions is presented in Fig. [8](#h2oprof). As shown in the inserted energy level diagram, the displayed lines (mostly within the R branch) span a broad range of level excitation in the ground vibrational state, from the ground ortho level ($1_{0,1}$) to the $10_{1,10}$ one at $\sim1600$ K, including both backbone and non-backbone levels.

As described in Section [3.2](#sech2oband), we include two H$_2$O components along the line of sight to the mid-IR continuum from the $H_C$: one is evenly mixed with the hot dust responsible for this continuum, with velocities between 75 and 170 km s$^{-1}$, and the other is a broad layer extending from the $H_C$ photosphere outwards with velocities between 150 and 400 km s$^{-1}$. In combination with a turbulent velocity of $90$ km s$^{-1}$, this velocity field can approximately match the observed profiles. Radiative pumping fully dominates the excitation of the first component, so that the H$_2$ density used in the models ($n_{\mathrm{H_2}}=N_{\mathrm{H_2}}/(R_{h}-R_{\mathrm{int}})\sim6\times10^5$ cm$^{-3}$) has no impact on the results as long as the H$_2$O abundance relative to the dust remains unchanged. The foreground layer is used to account for the low-excitation absorption at the highest velocities, and is shown to produce significant absorption up to the $5_{0,5}-4_{1,4}$ line ($E_{\mathrm{low}}\approx300$ K). In higher excitation lines, the blueshifted absorption is restricted to velocities $>-300$ km s$^{-1}$ (e.g., $7_{1,6}-6_{2,5}$). Because of the strong nuclear mid-IR radiation field, the excitation of this layer component is also dominated by radiative pumping.

In spite of the large column densities of H$_2$O mixed with the dust in the $H_C$, the predicted absorption troughs are still sensitive to the H$_2$O abundance relative to the dust, mostly in the highest excitation lines. This is because the dust opacity restricts the H$_2$O that can generate absorption to the external layers of the source (i.e. to $\tau_{6\mu m}\lesssim 1.5$ from the surface), and $N(\mathrm{H_2O})\sim5\times10^{18}$ cm$^{-2}$ in this shell is much lower than the total value. Our best-fit H$_2$O abundance relative to H$_2$ of $8\times10^{-5}$ is similar to the value inferred by (cite: gber25).

The profiles displayed in Fig. [8](#h2oprof) show that our best fit model overpredicts the absorption in the low excitation $1_{1,0}-1_{0,1}$ and $1_{0,1}-1_{1,0}$ lines. The discrepancy is attributable to potential resonant scattering of the mid-IR continuum over larger scales, as H$_2$O is also present in the $W_C$ (Appendix [9](#farir)). The model also overpredicts the absorption in some high excitation lines ($9_{0,9}-8_{1,8}$, $10_{1,10}-9_{0,9}$, $9_{1,8}-8_{2,7}$, $7_{3,5}-6_{2,4}$), but accounts rather well for the rest of the lines.

# The far-IR molecular absorption

![](iras07251_PACS.pdf)

| Species    |  Abundance $^{a}$  |
|:-----------|:------------------:|
| OH         | $5.0\times10^{-6}$ |
| $^{18}$OH  | $2.5\times10^{-8}$ |
| H$_2$O     | $5.0\times10^{-6}$ |
| CH         | $2.5\times10^{-7}$ |
| CH$^+$     | $2.5\times10^{-7}$ |
| H$_2$O$^+$ | $5.0\times10^{-8}$ |

: Molecular abundances relative to H nuclei in the $W_C$ of IRAS 07251$-$0248 E

Table notes:

Due to the dilution of the $W_C+H_C$ far-IR continuum discussed in Section [4](#disc), we show in Fig. [9](#pacs) the continuum-subtracted far-IR spectra observed with *Herschel*/PACS around the wavelengths of the OH 119, 79, and 65 $\mu$m doublets. If the far-IR continuum level predicted by our model for the $W_C$ is correct, we will be able to match the observed absorption troughs in this absolute scale.

The far-IR absorption features shown in Fig. [9](#pacs) are characteristic of very optically thick regions. In panel a, the ground-state OH 119 $\mu$m doublet exhibits a flat profile with no dip in the absorption between the two $l-$doubling components. We also find clear detection of the red component of $^{18}$OH 120.15 $\mu$m, as well as strong absorption due to CH$^+$ 3-2 at 119.8 $\mu$m and to the CH $(N=3,J=7/2)-(2,5/2)$ doublet around 118.5 $\mu$m (cite: dav01). To our knowledge, this is the only ULIRG where the CH$^+$ 3-2 absorption is nearly as strong as that due to OH 119 $\mu$m. In panel b, two H$_2$O lines ($4_{2,3}-3_{1,2}$ and $6_{1,5}-5_{2,4}$ at 78.7-78.9 $\mu$m) are detected, together with a broad feature that is in part due to the ground-state OH 79 $\mu$m doublet but requires additional absorption at velocities more blueshifted than $-350$ km s$^{-1}$ from OH. In panel c, strong absorption in the OH 65 $\mu$m doublet ($E_{\mathrm{low}}\approx300$ K) is seen, which has the second highest equivalent width among all galaxies observed with *Herschel*/PACS (cite: gon15). $^{18}$OH at 65.6 $\mu$m is also detected. As indicated in Fig. [9](#pacs) for the OH lines, all features are blueshifted by $\sim150$ km s$^{-1}$.

Our model for the far-IR lines includes the quoted species (OH, $^{18}$OH, H$_2$O, CH, CH$^+$) together with H$_2$O$^+$, which has several rotational lines in these spectral regions. Spectroscopic data used for OH, CH, CH$^+$, and H$_2$O$^+$ were obtained from the JPL (cite: pic98) and CDMS (cite: mul01; mul05) catalogs. Since the $W_C$ is very optically thick ($\tau_{100\mu m}\approx10$, Fig. [2](#sed)), warm ($T_d=123$ K, Table [\[tab\]](#tab)), and has a size ($R_w=71$ pc) larger than the $H_C$, it dominates the absorption in the observed lines. The inferred abundances are listed in Table [2](#tab2). An OH abundance of $\approx5\times10^{-6}$, similar to the value found in the nuclear region of NGC 4418 (cite: gon12) is required to generate absorption troughs in the OH 119 and 65 $\mu$m doublets comparable to the observed features (light-blue curves in Fig. [9](#pacs)). However, the observed very broad OH 79 $\mu$m feature is still underpredicted with just the $W_C$, and we have thus included in the model the expected OH contribution from the $H_C$, as well as a model for H$_2$O$^+$ in both components. The 79.1 $\mu$m absorption is then better reproduced, although its unpredicted blueshifted shoulder at 79.0 $\mu$m suggests that an additional unidentified species further contributes to the absorption. With a similar abundance of $\approx5\times10^{-6}$ in the $W_C$, the H$_2$O lines are matched as well, thus indicating a decline of its abundance of $\sim1$ dex from the compact $H_C$ to the more extended $W_C$. We also note the high abundances inferred for both CH and CH$^+$, suggesting that the hydrocarbon-rich chemistry observed in the mid-IR towards the nuclear region (cite: gber25) applies to some extent to the $W_C$.

In summary, the reasonable match to the far-IR absorption lines indicates that the continuum level of the $W_C$ in the far-IR predicted by our model is accurate within $\sim20$%. The similar kinematics found for the far-IR and mid-IR absorption lines and the high abundances found for CH and CH$^+$ indicate that the physical and chemical processes in the $W_C$ are also affected by the AGN at the core of the $H_C$.

# The HCN, C$_2$H$_2$, CH$_4$, and CO$_2$ bands

![](iras07251_hcnc2h2_isel20.pdf)

![](iras07251_CO2.pdf)

The *JWST* MIRI/MRS spectrum of IRAS 07251$-$0248 at $6.8-8.0$ $\mu$m in Fig. [10](#fighcnc2h2)a shows a forest of absorption lines that are identified with the gas-phase HCN 2$\nu_2$ 7.1 $\mu$m, C$_2$H$_2$ $\nu_4+\nu_5$ 7.5 $\mu$m, and CH$_4$ $\nu_4$ 7.7 $\mu$m bands (cite: gber25). Spectroscopic parameters for these species were obtained from the HITRAN2020 (cite: gor22) and ExoMol (cite: chu20; yur24) databases. The strengths of the individual lines (panel b) are comparable to those of the H$_2$O $\nu_2$ lines, which is surprising given that these bands are intrinsically weak. For the HCN 2$\nu_2$ and C$_2$H$_2$ $\nu_4+\nu_5$ bands, the Einstein coefficients for absorption of radiation ($B_{lu}$) are $\sim10^6$ and $\sim2.5\times10^6$ cm$^2$ erg$^{-1}$ s$^{-1}$, respectively, while the $B_{lu}$ values for the backbone-backbone transitions of the H$_2$O $\nu_2$ lines are factors of $\sim5$ and $\sim2$ higher.

We have used our model for the $H_C$, which dominates the continuum at these wavelengths, to fit these bands, with the goals of checking the excitation predicted by the continuum model and deriving the abundances of these species. Our model uses, as for H$_2$O, a $\lambda$-dependent covering factor $f_{\mathrm{hot}}$ as defined in eq. ([\[fhot\]](#fhot)) (Section [3.2](#sech2oband)). The dilution of the molecular absorption at $7-8$ $\mu$m is also due to the “hidden” 230 K component (Fig. [2](#sed)). The best-fit model is shown in Fig. [10](#fighcnc2h2)b. To explain the band strengths we require extraordinary abundances relative to H$_2$O, indicating an extreme C-rich chemistry: $\mathrm{[HCN]/[H_2O]}\approx0.56$, $\mathrm{[C_2H_2]/[H_2O]}\approx0.54$, and $\mathrm{[CH_4]/[H_2O]}\approx0.22$. These are within a factor 2 consistent with the values inferred by (cite: gber25).

The HCN $\nu_2$ 14 $\mu$m and C$_2$H$_2$ $\nu_5$ 13.7 $\mu$m bands are also clearly detected (Fig. [10](#fighcnc2h2)c). These bands have $B_{lu}$ values higher than the HCN and C$_2$H$_2$ $7.1-7.5$ $\mu$m bands by factors of $5-10$, and thus the P and R branch lines from the $H_C$ at 14 $\mu$m, predicted by our model for the $\sim7.5$ $\mu$m bands, would be expected to be strong. However, the $W_C$ continuum emission at 14 $\mu$m, here dominated by the $W_C$ 123 K component (Table [\[tab\]](#tab)), is expected to account for about half of the observed continuum (Figs. [2](#sed) and [10](#fighcnc2h2)c) and thus the 14 $\mu$m absorption from the $H_C$ is diluted with $f_{\mathrm{hot}}\sim0.5$ (Fig. [10](#fighcnc2h2)d). This dilution has the effect of reducing the predicted 14 $\mu$m high-$J$ molecular absorption troughs at levels comparable with the observations. Using a common model for the $H_C$, our composite continuum model thus yields consistent results for the 7.5 and 14 $\mu$m bands, which is required as the high-J lines of the R and P branches in both bands are produced by the same gas.

However, the Q branches of both 14 $\mu$m bands are saturated, and the model for the $H_C$ alone cannot reproduce them as they absorb more than 50% of the continuum. We have therefore added a model for the $W_C$ in Fig. [10](#fighcnc2h2)d that accounts for the remaining Q branch absorption, using a covering factor for the $W_C$ of $f_{\mathrm{warm}}=1-f_{\mathrm{hot}}$ (note that the $C_C$ contributes negligibly to the 14 $\mu$m continuum, Fig. [2](#sed)). The absorbing column densities of both HCN and C$_2$H$_2$ in the $W_C$ are $10^{17}$ cm$^{-2}$, generating absorption in the Q branches and in the low-$J$ lines of the P and R branches. The low-$J$ lines of the HCN 14 $\mu$m band have additional contribution by the low-excitation shell in front of the $H_C$, and indeed absorption is seen up to $\sim-500$ km s$^{-1}$ in the uncontaminated HCN $\nu_2$ R4 line (this has the effect of lowering the apparent $T_d$). The fit to the 14 $\mu$m bands tends to overestimate the absorption in high-excitation lines, most likely reflecting the uncertainties of $f_{\mathrm{hot}}$.

From the results for the HCN abundance found here and by (cite: gber25), and those for the HCO$^+$ abundance by (cite: spe25), a very high \[HCN\]/\[HCO$^+$\] abundance ratio of $\sim100$ is obtained in IRAS 07251$-$0248 E. This result can be related to the variety of HCN/HCO$^+$ rotational line ratios observed galaxies, and widely discussed in the literature (cite: kri08; ima09; izu16). While a high HCN/HCO$^+$ line ratio was first attributed to the chemistry involved in X-ray dominated regions around AGNs, further observations showing high ratios in non-AGN galaxies and low ratios in AGN have dismissed this relationship (cite: cos11; pri20). Recently, (cite: nis24) have identified the highest HCN/HCO$^+$ line ratios in shell-like structures kinematically associated with outflows or inflows, and their chemical models indeed indicate a strong enhancement of \[HCN\]/\[HCO$^+$\] in shock conditions. The nuclear conditions in IRAS 07251$-$0248 E are more extreme than those modeled by (cite: nis24), which are appropriate for the more extended regions probed by the rotational lines, but their shock models illustrate the high \[HCN\]/\[HCO$^+$\] ratio that can be attained in the outflow associated with the $H_C$. Nevertheless, the additional effect of cosmic rays in enhancing the ionization rate and processing the carbonaceous grains and PAHs are most likely required to explain the extreme $\mathrm{[HCN]/[H_2]}\sim4\times10^{-5}$ we find in the nucleus of IRAS 07251$-$0248 E.

Finally, we have also applied the $H_C$ model to the CO$_2$ $\nu_3$ ($4.25$ $\mu$m) and $\nu_2$ ($14.97$ $\mu$m) bands (Fig. [11](#figco2)). The best fit model to both the CO$_2$ $\nu_3$ R branch and the $\nu_2$ Q branch requires $\mathrm{[CO_2]/[H_2O]}\approx0.03$ at the $H_C$ photosphere, with an additional contribution by the surrounding outflowing shell with $\mathrm{[CO_2]/[H_2O]}\approx0.014$. The fit, however, grossly underestimates the strength of the CO$_2$ $\nu_3$ P branch up to $J\sim20$, so we added foreground CO$_2$ ice with $\mathrm{H_2O:CO_2=10:1}$ (cite: ehr97; roc22). The resulting modeled spectrum appears to overestimate the absorption in the high-$J$ lines of the $\nu_3$ P branch, but fits both the $\nu_3$ R branch at 4.23 $\mu$m and the $\nu_2$ Q branch at 15 $\mu$m rather well. This match validates our fit to the $H_C$ continuum.

[^1]: We use luminosities integrated from 3 to $1200$ $\mu$m (basically TIR) because the nuclear component emits strongly below 10 $\mu$m, as seen below.

[^2]: Here we define $\Sigma_{\mathrm{bol}}$ as $L_{\mathrm{bol}}/(4\pi R^2)$, where $R$ is the radius of the equivalent sphere, and modify the published values in case that $\Sigma_{\mathrm{bol}}$ is defined in a different way.

</paper>

Write the methods card for this paper.