# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...693A.309S\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...693A.309S",
 "title": "Behind the dust veil: A panchromatic view of an optically dark galaxy at z = 4.82",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Sillassen, Nikolaj B.",
 "n_authors": 33,
 "arxiv_id": "2412.09363",
 "doi": "10.1051/0004-6361/202452932",
 "alma_projects_linked_by_archive": [
  "2021.1.00225.S",
  "2022.1.00863.S",
  "2022.1.00884.S"
 ]
}
```

Paper text:
<paper>
# Behind the dust veil: A panchromatic view of an optically dark galaxy at z=4.82

Optically dark dusty star-forming galaxies (DSFGs) play an essential role in massive galaxy formation at early cosmic time, however their nature remains elusive. Here we present a detailed case study of all the baryonic components of a $z=4.821$ DSFG, XS55. Selected from the ultra-deep COSMOS-XS 3GHz map with a red SCUBA-2 450$\mu$m/850$\mu$m colour, XS55 was followed up with ALMA 3mm line scans and spectroscopically confirmed to be at $z=4.821$ via detections of the CO(5-4) and \[CI\](1-0) lines.

JWST/NIRCam imaging reveals that XS55 is a F150W-dropout with red F277W/F444W colour, and a complex morphology: a compact central component embedded in an extended structure with a likely companion.

XS55 is tentatively detected in X-rays with both Chandra and XMM-Newton, suggesting an active galactic nucleus (AGN) nature. By fitting a panchromatic SED spanning NIR to radio wavelengths, we revealed that XS55 is a massive main-sequence galaxy with a stellar mass of $M_\ast=(5\pm1)\times10^{10}\,{\rm M_\odot}$ and a star formation rate of ${\rm SFR}=540\pm177~{\rm M_\odot\,yr^{-1}}$. The dust of XS55 is optically thick in the far infrared (FIR) with a surprisingly cold dust temperature of $T_{\rm dust}=33\pm2\,{\rm K}$, making XS55 one of the coldest DSFGs at $z>4$ known to date. This work unveils the nature of a radio-selected F150W-dropout, suggesting the existence of a population of DSFGs hosting active black holes embedded in optically thick dust.

# Introduction

Optically faint/dark galaxies are a population of massive dusty star-forming galaxies (DSFGs) that are faint or undetected in deep optical images while bright at longer wavelengths. This population includes but is not limited to the following samples: sub-millimetre galaxies (SMGs) (cite: Walter2012), H-band dropouts (cite: Wang2019Natur; Pampliega2019; Smail2023), Ks-faint (cite: Smail2020), Hubble Space Telescope (HST)-dark/faint galaxies (cite: Franco2018; Perez-Gonzalez2023; Xiao2023_OFGs; Gomez-Guijarro2023), and radio-selected near infrared (NIR) dark galaxies ((cite: Algera2020; Talia2021; Enia2022; vanderVlugt2023_COSMOS_XS; Gentile2024a; Gentile2024)). Recent studies revealed that this population contributes significantly ($10-40\%$) to the cosmic star formation rate density in the early universe ($z\sim3-6$, (cite: Wang2019Natur; Fudamoto2021; Talia2021; Enia2022; Shu2022; Xiao2023_OFGs)), and dominates the massive end of the stellar mass function (SMF) at $z\sim3-8$ (cite: Wang2019Natur; Gottumukkala2024_OFG_SMF). This indicates that this population plays a significant role in cosmic star formation history, even up to 50% estimated from Lyman break galaxy selected samples at $z\sim3$ (cite: Enia2022), but has been largely missed by previous optical/NIR surveys. Thanks to the unprecedented sensitivity and long wavelength coverage, the *James Webb Space Telescope* (JWST) can efficiently detect these objects and allows for detailed studies and large sample census of optically faint galaxies. For example, (cite: Barrufet2023) studied the stellar emission of a sample of 30 HST-dark sources in the CEERS field with red colours through 1.6 – 4.4 ${\rm \mu}$m in JWST NIRCam filters, revealing them all to be heavily dust obscured massive main sequence galaxies and significantly contributing to the star formation rate density at high redshift. In a NIRSpec study of 23 HST-dark galaxies, (cite: Barrufet2024_OFGs) found the majority to be massive ($\log(M_\ast/\mathrm{M_\odot})>9.8$) and highly attenuated ($A_V>2$) star-forming galaxies with a broad range of recent star-formation activities. (cite: Kokorev2023_dustyguy) studied the multi-wavelength properties of an HST-dark galaxy at $z_{\rm spec}=2.58$ with JWST/NIRCam data, revealing it to be a massive disk galaxy with log$(M_{\star}/\mathrm{M_\odot})>11$ and optically thick dust in the far-infrared. They also found that such objects would not be detected in JWST filters bluer than F356W if placed at $z>4$, and becoming JWST-dark at $z>6$ at current depths of major JWST surveys. Given their extreme faintness in optical and NIR wavelengths, and brightness in far infrared (FIR), (sub)mm facilities like ALMA and NOEMA, are more efficient in confirming their redshifts via detecting CO and/or \[CI\] lines (cite: Weiss2009; Walter2012; Riechers2013Nature; Riechers2017; Jin2019alma; Jin2022; Casey2019; Birkin2021; Chen2022; Gentile2024), which hence revealed vigorous star-bursting activities with obscured star formation rate ${\rm SFR}\sim300-3000\,{\rm M_\odot/yr}$ and large gas reservoirs $\log M_{\rm gas}/{\rm M_\odot}\sim 10.5-11.5$ in these massive systems (cite: Riechers2013Nature; Jin2022). However, the spectroscopic sample is still small and strongly biased towards sources with the brightest submm fluxes.

Consequently, studies of this population strongly rely on photometric redshifts, which entail the risk of catastrophic failures. For example, (cite: Ling2024_cosbo7) reported an optically dark ${\rm photo-}z>7$ DSFG candidate using 10 bands of JWST photometry, however, it was eventually confirmed at ${\rm spec-}z=2.625$ by (cite: Jin2024_cosbo7) via multiple CO and \[CI\] line detections. Evidently, robust spectroscopic confirmation is essential to uncover the nature of these extreme dusty objects.

Despite the limited sample of spectroscopically confirmed DSFGs, recent studies have revealed optically faint/dark DSFGs have optically thick dust in FIR, massive gas reservoirs and elevated star formation efficiency (SFE) compared to main sequence galaxies (cite: Jin2019alma; Jin2022; Kokorev2023_dustyguy). Nevertheless, it remains unclear whether active galactic nuclei (AGN) are present in these systems. As both X-ray and optical AGN features can be severely attenuated by dust, the AGN fraction of DSFGs could be largely underestimated (cite: Franco2018). Therefore, panchromatic studies including deep radio observations (cite: Delvecchio2017; Algera2020; van_der_Vlugt2021_COSMOS_XS; vanderVlugt2023_COSMOS_XS; Gentile2024) are key to identify potential AGN activity in these systems. As previous studies focus either on the stellar or interstellar medium (ISM) components, comprehensive studies of all baryonic components (stellar, dust, and gas) and AGN activity are essential to unveil their nature.

In this letter, we report the spectroscopic confirmation of the radio-selected DSFG XS55 and provide a panchromatic view of its stellar, dust, and gas components and associated AGN activity. We adopt a flat cosmology with $H_0=70\,{\rm km\,s^{-1}\,Mpc^{-1}}$, $\Omega_{\rm M}=0.27$, and $\Omega_\Lambda=0.73$, and use a (cite: Chabrier2003) initial mass function (IMF). All magnitudes are in the AB system (cite: Oke1974_AB_sys).

# Selection and Data

## Selection

XS55 was originally selected in the COSMOS-XS (cite: Algera2020; van_der_Vlugt2021_COSMOS_XS) catalog with an ID=55, hence we dub it XS55. It is detected in the ultra-deep COSMOS-XS S-band image with $S_{\rm 3GHz}$ = $6.35\pm0.96\,{\rm \mu Jy}$, but undetected in the less deep COSMOS 3 GHz map (cite: Smolcic2017), and detected in the MeerKAT image with $S_{{\rm 1.3GHz}}=10.9\pm2.1\,{\rm \mu Jy}$ (cite: Jarvis2016mightee; Heywood2022; Hale2024_meerkat). XS55 has no optical counterpart (i.e., optically dark) and is not included in the COSMOS2020 catalogue (cite: Weaver2022COSMOS2020). It drops out in JWST F115W and F150W images, but is detected in IRAC 4.5$\mu$m ([1](#fig:cutouts)) and tentatively detected ($\sim3\sigma$) in the ALMA 2 mm MORA map ((cite: Casey2021_MORA)). By performing the super-deblending technique (cite: Jin2018cosmos; Liu_DZ2017) with the radio prior, we measure the deblended *Herschel* and SCUBA-2 photometry of XS55. Interestingly, it is not detected in *Herschel* images ($3\sigma$ limiting depths: 250 ${\rm \mu}$m=$5.3\, {\rm mJy}$,350 ${\rm \mu}$m=$8.0\,{\rm mJy}$, 500 ${\rm \mu}$m=$8.7\,{\rm mJy}$, (cite: Jin2018cosmos)), but is well detected in two SCUBA-2 bands; 450$\mu$m (cite: Gao2024_SCUBA450) and 850$\mu$m (cite: Simpson2019) with a red 450$\mu$m/850$\mu$m colour ($S_{\rm450\,\mu m}=5.6\pm1.4\,{\rm mJy}, S_{\rm850\,\mu m}=5.7\pm0.8\,{\rm mJy}$). Assuming typical dust templates from (cite: Magdis2012SED), the red SCUBA-2 colour suggests a FIR photometric redshift of $z>6$. Consequently, XS55 was followed up by two ALMA 3 mm line scan projects in Cycle 9 (ID: 2022.1.00884, PI: R. Gobat; ID: 2022.1.00863.S, PI: J. Hodge).

## ALMA

The two ALMA programmes were observed for a total of 1.9 hours on source. The frequency setups are identical in the two programs, adopting the same setups as in (cite: Jin2019alma) and covering 84–108 GHz with three tunings. We produce measurement sets with the Common Astronomy Software Applications (CASA, (cite: McMullin2007CASA)) pipeline for each observation programme. Following the methods presented in (cite: Jin2022), (cite: Zhou2024), and (cite: Sillassen2024), the calibrated data are converted to $uv$ table format and analysed with the `GILDAS` software package in $uv$ space. To enhance the signals, the $uv$ tables from the two programs are combined using the task $uv\_merge$. The final products reach a continuum sensitivity of 9.6$\,{\rm \mu Jy/beam}$ with a spatial resolution of $1.6\ensuremath{''}$, and a line sensitivity of 12$\,{\rm mJy/beam}$ over 500 km/s at $\sim 99\,{\rm GHz}$. As shown in see [\[fig:spectrum,sec:redshift\]](#fig:spectrum,sec:redshift), We robustly detect continuum ($\sim14\sigma$) and two lines ($\sim10\sigma$ and $\sim4\sigma$). The dust continuum is well-fitted by a point-source model using `GILDAS` `uvfit`, while fitting with an elliptical Gaussian does not yield useful constraints. Therefore, the dust continuum is unresolved, and we place an upper limit on the continuum size using Eq. (2) from (cite: Gomez_Guijarro2022) (Table [2](#tab:physpars)).

## JWST

XS55 was observed with JWST NIRCam in F115W, F150W, F277W and F444W bands, as a part of the COSMOS-Web survey (cite: Casey2023_COSMOS_WEB). We use the image product versions from the Dawn JWST Archive (cite: Valentino2023_DJA), and further, have verified these are consistent with the COSMOS-Web team’s map (Shuntov et al. in prep.).

XS55 is well detected in both F277W ($\sim10\sigma$) and F444W ($\sim36\sigma$), but not detected in both F115W and F150W ($<3\sigma$), consistent with the H-dropout selection from (cite: Wang2019Natur).

## X-ray

The COSMOS field has been fully observed in soft (0.5-2.0 keV) and hard (2.0-10 keV) X-rays with both XMM-Newton (cite: Hasinger2007_XMMCosmos) and Chandra ($\sim$180 ks exposure) as part of the Chandra COSMOS (cite: Elvis2009_CCOSMOS) and Chandra COSMOS Legacy (cite: Civano2016) surveys.

As shown in [\[fig:color-img,fig:cutouts\]](#fig:color-img,fig:cutouts), XS55 is tentatively detected in soft X-ray band of Chandra with $2.1\sigma$ significance, and detected in the stacked soft, medium and hard X-ray XMM-Newton images with $3.1\sigma$.

![](60000055.pdf)

# Results

## Redshift identification

After extracting the ALMA spectra in all spectral windows (SPWs), we combine them in a single 1D spectrum ([2](#fig:spectrum)), and run a line-searching algorithm as in (cite: Jin2019alma) to search for emission line features with the highest significance. The continuum is fit with a power-law with fixed slope of 3.7 in frequency (cite: Magdis2012SED; Sillassen2024), masking out the channels of significant emission lines. The detected emission lines are fitted with a Gaussian profile in the continuum subtracted spectrum. XS55 is detected in 3mm continuum at $\sim14\sigma$ with a flux of $134.2\pm9.3\,{\rm \mu Jy}$ at $\sim96\,{\rm GHz}$. One line is detected at $98.99\,{\rm GHz}$ at $9.8\sigma$ (see [2](#fig:spectrum)), and we search for other lines in the spectrum consistent with this detection. We find a $3.9\sigma$ detection at $84.58\,{\rm GHz}$. The two lines are consistent with CO(5-4) and \[CI\](1-0) at $z=4.8214\pm0.0004$. We note that there is a slight velocity offset between the CO and CI line peaks of $\sim141\,{\rm km/s}$ ([2](#fig:spectrum)). By defining the \[CI\] line range using the velocity range of the CO line, the \[CI\] S/N is $3.3\sigma$, yielding a low $P_{\rm chance}=0.4\%$, where $P_{\rm chance}$ is the chance probability of finding a spurious second line (cite: Jin2019alma). Further, we compare the redshift solution with the NIR-SED fitted redshift probability distribution PDF(z) of `LePhare` in the COSMOS-Web catalog ($z_{\rm phot}=4.73^{+0.52}_{-0.64}$, Shuntov et al. in prep.), and find they are in excellent agreement ([4](#fig:full_sed)). For a sanity check, we tested the redshift solution of $z=3.66$ in the case of the bright line being CO(4-3), as this redshift is seemingly consistent with the second peak of the NIR PDF(z). However, we found $z=3.66$ is very unlikely, because (1) the $z=3.66$ \[CI\](1-0) is not detected at the expected frequency 105.6 GHz ($<1\sigma$); (2) the SED fitting at $z=3.66$ yields an abnormally high dust mass to stellar mass fraction $0.09<{M_{\rm dust}/M_\ast}<0.13$ that is $>10\times$ above typical values (cite: Donevski2020), again disfavouring the $z=3.66$ solution. Therefore, the multitude of evidence confirms the redshift of XS55 to be $z=4.8214\pm0.0004$.

![](XS55_spectrum_full.pdf)

## Morphology

We model the F277W and F444W morphology of XS55 using `Galfit` (cite: Peng2010_galfit). We adopt three separate components in both F277W and F444W: a compact central emission, a diffuse central emission, and a companion component at the south-east. The NIRCam PSFs were obtained using Webbpsf (cite: Perrin2014_WebbPSF) with a pixel scale of $0.05{\rm \ensuremath{''}/pix}$. We consider two cases; one case using a point source (compact component) together with two Sérsic profiles (diffuse component and companion), and another case with three separate Sérsic profiles. In the case using a point source and two Sérsic models in F444W, there is a ring of emission left in the residual ([6](#fig:morph)-middle-right), suggesting the brightest part of the galaxy is marginally resolved, or the PSF modelling is imperfect. In the case of three Sérsic profiles, there are no clear structures, as would be expected with random noise ([6](#fig:morph)-top). In the three Sérsic profile model of F444W, the compact component has a size of $0.061\ensuremath{''}\pm0.007\ensuremath{''}$ corresponding to $R_{\rm e}=0.40\pm0.05\,{\rm kpc}$ with Sérsic index $n<1.2$, while the diffuse emission and the companion have sizes and Sérsic indices of $R_{\rm e}=1.7\pm0.1\,{\rm kpc}$, $n=0.37\pm0.08$ and $R_{\rm e}=1.1\pm0.1\,{\rm kpc}$, $n=0.61\pm0.33$ respectively ([3](#tab:sizes)). In F444W, $33\pm3$% of the total flux is coming from the compact component, while $53\pm3$% is coming from the extended diffuse component, and $14\pm3$% is coming from the companion. In JWST/F277W, the fit of the compact component yields a bulge-like $n=2.6\pm0.8$ model with $R_{\rm e}=0.58\pm0.07\,{\rm kpc}$ ([3](#tab:sizes)), providing $87\pm2\%$ of the total flux. The diffuse component cannot be fit, and the fit to the companion yields a $n=2.0\pm1.4$ model with $R_{\rm e}=1.7\pm0.5\,{\rm kpc}$, providing $13\pm2\%$ of the total flux ([\[sec:morphology,tab:sizes\]](#sec:morphology,tab:sizes)). At this redshift, \[OIII\]${\lambda\lambda4959,5007}$ and ${\rm H\beta}$ fall within the JWST/F277W filter, consequently the flux is possibly boosted by line emission ([4](#fig:full_sed)).

## FIR SED

To estimate the dust mass ($M_{\rm dust}$) and temperature ($T_{\rm dust}$), we fit the FIR and (sub)mm photometry of XS55 with a modified black-body (MBB) model (cite: Magdis2012SED) using the code `mercurius` (cite: Witstok2022-mercurius). We explore two cases; one assuming optically thin dust, and the other assuming ‘self-consistent’ optically thick dust. For the optically thick case, we place an upper limit on the emitting area based on the half light radius of the galaxy in JWST/F444W ($9.08\,{\rm kpc^2}$; [3.2](#sec:morphology)). The resulting fit and corresponding parameters are shown in [\[fig:FIR-SEDs,tab:physpars\]](#fig:FIR-SEDs,tab:physpars). In both cases, the IR spectral index $\beta_{\rm IR}$ is consistent with a weighted average of $\beta_{\rm IR}=2.02\,{\pm \,0.12}$. For the optically thin case, we recover a low dust temperature of $T_{\rm dust}=27.6^{+3.1}_{-2.7}\,{\rm K}$, with an accompanying high dust mass of $M_{\rm dust}=2.4^{+1.4}_{-0.9}\times10^9\,{\rm M_\odot}$. On the other hand, the optically thick dust yields a higher $T_{\rm dust}=32.5^{+2.2}_{-1.9}\,{\rm K}$ and a lower $M_{\rm dust}=1.7^{+0.5}_{-0.4}\times10^9\,{\rm M_\odot}$.

To construct a panchromatic SED of XS55, we fit the stellar, AGN, and dust components using `STARDUST` (cite: Kokorev2021) and available photometry from optical to radio wavelength, yielding an IR luminosity of $L_{\rm IR}=(5.43\pm1.77)\times10^{12}\,{\rm L_\odot}$ and a ${\rm SFR}_{\rm IR}=543\pm177\,{\rm M_\odot\,yr^{-1}}$. For the stellar component, we recover the stellar mass $\log(M_\ast/{\rm M_\odot})=10.7\pm0.1$, attenuated by $A_v=2.2\pm0.3\,{\rm mag}$. As an additional check, we also fit the stellar part of the spectrum (up to F444W) using `Bagpipes`[^1] (cite: Carnall2018_bagpipes), using the same parameters as in (cite: Jin2024_cosbo7), yielding physical properties similar to those from `STARDUST`, $\log(M_{\rm \ast,bagpipes}/{\rm M_\odot})=10.7\pm0.1$, $A_{\rm v,bagpipes}=2.1\pm0.3$. The physical parameters calculated with LePhare in the COSMOS-Web catalog (Shuntov et al. in prep.) also agree with our results ($\log(M_{\rm \ast,LePhare}/{\rm M_\odot})=10.8\pm0.3$, $E({\rm B-V})_{\rm LePhare}=1.1$). The resulting panchromatic SED and corresponding properties from `STARDUST`, and MBB fit from `mercurius`, are shown in [\[fig:full_sed,tab:physpars\]](#fig:full_sed,tab:physpars).

## Molecular gas mass and far-infrared lines

With the derived dust mass, we infer a molecular gas mass ($M_{\rm mol}$) using the standard gas-to-dust mass ratio of star-forming galaxies (cite: Magdis2012SED), yielding $M_{\rm mol,thin}=2.6^{+0.5}_{-0.4}\times10^{11}\,{\rm M_\odot}$ and $M_{\rm mol,thick}=1.7^{+0.5}_{-0.4}\times10^{11}\,{\rm M_\odot}$. Furthermore, based on the detection of the \[CI\](1-0) line ([1](#tab:measured_properties)), we infer the molecular gas mass $M_{\rm mol}/{\alpha_{\rm CI}}=(1.8\pm0.5)\times10^{11}/{\alpha_{\rm CI}}\,{\rm M_\odot}$, where $\alpha_{\rm C{\tiny I}}=17.0\pm0.3\,{\rm M_\odot\,K^{-1}\,km^{-1}\,s\,pc^{-2}}$ (cite: Dunne2022alphaCI) that is consistent with other calibrations (cite: Valentino2018CI; Heintz2020_alphaCI). Adopting instead $\alpha_{\rm CI}=4.1\pm1.4\,{\rm M_\odot\,K^{-1}\,km^{-1}\,s\,pc^{-2}}$ from (cite: FriasCastillo2024) for high-$z$ SMGs, it yields a $M_{\rm mol}=(4.3\pm1.9)\times10^{10}\,{\rm M_\odot}$. Interestingly, the CO(5-4) emission is marginally resolved along the NE-SW direction (see [\[fig:spectrum,fig:color-img\]](#fig:spectrum,fig:color-img)), as the minor axis of the CO emission as well as the continuum source are unresolved, we obtain upper limits on their sizes using Eq. (2) of (cite: Gomez_Guijarro2022). We measure the size of the integrated CO(5-4) emission by fitting an elliptical Gaussian in $uv$-space with `GILDAS/uvfit`, and obtain $R_e=1.79\pm1.22\,{\rm kpc}$ with ${\rm PA}=28\pm20\,{\rm deg}$. We constructed the CO(5-4) moment-1 map using Cube Analysis and Rendering Tool for Astronomy (cite: Comrie2021_CARTA).

In the moment-1 map there is a clear velocity gradient, with the highest redshifted velocity of $70\,{\rm km/s}$ and the highest blueshifted velocity of $-130\,{\rm km/s}$. This velocity gradient is comparable to that of the radio selected NIR-dark galaxies from (cite: Gentile2024). We discuss the possible interpretations of the extended CO(5-4) emission in Sect. 4.2.

## Obscured AGN

XS55 is tentatively detected in X-ray with both Chandra and XMM-Newton (Fig. [3](#fig:color-img), [1](#fig:cutouts)). Using a 3" radius aperture that corresponds to the mean PSF of the Chandra COSMOS Legacy Survey (cite: Civano2016), we detect 3 counts in the 0.5-2 keV band of Chandra. This corresponds to a flux of $f_{\rm [0.5-2keV]}=(1.15\pm0.54)\times10^{-16}\,{\rm erg\,s^{-1}\,cm^{-2}}$ adopting the conversion rate from (cite: Civano2016). Since XS55 is extremely dusty, this flux should be considered a lower limit, yielding a soft X-ray luminosity of $L_{\rm [0.5-2keV]}>2.81\times10^{43}\,{\rm erg\,s^{-1}}$. Using the soft X-ray to bolometric luminosity correction from (cite: Lusso2012_Lbol) we obtained a bolometric luminosity of $L_{\rm bol}>5.35\times10^{44}\,{\rm erg\,s^{-1}}$. XS55 would be an X-ray selected AGN using the criterion from (cite: Riccio2023Xray) (i.e., $L_{0.2-2.3{\rm keV}}\geq3\times10^{42}\,{\rm erg\,s^{-1}}$). Due to the low significance of the X-ray detection, we cannot exclude that the detection could be spurious, or is originating from star-formation.

XS55 does not show excess radio emission compared to the infrared radio correlation (IRRC) of (cite: Delvecchio2021_IR_Radio), however, this could be due to the large scatter of IR-radio correlation that is largely unconstrained at $z\sim5$ (cite: Delvecchio2021_IR_Radio). Further, while radio excess is a clear indicator of AGN activity, X-ray AGN are not necessarily radio loud.

![](Fig2.png)

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Line | S/N | FWHM | $I_{\rm line}$ | $L'_{\rm line}$ | $P_{\rm chance}^a$ |
|  |  | \[${\rm km\,s^{-1}}$\] | \[${\rm Jy\,km\,s^{-1}}$\] | \[$10^{10}{\rm K\,km\,s^{-1}\,pc^2}$\] |  |
| CO(5-4) | 9.8 | $365\pm37$ | $0.53\pm0.07$ | $1.9\pm0.2$ | $<10^{-6}$ |
| ${\rm [C{\tiny I}]}$(1-0) | 3.9 | $293\pm75$ | $0.22\pm0.06$ | $1.1\pm0.3$ | $<0.004$ |

: Measured properties of XS55 emission lines

\
Notes:$^a$chance probability of emission line (cite: Jin2019alma).

| Parameter | Value |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | XS55 |  |  |  |  |  |  |
| RA, Dec \[deg\] | 150.1002501, 2.4967382 |  |  |  |  |  |  |
| $z$ | $4.8214\pm0.0004$ |  |  |  |  |  |  |
| $A_V$ \[mag\] | $2.2\pm0.3$ |  |  |  |  |  |  |
| $M_\ast$ \[$10^{10}{\rm M_\odot}$\] | $5\pm1$ |  |  |  |  |  |  |
| ${\rm SFR}_{\rm IR}$ \[${\rm M_\odot\,yr^{-1}}$\] | $540\pm180$ |  |  |  |  |  |  |
| $L_{\rm X}$ \[$10^{44}{\rm erg\,s^{-1}}$\] | $>5.4$ |  |  |  |  |  |  |
| $L_{\rm IR}$ \[$10^{12}{\rm L_{\odot}}$\] | $5.4\pm1.8$ |  |  |  |  |  |  |
| $\beta_{\rm IR}$ | $2.0\pm0.2$ |  |  |  |  |  |  |
| $M_{\rm gas,[C{\tiny I}]}$ \[$10^{11}{\rm M_\odot}$\] | $1.8\pm0.5$ |  |  |  |  |  |  |
| ${\rm SFE}$ \[$10^{-9}{\rm yr^{-1}}$\] | $3.0\pm1.0$ |  |  |  |  |  |  |
| $T_{\rm dust,thick}$ \[K\] | $32.7^{+2.2}_{-1.9}$ |  |  |  |  |  |  |
| $M_{\rm dust,thick}$ \[$10^{9}{\rm M_\odot}$\] | $1.7^{+0.6}_{-0.5}$ |  |  |  |  |  |  |
| $T_{\rm dust,thin}$ \[K\] | $28.0^{+3.3}_{-2.8}$ |  |  |  |  |  |  |
| $M_{\rm dust,thin}$ \[$10^{9}{\rm M_\odot}$\] | $2.3^{+1.4}_{-0.8}$ |  |  |  |  |  |  |
| $R_{\rm eff, 3mm}$ \[kpc\] | \<1.76\* |  |  |  |  |  |  |
| $R_{\rm maj, CO(5-4))}$ \[kpc\] | $3.2\pm1.1$ |  |  |  |  |  |  |
| $R_{\rm min, CO(5-4))}$ \[kpc\] | \<2.08\* |  |  |  |  |  |  |
| ${\rm PA}_{\rm CO(5-4)}$ \[deg\] | $28\pm20$ |  |  |  |  |  |  |

: Fitted and inferred physical properties of XS55

\
Notes:\*size upper limit (2$\sigma$) calculated with Eq. 2 in (cite: Gomez_Guijarro2022).

![](XS55_FIR_SED_zpdf.pdf)

# Discussion

## Intrinsically cold or optically thick dust (or both)?

To determine whether XS55 is intrinsically cold, or optically thick dust is making it appear cold, we apply three methods of diagnosing optically thick dust from (cite: Jin2022):

\(1\) We compare the molecular gas masses derived from \[CI\](1-0) emission with gas mass inferred by both thin and thick $M_{\rm dust}$. We find that the lower gas mass from the thick dust model is in good agreement with the \[CI\]-derived gas mass, assuming $\delta_{\rm gdr}=100$ and $\alpha_{\rm [CI]}=17\pm3\,{\rm M_\odot\,K^{-1}\,km^{-1}\,s\,pc^{-2}}$, while the gas mass from the thin dust model is likely overestimated.

\(2\) We estimate the dust opacity at 100 $\mu$m, $\tau_{\rm 100\mu m}=\kappa \rho R_{\rm e}$, where $\kappa$ is adopted from (cite: Jones2013), and $\rho$ is the volumetric dust density assuming spherical symmetry, using $R_{\rm e}$ from dust continuum ($R_{\rm e}<1.76\,{\rm kpc}$). This yields $\tau_{\rm 100\mu m,thin}>1.6$, and $\tau_{\rm 100\mu m,thick}>1.2$. Furthermore, we calculate the surface SFR density and find $\Sigma_{\rm SFR}>37\,{\rm M_\odot\,yr^{-1}\,kpc^{-2}}$. With both $\tau_{\rm 100\mu m}>1$ and $\Sigma_{\rm SFR}>20\,{\rm M_\odot\,yr^{-1}\,kpc^{-2}}$, the dust is hence optically thick (cite: Jin2022).

\(3\) We derive a lower limit of IR luminosity surface density $\Sigma_{\rm IR}>3.7\times10^{11}\,{\rm L_\odot\,kpc^{-2}}$, and place it on the $\Sigma_{\rm IR}-T_{\rm dust}$ diagram. As seen in [5](#fig:Tdust_z_sigma)-right, the thin case is clearly violating the blackbody Stefan-Boltzmann law, and the optically thick case is more favourable. Therefore, these pieces of evidence together imply that the dust of XS55 is optically thick in FIR.

Interestingly, the recovered $T_{\rm dust}$ assuming optically thick dust remains cold. Comparing to the redshift evolution of $T_{\rm dust}$ in main sequence galaxies (cite: Schreiber2018Tdust; Jin2022), the thick dust solution is 0.13 dex ($\sim4\sigma$) below the relation ([5](#fig:Tdust_z_sigma)). This makes XS55 one of the coldest DSFGs at $z>4$ discovered to date (cite: Faisst2020; Jin2022; Algera2024). Since dust temperature is proportional to the radiation field (cite: Magdis2012SED), and the radiation field is proportional to the ratio of star formation efficiency to metallicity (cite: Magdis2012SED), and given that XS55 has typical SFE of DSFGs, the intrinsically low dust temperature could suggest a high metallicity in XS55, where the cooling is more efficient.

![image](XS55_Tdust_z.pdf) ![image](XS55_sigmaIR_Tdust.pdf)

## Stable disk, outflow, or merger?

Interestingly, the CO(5-4) is more extended than the dust continuum size and shows a tentative velocity gradient. These properties could suggest a rotating molecular disk (cite: Rizzo2023_alpaka) with compact star-formation (cite: Cochrane2019_compact_starburst). However, given the low spatial resolution of the CO data, high resolution data are needed to confirm whether it is a rotating disk (e.g., (cite: Rowland2024z7)). As suggested by the complex JWST morphology, galaxy interaction or merger can also be accounted for the extended CO(5-4) emission. Furthermore, given the possible AGN nature of XS55 and that the CO(5-4) is only resolved in one direction, a molecular outflow driven by a central AGN (cite: Lutz2020_Molecular_outflow) is also a potential scenario.

To disentangle the above scenarios, a high resolution \[CII\] follow-up would be ideal to reveal the kinematics of XS55.

## Why is this source optically faint?

In nearly all terms, XS55 is a normal but massive main sequence star-forming galaxy at $z=4.8214$, within 2$\sigma$ of the (cite: Schreiber2015) main-sequence relation (${\rm \Delta MS} ({\rm SFR/SFR_{MS}})=2.4\pm0.9$). Its star formation efficiency, and thereby depletion time of $300\pm100\,{\rm Myr}$, is comparable to other optically faint galaxies at similar redshift (cite: Jin2019alma; Jin2022). However, with the compact stellar ($R_e=1.72\pm0.13\,{\rm kpc}$) and dust continuum ($R_e<1.76\,{\rm kpc}$) sizes, XS55 falls 2.6$\times$ below the mass-size relation of main sequence galaxies (cite: Ward2024_Mass_size_relation). The compact size, together with a massive amount of dust, could explain the optically faint nature of this source, in agreement with observations from (cite: Gomez-Guijarro2023) and simulations from (cite: Cochrane2024_compact_hstdark).

# Conclusions

By combining ALMA spectroscopy with JWST imaging and multi-wavelength ancillary data in the COSMOS field, we presented a detailed study of a newly discovered radio selected optically faint galaxy, XS55. ALMA detections of the CO(5-4) and \[CI\](1-0) lines places the source at $z=4.8214$, and reveals the presence of large amounts of dust in the ISM ($M_{\rm dust}=(1.7\pm0.5)\times10^9\,{\rm M_\odot}$). XS55 is a compact massive main-sequence galaxy, with extremely cold dust temperature, and optically thick FIR emission. The F444W size of the source falls below the mass-size relation. The tentative X-ray emission and the compactness of the central component suggest the presence of an AGN. The compactness together with the massive amount of cold dust in XS55 naturally explain its optical faintness.

# Acknowledgements

We thank the anonymous referee for constructive comments, improving this manuscript. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.00884.S, 2022.1.00863.S and 2021.1.00225.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Some of the data products presented herein were retrieved from the Dawn JWST Archive (DJA). DJA is an initiative of the Cosmic Dawn Center (DAWN). The Cosmic Dawn Center (DAWN) is funded by the Danish National Research Foundation under grant DNRF140. SJ acknowledges financial support from the European Union’s Horizon Europe research and innovation program under the Marie Skłodowska-Curie grant No. 101060888. GEM and SJ acknowledge the Villum Fonden research grants 37440 and 13160. JH acknowledges support from the ERC Consolidator Grant 101088676 (“VOYAJ”). CCC acknowledges the support of the Taiwan National Science and Technology Council (111-2112M-001-045-MY3), as well as the Academia Sinica through the Career Development Award (AS-CDA-112-M02). KK acknowledges support from the Knut and Alice Wallenberg Foundation (KAW 2017.0292 and 2019.0443).

87 natexlab

(ref: Pampliega2019) Alcalde Pampliega, B., Pérez-González, P. G., Barro, G., et al. 2019, ApJ, 876, 135

(ref: Algera2024) Algera, H. S. B., Inami, H., De Looze, I., et al. 2024a, MNRAS, 533, 3098

(ref: Algera2024_tdust_rebels) Algera, H. S. B., Inami, H., Sommovigo, L., et al. 2024b, MNRAS, 527, 6867

(ref: Algera2020) Algera, H. S. B., van der Vlugt, D., Hodge, J. A., et al. 2020, ApJ, 903, 139

(ref: Barrufet2024_OFGs) Barrufet, L., Oesch, P., Marques-Chaves, R., et al. 2024, arXiv e-prints, arXiv:2404.08052

(ref: Barrufet2023) Barrufet, L., Oesch, P. A., Weibel, A., et al. 2023, MNRAS, 522, 449

(ref: Birkin2021) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021, MNRAS, 501, 3926

(ref: Carnall2018_bagpipes) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379

(ref: Casey2023_COSMOS_WEB) Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023, ApJ, 954, 31

(ref: Casey2019) Casey, C. M., Zavala, J. A., Aravena, M., et al. 2019, ApJ, 887, 55

(ref: Casey2021_MORA) Casey, C. M., Zavala, J. A., Manning, S. M., et al. 2021, ApJ, 923, 215

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Chen2022) Chen, C.-C., Liao, C.-L., Smail, I., et al. 2022, ApJ, 929, 159

(ref: Civano2016) Civano, F., Marchesi, S., Comastri, A., et al. 2016, ApJ, 819, 62

(ref: Cochrane2024_compact_hstdark) Cochrane, R. K., Anglés-Alcázar, D., Cullen, F., & Hayward, C. C. 2024, ApJ, 961, 37

(ref: Cochrane2019_compact_starburst) Cochrane, R. K., Hayward, C. C., Anglés-Alcázar, D., et al. 2019, MNRAS, 488, 1779

(ref: Comrie2021_CARTA) Comrie, A., Wang, K.-S., Hsu, S.-C., et al. 2021, CARTA: The Cube Analysis and Rendering Tool for Astronomy

(ref: Delvecchio2021_IR_Radio) Delvecchio, I., Daddi, E., Sargent, M. T., et al. 2021, A&A, 647, A123

(ref: Delvecchio2017) Delvecchio, I., Smolčić, V., Zamorani, G., et al. 2017, A&A, 602, A3

(ref: Donevski2020) Donevski, D., Lapi, A., Małek, K., et al. 2020, A&A, 644, A144

(ref: Dunne2022alphaCI) Dunne, L., Maddox, S. J., Papadopoulos, P. P., Ivison, R. J., & Gomez, H. L. 2022, MNRAS, 517, 962

(ref: Elvis2009_CCOSMOS) Elvis, M., Civano, F., Vignali, C., et al. 2009, ApJS, 184, 158

(ref: Enia2022) Enia, A., Talia, M., Pozzi, F., et al. 2022, ApJ, 927, 204

(ref: Faisst2020) Faisst, A. L., Fudamoto, Y., Oesch, P. A., et al. 2020, MNRAS, 498, 4192

(ref: Franco2018) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152

(ref: FriasCastillo2024) Frias Castillo, M., Rybak, M., Hodge, J. A., et al. 2024, arXiv e-prints, arXiv:2404.05596

(ref: Fudamoto2023) Fudamoto, Y., Inoue, A. K., & Sugahara, Y. 2023, MNRAS, 521, 2962

(ref: Fudamoto2021) Fudamoto, Y., Oesch, P. A., Schouws, S., et al. 2021, Nature, 597, 489

(ref: Gao2024_SCUBA450) Gao, Z.-K., Lim, C.-F., Wang, W.-H., et al. 2024, ApJ, 971, 117

(ref: Gentile2024a) Gentile, F., Talia, M., Behiri, M., et al. 2024a, ApJ, 962, 26

(ref: Gentile2024) Gentile, F., Talia, M., Daddi, E., et al. 2024b, A&A, 687, A288

(ref: Gomez_Guijarro2022) Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022, A&A, 658, A43

(ref: Gomez-Guijarro2023) Gómez-Guijarro, C., Magnelli, B., Elbaz, D., et al. 2023, A&A, 677, A34

(ref: Gottumukkala2024_OFG_SMF) Gottumukkala, R., Barrufet, L., Oesch, P. A., et al. 2024, MNRAS, 530, 966

(ref: Hale2024_meerkat) Hale, C. L., Heywood, I., Jarvis, M. J., et al. 2024, MNRAS \[\]

(ref: Hasinger2007_XMMCosmos) Hasinger, G., Cappelluti, N., Brunner, H., et al. 2007, ApJS, 172, 29

(ref: Heintz2020_alphaCI) Heintz, K. E. & Watson, D. 2020, ApJL, 889, L7

(ref: Heywood2022) Heywood, I., Jarvis, M. J., Hale, C. L., et al. 2022, MNRAS, 509, 2150

(ref: Hodge2018) Hodge, J. A., Smail, I., Walter, F., et al. 2019, ApJ, 876, 130

(ref: Jarvis2016mightee) Jarvis, M., Taylor, R., Agudo, I., et al. 2016, in MeerKAT Science: On the Pathway to the SKA, 6

(ref: Jin2018cosmos) Jin, S., Daddi, E., Liu, D., et al. 2018, ApJ, 864, 56

(ref: Jin2019alma) Jin, S., Daddi, E., Magdis, G. E., et al. 2019, ApJ, 887, 144

(ref: Jin2022) Jin, S., Daddi, E., Magdis, G. E., et al. 2022, A&A, 665, A3

(ref: Jin2024_cosbo7) Jin, S., Sillassen, N. B., Hodge, J., et al. 2024, A&A, 690, L16

(ref: Jones2013) Jones, A. P., Fanciullo, L., Köhler, M., et al. 2013, A&A, 558, A62

(ref: Kokorev2023_dustyguy) Kokorev, V., Jin, S., Magdis, G. E., et al. 2023, ApJL, 945, L25

(ref: Kokorev2021) Kokorev, V. I., Magdis, G. E., Davidzon, I., et al. 2021, ApJ, 921, 40

(ref: Ling2024_cosbo7) Ling, C., Sun, B., Cheng, C., et al. 2024, ApJL, 969, L28

(ref: Liu_DZ2017) Liu, D., Daddi, E., Dickinson, M., et al. 2018, ApJ, 853, 172

(ref: Lusso2012_Lbol) Lusso, E., Comastri, A., Simmons, B. D., et al. 2012, MNRAS, 425, 623

(ref: Lutz2020_Molecular_outflow) Lutz, D., Sturm, E., Janssen, A., et al. 2020, A&A, 633, A134

(ref: Magdis2012SED) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6

(ref: Marrone2017Nature) Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, Nature, 553, 51

(ref: McMullin2007CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Oke1974_AB_sys) Oke, J. B. 1974, ApJS, 27, 21

(ref: Pavesi2018) Pavesi, R., Riechers, D. A., Sharon, C. E., et al. 2018, ApJ, 861, 43

(ref: Peng2010_galfit) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2010, AJ, 139, 2097

(ref: Perez-Gonzalez2023) Pérez-González, P. G., Barro, G., Annunziatella, M., et al. 2023, ApJL, 946, L16

(ref: Perrin2014_WebbPSF) Perrin, M. D., Sivaramakrishnan, A., Lajoie, C.-P., et al. 2014, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9143, Space Telescopes and Instrumentation 2014: Optical, Infrared, and Millimeter Wave, ed. J. Oschmann, Jacobus M., M. Clampin, G. G. Fazio, & H. A. MacEwen, 91433X

(ref: Riccio2023Xray) Riccio, G., Yang, G., Małek, K., et al. 2023, A&A, 678, A164

(ref: Riechers2013Nature) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329

(ref: Riechers2014) Riechers, D. A., Carilli, C. L., Capak, P. L., et al. 2014, ApJ, 796, 84

(ref: Riechers2017) Riechers, D. A., Leung, T. K. D., Ivison, R. J., et al. 2017, ApJ, 850, 1

(ref: Rizzo2023_alpaka) Rizzo, F., Roman-Oliveira, F., Fraternali, F., et al. 2023, A&A, 679, A129

(ref: Rowland2024z7) Rowland, L. E., Hodge, J., Bouwens, R., et al. 2024, MNRAS \[\]

(ref: Schreiber2018Tdust) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30

(ref: Schreiber2015) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74

(ref: Shu2022) Shu, X., Yang, L., Liu, D., et al. 2022, ApJ, 926, 155

(ref: Sillassen2024) Sillassen, N. B., Jin, S., Magdis, G. E., et al. 2024, A&A, 690, A55

(ref: Simpson2019) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2019, ApJ, 880, 43

(ref: Simpson2017) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2017, ApJ, 839, 58

(ref: Smail2023) Smail, I., Dudzevičiūtė, U., Gurwell, M., et al. 2023, ApJ, 958, 36

(ref: Smail2020) Smail, I., Dudzevičiūtė, U., Stach, S. M., et al. 2021, MNRAS, 502, 3426

(ref: Smolcic2017) Smolčić, V., Novak, M., Bondi, M., et al. 2017, A&A, 602, A1

(ref: Talia2021) Talia, M., Cimatti, A., Giulietti, M., et al. 2021, ApJ, 909, 23

(ref: Valentino2023_DJA) Valentino, F., Brammer, G., Gould, K. M. L., et al. 2023, ApJ, 947, 20

(ref: Valentino2018CI) Valentino, F., Magdis, G. E., Daddi, E., et al. 2018, ApJ, 869, 27

(ref: van_der_Vlugt2021_COSMOS_XS) van der Vlugt, D., Algera, H. S. B., Hodge, J. A., et al. 2021, ApJ, 907, 5

(ref: vanderVlugt2023_COSMOS_XS) van der Vlugt, D., Hodge, J. A., Jin, S., et al. 2023, ApJ, 951, 131

(ref: Walter2012) Walter, F., Decarli, R., Carilli, C., et al. 2012, Nature, 486, 233

(ref: Wang2019Natur) Wang, T., Schreiber, C., Elbaz, D., et al. 2019, Nature, 572, 211

(ref: Ward2024_Mass_size_relation) Ward, E., de la Vega, A., Mobasher, B., et al. 2024, ApJ, 962, 176

(ref: Weaver2022COSMOS2020) Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022, ApJS, 258, 11

(ref: Weiss2009) Weiß, A., Ivison, R. J., Downes, D., et al. 2009, ApJL, 705, L45

(ref: Witstok2022-mercurius) Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS, 515, 1751

(ref: Xiao2023_OFGs) Xiao, M. Y., Elbaz, D., Gómez-Guijarro, C., et al. 2023, A&A, 672, A18

(ref: Zhou2024) Zhou, L., Wang, T., Daddi, E., et al. 2024, A&A, 684, A196

# Morphology

![](XS55_galfit_full.pdf)

+-------------------------------------------+
| *F444W*                                   |
+:=========================:+:=============:+
| Compact component                         |
+---------------------------+---------------+
| $R_{\rm e,F444W}$ \[kpc\] | $0.40\pm0.05$ |
+---------------------------+---------------+
| $n$                       | $<1.2$        |
+---------------------------+---------------+
| Diffuse disk component                    |
+---------------------------+---------------+
| $R_{\rm e,F444W}$ \[kpc\] | $1.72\pm0.13$ |
+---------------------------+---------------+
| $n$                       | $0.37\pm0.08$ |
+---------------------------+---------------+
| Companion                                 |
+---------------------------+---------------+
| $R_{\rm e,F444W}$ \[kpc\] | $1.06\pm0.13$ |
+---------------------------+---------------+
| $n$                       | $0.61\pm0.33$ |
+---------------------------+---------------+
| F277W                                     |
+-------------------------------------------+
| Compact component                         |
+---------------------------+---------------+
| $R_{\rm e,F277W}$ \[kpc\] | $0.58\pm0.07$ |
+---------------------------+---------------+
| $n$                       | $2.6\pm0.8$   |
+---------------------------+---------------+
| Diffuse disk component                    |
+-------------------------------------------+
| Component not detected                    |
+-------------------------------------------+
| Companion                                 |
+---------------------------+---------------+
| $R_{\rm e,F277W}$ \[kpc\] | $1.7\pm0.5$   |
+---------------------------+---------------+
| $n$                       | $2.0\pm1.4$   |
+---------------------------+---------------+
|                           |               |
+---------------------------+---------------+

: Effective radii and Sérsic indices from Galfit

# FIR fitting

![image](Thin_reduced_res.pdf) ![image](Thick_reduced_res.pdf)

[^1]: <https://bagpipes.readthedocs.io/en/latest/>

</paper>

Write the methods card for this paper.