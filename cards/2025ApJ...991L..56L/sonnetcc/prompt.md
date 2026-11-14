# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...991L..56L\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...991L..56L",
 "title": "Resolving Emission from Small Dust Grains in the Blue Compact Dwarf II Zw 40 with JWST",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Lai, Thomas S.-Y.",
 "n_authors": 18,
 "arxiv_id": "2509.04662",
 "doi": "10.3847/2041-8213/ae0467",
 "alma_projects_linked_by_archive": [
  "2012.1.00984.S"
 ]
}
```

Paper text:
<paper>
# Resolving Emission from Small Dust Grains in the Blue Compact Dwarf II Zw 40 with JWST

## Abstract

We present James Webb Space Telescope (JWST) Near Infrared Spectrograph (NIRSpec) and Mid-infrared Instrument (MIRI) integral-field spectroscopy of the nearby blue compact dwarf II Zw 40, which has a low metallicity of 25% of solar. Leveraging the high spatial/spectral resolution and wavelength coverage of JWST/NIRSpec, we present robust detections of the 3.3 $\mu$m polycyclic aromatic hydrocarbon (PAH) emission on 20 pc scales. The strength of the $\mathrm{Pf}\,\delta$ emission relative to the 3.3 PAH feature is significantly stronger than typical higher metallicity star-forming galaxies. We find that 3.3 $\mu$m PAH emission is concentrated near the northern super star cluster and is co-spatial with CO gas. A strong correlation exists between the 3.3/11.3 PAH ratio and radiation hardness probed by \[Ne III\]/\[Ne II\], providing evidence of photodestruction of PAH molecules in intense radiation environments. Our analysis shows that while the overall PAH fraction is lower in II Zw 40 than in higher metallicity galaxies, the contribution of the 3.3 $\mu$m PAH feature to the total PAH emission is higher. We propose that the PAH size distribution is fundamentally shaped by two competing mechanisms in low-metallicity environments: photo-destruction and inhibited growth. Additionally, the high radiation field intensity in II Zw 40 suggests that multi-photon heating of PAHs may be an important effect. As one of the first spatially resolved studies of aromatic emission in a low-metallicity environment, our spectroscopic results offer practical guidance for future observations of the 3.3 $\mu$m PAH feature in low-metallicity galaxies using JWST.

UTF8bsmi

show\]ThomasLai.astro@gmail.com

# Introduction

Blue compact dwarf (BCD) galaxies constitute the least chemically evolved star-forming systems in the local universe (cite: Thuan2008), making them excellent laboratories for examining primordial star formation and the build-up of metal content in the early universe. BCDs are characterized by their low luminosity (M$_\mathrm{V}\gtrsim-18$), compact size ($\leq$1 kpc in diameter), blue optical color, and low metal abundance, with oxygen abundances 12+log(O/H) ranging from 7.1 to 8.3 ($\sim$3—30% Z$_{\odot}$) (cite: Thuan1981).

The ISM conditions in metal-poor galaxies and typical starburst galaxies exhibit significant differences (cite: Henkel2022). Between galaxies with extremely low metallicity (2% Z$_{\odot}$) and those approaching solar metallicity, the gas-to-dust mass ratio differs by three orders of magnitude (cite: Remy-Ruyer2014), and the dust-to-metal ratio varies by about an order of magnitude (cite: DeVis2019). In low-metallicity galaxies, (cite: Remy-Ruyer2015) identified far-infrared dust SEDs with broader profiles and peaks at shorter wavelengths compared to their metal-rich counterparts. Another notable difference is the reduction in polycyclic aromatic hydrocarbon (cite: Tielens2008; Li2020) flux relative to the dust continuum level, as demonstrated in various studies (cite: Madden2006; Engelbracht2005; Wu2006; Gordon2008), particularly when the metallicity drops to very low levels below 12+log(O/H)$\sim$8 (cite: Draine2007b; Engelbracht2008).

While there is evidence that PAHs are affected by the metal content and the radiation fields of the ISM, the precise dependence of PAH emission on metallicity, particularly in galaxies of intermediate metallicities, and the role of the interstellar radiation field on PAH emission in such environments warrant further exploration. Several hypotheses have been proposed to address the deficit of PAHs in low-metallicity environments: (i) from a destruction viewpoint, low dust shielding of the ISM in metal-poor environments may allow UV photons to penetrate and dissociate PAHs (cite: Madden2006; Wu2006; Hunt2010; Cormier2015); (ii) from a chemical formation standpoint, inhibited grain growth in low-metallicity environments may result from a shortage of available carbon atoms essential for building up PAH molecules (cite: Sandstrom2012; Whitcomb2024); and (iii) (cite: Galliano2008) suggested that AGB stars delay their injection of carbon dust into the ISM, and since these stars are the main source of PAHs (cite: Latter1991), their absence in young clusters naturally leads to PAH scarcity.

To test these hypotheses, high spatial resolution MIR observations are essential for tracking PAH emission in low-metallicity dwarf galaxies, particularly since observations from Local Group dwarfs reveal that PAH emission concentrates in small clumps, unlike in high-metallicity galaxies where PAHs are pervasively distributed throughout the ISM (cite: Chown2025_WLM). While Spitzer has provided valuable insights, its spectral mapping capabilities were limited to a handful of low-metallicity targets (cite: Haynes2010; Sandstrom2012; Whitcomb2024). In contrast, JWST’s unparalleled spatial and spectral resolving power has significantly advanced our understanding of stellar populations, as well as the dust and gas properties in metal-poor environments. For instance, previously undetectable populations of dusty evolved stars and young stellar objects have been identified, providing crucial insights into star formation in low-metallicity environments (cite: Hirschauer2024; Lenkic2024; Nally2024). In the low-mass, isolated galaxy Leo P ($\sim$3% Z$_{\odot}$), precise photometric detection of stars below the oldest main-sequence turnoff has enabled an accurate reconstruction of its star formation history (cite: McQuinn2024), and the detection of S(1) 17.03 $\mu$m micron transition of molecular hydrogen in this system has established a lower limit on the metallicity required for molecular hydrogen formation and subsequent star formation (cite: Telford2024). Moreover, JWST/MIRI has enabled the detection of \[Ne V\] in the BCD SBS0335-052E ($\sim$5% Z$_{\odot}$) and I Zw 18 ($\sim$3% Z$_{\odot}$), revealing the highly ionized nature in low-metallicity environments (cite: Mingozzi2025; Hunt2025).

In this paper, we use JWST to investigate the resolved dust properties of II Zw 40, a nearby blue compact dwarf (BCD) galaxy located at a distance of 10 Mpc with a metallicity of 12+log(O/H) = 8.1, corresponding to Z = 25% Z$_\odot$ (cite: Guseva2000). As one of the earliest studied low-metallicity galaxies (cite: Sargent1970; Searle1972; Bergeron1977), II Zw 40 exhibits characteristics similar to those of highly ionized H II regions. The galaxy hosts two super-star clusters (SSC-N and SSC-S), with SSC-N, the dominant power source, spanning approximately 15 pc in physical size. This northern cluster hosts intense star formation, with a star formation rate surface density of $1600~\mathrm{M}_\odot\,\mathrm{yr}^{-1}\,\mathrm{kpc}^{-2}$, several times higher than that of 30 Doradus in the Large Magellanic Cloud ($380~\mathrm{M}_\odot\,\mathrm{yr}^{-1}\,\mathrm{kpc}^{-2}$) (cite: Vanzi2008). Evidence of this vigorous activity is further reflected in II Zw 40’s exceptionally high \[Ne III\]/\[Ne II\] ratio, which makes it the highest known for a pure star-forming environment (cite: Hao2009). This high excitation condition is also evident in HST COS UV spectroscopy (cite: Leitherer2018), which shows emission line ratios similar to those seen in Green Pea galaxies. Based on SED fitting, dust in II Zw 40 appears to be relatively hot, peaking at $\sim$60 $\mu$m (cite: Galliano2005). Observations of the young central cluster ($<$5 Myr; (cite: Kepley2014)) reveal a relatively low gas-to-dust ratio suggestive of a localized dust formation event, as indicated by ALMA observations (cite: Consiglio2016). Together, these traits make II Zw 40 an exceptional case for studying dust formation and its link to recent star formation in the context of low abundance and high radiation intensity. While PAH emission has been detected in this galaxy via AKARI and Spitzer spectroscopy (cite: Wu2006; Lai2020), the spatial distribution of the PAH emission was unknown until now.

This paper is organized as follows. §2 describes the observations and data reduction processes, while §3 details our analysis. In §4, we present the resolved PAH properties of II Zw 40 and insights from variations in PAH ratios across different ISM conditions. §5 proposes a hypothesis on PAH size changes in low-metallicity environments based on these findings, and §6 offers a summary. For this study, we adopt a redshift for II Zw 40 of $z$=0.00248[^1], corresponding to a projected physical scale of 50 pc/arcsec.

![](IIZw40_img_v3.pdf)

![](Lai2025_IIZw40_spec_v3_final.pdf)

# Observations and data reduction

The GO program 2511 (PI: T. Lai) includes both the *JWST* Near-Infrared and Mid-Infrared integral-field spectroscopy taken with NIRSpec integral-field units (IFU) (cite: Boker2022) on Sep 29, 2023 and the Mid-InfraRed Instrument (cite: Rieke2015; Labiano2021) on Sep 27, 2023. The data are available at the Mikulski Archive for Space Telescopes (MAST) at DOI: [10.17909/fz5p-qx55](http://dx.doi.org/10.17909/fz5p-qx55). For the NIRSpec IFU observation, a set of medium-resolution gratings (with a nominal resolving power of R$\sim$1000) was used — G235M/F170LP and G395M/F290LP, covering the wavelength of 1.66–5.10 $\mu$m. The science exposure time was 934 seconds, and a 4-pt dither pattern was used to sample the two super-star clusters (SSCs) in II Zw 40. For the MRS observations, a set of four IFUs (channels 1–4) was used, covering a full range of 4.9–28.1 $\mu$m with three band settings, SHORT (A), MEDIUM (B), and LONG (C) in each channel, with the science exposure time of 278, 266, and 222 seconds, respectively, and a 4-pt dither pattern.

While taking the MIRI MRS background, simultaneous MIRI images were obtained using the F770W, F1130W, and F2100W filters. These filters were originally selected to capture the two bright PAH emission bands at 7.7 and 11.3 $\mu$m, while the longer wavelength filter traces the dust continuum at 21 $\mu$m.

In this study, we focus on the observations with the NIRSpec G395M/F290LP grating together with Channel 1-4 of MIRI MRS IFUs. The uncalibrated science observations were downloaded through the MAST Portal. For NIRSpec observations, the data reduction process was done using the *JWST* Science Calibration Pipeline version 1.12.5 (cite: Bushouse2022), with a reference file of `jwst_1177.pmap`. We followed the standard process of the first two stages of the pipeline, including `Detector1` and `Spec2`. In `Spec2`, “leakcal" was performed in the observation to mitigate the contamination due to a failed open micro-shutter assembly (MSA). For the `Spec3` stage, which handles the cube build process, at the time of reduction, we substituted it with a routine built in the `Q3D` software (cite: Rupke2014; Rupke2021) that uses the Python package `reproject` to construct the cube with a finer spaxel size of 0.05$''$ that properly samples the PSF as opposed to 0.1$''$ from the `Spec3` stage in the pipeline that is PSF undersampled (cite: Vayner2023). For the MIRI MRS observation, we followed the data reduction processes based on the Pipeline version 1.15.0, using a reference file of `jwst_1276.pmap`. All three stages of the pipeline processing, including `Detector1`, `Spec2`, and `Spec3`, were applied. A change and an additional step in `Spec2` were conducted — (i) *residual_fringe* step is on, and (ii) to correct for the over-subtraction of the continuum near the \[Ar II\] line at 8.99 $\mu$m caused by the cruciform artifact, an alternative reference file (provided by STScI) for the *straylight* step is adopted.

# Analysis & Method

The simultaneous MIRI wide band imaging of the F770W, F1130W, and F2100W was taken in parallel with the MIRI IFU observation. Due to the brightness and compactness of the source, these images were saturated at the first frame of the ramp near the northern SSC. Nonetheless, deep MIR images of II Zw 40 can be obtained, featuring the stellar streams that extend $\sim$2 kpc away from the nucleus (see Figure [1](#fig:IIZw40_img)(a)), which has been suggested as evidence that II Zw 40 underwent a recent merger (cite: vanZee1998; Kepley2014; Beilis2024). To recover the saturated pixels near the northern SSC, we replaced their values using synthetic photometry derived from matched spectra extracted from the IFU cube, reprojected onto the MIRI images. The recovered 3-color image is presented in Figure [1](#fig:IIZw40_img)(a), with F770W in blue, F1130W in green, and F1500W in red.

Combining the NIRSpec and MIRI IFU observations provides a comprehensive analysis of PAH bands across a wide range from 3 to 17 $\mu$m. While integrating both instruments offers a holistic view of all the PAH emission, the NIRSpec IFU alone provides the advantage of the highest spatial resolution, specifically for probing the smallest PAH grains that emit at 3.3 $\mu$m. In the first part of this paper (§ [4.1](#sec:pah33_variation)), we leverage the 0.05$''$ pixel size of the NIRSpec observations to precisely localize regions within the BCD where small grains can survive and examine the interplay between PAH emission and ionizing gas in a metal-poor environment. The second part of the paper (§ [4.2](#sec:pah_ratio)) focuses on the joint NIRSpec and MIRI IFU dataset. These data sets were combined by smoothing the cubes to a common PSF at 11.5 $\mu$m, enabling a proper comparison of the 3.3 $\mu$m PAH emission with its longer-wavelength counterparts.

For the NIRSpec cube, we focus on characterizing the aromatic feature at 3.3 $\mu$m and the aliphatic feature at 3.4 $\mu$m. To achieve this, we perform a detailed spectral decomposition of this wavelength range using the latest version of the *Continuum And Feature Extraction* `(CAFE)` software (cite: Diaz-Santos2025). CAFE was originally developed by (cite: Marshall2007) for *Spitzer*/IRS and has been recently updated for *JWST*, incorporating enhanced functionalities for spectral decomposition and the extraction of IFU cubes. The spectrum from each NIRSpec spaxel is fitted with `CAFE`, covering a wavelength range from 2.87 to 5.27 $\mu$m, which includes key components such as the 3.3 $\mu$m PAH band, the Pf$\delta$ line, the 3.4 $\mu$m aliphatic feature, the 3.47 $\mu$m plateau feature, and the Br$\alpha$ line.

For the combined NIRSpec and MIRI cube, we follow the method detailed in (cite: Lai2022), which smoothed the NIRSpec G395M/F290LP cube and MIRI Channels 1 and 2 by convolving them with wavelength-dependent Gaussian convolution kernels to match with the FWHM measured at 11.5 $\mu$m (FWHM$\sim$0.46$''$). Next, we use `(CAFE)` to perform a 19$\times$19 grid extraction on both smoothed cubes with each cell having a width of 0.4$''$ ($\sim$20 pc), and the grid was set to center at the northern SSC (5:55:42.6324, +3:23:32.000 ICRS). For spectral stitching, CH3 LONG is used as the reference channel, with all spectral segments combined multiplicatively using typical scaling factors of $\sim$2% for MIRI sub-channels and $\sim$10% between NIRSpec and MIRI. For the extracted 1D MIRI spectra, an additional spectral defringing procedure was applied using the routine provided by STScI (Kavanagh, P., et al., in prep).

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Region | PAH 3.3 $\mu$m | Aliphatic 3.4 $\mu$m | PAH 6.2 $\mu$m | PAH 11.3 $\mu$m | $\Sigma$PAH$_\mathrm{IIZw40}$ | $\Sigma$PAH$_\mathrm{UL}$ | Region | \[NeII\] 12.81 $\mu$m | \[NeIII\] 15.56 $\mu$m |  |  |
|  | \[$\times$10$^{-18}$\] | \[$\times$10$^{-19}$\] | \[$\times$10$^{-18}$\] | \[$\times$10$^{-18}$\] | \[$\times$10$^{-18}$\] | \[$\times$10$^{-18}$\] |  | \[$\times$10$^{-18}$\] | \[$\times$10$^{-18}$\] |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
| Extraction | 22.06 $\pm$ 2.59 | 21.06 $\pm$ 12.12 | 45.00 $\pm$ 5.52 | 78.32 $\pm$ 10.87 | 145.39 $\pm$ 12.46 | 408.55 $\pm$ 35.02 |  |  |  |  |  |
| Extraction | 27.31 $\pm$ 0.37 | 794.05 $\pm$ 42.89 |  |  |  |  |  |  |  |  |  |
|  | 7.06 $\pm$ 0.67 | 7.31 $\pm$ 3.56 | 26.47 $\pm$ 6.89 | 38.98 $\pm$ 5.91 | 72.51 $\pm$ 9.11 | 203.77 $\pm$ 25.59 |  | 10.47 $\pm$ 0.57 | 372.91 $\pm$ 27.09 |  |  |
|  | 2.69 $\pm$ 0.25 | 2.16 $\pm$ 1.41 | 8.42 $\pm$ 2.18 | 4.98 $\pm$ 1.45 | 16.09 $\pm$ 2.63 | 42.22 $\pm$ 7.40 |  | 2.32 $\pm$ 0.06 | 62.11 $\pm$ 2.62 |  |  |
| 8-8 | 0.32 $\pm$ 0.05 | 0.31 $\pm$ 0.12 | 1.02 $\pm$ 0.24 | 2.46 $\pm$ 0.62 | 3.80 $\pm$ 0.67 | 10.68 $\pm$ 1.88 | 8-8 | 0.84 $\pm$ 0.03 | 29.30 $\pm$ 1.00 |  |  |
| 8-9 | 0.99 $\pm$ 0.10 | 1.15 $\pm$ 0.55 | 2.93 $\pm$ 0.84 | 5.05 $\pm$ 1.09 | 8.97 $\pm$ 1.38 | 25.21 $\pm$ 3.88 | 8-9 | 1.33 $\pm$ 0.04 | 41.40 $\pm$ 1.38 |  |  |
| 8-10 | 2.12 $\pm$ 0.10 | 1.97 $\pm$ 0.53 | 5.09 $\pm$ 0.61 | 5.06 $\pm$ 0.61 | 12.27 $\pm$ 0.87 | 34.48 $\pm$ 2.44 | 8-10 | 1.28 $\pm$ 0.06 | 28.30 $\pm$ 1.33 |  |  |
| 9-8 | 0.59 $\pm$ 0.06 | 0.59 $\pm$ 0.34 | 2.92 $\pm$ 0.35 | 2.80 $\pm$ 0.93 | 6.31 $\pm$ 1.00 | 17.73 $\pm$ 2.81 | 9-8 | 1.25 $\pm$ 0.06 | 42.40 $\pm$ 2.15 |  |  |
| 9-9 | 1.13 $\pm$ 0.13 | 1.30 $\pm$ 0.74 | 3.26 $\pm$ 1.00 | 6.92 $\pm$ 1.37 | 11.31 $\pm$ 1.70 | 31.78 $\pm$ 4.78 | 9-9 | 1.72 $\pm$ 0.06 | 54.40 $\pm$ 2.51 |  |  |
| 9-10 | 1.46 $\pm$ 0.10 | 1.48 $\pm$ 0.53 | 3.36 $\pm$ 0.25 | 5.49 $\pm$ 1.27 | 10.31 $\pm$ 1.30 | 28.97 $\pm$ 3.65 | 9-10 | 1.21 $\pm$ 0.04 | 31.50 $\pm$ 1.37 |  |  |
| 10-8 | 1.23 $\pm$ 0.11 | 1.22 $\pm$ 0.60 | 5.17 $\pm$ 0.66 | 4.83 $\pm$ 0.80 | 11.23 $\pm$ 1.04 | 31.56 $\pm$ 2.92 | 10-8 | 1.40 $\pm$ 0.05 | 39.80 $\pm$ 1.80 |  |  |
| 10-9 | 1.06 $\pm$ 0.10 | 1.07 $\pm$ 0.24 | 4.38 $\pm$ 0.82 | 5.06 $\pm$ 1.01 | 10.50 $\pm$ 1.31 | 29.50 $\pm$ 3.68 | 10-9 | 1.55 $\pm$ 0.06 | 44.90 $\pm$ 1.63 |  |  |

: Attenuation-corrected PAH Band and Neon Line Fluxes in II Zw 40 from the Total and Grid Extraction

Table notes: All the flux units are in W/m$^{2}$. $\Sigma$PAH$_\mathrm{IIZw40}$ is the direct sum of the three PAH features at 3.3, 6.2, and 11.3 $\mu$m. This value is treated as a lower limit, while $\Sigma$PAH$_\mathrm{UL}$ is the upper limit when accounting for other non-detected PAHs

Figure [1](#fig:IIZw40_img)(b) shows the NIRSpec IFU footprint centering at the two main SSCs in II Zw 40. The map is created by stacking the frames between 3.25 and 3.34 $\mu$m. Overlaid are the apertures for which the spectra in this paper are extracted. The dashed line aperture, centered at (5:55:42.6474, +3:23:31.020 ICRS) with a radius of 1.6$''$, represents the total extraction, with its spectrum presented in Figure [2](#fig:tot_spec). Two smaller apertures (each with a radius of 0.6$''$), colored orange and blue, target the regions of SSC-N and SSC-S, respectively; their extracted spectra appear in Figure [3](#fig:pah33) and are further explored in §[4.1](#sec:pah33_variation).

For the grid extraction, we focus on the eight spectra extracted from cells near the northern SSC, as marked in Figure [1](#fig:IIZw40_img)(b), selected for their high spectral quality across both NIRSpec and MIRI wavelength ranges. Spectra from regions farther from the clusters, however, suffer from low S/N, especially at the blue end of MIRI (CH1), where MIRI’s lower sensitivity compared to NIRSpec, the source’s red MIR spectral SED, and its compact size pose challenges to achieving adequate spectral quality. The need for high S/N across all wavelengths is primarily driven by our scientific goal to accurately measure all available PAH bands from 3—17 $\mu$m. With the combined NIRSpec and MIRI observations, we find in II Zw 40 the only detected PAHs are the 3.3, 6.2, and 11.3 $\mu$m bands, where 11.3 $\mu$m is a PAH complex that includes both the 11.23 and 11.33 $\mu$m bands.

Given that the spectra are continuum-dominated, simultaneous spectroscopic fitting with a wide wavelength range across NIRSpec and MIRI is challenging. Therefore, to precisely measure the PAH fluxes, we fit each band locally with carefully defined spectral ranges, with \[3.0, 3.6\], \[5.6, 7.2\], and \[10.7, 12.4\] for PAH 3.3, 6.2, and 11.3 $\mu$m bands, respectively. These fluxes are subsequently corrected for attenuation, assuming a mixed geometry based on the opacity profile fitted by CAFE using the full NIRSpec+MIRI spectrum. This attenuation correction is minimal, with the correction factor for the 11.3 $\mu$m PAH emission, the band most susceptible to attenuation (cite: Lai2024), reaching only the 5% level. Neon lines are corrected in the same manner as the PAHs. Table [\[tab:flux\]](#tab:flux) lists all attenuation-corrected measurements of PAH and neon line fluxes.

Also included in Table [\[tab:flux\]](#tab:flux) are the fluxes of total PAH power, with their corresponding lower and upper limits ($\Sigma$PAH$_\mathrm{IIZw40}$ and $\Sigma$PAH$_\mathrm{UL}$). $\Sigma$PAH$_\mathrm{IIZw40}$ is the direct sum of the robustly detected PAH bands at 3.3, 6.2, and 11.3 $\mu$m. This value is considered a *lower limit* in our estimation, given that contributions from other typically prominent PAH features (e.g., 7.7, 8.6, and 17 $\mu$m PAHs) are not included. The effects of continuum dilution on the detectability of different PAH features depend on the strength of the underlying continuum and the power-to-width ratio of the feature. Broad features (PAH 7.7 and 17) in particular fall beneath the detection floor more readily than narrow features (e.g., PAH 3.3). While certain broad features such as PAH 7.7, 8.6, and 17 may be present below our detection threshold, we can directly estimate this missing power using known templates. This estimation, detailed in Appendix [8](#sec:no_pah), yields an upper limit for the total PAH flux $\Sigma$PAH$_\mathrm{UL}$ being 2.81$\times$ of $\Sigma$PAH$_\mathrm{IIZw40}$.

# Results

The Field of View (FoV) of the dithered JWST NIRSpec and MIRI IFU observations provides complete coverage of the two main SSCs (SSC-N and SSC-S) in II Zw 40, allowing for high spatial and spectral resolution in resolving dust and star-formation properties on a scale of a few tens of pc. As mentioned in §[3](#sec:analysis), the total IFU spectrum was extracted with a radius of 1.6$''$, as indicated by the dashed line in Figure [1](#fig:IIZw40_img)(b), encompassing the largest aperture size that fits within the FoV.

The extracted spectrum, presented in Figure [2](#fig:tot_spec)(a), is dominated by hot dust continuum underlying strong atomic emission lines, with relatively faint PAH emission appearing atop the continuum. Among these PAH features, the 3.3 $\mu$m band exhibits the greatest contrast to the continuum. Panels (b)–(d) show the continuum-subtracted profiles of the 3.3, 6.2, and 11.3 $\mu$m bands, with dotted horizontal lines indicating the zero baseline. The dashed lines represent the modified 1C template from (cite: Lai2020), featuring the continuum-subtracted PAH and aliphatic emission, scaled to match the 3.3 $\mu$m PAH flux in II Zw 40. This template, derived from low spectral resolution AKARI and Spitzer spectra, exhibits a broader width primarily due to its lower spectral resolution of R$\sim$120. Both the 6.2 and 11.3 $\mu$m PAH profiles appear weaker than the reference starburst template, suggesting a PAH power shift toward PAH 3.3. Within the II Zw 40 spectrum, only the 3.3, 6.2, and 11.3 $\mu$m PAH features are robustly detected.

A suite of atomic and rotational H$_\mathrm{2}$ lines can also be seen. Notably, we detected the \[O IV\] line at 25.89 $\mu$m, which typically traces AGN activity (cite: Genzel2000; Peeters2004a; LaMassa2010) but can also appear in environments with intense star formation (cite: Hunt2006), particularly in the presence of metal-poor Wolf-Rayet stars (cite: Tarantino2024).

The AKARI+Spitzer spectrum of II Zw 40 from (cite: Lai2020) is shown in Figure [2](#fig:tot_spec)(a). While the overall spectral shapes are in good agreement, JWST’s higher spectral resolution allows for the detection of additional emission lines. In particular, the Pf$\delta$ line, which overlaps with the 3.3 $\mu$m PAH band, can now be clearly separated from the PAH feature — a result that was not possible with the lower resolution AKARI spectrum.

In (cite: Lai2020), the blending of 3.3 $\mu$m PAH and Pf$\delta$ was accounted for when estimating the PAH 3.3 flux by subtracting the possible contribution from the Pf$\delta$ line, scaled from Br$\alpha$ assuming Case B conditions. With JWST, we find the 3.3 $\mu$m PAH flux measured in the total extraction is $2.21\times10^{-17}$ W/m$^{2}$, approximately 25% of the 3.3 $\mu$m flux estimated in the AKARI+Spitzer spectrum. This discrepancy is likely due to two reasons. First, the AKARI+Spitzer spectrum essentially probes a region that is more than 10 times larger than our IFU-extracted area[^2]. Second, with the AKARI spectral resolution of R$\sim$120, multiple emission lines were blended. Other bright emission lines, in addition to Pf$\delta$ (e.g. \[Fe II\] at 3.21 $\mu$m), lie close to the PAH 3.3 band and were not fully subtracted in the low-resolution AKARI measurement, resulting in an overestimate of the 3.3 $\mu$m PAH flux.

## Spectral Variation across II Zw 40

With JWST’s enhanced spatial/spectral resolving power, we see that PAH emission varies significantly across the face of II Zw 40. For illustration, Figure [3](#fig:pah33) shows the 3.3 $\mu$m PAH profiles from the SSC-N and SSC-S regions extracted from the orange and blue circles, respectively, indicated in Figure [1](#fig:IIZw40_img)(b). Also included is the star-forming ring spectrum in NGC 7469 (cite: Lai2023), which represents the typical 3.3 $\mu$m profile in galaxies with active star formation. Compared to the NGC 7469 spectrum, II Zw 40 spectra exhibit prominent Pf$\delta$ emission relative to the PAH 3.3 component due to the strong recombination line plus the suppression of the PAH emission. The relative contribution between the 3.3 $\mu$m PAH and the Pf$\delta$ line across the IFU and its photometric implications will be discussed in §[5.2](#sec:synphot).

![](IIZw40_pah33_spec_v4.pdf)

Spectral decomposition using CAFE (cite: Diaz-Santos2025)[^3] is applied to each individual spaxel (with 0.05$''$ width) within the NIRSpec cube, totaling approximately $\sim$5000 spaxels. Figure [4](#fig:IIZw40_maps)(a) presents the 3.3 $\mu$m flux map, with crosses marking the peak emission in both SSCs, providing reference points for subsequent maps. Panels (b) and (c) display the resulting spectral fits, the 3.3 $\mu$m PAH and Pf$\delta$ distributions, respectively. These maps reveal distinct morphologies between the emitters: the 3.3 $\mu$m PAH emission is concentrated at SSC-N with an elongated structure, whereas the Pf$\delta$ emission appears more rounded and diffuse. The bar-like distribution of the 3.3 $\mu$m PAH emission emerges only after isolating the PAH component through spectral decomposition. This PAH emission correlates well with the CO (3-2) emission from ALMA (ID: 2012.1.00984.S; PI: A. Kepley), indicating the co-spatiality of PAHs and CO (cite: Shivaei2024; Chown2025_PAH_CO; Shim2025). This co-spatiality suggests that shielding from the molecular gas is likely conducive to the survival of these small PAHs, protecting them from destruction by the radiation field. The contours of the neon ratios (\[Ne III\]/\[Ne II\]) from the MIRI observation are also included in Panel (b). The morphological correspondence between the bend in the 3.3 $\mu$m PAH emission map and the neon emission is reminiscent of blisters at the edge of H II regions. The grayscale background and the contours in Panel (c) are from H$\alpha$ emission observed by HST (ID: 9739; PI: R. Chandar). We see the $\mathrm{Pf}\,\delta$ emission agrees well with the H$\alpha$ emission. For Panel (d), the map shows the ratios of $\mathrm{Pf}\,\delta$ to 3.3 $\mu$m PAH, and the contours are from PAH 3.3 (Panel (b)). As opposed to main sequence star-forming galaxies, which have relatively weak $\mathrm{Pf}\,\delta$ emission relative to 3.3 $\mu$m PAH emission (e.g., the ratio of $\mathrm{Pf}\,\delta$ to PAH 3.3 in the star-forming ring of NGC 7469 is $\sim$0.01), II Zw 40 exhibits a high $\mathrm{Pf}\,\delta$/PAH 3.3 ratio, reaching $\sim$2 in regions close to the illuminated stars, coinciding with the peak in the \[Ne III\]/\[Ne II\] contour that traces radiation field hardness.

![](IIZw40_maps_1.pdf)

![](Ne_pah113_pah33_v7.pdf)

## Resolving PAH band ratios in II Zw 40

In this section, we focus on the results carried out by the combined NIRSpec and MIRI cubes. As pointed out in §[3](#sec:analysis), we are able to extract eight independent spectra from the combined cubes that span a wavelength range of 2.87—27.90 $\mu$m. For all eight spectra, the most prominent PAH band detected is the 3.3 $\mu$m PAH feature, whereas other PAH bands at longer wavelengths are weak and hardly distinguishable from the underlying continuum, which rises steeply to the red.

We compare the PAH ratios derived from each spectrum with the neon line ratios measured by MIRI/MRS, with the results in Figure [5](#fig:Ne_pah_ratio). The four symbols in the figure represent the combined ratios of PAH (and aliphatic) bands relative to the \[Ne III\]/\[Ne II\] ratio, which is used primarily as a diagnostic of the radiation field hardness, albeit with a secondary dependence on the ionization parameter (cite: Thornley2000; Forster_Schreiber2001). Here the \[Ne III\]/\[Ne II\] ratio reaches as high as 35 in cell 8-8, a factor of 1.75 higher than the maximum seen with Spitzer/IRS (cite: Hao2009), likely due to the higher spatial resolution in the JWST data.

The PAH ratios are expressed as short-to-long wavelength ratios, where a higher value indicates a smaller PAH size distribution and a lower value corresponds to larger PAH sizes (cite: Schutte1993). The 3.3/11.3 ratio exhibits a strong correlation (Pearson r=-0.92) to \[Ne III\]/\[Ne II\], while other ratios show no significant variation. The high correlation coefficient between the \[Ne III\]/\[Ne II\] line flux ratio and 3.3/11.3 suggests that the radiation field is correlated with the PAH sizes in II Zw 40, since this PAH ratio is a strong tracer of average PAH size (cite: Croiset2016; Maragkoudakis2020). While this finding is consistent with previous studies that support the photodestruction of PAHs in metal-poor environments (cite: Madden2006; Wu2006; Gordon2008; Hunt2010), it is worth noting that no 17 $\mu$m PAH emission, which is typically associated with the largest PAH populations, is detected in II Zw 40.

While the aromatic-to-aliphatic ratio is known to decrease with increasing intensity and hardness of the radiation field (cite: Joblin1996; Pilleri2015; Lai2023; Peeters2024; Chown2024), in this case, no significant correlation was observed with the \[Ne III\]/\[Ne II\] ratio. Further investigation into its cause requires additional observations of aliphatic features in dwarf galaxies. The plateau feature centered at $\sim$3.47 $\mu$m appears only in two cells, 8-10 and 9-10, which have relatively low \[Ne III\]/\[Ne II\] ratios and are co-spatial with the CO molecular cloud that provides additional shielding. This lack of detection of the broad 3.47 $\mu$m plateau suggests that this feature disappears more readily than the 3.3 and 3.4 $\mu$m bands as radiation hardness increases.

![](pah33_totPAH_Ne_v10_with_limits_withanno.pdf)

# Discussion

The smallest condensed dust grains, while emitting only a tiny share of a galaxy’s total dust luminosity, are in many ways the most responsive to their environments. Thanks to their tiny heat capacities, they are uniquely sensitive to the effects of destruction by photons, elevated radiation intensity and changes in mean photon energy, and may form the building blocks for growing larger grains through coagulation. Here we discuss how these competing effects may operate in galaxies like II Zw 40.

## Tug-of-war: Competing Mechanisms that Shape PAHs in II Zw 40

The influence of metallicity on the life cycle of PAHs has been a subject of investigation for decades, particularly with Spitzer spectroscopy, which provided access to prominent PAH bands longward of 5 $\mu$m. (cite: Hunt2010) examined 22 blue compact dwarfs (BCDs) and identified a significant deficit—exceeding an order of magnitude—in PAH emission relative to total infrared luminosity in low-metallicity dwarfs compared to metal-rich star-forming galaxies. The authors attributed this deficit of PAHs to their destruction by intense, hard radiation fields. Similar conclusions were drawn by other studies, which identified photodissociation as the dominant mechanism processing PAH grains in low-metallicity environments (cite: Martin-Hernandez2002; Madden2006). Yet, observations of normal star-forming galaxies in SINGS (cite: Kennicutt2003) noted the suppression of large-grains towards lower metallicity (cite: Smith2007), and star-forming regions in the Small Magellanic Cloud revealed a shift in PAH size distribution toward smaller grains, challenging the idea that radiation-driven PAH destruction is the dominant effect (cite: Sandstrom2012). Instead, the authors argued that differences in PAH formation at low metallicity primarily govern PAH size distribution. Mid-infrared spectroscopic maps of nearby galaxies from Spitzer combined with detailed grain modeling have further supported this perspective (cite: Whitcomb2024). More recently, JWST IFU observations of 30 Doradus reached a similar conclusion, showing that PAHs in this low-metallicity environment tend to be smaller than those in the Orion Bar (cite: Zhang2024). Indeed, if photo-destruction were the dominant mechanism, the presence of 3.3 $\mu$m emission would be unexpected, as its carriers, which represent the smallest PAH population, are thought to be the most vulnerable to photo-processing. Nevertheless, recurrent fluorescence could be a plausible mechanism to enhance the survival of these small molecules by providing extremely efficient energy dissipation pathways (cite: Leger1988; Lai2017; Draine2021).

### PAH Formation and Destruction in Low Metallicity Environments

It is now possible to study PAH emission, in particular the 3.3 $\mu$m PAH feature, in low-metallicity galaxies at unprecedented sensitivity with JWST, providing a comprehensive understanding of the size distribution in low-metal systems via the 3.3/11.3 ratio (cite: Maragkoudakis2020). Figure [5](#fig:Ne_pah_ratio) exhibits a 3.3/11.3 PAH ratio ranging from $\sim$0.13—0.42, corresponding to PAH molecules with $\sim$70—150 carbon atoms (cite: Croiset2016; Maragkoudakis2020; Rigopoulou2021). This ratio reveals a strong correlation between the neon ratio and PAH 3.3/11.3 in II Zw 40  suggesting small PAHs are photo-processed as they approach the bright H II regions. However, this top-down scenario cannot fully explain two critical observations in II Zw 40: the absence of the 17 $\mu$m PAH band, which typically traces the largest PAH population, and the unexpectedly strong presence of the 3.3 $\mu$m relative to the longer wavelength PAH bands that trace larger grains. Photodissociation is clearly not the dominant mechanism determining the size distribution of PAHs in II Zw 40. If it were, the grains traced by the 3.3 $\mu$m band should be the *first* to disappear, leaving only the largest PAH populations. Other mechanisms must be at play in II Zw 40.

Following the analysis presented in (cite: Lai2023), we study the comparison between the PAH and neon ratios and how they compare to star-forming and photodissociation regions in NGC 7469 (cite: Lai2023) and the Orion Bar (cite: Chown2024; Peeters2024). As shown in Figure [6](#fig:pah33_totPAH_Ne)(d), the total PAH emission ($\Sigma$PAH) in II Zw 40, when normalized to the \[Ne II\]+\[Ne III\] flux, is more than an order of magnitude lower than in the NGC 7469 and the Orion Bar, which agrees with the observations in (cite: Hunt2010) where the average of $\Sigma$PAH/TIR in the BCDs is $\sim$0.5% (it is closer to $\sim$10% in metal-rich star-forming galaxies). While total PAH emission is low in II Zw 40 compared to high-metallicity starburst galaxies, the 3.3 $\mu$m PAH is less suppressed (see Panel (e)), leading to an elevated fractional 3.3 $\mu$m PAH strength (PAH 3.3/$\Sigma$PAH) as shown in Panel (f).

In some regions with moderate neon ratios (\[Ne III\]/\[Ne II\]$\lesssim$30), the fractional PAH 3.3 strength can reach values as high as $\sim$10%. These elevated PAH 3.3/$\Sigma$PAH ratios agree well with the predictions of the *inhibited growth model* proposed by (cite: Whitcomb2024), which showed that fractional 3.3 $\mu$m PAH power can reach a factor of $\sim$3–4 higher than the typical solar metallicity values as indicated by the contours in Figure 4 of (cite: Lai2023). These projections have been confirmed in new NIRCam measurements of 3.3 $\mu$m emission in M101, which show 3.3/$\Sigma$PAH ratios in the range of 5—10% (Whitcomb et al., in prep.).

An additional test was conducted to validate the 3—6% lower limit of PAH 3.3/$\Sigma$PAH, as depicted in Figure [6](#fig:pah33_totPAH_Ne)(c). By scaling a PAH-metallicity model spectrum ($Z = 0.25\,Z_{\odot}$) from Whitcomb et al. (in prep.) to match the observed PAH 6.2  $\mu$m flux, we recalculated $\Sigma$PAH to estimate upper limits that account for missing PAH features. The resulting PAH 3.3/$\Sigma$PAH ratios, ranging from 3–7% across all spatial cells, are in good agreement with the quoted lower limits (lower envelope of the shaded region). These two independent and conservative estimates collectively indicate no relative decrease in PAH 3.3 when compared to star-forming region references.

Taken together, these observations reveal that the PAH size distribution in II Zw 40 shows a marked shift toward smaller molecules compared to typical star-forming regions. Although the fractional strength of the 3.3 $\mu$m PAH to total PAH emission can vary considerably when taking into account the limits, spanning from approximately 3% to 17% in this spatially resolved study, there is *no* evidence that small PAH molecules are the first to vanish in metal-poor environments. On the contrary, these tiniest of grains appear to be robust. Therefore, we conclude that inhibited growth may also play a key role in shaping the PAH size distribution. The influence of photo-processing of the smallest grain cannot, however, be fully dismissed, as evidenced by the tight 3.3/11.3-to-\[Ne III\]/\[Ne II\] correlation seen in Figure [5](#fig:Ne_pah_ratio), where the ISM is resolved on a 20 pc scale. II Zw 40, with its metallicity of approximately 0.25 Z$_{\odot}$, provides a unique opportunity to observe the interplay and competition between the top-down and bottom-up evolution path of PAHs, as galaxies with even lower metallicity might not show the presence of PAHs even with JWST (cite: Telford2024; Mingozzi2025). This underscores the value of studying PAH properties in galaxies with intermediate metallicities, where these effects are more evident.

### Small-PAH Imposter: PAH with double photon heating

In addition to the two mechanisms discussed above which can alter the PAH size distribution, an alternative explanation for the disappearance of the 17 $\mu$m PAH feature together with the enhanced 3.3 $\mu$m PAH emission is a power shift from long to short wavelengths in large PAH molecules when exposed to intense radiation fields with $U \gtrsim 300$ (cite: Draine2021). In such a high-$U$ environment, a large PAH grain can behave like a small-PAH “impostor" by absorbing an additional UV photon before fully cooling, thereby shifting its emission toward shorter wavelengths. The radiation field intensity in SSC-N is exceptionally high, with $U \sim 76{,}000$, corresponding to a Habing unit of G$_\mathrm{0}$$\sim 8.6 \times 10^4$ (see Appendix [9](#sec:radiation_field) for details). This level of radiation is consistent with the $U$ value at which the 17 $\mu$m-to-total IR flux ratio reaches a minimum before its rise due to the second peak associated with a bimodal PAH size distribution (cite: Draine2021). In other words, a substantial portion of the power that would have been emitted at 17 $\mu$m is instead redistributed to shorter-wavelength emission. The extreme radiation field in SSC-N could therefore account for the absence of the 17 $\mu$m PAH feature and the strong emission at 3.3 $\mu$m in II Zw 40.

![](IIZw40_phot_pah33.pdf)

## Probing 3.3 $\mu$m PAHs Photometrically in Dwarfs

Various methods have been developed to recover the 3.3 $\mu$m PAH photometrically using the NIRCam filters (cite: Sandstrom2023; Bolatto2024; Gregg2024). With our NIRSpec spectroscopy, we compare synthetic photometry derived from three NIRCam filters (F300M, F335M, and F360M) using the `pyphot` software (cite: Morgan2025) with spectroscopically fitted 3.3 $\mu$m PAH fluxes. This comparison, illustrated in Figure [7](#fig:pah33_synphot)(*top panel*), incorporates all spaxels within the total extraction region shown in Figure [1](#fig:IIZw40_img)(b), and evaluates how effectively 3.3 $\mu$m PAH emission can be recovered through photometric methods. Each point represents measurements from a single spaxel with a width of 0.05$''$, with the corresponding surface brightness on the top axis. The empirical formula for probing 3.3 $\mu$m PAH flux as established by (cite: Lai2020) can be written as $$\begin{equation}
    \bigg(\frac{f_\mathrm{PAH \ 3.3}}{10^{-17} \ \mathrm{W m^{-2}}}\bigg) = (10.78 \ \pm \ 0.44) \cdot x, 
\end{equation}$$ where $$\begin{equation}
    x = \mathrm{F335M} - (0.35\times\mathrm{F300M} + 0.65\times\mathrm{F360M}) \ \mathrm{[mJy]}.
\end{equation}$$ This relationship is indicated by the red line, and each point in the figure is color-coded by the ratio of PAH 3.3 / (PAH 3.3 + Pf$\delta$) in each spaxel. Notably, points with relatively higher contributions from the 3.3 $\mu$m PAH align closely with the empirical line. As the $\mathrm{Pf}\,\delta$ contribution to the F335M filter increases, points progressively deviate from the established relationship. This observation supports our prediction, as the empirical relationship was derived from a set of starburst galaxies that exhibit relatively minimal $\mathrm{Pf}\,\delta$ emission (similar to the NGC 7469 ring spectrum shown in Figure [3](#fig:pah33)). In contrast, we find the 5—95% range of PAH 3.3 / ($\mathrm{Pf}\,\delta$+PAH 3.3) is 54—89%, indicating that $\mathrm{Pf}\,\delta$ can account for approximately 10—50% of the residual power after continuum subtraction in F335M. Therefore, caution should be exercised when probing 3.3 $\mu$m PAH emission with photometry in dwarfs, particularly in highly ionized environments. One potential approach to mitigate contamination from $\mathrm{Pf}\,\delta$ is to obtain observations of additional recombination lines, such as Pa$\alpha$ and Br$\alpha$, using the F187N and F405N narrow-band filters, although this may require substantial observing time.

To further understand how accurately the 3.3 $\mu$m PAH flux can be recovered photometrically, we divide the CAFE-measured PAH 3.3 flux by the empirical relationship (Figure [7](#fig:pah33_synphot) bottom panel) and bin the data according to surface brightness. Most points show ratios larger than unity because the artificial continuum level derived from the F300M and F360M filters is likely overestimated in most cases due to the numerous strong emission lines present within the filters, as shown in the inset of Figure [7](#fig:pah33_synphot)(top panel). Based on the binning results, we show that the photometric method can recover the 3.3 $\mu$m PAH flux within 50% of the “true" value when the continuum-subtracted F335M surface brightness is greater than 0.1 MJy/sr in II Zw 40. The precision of using NIRCam filters to probe PAH 3.3 deteriorates drastically (uncertainty increases 2—3$\times$) below the 0.1 MJy/sr threshold. We emphasize that these findings are specific to II Zw 40 and anticipate that in galaxies with even lower metallicity, deviations from the empirical trend will occur at even higher surface brightness thresholds. Fully understanding how this trend varies with metallicity will thus require additional observations.

# Summary

In this paper, we present a study of resolved PAH emission on $\sim$20 pc scales in II Zw 40, a BCD with metallicity of 25% of solar, using JWST NIRSpec and MIRI. In particular, we focus on pinpointing the location of strong PAH emission and the relation between PAH emission and the local radiation field. Our findings can be summarized as follows:

- Despite its continuum-dominated spectrum, II Zw 40 shows clear PAH emission at 3.3, 6.2, and 11.3 $\mu$m, with a notable PAH power shift favoring the shortest PAH band at 3.3 $\mu$m. We detect the aliphatic feature at 3.4 $\mu$m, together with atomic fine-structure lines including \[Fe II\] (3.21 $\mu$m) and \[O IV\] (25.88 $\mu$m), as well as various H$_\mathrm{2}$ transitions (Figure [2](#fig:tot_spec)). II Zw 40 also exhibits a strong $\mathrm{Pf}\,\delta$ recombination line at $\sim$3.3 $\mu$m easily detected against the 3.3 PAH emission, in contrast to that seen in typical star-forming galaxies where the PAH feature dominates this part of the spectrum (Figure [3](#fig:pah33)). The 3.47 $\mu$m broad plateau feature seen in many star-forming systems is mostly absent from the II Zw 40 spectrum, possibly as a result of processing by the hard radiation field.

- A 3.3 $\mu$m PAH map shows most of the PAH emission in II Zw 40 is concentrated near the northern super star cluster (SSC), spatially coincident with the CO emission detected by ALMA (Figure [4](#fig:IIZw40_maps)). Molecular gas likely provides shielding to these small PAH molecules in this region.

- There is a strong spatial correlation of the \[Ne III\]/\[Ne II\] and 3.3/11.3 PAH ratios, suggesting a destruction of small grains by UV photons in regions with the hardest radiation fields (Figure [5](#fig:Ne_pah_ratio)). However, we find *no* evidence that the smallest PAH population is being preferentially destroyed throughout II Zw 40. In fact, the 3.3 $\mu$m PAH band appears substantially enhanced compared to longer-wavelength bands, resulting in fractional PAH 3.3 strength (PAH 3.3 / $\Sigma$PAH) approaching 10% or more (Figure [6](#fig:pah33_totPAH_Ne)), significantly higher than seen in other star-forming environments. We propose that the PAH size distribution in II Zw 40 is shaped by two mechanisms: photo-processing (top-down) and inhibited growth (bottom-up). In addition, double photon heating might be contributing to the strength of the 3.3 PAH feature in II Zw 40 due to its extremely high radiation field intensity (log$U\sim$5).

- The apparent 3.3 $\mu$m PAH flux derived from NIRCam F335M photometry can be strongly affected by the presence of the $\mathrm{Pf}\,\delta$ emission line and other strong emission lines within the flanking F300M and F360M filters. We find that the photometric method can recover the 3.3 $\mu$m PAH flux within 50% when the continuum-subtracted F335M surface brightness exceeds 0.1 MJy/sr, but can substantially under-predict the true 3.3 $\mu$m PAH flux at lower surface brightness levels (Figure [7](#fig:pah33_synphot)).

Future JWST observations of additional BCD galaxies, particularly those with intermediate metallicities similar to II Zw 40, will be crucial for establishing a more comprehensive understanding of PAH evolution.

# Software and third party data repository citations

# Software

Astropy (cite: Astropy2013; Astropy2018; astropy2022), CAFE (cite: Marshall2007; Diaz-Santos2025), *JWST* Science Calibration Pipeline (cite: Bushouse2022), lmfit (cite: Newville2014), Matplotlib (cite: Hunter2007), Numpy (cite: VanderWalt2011; Harris2020), pyphot (cite: Morgan2025), SciPy (cite: Virtanen2020)

The authors thank the anonymous referee for providing useful comments and suggestions. T.S.-Y.L. acknowledges funding support from NASA grant JWST-2511. This work was carried out in part at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with the National Aeronautics and Space Administration. This work was performed in part at the Aspen Center for Physics, which is supported by National Science Foundation grant PHY-2210452. MI acknowledges the support by JSPS KAKENHI Grant Numbers 21K03632 and 25K07359. TN acknowledges the support by JSPS KAKENHI Grant Numbers 23H05441 and 23K17695.

# Facilities

*JWST* (NIRSpec & MIRI), MAST, NED

# Software

Astropy (cite: Astropy2013; Astropy2018; astropy2022), CAFE (cite: Marshall2007), *JWST* Science Calibration Pipeline (cite: Bushouse2022), lmfit (cite: Newville2014), Matplotlib (cite: Hunter2007), Numpy (cite: VanderWalt2011; Harris2020), SciPy (cite: Virtanen2020)

# The apparent absence of 7.7, 8.6, and 17 $\mu$m PAH

To illustrate the absence of PAH features at 7.7, 8.6, and 17 $\mu$m, Figure [8](#fig:no_PAH) presents spectral zoom-ins of these ranges. The left panel shows the wavelength range between 5.0–9.5 $\mu$m. For a fair comparison between the observed spectrum and the 1C PAH template from (cite: Lai2020) (as shown in Figure [2](#fig:tot_spec)), we overlay the template onto a *pseudo-continuum* (gray) defined by a power law based on two pivot points at 5.0 and 9.8 $\mu$m, wavelengths where PAH emission contributes minimally in this spectral regime. After scaling the template based on the detected 6.2 $\mu$m PAH band, the observed spectrum shows no resemblance to the template at 7.7 and 8.6 $\mu$m, indicating no detectable emission at these wavelengths. This non-detection may be due to dilution by the strong hot dust continuum. The right panel examines the 17 $\mu$m range based on the same approach, with a power law continuum pivoting at 15.6 and 19.0 $\mu$m. Despite arbitrary scaling of the PAH profile, the spectrum aligns closely with the continuum (gray), revealing no evidence of the 17 $\mu$m PAH feature.

In Figure [6](#fig:pah33_totPAH_Ne), $\Sigma$PAH denotes the sum of the PAH features at 3.3, 6.2, 7.7, 8.6, 11.3, and 17 $\mu$m, which typically accounts for $>$90% of the PAH flux in star-forming galaxies. However, in the case of II Zw 40, only the 3.3, 6.2, and 11.3 $\mu$m features are robustly detected as discussed in §[4](#sec:Results). We define $\Sigma$PAH$_\mathrm{IIZw40}$ to refer specifically to the sum of these three detected features, which we treat as a lower limit for the total PAH emission. To account for the missing contributions from the undetected features, we derive an upper limit on the total PAH flux ($\Sigma$PAH$_\mathrm{UL}$) by estimating the 3$\sigma$ integrated fluxes of the 7.7, 8.6, and 17 $\mu$m bands in the total extracted spectrum. This upper limit is then scaled and applied uniformly across individual spatial cells using a fixed $\Sigma$PAH$_\mathrm{UL}$/$\Sigma$PAH$_\mathrm{IIZw40}$ ratio.

Here, $\sigma$ is defined as the product of the PAH profile’s width and the root mean square (RMS) of the residuals after subtracting a 3rd order polynomial fit from the local continuum, where no PAH band and emission line can be seen in the spectrum. Specifically, for the 7.7 and 8.6 $\mu$m features, the RMS is measured over the 9.68—10.43 $\mu$m continuum range, yielding 0.68 mJy. For the 17 $\mu$m feature, the RMS derived from the 18.15–18.50 $\mu$m region is 1.93 mJy. The width of each PAH band is defined as the interval spanning one FWHM, centered on the central wavelength reported in (cite: Smith2007). For PAH complexes comprising multiple sub-features such as the 7.7 and 11.3 $\mu$m bands, the integration range extends from half an FWHM below the bluest sub-feature to half an FWHM above the reddest sub-feature. The resulting ratio of $\Sigma$PAH$_\mathrm{UL}$/$\Sigma$PAH$_\mathrm{IIZw40}$ is 2.81.

![](IIZw40_no_PAH_proof.pdf)

# Estimate of the radiation field

The intensity of interstellar ultraviolet (UV) radiation is often expressed in units of the Habing field (G$_\mathrm{0}$). Below, we outline the steps used to derive G$_\mathrm{0}$ for SSC-N.

We adopt the dereddened far-UV (FUV) spectrum of SSC-N from (cite: Leitherer2018), which shows a relatively smooth continuum between 1200–1700 Å. Since this spectral coverage does not extend over the full range required to compute G$_\mathrm{0}$, we extrapolate the spectrum linearly to span 912–2400 Å for the flux integration. The resulting FUV flux is $$F_{FUV} = 1.38 \times 10^{-10}~\mathrm{erg~s^{-1}~cm^{-2}}.$$ Assuming the distance to II Zw 40 of $D$=10 Mpc, we estimate the total FUV luminosity to be $$L_{FUV}=4\pi D^2 F_{FUV} \approx 1.65 \times 10^{42}~\mathrm{erg~s^{-1}}.$$ Further, assuming the cluster radius of $R$=10 pc (cite: Leitherer2018), the local FUV flux at 10 pc from the cluster can be written as $$F_{local}=\frac{L_{FUV}}{4\pi R^2} \approx 138~\mathrm{erg~s^{-1}~cm^{-2}}.$$ Therefore, $$\begin{equation}
    G_{0} = \frac{F_\mathrm{local}}{F_\mathrm{Habing}} = \frac{138}{1.6 \times 10^{-3}} \approx 8.6 \times 10^{4}.
\end{equation}$$

Using the relation $U = 0.88 \times G_0$ (cite: Draine2007b), this corresponds to a radiation field parameter of $$U = 75{,}680,\quad \text{or} \quad \log U \approx 4.88.$$

natexlab

(ref: Astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: astropy2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Beilis2024) Beilis, D., Beck, S. C., Lacy, J., et al. 2024, MNRAS, 535, 1052, doi: [`10.1093/mnras/stae2447`](http://doi.org/10.1093/mnras/stae2447)

(ref: Bergeron1977) Bergeron, J. 1977, ApJ, 211, 62, doi: [`10.1086/154903`](http://doi.org/10.1086/154903)

(ref: Boker2022) Böker, T., Arribas, S., Lützgendorf, N., et al. 2022, A&A, 661, A82, doi: [`10.1051/0004-6361/202142589`](http://doi.org/10.1051/0004-6361/202142589)

(ref: Bolatto2024) Bolatto, A. D., Levy, R. C., Tarantino, E., et al. 2024, ApJ, 967, 63, doi: [`10.3847/1538-4357/ad33c8`](http://doi.org/10.3847/1538-4357/ad33c8)

(ref: Bushouse2022) Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2022, , 1.6.2 Zenodo, doi: [`10.5281/zenodo.6984366`](http://doi.org/10.5281/zenodo.6984366)

(ref: Chown2024) Chown, R., Sidhu, A., Peeters, E., et al. 2024, A&A, 685, A75, doi: [`10.1051/0004-6361/202346662`](http://doi.org/10.1051/0004-6361/202346662)

(ref: Chown2025_WLM) Chown, R., Leroy, A. K., Bolatto, A. D., et al. 2025a, arXiv e-prints, arXiv:2504.08069, doi: [`10.48550/arXiv.2504.08069`](http://doi.org/10.48550/arXiv.2504.08069)

(ref: Chown2025_PAH_CO) Chown, R., Leroy, A. K., Sandstrom, K., et al. 2025b, ApJ, 983, 64, doi: [`10.3847/1538-4357/adbd40`](http://doi.org/10.3847/1538-4357/adbd40)

(ref: Consiglio2016) Consiglio, S. M., Turner, J. L., Beck, S., & Meier, D. S. 2016, ApJL, 833, L6, doi: [`10.3847/2041-8205/833/1/L6`](http://doi.org/10.3847/2041-8205/833/1/L6)

(ref: Cormier2015) Cormier, D., Madden, S. C., Lebouteiller, V., et al. 2015, A&A, 578, A53, doi: [`10.1051/0004-6361/201425207`](http://doi.org/10.1051/0004-6361/201425207)

(ref: Croiset2016) Croiset, B. A., Candian, A., Berné, O., & Tielens, A. G. G. M. 2016, A&A, 590, A26, doi: [`10.1051/0004-6361/201527714`](http://doi.org/10.1051/0004-6361/201527714)

(ref: DeVis2019) De Vis, P., Jones, A., Viaene, S., et al. 2019, A&A, 623, A5, doi: [`10.1051/0004-6361/201834444`](http://doi.org/10.1051/0004-6361/201834444)

(ref: Diaz-Santos2025) Diaz-Santos, T., Lai, T. S. Y., Finnerty, L., et al. 2025, , Astrophysics Source Code Library, record ascl:2501.001

(ref: Draine2021) Draine, B. T., Li, A., Hensley, B. S., et al. 2021, ApJ, 917, 3, doi: [`10.3847/1538-4357/abff51`](http://doi.org/10.3847/1538-4357/abff51)

(ref: Draine2007b) Draine, B. T., Dale, D. A., Bendo, G., et al. 2007, ApJ, 663, 866, doi: [`10.1086/518306`](http://doi.org/10.1086/518306)

(ref: Engelbracht2005) Engelbracht, C. W., Gordon, K. D., Rieke, G. H., et al. 2005, ApJL, 628, L29, doi: [`10.1086/432613`](http://doi.org/10.1086/432613)

(ref: Engelbracht2008) Engelbracht, C. W., Rieke, G. H., Gordon, K. D., et al. 2008, ApJ, 678, 804, doi: [`10.1086/529513`](http://doi.org/10.1086/529513)

(ref: Forster_Schreiber2001) Förster Schreiber, N. M., Genzel, R., Lutz, D., Kunze, D., & Sternberg, A. 2001, ApJ, 552, 544, doi: [`10.1086/320546`](http://doi.org/10.1086/320546)

(ref: Morgan2025) Fouesneau, M. 2025, , pyphot_v1.6.0 Zenodo, doi: [`10.5281/zenodo.14712174`](http://doi.org/10.5281/zenodo.14712174)

(ref: Galliano2008) Galliano, F., Dwek, E., & Chanial, P. 2008, ApJ, 672, 214, doi: [`10.1086/523621`](http://doi.org/10.1086/523621)

(ref: Galliano2005) Galliano, F., Madden, S. C., Jones, A. P., Wilson, C. D., & Bernard, J. P. 2005, A&A, 434, 867, doi: [`10.1051/0004-6361:20042369`](http://doi.org/10.1051/0004-6361:20042369)

(ref: Genzel2000) Genzel, R., & Cesarsky, C. J. 2000, ARA&A, 38, 761, doi: [`10.1146/annurev.astro.38.1.761`](http://doi.org/10.1146/annurev.astro.38.1.761)

(ref: Gordon2008) Gordon, K. D., Engelbracht, C. W., Rieke, G. H., et al. 2008, ApJ, 682, 336, doi: [`10.1086/589567`](http://doi.org/10.1086/589567)

(ref: Gregg2024) Gregg, B., Calzetti, D., Adamo, A., et al. 2024, ApJ, 971, 115, doi: [`10.3847/1538-4357/ad54b4`](http://doi.org/10.3847/1538-4357/ad54b4)

(ref: Guseva2000) Guseva, N. G., Izotov, Y. I., & Thuan, T. X. 2000, ApJ, 531, 776, doi: [`10.1086/308489`](http://doi.org/10.1086/308489)

(ref: Hao2009) Hao, L., Wu, Y., Charmandaris, V., et al. 2009, ApJ, 704, 1159, doi: [`10.1088/0004-637X/704/2/1159`](http://doi.org/10.1088/0004-637X/704/2/1159)

(ref: Harris2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Haynes2010) Haynes, K., Cannon, J. M., Skillman, E. D., Jackson, D. C., & Gehrz, R. 2010, ApJ, 724, 215, doi: [`10.1088/0004-637X/724/1/215`](http://doi.org/10.1088/0004-637X/724/1/215)

(ref: Henkel2022) Henkel, C., Hunt, L. K., & Izotov, Y. I. 2022, Galaxies, 10, 11, doi: [`10.3390/galaxies10010011`](http://doi.org/10.3390/galaxies10010011)

(ref: Hirschauer2024) Hirschauer, A. S., Crouzet, N., Habel, N., et al. 2024, AJ, 168, 23, doi: [`10.3847/1538-3881/ad4967`](http://doi.org/10.3847/1538-3881/ad4967)

(ref: Hunt2010) Hunt, L. K., Thuan, T. X., Izotov, Y. I., & Sauvage, M. 2010, ApJ, 712, 164, doi: [`10.1088/0004-637X/712/1/164`](http://doi.org/10.1088/0004-637X/712/1/164)

(ref: Hunt2006) Hunt, L. K., Thuan, T. X., Sauvage, M., & Izotov, Y. I. 2006, ApJ, 653, 222, doi: [`10.1086/508867`](http://doi.org/10.1086/508867)

(ref: Hunt2025) Hunt, L. K., Aloisi, A., Navarro, M. G., et al. 2025, arXiv e-prints, arXiv:2508.09251, doi: [`10.48550/arXiv.2508.09251`](http://doi.org/10.48550/arXiv.2508.09251)

(ref: Hunter2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Joblin1996) Joblin, C., Tielens, A. G. G. M., Allamandola, L. J., & Geballe, T. R. 1996, ApJ, 458, 610, doi: [`10.1086/176843`](http://doi.org/10.1086/176843)

(ref: Kennicutt2003) Kennicutt, Jr., R. C., Armus, L., Bendo, G., et al. 2003, PASP, 115, 928, doi: [`10.1086/376941`](http://doi.org/10.1086/376941)

(ref: Kepley2014) Kepley, A. A., Reines, A. E., Johnson, K. E., & Walker, L. M. 2014, AJ, 147, 43, doi: [`10.1088/0004-6256/147/2/43`](http://doi.org/10.1088/0004-6256/147/2/43)

(ref: Labiano2021) Labiano, A., Argyriou, I., Álvarez-Márquez, J., et al. 2021, A&A, 656, A57, doi: [`10.1051/0004-6361/202140614`](http://doi.org/10.1051/0004-6361/202140614)

(ref: Lai2020) Lai, T. S. Y., Smith, J. D. T., Baba, S., Spoon, H. W. W., & Imanishi, M. 2020, ApJ, 905, 55, doi: [`10.3847/1538-4357/abc002`](http://doi.org/10.3847/1538-4357/abc002)

(ref: Lai2024) Lai, T. S. Y., Smith, J. D. T., Peeters, E., et al. 2024, ApJ, 967, 83, doi: [`10.3847/1538-4357/ad354b`](http://doi.org/10.3847/1538-4357/ad354b)

(ref: Lai2017) Lai, T. S.-Y., Witt, A. N., & Crawford, K. 2017, MNRAS, 469, 4933, doi: [`10.1093/mnras/stx1124`](http://doi.org/10.1093/mnras/stx1124)

(ref: Lai2022) Lai, T. S. Y., Armus, L., U, V., et al. 2022, ApJL, 941, L36, doi: [`10.3847/2041-8213/ac9ebf`](http://doi.org/10.3847/2041-8213/ac9ebf)

(ref: Lai2023) Lai, T. S. Y., Armus, L., Bianchin, M., et al. 2023, ApJL, 957, L26, doi: [`10.3847/2041-8213/ad0387`](http://doi.org/10.3847/2041-8213/ad0387)

(ref: LaMassa2010) LaMassa, S. M., Heckman, T. M., Ptak, A., et al. 2010, ApJ, 720, 786, doi: [`10.1088/0004-637X/720/1/786`](http://doi.org/10.1088/0004-637X/720/1/786)

(ref: Latter1991) Latter, W. B. 1991, ApJ, 377, 187, doi: [`10.1086/170346`](http://doi.org/10.1086/170346)

(ref: Leger1988) Leger, A., D’Hendecourt, L., & Boissel, P. 1988, Physical Review Letters, 60, 921, doi: [`10.1103/PhysRevLett.60.921`](http://doi.org/10.1103/PhysRevLett.60.921)

(ref: Leitherer2018) Leitherer, C., Byler, N., Lee, J. C., & Levesque, E. M. 2018, ApJ, 865, 55, doi: [`10.3847/1538-4357/aada84`](http://doi.org/10.3847/1538-4357/aada84)

(ref: Lenkic2024) Lenkić, L., Nally, C., Jones, O. C., et al. 2024, ApJ, 967, 110, doi: [`10.3847/1538-4357/ad3f90`](http://doi.org/10.3847/1538-4357/ad3f90)

(ref: Li2020) Li, A. 2020, Nature Astronomy, 4, 339, doi: [`10.1038/s41550-020-1051-1`](http://doi.org/10.1038/s41550-020-1051-1)

(ref: Madden2006) Madden, S. C., Galliano, F., Jones, A. P., & Sauvage, M. 2006, A&A, 446, 877, doi: [`10.1051/0004-6361:20053890`](http://doi.org/10.1051/0004-6361:20053890)

(ref: Maragkoudakis2020) Maragkoudakis, A., Peeters, E., & Ricca, A. 2020, MNRAS, 494, 642, doi: [`10.1093/mnras/staa681`](http://doi.org/10.1093/mnras/staa681)

(ref: Marshall2007) Marshall, J. A., Herter, T. L., Armus, L., et al. 2007, ApJ, 670, 129, doi: [`10.1086/521588`](http://doi.org/10.1086/521588)

(ref: Martin-Hernandez2002) Martı́n-Hernández, N. L., Vermeij, R., Tielens, A. G. G. M., van der Hulst, J. M., & Peeters, E. 2002, A&A, 389, 286, doi: [`10.1051/0004-6361:20020528`](http://doi.org/10.1051/0004-6361:20020528)

(ref: McQuinn2024) McQuinn, K. B. W., Newman, M. J. B., Skillman, E. D., et al. 2024, ApJ, 976, 60, doi: [`10.3847/1538-4357/ad8158`](http://doi.org/10.3847/1538-4357/ad8158)

(ref: Mingozzi2025) Mingozzi, M., Garcia Del Valle-Espinosa, M., James, B. L., et al. 2025, arXiv e-prints, arXiv:2502.07662, doi: [`10.48550/arXiv.2502.07662`](http://doi.org/10.48550/arXiv.2502.07662)

(ref: Nally2024) Nally, C., Jones, O. C., Lenkić, L., et al. 2024, MNRAS, 531, 183, doi: [`10.1093/mnras/stae1163`](http://doi.org/10.1093/mnras/stae1163)

(ref: Newville2014) Newville, M., Stensitzki, T., Allen, D. B., & Ingargiola, A. 2014, , 0.8.0 Zenodo, doi: [`10.5281/zenodo.11813`](http://doi.org/10.5281/zenodo.11813)

(ref: Peeters2004a) Peeters, E., Spoon, H. W. W., & Tielens, A. G. G. M. 2004, ApJ, 613, 986, doi: [`10.1086/423237`](http://doi.org/10.1086/423237)

(ref: Peeters2024) Peeters, E., Habart, E., Berné, O., et al. 2024, A&A, 685, A74, doi: [`10.1051/0004-6361/202348244`](http://doi.org/10.1051/0004-6361/202348244)

(ref: Pilleri2015) Pilleri, P., Joblin, C., Boulanger, F., & Onaka, T. 2015, A&A, 577, A16, doi: [`10.1051/0004-6361/201425590`](http://doi.org/10.1051/0004-6361/201425590)

(ref: Remy-Ruyer2014) Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014, A&A, 563, A31, doi: [`10.1051/0004-6361/201322803`](http://doi.org/10.1051/0004-6361/201322803)

(ref: Remy-Ruyer2015) Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2015, A&A, 582, A121, doi: [`10.1051/0004-6361/201526067`](http://doi.org/10.1051/0004-6361/201526067)

(ref: Rieke2015) Rieke, G. H., Wright, G. S., Böker, T., et al. 2015, PASP, 127, 584, doi: [`10.1086/682252`](http://doi.org/10.1086/682252)

(ref: Rigopoulou2021) Rigopoulou, D., Barale, M., Clary, D. C., et al. 2021, MNRAS, 504, 5287, doi: [`10.1093/mnras/stab959`](http://doi.org/10.1093/mnras/stab959)

(ref: Rupke2014) Rupke, D. S. N. 2014, [`http://ascl.net/1409.005`](http://ascl.net/1409.005)

