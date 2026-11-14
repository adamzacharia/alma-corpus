# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...908..250H\sonnetcc\reply.txt

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
 "bibcode": "2021ApJ...908..250H",
 "title": "ALMA Observations of the Inner Cavity in the Protoplanetary Disk around Sz 84",
 "year": 2021,
 "journal": "The Astrophysical Journal",
 "first_author": "Hashimoto, Jun",
 "n_authors": 8,
 "arxiv_id": "2009.09912",
 "doi": "10.3847/1538-4357/abba76",
 "alma_projects_linked_by_archive": [
  "2013.1.00220.S",
  "2015.1.01301.S",
  "2016.1.00571.S"
 ]
}
```

Paper text:
<paper>
# ALMA Observations of the Inner Cavity in the Protoplanetary Disk around Sz 84

## Abstract

We present Atacama Large Millimeter/submillimeter Array (ALMA) observations of a protoplanetary disk around the T Tauri star Sz 84 and analyses of the structures of the inner cavity in the central region of the dust disk. Sz 84’s spectral energy distribution (SED) has been known to exhibit negligible infrared excess at $\lambda \lesssim$10 $\mu$m due to the disk’s cavity structure. Analyses of the observed visibilities of dust continuum at 1.3 mm and the SED indicate that the size of the cavity in the disk of large (millimeter size) dust grains is 8 au in radius and that in the disk of small (sub-micron size) dust grains is 60 au in radius. Furthermore, from the SED analyses, we estimate that the upper limit mass of small dust grains at $r<$60 au is less than $\sim$10$^{-3}$ $M_{\ensuremath{\oplus}}$, which is $\lesssim$0.01 % of the total (small $+$ large) dust mass at $r<$60 au. These results suggest that large dust grains are dominant at $r<$60 au, implying that dust grains efficiently grow with less efficient fragmentation in this region, potentially due to weak turbulence and/or stickier dust grains. The balance of grain growth and dust fragmentation is an important factor for determining the size of large dust grains in protoplanetary disks, and thus Sz 84 could serve as a good testbed for investigations of grain growth in such disks.

# Introduction

Planet formation is believed to take place in protoplanetary disks. In its earliest stages, dust grains grow. For small (sub-micron size) dust grains, which are comparable to typical interstellar medium dust in size, van der Waals forces cause the dust grains, which exhibit Brownian motion, to stick when they collide. Beyond the millimeter size, dust grains can grow into planetesimals a kilometer (or larger) in size via either direct collisional aggregation of dust grains (cite: weid1993; kata2013a) or some instabilities such as streaming instabilities (cite: joha2014a). The accretion of such planetesimals eventually leads to the formation of planets.

Grain growth in protoplanetary disks has been extensively investigated (cite: test2014). Theoretically, grain growth is limited by two processes, namely radial drift and fragmentation. Radial drift occurs when dust grains become large enough to decouple from the disk gas and then experience a head wind (cite: weid77). Accordingly, dust size is limited when dust grains undergo radial drift. Fragmentation also limits grain growth. It occurs when the relative velocity of colliding dust grains becomes high enough to result in fragmentation rather than a merger.

Observational investigations of grain growth have been conducted at (sub-)millimeter wavelengths (cite: test2003; pere2012; test2014). Optical and infrared (IR) observations can trace the surface layer of the disk due to the layer’s large optical depth, whereas (sub-)millimeter observations probe thermal emissions from the disk midplane region, where grain growth is the most efficient. This region becomes optically thin (or thinner) at longer wavelengths. As dust grains grow, the dust opacity ($\kappa_{\lambda}$), which is approximated as $\kappa_{\lambda} \propto \lambda^{\beta}$, and its index ($\beta$) both decrease (cite: miya1993; drai2006). Based on the Rayleigh-Jeans limit and the optically thin assumption, the observed flux can be expressed as $F_{\lambda} \propto \lambda^{\beta+2}$, and thus multiple wavelength observations can be used to measure $\beta$ even if the absolute dust opacity is unknown.

In addition to determining $\beta$, comparisons of disk structures observed at near-infrared (NIR) and (sub-)millimeter wavelengths are useful for exploring grain growth. When a cavity structure in the central region of a disk (such disks are called transitional disks[^1]; e.g., (cite: espaillat+14)) is observed directly, it may have different sizes at different wavelengths (cite: dong12cavity; garu2013; vandermarel13; vill2019a). One explanation for the different cavity sizes at different wavelengths is the trapping of large (millimeter size) dust grains (cite: rice06) by planet–disk interactions (cite: zhu12). A planet embedded in a disk reduces the surface density of the gas and creates a gas gap at the planetary orbital radius. The gap thereby produces a gas pressure bump at its outer edge where large dust grains are trapped. Because the small dust grains coupled to the gas can flow inside the gas pressure bump, their cavity sizes are smaller. This spatial segregation can be used as a proxy of grain growth in the disk.

Dust growth itself can also spatially segregate cavities without dust trapping. The trend of such segregation is opposite to that mentioned above. Numerical simulations of grain growth (cite: dull2005a; birn2012a) show that small dust grains, which are the main components of NIR excesses in the spectral energy distribution (SED), grow into large (millimeter size) dust grains within a time scale of $\lesssim$0.1 Myr at $r=$1 au if dust fragmentation is negligible. When small dust grains in the central region of a protoplanetary disk are removed, the corresponding SED shows a deficit of flux at NIR wavelengths. Because grain growth proceeds in an inside-out manner, which is due to higher gas density and a faster dynamical time scale in the inner disk (cite: dull2005a; brauer+2008), the small and large dust grains are predicted to be preferentially distributed in the outer and inner regions of the disk, respectively. Such opposite distributions of small and large dust grains were reported for the transitional disk around DM Tau ((cite: kudo2018); Hashimoto et al. submitted), in which the cavity in the disk of small dust grains is inferred to be located at $r=$3 au. Large dust grains are present even within this cavity. These results suggest that small dust grains at a few au around DM Tau efficiently grow into large dust grains with less efficient fragmentation, possibly due to weak turbulence and/or stickier dust grains (cite: stei2019).

In this paper, we report another example of an opposite spatial segregation for a cavity in the disk around the T Tauri star Sz 84 (spectral type: M5, (cite: alca2014); $T_{\rm eff}$: 3162 K, (cite: hend2020a); $M_{\rm *}$: 0.2 $M_{\odot}$, (cite: alca2014); age: 1 Myr, (cite: alca2014); distance: 152.6 pc, (cite: gaia18); disk inclination: 75$^\circ$, (cite: ansd2016a)). The SED of Sz 84 shows no or very weak IR excesses at $\lambda \lesssim$10 $\mu$m, which has been interpreted as indicating the presence of an almost clean cavity in the disk of small dust grains at $r\sim$55 au (i.e., negligible small dust grains inside the cavity; e.g., (cite: meri2010a)). Subsequent Atacama Large Millimeter/submillimeter Array (ALMA) observations of Sz 84 with a beam size of 0.3$''$ (46 au) showed no cavity structures in the dust continuum image (cite: ansd2016a), even though visibility analyses suggested a cavity structure at $r=$20–41 au (cite: tazz2017a; vandermarel18a). These results suggest that the size of the cavity in the disk of small dust grains ($r\sim$55 au) could be larger than that in the disk of large dust grains ($r=$20–41 au). The $^{13}$CO $J=3\rightarrow2$ gas disk around Sz 84 reveals no cavity structure in integrated CO visibilities (cite: vandermarel18a). However, gas cavities tend to be 1.5–3 times smaller than dust cavities (cite: vandermarel+16; vandermarel18a), and thus the available data may simply not resolve a gas cavity. Furthermore, it is reasonable to assume that the mass accretion rate of Sz 84, $\dot{M}$ $\sim$ 1 $\times$ 10$^{-9}$ $M_{\odot}$/yr (cite: mana14), is comparable to that of typical T Tauri stars (cite: naji15). These two observational results predict that small dust grains well coupled to the gas exist in the vicinity of the central star (they arrive there by flowing inside the cavity), possibly explaining the smaller size of the cavity in the disk of small dust grains. However, as mentioned above, analyses of the visibilities of the dust continuum and the SED in the literature show the opposite observational results. The origin of Sz 84’s cavity in the disk of small dust grains with a moderate mass accretion rate is still unclear (cite: mana14).

# Observations

ALMA observations of Sz 84 were carried out with band 6 in cycle 3 (ID: 2015.1.01301.S; PI: J. Hashimoto); they are summarized in Table [1](#tab:table1). The data were calibrated using the Common Astronomy Software Applications (CASA) package (cite: mcmu07) with the calibration scripts provided by ALMA. We conducted a self-calibration of the visibilities. The phases were self-calibrated once with fairly long solution intervals (solint=‘inf’) that combined all spectral windows. The proper motions of Sz 84 were calculated with the function `EPOCH_PROP` in GAIA ADQL (Astronomical Data Query Language[^2]). The phase centers were corrected using `fixvis` in the CASA tools. The dust continuum image at band 6 was synthesized by CASA with the `CLEAN` task using a multi-frequency deconvolution algorithm (cite: rau11). In the `CLEAN` task, we set the $uv$-taper to obtain a nearly circular beam pattern (Table [1](#tab:table1)). The synthesized dust continuum image is shown in Figure [1](#fig1). The root-mean-square (r.m.s.) noise in the region far from the object is 61.3 $\mu$Jy/beam with a beam size of 198 $\times$ 195 mas at a position angle (PA) of $-$88.5$\ensuremath{^\circ}$.

In addition to our own data, two archival dust continuum datasets were used for our visibility analysis in § [4.1](#subsec:mcmc). They were taken with band 3 in cycle 4 (ID: 2016.1.00571.S; PI: M. Tazzari) and band 7 in cycle 2 (ID: 2013.1.00220.S; PI: J. Williams). The calibration procedures described above were applied to these data. These additional observations are summarized in Table [4](#tab:band3-7) in the Appendix. Because the data quality (spatial resolution and sensitivity) of our band 6 data is better than that of the archival data, whose spatial resolution is $\sim$0.3$''$, we only show the band 6 image in Figure [1](#fig1).

The $^{12}$CO $J=2\rightarrow1$ line data (Table [1](#tab:table1)) were extracted by subtracting the continuum in the $uv$ plane using the `uvcontsub` task in the CASA tools. A line image cube with channel widths of 1.0 km/s was produced by the `CLEAN` task. The integrated line flux map (moment 0) and the intensity-weighted velocity map (moment 1) are shown in Figures [1](#fig1) and [2](#fig4), respectively. The channel maps at $-$1.0 to $+$11.0 km/s are shown in Figure [6](#figA1) in the Appendix. The r.m.s. noise in the moment 0 map is 8.7 mJy/beam$\cdot$km/s with a beam size of 235 $\times$ 161 mas at a PA of $-$2.0$\ensuremath{^\circ}$ and that in the moment 1 map at the 1.0 km/s bin is 2.37 mJy/beam. The peak signal-to-noise ratio (SNR) is 17.9 in the channel map of $+$7.0 km/s. $^{13}$CO $J=2\rightarrow1$ line emissions were detected with a peak SNR of less than 5, and thus the images are not shown. We did not detect C$^{18}$O $J=2\rightarrow1$ line emissions.

+-----------------------------+--------------------------------------------------------------+-----------------------------------------------------------+
| Observations                |                                                              |                                                           |
+:============================+:============================================================:+:=========================================================:+
| Observing date (UT)         | 2016.Sep.17                                                                                                              |
+-----------------------------+--------------------------------------------------------------------------------------------------------------------------+
| Project code                | 2015.1.01301.S                                                                                                           |
+-----------------------------+--------------------------------------------------------------------------------------------------------------------------+
| Time on source (min)        | 29.7                                                                                                                     |
+-----------------------------+--------------------------------------------------------------------------------------------------------------------------+
| Number of antennas          | 38                                                                                                                       |
+-----------------------------+--------------------------------------------------------------------------------------------------------------------------+
| Baseline lengths            | 15.1 m to 2.5 km                                                                                                         |
+-----------------------------+--------------------------------------------------------------------------------------------------------------------------+
| Baseband Freqs. (GHz)       | 219.5, 220.4, 230.5, 232.5                                                                                               |
+-----------------------------+--------------------------------------------------------------------------------------------------------------------------+
| Channel width (MHz)         | 0.122, 0.122, 0.122, 15.6                                                                                                |
+-----------------------------+--------------------------------------------------------------------------------------------------------------------------+
| Continuum band width (GHz)  | 2.3                                                                                                                      |
+-----------------------------+--------------------------------------------------------------------------------------------------------------------------+
| Bandpass calibrator         | J1517$-$2422                                                                                                             |
+-----------------------------+--------------------------------------------------------------------------------------------------------------------------+
| Flux calibrator             | J1427$-$4206                                                                                                             |
+-----------------------------+--------------------------------------------------------------------------------------------------------------------------+
| Phase calibrator            | J1610$-$3958                                                                                                             |
+-----------------------------+--------------------------------------------------------------------------------------------------------------------------+
| New phase center with GAIA  | 15h58m2.50261s, -37d36m3.1145s                                                                                           |
+-----------------------------+--------------------------------------------------------------+-----------------------------------------------------------+
| Imaging                     | Dust continuum                                               | $^{12}$CO $J=2\rightarrow1$                               |
+-----------------------------+--------------------------------------------------------------+-----------------------------------------------------------+
| Bobust clean parameter      | $-2.0$                                                       | 2.0                                                       |
+-----------------------------+--------------------------------------------------------------+-----------------------------------------------------------+
| Outer $uv$-taper parameter  | 50.0 $\times$ 0.6 M$\lambda$ with 183.0$\ensuremath{^\circ}$ | ...                                                       |
+-----------------------------+--------------------------------------------------------------+-----------------------------------------------------------+
| Beam shape                  | 198 $\times$ 195 mas at PA of $-$88.5$\ensuremath{^\circ}$   | 235 $\times$ 161 mas at PA of $-$2.0$\ensuremath{^\circ}$ |
+-----------------------------+--------------------------------------------------------------+-----------------------------------------------------------+
| r.m.s. noise ($\mu$Jy/beam) | 61.3                                                         | 2.37 $\times$ 10$^{3}$ at 1.0 km/s bin                    |
+-----------------------------+--------------------------------------------------------------+-----------------------------------------------------------+

: ALMA observations and imaging parameters

# Results

Figures [1](#fig1)(a) and (b) show the dust continuum image at band 6 and the $^{12}$CO moment 0 map, respectively. Our observations clearly detect the spatially resolved disk in both images. However, no cavity structure appears in the central region of the disk in either image. The total flux density of the dust continuum derived from the visibility fitting in § [4.1](#subsec:mcmc) is 13.43 $\pm$ 0.13 mJy, which is consistent with previous ALMA band 6 observations (12.63 $\pm$ 0.21; (cite: ansd2018a)) assuming a 10 % uncertainty in absolute flux calibration. The $^{12}$CO integrated flux density at more than 3 $\sigma$ is 1.89 $\pm$ 0.05 Jy/beam$\cdot$km/s.

We derived the spectral index $\alpha$ based on band 3, 6, and 7 data. The total flux densities at bands 3 and 6 taken from our visibility fitting in § [4.1](#subsec:mcmc) are 1.70 $\pm$ 0.06 and 13.43 $\pm$ 0.13 mJy, respectively, and that at band 7 taken from (cite: vandermarel18a) is 33 $\pm$ 0.4 mJy. Note that because our visibility fitting for band 7 data shows large uncertainty (Figure [10](#figA6)), we used the flux density reported in the literature. The value of $\alpha$ was then calculated as 2.42 $\pm$ 0.04, which is lower than the value of $\alpha \sim$2.7 found in other transitional disk systems (cite: pini2014a). This indicates that larger dust grains are present in the disk or that the disk tends to be partially optically thick at (sub-)millimeter wavelengths.

Figure [1](#fig1)(c) shows radial cuts of the dust continuum (Figure [1](#fig1)a) and the $^{12}$CO moment 0 map (Figure [1](#fig1)b) at a PA of 165.71$\ensuremath{^\circ}$ taken from our modeling results in § [4.1](#subsec:mcmc). Their brightness profiles are similar at $r\lesssim$50 au with a nearly flat slope at $r\lesssim$20 au. In contrast, the two brightness profiles (Figure [1](#fig1)c) at $r \gtrsim$50 au deviate, possibly due to the larger size of the CO disk (cite: trap2020a) or the presence of small dust grains, which is discussed in § [4.2](#subsec:mcrt).

Figure [2](#fig4) shows the $^{12}$CO moment 1 map and its position–velocity (PV) diagram at a PA of 165.71$\ensuremath{^\circ}$ and a disk inclination of 75.13$\ensuremath{^\circ}$ taken from § [4.1](#subsec:mcmc). The center of the CO gas motion in the moment 1 map nearly coincides with the center of the dust continuum emission (Figure [2](#fig4)a). We plotted the loci of the peak emission of a Keplerian disk around the central star by changing its mass from 0.2 to 0.6 $M_{\odot}$ in the PV diagram and found that the dynamical mass of Sz 84 is $\sim$0.4–0.6 $M_{\ensuremath{\odot}}$. This value is consistent with the dynamical mass estimated from the $^{13}$CO $J=3\rightarrow2$ line reported in the literature (0.4 $\pm$ 0.1 $M_{\ensuremath{\odot}}$; (cite: yen2018a)). Note that these estimates are roughly 2–3 times larger than the spectroscopically determined mass (0.16–0.18 $M_{\ensuremath{\odot}}$; (cite: alca2017)). This discrepancy may result from the high disk inclination of 75$^\circ$. $^{12}$CO is generally optically thick and traces the surface layer of the disk, and thus the velocity structure could be largely affected by the high inclination. The disk vertical structure must be taken into account to derive a dynamical mass in the inclined disk system.

![](fig1v4.eps)

![](fig4v3.eps)

# Modeling

In this section, we determine the radial structure of the dust disk around Sz 84 by conducting both visibility and SED fitting. Because the high disk inclination of 75$^\circ$ (cite: ansd2016a) makes characterizing a cavity with a radius of a few tens of au in an image challenging, modeling is necessary. As mentioned in the introduction (§ [1](#sec:intro)), (sub-)millimeter and near- to mid-IR observations are generally sensitive to large and small dust grains, respectively, and hence two models, one each for visibility and the SED, were used to determine the radial distributions of large and small dust grains, respectively. Note that (cite: vandermarel18a) derived these models using ALMA cycle 2 band 7 data for Sz 84. Modeling with our new dataset, which has better sensitivity and a better spatial resolution, could better constrain the structures of the dust disk.

## Visibility fitting

The visibilities of Sz 84 show a null point at $\sim$450 k$\lambda$ (Figure [3](#fig2)b), which suggests cavity (or gap) structures in the protoplanetary disk (cite: zhan16). To confirm the cavity structures, we performed visibility fitting, in which observed visibilities are reproduced with a parametric model of the disk by utilizing all the spatial frequency information.[^3]

We describe the surface brightness distributions of the disk in our model with a simple power-law radial profile:

$$\begin{eqnarray}
I(r) \propto C_{1} \cdot (r/r_{0})^{-C_{2}}, 
\end{eqnarray}$$ where $C_{1}$, $C_{2}$, and $r_{0}$ are a scaling factor, the exponent of the power law, and the normalization factor at $r_{\rm cav2}$, respectively. As shown below, this simple profile is sufficient for reproducing the observations. In the radial direction, we adopt the following scaling factors and exponents:

$$\begin{eqnarray*}
C_{1} &=& \left \{
\begin{array}{llllllll}
0       &{\rm for}&              & & r  &<& r_{\rm cav1}\\
\delta  &{\rm for}& r_{\rm cav1} &<& r  &<& r_{\rm cav2}\\
1       &{\rm for}& r_{\rm cav2} &<& r  &<& 300\ {\rm au},
\end{array}
\right. \\
\end{eqnarray*}$$

$$\begin{eqnarray*}
C_{2} &=& \left \{
\begin{array}{llllllll}
{\rm NA}    &{\rm for}&              & & r  &<& r_{\rm cav1}\\
\gamma_{1}  &{\rm for}& r_{\rm cav1} &<& r  &<& r_{\rm cav2}\\
\gamma_{2}  &{\rm for}& r_{\rm cav2} &<& r  &<& 300\ {\rm au}.
\end{array}
\right. \\
\end{eqnarray*}$$

The best-fit surface brightness profile[^4] with explanations is shown in Figure [3](#fig2)(a). Because the SED of Sz 84 shows negligible NIR excess, we set no emissions at $r < r_{\rm cav1}$; that is, $C_1=0$. The total flux density ($F_{\rm total}$) was set as a free parameter. The disk inclination ($i$) and PA were also set as free parameters. The phase center was fixed. In total, there are 8 free parameters in our model ($F_{\rm total}$, $r_{\rm cav}$, $r_{\rm gap}$, $\delta$, $\gamma_{1}$, $\gamma_{2}$, $i$, PA)[^5].

The modeled disk image was converted into complex visibilities with the public Python code `vis_sample` (cite: loomis+17), in which modeled visibilities are sampled with the same ($u$, $v$) grid points as those in our observations. The modeled visibilities were deprojected[^6] with the system PA and $i$ as free parameters, and were calculated as azimuthal mean values ($V_{\rm mean}$) and standard deviations ($\sigma$) within 20 k$\lambda$ bins in the real part. The fitting was performed with the Markov chain Monte Carlo (MCMC) method in the `emcee` package (cite: foreman-mackey+2013). The log-likelihood function ln$L$ in the MCMC fitting was ${\rm ln}L = -0.5 \Sigma \{({\rm Re}V_{{\rm mean},j}^{\rm obs} - {\rm Re}V_{{\rm mean},j}^{\rm model})^{2}/\sigma_{j}^{2}\}$, where ${\rm Re}V_{{\rm mean},j}^{\rm obs}$, ${\rm Re}V_{{\rm mean},j}^{\rm model}$, and $\sigma_{j}$ are the observed and modeled visibilities and standard deviations in the real part, respectively. The subscript $j$ represents the $j$-th bin. Our calculations used flat priors with the parameter ranges summarized in Table [1](#tab:table1). The burn-in phase (from initial conditions to reasonable sampling) employed 2000 steps, and we ran another 2000 steps for convergence, for a total of 4000 steps with 200 walkers. These fitting procedures were also applied to the band 3 and 7 data with the same parameter ranges except for that of the total flux density. However, we found multiple peaks and a nearly flat posterior probability distribution, especially for the disk inclination and flux density in band 3 and 7 data, respectively, possibly due to shorter baseline lengths and lower sensitivities (Table [5](#tab:table4) and Figures [9](#figA5) and [10](#figA6) in the Appendix). Therefore, we decided to use only the flux density from band 3 data (i.e., band 7 data were not used).

The fitting results with errors computed from the 16th and 84th percentiles are shown in Table [2](#tab:table2), the radial profile of best-fit surface brightness is shown in Figure [3](#fig2)(a), the best-fit visibilities with a reduced-$\chi^{2}$ of 1.24 are shown in Figure [3](#fig2)(b), the best-fit modeled image is shown in Figure [7](#figA3), and the probability distributions for the MCMC posteriors are shown in Figure [8](#figA2). We found that the cavity at $r=$26 au (i.e., $r_{\rm cav2}$) is shallow with $\delta \gtrsim$0.2 (Figure [8](#figA2)). We also found that it is difficult to determine the size of the empty cavity (i.e., $r_{\rm cav1}$) due to insufficient baselines in our observations, which have an upper limit of $r_{\rm cav1}\sim$10 au (Figure [8](#figA2)). A better constraint on this size can be obtained by the SED fitting (see § [4.2](#subsec:mcrt)). The flux inside the 26 au cavity was measured at 4.4 mJy in the best-fit model disk, which is 33 % of the total flux at band 6. We subtracted the modeled visibilities from the observed ones, and made a CLEANed image (Figure [1](#fig1)c).

In § [3](#sec:result), we mentioned the similarity of the radial profiles at $r\lesssim$50 au in the dust continuum and $^{12}$CO moment 0 images. As shown here, the dust continuum emission decreases at $r<$26 au. Hence, the brightness of $^{12}$CO might decrease in the central region of the disk as well. Note that we assumed that the flux attenuation in the central region of the CO gas disk caused by the foreground cloud absorption is negligible due to the high inclination of Sz 84 (75.1$\ensuremath{^\circ}$).

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Flux | $r_{\rm cav1}$ | $r_{\rm cav2}$ | $\gamma_{1}$ | $\gamma_{2}$ | $\delta$ | $i$ | P.A. | Reduced $\chi^{2}$ |
| (mJy) | (au) | (au) |  |  |  | ($\ensuremath{^\circ}$) | ($\ensuremath{^\circ}$) |  |
| 13.43$^{+0.13}_{-0.13}$ | 6.45$^{+4.12}_{-4.29}$ | 25.90$^{+2.01}_{-1.85}$ | $-0.43^{+0.85}_{-0.46}$ | 4.07$^{+0.16}_{-0.13}$ | 0.59$^{+0.26}_{-0.25}$ | 75.13$^{+1.74}_{-0.46}$ | 165.71$^{+3.22}_{-2.58}$ | 1.24 |
| {10.0-20.0} | {0.0 .. 21.4} | {15.3 .. 45.8} | {0.0 .. 10} | {-10 .. 10} | {0.0 .. 1.0} | {50 .. 80} | {150 .. 180} |  |

: Results of MCMC fitting for band 6 data and corresponding parameter ranges

Table notes: Values in parentheses are parameter ranges in our MCMC calculations.

![](fig2v2.eps)

## SED fitting

In the previous section, our model showed that the innermost cavity ($r_{\rm cav1}$) is located at $r\lesssim$10 au. Because Sz 84’s SED has negligible IR excess at $\lambda \lesssim$10 $\mu$m (Figure [4](#fig3)e), we need to confirm that our model does not produce significant IR excess. Furthermore, we found a shallow cavity at $r=$26 au in the disk of large dust grains in the previous section. This size is roughly consistent with the $r=20$ au estimated by (cite: vandermarel18a), who suggested that the 20 au cavity can reproduce the SED of Sz 84. However, this size is smaller than the cavity size derived from the SED analysis by (cite: meri2010a), namely 55 au in radius. Therefore, we revisited the SED analyses to constrain the radial distributions of both large and small dust grains by running radiative transfer modeling using a Monte Carlo radiative transfer (MCRT) code (`HOCHUNK3D`; (cite: whit2013)).

The MCRT code follows a two-layer disk model with small (up to micron size) dust grains in the upper disk atmosphere and large (up to millimeter size) dust grains in the disk midplane (cite: dale2006). The modeled disk structure and dust properties in the MCRT code are described in our previous studies (cite: hashimoto+15). Briefly, small dust grains are from the standard interstellar-medium dust model (a composite of silicates and graphites with a size distribution of $n(s) \propto s^{-3.5}$ from $s_{\rm min} = 0.0025$ $\mu$m to $s_{\rm max} = 0.2$ $\mu$m) in (cite: kim1994) and large dust grains (a composite of carbons and silicates with a size distribution of $n(s) \propto s^{-3.5}$ from $s_{\rm min} = 0.01$ $\mu$m to $s_{\rm max} = 1000$ $\mu$m) are from Model 2 in (cite: wood2002). The radial surface density was assumed to have a simple power-law radial profile similar to the equation in § [4.1](#subsec:mcmc):

$$\begin{eqnarray*}
\Sigma(r) &=& C_{3} \cdot \Sigma_{0} (r/r_{0})^{-C_{4}}, \\
C_{3} &=& \left \{
\begin{array}{llllllll}
0       &{\rm for}&              & & r  &<& r_{\rm cav1}\\
\delta  &{\rm for}& r_{\rm cav1} &<& r  &<& r_{\rm cav2}\\
1       &{\rm for}& r_{\rm cav2} &<& r  &<& 300\ {\rm au}
\end{array}
\right. 
\end{eqnarray*}$$

$$\begin{eqnarray*}
C_{4} &=& \left \{
\begin{array}{llllllll}
{\rm NA}    &{\rm for}&              & & r  &<& r_{\rm cav1}\\
q_{1}  &{\rm for}& r_{\rm cav1} &<& r  &<& r_{\rm cav2}\\
q_{2}  &{\rm for}& r_{\rm cav2} &<& r  &<& 300\ {\rm au}.
\end{array}
\right. \\
\end{eqnarray*}$$ where $r_{0}$ is the normalization factor at $r_{\rm cav2}$, $\Sigma_{0}$ is the normalized surface density determined from the total (gas $+$ dust) disk mass ($M_{\rm disk}$) assuming a gas-to-dust mass ratio of 100, $C_{3}$ is the scaling factor for the surface density (which is set to the same value as $C_{1}$ in § [4.1](#subsec:mcmc) for large dust grains), and $C_{4}$ is the radial gradient parameter. The scaling factor for small dust grains ($\delta^{\rm small}$) was assumed to be zero at $r<r^{\rm small}_{\rm rcav2}$. The radial gradient parameters $q_{1}$ and $q_{2}$ (which are the same for disks of large and small dust grains) were fixed to reproduce the surface brightness derived in § [4.1](#subsec:mcmc), as explained below. The value of $r^{\rm large}_{\rm rcav2} =$26 au was taken from the result in § [4.1](#subsec:mcmc). $r^{\rm large}_{\rm rcav1}$ and $r^{\rm small}_{\rm rcav2}$ were free parameters. We set $M_{\rm disk}$ to reproduce a flux of 13.43 mJy at 1.3 mm. The scale heights ($h$) of large and small grains were assumed to vary as $h \propto r^{p}$. For simplicity, we assumed $p=$ 1.25 with a typical midplane temperature profile of $T \propto r^{-0.5}$. We fixed the scale heights of 1 au at $r=$ 100 au for the disk of large dust grains ($h^{\rm large}_{r=100{\rm au}}$). Those of small dust grains ($h^{\rm small}_{r=100{\rm au}}$) were varied to reproduce the flux at $\lambda \sim$60–70 $\mu$m. The mass fraction ($f$) of large dust grains in the total dust mass was set to 0.9. The disk inclination was set to 75$\ensuremath{^\circ}$, as derived in our visibility analyses (§ [4.1](#subsec:mcmc)). The `HOCHUNK3D` code calculates the accretion luminosity from the star based on the mass accretion rate. Half of the flux was emitted as X-rays (which heat the disk) and half as stellar flux at a higher temperature. We set a mass accretion rate of $\dot{M} =$ 1.3 $\times$10$^{-9}$ $M_{\odot}$/yr (cite: mana14). In the code, we varied four parameters, namely $r^{\rm large}_{\rm rcav1}$, $r^{\rm small}_{\rm rcav2}$, $h^{\rm small}_{r=100{\rm au}}$, and $M_{\rm disk}$, as shown in Table [3](#tab:table3), along with the $\chi^{2}$ calculated at $\lambda=$1–100 $\mu$m.

Figure [4](#fig3) shows the surface densities and the SEDs for each model. Photometry and spectroscopy data used here are summarized in Table [6](#tab:phot). Our fitting procedure included the following four steps.

1.  We first tentatively set $r^{\rm large}_{\rm rcav1} =$10 au, $q_{1}=-$0.5, $q_{2}=$4.0 (which are derived in § [4.1](#subsec:mcmc)) and $r^{\rm small}_{\rm rcav2} =$55 au (which is taken from (cite: meri2010a)) with varying values of $h^{\rm small}_{r=100{\rm au}}$ and $M_{\rm disk}$, and found that the values of $h^{\rm small}_{r=100{\rm au}}=$5.0 au and $M_{\rm disk}=$2.5 $M_{\rm Jup}$ well reproduce far-IR flux at $\lambda \sim$60–70 $\mu$m and millimeter flux at 1.3 mm in the SED (Figure [4](#fig3)e to g).

2.  We iteratively varied the radial gradient parameters $q_{1}$ and $q_{2}$ to reproduce the radial surface brightness of the dust continuum at band 6 derived in § [4.1](#subsec:mcmc), and found that the values of $q_{1}=-$1.0 and $q_{2}=$4.5 (fiducial model) well reproduce the surface brightness, as shown in Figures [11](#figA4)(a) and (b). The bumps at $r\sim$10 and $\sim$60 au in the surface brightness of the MCRT modeling are attributed to those of the midplane temperature in Figure [11](#figA4)(c) due to irradiated cavity walls. We fixed these two values in the following procedures.

3.  To constrain the cavity size of small dust grains, $r^{\rm small}_{\rm rcav2}$ was set to 40 (model A), 50 (model B), 60 (fiducial model), 70 (model C), and 80 au (model D), as shown in upper panels in Figure [4](#fig3), with iterative adjustment of $h^{\rm small}_{r=100{\rm au}}$. The SED can be well reproduced by a cavity in the small dust with a size of $60\pm10$ au.

4.  Finally, we set $r^{\rm large}_{\rm rcav1}$ at 1 (model E), 8 (fiducial model), and 26 au (model F), as shown in lower panels in Figure [4](#fig3), to constrain the size of the inner cavity in the disk of large dust grains. The 8 au cavity, which is consistent with the results of MCMC modeling in § [4.1](#subsec:mcmc) (i.e., $r^{\rm large}_{\rm rcav1} \lesssim$10 au), is suitable for the fiducial model.

In summary, our modeling suggests that the small dust grains are located at $r\gtrsim$60 au and the large dust grains are distributed at 10 au $\lesssim r \lesssim$ 60 au. There is a dust-free region at $r\lesssim$10 au.

Because we used two independent disk models in the visibility fitting (§ [4.1](#subsec:mcmc)) and the SED fitting (§ [4.2](#subsec:mcrt)), we compare the surface brightness of the two models at band 6 in Figure [11](#figA4) to check their consistency. The maximum residual between the two surface brightness profiles convolved with the ALMA observation beam of 0.2$''$ (30 au) in Figure [11](#figA4)(b) is $\sim$119 $\mu$Jy/beam (1.9 $\sigma$). This residual is insignificant and thus the two models are mutually consistent.

Our picture of the disk with small dust grains residing only at large radii is supported by gas observations. As shown in § [3](#sec:result), the radial profile of the CO moment 0 deviates from that of dust at $r\gtrsim 50$ au. Small dust grains are the main source of heating as they are present in the upper layer of the disk and are thus directly irradiated by the stellar light and effectively absorb it. Therefore, the outer disk is heated more effectively than the inner disk, which contains only a small amount of small dust grains. Because small dust grains do not emit effectively at (sub-)millimeter wavelengths and the amount of large dust grains rapidly decreases at outer radii ($\propto r^{-4.5}$), these two facts do not greatly affect dust continuum emission. However, the $^{12}$CO gas emission mainly traces the temperature of the disk and therefore its moment 0 emission profile should be affected by the presence of small dust grains.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Model | $r_{\rm cav1}^{\rm large}$ | $r_{\rm cav1}^{\rm small}$ | $r_{\rm cav2}^{\rm large}$ | $r_{\rm cav2}^{\rm small}$ | $\delta^{\rm large}$ | $\delta^{\rm small}$ | $p$ | $q_{1}$ | $q_{2}$ | $h^{\rm large}_{r=100au}$ | $h^{\rm small}_{r=100au}$ | $M_{\rm disk}$ | $\dot{M}$ | $i$ | $\chi^{2}$ |
|  | (au) | (au) | (au) | (au) |  |  |  |  |  | (au) | (au) | ($M_{\rm Jup}$) | ($M_{\ensuremath{\odot}}$ yr$^{-1}$) | ($^\circ$) | ($^\circ$) |
| fiducial | 8.0 | — | 26.0 | 60.0 | 0.59 | 0 | 1.25 | $-$1.0 | 4.5 | 1.0 | 5.0 | 2.5 | 1.3 $\times$ 10$^{-9}$ | 75 | 151.0 |
| A | 8.0 | — | 26.0 | 40.0 | 0.59 | 0 | 1.25 | $-$1.0 | 4.5 | 1.0 | 5.8 | 2.5 | 1.3 $\times$ 10$^{-9}$ | 75 | 662.4 |
| B | 8.0 | — | 26.0 | 50.0 | 0.59 | 0 | 1.25 | $-$1.0 | 4.5 | 1.0 | 5.2 | 2.5 | 1.3 $\times$ 10$^{-9}$ | 75 | 200.0 |
| C | 8.0 | — | 26.0 | 70.0 | 0.59 | 0 | 1.25 | $-$1.0 | 4.5 | 1.0 | 4.8 | 2.5 | 1.3 $\times$ 10$^{-9}$ | 75 | 180.7 |
| D | 8.0 | — | 26.0 | 80.0 | 0.59 | 0 | 1.25 | $-$1.0 | 4.5 | 1.0 | 4.5 | 2.5 | 1.3 $\times$ 10$^{-9}$ | 75 | 299.6 |
| E | 1.0 | — | 26.0 | 60.0 | 0.59 | 0 | 1.25 | $-$1.0 | 4.5 | 1.0 | 5.5 | 2.5 | 1.3 $\times$ 10$^{-9}$ | 75 | 312.4 |
| F | 26.0 | — | 26.0 | 60.0 | 0.59 | 0 | 1.25 | $-$1.0 | 4.5 | 1.0 | 5.0 | 2.5 | 1.3 $\times$ 10$^{-9}$ | 75 | 478.2 |

: Parameters in our MCRT modeling

![](fig3v3.eps)

## Upper limit on amount of small grains inside cavity

Following (cite: beichman05), we converted the upper limit on the measured IR ($\lambda\lesssim$10 $\mu$m) flux at a certain wavelength $\lambda$ into an upper limit on the amount of small dust grains inside the 60 au cavity, $M_{\rm cav}^{\rm small}$. At NIR wavelengths, the emission from large dust grains at $r>$26 au is negligible, as shown in our SED fitting (§ [4.2](#subsec:mcrt)). The value of $M_{\rm cav}^{\rm small}$ is expected to be very small because the NIR flux is consistent with stellar photospherical emission. We assumed that the excess emission at NIR wavelengths is optically thin (i.e., a transitional disk with a cavity, (cite: espaillat10)). The surface density of small dust grains inside the cavity, $\Sigma_{\rm cav}^{\rm small}$, was assumed to vary with the radius as $$\begin{eqnarray*}
\Sigma_{\rm cav}^{\rm small}(r)=\Sigma_{\rm cav}^{\rm small}(r_0) (r/r_0)^\alpha \ 
\mbox{for } r^{\rm min} < r < r^{\rm max}
\end{eqnarray*}$$ where $r_0=$1 au and $\Sigma_{\rm cav}^{\rm small}(r_0)$ is the surface density at 1 au. The total dust mass is thus $$\begin{eqnarray*}
 M_{\rm cav}^{\rm small} = \int_{r^{\rm min}}^{r^{\rm max}} \Sigma_{\rm cav}^{\rm small}(r) 2\pi r dr. 
\end{eqnarray*}$$ We calculated the equilibrium temperature of optically thin dust at each radius inside the cavity, $T(r)$, using the `HOCHUNK3D` code. The total NIR flux from the cavity dust at a given wavelength is $$\begin{eqnarray*}
 I(\lambda)=\int_{r_{\rm min}}^{r_{\rm max}} B(T(r),\lambda) \kappa_{\rm small}(\lambda) \Sigma_{\rm cav}^{\rm small}(r) 2\pi r dr, 
\end{eqnarray*}$$ where $B(T(r),\lambda)$ is the Planck function at $T(r)$ and $\lambda$, and $\kappa_{\rm small}(\lambda)$ is the absorption opacity of small dust grains. Note that because our purpose is to derive the total mass of small dust grains from the upper limit of the observed flux, disk inclination is not needed to take into account in the calculation.

At $\lambda=$10 $\mu$m, the upper limit on the IR excess of the system $\lambda F(\lambda)$ is $2.5\times10^{-13}$ ergs s$^{-1}$ cm$^{-2}$. Assuming that $r^{\rm min}$ is the dust sublimation radius at 0.03 at, $r^{\rm max}$ is 60 au, and $\alpha=-1$ (self-similar viscous disk solution with viscosity $\propto$ radius, (cite: lyndenbell74)), the upper limit on $M_{\rm cav}^{\rm small}$ is $4\times10^{-7}M_\oplus$ ($\Sigma^{\rm small}_{r=26 {\rm au}}=1.2\times10^{-9}$ g cm$^{-2}$, equivalent to $\delta^{\rm small}=4\times10^{-7}$). We note that the value of $M_{\rm cav}^{\rm small}$ is only weakly affected by the chosen wavelength. For example, using $\lambda=$3.35 $\ensuremath{\mu}m$, the associated upper limit on the disk flux $\lambda F(\lambda)<7.9\times10^{-13}$ ergs s$^{-1}$ cm$^{-2}$ yields $M_{\rm cav}^{\rm small} = 1\times10^{-6}M_\oplus$. Decreasing $r_{\rm max}$ reduces $M_{\rm cav}^{\rm small}$ (e.g., setting $r_{\rm max}=$5 au results in $M_{\rm cav}^{\rm small}=4\times10^{-8}M_\oplus$) and increasing $r_{\rm min}$ has the opposite effect (e.g., setting $r_{\rm min}=$1 au results in $M_{\rm cav}^{\rm small}=8\times10^{-6}M_\oplus$). Flattening or reversing the dependence of $\Sigma_{\rm cav}^{\rm small}(r)$ on radius yields a higher value of $M_{\rm cav}^{\rm small}$ (e.g., setting $\alpha=1$ results in $M_{\rm cav}^{\rm small}=1\times10^{-3}M_\oplus$).

We conclude that the amount of small dust inside the millimeter emission cavity is tiny, less than a lunar mass under reasonable assumptions. The mass of large dust grains at $r<$60 au is $\sim$7 $M_{\ensuremath{\oplus}}$, and thus the ratio of the mass of small dust grains to that of large dust grains is smaller than $\sim$10$^{-4}$.

# Discussion

## Comparison with other systems

The sizes of the cavities of large and small dust grains have been discussed by combining NIR direct imaging and radio interferometry (cite: dong12cavity; vill2019a). Additionally, assuming that small dust grains are well coupled to the gas, measured CO gas distributions might serve as a proxy of the spatial distribution of small dust grains. CO gas observations with sufficient spatial resolution and sensitivity have been conducted with ALMA (cite: vandermarel+15b; vandermarel+16; vandermarel18a). The general trend of the cavity sizes in the disk of large dust grains vs. small ones (or CO gas) indicates that the cavity size in the disk of large dust grains is largest. The ratios of $r_{\rm cav}^{\rm small}$ to $r_{\rm cav}^{\rm large}$ and those of $r_{\rm cav}^{\rm CO}$ to $r_{\rm cav}^{\rm large}$ from the literature are compiled in Figure [5](#fig5). These results can be interpreted as outcomes of planet–disk interactions (cite: zhu12; dujuanovelar2013; facc2018b), as described in § [1](#sec:intro).

For Sz 84, the cavity sizes show the opposite trend (Figure [5](#fig5)), i.e., the disk composed of small dust grains has a larger cavity, as shown in § [4](#sec:model). As far as we know, such structures can only be found in DM Tau ($r_{\rm cav}^{\rm small} \sim$3 au and $r_{\rm cav}^{\rm large} \sim$1 au; Hashimoto et al. submitted). Systems with a larger cavity in the disk of small dust grains may be relatively rare. (cite: vill2019a) and (cite: vandermarel+16; vandermarel18a) compared the cavity sizes ($r_{\rm cav}^{\rm small}$ vs. $r_{\rm cav}^{\rm large}$ or $r_{\rm cav}^{\rm CO}$ vs. $r_{\rm cav}^{\rm large}$) for 24 objects and found that all the disks have larger cavities of large dust grains (Figure [5](#fig5)). There are currently two objects (Sz 84 and DM Tau) that have a larger cavity in the disk of small dust grains, accounting for 7.7 % of objects observed with NIR direct imaging and ALMA. However, current NIR observations are biased toward brighter objects ($R$ band $\lesssim$12 mag) due to the limitations of the adaptive optics system. Future observations with extreme adaptive optics systems such as VLT/SPHERE and Subaru/SCExAO would increase the number of samples (especially faint objects) and thus further constrain the statistics.

![](fig5v2.eps)

## Origin of cavities

Although systems with large dust grains inside the cavity in the disk of small dust grains may be rare, Sz 84 data have important implications for understanding planet formation. Here, we discuss the possible origins of such cavity structures. Some formation mechanisms of the cavity have been proposed, including photoevaporation (cite: clar2001a; alex2014), planet–disk interactions (cite: kley12), grain growth (cite: dull2005a), radiation pressure (cite: krum2019a), and a combination of these mechanisms (e.g., planet $+$ grain growth; (cite: zhu12)).

*Photoevaporation —* The basic idea of photoevaporation is that high-energy radiation (UV/X-ray) from the central star heats the surface of the disk, and the hot gas ($\sim$10$^{3}$–10$^{4}$ K) escapes from the disk as a photoevaporative wind. Because small dust grains are well coupled to the gas, they flow with the gas, possibly resulting in similar sizes of the cavities in the disks of small dust grains and gas. However, $^{12}$CO emissions can be clearly seen at $r<$60 au (Figure [1](#fig1)). Furthermore Sz 84 has a moderate mass accretion rate (cite: mana14). Thus, photoevaporation does not seem to be a viable mechanism for creating the cavity in the disk around Sz 84 (cite: erco2017a).

*Planet–disk interactions —* This mechanism is commonly considered as a potential origin of transitional disks (cite: espaillat+14). However, the robust detection of young planets that possibly induce cavity/gap structures is currently very limited (cite: kepp18a; haff19a), and no planets have been detected around Sz 84. Additionally, as mentioned above (§ [5.1](#subsec:comparison)), the spatial distributions of small and large dust grains expected for planet–disk interactions are opposite to those around Sz 84. Furthermore, as discussed in (cite: zhu12), because gas ($+$ small dust grains) can flow across the planet-induced gap, NIR excess in the SED emitted by hot ($\gtrsim$100–1000 K) dust grains around the central star cannot be sufficiently suppressed by only planet–disk interactions. This is also opposite to Sz 84’s SED with negligible NIR excess. Therefore, planet–disk interactions alone cannot account for the observational results for Sz 84.

*Grain growth —* To account for a transitional disk system with negligible NIR excess in the SED and a moderate mass accretion, only small dust grains in the vicinity of the central star need to be removed. For this purpose, (cite: zhu12) introduced grain growth in addition to planet–disk interactions. Dust grains grow faster in the inner region of the disk because of a faster dynamical time scale (cite: brauer+2008), and thus small dust grains are dispersed from the inside out. However, large dust grains are expected to fragment into small dust grains depending on disk turbulence (cite: weid1984a) and/or their stickiness (cite: wada2009), and thus weak dust fragmentation is required to efficiently remove small dust grains. Numerical simulations of grain growth with no/low fragmentation show a deficit of flux at NIR to MIR wavelengths in the SED (cite: dull2005a; birn2012a). Moreover, as grain growth does not affect gas distribution, the mass accretion would be unchanged. Hence, grain growth with less efficient fragmentation would explain both the spatial distributions of dust grains at $r\gtrsim$10 au and the moderate mass accretion rate of Sz 84. We note that our modeling in § [4](#sec:model) implies that the inner disk at $r\lesssim$10 au is optically thin at $\lambda \lesssim$10 $\mu$m for both small and large dust grains, which could be interpreted as meaning that dust grains are large enough to radially drift to the central star (cite: brauer+2008) or have already grown into planetesimals (cite: okuz2012; kata2013a).

As mentioned in § [5.1](#subsec:comparison), Sz 84 could be a very rare system because most T Tauri stars have IR excesses in their SEDs (cite: espaillat+14). These facts suggest that in most T Tauri star systems, small dust grains need to be replenished after being removed by grain growth, for instance by dust fragmentation through high-speed collisions. Under reasonable assumptions, the balance of the rates of grain growth and fragmentation determines whether T Tauri star systems have IR excess. For Sz 84, grain growth could be very efficient and/or fragmentation could be very inefficient, potentially due to weak turbulence in the disk or stickier dust grains.

Furthermore, according to numerical simulations in (cite: dull2005a), the time scale of grain growth with less effective fragmentation required to create the dip at NIR to MIR wavelengths in the SED is expected to be $\lesssim$0.1 Myr, and the cavity size in the disk of small dust grains reaches $r\sim$100 au within 1 Myr (see model F2 in Figure 6). This picture is roughly consistent with Sz 84 ($r_{\rm cav}^{\rm small} =$60 au in § [4.2](#subsec:mcrt); an age of 1 Myr, (cite: alca2014)). In contrast, DM Tau, which also has larger cavities of small dust grains, as mentioned in the previous subsection (§ [5.1](#subsec:comparison)), has a cavity size on the order of 1 au even though the cavity’s age is $\sim$1 Myr (cite: andr2013). Because the time scale of the cavity formation on the order of $r=$1 au via grain growth is predicted to be $\sim$0.01 Myr (cite: dull2005a), slow grain growth might occur in DM Tau’s disk. These results suggest that Sz 84 has more efficient grain growth and/or more insufficient fragmentation than those of DM Tau because the time scale of the cavity formation might also depend on the balance of grain growth and fragmentation. Therefore, Sz 84 could serve as an excellent testbed for investigating grain growth with less efficient fragmentation because dust fragmentation is one of the big problems in planet formation. One way to test the scenario of grain growth is to investigate the spectral index as a function of radius. Future multiple wavelength observations with higher spatial resolution and better sensitivity will guide our understanding of the cavity formation mechanism around Sz 84.

*Radiation pressure —* Another possible mechanism for the selective removal of small dust grains is radiation pressure (cite: krum2019a; owen2019). Stellar radiation radially and rapidly pushes away small dust grains, whereas large dust grains persist for a longer time, when the radiation pressure force on dust grains is stronger than the drag force of the gas. To suppress this drag force, (cite: krum2019a) reduced the gas density to less than 1 % of the minimum mass solar nebula (cite: weid77; haya1981). Additionally, because the dust disk needs optically thin conditions to avoid shielding stellar radiation, a dust-to-mass ratio of less than 10$^{-4}$ is preferable. Consequently, radiation pressure could efficiently remove small dust grains on gas-poor systems, i.e., debris disks. Conversely, the protoplanetary disk of Sz 84 is likely to be a gas-rich system, as detected in $^{12}$CO (Figure [1](#fig1)), and therefore, radiation pressure can be safely ruled out as the dominant mechanism for cavity formation around Sz 84.

# Conclusion

We observed the transitional disk around the T Tauri star Sz 84 at band 6 ($\lambda \sim$1.3 mm) with a spatial resolution of 0.2$''$ (30 au) with ALMA. We clearly detected a dust continuum and $^{12}$CO $J=2\rightarrow1$ line emissions. Although the SED of Sz 84 exhibits obvious deficits of IR excess at $\lambda \lesssim$10 $\mu$m, indicating a cavity structure with a size of $\sim$100 au in diameter, the dust continuum image does not show any cavity structures. In contrast, the observed visibilities of the dust continuum clearly show a null point at the $uv$-distance of $\sim$450 k$\lambda$, suggesting a cavity structure in dust continuum. These observational results motivated us to conduct analyses of the visibilities and the SED to explore the structures of the dust disk. Our main findings are as follows.

1.  The spectral index ($\alpha$) at bands 3, 6, and 7 (0.9 to 3 mm) is 2.42 $\pm$ 0.04, which is lower than the value of $\alpha \sim$2.7 found in other transitional disk systems (cite: pini2014a).

2.  The analyses of visibilities and the SED show that the cavity in the disk consisting of small dust grains is located at $r\gtrsim$60 au, and that large dust grains are present inside the cavity in the disk of small dust grains at $r\sim$60 au down to $\sim$10 au. Gas is also present at $r<$60 au in the $^{12}$CO moment 0 map.

3.  A transitional disk in which the size of the cavity in the disk of small dust grains is larger than that in the disk of large dust grains may be rare (to our knowledge, only Sz 84 and DM Tau), accounting for 7.7 % of objects observed with NIR direct imaging and ALMA (cite: vill2019a; vandermarel+16; vandermarel18a). Note that we assumed that the cavity sizes in disks of gas and small dust grains are identical in the modeling of CO gas taken from (cite: vandermarel+16; vandermarel18a).

4.  To account for the observational results for Sz 84 (spatial distributions of dust grains and gas in the disk, SED with negligible IR excess, and moderate mass accretion), grain growth and less efficient fragmentation (i.e., not photoevaporation, planet–disk interactions, or radiation pressure) are the likely mechanisms for cavity formation around Sz 84. Grain growth is thought to be an important first step in planet formation, and dust fragmentation prevents dust grains from growing into larger bodies. Therefore, Sz 84 is a good testbed for investigating grain growth with inefficient fragmentation of dust grains.

# Acknowledgments

We thanks an anonymous referee for a helpful review of the manuscript. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00571.S, ADS/JAO.ALMA#2015.1.01301.S, and ADS/JAO.ALMA#2013.1.00220.S. ALMA is a partnership among ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. This work is based in part on archival data obtained with the Spitzer Space Telescope, which was operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with NASA. Support for this work was provided by an award issued by JPL/Caltech. This work was supported by JSPS KAKENHI Grant Numbers 19H00703, 19H05089, 19K03932, 18H05442, 15H02063, and 22000005. Y.H. is supported by the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA.

*Software*: `vis_sample` (cite: loomis+17), `HOCHUNK3D` (cite: whit2013), `CASA` (cite: mcmu07), `emcee` (cite: foreman-mackey+2013)

Here, we provide additional supporting tables and figures. ALMA observations of archive data from bands 3 and 7 used in this paper are summarized in Table [4](#tab:band3-7).

|  | Band 3 | Band 7 |
|:---|:---|:---|
| Observing date (UT) | 2016.Oct.06 | 2015.Jun.14 |
| Project code | 2016.1.00571.S | 2013.1.00220.S |
| Time on source (min) | 6.0 | 2.2 |
| Number of antennas | 42 | 41 |
| Baseline lengths | 18.6 m to 3.1 km | 21.4 m to 0.78 km |
| Baseband Freqs. (GHz) | 90.6, 92.5, 102.6, 104.5 | 328.3, 329.3, 330.6, 340.0, 341.8 |
| Channel width (MHz) | 0.98, 0.98, 0.98, 0.98 | 15.6, 0.122, 0.122, 0.244, 0.977 |
| Continuum band width (GHz) | 7.5 | 4.8 |
| Bandpass calibrator | J1517$-$2422 | J1427$-$4206 |
| Flux calibrator | J1427$-$4206 | Titan |
| Phase calibrator | J1610$-$3958 | J1610$-$3958 |
| New phase center with GAIA | 15h58m2.50256s, -37d36m3.1157s | 15h58m2.50402s, -37d36m3.0857s |

: ALMA observations of archive data

Table notes: Because bands 3 and 6 data are mainly used for visibility analyses in § [4.1](#subsec:mcmc), we do not describe the imaging parameters.

Figure [6](#figA1) shows the $^{12}$CO $J=2-1$ channel maps at $-$1.0 to $+$11.0 km/s.

![](figA1v1.eps)

Figure [7](#figA3) shows the best-fit model image of the disk around Sz 84 based on MCMC model fitting in § [4.1](#subsec:mcmc).

![](figA3v2.eps)

Figures [8](#figA2), [9](#figA5), and [10](#figA6) show corner plots of the MCMC posteriors calculated in the visibility fitting for bands 6, 3, and 7, respectively, in § [4.1](#subsec:mcmc).

![](figA2v2.eps)

![](figA5v2.eps)

![](figA6v2.eps)

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Band | Flux | $r_{\rm cav1}$ | $r_{\rm cav2}$ | $\gamma_{1}$ | $\gamma_{2}$ | $\delta$ | $i$ | P.A. |
|  | (mJy) | (au) | (au) |  |  |  | ($\ensuremath{^\circ}$) | ($\ensuremath{^\circ}$) |
| Band 3 | 1.70$^{+0.06}_{-0.05}$ | 8.70$^{+4.67}_{-5.83}$ | 23.71$^{+7.74}_{-4.15}$ | 1.45$^{+3.89}_{-5.38}$ | 6.98$^{+2.11}_{-2.12}$ | 0.54$^{+0.32}_{-0.36}$ | 64.73$^{+8.15}_{-10.94}$ | 152.43$^{+22.92}_{-1.88}$ |
|  | {0.0-3.0} | {0.0 .. 21.4} | {15.3 .. 45.8} | {0.0 .. 10} | {-10 .. 10} | {0.001 .. 1.0} | {50 .. 80} | {150 .. 180} |
| Band 7 | 30.88$^{+5.44}_{-7.24}$ | 12.65$^{+2.12}_{-6.94}$ | 20.39$^{+16.73}_{-4.12}$ | 2.70$^{+2.46}_{-5.35}$ | 2.11$^{+0.42}_{-0.30}$ | 0.69$^{+0.23}_{-0.35}$ | 68.29$^{+9.18}_{-2.37}$ | 165.30$^{+8.26}_{-3.16}$ |
|  | {20.0-40.0} | {0.0 .. 21.4} | {15.3 .. 45.8} | {0.0 .. 10} | {-10 .. 10} | {0.001 .. 1.0} | {50 .. 80} | {150 .. 180} |

: Results of MCMC fitting for band 3 and 7 data and their parameter ranges

Table notes: Values in parentheses are parameter ranges in our MCMC calculations.

Table [6](#tab:phot) shows photometric and spectroscopic data of Sz 84 used in SED fitting in § [4.2](#subsec:mcrt).

|  |  |  |
|:---|:---|:---|
| Wavelength | $\lambda F_{\lambda}$ | Reference |
| ($\mu$m) | (10$^{-13}$ erg s$^{-1}$ cm$^{-2}$) |  |
| 0.44 | 132.0 | USNO-B1.0 (cite: mone2003) |
| 0.64 | 400.8 | USNO-B1.0 (cite: mone2003) |
| 0.80 | 1388.1 | USNO-B1.0 (cite: mone2003) |
| 1.235 | 2042.6 $\pm$ 43.2 | 2MASS (cite: cutr2003a) |
| 1.662 | 1758.1 $\pm$ 37.2 | 2MASS (cite: cutr2003a) |
| 2.159 | 1152.8 $\pm$ 24.4 | 2MASS (cite: cutr2003a) |
| 3.350 | 37.12 $\pm$ 7.9 | WISE (cite: cutr2014a) |
| 4.600 | 20.80 $\pm$ 4.0 | WISE (cite: cutr2014a) |
| 5.308 | 110.1 $\pm$ 8.3 | Spitzer/IRS (Spitzer Heritage Archive) |
| 5.520 | 104.7 $\pm$ 6.8 | Spitzer/IRS (Spitzer Heritage Archive) |
| 5.731 | 94.0 $\pm$ 6.4 | Spitzer/IRS (Spitzer Heritage Archive) |
| 5.943 | 94.2 $\pm$ 6.2 | Spitzer/IRS (Spitzer Heritage Archive) |
| 6.155 | 90.5 $\pm$ 6.0 | Spitzer/IRS (Spitzer Heritage Archive) |
| 6.366 | 79.6 $\pm$ 6.4 | Spitzer/IRS (Spitzer Heritage Archive) |
| 6.578 | 64.4 $\pm$ 7.1 | Spitzer/IRS (Spitzer Heritage Archive) |
| 6.790 | 63.7 $\pm$ 7.6 | Spitzer/IRS (Spitzer Heritage Archive) |
| 7.002 | 57.7 $\pm$ 8.3 | Spitzer/IRS (Spitzer Heritage Archive) |
| 7.213 | 55.0 $\pm$ 8.2 | Spitzer/IRS (Spitzer Heritage Archive) |
| 7.425 | 53.3 $\pm$ 8.9 | Spitzer/IRS (Spitzer Heritage Archive) |
| 7.701 | 37.2 $\pm$ 4.9 | Spitzer/IRS (Spitzer Heritage Archive) |
| 8.120 | 37.3 $\pm$ 3.8 | Spitzer/IRS (Spitzer Heritage Archive) |
| 8.544 | 40.1 $\pm$ 3.4 | Spitzer/IRS (Spitzer Heritage Archive) |
| 8.967 | 31.2 $\pm$ 3.3 | Spitzer/IRS (Spitzer Heritage Archive) |
| 9.391 | 27.1 $\pm$ 3.2 | Spitzer/IRS (Spitzer Heritage Archive) |
| 9.814 | 28.1 $\pm$ 2.7 | Spitzer/IRS (Spitzer Heritage Archive) |
| 10.24 | 24.7 $\pm$ 2.4 | Spitzer/IRS (Spitzer Heritage Archive) |
| 10.66 | 23.7 $\pm$ 2.6 | Spitzer/IRS (Spitzer Heritage Archive) |
| 11.08 | 18.1 $\pm$ 3.0 | Spitzer/IRS (Spitzer Heritage Archive) |
| 11.51 | 14.3 $\pm$ 3.1 | Spitzer/IRS (Spitzer Heritage Archive) |
| 11.93 | 15.5 $\pm$ 3.2 | Spitzer/IRS (Spitzer Heritage Archive) |
| 12.35 | 10.9 $\pm$ 3.0 | Spitzer/IRS (Spitzer Heritage Archive) |
| 12.78 | 14.7 $\pm$ 2.9 | Spitzer/IRS (Spitzer Heritage Archive) |
| 13.20 | 11.5 $\pm$ 3.5 | Spitzer/IRS (Spitzer Heritage Archive) |
| 13.62 | 11.1 $\pm$ 3.8 | Spitzer/IRS (Spitzer Heritage Archive) |
| 14.05 | 10.9 $\pm$ 4.3 | Spitzer/IRS (Spitzer Heritage Archive) |
| 14.58 | 6.7 $\pm$ 2.5 | Spitzer/IRS (Spitzer Heritage Archive) |
| 15.17 | 7.4 $\pm$ 2.8 | Spitzer/IRS (Spitzer Heritage Archive) |
| 15.76 | 11.4 $\pm$ 2.2 | Spitzer/IRS (Spitzer Heritage Archive) |
| 16.36 | 8.0 $\pm$ 3.0 | Spitzer/IRS (Spitzer Heritage Archive) |
| 16.95 | 7.4 $\pm$ 2.8 | Spitzer/IRS (Spitzer Heritage Archive) |
| 17.54 | 10.9 $\pm$ 2.7 | Spitzer/IRS (Spitzer Heritage Archive) |
| 18.13 | 7.6 $\pm$ 3.3 | Spitzer/IRS (Spitzer Heritage Archive) |
| 18.73 | 11.1 $\pm$ 3.2 | Spitzer/IRS (Spitzer Heritage Archive) |
| 19.32 | 12.7 $\pm$ 4.7 | Spitzer/IRS (Spitzer Heritage Archive) |
| 19.91 | 14.8 $\pm$ 3.8 | Spitzer/IRS (Spitzer Heritage Archive) |
| 20.54 | 11.8 $\pm$ 4.6 | Spitzer/IRS (Spitzer Heritage Archive) |
| 21.61 | 23.0 $\pm$ 3.2 | Spitzer/IRS (Spitzer Heritage Archive) |
| 22.79 | 27.1 $\pm$ 2.4 | Spitzer/IRS (Spitzer Heritage Archive) |
| 23.98 | 31.3 $\pm$ 2.2 | Spitzer/IRS (Spitzer Heritage Archive) |
| 25.16 | 37.7 $\pm$ 2.3 | Spitzer/IRS (Spitzer Heritage Archive) |
| 26.35 | 41.3 $\pm$ 2.2 | Spitzer/IRS (Spitzer Heritage Archive) |
| 27.53 | 49.1 $\pm$ 2.1 | Spitzer/IRS (Spitzer Heritage Archive) |
| 28.72 | 57.6 $\pm$ 2.6 | Spitzer/IRS (Spitzer Heritage Archive) |
| 29.90 | 61.4 $\pm$ 2.4 | Spitzer/IRS (Spitzer Heritage Archive) |
| 31.09 | 67.6 $\pm$ 3.1 | Spitzer/IRS (Spitzer Heritage Archive) |
| 32.27 | 78.9 $\pm$ 3.4 | Spitzer/IRS (Spitzer Heritage Archive) |
| 33.46 | 87.7 $\pm$ 5.2 | Spitzer/IRS (Spitzer Heritage Archive) |
| 34.65 | 103.2 $\pm$ 4.9 | Spitzer/IRS (Spitzer Heritage Archive) |
| 35.83 | 109.7 $\pm$ 9.6 | Spitzer/IRS (Spitzer Heritage Archive) |
| 37.02 | 112.3 $\pm$ 9.2 | Spitzer/IRS (Spitzer Heritage Archive) |
| 63 | 190.0 $\pm$ 4.8 | Herschel (cite: rivi2016a) |
| 70 | 105.0 $\pm$ 3.1 | Spitzer/MIPS (cite: meri2010a) |
| 909 | 1.14 $\pm$ 0.14 | ALMA (cite: vandermarel18a) |
| 1300 | 0.30 $\pm$ 0.003 | ALMA (this work) |

: Photometric and spectroscopic values of Sz 84

Table notes: The value of $A_{V}=$0.5 mag (cite: mana14) is applied here.

Figure [11](#figA4) shows the azimuthally averaged radial profile at $r<$150 au based on MCMC model fitting and MCRT modeling in § [4.1](#subsec:mcmc) and § [4.2](#subsec:mcrt), respectively, to test the consistency of the surface brightness in the two models.

![](figA4v4.eps)

natexlab

(ref: alca2014) Alcalá, J. M., Natta, A., Manara, C. F., et al. 2014, A&A, 561, A2, doi: [`10.1051/0004-6361/201322254`](http://doi.org/10.1051/0004-6361/201322254)

(ref: alca2017) Alcalá, J. M., Manara, C. F., Natta, A., et al. 2017, A&A, 600, A20, doi: [`10.1051/0004-6361/201629929`](http://doi.org/10.1051/0004-6361/201629929)

(ref: alex2014) Alexander, R., Pascucci, I., Andrews, S., Armitage, P., & Cieza, L. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 475, doi: [`10.2458/azu_uapress_9780816531240-ch021`](http://doi.org/10.2458/azu_uapress_9780816531240-ch021)

(ref: andr2013) Andrews, S. M., Rosenfeld, K. A., Kraus, A. L., & Wilner, D. J. 2013, ApJ, 771, 129, doi: [`10.1088/0004-637X/771/2/129`](http://doi.org/10.1088/0004-637X/771/2/129)

(ref: ansd2016a) Ansdell, M., Williams, J. P., van der Marel, N., et al. 2016, ApJ, 828, 46, doi: [`10.3847/0004-637X/828/1/46`](http://doi.org/10.3847/0004-637X/828/1/46)

(ref: ansd2018a) Ansdell, M., Williams, J. P., Trapman, L., et al. 2018, ApJ, 859, 21, doi: [`10.3847/1538-4357/aab890`](http://doi.org/10.3847/1538-4357/aab890)

(ref: beichman05) Beichman, C. A., Bryden, G., Gautier, T. N., et al. 2005, ApJ, 626, 1061, doi: [`10.1086/430059`](http://doi.org/10.1086/430059)

(ref: birn2012a) Birnstiel, T., Andrews, S. M., & Ercolano, B. 2012, A&A, 544, A79, doi: [`10.1051/0004-6361/201219262`](http://doi.org/10.1051/0004-6361/201219262)

(ref: brauer+2008) Brauer, F., Dullemond, C. P., & Henning, T. 2008, A&A, 480, 859, doi: [`10.1051/0004-6361:20077759`](http://doi.org/10.1051/0004-6361:20077759)

(ref: clar2001a) Clarke, C. J., Gendrin, A., & Sotomayor, M. 2001, MNRAS, 328, 485, doi: [`10.1046/j.1365-8711.2001.04891.x`](http://doi.org/10.1046/j.1365-8711.2001.04891.x)

(ref: cutr2014a) Cutri, R. M., & et al. 2014, VizieR Online Data Catalog, II/328

(ref: cutr2003a) Cutri, R. M., Skrutskie, M. F., van Dyk, S., et al. 2003, VizieR Online Data Catalog, II/246

(ref: dale2006) D’Alessio, P., Calvet, N., Hartmann, L., Franco-Hernández, R., & Servı́n, H. 2006, ApJ, 638, 314, doi: [`10.1086/498861`](http://doi.org/10.1086/498861)

(ref: dujuanovelar2013) de Juan Ovelar, M., Min, M., Dominik, C., et al. 2013, A&A, 560, A111, doi: [`10.1051/0004-6361/201322218`](http://doi.org/10.1051/0004-6361/201322218)

(ref: dong12cavity) Dong, R., Rafikov, R., Zhu, Z., et al. 2012, ApJ, 750, 161, doi: [`10.1088/0004-637X/750/2/161`](http://doi.org/10.1088/0004-637X/750/2/161)

(ref: drai2006) Draine, B. T. 2006, ApJ, 636, 1114, doi: [`10.1086/498130`](http://doi.org/10.1086/498130)

(ref: dull2005a) Dullemond, C. P., & Dominik, C. 2005, A&A, 434, 971, doi: [`10.1051/0004-6361:20042080`](http://doi.org/10.1051/0004-6361:20042080)

(ref: erco2017a) Ercolano, B., & Pascucci, I. 2017, Royal Society Open Science, 4, 170114, doi: [`10.1098/rsos.170114`](http://doi.org/10.1098/rsos.170114)

(ref: espaillat10) Espaillat, C., D’Alessio, P., Hernández, J., et al. 2010, ApJ, 717, 441, doi: [`10.1088/0004-637X/717/1/441`](http://doi.org/10.1088/0004-637X/717/1/441)

(ref: espaillat+14) Espaillat, C., Muzerolle, J., Najita, J., et al. 2014, Protostars and Planets VI, 497, doi: [`10.2458/azu_uapress_9780816531240-ch022`](http://doi.org/10.2458/azu_uapress_9780816531240-ch022)

(ref: facc2018b) Facchini, S., Pinilla, P., van Dishoeck, E. F., & de Juan Ovelar, M. 2018, A&A, 612, A104, doi: [`10.1051/0004-6361/201731390`](http://doi.org/10.1051/0004-6361/201731390)

(ref: foreman-mackey+2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: fran2020a) Francis, L., & van der Marel, N. 2020, arXiv e-prints, arXiv:2003.00079. [`https://arxiv.org/abs/2003.00079`](https://arxiv.org/abs/2003.00079)

