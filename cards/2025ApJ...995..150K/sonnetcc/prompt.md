# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...995..150K\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...995..150K",
 "title": "Comprehensive JWST+ALMA Study on the Extended Lyα Emitters, Himiko, and CR7 at z ∼ 7: Blue Major Merger Systems in Stark Contrast to Submillimeter Galaxies",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Kiyota, Tomokazu",
 "n_authors": 17,
 "arxiv_id": "2504.03156",
 "doi": "10.3847/1538-4357/ae1cc3",
 "alma_projects_linked_by_archive": [
  "2011.0.00115.S",
  "2012.1.00033.S",
  "2015.1.00122.S"
 ]
}
```

Paper text:
<paper>
#  Comprehensive JWST+ALMA Study on the Extended Ly$\alpha$ Emitters, Himiko and CR7 at $z\sim 7$:\
Blue Major Merger Systems in Stark Contrast to Submillimeter Galaxies

## Abstract

We present various properties of two bright extended Ly$\alpha$ objects, Himiko and CR7, at $z=6.6$ thoroughly investigated with JWST/NIRCam photometry, NIRSpec-IFU spectroscopy, and ALMA data, uncovering their physical origins. Himiko (CR7) shows at least five (four) clumps with small separations of 2.4–7.3 kpc and velocity offsets of $\Delta v<220~\mathrm{km~s^{-1}}$ in the \[O iii\]$\lambda\lambda4959,5007$ line maps, three of which exhibit stellar components with comparable stellar masses ranging in $\log{(M_*/M_\odot)}=8.4$–$9.0$ ($8.3$–$8.8$), indicative of major merger systems that are consistent with our numerical simulations. The \[C ii\]158$\mu$m and Ly$\alpha$ lines are found in the middle of two clumps (the brightest clump) in Himiko (CR7), suggesting that the distribution of neutral gas does not always coincide with that of ionized gas or stars in merging processes. We find that some of the clumps have broad \[O iii\] components (250–400$~\mathrm{km~s^{-1}}$) in Himiko and CR7, likely tracing outflow and tidal features, while the central clump in Himiko presents a broad H$\alpha$ ($\sim1000~\mathrm{km~s^{-1}}$) line explained by an AGN with a low mass black hole of $M_\mathrm{BH}=10^{6.6}~M_\odot$, which contribute to the extended and bright nature of Himiko and CR7. We find low metallicities of $12+\log(\mathrm{O/H})=$7.9–8.1 in Himiko and CR7 based on auroral \[O iii\]$\lambda4363$ and strong lines that are consistent with no 1-mm continuum detection corresponding to the dust mass limits of $M_\mathrm{dust}\lesssim 9\times 10^6 M_\odot$. Himiko and CR7 are metal- and dust-poor blue merger systems with stellar and dust masses $\gtrsim2$ orders of magnitude smaller than the massive dust-rich merger systems represented by submillimeter galaxies.

# Introduction

Recent advancements in observing the high-redshift Universe have enabled us to explore the detailed physical properties of early galaxies. Over the past several decades, ground-based telescopes, such as Subaru and Keck, and space telescopes, like the Hubble Space Telescope (HST), have observed thousands of galaxies in the epoch of reionization ($z>6$). These observations have provided deep photometric data spanning the rest-frame ultraviolet (UV) to near-infrared (NIR) wavelengths and UV spectroscopic data, which are crucial for understanding the physical conditions of these early systems (e.g., (cite: bouwens15; finkelstein15)).

Wide-field ground-based surveys conducted with Subaru have successfully identified bright targets, resulting in large galaxy samples, including Ly$\alpha$ emitters (LAEs), even at $z>6$. Subaru narrow-band (NB) surveys effectively select LAEs at $z=2$–$7$ by detecting NB excess in combination with broadband imaging (e.g., (cite: ouchi10; matthee15; ouchi18; kikuta23)). These surveys have been critical in identifying large populations of high-redshift galaxies and have enabled the discovery of unique and rare objects. Notably, such surveys have led to the identification of high-redshift Ly$\alpha$ blobs (e.g., (cite: shibuya18); see also e.g., (cite: steidel00; matsuda04; prescott12; cantalupo14) for Ly$\alpha$ blobs or Ly$\alpha$ nebulas at $z=2$–$3$ studies) and protoclusters (e.g., (cite: toshikawa18; harikane19a)). The discovery of these sources provides insight into the processes that govern galaxy formation and evolution.

The remarkable findings of these surveys are large Ly$\alpha$ blobs at $z=6.6$, known as ‘Himiko’ (e.g., (cite: ouchi09; walter12; ouchi13; hirashita14; ota14; zabl15; carniani18)) and ‘CR7’ (COSMOS Redshift 7; (cite: matthee15; sobral15; bowler17b; matthee17; sobral19; matthee20; marconcini24b)). Himiko and CR7 were identified as the most luminous Ly$\alpha$ emitter candidates at $z\sim6.6$ in the UKIDSS/UDS and COSMOS/UltraVISTA field, respectively, using the Subaru/Suprime-Cam NB921 filter (cite: ouchi09; matthee15). They are confirmed spectroscopically with Keck and the Very Large Telescope (VLT) aimed at the Ly$\alpha$ emission. Both are significantly bright in the rest-frame UV continuum ($m_\mathrm{AB}\sim25$ or $M_{\mathrm{UV}}\sim-22$) and Ly$\alpha$ emission with their Ly$\alpha$ luminosity of $3.9\times10^{43}~\mathrm{erg~s^{-1}}$ and $8.9\times10^{43}~\mathrm{erg~s^{-1}}$, and their Ly$\alpha$ emissions are spatially extended over 17 kpc and 16 kpc for Himiko and CR7, respectively (cite: ouchi09; sobral15). The HST/Wide Field Camera 3 (WFC3) imaging revealed their clumpy UV counterparts, which are composed of at least three components within 10 kpc$\times$10 kpc, indicating potentially merging systems. The follow-up observations with the Atacama Large Millimeter/submillimeter Array (ALMA) Band 6 detected \[C ii\]$158\ensuremath{\mu}m$ emissions but no dust continuum (cite: matthee17; carniani18).

In addition, NIR photometry with Spitzer/IRAC revealed a $3.6\ensuremath{\mu}m$ excess, suggesting the presence of strong H$\beta$+\[O iii\] lines, although the spatial resolution is lower than that of UV photometry (cite: ouchi13; matthee15; bowler17a). However, these datasets alone suffer from dust-age-metallicity degeneracies and potential misinterpretation of the stellar populations due to contributions from nebular emissions. The limited data make it difficult to clarify the physical origins of their extended Ly$\alpha$ emission and their bright nature in the rest-frame UV, leaving the topic still under debate (e.g., the discussion on LAEs at $z=2$–$3$; (cite: sobral18b)).

The advent of the James Webb Space Telescope (JWST; (cite: gardner23)) has changed our ability to study early galaxies with remarkable sensitivity and resolution. JWST/Near Infrared Spectrograph (NIRSpec; (cite: jakobsen22)) is the first instrument to observe the rest-frame optical spectrum of Himiko and CR7, providing their detailed physical properties, such as metallicity, ionization conditions, and dynamics. Furthermore, JWST has an Integral Field Unit (IFU; (cite: boker22)), allowing for high-resolution, three-dimensional spectroscopic observations. IFU observations enable us to investigate the morphology and kinematics of clumpy or merging galaxies like Himiko and CR7 in detail, offering a comprehensive view of their internal structure, dynamics, and interactions (e.g., (cite: perna23; arribas24; ishikawa24; jones24a; jones24b; lamperti24; marconcini24b; marconcini24a; marshall24; scholtz24; morishita25; parlanti25)) .

This paper comprehensively analyzes Himiko and CR7 using publicly available data from the JWST Near Infrared Camera (NIRCam; (cite: rieke23)) and the NIRSpec IFU. We also include archival ALMA Band 6 data to examine their cold gas and dust characteristics. We integrate these data sets to explore their dynamics, stellar populations, ionization conditions, and dust content.

The structure of this paper is as follows. Section [2](#sec:data) outlines the data processing of the JWST, ALMA, and Subaru. Section [3](#sec:analysis) details the analysis procedures, including flux measurements and spectral energy distribution (SED) fitting. Section [4](#sec:results) presents the results and the derived physical properties. In Section [5](#sec:discussion), we interpret the results and discuss their implications for the extended Ly$\alpha$ emission, UV bright nature, and galaxy mergers. Finally, Section [6](#sec:conclusions) summarizes our study. Throughout the paper, we use the Chabrier initial mass function ((cite: chabrier03)), and a flat $\Lambda$CDM cosmology with $H_0 = 67.7~\mathrm{km~s^{-1}~Mpc^{-1}}$, $\Omega_m = 0.3111$ and $\Omega_\Lambda=0.6889$ (cite: planck20). All magnitudes are in the AB system (cite: oke83).

# Data and reduction

## JWST/NIRSpec

We use the JWST/NIRSpec IFU data of Himiko and CR7 that were taken by the Guaranteed Time Observations (GTO) programs #GTO-1215 and #GTO-1217 (PI: Nora Luetzgendorf) as part of the Galaxy Assembly with NIRSpec Integral Field Spectroscopy (GA-NIFS; (cite: perna23IAU)) in 2022 December and 2023 May, respectively. Both programs were carried out with two sets of dispersers/filters: PRISM/CLEAR and G395H/F290LP. The spectral resolutions were $R\sim100$ and $R\sim2700$, covering 0.60–5.30 $\ensuremath{\mu}m$ and 2.87–5.27 $\ensuremath{\mu}m$, respectively. The observations were conducted with a medium cycling pattern and eight dithers. The exposure times were 3968 and 18207 seconds, respectively.

We reduce the NIRSpec IFU data obtained from the Mikulski Archive for Space Telescopes (MAST) portal[^1]. We use the JWST Science Calibration pipeline (version 1.14.0; (cite: bushouse_2024_10870758)), and the calibration reference data system (CRDS) contexts are `jwst_1227.pmap` and `jwst_1263.pmap` for Himiko and CR7, respectively. We mainly follow the reduction procedure presented by the team of the Targeting Extremely Magnified Panchromatic Lensed Arcs and Their Extended Star formation (TEMPLATES) that is the JWST Early Release Science (ERS) program (#ERS-1355, PI: Jane R. Rigby; (cite: rigby23)). The reduction procedure is coded in the script that is now publicly available (version 1.0.2; (cite: jane_rigby_2024_10933642))[^2]. Here, we briefly summarize the reduction procedures detailed in (cite: rigby23). First, we conduct `calwebb_detector1` as stage 1, including detector-level corrections for each exposure. We then correct $1/f$ noise of the data using `NSClean` ((cite: rauscher24)). We perform `calwebb_spec2` to the stage 1 individual exposure as a stage 2, including WCS/wavelength corrections, flat-fielding, path-loss correction, and flux calibration. We perform drizzle weighting that accomplishes the spaxel scale of $0.06\ensuremath{''}$. Finally, instead of stage 3, we use `reproject` (version 0.13.1; (cite: robitaille_2024_10931886)) and `reproject_interp` packages for the stage 2 data to obtain the median stack final 3D data cube, reducing outliers. We estimate a median value for each wavelength channel with masks around the object to subtract the background. We approximate the background as a function of wavelength and subtract them from each wavelength channel to obtain the final background-subtracted 3D data cube.

Previous studies have reported astrometric offsets ($\sim0.2\ensuremath{''}$) between IFU data and NIRCam or HST images (e.g., (cite: fujimoto24; jones24a; jones24b; jones24c; zamora24)). Similarly, we identify astrometric offsets between NIRCam and NIRSpec IFU data. These offsets are corrected by aligning the \[O iii\]$\lambda$5007 (H$\alpha$) emission line peak observed with the IFU to the NIRCam F356W (F444W) image of Himiko (CR7), where the \[O iii\]$\lambda$5007 (H$\alpha$) falls in the filter response.

## JWST/NIRCam

We utilize JWST/NIRCam images to extract the photometric properties of Himiko and CR7. The images of Himiko were obtained through Public Release IMaging for Extragalactic Research (PRIMER) as part of the General Observers (GO) program (#GO-1837, PI: James S. Dunlop). The observations were conducted using eight filters: F090W, F115W, F150W, F200W, F277W, F356W, F410M, and F444W. We utilize the images reduced with `grizli` ((cite: brammer23)), available on the Dawn JWST Archive website[^3] (version 7.0 of the UDS field; see (cite: valentino23) for details of the reduction).

The images of CR7 were obtained as part of the COSMOS-Web survey (#GO-1727, PI: Jeyhan Kartaltepe and Caitlin M. Casey; for an overview, see (cite: casey23)) using four filters: F115W, F150W, F277W, and F444W. We employ the COSMOS-Web data presented in the COSMOS-Web Data Release (DR) 0.5[^4], which include the NIRCam data from epochs 1 and 2 taken in 2023 January and April, respectively. We choose images with a pixel size of $0.03\ensuremath{''}$/pixel provided by the COSMOS-Web DR0.5.

## ALMA

We observed Himiko with ALMA Band 6 to characterize \[C ii\]158$\ensuremath{\mu}m$ emission line (250.24 GHz at $z_\mathrm{Ly\alpha}=6.595$) and dust continuum. The observation was carried out on 2015 July 22, 23, and 24 as a Cycle 1 program (#2012.1.00033.S, PI: M. Ouchi). The extended array configuration with 44 12-m antennas was used, and the baseline ranges from 15 to 1600 m. The observation was conducted in frequency division mode with four spectral windows centered at 250.262 GHz, 252.138 GHz, 265.638 GHz, and 267.513 GHz. A total bandwidth was 7.5 GHz and a spectral resolution would be 0.976 kHz, corresponding to $\sim1.2~\mathrm{km~s^{-1}}$. The on-source integration time was 3.2 hours. Ceres and J0238+166 were observed as flux calibrators. Bandpass calibration was performed with J2357-5311, J0334-4008, and J0423-0120. J0208-0047 was used for gain calibration or complex gain calibration.

Himiko was also observed with the same band in 2012 July as a Cycle 0 program (#2011.0.00115.S, PI: M. Ouchi; (cite: ouchi13)). These Cycles 0 and 1 data have previously been used in (cite: carniani18), which reported the detection of \[C ii\] emission from Himiko. CR7 was observed with the Band 6 in 2016 May and November (Cycle 3, ID: #2015.1.00122.S, PI: D. Sobral; (cite: matthee17)).

We retrieve these data from the ALMA Science Archive[^5]. We calibrate the Cycles 0, 1, and 3 data using the Common Astronomy Software Applications package (CASA; (cite: casa22)) version 3.4, 4.3.1, and 4.7.0, respectively, using the calibration script or pipeline script in the archive. We image from the calibrated visibility using CASA version 6.6.4. For Himiko data, we combine the Cycles 0 and 1 data using the CASA task `CONCAT` to obtain high-sensitivity data with a total on-source time of 6.4 hours. Using the CASA task `TCLEAN`, we generate both continuum images and \[C ii\]$158\ensuremath{\mu}m$ line cubes with a natural weighting, a pixel scale of $0.1\ensuremath{''}$, and a spectral channel bin of $50~\mathrm{km~s^{-1}}$. Continuum maps are created by excluding spectral windows containing \[C ii\]$158\ensuremath{\mu}m$ emission. The resulting continuum map sensitivities for Himiko and CR7 are $\sigma_\mathrm{cont} = 10.5~\mu\mathrm{Jy~beam^{-1}}$ and $6.4~\mu\mathrm{Jy~beam^{-1}}$, respectively, which is consistent with previous studies (cite: carniani18; matthee17). The beam sizes of the continuum maps for Himiko and CR7 are $0.38\ensuremath{''} \times 0.30\ensuremath{''}$ with a position angle of 66$.\!\!{ \degree }$9 and $0.46\ensuremath{''} \times 0.41\ensuremath{''}$ with a position angle of $38\mbox{$.\!\!{\degree}$}4$, respectively. We also produce a uv-tapered \[C ii\]$158\ensuremath{\mu}m$ line cube with a Gaussian width of $0.7\ensuremath{''}$ to optimize the signal-to-noise ratio (S/N). The uv-tapered \[C ii\]$158\ensuremath{\mu}m$ line cube achieves a synthesized beam full width at half maximum (FWHM) of $0.94\ensuremath{''} \times 0.81\ensuremath{''}$ with a position angle of 81$.\!\!{ \degree }$7 ($0.90\ensuremath{''} \times 0.87\ensuremath{''}$ with a position angle of $-52\mbox{$.\!\!{\degree}$}0$) for Himiko (CR7). We use the uv-tapered line cube to measure the spatial distributions and fluxes of \[C ii\]$158\ensuremath{\mu}m$ of Himiko and CR7. Throughout this paper, we only show statistical errors. The absolute flux uncertainty of Band 6 is $\sim10\%$ (ALMA Cycle 1 Properser’s Guide[^6]).

## Subaru

We obtain ultra-deep images from the Hyper Suprime-Cam (HSC) Subaru Strategic Program (SSP; (cite: aihara18a; aihara18b; aihara19; aihara22)) public data release 3 (PDR3; (cite: aihara22)). Especially, we utilize the narrowband (NB) images taken by the NB921 filter ($\lambda_{\rm c}=9215$Å) that covers the redshifted Ly$\alpha$ emission at $z=6.6$. We study the extended Ly$\alpha$ emission of Himiko and CR7 with these images. The point spread function (PSF) FWHM is typically $\sim0.75\ensuremath{''}$ for the NB921 filter.

# Analysis

## NIRCam Photometry

To extract the NIRCam photometry of these objects, we conduct PSF matching. The reference images are F444W, with the largest PSF ($\mathrm{FWHM}\sim0.16\ensuremath{''}$) among the NIRCam filters. We measure the size of the PSF for each filter and match the PSF using a Gaussian kernel convolution. When we extract the photometry, we use SEP (version 1.2.1, (cite: barbary16)), the Python version of the SOURCE EXTRACTOR (SExtractor; (cite: bertin96)). We extract the photometry of each clump in a circular aperture with a $0.4\ensuremath{''}$-diameter, except for CR7-A (Figure [1](#fig:NIRCam-cutout), see Section [4](#sec:results)), for which a $0.5\ensuremath{''}$-diameter is used. This is because CR7-A is more extended than other clumps. We do not apply aperture correction because these objects have complex morphology. We estimate errors with 1000 circular apertures of the same size on a blank field using the Photutils package (version 2.0.2, (cite: larry_bradley_2024_13989456)). No uncertainty floor (e.g., 5%–10%) is applyed to the photometric errors.

## SED Modeling

We perform a spectral energy distribution (SED) fitting with Prospector (version 1.2.0, (cite: leja17; johnson21)), utilizing NIRCam photometry to characterize the stellar population of these objects. We do not include the ALMA photometry because the ALMA data have a lower resolution ($\sim0.90\ensuremath{''}$) than the NIRCam photometry ($\sim0.16\ensuremath{''}$), and we only have the upper limit of the dust continuum. We note that F090W photometry is not used for the SED fitting because Ly$\alpha$ emission and intergalactic medium (IGM) absorption can contaminate the photometry. We employ a stellar population synthesis package called Flexible Stellar Population Synthesis (FSPS; (cite: conroy09; conroy10)). Nebula emission is modeled using the Cloudy photo-ionization framework ((cite: byler17)) and is implemented in the FSPS. We apply the (cite: chabrier03) initial mass function, the Calzetti dust attenuation law ((cite: calzetti00)), and the (cite: madau95) model of intergalactic medium attenuation. We assume a nonparametric star formation history (SFH) as described by (cite: harikane25). We do not include AGN models in the SED fitting because our photometry is limited to the rest-frame UV through the optical wavelength. We allow varying total stellar mass ($M_*$) and optical depth in the $V$ band ($\tau_V$) to be in the range of $6<\log{(M_*/M_\odot)}<11$ and $0<\tau_V<2$ with top-hat priors and log-uniform priors, respectively. We set the metallicity to $Z=0.2Z_\odot$, which is indicated from the NIRSpec IFU data (see Section [4.3](#subsec:emission-line)). We use the redshifts measured from the NIRSpec IFU data. We apply the Markov Chain Monte Carlo method using the `emcee` ((cite: Foreman-Mackey13)) to estimate the best-fit parameters and their uncertainties.

## Emission-line fitting and flux measurements

### JWST NIRSpec

We perform least-square Gaussian fitting of emission lines to measure spatially integrated emission line fluxes using the `scipy.optimize` package (cite: virtanen20). We conduct the fitting with up to three Gaussian components for the high-resolution G395H data ($R\sim2700$) that show complex emission line profiles. We constrain the Gaussian width to be larger than the instrumental dispersion, adopting $R=2700$ for G395H and $R=100$ for PRISM. The optimal number of components is determined using the Akaike Information Criterion (AIC; (cite: akaike74)), with a threshold of $\Delta\mathrm{AIC}\equiv\mathrm{AIC}_{i \mathrm{\,components}} - \mathrm{AIC}_{(i+1)\mathrm{\,components}}>20$, where $\mathrm{AIC}_{i \mathrm{~components}}$ is the AIC value in the case of $i$ Gaussian components. A single Gaussian component is used to fit the PRISM spectra with lower spectral resolution. We fix the flux ratio of $f_\mathrm{[O\,III]\lambda5007}/f_\mathrm{[O\,III]\lambda4959}=2.98$ (cite: storey00) to reduce the fitting parameters. When calculating emission line ratios, we use flux values obtained from the G395H spectra except for metallicity measurements and some line ratios involving \[O ii\]$\lambda$3727. The error spectrum is scaled to the background noise level. Flux errors are calculated by summing the errors of the spectral bins in quadrature over a wavelength range of $2\times\mathrm{FWHM}$, centered on the Gaussian peak. All rest-frame wavelengths are adopted on the vacuum wavelength scale (e.g., 5008.240Å for \[O iii\]$\lambda5007$), while we follow the conventional emission line names based on their wavelengths in the air.

To evaluate the morphology and kinematics of the objects, we create moment maps using G395H data cubes. The emission lines in each spatial pixel (spaxel) have distorted shapes, which implies complex structures and kinematics. Therefore, we calculate the moment 0, 1, and 2 maps (flux, velocity, and velocity dispersion) using a flux-weighted average (e.g., (cite: walter08)) instead of the Gaussian profile fitting. When we consider the flux ratio maps, we conduct a single Gaussian fitting for each spaxel individually. The velocity dispersion is corrected for instrumental broadening assuming $\sigma_\mathrm{int} = \sqrt{\sigma_\mathrm{obs}^2 - \sigma_\mathrm{inst}^2}$, where $\sigma_\mathrm{int}$, $\sigma_\mathrm{obs}$, and $\sigma_\mathrm{inst}$ are intrinsic, observed, and instrumental dispersions, respectively. We assume $R=2700$ to obtain $\sigma_\mathrm{inst}$ for the G395H data.

### ALMA

We create moment 0 maps around the \[C ii\]158$\ensuremath{\mu}m$ emission line and sum up data from regions of $>3\sigma$ to obtain the total spectrum of Himiko and CR7. \[C ii\] flux measurements are conducted by summing up the spectral bins because the line shapes deviate from a Gaussian profile. However, these flux values are largely consistent with the results obtained by least-squares fitting of a Gaussian. We measure the noise by placing 1000 random circular apertures around the objects, the spatial sizes of which are the same as those used for flux measurements of Himiko and CR7. The flux errors are calculated using the same method as in the NIRSpec IFU analysis. We convert the \[C ii\] fluxes to \[C ii\] luminosities following the relation: $$\begin{equation}
    L_\mathrm{[CII]} = 1.04 \times 10^{-3} \times \left( \frac{S_\mathrm{[CII]} \Delta v}{\mathrm{Jy~km~s^{-1}}} \right) \left(\frac{D_\mathrm{L}}{\mathrm{Mpc}} \right)^2 \left(\frac{\nu_\mathrm{obs}}{\mathrm{GHz}} \right) L_\odot, 
\end{equation}$$ where $S_\mathrm{[CII]} \Delta v$ is the line flux in Jy km s$^{-1}$, $D_\mathrm{L}$ is the luminosity distance in Mpc ($D_\mathrm{L}=65862.5~\mathrm{Mpc}$ at $z=6.60$), and $\nu_\mathrm{obs}$ is the observed frequency in GHz (e.g., (cite: solomon05; carilli13)).

The dust continuum at a rest-frame wavelength of $\lambda=158~\ensuremath{\mu}m$ is undetected for Himiko and CR7. We only put the $3\sigma$ upper limit for the dust continuum estimated from the noise of the continuum maps.

# Results

## Morphology and Dynamics

Figure [1](#fig:NIRCam-cutout) shows $5\ensuremath{''} \times 5\ensuremath{''}$ NIRCam cutout images of Himiko (top) and CR7 (bottom). We identify at least three clumps within $\sim2\ensuremath{''}$ diameter ($\sim11.1$ kpc at $z=6.6$) aperture for each object in the rest-frame UV to optical images. Throughout the paper, we label these clumps as Himiko-A, Himiko-B, Himiko-C, and CR7-A, CR7-B, CR7-C as indicated in Figure [1](#fig:NIRCam-cutout), which are the same terminologies as in previous studies (e.g., (cite: ouchi13; sobral15)). We note that the F356W image is significantly affected by strong emission lines, including H$\beta$ and \[O iii\]$\lambda\lambda4959,5007$, which can enhance brightness. The F090W image of Himiko includes the Ly$\alpha$ emission but does not reveal a clear signature of the extended Ly$\alpha$. This absence likely attributes to the shallower surface brightness sensitivity of JWST (6.5 m mirror) compared to that of Subaru (8 m mirror) or the difference in the filter response.

In Figure [2](#fig:ifu_oiii), we show the NIRSpec IFU G395H data cube collapsing around the \[O iii\]$\lambda5007$ line, with the highest S/N among the detected emission lines. The spatially integrated spectrum of \[O iii\]$\lambda\lambda4959, 5007$ for each region is also presented in Figure [2](#fig:ifu_oiii). The apertures are shown as white circles ($0.3\ensuremath{''}$-diameter for Himiko-A, -B, -C; $0.2\ensuremath{''}$-diameter for Himiko-D, -E; $0.5\ensuremath{''}$-diameter for CR7-A; $0.4\ensuremath{''}$-diameter for CR7-B, -C, -D). We extract the spectrum using the Photutils package, and we do not perform aperture corrections because Himiko and CR7 have complex morphology. Using the \[O iii\] doublet, for Himiko, we find additional clumps named Himiko-D and Himiko-E with separations of 0.43$''$ and 1.2$''$ ($=2.4~\mathrm{kpc}$ and $6.6~\mathrm{kpc}$) from Himiko-B, respectively. We measure the redshift by performing a single Gaussian fitting for the \[O iii\]$\lambda5007$ G395H spectrum. The Redshifts of Himiko-D, -E are $z=6.5902$ and $z=6.5905$, respectively, which are almost the same as those of other clumps ($z=6.5920, 6.5875, 6.5898$ for Himiko-A, -B, and -C). For CR7, the redshifts of CR7-A, -B, and -C are $z=6.6022$, $z=6.5994$, and $z=6.5977$. There is an additional clump named CR7-D (1.3$''$ separation from CR7-A), and the redshift is $z=6.6011$. These results show that Himiko and CR7 are complex systems with at least five and four clumps, respectively. We further discuss the origin of the multiple clumps in Section [5.1](#subsec:multiple-clumps).

We also note that in the NIRCam images of CR7 (Figure [1](#fig:NIRCam-cutout)), there is an object in the north with a separation of $1.5\ensuremath{''}$ ($0.5\ensuremath{''}$) from CR7-A (CR7-B). In the F277W image of Figure [1](#fig:NIRCam-cutout), this object is indicated by the gray arrow. The object is also observed in the HST/WFC3 $YJ$ band image in Figure 6 of (cite: sobral15). To check whether the object is associated with CR7, we investigate the NIRSpec IFU PRISM and G395H data at the same location as the NIRCam images. The object is detected with a continuum in the PRISM spectrum and an emission line at $\sim2.94~\ensuremath{\mu}m$ in the G395H spectrum, which corresponds to the \[Ne iii\]$\lambda$3869 at $z=6.6$. However, other emission lines are not detected in the spectrum, which might indicate that the object is merely a chance projection. In addition, COSMOS-Web DR1 (cite: casey23; shuntov25) conducts SED fitting for the object and reports that it has a photometric redshift of $z_\mathrm{phot}=1.8\pm 0.7$. Further spectroscopic observations are necessary to determine its redshift. We assume that the object is a chance projection and do not discuss it in the latter sections of this paper.

Figure [3](#fig:jwst-alma-subaru-image) compares the spatial distribution of each emission from Himiko (left) and CR7 (right). The background gray images are the rest-frame UV emission (NIRCam F115W). The green contours show the H$\alpha$ emission taken with the NIRSpec IFU, obtained by collapsing around the H$\alpha$ wavelength. The red contours show the \[C ii\] emission obtained with ALMA Band 6, and the red cross shows the uncertainty of the ALMA positional accuracy[^7]. The blue contours show the Ly$\alpha$ distributions estimated by subtracting the F115W images (UV continuum) from the NB921 images (Ly$\alpha$ and UV continuum). The PSFs of F115W images are matched to those of NB921 images by conducting Gaussian kernel convolutions. The spatial distribution of the UV continuum and H$\alpha$ emission in Himiko and CR7 aligns well. This indicates that H$\alpha$ emission mainly comes from the star-forming regions. In addition, the spatial position of the \[C ii\] and Ly$\alpha$ peaks agree within the positional uncertainty, consistent with (cite: carniani18) and (cite: matthee17). Ly$\alpha$ emission of CR7 mostly aligns well with the CR7-A indicated by UV continuum and H$\alpha$ emission. (cite: matthee20) have observed CR7 with VLT/MUSE and reported the $\sim1~\mathrm{kpc}$ spatial offset between Ly$\alpha$ and UV peak of CR7-A. We cannot detect such an offset of Ly$\alpha$, which might be due to the low angular resolution of Subaru NB921 data ($0.75\ensuremath{''}$). On the other hand, we find that the peaks of \[C ii\] and Ly$\alpha$ from Himiko have an offset ($\sim0.3\ensuremath{''}$) from those of the UV continuum and H$\alpha$ peaks of Himiko-A or Himiko-B. This offset is beyond the positional uncertainty, and we discuss the physical origin of the offset in Section [5](#sec:discussion). \[C ii\] emission of CR7 is spatially resolved, and we find two flux peaks near the position of CR7-A and -B, indicating that the \[C ii\] is mainly associated with the stellar component of CR7 and consistent with (cite: matthee17).

Figure [4](#fig:lya-map) shows the spatial distribution of the Ly$\alpha$ emission from Himiko (left) and CR7 (right), observed with NIRSpec IFU (background map) and Subaru NB921 (blue contours). For comparison, the H$\alpha$ distribution is also shown with gray contours. In the NIRSpec IFU images, the Ly$\alpha$ emission peaks for Himiko and CR7 are located around Himiko-A and CR7-A, respectively. Furthermore, Ly$\alpha$ emission can be observed between Himiko-A and Himiko-B, coinciding with the peak in the Subaru NB921 image. Similarly, there is Ly$\alpha$ emission between CR7-A and CR7-B. (cite: matthee20) have reported that the spatial distribution of Ly$\alpha$ elongated from CR7-A to CR7-B, which is consistent with the JWST NIRSpec PRISM data.

Figure [5](#fig:integrated-spectrum-himiko) and Figure [6](#fig:integrated-spectrum-CR7) show the spatially integrated spectrum of Himiko and CR7, respectively. The apertures to extract the spectrum are shown in Figure [2](#fig:ifu_oiii), and we conduct no aperture corrections. We find clear Ly$\alpha$ emission lines in Himiko-A and CR7-A, although other clumps do not. We utilize these spatially integrated spectra to measure the fluxes of each clump. Table [1](#tab:flux-measurement) summarizes the flux measurements for each clump. We also list the values of CR7 from the literature (cite: marconcini24b). The flux measurements of CR7 are almost in agreement with those of (cite: marconcini24b) within 2$\sigma$, despite the slight differences in the apertures (see Figure 1 of (cite: marconcini24b)).

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Object | \[O ii\] | \[Ne  iii\] | H$\delta$ | H$\gamma$ | \[O iii\] | H$\beta$ | \[O iii\] | H$\alpha$ | reference |  |
|  | $\lambda$3727 | $\lambda$3869 |  |  | $\lambda$4363 |  | $\lambda$5007 |  |  |  |
| Himiko-A | 0.6$\pm$0.2 | 0.6$\pm$0.1 | 0.3$\pm$0.1 | 0.6$\pm$0.1 | 0.2$\pm$0.1 | 1.2$\pm$0.1 | 9.2$\pm$0.1 | 3.2$\pm$0.1 | This work |  |
| Himiko-B | 1.0$\pm$0.2 | 0.7$\pm$0.1 | 0.4$\pm$0.1 | 0.7$\pm$0.1 | 0.2$\pm$0.1 | 1.2$\pm$0.1 | 9.8$\pm$0.1 | 4.4$\pm$0.1 | This work |  |
| Himiko-C | 1.5$\pm$0.2 | 1.1$\pm$0.1 | 0.5$\pm$0.1 | 0.9$\pm$0.1 | 0.2$\pm$0.1 | 1.8$\pm$0.1 | 13.6$\pm$0.1 | 4.9$\pm$0.1 | This work |  |
| Himiko-D | ... | ... | ... | ... | ... | ... | 0.63$\pm$0.04 | 0.3$\pm$0.1 | This work |  |
| Himiko-E | ... | ... | ... | ... | ... | ... | 0.24$\pm$0.04 | ... | This work |  |
| CR7-A | 3.8$\pm$0.5 | 4.0$\pm$0.2 | 1.7$\pm$0.1 | 3.3$\pm$0.1 | 1.3$\pm$0.1 | 6.8$\pm$0.2 | 56.5$\pm$0.4 | 19.1$\pm$0.3 | This work |  |
|  | 5.5$\pm$1.6 | 4.6$\pm$0.7 | 1.8$\pm$0.5 | 3.2$\pm$0.4 | 1.15$\pm$0.4 | 7.3$\pm$0.4 | 62.6$\pm$0.4 | 21.5$\pm$0.7 | (cite: marconcini24b) |  |
| CR7-B | 1.8$\pm$0.4 | 0.8$\pm$0.1 | 0.2$\pm$0.1 | 0.6$\pm$0.1 | 0.2$\pm$0.1 | 1.5$\pm$0.1 | 10.7$\pm$0.1 | 4.1$\pm$0.2 | This work |  |
|  | 1.8$\pm$0.4 | 0.8$\pm$0.3 | 0.3$\pm$0.2 | 0.3$\pm$0.2 | 0.1$\pm$0.1 | 1.5$\pm$0.3 | 12.5$\pm$0.3 | 4.3$\pm$0.5 | (cite: marconcini24b) |  |
| CR7-C | 1.1$\pm$0.4 | 0.5$\pm$0.1 | 0.2$\pm$0.1 | 0.5$\pm$0.1 | ... | 0.9$\pm$0.1 | 5.4$\pm$0.1 | 2.5$\pm$0.1 | This work |  |
|  | 1.4$\pm$0.4 | 0.4$\pm$0.3 | 0.2$\pm$0.2 | ... | ... | 0.9$\pm$0.3 | 5.8$\pm$0.3 | 2.3$\pm$0.3 | (cite: marconcini24b) |  |
| CR7-D | ... | ... | ... | ... | ... | ... | 0.8$\pm$0.1 | ... | This work |  |
|  | ... | ... | ... | ... | ... | ... | ... | ... | (cite: marconcini24b) |  |

: Flux measurements of Himiko and CR7.

Table notes: Integrated emission line fluxes ($>$3$\sigma$) that are estimated by a single Gaussian fitting. Each aperture is shown in Figure [2](#fig:ifu_oiii). The fluxes are not corrected for dust extinction and units of $10^{-18}$ erg s$^{-1}$ cm$^{-2}$. All flux values are measured from the G395H spectra except for \[O ii\]$\lambda3727$, which is derived from the PRISM spectra. (cite: marconcini24b) have used slightly different apertures compared to this work (see Figure 1 of (cite: marconcini24b)), but the flux measurements of CR7 align well.

Figure [7](#fig:Ha) shows the spectrum of H$\alpha$ emission from Himiko-A, -B, -C, and CR7-A, -B, -C. Thanks to the high-resolution data from NIRSpec IFU, we can investigate the multiple components of the H$\alpha$ emission lines (see Section [3](#sec:analysis)). The right panel of Figure [2](#fig:ifu_oiii) also shows the \[O iii\] emission lines from the individual clumps. The \[O iii\]$\lambda$5007 emission lines have the highest S/N, allowing us to detect both narrow and broad components. Especially, Himiko-C and CR7-A have broad components of $\mathrm{FWHM=250}$, and $400~\mathrm{km~s^{-1}}$ with $\Delta\mathrm{AIC}>20$, respectively. The broad components in the \[O iii\] emission lines may originate from outflows or tidal features. We discuss the connection between this outflow or tidal features with the origin of the extended Ly$\alpha$ emission in Section [5.4](#subsec:extended-Lya). Additionally, we conduct the Gaussian fitting to H$\alpha$ emission lines independently of \[O iii\] emission lines. For H$\alpha$ emission lines, there are also several components in one emission line. Himiko-B shows a distorted H$\alpha$ emission line profile, which is best characterized by two narrow components ($\mathrm{FWHM}\sim100~\mathrm{km~s^{-1}}$) and one broad component. The two narrow components have similar redshifts compared to their \[O iii\] emission line components. The two narrow components remain even when using smaller apertures, suggesting that they may originate from gas clouds in front or behind Himiko-B. H$\alpha$ emission line in Himiko-B also has a broad component with FWHM$=1030\pm110~\mathrm{km~s^{-1}}$, which cannot be observed in the \[O iii\] emission line. This broad permitted line (H$\alpha$) and the narrow forbidden line (\[O iii\]) can indicate the possibility of active galactic nuclei (AGN). We further characterize the AGN signature in Section [4.4](#subsec:AGN). We note that no significant broad H$\beta$ component is detected from Himiko-B, possibly due to the lower S/N than H$\alpha$. Similarly, Himiko-C has a broad component in the H$\alpha$ emission line with $\mathrm{FWHM}=840\pm140\mathrm{~km~s^{-1}}$, which could be attributed to either stellar outflows or AGN activity. Since a threshold value of $\mathrm{FWHM=1000~km~s^{-1}}$ is often adopted to identify AGNs (e.g., (cite: harikane23b; matthee24)), the nature of this broad component remains uncertain. We do not further investigate the broad H$\alpha$ component of Himiko-C in this study.

We also investigate moment maps to characterize the dynamics of these objects, which cannot be achieved from the spatially integrated spectra. In Figure [8](#fig:moment-maps), we show the \[Oiii\]$\lambda$5007 moment 0 (left), 1 (middle), 2 (right) maps of Himiko (top), and CR7 (bottom). In Figure [8](#fig:moment-maps), we only use the spaxels with $\mathrm{S/N}>5$ to calculate the moment maps. We find that the velocity (moment 1) maps of both Himiko and CR7 show complex kinematics with a velocity offset of $\Delta v \lesssim 220~\mathrm{km~s^{-1}}$, indicating that each clump has close separations between other clumps. In the velocity maps, neither Himiko nor CR7 shows an entire galaxy-scale, disk-like velocity gradient. This disfavors a single rotating disk and motivates a merger scenario for the origin of the clumps discussed in Sections [5.1](#subsec:multiple-clumps) and [5.2](#subsec:jwst-clump-comparison). CR7-A shows a velocity gradient from north to south, which might be a signature of a rotating disk (see also (cite: marconcini24b)). In this study, a detailed investigation of this potential rotation signature is beyond the scope, and we do not further explore it. (cite: matthee17) have reported the velocity map of CR7 utilizing ALMA \[C ii\]$158\ensuremath{\mu}m$ emission line. The \[C ii\] velocity map has a similar velocity kinematics as that of \[O iii\]$\lambda5007$, indicating that the \[C ii\] emission aligns well with the ionized gas distribution represented by \[O iii\] emission.

Figure [9](#fig:spectrum-jwst-alma) shows the comparison between the \[O iii\]$\lambda5007$ (gray), \[C ii\]$158\ensuremath{\mu}m$ (red), and Ly$\alpha$ (blue; (cite: ouchi09; sobral15)) spectra of Himiko (left) and CR7 (right). The \[C ii\] emission line of Himiko is mainly aligned with the \[O iii\]$\lambda5007$ emission line of Himiko-A. For CR7, the \[C ii\] emission is located within the \[O iii\]$\lambda5007$ emission from CR7-A to CR7-C, as indicated by the \[O iii\] and \[C ii\] velocity maps (see also (cite: matthee17)). The peaks of the Ly$\alpha$ emission from both Himiko and CR7 are redshifted relative to the \[O iii\] emission lines. However, measuring the velocity offset of the Ly$\alpha$ emission is challenging because the Ly$\alpha$ emission from Himiko and CR7 is extended across multiple clumps.

## Spectral energy distribution

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Object | F090W | F115W | F150W | F200W | F277W | F356W | F410M | F444W |
|  | ($\mu\mathrm{Jy}$) | ($\mu\mathrm{Jy}$) | ($\mu\mathrm{Jy}$) | ($\mu\mathrm{Jy}$) | ($\mu\mathrm{Jy}$) | ($\mu\mathrm{Jy}$) | ($\mu\mathrm{Jy}$) | ($\mu\mathrm{Jy}$) |
| Himiko-A | $0.048\pm0.007$ | $0.127\pm0.007$ | $0.101\pm0.006$ | $0.092\pm0.005$ | $0.096\pm0.003$ | $0.183\pm0.003$ | $0.066\pm0.006$ | $0.098\pm0.004$ |
| Himiko-B | $0.025\pm0.007$ | $0.065\pm0.007$ | $0.064\pm0.006$ | $0.075\pm0.005$ | $0.070\pm0.003$ | $0.178\pm0.003$ | $0.071\pm0.006$ | $0.109\pm0.004$ |
| Himiko-C | $0.041\pm0.007$ | $0.117\pm0.007$ | $0.117\pm0.006$ | $0.112\pm0.005$ | $0.122\pm0.003$ | $0.262\pm0.003$ | $0.078\pm0.006$ | $0.120\pm0.004$ |
| CR7-A | ... | $0.242\pm0.013$ | $0.246\pm0.010$ | ... | $0.282\pm0.006$ | ... | ... | $0.238\pm0.006$ |
| CR7-B | ... | $0.046\pm0.010$ | $0.048\pm0.008$ | ... | $0.048\pm0.005$ | ... | ... | $0.056\pm0.005$ |
| CR7-C | ... | $0.051\pm0.010$ | $0.043\pm0.008$ | ... | $0.040\pm0.005$ | ... | ... | $0.029\pm0.005$ |

: NIRCam photometry measurements of Himiko and CR7.

Table notes: All Himiko clumps, CR7-B, and CR7-C are extracted with $0.4\ensuremath{''}$-diameter apertures, while $0.5\ensuremath{''}$-diameter aperture is used for CR7-A.

Table [2](#tab:NIRCam-phot) summarizes the NIRCam photometry with $1\sigma$ uncertainties for Himiko and CR7, respectively. SED fittings are performed only for clumps detected in multiple filters with a significance greater than $5\sigma$ (specifically, Himiko-A, -B, and -C; CR7-A, -B, and -C). The parameter settings are described in Section [3.2](#subsec:sed_modeling). Table [3](#tab:SED-fitting) shows the physical properties of Himiko and CR7 as inferred from the SED fitting. Figure [10](#fig:sed-fitting) displays the best-fit SEDs for these objects. For Himiko, Himiko-A and -C have a similar spectral shape, while Himiko-B has a redder spectrum with $A_V=0.48^{+0.06}_{-0.06}~\mathrm{mag}$ compared to the other two clumps ($A_V\sim0.03$–$0.21$ mag). The stellar masses of individual Himiko clumps range $\log{(M_*/M_\odot)}=8.4$–$8.9$, with a mean stellar mass of $\log{(M_*/M_\odot)}=8.6$. This result is broadly consistent with that of (cite: harikane25). In the case of CR7, CR7-A is the brightest clump and has the highest star formation rate (SFR) measured at $23.4^{+2.4}_{-3.0}~M_\odot~\mathrm{yr^{-1}}$, which is averaged over the past 10 Myr. This rate is approximately ten times higher than that of the other two clumps, indicating that CR7-A mainly dominates star formation in CR7. CR7-A and CR7-B have comparable stellar masses, each with $\log{(M_*/M_\odot)}=8.8$–$8.9$, while CR7-C has a lower stellar mass of $\log{(M_*/M_\odot)}=8.3^{+0.3}_{-0.3}$. These results align well with the stellar mass estimates of CR7 derived from NIRSpec IFU spectra by (cite: marconcini24b) within 2$\sigma$. Individual Himiko and CR7 clumps primarily lie on the SFR–$M_*$ main sequence at $z\sim6$ (e.g., (cite: santini17)). Figure [11](#fig:sfh) shows the inferred SFHs from the SED fitting. The SFHs of all the clumps show rising trends (starbursts) toward the 0–10 Myr age bins, although the uncertainties in the SFHs are large at $>10$ Myr (see also (cite: harikane25; marconcini24b)). These increasing trends in SFHs could be associated with galaxy mergers (e.g., (cite: hopkins08; asada24)). We further discuss the implications of galaxy mergers and their scenarios in Section [5](#sec:discussion).

+------------+-----------------------------------------------------------------------------+--------------------------------------------------+-----------------------+
|            | SED fitting                                                                 | direct method                                    |                       |
+:===========+:===================:+:============================:+:======================:+:====================:+:=========================:+:=====================:+
| 2-4 Object | $\log{(M_*)}$       | SFR                          | $A_V$                  | $T_e$(\[O iii\])     | $12+\log{(\mathrm{O/H})}$ | reference             |
+------------+---------------------+------------------------------+------------------------+----------------------+---------------------------+-----------------------+
|            | ($M_\odot$)         | ($M_\odot~\mathrm{yr}^{-1}$) | (mag)                  | ($10^4\,\mathrm{K}$) |                           |                       |
+------------+---------------------+------------------------------+------------------------+----------------------+---------------------------+-----------------------+
| Himiko-A   | $8.4^{+0.2}_{-0.1}$ | $7.9^{+0.6}_{-0.6}$          | $0.03^{+0.03}_{-0.02}$ | $1.6\pm0.3$          | $7.92\pm0.19$             | This work             |
+------------+---------------------+------------------------------+------------------------+----------------------+---------------------------+-----------------------+
| Himiko-B   | $8.9^{+0.1}_{-0.2}$ | $11.7^{+1.2}_{-1.0}$         | $0.48^{+0.06}_{-0.06}$ | $1.6\pm0.3$          | $7.90\pm0.20$             | This work             |
+------------+---------------------+------------------------------+------------------------+----------------------+---------------------------+-----------------------+
| Himiko-C   | $8.4^{+0.1}_{-0.1}$ | $14.1^{+0.9}_{-0.7}$         | $0.21^{+0.04}_{-0.04}$ | $1.4\pm0.2$          | $8.02\pm0.14$             | This work             |
+------------+---------------------+------------------------------+------------------------+----------------------+---------------------------+-----------------------+
| CR7-A      | $8.8^{+0.1}_{-0.2}$ | $23.4^{+2.4}_{-3.0}$         | $0.13^{+0.04}_{-0.05}$ | $1.6\pm0.1$          | $7.90\pm0.06$             | This work             |
+------------+---------------------+------------------------------+------------------------+----------------------+---------------------------+-----------------------+
|            | $9.3^{+0.1}_{-0.1}$ | $25.7^{+1.2}_{-1.1}$         | $0.20^{+0.01}_{-0.01}$ | $1.6$                | $8.0$                     | (cite: marconcini24b) |
+------------+---------------------+------------------------------+------------------------+----------------------+---------------------------+-----------------------+
| CR7-B      | $8.9^{+0.2}_{-0.2}$ | $2.9^{+1.4}_{-0.9}$          | $0.13^{+0.15}_{-0.09}$ | $1.3\pm0.2$          | $8.11\pm0.20$             | This work             |
+------------+---------------------+------------------------------+------------------------+----------------------+---------------------------+-----------------------+
|            | $8.5^{+0.2}_{-0.2}$ | $5.9^{+0.5}_{-0.4}$          | $0.14^{+0.05}_{-0.03}$ | $0.9$                | $8.08$                    | (cite: marconcini24b) |
+------------+---------------------+------------------------------+------------------------+----------------------+---------------------------+-----------------------+
| CR7-C      | $8.3^{+0.3}_{-0.3}$ | $2.8^{+0.6}_{-0.6}$          | $0.05^{+0.07}_{-0.04}$ | ...                  | ...                       | This work             |
+------------+---------------------+------------------------------+------------------------+----------------------+---------------------------+-----------------------+
|            | $8.3^{+0.3}_{-0.1}$ | $3.8^{+0.7}_{-0.7}$          | $0.08^{+0.04}_{-0.03}$ | ...                  | ...                       | (cite: marconcini24b) |
+------------+---------------------+------------------------------+------------------------+----------------------+---------------------------+-----------------------+

: Physical properties of Himiko and CR7 (SED fitting and direct method).

Table notes: Columns: (1) object name; (2) stellar mass; (3) star formation rate averaged over the past 10 Myr; (4) $V$-band magnitude of dust attenuation; (5) electron temperature from the direct method; (6) gas phase metallicity $12+\log{(\mathrm{O/H})}$ from the direct method. Since (cite: marconcini24b) have not reported the electron temperature of CR7-C, the electron temperature and the metallicity of CR7-C from (cite: marconcini24b) are not listed.; (7) references.

We also perform pixel-by-pixel SED fitting (e.g., (cite: sorba15; sorba18; gimenez’-arteaga23)) to examine spatially resolved physical properties using the high-resolution NIRCam photometry. We use the NIRCam images whose PSFs are matched to F444W. Only pixels detected in the F444W segmentation map, constructed by SEP, are included in the fitting. The model settings for the pixel-by-pixel SED fitting are the same as those used for the aperture photometry, except for the stellar mass prior range, which is set to $6<\log{(M_*/M_\odot)}<10$. Figure [12](#fig:pixel-by-pixel-sed) shows the stellar mass densities ($\Sigma_*$), the SFR densities ($\Sigma_\mathrm{SFR}$), and the specific star formation rate (sSFR) of Himiko (top) and CR7 (bottom) inferred from the pixel-by-pixel SED fitting.

For Himiko, the central region of Himiko-B has high stellar mass density distributions ($\log{(\Sigma_*\,[M_\odot~\mathrm{kpc^{-2}}])}\sim 9$). SFR and sSFR distributions are high in the central regions of Himiko clumps ($\Sigma_{\mathrm{SFR}}\sim3~M_\odot~\mathrm{yr^{-1}~kpc^{-2}}$ at maximum). One interesting point is that the west side of Himiko-A has about one order of magnitude higher sSFR than the east. This region is near the peak position of the Ly$\alpha$ emission indicated by the Subaru NB image (Figure [3](#fig:jwst-alma-subaru-image)). This result could indicate that the region also contributes to the bright Ly$\alpha$ emission of Himiko, although the gas distribution is also key to explaining the distribution of the Ly$\alpha$ emission. For CR7, CR7-A has the highest stellar mass density ($\log{(\Sigma_*\,[M_\odot~\mathrm{kpc^{-2}}])}\sim 8.5$) and SFR surface density ($\Sigma_{\mathrm{SFR}}\sim5~M_\odot~\mathrm{yr^{-1}~kpc^{-2}}$), which is consistent with the SED fitting using the total photometry of CR7-A. (cite: marconcini24b) have conducted spatially resolved SED fittings of CR7 using NIRSpec IFU data, and their results are consistent with ours.

## Emission line diagnostics

We focus on the IFU data to characterize the ionizing conditions of Himiko and CR7. Using the Balmer lines (H$\alpha$ and H$\beta$), we assess dust extinction, assuming an electron density of $n_e = 100~\mathrm{cm^{-3}}$, an electron temperature of $T_e = 15000~\mathrm{K}$, and case B recombination (cite: osterbrock06). We use the (cite: calzetti00) extinction law and obtain a nebular attenuation of $A_V = 0.00, 0.73, 0.02$ ($A_V = 0.01, 0.00, 0.02$) for Himiko-A, -B, and -C (CR7-A, -B, and -C), respectively. These values are consistent with the SED fitting results using NIRCam photometry (Section [4.2](#subsec:sed)). These low values are also in line with the low dust content indicated by the non-detection of dust continuum through ALMA Band 6 observations (see also (cite: matthee17; carniani18)). Further discussion of this low dust condition and its relation to merger systems are provided in Section [5.6](#subsec:comparison).

We calculate the standard line ratios: \[O iii\]$\lambda5007$/H$\beta$ (R3), (\[O iii\]$\lambda\lambda5007, 4959$ + \[O ii\]$\lambda3727$)/H$\beta$ (R23), and \[O iii\]$\lambda5007$/\[O ii\]$\lambda3727$ (O32). We also detect the \[O iii\]$\lambda4363$ auroral line that enables us to measure an electron temperature and metallicity using the direct method. When calculating the line ratios and metallicity, we do not apply dust extinction corrections, as Himiko and CR7 have low dust contents, and the procedure does not change the overall results. We estimate the electron temperature of O$^{2+}$ zone $T_e$(\[O iii\]) using the \[O iii\]$\lambda4363$/\[O iii\]$\lambda5007$ ratio with the Pyneb (cite: luridiana15) package `getTemDen`. We assume an electron number density of $n_e=100~\mathrm{cm^{-3}}$ because we do not resolve the \[O ii\]$\lambda3726, 3729$ lines in the PRISM spectra ($R\sim100$). The O$^{+}$ zone temperature $T_e$(\[O ii\]) is estimated from $T_e$(\[O iii\]) (cite: garnett92). We obtain the abundance of O$^{2+}$/H$^+$ with the \[O iii\]$\lambda4959, 5007$, H$\beta$, and $T_e$(\[O iii\]), and O$^{+}$/H$^{+}$ with the \[O ii\]$\lambda3727$, H$\beta$ and $T_e$(\[O ii\]) using the Pyneb package `getIonAbundance`. We ignore a higher ionization abundance of O$^{3+}$/H$^{+}$ (cite: izotov06).

Figure [13](#fig:line_ratio) shows the line ratio diagnostics (left: \[N ii\] BPT diagram; (cite: baldwin81), middle: O32-R23) and mass-metallicity relation (right) of Himiko (red squares) and CR7 (magenta squares). In the \[N ii\] BPT diagram (left panel of Figure [13](#fig:line_ratio)), all clumps of Himiko and CR7 have high \[O iii\]$\lambda5007$/H$\beta$ values, indicating the high ionization parameters. We cannot find an AGN signature only in the \[N ii\] BPT diagram, although they are located at the edge of the demarcation curves between star-forming and AGN (cite: kewley01; kauffmann03). This might be due to the low metallicity or high ionization states (e.g., (cite: nakajima22)).

In the O32-R23 diagram (middle panel of Figure [13](#fig:line_ratio)), the Himiko and CR7 clumps show higher O32 values than the Sloan Digital Sky Survey (SDSS) galaxies. When we compare Himiko and CR7 clumps with the other high redshift galaxies observed with JWST (e.g., (cite: nakajima23; cameron23)), they both show high O32 values, which can be explained by the hard ionizing radiation field and a low metallicity (e.g., (cite: nakajima16)).

From the direct method, we obtain the electron temperature $T_e$(\[O iii\]) of $(1.6\pm0.3)\times10^4$ K, $(1.6\pm0.3)\times10^4$ K, $(1.4\pm0.2)\times10^4$ K, $(1.6\pm0.1)\times10^4$ K, and $(1.3\pm0.2)\times10^4$ K for Himiko-A, -B, -C, CR7-A, and -B, respectively. The metallicities are estimated as $12+\log{(\mathrm{O/H})}=7.92\pm0.19, 7.90\pm0.20, 8.02\pm0.14, 7.90\pm0.06$, and $8.11\pm0.20$ for Himiko-A, -B, -C, CR7-A, and -B, respectively (see Table [3](#tab:SED-fitting)). For CR7-C, we do not detect the \[O iii\]$\lambda$4363 line. In the relation between metallicity and stellar mass (right panel of Figure [13](#fig:line_ratio)), the positions of Himiko and CR7 broadly align with the mass-metallicity relation established by JWST-observed galaxies at $z>4$ (e.g., (cite: heintz23; curti24a; nakajima23)). The caveat is that Himiko-B shows the broad H$\alpha$ emission line explained by AGN activity (see Section [4.4](#subsec:AGN)). The metallicity measurements might be affected by the AGN.

Additionally, we can explore the spatially resolved line ratio properties, thanks to the high-resolution spectroscopy obtained with JWST. Figure [14](#fig:line_ratio_map) presents the line ratio maps (H$\alpha$/H$\beta$, $E(B-V)$ derived from H$\alpha$/H$\beta$, R3, and metallicity derived from R3) for Himiko (top) and CR7 (bottom). We do not correct the dust extinction for the R3 maps. From the H$\alpha$/H$\beta$ and $E(B-V)$ maps of Himiko, we observe that Himiko-A has low dust extinctions ($E(B-V)\sim0$). The $E(B-V)$ values are slightly higher ($\gtrsim0.2$) in the region between Himiko-B and Himiko-C compared to Himiko-A or the central region of Himiko-B and -C. The region between Himiko-B and Himiko-C has smaller fluxes than the central areas of the clumps, and the overall dust extinction of Himiko is low ($E(B-V)\lesssim0.18$). In the case of CR7, all clumps show low dust extinctions ($E(B-V)\sim0$). When examining the R3 maps, we find high R3 values ($\mathrm{R3}\sim10$) in CR7-A. Notably, CR7-A has a spatial gradient of R3; the north is low ($\mathrm{R3}\sim7$) while the south is high ($\mathrm{R3}\sim9$), which aligns with (cite: marconcini24b). The metallicities derived from R3 using the relation presented in (cite: hirschmann23) range from $12+\log(\mathrm{O/H})=7.5$–$8.0$, which generally agrees with those measured by the direct method (see Figure [13](#fig:line_ratio)).

## Signature of AGN

Himiko-B has the broad permitted H$\alpha$ emission line ($\mathrm{FWHM}=1030\pm110~\mathrm{km~s^{-1}}$) with narrow forbidden \[O iii\] emission (Section [4.1](#subsec:morphology)). The broad H$\alpha$ emission feature suggests that the broad component is powered by AGN activity, especially from its broad line region (e.g., (cite: kocevski23; harikane23b; maiolino23; juodvzbalis25)).

Table [4](#tab:BH-properties) summarizes the black hole properties of Himiko-B. We estimate the black hole mass ($M_\mathrm{BH}$) following the equation 5 of (cite: reines13): $$\begin{equation}
\begin{split}
& \log{\left(\frac{M_\mathrm{BH}}{M_\odot} \right)} = \log{(\epsilon)} + 6.57 \notag \\
& +0.47\log{\left( \frac{L_\mathrm{H\alpha}}{10^{42}~\mathrm{erg~s^{-1}}} \right)} + 2.06 \log{\left( \frac{\mathrm{FWHM_{H\alpha}}}{10^3~\mathrm{km~s^{-1}}} \right)}, 
\end{split}
\end{equation}$$ where $\epsilon$ is a scaling factor related to the geometry and kinematics of the broad line region. We adopt $\epsilon=1.075$ following (cite: reines15). Here, $L_\mathrm{H\alpha}$ and $\mathrm{FWHM_{H\alpha}}$ are the broad-line H$\alpha$ luminosity and the FWHM, respectively (see also (cite: green05)). We measure a black hole mass of $\log{(M_\mathrm{BH}/M_\odot)}=6.6^{+0.1}_{-0.2}$, and its uncertainties are based on the variation of $\epsilon$ ($\epsilon=0.75$–$1.4$; (cite: onken04; reines13)). The corresponding Eddington luminosity: $$\begin{equation}
    L_{\mathrm{Edd}}=1.3\times10^{38}\left( \frac{M_{\mathrm{BH}}}{M_\odot} \right)\,\mathrm{erg~s^{-1}}
\end{equation}$$ is $5.1^{+1.6}_{-1.5}\times10^{44}$ erg s$^{-1}$. The black hole mass remains unchanged even when we reduce the size of the aperture to $0.2\ensuremath{''}$–$0.3\ensuremath{''}$, confirming that the broad H$\alpha$ line comes from the central region of Himiko-B. The black hole mass estimations have a systematic uncertainty of 0.5 dex (cite: reines15).

| Measurements | Value |
|:---|:--:|
| $\log{(M_\mathrm{BH}/M_\odot)_\mathrm{H\alpha}}$ | $6.6^{+0.1}_{-0.2}$ |
| $L_\mathrm{bol}$ | $5.7^{+19.0}_{-3.8}\times10^{44}$ erg s$^{-1}$ |
| $L_\mathrm{Edd}$ | $5.1^{+1.6}_{-1.5}\times10^{44}$ erg s$^{-1}$ |
| $\lambda_\mathrm{Edd}$ | $1.1^{+3.7}_{-0.8}$ |

: AGN properties of Himiko-B.

Table notes: These properties are estimated using a $0.3\ensuremath{''}$ circular aperture.

Figure [15](#fig:MBH-Mstar) shows the relation between black hole mass and the stellar mass of Himiko-B. Himiko-B is located in a region similar to the high-$z$ AGN samples identified with JWST (red plots; e.g., (cite: harikane23b; maiolino23)). Compared to the local AGN samples (gray plots and line; (cite: reines15)), Himiko-B shows a higher black hole mass (or lower stellar mass) by an order of magnitude, although the local and high-$z$ AGN samples have large scatters.

We note that the stellar mass of Himiko-B is derived from the SED fitting using all fluxes (i.e., without decomposition into a host galaxy and a point source). Therefore, the actual stellar mass can be lower than our estimate due to contributions from the AGN. However, since we see the extended morphology of Himiko-B in the rest-frame UV to optical image (Figure [1](#fig:NIRCam-cutout)), we can consider that its stellar components mainly dominate the photometry.

We calculate the bolometric luminosity ($L_\mathrm{bol}$) of Himiko-B following the procedure of (cite: harikane23b). The best value of the bolometric luminosity is derived from the relation between H$\alpha$ luminosity and 5100Å luminosity in (cite: green05): $$\begin{equation}
    L_{5100} = 10^{44} \times \left( \frac{L_\mathrm{H\alpha}}{5.25 \times10^{42}~\mathrm{erg~s^{-1}}} \right)^{1/1.157}~\mathrm{erg~s~^{-1}}, \label{eq:L5100}
\end{equation}$$ where $L_\mathrm{H\alpha}$ is the sum of the narrow and broad-line H$\alpha$ luminosity. We convert $L_{5100}$ to $L_\mathrm{bol}$ using the relation of $L_\mathrm{bol}=10.33 \times L_{5100}$ (cite: richards06). For the lower limit, we use Equation ([\[eq:L5100\]](#eq:L5100)) with only broad-line H$\alpha$ luminosity and calculate the bolometric luminosity using the relation of $L_\mathrm{bol}=9.8\times L_{5100}$ (cite: mclure04). For the upper limit, we follow the calibration in (cite: netzer09): $$\begin{equation}
\begin{split}
\log{\left ( \frac{L_\mathrm{bol}}{\mathrm{erg~s^{-1}}} \right)} = & \log{\left ( \frac{L_\mathrm{H\beta}}{\mathrm{erg~s^{-1}}} \right)} + 3.48 \notag \\ 
& + \mathrm{max[0.0, 0.31(\log{([\textsc{O\,iii}]/H\beta)} - 0.6)]}, 
\end{split}
\end{equation}$$ where $L_\mathrm{H\beta}$ is the H$\beta$ luminosity. We obtain the bolometric luminosity of Himiko-B as $L_\mathrm{bol}=5.7^{+19.0}_{-3.8}\times10^{44}$ erg s$^{-1}$. We do not apply dust-extinction corrections to the black hole mass and bolometric luminosity values because a broad H$\beta$ component is not detected and the dust extinction of the broad line is unclear.

Figure [16](#fig:Lbol-MBH) shows the relation between the bolometric luminosity and the black hole mass. As a comparison, we also plot other broad-line AGNs found by JWST (cite: harikane23b; maiolino23) and high-$z$ quasars at $z\sim4$–$6$ (cite: trakhtenbrot11; shen19) in red and blue, respectively. We also show the low-$z$ AGN distributions (cite: shen11; liu19) in blue and gray contours. Himiko-B has a higher bolometric luminosity than the low-$z$ AGNs and a similar $M_\mathrm{BH}$–$L_\mathrm{bol}$ relation compared to the samples found by JWST, although the uncertainty of bolometric luminosity is large.

Numerical simulations have suggested that a galaxy merger is a trigger to cause AGN activity (e.g., (cite: hopkins08; zana22)). Additionally, recent JWST or ALMA observations have revealed the merging phase AGNs or quasars in the high redshift Universe (see, e.g., (cite: perna23; ubler24; harikane23b; maiolino23; izumi24; perna25)). Given that Himiko is in a merging phase (Section [5.1](#subsec:multiple-clumps)), we might observe the growth of a supermassive black hole induced by the merger.

It is worth noting that there are other possibilities of producing a broad H$\alpha$ emission line, such as massive star outflow, Type IIn supernovae, and tidal disruption events (e.g., (cite: kokubo24)). These mechanisms broaden both permitted H$\alpha$ line and forbidden \[O iii\] line. However, Himiko has the broad ($\mathrm{FWHM>1000~\mathrm{km~s^{-1}}}$) component only in the H$\alpha$ line and remains \[O iii\] line narrow ($\mathrm{FWHM\lesssim400~\mathrm{km~s^{-1}}}$), which favors emission from a high-density broad line region around a supermassive black hole (see also e.g., (cite: maiolino23; greene24)). We do not detect any other AGN signatures, such as high-excitation UV emission lines (e.g., C iv\]) in the JWST/NIRSpec data. Further observations are needed to obtain other AGN signs from Himiko.

We also note that all CR7 clumps do not show any H$\alpha$ components with $\mathrm{FWHM>1000~\mathrm{km~s^{-1}}}$ that are broader than the \[O iii\] components ($\mathrm{FWHM\lesssim400~\mathrm{km~s^{-1}}}$). (cite: marconcini24b) have argued the tentative evidence of AGN ionization for CR7-A and CR7-B using the excitation diagnostics of \[O iii\]$\lambda$/H$\gamma$ vs \[O iii\]$\lambda5007$/\[O iii\]$\lambda4363$ (cite: mazzolari24) and the high \[O iii\]$\lambda5007$/H$\beta$ values (\[O iii\]$\lambda5007$/H$\beta\sim10$; Figure [14](#fig:line_ratio_map)).

## \[CII\] and IR luminosity

Figure [17](#fig:CII_IRluminosity) shows the relation between \[C II\]-IR luminosity ratio ($L_\mathrm{[\textsc{C\,ii}]}/L_\mathrm{IR}$) and IR luminosity ($L_\mathrm{IR}$; 8–1000 $\ensuremath{\mu}m$). Their \[C ii\] and IR luminosities are also summarized in Table [5](#tab:ALMA-measurement). Himiko and CR7 are not detected in the dust continuum with the 3$\sigma$ upper limits of $S_\mathrm{158\,\mu m}<31~\mathrm{\mu Jy}$ and $S_\mathrm{158\,\mu m}<19~\mathrm{\mu Jy}$, respectively. These upper limits correspond to the IR luminosity of $<4\times10^{10}~L_\odot$ and $<3\times10^{10}~L_\odot$ for Himiko and CR7, respectively, assuming the dust temperature of $T_\mathrm{dust}=40~\mathrm{K}$ and the dust emissivity index of $\beta_\mathrm{IR}=1.5$. The IR luminosity depends on the $T_\mathrm{dust}$ and $\beta_\mathrm{IR}$, but the trends of $L_\mathrm{[\textsc{C\,ii}]}/L_\mathrm{IR}$ or $L_\mathrm{IR}$ for Himiko and CR7 still hold if we adopt other $T_\mathrm{dust}$ or $\beta_\mathrm{IR}$ values ($30~\mathrm{K}<T_\mathrm{dust}<50~\mathrm{K}$ or $1.5<\beta_\mathrm{IR}<2.0$). For comparison, we overlay some UV bright ($M_\mathrm{UV} \lesssim -21.5$) and clumpy galaxies at $z\sim7$ (cite: smit18; witstok22) in Figure [17](#fig:CII_IRluminosity), showing similar \[C ii\]-IR ratio limits as those of Himiko and CR7. On the other hand, we can see a distinct difference compared to other dusty merger systems ((cite: capak15; wong22; hashimoto19)) and submillimeter galaxy (SMG) samples ((cite: marrone18; gullberg15)), indicating the low dust content of Himiko and CR7. It is worth noting that SPT0311 ($z=6.9$; (cite: marrone18)) and HFLS3 ($z=6.3$; (cite: riechers13)) are the clumpy merging galaxies at redshifts similar to those of Himiko and CR7, but they show high IR luminosity, indicating their rich dust content. Even at $z\sim6$–$7$, there is a variety of IR luminosity or dust content in clumpy merging galaxies. We discuss details about the dust content of Himiko/CR7 and the comparison with other merger galaxies in Section [5.6](#subsec:comparison).

+--------------------------------------------------------------------------------------------+----------------------------------------+-------------------------------------+
|                                                                                            | Himiko-Total                           | CR7-Total                           |
+:==========================================================================================:+:=================:+:==================:+:===============:+:=================:+
| 2-3                                                                                        | This work         | (cite: carniani18) | This work       | (cite: matthee17) |
+--------------------------------------------------------------------------------------------+-------------------+--------------------+-----------------+-------------------+
| $z_{[\textsc{C\,ii}]}$                                                                     | 6.5913$\pm$0.0006 | 6.5913$\pm$0.0004  | 6.600$\pm$0.001 | 6.600$\pm$0.001   |
+--------------------------------------------------------------------------------------------+-------------------+--------------------+-----------------+-------------------+
| $\mathrm{FWHM_{[\textsc{C\,ii}]}}$ ($\mathrm{km~s^{-1}}$)                                  | 184$\pm$62        | 180$\pm$50         | 298$\pm$112     | 299$\pm$26        |
+--------------------------------------------------------------------------------------------+-------------------+--------------------+-----------------+-------------------+
| $S_\mathrm{[\textsc{C\,ii}]} \Delta\nu$ ($\mathrm{mJy~km~s^{-1}}$)                         | 70.9$\pm$15.9     | 108$\pm$13         | 196.9$\pm$32.5  | 185.2$\pm$39.0    |
+--------------------------------------------------------------------------------------------+-------------------+--------------------+-----------------+-------------------+
| $L_\mathrm{[\textsc{C\,ii}]}$ ($10^{8}\,L_\odot$)                                          | 0.80$\pm$0.17     | 1.2$\pm$0.2        | 2.22$\pm$0.37   | 2.17$\pm$0.36     |
+--------------------------------------------------------------------------------------------+-------------------+--------------------+-----------------+-------------------+
| $S_{158\,\mu \mathrm{m}}$ ($\mu$Jy)                                                        | $<31$             | $<27$              | $<19$           | $<21$             |
+--------------------------------------------------------------------------------------------+-------------------+--------------------+-----------------+-------------------+
| $L_\mathrm{IR}$ ($10^{10}\,L_\odot$)                                                       | $<4$              | $<3$               | $<3$            | $<3$              |
+--------------------------------------------------------------------------------------------+-------------------+--------------------+-----------------+-------------------+
| $M_\mathrm{dust}$ ($10^6~M_\odot$; $T_\mathrm{d}=35\,\mathrm{K}$, $\beta_\mathrm{IR}=1.5$) | $<13$             | ...                | $<8$            | $<8$              |
+--------------------------------------------------------------------------------------------+-------------------+--------------------+-----------------+-------------------+
| $M_\mathrm{dust}$ ($10^6~M_\odot$; $T_\mathrm{d}=40\,\mathrm{K}$, $\beta_\mathrm{IR}=1.5$) | $<9$              | ...                | $<5$            | ...               |
+--------------------------------------------------------------------------------------------+-------------------+--------------------+-----------------+-------------------+
| $M_\mathrm{dust}$ ($10^6~M_\odot$; $T_\mathrm{d}=45\,\mathrm{K}$, $\beta_\mathrm{IR}=1.5$) | $<6$              | ...                | $<4$            | ...               |
+--------------------------------------------------------------------------------------------+-------------------+--------------------+-----------------+-------------------+
| $M_\mathrm{gas}$ ($10^9~M_\odot$)                                                          | 3.1               | ...                | 8.9             | ...               |
+--------------------------------------------------------------------------------------------+-------------------+--------------------+-----------------+-------------------+
| $M_\mathrm{metal}$ ($10^6~M_\odot$)                                                        | $<16$             | ...                | $<33$           | ...               |
+--------------------------------------------------------------------------------------------+-------------------+--------------------+-----------------+-------------------+

: FIR properties of Himiko and CR7.

Table notes: We measure the \[C ii\] and dust properties using the spaxels above 3$\sigma$ levels. (cite: carniani18) and (cite: matthee17) have used the spaxels above 2$\sigma$ and 3$\sigma$ levels, respectively. Gas mass and metal mass are estimated from the \[C ii\]158$\ensuremath{\mu}m$ luminosity and metallicity using the conversion given in (cite: zanella18) and (cite: clark16) (see Section [5.6](#subsec:comparison)). All upper limits are given at the 3$\sigma$ levels.

# Discussion

## Origins of the multiple clumps

In Section [4.1](#subsec:morphology), we find multiple clumps of Himiko and CR7 using \[O iii\]$\lambda\lambda4959, 5007$ emission lines. In this section, we discuss the origin of the multiple clumps.

Figure [18](#fig:phase-space) shows the phase-space diagram (e.g., (cite: jaffe15)) of Himiko (top) and CR7 (bottom). Although such phase-space diagrams are typically used at the galaxy cluster scale, we adapt and apply the same approach to the halo of a single galaxy to investigate the kinematics and membership of its clumpy substructures. The horizontal axis is the projected distance from Himiko-C or CR7-B normalized to a virial radius $r_{200}$. The vertical axis is the absolute line-of-sight velocity normalized to the line-of-sight velocity dispersion $\sigma$. The line-of-sight velocities of Himiko and CR7 are estimated from the \[O iii\]$\lambda5007$ emission lines. The fiducial clumps are set to Himiko-C or CR7-B, located at the center along the velocity axis. If we set another clump as a fiducial value, the line-of-sight velocity and projected distance differ only by a factor of two, which does not change our following discussions. The virial mass $M_{200}$ is derived from the stellar-to-halo mass relation (SHMR) in (cite: behroozi19). We assume the stellar mass as the total stellar mass of the clumps in the system, resulting in $\log{(M_{200}/M_\odot)}=11.3$ ($11.4$) for Himiko (CR7). We estimate the virial radius $r_{200}$ from $M_{200}$ using the relation presented in (cite: mo02): $$\begin{equation}
    r_{200} = \left( \frac{GM_{200}}{100\Omega_m H_0^2} \right)^{1/3} (1 + z)^{-1}, 
\end{equation}$$ where $G$ is the gravitational constant. The virial radius $r_{200}$ of Himiko and CR7 is $\sim24~\mathrm{kpc}$. The line-of-sight velocity dispersion $\sigma$ is calculated using the virial theorem: $$\begin{equation}
    M_{200} = \frac{3}{2}\frac{r_{200} \sigma^2}{G}.  
\end{equation}$$ In Figure [18](#fig:phase-space), the black dashed line shows the escape velocity from a Navarro–Frenk–White (NFW; (cite: navarro96)) potential of the dark matter halo (see, (cite: jaffe15; rhee17)). The gray region indicates where the line-of-sight velocity is below the escape velocity, corresponding to the infalling region. The blue region represents the virialized area as indicated by (cite: rhee17) and (cite: yoon17). We find that all clumps are located either in the infalling or virialized regions, indicating that they will be in equilibrium or virialized within the dark matter halo. This result suggests that the clumps can possibly merge in the future.

We note some caveats when estimating halo mass. We choose the SHMR of (cite: behroozi19) because the model is calibrated to a broad set of observables at $0<z<10$, such as UV luminosity function and stellar mass function, providing consistency with the averaged galaxy population. When we choose another model, for example, (cite: moster13; moster18), the stellar to halo mass ratio is consistent with the (cite: behroozi19) relation. In addition, we need to be careful about the scatter of the SHMR. In (cite: behroozi19), the scatter of SHMR is $\sim0.3$ dex, but this scatter does not change our discussion. We also mention that Himiko and CR7 are merging systems, and it is difficult to estimate their exact halo profile. But still, we can roughly estimate the escape velocity (black dashed line in Figure [18](#fig:phase-space)) through a typical assumption of a dark matter halo profile. For example, Figure 2 of (cite: dutton14) shows the differences in the circular velocity depending on dark matter halo profiles. They indicate that the circular velocity does not largely change around $r=0.2r_{200}$, where Himiko and CR7 clumps are located. The threshold of the escape velocity in Figure [18](#fig:phase-space) (black dashed lines) remains similar, even when choosing other dark matter halo profiles.

It is interesting to compare these clumps with numerical simulations to check whether these systems can be observed in simulations. We use FirstLight simulations (cite: ceverino17), which are zoom-in cosmological simulations with maximum resolutions of 17-32 proper pc. The simulation has a box size of 60 comoving Mpc (cMpc). Following the clump-identification methods in (cite: nakazato24), we search for a clumpy galaxy with a total stellar mass of $\log{(M_*/M_\odot)}\sim9$ and SFR of $\mathrm{SFR}\sim30~M_\odot~\mathrm{yr^{-1}}$ at $z\sim6.5$, which are similar properties of Himiko and CR7. We successfully find an object similar to Himiko and CR7, named FL956. The FL956 track ($z=6.6$–$6.1$) in the phase space diagram is indicated in Figure [18](#fig:phase-space) by dash-dotted lines. The track shows that FL956 is experiencing a similar dynamical phase at $z\sim6.5$ to those of Himiko and CR7. Panels (a) and (b) of Figure [19](#fig:firstlight) show the gas density distribution and SFR surface density of FL956 at $z=6.69$ to $z=6.14$, respectively. At $z=7.0$, the system contains one central galaxy. At $z=6.69$, the counterpart galaxy enters the 10 kpc $\times$ 10 kpc region (left side of panel (a) in Figure [19](#fig:firstlight)) and experiences pericenter passage at $z=6.58$. The surrounding gas is perturbed, leading to the formation of new clumps in a tidal tail at $z=6.52$ (middle side of panel (a) in Figure [19](#fig:firstlight)). There are at least three clumps at $z=6.52$ within a $10~\mathrm{kpc}\times10~\mathrm{kpc}$ region, and the separation of each clump is a few kpc, which is also similar to CR7 and Himiko. The SFR surface density distribution aligns well with the gas density distribution.

Panel (c) of Figure [19](#fig:firstlight) displays the star formation history and stellar mass evolution of FL956 from $z=9.0$ to $z=5.3$. This system merges into one galaxy at $z\sim6.1$ (right side of panel (a) in Figure [19](#fig:firstlight)), and the total stellar mass (SFR) reaches $\log{(M_*/M_\odot)=9.6}$ ($65~M_\odot~\mathrm{yr^{-1}}$). The stellar mass in the system increases by approximately $1~\mathrm{dex}$ during the merging phase from $z=7$ to $z=6$ within just 170 Myr. The star formation rate rises at $z\sim6.6$, likely driven by merger-induced star formation. The trend of simulated star formation history is consistent with those of Himiko and CR7 derived from the SED fittings (Figure [11](#fig:sfh) and Section [4.2](#subsec:sed)). Additionally, the number density of the clumpy galaxy in the FirstLight simulation is broadly consistent with the number density of Himiko and CR7 observed by Subaru ($\sim10^{-5}$ cMpc$^{-3}$ to $10^{-6}$ cMpc$^{-3}$; (cite: ouchi09; sobral15)), further supporting the merger scenario (see Figures 7 and 8 of (cite: nakazato24)). These results support the claim that multiple components of Himiko and CR7 are attributed to merger systems (see also (cite: nakazato24) and (cite: harikane25) for the formation of clumpy galaxies through mergers). Also, given that each clump of Himiko and CR7 has comparable stellar mass (within 1:4; see Section [4.2](#subsec:sed)), Himiko and CR7 are experiencing major mergers.

We observe the \[O iii\]-detected clumps that are not detected in the NIRCam images (Himiko-D, Himiko-E, and CR7-D). The origins of these clumps are an interesting topic for further investigation. One possible explanation for these clumps is galaxy mergers. With gravitational interactions, the gas could be spatially distorted, forming tidal features, and the ionized gas clumps could be located near the stellar clumps (Himiko-A to Himiko-C and CR7-A to CR7-C). In panel (a) of Figure [19](#fig:firstlight), we find a complex spatial gas distribution in the snapshots, which could be observed as \[O iii\]-detected clumps like Himiko-D, Himiko-E, and CR7-D. Additionally, these clumps can also be explained by low-mass satellite galaxies, which fall into the same dark matter halo and will merge into one galaxy. In this case, small clumps also have stellar populations, but they are dark below the sensitivity limit of NIRCam. While galaxy mergers can explain these clumps, outflows from the stellar clumps are another plausible interpretation. Stellar- or AGN-driven winds could ionize the surrounding gas, making it visible as \[O iii\]-detected clumps that are undetectable in the NIRCam images. There is limited information on Himiko-D, Himiko-E, and CR7-D, as they are only detected through strong emission lines. Deep follow-up observations will be necessary to reveal the detailed physical conditions and origins of these clumps.

## Comparisons with JWST studies of clumpy galaxies

With JWST’s high spatial resolution, numerous clumpy galaxies at high redshift have recently been identified. Here we briefly place Himiko and CR7 in the context of recent JWST studies of clumpy substructure.

(cite: chen23) report multiple substructures in clumpy galaxies at $z=6$–$8$, with clump stellar masses $\log(M_*/M_\odot)=7$–$9$ on scales of several kpc, comparable to those inferred for Himiko and CR7. Their analysis is based solely on NIRCam imaging, and future IFU spectroscopy will provide dynamical information. (cite: claeyssens23), (cite: adamo24), and (cite: mowla24) examine gravitationally lensed systems at $z=1$–$10$. Thanks to the magnification, they probe intrinsically smaller clumps with $\log(M_*/M_\odot)=6$–$8$, below the clump masses of Himiko and CR7. (cite: fujimoto24_cosmicgrape) identify $>15$ clumps in one lensed galaxy at $z=6.072$ (Cosmic Grapes), with $\log(M_*/M_\odot)=6$–$8$ and effective radii of 10–60 pc. The moment-1 (velocity) map of the total system shows a clear gradient with Toomre $Q\sim0.2$–$0.3$ (i.e. $Q<1$), indicative of a gravitationally unstable rotating disk. From this result, they argue that these clumps form via disk instabilities rather than galaxy mergers. By contrast, Himiko and CR7 show no galaxy-wide, disk-like velocity gradient (Section [4.1](#subsec:morphology)), favoring a merger interpretation for their clumps (see also Section [5.1](#subsec:multiple-clumps)).

These studies place Himiko and CR7 at the high-mass clumps observed at high redshift, while gravitational lensing extends to intrinsically lower masses. Spatially resolved IFU kinematics for these targets reported in these studies will be decisive for understanding their dynamical structures.

## Illuminating sources

In Sections [4.2](#subsec:sed) and [4.4](#subsec:AGN), we discuss the recent star formation ($\sim10~\mathrm{Myr}$) in Himiko/CR7 and the AGN activity of Himiko-B. (cite: marconcini24b) have reported tentative evidence of AGN from the line diagnostics. These aspects are examined with the sources illuminating Himiko and CR7.

Recent star formation, particularly massive O- and B-type stars, emits stronger UV radiation than older stellar populations. The recent increase in the star formation rate likely contributes to the strong UV emission (Figure [11](#fig:sfh)). Under these conditions, these objects appear as bright UV sources. Additionally, Himiko-B shows a broad H$\alpha$ component, indicating AGN activity. CR7 shows the tentative evidence of AGNs (cite: marconcini24b). These AGNs also contribute to the UV-bright nature of Himiko and CR7. However, rest-frame UV images of Himiko and CR7 (Figure [1](#fig:NIRCam-cutout)) reveal spatially extended stellar components instead of a point source, suggesting that the extended UV emission is primarily dominated by stellar light, although we cannot rule out the possibility that UV emission in the central region originates from the AGN.

Finally, we briefly compare LAEs at $z=2$–$3$ with Himiko and CR7. While the physical conditions might not be the same owing to the redshift difference, this comparison provides insight into the properties of Himiko and CR7. (cite: sobral18b) have observed 21 luminous LAEs at $z=2$–$3$ with the William Herschel Telescope/ Intermediate dispersion Spectrograph and Imaging System, Keck/DEIMOS, and VLT/X-SHOOTER to study high ionization UV lines. They suggest that 60% of the sources show the AGN signatures, while others lacking AGN signatures (40%) are likely powered by low-metallicities and dust-poor unobscured starbursts. They also report that luminous LAEs of $M_\mathrm{UV}<-21.5$ at $z=2$–$3$ are all AGNs. In comparison, Himiko and CR7 ($M_\mathrm{UV}\sim-22$) appear consistent with this study, as they show unobscured starbursts, which may be triggered by galaxy mergers involving low-metallicity, dust-poor clumps.

## Origins of the extended Ly$\alpha$

A spatially extended Ly$\alpha$ emission is one of the most distinctive features of Himiko and CR7. In this subsection, we explore the physical origins of the extended Ly$\alpha$ emission based on our analysis. Using NIRSpec IFU data, we identified multiple clumps, at least five for Himiko and four for CR7. The broad components observed in the \[O iii\] emission suggest the presence of outflows or tidal features. The clumps in both Himiko and CR7 are involved in major mergers with small separations, indicating strong gravitational interactions among the clumps.

Several physical mechanisms are proposed to explain the extended Ly$\alpha$ emission: 1) the circumgalactic medium (CGM) scattering of Ly$\alpha$ photons produced by star-forming regions or AGNs, 2) the cold gas inflow (cold stream, gravitational cooling), 3) satellite galaxies, 4) Ly$\alpha$ fluorescence (photoionization by LyC radiation escaped from the host galaxy, generated by nearby objects, or by UV background) 5) galaxy mergers or shocks (e.g., (cite: dijkstra09; ouchi09; hayes11; ouchi13; yajima13; momose14; lake15; momose16; leclercq17; kusakabe19; herenz20; kimock21)). The observed features of Himiko and CR7 are all related to the spatially extended gas distributions. Simulations also suggest that gas around clumps is spatially extended in a merger phase (Panel (a) of Figure [19](#fig:firstlight)). Neutral hydrogen (H i) in such extended gas around the clumps scatters Ly$\alpha$ photons produced by young stars and AGNs in the clumps. The scattered light of Ly$\alpha$ photons by H i gas can be observed as the extended morphology. Our analysis results (multiple clumps, major mergers, outflows) are the direct evidence for such an extended gas distribution beyond clumps. Scenario 1) is closely related to our analysis results, and multiple clumps (potentially Himiko-D, Himiko-E, and CR7-D) might also contribute to Scenario 3). We cannot obtain direct evidence of scenario 2) from the data. However, given the fact that Himiko and CR7 have massive halos at $z\sim7$ ($\log{(M_{200}/M_\odot)}\sim11.3$) indicated by the stellar-to-halo mass relation (Section [5.1](#subsec:multiple-clumps)), we cannot exclude the cold gas inflow to their dark matter halos. The cold gas inflow might also contribute to the extended Ly$\alpha$ emission of Himiko and CR7. Given that Himiko-B has AGN, fluorescence (scenario 4) is also a possible mechanism (e.g., (cite: kimock21)).

As related to the scenario 5), some hydrodynamical simulations have suggested that a gas-rich galaxy merger is a key mechanism of the extended Ly$\alpha$ emission. (cite: yajima13) have conducted the hydrodynamical simulations and radiative transfer calculations for the binary gas-rich major merger system at $z=3$–$7$ with a halo mass range of $3$–$7\times10^{12}~M_\odot$, which are one order of magnitude higher halo mass than Himiko or CR7. They have found that shocked gas regions and star formation induced by gravitational interaction produce strong Ly$\alpha$ emission. The Ly$\alpha$ emission is extended due to the gas distribution with a luminosity of $L_\mathrm{Ly\alpha}\sim10^{43}$–$10^{44}~\mathrm{erg~s^{-1}}$ and a size of $\sim10$–$20$ kpc at $z>6$. These results also support the physical origin of the extended Ly$\alpha$ that can be explained by galaxy mergers like Himiko and CR7.

To further characterize merger galaxies with extended Ly$\alpha$ emission, such as Himiko and CR7, we investigate Himiko-type objects in the FOREVER22 simulation (cite: yajima22; yajima23). FOREVER22 is a zoom-in cosmological hydrodynamics simulation of protocluster regions with a volume of (28.6 cMpc)$^3$ and an initial gas particle mass of $2.9\times10^6~M_\odot~h^{-1}$. (cite: yajima22) carry out post-processing radiative transfer calculations, including Ly$\alpha$ emission, using the ART$^2$ code (cite: li08; li20a; yajima12c).

We search for a galaxy with properties similar to those of Himiko and CR7 ($z\sim7$, $M_*\sim10^9~M_\odot$, clumpy morphology) in protocluster region 0 (PCR0) of the simulation and find a similar object named PCR0-ID32 at $z=6.8$. The left panel of Figure [20](#fig:Lya-simulation) shows the stellar distribution of PCR0-ID32 at $z=6.8$. The simulated map is smoothed with a Gaussian kernel to match the spatial resolution of NIRCam F444W ($0.16\ensuremath{''}$), and the pixel scale is matched to that of Himiko’s NIRCam image ($0.04\ensuremath{''}$; Figure [1](#fig:NIRCam-cutout)). By observing down to about one third of the JWST’s observational limit measured with the Himiko data ($M_*\sim10^6~M_\odot\mathrm{/pixel}$ or $M_*\sim10^{7.3}~M_\odot\mathrm{\,kpc^{-2}}$), we can detect three clumps of PCR0-ID32 within $\sim10~\mathrm{kpc}\times10~\mathrm{kpc}$.

In Figure [18](#fig:phase-space), we plot the PCR0-ID32 track from $z=6.8$ to $z=6.3$. We find that PCR0-ID32 at $z\sim6.6$ is in a region comparable to Himiko or CR7, indicating that it shares a similar dynamical merger phase. The middle and right panels of Figure [20](#fig:Lya-simulation) show Ly$\alpha$ surface brightness (SB) of PCR0-ID32 with dust-free and dust, respectively. The Ly$\alpha$ SB map is smoothed with a Gaussian kernel to match the spatial resolution of Subaru NB921 ($0.75\ensuremath{''}$). The surface brightness limit of Subaru NB921 is $\sim10^{-18}$ erg s$^{-1}$ cm$^{-2}$ arcsec$^{-2}$, and only the color map above this limit is shown. The dust-free model shows extended Ly$\alpha$ emission ($\sim 10~\mathrm{kpc}$ scale), which coincides with the stellar distribution (middle panel of Figure [20](#fig:Lya-simulation)). The Ly$\alpha$ luminosity of the object is $1.2\times10^{43}$ erg s$^{-1}$, which is consistent with Himiko and CR7. This result shows that Himiko-type objects with extended Ly$\alpha$ emission exist in the simulation. In contrast, with dust extinction and obscuration (right panel of Figure [20](#fig:Lya-simulation)), the Ly$\alpha$ emission is detected only at the PSF scale, comparable to the Subaru NB921 PSF. In that case, the Ly$\alpha$ luminosity is $7.4\times10^{41}$ erg s$^{-1}$, which is lower than those of Himiko and CR7. These results suggest that stellar/gas distributions due to mergers and the presence or absence of dust play key roles in extended Ly$\alpha$ emission (see also (cite: witten24)). It is possible that the dust in Himiko and CR7 has not yet grown sufficiently and/or has undergone efficient destruction processes, such as those caused by supernovae (e.g., sputtering by supernova shock waves). This could result in a high escape fraction, and the low dust content is consistent with the non-detection of their dust continuum in ALMA observations (see also (cite: hirashita14)). Alternatively, other ionizing sources (e.g., hidden AGN) could also enhance the Ly$\alpha$ emission of Himiko and CR7, which are related to scenarios 1) and 4).

## Physical interpretations of the \[CII\] offset

In Section [4.1](#subsec:morphology) and Figure [3](#fig:jwst-alma-subaru-image), we find that Himiko has the spatial offset between UV, H$\alpha$ (Himiko-A, -B) and \[C ii\], Ly$\alpha$ beyond the astrometric uncertainty. We discuss the physical origins of the offset (see e.g., (cite: carniani20)). The possible origins of the offset are 1) the photodissociation region (cite: hollenbach99) between Himiko-A and -B, and 2) shock heating by galaxy mergers. In scenario 1), ionizing photons caused by the star formation in Himiko-A, Himiko-B, and AGN activity of Himiko-B are the possible illuminating sources discussed in Section [5.3](#subsec:illuminating-source). For scenario 2), gravitational interactions cause the shock heating, thus \[C ii\] can be emitted in a region between Himiko-A and -B. Some local merging galaxies tend to have a large \[C ii\] luminosity caused by shock heating. For example, (cite: appleton13) have reported the \[C ii\] emission from the shocked intergalactic filament in Stephan’s Quintet (see also (cite: umehata21) for the Ly$\alpha$ blob at $z=3.1$ case). Considering that Himiko is the merger system, shock heating can be a possible scenario to explain the offset. The presence of such gas beyond the stellar clumps can lead to resonant scattering of Ly$\alpha$ photons, thereby producing the observed extended Ly$\alpha$ emission (Section [5.4](#subsec:extended-Lya)).

It is also worth noting that the beam size of ALMA ($\sim0.9\ensuremath{''}$) is larger than JWST/NIRCam and NIRSpec IFU ($\sim0.1\ensuremath{''}$–$0.2\ensuremath{''}$). We can not exclude the possibility that the \[C ii\] emission from Himiko-A and Himiko-B can contribute to the total \[C ii\] emission, which has the offset from each clump. As a test, we examine the smoothed F115W image of Himiko, matched to the PSF size of Subaru or ALMA. We find that the peak flux position remains at Himiko-A, preferring that the \[C ii\] and Ly$\alpha$ offset in Himiko is not due to the lower angular resolution. Additional high-resolution ALMA data are necessary to comprehend the \[C ii\] distribution of Himiko, which will also enable us to explore the \[C ii\] kinematics.

## Comparisons with other merger systems: ‘blue mergers’ and ‘red mergers’

This section compares these unique triple merger systems with other galaxy populations. This comparison provides valuable insight into whether they share similarities with other galaxy populations. We focus on the dust, metal, and gas mass content of Himiko and CR7.

We finally compare Himiko and CR7 with the dusty merger systems, including SMGs (see also Section [4.5](#subsec:cii_LIR)). SMGs trace heavily obscured, short-lived starburst phases with high SFRs ($10^2$–$10^3$ $M_\odot\,\mathrm{yr^{-1}}$) and large dust/gas reservoirs (e.g.,(cite: casey14)). Their properties and number densities suggest that a subset evolves into massive quiescent/early-type galaxies at later times (e.g., (cite: hopkins08; toft14; dudzevivciute20)). Comparisons with these distinct populations highlight the diversity in the merger phase at high redshift and provide valuable insights for a deeper understanding of both Himiko/CR7 and dusty star-forming galaxies. In addition, the comparison highlights the mechanisms of the extended Ly$\alpha$ emission.

The left (right) panel of Figure [21](#fig:DTG-DTM) shows the relation between the dust mass-to-gas mass ratio (DTG) and metallicity (dust mass-to-metal mass ratio; DTM). Himiko and CR7 are colored red. Damped Ly$\alpha$ system (DLA; (cite: peroux20)), local galaxies (dustpedia; (cite: devis19; casasola20)), and submillimeter galaxies at $z\sim2$ whose metallicities are estimated by N2 (\[N ii\]$\lambda6584$/H$\alpha$) index ((cite: shapley20)) are plotted in blue, gray, and magenta, respectively.

We calculate the dust masses of Himiko and CR7 using the following formula: $$\begin{equation}
    M_\mathrm{dust} = \frac{D_\mathrm{L}^2 S_{\nu, \mathrm{obs}}}{(1+z) \kappa_\mathrm{d}(\nu_\mathrm{rest}) [B_\nu(T_\mathrm{dust})-B_\nu(T_\mathrm{CMB}(z))]}, 
\end{equation}$$ where $D_\mathrm{L}$ is the luminosity distance, $S_{\nu, \mathrm{obs}}$ is the observed flux, $\kappa_\mathrm{d}(\nu_\mathrm{rest})$ is the rest-frame dust mass absorption coefficient, and $B_\nu(T_{\mathrm{dust}})$ is the Planck function at a rest-frame frequency $\nu_\mathrm{rest}$ and dust temperature $T_\mathrm{dust}$. In this equation, $B_\nu(T_\mathrm{CMB}(z))$ is used to correct for the cosmic microwave background (CMB) effects (e.g., (cite: ota14)). We assume $\kappa_\mathrm{d}(\nu_\mathrm{rest})=0.77(850~\mathrm{\ensuremath{\mu}m}/\lambda_\mathrm{rest})^{\beta_\mathrm{IR}}~\mathrm{cm^2~g^{-1}}$ (cite: dunne00) with the rest-frame wavelength of $\lambda_\mathrm{rest}=158~\mathrm{\ensuremath{\mu}m}$. We use the 3$\sigma$ upper limit of the dust continuum of Himiko (CR7) and obtain a dust mass upper limit of $9\times10^6~M_\odot$ ($5\times10^6~M_\odot$), assuming $\beta_\mathrm{IR}=1.5$ and $T_\mathrm{dust}=40~\mathrm{K}$ (Table [5](#tab:ALMA-measurement)).

The gas mass estimate has a large uncertainty, but the most promising way to obtain the gas mass at $z\gtrsim6$ is to use a cold neutral gas tracer \[C ii\]158$\ensuremath{\mu}m$. We generally follow the estimation procedures outlined in (cite: algera25) (see also (cite: palla24)). The molecular H$_2$ gas mass $M_\mathrm{H_2}$ is estimated using the following relation presented in (cite: zanella18): $$\begin{equation}
    \log{\left( \frac{L_\mathrm{[\textsc{C\,ii}]}}{L_\odot} \right)} = -1.28 + 0.98\log{\left( \frac{M_\mathrm{H_2}}{M_\odot} \right)}, 
\end{equation}$$ where, $M_\mathrm{H_2}$ and $L_\mathrm{[\textsc{C\,ii}]}$ are in the units of $M_\odot$ and $L_\odot$, respectively. We can use the $L_\mathrm{[\textsc{C\,ii}]}/L_\odot$ taken from the ALMA observations. Finally, the total gas mass ($M_\mathrm{gas}$) is obtained by following the relation presented in (cite: devis19): $M_\mathrm{gas} = \xi (M_\mathrm{HI} + M_\mathrm{H_2})$, where $\xi$ is a correction factor ($\sim1.3$–$1.4$) depending on the metallicity and $M_\mathrm{HI}$ is the atomic H i gas mass. We follow (cite: clark16) and define $\xi$ as $$\begin{equation}
    \xi = \frac{1}{1-\left(f_\mathrm{He_p} + f_Z [\frac{\Delta f_\mathrm{He_p}}{\Delta Z}] \right) - f_Z},
\end{equation}$$ where $f_\mathrm{He_p}$ is the primordial Helium mass fraction of 0.2485 (cite: aver11), $f_Z = Z  \times f_{Z_{\odot}}$ is the fraction by mass using $f_Z=27.36 \times 10^{(12+\log{(\mathrm{O/H)}} -12)}$. The factor of 27.36 comes from the assumption of $12+\log{(\mathrm{O/H})_\odot}=8.69$ and a solar metal mass fraction of 0.0134 (cite: asplund09). Here, $\Delta f_\mathrm{He_p}/\Delta Z=1.41$ (cite: balser06) is the metallicity-dependent evolution of the helium mass fraction. Depending on the metallicity, $\xi$ varies from 1.33 (zero metallicity) to 1.39 (solar metallicity). In this paper, we ignore atmic H i gas mass because the atomic gas mass estimate has large uncertainties and \[C ii\]-to-$\mathrm{H_2}$ calibration might already trace the full gas content in galaxies at the epoch of reionization (see detailed discussions in (cite: algera25)). We note that the estimate of molecular gas mass also has uncertainty ($\sim0.3$ dex; see also (cite: palla24; devis19)), but subsequent discussions and observed trends remain valid. Using the gas mass, we can also estimate the metal mass ($M_\mathrm{metal}$) of Himiko and CR7 following the relation (cite: devis19): $$\begin{equation}
    M_\mathrm{metal}= f_Z \times M_\mathrm{gas} + M_\mathrm{dust}. 
\end{equation}$$ The gas and metal mass of Himiko and CR7 are summarized in Table [5](#tab:ALMA-measurement).

Himiko and CR7 only have the upper limit of dust mass, so we can only show the upper limit of DTG and DTM in Figure [21](#fig:DTG-DTM). The DTG and DTM upper limits of Himiko and CR7 are consistent with the DLA samples that have similar metallicities, indicating that Himiko and CR7 are mainly in the sequence of stellar mass or dust mass-metallicity relation (see also mass-metallicity relation of Figure [13](#fig:line_ratio)). However, it is important to note that Himiko and CR7 might still have lower DTG or DTM than other galaxy populations. We need deeper dust continuum observations aimed at Himiko and CR7 to constrain these properties.

Figure [22](#fig:Mdust_Mstar) shows the relation between the dust and the stellar mass. Himiko and CR7 are indicated in red-filled plots. We also present a compilation of UV bright ($M_\mathrm{UV}\lesssim-21.5$) and clumpy galaxies at $z\sim7$ with open-red symbols (e.g., (cite: bowler18; inami22)). As a comparison, we display submillimeter galaxies: ALESS (cite: dacunha15), HUDF (cite: dunlop17), SPT0311-58 at $z=6.9$ (cite: marrone18), HFLS3 at $z=6.3$ (cite: riechers13) with magenta plots (see also Figure [17](#fig:CII_IRluminosity)). Similarly, dusty merger systems at $z\sim5$–$7$ (e.g., (cite: villanueva24; jones20; knudsen17; hashimoto19)) are shown in black filled plots. The gray belt shows the local galaxy samples (cite: bourne12). The JWST CEERS samples ($4<z<11$; (cite: burgarella24)) are shown by the black open circles.

Himiko and CR7 are consistent with other UV-bright and clumpy galaxies at $z\sim7$, suggesting that these sources might have dust properties similar to those of Himiko and CR7. Compared to dusty merger systems at $z\sim5$–$7$, Himiko and CR7 have lower dust mass, even in a similar stellar mass range. This trend can be explained by the difference in their SFR and merger phase. For example, B14-65666 at $z=7.15$ has $\mathrm{SFR\sim200}~M_\odot~\mathrm{yr^{-1}}$ ((cite: hashimoto19; jones24b; sugahara25)), which is more than five times higher than that of Himiko or CR7. The star formation history from our simulation shows that Himiko-like objects are experiencing early-phase mergers because their SFR is still lower ($\sim30~M_\odot~\mathrm{yr^{-1}}$) than the peak SFR ($\sim80~M_\odot~\mathrm{yr^{-1}}$) at $z\sim5.4$ (Figure [19](#fig:firstlight)). The dust construction of Himiko and CR7 might still be ongoing, and the dust mass remains small compared to the other dusty merger systems.

Himiko-type objects (UV-bright, clumpy galaxies) contrast sharply with dusty mergers, including some SMGs. Previous observations have revealed that some SMGs are merging galaxies with distorted morphologies (e.g., (cite: tacconi08)), while some others are experiencing disk instability (e.g., (cite: tadaki18)). Himiko-type objects are metal-poor ($Z\sim0.1$–$0.2Z_\odot$), dust-poor ($M_\mathrm{dust}\lesssim9\times10^6~M_\odot$), and low-mass ($M_*\sim10^9~M_\odot$), while dusty mergers are metal-rich ($Z\sim Z_\odot$), dust-rich ($M_\mathrm{dust}\gtrsim10^8~M_\odot$), and massive ($M_*\gtrsim10^{10}~M_*$), aligning with the mass-metallicity and dust-mass-metallicity relations. Himiko-type objects show self-similar properties in both stellar mass and dust mass compared to SMGs. Himiko-type objects appear as ‘blue mergers’, whereas dusty mergers, heavily affected by dust extinction, appear as ‘red mergers’. Interestingly, we now have two blue mergers, Himiko and CR7, showing spatially extended Ly$\alpha$ emission. Furthermore, in Figure [22](#fig:Mdust_Mstar), COS-2987030247 is also a clumpy merger galaxy at $z=6.8$ (cite: harikane25). COS-2987030247 has been detected in Ly$\alpha$ emission with VLT/X-SHOOTER (cite: laporte17)[^8], although with limited spatial information. Some other UV bright ($M_{\mathrm{UV}}\sim-21.5$) and clumpy merger galaxies reported in (cite: harikane25) are also detected in Ly$\alpha$ (e.g., COS-788571 at $z=6.9$, COS-1009842 at $z=6.8$; (cite: endsley21)). These samples indicate that the ‘blue mergers’ with extended gas distributions triggered by mergers are important physical mechanisms for emitting extended Ly$\alpha$ emission, which is also suggested from the FOREVER22 simulation described in Section [5.4](#subsec:extended-Lya). Their low dust content allows Ly$\alpha$ photons to escape easily. In contrast, although the ‘red merger’ population can also exhibit extended gas distributions due to gravitational interactions, their high dust content prevents Ly$\alpha$ photons from escaping, making extended Ly$\alpha$ emission difficult to observe.

# Summary and conclusions

We investigate the two bright extended Ly$\alpha$ objects, Himiko and CR7, at $z=6.6$ using publicly available JWST/NIRCam photometry, NIRSpec IFU spectroscopy, ALMA Band 6, and Subaru NB921 data. We also incorporate cosmological simulations, providing information on the connection between galaxy mergers and extended Ly$\alpha$ emission. Our findings and discussions are summarized as follows:

1.  Himiko (CR7) is composed of at least five (four) clumps with separations of 2.4–7.3 kpc found by the \[O iii\]$\lambda\lambda4959, 5007$ emission lines in the JWST NIRSpec IFU data. Individual clumps have small velocity offsets with $\Delta v\lesssim 220~\mathrm{km~s^{-1}}$. The stellar masses of Himiko (CR7) estimated by the SED fitting using the NIRCam photometry range in $\log{(M_*/M_\odot)}=8.4$–$9.0$ ($8.3$–$8.8$). Because of the small velocity offsets and equal stellar masses, Himiko and CR7 are major merger systems, which is also suggested by the FirstLight simulations.

2.  The star formation histories of Himiko and CR7, derived from the SED fitting using NIRCam photometry, indicate an increasing trend over the past $\sim 10~\mathrm{Myr}$. These starbursts may be triggered by mergers and are connected to the UV-bright nature of both Himiko and CR7.

3.  The spatial distributions of UV and H$\alpha$ or \[C ii\]$158\mu\mathrm{m}$ and Ly$\alpha$ align well in Himiko and CR7. Between Himiko-A and B, there is a spatial offset between UV, H$\alpha$, and \[C ii\], Ly$\alpha$($\sim0.3\ensuremath{''}$), suggesting that the distribution of neutral gas does not coincide with that of ionized gas or stellar clumps in the merging phase. However, there is no significant offset in CR7.

4.  $\lambda\lambda4959, 5007$ emission lines of Himiko-C and CR7-A show broad components ($\mathrm{FWHM}\sim250$–$400~\mathrm{km~s^{-1}}$) that can be explained by outflows or tidal features. This signature is related to the spatially extended gas distribution that can be related to the extended Ly$\alpha$ emission of Himiko and CR7.

5.  Himiko-B shows the broad H$\alpha$ emission line ($\mathrm{FWHM}\sim1000~\mathrm{km\,s^{-1}}$). This broad component is not observed in the forbidden \[O iii\]$\lambda5007$ emission line of Himiko-B, indicating AGN activity with a low-mass black hole of $M_\mathrm{BH}\sim10^{6.6}~M_\odot$. In the $M_\mathrm{BH}$–$M_*$ plane, Himiko-B is located in the higher black hole mass region than those of local galaxies, which is similar to the recent JWST AGN samples. The AGN could also contribute to the bright UV emission from Himiko.

6.  Himiko and CR7 are not detected in 1 mm dust continuum in the ALMA Band 6 observations with $3\sigma$ upper limits of $S_{\mathrm{158~\ensuremath{\mu}m}}<31~\mu\mathrm{Jy}$ and $S_{\mathrm{158~\ensuremath{\mu}m}}<19~\mu\mathrm{Jy}$, respectively. From these upper limits, we can derive the dust mass upper limits of $M_{\mathrm{dust}}\lesssim9\times10^6~M_\odot$ and $M_{\mathrm{dust}}\lesssim5\times10^6~M_\odot$ for Himiko and CR7, respectively. This result indicates that Himiko and CR7 are dust-poor systems.

7.  We interpret high-redshift galaxy merger systems with two classifications: ‘blue mergers’ and ‘red mergers.’ Blue mergers, such as Himiko and CR7, are characterized by low stellar mass, low dust mass, and low metallicity. In contrast, red mergers represent the opposite population, including dusty mergers and some submillimeter galaxies. Blue mergers show self-similarity in stellar mass and dust mass compared to red mergers and are one of the key mechanisms for explaining the extended Ly$\alpha$ emission, like Himiko and CR7.

# acknowledgments

We thank the anonymous referee for careful reading and valuable comments that improved our manuscript. We thank Rychard Bouwens, Rebecca A. A. Bowler, Takuya Hashimoto, Jacqueline Hodge, Ryota Ikeda, Yuta Kageura, Kentaro Nagamine, Takayuki Saito, Yoichi Tamura, Daisuke Toyouchi, Takafumi Tsukui, Hideki Umehata, Joris Witstok, and Jorge A. Zavala for the valuable comments and discussions. We are grateful to the ALMA Help Desk for calibrating the Cycle 1 archival data and for answering our questions.

This work is based in part on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with programs GTO-1215, GTO-1217 (GA-NIFS), GO-1727 (COSMOS-Web), and GO-1837 (PRIMER). The authors acknowledge the GA-NIFS, COSMOS-Web, and PRIMER teams led by Santiago Arribas & Roberto Maiolino, Jeyhan Kartaltepe & Caitlin M. Casey, and James S. Dunlop, respectively, for developing their observation programs. The authors also acknowledge the TEMPLATE team led by Jane R. Rigby for establishing the JWST/NIRSpec IFU reduction procedures. The JWST/NIRSpec IFU data presented in this article were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute. The specific observations analyzed can be accessed via .

Some of the data products presented herein were retrieved from the Dawn JWST Archive (DJA). DJA is an initiative of the Cosmic Dawn Center (DAWN), which is funded by the Danish National Research Foundation under grant DNRF140.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00115.S, #2012.1.00033.S, and #2015.1.00122.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

The Hyper Suprime-Cam (HSC) collaboration includes the astronomical communities of Japan and Taiwan, and Princeton University. The HSC instrumentation and software were developed by the National Astronomical Observatory of Japan (NAOJ), the Kavli Institute for the Physics and Mathematics of the Universe (Kavli IPMU), the University of Tokyo, the High Energy Accelerator Research Organization (KEK), the Academia Sinica Institute for Astronomy and Astrophysics in Taiwan (ASIAA), and Princeton University. Funding was contributed by the FIRST program from the Japanese Cabinet Office, the Ministry of Education, Culture, Sports, Science and Technology (MEXT), the Japan Society for the Promotion of Science (JSPS), Japan Science and Technology Agency (JST), the Toray Science Foundation, NAOJ, Kavli IPMU, KEK, ASIAA, and Princeton University.

This paper makes use of software developed for Vera C. Rubin Observatory. We thank the Rubin Observatory for making their code available as free software at <http://pipelines.lsst.io/>.

This paper is based on data collected at the Subaru Telescope and retrieved from the HSC data archive system, which is operated by the Subaru Telescope and Astronomy Data Center (ADC) at NAOJ. Data analysis was in part carried out with the cooperation of Center for Computational Astrophysics (CfCA), NAOJ. We are honored and grateful for the opportunity of observing the Universe from Maunakea, which has the cultural, historical and natural significance in Hawaii.

The Pan-STARRS1 Surveys (PS1) and the PS1 public science archive have been made possible through contributions by the Institute for Astronomy, the University of Hawaii, the Pan-STARRS Project Office, the Max Planck Society and its participating institutes, the Max Planck Institute for Astronomy, Heidelberg, and the Max Planck Institute for Extraterrestrial Physics, Garching, The Johns Hopkins University, Durham University, the University of Edinburgh, the Queen’s University Belfast, the Harvard-Smithsonian Center for Astrophysics, the Las Cumbres Observatory Global Telescope Network Incorporated, the National Central University of Taiwan, the Space Telescope Science Institute, the National Aeronautics and Space Administration under grant No. NNX08AR22G issued through the Planetary Science Division of the NASA Science Mission Directorate, the National Science Foundation grant No. AST-1238877, the University of Maryland, Eotvos Lorand University (ELTE), the Los Alamos National Laboratory, and the Gordon and Betty Moore Foundation.

This publication is based upon work supported by the World Premier International Research Center Initiative (WPI Initiative), MEXT, Japan, KAKENHI (20H00180, 23KJ2148, 21H04489, 22H04939, 23K20035, 24H00004, 23KJ0728) through the Japan Society for the Promotion of Science, and JST FOREST Program (JP-MJFR202Z). This work was supported by the joint research program of the Institute for Cosmic Ray Research (ICRR), University of Tokyo. Numerical analyses of FirstLight simulations were carried out on the analysis servers at the Center for Computational Astrophysics, National Astronomical Observatory of Japan. The English writing in this paper was improved with ChatGPT and Grammarly, while no sentences were generated by these softwares from scratch.

# Facilities

JWST (NIRSpec, NIRCam), ALMA (Band 6), Subaru (Hyper Suprime-Cam)

# Software

Astropy (cite: astropy:2013; astropy:2018; astropy:2022), CASA (cite: casa22), Matplotlib (cite: hunter07), NumPy (cite: harris20), pandas (cite: mckinney2010data) Prospector (cite: leja17; johnson21), PyNeb (cite: luridiana15), SciPy (cite: virtanen20), SEP (cite: barbary16),

natexlab

(ref: adamo24) Adamo, A., Bradley, L. D., Vanzella, E., et al. 2024, Nature, 632, 513, doi: [`10.1038/s41586-024-07703-7`](http://doi.org/10.1038/s41586-024-07703-7)

(ref: ahumada20) Ahumada, R., Allende Prieto, C., Almeida, A., et al. 2020, ApJS, 249, 3, doi: [`10.3847/1538-4365/ab929e`](http://doi.org/10.3847/1538-4365/ab929e)

(ref: aihara18a) Aihara, H., Arimoto, N., Armstrong, R., et al. 2018a, PASJ, 70, S4, doi: [`10.1093/pasj/psx066`](http://doi.org/10.1093/pasj/psx066)

(ref: aihara18b) Aihara, H., Armstrong, R., Bickerton, S., et al. 2018b, PASJ, 70, S8, doi: [`10.1093/pasj/psx081`](http://doi.org/10.1093/pasj/psx081)

(ref: aihara19) Aihara, H., AlSayyad, Y., Ando, M., et al. 2019, PASJ, 71, 114, doi: [`10.1093/pasj/psz103`](http://doi.org/10.1093/pasj/psz103)

(ref: aihara22) —. 2022, PASJ, 74, 247, doi: [`10.1093/pasj/psab122`](http://doi.org/10.1093/pasj/psab122)

(ref: akaike74) Akaike, H. 1974, IEEE Transactions on Automatic Control, 19, 716

(ref: algera25) Algera, H., Rowland, L., Stefanon, M., et al. 2025, arXiv e-prints, arXiv:2501.10508, doi: [`10.48550/arXiv.2501.10508`](http://doi.org/10.48550/arXiv.2501.10508)

(ref: andrews13) Andrews, B. H., & Martini, P. 2013, ApJ, 765, 140, doi: [`10.1088/0004-637X/765/2/140`](http://doi.org/10.1088/0004-637X/765/2/140)

(ref: appleton13) Appleton, P. N., Guillard, P., Boulanger, F., et al. 2013, ApJ, 777, 66, doi: [`10.1088/0004-637X/777/1/66`](http://doi.org/10.1088/0004-637X/777/1/66)

(ref: arribas24) Arribas, S., Perna, M., Rodrı́guez Del Pino, B., et al. 2024, A&A, 688, A146, doi: [`10.1051/0004-6361/202348824`](http://doi.org/10.1051/0004-6361/202348824)

(ref: asada24) Asada, Y., Sawicki, M., Abraham, R., et al. 2024, MNRAS, 527, 11372, doi: [`10.1093/mnras/stad3902`](http://doi.org/10.1093/mnras/stad3902)

(ref: asplund09) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481, doi: [`10.1146/annurev.astro.46.060407.145222`](http://doi.org/10.1146/annurev.astro.46.060407.145222)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: astropy:2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: aver11) Aver, E., Olive, K. A., & Skillman, E. D. 2011, JCAP, 2011, 043, doi: [`10.1088/1475-7516/2011/03/043`](http://doi.org/10.1088/1475-7516/2011/03/043)

(ref: baldwin81) Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5, doi: [`10.1086/130766`](http://doi.org/10.1086/130766)

(ref: balser06) Balser, D. S. 2006, AJ, 132, 2326, doi: [`10.1086/508515`](http://doi.org/10.1086/508515)

(ref: barbary16) Barbary, K. 2016, Journal of Open Source Software, 1, 58, doi: [`10.21105/joss.00058`](http://doi.org/10.21105/joss.00058)

(ref: behroozi19) Behroozi, P., Wechsler, R. H., Hearin, A. P., & Conroy, C. 2019, MNRAS, 488, 3143, doi: [`10.1093/mnras/stz1182`](http://doi.org/10.1093/mnras/stz1182)

(ref: bertin96) Bertin, E., & Arnouts, S. 1996, A&AS, 117, 393, doi: [`10.1051/aas:1996164`](http://doi.org/10.1051/aas:1996164)

(ref: blain93) Blain, A. W., & Longair, M. S. 1993, MNRAS, 264, 509, doi: [`10.1093/mnras/264.2.509`](http://doi.org/10.1093/mnras/264.2.509)

(ref: blain02) Blain, A. W., Smail, I., Ivison, R. J., Kneib, J. P., & Frayer, D. T. 2002, Phys. Rep., 369, 111, doi: [`10.1016/S0370-1573(02)00134-5`](http://doi.org/10.1016/S0370-1573(02)00134-5)

(ref: boker22) Böker, T., Arribas, S., Lützgendorf, N., et al. 2022, A&A, 661, A82, doi: [`10.1051/0004-6361/202142589`](http://doi.org/10.1051/0004-6361/202142589)

(ref: bourne12) Bourne, N., Maddox, S. J., Dunne, L., et al. 2012, MNRAS, 421, 3027, doi: [`10.1111/j.1365-2966.2012.20528.x`](http://doi.org/10.1111/j.1365-2966.2012.20528.x)

(ref: bouwens15) Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2015, ApJ, 803, 34, doi: [`10.1088/0004-637X/803/1/34`](http://doi.org/10.1088/0004-637X/803/1/34)

(ref: bouwens22) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931, 160, doi: [`10.3847/1538-4357/ac5a4a`](http://doi.org/10.3847/1538-4357/ac5a4a)

(ref: bowler18) Bowler, R. A. A., Bourne, N., Dunlop, J. S., McLure, R. J., & McLeod, D. J. 2018, MNRAS, 481, 1631, doi: [`10.1093/mnras/sty2368`](http://doi.org/10.1093/mnras/sty2368)

(ref: bowler17a) Bowler, R. A. A., Dunlop, J. S., McLure, R. J., & McLeod, D. J. 2017a, MNRAS, 466, 3612, doi: [`10.1093/mnras/stw3296`](http://doi.org/10.1093/mnras/stw3296)

(ref: bowler17b) Bowler, R. A. A., McLure, R. J., Dunlop, J. S., et al. 2017b, MNRAS, 469, 448, doi: [`10.1093/mnras/stx839`](http://doi.org/10.1093/mnras/stx839)

(ref: larry_bradley_2024_13989456) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2024, astropy/photutils: 2.0.2, 2.0.2, Zenodo, doi: [`10.5281/zenodo.13989456`](http://doi.org/10.5281/zenodo.13989456)

(ref: brammer23) Brammer, G. 2023, grizli, 1.9.11, Zenodo, doi: [`10.5281/zenodo.8370018`](http://doi.org/10.5281/zenodo.8370018)

(ref: burgarella24) Burgarella, D., Buat, V., Theulé, P., et al. 2024, arXiv e-prints, arXiv:2410.23959, doi: [`10.48550/arXiv.2410.23959`](http://doi.org/10.48550/arXiv.2410.23959)

(ref: bushouse_2024_10870758) Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2024, JWST Calibration Pipeline, 1.14.0, Zenodo, doi: [`10.5281/zenodo.10870758`](http://doi.org/10.5281/zenodo.10870758)

(ref: byler17) Byler, N., Dalcanton, J. J., Conroy, C., & Johnson, B. D. 2017, ApJ, 840, 44, doi: [`10.3847/1538-4357/aa6c66`](http://doi.org/10.3847/1538-4357/aa6c66)

(ref: calzetti00) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: cameron23) Cameron, A. J., Saxena, A., Bunker, A. J., et al. 2023, A&A, 677, A115, doi: [`10.1051/0004-6361/202346107`](http://doi.org/10.1051/0004-6361/202346107)

(ref: cantalupo14) Cantalupo, S., Arrigoni-Battaia, F., Prochaska, J. X., Hennawi, J. F., & Madau, P. 2014, Nature, 506, 63, doi: [`10.1038/nature12898`](http://doi.org/10.1038/nature12898)

(ref: capak15) Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455, doi: [`10.1038/nature14500`](http://doi.org/10.1038/nature14500)

(ref: carilli13) Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105, doi: [`10.1146/annurev-astro-082812-140953`](http://doi.org/10.1146/annurev-astro-082812-140953)

(ref: carniani18) Carniani, S., Maiolino, R., Smit, R., & Amorı́n, R. 2018, ApJL, 854, L7, doi: [`10.3847/2041-8213/aaab45`](http://doi.org/10.3847/2041-8213/aaab45)

(ref: carniani20) Carniani, S., Ferrara, A., Maiolino, R., et al. 2020, MNRAS, 499, 5136, doi: [`10.1093/mnras/staa3178`](http://doi.org/10.1093/mnras/staa3178)

(ref: casa22) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: casasola20) Casasola, V., Bianchi, S., De Vis, P., et al. 2020, A&A, 633, A100, doi: [`10.1051/0004-6361/201936665`](http://doi.org/10.1051/0004-6361/201936665)

(ref: casey14) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45, doi: [`10.1016/j.physrep.2014.02.009`](http://doi.org/10.1016/j.physrep.2014.02.009)

(ref: casey23) Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023, ApJ, 954, 31, doi: [`10.3847/1538-4357/acc2bc`](http://doi.org/10.3847/1538-4357/acc2bc)

(ref: ceverino17) Ceverino, D., Glover, S. C. O., & Klessen, R. S. 2017, MNRAS, 470, 2791, doi: [`10.1093/mnras/stx1386`](http://doi.org/10.1093/mnras/stx1386)

(ref: chabrier03) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: chen23) Chen, Z., Stark, D. P., Endsley, R., et al. 2023, MNRAS, 518, 5607, doi: [`10.1093/mnras/stac3476`](http://doi.org/10.1093/mnras/stac3476)

(ref: claeyssens23) Claeyssens, A., Adamo, A., Richard, J., et al. 2023, MNRAS, 520, 2180, doi: [`10.1093/mnras/stac3791`](http://doi.org/10.1093/mnras/stac3791)

(ref: clark16) Clark, C. J. R., Schofield, S. P., Gomez, H. L., & Davies, J. I. 2016, MNRAS, 459, 1646, doi: [`10.1093/mnras/stw647`](http://doi.org/10.1093/mnras/stw647)

(ref: conroy10) Conroy, C., & Gunn, J. E. 2010, ApJ, 712, 833, doi: [`10.1088/0004-637X/712/2/833`](http://doi.org/10.1088/0004-637X/712/2/833)

(ref: conroy09) Conroy, C., Gunn, J. E., & White, M. 2009, ApJ, 699, 486, doi: [`10.1088/0004-637X/699/1/486`](http://doi.org/10.1088/0004-637X/699/1/486)

(ref: curti24a) Curti, M., Maiolino, R., Curtis-Lake, E., et al. 2024, A&A, 684, A75, doi: [`10.1051/0004-6361/202346698`](http://doi.org/10.1051/0004-6361/202346698)

(ref: dacunha15) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110, doi: [`10.1088/0004-637X/806/1/110`](http://doi.org/10.1088/0004-637X/806/1/110)

(ref: devis19) De Vis, P., Jones, A., Viaene, S., et al. 2019, A&A, 623, A5, doi: [`10.1051/0004-6361/201834444`](http://doi.org/10.1051/0004-6361/201834444)

(ref: diaz-santos13) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2013, ApJ, 774, 68, doi: [`10.1088/0004-637X/774/1/68`](http://doi.org/10.1088/0004-637X/774/1/68)

(ref: dijkstra09) Dijkstra, M., & Loeb, A. 2009, MNRAS, 400, 1109, doi: [`10.1111/j.1365-2966.2009.15533.x`](http://doi.org/10.1111/j.1365-2966.2009.15533.x)

(ref: dudzevivciute20) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828, doi: [`10.1093/mnras/staa769`](http://doi.org/10.1093/mnras/staa769)

(ref: dunlop17) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861, doi: [`10.1093/mnras/stw3088`](http://doi.org/10.1093/mnras/stw3088)

(ref: dunne00) Dunne, L., Eales, S., Edmunds, M., et al. 2000, MNRAS, 315, 115, doi: [`10.1046/j.1365-8711.2000.03386.x`](http://doi.org/10.1046/j.1365-8711.2000.03386.x)

(ref: dutton14) Dutton, A. A., & Macciò, A. V. 2014, MNRAS, 441, 3359, doi: [`10.1093/mnras/stu742`](http://doi.org/10.1093/mnras/stu742)

(ref: endsley21) Endsley, R., Stark, D. P., Charlot, S., et al. 2021, MNRAS, 502, 6044, doi: [`10.1093/mnras/stab432`](http://doi.org/10.1093/mnras/stab432)

(ref: finkelstein15) Finkelstein, S. L., Ryan, Jr., R. E., Papovich, C., et al. 2015, ApJ, 810, 71, doi: [`10.1088/0004-637X/810/1/71`](http://doi.org/10.1088/0004-637X/810/1/71)

(ref: Foreman-Mackey13) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: fujimoto24) Fujimoto, S., Ouchi, M., Nakajima, K., et al. 2024a, ApJ, 964, 146, doi: [`10.3847/1538-4357/ad235c`](http://doi.org/10.3847/1538-4357/ad235c)

(ref: fujimoto24_cosmicgrape) Fujimoto, S., Ouchi, M., Kohno, K., et al. 2024b, arXiv e-prints, arXiv:2402.18543, doi: [`10.48550/arXiv.2402.18543`](http://doi.org/10.48550/arXiv.2402.18543)

(ref: gardner23) Gardner, J. P., Mather, J. C., Abbott, R., et al. 2023, PASP, 135, 068001, doi: [`10.1088/1538-3873/acd1b5`](http://doi.org/10.1088/1538-3873/acd1b5)

(ref: garnett92) Garnett, D. R. 1992, AJ, 103, 1330, doi: [`10.1086/116146`](http://doi.org/10.1086/116146)

(ref: gimenez’-arteaga23) Giménez-Arteaga, C., Oesch, P. A., Brammer, G. B., et al. 2023, ApJ, 948, 126, doi: [`10.3847/1538-4357/acc5ea`](http://doi.org/10.3847/1538-4357/acc5ea)

(ref: green05) Greene, J. E., & Ho, L. C. 2005, ApJ, 630, 122, doi: [`10.1086/431897`](http://doi.org/10.1086/431897)

(ref: greene24) Greene, J. E., Labbe, I., Goulding, A. D., et al. 2024, ApJ, 964, 39, doi: [`10.3847/1538-4357/ad1e5f`](http://doi.org/10.3847/1538-4357/ad1e5f)

(ref: gullberg15) Gullberg, B., De Breuck, C., Vieira, J. D., et al. 2015, MNRAS, 449, 2883, doi: [`10.1093/mnras/stv372`](http://doi.org/10.1093/mnras/stv372)

(ref: harikane19a) Harikane, Y., Ouchi, M., Ono, Y., et al. 2019, ApJ, 883, 142, doi: [`10.3847/1538-4357/ab2cd5`](http://doi.org/10.3847/1538-4357/ab2cd5)

(ref: harikane23b) Harikane, Y., Zhang, Y., Nakajima, K., et al. 2023, ApJ, 959, 39, doi: [`10.3847/1538-4357/ad029e`](http://doi.org/10.3847/1538-4357/ad029e)

(ref: harikane25) Harikane, Y., Inoue, A. K., Ellis, R. S., et al. 2025, ApJ, 980, 138, doi: [`10.3847/1538-4357/ad9b2c`](http://doi.org/10.3847/1538-4357/ad9b2c)

(ref: harris20) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: hashimoto19) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, PASJ, 71, 71, doi: [`10.1093/pasj/psz049`](http://doi.org/10.1093/pasj/psz049)

(ref: hayes11) Hayes, M., Scarlata, C., & Siana, B. 2011, Nature, 476, 304, doi: [`10.1038/nature10320`](http://doi.org/10.1038/nature10320)

(ref: heintz23) Heintz, K. E., Brammer, G. B., Giménez-Arteaga, C., et al. 2023, Nature Astronomy, 7, 1517, doi: [`10.1038/s41550-023-02078-7`](http://doi.org/10.1038/s41550-023-02078-7)

(ref: herenz20) Herenz, E. C., Hayes, M., & Scarlata, C. 2020, A&A, 642, A55, doi: [`10.1051/0004-6361/202037464`](http://doi.org/10.1051/0004-6361/202037464)

(ref: hirashita14) Hirashita, H., Ferrara, A., Dayal, P., & Ouchi, M. 2014, MNRAS, 443, 1704, doi: [`10.1093/mnras/stu1290`](http://doi.org/10.1093/mnras/stu1290)

(ref: hirschmann23) Hirschmann, M., Charlot, S., & Somerville, R. S. 2023, MNRAS, 526, 3504, doi: [`10.1093/mnras/stad2745`](http://doi.org/10.1093/mnras/stad2745)

(ref: holland99) Holland, W. S., Robson, E. I., Gear, W. K., et al. 1999, MNRAS, 303, 659, doi: [`10.1046/j.1365-8711.1999.02111.x`](http://doi.org/10.1046/j.1365-8711.1999.02111.x)

(ref: hollenbach99) Hollenbach, D. J., & Tielens, A. G. G. M. 1999, Reviews of Modern Physics, 71, 173, doi: [`10.1103/RevModPhys.71.173`](http://doi.org/10.1103/RevModPhys.71.173)

(ref: hopkins08) Hopkins, P. F., Hernquist, L., Cox, T. J., & Kereš, D. 2008, ApJS, 175, 356, doi: [`10.1086/524362`](http://doi.org/10.1086/524362)

(ref: hunter07) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: inami22) Inami, H., Algera, H. S. B., Schouws, S., et al. 2022, MNRAS, 515, 3126, doi: [`10.1093/mnras/stac1779`](http://doi.org/10.1093/mnras/stac1779)

(ref: ishikawa24) Ishikawa, Y., Zakamska, N. L., Shen, Y., et al. 2024, arXiv e-prints, arXiv:2403.08098, doi: [`10.48550/arXiv.2403.08098`](http://doi.org/10.48550/arXiv.2403.08098)

(ref: izotov06) Izotov, Y. I., Stasińska, G., Meynet, G., Guseva, N. G., & Thuan, T. X. 2006, A&A, 448, 955, doi: [`10.1051/0004-6361:20053763`](http://doi.org/10.1051/0004-6361:20053763)

(ref: izumi24) Izumi, T., Matsuoka, Y., Onoue, M., et al. 2024, ApJ, 972, 116, doi: [`10.3847/1538-4357/ad57c6`](http://doi.org/10.3847/1538-4357/ad57c6)

(ref: jaffe15) Jaffé, Y. L., Smith, R., Candlish, G. N., et al. 2015, MNRAS, 448, 1715, doi: [`10.1093/mnras/stv100`](http://doi.org/10.1093/mnras/stv100)

(ref: jakobsen22) Jakobsen, P., Ferruit, P., Alves de Oliveira, C., et al. 2022, A&A, 661, A80, doi: [`10.1051/0004-6361/202142663`](http://doi.org/10.1051/0004-6361/202142663)

(ref: johnson21) Johnson, B. D., Leja, J., Conroy, C., & Speagle, J. S. 2021, ApJS, 254, 22, doi: [`10.3847/1538-4365/abef67`](http://doi.org/10.3847/1538-4365/abef67)

(ref: jones20) Jones, G. C., Béthermin, M., Fudamoto, Y., et al. 2020, MNRAS, 491, L18, doi: [`10.1093/mnrasl/slz154`](http://doi.org/10.1093/mnrasl/slz154)

(ref: jones24a) Jones, G. C., Übler, H., Perna, M., et al. 2024a, A&A, 682, A122, doi: [`10.1051/0004-6361/202347838`](http://doi.org/10.1051/0004-6361/202347838)

(ref: jones24b) Jones, G. C., Bowler, R., Bunker, A. J., et al. 2024b, arXiv e-prints, arXiv:2412.15027, doi: [`10.48550/arXiv.2412.15027`](http://doi.org/10.48550/arXiv.2412.15027)

(ref: jones24c) Jones, G. C., Bunker, A. J., Telikova, K., et al. 2024c, arXiv e-prints, arXiv:2405.12955, doi: [`10.48550/arXiv.2405.12955`](http://doi.org/10.48550/arXiv.2405.12955)

(ref: juodvzbalis25) Juodžbalis, I., Maiolino, R., Baker, W. M., et al. 2025, arXiv e-prints, arXiv:2504.03551, doi: [`10.48550/arXiv.2504.03551`](http://doi.org/10.48550/arXiv.2504.03551)

(ref: kauffmann03) Kauffmann, G., Heckman, T. M., Tremonti, C., et al. 2003, MNRAS, 346, 1055, doi: [`10.1111/j.1365-2966.2003.07154.x`](http://doi.org/10.1111/j.1365-2966.2003.07154.x)

(ref: kewley01) Kewley, L. J., Dopita, M. A., Sutherland, R. S., Heisler, C. A., & Trevena, J. 2001, ApJ, 556, 121, doi: [`10.1086/321545`](http://doi.org/10.1086/321545)

(ref: kikuta23) Kikuta, S., Ouchi, M., Shibuya, T., et al. 2023, ApJS, 268, 24, doi: [`10.3847/1538-4365/ace4cb`](http://doi.org/10.3847/1538-4365/ace4cb)

(ref: kimock21) Kimock, B., Narayanan, D., Smith, A., et al. 2021, ApJ, 909, 119, doi: [`10.3847/1538-4357/abbe89`](http://doi.org/10.3847/1538-4357/abbe89)

(ref: knudsen17) Knudsen, K. K., Watson, D., Frayer, D., et al. 2017, MNRAS, 466, 138, doi: [`10.1093/mnras/stw3066`](http://doi.org/10.1093/mnras/stw3066)

(ref: kocevski23) Kocevski, D. D., Onoue, M., Inayoshi, K., et al. 2023, ApJL, 954, L4, doi: [`10.3847/2041-8213/ace5a0`](http://doi.org/10.3847/2041-8213/ace5a0)

(ref: kokubo24) Kokubo, M., & Harikane, Y. 2024, arXiv e-prints, arXiv:2407.04777, doi: [`10.48550/arXiv.2407.04777`](http://doi.org/10.48550/arXiv.2407.04777)

(ref: kusakabe19) Kusakabe, H., Shimasaku, K., Momose, R., et al. 2019, PASJ, 71, 55, doi: [`10.1093/pasj/psz029`](http://doi.org/10.1093/pasj/psz029)

(ref: lake15) Lake, E., Zheng, Z., Cen, R., et al. 2015, ApJ, 806, 46, doi: [`10.1088/0004-637X/806/1/46`](http://doi.org/10.1088/0004-637X/806/1/46)

(ref: lamperti24) Lamperti, I., Arribas, S., Perna, M., et al. 2024, A&A, 691, A153, doi: [`10.1051/0004-6361/202451021`](http://doi.org/10.1051/0004-6361/202451021)

(ref: laporte17) Laporte, N., Nakajima, K., Ellis, R. S., et al. 2017, ApJ, 851, 40, doi: [`10.3847/1538-4357/aa96a8`](http://doi.org/10.3847/1538-4357/aa96a8)

(ref: leclercq17) Leclercq, F., Bacon, R., Wisotzki, L., et al. 2017, A&A, 608, A8, doi: [`10.1051/0004-6361/201731480`](http://doi.org/10.1051/0004-6361/201731480)

(ref: leja17) Leja, J., Johnson, B. D., Conroy, C., van Dokkum, P. G., & Byler, N. 2017, ApJ, 837, 170, doi: [`10.3847/1538-4357/aa5ffe`](http://doi.org/10.3847/1538-4357/aa5ffe)

(ref: li20a) Li, Y., Gu, M. F., Yajima, H., Zhu, Q., & Maji, M. 2020, MNRAS, 494, 1919, doi: [`10.1093/mnras/staa733`](http://doi.org/10.1093/mnras/staa733)

(ref: li08) Li, Y., Hopkins, P. F., Hernquist, L., et al. 2008, ApJ, 678, 41, doi: [`10.1086/529364`](http://doi.org/10.1086/529364)

(ref: liu19) Liu, H.-Y., Liu, W.-J., Dong, X.-B., et al. 2019, ApJS, 243, 21, doi: [`10.3847/1538-4365/ab298b`](http://doi.org/10.3847/1538-4365/ab298b)

(ref: luridiana15) Luridiana, V., Morisset, C., & Shaw, R. A. 2015, A&A, 573, A42, doi: [`10.1051/0004-6361/201323152`](http://doi.org/10.1051/0004-6361/201323152)

(ref: madau95) Madau, P. 1995, ApJ, 441, 18, doi: [`10.1086/175332`](http://doi.org/10.1086/175332)

(ref: maiolino23) Maiolino, R., Scholtz, J., Curtis-Lake, E., et al. 2023, arXiv e-prints, arXiv:2308.01230, doi: [`10.48550/arXiv.2308.01230`](http://doi.org/10.48550/arXiv.2308.01230)

(ref: marconcini24b) Marconcini, C., D’Eugenio, F., Maiolino, R., et al. 2024a, arXiv e-prints, arXiv:2411.08627, doi: [`10.48550/arXiv.2411.08627`](http://doi.org/10.48550/arXiv.2411.08627)

(ref: marconcini24a) —. 2024b, MNRAS, 533, 2488, doi: [`10.1093/mnras/stae1971`](http://doi.org/10.1093/mnras/stae1971)

(ref: marrone18) Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, Nature, 553, 51, doi: [`10.1038/nature24629`](http://doi.org/10.1038/nature24629)

(ref: marshall24) Marshall, M. A., Yue, M., Eilers, A.-C., et al. 2024, arXiv e-prints, arXiv:2410.11035, doi: [`10.48550/arXiv.2410.11035`](http://doi.org/10.48550/arXiv.2410.11035)

(ref: matsuda04) Matsuda, Y., Yamada, T., Hayashino, T., et al. 2004, AJ, 128, 569, doi: [`10.1086/422020`](http://doi.org/10.1086/422020)

(ref: matthee15) Matthee, J., Sobral, D., Santos, S., et al. 2015, MNRAS, 451, 400, doi: [`10.1093/mnras/stv947`](http://doi.org/10.1093/mnras/stv947)

(ref: matthee17) Matthee, J., Sobral, D., Boone, F., et al. 2017, ApJ, 851, 145, doi: [`10.3847/1538-4357/aa9931`](http://doi.org/10.3847/1538-4357/aa9931)

(ref: matthee20) Matthee, J., Pezzulli, G., Mackenzie, R., et al. 2020, MNRAS, 498, 3043, doi: [`10.1093/mnras/staa2550`](http://doi.org/10.1093/mnras/staa2550)

(ref: matthee24) Matthee, J., Naidu, R. P., Brammer, G., et al. 2024, ApJ, 963, 129, doi: [`10.3847/1538-4357/ad2345`](http://doi.org/10.3847/1538-4357/ad2345)

(ref: mazzolari24) Mazzolari, G., Übler, H., Maiolino, R., et al. 2024, A&A, 691, A345, doi: [`10.1051/0004-6361/202450407`](http://doi.org/10.1051/0004-6361/202450407)

(ref: mckinney2010data) McKinney, W., et al. 2010, in Proceedings of the 9th Python in Science Conference, Vol. 445, Austin, TX, 51–56

(ref: mclure04) McLure, R. J., & Dunlop, J. S. 2004, MNRAS, 352, 1390, doi: [`10.1111/j.1365-2966.2004.08034.x`](http://doi.org/10.1111/j.1365-2966.2004.08034.x)

(ref: mo02) Mo, H. J., & White, S. D. M. 2002, MNRAS, 336, 112, doi: [`10.1046/j.1365-8711.2002.05723.x`](http://doi.org/10.1046/j.1365-8711.2002.05723.x)

(ref: momose14) Momose, R., Ouchi, M., Nakajima, K., et al. 2014, MNRAS, 442, 110, doi: [`10.1093/mnras/stu825`](http://doi.org/10.1093/mnras/stu825)

(ref: momose16) —. 2016, MNRAS, 457, 2318, doi: [`10.1093/mnras/stw021`](http://doi.org/10.1093/mnras/stw021)

(ref: morishita25) Morishita, T., Stiavelli, M., Vanzella, E., et al. 2025, ApJ, 985, 83, doi: [`10.3847/1538-4357/adc4c3`](http://doi.org/10.3847/1538-4357/adc4c3)

(ref: moster13) Moster, B. P., Naab, T., & White, S. D. M. 2013, MNRAS, 428, 3121, doi: [`10.1093/mnras/sts261`](http://doi.org/10.1093/mnras/sts261)

(ref: moster18) —. 2018, MNRAS, 477, 1822, doi: [`10.1093/mnras/sty655`](http://doi.org/10.1093/mnras/sty655)

(ref: mowla24) Mowla, L., Iyer, K., Asada, Y., et al. 2024, Nature, 636, 332, doi: [`10.1038/s41586-024-08293-0`](http://doi.org/10.1038/s41586-024-08293-0)

(ref: nakajima16) Nakajima, K., Ellis, R. S., Iwata, I., et al. 2016, ApJL, 831, L9, doi: [`10.3847/2041-8205/831/1/L9`](http://doi.org/10.3847/2041-8205/831/1/L9)

(ref: nakajima22) Nakajima, K., & Maiolino, R. 2022, MNRAS, 513, 5134, doi: [`10.1093/mnras/stac1242`](http://doi.org/10.1093/mnras/stac1242)

(ref: nakajima23) Nakajima, K., Ouchi, M., Isobe, Y., et al. 2023, ApJS, 269, 33, doi: [`10.3847/1538-4365/acd556`](http://doi.org/10.3847/1538-4365/acd556)

(ref: nakazato24) Nakazato, Y., Ceverino, D., & Yoshida, N. 2024, ApJ, 975, 238, doi: [`10.3847/1538-4357/ad7d0b`](http://doi.org/10.3847/1538-4357/ad7d0b)

(ref: navarro96) Navarro, J. F., Frenk, C. S., & White, S. D. M. 1996, ApJ, 462, 563, doi: [`10.1086/177173`](http://doi.org/10.1086/177173)

(ref: netzer09) Netzer, H. 2009, MNRAS, 399, 1907, doi: [`10.1111/j.1365-2966.2009.15434.x`](http://doi.org/10.1111/j.1365-2966.2009.15434.x)

(ref: oke83) Oke, J. B., & Gunn, J. E. 1983, ApJ, 266, 713, doi: [`10.1086/160817`](http://doi.org/10.1086/160817)

(ref: onken04) Onken, C. A., Ferrarese, L., Merritt, D., et al. 2004, ApJ, 615, 645, doi: [`10.1086/424655`](http://doi.org/10.1086/424655)

(ref: osterbrock06) Osterbrock, D. E., & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and active galactic nuclei (University Science Books)

(ref: ota14) Ota, K., Walter, F., Ohta, K., et al. 2014, ApJ, 792, 34, doi: [`10.1088/0004-637X/792/1/34`](http://doi.org/10.1088/0004-637X/792/1/34)

(ref: ouchi09) Ouchi, M., Ono, Y., Egami, E., et al. 2009, ApJ, 696, 1164, doi: [`10.1088/0004-637X/696/2/1164`](http://doi.org/10.1088/0004-637X/696/2/1164)

(ref: ouchi10) Ouchi, M., Shimasaku, K., Furusawa, H., et al. 2010, ApJ, 723, 869, doi: [`10.1088/0004-637X/723/1/869`](http://doi.org/10.1088/0004-637X/723/1/869)

(ref: ouchi13) Ouchi, M., Ellis, R., Ono, Y., et al. 2013, ApJ, 778, 102, doi: [`10.1088/0004-637X/778/2/102`](http://doi.org/10.1088/0004-637X/778/2/102)

(ref: ouchi18) Ouchi, M., Harikane, Y., Shibuya, T., et al. 2018, PASJ, 70, S13, doi: [`10.1093/pasj/psx074`](http://doi.org/10.1093/pasj/psx074)

(ref: pacucci23) Pacucci, F., Nguyen, B., Carniani, S., Maiolino, R., & Fan, X. 2023, ApJL, 957, L3, doi: [`10.3847/2041-8213/ad0158`](http://doi.org/10.3847/2041-8213/ad0158)

(ref: palla24) Palla, M., De Looze, I., Relaño, M., et al. 2024, MNRAS, 528, 2407, doi: [`10.1093/mnras/stae160`](http://doi.org/10.1093/mnras/stae160)

(ref: parlanti25) Parlanti, E., Carniani, S., Venturi, G., et al. 2025, A&A, 695, A6, doi: [`10.1051/0004-6361/202451692`](http://doi.org/10.1051/0004-6361/202451692)

(ref: perna23IAU) Perna, M. 2023, in IAU Symposium, Vol. 373, Resolving the Rise and Fall of Star Formation in Galaxies, ed. T. Wong & W.-T. Kim, 60–62, doi: [`10.1017/S174392132200374X`](http://doi.org/10.1017/S174392132200374X)

(ref: perna23) Perna, M., Arribas, S., Marshall, M., et al. 2023, A&A, 679, A89, doi: [`10.1051/0004-6361/202346649`](http://doi.org/10.1051/0004-6361/202346649)

(ref: perna25) Perna, M., Arribas, S., Lamperti, I., et al. 2025, A&A, 696, A59, doi: [`10.1051/0004-6361/202453430`](http://doi.org/10.1051/0004-6361/202453430)

(ref: peroux20) Péroux, C., & Howk, J. C. 2020, ARA&A, 58, 363, doi: [`10.1146/annurev-astro-021820-120014`](http://doi.org/10.1146/annurev-astro-021820-120014)

(ref: planck20) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6, doi: [`10.1051/0004-6361/201833910`](http://doi.org/10.1051/0004-6361/201833910)

(ref: prescott12) Prescott, M. K. M., Dey, A., Brodwin, M., et al. 2012, ApJ, 752, 86, doi: [`10.1088/0004-637X/752/2/86`](http://doi.org/10.1088/0004-637X/752/2/86)

(ref: rauscher24) Rauscher, B. J. 2024, PASP, 136, 015001, doi: [`10.1088/1538-3873/ad1b36`](http://doi.org/10.1088/1538-3873/ad1b36)

(ref: reines13) Reines, A. E., Greene, J. E., & Geha, M. 2013, ApJ, 775, 116, doi: [`10.1088/0004-637X/775/2/116`](http://doi.org/10.1088/0004-637X/775/2/116)

(ref: reines15) Reines, A. E., & Volonteri, M. 2015, ApJ, 813, 82, doi: [`10.1088/0004-637X/813/2/82`](http://doi.org/10.1088/0004-637X/813/2/82)

(ref: rhee17) Rhee, J., Smith, R., Choi, H., et al. 2017, ApJ, 843, 128, doi: [`10.3847/1538-4357/aa6d6c`](http://doi.org/10.3847/1538-4357/aa6d6c)

(ref: richards06) Richards, G. T., Lacy, M., Storrie-Lombardi, L. J., et al. 2006, ApJS, 166, 470, doi: [`10.1086/506525`](http://doi.org/10.1086/506525)

(ref: riechers13) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329, doi: [`10.1038/nature12050`](http://doi.org/10.1038/nature12050)

(ref: rieke23) Rieke, M. J., Kelly, D. M., Misselt, K., et al. 2023, PASP, 135, 028001, doi: [`10.1088/1538-3873/acac53`](http://doi.org/10.1088/1538-3873/acac53)

(ref: jane_rigby_2024_10933642) Rigby, J., Hutchison, T. A., Rivera-Thorsen, T. E., et al. 2024, JWST-Templates/Notebooks: minor update, added DOI tracker, v1.0.2, Zenodo, doi: [`10.5281/zenodo.10933642`](http://doi.org/10.5281/zenodo.10933642)

(ref: rigby23) Rigby, J. R., Vieira, J. D., Phadke, K. A., et al. 2023, arXiv e-prints, arXiv:2312.10465, doi: [`10.48550/arXiv.2312.10465`](http://doi.org/10.48550/arXiv.2312.10465)

(ref: robitaille_2024_10931886) Robitaille, T., Ginsburg, A., Mumford, S., et al. 2024, astropy/reproject: v0.13.1, v0.13.1, Zenodo, doi: [`10.5281/zenodo.10931886`](http://doi.org/10.5281/zenodo.10931886)

(ref: santini17) Santini, P., Fontana, A., Castellano, M., et al. 2017, ApJ, 847, 76, doi: [`10.3847/1538-4357/aa8874`](http://doi.org/10.3847/1538-4357/aa8874)

(ref: scholtz24) Scholtz, J., Curti, M., D’Eugenio, F., et al. 2024, arXiv e-prints, arXiv:2411.07695, doi: [`10.48550/arXiv.2411.07695`](http://doi.org/10.48550/arXiv.2411.07695)

(ref: shapley20) Shapley, A. E., Cullen, F., Dunlop, J. S., et al. 2020, ApJL, 903, L16, doi: [`10.3847/2041-8213/abc006`](http://doi.org/10.3847/2041-8213/abc006)

(ref: shen11) Shen, Y., Richards, G. T., Strauss, M. A., et al. 2011, ApJS, 194, 45, doi: [`10.1088/0067-0049/194/2/45`](http://doi.org/10.1088/0067-0049/194/2/45)

(ref: shen19) Shen, Y., Wu, J., Jiang, L., et al. 2019, ApJ, 873, 35, doi: [`10.3847/1538-4357/ab03d9`](http://doi.org/10.3847/1538-4357/ab03d9)

(ref: shibuya18) Shibuya, T., Ouchi, M., Konno, A., et al. 2018, PASJ, 70, S14, doi: [`10.1093/pasj/psx122`](http://doi.org/10.1093/pasj/psx122)

(ref: shuntov25) Shuntov, M., Akins, H. B., Paquereau, L., et al. 2025, arXiv e-prints, arXiv:2506.03243, doi: [`10.48550/arXiv.2506.03243`](http://doi.org/10.48550/arXiv.2506.03243)

(ref: smit18) Smit, R., Bouwens, R. J., Carniani, S., et al. 2018, Nature, 553, 178, doi: [`10.1038/nature24631`](http://doi.org/10.1038/nature24631)

(ref: sobral15) Sobral, D., Matthee, J., Darvish, B., et al. 2015, ApJ, 808, 139, doi: [`10.1088/0004-637X/808/2/139`](http://doi.org/10.1088/0004-637X/808/2/139)

(ref: sobral18b) —. 2018, MNRAS, 477, 2817, doi: [`10.1093/mnras/sty782`](http://doi.org/10.1093/mnras/sty782)

(ref: sobral19) Sobral, D., Matthee, J., Brammer, G., et al. 2019, MNRAS, 482, 2422, doi: [`10.1093/mnras/sty2779`](http://doi.org/10.1093/mnras/sty2779)

(ref: solomon05) Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677, doi: [`10.1146/annurev.astro.43.051804.102221`](http://doi.org/10.1146/annurev.astro.43.051804.102221)

(ref: sorba15) Sorba, R., & Sawicki, M. 2015, MNRAS, 452, 235, doi: [`10.1093/mnras/stv1235`](http://doi.org/10.1093/mnras/stv1235)

(ref: sorba18) —. 2018, MNRAS, 476, 1532, doi: [`10.1093/mnras/sty186`](http://doi.org/10.1093/mnras/sty186)

(ref: steidel00) Steidel, C. C., Adelberger, K. L., Shapley, A. E., et al. 2000, ApJ, 532, 170, doi: [`10.1086/308568`](http://doi.org/10.1086/308568)

(ref: storey00) Storey, P. J., & Zeippen, C. J. 2000, MNRAS, 312, 813, doi: [`10.1046/j.1365-8711.2000.03184.x`](http://doi.org/10.1046/j.1365-8711.2000.03184.x)

(ref: sugahara25) Sugahara, Y., Álvarez-Márquez, J., Hashimoto, T., et al. 2025, ApJ, 981, 135, doi: [`10.3847/1538-4357/adb02a`](http://doi.org/10.3847/1538-4357/adb02a)

(ref: tacconi08) Tacconi, L. J., Genzel, R., Smail, I., et al. 2008, ApJ, 680, 246, doi: [`10.1086/587168`](http://doi.org/10.1086/587168)

(ref: tadaki18) Tadaki, K., Iono, D., Yun, M. S., et al. 2018, Nature, 560, 613, doi: [`10.1038/s41586-018-0443-1`](http://doi.org/10.1038/s41586-018-0443-1)

(ref: toft14) Toft, S., Smolčić, V., Magnelli, B., et al. 2014, ApJ, 782, 68, doi: [`10.1088/0004-637X/782/2/68`](http://doi.org/10.1088/0004-637X/782/2/68)

(ref: toshikawa18) Toshikawa, J., Uchiyama, H., Kashikawa, N., et al. 2018, PASJ, 70, S12, doi: [`10.1093/pasj/psx102`](http://doi.org/10.1093/pasj/psx102)

(ref: trakhtenbrot11) Trakhtenbrot, B., Netzer, H., Lira, P., & Shemmer, O. 2011, ApJ, 730, 7, doi: [`10.1088/0004-637X/730/1/7`](http://doi.org/10.1088/0004-637X/730/1/7)

(ref: ubler24) Übler, H., Maiolino, R., Pérez-González, P. G., et al. 2024, MNRAS, 531, 355, doi: [`10.1093/mnras/stae943`](http://doi.org/10.1093/mnras/stae943)

(ref: umehata21) Umehata, H., Smail, I., Steidel, C. C., et al. 2021, ApJ, 918, 69, doi: [`10.3847/1538-4357/ac1106`](http://doi.org/10.3847/1538-4357/ac1106)

(ref: valentino23) Valentino, F., Brammer, G., Gould, K. M. L., et al. 2023, ApJ, 947, 20, doi: [`10.3847/1538-4357/acbefa`](http://doi.org/10.3847/1538-4357/acbefa)

(ref: villanueva24) Villanueva, V., Herrera-Camus, R., González-López, J., et al. 2024, A&A, 691, A133, doi: [`10.1051/0004-6361/202451490`](http://doi.org/10.1051/0004-6361/202451490)

(ref: virtanen20) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: walter08) Walter, F., Brinks, E., de Blok, W. J. G., et al. 2008, AJ, 136, 2563, doi: [`10.1088/0004-6256/136/6/2563`](http://doi.org/10.1088/0004-6256/136/6/2563)

(ref: walter12) Walter, F., Decarli, R., Carilli, C., et al. 2012, ApJ, 752, 93, doi: [`10.1088/0004-637X/752/2/93`](http://doi.org/10.1088/0004-637X/752/2/93)

(ref: watson15) Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327, doi: [`10.1038/nature14164`](http://doi.org/10.1038/nature14164)

(ref: witstok22) Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS, 515, 1751, doi: [`10.1093/mnras/stac1905`](http://doi.org/10.1093/mnras/stac1905)

(ref: witten24) Witten, C., Laporte, N., Martin-Alvarez, S., et al. 2024, Nature Astronomy, 8, 384, doi: [`10.1038/s41550-023-02179-3`](http://doi.org/10.1038/s41550-023-02179-3)

(ref: wong22) Wong, Y. H. V., Wang, P., Hashimoto, T., et al. 2022, ApJ, 929, 161, doi: [`10.3847/1538-4357/ac5cc7`](http://doi.org/10.3847/1538-4357/ac5cc7)

(ref: yajima23) Yajima, H., Abe, M., Fukushima, H., et al. 2023, MNRAS, 525, 4832, doi: [`10.1093/mnras/stad2497`](http://doi.org/10.1093/mnras/stad2497)

(ref: yajima13) Yajima, H., Li, Y., & Zhu, Q. 2013, ApJ, 773, 151, doi: [`10.1088/0004-637X/773/2/151`](http://doi.org/10.1088/0004-637X/773/2/151)

(ref: yajima12c) Yajima, H., Umemura, M., & Mori, M. 2012, MNRAS, 420, 3381, doi: [`10.1111/j.1365-2966.2011.20261.x`](http://doi.org/10.1111/j.1365-2966.2011.20261.x)

(ref: yajima22) Yajima, H., Abe, M., Khochfar, S., et al. 2022, MNRAS, 509, 4037, doi: [`10.1093/mnras/stab3092`](http://doi.org/10.1093/mnras/stab3092)

(ref: yoon17) Yoon, H., Chung, A., Smith, R., & Jaffé, Y. L. 2017, ApJ, 838, 81, doi: [`10.3847/1538-4357/aa6579`](http://doi.org/10.3847/1538-4357/aa6579)

(ref: zabl15) Zabl, J., Nørgaard-Nielsen, H. U., Fynbo, J. P. U., et al. 2015, MNRAS, 451, 2050, doi: [`10.1093/mnras/stv1019`](http://doi.org/10.1093/mnras/stv1019)

(ref: zamora24) Zamora, S., Venturi, G., Carniani, S., et al. 2024, arXiv e-prints, arXiv:2412.02751, doi: [`10.48550/arXiv.2412.02751`](http://doi.org/10.48550/arXiv.2412.02751)

(ref: zana22) Zana, T., Gallerani, S., Carniani, S., et al. 2022, MNRAS, 513, 2118, doi: [`10.1093/mnras/stac978`](http://doi.org/10.1093/mnras/stac978)

(ref: zanella18) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976, doi: [`10.1093/mnras/sty2394`](http://doi.org/10.1093/mnras/sty2394)

[^1]: <https://mast.stsci.edu/portal/Mashup/Clients/Mast/Portal.html>

[^2]: <https://github.com/JWST-Templates>

[^3]: <https://dawn-cph.github.io/dja/index.html>

[^4]: <https://cosmos.astro.caltech.edu/page/cosmosweb-dr>

[^5]: <https://almascience.org/>

[^6]: <https://almascience.nao.ac.jp/documents-and-tools/cycle-1/alma-proposers-guide>

[^7]: The positional accuracy of ALMA imaging is roughly estimated by the relationship: $\theta_\mathrm{beam}/(\mathrm{S/N})/0.9$, where $\theta_\mathrm{beam}$ is FWHM synthesized beam size in arcsecond (see equation 10.7 of ALMA Technical Handbook: <https://almascience.nao.ac.jp/documents-and-tools/cycle11/alma-technical-handbook>).

[^8]: (cite: laporte17) have referred to COS-2987030247 as ‘COSz2’.

</paper>

Write the methods card for this paper.