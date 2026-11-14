# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...960....1L\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...960....1L",
 "title": "A Centiparsec-scale Compact Radio Core in the Nearby Galaxy M60",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Li, Xiaofeng",
 "n_authors": 10,
 "arxiv_id": "2311.06126",
 "doi": "10.3847/1538-4357/ad0be6",
 "alma_projects_linked_by_archive": [
  "2016.1.01135.S",
  "2017.1.00830.S"
 ]
}
```

Paper text:
<paper>
# A centi-pc-scale compact radio core in the nearby galaxy M60

## Abstract

M60, an elliptical galaxy located 16.5 Mpc away, has an active nucleus with a very low luminosity and an extremely low accretion rate. Its central supermassive black hole has a mass of $M_{\rm BH}\sim4.5\times10^{9}\, M_{\odot}$ and a Schwarzschild radii corresponding to $R_{\rm S}\sim5.4\,\mu\mathrm{as}$. To investigate the nature of its innermost radio nucleus, data from the Very Long Baseline Array (VLBA) at 4.4 and 7.6 GHz were reduced. The VLBA images reveal a compact component with total flux densities of $\sim$20 mJy at both frequencies, a size of $\leq$0.27 mas (99.7$\%$ confidence level), about 0.022 pc ($50\,R_{\rm S}$) at 7.6 GHz, and a brightness temperature of $\geq6\times10^{9}$ K. This suggests that the observed centi-parsec-scale compact core could be attributed to a nonthermal jet base or an advection-dominated accretion flow (ADAF) with nonthermal electrons. The extremely compact structure also supports the presence of an SMBH in the center. Our results indicate that M60 is a promising target for broad-band VLBI observations at millimeter wavelengths to probe ADAF scenarios and tightly constrain the potential photon ring (about 28 $\mu$as) around its SMBH.

# Introduction

Spectroscopy and dynamical modeling suggest that supermassive black holes (SMBHs) are usually located in the center of massive galaxies (cite: Gebhardt2000; Kormendy2013). The most powerful evidence for the presence of an SMBH in the center of a galaxy is the detection of the inner radio structure close to the SMBH candidates, e.g., M87 (cite: EHTC2019), Sagittarius A\* (cite: EHTC2022), NGC 4258 (cite: Miyoshi1995). A spectroscopic survey of nearby bright galaxies found that around $40\%$ of them contain low-luminosity active galactic nuclei (LLAGNs) that are powered by SMBHs (cite: Ho1997; Ho2008). Generally, the radiation of most LLAGNs originates from sub-pc-scale or even smaller regions, making it difficult for radio observations to resolve these regions. The radiation mechanism of LLAGNs is not yet well understood.

Radio images of LLAGNs often display a compact core, and some of them also have jet-like structures (cite: Ho2001; Nagar2005). These radio cores remain compact on milliarcsecond scales, as observed through very long baseline interferometry (cite: Ulvestad1999ApJL; Ulvestad2001; Anderson2004; Falcke2000; Nagar2002; Nagar2005; Doi2005; Park2017). A few LLAGN have been resolved on scales of $\leq100$ Schwarzschild radii, $R_{\rm S}$, including Sgr A\* (cite: Shen2005; Lu2018; EHTC2022), M87 (cite: Hada2011; EHTC2019; Lu2023), Cen A (cite: Janssen2021), M104 (cite: Hada2013), M81 (cite: Jiang2018), and M84 (cite: Jiang2021). The radio cores of LLAGNs typically have a flat or slightly inverted spectrum (cite: Ho2001; Nagar2005; Anderson2004; Cho2022). The LLAGN jets usually have subluminal speeds (cite: Ulvestad1999ApJL; Hada2013).

The radio emission of LLAGNs has multiple origins, one of the most common being outflows. These outflows consist of collimated jets (cite: Blandford1977; Falcke1999; Chen2021), accelerated to relativistic velocities (cite: Lister2021) with a very small opening angle (cite: Pushkarev2017), and winds (cite: Blandford1982; Blandford1999) with low brightness, a large opening angle and low velocity (cite: Panessa2019). The jets emit a power law continuum spectrum in the radio band, which is caused by nonthermal synchrotron radiation. Radio winds have the same radiation mechanism as jets, but are much weaker than jets due to low energy and weak magnetic fields. They have only been detected in a few sources, e.g., Markarian 6 (cite: Kharb2006; Kharb2014). Additionally, advection-dominated accretion flows (ADAFs), characterized by geometry thick and optical thin, also emit significant radio flux (cite: Narayan1994; Narayan1995A; Yuan2003). The radio emission from ADAF primarily dominates in the very inner region, making it difficult to study with low-resolution observations (cite: Mahadevan1997; Manmoto1997; Bandyopadhyay2019). Lastly, star formation activity and supernova remnants can also contribute significant radio emission, adding complexity to the study of outflow and ADAF (cite: Panessa2019).

Sgr A\*, the closest known SMBH at a distance D $\sim$8.1 kpc (cite: GRAVITYCollaboration2019), is one of the most promising targets for studying the vicinity of SMBHs in extremely low accretion rate (cite: EHTC2022). Despite extensive VLBI observations, no direct evidence of a jet has been found in Sgr A\* (cite: Rauch2016; EHTC2022; Cho2022; Cheng2023). Interstellar scattering (cite: Bower2006; Psaltis2018) is a major obstacle to detecting potential jets in Sgr A\*. To avoid complications caused by interstellar scattering, we conducted a comprehensive literature review (cite: Kormendy2013; Ramakrishnan2023) and identified M60 as a prime candidate for studying the presence of jets in LLAGNs with very low luminosity and extremely low accretion rates.

M60 (NGC 4649), a nearby elliptical galaxy, has an active nucleus (cite: DiMatteo1997; DiMatteo1999; Paggi2017). Its high Galactic latitude ($b=74.3^\circ$) implies that the interstellar medium (ISM) has a negligible effect on scatter broadening (cite: Koryukova2022). The distance to M60, as estimated by the tip of the red giant branch (TRGB) method, is $d=16.23\pm0.50({\rm ran})\pm0.42({\rm sys})~$Mpc (cite: Lee2017), and the surface brightness fluctuation (SBF) method gives an estimate of $d=16.7\pm0.6~$Mpc (cite: Cantiello2018). In this work, we use the weighted average of the two distances, $d = 16.5\pm0.5~$Mpc. The image scale of M60 is $0.080\pm0.003~{\rm pc\,mas^{-1}}$. The central object, most likely an SMBH, has a dynamic mass of $M_{\rm BH} = (4.5\pm1.0)\times10^{9}~M_{\odot}$ (cite: Shen2010). The central SMBH candidate has an angular size of $R_{\rm S}=2GM_{\rm BH}/(c^{2}d)\sim 5.4~{\rm \mu{}as}$, where $G$ and $c$ are the gravitational constant and the speed of light, respectively. The mass accretion rate of an SMBH $\dot{M}$ is often scaled to Eddington rate $\dot{M}_{\rm Edd}=10L_{\rm Edd}/c^{2}$, i.e., $\dot{m}=\frac{\dot{M}}{\dot{M}_{\rm Edd}}$, where $L_{\rm Edd}$ is the Eddington luminosity[^1]. The scaled mass accretion rate of M60, as reported by (cite: Johannsen2012), is $\dot{m}=1.4\times10^{-8}$ and (cite: Paggi2014) reported a rate of $\dot{m}=7.2\times10^{-9}$. Both of these accretion rates are extremely low. We adopt the arithmetic mean value of these two scaled mass accretion rates, $\dot{m}\sim1.1\times10^{-8}$, for this study. Given the relatively large angular size of $R_{\rm S}$ in M60, this galaxy may provide an excellent opportunity to study the properties of ADAF and jets in LLAGNs with very low mass accretion rates using VLBI observations.

The Very Large Array (cite: Stanger1986; Temi2022; Grossova2022) and Low-Frequency Array (cite: Capetti2022) images of M60 exhibit a typical Fanaroff-Riley type I (cite: Fanaroff1974) radio galaxy morphology on kpc scales, which includes a compact core and double side jets. These jets are also associated with X-ray cavities (cite: Shurkin2008; Dunn2010; Paggi2014). The high-resolution VLA A-configuration images (cite: Temi2022; Grossova2022) or high-frequency images (cite: DiMatteo1999) of M60 only display a compact core. Submillimeter Array (SMA) observations detected significant variability at 223 GHz in M60 in March 2016 (cite: Lo2023). The radio flux density of M60 at 223 GHz varied from not-detection ($\leq8.1$ mJy) on 3 March, increasing to $15.9\pm2.1$ mJy on 5 March, and then decreasing to $6.7\pm1.6$ mJy on 13 March. Infrared observations and dust absorption map suggest that M60 is a cold-gas-free galaxy with no signs of star formation (cite: Temi2022). Thus, it could be an ideal candidate for VLBI observations to investigate outflow or ADAF radio emission properties. Furthermore, VLBI observations could provide more direct evidence for the presence of an accreting SMBH in M60 (cite: Maoz1995; Maoz1998; Genzel2000; Ghez2005; Shen2005) and independently constrain its SMBH mass (cite: Johannsen2010; Johannsen2012).

This paper is structured as follows. In Section [2](#sec:data), we introduce the radio data used, which include high-resolution Very Long Baseline Array (VLBA) data and low-resolution archival radio flux density. Section [3.1](#sec:image) presents the imaging results, and Section [3.2](#sec:radio) discusses the radio origins of the compact component. Section [3.3](#sec:bh) provides independent evidence supporting the presence of an SMBH in M60. Finally, Section [4](#sec:conclusion) summarizes the conclusions.

# Data reduction and analysis

## VLBA observations and data reduction

In the VLBA Calibrator Survey 12 (program code BP252AF, principal investigator: Leonid Petrov), the radio AGN in M60 was observed simultaneously at 4.4 and 7.6 GHz for a duration of 3 min on July 26, 2022. During the experiment, the stations Kitt Peak (`KP`) and North Liberty (`NL`) were out, and the station Pie Town (`PT`) failed to record data. As a result, seven VLBA stations contributed valid data. The experiment was carried out with circular right polarization at a data rate of 4096 Mbps, using 8 subbands (4 at 4.4 GHz and 4 at 7.6 GHz), 128 MHz per subband, and 2-bit quantization. The DiFX2 software correlator (cite: Deller2011) at the National Radio Astronomy Observatory (NRAO) was employed to correlate the data, utilizing a 0.0625-MHz frequency resolution and a 0.1-s integration time.

The correlation data were calibrated in the Astronomical Image Processing System (cite: Greisen2003). After the data were imported into `AIPS`, we corrected the correlation amplitudes due to minor sampling errors, and then ran amplitude calibration based on the system temperature data and antenna gain curves. NRAO recently announced the default antenna gain values of PT and NL at C band (4-8 GHz) between 11 Feb 2020 and 5 April 2023 were incorrect due to incorrect focus. To fix the issue, we used the new gain curve table provided by NRAO [^2]. To align phase across sub-bands, we performed fringe fitting on the 1-min data from the $\sim$1-Jy bright calibrator B1116$+$128. After the manual phase calibration, we merged the subbands in halves (i.e., the 4.4 and 7.6 GHz data are combined, respectively) to enhance the Signal Noise Ratio (SNR) of the solution and conducted global fringe fitting on the data of M60 with 0.75 min solution interval. All the solutions had SNRs greater than 4. Finally, we applied all the solutions to the data, averaged all the frequency channels in each subband, and split the data at 4.4 and 7.6 GHz into two files.

The $(u,v)$ coverage of M60 is shown in Figure [1](#fig:uvcov). The 4.4 and 7.6 GHz data have similar characteristics, with a sparse $(u,v)$ coverage. The maximum side lobe was approximately 72% of the primary lobe.

The radio source M60 is relatively weak (correlation amplitude $\sim$20 mJy). Before running the amplitude self-calibration on the M60 data, we also did a test to verify the reliability of the step. In the same geodetic VLBI experiment, the compact calibrator B1241$+$166 with a total flux density of $\sim$380 mJy at 4.4 GHz was also observed. Because both M60 and B1241$+$166 have a small separation of $4.8^\circ$ and were observed in two neighboring scans, their data were supposed to suffer fairly consistent amplitude errors. We did deconvolution and self-calibration on the data of the pair of sources in `Difmap`. The amplitude self-calibration solutions looked quite similar and were fully as expected. Therefore, it is safe to run the self-calibration of amplitude on the data of M60.

In view of the positive results above, we transferred the amplitude self-calibration solutions from the bright calibrator B1241$+$166 to the nearby target M60 in `AIPS`. The gain correction factors of B1241$+$166, derived from `gscale` command in `Difmap` (cite: Shepherd1997), are reported in Appendix [5](#sec:gain) (Table [\[tab:gain\]](#tab:gain)). We noticed that the gain correction factors of the station LA were abnormally larger than those of other stations. After contacting VLBA support scientists, we figured out that these large correction factors resulted from improper antenna gain measurements.

After calibrating out the large amplitude errors with the nearby bright calibrator B1241$+$166 in `AIPS`, we did deconvolution and self-calibration in `Difmap`. Initially, we fitted the circular Gaussian model to the visibility data and then performed phase self-calibration with a solution interval of 1.5 min. After a few iterations, we started to run the amplitude self-calibration. The amplitude correction factors of M60 were also listed in Appendix [5](#sec:gain) (Table [\[tab:gain\]](#tab:gain)). All the correction factors are quite close to 1, in particular at 4.4 GHz. The `selfcal` command was then run with a solution interval of 3 min, allowing the amplitude and phase to change simultaneously. The model fitting and self-calibration processes were repeated until the reduced chi-square $\chi_{\nu}^{2}$ was minimized. To obtain accurate uncertainty estimates, we scaled the data weights to set $\chi_{\nu}^{2} = 1$. The data at 4.4 and 7.6 GHz were reduced in the same method. We also tried the elliptical Gaussian model. Because some best-fitting parameters, in particular the position angle of the major axis, had large uncertainties, the more complex model was not considered in the paper. The final clean images of M60 at 4.4 and 7.6 GHz are presented in Figure [2](#fig:image).

To accurately characterize the uncertainties of the parameters of the Gaussian model, in particular the angular size, we also used the Markov Chain Monte Carlo (MCMC) method to fit the circular Gaussian mode to the visibility data calibrated in `Difmap`. The used MCMC program `MCMCUVFit` was developed by us. More details of the program are available in Appendix [6](#sec:mcmc). The results of the MCMC method are presented in Table [\[tab:model\]](#tab:model). The calibrated visibility and the model from the MCMC output are shown in the right panels of Figure [2](#fig:image).

We also tried the MCMC and least-square fitting methods to analyze the M60 visibility data using phase-only self-calibration in `Difmap`. The best-fitting parameters show slightly larger uncertainties but are fully consistent with the above results using the phase and amplitude self-calibration.

## Non-simultaneous radio spectrum

To analyze the origin of the radio emission in M60, we collected radio flux density measurements in some online data archives and literature. To exclude possible diffuse emission from the relic jet, we used the measurements from the VLBA data and the VLA data observed with A-configuration at $\leq15$ GHz. At higher frequencies, the contribution of the extended steep spectrum relic jet is quite low and can be ignored. Therefore, we included low-resolution data. The VLBA data are the first VLBI detected flux density that is presented in Appendix [6](#sec:mcmc). Most data extracted from the NRAO VLA Archive Survey (cite: Crossley2008) [^3]. M60 was observed by ALMA at $\sim$350 GHz to study its black hole mass, central parsec gas dynamics, and event horizon detectability by CO lines (program code 2016.1.01135.S and 2017.1.00830.S, Principal Investigator: Neil Nagar). (cite: Temi2022) reported non-detection of the CO lines. We reduced these ALMA data to extract flux densities from the radio continuum spectrum. The data reduction was carried out in Common Astronomy Software Applications (CASA) casa-release-5.1.1 (cite: McMullin2007) with ALMA Pipeline-Cycle5-R2-B (cite: ALMAPipeline). The resulting radio flux density of M60 at 350 GHz is $1.7\pm0.2$ mJy on 18 July 2017 and $1.1\pm0.1$ mJy on 24 December 2017. We also include four published data points: one data point was observed by VLA with A-configuration at 1.5 (cite: Temi2022; Grossova2022), two data points were observed by VLA with D-configuration at 22 and 43 GHz respectively (cite: DiMatteo1999), one data point was observed by submillimetre common-user bolometer array (SCUBA) at 150 GHz (cite: DiMatteo1999). These error bars include systematic errors: 5 percent for the VLBA results and 3 percent for the VLA results. All these flux density measurements are presented in Table [\[tab:flux\]](#tab:flux). There is no hint of strong variability from these non-simultaneous observations, which span approximately four decades, except the SMA data, which is not used.

# Results and discussion

## Radio images of M60

Recently, the Astrogeo Center has precisely determined the location of the radio source in M60. According to the Radio Fundamental Catalog (RFC)[^4], which is available to the public, the coordinates are RA=12:43:39.9715 and Dec=+11:33:09.688 (with an error of 1.8 mas). In Gaia Data Release 3 (DR3), the optical coordinates of M60 are given as RA=12:43:39.9708 (with an error of 6.2 mas) and Dec=+11:33:09.6882 (cite: Gaia2022). The RFC position of M60 is located east of the Gaia DR3 position, with a separation of 9.9 mas. This indicates that the radio position is consistent with the optical position.

The left panels of Figure [2](#fig:image) display the total intensity images of M60 at 4.4 and 7.6 GHz. The peak brightness of the 4.4/7.6 GHz image is $18.58/19.69\,{\rm mJy\,beam^{-1}}$ and the image rms is 0.16/0.17 mJy beam$^{-1}$, respectively. The image scale is $0.08~{\rm pc\,mas^{-1}}$ and the average beam size at 4.4/7.6 GHz is 2.31/1.33 mas. The total flux density at 4.4 and 7.6 GHz is $19.1\pm1.0$ mJy and $20.2\pm1.0$ mJy, respectively, with the error mainly due to the systematic error ($5\%$). The radio component remains unresolved, with an upper limit size of $\leq 0.45$ mas (0.036 pc, or 83 $R_{\rm S}$) at 4.4 GHz, and $\leq$0.27 mas (0.022 pc, or 50 $R_{\rm S}$) at 7.6 GHz at a confidence level of $99.7\%$. These sizes are roughly a fifth of the restore beam. The fitted component sizes at both bands are on centi-pc-scale. The relatively low image sensitivity did not allow us to detect the emission beyond the compact core, and the sub-pc-scale jet might be resolved out or substantially weaker than the image sensitivity can detect.

The VLBA data of M60 suggest a spectral index of $\alpha_{\rm 4.4\,GHz}^{\rm 7.6\,GHz}=0.11\pm0.13$ ($S_{\nu}\propto \nu^{+\alpha}$), implying a slightly inverted spectrum at 4.4-7.6 GHz. Figure [3](#fig:spix) displays the non-simultaneous radio spectrum of M60, which is marginally inverted at $\leq21.6$ GHz with $\alpha_{\rm thick}=0.12\pm0.04$ and steep at $>21.6$ GHz with $\alpha_{\rm thin}=-1.5\pm0.1$ (see Section [3.2.1](#sec:jet)). The brightness temperature of the unresolved component is $T_{\rm B}(4.4{\rm \,GHz})\geq6.0\times10^{9}$ K and $T_{\rm B}(7.6{\rm \,GHz})\geq5.9\times10^{9}$ K, which is much higher than the typical brightness temperature of thermal radiation ($\leq10^5$ K).

The morphology of M60 on both the kpc and centi-pc scales, its slightly inverted radio spectrum, and its extremely high brightness temperature all point to the radio emission being caused by an AGN rather than star formation. This is further supported by the lack of cold gas, which is necessary for star formation, as evidenced by the non-detection of \[C II\] emitting gas with SOFIA, the non-detection of CO line by ALMA, and the absence of dust in the HST dust absorption map (cite: Temi2022).

## Origin of the centi-pc-scale compact component

In the vicinity of LLAGN SMBH, radio emission could be generated by outflows such as jets (cite: Blandford1977; Falcke1999; Chen2021) and winds (cite: Blandford1982; Blandford1999), or an ADAF (cite: Narayan1994; Mahadevan1997; Manmoto1997). However, in the case of M60, no extended jets or winds exceeding $0.85~\mathrm{mJy\,beam^{-1}}$ were detected in the VLBI images. Therefore, we only consider two possible origins: the jet base and the ADAF. Both of these origins have a peaked continuum spectrum in the radio bands. The jet base has an inverted spectrum at low frequency with a spectral index of $0<\alpha\leq2.5$, and a steep spectrum at high frequency (cite: Falcke1999). On the other hand, the ADAF has a similar continuum spectrum but with a spectral index of $\alpha\sim0.4$ at low frequency (cite: Mahadevan1997). A comprehensive analysis of these possibilities is provided in the following sections.

### **Jet base**

The radio continuum spectrum of M60 is shown in Figure [3](#fig:spix). To measure the variability of M60, we employ the variability index $m_{\rm var}=\sigma/<S>$, where $<S>$ and $\sigma$ are the mean and standard deviation of the flux density, respectively. The $m_{\rm var}$ at 1.5 GHz and 4.9 GHz is approximately 7.4% and 11.9%, respectively, indicating a low variability. The radio flux density at 223 GHz detected by SMA showed significant variability during March 2016 (cite: Lo2023), but was not used in the continuum spectrum fitting. The M60 radio spectrum is characterized by a peaked shape, which can be attributed to the synchrotron radiation of jets (cite: Konigl1981; Chen2017). Inverted and steep spectral indexes indicate the optically thick and thin parts, respectively. To fit the radio spectrum of M60, we use a smooth broken power law model proposed by (cite: Callingham2017). The flux density $S_{\nu}$ is given by $$\begin{equation}
\label{eq:ps}
    S_{\nu} = \frac{S_{\rm t}}{1-e^{-1}} \left(1-e^{-(\nu/\nu_{\rm t})^{\alpha_{\rm thin}-\alpha_{\rm thick}}}\right) \left(\frac{\nu}{\nu_{\rm t}}\right)^{\alpha_{\rm thick}}
\end{equation}$$ where $\alpha_{\rm thick}$ and $\alpha_{\rm thin}$ are the spectral indices in the optically thick and optically thin regions, respectively, and $S_{\rm t}$ is the flux density at the turnover frequency $\nu_{\rm t}$. The data used to fit is presented in Table [\[tab:flux\]](#tab:flux), and a variable error 10% ($\sigma_{\rm var}=10\%\times S_{\rm tot}$) was added to the flux density error, i.e., $\sigma=\sqrt{\sigma_{\rm m}^{2}+\sigma_{\rm var}^{2}}$ where $\sigma_{\rm m}$ is the measurement error. The fitting results are $\nu_{\rm t} = 51_{-7}^{+8}$ GHz, $S_{\rm t} = 15_{-1}^{+1}$ mJy, $\alpha_{\rm thick} = 0.12_{-0.04}^{+0.04}$ and $\alpha_{\rm thin} = -1.5_{-0.1}^{+0.1}$. The flux density of the model is plotted with a solid cyan line in Figure [3](#fig:spix) (top left). It is important to note that $\nu_{\rm t}$ is not the peak frequency but the turnover frequency. The peak frequency $\nu_{\rm p}$ and peak flux density $S_{\rm p}$ can be numerically derived from model parameters. By substituting the parameters of the fit into equation [\[eq:ps\]](#eq:ps), we obtain $\nu_{\rm p}\sim21.6~$GHz and $S_{\rm p}\sim21.2~$mJy.

Equation 8 in (cite: Falcke1999) can be used to determine the jet power $Q_{\rm jet}$ and the inclination angle $i$ of the jet in relation to the line of sight. The characteristic electron Lorentz factor of the jet, denoted as $\gamma_{\rm e,0}$, is a free parameter. We set it to $\gamma_{\rm e,0}=230$, which is lower than the median value of 300, to ensure that the simulated jet size is in line with the core size-frequency relation (Figure [3](#fig:spix), bottom). This yields an estimated jet power of $Q_{\rm jet} \sim 5.7\times10^{41}~{\rm erg\,s^{-1}}$ and an inclination angle of $i\sim30^\circ$.

### ADAF

The low luminosity (cite: DiMatteo1997; DiMatteo1999; Paggi2014) and low accretion rate (cite: Johannsen2012; Paggi2014) of M60 suggest that its accretion disk is an ADAF, which exhibits radio emission in the inner disk region. This ADAF model has a peaked spectrum with an inverted spectral index of approximately 0.4 before the peak frequency, which is due to synchrotron cooling, and a steep spectral index after the peak frequency, which is caused by Compton cooling (cite: Manmoto1997; Mahadevan1997). (cite: Mahadevan1997) provided an analytical expression for the ADAF radiation spectrum by a self-similar solution, which can accurately describe the main features of ADAF and can be used to fit the observed data. In this model, the radio emission is generated by synchrotron radiation from thermal electrons.

The parameters used to characterize the ADAF model include the scaled black hole mass $m$, the scaled accretion rate $\dot{m}$, the viscosity parameter $\alpha$, the ratio of gas pressure to total pressure $\beta$, and the fraction of viscous energy transferred to electrons $\delta$. The black hole mass (cite: Shen2010) and accretion rate (cite: Johannsen2012; Paggi2014) were determined by observations and kept constant. The other three parameters $\alpha$, $\beta$, and $\delta$ were allowed to vary in order to fit the radio continuum spectrum of M60. We tried to fit the data with the (cite: Mahadevan1997) model and found that the low-frequency band could not be accurately modeled because the observed spectral index $\alpha_{\rm thick}\sim0.12$ was not consistent with the ADAF model. Therefore, a simple ADAF model with only thermal electrons cannot fully explain the observed radio spectrum of M60.

We included a broken power law (BPL) component in the model to refine the fit of the low-frequency data. This BPL component has the same expression as equation [\[eq:ps\]](#eq:ps), but allows for a negative value for $\alpha_{\rm thick}$, that is, a flat spectrum. The fitting results yielded the following parameters: $\alpha=2.4_{-1.1}^{+1.7}\times10^{-4}$, $\beta=0.96_{-0.03}^{+0.01}$, $\delta=0.61_{-0.30}^{+0.25}$, $\nu_{\rm t}^{\rm BPL}=17.4_{-7.9}^{+8.9}$ GHz, $S_{\rm t}^{\rm BPL}=4.3_{-1.2}^{+1.2}$ mJy, $\alpha_{\rm thick}^{\rm BPL}=-0.13_{-0.13}^{+0.09}$, $\alpha_{\rm thin}^{\rm BPL}=-1.3_{-0.4}^{+0.2}$. The fitting results are shown in Figure [3](#fig:spix) (top right).

The BPL component can be attributed to the synchrotron radiation of nonthermal electrons in the ADAF (cite: Yuan2003; Ozel2000; Bandyopadhyay2019; Cho2022). This further indicates that the core size at lower frequencies is larger than the pure thermal electron model. Moreover, the core size versus frequency relation is more complicated, and no straightforward solution can be derived. Therefore, we have only plotted the core size versus frequency relation for the pure thermal electron model, considering it as a lower bound (Figure [3](#fig:spix) bottom).

## New evidence for the existence of a SMBH in M60

The stellar dynamics (cite: Shen2010) and X-ray hot gas hydrodynamics (cite: Humphrey2008; Paggi2014; Paggi2017) of M60 suggest the presence of a massive dark object at its center. This could be an SMBH or a cluster of brown dwarfs or stellar remnants (cite: Maoz1995; Maoz1998). Here, we present a new argument in favor of the central massive object being an SMBH. Previous studies have demonstrated that if the maximum lifetime of a putative dark cluster is much less than the age of the host galaxy, due to evaporation and physical collision, it could not survive to present (cite: Maoz1995; Maoz1998; Genzel2000; Ghez2005; Shen2005). With a black hole mass of $4.5\times10^{9}\,M_{\odot}$ and a core size at 7.6 GHz of $0.27\,{\rm mas}$, the half mass density of the central object is $\rho_{\rm h} \geq 5.4\times10^{13}\,M_{\rm \odot}{\rm \,pc^{-3}}$. If the central object is a dark cluster, its lifetime would be $\tau \leq 8.4\times10^{9}\,{\rm yr}$, which is less than the lifetime of the host galaxy, $\sim10^{10}\,{\rm yr}$ (see Figure [4](#fig:tau) and the detailed calculation method presented in Appendix [7](#sec:lifetime)). Therefore, it is more likely that the centi-pc-scale radio core in M60 is associated with an SMBH.

Johannsen et al. (2010) proposed a method to estimate the mass of SMBH by imaging its compact radio structure with VLBI. They showed that the photons emitted around the SMBH form a ring-like structure, its diameter is determined by the mass of the SMBH ($d_{\rm ring}=5.2\, R_{\rm S}$) and are not significantly affected by the spin of the SMBH, the angle of inclination, or the observation frequency. Thus, the mass of the SMBH can be estimated by the size of the associated compact radio source. Taking the core size of M60 at 7.6 GHz ($\theta_{\rm size}\leq0.27\,{\rm mas}$) as the upper limit of the photon ring diameter, an upper limit for the SMBH mass can be derived: $M_{\rm BH} \leq 4.3\times10^{10}\, M_{\rm \odot}$. This independent derived upper limit for the black hole mass is consistent with the mass determined by stellar dynamics ($(4.5\pm1.0)\times10^{9}~M_{\odot}$, Shen et al. 2010) and the mass estimated from X-ray hot gas hydrodynamics ($(5.1\pm0.9)\times10^{9}~M_{\odot}$, Humphrey et al. 2008, Paggi et al. 2014, 2017).

# Conclusions

We presented high-resolution VLBA observations conducted in snapshot mode at 4.4 and 7.6 GHz, alongside radio flux density data that include low-resolution data. The resulting VLBA image revealed compact components with a flux density of $19.1\pm1.0$ mJy at 4.4 GHz and $20.2\pm1.0$ mJy at 7.6 GHz. The size of the components, estimated by MCMC fitting, was $\leq83 R_{\rm S}=0.036\,\mathrm{pc}=0.45\,$mas at 4.4 GHz and $\leq50 R_{\rm S}=0.022\,\mathrm{pc}=0.27~$mas at 7.6 GHz. The brightness temperature of the compact components in both bands was $T_{\rm B}\geq6\times10^{9}$ K. The multiband radio flux density of M60 displayed a peaked spectrum. These results enable us to confidently identify the compact component as the radio core of M60. The radio core detected by VLBA within M60 could be due to synchrotron radiation of nonthermal electrons in the jet base, or it could also be attributed to synchrotron radiation generated by a combination of thermal and nonthermal electrons present within ADAF. The high mass density ($\rho_{\rm h} \geq 5.4\times10^{13}\,{\rm M_{\odot}\,pc^{-3}}$) suggests that the central object is an SMBH rather than a dark cluster. The black hole mass was restricted to $M_{\rm BH}\leq 4.3\times10^{10}\,M_{\odot}$, which is in agreement with the dynamical mass.

Our findings indicate that M60 could be a promising object for further deep VLBI observations at $\geq$15 GHz. This would enable us to accurately determine the diameter of the potential photon ring and the mass of its SMBH, as well as to investigate the jet base and ADAF in M60. We have been granted permission for 16-Gbps observations on M60 at 22 and 43 GHz using the Korean VLBI Network (KVN) and some stations in the European VLBI Network (EVN). This project is scheduled to be observed in the near future.

This work is supported by the National Natural Science Foundation of China (No.12203014). X.-P. Cheng was supported by Brain Pool Program through the National Research Foundation of Korea (NRF) funded by the Ministry of Science and ICT (2019H1D3A1A01102564). We thank Feng Wang, Ying Mei, and Hui Deng for their insightful discussions during the initial stages of our work. This research has made use of the NASA/IPAC Extragalactic Database (NED), which is operated by the Jet Propulsion Laboratory, California Institute of Technology, under contract with the National Aeronautics and Space Administration. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01135.S and ADS/JAO.ALMA#2017.1.00830.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# Facilities

VLBA (NRAO), VLA (NRAO), ALMA.

# Software

AIPS (cite: Greisen2003), CASA (cite: McMullin2007), Difmap (cite: Shepherd1997), DiFX (cite: Deller2011), MCMCUVFit, Astropy (cite: Astropy2018).

![image](uvplot4GHz.pdf) ![image](uvplot7GHz.pdf)\

![image](image4GHz.pdf) ![image](radplot4GHz.pdf)\
![image](image7GHz.pdf) ![image](radplot7GHz.pdf)

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| $\nu$ | Beam | $S_{\rm p}$ | rms | $S_{\rm tot}$ | $\theta_{\rm core}$ | $x$ | $y$ |
| (GHz) | (mas$\times$mas, $^\circ$) | (${\rm mJy\,beam^{-1}}$) | ($\mathbf{\rm mJy\,beam^{-1}}$) | (mJy) | (mas/$R_{\rm S}$) | (mas) | (mas) |
| 4.4 | 3.65$\times$1.46, 4.69 | 18.58 | 0.16 | $19.1\pm1.0$ | $\leq0.45/\leq83$ | $0.008_{-0.006}^{+0.006}$ | $0.015_{-0.015}^{+0.015}$ |
| 7.6 | 2.11$\times$0.84, 7.99 | 19.69 | 0.17 | $20.2\pm1.0$ | $\leq 0.27/\leq50$ | $0.007_{-0.004}^{+0.004}$ | $0.008_{-0.009}^{+0.009}$ |

: VLBI results of M60 at C band

Table notes: Column 1: Observation frequency in GHz; Column 2: Restore bean shape (Major axis and Minor axis in mas, Position angle in degree); Column 3: Peak flux density in ${\rm mJy\,beam^{-1}}$; Column 4: Image rms in $\rm mJy\,beam^{-1}$; Column 5: Total flux density in mJy; Columns 6: Core size in mas or $R_{\rm S}$ with 99.7% confidence; Column 7 & 8: Position relative to image center in mas.

|           |            |       |              |           |
|:---------:|:----------:|:-----:|:------------:|:---------:|
| Telescope |   Epoch    | $\nu$ |  $S_{\nu}$   | Reference |
|           |  (Y-M-D)   | (GHz) |    (mJy)     |           |
|   VLA/A   | 1982-04-04 |  1.5  | 16.7$\pm$0.5 |   NVAS    |
|   VLA/A   | 1982-04-04 |  4.9  | 15.5$\pm$0.5 |   NVAS    |
|   VLA/A   | 1982-04-04 |  15   | 17.7$\pm$0.5 |   NVAS    |
|   VLA/A   | 1984-12-15 |  4.9  | 19.7$\pm$0.6 |   NVAS    |
|   VLA/A   | 1991-08-25 |  1.5  | 14.4$\pm$0.4 | T22, G22  |
|   VLA/D   | 1997-12-07 |  22   | 23.5$\pm$0.7 |    D99    |
|   VLA/D   | 1997-12-07 |  43   | 12.9$\pm$0.4 |    D99    |
|   SCUBA   | 1998-01-30 |  150  |  $\leq$5.1   |    D99    |
|   VLA/C   | 1998-12-30 |  22   | 22.3$\pm$0.7 |   NVAS    |
|   VLA/C   | 1998-12-30 |  43   | 21.3$\pm$0.6 |   NVAS    |
|   ALMA    | 2017-07-18 |  350  | 1.7$\pm$0.2  | This work |
|   ALMA    | 2017-12-24 |  350  | 1.1$\pm$0.1  | This work |
|   VLBA    | 2022-07-26 |  4.4  | 19.1$\pm$1.0 | This work |
|   VLBA    | 2022-07-26 |  7.6  | 20.2$\pm$1.0 | This work |

: Radio flux density for continuum spectrum fitting

Table notes: Column 1: Telescope; Column 2: Epoch; column 3: Observation frequency in GHz; Column 4: flux density in mJy; Column 5: Reference. NVAS: (cite: Crossley2008), T22: (cite: Temi2022), G22: (cite: Grossova2022), D99: (cite: DiMatteo1999).

![image](spix_ps.pdf) ![image](spix_adaf_ps.pdf)\
![image](size_vs_freq.pdf)

![](tau.pdf)

# Gain correction factors for amplitude self-calibration

+-------+-------+-------+-------+-------+-------+-------+-------+---------+---------+---------+---------+---------+---------+---------+---------+
| IF    | BR    | FD    | HN    | LA    | MK    | OV    | SC    | IF      | BR      | FD      | HN      | LA      | MK      | OV      | SC      |
+:=====:+:=====:+:=====:+:=====:+:=====:+:=====:+:=====:+:=====:+:=======:+:=======:+:=======:+:=======:+:=======:+:=======:+:=======:+:=======:+
| 1241+166 at 4.4 GHz                                           | M60 at 4.4 GHz                                                                |
+-------+-------+-------+-------+-------+-------+-------+-------+---------+---------+---------+---------+---------+---------+---------+---------+
| 1     | 1.04  | 1.03  | 0.94  | 1.30  | 0.88  | 0.88  | 1.00  | 1       | 0.96    | 0.97    | 1.01    | 1.02    | 1.01    | 1.04    | 1.04    |
+-------+-------+-------+-------+-------+-------+-------+-------+---------+---------+---------+---------+---------+---------+---------+---------+
| 2     | 0.85  | 0.98  | 0.96  | 1.25  | 0.92  | 0.97  | 1.03  | 2       | 1.01    | 0.97    | 0.99    | 0.98    | 0.98    | 1.03    | 1.01    |
+-------+-------+-------+-------+-------+-------+-------+-------+---------+---------+---------+---------+---------+---------+---------+---------+
| 3     | 0.92  | 0.88  | 0.94  | 1.22  | 0.84  | 0.93  | 1.09  | 3       | 0.98    | 0.95    | 1.02    | 1.01    | 0.98    | 1.02    | 0.98    |
+-------+-------+-------+-------+-------+-------+-------+-------+---------+---------+---------+---------+---------+---------+---------+---------+
| 4     | 1.00  | 0.86  | 0.86  | 1.11  | 0.79  | 0.93  | 0.99  | 4       | 1.03    | 1.02    | 0.95    | 1.05    | 0.97    | 1.03    | 0.90    |
+-------+-------+-------+-------+-------+-------+-------+-------+---------+---------+---------+---------+---------+---------+---------+---------+
| 1241+166 at 7.6 GHz                                           | M60 at 7.6 GHz                                                                |
+-------+-------+-------+-------+-------+-------+-------+-------+---------+---------+---------+---------+---------+---------+---------+---------+
| 1     | 1.04  | 0.87  | 1.03  | 0.90  | 0.96  | 1.12  | 1.03  | 1       | 0.99    | 0.98    | 1.04    | 1.00    | 1.04    | 1.03    | 0.90    |
+-------+-------+-------+-------+-------+-------+-------+-------+---------+---------+---------+---------+---------+---------+---------+---------+
| 2     | 0.97  | 0.91  | 1.10  | 0.96  | 0.99  | 0.99  | 0.99  | 2       | 1.02    | 0.99    | 1.10    | 0.90    | 1.02    | 0.99    | 1.05    |
+-------+-------+-------+-------+-------+-------+-------+-------+---------+---------+---------+---------+---------+---------+---------+---------+
| 3     | 1.03  | 1.06  | 0.93  | 0.91  | 0.84  | 0.96  | 1.09  | 3       | 0.97    | 0.97    | 0.92    | 1.06    | 1.02    | 0.97    | 1.00    |
+-------+-------+-------+-------+-------+-------+-------+-------+---------+---------+---------+---------+---------+---------+---------+---------+
| 4     | 1.04  | 0.94  | 1.04  | 0.92  | 0.99  | 1.07  | 0.93  | 4       | 1.01    | 1.01    | 1.02    | 1.04    | 0.93    | 1.01    | 1.03    |
+-------+-------+-------+-------+-------+-------+-------+-------+---------+---------+---------+---------+---------+---------+---------+---------+

: Gain correction factors of amplitude calibrator 1241+166 and target source M60

# MCMC fitting

To derive the total flux density ($S_{\rm tot}$), core size ($\theta_{\rm core}$), and relative position ($x, y$) of M60, we fitted the calibrated visibility data using the MCMC method, as recommended by (cite: Salafia2022). The logarithmic likelihood equation used in the fitting is: $$\begin{eqnarray}
    \ln L(x) =-\frac{1}{2}\Sigma_{i=0}^{N} w_{i}[(V_{R,\,m}(u_{i},\,v_{i},\,\theta)-V_{R,\,i})^{2} +(V_{I,\,m}(u_{i},\,v_{i},\theta)-V_{I,i})^2]
\end{eqnarray}$$ where $V_{R,\,i}$ and $V_{I,\,i}$ represent the real and imaginary parts of the $i$’th visibility at the position $(u_{i},\,v_{i})$, and $w_{i}$ is data weight. $V_{R,\,m}(u,\,v,\,\theta)$ and $V_{I,\,m}(u,\,v,\,\theta)$ are the real and imaginary parts of the model visibility, where $\theta=(S_{\rm tot},\,\theta_{\rm core},\,x,\,y)$ are parameters to be estimated. The model visibility function is defined as: $$\begin{equation}
    V_{\rm m} = S_{\rm tot} \exp{\left[-2\pi^{2}\left(\frac{\theta_{\rm core}}{\sqrt{8\ln 2}}\right)^{2}(u^{2}+v^{2})-2\pi i (ux+vy)\right]}
\end{equation}$$ where $i=\sqrt{-1}$.

The MCMC fitting was executed using MCMCUVFit, a Python-based software specifically designed for fitting visibility data using MCMC method. The input model for MCMC fitting need four parameters: $S_{\rm tot}$, $\theta_{\rm core}$, $x$ and $y$. The search ranges for these four parameters to be estimated were set as follows: 10–25 mJy for $S_{\rm tot}$, $10^{-6}$–2  mas for $\theta_{\rm core}$, -1–1  mas for both $x$ and $y$. The MCMC fitting process was conducted with 200 walkers and $10^{4}$ iterations. The initial half of the samples were discarded, and results are presented using corner plots in Figure [5](#fig:corner). The parameters fitted through this process are listed in Table [\[tab:model\]](#tab:model).

![image](corner4.4GHz.pdf) ![image](corner7.6GHz.pdf)

# Lifetime of the dark cluster

Our approach to estimating the lifetime of the dark cluster present here follows (cite: Maoz1995; Maoz1998) and references therein. Since our objective is to exclude a dark cluster by illustrating that its lifetime is very short, we only consider the cluster that could survive for a long time. We presuppose that the structure of the cluster is described by Plummer model, with each constituent object assumed to have the same mass and zero temperature.

The dark cluster could be composed of variety of objects, such as (1) black holes with $m_{*}\geq3~M_{\odot}$; (2) neutron stars with $1.4\leq m_{*} \leq 3~M_{\odot}$; (3) brown dwarfs and (4) white dwarfs with $10^{-3} \leq m_{*} \leq 1.4~M_{\odot}$. The lifespan of a cluster is determined by the mass and radius of the objects that constitute it. We use $R_{\rm S}$ to represent the black hole radius. The radius of a neutron star is given by the equation $$\begin{equation}
    r_{*}(m_{*}) = \frac{(18\pi)^{2/3}}{10} \frac{\hbar^{2}}{Gm_{*}^{1/3}}\left(\frac{1}{m_{\rm H}}\right)^{8/3}
\end{equation}$$ where $\hbar$ is Plank constant and $m_{\rm H}$ is the mass of hydrogen atom. The radius of a white dwarf at zero temperature is expressed by the formula $$\begin{equation}
    r_{*} (m_{*}) = \frac{1.57\times10^{9}}{\mu} \frac{[1-(m_{*}/M_{3})^{4/3}]^{1/2}}{(m_{*}/M_{3})^{1/2}} ~ {\rm cm}
\end{equation}$$ where $\mu$ is the mean molecular weight and $M_{3}=5.816\mu^{-2}~M_{\odot}$. Lastly, the radius of a brown dwarf is represented by $$\begin{equation}
    r_{*}(m_{*}) = 2.2\times10^{9} \left(\frac{m_{*}}{M_{\odot}}\right)^{-1/3} \times \left[1+\left(\frac{m_{*}}{0.0032\,M_{\odot}}\right)^{-1/2}\right]^{-4/3}~{\rm cm}
\end{equation}$$

The lifetime of a dark cluster is constrained by two processes: evaporation and physical collisions. The maximum possible lifetime of the dark cluster depends on cluster’s half-mass $M_{\rm h} \equiv M/2$ and its half-mass density $\rho_{\rm h}$, where $M$ is mass of the cluster. The evaporation process is a consequence of weak gravitational scattering. The evaporation timescale of a cluster can be described as follows: $$\begin{equation}
\label{eq:t_evap}
    t_{\rm evap} \simeq \frac{4.3\times10^{4}(M_{\rm h}/m_{*})}{\ln [0.8(M_{\rm h}/m_{*})]} \left(\frac{\rho_{\rm h}}{10^{8}M_{\odot}\,{\rm pc^{-3}}}\right)^{-1/2}~{\rm yr}
\end{equation}$$ The typical timescale for each object to physically collide with another is given by: $$\begin{eqnarray}
\label{eq:t_coll}
    t_{\rm coll}(r_{*},r_{*}) =\nonumber \\ 
     \left[ 23.8 G^{1/2} M_{\rm h}^{1/3} \rho_{\rm h}^{7/6} \left(\frac{r_{*}^{2}}{m_{*}}\right)\left(1+\frac{m_{*}}{2^{1/2}\rho_{\rm h}^{1/3} M_{\rm h}^{2/3} r_{*}}\right) \right]^{-1} ~ {\rm s}
\end{eqnarray}$$ For a given $M_{\rm h}$ and $\rho_{h}$, the lifetime of a cluster composed of objects with mass $m_{*}$ and radius $r_{*}$ is $$\begin{equation}
    \tau(r_{*},m_{*}) = \min\left[t_{\rm coll},t_{\rm evap}\right]
\end{equation}$$ The maximum lifetime of a dark cluster, $\tau_{\rm max}$, can be determined by examining all classes of dark objects mentioned above, across different mass ranges, i.e., $$\begin{equation}
    \tau_{\rm max}(M_{\rm h},\rho_{\rm h}) = \max\left[\tau(r_{*}, m_{*})\right]
\end{equation}$$ Figure [4](#fig:tau) show the $\tau_{\rm max}$ for each pair of $M_{\rm h}$ and $\rho_{\rm h}$.

natexlab

(ref: ALMAPipeline) ALMA Pipeline Team. 2017, ALMA Science Pipeline User’s Guide, ALMA Doc 5.13

(ref: Anderson2004) Anderson, J. M., Ulvestad, J. S., & Ho, L. C. 2004, ApJ, 603, 42, doi: [`10.1086/381313`](http://doi.org/10.1086/381313)

(ref: Astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Bandyopadhyay2019) Bandyopadhyay, B., Xie, F.-G., Nagar, N. M., et al. 2019, MNRAS, 490, 4606, doi: [`10.1093/mnras/stz2874`](http://doi.org/10.1093/mnras/stz2874)

(ref: Blandford1999) Blandford, R. D., & Begelman, M. C. 1999, MNRAS, 303, L1, doi: [`10.1046/j.1365-8711.1999.02358.x`](http://doi.org/10.1046/j.1365-8711.1999.02358.x)

(ref: Blandford1982) Blandford, R. D., & Payne, D. G. 1982, MNRAS, 199, 883, doi: [`10.1093/mnras/199.4.883`](http://doi.org/10.1093/mnras/199.4.883)

(ref: Blandford1977) Blandford, R. D., & Znajek, R. L. 1977, MNRAS, 179, 433, doi: [`10.1093/mnras/179.3.433`](http://doi.org/10.1093/mnras/179.3.433)

(ref: Bower2006) Bower, G. C., Goss, W. M., Falcke, H., Backer, D. C., & Lithwick, Y. 2006, ApJL, 648, L127, doi: [`10.1086/508019`](http://doi.org/10.1086/508019)

(ref: Callingham2017) Callingham, J. R., Ekers, R. D., Gaensler, B. M., et al. 2017, ApJ, 836, 174, doi: [`10.3847/1538-4357/836/2/174`](http://doi.org/10.3847/1538-4357/836/2/174)

(ref: Cantiello2018) Cantiello, M., Blakeslee, J. P., Ferrarese, L., et al. 2018, ApJ, 856, 126, doi: [`10.3847/1538-4357/aab043`](http://doi.org/10.3847/1538-4357/aab043)

(ref: Capetti2022) Capetti, A., Brienza, M., Balmaverde, B., et al. 2022, A&A, 660, A93, doi: [`10.1051/0004-6361/202142911`](http://doi.org/10.1051/0004-6361/202142911)

(ref: Chen2017) Chen, L. 2017, ApJ, 842, 129, doi: [`10.3847/1538-4357/aa7744`](http://doi.org/10.3847/1538-4357/aa7744)

(ref: Chen2021) Chen, L., & Zhang, B. 2021, ApJ, 906, 105, doi: [`10.3847/1538-4357/abc42d`](http://doi.org/10.3847/1538-4357/abc42d)

(ref: Cheng2023) Cheng, X., Cho, I., Kawashima, T., et al. 2023, Galaxies, 11, 46, doi: [`10.3390/galaxies11020046`](http://doi.org/10.3390/galaxies11020046)

(ref: Cho2022) Cho, I., Zhao, G.-Y., Kawashima, T., et al. 2022, ApJ, 926, 108, doi: [`10.3847/1538-4357/ac4165`](http://doi.org/10.3847/1538-4357/ac4165)

(ref: Crossley2008) Crossley, J. H., Sjouwerman, L. O., Fomalont, E. B., & Radziwill, N. M. 2008, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7016, Observatory Operations: Strategies, Processes, and Systems II, ed. R. J. Brissenden & D. R. Silva, 70160O, doi: [`10.1117/12.787890`](http://doi.org/10.1117/12.787890)

(ref: Deller2011) Deller, A. T., Brisken, W. F., Phillips, C. J., et al. 2011, PASP, 123, 275, doi: [`10.1086/658907`](http://doi.org/10.1086/658907)

(ref: DiMatteo1997) Di Matteo, T., & Fabian, A. C. 1997, MNRAS, 286, L50, doi: [`10.1093/mnras/286.4.L50`](http://doi.org/10.1093/mnras/286.4.L50)

(ref: DiMatteo1999) Di Matteo, T., Fabian, A. C., Rees, M. J., Carilli, C. L., & Ivison, R. J. 1999, MNRAS, 305, 492, doi: [`10.1046/j.1365-8711.1999.02334.x`](http://doi.org/10.1046/j.1365-8711.1999.02334.x)

(ref: Doi2005) Doi, A., Kameno, S., & Inoue, M. 2005, MNRAS, 360, 119, doi: [`10.1111/j.1365-2966.2005.09014.x`](http://doi.org/10.1111/j.1365-2966.2005.09014.x)

(ref: Dunn2010) Dunn, R. J. H., Allen, S. W., Taylor, G. B., et al. 2010, MNRAS, 404, 180, doi: [`10.1111/j.1365-2966.2010.16314.x`](http://doi.org/10.1111/j.1365-2966.2010.16314.x)

(ref: EHTC2019) EHT Collaboration, Akiyama, K., Alberdi, A., et al. 2019, ApJL, 875, L1, doi: [`10.3847/2041-8213/ab0ec7`](http://doi.org/10.3847/2041-8213/ab0ec7)

(ref: EHTC2022) —. 2022, ApJL, 930, L12, doi: [`10.3847/2041-8213/ac6674`](http://doi.org/10.3847/2041-8213/ac6674)

(ref: Falcke1999) Falcke, H., & Biermann, P. L. 1999, A&A, 342, 49, doi: [`10.48550/arXiv.astro-ph/9810226`](http://doi.org/10.48550/arXiv.astro-ph/9810226)

(ref: Falcke2000) Falcke, H., Nagar, N. M., Wilson, A. S., & Ulvestad, J. S. 2000, ApJ, 542, 197, doi: [`10.1086/309543`](http://doi.org/10.1086/309543)

(ref: Fanaroff1974) Fanaroff, B. L., & Riley, J. M. 1974, MNRAS, 167, 31P, doi: [`10.1093/mnras/167.1.31P`](http://doi.org/10.1093/mnras/167.1.31P)

(ref: Gaia2022) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2022, arXiv e-prints, arXiv:2208.00211, doi: [`10.48550/arXiv.2208.00211`](http://doi.org/10.48550/arXiv.2208.00211)

(ref: Gebhardt2000) Gebhardt, K., Bender, R., Bower, G., et al. 2000, ApJL, 539, L13, doi: [`10.1086/312840`](http://doi.org/10.1086/312840)

(ref: Genzel2000) Genzel, R., Pichon, C., Eckart, A., Gerhard, O. E., & Ott, T. 2000, MNRAS, 317, 348, doi: [`10.1046/j.1365-8711.2000.03582.x`](http://doi.org/10.1046/j.1365-8711.2000.03582.x)

(ref: Ghez2005) Ghez, A. M., Salim, S., Hornstein, S. D., et al. 2005, ApJ, 620, 744, doi: [`10.1086/427175`](http://doi.org/10.1086/427175)

(ref: GRAVITYCollaboration2019) GRAVITY Collaboration, Abuter, R., Amorim, A., et al. 2019, A&A, 625, L10, doi: [`10.1051/0004-6361/201935656`](http://doi.org/10.1051/0004-6361/201935656)

(ref: Greisen2003) Greisen, E. W. 2003, in Astrophysics and Space Science Library, Vol. 285, Information Handling in Astronomy - Historical Vistas, ed. A. Heck, 109, doi: [`10.1007/0-306-48080-8_7`](http://doi.org/10.1007/0-306-48080-8_7)

(ref: Grossova2022) Grossová, R., Werner, N., Massaro, F., et al. 2022, ApJS, 258, 30, doi: [`10.3847/1538-4365/ac366c`](http://doi.org/10.3847/1538-4365/ac366c)

(ref: Hada2011) Hada, K., Doi, A., Kino, M., et al. 2011, Nature, 477, 185, doi: [`10.1038/nature10387`](http://doi.org/10.1038/nature10387)

(ref: Hada2013) Hada, K., Doi, A., Nagai, H., et al. 2013, ApJ, 779, 6, doi: [`10.1088/0004-637X/779/1/6`](http://doi.org/10.1088/0004-637X/779/1/6)

(ref: Ho2008) Ho, L. C. 2008, ARA&A, 46, 475, doi: [`10.1146/annurev.astro.45.051806.110546`](http://doi.org/10.1146/annurev.astro.45.051806.110546)

(ref: Ho1997) Ho, L. C., Filippenko, A. V., & Sargent, W. L. W. 1997, ApJ, 487, 568, doi: [`10.1086/304638`](http://doi.org/10.1086/304638)

(ref: Ho2001) Ho, L. C., & Ulvestad, J. S. 2001, ApJS, 133, 77, doi: [`10.1086/319185`](http://doi.org/10.1086/319185)

(ref: Humphrey2008) Humphrey, P. J., Buote, D. A., Brighenti, F., Gebhardt, K., & Mathews, W. G. 2008, ApJ, 683, 161, doi: [`10.1086/589709`](http://doi.org/10.1086/589709)

(ref: Janssen2021) Janssen, M., Falcke, H., Kadler, M., et al. 2021, Nature Astronomy, 5, 1017, doi: [`10.1038/s41550-021-01417-w`](http://doi.org/10.1038/s41550-021-01417-w)

(ref: Jiang2018) Jiang, W., Shen, Z., Jiang, D., Martı́-Vidal, I., & Kawaguchi, N. 2018, ApJL, 853, L14, doi: [`10.3847/2041-8213/aaa755`](http://doi.org/10.3847/2041-8213/aaa755)

(ref: Jiang2021) Jiang, W., Shen, Z., Martı́-Vidal, I., et al. 2021, ApJL, 922, L16, doi: [`10.3847/2041-8213/ac375c`](http://doi.org/10.3847/2041-8213/ac375c)

(ref: Johannsen2010) Johannsen, T., & Psaltis, D. 2010, ApJ, 718, 446, doi: [`10.1088/0004-637X/718/1/446`](http://doi.org/10.1088/0004-637X/718/1/446)

(ref: Johannsen2012) Johannsen, T., Psaltis, D., Gillessen, S., et al. 2012, ApJ, 758, 30, doi: [`10.1088/0004-637X/758/1/30`](http://doi.org/10.1088/0004-637X/758/1/30)

(ref: Kharb2006) Kharb, P., O’Dea, C. P., Baum, S. A., Colbert, E. J. M., & Xu, C. 2006, ApJ, 652, 177, doi: [`10.1086/507945`](http://doi.org/10.1086/507945)

(ref: Kharb2014) Kharb, P., O’Dea, C. P., Baum, S. A., et al. 2014, MNRAS, 440, 2976, doi: [`10.1093/mnras/stu421`](http://doi.org/10.1093/mnras/stu421)

(ref: Konigl1981) Konigl, A. 1981, ApJ, 243, 700, doi: [`10.1086/158638`](http://doi.org/10.1086/158638)

(ref: Kormendy2013) Kormendy, J., & Ho, L. C. 2013, ARA&A, 51, 511, doi: [`10.1146/annurev-astro-082708-101811`](http://doi.org/10.1146/annurev-astro-082708-101811)

(ref: Koryukova2022) Koryukova, T. A., Pushkarev, A. B., Plavin, A. V., & Kovalev, Y. Y. 2022, MNRAS, 515, 1736, doi: [`10.1093/mnras/stac1898`](http://doi.org/10.1093/mnras/stac1898)

(ref: Lee2017) Lee, M. G., & Jang, I. S. 2017, ApJ, 841, 23, doi: [`10.3847/1538-4357/aa6c6a`](http://doi.org/10.3847/1538-4357/aa6c6a)

(ref: Lister2021) Lister, M. L., Homan, D. C., Kellermann, K. I., et al. 2021, ApJ, 923, 30, doi: [`10.3847/1538-4357/ac230f`](http://doi.org/10.3847/1538-4357/ac230f)

(ref: Lo2023) Lo, W.-P., Asada, K., Matsushita, S., et al. 2023, ApJ, 950, 10, doi: [`10.3847/1538-4357/acc855`](http://doi.org/10.3847/1538-4357/acc855)

(ref: Lu2018) Lu, R.-S., Krichbaum, T. P., Roy, A. L., et al. 2018, ApJ, 859, 60, doi: [`10.3847/1538-4357/aabe2e`](http://doi.org/10.3847/1538-4357/aabe2e)

(ref: Lu2023) Lu, R.-S., Asada, K., Krichbaum, T. P., et al. 2023, Nature, 616, 686, doi: [`10.1038/s41586-023-05843-w`](http://doi.org/10.1038/s41586-023-05843-w)

(ref: Mahadevan1997) Mahadevan, R. 1997, ApJ, 477, 585, doi: [`10.1086/303727`](http://doi.org/10.1086/303727)

(ref: Manmoto1997) Manmoto, T., Mineshige, S., & Kusunose, M. 1997, ApJ, 489, 791, doi: [`10.1086/304817`](http://doi.org/10.1086/304817)

(ref: Maoz1995) Maoz, E. 1995, ApJL, 447, L91, doi: [`10.1086/309574`](http://doi.org/10.1086/309574)

(ref: Maoz1998) —. 1998, ApJL, 494, L181, doi: [`10.1086/311194`](http://doi.org/10.1086/311194)

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Miyoshi1995) Miyoshi, M., Moran, J., Herrnstein, J., et al. 1995, Nature, 373, 127, doi: [`10.1038/373127a0`](http://doi.org/10.1038/373127a0)

(ref: Nagar2005) Nagar, N. M., Falcke, H., & Wilson, A. S. 2005, A&A, 435, 521, doi: [`10.1051/0004-6361:20042277`](http://doi.org/10.1051/0004-6361:20042277)

(ref: Nagar2002) Nagar, N. M., Falcke, H., Wilson, A. S., & Ulvestad, J. S. 2002, A&A, 392, 53, doi: [`10.1051/0004-6361:20020874`](http://doi.org/10.1051/0004-6361:20020874)

(ref: Narayan1994) Narayan, R., & Yi, I. 1994, ApJL, 428, L13, doi: [`10.1086/187381`](http://doi.org/10.1086/187381)

(ref: Narayan1995A) —. 1995, ApJ, 444, 231, doi: [`10.1086/175599`](http://doi.org/10.1086/175599)

(ref: Ozel2000) Özel, F., Psaltis, D., & Narayan, R. 2000, ApJ, 541, 234, doi: [`10.1086/309396`](http://doi.org/10.1086/309396)

(ref: Paggi2014) Paggi, A., Fabbiano, G., Kim, D.-W., et al. 2014, ApJ, 787, 134, doi: [`10.1088/0004-637X/787/2/134`](http://doi.org/10.1088/0004-637X/787/2/134)

(ref: Paggi2017) Paggi, A., Kim, D.-W., Anderson, C., et al. 2017, ApJ, 844, 5, doi: [`10.3847/1538-4357/aa7897`](http://doi.org/10.3847/1538-4357/aa7897)

(ref: Panessa2019) Panessa, F., Baldi, R. D., Laor, A., et al. 2019, Nature Astronomy, 3, 387, doi: [`10.1038/s41550-019-0765-4`](http://doi.org/10.1038/s41550-019-0765-4)

(ref: Park2017) Park, S., Yang, J., Oonk, J. B. R., & Paragi, Z. 2017, MNRAS, 465, 3943, doi: [`10.1093/mnras/stw3012`](http://doi.org/10.1093/mnras/stw3012)

(ref: Psaltis2018) Psaltis, D., Johnson, M., Narayan, R., et al. 2018, arXiv e-prints, arXiv:1805.01242, doi: [`10.48550/arXiv.1805.01242`](http://doi.org/10.48550/arXiv.1805.01242)

(ref: Pushkarev2017) Pushkarev, A. B., Kovalev, Y. Y., Lister, M. L., & Savolainen, T. 2017, MNRAS, 468, 4992, doi: [`10.1093/mnras/stx854`](http://doi.org/10.1093/mnras/stx854)

(ref: Ramakrishnan2023) Ramakrishnan, V., Nagar, N., Arratia, V., et al. 2023, Galaxies, 11, 15, doi: [`10.3390/galaxies11010015`](http://doi.org/10.3390/galaxies11010015)

(ref: Rauch2016) Rauch, C., Ros, E., Krichbaum, T. P., et al. 2016, A&A, 587, A37, doi: [`10.1051/0004-6361/201527286`](http://doi.org/10.1051/0004-6361/201527286)

(ref: Salafia2022) Salafia, O. S., Ravasio, M. E., Yang, J., et al. 2022, ApJL, 931, L19, doi: [`10.3847/2041-8213/ac6c28`](http://doi.org/10.3847/2041-8213/ac6c28)

(ref: Shen2010) Shen, J., & Gebhardt, K. 2010, ApJ, 711, 484, doi: [`10.1088/0004-637X/711/1/484`](http://doi.org/10.1088/0004-637X/711/1/484)

(ref: Shen2005) Shen, Z.-Q., Lo, K. Y., Liang, M. C., Ho, P. T. P., & Zhao, J. H. 2005, Nature, 438, 62, doi: [`10.1038/nature04205`](http://doi.org/10.1038/nature04205)

(ref: Shepherd1997) Shepherd, M. C. 1997, in Astronomical Society of the Pacific Conference Series, Vol. 125, Astronomical Data Analysis Software and Systems VI, ed. G. Hunt & H. Payne, 77

(ref: Shurkin2008) Shurkin, K., Dunn, R. J. H., Gentile, G., Taylor, G. B., & Allen, S. W. 2008, MNRAS, 383, 923, doi: [`10.1111/j.1365-2966.2007.12651.x`](http://doi.org/10.1111/j.1365-2966.2007.12651.x)

(ref: Stanger1986) Stanger, V. J., & Warwick, R. S. 1986, MNRAS, 220, 363, doi: [`10.1093/mnras/220.2.363`](http://doi.org/10.1093/mnras/220.2.363)

(ref: Temi2022) Temi, P., Gaspari, M., Brighenti, F., et al. 2022, ApJ, 928, 150, doi: [`10.3847/1538-4357/ac5036`](http://doi.org/10.3847/1538-4357/ac5036)

(ref: Ulvestad2001) Ulvestad, J. S., & Ho, L. C. 2001, ApJ, 558, 561, doi: [`10.1086/322307`](http://doi.org/10.1086/322307)

(ref: Ulvestad1999ApJL) Ulvestad, J. S., Wrobel, J. M., Roy, A. L., et al. 1999, ApJL, 517, L81, doi: [`10.1086/312040`](http://doi.org/10.1086/312040)

(ref: Yuan2003) Yuan, F., Quataert, E., & Narayan, R. 2003, ApJ, 598, 301, doi: [`10.1086/378716`](http://doi.org/10.1086/378716)

[^1]: The Eddington luminosity is the maximum luminosity that can be achieved by an accreting black hole when there is hydrostatic equilibrium: $L_{\rm Edd} = 4\pi GM_{\rm BH}cm_{p}/\sigma_{\rm T}$, where $\sigma_{\rm T}$ is the Thomson cross section and $m_{p}$ is the mass of a proton.

[^2]: <https://science.nrao.edu/facilities/vlba/data-processing/vlba-7ghz-flux-density-scale>

[^3]: <https://www.vla.nrao.edu/astro/nvas/>

[^4]: <http://astrogeo.org/rfc/>

</paper>

Write the methods card for this paper.