# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...904...37W\sonnetcc\reply.txt

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
 "bibcode": "2020ApJ...904...37W",
 "title": "ALMA and VLA Observations of EX Lupi in Its Quiescent State",
 "year": 2020,
 "journal": "The Astrophysical Journal",
 "first_author": "White, Jacob Aaron",
 "n_authors": 18,
 "arxiv_id": "2009.14216",
 "doi": "10.3847/1538-4357/abbb94",
 "alma_projects_linked_by_archive": [
  "2015.1.00200.S",
  "2017.1.00224.S"
 ]
}
```

Paper text:
<paper>
# ALMA and VLA Observations of EX Lupi in its Quiescent State

## Abstract

Extreme outbursts in young stars may be a common stage of pre-main-sequence stellar evolution. These outbursts, caused by enhanced accretion and accompanied by increased luminosity, can also strongly impact the evolution of the circumstellar environment. We present ALMA and VLA observations of EX Lupi, a prototypical outburst system, at 100 GHz, 45 GHz, and 15 GHz. We use these data, along with archival ALMA 232 GHz data, to fit radiative transfer models to EX Lupi’s circumstellar disk in its quiescent state following the extreme outburst in 2008. The best fit models show a compact disk with a characteristic dust radius of 45 au and a total mass of 0.01 M$_{\odot}$. Our modeling suggests grain growth to sizes of at least 3 mm in the disk, possibly spurred by the recent outburst, and an ice line that has migrated inward to $0.2-0.3$ au post-outburst. At 15 GHz, we detected significant emission over the expected thermal disk emission which we attribute primarily to stellar (gyro)synchrotron and free-free disk emission. Altogether, these results highlight what may be a common impact of outbursts on the circumstellar dust.

# Introduction

Giant molecular clouds are the nurseries in which stars are born. The earliest phases of mass accumulation take place in the densest regions of the cloud cores and the rotation of these in-falling cores can lead to the formation of young stellar objects (YSOs) embedded in accretion disks.

A growing number of YSOs have been observed to have extreme outbursts (cite: audard14), increasing the brightness by up to several magnitudes and the total luminosity by a factor of $10-100$. The prototypical outbursting YSO, FU Orionis, entered an outburst in 1936 (cite: herbig66) and is still slowly fading (cite: kenyon00). This outburst has motivated the study of other similar systems (named FUors) that have also experienced outbursts of various timescales and intensities. In addition to the FUor class of young stars, there are systems that exhibit shorter duration and weaker outbursts called EXors (named after EX Lupi, discussed in detail below). Theoretical considerations (cite: zhu09; dangelo12; vorobyov15) suggest that EXors/FUors, and Sun-like stars in general, can build up a significant fraction of their mass during periods of enhanced accretion, referred to as episodic accretion. The outbursts of both EXors and FUors are thought to be due to this episodic accretion of material from their circumstellar disks onto the protostars. While it is generally accepted that the observed outbursts are due to accretion, the exact triggering and transport mechanism(s) that deliver material from the disk on to the star over short time periods typical for FUors/EXors is still unknown (cite: audard14).

Understanding the outburst mechanisms of protostars is important not only for building a complete picture of stellar evolution, but also for the potential implications for the planet formation process around low-mass stars. If these types of outbursts are a common byproduct of the star formation process then they will undoubtedly also impact disk evolution and therefore the conditions in which planets form. Outbursts have been shown to potentially change the chemistry and mineralogy of the surrounding circumstellar disk (cite: abraham09; rab17; molyarova18); could spur the growth of small solids through, e.g., evaporation and recondensation from a rapid evolution of the ice line (cite: cieza16); and offer a potential solution to the luminosity problem (cite: hartmann96).

EX Lupi is a young $1-3$ Myr M0 star (0.6 M$_{\odot}$, 0.7 L$_{\odot}$ quiescent luminosity) located $157.7\pm0.9$ pc away in the Lupus 3 cloud (cite: lombardi08; sipos09; frasca17; bailer18). There have been multiple observed outbursts in the EX Lupi system, the most recent of which was in 2008. During this last outburst, EX Lupi was monitored in the optical and infrared. The outburst caused the annealing of amorphous silicate particles to crystalline grains, which were transported to the outer comet-forming zone (cite: abraham09; abraham19). The direct effects of the outburst on the outer disk, however, are still yet to be fully characterized (cite: aguilar12). The outer disk was only recently spatially resolved by (cite: hales18) using the Atacama Large Millimeter Array (ALMA) at 232 GHz. They found no indications of substructure in the disk and used radiative transfer modeling to constrain the total dust mass to $1.0\times10^{-4}~\rm M_{\odot}$. (cite: kospal20) used spectropolarimetric monitoring of EX Lupi post-outburst with the Canada-France Hawaii Telescope (CFHT) to place constraints on the stellar magnetic fields. Their preliminary analysis suggests the surface magnetic field is 3 kG, stronger than what has been observed for some embedded FUor/EXor objects (cite: donati05) and more in line with what is seen in Classical T Tauri stars with field strengths of up to a few kG (cite: johnskrull07; bouvier07; johnskrull09). The strength and stability of the stellar magnetic field in EX Lupi can influence the stability of the accretion columns (cite: aguilar15) and has significant implications on possible outburst mechanisms.

In this paper, we present long wavelength observations of EX Lupi. In Sec. [2](#sec:obs), we describe the data and calibration procedures. In Sec. [3](#sec:models), we outline the model fitting approach used and in Sec. [4](#sec:disc) we discuss the results.

# Observations

|  | 232 GHz | 100 GHz | 45 GHz | 15 GHz |
|:--:|:--:|:--:|:--:|:--:|
| Facility | ALMA | ALMA | VLA | VLA |
| Observation Date | 2016 Jul 25 | 2018 Jan 27, Mar 17, Mar 19 | 2019 May 13, Jul 10 | 2019 Mar 09 |
| Flux Calibrator | J1427-4206 | J1427-4206, J1517-2422 | 3C286 | 3C286 |
| Beam Size | $0.32\ensuremath{''}\times0.26\ensuremath{''}$ | $1.09\ensuremath{''} \times 0.81\ensuremath{''}$ | $0.36\ensuremath{''} \times 0.16\ensuremath{''}$ | $1.88\ensuremath{''} \times 0.42\ensuremath{''}$ |
| Beam PA | $61.8^{\circ}$ | $87.8^{\circ}$ | $10.2 ^{\circ}$ | $10.5^{\circ}$ |
| $\sigma_{\rm rms}$ | 0.038 mJy beam$^{-1}$ | 0.013 mJy beam$^{-1}$ | 0.043 mJy beam$^{-1}$ | 0.007 mJy beam$^{-1}$ |
| Peak Flux | 8.8 mJy beam$^{-1}$ | 1.98 mJy beam$^{-1}$ | $<0.130^{*}$ mJy beam$^{-1}$ | 0.044 mJy beam$^{-1}$ |
| Total Flux | $17.37\pm 0.15$ mJy | $2.72\pm0.013$ mJy | \- | $0.050\pm0.008$ mJy |

The analysis presented here uses a combination of new radio observations with the *NSF’s Karl G. Jansky Very Large Array* (VLA), new ALMA 100 GHz observations, and ALMA 232 GHz data from literature (cite: hales18). All of the observations are summarized in Table [\[obs_overview\]](#obs_overview) and the new ones are detailed below.

## VLA Observations

The VLA observations (ID 19A-145, PI White) were centered on EX Lupi using J2000 coordinates RA $= 16^{\rm h}~ 03^{\rm m} ~  7.09^{\rm s}$ and $\delta = -40^{\circ} ~18' ~05.10\ensuremath{''}$. The Scheduling Blocks (SB) for each observation were executed on different days but all used the B configuration with 26 antennas and baselines ranging from 0.21 to 11.1 km. Quasar J1607-3331 was used for bandpass and gain calibration. Quasar 3C286 was used as a flux calibration source. Data were reduced using the CASA 5.4.1 pipeline, which included bandpass, flux, and phase calibrations (cite: casa_reference). The absolute flux calibration of the VLA at these wavelengths is typically $\sim5\%$. [^1] All of the SBs used the same sources for calibration.

The 15 GHz data from the VLA were acquired in Semester 19A on 2019 March 09 and had a total on-source time of $948\rm~s$. The observations used a Ku Band tuning setup with $3\times2$ GHz basebands and rest frequency centers of 13 GHz, 15 GHz, and 17 GHz. This gives an effective frequency of 15 GHz (1.99 cm). The data were imaged with a natural weighting and cleaned using CASA’s *CLEAN* algorithm down to a threshold of $\frac{1}{2}$ the RMS noise. The 15 GHz observations achieve a sensitivity of $7~\rm \mu Jy~beam^{-1}$. The size of the resulting synthesized beam is $1.88\ensuremath{''}\times 0.42\ensuremath{''}$ ($\sim 180$ au) at a position angle of $10.5^{\circ}$. Due to the large beam, the emission is only marginally resolved along the minor axis of the beam. The peak flux is $0.044~\rm  mJy~beam^{-1}$ as measured in the CLEANed image. We used the CASA task *uvmodelfit* and a disk model to obtain a total flux of $0.050\pm0.008~\rm  mJy$.

The 45 GHz VLA data were acquired on 2019 May 13 and 2019 July 10 and had a total combined on-source time of $2345\rm~s$. Both 45 GHz SBs used a Q Band tuning setup with $4\times2.048$ GHz basebands and rest frequency centers of 41 GHz, 43 GHz, 47 GHz, and 49 GHz. This gives an effective frequency of 45 GHz (6.7 mm) for the Q band. The 45 GHz observations were concatenated in CASA and the data were imaged with a natural weighting and cleaned using the *CLEAN* algorithm down to a threshold of $\frac{1}{2}$ the RMS noise. Together, these data achieve a sensitivity of $43~\rm \mu Jy~beam^{-1}$. The resulting synthesized beam is $0.36\ensuremath{''} \times 0.16\ensuremath{''}$ ($\sim 40$ au) at a position angle of $10.2^{\circ}$.

The low declination of EX Lupi leads to an elongated synthesized beam with the VLA (EX Lupi is located at $\delta = -40^{\circ}$ and the VLA is at a latitude of $34^{\circ}~ \rm N$). The atmospheric fluctuations at low altitude can also be much greater, leading to a poorer phase calibration and thus impacting the quality of the reconstructed images. These factors, coupled with less time on source than initially requested for the Q Band, led to a non-detection at 45 GHz. We note that this does not necessarily mean the disk is not observable at these frequencies.

## ALMA Observations

EX Lupi was observed with ALMA (2017.1.00224.S, PI Kóspál) on 2018 January 27, March 17, and March 19 with a phase center of RA$= 16^{\rm h}~ 03^{\rm m} ~ 5.5^{s}$ $\delta = -40^{\circ}$ $18'$ $25.4\ensuremath{''}$. The total on-source integration time was 11640 s. The nominal antenna configuration was C43-4, with baselines between 14 m and 1398 m. Two spectral setups were used with spectral windows for different molecular lines (which will be presented in a later paper). In both setups, a 1.875 GHz wide window was centered at 100.2 GHz (2.99 mm) to measure the continuum emission of EX Lupi. The data were manually calibrated using the CASA 5.4.1 pipeline. The procedure included offline water vapor radiometer calibration, system temperature correction, and bandpass, phase and amplitude calibrations. Quasars J1427$-$4206 and J1517$-$2422 were used for pointing, bandpass, and flux calibration, and Quasar J1610$-$3958 was used for phase calibration. The sampled visibilities were Fourier transformed, creating dirty images of the source, which yields the skymodel of the target convolved with the point source function (PSF) of the beam. Dirty images for each spectral window were used to determine the frequencies without line emission and as input for the *uvcontsub* routine in CASA to obtain the continuum emission.

The 100 GHz observations were concatenated in CASA and the data were imaged with a natural weighting and CLEANed using the *CLEAN* algorithm down to a threshold of $\frac{1}{2}$ the RMS noise. Together, these data achieve a sensitivity of $13~\rm \mu Jy~beam^{-1}$. The resulting synthesized beam is $1.09\ensuremath{''} \times 0.81\ensuremath{''}$ ($\sim 150$ au) at a position angle of $87.8^{\circ}$. The disk is marginally resolved. The peak flux is $1.98~\rm Jy~beam^{-1}$ as measured in the CLEANed image. We used the CASA task *uvmodelfit* and a disk model to obtain a total flux of $2.72\pm0.013~\rm \mu Jy$.

## Literature Data

In addition to the new ALMA and VLA data presented here, we also use the ALMA 232 GHz continuum data from (cite: hales18) in our analysis. The observations were made on 2016 July 25, have a CLEANed synthesized beam of $0.32\ensuremath{''}\times0.26\ensuremath{''}$, and sensitivity of $\sigma_{\rm rms} = 38 ~\rm \mu Jy~beam^{-1}$. The disk was well resolved at this frequency. No further calibration or processing was performed outside the procedure listed in (cite: hales18).

# Model Fitting

To constrain the parameters of the dust in EX Lupi’s circumstellar disk, we followed a radiative transfer (RT) model fitting approach similar to (cite: hales18). We use the RT code RADMC-3D 0.41 (cite: dullemond12) with the Python interface radmc3dPy[^2] to set the code input parameters for a given disk model. We keep the following parameters fixed in the fitting procedure: inclination $i=32^{\circ}$, position angle PA$=65^{\circ}$, and inner disk radius $\rm r=0.05~au$ (cite: hales18); flaring parameter $\psi = 0.09$ (cite: sipos09); stellar temperature T $=3859~\rm K$ and stellar radius R $=1.6~\rm R_{\odot}$ (cite: frasca17).

We adopt a disk model similar to that of a typical T Tauri protoplanetary disk (cite: andrews09) with a disk density given by:

$$\begin{equation}
\rho =\frac{\Sigma(r,\phi)}{H_p\sqrt{(2\pi)}}\exp{\left(-\frac{z^2}{2H_p^2}\right)},
\end{equation}$$

where $\Sigma$ is the surface density profile, $H_{\rm p}$ is the pressure scale height, and z is the height above the disk midplane. The disk’s surface density profile follow a power-law profile with an exponential outer tapering:

$$\begin{equation}
\Sigma(r) = \Sigma_0\left(\frac{r}{R_c}\right)^{-\gamma} \exp{\left\{-\left(\frac{r}{R_c} \right)^{2-\gamma}\right\}},
\end{equation}$$

where $\Sigma_{0}$ is the surface density at the inner radius of 0.05 au, $R_{\rm c}$ is the characteristic radius of the disk, and $\gamma$ is the power-law exponent of the radial surface density profile. The pressure scale height is defined as:

$$\begin{equation}
H_p = h_c \left( \frac{r}{100 \rm~au} \right) ^{1+\psi}, 
\end{equation}$$

where $\psi$ is the disk flaring parameter and $h_{\rm c}$ is the ratio of the pressure scale height over radius at 100 au (cite: hales18).

In order to converge on the best fit disk parameters, we use a Metropolis-Hastings Markov Chain Monte Carlo (MCMC) model fitting approach. The free parameters considered in the modeling are: the total disk mass with a gas-to-dust ratio of 100:1, $M_{\rm disk}$, characteristic radius, $R_{\rm c}$, power law exponent of the surface density profile, $\gamma$, and scale height ratio at 100 au, $h_{\rm c}$. We perform the MCMC modelling in the image plane (cite: booth16; white_fom). After a trial model is selected, we use RADMC-3D and the *mctherm* command to calculate the dust temperature and then use the *image* command to generate a ray-traced continuum image projected to the inclination and position angle of the disk. The image is then attenuated by the primary beam and convolved with the dirty beam for a given observational setup. A $\chi^{2}$ for each trial model is calculated as

$$\begin{equation}
    \chi^{2} = \frac{(Data - Model)^{2}}{\sigma^{2}},
\end{equation}$$

where $\sigma$ is the observed $\sigma_{\rm rms}$ for a given observation multiplied by the synthetic beam size in pixels (cite: booth16). To fit multiple wavelength’s data simultaneously, the $\chi^{2}$ at each wavelength needs to be calculated and weighted. We adopt an equal weighting for each wavelength, and all of the $\chi^{2}$ values are averaged together. A given trial model is then accepted if a random number drawn from a uniform distribution \[0,1\] is less than $\alpha$, where

$$\begin{equation}
    \alpha = \min(e^{\frac{1}{2}(\chi^{2}_{i} - \chi^{2}_{i+1})},1).
\end{equation}$$

Fitting the 232 GHz, 100 GHz, and 15 GHz data simultaneously requires a dust opacity file extended to larger grain sizes. We use the OpacityTool[^3] program (cite: toon81; woitke16) to get more realistic dust absorption and scattering parameters. This program calculates dust opacities by using a volume mixture of 60% amorphous silicates (cite: dorschner95), 15% amorphous carbon (cite: zubko96), and a 25% porosity. Bruggeman mixing is used to calculate an effective refractory index and a distribution of hollow spheres with a maximum hollow ratio of 0.8 (cite: min05) is included to avoid Mie theory scattering artifacts. We further assume the disk is populated by $0.1 - 21000~\mu$m grains following a power-law size distribution of $s^{-3.5}$.

We were unable to adequately reproduce any wavelength’s data with this approach. We tried varying the weight of each wavelength’s $\chi^{2}$ and could only begin obtaining reasonable results if the weighting for the 15 GHz data was set to an arbitrarily small value. This indicates that the approach is not well suited for fitting all three datasets simultaneously, or that there are different emission mechanisms at longer wavelengths. Therefore, we decided to exclude the 15 GHz data and discuss other approaches to fitting it in Sec.[4.1](#sec:mod).

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Dataset(s) | Disk Mass | Characteristic Radius | $\gamma$ | Scale Height |
|  | (M$_{\odot}$) | (au) |  | (au) |
| 232 GHz + 100 GHz | 0.0099 | 45 | 0.25 | 2.5 |
|  | \[0.0067, 0.012\] | \[39, 68\] | \[$-0.36$, 0.77\] | \[1.9, 3.8\] |
| 15 GHz | 0.035 | 56 | 0.12 | 89 |
|  | \[0.011, 0.053\] | \[13, 140\] | \[$-1.8$, 1.2\] | \[21, 98\] |
|  |  |  |  |  |
| Dataset | Flux | X-offset | Y-offset |  |
|  | (mJy) | ($''$) | ($''$) |  |
| 15 GHz | 0.055 | 0.025 | 0.26 |  |
|  | \[0.045, 0.066\] | \[$-0.09$, 0.11\] | \[$-0.010$, 0.55\] |  |

To constrain the properties of the 232 GHz and 100 GHz observations, we use all the same approach and assumptions outlined above but change the particle size population to $0.1 - 10000~\mu$m grains. We adopted an equal weighting for the two data sets and ran an MCMC fit with $100\times1000$ link chains minus 100 each for burn-in. This approach of only fitting the ALMA data was able to well reproduce the observations. The most probable values of the free parameters and 95% credible region (CR) are summarized in Table [\[mod_results\]](#mod_results). The resulting best fit model and residuals are shown in Fig. [1](#fig:resid_alma) and the posterior distribution functions (PDF) are shown in Fig. [2](#fig:pdf_alma).

![](b3_b6_residuals_map_label.png)

![](b3_b6_PDF.png)

# Discussion

## Model Fitting Results

Our RT models of the 232 and 100 GHz ALMA data were able to well reproduce the observations. When fitting both of the datasets simultaneously, we find most probable values of: M$_{\rm disk} = 0.01~\rm M_{\odot}$, R$_{c}=45$ au, $\gamma= 0.25$, and h$_{c} = 2.5$ au (the corresponding 95% confidence intervals are listed in Table [\[mod_results\]](#mod_results)). The total flux of the most probable models at 232 and 100 GHz are 18.2 and 2.45 mJy, respectively. Most of the results are consistent with the values reported in (cite: hales18), within the uncertainties, which only fit the ALMA 232 GHz data. We find though that the most probable value of the characteristic radius is about a factor of 2 larger. This difference in radius could be due to the larger beam size in the 100 GHz observations, along with equal weighting, which is forcing the models to be larger. The spectral index between 232 and 100 GHz is $\alpha_{1.3-3.0 {\rm mm}} = 2.20\pm 0.11$ (the uncertainty includes a 10% absolute flux calibration uncertainty at each frequency). The spectral index is consistent with $2.19\pm0.47$ as reported in (cite: hales18) and calculated within the ALMA Band 6 spectral windows. Extrapolating the peak flux of the 100 GHz data to 45 GHz, along with the new beam size and $\alpha=2.2$, gives a peak flux lower than the achieved $\sigma_{\rm rms}$ of the 45 GHz observations. This calculated flux shows that the non-detection at 45 GHz is not useful for constraining the thermal disk properties.

If the 15 GHz observations are tracing the thermal emission from large grains, then it is possible these large grains are located at a different area of the disk than the smaller grains probed by ALMA. To test this, we tried fitting the VLA 15 GHz data alone with the same RT approach as for the ALMA datasets. This approach allows for a different disk geometry of the large grains, but still requires the total flux to be well fit to the data. We note though that due to the large beam size at 15 GHz, the disk is not resolved along the major axis and would be only marginally resolved along the minor axis. The results are summarized in Table [\[mod_results\]](#mod_results), the best fit model and residuals are shown in Fig. [3](#fig:resid_vla), and the PDF is shown in Fig. [4](#fig:pdf_vla).

![](vla_only_residuals_map.png)

![](vla_only_PDF.png)

While the 15 GHz only model does indeed well reproduce the data, the resulting disk parameters seem improbable. As segregation by grain size is possible due to radial drift and settling, a different disk geometry alone is not immediately disqualifying. The scale height, however, seems un-physically large at 89 au. Larger grains would be expected to settle in the midplane of the disk, meaning the scale height would likely be the same or smaller than is observed with the mm grains. The best fit total disk mass is also $3.5\times$ larger than when fitting to the mm data alone. Such a disk may have emission at 45 GHz, depending on the spectral index, and we report a non-detection at 45 GHz. We conclude that even though a thermal emission model can technically fit the data well at 15 GHz, the resulting disk parameters to do so are highly improbable. Alternate sources of 15 GHz emission are explored in Sec. [4.3](#sec:long).

## Millimeter Observations & Grain Growth

EX Lupi lies between the Lupus 3 and Lupus 4 star forming regions (cite: cambresy99). ALMA surveys of protoplanetary disks in the Lupus star forming regions have found total disk masses to be $\sim10^{-3}~\rm M_{\odot}$ (cite: ansdell16). Our model fitting finds a total disk mass nearly an order of magnitude higher, assuming a gas-to-dust ratio of 100:1. The mass discrepancy could be due to the assumptions made in the mass calculation in (cite: ansdell16) such as the optical depth and that here we include a full RT calculation. The actual gas-to-dust ratio in EX Lupi could also be much lower than assumed. If the difference in the masses is indeed real, it could be explained by EX Lupi being younger, more heavily accreting, or from an inherent difference in the disks of EXor/FUor-type system from that of typical protoplanetary disks. EX Lupi’s disk mass is smaller than that of FUors, as expected, but the characteristic radius is similar. Other ALMA studies have found that EXor/FUor disks tend to be more compact than that of typical protoplanetary disks (cite: cieza18).

EX Lupi experienced an outburst in 2008 and has since returned to a quiescent state. Therefore, all of the ALMA and VLA data presented here are indicative of a post-outburst circumstellar environment. (cite: abraham09) found that the outburst increased the crystallinity of the disk grains and transported them from the inner regions to the outer regions. Their work shows that even a short-lived outburst, such as an EXor-type outburst, can have observable effects on the circumstellar disk.

The water ice line (or snow line) is the radial location in a disk where water reaches its condensation temperature and freezes out on to grains in the disk. The exact temperature at which this occurs depends on other disk properties, such as gas pressure, but is typically between 150 to 175 K in the midplane of a disk (cite: lecar06). EX Lupi’s recent outburst increased the bolometric luminosity by about $36 \times$ (cite: abraham09). This enhanced luminosity can heat the disk and push the ice line(s) out to further radial distances. This was observed in ALMA observations of V883 Ori, where the ice line moved from a presumed $1-5$ au pre-outburst to a current location of 42 au as measured on the surface of the disk (cite: cieza16). As an outburst fades and the temperature drops, the ice line will move back inwards to the pre-outburst location. From (cite: abraham09), we estimate that during EX Lupi’s outburst the ice line was located at $20-30$ au on the surface of the disk and $1-2$ au in the midplane of the disk. Using *Spitzer* observations of the H$_{2}$O spectra, (cite: banzatti12) find the ice line moved from 1.3 au during outburst to 0.6 au after outburst.

Our RT modeling shows that the ice line is now located at $3-4$ au on the surface of the disk and $0.2-0.3$ au in the disk’s midplane, indicating a significant shift inwards post-outburst. To check if the disk could have reasonably cooled off enough to make this change in the position of the ice line, we explore the disk relaxation timescales (cite: flock17). The density and temperature we take from our best-fit RT model, the gas-to-dust ratio is set to 100:1, and we choose a representative cooling wavelength opacity at $\rm 18\,\mu m$ of $\kappa=52.7 \rm \,cm^2/g$. The relaxation time curve is shown in Fig. [5](#fig:time_plot).

The black line represents the relaxation timescale in years for the best fit disk model as a function of radial position in the disk, with the outburst and post-outburst ice lines indicated in gray. This curve shows that EX Lupi’s recent outburst, of duration of $\sim1$ year, could only significantly heat the midplane of the disk out to radii of 1-2 au, consistent with data from during the outburst (cite: abraham09; banzatti12). While the current data cannot be used to infer the location of the ice line prior to the outburst, the outburst and post-outburst data together show evidence that the location of the ice line can indeed shift during EXor-type events. The plot also shows that the $\sim10$ yr time between the end of the outburst and the observations is more than enough to relax the disk up to 10 au to a new thermal state.

![](timescale_plot.png)

An ice line can be a source of turbulence in a disk, around which grain growth can occur (cite: brauer08; ros13; zhang15). Therefore as the ice line moves inwards after an outburst it provides a potential mechanism to spur grain growth throughout the disk. The associated timescales for water to deposit onto grains near the ice line will be much shorter than the relaxation timescale outlined above, meaning grain growth from water freeze-out or deposition can be commensurate with the moving position of the ice line (cite: brown90). Thermal grains are inefficient emitters at wavelengths longer than their grain size. Therefore, using the detection of the disk in the ALMA 100 GHz data, and calculated spectral index of $\alpha=2.20\pm0.01$ indicating the disk is optically thin, we infer that grains of at least $3\rm~mm$ may be present in the disk post-outburst. Our RT models include grains of sizes up to $1\rm~cm$. While this is not a confirmation of $1\rm~cm$ grains it does indicate the data is at least consistent with the presence of up to $1\rm~cm$ grains. Significant grain growth is possible with EX Lupi’s evolving ice line, although we note that there is no pre-outburst ALMA and VLA data to compare it to. If EXor-like outbursts, which are short lived and can repeat many times during pre-main-sequence stellar evolution (cite: vorobyov15; white19), are indeed common for most stars then appreciable grain growth can occur throughout the disk both early and often. Quick and abundant grain growth to mm-cm sized particles is an important step in the planet formation process and can drive the growth of larger planets and planetesimals (cite: morbidelli16; johansen17; hughes17). Significant early grain growth and the presence of planetesimals is also a possible explanation for the gaps seen in HL Tau (cite: brogan15) or surveys of nearby protoplanetary disks with the ALMA DSHARP survey (cite: andrews18).

## Long Wavelength Central Emission

In Sec. [3](#sec:models), we concluded that the 15 GHz VLA data is likely dominated by something other than thermal disk emission. A more likely scenario is that at 15 GHz we are seeing thermal disk emission plus a combination of non-thermal disk emission, stellar winds, jets, or stellar emission. To test this scenario, we can fit a point source emission model on top of the thermal disk emission. Given the resolution of the 15 GHz data ($1.88\ensuremath{''}\times0.42\ensuremath{''}$), we are unable to differentiate emission from a point source and a moderately extended (i.e., a few au) region. Taking the best fit RT model from the ALMA data alone, we use RADMC-3D to calculate the emission at 15 GHz, resulting in a very faint disk with a total flux of only $\sim0.001$ mJy. Starting with this disk model, the “additional" emission required to reproduce the data can be assumed to be coming from approximately the center of the disk. This leaves only 3 free parameters: the flux of the central emission, the X-offset, and the Y-offset. We adopt an MCMC modelling approach similar to the one outlined in Sec. [3](#sec:models) but now just add the flux of the central emission on top of the already calculated RT model. The results are summarized in Table [\[mod_results\]](#mod_results), the best fit model and residuals are shown in Fig. [6](#fig:resid_cent), and the PDF is shown in Fig. [7](#fig:pdf_cent). We find a most probable flux of 0.055 mJy, an X-offset of $0.025\ensuremath{''}$, and a Y-offset of $0.26\ensuremath{''}$. Due to the nature of the large beam at 15 GHz ($1.88\ensuremath{''}\times 0.42\ensuremath{''}$), the location of the central emission flux is still broadly consistent with being peaked on the star itself.

![](central_emission_residuals_map.png)

![](central_emission_PDF.png)

### Role of the Magnetic Field

Some of the most promising outburst theories for EXors rely on the role of the magnetic field. (cite: armitage16) predicted that the outbursts could be explained by changes in the polarity and strength of the stellar magnetic fields at the kG-level. In a competing scenario, (cite: dangelo12) proposed an instability which can lead to quasi-periodic oscillations in the inner disk and associated recurrent outbursts. This instability can occur when the accretion disk is truncated close to the co-rotation radius by the strong magnetic field of the star. Stable accretion columns linked to a very strong magnetic field in EX Lupi were noted in (cite: aguilar15).

In principle, if kG-level stellar magnetic fields were present in EX Lupi then there could be significant non-thermal emission that would yield brightness temperatures easily detectable at long wavelengths with VLA. The central emission flux of 0.055 mJy corresponds to a Rayleigh-Jeans brightness temperature of T$_{B} \approx 4\times10^{7}$ K, assuming the size of the emitting region is uniformly spread out over the surface of the star (we note that depending on the emission mechanism the actual emitting region could range from a small localized area of the star to several stellar radii). This brightness temperature is much larger than the effective temperature of EX Lupi ($T=3859~\rm K$), which indicates that significant non-thermal stellar emission could be present as was seen in optical line emission (cite: aguilar12).

One potential source of such large brightness temperatures is synchrotron emission from relativistic or nearly relativistic electrons being accelerated by EX Lupi’s magnetic field. If synchrotron emission is present, then the flux should peak near the critical frequency (cite: hughes19),

$$\begin{equation}
\nu_{crit} = \frac{\gamma^{2} q B} {2 \pi m_{e}},
\end{equation}$$

where $\gamma$ is the Lorentz factor and is assumed to be $\sim1$, q is the electron charge, B is the magnetic field strength, and $m_{e}$ is the electron mass (we note that $\gamma$ here is not the same as the disk power-law exponent used in Eqn. 2). Adopting a magnetic field strength of 3 kG gives $\nu_{crit} = 8.4$ GHz. Since the flux should quickly drop off at frequencies larger than the critical frequency, it would be unlikely to observe such a large flux at 15 GHz. However, if the electrons are slightly more relativistic, with $\gamma=1.34$, then $\nu_{crit}=15$ GHz. Alternatively, (cite: armitage16) predict that significant changes in magnetic field strength could be a driver for the episodic accretion in EXor-type stars. Therefore, the magnetic field strength could potentially be different than measured previously with CFHT (cite: kospal20). If this is indeed the case, and $\nu_{crit}$ is $\sim15$ GHz, then a magnetic field strength of $\sim5.4$ kG can be inferred.

The effective temperature (cite: pacholczyk70) of electrons emitting synchrotron radiation at a frequency $\nu$, is given by:

$$\begin{equation}
T_{e}\approx \Big(\frac{2 \pi m_{e} \nu }{q B}\Big)^{1/2} \frac{m_e c^2}{3 k}
\end{equation}$$

where k is the Boltzmann constant. This yields $2-3 \times 10^{9}$ K, depending on which value for the magnetic field is used. The electron temperature is about a factor of 50 larger than the observed brightness temperature implying the emission is optically thin. At face value, synchrotron emission is a potential source of the 15 GHz emission. An important consideration though is that the size of the emitting region could be extended much further from the stellar surface. At further stellar separations, the magnetic field strength will become weaker causing $\nu_{crit}$ to fall below 15 GHz and the expected synchrotron emission at 15 GHz to be much lower as well.

While EX Lupi is indeed still a pre-main-sequence star, its spectral classification is M0 and its mass indicates that when it reaches the main-sequence it will still be an M-type star. M-type stars are notorious for flares and magnetic activity, but were not observed at radio wavelengths until recent technological advancements (cite: berger01). While the exact emission mechanisms are still debated, they are thought to be primarily due to electron cyclotron maser instabilities (ECMI) and/or gyrosynchrotron emission.

ECMI emission is similar to the auroral emission observed on most solar system planets (cite: turnpenney18). If the 15 GHz emission in EX Lupi was due to ECMI, then the emission is expected to peak at the fundamental critical frequency of $\nu_{crit} = 8.4$ GHz and fall off rapidly at higher frequencies. ECMI requires a relatively stable magnetic field configuration, such as in planetary or brown dwarf magnetic fields. Therefore, even though EX Lupi’s magnetic field strength could have changed between the CFHT and VLA observations such that $\nu_{crit} \sim 15$ GHz, ECMI is a highly unlikely source of the 15 GHz emission due to the required stability.

If the 15 GHz emission in EX Lupi was due to gyrosynctrotron emission, then it is likely due to magnetic reconnection events releasing a large number of energetic particles (cite: williams14; hughes19). The surface of a pre-main-sequence accreting M-type star, such as EX Lupi, is undoubtedly a turbulent environment where these processes could dominate. The expected emission at 15 GHz depends on the size of the emitting region (which is typically much smaller than the stellar radius), the magnetic field strength, and the electron energy index $\delta$. Assuming the gyrosynchrotron emission is optically thin, then the spectral index can be used as a tracer for $\delta$. Following (cite: hughes19), the relation between all of these parameters is given by:

$$\begin{equation}
    R_{\rm em} = 132 \Big(\frac{d}{pc}\Big) \Big(\frac{GHz}{\nu}\Big) \sqrt{\frac{F_{\mu Jy}}{T_{eff}}}, 
\end{equation}$$

where $R_{\rm em}$ is the emitting region in units of R$_{\odot}$, F$_{\rm  \mu Jy}$ is the observed flux in $\mu$Jy, and T$_{\rm eff}$ is given by:

$$\begin{equation}
    T_{\rm eff} = 2.2\times 10^9 ~ ({\rm sin}~\theta)^{-0.36 - 0.06\delta} 10^{-0.31 \delta}  \Big(\frac{\nu}{\nu_{crit}}\Big)^{0.50 + 0.085 \delta}
\end{equation}$$

where $\theta$ is assumed to be $\sim90^{\circ}$ (cite: dulk85). Fig. [8](#fig:gyro_plot) shows the size of the emitting region and magnetic field strength for various values of $\delta$ (which cannot be constrained with the available data). If we assume a typical lower level limit of $\delta\sim2$ and a magnetic field strength range of $3-6~\rm kG$ then the corresponding size of the emitting region is $\sim0.3-0.5~\rm R_{\odot}$. This is a significant fraction of the stellar surface ($\rm R_{*}=1.6~ R_{\odot}$) and much larger than is typically expected for main-sequence M-dwarf stars which have reconnection regions typically of order $0.01~\rm R_{\odot}$. If $\delta>2$, which is typically the case in M-dwarfs, then the size of the emitting region quickly becomes larger than the star. EX Lupi could, however, have a very small value of $\delta$ or have the gyrosynchrotron emission come from a large area where it is actively accreting disk material. Follow-up observations at higher/lower frequencies will enable spectral index constraints, and thus a value for $\delta$, to better determine if gyrosynchrotron is a potential source of the observed 15 GHz emission.

![](gyro_ex_lup_plot.png)

### Radio Jets and Non-thermal Disk Emission

Some EXor/FUor systems also have very bright radio jets (cite: poetzel89; rodriguez03). While EX Lupi did show significant X-ray activity leading up to and during the most recent outburst, the emission is most likely stemming from accretion shocks instead of jets (cite: grosso10). No radio jets have been previously reported in EX Lupi. If the 15 GHz emission was indeed due to a radio jet, then we would expect it to have an approximately flat spectral index leading it to possibly be detectable at 45 GHz. Since we did not detect anything at 45 GHz, and no radio jet was reported previously, we note the likelihood of the 15 GHz emission being jet-driven is low.

Centrally located disk winds are another possible source of long wavelength emission. (cite: kospal11) found that the hydrogen emission within 1 au is likely due to disk winds in EX Lupi. In optical line spectra, there is further evidence of disk winds in both outburst and quiescence (cite: aguilar12; aguilar15; banzatti19). (cite: hales18) observed large scale asymmetries in the outer CO gas disk which could be due to a molecular outflow. Similar to jets, disk winds would likely be peaked at frequencies $<15$ GHz and have a flat to slightly positive spectral index. Follow-up observations at $<15$ GHz are necessary in order to measure the spectral index and determine if winds or jets are a possible source of observed emission.

Free-free emission from an ionized disk, typically more prevalent in the latter stages of disk dissipation when photoevaporation becomes significant, can come from EUV and X-ray irradiation. EX Lupi had significant X-ray activity before and during the outburst, which could have significantly ionized its inner disk. Although unlikely, if this irradiation continued after the outburst ended then free-free emission could still be present in the EX Lupi system. Free-free emission can also arise from accretion shocks propagating through the disk when the accretion rate becomes much larger (cite: hartmann96). (cite: aguilar15) find evidence of accretion shocks via optical spectroscopy and (cite: grosso10) noted that the X-ray emission seen in EX Lupi is also likely due to accretion shocks. The X-ray luminosity of EX Lupi was $1.7\times10^{30}~erg~s^{-1}$ during the outburst (cite: grosso10). Using the relation for X-ray luminosity to expected radio flux from free-free emission outlined in (cite: pascucci12):

$$\begin{equation}
    F_{3.5 \,cm} = 2.4 \times 10^{-29} ~ \Big(\frac{51}{d} \Big)^{2} ~ L_{x} ~ [\mu Jy],
\end{equation}$$

where F$_{3.5\, \rm cm}$ is the 3.5 cm flux, d is the distance to the source in pc and L$_{X}$ is the X-ray luminosity in $\rm erg~s^{-1}$, we find an expected flux of 4.3 $\mu$Jy. Free-free emission should have an approximately flat spectral index meaning the expected flux at 15 GHz (2 cm) should also be $\sim4.3~\mu$Jy. It is therefore possible that free-free emission accounts for up to $10\%$ of the observed 15 GHz flux. We note though that since the post-outburst X-ray luminosity should be lower than that observed by (cite: grosso10), the expected post-outburst radio flux should be lower as well.

Considering all of the potential sources of the 15 GHz emission, we find that the most likely scenario is a combination of (gyro)synchrotron and free-free emission. We note though that follow-up observations at lower frequencies are needed to confirm the spectral index. It is indeed possible that there is a combination of more emission mechanisms present at 15 GHz. In order to disentangle all the potential sources of emission, $1-15$ GHz observations with both high angular resolution and sensitivity are necessary. The VLA is currently the leading facility in this regime and the observations presented are already pushing the limits of its capabilities. Therefore, proposed future facilities, such as the ngVLA (cite: white18), will be key to fully understanding the underlying emission mechanisms in EX Lupi and connecting them in the broader context of EXor/FUors in general.

# Summary

In this paper, we presented ALMA and VLA continuum observations of the EX Lupi disk in its post-outburst state. We fit radiative transfer models of the circumstellar dust and find the models are consistent with grain growth up to at least 3 mm, and possibly as high as 1 cm. The grain growth could have been spurred by the recent outburst, which ended in 2008. The best fit disk model has an ice line located at $0.2-0.3$ au in the disk’s midplane, and the associated cooling timescales show there as been adequate time for the ice line to migrate inward from the observed position during the outburst. The most probable value for the total disk mass is 0.01 M$_{\odot}$, accompanied by a relatively compact characteristic dust radius of 45 au. The size is in agreement with other studies that find EXor/FUor disks to be more compact than that of typical protoplanetary disks.

We find a best fit flux of 0.055 mJy at 15 GHz, significantly more than can be explained by thermal disk emission alone. We explored several potential sources of the emission and conclude that it is likely primarily due to (gyro)synchrotron emission coming from strong stellar magnetic fields and/or non-negligible free-free emission from accretion shocks and disk heating through X-ray emission.

# Acknowledgments

We thank the anonymous referee for feedback that improved this paper. This project received support from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation program under grant agreement No 716155 (SACCRED). DS acknowledges support by the Deutsche Forschungsgemeinschaft through SPP 1833: “Building a Habitable Earth” (SE 1962/6-1). EV and VA acknowledge the support of the Large Scientific Project of the Russian Ministry of Science and Higher Education “Theoretical and experimental studies of the formation and evolution of extrasolar planetary systems and characteristics of exoplanets” (No. 13.1902.21.0039). On behalf of the SACCRED project we are thankful for the usage of MTA Cloud (https://cloud.mta.hu/) that helped us achieving the results published in this paper. This paper makes use of the ALMA data from projects ADS/JAO.ALMA#2017.1.00224.S and ADS/JAO.ALMA#2015.1.00200.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Facilities

ALMA, VLA

# Software

CASA 5.4.1 (cite: casa_reference)

(ref: abraham09) Ábrahám, P., Juhász, A., Dullemond, C.P., et al., 2009, Nat, 459(7244), pp.224-226.

(ref: abraham19) Ábrahám, P., Chen, L., Kóspál, Á., et al., 2019, ApJ, 887(2), p.156.

(ref: andrews09) Andrews, S.M., Wilner, D.J., Hughes, A.M., et al., 2009, ApJ, 700(2), p.1502.

(ref: andrews18) Andrews, S.M., Huang, J., Pérez, L.M., et al., 2018, ApJL, 869(2), p.L41.

(ref: ansdell16) Ansdell, M., Williams, J.P., van der Marel, N., et al., 2016, ApJ, 828(1), p.46.

(ref: armitage16) Armitage, P.J., 2016, ApJL, 833(2), p.L15.

(ref: audard14) Audard, M., Ábrahám, P., Dunham, M.M., et al., 2014, Protostars & Planets VI, 387.

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: bailer18) Bailer-Jones, C.A.L., Rybizki, J., Fouesneau, M., et al., 2018, AJ, 156(2), p.58.

(ref: banzatti12) Banzatti, A., Meyer, M.R., Bruderer, S., et al., 2012, ApJ, 745(1), p.90.

(ref: banzatti19) Banzatti, A., Pascucci, I., Edwards, S., et al., 2019, ApJ, 870(2), p.76.

(ref: baryshev15) Baryshev, A.M., Hesper, R., Mena, F.P., et al., 2015, A&A, 577, A129

(ref: berger01) Berger, E., Ball, S., Becker, K. M., et al. 2001, Natur, 410, 338

(ref: booth16) Booth, M., Jordán, A., Casassus, S., et al., MNRAS, 460(1), pp.L10-L14.

(ref: bouvier07) Bouvier, J., Alencar, S. H. P., Harries, T. J., et al., 2007, Protostars & Planets V

(ref: brauer08) Brauer, F., Henning, T., & Dullemond, C.P., 2008, A&A, 487(1), pp.L1-L4.

(ref: brogan15) Brogan, C.L., Pérez, L.M., Hunter, T.R., et al., 2015, ApJL, 808(1), p.L3.

(ref: brown90) Brown, P.D. & Charnley, S.B., 1990, MNRAS, 244, pp.432-443.

(ref: cambresy99) Cambrésy, L. 1999, A&A, 345, 965

(ref: cieza16) Cieza, L.A., Casassus, S., Tobin, J., et al., 2016, Nature, 535(7611), p.258.

(ref: cieza18) Cieza, L. A., Ruíz-Rodríguez, D., Perez, S., et al. 2018, MNRAS, 474, 4347

(ref: dangelo12) D’Angelo, C. R., Spruit, H. C., 2012, MNRAS, 420, 416

(ref: donati05) Donati, J., Paletou, F., Bouvier, J. et al., 2005, Nat., 438, 466-469

(ref: dorschner95) Dorschner, J., Begemann, B., Henning, T., et al., 1995, A&A, 300, 503

(ref: dulk85) Dulk, G. A., 1985, ARA&A, 23, 169

(ref: dullemond12) Dullemond, C.P., Juhász, A., Pohl, A., et al. , 2012, Astrophysics Source Code Library, ascl:1202.015

(ref: flock17) Flock, M., Nelson, R.P., Turner, N.J., et al., 2017, ApJ, 850(2), p.131.

(ref: frasca17) Frasca, A., Biazzo, K., Alcala, J. M., et al. 2017, A&A, 602, A33

(ref: grosso10) Grosso, N., Hamaguchi, K., Kastner, J.H., et al., 2010, A&A, 522, p.A56.

(ref: hales18) Hales, A.S., Pérez, S., Saito, M., et al., 2018, ApJ, 859(2), p.111.

(ref: hartmann96) Hartmann, L., & Kenyon, S. J. 1996, ARA&A, 34, 207

(ref: herbig66) Herbig, G.H., 1966, Vistas in Astronomy, 8, pp.109-125.

(ref: herbig07) Herbig, G.H., 2007, AJ, 133(6), p.2679.

(ref: hughes19) Hughes, A.G., Boley, A.C., Osten, R.A.,et al., 2019, ApJ, 881(1), p.33.

(ref: hughes17) Hughes, A.G., Boley, A.C., 2017, MNRAS, 472(3), pp.3543-3553.

(ref: johansen17) Johansen, A., Lambrechts, M., 2017, AREPS, 45, pp.359-387.

(ref: johnskrull07) Johns-Krull, C.M., 2007, ApJ, 664(2), p.975.

(ref: johnskrull09) Johns-Krull, C.M., Greene, T.P., Doppmann, G.W., et al., 2009, ApJ, 700(2), p.1440.

(ref: kenyon00) Kenyon, S. J., Kolotilov, E. A., Ibragimov, M. A., et al., 2000, ApJ, 531, 1028

(ref: kospal11) Kóspál, Á., Ábrahám, P., Goto, M., et al., 2011, ApJ, 736(1), p.72.

(ref: kospal20) Kóspál, Á., Donati, J.F., Bouvier J., et al., 2020, IAUGA, 125

(ref: lecar06) Lecar, M., Podolak, M., Sasselov, D., et al., 2006, ApJ,, 640(2), p.1115.

(ref: lin15) Lin, M.-K., & Youdin, A. N., 2015, ApJ, 811, 17

(ref: lombardi08) Lombardi, M., Lada, C. J. Alves, J., 2008, A&A, 480, 785

(ref: casa_reference) McMullin J.P., Waters B., Schiebel D., et al., 2007, Astronomical Data Analysis Software and Systems XVI (ASP Conf. Ser. 376), ed. R. A. Shaw, F. Hill, & D. J. Bell (San Francisco, CA: ASP), 127

(ref: min05) Min, M., Hovenier, J. W., & de Koter, A. 2005, A&A, 432, 909

(ref: molyarova18) Molyarova, T., Akimkin, V., Semenov, D., et al., 2018, ApJ, 866(1), p.46.

(ref: morbidelli16) Morbidelli, A., Raymond, S.N., 2016, JGRP, 121(10), pp.1962-1980.

(ref: pacholczyk70) Pacholczyk, A.G., 1970, Radio astrophysics: Nonthermal processes in galactic and extragalactic sources.

(ref: pascucci12) Pascucci, I., Gorti, U., & Hollenbach, D., 2012, ApJL, 751(2), p.L42.

(ref: poetzel89) Poetzel, R., Mundt, R., Ray, T.P., 1989, A&A, 224, pp.L13-L16.

(ref: rab17) Rab, C., Elbakyan, V., Vorobyov, E., et al., 2017, A&A, 604, A15

(ref: rodriguez03) Rodríguez, L.F., Porras, A., Claussen, M.J., et al., 2003, ApJL, 586(2), p.L137.

(ref: ros13) Ros, K. & Johansen, A., 2013, A&A, 552, p.A137.

(ref: aguilar12) Sicilia-Aguilar, A., Kóspál, Á., Setiawan, J., et al., 2012, A&A, 544, A93

(ref: aguilar15) Sicilia-Aguilar, A., Fang, M., Roccatagliata, V., et al., 2015, A&A, 580, p.A82.

(ref: sipos09) Sipos, N., Ábrahám, P., Acosta-Pulido, J., et al., 2009, A&A, 507(2), pp.881-889.

(ref: toon81) Toon, O. & Ackerman, T., 1981, Applied Optics 20, 3657

(ref: turnpenney18) Turnpenney, S., Nichols, J.D., Wynn, G.A., et al., 2018, ApJ, 854(1), p.72.

(ref: white_fom) White, J. A., Boley, A. C., Dent, W. R. F., et al., 2017a, MNRAS, 466(4), p.4201

(ref: white18) White, J.A., Audard, M., Ábrahám, P., et al., 2018, Science with a Next Generation Very Large Array, ASP Conference Series, (Vol. 517, p. 177), Edited by Eric Murphy

(ref: white19) White, J.A., Kóspál, Á., Rab, C., et al., 2019, ApJ, 877(1), p.21.

(ref: williams14) Williams, P.K.G., Cook, B.A., & Berger, E., 2014, ApJ, 785, 9

(ref: woitke16) Woitke, P., Min, M., Pinte, C., et al., 2016, A&A, 586, p.A103

(ref: vorobyov15) Vorobyov, E.I., & Basu, S., 2015, ApJ, 805(2), p.115

(ref: zhang15) Zhang, K., Blake, G.A., & Bergin, E.A., 2015, ApJL, 806(1), p.L7.

(ref: zhu09) Zhu, Z., Hartmann, L., & Gammie, C., 2009, ApJ, 694(2), p.1045.

(ref: zubko96) Zubko, V.G., Mennella, V., Colangeli, L., et al.. 1996, MNRAS, 282, 1321

[^1]: For a note on the VLA flux calibration uncertainty, see science.nrao.edu/facilities/vla/docs/manuals/oss/performance/fdscale.

[^2]: http://www.ast.cam.ac.uk/ juhasz/radmc3dPyDoc/index.html

[^3]: The OpacityTool Software was obtained from https://dianaproject.wp.st-andrews.ac.uk/data-results-downloads/fortran-package/

</paper>

Write the methods card for this paper.