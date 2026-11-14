# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...989..115T\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...989..115T",
 "title": "ALMA Lensing Cluster Survey: Physical Characterization of Near-infrared-dark Intrinsically Faint ALMA Sources at z = 2─4",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Tsujita, Akiyoshi",
 "n_authors": 36,
 "arxiv_id": "2406.09890",
 "doi": "10.3847/1538-4357/adb41d",
 "alma_projects_linked_by_archive": [
  "2018.1.00035.L",
  "2019.1.00949.S",
  "2021.1.01246.S"
 ]
}
```

Paper text:
<paper>
# ALMA Lensing Cluster Survey: Physical characterization of near-infrared-dark intrinsically faint ALMA sources at z=2-4

## Abstract

We present results from Atacama Large Millimeter/submillimeter Array (ALMA) spectral line-scan observations at 3-mm and 2-mm bands of three near-infrared-dark (NIR-dark) galaxies behind two massive lensing clusters MACS J0417.5-1154 and RXC J0032.1+1808. Each of these three sources is a (sub)mm faint (de-lensed $S_{\rm 1.2 mm}$ $<$ 1 mJy) triply lensed system originally discovered in the ALMA Lensing Cluster Survey. We have successfully detected CO and \[C I\] emission lines and confirmed that their spectroscopic redshifts are $z=3.652$, 2.391, and 2.985. By utilizing a rich multi-wavelength data set, we find that the NIR-dark galaxies are located on the star formation main sequence in the intrinsic stellar mass range of log ($M_*$/$M_\odot$) = 9.8 – 10.4, which is about one order of magnitude lower than that of typical submillimeter galaxies (SMGs). These NIR-dark galaxies show a variety in gas depletion times and spatial extent of dust emission.

One of the three is a normal star-forming galaxy with gas depletion time consistent with a scaling relation, and its infrared surface brightness is an order of magnitude smaller than that of typical SMGs. Since this galaxy has an elongated axis ratio of $\sim 0.17$, we argue that normal star-forming galaxies in an edge-on configuration can be heavily dust-obscured. This implies that existing deep WFC3/F160W surveys may miss a fraction of typical star-forming main-sequence galaxies due to their edge-on orientation.

# Introduction

Dust affects the spectral energy distribution (SED) of galaxies by absorbing and scattering ultraviolet (UV) and optical emission, mainly produced by young stars, and re-emitting the energy at the far-infrared (FIR) and sub-millimeter (sub-mm) wavelengths. Consequently, dusty galaxies at $z\gtrsim 2$ typically appear very faint at observed-frame optical/near-infrared (NIR) due to dust obscuration.

Instead, their dust continuum is prominent at FIR/sub-mm band and some extreme ones are bright enough (e.g., $S_{\SI{870}{\mu m}}>\mathrm{several\  mJy}$) to be detected with single-dish telescopes. They are referred to as submillimeter galaxies (SMGs; (cite: Hodge2020) for a review).

Since the first detection of high-redshift SMGs, many have been found to be completely obscured in the rest-frame UV/optical (or observed-frame NIR) due to strong dust attenuation, dubbed NIR-dark galaxies (e.g., (cite: Smail1999; dacunha2015; Yamaguchi2019; Casey2019; Umehata2020; Dudzeviciute2020; Riechers2020; Sun2021; zavala2021; Smail2021; Shu2022)).

Similar terms, such as $HST$-dark and $H/K$-dropout, are also used to describe these dust-obscured sources.

The advent of the Atacama Large Millimeter/submillimeter Array (ALMA) has enabled us to uncover the faint ($S_{\mathrm{1.2mm}} < \SI{1}{mJy}$) (sub-)mm-selected galaxies, that are significantly fainter (up to $\sim100$ times) than the classical SMGs. Hereafter, we will use the term dusty star-forming galaxies (DSFGs) to more generally refer to dusty galaxies including these faint sources. It has been revealed that the dust-obscured galaxies exist not only among SMG-like extreme starburst galaxies but also among more common DSFGs which lie on the main sequence of the $M_*$–SFR relation (cite: Schreiber2015), particularly at the high mass end where $M_* > 10^{10.3} M_\odot$ (e.g., (cite: Wang2019Nat)). These galaxies have been detected through blind ALMA surveys (e.g., (cite: Simpson2014; Yamaguchi2016; Fujimoto2016; Franco2018; Yamaguchi2019; Dudzeviciute2020; Gruppioni2020; Xiao2023; Fujimoto2024ApJS..275...36F; Fujimoto2023b)), follow-up ALMA observations of galaxies with very red colors in NIR range (e.g., (cite: Caputi2012; Wang2016; Wang2019Nat; Alcalde2019)), follow-up ALMA observations of strongly-lensed galaxies that are identified in (sub)mm-single-dish surveys (cite: Pope2017ApJ...838..137P; Pope2023ApJ...951L..46P; Mizener2024ApJ...970...30M; Shu2022), and serendipitous discoveries (cite: Hatsukade2015; Williams2019; Romano2020; Fudamoto2021). Recent *James Webb Space Telescope* (*JWST*) observations have also begun to uncover a broader range of NIR-dark galaxies, including those that are less massive (e.g., (cite: Barrufet2023; Barrufet2024arXiv240408052B; Nelson2023; Perez-Gonzalez2023ApJ; Gomez-Guijarro2023; Xiao2023arXiv230902492X; Smail2023; Kokorev2023; McKinney2023ApJ...956...72M; Sun2024)).

This normal dust-obscured population was often missed by previous (sub)mm-single-dish surveys due to its modest (sub-)mm flux, lower than the confusion limit of single-dish telescopes, and was also overlooked by the Lyman break technique which relies on the rest-frame UV light. However, (cite: Wang2019Nat) suggested that this population constitutes the bulk of massive galaxies (from 20% at $M_*\sim 10^{10.3}\,M_\odot$ to 80% at $M_*\sim 10^{11.0}\,M_\odot$) at $z\sim3-6$ and is the main progenitor of the most massive quiescent galaxies at $z\sim2-3$, as well as of today’s ellipticals that reside in the central regions of massive groups and clusters (see also (cite: Valentino2020)). The large number of such dusty massive galaxies in the early universe is not accounted for by current semi-analytical models, posing a challenge to our understanding of massive galaxy formation.

Despite its importance, obtaining accurate redshifts for these galaxies (either optical/NIR spectroscopy or (sub-)mm line scans) is challenging, hindering efforts to characterize the population. This difficulty is partly due to significant extinction in the rest-frame UV and optical, where key redshift indicators like the Lyman break and 4000 Å break lie. Another factor is the significantly lower (sub-)mm flux of this population compared with those of classical SMGs, which makes line scan observations for redshift search much more expensive, even with ALMA. To date, several spectroscopic redshift identifications for the NIR-dark galaxies have been reported (e.g., (cite: Swinbank2012; Casey2019; Williams2019; Umehata2020; Zhou2020; Riechers2020; Smail2023; Kokorev2023; Sun2024; Barrufet2024arXiv240408052B)) but almost all of them are for the SMG-class bright sources except for a few cases such as (cite: Fudamoto2021) which reported the serendipitous \[C II\]$_{158}$ line detection of two normal dust-obscured galaxies at $z\sim7$.

Therefore, physical characterizations based on secure redshifts remain largely unexplored for the normal NIR-dark population, particularly in terms of molecular gas properties based on CO or \[C I\] emission lines.

Furthermore, it remains unclear what the origin of the strong dust attenuation is, or in other words, what differentiates NIR-dark galaxies from other normal main-sequence SFGs.

(cite: Smail2021) investigated the correlation between the strength of dust attenuation ($A_V$) and other physical quantities in ALMA-identified SMGs, concluding that the correlations with dust mass and stellar mass are weak, while those with the photometric redshift and the “compactness" of the star-forming region ($\Sigma_{\mathrm{IR}}$) show stronger links. However, they suggest that other factors such as the geometry of stars/dust may also be involved, particularly for completely dust-obscured galaxies (see also (cite: dacunha2015; Wang2018; Cochrane2023)). Moreover, recent *JWST* studies claim that the viewing angle of the galaxy (i.e., an edge-on disk) may be a contributing factor (cite: Nelson2023), while others argue that redshift and/or stellar mass are the main factors (cite: Lagos2020; Gomez-Guijarro2023; Lorenz2023).

In this paper, we focus on normal dust-obscured galaxies originally discovered in the ALMA Lensing Cluster Survey (ALCS). Thanks to lens magnification, these galaxies appear as bright as classic SMGs (detectable with typical single-dish telescopes), making them suitable for follow-up observations. We successfully identified spectroscopic redshifts for three sources and estimated their basic physical properties via ALMA Band 3 and 4 line scan observations. We then compared these properties with those of other galaxy populations. Based on the obtained results, we discuss the evolutionary scenario and the origin of the strong dust attenuation for the normal dust-obscured galaxies.

This paper is organized as follows. Section [2](#sec:data) describes the observational data and reduction. In Section [3](#sec:results), we present the spectral redshift identification, SED fitting results, molecular gas properties, FIR morphology, and properties of the photodissociation region of our samples. In Section [4](#sec:discussion), we discuss the origin of the strong dust attenuation. A summary is presented in Section [5](#sec:summary). Throughout the paper, we adopt a cosmology with $\Omega_{\mathrm{m}}=0.3$, $\Omega_\Lambda=0.7$, and $H_0=\SI{70}{km.s^{-1}.Mpc^{-1}}$ and the Chabrier initial mass function (IMF, (cite: Chabrier2003)). We convert values obtained by other studies from the (cite: Salpeter1955) IMF to the Chabrier IMF by dividing SFR and stellar masses by the same factor, 1.7 (cite: Speagle2014). All magnitudes in this paper are expressed in the AB system (cite: Oke1974).

# Data and reduction

## ALMA Lensing Cluster Survey

The ALMA Lensing Cluster Survey (ALCS, (cite: Kohno2023; Fujimoto2024ApJS..275...36F)) is a Cycle-6 ALMA large program (project code: 2018.1.00035.L; PI: K. Kohno) that targets highly magnified areas within 33 massive galaxy clusters. The samples are selected from the best-studied clusters drawn from the Cluster Lensing And Supernova Survey with Hubble (CLASH; (cite: Postman2012)), Hubble Frontier Fields (HFF; (cite: Lotz2017)), and the Reionization Lensing Cluster Survey (RELICS; (cite: Coe2019)). The survey employs a 15-GHz-wide spectral scan in Band 6 ($\overline{\lambda_{\mathrm{obs}}}=\SI{1.15}{mm}$, $\overline{\nu_\mathrm{obs}}=\SI{260}{GHz}$).

The total mapping area reaches $\SI{134}{arcmin^2}$ (primary beam $> 0.3$) with a typical noise level of $1\sigma\sim\SI{60}{\mu Jy.beam^{-1}}$. Thanks to cluster lensing, ALCS explores a unique parameter space towards faint and wide regimes, compared to existing ALMA deep surveys.

Observations were carried out between December 2018 and December 2019 in compact array configurations of C43-1 and C43-2 (corresponding to a beam size of $\theta\sim 1\ensuremath{''}$) fine-tuned to recover strongly lensed (i.e., spatially elongated), low surface brightness sources.

ALCS yields 180 continuum source detections in total (including multiple images) consisting of 141 blind detections with a signal-to-noise ratio (SNR) of greater than five in the natural weighting maps and 39 prior-based detections with $\mathrm{SNR=4-5}$ which have IRAC-counterparts. Full descriptions of the data analysis and source catalog are given in (cite: Fujimoto2024ApJS..275...36F).

## Optical, NIR, and FIR catalogs

The 33 clusters were observed with *HST*, *Spitzer Space Telescope*, and *Herschel Space Observatory*.

(cite: Kokorev2022) builds a set of *HST* and *Spitzer*/IRAC 3.6 and 4.5  m mosaics and photometric catalogs by reprocessing archival data in the ALCS fields.

One of the difficulties in studying the galaxy clusters and other crowded regions is that the photometries taken by low-resolution instruments such as *Spitzer*/IRAC suffer from the effect of blending. To alleviate the effect, they model the *Spitzer* photometry by convolving the *HST* detection image with the *Spitzer* PSF using the novel `GOLFIR` software.

(cite: sun2022) compiles archival data from *Herschel*/PACS and SPIRE observations of the 33 clusters, with most of the data coming from *Herschel* Lensing Survey (cite: Egami2010). The study includes data taken at 100 and $\SI{160}{\mu m}$ with PACS, and 250, 350, $\SI{500}{\mu m}$ with SPIRE. Given the coarse angular resolution of *Herschel* (typical beam sizes are 7.4$\ensuremath{''}$ and 11.4$\ensuremath{''}$ for the 100 and $\SI{160}{\mu m}$ bands of PACS, and 18$\ensuremath{''}$, 24$\ensuremath{''}$, and 35$\ensuremath{''}$ for the 250, 350, and $\SI{500}{\mu m}$ bands of SPIRE), the authors deblended the *Herschel* fluxes using secure ALMA detections from the ALCS as priors.

## Target selection

In this work, we define NIR-dark sources as those with $H-[4.5]>2.3$, which are extremely red objects with $H$-band (F160W-band) and IRAC 4.5  m channel color, following the traditional method described in (cite: Wang2016). This color selection is designed to complementarily select massive star-forming galaxies that are systematically missed by the Lyman-break selection, which is specifically designed to select young and less attenuated galaxies (e.g., (cite: Bouwens2012)).

Figure [1](#fig:h-[4.5]) presents the color-magnitude diagram ($H-[4.5]$ vs. \[4.5\]) for the ALCS sample. We exclude sources that are not covered in the $H$-band, those contaminated by nearby bright objects or other artificial factors, or those identified as IRAC-dropout. Among the NIR-dark objects, six are $H$-dropout or $HST$-dark. We calculated the lower limit of their $H$-band magnitude by taking three times the median uncertainty of all photometric measurements within the corresponding galaxy cluster region in the (cite: Kokorev2022) catalog. In the (cite: Kokorev2022) catalogs, the IRAC photometries are measured by convolving the *HST* detection image with the IRAC PSF. The IRAC photometries of the $HST$-dark sources are instead measured using a $D=3\ensuremath{''}$ aperture with some aperture corrections centered on ALMA Band 6 continuum positions (cite: Kokorev2022). To mitigate contamination from nearby sources, we use the residual IRAC maps, wherein sources detected in the *HST* maps are modeled with the IRAC PSF and subtracted.

![](H-ch2_v2.png)

From these NIR-dark objects, we focused on three triply lensed systems: ID46, ID58, and ID121 in the MACS J0417.5-1154 (hereafter M0417) cluster region, ID127, ID131, ID198 in the RXC J0032.1+1808 (hereafter R0032) cluster region, and ID208, ID281, and ID304 in the R0032 cluster region. Figure [3](#fig:multi_band) shows the multi-band images for these sources. For clarity, we will hereafter refer to the three intrinsic sources as M0417-z365, R0032-z239, and R0032-z299, and their associated triply lensed images as M0417-z365.ID46/.ID58/.ID121, R0032-z239.ID127/.ID131/.ID198, and R0032-z299.ID208/.ID281/.ID304, respectively. The “z” values represent the spectroscopic redshift of each source, as described in Section [3.1](#sec:specz). Note that M0417-z365.ID46 is excluded in Figure [1](#fig:h-[4.5]) due to the blending with a foreground galaxy (see Figure [3](#fig:multi_band)). These systems were predicted to be multiple images by our fiducial lens model (section [3.2](#sec:lensmodel)). Figure [2](#fig:hst_alma) shows their ALMA 1.2 mm continuum and $HST$ images with critical lines of our fiducial lens models. We selected them since we are able to estimate their redshifts by the lens model, which allowed us to carry out line scan observations even though the photometric redshifts are unreliable.

![](hst_alma.png)

![](multiband_image.png)

## ALMA follow-up line scan observations

Based on the redshift estimates, we conducted follow-up line-scan observations for the three lensed systems with ALMA band 3 and 4 (project code: 2019.1.00949.S and 2021.1.01246 for M0417 and R0032 region, respectively). Four and three different tunings were assigned to band 3 and 4 observations, respectively.

The observational parameters are summarised in Table [1](#tab:ALMA_obs).

The fields of view of the observations are shown in Figure [2](#fig:hst_alma). The data were calibrated and flagged in the standard manner using the Common Astronomy Software Applications package (`CASA`; (cite: CASA2022)). The four tunings for band 3 and the three tunings for band 4 were separately combined to create individual continuum images for each band using `CASA/tclean` task with the natural weighting. The spectral channels where the emission line is detected were not used for the continuum imaging. Each tuning data was also imaged to produce a cube with a channel width of 40 MHz ($\sim \SI{100}{km.s^{-1}}$) to search for emission lines after the continuum subtraction with `CASA/uvcontsub` task. The emission is cleaned down to $2\sigma$ level. For all images and cube data, the primary beam correction is applied. We create images and cubes with a pixel size of 1$''$ for both band3 and 4 in the M0417. In the R0032 region, a pixel size of 0.2$''$ is used for both Band 3 and 4.

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Project code | Band | Target | Date | Antenna$^{$a$}$ | PWV | Frequency range | Beam size | Cont. sensitivity |
|  |  |  |  |  | \(mm\) | (GHz) |  | ($\mu$Jy/beam) |
|  | 3 | M0417-z365.ID46/.ID58/.ID121 | 2019/12 | C43-2 | 4.9–6.8 | 85.05–112.18 | $3.84\ensuremath{''}$$\times$$2.95\ensuremath{''}$ | 4.6 |
| 2019.1.00949.S |  | (2-pointing mosaic) |  | (46–48) |  | (T1–T4) |  |  |
| (PI: K. Kohno) | 4 | M0417-z365.ID46 | 2019/12 | C43-1/2 | 2.5–3.3 | 130.57–153.95$^{$b$}$ | $2.66\ensuremath{''}$$\times$$1.96\ensuremath{''}$ | 7.6 |
|  |  | (1-pointing) |  | (42–43) |  | (T5–T7) |  |  |
|  | 3 | R0032-z239.ID127/.ID131/.ID198 | 2021/12 | C43-4/5 | 1.5–7.5 | 85.06–112.18 | $1.04\ensuremath{''}$$\times$$0.87\ensuremath{''}$ | 3.8 |
|  |  | R0032-z299.ID208/.ID281/.ID304 | $\sim$2022/1 | (41–45) |  | (T1–T4) |  |  |
| 2021.1.01246.S |  | (2-pointing mosaic) |  |  |  |  |  |  |
| (PI: K. Kohno) | 4 | R0032-z239.ID127/.ID131 | 2022/8 | C43-5 | 0.3–0.9 | 130.56–153.94$^{$b$}$ | $0.77\ensuremath{''}$$\times$$0.53\ensuremath{''}$ | 6.8 |
|  |  | R0032-z299.ID208 |  | (44–47) |  | (T5–T7) |  |  |
|  |  | (2-pointing mosaic) |  |  |  |  |  |  |

: ALMA band 3 and 4 observation parameters

Table notes: a. Antenna configuration (the number in parentheses indicates the number of antennas) b. There is a frequency gap of about 2.75 GHz in this range as shown in Figure [4](#fig:spectrum).)

## JCMT SCUBA-2 450 & 850 $\mu$m

We observed the M0417 cluster region at $\SI{450}{\mu m}$ and $\SI{850}{\mu m}$ with James Clerk Maxwell Telescope (JCMT)/Submillimetre Common-User Bolometer Array 2 (SCUBA-2) (Program ID: M20AP036, PI: K. Kohno).

Observations were conducted on 2020 February 4, 16, July 8, and 31 using the CV Daisy scan, which creates a $\sim6\ensuremath{'}$ diameter circular map with a deep and uniform exposure coverage in the central $\sim1.5'$ diameter region. The total on-source time was 7.2 hr under excellent weather conditions, where the measured atmospheric opacities at 225 GHz were less than 0.05. The typical beam sizes are 7$\ensuremath{''}$ and 15$\ensuremath{''}$ at 450 $\mu$m and 850 $\mu$m, respectively.

We reduced the data using the Dynamic Iterative Map Maker (DIMM) within the STARLINK Sub-Millimetre User Reduction Facility (SMURF) software package (cite: Chapin2013).

The maps for each individual exposure were co-added and combined, using the STARLINK Pipeline for Combining and Analyzing Reduced Data (PICARD), and beam-match filtered. The resulting 1$\sigma$ noise levels were $\sim$3.9 mJy and $\sim$0.6 mJy at 450 $\mu$m and 850 $\mu$m bands, respectively.

The ALMA observations conducted by the ALCS did not detect any contamination sources near the positions of M0417-z365.ID46, ID58, and ID121. Therefore, no deblending was required, and the peak values at the ALMA Band 6 continuum positions were extracted as the source photometries.

## $K_{\rm S}$-band

In order to obtain better constraints on the stellar properties of faint ALMA sources without any counterpart in $H$-band, we observed M0417 cluster region at $\SI{2.16}{\mu m}$ $Ks$-band with the 6.5 m Magellan Baade Telescope/FourStar near-Infrared Camera on 2021 November 20 (PI: Wei-Hao Wang). We expect a significantly improved characterization of the stellar population (i.e., stellar mass, stellar age, visual extinction, etc.) by catching the 4000 Å break between $H$- and $K_{\rm S}$-bands at $z\sim3.7$ (the redshift of the triple-lensed images in the M0417 region, as we will conclude in Section [3.1](#sec:specz)). We obtained approximately 4.8 hr of on-source exposure. The final averaged seeing measured with `PSFEx` software is $\sim$0.64$''$.

We extracted photometries using a $D=1.5\ensuremath{''}$ aperture centered on the ALMA band 6 continuum positions for our target sources. We confirmed that this aperture maximizes the SNR of the enclosed flux density by drawing a growth curve. The noise level is obtained by 1000 random apertures on the sigma-clipped map. We note that the values in the weight map do not deviate significantly from the average at the source location. The aperture correction factor, calculated with the obtained PSF, is $\sim1.4$. The $5\sigma$-depth is measured to be 24.18 mag with the $D=1.5\ensuremath{''}$ aperture.

For the R0032 region, we make use of $K_S$-band imaging data taken with the High Acuity Wide field K-band Imager (HAWK-I) on Very Large Telescope. The Ks-band imaging of R0032 region (Program ID: 0103.A-0871(B), PI: A. Edge) is publicly available on the ESO Science archive. The final averaged seeing is $\sim$1.12$''$, and the $5\sigma$-depth is 22.81 mag with a $D=2.0\ensuremath{''}$ aperture. No significant detection is obtained for our sources.

# Data analysis

## Spectroscopic redshift identifications

### M0417-z365.ID46/.ID58/.ID121

Due to the sufficiently large beam size, the detection can be considered as a point source. We first created integrated-intensity maps around 99.1 GHz for Band 3 and around 148.6 GHz for Band 4, where bright emission lines were detected. On these maps, we selected the pixels with peak values at each position of the triply lensed image. The spectra were then extracted from the cube image data at these specific pixels.

Emission lines are clearly detected at $99.114\pm0.005\,\si{GHz}$ with peak flux densities of $8.6\sigma$, $7.3\sigma$, and $5.4\sigma$ from ID46, 58, and 121, respectively. Here, the noise level is calculated as the standard deviation of the line-free channel fluxes at the same pixels, specifically those within 50 channels of the emission line, with an absolute flux calibration error of 5%. We fitted the emission line with a single Gaussian and calculated the total flux as the integral over a frequency range of $1.5\times\text{FWHM}$. For a more robust measurement, the FWHM of all lines is fixed to that of the CO(4-3) line with the highest SNR. The total fluxes are $14.6\sigma$, $12.5\sigma$, and $8.9\sigma$ from ID46, 58, and 121, respectively. This line detection confirms the initial prediction from our lens model that these three sources are triply lensed images. In addition, a bright emission line is detected at $148.650\pm0.006\,\si{GHz}$ from ID46 with a peak (total) $\text{flux}=9.6\sigma\ (22.3\sigma)$. The noise level of the total flux is calculated by summing, in quadrature, the RMS noise from each channel derived from signal-free regions of the map across the channels containing the line.

Furthermore, when combining the spectra of the triply lensed images, a faint emission line is marginally detected at $105.84\pm0.02\,\si{GHz}$ with a total flux of $4.6\sigma$, although the peak flux density is only $3.4\sigma$. We search the redshift solution that matches the three detected line combinations using a publicly-available code[^1] (cite: Bakx2022). Since the frequency spacing between CO rotational transition lines is constant, detecting two CO lines can result in multiple possible redshift solutions. This code visually identifies the correct redshift solution by considering the observed frequencies, as well as the presence of detected lines and the absence of others. The only solution is at $z=3.6517\pm0.0002$ and the three lines are CO(4-3), \[C I\](1-0), and CO(6-5). This result is somewhat lower than the initial prediction from our lens model, $z=4.5\pm0.5$. Figure [4](#fig:spectrum) shows the full ALMA band-3/4 spectra for the three triply lensed NIR-dark sources, including the other two triply lensed images in the R0032 region discussed below. The line properties are summarized in Table [2](#tab:line_property). We similarly measured the band 3 and 4 continuum fluxes by extracting peak values near the source positions.

### R0032-z239.ID127/.ID131/.ID198

We used a circular aperture with a diameter of $D=4\ensuremath{''}$ centered on the ALCS band 6 continuum positions to extract spectra and continuum fluxes. By drawing a growth curve, we confirmed that this aperture is sufficient to include source fluxes. Emission lines are clearly detected at $101.963\pm0.008\,\si{GHz}$ with peak (total) fluxes of $8.8\sigma\ (13.6\sigma)$, $6.9\sigma\ (11.7\sigma)$, and $2.5\sigma\ (3.3\sigma)$ from ID127, 131, and 198, respectively. Thus, these three sources are triply lensed images as predicted from our lens model. The total line fluxes are measured in the same manner as section [3.1.1](#sec:M0417-z365). In addition, bright emission lines are detected at $135.956\pm0.008\,\si{GHz}$ and $145.123\pm0.018\,\si{GHz}$ from ID127 and ID131. From these lines, we conclude that this triply lensed source is at $z=2.39112\pm0.00019$ and detected emission lines are CO(3-2), CO(4-3), and \[C I\](1-0). This result is consistent with the initial prediction from our lens model, $z=2.0\pm0.5$.

### R0032-z299.ID208/.ID281/.ID304

We reconstructed the initial lens model of the R0032 cluster with the additional constraint that the R0032-z239.ID127/.ID131/.ID198 are triply lensed images and then found that it is highly likely that the R0032-z299.ID208/.ID281/.ID304 are also triply lensed images. The spectra and continuum fluxes are measured in the same manner as in section [3.1.2](#sec:R0032-z239). A emission line is barely detected at $144.56\pm0.03\,\si{GHz}$ with peak (total) fluxes of $3.0\sigma\ (5.2\sigma)$ from ID208. In addition, when combining the spectra of the triply lensed images, a faint emission line is detected at $86.77\pm0.02\,\si{GHz}$ with a peak (total) flux of $5.1\sigma\ (6.2\sigma)$. These results conclude that this lensed source is at $z=2.9853\pm0.0009$ and detected emission lines are CO(3-2) and CO(5-4). This result is consistent with the initial prediction from our lens model, $z=3.0\pm0.5$. These consistencies enhance the reliability of the identified spectroscopic redshift, even though the line detections are marginal. We emphasize that the detection of CO(3-2) line was made possible by the total magnification factor of $\sim15$, making the observation more than 100 times more efficient in terms of observation time.

![](spectrum.png)

| M0417-z365. | ID46 | ID58 | ID121 | Total |
|:--:|:--:|:--:|:--:|:--:|
| $\mu$ | $5.1\substack{+2.6 \\ -2.6}$ | $3.9\substack{+1.6 \\ -1.6}$ | $3.4\substack{+1.4 \\ -1.4}$ | $12.5\substack{+3.3 \\ -3.3}$ |
| CO(4-3) | $0.88\pm0.06$ | $0.59\pm0.05$ | $0.48\pm0.05$ | $1.95\pm0.10$ |
|  | $0.16\pm0.06$ | $0.17\pm0.06$ | $0.16\pm0.07$ | $0.49\pm0.11$ |
| CO(6-5) | $1.20\pm0.05$ | – | – | $1.20\pm0.05$ |
| R0032-z239. |  |  |  |  |
| $\mu$ | $6.9\substack{+3.6 \\ -3.5}$ | $5.3\substack{+2.7 \\ -2.7}$ | $2.5\substack{+1.1 \\ -1.0}$ | $14.7\substack{+4.6 \\ -4.6}$ |
| CO(3-2) | $3.5 \pm 0.3$ | $3.7 \pm 0.3$ | $1.1\pm0.3$ | $8.3\pm0.5$ |
| CO(4-3) | $5.9\pm0.3$ | $4.8\pm0.4$ | – | $10.7\pm0.5$ |
|  | $3.7\pm0.4$ | $2.2\pm0.5$ | – | $5.9\pm0.6$ |
| R0032-z299. |  |  |  |  |
| $\mu$ | $7.9\substack{+4.1 \\ -4.0}$ | $4.3\substack{+1.8 \\ -1.8}$ | 3.0$\substack{+1.3 \\ -1.2}$ | $15.2\substack{+4.6 \\ -4.6}$ |
| CO(3-2) | $0.57\pm0.17$ | $0.42\pm0.15$ | $0.59\pm0.13$ | $1.6\pm0.2$ |
| CO(5-4) | $1.6\pm0.3$ | – | – | $1.6\pm0.3$ |

: Velocity-integrated line flux density

Table notes: $\mu$ is the magnification factor. The velocity-integrated line flux density is in unit of Jy km s^−1^. The magnification factor is not corrected.

## Mass model

We utilize the publicly available `glafic` code (cite: Oguri2010; Oguri2021) to construct our fiducial lens models, following (cite: Kawamata2016) and (cite: Okabe2020). The multiple images that constrain the lens model are sourced from (cite: Mahler2019) for the M0417 cluster and from (cite: Acebron2020) for the R0032 cluster. Additionally, the three triply lensed systems identified in this study are included to provide further constraints. To assess the statistical uncertainty of the magnification factor, we employ an MCMC method, taking into account uncertainties in the positions of the multiple images ($\Delta x= \Delta y=0.4\ensuremath{''}$) and photometric redshifts ($\Delta z= 0.6$). The median value is chosen as the representative value, with the 16th and 84th percentiles serving as the uncertainty range. To account for potential systematic errors in the lens model, we introduce an additional error based on a comparison with other lens models that are constructed with different software, as detailed by (cite: Fujimoto2024ApJS..275...36F). Specifically, we incorporate an error of 40% for magnifications below 5 and 50% for those above 5. The obtained magnification factors can be found in Table [2](#tab:line_property).

## SED fitting

We use the `CIGALE` code (cite: Boquien2019) to perform SED fitting and estimate key physical parameters. The photometries used for the SED fitting are listed in Table [3](#tab:photometry). `CIGALE` models the SED panchromatically based on an energy balance principle, where all the absorbed energy is then re-emitted by the dust in the mid/far-infrared domains. Following (cite: Huang2023), instead of the default fixed grid parameter search in `CIGALE`, we implement a Bayesian-based approach using `DYNESTY` package (cite: Speagle2020). This allows for efficient exploration of extensive parameter spaces and computation of the Bayesian posterior distribution for the free parameters. We use flat prior distributions for all parameters.

We assume a nonparametric star-formation history (SFH) (cite: Leja2019) and adopt the stellar population model from (cite: Bruzual2003) with solar metallicity. The dust attenuation law is taken from (cite: Calzetti2000). For the dust infrared emission model, we use (cite: Draine2014) templates. We note that bright optical emission lines such as H$\alpha$ and \[O III\]$_{5007}$ don’t fall into the photometric bands used for our sources at their redshifts. For each multiple image, we performed SED fitting and, based on the posterior distribution, determined the median value as the best-fit parameter, accompanied by the 16–84% credible interval. In our case, differential magnification is negligible, meaning that the physical quantities scale linearly with the magnification factor. Therefore, the intrinsic physical quantities are derived by dividing the obtained apparent physical quantities by the magnification factor. After correcting each value for magnification, we took the intrinsic physical quantity as the average weighted by the inverse square of the uncertainties.

The best-fit SED models along with their 16–84% credible interval are shown in Figure [10](#fig:sed). The obtained intrinsic physical parameters along with their 16–84% percent credible interval are listed in Table [4](#tab:all_params). For the fiducial SFR value, we take one that is averaged over 100 Myr. The SFR can also be estimated from the total infrared luminosity ($L_{\mathrm{IR}}$) using the following relation: $\mathrm{SFR} = 4.5 \times 10^{-44} \, \mathrm{M_\odot \, yr^{-1} \, (erg \, s^{-1})^{-1}} \, L_{\mathrm{IR}}$, which is a calibration by (cite: Madau2014), but we multiply a factor of 0.63 to account for the correction from the Salpeter IMF to the Chabrier IMF. Using this equation, the SFR values inferred from $L_{\mathrm{IR}}$ are $167_{-69}^{+63}~\mathrm{M_\odot \, yr^{-1}}$ for M0417-z365, $92_{-35}^{+35}~\mathrm{M_\odot \, yr^{-1}}$ for R0032-z239, and $33_{-16}^{+12}~\mathrm{M_\odot \, yr^{-1}}$ for R0032-z299. These values are consistent within the uncertainties with the SFRs derived from the SED fitting.

Figure [5](#fig:mstar_sfr) shows the SFR versus $M_*$ relation of our three intrinsic sources. For comparison, *JWST*/NIRCam (long-wavelength filter)-selected $H$-band dropouts ($3\sigma$ depth of $H>\SI{27}{mag}$, (cite: Barrufet2023)), ALMA and *Spitzer*/IRAC-detected $H$-band dropouts (typical $5\sigma$ depth of $H>\SI{27}{mag}$, (cite: Wang2019Nat)), $2<z<4$ SMGs from the AS2UDS samples (cite: Dudzeviciute2020), NIR-dark SMGs (cite: Casey2019; Williams2019; Zhou2020; Umehata2020; Riechers2020; Manning2022; Smail2023; Kokorev2023; Sun2024), and NIR-dark DSFGs (cite: Fudamoto2021) are also shown. Some of these previous studies estimate physical quantities using `MAGPHYS` (cite: dacunha2015). Different SED fitting codes often produce systematic differences in results due to various assumptions they employ, especially the dust attenuation models. (cite: Uematsu2024) investigated whether there are systematic differences in physical quantities obtained with `MAGPHYS` and `CIGALE` with the Calzetti attenuation curve, using ALCS sample. They found that while the SFR estimates agree well, the stellar mass estimates from `CIGALE` are 0.37 dex lower at $M_*=10^{10.5} M_\odot$. In any case, our sample remains significantly lower in SFR and stellar mass compared to the SMGs in previous studies.

Our three samples lie on the main sequence (offset from the main sequence $\Delta \mathrm{MS}=\mathrm{SFR}/\mathrm{SFR_{MS}}$ is within a factor of 3), exhibiting a $M_*$–SFR relation similar to typical star-forming galaxies selected in NIR bands (e.g., (cite: Schreiber2015; Straatman2016)).

(cite: Wang2019Nat) and (cite: Xiao2023) suggest that such dust-obscured galaxies on the main sequence are a dominant population of the massive galaxies ($M_*\gtrsim10^{9.5}\,M_\odot$) at $3<z<6$. Among our samples, M0417-z365 is located at a region where $H$-dropouts of (cite: Wang2019Nat) are sampled. R0032-z299 is positioned on the lower mass and SFR region, bridging the gap with the dust-obscured galaxy candidates recently explored by *JWST*.

+:------------+:----------:+:----:+:---------------:+:---------------:+:---------------:+:-------------:+:--------------:+:-------------:+:-------------:+:-----------:+:-------------:+:---------:+
|             |            |      | M0417-z365                                          | R0032-z239                                     | R0032-z299                                  |           |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| Band        | Wavelength | Unit | ID46            | ID58            | ID121           | ID127         | ID131          | ID198         | ID208         | ID281       | ID304         | Reference |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| *HST*-F606W | 606 nm     | nJy  | blended         | $<26$           | $<26$           | $<53$         | $<53$          | $<53$         | $<53$         | $<53$       | $<53$         | K22       |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| *HST*-F814W | 814 nm     | nJy  | blended         | $<68$           | $<68$           | $<63$         | $<63$          | $<63$         | $<63$         | $<63$       | $<63$         | K22       |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| *HST*-F105W | 1.05  m    | nJy  | blended         | $<106$          | $<106$          | $<83$         | $<83$          | $<83$         | $<83$         | $<83$       | $<83$         | K22       |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| *HST*-F125W | 1.25  m    | nJy  | blended         | $<135$          | $<135$          | $<137$        | $<137$         | $<137$        | $<137$        | $<137$      | $<137$        | K22       |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| *HST*-F140W | 1.40  m    | nJy  | blended         | $<116$          | $<116$          | $207\pm31$    | $<119$         | $<119$        | $<119$        | $<119$      | $<119$        | K22       |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| *HST*-F160W | 1.60  m    | nJy  | blended         | $<111$          | $<111$          | $262\pm23$    | $707\pm121$    | $362\pm42$    | $<88$         | $<88$       | $<88$         | K22       |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| FourStar-Ks | 2.2  m     |  Jy  | blended         | $0.85\pm0.22$   | $<0.63$         | $\cdots$      | $\cdots$       | $\cdots$      | $\cdots$      | $\cdots$    | $\cdots$      | This work |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| HAWKI-Ks    | 2.2  m     |  Jy  | $\cdots$        | $\cdots$        | $\cdots$        | $<2.4$        | $<2.4$         | $<2.4$        | $<2.4$        | $<2.4$      | $<2.4$        | This work |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| IRAC-ch1    | 3.6  m     |  Jy  | blended         | $1.59\pm0.08$   | $1.33\pm0.07$   | $4.77\pm0.19$ | $11.5\pm0.2$   | $3.77\pm0.15$ | $2.02\pm0.19$ | $2.5\pm0.2$ | $2.65\pm0.16$ | K22       |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| IRAC-ch2    | 4.5  m     |  Jy  | blended         | $2.85\pm0.14$   | $2.67\pm0.14$   | $8.32\pm0.17$ | $17.85\pm0.17$ | $6.44\pm0.14$ | $3.22\pm0.17$ | $2.5\pm0.3$ | $4.10\pm0.14$ | K22       |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| SPIRE       | 250  m     | mJy  | $45.4\pm5.8$    | $11.1\pm7.3$    | $10.9\pm6.3$    | $13.2\pm5.3$  | $12.7\pm5.3$   | $33.8\pm7.7$  | $<15.6$       | $<15.7$     | $\cdots$      | S22       |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| SPIRE       | 350  m     | mJy  | $39.0\pm6.2$    | $14.8\pm5.3$    | $6.9\pm4.7$     | $30.2\pm7.4$  | $15.6\pm7.4$   | $24.9\pm8.4$  | $<21.7$       | $<21.8$     | $<27.0$       | S22       |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| SCUBA-2     | 450  m     | mJy  | $24.9\pm4.0$    | $14.3\pm4.0$    | $13.8\pm3.8$    | $\cdots$      | $\cdots$       | $\cdots$      | $\cdots$      | $\cdots$    | $\cdots$      | This work |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| SPIRE       | 500  m     | mJy  | $30.7\pm5.1$    | $11.1\pm5.7$    | $17.6\pm5.2$    | $<38.9$       | $32.7\pm11.4$  | $<23.0$       | $10.6\pm8.8$  | $<21.8$     | $<22.7$       | S22       |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| SCUBA-2     | 850  m     | mJy  | $11.09\pm0.65$  | $5.4\pm0.66$    | $5.28\pm0.65$   | $\cdots$      | $\cdots$       | $\cdots$      | $\cdots$      | $\cdots$    | $\cdots$      | This work |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| ALMA-B6     | 1.2 mm     | mJy  | $4.3\pm0.5$     | $3.1\pm0.4$     | $2.1\pm0.3$     | $4.5\pm0.5$   | $3.9\pm0.4$    | $1.4\pm0.2$   | $1.2\pm0.2$   | $1.2\pm0.2$ | $1.1\pm0.2$   | This work |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| ALMA-B4     | 2.1 mm     | mJy  | $0.395\pm0.018$ | $\cdots$        | $\cdots$        | $1.1\pm0.1$   | $0.88\pm0.09$  | $\cdots$      | $0.41\pm0.08$ | $\cdots$    | $\cdots$      | This work |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+
| ALMA-B3     | 3.0 mm     | mJy  | $0.095\pm0.007$ | $0.051\pm0.005$ | $0.039\pm0.007$ | $0.25\pm0.04$ | $0.23\pm0.04$  | $<0.09$       | $<0.08$       | $<0.08$     | $0.09\pm0.03$ | This work |
+-------------+------------+------+-----------------+-----------------+-----------------+---------------+----------------+---------------+---------------+-------------+---------------+-----------+

: Photometries of the three NIR-dark triply lensed systems (the magnification factor is not corrected)

![](mstar_sfr.png)

## Molecular gas properties

We estimate the total molecular gas mass $M_{\mathrm{gas}}$ using CO(3-2) line for the R0032-z239 and R0032-z299 and CO(4-3) line for the M0417-z365, respectively. We assume an average CO excitation of $r_{32/10}=0.58\pm0.10$ and $r_{43/10}=0.30\pm0.08$ (cite: Boogaard2020), where $r$ represents brightness temperature ratio. The value of CO-to-H$_2$ conversion factor $\alpha_{\mathrm{CO}}$ depends on various properties including metallicity, galactic environment, and morphology. In the following, we will show both results obtained with the assumption of $\alpha_{\mathrm{CO}}=3.6\ \mathrm{M_\odot (K.km.s^{-1}.pc^2)^{-1}}$, which is often assumed for massive MS galaxies (e.g., (cite: Aravena2019)), and of $\alpha_{\mathrm{CO}}=1.0\ \mathrm{M_\odot (K.km.s^{-1}.pc^2)^{-1}}$, which is often assumed for SMGs and compact starbursts (e.g., (cite: Bothwell2013)). We also calculate the molecular gas mass using \[C I\](1-0) luminosity for M0417-z365 and R0032-z239 following (cite: Umehata2020). The gas masses derived from both CO and \[C I\] luminosities are consistent provided that the $\alpha_{\mathrm{CO}}$ ranges between 1.0 and 3.6. We use CO-based molecular gas mass as a fiducial value.

The gas depletion time $\tau_{\mathrm{dep}}=M_{\mathrm{gas}}/\mathrm{SFR}$ and gas fraction $f_{\mathrm{gas}}=M_{\mathrm{gas}}/M_*$ are also derived in conjunction with the SED fitting results. The obtained values are listed in Table [4](#tab:all_params).

The molecular gas depletion time ($\tau_{\mathrm{dep}}=M_{\mathrm{gas}}/\mathrm{SFR}$) and gas fraction ($f_{\mathrm{gas}}=M_{\mathrm{gas}}/M_*$) depend on redshift, stellar mass, and offset from the main sequence ($\Delta\mathrm{MS}$). (cite: Tacconi2018) compiled molecular gas mass data of star-forming galaxies at $0<z<4$, covering a wide range of stellar mass and $\Delta\mathrm{MS}$ and derived the scaling relations of $\tau_{\mathrm{dep}} \propto (1+z)^{-0.62}\times \Delta\mathrm{MS}^{-0.44}\times M_*^{0.09}$ and $f_{\mathrm{gas}} \propto (1+z)^{2.5}\times \Delta\mathrm{MS}^{0.52}\times M_*^{-0.36}$. Figure [6](#fig:dms_dep_fgas) shows $\tau_{\mathrm{dep}}$ and $f_{\mathrm{gas}}$ as a function of $\Delta\mathrm{MS}$, normalized using the scaling relations. For comparison, we also plot ASPECS DEFGs (cite: Aravena2020), NIR-dark SMGs in literature (cite: Williams2019; Riechers2020; Umehata2020; Sun2024). The gas depletion time and gas fraction of R0032-z299 are consistent with the scaling relation regardless of $\alpha_{\mathrm{CO}}$ value. This suggests that this galaxy is a normal star-forming galaxy undergoing secular evolution. M0417-z365 seems to exhibit a shorter $\tau_{\mathrm{dep}}$ and a smaller $f_{\mathrm{gas}}$, deviating by 0.80 dex and 0.96 dex from the scaling relations, respectively, assuming $\alpha_{\mathrm{CO}} = 1.0$ (0.25 dex and 0.41 dex if $\alpha_{\mathrm{CO}} = 3.6$).

For R0032-z239, these quantities are consistent with the scaling relation when $\alpha_{\mathrm{CO}}$ is close to 1. Examining our results with those of previous literature suggests that the NIR-dark galaxy population has a wide range of molecular gas depletion time and gas fraction.

We will further discuss the interpretations of the molecular gas properties in section [4](#sec:discussion).

Using the molecular gas masses derived above and the dust masses estimated from the SED fitting, we calculate the dust-to-gas mass ratio ($\delta_{\mathrm{GDR}} = M_{\mathrm{dust}} / M_{\mathrm{gas}}$). Assuming $\alpha_{\mathrm{CO}} = 1.0$, the dust-to-gas mass ratios based on CO luminosity are $23 \pm 13$ for M0417-z365, $31 \pm 18$ for R0032-z239, and $23 \pm 14$ for R0032-z299. When compared with the sample of SMGs at $z = 1–5$ presented in (cite: Birkin2021), where molecular gas masses are derived using CO with the assumption of $\alpha_{\mathrm{CO}} = 1.0$, the $\delta_{\mathrm{GDR}}$ values for our sources appear to be smaller, despite the large scatter in the sample. If the $\delta_{\mathrm{GDR}}$ of our sources is comparable to that of the $z=1-5$ SMG sample, this could imply that $\alpha_{\mathrm{CO}}$ for our sources is larger than 1.0.

![](dms_dep_fgas.png)

## Morphology of star-forming region

We reconstruct ALMA band 6 (1.2 mm) continuum images for the three triply lensed systems observed by ALCS using the `glafic` version 2. Ideally, it would be preferable to simultaneously fit the triply lensed images using a single source model. However, galaxy cluster lenses have complex gravitational potential such as small-scale substructures that are not accounted for in the parametric mass model. As a result, the positions of these multiple images typically often deviate by about $\sim 0.5\ensuremath{''}$ (e.g., (cite: Oguri2013)). In this study, we perform individual fittings for each of the three images and then adopt their average value.

First, we refine the lens model by including the multiple images identified in this study as constraints, in addition to those previously recognized. Subsequently, we put a Sérsic source with a Sérsic index $n$ of 1, characterized by six free parameters: $xy$-coordinates, flux, effective radius (half-light radius), major-to-minor axis ratio, and position angle) on the source plane and all source parameters are optimized with the lens parameters hold constant. For $\chi^2$ optimization, only the area within a 3$''$-radius circle centered on each source was considered.

The uncertainty in source reconstruction arises from both the lens model and the observed image. To address the uncertainty of the lens model, we utilize the multitude of lens models generated and accepted via the MCMC method when constructing the lens model as described in Section [3.2](#sec:lensmodel). We repeat the same `glafic` fitting process with these lens models. In addition, to consider the uncertainty of the observed image, we add a randomly generated noise map with the same noise level as the observed image to the best-fit (lensed) model image (which does not include noise; the image in the Model panel of Figure [7](#fig:glafic)) and iterate the fitting. Given the pixel-correlated noise characteristic of interferometric images, we use a noise map convolved with the dirty beam of the ALMA observation. After conducting the fitting procedure 20,000 times in total, we adopt the median value as the best-fit value and use the 16–84% percent interval as the uncertainty. In Appendix [7](#appe:resolution), we further discuss the feasibility of spatially resolving the dust continuum from our ALMA observations.

Figure [7](#fig:glafic) shows the best-fit model for the three triply lensed systems. The obtained intrinsic circularized effective radius $r_e$ and apparent axis ratio for them are listed in Table [4](#tab:all_params).

![](glafic2.png)

Figure [8](#fig:re_fir) shows the relation of the intrinsic infrared luminosities and circularized effective radii for our three samples along with massive ($10^{10.5}\,M_\odot < M_*< 10^{11}\,M_\odot$) MS SFGs at $z\sim 2$ (cite: Rujopakarn2016), faint DSFGs with SFR of 10–100 $M_\odot/\mathrm{yr^{-1}}$ at $z=1-4$ (cite: Gonzalez-Lopez2017; Laporte2017b; Pope2023ApJ...951L..46P; Mizener2024ApJ...970...30M), massive ($M_*>10^{11}\,M_\odot$) DSFGs at $z\sim2$ (cite: Tadaki2020), SCUBA-2 selected SMGs at $z=1-4$ (cite: Gullberg2019; Dudzeviciute2020), and NIR-dark SMGs (cite: Umehata2017; Umehata2020; Gomez2022). While the infrared luminosity of M0417-z365 and R0032-z239 is much lower than that of SMGs, their dust-emitting regions are as compact as those of NIR-dark SMGs. The tendency for compact objects to experience stronger dust attenuation has been suggested by other studies (e.g., (cite: Smail2021; Gomez-Guijarro2023)). On the other hand, R0032-z299, the faintest one in our sample, has a more extended dust continuum of $R_{\mathrm{e, 1.2mm}}=1.3\pm0.3$ kpc. The infrared surface densities of M0417-z365, R0032-z239, and R0032-z299 are $6.6\substack{+7.8 \\ -3.3}\times 10^{11}$, $4.7\substack{+2.9 \\ -1.9}\times 10^{11}$, and $2.8\substack{+2.6 \\ -1.3}\times 10^{10}\,L_\odot\si{kpc^{-2}}$, respectively. We will further discuss the interpretations of the size-luminosity relation in section [4](#sec:discussion).

![](re_fir.png)

+-----------------------------------------------------------------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| Parameters                                                                                                      | M0417-z365                       | R0032-z239                       | R0032-z299                       |
+:========================================================+:======================================================+:================================:+:================================:+:================================:+
| Redshift                                                | $z$                                                   | $3.6517\pm0.0002$                | $2.3911\pm0.0002$                | $2.9853\pm0.0009$                |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| Stellar mass                                            | $\log_{10}(M_*/M_\odot)$                              | $10.37\substack{+0.23 \\ -0.47}$ | $10.04\substack{+0.20 \\ -0.30}$ | $9.82\substack{+0.19 \\ -0.37}$  |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| Infrared luminosity                                     | $\log_{10}(L_{\mathrm{IR}}/L_\odot)$                  | $12.19\substack{+0.14 \\ -0.15}$ | $11.93\substack{+0.14 \\ -0.14}$ | $11.48\substack{+0.14 \\ -0.17}$ |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| Star formation rate (averaged over 100 Myr)             | SFR \[$M_\odot \si{yr^{-1}}$\]                        | $101\substack{+39 \\ -54}$       | $52\substack{+18 \\ -24}$        | $21\substack{+8 \\ -10}$         |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| Dust attenuation                                        | $A_V$ \[mag\]                                         | $4.5\substack{+0.4 \\ -0.4}$     | $4.6\substack{+0.19 \\ -0.20}$   | $4.0\substack{+0.4 \\ -0.5}$     |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| Dust mass                                               | $\log_{10}(M_\mathrm{dust}/M_\odot)$                  | $8.46\substack{+0.14 \\ -0.14}$  | $8.73\substack{+0.14 \\ -0.15}$  | $8.29\substack{+0.14 \\ -0.14}$  |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| Offset from the main sequence                           | $\Delta \mathrm{MS}$                                  | $1.4\substack{+0.5 \\ -0.7}$     | $2.4\substack{+1.1 \\ -0.8}$     | $1.3\substack{+0.5 \\ -0.6}$     |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| Molecular gas mass (CO-based, $\alpha_{\mathrm{CO}}=1$) | $\log_{10}(M_\mathrm{gas}^{\mathrm{CO})}/M_\odot)$    | $9.83\pm0.14$                    | $10.22\pm0.15$                   | $9.66\pm0.16$                    |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| Molecular gas mass (\[C I\]-based)                      | $\log_{10}(M_\mathrm{gas}^{\mathrm{[C I]})}/M_\odot)$ | $9.92\pm0.15$                    | $10.71\pm0.17$                   | $\cdots$                         |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| Gas depletion time ($\alpha_{\mathrm{CO}}=1$)           | $\tau_{\mathrm{gas}}$ \[Gyr\]                         | $0.07\substack{+0.02 \\ -0.03}$  | $0.35\substack{+0.09 \\ -0.14}$  | $0.22\substack{+0.07 \\ -0.10}$  |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| Gas fraction ($\alpha_{\mathrm{CO}}=1$)                 | $f_{\mathrm{gas}}\equiv M_\mathrm{gas}/M_*$           | $0.30\substack{+0.15 \\ -0.32}$  | $1.7\substack{+0.7 \\ -1.1}$     | $0.7\substack{+0.3 \\ -0.6}$     |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| 1.2 mm continuum circularized radius                    | $R_{\mathrm{e, 1.2 mm}}$ \[kpc\]                      | $0.60\substack{+0.14 \\ -0.24}$  | $0.53\substack{+0.06 \\ -0.14}$  | $1.3\substack{+0.3 \\ -0.3}$     |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+
| Apparent axis ratio                                     | $b/a$                                                 | $0.50\substack{+0.27 \\ -0.32}$  | $0.24\substack{+0.04 \\ -0.07}$  | $0.17\substack{+0.11 \\ -0.07}$  |
+---------------------------------------------------------+-------------------------------------------------------+----------------------------------+----------------------------------+----------------------------------+

: Derived intrinsic physical properties for our three samples

## PDR properties

The photodissociation regions (PDRs) play a dominant role in the heating, cooling, ionization, and dissociation of molecules in the neutral interstellar medium (ISM) (cite: TH1985ApJ...291..722T; BT1994ApJ...427..822B).

The heating occurs when far-UV photons penetrate the ISM and are absorbed by Polycyclic Aromatic Hydrocarbons (PAHs). These particles release photoelectrons, which collisionally excite the gas, ultimately converting the energy into dust emission. The gas cooling occurs primarily through FIR fine structure lines, such as \[C II\]$_158$, \[O I\]$_63$, and \[C I\] where the cooling rate depends on the gas density. Thus, we can constrain the gas density $n_{\mathrm{H}}$ and far-UV incident radiation field $U_{\mathrm{UV}}$ in PDRs from the dust luminosity ($\SI{8}{\mu m}<\lambda<\SI{1000}{\mu m}$) and the ratio of CO to \[C I\] luminosity. We perform the PDR modeling for our two samples, M0417-z365 and R0032-z239, which have both CO(4-3) and \[C I\](1-0) line data using the `PDRTToolbox` (cite: Pound2008; Pound2011; Pound2023). The model of (cite: Kaufman2006) with the gas metallicity of $Z=1$ and simple plane-parallel geometry is assumed.

Figure [9](#fig:pdr) shows the model predictions for $L_\mathrm{[C I](1-0)}/L_\mathrm{CO(4-3)}$ against $L_\mathrm{[C I](1-0)}/L_\mathrm{IR}$ together with the observed data of our two samples, previously reported NIR-dark SMGs at $z=3.99$ (cite: Umehata2020) and $z=4.26$ (cite: Smail2023), $z\sim1-5$ bright SMGs (cite: Bothwell2017; Harrington2021; Valentino2020; Hagimoto2023), MS SFGs at $z\sim1$ (cite: Valentino2020), $z\sim2-6.5$ QSOs (cite: Alaghband2013; Bothwell2013), and local U/LIRGs (cite: Michiyama2021). While dust continuum and \[C I\](1–0) emission are generally optically thin, low-$J$ CO emission is optically thick. Thus, we increase the observed CO(4-3) luminosity by a factor of two to incorporate this effect.

M0417-z365 has a lower \[C I\]/CO and \[C I\]/FIR luminosity ratio than R0032-z239 and is located closer to other SMGs than MSs or R0032-z239, indicating a higher gas density and stronger radiation field.

However, we note that the actual ISM would consist of a range of molecular clouds that have different properties like density and radiation field rather than a simple plane-parallel model. Since our measurements are integrated over the whole galaxy, the obtained results should be treated qualitatively.

![](pdr_phaseplot.png)

# Discussion

In this section, we discuss how our three normal dust-obscured galaxies relate to the broader context of galaxy evolution, primarily based on the properties of molecular gas and the morphology of the star-forming regions.

## M0417-z365 and R0032-z239: compact dust-obscured galaxies

Both M0417-z365 and R0032-z239 are main sequence star-forming galaxies and they are characterized by having compact star-forming regions of $\sim 0.6$ kpc, comparable to those of NIR-dark SMGs in literature. The gas depletion time and molecular gas fraction of M0417-z365 seem to be lower than the scaling relation, although those gas properties are consistent with the scaling relation within the margin of error when $\alpha_{\mathrm{CO}}$ is 3.6. We first state an interpretation of the former case. (cite: Elbaz2018) and (cite: Gomez2022) focus on a galaxy population that lies on the MS but has gas depletion times shorter than the scaling relations like starburst (SB) galaxies. They term these galaxies "SBs in the MS" and report that they tend to have a smaller gas fraction and higher dust temperature (but see also (cite: Jin2019; Jin2022; Xiao2023)).

Furthermore, the authors argue that the compactness of the dust continuum area correlates with these characteristics: As the star-forming region becomes more compact compared to the stellar disk, the gas depletion timescale and gas fraction become lower (see also (cite: Jimenez2019)). To phenomenologically explain this galaxy population, (cite: Gomez2022) propose a scenario in which the galaxy exhausts its gas from the outside and, through some mechanism, gradually becomes more compact. However, this is not confirmed observationally (cite: Ciesla2022).

Next, we present an interpretation of the latter case. The molecular gas properties of R0032-z239 are also aligned with the scaling relation when $\alpha_{\mathrm{CO}}$ close to 1. This case can be interpreted as being in a compaction phase of a steady galaxy evolution scenario for MS galaxies, proposed by cosmological simulations (e.g., (cite: Zolotov2015; Tacchella2016a)). In this scenario, the galaxy experiences compaction of gas and star formation triggered by an intense gas inflow event such as minor mergers or counter-rotating streams. This phase is then followed by inside-out quenching driven by outflows and central gas depletion. These processes are repeated until the halo mass grows sufficiently to halt cold gas accretion from the intergalactic medium. Throughout these cycles, the galaxy remains MS on the SFR–$M_*$ plane and upholds the scaling relations for gas depletion time and gas fraction.

Both M0417-z365 and R0032-z239 have compact star-forming regions, which aligns with prior studies suggesting a correlation between compactness and the strength of dust attenuation (cite: Smail2021). However, based only on our current results, it is unclear whether this compactness is the actual cause of the strong dust attenuation observed in these galaxies.

## R0032-z299: a normal DSFG with edge-on disk

R0032-z299, the faintest source in our sample, is a LIRG-class MS SFG and its gas depletion time and gas fraction are consistent with the scaling relation, which suggests that this galaxy is under secular evolution. This source has a dust continuum that is roughly twice as extended as the other two samples and NIR-dark SMGs in the literature. Its infrared surface brightness of $\Sigma_{\mathrm{IR}}=2.8\substack{+2.6 \\ -1.3}\times 10^{10}\,L_\odot\si{kpc^{-2}}$ is more than an order of magnitude lower. The FIR size–luminosity relation at $z\gtrsim2$ is not well constrained at the faint end of $L_{\mathrm{IR}}<10^{12}L_\odot$. While (cite: Fujimoto2017) postulates in their statistical ALMA study that fainter galaxies tend to be smaller, (cite: Gonzalez-Lopez2017) and (cite: Rujopakarn2016) report that, despite large scatter, the FIR sizes of fainter DSFGs at $z\sim1-2$ are either comparable to or exceed those of brighter SMGs. In the local universe, the IR-size relation has been investigated down to $L_{\text{IR}} \sim 10^{10} L_\odot$, suggesting that galaxies with lower $L_{\text{IR}}$ tend to have larger sizes (cite: McKinney2023ApJ...955..136M).

(cite: Gullberg2019) stacks dust continuum of SCUBA-2 detected bright SMGs to find not only a central compact (sub-kpc) component but also a fainter extended component extending about a few kpc associated with (unobscured) star and molecular gas. The infrared surface brightness of the compact and extended components are about $(6-10)\times 10^{11}$ and $1\times 10^{10}\,L_\odot\,\mathrm{kpc^{-2}}$, respectively. As the SFR increases, the infrared surface brightness of the compact component shows a rising trend, while that of the extended component remains constant. Based on this result and simulation works (e.g., (cite: Hopkins2013)), the authors argue that the two components are physically decoupled. They suggest that the compact component likely represents a merger-induced starburst triggered by radial gas inflow that loses its angular momentum. Meanwhile, the extended component seems to be a regular disk that had formed before the merger.

The infrared surface brightness of R0032-z299 is comparable to that of the extended component identified by (cite: Gullberg2019) and those of faint ($L_{\mathrm{IR}}\lesssim 10^{12}L_\odot$) DSFGs (cite: Rujopakarn2016; Gonzalez-Lopez2017). Together with the normal molecular gas properties, we interpret that R0032-z299 is in a secular evolution phase prior to an outside-in transformation caused by mergers or violent disk instability.

Another characteristic of this source is its elongated projected axis ratio of 0.17, the most elongated of our three samples.

If we assume axisymmetry, R0032-z299 is likely to be a dusty edge-on disk, although there is another case that even a face-on galaxy can appear elongated if we are viewing a bar-like structure (e.g., (cite: Hodge2019; Huang2023b)). Nonetheless, to explain the origin of the strong dust attenuation ($A_V\sim4$), we interpret that this galaxy has an extended dusty edge-on disk, which causes the stellar light to be strongly attenuated by the large dust column density (cite: Wang2018). This interpretation suggests that even normal dusty star-forming galaxies can be strongly dust-obscured and missed in optical/NIR observations, depending on the orientation to the observer. Recently, a *JWST* study discovered a *HST*-dark galaxy population with similar properties to R0032-z299: massive ($M_*\gtrsim 10^{10}\,M_\odot$), extended ($R_{\mathrm{e,F444W}}\sim1-2$ kpc), and edge-on disk galaxies (cite: Nelson2023).

We think that these *JWST*/NIRCam selected *HST*-dark galaxies and R0032-z299 are the same population and that our ALMA observations directly capture the dust responsible for the attenuation. These were identified in the early observations of *JWST*, suggesting that such a galaxy population is not uncommon. The geometric orientation–whether a galaxy is observed from an edge-on angle or not–would not be the only factor of the strong dust attenuation (cite: Lorenz2023; Gomez-Guijarro2023; Fujimoto2023b), but in massive galaxies where a disk is present, the edge-on disk orientation may be a significant factor contributing to dust attenuation. However, it should be noted that a recent simulation study predicts that edge-on disks tend to have less dust attenuation because stellar light escapes from the edges of the dust distribution (cite: Cochrane2023). In the near future, we expect that deep multi-band observation with a high angular resolution by *HST*, *JWST*, and ALMA will statistically reveal the detailed properties of dust-obscured galaxies and the origins of strong dust attenuation by directly comparing the spatial distribution of stars and dust. It would also be important to break the degeneracy between dust mass and dust temperature by observing the dust continuum with multiple bands.

# Summary

We present spectroscopic redshifts and physical characterizations of three triply lensed dust-obscured galaxies that are originally detected in the ALCS program. The multiple images are apparently bright at 1.2 mm band but intrinsically faint ($S_{\SI{1.2}{mm}}<\SI{1}{mJy}$) compared with classical SMGs due to the lens magnifications.

We perform ALMA band 3/4 line scan follow-up observations and successfully confirm the spectroscopic redshifts to be $z=3.6517$, 2.3911, and 2.9853 for M0417-z365, R0032-z239, and R0032-z299, respectively. We also conduct follow-up observations toward the triply lensed sources in M0417 with the SCUBA-2/450, 850 $\mu$m and FourStar/K-band to collect more multi-band photometries. Together with archival *HST*, *Spitzer*/IRAC, Herschel/SPIRE, VLT/HAWK-I data, the stellar masses, SFRs, and visual extinctions are derived from panchromatic SED fitting. Thanks to a total magnification factor of up to $\sim15$, we were able to detect faint CO emission lines and estimate the gas mass.

Our three samples are located in the MS region in the $M_*$–SFR plane, with lower $M_*$ and SFR than classical SMGs. They show a variety in molecular gas depletion time, gas fraction, and spatial extent of dust.

M0417-z365 and R0032-z239 have compact 1.2 mm dust size of $\sim 0.6$ kpc, comparable to those of previously reported NIR-dark SMGs, following a proposed trend that the more compact the dust continuum size, the higher the $A_V$. On the other hand, the dust continuum of R0032-z299 is roughly twice as extended as the other two samples and NIR-dark SMGs in the literature. Its infrared surface brightness is more than an order of magnitude lower than the other two samples and SMGs, which suggests that R0032-z299 is a different population. The molecular gas depletion time and gas fraction of R0032-z299 are consistent with a scaling relation for star-forming galaxies, suggesting this galaxy undergoes a secular evolution phase. R0032-z299 has an elongated projected axis ratio of $\sim 0.17$, the most elongated of our three samples. This suggests that the edge-on dusty disk configuration causes strong dust attenuation. If so, even normal DSFGs can be strongly dust-obscured and missed in optical/NIR observations, depending on the orientation to the observer.

# Acknowledgments

We thank Masato Hagimoto for providing us with the \[C I\](1-0)/CO(4-3)/FIR data. We appreciate Takeo Minezaki for constructive comments and suggestions. We also sincerely thank the anonymous referee for constructive comments and suggestions, which have improved the quality of this paper. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00035.L, #2019.1.00949.S, and #2021.1.01246.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work is based (in part) on data collected at the Magellan Telescopes, with the support from the ALTA program of ASIAA. Data analysis was in part carried out on the Multi-wavelength Data Analysis System operated by the Astronomy Data Center (ADC), NAOJ. This research was supported by FoPM, WINGS Program, the University of Tokyo. AT was supported by the ALMA Japan Research Grant of NAOJ ALMA Project, NAOJ-ALMA-343. AT also acknowledges the support by JSPS KAKENHI Grant Number 24KJ0562. KK acknowledges the support by JSPS KAKENHI Grant Number JP17H06130 and JP22H04939, and the NAOJ ALMA Scientific Research Grant Number 2017-06B. HU appreciates the support by JSPS KAKENHI Grant Number 20H01953, 22KK0231, and 23K20240. WHW and ZKG acknowledge support by NSTC grant 111-2112-M-001-052-MY3. FS acknowledges JWST/NIRCam contract to the University of Arizona NAS5-02015. RU appreciates the support by JSPS KAKENHI Grant Number 22J22795. FEB acknowledges support from ANID-Chile BASAL CATA FB210003, FONDECYT Regular 1200495, and Millennium Science Initiative Program – ICN12_009.

# Facilities

HST (ACS and WFC3), Magellan (FourStar), VLT (HAWK-I), Spitzer (IRAC), Herschel (PACS), JCMT (SCUBA-2), ALMA

# Software

Astropy (cite: astropy:2022), Glafic (cite: Oguri2010), CASA (cite: McMullin2007), Photutils (cite: photutils), SExtractor (cite: Bertin1996), PSFEx (cite: Bertin2011), CIGALE (cite: Boquien2019),

PDRToolbox (cite: Pound2023), Dynesty (cite: Speagle2020),

# SED fitting

Table [\[tab:param_cigale\]](#tab:param_cigale) lists the parameter ranges used for our sed fitting. Figure [10](#fig:sed) shows the sed fit results for all our sources.

+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Parameter                                                            | Symbol                | Value                                              |
+:=====================================================================+:======================+:===================================================+
| SFH (`nonparametric`; (cite: Leja2019))                                                                                                           |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Number of constant SFH bins                                          |                       | 6                                                  |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Prior                                                                |                       | Continuity                                         |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
|                                                                      |                       | (SFR$_n$/SFR$_{n+1}\sim$ Student’s-t distribution) |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| SSP (`bc03`; (cite: Bruzual2003))                                                                                                                 |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Initial mass function                                                | IMF                   | (cite: Chabrier2003)                               |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Metallicity of the stellar model                                     | $Z_{\text{star}}$     | 0.02                                               |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Nebular emission (`nebular`)                                                                                                                      |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Ionisation parameter                                                 | $\log U$              | -2.0                                               |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Gas Metallicity                                                      | $Z_{\text{gas}}$      | 0.02                                               |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Electron density                                                     | $n_e$ \[cm^−3^\]      | 100                                                |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Dust attenuation (`dustatt_calzleit`; (cite: Calzetti2000))                                                                                       |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Color excess of the stellar continuum light for the young population | E(B-V)$_*$            | 0–10                                               |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Reduction factor to apply E(B-V)$_*$ for the old population          |                       | 0–1                                                |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| UV bump amplitude                                                    |                       | 0                                                  |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Slope of the power law modifying the attenuation curve               | $\delta$              | -0.7–0.4                                           |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Dust emission (`dl14`; (cite: Draine2014))                                                                                                        |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Mass fraction of Polycyclic Aromatic Hydrocarbons (PAH)              | $q_{PAH}$             | 0.47, 1.12, 2.50, 3.19, 3.90                       |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Minimum radiation field                                              | $U_{\text{min}}$      | All possible values above 5.0                      |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Power-law index of starlight intensity distribution                  | $\alpha$              | All possible values (1.0–3.0)                      |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+
| Fraction illuminated from $U_{\text{min}}$ to $U_{\text{max}}$       | $1-\gamma$            | 0–1                                                |
+----------------------------------------------------------------------+-----------------------+----------------------------------------------------+

![](sed.png)

# Intrinsic dust continuum size

In section [3.5](#sec:morphology), we reconstructed the intrinsic source morphology of the 1.2 mm continuum from ALCS observations using a MCMC approach. Here, we discuss an alternative method to demonstrate that the ALCS observations, with a resolution of $\sim1\ensuremath{''}$, are capable of spatially resolving structures with $r_e\sim0.5$ kpc.

In principle, it is possible to resolve sources smaller than the beam if the beam profile is well-defined, the SNR is sufficiently high, and some assumptions about the source light profile are made. (cite: Simpson2015) demonstrated that when the source size is close to the synthesized beam size and a peak SNR is more than $\sim 10$, source sizes can be recovered with a precision of $\sim30$%. (cite: Tsujita2022PASJ...74.1429T) demonstrated that, in the presence of strong lensing, it is possible to measure source sizes even when they are smaller than the effective beam size. The minimum radius $r_{\text{min}}$ that can be reliably measured can be expressed as follows (cite: MV2012A&A...541A.135M; Gomez2022): $r_{\text{min}}\simeq0.44~ \theta_{\text{beam}}/\sqrt{\text{SNR}}$, where $\theta_{\text{beam}}$ is the FWHM of the beam. Note that the effective angular resolution is improved by a factor of $\sqrt{\mu}$ due to the strong lensing. For example, M0417-z365.ID46 has a magnification factor of $\mu = 5.1$ (Table [2](#tab:line_property)) and a peak SNR of $\sim50$ (cite: Fujimoto2024ApJS..275...36F). Substituting these values into the above equation yields $r_{\text{min}}\sim0.03\ensuremath{''}$, which corresponds to $\sim0.2$ kpc at $z=3.652$. This calculation demonstrates that this source is indeed resolvable with our observations.

Similarly, for M0417-z365.ID58 and M0417-z365.ID121, we obtain $r_{\text{min}} \sim 0.3$ kpc and $\sim 0.4$ kpc at $z = 3.652$, respectively. For R0032-z239.ID127, R0032-z239.ID131, and R0032-z239.ID198, the calculations yield $r_{\text{min}} \sim 0.2$ kpc, $\sim 0.2$ kpc, and $\sim 0.5$ kpc at $z = 2.391$, respectively. Likewise, for R0032-z239.ID208, R0032-z239.ID281, and R0032-z239.ID304, we obtain $r_{\text{min}} \sim 0.4$ kpc, $\sim 0.5$ kpc, and $\sim 0.6$ kpc at $z = 2.985$. These results confirm that all sources in our sample are spatially resolved.

natexlab

(ref: Acebron2020) Acebron, A., Zitrin, A., Coe, D., et al. 2020, ApJ, 898, 6, doi: [`10.3847/1538-4357/ab929d`](http://doi.org/10.3847/1538-4357/ab929d)

(ref: Alaghband2013) Alaghband-Zadeh, S., Chapman, S. C., Swinbank, A. M., et al. 2013, MNRAS, 435, 1493, doi: [`10.1093/mnras/stt1390`](http://doi.org/10.1093/mnras/stt1390)

(ref: Alcalde2019) Alcalde Pampliega, B., Pérez-González, P. G., Barro, G., et al. 2019, ApJ, 876, 135, doi: [`10.3847/1538-4357/ab14f2`](http://doi.org/10.3847/1538-4357/ab14f2)

(ref: Aravena2019) Aravena, M., Decarli, R., Gónzalez-López, J., et al. 2019, ApJ, 882, 136, doi: [`10.3847/1538-4357/ab30df`](http://doi.org/10.3847/1538-4357/ab30df)

(ref: Aravena2020) Aravena, M., Boogaard, L., Gónzalez-López, J., et al. 2020, ApJ, 901, 79, doi: [`10.3847/1538-4357/ab99a2`](http://doi.org/10.3847/1538-4357/ab99a2)

(ref: astropy:2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, apj, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: BT1994ApJ...427..822B) Bakes, E. L. O., & Tielens, A. G. G. M. 1994, ApJ, 427, 822, doi: [`10.1086/174188`](http://doi.org/10.1086/174188)

(ref: Bakx2022) Bakx, T. J. L. C., & Dannerbauer, H. 2022, MNRAS, 515, 678, doi: [`10.1093/mnras/stac1306`](http://doi.org/10.1093/mnras/stac1306)

(ref: Barrufet2023) Barrufet, L., Oesch, P. A., Weibel, A., et al. 2023, MNRAS, 522, 449, doi: [`10.1093/mnras/stad947`](http://doi.org/10.1093/mnras/stad947)

(ref: Barrufet2024arXiv240408052B) Barrufet, L., Oesch, P., Marques-Chaves, R., et al. 2024, arXiv e-prints, arXiv:2404.08052, doi: [`10.48550/arXiv.2404.08052`](http://doi.org/10.48550/arXiv.2404.08052)

(ref: Bertin2011) Bertin, E. 2011, in Astronomical Society of the Pacific Conference Series, Vol. 442, Astronomical Data Analysis Software and Systems XX, ed. I. N. Evans, A. Accomazzi, D. J. Mink, & A. H. Rots, 435

(ref: Bertin1996) Bertin, E., & Arnouts, S. 1996, A&AS, 117, 393, doi: [`10.1051/aas:1996164`](http://doi.org/10.1051/aas:1996164)

(ref: Birkin2021) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021, MNRAS, 501, 3926, doi: [`10.1093/mnras/staa3862`](http://doi.org/10.1093/mnras/staa3862)

(ref: Boogaard2020) Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020, ApJ, 902, 109, doi: [`10.3847/1538-4357/abb82f`](http://doi.org/10.3847/1538-4357/abb82f)

(ref: Boquien2019) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103, doi: [`10.1051/0004-6361/201834156`](http://doi.org/10.1051/0004-6361/201834156)

(ref: Bothwell2013) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, MNRAS, 429, 3047, doi: [`10.1093/mnras/sts562`](http://doi.org/10.1093/mnras/sts562)

(ref: Bothwell2017) Bothwell, M. S., Aguirre, J. E., Aravena, M., et al. 2017, MNRAS, 466, 2825, doi: [`10.1093/mnras/stw3270`](http://doi.org/10.1093/mnras/stw3270)

(ref: Bourne2019) Bourne, N., Dunlop, J. S., Simpson, J. M., et al. 2019, MNRAS, 482, 3135, doi: [`10.1093/mnras/sty2773`](http://doi.org/10.1093/mnras/sty2773)

(ref: Bouwens2012) Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2012, ApJ, 754, 83, doi: [`10.1088/0004-637X/754/2/83`](http://doi.org/10.1088/0004-637X/754/2/83)

(ref: photutils) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2022, astropy/photutils: 1.5.0, 1.5.0, Zenodo, doi: [`10.5281/zenodo.6825092`](http://doi.org/10.5281/zenodo.6825092)

(ref: Bruzual2003) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000, doi: [`10.1046/j.1365-8711.2003.06897.x`](http://doi.org/10.1046/j.1365-8711.2003.06897.x)

(ref: Calzetti2000) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: Caputi2012) Caputi, K. I., Dunlop, J. S., McLure, R. J., et al. 2012, ApJL, 750, L20, doi: [`10.1088/2041-8205/750/1/L20`](http://doi.org/10.1088/2041-8205/750/1/L20)

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Casey2019) Casey, C. M., Zavala, J. A., Aravena, M., et al. 2019, ApJ, 887, 55, doi: [`10.3847/1538-4357/ab52ff`](http://doi.org/10.3847/1538-4357/ab52ff)

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Chapin2013) Chapin, E., Gibb, A. G., Jenness, T., et al. 2013, Starlink User Note, 258

(ref: Ciesla2022) Ciesla, L., Gómez-Guijarro, C., Buat, V., et al. 2022, arXiv e-prints, arXiv:2211.02510. [`https://arxiv.org/abs/2211.02510`](https://arxiv.org/abs/2211.02510)

