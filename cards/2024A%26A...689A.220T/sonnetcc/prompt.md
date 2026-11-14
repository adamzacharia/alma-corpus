# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...689A.220T\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...689A.220T",
 "title": "HYPERION: Coevolution of supermassive black holes and galaxies at z &gt; 6 and the build-up of massive galaxies",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Tripodi, R.",
 "n_authors": 25,
 "arxiv_id": "2401.04211",
 "doi": "10.1051/0004-6361/202349054",
 "alma_projects_linked_by_archive": [
  "2015.1.00399.S",
  "2016.1.01063.S",
  "2017.1.01088.S",
  "2017.1.01195.S",
  "2017.1.01472.S",
  "2018.1.01188.S",
  "2018.1.01289.S",
  "2018.1.01790.S",
  "2019.1.00672.S",
  "2019.1.01633.S",
  "2021.1.00934.S",
  "2021.2.00064.S",
  "2021.2.00151.S"
 ]
}
```

Paper text:
<paper>
# HYPERION. Coevolution of supermassive black holes and galaxies at $z>6$ and the build-up of massive galaxies

# Introduction

In the past few decades, many advances have been made in unveiling the properties of the host galaxies of the first quasi-stellar-objects (QSOs) from theory and observations. The Atacama Large Millimeter/sub-millimeter Array (ALMA), along with the Northern Extended Millimeter Array (NOEMA), the Very Large Array (VLA), and *Herschel*, have probed the cold gas and dust of the QSO host galaxies. The dust continuum was detected in many $z \sim 6$ QSOs with estimated far-infrared (FIR) luminosities of $L_{\rm FIR}=10^{11-13}\ \rm L_{\odot}$ and dust masses of about $M_{\rm dust}= 10^{7-9}\ \rm M_{\odot}$ (cite: decarli2018; carniani2019; shao2019).

The rest-frame FIR continuum emission originates from dust heated by the ultraviolet (UV) radiation from young and massive stars (cite: decarli2018; venemans2020; neeleman2021) and the active galactic nucleus (AGN) radiation (cite: schneider2015; dimascia2021; walter2022). The latter contribution is usually neglected when modeling the FIR spectral energy distribution (SED) of $z\sim 6$ QSOs, although the AGN heating can contribute $30-70$% of the FIR luminosity (cite: schneider2015; duras2017). Moreover, dust masses are often determined with huge uncertainties and only rely on single-frequency continuum detections. However, if multifrequency ALMA and/or NOEMA observations are available in the rest-frame FIR, which probe both the peak and the Rayleigh Jeans tail of the dust SED, the dust temperature and mass can be constrained with statistical uncertainties $<10-20\%$ (e.g., (cite: carniani2019; Tripodi2022; tripodi2023a; witstok2023)). This results in a high accuracy in the determination of the star formation rate (SFR).

Accurate estimates of the dust masses would also allow us to derive the molecular gas mass of the host galaxy through the gas-to-dust ratio (GDR). Although it is possible to directly probe the molecular reservoirs of the QSO host galaxies using the rotational transitions of the CO (e.g., (cite: vallini2018; madden2020)), very few high-$z$ QSOs are observed in CO because this emission line is typically faint at high $z$. The GDR has indeed often been assumed in order to compute the gas mass, resulting in a high degree of uncertainty in its estimate. Studies of $z\sim 2.4-4.7$ hyperluminous QSOs showed that the GDR spans a broad range of values, 100-300, with an average GDR $\sim 180$ (cite: bischetti2021). This is consistent with the results found for submillimeter (submm) galaxies to $z\sim3-5$ with a GDR$\sim150-250$ (e.g., (cite: saintonge2013; miettinen2017)). Recent studies suggested that the GDR for SMGs may be lower than 100 (cite: birkin2021; liao2023). In low-z galaxies, a GDR$\sim 100$ is typically observed (cite: draine2007; leroy2011), implying that the GDR increases with redshift. However, the combination of gas-mass estimates from CO with the dust mass from finely sampled FIR SEDs results in an accurate determination of the GDR, and this allows us to study its evolution with redshift.

Another central question is to understand the efficiency of large halos in forming stars during the first cosmic billion year. In this context, luminous QSOs are efficient signposts of large halos at high redshift (cite: wang2024), which allows us to investigate the complex physics at play in the building of massive galaxies. The efficiency of a galaxy in forming stars is an intricate mechanism that depends on the efficiency with which cold gas is formed from baryons and on the efficiency with which the cold gas is converted into stars. The former is influenced by the capability of gas cooling and the capability of gas removal or gas heating by feedback. The gas star formation efficiency (SFE) has been investigated for decades in both the local and high-redshift universe. It is parameterized by the Kennicutt-Schmidt (KS) relation (cite: kennicutt1998; genzel2010; speagle2014; calabro2024). Because spatially resolved observations and of robust estimates of the SFR are still lacking, the KS relation is still poorly studied in high-z QSOs. Many questions about the SFE in these objects are therefore still unanswered.

Targeting the QSO host galaxies at these redshifts provides a unique opportunity to characterize the formation and concurrent build-up of SMBHs and their host galaxies, and also the physical properties of the ISM in the first billion year of the Universe (cite: decarli2018; venemans2020; neeleman2021). The local correlation between massive BHs and bulges is indeed tight, suggesting that the same process that assembled galaxy bulges may cause most of the growth of massive BHs. QSOs at $z\gtrsim 6$ appear to lie above the local $M_{\rm BH}-M_*$ correlation, and thus, the BH growth seems to precede that of its host galaxy (cite: ding2023; stone2023; yue2023). However, before the advent of the James Webb Space Telescope (JWST), it was difficult to obtain reliable and accurate estimates of the stellar mass in QSO hosts at high $z$, even with deep HST observations (cite: metchtley2012; marshall2020). Therefore, instead of the stellar mass, the dynamical mass is used at high $z$, exploring the $M_{\rm BH}-M_{\rm dyn}$ relation. For instance, (cite: feruglio2018) and (cite: pensabene2020) studied the $M_{\rm BH}-M_{\rm dyn}$ relation in luminous high-$z$ QSO hosts and reported that this relation evolves with redshift and that high-$z$ QSOs lie above the local relations. This implies that the SMBHs formed significantly faster than their hosts. In this context, (cite: izumi2018; izumi2019) studied the $M_{\rm BH}-M_{\rm dyn}$ using a sample of seven $z> 6$ low-luminosity quasars. They found that while the luminous quasars typically lie above the local relation (cite: kormendy2013) with BHs overmassive compared to local AGNs, the discrepancy becomes less evident for low-luminosity quasars (cite: maiolino2023c). In order to avoid being biased by the properties of higher luminosity sources, it is essential to study the whole population of QSOs and galaxies at high $z$, including the low-luminosity sources. This is now possible with data from JWST (cite: santini2023; harikane2023), which enable us to determine the stellar mass especially in low-luminosity sources based on a sharper PSF (especially in the short-wavelength bands) and longer-wavelength coverage out to 5 micron compared to HST, which is less affected by dust attenuation. Recently, (cite: harikane2023) analyzed a first statistical sample of faint type 1 AGNs at $z>4$ identified by JWST/NIRSpec deep spectroscopy. They compared their AGNs to the AGNs at $z\sim 0$ (cite: reines2015) and to high-$z$ QSOs. Their AGNs have similar BH masses, but systematically lower stellar masses than the local AGNs. Moreover, (cite: maiolino2023c; maiolino2023) showed even more extreme $M_{\rm BH}-M_*$ ratios in their sample of 12 AGNs at $z=4-7$ that belong to the JADES survey. Similar results were also obtained in previous studies with a smaller number of AGNs (cite: ubler2023). This indicates that the BH grows faster than its host galaxy at high redshift. The fast BH growth was also suggested by previous studies at $z\sim 2$ (cite: zhang2023c). These overmassive (compared to their host stellar masses) BHs are indeed predicted in some theoretical models simulations (cite: toyouchi2021; trinca2022; inayoshi2022; hu2022; zhang2023b; pacucci2023; pacucci2024). In summary, recent observations showed that high-$z$ QSOs may lie above the local $M_{\rm BH}$ - $M_{*}$ correlation, and they are thus likely to follow the BH-dominance growth or BH-dominance evolutionary path (cite: volonteri2012).

The significance of our work becomes evident in the context of these prior studies, as we aim to explore the interconnected growth of supermassive black holes and their host galaxies. Additionally, we seek to understand whether the high-redshift hosts of quasars serve as the progenitors of the massive galaxies observed in the local Universe. These two queries are pivotal to the study of galaxy evolution and are tightly interconnected. They can only be addressed through a reliable and precise understanding of the properties of QSOs and their massive hosts.

In this work, we present the analysis of the cold-dust SEDs of four QSOs at $z>6$, PSO J036.5078+03.0498 (cite: venemans2015) at $z=6.5405$, VDESJ022426.54-471129.4 (cite: reed2017) at $z=6.5222$, PSO J231.6576-20.8335 (cite: mazzucchelli2017) at $z=6.587$, and SDSS J205406.49-000514.8 (cite: reed2017) at $z=6.0391$, based on new ALMA band 8 (B8) and/or band 9 (B9) observations, archival ALMA observations from band 3 (B3) to band 6 (B6), and a NOEMA observation at 3 mm. These observations allowed us to retrieve reliable and accurate estimates of the dust parameters and the SFR of the QSO host galaxies in our sample. Furthermore, from the analysis of archival observations, we were also able to detect the CO(7-6) and \[CI\] emission lines for J0224-4711 and the CO(6-5) emission line for J2054-0005, from which we were able to estimate the gas mass for these objects.

In order to investigate the dust properties, SFR, GDR, and gas SFE in a statistically sound sample of QSOs at $z>6$, we considered another six high-$z$ QSOs whose dust properties and SFR were already derived with high accuracy. The sample is presented in the following section.

The paper is organized as follows. In Sect. [2](#sec:sample), we describe our sample of QSOs at $z>6$. In Sect. [3](#sec:obs), we describe the observations used in this work. In Sect. [4](#sec:res), we present the results for the continuum and line emissions. In Sect. [5](#sec:analysis), we analyze the cold-dust SED of the QSOs in our sample, and we derive the gas mass for QSOs J0224-4711, J1319+0950, and J2054-0005. In Sect. [6](#sec:disc), we contextualize our findings regarding the dust and gas in high-$z$ QSO, and we discuss the observed scenario for the evolutionary paths of these objects. In Sect. [7](#sec:sum), we summarize the content of this work.

Throughout the paper, we adopt the $\Lambda$CDM cosmology from (cite: planck2018): $H_0=67.4\ \rm km\ s^{-1}\ Mpc^{-1}$, $\Omega_m = 0.315$, and $\Omega_{\Lambda} = 0.685$. Thus, the angular scale is $5.66$ kpc/arcsec at $z=6.3$.

# Sample

We selected from the currently known $\sim$300 QSOs at $z>6$ (cite: fan2022; jiang2016; mortlock2011; wang2019b; inayoshi2020) all the QSOs at $z>6$ for which we were able to investigate and compare the evolutionary path of the SMBHs and their host galaxies, and we linked it to feedback processes. This implied that we should be able derive or retrieve accurate estimates of the SMBH properties, dust properties, SFR and gas mass, and to detect outflowing emission. In other words, all these QSOs have high-quality rest-frame optical-UV spectra and ALMA and/or NOEMA observations targeting the continuum emission from low to high frequencies (in the range of observed frequency $\sim$ 100-600 GHz), that is, probing both the Rayleigh-Jeans and peak region of the cold-dust SED, and targeting the CO and \[CII\] line emissions (cite: zappacosta2023; dodorico2023; wang2013; neeleman2019; witstok2023; decarli2022). Moreover, we selected QSOs with $L_{\rm bol}>10^{47}\rm erg \ s^{-1}$. Consequently, our findings are not directly applicable to the entire population of AGNs at $z>6$; instead, they specifically pertain to high-luminosity sources. Nevertheless, this luminosity bias aligns with our objectives, as we are particularly interested in investigating the role of AGN feedback in influencing the SMBH-galaxy evolution, and notably, high-luminosity QSOs exhibit compelling evidence of powerful outflows (cite: bischetti2022; shao2022; tripodi2023c; salak2023).

Our final sample consisted of ten QSOs at $z>6$. Together with the four QSOs presented in the previous section (J036+03, J0224-4711, J231-20, and J2054-0005), we considered six other QSOs: SDSS J010013.02+280225.8 (hereafter J0100+2802), SDSS J231038.88+185519.7 (hereafter J2310+1855), J1319+0950, ULAS J134208.10+092838.35 (hereafter J1342+0928), SDSS J114816.64+525150.3 (hereafter J1148+5251), and PSO J183.1124+05.0926 (hereafter J183+05).

| QSO | z | $\log(M_{\rm BH}/M_\odot)$ | $\log(L_{\rm bol}/{\rm erg\ s^{-1}})$ | Refs | Results |
|:---|:--:|:--:|:--:|:--:|:--:|
| J0100+2802 | 6.327 | 10.04 $\pm$ 0.27 | 48.24 $\pm$ 0.04 | \[1\],\[2\] | SED$^{(*)}$ |
| J036+03 | 6.540 | 9.49 $\pm$ 0.12 | 47.33 $\pm$ 0.05 | \[1\],\[2\] | SED, $M_{\rm H_2}$ |
| J0224-4711 | 6.522 | 9.36 $\pm$ 0.08 | 47.53 $\pm$ 0.01 | \[1\] | SED, $M_{\rm H_2}$ |
| J231-20 | 6.587 | 9.50 $\pm$ 0.09 | 47.31 $\pm$ 0.01 | \[1\],\[2\] | SED, $M_{\rm H_2}$ |
| J1342+0928 | 7.540 | 8.90 $\pm$ 0.14 | 47.19 $\pm$ 0.01 | \[1\],\[2\] | SED |
| J1148+5251 | 6.419 | 9.74 $\pm$ 0.03 | 47.57 $\pm$ 0.01 | \[1\] | – |
| J2310+1855 | 6.003 | 9.67$^{+0.06}_{-0.08}$ | 47.49$^{+0.10}_{-0.13}$ | \[3\],\[4\] | SED$^{(**)}$ |
| J2054-0005$^{(***)}$ | 6.390 | 9.17 | 47.03 | \[2\],\[5\] | SED, $M_{\rm H_2}$ |
| J1319+0950 | 6.133 | 9.53$^{+0.05}_{-0.11}$ | 47.30$^{+0.07}_{-0.08}$ | \[3\],\[2\] | $M_{\rm H_2}$ |
| J183+05 | 6.439 | 9.41$^{+0.21}_{-0.41}$ | 47.20$^{+0.16}_{-0.25}$ | \[3\],\[2\] | SED |

**Notes.** Columns: QSO name; redshift from the \[CII\] emission line; BH mass; bolometric luminosity; references for z, $M_{\rm BH}$, and $L_{\rm bol}$; results presented in this work: cold-dust SED along with the dust properties and SFR (SED), gas mass from the CO(6-5) or CO(7-6) emission lines ($M_{\rm H_2}$). $^{(*)}$, $^{(**)}$: results already presented in (cite: tripodi2023b) and in (cite: Tripodi2022), respectively, which are reported in this work. $^{(***)}$ The error on the BH mass for J2054-0005 was not provided in the reference works, and we therefore considered an average systematic error on the BH mass of 0.3 dex. The QSOs above the double black line belong to the HYPERION sample. The errors for the BH masses and bolometric luminosities of the HYPERION QSOs are taken from Tortosa et al. in prep. References: \[1\] (cite: zappacosta2023); \[2\] (cite: neeleman2021); \[3\] (cite: mazzucchelli2023); \[4\] (cite: Tripodi2022); \[5\] (cite: wang2013).

We divided the sample into two subsamples of six and four QSOs each, hereafter called HYPERION QSOs and $z>6$ QSOs, respectively (see Tab. [\[tab:sample\]](#tab:sample)).

The first subsample is composed of the six QSOs belonging to the sample called HYPerluminous QSOs at the Epoch of ReionizatION (HYPERION). HYPERION comprises the titans of $z>6$ QSOs (cite: zappacosta2023), that is, those whose SMBH had the fastest mass growth history. In particular, these QSOs were selected so that the SMBHs powering them required to form at least a 1000 $M_{\odot}$ BH seed (at $z=20$) under the hypothesis of a continuous exponential accretion at the Eddington rate. These SMBHs likely assembled from the largest BH seeds, or alternatively, they experienced peculiar, possibly super-Eddington, mass accretion histories. Of the $\sim 300$ QSOs known at the epoch of reionization (EoR), the HYPERION QSOs comprise 18 QSOs with a mean redshift $z \sim 6.7$, and average $\rm \log(L_{\rm bol}/\rm erg/s) \sim 47.3$, and a BH mass in the range $10^9-10^{10}~\rm M_\odot$. HYPERION is based on a 2.4 Ms XMM-Newton Multi-Year Heritage Programme (PI: Zappacosta) to provide for the first time for such a large sample of $z>6$ QSOs a uniform high quality X-ray spectral characterization for a detailed investigation of the nuclear properties and the accretion and ejection processes that are tied to the fast build-up experienced by their SMBH. The first results suggest a genuine redshift evolution of their X-ray spectral slopes, which appear to be steeper than reported in $z<6$ QSOs with a similar luminosity and accretion rate. This supports a different regime for the X-ray nuclear properties of the first quasars that might be linked to the presence of fast disk-driven winds (cite: zappacosta2023). While the nuclear properties of HYPERION QSOs are well constrained, as are the dynamical masses of most QSOs based on archival \[CII\] observations, their dust properties and SFR are still mostly unconstrained.

The $z>6$ QSO subsample comprises the QSOs that did not satisfy the criteria for belonging to the HYPERION sample (cite: zappacosta2023), that is, they did not experience a rapid SMBH mass growth.

We divided our final sample based on the HYPERION survey selection criteria in order to assess whether the BH accretion history has strong implications for the properties of the host galaxy.

Seven QSOs in our sample[^2] are also part of the XQR-30 ESO Large Program (cite: dodorico2023). Therefore, they have high S/N X-Shooter spectra, from which (cite: mazzucchelli2023) derived BH masses using the C IV and Mg II emission lines. The Mg II BH masses derived for J0100+2802, J036+03, J0224-4711, and J231-20 agree well with those in (cite: zappacosta2023).

The properties of the ten QSOs in our final sample are summarized in Tab. [\[tab:sample\]](#tab:sample), and a more detailed presentation of each object can be found in Appendix [8](#app:a).

# Observations

All ALMA observations targeting QSOs J036+03, J0224-4711, J231-20, J1319+0950, J2054-0005 were calibrated and imaged as outlined in the following.

The visibility calibration of the observations was executed by the ALMA science archive. The imaging was performed through the Common Astronomy Software Applications (CASA; (cite: mcmullin2007)), version 5.1.1-5. We applied `tclean` using natural weighting and a $3\sigma$ cleaning threshold. We imaged the continuum using the multifrequency synthesis (MFS) mode in all line-free channels. To image the line emissions, we used the CASA task `uvcontsub` to fit the continuum visibilities in the line-free channels with a first-order polynomial for QSO J0224-4711, since the continuum showed a non-negligible slope, and zeroth-order polynomial for the other QSOs. We then obtained continuum-subtracted cubes to be used in our analyses. We produced line maps using the MFS mode in the channels enclosing the emission lines (see Tab. [\[tab:c2-table-obs\]](#tab:c2-table-obs)).

We analyzed all archival observations available for J036+03 and J0224-4711. We also used the results on the continuum emission at $\sim 107$ GHz of J036+03, obtained from a NOEMA observation (project ID: S17CD).

Because many ALMA observations are available for J2054-0005, especially in B6, we considered for each band those whose continuum sensitivity and resolution were suited for our analysis of the SED. That is, when multiple observations per band were available, we considered the observation with the highest continuum sensitivity and with a resolution that allowed us to spatially resolve the source and/or that was as close as possible to the angular resolution of the B9 observation, in order to ensure a reliable and consistent analysis of the cold-dust SED (for more details, see Sect. [4.1](#subsec:cont)).

For J231-20, we used the results presented in (cite: Pensabene2021), who analyzed all the ALMA observations from B3 to B6 available for this QSO, and we independently analyzed a new B8 ALMA observation targeting this QSO (ID: 2021.2.00064.S). Since J231-20 was found to have a close companion (at a distance $<10$ kpc), we discuss the analysis of the B8 observation in more detail in Sect. [4.1](#subsec:cont).

Information about the project ID, synthesized beam, lines detected, line channels, and root mean square (r.m.s) noise of the continuum map and of the continuum-subtracted cube for each observation analyzed in this work is reported in Tabs. [\[tab:c3-table-obs\]](#tab:c3-table-obs) and [\[tab:c2-table-obs\]](#tab:c2-table-obs).

# Data analysis

In the following, we report the results for our proprietary observations targeting the continuum (Sect. [4.1](#subsec:cont)) and/or line emissions (Sect. [4.2](#subsec:emlines)) in ALMA bands 3, 8, and/or 9 of QSOs J036+03, J0224-4711, J1319+0950, and J2054-0005. As an exception, we discuss the archival observation targeting the continuum emission in B8 of J231-20 because it was found to have a close companion in lower-frequency observations. Details of the analysis of archival observations of the continuum emissions of QSOs J036+03, J0224-4711, and J2054-0005 can be found in Appendix [9](#app:b). The results obtained from the analysis of archival observations are reported in Tab. [\[tab:c3-table-obs\]](#tab:c3-table-obs).

## Continuum emission

![image](continuum-PSOJ036-B8.png) ![image](continuum-PSOJ036-B9.png) ![image](continuum-VDESJ0224-B8.png) ![image](continuum-VDESJ0224-B9.png)

### QSO J036+03

The top left and right panels of Fig. [1](#fig:c3-contj036) show the continuum emission at 404.9 GHz and 670.9 GHz of J036+03, respectively. Neither emission is spatially resolved, and therefore, we considered the peak flux as the total flux of the source, that is, 6.63 $\pm$ 0.39 mJy/beam at 404.9 GHz and 5.60 $\pm$ 0.69 mJy/beam at 670.9 GHz. The emission at 670.9 GHz presents a secondary peak at RA,DEC=\[-1.5,-1.5\], which likely is an artifact due to the low resolution of the B9 observation. This interpretation is supported by the absence of line and continuum emission at the same spatial position in all lower-frequency observations and by the presence of another dimmer peak that is located symmetrically with respect to the QSO position (RA,DEC=\[1.0,-1.5\]).

### QSO J0224-4711

The continuum emission of J0224-4711 at 405.2 GHz and 670.9 GHz is shown in the bottom left and right panels of Fig. [1](#fig:c3-contj036), respectively. Neither emission is spatially resolved, and therefore, we consider the peak flux as total flux of the source, which is 8.73 $\pm$ 0.38 mJy/beam at 405.2 GHz and 19.9 $\pm$ 0.96 mJy/beam at 670.9 GHz.

### QSO J2054-0005

We show the continuum map at 92.3 GHz underlying the CO(6-5) emission line in the bottom row of Fig. [4](#fig:c2-co65J2054). Performing a 2D Gaussian fit, we found that the peak flux is 0.066$\pm$0.004 mJy/beam, the integrated flux is $0.082 \pm 0.009$ mJy, and the emission is spatially resolved with a size of $(0.27\pm 0.07)\times (0.07\pm 0.09)$ arcsec$^2$.

### QSO J231-20

J231-20 was found to have a close companion that is detected in multiple emission lines and in the continuum emission from $\sim 100$ GHz up to $\sim 250$ GHz at a distance of $\sim 2$ arcsec from the QSO (cite: Pensabene2021; decarli2017; neeleman2019). (cite: Pensabene2021) were able to disentangle the continuum emission of the QSO from that of the companion using $\sim 1$ arcsec resolution ALMA observations. Unfortunately, the low resolution of the new band 8 observation (beam of $4.3\times 2.9$ arcsec$^2$) did not allow us to distinguish the two emissions (see Fig. [18](#fig:app-j231)). Performing a 2D fit with CASA on the continuum map, we found a peak flux of $8.43\pm 0.39$ mJy/beam, and the source was unresolved. The B8 flux is indeed contaminated by the continuum emission of the companion, and this can therefore bias the SED fitting and the determination of the dust properties. We corrected for the companion contribution using the results found by (cite: Pensabene2021). In their SED modeling, the flux of the companion at $\sim 400$ GHz is more than 0.6 dex lower than that of the QSO. Conservatively considering the highest-temperature model for the companion, that is, that the flux of the companion is 0.6 dex lower than that of the QSO, we can correct our flux in band 8. We obtain 6.74$\pm$0.31. We considered this flux as a detection in the SED fitting, but it might also be seen as a lower limit to the flux of the QSO.

## Emission lines

### CO(7-6) and \[CI\] emission lines in J0224-4711

We used the continuum-subtracted data cube in B3 to study the CO(7-6) and \[CI\] emission lines of J0224-4711. The central and right panels of Fig. [2](#fig:c2-co76) present the maps of CO(7-6) and \[CI\], respectively, imaged using the MFS mode in the channels specified in Tab. [\[tab:c2-table-obs\]](#tab:c2-table-obs). The CO(7-6) and \[CI\] emission are detected with a statistical significance of $\sim 8\sigma$ and $\sim 3\sigma$, respectively, and neither is spatially resolved. Performing a 2D Gaussian fit, we obtained a peak flux of 0.36 $\pm$ 0.02 mJy/beam for CO(7-6) and of $0.19 \pm 0.03$ mJy/beam for \[CI\].

Fig. [3](#fig:c2-momj0224) shows the moment -0, -1, and -2 maps of the CO(7-6) emission, obtained by applying a 2.5$\sigma$ threshold to the continuum-subtracted cube in the line channels, and the spectrum extracted from the region with S/N$>2$ in the CO(7-6) map. The moment-0 map shows a velocity gradient oriented east to west with $\Delta v=100$ $\rm km\ s^{-1}$, and the moment-2 map shows a range of the velocity dispersion[^3] between 20 and 120 $\rm km\ s^{-1}$. The CO(7-6) line profile peaks at a frequency of 107.239 GHz, corresponding to $z=6.5220\pm 0.0002$, consistent with previous determinations (cite: reed2017) and with the redshift derived from MgII emission line (cite: dodorico2023). From the fit with a single Gaussian, the FWHM of the line is $307 \pm 25$ $\rm km\ s^{-1}$ and the integrated flux is 0.34 $\pm$ 0.05 Jy km s$^{-1}$, which corresponds to a luminosity of $L_{\rm CO(7-6)}= (1.6 \pm 0.2) \times 10^8 \rm \ L_\odot$ and $L'_{\rm CO(7-6)}= (9.6\pm 1.4)\times 10^9\rm K ~km ~s^{-1} ~pc^2$ (cite: solomon2005). The \[CI\] line is slightly blueshifted, peaking at 107.610 GHz, which corresponds to $z=6.5211 \pm 0.0004$. Performing a single-Gaussian fit, we obtained that the FWHM of the line is $165 \pm 29$ $\rm km\ s^{-1}$ and the integrated flux is 0.108 $\pm$ 0.036 Jy km s$^{-1}$, which corresponds to a luminosity[^4] of $L_{\rm [CI]}= (5.1 \pm 1.7) \times 10^7 \rm \ L_\odot$ and $L'_{\rm [CI]}= (3.0\pm 1.0)\times 10^9\rm K ~km ~s^{-1} ~pc^2$. All line properties are reported in Tab. [\[tab:c2-colines\]](#tab:c2-colines).

### CO(6-5) emission line in J1319+0950

In order to analyze the CO(6-5) emission line of J1319+0950, we rebinned the continuum-subtracted data cube in B3 to 50 km s$^{-1}$ .

![](band3-maps-ord1.png)

![](mom-spec-j0224-co76.png)

The top row of Fig. [4](#fig:c2-co65J2054) presents the map of the CO(6-5) emission line of J1319+0950 and its underlying continuum, imaged using the MFS mode in the channels specified in Tab. [\[tab:c2-table-obs\]](#tab:c2-table-obs). The CO(6-5) is detected with a statistical significance of $\sim 15 \sigma$, and performing a 2D Gaussian fit, we obtained a peak flux of 0.303 $\pm$ 0.014 mJy/beam and an integrated flux of 0.570 $\pm$ 0.038 mJy. The emission is spatially resolved with a size of $(0.35 \pm 0.03)\times (0.23\pm 0.03)$ arcsec$^2$.

The top row of Fig. [5](#fig:c2-momj2054) shows the moment -0, -1, and -2 maps of the CO(6-5) emission of J1319+0950, obtained by applying 3$\sigma$ threshold to the continuum-subtracted cube in the line channels, and the spectrum extracted from the region with S/N$>2$ in the CO(6-5) map. The moment-0 shows a velocity gradient oriented northeast to southwest with $\Delta v=400$ $\rm km\ s^{-1}$, and the moment-2 map shows a range of the velocity dispersion between 20 and 160 $\rm km\ s^{-1}$. The CO(6-5) line profile peaks at a frequency of 96.939 GHz, corresponding to $z=6.1331\pm 0.0004$. Performing a single-Gaussian fit to the line spectral profile, we obtained an FWHM of the line of $529 \pm 41$ $\rm km\ s^{-1}$ and an integrated flux of 0.662 $\pm$ 0.094 Jy km s$^{-1}$, which corresponds to a luminosity of $L_{\rm CO(6-5)}= (2.4 \pm 0.3) \times 10^8 \rm \ L_\odot$ and $L'_{\rm CO(6-5)}= (2.3 \pm 0.3)\times 10^{10}\rm K ~km ~s^{-1} ~pc^2$.

### CO(6-5) emission line in J2054-0005

In order to analyze the CO(6-5) emission line of J2054-0005, we rebinned to 50 km s$^{-1}$ the continuum-subtracted data cube in B3.

The bottom row of Fig. [4](#fig:c2-co65J2054) presents the map of the CO(6-5) emission line of J2054-0005 and its underlying continuum, imaged using the MFS mode in the channels specified in Tab. [\[tab:c2-table-obs\]](#tab:c2-table-obs). The CO(6-5) is detected with a statistical significance of $\sim 10 \sigma$. Performing a 2D Gaussian fit, we obtained a peak flux of 0.349 $\pm$ 0.036 mJy/beam, an integrated flux of 0.496 $\pm$ 0.080 mJy, and the emission is spatially resolved with a size of $(0.30 \pm 0.09)\times (0.08\pm 0.16)$ arcsec$^2$.

The bottom row of Fig. [5](#fig:c2-momj2054) shows the moment-0, -1, and -2 maps of the CO(6-5) emission of J2054-0005, obtained by applying 3$\sigma$ threshold to the continuum-subtracted cube in the line channels, and the spectrum extracted from the region with S/N$>2$ in the CO(6-5) map. The moment-0 shows a velocity gradient oriented southeast to northwest with $\Delta v=120$ $\rm km\ s^{-1}$, and the moment-2 map shows a range of the velocity dispersion between 20 and 80 $\rm km\ s^{-1}$. The CO(6-5) line profile peaks at a frequency of 98.233 GHz, corresponding to $z=6.0391\pm 0.0002$. Performing a single-Gaussian fit to the line spectral profile, we obtained a FWHM of the line of $229 \pm 20$ $\rm km\ s^{-1}$ and an integrated flux of 0.288 $\pm$ 0.047 Jy km s$^{-1}$, which corresponds to a luminosity of $L_{\rm CO(6-5)}= (1.0 \pm 0.2) \times 10^8 \rm \ L_\odot$ and $L'_{\rm CO(6-5)}= (9.8\pm 1.6)\times 10^9\rm K ~km ~s^{-1} ~pc^2$.

![image](cont-J1319-103ghz.png) ![image](line-J1319-CO-6-5.png)

![image](cont-J2054-92ghz.png) ![image](line-J2054-CO-6-5.png)

![](mom-spec-j1319-2054-0129.png)

|  | J0224-4711 | J1319+0950 | J2054-0005 |
|:---|:--:|:--:|:--:|
| CO transition | CO(7-6) | CO(6-5) | CO(6-5) |
| $z_{\rm CO}$ | $6.5220\pm0.0002$ | 6.1331 $\pm$ 0.0004 | 6.0391 $\pm$ 0.002 |
| FWHM$_{\rm CO}$ \[$\rm km\ s^{-1}$\] | $307\pm25$ | 529 $\pm$ 41 | 229 $\pm$ 20 |
| F$_{\rm CO}$ \[Jy $\rm km\ s^{-1}$\] | $0.342\pm 0.052$ | 0.662 $\pm$ 0.094 | 0.288 $\pm$ 0.047 |
| L$^\prime_{\rm CO}$ \[$\rm K ~km ~s^{-1} ~pc^2$\] | $(9.6\pm 1.4)\times 10^{9}$ | $(2.3 \pm 0.3)\times 10^{10}$ | $(9.8\pm 1.6)\times 10^{9}$ |
| L$_{\rm CO}$ \[L$_\odot$\] | $(1.6\pm 0.2)\times 10^{8}$ | $(2.4 \pm 0.3)\times 10^{8}$ | $(1.0\pm 0.2)\times 10^{8}$ |
| M$_{\rm H2, CO}^{(\rm a)}$ \[M$_\odot$\] | (1.0 $\pm$ 0.1) $\times 10^{10}$ | $(1.5 \pm 0.2)\times 10^{10}$ | (6.4 $\pm$ 1.0) $\times 10^9$ |
| $z_{\rm [CI]}$ | $6.5211\pm0.0004$ | – | – |
| FWHM$_{\rm [CI]}$ \[$\rm km\ s^{-1}$\] | $165\pm29$ | – | – |
| F$_{\rm [CI]}$ \[Jy $\rm km\ s^{-1}$\] | $0.108 \pm 0.036$ | – | – |
| L$^\prime$\[CI\] \[$\rm K ~km ~s^{-1} ~pc^2$\] | $(3.0\pm 1.0)\times 10^{9}$ | – | – |
| L\[CI\] \[L$_\odot$\] | $(5.1\pm 1.7)\times 10^{8}$ | – | – |

**Notes.** $^{(\rm a)}$: assuming a conversion factor $\alpha_{\rm CO}$ = 0.8 $\rm M_{\odot} (K\,km \, s^{-1} \,pc^{2})^{-1}$ and assuming a brightness temperature ratio $\rm r_{76}=CO(7-6)/CO(1-0)=0.76$ for J0224-4711, $\rm r_{65}=CO(6-5)/CO(1-0)=1.23$ for J1319+0950, and J2054-0005.

# Analysis

## Dust properties and star formation rate

In order to ensure a self-consistent analysis of the cold-dust SEDs of J036+03, J0224-4711, J231-20 and J2054-0005, we performed an SED fitting of the flux densities reported in Tab. [\[tab:c3-table-obs\]](#tab:c3-table-obs) considering the tapered fluxes for the higher-resolution observations if needed (see Appendix [9](#app:b) for details of the tapering procedure). The observations of J231-20 in (cite: Pensabene2021) did not need additional tapering because their resolution was well matched and low enough to account for the fainter and more extended emission. Moreover, for J231-20, we considered the flux corrected for the contribution of the companion to the QSO emission as explained in Sect. [4](#sec:res).

We modeled the dust continuum in an optically thick regime with a modified black body (MBB) function given by $$\begin{equation}
\label{eq:MBB}
        S_{\nu_{\rm obs}}^{\rm obs} = S_{\nu/(1+z)}^{\rm obs} = \frac{\Omega}{(1+z)^3}[B_{\nu}(T_{\rm dust}(z))-B_{\nu}(T_{\rm CMB}(z))](1-e^{-\tau_{\nu}}),
    
\end{equation}$$

where $\Omega = (1+z)^4A_{\rm gal}D_{\rm L}^{-2}$ is the solid angle as a function of the surface area of the galaxy, $A_{\rm gal}$, and of the luminosity distance of the galaxy, $D_{\rm L}$. The dust optical depth is $$\begin{equation}
        \tau_{\nu}= \frac{M_{\rm dust}}{A_{\rm gal}}k_\nu= \frac{M_{\rm dust}}{A_{\rm gal}}k_0\biggl(\frac{\nu}{\nu_0}\biggr)^{\beta},
    
\end{equation}$$ where $\beta$ is the emissivity index, $k_{\nu}$ is the opacity, $k_0 = 0.45\  \rm cm^{2}\ g^{-1}$ is the mass absorption coefficient, and $\nu_0= 250$ GHz. The latter two terms define the opacity model adopted here (cite: beelen+2006; carniani2019). In this model, $k_\nu$ carries huge systematics because the actual composition of the dust is currently unknown. Variations in the opacity model can, in principle, lower dust masses by a factor of $\sim$ 3 or increase them by a factor of $\sim 1.5$. The solid angle for each source was estimated using the continuum mean size from resolved observations (see Tab. [\[tab:c3-table-obs\]](#tab:c3-table-obs)). The effect of the CMB on the dust temperature is given by $$\begin{equation}
        T_{\rm dust}(z)=((T_{\rm dust})^{4+\beta}+T_0^{4+\beta}[(1+z)^{4+\beta}-1])^{\frac{1}{4+\beta}},
    
\end{equation}$$ with $T_0 = 2.73$ K. We also considered the contribution of the CMB emission given by $B_{\nu}(T_{\rm CMB}(z)=T_0(1+z))$ (cite: dacunha2013).

Therefore, the MBB model has three fitting parameters: the dust temperature ($T_{\rm dust}$), the dust mass ($M_{\rm dust}$), and $\beta$. We explored the 3D parameter space using a Markov chain Monte Carlo (MCMC) algorithm implemented in the `EMCEE` package (cite: foreman2013). We assumed uniform priors for the fitting parameters: $10{\ \rm K} <T_{\rm dust}<300$ K, $10^{5} \ {\rm M_{\odot}}<M_{\rm dust}<10^{9}\ {\rm M_{\odot}}$, and $1.0<\beta<3.0$. The best-fitting $T_{\rm dust}$, $M_{\rm dust}$, and $\beta$, obtained from a MCMC with 40 chains, 6000 trials and a burn-in phase of $\sim 100$ for each QSO, are reported in Tab. [\[tab:c3-sed-res\]](#tab:c3-sed-res). The errors on the best-fitting parameters were computed considering the 16th and 84th percentiles of the posterior distribution of each parameter. Overall, we found $T_{\rm dust} = 50 - 80$ K, $M_{\rm dust}\sim 10^8\ \rm M_\odot$, and $\beta = 1.6-2.5$. Fig. [6](#fig:c3-sedj036) shows the observed SEDs with the best-fitting function and the posterior distributions of $T_{\rm dust}$, $M_{\rm dust}$, and $\beta$ for J036+03, J0224-4711, and J231-20, and Fig. [7](#fig:c3-sedj2054) shows this for J2054-0005.

![image](sed-j036-final-B3-tape-bis.png) ![image](corner_plot_j036-final-B3-tape-bis.png) ![image](sed-vj0224-mcmc-b9-peak-freq.png) ![image](corner_plot_vj0224-b9-peak.png) ![image](sed-j231-mcmc-b8-freq.png) ![image](corner_plot_j231-b8.png)

We estimated the total infrared (TIR) luminosity for the best-fit model for each source by integrating from $8$ to $1000\ \mu$m rest-frame, and we derived the SFR considering that ${\rm SFR}\propto L_{\rm TIR}$. The proportionality factor between SFR and $L_{\rm TIR}$ depends on the initial mass function (IMF) chosen. We adopted a Kroupa IMF (cite: kroupa2003). The values of $L_{\rm TIR}$ and SFR derived for our QSO sample are reported in Tab. [\[tab:c3-sed-res\]](#tab:c3-sed-res). An Salpeter or Chabrier IMF (cite: salpeter1955; chabrier2003) would imply an SFR that is higher by a factor of 1.16 or lower by factor of 0.67, respectively. When comparing with results of the SFR from the literature, we rescaled the SFR according to the Kroupa IMF (see also (cite: kennicutt2012)):

$$\begin{equation}
        \label{eq:sfr}
        {\rm SFR}\ ({\rm M_\odot\ yr^{-1}})= 1.496 \times 10^{-10}\ L_{\rm IR\ 8-1000\mu m} (L_\odot).
    
\end{equation}$$

![image](sed-j2054-mcmc-tape.png) ![image](corner_plot_j2054-tape.png)

As a word of caution, we recall that we adopted a lower limit for the flux in B8 of J231-20, and thus, $T_{\rm dust}$ and SFR can be underestimated in principle. By performing another fit considering the B8 flux not corrected for the contribution of the companion (which is an upper limit to the flux of the QSO), we indeed derived $T_{\rm dust}=61$ K and SFR$=1913 \ \rm M_\odot ~yr^{-1}$, which is a factor of 2 higher than that obtained considering the lower limit in B8, while the dust mass and emissivity index agree well with the previous values. The best-fitting curve is displayed as a dashed line in the bottom left panel of Fig. [6](#fig:c3-sedj036), along with the uncorrected B8 flux as an empty diamond. Hereafter, we conservatively use the results of the SED fitting with the B8 flux corrected for the companion emission, considering that the SFR can vary of a factor of 2 at most.

We adopted a contribution of the AGN emission to the dust heating of 50% considering that all our sources are hyperluminous QSOs at $z\gtrsim 6$, likely sharing similar properties with the hyperluminous QSOs at $z=2-4$ in (cite: duras2017) and with J1148+5251 in (cite: schneider2015), which also belongs to the HYPERION sample. This assumption yields SFR$=466\pm 75\ \rm M_{\odot}\ yr^{-1}$ for J036+03, an SFR$=2485^{+1682}_{-768} \ \rm M_{\odot}\ yr^{-1}$ for J0224-4711, an SFR$= 496\pm 118$ for J231-20, and an SFR$=730 \pm 75$ for J2054-0005. The role of AGN in heating the dust is further discussed in Sect. [6.1.6](#subsec:AGNeffect).

![image](sed-j183+05-mcmc-freq.png) ![image](corner_plot_j183.png) ![image](sed-j1342-mcmc-freq-novak.png) ![image](corner_plot_j1342-novak.png)

We wished to perform a statistically sound investigation of the dust properties in a sample of $z>6$ QSOs and therefore explored the archives and the literature in our search for other suitable candidates for our analysis of cold-dust SED, that is, with ALMA and/or NOEMA observations of the continuum emission probing both the Rayleigh-Jeans regime and the peak region of the SED. To our knowledge, only four other QSOs at $z>6$ currently have multiple-frequency observations sampling the Rayleigh-Jeans part and, barely, the peak of the cold-dust SED: QSOs J1319+0950, J1148+5251, J1342+0928, and J183+05. Their SEDs were analyzed in (cite: carniani2019) (J1319+0950 and J1148+5251), in (cite: novak2019; witstok2023) (J1342+0928), and in (cite: decarli2023) (J183+05). Since we adopted the same method as (cite: carniani2019), we used the results for the dust properties and SFRs of J1319+0950 and J1148+5251 found in Carniani’s work, which are reported here in Table [\[tab:c3-sed-res\]](#tab:c3-sed-res). For consistency, we modeled the observed SEDs of the other two QSOs using the procedure described in the previous paragraph because the method and/or the opacity models adopted in (cite: novak2019; witstok2023; decarli2023) were different from ours. The best-fitting SEDs are shown in Fig. [8](#fig:c3-sedothers), and the results can be found in Tab. [\[tab:c3-sed-res\]](#tab:c3-sed-res). Within the uncertainties, our results agree well overall with those in the previous papers. The discrepancies in the best-fitting values arise from the different regime assumed (optically thin in (cite: novak2019), and thick in (cite: witstok2023; decarli2023)) and in the different opacity models.

It is worth noting that the uncertainties on $T_{\rm dust}$ (SFR) increase to $\sim 40\%$ ($>80\%$ for SFR) when the peak of the cold-dust SED is not probed: This is the case of J1319+0950 and J1342+0928, which lack ALMA observations in bands 8 and 9, and of J0224-4711, for which even band 9 is unable to reach the peak of the SED given that this QSO has an extremely bright dust emission. In the latter case, an ALMA B10 observation is required. The strongest effect is seen in J1342+0928, for which $T_{\rm dust}$ is determined with an uncertainty of $\sim 40\%$, leaving the SFR basically unconstrained. To investigate the impact of B8-B9 observations on the uncertainties of $T_{\rm dust}$, we again fit the SEDs for all the QSOs in our sample, excluding the data available at $\lambda_{\rm rest}>100\ \mu$m for each source, that is, corresponding to ALMA B8 and B9. We found that in this case, the uncertainties on $T_{\rm dust}$ become $\sim 70\%$ on average (in some cases, up to 90%). This highlights the importance of high-frequency observations (ALMA bands 8, 9, and 10) in providing precise and reliable estimates of the dust properties and SFR.

![](SEDs-all.png)

In Fig. [9](#fig:sed-all) we show the cold-dust SEDs analyzed in this work. All SEDs were normalized at $\lambda = 850\ \mu$m rest-frame in order to facilitate the comparison. It is worth noting the difference in slope and position of the peak, which are clearly related to the variation in the dust properties, namely $T_{\rm dust}$, $M_{\rm dust}$, and $\beta$.

Additionally, we developed an observed mean cold-dust SED by averaging (mean) the observational data available for all the QSOs in our sample in six wavelength bins[^5]. They are shown as dashed gray lines in Fig. [10](#fig:sed-mean), along with the resulting averaged fluxes as violet squares. The error bars are the standard errors on the mean associated with each flux. We fit this mean SED following the procedure described above, and we obtained $T_{\rm dust}=54^{+8}_{-4}$ K, $M_{\rm dust}=(4.6\pm 3.0)\times 10^8\ \rm M_\odot$, and $\beta=1.6 \pm 0.55$. Fig. [10](#fig:sed-mean) shows the best-fitting function and the posterior distribution of each fitting parameter.

![](sed-mean-wave-gray.png)

![](corner_plot_sed_mean.png)

## Molecular gas mass

In this section, we infer the molecular gas mass of QSOs J0224-4711, J1319+0950, and J2054-0005 from molecular tracers such as the CO(7-6) and CO(6-5) emission lines. The molecular gas mass estimates in high-$z$ QSO host galaxies rely on CO observations, and especially on intermediate (J$_{\rm up}$=5-7) transitions (cite: venemans2017a; Yang2019; decarli2022), which are found to be at the peak of the CO spectral line energy distribution (cite: li2020; feruglio2023). In principle, low-J transitions should be preferred, as they are less sensitive to uncertainties on the CO excitation. However, these are quite challenging to detect because of their intrinsic faintness.

The molecular gas mass was therefore derived as

$$\begin{equation}
        M_{\rm H2, CO} = \alpha_{\rm CO} r^{-1}_{\rm J-(J-1)} L_{\rm CO(J-(J-1))},
    
\end{equation}$$

where $\alpha_{\rm CO}=0.8~ \rm M_{\odot}~ (K\,km\,s^{-1} \,pc^{2})^{-1}$ is the CO-to-H$_2$ conversion factor typical for ULIRG and QSOs (cite: carilli2013), and $r_{\rm J-(J-1)}$ is the CO(J-(J-1))/CO(1-0) luminosity ratio. Fig. [11](#fig:c2-cosled) shows the CO SLEDs normalized to the J$_{\rm up}$=6 transition of J036+03 (cite: decarli2022) and J2054-4711, limited to the (6-5) and (7-6) transitions (cite: decarli2022), compared with other $z>6$ QSOs, and QSO APM0879+5255 at $z=3.9$ and QSO Cloverleaf at z=2.56 (cite: li2020; feruglio2023), for which the CO SLED is well constrained down to J$_{\rm up}$=1. We note that the CO SLED for QSO at $z>6$ presents a flattening at the CO(6-5) and (7-6) transitions on average, and that all CO SLEDs have similar slopes from CO(6-5) to CO(2-1) transitions, while at higher J, the CO SLED are very different.

So far, APM0879+5255 and Cloverleaf are the only objects for which the CO(1-0) transition is detected and the ratio of the transition CO(2-1) and (1-0) is consistent between the two sources. The upper limit on the CO(1-0) of J1148+5251 also indicates a similar CO(2-1)-to-CO(1-0) ratio. Therefore, in order to estimate the molecular gas mass for J1319+0950, and J2054-0005 from CO(6-5), we assumed $r_{65}=$CO(6-5)/CO(1-0)=$1.23\pm 0.66$, considering the average between the maximum and minimum values of $r_{65}$ in APM0879+5255 and Cloverleaf. We then obtained $M_{\rm H2}=(1.5 \pm 0.2)\times 10^{10}$ for J1319+0950, and $M_{\rm H2}=(6.4 \pm 1.0) \times 10^9\ \rm M_\odot$ for J2054-0005. Regarding J0224-4711, we assumed that CO(7-6)$\sim$CO(6-5), given the averaged CO SLED of high-$z$ QSO (see Fig. [11](#fig:c2-cosled)), and $r_{76}=0.76\pm 0.41$, considering the average between APM0879+5255 and Cloverleaf. This gave $M_{\rm H2}=(1.0 \pm 0.1) \times 10^{10}\ \rm M_\odot$ for J0224-4711.

For the purposes of this work, we also investigated the properties of QSO J036+03, and thus, we computed its molecular gas mass from CO(6-5) consistently with the rest of the sample. (cite: decarli2023) reported the detection of the CO(6-5) emission line of J036+03, finding $L'_{\rm CO(6-5)}=(1.27\pm 0.11)\times 10^{10}~ \rm K\,km\,s^{-1} \,pc^{2}$. This yielded $M_{\rm H2}=(7.5 \pm 0.64) \times 10^9\ \rm M_\odot$ following our assumptions.

![](co-sled.png)

Our analysis revealed that the gas masses in our sample of QSOs, estimated with the smallest statistical uncertainties, are $\sim 10^{10}\ \rm M_\odot$ on average. However, it is worth noting that our assumptions for the CO(6-5)-to-CO(1-0) (or CO(7-6)-to-CO(1-0)) line ratio introduce significant systematic uncertainties to our estimates of $\gtrsim 50\%$. Our results agree well on average with the gas masses found in (cite: neeleman2021) derived from converting the \[CII\] underlying continuum flux into a dust mass and then assuming a constant GDR (=100). In contrast, the gas mass estimated from converting the \[CII\] luminosity directly into a molecular mass using the conversion of (cite: zanella2018) mostly is higher by one order of magnitude than ours. Specifically, molecular gas masses for QSOs J1319+0950 and J2054-0005 were derived in (cite: neeleman2021), who reported higher values than ours using the GDR and the Zanella conversion factor. In the former case, the GDR assumed in (cite: neeleman2021) (GDR=100) may not be valid for every QSO (see the results and discussion of the GDR in our sample in Sect. [6.1.5](#subsec:GDR)). In the latter, the Zanella conversion factor, which is calibrated for $z\sim 2$ main-sequence galaxies, may not be applicable for high-$z$ QSO hosts. This was also reported in (cite: Tripodi2022) for the case of QSO J2310+1855 at $z\sim 6$.

The molecular gas masses and line properties are summarized in Tab. [\[tab:c2-colines\]](#tab:c2-colines). The uncertainties reported on the gas mass are only statistical. Systematics uncertainties are induced by the choice of $\alpha_{\rm CO}$ (a factor of 0.2-0.3 dex) and by the scaling from high-J CO transition to J=1 using the CO excitation ladder (a factor of 20-30%).

# Discussion

In this section, we first discuss our findings concerning the dust and gas within our high-$z$ QSO sample by conducting a comparative analysis with the properties observed in lower-z sources. Finally, we investigate the evolutionary paths of the ten QSOs in our sample, exploiting the results for the properties of their host galaxies derived in Sects. [5.1](#sec:sed) and [5.2](#sec:gasmass).

## Properties of the QSO host galaxies

Our final sample comprises ten QSOs at $6\lesssim z<7.5$, out of which six belong to the HYPERION sample. In the previous sections, we analyzed the cold-dust SED in a homogeneous way for all quasars, and the results are summarized in Tab. [\[tab:c3-sed-res\]](#tab:c3-sed-res). In the following, we briefly describe the compilation of galaxy and AGN host samples we used for the comparison.

![](fig_Tdust_all_combined.png)

For the local Universe, we considered the JCMT dust and gas the In Nearby Galaxies Legacy Exploration (JINGLE) survey, the *Herschel* (U)LIRG Survey (HERUS), and a sample of QSOs selected from the Palomar-Green (PG) survey (cite: witstok2023). The JINGLE sample is composed of 192 nearby ($0.01<z<0.05$) galaxies, for which (cite: lamperti2019) studied their cold-dust SED using photometric data in the 22-850 $\mu$m range from *Herschel*, applying a hierarchical Bayesian fitting approach. We used the cold-dust properties derived from their two MBB models, which also take into account the warm dust component in the optically thin regime. These results agreed well with those from a single MBB model. The HERUS sample comprises 43 $z<0.3$ (ultra)-luminous infrared galaxies or (U)LIRGs observed with the *Infrared Astronomical Satellite* (IRAS) and *Herschel* (cite: sanders2003; clements2018). (cite: clements2018) derived the dust properties for this sample assuming an MBB function in the optically thin regime. (cite: witstok2023) recalculated the dust properties of the JINGLE and HERUS datasets, employing a method analogous to ours (see Sect. [5.1](#sec:sed) and (cite: witstok2022)), except for the variation in the chosen opacity model. Their results agreed with those presented in (cite: lamperti2019) and (cite: clements2018) within the uncertainties. Therefore, for the sake of simplicity, we used the results from the original papers. The dust properties of the PG sample, consisting of 85 nearby ($z<0.5$) QSOs, were obtained by (cite: petric2015) through modeling the photometry taken by *Herschel* by means of an MBB function with $\beta$ fixed to 2.0 and the dust model of (cite: draine2007)[^6].

At higher redshift, we selected a sample of 81 $2<z<7$ strongly gravitationally lensed, dusty star-forming galaxies identified by the South Pole Telescope (SPT). (cite: reuter2020) analyzed the cold-dust SEDs of the objects in this sample employing an MBB function in the optically thick regime with $\beta$ fixed to 2. We also included the dust properties inferred for 16 QSOs belonging to the WISE-SDSS Selected Hyper-luminous (WISSH) sample at $2<z<5$ (cite: duras2017). Their SEDs were analyzed accounting for the cold dust, dusty torus, and warm dust emission components. In particular, the cold-dust emission was modeled by an MBB function in the optically thin regime with $\beta=1.6$. Finally, at $4<z<7.5$, we considered a sample composed of three submm galaxies (SMGs) and eight star-forming (SF) galaxies from (cite: witstok2023). As stated before, they adopted a model for the SED fitting analogous to ours. For the QSO host galaxy samples, we note that the PG QSOs have a lower bolometric luminosity $L_{\rm bol}$ compared to our $z\gtrsim 6$ sample ($L_{\rm bol, PG} \sim 10^{44-47}\rm ~erg ~s^{-1}$), whereas the WISSH quasars are the most luminous, with $L_{\rm bol, WISSH} \gtrsim 10^{47.5}\rm ~erg ~s^{-1}$ (cite: vietri2018).

### Dust temperature

In the past few years, the trend of $T_{\rm dust}$ as a function of time has been the object of multiple studies (cite: faisst2017; schreiber2018; sommovigo2020; bakx2021; viero2022). However, the behavior of the $T_{\rm dust}-z$ relation, which increases or plateaus at $z>4$, has remained unclear. The top panel of Fig. [12](#fig:c3-tdust-z) presents the redshift distribution of the dust temperatures in our sample compared to the low-z samples described above. Additionally, we display the average $T_{\rm dust}$ derived for REBELS[^7] galaxies by (cite: sommovigo2022) as a light blue triangle, and $T_{\rm dust}$ found for three REBELS galaxies at $z>6.7$ by (cite: algera2023) as light blue diamonds. As a word of caution, the dust temperatures for REBELS galaxies derived in (cite: sommovigo2022) carry large uncertainties since they are based on a combination of a single photometric point in band 6 and the \[CII\] line emission. Hence, in this context, we exclusively present the mean value. (cite: algera2023) analyzed band 8 and 6 observations of REBELS-12[^8], REBELS-25, and REBELS-38 considering both optically thin and thick cases. We present the results for the optically thick case, fixing $\beta=1.5$[^9]. Because we relied on only two photometric points per galaxy, the inferred $T_{\rm dust}$ are still uncertain ($\Delta T_{\rm dust}=30-60\%$); the results obtained in the thin and thick regime agree within the large uncertainties. For clarity, we show the mean values of the temperature distribution for the JINGLE and HERUS samples with their corresponding standard deviation[^10]. Interestingly, there is no significant difference in $T_{\rm dust}$ between QSOs and normal SF galaxies at fixed redshift, also considering that our sample is biased toward high luminosity and therefore possibly higher dust temperatures.

We observe an increasing trend of $T_{\rm dust}$ with redshift that is naturally expected from a theoretical perspective as a result of decreasing gas depletion times, as seen in (cite: sommovigo2022). Sommovigo et al. theoretically derived that $T_{\rm dust}\propto t_{\rm dep}^{-1/6}\propto (1+z)^{5/2(4+\beta)}$, where $\beta$ is the dust emissivity index. This $T_{\rm dust}-z$ relation is shown in Fig. [12](#fig:c3-tdust-z) (dash-dotted gray line) for $\beta=2.03$ and assuming optical depth and metallicity (in solar unit) both equal unity, as presented in (cite: sommovigo2022), implying $T_{\rm dust}\propto (1+z)^{0.42}$. This theoretical relation is able to reproduce the trend observed in many SF galaxies (e.g., considering REBELS and ALPINE galaxies), and in (cite: schreiber2018) from the stacking of star-forming galaxies at $0.5<z<4$ in the deep CANDELS fields. The stacked SEDs were fit with a library of template SEDs generated with $\beta=1.5$. (cite: schreiber2018) found a linear trend with redshift, and we also show an extrapolated curve at $z>4$ as dashed green line.

![](beta-z.png)

![](SFR-Mdust.png)

On the other hand, the population of SPT SF galaxies, QSOs ,and SF with $T_{\rm dust}>60$ K shows a steeper increase in $T_{\rm dust}$ with z, which is well captured by the observed relation inferred by (cite: viero2022). They employed stacked maps in the FIR/submm of 111227 galaxies at $0<z<10$ from the COSMOS-MOS2020/FARMER catalog to derive dust temperatures at different redshifts. Their observed relation for $T_{\rm dust}(z)$, which is a second-order polynomial in $z$, agrees well with the observed trend of the WISSH QSOs, with the sources at $z>5$ that shows the most extreme temperatures ($\sim 70-80$ K), and with the lower limit of (cite: bakx2020) and estimate of (cite: behrens2018) based on data from (cite: laporte2017) (cite: viero2022). However, it fails to describe the bulk of the PG QSOs and HERUS ULIRGs and the sources at $z>5$ with temperatures below $60$ K ((cite: faisst2020; bethermin2020; hashimoto2019; sommovigo2022), see (cite: viero2022)). As a word of caution, these latter low-temperature estimates are very uncertain because they were derived from ALMA observations that did not bracket the peak of the SED, and they are therefore not adequate for modeling hotter dust components.

In order to find a general relation that can be applied to SF galaxies, SMGs, and QSO host galaxies at high $z$, we fit the observed data (excluding the stacked results) adopting the parameterization of $T_{\rm dust}(z)$ that was theoretically found in (cite: sommovigo2022), therefore using a power law of the form

$$\begin{equation}
        T_{\rm dust} (z) = A \times (1+z)^B,
    
\end{equation}$$

where $A$ and $B$ are free fitting parameters. The latter is linked with $\beta$, since $\beta=-4+5/2B$ (considering the derivation of (cite: sommovigo2022)). We found $A=19\pm 2$ K and $B=0.7\pm 0.1$, implying a value of $\beta$ that is unphysical. This underlines that $T_{\rm dust}$ does not depend uniquely on redshift, especially when considering different galaxy populations. (cite: sommovigo2022) pointed out that at fixed redshift, the scatter in $T_{\rm dust}$ derives from variations either in optical depth or in metallicity. This is a likely scenario for different galaxy populations. Our best-fitting function, shown as a purple line and shaded region in the top panel of Fig. [12](#fig:c3-tdust-z), is slightly flatter than Viero’s at $z>1$, but still agrees with it pretty well in both the low- and high-$z$ regimes. It captures both the flattening and the increasing trends at $z>4$, that is, it describes the populations with both higher and lower $T_{\rm dust}$.

Taking advantage of our robust estimates for $T_{\rm dust}$ in our QSO sample, we also performed a fit only to the observed QSO dust temperatures at different redshift in order to investigate the $T_{\rm dust}-z$ relation in QSOs for the first time. We found $A=29\pm 2$ K and $B=0.35\pm 0.04$. This trend is flatter than Sommovigo’s, but still agrees well with observed SF galaxies. The majority of the sources are within the uncertainties, including those from (cite: schreiber2018). Three sources with low $T_{\rm dust}$ belonging to the sample of (cite: witstok2023) (SPT0311-58W, SPT0311-58E, and A1689-zD1) agree within $2\sigma$ with our relation, along with another three sources that are well known for their low dust temperatures (cite: witstok2022; algera2023; harikane2020). As a word of caution, the dust temperature estimated for J0217-0208 and COS-3018555981 has large uncertainties because the data available for the two sources are poor (one or two detections and an upper limit) and because of the assumption of $\beta=1.5$. In particular, for COS-3018555981, we show the upper limit on $T_{\rm dust}$ derived in (cite: witstok2022). Even if these two sources were excluded from our fit of the $T_{\rm dust}-z$ relation, our results would not change. As discussed in (cite: sommovigo2022), the scatter seen in $T_{\rm dust}$ at fixed redshift can be explained by variations in column density and metallicity within sources for optically thin and thick galaxies, respectively. This best-fitting relation is shown as a purple line with shaded region in the bottom panel of Fig. [12](#fig:c3-tdust-z).

### Dust emissivity

We now focus on the investigation of the dust emissivity index, $\beta$, which is physically related to the microscopic properties of dust. Fig. [13](#fig:c3-beta-z) shows the redshift distribution of $\beta$ for our sample and the comparison samples. As was also found in (cite: witstok2023), $\beta$ does not evolve with redshift, with a mean value of $\sim 1.6\pm 0.2$ (cite: beelen+2006), indicating that the average dust properties do not change drastically. Interestingly, other studies of SMGs found a value of $\beta$ that was closer to 2 on average (cite: dacunha2021; cooper2022; bendo2023; mckay2023; liao2023). There is no difference (on average) in this case either between the QSOs belonging to the HYPERION sample and the others. As a word of caution, we note that high-$z$ samples are biased toward high luminosity, and this can introduce a bias toward lower values of $\beta$ (cite: witstok2023). $\beta$ is significantly higher than 2 in only two exceptions, all of which lie in the high-$z$ regime: J0100+2802, J036+03 from our sample, and GN10 from (cite: witstok2023).

It is not straightforward to assess the physical reasons of these high $\beta$ value. In principle, $\beta$ depends on the physical properties and chemical composition of the grains, and possibly on environment and temperature. There are cases in which $\beta$ can be higher than 2 (cite: valiante2011; galliano2018). Spatially resolved studies in low-z galaxies showed a spread of $\beta$ within a single galaxy, probably due to the temperature mixing, the different properties of the grain populations, or a combination thereof (cite: galliano2018). (cite: liao2023) discussed how to interpret $\beta$ in terms of dust properties and suggested that the grain composition plays a significant role in determining $\beta$. Simulations conducted by (cite: hirashita2014) indicated that a $\beta$ value of 2 can result from emission by either graphite or silicate grains. However, the correlation between the exact grain composition and $\beta$ is unclear. In our case, a physical explanation for the high value of $\beta$ would require studies of the dust grain properties and/or a detailed analysis of the temperature mixing, which is beyond the scope of this work.

### Dust mass and star formation ratio

In Fig. [14](#fig:c3-SFR), we compare the SFR versus dust mass of our sample with results from the PG and WISSH sample of QSOs. In our sample, five QSOs are the first at $z>6$ for which the SFR was derived with the smallest statistical uncertainty based on high-frequency observations. As already mentioned in Sect. [5.1](#sec:sed), the uncertainty of $\sim 40\%$ on $T_{\rm dust}$ of J1342+0928 strongly affects the determination of the SFR, which has a large uncertainty. Therefore, this QSO is marked with a green circle in the plot. A correlation between the dust content and the star formation activity is evident in all the three samples, which are at different redshifts, with some scatter. This correlation is thought to be a consequence of the Schmidt-Kennicutt relation, linking the SFR to the dust content through the GDR (cite: santini2014). Overall, the SFR is higher in the $z>2$ samples (by $\sim 2$ orders of magnitudes on average), supporting the well-known concept that high-$z$ QSOs are hosted in highly star-forming galaxies. The dust masses are higher at high $z$ by $\lesssim 2$ orders of magnitudes on average as well.

Observations of galaxies at low and high $z$ (cite: dunne2011; driver2018; pozzi2020; beeston2018) found that the amount of dust in galaxies has decreased by a factor of $\sim 2-3$ during the last $\sim 8$ Gyr, and this was recently reproduced by (cite: parente2023) using the semi-analytic model (SAM) L-GALAXIES2020. Considering an average value, we also observe a mild increase in the dust mass from our HYPERION sample ($M_{\rm dust, HYP}^{\rm mean}=1.8 \times 10^8\ \rm M_\odot$) to the WISSH sample at lower-z ($M_{\rm dust, WISSH}^{\rm mean}=3 \times 10^8\ \rm M_\odot$), and followed by a drop of 2 orders of magnitude at $z\sim 0$. Interestingly, here, we observe a difference within our sample: Four HYPERION QSOs have lower dust mass than the other $z>6$ QSOs, up to more than about one order of magnitude and a factor of 2 on average. However, this is a preliminary result because two-thirds of the sample still has to be analyzed, and we will design future ALMA and NOEMA observations to complete the overview of the sample.

Even though we focused on QSOs, we recall that the relation between SFR and dust mass has also been studied in normal galaxies (cite: santini2014; dacunha2010; hjorth2014) and in SMGs at $z=1-4$ (cite: dudzevi2020). (cite: santini2014) used *Herschel* observations to estimate the dust mass of a large sample of galaxies extracted from the GOOD-S, GOOD-N, and COSMOS fields, and they performed a stacked analysis on a grid of redshifts, stellar masses, and SFR. Similarly to us, they found correlations between SFR and dust mass at different redshifts, from the local Universe out to $z=2.5$. Their analysis revealed no clear evolution of the dust mass with redshift at a given SFR and stellar mass, indicating that galaxies with similar properties (in terms of SFR and stellar mass) do not show a significant difference in terms of dust content across the cosmic epochs, out to $z=2.5$.

It is challenging to assess whether or not there is an evolution of $M_{\rm dust}$ with z at fixed SFR for the samples of QSOs we considered because the statistics is still poor at high $z$, especially for the low $M_{\rm dust}$ regime. Moreover, we are not able to explore the relation involving the stellar mass in our sample because $M_{\rm *}$ estimates are not yet available for our high-$z$ sample. Future JWST campaigns devoted to the investigation of the stellar content in QSOs and galaxies at $z\gtrsim 6$ will certainly allow us to perform these studies in detail (cite: harikane2023; santini2023).

### Star formation efficiency

![](SFR-MH2.png)

The efficiency with which gas is converted into stars may vary by some orders of magnitude depending on the QSO and galaxy properties, such as luminosity, mass, the presence of a disk, bulges or mergers, and on cosmic time. At fixed redshift, the observed strong variation in the gas star formation efficiency (${\rm SFE}={\rm SFR}/M_{\rm H_2}$) has usually been attributed to the existence of two distinct star formation laws: a secular mode in main-sequence (MS) galaxies, and a star-bursting (SB) mode characterized by short gas depletion timescales ($\tau_{\rm dep}= 1/{\rm SFE}\lesssim 100$ Myr; e.g., (cite: solomon2005; sargent2014; daddi2010; scoville2023; genzel2010; vallini2024)). The Kennicutt-Schmidt (KS) relation between the $\Sigma_{M_{\rm H2}}$ and $\Sigma_{\rm SFR}$ (cite: kennicutt1998) is the most common method for studying the SFE in galaxies. However, we lack spatially resolved observations for all the QSOs in our sample. As an alternative, we discuss the integrated KS relation, considering $M_{\rm H_2}$ and $\rm SFR$.

The wide range of SFEs, and thus $\tau_{\rm dep}$, that is spanned by different galaxies at different cosmic times is shown in Fig. [15](#fig:SFE). We compared our results (red and green stars) with the $2<z<5$ WISSH QSO sample, $1<z<1.5$ QSOs (cite: castillo2024), a sample of narrow-line Seyfert 1 galaxies at $z<0.1$ (cite: salome2023), 23 PG QSOs at $z<0.1$ (cite: shangguan20a; shangguan20b), $0.025<z<0.05$ xCOLDGASS galaxies (cite: saintonge2011; saintonge2017), $0.002<z<0.09$ LIRGs and ULIRGs with CO(1-0) detections from the literature (cite: tacconi2018), and AGNs at $z<0.05$ selected from the *Swift*-BAT all-sky catalog (cite: rosario18; koss21). As a reference, we also plot the gas MS computed by (cite: sargent2014) considering a sample of galaxies at $0<z<2$ (solid black line). While discussing this comparison, we recall the possible sources of systematic uncertainties (see also Sects. [5.2](#sec:gasmass), [6.1.6](#subsec:AGNeffect)): the assumption of the $\alpha_{\rm CO}$, the scaling from the CO ladder for the CO($J\rightarrow J-1$) transition with $J>1$, and the assumption of $T_{\rm dust}$ for the cold-dust SED fitting and of the AGN contribution to the dust heating (for AGN-QSOs only).

Our sample exhibits $\tau_{\rm dep}\sim 10^{-2}$ Gyr, which is smaller by $1-2$ orders of magnitude than those of the comparison samples up to $z\sim 2$. As pointed out in Sect. [6.1.1](#subsec:tdust), this may be connect to the high dust temperatures found in our QSOs. (cite: vallini2024) modeled the variation in the dust temperature in terms of gas depletion timescales, optical depth, and metallicity. Based on the values of $T_{\rm dust}$ in Tab. [\[tab:c3-sed-res\]](#tab:c3-sed-res), the implied $\tau_{\rm dep}$ of the (cite: vallini2024) models agrees with those found from the observed SFR and $M_{\rm H_2}$ (see Tab. [\[tab:c3-sed-res\]](#tab:c3-sed-res)).

Moreover, considering the high-z MS derived by (cite: scoville2023), our QSO host galaxies are found to be star-bursting sources. The star-bursting nature of our sample is also supported by the fact that $\tau_{\rm dep}$ is lower than that found considering the relation of (cite: tacconi2020) for $\tau_{\rm dep}(z)$ in SB galaxies extrapolated up to $z\sim 6$ (cite: vallini2024). According to the results of (cite: scoville2023), for SB galaxies such as ours, 70% of the increased SFR relative to the MS is due to the elevated SFEs and not to the increased gas masses at early epochs.

### Gas-to-dust ratio

![](GDR-z-log.png)

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| QSO | z | $\log(M_{\rm BH}/M_\odot)$ | $\log(M_{\rm dyn}/M_\odot)$ | SFR | $G_{\rm BH}$ | $G_{\rm GAL}$ | angles | Class | Refs |
|  |  |  |  | \[$\rm M_\odot \ yr^{-1}$\] | \[$10^{-8}\rm \ yr^{-1}$\] | \[$10^{-8}\rm \ yr^{-1}$\] | \[deg\] |  |  |
| J0100+2802 | 6.327 | 10.04 $\pm$ 0.27 | 10.51 $\pm$ 0.1 | 396 | 2.5 | 1.8 | 54 | BG (S) | \[1\],\[2\] |
| J036+03 | 6.540 | 9.49 $\pm$ 0.12 | 10.46 $\pm$ 0.1 | 466 | 1.1 | 1.8 | 31 | GG | \[1\],\[2\] |
| J0224-4711 | 6.522 | 9.36 $\pm$ 0.08 | 10.58 $\pm$ 0.3 | 2485 | 2.3 | 6.9 | 19 | GG | \[1\],\[3\] |
| J231-20 | 6.587 | 9.50 $\pm$ 0.09 | 10.15 $\pm$ 0.2 | 496 | 1.0 | 4.5 | 13 | GG | \[1\],\[2\] |
| J1342+0928 | 7.540 | 8.90 $\pm$ 0.14 | 10.56 $\pm$ 0.3 | 180 | 3.1 | 0.5 | 81 | BG | \[1\],\[2\] |
| J1148+5251 | 6.419 | 9.74 $\pm$ 0.03 | 10.18 $\pm$ 0.3 | 1570 | 1.1 | 16 | 4 | GG | \[1\],\[4\] |
| J2310+1855 | 6.003 | 9.67$^{+0.06}_{-0.08}$ | 10.72 $\pm$ 0.1 | 1855 | 1 | 4 | 15 | GG | \[5\],\[6\] |
| J2054-0005 | 6.390 | 9.17 $\pm$ 0.3 | $>10.46$ | 730 | 1.1 | 2.7 | 23 | GG | \[2\] |
| J1319+0950 | 6.133 | 9.53$^{+0.05}_{-0.11}$ | 11.09 $\pm$ 0.1 | 1197 | 0.9 | 1.0 | 43 | S | \[5\],\[2\] |
| J183+05 | 6.439 | 9.41$^{+0.21}_{-0.41}$ | $>11.11$ | 894 | 1.0 | 0.7 | 54 | BG (S) | \[5\],\[2\] |

**Notes.** Columns: QSO name; redshift; BH mass; dynamical mass; SFR computed in Sect. [5.1](#sec:sed); slope of the relation $G_{\rm BH}-G_{\rm gal}$, exemplified by the slope of the arrows in Fig. [17](#fig:c4-mbh-mdyn); classification of the evolutionary state of each QSO; references for BH and dynamical masses. QSOs above the double black line belong to the HYPERION sample. SFRs are corrected by a factor of 50% to account for the possible contribution of the AGN to the dust heating (see Sect. [6.1.6](#subsec:AGNeffect)). The dynamical mass for J0224-4711 was preliminarily estimated using the \[CII\] FWHM from an archival ALMA observations in band 6. This work is still in progress (Tripodi in prep.). Classification: BG = BH growth regime, S = symbiotic growth regime, and GG = galaxy growth regime. J0100+2802 and J183+05 are classified twice; see text (Sect. [6.2](#subsec:evol)). References: \[1\] (cite: zappacosta2023); \[2\] (cite: neeleman2021); \[3\] Tripodi in prep.; \[4\] (cite: riechers2009); \[5\] (cite: mazzucchelli2023); \[6\] (cite: Tripodi2022). For each line with multiple references, the first reference is for $M_{\rm BH}$ and $L_{\rm bol}$, which enters in $\dot{M}_{\rm BH}$, and the second reference is for $M_{\rm dyn}$.

We computed the GDR for the QSOs in our sample using the dust and gas masses reported in Tab. [\[tab:c3-sed-res\]](#tab:c3-sed-res), which were either estimated in this work or were taken from previous works in the literature (all references are reported in the table). In Fig. [16](#fig:c3-GDR), we present the redshift distribution of the GDR in our sample compared with the WISSH sample (cite: bischetti2021), a sample of $2<z<5$ star-forming galaxies hosting a heavily obscured AGN in the Chandra Deep Field-South (cite: damato2020), and a sample of $z>5.5$ QSOs (cite: calura2014). (cite: damato2020) derived the dust mass by modeling the SEDs with an MBB in the optically thin regime assuming $\beta=2.0$, and (cite: calura2014) also adopted a MBB in the optically thin regime, but assuming both $T_{\rm dust}=47$ K and $\beta=1.6$ because these two works both mostly relied on a single data point at 250 GHz. Therefore, these latter estimates for $M_{\rm dust}$ are highly uncertain and, for instance, $M_{\rm dust}$ (GDR) would be lower (higher) by $\sim 2.4$ times if a lower temperature, $T_{\rm dust}=33$ K, were assumed. For the comparison samples in Fig. [16](#fig:c3-GDR), the vertical black line represents an average uncertainty on the GDR of about 0.3 dex, which accounts for the uncertainties on the cold-dust SED modeling. For our sample, the dust masses are in constrast constrained with uncertainties smaller than 30% on average. Systematic uncertainties are also significant when the gas mass is derived from CO transitions higher than J=1-0 because this requires assuming a scaling between the luminosity of the considered CO transition and of CO(1-0) (see Sect. [5.2](#sec:gasmass)). This correction depends on the CO excitation ladder, which may vary from one source to the next depending on the ISM conditions. Given the large systematics in the gas mass determination (0.2-0.3 dex for $\alpha_{\rm CO}$ and 20-30% for $r_{65}$ or $r_{76}$), we did not include error bars in the GDR plot. We stress, however, that the dust masses in our sample are derived with the smallest statistical uncertainties. This has never been achieved before in a sample of QSOs at $z\gtrsim 6$. In low-z galaxies, a GDR$\sim 100$ is typically observed (cite: draine2007; leroy2011), while studies of massive star-forming galaxies and SMGs out to $z\sim 3-5$ found a GDR that might increase with z, with a typical GDR$\sim 120-250$ at $z \sim 2-4$ (cite: saintonge2013; miettinen2017). In some cases, the GDR was also found to be \<100, as in recent studies of SMGs (cite: birkin2021; liao2023). Overall, the WISSH sample and our sample of QSOs show GDRs above 100 on average (this value is also commonly assumed when deriving the dust mass). In particular, our HYPERION QSOs show the highest GDRs on average (GDRs$>100$) of the sources at $z>6$. Two QSOs, J1319+0950 and J231-20, exhibit particularly low ($<50$) GDRs that are comparable with other QSOs from (cite: calura2014). The tail of low GDRs in our sample, that is, GDR$<50$, can mostly be attributed to the different dust mass values because the gas masses are $\sim 10^{10}\ M_{\odot}$ for all the sources (see Sect. [5.2](#sec:gasmass)). J1319+0950 and J231-20 both have the highest dust masses in our sample, $M_{\rm dust}\sim (5-6) \times 10^8\ \rm M_\odot$.

### Caveat: Effect of active galactic nuclei on the dust heating

As mentioned in Sect. [5.1](#sec:sed), when the SFR is derived, the presence of an AGN at the center of the host galaxy likely plays a role in heating the surrounding dust. In theory, the galaxy is characterized by a distribution of dust temperatures that rise toward the center. Both observations and simulations have shown that in the innermost region of the host galaxy ($\sim$ a few hundred parsec), $T_{\rm dust}$ can be as high as some hundred K, and this is mainly due to the presence of the AGN as a heating source (cite: walter2022; dimascia2021; dimascia2022). The resolution of our observations prevents us from performing a spatially resolved study of the dust emission, and therefore, from isolating the warmer central dust component. We therefore modeled the dust emission with a single temperature BB, that is, we mixed the dust emission that is mainly heated by the stellar distribution with the emission that is mainly heated by the central AGN. This implies that the SFR derived above from the best-fit MBB might be contaminated by the contribution of the AGN to the heating of the dust in the center.

To overcome this problem, there are two different possibilities that can also be used simultaneously. First, observations with a resolution of $\sim 100-300$ pc can be used to disentangle the warmer dust component, which mainly resides in the center of the colder and more extended component. Then, it is possible to fit the warm and cold dust component separately, either using two MBBs or with an MBB for the cold dust emission and a radiative transfer modeling for the warm dust heated by the AGN. This approach has been adopted at high-$z$ only by (cite: tsukui2023) for a QSO host galaxy at $z=4.4$. They found a warm-dust component with $T_{\rm dust, warm}=87$ K and an AGN contribution to the dust heating of $\sim 60\%$.

![](mbh-mdyn-new-2.png)

The availability of very high-resolution data is still quite rare at high $z$, and this approach has indeed not yet been applied to any QSO at $z>4.4$. As an alternative to the spatially resolved study of the SED, radiative transfer models can be used to determine the AGN contribution to the dust heating. (cite: schneider2015) used a radiative transfer code to follow the transfer of radiation from the central source and from stellar sources through the dusty environment of the host galaxy of QSO SDSS J1148+5251 at $z=6.4$. For the stellar sources in the host galaxy, they adopted the SED computed with the PÉGASE population synthesis model using as input the star formation histories, age, and metallicities of the stellar populations predicted by GAMETE/QSOdust. To account for the emission of the dust in the host at longer wavelength, they considered two heating sources, (1) the stellar component and (2) the central AGN. This latter can account for up to $\sim 70\%$ of the dust emission, supporting the idea that AGN have a strong impact on heating the surrounding dust. The exact amount of the contribution of AGN to the dust heating depends on the prescription adopted to model the central source and the torus. (cite: schneider2015) tested alternative but still reasonable models and found that the AGN contribution can vary from $30\%$ to $70\%$. (cite: duras2017) also investigated the effect of the AGN to the FIR emission in the WISSH quasars at $1.8<z<4.6$, using the same approach as in (cite: schneider2015). In particular, considering the least and most luminous QSOs in their sample, they found that the AGN contribution to the FIR fluxes is $43\%$ and $60\%$, respectively, pointing toward a mild trend with luminosity. Therefore, they assumed an average contribution of $\sim 50\%$ to the total FIR luminosity, which also accounts for the uncertainties in the radiative transfer model and is in line with the average result found in (cite: schneider2015).

Considering that the dynamic range of bolometric luminosity, redshift, and properties of the host galaxy of the QSOs in our sample is quite small and that these properties are remarkably like those of J1148+5251, the impact of the AGN on the dust heating may be similar. Therefore, we considered an AGN contribution of $\sim 50\%$ to the dust heating. A precise estimate of the AGN impact on the FIR emission would require either a spatially resolved study of the SED or radiative transfer modeling. The former is not yet feasible because of the lack of high-resolution data, and the latter is beyond the scope of this project, but will be the goal of future investigations.

## Evolutionary paths

As mentioned in Sect. [1](#sec:intro), the BH masses of luminous QSOs at $z\gtrsim 6$ can be extremely high for their cosmic epoch, of about $\gtrsim 10^9\ \rm M_\odot$. The temporal window within which they could have accreted their mass spans approximately 650-750 Myr (considering a possible seeding era at $z=15-22$). These masses are not lower than those of hyperluminous QSOs at lower redshift, meaning that the BH growth had to be a fast process and that the process had to stop with a similarly high efficiency after the rapid build-up. QSOs at $z\gtrsim 6$ indeed appear to lie above the local $M_{\rm BH}-M_{\rm dyn}$ correlation, and thus the BH growth seems to precede that of its host galaxy (cite: volonteri2012; pensabene2020; fan2022).

Focusing on the BH dominance evolutionary scenario, which seems to be the most likely formation path of local massive galaxies, we can distinguish two large regimes: the first regime is characterized by an intense and predominant growth of the BH, and the second regime is marked by an intense and predominant growth of the host galaxy[^11]. Additionally, a transition phase can be imagined in which the growth of the two components is in almost perfect balance (a symbiotic growth). Already at $6<z<8$, SMBHs have reached masses similar to those observed in the most massive local galaxies. This implies that the SMBH growth has to slow down. At these redshifts, we may therefore be able to witness QSOs in their transition phase toward the galaxy regime or in the galaxy regime, for instance, moving toward the local relation in the $M_{\rm BH}-M_{\rm dyn}$ plane.

In the following, we quantitatively characterize the three different regimes outlined above (BH dominated, galaxy dominated, and symbiotic). For this purpose, we defined the growth efficiency of the galaxy as $G_{\rm gal}={\rm SFR}/M_{\rm gal}$, where $M_{\rm gal}= M_{\rm dyn}-M_{\rm BH}$ is the mass of the galaxy, and the SFR was corrected for the QSO contribution. This term is a lower limit to the specific SFR of the galaxy defined as SFR$/M_*$, which might be a better probe of the galaxy growth in principle. We did not use the specific SFR because the stellar mass is not yet available for most high-redshift QSOs. We derived the BH growth efficiency as $G_{\rm BH}=(1-\epsilon)\dot{M}_{\rm BH}/M_{\rm BH}$, where $\epsilon$ is the radiative efficiency, and $\dot{M}_{\rm BH}$ is the BH accretion rate that depends on the bolometric luminosity of the source[^12]. We assumed $\epsilon=0.1$ (cite: marconi2004), and we used the BH mass derived from the MgII emission line. Comparing these two terms, we distinguished among (1) $G_{\rm BH}>G_{\rm gal}$ or black-hole-dominance regime, (2) $G_{\rm BH}=G_{\rm gal}$ or symbiotic growth, and (3) $G_{\rm BH}<G_{\rm gal}$ or galaxy-dominance regime. The proportionality factor between $G_{\rm BH}$ and $G_{\rm gal}$ that allowed us to distinguish among these different regimes can be straightforwardly translated into an angle, that is, an angle $>45^{\circ}$ corresponds to the BH-dominance regime, an angle $\sim 45^{\circ}$ to the symbiotic growth, and an angle $< 45^{\circ}$ to the galaxy regime. The properties derived for our sample of QSOs are summarized in Tab. [\[tab:c4-prop\]](#tab:c4-prop). In particular, the SFRs were derived in this work, the BH masses and bolometric luminosities for $\dot{M}_{\rm BH}$ (cite: zappacosta2023; mazzucchelli2023), and the dynamical masses (cite: neeleman2021; riechers2009; Tripodi2022) were taken from the literature as reported in the last column of Tab. [\[tab:c4-prop\]](#tab:c4-prop).

Before we discuss our results, it is important to briefly illustrate the possible caveats. As reported in Tab. [\[tab:c4-prop\]](#tab:c4-prop), both $M_{\rm BH}$ and $M_{\rm dyn}$ carry large systematic uncertainties[^13] (0.1-0.3 dex). Additionally, even though the SFR was derived with high statistical accuracy and corrected for a reasonable AGN contribution (50%; see Sect. [6.1.6](#subsec:AGNeffect)), this contribution may in principle vary from $\sim$ 30% to 70%. These uncertainties (a factor of $\sim$ 2 for $M_{\rm BH}$ and $M_{\rm dyn}$, and a factor of $\sim$ 1.5 for the SFR) affect the inferred evolutionary scenario because $G_{\rm BH}$ may vary by a factor of 2 and $G_{\rm gal}$ by a factor of 3 at most. Keeping in mind these systematics, we discuss our results below, based on the best-fitting values for $M_{\rm BH}$, $M_{\rm dyn}$, and SFR (reported in Tab. [\[tab:c4-prop\]](#tab:c4-prop)).

We evaluated the evolutionary state of the QSOs in our sample. Fig. [17](#fig:c4-mbh-mdyn) presents our results, where the HYPERION QSOs in our sample are shown as a star with green contours, and the other QSOs in our sample as a star with red contours. The stars are color-coded as a function of $G_{\rm gal}$. The slope of the arrows associated with each star corresponds to the angle reported in Tab. [\[tab:c4-prop\]](#tab:c4-prop), that is, to the proportionality factor of the $G_{\rm BH}-G_{\rm gal}$ relation. Given the large systematics quoted above, we did not draw the uncertainty of the arrows for clarity. Overall, the growth of the QSOs in our sample is mainly dominated by the galaxy, or it is symbiotic (see also Tab. [\[tab:c4-prop\]](#tab:c4-prop)). In particular, the color-code of the stars shows that the closer a QSO to the local relation, the slower the growth of the galaxy on average.

In (cite: Tripodi2022; tripodi2023b), we investigated the evolutionary path of J2310+1855 and J0100+2802 in detail. For J0100+2802, we found $G_{\rm BH}>G_{\rm gal}$, suggesting that the BH still dominates the process of BH-galaxy growth in this QSO at $z=6.327$[^14]. On the other hand, in QSO J2310+1855 at $z\sim6$, AGN feedback might be slowing down the accretion onto the SMBH, while the host galaxy grows fast (cite: Tripodi2022; bischetti2022). One of the likely causes of the slow-down of the SMBH accretion is radiatively driven AGN winds that impact on the accreting matter, providing enough momentum to stop further accretion, and which can further propagate outward on the scale of the host galaxy. In J2310+1855, the SMBH accretion may be limited by the ionized wind traced by a CIV broad absorption line (BAL) system (cite: bischetti2022). J2310+18655 also shows evidence of a \[CII\] outflow approximately located in the central kiloparsec, with an outflow mass $M_{\rm out} = 3.5\times 10^8\ \rm M_{\odot}$. Additionally, (cite: shao2022; butler2023) detected molecular outflows traced by OH and OH+. QSO J231-20, which shows a galaxy growth similar to J2310+1855, is also a BAL QSO (cite: bischetti2022). Additionally, evidence of high-velocity \[CII\] emission wings and/or OH absorption wings indicating powerful and fast outflows was found in J2054-0005 (cite: salak2023), J1148+5251 (cite: maiolino2012; cicone2015), and tentatively in J1319+0950 (cite: herrera-camus2019). For all of these QSOs, the angles of the $G_{\rm BH}-G_{\rm gal}$ relation are $\lesssim 45^\circ$. Therefore, the onset of the symbiotic or galaxy dominated regime may be linked to a phase of strong feedback that hampers the BH growth. Three QSOs still experience a BH-dominated growth: J0100+2802, J1342+0928, and J183+05. J0100+2802 and J1342+0928, both belonging to the HYPERION sample, have the highest and lowest BH mass in our sample, respectively. Given that the locally observed SMBH masses do not exceed $10^{11}\ \rm M_\odot$ and that the BH of J0100+2802 is the most massive observed at $z>6$ with already $10^{10}\ \rm M_\odot$, a substantial BH growth is an unlikely prospect. BH-dominated growth therefore is indeed a peculiar scenario for J0100+2802. Conversely, it is likely that J1342+0928 is in the process of strong BH growth given its low BH mass. Interestingly, J183+05 is closest to the local relation. Both in J0100+2802 and J183+05, high-velocity wings were detected in \[CII\] and OH, respectively (cite: tripodi2023c; butler2023). The outflows here might also be related to the fact that both QSOs may be approaching a phase of symbiotic growth. For the uncertainties on $M_{\rm BH}, M_{\rm dyn}$, and SFR quoted above, both J0100+2802 and J183+05 would fall in the symbiotic-growth regime on average. The other QSOs in our sample would keep the same classification as reported in Tab. [\[tab:c4-prop\]](#tab:c4-prop).

To summarize, our study suggests that QSOs at $z\gtrsim 6$ experience a phase of intense galaxy growth. This may be connected to the emergence of strong outflows that are able to regulate the BH growth. On the $M_{\rm BH}-M_{\rm dyn}$ plane, high-$z$ QSOs appear to converge toward the massive end of the local relation. This suggests that they are viable and plausible candidate progenitors of the massive galaxies found in the local Universe.

# Summary

We exploited newly acquired and archival ALMA observations to perform an analysis of the cold-dust SED in a sample of ten QSOs at $z\gtrsim 6$, deriving the dust properties and SFR with the smallest statistical uncertainty ($<10-25\%$). We also investigated the molecular gas in our sample in order to estimate the GDR. The final goal was to discuss the evolutionary path of the QSOs in our sample by assessing whether high-$z$ QSOs can be considered the progenitors of local massive galaxies. We divided our sample into two subsamples depending on whether they belonged to the HYPERION sample. The HYPERION QSOs experienced an intense and rapid SMBH growth, and we therefore aimed to examine whether they showed similar or distinct properties in terms of host galaxies compared to other QSOs at the same redshift. We summarize our main findings below.

- The analysis of the CO(6-5) and CO(7-6) emission lines in select QSOs provides insights into their molecular gas masses, which average around $10^{10}\ \rm M_\odot$, which is consistent with typical values for high-redshift QSOs. Our findings support the picture in which high-$z$ QSO host galaxies have large gas reservoirs that constitute the fuel for star formation. The combination of this information with the SFR and dust masses estimated from the analysis of the SEDs can provide crucial insights into the galaxy assembly and evolution.

- Proprietary and archival ALMA observations in bands 8 and 9 enabled precise constraints on the dust properties and SFR of four QSOs at $z>6$ for the first time. Taking advantage of these new results, we developed a mean cold-dust SED by combining all the observations available at $50\mu m<\lambda<500\mu m$ for the ten QSOs in our sample. This offered a comprehensive view of the dust properties in the QSO hosts.

- Our investigation of the redshift distribution of dust temperatures revealed a large scatter in dust temperature between QSOs and typical star-forming galaxies at fixed redshift, but indicated a general trend of increasing $T_{\rm dust}$ with redshift, as theoretically expected. Considering the whole population of galaxies at $0<z<7$, our best-fitting $T_{\rm dust}-z$ relation is of the form $T_{\rm dust}\propto (1+z)^{0.7\pm 0.1}$, which is steeper than expected from theory ($T_{\rm dust}\propto (1+z)^{0.4}$ (see (cite: sommovigo2022)). This implies that the variation in $T_{\rm dust}$ in different sources has non-negligible dependences on other physical properties, such as optical depth and metallicity. When we focused on QSOs alone, we recovered the theoretical results with $T_{\rm dust}\propto (1+z)^{0.35\pm 0.04}$.

- Investigating the variation in the dust emissivity index $\beta$ with redshift, we found that it is approximately constant with $z$ ($\beta\sim 1.6$), indicating that all sources share similar dust properties. Two QSOs, J0100+2802 and J036+03, show $\beta>2$, suggesting that they may have peculiar dust properties. The analysis of the dust extinction curves in the rest-frame UV-optical could provide complementary information on the properties of dust in these QSOs.

- All the QSOs in our sample are highly star forming, with an ${\rm SFR}\sim 200-2000\ \rm M_\odot ~yr^{-1}$. Compared with local QSOs, the SFR is higher at $z>2$ by $\sim 2$ orders of magnitudes on average, ranging from few hundred to thousands of $\rm M_\odot ~yr^{-1}$. This supports the well-known concept that high-$z$ QSOs are hosted in highly star-forming galaxies. The dust masses are higher at high $z$ as well, by $\lesssim 2$ order of magnitudes on average. As a preliminary result, the dust masses of the HYPERION QSOs in our sample are lower on average (about a factor of 2) than the other QSOs in our sample.

- The observed high SFR in our sample yields high SFEs, and thus, very low gas depletion timescales ($\tau_{\rm dep}\sim 10^{-2}$ Gyr). The latter is connected to the observed high dust temperatures and indicates that the nature of our sample’s host galaxies is indeed star bursting. In order to derive firm conclusions on the SFE in high-z QSOs, we need a systematic study of the SFE in a larger sample that includes QSOs at lower luminosities.

- We found a large scatter of the GDR in our sample, from 30 to 250. The lowest measured GDRs are due to massive reservoirs of dust, $M_{\rm dust} \sim 5-6 \times 10^8\ \rm M_\odot$, which pose challenges to theoretical modeling of dust formation. Interestingly, the HYPERION QSOs show the highest GDRs in our sample owing to their lower dust masses, $M_{\rm dust} \sim 2-9 \times 10^7\ \rm M_\odot$, whereas their $H_2$ gas reservoirs are in line with those previously found in QSOs at the same z ($M_{\rm H_2}\sim 10^{10}\ \rm M_\odot$).

- We were able to investigate and discuss the evolutionary path of our sample of ten QSOs with an accurate determination of the dust properties and SFR. Our study suggests that QSOs at $z\gtrsim 6$ experience a phase of rapid galaxy growth. This may be connected to the emergence of strong outflows that are able to regulate the BH growth. BALs were indeed detected in J2310+1855 and J231-20 (cite: bischetti2022), and evidence of powerful and fast outflows was found in J2310+1855 (cite: Tripodi2022; shao2022; butler2023), J2054-0005 (cite: salak2023), J1148+5251 (cite: maiolino2012; cicone2015), and tentatively in J1319+0950 (cite: herrera-camus2019). On the $M_{\rm BH}-M_{\rm dyn}$ plane, high-$z$ QSOs appear to be converging toward the massive end of the local relation. This makes high-$z$ QSOs viable and plausible candidate progenitors of massive galaxies found in the local Universe. Interestingly, the average pathway pursued by high-$z$ QSOs to end up as local massive galaxies involves an intense BH growth, which is supported by the upward offset from the local $M_{\rm BH}-M_{\rm dyn}$ relation, followed by a substantial growth of the galaxy. This is in contrast with the picture of the formation of massive local galaxies via symbiotic growth. Our scenario is further supported by the evidence of a stellar bulge in J2310+1855 (cite: tripodi2023a), which indicates that the structure of QSOs at $z\sim 6$ is surprisingly similar to that typical of local massive galaxies.

*Acknowledgments.* We thank the referee for providing insightful comments that helped the clarity and robustness of this work. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01633.S, 2015.1.00399.S, 2018.1.01790.S, 2021.2.00151.S, 2017.1.01472.S, 2018.1.01188.S, 2021.1.00934.S, 2021.2.00064.S, 2018.1.01289.S, 2019.1.00672.S, 2017.1.01195.S, 2016.1.01063.S. ALMA is a partnership of ESO (representing its member states), NFS (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The project leading to this publication has received support from ORP, that is funded by the European Union’s Horizon 2020 research and innovation programme under grant agreement No 101004719 \[ORP\]. RT acknowledges financial support from the University of Trieste. RT, CF, FF, MB, EP acknowledge support from PRIN MIUR project “Black Hole winds and the Baryon Life Cycle of Galaxies: the stone-guest at the galaxy evolution supper”, contract #2017PH3WAT. C.-C.C. acknowledges support from the National Science and Technology Council of Taiwan (NSTC 111-2112M-001-045-MY3), as well as Academia Sinica through the Career Development Award (AS-CDA-112-M02). EP, LZ and CF acknowledge financial support from the Bando Ricerca Fondamentale INAF 2022 Large Grant "Toward a holistic view of the Titans: multi-band observations of $z>6$ QSOs powered by greedy supermassive black-holes". RM acknowledges ERC Advanced Grant 695671 QUENCH, and support from the UK Science and Technology Facilities Council (STFC). RM also acknowledges funding from a research professorship from the Royal Society. SC acknowledges support from the European Union (ERC, WINGS,101040227). *Facilities:* ALMA. *Software:* astropy (cite: astropy2022), Matplotlib (cite: matplotlib2007), SciPy (cite: scipy2023), CASA (v5.1.1-5, (cite: casa2022)).

197 natexlab

(ref: algera2023) Algera, H. S. B., Inami, H., Oesch, P. A., et al. 2023, MNRAS, 518, 6142

(ref: astropy2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: banados2018) Bañados, E., Venemans, B. P., Mazzucchelli, C., et al. 2018, Nature, 553, 473

(ref: bakx2021) Bakx, T. J. L. C., Sommovigo, L., Carniani, S., et al. 2021, MNRAS, 508, L58

(ref: bakx2020) Bakx, T. J. L. C., Tamura, Y., Hashimoto, T., et al. 2020, MNRAS, 493, 4294

(ref: beelen+2006) Beelen, A., Cox, P., Benford, D. J., et al. 2006, ApJ, 642, 694

(ref: beeston2018) Beeston, R. A., Wright, A. H., Maddox, S., et al. 2018, MNRAS, 479, 1077

(ref: behrens2018) Behrens, C., Pallottini, A., Ferrara, A., Gallerani, S., & Vallini, L. 2018, MNRAS, 477, 552

(ref: bendo2023) Bendo, G. J., Urquhart, S. A., Serjeant, S., et al. 2023, MNRAS, 522, 2995

(ref: bertoldi2003a) Bertoldi, F., Carilli, C. L., Cox, P., et al. 2003, A&A, 406, L55

(ref: bethermin2020) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2

(ref: birkin2021) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021, MNRAS, 501, 3926

(ref: bischetti2022) Bischetti, M., Feruglio, C., D’Odorico, V., et al. 2022, Nature, 605, 244

(ref: bischetti2021) Bischetti, M., Feruglio, C., Piconcelli, E., et al. 2021, A&A, 645, A33

(ref: bouwens2022) Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ, 931, 160

(ref: bradford2009) Bradford, C. M., Aguirre, J. E., Aikin, R., et al. 2009, ApJ, 705, 112

(ref: butler2023) Butler, K. M., van der Werf, P. P., Topkaras, T., et al. 2023, ApJ, 944, 134

(ref: calabro2024) Calabrò, A., Pentericci, L., Santini, P., et al. 2024, accepted for publication in A&A, arXiv:2402.17829

(ref: calura2014) Calura, F., Gilli, R., Vignali, C., et al. 2014, MNRAS, 438, 2765

(ref: carilli2013) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: carniani2019) Carniani, S., Gallerani, S., Vallini, L., et al. 2019, MNRAS, 489, 3939

(ref: casa2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: chambers2016) Chambers, K. C., Magnier, E. A., Metcalfe, N., et al. 2016, arXiv e-prints, arXiv:1612.05560

(ref: cicone2015) Cicone, C., Maiolino, R., Gallerani, S., et al. 2015, A&A, 574, A14

(ref: clements2018) Clements, D. L., Pearson, C., Farrah, D., et al. 2018, MNRAS, 475, 2097

(ref: compiegne2011) Compiègne, M., Verstraete, L., Jones, A., et al. 2011, A&A, 525, A103

(ref: cooper2022) Cooper, O. R., Casey, C. M., Zavala, J. A., et al. 2022, ApJ, 930, 32

(ref: dacunha2010) da Cunha, E., Eminian, C., Charlot, S., & Blaizot, J. 2010, MNRAS, 403, 1894

(ref: dacunha2013) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13

(ref: dacunha2021) da Cunha, E., Hodge, J. A., Casey, C. M., et al. 2021, ApJ, 919, 30

(ref: daddi2010) Daddi, E., Elbaz, D., Walter, F., et al. 2010, ApJL, 714, L118

(ref: damato2020) D’Amato, Q., Gilli, R., Prandoni, I., et al. 2020, A&A, 641, L6

(ref: davies2011) Davies, R., Förster Schreiber, N. M., Cresci, G., et al. 2011, ApJ, 741, 69

(ref: derosa2014) De Rosa, G., Venemans, B. P., Decarli, R., et al. 2014, ApJ, 790, 145

(ref: decarli2023) Decarli, R., Pensabene, A., Diaz-Santos, T., et al. 2023, A&A, 673, A157

(ref: decarli2022) Decarli, R., Pensabene, A., Venemans, B., et al. 2022, A&A, 662, A60

(ref: decarli2017) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457

(ref: decarli2018) Decarli, R., Walter, F., Venemans, B. P., et al. 2018, ApJ, 854, 97

(ref: dimascia2022) Di Mascia, F., Carniani, S., Gallerani, S., et al. 2023, MNRAS, 518, 3667

(ref: dimascia2021) Di Mascia, F., Gallerani, S., Behrens, C., et al. 2021, MNRAS, 503, 2349

(ref: ding2023) Ding, X., Onoue, M., Silverman, J. D., et al. 2023, Nature, 621, 51

(ref: dodorico2023) D’Odorico, V., Bañados, E., Becker, G. D., et al. 2023, MNRAS, 523, 1399

(ref: dodorico2018) D’Odorico, V., Feruglio, C., Ferrara, A., et al. 2018, ApJL, 863, L29

(ref: draine2007) Draine, B. T., Dale, D. A., Bendo, G., et al. 2007, ApJ, 663, 866

(ref: driver2018) Driver, S. P., Andrews, S. K., da Cunha, E., et al. 2018, MNRAS, 475, 2891

(ref: dudzevi2020) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828

(ref: dunne2011) Dunne, L., Gomez, H. L., da Cunha, E., et al. 2011, MNRAS, 417, 1510

(ref: duras2017) Duras, F., Bongiorno, A., Piconcelli, E., et al. 2017, A&A, 604, A67

(ref: eilers2022) Eilers, A.-C., Simcoe, R. A., Yue, M., et al. 2023, ApJ, 950, 68

(ref: faisst2017) Faisst, A. L., Capak, P. L., Yan, L., et al. 2017, ApJ, 847, 21

(ref: faisst2020) Faisst, A. L., Fudamoto, Y., Oesch, P. A., et al. 2020, MNRAS, 498, 4192

(ref: fan2022) Fan, X., Bañados, E., & Simcoe, R. A. 2023, ARA&A, 61, 373

(ref: fan2003) Fan, X., Strauss, M. A., Schneider, D. P., et al. 2003, AJ, 125, 1649

(ref: feruglio2018) Feruglio, C., Fiore, F., Carniani, S., et al. 2018, A&A, 619, A39

(ref: feruglio2023) Feruglio, C., Maio, U., Tripodi, R., et al. 2023, ApJL, 954, L10

(ref: foreman2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: castillo2024) Frias Castillo, M., Rybak, M., Hodge, J., et al. 2024, A&A, 683, A211

(ref: gallerani2014) Gallerani, S., Ferrara, A., Neri, R., & Maiolino, R. 2014, MNRAS, 445, 2848

(ref: galliano2018) Galliano, F., Galametz, M., & Jones, A. P. 2018, ARA&A, 56, 673

(ref: genzel2010) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091

(ref: scipy2023) Gommers, R., Virtanen, P., Burovski, E., et al. 2023, scipy/scipy: SciPy 1.10.1, Zenodo

(ref: greiner2021) Greiner, J., Bolmer, J., Yates, R. M., et al. 2021, A&A, 654, A79

(ref: harikane2020) Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ, 896, 93

(ref: harikane2023) Harikane, Y., Zhang, Y., Nakajima, K., et al. 2023, ApJ, 959, 39

(ref: hashimoto2019) Hashimoto, T., Inoue, A. K., Tamura, Y., et al. 2019, PASJ, 71, 109

(ref: herrera-camus2020) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2020, A&A, 633, L4

(ref: herrera-camus2019) Herrera-Camus, R., Tacconi, L., Genzel, R., et al. 2019, ApJ, 871, 37

(ref: hines2006) Hines, D. C., Krause, O., Rieke, G. H., et al. 2006, ApJL, 641, L85

(ref: hirashita2014) Hirashita, H., Ferrara, A., Dayal, P., & Ouchi, M. 2014, MNRAS, 443, 1704

(ref: hjorth2014) Hjorth, J., Gall, C., & Michałowski, M. J. 2014, ApJL, 782, L23

(ref: hu2022) Hu, H., Inayoshi, K., Haiman, Z., et al. 2022, ApJ, 935, 140

(ref: matplotlib2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90

(ref: inayoshi2022) Inayoshi, K., Nakatani, R., Toyouchi, D., et al. 2022, ApJ, 927, 237

(ref: inayoshi2020) Inayoshi, K., Visbal, E., & Haiman, Z. 2020, ARA&A, 58, 27

(ref: iwamuro2004) Iwamuro, F., Kimura, M., Eto, S., et al. 2004, ApJ, 614, 69

(ref: izumi2019) Izumi, T., Onoue, M., Matsuoka, Y., et al. 2019, PASJ, 71, 111

(ref: izumi2018) Izumi, T., Onoue, M., Shirakata, H., et al. 2018, PASJ, 70, 36

(ref: jiang2008) Jiang, L., Fan, X., Annis, J., et al. 2008, AJ, 135, 1057

(ref: jiang2006) Jiang, L., Fan, X., Hines, D. C., et al. 2006, AJ, 132, 2127

(ref: jiang2016) Jiang, L., McGreer, I. D., Fan, X., et al. 2016, ApJ, 833, 222

(ref: kashikawa2015) Kashikawa, N., Ishizaki, Y., Willott, C. J., et al. 2015, ApJ, 798, 28

(ref: kennicutt1998) Kennicutt, Robert C., J. 1998, ARA&A, 36, 189

(ref: kennicutt2012) Kennicutt, R. C. & Evans, N. J. 2012, ARA&A, 50, 531

(ref: kimball2015) Kimball, A. E., Lacy, M., Lonsdale, C. J., & Macquart, J. P. 2015, MNRAS, 452, 88

(ref: kormendy2013) Kormendy, J. & Ho, L. C. 2013, Annual Review of Astronomy and Astrophysics, 51, 511

(ref: koss21) Koss, M. J., Strittmatter, B., Lamperti, I., et al. 2021, ApJS, 252, 29

(ref: kroupa2003) Kroupa, P. & Weidner, C. 2003, ApJ, 598, 1076

(ref: lamperti2019) Lamperti, I., Saintonge, A., De Looze, I., et al. 2019, MNRAS, 489, 4389

(ref: laporte2017) Laporte, N., Ellis, R. S., Boone, F., et al. 2017, ApJL, 837, L21

(ref: leipski2013) Leipski, C., Meisenheimer, K., Walter, F., et al. 2013, ApJ, 772, 103

(ref: Leipski2014) Leipski, C., Meisenheimer, K., Walter, F., et al. 2014, ApJ, 785, 154

(ref: leroy2011) Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ, 737, 12

(ref: li2020) Li, J., Wang, R., Riechers, D., et al. 2020, ApJ, 889, 162

(ref: li2008) Li, Y., Hopkins, P. F., Hernquist, L., et al. 2008, ApJ, 678, 41

(ref: liao2023) Liao, C.-L., Chen, C.-C., Wang, W.-H., et al. 2024, ApJ, 961, 226

(ref: madden2020) Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A, 643, A141

(ref: maiolino2012) Maiolino, R., Gallerani, S., Neri, R., et al. 2012, MNRAS, 425, L66

(ref: maiolino2023c) Maiolino, R., Scholtz, J., Curtis-Lake, E., et al. 2023, submitted to A&A, arXiv:2308.01230

(ref: maiolino2023) Maiolino, R., Scholtz, J., Witstok, J., et al. 2024, Nature, 627, 59

(ref: marconi2004) Marconi, A., Risaliti, G., Gilli, R., et al. 2004, MNRAS, 351, 169

(ref: marshall2020) Marshall, M. A., Mechtley, M., Windhorst, R. A., et al. 2020, ApJ, 900, 21

(ref: mazzucchelli2017) Mazzucchelli, C., Bañados, E., Venemans, B. P., et al. 2017, ApJ, 849, 91

(ref: mazzucchelli2023) Mazzucchelli, C., Bischetti, M., D’Odorico, V., et al. 2023, A&A, 676, A71

(ref: mckay2023) McKay, S. J., Barger, A. J., Cowie, L. L., Bauer, F. E., & Rosenthal, M. J. N. 2023, ApJ, 951, 48

(ref: mcmullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: metchtley2012) Mechtley, M., Windhorst, R. A., Ryan, R. E., et al. 2012, ApJL, 756, L38

(ref: miettinen2017) Miettinen, O., Delvecchio, I., Smolčić, V., et al. 2017, A&A, 606, A17

(ref: mortlock2008) Mortlock, D. J., Patel, M., Warren, S. J., et al. 2008, arXiv e-prints, arXiv:0810.3859

(ref: mortlock2011) Mortlock, D. J., Warren, S. J., Venemans, B. P., et al. 2011, Nature, 474, 616

(ref: neeleman2019) Neeleman, M., Bañados, E., Walter, F., et al. 2019, ApJ, 882, 10

(ref: neeleman2021) Neeleman, M., Novak, M., Venemans, B. P., et al. 2021, ApJ, 911, 141

(ref: novak2019) Novak, M., Bañados, E., Decarli, R., et al. 2019, ApJ, 881, 63

(ref: pacucci2024) Pacucci, F. & Loeb, A. 2024, ApJ, 964, 154

(ref: pacucci2023) Pacucci, F., Nguyen, B., Carniani, S., Maiolino, R., & Fan, X. 2023, ApJL, 957, L3

(ref: papado2001) Papadopoulos, P., Ivison, R., Carilli, C., & Lewis, G. 2001, Nature, 409, 58

(ref: parente2023) Parente, M., Ragone-Figueroa, C., Granato, G. L., & Lapi, A. 2023, MNRAS, 521, 6105

(ref: pensabene2020) Pensabene, A., Carniani, S., Perna, M., et al. 2020, A&A, 637, A84

(ref: Pensabene2021) Pensabene, A., Decarli, R., Bañados, E., et al. 2021, A&A, 652, A66

(ref: petric2015) Petric, A. O., Ho, L. C., Flagey, N. J. M., & Scoville, N. Z. 2015, ApJS, 219, 22

(ref: planck2018) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6

(ref: pons2020) Pons, E., McMahon, R. G., Banerji, M., & Reed, S. L. 2020, MNRAS, 491, 3884

(ref: pozzi2020) Pozzi, F., Calura, F., Zamorani, G., et al. 2020, MNRAS, 491, 5073

(ref: reed2019) Reed, S. L., Banerji, M., Becker, G. D., et al. 2019, MNRAS, 487, 1874

(ref: reed2017) Reed, S. L., McMahon, R. G., Martini, P., et al. 2017, MNRAS, 468, 4702

(ref: reines2015) Reines, A. E. & Volonteri, M. 2015, ApJ, 813, 82

(ref: reuter2020) Reuter, C., Vieira, J. D., Spilker, J. S., et al. 2020, ApJ, 902, 78

(ref: riechers2009) Riechers, D. A., Walter, F., Carilli, C. L., & Lewis, G. F. 2009, ApJ, 690, 463

(ref: rosario18) Rosario, D. J., Burtscher, L., Davies, R. I., et al. 2018, MNRAS, 473, 5658

(ref: saintonge2017) Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22

(ref: saintonge2011) Saintonge, A., Kauffmann, G., Wang, J., et al. 2011, MNRAS, 415, 61

(ref: saintonge2013) Saintonge, A., Lutz, D., Genzel, R., et al. 2013, ApJ, 778, 2

(ref: salak2023) Salak, D., Hashimoto, T., Inoue, A. K., et al. 2024, ApJ, 962, 1

(ref: salome2023) Salomé, Q., Krongold, Y., Longinotti, A. L., et al. 2023, MNRAS, 524, 3130

(ref: salpeter1955) Salpeter, E. E. 1955, ApJ, 121, 161

(ref: sanders2003) Sanders, D. B., Mazzarella, J. M., Kim, D. C., Surace, J. A., & Soifer, B. T. 2003, AJ, 126, 1607

(ref: santini2023) Santini, P., Fontana, A., Castellano, M., et al. 2023, ApJL, 942, L27

(ref: santini2014) Santini, P., Maiolino, R., Magnelli, B., et al. 2014, A&A, 562, A30

(ref: sargent2014) Sargent, M. T., Daddi, E., Béthermin, M., et al. 2014, ApJ, 793, 19

(ref: schneider2015) Schneider, R., Bianchi, S., Valiante, R., Risaliti, G., & Salvadori, S. 2015, A&A, 579, A60

(ref: schreiber2018) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30

(ref: scoville2023) Scoville, N., Faisst, A., Weaver, J., et al. 2023, ApJ, 943, 82

(ref: shangguan20b) Shangguan, J., Ho, L. C., Bauer, F. E., Wang, R., & Treister, E. 2020a, ApJ, 899, 112

(ref: shangguan20a) Shangguan, J., Ho, L. C., Bauer, F. E., Wang, R., & Treister, E. 2020b, ApJS, 247, 15

(ref: shao2019) Shao, Y., Wang, R., Carilli, C. L., et al. 2019, ApJ, 876, 99

(ref: shao2017) Shao, Y., Wang, R., Jones, G. C., et al. 2017, ApJ, 845, 138

(ref: shao2022) Shao, Y., Wang, R., Weiss, A., et al. 2022, A&A, 668, A121

(ref: solomon2005) Solomon, P. M. & Vanden Bout, P. A. 2005, ARA&A, 43, 677

(ref: sommovigo2020) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2020, MNRAS, 497, 956

(ref: sommovigo2022) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022, MNRAS, 513, 3122

(ref: speagle2014) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15

(ref: stefan2015) Stefan, I. I., Carilli, C. L., Wagg, J., et al. 2015, Monthly Notices of the Royal Astronomical Society, 451, 1713

(ref: stone2023) Stone, M. A., Lyu, J., Rieke, G. H., Alberts, S., & Hainline, K. N. 2024, ApJ, 964, 90

(ref: tacconi2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: tacconi2020) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157

(ref: toyouchi2021) Toyouchi, D., Inayoshi, K., Hosokawa, T., & Kuiper, R. 2021, ApJ, 907, 74

(ref: trakhtenbrot2017) Trakhtenbrot, B., Lira, P., Netzer, H., et al. 2017, ApJ, 836, 8

(ref: trinca2022) Trinca, A., Schneider, R., Valiante, R., et al. 2022, MNRAS, 511, 616

(ref: tripodi2023b) Tripodi, R., Feruglio, C., Kemper, F., et al. 2023a, ApJL, 946, L45

(ref: Tripodi2022) Tripodi, R., Feruglio, C., Fiore, F., et al. 2022, A&A, 665, A107

(ref: tripodi2023a) Tripodi, R., Lelli, F., Feruglio, C., et al. 2023b, A&A, 671, A44

(ref: tripodi2023c) Tripodi, R., Scholtz, J., Maiolino, R., et al. 2024, A&A, 682, A54

(ref: tsukui2023) Tsukui, T., Wisnioski, E., Krumholz, M. R., & Battisti, A. 2023, MNRAS, 523, 4654

(ref: ubler2023) Übler, H., Maiolino, R., Curtis-Lake, E., et al. 2023, A&A, 677, A145

(ref: uzgil2016) Uzgil, B. D., Bradford, C. M., Hailey-Dunsheath, S., Maloney, P. R., & Aguirre, J. E. 2016, ApJ, 832, 209

(ref: valiante2011) Valiante, R., Schneider, R., Salvadori, S., & Bianchi, S. 2011, MNRAS, 416, 1916

(ref: vallini2018) Vallini, L., Pallottini, A., Ferrara, A., et al. 2018, MNRAS, 473, 271

(ref: vallini2024) Vallini, L., Witstok, J., Sommovigo, L., et al. 2024, MNRAS, 527, 10

(ref: venemans2015) Venemans, B. P., Bañados, E., Decarli, R., et al. 2015, ApJL, 801, L11

(ref: venemans2017a) Venemans, B. P., Walter, F., Decarli, R., et al. 2017, ApJ, 837, 146

(ref: venemans2020) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130

(ref: venemans2016) Venemans, B. P., Walter, F., Zschaechner, L., et al. 2016, ApJ, 816, 37

(ref: viero2022) Viero, M. P., Sun, G., Chung, D. T., Moncelsi, L., & Condon, S. S. 2022, MNRAS, 516, L30

(ref: vietri2018) Vietri, G., Piconcelli, E., Bischetti, M., et al. 2018, A&A, 617, A81

(ref: volonteri2012) Volonteri, M. 2012, Science, 337, 544

(ref: walter2003) Walter, F., Bertoldi, F., Carilli, C., et al. 2003, Nature, 424, 406

(ref: walter2022) Walter, F., Neeleman, M., Decarli, R., et al. 2022, ApJ, 927, 21

(ref: wang2019) Wang, F., Wang, R., Fan, X., et al. 2019a, ApJ, 880, 2

(ref: wang2021) Wang, F., Yang, J., Fan, X., et al. 2021, ApJL, 907, L1

(ref: wang2019b) Wang, F., Yang, J., Fan, X., et al. 2019b, ApJ, 884, 30

(ref: wang2024) Wang, F., Yang, J., Hennawi, J. F., et al. 2024, ApJL, 962, L11

(ref: wang2011) Wang, R., Wagg, J., Carilli, C. L., et al. 2011, AJ, 142, 101

(ref: wang2013) Wang, R., Wagg, J., Carilli, C. L., et al. 2013, ApJ, 773, 44

(ref: weiss2007) Weiß, A., Downes, D., Neri, R., et al. 2007, A&A, 467, 955

(ref: willott2015) Willott, C. J., Bergeron, J., & Omont, A. 2015, ApJ, 801, 123

(ref: willott2017) Willott, C. J., Bergeron, J., & Omont, A. 2017, ApJ, 850, 108

(ref: willott2013) Willott, C. J., Omont, A., & Bergeron, J. 2013, ApJ, 770, 13

(ref: witstok2023) Witstok, J., Jones, G. C., Maiolino, R., Smit, R., & Schneider, R. 2023, MNRAS, 523, 3119

(ref: witstok2022) Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS, 515, 1751

(ref: wu2015) Wu, X.-B., Wang, F., Fan, X., et al. 2015, Nature, 518, 512

(ref: Yang2019) Yang, J., Venemans, B., Wang, F., et al. 2019, ApJ, 880, 153

(ref: yang2023) Yang, J., Wang, F., Fan, X., et al. 2023, ApJL, 951, L5

(ref: yue2023) Yue, M., Eilers, A.-C., Simcoe, R. A., et al. 2024, ApJ, 966, 176

(ref: zanella2018) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976

(ref: zappacosta2023) Zappacosta, L., Piconcelli, E., Fiore, F., et al. 2023, A&A, 678, A201

(ref: zhang2023b) Zhang, H., Behroozi, P., Volonteri, M., et al. 2023a, MNRAS, 523, L69

(ref: zhang2023c) Zhang, Y., Ouchi, M., Gebhardt, K., et al. 2023b, ApJ, 948, 103

# Individual objects

## SDSS J010013.02+280225.8 (HYPERION)

For QSO SDSS J010013.02+280225.8 (hereafter J0100+2802) at $z_{\rm [CII]}=6.327$ (cite: wang2019), (cite: wu2015) estimated a bolometric luminosity of $L_{\rm bol}=4.29\times 10^{14}\rm \ L_{\odot}$ and a BH mass of $M_{\rm BH}=1.24\times10^{10}\ \rm M_{\odot}$, making it the most optically luminous QSO with the most massive SMBH known at $z>6$. Both measurements have been recently confirmed by JWST (cite: eilers2022). (cite: wang2019) performed a multi-frequency analysis of the dust SED, but they could not obtain a precise determination of the dust properties, concluding that J0100+28 has either a high dust emissivity ($\beta \gtrsim 2$) or a high dust temperature ($T_{\rm dust} \gtrsim 60$ K), or a combination of thereof.

## PSO J036.5078+03.0498 (HYPERION)

PSO J036.5078+03.0498 (cite: venemans2015) at $z=6.5405$ was observed for the first time in the Pan-STARRS1 survey (cite: venemans2015), and it has a BH mass of $M_{\rm BH, MgII}=(2.69-3.09) \times 10^{9}\ \rm M_\odot$ from the analysis of MgII emission line and a bolometric luminosity of $L_{\rm bol}=(2.13-3.16)\times 10^{47}$ erg s$^{-1}$ (cite: zappacosta2023; mazzucchelli2023). (cite: decarli2022) studied the CO(6-5), CO(7-6) and \[CI\]$_{2-1}$ emission lines of this QSO host with NOEMA observations, and they found $L_{\rm CO(6-5)}=12.7\times 10^9\ \rm K ~km ~s^{-1} ~pc^2$, $L_{\rm CO(7-6)}=10.7\times 10^9\ \rm K ~km ~s^{-1} ~pc^2$ and $L_{\rm [CI]}=5.7\times 10^9\ \rm K ~km ~s^{-1} ~pc^2$, implying a molecular gas mass of $M_{\rm H2, CO}=5.0^{+0.5}_{-0.6} \times 10^{10}\ \rm M_\odot$ and $M_{\rm H2, [CI]}=7.1^{+1.6}_{-1.4} \times 10^{10}\ \rm M_\odot$. The \[CII\] emission shows ordered motion, with a clear and regular velocity gradient in the moment-1 map and $v_{\rm rot}/\sigma>3$, and it has a $L_{\rm [CII]}=3.38\times 10^9\ \rm L_\odot$ and a size of $\sim 2.4\times 1.6$ kpc$^2$ (cite: venemans2020; neeleman2021). From the modeling of the velocity rotation they estimated a dynamical mass of $M_{\rm dyn}=2.9^{+1.1}_{-0.7}\times 10^{10}\ \rm M_\odot$, and from the \[CII\] underlying continuum emission they derived a gas mass of $M_{\rm H2, cont}=2.8^{+15}_{-1.1} \times 10^{10}\ \rm M_\odot$, assuming a gas-to-dust ratio of 100 and a molecular-to-total gas mass fraction of 0.75. (cite: greiner2021) did not find any companion brighter than $M_{1450}(AB)<-26$ mag within 0.1-3.3$h^{-1}$ comoving Mpc search radius, using the simultaneous seven-channel Gamma-ray Burst Optical/Near-infrared Detector, confirming the results of (cite: venemans2020), who did not detect any companion for this source using ALMA observation of \[CII\] emission.

## VDES J022426.54-471129.4 (HYPERION)

VDESJ022426.54-471129.4 (cite: reed2017) at $z=6.5222$, firstly discovered by (cite: reed2017), is one of the most X-ray luminous QSOs at $z>5.5$ and the most X-ray luminous QSO at $z>6.5$ (cite: pons2020; zappacosta2023). It belongs to the HYPERION sample, the XQR-30 sample and the ASPIRE survey (cite: yang2023). It has a bolometric luminosity of $L_{\rm bol}=3.47\times 10^{47}$ erg s$^{-1}$, and BH mass of $M_{\rm BH, MgII}=(1.30-2.29) \times 10^{9}\ \rm M_\odot$ from the analysis of MgII emission line (cite: reed2019; wang2021; zappacosta2023; mazzucchelli2023) and $M_{\rm BH, H\beta}=2.15 \times 10^{9}\ \rm M_\odot$, from the analysis of H$\beta$ emission line (cite: yang2023). It has the most extreme broad and blueshifted \[OIII\] lines observed to date, even compared to observations of lower-redshift QSOs, with a velocity shift of $-1690$ km s$^{-1}$ relative to the narrow \[OIII\], suggesting powerful ionized outflows (cite: yang2023).

## PSO J231.6576-20.8335 (HYPERION)

PSO J231.6576-20.8335 (hereafter J231-20) at $z=6.587$ has been discovered using the Pan-STARRS1 survey (cite: mazzucchelli2017), and it is one of the brightest objects at $z>6.5$. (cite: decarli2017) detected a \[CII\]-bright nearby companion at $<$10 kpc separation. (cite: Pensabene2021) performed an extensive study of both the QSO and its companion, detecting \[NII\], CO(7-6), CO(10-9) emission lines, two OH transitions and their underlying continuum in both of them. Additionally, the CO(15-14), CO(16-15) and three transitions of H$_2$O emission line have been detected for the central QSO. Analyzing the cold-dust SED of both the QSO and its companion, they derived $T_{\rm dust}=54$ K, $M_{\rm dust}=5.1\times 10^8\ \rm M_\odot$ and $T_{\rm dust}=35-46$ K, $M_{\rm dust}=(2.3-3.4)\times 10^8\ \rm M_\odot$, respectively. The estimates on the dust temperature suffer of high uncertainties given that they lack of high-frequency observations to probe the peak of the SED. (cite: neeleman2021) found a dynamical mass $M_{\rm dyn}=1.4\times 10^{10}\ \rm M_\odot$ from the modeling of the velocity rotation curve, and reported a BH mass of $M_{\rm BH} = 4.1\times 10^9\ \rm M_\odot$. Finally, (cite: bischetti2022) classified this as a broad absorption line (BAL) QSO, indicating that J231-20 may be caught in a phase of strong BH feedback.

## ULAS J134208.10+092838.35 (HYPERION)

ULAS J134208.10+092838.35 (hereafter J1342+0928) at $z=7.54$, the most distant QSO known to date, was discovered by (cite: banados2018) who reported an absolute AB magnitude $M_{1450}=-26.8$, bolometric luminosity of $L_{\rm bol}=10^{13}\ \rm L_\odot$, and an SMBH mass of $8\times 10^8\ \rm M_\odot$. It was followed-up with NOEMA resulting in the detection of bright \[CII\] emission and upper limits on several CO lines (cite: venemans2017a). (cite: novak2019) presented ALMA observations of the dust continuum and the ISM of the host galaxy J1342+0928. They well constrained the Rayleigh-Jeans tail of the dust SED, deriving a $M_{\rm dust}=3.5\times 10^7\ \rm M_\odot$ and a SFR$\sim 150 \rm \ M_\odot ~yr^{-1}$, fixing the temperature at 47 K. They also detected many atomic fine structure line, such as \[CII\], \[NII\], \[OIII\], and limits on \[CI\], \[OI\] and multiple CO transitions (with a tentative stack detection).

## SDSS J114816.64+525150.3 (HYPERION)

SDSS J114816.64+525150.3 (hereafter J1148+5251) at $z=6.42$ was discovered by (cite: fan2003) who reported an absolute magnitude of $M_{1450}=-27.82$. It is one of the most studied QSOs at high-$z$. It was observed by Subary Telescope (cite: iwamuro2004), *Spitzer* (cite: jiang2006; hines2006) and *Herschel* (cite: leipski2013), and therefore this allowed a full modeling of the SED of this QSO (cite: li2008; valiante2011; schneider2015; carniani2019). In particular, (cite: schneider2015) derived that the AGN contribution to the dust heating in this QSO can be between 30% and 70%. (cite: gallerani2014) detected an exceptionally strong CO(17–16) line in this QSO with the Plateau de Bure interferometer (PdBI) and performed a detailed analysis of the CO SLED using previously detected lower CO transitions (cite: bertoldi2003a; walter2003; riechers2009).

## SDSS J231038.88+185519.7

QSO SDSS J231038.88+185519.7 (hereafter J2310+1855), first discovered in SDSS (cite: jiang2006; wang2013), is one of the most FIR-luminous QSOs and one of the brightest optical QSOs known at $z\sim 6$, with $L_{\rm bol}=9.3 \times 10^{13}\ \rm L_\odot$. The redshift measured with the QSO rest-frame UV line emission is $z = 6.00\pm 0.03$ (cite: wang2013). (cite: feruglio2018) detected and analyzed the CO(6-5) and \[CII\] emission lines and the submm continuum of J2310+1855, deriving a size of the dense molecular gas of $2.9\pm 0.5$ kpc and of $1.4 \pm 0.2$ kpc for the 91.5 GHz dust continuum and a molecular gas mass of $M({\rm H}_2)=(3.2\pm 0.2)\times 10^{10}\rm M_{\odot}$. They estimated a dynamical mass of $M_{\rm dyn} =  (4.1^{+9.5}_{-0.5})\times 10^{10}\rm M_\odot$, measuring a disk inclination of $i\sim50$ deg. They also inferred the BH mass from the CIV emission line, measured in the X-shooter/VLT spectrum of the QSO, obtaining $M_{\rm BH}=(1.8\pm 0.5)\times 10^9\rm M_\odot$. (cite: shao2019) presented a detailed analysis of the FIR and submm SED and derived a dust temperature of $T\sim 40$ K, a dust mass of $M_{\rm dust}= 1.6\times 10^9\rm M_\odot$, a FIR luminosity $L_{\rm FIR}^{8-1000 \mu m}=1.6\times  10^{13}\ \rm L_{\odot}$, and an SFR$= 2400-2700\ \rm M_\odot yr^{-1}$. (cite: dodorico2018) detected a very metal-poor, proximate damped Lyman $\alpha$ system (DLA) located at z=$5.938646 \pm 0.000007$ in the X-shooter/VLT spectrum of J2310, which was associated with a CO emitting source at $z = 5.939$. This source, called Serenity-18, was detected through its CO(6-5) emission line at \[RA, DEC\] = 23:10:38.44, 18:55:21.95.

## SDSS J205406.49-000514.8

SDSS J205406.49-000514.8 (hereafter J2054-0005) at $z=6.39$ was selected from SDSS stripe 82 with $m_{1450}$ = 20.60, that is, about one magnitude fainter than the objects discovered from the SDSS main survey (cite: jiang2008). (cite: Leipski2014) reported observations in band z, y, J, H, K and with *Herschel*, however they were not able to fully study its SED due to lack of observations in the mm/submm regime. (cite: wang2013) reported a BH mass of $M_{\rm BH} = 8.6 \times 10^8\rm \ M_\odot$, later updated to $M_{\rm BH} = 1.48 \times 10^9\ \rm M_\odot$ using the MgII emission line (cite: neeleman2021). (cite: neeleman2021) studied the rotation curve of J2054-0005 using a high-resolution ALMA observation of the \[CII\] emission of this object, and they determined a lower limit for the dynamical mass of $M_{\rm dyn} > 2.9 \times 10^{10}\ \rm M_\odot$.

## ULAS J131911.29+095051.4

ULAS J131911.29+095051.4 (hereafter J1319+0950) at $z=6.133$ was discovered in the UKIRT Infrared Deep Sky Survey (UKIDSS) with $m_{1450} = 19.65$, which lies in the typical magnitude range of the optically bright $z\sim 6$ quasars selected from the SDSS main survey (cite: mortlock2008). (cite: wang2011) detected the CO(6-5) emission line and its underlying continuum, deriving a gas mass of $M_{\rm gas}=1.5 \times 10^{10}\ \rm M_\odot$. Later, (cite: wang2013) analyzed the \[CII\] line emission and underlying continuum, deriving a dynamical mass of $M_{\rm dyn}=12.5 \times 10^{10}\rm \ M_\odot$ (also confirmed by (cite: shao2017)). (cite: shao2017) estimated a BH mass $M_{\rm BH} = (2.7 \pm 0.6) \times 10^9 \rm \ M_\odot$ from the MgII line, which contributes 2% of the dynamical mass of the system. (cite: carniani2019) performed a detailed study of the cold-dust SED of J1319+1950 deriving a dust mass of $\log(M_{\rm dust}/M_\odot)=8.8\pm 0.2$ and a dust temperature of $T_{\rm dust}=66^{+15}_{-10}$ K. (cite: herrera-camus2020) tentatively detected the OH 119 $\mu$m doublet in absorption, which is blueshifted with a median velocity that suggests the presence of a molecular outflow, although characterized by a modest molecular mass loss rate of $\sim 200\ \rm M_\odot ~yr^{-1}$.

## PSO J183.1124+05.0926

PSO J183.1124+05.0926 (hereafter J183+05) at $z = 6.439$ was discovered by (cite: banados2018) using color-color selections from the Pan-STARRS1 database (cite: chambers2016) and follow-up photometric and spectroscopic observations. The \[CII\] luminosity in this source is the highest among 27 quasars at $z>6$ surveyed in (cite: decarli2018). J183+05 showed a clear velocity gradient however, given the resolution of the observation, only an upper limit to dynamical mass has been derived $M_{\rm dyn} >1.3 \times 10^{11}\ \rm M_\odot$ from the study of its rotation curve (cite: neeleman2021). It has a BH mass of $M_{\rm BH} = 3.0\times 10^9\ \rm M_\odot$ derived from MgII emission line. Recently, (cite: decarli2023) analyzed the cold-dust SED of this QSO in detail, deriving $T_{\rm dust}=47 \pm 2$ K, $M_{\rm dust}= (8.7 \pm 1.1) \times 10^{8} \ \rm M_\odot$ and ${\rm SFR}=1330\ \rm M_\odot ~yr^{-1}$. They also presented a multi-line study of this object, reporting detections of \[CII\], \[OIII\], \[NII\], CO(7-6), OH and two H$_2$O transitions.

# Analysis of continuum emission from archival observations

## QSO J036+03

We analyzed the three ALMA observations available in B6 and B7 for J036+03, and we derived continuum flux densities and sizes at 243.11 GHz, 260.53 GHz and 338.71 GHz, performing a 2D Gaussian fit with CASA for each observation. All continuum emissions at these frequencies are spatially resolved and the values for flux densities, peak fluxes and sizes are reported in Tab. [\[tab:c3-table-obs\]](#tab:c3-table-obs).

In order not to miss the fainter and more extended flux, we tapered the higher resolution observations at 243.1 GHz and 260.5 GHz, performing the imaging with `uvtaper`=\[$0.9$ arcsec\], reaching a resolution of $\sim 0.7\times 0.7$ arcsec$^2$ and of $\sim 0.88\times 0.83$ arcsec$^2$ respectively. The sources in the tapered maps were fitted with the CASA 2D Gaussian fit, and the new continuum fluxes are reported in bold within brackets in Tab. [\[tab:c3-table-obs\]](#tab:c3-table-obs). At 243.1 GHz, the higher resolution observation missed $\sim 20\%$ of the flux. Similar flux losses were also seen by (cite: wang2019) when analyzing high resolution observations of QSO J0100+2802. We checked that there was no further flux gain if tapering at even lower resolution.

## QSO J0224-4711

We analyzed the three ALMA observations available in B3 and B6 for J0224-4711, and we derived continuum flux densities and sizes at 95.33 GHz, 245.67 GHz, and 260.51 GHz, performing a 2D Gaussian fit with CASA for each observation. The two B6 continuum emissions are spatially resolved and the values for flux densities, peak fluxes and sizes are reported in Tab. [\[tab:c3-table-obs\]](#tab:c3-table-obs). The emission in B3 is not resolved (see left panel of Fig. [2](#fig:c2-co76)), therefore we considered the peak flux as total flux of the source, which is $0.103 \pm 0.009$ mJy/beam, analogously to B8 and B9.

Also for this object, we tapered the higher resolution observations at 245.67 GHz and 260.51 GHz, performing the imaging with `uvtaper`=\[$0.7$ arcsec\], reaching a resolution of $\sim 0.7\times 0.7$ arcsec$^2$. The sources in the tapered maps were fitted with the CASA 2D Gaussian fit, and we found no gain in flux even when tapering both observations at even lower resolution.

## QSO J2054-0005

We analyzed the continuum emission at different frequencies of J2054-0005 from the archival observations reported in Tab. [\[tab:c3-table-obs\]](#tab:c3-table-obs). The analyses were carried analogously to the ones of J036+03 and J0224-4711, and the info about the fluxes and sizes obtained are reported in Tab. [\[tab:c3-table-obs\]](#tab:c3-table-obs).

We tapered the higher resolution observations at 92.26 GHz, 262.6 GHz, and 488.31 GHz using `uvtaper`=\[0.7 arcsec\], in order to account for the more extended and fainter emission. We achieved a resolution of 1.0 $\times$ 0.89 arcsec$^2$, 0.88 $\times$ 0.82 arcsec$^2$, and 0.88 $\times$ 0.81 arcsec$^2$ for the 92.26 GHz, 262.6 GHz and 488.31 GHz observation, respectively. We did not find any further emission for the lowest frequency observation, while we gained $\sim 5\%$ of the flux in the other two observations.

## QSO J231-20

![](continuum-J231-B8.png)

Fig. [18](#fig:app-j231) shows the B8 continuum emission of QSO J231-20. Details on the analysis can be found in Sect. [4.1.4](#subsec:j231).

# Tables

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| QSO | Obs freq | Beam cont | r.m.s. cont | Flux density | Peak flux | Size | Size | Refs | Project ID |
|  | (GHz) | \[arcsec$^2$\] | \[mJy/beam\] | \[mJy\] | \[mJy\] | \[arcsec$^2$\] | \[kpc$^2$\] |  |  |
| J036+03 | 106.97 | 6.1 $\times$ 3.5 | 0.038 | 0.13 $\pm$ 0.02 | – | – | – | \[1\] | S17CD (NOEMA) |
|  | 243.11 | 0.12 $\times$ 0.08 | 0.007 | 2.05 $\pm$ 0.1 | 0.54 $\pm$ 0.02 | 0.17 $\times$ 0.14 | 0.94 $\times$ 0.78 | TP | 2019.1.01633.S |
|  |  |  |  | (**2.43 $\pm$ 0.06**) | (**2.22 $\pm$ 0.03**) |  |  |  |  |
|  | 260.53 | 0.18 $\times$ 0.17 | 0.01 | 2.84 $\pm$ 0.13 | 1.28 $\pm$ 0.04 | 0.22 $\times$ 0.18 | 1.22 $\times$ 1.00 | TP, \[2\] | 2015.1.00399.S |
|  |  |  |  | (**2.95 $\pm$ 0.03**) | (**2.71 $\pm$ 0.01**) |  |  |  |  |
|  | 338.71 | 0.77 $\times$ 0.54 | 0.03 | 5.54 $\pm$ 0.05 | 4.69 $\pm$ 0.03 | 0.31 $\times$ 0.22 | 1.72 $\times$ 1.22 | TP | 2018.1.01790.S |
|  | 404.99 | 2.10 $\times$ 1.43 | 0.60 | 6.63 $\pm$ 0.39 | 6.63 $\pm$ 0.39 | – | – | TP | 2021.2.00151.S |
|  | 670.92 | 1.12 $\times$ 0.97 | 0.50 | 5.60 $\pm$ 0.69 | 5.60 $\pm$ 0.69 | – | – | TP | 2021.2.00151.S |
| J0224-4711 | 95.33 | 3.95 $\times$ 2.32 | 0.016 | 0.094 $\pm$ 0.010 | 0.094 $\pm$ 0.010 | – | – | TP | 2017.1.01472.S |
|  | 245.67 | 0.56 $\times$ 0.56 | 0.024 | 2.03 $\pm$ 0.05 | 1.49 $\pm$ 0.02 | 0.35 $\times$ 0.33 | 1.95 $\times$ 1.84 | TP | 2018.1.01188.S |
|  | 260.51 | 0.13 $\times$ 0.11 | 0.013 | 3.01 $\pm$ 0.25 | 0.80 $\pm$ 0.05 | 0.20 $\times$ 0.18 | 1.11 $\times$ 1.00 | TP | 2021.1.00934.S |
|  | 405.19 | 3.87 $\times$ 2.79 | 0.88 | 8.73 $\pm$ 0.38 | 8.73 $\pm$ 0.38 | – | – | TP | 2021.2.00151.S |
|  | 670.96 | 1.08 $\times$ 0.95 | 1.3 | 19.9 $\pm$ 0.96 | 19.9 $\pm$ 0.96 | – | – | TP | 2021.2.00151.S |
| J231-20 | 406.848 | 4.35 $\times$ 2.90 | 0.50 | 8.43 $\pm$ 0.39 | 8.43 $\pm$ 0.39 | – | – | TP | 2021.2.00064.S |
|  |  |  |  | 6.74 $\pm$ 0.31$^{(a)}$ |  |  |  |  |  |
| J2054-0005 | 92.26 | 0.42 $\times$ 0.32 | 0.006 | 0.082 $\pm$ 0.009 | 0.066 $\pm$ 0.004 | 0.27 $\times$ 0.07 | 1.57 $\times$ 0.41 | TP | 2018.1.01289.S |
|  | 262.6 | 0.33 $\times$ 0.29 | 0.019 | 2.82 $\pm$ 0.06 | 2.17 $\pm$ 0.03 | 0.19 $\times$ 0.15 | 1.10 $\times$ 0.87 | TP | 2019.1.00672.S |
|  |  |  |  | (**2.93 $\pm$ 0.07**) | (**2.74 $\pm$ 0.04**) |  |  |  |  |
|  | 263.93 | 1.23 $\times$ 1.12 | 0.010 | 3.08 $\pm$ 0.03 | 2.90 $\pm$ 0.02 | 0.33 $\times$ 0.23 | 1.92 $\times$ 1.34 | TP | 2017.1.01088.S |
|  | 488.31 | 0.43 $\times$ 0.37 | 0.064 | 11.32 $\pm$ 0.25 | 9.05 $\pm$ 0.12 | 0.24 $\times$ 0.15 | 1.39 $\times$ 0.87 | TP | 2017.1.01195.S |
|  |  |  |  | (**11.71 $\pm$ 0.11**) | (**10.77 $\pm$ 0.06**) |  |  |  |  |
|  | 674.97 | 0.65 $\times$ 0.57 | 0.50 | 9.87 $\pm$ 0.94 | 8.25 $\pm$ 0.48 | 0.29 $\times$ 0.24 | 1.68 $\times$ 1.39 | TP | 2016.1.01063.S |

**Notes.** Columns: (1) Target QSO; (2) observed frequency of the continuum emission; (3) clean beam of the continuum map; (4) r.m.s of the continuum map; (5) flux density of the continuum emission at the nominal resolution of the observation and at a tapered resolution when necessary (in bold and brackets); (6) peak flux of the continuum emission at the nominal resolution of the observation and at a tapered resolution when necessary (in bold and brackets); (7) size in arcsec$^2$ of the resolved continuum emission; (8) size in kpc$^2$ of the resolved continuum emission. (9) References: This paper (TP); \[1\] (cite: decarli2022); \[2\] (cite: venemans2020). (10) project ID of the observation. $^{(a)}$: flux corrected for the contribution of the companion to the QSO emission.

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| QSO | Obs freq | Beam cont | r.m.s. cont | line (spw:chans) | Beam line | r.m.s line | chan width | Project ID |
|  | (GHz) | \[arcsec$^2$\] | \[mJy/beam\] |  | \[arcsec$^2$\] | \[mJy/beam\] | \[km s$^{-1}$\] |  |
| J0224-4711 | 95.33 | 3.95 $\times$ 2.32 | 0.016 | CO(7-6) (0/1:56-76)$^{(\rm a)}$ | 3.53 $\times$ 2.07 | 0.14 | 43.7 | 2017.1.01472.S |
|  |  |  |  | \[CI\] (0/1:88-100)$^{(\rm a)}$ |  |  |  |  |
| J1319+0950 | 103.51 | 0.3 $\times$ 0.3 | 0.054 | CO(6-5) (0/1:100-141)$^{(\rm a)}$ | 0.32 $\times$ 0.31 | 0.1 | 24 | 2018.1.01289.S |
| J2054-0005 | 92.26 | 0.42 $\times$ 0.32 | 0.006 | CO(6-5) (0/1:106-130)$^{(\rm a)}$ | 0.39 $\times$ 0.30 | 0.1 | 24 | 2018.1.01289.S |

**Notes.** Columns: (1) Target QSO; (2) observed frequency of the observation; (3) clean beam of the continuum map; (4) r.m.s of the continuum map; (5) spw and channels of the detected emission lines; (6) clean beam of the continuum-subtracted cube; (7) r.m.s of the continuum-subtracted cube; (8) channel width of the continuum-subtracted cube; (9) project ID of the observation. $^{(\rm a)}$: spw 0 and spw 1 were combined since they covered almost the same spectral range and in order to maximize the S/N of the emission lines. $^{(\rm b)}$: natural weighting. $^{(\rm c)}$: Briggs weighting with robust=0.5. $^{(\rm d)}$: since the \[CII\] of J0110+2802 showed emission up to high-velocities ($\sim 1000$ km s$^{-1}$), we combined the two spectral windows in the upper side band to ensure a reliable continuum subtraction.

|  |  | J036+03 | J0224-4711 | J231-20 | J2054-0005 | J183+05 | J1342+0928 | J1319+0950 | J1148+5251 | J0100+2802 | J2310+1855 |
|:---|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| HYP |  | Y | Y | Y | N | N | Y | N | Y | Y | N |
| z |  | 6.540 | 6.522 | 6.587 | 6.390 | 6.439 | 7.540 | 6.133 | 6.419 | 6.327 | 6.003 |
| $M_{\rm dust}$ | $[10^7\ M_{\odot}]$ | 6.1 ± 2.5 | 9.3 ± 2.7 | 53 ± 5 | 10.6 ± 2.4 | 45 ± 9 | 2.6 ± 1.4 | 63 ± 29 | 32 ± 8 | $2.3\pm 0.8$ | 44 $\pm$ 7 |
| $T_{\rm dust}$ | \[K\] | $59\pm 2$ | $85^{+12}_{-8}$ | $51\pm 3$ | 64 ± 2 | 54 ± 5 | 55 ± 20 | 66$^{+15}_{-12}$ | 75 ± 8 | $48 \pm 2$ | 71 $\pm$ 4 |
| $\beta$ |  | 2.4 ± 0.2 | 1.7 ± 0.2 | 1.6 ± 0.1 | 2.1 ± 0.1 | 1.7 ± 0.2 | 1.8 ± 0.4 | 1.5 ± 0.3 | 1.5 ± 0.2 | $2.6 \pm 0.2$ | 1.86 $\pm$ 0.12 |
| $L_{\rm TIR}$ | \[$10^{12}\ \rm L_{\odot}$\] | 6.2 ± 1.0 | 33.2$^{+22}_{-10}$ | 6.6 ± 1.6 | 9.8 ± 1.0 | 11.9 ± 4.0 | 2.4$^{+3.7}_{-2.3}$ | 16$^{+13}_{-6}$ | 21 ± 7 | 5.3 ± 0.6 | 2.48$^{+0.62}_{-0.52}$ |
| SFR | \[$\rm M_{\odot}\ yr^{-1}$\] | 466 ± 75 | 2485$^{+1682}_{-768}$ | 496 ± 118 | 730 ± 75 | 894 ± 299 | 180$^{+280}_{-170}$ | 1197$^{+972}_{-449}$ | 1570 ± 524 | 396 ± 48 | $1855^{+464}_{-389}$ |
| Refs-D |  | This work | This work | This work | This work | TW,\[1\] | TW,\[2\] | \[3\] | \[3\] | \[4\] | \[5\] |
| $M_{\rm gas}$ | \[$10^{10}\ \rm M_{\odot}$\] | 0.7 $\pm$ 0.1 | 1.0 $\pm$ 0.1 | 1.4 ± 0.1 | 0.6 $\pm$ 0.1 | 4.5 | $<0.35$ | $1.5\pm 0.2$ | 2.6 | $0.5\pm 0.2$ | 4.4$\pm$ 0.2 |
| GDR |  | 123 | 110 | 26 | 60 | 100 | $<130$ | 24 | 81 | 236 | 101 |
| $\tau_{\rm dep}$ | \[Gyr\] | 0.01 | 0.004 | 0.03 | 0.008 | 0.05 | $<0.02$ | 0.01 | 0.02 | 0.01 | 0.02 |
| Refs-G |  | This work | This work | TW,\[6\] | This work | \[1\] | \[2\] | This work | \[7\] | \[1\] | \[5\] |

**Notes**. The results for the QSOs on the left side of the first vertical line are entirely obtained from this work, that is, all observations were analyzed by the author. Between the two vertical lines, the results for J183+05 and J1342+0928 were obtained fitting their observed SEDs presented in (cite: decarli2023) and (cite: novak2019), respectively; the results for J1319+0950 and J1148+5251 are taken from (cite: carniani2019). On the right side of the second vertical line, the results for J0100+2802 and J2310+1855 are taken from (cite: tripodi2023b; Tripodi2022), respectively. The SFRs are computed from $L_{\rm TIR}$ assuming a Kroupa IMF, and they are corrected by a factor of 50% in order to take the contribution of the AGN to the dust heating into account. The first raw shows whether the QSO belongs to the HYPERION sample. The gas mass for J231-20 is computed from the CO(7-6) luminosity in \[6\] using the $r_{76}$ derived in Sect. [5.2](#sec:gasmass) for J1007+2115, and it agrees with that derived from \[CI\] in \[2\]. Refs-D: References for the dust properties and SFR. Refs-G: References for the gas mass. Refs: This work (TW); \[1\] (cite: decarli2023); \[2\] (cite: novak2019); \[3\] (cite: carniani2019); \[4\] (cite: tripodi2023b); \[5\] (cite: Tripodi2022); \[6\] (cite: Pensabene2021); \[7\] (cite: stefan2015).

[^1]:

[^2]: These QSOs are J0100+2802, J036+03, J0224-4711, J231-20, J2310+1855, J1319+0950, and J183+05.

[^3]: The maximum value of the velocity dispersion toward the nucleus is usually affected by beam smearing (cite: davies2011).

[^4]: All luminosities were computed following Eq.1 and Eq.3 of (cite: solomon2005)

[^5]: The bins were defined considering the different ALMA bands and trying to have a similar number of data in each bin.

[^6]: They also derived the dust properties using the dust model of (cite: compiegne2011) with $\beta=1.91$ finding that the dust masses are systematically larger by about 20%-40% when adopting the model of (cite: draine2007).

[^7]: ‘Reionization Era Bright Emission Line Survey’ (REBELS; PI: Bouwens) is an ALMA large program targeting 40 of the brightest known galaxies at $z>6.5$ (cite: bouwens2022).

[^8]: The Band 8 continuum of REBELS-12 was undetected, therefore they derived an upper-limit.

[^9]: Fixing $\beta$ introduces an uncertainty of $\sim 25\%$ in the estimate of $T_{\rm dust}$.

[^10]: For both samples, the mean value of the distribution corresponds to the median.

[^11]: As a note of caution, we must emphasize that during the BH- (galaxy-) dominated regime, the galaxy (BH) is still growing, but more slowly and/or less efficiently than the BH (galaxy).

[^12]: $\dot{M}_{\rm BH}=L_{\rm bol}/(\epsilon ~c^2)$, where $c$ is the speed of light.

[^13]: The errors reported on $M_{\rm dyn}$ take into account the systematics due to the circular velocity and the radius of the galaxy used to derive $M_{\rm dyn}$ (see also the discussion in (cite: neeleman2021)). For the majority of the QSOs in our sample, $M_{\rm dyn}$ was derived in (cite: neeleman2021) in a consistent way.

[^14]: The slope of the arrow in (cite: tripodi2023b) is higher than reported in this work. This is because the SFR was computed using the Chabrier IMF rather then the Kroupa IMF (as in this work), which yielded an SFR that was lower by a factor of $\sim 0.7$ than in this work, and therefore, to a lower $G_{\rm gal}$ and a higher slope of the arrow.

</paper>

Write the methods card for this paper.