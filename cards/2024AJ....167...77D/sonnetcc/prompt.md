# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024AJ....167...77D\sonnetcc\reply.txt

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
 "bibcode": "2024AJ....167...77D",
 "title": "JWST Imaging of Edge-on Protoplanetary Disks. I. Fully Vertically Mixed 10 μm Grains in the Outer Regions of a 1000 au Disk",
 "year": 2024,
 "journal": "The Astronomical Journal",
 "first_author": "Duchêne, Gaspard",
 "n_authors": 9,
 "arxiv_id": "2309.07040",
 "doi": "10.3847/1538-3881/acf9a7",
 "alma_projects_linked_by_archive": [
  "2016.1.00771.S"
 ]
}
```

Paper text:
<paper>
# JWST imaging of edge-on protoplanetary disks. I. Fully vertically mixed 10 $\mu$m grains in the outer regions of a 1000 au disk

## Abstract

Scattered light imaging of protoplanetary disks provides key insights on the geometry and dust properties in the disk surface. Here we present JWST 2–21 $\mu$m images of a 1000 au-radius edge-on protoplanetary disk surrounding an 0.4 $M_\odot$ young star in Taurus, 2MASS J04202144+2813491. These observations represent the longest wavelengths at which a protoplanetary disk is spatially resolved in scattered light. We combine these observations with HST optical images and ALMA continuum and CO mapping. We find that the changes in the scattered light disk morphology are remarkably small across a factor of 30 in wavelength, indicating that dust in the disk surface layers is characterized by an almost gray opacity law. Using radiative transfer models, we conclude that grains up to $\gtrsim10\,\mu$m in size are fully coupled to the gas in this system, whereas grains $\gtrsim100\,\mu$m are strongly settled towards the midplane. Further analyses of these observations, and similar ones of other edge-on disks, will provide strong empirical constraints on disk dynamics and evolution and grain growth models. In addition, the 7.7 and 12. $\mu$m JWST images reveal an X-shaped feature located above the warm molecular layer traced by CO line emission. The highest elevations at which this feature is detectable roughly match the maximal extent of the disk in visible wavelength scattered light as well as of an unusual kinematic signature in CO. We propose that these phenomena could be related to a disk wind entraining small dust grains.

# Introduction

Gas-rich protoplanetary disks are the birth site of planetary systems. How the small ($\lesssim 1\,\mu$m) grains these disks inherit from their parent molecular cloud evolve to form km-sized planetesimals and, ultimately, rocky planets and cores of giant planets is hotly debated and multiple scenarios have been proposed (cite: drazkowska2022). As a first step, small grains are generally believed to grow to mm- or cm-sized pebbles by coagulation through gentle hit-and-stick interactions (cite: blum2008). Spatially unresolved (sub)mm observations of disks surrounding T Tauri stars indicate that this process is largely underway by an age of $\sim1\,$Myr (cite: williams2011). Once they have grown to large enough sizes, drag forces induced by the surrounding gas lead to their settling in the midplane and inward drift. The details of these two phenomena depend sensitively on the gas dynamics, which can be both turbulent and subject to various instabilities (cite: lesur2022). Mapping out the degree of settling and radial drift thus informs the physics of the initial stages of planet formation and disk evolution. By modifying the local dust opacity in different regions of the disk, settling has a significant influence on even unresolved observations of protoplanetary disks (cite: dullemond2004; dalessio2006) but these effects are generally ambiguous and dependent on assumptions about the disk structure.

The advent of high resolution imaging capabilities over the past decade has provided crucial insight on dust settling. In particular, the Atacama Large Millimeter/submillimeter Array (ALMA) observations of disks have shown that the vertical extent of the (sub)mm-emitting pebbles is roughly an order of magnitude smaller than that of the gas and/or $\mu$m-sized dust that dominates scattered light (cite: pinte2016; villenave2022). This is most readily illustrated in the case of edge-on disks (hereafter EODs), whose vertical extent is directly exposed to the observer. From a practical standpoint, these systems present the advantage that the disk blocks direct starlight, thus alleviating the need for coronagraphic techniques that are otherwise necessary. They are however severely underluminous as a result and, in general, cannot be observed with ground-based adaptive optics instruments. Space-based observations, with the Hubble Space Telescope (HST) and James Webb Space Telescope (JWST), are therefore necessary to image them at the required resolution. Achieving similarly high angular resolution from the optical to the millimeter regime is key to constraining settling in disks associated with T Tauri stars. Indeed, direct comparisons of HST and millimeter observations of EODs have confirmed that settling is prevalent (cite: duchene2003; villenave2020; wolff2021).

However, because those observational approaches are primarily sensitive to grains sizes that are several orders of magnitudes apart, they only provide constraints in two dramatically different regimes: $\mu$m-sized (and smaller) grains are fully coupled with the gas, whereas mm-sized pebbles are strongly decoupled. These are necessary constraints but it is critical to determine the behavior of intermediate-sized grains (several to a few tens of $\mu$m), which are only partially coupled to the gas, to fully disambiguate between disk and dust evolution models. Observations in the mid-infrared regime are crucial to fill this gap, as they are sensitive to such intermediate grains. In addition, thanks to the expected reduced opacity of dust at mid-infrared wavelengths, such observations should naturally probe deeper in the disk than the surface layers that are imaged with HST. Unresolved analyses of a few EODs have suggested that grains up to $\sim10\,\mu$m are present in the upper scattering layers (cite: pontoppidan2007; sturm2023a). This has been corroborated for the few EODs that have been imaged in the 3–5 $\mu$m range to date (cite: duchene2010; tobin2010; mccabe2011), although only two have been resolved at 10 $\mu$m (cite: mccabe2003; perrin2006). The successful deployment of JWST now provides a new opportunity to image EODs in scattered light through the near- and mid-infrared ranges.

This paper focuses on the disk surrounding 2MASS J04202144+2813491, hereafter Tau 042021. The object is located on the Western edge of the L1495 complex in the Taurus star forming-region, at a distance of 130 pc (cite: galli2019). Seeing-limited images first identified the system as an EOD, with two parallel nebulae representing the disk surfaces where stellar photons are scattered towards the observer (cite: luhman2009). Remarkably Tau 042021 is one of the largest disks known in Taurus, 50% larger than the iconic EOD HH 30 (cite: burrows1996). Deeper, higher-resolution HST images subsequently revealed a smooth and mostly symmetrical disk with a radius of at least 400 au, as well as a bright collimated bipolar atomic jet (cite: duchene2014). This indicates that the central star is actively accreting, consistent with the detection of an apparent UV excess (see Appendix [\[sec:sed\]](#sec:sed)). Based on near-infrared spectroscopy, (cite: luhman2009) estimated a spectral type of M1$\pm$2, suggesting an 0.4–0.8 $M_\odot$ for the central star. (cite: andrews2013) reported the first millimeter observation of the system, with a flux density that places it in the top quartile among other Taurus members with a similar spectral type, suggesting a relatively massive disk, consistent with its large physical size. High-resolution 0.9-1.3 mm ALMA observations were subsequently obtained by (cite: villenave2020). These marginally resolved the disk along the vertical axis, with an apparent vertical size that is several times thinner than the separation between the two disk surfaces revealed in scattered light images. Broadly speaking, the ALMA maps support the presence of strong settling in the Tau 042021 disk. (cite: villenave2020) further estimate a lower limit to the disk dust mass of $8\times10^{-5}\,M_\odot$ although optical depth effects could boost this mass by up to an order of magnitude.

This paper presents the first results of an ongoing near- to mid-infrared imaging campaign of most known EODs with JWST (GO programs 2562 and 4290 in Cycles 1 and 2, co-PIs: F. Ménard and K. R. Stapelfeldt). Specifically, we present the first 2–21 $\mu$m JWST observations of Tau 042021 to further constrain the degree of settling in this disk. We also present

CO ALMA maps to locate the warm molecular layer of the disk and to estimate the dynamical mass of the central star. Furthermore, we make use of archival GALEX, *Spitzer* and *Herschel* observations to complete the SED of the system and to probe the presence of mid-infrared emission lines. The paper is organized as follows: Section [2](#sec:obs) summarizes the new and archival observations used here, and the corresponding observational results are presented in Section [3](#sec:res). In Section [4](#sec:models), we construct several toy models, with varying degrees of settling and dust evolution to try and match the appearance of Tau 042021 across the wavelength range. We then discuss the implications of our findings in Section [5](#sec:disc).

# Observations

## JWST

We observed Tau 042021 with JWST as part of GO program 2562, using NIRCam and MIRI in two consecutive visits starting at 2023 January 23 UT 09:00. See Table [1](#tab:log) for more detail including total exposure times per filter. We used the dual channel capability of NIRCam to obtain simultaneous F200W and F444W images. With MIRI, we obtained consecutive images with the F770W, F1280W and F2100W filters. With both instruments, we used 4-point dither patterns to improve spatial sampling and mitigate detector artifacts: NIRCam used module B with the STANDARD subpixel dithering (because this target is spatially small, we did not use any large primary dither to fill in the SW inter-chip gaps), while MIRI used the BRIGHTSKY subarray and EXTENDED SOURCE dither pattern. Exposure settings (e.g. readout pattern and number of groups per integration) were chosen to avoid saturation on target, and the number of integrations per position were set to achieve the desired total integration times for high SNR on fainter surrounding nebulosity, based on ETC predictions scaled from the HST images.

We obtained the level-3 reduced and combined `i2d` data products from the Mikulski Archive for Space Telescopes (MAST). The retrieved files were reduced with pipeline version 1.8.2 (cite: bushouse2022) and using CRDS reference file context 1041. These frames are corrected for flat-field, cosmic rays and other outliers, and optical distortion, but not for background. The background in the dither-combined NIRCam images is low and uniform and we simply subtracted the median value across the frame to remove it. This approach fails for the MIRI images due to residual gradients in the background. We therefore retrieved the individual level-2 data products from MAST, generated a background frame by median-combining the exposures at each individual location of the dither patterns, subtracted it from each frame, and manually aligned and median-combined the resulting images to produce the final images of Tau 042021. Finally, we used a 5$''$ square aperture in all JWST images to measure fluxes of 2.4, 2.6, 2.3, 1.8 and 1.9 mJy in the F200W, F444W, F770W, F1280W and F2100W filters, respectively, with a conservative 10% uncertainty based on comparing these fluxes with those in larger apertures.

| Telescope | Instrument | Filter | $t_{int}$ (s) |  UT Date   |
|:---------:|:----------:|:------:|:-------------:|:----------:|
|   JWST    |   NIRCam   | F200W  |     1288      | 2023/01/23 |
|           |   NIRCam   | F444W  |     1288      | 2023/01/23 |
|           |    MIRI    | F700W  |     1052      | 2023/01/23 |
|           |    MIRI    | F1280W |     1284      | 2023/01/23 |
|           |    MIRI    | F2100W |     1326      | 2023/01/23 |
|    HST    |    ACS     | F606W  |     1300      | 2011/12/10 |
|           |    ACS     | F814W  |      840      | 2011/12/10 |

: Observing Log

Table notes: $t_{int}$ is the total on source integration time. Additional technical details for the JWST observations, such as detector readout settings per filter, may be found by retrieving APT program 2562 observations 1 and 2.

## HST

We previously observed Tau 042021 with HST/ACS as part of Program 12514 (PI: K. R. Stapelfeldt). The observations were first presented in (cite: duchene2014) and (cite: stapelfeldt2014). We obtained consecutive images with the F606W and F814W filters in a single orbit using `CRSPLIT=2` to reject cosmic rays. The images presented here are the `drz` data products available through MAST, which are corrected for flat field and optical distortion. The background level is low and uniform in both filters, and we subtracted the median value over the entire images to correct for it.

## ALMA

Continuum maps in ALMA bands 4, 6 and 7 were previously presented in (cite: villenave2020), to which we refer the reader for details about observations and data reduction. Here we report the CO J $= 2 - 1$ observations associated with the already published band 6 continuum map (program 2016.1.0771.S, PI: G. Duchêne). The source was observed using a compact array configuration on December 5, 2016 and an extended configuration on October 21, 2016. The spectral set-up was divided into two 1.9 GHz continuum spectral windows, of rest frequency 216.5 GHz and 219.6 GHz, and three spectral windows that were set-up to include the $^{12}$CO, $^{13}$CO, and C$^{18}$O J = 2 - 1 transitions at 230.538 GHz, 220.399 GHz and 219.56 GHz, respectively. Here, we focus on the $^{12}$CO and $^{13}$CO observations, which were obtained with a sampling of 122 kHz and 61 kHz, respectively. The raw data were calibrated using the CASA pipeline version 4.7.2 (cite: casa2022).

To maximize the dynamical range, we performed phase self-calibration on the continuum data for the compact configuration, and applied the continuum solution to the $^{12}$CO and $^{13}$CO spectral windows. We extracted the emission lines from the calibrated visibilities after subtracting continuum emission using the `uvcontsub` function in CASA. We used the `tclean` task, with a spectral resolution of 0.22 km s$^{-1}$ and a Briggs robust parameter of 0.5, to produce two sets of line emission maps. For the maps combining both extended and compact configuration observations, we obtain an angular resolution of 0.19$''$$\times$0.37$''$. In addition, we also use a `uvtaper` to produce a smoothed image of the $^{12}$CO channel map centered at $V-V_{sys}$= -0.3 km s$^{-1}$, which achieved an angular resolution of 0.74$''$$\times$0.67$''$.

# Results

## The dust disk in scattered light

![](gduchene_f1.pdf)

Figure [1](#fig:hst_jwst) presents a 3-color combination of selected HST and JWST images of Tau 042021, whereas Figure [2](#fig:gallery) compares all HST and JWST images along with the ALMA band 7 continuum map. All images from the optical to the mid-infrared reveal a similar morphology, namely two nearly symmetrical nebulae bisected by a dark lane, as expected for EODs. The system’s SED has its trough around 20 $\mu$m (see Figure [3](#fig:sed)), and the 21 $\mu$m image confirms that the disk is still optically thick to its own radiation out to that wavelength. In the ALMA regime, the disk is either optically thin (and emission is dominated by the denser midplane) or the two scattering surfaces are too close to each other to be fully resolved (possibly due to settling). (cite: villenave2020) showed that the intrinsic vertical extent is about 0.2$''$–0.3$''$, or 25–45 au, with a tentative identification of separation between layers, favoring the second scenario (see below).

![](gduchene_f2.pdf)

![](gduchene_f3.pdf)

The overall morphology of the disk does not qualitatively change out to 5 $\mu$m with both top and bottom nebulae showing increasing curvature as a function of distance from the symmetry axis. In the optical, faint, diffuse scattered light is detected at high elevations (up to $\approx 2$$''$ from the midplane), unlike what is seen in the 2–5 $\mu$m regime, despite comparable (or better) dynamic range in the JWST/NIRCam images. The MIRI 7.7 $\mu$m and 12.8 $\mu$m images reveal a markedly different structure, although the bisecting dark lane is still clearly present. On both sides of the disk a strong symmetrical X-shaped feature is present on top of a structure that is similar to the 4.4 $\mu$m image. This will be further explored in Section [3.3](#subsec:Xwing). At the longest JWST wavelength, the disk is back to a simple two-nebulae structure, with a significantly reduced radial extent, and a much more centrally condensed peak, which we quantify below.

![image](gduchene_f4a.pdf) ![image](gduchene_f4b.pdf)

Of interest to this study is the gradual decline in the thickness of the dark lane, measured as the distance between the peaks of the top and bottom nebulae along the disk’s symmetry axis (see Figure [4](#fig:neb_sep)). To quantify this, we followed a similar method to that presented in (cite: villenave2020). We first generated vertical brightness profiles, averaging within 0.4$''$–0.5$''$ windows to improve SNR, and fitted sixth to eighth order polynomials to the peak of each nebulae. We repeated the process out to 1.5$''$–3$''$ (depending on filter) on either side of the symmetry axis and then fitted second order polynomials to the spine of each nebulae to evaluate the closest distance between the resulting parabolas, $d_{neb}$, as well as their peak flux ratio, FWHM and full width at 10% of the peak (FW10%). The latter is useful as an indication of the disk radius. Varying the polynomial degrees used in the method, we estimate uncertainties of about 0.02$''$ on $d_{neb}$. This two-step approach is more reliable than simply using vertical brightness profile along the symmetry axis for wavelengths with significant contribution from the collimated jet. As indicated in Table [2](#tab:disk_morphology) and shown in Figure [4](#fig:neb_sep), the chromaticity of the dark lane thickness is much shallower than for other EODs (cite: watson2004; duchene2010; mccabe2011). We defer discussion of these results to Section [5.1](#subsec:growth_settling).

Since Tau 042021 is also resolved along the vertical direction in the ALMA observations (cite: villenave2020), we extracted the profile within 0.5$''$ of the symmetry axis and noticed that it presents a shoulder characteristic of two distinct components separated by a distance comparable to the projected beam size. We interpret this as an indication that the disk is still optically thick at 890 $\mu$m, but with the two disk surfaces not fully separated. We thus fitted a double Gaussian model to this profile and estimated a distance between the two surfaces of 0.11$''$$\pm$0.02$''$, roughly ten times thinner than is observed in the optical through the mid-infrared.

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Instrument | Filter | $\lambda$ | $d_{neb}$ | Flux Ratio | FWHM$_{top}$ | FWHM$_{bot}$ | FW10%$_{top}$ |
|  |  | ($\mu$m) | ($''$) |  | ($''$) | ($''$) | ($''$) |
| HST/ACS$^{$\dagger$}$ | F606W | 0.6 | 1.14 | 0.41 | 0.80 | 0.97 | 2.37 |
| HST/ACS | F814W | 0.8 | 1.17 | 0.44 | 1.11 | 1.41 | 3.40 |
| JWST/NIRCam | F200W | 2.0 | 1.11 | 0.44 | 1.13 | 1.49 | 3.47 |
| JWST/NIRCam | F444W | 4.4 | 1.04 | 0.49 | 0.99 | 1.25 | 2.69 |
| JWST/MIRI$^{$^\#$}$ | F770W | 7.7 | 0.89 | 0.56 | 1.10 | 1.62 | 2.50 |
| JWST/MIRI$^{$\dagger ^\#$}$ | F1280W | 12.8 | 0.91 | 0.61 | 1.21 | 1.63 | 2.75 |
| JWST/MIRI | F2100W | 21 | 0.96 | 0.55 | 1.18 | 1.59 | 2.85 |

: Disk Morphological properties

Table notes: The distance between the apexes of the top and bottom nebulae, $d_{neb}$, is estimated based on fitting a parabola to each spine (see Section [3.1](#subsec:dustdisk)). Their flux ratio is measured along the vertical profile at the location corresponding to this smallest separation. The FWHM of both nebulae and full width at 10% of the top nebula are estimated from the brightness profile along their respective spines. $^{\dagger}$ Dataset with significant contamination by line emission along the collimated jet. $^{\#}$ Dataset with significant contamination by the X feature.

In the HST images, the disk presents a significant lateral asymmetry in its outer regions (away from the axis of symmetry), with the top and bottom nebulae extending further in opposite directions from one another. In contrast, in the JWST images, such an asymmetry is strongly suppressed across all wavelengths.There is therefore temporal variability in the illumination from the central star, in line with the findings from (cite: luhman2009). Unfortunately, there is currently not enough temporal coverage to determine whether this variability is periodic.

The brightness ratio between top and bottom nebula in an EOD is related to the system’s inclination for symmetric disk, via the dust scattering phase function and extinction through the disk (cite: watson2007). The brightness ratio between the two nebulae is $\approx0.5$ (see Table [2](#tab:disk_morphology)), suggesting a small deviation from the $i=90$$^\circ$ configuration. We note, however, that this ratio has been found to vary and occasionally approach unity (cite: luhman2009), which precludes a definitive estimate. In addition, we find a mild increase from the optical to the mid-infrared, from $\approx0.45$ to $\approx0.6$. By comparison, this flux ratio was found to strongly increase and decrease in the cases of HK Tau B and HV Tau C, respectively (cite: duchene2010; mccabe2011).

The surface brightness profile along the spine of each nebulae is also (indirectly) driven by the scattering phase function since it probes scattering angles that range from $\approx0$$^\circ$ to $\approx90$$^\circ$ (along the major axis and at the tips of the each nebula, respectively). As indicated in Table [2](#tab:disk_morphology), both the top and bottom nebulae have essentially achromatic FWHM, with the fainter (bottom) nebula being broader than the brighter (top) one. This results from an enhanced role of multiple scattering for photons escaping through the bottom layer. This is in line with the behavior observed for HV Tau C (cite: duchene2010). Instead, in HK Tau B, the images become increasingly peakier at longer wavelengths (cite: mccabe2011), suggesting that there is diversity in the dust scattering properties of EODs. In the mid-infrared, the Tau 042021 disk appears to be somewhat more compact as measured by FW10%$_{top}$, with a decrease of 20–30% relative to the optical and near-infrared.

Finally, we note the presence of a background galaxy (clearly identified as such in the JWST 2 $\mu$m image, see Figure [1](#fig:hst_jwst)) at a projected distance of 6.6$''$, slightly interior to the gaseous disk outer edge (see Section [3.4](#subsec:gasdisk)). The galaxy is faintly detected in the HST F814W image but not in the F606W. We thus conclude that the disk must be optically thin at least at $\lambda \gtrsim 0.8\,\mu$m at this location, revealing a low column density of dust in these outer regions. Furthermore, to estimate the proper motion of Tau 042021 between the HST and JWST observing epochs, we evaluated the centroid position of the galaxy in the 0.8 $\mu$m and 2 $\mu$m images, respectively, and measured the offset from the location of peak surface brightness in the disk (center of the brighter nebula). This yields a proper motion for Tau 042021 of about 28 mas/yr South and 11 mas/yr East, with an uncertainty of about 4 mas/yr based on an estimated $\approx$1 pixel uncertainty in the disk position. This result is consistent with membership to the L1495 cloud (cite: galli2019). Interestingly, the projected separation between Tau 042021 and the background galaxy is declining so that photometric monitoring of the galaxy could be used as a probe of dust extinction in the disk over the next few decades.

## The collimated jet

Jet emission in the form of discrete knots is clearly detected in the HST and some of the JWST images. To highlight these features, we applied a 1$''$ box median filter to these images; the resulting high-passed images are shown in Figure [5](#fig:jet). A series of prominent emission knots can be traced up to $\approx6$$''$ in the HST 0.6 $\mu$m image. Jet emission in this filter is typically produced by a combination of H$\alpha$ and several nearby forbidden lines, in particular \[O I\], \[N II\] and \[S II\] (cite: ray2007). Fainter emission is also identified in the same knots in the 0.8 $\mu$m image. We speculate that these are due to \[O II\], \[S III\] or \[Fe II\] forbidden lines, which have been seen in some jet-driving T Tauri stars with near-edge-on viewing geometry (cite: bacciotti2011; whelan2014).

![](gduchene_f5.pdf)

Several knots are similarly identified in the JWST 2 $\mu$m and 12.8 $\mu$m images. In the infrared, H$_2$ and \[Ne II\] are among the dominant outflow-related emission line (cite: lahuis2007). To confirm that these lines are the likely tracers of the jet knots in the Tau 042021 system, we obtained the *Spitzer*/IRS spectrum of Tau 042021 from the Combined Atlas of Sources with *Spitzer* IRS Spectra (cite: lebouteiller2011). Although the source is faint ($\approx1$ mJy), the detection is solid and the spectrum is of good quality across the entire 5–35 $\mu$m range. Of particular interest for this study is the $\lambda \leq 15\,\mu$m regime, which contains the F770W and F1280W bandpasses in which the X-shaped feature is detected (see Section [3.3](#subsec:Xwing)). As shown in Figure [6](#fig:irs_spec), there are multiple emission lines present in the spectrum, with the most prominent being the 12.8 $\mu$m \[Ne II\] line and the H$_2$ S(1)–S(7) series (cite: sturm2023b). The former is commonly associated with disk winds and/or outflows in young stars (cite: gudel2010; pascucci2020) whereas the latter is generally thought to be due to UV excitation in the uppermost layers of disks and in photodissociative winds (cite: nomura2005; lahuis2007). We also find tentative detections of the H I 6–5, 8–6, 9–7 and 7–6 lines (7.46, 7.50, 11.31 and 12.37 $\mu$m, respectively), which are thought to be driven by accretion on the central star (cite: rigliaco2015).

![](gduchene_f6.pdf)

## A new X-shaped feature

The 7.7 $\mu$m and 12.8 $\mu$m images reveal a prominent X-shaped feature with an essentially linear shape that is absent in all other images of the system. Such straight features are often a consequence of telescope diffraction and/or detector properties, and JWST/MIRI is known for displaying such structures in some filters (cite: gaspar2021). To assess whether this feature is instrumental or astrophysical, we compare the F770W image of Tau 042021 with that of a bright point source (2MASS J04202192+2813206) observed in the same frame in Figure [7](#fig:Xwing_psf). None of the diffraction features of the hexagonal primary mirror line up with the X-shaped feature, nor does the so-called “cross artefact" that runs along the detector columns and rows. The X-shaped feature associated with Tau 042021 is therefore astrophysical in nature. Given the bandpasses of the F770W and F1280W filters, we interpret the emission in this feature as due to photodissociated H$_2$, shock-excited \[Ne II\] and/or thermal emission from out-of-equilibrium very small grains, either at the disk surface or at the base of disk wind. This can be confirmed with integral field unit JWST observations as these have different spectral characteristics.

![](gduchene_f7.pdf)

Figure [8](#fig:Xwing_co) shows the 7.7 $\mu$m image of Tau 042021 with a stretch that highlights the faint outer substructures. In addition to the X-shaped feature, fainter whiskers are seen extending at similar position angles as the disk surface traced in the 4.4 $\mu$m image. To better characterize the location of this feature, we also compare the 7.7 $\mu$m image to the molecular warm layer, as determined by the moment zero map of the $^{12}$CO emission (see Section [3.4](#subsec:gasdisk)). It appears that the warm molecular layer is located between the 5–8 $\mu$m scattered light disk “surface" and the X-shaped feature itself.

![](gduchene_f8.pdf)

The “arms" of the X-shaped feature appear remarkably linear and are well represented by symmetrical straight lines inclined $\approx36$$^\circ$ from the disk midplane. The location where the two lines intersect aligns well with the jet features seen in the 12.8 $\mu$m image (see Section [3.2](#subsec:jet)) and we therefore assume that it is the location of the central star. We further note that the arms of the feature are resolved along their minor axis, with a FWHM of $\sim$0.6$''$ in the 7.7 $\mu$m image, i.e., more than twice the instrumental resolution. It is likely that the X-shaped feature is the limb-brightened edge of a biconical structure, whose nature will be discussed in Section [5.2](#subsec:wind_pahs). This feature can be traced up to an elevation of 1.5$''$–1.75$''$ on either side of the midplane, almost as high as the most vertically extended scattered light detected in the HST optical images.

## The gaseous disk

The ALMA spectral cubes show a strong detection of the $^{12}$CO and $^{13}$CO emission, which enables us to 1) estimate the dynamical mass of the central star via its (near) Keplerian motion, and 2) probe the full radial extent of the disk.

![](gduchene_f9a.pdf)

![](gduchene_f9b.pdf)

Inspection of the spectral cubes reveals that the northern side of the disk is rotating away from the observer. By comparing the blue- and red-shifted channels, we estimate that $V_{sys} = 7.4$ km s$^{-1}$ consistent with the $\approx7.0\pm0.5$ km s$^{-1}$ range observed in the L1495 cloud (cite: galli2019). This is further confirmation that Tau 042021 is physically associated with that cloud within the Taurus complex. We also note that the $^{12}$CO disk emission is heavily suppressed in the $V_{LSR} = 7$–8 km s$^{-1}$ range, consistent with cloud emission (cite: goldsmith2008) that is filtered by the interferometer. Apart from this, the moment maps (Figure [9](#fig:momentmaps)) show the typical morphology of EODs (cite: dutrey2017; louvet2018), with the two warm molecular layers separated by a cold midplane where CO freezes out on dust grains.

We then constructed the $^{12}$CO and $^{13}$CO position-velocity diagrams and superimposed representative Keplerian curves (Figure [10](#fig:PVdiag)). A coarse exploration suggests a stellar mass in the 0.3–0.4 $M_\odot$ range. We note that this estimate is consistent with the lower end of the range derived from the system’s spectral type while the higher end of that range is firmly excluded by observations (cite: luhman2009). Conversely, the 0.25 $M_\odot$ estimated by (cite: Simon2019) is too low. We note that the best-fitting Keplerian model derived by (cite: Simon2019) present significant residuals, which may be due to a systematic bias at high inclination induced by the methodology employed by these authors or to the presence of non-Keplerian motion (see below). While obtaining a precise estimate of the stellar mass is beyond the scope of this study since it does not directly affect our analysis, we conclude that $M_\star \approx 0.4\,M_\odot$.

![](gduchene_f10.pdf)

The moment maps are well defined up to a radius of about 2$''$, significantly less than the HST or JWST radial extent but marginally larger than the submillimeter continuum (cite: villenave2020). However, faint $^{12}$CO emission is detected out to much larger distances and is best mapped in a few individual channels. On the blueshifted (South) side of the disk, the channel centered at $V - V_{sys} = -0.3$ km s$^{-1}$ reveals detectable emission in the disk upper layers out to a radius of at least $\approx8$$''$ ($\approx1000$ au, see Figure [11](#fig:COsinglechannel)). The fact that the CO emission is most extended at such a low velocity (relative to the systemic velocity) is highly unusual among EODs (cite: guilloteau2016; louvet2018; teague2020) and suggests non-Keplerian motion. Unfortunately, the corresponding red-shifted channel is devoid of emission due to filtered-out cloud emission. Nonetheless, this measured size is twice as much as in the HST and JWST images, and $\approx3.5$ times more than in the submillimeter continuum emission. This is in line with the typical ratio between gas and dust (submillimeter) component of protoplanetary disks, both edge-on and at lower inclinations (cite: ansdell2018; flores2021). This channel map shows a notably boxy pattern, essentially flat-topped, suggesting that the warm molecular layer extends over a wide range of radii at a fixed elevation of $\sim325$ au, a height that matches the end points of the X-shaped feature discussed in Section [3.3](#subsec:Xwing).

![](gduchene_f11.pdf)

# Modeling

## Objectives and modeling setup

With the data presented here, the Tau 042021 disk is now extremely well characterized, with scattered light images spanning a factor of 30 in wavelengths, several thermal emission maps in the (sub)millimeter regime, CO (2–1) spectral cubes, and a well sampled SED that includes a *Spitzer*/IRS spectrum. While simultaneously modeling all of these observables is the principled methodology to characterizing the disk structure in great detail, it is beyond the scope of this study. Instead, we adopt an exploratory approach that focuses on two key physical aspects, the grain size distribution (indicative of grain growth) and the degree of settling in the disk. To probe these phenomena in an efficient manner, we consider the thickness of the dark lane that separate the two scattered light surfaces ($d_{neb}$) as a direct, albeit reductive, observable tracer of dust opacity and disk vertical structure. All model calculations are performed with the MCFOST radiative transfer code (cite: pinte2006; pinte2009).

Concretely, we adopted the following methodology. We first fix the stellar properties based on our current knowledge of the system. Specifically, we adopt a stellar mass of 0.4 $M_\odot$ (Section [3.4](#subsec:gasdisk)) and an effective temperature of 3700 K based on the system’s spectral type and adopting the conversion law from (cite: luhman2003). We further set the stellar luminosity to $L_\star = 0.85\,L_\odot$ based on the median luminosity of Taurus members with the same spectral type (cite: luhman2009). Our model also includes a UV excess component that is evident in the short wavelength end of the system’s SED. Fitting a power law to the datapoints at $\lambda < 0.5\,\mu$m, we find that this excess is characterized by a $F_\nu \propto \nu^{-2}$ shape and a total excess of $F_{\mathrm{UV}} / F_\star = 4$% (see Figure [3](#fig:sed)). Finally, we include no foreground extinction, consistent with the GALEX detection of Tau 042021.

To describe the density structure of the gaseous component, we adopt the commonly used tapered edge surface density profile (cite: williams2011; andrews2015): $$\ \Sigma(r)\ \propto \ r^{-\gamma}\ \exp\left[ - \left(\frac{r}{r_c}\right)^{2 - \gamma_{\exp}}\right],$$ where we set $\gamma = \gamma_{\exp} = 1$ and $r_c = 300$ au, coupled with a hard outer cutoff at $r_{out} = 400$ au. These values were selected based on an initial manual exploration of the parameter space as they produced an acceptable extent along the disk major axis. We assumed a Gaussian vertical density profile, appropriate for a vertically isothermal disk, characterized by a scale height of $h_0 =11$ au at $r_0 = 100$ au and a flaring exponent of $\beta = 1.125$ so that $h(r) = h_0 (\frac{r}{r_0})^\beta$. The value for $h_0$ was computed from Eq. 6 in (cite: andrews2015), using the midplane temperature of the same initial models. The vertically isothermal assumption is incorrect as the disk surface is super-heated but the resulting difference in vertical density profile is most noticeable in the optically thin highest regions of the disk that do not contribute significantly to scattered light images. Besides, the assumption is only employed to set the vertical density structure; the temperature is subsequently computed locally during the radiative transfer calculation.

Finally, we selected an inclination of $i=88$$^\circ$, which generally leads to peak flux ratios of $\approx2$ between the two disk surfaces, consistent with the observations presented here. While model scattered light images are dependent on all of these parameters, our analysis on the wavelength dependence of the dark lane thickness is not strongly affected as it is a chromatic effect. Thus, fixing these parameters reduces dramatically the dimensionality of the problem while keeping the focus on the topic of interest here, namely the dust properties and especially their spatially-dependent size distribution. Nonetheless, a more thorough exploration of the disk structural parameters will be required in future modeling of the source. As described below, we explore models in which dust particles of all sizes are fully mixed with the gas, as well as some models in which larger grains are settled closer to the midplane.

![](gduchene_f12.pdf)

In the absence of direct quantitative constraints on the dust composition in the Tau 042021 disk, we adopted the DIANA mixture, namely a 60/15/25 (volume fraction) mixture of silicates, amorphous carbon and vacuum (cite: woitke2016). Instead of the standard Mie theory, applicable for compact spherical grains, this model uses the Distribution of Hollow Spheres method (cite: min2016), which provides absorption and scattering properties that mimic aggregate dust particles. In combination with the selected porosity, this treatment of dust scattering produces stronger forward scattering. In turn, this leads to more centrally peaked images of EODs (since the central part of the top disk surface is seen at very small scattering angles), which matches better with our observations of Tau 042021.

Regarding the grain size distribution, we first consider a “standard" model that is a $\mathrm{d}n(a) \propto a^{-p}\,\mathrm{d}a$ power law with $p=3.5$ ranging from $a_\mathrm{min} = 0.03\,\mu$m to $a_\mathrm{max} = 1$ mm, although we will also explore deviations from these default values (see Table [\[tab:model_res\]](#tab:model_res)). Furthermore, we consider a “pristine" model, in which we built a grain size distribution that produces an extinction law consistent with that observed in molecular clouds out to $\lambda = 70\,\mu$m, albeit with moderately too strong mid-infrared silicate features (see Figure [12](#fig:dust_prop)). We refer the reader to Appendix [\[sec:dust_molcloud\]](#sec:dust_molcloud) for the details of this model. We stress that this model should not be considered as physically realistic but it achieves the desired opacity law, which is the quantity we wish to probe in the Tau 042021 disk.

Since empirical evidence for dust settling of large (millimeter-emitting) dust in protoplanetary disks is now strong (cite: villenave2020), we incorporate a simple settling prescription to explore its qualitative influence on the JWST images of Tau 042021. Rather than adopting a specific physical model, which depends on poorly constrained ingredients such as the level of turbulence in a disk and the microphysics of grain-gas interactions, we adopt a simple analytical prescription, whereby grains with $a > a_\mathrm{mix}$ have a reduced scale height: $h(a) \propto (a/a_\mathrm{mix})^{\eta_\mathrm{settl}}$, with $\eta_\mathrm{settl} < 0$. Expectations from hydrodynamical and magneto-hydrodynamical turbulent settling suggest $\eta_\mathrm{settl} \gtrsim -0.5$ (cite: dubrulle1995; fromang2009), while ALMA observations indicate that $h(a \gtrsim 100\mu\mathrm{m}) \approx 1$ au (cite: pinte2016; villenave2020).

For each model (i.e., different size distribution and settling parameters), we then adjusted the disk mass to match the observed dark lane thickness at 2 $\mu$m. We selected the JWST 2 $\mu$m disk image for this as it has the best contrast/resolution combination in our datasets. Having set this last parameter, we then compute images at other wavelengths from the optical to the sub-millimeter as well as the complete SED, and determine whether it is an acceptable fit to the observations (see Table [\[tab:model_res\]](#tab:model_res)).

## Modeling results

+:---------------------------------------:+:--------------------:+:--------------------:+:--------------------:+:---------------------:+:----------------:+:--------------------:+:---------:+:----------:+:--------:+
| Model                                   | Grain Size Distribution                                            | Settling                                 | Total                | Dark Lane | 890 $\mu$m | SED      |
+-----------------------------------------+----------------------+----------------------+----------------------+-----------------------+------------------+----------------------+-----------+------------+----------+
|                                         | $p$                  | $a_\mathrm{min}$     | $a_\mathrm{max}$     | $\eta_\mathrm{settl}$ | $a_\mathrm{mix}$ | Dust Mass            | Thickness | Map        |          |
+-----------------------------------------+----------------------+----------------------+----------------------+-----------------------+------------------+----------------------+-----------+------------+----------+
|                                         |                      | ($\mu$m)             | ($\mu$m)             |                       | ($\mu$m)         | ($10^{-4}\,M_\odot$) |           |            |          |
+-----------------------------------------+----------------------+----------------------+----------------------+-----------------------+------------------+----------------------+-----------+------------+----------+
| Standard                                | 3.5                  | 0.03                 | 1000                 | None                                     | 4.9                  | ()        | $\times$   | ()       |
+-----------------------------------------+----------------------+----------------------+----------------------+------------------------------------------+----------------------+-----------+------------+----------+
| Pristine Dust                           | see Appendix [\[sec:dust_molcloud\]](#sec:dust_molcloud)           | None                                     | 2.8                  | $\times$  | $\times$   | $\times$ |
+-----------------------------------------+----------------------+----------------------+----------------------+------------------------------------------+----------------------+-----------+------------+----------+
| Shallow Size Distribution               | 3.25                 | 0.03                 | 1000                 | None                                     | 13                   |           | $\times$   | ()       |
+-----------------------------------------+----------------------+----------------------+----------------------+------------------------------------------+----------------------+-----------+------------+----------+
| No Small Dust                           | 3.5                  | 0.3                  | 1000                 | None                                     | 5.1                  |           | $\times$   | $\times$ |
+-----------------------------------------+----------------------+----------------------+----------------------+-----------------------+------------------+----------------------+-----------+------------+----------+
| Settling ($a_\mathrm{mix} = 100\,\mu$m) | 3.5                  | 0.03                 | 1000                 | 0.5                   | 100              | 4.5                  | ()        | $\times$   | ()       |
+-----------------------------------------+----------------------+----------------------+----------------------+-----------------------+------------------+----------------------+-----------+------------+----------+
| Settling ($a_\mathrm{mix} = 10\,\mu$m)  | 3.5                  | 0.03                 | 1000                 | 0.5                   | 10               | 4.9                  | ()        | ()         | ()       |
+-----------------------------------------+----------------------+----------------------+----------------------+-----------------------+------------------+----------------------+-----------+------------+----------+
| Settling ($a_\mathrm{mix} = 1\,\mu$m)   | 3.5                  | 0.03                 | 1000                 | 0.5                   | 1                | 7.0                  | $\times$  | ()         | $\times$ |
+-----------------------------------------+----------------------+----------------------+----------------------+-----------------------+------------------+----------------------+-----------+------------+----------+

![](gduchene_f13.pdf)

Figure [13](#fig:model_images_nosettling) presents a gallery of PSF-convolved model images from the optical to the sub-mm. Furthermore, Figure [14](#fig:model_geometry_nosettling) presents the wavelength dependence of the distance between the top and bottom nebulae (referred to as “dark lane thickness" in Table [\[tab:model_res\]](#tab:model_res)), measured in the same manner as in the data, as well as the observed and model SED.

Focusing first on the dark lane thickness metric, the standard model displays a decline of about 25% from the optical to the mid-infrared, similar to, albeit slightly steeper, than in the observations. The disk morphology is reasonably well reproduced, although the images are not quite as centrally peaked as in the observations, suggesting that the scattering phase function is not sufficiently forward scattering. The overall SED of the system is also satisfyingly well reproduced, although we note a strong albedo feature around 9 $\mu$m that is not seen in the *Spitzer* observations but is inherent to the dust composition adopted here. The submillimeter regime is where this model shows its largest shortcoming, with the disk much too vertically extended and showing too flared of a structure at large distances from the symmetry axis. This highlights that settling is most likely present in this system. Nonetheless, considering that the model disk mass is only set by the distance between nebulae at 2 $\mu$m in our modelling approach, we conclude that this model overall matches surprisingly well with all observations.

Conversely, the “pristine dust" model experiences a strongly chromatic dark lane thickness, with a $\gtrsim50\%$ decline from the optical to the mid-infrared, in line with its much steeper opacity law (Figure [12](#fig:dust_prop)). In addition, this model underpredicts the SED by more than an order of magnitude in the 2–20 $\mu$m range, for lack of effective scatterers in that wavelength regime. Finally, in the submillimeter regime, the model image is much too radially concentrated, as a consequence of the strongly reduced opacity of that dust model at the longest wavelengths. All in all, this model convincingly demonstrates that dust in the Tau 042021 disk is significantly different from that present in molecular cloud.

To try and reconcile the very shallow chromaticity of the dark lane with a fully mixed model, we considered two minor changes to the standard model. In the first one, we adopted a slightly shallower grain size distribution ($p = 3.25$), while in the other one we increased the minimum grain size to $a_\mathrm{min}=0.3\,\mu$m. Since both of these models produce a flatter extinction law from the optical to the near-infrared (Figure [12](#fig:dust_prop)), they succeed in matching the dark lane thickness behavior better than the standard model. However, they still produce submillimeter maps that do not match the observed one. Furthermore, the model with increased minimum grain size underpredicts the system’s SED at $\lambda \lesssim0.5\,\mu$m as all dust grains are too large to scatter such short wavelengths. These models indicate that a modest decrease in the population of small ($\lesssim0.1\,\mu$m) relative to the standard model **may** yield a satisfying match to the HST and JWST images, although it would still fail in the ALMA regime.

![image](gduchene_f14a.pdf) ![image](gduchene_f14b.pdf)

Finally, we considered three settling models in which grains up to $a_\mathrm{mix}\!=\!100\,\mu$m, $10\,\mu$m or $1\,\mu$m are fully mixed, with large grains increasingly settled with $\eta_\mathrm{settl} = -0.5$. These models yield an effective scale height of $\approx3$, 1 and 0.3 au at 100 au for 1 mm grains, respectively, in reasonable agreement with derived scale height in protoplanetary disks (cite: pinte2016; villenave2022). The $a_\mathrm{mix}\!=\!100\,\mu$m model is essentially indistinguishable from the “standard" model in all observations, indicating that this it produces an insufficient degree of settling for mm-emitting grains. For smaller values of $a_\mathrm{mix}$, settled models produce much improved 890 $\mu$m images, as expected, although the surface brightness along the major axis is not quite flat enough. However, whereas the $a_\mathrm{mix}\!=\!10\,\mu$m model shows a dark lane thickness chromaticity that is almost identical to the standard model presented above, i.e., only slightly too steep, the $a_\mathrm{mix}\!=\!1\,\mu$m model shows a significant decline at the longest mid-infrared wavelengths due to its significant settling of infrared-scattering grains. Furthermore, the SED for that model shows a deeper trough in the mid-infrared whereas the $a_\mathrm{mix}\!=\!10\,\mu$m model matches well with the observed SED, albeit with a modest overprediction in the 30–100 $\mu$m regime.

Overall, as summarized in Table [\[tab:model_res\]](#tab:model_res), we consider this brief model exploration as a strong indication that a model in which grains up to $\sim10\,\mu$m in size are fully mixed with the gas and larger grains ($\gtrsim100\,\mu$m) are increasingly settled down to a scale height of $\sim1$ au could simultaneously match the HST, JWST and ALMA continuum observations of Tau 042021. We note that the disk dust masses required to match the dark lane thickness at 2 $\mu$m are fairly high, in the $\sim 3-10 \times 10^{-4}\,M_\odot$ range. This is consistent with the lower limit derived independently by (cite: villenave2020) from ALMA continuum maps. While the dust mass is inversely proportional to the assumed dust opacity and remains therefore somewhat uncertain, the Tau 042021 disk is on the high end of the observed distribution of $M_d/M_\star$ ratio (cite: barenfeld2016), consistent with it being one the largest disks in Taurus (cite: andrews2018). We defer additional improvements upon this model, including a different scattering phase function and a more realistic settling prescription, to a further study.

# Discussion

## Dust properties and settling

With a 1000 au radius as measured in CO, Tau 042021 is one of the largest EOD in nearby star-forming regions. Its images across all wavelengths are smooth and largely symmetric and it has no known companion. It is therefore an ideal testbed for models of disk structure and dust evolution. The JWST images we presented here allow us to probe the properties of its dust component, mostly opacity and scattering phase function, as well as the degree of vertical settling in the disk.

In scattered light imaging, the thickness of the dark lane that separates the scattering surfaces is driven by the optical depth along our line of sight to the central star. In turn, this depends on the product of the disk mass and the dust opacity. The very modest drop in dark lane thickness from the optical through the mid-infrared indicates that the dust located in the upper layers of the Tau 042021 disk is characterized by a (nearly) gray opacity law over that wavelength range. Indeed, our analysis showed that a model based on a dust population consistent with that found in molecular cloud is strongly inconsistent with observations. This confirms that significant grain growth occurs in protoplanetary disks. Assuming the standard power law size distribution ($p = 3.5$), the limited dark lane chromaticy in this disk indicates that grains at least as large as 10 $\mu$m are present in copious amount in its upper layers. Similar conclusions were reached for other disks based on a variety of observation constraints, such as system SED, polarized intensity scattered light imaging or water ice absorption (cite: pontoppidan2007; tazaki2021b; franceschi2023; sturm2023a). The JWST images presented here provide a direct probe of the dust opacity in the upper outer layers of the Tau 042021 disk, which complements these other methods. Specifically, the observations presented here demonstrate the abundant presence of 10 $\mu$m-sized grains in a region located $\sim60$ au above the midplane at a radius of $\sim400$ au from the central star. Ultimately, combining these different observables, as well as the spectral shape of the mid-infrared silicate features, will enable a more granular analysis of the dust properties in the disk upper layers, including allowing for departures from simple power law parametrizations. Indeed, each observational approach is uniquely sensitive to different aspects of the dust component, both spatially and in terms of grain size.

One of the shortcomings of our “standard" model, however, is that it predicts a change in dark lane thickness between the optical and near-infrared ranges that is 10–15% too large. An even shallower dust opacity law seems necessary to account for this, as supported by our models using a shallower size distribution or a larger minimum grain size. This is an indication that the growth of dust particles may introduce a break in the slope of the distribution, as is suggested by numerical models of grain growth and fragmentation (cite: birnstiel2011). However, it is unclear if grains as large as 10 $\mu$m can efficiently grow in situ in the uppermost layers of the outer disks, where overall densities are relatively low. Instead, a (turbulent) mechanism may be necessary to loft them up from deeper layers, where they could more easily form (cite: tazaki2021b; franceschi2023).

While the fully mixed models we developed can (roughly) reproduce all HST and JWST images of Tau 042021, they produce submillimeter images that do not match the observations. In short, the optical depth through the disk is much too high, and thermally emitted photons scatter off layers that are a few tens of au above the midplane. In our models, we were able to obtain a better match to observations by introducing some settling of large grains, as suggested by other ALMA observations of protoplanetary disks. While we did not consider physical models of dust settling, our parametric approach allows us to reach some general conclusions. To reproduce the images of Tau 042021 through the HST–JWST regime, we find that grains up to $\gtrsim10\,\mu$m must be vertically fully mixed, i.e., turbulence is sufficiently strong to dredge them all the way to the disk surface. Conversely, millimeter-emitting grains (sizes $\gtrsim100\mu$m) must have a scale height that is roughly one tenth that of the gas and the smallest dust grains.

Let us now consider how this compares to settling model predictions. Pure hydrodynamical simulations (cite: dubrulle1995) indicate that the scale height of the dust component scales as $h_\mathrm{dust} \approx h_\mathrm{gas} \sqrt{\frac{\alpha}{\alpha + St}}$, where $St$ is the Stokes number, i.e. the product of the orbital frequency by the stopping time of a grain as a result of the drag force induced by the surrounding gas, and $\alpha$ the standard turbulence parameter (cite: shakura1973). In the large grain limit, $St \propto a$, leading to $h_\mathrm{dust} \propto a^{-0.5}$ in the case of weak turbulence ($\alpha \ll St$). Therefore, mm-sized dust are expected to have a scale height that is $\approx 10$ times smaller than that of 10 $\mu$m grains, in line with our findings. Magneto-hydrodynamical models, on the other hand, predict shallower dependencies: (cite: fromang2009) find an $h_\mathrm{dust} \propto St^{-0.2}$ approximate relationship, for instance. This may imply that the importance of magnetized transport is reduced in the outer regions of the Tau 042021 disk, which are primarily traced by scattered light images. However, (cite: riols2018) have shown that, while the hydrodynamical solutions may be approximately correct in the context of 1D models, higher dimension simulations reveal more complex behaviors, in which it is nearly impossible to characterize settling through a single scale height quantity. To make matters worse, both types of simulations concur on the fact that the relevant quantity is not directly the size of dust grains but their Stokes number. Because the latter depends also on the local gas density and the material density of the dust particles, the constraint we have obtained from the JWST images presented here can only be indirectly compared to such models. We leave the comparison of more physically-grounded settling models with JWST images to future studies.

While the models we have constructed reproduce the dark lane thickness, they are imperfect when considering the overall morphology of the Tau 042021 disk. In particular, model images appear consistently less centrally peaked than is observed, especially at the longest JWST wavelengths. Although this may be due to a combination of factors, we suspect that a main issue is that the dust prescription we have used leads to a scattering phase function that is not sufficiently forward scattering. The more peaky phase functions could be either due to solid grains with a lower refractive index (i.e., more ice rich) or porous aggregates. Indeed, lower refractive indices of solid grains facilitate efficient transmission of light, leading to more efficient forward scattering (cite: tazaki2021). Porous aggregates are also known as efficient forward scatterers (cite: min2012; tazaki2019), although the phase function depends on the detailed structure of aggregates, such as fractal dimension (cite: min2016; tazaki2016; tobon2022). Future modeling of this system should explore such dust properties to improve the match between observed and model scattered light images of Tau 042021 (R. Tazaki, priv. comm.).

Finally, we note that the modest chromaticity of the dark lane thickness in Tau 042021 is in stark contrast with previously-imaged EODs, which become markedly thinner towards longer wavelengths, at least out to 5 $\mu$m (cite: duchene2010; mccabe2011). One possible explanation is that this system contains a shallower size distribution than other disks, possibly as a result of more advanced dust evolution. It could also be the case that the Tau 042021 disk is more optically thick than other EODs. Indeed, in the limit of very high optical depths, the chromatic dependence of the opacity law is gradually muted with increasing disk mass as the elevation of $\tau = 1$ surface does not depend much of the total column density in the disk since the density drops rapidly in the disk atmosphere. In other words, if the disk is very optically thick up to $\approx60au$ above the midplane at $\lambda<21\,\mu$m and the density drops extremely fast above this layer, the lack of chromaticity could be explained with a wide range of grain sizes. The gradual decline in surface brightness in the optical HST images seems to argue against this scenario but further analyses are needed to definitely rule it out. JWST observations of other EODs will allow us to place Tau 042021 in the larger context.

## A possible disk wind

Arguably the most surprising outcome of the JWST observations of Tau 042021 is the X-shaped feature that is prominent at 7.7 and 12.8 $\mu$m and resides immediately above the warm molecular layer traced by the ALMA $^{12}$CO mapping, at elevations up to $\sim225$ au. Without follow-up spectroscopic observations, no definitive conclusion can be reached about its nature. Given its large opening angle ($\sim35$$^\circ$ above the midplane), this feature must arise in the highest layers of the disk, or in a wind above the disk, and over a broad range of stellocentric distances. In this context, it is worth recalling two other unusual features of this system: 1) the presence of scattered light in the optical up to $\gtrsim250$ au above the midplane, and 2) the unusually extended CO channel map at a very small velocity relative to the systemic velocity, also marking surfaces that are about $\sim325$ au above the midplane. The similarity in elevation between these various features suggest a common origin.

Since the diffuse optical emission observed in this region is found in two separate filters, it is unlikely to be due to line emission and instead points to a scattered light nature. The absence of this component in even the shortest wavelength JWST image suggests scattering off of small ($\lesssim1\,\mu$m) grains. Conversely, the X-shaped feature is unlikely to be solely due to scattering since it is not detected in the 4.4 $\mu$m image. We speculate that it could be due to H$_2$ photodissociation, or to out-of-equilibrium thermal emission from very small ($\lesssim0.1\mu$m) grains in the disk atmosphere that are in direct view of the X- and UV-emitting central source. In the H$_2$ interpretation, we note the lack of detection of the S(0) line (at 28.2 $\mu$m) in the IRS spectrum and the absence of the X-shaped feature in the 4.4 $\mu$m image, which contains the S(9) line (at 4.7 $\mu$m). In conjunction, these would suggest an excitation temperature of $\lesssim100$ K (cite: nomura2005; lahuis2007). Polycyclic aromatic hydrocarbons (PAHs) are commonly observed in the 3–15 $\mu$m range in disks surrounding more massive Herbig AeBe stars (cite: meeus2001), and it is plausible that the active accretion from the central source in Tau 042021 can excite such grains even though it is not intrinsically as hot (cite: siebenmorgen2012). We note that, while the X-shaped feature is prominent in the JWST images presented here, it represents a small fraction of the integrated brightness of the system, so that PAHs could remain undetected in the *Spitzer*/IRS spectrum. It is also possible that the out-of-equilibrium grains have a more standard composition, in which case their stochastic emission would appears as a sum of warmer-than-expected blackbodies (cite: draine2001). Ultimately, the only requirement for this process to occur is that the grains are very small, to the point where the absorption of a single UV photon can overheat them for a short time. If this very small grain interpretation is correct, it could be common among T Tauri systems, and mid-infrared integral field unit spectroscopy of a large sample could confirm this conclusion.

A plausible scenario to explain these various features invokes a photodissociative disk wind (cite: owen2011; bai2016). In this picture, the UV emission from the central star (and accretion column) dissociates molecules located at the very top of the warm molecular layer. The excited atoms escape the disk surface and are then placed on ballistic outward trajectories. Recombination of H$_2$ molecules along them could then produce the X-shaped feature through limb brightening of the conical wind, while the non-Keplerian flow of the wind could possible lead to the odd-looking low-velocity CO channel map. It is also possible that PAHs and other very small grains are entrained along with the gas and get stochastically heated once they reach high enough layers from which they are in direct sight of the central source. Furthermore, if this wind can entrain grains as large as 0.1–1 $\mu$m, this would naturally produce a “veil" of optical scattered light well above the disk midplane, as is observed in Tau 042021. Current disk wind models suggest that entrainment of such grains is possible (cite: booth2021; rodenkirch2022; franz2022). In summary, such a scenario can qualitatively reproduce some of the unexpected features observed in this system, but we defer to a later study a physically-grounded wind model.

# Conclusion

In this study, we have presented new optical through suubmillimeter high-resolution observations of the Tau 042021 edge-on protoplanetary disk. With a $\approx1000$ au radius, this disk is one of the largest disks known in nearby star-forming regions, and it shows a smooth and symmetrical structure. This makes it a perfect prototype to study the disk structure and dust properties in such environments.

We have presented the first JWST observations of Tau 042021, imaging its edge-on protoplanetary disk from 2 to 21 $\mu$m, which we interpret in combination with HST images at 0.6 and 0.8 $\mu$m. The disk is observed in scattered light throughout the entire wavelength range considered here, and shows very modest levels of chromaticity. In particular, the thickness of the dark lane that separate the two disk surfaces only declines by $\sim15$% from 0.6 to 21 $\mu$m, a much shallower decline than has been observed for other edge-on disks (over more limited wavelengths ranges). We also find that up to 21 $\mu$m, the vertical extent of the disk is an order of magnitude larger than observed in ALMA continuum maps, a confirmation that the large, millimeter-emitting grains, must be strongly settled. To interpret these observations, we build radiative transfer models that explore the role of the grain size distribution and degree of dust settling in the disk. We conclude that grains up to $\gtrsim10\mu$m in size are fully coupled to the gas up to the disk surface layers, whereas particles larger than $\gtrsim100\mu$m must be concentrated $\sim10$ times closer to the midplane. This is the first time observations provide a direct constraint on the degree of settling of grains in the 10 $\mu$m size regime via a spatially-resolved analysis of dust opacity. Future studies of other edge-on disks will help place this system in context and identify the underlying physical processes that are responsible for settling and, ultimately, growth, of dust particles in disks.

In addition to analyzing the scattered light properties of the disk, the HST and JWST images reveal multiple knots of emission from the jet launched by the central source. Multiple emission line features are also detected in the *Spitzer*/IRS spectrum of the system. The ALMA CO observations yield an estimate of the stellar mass ($\sim0.4\,M_\odot$) that is on the low end of the range suggested by past spectroscopic observations. Finally, we have also identified several unexpected features in this system. The HST optical images point to the presence of $\lesssim1\,\mu$m grains located up to 250 au above the disk midplane. The $^{12}$CO channel maps reveal a $\sim300$ au-elevation CO layer with unusual kinematic properties, suggesting non-Keplerian motion. Finally, and most intriguingly, the 7.7 and 12.8 $\mu$m JWST images reveal a X-shaped feature that is located above the CO warm molecular layer. We propose that these various features can be explained if the disk drives a significant photoevaporative disk wind that entrains small dust grains. Follow-up spectroscopic observations of this system can help identify the nature of the X-shaped feature and its relationship to the other phenomena.

This project has received funding from the European Research Council (ERC) under the European Union’s Horizon Europe research and innovation program (grant agreement No. 101053020, project Dust2Planets, PI F.Ménard). GD, KRS, MV, and SGW acknowledge funding support from JWST GO program #2562 provided by NASA through a grant from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Incorporated, under NASA contract NAS5-26555. We are grateful to the W.M. Keck Institute for Space Studies as the hosts for our week-long team meeting in May 2023. CP acknowledges Australian Research Council funding via FT170100040, DP18010423 and DP220103767. RT acknowledges financial support from a CNES postdoc fellowship. MV research was supported by an appointment to the NASA Postdoctoral Program at the Jet Propulsion Laboratory, administered by Oak Ridge Associated Universities under contract with NASA. Some of the data presented in this paper were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute. The specific JWST observations analyzed can be accessed via . This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.0771.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Facilities

JWST (NIRCam and MIRI), HST (ACS), ALMA

# Compiling the SED of the system 

To produce the complete SED of the system, we complement the new JWST photometric datapoints presented in this study and the IRS spectrum (Section [3.1](#subsec:dustdisk)) with published and archival data. The complete SED is presented in Figure [3](#fig:sed) while Table [3](#tab:sed) summarizes the photometry adopted here (see below), as well as the new JWST fluxes.

+--------------------+---------------+------------------+-----------+
| $\lambda$ ($\mu$m) | $F_\nu$ (mJy) | Observatory      | Reference |
+:==================:+:=============:+:================:+:=========:+
| 0.23               | 0.010         | GALEX            | 1         |
+--------------------+---------------+------------------+-----------+
| 0.36               | 0.030         | SDSS             | 2         |
+--------------------+---------------+------------------+-----------+
| 0.48               | 0.045         | ”                | 2         |
+--------------------+---------------+------------------+-----------+
| 0.62               | 0.17          | ”                | 2         |
+--------------------+---------------+------------------+-----------+
| 0.76               | 0.28          | ”                | 2         |
+--------------------+---------------+------------------+-----------+
| 0.91               | 0.56          | ”                | 2         |
+--------------------+---------------+------------------+-----------+
| 1.22               | 0.74          | 2MASS            | 3         |
+--------------------+---------------+------------------+-----------+
| 1.63               | 1.27          | ”                | 3         |
+--------------------+---------------+------------------+-----------+
| 2.19               | 1.58          | ”                | 3         |
+--------------------+---------------+------------------+-----------+
| 3.6                | 2.1           | *Spitzer*/IRAC   | 4         |
+--------------------+---------------+------------------+-----------+
| 4.5                | 1.9           | ”                | 4         |
+--------------------+---------------+------------------+-----------+
| 5.8                | 1.61          | ”                | 4         |
+--------------------+---------------+------------------+-----------+
| 8.0                | 1.42          | ”                | 4         |
+--------------------+---------------+------------------+-----------+
| 24                 | 2.0           | *Spitzer*/MIPS   | 4         |
+--------------------+---------------+------------------+-----------+
| 70                 | 75            | ”                | 4         |
+--------------------+---------------+------------------+-----------+
| 100                | 298           | *Herschel*/PACS  | 5         |
+--------------------+---------------+------------------+-----------+
| 160                | 445           | ”                | 5         |
+--------------------+---------------+------------------+-----------+
| 250                | 394           | *Herschel*/SPIRE | 6         |
+--------------------+---------------+------------------+-----------+
| 350                | 340           | ”                | 6         |
+--------------------+---------------+------------------+-----------+
| 500                | 236           | ”                | 6         |
+--------------------+---------------+------------------+-----------+
| 890                | 124           | ALMA             | 7         |
+--------------------+---------------+------------------+-----------+
| 1330               | 52            | SMA              | 8         |
+--------------------+---------------+------------------+-----------+
| 1340               | 47            | ALMA             | 7         |
+--------------------+---------------+------------------+-----------+
| 2060               | 15            | ”                | 7         |
+--------------------+---------------+------------------+-----------+
| New JWST Photometry                                               |
+--------------------+---------------+------------------+-----------+
| 2.0                | 2.4           | JWST/NIRCam      | 6         |
+--------------------+---------------+------------------+-----------+
| 4.4                | 2.6           | JWST/NIRCam      | 6         |
+--------------------+---------------+------------------+-----------+
| 7.7                | 2.3           | JWST/MIRI        | 6         |
+--------------------+---------------+------------------+-----------+
| 12.8               | 1.8           | JWST/MIRI        | 6         |
+--------------------+---------------+------------------+-----------+
| 21.0               | 1.9           | JWST/MIRI        | 6         |
+--------------------+---------------+------------------+-----------+

: Adopted system SED for Tau 042021

Table notes: References: 1) GALEX GR6/GR7; 2) (cite: ahumada2020); 3) (cite: cutri2003); 4) (cite: rebull2010); 5) (cite: herschel2017); 6) This work; 7) (cite: villenave2020); 8) (cite: andrews2013).

Tau 042021 was detected by GALEX with its NUV channel (0.18–0.28 $\mu$m) in a 2662 s exposure as part of the Medium Imaging Survey. We retrieved the corresponding flux density from the GR6/GR7 source catalog available through the MAST portal[^1]. The GALEX detection suggests that the source is actively accreting, consistent with the presence of the collimated atomic jet, and that it is not significantly extincted by foreground cloud material. No corresponding FUV (0.13–0.18 $\mu$m) observation was taken. In the optical range, we adopted the SDSS DR16 (cite: ahumada2020) “Petrossian" magnitudes of Tau 042021. These represent an aperture photometry method with a radius based on the extent of the source; while this method was designed for galaxies, we assume that it operates reasonably well for any smooth, extended source. In the far-infrared, Tau 042021 was observed with *Herschel* as part of the “*Herschel* Gould Belt Survey" Guaranteed Time Key Program (cite: andre2010). PACS flux densities are available through the *Herschel* PACS Point Source Catalog (cite: herschel2017). To complete the SED, we retrieved the level 2.5 SPIRE (250, 350 and 500 $\mu$m) data products from the *Herschel* archive and averaged the individual frames to produce final images in each filter. Tau 042021 is clearly detected – and unresolved – in all filters. Following the SPIRE Handbook, we estimated photometry for the system using Gaussian fitting and applying band-appropriate aperture corrections to obtain the far-infrared flux densities of Tau 042021. The resulting measurements, for which we estimate a 10% relative uncertainty due to a combination of absolute calibration error and uncertainties due to the complex background, are listed in Table [3](#tab:sed). We note that a “starless core" was identified by (cite: marsh2016) at the location of Tau 042021, using the same *Herschel* data. The SPIRE flux densities estimated by these authors are broadly consistent with our estimates. However, their 160 $\mu$m measurement is about 33% lower than that estimated by (cite: herschel2017), probably as a result of methodological differences. As a result, we decided against adopting their *Herschel* photometry both to ensure consistency and to avoid an implausible break between 100 and 160 $\mu$m.

In some regimes, Tau 042021 is detected in multiple catalogs and surveys, which reveals significant variability in some cases. In the optical, the Pan-STARRS Kron photometry (cite: chambers2016) is consitent with the SDSS photometry adopted here to within 20% or so. On the other hand, the UKIDSS photometry (cite: lawrence2012) is a factor of $\approx2$ fainter than the 2MASS photometry, and the 3.4 and 4.6 $\mu$m WISE flux densities (cite: cutri2012) are about 30% lower than the corresponding Spitzer/IRAC ones (cite: rebull2010). Finally, the integrated flux densities measured in the JWST images presented here are 20–60% higher than the *Spitzer* measurements in the 4–8 $\mu$m, whereas the 20 $\mu$m JWST flux is consistent with the 24 $\mu$m *Spitzer* one. All in all, the source is affected by a typical variability of up to a factor of $\approx2$ from the optical to the mid-infrared, which is in line with the morphological variability noted by (cite: luhman2009) in the near-infrared. Here we selected datasets on the basis of producing a smoothly continuous SED but we caution against interpreting any photometric point without taking into consideration this significant variability.

Finally, we performed power law fits to the (sub)millimeter and UV/blue regimes of the SED, which led to spectral indices of $\alpha_\mathrm{mm} = 2.5$ (cite: villenave2020) and $\alpha_\mathrm{UV} = -2.0$, defined by $F_\nu \propto \nu^\alpha$. In particular, at $\lambda \lesssim0.5\,\mu$m, the system’s SED presents a markedly different spectral index from the rest of the optical regime, suggesting the presence of a significant accretion-driven UV excess and we use the latter index in our modeling setup (Section [4.1](#subsec:models_setup)).

# Dust opactiy in molecular clouds 

The extinction law in the interstellar medium (ISM) and molecular clouds has long been used as a probe into the grain size distribution in these environments (cite: draine2003). In particular, the realization that the extinction law in molecular cloud flattens out in the near- to mid-infrared range revealed the presence of larger grains in these clouds than in the diffuse ISM (cite: lutz1999; flaherty2007), suggesting that the initial stages of grain growth occur before the formation of stars and their disks. To determine the extent and timescale of grain growth in disks, it is therefore necessary to develop a model of the dust population of molecular clouds, whose properties can then be compared to observations of protoplanetary disks, such as those presented in the present study.

Unlike the case of the diffuse Galactic ISM, the extinction law in molecular clouds is not a unique curve, as it depends, among other things, on the temperature and column density of the cloud. Furthermore, no single observational method can probe extinction from the short-wavelength optical to the mid-infrared, requiring combining multiple studies that may inherently probe different environments. Fortunately, the agreement between studies is sufficient for our purposes, as we show below.

![](gduchene_f15.pdf)

To construct the extinction law in the molecular clouds, we focus on *Spitzer* studies. Specifically, (cite: flaherty2007) and (cite: chapman2009) provided broadband extinction laws ranging from 3.6 to 24 $\mu$m for multiple nearby star-forming regions. In both cases, we computed the weighted average of the individual line of sight extinction laws. We note that the $1 \leq A_K < 2$ and $A_K \geq 2$ curves from (cite: chapman2009) bracket the 24 $\mu$m estimate from (cite: flaherty2007) and are comparable to the latter at $\lambda \leq 8\,\mu$m. (cite: lim2015) extend broadband extinction through an infrared dark cloud to longer wavelengths (12, 24 and 70 $\mu$m). Again, we computed the average of the various line of sights they studied and anchored their relationship to the 8 $\mu$m extinction coefficient from (cite: flaherty2007). Finally, (cite: mcclure2009) used 5–20 $\mu$m spectroscopy to sample the extinction law across the silicate feature. To improve signal-to-noise, we resampled their extinction curve to a resolution of $R\approx15$. Altogether, we find that these different extinction laws agree to $\approx10\%$ across the near- to mid-infrared range (Figure [15](#fig:ext_molcloud)). To produce a representative extinction law, we adopt the (cite: flaherty2007) datapoints from 3.6 to 24 $\mu$m, together with the 70 $\mu$m point from (cite: lim2015) and the resampled IRS spectrum from (cite: mcclure2009). At shorter wavelengths, we adopted the "Case B" $R_V=5.5$ curve from (cite: weingartner2001), as it has been found to match extinction in molecular clouds out to at least 5 $\mu$m. We emphasize that this is an hybrid extinction law that we only use as a general guideline.

We then constructed a “pristine dust" model that attempts to match the observed extinction law in molecular clouds. We assume the same composition as in our dust models (see Section [4.1](#subsec:models_setup)). No single power law size distribution can simultaneously reproduce the steep drop-off across the optical and near-infrared and the nearly flat extinction law across the mid-infrared. We therefore used a model that combines two power laws: a $p=-3$ power law for grains sizes ranging from 0.03 $\mu$m to 0.35 $\mu$m, and a $p=-1.5$ power law from 0.35 $\mu$m to 100 $\mu$m. The normalization constants for both power laws are such that 80% of the total mass is in the large grains component. This model produces an extinction law that matches well (within $\approx$10%) all broadband estimates of the extinction law, although it produces mid-infrared silicate features that are too strong (Figure [12](#fig:dust_prop)). This is likely a result of the silicate-rich nature of the adopted composition coupled with the large contribution of the smallest dust grains. However, any attempt to suppress the silicate feature in our simplified framework led to a much poorer match to the broadband extinction law. This indicates that this dust model is not physically accurate, which is further reinforced by the sharp break at a grain size of 0.35 $\mu$m. Nonetheless, this model produces the correct broadband opacity across the broad range of wavelengths of interest for our study and thus we consider that it is a good proxy for molecular cloud dust.

natexlab

(ref: ahumada2020) Ahumada, R., Allende Prieto, C., Almeida, A., et al. 2020, ApJS, 249, 3, doi: [`10.3847/1538-4365/ab929e`](http://doi.org/10.3847/1538-4365/ab929e)

(ref: andre2010) André, P., Men’shchikov, A., Bontemps, S., et al. 2010, A&A, 518, L102, doi: [`10.1051/0004-6361/201014666`](http://doi.org/10.1051/0004-6361/201014666)

(ref: andrews2015) Andrews, S. M. 2015, PASP, 127, 961, doi: [`10.1086/683178`](http://doi.org/10.1086/683178)

(ref: andrews2013) Andrews, S. M., Rosenfeld, K. A., Kraus, A. L., & Wilner, D. J. 2013, ApJ, 771, 129, doi: [`10.1088/0004-637X/771/2/129`](http://doi.org/10.1088/0004-637X/771/2/129)

(ref: andrews2018) Andrews, S. M., Terrell, M., Tripathi, A., et al. 2018, ApJ, 865, 157, doi: [`10.3847/1538-4357/aadd9f`](http://doi.org/10.3847/1538-4357/aadd9f)

(ref: ansdell2018) Ansdell, M., Williams, J. P., Trapman, L., et al. 2018, ApJ, 859, 21, doi: [`10.3847/1538-4357/aab890`](http://doi.org/10.3847/1538-4357/aab890)

(ref: bacciotti2011) Bacciotti, F., Whelan, E. T., Alcalá, J. M., et al. 2011, ApJL, 737, L26, doi: [`10.1088/2041-8205/737/2/L26`](http://doi.org/10.1088/2041-8205/737/2/L26)

(ref: bai2016) Bai, X.-N., Ye, J., Goodman, J., & Yuan, F. 2016, ApJ, 818, 152, doi: [`10.3847/0004-637X/818/2/152`](http://doi.org/10.3847/0004-637X/818/2/152)

(ref: barenfeld2016) Barenfeld, S. A., Carpenter, J. M., Ricci, L., & Isella, A. 2016, ApJ, 827, 142, doi: [`10.3847/0004-637X/827/2/142`](http://doi.org/10.3847/0004-637X/827/2/142)

(ref: birnstiel2011) Birnstiel, T., Ormel, C. W., & Dullemond, C. P. 2011, A&A, 525, A11, doi: [`10.1051/0004-6361/201015228`](http://doi.org/10.1051/0004-6361/201015228)

(ref: blum2008) Blum, J., & Wurm, G. 2008, ARA&A, 46, 21, doi: [`10.1146/annurev.astro.46.060407.145152`](http://doi.org/10.1146/annurev.astro.46.060407.145152)

(ref: booth2021) Booth, R. A., & Clarke, C. J. 2021, MNRAS, 502, 1569, doi: [`10.1093/mnras/stab090`](http://doi.org/10.1093/mnras/stab090)

(ref: burrows1996) Burrows, C. J., Stapelfeldt, K. R., Watson, A. M., et al. 1996, ApJ, 473, 437, doi: [`10.1086/178156`](http://doi.org/10.1086/178156)

(ref: bushouse2022) Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2022, JWST Calibration Pipeline, 1.8.2, Zenodo, Zenodo, doi: [`10.5281/zenodo.7229890`](http://doi.org/10.5281/zenodo.7229890)

(ref: casa2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: chambers2016) Chambers, K. C., Magnier, E. A., Metcalfe, N., et al. 2016, arXiv e-prints, arXiv:1612.05560, doi: [`10.48550/arXiv.1612.05560`](http://doi.org/10.48550/arXiv.1612.05560)

(ref: chapman2009) Chapman, N. L., Mundy, L. G., Lai, S.-P., & Evans, Neal J., I. 2009, ApJ, 690, 496, doi: [`10.1088/0004-637X/690/1/496`](http://doi.org/10.1088/0004-637X/690/1/496)

(ref: cotera2001) Cotera, A. S., Whitney, B. A., Young, E., et al. 2001, ApJ, 556, 958, doi: [`10.1086/321627`](http://doi.org/10.1086/321627)

(ref: cutri2012) Cutri, R. M., & et al. 2012, VizieR Online Data Catalog, II/311

(ref: cutri2003) Cutri, R. M., Skrutskie, M. F., van Dyk, S., et al. 2003, VizieR Online Data Catalog, II/246

(ref: dalessio2006) D’Alessio, P., Calvet, N., Hartmann, L., Franco-Hernández, R., & Servı́n, H. 2006, ApJ, 638, 314, doi: [`10.1086/498861`](http://doi.org/10.1086/498861)

(ref: draine2003) Draine, B. T. 2003, ARA&A, 41, 241, doi: [`10.1146/annurev.astro.41.011802.094840`](http://doi.org/10.1146/annurev.astro.41.011802.094840)

(ref: draine2001) Draine, B. T., & Li, A. 2001, ApJ, 551, 807, doi: [`10.1086/320227`](http://doi.org/10.1086/320227)

(ref: drazkowska2022) Drazkowska, J., Bitsch, B., Lambrechts, M., et al. 2022, arXiv e-prints, arXiv:2203.09759, doi: [`10.48550/arXiv.2203.09759`](http://doi.org/10.48550/arXiv.2203.09759)

(ref: dubrulle1995) Dubrulle, B., Morfill, G., & Sterzik, M. 1995, Icarus, 114, 237, doi: [`10.1006/icar.1995.1058`](http://doi.org/10.1006/icar.1995.1058)

(ref: duchene2003) Duchêne, G., Ménard, F., Stapelfeldt, K., & Duvert, G. 2003, A&A, 400, 559, doi: [`10.1051/0004-6361:20021906`](http://doi.org/10.1051/0004-6361:20021906)

(ref: duchene2010) Duchêne, G., McCabe, C., Pinte, C., et al. 2010, ApJ, 712, 112, doi: [`10.1088/0004-637X/712/1/112`](http://doi.org/10.1088/0004-637X/712/1/112)

(ref: duchene2014) Duchêne, G., Stapelfeldt, K., Isella, A., et al. 2014, in Exploring the Formation and Evolution of Planetary Systems, ed. M. Booth, B. C. Matthews, & J. R. Graham, Vol. 299, 111–112, doi: [`10.1017/S174392131300803X`](http://doi.org/10.1017/S174392131300803X)

(ref: dullemond2004) Dullemond, C. P., & Dominik, C. 2004, A&A, 421, 1075, doi: [`10.1051/0004-6361:20040284`](http://doi.org/10.1051/0004-6361:20040284)

(ref: dutrey2017) Dutrey, A., Guilloteau, S., Piétu, V., et al. 2017, A&A, 607, A130, doi: [`10.1051/0004-6361/201730645`](http://doi.org/10.1051/0004-6361/201730645)

(ref: flaherty2007) Flaherty, K. M., Pipher, J. L., Megeath, S. T., et al. 2007, ApJ, 663, 1069, doi: [`10.1086/518411`](http://doi.org/10.1086/518411)

(ref: flores2021) Flores, C., Duchêne, G., Wolff, S., et al. 2021, AJ, 161, 239, doi: [`10.3847/1538-3881/abeb1e`](http://doi.org/10.3847/1538-3881/abeb1e)

(ref: franceschi2023) Franceschi, R., Birnstiel, T., Henning, T., & Sharma, A. 2023, A&A, 671, A125, doi: [`10.1051/0004-6361/202244869`](http://doi.org/10.1051/0004-6361/202244869)

(ref: franz2022) Franz, R., Ercolano, B., Casassus, S., et al. 2022, A&A, 657, A69, doi: [`10.1051/0004-6361/202140812`](http://doi.org/10.1051/0004-6361/202140812)

(ref: fromang2009) Fromang, S., & Nelson, R. P. 2009, A&A, 496, 597, doi: [`10.1051/0004-6361/200811220`](http://doi.org/10.1051/0004-6361/200811220)

(ref: galli2019) Galli, P. A. B., Loinard, L., Bouy, H., et al. 2019, A&A, 630, A137, doi: [`10.1051/0004-6361/201935928`](http://doi.org/10.1051/0004-6361/201935928)

(ref: gaspar2021) Gáspár, A., Rieke, G. H., Guillard, P., et al. 2021, PASP, 133, 014504, doi: [`10.1088/1538-3873/abcd04`](http://doi.org/10.1088/1538-3873/abcd04)

(ref: goldsmith2008) Goldsmith, P. F., Heyer, M., Narayanan, G., et al. 2008, ApJ, 680, 428, doi: [`10.1086/587166`](http://doi.org/10.1086/587166)

(ref: gudel2010) Güdel, M., Lahuis, F., Briggs, K. R., et al. 2010, A&A, 519, A113, doi: [`10.1051/0004-6361/200913971`](http://doi.org/10.1051/0004-6361/200913971)

(ref: guilloteau2016) Guilloteau, S., Piétu, V., Chapillon, E., et al. 2016, A&A, 586, L1, doi: [`10.1051/0004-6361/201527620`](http://doi.org/10.1051/0004-6361/201527620)

(ref: herschel2017) Herschel Point Source Catalogue Working Group, Marton, G., Calzoletti, L., et al. 2020, VizieR Online Data Catalog, VIII/106

(ref: lahuis2007) Lahuis, F., van Dishoeck, E. F., Blake, G. A., et al. 2007, ApJ, 665, 492, doi: [`10.1086/518931`](http://doi.org/10.1086/518931)

(ref: lawrence2012) Lawrence, A., Warren, S. J., Almaini, O., et al. 2012, VizieR Online Data Catalog, II/314

(ref: lebouteiller2011) Lebouteiller, V., Barry, D. J., Spoon, H. W. W., et al. 2011, ApJS, 196, 8, doi: [`10.1088/0067-0049/196/1/8`](http://doi.org/10.1088/0067-0049/196/1/8)

(ref: lesur2022) Lesur, G., Ercolano, B., Flock, M., et al. 2022, arXiv e-prints, arXiv:2203.09821, doi: [`10.48550/arXiv.2203.09821`](http://doi.org/10.48550/arXiv.2203.09821)

(ref: lim2015) Lim, W., Carey, S. J., & Tan, J. C. 2015, ApJ, 814, 28, doi: [`10.1088/0004-637X/814/1/28`](http://doi.org/10.1088/0004-637X/814/1/28)

(ref: louvet2018) Louvet, F., Dougados, C., Cabrit, S., et al. 2018, A&A, 618, A120, doi: [`10.1051/0004-6361/201731733`](http://doi.org/10.1051/0004-6361/201731733)

(ref: luhman2009) Luhman, K. L., Mamajek, E. E., Allen, P. R., & Cruz, K. L. 2009, ApJ, 703, 399, doi: [`10.1088/0004-637X/703/1/399`](http://doi.org/10.1088/0004-637X/703/1/399)

(ref: luhman2003) Luhman, K. L., Stauffer, J. R., Muench, A. A., et al. 2003, ApJ, 593, 1093, doi: [`10.1086/376594`](http://doi.org/10.1086/376594)

(ref: lutz1999) Lutz, D. 1999, in ESA Special Publication, Vol. 427, The Universe as Seen by ISO, ed. P. Cox & M. Kessler, 623

(ref: marsh2016) Marsh, K. A., Kirk, J. M., André, P., et al. 2016, MNRAS, 459, 342, doi: [`10.1093/mnras/stw301`](http://doi.org/10.1093/mnras/stw301)

(ref: mccabe2003) McCabe, C., Duchêne, G., & Ghez, A. M. 2003, ApJL, 588, L113, doi: [`10.1086/375632`](http://doi.org/10.1086/375632)

(ref: mccabe2011) McCabe, C., Duchêne, G., Pinte, C., et al. 2011, ApJ, 727, 90, doi: [`10.1088/0004-637X/727/2/90`](http://doi.org/10.1088/0004-637X/727/2/90)

(ref: mcclure2009) McClure, M. 2009, ApJL, 693, L81, doi: [`10.1088/0004-637X/693/2/L81`](http://doi.org/10.1088/0004-637X/693/2/L81)

(ref: meeus2001) Meeus, G., Waters, L. B. F. M., Bouwman, J., et al. 2001, A&A, 365, 476, doi: [`10.1051/0004-6361:20000144`](http://doi.org/10.1051/0004-6361:20000144)

(ref: min2012) Min, M., Canovas, H., Mulders, G. D., & Keller, C. U. 2012, A&A, 537, A75, doi: [`10.1051/0004-6361/201117333`](http://doi.org/10.1051/0004-6361/201117333)

(ref: min2016) Min, M., Rab, C., Woitke, P., Dominik, C., & Ménard, F. 2016, A&A, 585, A13, doi: [`10.1051/0004-6361/201526048`](http://doi.org/10.1051/0004-6361/201526048)

(ref: nomura2005) Nomura, H., & Millar, T. J. 2005, A&A, 438, 923, doi: [`10.1051/0004-6361:20052809`](http://doi.org/10.1051/0004-6361:20052809)

(ref: owen2011) Owen, J. E., Ercolano, B., & Clarke, C. J. 2011, MNRAS, 411, 1104, doi: [`10.1111/j.1365-2966.2010.17750.x`](http://doi.org/10.1111/j.1365-2966.2010.17750.x)

(ref: pascucci2020) Pascucci, I., Banzatti, A., Gorti, U., et al. 2020, ApJ, 903, 78, doi: [`10.3847/1538-4357/abba3c`](http://doi.org/10.3847/1538-4357/abba3c)

(ref: perrin2006) Perrin, M. D., Duchêne, G., Kalas, P., & Graham, J. R. 2006, ApJ, 645, 1272, doi: [`10.1086/504510`](http://doi.org/10.1086/504510)

(ref: pinte2016) Pinte, C., Dent, W. R. F., Ménard, F., et al. 2016, ApJ, 816, 25, doi: [`10.3847/0004-637X/816/1/25`](http://doi.org/10.3847/0004-637X/816/1/25)

(ref: pinte2009) Pinte, C., Harries, T. J., Min, M., et al. 2009, A&A, 498, 967, doi: [`10.1051/0004-6361/200811555`](http://doi.org/10.1051/0004-6361/200811555)

(ref: pinte2006) Pinte, C., Ménard, F., Duchêne, G., & Bastien, P. 2006, A&A, 459, 797, doi: [`10.1051/0004-6361:20053275`](http://doi.org/10.1051/0004-6361:20053275)

(ref: pontoppidan2007) Pontoppidan, K. M., Stapelfeldt, K. R., Blake, G. A., van Dishoeck, E. F., & Dullemond, C. P. 2007, ApJL, 658, L111, doi: [`10.1086/514817`](http://doi.org/10.1086/514817)

(ref: ray2007) Ray, T., Dougados, C., Bacciotti, F., Eislöffel, J., & Chrysostomou, A. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 231, doi: [`10.48550/arXiv.astro-ph/0605597`](http://doi.org/10.48550/arXiv.astro-ph/0605597)

(ref: rebull2010) Rebull, L. M., Padgett, D. L., McCabe, C. E., et al. 2010, ApJS, 186, 259, doi: [`10.1088/0067-0049/186/2/259`](http://doi.org/10.1088/0067-0049/186/2/259)

(ref: rigliaco2015) Rigliaco, E., Pascucci, I., Duchene, G., et al. 2015, ApJ, 801, 31, doi: [`10.1088/0004-637X/801/1/31`](http://doi.org/10.1088/0004-637X/801/1/31)

(ref: riols2018) Riols, A., & Lesur, G. 2018, A&A, 617, A117, doi: [`10.1051/0004-6361/201833212`](http://doi.org/10.1051/0004-6361/201833212)

(ref: rodenkirch2022) Rodenkirch, P. J., & Dullemond, C. P. 2022, A&A, 659, A42, doi: [`10.1051/0004-6361/202142571`](http://doi.org/10.1051/0004-6361/202142571)

(ref: shakura1973) Shakura, N. I., & Sunyaev, R. A. 1973, A&A, 24, 337

(ref: siebenmorgen2012) Siebenmorgen, R., & Heymann, F. 2012, A&A, 543, A25, doi: [`10.1051/0004-6361/201219039`](http://doi.org/10.1051/0004-6361/201219039)

(ref: Simon2019) Simon, M., Guilloteau, S., Beck, T. L., et al. 2019, ApJ, 884, 42, doi: [`10.3847/1538-4357/ab3e3b`](http://doi.org/10.3847/1538-4357/ab3e3b)

(ref: stapelfeldt2014) Stapelfeldt, K. R., Duchêne, G., Perrin, M., et al. 2014, in Exploring the Formation and Evolution of Planetary Systems, ed. M. Booth, B. C. Matthews, & J. R. Graham, Vol. 299, 99–103, doi: [`10.1017/S1743921313008004`](http://doi.org/10.1017/S1743921313008004)

(ref: sturm2023a) Sturm, J. A., McClure, M. K., Law, C. J., et al. 2023a, arXiv e-prints, arXiv:2305.02338, doi: [`10.48550/arXiv.2305.02338`](http://doi.org/10.48550/arXiv.2305.02338)

(ref: sturm2023b) Sturm, J. A., McClure, M. K., Bergner, J. B., et al. 2023b, arXiv e-prints, arXiv:2305.02355, doi: [`10.48550/arXiv.2305.02355`](http://doi.org/10.48550/arXiv.2305.02355)

(ref: tazaki2021b) Tazaki, R., Murakawa, K., Muto, T., Honda, M., & Inoue, A. K. 2021a, ApJ, 921, 173, doi: [`10.3847/1538-4357/ac1f8c`](http://doi.org/10.3847/1538-4357/ac1f8c)

(ref: tazaki2021) —. 2021b, ApJ, 910, 26, doi: [`10.3847/1538-4357/abdd3d`](http://doi.org/10.3847/1538-4357/abdd3d)

(ref: tazaki2019) Tazaki, R., Tanaka, H., Muto, T., Kataoka, A., & Okuzumi, S. 2019, MNRAS, 485, 4951, doi: [`10.1093/mnras/stz662`](http://doi.org/10.1093/mnras/stz662)

(ref: tazaki2016) Tazaki, R., Tanaka, H., Okuzumi, S., Kataoka, A., & Nomura, H. 2016, ApJ, 823, 70, doi: [`10.3847/0004-637X/823/2/70`](http://doi.org/10.3847/0004-637X/823/2/70)

(ref: teague2020) Teague, R., Jankovic, M. R., Haworth, T. J., Qi, C., & Ilee, J. D. 2020, MNRAS, 495, 451, doi: [`10.1093/mnras/staa1167`](http://doi.org/10.1093/mnras/staa1167)

(ref: tobin2010) Tobin, J. J., Hartmann, L., & Loinard, L. 2010, ApJL, 722, L12, doi: [`10.1088/2041-8205/722/1/L12`](http://doi.org/10.1088/2041-8205/722/1/L12)

(ref: tobon2022) Tobon Valencia, V., Geffrin, J.-M., Ménard, F., et al. 2022, A&A, 666, A68, doi: [`10.1051/0004-6361/202142656`](http://doi.org/10.1051/0004-6361/202142656)

(ref: villenave2020) Villenave, M., Ménard, F., Dent, W. R. F., et al. 2020, A&A, 642, A164, doi: [`10.1051/0004-6361/202038087`](http://doi.org/10.1051/0004-6361/202038087)

(ref: villenave2022) Villenave, M., Stapelfeldt, K. R., Duchêne, G., et al. 2022, ApJ, 930, 11, doi: [`10.3847/1538-4357/ac5fae`](http://doi.org/10.3847/1538-4357/ac5fae)

(ref: watson2004) Watson, A. M., & Stapelfeldt, K. R. 2004, ApJ, 602, 860, doi: [`10.1086/381142`](http://doi.org/10.1086/381142)

(ref: watson2007) Watson, A. M., Stapelfeldt, K. R., Wood, K., & Ménard, F. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 523, doi: [`10.48550/arXiv.0707.2608`](http://doi.org/10.48550/arXiv.0707.2608)

(ref: weingartner2001) Weingartner, J. C., & Draine, B. T. 2001, ApJ, 548, 296, doi: [`10.1086/318651`](http://doi.org/10.1086/318651)

(ref: whelan2014) Whelan, E. T., Bonito, R., Antoniucci, S., et al. 2014, A&A, 565, A80, doi: [`10.1051/0004-6361/201322037`](http://doi.org/10.1051/0004-6361/201322037)

(ref: williams2011) Williams, J. P., & Cieza, L. A. 2011, ARA&A, 49, 67, doi: [`10.1146/annurev-astro-081710-102548`](http://doi.org/10.1146/annurev-astro-081710-102548)

(ref: woitke2016) Woitke, P., Min, M., Pinte, C., et al. 2016, A&A, 586, A103, doi: [`10.1051/0004-6361/201526538`](http://doi.org/10.1051/0004-6361/201526538)

(ref: wolff2021) Wolff, S. G., Duchêne, G., Stapelfeldt, K. R., et al. 2021, AJ, 161, 238, doi: [`10.3847/1538-3881/abeb1d`](http://doi.org/10.3847/1538-3881/abeb1d)

[^1]: `https://galex.stsci.edu/GR6/?page=mastform`

</paper>

Write the methods card for this paper.