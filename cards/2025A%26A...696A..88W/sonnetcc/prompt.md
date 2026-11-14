# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...696A..88W\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...696A..88W",
 "title": "JWST + ALMA ubiquitously discover companion systems within ≲18 kpc around four z ≍ 3.5 luminous radio-loud AGN",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Wang, Wuji",
 "n_authors": 14,
 "arxiv_id": "2502.20442",
 "doi": "10.1051/0004-6361/202553668",
 "alma_projects_linked_by_archive": [
  "2021.1.00576.S"
 ]
}
```

Paper text:
<paper>
#  *JWST* + ALMA ubiquitously discover companion systems within $\lesssim18\,$kpc around four $z$$\approx$3.5 luminous radio-loud AGN

# Introduction

The hierarchical model for galaxy evolution suggests that galaxy-galaxy mergers are one of the important mechanisms in stellar mass build-up (cite: Moster_2018; Behroozi_2019). The fraction of mergers, $f_{\mathrm{MM}}$, is found to be higher in the early universe (cite: Romano_2021). The merger fraction evolution mirrors the trend of star formation rate (SFR) density through cosmic history with a peak around $z\sim3$ (cite: MandD_2014; Husko_2022). Given that the growth rate of supermassive black holes (SMBHs) related to active galactic nuclei (AGN) activity, also follows the cosmic SFR density evolution (cite: Heckman_2014), it is reasonable to conclude that the galaxy-galaxy interactions play an important role in feeding black holes and building stellar mass by either direct collapse or stimulating star formation. Indeed, simulations show that the merger processes enhance starbursts (cite: Hopkins_2008d; Hopkins_2008). Quasar activity is also shown to be related to mergers, suggesting that they play an important role in both the feeding and feedback processes (cite: Pierce_2023).

Early works studying mergers were hampered by limited resolution and sensitivity. The detection of mergers is difficult without kinematic information. The successful operation of *JWST* provided the opportunity for a clearer look. Using NIRCam, (cite: Gupta_2023) reported that the extreme emission lines observed at $z\sim3$ could be driven by major mergers. (cite: Dalmasso_2024) quantified the morphologies of $z>4$ galaxies and reported the fraction rate of mergers even beyond the epoch of reionization. In addition to imaging, NIRSpec is a more powerful tool for merger studies especially with its integral field unit (IFU) mode. For example, (cite: Jones_2024) studied the ionized gas kinematics of a dense cluster system at $z\sim6.34$ with the NIRSpec IFU. Resolution-matched observations by Atacama Large Millimeter/submillimeter Array (ALMA) are equally important for high-redshift companion studies. For example, the far-infrared (FIR) line \[C II\]$158\rm \mu m$ (hereinafter \[C ii\]), redshifted into the spectral window of ALMA, is a more reliable tracer of cold gas dynamics than the warm ionized optical lines which are affected by strong AGN (cite: Lagache_2018; Dessauges-Zavadsky_2020). Simultaneously, the continuum underneath offers us information on the dust content of the galaxies whose detections and morphologies are very useful in the context of merger studies (cite: Faisst_2020; Romano_2021).

It is of significant interest to look at the so called transition period from Cosmic Dawn to Noon (i.e., $3\lesssim z \lesssim 6$) and study how the growth of SMBHs and star formation are reaching their peak. This period of time is important to look for the quenching of some of the most massive galaxies and energetic AGN (cite: Suzuki_2022). Among the quasar species, high-redshift radio galaxies (cite: Miley_2008) uniquely useful for investigating close companions and mergers. HzRGs are type-2 quasars, thereby offering a clean view of the vicinity around the host galaxy with the “natural coronograph" blocking the bright quasar (cite: vernet_2001). It has been proposed that mergers are a possible trigger of the powerful jet (radio-loud AGN), but the link is elusive (cite: Chiaberge_2015). With joint *JWST* and ALMA observations, we can search for companions, and merger candidates, on tens of kiloparsec scales, moving a step towards understanding the ignition of HzRGs and their impact on galaxy evolution.

HzRGs are known to be beacons tracing dense, proto-cluster, environments (cite: Venemans_2007). Particularly, imaging and spectroscopic observations exploiting *Spitzer*, *Herschel* and the *Hubble Space Telescope* (HST) have shown the robust detection of companion galaxies (cite: Galametz_2012; Ivison_2012; Wylezalek_2013; Wylezalek_2014; Noirot_2016; Noirot_2018). Using MUSE/VLT, (cite: Vernet2017) and (cite: wang2023) found evidence that the $\sim100\,$kpc-scale emission halos around HzRGs are “contaminated" by companions, which also supports this scenario. These works provided information about early clustering and AGN feedback on the scale of circumgalactic medium (CGM) and beyond. Due to the technical constraints, studies of the environments around HzRGs so far are limited to the CGM. Several works have looked into well-known HzRGs with starbursts using primarily observations from ALMA. The Dragonfly Galaxy ( at $z=1.92$) is found to be going through a major merger process with a gas rich companion (cite: Emonts_2015; ZhongYuxing_2024; Lebowitz_2023). , at $z=3.8$, also shows evidence of a merger with a molecular stream feeding star formation (cite: Rocca-Volmerange_2013; Emonts_2023). (cite: Perez-Martinez_2024) and (cite: Shimakawa_2024) studied the famous HzRG proto-cluster, the Spiderweb at $z=2.16$, with NIRCam. So far, there are only two HzRGs with published *JWST* IFU observations. On $\sim20\,$kpc scales, (cite: Wang_2024) reported a tentative detection of a companion to at $z=3.59$. There is also evidence of a companion to at $z=4.1$ which is known to reside in a dense environment (cite: Duncan_2023; Roy_2024; Saxena_2024). It is of great interest to inspect the new *JWST* data together with resolution-matched ALMA data and study nearby companions on galactic scales for a sample of HzRGs. This is crucial to understand triggering of the most powerful cosmic jets and the evolution of their massive host galaxies (cite: Seymour_2007; DeBreuck_2010).

In this paper, we present the first joint analysis of *JWST*/NIRSpec IFU and ALMA Band 8 observations of a sample of four HzRGs at $z\approx3.5$ and focus on the detection of nearby companions. Throughout this paper, we use the term “companion" for an emission-line component that has either a spatial or velocity offset from the central source. In Sect. [2](#sec:data_process), we summarize the sample properties and data processing. We present the detection methods and discuss individual companions in Sects. [3](#sec:analysis) and [4](#sec:results), respectively. Finally, we provide an estimate of companion masses and discuss our results in Sect. [5](#sec:discussion). Throughout this paper, we assume a flat $\Lambda$ cosmology with $H_{0} = 70\, \rm{km\,s^{-1}\,Mpc^{-1}}$ and $\Omega_{m}=0.3$. Following this cosmology, $\rm{1\,arcsec=7.25-7.32\, kpc}$ at the redshifts in this study.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target | RA, Dec (J2000) | Redshift | *JWST* WCS shift | ALMA beam | Stellar mass | SFR |
|  | (hh:mm:ss, dd:mm:ss) | $z_{\rm sys}$ | ($\Delta \alpha$, $\Delta \delta$) | $\theta_{\rm 400GHz}$ | $\log(M_{\star}/M_{\odot})$ | $M_{\odot}\,\mathrm{yr^{-1}}$ |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(5\) | \(6\) |
| TN J0121+1320 | (01:21:42.725, +13:20:58.26) | 3.5190$^{\rm{(\dag)}}$ | ($-0.210\ensuremath{''}$, $+0.003\ensuremath{''}$) | $0.19\ensuremath{''}$$\times$$0.15\ensuremath{''}$ | 11.02 | $626$ |
| TN J0205+2242 | (02:05:10.676, +22:42:50.57) | 3.5060$^{\rm{(\dag)}}$ | ($-0.122\ensuremath{''}$, $-0.181\ensuremath{''}$) | $0.14\ensuremath{''}$$\times$$0.12\ensuremath{''}$ | 10.82 | $<84$ |
| 4C+03.24 | (12:45:38.377, +03:23:21.14) | 3.5657$^{(\rm{\ddag})}$ | ($-0.161\ensuremath{''}$, $-0.131\ensuremath{''}$) | $0.23\ensuremath{''}$$\times$$0.18\ensuremath{''}$ | $<11.27$ | $142$ |
| 4C+19.71 | (21:44:07.512, +19:29:14.58) | 3.5892$^{\rm{(*)}}$ | ($-0.014\ensuremath{''}$, $+0.173\ensuremath{''}$) | $0.23\ensuremath{''}$$\times$$0.18\ensuremath{''}$ | $<11.13$ | $84$ |

Table notes: (1) Name of the HzRG. (2) Coordinate of the radio core, i.e., AGN. (3) Systemic redshifts of the HzRG based on or The typical uncertainty is $\pm0.0004$. (4) WCS correction of the NIRSpec IFU data cube. (5) Size and position angle of the synthesized beam of the cleaned ALMA cube combined with two consecutive spectral windows. Robust = +0.5 Briggs weighting was applied for TN J0121+1320 and 4C+19.71 and robust = +2.0 Briggs weighting was applied for TN J0205+2242 and 4C+03.24. (6) Stellar mass, $M_{\star}$, and SFR from (cite: DeBreuck_2010) and (cite: Falkendal_2019) based on SED fitting.

# Sample, observations and data processing

## HzRGs sample

In this work, we search for signatures of companions and/or mergers around four HzRGs at $z\approx3.5$ through joint observations by *JWST*/NIRSpec and ALMA. These HzRGs come from a group of eight at $z$$\approx$3–5 which have multi-wavelength supporting datasets (cite: Seymour_2007; DeBreuck_2010; Nesvadba_2007a; Nesvadba_2017b). In particular, they have observations from MUSE and ALMA Band 3 focusing on the ionized CGM gas (in rest frame UV) and molecular gas (cite: wang2023; kolwa2023). Our new NIRSpec IFU and new ALMA Band 8 observations cover rest frame optical and FIR in three-dimensional (3D) data cubes at matched sub-kpc resolution.

Besides the prerequisite selection for multi-wavelength coverage in three dimensions, these four HzRGs also have a wide range of host properties and radio morphologies. Their host galaxies are very massive with $M_{\star}\sim10^{11}\,M_{\odot}$. Their SFR span a wide range from upper limit of $84\,M_{\odot}\,\mathrm{yr^{-1}}$ () to $\sim 626 \,M_{\odot}\,\mathrm{yr^{-1}}$ (, Table [\[tab:sampleobs\]](#tab:sampleobs)). is found to be on the $M_{\star}-$SFR main sequence, while the others show signatures of quenching (cite: Falkendal_2019; kolwa2023). is also the only source with an unresolved radio morphology. The others all have double-lobed morphologies. has the most extended jet, with two hot spots separated by $\sim60\,$kpc (cite: Pentericci_1999). shows evidence of a jet being deflected (cite: vanOjik_1996). This variety in radio morphology implies differences in terms of jet age, range over which jet-cloud interactions can take place, and etc.

The systemic redshifts of the sample used in this work are presented in Table [\[tab:sampleobs\]](#tab:sampleobs). Except for , the systemic redshifts are derived from He ii1640 or \[C i\](1-0) (\[C i\] hereafter) emission at the radio core (cite: kolwa2023). The \[C i\] emission of was known to have $\Delta v_{[C i]}=1123\pm282\,\rm km\,s^{-1}$ redshifted from the warm ionized gas prior to *JWST* observations (cite: wang2023). This is confirmed by our new NIRSpec IFU data. Throughout this work, we adopt the redshift determined from \[O iii\]$5007$ based on VLT/SINFONI data (cite: Nesvadba_2017b). These redshifts are from observations with lower spatial resolution and sensitivity than the data presented here. They are assumed to trace diffused gas ionized by the AGN and are found typically within $\sim300\,\rm km\,s^{-1}$ of the core \[O iii\]$5007$ velocity measured by NIRSpec IFU.

We note that there was no prerequisite for any of the HzRGs to be in cluster environments on large scales. The only common features of these four are their similar redshifts, multi-wavelength supporting data, and bright Ly$\alpha$ emission nebulae.

![](Figures/O3_dv_map/O3_chan_comp_TNJ0121.pdf)

![](Figures/CII_companions/C2_comp_TNJ0121.pdf)

![](Figures/Full_Continuum_spectra_J0121_CII_B.png)

![](Figures/CII_Barolo_fit/TN_J0121+1320_maps_dv_paper.pdf)

![](Figures/O3_dv_map/O3_chan_comp_TNJ0205.pdf)

![](Figures/CII_companions/C2_comp_TNJ0205.pdf)

![](Figures/O3_dv_map/O3_chan_comp_4C03.pdf)

![](Figures/CII_companions/C2_comp_4C03.pdf)

![](Figures/O3_dv_map/O3_chan_comp_4C19.pdf)

![](Figures/CII_companions/C2_comp_4C19.pdf)

![](Figures/CII_Barolo_fit/4C19.71_maps_dv_paper.pdf)

## JWST/NIRSpec IFU

The NIRSpec IFU data presented here were taken from the *JWST* Cycle 1 General Observer (GO) program JWST-GO-1970 (PI: Wuji Wang) between UT 2022 October 30 and 2023 August 29. Our observations targeted the four HzRGs (Sect. [2.1](#subsec:sample)) at $z\approx3.5$ using G235H/F170LP. This offers the wavelength coverage of $1.70-3.15\,\mathrm{\mu m}$ in the observed frame or $\sim3700-7620\,\mathrm{\AA}$ in the rest frame with a spectral resolution of $85-150\,\mathrm{km\,s^{-1}}$. In this setup, we capture all major optical emission lines seen in type-2 AGN (i.e., \[O ii\]$3726,\,3729$ to H$\alpha$, including \[S ii\]$6716,6731$) at once (cite: Zakamska_2003). We adopted a 9-point dither pattern and the improved reference sampling and subtraction (IRS$^2$) read-out pattern. The total on-source exposure time ranged from 3.7 to 4.0 h per target. For and , we included the leakage exposure, $\sim0.4$ h each, to identify contamination light due to failed open shutters on the microshutter array (MSA) at the first dither position. For and , we designed pointing verification imaging exposures, $\sim233$ s each, after the science observation with MSA shutters all-open to improve the astrometry (cite: Wang_2024).

We downloaded all raw data from the Mikulski Archive for Space Telescopes (MAST). We used v1.13.4 of the *JWST* Science Calibration pipeline[^1] with the Calibration Reference Data System (CRDS) context file jwst_1202.pmap. Our procedure is similar to (cite: Vayner_2023Q3D) and (cite: Wang_2024). Specifically, we executed the standard first and second stages of the pipeline. We subtracted the $1/f$ noise from the rate files resulted from stage 1. The stage 3 of the standard pipeline does not perform well the outlier rejection. Therefore, we used sigma clipping to combine the dithered exposures into the final data cube. The primary source of outliers for our observations is likely cosmic rays due to the adopted readout mode. We did not include flux calibration step as in (cite: Wang_2024) since the standard pipeline already has a good performance (i.e., relative flux difference $<5\%$ for ). The flux density unit of the final cube was converted into $\mathrm{erg\,s^{-1}\,cm^{-2}\,\AA^{-1}}$.

Through out the field of view (FoV), there is an uniform background continuum emission with a flux density of several $\mathrm{10^{-21}\,erg\,s^{-1}\,cm^{-2}\,\AA^{-1}}$, and it is brighter at shorter wavelength. To subtract this background, we first extracted the median background spectrum by spatially masking the continuum emission sources and continuum-like patterns (presumably leakage emission from the MSA). Then, we fitted a fifth or sixth order polynomial to the median background spectrum. Finally, we subtracted this fitted contribution from the whole data cube. The final cubes have a rms noise at 2.6$\,\rm \mu m$ of $\sim4$ to $6\times \mathrm{10^{-22}\,erg\,s^{-1}\,cm^{-2}\,\AA^{-1}}$ per wavelength channel.

The point spread function (PSF) of the NIRSpec IFU depends on wavelength and spatial position. The HzRGs analyzed in the paper are all type-2 AGN, meaning the presumed bright point-like quasar is obscured. Hence, it is not necessary for us to subtract the PSF of the quasar. The full width at half maximum (FWHM) of the *JWST* PSF used in this work is given as the one constructed in (cite: Vayner_2023Q3D_2), which has a typical size of $\sim0.11\ensuremath{''}$.

## ALMA Band 8

Our ALMA Band 8 observations were taken under the program ID 2021.1.00576S (PI: Wuji Wang). The observations of and were fully carried out. For the remaining two, only half of the proposed integration times were executed. Despite the shallow exposure time, \[C ii\] lines are detected in the field of and . However, the FIR continuum of these two are undetected. These observations were carried out in C43-5 configuration between UT 2022 June 17 and 2022 August 10. We set up one spectral window in Band 8 to be centered at the redshifted frequency of \[C ii\] ($\nu_{\rm rest}=1900.537\,$GHz). Then, the other three spectral windows were used to observe dust emission. We note that the unexpected broad \[C ii\] line width relative to the width of spectral window (1.875$\,$GHz $\sim$ 1350$\,\rm km\,s^{-1}$) and the redshift uncertainty end up of the line detection in two consecutive spectral windows, especially and (see processing below). The default ALMA bandpass and phase calibrations were adopted.

We processed the data using the Common Astronomy Software Applications for Radio Astronomy v6.6.0 (cite: CASA_2022). The task `tclean` was used to clean the cube down to a $2\sigma$ level. For and , we use the cubes with Briggs weighting of robust$=+0.5$ in the analysis. For and , we use the cubes with Briggs weighting of robust$=+2.0$. This provides higher signal to noise ratio (S/N) with a trade off in spatial resolution. We cleaned the two consecutive spectral windows with \[C ii\] together without continuum subtraction in the $uv-$plane. The shapes of the spectra at the transition frequencies of the two windows were compared to the cubes cleaned individually. We did not find any jump in flux. Throughout the paper, we used the cubes and continuum maps (for the two with detections) after the primary beam correction. The final cubes were smoothed to $14,\rm km,s^{-1}$ per channel. The choice of resolution element is a balance among S/N, continuum coverage and a sufficient number of channels for dynamical study (especially for TN J0121+1320 and 4C+19.71). The rms noise of the \[C ii\] cubes at the systemic redshift are $3.0\,\rm mJy\,beam^{-1}$, $1.3\,\rm mJy\,beam^{-1}$, $1.1\,\rm mJy\,beam^{-1}$, and $1.0\,\rm mJy\,beam^{-1}$ per channel for , , , and , respectively. The rms noise for the continuum maps constructed from the individual spectral windows are $76\,\rm \mu Jy\,beam^{-1}$ and $92\,\rm \mu Jy\,beam^{-1}$ for and , respectively. The continuum images for these two targets from the spectra windows centered at the lowest frequency, i.e., separated the most from the windows with line emission. For the remaining two without FIR continuum detections, we report $3\sigma$ upper limits of $0.28\,\rm mJy\,beam^{-1}$ and $0.25\,\rm mJy\,beam^{-1}$ for and , respectively. These upper limits were calculated from the continuum images constructed using all four spectral windows.

## Astrometric alignment of NIRSpec IFU cubes

The absolute astrometric calibration of NIRSpec IFU observations is known to have a $\sim0.2-0.3\ensuremath{''}$ uncertainty (cite: Perna_2023; Wang_2024). Hence, we manually align the World Coordinate System (WCS) of our targets to other datasets with known WCS. Our manual shifts are summarized in Table [\[tab:sampleobs\]](#tab:sampleobs). The assumption behind this alignment is that the continuum detected by the NIRSpec IFU is at the position of the radio AGN (i.e., core position of the radio jet). The NIRSpec IFU continuum may be affected by leakage light through microshutter array and other artifacts. We checked the continuum and found that the continuum centroids are often close, $<0.1\ensuremath{''}$, to the position of the brightness peak of the emission lines (e.g., \[O iii\]5007), which supports our assumption. Specifically, to determine the alignment, we fitted a 2D Gaussian profile to the continuum of the radio galaxy at observed wavelength $2.6\,\rm \mu m$ (i.e., line-free region at rest frame $\sim5770\AA$ at $z=3.5$). Similarly, we fit a 2D Gaussian profile to the radio core observed at $8.4\,$GHz (cite: vanOjik_1996; Nesvadba_2007a; Nesvadba_2017b). We then shifted the WCS of the NIRSpec IFU to match the radio data.

The case of is complex. Its compact radio emission has an offset of $\sim1\ensuremath{''}$ from the ALMA Band 8 dust position. Assuming that the WCS of the two interferometers are accurate, this may already suggest an offset likely due the existence of companions. In addition, we find a foreground galaxy at $z=1.4577$ in the NIRSpec IFU cube as well as the MUSE cube whose continuum may contaminate (cite: wang2023). It is located to the north of the radio emission with a projected offset of $\sim0.5\ensuremath{''}$. There is another continuum source detected by the NIRSpec IFU located west of the radio emission with an offset of $\sim0.7 \ensuremath{''}$ (discussed in Sect. [4.1](#subsec:comp_0121)). This continuum position is not at the same position as the brightness peak of the optical line (e.g., \[O III\]5007). The projected separations quoted here are prior to the astrometric correction. Assuming the WCS assigned by the *JWST* pipeline is accurate to $\sim0.2\ensuremath{''}$ to $0.3\ensuremath{''}$, this western continuum may not be the emission associated with the radio galaxy. Hence, our correction procedure for is based on the foreground object in the north. As its continuum is faint and presumably blended with by MUSE, we used the fitted 2D Gaussian positions of the foreground \[O ii\]$3726,3729$ line in the MUSE data cube and its \[S iii\]$9533$ line in NIRSpec IFU data cube to determine the WCS correction. The narrow band \[O ii\]$3726,3729$ line emission map is spatially unresolved which leads to less uncertainty in the position determination. The resulting shift is $-0.21\ensuremath{''}$ and $0.003\ensuremath{''}$ in RA and Dec, respectively, consistent with the expected systemic uncertainty. After the correction, we found that the western optical continuum is aligned with the ALMA dust position.

In (cite: Wang_2024), we used one of the foreground galaxies to determine the astrometric correction (G1 in their naming format and using imaging data from *HST*). In this work, we updated the reduction of the $8.4\,$GHz radio observation where the previously unseen radio core is now detected at $5\sigma$ (cite: Nesvadba_2017b). The aligned WCS of in this work has an offset of $\sim0.16\ensuremath{''}$ from the one in (cite: Wang_2024). In addition, the position of the dust continuum observed by ALMA Band 8 is aligned with the radio core (Sect. [2.3](#subsec:alma_obs)).

## Radio maps

In this work, we only used the radio observations to trace the position of the jets. We adopted the VLA X-Band ($8.4\,$GHz) radio maps of published in (cite: Nesvadba_2007a).

We used the new radio data of in this work (cite: vanOjik_1996; wang2023). The observation of 4C+03.24 was carried on UT 2024 December 20, UT 2025 January 02, and UT 2025 January 03 with the VLA in A configuration in the Ku-band covering a frequency range of 12 to 18 GHz (Project 24B-147, PI: Carlos De Breuck). The target was observed for 5 h (8.7 h in total) over a contiguous Local Sidereal Time (LST) range for good sampling of the $uv$-plane. The 6 GHz bandwidth was split into 48 spectral windows of 128 channels of 2 MHz width each, and a sample integration time of 2 s. 3C286 and J1224+0330 were used as the ﬂux and phase calibrators, respectively. Pointing calibration was also performed using both sources. The data were then cross-calibrated, imaged and self-calibrated in CASA. The final image was made using Briggs weighting with a `robust = 0.0`. We obtained a resolution of $0.15\ensuremath{''}\times0.13\ensuremath{''}$ (PA=56.5$^{\circ}$) and rms noise of $\sim$4.5$\rm \mu Jy\,beam^{-1}$.

We reprocessed archival VLA C-band observations of () using CASA and detected the previously unseen radio core (cite: Nesvadba_2017b). The observation was carried on UT 2012 December 22 with the VLA in A configuration (Project code: 12B-243). The target was observed for $\sim$15 min with an integration time of $1\,$s and 16 spectral windows of 128$\,$MHz bandwidth each, between 4.15 and 7.85$\,$GHz. For our analysis, we only used the 8 spectral windows from 6.95 to 7.85$\,$GHz. Each spectral window consisted of 32 channels of 4$\,$MHz width. 3C 48 and J2139+1423 were used as the ﬂux and phase calibrators, respectively. The data were manually ﬂagged and cross-calibrated in CASA, set to the same ﬂux scale as above. Imaging and self-calibration were then performed using the tasks `tclean` and `gaincal` respectively. The ﬁnal image was made using Briggs weighting with robust$=+0.5$. We obtained a resolution of 0.25$\ensuremath{''} \times 0.24\ensuremath{''}$ and an rms noise of $\sim17\, \rm \mu Jy\,beam^{-1}$.

We reprocessed archival VLA X-band observations of , carried out on UT 1998 May 07 with the VLA in A configuration (Project code: AY92). The target was observed for $\sim$9$\,$min with an integration time of 10$\,$s and two spectral windows of 50$\,$MHz bandwidth centered at 8.435 and 8.485$\,$GHz each. 3C 286 and J0121+118 were used as the ﬂux and phase calibrators, respectively. The data were manually ﬂagged and cross-calibrated using Astronomical Image Processing System (cite: Greisen_2003). The ﬂux scale was set according to (cite: Perley_2017). The data were then imaged using CASA. The ﬁnal image was made using task `tclean` and Briggs weighting with robust$=-0.5$. We obtained a resolution of 0.24$\ensuremath{''} \times 0.24\ensuremath{''}$ and rms noise of $\sim90\,\rm \mu Jy\,beam^{-1}$. We were not able to perform reliable self-calibration of the data due to the low S/N of the solutions. However, the source position is still reliable, which is the only information used in this analysis.

# Analysis

In this section, we first describe general methods used to search for companions around our radio AGN. We used two independent approaches to identify companion systems: (i) peculiar kinematics of warm ionized gas observed by *JWST*/NIRSpec IFU (\[O iii\], Sect. [3.1](#subsec:O3_kine)) and (ii) cold gas observed by ALMA (\[C ii\], Sect. [3.2](#subsec:c2_detection)). We also look for continuum emission from the companions detected by the two methods (Sect. [3.3](#subsec:cont_method)). We note that a systematic continuum study is beyond the scope of this work, especially optical continuum studies which would require careful treatment in data processing. Hence, in this paper, we do not leverage detection of continuum as evidence for a companion. We name the companions by their central radio AGN followed by the detection method. For example, the companion in the field of TN J0121+1320 detected through \[O iii\] is named as J0121-\[O iii\]. If more than one companion is detected in the same field using the same method, we name these alphabetically in the order of redshift. For example, the \[C ii\] companion with the lowest redshift in the field of 4C+03.24 is named as 4C03-\[C ii\]-A. There is a companion detected in both methods (i.e., J0121-\[O iii\] and J0121-\[C ii\]-C may be one companion, see Sect. [4.1](#subsec:comp_0121)). We note that our analysis may not be complete in the sense of detecting all possible companion sources in the fields of the radio galaxies, but we focus here specifically on peculiar warm ionized gas kinematics and \[C ii\] detections. Furthermore, we deliberately refer to the detected structures as companions rather than galaxies as we do not necessarily detect stellar continuum at each location. These companions could therefore also represent isolated gas clouds, possibly related to ongoing jet activity as suggested in simulations (cite: Ondaro-Mallea_2024).

## Warm ionized gas kinematics

We first search for peculiar ionized gas kinematics captured by the NIRSpec IFU as a signature of companions. \[O iii\]$5007$ is one of the brightest optical emission lines and is a traditional kinematic tracer of warm ionized gas around AGN (cite: Harrison_2014). Using VLT/SINFONI observations of \[O iii\]$5007$, (cite: Nesvadba_2007a; Nesvadba_2017b) analyzed the ionized gas kinematics of a large sample HzRGs, including our targets. At a spatial resolution of $\sim0.5\ensuremath{''}$ to $0.8\ensuremath{''}$, the bulk motion of the ionized gas is found to be consistent with jet-driven outflows. *JWST*/NIRSpec IFU makes it possible to examine the sub-kpc kinematics at and beyond Cosmic Noon with the same tracer (cite: Perna_2023; Vayner_2023Q3D_2; Wang_2024). As pointed by some studies, the nature of some outflows may be confined on smaller scales, only evident at finer resolution and high sensitivity (cite: Wang_2024; Holden_2024_MUSE). When focusing on the vicinity ($\lesssim18\,$kpc) of the brightest quasars, we often have \[O iii\]$5007$ out to the edge of the FoV. Hence, we classify a \[O iii\]$5007$ emitter as a companion in this study by leveraging the full 3D information of the data cube.

Specifically, we visually inspect the \[O iii\]$5007$ emission at different velocity channels (e.g., Fig. [1](#fig:O3_chanmap_0121)a[1](#fig:O3_chanmap_0121)b and Appendix [7](#app:o3_channel)). For each target, we detect line-emitting gas blobs of $\sim3-6\,$kpc extent which are kinematically distinct from the tens of kiloparsecs scale velocity fields seen in the SINFONI data. That is to say, these blobs are different from either large-scale outflows or gaseous nebula at the systemic redshift. To further separate the companion emission, we decompose these line-emitting components by fitting $r=0.1\ensuremath{''}$ aperture-extracted spectra using `q3dfit` (cite: Wylezalek_2022q3d; Rupke_2023q3dfit). In `q3dfit`, the wavelength dependent spectral resolution is taken into account. The fitting is done simultaneously for all bright emission lines covered, namely \[O ii\]$3726,3729$, H$\beta$, \[O iii\]$4959,5007$, H$\alpha$, \[N ii\]$6548,6583$, and \[S ii\]$6716,6731$, while keeping the Gaussian components for different lines kinematically tied (cite: Vayner_2023Q3D; Wang_2024). The flux ratios of doublets are set according to atomic physics: $F_{\rm [O iii]5007}$/$F_{\rm [O iii]4959}=3$ and $F_{\rm [N ii]6583}$/$F_{\rm [N ii]6548}=3$. We limit $F_{\rm [S ii]6716}$/$F_{\rm [S ii]6731}$ to the range \[0.4375, 1.4484\] and fixed the ratio of spectrally unresolved $[O ii]3726,3729$ to $F_{\rm [O ii]3726}$/$F_{\rm [O ii]3729}=1$ (cite: Sanders_2016). The optimized number of components are determined by `q3dfit`, with a maximum allowed number as input. For comparison, we also fit the spectra at central AGN positions through the same procedure (e.g., Fig. [1](#fig:O3_chanmap_0121)c). The fitting results are presented in Table [1](#tab:1d_o3_spec_fit).

We further map the companion emissions spatially to demonstrate their offset from the bulk emission on larger scales. Using `q3dfit`, we fit spaxel-based spectra around the companion positions. Due to the limitation of S/N and the focus on kinematics, we limit this spatial fit only to \[O iii\]$4959,5007$. We detect velocity gradients for three out of the four \[O iii\] emission blobs. The gradient detection of 4C19-\[O iii\] is tentative. We present the velocity shift maps and exemplar spectra at both ends of the gradient to demonstrate the gas kinematics (e.g., Fig. [1](#fig:O3_chanmap_0121)d[1](#fig:O3_chanmap_0121)e). We refer to these line-emitting gaseous blobs with peculiar kinematics as “\[O iii\] companions" and examine them individually below.

## \[C ii\] emitters

The brightest FIR emission line, \[C ii\] is a frequently used gas tracer at high-redshift (cite: Lagache_2018; Dessauges-Zavadsky_2020). Directly associated with photodissociation regions, the detection of \[C ii\] may indicate the presence of cold gas systems. Moreover, it has been used as a kinematic tracer of regular motion (e.g., rotation) and merger activity (cite: Lelli_2021; Romano_2021; Herrera-Camus_2022).

We examine the ALMA Band 8 data cubes and detect at least one \[C ii\] emitters at $\gtrsim3\sigma$ in the field around each the four radio AGN. We present the \[C ii\] moment 0 maps constructed from velocity channels where emission is detected (e.g., contours in Fig. [2](#fig:j0121_c2_map_sp)a). We then extract 1D spectra at the position of \[C ii\] emitters (e.g., Fig. [2](#fig:j0121_c2_map_sp)b). For the field of TN J0121+1320 and 4C+19.71, we use apertures with the size of the major synthesized beam. For TN J0205+2242 and 4C+03.24, we increase the aperture to twice the size of major synthesized beam to increase the S/N. We perform line fitting to the 1D spectra with one Gaussian component (Table [\[tab:1d_c2_spec_fit\]](#tab:1d_c2_spec_fit)). For the brighter \[C ii\] companions (S/N$>10\sigma$; i.e., J0121-\[C ii\]-B and 4C19-\[C ii\], see Sect. [4.1](#subsec:comp_0121) and [4.4](#subsec:comp_4c19)), we also conduct spatial fitting using $^{\rm 3D}$BAROLO to study the dynamics of the cold ionized gas (cite: DiTeodoro_2015).

We refer to these \[C ii\] emitting systems as “\[C ii\] companion" and examine them individually below. To compare the warm and cold ionized gas at the position of \[C ii\] companions, we overlay the \[O iii\] surface brightness map and 1D spectra with the \[C ii\] moment 0 map and spectra (e.g., Fig. [2](#fig:j0121_c2_map_sp)). Without further information, we cannot rule out the possibility that the “\[C ii\] emissions" without corresponding \[O iii\] emission or dust continuum (Sect. [3.3](#subsec:cont_method)) are different lines detected at different redshifts. In this paper, we assume the lines detected by ALMA Band 8 are \[C ii\] at similar redshifts to the central HzRGs.

## Continuum check

We examine the continuum at the positions of each of the \[O iii\] and \[C ii\] companions (Table [\[tab:summa_comp\]](#tab:summa_comp)). For potential companions, we may expect optical continuum emission, captured by NIRSpec IFU, which would presumably be dominated by evolved stellar populations. The ALMA Band 8 continuum (i.e., rest frame $\sim150\,\rm \mu m$) is emitted by cold dust which may trace forming stars. The case becomes more complicated with the presence of an AGN that could dominate the optical continuum (cite: Wang_2024). Excluding the companions near the radio AGN, we only find that J0121-\[C ii\]-B shows optical continuum emission (Fig. [3](#fig:sp_0121_continuum_opt)). As for FIR continuum, we detect emission from J0121-\[C ii\]-A, J0121-\[C ii\]-B, and 4C19-\[C ii\].

The most interesting case is from the field of (Sect. [4.3](#subsec:comp_4c03)). We discovered a tail-like continuum towards the south. It has a similar morphology to the systemic \[O iii\]5007 emission. MUSE observation also captured UV continuum with a similar morphology (Appendix [10.2](#app:4C03_fore)).

# Results

In this section, we report evidence for nearby companions around our radio AGN following the methods in Sect. [3](#sec:analysis). Since the nature (i.e., interpretation of the gas dynamics) are unique for each target, we examine them individually. The properties of the companions detected in this work are summarized in Table [\[tab:summa_comp\]](#tab:summa_comp).

## Companions of TN J0121+1320

is the only target in our sample without a clearly resolved radio core. In this section, we first define the position of the radio AGN and then present evidence of nearby companions around it.

### Radio core of TN J0121+1320

The radio emission from has a compact morphology even in the highest resolution 8.4$\,$GHz dirty image ($\sim0.3\ensuremath{''}$). It only shows an elongation along the east-west direction (e.g., green contours in Fig. [1](#fig:O3_chanmap_0121)a[1](#fig:O3_chanmap_0121)b). We adopt the west peak of this elongation as the radio core based on: (i) its position being closer to the peak position of the line emission (e.g., \[O iii\]$5007$); (ii) the morphology of \[O iii\]$5007$ at $\Delta v=0\,\mathrm{km\,s^{-1}}$ resembling AGN ionization cone (Fig. [1](#fig:O3_chanmap_0121)a); (iii) its ALMA 100$\,$GHz continuum being skewed spatially towards the west (cite: Falkendal_2019). Argument (iii) is also based on the spectral energy distribution (SED) study of (cite: Falkendal_2019) where the ALMA Band 3 continuum was used to constrain the radio sychrotron emission and the cold dust continuum (see their Fig. A.7). Based on their analysis, the 100$\,$GHz Band 3 continuum may be contributed by both. If it indeed contains synchrotron emission, then the closer west 8.4$\,$GHz radio excess is likely to be the radio core of the radio AGN. Taking our new Band 8 continuum into consideration, the 100$\,$GHz continuum seems likely to trace more diffuse and colder dust. Even in this case, the host galaxy is more likely located towards the west where the dust is.

### Results of companion search

(cite: DeBreuck_2002) reported a $18-19\,$mag detection of in $K_{s}$ using Keck/NIRC, which may indicate the presence of nearby companions based on morphology (seeing $0.4\ensuremath{''}-0.5\ensuremath{''}$). We caution that the $K_{s}$ observation was likely contaminated by bright \[O iii\]4959,5007 emission [^2]. Based on a seeing-limited SINFONI $K-$band observation ($0.65\ensuremath{''}\times0.55\ensuremath{''}$), (cite: Nesvadba_2007a) reported two \[O iii\]4959,5007 spatial components in the field of separated by $\sim10\,$kpc (component A and B under their naming). They also detected $K=19.8\pm$0.4$\,$mag continuum emission at the emission peak of \[O iii\]4959,5007 after excluding the line contamination (their component A). (cite: Nesvadba_2007a) suggested that component A may be the host galaxy of the radio AGN. We note that the continuum of radio AGN host galaxy may be contaminated by the foreground galaxy $\sim0.45\ensuremath{''}$ from the radio core (blue dot in Fig. [1](#fig:O3_chanmap_0121)a[1](#fig:O3_chanmap_0121)b, see also Appendix [10.1](#app:tnj0121_fore)). Though it may also be affected by leakage from MSA, we find that the continuum detected near the radio core in our NIRSpec IFU data is indeed spatially skewed towards the position of the foreground galaxy.

We next focus on the new evidence of nearby companions in our latest datasets with sub-kiloparsec resolution that reveal that there may be three systems across the $\sim25\,$kpc FoV. To the west of the radio core of , we detect a $\sim$$6\,$kpc extended bright \[O iii\] line-emitting nebula, J0121-\[O iii\], (blue triangle in Fig. [1](#fig:O3_chanmap_0121)a[1](#fig:O3_chanmap_0121)b). As shown in the spectrum in Fig. [1](#fig:O3_chanmap_0121)c, the dominant emission component of J0121-\[O iii\] is $434\,\rm km\,s^{-1}$ redshifted from the systemic velocity and has a width $\sigma_{v}=95\pm3\,\rm km\,s^{-1}$ (Table [1](#tab:1d_o3_spec_fit)). This is consistent with the results of (cite: Nesvadba_2007a) (i.e., their component B). J0121-\[O iii\] is at a projected distance of $\sim12.6\,$kpc from the radio AGN, $d_{\rm RG}$, measured from the peak \[O iii\] emission. Its narrower line width reveals its AGN-undisturbed nature. This suggests it is a distinct system from the gaseous medium surrounding the radio AGN and is likely a nearby companion. We map the kinematics of J0121-\[O iii\] in Fig. [1](#fig:O3_chanmap_0121)d across $\sim25\,\rm kpc^{2}$, a clear velocity gradient along the north-south direction with $\Delta v\sim400\,\rm km\,s^{-1}$. Visually, the $\Delta v$ map does not resemble disk rotation in that. There is no clearly defined positive-negative velocity transition edge. $^{\rm 3D}$BAROLO (cite: DiTeodoro_2015) fitting of this \[O iii\] emission nebula also does not indicate a clear rotation structure.

In addition to the \[O iii\] companion, we detect three \[C ii\] companions in this field (Fig. [2](#fig:j0121_c2_map_sp)). J0121-\[C ii\]-A is at $d_{\rm RG}=17.2\,$kpc away from the radio core with a $\Delta v=-401\,\rm km\,s^{-1}$. Cold dust continuum is also detected at this position. We do not have information about warm ionized gas at this position since J0121-\[C ii\]-A is outside the NIRSpec IFU FoV. J0121-\[C ii\]-C is at $d_{\rm RG}=11.1\,$kpc and falls within the ionized nebula of J0121-\[O iii\]. J0121-\[C ii\]-C (Fig. [2](#fig:j0121_c2_map_sp), Table [\[tab:1d_c2_spec_fit\]](#tab:1d_c2_spec_fit)) has $\Delta v=366\,\rm km\,s^{-1}$ and a similar profile to the \[O iii\]5007 line at the same position. Therefore, J0121-\[C ii\]-C and J0121-\[O iii\] may trace the same companion system. J0121-\[C ii\]-B has the brightest \[C ii\] emission and is at $d_{\rm RG}=6.4\,$kpc. Compared to the \[O iii\]5007 at the same position, J0121-\[C ii\]-B may have different dynamics.

To further study the cold ionized gas dynamics of J0121-\[C ii\]-B, we performed spatial \[C ii\] fitting using $^{\rm 3D}$BAROLO (cite: DiTeodoro_2015). The result is shown in Fig. [4](#fig:barolo_m1_0121) where we find a velocity gradient of $\sim 400\,\rm km\,s^{-1}$ along the north-south direction (i.e., PA$=187^{\circ}$ for the kinematic major axis). The residual from $^{\rm 3D}$BAROLO and the position-velocity diagram (especially moment 2 residual in Fig. [17](#fig:barolo_m02_j0121) and [19](#fig:barolo_pv_0121)) indicate gas motions other than disk rotation.

Both FIR and optical continuum are detected at J0121-\[C ii\]-B (Fig. [1](#fig:O3_chanmap_0121) and [3](#fig:sp_0121_continuum_opt)). We show the aperture-extracted optical spectrum at J0121-\[C ii\]-B. A stellar continuum fit is beyond the scope of this work. Instead, we overlay a model spectrum generated using Bagpipe (cite: Carnall_2018_Bagpipe). We used a single starburst model with solar metallicity. The extinction is set to $A_{V}=1.5\,$mag based on Balmer decrement and (cite: Calzetti_2000) law. We find that this continuum level could be consistent with a galaxy with $M_{\star}=10^{9.9}\,M_{\odot}$. This model spectrum should simply be considered as a zeroth order indication of the stellar mass.

## Companion search of TN J0205+2242

We detect a \[O iii\] line-emitting blob, J0205-\[O iii\], $d_{\rm RG}\sim3.22\,$kpc south of the radio AGN (Fig. [5](#fig:O3_chanmap_0205)a[5](#fig:O3_chanmap_0205)b). This kinematic feature was missed in previous SINFONI observations due to its limited spatial resolution and sensitivity (cite: Nesvadba_2007a). J0205-\[O iii\] has $\Delta v=-1426\,\rm km\,s^{-1}$ with respect to the systemic redshift of . It has a morphology with $\sim3\,$kpc extent which is barely resolved by the NIRSpec IFU. Compared to the spectrum of the central AGN, J0205-\[O iii\] is a distinct emission component (cyan Gaussian, Fig. [5](#fig:O3_chanmap_0205)c). The fitted line width is relatively broad with $\sigma_{v}=309\,\rm km\,s^{-1}$ which could be affected by beam smearing. That is to say that the physical scale of J0205-\[O iii\] cloud is small compared to the resolution of NIRSpec IFU, $\sim0.1-0.2\ensuremath{''}$ (cite: Vayner_2023Q3D; Vayner_2023Q3D_2; Vayner_2025). As a result, the unresolved gas motion (e.g., velocity gradient due to rotation) artificially broadens the observed line width. J0205-\[O iii\] has a tentative spatial velocity gradient along the northeast to southwest direction with $\sim300\,\rm km\,s^{-1}$ (Fig. [5](#fig:O3_chanmap_0205)d[5](#fig:O3_chanmap_0205)e). Another possibility is that this broad line width is due to the impact from the central AGN.

We detect tentative \[C ii\] emission, J0205-\[C ii\], $d_{\rm RG}=5.0\,$kpc north of the radio core at $3\sigma$ (Fig. [6](#fig:j0205_c2_map_sp)). The 1D spectrum shows a narrow line with $\sigma_{v}=54\,\rm km\,s^{-1}$ (Table [\[tab:1d_c2_spec_fit\]](#tab:1d_c2_spec_fit)). Given low S/N, we take this as a marginal detection though there is a \[O iii\] counterpart which may strengthens confidence in its existence (see the \[O iii\] line profile in Fig. [6](#fig:j0205_c2_map_sp)b). The nature of this system would be more tentative if only one dataset were available. This showcases the advantage of joint ALMA-*JWST* observation for discovering companion systems.

## Companions of 4C+03.24

In this work, we use the new VLA 15$\,$GHz observation of to trace the jet morphology (Sect. [2.5](#subsec:radio_ima)). In this rest-frame 70$\,$GHz data, we resolve the central structures of jet where three spatial peaks are discovered (cite: vanOjik_1996). We note that a detailed radio analysis of is beyond the scope of this work and will be presented in Kukreti et al. (in prep.). We determine that the center one of these three peaks is the core, radio AGN, based on spectral slope (magenta star in Fig. [7](#fig:O3_chanmap_4c03)). The coordinate of the radio core is given in Table [\[tab:sampleobs\]](#tab:sampleobs) which is used for WCS alignment (Sect. [2.4](#subsec:WCS_align)).

shows a complex warm ionized gas kinematics in the vicinity of its radio core. We focus on the most peculiar blob just to the north at $d_{\rm RG}=1.6\,$kpc but with a significant velocity shift, $\Delta v\simeq1300\,\rm km\,s^{-1}$ (precisely, $\Delta v=1395\pm47\,\rm km\,s^{-1}$ using fitting results from Table [1](#tab:1d_o3_spec_fit)). This emission nebula, 4C03-\[O iii\], is barely resolved (Fig. [7](#fig:O3_chanmap_4c03)b). With `q3dfit`, we spectrally decompose it to a narrow and a broad component with $\sigma_{v}=55\pm16\,\rm km\,s^{-1}$ and $574\pm5\,\rm km\,s^{-1}$, respectively (Fig. [7](#fig:O3_chanmap_4c03)c lower panel and Table [1](#tab:1d_o3_spec_fit)). Due to low S/N, the spatial velocity fitting of the 4C03-\[O iii\] narrow component is noisy, as shown in Fig. [7](#fig:O3_chanmap_4c03)d, but may show a tentative velocity gradient. The broad component of 4C03-\[O iii\] shows a gradient along the southeast-northwest direction with $\Delta v\sim500\,\rm km\,s^{-1}$. Both the kinematics and morphology of the 4C03-\[O iii\] broad component are distinct from the bulk motion of ionized gas detected by SINFONI (cite: Nesvadba_2017b), indicating a different nature from the jet-driven outflow. Taking both the narrow and broad components into account, we may be witnessing a companion AGN in the vicinity of the central radio quasar. Indeed, the 15$\,$GHz radio map shows a emission peak coincide with 4C03-\[O iii\] northward of the radio core. This may further indicate that the presence of two radio AGN. Alternatively, this may suggest a strong jet gas interaction. 4C03-\[O iii\] might be related to the previously published \[C i\] emission of .

We discovered three \[C ii\] emitters despite the shallow ALMA observation. 4C03-\[C ii\]-A is detected at $4\sigma$ and is located close to the radio core, $d_{\rm RG}=1.4\,$kpc. Since it is at the systemic redshift, 4C03-\[C ii\]-A likely traces gas in the AGN host ($\Delta v=9\pm17\,\rm km\,s^{-1}$, Fig. [8](#fig:4c03_c2_map_sp)a[8](#fig:4c03_c2_map_sp)b). Base on the current dataset, we cannot exclude the possibility that 4C03-\[C ii\]-A being a companion cloud system at projected distance near the core. 4C03-\[C ii\]-B is at $d_{\rm RG}=15.8\,$kpc southeast of the radio core with $\Delta v=-99\,\rm km\,s^{-1}$. The \[O iii\] profile at the same position has an emission component consistent with the \[C ii\] emission. 4C03-\[C ii\]-B is diffuse, as indicated by the clumpy contours shown in Fig. [8](#fig:4c03_c2_map_sp)a. 4C03-\[C ii\]-C has an elongated morphology extended by $\sim10\,$kpc located to the southeast of the radio core and with $\Delta v=342\,\rm km\,s^{-1}$. The \[O iii\] profile at the same position does not show a clear similarity. This may be a disturbed gas system in the vicinity of the radio AGN. We note that the rough positions of 4C03-\[C ii\]-B and \[C ii\]-C are given as the centroid positions of the $5\sigma$ contour (Table [\[tab:summa_comp\]](#tab:summa_comp)).

We show the optical continuum from NIRSpec IFU in Fig. [8](#fig:4c03_c2_map_sp)a as dashed green contours. This continuum map is constructed by collapsing the cube in wavelength directions with strong emission lines masked. We further masked artifacts at detector edges, the foreground galaxy to the west, and identified MSA leakage contamination.

The optical continuum has a complex morphology which resembles a merger tidal tail. A similar morphology is also seen in UV continuum by MUSE (Fig. [22](#fig:foreg_4c03) and also *HST*). Taking 4C03-\[C ii\]-B and -\[C ii\]-C into account, it is more likely that we are witnessing stars and gas stripped through merger processes at the center of . 4C03-\[O iii\] may also be in the same system. It has been known for decades that the southern radio jet of is bent (cite: vanOjik_1996). The hypothesis is that a dense system may exist in the south deflecting the jet. With our new ALMA+*JWST* data, we now confirm tidal structures to the south responsible for this deflection. A future paper will examine the jet-cloud interaction in further detail. The morphology of the extended continuum is similar to the \[O iii\]5007 (Fig.[7](#fig:O3_chanmap_4c03))a. This cautions that the continuum emission might be scattered AGN light rather than stellar emission.

## Companion search of 4C+19.71

(cite: Wang_2024) reported the detection of multiple emission components to the south of the radio core of , providing evidence for companions (see their Fig. 1c2). We confirm this detection at $d_{\rm RG}=6.2\,$kpc south of the core, 4C19-\[O iii\] (Fig. [9](#fig:O3_chanmap_4c19)b). As seen in the aperture-extracted spectrum in Fig. [9](#fig:O3_chanmap_4c19)c, there are three line emission components. The most blueshifted component, shown as the teal Gaussian, has a spatial extent of only $\sim 3\,$kpc and is likely the companion. (cite: Wang_2024) suggested that the most redshifted component at the position of 4C19-\[O iii\] as the receding emission from a rotating disk, with the most blueshifted one as the approaching side. After a spatial examination, we find that the two Gaussians redward of the teal Gaussian in Fig. [9](#fig:O3_chanmap_4c19)c are spatially more diffuse and are likely to be ionized ISM associated with the radio AGN. Hence, we infer that only the most blueshifted teal Gaussian is from a potential companion, with $\Delta v=-584\,\rm km\,s^{-1}$ and $\sigma_{v}=210\,\rm km\,s^{-1}$. In Fig. [9](#fig:O3_chanmap_4c19)d, we map the velocity shift 4C19-\[O iii\]. We do not detect a clear gradient, though $\Delta v$ in the northern part of the blob shows evidence of being redshifted with respect to the southern part by $\sim100\,\rm km\,s^{-1}$ (Fig. [9](#fig:O3_chanmap_4c19)e).

There is one bright \[C ii\] emitter detected, 4C19-\[C ii\] (Fig. [10](#fig:4c19_c2_map_sp)). FIR continuum peaking at the same position is also detected (Fig. [9](#fig:O3_chanmap_4c19)a[9](#fig:O3_chanmap_4c19)b). 4C19-\[C ii\] is at a small projected distance from the radio core, $d_{\rm RG}=0.3\,$kpc ($0.04\ensuremath{''}$). We find that the \[C ii\] and \[O iii\] line profiles are different, as shown in Fig. [10](#fig:4c19_c2_map_sp)b (offset $\sim 300\,\rm km\,s^{-1}$). Based on fitting of the 1D spectrum, \[C ii\] is at $\Delta v=-71\,\rm km\,s^{-1}$. This is more consistent with the redshift of the molecular gas (\[C i\]) than the warm ionized gas and suggests that the cold and warm gas are associated with two different systems (cite: Falkendal_2021; kolwa2023). The absolute astrometric accuracy of ALMA can be estimated as $\mathrm{pos_{acc}} = \mathrm{beam_{FWHP}}/(\mathrm{S/N})/0.9$ where $\mathrm{beam_{FWHP}}$ is the Full Width Half Maximum synthesized beam size in arcseconds. With $\theta_{\rm 400GHz}=0.23\ensuremath{''} \times 0.18\ensuremath{''}$ and S/N$=13.3$, the positional accuracy is $\sim0.019\ensuremath{''}\simeq d_{\rm RG,4C19-[C ii]}/2$. Assuming the errors are Gaussian distribution, the project distance is at $2\sigma$ away from the zero (i.e., the same position as the radio core) which implies that there is only a $5\%$ probability that the dust is at the same position as the AGN. The probability can be even lower if we take the uncertainty of the radio position into consideration ($\sim \theta_{\rm radio}/10$). In addition, there is no information on the line-of-sight separation. Hence, 4C19-\[C ii\] might be a gas-rich companion in front of or behind the massive radio galaxy (cite: Lin_2024). We also model the \[C ii\] emission with $^{\rm 3D}$BAROLO and find evidence of disk rotation (kinematic major axis along east-west with PA=$91^{\circ}$, Fig. [11](#fig:barolo_m1_4c19) and Appendix [9](#app:barolo)). Based on the residuals, we cannot rule out the possibility that the \[C ii\] kinematics is disturbed by a jet-driven cocoon if they indeed belong to the same system (cite: Mukherjee_2016).

![](Figures/BPT_1D_companion.png)

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| Companion | 2nd detection | Continuum | RA, Dec (J2000) | $d_{\rm RG}$ | $M_{\rm dyn, dis}$ | $M_{\rm dyn, rot}$ |
|  |  | opt./FIR | (hh:mm:ss, dd:mm:ss) | arcsec/kpc | $10^{10}\,M_{\odot}$ | $10^{10}\,M_{\odot}$ |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) |
| J0121- |  |  |  |  |  |  |
|  |  | / | (01:21:42.608, +13:20:58.52) | 1.72/12.6 | \- | 3.1${\rm csc^{2}} i$ |
| \[C ii\]-A | \- | -/ | (01:21:42.579, +13:20:59.26) | 2.36/17.2 | 4.5 | \- |
| \[C ii\]-B |  | / | (01:21:42.667, +13:20:58.52) | 0.88/6.4 | 48 | 9.0 |
| \[C ii\]-C |  | / | (01:21:42.622, +13:20:58.34) | 1.52/11.1 | 3.3 | \- |
| J0205- |  |  |  |  |  |  |
|  |  | / | (02:05:10.689, +22:42:50.17) | 0.44/3.2 | 22 | 0.8${\rm csc^{2}} i$ |
| \[C ii\] | $\bigcirc$ | / | (02:05:10.674, +22:42:51.26) | 0.69/5.0 | 1.8 | \- |
| 4C03- |  |  |  |  |  |  |
| narrow |  | / | (12:45:38.367, +03:23:21.45) | 0.22/1.6 | 0.7 | 0.3${\rm csc^{2}} i$ |
| \[O iii\] broad |  | / | \- | \- | 77 | 1.3${\rm csc^{2}} i$ |
| \[C ii\]-A |  | / | (12:45:38.377, +03:23:20.96) | 0.20/1.4 | 4.3 | \- |
| \[C ii\]-B | $\bigcirc$ | / | (12:45:38.470, +03:23:19.48)$^{\rm{(\dag)}}$ | 2.17/15.8 | 6.1 | \- |
| \[C ii\]-C |  | / | (12:45:38.420, +03:23:21.00)$^{\rm{(\dag)}}$ | 0.65/4.7 | 17 | \- |
| 4C19- |  |  |  |  |  |  |
|  |  | / | (21:44:07.515, +19:29:13.73) | 0.85/6.17 | 10 | 0.2${\rm csc^{2}} i$ |
| \[C ii\] |  | / | (21:44:07.515, +19:29:14.59) | 0.04/0.3 | 32 | 7.0 |

Table notes: (1) Name of the companion. (2) Companion signature of the emission line other than the one used for detection. indicates the companion is detected by both methods. indicates there is no detection of the other line or there is no clear signature of companion from the other line. $\bigcirc$ indicates that there is a hint of a companion from the other line. (3) Detection of optical or FIR continuum. (4) Companion coordinate. (5) Projected distance between the radio core and the position of the companion. (6) Dynamical mass of the companion based on velocity dispersion. (7) Dynamical mass of the companion assuming disk rotation.

# Discussion

## Companion kinematics and masses

Companions play an important role in galaxy evolution. In particular, nearby companion systems as detected in this work may be mergers which are key for both mass growth and triggering AGN (cite: Springel_2005; Hopkins_2008). The mass of a companion system is a crucial parameter. With our new observations, we offer a first order mass estimate. For this calculation, we ignore gravitational interactions between the companion and the central AGN.

Most of the companions have large velocity dispersion, $\sigma_{v}$, which may indicate they are in dispersion dominated systems (cite: Forster-Schreiber_2020). Under this assumption, we estimate $M_{\rm dyn}$ following (cite: ubler_2023): $$\begin{equation}
\label{eq:m_dyndis}
    M_{\rm dyn, dis} = K(n)K(q)\frac{\sigma_{v}^{2}r_{e}}{G}
\end{equation}$$ where $G$ is the gravitational constant, $r_{e}$ is the effective radius, $K(n)=8.87-0.831n+0.0241n^{2}$ is a function of Sérsic index, $n$, and $K(q)=[0.87+0.38e^{-3.71(1-q)}]^{2}$ is a function of axis ratio, $q$. For unresolved systems, we use the PSF or major synthesized beam size (or 2$\theta$ for J0205-\[C ii\] and 4C03-\[C ii\]) as a proxy for $r_{e}$. We stress that this mass estimate should be treated as an upper limit, as the size is overestimated. For Sérsic index we use $n=1$ which gives an upper limit of $M_{\rm dyn}$. For simplicity, we take $q=1$. Equation [\[eq:m_dyndis\]](#eq:m_dyndis) implies $M_{\rm dyn, dis}$ for the companions discovered in this work are approximately $10^{10-11}\,M_{\odot}$ (Table [\[tab:summa_comp\]](#tab:summa_comp)).

Alternatively, we can calculate the dynamical mass of the companion under the assumption of disk rotation using $$\begin{equation}
    M_{\rm dyn, rot} = k\frac{r v_{\rm rot}(r)^{2}}{G}
\end{equation}$$ where $v_{\rm rot}(r)$ is the circular rotation velocity, and $k$, the virial coefficient, is a function of $n$ and $q$. We take $k=1.8$ (cite: deGraaff_2024). For J0121-\[C ii\]-B and 4C19-\[C ii\], we obtain $r$ and $v_{\rm rot}$ from $^{\rm 3D}$BAROLO where the disk inclination angle, $i$, has been taken into account. $M_{\rm dyn}$ can be directly calculated for these two (Sect. [4.1](#subsec:comp_0121) and [4.4](#subsec:comp_4c19)). For the other fainter \[C ii\] companions, we do not estimate a mass under the rotation scenario due to limited information. Warm ionized gas was also used to study regular dynamics (cite: Ubler_2019; deGraaff_2024). For the \[O iii\] companions, we found tentative velocity gradients from `q3dfit` (Sect. [4](#sec:results)). Assuming that these are rotating disks, we can perform the similar $M_{\rm dyn}$ estimation. Estimation of $v_{\rm rot}$ for these \[O iii\] companions is nontrivial given their marginally resolved spatial extents (except J0121-\[O iii\]). Another uncertainty comes from their unknown inclination, $i$. Without further information, we use $v_{\rm rot}=\frac{1}{2}\Delta v_{\rm proj}/{\rm sin}\,i$ as a proxy for the rotation velocity where $\Delta v_{\rm proj}$ is the projected velocity difference along the gradient and leaving ${\rm sin}\,i$ unconstrained (cite: Nesvadba_2011). Hence, the equation we use is $$\begin{equation}
    M_{\rm dyn, rot} = k\frac{\Delta v_{\rm proj}^{2}R}{4G}{\rm csc^{2}}\,i
\end{equation}$$ where ${\rm csc^{2}}\,i=1/{\rm sin^{2}}\,i$ is left unconstrained. For the unresolved systems, we take the size of the NIRSpec IFU PSF, $\sim0.11\ensuremath{''}$, as the disk size, $R$, which is a lower limit. This simple estimation implies $M_{\rm dyn, rot}$ is around $10^{9-10}\,M_{\odot}$ (Table [\[tab:summa_comp\]](#tab:summa_comp))

As shown in Sect. [4.1](#subsec:comp_0121) and Fig. [3](#fig:sp_0121_continuum_opt), we estimate $M_{\star}$ estimation of J0121-\[C ii\]-B to be $10^{9.9}\,M_{\odot}$. This is the only companion where a zeroth order estimation could be done based on the continuum detected by NIRSpec IFU. By integrating along the wavelength direction of the NIRSpec IFU cube excluding strong emission lines, we find that the continuum of J0121-\[C ii\]-B is detected at $\sim8\sigma$. This indicates that the $3\sigma$ $M_{\star}$ detection limit in the cube is $\sim10^{9.5}\,M_{\odot}$ if optical continuum flux is directly proportional to stellar mass. Since our four radio AGN systems are at similar redshifts and observed with similar exposure times, this limit should be applicable to all four fields, with the caveat that the dust extinction of J0121-\[C ii\]-B is high, implying the $M_{\star}$ detection upper limit may be lower if extinction is lower in the other fields. For J0121-\[C ii\]-B, its $M_{\rm dyn}$ is around $10^{11}\,M_{\odot}$ which gives a $M_{\star}/M_{\rm dyn}\sim0.1$. At high-$z$, we may find that galaxies with low $M_{\star}$ have high $M_{\rm gas}/M_{\rm dyn}$ (cite: Pillepich_2019; deGraaff_2024). Hence, the other companion systems may have low stellar mass ($\lesssim10^{9.5}\,M_{\odot}$) and/or may be extremely gas-rich (or pure gas cloud systems).

Despite the large uncertainties in mass estimates, we infer that the companions discovered here are a few percent to the central host galaxies of the radio AGN (cite: Seymour_2007; DeBreuck_2010; Falkendal_2019; Wang_2021). If they will go through mergers, these will be the minor mergers which are critical for the hierarchal growth of clusters (cite: Moster_2018). Despite previous environmental studies on cluster scales around larger sample of HzRGs which proves their proto-cluster natures (cite: Venemans_2007; Wylezalek_2013; Wylezalek_2014), there is no clear evidence that the four HzRGs studied here live in dense environments. Our observations bring new information on 5 to $20\,$kpc scales and suggest the existence of $M_{\rm dyn}\sim10^{10}\,M_{\odot}$ systems around these four radio galaxies. Given that the detection presented in this work is not complete, the number of companion systems could be higher. If these companions will merge with the central mass galaxies, we are observing the forming progenitors of $\gtrsim10^{12-13}\,M_{\odot}$ halos, traced by radio AGN beyond Cosmic Noon (cite: Behroozi_2010; Behroozi_2019). The detection rate of companions in our randomly selected sample is $100\%$. As a rough first order estimate, the major merger fraction in our four-source sample is $f_{\rm MM}\sim25\%$, since 4C03 may be a potential major merger.

The discussion above ignores the gravitational impact from the central AGN. At the physical scales probed in this paper, it is very likely that these companion systems are disturbed in the potential well. Supporting this, the residuals from $^{\rm 3D}$BAROLO fitting of J0121-\[C ii\]-B and 4C19-\[C ii\] indicate the existence of complex gas motions.

## Nature of \[O iii\] companions

Unlike \[C ii\] companions indicating cold gas systems, the nature of \[O iii\] companions is often elusive in the vicinity of luminous quasars with $L_{\rm bol}\gtrsim10^{47}\,\rm erg\,s^{-1}$ (cite: Falkendal_2019). \[O iii\] emission with complex features are discovered in bright $z\sim0.5$ type-2 AGN, which has been interpreted as debris from mergers (cite: Storchi-Bergmann_2018; Dallagnol_2021). Our detection criteria for \[O iii\] companions requires peculiar kinematics distinct from the bulk motion of the warm ionized gas (cite: Nesvadba_2017b). As a first order check of the ionizing mechanism, we investigate line ratio diagnostics based on our 1D spectral fitting (cite: Kewley_2001; Kewley_2006). We use both the \[O iii\]/H$\beta$-\[N ii\]/H$\alpha$ and \[O iii\]/H$\beta$-\[S ii\]/H$\alpha$ diagnostics. The line fluxes are corrected for extinction using Balmer decrement by adopting the canonical value of $F_{\rm H\alpha}/F_{\rm H\beta}=3.1$ assuming Case B recombination (cite: Veilleux_1987; Osterbrock_2006). The results are shown in Fig. [12](#fig:BPT_1D). Simply assuming the (cite: Kewley_2006) empirical classification, we conclude that all but one \[O iii\] companion are photonionized by an AGN. Within the uncertainties of the line fitting and classification, the narrow component of 4C03-\[O iii\] is also consistent with AGN photoionization. One immediate conclusion is that these emission components are indeed in the vicinity of powerful AGN, particularly J0205-\[O iii\] and 4C03-\[O iii\] with $|\Delta v|\sim1000\,\rm km\,s^{-1}$.

Except for J0121-\[O iii\] whose morphology, kinematics, and \[C ii\] detection make it a solid companion detection, we cannot rule out that the candidates are part of the outflows. Though they are all detected along the jet axis, the PA of tentative velocity gradients are not always clearly correlated with the jet axis which may support them being companions. The relatively large $|\Delta v|\sim1000\,\rm km\,s^{-1}$ between these companions and the radio AGN may be expected, which is consistent with the velocity range of companion motions in clusters (cite: Bahcall_1994). Hence, a possible scenario could be that there are more of these gaseous companion systems moving randomly in the potential well of the proto-cluster centered around the radio AGN.

In this scenario, the detected companions that happen to fall in the ionization cone are photoionized and therefore detected (cite: Drouart_2012). Another scenario could be that the \[O iii\] blobs originated from gas stripped from companions in a previous (or ongoing) interaction, and is now being illuminated by the AGN (e.g., 4C03-\[O iii\]).

We do not intend to be complete in companion detection in this paper but offer a possible explanation of these unresolved emission blobs with peculiar kinematics. We acknowledge that the \[O iii\] companions are clumps accelerated or illuminated by the AGN but may not in themselves be stellar systems (Sect. [3](#sec:analysis)).

## Impact on galaxy evolution

There is no clear agreement on how powerful AGN jets are triggered in the early universe. Merger processes provide one possibility (cite: Chiaberge_2015), though the confirmation of mergers and/or interactions is nontrivial without 3D information. In this work, we discover that the companions have a median $d_{\rm RG}\simeq7\,$kpc. Using a typical $\Delta v$ of $\sim100-500\,\rm km\,s^{-1}$ and assuming no projection, the zeroth order estimate of encounter time is around 10 to 100$\,$Myr (i.e., $d_{\rm RG}/\Delta v$). Assuming the companions are in the post-encounter phase, i.e., after the first pericenter passage, this time scale is consistent with the observed time after jet launch (cite: Nesvadba_2017b; Nesvadba_2017a). This supports the merger trigger scenario for jets.

Our detections show that there are gaseous clouds at $\lesssim18\,$kpc from these four HzRGs. With resolution limited observations, (cite: Falkendal_2019) and (cite: kolwa2023) reported that gas in radio AGN hosts should be relatively depleted. Taking this into account, our work may support the scenario that gas, if not completely depleted, is located in nearby systems rather than in the AGN hosts. This is consistent with literature studies of high-$z$ radio AGN, which show that gas-rich systems are present in the vicinity of massive host galaxies (cite: Emonts_2015; Lin_2024; Huang_2024). Our work may show evidence of how these mergers with high gas content evolve in the radiation field of AGN and contribute to the growth of mass of the system. (cite: Lehnert_2016) predicted that $z\sim2-4$ galaxies are gas-rich (i.e., with H i). These galaxies with $M_{\star}\sim10^{8-9}\,M_{\odot}$ are important for mass growth through minor merger processes. That is to say, gas-rich mergers like the ones discovered in this paper bring fuel to feed central SMBHs and lead to AGN ignition. Besides bringing gas within tens of kiloparsec scales, the disruption from these nearby companions plays an important role in dissipating angular moment and accelerating gas accretion.

Apart from triggering AGN activity, companions could alter jet development. is the only HzRG in our sample with a compact jet (at $0.3\ensuremath{''}$ resolution). All three of its companions are to the west of the radio source. Dust is also detected at the same location as the dense environment. Hence, we infer that interaction of the jet with the dense medium disturbs the jet propagation, making the jet flow more turbulent and the emission more diffuse, thus also reducing its surface brightness. Furthermore, the dense environment may even cause the jet of to fail in penetrating through the medium, resulting in its observed compact morphology despite being one of the most luminous radio sources (cite: DeBreuck_2010). The case of may be a prototypical example. It has gone through a merger phase during which gas (4C03-\[C ii\]-B and -\[C ii\]-C) and stars (continuum) were stripped. This merger process triggered the radio jet which is then deflected by debris to the south.

We consider how radio selection effects may cause companions to be identified in particular phases. (cite: Emonts_2023_CO) examined the correlation between radio axis and gas clouds or mergers and showed that the radio asymmetries (e.g., radio flux ratios) can be attributable to interactions with gas in the CGM. Our work on smaller scales similarly suggests that the gaseous systems deflect or disturb jets, resulting in asymmetry, for example, by brightening radio fluxes. This means that flux-limited radio surveys will preferentially detect radio galaxies that are interacting because this resistance causes the synchrotron emissivity to increase by driving shocks into the relativistic plasma (cite: Steffen_1997; villar-martin_1999; Best_1998; Gomez_2006; Anderson_2022_spradio; Jerrim_2024).

# Conclusion

We present the first analysis of the resolution-matched joint *JWST*/NIRSpec IFU and ALMA observations of a sample of four HzRGs at $z\approx3.5$. We focus on \[O iii\]5007 and \[C ii\] emitters detected by the two observatories (Sect. [3](#sec:analysis)) and report the ubiquitous discovery of companion systems within $\sim18\,$kpc of the powerful radio AGN using these two independent methods.

Specifically, we examine the 1D spectra at the positions of companions and quantify the gas kinematics ($\Delta v$ and $\sigma_{v}$). For \[O iii\] companions (Sect. [3.1](#subsec:O3_kine)), we map the gas kinematics with `q3dfit`. We discover velocity gradients showing different motions than the bulk of the ionized gas. For the two \[C ii\] companions detected at high S/N (J0121-\[C ii\]-B and 4C19-\[C ii\] with S/N$>$10), we perform $^{\rm 3D}$BAROLO fits and detect disk rotation with residuals suggesting more chaotic underlying motions (Sect. [3.2](#subsec:c2_detection)).

We discuss individual companions in Sect. [4](#sec:results). First order dynamical mass estimates derived from the gas kinematics imply a range of $10^{9-11}\,M_{\odot}$, suggesting a possible minor merger with the central radio AGN host galaxy (Sect. [5.1](#subsec:comp_mass)). We further discuss the nature of \[O iii\] companions in Sect. [5.2](#subsec:discu_agn) which indicate AGN photoionized gaseous clouds that happen to be within the ionization cone, though we cannot rule out the possibility that they are part of an AGN outflow. Finally, we discuss that the companions could trigger the launch of a jet by supplying gas and dissipating angular moment. These companions systems can also alter the jet development. This further suggests that these relatively minor companions play an important role in the evolution of massive systems.

The matched resolution *JWST* and ALMA data are very rich and more detailed continuum and emission line studies are in preparation to decipher these complex systems. This is critical to understand the AGN feedback, star formation quenching, and mass growth of massive systems in the early universe.

# Acknowledgements

We thank the anonymous referee for their valuable comments and suggestions, which have improved the quality of this manuscript.

This work uses the NASA’s Astrophysics Data System and a number of open source software other than the aforementioned ones such as Jupyter notebook (cite: kluyver2016jupyter); `matplotlib` (cite: Hunter_2007); `SciPy` (cite: virtanen2020scipy); `NumPy` (cite: harris2020numpy); `Astropy` (cite: Astropy_2018); `LMFIT` (cite: newville2016). We thank Hannah Übler for the discussion of ionized gas kinematics. We thank Yechi Zhang for the discussion of modeling optical stellar continuum.

This publication has received funding from the European Union’s Horizon 2020 research and innovation programme under grant agreement No 101004719 (ORP).

This work is based in part on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with program JWST-GO-01970. Support for program JWST-GO-01970 was provided by NASA through a grant from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127.

D.W. and W.W. acknowledge support through an Emmy Noether Grant of the German Research Foundation, a stipend by the Daimler and Benz Foundation and the MERAC foundation and a Verbundforschung grant by the German Space Agency.

W.W. also acknowledges the grant support from NASA through JWST-GO-3045 and JWST-GO-3950.

The work of D.S. was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA.

B. D. O. acknowledges the support from the Coordenação de Aperfeiçoamento de Pessoal de Nível Superior (CAPES-Brasil, 88887.985730/2024-00).

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00576.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

103 natexlab

(ref: Anderson_2022_spradio) Anderson, C. S., Carilli, C. L., Tozzi, P., et al. 2022, ApJ, 937, 45

(ref: Astropy_2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Bahcall_1994) Bahcall, N. A., Gramann, M., & Cen, R. 1994, ApJ, 436, 23

(ref: Behroozi_2019) Behroozi, P., Wechsler, R. H., Hearin, A. P., & Conroy, C. 2019, MNRAS, 488, 3143

(ref: Behroozi_2010) Behroozi, P. S., Conroy, C., & Wechsler, R. H. 2010, ApJ, 717, 379

(ref: Best_1998) Best, P. N., Carilli, C. L., Garrington, S. T., Longair, M. S., & Rottgering, H. J. A. 1998, MNRAS, 299, 357

(ref: Calzetti_2000) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: Carnall_2018_Bagpipe) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379

(ref: CASA_2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Chiaberge_2015) Chiaberge, M., Gilli, R., Lotz, J. M., & Norman, C. 2015, ApJ, 806, 147

(ref: Dallagnol_2021) Dall’Agnol de Oliveira, B., Storchi-Bergmann, T., Kraemer, S. B., et al. 2021, MNRAS, 504, 3890

(ref: Dalmasso_2024) Dalmasso, N., Calabrò, A., Leethochawalit, N., et al. 2024, arXiv e-prints, arXiv:2403.11428

(ref: DeBreuck_2010) De Breuck, C., Seymour, N., Stern, D., et al. 2010, ApJ, 725, 36

(ref: DeBreuck_2002) De Breuck, C., van Breugel, W., Stanford, S. A., et al. 2002, AJ, 123, 637

(ref: deGraaff_2024) de Graaff, A., Rix, H.-W., Carniani, S., et al. 2024, A&A, 684, A87

(ref: Dessauges-Zavadsky_2020) Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643, A5

(ref: DiTeodoro_2015) Di Teodoro, E. M. & Fraternali, F. 2015, MNRAS, 451, 3021

(ref: Drouart_2012) Drouart, G., De Breuck, C., Vernet, J., et al. 2012, A&A, 548, A45

(ref: Duncan_2023) Duncan, K. J., Windhorst, R. A., Koekemoer, A. M., et al. 2023, MNRAS, 522, 4548

(ref: Emonts_2015) Emonts, B. H. C., De Breuck, C., Lehnert, M. D., et al. 2015, A&A, 584, A99

(ref: Emonts_2023_CO) Emonts, B. H. C., Lehnert, M. D., Lebowitz, S., et al. 2023a, ApJ, 952, 148

(ref: Emonts_2023) Emonts, B. H. C., Lehnert, M. D., Yoon, I., et al. 2023b, Science, 379, 1323

(ref: Faisst_2020) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61

(ref: Falkendal_2019) Falkendal, T., De Breuck, C., Lehnert, M. D., et al. 2019, A&A, 621, A27

(ref: Falkendal_2021) Falkendal, T., Lehnert, M. D., Vernet, J., De Breuck, C., & Wang, W. 2021, A&A, 645, A120

(ref: Forster-Schreiber_2020) Förster Schreiber, N. M. & Wuyts, S. 2020, ARA&A, 58, 661

(ref: Galametz_2012) Galametz, A., Stern, D., De Breuck, C., et al. 2012, ApJ, 749, 169

(ref: Gomez_2006) Gómez, J. L., Marscher, A. P., Jorstad, S. G., & Agudo, I. 2006, Astronomische Nachrichten, 327, 223

(ref: Greisen_2003) Greisen, E. W. 2003, in Astrophysics and Space Science Library, Vol. 285, Information Handling in Astronomy - Historical Vistas, ed. A. Heck, 109

(ref: Gupta_2023) Gupta, A., Jaiswar, R., Rodriguez-Gomez, V., et al. 2023, ApJL, 957, L35

(ref: harris2020numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: Harrison_2014) Harrison, C. M., Alexander, D. M., Mullaney, J. R., & Swinbank, A. M. 2014, MNRAS, 441, 3306

(ref: Heckman_2014) Heckman, T. M. & Best, P. N. 2014, ARA&A, 52, 589

(ref: Herrera-Camus_2022) Herrera-Camus, R., Förster Schreiber, N. M., Price, S. H., et al. 2022, A&A, 665, L8

(ref: Holden_2024_MUSE) Holden, L. R. & Tadhunter, C. N. 2024, arXiv e-prints, arXiv:2411.17500

(ref: Hopkins_2008d) Hopkins, P. F., Cox, T. J., Kereš, D., & Hernquist, L. 2008a, ApJS, 175, 390

(ref: Hopkins_2008) Hopkins, P. F., Hernquist, L., Cox, T. J., & Kereš, D. 2008b, ApJS, 175, 356

(ref: Huang_2024) Huang, H.-T., Man, A. W. S., Lelli, F., et al. 2024, arXiv e-prints, arXiv:2411.04290

(ref: Hunter_2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90

(ref: Husko_2022) Huško, F., Lacey, C. G., & Baugh, C. M. 2022, MNRAS, 509, 5918

(ref: Ivison_2012) Ivison, R. J., Smail, I., Amblard, A., et al. 2012, MNRAS, 425, 1320

(ref: Jerrim_2024) Jerrim, L. A., Shabala, S. S., Yates-Jones, P. M., et al. 2024, MNRAS, 531, 2532

(ref: Jones_2024) Jones, G. C., Übler, H., Perna, M., et al. 2024, A&A, 682, A122

(ref: Kewley_2001) Kewley, L. J., Dopita, M. A., Sutherland, R. S., Heisler, C. A., & Trevena, J. 2001, ApJ, 556, 121

(ref: Kewley_2006) Kewley, L. J., Groves, B., Kauffmann, G., & Heckman, T. 2006, MNRAS, 372, 961

(ref: kluyver2016jupyter) Kluyver, T., Ragan-Kelley, B., Pérez, F., et al. 2016, in Positioning and Power in Academic Publishing: Players, Agents and Agendas, ed. F. Loizides & B. Schmidt, IOS Press, 87 – 90

(ref: kolwa2023) Kolwa, S., De Breuck, C., Vernet, J., et al. 2023, MNRAS, 525, 5831

(ref: Lagache_2018) Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130

(ref: Lebowitz_2023) Lebowitz, S., Emonts, B., Terndrup, D. M., et al. 2023, ApJ, 951, 73

(ref: Lehnert_2016) Lehnert, M. D., van Driel, W., & Minchin, R. 2016, A&A, 590, A51

(ref: Lelli_2021) Lelli, F., Di Teodoro, E. M., Fraternali, F., et al. 2021, Science, 371, 713

(ref: Lin_2024) Lin, L., Lelli, F., De Breuck, C., et al. 2024, arXiv e-prints, arXiv:2411.08958

(ref: MandD_2014) Madau, P. & Dickinson, M. 2014, ARA&A, 52, 415

(ref: Miley_2008) Miley, G. & De Breuck, C. 2008, A&ARv, 15, 67

(ref: Moster_2018) Moster, B. P., Naab, T., & White, S. D. M. 2018, MNRAS, 477, 1822

(ref: Mukherjee_2016) Mukherjee, D., Bicknell, G. V., Sutherland, R., & Wagner, A. 2016, MNRAS, 461, 967

(ref: Nesvadba_2011) Nesvadba, N. P. H., Boulanger, F., Lehnert, M. D., Guillard, P., & Salome, P. 2011, A&A, 536, L5

(ref: Nesvadba_2017b) Nesvadba, N. P. H., De Breuck, C., Lehnert, M. D., Best, P. N., & Collet, C. 2017a, A&A, 599, A123

(ref: Nesvadba_2017a) Nesvadba, N. P. H., Drouart, G., De Breuck, C., et al. 2017b, A&A, 600, A121

(ref: Nesvadba_2007a) Nesvadba, N. P. H., Lehnert, M. D., De Breuck, C., Gilbert, A., & van Breugel, W. 2007, A&A, 475, 145

(ref: newville2016) Newville, M., Stensitzki, T., Allen, D. B., et al. 2016, Lmfit: Non-Linear Least-Square Minimization and Curve-Fitting for Python

(ref: Noirot_2018) Noirot, G., Stern, D., Mei, S., et al. 2018, ApJ, 859, 38

(ref: Noirot_2016) Noirot, G., Vernet, J., De Breuck, C., et al. 2016, ApJ, 830, 90

(ref: Ondaro-Mallea_2024) Ondaro-Mallea, L., Angulo, R. E., Aricò, G., et al. 2024, arXiv e-prints, arXiv:2412.09526

(ref: Osterbrock_2006) Osterbrock, D. E. & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and active galactic nuclei

(ref: Pentericci_1999) Pentericci, L., Röttgering, H. J. A., Miley, G. K., et al. 1999, A&A, 341, 329

(ref: Perez-Martinez_2024) Pérez-Martı́nez, J. M., Dannerbauer, H., Koyama, Y., et al. 2024, arXiv e-prints, arXiv:2410.03366

(ref: Perley_2017) Perley, R. A. & Butler, B. J. 2017, ApJS, 230, 7

(ref: Perna_2023) Perna, M., Arribas, S., Marshall, M., et al. 2023, A&A, 679, A89

(ref: Pierce_2023) Pierce, J. C. S., Tadhunter, C., Ramos Almeida, C., et al. 2023, MNRAS, 522, 1736

(ref: Pillepich_2019) Pillepich, A., Nelson, D., Springel, V., et al. 2019, MNRAS, 490, 3196

(ref: Rocca-Volmerange_2013) Rocca-Volmerange, B., Drouart, G., De Breuck, C., et al. 2013, MNRAS, 429, 2780

(ref: Romano_2021) Romano, M., Cassata, P., Morselli, L., et al. 2021, A&A, 653, A111

(ref: Roy_2024) Roy, N., Heckman, T., Overzier, R., et al. 2024, ApJ, 970, 69

(ref: Rupke_2023q3dfit) Rupke, D., Wylezalek, D., Zakamska, N., et al. 2023, q3dfit: PSF decomposition and spectral analysis for JWST-IFU spectroscopy, Astrophysics Source Code Library, record ascl:2310.004

(ref: Sanders_2016) Sanders, R. L., Shapley, A. E., Kriek, M., et al. 2016, ApJ, 816, 23

(ref: Saxena_2024) Saxena, A., Overzier, R. A., Villar-Martı́n, M., et al. 2024, MNRAS, 531, 4391

(ref: Seymour_2007) Seymour, N., Stern, D., De Breuck, C., et al. 2007, ApJS, 171, 353

(ref: Shimakawa_2024) Shimakawa, R., Perez-Martinez, J. M., Dannerbauer, H., et al. 2024, arXiv e-prints, arXiv:2410.03362

(ref: Springel_2005) Springel, V., White, S. D. M., Jenkins, A., et al. 2005, Nature, 435, 629

(ref: Steffen_1997) Steffen, W., Gómez, J. L., Raga, A. C., & Williams, R. J. R. 1997, ApJL, 491, L73

(ref: Storchi-Bergmann_2018) Storchi-Bergmann, T., Dall’Agnol de Oliveira, B., Longo Micchi, L. F., et al. 2018, ApJ, 868, 14

(ref: Suzuki_2022) Suzuki, T. L., Glazebrook, K., Schreiber, C., et al. 2022, ApJ, 936, 61

(ref: Ubler_2019) Übler, H., Genzel, R., Wisnioski, E., et al. 2019, ApJ, 880, 48

(ref: ubler_2023) Übler, H., Maiolino, R., Curtis-Lake, E., et al. 2023, arXiv e-prints, arXiv:2302.06647

(ref: vanOjik_1996) van Ojik, R., Roettgering, H. J. A., Carilli, C. L., et al. 1996, A&A, 313, 25

(ref: Vayner_2025) Vayner, A., Dı́az-Santos, T., Eisenhardt, P. R. M., et al. 2024, arXiv e-prints, arXiv:2412.02862

(ref: Vayner_2023Q3D) Vayner, A., Zakamska, N. L., Ishikawa, Y., et al. 2023a, ApJ, 955, 92

(ref: Vayner_2023Q3D_2) Vayner, A., Zakamska, N. L., Ishikawa, Y., et al. 2023b, arXiv e-prints, arXiv:2307.13751

(ref: Veilleux_1987) Veilleux, S. & Osterbrock, D. E. 1987, ApJS, 63, 295

(ref: Venemans_2007) Venemans, B. P., Röttgering, H. J. A., Miley, G. K., et al. 2007, A&A, 461, 823

(ref: vernet_2001) Vernet, J., Fosbury, R. A. E., Villar-Martı́n, M., et al. 2001, A&A, 366, 7

(ref: Vernet2017) Vernet, J., Lehnert, M. D., De Breuck, C., et al. 2017, A&A, 602, L6

(ref: villar-martin_1999) Villar-Martı́n, M., Tadhunter, C., Morganti, R., Axon, D., & Koekemoer, A. 1999, MNRAS, 307, 24

(ref: virtanen2020scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: Wang_2021) Wang, W., Wylezalek, D., De Breuck, C., et al. 2021, A&A, 654, A88

(ref: Wang_2024) Wang, W., Wylezalek, D., De Breuck, C., et al. 2024, A&A, 683, A169

(ref: wang2023) Wang, W., Wylezalek, D., Vernet, J., et al. 2023, A&A, 680, A70

(ref: Wylezalek_2013) Wylezalek, D., Galametz, A., Stern, D., et al. 2013, ApJ, 769, 79

(ref: Wylezalek_2022q3d) Wylezalek, D., Vayner, A., Rupke, D. S. N., et al. 2022, ApJL, 940, L7

(ref: Wylezalek_2014) Wylezalek, D., Vernet, J., De Breuck, C., et al. 2014, ApJ, 786, 17

(ref: Zakamska_2003) Zakamska, N. L., Strauss, M. A., Krolik, J. H., et al. 2003, AJ, 126, 2125

(ref: ZhongYuxing_2024) Zhong, Y., Inoue, A. K., Sugahara, Y., et al. 2024, MNRAS, 529, 4531

# \[O iii\]5007 channel maps

We present the \[O iii\]5007 channel maps in this section. The channel maps are constructed from continuum subtracted NIRSpec IFU data cubes. Each map is collapsed from three consecutive channels. The maps shown in Fig. [13](#fig:o3_stamps_0121), [14](#fig:o3_stamps_0205), [15](#fig:o3_stamps_4C03), and [16](#fig:o3_stamps_4C19) are for , , , and , respectively.

![](Figures/O3_stamps/TNJ0121+1320_OIII_chanmap_stamps.png)

![](Figures/O3_stamps/TNJ0205+2242_OIII_chanmap_stamps.png)

![](Figures/O3_stamps/4C+03.24_OIII_chanmap_stamps.png)

![](Figures/O3_stamps/4C+19.71_OIII_chanmap_stamps.png)

# 1D emission line fitting results

The fitted parameters of the 1D spectra are given in this section. For the warm ionized gas spectra extracted from the NIRSpec IFU, we present the redshifts and line widths for each Gaussian component in Table [1](#tab:1d_o3_spec_fit). The fitted results of 1D \[C ii\] spectra are presented in Table [\[tab:1d_c2_spec_fit\]](#tab:1d_c2_spec_fit).

+:-----------------:+:-----------------:+:----------------:+:----------------:+
| component         | redshift          | $\Delta v$       | $\sigma_{v}$     |
+-------------------+-------------------+------------------+------------------+
|                   | $z$               | $\rm km\,s^{-1}$ | $\rm km\,s^{-1}$ |
+-------------------+-------------------+------------------+------------------+
| TN J0121-radio core                                                         |
+-------------------+-------------------+------------------+------------------+
| 0                 | 3.5191$\pm$0.0003 | 9$\pm$17         | 191$\pm$11       |
+-------------------+-------------------+------------------+------------------+
| 1                 | 3.5243$\pm$0.0002 | 352$\pm$10       | 132$\pm$7        |
+-------------------+-------------------+------------------+------------------+
| 2                 | 3.5246$\pm$0.0002 | 373$\pm$12       | 628$\pm$10       |
+-------------------+-------------------+------------------+------------------+
| J0121-\[O iii\]                                                             |
+-------------------+-------------------+------------------+------------------+
| 0                 | 3.5236$\pm$0.0003 | 305$\pm$20       | 248$\pm$13       |
+-------------------+-------------------+------------------+------------------+
| 1$^{\rm{(\dag)}}$ | 3.5255$\pm$0.0001 | 434$\pm$2        | 95$\pm$3         |
+-------------------+-------------------+------------------+------------------+
| TN J0205-radio core                                                         |
+-------------------+-------------------+------------------+------------------+
| 0                 | 3.5015$\pm$0.0001 | -302$\pm$4       | 158$\pm$5        |
+-------------------+-------------------+------------------+------------------+
| 1                 | 3.5059$\pm$0.0001 | -4$\pm$7         | 508$\pm$9        |
+-------------------+-------------------+------------------+------------------+
| 2                 | 3.5091$\pm$0.0001 | 204$\pm$2        | 106$\pm$2        |
+-------------------+-------------------+------------------+------------------+
| J0205-\[O iii\]                                                             |
+-------------------+-------------------+------------------+------------------+
| 0$^{\rm{(\dag)}}$ | 3.4846$\pm$0.0001 | -1426$\pm$8      | 309$\pm$7        |
+-------------------+-------------------+------------------+------------------+
| 1                 | 3.5066$\pm$0.0003 | 42$\pm$18        | 618$\pm$21       |
+-------------------+-------------------+------------------+------------------+
| 2                 | 3.5085$\pm$0.0001 | 167$\pm$4        | 174$\pm$6        |
+-------------------+-------------------+------------------+------------------+
| 4C03-radio core                                                             |
+-------------------+-------------------+------------------+------------------+
| 0                 | 3.5533$\pm$0.0002 | -817$\pm$16      | 1092$\pm$12      |
+-------------------+-------------------+------------------+------------------+
| 1                 | 3.5639$\pm$0.0007 | -115$\pm$46      | 294$\pm$21       |
+-------------------+-------------------+------------------+------------------+
| 2                 | 3.5691$\pm$0.0002 | 222$\pm$15       | 204$\pm$14       |
+-------------------+-------------------+------------------+------------------+
| 4C03-\[O iii\]                                                              |
+-------------------+-------------------+------------------+------------------+
| 0                 | 3.5748$\pm$0.0001 | 595$\pm$4        | 158$\pm$6        |
+-------------------+-------------------+------------------+------------------+
| 1$^{\rm{(\dag)}}$ | 3.5852$\pm$0.0002 | 1280$\pm$11      | 55$\pm$16        |
+-------------------+-------------------+------------------+------------------+
| 2$^{\rm{(\dag)}}$ | 3.5872$\pm$0.0001 | 1410$\pm$9       | 574$\pm$5        |
+-------------------+-------------------+------------------+------------------+
| 4C19-radio core                                                             |
+-------------------+-------------------+------------------+------------------+
| 0                 | 3.5822$\pm$0.0021 | -455$\pm$134     | 712$\pm$54       |
+-------------------+-------------------+------------------+------------------+
| 1                 | 3.5933$\pm$0.0001 | 265$\pm$3        | 207$\pm$4        |
+-------------------+-------------------+------------------+------------------+
| 2                 | 3.5947$\pm$0.0012 | 361$\pm$75       | 444$\pm$49       |
+-------------------+-------------------+------------------+------------------+
| 4C19-\[O iii\]                                                              |
+-------------------+-------------------+------------------+------------------+
| 0$^{\rm{(\dag)}}$ | 3.5803$\pm$0.0001 | -584$\pm$9       | 210$\pm$9        |
+-------------------+-------------------+------------------+------------------+
| 1                 | 3.5874$\pm$0.0001 | -121$\pm$7       | 98$\pm$8         |
+-------------------+-------------------+------------------+------------------+
| 2                 | 3.5970$\pm$0.0001 | 512$\pm$3        | 213$\pm$3        |
+-------------------+-------------------+------------------+------------------+

: Ionized gas kinematics from the 1D spectra extracted at the positions of the radio core and \[O iii\] companions.

Table notes: Kinematic components of each sources are ordered based on their redshifts. $\Delta v$ is calculated with respect to the systemic redshift listed in Table [\[tab:sampleobs\]](#tab:sampleobs). The quoted uncertainties are $1\sigma$ errors from `q3dfit`.\

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Companion | redshift | $\Delta v$ | $\sigma_{v}$ | $F_{\nu \rm [C ii]}\Delta v$ |
|  | $z$ | $\rm km\,s^{-1}$ | $\rm km\,s^{-1}$ | $\rm Jy\, km\,s^{-1}$ |
| J0121-\[C ii\]-A | 3.5130$\pm$0.0003 | -401$\pm$17 | 105$\pm$17 | 0.49$\pm$0.07 |
| J0121-\[C ii\]-B | 3.5197$\pm$0.0003 | 49$\pm$19 | 345$\pm$19 | 2.49$\pm$0.12 |
| J0121-\[C ii\]-C | 3.5245$\pm$0.0003 | 366$\pm$18 | 90$\pm$18 | 0.33$\pm$0.06 |
| J0205-\[C ii\] | 3.5053$\pm$0.0003 | -44$\pm$19 | 54$\pm$19 | 1.11$\pm$0.34 |
| 4C03-\[C ii\]-A | 3.5658$\pm$0.0003 | 9$\pm$17 | 66$\pm$17 | 0.65$\pm$0.14 |
| 4C03-\[C ii\]-B | 3.5690$\pm$0.0003 | 219$\pm$18 | 73$\pm$18 | 0.68$\pm$0.14 |
| 4C03-\[C ii\]-C | 3.5709$\pm$0.0003 | 343$\pm$21 | 117$\pm$21 | 1.21$\pm$0.18 |
| 4C19-\[C ii\] | 3.5881$\pm$0.0002 | -71$\pm$12 | 256$\pm$12 | 1.62$\pm$0.06 |

Table notes: The reported uncertainty is the $1\sigma$ error from the fit.

# $^{\rm 3D}$BAROLO fit of \[C ii\]

We use $^{\rm 3D}$BAROLO to fit the two bright \[C ii\] companions, J0121-\[C ii\]-B and 4C19-\[C ii\]. In $^{\rm 3D}$BAROLO, a rotating galaxy disk is modeled with a set of tilted rings. Each ring is parametrized by five geometric parameters — center coordinates ($x_{0}$, $y_{0}$), systemic velocity ($v_{\rm sys}$), position angle ($PA$, measured anti-clockwise from the North), and inclination ($i$) — and five physical parameters — rotation velocity ($v_{\rm rot}$), radial velocity ($v_{\rm rad}$), velocity dispersion ($\sigma_{\rm v}$), surface density ($\Sigma_{\rm gas}$), and vertical thickness ($z_{0}$). The separation between rings is set to half the width of beam major axis by default. We note that there are no constraints on the initial guesses for $PA$ and $i$. The fit is performed using values obtained from a visual inspection.

We initially perform the fit on cubes at the original resolution of 14 km s$^{-1}$, which leads to poorer constraints on the parameters. To mitigate this, we apply spectral smoothing to the cubes, aiming to enhance the S/N at the expense of spectral resolution. For J0121-\[C ii\]-B, the \[C ii\] cube is smoothed to a velocity resolution of 28 km s$^{-1}$. The initial values of $PA$ and $i$ are set to 193$^{\circ}$ and 60$^{\circ}$. They are allowed to be varied by $\pm15^{\circ}$. The initial values of $\sigma_{\rm v}$ is by default 8 km s$^{-1}$. We set `NORM=AZIM` so that the observed moment-0 map is azimuthally averaged to obtain $\Sigma_{\rm gas}$ of each ring in the model. Initial value of other parameters are guessed by $^{\rm 3D}$BAROLO. The center coordinates ($x_{0}$, $y_{0}$) are fixed to the initial guess. Then, the free parameters to be minimized are $v_{\rm sys}$, $PA$, $i$, $v_{\rm rot}$, and $\sigma_{\rm v}$. For 4C19-\[C ii\], the \[C ii\] cube is also smoothed to a velocity resolution of 28 km s$^{-1}$. The initial values of $PA$ and $i$ are 100$^{\circ}$ and 10$^{\circ}$. They are allowed to be varied by $\pm15^{\circ}$ and $\pm30^{\circ}$, respectively. $^{\rm 3D}$BAROLO fit is performed in two steps. First, all free parameters are fitted. Then, the geometric parameters are fixed while only $v_{\rm rot}$ and $\sigma_{\rm v}$ were fitted.

We show the fitted maps moment 0 (intensity) and moment 2 (velocity dispersion) maps in Fig. [17](#fig:barolo_m02_j0121) and [18](#fig:barolo_m02_4c19) for the two companions. In addition, we also present the position velocity (PV) diagrams from $^{\rm 3D}$BAROLO along the kinematic major axis in Fig. [19](#fig:barolo_pv_0121) and [20](#fig:barolo_pv_4c19) for the two companions. We report that the best fits of J0121-\[C ii\]-B $PA$ and $i$ are 187$^{\circ}$ and 61$^{\circ}$, respectively. The best fits of 4C19-\[C ii\] $PA$ and $i$ are 93$^{\circ}$ and 30$^{\circ}$, respectively. We note that the $i$ fit of 4C19-\[C ii\] is limited by angular resolution and should be treated with caution.

![](Figures/CII_Barolo_fit/TN_J0121+1320_maps_azim_mom02_paper.pdf)

![](Figures/CII_Barolo_fit/4C19.71_maps_azim_mom02_paper.pdf)

![](Figures/CII_Barolo_fit/TN_J0121+1320_pv.pdf)

![](Figures/CII_Barolo_fit/4C19.71_pv.pdf)

# Foreground detection

## Foreground cluster in the field of TN J0121+1320

![](Figures/Foreground/TNJ0121_Foreground_spec_combine.pdf)

We detect a foreground galaxy at $z=1.4577$ in the field of using the NIRSpec IFU data. The continuum emission of this foreground galaxy may contaminate the continuum of given its small spatial offset, $\sim0.1\ensuremath{''}$ (0.85$\,$kpc), from the line emission peak. This galaxy likely belongs to a cluster. Its \[O ii\]$3726,3729$ doublet is covered by MUSE (FoV of $1\ensuremath{'} \times 1\ensuremath{'}$). We present the continuum-subtracted MUSE narrow band image integrated from $-200$ to $200\,\mathrm{km\,s^{-1}}$ around \[O ii\]$3729$ in Fig. [21](#fig:foreg_tnj0121). There are at least two additional \[O ii\]$3726,3729$ emitters at similar redshift within $10\ensuremath{''}$ ($\sim84.5\,$kpc) of the one covered in the NIRSpec IFU FoV. We mark the positions of these two \[O ii\]$3726,3729$ emitters and name them $\mathrm{G_{N}}$ and $\mathrm{G_{S}}$ for the one in the north and south, respectively. In addition to \[O ii\]$3726,3729$, we also detect \[S III\]$9533$, He I$10833$ and Pa$\beta$ at the same redshift and position as the foreground galaxy using NIRSpec IFU. These assure the redshift of this foreground galaxy. The spectra are shown in Fig. [21](#fig:foreg_tnj0121). The spatial position of the foreground cluster and its redshift may lead to magnification and/or distortion of the emission from TN J0121+1320 by gravitational lensing.

## 4C+03.24

We report a potential foreground galaxy in the field of . This galaxy is covered at the edge of the NIRSpec IFU FoV. We do not find any emission lines in the NIRSpec IFU data cube and note that analysis of SINFONI data assumed it to be a star (cite: Nesvadba_2017b). At the same position in MUSE data cube, we detect both an emission line and continuum (Fig. [22](#fig:foreg_4c03)). With only a single line detected, the redshift is uncertain. If we assume it to be redshifted \[O ii\]$3726,3729$, the redshift is $z\sim0.7384$. The projected distance between the radio core of and this potential foreground object is $0.58\ensuremath{''}$, implying the possibility of gravitational lensing.

![](Figures/Foreground/4C+03_foreground.pdf)

[^1]: <https://github.com/spacetelescope/jwst>

[^2]: <https://www2.keck.hawaii.edu/inst/nirc/manual/fw_macros.html>

</paper>

Write the methods card for this paper.