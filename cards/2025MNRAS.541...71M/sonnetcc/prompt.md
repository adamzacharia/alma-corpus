# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025MNRAS.541...71M\sonnetcc\reply.txt

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
 "bibcode": "2025MNRAS.541...71M",
 "title": "ALMA millimetre-wavelength imaging of HD 138965: new constraints on the debris dust composition and presence of planetary companions",
 "year": 2025,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Marshall, J. P.",
 "n_authors": 13,
 "arxiv_id": "2506.11726",
 "doi": "10.1093/mnras/staf984",
 "alma_projects_linked_by_archive": [
  "2019.1.01220.S"
 ]
}
```

Paper text:
<paper>
# ALMA millimetre-wavelength imaging of HD 138965: New constraints on the debris dust composition and presence of planetary companions

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

# Abstract

HD 138965 is a young A type star and member of the nearby young Argus association. This star is surrounded by a broad, bright debris disc with two temperature components that was spatially resolved at far-infrared wavelengths by *Herschel*. Here we present ALMA millimetre-wavelength imaging of the cool outer belt. These reveal its radial extent to be 150$^{+10}_{-7}$ au with a width ($\sigma$) of 49$^{+7}_{-6}$ au ($\Delta R/R = 0.77$), at a moderate inclination of 49.9$^\circ$$^{+3.3}_{-3.7}$. Due to the limited angular resolution, signal-to-noise, and inclination we have no constraint on the disc’s vertical scale height. We modelled the disc emission with both gravitational and radiation forces acting on the dust grains. As the inner belt has not been spatially resolved, we fixed its radius and width prior to modelling the outer belt. We find astronomical silicate is the best fit for the dust composition. However, we could not reject possible scenarios where there are at least 10% water-ice inclusions. Combining the spatially resolved imaging by ALMA with non-detection at optical wavelengths by *HST*, we obtain a limit on the scattering albedo $\omega \leq 0.09$ for the debris dust in the outer belt. Analysis of the outer belt’s architecture in conjunction with simple stirring models places a mass limit of 2.3 $\pm$ 0.4 $M_{\rm Jup}$ on a companion interior to the belt ($a \leq$ 78 au), a factor of two improvement over constraints from high contrast imaging.

circumstellar matter – radio continuum: planetary systems – planet-disc interactions – stars: individual: HD 138965

# Introduction

Main sequence stars play host to both planets and belts of planetesimals. Dynamical interaction between the components can excite the motions of the planetesimals to such a degree that a collisional cascade is triggered generating detectable amounts of dust. The dust produced in the collisional cascade is most commonly detected at optical or near-infrared wavelengths as scattered light (cite: 2020Esposito; 2023Ren; 2023bMarshall; 2024Crotts) or at infrared to millimetre wavelengths as thermal emission (cite: 2013Eiroa; 2013Kennedy; 2016Montesinos; 2017Holland; 2025Matra). Due to their origins in destructive processes, these dusty structures are collectively referred to as ‘debris discs’ (cite: 2008Wyatt; 2018Hughes).

These debris discs are larger and more massive analogues to the Solar system’s Asteroid or Edgeworth-Kuiper belts (cite: 2020Horner). There is some dependence of disc detection on the stellar luminosity, with the highest detection rate found around A stars (cite: 2014Thureau), an intermediate fraction around FGK stars (cite: 2018Sibthorpe), and the lowest detection rate around M dwarfs (cite: 2009Lestrade; 2018Kennedy). However, these detections are strongly sensitivity limited at levels of fractional luminosity around ten times greater than that predicted for dust in the Solar system (cite: 2012Vitense). As such, the supposed lack of cold debris discs around M dwarf stars could be a result of that limitation (cite: 2020Luppe; 2023Cronin). Likewise, there is a dependence on disc detection with age. All else being equal, younger stars have brighter debris discs (cite: 2007Wyatt; 2011Kains). This is consistent with debris discs originating from the steady collisional grinding of parent bodies into dust over the lifetime of the system (cite: 2022Najita). That said, the interstellar medium (ISM) can influence the morphology of debris discs throughout their life (cite: 2025Heras). As such, young stars with reliable ages (e.g. in moving groups) make favourable targets for the detection and characterisation of both debris discs and planetary companions.

HD 138965 is a young A star lying at a distance of 78.60 $\pm$ 0.17 pc (cite: 2016Gaia; 2023aGaia; 2023bGaia). It has been identified as a member of the 40 to 50 Ma Argus association (cite: 2019Zuckerman), but an older age of 350$^{+37}_{-56}$ Ma based on fitting *Gaia* observations has been also proposed (cite: 2015Trevor). The first evidence of cool infrared excess was obtained from *IRAS* (cite: 1991PattenWillson; 2007Rhee), with subsequent detections by *Akari*/FIS (cite: 2014Liu) and *Spitzer* (cite: 2009Morales; 2014Chen). The *Spitzer*/IRS spectrum is featureless, but its shape is indicative that a substantial warm inner component to the debris disc is present within this system (cite: 2014Chen). The cool, outer disc was spatially resolved in *Herschel*/PACS observations, with a measured radius of 187 $\pm$ 6 au (cite: 2016Morales).

The disc has yet to be imaged in scattered light, and remains one of the few relatively bright debris discs ($L_{\rm d}/L_{\star} > 10^{-4}$) around nearby stars without such observations. Combining multi-wavelength, spatially resolved imaging of debris disc systems with radiative transfer modelling is necessary to weaken degeneracies inherent between the dust properties and architecture (cite: 2014aMarshall), thereby providing the greatest precision possible from the determination of the system’s properties.

The architecture of HD 138965’s debris disc, with two distinct temperature components, might imply the presence of two distinct planetesimal belts separated by (a) gap(s) produced by (a) planet(s), keeping the intervening region free of dust. Planetary companions influence the dynamics of planetesimal belts, stirring their motions and initiating the required collisional cascade and produce the observed debris disc (cite: 2009Mustill). Alternatively, the planetesimal belt may be stirred only by small bodies within the belt (cite: 2018KrivovBooth), or by some combination of these two factors (cite: 2023Munoz).

The radial and vertical structure of debris belts can potentially be used to constrain the mass of planetary companions stirring or sculpting them (cite: 2009Mustill; 2018KrivovBooth; 2019Daley; 2021Marino). Similarly, limits on the mass(es) of any potential companion(s) can be inferred from the overall architecture of the debris disc system (cite: 2022Pearce) or from the analysis of the gas kinematics. The power of constraints based on the disc architecture are limited by how well the belt is resolved and the nature of the interaction between companion and belt (i.e. stirring or sculpting). Existing imaging observations have not spatially resolved the width of the outer belt of HD 138965 (cite: 2021Marshall), so the constraints derived from such calculations remain weak. Theoretical models suggest that the extent of HD 138965’s debris disc is consistent with self-stirring by planetesimals, independent of the assumed age of the system (cite: 2018KrivovBooth). The current best limits come from high contrast imaging observations of HD 138965 which rule out the presence of a 10 $M_{\rm J}$ companion beyond 70 au from the star, assuming a stellar age of $348^{+39}_{-54}$ Ma (cite: 2018Matthews).

Here we present Atacama Large Millimiter/Submillimeter Array (ALMA) Band 6 (1.3 mm) observations of HD 138965’s debris disc, for the first time spatially resolving the system at millimetre wavelengths. We interpret these observations in conjunction with the scattered light non-detection to place upper limits on the dust albedo through radiative transfer modelling. We further infer mass limits on planetary companions in the vicinity of the disc based on the belt architecture and stellar age. The remainder of the paper proceeds as follows. In Section [2](#sec:obs) we summarise the observations of HD 138965 that underpin the subsequent analysis. Then, in Section [3](#sec:mod) we present the modelling approach, for both the host star and the disc architecture, before presenting our results. Our findings are then discussed in context in Section [\[sec:dis\]](#sec:dis). Finally, we summarise our results and present our conclusions in Section [\[sec:con\]](#sec:con).

# Observations

Here we describe the various data sets obtained and combined to model HD 138965 and its accompanying debris disc. Most of these observations are obtained from publicly available catalogues or archive as science-ready, reduced products.

## ALMA

Our target source HD 138965 (ICRS: RA = 15h 40m 11.395s, DEC = –70d 13m 41.47s) was observed by ALMA on 18 December, 2019, during its Cycle 6. The observations, under project code 2019.1.01220.S (PI: J.P. Marshall), were carried out using the 12 m array with a total of 42 antennas and employing a single pointing (no mosaic).

A total of four spectral windows (SPW) were used, including one centred at $\sim$ 230.1 GHz to target the CO (2-1) molecular line transition. The remaining three SPWs were centred at the topocentric frequencies of 227.2, 243.1, and 245.1 GHz and were employed to observe continuum emission. All SPWs fall in the ALMA Band 6 frequency coverage. Observations are sensitive to emission with a largest angular scale of $\sim$ 12.5$''$, while the field of view is approximately a factor of two larger. The instrument setup chosen used a bandwidth of 2 and 1.875 GHz, for the continuum and line SPWs, respectively. The corresponding channel spacings are $\sim$ 15625 and 976.6 kHz. Calibration and imaging of the single dataset were performed following standard procedures from the ALMA Observatory; during the observation, quasars J1427-4206 and J1558-6432 were used as bandpass/flux and phase/amplitude calibrators, respectively. The only dataset obtained for our ALMA program suffered from bad weather, resulting in amplitude drops for the flux calibrator during its observing scan. Affected data was removed, and a difference of at least 5% in flux level was found before and after data flagging. This indicates a larger than expected flux uncertainty for the calibration, and therefore imaging, of HD 138965.

A total on-source time of 40 min was achieved for HD 138965. All imaging was done using a robust value of 0.5 in the Briggs weighting scheme. The final continuum image has a sensitivity of 3$\times$RMS $\sim70~\mu$Jy, with a restored (synthesised) beam of $1.39\ensuremath{''}~\times~1.17\ensuremath{''}$, at a position angle $\phi = 10.5\ensuremath{^\circ}$. CO (2–1) line emission cubes were also inspected, with a channel width of $\sim$ 1.3 km s$^{-1}$ (RMS = 1.5 mJy beam$^{-1}$) and binned to 10 km s$^{-1}$ (RMS = 0.67 mJy beam$^{-1}$). Detailed data analysis and properties of the continuum and CO line emission are described in sections [3.2](#ssec:mm_image) and [\[ssec:COline\]](#ssec:COline).

## Ancilliary data

We compile a comprehensive set of photometric and spectroscopic data spanning optical to millimetre wavelengths. This includes optical and near-infrared photometry from *Hipparcos* and 2MASS (cite: 2000Hog; 2006Skrutskie), near- and mid-infrared photometry from *Akari* and *WISE* (cite: 2010Ishihara; 2010Wright),  *Spitzer* IRS spectroscopy and MIPS photometry (cite: 2014Chen), *IRAS* and *Herschel*/PACS far-infrared photometry (cite: 2016Morales), and the newly acquired ALMA millimetre photometry. Photometric measurements were colour corrected before modelling following the relevant instrument handbooks. A summary of the compiled photometry is presented in Table [\[tab:photometry\]](#tab:photometry). The *Spitzer* IRS spectrum was taken from the CASSIS archive (cite: 2011Lebouteiller) and scaled to the stellar photosphere model assuming a negligible infrared excess at 5 $\mu$m. Spectrophotometry using PyPhot (cite: PyPhot) was carried out to check for consistency between the rescaled spectrum and the *WISE* and MIPS photometric bands. The rescaled *Spitzer* IRS spectrum is consistent with the photometry.

These data complement the non-detection in scattered light from VLT/SPHERE and the spatially resolved imaging observations in thermal emission at far-infrared (*Herschel*/PACS) and millimetre (ALMA) wavelengths. They will be used to infer the stellar properties, in conjunction with the *Gaia*-derived stellar parallactic distance, and thereafter modelled in conjunction with the images to determine the dust grain minimum size and size distribution exponent through radiative transfer modelling.

# Modelling and results

Here we detail the data analysis and its outcomes. We first determine the fundamental parameters of HD 138965 to identify an appropriate stellar atmosphere model. The orientation and extent of the debris disc are then calculated from the ALMA imaging observations with constraints from the previous, lower angular resolution Herschel data. The stellar model in conjunction with the dust spatial distribution are used as inputs to a 1D radiative transfer code to infer the dust grain properties ($s_{\rm min}$, $M_{\rm dust}$, $q$) consistent with the observed thermal emission.

## Fundamental stellar parameters

In order to derive the fundamental stellar parameters of HD 138965 (Gaia DR3 5819811291755502976; 2MASS J15401155-7013403; IRAS 15351-7003), we applied the Bayesian inference code of (cite: delburgo2016; delburgo2018) on a grid of stellar evolution models constructed from the PARSEC v1.2S tracks (cite: bressan2012; chen2014; chen2015; tang2014). This choice is based on the good statistical agreement for detached eclipsing binaries, especially for stars on the main-sequence, where their measured dynamical masses and the corresponding predictions are consistent on average to within  4% (cite: delburgo2018).

The grid of PARSEC v1.2S models arranged for this analysis comprises ages ranging from 2 to 13,800 million years and steps of 5%, and \[M/H\] from -2.18 to 0.51 with steps of 0.02 dex, adopting the photometric passband calibration of (cite: riello2021), with the zero points of the VEGAMAG system.

We used it to infer the stellar parameters of HD 138965 through the code of (cite: delburgo2016; delburgo2018), fed by the three following input parameters: the absolute $G$ magnitude $M_{G}$, the colour $G_{\rm BP}-G_{\rm RP}$, and the iron to hydrogen \[Fe/H\]. Table [1](#tab:stellar_parameters) lists them. We reasonably assumed null extinction when deriving the colour $G_{\rm BP}-G_{\rm RP}$ and $M_{G}$ from the *Gaia* DR3 photometry and astrometry (cite: 2023aGaia). $M_{G}$ was determined from the apparent G magnitude by subtracting the distance modulus, which was calculated from the distance of 78.60$~\pm~$0.17 pc corresponding to the *Gaia* DR3 trigonometric parallax. We adopted \[Fe/H\]= $-0.30~\pm~0.30$ dex, derived by (cite: zhang2023) from *Gaia* XP spectra.

The Galactic space coordinates in units of parsec of HD 138965 are (X, Y, Z) = (55.66$~\pm~$0.11, -53.09$~\pm~$0.11, -16.195$~\pm~$0.032), which lies on the perimeter of the nearby, 40–50 Ma Argus association (cite: 2019Zuckerman). In addition, the Galactic space velocities in km s$^{-1}$ of HD 138965 are (U, V, W) = (-24.69$~\pm~$0.24, -10.58$~\pm~$0.23, -4.84$~\pm~$0.07), where U, V and W are positive toward the Galactic centre, the Galactic rotation, and the north Galactic pole, respectively. We determined the spatial and velocity parameters of HD 138965 from its *Gaia* DR3 Equatorial Coordinates (ICRS) at Ep=2016.0, proper motion, radial velocity (-9.38$~\pm~$0.30 km s$^{-1}$) and parallax. (cite: 2019Zuckerman) used *Gaia* DR2 data instead, deriving a mean Galactic space velocity in km s$^{-1}$ of (-22.5$~\pm~$1.2, -14.5$~\pm~$2.1, -5.0$~\pm~$1.6), excluding HD 188728, CD-52 9381 and HD 192640 because they may not be members of Argus, as well as HD 129496, HD 145689, and even HD 138965 because of the relative large uncertainties in UVW, and adding HD 102647. We calculated a mean Galactic space velocity, in km s$^{-1}$, from *Gaia* DR3 data without adding or removing any star, arriving at (-23.1$\pm$2.0, -14.5$~\pm~$2.7, -4.9$~\pm~$1.6). We note that (cite: 2019Zuckerman) adopted a radial velocity of -2.0$~\pm~$4.3 km s$^{-1}$ for HD 138965, which is significantly lower and much less precise than the most recent value from *Gaia* DR3. A full discussion of the membership of all stars collected by (cite: 2019Zuckerman) is out of the scope of this paper, but we find convincing evidence in the *Gaia* DR3-based spatial and velocity distributions that HD 138965 is particularly a member of the Argus association. This is supported by the Banyan Sigma analysis which assigns a 99.4% probability of its membership (cite: 2018Gagne). Imposing the prior that it is on the pre-main sequence and using the aforementioned inputs to feed the Bayesian inference code, we inferred the fundamental parameters of HD 138965 presented in Table [1](#tab:stellar_parameters).

Our effective temperature ($T_{\rm eff}$ = 8881$~\pm~$ 31 K) and surface gravity ($\log\,g$= 4.332$~\pm~$0.012) agree within a 2-$\sigma$ level with those of (cite: zhang2023) ($T_{\rm eff}$ = 9814$~\pm~$442 K, $\log\,g$= 4.69$~\pm~$0.20). Our age estimation of 31$~\pm~$11 Ma is consistent with that of (cite: 2007Rhee) (20 Ma), who considered the UVW analysis of (cite: zuckerman2004) as well as the location of HD 138965 on the Hertzsprung-Russell diagram.

As a validation test, we fed our Bayesian code with the same three input parameters but without imposing the prior on the evolution stage, finding that the age significantly increases to 805$~\pm~$468 Ma. This value is within 1-$\sigma$ uncertainty of the value of 350$^{+37}_{-56}$ Ma from (cite: 2015Trevor). The similarity is even greater if we adopt Solar metallicity, since we arrive at an age of 338$~\pm~$185 Ma.

However, the rotational broadening $v \sin i$= 94.8$~\pm~$1.7 km s$^{-1}$ from *Gaia* DR3 and the radius of HD 138965 lead to a maximum rotational period of 0.831$~\pm~$0.016 days that supports the youth of this host star.

| Parameter                       |       Value        |       Ref.        |
|:--------------------------------|:------------------:|:-----------------:|
| $\Pi$ ($mas$)                   | 12.722 $\pm$ 0.028 |    *Gaia* DR3     |
| $M_G$ (mag)                     | 1.949 $\pm$ 0.006  |    *Gaia* DR3     |
| $G_{BP}-G_{RP}$ (mag)           | 0.087 $\pm$ 0.005  |    *Gaia* DR3     |
| \[Fe/H\]                        |   -0.3 $\pm$ 0.3   | (cite: zhang2023) |
| Effective temperature (K)       |   8881 $\pm$ 31    |     this work     |
| Radius ($R_{\odot}$)            | 1.557 $\pm$ 0.009  |     this work     |
| Mass ($M_{\odot}$)              |  1.90 $\pm$ 0.04   |     this work     |
| Surface gravity ($\log g$, cgs) | 4.332 $\pm$ 0.012  |     this work     |
| Luminosity ($L$/$L_{\odot}$)    |  13.59 $\pm$ 0.09  |     this work     |
| Bolometric magnitude (mag)      | 1.907 $\pm$ 0.007  |     this work     |
| Age (Ma)                        |    31 $\pm$ 11     |     this work     |

: Fundamental stellar parameters of HD 138965.

## Millimetre continuum emission

We model the disc architecture as a single Gaussian belt. The model is defined by a flux density $f_{\rm disc}$, radius $R_{\rm peak}$, width (standard deviation) $\sigma_{R}$, scale height $h = z/R$, inclination $i$, and position angle $\phi$. Additionally, we include parameters for the stellar photospheric contribution $f_{\star}$, and position offsets $\Delta$RA, $\Delta$Dec between the star (assumed to be at the phase centre of the observations) and the disc centre. Previous marginally resolved *Herschel* observations of the disc at far-infrared wavelengths provide good constraints on the radius, inclination, and position angle for the priors for these parameters (cite: 2016Morales; 2021Marshall). These priors are normally distributed with a standard deviation 3% of the initial value and bounds informed by the likely range of each parameter.

![image](HD138965_cont_briggs0.5.pdf) ![image](HD138965_cont_res_briggs0.5.pdf)

We explore the parameter space of the model in a Bayesian framework using emcee (cite: 2013ForemanMackey), following the approach presented in previous, similar works (cite: 2018Marshall; 2023aMarshall). Walkers are initialised at the maximum likelihood values for the disc parameters determined from modelling the *Herschel* observations. Each set of parameters is used to generate a disc model using the radiative transfer code RADMC-3D (cite: 2012Dullemond) which is then converted into synthetic visibilities using Galario (cite: 2018Tazzari). These model visibilities are binned and compared to the ALMA observations through least-squares fitting. In total, we created 90,000 realisations of the model (90 walkers, 1,000 steps). The final posterior probability distribution used the last 10,000 realisations, from which the maximum likelihood parameters and their uncertainties were obtained. The posteriors are all monomodal and approximately normally distributed. We therefore take the 50th percentile of the posterior of each parameter as its model value and calculate the uncertainties from the 16th and 84th percentiles of each parameter distribution. We present the marginalised posteriors in Appendix [\[AppendixB\]](#AppendixB). The results of the model fitting are summarised in Table [\[tab:hd138965_alma_fit\]](#tab:hd138965_alma_fit), and we show the observations and residuals (after subtraction of the maximum likelihood model) in Figure [1](#fig:hd138965_alma).

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

| Parameter                |    Range    |         Value          |
|:-------------------------|:-----------:|:----------------------:|
| $R_{\rm peak}$ (au)      |  50 – 300   |    150$^{+10}_{-7}$    |
| $\sigma_{R}$ (au)        |  10 – 100   |     49$^{+7}_{-6}$     |
| $h$                      | 0.01 – 0.30 | 0.15$^{+0.07}_{-0.08}$ |
| $i$ ($^\circ$)           |   0 – 90    |  49.9$^{+3.3}_{-3.7}$  |
| $\phi$ ($^\circ$)        |   0 – 180   | 173.3$^{+3.7}_{-4.1}$  |
| $f_{\rm dust}$ (mJy)     | 0.1 – 10.0  |   1.460 $\pm$ 0.230    |
| $f_{\rm star}$ ($\mu$Jy) |   0 – 300   |         $<~70$         |
| $\Delta$RA ($''$)        |   -1 – 1    |  0.11$^{+0.5}_{-0.6}$  |
| $\Delta$Dec ($''$)       |   -1 – 1    |  0.16$^{+0.7}_{-0.7}$  |

: Results from visibility fits to the ALMA observation. We note that the relative scale height $h = (z/R)$ is unconstrained from the modelling and the stellar flux **density** $f_{\star}$ is an upper limit.

We find that HD 138965’s disc has a total flux density of 1.46 $\pm$ 0.23 mJy at a wavelength of 1.269 mm. The cold belt is spatially resolved, with a radius of 150$^{+10}_{-7}$ au and a width of 49$^{+7}_{-6}$ au (FWHM = 115$^{+16}_{-14}$ au). The radius is consistent with the *Herschel*-derived extent, and the width of the debris belt is marginally resolved with a fractional width $\Delta R / R = 0.77$. This places HD 138965 amongst the more radially extended discs that have been observed to-date spanning 0.1 to $>$1.0 (cite: 2025Matra), and in comparison to the Solar system’s Edgeworth-Kuiper belt (cite: 2009Kavelaars; 2011Petit). A 2-$\sigma$ brightness asymmetry between the NW and SE ansae of the disc is seen in the imaging data. Given the large uncertainties and calibration of these observations it is not necessarily a real feature of the disc, but should motivate future observations. The large relative vertical scale height, $h = 0.15^{+0.07}_{-0.08}$, might be taken as a further indication of the disc being stirred. The associated uncertainty, in conjunction with the moderate inclination and modest signal-to-noise, instead leads us to the interpretation that a broad range of scale heights tested by the model will adequately fit the observations. This motivates the need for higher spatial resolution, higher signal-to-noise observations in future to constrain the internal dynamics of this disc. Its inclination, $i = 49.9\ensuremath{^\circ}^{+3.3}_{-3.7}$, and position angle, $\phi = 173.3\ensuremath{^\circ}^{+3.7}_{-4.1}$, are the most precise measurements of the disc orientation, both consistent with previous estimates. As expected we do not detect either emission from the warm belt or the star and obtain a 3-$\sigma$ upper limit of 90 $\mu$Jy on the stellar photospheric emission. Furthermore, we find no evidence for an offset between the star (phase centre) and disc centre from these observations although the constraints on such an offset are low due to the limited spatial resolution of the observations.

## Millimetre CO line emission

We use the spatially resolved extent and orientation of the disc from the continuum image to identify the region of the spectral window covering the CO (2-1) line at 230.538 GHz to search for gas emission from the disc. A spatial mask is applied to the spectral cube, with pixels lying within the region from $R_{\rm peak} -$HWHM to $R_{\rm peak} +$HWHM and with a flux density $\geq$3-$\sigma$ being included in the summation. For each pixel included in the mask we shift the spectrum’s frequency according to the projected Keplerian velocity, interpolate these individual spectra to a set of common velocities and sum these to produce a final CO spectrum. The resulting spectrum centred on the CO (2-1) line at 230.54 GHz is presented in Figure [1](#fig:hd138965_alma_line), with a shaded region denoting the frequency space included in the search for CO line emission centred at the stellar radial velocity of -9.38 km/s taken from *Gaia* DR3 (cite: 2023aGaia). We find no evidence for any CO emission associated with the disc, and obtain a 5-$\sigma$ upper limit of 3.35 mJy/beam in a 10 km/s wide channel, equivalent to 2.7$\times10^{-23}$ W/m$^{2}$, which is around a factor of three above the predicted CO emission level of 1.1$\times10^{-23}$ W/m$^{2}$ ($M_{\rm CO}$ = 8.6$\times10^{-7}~M_{\oplus}$) of (cite: 2017Kral).

![](HD138965_co_spectrum_R1.pdf)

## Spectral energy distribution

We model HD 138965’s spectral energy distribution (SED) as a star plus two dust components, using two separate parametric models to represent the warm excess present at mid-infrared wavelengths, and the cold excess at mid-infrared to millimetre wavelengths. A summary of the photometry used in the radiative transfer modelling is provided in Table [2](#tab:photometry).

|            |                 |                     |           |
|:----------:|:---------------:|:-------------------:|:---------:|
| Wavelength |  Flux Density   |     Telescope /     | Reference |
|  ($\mu$m)  |      (mJy)      | Instrument / Filter |           |
|    0.44    | 10700 $\pm$ 200 |     Johnson $B$     |     1     |
|    0.55    | 9838 $\pm$ 186  |     Johnson $V$     |     1     |
|    0.58    |  8680 $\pm$ 20  |     *Gaia* $G$      |     2     |
|    1.24    | 4654 $\pm$ 172  |      2MASS $J$      |     3     |
|    1.65    | 3052 $\pm$ 190  |      2MASS $H$      |     3     |
|    2.16    |  2059 $\pm$ 58  |  2MASS $K_{\rm s}$  |     3     |
|    3.4     |  921 $\pm$ 88   |      *WISE* W1      |     4     |
|    4.6     |  551 $\pm$ 19   |      *WISE* W2      |     4     |
|     9      |  206 $\pm$ 10   |    *Akari* IRC9     |     5     |
|     12     |   103 $\pm$ 4   |      *WISE* W3      |     4     |
|     13     |   134 $\pm$ 7   |    *Spitzer* IRS    |     6     |
|     22     |   80 $\pm$ 5    |      *WISE* W4      |     4     |
|     24     |   81 $\pm$ 2    |   *Spitzer* MIPS    |     6     |
|     31     |   111 $\pm$ 2   |    *Spitzer* IRS    |     6     |
|     60     |  482 $\pm$ 63   |      *IRAS* 60      |     7     |
|     70     |  561 $\pm$ 29   |   *Spitzer* MIPS    |     6     |
|    100     |  527 $\pm$ 17   |   *Herschel* PACS   |     8     |
|    160     |  299 $\pm$ 13   |   *Herschel* PACS   |     8     |
|    1270    | 1.46 $\pm$ 0.23 |     ALMA Band 6     |     9     |

: Photometry used in the radiative transfer modelling.

**References:** 1. (cite: 2000Hog) 2. (cite: 2023aGaia)\
3. (cite: 2006Skrutskie) 4. (cite: 2010Wright) 5. (cite: 2010Ishihara)\
6. (cite: 2014Chen) 7. (cite: 1988Beichman) 8. (cite: 2016Morales)\
9. This work.

We obtained the best BT-NextGen stellar atmosphere model (cite: 2012Allard) that fits the HD 138965’s photometry from a classical least-squares approach. The fundamental stellar parameters derived are the effective temperature $T_{\rm eff} = 8800$ K, metallicity \[Fe/H\] = -0.5, and the surface gravity of $\log g = 4.5$, consistent with the values inferred in Section [\[ssec:star\]](#ssec:star). This model was scaled to the available optical and near-infrared photometric data up to 5 $\mu$m.

To model the thermal emission of the grains we applied *Stardust*, a model that takes into account the dust composition (determined by optical constants) and a combination of forces that influence the spatial redistribution of dust grains. These forces include the conservative forces of gravity competing with the outward radiation pressure (cite: 1979BurnsLamySoter) , and the non-conservative force of the Poynting-Robertson effect (cite: 1903Poynting; 1937Robertson; 2007Klacka) that causes grains to spiral inwards. *Stardust* includes modelling a simple collisional lifetime of the grains that depends on the optical depth of the debris disc (cite: 2010KuchnerStark). We used the fractional luminosity of HD 138965’s disc as a proxy for the optical depth. We summarise the *Stardust* model in Appendix [\[AppendixA\]](#AppendixA).

For our purposes, we assumed the radial planetesimal surface density to follow a Gaussian profile and differential power law grain size distribution ($dn/ds \propto s^{-q}$). In all considered scenarios, we assume the maximum size of the dust grains to be 3000 $\ensuremath{\mu}m$ and the inner belt to have a grain composition of astronomical silicate (cite: 2003Draine). The outer, cooler belt was assumed to have a fixed peak surface density at 150 au with a standard deviation of 49 au (taken directly from the ALMA observations, see Table [1](#tab:hd138965_alma_fit)).

We note that, since the inner belt is not spatially resolved, there will be a degeneracy between location and the temperature of the grains. We performed an initial analysis using *Stardust* to estimate the inner belt characteristics. As such we had the following components to be free parameters for both the inner and outer belts: belt radius ($r_m$) and width ($\sigma_r$), minimum grain size ($s_{\rm min}$), dust mass ($M_s$), and the size distribution component ($q$) to initially vary between 3 and 4 as is the case for collisional active discs (cite: 2016Macgregor; 2017Marshall; 2021Norfolk). Here we found that the inner belt had a minimum grain size of approximately 12 $\ensuremath{\mu}m$, however, as the value of $q$ did not converge.

To pin down the radial component of the inner belt, we ran *Stardust* with the following assumptions for the inner belt: minimum grain size of 12 $\ensuremath{\mu}m$, size distribution component to be 3.5 (cite: 1969Dohnanyi), and the disc fractional width ($\Delta r/r$) to be 0.3. The mean radial distance of the inner belt and the mass were kept as free parameters. This scenario still did not converge to a solution, but it did produce a reasonable goodness-of-fit to the data where our reduced minimum $\chi^2$ test was less than one. The posterior probability distribution for the corresponding emcee run is presented in Figure [\[fig:hd138965_SED_corner_plot\]](#fig:hd138965_SED_corner_plot) (Appendix [\[AppendixB\]](#AppendixB)). A summary of the fixed parameters that have been assumed for the inner belt component of HD 138965 are given in Table [3](#tab:hd138965_innerbelt).

| Parameter                                |         Value         |
|:-----------------------------------------|:---------------------:|
| $s_{\rm min}$ ($\ensuremath{\mu}m$)      |          12           |
| $T_{dust}$ (K)                           |          168          |
| $q$                                      |          3.5          |
| $M_{\rm s}$ ($\times10^{-3}~M_{\oplus}$) |         0.154         |
| $r_m$ (au)                               |         13.7          |
| $\sigma_{r}$ (au)                        |         1.75          |
| Composition                              | Astronomical Silicate |

: Assumed inner belt parameters for HD 138965.

Now that we have our fixed assumptions for the inner belt, we then modelled the outer belt with different compositions and porosities. For all scenarios, we set the minimum grain size in the outer belt to be the blowout limit of the corresponding grain composition. For the outer belt component ($q$), we allowed to vary between 2 and 5 to account for potential size-dependent velocity distributions for all bodies (cite: 2012PanSchlichting). The different compositions considered were a mixture of astronomical silicate with either crystalline water-ice (cite: 2008WarrenBrandt), amorphous water-ice (cite: 1993Hudgins), amorphous carbon (cite: 1993Preibisch), or vacuum (as porosity). For each mixture (or inclusion matrix particles; IMPs), we assumed the grains to be astronomical silicate combined with an inclusion material with a volume fraction of 0.5, 0.25, and 0.1 for each material.

To determine the maximum likelihood values for each model we again adopt a Bayesian approach using the Markov Chain Monte Carlo (MCMC) code emcee (cite: 2013ForemanMackey) to explore the parameter space and determine the posterior probability distributions for each parameter from which the maximum amplitude probability and uncertainties were determined. We ran a total of 320 000 realisations for each model with 80 walkers and 4 000 steps. We used the first 500 steps as burn-in for the MCMC chains and calculated probability distributions from the final 280 000 realisations. We used the 50$^{\rm th}$ value from the posterior of each parameter to determine the reduced $\chi^2$ of a given architecture and dust composition for comparison between dust composition models. For each of these scenarios, all of them converged to a solution before reaching the 4000th step.

To determine which model to be the best fit, we applied the Bayesian Information Criterion (cite: 1978Schwarz):

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

$$\begin{equation}
 \label{eq:BIC}
    BIC  = \chi^2 + k \ln N,
\end{equation}$$

where ‘$k$’ is the number of free parameters and ‘$N$’ is the number of data points used in the fit. In our scenarios, we have $k = 3$ (for outer belt composed of only astronomical silicate) or $k = 4$ (for outer belt composed of mixed grains), and $N = 15$. The lower the BIC value the better the fit. We then calculate the change of BIC (cite: 2004Burnham):

$$\begin{equation}
 \label{eq:dBIC}
    \Delta BIC  = BIC_{mc} - BIC_{best},
\end{equation}$$

where ‘$mc$’ is the model being compared with the ‘$best$’ model. In our case, the best model as determined by ‘BIC’ is the scenario where the outer belt is composed of pure astronomical silicate dust grains. If $\Delta BIC < 2$, the models are indistinguishable; $2 < \Delta BIC < 6$ there is some support for the ‘best’ model but not conclusive; $6 < \Delta BIC < 10$ there is stronger evidence to support the best model; ands $\Delta BIC > 10$ indicates that the ‘best’ model is highly preferred. See Table [\[tab:au-beta\]](#tab:au-beta) for a summary of the model outcomes.

On this basis, the model corresponding to P = 0.25 is a reasonable fit to the observations, while 90:10 astronomical silicate:amorphous water-ice, and the remaining porosity scenarios are all plausible dust compositions. See Figure [1](#fig:sed) for the corresponding SED to the scenario of 90:10 astronomical silicate:amorphous water-ice. The 90:10 and 75:25 of astronomical silicate:crystalline water-ice were not categorically ruled out based on the $\Delta$BIC values. We can however rule out the 50:50 compositions for both amorphous and crystalline water ice, and all three of the carbon:astronomical silicate compositions tested here. It should be noted that the emission from the inner belt is fixed following the initial modelling where the outer belt grains are assumed to be solely astronomical silicate. This may introduce an inherent bias toward astronomical silicate being the best solution for the outer belt. Ultimately, we would need to either independently determine the architecture of the inner belt through spatially resolved imaging or obtain spectroscopic data for the dust revealing features associated with water ice or other species to better infer the composition of the debris dust.

Through our initial analysis using MCMC, we found the value of the inner belt’s mean radial location to be at $15^{+3}_{-2}$ au, and minimum grain size $s_{\rm min}$ of 12$\ensuremath{\mu}m$, broadly consistent with the values reported in (cite: 2016Morales). The $s_{\rm min}$ adopted for the inner belt is much larger than that of the outer belt. We would expect $s_{\rm min}$ to be a few times the blowout size and for a 13.6 $L_{\odot}$ star, that ratio would be $s_{\rm min} \simeq 2.5 s_{\rm blow}$ or 7 $\mu$m (cite: 2014Pawellek). The effective temperature of 12 $\mu$m astronomical silicate dust grains is 168 K at 15 au from HD 138965, consistent with the sublimation temperature of water ice in vacuum (cite: 2021Kossacki). This supports our assumption of a dry inner belt; if the minimum grain size were smaller the dust would be hotter such that the major implication would be the inner belt would need to be placed further out to match the observed mid-infrared emission. Our study of the outer belt composition implemented a refined model compared to (cite: 2016Morales), where they assumed a single composition of 50:50 astronomical silicate:ice for the dust grains and a fixed density distribution. Our best-fit results correspond to the porosity scenarios and have a strong candidate with 90:10 astronomical silicate:crystalline water-ice mixture for the outer belt.

![](HD138965_SED_AS90WIA10.pdf)

| Parameter | S100 | S90WC10 | S75WC25 | S50WC50 | S90WA10 | S75WA25 | S50WA50 | S90C10 | S75C25 | S50C50 | P = 0.1 | P = 0.25 | P = 0.5 |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| $s_{\rm blow}$ ($\ensuremath{\mu}m$) | 2.70 | 2.86 | 3.16 | 4.04 | 2.86 | 3.16 | 3.87 | 2.86 | 3.04 | 3.46 | 2.93 | 3.41 | 4.80 |
| $q$ \[2.0 - 5.0\] | 3.73$^{+0.07}_{-0.07}$ | 3.82$^{+0.09}_{-0.08}$ | 3.86$^{+0.11}_{-0.10}$ | 4.01$^{+0.20}_{-0.17}$ | 3.78$^{+0.08}_{-0.08}$ | 3.83$^{+0.10}_{-0.09}$ | 4.00$^{+0.18}_{-0.15}$ | 4.15$^{+0.10}_{-0.09}$ | 4.41$^{+0.10}_{-0.09}$ | 4.89$^{+0.08}_{-0.16}$ | 3.63$^{+0.07}_{-0.07}$ | 3.49$^{+0.07}_{-0.06}$ | 3.30$^{+0.07}_{-0.07}$ |
| $M_{\rm s}$ \[1 - 20\] | 7.74$^{+0.49}_{-0.48}$ | 7.75$^{+0.55}_{-0.54}$ | 7.18$^{+0.58}_{-0.56}$ | 5.86$^{+0.70}_{-0.62}$ | 7.44$^{+0.51}_{-0.50}$ | 7.07$^{+0.55}_{-0.54}$ | 6.12$^{+0.65}_{-0.61}$ | 7.05$^{+0.43}_{-0.42}$ | 9.20$^{+0.76}_{-0.74}$ | 8.89$^{+0.60}_{-0.63}$ | 6.67$^{+0.43}_{-0.43}$ | 5.23$^{+0.35}_{-0.34}$ | 3.18$^{+0.21}_{-0.21}$ |
| ($\times10^{-3}~M_{\oplus}$) |  |  |  |  |  |  |  |  |  |  |  |  |  |
| $\chi^2$ | 9.3 | 14 | 17 | 150 | 11 | 28 | 100 | 19 | 20 | 120 | 9.4 | 8.3 | 10 |
| $\chi^2_{\rm red}$ | 0.66 | 0.90 | 1.1 | 9.8 | 0.78 | 1.9 | 6.9 | 1.3 | 1.3 | 7.7 | 0.62 | 0.55 | 0.67 |
| $\Delta$BIC | 0.0 | 7.0 | 10 | 140 | 4.4 | 21 | 96 | 12 | 14 | 110 | 2.8 | 1.7 | 3.4 |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |

## Constraints from scattered light

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

HD 138965 was observed by VLT/SPHERE IRDIS (cite: 2019Beuzit) using the BB_H filter for the SPHERE High-Angular Resolution Debris Disks Survey[^2] (cite: 2016Wahhaj; 2017Choquet; 2018Marshall; 2021Cronin-Coltsmann). These observations are deeper than those presented in (cite: 2018Matthews), but the disc is still not detected. From the SHARDDS observation we obtain a 5-$\sigma$ upper limit of 83 $\mu$Jy/arcsec$^{2}$ at a separation of $2\ensuremath{''}$ from the star. To estimate the equivalent integrated disc brightness required to be detectable, we inject model discs with an architecture consistent with the ALMA observation into the data cube. The cube was then reduced and stacked using the classical ADI algorithm. The model brightness was varied until the integrated stack exhibited residuals in excess of the 5-$\sigma$ limit. We find a minimum brightness of around 10 mJy is required for the disc to be detected in the SHARDDS data. Based on this calculation, we would need to go at least a factor of four deeper in imaging HD 138965 to detect the disc at near-infrared wavelengths. This assumes reducing the limit of the albedo to $\leq 0.2$ would start to probe values consistent with other discs at near-infrared wavelengths (cite: 2023Ren).

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

[^2]: ESO programs 096.C-0388 and 097.C-0394

We further estimate the contrast for point sources around HD 138965 at radial separations out to $\simeq~1\ensuremath{''}$. This contrast curve was calculated using the Regime Switching Model algorithm as presented in (cite: 2022Dahlqvist). We convert the observed contrast to mass in order to determine the limits on planetary companions in the vicinity of the disc, as shown in Figure [1](#fig:contrast). The mass limit as a function of separation was calculated for ages of 30 $\pm$ 10 Ma (our inferred age), 45 $\pm$ 5 Ma (Argus association membership), and 348$^{+39}_{-54}$ Ma (from *Gaia*). The masses were converted from the measured contrast using the AMES-COND grid of models (cite: 2001Allard). In the vicinity of the inner edge of the cold debris belt ($\simeq~80~$au) we obtain upper limits to the mass of any companion of 4$~M_{\rm Jup}$ ($t_{\star} =$ 31 Ma), 5$~M_{\rm Jup}$ ($t_{\star} =$ 45 Ma), and 15$~M_{\rm Jup}$ ($t_{\star} =$ 348 Ma).

![](HD138965_mass_limit.pdf)

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

A surface brightness limit of 20 mag/arcsec$^{2}$ at $2\ensuremath{''}$ ($\equiv 33~\mu$Jy/arcsec$^{2}$) was obtained in the *HST*/ACS F606W filter (cite: 2010Krist). The *HST*/ACS measurement is more constraining than the VLT/SPHERE measurement, resulting in a limit of $\omega \leq 0.09$ at optical wavelengths. This is consistent with the minimum grain size in the outer belt derived from modelling the SED, assuming an astronomical silicate composition for the dust. The calculated albedo limit for HD 138965’s disc is intermediate for those discs detected in scattered light (cite: 2018Choquet; 2023Ren), from which we infer deeper observations would stand a good chance of detecting the disc.

We can obtain an alternative measure of the dust scattering albedo using the maximum likelihood dust model determined in Section [\[ssec:sed\]](#ssec:sed). Here we take the $Q_{\rm abs}$ and $Q_{\rm sca}$ values derived from the dirty ice dust composition for grains with $s = 3.6~\mu$m, being the minimum grain size in our distribution and therefore the largest contribution to the disc surface area. We infer a scattering albedo of $\omega = 0.56$ over all angles at a wavelength of 1.6 $\mu$m, using the relation $\omega = Q_{\rm sca}/(Q_{\rm abs} + Q_{\rm sca})$ (cite: 1998BohrenHuffman). Considering instead only a restricted range of scattering angles close to $90\ensuremath{^\circ}$, based on the orientation of the disc, we instead infer an effective dust albedo $\simeq 0.1$ for astronomical silicate dust grains around $10~\mu$m in size (cite: 2013Mulders; 2018Choquet). This would result in non-detection of the disc and be marginally consistent with upper limits from *HST*.

# Discussion

The outer belt of HD 138965’s debris disc is found to be very broad with $\Delta R / R = 0.77$. This is far greater than the Solar system’s Edgeworth-Kuiper belt (cite: 2009Kavelaars; 2011Petit) and comparable to HR 8799’s outer belt (cite: 2021Faramaz).

A handful of radially broad discs followed-up at sufficient angular resolution have been found to contain substructures associated with disc-planet interaction believed to represent sculpting or scattering of planetesimals (cite: 2021Marino). The pursuit of further observations of HD 138965 at higher angular resolution to determine the architecture of the outer belt are therefore recommended.

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

Despite the modest angular resolution and signal-to-noise of the ALMA observations the outer belt is spatially resolved in both radius and width. We can therefore place constraints on the presence of a planetary companion stirring or sculpting the belt following the analysis presented in (cite: 2022Pearce). For these calculations we assume the disc inner edge to lie at 101 au (i.e. $R$ - $\sigma_{\rm R}$) and the stellar parameters from Table [\[tab:stellar_parameters\]](#tab:stellar_parameters). For the single planet sculpting scenario, we calculate a planetary mass $\geq$ 2.3 $\pm$ 0.4 $M_{\rm J}$ at a semi-major axis $\leq~74^{+8}_{-6}$ au. This is a factor of five improvement over the previous limit from (cite: 2018Matthews), and a factor of two better than obtained from the deeper SHARDDS image presented in Section [\[ssec:scat_limits\]](#ssec:scat_limits), but still relatively weak. At the other extreme, assuming the disc is self-stirred by massive planetesimals, we can constrain the total mass of the debris disc to be at least $400~\pm~100~M_{\oplus}$ in bodies up to 100 km in size. This mass is consistent with the maximum allowable debris disc masses as a function of disc properties (e.g. radius, fractional luminosity) determined by (cite: 2021KrivovWyatt).

Our analysis of the dust dynamics has been modelled by *Stardust*, where we include P-R effected grains (i.e., inward spiralling of dust grains) to eventually result in collisional destruction on its way to the host star. Due to the inner belt not being spatially resolved we attempted to mitigate the degeneracy between grain temperature and location, we performed an initial analysis to estimate its characteristics under the assumption that the outer belt grains are composed of pure astronomical silicate. The mean values taken from the posterior probability distributions for this scenario, we estimated the location of the inner belt to be mean distance of $15^{+3}_{-2}$ au, this result is in line with the study conducted by (cite: 2016Morales). With all subsequent scenarios modelled, we fixed the minimum grain size of the outer belt to be the blowout limit of the grain corresponding to the relative dust composition. We note that under the assumptions of inner belt characteristics there may be an inherent bias towards the best model where pure astronomical silicate grains are in the outer belt. On this basis, we cannot rule out the scenarios where there is at least 10% crystalline or amorphous water-ice inclusions in the astronomical silicate grains in the outer belt. However, we can eliminate grains for the scenarios with 50% water-ice inclusions and any grain that has amorphous carbon mixed in for HD 138965’s outer belt. To be sure of the inner belt radial location, higher spatial resolution images would be required. For example, at a radius of $\simeq 20$ au the inner belt would have an angular separation of $0.25\ensuremath{''}$ which is potentially resolvable by JWST/MIRI in imaging mode at 10 $\mu$m (cite: 2023Wright), or in future with AtLAST at 350 $\mu$m (cite: 2024Klaassen; 2024Booth).

# Conclusions

We have spatially resolved for the first time the radius and width of the outer cool belt of HD 138965’s debris disc at millimetre wavelengths with ALMA. We find the peak emission from the belt at 150 au with a standard deviation of 49 au (FWHM 115 au, $\Delta R /R \simeq 0.77$). The disc radius, inclination (49.9$^\circ$), and position angle (173.3$^\circ$) of the belt are in good agreement with previous marginally resolved *Herschel* observations. The disc is very broad, comparable in width to several systems that have exhibited indirect evidence of disc-planet interactions. However, the low signal-to-noise and relatively low angular resolution of the ALMA observations preclude any more detailed insights regarding the belt structure or its stirring.

Using the newly acquired ALMA imaging of the disc we modelled the disc spectral energy distribution using a novel code to redistribute dust grains based on their size and the gravitational and radiation forces acting upon them. As the inner belt is not spatially resolved, we assumed that both the inner and outer belt grains were composed of pure astronomical silicate to constrain the system’s inner belt by determining its location to be 15$^{+3}_{-2}$ au to help mitigate the degeneracy between the temperature and location for grains. We found, whilst the pure astronomical silicate grains were considered the best scenario for the composition of the dust in the outer belt, we could not categorically disregard scenarios with a 10% crystalline or amorphous water-ice inclusions in the silicate grains.

We then undertook a study of archival scattered light observations from VLT/SPHERE to obtain some constraint on the dust optical properties, but the disc remains undetected. Using the non-detection by *HST* at optical wavelengths in conjunction with the spatially resolved architecture of the disc from ALMA we calculate an upper limit to the dust albedo of 0.09. That limit from observations is inconsistent with the same limit determined from the dust grain size and composition inferred from the SED. These two values can be somewhat reconciled by considering either a restricted range of scattering angles to reduce the inferred albedo from HST imaging, or instead invoking the broad belt width and self-subtraction inherent to the data reduction process for its non-detection in SPHERE imaging.

Despite non-detection of the disc in scattered light, analysis of these data provided deeper constraints on the mass of companions to the system. Interpretation of the contrast curve derived from the SHARDDS observation of HD 138965 places a mass limit of 4 $M_{\rm Jup}$ at 80 au from the star, assuming an age of 30 Ma. Using the architecture of the disc we instead obtain a mass limit of 2.3 $\pm$ 0.4 $M_{\rm Jup}$ for a single planet sculpting the disc. This comparison illustrates the predictive power of debris disc architectures for the inference of planetary companions.

Future avenues for the characterisation of the HD 138965 system with current and planned facilities are promising. For example, in the infrared *JWST* is able to resolve both the inner and outer belts of the debris disc and simultaneously provide deep limits on the presence of planetary companions. At millimetre wavelengths, deeper observation with ALMA to resolve the outer belt’s structure is possible, albeit demanding, in terms of the time required with its current sensitivity; future bandwidth upgrades will make such high angular resolution observations more feasible.

# Acknowledgements

This research has made use of the SIMBAD database, operated at CDS, Strasbourg, France (cite: 2000Wenger). This research has also made use of NASA’s Astrophysics Data System. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01220.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

JPM acknowledges support by the National Science and Technology Council of Taiwan under grant NSTC 112-2112-M-001-032-MY3.

CdB acknowledges support from the Agencia Estatal de Investigación del Ministerio de Ciencia, Innovación y Universidades (MCIU/AEI) under grant WEAVE: EXPLORING THE COSMIC ORIGINAL SYMPHONY, FROM STARS TO GALAXY CLUSTERS and the European Regional Development Fund (ERDF) with reference PID2023-153342NB-I00/10.13039/501100011033, as well as from a Beatriz Galindo Senior Fellowship (BG22/00166) from the MICIU. The Universidad de La Laguna (ULL) and the Consejería de Economía, Conocimiento y Empleo of the Gobierno de Canarias are also gratefully acknowledged for the support provided to CdB (2024/347).

This work was also partly supported by the Spanish program Unidad de Excelencia María de Maeztu CEX2020-001058-M, financed by MCIN/AEI/10.13039/501100011033.

EC acknowledges funding from the European Union (ERC, ESCAPE, project No 101044152). Views and opinions expressed are, however, those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them.

VFG acknowledges funding from the National Aeronautics and Space Administration through the Exoplanet Research Program under Grants No. 80NSSC21K0394 and 80NSSC23K1473 (PI: S. Ertel), and Grant No 80NSSC23K0288 (PI: V. Faramaz).

*Facilities*: ALMA

*Software*: AstroPy (cite: 2013AstroPy; 2018AstroPy; 2022AstroPy), Corner (cite: 2016ForemanMackey), Emcee (cite: 2013ForemanMackey), Galario (cite: 2018Tazzari), Matplotlib (cite: 2007Hunter), Numpy (cite: 2020Harris), Scipy (cite: 2020Virtanen)

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

# Data Availability

The data presented in this work are available upon reasonable request to the authors.

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

# Dusty Grain Model

A quasi-static dynamics and radiative transfer code for dust grains in debris discs (‘Stardust’) was developed to:

1.  predict the radial location of the dust grains depending on the forces acting on the grains due to the host star according to size (dynamics)

2.  predict the thermal emission of the dust grains from the grain’s location, size, and composition (radiative transfer)

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

The grains in the Stardust model are assumed to be spherical objects that absorb and emit radiation according to Mie theory (cite: 1998BohrenHuffman). In addition to gravity, these grains are subject to different forces that can move them far away from the point of production (cite: 2008Krivov). The model can switch ‘on’ and ’off’ the force of stellar radiation pressure (cite: 1979BurnsLamySoter) and the inward drag due to the Poynting-Robertson (P-R) effect (cite: 1903Poynting; 1937Robertson; 2007Klacka) in comparison to the mean collisional time of the grain (cite: 2010KuchnerStark).

The model assumes an optically thin disc with no gas present. When the grains are traversing along elliptical orbits due to radiation pressure, it is assumed that no collisions occur. However, when the model activates the P-R effect, i.e. when the grain loses angular momentum and spirals inwards towards the star, a simple collision assumption is implemented based on the optical depth of the disc. Additional force components, such as stellar wind, will be considered with future iterations of this model.

![](beta0p3_plots.pdf)

## Radiation pressure affected grains

Grains in the model are initially on Keplerian orbits, where grains are under the influence of gravity. When the conservative radiation pressure force is switched on, this pushes grains out along elliptical orbits according to grain size. To determine the resultant orbit is by the ratio ($\beta$) of radiation pressure to gravitational forces (cite: 2010Krivov):

$$\begin{equation}
 \label{eq:beta_mod}
    \beta  = 0.574\frac{L_\star Q_{pr}(s)}{M_\star\rho s},
\end{equation}$$

where, $L_\star$ and $M_\star$ are the solar luminosity and mass of the host star, grain density ($\rho$) and size ($s$) are expressed in units of ‘g/cm$^3$’ and ‘$\ensuremath{\mu}m$’ respectively, and the dimensionless quantity $Q_{pr}(s)$ is the radiation pressure efficiency dependent on grain size. The $\beta$ values in the model are calculated for each corresponding grain size.

The eccentricity ($e$) of the orbit can be derived from the $\beta$ (cite: 2006AB):

$$\begin{equation}
\label{eq:e-beta}
    e = \frac{\beta}{1-\beta}
\end{equation}$$

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

and the semi-major distance ($a$) of the ellipse, with pericentre ($r_p$), calculated using:

$$\begin{equation}
\label{eq:a-e}
    a = \frac{r_p}{1-e}.
\end{equation}$$

Our aim is to determine the probability of a grain at a particular point in time along the orbit. If we simply plot stellar distance as a function of True Anomaly ($\theta$), time is not considered (see left plot of Figure [\[fig:b0.3\]](#fig:b0.3) for a grain corresponding to $\beta$ = 0.3). Therefore, to find a better representation we start with Kepler’s Second Law in the following form: $$\begin{equation}
 \label{eq:K2law}
    r^2d\theta = mabdt
\end{equation}$$

where $m = 2\pi/P$ is referred to as the mean motion, and $P$ is the orbital period in years for a given semi-major axis in au and host star mass in Solar masses ($P = a^{3/2}M_\star^{-1/2}$). The semi-major axis ($a$) and the semi-minor axis ($b$) are in units of au, and the period ($P$) is in years. Equation [\[eq:K2law\]](#eq:K2law) cannot be solved analytically, thus, we have adopted the following iterative case: $$\begin{equation}
\label{eq:anglestep}
    d\theta = \Delta\theta = \theta_{n+1} - \theta_{n}
\end{equation}$$

and the time-step defined by: $$\begin{equation}
\label{eq:timestep}
    dt = \Delta t~(= t_{n+1} - t_{n})
\end{equation}$$

So, substituting Equations [\[eq:anglestep\]](#eq:anglestep) and [\[eq:timestep\]](#eq:timestep) into Equation [\[eq:K2law\]](#eq:K2law), yields the following relationship:

$$\begin{equation}
\label{eq:angdisttime}
    \theta_{n+1} = \theta_{n} + \frac{abm}{r^{2}_{n}}\Delta t
\end{equation}$$

Equation [\[eq:angdisttime\]](#eq:angdisttime) allows iterative solution to the stellar distance of the grain as a function of both True Anomaly and time. An appropriate timestep has been chosen to correspond to the $\beta$-value of the largest grain size. See middle plot of Figure [\[fig:b0.3\]](#fig:b0.3), for the grain orbit corresponding to $\beta$ = 0.3. The next step is to group the radial data determined by solving Equation [\[eq:angdisttime\]](#eq:angdisttime) with a bin size of 1 au (although in principle this can be any size desired), resulting in the relative probability distribution corresponding to $\beta$ in the right-hand plot of Figure [\[fig:b0.3\]](#fig:b0.3). Inspecting this figure shows that the grain will spend most of its time on closest and farthest approaches of the star.

This may be counter-intuitive for the nearest approach as the grain has the fastest speed. However, these extreme points (pericentre and apocentre) are turning points for the grain and the corresponding stellar distances ($r$) at these locales are more frequent, as opposed to locales where the grain is travelling towards and away from these extremities.

## Grain size distribution

The distribution of grain sizes typically favour smaller grains in debris discs. (cite: 1969Dohnanyi) presented a collisional model that showed the number density of particles per unit volume ($dn/dV$) in the mass range m to m + dm is:

$$\begin{equation}
\label{eq:Dohnumden}
    \frac{dn}{dV} \propto m^{-\alpha}dm
\end{equation}$$

Where the exponent, $\alpha$, determines the rate of collisions. For example, for $\alpha$ equal to 11/6 corresponds to a steady-state collisional cascade. However, in the literature (cite: 1969Dohnanyi), the steady-state collisional cascade model is often cited with the transform that shows the relative number of grains according to size:

$$\begin{equation}
 \label{eq:relnumsize}
    dN \propto s^{-q}ds
\end{equation}$$

Where $N$ is the number of grains corresponding to size $s$, and $q$ is the exponent that determines the type of collision. In this transform, a steady-state collisional cascade occurs when $q = 3.5$. Generally, for debris discs, this exponent lies between 3.0 and 4.0 (cite: 2018Hughes).

## P-R Effect and collisions

The model can include grains that undergo orbital decay due to loss of energy from the incident electromagnetic radiation on a moving non-rotating spherical grain, i.e. the P-R Effect. The time taken for grain to spiral in from outer orbit of semi-major axis ($a_i$) to an inner orbit of reduced semi-major axis ($a_f$) due to the P-R Effect (cite: 2008WyattSmallBodies): $$\begin{equation}
\label{eq:tpr}
    t_{\rm pr} = 400M^{-1}_{\star}(a_i^2-a_f^2)/{\beta},
\end{equation}$$

For simplicity, the P-R time is compared to the (estimated) mean collisional time (cite: 2010KuchnerStark):

$$\begin{equation}
\label{eq:tcoll}
    t_{coll} = \sqrt{(a_i^3/M)}/4\pi\tau,
\end{equation}$$

Where $\tau$ is the effective optical depth of planetesimal belt.

## Radiative transfer of grains

We have described how the model defines grain location, size, and composition including belt structure. We can now estimate the temperature and determine the direct thermal emission of the grains.

If thermal equilibrium is assumed, i.e. the energy that the grains absorbs is equal to its emission, then the grain temperature ($T_g$) at a specific stellar distance ($r$) is derived from the following expression (cite: 2003Wolf):

$$\begin{equation}
 \label{eq:GraintTemp}
    r = \frac{R_\star}{2} \left[\frac{\int^{\infty}_0 Q_\lambda^{abs}(s)F_\lambda(T_\star) d\lambda}{\int^{\infty}_0 Q_\lambda^{abs}(s)B_\lambda(T_g) d\lambda}\right]^{1/2}
\end{equation}$$

where $R_\star$ and $T_\star$ are star’s radius and effective temperature respectively. $F_\lambda(T)$ is the photosphere stellar model for star, $B_\lambda(T_g)$ is the blackbody function for a given grain temperature ($T_g$), and $Q_\lambda^{abs}(s)$ is the absorption efficiency calculated for a grain radius ($s$) as a function of wavelength.

To determine the direct thermal emission, we will assume grains of a particular size ($s$) are within a rotationally symmetric disc heated by the host star observed from a distance $D$. These grains are within an annulus with mean stellar distance ($r$) with a thickness of one bin size. The direct thermal emission, measured in Janskys, is derived from a modified blackbody expression:

$$\begin{equation}
 \label{eq:fluxgrain}
    F^{th}_{\lambda}(r,s) = 4\pi^2N(r,s)\left(\frac{s}{D}\right)^2Q_\lambda^{abs}(s)B_{\lambda}(T_g),
\end{equation}$$

where the grain number density ($N(r,s)$) is defined as:

$$\begin{equation}
    N(r,s) =  2\pi n s r
\end{equation}$$

corresponding to the number of grains ($n$) of a specific grain size ($s$) that are present within an annulus with a mean radius defined by the stellar distance $r$. It is noted that Equation [\[eq:fluxgrain\]](#eq:fluxgrain) is a modified form of the equation presented in both (cite: 2008Krivov) and (cite: 2010Muller) where they calculate the flux for all grains at all distances across the entire disc.

The optical properties of the Inclusion Matrix Particles (IMPs) were determined using Equation 8.50 of (cite: 1998BohrenHuffman) where f = 0.5, 0.75, and 0.9 respectively; note this method was used in (cite: 2016Morales). These types of composition is commonly referred to as ‘dirty ice’.

# Posterior probability distributions of the modelling

Here we present a corner plot showing the posterior probability distributions from the emcee runs (10,0000 realisations of the model) and the values for the maximum likelihood model parameters presented in the text (Table [\[tab:hd138965_alma_fit\]](#tab:hd138965_alma_fit), Section [\[sec:mod\]](#sec:mod)). We omit the posterior for the scale height parameter ($h$) from the corner plot as it is flat and uninformative.

![](HD138965_corner_plot.pdf)

Here we also present the corner plot (Figure [\[Fig:Corner_AS100\]](#Fig:Corner_AS100))corresponding to the probability distribution to **to help pin down inner belt characteristics where the outer belt is composed of pure astronomical silicate.**

![](HD138965AS100_corner.pdf)

[^1]: E-mail: jmarshall@asiaa.sinica.edu.tw (JPM)

</paper>

Write the methods card for this paper.