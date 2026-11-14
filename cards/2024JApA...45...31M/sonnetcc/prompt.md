# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024JApA...45...31M\sonnetcc\reply.txt

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
 "bibcode": "2024JApA...45...31M",
 "title": "ALMA detection of hydrogen cyanide in the atmosphere of Saturn",
 "year": 2024,
 "journal": "Journal of Astrophysics and Astronomy",
 "first_author": "Manna, Arijit",
 "n_authors": 2,
 "arxiv_id": "2104.10474",
 "doi": "10.1007/s12036-024-10024-w",
 "alma_projects_linked_by_archive": [
  "2017.1.00636.S"
 ]
}
```

Paper text:
<paper>
# ALMA detection of hydrogen cyanide (HCN) in the atmosphere of Saturn

# Introduction

In the planetary atmosphere, hydrogen cyanide (HCN) is an important nitrogen (N)-bearing molecule for the synthesis of several complex organic molecules (cite: tok81; ka83). The HCN molecule contains a –C $\equiv$ N functional group, which plays a major role in the formation of peptides, nucleic acids, amino acids, and both nucleobases, that can be the building blocks of DNA and RNA in the planetary atmosphere (cite: mil57; oro61). The HCN molecule may play an important role in the formation of adenine (C$_{5}$H$_{5}$N$_{5}$) via the neutral-neutral reactions (cite: oro61). Adenine is one of the nucleobases of DNA and RNA and plays a major role in the origin of life in the possible primitive Earth conditions (cite: oro61). HCN molecules may also be responsible for the production of chromophores in planetary atmospheres (cite: wo69). The HCN molecule acts as a potential tracer of disequilibrium processes such as the transport of materials from the deep atmosphere or lightning (cite: le80). In a planetary atmosphere, HCN is mainly formed via the dissociation of methane (CH$_{4}$) and nitrogen (N$_{2}$) (cite: cat07; per19). Several energy sources can dissociate CH$_{4}$ and N$_{2}$ in planetary atmospheres, including galactic cosmic rays, lightning, and ultraviolet light (cite: per19; per20).

In our solar system, Saturn’s moon Titan had the most HCN-rich atmosphere because of its high atmospheric C/O ratio (cite: rim19). Earlier, four instruments aboard the Cassini spacecraft detected the HCN from the lower ($<$600 km) and upper ($>$700 km) atmospheres of Titan with mixing ratios of $\sim$0.1–10 ppm (parts per million) and $\sim$0.1%–5% (parts per thousand) (cite: mag09; vin10; ad11; kos11). The galactic cosmic rays and ultraviolet lights are responsible for dissociating CH$_{4}$ and N$_{2}$ to create radical compounds in the upper and lower atmospheres of Titan (cite: gro09; gro11; vui19). The emission lines of HCN were also detected in the atmospheres of Neptune and Pluto, with abundances of $\sim$1 ppb (parts per billion) and $\sim$40 ppm, respectively, (cite: mar93; lel17). (cite: ii20) detected the belt-like distribution of HCN in the atmosphere of Neptune using the ALMA. In the equatorial region and 60$^{\circ}$ S of Neptune, the abundance of HCN is 1.66 ppb and 1.17 ppb, respectively (cite: ii20). The concentration of HCN in the upper atmosphere of Uranus is 0.1 ppb (cite: mar93). Previously, (cite: tok81) detected HCN from Jupiter with a mixing ratio of 2$\times$10$^{-9}$.

![](cont.pdf)

In our solar system, the study of HCN in the atmosphere of Saturn at sub-millimeter wavelengths is important because HCN acts as a possible precursor of many major prebiotic molecules (cite: lel84). In the last several years, scientists have attempted to detect evidence of HCN in the atmosphere of Saturn without success. Earlier, (cite: tok81) searched for evidence of HCN in the atmosphere of Saturn in the infrared wavelength range, but they did not find any evidence of HCN in the atmosphere of Saturn because of the lower signal-to-noise ratio (SNR). (cite: tok81) calculated the upper-limit mixing ratio of HCN in Saturn’s atmosphere to be $\leq$5$\times$10$^{-10}$. Earlier, (cite: ka83) suggested that the HCN mixing ratio in the atmosphere at Saturn is 5$\times$10$^{-10}$, which was estimated based on photochemical reactions. According to (cite: lel84), the submillimeter spectral range is the best for searching for evidence of HCN in Saturn’s atmosphere because, using the heterodyne technique, the possibility of HCN line resolving power is at least 10$^{6}$ and the four strongest HCN rotational lines lie between 800 $\mu$m and 3 mm.

In this letter, we present the detection of the rotational emission line of HCN in the atmosphere of Saturn using ALMA. In Section [2](#sec:obs), we briefly describe our observations and data reduction. The result and discussion of the detection of HCN are described in Section [3](#sec:emi). The conclusion is presented in Section [4](#sec:con).

![](spec.pdf)

![](HCN.pdf)

# Observation and data reductions

We used the archival data of the solar gas planet Saturn, which was observed using the high-resolution Atacama Large Millimeter/Submillimeter Array (ALMA) band 7 with a 12 m array (PI: Fouchet, Thierry). The objective of this observation was to directly measure Saturn’s stratospheric winds using the emission lines of hydrogen cyanide (HCN) with transition J = 4–3 and carbon monoxide (CO) with transition J = 3–2. Saturn was observed on May 25, 2018, with the phase centre of ($\alpha,\delta$)$\rm J2000$ = 18:37:56.412, –22:15:52.617. During the observation, a total of forty-four antennas were used, with an on-source integration time of 476.40 sec. The observed frequency ranges were 340.98–342.96 GHz, 342.98–344.96 GHz, 354.42–354.54 GHz, and 354.98–356.96 GHz, with spectral resolutions of 1128.91 kHz, 70.56 kHz, 282.23 kHz, and 1128.91 kHz, respectively. During the observation, the angular diameter of Saturn was 17.44$^{\prime\prime}$, the geocentric distance was 9.21 AU, and the angular resolution was 0.70$^{\prime\prime}$, 0.78$^{\prime\prime}$, 0.82$^{\prime\prime}$, and 0.85$^{\prime\prime}$ for the corresponding frequency ranges of 340.98–342.96 GHz, 342.98–344.96 GHz, 354.42–354.54 GHz, and 354.98–356.96 GHz, respectively. The minimum and maximum baselines during the observation were 15.0 m and 313.7 m. As a result of the lack of short spacing with the interferometer, the disk flux of Saturn is filtered out, and only the emission from the limbs is preserved. The shortest baseline observation can directly measure Saturn’s stratospheric winds between the eastern and western limbs. During the Saturn observation, the flux and bandpass calibrators were taken as J1750+0939, and the phase calibrator was taken as J1832–2039. Previously, (cite: ben22) also used this data, but the authors did not focus on studying the mixing ratio, vertical distribution, and formation pathways of HCN in the atmosphere of Saturn.

After downloading the archival raw data of Saturn from the ALMA archive, we used the Common Astronomy Software Application (`CASA 5.4.1`) with a standard data reduction pipeline delivered by the ALMA observatory for data analysis and imaging (cite: m07). We imported the ALMA data into CASA using task `IMPORTASDM`. During the data analysis, we used the Perley-Butler 2017 flux calibrator model to match the continuum flux density of the flux calibrator with 5% accuracy using the task `SETJY` in CASA (cite: pal17). We applied the CASA pipeline tasks `hifa_bandpassflag` and `hifa_flagdata` to remove the bad antenna data. During the bandpass calibration, we carefully removed the telluric effect from the data by flagging the channels where the telluric absorption lines were observed. We do not observe any telluric lines near the lines of CO and HCN. We found a strong telluric absorption line of ozone (O$_{3}$) at a frequency of 355.01 GHz, and we removed that line during the data analysis. After the flux, bandpass, and gain calibration, we separated the target dataset into another dataset using the task `MSTRANSFORM` with all available rest frequencies. After splitting the target data, we used task `TCLEAN` with the `HOGBOM` algorithm to create the continuum image of Saturn. We used the line-free channels during the production of the continuum emission images. After that, we used the CASA task `UVCONTSUB` for continuum subtraction because continuum subtraction is essential for studying the spectral line. After continuum subtraction, we used the task `TCLEAN` with the `SPECMODE = CUBE` parameter for each rest frequency to create the spectral data cubes of Saturn. To correct the primary beam pattern in the synthesized image, we applied the `IMPBCOR` task in the CASA. The data analysis flowchart is shown in Figure A1.

# Result and discussion

![](retrival.pdf)

## Continuum emission towards Saturn

We present the 856.19 $\mu$m (350.14 GHz) wavelength continuum emission image of the gas planet Saturn in Figure [1](#fig:cont). The surface brightness colour scale in the continuum image has units of a Jy beam$^{-1}$. In the continuum image, the ring pattern of Saturn is clearly visible at sub-millimeter wavelengths. The synthesized beam size of the continuum image was 0.78$^{\prime\prime}\times$0.61$^{\prime\prime}$. The disk average (except ring) continuum flux density of Saturn is 1.60$\pm$0.35 Jy beam$^{-1}$. We estimate the flux density by drawing a 16$^{\prime\prime}$ circle over the disk part of planet. We do not estimate the flux densities of rings because it is very difficult due to their complex structure.

## Line emission towards Saturn

From the spectral data cubes, we find that the emission line of HCN with transition J = 4–3, whose rest frequency is 354.505 GHz, originates from both the eastern and western limbs of Saturn. We do not detect any line emissions from the equatorial region of Saturn. We also checked the TGSS, NVSS, and Spitzer sky survey data using the coordinates of Saturn, but we did not observe any source close to the limb. The channel maps of HCN in the atmosphere of Saturn is shown in Figure A2. The channel maps clearly indicates the HCN molecule circulating from the eastern limb to the western limbs of Saturn via the north pole. We extract the molecular emission spectra from the eastern and western limbs of the spectral data cubes of Saturn. For spectral extraction, we created a $2.7^{''}$ diameter circular region in the eastern limb of Saturn centred at RA (J2000) = (18$^{h}$35$^{m}$51.873$^{s}$), Dec (J2000) = (–22$^\circ$19$^{\prime}$27$^{\prime\prime}$.982). We applied the same method for spectral extraction from the western limb. We created a $2.7^{''}$ diameter circular region in the western limb centred at RA (J2000) = (18$^{h}$33$^{m}$53.128$^{s}$), Dec (J2000) = (–22$^\circ$19$^{\prime}$29$^{\prime\prime}$.406). The extracted spectra of HCN from the eastern and western limbs of Saturn are shown in Figure [2](#fig:SPEC). In Figure. [2](#fig:SPEC), the center position (i.e., 0 km s$^{-1}$) is the theoretical peak position of the HCN (354.505 GHz), but we find that the HCN spectra in the eastern limb (red line) is shifted –9.2 km s$^{-1}$ (354.516 GHz) from the center (i.e., 0 km s$^{-1}$), and for the western limb (black line), the peak of the HCN is shifted to 8.36 km s$^{-1}$ (354.494 GHz). This spectral shift could have been caused by strong stratospheric winds between the eastern and western limbs of Saturn. Earlier, (cite: ca10) also showed the millimeter-wavelength spectral line of Saturn is shifted –9.2 km s$^{-1}$ for the eastern limb line-of-sight and 7.7 km s$^{-1}$ for the western limb line-of-sight using the atmospheric radiative transfer model. Our estimated shift in the HCN emission line for both the eastern and western limbs is similar to that of (cite: ca10). Except for HCN, we also detected emission lines of CO (J = 3–2) at a frequency of 345 GHz from the eastern and western limbs of Saturn. We did not observe any other complex molecules that are chemically connected to HCN, such as CH$_{2}$NH. We did not present the CO emission line in this paper because the emission line of CO is a known molecule in the stratosphere of Saturn (cite: no86; ca09).

![](limb.pdf)

## Determination of the abundance of HCN

To determine the abundance of HCN in the atmosphere of Saturn, we used the Planetary Spectrum Generator (PSG, (cite: vil18)). PSG is a radiative transfer suite for spectrum simulation of the solar planets, exoplanets, comets, and other minor objects in our solar system. PSG combines radiative transfer modelling, planetary ephemeris databases (using JPL), and spectroscopic molecular databases to demonstrate the simulated spectra. During the computation of the simulated spectra, we used the line-by-line and correlated-k approaches for better spectral resolution. PSG is also able to fit the modelled spectra of the detected molecules over the observed spectra to determine the abundance of those molecules and the temperature and altitude of the atmospheric levels (cite: vil18). For spectral modelling, the pressure levels of the vertical atmospheric structure ranged from 10 to 100 $\mu$bar with 60 atmospheric layers. The atmospheric layers are taken from (cite: mos05). For the temperature profile, we used the disk-averaged retrieved result from (cite: lel84). We used the HITRAN molecular database for spectroscopic parameters to obtain the abundance of HCN from the western and eastern limbs of Saturn. For fitting the modelled spectra of atmospheric HCN over the observed spectra of HCN, we used the least-squares method, which is well described in (cite: ii20). During the spectral fitting, the velocity of the western limb spectra is fixed at 8.36 km s$^{-1}$. Similarly, the velocity of the eastern limb spectra is fixed at –9.26 kms$^{-1}$. After spectral fitting, the derived vertical mixing ratios (VMR) of HCN towards the western and eastern limbs of Saturn are 6.19 ppb and 2.90 ppb, respectively. The modelled fitted spectral line of HCN is shown in Figure [3](#fig:HCNSPEC). Earlier, (cite: lel84) simulated the VMR in the atmosphere of Saturn to be 3.58 ppb, which is nearly similar to our observed abundance of HCN in the atmosphere of Saturn.

## Retrieval profile of HCN

To understand the distribution of HCN in the atmosphere of Saturn, we computed the VMR retrieval profile of HCN using the PSG. We used the optimal estimation method to compute the retrieval model of HCN using the PSG. The pressure levels in the retrieval profile were between 10 bar and 100 $\mu$bar. The temperature profile derived from the disk-averaged result was obtained from (cite: lel84). For the vertical abundance profiles of CH$_{4}$, C$_{2}$H$_{6}$, C$_{2}$H$_{2}$, NH$_{3}$, and NH$_{4}$SH, except for the HCN, we use default values available in PSG (cite: mos05). During the VMR analysis of HCN, spectroscopic parameters of HCN are obtained from the HITRAN database. In the VMR retrieval profile of the HCN on Saturn, we used 60 atmospheric layers in the PSG (cite: mos05). To compute the retrieval profile, we used the abundance of HCN at 6.19 ppb (western limb) and 2.90 ppb (eastern limb) in the PSG. In the retrieval profile, we find that the VMR of HCN is saturated at a pressure level of 0.001 bar. This means that the HCN molecule is distributed up to 475 km in the stratosphere of Saturn. To understand the temperature of the HCN, we also generated the temperature-pressure (TP) retrieval profile of Saturn within a pressure level of 10 bar to 100 $\mu$bar using the PSG. The TP profile clearly shows that the temperature is saturated at a pressure level of 0.001 bar, and within this pressure level, the temperature varies between 100 and 250 K. The TP and VMR retrival profiles of the HCN in the atmosphere of Saturn are shown in Figure [4](#fig:retrival).

## Spatial distribution of HCN in Saturn

We create an integrated emission map of the HCN in Saturn using the task `IMMOMENTS` in CASA. Integrated emission maps are created by integrating the spectral data cubes in the velocity ranges where the emission line of the HCN is detected. After the generation of the integrated emission map, we find that the emission line of HCN emits from the eastern and western limbs of Saturn. We overplot the integrated emission map of HCN over the 856.19 $\mu$m continuum emission map of Saturn to determine the proper location of HCN emissions in Saturn. The integrated emission map and the overplotted map are shown in Figure [5](#fig:limb). We observe that the integrated map of HCN is resolved because the line emitting region is larger than the synthesized beam of the integrated emission map.

## Possible formation mechanism of HCN in the atmosphere of Saturn

Earlier, (cite: tok81) claimed that the formation mechanism of HCN in the atmosphere of Saturn is similar to that of Jupiter. (cite: tok81) stated that the photolysis of CH$_{4}$ and NH$_{3}$ is the most likely pathway for the formation of HCN in both Saturn and Jupiter. The laboratory experiment by (cite: rau79) shows that HCN can be produced by photochemical reactions in a mixture of H$_{2}$, CH$_{4}$, and NH$_{3}$ under ultraviolet light. During the experiment, (cite: rau79) observed that NH$_{3}$ abundance is low in the stratosphere of Jupiter, and most of the HCN is produced by photolysis reactions in the lower stratosphere and upper troposphere of Jupiter. If this mechanism holds true in Saturn’s atmosphere, the abundance of HCN in Saturn is lower than that in Jupiter because Saturn’s atmosphere contains a much lower abundance of NH$_{3}$ (cite: enc74; tok81). (cite: tok81) calculated the mixing ratio of HCN in Jupiter’s atmosphere to be (0.9–4.2)$\times$10$^{-9}$, and we calculated the mixing ratio of HCN in Saturn’s atmosphere to be (2.90–6.19) ppb. This comparison indicates that the abundance of HCN in the atmosphere of Saturn is slightly less than the abundance of HCN in the atmosphere of Jupiter. This implies that the laboratory experiment of (cite: rau79) is valid in the atmosphere of Saturn, i.e., the HCN in the atmosphere of Saturn is produced by the photolysis of CH$_{4}$ and NH$_{3}$. Further photochemical modelling is needed to establish the most efficient pathways for the production of HCN in the atmosphere of Saturn. 

# Conclusion

In this paper, we analyzed the ALMA band 7 data for Saturn. The main results are as follows:\
$\bullet$We successfully detected the rotational emission line of HCN with transition J = 4–3 from the atmosphere of Saturn using ALMA.\
$\bullet$We observe that the emission line of the HCN mainly arises from the eastern and western limbs of Saturn.\
$\bullet$ The derived abundances of HCN in the western and eastern limbs are 6.19 ppb and 2.90 ppb, respectively. We also computed the TP and VMR retrieval profiles using the PSG. After retrieval analysis, we observed that the HCN is distributed up to 475 km in the stratosphere of Saturn. Similarly, from the TP profile, the temperature of HCN varied between 100 and 250 K.\
$\bullet$We also discuss the possible formation mechanism of HCN towards Saturn and claim that the photolysis of CH$_{4}$ and NH$_{3}$ is responsible for the production of HCN.

# ACKNOWLEDGEMENTS

We thank the anonymous reviewers for her/his constructive comments that helped improve the manuscript. AM acknowledges the Swami Vivekananda Merit-cum-Means Scholarship (SVMCM) for financial support for this research. This paper makes use of the following data:\
ADS /JAO.ALMA#2017.1.00636.S. ALMA is a partnership of ESO, NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

natexlab

(ref: ad11) Adriani, A., Dinelli, B. M., López-Puertas, M., et al. 2011, Icar, 214, 584

(ref: ben22) Benmahi, B., Cavalié, T., Fouchet, T., et al. 2022, A&A, 666, A117

(ref: cat07) Catling, D., & Kasting, J. F. 2007, in Planetary Atmospheres and Life, ed. W. T. Sullivan, III & J. A. Baross (Cambridge: Cambridge Univ. Press), 91

(ref: ca09) Cavalié, T., Billebaud, F., Dobrijevic, M., et al. 2009, Icarus, 203, 531

(ref: ca10) Cavalié, T., et al. 2010, A&A, 510, A88.

(ref: enc74) Encrenaz, TH., Owen, T., Woodman, J. H. 1974, A&A, 37, 49-55.

(ref: gro09) Gronoff, G., Lilensten, J., Desorgher, L., & Fluckiger, E. 2009, A&A, 506, 955

(ref: gro11) Gronoff, G., Mertens, C., Lilensten, J., et al. 2011, A&A, 529, A143

(ref: ii20) Iino, T., Sagawa, H., Tsukagoshi, T., Nozawa, S., 2020, APJL, 903, L1

(ref: ka83) Kaye, J. A. and Strobel, D. F., 1984, Icarus, 59, 314

(ref: kos11) Koskinen, T. T., Yelle, R. V., Snowden, D. S., et al. 2011, Icar, 216, 507

(ref: le80) Lewis, J. S. 1980, Icarus 43, 85-95

(ref: lel84) Lellouch, E., Encrenaz, T., & Combes, F. 1984, A&A, 135, 371

(ref: lel17) Lellouch, E., Gurwell, M., Butler, B., et al. 2017, Icar, 286, 289

(ref: mil57) Miller, S. L. 1957, Biochim. Biophys. Acta, 23, 480

(ref: mos05) Moses, J. I. 2005, JGRE, 110, E08001

(ref: m07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mu05) Müller, H. S. P., SchlM$\ddot{o}$der, F., Stutzki, J. & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215–227

(ref: mag09) Magee, B. A., Waite, J. H., Mandt, K. E., et al. 2009, P&SS, 57, 1895

(ref: mar93) Marten, A., Gautier, D., Owen, T., et al. 1993, ApJ, 406, 285

(ref: no86) Noll, K. S., Knacke, R. F., Geballe, T. R., Tokunaga, A. T., 1986, ApJL, 309, L91

(ref: oro61) Oró, J. 1961, Nature, 191, 4794

(ref: pal17) Perley, R. A., Butler, B. J. 2017, ApJ, 230, 1538

(ref: per19) Pearce, B. K. D., Ayers, P. W., & Pudritz, R. E. 2019, JPCA, 123, 1861

(ref: per20) Pearce, B. K. D., Molaverdikhani, K., Pudritz, R. E., Henning, T., & Hébrard, E. 2020, Astrophys. J, 901, 110

(ref: pic98) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, Journal of Quantitative Spectroscopy and Radiative Transfer, 60, 883

(ref: rau79) Raulin, F., Bossard, A., Toupance, G., Ponnamperuma, C. 1979, Icarus 38, 358-366

(ref: rim19) Rimmer, P. B., & Rugheimer, S. 2019, Icar, 329, 124

(ref: tok81) Tokunaga, A. T., Beck, S. C., Geballe, T. R., Lacy, J. H., & Serabyn, E. 1981, Icarus, 48, 283

(ref: van07) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., van Dishoeck, E. F., 2007, A&A, 468, 2

(ref: vil18) Villanueva, G. L., Smith, M. D., Protopapa, S., Faggi, S., & Mandell, A. M. 2018, JQSRT, 217, 86

(ref: vin10) Vinatier, S., Bézard, B., Nixon, C. A., et al. 2010, Icar, 205, 559

(ref: vui19) Vuitton, V., Yelle, R. V., Klippenstein, S. J., Horst, S. M., & Lavvas, P. 2019, Icar, 324, 120

(ref: wo69) Woeller, F., & Ponnamperuma, C,. 1969. Icarus 10, 386-392

Appendix ![image](flowchart.pdf)

![](linemap.pdf)

</paper>

Write the methods card for this paper.