(ref: gaia18) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1, doi: [`10.1051/0004-6361/201833051`](http://doi.org/10.1051/0004-6361/201833051)

(ref: garu2013) Garufi, A., Quanz, S. P., Avenhaus, H., et al. 2013, A&A, 560, A105, doi: [`10.1051/0004-6361/201322429`](http://doi.org/10.1051/0004-6361/201322429)

(ref: haff19a) Haffert, S. Y., Bohn, A. J., de Boer, J., et al. 2019, Nature Astronomy, 329, doi: [`10.1038/s41550-019-0780-5`](http://doi.org/10.1038/s41550-019-0780-5)

(ref: hashimoto+15) Hashimoto, J., Tsukagoshi, T., Brown, J. M., et al. 2015, ApJ, 799, 43, doi: [`10.1088/0004-637X/799/1/43`](http://doi.org/10.1088/0004-637X/799/1/43)

(ref: haya1981) Hayashi, C. 1981, Progress of Theoretical Physics Supplement, 70, 35, doi: [`10.1143/PTPS.70.35`](http://doi.org/10.1143/PTPS.70.35)

(ref: hend2020a) Hendler, N., Pascucci, I., Pinilla, P., et al. 2020, ApJ, 895, 126, doi: [`10.3847/1538-4357/ab70ba`](http://doi.org/10.3847/1538-4357/ab70ba)

(ref: joha2014a) Johansen, A., Blum, J., Tanaka, H., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 547, doi: [`10.2458/azu_uapress_9780816531240-ch024`](http://doi.org/10.2458/azu_uapress_9780816531240-ch024)

(ref: kata2013a) Kataoka, A., Tanaka, H., Okuzumi, S., & Wada, K. 2013, A&A, 557, L4, doi: [`10.1051/0004-6361/201322151`](http://doi.org/10.1051/0004-6361/201322151)

(ref: kepp18a) Keppler, M., Benisty, M., Müller, A., et al. 2018, A&A, 617, A44, doi: [`10.1051/0004-6361/201832957`](http://doi.org/10.1051/0004-6361/201832957)

(ref: kim1994) Kim, S.-H., Martin, P. G., & Hendry, P. D. 1994, ApJ, 422, 164, doi: [`10.1086/173714`](http://doi.org/10.1086/173714)

(ref: kley12) Kley, W., & Nelson, R. P. 2012, ARA&A, 50, 211, doi: [`10.1146/annurev-astro-081811-125523`](http://doi.org/10.1146/annurev-astro-081811-125523)

(ref: krum2019a) Krumholz, M. R., Ireland, M. J., & Kratter, K. M. 2019, arXiv e-prints, arXiv:1912.06788. [`https://arxiv.org/abs/1912.06788`](https://arxiv.org/abs/1912.06788)

(ref: kudo2018) Kudo, T., Hashimoto, J., Muto, T., et al. 2018, ApJL, 868, L5, doi: [`10.3847/2041-8213/aaeb1c`](http://doi.org/10.3847/2041-8213/aaeb1c)

(ref: loomis+17) Loomis, R. A., Öberg, K. I., Andrews, S. M., & MacGregor, M. A. 2017, ApJ, 840, 23, doi: [`10.3847/1538-4357/aa6c63`](http://doi.org/10.3847/1538-4357/aa6c63)

(ref: lyndenbell74) Lynden-Bell, D., & Pringle, J. E. 1974, MNRAS, 168, 603, doi: [`10.1093/mnras/168.3.603`](http://doi.org/10.1093/mnras/168.3.603)

(ref: mana14) Manara, C. F., Testi, L., Natta, A., et al. 2014, A&A, 568, A18, doi: [`10.1051/0004-6361/201323318`](http://doi.org/10.1051/0004-6361/201323318)

(ref: mcmu07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: meri2010a) Merı́n, B., Brown, J. M., Oliveira, I., et al. 2010, ApJ, 718, 1200, doi: [`10.1088/0004-637X/718/2/1200`](http://doi.org/10.1088/0004-637X/718/2/1200)

(ref: miya1993) Miyake, K., & Nakagawa, Y. 1993, Icarus, 106, 20, doi: [`10.1006/icar.1993.1156`](http://doi.org/10.1006/icar.1993.1156)

(ref: mone2003) Monet, D. G., Levine, S. E., Canzian, B., et al. 2003, AJ, 125, 984, doi: [`10.1086/345888`](http://doi.org/10.1086/345888)

(ref: naji15) Najita, J. R., Andrews, S. M., & Muzerolle, J. 2015, MNRAS, 450, 3559, doi: [`10.1093/mnras/stv839`](http://doi.org/10.1093/mnras/stv839)

(ref: okuz2012) Okuzumi, S., Tanaka, H., Kobayashi, H., & Wada, K. 2012, ApJ, 752, 106, doi: [`10.1088/0004-637X/752/2/106`](http://doi.org/10.1088/0004-637X/752/2/106)

(ref: owen2019) Owen, J. E., & Kollmeier, J. A. 2019, MNRAS, 487, 3702, doi: [`10.1093/mnras/stz1591`](http://doi.org/10.1093/mnras/stz1591)

(ref: pere2012) Pérez, L. M., Carpenter, J. M., Chand ler, C. J., et al. 2012, ApJL, 760, L17, doi: [`10.1088/2041-8205/760/1/L17`](http://doi.org/10.1088/2041-8205/760/1/L17)

(ref: pini2014a) Pinilla, P., Benisty, M., Birnstiel, T., et al. 2014, A&A, 564, A51, doi: [`10.1051/0004-6361/201323322`](http://doi.org/10.1051/0004-6361/201323322)

(ref: pini18a) Pinilla, P., Tazzari, M., Pascucci, I., et al. 2018, ApJ, 859, 32, doi: [`10.3847/1538-4357/aabf94`](http://doi.org/10.3847/1538-4357/aabf94)

(ref: rau11) Rau, U., & Cornwell, T. J. 2011, A&A, 532, A71, doi: [`10.1051/0004-6361/201117104`](http://doi.org/10.1051/0004-6361/201117104)

(ref: rice06) Rice, W. K. M., Armitage, P. J., Wood, K., & Lodato, G. 2006, MNRAS, 373, 1619, doi: [`10.1111/j.1365-2966.2006.11113.x`](http://doi.org/10.1111/j.1365-2966.2006.11113.x)

(ref: rivi2016a) Riviere-Marichalar, P., Merı́n, B., Kamp, I., Eiroa, C., & Montesinos, B. 2016, A&A, 594, A59, doi: [`10.1051/0004-6361/201527829`](http://doi.org/10.1051/0004-6361/201527829)

(ref: stei2019) Steinpilz, T., Teiser, J., & Wurm, G. 2019, ApJ, 874, 60, doi: [`10.3847/1538-4357/ab07bb`](http://doi.org/10.3847/1538-4357/ab07bb)

(ref: tazz2017a) Tazzari, M., Testi, L., Natta, A., et al. 2017, A&A, 606, A88, doi: [`10.1051/0004-6361/201730890`](http://doi.org/10.1051/0004-6361/201730890)

(ref: test2003) Testi, L., Natta, A., Shepherd, D. S., & Wilner, D. J. 2003, A&A, 403, 323, doi: [`10.1051/0004-6361:20030362`](http://doi.org/10.1051/0004-6361:20030362)

(ref: test2014) Testi, L., Birnstiel, T., Ricci, L., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 339, doi: [`10.2458/azu_uapress_9780816531240-ch015`](http://doi.org/10.2458/azu_uapress_9780816531240-ch015)

(ref: trap2020a) Trapman, L., Ansdell, M., Hogerheijde, M. R., et al. 2020, A&A, 638, A38, doi: [`10.1051/0004-6361/201834537`](http://doi.org/10.1051/0004-6361/201834537)

(ref: vandermarel+16) van der Marel, N., Cazzoletti, P., Pinilla, P., & Garufi, A. 2016, ApJ, 832, 178, doi: [`10.3847/0004-637X/832/2/178`](http://doi.org/10.3847/0004-637X/832/2/178)

(ref: vandermarel+15b) van der Marel, N., van Dishoeck, E. F., Bruderer, S., Pérez, L., & Isella, A. 2015, A&A, 579, A106, doi: [`10.1051/0004-6361/201525658`](http://doi.org/10.1051/0004-6361/201525658)

(ref: vandermarel13) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2013, Science, 340, 1199, doi: [`10.1126/science.1236770`](http://doi.org/10.1126/science.1236770)

(ref: vandermarel18a) van der Marel, N., Williams, J. P., Ansdell, M., et al. 2018, ApJ, 854, 177, doi: [`10.3847/1538-4357/aaaa6b`](http://doi.org/10.3847/1538-4357/aaaa6b)

(ref: vill2019a) Villenave, M., Benisty, M., Dent, W. R. F., et al. 2019, A&A, 624, A7, doi: [`10.1051/0004-6361/201834800`](http://doi.org/10.1051/0004-6361/201834800)

(ref: wada2009) Wada, K., Tanaka, H., Suyama, T., Kimura, H., & Yamamoto, T. 2009, ApJ, 702, 1490, doi: [`10.1088/0004-637X/702/2/1490`](http://doi.org/10.1088/0004-637X/702/2/1490)

(ref: weid77) Weidenschilling, S. J. 1977, MNRAS, 180, 57, doi: [`10.1093/mnras/180.1.57`](http://doi.org/10.1093/mnras/180.1.57)

(ref: weid1984a) —. 1984, Icarus, 60, 553, doi: [`10.1016/0019-1035(84)90164-7`](http://doi.org/10.1016/0019-1035(84)90164-7)

(ref: weid1993) Weidenschilling, S. J., & Cuzzi, J. N. 1993, in Protostars and Planets III, ed. E. H. Levy & J. I. Lunine, 1031

(ref: whit2013) Whitney, B. A., Robitaille, T. P., Bjorkman, J. E., et al. 2013, ApJS, 207, 30, doi: [`10.1088/0067-0049/207/2/30`](http://doi.org/10.1088/0067-0049/207/2/30)

(ref: wood2002) Wood, K., Wolff, M. J., Bjorkman, J. E., & Whitney, B. 2002, ApJ, 564, 887, doi: [`10.1086/324285`](http://doi.org/10.1086/324285)

(ref: yen2018a) Yen, H.-W., Koch, P. M., Manara, C. F., Miotello, A., & Testi, L. 2018, A&A, 616, A100, doi: [`10.1051/0004-6361/201732196`](http://doi.org/10.1051/0004-6361/201732196)

(ref: zhan16) Zhang, K., Bergin, E. A., Blake, G. A., et al. 2016, ApJL, 818, L16, doi: [`10.3847/2041-8205/818/1/L16`](http://doi.org/10.3847/2041-8205/818/1/L16)

(ref: zhu12) Zhu, Z., Nelson, R. P., Dong, R., Espaillat, C., & Hartmann, L. 2012, ApJ, 755, 6, doi: [`10.1088/0004-637X/755/1/6`](http://doi.org/10.1088/0004-637X/755/1/6)

[^1]: There are two types of transitional disk in the simple classical picture based on SED analyses (cite: espaillat+14). One has a cavity in which the central region of the disk is optically thin, and the other is an optically thick disk separated into inner and outer disks by an optically thin gap. Recent studies on transitional disks by (cite: fran2020a) suggest that the existence of the inner disk responsible for the NIR excess does not correlate with that in the dust continuum at (sub-)millimeter wavelengths, and that this discrepancy may not exist for large dust grains.

[^2]: https://gea.esac.esa.int/archive/

[^3]: We originally attempted to derive the disk structure from the band 3, 6, and 7 data simultaneously to map the spatial distribution of the spectral index $\alpha$. However, we mainly show the results from band 6 in this paper due to the insufficient baseline lengths and lower sensitivities of the band 3 and 7 data (Figures [9](#figA5) and [10](#figA6)). Data from all three bands were used only to derive the average value of $\alpha$ for the entire disk in § [3](#sec:result).

[^4]: Because the best-fit profile can be rather complex, we attempted to fit the best-fit profile with an asymmetric Gaussian profile (cite: pini18a) by eye in Figure [3](#fig2)(a). We found that the asymmetric Gaussian profile extends inside the inner cavity at $r_{\rm cav1}$, which results in significant IR excess, as shown in model C in § [4.2](#subsec:mcrt). Thus, we utilized the power-law radial profile in this paper.

[^5]: The value of $\delta$ was set to zero in the initial fitting. However, we immediately found that the model with $\delta=$0 produces visibilities with an excessively deep gap at the $uv$-distance of $\sim$600k$\lambda$ in Figure [3](#fig2)(b) and cannot well reproduce the observed visibilities. Therefore, we decided to set $\delta$ as a free parameter.

[^6]: Visibilities were deprojected in the $uv$-plane using the following equations (cite: zhan16): $u'    =   (u\,{\rm cos\,PA} - v\,{\rm sin\,PA}) \times {\rm cos}\,i,
      v'    =   (u\,{\rm sin\,PA} - v\,{\rm cos\,PA}),$ where $i$ and PA are free parameters in our visibility analyses in § [4.1](#subsec:mcmc).

</paper>

Write the methods card for this paper.