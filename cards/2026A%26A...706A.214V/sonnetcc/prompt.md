# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026A%26A...706A.214V\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2026A&A...706A.214V",
 "title": "Observational evidence for a possible link between PAH emission and dust trap locations in protoplanetary disks",
 "year": 2026,
 "journal": "Astronomy and Astrophysics",
 "first_author": "van der Marel, Nienke",
 "n_authors": 7,
 "arxiv_id": "2511.06935",
 "doi": "10.1051/0004-6361/202453113",
 "alma_projects_linked_by_archive": [
  "2012.1.00303.S",
  "2012.1.00631.S",
  "2013.1.00100.S",
  "2013.1.00157.S",
  "2013.1.00498.S",
  "2015.1.00773.S",
  "2015.1.00979.S",
  "2015.1.01600.S",
  "2016.1.00336.S",
  "2016.1.00340.S",
  "2016.1.00344.S",
  "2016.1.00484.L",
  "2016.1.00826.S",
  "2017.1.01424.S",
  "2018.1.00689.S",
  "2018.1.01458.S",
  "2021.1.00709.S",
  "2021.1.00854.S",
  "2021.1.01137.S",
  "2022.1.01302.S"
 ]
}
```

Paper text:
<paper>
# Observational evidence for a possible link between PAH emission and dust trap locations in protoplanetary disks

In this work, the measured PAH intensities of a range of disks are compared with ALMA dust continuum images, in order to test whether there is evidence that PAHs are frozen out on pebbles in dust traps and only sublimate under certain conditions. A sample is constructed from 26 T Tauri and Herbig disks located within 300 pc, with constraints on the 3.3 $\mu$m PAH intensity and with high-resolution ALMA continuum data. The midplane temperature is derived using a power-law or with radiative transfer modeling. The warm dust mass is computed by integrating the flux within the 30 K radius and convert to a dust mass.A strong correlation with a Pearson coefficient of 0.88$\pm$0.07 between the 3.3 $\mu$m PAH intensity and the warm dust mass was found. The correlation is driven by the combination of deep upper limits and strong detections corresponding to a range of warm dust masses. Possible correlations with other disk properties like FUV radiation field or total dust mass are much weaker. Correlations with PAH features at 6.2, 8.6 and 11.3 $\mu$m are potentially weaker, but this could be explained by the smaller sample for which these data were available. The correlation is consistent with the hypothesis that PAHs are generally frozen out on pebbles in disks, and are only revealed in the gas phase if those pebbles have drifted towards warm dust traps inside the 30 K radius and vertically transported upwards to the disk atmosphere with sufficiently high temperature to sublimate PAHs into the gas phase. This is similar to previous findings on complex organic molecules in protoplanetary disks and provides further evidence that the chemical composition of the disk is governed by pebble transport.

# Introduction

Polycyclic Aromatic Hydrocarbons (PAHs) are molecules that are constituted of two or more integrated aromatic rings, often set in a honeycomb structure of carbon atoms, locking up $\sim20$% of all elemental carbon (cite: Visser2007) and emit several spectral features through vibrational transitions at infrared wavelengths (cite: Allamandola1985), at e.g. 3.3, 6.2, 7.7, 8.6, 11.2 and 12.7 $\mu$m. PAHs are strong absorbers in the ultraviolet (UV) and an important contributor to the local gas heating. The different features are attributed to various C-H and C-C bonds as well as ionization (cite: Acke2010). PAHs are generally found in high UV environments and have been observed in a wide variety of sources (cite: Peeters2004). However, the appearance of PAHs in protoplanetary disks, where the building blocks of comets and planets are formed, is less well understood, in particular the wide variation of PAH spectral intensities in disks. Dozens of protoplanetary disks have been targeted with infrared spectroscopy with e.g. ISO, *Spitzer* and VLT (cite: Habart2004; Geers2006; Geers2007; Acke2010), and very recently, with JWST (cite: Sturm2024). These surveys generally show infrared PAH signatures in around 60-70% of the spectra of Herbig stars and only 8% for T Tauri stars. Although a general correlation between PAH detection and stellar temperature linked to the UV radiation field exists, it is not clear why the PAH emission strength or even its detection also varies strongly within spectral type and millimeter-dust disk morphology as traced by ALMA. Specifically, some Herbig disks show relatively strong PAH emission when their disk has a cavity (e.g. HD100546), whereas others do not (e.g. HD135344B), while multi-ringed disks without cavity have much weaker PAH emission (e.g. HD163296), but compact disks show strong PAH emission (e.g. HD179218). For T Tauri stars there is a similar range of PAH emission strength across morphologies (cite: Geers2007). These findings hint at a possible link between the millimeter-dust substructures and the PAH intensity.

Several mechanisms have been proposed to explain the diversity of PAH emission in protoplanetary disks: flared Herbig disks (known as Group I disks) have a higher PAH emission due to their larger exposure to UV radiation compared to the flat, Group II disks due to the absorption of PAHs by the inner dusty regions in Group II disks (cite: Meeus2001; Habart2004); the lack of PAH emission in many T Tauri stars may be related to the destruction of PAHs due to EUV and X-ray photons (cite: Siebenmorgen2010) or efficient freeze out onto dust grains (cite: Geers2009), followed by ionisation reactions which deplete the PAHs (cite: Bouwman2010); PAHs cluster in outer disk regions where the UV radiation is lower and therefore PAH dissociation is limited, so that PAH emission at short wavelengths gets suppressed (cite: Rapaciola2009; Lange2021).

The latter led to a more thorough investigation combining cluster formation with freeze-out and vertical mixing (cite: Lange2023), showing that clustering followed by freeze-out in the low UV regime near the midplane of the disk can indeed deplete gas-phase PAHs by a factor 50-1000 compared to the ISM. This suggests a scenario where PAHs are locked up in the icy layers on dust grains, unless the dust grains are warm enough to release their icy cover.

In recent years, ALMA observations have demonstrated that a similar mechanism is at play for complex organic molecules (COMs) in disks, in particular in so-called dust traps. Dust traps are recognized as substructures observed in millimeter observations of protoplanetary disks (cite: Andrews2020) and are generally interpreted as the result of pressure bumps, which halt millimeter-sized dust grains from drifting inwards (cite: Pinilla2012b). In IRS 48, HD 100546 and HD100453 gas-phase COMs with sublimation temperatures $>$100 K have been found to be highly abundant and cospatial with these dust traps (cite: Booth2021-hd100; vanderMarel2021-irs48; Brunken2022; Booth2024; Booth2025). This is interpreted as the release of COMs into the gas-phase due to vertical mixing of the small grains after fragmentation of millimeter-sized pebbles at the location of the dust trap, where the COMs were locked up in icy mantles of the grains and pebbles (cite: vanderMarel2021-irs48). Vertical mixing is required, as the midplane temperature is generally too low at the dust trap location for sublimation, whereas the higher molecular layers in the disk are significantly warmer (cite: Bruderer2012). The icy pebbles have been transported inwards toward the dust trap through radial drift and are inherited from the original molecular cloud. This means that the classical picture of a radial snowline is revised to a ‘snow surface’, i.e. a snowline that is varying with both temperature and height in the disk (cite: Gavino2021), where the radius of the midplane CO snowline lies below the H$_2$O (and CH$_3$OH) snow surface (see Figure [1](#fig:graphic)). It has been proposed that other disks do not show any gas-phase COM emission as their dust traps are located too far out in the disk, i.e. their dust traps are considered ‘cold’, whereas IRS 48 and HD 100546 happen to have ‘warm’ dust traps (cite: vanderMarel2023; Temmink2023). A similar scenario has been proposed to explain the dichotomy in C/O ratios in disks as measured from C$_2$H emission (cite: vanderMarel2021-c2h). The chemical complexity of irradiated icy dust traps may even lead to the efficient formation of IOM (insoluble organic matter) or macromolecules, a dominant reservoir of organic carbon in meteorites (cite: Alexander2008; Ligterink2024).

Spatially resolved PAH emission of a handful of disks using ground-based facilities with $\sim$0.1-0.2" point spread function (PSF) indicated initially that PAH features were centrally peaked, while long wavelength features were found to be more extended than those at shorter wavelengths (cite: vanBoekel2004; Habart2004-hd97048; Habart2006; Lagage2006; Geers2007-irs48; Bouteraon2019). However, at least for PAH features at longer wavelengths the emission has now often been shown to be ring-like (cite: Devinat2022; Yoffe2023). These spatially resolved features are not obviously linked to the dust substructures, but the interpretation remains limited due to the small sample size. Also, these surveys have only targeted disks where PAHs have been previously detected, so non-detections of PAHs in other disks with similar properties remain unexplained. Therefore, in this study we consider the integrated PAH intensities and upper limits on those for a much larger disk sample, and compare their values with the amount of warm dust in these disks.

Within this study, ‘warm dust’ is defined as the millimeter dust inside the CO snowline, i.e. where CO ice has been sublimated and the midplane temperature is $>$30 K. Although PAHs sublimate at much higher temperatures $>$150-300 K (cite: Ligterink2023), such temperatures are easily reached at a few scale heights above the midplane (cite: vanderMarel2021-irs48), so efficient vertical transport of fragmented icy grains to warmer layers where ices could sublimate is required. The definition of the cutoff temperature of the warm dust region is thus chosen at 30 K in the midplane.

![](graphic.png)

In this study we will investigate the correlation between warm dust and PAH gas-phase intensity using a sample of suitable protoplanetary disks for which PAH intensities are available from the literature, as well as high-resolution ALMA observations and well-defined stellar properties. The paper is structured as follows: Section [2](#sec:data) presents the sample selection criteria and the collection of ALMA data, as well as details on the ALMA observations and temperature profiles. Section [3](#sec:analysis) explains the methods that were used to compute the warm dust mass. Section [4](#sec:results) presents the resulting correlations. Section [5](#sec:discussion) discusses the implications of our results and draws the conclusions.

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|:--:|:--:|:---|:---|
| Target | $d$ | $L_*$ | SpT | $M_*$ | $\log\dot{M}$ | $L_{FUV}^a$ | $F_{PAH3.3\mu{m}}$ | $I_{PAH3.3\mu{m},1pc}$ | Disk type$^b$ | Ref$^c$ |
|  | (pc) | ($L_{\odot}$) |  | ($M_{\odot}$) | ($M_{\odot}$ yr$^{-1}$) | ($L_{\odot}$) | (10$^{-14}$ W m$^{-2}$) |  |  |  |
| ABAur | 155 | 46 | A0 | 2.4 | -7.0 | 3.5 | $<$1.0$\pm$0.2 | $<$3.0$\pm$0.6 | TD | 2 |
| Elias1/V892Tau | 134 | 129$^d$ | A0 | 2 | \- | 7.8 | 0.5$\pm$0.1 | 0.87$\pm$0.18 | TD | 1 |
| HD100453 | 104 | 6.2 | A9 | 1.5 | -8.3 | 0.1 | 1.3$\pm$0.2 | 1.8$\pm$0.3 | TD | 3 |
| HD100546 | 110 | 23 | B9 | 2.2 | -7 | 2.5 | 2.5$\pm$0.5 | 3.8$\pm$0.8 | TD | 2 |
| HD135344 | 136 | 6.2 | F5 | 1.6 | -7.4 | 0.1 | $<$0.5$\pm$0.1 | $<$1.2$\pm$0.2 | TD | 2 |
| HD139614 | 135 | 5.9 | A9 | 1.5 | -8.1 | 0.1 | $<$0.5$\pm$0.1 | $<$1.1$\pm$0.2 | TD | 3 |
| HD142527 | 157 | 9.1 | F6 | 2.3 | -7.5 | 0.1 | 1.0$\pm$0.6 | 3.1$\pm$1.9 | TD | 2 |
| HD169142 | 114 | 20 | A5 | 2 | -8.7 | 0.56 | 1.0$\pm$0.2 | 1.6$\pm$0.3 | TD | 2 |
| HD97048 | 185 | 35 | A0 | 2.4 | -8.2 | 2.1 | 1.3$\pm$0.3 | 5.6$\pm$1.3 | TD | 2 |
| IRS48 | 134 | 18 | A0 | 2 | -8.4 | 1.1 | 0.24$\pm$0.02 | 0.54$\pm$0.04 | TD | 2 |
| SR21 | 138 | 12 | G3 | 2 | -7.9 | 0.04 | 0.35$\pm$0.02 | 0.84$\pm$0.05 | TD | 2 |
| SYCha | 181 | 0.73 | M0.5 | 0.8 | -9.4 | 0.0004 | $<$0.008$\pm$0.002 | $<$0.033$\pm$0.006 | TD | 2 |
| TCha | 102 | 1.3 | G8 | 1.2 | -8.4 | 0.01 | $<$0.25$\pm$0.05 | $<$0.33$\pm$0.06 | TD | 2 |
| GWLup | 155 | 0.33 | M1.5 | 0.5 | -9.0 | 0.0008 | $<$0.024$\pm$0.005 | $<$0.072$\pm$0.015 | RD | 5 |
| HD142666 | 148 | 8.7 | A8 | 1.6 | -7.6 | 0.2 | 0.3$\pm$0.2 | 0.83$\pm$0.55 | RD | 3 |
| HD163296 | 101 | 17 | A1 | 2.0 | -7.4 | 1 | $<$0.2$\pm$0.04 | $<$0.26$\pm$0.05 | RD | 5 |
| IMLup | 158 | 2.6 | K5 | 0.9 | -7.9 | 0.009 | $<$0.19$\pm$0.04 | $<$0.60$\pm$0.12 | RD | 5 |
| RULup | 159 | 1.5 | K7 | 0.6 | -7.1 | 0.04 | $<$0.57$\pm$0.11 | $<$1.8$\pm$0.4 | RD | 5 |
| V1121Oph/AS209 | 121 | 1.4 | K5 | 0.8 | -7.3 | 0.04 | 0.12$\pm$0.02 | 0.22$\pm$0.04 | RD | 5 |
| WaOph6 | 123 | 2.9 | K6 | 0.7 | -6.6 | 0.12 | 0.23$\pm$0.02 | 0.44$\pm$0.04 | RD | 5 |
| DoAr24E | 136 | 1.6 | K0 | 0.6 | -8.5 | 0.004 | $<$0.041$\pm$0.008 | $<$0.095$\pm$0.019 | CD | 4 |
| GQLup | 150 | 0.91 | K5 | 0.6 | -7.4 | 0.03 | $<$0.054$\pm$0.011 | $<$0.15$\pm$0.03 | CD | 4 |
| Haro1-17 | 142 | 0.22 | M7 | 0.1 | -99 | 0 | $<$0.0045$\pm$0.001 | $<$0.011$\pm$0.002 | CD | 4 |
| HD104237/DXCha | 108 | 21 | A4 | 1.8 | -6.4 | 1.5 | $<$0.5$\pm$0.1 | $<$0.73$\pm$0.14 | CD | 3 |
| HD179218 | 266 | 112 | A0 | 3 | \- | 6.8 | 1.7$\pm$0.2 | 15$\pm$1.8 | CD | 6 |
| Sz73 | 155 | 0.18 | K7 | 0.7 | -8.5 | 0.006 | 0.094$\pm$0.02 | 0.28$\pm$0.06 | CD | 4 |
| WXCha | 189 | 0.86 | M0 | 0.5 | -6.7 | 0.1 | $<$0.027$\pm$0.006 | $<$0.12$\pm$0.03 | CD | 4 |

\
$^a$ FUV luminosity, integrated from the stellar spectrum (including accretion luminosity) between 912-2050 $\AA$ or 6-13.6 eV (cite: Habing1968). In Figure [3](#fig:PAH_other) $L_{\rm FUV}$ is computed at 150 au radius to get the parameter $\chi$, similar to previous studies.\
$^b$ TD = transition disk, CD = compact disk ($<$20 au), RD = ring disk (see (cite: vdMMulders2021)).\
$^c$ Reference for stellar properties: 1) (cite: Herczeg2014) 2) (cite: vanderMarel2023), 3) (cite: Grant2023), 4) (cite: Manara2023), 5) (cite: Andrews2018), 6) (cite: Vioque2018).\
$^d$ Whereas (cite: Vioque2018) reports a luminosity of 1.3 $L_{\odot}$, the higher luminosity by (cite: Herczeg2014) is used here, as it is more consistent with the stellar mass, which is independently derived from CO kinematics by (cite: Long2021).

# Data

## Sample

The sample consists of a selection of targets from (cite: Habart2004) and (cite: Geers2007), who present ISO spectra of Herbig stars and VLT spectra of T Tauri stars, respectively. These studies report (amongst others) the integrated intensity of the 3.3 $\mu$m PAH feature. From their original target lists, the targets at distances $>$300 pc are excluded as their dust disk cannot be well constrained due to a lack of spatially well-resolved ALMA data. Targets in the high extinction CrA region are excluded due to lack of proper stellar information. We also remove close binaries with separation $\sim$0.5-1" (EM SR 9, HT Lup and SX Cha) as dust disks in such binary systems are truncated and less representative of pure radial drift effects (cite: Akeson2014). Furthermore, we exclude WL16 as it is an embedded disks and HD141569 as it is an evolved, debris-like disk. This leaves 26 targets, which are listed in Table [\[tbl:sample\]](#tbl:sample).

## Stellar properties and PAH intensities

Stellar properties are taken from the recent literature, which often includes updated values based on the Gaia DR2 distances compared to the original papers.

PAH emission consists of multiple infrared features, at e.g. 3.3, 6.2, 7.7, 8.6, 11.2 and 12.7 $\mu$m. The integrated 3.3 $\mu$m PAH feature is most commonly reported across a wide range of spectral types, both detections and non-detections (upper limits), and is thus chosen for our main sample analysis. The origin of this feature is likely due to a single aromatic material and its intensity ratio with aliphatic features is independent of the local UV-field, suggesting that these PAHs are continuously replenished at the disk surface (cite: Bouteraon2019). The measured PAH flux as well as the distance-scaled PAH intensity are listed in Table [\[tbl:sample\]](#tbl:sample). The latter is computed by multiplying the flux with 4$\pi d^2\times10^{-5}$ with $d$ the distance in pc. The (scaled) uncertainties are included as well. The upper limits are 5$\sigma$, following the convention of the original works.

In addition, we consider the 6.2, 8.6 and 11.3 $\mu$m PAH intensities derived by (cite: Habart2004) and (cite: Acke2010), as these are bright, commonly studied features, and the 8.6 and 11.3 features have been followed up with spatially resolved observations (cite: Yoffe2023). Whereas the 3.3 $\mu$m feature is dominated by emission from the inner region of the disk, PAH features at longer wavelengths are known to be more extended as they get a larger contribution from the outer disk, due to the lower UV radiation needed to excite these features (cite: Habart2004). Furthermore, the 11.3 $\mu$m feature is thought to be related to neutral PAHs, whereas the 8.6 $\mu$m feature is linked to ionized PAHs, and these features are thus not tightly correlated with each other (cite: Maaskant2014). Only 12 of our targets (all Herbigs) overlap with the sample from (cite: Acke2010), which means that the analysis of these features is much more limited. This subsample and their scaled PAH intensities are listed in Table [1](#tab:pahacke), where the intensities are scaled to the stellar distance, as explained above.

| Target | $I_{PAH6.2\mu{m},1pc}$ | $I_{PAH8.6\mu{m},1pc}$ | $I_{PAH11.3\mu{m},1pc}$ |
|:---|:---|:---|:---|
| AB Aur | 14.3 | 7.2 | 3.3 |
| HD100453 | 2.9 | 0.64 | 1.3 |
| HD100546 | 22$^a$ | 3.5 | $<$9.1 |
| HD135344 | 0.86 | 0.13 | 0.6 |
| HD139614 | 1.6 | 0.57 | $<$0.11 |
| HD142527 | 6.7 | 1.6 | 5.0 |
| HD169142 | 4.2 | 1.5 | 3.4 |
| HD97048 | 23.7 | 12.8 | 27.2 |
| HD142666 | 2.0 | 0.7 | 1.2 |
| HD163296 | $<$1.9$^a$ | $<$1.2 | $<$2.6 |
| HD104237 | $<$0.06 | $<$0.9 | $<$1.3 |
| HD179218 | 72$^a$ | 22 | $<$27 |

: Subsample of targets with long-wavelength PAH intensities, original data from (cite: Acke2010)

\
$^a$ 6.2 $\mu$m flux taken from (cite: Habart2004).\

|  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| Target | ALMA dataset | Frequency | Beam size | Total flux | $M_{\rm dust,total,20K}$ | $M_{\rm warm dust,>30K}$ | $R_{in}^a$ | $R_{size}^b$ | Origin$^a$ |  |  |
|  |  | (GHz) | (") | (mJy) | ($M_{\oplus}$) | ($M_{\oplus}$) | (au) | (au) |  |  |  |
| ABAur | 2012.1.00303.S | 338 | 0.31x0.17 | 181 | 45$\pm$5 | 26$\pm$3 | 150 | 214 | 0 |  |  |
| Elias1/V892Tau | 2013.1.00498.S | 225 | 0.23x0.16 | 284 | 120$\pm$12 | 73$\pm$7 | 29 | 54 | 1 |  |  |
| HD100453 | 2017.1.01424.S | 281 | 0.03x0.02 | 218 | 39$\pm$4 | 23$\pm$2 | 30 | 42 | 2 |  |  |
| HD100546 | 2016.1.00344.S | 225 | 0.04x0.02 | 397 | 145$\pm$15 | 87$\pm$9 | 25 | 72 | 2 |  |  |
| HD135344B | 2016.1.00340.S | 155 | 0.09x0.06 | 43 | 67$\pm$7 | 33$\pm$3 | 52 | 91 | 3 |  |  |
| HD139614 | 2022.1.01302.S | 226 | 0.16x0.12 | 164 | 90$\pm$9 | 34$\pm$3 | 19 | 70 | 4 |  |  |
| HD142527 | 2012.1.00631.S | 322 | 0.12x0.09 | 898 | 659$\pm$66 | 243$\pm$24 | 185 | 238 | 2 |  |  |
| HD169142 | 2016.1.00344.S | 225 | 0.05x0.03 | 135 | 53$\pm$5 | 32$\pm$3 | 24 | 67 | 2 |  |  |
| HD97048 | 2016.1.00826.S | 338 | 0.06x0.03 | 2061 | 730$\pm$73 | 167$\pm$17 | 63 | 226 | 2 |  |  |
| IRS48 | 2013.1.00100.S | 343 | 0.18x0.13 | 163 | 29$\pm$3 | 17$\pm$2 | 70 | 98 | 5 |  |  |
| SR21 | 2018.1.00689.S | 217 | 0.05x0.05 | 96 | 55$\pm$6 | 33$\pm$3 | 56 | 66 | 6 |  |  |
| SYCha | 2018.1.00689.S | 217 | 0.12x0.08 | 58 | 57$\pm$6 | 3$\pm$0.3 | 35 | 298 | 7 |  |  |
| TCha | 2015.1.00979.S | 97 | 0.08x0.04 | 15 | 51$\pm$5 | 8$\pm$1 | 34 | 54 | 2 |  |  |
| GWLup | DSHARP | 231 | 0.04x0.03 | 83 | 51$\pm$5 | 3$\pm$0.3 | 0.04 | 97 | 9 |  |  |
| HD142666 | DSHARP | 232 | 0.03x0.02 | 131 | 80$\pm$8 | 43$\pm$4 | 0.21 | 54 | 9 |  |  |
| HD163296 | DSHARP | 239 | 0.05x0.04 | 634 | 166$\pm$17 | 64$\pm$6 | 0.29 | 130 | 9 |  |  |
| IMLup | DSHARP | 231 | 0.04x0.04 | 209 | 134$\pm$13 | 20$\pm$2 | 0.11 | 242 | 9 |  |  |
| RULup | DSHARP | 231 | 0.03x0.02 | 195 | 127$\pm$13 | 25$\pm$3 | 0.09 | 79 | 9 |  |  |
| V1121Oph/AS209 | DSHARP | 231 | 0.04x0.04 | 233 | 88$\pm$9 | 8$\pm$1 | 0.08 | 127 | 9 |  |  |
| WaOph6 | DSHARP | 231 | 0.06x0.05 | 156 | 61$\pm$6 | 15$\pm$2 | 0.12 | 91 | 9 |  |  |
| DoAr24E | 2016.1.00336.S | 225 | 0.11x0.09 | 6 | 4$\pm$0.4 | 2$\pm$0.2 | 0.09 | 6 | 10 |  |  |
| GQLup | 2015.1.00773.S | 240 | 0.05x0.02 | 24 | 14$\pm$1.4 | 5$\pm$0.5 | 0.07 | 30 | 8 |  |  |
| Haro1-17 | 2013.1.00157.S | 344 | 0.16x0.14 | 9 | 2$\pm$0.2 | 0.1$\pm$0.01 | 0.03 | 9 | 11 |  |  |
| HD104237/DXCha | 2021.1.01137.S | 225 | 0.17x0.10 | 88 | 31$\pm$3 | 18$\pm$2 | 0.32 | 9 | 12 |  |  |
| HD179218 | 2021.1.00709.S | 105 | 0.24x0.19 | 5 | 87$\pm$9 | 55$\pm$6 | 0.74 | 21 | 12 |  |  |
| Sz73 | 2018.1.01458.S | 226 | 0.08x0.06 | 11 | 8$\pm$1 | $<$8 | 0.03 | 5 | 12 |  |  |
| WXCha | 2021.1.00854.S | 233 | 0.45x0.22 | 9 | 10$\pm$1 | $<$10 | 0.06 | $<$19 | 12 |  |  |

\
$^a$ Inner edge dust disk: either cavity radius for transition disks or dust sublimation radius (where T$>$1500 K) for compact/ring disks\
$^b$ Dust disk size, see text for definition. $^c$ References published ALMA images: 0) (cite: vanderMarel2021-asymm), 1) (cite: Pinilla2018), 2) (cite: Francis2020), 3) (cite: Cazzoletti2018), 4) Bosschaart et al. subm., 5) (cite: vanderMarel2021-irs48), 6) (cite: Yang2023), 7) (cite: Orihara2023), 8) (cite: Wu2017), 9) (cite: Andrews2018), 10) (cite: Ansdell2020), 11) (cite: Cox2017), 12) Product fits file.

## ALMA data

High-resolution ALMA dust continuum images are available for all targets (for the image gallery, see Figure [7](#fig:gallery)). The majority of these images have been previously published, and we use the published images for this work. For 5 targets we use the product fits files directly from the ALMA archive as these are sufficient for our purposes. All information on the ALMA images are listed in Table [\[tbl:almadata\]](#tbl:almadata). The disks are classified as either a transition disk (TD) with an inner dust cavity, a ring disk (RD) with multiple dust rings (but no inner cavity) or a compact disk (CD) with no evidence for dust rings and a dust disk radius $<$20 au, following the classification by (cite: vdMMulders2021). The ALMA continuum images are used to derive the radial intensity profile of the dust continuum, integrated flux and dust disk size, as explained in the next section.

The comparison of the ALMA disk morphology with the scaled PAH intensities immediately reveals that the two are not uniquely linked, but that the spectral type plays a role as well: 5 of the 13 transition disks have an upper limit of the 3.3 PAH feature, both for early and late type stars; the 7 ring disks have both upper limits and (weak) detections, irrespective of spectral type and for the compact disks only 1 disk has a strong PAH detection, whereas this is not the only early type star. Therefore, the combination of disk morphology and spectral type likely plays a role.

![](Profiles.pdf)

# Analysis

In the first step of the analysis, we check whether the PAH intensity at 3.3 $\mu$m is correlated with the stellar luminosity, FUV radiation field or disk dust mass. The FUV radiation field is computed from the stellar spectrum and the accretion rate, using the Kurucz models in combination with a 10,000 K blackbody scaled to the accretion luminosity, following the method by (cite: Kama2016). The FUV luminosity $L_{FUV}$ is computed by integrating the stellar spectrum between 912-2050 $\AA$. The FUV radiation field across the disk, named $\chi$, is estimated from $L_{FUV}$ at a distance of 150 au from the star, scaled to the interstellar radiation field ISRF (1.6$\cdot10^{-6}$ W m$^{-2}$ (cite: Habing1968), following the approach from previous works (cite: Habart2004), where a correlation with this parameter is equivalent to a correlation with the FUV luminosity itself. Furthermore, we estimate the FUV radiation field at the inner edge of the disk $R_{in}$, which is either the cavity radius for the transition disks or the dust sublimation radius (defined as $R_{\rm sub}\approx0.07(L_*/L_{\odot})^{1/2}$, assuming $T_{\rm sub}=$1500 K, (cite: Dullemond2001)) for other disks, as well as the radiation field at the outer edge of the dust disk, taken as the size of the dust disk $R_{\rm size}$.

The dust disk size $R_{\rm size}$ is derived from the ALMA images (Figure [7](#fig:gallery)) using a curve-of-growth method, encircling 90% of the total flux, following previous works (cite: Tripathi2017). The compact disks are only marginally resolved, so for those disks we use the CASA `imfit` task to estimate the FWHM to measure the radius of each dust disk. For the majority of targets $R_{\rm size}$ is measured at $\sim$1 mm wavelength (ALMA Band 6 or 7), only for HD135344B, T Cha and HD179218 longer wavelength images were used, which means that their disk sizes could be somewhat larger at 1 mm. These radii are listed in Table [\[tbl:almadata\]](#tbl:almadata).

Finally, we estimate the total dust mass using the common equation related to the total millimeter flux $F_{\nu}$, for an assumed temperature of 20 K and optically thin emission (cite: Hildebrand1983): $$\begin{equation}
\label{eqn:mdust}
M_{dust}=\frac{F_{\nu}d^2}{\kappa_{\nu}B_{\nu}(T)}    
\end{equation}$$ with distance $d$, Planck function $B_{\nu}$, dust opacity $\kappa_{\nu}$ (where $\kappa_{1000GHz}=10$ g cm$^{-2}$ and $\kappa_{\nu}\propto\nu^\beta$ with $\beta$=1). The uncertainty on this parameter is 10%, following the flux calibration uncertainty of ALMA. Furthermore, the assumption of optically thin emission may not be fully valid in protoplanetary disks, and the dust mass values are technically lower limits to the pebble mass (cite: Zhu2019). However, as all disks are computed in the same way, the assumption is sufficient for the comparison in this work.

Second, we estimate the warm dust mass in each disk using the spatially resolved ALMA emission inside the 30 K radius, where at least the CO ice is fully sublimated in the midplane, in a similar way as (cite: vanderMarel2021-c2h). The midplane temperature profile of each disk is estimated using a power-law profile assuming a passively heated disk, following (cite: Chiang1997): $$\begin{equation}
\label{eqn:temp}
    T(r)=\left(\frac{L_*\phi}{8\pi\sigma_{SB}r^2}\right)^{1/4}
\end{equation}$$ with the stellar luminosity $L_*$, flaring angle $\phi$=0.02, $\sigma_{SB}$ the Stefan-Boltzmann constant and radius $r$. Transition disks generally have a different temperature profile due to their empty cavity and heated cavity edge, and their temperature profiles are estimated individually using a RADMC-3D model fitting the Spectral Energy Distribution (see Section [8](#sec:SEDs)).

![](PAH_otherplots_update2.pdf)

Using these temperature profiles, we derive the radius of the CO snowline in each disk, for which different values have been found, ranging between 18 to 35 K (cite: Bisschop2006; Pinte2018; Qi2019; Minissale2022; Guilloteau2025). The warm dust mass flux is computed for each disk by integrating the millimeter flux from 0 out to the radius where the midplane temperature drops below 30 K, which is spatially resolved in all cases except WX Cha and Sz73. Figure [2](#fig:profiles) shows the radial intensity profiles of each ALMA millimeter image with the 22-30 K regime and spatial resolution indicated. Whereas the exact cutoff temperature will impact the warm dust mass, this range shows that the impact is generally negligible. Using this flux and Equation [\[eqn:mdust\]](#eqn:mdust) for T=30 K, we compute the warm dust mass, which is listed in Table [\[tbl:almadata\]](#tbl:almadata). Although the temperature increases to $\gg$30 K within the warm dust region, the dust mass will be dominated by the temperature at the outer radius due to the shape of the temperature profile and 30 K is a reasonable choice. The uncertainty on the warm dust mass is again 10%, following the flux calibration uncertainty of ALMA. For WX Cha and Sz73, the spatial resolution is insufficient to resolve the emission around the CO snowline and we use an upper limit to the total dust mass as value.

In 10 out of 26 targets, the millimeter emission is entirely inside the 30 K radius, and the integrated flux for the warm dust mass is equal to the total flux. In that case, the difference between total and warm dust mass is caused by the assumption of the temperature in $B_{\nu}(T)$ in Eqn [\[eqn:mdust\]](#eqn:mdust), and changes by a factor 1.7. For all other disks, the warm dust mass is (much) lower than the total dust mass, up to a factor 18.

![](PAH_mainplot_update2.pdf)

# Results

Figure [3](#fig:PAH_other) shows the 3.3 $\mu$m PAH intensity as a function of various radiation properties as well as the total dust mass. Using the `linmix` package (cite: Kelly2007), we perform a linear fit to the logarithmic data including the upper limits. We have scaled the 5$\sigma$ limits on the PAH intensity to 3$\sigma$ limits for consistency with the linmix methodology in these plots and calculations. We find Pearson correlation coefficients as reported in the lower left corner of each plot: $R=0.80\pm0.10, -0.15\pm0.19, 0.52\pm0.18$ and 0.59$\pm$0.17 for correlations with the FUV radiation field $\chi$, FUV at the inner disk edge, FUV at the outer disk edge and total dust mass, respectively. We also compute the Pearson correlation coefficients of the fit of the data of the detected PAH intensities only (excluding the upper limits from the fit), which generally results in somewhat lower correlation coefficients with larger error bars: $R=0.63\pm0.23, -0.23\pm0.30, 0.41\pm0.30$ and $0.54\pm0.26$.

These results imply that a correlation exists for $\chi$, as well as a tentative correlation for the total dust mass and an even more moderate correlation with the FUV at the outer disk edge. This is consistent with earlier suggestions by models that the PAH intensity may scale with the radiation field (cite: Habart2004). All plots show large scatter, in particular when considering the upper limits. The correlation is not unambiguous and does not explain why disks with similar spectral type or similar disk morphology show such a wide spread in PAH intensity.

Second, Figure [4](#fig:PAHmain) shows the 3.3 $\mu$m PAH intensity as function of the warm dust mass, computed from the flux inside the 30 K radius. For some disks the warm dust mass is an upper limit, as the continuum emission was insufficiently resolved with respect to the CO snowline (see Figure [2](#fig:profiles)). The data points show clear evidence for a correlation between the two parameters. Analysis with `linmix` including the PAH intensity upper limits results in a Pearson correlation coefficient of $r=0.88\pm0.07$, consistent with a very strong correlation. When considering only the data points of detected PAH 3.3 $\mu$m intensities, the Pearson correlation coefficient is $R=0.71\pm0.21$, showing that the upper limits are important drivers of the correlation.

The three groups of disks (transition, compact or ring disks) are color-coded to check for trends as well. Transition disks are found across the range of PAH intensity, consistent with a variation of warm and cold dust traps (cite: vanderMarel2023) and some of the strongest PAH intensities are found in transition disks. On the other hand, if the dust trap is ‘cold’ (outside the 30 K radius) such as SY Cha and T Cha, the PAH intensity is much lower. Although compact disks are warm, their dust mass tends to be lower in most cases due to their smaller size and thus millimeter flux. An obvious outlier is HD179218 with a very strong PAH flux for its warm dust mass. Half of the ring disks show a moderate PAH intensity. Whereas ring disks have similar total dust masses as transition disks, the bulk of their dust mass is relatively cold. One outlier here is HD163296, with a rather low PAH intensity limit compared to its warm dust mass.

Finally, we consider the correlation between the warm dust mass and three other PAH features at 6.2, 8.6 and 11.3 $\mu$m for a subsample of our targets. The relation between these parameters is shown in Figure [5](#fig:pahacke). The correlation coefficient is again computed using `linmix` (including upper limits), resulting in Pearson coefficients of typically 0.5$\pm$0.3 (see Figure), i.e. moderately positive correlations, although within uncertainties still matching with the 3.3 um correlation in a much larger sample. However, if we compute the correlation coefficient for the 3.3 $\mu$m feature for this subsample only, the Pearson correlation coefficient is $R=0.42\pm0.32$, i.e. the correlation disappears. This implies that there is some intrinsic scatter in the PAH intensities when restricting to a smaller subsample.

![](PAH_Acke_features_update.pdf)

# Discussion

## Origin of PAH emission in protoplanetary disks

The strong correlation between the warm dust mass and the 3.3$\mu$m PAH intensity regardless of disk morphology provides evidence for a scenario where PAHs are sublimated from icy dust pebbles transported vertically upwards, after those pebbles have drifted inwards toward the pressure bump(s) in the disks. This is comparable to the findings of e.g. (cite: vanderMarel2021-irs48) and (cite: Booth2021-hd100) on the release of CH$_3$OH ice into the gas-phase in IRS48 and HD100546 from the main dust traps in those disks. Fragmentation and vertical transport through turbulence is required, as PAHs sublimate at high temperatures $>$150-300 K compared to the midplane temperature, which are only reached at higher scale heights at the dust locations (cite: Bruderer2012; vanderMarel2021-irs48). This is consistent with the predictions from PAH disk models from (cite: Lange2023) who have calculated in which layers of the disk PAHs are dissociated and form clusters. Our proposed scenario is similar to this idea, with the additional insight that locked up PAHs are transported with the pebbles toward their final location in the disk, where they only desorb if the local temperature is above the PAH sublimation temperature. If the majority of PAHs remain locked up in ‘cold’ dust traps (such as seen in e.g. SY Cha and in the ring disks), the observed PAH intensity from gas-phase PAHs remains low. In this way, PAH intensities can be explained for the range of T Tauris and Herbigs as well as their individual dust substructures.

On the other hand, for PAH features at longer wavelengths these correlations are potentially weaker (Figure [5](#fig:pahacke)). This correlation only cover a small part of the sample though, including only Herbig disks. This results in larger uncertainties on the correlation coefficient, and a lack of disks where the bulk of the dust mass is ‘cold’ (i.e. outside the CO snowline). The correlation coefficient of the 3.3 $\mu$m feature is indeed much lower as well if only this subsample is considered. Furthermore, (cite: Geers2007) reports the non-detection of the 8.6 $\mu$m PAH feature in T Cha, SY Cha, and WX Cha, with very weak and non-detections of the 11.3 $\mu$m PAH feature, which are all T Tauri disks with small warm dust masses. As quantitative information is missing, these targets could not be added to our plot, but such data certainly strengthens the correlation. The observed trend at the long wavelength PAH features thus does not contradict the findings for the 3.3 $\mu$m feature and is consistent with the main hypothesis. It is also possible that the PAH intensity is not a sufficiently direct tracer of the amount of released PAHs, and thus, of the amount of warm dust pebbles, and therefore, the correlation is not reflected by the properties of the detected targets alone: the correlation is driven by the combination of deep upper limits and strong detections corresponding to a range of warm dust masses.

If PAHs are indeed locked up in ices in protoplanetary disks and only revealed in infrared observations due to sublimation, this implicates significantly high amounts of PAHs being present in planet forming regions, but mostly in solid form. This is particularly interesting in high UV regions, as irradiated ices have been shown to rapidly form organic macromolecules (cite: Ligterink2024). The destruction of PAHs through UV radiation into smaller components may result in a more efficient formation process of such macromolecules (cite: Alexander2008). On the other hand, there is also the possibility that (frozen) PAHs in disks are not inherited from the interstellar medium, but formed in situ under the influence of radiation. However, the omnipresence of PAHs in the ISM makes this unnecessary, and a thorough investigation of the fractional abundances of PAHs in disks compared to ISM would be required to test this.

## Outliers in the warm dust - PAH intensity correlation

The two exceptions in the main correlation with the 3.3 $\mu$m feature in Figure [4](#fig:PAHmain) are HD179218 and HD163296. HD179218 has a very high PAH intensity for its warm dust mass, also seen in the correlations with the 6.2 and 8.6 $\mu$m features. However, since this is a compact disk, it is plausible that the warm dust mass is underestimated by a factor of a few due to optically thick emission, as Eqn. [\[eqn:mdust\]](#eqn:mdust) is only valid for optically thin emission. This would bring this datapoint in line with the observed trend. Second, HD163296 appears to lie below the trend with an upper limit on the 3.3 $\mu$m PAH intensity and a fairly high warm dust mass. However, inspection of its radial profile in Figure [2](#fig:profiles) shows that there is a rather wide dust gap outside the CO snowline and it is possible that the majority of icy dust pebbles is halted outside, lowering the amount that ends up in the warm region. This would decrease the amount of sublimating icy pebbles in this disk and move also this datapoint closer to the general trend. This is a complex problem as it depends on which dust traps form first in the disk (cite: Pinilla2015). Quantifying the amount of icy pebbles that make it through the gap is however beyond the scope of this work. Removing HD179218 and HD163296 from the sample of Figure [4](#fig:PAHmain) increases the Pearson correlation coefficient to $R=0.94\pm0.04$. Potential other outliers in the long wavelength PAH features in Figure [5](#fig:pahacke) are HD104237 and HD139614, for which the PAH upper limits appear to be very low compared to the main trend.

In the sample selection, a number of targets from the original samples of (cite: Habart2004) and (cite: Geers2007) were excluded to ensure that the analysis would be consistent. For the majority of those targets only upper limits on the PAH 3.3 $\mu$m were reported. A remarkably bright PAH source is HD98922, a massive A0 Herbig star at 650 pc of 5.5 $M_{\odot}$ and 1200 $L_{\odot}$ with a flat SED and faint polarized emission (cite: Garufi2022). As these authors report, only low-resolution ALMA data exist (2015.1.01600.S) and the disk is detected but unresolved. If this system follows the trend from Figure [4](#fig:PAHmain), the warm dust mass is expected to be very high. Determining the warm dust mass would require higher resolution data and a full modeling of the temperature structure which is left for future work.

## Spatially resolved PAH emission

![](Spatialcurve.pdf)

From the integrated fluxes studied in this work it remains unclear if the PAH emission indeed originates from the dust trap region. For a subset of 7 targets in our sample (AB Aur, HD100453, HD100546, HD169142, HD97048, IRS48 and HD163206, mostly transition disks), spatially resolved information of the PAH features is available in the literature. The spatial extent of the 3.3 $\mu$m feature has been estimated for HD97048, IRS48, HD100453, HD100546 and HD169142 using VLT/NACO data (cite: Habart2006; Geers2007; Bouteraon2019). These profiles are somewhat broader than the PSF of $\sim$0.1-0.2" so although it is not possible to radially resolve a profile or constrain the inner edge, the spatial extent could be determined, which ranges up to radii of 0.9". For the 8.6 and 11.3 $\mu$m feature, the spatially resolved intensity profiles have been obtained with the VISIR-NEAR instrument for ABAur, HD100546, HD97048, HD169142 and HD163296 (cite: Yoffe2023). For IRS48, the spatial extent of these features is constrained with VISIR where the inner edge remains unconstrained (cite: Geers2007-irs48).

Figure [6](#fig:spatial) shows the spatial extent of the 3.3, 8.6 and 11.3 $\mu$m features from the literature described above. The 3.3 $\mu$m feature is indicated as a horizontal bar, where the inner part shows a dotted profile of the PSF size to indicate the inner edge is unconstrained. Since the 3.3 $\mu$m feature is only marginally resolved, its emission may be ring-like as well. The other two features are taken directly from (cite: Yoffe2023), where available. For HD169142, the 11.3 $\mu$m emission is consistent with a ring of 0.14-0.17" radius (cite: Devinat2022; Yoffe2023), so this is overlaid as well. These PAH extents are compared in Figure [6](#fig:spatial) with the $^{13}$CO 3–2 or 2–1 radial profiles taken from (cite: Wolfer2023) and the ALMA continuum as derived in Figure [2](#fig:profiles). For HD100453 only $^{12}$CO 3-2 data were available. The spatially resolved $^{13}$CO 3–2 or 2–1 line provides a proxy of the gas gap inside the dust cavity (cite: vanderMarel2016-isot; Facchini2017), although the gap depth could be overestimated if the gas is too warm to excite these transitions (cite: Leemker2022). The $^{12}$CO line of HD100453 becomes optically thin as well in the very inner part of the cavity, revealing the deepest part of the gas gap.

For AB Aur, HD100546, HD169142, HD97048, IRS48 and potentially HD100453 the PAH emission peaks inside the cavity. For HD169142 and HD100546, the spatially resolved PAH ring is close to the inner edge of the dust ring, for AB Aur the PAH ring is well inside. For HD163296, the PAH ring appears to coincide with the third dust ring. Therefore, the spatial information also shows that PAH emission is possibly correlated with the dust trap, hinting that these could be PAHs sublimating from vertically stirred grains. The emission does not fully correspond to the location of the dust ring or dust crescent itself like for example the CH$_3$OH emission in IRS48 (cite: vanderMarel2021-irs48). However, since gas extends within the cavity as seen in the $^{13}$CO emission, as well as from the high accretion rates of each of these disks (Table [\[tbl:sample\]](#tbl:sample)), the sublimated PAHs may follow the accretion flow through the gap without getting destroyed, and emit primarily in the inner region with the highest UV radiation. In contrast, the reason that the CH$_3$OH emission in IRS48 has the same morphology as the dust crescent is because the gas molecules are rapidly photodissociated outside the dust trap, and continuously replenished at the dust trap through sublimation (cite: Temmink2025). Furthermore, the PAH emission sometimes also extends out to larger radii. Additional radial transport, such as turbulent mixing and diffusion likely play a role here, and sublimation is not the sole process setting the radial extent of the PAH emission. Further studies including sublimation and transport processes are required to fully quantify this.

# Conclusions

In this study, we analyzed the PAH intensity of the 3.3 $\mu$m feature for a large sample of T Tauri and Herbig disks from the literature, as well as the 6.2, 8.6 and 11.3 $\mu$m PAH features for a subset of Herbig disks, to test for correlations with disk and radiation properties. We conclude the following:

- A strong correlation with a Pearson coefficient of 0.88$\pm$0.08 was found between the 3.3 $\mu$m PAH intensity and the warm dust mass, which is defined as the millimeter dust mass measured from ALMA continuum observations within the 30 K midplane radius.

- The 3.3 $\mu$m PAH intensity has (much) weaker correlations with other relevant parameters such as the FUV luminosity, the FUV radiation field at inner and outer edge of the disk and the total dust mass.

- The 6.2, 8.6 and 11.3 $\mu$m features show somewhat weaker correlations with warm dust mass for a smaller subsample, but within uncertainties matching with the correlation of the 3.3 um feature.

- The spatial distribution of the PAH features (where available) is generally inside of the dust trap locations, suggesting that gas-phase PAHs may follow the accretion flow after sublimation without getting destroyed, although additional transport like diffusion and turbulent mixing may also play a role.

- The correlation with warm dust mass is consistent with the hypothesis that PAHs are generally frozen out in protoplanetary disks, and only become detectable in the gas-phase when icy pebbles drift inwards, get transported vertically upwards and sublimate their icy layers, similar to previous findings for complex organic molecules (COMs) in dust traps (cite: vanderMarel2021-irs48; Booth2021-hd100). This can explain the PAH intensity w.r.t. the range in dust disk morphologies and stellar luminosities in the sample.

- The findings regarding PAH sublimation provide further evidence that disk composition is governed by icy pebble transport, rather than a static chemical equilibrium disk.

# Acknowledgements

We thank the referee for their thorough report and useful suggestions. We would also like to thank Margot Leemker, Kevin Lange, Rens Waters, Ella de Vries and Judith Moulijn for useful discussions. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00631.S, 2013.1.00100.S, 2013.1.00157.S, 2013.1.00498.S, 2015.1.00773.S, 2015.1.00979.S, 2016.1.00336.S, 2016.1.00340.S, 2016.1.00344.S, 2016.1.00484.L, 2016.1.00826.S, 2017.1.01424.S, 2018.1.00689.S, 2018.1.01458.S, 2021.1.00709.S, 2021.1.00854.S, 2021.1.01137.S, 2022.1.01302.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# ALMA gallery

This Appendix contains the ALMA images analyzed in this work.

![](Gallery.png)

# SEDs of transition disks

In this section we present the Spectral Energy Distributions (SEDs) and mid-plane temperature profiles of the transition disks in this study based on RADMC-3D modeling, since their temperature cannot be estimated with a simple power-law.

For HD135344B, HD169142 and HD97048, SED radiative transfer modeling was performed by (cite: vanderMarel2019), and we use their derived temperature profiles. For IRS48, we use the mid-plane temperature profile from (cite: vanderMarel2021-irs48) and for HD142527, we use the profile from (cite: Temmink2023).

For the other transition disks, no SED fits with temperature profiles were available in the literature, so we fit RADMC-3D models ourselves. The SEDs were constructed using photometry from Johnson BVR, Gaia, 2MASS, *WISE*, *Spitzer*, *IRAS*, *Herschel/PACS* and ALMA millimeter fluxes from this study. The optical-near infrared photometric data points were corrected for extinction using the $A_V$ values from (cite: Francis2020). For the fitting itself we follow a similar procedure as (cite: Temmink2023), but with a power-law surface density with an empty cavity inside cavity radius $r_{\rm cav}$ and an inner dust disk of 1 au which is depleted by a factor $\delta_{\rm dust}$. The outer radius is set at 150 au and the surface density is scaled to the total gas disk mass $M_{\rm disk}$ with a gas-to-dust ratio of 100. The dust opacities are computed using a combination of a small grain and large grain population, of 0.005-1 $\mu$m and 0.005-1000 $\mu$m, respectively. The vertical scale height is described by $h(r)=h_c({r}/{r_c})^{\psi}$ with $\psi=0.15$ and characteristic radius $r_c$=50 au. Stellar parameters are taken from Table [\[tbl:sample\]](#tbl:sample).

The free parameters in the model are thus the total disk mass $M_{\rm disk}$, the vertical height $h_c$ at characteristic radius $r_c$, the cavity radius $r_{\rm cav}$ and inner disk depletion factor $\delta_{\rm dust}$. The models were fit to both the radial continuum profiles and the SEDs. The final SEDs with their best fit models are shown in Figure [8](#fig:seds) and the best-fit parameters are given in Table [2](#tbl:sedfits). For T Cha, the SED fit had to be run at lower inclination than for the continuum image due to the obscuration of the star by the inner disk, indicating that the inner disk may be misaligned with the outer disk, similar to RY Lup (cite: vanderMarel2018).

|          |                       |       |               |                     |
|:---------|:----------------------|:------|:--------------|:--------------------|
| Target   | $M_{\rm disk}^a$      | $h_c$ | $r_{\rm cav}$ | $\delta_{\rm dust}$ |
|          | ($10^{-3} M_{\odot}$) |       | (au)          |                     |
| V892Tau  | 4                     | 0.05  | 23            | 10$^{-3}$           |
| HD100453 | 2                     | 0.20  | 32            | 10$^{-2}$           |
| HD100546 | 8                     | 0.20  | 30            | 10$^{-1}$           |
| HD139614 | 6.6                   | 0.10  | 13            | 10$^{0}$            |
| SR21     | 4                     | 0.15  | 60            | 10$^{-3}$           |
| SYCha    | 10                    | 0.10  | 106           | 10$^{0}$            |
| TCha     | 10                    | 0.10  | 28            | 10$^{-1}$           |

: Best-fit parameters SEDs

\
$^a$) $M_{\rm disk}$ is the total disk gas mass: the disk dust mass is computed within RADMC-3D assuming a gas-to-dust ratio of 100.

![](AllSEDs.pdf)

![](Temperatures_TDs.pdf)

</paper>

Write the methods card for this paper.