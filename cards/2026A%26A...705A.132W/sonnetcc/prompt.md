# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026A%26A...705A.132W\sonnetcc\reply.txt

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
 "bibcode": "2026A&A...705A.132W",
 "title": "Observation of CH<SUB>3</SUB><SUP>17</SUP>OH and CH<SUB>3</SUB><SUP>18</SUP>OH in Orion KL: A new tool to study star formation history",
 "year": 2026,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Watanabe, Yoshimasa",
 "n_authors": 5,
 "arxiv_id": "2510.08041",
 "doi": "10.1051/0004-6361/202556325",
 "alma_projects_linked_by_archive": [
  "2013.1.00553.S",
  "2011.0.00009.SV"
 ]
}
```

Paper text:
<paper>
# Observation of CH$_{3}$$^{17}$OH and CH$_{3}$$^{18}$OH in Orion KL: A New Tool to Study Star-Formation History

Methanol is a seed species of complex organic molecules that is of fundamental importance in astrochemistry. Although various isotopologues of CH$_3$OH have been detected in the interstellar medium (ISM), CH$_{3}$$^{17}$OH is only tentatively detected in Sgr B2. To confirm the presence of CH$_{3}$$^{17}$OH in the ISM and to investigate its abundance, we search for its emission lines in the Orion KL region.

We have obtained image cubes covering the frequency ranges 236.40 GHz-236.65 GHz and 231.68 GHz-231.88 GHz with a resolution of $\sim 2$ arcsec using ALMA archival data observed toward the Orion KL region. The spectra detected at the two CH$_3$$^{18}$OH peaks, MeOH1 and MeOH2, are compared to the spectrum and frequencies of CH$_{3}$$^{17}$OH measured in the laboratory. The column densities of CH$_3$$^{17}$OH and CH$_3$$^{18}$OH are estimated under the assumption of local thermodynamic equilibrium condition with fixed excitation temperatures.

We have identified six emission lines of CH$_{3}$$^{17}$OH in MeOH1 and MeOH2 and confirmed that the line profiles and spatial distributions are consistent with those of CH$_3$$^{18}$OH. The abundance ratios of CH$_3$$^{18}$OH/CH$_3$$^{17}$OH are evaluated to be $\sim 3.4-3.5$ and are similar to the canonical value of $^{18}$O/$^{17}$O $\sim 3-4$ derived from CO observations in the Orion KL region. We have compared the results with the previous study of CH$_3$OH and evaluated CH$_3$$^{16}$OH/CH$_3$$^{17}$OH ratios to be $\sim 2300-2500$ at a resolution of $\sim 4$ arcsec. The ratios are close to the $^{16}$O/$^{17}$O ratio in the local ISM.

This result indicates that the CH$_3$OH isotopologues can serve as new tracers of oxygen isotope ratios in star-forming regions because the opacity of CH$_3$OH can be evaluated using transition lines spanning a wide range of line intensities. Moreover, this method enables us to study the star-formation history of our Galaxy with the aid of the Galactic chemical evolution models.

![](Figure1.pdf)

# Introduction

Methanol (CH$_3$OH) is one of the most fundamental saturated organic molecules in interstellar medium (ISM) and a seed species of complex organic molecules. A laboratory experiment has demonstrated that this molecule is efficiently produced by the successive hydrogenation of CO on the surface of icy dust grains, as supported by theoretical and experimental studies (cite: Tielens1997; Watanabe2002). In cold molecular clouds, the CH$_3$OH formed is thought to be released into the gas phase through non-thermal sublimation driven by energy, such as surplus energy in chemical reactions, although the efficiency is not very high (cite: Garrod2007; Soma2015).

On the other hand, the CH$_3$OH in the inner envelope of protostellar core appears in the gas phase through desorption by protostellar heating. Such regions are called hot cores in massive-star forming regions, or hot corinos in low-mass star forming regions (cite: Blake1987; Dishoeck1995; Ceccarelli2007; Yang2021). CH$_3$OH has also been observed toward various objects including shocked regions induced by outflows from protostars (cite: Bachiller1997), and external galaxies (cite: Henkel1987; Watanabe2014).

The $^{18}$O isotopolog of CH$_3$OH has been observed in various objects (cite: Gardner1989; Gelder2022), while the observation of the $^{17}$O isotopolog has only been reported in a single case (cite: Muller2024). The primary reason for this was the lack of available laboratory spectroscopic data until recently. However, experimental spectroscopic measurements of CH$_3$$^{17}$OH have now been carried out and reported by (cite: Muller2024) and (cite: Tamanai2025). (cite: Muller2024) has presented rotational line list of CH$_3$$^{17}$OH and the tentative detection of it in Sgr B2(N2b). (cite: Tamanai2025) also conducted spectroscopic measurement from 216 GHz to 264 GHz by an emission-type millimeter and submillimeter spectrometer (cite: Watanabe2021) and reported line parameters of CH$_3$$^{17}$OH based on the spectroscopic data and previous study (cite: Hoshino1996). Moreover, they assigned several transition lines of $^{13}$CH$_3^{17}$OH, which were contained in the CH$_3$$^{17}$OH sample as the natural abundance of $^{13}$C. The study of CH$_3$$^{17}$OH in star-forming regions is still in its infancy, and the abundance ratios between CH$_3$$^{17}$OH and other CH$_3$OH isotopologues containing different oxygen isotopes are poorly understood. In contrast, deuterated CH$_3$OH isotopologues are known to be enhanced by 2-3 orders of magnitude compared with the cosmic H/D ratio of $\sim10^{-5}$ (cite: Mauersberger1988; Peng2012), due to grain-surface and gas-phase chemical reactions (cite: Charnley1997). Meanwhile, the abundance of $^{13}$CH$_3$OH is known to be similar to the elemental abundance ratio of $^{12}$C/$^{13}$C (cite: Soma2015). This is because CH$_3$OH molecules are mainly formed from CO molecules, which account for the majority of the carbon budget in the molecular clouds. In this study, we search for the CH$_3$$^{17}$OH emission lines in the Orion KL region by using the ALMA archive data and evaluate the isotope ratios of $^{18}$O/$^{17}$O, $^{16}$O/$^{17}$O, and $^{16}$O/$^{18}$O in CH$_3$OH.

Orion KL is nearby massive star forming region at the distance of $\sim 420$ pc (cite: Hirota2007; Menten2007). In this region, oxygen-bearing molecular species, such as CH$_3$OH and HCOOCH$_3$ are preferentially distributed in the vicinity of the compact ridge, while nitrogen-bearing molecular species, such as CH$_3$CN and CH$_3$CH$_2$CN, are associated around the hot core (cite: Wright1996; 2005Beuther; Tercero2018). (cite: Favre2011) identified 28 methyl formate emission peaks and found that the strongest peaks, MF1 and MF2, are in the compact ridge. (cite: Peng2012) also identified the strongest CH$_2$DOH emission peaks dM-1 and dM-3 in the almost identical positions as MF2 and MF1, respectively. As previous studies have demonstrated that CH$_3$OH shows a high column density and thus a high abundance in the compact ridge, we investigated the presence of CH$_3$$^{17}$OH lines in this region by using Atacama Large Millimeter/submillimeter Array (ALMA).

# Data and Reductions

We utilized two ALMA archival data ADS/JAO.ALMA #2013.1.00553.S (PI: P. Goldsmith) and ADS/JAO.ALMA #2011.0.00009.SV (the ALMA Science Verification data of Orion KL) to search for CH$_3$$^{17}$OH and CH$_3$$^{18}$OH, respectively. The observation of ADS/JAO.ALMA #2013.1.00553.S was conducted on 29 December 2014 toward the Orion KL region where the phase center was (R.A.(J2000), Dec.(J2000)) = ($05^{\rm h}35^{\rm m}14^{\rm s}.160$, $-05^{\circ}22'08''.504$). The details regarding the observation are described in (cite: Pagani2017). We used one spectral window that covered the frequency range from 236.26 GHz to 237.20 GHz with a frequency resolution of 488 kHz. The calibrated visibility data were acquired by applying the data reduction script provided by the ALMA observatory with the Common Astronomy Software Application (CASA) package (cite: casa2022) version 4.2.2 which contained the pipeline for the Cycle 2 ALMA observation. The visibility was imaged by using the CLEAN algorithm using Briggs weighting with a robustness parameter of 0.5, after the continuum emission was subtracted from the visibility data by fitting a 0$^{\rm th}$-order polynomial to the line free channels using task *uvcontsub*. The sensitivity and the synthesized beam of the cube data are 7 mJy beam$^{-1}$ and $1''.7 \times 1''.0$ with PA $=87.6^{\circ}$, respectively. The continuum image was made by the continuum visibility data generated by the task *uvcontsub*. Figure [1](#fig1) (a) shows the continuum image in the 1.3 mm band (236.7 GHz). The image reproduces the structures reported by (cite: Pagani2017) which used the same observation data.

The observation of ADS/JAO.ALMA #2011.0.00009.SV was carried out on 20 January 2012 at the phase center of (R.A.(J2000), Dec.(J2000)) = ($05^{\rm h}35^{\rm m}14^{\rm s}.350$, $-05^{\circ}22'36''.350$) as a part of the ALMA Science Verification to demonstrate the capabilities of spectral line survey observation with ALMA. The observation covered the frequency range from 214 GHz to 247 GHz with a frequency resolution of 488 kHz. Among the frequency range, we obtained synthesized image from 231.68 GHz to 231.88 GHz, witch contained 16 transitions of the $R$-branch series of CH$_3$$^{18}$OH with $J=5-4$. The calibrated visibility data was imaged by using the CLEAN algorithm by using Briggs weighting with a robustness parameter of 0.5 after the continuum emission was subtracted from the visibility data by fitting the 0$^{\rm th}$-order polynomial to the line free channels. The sensitivity and the synthesized beam of cube data are 12 mJy beam$^{-1}$ and $1''.9 \times 1''.4$ with PA $=-12.8^{\circ}$, respectively.

All the cube data and continuum images were corrected for the primary beam attenuation by applying task *impbcor*. CASA version 5.6.3 was used for all data processing after the calibration process.

![](Figure2.pdf)

![](Figure3.pdf)

# Results

## Detections of CH$_3$$^{18}$OH and CH$_3$$^{17}$OH

In the frequency range from 231.68 GHz to 231.88 GHz (Figure [2](#fig2) (a) and (b)), we detected the emission lines of CH$_3$$^{18}$OH ($5_0-4_0$ $E$) with a signal-to-noise (SN) ratio of more than $100\sigma$. Figure [1](#fig1) (b) is the integrated intensity map of CH$_3$$^{18}$OH ($5_0-4_0$ $E$) which is made by integrating the velocity range from 4.5 km s$^{-1}$ to 11.5 km s$^{-1}$. We found two prominent CH$_3$$^{18}$OH peaks, MeOH1 and MeOH2 (Table [1](#tab1)), which coincide with the methyl formate peaks, MF1 and MF2 (cite: Favre2011), respectively, within the synthesized beam of $1''.9 \times 1''.4$. In addition to the CH$_3$$^{18}$OH ($5_0-4_0$ $E$), 12 emission lines of CH$_3$$^{18}$OH are detected at the MeOH1 and MeOH2 in the frequency range, but most of them are contaminated by other molecules except for CH$_3$$^{18}$OH ($5_0-4_0$ $A^+$) and CH$_3$$^{18}$OH ($5_1-4_1$ $E$) (Figure [2](#fig2) (a) and (b)).

|  |  |  |  |
|:--:|:--:|:--:|:--:|
| Name | R.A. (J2000) | Dec. (J2000) | $V_{\rm LSR}$ $^{a}$ |
|  |  |  | (km s$^{-1}$) |
| MeOH1 | $05^{\rm h} 35^{\rm m} 14^{\rm s}.13$ | $-05^{\circ} 22' 36''.7$ | 7.50 |
| MeOH2 | $05^{\rm h} 35^{\rm m} 14^{\rm s}.44$ | $-05^{\circ} 22' 34''.9$ | 7.55 |

: Positions of MeOH1 and MeOH2

Table notes:

|  |  |  |  |  |
|:--:|:--:|:--:|---:|---:|
| Molecule | Transition | Freq. | $E_{\rm u}$ $^{a}$ | S$\mu^2$ |
|  |  | (GHz) | \(K\) | (Debye$^2$) |
| CH$_3$$^{18}$OH $^{b}$ | $5_{ 0}-4_{ 0}$ $E$ | 231.686680 | 46.22 | 16.166 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{-1}-4_{-1}$ $E$ | 231.735830 | 38.99 | 15.569 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{ 0}-4_{ 0}$ $A^+$ | 231.758446 | 33.38 | 16.194 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{ 4}-4_{ 4}$ $A^-$ | 231.768541 | 114.26 | 5.825 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{ 4}-4_{ 4}$ $A^+$ | 231.768542 | 114.26 | 5.825 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{-4}-4_{-4}$ $E$ | 231.777708 | 121.82 | 5.829 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{ 4}-4_{ 4}$ $E$ | 231.788110 | 129.55 | 5.867 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{ 3}-4_{ 3}$ $A^+$ | 231.796218 | 83.49 | 10.336 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{ 3}-4_{ 3}$ $A^-$ | 231.796521 | 83.49 | 10.336 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{ 3}-4_{ 3}$ $E$ | 231.801304 | 81.31 | 10.372 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{ 2}-4_{ 2}$ $A^-$ | 231.801466 | 70.86 | 13.755 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{-3}-4_{-3}$ $E$ | 231.809480 | 96.02 | 10.450 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{ 1}-4_{ 1}$ $E$ | 231.826744 | 54.14 | 16.171 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{ 2}-4_{ 2}$ $A^+$ | 231.840925 | 70.87 | 13.756 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{-2}-4_{-2}$ $E$ | 231.853853 | 59.26 | 13.625 |
| CH$_3$$^{18}$OH $^{b}$ | $5_{ 2}-4_{ 2}$ $E$ | 231.864501 | 55.77 | 13.380 |
| CH$_3$$^{17}$OH $^{c}$ | $5_{0}-4_{0}$ $E$ | 236.426222 | 47.09 | 4.041 |
| CH$_3$$^{17}$OH $^{c}$ | $5_{-1}-4_{-1}$ $E$ | 236.483332 | 39.68 | 3.887 |
| CH$_3$$^{17}$OH $^{c}$ | $5_{ 2}-4_{ 2}$ $A^-$ | 236.553557 | 71.71 | 13.380 |
| CH$_3$$^{17}$OH $^{c}$ | $5_{3}-4_{3}$ $E$ | 236.553786 | 82.09 | 2.590 |
| CH$_3$$^{17}$OH $^{c}$ | $5_{1}-4_{1}$ $E$ | 236.584222 | 55.04 | 4.020 |
| CH$_3$$^{17}$OH $^{c}$ | $5_{-2}-4_{-2}$ $E$ | 236.609861 | 60.04 | 3.403 |
| CH$_3$$^{17}$OH $^{c}$ | $5_{2}-4_{2}$ $E$ | 236.615575 | 56.47 | 3.345 |

: Line Parameters of Identified CH$_3$$^{18}$OH and CH$_3$$^{17}$OH

Table notes:

+:-----------:+:--------------------:+:------------------------:+:-----------------------------:+:---------------------------:+:---------------------------:+:---------------------------:+
| Position    | beam                 | Molecule                 | Column Density                | ${\rm O}^{18}/{\rm O}^{17}$ | ${\rm O}^{16}/{\rm O}^{17}$ | ${\rm O}^{16}/{\rm O}^{18}$ |
+-------------+----------------------+--------------------------+-------------------------------+-----------------------------+-----------------------------+-----------------------------+
|             |                      |                          | (cm$^{-2}$)                   |                             |                             |                             |
+-------------+----------------------+--------------------------+-------------------------------+-----------------------------+-----------------------------+-----------------------------+
| MeOH1       | $2''.0 \times 2''.0$ | CH$_3$$^{18}$OH $^{a,c}$ | $(3.7 \pm 0.2)\times 10^{15}$ | $3.3 \pm 0.2$               | N.A.                        | N.A.                        |
|             |                      +--------------------------+-------------------------------+                             |                             |                             |
|             |                      | CH$_3$$^{17}$OH $^{a,d}$ | $(1.1 \pm 0.6)\times 10^{15}$ |                             |                             |                             |
+-------------+----------------------+--------------------------+-------------------------------+-----------------------------+-----------------------------+-----------------------------+
| MeOH2       | $2''.0 \times 2''.0$ | CH$_3$$^{18}$OH $^{b,c}$ | $(9.8 \pm 0.5)\times 10^{15}$ | $3.3 \pm 0.2$               | N.A.                        | N.A.                        |
|             |                      +--------------------------+-------------------------------+                             |                             |                             |
|             |                      | CH$_3$$^{17}$OH $^{b,d}$ | $(3.0 \pm 0.2)\times 10^{15}$ |                             |                             |                             |
+-------------+----------------------+--------------------------+-------------------------------+-----------------------------+-----------------------------+-----------------------------+
| dM-1 $^{e}$ | $3''.8 \times 2''.0$ | CH$_3$$^{18}$OH $^{b,c}$ | $(6.5 \pm 0.3)\times 10^{15}$ | $3.5 \pm 0.3$               | $2300 \pm 300$              | $650 \pm 70$                |
|             |                      +--------------------------+-------------------------------+                             |                             |                             |
|             |                      | CH$_3$$^{17}$OH $^{b,d}$ | $(1.9 \pm 0.1)\times 10^{15}$ |                             |                             |                             |
|             |                      +--------------------------+-------------------------------+                             |                             |                             |
|             |                      | CH$_3$OH $^{b,f}$        | $(4.2 \pm 0.4)\times 10^{18}$ |                             |                             |                             |
+-------------+----------------------+--------------------------+-------------------------------+-----------------------------+-----------------------------+-----------------------------+
| dM-3 $^{g}$ | $3''.8 \times 2''.0$ | CH$_3$$^{18}$OH $^{a,c}$ | $(2.4 \pm 0.1)\times 10^{15}$ | $3.4 \pm 0.3$               | $2500 \pm 200$              | $710 \pm 60$                |
|             |                      +--------------------------+-------------------------------+                             |                             |                             |
|             |                      | CH$_3$$^{17}$OH $^{a,d}$ | $(6.9 \pm 0.4)\times 10^{14}$ |                             |                             |                             |
|             |                      +--------------------------+-------------------------------+                             |                             |                             |
|             |                      | CH$_3$OH $^{a,f}$        | $(1.7 \pm 0.1)\times 10^{18}$ |                             |                             |                             |
+-------------+----------------------+--------------------------+-------------------------------+-----------------------------+-----------------------------+-----------------------------+

Table notes:

We identified CH$_3$$^{17}$OH emission lines in the spectra from 236.26 GHz to 237.20 GHz at the two peaks (Figure [2](#fig2) (c) and (d)). The red spectrum shows the CH$_3$$^{17}$OH spectrum obtained from spectroscopic measurements in our laboratory (cite: Tamanai2025), for comparison with the observed spectra (black line). In MeOH1 and MeOH2, six emission lines are identified as CH$_3$$^{17}$OH with a S/N ratio of more than $50\sigma$. Most of the detected spectral lines are $E$ symmetry transitions, whereas a $A$ symmetry transition of $5_2-4_2~A^-$ is found to be blended with the $5_3-4_3~E$ line at 236.554 GHz. In addition to the CH$_3$$^{17}$OH lines, we assigned the other molecular lines in the spectra with the aid of spectral line databases, the Cologne Database for Molecular Spectroscopy (cite: Muller2001) and the Submillimeter, Millimeter, and Microwave Spectral Line Catalog provided by Jet Propulsion Laboratory (cite: Pickett1998). Figure [3](#fig3) shows the line profiles of CH$_3$$^{17}$OH and CH$_3$$^{18}$OH. Here, the cube data was convolved with Gaussian kernels to compare the spectra at the same angular resolution of $2''.0 \times 2''.0$. The peak velocities and line profiles of CH$_3$$^{17}$OH lines are similar to those of CH$_3$$^{18}$OH lines, although some of the CH$_3$$^{17}$OH lines are contaminated by other nearby molecular emission lines. The line profile shows two velocity components centered at $\sim 7.5$ km s$^{-1}$ and $\sim 9$ km s$^{-1}$ in MeOH1. The same velocity components have been detected by the observation of methyl formate in MF1 (cite: Favre2011). The integrated intensity maps of CH$_3$$^{17}$OH and CH$_3$$^{18}$OH lines are shown in Figure [4](#fig4). The maps were obtained by integrating the velocity range from 4.5 km s$^{-1}$ to 11.5 km s$^{-1}$. Most of CH$_3$$^{17}$OH images show peak emission at the two CH$_3$$^{18}$OH peaks MeOH1 and MeOH2, while some images (e.g., Figure [4](#fig4) (b) and (d)) show the strongest peaks at other positions due to contaminations of other molecular emission lines.

![](Figure4.pdf)

## Column densities

The column densities of CH$_3$$^{17}$OH and CH$_3$$^{18}$OH were calculated in MeOH1 and MeOH2 under the assumption of local thermodynamic equilibrium (LTE) approximation with optically thin conditions (Table [\[tab3\]](#tab3)). Since we are observing transition lines with the critical density of $n_{\rm crit} \sim 10^5$ cm$^{-3}$ [^1], the assumption of LTE is justified because the emissions originate from sufficiently dense regions with the H$_2$ volume density of $n_{\rm H_2} > 10^8$ cm$^{-3}$ (cite: Favre2011). We used the integrated intensities of CH$_3$$^{18}$OH ($5_0-4_0$ $E$) and CH$_3$$^{17}$OH ($5_0-4_0$ $E$) obtained from the convolved data cubes which have the common angular resolutions of $2''.0 \times 2''.0$. Using the CDMS and JPL databases, we have confirmed that these emission line are less contaminated by emission lines of other interstellar molecules. Assuming the canonical values of $^{16}$O/$^{18}$O $=560$ and $^{16}$O/$^{17}$O $=2000$ (cite: Wilson1999) and using the column densities and rotational temperatures of CH$_3$OH at dM-1 and dM-3 from (cite: Peng2012), the optical depths of CH$_3$$^{18}$OH ($5_0-4_0$ $E$) and CH$_3$$^{17}$OH ($5_0-4_0$ $E$) are expected to be $0.05-0.12$ and $0.01-0.04$, respectively. Therefore, the assumption of the optically thin condition is considered reasonable. In the calculation, we assumed the rotation temperature of 58 K and 130 K for MeOH1 and MeOH2, respectively, which are the rotation temperatures of CH$_3$OH in dM-3 and dM-1 (cite: Peng2012). Since we evaluated the column densities from the single transitions with the fixed rotation temperatures, the column densities are subject to uncertainties due to these factors.

By using the assumed rotation temperatures and the derived column densities of CH$_3$$^{17}$OH and CH$_3$$^{18}$OH, we generated model spectra under the LTE approximation and overlaid them on the observed spectra at MeOH1 and MeOH2 (blue spectra in Figure [2](#fig2)). Here, we utilized the line parameters of CH$_3$$^{17}$OH by (cite: Tamanai2025) and those in CDMS for CH$_3$$^{18}$OH (Table [2](#tab2)). The model spectra show good agreement with the observed spectra at the positions of CH$_3$$^{17}$OH and CH$_3$$^{18}$OH, except for the lines contaminated by emission lines from other molecules. For the CH$_3$$^{18}$OH, we also calculated the column densities using the integrated intensities of less contaminated CH$_3$$^{18}$OH ($5_1-4_1$ $E$) line in order to confirm the values. These are consistent, within the uncertainties, with the values obtained from CH$_3$$^{18}$OH ($5_0-4_0$ $E$). In this analysis, we attempted to estimate column density and rotation temperature by using the rotation diagram method, however, the limited range of the upper state energies ($E_{\rm u} = 40-60$ K) resulted in significant uncertainties in the derived values. Therefore, we employed the rotation temperatures of CH$_3$OH from (cite: Peng2012).

The CH$_3$$^{18}$OH/CH$_3$$^{17}$OH ratios are evaluated to be $3.3\pm 0.2$ in both MeOH1 and MeOH2, respectively. The assumed rotation temperatures have little effect on the CH$_3$$^{18}$OH/CH$_3$$^{17}$OH ratios because the upper state energies are very similar for the two transition lines due to the same quantum numbers.

In addition to the column densities in MeOH1 and MeOH2, the column densities of the two CH$_3$OH isotopologues were calculated in the two CH$_2$DOH peaks, dM-1 and dM-3, because (cite: Peng2012) estimated the column densities of CH$_3$OH main isotopologue by using the observation in the 101 GHz band with IRAM PdBI. In spite of the high column density of CH$_3$OH in the regions, the optical depths of the CH$_3$OH lines have been confirmed to be less than 0.2 (cite: Peng2012) due to the relatively small $S\mu^2$ values of these transition lines. The positions of dM-1 and dM-3 almost coincide with those of MeOH2 and MeOH1, respectively, within the beam size of the PdBI observation (Figure [1](#fig1)). We used the same procedures to calculate the column densities of the two CH$_3$OH isotopologues, after smoothing the angular resolution of the ALMA data to be $3''.8 \times 2''.0$ with PA of $22^{\circ}$ which is the observation beam of (cite: Peng2012). The rotation temperatures of 130 K and 58 K were adopted for dM-1 and dM-3, respectively, following (cite: Peng2012). The column densities of three isotopologues are summarized in Table [\[tab3\]](#tab3). The evaluated CH$_3$$^{16}$OH/CH$_3$$^{17}$OH, CH$_3$$^{16}$OH/CH$_3$$^{18}$OH, and CH$_3$$^{18}$OH/CH$_3$$^{17}$OH ratios are $2300\pm 300$, $650\pm 70$, and $3.5\pm 0.3$, respectively in dM-1.

# Discussion

## Comparisons of oxygen isotope ratios with those of other molecules

The isotopic ratios of $^{18}$O/$^{17}$O in the interstellar matter have been estimated from the observations of CO isotopologues (cite: Penzias1981). (cite: Persson2007) evaluated the $^{18}$O/$^{17}$O ratio of $3.6 \pm 0.7$ by using C$^{18}$O($J=5-4$) and C$^{17}$O($J=5-4$) observed with Odin satellite toward Orion KL. (cite: Plume2012) derived the $^{18}$O/$^{17}$O ratio of $4.1^{+2.1}_{-1.3}$ in the Compact Ridge, in which MeOH1 is associated, by using high-$J$ lines of CO isotopologues observed with Herschel/HIFI while they estimated different values of the ratios for the Hot Core ($3.0^{+1.2}_{-1.1}$), Outflow/Plateau ($1.7^{+0.4}_{-0.5}$), and Extended Ridge ($2.3\pm 0.5$). (cite: Zou2023) estimated the $^{18}$O/$^{17}$O ratio of $4.1\pm0.1$ in G209.00-19.38 in Orion Nebula by using C$^{18}$O($J=2-1$) and C$^{17}$O($J=2-1$) lines observed with SMT 10 m telescope. In addition, many transition lines of H$_2^{18}$O and H$_2$$^{17}$O have been detected toward Orion KL with Herschel/HIFI (cite: Melnick2010; Neill2013), but the $^{18}$O/$^{17}$O ratio was not estimated from the water isotopologues because the detected H$_2$$^{18}$O emission lines are moderately optically thick (cite: Neill2013).

The $^{18}$O/$^{17}$O ratios derived from CH$_3$OH isotopologues are consistent with the ratios derived from high-$J$ lines of CO isotopologues within the uncertainties. On the other hand, the ratio derived from the CO isotopologue lines with low-$J$ (cite: Zou2023) is significantly higher than those from CH$_3$OH isotopologues. The discrepancy cannot be explained by the optical depth of low-$J$ transition lines of CO isotopologues. The $^{18}$O/$^{17}$O ratio is likely to be underestimated, since the optical depth of C$^{18}$O is usually higher than that of C$^{17}$O by a factor of several. One possible explanation is that C$^{17}$O is dissociated by the selective photodissociation by the interstellar UV radiation because C$^{17}$O is optically thinner than C$^{18}$O as discussed by (cite: Plume2012). As a result, the $^{18}$O/$^{17}$O ratio derived from CO isotopologues would be higher than the canonical ratio. The transition lines of CO with low-$J$ especially tend to trace extended diffuse molecular gas which can be affected by the interstellar UV radiation. On the other hand, CH$_3$OH is thought to reside in the deep inside of dense gas and to be less affected by UV radiation. The other potential explanation is that the CH$_3$$^{18}$OH line is moderately optically thick.

The $^{16}$O/$^{17}$O ratio of $2300 \pm 300$ and $^{16}$O/$^{18}$O ratios of $650 \pm 70$ in dM-1 are consistent with the ratios of $^{16}$O/$^{17}$O $=2000\pm 200$ and $^{16}$O/$^{18}$O $=560\pm 30$ in the local ISM (cite: Wilson1999) within the uncertainty. In contrast, the $^{16}$O/$^{18}$O ratios are significantly higher than the isotopic ratios of methyl formate reported by (cite: Tercero2012), which estimated the $^{16}$O/$^{18}$O ratio to be $\sim 218$ from the total column density of the two isotopomer HC$^{18}$OOCH$_3$ and HCO$^{18}$OCH$_3$ observed with IRAM 30 m telescope toward Orion KL (cite: Tercero2010). The $^{16}$O/$^{18}$O ratio of CH$_3$OH should be compared with the ratio of HCOOCH$_3$/HC$^{18}$OOCH$_3$ or HCOOCH$_3$/HCO$^{18}$OCH$_3$ because HCOOCH$_3$ has two inequivalent oxygen atoms. The probability that each oxygen atom is substituted by $^{18}$O in HCOOCH$_3$ is expected to be proportional to the $^{16}$O/$^{18}$O ratio if neither fractionation nor dilution process is occurred by chemical reactions. Therefore, the $^{16}$O/$^{18}$O ratio in HCOOCH$_3$ is evaluated to be twice higher than the ratio by (cite: Tercero2012). Even if the factor of two is considered, our ratios are still higher than that of HCOOCH$_3$ by a factor of 1.5. One of the reasons for the underestimation is that the column density of the main HCOOCH$_3$ isotopologue is underestimated due to the use of optically thick transitions. Another possibility is the effect of missing flux caused by the different antenna configurations between the observations or the subthermal excitation condition of CH$_3$OH in this position as discussed in (cite: Peng2012). To confirm the difference, we need to observe multiple transition lines of CH$_3$OH and CH$_3$$^{18}$OH simultaneously with ALMA and apply an excitation analysis. This confirmation is for future work.

## CH$_3$OH as a tool of isotope ratio measurement

Although our analysis has uncertainty in the $^{16}$O/$^{18}$O ratio, the isotope ratios derived from CH$_3$OH isotopologue lines can potentially be more reliable value than those from the low-$J$ CO isotopologue lines because the CO isotopologues are sometimes affected by the optical thickness as well as the selective photodissociation by the intense interstellar UV radiation as aforementioned. However, it should be noted that CH$_3$OH is formed by hydrogenation of CO that has been frozen on interstellar dust grains in cold environments (cite: Watanabe2002; Soma2015). This implies that CH$_3$OH may preserve the isotopic ratios of CO from the prestellar phase when the gas density is relatively low. While CH$_3$OH is likely less affected by the selective photodissociation than the CO molecules that have remained exposed to interstellar UV radiation until the present day, the possible influence of this formation history on the derived isotope ratios warrants further investigation.

Specifically, future studies should examine the spatial distribution of CH$_3$$^{17}$OH and CH$_3$$^{18}$OH in hot cores or hot corinos with disk-like structures. By comparing the distributions from the outer regions where interstellar UV photons are more likely to penetrate to the inner regions where UV photons from the protostar are dominant, it may be possible to evaluate the effect of selective photodissociation on oxygen isotope ratios. Such studies, especially when discussed in connection with the known variation of $^{18}$O/$^{16}$O and $^{17}$O/$^{16}$O ratios in meteorites in the Solar system (cite: Clayton1993; Yurimoto2004), may provide valuable insights into the chemical origins of the Solar system.

The advantage of using CH$_3$OH isotopologues lies more in the following point than those mentioned above: if an appropriate frequency setting is selected, multiple transition lines of CH$_3$OH isotopologues can be simultaneously observed within a single ALMA frequency setup. As a result, precise isotope ratios are derived from the LTE modeling or the non-LTE modeling if the collision rates are available. Moreover, the column density of the main CH$_3$OH isotopologue is derived if optically thin transition lines with small line intensity $S\mu^2$ are carefully selected. As described in Section 4.1, the optical depth of spectral lines is a critical factor in obtaining reliable isotopic ratio estimates, especially for the main isotopologue. In our analysis, we employed the $J=5-4$ a-type transitions of CH$_3$$^{17}$OH and CH$_3$$^{18}$OH to derive the column density. However, the same transition lines of the main isotopologue could not be used due to high optical depth. Instead of these lines, we utilized the column densities of the main isotopologue which were derived from optically thin lines with smaller $S\mu^2$ values by (cite: Peng2012). Taking these into consideration, this method allows for a reliable estimation of oxygen isotopic ratios using this method. The elemental abundances are usually measured by the observation of atomic lines toward HII regions. The abundances of isotopes, however, cannot be measured at the same method because the atomic lines of isotopes are contaminated by the main isotopic line due to the relatively broad linewidth ($\sim 10$ km s$^{-1}$) in the HII regions. The isotope ratios are generally determined by the observation of isotopologues.

These isotope ratios can be used to constrain the star formation history of the Galaxy by the Galactic ‘chemical evolution’ (GCE) models. The elemental abundances reflect the star formation history in the Galaxy because the metal enrichment proceeds with nucleosynthesis in various types of stars. The negative abundance gradients for heavy elements along the Galactocentric distance have been known by the observations of atomic lines toward the Galactic HII regions (cite: Shaver1983; Arellano2020). The observed gradients of elemental abundances are thought to result from the inside-out star formation in the Galaxy (cite: Larson1976) and are explained by the GCE models (cite: Romano2022). Because different isotopes are synthesized by different processes, the isotopic ratios of stable isotopes provide unique parameters to constrain the GCE models. For instance, the $^{12}$C/$^{13}$C ratio increases with the Galactocentric distance (cite: Milam2005) because the primary element of $^{12}$C is produced faster than the secondary element of $^{13}$C. In the case of the oxygen isotopes, $^{18}$O is primarily produced in the massive star while $^{17}$O is synthesized in the intermediate-mass stars with longer timescale (cite: Henkel1993). (cite: Martin2019) reported that the $^{18}$O/$^{17}$O ratio is enhanced in the central molecular zone of starburst galaxy NGC 253 suggesting the enrichment of $^{18}$O by the massive stars. By the observation of CO isotopologues, a positive gradient of the $^{18}$O/$^{17}$O ratio has been reported (cite: Wouterloot2008; Zhang2020; Zou2023) in the Galaxy. Nevertheless, the sample size is small and scarce on the outer disk ($> 10$ kpc from the Galactic center). Therefore, simultaneous survey observations of CH$_3$$^{17}$OH, CH$_3$$^{18}$OH, and CH$_3$$^{16}$OH toward the hot cores on the outer disk regions with ALMA would increase the sample size of $^{18}$O/$^{17}$O and $^{16}$O/$^{18}$O ratios and contribute to improving the GCE models in our Galaxy.

# Conclusions

In this paper, the identification of emission lines of CH$_3$$^{17}$OH in the Orion KL region has been carried out by making use of our own experimentally measured spectra in the frequency range from 236.40 GHz to 236.65 GHz. We evaluated the abundance ratios of the CH$_3$OH isotopologues, CH$_3$$^{16}$OH, CH$_3$$^{17}$OH, and CH$_3$$^{18}$OH through comparative verification. The results are summarized as follows:

1.  We identified six emission lines of rare isotopologue CH$_3$$^{17}$OH toward the two CH$_3$$^{18}$OH emission peaks, MeOH1 and MeOH2, in Orion KL by using ALMA Archive data in the 1.3 mm band. Because the line profiles and spatial resolution of CH$_3$$^{17}$OH are similar to those of CH$_3$$^{18}$OH, these CH$_3$OH isotopologues are expected to reside in the same regions.

2.  The isotopologue ratios of CH$_3$$^{18}$OH/CH$_3$$^{17}$OH are derived to be $\sim 3.4\pm0.2$ on a resolution of 2.0 arcsec under the LTE approximation with fixed excitation temperatures. The ratios are consistent with the $^{18}$O/$^{17}$O ratios estimated from high excitation transition lines of CO isotopologues observed in the Orion KL region.

3.  We also estimated the CH$_3$$^{16}$OH/CH$_3$$^{17}$OH ratio to be $\sim 2300\pm200$ in dM-1 of Orion KL by using CH$_3$OH column density reported by (cite: Peng2012) on a resolution of $\sim 4.0$ arcsec and found that the ratios are consistent with the canonical $^{16}$O/$^{17}$O ratio in the local ISM.

4.  The simultaneous observation of CH$_3$OH isotopologues with ALMA would provide a unique method to estimate the isotope ratios of oxygen in the star-forming regions. Since transition lines of CH$_3$OH have wide range of the line intensities, optically thin transition lines can be used even for the main isotopologue. The measurements of the oxygen isotope ratios will contribute to constraining the GCE models and delineating the star formation history in the Galaxy.

# Acknowledgements

This paper makes use of the ALMA data set ADS/JAO.ALMA#2013.1.00553.S and ADS/JAO.ALMA#2011.0.00009.SV. ALMA is a partnership of the ESO (representing its member states), the NSF (USA) and NINS (Japan), together with the NRC (Canada) and the NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by the ESO, the AUI/NRAO and the NAOJ. The authors are grateful to the ALMA staff for their excellent support. This study is supported by a Grant-in-Aid from the Ministry of Education, Culture, Sports, Science, and Technology of Japan (No.20H05845) and a pioneering project in RIKEN (Evolution of Matter in the Universe). Y.W. acknowledges support from a Grant-in-Aid from the Ministry of Education, Culture, Sports, Science, and Technology of Japan (No.25K01042,24K00675,25H00676).

56 natexlab

(ref: Arellano2020) Arellano-Córdova, K. Z., Esteban, C., Garcı́a-Rojas, J., & Méndez-Delgado, J. E. 2020, MNRAS, 496, 1051

(ref: Bachiller1997) Bachiller, R. & Pérez Gutiérrez, M. 1997, ApJL, 487, L93

(ref: 2005Beuther) Beuther, H., Zhang, Q., Greenhill, L. J., et al. 2005, ApJ, 632, 355

(ref: Blake1987) Blake, G. A., Sutton, E. C., Masson, C. R., & Phillips, T. G. 1987, ApJ, 315, 621

(ref: casa2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Ceccarelli2007) Ceccarelli, C., Caselli, P., Herbst, E., Tielens, A. G. G. M., & Caux, E. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 47

(ref: Charnley1997) Charnley, S. B., Tielens, A. G. G. M., & Rodgers, S. D. 1997, ApJL, 482, L203

(ref: Clayton1993) Clayton, R. N. 1993, Annual Review of Earth and Planetary Sciences, 21, 115

(ref: Favre2011) Favre, C., Despois, D., Brouillet, N., et al. 2011, A&A, 532, A32

(ref: Fisher2007) Fisher, J., Paciga, G., Xu, L.-H., et al. 2007, Journal of Molecular Spectroscopy, 245, 7

(ref: Gardner1989) Gardner, F. F., Whiteoak, J. B., Reynolds, J., Peters, W. L., & Kuiper, T. B. H. 1989, MNRAS, 240, 35P

(ref: Garrod2007) Garrod, R. T., Wakelam, V., & Herbst, E. 2007, A&A, 467, 1103

(ref: Gerry1976) Gerry, M. C. L., Lees, R. M., & Winnewisser, G. 1976, Journal of Molecular Spectroscopy, 61, 231

(ref: Henkel1987) Henkel, C., Jacq, T., Mauersberger, R., Menten, K. M., & Steppe, H. 1987, A&A, 188, L1

(ref: Henkel1993) Henkel, C. & Mauersberger, R. 1993, A&A, 274, 730

(ref: Hirota2007) Hirota, T., Bushimata, T., Choi, Y. K., et al. 2007, PASJ, 59, 897

(ref: Hoshino1996) Hoshino, Y., Ohishi, M., Akabane, K., et al. 1996, ApJS, 104, 317

(ref: Hughes1951) Hughes, R. H., Good, W. E., & Coles, D. K. 1951, Physical Review, 84, 418

(ref: Ikeda1998) Ikeda, M., Duan, Y.-B., Tsunekawa, S., & Takagi, K. 1998, ApJS, 117, 249

(ref: Larson1976) Larson, R. B. 1976, MNRAS, 176, 31

(ref: Martin2019) Martı́n, S., Muller, S., Henkel, C., et al. 2019, A&A, 624, A125

(ref: Mauersberger1988) Mauersberger, R., Henkel, C., Jacq, T., & Walmsley, C. M. 1988, A&A, 194, L1

(ref: Melnick2010) Melnick, G. J., Tolls, V., Neufeld, D. A., et al. 2010, A&A, 521, L27

(ref: Menten2007) Menten, K. M., Reid, M. J., Forbrich, J., & Brunthaler, A. 2007, A&A, 474, 515

(ref: Milam2005) Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005, ApJ, 634, 1126

(ref: Muller2024) Müller, H. S. P., Ilyushin, V. V., Belloche, A., Lewen, F., & Schlemmer, S. 2024, A&A, 688, A201

(ref: Muller2001) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49

(ref: Neill2013) Neill, J. L., Wang, S., Bergin, E. A., et al. 2013, ApJ, 770, 142

(ref: Pagani2017) Pagani, L., Favre, C., Goldsmith, P. F., et al. 2017, A&A, 604, A32

(ref: Peng2012) Peng, T. C., Despois, D., Brouillet, N., Parise, B., & Baudry, A. 2012, A&A, 543, A152

(ref: Penzias1981) Penzias, A. A. 1981, ApJ, 249, 518

(ref: Persson2007) Persson, C. M., Olofsson, A. O. H., Koning, N., et al. 2007, A&A, 476, 807

(ref: Pickett1998) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: Plume2012) Plume, R., Bergin, E. A., Phillips, T. G., et al. 2012, ApJ, 744, 28

(ref: Predoi1997) Predoi-Cross, A., Lees, R. M., Lichau, H., Winnewisser, M., & Drummond, J. R. 1997, International Journal of Infrared and Millimeter Waves, 18, 2047

(ref: Romano2022) Romano, D. 2022, A&ARv, 30, 7

(ref: Schoier2005) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369

(ref: Shaver1983) Shaver, P. A., McGee, R. X., Newton, L. M., Danks, A. C., & Pottasch, S. R. 1983, MNRAS, 204, 53

(ref: Soma2015) Soma, T., Sakai, N., Watanabe, Y., & Yamamoto, S. 2015, ApJ, 802, 74

(ref: Tamanai2025) Tamanai, A., Oyama, T., Watanabe, Y., et al. 2025, ApJ, 980, 110

(ref: Tercero2010) Tercero, B., Cernicharo, J., Pardo, J. R., & Goicoechea, J. R. 2010, A&A, 517, A96

(ref: Tercero2018) Tercero, B., Cuadrado, S., López, A., et al. 2018, A&A, 620, L6

(ref: Tercero2012) Tercero, B., Margulès, L., Carvajal, M., et al. 2012, A&A, 538, A119

(ref: Tielens1997) Tielens, A. G. G. M. & Whittet, D. C. B. 1997, in IAU Symposium, Vol. 178, IAU Symposium, ed. E. F. van Dishoeck, 45

(ref: Dishoeck1995) van Dishoeck, E. F., Blake, G. A., Jansen, D. J., & Groesbeck, T. D. 1995, ApJ, 447, 760

(ref: Gelder2022) van Gelder, M. L., Jaspers, J., Nazari, P., et al. 2022, A&A, 667, A136

(ref: Watanabe2002) Watanabe, N. & Kouchi, A. 2002, ApJL, 571, L173

(ref: Watanabe2021) Watanabe, Y., Chiba, Y., Sakai, T., et al. 2021, PASJ, 73, 372

(ref: Watanabe2014) Watanabe, Y., Sakai, N., Sorai, K., & Yamamoto, S. 2014, ApJ, 788, 4

(ref: Wilson1999) Wilson, T. L. 1999, Reports on Progress in Physics, 62, 143

(ref: Wouterloot2008) Wouterloot, J. G. A., Henkel, C., Brand, J., & Davis, G. R. 2008, A&A, 487, 237

(ref: Wright1996) Wright, M. C. H., Plambeck, R. L., & Wilner, D. J. 1996, ApJ, 469, 216

(ref: Yang2021) Yang, Y.-L., Sakai, N., Zhang, Y., et al. 2021, ApJ, 910, 20

(ref: Yurimoto2004) Yurimoto, H. & Kuramoto, K. 2004, Science, 305, 1763

(ref: Zhang2020) Zhang, J. S., Liu, W., Yan, Y. T., et al. 2020, ApJS, 249, 6

(ref: Zou2023) Zou, Y. P., Zhang, J. S., Henkel, C., et al. 2023, ApJS, 268, 56

[^1]: The $n_{\rm crit}$ value is estimated from $A_{i,i}/C_{i,j}$ for CH$_3$OH ($5_0-4_0$, $E$) at 100 K where $A_{i,j}$ and $C_{i,j}$ is the Einstein A and C coefficient, respectively, from Leiden Atomic and Molecular Database (cite: Schoier2005).

</paper>

Write the methods card for this paper.