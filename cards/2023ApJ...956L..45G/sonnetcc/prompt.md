# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2023ApJ...956L..45G\sonnetcc\reply.txt

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
 "bibcode": "2023ApJ...956L..45G",
 "title": "An SiO Toroid and Wide-angle Outflow Associated with the Massive Protostar W75N(B)-VLA2",
 "year": 2023,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Gómez, José F.",
 "n_authors": 15,
 "arxiv_id": "2310.08086",
 "doi": "10.3847/2041-8213/ad01bd",
 "alma_projects_linked_by_archive": [
  "2019.1.00059.S"
 ]
}
```

Paper text:
<paper>
# An SiO Toroid and Wide-angle Outflow associated with the Massive Protostar W75N(B)-VLA2

## Abstract

We have carried out ALMA observations of the massive star-forming region W75N(B), which contains the massive protostars VLA1, VLA2, and VLA3. Particularly, VLA2 is an enigmatic protostar associated with a wind-driven H$_2$O maser shell, which has evolved from an almost isotropic outflow to a collimated one in just 20 years. The shell expansion seemed to be halted by an obstacle located to the northeast of VLA2. Here we present our findings from observing the 1.3 mm continuum and H$_2$CO and SiO emission lines. Within a region of $\sim$30$''$ ($\sim$39,000 au) diameter, we have detected 40 compact mm-continuum sources, three of them coinciding with VLA1, VLA2, and VLA3. While the H$_2$CO emission is mainly distributed in a fragmented structure around the three massive protostars, but without any of the main H$_2$CO clumps spatially coinciding with them, the SiO is highly concentrated on VLA2, indicating the presence of very strong shocks generated near this protostar. The SiO emission is clearly resolved into an elongated structure ($\sim 0.6''\times0.3''$; $\sim 780$ au$\times$390 au) perpendicular to the major axis of the wind-driven maser shell. The structure and kinematics of the SiO emission are consistent with a toroid and a wide-angle outflow surrounding a central mass of $\sim$10 M$_{\odot}$, thus supporting previous theoretical predictions regarding the evolution of the outflow. Additionally, we have identified the expected location and estimated the gas density of the obstacle that is hindering the expansion of the maser shell.

# Introduction

Understanding how massive stars form and evolve remains a major challenge in astrophysics. One of the observational approaches to advance in this field has been to search for systems with disks and jets in massive protostars deeply embedded in their parental molecular clouds, trying to find similarities with the formation and evolution of low-mass stars. Thus, several disk-jet systems in massive protostars are known today, indicating that they likely form in a similar way to low-mass stars, following the so-called monolithic core-accretion model, e.g., Cep A HW2 (cite: Patel05; Jimenez07; Sanna17), HH 80-81 (cite: Girart18; Anez20). However, in the last years, several observational studies have indicated that during the early stages of evolution of massive protostars there may be episodic events of short duration (tens of years) associated with very poorly collimated or near-isotropic outflows (cite: Torrelles01; Kim13; Surcis14; Carrasco15; Bartk20). These results are surprising since, according to the core-accretion model, collimated outflows are already expected in the earliest phases of star formation, rather than outflows that expand without any preferential direction. This expectation has been also confirmed with high-resolution observations of high-mass protostars in clustered star forming regions (cite: Goddi20). Therefore, it is still an open question whether the collimation and mass-ejection mechanisms in the early life of massive protostars differ from the case of low-mass protostars (cite: Carrasco21). This has important consequences for having a global vision of star formation, since mass ejection is related to the accretion process and then to the evolution of the protostar to its final mass.

A very enigmatic case is the massive protostar W75N(B)-VLA2. Through a research program consisting of monitoring for more than 20 years an expanding water-vapor maser shell and the radio continuum emission associated with this source, it has been possible to observe the transformation of a short-lived, originally poorly collimated outflow from a massive protostar into a collimated jet, as reported by (cite: Carrasco15). This sudden change of the outflow morphology has been modeled by these authors in terms of an episodic, short-lived, originally isotropic, ionized wind that drives the observed maser shell around VLA2 and whose morphology evolves as a consequence of the interaction with a toroidal density stratification. However, these expanding motions are not symmetric because they seem to be halted by a possible dense obstacle at a distance of $\sim$0.2$''$ to the northeast of VLA2, as recently suggested by (cite: Surcis23) through a monitoring of the H$_2$O maser emission with the European VLBI Network (EVN). A detailed description of the main properties of VLA2, as well as those of the other massive protostars in the high-mass star-forming region W75N(B), which is located at a distance of 1.3 kpc (cite: Rygl12), can be found in (cite: Surcis23).

In this work, we present Atacama Large Millimeter/submillimeter Array (ALMA) continuum and H$_2$CO and SiO line observations at 1.3 mm wavelength toward the brightest mm core of the W75N(B) region, MM1 (cite: Shepherd01; Minh10; R-K20; vanderWalt21), which contains the massive protostars VLA1, VLA2, and VLA3 seen at radio continuum wavelengths (cite: Hunter94; Torrelles97; R-K20). These protostars have individual masses equivalent to B1-B0.5 spectral type stars (cite: Shepherd01). The main goal of our ALMA observations was to test the presence of the molecular toroid around VLA2 predicted by previous works (cite: Carrasco15), as well as to study the distribution of gas and dust in the environment of these massive protostars. In a forthcoming paper we will analyze the emission from the other multiple molecular lines detected in this very active high-mass star-forming region.

# Observations

The ALMA observations in Band 6 ($\lambda$ = 1.1-1.4 mm; project 2019.1.00059.S; PI: Jeong-Sook Kim) were performed on four different sessions, and using two different array configurations: configuration C43-5 on 2021 April 29 (baselines 14–1261m) and 2022 August 2 (baselines 15–1301m), and configuration C43-8 on 2021 August 18 (baselines 92–8282m) and 2021 October 28 (baselines 63–8282m). The average observing time per session was $\sim$45 min, including calibration. The source J0006-0623 was used as flux and bandpass calibrator, while J2007+4029 was used as complex gain calibrator. The pointing position for the target W75N(B)-VLA2 was $\alpha$(J2000) = 20$^h$38$^m$36.486$^s$, $\delta$(J2000) = 42$^{\circ}$37$'$34.09$''$. The spectral setup consisted in six spectral windows with different bandwidths (BW) and velocity resolutions ($\Delta$V$_{ch}$), five of them centered on the rest frequencies (RF) of the molecular lines H$_2$CO \[3(0,3)-2(0,2)\], SiO \[v=0, 5-4\], C$^{18}$O \[2-1\], $^{13}$CO \[2-1\], $^{12}$CO \[2-1\], plus a continuum bandwidth (see Table [1](#tab:setup)). The ALMA data were pipeline calibrated, reduced, and analyzed with CASA version 6.2.1.7 (cite: casa22). The continuum data (obtained from line free-channels of the spectral windows plus the continuum spectral window) were self-calibrated and their solutions applied also to the spectral line data. For imaging, we used task tclean of CASA, with a Brigg’s weighting of visibilities, and a robust parameter of 0.5 (unless otherwise noted), resulting in a synthesized beam of $\sim 0.17''\times 0.08''$ (PA $\simeq -2^{\circ}$). A high dynamic range for the continuum image of $\sim$1,100 (rms = 0.08 mJy beam$^{-1}$) was reached after self-calibration (Fig. [1](#fig:continuum)). Images presented in this paper were corrected by the primary beam response, which has a full width at half maximum of $\simeq$ 25$''$ at 230 GHz.

|                           |            |        |                  |
|:-------------------------:|:----------:|:------:|:----------------:|
|      Spectral Window      |     RF     |   BW   | $\Delta$V$_{ch}$ |
|                           |   (GHz)    | (MHz)  |  (km s$^{-1}$)   |
| H$_2$CO \[3(0,3)-2(0,2)\] | 218.222192 | 468.75 |      0.775       |
|     SiO \[v=0, 5-4\]      | 217.104980 | 468.75 |      0.779       |
|     C$^{18}$O \[2-1\]     | 219.560358 | 234.38 |      0.385       |
|     $^{13}$CO \[2-1\]     | 220.398684 | 234.38 |      0.384       |
|     $^{12}$CO \[2-1\]     | 230.538000 | 468.75 |      0.734       |
|         Continuum         | 231.805970 | 1,875  |      40.443      |

: Spectral setup

# Results

## Dust continuum emission

![](Continuum_v3.pdf)

Figure [1](#fig:continuum) shows the continuum image obtained towards the central part of the W75N(B) region. The millimeter cores MM1, MM2, and MM3 (cite: Minh10; R-K20; vanderWalt21), are now resolved into multiple compact millimeter sources. All known radio continuum sources at centimeter wavelengths in this region (cite: R-K20), except Bc\[E\], Bc\[W\], Bd, and VLA4, have associated continuum emission at millimeter wavelengths, further reinforcing that VLA1, VLA2, VLA3, VLA\[SW\], and VLA\[NE\] are embedded protostars. The full width at half maximum (FWHM) of these continuum sources is unresolved by our beam. On the other hand, the fact that Bc\[E\], Bc\[W\], Bd, and VLA4 have no continuum emission at millimeter wavelengths (Fig. [1](#fig:continuum)) gives support to the interpretation by (cite: Carrasco10) and (cite: R-K20), through proper motion measurements, that these four objects are not embedded protostars, but obscured Herbig-Haro (HH) objects excited by the massive protostar VLA3.

In order to better distinguish weak compact mm continuum sources from extended emission present in the region (see Fig. [1](#fig:continuum)), we obtained images that exclude baselines shorter than 200 k$\lambda$, thus filtering out large-scale structures, in a similar way as in (cite: Girart18) and (cite: Busquet19). With this baseline restriction, 40 unresolved continuum sources have been identified in a region of $\sim$30$''$ ($\sim$39,000 au) diameter centered on VLA2, and with flux densities in the range of $\sim$0.4–90 mJy beam$^{-1}$ (Table [2](#tab:possources), Fig. [5](#fig:sources)). We are proposing, in particular, that one of these detected sources (ID 32 in Table [2](#tab:possources)) is the powering source of the highly collimated bipolar jet that we have detected $\sim$6$''$ ($\sim$7,800 au) northeast of VLA2 (see Appendix [8](#ap:siojet) and Fig. [7](#fig:siojet)), and that will be discussed in detail in a forthcoming paper.

## H$_2$CO line emission

![](H2CO-MOM0-1_v8.pdf)

The emission of the formaldehyde molecule is known to be a good tracer of dense gas ($n[{\rm H}_2] \gtrsim 5 \times 10^5 -10^6$ cm$^{-3}$) over a wide range of temperatures ($T_K \simeq 10-300$ K) in the cores of molecular clouds (cite: Mangum93; Shirley15). The integrated emission image obtained from the H$_2$CO \[3(0,3)-2(0,2)\] line in the velocity range $V_{\rm LSR} \simeq  -4$ to +23 km s$^{-1}$ (Fig. [2](#fig:h2co)a) shows a clumpy structure over a plateau of relatively weak emission covering a region of $\sim 3-4''$ ($\sim 3,900-5,200$ au). None of the main H$_2$CO clumps coincide with the position of any of the massive protostars VLA1, VLA2, or VLA3. The velocity field of the H$_2$CO emission (Fig. [2](#fig:h2co)b) shows that the greatest velocity differences are found along the northwest-southeast direction at angular scales of $\sim$3$''$ ($\sim$3,900 au), with blueshifted ($V_{\rm LSR}$ $\simeq$ +6 km s$^{-1}$) and redshifted velocities ($V_{\rm LSR}$ $\simeq$ +13 km s$^{-1}$) to the northwest and southeast of VLA2, respectively (cite: Surcis23). This direction also coincides with the orientation of the strongest H$_2$CO emission (Fig. [2](#fig:h2co)b) and consistent with the velocity field previously observed with the Submillimeter Array (SMA) and ALMA through different molecular species (e.g., H$_2$CO, CS, SO$_2$, CH$_3$OH), at scales of $\sim 4''$ and angular resolutions of $\sim 1''-2''$ (cite: Minh10; R-K20; vanderWalt21). In particular, (cite: vanderWalt21) suggested that the observed velocity shift is due to infalling gas onto a disk-like structure surrounding one of the massive protostars, but without being able to specify which one, probably due to an insufficient angular resolution in their observations ($\sim$1$''$). More recently, (cite: Zeng23) conclude that the gas infall proceeds along the magnetic field lines, as the gravitational force dominates over the magnetic field.

We suggest that the distribution of the clumpy H$_2$CO structure near but around VLA1, VLA2, and VLA3 could be due either to residual dense molecular gas fragments after the formation of these massive protostars, or to material still infalling toward the center of the region. This is supported by the fact that none of the main H$_2$CO clumps observed around the massive protostars have an associated mm continuum source (see Figs. [5](#fig:sources), [2](#fig:h2co)a, Table [2](#tab:possources)). The clumps observed in H$_2$CO have a relatively low mass of gas. For example, for the most intense clump (located $\sim0.2''-0.3''$ northeast of VLA2), assuming a density $n({\rm H}_2) \gtrsim (5\times 10^5)-10^6$ cm$^{-3}$, and adopting a diameter size of 0.5$''$ (650 au) from the emission image (Fig. [2](#fig:h2co)a), we roughly estimate a molecular mass $M({\rm H}_2) \gtrsim 4-8\times10^{-4}$ M$_{\odot}$. In addition, given its proximity to VLA2, we consider it plausible that this particular dense gas could be related to the obstacle predicted by (cite: Surcis23) to halt the expanding motions of the H$_2$O masers observed to the northeast of VLA2 (see Fig. [2](#fig:h2co) and discussion in §[4.2](#sec:halted)).

We also identify an H$_2$CO disk-like structure centered on VLA3 with a velocity gradient in the east-west direction (see Fig. [2](#fig:h2co)), therefore perpendicular to the VLA3 radio jet oriented in the north-south direction (cite: Carrasco10; R-K20). In addition, the H$_2$CO line is seen in absorption toward VLA3 (absorption is also observed in SiO at this location; see Fig. [6](#fig:absorption)). These results on VLA3 will be presented and discussed in a forthcoming paper.

## General distribution of the SiO line emission

The spatial and kinematic distribution of silicon monoxide emission is completely different from that of formaldehyde discussed in the previous section (§[3.2](#sec:h2co)). In Figure [3](#fig:sio)a we show the image of the integrated intensity of the SiO \[v=0, 5-4\] emission line covering the same spatial region as that of H$_2$CO in Figure [2](#fig:h2co)a. From the comparison of these two images (Figs. [2](#fig:h2co)a and [3](#fig:sio)a), we see that, while the H$_2$CO emission is distributed in several bright molecular clumps close, but not coinciding with any of the three massive protostars (VLA1, VLA2, VLA3), the SiO emission is strongly and almost exclusively concentrated around VLA2. This remarkable behavior related to the strong concentration of SiO emission on VLA2 had already been reported by (cite: Minh10) through SMA observations, but without resolving its spatial distribution. With our ALMA observations we now resolve the SiO emission around VLA2 into a northwest-southeast elongated structure with a size of $\sim0.6''\times0.3''$ ($\sim$780 au$\times$390 au; PA $\simeq$ $-$53$^{\circ}$), as seen in Figure [3](#fig:sio)b. The range of velocities with SiO emission observed within this elongated structure surrounding VLA2 is $V_{\rm LSR} \simeq -20$ to +28 km s$^{-1}$, which is significantly larger than that of H$_2$CO emission throughout all the region containing the three massive protostars (§[3.2](#sec:h2co)).

![](SiO-MOM0_v5.pdf)

The SiO emission is a well-known tracer of shocked gas, since the molecule is present in the gas phase in regions undergoing shocks with velocities of $\ensuremath{\gtrsim} 25$ km s$^{-1}$ (cite: Schilke97). Moreover, the SiO lines are high-density tracers and, for instance, the critical density of excitation for the SiO(5-4) transition is $\simeq 1.5\times10^{6}$ cm$^{-3}$ (cite: Huang22). These extreme properties of the SiO excitation, together with the distribution of its emission described above, lead us to conclude the presence of very strong shocks around VLA2. We think that this is a consequence of the high outflow activity that VLA2 has, with very intense H$_2$O masers expanding at several tens of km s$^{-1}$ driven by strong repetitive, short-lived ionized winds from the central source (cite: Torrelles03; Kim13; Carrasco15; Surcis23). All these properties observed in VLA2 are what make this massive protostar unique in comparison with the other two massive protostars in the region (VLA1 and VLA3). In §[4.1](#sec:toroid) we discuss and interpret the SiO structure with its kinematics in terms of a molecular toroid surrounding VLA2, together with a wide-angle outflow.

# Discussion

## The SiO toroid surrounding W75N(B)-VLA2

The elongated SiO structure ($\sim$780 au$\times$390 au, PA $\simeq$ $-$53$^{\circ}$; §[3.3](#sec:sio), Fig. [3](#fig:sio)b) that surrounds VLA2 is approximately perpendicular to the major axis of the expanding H$_2$O maser shell (cite: Surcis14; Surcis23), which, in its turn, is shock-excited and driven by the VLA2 ionized jet (cite: Carrasco15). We interpret this SiO molecular structure as the toroid whose existence was hypothesized and modeled by (cite: Carrasco15), as the collimating agent of an episodic, originally isotropic ionized wind associated with VLA2. These authors explain the observed evolution of a non-collimated outflow to a collimated outflow in VLA2 as due to a toroidal environmental density stratification, seen almost edge-on, with densities $\sim$5$\times$10$^{7}$ cm$^{-3}$ at distances of $\sim$28 au from the central massive protostar. This seems to be consistent with the fact that SiO(5-4) emission, which traces densities $\gtrsim$ 1.5$\times$10$^{6}$ cm$^{-3}$, is observed up to distances of $\sim$390 au from VLA2. Assuming this critical density of SiO as the minimum density for the entire toroid-like structure and given its observed size, a lower limit for the molecular mass $M({\rm H}_2) \gtrsim 2\times 10^{-3}$ M$_{\odot}$ is estimated. An independent estimate for a lower limit of the total mass (gas+dust) in this region can be obtained from the observed dust continuum emission of the unresolved VLA2 source (see §[6](#ap:sources)), under the assumption of optically thin emission and using Eq. [\[eq:massdust\]](#eq:massdust) (see §[6](#ap:sources)). Adopting $T_d$ = 300 K (a reasonable value for gas temperatures near the massive object, considering the presence of strong H$_2$O maser emission nearby, which implies that the gas should be at high-temperatures), we obtain a total mass (gas+dust) $\gtrsim 5\times 10^{-2}$ M$_{\odot}$ ($\gtrsim 51~M_J$; Table [2](#tab:possources)).

![](SiO-Kinematics_v3.pdf)

![](SiO-KinematicsB_V4.pdf)

Disk-like structures have been also reported in SiO emission surrounding other massive protostars (cite: Gomez99; Matthews10; Maud18). In particular, (cite: Maud18), through ALMA 1.3 mm observations, report a rotating SiO disk and a disk wind from the massive protostar G17.64+0.16 (probably an O-type star). The radius of the SiO disk structure in that object extends up to $\sim$600 au, similar to that of the SiO toroid observed around VLA2 (in terms of nomenclature we refer as toroids to disk-like structures with a size of $\sim$1,000 au). The very large velocity components observed in SiO within the VLA2 toroid ($V_{\rm LSR}\simeq -20$ to +28 km s$^{-1}$) are consistent with the velocities of the shocks needed to produce SiO as proposed by (cite: Maud18) for the disk (toroid) of G17.64+0.16. Similarly to G17.64+0.16, the shocks in VLA2 may originate at the inner edge and surface interface of the toroid by the fast expansion of the ionized wind and outflow (cite: Surcis14; Carrasco15).

Figure [4](#fig:siokine)a shows the position velocity (PV) diagram of the SiO emission along the major axis of the toroid-like structure (PA = $-$53$^{\circ}$) with an averaging width of 0.14$''$ (selected to optimize the visualization of the SiO kinematics). A velocity gradient of $\sim$6 km s$^{-1}$ is observed in the inner and most intense part of the SiO structure at angular scales of $\sim$0.1$''$ ($\sim$130 au), with the more blueshifted velocities to the northwest and the more redshifted velocities to the southeast. This velocity shift is in the same sense as the velocity shift observed northwest-southeast in H$_2$CO at larger scales (cite: Minh10) and in other molecular species (cite: R-K20). If the observed velocity shift of 6 km s$^{-1}$ is due to rotating motions at the inner parts ($\sim$130 au) of the toroid, those motions could be gravitationally bound by a central mass of $\sim$10 M$_{\odot}$ assuming Keplerian conditions, consistent with the expected mass of a B1-B0.5 espectral type star for VLA2 (cite: Shepherd01). However, it seems clear that observations at submillimetre wavelengths, with higher angular resolution than currently available in this work, are needed to resolve in more detail the kinematic behavior of molecular gas in the internal parts of the toroid (at angular scales of $\lesssim 0.1''$).

The weakest SiO emission displays high blueshifted velocities, reaching up to $V_{\rm LSR}$ $\simeq -17$ km s$^{-1}$, which appear as two rabbit-ear-shaped structures in the PV diagram along the major axis of the toroid (Fig. [4](#fig:siokine)a), and located symmetrically on both sides ($\sim\pm 0.2''$) of VLA2. Additionally, there is high redshifted velocity emission, with velocities up to $V_{\rm LSR}$ $\simeq +37$ km$^{-1}$, which is more apparent in the PV diagram along the minor axis of the SiO structure with an averaging width of $0.6''$ (Fig. [4](#fig:siokine)b). To explain these motions, which amount to approximately 27 km s$^{-1}$ relative to the ambient velocity ($V_{\rm LSR}$ = +10 km s$^{-1}$; e.g., Surcis et al. 2023), and considering the distances of 0.2$''$ (260 au), a central mass of around 210 M$_{\odot}$ would be required. However, such a mass is not observed, leading us to conclude that these high velocities traced by the weakest SiO emission represent unbound motions of an outflow originating from the outer parts ($\sim\pm 0.2''$) of the toroid.

Figure [4](#fig:siokine)c shows contour maps of the blueshifted ($V_{\rm LSR} = -16.6$ to $-3.1$ km s$^{-1}$) and redshifted ($V_{\rm LSR}$ = +23.9 to +37.4 km s$^{-1}$) SiO integrated emission, with the blueshifted lobe being stronger than the redshifted one. This figure allows us to identify the source of the two rabbit-ear-shaped structures observed in Figure [4](#fig:siokine)a as originating from the two peaks seen in the blueshifted lobe. These two peaks are separated by $\sim$0.4$''$, with the VLA2 source located between them.

It is worth noting that the SiO blueshifted lobe is slightly displaced towards the northeast of VLA2, while the redshifted lobe is slightly displaced towards the southwest (Fig. [4](#fig:siokine)c). This displacement is consistent with the direction observed in the CO bipolar outflow at parsec scales (cite: Davis98a; Davis98b; Shepherd03), indicating that the SiO outflow is being incorporated into the larger-scale molecular outflow, similar to the case of G17.64+0.16 (cite: Maud18). Furthermore, the morphological distribution of the two SiO outflow lobes (Fig. [4](#fig:siokine)c), which spatially surround VLA2, indicates the presence of a wide-angle outflow associated with this massive protostar.

Finally, we have considered the possibility that the two rabbit-ear-shaped structures that can be distinguished in Figure [4](#fig:siokine)a are due to the presence of two protostars embedded in the SiO toroid, one of which being VLA2. However, the fact that no other continuum source is detected, despite the high sensitivity of the data, together with the distribution of the two SiO outflow lobes around VLA2, makes this possibility very unlikely.

## A wind emerging from the toroid, interacting with a high-density gas obstacle

As metioned above, (cite: Carrasco15) showed that both, the VLA2 radio continuum source and the maser shell around it evolved in $\sim$20 years from a compact source into an elongated one in the northeast-southwest direction. They successfully modeled this behavior as due to the interaction of an episodic, short-lived isotropic ionized wind with a toroidal density stratification around the source. And we now find this toroidal structure, traced by the SiO emission.

Recently, (cite: Surcis23) found that the northeast part of the shell traced by the H$_2$O masers has stopped, and they suggest that this is due to the interaction of the shell with a high-density gas obstacle. An analytical and numerical simulation of such a situation by (cite: Canto06) show that, indeed, the interaction of a moving shell with a very dense medium can slow down the shell and stop its expansion completely. The detection of a strong H$_2$CO clump to the northeast of VLA2 as reported in the present paper (§[3.2](#sec:h2co), Fig. [2](#fig:h2co)a) seems to be consistent with the suggestion of (cite: Surcis23).

Following this idea, we can estimate the required gas density of the obstacle by assuming a balance between the thermal pressure of the gas in the clump and the ram pressure of the wind that drives the shell. That is,

$$\begin{equation}
 \label{eq:rampress}
nkT_k = \frac{\dot{M}_{w} V_{w}}{4\pi R^2},
 
\end{equation}$$ where $n$ is the density of the obstacle, $T_k$ its kinetic temperature, $k$ the Boltzmann constant, $\dot{M}_{w}$ and $V_{w}$ the mass-loss rate and terminal velocity of the isotropic wind, respectively, and $R$ the distance between the observed halted H$_2$O masers and the powering source of the wind. Solving for the density of the clump we find,

$$\begin{equation}
 \label{eq:densityclump}
\left[\frac{n}{\rm cm^{-3}}\right] = 1.6\times10^9 {\Large \frac{\left[\frac{\dot{M}_{w}}{\rm 10^{-7} M_{\odot}{yr}^{-1}}\right] \times \left[\frac{V_{w}}{\rm 100~km~s^{-1}}\right]}{\left[\frac{T_{k}}{\rm 10~K}\right] \times \left[\frac{R}{\rm 100~au}\right]^2}}.
 
\end{equation}$$ Assuming for $\dot{M}_{w}$ and $V_w$ the values quoted above from (cite: Carrasco15), together with $T_k$ = 300 K and R = 260 au (cite: Surcis23), we found $n \simeq 3.5\times 10^7-3.0\times10^8$ cm$^{-3}$. This is a very high density, but consistent with the fact that this obstacle is located within a very high-density region, close to the observed H$_2$CO clump to the northeast of VLA2 (Fig. [2](#fig:h2co)a) and to the outer parts of the SiO toroid (Fig. [3](#fig:sio)b). In addition, we should also consider that the density we estimated for the obstacle to halt the expanding motions of the H$_2$O masers to the northeast of VLA2 is likely to be an upper limit to the actual density. This is so because: 1) we have calculated the gas pressure (left expression of Eq. [\[eq:rampress\]](#eq:rampress)) from the kinetic temperature only, but if the clump has turbulent motions (cite: Surcis23) the actual pressure will be higher; 2) the ram pressure (right expression in Eq. [\[eq:rampress\]](#eq:rampress)) assumes that the shock is normal to the direction of the wind, but any deviation from this condition will produce a lower ram pressure; 3) to estimate the density in Eq. [\[eq:densityclump\]](#eq:densityclump), we have used the projected distance between the obstacle and the source, but the actual linear distance might be longer.

# Summary

Observations of the W75N(B) massive star-forming region using ALMA at a wavelength of 1.3 mm (beam $= 0.17''\times0.08''$, PA = $-2^{\circ}$) are presented, focusing on the continuum, H$_2$CO, and SiO lines. This region contains several massive protostars, including VLA1, VLA2, and VLA3, which are clustered within an area of $\sim$2$''$ in size ($\sim$2,600 au). The most relevant results are summarized as follows:

- We detected 40 compact 1.3 mm continuum sources within an area of $\sim 30''$ diameter ($\sim 39,000$ au), with three of them coinciding with VLA1, VLA2, and VLA3. The majority of these sources are new detections and are likely indicative of low- or intermediate-mass YSOs.

- The H$_2$CO emission is distributed in a clumpy structure around VLA1, VLA2, and VLA3. In contrast, the SiO emission is highly concentrated almost exclusively on VLA2, implying the presence of intense shocks in the vecinity of this particular massive protostar. The SiO emission outlines an elongated structure that is perpendicular to the major axis of the wind-driven shell of H$_2$O masers and its associated radio jet. We identify this structure as the toroidal structure that was previously theorized to explain the outflow’s evolution from an almost isotropic outflow to a collimated one.

- The observations provide a plausible scenario in which we are observing an SiO toroid and a wide-angle outflow surrounding VLA2. The wide-angle SiO outflow originates from the outer regions of the toroid, being incorporated into the large-scale bipolar molecular outflow. The gas located in the inner regions of the toroid might be rotating, although more precise observations are required to confirm this.

- The location of the obstacle that was previously predicted to stop the expansion of the wind-driven H$_2$O maser shell has been identified. It is situated between the outer parts of the SiO toroid and one of the main H$_2$CO clumps detected nearby, toward the northeast of VLA2. Additionally, this determination involves estimating the necessary gas density to impede the shell’s expansion toward the northeast.

## acknowledgments

This paper makes use of ALMA data ADS/JAO.ALMA#2019.1.00059.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The data processing for this paper has been carried out using the Spanish Prototype of an SRC (SPSRC) service and support, funded by the Spanish Ministry of Science, Innovation and Universities, by the Regional Government of Andalusia, by the European Regional Development Funds and by the European Union NextGenerationEU/PRTR. J.C. acknowledges the support of DGAPA/UNAM (Mexico) project IG100422. C.C.-G. acknowledges support from UNAM DGAPA-PAPIIT grant IG101321 and from CONACyT Ciencia de Frontera project ID 86372. G.A and J.F.G. acknowledge support from grants PID2020-114461GB-I00 and CEX2021-001131-S, funded by MCIN/AEI/10.13039/5011000110. J.M.G, A.S-M., and J.M.T. acknowledge partial support from the PID2020-117710GB-I00 grant funded by MCIN/AEI/10.13039/501100011033, and by the program Unidad de Excelencia Marı́a de Maeztu CEX2020-001058-M. A.S-M. also acknowledges support from the RyC2021-032892-I grant funded by MCIN/AEI/10.13039/501100011033 and by the European Union ‘Next GenerationEU’/PRTR. This work was partially supported by FAPESP (Fundação de Amparo á Pesquisa do Estado de São Paulo) under grant 2021/01183-8.

# Facilities

ALMA

# Software

CASA

natexlab

(ref: Anez20) Añez-López, N., Osorio, M., Busquet, G., et al. 2020, ApJ, 888, 41, doi: [`10.3847/1538-4357/ab5dbc`](http://doi.org/10.3847/1538-4357/ab5dbc)

(ref: Bartk20) Bartkiewicz, A., Sanna, A., Szymczak, M., et al. 2020, A&A, 637, A15, doi: [`10.1051/0004-6361/202037562`](http://doi.org/10.1051/0004-6361/202037562)

(ref: Busquet19) Busquet, G., Girart, J. M., Estalella, R., et al. 2019, A&A, 623, L8, doi: [`10.1051/0004-6361/201833687`](http://doi.org/10.1051/0004-6361/201833687)

(ref: Canto06) Cantó, J., Raga, A. C., & Adame, L. 2006, MNRAS, 369, 860, doi: [`10.1111/j.1365-2966.2006.10344.x`](http://doi.org/10.1111/j.1365-2966.2006.10344.x)

(ref: Carrasco10) Carrasco-González, C., Rodrı́guez, L. F., Torrelles, J. M., Anglada, G., & González-Martı́n, O. 2010, AJ, 139, 2433, doi: [`10.1088/0004-6256/139/6/2433`](http://doi.org/10.1088/0004-6256/139/6/2433)

(ref: Carrasco21) Carrasco-González, C., Sanna, A., Rodrı́guez-Kamenetzky, A., et al. 2021, ApJL, 914, L1, doi: [`10.3847/2041-8213/abf735`](http://doi.org/10.3847/2041-8213/abf735)

(ref: Carrasco15) Carrasco-González, C., Torrelles, J. M., Cantó, J., et al. 2015, Science, 348, 114, doi: [`10.1126/science.aaa7216`](http://doi.org/10.1126/science.aaa7216)

(ref: casa22) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Davis98a) Davis, C. J., Moriarty-Schieven, G., Eislöffel, J., Hoare, M. G., & Ray, T. P. 1998a, AJ, 115, 1118, doi: [`10.1086/300259`](http://doi.org/10.1086/300259)

(ref: Davis98b) Davis, C. J., Smith, M. D., & Moriarty-Schieven, G. H. 1998b, MNRAS, 299, 825, doi: [`10.1046/j.1365-8711.1998.01811.x`](http://doi.org/10.1046/j.1365-8711.1998.01811.x)

(ref: D-R22) Diaz-Rodriguez, A. K., Anglada, G., Blázquez-Calero, G., et al. 2022, ApJ, 930, 91, doi: [`10.3847/1538-4357/ac3b50`](http://doi.org/10.3847/1538-4357/ac3b50)

(ref: Girart18) Girart, J. M., Fernández-López, M., Li, Z. Y., et al. 2018, ApJL, 856, L27, doi: [`10.3847/2041-8213/aab76b`](http://doi.org/10.3847/2041-8213/aab76b)

(ref: Goddi20) Goddi, C., Ginsburg, A., Maud, L. T., Zhang, Q., & Zapata, L. A. 2020, ApJ, 905, 25, doi: [`10.3847/1538-4357/abc88e`](http://doi.org/10.3847/1538-4357/abc88e)

(ref: Gomez99) Gómez, J. F., Sargent, A. I., Torrelles, J. M., et al. 1999, ApJ, 514, 287, doi: [`10.1086/306916`](http://doi.org/10.1086/306916)

(ref: Huang22) Huang, K. Y., Viti, S., Holdship, J., et al. 2022, A&A, 666, A102, doi: [`10.1051/0004-6361/202142831`](http://doi.org/10.1051/0004-6361/202142831)

(ref: Hunter94) Hunter, T. R., Taylor, G. B., Felli, M., & Tofani, G. 1994, A&A, 284, 215

(ref: Jimenez07) Jiménez-Serra, I., Martı́n-Pintado, J., Rodrı́guez-Franco, A., et al. 2007, ApJL, 661, L187, doi: [`10.1086/519005`](http://doi.org/10.1086/519005)

(ref: Kim13) Kim, J.-S., Kim, S.-W., Kurayama, T., et al. 2013, ApJ, 767, 86, doi: [`10.1088/0004-637X/767/1/86`](http://doi.org/10.1088/0004-637X/767/1/86)

(ref: Mangum93) Mangum, J. G., & Wootten, A. 1993, ApJS, 89, 123, doi: [`10.1086/191841`](http://doi.org/10.1086/191841)

(ref: Matthews10) Matthews, L. D., Greenhill, L. J., Goddi, C., et al. 2010, ApJ, 708, 80, doi: [`10.1088/0004-637X/708/1/80`](http://doi.org/10.1088/0004-637X/708/1/80)

(ref: Maud18) Maud, L. T., Cesaroni, R., Kumar, M. S. N., et al. 2018, A&A, 620, A31, doi: [`10.1051/0004-6361/201833908`](http://doi.org/10.1051/0004-6361/201833908)

(ref: Minh10) Minh, Y. C., Su, Y. N., Chen, H. R., et al. 2010, ApJ, 723, 1231, doi: [`10.1088/0004-637X/723/2/1231`](http://doi.org/10.1088/0004-637X/723/2/1231)

(ref: Ossenkopf94) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: Patel05) Patel, N. A., Curiel, S., Sridharan, T. K., et al. 2005, Nature, 437, 109, doi: [`10.1038/nature04011`](http://doi.org/10.1038/nature04011)

(ref: R-K20) Rodrı́guez-Kamenetzky, A., Carrasco-González, C., Torrelles, J. M., et al. 2020, MNRAS, 496, 3128, doi: [`10.1093/mnras/staa1742`](http://doi.org/10.1093/mnras/staa1742)

(ref: Rygl12) Rygl, K. L. J., Brunthaler, A., Sanna, A., et al. 2012, A&A, 539, A79, doi: [`10.1051/0004-6361/201118211`](http://doi.org/10.1051/0004-6361/201118211)

(ref: Sanna17) Sanna, A., Moscadelli, L., Surcis, G., et al. 2017, A&A, 603, A94, doi: [`10.1051/0004-6361/201730773`](http://doi.org/10.1051/0004-6361/201730773)

(ref: Schilke97) Schilke, P., Walmsley, C. M., Pineau des Forets, G., & Flower, D. R. 1997, A&A, 321, 293

(ref: Shepherd01) Shepherd, D. S. 2001, ApJ, 546, 345, doi: [`10.1086/318252`](http://doi.org/10.1086/318252)

(ref: Shepherd03) Shepherd, D. S., Testi, L., & Stark, D. P. 2003, ApJ, 584, 882, doi: [`10.1086/345743`](http://doi.org/10.1086/345743)

(ref: Shirley15) Shirley, Y. L. 2015, PASP, 127, 299, doi: [`10.1086/680342`](http://doi.org/10.1086/680342)

(ref: Surcis14) Surcis, G., Vlemmings, W. H. T., van Langevelde, H. J., et al. 2014, A&A, 565, L8, doi: [`10.1051/0004-6361/201423877`](http://doi.org/10.1051/0004-6361/201423877)

(ref: Surcis23) Surcis, G., Vlemmings, W. H. T., Goddi, C., et al. 2023, A&A, 673, A10, doi: [`10.1051/0004-6361/202245734`](http://doi.org/10.1051/0004-6361/202245734)

(ref: Tobin20) Tobin, J. J., Sheehan, P. D., Megeath, S. T., et al. 2020, ApJ, 890, 130, doi: [`10.3847/1538-4357/ab6f64`](http://doi.org/10.3847/1538-4357/ab6f64)

(ref: Torrelles97) Torrelles, J. M., Gómez, J. F., Rodrı́guez, L. F., et al. 1997, ApJ, 489, 744, doi: [`10.1086/304824`](http://doi.org/10.1086/304824)

(ref: Torrelles01) Torrelles, J. M., Patel, N. A., Gómez, J. F., et al. 2001, Nature, 411, 277, doi: [`10.1038/35077020`](http://doi.org/10.1038/35077020)

(ref: Torrelles03) Torrelles, J. M., Patel, N. A., Anglada, G., et al. 2003, ApJL, 598, L115, doi: [`10.1086/380750`](http://doi.org/10.1086/380750)

(ref: vanderWalt21) van der Walt, S. J., Kristensen, L. E., Jørgensen, J. K., et al. 2021, A&A, 655, A86, doi: [`10.1051/0004-6361/202039950`](http://doi.org/10.1051/0004-6361/202039950)

(ref: Zeng23) Zeng, L., Zhang, Q., Alves, F. O., et al. 2023, ApJ, 954, 99, doi: [`10.3847/1538-4357/ace690`](http://doi.org/10.3847/1538-4357/ace690)

# 1.3 mm continuum sources

Table [2](#tab:possources) lists the position of all the 1.3 mm continuum compact sources detected with ALMA in a region of $\sim$30$''$ ($\sim$39,000 au) centered on the massive protostar W75N(B)-VLA2 (see §[3.1](#sec:dust)). Peak flux densities are primary beam corrected. Their association (if any) with sources detected at other wavelengths are indicated in the last column of Table [2](#tab:possources). Figure [5](#fig:sources) shows the distribution of these mm continuum sources (indicated by crosses) together with the positions of the cm continuum sources detected with the VLA (cite: R-K20). We are proposing, in particular, that one of these detected continuum sources (source ID 32 in Table [2](#tab:possources)) is the powering source of the highly collimated bipolar jet that we have detected $\sim$6$''$ ($\sim$7,800 au) northeast of VLA2 (see Appendix [8](#ap:siojet) and Fig. [7](#fig:siojet)).

Dust mass estimates in the detected sources can be obtained from the 1.3 mm continuum emission assuming that it is optically thin and that the dust is isothermal within the beam size, through the equation $$\begin{equation}
M_{\rm dust} = \frac{S_\nu D^2}{\kappa_\nu B_\nu(T_{\rm dust})},
 
\end{equation}$$ where $S_\nu$ is the observed flux density (Table [2](#tab:possources)), D the source distance (1.3 kpc), $\kappa_\nu$ the dust opacity, and $B_\nu(T_{\rm dust})$ the Planck function at the dust temperature $T_{\rm dust}$. Adopting a dust opacity $\kappa_\nu$(1.3 mm) = 0.899 cm$^2$ g$^{-1}$ (cite: Ossenkopf94; D-R22), we obtain

$$\begin{equation}
 \label{eq:massdust}
M_{\rm dust} \simeq  1.4\times 10^{-4} M_{\odot} \left[\frac{S_{1.3~mm}}{mJy}\right] \times  \left[\frac{T_{\rm dust}}{50~K}\right]^{-1}.
 
\end{equation}$$

These dust mass values should be taken with caution and as a first approximation, in particular because if the emission is not optically thin they represent lower limits. For sources with flux densities of $\sim$1 mJy (Table [2](#tab:possources)), and assuming a gas-to-dust ratio of 100, total masses (dust+gas) of $\sim$1.5$\times$10$^{-2}$ M$_{\odot}$ ($\sim$15 M$_J$) are estimated for $T_{\rm dust}$ = 50 K, similar to the values obtained for protostellar disks of low-mass YSOs in massive star-forming regions, e.g., GGD 27 (cite: Busquet19), or Orion molecular clouds A and B (cite: Tobin20). This suggests that, in the W75N(B) massive star-forming region, there may also exist a significant population of low-mass YSOs (coexisting with massive protostars as VLA1, VLA2, and VLA3, and other possible intermediate-mass YSOs), having protostellar disks of size $\lesssim$170 au. Complementary observations at submm wavelengths will indeed be important in properly characterizing and distinguishing the nature of these sources as potential protostars.

| source ID | R.A. (J2000) | Dec. (J2000) | S$_{\nu}$ (mJy beam$^{-1}$)$^{b}$ | $\Delta d$ (arcsec)$^{c}$ | M$_{\rm J}$$^{d}$ | Association$^{e}$ |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 1 | 20 38 35.375 | 42 37 13.75 | 21.36 | 23.75 | 313 | ... |
| 2 | 20 38 35.671 | 42 37 31.39 | 2.45 | 9.39 | 36 | ... |
| 3 | 20 38 35.769 | 42 37 50.41 | 3.76 | 18.14 | 55 | ... |
| 4 | 20 38 35.837 | 42 37 26.82 | 0.94 | 10.21 | 14 | ... |
| 5 | 20 38 35.947 | 42 37 31.86 | 3.39 | 6.35 | 50 | MM2 |
| 6 | 20 38 35.959 | 42 37 32.17 | 8.24 | 6.13 | 121 | MM2 |
| 7 | 20 38 35.974 | 42 37 32.35 | 3.87 | 5.91 | 57 | MM2 |
| 8 | 20 38 35.977 | 42 37 31.82 | 1.83 | 6.06 | 27 | MM2 |
| 9 | 20 38 35.991 | 42 37 31.39 | 12.68 | 6.09 | 186 | MM2, VLA\[SW\] |
| 10 | 20 38 36.004 | 42 37 31.57 | 6.66 | 5.89 | 98 | MM2 |
| 11 | 20 38 36.016 | 42 37 34.79 | 1.02 | 5.23 | 15 | ... |
| 12 | 20 38 36.025 | 42 37 27.29 | 0.75 | 8.49 | 11 | ... |
| 13 | 20 38 36.036 | 42 37 27.37 | 0.75 | 8.36 | 11 | ... |
| 14 | 20 38 36.070 | 42 37 31.35 | 0.75 | 5.35 | 11 | MM2 |
| 15 | 20 38 36.080 | 42 37 31.35 | 0.85 | 5.25 | 12 | MM2 |
| 16 | 20 38 36.194 | 42 37 31.47 | 1.88 | 4.15 | 28 | MM2 |
| 17 | 20 38 36.270 | 42 37 29.54 | 0.65 | 5.14 | 10 | ... |
| 18 | 20 38 36.279 | 42 37 29.60 | 0.78 | 5.04 | 11 | ... |
| 19 | 20 38 36.287 | 42 37 29.64 | 0.86 | 4.96 | 13 | ... |
| 20 | 20 38 36.298 | 42 37 29.70 | 1.05 | 4.86 | 15 | ... |
| 21 | 20 38 36.302 | 42 37 23.61 | 4.24 | 10.67 | 62 | ... |
| 22 | 20 38 36.401 | 42 37 34.79 | 2.16 | 1.17 | 32 | MM1 |
| 23 | 20 38 36.414 | 42 37 34.40 | 1.95 | 0.85 | 29 | MM1 |
| 24 | 20 38 36.418 | 42 37 34.63 | 1.60 | 0.92 | 23 | MM1 |
| 25 | 20 38 36.437 | 42 37 34.86 | 3.32 | 0.94 | 49 | MM1, VLA1 |
| 26 | 20 38 36.471 | 42 37 43.87 | 0.39 | 9.78 | 6 | MM\[N\] |
| 27 | 20 38 36.482 | 42 37 33.36 | 86.93 | 0.73 | 1275 | MM1, VLA3 |
| 28 | 20 38 36.484 | 42 37 34.04 | 20.75 | 0.05 | 51$^{d}$ | MM1, VLA2 |
| 29 | 20 38 36.641 | 42 37 25.93 | 0.99 | 8.34 | 15 | ... |
| 30 | 20 38 36.663 | 42 37 30.45 | 2.94 | 4.13 | 43 | ... |
| 31 | 20 38 36.912 | 42 37 37.03 | 0.55 | 5.55 | 8 | ... |
| 32 | 20 38 36.930 | 42 37 36.83 | 1.02 | 5.61 | 15 | f |
| 33 | 20 38 36.946 | 42 37 25.95 | 1.25 | 9.59 | 18 | ... |
| 34 | 20 38 37.083 | 42 37 37.13 | 1.87 | 7.26 | 27 | MM3 |
| 35 | 20 38 37.097 | 42 37 37.45 | 2.08 | 7.53 | 30 | MM3 |
| 36 | 20 38 37.114 | 42 37 36.79 | 1.26 | 7.44 | 18 | MM3 |
| 37 | 20 38 37.124 | 42 37 37.46 | 5.25 | 7.81 | 77 | MM3, VLA\[NE\] |
| 38 | 20 38 37.294 | 42 37 31.35 | 0.94 | 9.33 | 14 | ... |
| 39 | 20 38 37.752 | 42 37 35.60 | 12.46 | 14.05 | 183 | ... |
| 40 | 20 38 37.872 | 42 37 36.47 | 5.22 | 15.48 | 77 | ... |

: ALMA 1.3 mm continuum sources detected in the W75N(B) field$^{a}$

Table notes: $^{a}$ Positions and peak intensities of the ALMA 1.3 mm continuum sources determined from the images with a beam size of $0.13''\times0.06''$ (PA = $-2^{\circ}$) and rms $\simeq$ 0.06 mJy beam$^{-1}$ (see §3.1). The mm continuum sources are not resolved at FWHM, which implies physical sizes for the dust emission of $\lesssim$ 170 au. Positional uncertainties are $\sim$0.02$''$. Phase center is at $\alpha$(J2000) = 20$^h$38$^m$36.4860$^s$, $\delta$(J2000) = 42$^{\circ}$37$'$34.090$''$. $^{b}$ Peak intensities corrected by primary beam. $^{c}$ Distance from the source to the phase center of the observations. $^{d}$ Total mass (dust+gas) from Eq. [\[eq:massdust\]](#eq:massdust), assuming $T_{\rm dust}$ = 50 K (see §[6](#ap:sources)), excepting for source ID 28 (VLA2), where we assume $T_{\rm dust}$ = 300 K (see §[4.1](#sec:toroid)). $^{e}$ The association with the mm cores MM1, MM2, MM3, MM\[N\], and/or the VLA sources VLA\[SW\], VLA1, VLA2, VLA3, VLA\[NE\] (cite: R-K20) is indicated. $^{f}$ Source proposed to power the highly-collimated SiO bipolar outflow detected $\sim$6$''$ northeast of VLA2 (see §[8](#ap:siojet) and Fig. [7](#fig:siojet)).

![](Pos-mm-Sources.pdf)

# H$_2$CO and SiO absorption lines toward VLA3

H$_2$CO and SiO lines are seen in absorption against the continuum source VLA3. In Fig. [6](#fig:absorption) we present the spectra at the location of this source. Both show an absorption feature centered at $V_{\rm LSR}\simeq 6.4$ km s$^{-1}$.

![](Absorption2.pdf)

# Highly collimated bipolar SiO jet

We report here the detection of an extremely highly collimated bipolar SiO jet located $\sim$5$''$ ($\sim$6,500 au) northeast of the three massive protostars (Fig. [7](#fig:siojet)). This bipolar jet extends in the southeast-northwest direction, over an angular scale of $\sim 8''$ ($\sim 10,400$ au) and velocities in the range $V_{\rm LSR} \simeq -3$ to +43 km s$^{-1}$. From the detected compact mm continuum sources in the W75N(B) region (§[3.1](#sec:dust)), we identify one of them (source ID 32 in Table [2](#tab:possources)) that is well-centered between the two jet lobes (Fig. [7](#fig:siojet)), as the most probable powering source, most likely a low-mass protostar. Since it is located in a region outside the main focus of our observations on VLA2, we will present and discuss the main properties of this remarkable bipolar SiO jet in a forthcoming paper.

![](SiO-jet_v5.pdf)

</paper>

Write the methods card for this paper.