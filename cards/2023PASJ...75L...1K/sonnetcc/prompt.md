# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2023PASJ...75L...1K\sonnetcc\reply.txt

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
 "bibcode": "2023PASJ...75L...1K",
 "title": "ALMA detection of 321 GHz water maser emission in the radio galaxy NGC 1052",
 "year": 2023,
 "journal": "Publications of the Astronomical Society of Japan",
 "first_author": "Kameno, Seiji",
 "n_authors": 7,
 "arxiv_id": "2302.04211",
 "doi": "10.1093/pasj/psad011",
 "alma_projects_linked_by_archive": [
  "2021.1.00341.S"
 ]
}
```

Paper text:
<paper>
# ALMA Detection of 321 GHz water maser emission in the radio galaxy NGC 1052

## Abstract

The Atacama Large Millimeter/submillimeter Array (ALMA) serendipitously detected H$_2$O $J_{Ka, Kc} = 10_{2,9} - 9_{3,6}$ emission at 321 GHz in NGC 1052. This is the first submillimeter maser detection in a radio galaxy and the most luminous 321-GHz H$_2$O maser known to date with the isotropic luminosity of 1090 $L_{\Sol}$. The line profile consists of a broad velocity component with FWHM $= 208 \pm 12$ km s$^{-1}$ straddling the systemic velocity and a narrow component with FWHM $= 44 \pm 3$ km s$^{-1}$ blueshifted by 160 km s$^{-1}$. The profile is significantly different from the known 22-GHz $6_{1,6} - 5_{2,3}$ maser which shows a broad profile redshifted by 193 km s$^{-1}$. The submillimeter maser is spatially unresolved with a synthesized beam of $0^{\prime \prime}.68 \times 0^{\prime \prime}.56$ and coincides with the continuum core position within 12 pc. These results indicate amplification of the continuum emission through high-temperature ($>1000$ K) and dense ($n({\rm H}_2{\rm O}) > 10^4$ cm$^{-3}$) molecular gas in front of the core.

Joint ALMA Observatory, Alonso de Córdova 3107 Vitacura, Santiago 763-0355, Chile National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan Institute for Cosmic Ray Research, The University of Tokyo, 5-1-5 Kashiwanoha, Kashiwa, Chiba 277-8582, Japan Graduate School of Science, Osaka Metropolitan University, 1-1 Gakuen-cho, Naka-ku, Sakai, Osaka, 599-8531, Japan

# Introduction

Extragalactic H$_2$O masers (megamasers) are known to originate in sub-pc-scale disks rotating around supermassive black holes in active galactic nuclei (AGNs) (cite: 1995Natur.373..127M; 1995PNAS...9211427M; 2022NatAs...6..885I). Thanks to their compact and bright nature, megamasers allow $\mu$as-resolution VLBI observations (cite: 2022NatAs...6..976B) making them powerful probes to weigh black-hole mass, to trace accretion matter, and to measure geometrical distance and constrain cosmological parameters (cite: 2013ApJ...775...13H). To date 150 AGNs are known to harbor the $J_{Ka, Kc} = 6_{1,6} - 5_{2,3}$ maser at 22 GHz (cite: 2018IAUS..336...86B).

The radio galaxy NGC 1052 is a unique megamaser found in an elliptical galaxy with double-sided sub-relativistic jets (cite: 1994ApJ...437L..99B; 1998ApJ...500L.129C), while the majority of megamasers are radio-quiet AGNs in spiral galaxies. NGC 1052 shows the 22-GHz maser spectrum spanning $\sim 400$ km s$^{-1}$ (cite: 1998ApJ...500L.129C; 2003ApJS..146..249B; 2005ApJ...620..145K) which is smooth and broad as for radio-loud minorities such as TXS 2226-184 (cite: 1995Natur.378..697K), Mrk 348 (cite: 2003ApJ...590..149P) and Centaurus A (cite: 2013ApJ...771L..41O), unlike archetypal megamasers which display narrow spikes $<20$ km s$^{-1}$ spread over $\sim \pm 1000$ km s$^{-1}$ tracing (sub-)Keplerian rotation (cite: 1993Natur.361...45N; 2008ApJ...672..800H). H$_2$O masers in Mrk 348 and Centaurus A are interpreted to be excited in shocked molecular gas by interaction with jets (cite: 2003ApJ...590..149P; 2013ApJ...771L..41O). The maser spots in NGC 1052 appear to have high brightness temperature exceeding $10^9$ K and lie along jets (cite: 1998ApJ...500L.129C). (cite: 2008ApJ...680..191S) revealed the spatial distribution of maser spots consisting of two clusters on the line of sight towards the continuum components in the eastern approaching side and western receding side of jets, and found positional coincidence of maser spots and the plasma torus which obscures the core by free–free absorption (FFA) casting a gap between two maser clusters (cite: 2001PASJ...53..169K; 2003PASA...20..134K; 2003A&A...401..113V; 2004A&A...426..481K). As the FFA opacity decreases at higher frequency, the gap disappears above 43 GHz, and the core takes over the steep-spectrum jets at higher frequency than 86 GHz (cite: 2016ApJ...830L...3S; 2016A&A...593A..47B; 2019A&A...623A..27B; 2019ApJ...872L..21S). In this context, submillimeter (sub-mm) observations are crucial to probe inside the obscuring torus.

The H$_2$O $10_{2,9} - 9_{3,6}$ maser at 321.225677 GHz is a new probe for AGNs. Excitation of the 321-GHz maser, with the lower energy level of 1846 K in the vibrational ground state, requires high temperature and high density for an inverted excitation condition. (cite: 2016MNRAS.456..374G) calculated the excitation condition of possible H$_2$O maser transitions for evolved star environments and clarified that the 321-GHz maser requires a physical temperature of $T_k > 1000$ K and high density of $n({\rm H}_2{\rm O}) > 10^4$ cm$^{-3}$. The 321-GHz maser condition implies closer location to a central engine than that of the 22-GHz maser, if found in an AGN.

(cite: 2013ApJ...768L..38H) surveyed five type-2 Seyfert galaxies selected by strong 22-GHz maser emission and discovered the first 321-GHz megamaser in the Circinus galaxy, followed by the second detection in NGC 4945 (cite: 2016ApJ...827...68P; 2016ApJ...827...69H). (cite: 2019asrc.confE..24B) referred the third detection in NGC 5643 by (cite: PesceInPrep).

So far, no radio-loud AGN has been identified as a 321-GHz maser source.

In this letter we present the first discovery of the 321-GHz maser in NGC 1052, coupled with monitoring of the 22-GHz maser to compare the spectral profiles. Since the monitoring was taken 16 years earlier than the 321-GHz observation, we do not attempt to perform a detailed comparison however. We employ the systemic velocity of $V_{\rm sys} = 1492$ km s$^{-1}$ and the luminosity distance of $D_L = 17.6$ Mpc.

# Observations

Reduction scripts and reduced data are available in the GitHub repository[^1].

## GBT

We observed the 22-GHz maser at 6 epochs; 2005-11-18, 2005-11-28, 2005-12-07, 2005-12-20, 2005-12-27, and 2006-01-13 using the Green Bank Telescope (GBT) with the dual-beam dual-polarization receiving system. We followed the standard spectral calibration procedure using GBTIDL to obtain spectra with a velocity resolution of 0.33 km s$^{-1}$. The rms noise of the spectrum at each epoch was 2.3, 2.7, 2.1, 1.4, 4.6, and, 2.5 mJy, respectively. The continuum flux density was 1.451, 1.131, 1.365, 1.272, 1.505, and 1.168 Jy, respectively, involving systematic errors of $\sim 10$% in flux scaling and off-source subtraction.

## ALMA

The Atacama Large Millimeter/submillimeter Array (ALMA) observations with 41 12-m antennas were carried out on 2022-05-12, as the PI science project 2021.1.00341.S targeting a high-redshift galaxy. The operations software selected NGC 1052 as a phase calibrator within $15^{\circ}$ from the target and J$0423-0120$ as a bandpass calibrator. On-source integration were 30 s $\times 4$ scans and a 912 s scan, respectively. Four spectral windows (SPWs) with a 1875-MHz bandwidth were centered at 306.4, 308.2, 318.4 and 320.2 GHz. The spectral resolution was 7.8125 MHz corresponding to 7.3 km s$^{-1}$. The image rms was 3.3 mJy/beam/ch with the synthesized beam of $0^{\prime \prime}.68 \times 0^{\prime \prime}.56$ with PA$=79^{\circ}$

![](NGC1052_maser_series.pdf)

![](NGC1052_Cont+Maser_Map.pdf)

![](UVplot.pdf)

# Results

Continuum-subtracted spectra are shown in Fig.[1](#fig:maser_series) together with absorption lines of H$_2$O $5_{5,0}-6_{4,3}$, $v_2=1$, HCN $1-0$, and $4-3$ (cite: 2020ApJ...895...73K; 2023ApJsubmitted). The 22-GHz maser showed broad spectra in the velocity range of $1450 - 1850$ km s$^{-1}$ with time-variable narrower components. The centroid of the 22-GHz emission remained at $1685 \pm 4$ km s$^{-1}$, which was redshifted with respect to the systemic velocity by 193 km s$^{-1}$. The 321-GHz H$_2$O emission profile was biased blueward, which was fitted by two Gaussian components: (a) a broad component with the center velocity of $1467 \pm 5$ km s$^{-1}$ and FWHM of $208 \pm 12$ km s$^{-1}$, and (b) a narrow component with the center velocity of $1333 \pm 1$ km s$^{-1}$ with FWHM of $44 \pm 3$ km s$^{-1}$. The peak flux density was 0.07 Jy at 1334 km s$^{-1}$.

We produced channel maps of the 321-GHz H$_2$O line with a velocity slice of 20 km s$^{-1}$ in $1280$ km s$^{-1} \leq V_{\rm LSR} \leq 1580$ km s$^{-1}$ and measured the position by 2-D Gaussian fitting in the channel maps. Fig.[2](#fig:maserMap) shows the position of each channel registered on the continuum image. These coincided with the continuum position with an upper limit of $0^{\prime \prime}.14$ corresponding to 12 pc, except one outlier offset by $0^{\prime \prime}.29 \pm 0^{\prime \prime}.03$ at 1560 km s$^{-1}$ with a signal-to-noise ratio as low as 4.3. No significant velocity gradient was found.

The continuum component was unresolved with flux densities of 0.401 Jy and 0.380 Jy at 307.3 GHz and 319.3 GHz, respectively. The upper limits (99% confidence) of the FWHM size were $0^{\prime \prime}.024$ and $0^{\prime \prime}.12$ for the continuum and the continuum-subtracted velocity-integrated emission line, respectively, as shown in Fig.[3](#fig:uvplot).

# Discussion

## Justification for maser emission

The 321-GHz H$_2$O emission size of FWHM $\leq 0^{\prime \prime}.12$ and peak flux density of 0.07 Jy yields a brightness temperature of $T_{\rm B} \geq 43$ K. The ALMA array configuration was too compact ($<500.2$ m) to rule out the possibility of thermal emission. Nevertheless, ancillary evidence indicates that the emission is non-thermal maser.

All thermal molecular transitions, including H$_2$O $5_{5,0}-6_{4,3}$, $v_2=1$, appeared in absorption straddling the systemic velocity at the core position of NGC 1052 (cite: 2020ApJ...895...73K). CO $J=2-1$ and $3-2$ appeared as the sole thermal emission in the circum-nuclear disk (CND) extended in $230 \times 60$ pc off the continuum core, while they appeared in absorption toward the core (cite: 2020ApJ...895...73K). The 321-GHz emission locates within 12 pc from the radio continuum, much more compact than the CND. The integrated flux density of the 321-GHz H$_2$O emission was 10.5 Jy km s$^{-1}$ exceeding the 1.55 Jy km s$^{-1}$ and 7.96 Jy km s$^{-1}$ of CO emissions. The CND cannot harbor the 321-GHz H$_2$O emission.

Since the brightness temperature of the continuum emission exceeds $10^8$ K (cite: 2004A&A...426..481K), molecular gas covering the continuum source must be seen in absorption except non-thermal emission. Thus, the 321-GHz H$_2$O emission at the same position of the core is probably non-thermal maser. Longer-baseline ($> 3500$ m) observations would provide more concrete constraints on the brightness temperature $> 2000$ K.

## Spectral profiles and location of masers

Observed maser intensity is a product of the background brightness and amplification gain through population-inverted H$_2$O molecules. A line width becomes progressively narrower than the thermal width as it gains more amplification (cite: 2003adu..book.....D). The wide velocity width in NGC 1052 indicates small amplification gain and requires bright background continuum emission. Thus, the position of maser spots is related to the continuum structure. That characteristic is consistent with the smooth systemic-velocity components and is different from narrow spikes in archetypal megamasers.

(cite: 2008ApJ...680..191S) revealed that the position of 22-GHz masers in NGC 1052 coincides with the intensity peaks of the double-sided jets where the FFA opacity is not too high. The continuum core is hidden in the optically-thick gap at 22 GHz to generate 22-GHz maser avoidance. The GBT monitoring of 22-GHz maser emission always shows redshifted profiles with respect to the systemic velocity, implying an inward stream of the excited H$_2$O molecule inside the near side of the torus.

The continuum structure at higher frequency is more dominated by a compact core with a smaller contribution from steep-spectrum jets, and the gap due to FFA disappears in millimeter (mm) wavelengths (cite: 2016ApJ...830L...3S; 2016A&A...593A..47B; 2019A&A...623A..27B; 2019ApJ...872L..21S). Thus, the 321-GHz maser is considered to pinpoint the compact core and is amplified by population-inverted H$_2$O molecules with a temperature $>1000$ K. (cite: 2020ApJ...895...73K) found sub-mm molecular absorption features (see HCN $4-3$ in Fig.[1](#fig:maser_series)) that implied presence of a massive molecular torus covering the continuum source. The velocity ranges of the sub-mm absorption lines straddle the systemic velocity and resemble that of the broad component of the 321-GHz maser. This supports that molecular gas in the torus causes absorption and stimulated emission along the line of sight to the compact core.

(cite: 2023ApJsubmitted) found mm (86 – 130 GHz) molecular absorption features and identified different line profiles from sub-mm ones (see HCN $1-0$ and $4-3$ in Fig.[1](#fig:maser_series)). The difference is ascribed to the continuum structure dominated by the jet at mm and the core at sub-mm as mentioned in the former paragraph. The temperature of SO absorption lines were $26 \pm 4$ K and $344 \pm 43$ K for mm and sub-mm, respectively. The difference in temperatures also indicate that mm and sub-mm absorption lines represent different absorbers.

The torus is expected to consist of multiple layers with temperatures of $\geq 10^4$ K, $\geq 1000$ K, $\geq 400$ K, and $344 \pm 43$ K that accounts for the FFA, 321-GHz maser, 22-GHz maser, and sub-mm SO absorption region, respectively. (cite: 2023ApJsubmitted) interpret that SO molecules evaporate from dust grains through jet-torus interaction and the high temperature is maintained by shock heating. The shock heating also explains the excitation of the 321-GHz maser.

Since the mm SO absorber is too cold to excite the maser, downstream of the jets is unlikely to harbor the 321-GHz maser.

## Comparison with the Circinus galaxy and NGC 4945

In this subsection we compare the properties of the H$_2$O maser in NGC 1052 with those in NGC 4945 and the Circinus galaxy referring to (cite: 2021ApJ...923..251H).

The isotropic luminosity is estimated to be 176 $L_{\Sol}$ and 1090 $L_{\Sol}$ for 22-GHz and 321-GHz masers, respectively, using the formula $\displaystyle L = 1.04 \times 10^{-3} \nu_{\rm rest}, D^2_{L} \int S(v) \ dv$. These values are 5.5 times and 17 times larger than those of the Circinus galaxy. The ratio of the 321-GHz maser peak flux to continuum flux in NGC 1052 is 0.19, which is significantly smaller than that of 3.2 and 37 in the Circinus galaxy on 2012-06-03 and 2017-05-06, respectively. The ratio in NGC 4945 was 0.29 on 2012-06-03 and there was a non detection on 2017-05-06. Since the ratio is an indicator of maser amplification gain, the high isotropic luminosity in NGC 1052 is ascribed to the brighter continuum. The broader maser feature is consistent with less narrowing with the lower amplification gain. It is difficult to establish the degree of blending of multiple narrower features making up the spectrum in these observations however.

While the Circinus galaxy and NGC 4945 harbor high-velocity components $\sim 1000$ km s$^{-1}$ with respect to the systemic velocity, such components are not identified in NGC 1052. (cite: 1995PNAS...9211427M) interpreted the high-velocity components of 22-GHz masers as self-amplification of long velocity-coherent gain path through the rotating disk without a background continuum source. Presence of the systemic-velocity component and absence of high-velocity components in NGC 1052 also support lower gain amplification of brighter continuum.

# Summary

ALMA observations of NGC 1052 revealed the presence of 321 GHz H$_2$O emission with the isotropic luminosity of 1090 $L_{\Sol}$ which is in all probability the first sub-mm maser in a radio galaxy. The sub-mm maser profile straddles the systemic velocity of the galaxy, similar to sub-mm molecular absorption lines, unlike the redshifted profile of the 22-GHz maser. Although the sub-mm maser distribution is unresolved, the inferred location is between the two clusters of 22-GHz masers pinpointing the compact continuum core.

Followup ALMA observations of the 321 GHz emission, in order to establish variability and polarization in that line, as well as searching for emission in other H$_2$O maser lines such as at 183 and 325 GHz, could also provide valuable information on the nucleus of this target. Sub-mm VLBI observations are desired to resolve the structure of the maser and unveil the dynamics and the excitation mechanism in the sub-pc region of AGN.

This letter makes use of the following GBT and ALMA data: GBT 05C-034 and ADS/JAO.ALMA#2021.1.00341.S. The Green Bank Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work is supported by JSPS KAKENHI 18K03712 and 21H01137.

(ref: 2022NatAs...6..976B) Baan, W. A., An, T., Henkel, C., et al. 2022, Nature Astronomy, 6, 976

(ref: 2016A&A...593A..47B) Baczko, A.-K., Schulz, R., Kadler, M., et al. 2016, A&A, 593, A47

(ref: 2019A&A...623A..27B) Baczko, A.-K., Schulz, R., Kadler, M., et al. 2019, A&A, 623, A27

(ref: 1994ApJ...437L..99B) Braatz, J. A., Wilson, A. S., & Henkel, C. 1994, ApJL, 437, L99. doi:10.1086/187692

(ref: 2019asrc.confE..24B) Braatz, J. 2019, ALMA2019: Science Results and Cross-Facility Synergies, 24

(ref: 2018IAUS..336...86B) Braatz, J., Condon, J., Henkel, C., et al. 2018, Astrophysical Masers: Unlocking the Mysteries of the Universe, 336, 86

(ref: 2003ApJS..146..249B) Braatz, J. A., Wilson, A. S., Henkel, C., et al. 2003, ApJS, 146, 249

(ref: 1998ApJ...500L.129C) Claussen, M. J., Diamond, P. J., Braatz, J. A., et al. 1998, ApJL, 500, L129

(ref: 2003adu..book.....D) Dopita, M. A. & Sutherland, R. S. 2003, Astrophysics of the diffuse universe, Berlin, New York: Springer, 2003. Astronomy and astrophysics library, ISBN 3540433627

(ref: 2016MNRAS.456..374G) Gray, M. D., Baudry, A., Richards, A. M. S., et al. 2016, MNRAS, 456, 374

(ref: 2008ApJ...672..800H) Humphreys, E. M. L., Reid, M. J., Greenhill, L. J., et al. 2008, ApJ, 672, 800

(ref: 2013ApJ...775...13H) Humphreys, E. M. L., Reid, M. J., Moran, J. M., et al. 2013, ApJ, 775, 13

(ref: 2013ApJ...768L..38H) Hagiwara, Y., Miyoshi, M., Doi, A., et al. 2013, ApJL, 768, L38

(ref: 2016ApJ...827...69H) Hagiwara, Y., Horiuchi, S., Doi, A., et al. 2016, ApJ, 827, 69

(ref: 2021ApJ...923..251H) Hagiwara, Y., Horiuchi, S., Imanishi, M., et al. 2021, ApJ, 923, 251

(ref: 2005ApJ...629..719H) Herrnstein, J. R., Moran, J. M., Greenhill, L. J., et al. 2005, ApJ, 629, 719

(ref: 2022NatAs...6..885I) Impellizzeri, C. M. V. 2022, Nature Astronomy, 6, 885

(ref: 2004A&A...426..481K) Kadler, M., Ros, E., Lobanov, A. P., et al. 2004, A&A, 426, 481

(ref: 2001PASJ...53..169K) Kameno, S., Sawada-Satoh, S., Inoue, M., et al. 2001, PASJ, 53, 169

(ref: 2003PASA...20..134K) Kameno, S., Inoue, M., Wajima, K., et al. 2003, PASA, 20, 134

(ref: 2005ApJ...620..145K) Kameno, S., Nakai, N., Sawada-Satoh, S., et al. 2005, ApJ, 620, 145

(ref: 2020ApJ...895...73K) Kameno, S., Sawada-Satoh, S., Impellizzeri, C. M. V., et al. 2020, ApJ, 895, 73

(ref: 2023ApJsubmitted) Kameno, S., Sawada-Satoh, S., Impellizzeri, C. M. V., et al. 2023, to appear in ApJ

(ref: 1995Natur.378..697K) Koekemoer, A. M., Henkel, C., Greenhill, L. J., et al. 1995, Nature, 378, 697

(ref: 1995Natur.373..127M) Miyoshi, M., Moran, J., Herrnstein, J., et al. 1995, Nature, 373, 127

(ref: 1995PNAS...9211427M) Moran, J., Greenhill, L., Herrnstein, J., et al. 1995, Proceedings of the National Academy of Science, 92, 11427

(ref: 1993Natur.361...45N) Nakai, N., Inoue, M., & Miyoshi, M. 1993, Nature, 361, 45

(ref: 2013ApJ...771L..41O) Ott, J., Meier, D. S., McCoy, M., et al. 2013, ApJL, 771, L41

(ref: 2003ApJ...590..149P) Peck, A. B., Henkel, C., Ulvestad, J. S., et al. 2003, ApJ, 590, 149

(ref: 2016ApJ...827...68P) Pesce, D. W., Braatz, J. A., & Impellizzeri, C. M. V. 2016, ApJ, 827, 68

(ref: PesceInPrep) Pesce, D. W. in preparation

(ref: 2008ApJ...680..191S) Sawada-Satoh, S., Kameno, S., Nakamura, K., et al. 2008, ApJ, 680, 191

(ref: 2016ApJ...830L...3S) Sawada-Satoh, S., Roh, D.-G., Oh, S.-J., et al. 2016, ApJL, 830, L3

(ref: 2019ApJ...872L..21S) Sawada-Satoh, S., Byun, D.-Y., Lee, S.-S., et al. 2019, ApJL, 872

(ref: 2003A&A...401..113V) Vermeulen, R. C., Ros, E., Kellermann, K. I., et al. 2003, A&A, 401, 113

[^1]: https://github.com/kamenoseiji/ALMA-2021.1.00341.S

</paper>

Write the methods card for this paper.