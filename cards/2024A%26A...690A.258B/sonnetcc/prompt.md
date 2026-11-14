# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...690A.258B\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...690A.258B",
 "title": "ALMACAL: XII. Data characterisation and products",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Bollo, Victoria",
 "n_authors": 8,
 "arxiv_id": "2409.07166",
 "doi": "10.1051/0004-6361/202450336",
 "alma_projects_linked_by_archive": [
  "2012.1.00193.S",
  "2012.1.00268.S",
  "2012.1.00275.S",
  "2012.1.00303.S",
  "2012.1.00374.S",
  "2012.1.00496.S",
  "2012.1.00743.S",
  "2012.1.01069.S",
  "2012.1.01099.S",
  "2013.1.00111.S",
  "2013.1.00166.S",
  "2013.1.00553.S",
  "2013.1.00645.S",
  "2013.1.00658.S",
  "2013.1.00916.S",
  "2013.1.00988.S",
  "2013.1.01034.S",
  "2013.1.01110.S",
  "2013.1.01175.S",
  "2013.1.01195.S",
  "2015.1.00041.S",
  "2015.1.00188.S",
  "2015.1.00350.S",
  "2015.1.00410.S",
  "2015.1.00530.S",
  "2015.1.00669.S",
  "2015.1.00678.S",
  "2015.1.00856.S",
  "2015.1.00896.S",
  "2015.1.00986.S",
  "2015.1.01005.S",
  "2015.1.01054.S",
  "2015.1.01133.S",
  "2015.1.01222.S",
  "2015.1.01548.S",
  "2015.1.01602.S",
  "2016.1.00115.S",
  "2016.1.00119.S",
  "2016.1.00138.S",
  "2016.1.00447.S",
  "2016.1.00630.S",
  "2016.1.01135.S",
  "2016.1.01164.S",
  "2016.1.01284.S",
  "2016.1.01326.S",
  "2016.1.01398.S",
  "2016.1.01456.S",
  "2017.1.00280.S",
  "2017.1.00321.S",
  "2017.1.00707.S",
  "2017.1.00717.S",
  "2017.1.00941.S",
  "2017.1.00964.S",
  "2017.1.01027.S",
  "2017.1.01093.S",
  "2017.1.01347.S",
  "2017.1.01658.S",
  "2018.1.00035.L",
  "2018.1.00162.S",
  "2018.1.00276.S",
  "2018.1.00306.S",
  "2018.1.00538.S",
  "2018.1.00585.S",
  "2018.1.00781.S",
  "2018.1.00900.S",
  "2018.1.00992.S",
  "2018.1.01038.S",
  "2018.1.01119.S",
  "2018.1.01194.S",
  "2018.1.01241.S",
  "2018.1.01344.S",
  "2018.1.01438.S",
  "2018.1.01617.T",
  "2018.1.01740.S",
  "2018.1.01766.T",
  "2018.1.01812.S",
  "2018.A.00065.T",
  "2019.1.00061.S",
  "2019.1.00130.S",
  "2019.1.00260.S",
  "2019.1.00337.S",
  "2019.1.00397.S",
  "2019.1.00411.S",
  "2019.1.00447.S",
  "2019.1.00458.S",
  "2019.1.00597.S",
  "2019.1.00708.S",
  "2019.1.00801.S",
  "2019.1.01022.S",
  "2019.1.01027.S",
  "2019.1.01118.S",
  "2019.1.01136.S",
  "2019.1.01178.S",
  "2019.1.01190.S",
  "2019.1.01317.S",
  "2019.1.01337.S",
  "2019.1.01422.S",
  "2019.1.01437.S",
  "2019.1.01742.S",
  "2019.1.01813.S"
 ]
}
```

Paper text:
<paper>
# ALMACAL. XII. Data characterisation and products

# Introduction

Millimetre (mm) and sub-millimetre (sub-mm) observations offer a unique window into various astrophysical processes and phenomena in the Universe. At these wavelengths, key emission lines such as carbon monoxide (CO) and atomic and ionised carbon (\[CI\], \[CII\]) emit radiation that reveals essential information about molecular gas content, star-formation activity, and gas dynamics (cite: carilliCoolGasHighRedshift2013; tacconiEvolutionStarFormingInterstellar2020). Sub-mm observations help us explore the cosmic baryon cycle and the complex interplay between cold and dense molecular gas reservoirs, star formation activity, ionised gas, and dust emission (cite: perouxCosmicBaryonMetal2020).

Modern interferometers have produced large datasets consisting of hundreds to thousands of individual observations. In particular, the Atacama Large Millimeter/submillimeter Array (ALMA) is a pioneering observatory that provides high-resolution observations at mm and sub-mm wavelengths. Transforming the large volume of raw visibility (uv) data from ALMA into scientifically meaningful products is a significant task. This complex process includes several steps: calibration, imaging, and deconvolution.

ALMA has made remarkable progress in automating and ensuring high-quality calibration of interferometric data. These advances have been driven by the diligent efforts of the observatory staff and the success of ALMA’s sophisticated pipeline (cite: hunterALMAInterferometricPipeline2023), based on the Common Astronomy Software Applications (CASA) software (cite: mcmullinCASAArchitectureApplications2007). As a result, ALMA provides its users with meticulously calibrated visibilities, laying the groundwork for further processing and scientific analysis. Despite the effective functionality of the pipeline, certain complications can arise during the calibration process, requiring manual intervention. These complications can include unexpected radio frequency interference, atmospheric anomalies, or misbehaved antennas, all of which affect data quality. In such cases, the expertise of astronomers becomes crucial to correct or flag these problems, ensuring the integrity and reliability of the final scientific products.

Over the years, several large programs (LPs) have exploited the capabilities of ALMA to study the cosmic evolution of gas and stars. In particular, the ASPECS survey in the Hubble Ultra Deep Field (HUDF; (cite: walterALMASpectroscopicSurvey2016; decarliALMASPECTROSCOPICSURVEY2016)) aimed to detect CO and \[CI\] in galaxies without preselection at $z=1-3$ using Bands 3 and 6. ASPECS covered an area of 4.6 arcmin$^2$ in Band 3 and 2.9 arcmin$^2$ in Band 6. PHANGS–ALMA (cite: leroyPHANGSALMAArcsecondCO2021) is a survey of CO(2–1) emission from 90 nearby galaxies with a typical angular resolution of $\sim1.5''$ and a total survey area of 1050 arcmin$^2$. At higher redshifts, the REBELS survey (cite: bouwensReionizationEraBright2022) targeted 40 UV-bright galaxies at $z>6.5$, covering an area of 7 deg$^2$, and aimed to detect the \[CII\]$-$158$\mu$m and \[OIII\]$-$88$\mu$m lines as well as dust-continuum emission. The ALPINE survey (cite: lefevreALPINEALMACIISurvey2020) was designed to study 118 star-forming galaxies (SFGs) at $4 < z < 6$. This survey targeted the \[CII\] line and continuum emission, covering an area of 25 arcmin$^2$. The CRISTAL survey (cite: solimanoALMACRISTALSurveyDiscovery2024) selected 25 SFGs with available HST imaging and high stellar masses from the ALPINE sample ($\log$ M$_{\text{star}}$/M$_{\odot}$ $\geq 9.5$). CRISTAL targets \[CII\] with a resolution of $\sim 0.2''$, which is higher than its parent sample’s resolution of $\sim1''$. These surveys have played a key role in constraining the evolution of the molecular gas in galaxies across cosmic epochs. Using different molecular gas tracers shows that the evolution of the molecular gas mass density in the Universe aligns with the cosmic star formation history, providing insights into the process of gas accretion onto galaxies (cite: walterEvolutionBaryonsAssociated2020). In addition to the ALMA LPs, the ALMA Calibrator source catalogue has also been used by (cite: audibertCOALMARadioSource2022) on a representative sample of the NVSS (when flux limited to 0.4 mJy) to study the CO luminosity function up to redshift $z \sim 2.5$ and to assess the role of radioactivity in galaxy evolution. They found that most radio galaxies are more depleted and evolved than the typical simulated halo galaxy.

Other facilities have also been used for surveys of cold gas tracers. The Plateau de Bure High$-z$ Blue Sequence Survey 2 (PHIBSS2) (cite: guilloteauIRAMInterferometerPlateau1992), is a large observational campaign conducted with the Plateau de Bure Interferometer (PdBI), now part of the Northern Extended Millimeter Array (NOEMA) Observatory. With a frequency range spanning from 80 GHz to 350 GHz, (cite: lenkicPlateauBureHighz2020) searched for additional background emission lines in the fields of the original PHIBBSS survey. They explored the CO($2-1$), CO($3-2$), and CO($6-5$) emission lines in 110 main-sequence galaxies, covering a total area of $\sim130$ arcmin$^2$. This survey has been used to derive the molecular gas mass density evolution by converting high$-$J CO luminosity functions to CO($1-0$). Additionally, the COLDz survey looked directly for the CO($1-0$) emission at $z= 2-3$ and CO($2-1$) at $z = 5-7$ using more than 320 hrs of VLA time (cite: pavesiCOLuminosityDensity2018; riechersCOLDzShapeCO2019; riechersCOLDzHighSpace2020), covering a $\sim 60$ arcmin$^2$ area. However, the large uncertainties of these measurements reflect our limited understanding of the molecular gas content of galaxies across cosmic time.

Our current measurements of the molecular gas mass density ($\Omega_{\text{H}_2}$) reach redshift $z\sim 7$ and show that the density increases from early times, peaks at $z\sim 1-3$, and decreases to the present day (cite: tacconiHighMolecularGas2010; walterEvolutionBaryonsAssociated2020; hamanowiczALMACALVIIIPilot2022; aravenaALMAReionizationEra2023). However, one of the main challenges for the molecular gas surveys is the effect of cosmic variance, which introduces uncertainty on how well the sampled volume represents the Universe (cite: decarliALMASpectroscopicSurvey2020; poppingALMASpectroscopicSurvey2020; boogaardNOEMAMolecularLine2023). Cosmic variance, caused by natural fluctuations in the Universe’s large-scale structure, results in variations in the number density and distribution of cosmic objects across the sky (cite: driverQuantifyingCosmicVariance2010). Consequently, surveys covering limited sky areas may inadvertently sample regions that are unusually rich or devoid of galaxies, leading to biased estimates of cosmic properties such as the number density of galaxies, clustering, and luminosity function. Small sample sizes exacerbate this issue by introducing statistical uncertainties, which increases the probability of sampling regions with atypical characteristics. Several studies have investigated the effects of field-to-field variance on observables such as the luminosity function and the number density of galaxies (cite: keenanBiasesCosmicVariance2020; lenkicPlateauBureHighz2020; gkogkouCONCERTOSimulatingCO2022; boogaardNOEMAMolecularLine2023). Generally, there is a consensus on the significance of measuring the cosmic variance effect by comparing model predictions with observations and estimates from various sky regions (cite: poppingALMASpectroscopicSurvey2019). This is particularly crucial in deriving the molecular gas mass density of the Universe.

This paper presents a new survey based on ALMA calibrator data accumulated up to May 2022, which we denominated as ALMACAL$-22$. The original ALMACAL project started in 2016 (cite: oteoALMACALExploitingALMA2016) and has produced several scientific outcomes dedicated to studying molecular gas, dusty star-forming galaxies (DSFGs), absorption lines along the line of sight of quasars, and active galactic nucleus (AGN) physics. ALMACAL$-22$ was built on the experience of previous pilot ALMACAL surveys, but it has now been expanded to include longer integration times. As part of the strategy to exploit this large dataset, we present the details of processing and imaging data, along with different tests, to ensure the best quality of the sample selection. Here, we provide the characteristics and properties of this new dataset. We compare the strengths of ALMACAL$-22$ to previous surveys. This new survey covers 1047 fields across the southern sky, intending to alleviate the limitations introduced by Poisson errors due to limited statistics and cosmic variance. We review various studies conducted since ALMA Cycle 1 that have used extragalactic calibration data to explore interesting scientific cases (cite: oteoALMACALIIExtreme2017a; klitschALMACALAbsorptionselectedGalaxies2019; hamanowiczALMACALVIIIPilot2022; chenALMACALIXMultiband2022). We discuss how this new release, ALMACAL$-22$, can expand our understanding of molecular gas evolution, properties of DSFGs, extragalactic absorption lines, and AGN physics.

This paper is organised as follows. In Sect. [2](#sec:almacal) we describe the ALMACAL$-22$ survey, the calibration process (§[2.1](#sec:calibratio)), the selection of the pruned sample (Sect. [2.2](#sec:clean_sample_selection)), and the concatenation and imaging (Sect. [2.3](#sec:imaging)). In Sect. [3](#sec:properties) we explore the following properties: spatial distribution (Sect. [3.1](#sec:spatial_distribution)), spatial resolution (Sect. [3.2](#sec:spatial_resolution)), integration time (Sect. [3.3](#sec:integration_time)), and calibrator redshifts (Sect. [3.4](#sec:redshift)). Section [4](#sec:discussion) compares the strengths of ALMACAL$-22$ with the previous surveys and discusses the scientific areas where ALMACAL$-22$ will significantly contribute. In Sect. [5](#sec:conclusions) we summarise our key conclusions. Throughout this paper, we use $H_0 = 70$ kms$^{-1}$Mpc$^{-1}$, $\Omega_{\text{M}} =0.3$, and $\Omega_{\Lambda} = 0.7$.

# ALMA calibrator data

The ALMACAL$-22$ survey comprises archival data compiled from the calibration data used in every science project carried out by ALMA (cite: zwaanALMACALSurveyingUniverse2022). Each PI-led scientific project involves several observations of a calibrator source that is close to the science field. Most calibrators are bright sub-mm point sources classified as blazars (cite: bonatoALMACALIVCatalogue2018a) — AGN galaxies with a jet pointing towards the line of sight (cite: urryUnifiedSchemesRadioLoud1995). Blazars can be divided into two sub-classes: BL Lac objects, which are identified as radio galaxies, and flat-spectrum radio quasars (FSRQs), which are identified as quasars (cite: padovaniTwoMainClasses2017). When targeting a source with unknown structure and flux, calibration observations are crucial in interferometric astronomy. We used calibrator sources with well-known shapes and flux densities at (sub-)mm and radio wavelengths to adjust the bandpass response, set the flux density scale, and calibrate the amplitude and phase. This ensures we can correct for instrumental and atmospheric corruptions, providing accurate measurements of the target source. These calibration scans have exposure times and setups matching the project’s PI requests. Repeated use of the calibrators for ALMA science observations effectively creates deep observations that often cover a significant fraction of the sub-mm spectrum. The most popular calibrators have data from multiple observations of different ALMA bands. Multiple observations of ALMA calibrators create a high-sensitivity dataset that covers a significant sky area ($> 1000$ arcmin$^2$).

This paper presents 1047 calibration field data points accumulated from Cycle 1 (July 2012 - May 2022) from Band 3 through Band 10, resulting in a dataset of more than 30 Terabytes. These calibrator data are accessible to any user right after the main science dataset has passed quality assurance. In this section we explain the calibration process and subtraction of the calibrator at the centre of the pointing as well as the selection of the so-called pruned sample. Figure [1](#fig:spatial_distribution) shows the ALMACAL$-22$ field distribution on the sky for the full sample (top) and the pruned sample (bottom).

## Calibration

A dedicated ALMACAL pipeline was created to automate the processing of all delivered datasets. The complete pipeline description is available in (cite: oteoALMACALExploitingALMA2016), and the following is a brief overview of its essential components. This pipeline uses the `scriptForPI.py` script included in every delivered ALMA dataset, which generates fully calibrated data. While ALMA users use this script to create a final dataset, we used it to distinguish the calibrated calibrator data from the science observations. Next, we applied self-calibration to correct the short-time variability of the phase and amplitude during integration, improving the final image’s dynamic range. This process enabled us to create a model and remove the bright calibrator from the visibility data, resulting in the equivalent of blank sky or deep field observations.

During the execution of the ALMA calibration scripts, some bandpass calibrators needed to be consistently calibrated. Unlike with phase calibrators, calibration tables are not always applied to the bandpass calibrators. Most of the time, the bandpass calibrator is also the flux calibrator, so their solutions cannot be applied to themselves. To rectify this, the accurate flux density scale of the bandpass calibrators has to be recovered from the flux calibration table containing standardised values for each calibrator. Applying bandpass calibration tables to bandpass calibrators could, in principle, remove emission and absorption features from cubes that are constructed from these bandpass calibration observations. This could affect emission and absorption features at the phase centre. It should be noted, however, that the bandpass solution is spectrally averaged so that narrow spectral features are not calibrated out. Also, our ability to detect faint emission lines throughout the cubes is unaffected. Because emission lines on top of the quasar continuum are weak compared to the quasar continuum, they do not significantly affect the bandpass solution and do not affect the calibration quality of the data.

The calibration process extends to creating "pseudo-continuum" measurement sets, in which all channels within each spectral window are averaged. The averaging also boosts the signal-to-noise ratio (S/N) for the self-calibration. These files facilitate the implementation of two steps of self-calibration, initially focusing solely on phase and subsequently incorporating both amplitude and phase calibration. The solution interval for the calibration solution is set equal to the integration time. During the intervals of the self-calibration steps, a point source model is applied and fitted to the uv data. This approach offers the advantage of subtracting the point-source model independently for each observation, mitigating the impact of any flux variability in the calibration source. The final step involves deriving the calibrated visibilities and subtracting the continuum of the calibrator source to build line emission data cubes, thereby assembling the ALMACAL$-22$ dataset.

![image](figures/spatial_distribution_almacal_full.pdf) ![image](figures/spatial_distribution_almacal.pdf)

![](figures/rms_distribution.pdf)

## Pruned sample selection

While the central bright calibrator enables self-calibration, it introduces challenges to the scientific analysis. Most of the calibrators in our sample are blazars, but a few present extended structures that cannot be modelled as point sources. After subtracting the calibrator’s continuum at the centre of the pointing as a point source, these structures may remain as residuals since they are not taken into account during the cleaning process. These residuals affect the quality of the calibration process, resulting in strong continuum artefacts, interferometric patterns, or extra features that produce high noise values. To overcome this problem, we implemented a sequence of pruning steps to prevent any negative impact on the final combined images.

We analysed key properties, such as the integration time, frequency coverage, bandwidth of each spectral window, spatial resolution, and baseline distribution. We aim to obtain a coherently combined homogeneous sample that will provide broad statistics of the Universe, minimise cosmic variance, and cover the maximum possible volume.

The pruned sample includes only observations made with the 12-metre array. To create the deep cubes, we summed the on-source integration time of observations that covered the same frequency range. We chose bins of 1 GHz to select all the files spanning the same frequency across the extent of the ALMA band’s frequency coverage. To minimise contamination from artefacts, we used a multi-step approach. First, we created the continuum image for each measurement set using `CASA` and estimated the root-mean-square (RMS) noise. We chose to use the continuum image instead of the data cube because imaging the continuum is much faster and provides a good approximation of the quality of the files. We excluded files with an RMS value higher than $10^{-5}$ Jy, which introduced inconsistent noise patterns throughout the cube. Secondly, we estimated the theoretical sensitivity ($\sigma_{\text{theoretical}}$) associated with each observation by using the `apparentsens` function of the `CASA` image `toolkit`. This function calculates the point source sensitivity in imaged cubes, accounting for image weights and visibility weights, also used in the ALMA Interferometric Pipeline (cite: hunterALMAInterferometricPipeline2023). We insist that the measured RMS of each continuum imaged file compared with the theoretical sensitivity (ALMA pipeline) should not be greater than a factor of 3. We inspected a few files that were removed by the RMS criteria and found that most of them had strong interferometric patterns or errors in calibration. Figure  [2](#fig:rms_dist) shows the distribution ratio of the measured RMS and the theoretical RMS. The pruned sample extends by up to a factor of 3 with a median value of 1.8, while the full sample has a median value of 2.4. For comparison, the full sample reaches RMS ratios of hundreds. These high-RMS observations could introduce significant noise artefacts in the final data product.

Despite our efforts with the sample selection, we still found files with strong interferometric patterns, such as image artefacts, baseline stripes, blurring, or distortions in the image. In some cases, these patterns cannot be easily identified from the RMS of the continuum. Several errors can arise when one performs self-calibration using the pipeline, such as poor phase and amplitude calibration. These artefacts are usually caused by baseline errors due to uncertainties in the antenna position when measuring the differences in signal phase and amplitude between pairs of antennas. Artefacts can also appear during imaging, resulting in sidelobes, noise bias, and spatial distortion. The errors in interferometric data are primarily identified in the uv plane during calibration and imaging processes. Considering the large amount of data that the ALMACAL$-22$ survey contains, it is not possible to visualise all the observations in the uv plane to flag the possible misbehaved antennas. Thanks to our large amounts of data, we can afford to discard corrupted data by checking the continuum map of each observation to determine if it presents strong patterns. We visually identified the presence of stripes, blurring, artificial elongation or shifting of sources, and symmetric or asymmetric patterns, then discarded observations exhibiting these issues to ensure data quality. After removing $\sim 15 \%$ of the files, we combined the data with the same frequency coverage, selecting observations that contribute to a total integration time of at least 10 minutes.

We selected high-quality data to construct the survey. We started from a total of 34909 measurement sets (ms), that is, raw visibility files, of which 25594 add up to at least 10 minutes of integration time. Among these, 15270 files have acceptable RMS levels. After removing visual artefacts and reapplying the integration time criterion, we used 6494 ms files to build the pruned sample. Figure [3](#fig:subsample_selection) displays the distribution of the number of files in each band for both the full ALMACAL$-22$ and pruned samples in the left panel. Bands 3, 6, and 7 dominate the full sample, while Bands 3, 4, and 6 dominate the pruned sample. There are no Band 10 data available in the pruned sample. The middle panel shows the distribution of data cubes in both samples, where Bands 3, 4, 6, and 7 dominate (details on how cubes are constructed are discussed in Sect. [2.3](#sec:imaging)). The right panel shows the distribution of calibrators, with 1047 in the full sample and 401 in the pruned sample. For both samples, Band 3 has the most calibration fields, followed by 6 and 4.

![image](figures/nfiles_distribution.pdf) ![image](figures/ncubes_distribution.pdf) ![image](figures/ncalibrators_distribution.pdf)

|      |             |               |                |
|:----:|:-----------:|:-------------:|:--------------:|
| Band |  Frequency  | Nº data cubes | Nº calibrators |
|      |   \[GHz\]   |               |                |
|  3   | $84 - 116$  |      485      |      237       |
|  4   | $125 - 163$ |      155      |       75       |
|  5   |  $163-211$  |      64       |       31       |
|  6   | $211 - 275$ |      579      |      201       |
|  7   |  $275-373$  |      53       |       19       |
|  8   |  $385-500$  |      131      |       57       |
|  9   | $602 - 720$ |      41       |       15       |

: Number of data cubes and calibrators in the pruned sample

## Building cubes

Data cubes have three dimensions, two of which contain spatial information and one spectral information given by a frequency range. To produce each data cube, we followed a sequence of steps to combine multiple observations. First, we concatenated all the uv observations into a single file to obtain a data cube. We selected the ms files with sequential frequencies to be included in the cube. Then we applied the `CASA` task `statwt` to the concatenated file to recalibrate the uv weighting of different observations based on the variance of data. We estimated the beam size using the `CASA` task `getsynthesizedbeam` from the `analysisUtils` package. We sampled each beam with 3 pixels (using a pixel scale = synthesised beam / 3) and picked the image size to be $\sim1.8$ times that of the primary beam, selecting the number of pixels recommended by `CASA` to maximise the imaging efficiency. We defined the channel width for all cubes to be 31.2 MHz, a value selected to strike a balance between spectral resolution, S/N, and manageable data volume. Finally, we ran `tclean` in `CASA` for imaging using linear interpolation, natural weighting to optimise sensitivity, and 0.5 arcsec tapering. We parallelised `CASA` using eight cores and eight threads, which reduces by a factor of 4 the execution time of `tclean` for some cubes. The duration of the imaging process depends on how many observations we combine and the cubes’ frequency coverage, ranging from a few minutes to several hours per cube.

The pruned sample is composed of 1508 cubes from Band 3 to Band 9. Table [1](#tab:n_cubes_cal) details the number of cubes constructed in each band for the pruned sample and the number of calibrators covered. The distribution of the number of cubes is shown in the middle panel of Fig. [3](#fig:subsample_selection). The full sample exhibits three times more cubes than the pruned sample. The number of cubes in the full sample refers to the number of data cubes that can be built applying the integration time criterion only, that is, without taking into account the RMS selection and visual inspection that was used to build the pruned sample (see Sect. [2.2](#sec:clean_sample_selection)).

# ALMACAL$-22$ properties

This section explores the inherent properties of the latest data from the ALMACAL$-22$ survey in both the full and pruned samples. We characterise the fundamental properties of this dataset to provide a clear understanding of the survey’s scope and capabilities. These include the spatial distribution (Sect. [3.1](#sec:spatial_distribution)), spatial resolution (Sect. [3.2](#sec:spatial_resolution)), integration time (Sect. [3.3](#sec:integration_time)), and redshift of the calibrator sources (Sect. [3.4](#sec:redshift)).

## Spatial distribution

The ALMACAL$-22$ survey comprises calibrators randomly distributed across the southern sky, resulting in a widely dispersed area covering more than 1100 arcmin$^2$. The data collection strategy effectively captures diverse regions with a random distribution. This distribution is advantageous for serendipitous line and continuum detections, providing robustness against the effects of cosmic variance, a challenge often encountered in deep field surveys. The top panel of Fig. [1](#fig:spatial_distribution) shows the spatial distribution for the full ALMACAL$-22$ sample and bottom panel the pruned sample. In the pruned sample, two areas have relatively sparse data. These regions are near the projection of the galactic plane, likely resulting in fewer observations due to potential interference and the relative paucity of cosmological deep fields in those regions, or challenges associated with observing in those directions. The primary factor influencing the selection of the pruned sample is the minimum integration time, which determines how long observations need to be made to qualify for inclusion in the dataset.

## Spatial resolution

The spatial resolution of the ALMACAL$-22$ dataset varies depending on the observing frequency and array configuration chosen by PIs based on their scientific goals. Higher-frequency bands generally offer a finer spatial resolution, enabling the detection of more intricate structures and providing valuable insights into the morphology of the observed sources. Conversely, lower-frequency bands offer advantages regarding sensitivity and wider coverage but with a potential sacrifice of some spatial resolution.

Figure [4](#fig:spatial_resolution) shows how each band’s spatial resolution is distributed. In the ALMACAL$-22$ full sample, the median value in Band 3 is 1.14 arcsec. This consistently decreases for higher-frequency bands, reaching a median spatial resolution of 0.13 arcsec in Band 10. In the case of the pruned sample, Band 4 shows the maximum value in the median spatial resolution of 0.87 arcsec. This value is lower in Band 3, then decreases to a mean value of 0.23 arcsec in Band 9.

![image](figures/spatial-resolution/spatial_resolution_B3.pdf) ![image](figures/spatial-resolution/spatial_resolution_B4.pdf) ![image](figures/spatial-resolution/spatial_resolution_B5.pdf) ![image](figures/spatial-resolution/spatial_resolution_B6.pdf) ![image](figures/spatial-resolution/spatial_resolution_B7.pdf) ![image](figures/spatial-resolution/spatial_resolution_B8.pdf) ![image](figures/spatial-resolution/spatial_resolution_B9.pdf) ![image](figures/spatial-resolution/spatial_resolution_B10.pdf)

## Integration time

The integration time reflects the total on-source observation time obtained for the ALMA calibration data. The dataset’s construction requires combining two or more observations if their frequencies overlap by at least 1 GHz. We added up the integration time in a 1 GHz moving window, selecting all the files spanning the same frequency. We imposed a lower limit of 10 minutes for the pruned sample across the whole frequency coverage. Variations in integration time in the cubes arise from the concatenation of short calibration pointings, each lasting several minutes with overlapping spectral coverage. From the varying depths reached, different sensitivity values can be achieved within a cube, but every frequency meets the minimum time criterion. The cube’s frequency range within a cube is chosen to contain sequential frequencies. A calibration field observed several times in the same frequency band may have different frequency ranges observed, creating more than one cube for the same field and band, covering a distinctive frequency extent.

Figure [5](#fig:int_time) shows the distribution of total integration times for the full ALMACAL$-22$ dataset and the pruned sample. The median and maximum values of the total integration times for the full ALMACAL$-22$ dataset and the pruned sample are shown in Table [\[tab:int_time\]](#tab:int_time). The full sample comprises cubes that achieve more than 10 hours of integration time, while the pruned sample reaches an integration time of up to 7 hours. The median value in the full sample is 0.78 hours; in the pruned sample, it is 0.48 hours. The pruning process has only a slight impact on the median value, suggesting a small effect on the sensitivity. The mean sensitivity value reached in the pruned sample is $\sim0.78$ mJy/beam (for further discussion see Sect. [4.1](#sec:area_sensitivity)).

![](figures/Integration_time_full.png)

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  |  |  |  |
|  |  | Full sample |  |  |  | Pruned sample |  |  |
|  |  |  |  |  |  |  |  |  |
| Band | Median $t_{\text{int}}$ | Max $t_{\text{int}}$ | Median Res. | Area | Mean $t_{\text{int}}$ | Max $t_{\text{int}}$ | Median Res. | Area |
|  | \[min\] | \[h\] | \[arsec\] | \[arcmin$^2$\] | \[min\] | \[h\] | \[arcsec\] | \[arcmin$^2$\] |
| 3 | 19.7 | 21.2 | 1.15 | 1301.7 | 19.0 | 6.1 | 0.59 | 693.1 |
| 4 | 19.4 | 5.9 | 0.75 | 209.2 | 14.8 | 2.7 | 0.87 | 250.8 |
| 5 | 28.1 | 2.3 | 0.49 | 54.7 | 13.5 | 1.0 | 0.48 | 63.1 |
| 6 | 23.0 | 35.3 | 0.38 | 231.2 | 19.4 | 6.9 | 0.39 | 103.6 |
| 7 | 22.2 | 18.3 | 0.28 | 71.2 | 14.6 | 2.0 | 0.29 | 16.2 |
| 8 | 21.8 | 5.8 | 0.25 | 15.0 | 19.2 | 5.2 | 0.34 | 26.1 |
| 9 | 23.4 | 6.4 | 0.15 | 3.9 | 20.2 | 0.78 | 0.23 | 3.2 |
| 10 | 23.8 | 0.5 | 0.10 | 0.34 | ... | ... | ... | ... |

Table notes: Columns: (1) ALMA band, (2) and (6) median integration time in the cubes of the full sample and the pruned sample, (3) and (7) maximum integration time reached in the cubes of the full sample and the pruned sample, (4) and (8) median spatial resolution of the full sample and the pruned sample, (5) and (9) total covered area by all the cubes in the full sample and the pruned sample.

## Redshift

![](figures/redshift_distribution.pdf)

The ALMACAL Redshift Catalogue relies primarily on a redshift database introduced by (cite: bonatoALMACALIVCatalogue2018a) for a substantial portion of the calibrator sample. This compilation was further enriched after cross-matching radio sources with optical sources from NED, SIMBAD (cite: wengerSIMBADAstronomicalDatabase2000), and an optical catalogue of bright sources at gigahertz frequencies (cite: mahonyOpticalPropertiesHighfrequency2011). Team members individually checked each source, noting the redshift and provenance. This catalogue is also supplemented by VLT/X-Shooter observations of calibrator sources (ID 111.253L.001, PI: S. Weng and ID 0101.A-0528, PI: E. Mahony). Out of the initial 1047 sources, 675 have robust redshifts and spectra. For the pruned sample of this work, 390/635 ($61\%$) calibrators have confirmed spectroscopic redshifts. Further details will be presented in a forthcoming paper (Weng et al., in prep.).

The redshift distribution for calibrator sources in the full ALMACAL$-22$ dataset and the pruned sample is shown in Fig. [6](#fig:redshift_distribution). The full sample of calibrators has a median redshift of $z = 0.749$, with a maximum of $z=3.788$. In the pruned sample, the median redshift value is $z=0.797$, and the maximum is $z=3.591$. The sources excluded during pruning were likely more concentrated at lower redshifts. However, the redshift distribution in Fig. [6](#fig:redshift_distribution) shows that the higher redshift end is also less populated after pruning. Therefore, we do not expect any significant bias related to redshift in the pruned sample.

# Discussion

This section delves into a comparative analysis of ALMACAL$-22$ and other surveys, emphasising key properties such as sensitivity and survey area. We provide an overview of the scientific goals the ALMACAL survey has achieved so far. We evaluate the unique characteristics of this extensive dataset compared to existing surveys, shedding light on its strengths and potential scientific contributions.

## Survey area and sensitivity

We compared the sensitivity and total area covered by the ALMACAL$-22$ survey to those of previous large programs. Due to the primary beam response, the sensitivity in each cube decreases as we move away from the phase centre. We considered an area 1.8 times the primary beam size for each field, which we calculated using the `primaryBeamArcsec` function from the `analysisUtils` package in `CASA`. To estimate the sensitivity reached in each data cube, we used the `sensitivity` task from `analysisUtils`, which takes the integration time and central frequency as inputs.

ALMACAL$-22$’s coverage is distinguished by its larger footprint than any previous survey, covering over one thousand square arcminutes. For comparison, the ALMA Spectroscopic Survey in the Hubble Ultra Deep Field (HUDF), ASPECS, (cite: decarliALMASPECTROSCOPICSURVEY2016; walterALMASpectroscopicSurvey2016; aravenaALMASpectroscopicSurvey2019; boogaardALMASpectroscopicSurvey2020), covers 4.6 arcmin$^2$ area. The COLDz survey (cite: pavesiCOLuminosityDensity2018; riechersCOLDzShapeCO2019; riechersCOLDzHighSpace2020) covers a $\sim 60$ arcmin$^2$ area. The $6\times15$m IRAM Plateau de Bure High-z Blue-Sequence Survey 2 (PHIBSS2) covers a total area of $\sim130$ arcmin$^2$ (cite: tacconiPHIBSSUnifiedScaling2018; lenkicPlateauBureHighz2020).

Regarding sensitivity, ALMACAL$-22$ data cubes achieve remarkable sensitivity levels in ALMA bands 3, 4, 5, 8, and 9, comparable to ASPECS and COLDz. Bands 6 and 9 offer a wider range of sensitivities, mainly due to the variety of total integration times obtained in each cube after combining data with overlapping frequencies. Additionally, (cite: audibertCOALMARadioSource2022) demonstrated that ALMA calibrator data can be used to estimate the molecular gas content of galaxies, reaching sensitivities around $0.482$ mJy, comparable to surveys such as COLDz and GOODS-ALMA.

Figure [7](#fig:area_sensitivity) compares the total survey area reached by each band in the pruned ALMACAL$-22$ sample as a function of the sensitivity. For comparison, we also plotted the sky coverage and sensitivity values reached by other surveys (cite: lenkicCOExcitationHighz2023; riechersCOLDzShapeCO2019; decarliALMASpectroscopicSurvey2019; gomez-guijarroGOODSALMASourceCatalog2022; stachALMASurveySCUBA22019). Our pruned sample adds up to a total area of 1154 arcmin$^2$, shown as the light green dashed horizontal line, surpassing the total area covered by previous surveys. As the dark dashed horizontal line shows, the full sample area over all bands reaches 1887 arcmin$^2$. The total survey area for both the full and the pruned sample accounts for each calibration field once, prioritising the largest area. Overall, ALMACAL$-22$’s combination of extensive area coverage and average sensitivity will complement findings from other large surveys, addressing the effect of cosmic variance.

Despite these strengths, there are challenges to scientific interpretation. For example, since ALMACAL consists of pointed observations of specific sources, it cannot be considered a truly blind survey, raising concerns about potential biases in cosmic overdensities. However, (cite: bonatoALMACALIVCatalogue2018a) classified most calibrators as blazars ($\sim90\%$). This property mitigates clustering significance since the jets’ brightness is due to their orientation effects toward the observer rather than their mass. For instance, (cite: sushchProbingClusterEnvironments2015) found that clustering effects of a significant number of galaxies (more than five) situated near the line of sight of the blazar beam are absent in the local universe, but they may be possible at higher redshifts ($z > 2$). Moreover, the lack of correlation in redshifts between continuum- or line-detected galaxies and the calibrators further undermines the impact of having the calibrator source at the centre of each pointing (cite: hamanowiczALMACALVIIIPilot2022). Additionally, (cite: chenALMACALXIOverdensities2023) explored an overdense region in ALMACAL similar to extreme proto-cluster cores and found the most likely explanation to be alignment effects. Furthermore, the smaller primary beams in higher ALMA bands probe smaller volumes at lower redshifts.

![](figures/area_sensitivity.pdf)

## Science projects

The ALMACAL survey covers many scientific studies, focusing on four main areas: (1) molecular gas evolution, (2) properties of DSFGs, (3) extragalactic absorption lines, and (4) AGN physics. We briefly summarise what has been done in these areas and the impact that ALMACAL will have through further analysis of this dataset.

\(1\) The evolution of molecular gas has been investigated with ALMACAL through the redshifted CO emission line. ALMA observations cover the frequency range of CO lines at different redshifts. (cite: klitschALMACALAbsorptionselectedGalaxies2019) searched for the CO line in absorption in gas-rich galaxies selected via quasar absorption lines. They found multiple CO transitions, revealing that galaxies were associated with optically identified AGN activity. They reported different factors when using the CO spectral energy distributions (CO SLEDs) as a proxy to estimate the amount of molecular gas compared to the widely used galactic values. These findings indicate the galactic values might overestimate the molecular gas masses for some absorption-selected galaxies. This difference highlights the need to construct CO SLEDs in different systems rather than assuming the values measured for typical SFGs. More recently, (cite: hamanowiczALMACALVIIIPilot2022) developed an ALMACAL-CO pilot program to detect CO emission lines blindly over 38 calibrator fields, selected to have the longest integration times ($> 40$ minutes). This pilot program aimed to probe the feasibility of using ALMA calibrator fields to look blindly for CO emitters. Eleven emission lines were detected, providing a consistent estimation of the evolution of molecular gas compared with previous surveys. ALMACAL’s untargeted approach offers the advantage of being less sensitive to cosmic variance than previous deep surveys.

\(2\) Dusty star-forming galaxies represent more normal SFGs than conventional sub-mm galaxies; such faint systems are usually buried in the confusing noise of sub-mm wavelengths. Early on, (cite: oteoALMACALExploitingALMA2016; oteoALMACALIIExtreme2017a) exploited the high sensitivity levels achieved by ALMACAL by combining data from multiple visits to 69 ALMA calibrator fields in Bands 6 and 7. They found eight DSFGs and derived the number counts. They discovered systems so faint that even the deepest Herschel surveys would not have detected them. (cite: klitschALMACALVIIFirst2020) reported the first number counts in ALMA Band 8 over 81 calibrator fields, finding 21 DSFGs. Recently, (cite: chenALMACALIXMultiband2022) extended the number counts estimation using 1001 calibration fields in the ALMA Bands 3, 4, 5, 6, and 7, covering a wavelength range from 3mm to 870 $\mu$m. They report the detection of 186 DSFGs with flux densities comparable to existing large ALMA surveys, but less prone to cosmic variance. Establishing the space density and contribution of DSFGs to the cosmic far-infrared can be a powerful way to validate galaxy formation and evolution models.

\(3\) The ALMACAL data provide the opportunity to study absorption lines due to galaxies along the line of sight of the calibrators. (cite: klitschALMACALVIMolecular2019) reported several galactic absorption lines using 749 calibrators, but no intervening extragalactic molecular absorber was detected. They also used the cosmological hydrodynamical simulation IllustrisTNG (cite: naimanFirstResultsIllustrisTNG2018; pillepichFirstResultsIllustrisTNG2018; springelFirstResultsIllustrisTNG2018; marinacciFirstResultsIllustrisTNG2018) to obtain new upper bounds on the molecular gas mass density. Their results are consistent with an increasing depletion of molecular gas in the present Universe compared to redshift $z\sim 2$. In a subsequent study, (cite: klitschALMACALConstraintsMolecular2023) presented the first constraints on the molecular gas coverage fraction in the circumgalactic medium of low-redshift galaxies using estimates of CO column densities along the line of sight of quasars with intervening galaxies.

\(4\) As ALMACAL observations are repeated over the years, they allow for multi-year follow-up of the AGN variability. (cite: bonatoALMACALIVCatalogue2018a) examined 754 calibrator data using Bands 3 and 6 in the time domain space, identifying most of them as blazars based on their flat spectrum and low-frequency spectral index. They constructed the light curve of the blazars and found that the median variability index increases steadily with increasing source-to-time lag from 100 to 800 d. (cite: husemannJetdrivenGalaxyscaleGas2019) then studied the morphology and kinematics of the gas surrounding the calibrators. They detected a CO($1-0$) emission arc structure around the AGN of the quasar 3C 273. This arc morphology of the molecular gas is completely different from that of the ionised gas. This raises the question of whether the molecular gas is bound to a stellar overdensity formed from a recent galaxy interaction or is currently forming in situ due to a density wave and increased ambient pressure caused by the expanding outflow, as predicted in simulations for luminous AGNs (cite: mukherjeeRelativisticJetFeedback2018).

(cite: komugiDetectionExtendedMillimeter2022) detected extended mm emission associated with the host galaxy of a prototypical radio-loud quasar to investigate the QSO-host interstellar medium (ISM) interaction.

The new ALMACAL$-22$ dataset, comprising 1047 calibrator fields, promises significant advancements in our current understanding of these science cases. First, the increased calibrator fields will alleviate the field-to-field variance when determining molecular gas evolution. The volume probed by each CO transition will increase by a factor of $\sim10$ compared to previous surveys, reducing the uncertainties and expanding at different redshift bins. Figure [8](#fig:science_cases) shows an example of a blind search across the calibrator fields, where a prominent emission line was detected. Second, by adding 46 calibrator fields to the last search for DSFGs (cite: chenALMACALIXMultiband2022) and new observations of the same fields, it will be possible to achieve deeper sensitivity levels, which could improve the estimates of the number counts by detecting the faintest systems in the Universe. Thirdly, there are over 300 calibrator fields where the CO absorption lines have yet to be searched for. This updated version of the ALMACAL survey provides a significantly larger dataset than the data analysed in (cite: klitschALMACALAbsorptionselectedGalaxies2019). Finally, ALMACAL$-22$ will allow us to study the variability of specific AGN types such as blazars, including both BL Lacs in the nearby Universe and FSRQs at larger distances. Calibrators are usually chosen to be point-like, but some have shown extended large-scale jet structures. Figure [9](#fig:jets) illustrates the same calibration field showing extended structures in ALMA Bands 3, 4, and 6. Studying the effect of these powerful jets on star formation could help us to understand the high-energy processes better.

![image](figures/spectra-J0750-nid5.png) ![image](figures/map-J0750-nid5.png) ![image](figures/spectra-J0750-nid52.png)

![image](figures/map-J1225-b3.png) ![image](figures/map-J1225-b4.png) ![image](figures/map-J1225-b6.png)

# Conclusion

ALMACAL$-22$ is a large survey of ALMA calibrator observations, collecting over 30 TB of data and covering 1047 calibrator fields across the southern sky. We have presented all the calibrator data from science projects taken until May 2022, accumulating over 1000 square arcmin and more than 2000 hours of observing time. Here, we provide the characteristics of the survey.

We have presented the selection of a pruned sample, a subset of the highest-quality data. We outline the data processing details from Band 3 to Band 9 to obtain data cubes as final products. The pruned sample contains 401 calibrator fields and 1508 data cubes. We provide an overall review of the main properties of both the full and pruned samples, including the spatial distribution, spatial resolution, integration time, and redshift of the calibrator sources.

In a forthcoming paper, we will revisit the pruned sample to investigate serendipitous detections of the CO emission lines in the calibrator fields. In this way, this survey will provide clues to the evolution of molecular gas in the Universe through an untargeted approach. As ALMACAL$-22$ is one of the largest surveys to date, it will allow us to make statistical estimates that are less sensitive to potential cosmic variance effects.

Overall, ALMACAL is an ever-growing project, as every scientific project requires calibrator data, and the size of the dataset will continue to grow over the years. A diverse range of catalogues will be established, including the redshift catalogue, extended jets catalogue, and confirmed molecular line catalogue, showcasing the valuable insights ALMACAL$-22$ will contribute to the scientific community.

# Acknowledgements

This research was supported by the International Space Science Institute (ISSI) in Bern, through ISSI International Team project #564 (The Cosmic Baryon Cycle from Space).

# Data Availability

The ALMA Calibrator Source Catalogue is available [here](https://almascience.eso.org/alma-data/calibrator-catalogue). ALMACAL raw data and processed data cubes are available upon reasonable request. Please contact [almacal@eso.org](almacal@eso.org).

57 natexlab

(ref: aravenaALMASpectroscopicSurvey2019) Aravena, M., Decarli, R., Gónzalez-López, J., et al. 2019, The Astrophysical Journal, 882, 136

(ref: aravenaALMAReionizationEra2023) Aravena, M., Heintz, K. E., Dessauges-Zavadsky, M., et al. 2023, The ALMA Reionization Era Bright Emission Line Survey (REBELS): The Molecular Gas Content of Galaxies at Z\~7

(ref: audibertCOALMARadioSource2022) Audibert, A., Dasyra, K. M., Papachristou, M., et al. 2022, A&A, 668, A67

(ref: bonatoALMACALIVCatalogue2018a) Bonato, M., Liuzzo, E., Giannetti, A., et al. 2018, Monthly Notices of the Royal Astronomical Society, 478, 1512

(ref: boogaardNOEMAMolecularLine2023) Boogaard, L. A., Decarli, R., Walter, F., et al. 2023, A NOEMA Molecular Line Scan of the Hubble Deep Field North: Improved Constraints on the CO Luminosity Functions and Cosmic Density of Molecular Gas

(ref: boogaardALMASpectroscopicSurvey2020) Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020, ApJ, 902, 109

(ref: bouwensReionizationEraBright2022) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, The Astrophysical Journal, 931, 160

(ref: carilliCoolGasHighRedshift2013) Carilli, C. L. & Walter, F. 2013, Annual Review of Astronomy and Astrophysics, 51, 105

(ref: chenALMACALXIOverdensities2023) Chen, J., Ivison, R. J., Zwaan, M. A., et al. 2023, Astronomy and Astrophysics, 675, L10

(ref: chenALMACALIXMultiband2022) Chen, J., Ivison, R. J., Zwaan, M. A., et al. 2022, ALMACAL IX: Multi-Band ALMA Survey for Dusty Star-Forming Galaxies and the Resolved Fractions of the Cosmic Infrared Background

(ref: decarliALMASpectroscopicSurvey2020) Decarli, R., Aravena, M., Boogaard, L., et al. 2020, ApJ, 902, 110

(ref: decarliALMASPECTROSCOPICSURVEY2016) Decarli, R., Walter, F., Aravena, M., et al. 2016, ApJ, 833, 69

(ref: decarliALMASpectroscopicSurvey2019) Decarli, R., Walter, F., Gónzalez-López, J., et al. 2019, ApJ, 882, 138

(ref: driverQuantifyingCosmicVariance2010) Driver, S. P. & Robotham, A. S. G. 2010, Monthly Notices of the Royal Astronomical Society, 407, 2131

(ref: gkogkouCONCERTOSimulatingCO2022) Gkogkou, A., Béthermin, M., Lagache, G., et al. 2022, CONCERTO: Simulating the CO, \[CII\], and \[CI\] Line Emission of Galaxies in a 117 \$\\rm Deg\^2\$ Field and the Impact of Field-to-Field Variance

(ref: gomez-guijarroGOODSALMASourceCatalog2022) Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022, A&A, 658, A43

(ref: guilloteauIRAMInterferometerPlateau1992) Guilloteau, S., Delannoy, J., Downes, D., et al. 1992, Astronomy and Astrophysics, 262, 624

(ref: hamanowiczALMACALVIIIPilot2022) Hamanowicz, A., Zwaan, M. A., Péroux, C., et al. 2022, ALMACAL VIII: A Pilot Survey for Untargeted Extragalactic CO Emission Lines in Deep ALMA Calibration Data

(ref: hunterALMAInterferometricPipeline2023) Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023, PASP, 135, 074501

(ref: husemannJetdrivenGalaxyscaleGas2019) Husemann, B., Bennert, V. N., Jahnke, K., et al. 2019, ApJ, 879, 75

(ref: keenanBiasesCosmicVariance2020) Keenan, R. P., Marrone, D. P., & Keating, G. K. 2020, ApJ, 904, 127

(ref: klitschALMACALConstraintsMolecular2023) Klitsch, A., Davis, T. A., Hamanowicz, A., et al. 2023, ALMACAL X: Constraints on Molecular Gas in the Low-Redshift Circumgalactic Medium

(ref: klitschALMACALVIMolecular2019) Klitsch, A., Péroux, C., Zwaan, M. A., et al. 2019a, Monthly Notices of the Royal Astronomical Society, 490, 1220

(ref: klitschALMACALAbsorptionselectedGalaxies2019) Klitsch, A., Zwaan, M. A., Péroux, C., et al. 2019b, Monthly Notices of the Royal Astronomical Society, 482, L65

(ref: klitschALMACALVIIFirst2020) Klitsch, A., Zwaan, M. A., Smail, I., et al. 2020, Monthly Notices of the Royal Astronomical Society, 495, 2332

(ref: komugiDetectionExtendedMillimeter2022) Komugi, S., Toba, Y., Matsuoka, Y., Saito, T., & Yamashita, T. 2022, ApJ, 930, 3

(ref: lefevreALPINEALMACIISurvey2020) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, Astronomy and Astrophysics, 643, A1

(ref: lenkicCOExcitationHighz2023) Lenkić, L., Bolatto, A. D., Fisher, D. B., et al. 2023, CO Excitation in High-z Main Sequence Analogues: Resolved CO(4-3)/CO(3-2) Line Ratios in DYNAMO Galaxies

(ref: lenkicPlateauBureHighz2020) Lenkić, L., Bolatto, A. D., Förster Schreiber, N. M., et al. 2020, The Astronomical Journal, 159, 190

(ref: leroyPHANGSALMAArcsecondCO2021) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43

(ref: mahonyOpticalPropertiesHighfrequency2011) Mahony, E. K., Sadler, E. M., Croom, S. M., et al. 2011, Monthly Notices of the Royal Astronomical Society, 417, 2651

(ref: marinacciFirstResultsIllustrisTNG2018) Marinacci, F., Vogelsberger, M., Pakmor, R., et al. 2018, Monthly Notices of the Royal Astronomical Society, 480, 5113

(ref: mcmullinCASAArchitectureApplications2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, 376, 127

(ref: mukherjeeRelativisticJetFeedback2018) Mukherjee, D., Bicknell, G. V., Wagner, A. Y., Sutherland, R. S., & Silk, J. 2018, Monthly Notices of the Royal Astronomical Society, 479, 5544

(ref: naimanFirstResultsIllustrisTNG2018) Naiman, J. P., Pillepich, A., Springel, V., et al. 2018, Monthly Notices of the Royal Astronomical Society, 477, 1206

(ref: oteoALMACALExploitingALMA2016) Oteo, I., Zwaan, M., Ivison, R., Smail, I., & Biggs, A. 2016, The Messenger, 164, 41

(ref: oteoALMACALIIExtreme2017a) Oteo, I., Zwaan, M. A., Ivison, R. J., Smail, I., & Biggs, A. D. 2017, The Astrophysical Journal, 837, 182

(ref: padovaniTwoMainClasses2017) Padovani, P. 2017, Nature Astronomy, 1, 0194

(ref: pavesiCOLuminosityDensity2018) Pavesi, R., Sharon, C. E., Riechers, D. A., et al. 2018, ApJ, 864, 49

(ref: perouxCosmicBaryonMetal2020) Péroux, C. & Howk, J. C. 2020, Annual Review of Astronomy and Astrophysics, 58, 363

(ref: pillepichFirstResultsIllustrisTNG2018) Pillepich, A., Nelson, D., Hernquist, L., et al. 2018, Monthly Notices of the Royal Astronomical Society, 475, 648

(ref: poppingALMASpectroscopicSurvey2019) Popping, G., Pillepich, A., Somerville, R. S., et al. 2019, The Astrophysical Journal, 882, 137

(ref: poppingALMASpectroscopicSurvey2020) Popping, G., Walter, F., Behroozi, P., et al. 2020, ApJ, 891, 135

(ref: riechersCOLDzHighSpace2020) Riechers, D. A., Hodge, J. A., Pavesi, R., et al. 2020, ApJ, 895, 81

(ref: riechersCOLDzShapeCO2019) Riechers, D. A., Pavesi, R., Sharon, C. E., et al. 2019, ApJ, 872, 7

(ref: solimanoALMACRISTALSurveyDiscovery2024) Solimano, M., González-López, J., Aravena, M., et al. 2024, The ALMA-CRISTAL Survey. Discovery of a 15 Kpc-Long Gas Plume in a \$z=4.54\$ Lyman-\$\\alpha\$ Blob

(ref: springelFirstResultsIllustrisTNG2018) Springel, V., Pakmor, R., Pillepich, A., et al. 2018, Monthly Notices of the Royal Astronomical Society, 475, 676

(ref: stachALMASurveySCUBA22019) Stach, S. M., Dudzevičiūtė, U., Smail, I., et al. 2019, Monthly Notices of the Royal Astronomical Society, 487, 4648

(ref: sushchProbingClusterEnvironments2015) Sushch, I. & Böttcher, M. 2015, A&A, 573, A47

(ref: tacconiHighMolecularGas2010) Tacconi, L. J., Genzel, R., Neri, R., et al. 2010, Nature, 463, 781

(ref: tacconiPHIBSSUnifiedScaling2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: tacconiEvolutionStarFormingInterstellar2020) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, Annual Review of Astronomy and Astrophysics, vol. 58, p.157-203, 58, 157

(ref: urryUnifiedSchemesRadioLoud1995) Urry, C. M. & Padovani, P. 1995, Publications of the Astronomical Society of the Pacific, 107, 803

(ref: walterEvolutionBaryonsAssociated2020) Walter, F., Carilli, C., Neeleman, M., et al. 2020, ApJ, 902, 111

(ref: walterALMASpectroscopicSurvey2016) Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67

(ref: wengerSIMBADAstronomicalDatabase2000) Wenger, M., Ochsenbein, F., Egret, D., et al. 2000, Astron. Astrophys. Suppl. Ser., 143, 9

(ref: zwaanALMACALSurveyingUniverse2022) Zwaan, M., Ivison, R., Peroux, C., et al. 2022, ALMACAL: Surveying the Universe with ALMA Calibrator Observations, https://doi.eso.org/10.18727/0722-6691/5256

</paper>

Write the methods card for this paper.