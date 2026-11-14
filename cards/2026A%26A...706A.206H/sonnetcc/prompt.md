# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026A%26A...706A.206H\sonnetcc\reply.txt

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
 "bibcode": "2026A&A...706A.206H",
 "title": "The Atacama Cosmology Telescope: Observations of supermassive black hole binary candidates: Strong sinusoidal variations at 95, 147, and 225 GHz in PKS 2131─021 and PKS J0805─0111",
 "year": 2026,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Hincks, Adam D.",
 "n_authors": 26,
 "arxiv_id": "2504.04278",
 "doi": "10.1051/0004-6361/202555047",
 "alma_projects_linked_by_archive": []
}
```

Paper text:
<paper>
# The Atacama Cosmology Telescope: Observations\
of supermassive black hole binary candidates

# Introduction

Evidence of a stochastic background of gravitational waves with periods of months to years has recently been presented by the North American Nanohertz Observatory for Gravitational Waves collaboration (cite: agazie/etal:2023a) and the European Pulsar Timing Array collaboration (cite: epta:2023); the MeerKAT Pulsar Timing Array collaboration also find evidence for the background, but caution that it is highly dependent on choices in their noise modelling (cite: miles/etal:2025). These experiments use millisecond pulsar timing arrays ((cite: 1974MmRAS..78....1R; 1982Natur.300..615B))[^1] which currently provide the most sensitive method of searching for gravitational waves at these frequencies, although stellar astrometry of billions of stars (cite: 2017PhRvL.119z1102M; 1990NCimB.105.1141B) may be competitive in the future. Supermassive black hole binary systems (SMBHBs) have been suggested as the origin of this stochastic background (cite: agazie/etal:2023a; agazie/etal:2023b), making clear the importance of searches for their electromagnetic counterparts.

Supermassive black holes (SMBHs) are the central engines in active galactic nuclei (AGN), which are strong sources of emission across the electromagnetic spectrum (cite: 2000AmJPh..68..489K; Blandford2019). Since 2008 the 40 m Telescope of the Owens Valley Radio Observatory (OVRO) has been dedicated full time to monitoring ${\sim}1830$ blazars at 15 GHz on a 3–4 day cadence (cite: Richards2011). Of the ${\sim}1830$ blazars monitored, 1158 comprise a complete sample suitable for statistical tests. To date, two AGN with sinusoidal variations dominating their light curves have been identified in this sample, which rigorous statistical tests show are unlikely to be produced by random fluctuations in the red noise tail of their power spectral density: PKS 2131$-$021((cite: 2022ApJ...926L..35O), hereafter referred to as O22; (cite: 2025ApJ...985...59K), hereafter K25) and PKS J0805$-$0111((cite: delaparra/etal:2025), hereafter D25). K25 and D25 simulated $10^6$ light curves that match the power spectral densities and probability density functions (i.e., the flux distribution) of PKS 2131$-$021 and PKS J0805$-$0111, and showed that the joint global probability, $p$, of these two sources, out of the sample of 1158, being generated randomly due to the red noise tail in their variability spectra is $p<3\times 10^{-3}$ (D25). (cite: ren/etal:2021b) and (cite: ren/etal:2021) were the first to draw attention to possible quasi-periodic oscillations in PKS J0805$-$0111 and PKS 2131$-$021, respectively. However, in the case of PKS J0805$-$0111, D25 argue that they overestimated the significance of the periodicity by several orders of magnitude by assuming the data consisted of independent Gaussian values; similarly, for PKS 2131$-$021, the reported significance of the periodicity is inflated, since they consider the local rather than global significance (c.f., O22).

It is by no means obvious that orbital motion of a SMBH with a relativistic jet will produce sinusoidal variations; however, a mechanism was discovered independently by (cite: 2017MNRAS.465..161S) and by O22, which K25 refer to as the ‘Kinetic Orbital’ (KO) model. In the KO model, one of the SMBHs in the binary system produces a jet, and aberration of this jet due to orbital motion has a large effect on the observed emission from the highly relativistic emitting material. This is shown in O22 to produce sinusoidal variations. While other mechanisms like oscillations or precessions in the accretion disc have been invoked to explain (quasi-)periodic behaviour in AGN light curves (see, e.g., discussions in O22; (cite: TaoAn2013; wangpvb2014; Ingramreview)), the KO model is remarkably simple and economically explains the relevant observed phenomena.

In addition to studying radio light curves, K25 analysed publicly available light curves of PKS 2131$-$021 at millimetre (mm), infrared and optical frequencies and found the same sine wave pattern in them all, as well as ‘hints’ of a sinusoid at $\gamma$-ray frequencies. This broad-band signal is explained well by the KO model since the orbital aberration affects all frequencies. The light curves exhibited a monotonic phase shift in the sine waves from the radio to the optical, spanning more than five decades in frequency. This can be interpreted as an optical depth effect in which the higher frequencies probe closer to the central engine, a behaviour that has been observed in many blazars since it was discovered in the first maps made with very long baseline interferometry (cite: 1978Natur.276..768R; 1980IAUS...92..165R). In the KO model, simultaneous observations of multiple frequencies capture the jet at different points along its helical structure, and thus at different phases of the orbital pattern. Although the light travel time between the higher-frequency and lower-frequency zones corresponds to several sinusoidal cycles, the jet itself is traveling at close to the speed of light. Therefore, by the time the higher-frequency light arrives at the location of the lower-frequency emission, the jet material lags behind only slightly, leading to a relatively small phase delay in the observed light curve. An issue with this model, however, is that it is unclear how the helical structure can remain coherent over a large number of windings spanning tens of parsecs.

In this paper we report observations with the Atacama Cosmology Telescope (ACT) of PKS 2131$-$021 and PKS J0805$-$0111 from 2016 to 2022 at 95, 147 and 225 GHz that provide new insights into these two objects and the phenomenology of SMBHBs in blazars. Furthermore, we present a modified KO (MKO) model that solves the problem of maintaining a helical structure of the jet over many orbital periods by proposing that a sub-relativistic wind, which is dragged by the SMBH orbit, confines the relativistic flow of the jet and results in a helix that need not span so many windings to explain the observations. We also review recent numerical simulations of accretion discs that show how the jet can be interrupted in such a way as to produce the observed intermittency of the sinusoidal pattern in the light curves. Finally, we discuss the potential for wide-field CMB surveys to discover scores of SMBHB candidates and determine their periods, which has implications for gravitational wave science and SMBHB population studies.

The paper is organised as follows. In Sec. [2](#sec:data) we describe the ACT light curves and briefly introduce other key data used in our analyses. In Sec. [3](#sec:sinfit), we present sinusoidal fits to the ACT light curves of PKS 2131$-$021 and PKS J0805$-$0111, and in Sec. [4](#sec:multifreq_properties), we analyse and discuss the relative phase shifts between light curves at different frequencies as well as the achromaticity of the sinusoidal amplitudes. In Sec. [5](#sec:newmodsims), we present the new, MKO model and outline the relevance of recent numerical simulations of accretion discs for SMBHB blazars. In Sec. [6](#sec:cmparison), we discuss the promise of mm observations of AGN for future SMBHB candidate discoveries, comparing and contrasting to optical searches. We summarise our findings and discuss the potential of upcoming mm-surveys for discovering SMBHB candidates in Sec. [7](#sec:discussion).

# Data

## The ACT observations

ACT was a cosmic microwave background (CMB) experiment that operated from 2007 to 2022 in the Atacama Desert of Chile. Its 6 m telescope observed with three generations of receivers: the Millimeter Bolometric Array Camera (MBAC, 2007–11; (cite: swetz/etal:2011)), ACTPol (2013–15; (cite: thornton/etal:2016)) and Advanced ACTPol (2016–22; (cite: henderson/etal:2016)). All receivers were equipped with three optics tubes, each terminating in its own array of detectors that were occasionally changed to allow different combinations of frequencies to be observed. Starting with ACTPol, detectors were polarisation-sensitive and, beginning with the fourth polarised array (PA4), were also dichroic, i.e., sensitive to two frequency bands. Collectively, PA1 to PA7 observed in five frequency bands: f030, f040, f090, f150 and f220. The two lowest frequencies are still being analysed, and all science results so far, including in this paper, come from f090, f150 and f220, whose band centres for a synchrotron spectral index of $-0.7$, averaged across the PAs, were 95.0, 147.1 and 225.0 GHz, respectively.[^2] See (cite: hervias-caimapo/etal:2024) for a full summary of the array timelines and frequencies. The passbands are discussed in (cite: madhavacheril/etal:2020) and (cite: coulton/etal:2024).

A paper presenting the ACT bright AGN sample is in preparation (Ma et al.), and the light curve data will be publicly released. The data reduction process and an analysis of calibration uncertainties and other error sources will be described more fully in that paper and here we introduce only the essentials. Light curves are generated by creating $2\times2\,\si{deg\squared}$ maps centred on the source for each day the source was observed. Data are calibrated from raw readout units to incident power by measuring the detector response to small, square-wave changes in the voltage bias applied to the detectors (cite: niemack:2008); this is performed at least hourly. Interdetector calibration is achieved by flat fielding on the atmospheric emission which creates a common signal mode across the detectors. Calibration from incident power to celestial flux density is achieved using observations of Uranus that were taken every few nights and a final correction based on cross correlating ACT and *Planck* angular power spectra is applied.[^3] See (cite: choi/etal:2020) and (cite: naess/etal:2025) for more information on the general map-making process. With the individual maps in hand, the point source flux density is extracted from each with a matched filter using the known telescope beams and a noise covariance estimated from the map itself after masking the source, similar to the method of (cite: marriage/etal:2011), except that individual pixel weights are also accounted for in the noise covariance.[^4] The resulting light curves tend to have a few outlying points, almost all of which are automatically flagged as outliers by our pipeline due to the low effective number of detectors in the receiver for a particular observation (e.g., because of bad weather, or because the source was near the edge of the observed field). A small fraction of data points, ${\sim}0.1\%$, are flagged as outliers based on conservative visual inspections. In this work we exclude all points flagged as outliers and we combine all light curves from different polarised arrays that are observed at the same frequency (e.g., PA3–f090, PA5–f090 and PA6–f090).

Ma et al. will provide a detailed uncertainty analysis of the calibration, but preliminary studies of the variance of Uranus measurements over time, as well as comparison of flux densities of the AGN between array-bands (e.g., PA5–f090 vs. PA6–f090), indicate an uncertainty of ${\sim}2$ to 7%, depending on the array-frequency channel (cite: hervias-caimapo/etal:2024). These systematic measurement errors, which are not Gaussian-distributed, cause point-to-point scatter in the light curves that is mixed in with any intrinsic variability of observed sources. However, the results of this paper do not rely on detailed knowledge of these sources of uncertainty.

## Key Data at Other Wavelengths

Our analysis includes the following light curves from other observatories that overlap in time with the ACT light curves:

- OVRO light curves of PKS 2131$-$021 and PKS J0805$-$0111 at 15 GHz (cite: Richards2011).

- Atacama Large Millimeter Array (ALMA) light curves of PKS 2131$-$021 at 91.5, 103, 104, 337, 343, 344, 349 and 350 GHz, taken from the ALMA Calibrator Source Catalogue.[^5] Following K25, we combine the 103 and 104 GHz data into a single light curve and call the combination ‘103.5 GHz’. We also combine 337–350 GHz and refer to it as ‘345 GHz’.

- The Catalina Real Time Survey (CRTS; (cite: drake2009)) light curve of PKS 2131$-$021 in the optical $V$-band.

- The Zwicky Transient Facility (ZTF; (cite: masci2019; graham2019)) light curve of PKS 2131$-$021 in the optical $g$-band.

Data from CRTS and ZTF were rebinned to a daily cadence using a weighted mean scheme. For consistency with K25, especially in our analysis of the sinusoid phase shifts (Sec. [4.1](#sec:phase_shifts)), we use the same time spans as they did: MJD 56647.1–60053.7 (21 December 2013 – 19 April 2023) for the ALMA light curves, and MJD 54470.9–60175.3 (5 January 2008 – 19 August 2023) for OVRO.

The redshifts of PKS 2131$-$021 and PKS J0805$-$0111 are 1.285 and 1.39, respectively (cite: drinkwater/etal:1997; paliya/etal:2017).

(10080.00,5320.00) (0,0)

+-------------------------+---------------------+----------------------+----------------------+----------------------+
| Parameter               | OVRO 15 GHz         | ACT 95 GHz           | ACT 147 GHz          | ACT 225 GHz          |
+:========================+====================:+=====================:+=====================:+=====================:+
| $P$ (days)              | $1931\pm19$ (fixed)                                                                      |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $A$ (Jy)                | $0.4357 \pm 0.0052$ | $0.3185 \pm 0.0089$  | $0.2776 \pm 0.0078$  | $0.1899 \pm 0.0240$  |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\phi_0$ (rad)          | $3.678 \pm 0.015$   | $3.212 \pm 0.025$    | $3.179 \pm 0.027$    | $3.100 \pm 0.111$    |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\bar{S}$ (Jy)          | $2.2148 \pm 0.0040$ | $1.4070 \pm 0.0061$  | $1.1550 \pm 0.0054$  | $0.9773 \pm 0.0165$  |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\xi$ (Jy)              | $0.0656 \pm 0.0032$ | $0.0897 \pm 0.0043$  | $0.0992 \pm 0.0040$  | $0.1374 \pm 0.0141$  |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\Delta\phi_0$ (cycles) | 0                   | $-0.0742 \pm 0.0046$ | $-0.0793 \pm 0.0048$ | $-0.0919 \pm 0.0179$ |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\Delta\phi_0$ (days)   | 0                   | $-143.2 \pm 9.0$     | $-153.1 \pm 9.3$     | $-177.5 \pm 34.6$    |
+-------------------------+---------------------+----------------------+----------------------+----------------------+

Table notes: The period, $P$, was determined from an initial fit including only the OVRO data in the range $57500 < \mathrm{MJD} < 59800$. The joint fit including OVRO and the three ACT light curves kept the period fixed at this best fitting value. The fit uncertainties do not account for systematics due to superimposed, shorter term variations (see Appendix [9](#app:empirical_estimate)). The reference time for the phase, in MJD, is $t_0 = 59\,000$. The phase shift, $\Delta\phi_0$, is defined in Eq. [\[eq:phase_shift\]](#eq:phase_shift). Here, and in Tables [\[tab:0805_fits\]](#tab:0805_fits) and [\[tab:alma_2131_fits\]](#tab:alma_2131_fits), two significant figures are retained in the quoted uncertainties for consistency across all fits and as useful for error propagation, but we do not claim to know errors to that precision (see Appendix [9.1](#app:empirical_estimate_backgnd)).

# Sine-wave fits to the light curves

(5040.00,3440.00) (0,0)

\

(5040.00,2880.00) (0,0)

## Method

We fitted a sine wave function to the OVRO and ACT data by maximizing the following likelihood function: $$\begin{align}
\label{eq:mcmc_fit}
  \begin{split}
    \ln\mathcal{L} =& -\frac{1}{2}\sum_{j=1}^4\sum_{i=1}^{N_j}
    \frac{\left(S_{ij}-\bar{S}_j-A_j \sin\left[\frac{2\pi}{P}(t_{ij} - t_0)-\phi_j\right]\right)^2}{\sigma_{ij}^2+\xi_j^2} \\
    & -\frac{1}{2}\sum_{j=1}^4\sum_{i=1}^{N_j}\ln(\sigma_{ij}^2+\xi_j^2),
  \end{split}
\end{align}$$ where the $i$ is the time index of the light curve and $j$ stands for each of the light curves: OVRO 15 GHz, ACT 95 GHz, ACT 147 GHz and ACT 225 GHz, respectively. The light curves, $S_{ij}$, which have $N_j$ points and uncertainties $\sigma_{ij}$, are sampled at times $t_{ij}$; the reference time for the sinusoid phase is set at $t_0 =$ MJD 59 000 (2020 May 31). The period, $P$, is held fixed during the fit (see below), and there are four free parameters per light curve: the sine-wave offset $\bar{S}_j$, amplitude $A_j$, and phase $\phi_j$, plus a term quantifying the correlated noise in the data, $\xi_j$.

We determine the period $P$ by fitting the OVRO data alone in the range where there are ACT data. Then, keeping this period fixed, we do the joint fit of Eq. [\[eq:mcmc_fit\]](#eq:mcmc_fit) described above. The reason for calculating the period only within the ${\sim}6$-year time range where there are ACT data, rather than over the whole range of the OVRO data, is that real flux fluctuations due to processes inside the jet, which are superimposed on the sinusoidal signal, act as a source of ‘noise’ in the sine-wave fits that may not be fully captured by the correlated noise term $\xi$, and would require more SMBHB candidates to be properly understood. See O22, K25 and Appendix [9.1](#app:empirical_estimate_backgnd) for a more detailed discussion of this source of uncertainty. Restricting the fit to the time range when both OVRO and ACT data exist is the best approach for measuring the phase shifts as a function of frequency (see Sec. [4.1](#sec:phase_shifts), below). A result of this restriction of the time range is that the fits with ACT and ALMA data have slightly different fixed periods ($\approx4\%$), since their time spans are not equivalent (see Fig. [1](#plt:2131) and compare Tables [\[tab:2131_fits\]](#tab:2131_fits) and [\[tab:alma_2131_fits\]](#tab:alma_2131_fits)).

The best-fitting parameters and their uncertainties are calculated with a Markov chain Monte Carlo (MCMC) using the EMCEE code (cite: foreman_mackey_2013). The phase shifts are calculated from the best-fitting values as: $$\begin{equation}
\label{eq:phase_shift}
    \Delta\phi_j=(\phi_j-\phi_{\rm OVRO})/2\pi.
\end{equation}$$ The uncertainties represent the 68% confidence range of the marginalized posterior distributions. The results of the fits are reported in Tables [\[tab:2131_fits\]](#tab:2131_fits) and [\[tab:0805_fits\]](#tab:0805_fits); the fits to the OVRO+ALMA data, which are the same as those presented in K25 and were performed with the same methodology described above, are given in Table [\[tab:alma_2131_fits\]](#tab:alma_2131_fits).

## The light curves of PKS 2131$-$021

It is fortunate that PKS 2131$-$021[^6] is an ALMA calibrator that was observed during the same time period as the ACT data, as it affords us the opportunity to compare the ACT 95 GHz light curve with ALMA at 91.5 and 103.5 GHz, providing a useful cross-check of the calibration of the ACT data. The ACT light curves of PKS 2131$-$021 at 95, 147 and 225 GHz are shown in Fig. [1](#plt:2131), together with the OVRO 15 GHz and ALMA 91.5 GHz and 345 GHz light curves.

The ACT 95 GHz data show good consistency with the ALMA 91.5 GHz and 103.5 GHz data. We determine this by comparing the ratio of their light curves after colour-correcting the ALMA data to the ACT band centre using a spectral index of $-0.38\pm0.12$, which we obtained from the ratio of the ALMA 91.5 GHz and 103.5 GHz data for the 219 instances where both bands had simultaneous measurements.[^7] The mean ratio of the 95 GHz ACT flux to the 91.5 ALMA flux, using the 30 pairs of data points measured on the same day in both experiments, is $1.01\pm0.04$. For ACT 95 GHz and ALMA 103.5 GHz, the mean ratio is $1.00\pm0.05$, using the 28 available pairs of data. Another comparison, albeit less precise, can be made using the ratio of the best-fitting sinusoid offsets, $\bar{S}_j$. After colour correcting these offsets, we find: $1.00\pm0.12$ for ACT 95 GHz vs. ALMA 91.5 GHz, and $1.00\pm0.13$ for ACT 95 GHz vs. ALMA 103.5 GHz. Note that the uncertainties here are dominated by the uncertainty in colour correction. (cite: farren/etal:2021) also found consistency between ACT and ALMA flux densities using a few dozen point sources. In their case, the comparison was between ACT fluxes averaged over a year and ALMA data from the same year, rather than between individual points in light curves as we have done here, which they note increases the measurement uncertainty.

A further agreement between ACT and ALMA is found in the scatter in their light curves, which is similar between the two datasets on ${\sim}$month-long time scales. This ‘scatter’ is actually due to real flux density variations in the source. We illustrate this in the top panel of Fig. [2](#plt:J2134_alma-act_corr), in which the long term sinusoidal variation of the ALMA and ACT light curves has been filtered out and the two resulting light curves exhibit similar residuals. The bottom panel shows the Pearson correlation between the ALMA 91.5 GHz and ACT 95 GHz data as a function of how aggressive this high pass filter is. On timescales $> 1$ month the level of correlation is significant; on shorter time scales the correlation is noise dominated.

In Fig. [1](#plt:2131) we see a monotonic progression of the phases of the fitted sine waves with observing frequency, with the higher frequencies leading the lower frequencies. This phenomenon was discovered by K25. (cite: ren/etal:2025) also explored phase shifts in PKS 2131$-$021 using radio (OVRO), infrared (*WISE*, *NEOWISE*) and optical (ZTF, CRTS, Asteroid Terrestrial-impact Last Alert System (ATLAS)) light curves. They found phase shifts of $-0.19\pm0.13$ cycles between radio and infrared and $-0.17\pm0.13$ cycles between radio and optical.[^8] Since their results come from cross-correlation the uncertainties are much larger than K25 but are consistent within the errorbars. We analyse the phase shifts later, in Sec. [4.1](#sec:phase_shifts).

## The ACT light curve of PKS J0805$-$0111

(10080.00,5320.00) (0,0)

+-------------------------+---------------------+----------------------+----------------------+----------------------+
| Parameter               | OVRO 15 GHz         | ACT 95 GHz           | ACT 147 GHz          | ACT 225 GHz          |
+:========================+====================:+=====================:+=====================:+=====================:+
| $P$ (days)              | $1402\pm23$ (fixed)                                                                      |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $A$ (Jy)                | $0.2054 \pm 0.0057$ | $0.1324 \pm 0.0033$  | $0.1119 \pm 0.0030$  | $0.0872 \pm 0.0092$  |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\phi_0$ (rad)          | $2.721 \pm 0.028$   | $1.896 \pm 0.022$    | $1.800 \pm 0.024$    | $1.784 \pm 0.089$    |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\bar{S}$ (Jy)          | $0.4446 \pm 0.0041$ | $0.3221 \pm 0.0022$  | $0.2596 \pm 0.0020$  | $0.2039 \pm 0.0058$  |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\xi$ (Jy)              | $0.0482 \pm 0.0030$ | $0.0410 \pm 0.0018$  | $0.0408 \pm 0.0018$  | $0.0412 \pm 0.0076$  |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\Delta\phi_0$ (cycles) | 0                   | $-0.1312 \pm 0.0056$ | $-0.1465 \pm 0.0058$ | $-0.1490 \pm 0.0148$ |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\Delta\phi_0$ (days)   | 0                   | $-184.0 \pm 7.9$     | $-205.5 \pm 8.1$     | $-208.9 \pm 20.8$    |
+-------------------------+---------------------+----------------------+----------------------+----------------------+

Table notes: The period, $P$, was determined from an initial fit including only the OVRO data in the range $57634 < \mathrm{MJD} < 59343$. The joint fit including OVRO and the three ACT light curves kept the period fixed at this best fitting value. The fit uncertainties do not account for systematics due to superimposed, shorter term variations (see Appendix [9.1](#app:empirical_estimate_backgnd)). The reference time for the phase, in MJD, is $t_0 = 59\,000$. The phase shift, $\Delta\phi_0$, is defined in Eq. [\[eq:phase_shift\]](#eq:phase_shift).

We now turn to the case of PKS J0805$-$0111, for which there are no ALMA data. This is the second OVRO blazar discovered to exhibit significant sinusoidal variations, thereby making it a strong SMBHB candidate (D25). Best-fitting sinusoids to the ACT and OVRO data are reported in Table [\[tab:0805_fits\]](#tab:0805_fits) and are shown along with the light curves in Fig. [3](#plt:0805). The sinusoidal variation discovered at 15 GHz in the OVRO light curve of PKS J0805$-$0111, which lasted from 2008 to 2020 (D25), is clearly also seen in the ACT light curves, and shows that the broadband sinusoidal variation seen in PKS 2131$-$021 is not simply an isolated case. It suggests that broadband sinusoidal emission is a common phenomenon in SMBHB blazar candidates. The KO model explains this phenomenology which has now been confirmed in our two, high significance SMBHB candidates. This could be important for the detection of gravitational waves from SMBHBs.

D25 found that the sinusoidal variations in the 15 GHz OVRO light curve ceased at around MJD 59041, shown in Fig. [3](#plt:0805) with a dashed, vertical line. Although the ACT light curves do not extend long after this date, they too appear consistent with the sinusoid shutting off. A similar phenomenon was also observed by O22 and K25 in PKS 2131$-$021 in more than 45 years of data: its light curve was sinusoidal for about the first seven years, then non-sinusoidal for 19 years, after which the sinusoid recommenced with a smaller amplitude but otherwise consistent, in both period and phase, with the original periodicity. Completely independent fits to the Haystack data (1975–1983) and to the OVRO data (2008–2020) gave periods of $1729.1\pm32.4$ days and $1760\pm5.3$ days, respectively (O22). This is the same period within the uncertainties, which is better than 2%. Moreover, the new sinusoid was in phase with the original to within ${\sim}10\%$ of a cycle (O22). This suggests that the underlying mechanism is a good clock—i.e., the SMBHB orbit according to the KO model—that continued running when the sinusoidal variation seen in the Haystack and OVRO data was absent. The temporary cessation of the sinusoid is not explained by KO model *per se*, but O22 and K25 point out that its disappearance, as well as the change in its amplitude when it reappears, could plausibly be produced by changes in the fuelling of the jet. We discuss this intermittency in more detail in Sec. [5.2](#ssec:bh_sims).

As in the case of PKS 2131$-$021, a monotonic phase shift with frequency is observed in the light curves, which we analyse in Sec. [4.1](#sec:phase_shifts), below.

# Multi-frequency properties of the SMBHB candidates

## Frequency-dependent phase shifts

(4680.00,5040.00) (0,0)

|               |                |           |           |
|:-------------:|:--------------:|:---------:|:---------:|
|  Instrument   |   Frequency    |   Phase   |  Uncert.  |
|               |      Band      | (Fraction | (Fraction |
|               |                | of cycle) | of cycle) |
|   Haystack    |    2.7 GHz     |   0.145   |   0.028   |
|   Haystack    |    7.9 GHz     |   0.048   |   0.013   |
| Haystack/OVRO |  15 GHz$^{a}$  |     0     |     0     |
|   Haystack    |    31.4 GHz    | $-0.034$  |   0.022   |
|     ALMA      |    91.5 GHz    | $-0.073$  |   0.005   |
|      ACT      |     95 GHz     | $-0.074$  |   0.005   |
|     ALMA      |   103.5 GHz    | $-0.077$  |   0.005   |
|      ACT      |    147 GHz     | $-0.079$  |   0.005   |
|      ACT      |    225 GHz     | $-0.092$  |   0.018   |
|     ALMA      |    345 GHz     | $-0.134$  |   0.009   |
|    *WISE*     | infrared$^{b}$ |  $-0.27$  |   0.05    |
|      ZTF      | optical$^{c}$  | $-0.352$  |   0.008   |

: PKS 2131$-$021 Phase Shifts with Frequency

Table notes: The OVRO light curve was the phase reference, except for the Haystack data, whose light curves do no overlap with the others, and which use the Haystack 15.5 GHz channel as the reference. Apart from the ACT results, data in this table are taken directly from table 2 of K25.\

|           |           |             |
|:---------:|:---------:|:-----------:|
| Frequency |   Phase   | Uncertainty |
|   Band    | (Fraction |  (Fraction  |
|           | of cycle) |  of cycle)  |
|  15 GHz   |     0     |      0      |
|  95 GHz   | $-0.131$  |    0.006    |
|  147 GHz  | $-0.147$  |    0.006    |
|  225 GHz  | $-0.149$  |    0.015    |

: PKS J0805$-$0111 Phase Shifts with Frequency Relative to the 15 GHz Light Curve

Table notes: The 15 GHz light curve was used as the phase reference for the ACT data.

As noted in the previous section, in both of our sources the higher frequency ACT light curves are shifted towards earlier times relative to the OVRO 15 GHz light curves, and the shift is monotonic with frequency. This behaviour is explained by the KO model as being due to frequencies originating at different positions along the jet because of optical depth effects, and is further discussed below in the context of our new MKO model (Sec. [5.1](#ssec:mko)).

Table [1](#tab:2131_phases) shows the phase shifts for PKS 2131$-$021. In addition to the phase shifts of the ACT light curves relative to OVRO, it includes the phase shifts of light curves from the Haystack observatory (radio), ALMA (mm), the Wide-field Infrared Survey Explorer (*WISE*; infrared) and ZTF (optical), all relative to OVRO, as listed in table 2 of K25. Note that the Haystack data came from an earlier time period (1975–1983) and did not overlap with the other datasets; thus, the phase shift for the Haystack light curves are relative to the 15.5 GHz Haystack channel. The coherent behaviour from 2.7 GHz to optical wavelengths is strikingly illustrated by Fig. [4](#plt:2131_phases), which shows the phase shift measurements on top of the best-fit quadratic phase–frequency relation from K25, $$\begin{equation}
\label{eq:2131_quadratic_fit}
    \Delta \phi = 0.178 - 0.146\log_{10}(\nu) + 0.0093[\log_{10}(\nu)]^2.
\end{equation}$$ We discuss these phase shifts and Eq. [\[eq:2131_quadratic_fit\]](#eq:2131_quadratic_fit) shortly, below.

Table [2](#tab:0805_phases) lists the phase shifts for PKS J0805$-$0111. Note that, as found in PKS 2131$-$021, the ACT sinusoids are shifted towards earlier times relative to the OVRO 15 GHz light curve, and the shift is consistent with being monotonic with frequency. This is therefore likely to be a common phenomenology in SMBHB blazar candidates and a signature of a fundamental property of these jets.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| AGN | Data Sets | Span | $b$ | $a$ | $\chi^2$/dof | PTE |
|  |  | (GHz) |  | (cycles GHz$^{-1}$) |  |  |
| PKS 2131$-$021 | Haystack, OVRO, ALMA, ACT | 3–345 | $-0.3^{+0.1}_{-0.1}$ | $0.396^{+0.09}_{-0.001}$ | $13.3/7$ | 0.07 |
| PKS 2131$-$021 | Haystack, OVRO, ALMA, ACT | 3–225 | $-0.46^{+0.1}_{-0.09}$ | $0.44^{+0.06}_{-0.04}$ | $1.01/6$ | 0.99 |
| PKS 2131$-$021 | OVRO, ACT | 15–225 | $-0.8^{+0.1}_{-0.6}$ | $0.8^{+2}_{-0.2}$ | $0.21/1$ | 0.65 |
| PKS J0805$-$0111 | OVRO, ACT | 15–225 | $-0.7^{+0.2}_{-0.4}$ | $1.2^{+2}_{-0.3}$ | $0.22/1$ | 0.64 |

Table notes: Uncertainties are 68% credible intervals.

(5040.00,3600.00) (0,0)

The exact form of the frequency phase–shift relation depends on the details of where different frequencies originate in the blazar jet. The simple quadratic fit by K25 to the PKS 2131$-$021 phase shifts (Eq. [\[eq:2131_quadratic_fit\]](#eq:2131_quadratic_fit)) is not motivated by any particular jet model but is purely phenomenological. While the ACT 95 GHz measurement agrees with this curve, and is consistent with the ALMA measurement, the 147 GHz and 225 GHz measurements are $3.1\sigma$ and $1.2\sigma$ higher than the curve, respectively. A power law is potentially more physically realistic: $$\begin{equation}
\label{eq:powlaw}
  \Delta\phi = a (\nu^b - \nu_0^b),
\end{equation}$$ where $a$ and $b$ are model parameters and $\nu_0$ is the reference frequency for the phase shifts, in our case 15 GHz. This equation is motivated by the theoretical prediction that that the distance along the jet of the emission zone goes as $r \propto \nu^{-1}$ when the jet is optically thick (cite: blandford/konigl:1979). Eq. [\[eq:powlaw\]](#eq:powlaw) follows because the phase shift in the KO model is due to light-travel times, and thus proportional to $r$. Fig. [4](#plt:2131_phases) shows the best fit of Eq. [\[eq:powlaw\]](#eq:powlaw) to the radio and mm data (Haystack, ALMA and ACT) for PKS 2131$-$021, with best-fitting parameters reported in Table [\[tab:phase_comparison\]](#tab:phase_comparison).[^9] Fits were performed with a Metropolis–Hastings Monte Carlo (MC) with flat priors in the ranges $b = (0.05, 4)$ and $a = (-2, -0.05)$. The priors were cut off before zero to prevent the MC from piling up near unphysical $a = 0$. The exact cutoff does not change the maximum likelihood; naturally, though, it alters the posterior credible regions that we use for our error bars, but this does not qualitatively alter our findings. To check the accuracy of the MC, we also performed fits with the Marquardt–Levenberg algorithm and found consistent best-fitting values. Note that we do not know the level of covariance between all of the data points, which are treated independently in our fits, but in reality there will be some degree of covariance (see Appendix [9](#app:empirical_estimate)).

(5040.00,3600.00) (0,0)

The best-fitting index of $b = -0.3\pm0.1$ for the PKS 2131$-$021 mm data suggests that the jet is not optically thick in these emission zones. This may be compared to the finding in K25, based on the emission spectrum of PKS 2131$-$021, that the jet is optically thick below 70 GHz and optically thin above. To explore whether our result is sensitive to particular combination of frequencies, we fit different ranges. First, since the 345 GHz point from ALMA is a notable outlier to our fit—though the goodness of fit is acceptable, with PTE = 0.07—we excluded this point and obtained $b = -0.46^{+0.1}_{-0.09}$. (All fit results are shown in Table [\[tab:phase_comparison\]](#tab:phase_comparison).) This may suggest that the jet becomes optically thinner above 225 GHz, but the difference in fits is marginal. If we restrict our fits to the phase shifts of the ACT data alone (95–225 GHz), the best-fitting index is $b = -0.8^{+0.1}_{-0.6}$, which has too broad a posterior to be informative; Fig. [5](#plt:phase_mcmc) shows that the ACT data in isolation are not sufficient to break the degeneracy of the power law amplitude, $a$, and index, $b$. Thus, more phase-shift data are needed to probe whether the optical thickness changes through the radio, mm and submm emission regions, but our results are most consistent with the jet being optically thin in these zones.

Fig. [6](#plt:phase_comparison) shows the frequency–phase relations from the ACT data of PKS 2131$-$021 and PKS J0805$-$0111 together with the best-fitting power laws. Interestingly, the best-fitting values for the power law index are similar between the two AGNs (0.8 and 0.7 for PKS 2131$-$021 and PKS J0805$-$0111, respectively), both of which are consistent with $b = -1$. However, as mentioned above, the data support a wide range of $b$ values (see Fig. [5](#plt:phase_mcmc)) so this similarity may be a coincidence.

In summary, two points should be noted about the phase shifts:

1.  For both SMBHB candidates, the phase shift between 15 GHz and 95, 147 and 225 GHz is highly significant: $\chi^2$ for the null hypothesis of no phase shift is 548 and 1288, with three degrees of freedom, for PKS 2131$-$021 and PKS J0805$-$0111, respectively. Thus, regardless of the details of how the slope behaves in the radio and mm regime (point 2, below), the ACT data provide a strong detection of the phase shift between the radio and mm sinusoidal emission.

2.  When all radio and mm data are considered, the power law index is inconsistent with the jet of PKS 2131$-$021 being optically thick. If only the ACT data are considered, PKS 2131$-$021 and PKS J0805$-$0111 have similar best-fitting values for the power law index, but support a wide range of values. More data are needed to understand if there is a change in jet properties in the mm zones.

Improving on these results above would not only benefit from more data, but would also require better understanding of the uncertainties of the phase shifts. As discussed in K25, intrinsic variations in the jet that are superimposed on the sinusoidal variations can add covariance between the light curves at different frequencies, complicating the noise model used in fitting. We discuss this further in Appendix [9](#app:empirical_estimate), where we also make an empirical estimate of the phase shift uncertainties by injecting sine waves into other, real ACT light curves. These uncertainties are shown with light errorbars in Fig. [6](#plt:phase_comparison). Our analysis suggests that the MCMC-derived errorbars listed in Tables [\[tab:2131_fits\]](#tab:2131_fits) and [\[tab:0805_fits\]](#tab:0805_fits) and shown with heavy errorbars in Fig. [6](#plt:phase_comparison), are possibly underestimated. However, as we argue in Appendix [9](#app:empirical_estimate), light curves of more SMBHB candidates are needed to confirm such an assessment.

## Achromatic variability

Both the sinusoidal variation in emission (Sec. [3](#sec:sinfit)) and the frequency-dependent phase shifts just discussed (Sec. [4.1](#sec:phase_shifts)) provide important constraints on the physical origin of the emission and are predicted by the KO model. The model also predicts that the fractional amplitude of the sinusoidal variations should be achromatic, assuming the spectral index $\alpha$ is constant, since the rest-frame flux density, $S'$, gets boosted to $S = \mathcal{D}^{2-\alpha}S'$, where $\mathcal{D}$ is the Doppler factor (K25). This is a third feature we verify in our data. The fractional change in intensity, expressed as $A/\bar{S}$, is similar for all frequencies (see Tables [\[tab:2131_fits\]](#tab:2131_fits) and [\[tab:0805_fits\]](#tab:0805_fits)). K25 noted that it only varied by a factor of $\sim$2–3 over five decades in frequency, though their picture is complicated somewhat by the fact that the data were taken at several epochs. In contrast, K25 show that the OVRO and ALMA data, which were contemporaneous, show remarkably achromatic behaviour. In the OVRO+ACT data at 15, 95, 147 and 225 GHz, we find $A / \bar{S} = (21\pm2)\,\%$ for PKS 2131$-$021, where the quoted uncertainty is the standard deviation of the ratios at the four frequencies. As with the other SMBHB properties, we once again confirm for the first time that this expected property is found in a second SMBHB candidate: PKS J0805$-$0111 exhibits achromaticity, with $A / \bar{S} = (43\pm2)\,\%$.

# Interpreting the observations

## A modified Kinetic Orbital (MKO) model

(9.0,3.5) (0,0)![image](mko_diagram.pdf) (0.85,2.25)(0,0)\[l\]$\color{mko_green}\vec{\beta}_{\mathrm{w}}$ (1.85,1.65)(0,0)\[l\]$\color{mko_blue}\vec{\beta}$ (5.85,2.925) (3.3,0.25)(0,0)\[l\]225 GHz (5.85,0.25)(0,0)\[l\]15 GHz

In this section we present a modified KO model, which we will refer to here and in future papers as the ‘MKO’ model. In the original KO model ((cite: 2017MNRAS.465..161S); O22), the emitting region moves ballistically from one of the SMBH, producing a jet propagating at relativistic speeds and twisted into a conical helix by the orbital motion of the SMBH engine. The phase shift in the observed sinusoidal variations in flux between two frequencies, $\Delta\phi$, is due to the light-travel time between the two different zones of emission along the jet. Because the jet’s velocity, $\beta = v / c$, is relativistic, in the observer’s frame the jet material from the deeper zone travels almost as fast as the emitted light, such that its distance from the shallower zone, $\Delta r$, appears to be (K25): $$\begin{equation}
\label{eq:distance}
    \Delta r = \beta(1+\beta) \gamma^2 c P_{\mathrm{B}} \Delta \phi \approx 2\gamma^2 c P_{\mathrm{B}} \Delta\phi,
\end{equation}$$ where $\gamma = (1-\beta)^{-1/2}$ is the Lorentz factor, $c$ is the speed of light, $P_{\mathrm{B}}$ is the binary orbital period (in the rest frame) and $\Delta\phi$ is in units of cycles. For high Lorentz factors, this implies that the deeper zone has wound through multiple helical rotations before the light is emitted from the shallower zone, even though the observed phase difference is a fraction of a cycle. For instance, K25 use VLBI measurements to obtain $\gamma = 10$ for PKS 2131$-$021; using our best-fitting period and phase differences (Table [1](#tab:2131_phases)), this yields a distance of ${\sim}18$ pc and ${\sim}26$ helical windings between the 15 GHz and 95 GHz emission zones. This is a potential problem with the simple KO model, because it is hard to explain how the jet can remain in a coherent helical pattern over such a distance. It would seem more likely that the phase would get smeared out.

In our new MKO model, the outflowing, ultrarelativistic jet containing the emitting electrons is not launched ballistically by its black hole source but instead follows a channel defined by a slower, mildly relativstic or sub-relativstic hydromagnetic wind that confines it (Sullivan et al. in prep). This semi-ballistic wind, possibly launched from the disc, confines the relativistic flow, dragging it around with the binary motion (see Fig. [7](#plt:mko_diagram)). The channel may only be defined for a few helical windings, but because the wind has a low Lorentz factor (c.f., Eq. [\[eq:distance\]](#eq:distance)) this suffices to account for sinusoidal variation due to the varying angle of the jet line of sight to the observer. The jet–wind complex forms a helix with pattern speed set by the wind rather than the relativistic flow. The different emission regions can thus come from a range of radii with each frequency’s minimum radius separated by less than a wavelength of the conical helix $\lambda_h = \beta_w c P_\mathrm{B}$ and the average radius need not be separated by more than ${\sim}10\,\lambda_h$.

Our analysis of the sinusoid phase shifts in Sec. [4.1](#sec:phase_shifts) showed that the ACT data alone cannot constrain the power law $\Delta\phi \propto \nu^b$ well, but that when Haystack and ALMA data are included, there is evidence of $b < 1$ for PKS 2131$-$021. This differs from the classic scaling expected for the depth of a marginally optically thick photosphere as a function of frequency $r\propto\nu^{-1}$ (cite: blandford/konigl:1979) and would suggest that the emission does not come entirely from an optically thick photosphere as in the classic picture but instead may be optically thin. If optically thin, the observed emission at each radius would also contain the tail of the local synchrotron spectrum (Sullivan et al. in prep), and the frequency of the emissivity cut-off would thus decrease with distance along the jet.

## Simulations that address the intermittency of the periodicity

An observed feature of both PKS 2131$-$021 and PKS J0805$-$0111 that is not explained by the MKO model as presented thus far is the intermittency of the sinusoid pattern (see Sec. [3.3](#sec:pks0805)). Here, we provide for the first time a possible physical explanation for this phenomenon. It is based upon the possibility of precession or disturbances in the SMBH accretion disc temporarily disrupting the production of a jet. Synchrotron emission from much further out in the jet is responsible for the baseline synchrotron emission (as found by O22 via VLBI measurements of PKS 2131$-$021), while the sinusoidal component is produced by the MKO mechanism near the central engine. When the jet is disrupted at its base, the sinusoidal signal shuts off, but when the jet relaunches the new sinusoid is in phase with the previous sinusoid because the SMBHB orbit has continued unabated.

This picture is supported by recent numerical simulations which have have extensively investigated black hole accretion flows; see, e.g., (cite: Davis:2020wea) for a recent review. Three-dimensional simulations of magnetised circumbinary accretion, in particular on black hole binaries, have also advanced considerably (cite: Farris:2012ux; Gold:2013zma; Manikantan:2024giq; Ennoggi:2025nht; Avara:2023ztw). In the context of circumbinary disc formation from intermediate galactic scale accretion, (cite: wang2025galactic) have recently shown that realistic circumbinary discs might be strongly warped and tilted ((cite: nixon2013tearing); see also (cite: Guo:2024gqc) for a similar study on single black holes). Although these simulations focus on equal-mass black hole binaries, the disc tilt originates from large-scale inflow and is expected to persist in systems with unequal mass ratios. These tilted accretion discs launch jets along the disc’s rotation axis rather than the black hole’s, as shown by (cite: liska2018formation), who employed 3D general relativistic magnetohydrodynamic simulations. (cite: liska2018formation) showed how strong magnetic flux can partially realign the inner disc and jets with the black hole spin. On longer timescales, the entire disc-jet system undergoes Lense-Thirring precession (cite: lense1918einfluss). This precession can produce curved jet morphologies and, in some cases, disrupt the accretion flow and shut off the jets. Misaligned circumbinary accretion discs around a binary black hole system lead to disc tearing, caused by strong differential torques (cite: nixon2013tearing; kaaz2025extreme), which can result in jets shutting off. As such, realistic accretion environments might naturally be able to explain the temporary absence of a jet, with the timescale potentially being correlated with the inner disc precession timescale.

Even in the absence of disc tilt and precession, the accretion flow onto one constituent black hole in the binary can naturally feature variability. (cite: lalakos2025universal) have shown that extremely long-duration 3D general relativistic magnetohydrodynamic Bondi-like simulations (cite: Cho:2023wqr; Galishnikova:2024nsk; Guo:2025sjb) can exhibit transitions between a magnetically arrested disc (MAD) state (cite: 2003PASJ...55L..69N; 2011MNRAS.418L..79T), characterized by strong, stable jets, and a rocking accretion disc (RAD; (cite: lalakos2024jets)). In the RAD state, the gas angular momentum is randomly oriented and chaotic, which leads to violently precessing inner accretion discs. The RAD jets are weaker as they tilt, wobble, and dissipate within a few thousand gravitational radii. These simulations show that MAD-to-RAD cycles occur on timescales of $\tau \sim 10^5 \, r_{\mathrm{g}}\,c^{-1}$, where $r_{\mathrm{g}}$ is the black hole’s gravitational radius. For a $10^8\,\mathrm{M}_\odot$ black hole, $\tau \sim 600$ days—comparable to the orbital period of our SMBHB candidates. In this scenario, continued monitoring of such systems may reveal multiple accretion and jet activity cycles tied to the Bondi accretion timescale of the individual black hole rather than the binary’s orbital period.

# The value of millimetre light curves for SMBHB searches

(10080.00,4320.00) (0,0)

A notable feature of the mm light curves shown in Figs. [1](#plt:2131) and [3](#plt:0805) is their short-term deviations from the sinusoids. However, for the 95 and 147 GHz light curves, the sinusoidal variation dominates by a factor of $\sim$2–3.5 (see the $\mathrm{SNR}_{\mathrm{sin}}$values in Table [3](#tab:smbhb_props)). Thus, although the mm light curves do not have the same sensitivity as the OVRO 15 GHz light curves, and hence the uncertainties on individual observations are much larger in the ACT than in the OVRO data, this does not mean that ACT is less sensitive to sinusoidal light curves in blazars than the OVRO, provided we consider equal timespans.[^10] This argues strongly for continued, long term observations with mm survey instruments, such as the South Pole Telescope (cite: carlstrom/etal:2011; benson/etal:2014), the Simons Observatory (SO; (cite: so_collaboration:2019; so_collaboration:2025)) and the CCAT Observatory (cite: ccat:2023) for multi-messenger astronomy.

The promise of cm, mm, and submm data for identifying and studying SMBHB is evident when they are placed side by side with optical data. Fig. [8](#plt:optrad) shows the OVRO 15 GHz light curve of PKS 2131$-$021 together with optical light curves of the same object from CRTS and ZTF. As discussed in K25, the ZTF data show much stronger short-term variations than the radio–submm data, but when averaged over a year they follow a sine wave well and have a period consistent with that derived from the OVRO and Haystack 15 GHz observations. To further explore this point, in Appendix [10](#app:sim) we give a detailed account of statistical tests we have carried out on the CRTS and ZTF data for PKS 2131$-$021 and show that the optical data alone do not provide compelling evidence for the periodicity we see in PKS 2131$-$021, unless they are sampled about 3 times a week and then averaged for a long period ($\sim$ several months) to eliminate the rapid large fluctuations at optical wavelengths. This is illustrated in Fig. [8](#plt:optrad) by the sine wave, fitted to ZTF data by K25 (reported in their table 4), and here extrapolated back to the period covered by the CRTS. There is no clear correspondence between the curve and the CRTS data points, suggesting that searches for SMBHB candidates similar to PKS 2131$-$021 are unlikely to be found in the CRTS because the cadence is not frequent enough. The ZTF cadence is two days, and that clearly works well, although the short-term variations are much greater than at cm–mm–submm wavelengths. We do not offer any specific theories here about the origin of this behaviour, but it is reasonable to suppose that activity near the central engine could produce very different short-term variations than those seen from the more distant zones producing the radio and mm radiation.

(cite: ren/etal:2025) also found only weak evidence for periodicity from a Lomb-Scargle analysis of infrared (*WISE*, *NEOWISE*) and optical (ZTF, CRTS, ATLAS) light curves of PKS 2131$-$021, further highlighting the importance of cm-mm-submm data for this class of SMBHB candidate.

The cm, mm, and submm observations also have the great advantage that they can be sampled year-round, while at optical frequencies the daylight sky is bright compared to even the brightest optical blazar, 3C 273, which has an apparent optical magnitude of $V \sim 13$,[^11] so year-round optical monitoring of blazars is not possible.[^12] Nevertheless, there is evidence for SMBHB candidates that show more prominent sinusoidal variations at optical wavelengths. PG 1302$-$102 might be just such an example (cite: 2015Natur.518...74G): this source also shows radio periodicity at the same period as detected in the optical (cite: 2018A&A...615A.123Q). Recently, (cite: huijse/etal:2025) reported the detection of 181 SMBHB candidates from a search of 770,100 AGN that were monitored for 34 months in the optical by the *Gaia* satellite. It is therefore likely that optical and cm–mm–submm observations will be highly synergistic for discovering and characterising SMBHBs.

# Summary and discussion

ACT mm data at 95, 147 and 225 GHz have confirmed the presence of a sinusoidal variation in the light curves of PKS 2131$-$021 and PKS J0805$-$0111 that had been detected with high significance in OVRO 15 GHz data by O22, D25 and K25. Our main findings are as follows:

1.  The ACT 95 GHz light curve of PKS 2131$-$021 is in good agreement with the ALMA 91.5 and 103.5 GHz light curves, including in their small variations superimposed on the larger sinusoid variation. This confirms that the ACT calibration and data reduction of light curves are working well.

2.  ACT light curves of PKS J0805$-$0111, for which no ALMA data are available, corroborate the finding in D25 that this source is a SMBHB candidate. Especially compelling is the fact that the sinusoid appears to turn off in the ACT light curves in the same manner as in the OVRO data in mid-2020 (see Fig. [3](#plt:0805)). This provides further evidence that: (a) the long time-scale variations of the mm light curves are tracing the same underlying physics as the radio light curve and (b) that the phenomenon of the sinusoid stopping and starting, discovered in O22 for PKS 2131$-$021, is likely a common feature of SMBHB candidates. It can be explained as the temporary disruption of the jet by precession or by MAD-to-RAD transitions of the accretion disc. Further data will help clarify these hypotheses, and our results show that mm observations can play a key role in detecting this behaviour.

3.  The ACT data confirm that the sinusoidal variations at higher frequencies are shifted in phase relative to radio frequencies, a feature that is naturally explained in the MKO model by light-travel times due to higher frequencies originating from deeper in the jet. In both cases the mm phase leads the radio phase in time.

4.  A power-law fit to the phase shifts in PKS 2131$-$021 in the radio to submm-regime suggest that the jet in these emission zones is optically thin, but it is unclear whether the jet properties are uniform throughout the regions. ACT data alone cannot well-constrain the power-law index for either PKS J0805$-$0111 or PKS 2131$-$021 given current uncertainties.

5.  The sinusoidal signal is achromatic from 15 to 225 GHz, i.e., the ratio of its amplitude to offset, $A/\bar{S}$, is nearly constant at all measured frequencies in this range. This is expected under the MKO model and is further evidence for these objects being SMBHBs.

6.  In PKS 2131$-$021, the ratio of the sinusoid amplitude to the non-sinusoidal variations in the mm data is significantly higher than in optical data, which are contaminated by large, short term variability from the point of view of detecting SMBHB candidates. It seems likely that some SMBHB candidates will appear more cleanly in the optical (e.g., PG 1302$-$102, (cite: 2015Natur.518...74G); see also (cite: huijse/etal:2025)), but our findings provide strong motivation for using mm surveys to search for SMBHB. Such searches will be complementary to radio, submm and optical searches.

In addition to these empirical findings, we have presented the MKO model which, when combined with recent findings from simulated BH accretion discs, explains all four of the properties observed in the two SMBHB candidates: (a) the flux density exhibits a sinusoidal pattern; (b) the sinusoid is monochromatic, in that it has the same period and a similar amplitude to mean-flux ratio over a broad range of frequencies; (c) the phase of the sinusoid shifts monotonically with frequency; (d) the sinusoidal variations are intermittent on time scales $\gtrsim$ the SMBHB period.

Our results demonstrate the value of high cadence, wide area surveys of the mm and submm sky available from CMB and mm/sub-mm survey experiments such as SPT, SO and CCAT. In particular, the large aperture telescope (LAT) of SO will observe $25\,000\,\mathrm{deg}^2$ of the sky from 2025 to 2034 at 27, 39, 93, 145, 225 and 280 GHz with a planned cadence of 1–2 days (cite: so_collaboration:2025).[^13] We use their goal sensitivity for single observations at 93 GHz to forecast the number of AGN that SO can monitor over a $21\,000\,\mathrm{deg}^2$ sky area (to exclude the Galactic plane), using the 90 GHz radio number counts of (cite: lagache/etal:2020). We find that SO will be able to monitor ${\sim}8000$ AGN with a signal-to-noise ratio \> 5, if we allow six measurements to be binned together (i.e., corresponding to a 1–2 week cadence). The number will increase to ${\sim}12\,000$ when the Advanced SO upgrades, which will double the number of detectors, are completed by 2028. Estimating the rates of blazars in SMBHB depends on a number of factors, as discussed in K25 and D25, but these authors conclude that with current information, ${\sim}1$ in 100 blazars may be in SMBHB systems. If this is correct then SO should be able to observe $\mathcal{O}(100)$ SMBHB candidates. This large sample size will better constrain the SMBHB occurrence rate. At this point PKS 2131$-$021 is the only blazar in which sinusoidal variations have been observed at both optical and radio wavelengths,[^14] but this is unlikely to be an isolated case given the broadband sinusoidal variations of PKS J0805$-$0111 that we present in this paper, making a compelling case for joint searches for SMBHB candidates spanning from the radio to optical.

The nature of sinusoidal blazar signals and their potential connection with supermassive black hole binaries is of fundamental interest for both astrophysics and cosmology. Multi-wavelength information about more systems and over more periods, as will be possible with upcoming mm-wave surveys, will establish the correct model of emission and its connection to binary properties, including the duty cycle for sinusoidal emission and the selection function for observing binaries. Significant detections of correlated gravitational wave and electromagnetic signals from particular SMBHB systems are also imminent (cite: 2025arXiv250816534A). In principle, the absolute phase of mm-discovered SMBHB could be obtained from optical light curves, since the optical emission is believed to originate close to the AGN core and would therefore be virtually in phase with the SMBHB orbit. Further, if velocities were obtained from optical spectra, the masses could be derived, and the expected gravitational wave phase and amplitude of each source could be determined. One could then mount coherent gravitational wave searches with millsecond pulsar timing arrays, rather than searching within the stochastic noise, potentially expanding their reach to weaker sources of gravitational waves. In turn, these observations and binary blazar models could provide more reliable observation-based estimates of the total binary population with orbital periods of years. This population is of intense interest for its production of gravitational waves: the Laser Interferometer Space Antenna (LISA) will directly measure the supermassive binary merger rate throughout the Hubble volume, and comparison with the total years-period binary population will constrain the complex galactic dynamics and astrophysical mechanisms driving binary mergers (e.g., (cite: 2015ApJ...812...72A; 2020MNRAS.497..739N; 2003ApJ...596..860M)).

In addition, the close-orbit SMBHB population will likely provide a dominant contribution to the stochastic background of gravitational waves at nanohertz frequencies for pulsar timing arrays or astrometric probes (cite: 2023ApJ...952L..37A). This stochastic background complicates the prospects for detecting other cosmological sources of gravitational waves from the early universe (cite: 2021PhRvD.103j3529B), such as phase transitions or reheating after inflation (see (cite: 2023ApJ...951L..11A) for a recent overview). A detailed understanding of the SMBHB population enabled by multi-wavelength blazar observations may eventually be key to exploiting unique gravitational wave information about physics at the highest energy scales.

# Acknowledgements

We thank an anonymous referee for comments that strengthened our analysis and prompted us to introduce the MKO model.

This work was supported by the U.S. National Science Foundation through awards AST-0408698, AST-0965625, and AST-1440226 for the ACT project, as well as awards PHY-0355328, PHY-0855887, and PHY-1214379. Funding was also provided by Princeton University, the University of Pennsylvania, and a Canada Foundation for Innovation (CFI) award to UBC.

ACT operated in the Parque Astronómico Atacama in northern Chile under the auspices of the Agencia Nacional de Investigación y Desarrollo (ANID; formerly Comisión Nacional de Investigación Científica y Tecnológica de Chile, or CONICYT). We thank the Republic of Chile for hosting ACT in the northern Atacama, and the local indigenous Licanantay communities whom we follow in observing and learning from the night sky.

The development of multichroic detectors and lenses for ACT was supported by NASA grants NNX13AE56G and NNX14AB58G. Detector research at NIST was supported by the NIST Innovations in Measurement Science program. Computing for ACT was performed using the Princeton Research Computing resources at Princeton University, the National Energy Research Scientific Computing Center (NERSC), and the Niagara supercomputer at the SciNet HPC Consortium. SciNet is funded by the CFI under the auspices of Compute Canada, the Government of Ontario, the Ontario Research Fund–Research Excellence, and the University of Toronto.

Colleagues at AstroNorte and RadioSky provided logistical support for ACT and kept operations in Chile running smoothly. We also thank the Mishrahi Fund and the Wilkinson Fund for their generous support of the project.

The OVRO programme was supported by NASA grants NNG06GG1G, NNX08AW31G, NNX11A043G, and NNX13AQ89G from 2006 to 2016 and NSF grants AST-0808050 and AST-1109911 from 2008 to 2014. This work is currently supported by NSF grants AST2407603 and AST2407604.

This is not an official SO Collaboration paper.

ADH acknowledges support from the Sutton Family Chair in Science, Christianity and Cultures, from the Faculty of Arts and Science, University of Toronto, and from the Natural Sciences and Engineering Research Council of Canada (NSERC) \[RGPIN-2023-05014, DGECR-2023-00180\], and is further grateful to the Lumen Christi Institute for support that enabled a research visit to the University of Chicago, during which significant portions of this work were done. S.K. was funded by the European Union ERC-2022-STG – BOOTES – 101076343. Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them. CS acknowledges support from the Agencia Nacional de Investigación y Desarrollo (ANID) through Basal project FB210003. MJG acknowledges support from NSF grant AST-2108402.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00001.CAL. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

The CSS survey is funded by the National Aeronautics and Space Administration under Grant No. NNG05GF22G issued through the Science Mission Directorate Near-Earth Objects Observations Program. The CRTS survey is supported by the U.S. National Science Foundation under grants AST-0909182 and AST-1313422.

ZTF is supported by the NSF under Grants No. AST-1440341 and AST-2034437 and a collaboration including current partners Caltech, IPAC, the Oskar Klein Center at Stockholm University, the University of Maryland, University of California, Berkeley , the University of Wisconsin at Milwaukee, University of Warwick, Ruhr University, Cornell University, Northwestern University and Drexel University. Operations are conducted by COO, IPAC, and UW.

This research has made use of the NASA/IPAC Extragalactic Database (NED), which is funded by the National Aeronautics and Space Administration and operated by the California Institute of Technology.

Some of the results/plots in this paper have been derived/produced using the following software: ASTROPY,[^15] a community-developed core Python package for Astronomy (cite: software:astropy/a; software:astropy/b; software:astropy/c); EMCEE (cite: foreman-mackey/etal:2013); FASTKDE (cite: travis/etal:2014; travis/etal:2016); GNUPLOT;[^16] NUMPY (cite: software:numpy); PIXELL;[^17] and SCIPY (cite: software:scipy).

91 natexlab

(ref: so_collaboration:2025) Abitbol, M., Abril-Cabezas, I., Adachi, S., et al. 2025, JCAP, 2025, 034

(ref: so_collaboration:2019) Ade, P., Aguirre, J., Ahmed, Z., et al. 2019, JCAP, 2019, 056

(ref: 2023ApJ...951L..11A) Afzal, A., Agazie, G., Anumarlapudi, A., et al. 2023, ApJL, 951, L11

(ref: 2025arXiv250816534A) Agarwal, N., Agazie, G., Anumarlapudi, A., et al. 2025, arXiv e-prints, arXiv:2508.16534

(ref: agazie/etal:2023a) Agazie, G., Anumarlapudi, A., Archibald, A. M., et al. 2023a, ApJL, 951, L8

(ref: agazie/etal:2023b) Agazie, G., Anumarlapudi, A., Archibald, A. M., et al. 2023b, ApJL, 951, L50

(ref: 2023ApJ...952L..37A) Agazie, G., Anumarlapudi, A., Archibald, A. M., et al. 2023c, ApJL, 952, L37

(ref: TaoAn2013) An, T., Baan, W. A., Wang, J.-Y., Wang, Y., & Hong, X.-Y. 2013, MNRAS, 434, 3487

(ref: 2015ApJ...812...72A) Antonini, F., Barausse, E., & Silk, J. 2015, ApJ, 812, 72

(ref: software:astropy/a) Astropy Collaboration. 2013, A&A, 558, A33

(ref: software:astropy/b) Astropy Collaboration. 2018, AJ, 156, 123

(ref: software:astropy/c) Astropy Collaboration. 2022, ApJ, 935, 167

(ref: Avara:2023ztw) Avara, M. J., Krolik, J. H., Campanelli, M., et al. 2024, Astrophys. J., 974, 242

(ref: 1982Natur.300..615B) Backer, D. C., Kulkarni, S. R., Heiles, C., Davis, M. M., & Goss, W. M. 1982, Nature, 300, 615

(ref: benson/etal:2014) Benson, B. A., Ade, P. A. R., Ahmed, Z., et al. 2014, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9153, Millimeter, Submillimeter, and Far-Infrared Detectors and Instrumentation for Astronomy VII, ed. W. S. Holland & J. Zmuidzinas, 91531P

(ref: Blandford2019) Blandford, R., Meier, D., & Readhead, A. 2019, ARA&A, 57, 467

(ref: blandford/konigl:1979) Blandford, R. D. & Königl, A. 1979, ApJ, 232, 34

(ref: 2021PhRvD.103j3529B) Boileau, G., Christensen, N., Meyer, R., & Cornish, N. J. 2021, Phys. Rev. D, 103, 103529

(ref: 1990NCimB.105.1141B) Braginsky, V. B., Kardashev, N. S., Polnarev, A. G., & Novikov, I. D. 1990, Nuovo Cimento B Serie, 105, 1141

(ref: carlstrom/etal:2011) Carlstrom, J. E., Ade, P. A. R., Aird, K. A., et al. 2011, PASP, 123, 568

(ref: ccat:2023) CCAT-Prime Collaboration, Aravena, M., Austermann, J. E., et al. 2023, ApJS, 264, 7

(ref: Cho:2023wqr) Cho, H., Prather, B. S., Narayan, R., et al. 2023, Astrophys. J. Lett., 959, L22

(ref: choi/etal:2020) Choi, S. K., Hasselfield, M., Ho, S.-P. P., et al. 2020, JCAP, 2020, 045

(ref: coulton/etal:2024) Coulton, W., Madhavacheril, M. S., Duivenvoorden, A. J., et al. 2024, Phys. Rev. D, 109, 063530

(ref: Davis:2020wea) Davis, S. W. & Tchekhovskoy, A. 2020, Ann. Rev. Astron. Astrophys., 58, 407

(ref: delaparra/etal:2025) de la Parra, P. V., Kiehlmann, S., Mróz, P., et al. 2025, ApJ, 987, 191

(ref: drake2009) Drake, A. J., Djorgovski, S. G., Mahabal, A., et al. 2009, ApJ, 696, 870

(ref: drinkwater/etal:1997) Drinkwater, M. J., Webster, R. L., Francis, P. J., et al. 1997, MNRAS, 284, 85

(ref: 2013MNRAS.433..907E) Emmanoulopoulos, D., McHardy, I. M., & Papadakis, I. E. 2013, MNRAS, 433, 907

(ref: Ennoggi:2025nht) Ennoggi, L., Campanelli, M., Zlochower, Y., et al. 2025, Phys. Rev. D, 112, 063009

(ref: epta:2023) EPTA Collaboration. 2023, A&A, 678, A50

(ref: farren/etal:2021) Farren, G. S., Partridge, B., Kneissl, R., et al. 2021, ApJS, 256, 19

(ref: Farris:2012ux) Farris, B. D., Gold, R., Paschalidis, V., Etienne, Z. B., & Shapiro, S. L. 2012, Phys. Rev. Lett., 109, 221102

(ref: foreman_mackey_2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013a, PASP, 125, 306

(ref: foreman-mackey/etal:2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013b, PASP, 125, 306

(ref: Galishnikova:2024nsk) Galishnikova, A., Philippov, A., Quataert, E., Chatterjee, K., & Liska, M. 2025, Astrophys. J., 978, 148

(ref: Gold:2013zma) Gold, R., Paschalidis, V., Etienne, Z. B., Shapiro, S. L., & Pfeiffer, H. P. 2014, Phys. Rev. D, 89, 064060

(ref: 2015Natur.518...74G) Graham, M. J., Djorgovski, S. G., Stern, D., et al. 2015, Nature, 518, 74

(ref: graham2019) Graham, M. J., Kulkarni, S. R., Bellm, E. C., et al. 2019, PASP, 131, 078001

(ref: Guo:2024gqc) Guo, M., Stone, J. M., Quataert, E., & Springel, V. 2025a, ApJ, 987, 202

(ref: Guo:2025sjb) Guo, M., Stone, J. M., Quataert, E., & Springel, V. 2025b, ApJ, 987, 202

(ref: software:numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: henderson/etal:2016) Henderson, S. W., Allison, R., Austermann, J., et al. 2016, Journal of Low Temperature Physics, 184, 772

(ref: hervias-caimapo/etal:2024) Hervı́as-Caimapo, C., Naess, S., Hincks, A. D., et al. 2024, MNRAS, 529, 3020

(ref: huijse/etal:2025) Huijse, P., Davelaar, J., De Ridder, J., Jannsen, N., & Aerts, C. 2025, arXiv e-prints, arXiv:2505.16884

(ref: Ingramreview) Ingram, A. R. & Motta, S. E. 2019, New A Rev., 85, 101524

(ref: kaaz2025extreme) Kaaz, N., Lithwick, Y., Liska, M., & Tchekhovskoy, A. 2025, The Astrophysical Journal, 979, 192

(ref: 2023ascl.soft10002K) Kiehlmann, S. 2023, lcsim: Light curve simulation code, Astrophysics Source Code Library, record ascl:2310.002

(ref: 2025ApJ...985...59K) Kiehlmann, S., de la Parra, P. V., Sullivan, A. G., et al. 2025, ApJ, 985, 59

(ref: 2000AmJPh..68..489K) Krolik, J. H. & Di Matteo, T. 2000, American Journal of Physics, 68, 489

(ref: lagache/etal:2020) Lagache, G., Béthermin, M., Montier, L., Serra, P., & Tucci, M. 2020, A&A, 642, A232

(ref: lalakos2024jets) Lalakos, A., Tchekhovskoy, A., Bromberg, O., et al. 2024, The Astrophysical Journal, 964, 79

(ref: lalakos2025universal) Lalakos, A., Tchekhovskoy, A., Most, E. R., et al. 2025, arXiv preprint arXiv:2505.23888

(ref: lense1918einfluss) Lense, J. & Thirring, H. 1918, Physikalische zeitschrift, 19, 156

(ref: liska2018formation) Liska, M., Hesp, C., Tchekhovskoy, A., et al. 2018, Monthly Notices of the Royal Astronomical Society: Letters, 474, L81

(ref: 1976Ap&SS..39..447L) Lomb, N. R. 1976, Ap&SS, 39, 447

(ref: madhavacheril/etal:2020) Madhavacheril, M. S., Hill, J. C., Næss, S., et al. 2020, Phys. Rev. D, 102, 023534

(ref: Manikantan:2024giq) Manikantan, V., Paschalidis, V., & Bozzola, G. 2025, Astrophys. J. Lett., 984, L47

(ref: marriage/etal:2011) Marriage, T. A., Baptiste Juin, J., Lin, Y.-T., et al. 2011, ApJ, 731, 100

(ref: masci2019) Masci, F. J., Laher, R. R., Rusholme, B., et al. 2019, PASP, 131, 018003

(ref: Maxmoerbeck2014) Max-Moerbeck, W., Richards, J. L., Hovatta, T., et al. 2014, MNRAS, 445, 437

(ref: miles/etal:2025) Miles, M. T., Shannon, R. M., Reardon, D. J., et al. 2025, MNRAS, 536, 1489

(ref: 2003ApJ...596..860M) Milosavljević, M. & Merritt, D. 2003, ApJ, 596, 860

(ref: 2017PhRvL.119z1102M) Moore, C. J., Mihaylov, D. P., Lasenby, A., & Gilmore, G. 2017, , 119, 261102

(ref: naess/etal:2025) Naess, S., Guan, Y., Duivenvoorden, A. J., et al. 2025, arXiv e-prints, arXiv:2503.14451

(ref: 2003PASJ...55L..69N) Narayan, R., Igumenshchev, I. V., & Abramowicz, M. A. 2003, PASJ, 55, L69

(ref: 2020MNRAS.497..739N) Nasim, I., Gualandris, A., Read, J., et al. 2020, MNRAS, 497, 739

(ref: niemack:2008) Niemack, M. D. 2008, PhD thesis, Princeton University, New Jersey

(ref: nixon2013tearing) Nixon, C., King, A., & Price, D. 2013, Monthly Notices of the Royal Astronomical Society, 434, 1946

(ref: travis/etal:2014) O’Brien, T. A., Collins, W. D., Rauscher, S. A., & Ringler, T. D. 2014, Computational Statistics & Data Analysis, 79, 222

(ref: travis/etal:2016) O’Brien, T. A., Kashinath, K., Cavanaugh, N. R., Collins, W. D., & O’Brien, J. P. 2016, Computational Statistics & Data Analysis, 101, 148

(ref: 2022ApJ...926L..35O) O’Neill, S., Kiehlmann, S., Readhead, A. C. S., et al. 2022, ApJL, 926, L35

(ref: paliya/etal:2017) Paliya, V. S., Marcotulli, L., Ajello, M., et al. 2017, ApJ, 851, 33

(ref: 2018A&A...615A.123Q) Qian, S. J., Britzen, S., Witzel, A., Krichbaum, T. P., & Kun, E. 2018, A&A, 615, A123

(ref: 1980IAUS...92..165R) Readhead, A. C. S. 1980, in Objects of High Redshift, ed. G. O. Abell & P. J. E. Peebles, Vol. 92, 165–175

(ref: 2024JAHH...27..453R) Readhead, A. C. S. 2024, Journal of Astronomical History and Heritage, 27, 453

(ref: 1978Natur.276..768R) Readhead, A. C. S., Cohen, M. H., Pearson, T. J., & Wilkinson, P. N. 1978, Nature, 276, 768

(ref: 1974MmRAS..78....1R) Readhead, A. C. S. & Hewish, A. 1974, , 78, 1

(ref: ren/etal:2021) Ren, G.-W., Ding, N., Zhang, X., et al. 2021a, MNRAS, 506, 3791

(ref: ren/etal:2025) Ren, G.-W., Sun, M., Ding, N., Yang, X., & Zhang, Z.-X. 2025, MNRAS, 537, 2931

(ref: ren/etal:2021b) Ren, G.-W., Zhang, H.-J., Zhang, X., et al. 2021b, Research in Astronomy and Astrophysics, 21, 075

(ref: Richards2011) Richards, J. L., Max-Moerbeck, W., Pavlidou, V., et al. 2011, ApJS, 194, 29

(ref: 1982ApJ...263..835S) Scargle, J. D. 1982, ApJ, 263, 835

(ref: 2017MNRAS.465..161S) Sobacchi, E., Sormani, M. C., & Stamerra, A. 2017, MNRAS, 465, 161

(ref: swetz/etal:2011) Swetz, D. S., Ade, P. A. R., Amiri, M., et al. 2011, ApJS, 194, 41

(ref: 2011MNRAS.418L..79T) Tchekhovskoy, A., Narayan, R., & McKinney, J. C. 2011, MNRAS, 418, L79

(ref: thornton/etal:2016) Thornton, R. J., Ade, P. A. R., Aiola, S., et al. 2016, ApJS, 227, 21

(ref: software:scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: wang2025galactic) Wang, H.-Y., Guo, M., Most, E. R., Hopkins, P. F., & Lalakos, A. 2025, arXiv preprint arXiv:2504.03874

(ref: wangpvb2014) Wang, J.-Y., An, T., Baan, W. A., & Lu, X.-L. 2014, MNRAS, 443, 58

(ref: 2009A&A...496..577Z) Zechmeister, M. & Kürster, M. 2009, A&A, 496, 577

# ALMA sine-wave fit results

K25 performed sine-wave fits to the OVRO and ALMA data for PKS 2131$-$021 using the same methodology described in Sec. [3.1](#sec:sinfit_method), but only reported the best-fitting phase shifts. For completeness we include all the best-fitting parameters from this analysis in Table [\[tab:alma_2131_fits\]](#tab:alma_2131_fits).

+-------------------------+---------------------+----------------------+----------------------+----------------------+
| Parameter               | OVRO 15 GHz         | ALMA 91.5 GHz        | ALMA 103.5 GHz       | ALMA 345 GHz         |
+:========================+====================:+=====================:+=====================:+=====================:+
| $P$ (days)              | $2003\pm19$ (fixed)                                                                      |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $A$ (Jy)                | $0.4385 \pm 0.0059$ | $0.3170 \pm 0.0066$  | $0.2995 \pm 0.0067$  | $0.1386 \pm 0.0060$  |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\phi_0$ (rad)          | $3.725 \pm 0.016$   | $3.268 \pm 0.027$    | $3.242 \pm 0.028$    | $2.886 \pm 0.054$    |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\bar{S}$ (Jy)          | $2.2022 \pm 0.0045$ | $1.4227 \pm 0.0054$  | $1.3536 \pm 0.0054$  | $0.7194 \pm 0.0044$  |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\xi$ (Jy)              | $0.0696 \pm 0.0035$ | $0.0731 \pm 0.0043$  | $0.0717 \pm 0.0042$  | $0.0466 \pm 0.0044$  |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\Delta\phi_0$ (cycles) | $0$                 | $-0.0727 \pm 0.0050$ | $-0.0769 \pm 0.0052$ | $-0.1336 \pm 0.0090$ |
+-------------------------+---------------------+----------------------+----------------------+----------------------+
| $\Delta\phi_0$ (days)   | $0$                 | $-145.6 \pm 9.9$     | $-154 \pm 10$        | $-268 \pm 18$        |
+-------------------------+---------------------+----------------------+----------------------+----------------------+

Table notes: The period, $P$, was determined from an initial fit including only the OVRO data in the range $57779 < \mathrm{MJD} < 60053$. The joint fit including OVRO and the three ALMA light curves kept the period fixed at this best fitting value. The fit uncertainties do not account for systematics due to superimposed, shorter term variations (see Appendix [9.1](#app:empirical_estimate_backgnd)). The reference time for the phase, in MJD, is $t_0 = 59\,000$. The phase shift, $\Delta\phi_0$, is defined in Eq. [\[eq:phase_shift\]](#eq:phase_shift).

# Empirical estimates of phase shift uncertainties

## Background

Given the important information about SMBHB jet physics encoded in the phase of the sinusoidal variation of the light curves as a function of frequency, it is important to assess how well we can measure those phase shifts. There are at least two types of uncertainty associated with them. The *absolute error* encodes how uncertain the phase measurement of a light curve is with respect to the true, underlying sinusoid. The *relative error* encodes how uncertain the phase shifts at two different frequencies are with respect to each other, rather than to the true, underlying sinusoid. This is the more relevant uncertainty for probing how the location of the emission zone in the jet varies with frequency. If the light curves consisted of a pure sine wave with white noise, then the absolute and relative errors would be identical. In reality, the noise is correlated within single light curves and between light curves of different frequencies, and so the two types of uncertainty will be different.

Some background on physical origin of the light curves is in order. The radio flux density variations in blazars originate from a number of sites along the jet, but are dominated by the variations in the core, which is unresolved even by very long baseline imaging (VLBI; (cite: Blandford2019)). These variations in blazars are believed to generally follow a power law spectrum (see, e.g., (cite: Maxmoerbeck2014)), so it is to be expected that there will be ongoing, non-sinusoidal variations on both longer and shorter timescales than the sinusoidal variations. When a limited number of sinusoid cycles are measured, the superimposed variations can bias the phase shift. This is evident, for instance, in the 15 GHz OVRO light curve of PKS 2131$-$021 in Fig. [1](#plt:2131). One can see by eye that if the dashed orange curve, representing the best-fit sine wave to the OVRO data during the period when ALMA data are available, were continued half a cycle to the left, such that it extended into ${\sim}$2010–2014, it would not line up perfectly with the data points due to superimposed variations during this time range. Another feature to note in this plot is the fluctuation of the ALMA and ACT data points above the sine curve in the year 2018: one sees the *same* trend at all the mm frequencies (Fig. [2](#plt:J2134_alma-act_corr)), which also appears to be present in the 15 GHz OVRO data earlier, at 2017.5 (Fig. [1](#plt:2131)). In other words, random, non-sinusoidal fluctuations can be coherent across frequency bands. All these variations contribute to the uncertainty of the absolute phase measurement, and will be larger the smaller the number of cycles.

K25 distinguish two important types of variations, which we summarise here. ‘Type-A variations’ are common across different observing frequencies, only shifted by the same amount as the sinusoid phase shift; an example was described at the end of the previous paragraph. ‘Type-B’ variations, on the other hand, are unique at each frequency, or show a different frequency dependence from that of the sinusoid. If the light curves are dominated by Type-A variations, which could arise from variable fuelling of the jet, then the *relative error* of the phase difference between frequencies will be considerably smaller than the absolute error, since all frequencies will have have the same bias in the absolute phase determination; if, on the other hand, they are dominated by Type-B variations, which could be caused by local disturbances along the jet, then the uncertainty of the relative phase difference would be commensurate with the uncertainty of the absolute phase.

Whether Type-A or Type-B variations dominate is an empirical question, and K25 conclude that they cannot make a firm estimate given the lack of a large sample of multi-frequency light curves of SMBHB candidates. Thus, our fitting procedure in Sec. [3.1](#sec:sinfit_method), while it includes a parameter for correlated noise within a single light curve, does not assign any noise covariance between different light curves; they are essentially independent fits, all using the same period that is measured in the OVRO data. As K25 point out, if all of the variations are Type-A, then any bias on the fits will be the same at all frequencies, and the independent fits will provide a good uncertainty estimate.

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| AGN | Freq. | span$^{a}$ | $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}$ | $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}$ |
|  | (GHz) | (days) |  |  |
| PKS 2131$-$021 | 95 | 2084 | 3.4 | 3.8 |
| *period: 1931 d* | 147 | 2197 | 2.5 | 2.9 |
|  | 225 | 1837 | 1.1 | 2.0 |
| PKS J0805$-$0111 | 95 | 1695 | 3.0 | 2.0 |
| *period: 1402 d* | 147 | 1708 | 2.2 | 1.6 |
|  | 225 | 1447 | 1.1 | 1.1 |

: Properties of SMBHB candidate ACT light curves

Table notes: $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}$ is the amplitude of the sine relative to its residuals (Eq. [\[eq:snrsin\]](#eq:snrsin), and $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}$ is the rms of the residuals relative to the average flux uncertainty (Eq. [\[eq:snrvar\]](#eq:snrvar).)\

## Method

(5040.00,5760.00) (0,0)

|                  |       |             |                |            |           |      |
|:----------------:|:-----:|:-----------:|:--------------:|:----------:|:---------:|:----:|
|       AGN        | Freq. | Count$^{a}$ |   Empirical    | Freq. Pair | Empirical | MCMC |
|                  | (GHz) |             | Abs.$^{b}$ (%) | (GHz–GHz)  | Rel. (%)  | (%)  |
|                  |  95   |     31      |      3.1       |   95–147   |    1.2    | 0.59 |
|  PKS 2131$-$021  |  147  |     25      |      4.7       |   95–225   |    2.4    | 1.8  |
|                  |  225  |     21      |      6.0       |  147–225   |    3.9    | 1.8  |
|                  |  95   |     36      |      2.6       |   95–147   |    1.5    | 0.52 |
| PKS J0805$-$0111 |  147  |     37      |      4.5       |   95–225   |    3.1    | 1.5  |
|                  |  225  |     28      |      5.5       |  147–225   |    3.3    | 1.5  |

Table notes: The MCMC error is obtained via the method described in Sec. [3.1](#sec:sinfit_method), and the empirical absolute and empirical relative errors are estimated by injecting known, artificial sine waves into real AGN light curves and measuring how well their phases can be recovered with respect to the input phase (absolute error) and with respect to the best fit in other frequencies (relative error). Note that it is not appropriate to compare the MCMC error directly against the absolute error; see text for details.\

For our ACT light curves, we can make progress on the empirical front using our preliminary catalog of 205 bright AGN multi-frequency light curves (see Sec. [2.1](#sec:actobs)). Under the assumption that the Type-A and Type-B variations affect blazars that are not SMBHB candidates in the same way that they affect the two SMBHB candidates discovered thus far – which we stress is untested – we can estimate the absolute and relative phase shift uncertainties by injecting a sinusoid into the light curves: $$\begin{equation}
\label{eq:sine_injection}
  f'(t) = f(t) + \ensuremath{\mathrm{SNR}_{\mathrm{sin}}}\,\sigma_f\,\sin\left(\frac{2\pi t}{P_0}\right),
\end{equation}$$ where $f$ is the original light curve, $\sigma_f$ is the standard deviation of the original light curve, $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}$ is the signal-to-noise ratio (SNR) of the sinusoid and $P_0$ its period. When we have multiple measurements at the same MJD at the same frequency (i.e., from different arrays), we use their mean value. Note that we have factored the amplitude of the sinusoid into a SNR term ($\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}$) and a noise term ($\sigma_f$) in order to use sine waves of similar SNR as our SMBHB candidates. Table [3](#tab:smbhb_props) shows the SNR of the sinusoids in our SMBHB candidates at each frequency, which we obtained by subtracting the best-fitting sinusoid from the SMBHB candidate, measuring the standard deviation of its residuals, $\sigma_{\mathrm{resid}}$, and calculating: $$\begin{equation}
\label{eq:snrsin}
  \ensuremath{\mathrm{SNR}_{\mathrm{sin}}}= \frac{A}{\sigma_{\mathrm{resid}}}.
\end{equation}$$ where $A$ is the best-fitting amplitude of the sine wave. In the same table, we also list the SNR of the residuals after subtracting the sine wave with respect to the flux uncertainties: $$\begin{equation}
\label{eq:snrvar}
  \ensuremath{\mathrm{SNR}_{\mathrm{var}}}= \frac{\sigma_{\mathrm{resid}}}{\widebar{\sigma}_{\mathrm{f}}}
\end{equation}$$ where $\widebar{\sigma}_{\mathrm{f}}$ is the mean value of the flux uncertainties in the light curve. This variable captures the SNR of the non-sinusoidal residuals.

We estimate the uncertainty in phase measurements by fitting a sinusoid to $f'(t)$, $$\begin{equation}
\label{eq:sin_fit}
  s(t) = A\sin\left[\frac{2\pi(t - t_0)}{P_0}\right] + b,
\end{equation}$$ where $A$, $t_0$ and $b$ are free parameters. A non-zero best-fitting $t_0$ represents an error in recovering the input phase. We carry out this fit on our ensemble light curves (with the SMBHBs excluded from the sample), where the injected light curves have $P_0$ and $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}$ set to the values in Table [3](#tab:smbhb_props). We make two cuts on the ensemble of light curves. First, we require that the time span covered by each light curve be at least 95% that of PKS 2131$-$021 or PKS J0805$-$0111(see Table [3](#tab:smbhb_props)) so that the length of the sine wave being fitted is representative of our SMBHB candidates. Second, we only include light curves which have $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}< 5$, where here, $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}= \sigma / \widebar{\sigma}_{\mathrm{f}}$, with $\sigma$ being the standard deviation of the original light curve. We explain the rationale for this cut in Sec. [9.4](#sec:snr_considerations), below. After both cuts, 10 to 18% of the original 204 light curves remain, depending on the frequency and the AGN being studied (see ‘Count’ in Table [\[tab:act_phase_uncertainty\]](#tab:act_phase_uncertainty)).

With the final ensemble in hand, we use the `curve_fit()` routine in the optimization package of SCIPY to do a non-linear least squares fit to Eq. [\[eq:sin_fit\]](#eq:sin_fit) for each light curve and obtain a distribution of $t_0$ at each of the ACT frequencies. The width of this distribution indicates the absolute error on the phase shift. The width of the distribution of the difference of the recovered fits in the light curves at two frequencies, $\Delta t_{\nu_1,\nu_2} = t_{0,\nu_1} - t_{0,\nu_2}$, indicates the relative error on the phase shifts between frequencies $\nu_1$ and $\nu_2$.

## Results and discussion

The distributions of our phase fits are shown in Fig. [9](#plt:act_phase_uncertainty). We estimate the width of the distribution using the median absolute deviation (MAD) statistic, since it is robust to outliers, and report errors as $\sigma = \mathrm{MAD}/0.6745$, where the numeric factor is the conversion to the Gaussian width for a normal distribution.[^18] These error estimates are listed in Table [\[tab:act_phase_uncertainty\]](#tab:act_phase_uncertainty). There is broad agreement between the scenarios representing the two SMBHB candidates: the absolute uncertainty is about 3%, 5% and 6% of a cycle for 95, 147 and 225 GHz, respectively, and the relative uncertainty between 95 and 147 GHz is roughly 1.5% and is about 2–4% between 95/147 and 225 GHz.

(10080.00,2580.00) (0,0)

The uncertainties from the MCMC fits (Sec. [3.1](#sec:sinfit_method)) are also shown in Table [\[tab:act_phase_uncertainty\]](#tab:act_phase_uncertainty). Here, we have assumed the hypothesis that the SMBHB light curves are dominated by Type-A variations, such that the MCMC uncertainties represent purely *relative errors*, and have added in quadrature the uncertainties in $\phi_0$ provided in Tables [\[tab:2131_fits\]](#tab:2131_fits) and [\[tab:0805_fits\]](#tab:0805_fits) for the three pairs of ACT frequencies. The MCMC uncertainties are ${\sim}$2 times smaller than our empirical estimates. Given our current limited understanding of SMBHB light curve properties, we consider MCMC and empirical relative uncertainties to be in broad agreement. The MCMC uncertainties could be artificially low if Type-B variations are non-negligble. On the other hand, the empirical analysis is based on the assumption that injecting sine waves into non-SMBHB AGN light curves provides an accurate simulation of SMBHB light curves, or, in other words, that Type-A and Type-B variations behave the same way in SMBHB and non-SMBHB AGN. If this assumption is faulty then the resulting errors could be inflated; furthermore, the sample size is rather small. For these reasons, the MCMC uncertainties may well be appropriate for SMBHBs, and that they appear to be reasonable given the fit of the simple quadratic curve in Fig. [4](#plt:2131_phases). In the end, the main results of this paper are not sensitive to the exact size of the error bars, but the work in this Appendix demonstrates the need for more data to better understand the uncertainties in SMBHB sine fits.

## Further tests on phase uncertainty estimates

#### Varying $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}$:

The left panel of Fig. [10](#plt:act_phase_snr) shows the effect on the relative uncertainties of varying the value of $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}$ injected into the ensemble of light curves. Of particular interest is that the 95–225 GHz and 147–225 GHz uncertainties based on the fiducial $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}$ values, taken from our real SMBHB candidate (Table [3](#tab:smbhb_props)), are essentially the same if *no* sine wave is inserted into light curves in our ensemble, i.e., $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}= 0$. This means that our errors relative to the 225 GHz light curves, which only have $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}\approx 1$, are dominated by Type-A variations: it is not so much the phase shift in the sine wave that is being measured as the shift in the Type-A variations. On the other hand, the 95–147 GHz relative uncertainty, where the SMBHB candidate has $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}\approx 2.5{-}3.5$, is significantly smaller than if $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}$ is set to zero. When $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}$ is raised to 3 for light curves at all frequencies, the relative errors between all frequencies is ${\approx}1\%$, and is reduced as $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}$ increases, as expected.

#### Varying $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}$:

The right panel of Fig. [10](#plt:act_phase_snr) explores how well the relative uncertainty can be measured for different $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}$. Our SMBHBs have comparatively small $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}$: at 95 GHz, $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}= 3.8$ and 2.0 for PKS 2131$-$021 and PKS J0805$-$0111, respectively, compared to the median of 9.4 for the 204 other AGN in the ensemble. Effectively, this means that the residuals of the SMBHB candidates exhibit lower variations than are found in the other, non-SMBHB light curves. As the figure shows, when all AGN are used to estimate the relative light curves, the errors relative to 225 GHz are higher than if we perform a cut on $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}$, such that the AGN included in the sample have variations that are more representative of the SMBHB candidates. On the other hand, the 95–147 GHz relative error is not sensitive to any cuts on $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}$. Again, the interpretation is that when $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}\gtrsim 2$, the sine wave is larger than the other variations, and thus the relative phase errors are not very sensitive to the non-sinusoidal variations; this is not the case when $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}\sim 1$. With our limited sample, doing a cut for $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}< 3$ at 95 GHz, which would best represent our SMBHB candidates, only leaves 13 AGN in the sample. We therefore opt for a cut on $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}< 5$, which more than doubles the number of available AGN (see the ‘Count’ column in Table [\[tab:act_phase_uncertainty\]](#tab:act_phase_uncertainty)) while not significantly altering the resulting error estimates, as can be seen in Fig. [10](#plt:act_phase_snr). Finally, as a consistency check, for our fiducial cut of $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}< 5$ we also did a test where we set $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}=3$ for all frequencies, and found results similar to the left-hand panel of Fig. [10](#plt:act_phase_snr), where no cut on $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}$ was used. This confirms the point made above, that when $\ensuremath{\mathrm{SNR}_{\mathrm{sin}}}\gtrsim 2$, non-sinusoidal variations do not impact the uncertainty much.

(5040.00,2880.00) (0,0)

#### Including phase shifts in injected sine waves:

An inaccuracy in our empirical error estimates is that we inject sine waves with the same phase at all frequencies. In reality, we know from our two SMBHB candidates that they are slightly phase shifted. To test whether neglecting this effect affects our error estimates, we introduced different relative phase shifts into the injected sine waves and repeated the analysis. As for our fiducial error estimates, we apply a cut of $\ensuremath{\mathrm{SNR}_{\mathrm{var}}}< 5$. Fig. [11](#plt:act_sim-shifts) shows the results for the 95–147 GHz relative uncertainty, and demonstrates that it does have an effect on the error estimate. However, because the measured phase shifts between the ACT frequencies in our SMBHB candidates are smaller than 2%, corresponding to the central points along the $x$-axis in the figure, neglecting this effect in our fiducial results (Table [\[tab:act_phase_uncertainty\]](#tab:act_phase_uncertainty)) only makes a modest difference. The results for the 95–225 GHz and 147–225 GHz uncertainties are considerably noisier but broadly similar.[^19] In future estimates of the phase shift uncertainties, this effect should be taken into consideration.

| Test | Description | Data | GLS period (days) | GLS power | p-value |
|:---|:---|:---|---:|---:|---:|
| 1 | Independent of radio data | CTRS+ZTF | 1711 | 0.22 | 0.937 |
| 2 | Prior knowledge of radio period | CTRS+ZTF |  |  | 0.047 |
| 3 | Prior knowledge of radio period | ZTF |  |  | 0.065 |
| 4 | Prior knowledge of radio period | CRTS |  |  | 0.079 |

Table notes: The GLS peak in the OVRO 15 GHz light curve has power $\mathcal{P}_{\rm peak}\,=\,0.83$, and p-value $=5.3 \times 10^{-5}$ (K25).

# Optical light curve periodicity

We analyzed the joint CRTS V-band and ZTF g-band light curve of PKS 2131$-$021 with the generalized Lomb-Scargle (GLS) periodogram (cite: 1976Ap&SS..39..447L; 1982ApJ...263..835S; 2009A&A...496..577Z). The strongest peak in the periodogram is at a period of 1711 days and a power of 0.22 (normalized between 0 and 1, where 1 would imply a perfect sine fit). The period is within the 3$\sigma$ range, 1657.5–1854.1 days, of the periodicity detected in the OVRO 15 GHz data as reported in Table 1 of K25. The low GLS peak power is a result of the strong red-noise component in the data. We estimate[^20] a power-law index of $\beta_\mathrm{opt} = 1.5$ of the red-noise power spectral density (PSD $\sim \nu^{-\beta}$, where $\nu$ is the temporal frequency). Compared to the 15 GHz radio light curve with a PSD index $\beta_\mathrm{radio} = 1.8$ (O22), the optical PSD is flatter, implying stronger variability on short time scales.

GLS analysis of the joint CRTS and ZTF g-band data gives a period of 1711 days and a power of 0.22. ZTF alone gives a period of 1728 days and a power of 0.23 whereas CRTS alone does not identify a period consistent with the radio period. In fact, the strongest peaks in the CRTS periodogram come from the sampling window associated with the CRTS observing cadence. The effect of the CRTS cadence can be demonstrated by downsampling the ZTF data (median $\Delta t = 3$ days) to the CRTS cadence (median $\Delta  t = 15$ days): a joint analysis gives a period of 1724 days and a power of 0.36 but the false alarm probability (FAP) from bootstrap analysis shows the result is no longer significant. Although the FAP is not relevant for assessing the statistical significance of any peak against a correlated noise background, it can be used to assess the effect of cadence on a signal. In this case, the shorter cadence of ZTF data improves the statistical detectability of a signal in the joint data to a significant level, with a p-value of 0.002, as compared to a p-value of 0.414 for joint data with the same median cadence.

We perform different four tests to evaluate the feasibility of using optical data to robustly detect sinusoidal variations in PKS 2131$-$021.

#### Test 1:

We use the procedure described in Appendix A of O22 to estimate the significance of the detected periodicity. Our null hypothesis is that the detected periodicity is a spurious result of a pure red-noise stochastic process. We simulate 20 000 artificial light curves that have the same PSD, probability distribution function, time sampling and observational noise characteristics as the optical light curve. We use the `lcsim` python package (cite: 2023ascl.soft10002K) based on the algorithm of (cite: 2013MNRAS.433..907E). For the original data and each simulation we calculate the GLS periodogram, identify the strongest peak, and use the remaining simulations to estimate the probability that the red-noise process produces a power at least as strong as detected at the peak frequency. This probability is used as test statistic in the next analysis step. Among all simulations we count those that have a test statistic at least as low as that derived from the original light curve, which gives us the *global p-value*. This global p-value takes into account that spurious periodic signals may occur at any frequency in the frequency range tested by the GLS periodogram. We refer to Appendices A in O22 and D25 for a detailed description of the procedure. We find a global p-value of 0.937. Therefore, we cannot reject the null hypothesis of a red-noise process producing a spurious periodicity.

#### Test 2:

When we take our prior knowledge of the strongly significant radio periodicity (p-value $= 5.3 \times 10^{-7}$; K25) into account, we can ask the following question: How likely is it that the red-noise process produces a GLS peak at least as strong as observed in the optical data with a period in the $3\sigma$ range of the radio period (1657.5–1854.1 days, K25)? Among the 20 000 simulations we count 934 that fulfill these criteria, corresponding to a p-value of 0.047. Even with the optical period falling close to the radio period, we cannot confidently rule out the red-noise hypothesis.

Stronger support for the true existence of a period in the optical data consistent with the period seen in the radio data comes from the fact of how well the phase of the optical periodicity ties into the phase-frequency relation discussed in K25.

#### Tests 3 and 4:

We also analysed the CRTS and ZTF data independently. The GLS periodogram of the ZTF data shows the strongest peak at a period of 1728 days. The periodogram of the CRTS also shows a peak near the radio periodicity. However, there are several other spurious peaks that do not correspond to significant detections. Using the same approach as for Test 2 above on the individual light curves, in Table [\[tab:periodicityanalysis\]](#tab:periodicityanalysis) we see that the combined CRTS+ZTF light curve provides the most evidence against the null hypothesis. This is expected as the joint data cover more cycles of the long time-scale periodicity, hidden in the red-noise component, that produces strong variability on shorter time-scales.

The foregoing analyses demonstrates that it can be more complicated to detect a periodicity in optical blazar light curves from current surveys, since the short-term variability is stronger than at radio-submm frequencies. Thus more extended long-term observations with higher cadence are needed to reveal periodicities in the presence of the red-noise component

[^1]: There were two crucial steps in the discovery of millisecond pulsars: (i) the discovery of interplanetary scintillation, at Galactic latitude $-0.3^\circ$, in 4C 21.53 by (cite: 1974MmRAS..78....1R) (see (cite: 2024JAHH...27..453R)), which drew attention to the singular nature of this object; and (ii) the discovery of millisecond pulses from 4C 21.53W by (cite: 1982Natur.300..615B).

[^2]: For f150 we have given the mean excluding PA1, since that array was removed before the light curves in this paper begin. With PA1 included the mean band centre of f150 is 146.9 GHz.

[^3]: The 147 GHz data from PA4 are lacking the final, *Planck*-based correction due to issues with the ACT power spectra for these data (cite: naess/etal:2025). Since these corrections for other frequency-arrays are on the order of a few percent, comparable to our uncertainty (see below), this should not noticeably affect our results in this paper.

[^4]: For details, see the documentation for the `matched_filter_constcorr_dual()` method in the `pixell` package: <https://github.com/simonsobs/pixell>.

[^5]: <https://almascience.eso.org/alma-data/calibrator-catalogue>

[^6]: This AGN is well known in the literature as PKS J2134$-$0153, but we use the identifier PKS 2131$-$021 to be in continuity with O22 and K25.

[^7]: In principle, the ACT band centre should also be colour-corrected, since we have adopted the band centre for synchrotron emission, i.e., an index of $-0.7$ (see Sec. [2.1](#sec:actobs)). However, the difference is subdominant to other uncertainties, particularly the ${\approx}3\%$ scatter in band centre from detector array to detector array, and we ignore it in this analysis.

[^8]: We have converted the values they report, which are in units of days, to units of cycles using their radio period of $1760\pm33$ days.

[^9]: Including the infrared and optical frequencies result in a poor fit, so we omit them. This is not necessarily surprising: the emission is likely to be more complicated at these higher frequencies, which originate close to the central engine, thus affecting the scaling of the phase shifts.

[^10]: The 225 GHz channel has more noise due to the larger atmospheric contamination it suffers, and also has lower fluxes due to the falling synchrotron spectrum. It will therefore not be as important a channel for SMBHB detection. Nonetheless, for our SMBHB candidates, its SNR of $\approx 1$ (Table [\[tab:act_phase_uncertainty\]](#tab:act_phase_uncertainty)), will still allow 225 GHz data to be used to study phase shifts and spectra.

[^11]: See the NASA/IPAC Extragalactic Database (NED).

[^12]: While AGN can be observed in daylight in the mm, it is still the case that mid-latitude CMB surveys will have observing gaps for most AGNs for part of the year—about one month for SO—due to Sun- and Moon-avoidance in their observation strategies (cite: so_collaboration:2025).

[^13]: Though see footnote [12](#fn:sun_avoidance).

[^14]: The report of 181 SMBHB candidates found in optical *Gaia* data by (cite: huijse/etal:2025) ((cite: huijse/etal:2025); see Sec. [6](#sec:cmparison)) was posted to the arXiv while this paper was in review; we have not yet followed up these candidates in our data.

[^15]: http://www.astropy.org

[^16]: http://www.gnuplot.info/

[^17]: https://github.com/simonsobs/pixell

[^18]: The MAD is the distance between the 50th and 75th percentiles (assuming the distribution is symmetric), which for a Gaussian is equal to $\sqrt{2}\,\mathrm{erf}^{-1}\!(\frac{1}{2})\sigma \approx 0.6745\sigma.$

[^19]: The 95–225 GHz result for PKS 2131$-$021 is the noisiest, with the uncertainty estimate varying by a factor of 2.5 for shifts between $-2\%$ and $2\%$.

[^20]: We used this Python package for the power spectral density analysis: <https://github.com/skiehl/psd_analysis>.

</paper>

Write the methods card for this paper.