# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...969...56M\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2024ApJ...969...56M",
 "title": "Observational Constraints on Sunyaev─Zeldovich Effect Halos around High-z Quasars",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Massingill, Kyle",
 "n_authors": 7,
 "arxiv_id": "2310.09445",
 "doi": "10.3847/1538-4357/ad3a67",
 "alma_projects_linked_by_archive": [
  "2019.1.01251.S"
 ]
}
```

Paper text:
<paper>
# Observational Constraints on Sunyaev-Zeldovich Effect Halos Around High-z Quasars

## Abstract

We present continuum observations from the Atacama Large Millimeter/submillimeter Array (ALMA) of 10 high-redshift ($2.2 \le z \le 2.7$) ultraluminous quasars (QSOs) and constrain the presence of hot, ionized, circum-galactic gas in a stacking analysis. We measure a Compton-y parameter profile with a peak value of $(1.7 \pm 1.1) \times 10^{-6}$ at a radius of $\sim50$ kpc. We compare our stacked observations to active galactic nucleus (AGN) feedback wind models and generalized Navarro-Frenk-White (gNFW) pressure profile models to constrain the wind luminosity and halo mass of the stacked QSOs. Our observations constrain the observed stack’s halo mass to $<1\times 10^{13}M_{\odot}$ and the stack’s feedback wind power $<1\times 10^{12}L_{\odot}$, which is $<1$% of the bolometric luminosity of the quasar.

# Introduction

The lack of super massive galaxies at low redshift ((cite: Drory_2008); (cite: Treu_2005)) and the “downsizing" (cite: Cowie_1996) of star-forming galaxies below $z\sim2$ indicates some process regulating the growth of galaxies on long time scales. Active galactic nucleus (AGN) feedback has been postulated as the mechanism regulating galaxy formation ((cite: Scannapieco2004); (cite: 10.1111/j.1365-2966.2006.10519.x)) and remains the best explanation for the observed galaxy sizes. An AGN has enough energy to heat gas in the circumgalactic medium (CGM) and even possibly expel gas out of the galaxy completely ((cite: Silk1998); (cite: 10.1111/j.1365-2966.2006.10519.x)). It is not yet well understood what role different feedback mechanisms play in stifling galaxy growth (cite: Ostriker_2010; Fabian2012). The relative importance of feedback mechanisms, such as jets, winds, and radiation, is still being studied.

In order to better understand AGN feedback, observations must be made to constrain the energy of the the different feedback mechanisms. Quasar winds or outflows have been detected directly in X-ray for two low-z cases ((cite: Greene_2014); (cite: 10.1093/mnras/stu515)). X-ray detections of outflows from high-$z$ systems where AGN are most powerful are more difficult, as the faint, diffuse X-ray emission from the winds is hard to detect against the strong point source emission from the quasar (cite: 2022ApJ...940...47K). Instead, detections can be obtained using the Sunyaev-Zel’dovich effect (SZE) (cite: 1972CoASP...4..173S) around QSOs. The thermal SZE (tSZE) is the process where cosmic microwave background (CMB) emission is distorted by traveling through hot gas, inducing an inverse Compton scattering. Bulk motion of electrons in the gas also produce a kinetic SZE (kSZE). In the case of AGN feedback, most studies focus on detecting the tSZE from the superposition of multiple wind events in the CGM of the quasar, when the tSZE is dominant (cite: Scannapieco2008). By stacking large numbers of quasars in tSZE maps from mm-wave telescopes a number of studies have claimed to detect a significant tSZE signal from quasar winds (e.g. (cite: Chatterjee2010); (cite: Ruan2015); (cite: Crichton2016); (cite: Verdier2016); (cite: Hall2019); (cite: Meinke2021)). With the large beams of the mm-wave telescopes used and uncertainties regarding the contamination of the SZ signal by dust emission from the quasar host galaxies, however, it can be hard to tell if the detections correspond simply to a combination of dust emission and the tSZE from virialized gas in the massive dark matter haloes in which the quasars reside, or whether there is an extra component of the tSZE due to quasar feedback. tSZE from hot intracluster medium has been detected in the Spiderweb radio galaxy ((cite: Mascolo2023)).

Typical AGN exist in relatively rich environments, even at high redshift. Quasar-quasar clustering analyses (cite: White2012; Timlin2018; Eftekharzadeh2019), lensing of the Cosmic Microwave Background by quasar hosts (cite: Geach2019), the kinematics of the warm ionized gas from quasar absorption lines (cite: Lau2018) and Ly-$\alpha$ haloes (cite: Fossati2021) all suggest that quasars at $z\sim 1-4$ lie in dark matter haloes of masses $\approx 2-10\times 10^{12}h^{-1} M_{\odot}$, consistent with galaxy groups in the local Universe. Most estimates for radio-quiet quasars are towards the lower end of that range, whereas radio-loud AGN cluster more strongly, consistent with halo masses at the upper end of that range (cite: Miley2008; Retana-Montenegro2017). These relatively high mass haloes led (cite: Cen2015) and (cite: Soergel2017) to argue that the tSZE signal from stacking studies is dominated by that from the virialized haloes of the quasars. By using a halo occupation distribution model for quasar clustering (cite: Chowdhury2017) suggested that the signal from feedback in the stacking studies made prior to 2017 is significantly higher than that expected from the virialized gas in the quasar halo only at high redshifts ($z>2.5$).

Some of the ambiguities of stacking studies can be overcome using high resolution images from mm-wave interferometers, such as ALMA. These studies enable the subtraction of emission by the quasar host and any companion or foreground/background galaxies. The morphology of the SZE signal can also be compared to, for example, that of emission line gas to determine whether the signal is associated with an outflow, or more generally with the halo in which the quasar resides. However, these observations are challenging, requiring $\stackrel{>}{_{\sim}}10$ hours of integration time on ALMA to detect a signal around even the most luminous quasars. It is also not possible to separate the tSZE from any kSZE contribution without further very deep observations at other frequencies. To date, there is only one example of an SZE detection around a single QSO, the hyperluminous (bolometric luminosity $\sim 10^{15} L_{\odot}$) quasar HE 0515-4414 (cite: Lacy2019).

|  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|
| Target | Position | SNR | Redshift | log$_{10}(L_{\rm bol}/L_{\odot}$) | RMS |
|  |  | ($\sigma$) | ($z$) |  | (Jy/beam) |
| Q0050+0051 | ICRS 00:50:21.2200, 00:51:35.000 | 14 | 2.22 | 13.79 | 2.14e-5 |
| Q0052+0140 | ICRS 00:52:33.6700, 01:40:40.800 | 11 | 2.30 | 13.99 | 2.00e-5 |
| Q0101+0201 | ICRS 01:01:16.5400, 02:01:57.400 | 13 | 2.46 | 13.91 | 1.91e-5 |
| Q1227+2848 | ICRS 12:27:27.4800, 28:48:47.900 | 7 | 2.26 | 13.76 | 1.64e-5 |
| Q1228+3128 | ICRS 12:28:24.9700, 31:28:37.700 | 307 | 2.22 | 14.55 | 2.80e-5 |
| Q1230+3320 | ICRS 12:30:35.4700, 33:20:00.500 | 13 | 2.32 | 13.66 | 1.99e-5 |
| Q1416+2649 | ICRS 14:16:17.3800, 26:49:06.200 | 21 | 2.29 | 13.51 | 1.86e-5 |
| Q2121+0052 | ICRS 21:21:59.0400, 00:52:24.100 | 3 | 2.37 | 13.69 | 2.17e-5 |
| Q2123$-$0050 | ICRS 21:23:29.4600, $-$00:50:52.900 | 7 | 2.65 | 14.52 | 2.21e-5 |
| Q0107+0314 | ICRS 01:07:36.9000, 03:14:59.200 | 9 | 2.28 | 13.76 | 2.18e-5 |

We therefore decided to try a different approach to constrain the tSZE signal from a sample of more typically-luminous quasars, also by using ALMA, but stacking the signal from a moderate number ($\approx 10$) of ultraluminous quasars (with bolometric luminosities $\sim 10^{14} L_{\odot}$). These quasars were selected to have extended Ly$\alpha$ nebulae around them ((cite: Cai2019)), which allow a rough estimate of the typical halo mass in the sample to be made based on the gas dynamics (uncertain due to radiative transfer effects and possible non-gravitational motions in the Ly$\alpha$-emitting gas). Using ALMA allows us to take advantage of the capability to subtract emission from discrete sources, both in the field and associated with the quasar, whilst still building up enough signal-to-noise to make a detection or place a meaningful limit on the tSZE signal from feedback.

In this paper we present observations of ten ultraluminous QSOs at $2.2 \le z \le 2.7$ observed by the ALMA 12m array. We constrain the Compton parameter of the observed population. We compare our measured Compton parameters to generalized Navarro–Frenk–White (gNFW) ((cite: Arnaud2010)) profiles and spherical feedback models.

# Observations

Our ALMA QSO targets were observed by project 2019.1.01251.S. This was a commensal program between our continuum study of the SZE and emission-line observations of CO(4-3) and \[CI\] as part of the SUPERCOLD-CGM survey (cite: 2023ApJ...950..180L), which both benefited from sensitive low-surface-brightness observations with ALMA Band 4. Ten pointings were used to observe ten QSO’s on the ALMA 12m array band 4 ($\sim 145\,{\rm GHz}$) with an angular resolution of $\sim$$2^{''}$. Targets were observed by the 12m array for $1-2$ hours in order to achieve an root mean square RMS of $\approx 11 \mu \rm Jy$ in the continuum. Observations of these sources were also made with the ALMA 7m array but at a much higher noise level, so we do not utilize them in our analysis here. See Table 1 for a full list of targets and the achieved signal to noise ratio of the observations. Observations were made with four $2\,\rm GHz$ spectral windows (SPWs), two containing line emission (from CO and CI) and two only containing continuum.

## Data Reduction and Calibration

The standard pipeline calibrations of the ALMA data (cite: Hunter2023) were utilized for the QSO observations. Data reduction scripts supplied with the ALMA archival data were used together with the Common Astronomy Software Application (CASA; (cite: casa2022)) version 5.6.1-8, which includes the ALMA pipeline ((cite: Masters2020)) version r42866. We reduced the data by first splitting off the calibrated on source observations from the full data set then flagging spectral line in each SPW. For flagging spectral lines, an image cube with a channel width of $\sim8$ MHz (base bands have a full bandwidth of $1875$ MHz) was produced for each base band. Then channels with localized emission $4\sigma$ or more above the continuum of the channel were flagged. Flagged channels were then ignored in subsequent cleaning/imaging. All four SPWs were then combined to make a single, aggregate continuum image.

Imaging and cleaning was done using CASA task “tclean”. We imaged an area of 60$\times$60 arcseconds centered on each quasar using a pixel scale of $0.4^{''}$/pixel. We started the imaging process by first cleaning the ALMA 12m images at full resolution. We cleaned using a robustness of $0.5$. For each of the ten targets, the sources (the QSO and any nearby serendipitous sources) were masked manually; we then cleaned the masked region to the threshold of the overall image RMS. All subsequent analysis was performed upon the clean residual images, which have effectively had the central QSO (and any strong, positive emission) subtracted. We applied Gaussian tapers to the (u,v)-data during imaging to improve surface brightness measurements of extended signals. We made tapered images for each source at $\sim 6^{''}$ and $\sim 3^{''}$ resolutions.

The object Q1228+3128 (previously identified as a radio loud QSO in (cite: Li2021)) was detected with very high ($\sim 307\sigma$) signal-to-noise ratio (SNR) in the ALMA continuum observations such that the image was dynamic range limited and benefited from self-calibration. To self-calibrate we use the central source to correct for changes in phase. We solved for phase in intervals of scan length following ALMA NAASC recommended self-calibration procedure ((cite: Brogan2018)). However, even with self-calibration we determined the observation to not have enough dynamic range to detect the $\mu$Jy level signal of the tSZE. Q1228+3128 was therefore excluded from the analyses. Our second highest QSO SNR detection in the continuum observations was Q1416+2649 with a much lower significance of $\sim 21\sigma$ (we do not utilize self-calibration for this Q1416+264). Continuum emission from the central QSO was clearly detected in 9 of the 10 targets, and weakly ($\sim 3 \sigma$) detected in the other.

![](Figures/stack_y.png)

## Stacked SZE Signal

We stacked the source subtracted ALMA images by first measuring the median absolute deviation (MAD) of each residual image and applying weighting to each residual image based on the MAD. The masks from the cleaning stage (see section [2.1](#sec:Data Reduction and Calibration) Data Reduction and Calibration) were applied to the residuals and masked regions were not included in the stack. This was done to ensure any leftover source emission was not added to the final stacked image. All the residuals were then stacked by summation in units of Jy/beam. We produced a $\sim 6^{''}$ and $\sim 3^{''}$ resolution stack.

We interpret the stacked continuum flux observations as SZE signal by converting to Compton parameter ($y$). Observed decrement in the continuum flux will correspond to a positive Compton parameter. Our stacking analysis will not be sensitive to the non-spherically symmetric kSZE. For stacked QSO environments we use a pure thermal SZE model to determine the Compton parameters. We therefore assume $v_r/c<<(k_BT_e)/(m_ec^2)f_1(x)$. Following (cite: Sazonov1998), the change in intensity of the CMB due to SZE is given by:

$$\begin{equation}
    \Delta I(x) = \frac{2k_B T_{CMB}}{\lambda^2}\frac{x^2e^x}{(e^x-1)^2}\tau\frac{ k_BT_e}{m_ec^2}f_1(x),
\end{equation}$$ where $x\equiv h\nu/k_BT_{CMB}$, and $f_1(x)=x\coth(x/2)-4$. $\tau$ is the Thompson scattering optical depth along the line of sight and $f_1(x)$ is the frequency dependence of thermal SZE. We therefore describe the spectral distortion along a line of sight as the Compton parameter ((cite: 1972CoASP...4..173S)): $$\begin{equation}
    y=\frac{\tau k_BT_e}{m_ec^2}.
\end{equation}$$ We convert observed flux into Compton parameter for the purposes of comparing observations to theoretical models.

Fig. [1](#fig:stacked_y) shows the Compton parameter of the stacked QSO environments tapered to an effective beam of $\sim 6''$. A region of high $y$ can be seen in the east side of the image, at a radius of $\sim 5''$ from the center, peaking at $y= 2.4e-5$ or $\sim2.6\sigma$. Regions of null pixels exist (prominently seen as white pixels at the center of Fig. [1](#fig:stacked_y)) due to masking as described earlier in this section.

# Analysis

## gNFW Models

In order to compare our observations to theoretical models of different halo masses, we use a generalized Navarro-Frenk-White (gNFW) pressure profile: $$\begin{equation}
\mathbb{P} (x) = \frac{P_0}{(c_{500}x)^\gamma[1+(c_{500}x)^\alpha]^{(\beta-\gamma)/\alpha}}
\end{equation}$$ as described in (cite: Arnaud2010) and (cite: Nagai2007). $x\equiv r/r_s$ and $r_s=r_{500}/c_{500}$, where $r_{500}$ is the radius containing matter at 500 times the ambient density. We treat the halo as a cube divided into cells; the cube is $300^3$ cells. Each is cell is $0.4^{''}$ per side and the total volume of the cube, within which we are integrating the line-of-sight pressure, is $\sim 1\times 10^{10}$ kpc$^3$at our average redshift of $z=2.34$. We then calculate the pressure of each cell:

$$\begin{equation}
P(r)=P_{500} \left[\frac{M_{500}}{3\times10^{14}h_{70}^{-1}M_\odot} \right]^{\alpha_P+\alpha'_P(x)}\mathbb{P} (x)
\end{equation}$$with parameters:

$$\begin{eqnarray}
&& [P_0,c_{500},\gamma,\alpha,\beta] = \nonumber \\
&& \left[ 8.403 h^{-3/2}_{70}, 1.177, 0.3081, 1.0510, 5.4905 \right]
\end{eqnarray}$$

where $P_{500}$ and $M_{500}$ are the corresponding pressure and mass respectively. To determine $y$ we integrate the pressure through the cube. We generate halo simulation images (see section [3.3](#sec:Simulating Observations)) for halo masses of $1 \times 10^{12}M_{\odot}$ , $3 \times 10^{12}M_{\odot}$, $1 \times 10^{13}M_{\odot}$, and $3 \times 10^{13}M_{\odot}$. For the nominal mass case of $3 \times 10^{12}M_{\odot}$, $y\sim 10^{-6}$ out to a radius of $\sim 100$ kpc (or $\approx 12^{''}$ at $z=2.34$) from the center of the profile.

## Feedback Models

The gNFW models do not include the effects of feedback. We therefore constructed a set of simple spherical wind models of AGN feedback using the prescription of (cite: 2011MNRAS.412..905R) as adapted for AGN winds by (cite: Lacy2019). These give the radius of the bubble, $R$:

$$\begin{equation}
    R=\beta \left(\frac{L_W T^3}{\Omega_{b}\rho_{c}(1+z)^3(1+b_{Q}\delta)}\right)^{1/5}
\end{equation}$$ where $\beta=0.8828$, $L_W$ is the wind power, $T$ is the age of the outflow, $\Omega_b$ is the fraction of the critical density of the Universe $\rho_c$ in baryons, $b_Q\approx 13$ is the cosmological bias factor for quasars and $\delta=180$ is the assumed overdensity corresponding to collapsed structures. The pressure inside the bubble is approximately constant and is: $$\begin{equation}
    P_{\rm bub}=\frac{2}{5}\frac{3}{4 \pi}\frac{L_W T}{R^3}
\end{equation}$$ and the peak Compton-$y$ signal (through the center of the bubble): $$\begin{equation}
    y_{\rm max}=1.08\frac{P_e\sigma_T}{m_ec^2}2R
\end{equation}$$ where the electron pressure, $P_e=P_{\rm bub}/1.92$, $\sigma_T$ is the Thompson cross-section and $m_e$ the electron mass. We constructed 2-D models of the SZE signal to then run through the simulator, as described below.

![](Figures/feedbackmodel_simulator_example.png)

![](Figures/halo_mass_radial_C.png)

## Simulating Observations

The gNFW pressure profiles and wind models are simulations of sky images. In order to compare them to our observations in the image plane, we had to add the effects of the ALMA beam to our simulated images. We do this by utilizing the ALMA simulator, a facility within CASA ((cite: casa2022)). The ALMA simulator takes a sky image and a given set of observational conditions and produces the expected ALMA visibilities. This is done by convolving the telescope configuration with the theoretical sky image. We used simulator task “simpredict" from CASA version 5.6.1-8. For each of calculated models, we produce a set of theoretical visibilities based on the QSO observational conditions. These simulated visibities are then imaged using the same parameters as the QSOs (see Fig. [2](#fig:simulation_demo) for an example). These imaged models now have the same primary beam and side lobe effects as the observations.

## Radial Profile Analysis

To compare the gNFW models to our observations, the Compton parameter of the stack was analyzed as a radial profile in bins slightly wider then the width of the tapered beam. We utilized the lower resolution stack for this analysis, as the pressure profiles are relatively extended ( $>10^{''}$) sources. The beam of the smoothed ALMA image is $\sim 6^{''}$ while we used $\sim 6.7^{''}$ wide bins. The central pixels of the image (out to $r\sim 3^{''}$) were not utilized in the radial profile analysis as that region is mostly masked out. We measured the mean Compton parameter and RMS in each bin of the stack. Figure [3](#fig:Halo Mass RP) shows our radial profile analysis comparing the stacked QSO images to gNFW profiles of different halo masses.

The feedback models were prepared using the same procedure as the gNFW models (see section [3.3](#sec:Simulating Observations)). We compared the feedback models to the higher resolution stack ($\sim 3^{''}$ beam) in order to be sensitive to wind bubbles with radii on order of a few arcseconds predicted by recent simulations (cite: Chakraborty2023). We analyzed this stack in Compton-$y$ as a radial profile using bins with a width of $\sim 5.3^{''}$. As on the lower resolution image, the central pixels of the image (out to $r\sim 3^{''}$) were not utilized in the radial profile analysis. We compared this profile to the feedback models at a variety of wind powers ($L_W$) and two outflow ages ($T$). The chosen outflow ages are based on the estimated age of a previously detected feedback wind bubble in (cite: Lacy2019) and are of the order of the Salpeter timescale for quasar growth (cite: 2013BASI...41...61S). Figures [4](#fig:T=3e7 Wind RP) and [5](#fig:T=1e8 Wind RP) show our radial profile analysis.

# Results and Discussion

| Model Halo Mass              | $\chi^2$ | p-value              |
|:-----------------------------|:---------|:---------------------|
| $1 \times 10^{12} M_{\odot}$ | $4.03$   | $0.4$                |
| $3\times 10^{12} M_{\odot}$  | $4.38$   | $0.36$               |
| $1\times 10^{13}M_{\odot}$   | $8.02$   | $0.09$               |
| $3\times 10^{13}M_{\odot}$   | $31.43$  | $2.51\times 10^{-6}$ |

: Results of image plane analysis, comparing stacked observations of QSO environments to gNFW halo profiles at four different halo masses as a goodness of fit $\chi^2$ and associated statistical p-value with four degrees of freedom. All models use a concentration of 1.

![](Figures/winds_radial_3e7years.png)

![](Figures/winds_radial_e8years.png)

## Halo Mass

Signal from a gNFW halo (CMB decrement) is strongest at the center of the profile, which would not be detectable by these observations as they are centered on continuum bright QSOs. On the image plane we instead try to fit the regions around the QSO to the profile the same distance from the center. In our stacked data we do see a Compoton signal in the inner radial bin (see figure [3](#fig:Halo Mass RP)), but the error is large due to the small radius; this bin only contains $\sim 10$ beams. The other notable features of the gNFW halo when observed through the ALMA simulator are the dark sidelobes. Larger mass halo models will have brighter (in Compton-$y$) centered decrement and darker sidelobes than lower mass models. Our observations lack dark sidelobes that would indicate a higher mass halo. We quantify the relationship between the stacked QSO observations and the simulated gNFW models by calculating the $\chi^2$ and p-value (where “p” is the probability that the difference between model and observations are due to chance) for each halo mass model compared to the stacked observations. $\chi^2$ is calculated from 4 bins in the case of halo mass. Looking at Table 2 we can see that as we go to higher halo mass models, it becomes statistically less likely that they are consistent with our observations. The gNFW model with halo mass $1\times 10^{13}M_{\odot}$ has a p-value $0.09$. We can therefore constrain our observed stack of QSOs to have a halo mass $<1\times 10^{13}M_{\odot}$ with $90\%$ confidence.

+------------------------------------------------------------------+
| $T = 3 \times 10^{7}$years                                       |
+:=============================+:===========+:=====================+
| $L_{W}$                      | $\chi^2$   | p-value              |
+------------------------------+------------+----------------------+
| $1 \times 10^{11} L_{\odot}$ | $1.49$     | $0.19$               |
+------------------------------+------------+----------------------+
| $3 \times 10^{11} L_{\odot}$ | $1.6$      | $0.16$               |
+------------------------------+------------+----------------------+
| $1 \times 10^{12} L_{\odot}$ | $2.08$     | $0.06$               |
+------------------------------+------------+----------------------+
| $3 \times 10^{12} L_{\odot}$ | $4.93$     | $1.6 \times 10^{-4}$ |
+------------------------------+------------+----------------------+
| $1 \times 10^{13} L_{\odot}$ | $30.56$    | $<1 \times 10^{-16}$ |
+------------------------------+------------+----------------------+

: Results of image plane analysis, comparing stacked observations of QSO environments to outflow age $3 \times 10^{7}$ years feedback models at five different wind powers as a goodness of fit $\chi^2$ and associated statistical p-value with five degrees of freedom.

+--------------------------------------------------------------------+
| $T = 1 \times 10^{8}$years                                         |
+:=============================+:===========+:=======================+
| $L_{W}$                      | $\chi^2$   | p-value                |
+------------------------------+------------+------------------------+
| $1 \times 10^{11} L_{\odot}$ | $1.55$     | $0.17$                 |
+------------------------------+------------+------------------------+
| $3 \times 10^{11} L_{\odot}$ | $1.88$     | $0.09$                 |
+------------------------------+------------+------------------------+
| $1 \times 10^{12} L_{\odot}$ | $3.32$     | $0.01$                 |
+------------------------------+------------+------------------------+
| $3 \times 10^{12} L_{\odot}$ | $7.78$     | $2.51 \times 10^{-7}$  |
+------------------------------+------------+------------------------+
| $1 \times 10^{13} L_{\odot}$ | $13.68$    | $2.18 \times 10^{-13}$ |
+------------------------------+------------+------------------------+

: Results of image plane analysis, comparing stacked observations of QSO environments to outflow age $1 \times 10^{8}$ years feedback models at five different wind powers as a goodness of fit $\chi^2$ and associated statistical p-value with five degrees of freedom.

## Feedback

We have modeled feedback as a spherical wind bubble that will cause a positive Compton-$y$ signal within the radius of the bubble. Sidelobe effects from the ALMA observatory are accounted for by the simulator and cause negative Compton-$y$ signal around the feedback wind bubble. On the image plane we fit the regions around the QSO to the feedback models at the same distance from image center. We quantify the relationship between the stacked QSO observations and the simulated feedback models by calculating the $\chi^2$ and p-value for each wind power and outflow age model compared to the stacked observations. Looking at Tables 3 and 4 we see that in both outflow age cases, as we go to higher power models, it becomes statistically less likely that they are consistent with our observations. At a wind power of $1 \times 10^{12} L_{\odot}$ and an outflow age $1 \times 10^{8}$ years the p-value is $0.01$ We can therefore constrain our observed stack of QSOs to have a feedback wind power $<1\times 10^{12}L_{\odot}$ , or $\stackrel{<}{_{\sim}}1$% of the bolometric luminosity of the quasar.

# Conclusions

We use the constraints on the tSZE from our stack of quasar observations to show that (1) if the quasars are in quiescent halos of virialized gas, the halo mass is $<1\times 10^{13}M_{\odot}$ (consistent with estimates $\sim 3\times 10^{12}M_{\odot}$ from clustering analyses), and (2), if feedback from thermal winds extends to spatial scales $\sim 100$ kpc, these winds carry $<1\%$ of the bolometric luminosity of the quasars. This finding is consistent with the only direct detection of SZE around a single QSO, (cite: Lacy2019), which found the hyperluminous quasar HE 0515-4414 to have a wind luminosity of $\sim0.01\%$ of the bolometric luminosity of the quasar. The $\chi^2$ of our best fitting models is similar to zero signal. Further fitting of halo and feedback models is therefore not merited by the data available in this survey. We do not see evidence of a strongly peaked central decrement that would be indicative of a gNFW profile or feedback wind bubble. We note that the simulations of (cite: Chakraborty2023) show that strong jet-mode feedback is effective at suppressing the SZE from both the halo and thermal winds, thus jet feedback may be occurring in these objects. Only one of the quasars (Q1228+3128, which was not included in our stacking analysis) is currently radio loud, however there could be intermittent jet activity (cite: 2020ApJ...905...74N) and it has been show that non radio-loud quasars can still have radio mode feedback that effect the QSO environment on scales of $\sim$10-100 kpc ((cite: VillarMartin2021)).

# Acknowledgments

This paper makes use of the ALMA data: 2019.1.01251.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Tai-wan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. We thank the North American ALMA Science Center faculty and staff for their support. We thank the Arizona State University SZ science group, including Seth Cohen, Phil Mauskopf, Sean Bryan, Jenna Moore, Emily Lunde, Jeremey Meinke, Skylar Grayson and Evan Scannapieco, for their advice and contributions.

natexlab

(ref: Arnaud2010) Arnaud, M., Pratt, G. W., Piffaretti, R., et al. 2010, Astronomy and Astrophysics, 517, A92, doi: [`10.1051/0004-6361/200913416`](http://doi.org/10.1051/0004-6361/200913416)

(ref: 10.1111/j.1365-2966.2006.10519.x) Bower, R. G., Benson, A. J., Malbon, R., et al. 2006, Monthly Notices of the Royal Astronomical Society, 370, 645, doi: [`10.1111/j.1365-2966.2006.10519.x`](http://doi.org/10.1111/j.1365-2966.2006.10519.x)

(ref: Brogan2018) Brogan, C. L., Hunter, T. R., & Fomalont, E. B. 2018, arXiv, 1, doi: [`10.48550/arXiv.1805.05266`](http://doi.org/10.48550/arXiv.1805.05266)

(ref: Cai2019) Cai, Z., Cantalupo, S., Prochaska, J. X., et al. 2019, The Astrophysical Journal Supplement Series, 245, 23, doi: [`10.3847/1538-4365/ab4796`](http://doi.org/10.3847/1538-4365/ab4796)

(ref: Cen2015) Cen, R., & Safarzadeh, M. 2015, Astrophysical Journal Letters, 809, doi: [`10.1088/2041-8205/809/2/L32`](http://doi.org/10.1088/2041-8205/809/2/L32)

(ref: Chakraborty2023) Chakraborty, A., Chatterjee, S., Lacy, M., et al. 2023, The Astrophysical Journal, 954, 8, doi: [`10.3847/1538-4357/ace1e4`](http://doi.org/10.3847/1538-4357/ace1e4)

(ref: Chatterjee2010) Chatterjee, S., Ho, S., Newman, J. A., & Kosowsky, A. 2010, The Astrophysical Journal, 720, 299, doi: [`10.1088/0004-637X/720/1/299`](http://doi.org/10.1088/0004-637X/720/1/299)

(ref: Chowdhury2017) Chowdhury, D. D., & Chatterjee, S. 2017, doi: [`10.3847/1538-4357/aa64d6`](http://doi.org/10.3847/1538-4357/aa64d6)

(ref: Cowie_1996) Cowie, L. L., Songaila, A., Hu, E. M., & Cohen, J. G. 1996, The Astronomical Journal, 112, 839, doi: [`10.1086/118058`](http://doi.org/10.1086/118058)

(ref: Crichton2016) Crichton, D., Gralla, M. B., Hall, K., et al. 2016, Monthly Notices of the Royal Astronomical Society, 458, 1478, doi: [`10.1093/mnras/stw344`](http://doi.org/10.1093/mnras/stw344)

(ref: Drory_2008) Drory, N., & Alvarez, M. 2008, The Astrophysical Journal, 680, 41, doi: [`10.1086/588006`](http://doi.org/10.1086/588006)

(ref: Eftekharzadeh2019) Eftekharzadeh, S., Myers, A. D., & Kourkchi, E. 2019, Monthly Notices of the Royal Astronomical Society, 486, 274, doi: [`10.1093/mnras/stz770`](http://doi.org/10.1093/mnras/stz770)

(ref: Fabian2012) Fabian, A. C. 2012, doi: [`10.1146/annurev-astro-081811-125521`](http://doi.org/10.1146/annurev-astro-081811-125521)

(ref: Fossati2021) Fossati, M., Fumagalli, M., Lofthouse, E. K., et al. 2021, doi: [`10.1093/mnras/stab660`](http://doi.org/10.1093/mnras/stab660)

(ref: Geach2019) Geach, J. E., Peacock, J. A., Myers, A. D., et al. 2019, The Astrophysical Journal, 874, 85, doi: [`10.3847/1538-4357/ab0894`](http://doi.org/10.3847/1538-4357/ab0894)

(ref: Greene_2014) Greene, J. E., Pooley, D., Zakamska, N. L., Comerford, J. M., & Sun, A.-L. 2014, The Astrophysical Journal, 788, 54, doi: [`10.1088/0004-637x/788/1/54`](http://doi.org/10.1088/0004-637x/788/1/54)

(ref: Hall2019) Hall, K. R., Zakamska, N. L., Addison, G. E., et al. 2019, 23, 1

(ref: 10.1093/mnras/stu515) Harrison, C. M., Alexander, D. M., Mullaney, J. R., & Swinbank, A. M. 2014, Monthly Notices of the Royal Astronomical Society, 441, 3306, doi: [`10.1093/mnras/stu515`](http://doi.org/10.1093/mnras/stu515)

(ref: Hunter2023) Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023, Publications of the Astronomical Society of the Pacific, 135, 074501, doi: [`10.1088/1538-3873/ace216`](http://doi.org/10.1088/1538-3873/ace216)

(ref: 2022ApJ...940...47K) Kar Chowdhury, R., Chatterjee, S., Paul, A., Sarazin, C. L., & Dai, J. L. 2022, ApJ, 940, 47, doi: [`10.3847/1538-4357/ac951c`](http://doi.org/10.3847/1538-4357/ac951c)

(ref: Lacy2019) Lacy, M., Mason, B., Sarazin, C., et al. 2019, Monthly Notices of the Royal Astronomical Society: Letters, 483, L22, doi: [`10.1093/mnrasl/sly215`](http://doi.org/10.1093/mnrasl/sly215)

(ref: Lau2018) Lau, M. W., Prochaska, J. X., & Hennawi, J. F. 2018, The Astrophysical Journal, 857, 126, doi: [`10.3847/1538-4357/aab78e`](http://doi.org/10.3847/1538-4357/aab78e)

(ref: Li2021) Li, J., Emonts, B. H. C., Cai, Z., et al. 2021, The Astrophysical Journal Letters, 922, L29, doi: [`10.3847/2041-8213/ac390d`](http://doi.org/10.3847/2041-8213/ac390d)

(ref: 2023ApJ...950..180L) Li, J., Emonts, B. H. C., Cai, Z., et al. 2023, ApJ, 950, 180, doi: [`10.3847/1538-4357/accbbd`](http://doi.org/10.3847/1538-4357/accbbd)

(ref: Mascolo2023) Mascolo, L. D., Saro, A., Mroczkowski, T., et al. 2023, Nature, 615, 809, doi: [`10.1038/s41586-023-05761-x`](http://doi.org/10.1038/s41586-023-05761-x)

(ref: Masters2020) Masters, J. S., Sugimoto, K., Kent, B. R., et al. 2020, Astronomical Data Analysis Software and Systems XXIX, 527

(ref: Meinke2021) Meinke, J., Böckmann, K., Cohen, S., et al. 2021. <http://arxiv.org/abs/2103.01245>

(ref: Miley2008) Miley, G., & Breuck, C. D. 2008, doi: [`10.1007/s00159-007-0008-z`](http://doi.org/10.1007/s00159-007-0008-z)

(ref: Nagai2007) Nagai, D., Kravtsov, A. V., & Vikhlinin, A. 2007, The Astrophysical Journal, 668, 1, doi: [`10.1086/521328`](http://doi.org/10.1086/521328)

(ref: 2020ApJ...905...74N) Nyland, K., Dong, D. Z., Patil, P., et al. 2020, ApJ, 905, 74, doi: [`10.3847/1538-4357/abc341`](http://doi.org/10.3847/1538-4357/abc341)

(ref: Ostriker_2010) Ostriker, J. P., Choi, E., Ciotti, L., Novak, G. S., & Proga, D. 2010, The Astrophysical Journal, 722, 642, doi: [`10.1088/0004-637x/722/1/642`](http://doi.org/10.1088/0004-637x/722/1/642)

(ref: Retana-Montenegro2017) Retana-Montenegro, E., & Röttgering, H. J. 2017, Astronomy and Astrophysics, 600, doi: [`10.1051/0004-6361/201526433`](http://doi.org/10.1051/0004-6361/201526433)

(ref: 2011MNRAS.412..905R) Rowe, B., & Silk, J. 2011, MNRAS, 412, 905, doi: [`10.1111/j.1365-2966.2010.17953.x`](http://doi.org/10.1111/j.1365-2966.2010.17953.x)

(ref: Ruan2015) Ruan, J. J., McQuinn, M., & Anderson, S. F. 2015, Astrophysical Journal, 802, doi: [`10.1088/0004-637X/802/2/135`](http://doi.org/10.1088/0004-637X/802/2/135)

(ref: Sazonov1998) Sazonov, S., & Sunyaev, R. 1998, The Astrophysical Journal, 508, 1, doi: [`10.1086/306406`](http://doi.org/10.1086/306406)

(ref: Scannapieco2004) Scannapieco, E., & Oh, S. P. 2004, The Astrophysical Journal, 608, 62, doi: [`10.1086/386542`](http://doi.org/10.1086/386542)

(ref: Scannapieco2008) Scannapieco, E., Thacker, R., & Couchman, H. 2008, The Astrophysical Journal, 678, 674, doi: [`10.1086/528948`](http://doi.org/10.1086/528948)

(ref: 2013BASI...41...61S) Shen, Y. 2013, Bulletin of the Astronomical Society of India, 41, 61, doi: [`10.48550/arXiv.1302.2643`](http://doi.org/10.48550/arXiv.1302.2643)

(ref: Silk1998) Silk, J., & Rees, M. J. 1998, 4, 4

(ref: Soergel2017) Soergel, B., Giannantonio, T., Efstathiou, G., Puchwein, E., & Sijacki, D. 2017, Monthly Notices of the Royal Astronomical Society, 468, 577, doi: [`10.1093/mnras/stx492`](http://doi.org/10.1093/mnras/stx492)

(ref: 1972CoASP...4..173S) Sunyaev, R. A., & Zeldovich, Y. B. 1972, Comments on Astrophysics and Space Physics, 4, 173

(ref: casa2022) The CASA Team, Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacific, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Timlin2018) Timlin, J. D., Ross, N. P., Richards, G. T., et al. 2018, The Astrophysical Journal, 859, 20, doi: [`10.3847/1538-4357/aab9ac`](http://doi.org/10.3847/1538-4357/aab9ac)

(ref: Treu_2005) Treu, T., Ellis, R. S., Liao, T. X., & van Dokkum, P. G. 2005, The Astrophysical Journal, 622, L5, doi: [`10.1086/429374`](http://doi.org/10.1086/429374)

(ref: Verdier2016) Verdier, L., Melin, J. B., Bartlett, J. G., et al. 2016, Astronomy and Astrophysics, 588, doi: [`10.1051/0004-6361/201527431`](http://doi.org/10.1051/0004-6361/201527431)

(ref: VillarMartin2021) Villar-Martín, M., Emonts, B. H. C., Lavers, A. C., et al. 2021, Astronomy & Astrophysics, 650, A84, doi: [`10.1051/0004-6361/202039642`](http://doi.org/10.1051/0004-6361/202039642)

(ref: White2012) White, M., Myers, A. D., Ross, N. P., et al. 2012, Monthly Notices of the Royal Astronomical Society, 424, 933, doi: [`10.1111/j.1365-2966.2012.21251.x`](http://doi.org/10.1111/j.1365-2966.2012.21251.x)

</paper>

Write the methods card for this paper.