(ref: Rupke2021) Rupke, D. S. N., Schweitzer, M., Viola, V., et al. 2021, [`http://ascl.net/2112.002`](http://ascl.net/2112.002)

(ref: Sandstrom2012) Sandstrom, K. M., Bolatto, A. D., Bot, C., et al. 2012, ApJ, 744, 20, doi: [`10.1088/0004-637X/744/1/20`](http://doi.org/10.1088/0004-637X/744/1/20)

(ref: Sandstrom2023) Sandstrom, K. M., Chastenet, J., Sutter, J., et al. 2023, ApJL, 944, L7, doi: [`10.3847/2041-8213/acb0cf`](http://doi.org/10.3847/2041-8213/acb0cf)

(ref: Sargent1970) Sargent, W. L. W., & Searle, L. 1970, ApJL, 162, L155, doi: [`10.1086/180644`](http://doi.org/10.1086/180644)

(ref: Schutte1993) Schutte, W. A., Tielens, A. G. G. M., & Allamandola, L. J. 1993, ApJ, 415, 397, doi: [`10.1086/173173`](http://doi.org/10.1086/173173)

(ref: Searle1972) Searle, L., & Sargent, W. L. W. 1972, ApJ, 173, 25, doi: [`10.1086/151398`](http://doi.org/10.1086/151398)

(ref: Shim2025) Shim, H., Baek, J., Kim, D., et al. 2025, arXiv e-prints, arXiv:2503.21230, doi: [`10.48550/arXiv.2503.21230`](http://doi.org/10.48550/arXiv.2503.21230)

(ref: Shivaei2024) Shivaei, I., & Boogaard, L. A. 2024, A&A, 691, L2, doi: [`10.1051/0004-6361/202451826`](http://doi.org/10.1051/0004-6361/202451826)

(ref: Smith2007) Smith, J. D. T., Draine, B. T., Dale, D. A., et al. 2007, ApJ, 656, 770, doi: [`10.1086/510549`](http://doi.org/10.1086/510549)

(ref: Tarantino2024) Tarantino, E., Bolatto, A. D., Indebetouw, R., et al. 2024, ApJ, 969, 101, doi: [`10.3847/1538-4357/ad3def`](http://doi.org/10.3847/1538-4357/ad3def)

(ref: Telford2024) Telford, O. G., Sandstrom, K. M., McQuinn, K. B. W., et al. 2024, arXiv e-prints, arXiv:2410.21368, doi: [`10.48550/arXiv.2410.21368`](http://doi.org/10.48550/arXiv.2410.21368)

(ref: Thornley2000) Thornley, M. D., Förster Schreiber, N. M., Lutz, D., et al. 2000, ApJ, 539, 641, doi: [`10.1086/309261`](http://doi.org/10.1086/309261)

(ref: Thuan2008) Thuan, T. X. 2008, in Low-Metallicity Star Formation: From the First Stars to Dwarf Galaxies, ed. L. K. Hunt, S. C. Madden, & R. Schneider, Vol. 255, 348–360, doi: [`10.1017/S1743921308025064`](http://doi.org/10.1017/S1743921308025064)

(ref: Thuan1981) Thuan, T. X., & Martin, G. E. 1981, ApJ, 247, 823, doi: [`10.1086/159094`](http://doi.org/10.1086/159094)

(ref: Tielens2008) Tielens, A. G. G. M. 2008, ARA&A, 46, 289, doi: [`10.1146/annurev.astro.46.060407.145211`](http://doi.org/10.1146/annurev.astro.46.060407.145211)

(ref: VanderWalt2011) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science Engineering, 13, 22

(ref: vanZee1998) van Zee, L., Skillman, E. D., & Salzer, J. J. 1998, AJ, 116, 1186, doi: [`10.1086/300510`](http://doi.org/10.1086/300510)

(ref: Vanzi2008) Vanzi, L., Cresci, G., Telles, E., & Melnick, J. 2008, A&A, 486, 393, doi: [`10.1051/0004-6361:20078885`](http://doi.org/10.1051/0004-6361:20078885)

(ref: Vayner2023) Vayner, A., Zakamska, N. L., Ishikawa, Y., et al. 2023, ApJ, 955, 92, doi: [`10.3847/1538-4357/ace784`](http://doi.org/10.3847/1538-4357/ace784)

(ref: Virtanen2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`https://doi.org/10.1038/s41592-019-0686-2`](http://doi.org/https://doi.org/10.1038/s41592-019-0686-2)

(ref: Whitcomb2024) Whitcomb, C. M., Smith, J. D. T., Sandstrom, K., et al. 2024, arXiv e-prints, arXiv:2405.09685, doi: [`10.48550/arXiv.2405.09685`](http://doi.org/10.48550/arXiv.2405.09685)

(ref: Wu2006) Wu, Y., Charmandaris, V., Hao, L., et al. 2006, ApJ, 639, 157, doi: [`10.1086/499226`](http://doi.org/10.1086/499226)

(ref: Zhang2024) Zhang, C., Hales, J., Peeters, E., et al. 2024, arXiv e-prints, arXiv:2410.18909, doi: [`10.48550/arXiv.2410.18909`](http://doi.org/10.48550/arXiv.2410.18909)

[^1]: NASA/IPAC Extragalactic Database (NED)

[^2]: The AKARI+Spitzer spectrum is drawn from the IDEOS sample which used the Spitzer IRS LL2 (with a slit width of 10$''$) as a reference to stitch the shorter wavelength segments, and the AKARI spectrum was then scaled to match with the IRS spectrum (cite: Lai2020).

[^3]: https://github.com/GOALS-survey/CAFE

</paper>

Write the methods card for this paper.