(ref: Cochrane2023) Cochrane, R. K., Anglés-Alcázar, D., Cullen, F., & Hayward, C. C. 2023, arXiv e-prints, arXiv:2310.08829, doi: [`10.48550/arXiv.2310.08829`](http://doi.org/10.48550/arXiv.2310.08829)

(ref: Coe2019) Coe, D., Salmon, B., Bradač, M., et al. 2019, ApJ, 884, 85, doi: [`10.3847/1538-4357/ab412b`](http://doi.org/10.3847/1538-4357/ab412b)

(ref: dacunha2015) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110, doi: [`10.1088/0004-637X/806/1/110`](http://doi.org/10.1088/0004-637X/806/1/110)

(ref: Draine2014) Draine, B. T., Aniano, G., Krause, O., et al. 2014, ApJ, 780, 172, doi: [`10.1088/0004-637X/780/2/172`](http://doi.org/10.1088/0004-637X/780/2/172)

(ref: Dudzeviciute2020) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828, doi: [`10.1093/mnras/staa769`](http://doi.org/10.1093/mnras/staa769)

(ref: Egami2010) Egami, E., Rex, M., Rawle, T. D., et al. 2010, A&A, 518, L12, doi: [`10.1051/0004-6361/201014696`](http://doi.org/10.1051/0004-6361/201014696)

(ref: Elbaz2018) Elbaz, D., Leiton, R., Nagar, N., et al. 2018, A&A, 616, A110, doi: [`10.1051/0004-6361/201732370`](http://doi.org/10.1051/0004-6361/201732370)

(ref: Franco2018) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152, doi: [`10.1051/0004-6361/201832928`](http://doi.org/10.1051/0004-6361/201832928)

(ref: Fudamoto2017) Fudamoto, Y., Ivison, R. J., Oteo, I., et al. 2017, MNRAS, 472, 2028, doi: [`10.1093/mnras/stx1956`](http://doi.org/10.1093/mnras/stx1956)

(ref: Fudamoto2021) Fudamoto, Y., Oesch, P. A., Schouws, S., et al. 2021, Nature, 597, 489, doi: [`10.1038/s41586-021-03846-z`](http://doi.org/10.1038/s41586-021-03846-z)

(ref: Fujimoto2016) Fujimoto, S., Ouchi, M., Ono, Y., et al. 2016, ApJS, 222, 1, doi: [`10.3847/0067-0049/222/1/1`](http://doi.org/10.3847/0067-0049/222/1/1)

(ref: Fujimoto2017) Fujimoto, S., Ouchi, M., Shibuya, T., & Nagai, H. 2017, ApJ, 850, 83, doi: [`10.3847/1538-4357/aa93e6`](http://doi.org/10.3847/1538-4357/aa93e6)

(ref: Fujimoto2023b) Fujimoto, S., Bezanson, R., Labbe, I., et al. 2023, arXiv e-prints, arXiv:2309.07834, doi: [`10.48550/arXiv.2309.07834`](http://doi.org/10.48550/arXiv.2309.07834)

(ref: Fujimoto2024ApJS..275...36F) Fujimoto, S., Kohno, K., Ouchi, M., et al. 2024, ApJS, 275, 36, doi: [`10.3847/1538-4365/ad5ae2`](http://doi.org/10.3847/1538-4365/ad5ae2)

(ref: Gomez2022) Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022, A&A, 659, A196, doi: [`10.1051/0004-6361/202142352`](http://doi.org/10.1051/0004-6361/202142352)

(ref: Gomez-Guijarro2023) Gómez-Guijarro, C., Magnelli, B., Elbaz, D., et al. 2023, arXiv e-prints, arXiv:2304.08517, doi: [`10.48550/arXiv.2304.08517`](http://doi.org/10.48550/arXiv.2304.08517)

(ref: Gonzalez-Lopez2017) González-López, J., Bauer, F. E., Romero-Cañizales, C., et al. 2017, A&A, 597, A41, doi: [`10.1051/0004-6361/201628806`](http://doi.org/10.1051/0004-6361/201628806)

(ref: Gruppioni2020) Gruppioni, C., Béthermin, M., Loiacono, F., et al. 2020, A&A, 643, A8, doi: [`10.1051/0004-6361/202038487`](http://doi.org/10.1051/0004-6361/202038487)

(ref: Gullberg2019) Gullberg, B., Smail, I., Swinbank, A. M., et al. 2019, MNRAS, 490, 4956, doi: [`10.1093/mnras/stz2835`](http://doi.org/10.1093/mnras/stz2835)

(ref: Habing1968) Habing, H. J. 1968, , 19, 421

(ref: Hagimoto2023) Hagimoto, M., Bakx, T. J. L. C., Serjeant, S., et al. 2023, MNRAS, 521, 5508, doi: [`10.1093/mnras/stad784`](http://doi.org/10.1093/mnras/stad784)

(ref: Harrington2021) Harrington, K. C., Weiss, A., Yun, M. S., et al. 2021, ApJ, 908, 95, doi: [`10.3847/1538-4357/abcc01`](http://doi.org/10.3847/1538-4357/abcc01)

(ref: Hatsukade2015) Hatsukade, B., Ohta, K., Yabe, K., et al. 2015, ApJ, 810, 91, doi: [`10.1088/0004-637X/810/2/91`](http://doi.org/10.1088/0004-637X/810/2/91)

(ref: Hodge2020) Hodge, J. A., & da Cunha, E. 2020, Royal Society Open Science, 7, 200556, doi: [`10.1098/rsos.200556`](http://doi.org/10.1098/rsos.200556)

(ref: Hodge2019) Hodge, J. A., Smail, I., Walter, F., et al. 2019, ApJ, 876, 130, doi: [`10.3847/1538-4357/ab1846`](http://doi.org/10.3847/1538-4357/ab1846)

(ref: Hopkins2013) Hopkins, P. F., Cox, T. J., Hernquist, L., et al. 2013, MNRAS, 430, 1901, doi: [`10.1093/mnras/stt017`](http://doi.org/10.1093/mnras/stt017)

(ref: Huang2023) Huang, S., Umehata, H., Kawabe, R., et al. 2023a, ApJ, 953, 75, doi: [`10.3847/1538-4357/ace0c0`](http://doi.org/10.3847/1538-4357/ace0c0)

(ref: Huang2023b) Huang, S., Kawabe, R., Kohno, K., et al. 2023b, ApJL, 958, L26, doi: [`10.3847/2041-8213/acff63`](http://doi.org/10.3847/2041-8213/acff63)

(ref: Jimenez2019) Jiménez-Andrade, E. F., Magnelli, B., Karim, A., et al. 2019, A&A, 625, A114, doi: [`10.1051/0004-6361/201935178`](http://doi.org/10.1051/0004-6361/201935178)

(ref: Jin2019) Jin, S., Daddi, E., Magdis, G. E., et al. 2019, ApJ, 887, 144, doi: [`10.3847/1538-4357/ab55d6`](http://doi.org/10.3847/1538-4357/ab55d6)

(ref: Jin2022) —. 2022, A&A, 665, A3, doi: [`10.1051/0004-6361/202243341`](http://doi.org/10.1051/0004-6361/202243341)

(ref: Kaufman2006) Kaufman, M. J., Wolfire, M. G., & Hollenbach, D. J. 2006, ApJ, 644, 283, doi: [`10.1086/503596`](http://doi.org/10.1086/503596)

(ref: Kawamata2016) Kawamata, R., Oguri, M., Ishigaki, M., Shimasaku, K., & Ouchi, M. 2016, ApJ, 819, 114, doi: [`10.3847/0004-637X/819/2/114`](http://doi.org/10.3847/0004-637X/819/2/114)

(ref: Kohno2023) Kohno, K., Fujimoto, S., Tsujita, A., et al. 2023, in Physics and Chemistry of Star Formation: The Dynamical ISM Across Time and Spatial Scales, 16

(ref: Kokorev2022) Kokorev, V., Brammer, G., Fujimoto, S., et al. 2022, ApJS, 263, 38, doi: [`10.3847/1538-4365/ac9909`](http://doi.org/10.3847/1538-4365/ac9909)

(ref: Kokorev2023) Kokorev, V., Jin, S., Magdis, G. E., et al. 2023, ApJL, 945, L25, doi: [`10.3847/2041-8213/acbd9d`](http://doi.org/10.3847/2041-8213/acbd9d)

(ref: Lagos2020) Lagos, C. d. P., da Cunha, E., Robotham, A. S. G., et al. 2020, MNRAS, 499, 1948, doi: [`10.1093/mnras/staa2861`](http://doi.org/10.1093/mnras/staa2861)

(ref: Laporte2017b) Laporte, N., Bauer, F. E., Troncoso-Iribarren, P., et al. 2017, A&A, 604, A132, doi: [`10.1051/0004-6361/201730628`](http://doi.org/10.1051/0004-6361/201730628)

(ref: Leja2019) Leja, J., Carnall, A. C., Johnson, B. D., Conroy, C., & Speagle, J. S. 2019, ApJ, 876, 3, doi: [`10.3847/1538-4357/ab133c`](http://doi.org/10.3847/1538-4357/ab133c)

(ref: Lorenz2023) Lorenz, B., Kriek, M., Shapley, A. E., et al. 2023, ApJ, 951, 29, doi: [`10.3847/1538-4357/accdd1`](http://doi.org/10.3847/1538-4357/accdd1)

(ref: Lotz2017) Lotz, J. M., Koekemoer, A., Coe, D., et al. 2017, ApJ, 837, 97, doi: [`10.3847/1538-4357/837/1/97`](http://doi.org/10.3847/1538-4357/837/1/97)

(ref: Madau2014) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: Mahler2019) Mahler, G., Sharon, K., Fox, C., et al. 2019, ApJ, 873, 96, doi: [`10.3847/1538-4357/ab042b`](http://doi.org/10.3847/1538-4357/ab042b)

(ref: Manning2022) Manning, S. M., Casey, C. M., Zavala, J. A., et al. 2022, ApJ, 925, 23, doi: [`10.3847/1538-4357/ac366a`](http://doi.org/10.3847/1538-4357/ac366a)

(ref: MV2012A&A...541A.135M) Martı́-Vidal, I., Pérez-Torres, M. A., & Lobanov, A. P. 2012, A&A, 541, A135, doi: [`10.1051/0004-6361/201118334`](http://doi.org/10.1051/0004-6361/201118334)

(ref: McKinney2023ApJ...956...72M) McKinney, J., Manning, S. M., Cooper, O. R., et al. 2023a, ApJ, 956, 72, doi: [`10.3847/1538-4357/acf614`](http://doi.org/10.3847/1538-4357/acf614)

(ref: McKinney2023ApJ...955..136M) McKinney, J., Pope, A., Kirkpatrick, A., et al. 2023b, ApJ, 955, 136, doi: [`10.3847/1538-4357/ace25c`](http://doi.org/10.3847/1538-4357/ace25c)

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Michiyama2021) Michiyama, T., Saito, T., Tadaki, K.-i., et al. 2021, ApJS, 257, 28, doi: [`10.3847/1538-4365/ac16df`](http://doi.org/10.3847/1538-4365/ac16df)

(ref: Mizener2024ApJ...970...30M) Mizener, A., Pope, A., McKinney, J., et al. 2024, ApJ, 970, 30, doi: [`10.3847/1538-4357/ad4965`](http://doi.org/10.3847/1538-4357/ad4965)

(ref: Nelson2023) Nelson, E. J., Suess, K. A., Bezanson, R., et al. 2023, ApJL, 948, L18, doi: [`10.3847/2041-8213/acc1e1`](http://doi.org/10.3847/2041-8213/acc1e1)

(ref: Oguri2010) Oguri, M. 2010, PASJ, 62, 1017, doi: [`10.1093/pasj/62.4.1017`](http://doi.org/10.1093/pasj/62.4.1017)

(ref: Oguri2021) —. 2021, PASP, 133, 074504, doi: [`10.1088/1538-3873/ac12db`](http://doi.org/10.1088/1538-3873/ac12db)

(ref: Oguri2013) Oguri, M., Schrabback, T., Jullo, E., et al. 2013, MNRAS, 429, 482, doi: [`10.1093/mnras/sts351`](http://doi.org/10.1093/mnras/sts351)

(ref: Okabe2020) Okabe, T., Oguri, M., Peirani, S., et al. 2020, MNRAS, 496, 2591, doi: [`10.1093/mnras/staa1479`](http://doi.org/10.1093/mnras/staa1479)

(ref: Oke1974) Oke, J. B. 1974, ApJS, 27, 21, doi: [`10.1086/190287`](http://doi.org/10.1086/190287)

(ref: Perez-Gonzalez2023ApJ) Pérez-González, P. G., Barro, G., Annunziatella, M., et al. 2023, ApJL, 946, L16, doi: [`10.3847/2041-8213/acb3a5`](http://doi.org/10.3847/2041-8213/acb3a5)

(ref: Pope2017ApJ...838..137P) Pope, A., Montaña, A., Battisti, A., et al. 2017, ApJ, 838, 137, doi: [`10.3847/1538-4357/aa6573`](http://doi.org/10.3847/1538-4357/aa6573)

(ref: Pope2023ApJ...951L..46P) Pope, A., McKinney, J., Kamieneski, P., et al. 2023, ApJL, 951, L46, doi: [`10.3847/2041-8213/acdf5a`](http://doi.org/10.3847/2041-8213/acdf5a)

(ref: Postman2012) Postman, M., Coe, D., Benı́tez, N., et al. 2012, ApJS, 199, 25, doi: [`10.1088/0067-0049/199/2/25`](http://doi.org/10.1088/0067-0049/199/2/25)

(ref: Pound2008) Pound, M. W., & Wolfire, M. G. 2008, in Astronomical Society of the Pacific Conference Series, Vol. 394, Astronomical Data Analysis Software and Systems XVII, ed. R. W. Argyle, P. S. Bunclark, & J. R. Lewis, 654

(ref: Pound2011) Pound, M. W., & Wolfire, M. G. 2011, PDRT: Photo Dissociation Region Toolbox. [`http://ascl.net/1102.022`](http://ascl.net/1102.022)

(ref: Pound2023) —. 2023, AJ, 165, 25, doi: [`10.3847/1538-3881/ac9b1f`](http://doi.org/10.3847/1538-3881/ac9b1f)

(ref: Riechers2020) Riechers, D. A., Hodge, J. A., Pavesi, R., et al. 2020, ApJ, 895, 81, doi: [`10.3847/1538-4357/ab8c48`](http://doi.org/10.3847/1538-4357/ab8c48)

(ref: Romano2020) Romano, M., Cassata, P., Morselli, L., et al. 2020, MNRAS, 496, 875, doi: [`10.1093/mnras/staa1546`](http://doi.org/10.1093/mnras/staa1546)

(ref: Rujopakarn2016) Rujopakarn, W., Dunlop, J. S., Rieke, G. H., et al. 2016, ApJ, 833, 12, doi: [`10.3847/0004-637X/833/1/12`](http://doi.org/10.3847/0004-637X/833/1/12)

(ref: Salpeter1955) Salpeter, E. E. 1955, ApJ, 121, 161, doi: [`10.1086/145971`](http://doi.org/10.1086/145971)

(ref: Schreiber2015) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74, doi: [`10.1051/0004-6361/201425017`](http://doi.org/10.1051/0004-6361/201425017)

(ref: Shu2022) Shu, X., Yang, L., Liu, D., et al. 2022, ApJ, 926, 155, doi: [`10.3847/1538-4357/ac3de5`](http://doi.org/10.3847/1538-4357/ac3de5)

(ref: Simpson2014) Simpson, J. M., Swinbank, A. M., Smail, I., et al. 2014, ApJ, 788, 125, doi: [`10.1088/0004-637X/788/2/12510.48550/arXiv.1310.6363`](http://doi.org/10.1088/0004-637X/788/2/12510.48550/arXiv.1310.6363)

(ref: Simpson2015) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2015, ApJ, 799, 81, doi: [`10.1088/0004-637X/799/1/81`](http://doi.org/10.1088/0004-637X/799/1/81)

(ref: Smail1999) Smail, I., Ivison, R. J., Kneib, J. P., et al. 1999, MNRAS, 308, 1061, doi: [`10.1046/j.1365-8711.1999.02819.x10.48550/arXiv.astro-ph/9905246`](http://doi.org/10.1046/j.1365-8711.1999.02819.x10.48550/arXiv.astro-ph/9905246)

(ref: Smail2021) Smail, I., Dudzevičiūtė, U., Stach, S. M., et al. 2021, MNRAS, 502, 3426, doi: [`10.1093/mnras/stab283`](http://doi.org/10.1093/mnras/stab283)

(ref: Smail2023) Smail, I., Dudzevičiūtė, U., Gurwell, M., et al. 2023, ApJ, 958, 36, doi: [`10.3847/1538-4357/acf931`](http://doi.org/10.3847/1538-4357/acf931)

(ref: Speagle2020) Speagle, J. S. 2020, MNRAS, 493, 3132, doi: [`10.1093/mnras/staa278`](http://doi.org/10.1093/mnras/staa278)

(ref: Speagle2014) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15, doi: [`10.1088/0067-0049/214/2/15`](http://doi.org/10.1088/0067-0049/214/2/15)

(ref: Straatman2016) Straatman, C. M. S., Spitler, L. R., Quadri, R. F., et al. 2016, ApJ, 830, 51, doi: [`10.3847/0004-637X/830/1/51`](http://doi.org/10.3847/0004-637X/830/1/51)

(ref: Sun2021) Sun, F., Egami, E., Pérez-González, P. G., et al. 2021, ApJ, 922, 114, doi: [`10.3847/1538-4357/ac2578`](http://doi.org/10.3847/1538-4357/ac2578)

(ref: sun2022) Sun, F., Egami, E., Fujimoto, S., et al. 2022, ApJ, 932, 77, doi: [`10.3847/1538-4357/ac6e3f`](http://doi.org/10.3847/1538-4357/ac6e3f)

(ref: Sun2024) Sun, F., Helton, J. M., Egami, E., et al. 2024, ApJ, 961, 69, doi: [`10.3847/1538-4357/ad07e3`](http://doi.org/10.3847/1538-4357/ad07e3)

(ref: Swinbank2012) Swinbank, A. M., Karim, A., Smail, I., et al. 2012, MNRAS, 427, 1066, doi: [`10.1111/j.1365-2966.2012.22048.x`](http://doi.org/10.1111/j.1365-2966.2012.22048.x)

(ref: Tacchella2016a) Tacchella, S., Dekel, A., Carollo, C. M., et al. 2016, MNRAS, 457, 2790, doi: [`10.1093/mnras/stw131`](http://doi.org/10.1093/mnras/stw131)

(ref: Tacconi2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179, doi: [`10.3847/1538-4357/aaa4b4`](http://doi.org/10.3847/1538-4357/aaa4b4)

(ref: Tadaki2020) Tadaki, K., Iono, D., Yun, M. S., et al. 2020, ApJ, 889, 141, doi: [`10.3847/1538-4357/ab64f4`](http://doi.org/10.3847/1538-4357/ab64f4)

(ref: TH1985ApJ...291..722T) Tielens, A. G. G. M., & Hollenbach, D. 1985, ApJ, 291, 722, doi: [`10.1086/163111`](http://doi.org/10.1086/163111)

(ref: Tsujita2022PASJ...74.1429T) Tsujita, A., Tadaki, K.-i., Kohno, K., et al. 2022, PASJ, 74, 1429, doi: [`10.1093/pasj/psac082`](http://doi.org/10.1093/pasj/psac082)

(ref: Uematsu2024) Uematsu, R., Ueda, Y., Kohno, K., et al. 2024, ApJ, 965, 108, doi: [`10.3847/1538-4357/ad26f7`](http://doi.org/10.3847/1538-4357/ad26f7)

(ref: Umehata2017) Umehata, H., Tamura, Y., Kohno, K., et al. 2017, ApJ, 835, 98, doi: [`10.3847/1538-4357/835/1/98`](http://doi.org/10.3847/1538-4357/835/1/98)

(ref: Umehata2020) Umehata, H., Smail, I., Swinbank, A. M., et al. 2020, A&A, 640, L8, doi: [`10.1051/0004-6361/202038146`](http://doi.org/10.1051/0004-6361/202038146)

(ref: Valentino2020) Valentino, F., Magdis, G. E., Daddi, E., et al. 2020, ApJ, 890, 24, doi: [`10.3847/1538-4357/ab6603`](http://doi.org/10.3847/1538-4357/ab6603)

(ref: Wang2016) Wang, T., Elbaz, D., Schreiber, C., et al. 2016, ApJ, 816, 84, doi: [`10.3847/0004-637X/816/2/84`](http://doi.org/10.3847/0004-637X/816/2/84)

(ref: Wang2019Nat) Wang, T., Schreiber, C., Elbaz, D., et al. 2019, Nature, 572, 211, doi: [`10.1038/s41586-019-1452-4`](http://doi.org/10.1038/s41586-019-1452-4)

(ref: Wang2018) Wang, W., Kassin, S. A., Pacifici, C., et al. 2018, ApJ, 869, 161, doi: [`10.3847/1538-4357/aaef79`](http://doi.org/10.3847/1538-4357/aaef79)

(ref: Williams2019) Williams, C. C., Labbe, I., Spilker, J., et al. 2019, ApJ, 884, 154, doi: [`10.3847/1538-4357/ab44aa`](http://doi.org/10.3847/1538-4357/ab44aa)

(ref: Xiao2023arXiv230902492X) Xiao, M., Oesch, P., Elbaz, D., et al. 2023a, arXiv e-prints, arXiv:2309.02492, doi: [`10.48550/arXiv.2309.02492`](http://doi.org/10.48550/arXiv.2309.02492)

(ref: Xiao2023) Xiao, M. Y., Elbaz, D., Gómez-Guijarro, C., et al. 2023b, A&A, 672, A18, doi: [`10.1051/0004-6361/202245100`](http://doi.org/10.1051/0004-6361/202245100)

(ref: Yamaguchi2016) Yamaguchi, Y., Tamura, Y., Kohno, K., et al. 2016, PASJ, 68, 82, doi: [`10.1093/pasj/psw073`](http://doi.org/10.1093/pasj/psw073)

(ref: Yamaguchi2019) Yamaguchi, Y., Kohno, K., Hatsukade, B., et al. 2019, ApJ, 878, 73, doi: [`10.3847/1538-4357/ab0d22`](http://doi.org/10.3847/1538-4357/ab0d22)

(ref: zavala2021) Zavala, J. A., Casey, C. M., Manning, S. M., et al. 2021, ApJ, 909, 165, doi: [`10.3847/1538-4357/abdb27`](http://doi.org/10.3847/1538-4357/abdb27)

(ref: Zhou2020) Zhou, L., Elbaz, D., Franco, M., et al. 2020, A&A, 642, A155, doi: [`10.1051/0004-6361/202038059`](http://doi.org/10.1051/0004-6361/202038059)

(ref: Zolotov2015) Zolotov, A., Dekel, A., Mandelker, N., et al. 2015, MNRAS, 450, 2327, doi: [`10.1093/mnras/stv740`](http://doi.org/10.1093/mnras/stv740)

[^1]: <https://github.com/tjlcbakx/redshift-search-graphs>

</paper>

Write the methods card for this paper.