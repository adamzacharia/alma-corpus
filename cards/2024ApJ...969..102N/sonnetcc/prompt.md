# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...969..102N\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...969..102N",
 "title": "Physical and Chemical Properties of Galactic Molecular Gas toward QSO J1851+0035",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Narita, Kanako",
 "n_authors": 5,
 "arxiv_id": "2404.09984",
 "doi": "10.3847/1538-4357/ad3d5b",
 "alma_projects_linked_by_archive": [
  "2013.1.01035.S",
  "2015.1.00054.S",
  "2015.1.00072.S",
  "2015.1.00283.S",
  "2015.1.00600.S",
  "2015.1.00615.S",
  "2015.1.01454.S",
  "2015.1.01535.S",
  "2015.1.01571.S",
  "2016.1.00005.S",
  "2016.1.00010.S",
  "2016.1.00071.S",
  "2016.1.00988.S",
  "2016.1.01284.S",
  "2016.1.01346.S",
  "2016.1.01363.S",
  "2016.1.01548.S",
  "2017.1.00101.S",
  "2017.1.00377.S",
  "2017.1.00501.S",
  "2017.1.01248.S",
  "2018.1.00010.S",
  "2018.1.00024.S",
  "2018.1.00101.S",
  "2018.1.00190.S",
  "2018.1.00424.S",
  "2018.1.00443.S",
  "2018.1.00632.S",
  "2018.1.00659.L",
  "2018.1.00850.S",
  "2018.1.01242.S",
  "2019.1.00246.S",
  "2019.1.00685.S"
 ]
}
```

Paper text:
<paper>
# Physical and Chemical Properties of Galactic Molecular Gas toward QSO J1851+0035

## Abstract

ALMA data toward QSO J1851+0035 ($l$=$33.498^{\circ}$, $b$=$+0.194^{\circ}$) were used to study absorption lines by Galactic molecular gas. We detected 17 species (CO, $^{13}$CO, C$^{18}$O, HCO$^+$, H$^{13}$CO$^+$, HCO, H$_2$CO, C$_2$H, $c$-C$_3$H, $c$-C$_3$H$_2$, CN, HCN, HNC, CS, SO, SiO, and C) and set upper limits to 18 species as reference values for chemical models. About 20 independent velocity components at 4.7–10.9 kpc from the Galactic Center were identified. Their column density and excitation temperature estimated from the absorption study, as well as the CO intensity distributions obtained from the FUGIN survey, indicate that the components with $\tau$ $\lesssim$ 1 correspond to diffuse clouds or cloud outer edges. Simultaneous multiple-Gaussian fitting of CO $J$=1–0 and $J$=2–1 absorption lines shows that these are composed of narrow- and broad-line components. The kinetic temperature empirically expected from the high HCN/HNC isomer ratio ($\gtrsim$4) reaches $\gtrsim$40 K and the corresponding thermal width accounts for the line widths of the narrow-line components. CN-bearing molecules and hydrocarbons have tight and linear correlations within the groups. The CO/HCO$^+$ abundance ratio showed a dispersion as large as 3 orders of magnitude with a smaller ratio in a smaller $N$(HCO$^+$) (or lower $A_{\rm V}$) range. Some of the velocity components are detected in single-dish CO emission and ALMA HCO$^+$ absorption but without corresponding ALMA CO absorption. This may be explained by the mixture of clumpy CO emitters not resolved with the $\sim$1 pc single-dish beam surrounded by extended components with a very low CO/HCO$^+$ abundance ratio (i.e., CO-poor gas).

# Introduction

It is known that there is a large amount of interstellar gas, consisting of not only hydrogen and helium but also a wide variety of molecules of more than 200 different species known so far. Most of these species have been identified through their radio emission lines. The spatial distribution of individual species has also been mapped in line emission. However, such emission line studies are biased to denser parts where the lines are excited. In contrast, absorption line studies equally sample dense and diffuse gas through a narrow pencil beam toward background sources. Bright QSOs can be used as background sources for such studies with radio interferometers since a 1 Jy source observed at 100 GHz with a $1''$ resolution provides $\sim$120 K background.

Previous millimetric absorption studies have successfully observed low-excitation molecular gas in the Galaxy (cite: 1991ApJ...371L..77M; 1993A&A...276L..33L; 1994A&A...282L...5L; 2001A&A...370..576L; 2018A&A...610A..43R), and even in distant QSO host and lensing galaxies (cite: 2008Ap&SS.313..321C; 2011A&A...535A.103M). Such low-excitation transition regions between fully molecular and fully atomic gas may extend over large areas in the sky and account for a significant ($\sim$30%) amount of the neutral gas mass in the Galaxy (cite: 2013A&A...554A.103P). These gases may provide initial conditions for probing the physical and chemical evolution of molecular clouds, which are parent bodies of star formation. Little is known about the spatial extent and mass, internal structure including volume filling factor, detailed excitation conditions, chemical composition, and internal motion of the diffuse molecular gas. The study of diffuse molecular gas is thus crucial to understanding the full picture of the evolution of interstellar matter in the Galaxy. Although the number of such background sources behind the Galactic plane with known foreground absorption has been limited to about 30 systems, a recent systematic study of ALMA calibration sources significantly increased its total number (cite: 2016PASJ...68....6A; yoshimura2020).

The target of this study, QSO J1851+0035 (RA=18:51:46.723, DEC=+00:35:32.364; $l$=$33.498^{\circ}$, $b$=$+0.194^{\circ}$), is one of such sources with the largest visual extinction ($A_{\rm V}$), with $A_{\rm V}$ = 78.59 mag estimated from the $A_{\rm V}$ map of $Planck$ (cite: 2014A&A...571A..11P) by (cite: yoshimura2020). In addition to the observations for calibration purposes, this source was observed in $J$=1–0 and $J$=2–1 transition of CO, $^{13}$CO, and C$^{18}$O by ALMA with a high-velocity resolution, and also in $J$=1–0 emissions of CO, $^{13}$CO and C$^{18}$O by the NRO 45 m telescope (cite: 2019AAS...23325310K). The line of sight toward QSO J1851+0035 ($l$=$33.498^{\circ}$) crosses, from the near to far, the local Aql Rift, near Sagittarius arm, Scutum arm tangent, far Sagittarius arm, Perseus arm, Outer arm, and then Outer Scutum–Centaurus arm as shown in Figure [1](#fig:los).

# Data and analysis

## CO absorption data from ALMA

Absorption spectra toward QSO J1851+0035 were observed in Band 3 and 6 in ALMA Cycle 4 (project #2016.1.00010.S). Table [7](#table:archive-1a) shows the three setups of spectral windows that cover the $J$=2–1 and $J$=1–0 transitions of CO, $^{13}$CO, and C$^{18}$O in wide (2 GHz) and narrow ($\sim$59 or 117 MHz) bandwidths. The observations were run in three science blocks; each of which started from integrations of bandpass calibrator, J1924-2914, and flux calibrator, J1751+0939, and proceeded to integrations of the target, J1851+0035. The targets are bright enough for selfcal, and no separate gain calibrator was observed. The Common Astronomy Software Applications (CASA) package (cite: 2007ASPC..376..127M; cite-key) and ALMA data reduction pipeline were used to carry through the first part of data reduction, including corrections for baseline, system temperature, and water vapor fluctuations. After calibrating the visibility data, no deconvolution using the CLEAN method was performed, and a dirty map was created. The brightest peak of the QSO was extracted and divided by the continuum intensity to obtain a normalized profile. Natural weighting was selected to maximize the continuum sensitivity.

Figure [3](#fig:em_abs) shows the final absorption spectra.

## Absorption data from ALMA calibration data

The absorption study was also performed using archived ALMA data taken for calibration with QSO J1851+0035.

These data were taken for calibration purposes, and the angular resolution, frequency resolution, and sensitivity were not as good as those of the CO data. Details of the data used for this study are shown in Tables [7](#table:archive-1a)–[10](#table:archive-3) of Appendix [6](#sec:archive).

The data reduction was conducted using the CASA version 4.7.2, 6.4.3, 6.4.4, 6.5.0, and 6.5.2.

In the archived ALMA calibration data, the raw visibility data for the calibrator were flagged to mask the frequencies with significant absorption lines or contamination by atmospheric lines and interference. We thus generated a script to remove the flags in those parts to include them in our analysis. After calibrating the visibility data, the analysis was performed as described in [2.1](#sec:data_2).

Careful removal of the effects of the contamination by other species and other hyperfine components was also done. If components are available, the study was done based on these lines without using the possibly contaminated lines. Nevertheless, some velocity components were heavily contaminated by the other lines and were not included in the study for CN, HCN, and C$_2$H.

## CO emission data from NRO 45 m telescope data archive

To obtain the emissivity of individual components and the lower limit to the CO excitation temperature, the single pointing observations data in CO and $^{13}$CO $J$=1–0 emission line taken with the NRO 45 m telescope on 2019-04-07 UTC (Observation ID: 20190408020229, 20190408031727, 20190408045557, 20190408060934) were downloaded from Nobeyama 45m and ASTE Science Data Archive. Frequency resolution and bandwidth were set at 122.07 kHz (0.32 km s$^{-1}$ at 115 GHz) and 250 MHz (648 km s$^{-1}$). The final spectra of CO and $^{13}$CO after flagging, calibration, and linear baseline subtraction had a 1$\sigma$ sensitivity of 185 and 63 mK, respectively, in the main beam temperature $T_{\rm{mb}}$ at the full velocity resolution.

## Additional emission data with NRO 45 m telescope

To estimate the line ratios and excitation temperatures of dense gas tracers, the emission line data in HCO$^+$, HCN, HNC $J$=1–0 and C$_2$H $N$=1–0 were taken with the NRO 45 m telescope. FOREST (FOur-beam REceiver System on the 45-m Telescope) (cite: 2016SPIE.9914E..1ZM) was used for observations in a single pointing mode. The 2$\times$2 beams were aligned to have a beam spacing of $\sim$50$''$, and the full width of each beam was 18.3$\pm$$0.2''$ (H) 18.1$\pm$$0.2''$ (V) at 86 GHz and was 14.4$\pm$$0.4''$ (H) 14.6$\pm$$0.3''$ (V) at 110 GHz, respectively. The LO frequency was set to 95.0 GHz so that four lines (HCO$^+$, HCN, HNC $J$=1–0 and C$_2$H $N$=1–0) could be observed simultaneously. The observation was conducted in the mornings of 2023-03-21 and 2023-04-24 JST. The system noise temperature, including the sky, ranged from 166 to 358 K at the elevation of the source. Off position was set at RA(J2000)=18:59:09.616, DEC(J2000)=$-$00:04:12.52. This was confirmed to be emission-free in the observed lines through observations with relatively far different off positions known to be free of CO emission. Telescope pointing was established every $\sim$50 minutes with a nearby SiO maser source toward OH31.7$-$0.8 and was accurate at the level of 5$''$. The intensity calibration was done using the chopper wheel method. W51 (RA(J2000)=19:23:43.9, DEC(J2000)=$+$14:30:30.5) and G34.3$+$0.1 (RA(J2000)=18:53:18.7, DEC(J2000)=$+$01:14:58) were observed as standard sources to establish the absolute line intensity scale of the four beams. The scaled values for the HCO$^+$ $J$=1–0 line agree with those taken with the IRAM 30-m telescope by (cite: refId0). The frequency resolution and bandwidth were set at 122.07 kHz (0.32 km s$^{-1}$ at 115 GHz) and 250 MHz (648 km s$^{-1}$), respectively. After flagging, calibration, and linear baseline subtraction, the spectra had a 1$\sigma$ sensitivity of 2 mK at the 2-binning velocity resolution.

## CO maps from FUGIN survey

To understand the nature of the molecular gas toward the QSO, the CO and $^{13}$CO $J$=1–0 channel maps of the FUGIN (FOREST unbiased Galactic plane imaging survey with the Nobeyama 45 m telescope) project (cite: 2017PASJ...69...78U) were used. The original data were sliced to create a subset of $0.5^{\circ}$$\times$$0.5^{\circ}$ area centered at the line of sight toward QSO J1851+0035, and were smoothed in space and velocity domains for better signal-to-noise ratio. Specifications of the original and the smoothed sub-sample of the FUGIN data are summarized in Table [1](#table:fugin).

+-----------------------+-------------------------+-------------------------+
|                       | Original                | Smoothed                |
+:======================+:=======================:+:=======================:+
| Spatial resolution    | 20$''$                  | 40$''$                  |
+-----------------------+-------------------------+-------------------------+
| Spacial area          | $l$=33.25–33.75$^\circ$; $b$=0.04–0.34$^\circ$    |
+-----------------------+---------------------------------------------------+
| Spacial sampling      | $\Delta l$=$\Delta b$=8.5$''$                     |
+-----------------------+-------------------------+-------------------------+
| Velocity range        | $-100$–200 km s$^{-1}$  | $-30$–125 km s$^{-1}$   |
+-----------------------+-------------------------+-------------------------+
| Velocity resolution   | 0.65 km s$^{-1}$        | 1.3 km s$^{-1}$         |
+-----------------------+-------------------------+-------------------------+
| $1\sigma$ sensitivity | 1.5 K (CO)              | 0.5 K (CO)              |
+-----------------------+-------------------------+-------------------------+
|                       | 0.9 K ($^{13}$CO)       | 0.3 K ($^{13}$CO)       |
+-----------------------+-------------------------+-------------------------+

: Specifications of the original and the smoothed FUGIN sub-sample data used for this study

# Results

## Identification of species

### Detected species

Figure [2](#fig:band35678) shows the complete spectrum normalized to the detected continuum level. This figure illustrates the frequency coverage and sensitivity of the archive data used for this study, together with major lines and possible interference. The continuum level at the $1''$ resolution corresponds to $\sim$0.5 Jy at 100 GHz and $\sim$0.2 Jy at 350 GHz, respectively. Changes in the continuum level at this high-temperature range do not significantly affect the results of this study since the excitation temperature of the lines is significantly lower than these values, and the analysis is based on the opacities of the absorption lines.

Fourteen species (CO, $^{13}$CO, HCO$^+$, H$^{13}$CO$^+$, HCO, C$_2$H, $c$-C$_3$H, $c$-C$_3$H$_2$, CN, HCN, HNC, CS, SO, and SiO) were detected, including five with significant hyperfine structure, i.e., HCO, C$_2$H, $c$-C$_3$H, CN, and HCN. The line identification was carried out with the Cologne Database for Molecular Spectroscopy (CDMS) (cite: 2001A&A...370L..49M; 2005JMoSt.742..215M), the Jet Propulsion Laboratory (JPL) Submillimeter, Millimeter, and Microwave Spectral Line Catalog (cite: 1998JQSRT..60..883P), and Spectral Line Atlas of Interstellar Molecules (SLAIM).

Tables [2](#table:mol_data-1) and [3](#table:mol_data-2) show the spectral parameters of all detected or searched transitions. For the partition function $Q_{\rm CMB}$, we either referenced value from CDMS or summed up the states with $Q_{\rm CMB}$ = $\sum g_{\rm u} \exp (\frac{-E_{\rm l}}{k_{\rm B} T_{\rm CMB}})$, where $g_{\rm u}$ is the degeneracy of the upper state, $E_{\rm l}$ is the energy level of the lower state, $k_{\rm B}$ is the Boltzmann constant, and $T_{\rm CMB}$ is the cosmic microwave background temperature (2.73 K).

|  |  |  |  |  |  |  |  |
|:---|:--:|---:|:---|---:|---:|---:|:---|
| Species | Transitions | Frequency | $\mu$ | $S_{\rm ul}\mu^2$ | $Q_{\rm CMB}$ | $E_{\rm l}/k_{\rm B}$ | Reference |
|  |  | (GHz) | \(D\) | (D$^2$) |  | \(K\) |  |
| HC$^{18}$O$^+$ | $J$=1–0 | 85.162223 | 3.90 | 15.210 | 1.7259 | 0.00 | CDMS |
| $c$-${\rm C_3H_2}$ | $J_{K_a,K_c}$=$2_{1,2}$–$1_{0,1}$ (ortho) | 85.338893 | 3.43 | 52.945 | 8.8732 | 2.35 | JPL |
| HCS$^+$ | $J$=2–1 | 85.347890 | 1.86 | 7.667 | 3.0215 | 2.05 | CDMS |
| SO | $J_K$=$2_2$–$1_1$ | 86.093950 | 1.535 | 3.534 | 4.0346 | 15.18 | CDMS |
| H$^{13}$CN | $J$=1–0, $F$=2–1 | 86.340163 | 2.9852 | 14.853 | 5.1261 | 0.00 | CDMS |
| H$^{13}$CO$^+$ | $J$=1–0 | 86.754288 | 3.90 | 15.211 | 1.7028 | 0.00 | CDMS |
| HCO | $N_K$=$1_{0,1}$–$0_{0,0}$, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=2–1 | 86.670760 | 1.3626 | 3.094 | 6.7785 | 0.02 | JPL |
| HCO | $N_K$=$1_{0,1}$–$0_{0,0}$, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=1–0 | 86.708360 | 1.3626 | 1.817 | 6.7785 | 0.00 | JPL |
| HCO | $N_K$=$1_{0,1}$–$0_{0,0}$, $J$=$\frac{1}{2}$–$\frac{1}{2}$, $F$=1–1 | 86.777460 | 1.3626 | 1.817 | 6.7785 | 0.02 | JPL |
| HCO | $N_K$=$1_{0,1}$–$0_{0,0}$, $J$=$\frac{1}{2}$–$\frac{1}{2}$, $F$=0–1 | 86.805780 | 1.3626 | 0.619 | 6.7785 | 0.02 | JPL |
| SiO | $J$=2–1 | 86.846960 | 3.098 | 19.197 | 2.98 | 2.08 | CDMS |
| C$_2$H | $N$=1–0, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=1–1 | 87.284105 | 0.769 | 0.100 | 6.7735 | 0.00 | CDMS |
| C$_2$H | $N$=1–0, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=2–1 | 87.316898 | 0.769 | 0.986 | 6.7735 | 0.00 | CDMS |
| C$_2$H | $N$=1–0, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=1–0 | 87.328585 | 0.769 | 0.491 | 6.7735 | 0.00 | CDMS |
| C$_2$H | $N$=1–0, $J$=$\frac{1}{2}$–$\frac{1}{2}$, $F$=1–1 | 87.401989 | 0.769 | 0.491 | 6.7735 | 0.00 | CDMS |
| C$_2$H | $N$=1–0, $J$=$\frac{1}{2}$–$\frac{1}{2}$, $F$=0–1 | 87.407165 | 0.769 | 0.197 | 6.7735 | 0.00 | CDMS |
| C$_2$H | $N$=1–0, $J$=$\frac{1}{2}$–$\frac{1}{2}$, $F$=1–0 | 87.446470 | 0.769 | 0.100 | 6.7735 | 0.00 | CDMS |
| HCN | $J$=1–0, $F$=1–1 | 88.630416 | 2.984 | 8.912 | 5.03 | 0.00 | CDMS |
| HCN | $J$=1–0, $F$=2–1 | 88.631848 | 2.984 | 14.852 | 5.03 | 0.00 | CDMS |
| HCN | $J$=1–0, $F$=0–1 | 88.633936 | 2.984 | 2.971 | 5.03 | 0.00 | CDMS |
| HCO$^+$ | $J$=1–0 | 89.188525 | 3.90 | 15.210 | 1.6691 | 0.00 | CDMS |
| HOC$^+$ | $J$=1–0 | 89.487414 | 2.77 | 7.678 | 1.6651 | 0.00 | CDMS |
| $l$-C$_3$H$^+$ | $J$=4–3 | 89.957625 | 3.0 | 36.000 | 5.3963 | 6.48 | CDMS |
| HNC | $J$=1–0 | 90.663568 | 3.05 | 9.302 | 1.6497 | 0.00 | CDMS |
| $c$-C$_3$H | $N_{K_a,K_c}$=$2_{1,2}$–$1_{1,1}$, $J$=$\frac{5}{2}$–$\frac{3}{2}$, $F$=3–2 | 91.494349 | 2.4 | 12.096 | 5.6348 | 2.13 | (cite: 1987ApJ...322L..55Y) |
| $c$-C$_3$H | $N_{K_a,K_c}$=$2_{1,2}$–$1_{1,1}$, $J$=$\frac{5}{2}$–$\frac{3}{2}$, $F$=2–1 | 91.497608 | 2.4 | 7.776 | 5.6348 | 2.13 | (cite: 1987ApJ...322L..55Y) |
| $c$-C$_3$H | $N_{K_a,K_c}$=$2_{1,2}$–$1_{1,1}$, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=2–1 | 91.699471 | 2.4 | 7.720 | 5.6348 | 2.13 | (cite: 1987ApJ...322L..55Y) |
| CH$_3$CN | $J_K$=$5_0$–$4_0$ | 91.987086 | 3.922 | 76.558 | 13.8357 | 8.83 | SLAIM |
| N$_2$H$^+$ | $J$=1–0, $F1$=2–1, $F$=3–2 | 93.173772 | 3.40 | 26.972 | 14.5633 | 0.00 | CDMS |
| C$^{34}$S | $J$=2–1 | 96.412950 | 1.958 | 7.650 | 2.7242 | 1.62 | CDMS |
| CH$_3$OH | $J_{K_a,K_c}$=$2_{0,2}$–$1_{0,1}$, A | 96.741375 | 0.899 | 1.617 | 11.8899 | 2.32 | CDMS |
| CS | $J$=2–1 | 97.980953 | 1.958 | 7.644 | 2.6827 | 2.35 | CDMS |
| SO | $J_K$=$3_2$–$2_1$ | 99.299870 | 1.535 | 6.911 | 4.0346 | 4.46 | CDMS |
| CF$^+$ | $J$=1–0 | 102.587484 | 1.072 | 1.150 | 1.5167 | 0.00 | CDMS |
| H$_2$CS | $J_{K_a,K_c}$=$3_{0,3}$–$2_{0,2}$ | 103.040452 | 1.649 | 8.158 | 3.7879 | 4.95 | CDMS |
| SO$_2$ | $J_{K_a,K_c}$=$3_{1,3}$–$2_{0,2}$ | 104.029418 | 1.6331 | 5.373 | 5.3815 | 2.75 | CDMS |
| $^{13}$CN | $N$=1–0, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F1$=2–1, $F$=3–2 | 108.780201 | 1.45 | 4.905 | 17.3716 | 0.03 | CDMS |
| C$^{18}$O | $J$=1–0 | 109.782173 | 0.11049 | 0.012 | 1.4491 | 0.00 | CDMS |
| $^{13}$CO | $J$=1–0 | 110.201354 | 0.11046 | 0.024 | 2.8912 | 0.00 | CDMS |
| CN$^-$ | $J$=1–0, $F$=1–1 | 112.263694 | 0.65 | 0.141 | 4.2911 | 0.00 | CDMS |
| CN$^-$ | $J$=1–0, $F$=2–1 | 112.264993 | 0.65 | 0.235 | 4.2911 | 0.00 | CDMS |
| CN | $N$=1–0, $J$=$\frac{1}{2}$–$\frac{1}{2}$, $F$=$\frac{1}{2}$–$\frac{3}{2}$ | 113.144157 | 1.45 | 1.249 | 8.5178 | 0.00 | CDMS |
| CN | $N$=1–0, $J$=$\frac{1}{2}$–$\frac{1}{2}$, $F$=$\frac{3}{2}$–$\frac{1}{2}$ | 113.170492 | 1.45 | 1.220 | 8.5178 | 0.00 | CDMS |
| CN | $N$=1–0, $J$=$\frac{1}{2}$–$\frac{1}{2}$, $F$=$\frac{3}{2}$–$\frac{3}{2}$ | 113.191278 | 1.45 | 1.584 | 8.5178 | 0.00 | CDMS |
| CN | $N$=1–0, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=$\frac{3}{2}$–$\frac{1}{2}$ | 113.488120 | 1.45 | 1.584 | 8.5178 | 0.00 | CDMS |
| CN | $N$=1–0, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=$\frac{5}{2}$–$\frac{3}{2}$ | 113.490970 | 1.45 | 4.205 | 8.5178 | 0.00 | CDMS |
| CN | $N$=1–0, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=$\frac{1}{2}$–$\frac{1}{2}$ | 113.499644 | 1.45 | 1.249 | 8.5178 | 0.00 | CDMS |
| CN | $N$=1–0, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=$\frac{3}{2}$–$\frac{3}{2}$ | 113.508907 | 1.45 | 1.220 | 8.5178 | 0.00 | CDMS |
| CO | $J$=1–0 | 115.271202 | 0.11011 | 0.012 | 1.4053 | 0.00 | CDMS |

: Molecular data for detected/searched transitions in ALMA Band 3

|  |  |  |  |  |  |  |  |
|:---|:--:|---:|:---|---:|---:|---:|:---|
| Species | Transitions | Frequency | $\mu$ | $S_{\rm ul}\mu^2$ | $Q_{\rm CMB}$ | $E_{\rm l}/k_{\rm B}$ | Reference |
|  |  | (GHz) | \(D\) | (D$^2$) |  | \(K\) |  |
| C$_2$S | $N$=3–2, $J$=3–3 | 191.940220 | 2.88 | 0.251 | 31.7632 | 3.23 | CDMS |
| C$_2$S | $N$=3–2, $J$=2–1 | 214.571817 | 2.88 | 0.111 | 31.7632 | 0.53 | CDMS |
| H$_2$CO | $J_{K_a,K_c}$=$3_{0,3}$–$2_{0,2}$ | 218.222192 | 2.3317 | 16.308 | 2.0165 | 10.48 | CDMS |
| C$^{18}$O | $J$=2–1 | 219.560354 | 0.11049 | 0.024 | 1.4491 | 5.27 | CDMS |
| $^{13}$CO | $J$=2–1 | 220.398684 | 0.11046 | 0.049 | 2.8912 | 5.29 | CDMS |
| CN | $N$=2–1, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=$\frac{3}{2}$–$\frac{3}{2}$ | 226.632190 | 1.45 | 1.258 | 8.5178 | 5.43 | CDMS |
| CN | $N$=2–1, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=$\frac{5}{2}$–$\frac{3}{2}$ | 226.659558 | 1.45 | 4.191 | 8.5178 | 5.43 | CDMS |
| CN | $N$=2–1, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=$\frac{1}{2}$–$\frac{1}{2}$ | 226.663693 | 1.45 | 1.249 | 8.5178 | 5.43 | CDMS |
| CN | $N$=2–1, $J$=$\frac{3}{2}$–$\frac{1}{2}$, $F$=$\frac{3}{2}$–$\frac{1}{2}$ | 226.679311 | 1.45 | 1.554 | 8.5178 | 5.43 | CDMS |
| CN | $N$=2–1, $J$=$\frac{5}{2}$–$\frac{3}{2}$, $F$=$\frac{5}{2}$–$\frac{3}{2}$ | 226.874191 | 1.45 | 4.247 | 8.5178 | 5.45 | CDMS |
| CN | $N$=2–1, $J$=$\frac{5}{2}$–$\frac{3}{2}$, $F$=$\frac{7}{2}$–$\frac{5}{2}$ | 226.874781 | 1.45 | 6.728 | 8.5178 | 5.45 | CDMS |
| CN | $N$=2–1, $J$=$\frac{5}{2}$–$\frac{3}{2}$, $F$=$\frac{3}{2}$–$\frac{1}{2}$ | 226.875896 | 1.45 | 2.527 | 8.5178 | 5.45 | CDMS |
| CO | $J$=2–1 | 230.538000 | 0.11011 | 0.024 | 1.4053 | 5.53 | CDMS |
| CO$^+$ | $N$=2–1, $J$=$\frac{3}{2}$–$\frac{1}{2}$ | 235.789641 | 2.61 | 9.046 | 2.7714 | 5.67 | CDMS |
| CO$^+$ | $N$=2–1, $J$=$\frac{5}{2}$–$\frac{3}{2}$ | 236.062553 | 2.61 | 16.285 | 2.7714 | 5.67 | CDMS |
| SO | $J_K$=$1_2$–$0_1$ | 329.385477 | 1.535 | 0.103 | 4.0346 | 0.00 | CDMS |
| C$^{18}$O | $J$=3–2 | 329.330553 | 0.11049 | 0.037 | 1.4491 | 15.81 | CDMS |
| $^{13}$CO | $J$=3–2 | 330.587965 | 0.11046 | 0.073 | 2.8912 | 15.87 | CDMS |
| CN | $N$=3–2, $J$=$\frac{7}{2}$–$\frac{5}{2}$, $F$=$\frac{7}{2}$–$\frac{5}{2}$ | 340.247770 | 1.45 | 9.011 | 8.5178 | 16.33 | CDMS |
| CO | $J$=3–2 | 345.795990 | 0.11011 | 0.036 | 1.4053 | 16.60 | CDMS |
| SH$^+$ | $N$=0–1, $J$=1–0, $F$=$\frac{3}{2}$–$\frac{1}{2}$ | 345.944350 | 1.285 | 0.954 | 6.0025 | 0.00 | CDMS |
| ND | $N$=1–0, $J$=0–1, $F1$=1–2, $F$=2–3 | 491.933934 | 1.389 | 1.570 | 26.9872 | 0.00 | CDMS |
| C | $^3P_1$–$^3P_0$ | 492.160651 | — | 0.00017 | 1.0005 | 0.00 | CDMS |

: Molecular data for detected/searched transitions in ALMA Bands 5, 6, 7, 8

### Marginal and non-detection

C$^{18}$O, H$_2$CO, and C were marginally detected for some velocity components with the largest $^{13}$CO column density, presumably dark clouds. CO$^+$, HC$^{18}$O$^+$, HOC$^+$, CH$_3$OH, $l$-C$_3$H$^+$, $^{13}$CN, CN$^-$, H$^{13}$CN, CH$_3$CN, ND, N$_2$H$^+$, SH$^+$, C$^{34}$S, HCS$^+$, H$_2$CS, C$_2$S, SO$_2$, and CF$^+$ were also searched in the present data sets but were not detected.

The column density $N$ of the absorbing species can be deduced from the opacity $\tau$ of the absorption line integrated over the velocity range $v$ by assuming optically thin lines and the LTE (local thermodynamic equilibrium) conditions, $$\begin{equation}
\label{eq:n_tot}
N = \frac{3hQ(T_{\rm ex})}{8\pi^3\mu^2S_{\rm ul}} \frac{\exp(\frac{E_{\rm l}}{k_{\rm B} T_{\rm ex}})} {[1-\exp(\frac{-h\nu}{k_{\rm B}T_{\rm ex}})]} \int\tau dv, 
\end{equation}$$ where $h$ is the Planck constant, $\nu$ is the frequency of the transition, $k_{\rm B}$ is the Boltzmann constant, $Q(T_{\rm ex})$ is the partition function at the (assumed) excitation temperature $T_{\rm ex}$, $E_{\rm l}$ is the energy of the lower level, $\mu$ is the dipole moment, and $S_{\rm ul}$ is the line strength.

The column densities $N$ of these species or their 1$\sigma$ upper limits for Components 7 and 16 deduced in this manner are tabulated in Table [4](#table:non-detection). The abundance was calculated as $X$(M) $\equiv$ $N$(M)/$N$(H$_2$) by assuming $N$(H$_2$) to be $2 \times 10^{21}$ cm$^{-2}$ for Components 7 and 16. This $N$(H$_2$) value was determined to be in reasonable agreement with the one estimated from CO emission using the CO-to-H$_2$ conversion factor, the one from optically thin $^{13}$CO emission under the LTE condition, and the ones from HCO$^+$ and $c$-C$_3$H$_2$ absorption column densities. The values for TMC-1 Cyanopolyyne Peak (CP), which is often used to test chemical models, and FG0.89SW, which is a $z$ = 0.89 absorber with a large column of absorbing gas ($N$(H$_2$) $>$ $10^{22}$ cm$^{-2}$) toward PKS 1830$-$211, are also included as references.

+:-------------------+:-----------------------------:+------------:+:-----------------------------:+------------:+------------:+:-----:+------------:+:-----:+
|                    | Component 7                                 | Component 16                                | TMC-1 (CP)          | FG0.89SW            |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| Species            | $N$(M)                        | $\log X$(M) | $N$(M)                        | $\log X$(M) | $\log X$(M) | Ref   | $\log X$(M) | Ref   |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
|                    | ($10^{12}$ cm$^{-2}$)         |             | ($10^{12}$ cm$^{-2}$)         |             |             |       |             |       |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| H$_2$              | $2 \times 10^{9}$\*           | 0           | $2 \times 10^{9}$\*           | 0           | 0           |       | 0           |       |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| C                  | (19.1$\pm$4.17)$\times$$10^4$ | $-4.02$     | (6.16$\pm$3.77)$\times$$10^4$ | $-4.51$     |             |       | $-3.93$     | \(7\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| CO                 | (saturated)                   | ($-4.06$)   | (saturated)                   | ($-4.52$)   | ($-4.01$)   | \(5\) | $-4.20$     | \(7\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| $^{13}$CO          | 3461$\pm$47                   | $-5.76$     | 1209$\pm$24                   | $-6.22$     | $-5.79$     | \(5\) | $<$$-6.00$  | \(7\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| C$^{18}$O          | 19.7$\pm$13.5                 | $-8.01$     | 30.5$\pm$15.5                 | $-7.82$     | $-6.79$     | \(5\) | $<$$-6.00$  | \(7\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| CO$^+$             | $<$$0.72$                     | $<$$-9.44$  | $<$$0.83$                     | $<$$-9.38$  |             |       |             |       |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| HCO$^+$            | (saturated)                   | ($-8.76$)   | (saturated)                   | ($-8.64$)   | ($-8.00$)   | \(5\) | $-8.06$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| H$^{13}$CO$^+$     | 0.07$\pm$0.02                 | $-10.46$    | 0.09$\pm$0.02                 | $-10.34$    | $-9.78$     | \(5\) | $-$9.38     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| HC$^{18}$O$^+$     | $<$$0.03$                     | $<$$-10.83$ | 0.05$\pm$0.01                 | $-10.64$    | $-10.78$    | \(5\) | $-$9.74     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| HOC$^+$            | $<$$0.02$                     | $<$$-10.98$ | $<$$0.02$                     | $<$$-11.05$ |             |       | $-9.80$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| HCO                | 1.85$\pm$0.90                 | $-9.03$     | 1.92$\pm$0.65                 | $-9.02$     |             |       | $-9.19$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| H$_2$CO            | 4.52$\pm$1.70                 | $-8.65$     | 2.47$\pm$1.54                 | $-8.91$     | $-7.70$     | \(2\) | $-7.92$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| CH$_3$OH           | $<$$3.85$                     | $<$$-8.72$  | $<$$3.95$                     | $<$$-8.70$  | $-8.84$     | \(3\) | $-8.07$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| C$_2$H             | 81.36$\pm$5.19                | $-7.39$     | 41.68$\pm$2.59                | $-7.68$     | $-7.12$     | \(2\) | $-7.20$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| $l$-C$_3$H$^+$     | $<$$0.34$                     | $<$$-9.77$  | $<$$0.27$                     | $<$$-9.87$  |             |       |             |       |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| $c$-C$_3$H         | 0.85$\pm$0.21                 | $-9.37$     | 0.45$\pm$0.17                 | $-9.65$     | $-8.52$     | \(3\) |             |       |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| $c$-C$_3$H$_2$ (o) | 2.99$\pm$0.09                 | $-8.83$     | 1.22$\pm$0.09                 | $-9.21$     | $-8.73$     | \(3\) | $-8.71$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| CN                 | 30.87$\pm$0.37                | $-7.82$     | 22.21$\pm$0.31                | $-7.95$     | $-7.52$     | \(2\) |             |       |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| $^{13}$CN          | $<$$0.09$                     | $<$$-10.35$ | $<$$0.09$                     | $<$$-10.37$ |             |       |             |       |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| CN$^-$             | $<$$5.95$                     | $<$$-8.53$  | $<$$6.36$                     | $<$$-8.50$  | $<$$-9.85$  | \(4\) |             |       |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| HCN                | 9.58$\pm$0.30                 | $-8.37$     | 8.42$\pm$0.35                 | $-8.38$     | ($-8.15$)   | \(5\) | $-7.82$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| H$^{13}$CN         | $<$$0.09$                     | $<$$-10.35$ | $<$$0.09$                     | $<$$-10.37$ | $-9.93$     | \(5\) | $-9.38$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| HNC                | 1.97$\pm$0.06                 | $-9.00$     | 1.45$\pm$0.05                 | $-9.14$     | $-7.70$     | \(2\) | $-8.29$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| CH$_3$CN           | $<$$1.62$                     | $<$$-9.09$  | $<$$1.35$                     | $<$$-9.17$  | $-9.00$     | \(2\) | $-9.19$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| ND                 | $<$$76.41$                    | $<$$-7.42$  | $<$$60.70$                    | $<$$-7.52$  |             |       |             |       |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| N$_2$H$^+$         | $<$$0.49$                     | $<$$-9.61$  | $<$$0.42$                     | $<$$-9.68$  | $-9.11$     | \(5\) | $-8.93$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| SH$^+$             | $<$$5.04$                     | $<$$-8.60$  | $<$$3.66$                     | $<$$-8.74$  |             |       |             |       |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| CS                 | 7.86$\pm$0.15                 | $-8.41$     | 0.87$\pm$0.13                 | $-9.36$     | $-7.89$     | \(5\) | $-7.55$     | \(6\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| C$^{34}$S          | $<$$0.19$                     | $<$$-10.01$ | $<$$0.16$                     | $<$$-10.09$ | $-9.30$     | \(3\) | $-8.58$     | \(6\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| HCS$^+$            | $<$$0.76$                     | $<$$-9.42$  | $<$$0.60$                     | $<$$-9.52$  | $-9.40$     | \(5\) |             |       |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| H$_2$CS            | $<$$0.69$                     | $<$$-9.46$  | $<$$0.71$                     | $<$$-9.45$  | $-8.38$     | \(3\) | $-9.42$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| C$_2$S             | $<$$107.54$                   | $<$$-7.27$  | $<$$90.92$                    | $<$$-7.34$  | $-7.99$     | \(3\) | $-9.62$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| SO                 | 2.06$\pm$0.24                 | $-9.00$     | $<$$0.21$                     | $<$$-9.97$  | $-8.74$     | \(5\) | $-8.89$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| SO$_2$             | $<$$0.94$                     | $<$$-9.33$  | $<$$0.79$                     | $<$$-9.40$  | $-9.00$     | \(2\) | $<$$-10.28$ | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| SiO                | 0.36$\pm$0.07                 | $-9.74$     | $<$$0.06$                     | $<$$-10.54$ | $-11.62$    | \(1\) | $-9.43$     | \(8\) |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+
| CF$^+$             | $<$$0.36$                     | $<$$-9.75$  | $<$$0.34$                     | $<$$-9.77$  |             |       |             |       |
+--------------------+-------------------------------+-------------+-------------------------------+-------------+-------------+-------+-------------+-------+

: Column densities, abundances or their 1$\sigma$ upper limits for dark clouds – Components 7 and 16, TMC-1 Cyanopolyyne Peak, and FG0.89SW.

References: (1) (cite: 1989ApJ...343..201Z); (2) (cite: 1992IAUS..150..171O); (3) (cite: 2016ApJS..225...25G); (4) (cite: doi:10.1021/acs.chemrev.6b00480); (5) (cite: Fuente2019); (6) (cite: 2006A&A...458..417M); (7) (cite: 2009ApJ...690L.130B); (8) (cite: 2011A&A...535A.103M)

### Possible interference

Instrumental and atmospheric artifacts are also visible at some frequencies. Frequencies of possible interference are listed in Table [5](#table:interference). Most of them were identified to be the atmospheric emission of O$_3$. The one at 91.66 GHz is the interference due to the 6th harmonics of the local oscillator for the Water Vapor Radiometer (WVR) installed on the 12 m antennas. The one at 213.57 GHz is close to the 14th harmonics but does not perfectly match. The possibility of high-$z$ lines will be tested in Section [4.6](#sec:redshifted_lines).

|           |                      |
|:---------:|:---------------------|
| Frequency | Identification       |
|   (GHz)   |                      |
|   91.66   | WVR LO 6th harmonics |
|   96.23   | atmospheric (O$_3$)  |
|  101.74   | atmospheric (O$_3$)  |
|  110.84   | atmospheric (O$_3$)  |
|  213.57   | unidentified         |
|  214.80   | atmospheric (O$_3$)  |
|  231.61   | unidentified         |
|  235.71   | atmospheric (O$_3$)  |
|  237.14   | atmospheric (O$_3$)  |
|  239.07   | atmospheric (O$_3$)  |
|  242.28   | unidentified         |
|  243.41   | atmospheric (O$_3$)  |
|  258.70   | atmospheric (O$_3$)  |
|  331.06   | unidentified         |
|  359.60   | atmospheric (O$_3$)  |
|  478.83   | unidentified         |

: Possible interference

## Identification of velocity components

### Overall characteristics of velocity components and species

In Figure [3](#fig:em_abs), spectra of some species that characterize the absorption profile toward this line of sight are shown. HNC is an example of the CN-bearing molecules, $c$-${\rm C_3H_2}$ is that of hydrocarbons, and CS is that of the sulfur-bearing molecules and shock tracers. These species were chosen because they are free from hyperfine components, unlike CN, HCN, and C$_2$H.

We identified velocity components along this line of sight based on the absorption profiles in the CO, $^{13}$CO, and HCO$^+$ $J$=1–0 lines obtained with ALMA, as well as the emission profile in the CO $J$=1–0 line observed with the NRO 45 m telescope as shown in Table [6](#table:velcomp).

From the line profiles shown in Figure [3](#fig:em_abs), we note the following non-trivial characteristics:

- Both the CO and $^{13}$CO $J$=1–0 emission lines have near continuous emissivity in a broad velocity range from 0 to 120 km s$^{-1}$ (near the terminal velocity). However, the main beam antenna temperature is usually low ($\sim$1 K). Their line profiles mimic each other with an overall intensity ratio of $\sim$6.

- Both the CO and $^{13}$CO absorption lines are much more sparse than their corresponding emission lines and show discrete velocity components. The CO $J$=1–0 absorption is saturated ($e^{-\tau} \sim 0$) only for a few velocity components. This means that the common assumption of the CO $J$=1–0 emission being optically thick ($\tau$ $\gg$ 1) and beam-filling ($f$ $\simeq$ 1) is often invalid. The $^{13}$CO $J$=1–0 absorption is barely visible except for the saturated CO absorption systems.

- The CO and $^{13}$CO absorption lines sometimes show (multiple) narrow-line components.

- The spectra of the CO $J$=1–0 and $J$=2–1 absorption lines mimic each other with significantly smaller $J$=3–2 absorption, suggesting the excitation temperature is close to $E_{J=1}/k_{\rm B}$ (5.53 K for CO).

- The HCO$^+$ $J$=1–0 absorption lines have near continuous absorption in a broad velocity range from 0 to 120 km s$^{-1}$. The same applies to $c$-${\rm C_3H_2}$ $J_{K_a,K_c}$=$2_{1,2}$–$1_{0,1}$, while the individual features are less prominent in this line due to the poorer velocity resolution.

- The $^{13}$CO and HNC $J$=1–0, and CS $J$=2–1 absorption lines have similar opacity. HNC is more commonly detected than $^{13}$CO in terms of opacity. CS is highly concentrated in one of the velocity components with the largest $^{13}$CO absorption column density.

- There are a few velocity components where the CO emission and HCO$^+$ $J$=1–0 absorption are observed without significant CO absorption. The most prominent case is found near 68 km s$^{-1}$.

These findings will be discussed in the following sections.

### Characteristics of the parent clouds

The types of the parent clouds of individual velocity components were identified in Table [6](#table:velcomp) based on their column density in Tables [\[table:col_co_abs\]](#table:col_co_abs) and [\[table:col_co_em\]](#table:col_co_em) and their appearances in the CO and $^{13}$CO $J$=1–0 channel maps in Appendix [8.1](#sec:channel_map), which includes locations of HII regions and dense clumps.

We classified the molecular clouds based on the following criteria:

- Diffuse clouds have a hydrogen column density $N$(H$_2$) $\lesssim 1 \times 10^{21}$ cm$^{-2}$. They are difficult to visualize in emission line mapping because their excitation temperature is close to the CMB.

- Dark clouds are denser than diffuse clouds and have $N$(H$_2$) $\gtrsim 1 \times 10^{21}$ cm$^{-2}$, though their edges may have less column density. Most of the velocity components identified in this study belong to this group.

- GMCs have large peak brightness due to the heating by nearby/embedded sources or accompanied HII regions and/or ATLASGAL GCSC sources in the neighborhood ($\sim$10 pc). The association with HII regions was studied based on the HII region catalog in Table [11](#table:hrds) of Appendix [8.3](#sec:hrds). Similarly, the association with dense clumps was studied based on the ATLASGAL GCSC source catalog in Table [12](#table:atlasgal) of Appendix [8.4](#sec:atlasgal).

- Globules are isolated small clouds with a discontinuous brightness distribution and sizes up to a few pc when viewed in the channel maps and the position-velocity diagrams. They are much smaller in size than dark clouds and GMCs that extend several tens of parsecs.

The Galactocentric distance ($R_{\rm G}$) was calculated from the center of the velocity range of the component by assuming the distance to the Galactic Center ($R_{\rm 0}$) to be 8.5 kpc and the flat rotation curve at 220 km s$^{-1}$.

The association with the spiral arms and some other features is given based on the identification of spiral arms by (cite: 2016ApJ...823...77R). These arms can be traced in the longitude-velocity ($l$–$v$) diagram (Figure [4](#fig:arm)), and possible association of the individual velocity components was judged based on this information and the apparent angular extent of the surrounding emission features.

+:----:+--------------:+--------------:+:-----------:+:------------------+:----------------+:----:+:---------------------------------------+
|      | Velocity                      |             |                   |                 |      |                                        |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| Comp | $v_{\rm min}$ | $v_{\rm max}$ | $R_{\rm G}$ | Spiral arm?       | Cloud type/     | Case | Note                                   |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| ID   | (km s$^{-1}$)                 | (kpc)       | (near/far)        | location        |      |                                        |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 1    | $-$30.0       | $-$23.0       | 10.87       | interarm          | diffuse cloud   | 3    | no CO emission                         |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 2    | $-$23.0       | $-$17.0       | 10.18       | Outer Arm         | diffuse cloud   | 2    | weak CO emission                       |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 3    | $-$17.0       | $-$6.0        | 9.39        | —                 | —               |      | no absorption/emission                 |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 4    | $-$6.0        | 0.0           | 8.72        | interarm          | diffuse cloud   | 2    | no CO emission                         |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 5    | 0.0           | 7.0           | 8.26        | Per arm?          | diffuse cloud   | 1    |                                        |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 6    | 7.0           | 14.5          | 7.81        | Aql Rift          | dark cloud      | 1    | saturated CO absorption                |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 7    | 14.5          | 20.0          | 7.44        | interarm (far)    | dark cloud      | 1    | saturated CO absorption; shock tracers |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 8    | 20.0          | 23.5          | 7.21        | interarm          | globule edge    | 2    |                                        |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 9    | 23.5          | 26.0          | 7.06        | Sgr arm (near)    | globule edge    | 3    |                                        |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 10   | 26.0          | 30.5          | 6.90        | Sgr arm (near)    | globule edge    | 2    |                                        |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 11   | 30.5          | 34.5          | 6.71        | Sgr arm (near)    | globule edge    | 2    |                                        |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 12   | 34.5          | 40.0          | 6.50        | interarm          | GMC edge        | 2    | ATLASGAL GCSC source                   |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 13   | 40.0          | 47.0          | 6.26        | interarm (far)    | GMC edge        | 3    | ATLASGAL GCSC source                   |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 14   | 47.0          | 51.5          | 6.05        | interarm (far)    | dark cloud edge | 3    |                                        |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 15   | 51.5          | 55.5          | 5.90        | Sgr arm (far)     | dark cloud      | 1    | saturated CO absorption                |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 16   | 55.5          | 60.0          | 5.76        | Sgr arm (far)     | dark cloud      | 1    | saturated CO absorption                |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 17   | 60.0          | 76.0          | 5.45        | interarm (far)    | GMC edge        | 3    | adjacent to HCO$^+$/HCN clump          |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 18   | 76.0          | 81.0          | 5.16        | Scu arm (tangent) | GMC edge        | 2    | ATLASGAL GCSC source                   |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 19   | 81.0          | 88.0          | 5.01        | Scu arm (tangent) | GMC edge        | 2    |                                        |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 20   | 88.0          | 97.0          | 4.82        | Scu arm (tangent) | dark cloud edge | 1    |                                        |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 21   | 97.0          | 102.0         | 4.69        | Scu arm (tangent) | GMC edge        | 3    | ATLASGAL GCSC source                   |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 22   | 102.0         | 110.0         | 4.69        | Scu arm (tangent) | dark cloud edge | 3    |                                        |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 23   | 110.0         | 120.0         | 4.69        | Scu arm (tangent) | dark cloud edge | 3    |                                        |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+
| 24   | 120.0         | 130.0         | 4.69        | —                 | —               |      | no absorption/emission                 |
+------+---------------+---------------+-------------+-------------------+-----------------+------+----------------------------------------+

: Identification of velocity components.

Column densities of CO, $^{13}$CO, HCO$^+$, HNC, C$_2$H, $c$-C$_3$H, and $c$-C$_3$H$_2$ are shown in Tables [\[table:col_co_abs\]](#table:col_co_abs)–[\[table:col_c2h_c3h_c3h2\]](#table:col_c2h_c3h_c3h2) for the individual velocity components. Components 6, 7, 15, and 16 are saturated CO absorbers and may be classified as dark clouds. Among these, Component 7 may be the densest cloud as judged by the excitation temperature of $^{13}$CO. For H$^{13}$CO$^+$, HCO, and H$_2$CO, their column densities are shown in Table [\[table:col_h13co+\_hco_and C\]](#table:col_h13co+_hco_and C) for Components 6, 7, 15, 16, and 17. Column densities of CS, SO, and SiO are shown in Table [\[table:col_cs_so_sio\]](#table:col_cs_so_sio) for Components 5, 6, 7, 15, and 16.

crrDcDDcD & & &\
Comp & $v_{\rm min}$ & $v_{\rm max}$ & & $T_{\rm ex}$ & & & $T_{\rm ex}$ &\
ID & & & (K) & & & (K) &\
1 & $-$30.0 & $-$23.0 &$-$0.04 &$\pm$0.05 & & $-$0.45&$\pm$0.58 & 0.01 &$\pm$0.02 & & 0.12&$\pm$0.17\
2 & $-$23.0 & $-$17.0 &0.11 &$\pm$0.05 &2.27$\pm$10.63 & 1.18&$\pm$0.54 & $-$0.01 &$\pm$0.01 & & $-$0.08&$\pm$0.15\
3 & $-$17.0 & $-$6.0 &$-$0.15 &$\pm$0.07 & & $-$1.59&$\pm$0.72 & 0.04 &$\pm$0.02 & & 0.42&$\pm$0.21\
4 & $-$6.0 & 0.0 &0.01 &$\pm$0.05 & & 0.11&$\pm$0.54 &$-$0.01 &$\pm$0.01 & & $-$0.06&$\pm$0.15\
5 & 0.0 & 7.0 & 2.17 &$\pm$0.05 & 4.30$\pm$0.18 & 38.75&$\pm$0.71 & 0.11&$\pm$0.01 & 2.74$\pm$4.52 & 1.27&$\pm$0.17\
6 & 7.0 & 14.5 & & (393&$\pm$6)& 0.97 &$\pm$0.02 & 3.80$\pm$0.28 & 15.71&$\pm$0.25\
7 & 14.5 & 20.0 & & (865&$\pm$12)& 0.96 &$\pm$0.01 & 6.75$\pm$0.11 & 34.61&$\pm$0.47\
8 & 20.0 & 23.5 &0.96 &$\pm$0.04 & 5.69$\pm$0.22 & 24.98&$\pm$0.81 & 0.04 &$\pm$0.01 & & 0.40 &$\pm$0.12\
9 & 23.5 & 26.0 &0.05 &$\pm$0.03 &4.67$\pm$4.58 & 0.92&$\pm$0.76 & $-$0.00 &$\pm$0.01 & & $-$0.04&$\pm$0.10\
10 & 26.0 & 30.5 &0.34 &$\pm$0.04 &6.00$\pm$0.69 & 9.57&$\pm$1.01 & 0.01 &$\pm$0.01 & & 0.11&$\pm$0.13\
11 & 30.5 & 34.5 &0.80 &$\pm$0.04 &5.28$\pm$0.30 & 18.85&$\pm$1.08 & 0.02 &$\pm$0.01 & & 0.22&$\pm$0.13\
12 & 34.5 & 40.0 &0.04 &$\pm$0.05 &4.75$\pm$7.50 & 0.84&$\pm$1.08 &$-$0.01 &$\pm$0.01 & & $-$0.15&$\pm$0.15\
13 & 40.0 & 47.0 &$-$0.07 &$\pm$0.05 & & $-$0.78&$\pm$0.57 &$-$0.01 &$\pm$0.01 & & $-$0.07&$\pm$0.16\
14 & 47.0 & 51.5 &0.02 &$\pm$0.04 & & 0.17&$\pm$0.57 &$-$0.01 &$\pm$0.01 & & $-$0.12&$\pm$0.13\
15 & 51.5 & 55.5 & & (114&$\pm$4)& 0.30 &$\pm$0.01 & 3.60$\pm$0.72 & 4.58&$\pm$0.17\
16 & 55.5 & 60.0 & & (302&$\pm$6)& 0.61 &$\pm$0.01 & 4.45$\pm$0.26 & 12.09&$\pm$0.24\
17 & 60.0 & 76.0 & 0.04&$\pm$0.08 & & 0.37&$\pm$0.88 &$-$0.03 &$\pm$0.02 & & $-$0.35&$\pm$0.25\
18 & 76.0 & 81.0 & 0.22&$\pm$0.05 &6.98$\pm$1.06 & 7.67&$\pm$1.18 & $-$0.01 &$\pm$0.01 & & $-$0.10&$\pm$0.14\
19 & 81.0 & 88.0 &0.48 &$\pm$0.05 &6.39$\pm$0.60 & 14.71&$\pm$1.82 & $-$0.01 &$\pm$0.01 & & $-$0.15&$\pm$0.16\
20 & 88.0 & 97.0 &2.20 &$\pm$0.06 &4.64$\pm$0.18 & 43.33&$\pm$1.59 & 0.03 &$\pm$0.02 & & 0.32 &$\pm$0.19\
21 & 97.0 & 102.0 &0.00 &$\pm$0.05 & & $-$0.04&$\pm$0.49 & 0.01 &$\pm$0.01 & & 0.07&$\pm$0.14\
22 & 102.0 & 110.0 &$-$0.14 &$\pm$0.06 & & $-$1.52&$\pm$0.61 &$-$0.04 &$\pm$0.02 & & $-$0.41&$\pm$0.18\
23 & 110.0 & 120.0 &$-$0.24 &$\pm$0.07 & & $-$2.61&$\pm$0.67 &$-$0.03 &$\pm$0.02 & & $-$0.36&$\pm$0.20\
24 & 120.0 & 130.0 &$-$0.17 &$\pm$0.07 & & $-$1.78&$\pm$0.68 & 0.01 &$\pm$0.02 & & 0.07&$\pm$0.20\
$\Sigma$ & $-$30.0 & 130.0 & & & & 1827& & 2.94 & & & 68.10 &\

crrDDDDDD & & &\
Comp & $v_{\rm min}$ & $v_{\rm max}$ & & & &\
ID & & & & &\
1 & $-$30.0 & $-$23.0 & 0.13 &$\pm$0.03 & 0.15 &$\pm$0.04 & 0.03&$\pm$0.01 & 0.06&$\pm$0.02\
2 & $-$23.0 & $-$17.0 & 0.30 &$\pm$0.03 & 0.33 &$\pm$0.03 & 0.00&$\pm$0.01 & 0.00&$\pm$0.02\
3 & $-$17.0 & $-$6.0 & 0.01 &$\pm$0.04 & 0.02 &$\pm$0.04 & 0.01&$\pm$0.01 & 0.02&$\pm$0.03\
4 & $-$6.0 & 0.0 & 0.05 &$\pm$0.03 & 0.05 &$\pm$0.03 & $-$0.01&$\pm$0.03 & $-$0.02&$\pm$0.05\
5 & 0.0 & 7.0 & 0.75 &$\pm$0.04 & 0.83 &$\pm$0.04 & 0.12&$\pm$0.03 & 0.21&$\pm$0.05\
6 & 7.0 & 14.5 & 4.80 &$\pm$0.04 & 5.34 &$\pm$0.04 & 0.49&$\pm$0.03 & 0.87&$\pm$0.05\
7 & 14.5 & 20.0 & & (3.49&$\pm$1.18)& 1.11&$\pm$0.03 & 1.97&$\pm$0.06\
8 & 20.0 & 23.5 & 1.01 &$\pm$0.03 & 1.12 &$\pm$0.04 & 0.19&$\pm$0.02 & 0.35&$\pm$0.04\
9 & 23.5 & 26.0 & 0.58 &$\pm$0.02 & 0.64 &$\pm$0.03 & $-$0.01&$\pm$0.02 & $-$0.01&$\pm$0.03\
10 & 26.0 & 30.5 & 1.56 &$\pm$0.04 & 1.73 &$\pm$0.04 & 0.09&$\pm$0.02 & 0.16&$\pm$0.04\
11 & 30.5 & 34.5 & 1.99 &$\pm$0.05 & 2.21 &$\pm$0.06 & 0.15&$\pm$0.02 & 0.28&$\pm$0.04\
12 & 34.5 & 40.0 & 0.44 &$\pm$0.03 & 0.49 &$\pm$0.03 & 0.06&$\pm$0.02 & 0.11&$\pm$0.04\
13 & 40.0 & 47.0 & 0.30 &$\pm$0.04 & 0.33 &$\pm$0.04 & $-$0.04&$\pm$0.03 & $-$0.07&$\pm$0.05\
14 & 47.0 & 51.5 & 0.16 &$\pm$0.03 & 0.18 &$\pm$0.03 & 0.00&$\pm$0.02 & 0.00&$\pm$0.04\
15 & 51.5 & 55.5 & & (3.48&$\pm$1.01)& 0.63&$\pm$0.02 & 1.12&$\pm$0.04\
16 & 55.5 & 60.0 & & (4.58&$\pm$1.08)& 0.81&$\pm$0.03 & 1.45&$\pm$0.05\
17 & 60.0 & 76.0 & 2.68 &$\pm$0.06 & 2.98 &$\pm$0.06 & 0.05&$\pm$0.04 & 0.09&$\pm$0.07\
18 & 76.0 & 81.0 & 1.88 &$\pm$0.04 &2.10 &$\pm$0.05 & 0.32&$\pm$0.02 & 0.57&$\pm$0.04\
19 & 81.0 & 88.0 & 2.00 &$\pm$0.05 & 2.22 &$\pm$0.05 & 0.26&$\pm$0.03 & 0.47&$\pm$0.05\
20 & 88.0 & 97.0 & 3.17 &$\pm$0.05 &3.52 &$\pm$0.06 & 0.16&$\pm$0.03 & 0.28&$\pm$0.06\
21 & 97.0 & 102.0 & 0.46 &$\pm$0.03 & 0.51 &$\pm$0.03 & $-$0.03&$\pm$0.02 & $-$0.06&$\pm$0.04\
22 & 102.0 & 110.0 & 0.28 &$\pm$0.04 & 0.31 &$\pm$0.04 & $-$0.03&$\pm$0.03 & $-$0.05&$\pm$0.05\
23 & 110.0 & 120.0 & 0.09 &$\pm$0.04 & 0.10 &$\pm$0.04 & $-$0.10&$\pm$0.03 & $-$0.17&$\pm$0.06\
24 & 120.0 & 130.0 & $-$0.06 &$\pm$0.04 & $-$0.07 &$\pm$0.04 & $-$0.06&$\pm$0.03 & $-$0.10&$\pm$0.06\
$\Sigma$ & $-$30.0 & 130.0 & & & 36.67 & & 4.22 & & 7.53 &\

crrDDDDDD & & & &\
Comp & $v_{\rm min}$ & $v_{\rm max}$ & & & & & &\
ID & & & & & & &\
1 & $-$30.0 & $-$23.0 & $-$0.05&$\pm$0.04 & $-$7.71&$\pm$6.00 & $-$0.05&$\pm$0.02 & $-$0.51&$\pm$0.25 & 0.02&$\pm$0.04 & 0.09&$\pm$0.20\
2 & $-$23.0 & $-$17.0 & $-$0.03&$\pm$0.04 & $-$3.68&$\pm$5.61 & $-$0.04&$\pm$0.02 & $-$0.45&$\pm$0.25 & 0.12&$\pm$0.02 & 0.55&$\pm$0.11\
3 & $-$17.0 & $-$6.0 & $-$0.09&$\pm$0.05 & $-$12.76&$\pm$7.65 & $-$0.02&$\pm$0.03 & $-$0.17&$\pm$0.32 & $-$0.01&$\pm$0.03 & $-$0.07&$\pm$0.13\
4 & $-$6.0 & 0.0 & $-$0.06&$\pm$0.04 & $-$8.72&$\pm$5.61 & $-$0.03&$\pm$0.02 & $-$0.32&$\pm$0.25 & 0.02&$\pm$0.02 & 0.07&$\pm$0.11\
5 & 0.0 & 7.0 & 0.19&$\pm$0.05 & 27.10&$\pm$6.36 & $-$0.02&$\pm$0.02 & $-$0.17&$\pm$0.25 & 0.28&$\pm$0.02 & 1.25&$\pm$0.11\
6 & 7.0 & 14.5 & 0.31&$\pm$0.05 & 43.99&$\pm$6.36 & $-$0.01&$\pm$0.03 & $-$0.09&$\pm$0.27 & 0.38&$\pm$0.02 & 1.72&$\pm$0.11\
7 & 14.5 & 20.0 & 0.58&$\pm$0.04 & 81.36&$\pm$5.19 & 0.08&$\pm$0.02 & 0.85&$\pm$0.21 & 0.66&$\pm$0.02 & 2.99&$\pm$0.09\
8 & 20.0 & 23.5 & 0.06&$\pm$0.03 & 4.05&$\pm$2.11 & 0.02&$\pm$0.02 & 0.25&$\pm$0.21 & 0.07&$\pm$0.02 & 0.31&$\pm$0.08\
9 & 23.5 & 26.0 & 0.11&$\pm$0.03 & 7.89&$\pm$1.83 & 0.01&$\pm$0.01 & 0.09&$\pm$0.12 & 0.10&$\pm$0.02 & 0.46&$\pm$0.08\
10 & 26.0 & 30.5 & 0.37&$\pm$0.04 & 26.07&$\pm$2.59 & 0.04&$\pm$0.02 & 0.36&$\pm$0.21 & 0.13&$\pm$0.02 & 0.58&$\pm$0.08\
11 & 30.5 & 34.5 & 0.21&$\pm$0.03 & 15.10&$\pm$2.36 & 0.03&$\pm$0.02 & 0.27&$\pm$0.17 & 0.18&$\pm$0.02 & 0.82&$\pm$0.09\
12 & 34.5 & 40.0 & 0.21&$\pm$0.04 & 14.46&$\pm$2.59 & 0.00&$\pm$0.02 & 0.00&$\pm$0.25 & 0.11&$\pm$0.02 & 0.50&$\pm$0.09\
13 & 40.0 & 47.0 & 0.23&$\pm$0.04 & 16.44&$\pm$2.99 & 0.05&$\pm$0.02 & 0.46&$\pm$0.25 & 0.04&$\pm$0.02 & 0.18&$\pm$0.11\
14 & 47.0 & 51.5 & 0.08&$\pm$0.04 & 5.59&$\pm$2.59 & 0.00&$\pm$0.02 & 0.04&$\pm$0.21 & 0.03&$\pm$0.02 & 0.15&$\pm$0.09\
15 & 51.5 & 55.5 & 0.40&$\pm$0.03 & 28.06&$\pm$2.11 & 0.05&$\pm$0.02 & 0.55&$\pm$0.21 & 0.17&$\pm$0.02 & 0.76&$\pm$0.08\
16 & 55.5 & 60.0 & 0.59&$\pm$0.04 & 41.68&$\pm$2.59 & 0.04&$\pm$0.02 & 0.45&$\pm$0.17 & 0.27&$\pm$0.02 & 1.22&$\pm$0.09\
17 & 60.0 & 76.0 & 0.15&$\pm$0.07 & 10.35&$\pm$4.60 & $-$0.05&$\pm$0.04 & $-$0.55&$\pm$0.39 & 0.06&$\pm$0.04 & 0.28&$\pm$0.16\
18 & 76.0 & 81.0 & 0.27&$\pm$0.04 & 19.15&$\pm$2.59 & $-$0.05&$\pm$0.02 & $-$0.55&$\pm$0.25 & 0.19&$\pm$0.02 & 0.83&$\pm$0.09\
19 & 81.0 & 88.0 & 0.28&$\pm$0.04 & 19.97&$\pm$2.99 & 0.00&$\pm$0.02 & $-$0.01&$\pm$0.25 & 0.22&$\pm$0.02 & 0.98&$\pm$0.11\
20 & 88.0 & 97.0 & 0.43&$\pm$0.05 & 30.01&$\pm$3.50 & 0.03&$\pm$0.03 & 0.34&$\pm$0.27 & 0.27&$\pm$0.03 & 1.23&$\pm$0.12\
21 & 97.0 & 102.0 & 0.03&$\pm$0.04 & 2.13&$\pm$2.59 & 0.02&$\pm$0.02 & 0.19&$\pm$0.25 & 0.00&$\pm$0.02 & 0.01&$\pm$0.09\
22 & 102.0 & 110.0 & 0.01&$\pm$0.05 & 0.38&$\pm$3.34 &$-$0.03&$\pm$0.03 & $-$0.30&$\pm$0.27 & 0.06&$\pm$0.03 & 0.27&$\pm$0.12\
23 & 110.0 & 120.0 & $-$0.02&$\pm$0.05 & $-$1.44&$\pm$3.50 & 0.00&$\pm$0.03 & 0.01&$\pm$0.30 & $-$0.02&$\pm$0.03 & $-$0.09&$\pm$0.13\
24 & 120.0 & 130.0 & 0.10&$\pm$0.05 & 7.17&$\pm$3.66 & $-$0.05&$\pm$0.03 & $-$0.56&$\pm$0.30 & $-$0.02&$\pm$0.03 & $-$0.09&$\pm$0.12\
$\Sigma$ & $-$30.0 & 130.0 & 4.36 & & 366.64 & & 0.02 & & 0.18 & & 3.34 & & 15.02\

crrDDDDDD & & & &\
Comp & $v_{\rm min}$ & $v_{\rm max}$ & & & & & &\
ID & & & & & & &\
6 & 7.0 & 14.5 & 0.02&$\pm$0.02 & 0.03&$\pm$0.03 & 0.01&$\pm$0.03 & 0.41&$\pm$1.06 & 0.03&$\pm$0.04 & 1.51&$\pm$1.93\
7 & 14.5 & 20.0 & 0.06&$\pm$0.02 & 0.07&$\pm$0.02 & 0.05&$\pm$0.02 & 1.85&$\pm$0.90 & 0.10&$\pm$0.04 & 4.52&$\pm$1.70\
15 & 51.5 & 55.5 & 0.06&$\pm$0.02 & 0.07&$\pm$0.02 & 0.04&$\pm$0.02 & 1.73&$\pm$0.62 & $-$0.02&$\pm$0.03 & $-$0.80&$\pm$1.42\
16 & 55.5 & 60.0 & 0.08&$\pm$0.02 & 0.09&$\pm$0.02 & 0.05&$\pm$0.02 & 1.92&$\pm$0.65 & 0.05&$\pm$0.03 & 2.47&$\pm$1.54\
17 & 60.0 & 76.0 & $-$0.00&$\pm$0.03 & $-$0.00&$\pm$0.04 & $-$0.02&$\pm$0.03 & $-$0.65&$\pm$1.23 & $-$0.08&$\pm$0.06 & $-$3.61&$\pm$2.85\

crrDDDDDD & & & &\
Comp & $v_{\rm min}$ & $v_{\rm max}$ & & & & & &\
ID & & & & & & &\
5 & 0.0 & 7.0 & 0.22&$\pm$0.02 & 1.80&$\pm$0.17 & $-$0.04&$\pm$0.02 & $-$1.05&$\pm$0.58 & $-$0.00&$\pm$0.02 & $-$0.01&$\pm$0.07\
6 & 7.0 & 14.5 & 0.22&$\pm$0.02 & 1.81&$\pm$0.17 & $-$0.00&$\pm$0.02 & $-$0.13&$\pm$0.60 & 0.04&$\pm$0.02 & 0.15&$\pm$0.08\
7 & 14.5 & 20.0 & 0.97&$\pm$0.02 & 7.85&$\pm$0.15 & 0.16&$\pm$0.02 & 4.54&$\pm$0.52 & 0.11&$\pm$0.02 & 0.36&$\pm$0.06\
15 & 51.5 & 55.5 & 0.02&$\pm$0.02 & 0.20&$\pm$0.13 & 0.02&$\pm$0.02 & 0.66&$\pm$0.44 & 0.01&$\pm$0.02 & 0.05&$\pm$0.06\
16 & 55.5 & 60.0 & 0.11&$\pm$0.02 & 0.87&$\pm$0.13 & 0.00&$\pm$0.02 & 0.12&$\pm$0.47 & 0.01&$\pm$0.02 & 0.04&$\pm$0.06\

The H$_2$ column density was also deduced through CO and $^{13}$CO $J$=1–0 emission lines, as shown in Table [\[table:col_co_em\]](#table:col_co_em). The standard Galactic CO-to-H$_2$ conversion factor (cite: 2013ARA&A..51..207B) was used for the calculation from the CO integrated intensity to $N$(H$_2$). We also obtained the $^{13}$CO column density with its $J$=1–0 emission in a manner described in Appendix [9](#sec:reliability). The H$_2$ column density was then deduced by using the $^{13}$CO/H$_2$ abundance ratio ($X$($^{13}$CO) = $2 \times 10^{-6}$) as a canonical value for Galactic disk clouds (cite: 2008ApJ...679..481P).

crrcDDDD & & &\
Comp & $v_{\rm min}$ & $v_{\rm max}$ & $T_{\rm peak}$ & & & &\
ID & & (K) & & & &\
1 &$-$30.0&$-$23.0&2.93 & 0.45 &$\pm$0.83 & 1 &$\pm$2 & 0.12 &$\pm$0.19 & 0.57 &$\pm$0.89\
2 &$-$23.0&$-$17.0&2.83 & 0.22 &$\pm$0.77 & 0 &$\pm$2 & 0.26 &$\pm$0.17 & 1.22 &$\pm$0.83\
3 &$-$17.0&$-$6.0&2.81 &$-$1.04&$\pm$1.04 &$-$2&$\pm$2&$-$0.17&$\pm$0.24 &$-$0.80&$\pm$1.12\
4 &$-$6.0& 0.0 & 2.82 &$-$0.53&$\pm$0.77 &$-$1&$\pm$2 & 0.08 &$\pm$0.17 & 0.38 &$\pm$0.83\
5 & 0.0 & 7.0 & 4.15 & 1.85 &$\pm$0.83 & 4 &$\pm$2 & 0.21 &$\pm$0.17 & 0.95 &$\pm$0.79\
6 & 7.0 & 14.5 & 8.50 & 22.60 &$\pm$0.86 & 45 &$\pm$2 & 0.21 &$\pm$0.19 & 1.05 &$\pm$0.96\
7 & 14.5 & 20.0 & 6.43 & 12.26 &$\pm$0.73 & 25 &$\pm$1 & 1.61 &$\pm$0.17 & 7.46 &$\pm$0.77\
8 & 20.0 & 23.5 & 3.90 & 2.13 &$\pm$0.59 & 4 &$\pm$1 & 0.40 &$\pm$0.13 & 1.80 &$\pm$0.60\
9 & 23.5 & 26.0 & 3.34 & 0.92 &$\pm$0.50 & 2 &$\pm$1 & 0.17 &$\pm$0.11 & 0.79 &$\pm$0.52\
10 & 26.0 & 30.5 & 3.95 & 2.97 &$\pm$0.66 & 6 &$\pm$1 & 0.41 &$\pm$0.15 & 1.87 &$\pm$0.68\
11 & 30.5 & 34.5 & 3.15 & 0.79 &$\pm$0.63 & 2 &$\pm$1 & 0.43 &$\pm$0.14 & 2.00&$\pm$0.66\
12 & 34.5 & 40.0 & 2.65 &$-$0.93&$\pm$0.73 &$-$2&$\pm$1 & 0.38 &$\pm$0.17 & 1.82 &$\pm$0.81\
13 & 40.0 & 47.0 & 3.28 & 1.01 &$\pm$0.83 & 2 &$\pm$2 & 0.77 &$\pm$0.19 & 3.55 &$\pm$0.87\
14 & 47.0 & 51.5 & 2.67 &$-$0.77&$\pm$0.66 &$-$2&$\pm$1 & 0.40 &$\pm$0.15 & 1.94 &$\pm$0.73\
15 & 51.5 & 55.5 & 6.10 & 6.51 &$\pm$0.63 & 13 &$\pm$1 & 1.22 &$\pm$0.14 & 5.58 &$\pm$0.65\
16 & 55.5 & 60.0 & 7.60 & 10.48 &$\pm$0.66 & 21 &$\pm$1 & 1.48 &$\pm$0.15 & 7.05 &$\pm$0.72\
17 & 60.0 & 76.0 & 4.48 & 10.34 &$\pm$1.25 & 21 &$\pm$3 & 2.67 &$\pm$0.28 & 12.01 &$\pm$1.28\
18 & 76.0 & 81.0 & 3.92 & 1.93 &$\pm$0.70 & 4 &$\pm$1 & 0.52 &$\pm$0.16 & 2.35 &$\pm$0.72\
19 & 81.0 & 88.0 & 3.75 & 5.80 &$\pm$0.83 & 12 &$\pm$2 & 1.53 &$\pm$0.19 & 6.96 &$\pm$0.85\
20 & 88.0 & 97.0 & 6.10 & 16.02 &$\pm$0.94 & 32 &$\pm$2 & 2.37 &$\pm$0.21 & 10.87 &$\pm$0.98\
21 & 97.0 &102.0 & 3.83 & 4.30 &$\pm$0.70 & 9 &$\pm$1 & 0.80 &$\pm$0.16 & 3.64 &$\pm$0.72\
22 &102.0 &110.0 & 3.84 & 5.42 &$\pm$0.89 & 11 &$\pm$2 & 1.17 &$\pm$0.20 & 5.29 &$\pm$0.91\
23 &110.0 &120.0 & 3.05 & 0.31 &$\pm$0.99 & 1 &$\pm$2 & 0.22 &$\pm$0.22 & 1.01 &$\pm$1.05\
24 &120.0 &130.0 & 2.83 &$-$0.61&$\pm$0.99 &$-$1&$\pm$2 & 0.27 &$\pm$0.22 & 1.26 &$\pm$1.07\
$\Sigma$ & $-$30.0 & 130.0 & & 102.41 & & 205 & & 17.52 & & 80.62 &\

## Excitation analysis and physical properties

### Excitation temperature through multi-transition study of CO absorption

An excitation analysis can be done if some species are detected in several transitions. Under the Rayleigh-Jeans approximation ($h\nu \ll k_{\rm B}T$), Equation [\[eq:n_tot\]](#eq:n_tot) can be rewritten as, $$\begin{equation}
\label{eq:equation-3}
\log \left(\frac{3 k_{\rm B} \int \tau dv}{8 \pi^3 \nu \mu^2 S_{\rm ul}}\right)=\log \left(\frac{N_{\rm tot}}{Q\left(T_{\rm ex}\right) T_{\rm ex}}\right)-\frac{E_{\rm l} \log (e)}{k_{\rm B} T_{\rm ex}}.
\end{equation}$$

The excitation temperature for each component can be calculated as an inverse of the slope of the rotation diagram.

However, the excitation temperature is quite small for the current absorption study and the assumption for the Rayleigh-Jeans approximation ($h\nu \ll k_{\rm B}T_{\rm ex}$) is not met. We thus need to deduce $T_{\rm ex}$ from $\tau_{1-0}$ and $\tau_{2-1}$ without using this approximation.

For $J$=1–0 and $J$=2–1 absorption, Equation [\[eq:n_tot\]](#eq:n_tot) can be rewritten as, $$\begin{equation}
\label{eq:n_tot_1}
N = \frac{3hQ(T_{\rm ex})}{8\pi^3\mu^2S_{1,0}} \frac{\exp(\frac{E_{J=0}}{k_{\rm B} T_{\rm ex}})}{[1-\exp(\frac{-h\nu_{1-0}}{k_{\rm B}T_{\rm ex}})]} \int\tau_{1-0} dv, 
\end{equation}$$ $$\begin{equation}
\label{eq:n_tot_2}
N = \frac{3hQ(T_{\rm ex})}{8\pi^3\mu^2S_{2,1}} \frac{\exp(\frac{E_{J=1}}{k_{\rm B} T_{\rm ex}})}{[1-\exp(\frac{-h\nu_{2-1}}{k_{\rm B}T_{\rm ex}})]} \int\tau_{2-1} dv. 
\end{equation}$$ Under the LTE condition, $T_{\rm ex}$ remains constant for all transitions, and thus $T_{\rm ex}$ shall meet $$\begin{equation}
\label{eq:tex_deduction1}
\frac{1}{S_{1,0}} \frac{\exp(\frac{E_{J=0}}{k_{\rm B} T_{\rm ex}})} {[1-\exp(\frac{-h\nu_{1-0}}{k_{\rm B}T_{\rm ex}})]} \int\tau_{1-0} dv = 
\frac{1}{S_{2,1}} \frac{\exp(\frac{E_{J=1}}{k_{\rm B} T_{\rm ex}})} {[1-\exp(\frac{-h\nu_{2-1}}{k_{\rm B}T_{\rm ex}})]} \int\tau_{2-1} dv. 
\end{equation}$$ Here, $E_{J=0}/k_{\rm B}$ = 0 K, $E_{J=1}/k_{\rm B}$ = 5.53 K (CO) or 5.29 K ($^{13}$CO), $h\nu_{1-0}$ = $E_{J=1}$, $\nu_{2-1}$ $\simeq$ 2$\nu_{1-0}$, and $S_{2,1}$ $\simeq$ $2S_{1,0}$, and thus, $$\begin{equation}
\label{eq:tex_deduction2}
\frac{\int\tau_{2-1} dv}{ \int\tau_{1-0} dv} = 
\frac{2\exp(\frac{-E_{J=1}}{k_{\rm B} T_{\rm ex}})[1-\exp(\frac{-2E_{J=1}}{k_{\rm B}T_{\rm ex}})]}{[1-\exp(\frac{-E_{J=1}}{k_{\rm B}T_{\rm ex}})]} = 
2\exp\left(\frac{-E_{J=1}}{k_{\rm B} T_{\rm ex}}\right)\left[1+\exp\left(\frac{-E_{J=1}}{k_{\rm B}T_{\rm ex}}\right)\right].
\end{equation}$$ By defining $x \equiv \exp\left(\frac{-E_{J=1}}{k_{\rm B} T_{\rm ex}}\right)$, the formula for the solution of the quadratic equation gives, $$\begin{equation}
\label{eq:tex_deduction3}
x = -\frac{1}{2} \pm \frac{1}{2}\sqrt{2\frac{\int\tau_{2-1} dv}{\int\tau_{1-0} dv}+ 1}. 
\end{equation}$$ Since $x$ shall be positive, we finally get the analytical solution of $T_{\rm ex}$ as, $$\begin{equation}
\label{eq:tex_deduction4}
T_{\rm ex} = -\frac{E_{J=1}}{k_{\rm B}} \left[\ln\left(-\frac{1}{2} + \frac{1}{2}\sqrt{2\frac{\int\tau_{2-1} dv}{\int\tau_{1-0} dv}+ 1}\right)\right]^{-1}.  
\end{equation}$$ The obtained excitation temperatures for CO and its rarer isotopologue were listed in Table [\[table:col_co_abs\]](#table:col_co_abs).

### Validity of CO excitation temperature estimated from CO main beam antenna temperature

The alternative used for the estimation of the CO excitation temperature is the CO brightness temperature since both will agree if the emission is optically thick ($\tau \gg 1$) and the filling factor ($f$) is close to unity. To check the validity of this method toward general Galactic disk clouds, the CO excitation temperatures obtained through the excitation analysis of the absorption lines were compared with the CO brightness temperatures. The CO brightness temperature toward the QSO was estimated from the baseline-subtracted profile by adding the 2.73 K cosmic background and the QSO continuum diluted by the single-dish beam (0.25 K). Figure [5](#fig:tex_tex) shows the correlation plot of these CO excitation temperatures taken from Tables [\[table:col_co_abs\]](#table:col_co_abs) and [\[table:col_co_em\]](#table:col_co_em).

There is a trend that the CO excitation temperatures obtained through the excitation analysis of the absorption lines tend to be higher than those estimated from the CO brightness temperatures by assuming the optically thick and beam-filling CO emission. The opacity explains this discrepancy because the excitation analysis of the CO absorption lines can only be done when the lines are not saturated ($\tau \lesssim 1$). Given that nearly half of the molecular gas mass along this line of sight is attributed to the velocity components not fully saturated in the CO absorption (Table [\[table:col_co_em\]](#table:col_co_em)), nearly half of the Galactic molecular gas mass does not satisfy the assumption of the optically thick and beam-filling CO emission and their excitation temperature is underestimated.

### Single-dish emission/absorption study of HCO$^+$, HCN, HNC and C$_2$H

The obtained excitation temperature for CO or its rarer isotopologue was less than 6 K in most cases, as described in the previous subsection. The excitation temperature for molecules with larger dipole moments shall be much less than this value and is close to that of the cosmic microwave background. To test the validity of the above assumption, the emission and absorption studies of HCO$^+$, HCN, HNC, and C$_2$H lines were done with the NRO 45 m telescope.

The line profiles obtained toward the QSO with the NRO 45 m telescope are shown in Figure [6](#fig:45m_abs). The subtracted continuum level of the QSO was diluted to $\sim$0.25 K due to the relatively large beam of the telescope. No significant emission lines were detected in the QSO direction for the four molecular species of HCO$^+$, HCN, HNC, and C$_2$H in the QSO direction.

This suggests that these species’ excitation temperatures are very low.

The four beams of the FOREST receiver separated by $50 ''$ (1.2 pc at 5 kpc) in RA and DEC directions provided us with three additional data sets as a bonus. The analysis of these emission-line data from adjacent areas will be presented in Appendix [8.2](#sec:emission_line_ratio).

## Total amount of molecular gas along the line of sight

We estimated the total molecular gas column density toward this line of sight using several different means. Here, we verify the validity of these estimations.

- Visual extinction – $A_{\rm V}$ = 78.59 mag was estimated by (cite: yoshimura2020) from the all-sky $A_{\rm V}$ map taken with *Planck* (cite: 2014A&A...571A..11P). With the standard gas-to-extinction ratio ($N$(H)+2$N$(H$_2$))/$A_{\rm V}$ = $2 \times 10^{21}$ cm$^{-2}$ mag$^{-1}$ (cite: 2017MNRAS.471.3494Z) and by introducing the molecular mass fraction $f_{\rm mol}$ $\equiv$ 2$N$(H$_2$)/($N$(H)+2$N$(H$_2$)), this reads $N$(H$_2$) $\sim 8 \times 10^{22}$ $f_{\rm mol}$ cm$^{-2}$.

- The CO $J$=1–0 integrated intensity – $N$(H$_2$) in the corresponding column of Table [\[table:col_co_em\]](#table:col_co_em) was estimated from $\int T_{\rm mb}({\rm CO}) dv$ and the standard Galactic CO-to-H$_2$ conversion factor (cite: 2013ARA&A..51..207B). The observed values is $N$(H$_2$) $\sim 2 \times 10^{22}$ cm$^{-2}$.

- The optically thin LTE $^{13}$CO $J$=1–0 emission – $N$(H$_2$) in the corresponding column of Table [\[table:col_co_em\]](#table:col_co_em) was estimated by assuming the LTE conditions, optically thin $^{13}$CO emission, the $^{13}$CO excitation temperature equal to the CO peak brightness temperature, and the canonical $^{13}$CO abundance as described in detail in Appendix [9](#sec:reliability). This yields $N$(H$_2$) $\sim 0.8 \times 10^{22}$ cm$^{-2}$ with large uncertainty.

- The CO absorption – The total CO column density in Table [\[table:col_co_abs\]](#table:col_co_abs) can be converted to $N$(H$_2$) by assuming the CO/H$_2$ abundance ratio (cite: 2008ApJ...679..481P). The extracted value of $N$(H$_2$) = $1.8 \times$ $10^{21}$ cm$^{-2}$ is about one order of magnitude smaller than the others. The total $^{13}$CO column density in Table [\[table:col_co_abs\]](#table:col_co_abs) and the canonical $X$($^{13}$CO) = $2 \times 10^{-6}$ also yields small value ($N$(H$_2$) = $3.4 \times 10^{21}$ cm$^{-2}$).

- The HCO$^+$ column density – The total HCO$^+$ column density in Table [\[table:col_co_abs\]](#table:col_co_abs) can be converted to $N$(H$_2$) by assuming the universal HCO$^+$ abundance (cite: 2023ApJ...943..172L). $N$(HCO$^+$) = $5.3 \times 10^{13}$ cm$^{-2}$ yields $N$(H$_2$) $\sim 2 \times 10^{22}$ cm$^{-2}$

- The total $c$-C$_3$H$_2$ column density – The total $c$-C$_3$H$_2$ column density in Table [\[table:col_c2h_c3h_c3h2\]](#table:col_c2h_c3h_c3h2) can be converted to $N$(H$_2$) by assuming the universal $c$-C$_3$H$_2$ abundance (cite: 2012ApJ...753L..28L). $N$($c$-C$_3$H$_2$) = $1.5 \times 10^{13}$ cm$^{-2}$ yields $N$(H$_2$) $\sim 0.6 \times 10^{22}$ cm$^{-2}$.

All these estimations of total molecular column density are in reasonable agreement with $N$(H$_2$) $\sim$ (0.6–2) $\times 10^{22}$ cm$^{-2}$ except the ones estimated from $A_{\rm V}$ and CO absorption. The deviation of the first one may be attributed at least in part to the molecular fraction, which is $\sim$0.5 near the solar circle and even smaller out of the Galactic plane (cite: 2016ApJ...823...76K; 2016PASJ...68...63S). The extremely low $N$(H$_2$) obtained through the conversion from the CO absorption column density to $N$(H$_2$) may be due to the ubiquity of the “CO-poor” molecular gas due to the differential photo-dissociation. We will touch on this in Section [3.6.4](#sec:co_hco+).

## Identification of velocity substructures

### Multiple-Gaussian line fit of CO absorption

To understand the internal motion of velocity components and to resolve the velocity substructures, simultaneous multiple-Gaussian fitting was done with the CO $J$=1–0 and $J$=2–1 absorption profiles by assuming the same center velocity ($v_{\rm c}$) and half velocity width at half maximum ($\Delta v_{1/2}$) to both transitions. For those velocity components with saturated CO absorption, the $^{13}$CO $J$=1–0 and $J$=2–1 absorption profiles were used instead. The fitting results are summarized in Figures [7](#fig:gaussfit12)–[9](#fig:gaussfit13) and Tables [\[table:gaussfit12\]](#table:gaussfit12) and [\[table:gaussfit13\]](#table:gaussfit13). The corresponding CO emission line profiles were also shown. The overall fitting was quite satisfactory, and the corresponding reduced $\chi^2$ ranged from 0.54 to 1.17. Although there are some hints of even narrower line components, the limited signal-to-noise ratio prevented us from further identification. More sensitive observations are needed to pursue this possibility further.

cccDDDDcc Sub-comp & & $\Delta v_{1/2}$ & & & & & $n$(H$_2$) & $X$(CO)/($dv/dr$)\
ID & & (km s$^{-1}$) & & & & & & & (cm$^{-3}$) & ($\rm (km~s^{-1}~pc^{-1})^{-1}$)\
2-1 & $-$19.37 & 0.25 & 0.17&$\pm$0.02 & 0.07&$\pm$0.02 & 3.07&$\pm$1.50 & 1.11&$\pm$0.12 & $3.1 \times 10^1$ & $2.3 \times 10^{-6}$\
4-1 & $-$0.71 & 0.39 & 0.11&$\pm$0.01 & 0.07&$\pm$0.01 & 4.15&$\pm$1.04 & 1.53&$\pm$0.19 & $1.4 \times 10^2$ & $4.8 \times 10^{-7}$\
4-2 & 1.32 & 0.30 & 0.10&$\pm$0.02 & 0.05&$\pm$0.02 & 3.29&$\pm$2.38 & 0.86&$\pm$0.20 & $5.4 \times 10^1$ & $8.3 \times 10^{-7}$\
5-1 & 4.93 & 0.14 & 0.65&$\pm$0.11 & 1.00&$\pm$0.11 & 8.22&$\pm$2.40 &9.04&$\pm$1.58 & $3.4 \times 10^2$ & $2.6 \times 10^{-6}$\
5-2 & 5.12 & 0.49 & 0.65&$\pm$0.14 & 0.70&$\pm$0.07 & 5.88&$\pm$1.03 &18.42&$\pm$4.12 & $2.1 \times 10^2$ & $2.7 \times 10^{-6}$\
5-3 & 5.13 & 1.00 & 0.55&$\pm$0.12 & 0.24&$\pm$0.07 & 3.24&$\pm$1.55 &15.02&$\pm$3.36 & $3.8 \times 10^1$ & $6.4 \times 10^{-6}$\
6-1 & 8.27 & 0.29 & 0.74&$\pm$0.04 & 0.62&$\pm$0.03 & 4.83&$\pm$0.42 & 9.58&$\pm$0.49 & $1.4 \times 10^2$ & $3.7 \times 10^{-6}$\
6-2 & 9.52 & 0.95 & 0.65&$\pm$0.02 & 0.45&$\pm$0.01 & 4.25&$\pm$0.16 &23.20&$\pm$0.65 & $1.1 \times 10^2$ & $3.6 \times 10^{-6}$\
6-3 & 9.83 & 0.12 & 0.66&$\pm$0.06 & 0.73&$\pm$0.08 & 6.00&$\pm$1.56 & 4.66&$\pm$0.41 & $2.2 \times 10^2$ & $2.8 \times 10^{-6}$\
8-1 & 22.12 & 0.20 & 1.18&$\pm$0.05 & 1.13&$\pm$0.05 & 5.32&$\pm$0.51 &11.79&$\pm$0.53 & $1.4 \times 10^2$ & $6.7 \times 10^{-6}$\
8-2 & 22.68 & 0.27 & 0.91&$\pm$0.03 & 0.98&$\pm$0.04 & 5.85&$\pm$0.32 &13.35&$\pm$0.49 & $1.9 \times 10^2$ & $4.4 \times 10^{-6}$\
10-1 & 28.31 & 0.29 & 0.11&$\pm$0.02 & 0.08&$\pm$0.02 & 4.44&$\pm$1.49 & 1.20&$\pm$0.19 & $1.6 \times 10^2$ & $4.3 \times 10^{-7}$\
10-2 & 29.33 & 0.41 & 0.32&$\pm$0.02 & 0.32&$\pm$0.02 & 5.45&$\pm$0.32 & 6.60&$\pm$0.31 & $2.2 \times 10^2$ & $1.2 \times 10^{-6}$\
11-1 & 32.59 & 0.30 & 0.97&$\pm$0.03 & 1.03&$\pm$0.04 & 5.75&$\pm$0.29 &16.21&$\pm$0.56 & $1.8 \times 10^2$ & $4.8 \times 10^{-6}$\
11-2 & 33.09 & 0.20 & 0.44&$\pm$0.05 & 0.40&$\pm$0.06 & 5.16&$\pm$1.41 & 4.48&$\pm$0.54 & $1.9 \times 10^2$ & $1.8 \times 10^{-6}$\
12-1 & 36.74 & 0.51 & 0.08&$\pm$0.01 & 0.06&$\pm$0.01 & 4.42&$\pm$1.05 & 1.78&$\pm$0.27 & $1.6 \times 10^2$ & $3.1 \times 10^{-7}$\
14-1 & 51.50 & 0.28 & 0.16&$\pm$0.02 & 0.07&$\pm$0.01 & 3.35&$\pm$1.26 & 1.28&$\pm$0.13 & $5.7 \times 10^1$ & $1.3 \times 10^{-6}$\
15-1 & 53.26 & 0.29 & 1.82&$\pm$0.06 & 1.64&$\pm$0.05 & 5.08&$\pm$0.26 &25.42&$\pm$0.81 & $9.6 \times 10^1$ & $1.4 \times 10^{-5}$\
18-1 & 79.50 & 1.18 & 0.09&$\pm$0.01 & 0.12&$\pm$0.01 & 6.96&$\pm$0.28 & 7.81&$\pm$0.61 & $3.7 \times 10^2$ & $2.7 \times 10^{-7}$\
19-1 & 84.09 & 0.37 & 0.33&$\pm$0.02 & 0.53&$\pm$0.02 & 8.73&$\pm$0.32 &12.98&$\pm$0.65 & $4.3 \times 10^2$ & $1.1 \times 10^{-6}$\
20-1 & 92.24 & 0.24 & 0.19&$\pm$0.03 & 0.19&$\pm$0.02 & 5.50&$\pm$1.35 & 2.38&$\pm$0.34 & $2.4 \times 10^2$ & $6.4 \times 10^{-7}$\
20-2 & 93.12 & 0.59 & 0.70&$\pm$0.02 & 0.50&$\pm$0.33 & 4.32&$\pm$3.00 &17.71&$\pm$0.61 & $1.1 \times 10^2$ & $3.9 \times 10^{-6}$\
20-3 & 93.98 & 0.24 & 0.74&$\pm$0.04 & 0.61&$\pm$0.04 & 4.81&$\pm$0.61 & 7.63&$\pm$0.46 & $1.4 \times 10^2$ & $3.7 \times 10^{-6}$\
20-4 & 94.45 & 0.93 & 0.30&$\pm$0.00 & 0.30&$\pm$0.00 & 5.50&$\pm$0.07 &14.85&$\pm$0.07 & $2.3 \times 10^2$ & $1.1 \times 10^{-6}$\
21-1 & 100.90 & 0.18 & 0.12&$\pm$0.02 & 0.10&$\pm$0.02 & 4.98&$\pm$2.44 & 0.95&$\pm$0.18 & $2.1 \times 10^2$ & $4.2 \times 10^{-7}$\

cccDDDDcc Sub-comp & $v_{\rm c}$ & $\Delta v_{1/2}$ & & & & & $n$(H$_2$) & $X$($^{13}$CO)/($dv/dr$)\
ID & (km s$^{-1}$) & (km s$^{-1}$) & & & & & & & (cm$^{-3}$) & ($\rm (km~s^{-1}~pc^{-1})^{-1}$)\
6-4 & 10.49 & 0.11 & 0.39&$\pm$0.02 & 0.31&$\pm$0.03 & 4.45&$\pm$0.47 & 1.88&$\pm$0.12 & $1.3 \times 10^2$ & $2.1 \times 10^{-6}$\
6-5 & 10.81 & 0.18 & 0.35&$\pm$0.01 & 0.20&$\pm$0.02 & 3.63&$\pm$0.47 & 2.11&$\pm$0.08 & $6.8 \times 10^1$ & $2.7 \times 10^{-6}$\
6-6 & 12.01 & 0.72 & 0.22&$\pm$0.02 & 0.17&$\pm$0.02 & 4.42&$\pm$0.67 & 6.57&$\pm$0.71 & $1.4 \times 10^2$ & $1.1 \times 10^{-6}$\
6-7 & 12.36 & 0.24 & 0.31&$\pm$0.05 & 0.20&$\pm$0.02 & 3.93&$\pm$0.89 & 2.63&$\pm$0.45 & $9.2 \times 10^1$ & $1.9 \times 10^{-6}$\
6-8 & 12.90 & 0.15 & 0.23&$\pm$0.05 & 0.16&$\pm$0.05 & 4.10&$\pm$1.57 & 1.31&$\pm$0.28 & $1.1 \times 10^2$ & $1.3 \times 10^{-6}$\
6-9 & 13.28 & 0.17 & 0.12&$\pm$0.03 & 0.04&$\pm$0.03 & 2.81&$\pm$3.75 & 0.50&$\pm$0.13 & $< 3.0 \times 10^2$ & –\
6-10 & 14.00 & 0.37 & 0.14&$\pm$0.01 & 0.04&$\pm$0.01 & 2.61&$\pm$1.22& 1.29&$\pm$0.06 & $< 9.3 \times 10^1$ & –\
7-1 & 15.99 & 0.13 & 0.56&$\pm$0.03 & 0.94&$\pm$0.08 & 8.74&$\pm$0.38 & 8.61&$\pm$0.43 & $3.4 \times 10^2$ & $2.6 \times 10^{-6}$\
7-2 & 16.31 & 0.52 & 0.52&$\pm$0.06 & 0.49&$\pm$0.08 & 5.05&$\pm$0.87 &13.49&$\pm$1.59 & $1.5 \times 10^2$ & $2.6 \times 10^{-6}$\
7-3 & 16.34 & 0.20 & 0.37&$\pm$0.06 & 0.93&$\pm$0.09 &17.16&$\pm$0.74 &26.44&$\pm$4.65 & $7.2 \times 10^2$ & $2.0 \times 10^{-6}$\
7-4 & 16.92 & 0.14 & 0.29&$\pm$0.02 & 0.33&$\pm$0.04 & 5.85&$\pm$0.58 & 2.55&$\pm$0.21 & $2.3 \times 10^2$ & $1.2 \times 10^{-6}$\
15-2 & 54.56 & 0.29 & 0.34&$\pm$0.00 & 0.24&$\pm$0.02 & 4.10&$\pm$0.31 & 3.80&$\pm$0.02 & $1.0 \times 10^2$ & $2.0 \times 10^{-6}$\
16-1 & 55.04 & 1.05 & 0.06&$\pm$0.00 & 0.03&$\pm$0.01 & 3.17&$\pm$1.36 & 1.82&$\pm$0.09 & $3.9 \times 10^1$ & $6.9 \times 10^{-7}$\
16-2 & 56.55 & 0.21 & 0.61&$\pm$0.02 & 0.62&$\pm$0.03 & 5.32&$\pm$0.23 & 6.88&$\pm$0.20 & $1.6 \times 10^2$ & $3.1 \times 10^{-6}$\
16-3 & 56.77 & 0.09 & 0.16&$\pm$0.03 & 0.12&$\pm$0.04 & 4.34&$\pm$1.70 & 0.56&$\pm$0.11 & $1.3 \times 10^2$ & $7.8 \times 10^{-7}$\
16-4 & 57.10 & 0.28 & 0.43&$\pm$0.01 & 0.22&$\pm$0.02 & 3.39&$\pm$0.34 & 3.60&$\pm$0.08 & $4.8 \times 10^1$ & $4.4 \times 10^{-6}$\

### Narrow- and broad-line components

The CO absorption profile often comprises narrow-line components ($\Delta v_{1/2}$ $\simeq$ 0.1 km s$^{-1}$) and broad-line components with $\Delta v_{1/2}$ $\gtrsim$ 0.3 km s$^{-1}$. The shape of the emission lines tends to be smoother than that of the absorption lines, though the velocity resolution for the emission study is sufficiently high. Narrow-line components seen in ALMA absorption spectra are less prominent in the single-dish emission spectra.

At $T_{\rm k}$ = 40 K, the thermal line width of CO is 0.16 km s$^{-1}$, which is comparable with the line widths of narrow-line components. This implies that the non-thermal motion does not dominate the internal motion of these components. On the other hand, the internal motion of the broad-line components is apparently dominated by non-thermal motion. In Subsections [4.2](#sec:substructure-1) and [4.3](#sec:substructure-2), we will estimate the physical conditions and sizes of substructures and test if the broad-line components can be explained as ensembles of narrow-line components.

### Link between line width and excitation temperature

The correlation plot of the line width and the excitation temperature of individual Gaussian components is shown in Figure [10](#fig:linewidth-tex). The data were taken from Tables [\[table:gaussfit12\]](#table:gaussfit12) and [\[table:gaussfit13\]](#table:gaussfit13). The histogram of line widths is not bimodal and is scattered over the wide velocity range from 0.1 to 1 km s$^{-1}$. This means that the partition between the narrow- and broad-line components is unclear. All components with high excitation temperature ($>$ 8 K) have half maximum half widths narrower than 0.4 km s$^{-1}$. This may be understood as the kinematic and physical co-evolution of clumps or the result of confusion of multiple components with similar center velocities and excitation temperatures.

## Chemical compositions

Here, we deduce the chemical composition of individual velocity components. The subcomponents resolved by multiple Gaussian fitting of CO and $^{13}$CO are not separated in this analysis because of the poorer sensitivity and velocity resolution for most of the subcomponents. For CO and $^{13}$CO, multiple transitions were detected, and the column density was obtained by using the results of the excitation analysis in Section [3.3](#sec:excitation_analysis). For most cases, the column density was obtained by assuming LTE for optically thin lines and that the excitation temperature is the CMB temperature. We also detected multiple transitions of CN, but excitation analysis was not done because of the severe hyperfine contamination.

In the following subsections, the column density of HCO$^+$, $N$(HCO$^+$), is used as an indicator of $N$(H$_2$) because we cannot directly measure it for individual Galactic disk clouds that overlap along the line of sight toward the QSO behind the Galactic plane. Note that the reliability of $N$(HCO$^+$) as a proxy of $N$(H$_2$) in diffuse clouds with a constant $N$(HCO$^+$)/$N$(H$_2$) = $3 \times 10^{-9}$ is well established as described in (cite: 2023ApJ...943..172L). This value is consistent with the results for low-density ($<$$10^3$ cm$^{-3}$) regions in star-forming clouds (cite: 2021A&A...648A.120R). Very rough conversion to $A_{\rm V}$ may also be possible by assuming the standard gas-to-extinction ratio ($N$(H)+2$N$(H$_2$))/$A_{\rm V}$ = $2 \times 10^{21}$ cm$^{-2}$ mag$^{-1}$ (cite: 2017MNRAS.471.3494Z) and that the molecular fraction is close to unity. In the horizontal axis of the following figures, $N$(HCO$^+$) = $10^{12}$ cm$^{-2}$ roughly corresponds to $A_{\rm V}$ = 0.3 mag.

### CN-bearing molecules

#### HNC and HCO$^+$

A correlation plot of HNC and HCO$^+$ column densities from this study is shown in Figure [11](#fig:hco+_hnc) together with the results of the previous studies (cite: 2001A&A...370..576L; 2010A&A...520A..20G; 2011A&A...535A.103M; 2016PASJ...68....6A). The overall correlation is good, as we see in Figure [11](#fig:hco+_hnc). The behavior of our data points is quite similar to that of (cite: 2018A&A...610A..43R), who observed the molecular clouds in the inner Galaxy. The results of (cite: 2001A&A...370..576L) also show a similar trend except for one outlier (29.10 km s$^{-1}$ component of G10.62$-$0.38) in the anti-center direction.

Our data also show that the abundance of HNC over HCO$^+$ significantly decreases at $N$(HCO$^+$) $< 5 \times 10^{12}$ cm$^{-2}$ ($A_{\rm V}$ $<$ 1.5 mag). This may be attributed to the selective dissociation of HNC in diffuse molecular gas.

#### CN, HCN, and HNC

To understand the correlation of column densities of CN-bearing molecules, narrower velocity ranges were set to minimize the blending by the other hyperfine components of CN and HCN. The column densities of HCN, HNC, and CN obtained in this manner are shown in Table [\[table:col_cn\]](#table:col_cn). Note that the opacity was obtained for the clean component. Thus, the conversion from the integrated opacity to the column density varies by the hyperfine component used (See, Equation [\[eq:n_tot\]](#eq:n_tot) and Tables [2](#table:mol_data-1) and [3](#table:mol_data-2)). Due to the velocity range being narrower than Table [\[table:col_hco+\_hnc\]](#table:col_hco+_hnc), the column density of HNC is slightly lower by about 10%. The same shall apply to CN and HCN. This slight difference does not affect the overall conclusion of this work.

crrDDDDDD & & & &\
Comp & $v_{\rm min}$ & $v_{\rm max}$ & & & & & &\
ID & & & & & & &\
1a & $-$28.0 & $-$23.0 & $-$0.13 &$\pm$0.03 & $-$22.2 &$\pm$0.48 & 0.027 &$\pm$0.004 & 0.05 &$\pm$0.01 & 0.07 &$\pm$0.06 & 1.29 &$\pm$1.07\
2a & $-$20.0 & $-$19.0 & $-$0.02 &$\pm$0.01 & $-$0.27 &$\pm$0.22 & $-$0.001 &$\pm$0.002 & 0.00 &$\pm$0.00 & $-$0.02 &$\pm$0.03 & $-$0.43 &$\pm$0.51\
4a & $-$1.4 & 0.0 & $-$0.01 &$\pm$0.02 & $-$0.19 &$\pm$0.26 & 0.009 &$\pm$0.008 & 0.02 &$\pm$0.01 & $-$0.06 &$\pm$0.03 & $-$4.17 &$\pm$1.98\
5a & 0.0 & 2.8 & $-$0.05 &$\pm$0.02 & $-$0.82 &$\pm$0.36 & $-$0.003 &$\pm$0.011 & $-$0.01 &$\pm$0.02 & $-$0.09 &$\pm$0.04 & $-$1.77 &$\pm$0.81\
5b & 2.9 & 7.0 & 0.03 &$\pm$0.03 & 0.60 &$\pm$0.43 & 0.111 &$\pm$0.013 & 0.20 &$\pm$0.02 & $-$0.08 &$\pm$0.05 & $-$5.13 &$\pm$3.30\
6a & 7.3 & 10.0 & $-$0.04 &$\pm$0.02 & $-$0.72 &$\pm$0.35 & $-$0.018 &$\pm$0.011 & $-$0.03 &$\pm$0.02 & $-$0.08 &$\pm$0.04 & $-$5.37 &$\pm$2.72\
6b & 10.2 & 14.5 & 1.46 &$\pm$0.03 & 5.03 &$\pm$0.09 & 0.503 &$\pm$0.015 & 0.90 &$\pm$0.03 & 0.95 &$\pm$0.05 & 17.95 &$\pm$0.98\
7a & 15.2 & 17.3 & & 1.034 &$\pm$0.017 & 1.85 &$\pm$0.03 & 0.49 &$\pm$0.04 & 31.01 &$\pm$2.32\
8a & 21.5 & 23.3 & 0.40 &$\pm$0.02 & 2.31 &$\pm$0.10 & 0.189 &$\pm$0.010 & 0.34 &$\pm$0.02 & 0.37 &$\pm$0.03 & 6.99 &$\pm$0.64\
9a & 24.0 & 26.0 & & $-$0.002 &$\pm$0.009 & 0.00 &$\pm$0.02 & $-$0.02 &$\pm$0.04 & $-$1.52 &$\pm$2.38\
10a & 27.8 & 30.2 & 0.39 &$\pm$0.02 & 1.33 &$\pm$0.07 & 0.087 &$\pm$0.010 & 0.16 &$\pm$0.02 & 0.22 &$\pm$0.04 & 4.23 &$\pm$0.74\
11a & 31.9 & 33.6 & 0.48 &$\pm$0.02 & 1.67 &$\pm$0.06 & 0.141 &$\pm$0.009 & 0.25 &$\pm$0.02 & 0.06 &$\pm$0.03 & 3.03 &$\pm$1.61\
12a & 36.0 & 37.5 & 0.03 &$\pm$0.02 & 0.18 &$\pm$0.09 & 0.042 &$\pm$0.008 & 0.08 &$\pm$0.01 & $-$0.03 &$\pm$0.03 & $-$1.64 &$\pm$1.61\
13a & 44.3 & 47.0 & & $-$0.024 &$\pm$0.011 & $-$0.04 &$\pm$0.02 & 0.01 &$\pm$0.04 & 0.28 &$\pm$0.79\
14a & 48.8 & 50.7 & 0.00 &$\pm$0.02 & $-$0.01 &$\pm$0.30 & $-$0.001 &$\pm$0.009 & 0.00 &$\pm$0.02 & $-$0.07 &$\pm$0.04 & $-$1.28 &$\pm$0.66\
14b & 51.0 & 52.0 & $-$0.02 &$\pm$0.01 & $-$0.27 &$\pm$0.22 & 0.000 &$\pm$0.006 & 0.00 &$\pm$0.01 & 0.00 &$\pm$0.02 & 0.00 &$\pm$0.47\
15a & 54.0 & 55.4 & 1.07 &$\pm$0.01 & 6.12 &$\pm$0.08 & 0.498 &$\pm$0.0011 & 0.89 &$\pm$0.02 & 0.93 &$\pm$0.03 & 17.52 &$\pm$0.57\
16a & 56.0 & 57.5 & 1.48 &$\pm$0.02 & 8.51 &$\pm$0.09 & 0.646 &$\pm$0.012 & 1.15 &$\pm$0.02 & 1.31 &$\pm$0.03 & 24.64 &$\pm$0.57\
17a & 64.0 & 71.8 & & 0.032 &$\pm$0.018 & 0.06 &$\pm$0.03 & 0.19 &$\pm$0.03 & 12.13 &$\pm$1.74\
18a & 77.0 & 81.0 & 0.88 &$\pm$0.03 & 5.07 &$\pm$0.14 & 0.320 &$\pm$0.014 & 0.57 &$\pm$0.02 & 0.12 &$\pm$0.02 & 7.37 &$\pm$1.23\
19a & 83.0 & 85.0 & 0.26 &$\pm$0.02 & 1.47 &$\pm$0.10 & 0.148 &$\pm$0.010 & 0.27 &$\pm$0.02 & 0.07 &$\pm$0.02 & 4.68 &$\pm$1.62\
19b & 86.7 & 87.7 & & 0.031 &$\pm$0.007 & 0.06 &$\pm$0.01 & 0.05 &$\pm$0.02 & 3.36 &$\pm$1.62\
20a & 91.5 & 96.2 & 0.78 &$\pm$0.03 & 2.70 &$\pm$0.09 & 0.166 &$\pm$0.014 & 0.30 &$\pm$0.03 & 0.00 &$\pm$0.05 & 0.01 &$\pm$3.55\
21a & 100.7 & 101.2 & 0.00 &$\pm$0.01 & 0.02 &$\pm$0.05 & 0.007 &$\pm$0.005 & 0.01 &$\pm$0.01 &\

A correlation plot of column densities of HCN and HNC based on Table [\[table:col_cn\]](#table:col_cn) is shown in Figure [12](#fig:hcn_hnc), together with the results of previous studies for the Galactic absorption system (cite: 2001A&A...370..576L; 2010A&A...520A..20G; 2018A&A...610A..43R) and for $z$=0.89 QSO absorption system (cite: 2011A&A...535A.103M). The results obtained from emission line observations for dark cloud cores (cite: 1998ApJ...503..717H) are also overlaid. The diagonal lines represent ratios of 1 and 4.

In the present study and the other absorption studies toward Galactic diffuse clouds, the HCN/HNC ratio is nearly constant ($\gtrsim$4). On the other hand, the HCN/HNC ratio for dark cloud cores is about 1, indicating that the ratios are very different. The systematic difference between star-forming and starless cores claimed by (cite: 1998ApJ...503..717H) is not clearly seen.

This difference in the HCN/HNC ratio may be understood as a difference in kinetic temperature, as has been suggested by previous studies (cite: 1998ApJ...503..717H; 2020A&A...635A...4H). The empirical relation by (cite: 2020A&A...635A...4H) indicates that the clouds explored in this study have a kinetic temperature of $\gtrsim$40 K, and the dark cloud cores with a ratio of about 1 have a kinetic temperature of 10 K.

A correlation plot of the column densities of CN and HCN obtained in this study is shown in Figure [13](#fig:cn_hcn), together with the results of previous studies (cite: 2001A&A...370..576L; 2010A&A...520A..20G; 2018A&A...610A..43R). The correlation between CN and HCN is good and in agreement with the previous studies, though our data tend to have a lower CN/HCN ratio than the best fit (6.8) obtained by (cite: 2001A&A...370..576L). Here we reiterate that the velocity range for this analysis of the CN group in Table [\[table:col_cn\]](#table:col_cn) was set narrower than that in Table [\[table:col_hco+\_hnc\]](#table:col_hco+_hnc) to reduce the effect of blending by hyperfine components. The column densities shown here are thus smaller than those in Table [\[table:col_hco+\_hnc\]](#table:col_hco+_hnc) by about 10%. This slight difference does not affect the overall conclusion of this work.

Similarly, a correlation plot of the column densities of CN and HNC obtained in this study is shown in Figure [14](#fig:cn_hnc). At large $N$(CN) $> 3 \times 10^{12}$ cm$^{-2}$, CN and HNC show a tight and linear correlation with the HNC/CN abundance ratio $\simeq$1/20. The ratio starts to show a large and significant scatter below this threshold.

### Other N-bearing molecules

We obtain 1$\sigma$ upper limits of $N$(N$_2$H$^+$)/$N$(HCO$^+$) $< 0.14$ and $< 0.09$ toward Components 7 and 16, which are presumably dark clouds. These values are much smaller than the previous results — $N$(N$_2$H$^+$)/$N$(HCO$^+$) = 0.25 in TMC-1 (cite: 1992IAUS..150..171O). Since N$_2$H$^+$ is considered to form only very late in the chemical evolution of dark clouds (cite: 1999A&A...350..204N), this low upper limit supports that these clouds are still in the early phase of evolution.

Regarding ND, there is not much work on the measurement of its abundance in interstellar space. (cite: 2016A&A...587A..26B) detected the ND emission from the prestellar core 16293E in L1689N and estimated $X$(ND) = $1.6 \times 10^{-9}$ in its central $15''$ region. In this work, due to the high noise level at ALMA Band 8, the 1$\sigma$ upper limit ($X$(ND) $< 3 \times 10^{-8}$) was not sufficient for direct comparison with the above value. It may still be useful as a reference value for the Galactic disk clouds.

CN$^-$ is one of the smallest anions observable in interstellar space and will provide a key to understanding the formation mechanism of anions in interstellar space. The past observations demonstrate that the anion-to-neutral abundance ratio of C$_{2n-1}$N$^-$ (with $n$ = 1, 2, 3, and 4) increases with increasing molecular size (cite: doi:10.1021/acs.chemrev.6b00480), as was expected if the radiative electron attachment to the neutral counterpart of the anion is the formation mechanism (cite: 1981Natur.289..656H). The only claimed detection of interstellar CN$^-$ so far is toward the carbon star IRC+10216, presumably in the outer regions of the envelope with very large anion/neutral ratio (cite: 2010A&A...517L...2A) but with severe contamination in the $J$=1–0 and $J$=2–1 lines. We set very robust 1$\sigma$ upper limits of $N$(CN$^-$)/$N$(CN) $<$ 0.19 and $<$ 0.29 (or $\log X$(CN$^-$) at $-8.53$ and $-8.50$) for Components 7 and 16, respectively.

### Hydrocarbons

#### c-C$_3$H$_2$ and HCO$^+$

A correlation plot of $c$-C$_3$H$_2$ and HCO$^+$ column densities obtained in this study is shown in Figure [15](#fig:hco+_c2h), together with the results of the previous studies (cite: 2001A&A...370..576L; 2010A&A...520A..20G; 2011A&A...525A.116G; 2011A&A...535A.103M; 2018A&A...610A..43R). A relatively tight linear correlation was observed over the wide range $N$(HCO$^+$) = (0.05–200) $\times 10^{12}$ cm$^{-2}$. This suggests that $c$-C$_3$H$_2$ is quite ubiquitous in diffuse molecular gas and may be a good tracer of H$_2$ in diffuse gas as has been pointed out in previous studies (cite: 2000A&A...358.1069L).

#### C$_2$H, c-C$_3$H, and c-C$_3$H$_2$

A correlation plot of C$_2$H and $c$-C$_3$H$_2$ column densities obtained in this study is shown in Figure [16](#fig:c2h_c3h2) together with the results of previous studies (cite: 2000A&A...358.1069L; 2010A&A...520A..20G; 2011A&A...525A.116G; 2011A&A...535A.103M; 2016PASJ...68....6A; 2018A&A...610A..43R). A tight linear relationship was observed in this study, at least for higher column density components (Figure [16](#fig:c2h_c3h2)). This supports the tight correlation between the abundances of C$_2$H and $c$-C$_3$H$_2$ in diffuse clouds (cite: 2000A&A...358.1069L; 2011A&A...525A.116G).

On the contrary, the correlation between ortho- $c$-C$_3$H$_2$ and $c$-C$_3$H is much poorer (Figure [17](#fig:c3h_c3h2)) though (cite: 2014A&A...564A..64L) claimed that the $c$-C$_3$H/$c$-C$_3$H$_2$ ratio is near constant at $\simeq$0.1 for diffuse gas. This difference comes from the increase of the data sampled at lower column density and the inclusion of the upper limit data from (cite: 1990A&A...239..319M). The fitting by (cite: 2014A&A...564A..64L) may be affected by the small number of data points in low column density regions. Nevertheless, with only a few exceptions, ortho- $c$-C$_3$H$_2$ is more abundant than $c$-C$_3$H.

The ubiquity of $c$-C$_3$H$_2$ in diffuse environments is surprising because the gas phase formation reaction of this molecule in diffuse environments seems difficult. The formation reaction of $c$-C$_3$H$_2$ has been speculated by (cite: 1993ApJ...417..181M) to be the dissociative recombination of $c$-C$_3$H$_3^+$, $$\begin{equation}
\label{eq:c3h2}
{\rm C_3H_3^+} + e^- \rightarrow {\rm C_3H_2} + {\rm H}.
\end{equation}$$ On the other hand, $c$-C$_3$H$_2$ is generally destroyed by reactions between ions and neutral molecules, and any species of the type HX$^+$ can react to convert the $c$-C$_3$H$_2$ back to $c$-C$_3$H$_3^+$ (cite: 1993ApJ...417..181M). The most important reactants for the destruction of $c$-C$_3$H$_2$ are HCO$^+$, H$_3^+$, and H$_3$O$^+$ like: $$\begin{equation}
\label{eq:c3h3+}
{\rm C_3H_2} + {\rm HCO^+} \rightarrow {\rm C_3H_3^+} + {\rm CO}, 
\end{equation}$$ and thus $c$-C$_3$H$_2$ is mostly destroyed by converting it back to an even larger molecule, $c$-C$_3$H$_3^+$ (cite: 1997A&AS..121..139M).

The ubiquity of C$_2$H and $c$-C$_3$H$_2$ supports a top-down formation mechanism by release from hydrogenated amorphous carbon, rather than a bottom-up synthesis by gas phase reaction (cite: 2000ESASP.456...91F; 2003A&A...406..899F; 2004A&A...417..135T; 2005A&A...435..885P; 2015ApJ...800L..33G; 2020ApJ...896..130C) even in dark and diffuse clouds. Recent experimental (cite: 2015MNRAS.447.1242D) and theoretical (cite: 2022MNRAS.511.3832A) studies also support this scenario.

### CO, HCO$^+$, and “CO-poor” molecular gas

A correlation plot of the column densities of CO and HCO$^+$ obtained in this study is shown in Figure [18](#fig:hco+_co) together with the results of the previous studies (cite: 1998A&A...339..561L; 2019A&A...627A..95L; 2023ApJ...943..172L). In the previous studies, CO and HCO$^+$ were reported to be loosely correlated with a power-law slope of 1.4. Our data extended the plot toward the dense end ($N$(HCO$^+$) $\sim$ 10$^{13}$ cm$^{-2}$, or $A_{\rm V}$ $\sim$ 3 mag) and prefers an even steeper power-law slope close to 2.

Given that all major species analyzed in this study except CO (i.e., HCO$^+$, HCN, HNC, CN, C$_2$H, $c$-C$_3$H, and $c$-C$_3$H$_2$) show a good positive correlation, only the behavior of CO is totally different. This is thus understood as a reduction of CO rather than an enhancement of HCO$^+$ and all the other major species.

To understand the controlling factor of the CO/HCO$^+$ fractional abundance, the CO/HCO$^+$ abundance ratio was plotted as a function of the HCO$^+$ column density and the Galactocentric distance $R_{\rm G}$ in Figure [19](#fig:co_hco+_ratio). Its dependence on the HCO$^+$ column density, or $A_{\rm V}$, is quite visible with a large scatter, while its dependence on the Galactocentric distance is not apparent.

The presence of “CO-dark” (or we call it here more precisely as “CO-poor”) molecular gas has been pointed out in UV-irradiated environments (cite: 1988ApJ...334..771V; 2010ApJ...716.1191W) and in diffuse environments (cite: 2007ApJS..168...58S; 2008ApJ...687.1075S; 2018A&A...617A..54L). This relative reduction of the CO abundance was also pointed out by (cite: 2019A&A...627A..95L) and (cite: 2020ApJ...889L...4L), but the amplitude of the reduction was not much (up to a factor of 10) for their data. Thanks to the addition of the measurements toward dark clouds, the plot more clearly shows the possible dependence of the CO/HCO$^+$ abundance ratio on the HCO$^+$ column density.

### HCO$^+$ and HOC$^+$

No HOC$^+$, the isomer of HCO$^+$, was detected in the present study, and the upper limit for the HCO$^+$/HOC$^+$ isomer ratio at the 1$\sigma$ level is approximately 200 for the dark clouds, Components 7 and 16. Note that the upper limit was obtained for the components with saturated HCO$^+$ absorption by multiplying the H$^{13}$CO$^+$ column density by a factor of 50 to obtain the HCO$^+$ column density.

The present results are higher than those for diffuse clouds (cite: 2004A&A...428..117L; 2019A&A...622A..26G) and lower than those for massive star-forming regions (cite: 1995ApJ...455L..73Z; 1997ApJ...481..800A). This may be explained if these clouds are richer in molecular hydrogen than diffuse clouds but poorer than GMCs, and the conversion of HOC$^+$ to HCO$^+$ proceeds as in the following reaction equation (cite: 1996ApJ...463L.113H): $$\begin{equation}
\label{eq:hoc+_h2}
{\rm HOC^+} + {\rm H_2} \rightarrow {\rm HCO^+} + {\rm H_2}.
\end{equation}$$

### HCO/H$^{13}$CO$^+$ ratio and UV intensity

In emission line studies, the enhancement of the HCO/H$^{13}$CO$^+$ abundance ratio is often used as a probe of PDRs because both of them trace dense regions with very similar optical thicknesses and because their frequencies are extremely close ($\Delta$ = 23.172 MHz, or 80.07 km s$^{-1}$ for HCO $N_K$=$1_{0,1}$–$0_{0,0}$, $J$=$\frac{1}{2}$–$\frac{1}{2}$, $F$=1–1), making it possible to measure very accurate ratios of column densities in simultaneous observations. Although the column densities of HCO and HCO$^+$ should be compared from the viewpoint of the chemical network and the isotopic fractionation, the above merits justify using the HCO/H$^{13}$CO$^+$ rather than HCO/HCO$^+$. We extend this analysis to diffuse gas whose density is much lower than the critical densities of HCO and H$^{13}$CO$^+$ (cite: 2002ApJ...575..950O; 2009A&A...494..977G) through measurements of their absorption lines.

A correlation plot of the column densities of HCO and H$^{13}$CO$^+$ obtained in this study is shown in Figure [20](#fig:hco_hco+). In addition, the results of absorption measurements toward QSOs and Galactic radio continuum sources from previous studies (cite: 2014A&A...564A..64L; 2016PASJ...68....6A) and those of emission studies toward typical PDRs (cite: 2001A&A...372..291S; 2009A&A...494..977G) are plotted. The diagonal lines indicate the constant $N$(HCO)/$N$(H$^{13}$CO$^+$) ratios of 20 and 1. The PDRs tend to have larger ratios, while the associated cold, dense core has a small value close to unity.

The possible processes that enhance the HCO/HCO$^+$ ratio in PDRs were examined by (cite: 2009A&A...494..977G) and the references therein. In the FUV-shielded gas, the charge exchange reactions of HCO$^+$ with metals, like, $$\begin{equation}
\label{eq:hco+_ion_exchange}
{\rm Fe} + {\rm HCO^+} \rightarrow {\rm HCO} + {\rm Fe^+}, 
\end{equation}$$ are the main gas-phase formation routes of HCO. Since metals are depleted from the gas phase in dense cores, the HCO abundance remains low inside the cores.

The formation of HCO in the PDR is dominated by the dissociative recombination of H$_2$CO$^+$, like, $$\begin{equation}
\label{eq:and C+_recomb}
{\rm H_2CO^+} + e^- \rightarrow {\rm HCO} + {\rm H}.
\end{equation}$$ In addition, the photodissociation of H$_2$CO contributes to the formation of HCO, like, $$\begin{equation}
\label{eq:h2co_photodissociation}
{\rm H_2CO} + h\nu \rightarrow {\rm HCO} + {\rm H}.
\end{equation}$$ Another effective pathway to produce HCO is to proceed with chemical reactions of atomic oxygen with carbon radicals that reach high abundances only in the PDR, $$\begin{equation}
\label{eq:hco_synthesis}
\ce{C+ ->C[H2] CH2+ ->C[H2] CH3+ ->C[e-]  CH2 ->C[O]  HCO}
\end{equation}$$ In both cases, the environment is of high UV intensity, which is common in PDRs.

The above descriptions are made for dense PDRs but remain valid in a diffuse regime as long as the regions are C$^+$-rich. The absorption line observations can measure the abundance ratio even when excitation is insufficient. Therefore, even at relatively low densities, the C$^+$-rich regions can be observed as a region of high $N$(HCO)/$N$(H$^{13}$CO$^+$) ratio.

The previous studies showed that high $N$(HCO)/$N$(H$^{13}$CO$^+$) ratios are observed in the normal molecular gas in the Galactic plane (cite: 2014A&A...564A..64L; 2016PASJ...68....6A). Our data for Components 6, 7, 15, and 16 showed that the ratio remains high even in dark clouds when observed in absorption. This suggests that from the viewpoint of interstellar chemical reactions involving C$^+$, most of the normal molecular gas in the Galactic plane is in an environment closer to the PDRs than to the cold, dense cores. This may be understood as our absorption measurements toward dark clouds still unbiasedly sample diffuse surrounding material. In contrast, the ratio through emission measurements is strongly biased to the regions with the highest density.

### H$_2$CO and C

#### H$_2$CO

Although the sensitivity is limited, we see marginal detection of H$_2$CO in Components 7 and 16. Components 6, 15, 18, and 20 are barely visible in this $J_{K_a,K_c}$=$3_{0,3}$–$2_{0,2}$ line. Observations in $J_{K_a,K_c}$=$2_{0,2}$–$1_{0,1}$ at 145.602949 GHz are needed for a better constraint of the H$_2$CO column density. It is known that H$_2$CO has a rapid increase in abundance around $N$(HCO$^+$) $\sim 1 \times 10^{12}$ cm$^{-2}$ (cite: 1995A&A...299..847L). This study obtained the H$_{2}$CO/HCO$^{+}$ ratio for the four saturated CO absorbers ($N$(HCO$^+$) $\sim 1 \times 10^{12}$ cm$^{-2}$ ), which are dark clouds. The H$_{2}$CO/HCO$^{+}$ ratio is $<$ 0.36, 1.36$\pm$0.65, $<$ 0.41, and 0.54$\pm$0.36 for Components 6, 7, 15, and 16, respectively. On the other hand, H$_{2}$CO was not detected in diffuse clouds, implying the ratio was less than approximately 10. Previous studies have obtained values of about 2 for dark clouds, TMC1 (cite: 1992IAUS..150..171O), and 2.3 for diffuse and translucent clouds (cite: 2006A&A...448..253L), indicating that the composition is constant regardless of cloud type. In these dark cloud results, it is noteworthy that the ratios are small. The high $^{13}$CO/C$^{18}$O and HCO/H$^{13}$CO$^{+}$ also suggest a PDR-like environment, implying the photodissociation of H$_{2}$CO.

#### C

A similar trend is also visible for C in the $^3P_1$–$^3P_0$ transition, though the poor signal-to-noise ratio of the archived data prevents further study. A comparison of $N$(C) and $N$(CO) in Table [4](#table:non-detection) shows an equal amount of neutral gas-phase carbon and CO for Components 7 and 16.

#### CO$^+$

CO$^+$ is routinely observed in dense PDRs, and the CO$^+$ abundance was $7.2 \times 10^{-11}$ toward the PDR3 position of Mon R2 and $2.0 \times 10^{-11}$ toward the IF position of Mon R2 (cite: 2016A&A...593L..12T). On the other hand, while HCO$^+$ is abundant, there are no reported detections of CO$^+$ in the diffuse and translucent interstellar medium or dark clouds. The best constraint in the diffuse and translucent interstellar medium so far was given by (cite: 2021A&A...648A..38G), and the 1$\sigma$ upper limit of the CO$^+$ abundance is $<4 \times 10^{-11}$. As discussed in (cite: 2021A&A...648A..38G), the non-detection of CO$^+$ at this level in diffuse clouds suggests that CO$^+$ is not the precursor of HCO$^+$ that recombines to form CO. The present result constrained the 1$\sigma$ upper limits in dark clouds to be $<7.2 \times 10^{-11}$ and $<8.3 \times 10^{-11}$, respectively, for Components 7 and 16.

### Sulfur-bearing molecules and shock tracers

#### CS, SO, and SiO

Sulfur and silicon are elements with low volatility; thus, sulfur- and silicon-bearing molecules are rare in the gas phase. Molecules like SiO and SO are thus used as tracers of interstellar shocks that spatter these molecules out from dust grains.

In this study, one of the velocity components showed absorption of SO, SiO, and CS. The column densities of SO and SiO are plotted against that of CS in Figures [21](#fig:cs_so) and [22](#fig:cs_sio), respectively, overlaid on the data from previous studies (cite: 2002A&A...384.1054L; 2015A&A...577A..49N; 2018A&A...610A..10C).

In Figure [21](#fig:cs_so), we identified an upper envelope that corresponds to the $N$(SO)/$N$(CS) ratio close to unity. In some cases, $N$(CS) and $N$(SO) have significant errors, and only upper limits are obtained. However, there is generally a good correlation between $N$(CS) and $N$(SO).

Considering that the $X$(CS) values obtained for the four dark clouds with saturated CO absorption lines vary by as much as two orders of magnitude, they both change closely following each other.

Regarding the correlation between CS and SiO, the present result shows the SiO/CS abundance ratio of 0.046$\pm$ 0.009, similar to the ones obtained in the previous study (cite: 2018A&A...610A..10C).

In the component we obtained a SiO/CS ratio, the CO excitation temperature was only slightly higher than the other components, and no YSO-like excitation sources were found. This suggests that the shock wave’s impact was not so large, or the gas cooled rapidly before re-agglomeration into dust.

#### HCS$^+$, H$_2$CS, and C$_2$S

We only obtained 1$\sigma$ upper limits of the abundances of HCS$^+$, H$_2$CS, and C$_2$S at $<5 \times 10^{-8}$, $<5 \times 10^{-9}$, and $<6 \times 10^{-9}$, respectively, for Component 7, which is presumably a dark cloud. These values do not provide meaningful limits since the previous study showed that $X$(HCS$^+$) $\sim 2 \times 10^{-10}$, $X$(H$_2$CS) $\sim 3 \times 10^{-10}$, and $X$(C$_2$S) $\sim 1 \times 10^{-10}$ in diffuse and translucent clouds in the line-of-sight to Sgr B2 (cite: 2018A&A...610A..10C).

#### SH$^+$

Although we did not detect SH$^+$ this time, we could put a 1$\sigma$ upper limit at $3 \times 10^{-8}$. This value is more than an order of magnitude lower than the previous studies (cite: 2000A&A...355..327L; 2002A&A...384.1054L).

In this study, the 1$\sigma$ upper limits of $\log X$(SH$^+$) obtained for Components 7 and 16 were $-8.60$ and $-8.74$. On the other hand, (cite: 2011A&A...525A..77M) and (cite: 2012A&A...540A..87G) found SH$^+$ absorption in Galactic diffuse clouds. (cite: 2011A&A...525A..77M) sampled the gas on the Galactic plane toward Sgr B2(M) to detect 6 components with $\log$(SH$^+$)/(H+2H$_2$) ranging from $-9.48$ to $-7.96$. Similarly, (cite: 2012A&A...540A..87G) sampled the gas toward Sgr B2(N) and Sgr A$^*$+50 and obtained $\log X$(SH$^+$) to be $-6.15$ and $-6.22$, respectively, which are considerably higher than the present results.

This significant difference in $X$(SH$^+$) may reflect the effect of galactic shock waves in these clouds because SH$^+$ is known to be produced by the following endothermic chemical reaction (cite: 1986ApJ...310..408D; 1986MNRAS.221..673M), $$\begin{equation}
\label{eq:sh+}
{\rm S}^+ + {\rm H_2} \rightarrow {\rm SH}^+ + {\rm H}. 
\end{equation}$$ The lower SH$^+$ abundance than the results of (cite: 2012A&A...540A..87G) suggests that the contribution of shock waves is less than in the region of their samples.

#### CH$_3$OH

Complex organic molecules (COMs) are thought to be tracers of interstellar shocks because these species form on grain surfaces and are sputtered out to the gas phase. CH$_3$OH is one of the simplest among such species.

CH$_3$OH was searched in absorption toward diffuse clouds by (cite: 2008A&A...486..493L) without success. The 1$\sigma$ upper limit of $N$(CH$_3$OH)/$N$(HCO$^+$) toward the three targets ranged from 0.06 to 0.18, which is even smaller than the value in TMC-1 (cite: 1992IAUS..150..171O). On the other hand, CH$_3$OH detected in absorption toward the $z$=0.89 system (cite: 2021A&A...652A...5M) had $\log X$(CH$_3$OH) = $-8.07$. Our upper limits of the CH$_3$OH abundance ($\log X$(CH$_3$OH) $< -8.72$ and $< -8.70$ for Components 7 and 16) are much smaller than the above values. These dark clouds may be still young in the chemical evolution that leads to COMs.

### Isotopologue ratios involving C, O, and S

The isotopologue ratio in the interstellar medium reflects the history of nucleosynthesis and is used to understand such history in the Galaxy. It is widely known that there are gradients of isotopic ratios as a function of Galactocentric distance. The isotopologue ratios of molecules often show deviation from the elemental isotopic ratio, and such an effect is called chemical fractionation. Chemical fractionation is more prominent in diffuse clouds than in cold, dense clouds (cite: 2011ApJ...728...36R). In this section, we try to extract the abundance ratios of some of the isotopologues.

#### CO/$^{13}$CO

CO is the main form of gas-phase carbon in molecular clouds, and thus the CO/$^{13}$CO isotopologue ratio is essential because it controls the C/$^{13}$C ratio of the gas-phase carbon reservoir. Because of the CO absorption saturation in dark clouds and giant molecular clouds and the limited $^{13}$CO sensitivity toward diffuse clouds and cloud edges, however, precise measurement of the CO/$^{13}$CO isotopologue ratio over a wide column density range is difficult.

In this study, a meaningful CO/$^{13}$CO isotopologue ratio was observed toward cloud edges and some of the dark and diffuse clouds, which have 30.1$\pm$4.1, 62.5$\pm$18.8, 85.5$\pm$48.8, $>$ 91.9 and 135.4$\pm$80.6 for Components 5, 8, 11, 19, and 20, respectively.

For saturated CO absorbers, the slopes of the line wings are used to estimate the isotopologue ratio. Figure [23](#fig:tau_dumped) compares the CO opacity with the $^{13}$CO opacity multiplied by 25 and 50. Components 5, 6, 7, 15, and 16 have significantly small CO/$^{13}$CO ratios that favor 25 rather than 50.

#### $^{13}$CO/C$^{18}$O double isotope ratio

In this study, the $^{13}$CO/C$^{18}$O double isotope ratio was obtained for the four saturated CO absorbers. The $^{13}$CO/C$^{18}$O isotopologue ratio is $>$ 78.3, 175.2$\pm$119.8, $>$ 31.8, and $>$ 76.8 for Components 6, 7, 15, and 16, respectively. On the other hand, the isotope ratios as elements are $^{12}$C/$^{13}$C = 89 (cite: 1987ApJ...317..926H) and $^{16}$O/$^{18}$O = 498 (cite: 1997A&A...326..139W) in the solar system. If this is directly reflected in the CO isotope ratio, the $^{13}$CO/C$^{18}$O isotope ratio is 5.5. In addition, $^{13}$CO and C$^{18}$O are 1/59 and 1/560 compared to CO in the local interstellar medium (cite: 1994ARA&A..32..191W; 1998A&A...337..246L), expecting $^{13}$CO/C$^{18}$O isotope ratio of 9.5. The CO/$^{13}$CO ratios in Components 5, 6, 7, 15, and 16 are low at about 25, which would suggest that the $^{13}$CO/C$^{18}$O ratio is at most 20. However, the results obtained for the dark clouds are much larger than this.

These chemical fractionations may be explained by the selective far-UV photodissociation of the C$^{18}$O reported in previous studies (cite: 2016ApJ...826..193L; 2018A&A...617A..14P). Observations with the NRO 45 m telescope toward the Orion A giant molecular cloud (cite: 2014A&A...564A..68S) show an average $N$($^{13}$CO)/$N$(C$^{18}$O) value of 16.47$\pm$0.10 in the nearly edge-on photon-dominated region. The average $X$($^{13}$CO)/$X$(C$^{18}$O) value in the other regions is 12.29$\pm$0.02. The values obtained in the dark clouds in this study are higher than those in such photodissociation regions (PDRs). Furthermore, the ratios of HCO to H$^{13}$CO$^{+}$ are comparable to those in typical PDR environments. Interestingly, evidence for selective photodissociation, i.e., an influence of UV radiation, is seen even in normal Galactic disk clouds.

#### CN/$^{13}$CN

CN is expected to be fractionated in the opposite sense compared to CO. CO is the most abundant C-bearing molecule and will regulate the availability of $^{13}$C atoms from the carbon reservoir if both molecules coexist.

Because of the weakness of $^{13}$CN absorption, only the lower limit of the CN/$^{13}$CN isotopologue ratio was obtained toward some of the saturated CO absorbers. The ratio is large, and $>$ 340 and $>$ 240 for Components 7 and 16, respectively. Note that these components’ CO/$^{13}$CO isotopologue ratio is smaller than 50.

The observed large values toward dark clouds in the inner Galaxy have considerable deviations from previous studies. For instance, (cite: 2005ApJ...634.1126M) measured the CN/$^{13}$CN isotopologue ratio in dense clouds to find the Galactic gradient CN/$^{13}$CN = (6.01$\pm$1.19)$R_{\rm G}$ + 12.28$\pm$9.33. (cite: 2011ApJ...728...36R) obtained the CN/$^{13}$CN isotopologue ratio toward the 11 diffuse clouds ranges from 36 to 134, having a much larger deviation than the local interstellar C/$^{13}$C ratio (cite: 2007ApJ...667.1002S). They compared these CN/$^{13}$CN isotopologue ratios with the CO/$^{13}$CO isotopologue ratio for the same lines of sight to find these ratios are generally fractionated in the opposite sense. The present results support the above scenario.

#### HCN/H$^{13}$CN

Because of the weakness of H$^{13}$CN absorption, only the lower limit of the HCN/H$^{13}$CN isotopologue ratio was obtained toward some of the saturated CO absorbers. The ratio is quite large, $>$ 106 and $>$ 94 for Components 7 and 16, respectively. This trend, similar to CN, may be explained if HCN is fractionated in the opposite sense compared to CO.

#### CS/C$^{34}$S

The CS abundance is estimated to be $\log X$(CS) = $-$8.41 and $-$9.36 for Components 7 and 16, respectively. This demonstrates that the CS abundance has a large scatter that reaches one order of magnitude in dark clouds.

We observed a high CS/C$^{34}$S isotopologue ratio ($>$ 41) toward Component 7 ($R_{\rm{G}}$ = 7.44 kpc). This is significantly higher than that expected (19.06$\pm$2.43 at $R_{\rm{G}}$ = 7.44 kpc) from the Galactic gradient of sulfur isotope ratio $^{32}$S/$^{34}$S = (1.50$\pm$0.17) $R_{\rm{G}}$ + (7.90$\pm$1.17) obtained through observations of a large sample of massive star-forming regions in CS and its isotopologues (cite: 2020ApJ...899..145Y). The present result is also much larger than the CS/C$^{34}$S isotopologue ratio of diffuse and translucent clouds in the line-of-sight to Sgr B2 measured by (cite: 2018A&A...610A..10C), which ranges from 5 to 10 except for the $-92$ km s$^{-1}$ cloud with 29$\pm$14.

The upper limit for the CS/C$^{34}$S isotopologue ratio in this study is the largest known. In the mapping spectral line survey toward W3(OH), including CS and C$^{34}$S lines (cite: 2017ApJ...848...17N), we also see a hint of an increase of CS/C$^{34}$S toward the cloud edge. We find no reasonable explanation for this high CS/C$^{34}$S isotopologue ratio since the self-shielding of the main species will not be effective for such rare species.

# Discussion

## Substructure of molecular clouds deduced from CO emission/absorption study

This study provides the following seven noteworthy results for general Galactic disk molecular clouds.

1.  Warm environment – The nearly constant and high HCN/HNC isomer ratio ($\gtrsim$4) suggests a nearly uniform kinetic temperature at $\gtrsim$40 K.

2.  Narrow- and broad-line components – Absorption lines consist of “narrow-line components” ($\sim$0.1 km s$^{-1}$) and “broad-line components” ($\gtrsim$0.3 km s$^{-1}$). The narrow line width is comparable with the thermal line width.

3.  Compactness of narrow-line components – By comparing the ALMA absorption profiles with the corresponding single-dish emission profiles, we found some of the narrow-line absorption components with high excitation temperatures are not prominent in the single-dish emission profile. This is understood if they occupy only a small fraction of the single-dish beam.

4.  CO-poor gas – The CO/HCO$^+$ abundance ratio has a large scatter of $\sim$3 orders, ranging from $\sim2 \times 10^4$ to $\sim30$. There is a trend that the low $N$(HCO$^+$) regions have low CO/HCO$^+$ abundance ratios.

5.  Mismatch of emission and absorption profiles – Some of the significant CO emission components show no counterparts in CO absorption. This may be explained if the cloud has CO-emitting substructures unresolved by the single-dish beam and the line of sight toward the QSO misses CO-containing molecular gas.

6.  Saturated CO absorption – “Saturated CO absorbers” were detected. The QSO continuum toward these components was fully saturated over a wide ($\sim$4 km s$^{-1}$) range and has $N$(H$_2$) $\gtrsim 1 \times 10^{21}$ cm$^{-2}$ (km s$^{-1}$)$^{-1}$, which means that the line is optically thick throughout the velocity range.

7.  C$^+$-rich environments – Even for velocity components with saturated CO absorption, large values of $N$(HCO)/$N$(H$^{13}$CO$^+$) $\sim$ 20 were observed. These values are comparable to typical PDRs in the Galaxy and suggest C$^+$-rich environments. The large $^{13}$CO/C$^{18}$O abundance ratio, possibly caused by selective photodissociation, also supports this argument.

The presence of compact narrow-line components, spatial heterogeneity in the single dish beam, and a C$^+$-rich environment require a clumpy structure in the cloud. The narrow-line components have near-thermal line widths and a small filling factor. Regarding the broad-line components, the close matching of the synthesized and emission line profiles that correspond to the broad-line components suggests a filling factor close to unity.

Similar narrow-line components are detected near the dense core, while broad-line components are seen outside the core in the nearby molecular clouds (cite: 2010ApJ...712L.116P; 2012A&A...546A.103S).

## Physical conditions and CO abundance of substructures

Here we deduce the physical conditions and CO abundance of some of the substructures identified by absorption measurements with the aid of `ndradex` (cite: ndradex) developed based on `RADEX` (cite: 2007A&A...468..627V). Both `ndradex` and `RADEX` calculate $T_{\rm ex}$ and $\tau$ as functions of $T_{\rm k}$, $n({\rm H_2})$, and $X({\rm CO})/(dv/dr)$. Since $T_{\rm ex}$ and $\tau$ of the individual subcomponents are listed in Tables [\[table:gaussfit12\]](#table:gaussfit12) and [\[table:gaussfit13\]](#table:gaussfit13), it is possible to estimate the physical conditions and the CO abundance of these subcomponents. Note that the saturated CO absorbers are not included in Table [\[table:gaussfit12\]](#table:gaussfit12) since Gaussian fitting was not possible for these saturated absorption features. Thus only the subcomponents with $\tau_{1-0}$ $\lesssim$ 1 (Tables [\[table:gaussfit12\]](#table:gaussfit12) and [\[table:gaussfit13\]](#table:gaussfit13)) are analyzed. As illustrated in Figures [36](#fig:radex_norm) and [37](#fig:radex_poor), the standard assumption of canonical $X$(CO) value and $dv/dr$ = 1 km s$^{-1}$ pc$^{-1}$ cannot reproduce such low $\tau_{1-0}$. This means that a significant reduction of $X({\rm CO})/(dv/dr)$ is needed to explain the observations, supporting our findings on the ubiquity of the CO-poor molecular gas. We thus do not assume the canonical $X$(CO) value in the present analysis.

Instead, we assume $T_{\rm k}$ = 50 K suggested from the large HCN/HNC ratio toward these velocity components throughout this subsection. Very weak dependences of $T_{\rm ex}$ and $\tau$ on $T_{\rm k}$ in low-density regime justify this assumption. Then, the other two free parameters that determine $T_{\rm ex}$ and $\tau$ are $n({\rm H_2})$ and $X({\rm CO})/(dv/dr)$.

The dependence of $T_{\rm ex}$ and $\tau$ on $n({\rm H_2})$ and $X({\rm CO})/(dv/dr)$ are plotted in Figure [24](#fig:radex_Xco_abundance).

For most of the components identified in CO in Table [\[table:gaussfit12\]](#table:gaussfit12), $\tau_{1-0} \gtrsim 1$ and $\tau_{2-1}$/$\tau_{1-0}$ $\simeq$ 1 ($T_{\rm ex}$ $\simeq$ 5.5 K from Equation [\[eq:tex_deduction4\]](#eq:tex_deduction4)). For this optically thin (low-$\tau$) subthermal (low-$T_{\rm ex}$) regime, $T_{\rm ex}$ is determined by $n$(H$_2$)$T_{\rm k}^{1/2}$ as shown in `RADEX` results (Figure [37](#fig:radex_poor)). The range of variation of $T_{\rm k}$ is also narrower than $n$(H$_2$). Therefore $T_{\rm k}$ does not contribute strongly to $T_{\rm ex}$ and both $n$(H$_2$) and $X({\rm CO})/(dv/dr)$ can be estimated with sufficient reliability as a cross point of the lines with constant $T_{\rm ex}$ and constant $\tau$.

We start the analysis from Subcomponent 5-1 as an example of the narrow-line components and deduce its physical conditions and CO abundance. For this subcomponent, $T_{\rm ex}$ $\simeq$ 8.2 K and $\tau_{1-0}$ $\simeq$ 0.65 requires $n$(H$_2$) $\simeq 3 \times 10^2$ cm$^{-3}$ and $X({\rm CO})/(dv/dr)$ $\simeq 4 \times 10^{-6}$ $(\rm km~s^{-1}~pc^{-1})^{-1}$. The values for the other subcomponents were deduced similarly and were listed in Tables [\[table:gaussfit12\]](#table:gaussfit12) and [\[table:gaussfit13\]](#table:gaussfit13). Since $dv/dr$ is an order of 1 $\rm km~s^{-1}~pc^{-1}$, $X({\rm CO})$ may be estimated from $X({\rm CO})/(dv/dr)$. The $X({\rm CO})$ values support the finding in Subsection [3.6.4](#sec:co_hco+) that the CO abundance significantly decreases in lower column density components, while it is comparable with the canonical value in saturated CO absorbers.

The excitation temperature of the subcomponents traced by CO tends to be higher than that traced by $^{13}$CO as shown in Tables [\[table:gaussfit12\]](#table:gaussfit12) and [\[table:gaussfit13\]](#table:gaussfit13). This is understood as a result of the photon-trapping effect that reduces the effectiveness of radiative cooling for optically thicker lines and keeps the excitation temperature higher. This is also visible in the left panel of Figure [24](#fig:radex_Xco_abundance).

### Properties of molecular gas at the diffuse end

Through the sensitive absorption measurements with ALMA, we detected very faint CO absorption at the level of $\tau_{\rm max}$ $\simeq$ 0.1, or $N$(CO)/$dv$ $\simeq 2 \times 10^{14}$ cm$^{-2}$ (km s$^{-1}$)$^{-1}$, as shown in Figure [8](#fig:gaussfit12b) and Table [\[table:gaussfit12\]](#table:gaussfit12). Most of them have very low $\tau_{2-1}$/$\tau_{1-0}$ $\simeq$ 0.3, suggesting very low $T_{\rm ex}$ $\simeq$ $T_{\rm CMB}$. If these components have $T_{\rm ex}$ comparable to the others ($T_{\rm ex} - T_{\rm CMB}$ $\sim$ 3 K) and $f$ $\simeq$ 1, $\tau_{1-0}$ $\simeq$ 0.1 predicts the measurable main beam antenna temperature at the level of $T_{\rm mb}$ $\gtrsim$ 0.3 K. The lack of corresponding emission at that level supports the very low $T_{\rm ex}$. The exception is the faint Subcomponent 18-1, which has high $\tau_{2-1}$/$\tau_{1-0}$, indicating $T_{\rm ex}$ = 6.52$\pm$2.72 K. The corresponding $T_{\rm mb}$ of the CO $J$=1–0 emission at the level of 1.5 K with $\tau_{1-0}$ $\simeq$ 0.1 suggests even higher $T_{\rm ex}$ exceeding 10 K. Interestingly, this subcomponent with very faint CO absorption has comparable column densities of HCO$^+$, CN-bearing molecules, and hydrocarbons with Components 8, 11, 19, and 20, as shown in Tables [\[table:col_hco+\_hnc\]](#table:col_hco+_hnc) and [\[table:col_c2h_c3h_c3h2\]](#table:col_c2h_c3h_c3h2).

We classify these faint CO absorption features into three based on the nature of the parent cloud and the location of the line of sight in the cloud.

The faint components in 20–50 km s$^{-1}$ (e.g., Subcomponents 10-1 and 10-2) are seen as surrounding material around scattered globules or small clouds in the longitude-velocity diagram (Figure [4](#fig:arm)) and the CO channel maps (Figure [33](#fig:fugin_12co)). This may be the molecular gas left unstructured or dispersing from structured molecular clouds.

The faint components near 80, 84, and 101 km s$^{-1}$ (i.e., Subcomponents 18-1, 19-1, and 21-1) are found near the edge of prominent clouds and thus are considered cloud edges.

The faintest components near $-19$ and $0$ km s$^{-1}$ (i.e., Subcomponents 2-1, 4-1, and 4-2) cannot be seen in either figure. The $\tau_{2-1}$/$\tau_{1-0}$ ratio suggests very low $T_{\rm ex}$ close to $T_{\rm CMB}$, accounting for the extremely low brightness of these subcomponents. For the $-19$ km s$^{-1}$ components, a very small structure is seen close to the line of sight, but it is not as bright as globules. Notably, these components already have narrow-line components, and these subcomponents are considered to be in the earliest stage of molecular cloud formation.

## Sizes of substructures

Although we did not image the subcomponents, the sizes of these subcomponents can be estimated as the filling factor of the individual subcomponent within the single-dish beam through a comparison of the actual main beam antenna temperature from single-dish emission-line observations with the “synthesized main beam antenna temperature” calculated from $f (1 - \exp(-\tau)) (T_{\rm ex} - T_{\rm CMB})$ through absorption measurements. Because $T_{\rm ex}$ and $\tau$ are known for the absorption components, the difference in the shape of the emission and absorption profiles is understood as the heterogeneity (difference in the filling factor) in the single-dish beam. As shown in Figure [7](#fig:gaussfit12), the main beam antenna temperature corresponding to Subcomponents 5-2 and 10-2 are consistent with the one calculated from $f (1 - e^{-\tau}) (T_{\rm ex} - T_{\rm CMB})$ by assuming $f$ = 1. On the other hand, there are many subcomponents with high $T_{\rm ex}$ in absorption and low $T_{\rm mb}$ for their opacity in single-dish emission spectra, and they shall be compact. Examples of such compact components include Subcomponents 5-1, 11-1, 11-2, and 19-1. Since $f = (2R/\theta D)^2$ with the clump radius $R$, the single-dish FWHM beam size $\theta$, and the distance to the cloud $D$, these components which are weaker in the observed main beam antenna temperature than expected from $T_{\rm ex}$ and $\tau$ by more than one order of magnitude shall be smaller than one-third of the $15''$ beam of the Nobeyama 45 m telescope, or $<$0.1 pc at 5 kpc.

## Other examples of small low-density substructures

The current results indirectly show that there are small ($\lesssim$0.3 pc) substructures even in diffuse clouds and cloud envelopes. Such structures have been known through sensitive and high-resolution single-dish observations to resolve small-scale diffuse structures in nearby molecular clouds. For instance, (cite: 1997ApJ...481..302S) obtained extensive CO $J$=1–0 images along the minor axis of the L1641 cloud in Orion with a $15''$ (0.03 pc) beam spaced by $34''$. Besides bright ridge-like emission in the middle of the cloud, CO emission was detected almost everywhere within the outermost boundary of the cloud. At least two distinct populations of molecular gas were found: well-defined “clumps” with small size ($\sim$ 0.3 pc), high main beam antenna temperature ($\sim$ 25 K), and relatively small line width ($\simeq$ 1.5 km s$^{-1}$) and “extended components” with low main beam antenna temperature ($\sim$ 2.5 K) and broader line width ($\simeq$ 2.5 km s$^{-1}$). In addition, (cite: 2002ApJ...565.1050S) resolved clumps with sizes from $\sim$0.2 pc down to $\sim$0.02 pc through extensive strip-scan observations of high-latitude clouds MBM 32, MBM 54, and MBM 55 in the CO $J$=1–0 emission. (cite: 2003ApJ...594..340S) further discovered several small ($\lesssim$ 0.1 pc) low-density structures in the envelope of Heiles Cloud 2 in Taurus. Toward a filamentary cloud complex facing the Sh 2–27 HII region, (cite: 2012ApJ...754...95T) found that many small clumps are moving at supersonic velocities.

Considering that the Jeans length $\lambda_{\rm J} = c_{\rm s} (G\rho)^{-1/2}$ corresponds to 0.6 ($T_{\rm k}$/10 K)$^{1/2}$ \[$n$(H$_2$)/$10^3$ cm$^{-3}$\]$^{-1/2}$ pc, most of these small substructures with lower density and higher kinetic temperature are unlikely to be formed by gravitational contraction. We will examine their formation mechanisms in our forthcoming papers.

## Molecular cloud model with small substructures and CO-poor gas

Based on the above, we propose a model of molecular clouds with the structure shown in Figure [26](#fig:clump). Since molecular clouds are a non-uniform medium due to their internal structures, the detected velocity components and chemical composition may differ depending on how the line of sight penetrates the cloud. The following three cases would exist.

Case 1: Both CO and HCO$^+$ absorption lines have narrow- and broad-line components, and the CO emission lines have bright broad-line components. The narrow-line components observed in the absorption lines often have higher densities than average. They may be compact because their beam-filling factor is small. The narrow-line components are illustrated as clumps in Figure [26](#fig:clump). The detection of multiple narrow-line components in the saturated CO absorbers suggests that many clumps are concentrated in the center of the cloud. On the other hand, some of the broad-line components observed in the absorption lines successfully reproduce the profile of the emission lines assuming a filling factor of unity. It means that some of the broad-line components are extended.\
Case 2: Broad CO and HCO$^+$ absorption lines and weak and broad CO emission are detected. The absorption and emission lines trace the CO-emitting components within the 45 m telescope beam. The weak intensity of the emission lines suggests that the beam-filling factor is small.\
Case 3: A broad-line components are observed in the HCO$^+$ absorption lines without prominent CO absorption lines. The line of sight of the absorption may have missed the clumps. This implies that the clumps are sparsely distributed. The CO abundance in the extended HCO$^+$-absorbing gas might be extremely low.

This model could explain sparse cloud structure or chemical composition heterogeneities in the beam of the NRO 45 m telescope. If the clumps overlap on the line of sight in the QSO direction, then narrow-line components were detected in absorption separately; the component in Figure [27](#fig:co_abs), which extends from 20.0–34.5 km s$^{-1}$, is considered such a region.

To examine where Cases 1, 2, or 3 are situated and which type of molecular clouds they correspond to, we used the FUGIN galactic plane survey shown in Figures [33](#fig:fugin_12co) and [34](#fig:fugin_13co). Table [6](#table:velcomp) summarizes the cloud types observed in absorption and emission lines and the position of the QSO line of sight in the clouds. Next, we examined which types of individual molecular clouds were classified. Case 1 corresponds to Components 5, 6, 7, 15, 16, and 20, and the line of sight is considered to penetrate centers of dark clouds; Case 2 corresponds to Components 2, 4, 8, 10, 11, 12, 18, and 19; Case 3 corresponds to Components 1, 9, 13, 14, 17, 21, 22, and 23. These classifications are also reflected in Table [6](#table:velcomp).

## Search for redshifted absorption lines

Because QSO J1851+0035 is heavily obscured by the Galactic plane, its optical redshift is unknown. We thus searched for the redshifted absorption lines associated with the QSO host galaxy and intergalactic components as a blind search by using the consolidated spectra in Figure [2](#fig:band35678) and the line identification in Tables [2](#table:mol_data-1)–[5](#table:interference). Only features near 213.57 GHz, 231.61 GHz, 242.28 GHz, 331.06 GHz, and 478.83 GHz remain unidentified. We calculated their frequency ratios to identify the possible pair of redshifted lines since the ratio remains unchanged after the redshift. After comparing them with those of strong absorption lines of CO, HCO$^+$, CN, HCN, and C, we found that none of the possible pairs matched them.

The lack of notable absorption features at $\int \tau dv$ $\sim$ 1 km s$^{-1}$ level in the continuous 84–116 GHz frequency range demonstrates that there is no significant CO absorber in front of this QSO at $0.001 < z < 0.37$ for CO $J$=1–0 and at $0.99 < z < 1.74$ for CO $J$=2–1 with $N$(CO) $\gtrsim 1 \times 10^{14}$ cm$^{-2}$.

# Conclusions

Using ALMA calibration source data and archival data from the NRO 45 m telescope emission line observations, we have reported the results of physical state and chemical composition analyses for about 20 velocity components in the QSO J1851+0035 ($l$=$33.498^{\circ}$, $b$=$+0.194^{\circ}$) direction behind the Galactic plane. Our results are summarized as follows.

1.  A total of 17 species (CO, $^{13}$CO, C$^{18}$O, HCO$^+$, H$^{13}$CO$^+$, HCO, H$_2$CO, HCN, HNC, CN, C$_2$H, $c$-C$_3$H, $c$-C$_3$H$_2$, CS, SO, SiO, and C) were detected in absorption by Galactic molecular gas toward QSO J1851+0035. Upper limits were set for the column densities of CO$^+$, HC$^{18}$O$^+$, HOC$^+$, CH$_3$OH, $^{13}$CN, CN$^-$, H$^{13}$CN, CH$_3$CN, ND, N$_2$H$^+$, $l$-C$_3$H$^+$, SH$^+$, C$^{34}$S, HCS$^+$, H$_2$CS, C$_2$S, SO$_2$, and CF$^+$.

2.  More than 20 velocity components were identified with absorption and emission profiles of CO, $^{13}$CO, and HCO$^+$. Some were further resolved into subcomponents by the multiple-Gaussian fitting of the $J$=1–0 and $J$=2–1 line profiles of CO (and those of $^{13}$CO for components with saturated CO absorption) with fixed centers and line widths. As a result, narrow-line components ($\simeq$0.1 km s$^{-1}$) and broad-line components ($\gtrsim$0.3 km s$^{-1}$) were identified. The excitation temperature of each identified component is approximately 5 K. Components with higher excitation temperatures are those with narrower line widths, which implies that the environment is dense enough for collisional excitation to predominate.

3.  Based on the chemical compositions and the results of previous research, we found a very tight and linear correlation between the column densities within the CN-bearing species (HCN, HNC, CN) and the hydrocarbons (C$_2$H, $c$-C$_3$H, $c$-C$_3$H$_2$). Comparing the column densities of these groups with that of HCO$^+$, we found that the CN-bearing species tend to have reduced abundances at $N$(HCO$^+$) $\lesssim$ 10$^{12}$ cm$^{-2}$.

4.  A large dispersion (up to three orders of magnitude) was observed in the CO and HCO$^+$ column density ratios. This dispersion is attributed to the CO-poor gas, which was predominantly found in low-column-density regions. Such component is often observed as the velocity components with significant HCO$^+$ absorption lines but without significant CO absorption lines in ALMA data, while significant CO emission lines are visible in the Nobeyama 45 m data. The `RADEX` analysis of the absorption data also supports the ubiquity of the CO-poor molecular gas.

5.  The results of the excitation analysis for CO and $^{13}$CO indicate that the excitation temperature of each cloud is below 7 K, meaning that the observed gases are low density. The emission and absorption studies with the Nobeyama 45 m telescope indicate that the excitation temperature of dense gas tracers (HCO$^+$, HCN) toward this line of sight is very low ($\sim$2.9 K).

6.  The $N$(HCO)/$N$(H$^{13}$CO$^+$) ratio, which is thought to increase with UV light, exceeds 10 in the region where $N$(HCO$^+$) is relatively high ($\sim$$10^{12}$ cm$^{-2}$) as in the photodissociation region, suggesting that these molecular gases are in an environment where H$_2$ and C$^+$ are mixed.

7.  One of the velocity components showed absorption of shock wave tracers (SiO and SO) while no YSO-like excitation source was found. The CO excitation temperature was just 6.75$\pm$0.11 K, slightly higher than the other components. This suggests that the shock wave’s impact was not so significant or that the gas cooled rapidly before re-agglomeration into dust.

8.  Discrete narrow-line component, spatial heterogeneity in the beam, and a C$^+$-rich environment require a clumpy structure in the cloud. The presence of broader-line components implies extended gas.

This paper uses the ALMA data tabulated in Appendix [6](#sec:archive). ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. The data are partially obtained from Nobeyama 45m and ASTE Science Data Archive (https://nobeyama-archive.nao.ac.jp/). The Nobeyama 45-m radio telescope is operated by the Nobeyama Radio Observatory, a branch of the National Astronomical Observatory of Japan. Data analysis was carried out on the Multi-wavelength Data Analysis System operated by the Astronomy Data Center (ADC), National Astronomical Observatory of Japan. The ATLASGAL project is a collaboration between the Max-Planck-Gesellschaft, the European Southern Observatory (ESO), and the Universidad de Chile. It includes projects E-181.C-0885, E-078.F-9040(A), M-079.C-9501(A), M-081.C-9501(A) plus Chilean data. JK acknowledges support from NSF through grant AST-2006600. KK acknowledges the support by JSPS KAKENHI Grant Numbers JP17H06130 and JP23K20035. K.N. and Y.Y. were supported by the International Graduate Program for Excellence in Earth-Space Science (IGPEES), The University of Tokyo.

We thank Yuri Aikawa, Shu-ichiro Inutsuka, Yuto Komichi, Daisuke Taniguchi, and Satoshi Yamamoto for fruitful discussions, and Fumiya Maeda for the support of the NRO 45 m telescope observations.

# Facilities

ALMA, NRO 45 m telescope

# Software

CASA

# ALMA archive data used for this study

The list of ALMA archive data used for this study is shown in Tables [7](#table:archive-1a)–[10](#table:archive-3). In these tables, $f_{\rm min}$, $f_{\rm max}$, $\Delta f$, $\theta$, and $\Delta S$ mean the minimum and maximum frequency, the frequency resolution, the angular resolution, and the line sensitivity of the data, respectively.

|  |  |  |  |  |  |  |  |
|:--:|:--:|---:|---:|---:|:--:|:--:|:--:|
| Project Code | ALMA | $f_{\rm min}$ | $f_{\rm max}$ | $\Delta f$ | $\theta$ | $\Delta S$ @10 km s$^{-1}$ | Obs. date |
|  | Band | (GHz) | (GHz) | (kHz) | ($''$) | (mJy beam$^{-1}$) | (yyyy-mm-dd) |
| 2016.1.00010.S | 3 | 109.73 | 109.79 | 30.52 | 0.315 | 0.70 | 2016-10-11 |
|  |  | 110.15 | 110.21 | 30.52 | 0.315 | 0.70 | 2016-10-11 |
|  |  | 115.22 | 115.28 | 30.52 | 0.351 | 1.30 | 2016-10-12 |
|  |  | 115.19 | 115.31 | 61.04 | 0.351 | 1.30 | 2016-10-12 |
| 2016.1.01363.S | 3 | 86.30 | 86.36 | 61.04 | 2.561 | 1.72 | 2017-01-21 |
| 2016.1.01363.S | 3 | 86.30 | 86.36 | 61.04 | 2.561 | 1.72 | 2017-01-21 |
|  |  | 86.71 | 86.77 | 61.04 | 2.561 | 1.72 | 2017-01-21 |
|  |  | 86.81 | 86.86 | 61.04 | 2.561 | 1.72 | 2017-01-21 |
|  |  | 96.70 | 96.76 | 61.04 | 2.561 | 1.60 | 2017-01-21 |
| 2017.1.00501.S | 3 | 84.05 | 84.99 | 564.45 | 0.780 | 1.83 | 2018-01-18 |
|  |  | 84.91 | 85.85 | 564.45 | 0.780 | 1.82 | 2018-01-18 |
|  |  | 85.82 | 86.75 | 564.45 | 0.780 | 1.87 | 2018-01-18 |
|  |  | 86.72 | 87.66 | 564.45 | 0.780 | 1.86 | 2018-01-18 |
|  |  | 87.63 | 88.57 | 564.45 | 0.699 | 2.01 | 2018-01-27 |
|  |  | 88.53 | 89.47 | 564.45 | 0.699 | 2.02 | 2018-01-27 |
|  |  | 89.44 | 90.38 | 564.45 | 0.699 | 2.01 | 2018-01-27 |
|  |  | 90.35 | 91.28 | 564.45 | 0.699 | 2.00 | 2018-01-27 |
|  |  | 91.25 | 92.19 | 564.45 | 1.149 | 1.80 | 2018-03-17 |
|  |  | 92.16 | 93.10 | 564.45 | 1.149 | 1.82 | 2018-03-17 |
|  |  | 93.06 | 94.00 | 564.45 | 1.149 | 1.81 | 2018-03-17 |
|  |  | 93.97 | 94.91 | 564.45 | 1.149 | 1.81 | 2018-03-17 |
|  |  | 94.88 | 95.81 | 564.45 | 1.074 | 1.62 | 2018-03-12 |
|  |  | 95.78 | 96.72 | 564.45 | 1.074 | 1.63 | 2018-03-12 |
|  |  | 96.69 | 97.62 | 564.45 | 1.074 | 1.63 | 2018-03-12 |
|  |  | 97.59 | 98.53 | 564.45 | 1.074 | 1.63 | 2018-03-12 |
|  |  | 98.50 | 99.44 | 564.45 | 1.085 | 2.02 | 2018-03-14 |
|  |  | 99.41 | 100.34 | 564.45 | 1.085 | 1.97 | 2018-03-14 |
|  |  | 100.31 | 101.25 | 564.45 | 1.085 | 1.96 | 2018-03-14 |
|  |  | 101.22 | 102.15 | 564.45 | 1.085 | 1.95 | 2018-03-14 |
|  |  | 102.12 | 103.06 | 564.45 | 1.016 | 1.98 | 2018-03-14 |
|  |  | 103.03 | 103.97 | 564.45 | 1.016 | 1.93 | 2018-03-14 |
|  |  | 103.94 | 104.87 | 564.45 | 1.016 | 1.92 | 2018-03-14 |
|  |  | 104.84 | 105.78 | 564.45 | 1.016 | 1.92 | 2018-03-14 |
|  |  | 105.75 | 106.68 | 564.45 | 1.040 | 2.22 | 2018-03-14 |
|  |  | 106.65 | 107.59 | 564.45 | 1.040 | 2.21 | 2018-03-14 |
|  |  | 107.56 | 108.50 | 564.45 | 1.040 | 2.22 | 2018-03-14 |
|  |  | 108.47 | 109.40 | 564.45 | 1.040 | 2.21 | 2018-03-14 |
|  |  | 109.37 | 110.31 | 564.45 | 0.966 | 2.28 | 2018-03-14 |
|  |  | 110.28 | 111.21 | 564.45 | 0.966 | 2.17 | 2018-03-14 |
|  |  | 111.18 | 112.12 | 564.45 | 0.966 | 2.16 | 2018-03-14 |
|  |  | 112.09 | 113.03 | 564.45 | 0.966 | 2.16 | 2018-03-14 |
|  |  | 112.90 | 113.83 | 564.45 | 0.909 | 2.85 | 2018-03-21 |
|  |  | 113.70 | 114.64 | 564.45 | 0.909 | 2.84 | 2018-03-21 |
|  |  | 114.47 | 115.41 | 564.45 | 0.909 | 3.04 | 2018-03-21 |
|  |  | 114.97 | 115.91 | 564.45 | 0.909 | 3.03 | 2018-03-21 |

: List of ALMA Band 3 data used for this study

|  |  |  |  |  |  |  |  |
|:--:|:--:|---:|---:|---:|:--:|:--:|:--:|
| Project Code | ALMA | $f_{\rm min}$ | $f_{\rm max}$ | $\Delta f$ | $\theta$ | $\Delta S$ @10 km s$^{-1}$ | Obs. date |
|  | Band | (GHz) | (GHz) | (kHz) | ($''$) | (mJy beam$^{-1}$) | (yyyy-mm-dd) |
| 2018.1.00010.S | 3 | 112.89 | 113.36 | 282.23 | 0.759 | 2.18 | 2018-11-27 |
| 2018.1.00101.S | 3 | 88.59 | 88.65 | 61.04 | 3.099 | 2.36 | 2019-03-10 |
| 2018.1.00424.S | 3 | 86.77 | 86.89 | 282.23 | 0.669 | 2.82 | 2019-11-09 |
|  |  | 87.24 | 87.36 | 282.23 | 0.669 | 2.87 | 2018-10-28 |
|  |  | 93.10 | 93.21 | 282.23 | 0.658 | 2.83 | 2018-10-27 |
|  |  | 97.90 | 98.02 | 282.23 | 0.669 | 2.58 | 2018-10-28 |
|  |  | 102.96 | 103.08 | 282.23 | 0.658 | 2.55 | 2018-10-27 |
|  |  | 103.95 | 104.07 | 282.23 | 0.658 | 2.54 | 2018-10-27 |
| 2018.1.00443.S | 3 | 89.10 | 89.22 | 70.56 | 1.982 | 2.03 | 2018-12-20 |
| 2018.1.00850.S | 3 | 90.67 | 90.61 | 61.04 | 2.771 | 2.21 | 2019-01-16 |
| 2018.1.01242.S | 3 | 113.47 | 113.53 | 70.56 | 0.588 | 2.42 | 2018-10-30 |
| 2019.1.00685.S | 3 | 86.72 | 86.78 | 122.07 | 1.487 | 3.15 | 2019-10-31 |
| 2017.1.01248.S | 5 | 191.28 | 191.52 | 564.45 | 0.923 | 1.44 | 2018-05-13 |
|  |  | 191.55 | 191.79 | 564.45 | 0.923 | 1.44 | 2018-05-13 |
|  |  | 191.78 | 192.01 | 564.45 | 0.923 | 1.44 | 2018-05-13 |
|  |  | 192.03 | 192.27 | 564.45 | 0.923 | 1.44 | 2018-05-13 |
|  |  | 192.29 | 192.52 | 564.45 | 0.923 | 1.44 | 2018-05-13 |
|  |  | 192.44 | 192.68 | 564.45 | 0.923 | 1.44 | 2018-05-13 |
|  |  | 193.23 | 193.47 | 564.45 | 0.923 | 1.44 | 2018-05-13 |

: List of ALMA Band 3 and 5 data used for this study (continued)

|  |  |  |  |  |  |  |  |
|:--:|:--:|---:|---:|---:|:--:|:--:|:--:|
| Project Code | ALMA | $f_{\rm min}$ | $f_{\rm max}$ | $\Delta f$ | $\theta$ | $\Delta S$ @10 km s$^{-1}$ | Obs. date |
|  | Band | (GHz) | (GHz) | (kHz) | ($''$) | (mJy beam$^{-1}$) | (yyyy-mm-dd) |
| 2015.1.00072.S | 6 | 237.75 | 238.69 | 564.45 | 0.205 | 1.97 | 2016-08-04 |
|  |  | 256.11 | 256.34 | 484.62 | 0.205 | 1.95 | 2016-08-04 |
|  |  | 256.83 | 257.30 | 484.62 | 0.205 | 1.95 | 2016-08-04 |
| 2015.1.00615.S | 6 | 219.47 | 219.71 | 564.45 | 0.157 | 1.95 | 2016-09-05 |
|  |  | 231.74 | 231.97 | 564.45 | 0.157 | 1.91 | 2016-09-05 |
| 2015.1.01454.S | 6 | 220.22 | 220.28 | 141.11 | 0.175 | 2.06 | 2016-09-11 |
|  |  | 231.59 | 232.06 | 564.45 | 0.175 | 2.02 | 2016-09-11 |
| 2015.1.01571.S | 6 | 212.87 | 213.81 | 969.24 | 0.254 | 1.26 | 2016-08-15 |
| 2016.1.00005.S | 6 | 226.09 | 227.96 | 1938.48 | 1.526 | 2.76 | 2017-03-28 |
|  |  | 229.09 | 230.96 | 1938.48 | 1.526 | 2.59 | 2017-03-28 |
|  |  | 242.07 | 243.94 | 1938.48 | 1.526 | 2.54 | 2017-03-28 |
|  |  | 244.08 | 245.95 | 1938.48 | 1.526 | 2.53 | 2017-03-28 |
| 2016.1.00010.S | 6 | 219.46 | 219.58 | 61.04 | 0.138 | 0.71 | 2016-09-30 |
|  |  | 220.30 | 220.42 | 61.04 | 0.138 | 0.70 | 2016-09-30 |
|  |  | 230.44 | 230.55 | 61.04 | 0.138 | 0.72 | 2016-09-30 |
| 2016.1.01284.S | 6 | 232.56 | 234.43 | 976.56 | 0.536 | 2.47 | 2016-11-22 |
|  |  | 234.56 | 236.43 | 976.56 | 0.536 | 2.46 | 2016-11-22 |
| 2016.1.01346.S | 6 | 215.93 | 217.80 | 488.28 | 1.194 | 2.91 | 2018-05-14 |
|  |  | 217.80 | 219.67 | 488.28 | 1.194 | 2.90 | 2018-05-14 |
| 2017.1.00101.S | 6 | 242.51 | 244.38 | 1953.13 | 0.254 | 1.54 | 2018-09-24 |
|  |  | 244.51 | 246.38 | 1953.13 | 0.254 | 1.52 | 2018-09-24 |
|  |  | 256.51 | 258.38 | 1953.13 | 0.254 | 1.52 | 2018-09-24 |
| 2017.1.01248.S | 6 | 261.60 | 261.84 | 564.45 | 1.040 | 2.37 | 2018-05-15 |
|  |  | 263.78 | 264.02 | 564.45 | 1.040 | 2.37 | 2018-05-15 |
|  |  | 263.97 | 264.20 | 564.45 | 1.040 | 2.37 | 2018-05-15 |
|  |  | 264.25 | 264.49 | 564.45 | 1.040 | 2.37 | 2018-05-15 |
|  |  | 264.55 | 264.78 | 564.45 | 1.040 | 2.37 | 2018-05-15 |
| 2018.1.00632.S | 6 | 225.05 | 226.93 | 2257.81 | 0.043 | 0.89 | 2019-07-18 |
|  |  | 241.05 | 242.93 | 2257.81 | 0.043 | 0.88 | 2019-07-18 |
| 2018.1.00659.L | 6 | 213.83 | 215.70 | 1128.91 | 0.293 | 3.51 | 2018-11-18 |
|  |  | 220.23 | 222.10 | 1128.91 | 0.287 | 3.55 | 2018-11-18 |
|  |  | 223.62 | 225.50 | 1128.91 | 0.287 | 3.52 | 2018-11-18 |
|  |  | 227.22 | 229.10 | 1128.91 | 0.293 | 3.55 | 2018-11-18 |
|  |  | 229.58 | 231.45 | 1128.91 | 0.293 | 3.50 | 2018-11-18 |
|  |  | 235.43 | 237.30 | 1128.91 | 0.287 | 3.41 | 2018-11-18 |
|  |  | 245.34 | 247.21 | 1128.91 | 0.239 | 3.21 | 2018-11-18 |
|  |  | 251.57 | 253.45 | 1128.91 | 0.268 | 3.75 | 2018-11-18 |
|  |  | 253.94 | 255.81 | 1128.91 | 0.268 | 3.74 | 2018-11-18 |
|  |  | 262.09 | 263.03 | 564.45 | 0.239 | 3.00 | 2018-11-18 |
|  |  | 265.52 | 267.39 | 1128.91 | 0.268 | 3.61 | 2018-11-18 |
|  |  | 267.77 | 269.64 | 1128.91 | 0.268 | 3.68 | 2018-11-18 |
| 2019.1.00246.S | 6 | 237.95 | 238.89 | 488.28 | 0.274 | 0.84 | 2021-03-28 |
|  |  | 238.88 | 239.82 | 488.28 | 0.274 | 0.83 | 2021-03-28 |
|  |  | 239.81 | 240.75 | 488.28 | 0.274 | 0.82 | 2021-03-28 |
|  |  | 240.74 | 241.68 | 488.28 | 0.274 | 0.82 | 2021-03-28 |
|  |  | 257.95 | 258.88 | 488.28 | 0.246 | 0.96 | 2021-03-31 |
|  |  | 258.88 | 259.81 | 488.28 | 0.246 | 0.96 | 2021-03-31 |
|  |  | 259.81 | 260.74 | 488.28 | 0.246 | 0.96 | 2021-03-31 |
|  |  | 260.74 | 261.67 | 488.28 | 0.246 | 0.96 | 2021-03-31 |

: List of ALMA Band 6 data used for this study

|  |  |  |  |  |  |  |  |
|:--:|:--:|---:|---:|---:|:--:|:--:|:--:|
| Project Code | ALMA | $f_{\rm min}$ | $f_{\rm max}$ | $\Delta f$ | $\theta$ | $\Delta S$ @10 km s$^{-1}$ | Obs. date |
|  | Band | (GHz) | (GHz) | (kHz) | ($''$) | (mJy beam$^{-1}$) | (yyyy-mm-dd) |
| 2013.1.01035.S | 7 | 278.79 | 278.90 | 122.07 | 0.816 | 2.81 | 2015-04-28 |
|  |  | 279.41 | 279.53 | 122.07 | 0.816 | 2.81 | 2015-04-28 |
|  |  | 288.07 | 288.13 | 141.11 | 0.816 | 2.61 | 2015-04-28 |
|  |  | 289.14 | 289.20 | 141.11 | 0.816 | 2.61 | 2015-04-28 |
|  |  | 289.54 | 289.66 | 244.14 | 0.816 | 2.61 | 2015-04-28 |
|  |  | 290.00 | 290.24 | 282.23 | 0.816 | 2.60 | 2015-04-28 |
|  |  | 290.46 | 290.70 | 282.23 | 0.816 | 2.60 | 2015-04-28 |
| 2015.1.00054.S | 7 | 328.99 | 330.86 | 1128.91 | 0.122 | 5.02 | 2016-08-30 |
|  |  | 330.80 | 331.73 | 3906.25 | 0.122 | 5.02 | 2016-08-30 |
|  |  | 339.92 | 341.79 | 1128.91 | 0.122 | 4.98 | 2016-08-30 |
|  |  | 341.75 | 343.62 | 1128.91 | 0.122 | 5.01 | 2016-08-30 |
| 2015.1.00283.S | 7 | 334.04 | 335.91 | 1938.48 | 0.126 | 2.08 | 2016-08-17 |
|  |  | 336.42 | 336.66 | 282.23 | 0.126 | 2.08 | 2016-08-17 |
|  |  | 336.93 | 337.17 | 282.23 | 0.126 | 2.08 | 2016-08-17 |
|  |  | 345.55 | 346.02 | 282.23 | 0.126 | 2.04 | 2016-08-17 |
|  |  | 346.87 | 347.10 | 282.23 | 0.126 | 2.06 | 2016-08-17 |
|  |  | 347.20 | 347.44 | 282.23 | 0.126 | 2.06 | 2016-08-17 |
| 2015.1.00600.S | 7 | 334.98 | 336.85 | 976.56 | 0.180 | 1.62 | 2016-07-26 |
|  |  | 336.86 | 338.74 | 976.56 | 0.180 | 1.65 | 2016-07-26 |
|  |  | 346.90 | 348.78 | 976.56 | 0.180 | 1.57 | 2016-07-26 |
|  |  | 348.86 | 350.74 | 976.56 | 0.180 | 1.57 | 2016-07-26 |
| 2015.1.01535.S | 7 | 352.63 | 354.50 | 1938.48 | 0.178 | 9.05 | 2016-07-27 |
|  |  | 352.63 | 354.50 | 1938.48 | 0.178 | 9.05 | 2016-07-27 |
|  |  | 365.65 | 367.52 | 1938.48 | 0.178 | 5.73 | 2016-07-27 |
| 2016.1.00071.S | 7 | 333.51 | 335.38 | 1953.13 | 0.811 | 1.79 | 2017-04-04 |
|  |  | 335.47 | 337.34 | 1953.13 | 0.811 | 1.84 | 2017-04-04 |
|  |  | 345.51 | 347.38 | 1953.13 | 0.811 | 1.83 | 2017-04-04 |
|  |  | 347.51 | 349.38 | 1953.13 | 0.811 | 1.90 | 2017-04-04 |
| 2016.1.00988.S | 7 | 358.87 | 360.74 | 1938.48 | 0.989 | 3.28 | 2017-04-04 |
|  |  | 360.01 | 360.13 | 70.56 | 0.989 | 3.28 | 2017-04-04 |
|  |  | 370.86 | 372.73 | 1938.48 | 0.989 | 2.36 | 2017-04-04 |
|  |  | 372.29 | 372.35 | 70.56 | 0.989 | 2.36 | 2017-04-04 |
|  |  | 372.54 | 372.60 | 70.56 | 0.989 | 2.36 | 2017-04-04 |
| 2016.1.01548.S | 7 | 344.86 | 346.73 | 976.56 | 1.067 | 2.31 | 2017-03-24 |
|  |  | 346.40 | 348.27 | 976.56 | 1.067 | 2.44 | 2017-03-24 |
| 2017.1.00377.S | 7 | 336.31 | 337.25 | 564.45 | 0.470 | 2.37 | 2018-04-04 |
|  |  | 337.24 | 338.18 | 564.45 | 0.470 | 2.30 | 2018-04-04 |
|  |  | 338.17 | 339.11 | 564.45 | 0.470 | 2.29 | 2018-04-04 |
|  |  | 339.16 | 340.10 | 564.45 | 0.470 | 2.29 | 2018-04-04 |
| 2018.1.00024.S | 7 | 320.90 | 321.37 | 282.23 | 0.074 | 2.18 | 2019-08-20 |
|  |  | 321.50 | 323.38 | 1128.91 | 0.074 | 2.55 | 2019-08-20 |
|  |  | 333.00 | 334.88 | 1128.91 | 0.074 | 2.53 | 2019-08-20 |
|  |  | 334.90 | 336.77 | 1128.91 | 0.074 | 2.52 | 2019-08-20 |
| 2018.1.00190.S | 8 | 476.98 | 477.92 | 1952.15 | 0.221 | 8.90 | 2019-04-27 |
|  |  | 477.84 | 479.71 | 1938.48 | 0.221 | 8.75 | 2019-04-27 |
|  |  | 489.84 | 491.71 | 1938.48 | 0.221 | 7.80 | 2019-04-27 |
|  |  | 491.64 | 492.57 | 1952.15 | 0.221 | 7.80 | 2019-04-27 |

: List of ALMA Band 7 and 8 data used for this study

# Absorption profiles of individual species

Here, we summarize the absorption profiles of individual species, including their hyperfine components in Figures [27](#fig:co_abs)–[32](#fig:cs_abs) for several species groups.

# Nature of absorption host clouds

## Spatial distribution in CO and $^{13}$CO emission lines

The spatial distribution of molecular gas in CO and $^{13}$CO emission lines is examined to understand the nature of the parent molecular clouds. In Figures [33](#fig:fugin_12co)–[34](#fig:fugin_13co), velocity channel maps of the $0.5^{\circ}$$\times$$0.5^{\circ}$ area centered at the line of sight toward QSO J1851+0035 are shown for CO and $^{13}$CO $J$=1–0 emission. The area corresponds to 43.6 pc$\times$43.6 pc in a linear scale at the distance of 5 kpc. Because the dense part of molecular clouds tends to occupy a small spacial fraction, the line of sight toward the QSO penetrates cloud envelopes in most cases. The brightness and the spatial distribution, including the degree of structurization, are used to classify the parent molecular clouds.

## Physical conditions of molecular gas deduced from emission studies

The observations with the FOREST receiver of the NRO 45 m telescope provided the line profiles of HCO$^+$, HCN, HNC, and C$_2$H toward three more lines of sight with offsets of ($\Delta$RA, $\Delta$DEC) = ($0''$, $+50''$), ($+50''$, $+50''$), ($+50''$, $0''$) from the pointing center (RA=18:51:46.723, DEC=+00:35:32.364). Since the line of sight toward the QSO is affected by continuum and is not ideal for emission line studies, we also analyzed the adjacent beams and compared the line profiles of CO, $^{13}$CO, HCO$^+$, HCN, HNC, and C$_2$H data (Figure [35](#fig:dense_core)). For the saturated CO absorbers, $T_{\rm b}$(CO)/$T_{\rm b}$(HCO$^+$) $>$ 100, $T_{\rm b}$(CO)/$T_{\rm b}$($^{13}$CO) $\sim$ 8, and $T_{\rm b}$(CO) $\sim$ 5 K. Comparison with the non-LTE calculation assuming an expanding sphere in `RADEX` suggests a number density of $\sim$300 cm$^{-3}$ at most.

## Association with HII regions

The position, velocity, and the near-far ambiguity solution of known HII regions taken from the HII Region Discovery Survey (cite: 2011ApJS..194...32A; 2012ApJ...754...62A) and references therein are summarized in Table [11](#table:hrds).

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:---|
| Name | $l$ | $b$ | $v_{\rm LSR}$ | N/F/T | References |
|  | ($^{\circ}$) | ($^{\circ}$) | (km s$^{-1}$) |  |  |
| G033.810$-$00.190 | 33.810 | $-$0.190 | 40.3 |  | (cite: 2003ApJ...587..714W) |
| G033.882$+$0.057 | 33.882 | $+$0.057 | 40.8 | F | HRDS |
| G033.810$-$0.154 | 33.810 | $-$0.154 | 50.0 | F | HRDS |
| G033.943$-$00.036 | 33.943 | $-$0.036 | 57.2 |  | (cite: 1996ApJ...472..173L) |
| G033.994$-$0.006 | 33.994 | $-$0.006 | 59.0 |  | HRDS |
| G033.418$-$00.004 | 33.418 | $-$0.004 | 76.5 |  | (cite: 1989ApJS...71..469L) |
| G033.091$+$0.073 | 33.091 | $+$0.073 | 86.9 | F | HRDS |
| G033.130$-$00.090 | 33.130 | $-$0.090 | 87.4 |  | (cite: 2002ApJS..138...63A) |
| G033.265$+$0.068 | 33.265 | $+$0.068 | 98.3 | T | HRDS |
| G033.920$+$00.110 | 33.920 | $+$0.110 | 99.0 |  | (cite: 2002ApJS..138...63A) |
| G033.753$-$0.063 | 33.753 | $-$0.063 | 101.7 | N | HRDS |
| G033.645$-$0.227 | 33.645 | $-$0.227 | 102.9 | T | HRDS |
| G033.200$-$00.010 | 33.200 | $-$0.010 | 105.8 |  | (cite: 2003ApJ...587..714W) |

: HII regions near the line of sight toward QSO J1851+0035

## Association with ATLASGAL sources

The position and LSR velocity of ATLASGAL GaussClump Source Catalogue (GCSC) sources (cite: 2014A&A...565A..75C)

|                    |               |
|:------------------:|:-------------:|
|      ATLASGAL      | $v_{\rm LSR}$ |
|     GCSC Name      | (km s$^{-1}$) |
| G033.3883$+$0.1670 |     9.43      |
| G033.7142$+$0.2557 |     36.27     |
| G033.7038$+$0.2832 |     37.23     |
| G033.6744$+$0.2028 |     39.90     |
| G033.6092$+$0.2305 |     41.90     |
| G033.4306$-$0.0143 |     73.76     |
| G033.4025$-$0.0032 |     73.78     |
| G033.4160$-$0.0030 |     75.10     |
| G033.4196$+$0.1249 |     83.10     |
| G033.5185$-$0.0575 |     84.68     |
| G033.3376$+$0.1655 |     84.80     |
| G033.3883$+$0.1984 |     85.29     |
| G033.2645$+$0.0670 |     98.79     |
| G033.2868$-$0.0190 |     99.20     |
| G033.2058$-$0.0088 |     99.96     |
| G033.2093$+$0.0023 |     99.96     |
| G033.2278$-$0.0179 |    100.44     |
| G033.2371$-$0.0214 |    100.44     |
| G033.2011$+$0.0194 |    101.20     |
| G033.4941$-$0.0138 |    102.20     |
| G033.6546$-$0.0204 |    102.67     |
| G033.5236$+$0.0195 |    103.30     |
| G033.6377$-$0.0345 |    103.47     |
| G033.6218$-$0.0335 |    103.60     |
| G033.6488$-$0.0273 |    103.60     |
| G033.4173$+$0.0319 |    103.70     |
| G033.3860$+$0.0020 |    103.86     |
| G033.3917$+$0.0099 |    103.86     |
| G033.6326$-$0.0227 |    104.45     |
| G033.7578$-$0.0029 |    104.54     |
| G033.7394$-$0.0197 |    104.70     |
| G033.5685$+$0.0272 |    105.65     |
| G033.7425$+$0.0029 |    106.65     |
| G033.7440$-$0.0074 |    106.65     |
| G033.4526$-$0.0810 |    109.20     |

: ATLASGAL sources near the line of sight toward QSO J1851+0035

are summarized in Table [12](#table:atlasgal). The position and LSR velocity of ATLASGAL GaussClump Source Catalogue (GCSC) sources (cite: 2014A&A...565A..75C) are summarized in Table [12](#table:atlasgal). Note that the ATLASGAL GCSC sources are candidate compact submillimeter sources that can potentially host precursors to high-mass stars.

## Association with dense gas

Emission line profiles of CO, $^{13}$CO, HCO$^+$, HCN, HNC, and C$_2$H toward ($\Delta$RA, $\Delta$DEC) = ($+50''$, $+50''$) are shown in Figure [35](#fig:dense_core) as an example. No emission was detected in these lines except in the velocity range corresponding to Component 17.

Model calculation results of multi-line analysis of CO, $^{13}$CO, and HCO$^+$ are shown in Figures [36](#fig:radex_norm) and [37](#fig:radex_poor). The CO main beam antenna temperature, $T_{\rm mb}$(CO), and the line intensity ratios, $T_{\rm mb}$(CO)/$T_{\rm mb}$($^{13}$CO) and $T_{\rm mb}$(CO)/$T_{\rm mb}$(HCO$^+$), were calculated as functions of $T_{\rm k}$ and $n$(H$_2$) for different values of $X$(CO)/($dv/dr$) using `ndradex` (cite: ndradex) developed based on `RADEX` (cite: 2007A&A...468..627V). The beam-filling factor was assumed to be unity.

In Figure [36](#fig:radex_norm), the velocity gradient $dv/dr$ was fixed at 1.0 $\rm km~s^{-1}~pc^{-1}$, and the abundances of CO and $^{13}$CO were set at $X$(CO) = $1 \times 10^{-4}$ and $X$($^{13}$CO) = $2 \times 10^{-6}$ as canonical values for Galactic disk clouds (cite: 2008ApJ...679..481P). The abundance of HCO$^+$ was set at $X$(HCO$^+$) = $3 \times 10^{-9}$, which is the recommended value for diffuse gas in the Galactic disk (cite: 2023ApJ...943..172L). This value is consistent with the results for low-density ($<$$10^3$ cm$^{-3}$) regions in star-forming clouds (cite: 2021A&A...648A.120R).

For the velocity components with relatively high CO brightness, we obtained $T_{\rm mb}$(CO)/$T_{\rm mb}$(HCO$^+$) $>$ 100, $T_{\rm mb}$(CO)/$T_{\rm mb}$($^{13}$CO) $\sim$ 8, and $T_{\rm mb}$(CO) $\sim$ 5 K. Typical molecular gas with $n$(H$_2$) $\sim 1 \times 10^3$ cm$^{-3}$ accounts for these parameters.

If we half the $X$(CO) value to $5 \times 10^{-5}$ so that it is consistent with the CO/$^{13}$CO isotopologue ratio of 25 assumed for saturated CO absorbers, the contours go down so that their intercepts with the vertical axis are reduced by a factor of 1/1.4. This will not have a critical impact on the above-deduced values.

For the nearby emission feature that corresponds to Component 17, we obtained $T_{\rm mb}$(CO)/$T_{\rm mb}$(HCO$^+$) $\sim$ 5, $T_{\rm mb}$(CO)/$T_{\rm mb}$($^{13}$CO) $\sim$ 50, and $T_{\rm mb}$(CO) $\sim$ 2.5 K. The extremely low $T_{\rm mb}$(CO)/$T_{\rm mb}$(HCO$^+$) value prefers high density, but there is no solution with the canonical values of $X$(CO), $X$($^{13}$CO), and $X$(HCO$^+$). The large $T_{\rm mb}$(CO)/$T_{\rm mb}$($^{13}$CO) close to the isotopologue ratio requires even CO emission to be optically thin. Because the reduction of the CO abundance will make the CO emission optically thinner, enhance the $T_{\rm mb}$(CO)/$T_{\rm mb}$(HCO$^+$) ratio, and reduce the $T_{\rm mb}$(CO), the CO-poor environment will explain the observed results. The `RADEX` calculation with 100 times poorer CO and $^{13}$CO abundances demonstrates a parameter space at $n$(H$_2$) $\sim  1 \times 10^3$ cm$^{-3}$ and $T_{\rm k}$ $\gtrsim$ 30 K that accounts for the observed parameters (Figure [37](#fig:radex_poor)). Note that Component 17 is one of the most prominent velocity components with notable HCO$^+$ absorption but without CO absorption (Figure [3](#fig:em_abs)) and the CO/HCO$^+$ abundance ratio was measured as small as $<$3 as shown in Tables [\[table:col_co_abs\]](#table:col_co_abs) and [\[table:col_hco+\_hnc\]](#table:col_hco+_hnc). The abnormal line ratios observed in this adjacent area suggest that the CO-poor gas is extended.

# Reliability of H$_2$ column density from $^{13}$CO $J$=1–0 emission studies

Here we examine the reliability of the H$_2$ column density of diffuse gas extracted from $^{13}$CO $J$=1–0 emission studies.

The brightness temperature $T_{\rm{b}}$ for the specific intensity $I_{\nu}$ is defined by $$\begin{equation}
\label{eq:d1}
T_{\rm{b}} \equiv \frac{c^2}{2 \nu^2 k_{\rm{B}}}I_{\nu}. 
\end{equation}$$ For black body radiation, $T_{\rm{b}}$ agrees with the temperature of the black body under the Rayleigh-Jeans approximation.

If the background radiation with $T_{\rm{bg}}$ propagates through a uniform medium with its excitation temperature $T_{\rm{ex}}$ and opacity $\tau$, the radiative transfer equation gives $$\begin{equation}
\label{eq:d2}
T_{\rm{b}} = \left(\frac{h\nu/k_{\rm{B}}}{\exp({h\nu/k_{\rm{B}} T_{\rm{bg}})} - 1}\right)e^{-\tau} + \left(\frac{h\nu/k_{\rm{B}}}{\exp({h\nu/k_{\rm{B}} T_{\rm{ex}})} - 1}\right) (1-e^{-\tau}).
\end{equation}$$

If the medium occupies only a limited fraction $f$ of the telescope beam (beam-filling factor), $$\begin{equation}
\label{eq:d3}
\begin{split} 
T_{\rm{b}} & = f \left[\left(\frac{h\nu/k_{\rm{B}}}{\exp({h\nu/k_{\rm{B}} T_{\rm{bg}})} - 1}\right)e^{-\tau} + \left(\frac{h\nu/k_{\rm{B}}}{\exp({h\nu/k_{\rm{B}} T_{\rm{ex}})} - 1}\right) (1-e^{-\tau})\right] + (1-f)\left(\frac{h\nu/k_{\rm{B}}}{\exp({h\nu/k_{\rm{B}} T_{\rm{bg}})} - 1}\right) \\
& = f(1-e^{-\tau}) \left(\frac{h\nu/k_{\rm{B}}}{\exp({h\nu/k_{\rm{B}} T_{\rm{ex}})} - 1} - \frac{h\nu/k_{\rm{B}}}{\exp({h\nu/k_{\rm{B}} T_{\rm{bg}})} - 1}\right) + \left(\frac{h\nu/k_{\rm{B}}}{\exp({h\nu/k_{\rm{B}} T_{\rm{bg}})} - 1}\right).
\end{split} 
\end{equation}$$ In the position-switching observations, we usually measure the enhanced intensity over the uniform background, and the last term of Equation [\[eq:d3\]](#eq:d3) is eliminated to yield the main beam antenna temperature $T_{\rm{mb}}$ as $$\begin{equation}
\label{eq:d4}
T_{\rm{mb}} = f(1-e^{-\tau}) \left(\frac{h\nu/k_{\rm{B}}}{\exp({h\nu/k_{\rm{B}} T_{\rm{ex}})} - 1} - \frac{h\nu/k_{\rm{B}}}{\exp({h\nu/k_{\rm{B}} T_{\rm{bg}})} - 1}\right) = f_{\rm{d}} \left(\frac{h\nu/k_{\rm{B}}}{\exp({h\nu/k_{\rm{B}} T_{\rm{ex}})} - 1} - \frac{h\nu/k_{\rm{B}}}{\exp({h\nu/k_{\rm{B}} T_{\rm{bg}})} - 1}\right).
\end{equation}$$ Here the dilution factor is defined as $f_{\rm{d}} \equiv f(1-e^{-\tau})$. In Equation [\[eq:d4\]](#eq:d4), only $T_{\rm{mb}}$ and $\tau$ are considered as variables as functions of velocity for each velocity component.

The excitation temperature $T_{\rm{ex}}$ is then related to $T_{\rm{mb}}$ and $f_{\rm{d}}$ as $$\begin{equation}
\label{eq:d5}
T_{\rm{ex}} = \frac{h \nu}{k_{\rm{B}}}\left[\ln \left(1 + \frac{1}{\frac{k_{\rm{B}}}{h \nu}\frac{T_{\rm{mb}}}{f_{\rm{d}}} +\frac{1}{\exp({h \nu / k_{\rm{B}} T_{\rm{bg}})-1}}}\right)\right]^{-1}. 
\end{equation}$$

For optically thick ($\tau \gg 1$) and beam-filling ($f = 1$) emission, $f_{\rm{d}}$ nearly equals to unity. However, if $f_{\rm{d}}$ is significantly smaller than unity as is expected for the $^{13}$CO $J$=1–0 emission and even for the CO $J$=1–0 emission toward diffuse gas, the observed $T_{\rm{mb}}$ shall be corrected for $f_{\rm{d}}$, and the analysis without this correction will severely underestimate $T_{\rm{ex}}$.

Next, we deduce the column density $N$. For optically thin emission, $\tau \simeq 1-e^{-\tau}$, and Equation [\[eq:d4\]](#eq:d4) is transformed to, $$\begin{equation}
\label{eq:d6}
1-e^{-\tau} = \frac{k_{\rm{B}}}{h\nu} \frac{T_{\rm{mb}}}{f} \left(\frac{1}{\exp({h\nu/k_{\rm{B}} T_{\rm{ex}})} - 1} - \frac{1}{\exp({h\nu/k_{\rm{B}} T_{\rm{bg}})} - 1}\right)^{-1}.
\end{equation}$$ Then Equation [\[eq:n_tot\]](#eq:n_tot) is approximated by, $$\begin{equation}
\label{eq:d7}
\begin{split} 
N & \simeq \frac{3hQ(T_{\rm ex})}{8\pi^3\mu^2S_{\rm ul}} 
\frac{\exp(\frac{E_{\rm l}}{k_{\rm B} T_{\rm ex}})} {[1-\exp(\frac{-h\nu}{k_{\rm B}T_{\rm ex}})]} 
\int (1-e^{-\tau})\ dv \\ 
& = \frac{3hQ(T_{\rm ex})}{8\pi^3\mu^2S_{\rm ul}} 
\frac{\exp(\frac{E_{\rm l}}{k_{\rm B} T_{\rm ex}})} {[1-\exp(\frac{-h\nu}{k_{\rm B}T_{\rm ex}})]} 
\frac{k_{\rm B}}{h\nu} 
\left(\frac{1}{\exp({h\nu/k_{\rm{B}}T_{\rm{ex}})}-1} - \frac{1}{\exp({h\nu/k_{\rm{B}}T_{\rm{bg}})}-1}\right)^{-1} 
\int \frac{T_{\rm{mb}}}{f}\ dv, 
\end{split} 
\end{equation}$$

For pure rotation of a diatomic rotor like CO, the partition function $Q(T_{\rm ex})$ can be calculated as the sum of the populations of all energy levels $E_{\rm l}$ (= $\frac{1}{2}E_{J=1} J(J+1)$) degenerated by $g_{\rm u}$ (= $2J+1$), $$\begin{equation}
\label{eq:d8}
Q(T_{\rm ex}) = \sum_{J=0}^{\infty} g_{\rm u} \exp \left(-\frac{E_{\rm l}}{k_{\rm{B}}T_{\rm ex}}\right), 
\end{equation}$$ and we performed a direct sum over all energy levels obtained from CDMS for each $T_{\rm ex}$.

For $^{13}$CO $J$=1–0 emission, $h\nu/k_{\rm{B}}$ = 5.29 K, $E_{\rm l}$ = 0 K. By assuming $T_{\rm{bg}}$ = $T_{\rm{CMB}}$ = 2.73 K, we derive the $^{13}$CO column density from its optically thin $J$=1–0 emission as, $$\begin{equation}
\label{eq:d9}
N({\rm ^{13}CO}) \simeq 
\frac{3.29 \times 10^{14}}{5.29\ {\rm K}}
\frac{Q(T_{\rm ex})}{[1-\exp(-5.29\ {\rm K}/T_{\rm ex})]} 
\left(\frac{1}{\exp(5.29\ {\rm K}/T_{\rm ex})-1}-0.168\right)^{-1}
\int \frac{T_{\rm{mb}}}{f}\ dv \ 
{\rm cm^{-2}~(km~s^{-1})^{-1}}.
\end{equation}$$

In the case of $k_{\rm{B}}T_{\rm ex}/E_{\rm l} \gg 1$, Equation [\[eq:d8\]](#eq:d8) can be approximated by, $$\begin{equation}
\label{eq:d10}
Q(T_{\rm ex})  \simeq \int_{0}^{\infty} g_{\rm u} \exp \left(-\frac{E_{\rm l}}{k_{\rm{B}}T_{\rm ex}}\right)dJ
= \int_{0}^{\infty} (2J+1) \exp \left(-\frac{E_{J=1} J(J+1)}{2k_{\rm{B}}T_{\rm ex}}\right)dJ
=\frac{2k_{\rm{B}}T_{\rm ex}}{E_{J=1}}=\frac{2k_{\rm{B}}T_{\rm ex}}{h\nu}.
\end{equation}$$

$$\begin{equation}
\label{eq:d11}
\begin{split} 
N({\rm ^{13}CO}) & \simeq 
\frac{3.29 \times 10^{14}}{5.29\ {\rm K}}
\frac{2 T_{\rm ex}/5.29\ {\rm K}}{[1-\exp(-5.29\ {\rm K}/T_{\rm ex})]} 
\left(\frac{\exp(-5.29\ {\rm K}/T_{\rm ex})}{1-\exp(-5.29\ {\rm K}/T_{\rm ex})}-0.168\right)^{-1}
\int \frac{T_{\rm{mb}}}{f}\ dv \ 
{\rm cm^{-2}~(km~s^{-1})^{-1}} \\
& \simeq 
\frac{6.58 \times 10^{14}}{5.29\ {\rm K}}
\frac{T_{\rm ex}/5.29\ {\rm K}}{5.29\ {\rm K}/T_{\rm ex}} 
\left(\frac{1}{5.29\ {\rm K}/T_{\rm ex}}-0.168\right)^{-1}
\int \frac{T_{\rm{mb}}}{f}\ dv \ 
{\rm cm^{-2}~(km~s^{-1})^{-1}} \\
& = 
1.24 \times 10^{14} 
\left(\frac{T_{\rm ex}}{5.29\ {\rm K}}\right)^2
\left(\frac{T_{\rm ex}}{5.29\ {\rm K}}-0.168\right)^{-1}
\int \frac{T_{\rm{mb}}}{f}\ dv \ 
{\rm cm^{-2}~(K~km~s^{-1})^{-1}}.
\end{split} 
\end{equation}$$

Now we need a good estimate of the $^{13}$CO excitation temperature $T_{\rm{ex,13}}$ and $f$ because both of them almost linearly affect the column density. However, it is hard to estimate $T_{\rm{ex,13}}$ from $T_{\rm{mb,13}}$ with Equation [\[eq:d5\]](#eq:d5) because $^{13}$CO $J$=1–0 emission is not optically thick for most of the molecular gas in the Galaxy. Instead, it is often assumed that $T_{\rm{ex,13}}$ is the same as $T_{\rm{ex,12}}$, and the CO $J$=1–0 emission is optically thick and beam-filling ($f_{\rm{d}} \simeq 1$). Under this assumption, Equation [\[eq:d5\]](#eq:d5) is approximated as, $$\begin{equation}
\label{eq:d12}
T_{\rm{ex,13}} \simeq T_{\rm{ex,12}} \simeq \frac{h\nu}{k_{\rm{B}}}\left[\ln \left(1 + \frac{1}{\frac{k_{\rm{B}}T_{\rm{mb,12}}}{h\nu} +\frac{1}{\exp({h\nu/k_{\rm{B}} T_{\rm{bg}})-1}}}\right)\right]^{-1}. 
\end{equation}$$

In reality, the above assumptions are never met at the same time for diffuse gas since we expect $T_{\rm{ex,12}}/T_{\rm{ex,13}} > 1$ because of the photon trapping effect that selectively enhances the excitation of optically thicker line. For diffuse and warm molecular gas with $T_{\rm{k}}$ = 50 K, $n$(H$_2$) = $3 \times 10^2$ cm$^{-3}$, $dv/dr$ = 1.0 $\rm km~s^{-1}~pc^{-1}$, and the canonical values of $X$(CO) = $1 \times 10^{-4}$ and $X$($^{13}$CO) = $2 \times 10^{-6}$ for Galactic disk clouds (cite: 2008ApJ...679..481P), the `RADEX` calculation results in Figure [24](#fig:radex_Xco_abundance) show that $T_{\rm{ex,12}} \simeq$ 20 K and $T_{\rm{ex,13}} \simeq$ 7 K to yield $T_{\rm{ex,12}}/T_{\rm{ex,13}} \simeq 3$. Thus the assumption of $T_{\rm{ex,13}} \simeq T_{\rm{ex,12}}$ overestimates $N$ accordingly.

For CO-poor components with the same physical conditions but with 100 times lower $X$(CO) and $X$($^{13}$CO), the photon-trapping effect for CO becomes less significant and $T_{\rm{ex,12}} \simeq$ 7.0 K and $T_{\rm{ex,13}} \simeq$ 6.2 K yield $T_{\rm{ex,12}}/T_{\rm{ex,13}} \simeq 1.1$. However, even the CO $J$=1–0 emission is not optically thick ($1-e^{-\tau_{12}} \simeq 0.2$), and $T_{\rm{ex,12}}$ from $T_{\rm{mb,12}}$ will be underestimated accordingly, resulting in underestimation of $N$($^{13}$CO). Since the H$_2$ column density is derived with $N({\rm H_2}) \equiv N({\rm ^{13}CO})/X({\rm ^{13}CO})$ by assuming $X$($^{13}$CO), which is $2 \times 10^{-6}$ as a canonical value for Galactic disk clouds (cite: 2008ApJ...679..481P) but may be smaller by 2–3 orders under diffuse environment as was shown in this study, the assumption of canonical $X$($^{13}$CO) will further underestimate $N({\rm H_2})$ by the same 2–3 orders.

Estimation of the beam-filling factor $f$ is an additional challenge, particularly in cloud edges. If it is not unity, $T_{\rm{ex}}$ in Equations [\[eq:d5\]](#eq:d5) and [\[eq:d11\]](#eq:d11) is underestimated, and the assumption of $f = 1$ in Equation [\[eq:d7\]](#eq:d7) further underestimate the column density. In case we are interested only in the column density averaged over the telescope beam $fN$, the latter effect is canceled.

Regarding the validity of the Rayleigh-Jeans approximation, the assumption of $T_{\rm{ex}} \gg h\nu/k_{\rm{B}}$ often fails because of the large $h\nu/k_{\rm{B}}$ for CO and low $T_{\rm{ex}}$ under diffuse environment. For $T_{\rm{ex}}$ = $h\nu/k_{\rm{B}}$ = 5.29 K and $T_{\rm{bg}}$ = $T_{\rm{CMB}}$ = 2.73 K, it gives $T_{\rm{mb}}/f_{\rm{d}} = (T_{\rm{ex}}-T_{\rm{bg}})$ = 2.56 K while it shall be 2.18 K. In other words, if we analyze the measured $T_{\rm{mb}}$ based on the Rayleigh-Jeans approximation, we will slightly underestimate $T_{\rm{ex}}$ accordingly.

To conclude this section, $N$(H$_2$) of diffuse gas extracted from $^{13}$CO $J$=1–0 emission study is highly doubtful and is often severely underestimated, and even the order estimation may not be relevant. Care must be taken to set an upper limit to the diffuse molecular gas mass from such studies.

natexlab

(ref: 2010A&A...517L...2A) Agúndez, M., Cernicharo, J., Guélin, M., et al. 2010, A&A, 517, L2, doi: [`10.1051/0004-6361/201015186`](http://doi.org/10.1051/0004-6361/201015186)

(ref: 2011ApJS..194...32A) Anderson, L. D., Bania, T. M., Balser, D. S., & Rood, R. T. 2011, ApJS, 194, 32, doi: [`10.1088/0067-0049/194/2/32`](http://doi.org/10.1088/0067-0049/194/2/32)

(ref: 2012ApJ...754...62A) —. 2012, ApJ, 754, 62, doi: [`10.1088/0004-637X/754/1/62`](http://doi.org/10.1088/0004-637X/754/1/62)

(ref: 2016PASJ...68....6A) Ando, R., Kohno, K., Tamura, Y., et al. 2016, PASJ, 68, 6, doi: [`10.1093/pasj/psv110`](http://doi.org/10.1093/pasj/psv110)

(ref: 1997ApJ...481..800A) Apponi, A. J., & Ziurys, L. M. 1997, ApJ, 481, 800, doi: [`10.1086/304080`](http://doi.org/10.1086/304080)

(ref: 2002ApJS..138...63A) Araya, E., Hofner, P., Churchwell, E., & Kurtz, S. 2002, ApJS, 138, 63, doi: [`10.1086/324021`](http://doi.org/10.1086/324021)

(ref: 2022MNRAS.511.3832A) Awad, Z., & Viti, S. 2022, MNRAS, 511, 3832, doi: [`10.1093/mnras/stac297`](http://doi.org/10.1093/mnras/stac297)

(ref: 2016A&A...587A..26B) Bacmann, A., Daniel, F., Caselli, P., et al. 2016, A&A, 587, A26, doi: [`10.1051/0004-6361/201526084`](http://doi.org/10.1051/0004-6361/201526084)

(ref: 2013ARA&A..51..207B) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: 2009ApJ...690L.130B) Bottinelli, S., Hughes, A. M., van Dishoeck, E. F., et al. 2009, ApJL, 690, L130, doi: [`10.1088/0004-637X/690/2/L130`](http://doi.org/10.1088/0004-637X/690/2/L130)

(ref: 2020ApJ...896..130C) Chacko, R., Banhatti, S., Barik, S., & Aravind, G. 2020, ApJ, 896, 130, doi: [`10.3847/1538-4357/ab8fb1`](http://doi.org/10.3847/1538-4357/ab8fb1)

(ref: 2009PASP..121..213C) Churchwell, E., Babler, B. L., Meade, M. R., et al. 2009, PASP, 121, 213, doi: [`10.1086/597811`](http://doi.org/10.1086/597811)

(ref: 2008Ap&SS.313..321C) Combes, F. 2008, Ap&SS, 313, 321, doi: [`10.1007/s10509-007-9632-3`](http://doi.org/10.1007/s10509-007-9632-3)

(ref: 2018A&A...610A..10C) Corby, J. F., McGuire, B. A., Herbst, E., & Remijan, A. J. 2018, A&A, 610, A10, doi: [`10.1051/0004-6361/201730988`](http://doi.org/10.1051/0004-6361/201730988)

(ref: 2014A&A...565A..75C) Csengeri, T., Urquhart, J. S., Schuller, F., et al. 2014, A&A, 565, A75, doi: [`10.1051/0004-6361/201322434`](http://doi.org/10.1051/0004-6361/201322434)

(ref: 1986ApJ...310..408D) Draine, B. T. 1986, ApJ, 310, 408, doi: [`10.1086/164694`](http://doi.org/10.1086/164694)

(ref: 2015MNRAS.447.1242D) Duley, W. W., Zaidi, A., Wesolowski, M. J., & Kuzmin, S. 2015, MNRAS, 447, 1242, doi: [`10.1093/mnras/stu2508`](http://doi.org/10.1093/mnras/stu2508)

(ref: 2000ESASP.456...91F) Fossé, D., Cesarsky, D., Gerin, M., Lequeux, J., & Tiné, S. 2000, in ESA Special Publication, Vol. 456, ISO Beyond the Peaks: The 2nd ISO Workshop on Analytical Spectroscopy, ed. A. Salama, M. F. Kessler, K. Leech, & B. Schulz, 91

(ref: 2003A&A...406..899F) Fuente, A., Rodrıguez-Franco, A., Garcıa-Burillo, S., Martın-Pintado, J., & Black, J. H. 2003, A&A, 406, 899, doi: [`10.1051/0004-6361:20030712`](http://doi.org/10.1051/0004-6361:20030712)

(ref: Fuente2019) Fuente, A., Navarro, D. G., Caselli, P., et al. 2019, A&A, 624, A105, doi: [`10.1051/0004-6361/201834654`](http://doi.org/10.1051/0004-6361/201834654)

(ref: 2009A&A...494..977G) Gerin, M., Goicoechea, J. R., Pety, J., & Hily-Blant, P. 2009, A&A, 494, 977, doi: [`10.1051/0004-6361:200810933`](http://doi.org/10.1051/0004-6361:200810933)

(ref: 2011A&A...525A.116G) Gerin, M., Kaźmierczak, M., Jastrzebska, M., et al. 2011, A&A, 525, A116, doi: [`10.1051/0004-6361/201015050`](http://doi.org/10.1051/0004-6361/201015050)

(ref: 2021A&A...648A..38G) Gerin, M., & Liszt, H. 2021, A&A, 648, A38, doi: [`10.1051/0004-6361/202039915`](http://doi.org/10.1051/0004-6361/202039915)

(ref: 2019A&A...622A..26G) Gerin, M., Liszt, H., Neufeld, D., et al. 2019, A&A, 622, A26, doi: [`10.1051/0004-6361/201833661`](http://doi.org/10.1051/0004-6361/201833661)

(ref: 2010A&A...520A..20G) Godard, B., Falgarone, E., Gerin, M., Hily-Blant, P., & de Luca, M. 2010, A&A, 520, A20, doi: [`10.1051/0004-6361/201014283`](http://doi.org/10.1051/0004-6361/201014283)

(ref: 2012A&A...540A..87G) Godard, B., Falgarone, E., Gerin, M., et al. 2012, A&A, 540, A87, doi: [`10.1051/0004-6361/201117664`](http://doi.org/10.1051/0004-6361/201117664)

(ref: refId0) Godard, B., Falgarone, E., Gerin, M., Hily-Blant, P., & De Luca, M. 2010, A&A, 520, A20, doi: [`10.1051/0004-6361/201014283`](http://doi.org/10.1051/0004-6361/201014283)

(ref: 2016ApJS..225...25G) Gratier, P., Majumdar, L., Ohishi, M., et al. 2016, ApJS, 225, 25, doi: [`10.3847/0067-0049/225/2/25`](http://doi.org/10.3847/0067-0049/225/2/25)

(ref: 2015ApJ...800L..33G) Guzmán, V. V., Pety, J., Goicoechea, J. R., et al. 2015, ApJL, 800, L33, doi: [`10.1088/2041-8205/800/2/L33`](http://doi.org/10.1088/2041-8205/800/2/L33)

(ref: 2020A&A...635A...4H) Hacar, A., Bosman, A. D., & van Dishoeck, E. F. 2020, A&A, 635, A4, doi: [`10.1051/0004-6361/201936516`](http://doi.org/10.1051/0004-6361/201936516)

(ref: 1987ApJ...317..926H) Hawkins, I., & Jura, M. 1987, ApJ, 317, 926, doi: [`10.1086/165342`](http://doi.org/10.1086/165342)

(ref: 1981Natur.289..656H) Herbst, E. 1981, Nature, 289, 656, doi: [`10.1038/289656a0`](http://doi.org/10.1038/289656a0)

(ref: 1996ApJ...463L.113H) Herbst, E., & Woon, D. E. 1996, ApJL, 463, L113, doi: [`10.1086/310059`](http://doi.org/10.1086/310059)

(ref: 2015ARA&A..53..583H) Heyer, M., & Dame, T. M. 2015, ARA&A, 53, 583, doi: [`10.1146/annurev-astro-082214-122324`](http://doi.org/10.1146/annurev-astro-082214-122324)

(ref: 1998ApJ...503..717H) Hirota, T., Yamamoto, S., Mikami, H., & Ohishi, M. 1998, ApJ, 503, 717, doi: [`10.1086/306032`](http://doi.org/10.1086/306032)

(ref: 2016ApJ...823...76K) Koda, J., Scoville, N., & Heyer, M. 2016, ApJ, 823, 76, doi: [`10.3847/0004-637X/823/2/76`](http://doi.org/10.3847/0004-637X/823/2/76)

(ref: 2019AAS...23325310K) Koda, J., Scoville, N., Sawada, T., et al. 2019, in American Astronomical Society Meeting Abstracts, Vol. 233, American Astronomical Society Meeting Abstracts #233, 253.10

(ref: 2016ApJ...826..193L) Lin, S.-J., Shimajiri, Y., Hara, C., et al. 2016, ApJ, 826, 193, doi: [`10.3847/0004-637X/826/2/193`](http://doi.org/10.3847/0004-637X/826/2/193)

(ref: 2023ApJ...943..172L) Liszt, H., & Gerin, M. 2023, ApJ, 943, 172, doi: [`10.3847/1538-4357/acae83`](http://doi.org/10.3847/1538-4357/acae83)

(ref: 2018A&A...617A..54L) Liszt, H., Gerin, M., & Grenier, I. 2018, A&A, 617, A54, doi: [`10.1051/0004-6361/201833167`](http://doi.org/10.1051/0004-6361/201833167)

(ref: 2019A&A...627A..95L) —. 2019, A&A, 627, A95, doi: [`10.1051/0004-6361/201935436`](http://doi.org/10.1051/0004-6361/201935436)

(ref: 1995A&A...299..847L) Liszt, H., & Lucas, R. 1995, A&A, 299, 847

(ref: 2001A&A...370..576L) —. 2001, A&A, 370, 576, doi: [`10.1051/0004-6361:20010260`](http://doi.org/10.1051/0004-6361:20010260)

(ref: 2004A&A...428..117L) Liszt, H., Lucas, R., & Black, J. H. 2004, A&A, 428, 117, doi: [`10.1051/0004-6361:20041649`](http://doi.org/10.1051/0004-6361:20041649)

(ref: 2012ApJ...753L..28L) Liszt, H., Sonnentrucker, P., Cordiner, M., & Gerin, M. 2012, ApJL, 753, L28, doi: [`10.1088/2041-8205/753/2/L28`](http://doi.org/10.1088/2041-8205/753/2/L28)

(ref: 1998A&A...339..561L) Liszt, H. S., & Lucas, R. 1998, A&A, 339, 561

(ref: 2006A&A...448..253L) Liszt, H. S., Lucas, R., & Pety, J. 2006, A&A, 448, 253, doi: [`10.1051/0004-6361:20054071`](http://doi.org/10.1051/0004-6361:20054071)

(ref: 2014A&A...564A..64L) Liszt, H. S., Pety, J., Gerin, M., & Lucas, R. 2014, A&A, 564, A64, doi: [`10.1051/0004-6361/201323320`](http://doi.org/10.1051/0004-6361/201323320)

(ref: 2008A&A...486..493L) Liszt, H. S., Pety, J., & Lucas, R. 2008, A&A, 486, 493, doi: [`10.1051/0004-6361:200809851`](http://doi.org/10.1051/0004-6361:200809851)

(ref: 1989ApJS...71..469L) Lockman, F. J. 1989, ApJS, 71, 469, doi: [`10.1086/191383`](http://doi.org/10.1086/191383)

(ref: 1996ApJ...472..173L) Lockman, F. J., Pisano, D. J., & Howard, G. J. 1996, ApJ, 472, 173, doi: [`10.1086/178052`](http://doi.org/10.1086/178052)

(ref: 1994A&A...282L...5L) Lucas, R., & Liszt, H. 1994, A&A, 282, L5

(ref: 1998A&A...337..246L) —. 1998, A&A, 337, 246

(ref: 1993A&A...276L..33L) Lucas, R., & Liszt, H. S. 1993, A&A, 276, L33

(ref: 2000A&A...358.1069L) —. 2000a, A&A, 358, 1069

(ref: 2000A&A...355..327L) —. 2000b, A&A, 355, 327

(ref: 2002A&A...384.1054L) —. 2002, A&A, 384, 1054, doi: [`10.1051/0004-6361:20020043`](http://doi.org/10.1051/0004-6361:20020043)

(ref: 2020ApJ...889L...4L) Luo, G., Li, D., Tang, N., et al. 2020, ApJL, 889, L4, doi: [`10.3847/2041-8213/ab6337`](http://doi.org/10.3847/2041-8213/ab6337)

(ref: 1993ApJ...417..181M) Maluendes, S. A., McLean, A. D., & Herbst, E. 1993, ApJ, 417, 181, doi: [`10.1086/173301`](http://doi.org/10.1086/173301)

(ref: 1990A&A...239..319M) Mangum, J. G., & Wootten, A. 1990, A&A, 239, 319

(ref: 1991ApJ...371L..77M) Marscher, A. P., Bania, T. M., & Wang, Z. 1991, ApJL, 371, L77, doi: [`10.1086/186006`](http://doi.org/10.1086/186006)

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2011A&A...525A..77M) Menten, K. M., Wyrowski, F., Belloche, A., et al. 2011, A&A, 525, A77, doi: [`10.1051/0004-6361/201014363`](http://doi.org/10.1051/0004-6361/201014363)

(ref: 2005ApJ...634.1126M) Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005, ApJ, 634, 1126, doi: [`10.1086/497123`](http://doi.org/10.1086/497123)

(ref: 1986MNRAS.221..673M) Millar, T. J., Adams, N. G., Smith, D., Lindinger, W., & Villinger, H. 1986, MNRAS, 221, 673, doi: [`10.1093/mnras/221.3.673`](http://doi.org/10.1093/mnras/221.3.673)

(ref: 1997A&AS..121..139M) Millar, T. J., Farquhar, P. R. A., & Willacy, K. 1997, A&AS, 121, 139, doi: [`10.1051/aas:1997118`](http://doi.org/10.1051/aas:1997118)

(ref: doi:10.1021/acs.chemrev.6b00480) Millar, T. J., Walsh, C., & Field, T. A. 2017, Chemical Reviews, 117, 1765, doi: [`10.1021/acs.chemrev.6b00480`](http://doi.org/10.1021/acs.chemrev.6b00480)

(ref: 2016SPIE.9914E..1ZM) Minamidani, T., Nishimura, A., Miyamoto, Y., et al. 2016, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9914, Millimeter, Submillimeter, and Far-Infrared Detectors and Instrumentation for Astronomy VIII, ed. W. S. Holland & J. Zmuidzinas, 99141Z, doi: [`10.1117/12.2232137`](http://doi.org/10.1117/12.2232137)

(ref: 2005JMoSt.742..215M) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215, doi: [`10.1016/j.molstruc.2005.01.027`](http://doi.org/10.1016/j.molstruc.2005.01.027)

(ref: 2001A&A...370L..49M) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49, doi: [`10.1051/0004-6361:20010367`](http://doi.org/10.1051/0004-6361:20010367)

(ref: 2006A&A...458..417M) Muller, S., Guélin, M., Dumke, M., Lucas, R., & Combes, F. 2006, A&A, 458, 417, doi: [`10.1051/0004-6361:20065187`](http://doi.org/10.1051/0004-6361:20065187)

(ref: 2021A&A...652A...5M) Muller, S., Ubachs, W., Menten, K. M., Henkel, C., & Kanekar, N. 2021, A&A, 652, A5, doi: [`10.1051/0004-6361/202140531`](http://doi.org/10.1051/0004-6361/202140531)

(ref: 2011A&A...535A.103M) Muller, S., Beelen, A., Guélin, M., et al. 2011, A&A, 535, A103, doi: [`10.1051/0004-6361/201117096`](http://doi.org/10.1051/0004-6361/201117096)

(ref: 1999A&A...350..204N) Nejad, L. A. M., & Wagenblast, R. 1999, A&A, 350, 204

(ref: 2015A&A...577A..49N) Neufeld, D. A., Godard, B., Gerin, M., et al. 2015, A&A, 577, A49, doi: [`10.1051/0004-6361/201425391`](http://doi.org/10.1051/0004-6361/201425391)

(ref: 2017ApJ...848...17N) Nishimura, Y., Watanabe, Y., Harada, N., et al. 2017, ApJ, 848, 17, doi: [`10.3847/1538-4357/aa89e5`](http://doi.org/10.3847/1538-4357/aa89e5)

(ref: 1992IAUS..150..171O) Ohishi, M., Irvine, W. M., & Kaifu, N. 1992, in Astrochemistry of Cosmic Phenomena, ed. P. D. Singh, Vol. 150, 171

(ref: 2002ApJ...575..950O) Onishi, T., Mizuno, A., Kawamura, A., Tachihara, K., & Fukui, Y. 2002, ApJ, 575, 950, doi: [`10.1086/341347`](http://doi.org/10.1086/341347)

(ref: 2018A&A...617A..14P) Paron, S., Areal, M. B., & Ortega, M. E. 2018, A&A, 617, A14, doi: [`10.1051/0004-6361/201833658`](http://doi.org/10.1051/0004-6361/201833658)

(ref: 2005A&A...435..885P) Pety, J., Teyssier, D., Fossé, D., et al. 2005, A&A, 435, 885, doi: [`10.1051/0004-6361:20041170`](http://doi.org/10.1051/0004-6361:20041170)

(ref: 2012A&A...548A..68P) Pety, J., Gratier, P., Guzmán, V., et al. 2012, A&A, 548, A68, doi: [`10.1051/0004-6361/201220062`](http://doi.org/10.1051/0004-6361/201220062)

(ref: 1998JQSRT..60..883P) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883, doi: [`10.1016/S0022-4073(98)00091-0`](http://doi.org/10.1016/S0022-4073(98)00091-0)

(ref: 2008ApJ...679..481P) Pineda, J. E., Caselli, P., & Goodman, A. A. 2008, ApJ, 679, 481, doi: [`10.1086/586883`](http://doi.org/10.1086/586883)

(ref: 2010ApJ...712L.116P) Pineda, J. E., Goodman, A. A., Arce, H. G., et al. 2010, ApJL, 712, L116, doi: [`10.1088/2041-8205/712/1/L116`](http://doi.org/10.1088/2041-8205/712/1/L116)

(ref: 2013A&A...554A.103P) Pineda, J. L., Langer, W. D., Velusamy, T., & Goldsmith, P. F. 2013, A&A, 554, A103, doi: [`10.1051/0004-6361/201321188`](http://doi.org/10.1051/0004-6361/201321188)

(ref: 2014A&A...571A..11P) Planck Collaboration, Abergel, A., Ade, P. A. R., et al. 2014, A&A, 571, A11, doi: [`10.1051/0004-6361/201323195`](http://doi.org/10.1051/0004-6361/201323195)

(ref: 2016ApJ...823...77R) Reid, M. J., Dame, T. M., Menten, K. M., & Brunthaler, A. 2016, ApJ, 823, 77, doi: [`10.3847/0004-637X/823/2/77`](http://doi.org/10.3847/0004-637X/823/2/77)

(ref: 2018A&A...610A..43R) Riquelme, D., Bronfman, L., Mauersberger, R., et al. 2018, A&A, 610, A43, doi: [`10.1051/0004-6361/201730602`](http://doi.org/10.1051/0004-6361/201730602)

(ref: 2011ApJ...728...36R) Ritchey, A. M., Federman, S. R., & Lambert, D. L. 2011, ApJ, 728, 36, doi: [`10.1088/0004-637X/728/1/36`](http://doi.org/10.1088/0004-637X/728/1/36)

(ref: 2021A&A...648A.120R) Rodrı́guez-Baras, M., Fuente, A., Riviére-Marichalar, P., et al. 2021, A&A, 648, A120, doi: [`10.1051/0004-6361/202040112`](http://doi.org/10.1051/0004-6361/202040112)

(ref: 2012A&A...546A.103S) Sakai, N., Maezawa, H., Sakai, T., Menten, K. M., & Yamamoto, S. 2012, A&A, 546, A103, doi: [`10.1051/0004-6361/201219106`](http://doi.org/10.1051/0004-6361/201219106)

(ref: 2002ApJ...565.1050S) Sakamoto, S. 2002, ApJ, 565, 1050, doi: [`10.1086/324781`](http://doi.org/10.1086/324781)

(ref: 1997ApJ...481..302S) Sakamoto, S., Hasegawa, T., Hayashi, M., Morino, J.-I., & Sato, K. 1997, ApJ, 481, 302, doi: [`10.1086/304023`](http://doi.org/10.1086/304023)

(ref: 2003ApJ...594..340S) Sakamoto, S., & Sunada, K. 2003, ApJ, 594, 340, doi: [`10.1086/376856`](http://doi.org/10.1086/376856)

(ref: 2001A&A...372..291S) Schilke, P., Pineau des Forêts, G., Walmsley, C. M., & Martı́n-Pintado, J. 2001, A&A, 372, 291, doi: [`10.1051/0004-6361:20010470`](http://doi.org/10.1051/0004-6361:20010470)

(ref: 2008ApJ...687.1075S) Sheffer, Y., Rogers, M., Federman, S. R., et al. 2008, ApJ, 687, 1075, doi: [`10.1086/591484`](http://doi.org/10.1086/591484)

(ref: 2007ApJ...667.1002S) Sheffer, Y., Rogers, M., Federman, S. R., Lambert, D. L., & Gredel, R. 2007, ApJ, 667, 1002, doi: [`10.1086/520875`](http://doi.org/10.1086/520875)

(ref: 2014A&A...564A..68S) Shimajiri, Y., Kitamura, Y., Saito, M., et al. 2014, A&A, 564, A68, doi: [`10.1051/0004-6361/201322912`](http://doi.org/10.1051/0004-6361/201322912)

(ref: 2016PASJ...68...63S) Sofue, Y., & Nakanishi, H. 2016, PASJ, 68, 63, doi: [`10.1093/pasj/psw062`](http://doi.org/10.1093/pasj/psw062)

(ref: 2007ApJS..168...58S) Sonnentrucker, P., Welty, D. E., Thorburn, J. A., & York, D. G. 2007, ApJS, 168, 58, doi: [`10.1086/508687`](http://doi.org/10.1086/508687)

(ref: 2012ApJ...754...95T) Tachihara, K., Saigo, K., Higuchi, A. E., et al. 2012, ApJ, 754, 95, doi: [`10.1088/0004-637X/754/2/95`](http://doi.org/10.1088/0004-637X/754/2/95)

(ref: ndradex) Taniguchi, A. 2023, ndradex, version 0.3.0, doi: [`10.5281/zenodo.3384031`](http://doi.org/10.5281/zenodo.3384031)

(ref: cite-key) Team, T. C., Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacific, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: 2004A&A...417..135T) Teyssier, D., Fossé, D., Gerin, M., et al. 2004, A&A, 417, 135, doi: [`10.1051/0004-6361:20034534`](http://doi.org/10.1051/0004-6361:20034534)

(ref: 2016A&A...593L..12T) Treviño-Morales, S. P., Fuente, A., Sánchez-Monge, Á., et al. 2016, A&A, 593, L12, doi: [`10.1051/0004-6361/201628899`](http://doi.org/10.1051/0004-6361/201628899)

(ref: 2017PASJ...69...78U) Umemoto, T., Minamidani, T., Kuno, N., et al. 2017, PASJ, 69, 78, doi: [`10.1093/pasj/psx061`](http://doi.org/10.1093/pasj/psx061)

(ref: 2007A&A...468..627V) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: 1988ApJ...334..771V) van Dishoeck, E. F., & Black, J. H. 1988, ApJ, 334, 771, doi: [`10.1086/166877`](http://doi.org/10.1086/166877)

(ref: 2003ApJ...587..714W) Watson, C., Araya, E., Sewilo, M., et al. 2003, ApJ, 587, 714, doi: [`10.1086/368286`](http://doi.org/10.1086/368286)

(ref: 1997A&A...326..139W) Wielen, R., & Wilson, T. L. 1997, A&A, 326, 139

(ref: 1994ARA&A..32..191W) Wilson, T. L., & Rood, R. 1994, ARA&A, 32, 191, doi: [`10.1146/annurev.aa.32.090194.001203`](http://doi.org/10.1146/annurev.aa.32.090194.001203)

(ref: 2010ApJ...716.1191W) Wolfire, M. G., Hollenbach, D., & McKee, C. F. 2010, ApJ, 716, 1191, doi: [`10.1088/0004-637X/716/2/1191`](http://doi.org/10.1088/0004-637X/716/2/1191)

(ref: 1987ApJ...322L..55Y) Yamamoto, S., Saito, S., Ohishi, M., et al. 1987, ApJL, 322, L55, doi: [`10.1086/185036`](http://doi.org/10.1086/185036)

(ref: yoshimura2020) Yoshimura, Y. 2020, Master’s thesis, The University of Tokyo

(ref: 2020ApJ...899..145Y) Yu, H. Z., Zhang, J. S., Henkel, C., et al. 2020, ApJ, 899, 145, doi: [`10.3847/1538-4357/aba8f1`](http://doi.org/10.3847/1538-4357/aba8f1)

(ref: 2017MNRAS.471.3494Z) Zhu, H., Tian, W., Li, A., & Zhang, M. 2017, MNRAS, 471, 3494, doi: [`10.1093/mnras/stx1580`](http://doi.org/10.1093/mnras/stx1580)

(ref: 1995ApJ...455L..73Z) Ziurys, L. M., & Apponi, A. J. 1995, ApJL, 455, L73, doi: [`10.1086/309811`](http://doi.org/10.1086/309811)

(ref: 1989ApJ...343..201Z) Ziurys, L. M., Friberg, P., & Irvine, W. M. 1989, ApJ, 343, 201, doi: [`10.1086/167696`](http://doi.org/10.1086/167696)

</paper>

Write the methods card for this paper.