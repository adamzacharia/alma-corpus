# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...652A.128J\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...652A.128J",
 "title": "ALMA Lensing Cluster Survey: A spectral stacking analysis of [C II] in lensed z ∼ 6 galaxies",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Jolly, Jean-Baptiste",
 "n_authors": 17,
 "arxiv_id": "2106.09085",
 "doi": "10.1051/0004-6361/202140878",
 "alma_projects_linked_by_archive": [
  "2013.1.00999.S",
  "2015.1.01425.S",
  "2018.1.00035.L"
 ]
}
```

Paper text:
<paper>
# ALMA Lensing Cluster Survey: A spectral stacking analysis of \[C ii\] in lensed $z\sim6$ galaxies

The properties of galaxies at redshift $z>6$ hold the key to our understanding of the early stages of galaxy evolution and can potentially identify the sources of the ultraviolet radiation that give rise to the epoch of reionisation. The far-infrared cooling line of \[C ii\] at 158 $\mu$m is known to be bright and correlate with the star formation rate (SFR) of low-redshift galaxies, and hence is also suggested to be an important tracer of star formation and interstellar medium properties for very high-redshift galaxies.

With the aim to study the interstellar medium properties of gravitationally lensed galaxies at $z>6$, we search for \[C ii\] and thermal dust emission in a sample of 52 $z\sim6$ galaxies observed by the ALMA Lensing Cluster Survey (ALCS).

We perform our analysis using LINESTACKER, stacking both \[C ii\] and continuum emission. The target sample is selected from multiple catalogues, and the sample galaxies have spectroscopic redshift or low-uncertainty photometric redshifts ($\sigma_z < 0.02$) in nine galaxy clusters. Source properties of the target galaxies are either extracted from the literature or computed using spectral energy distribution (SED) fitting. Both weighted-average and median stacking are used, on both the full sample and three sub-samples.

Our analyses find no detection of either \[C ii\] or continuum. An upper limit on $L_{\rm [CII]}$ is derived, implying that \[C ii\] remains marginally consistent for low-SFR $z>6$ galaxies but likely is under-luminous compared to the local $L_{\rm [CII]}$-SFR relationship. We discuss potential biases and possible physical effects that may be the cause of the non-detection. Further, the upper limit on the dust continuum implies that less than half of the star formation is obscured.

# Introduction

The first billion years after the Big Bang mark the epoch of early galaxy formation and evolution. The ultraviolet (UV) photons from the early galaxies ionised the hydrogen of the intergalactic medium, a period also known as the epoch of reionisation (EoR; see (cite: Stark2016) for a complete review).

Dedicated efforts to search for $z>6$ galaxies employing a variety of multi-wavelength data have resulted in thousands of viable candidates. The primary methods for discovering these early galaxies are photometric drop-out techniques and narrow-band Lyman-alpha emitter selection (cite: Steidel1996; Ono2012; Ono2018; Schenker2012; Oesch2015; Zitrin2015b; Song2016; Shibuya2018; Higuchi2019). The evolution of the derived luminosity function as a function of redshift for rest-frame UV-selected galaxies shows an increasing contribution to the total ionising UV light produced by sub-$L^*$ galaxies (cite: Bouwens2006; Bouwens2015; Mclure2013). This has implications for understanding which sources might be responsible for the largest fraction of the reionisation of the intergalactic medium during the EoR (cite: Bouwens2007; Bouwens2012; Ouchi2009; Bunker2010; McLure2010; Oesch2010; Robertson2013; Atek2015).

Spectroscpic redshift surveys have primarily targeted galaxies brighter than $L^*$ (cite: Lilly2009; Kochnek2012; Newman2013; Stark2013); however, the number of systematic spectroscopic redshift measurements for fainter galaxies is growing (cite: LeFevre2013; Bacon2017; Hasinger2018; Coe2019; Richard2020). Spectroscopic redshifts are essential for detailed investigations of the interstellar medium (ISM) and thus for understanding the physical conditions of the gas and dust. In the local universe the far-infrared fine-structure line of \[C ii\] at 158 $\mu$m from the $^2P_{3/2} \to ^2P_{1/2}$ transition is known to be one of the brightest gas-cooling lines in star forming galaxies (cite: DeLooze2014; Sargsyan2014; Cormier2015). As carbon has an ionisation potential of 11.2 eV, below that of hydrogen, \[C ii\] is detected in regions of both predominantly neutral and ionised gas. The line luminosity has been found to correlate with the star formation rate (SFR) in normal, star-forming galaxies (cite: Stacey2010; DeLooze2011; DeLooze2014; Herrera-Camus2015; Schaerer2020) and has also been proposed as a gas mass tracer (cite: Zanella2018; madden20). As the emission wavelength is redshifted into the submillimetre and millimetre bands, the \[C ii\] is recognised as an important probe of the ISM of high-$z$ galaxies. With an excitation temperature of $T = 91.2$ K, the line is less sensitive to the effects of the cosmic microwave background radiation compared to, for example, CO lines, which are otherwise common tracers of molecular gas and the ISM of high-$z$ galaxies. Notably, several studies have observed \[C ii\] in $z>6$ galaxies (cite: Riechers2013; Knudsen2016; Venemans2016; Decarli2017; Stanley2019; Venemans2020) as the line has the potential to characterise the ISM at this early epoch. A large number of detections have been discovered across a range broad of SFRs (cite: Capak2015; Willott2015; Knudsen2016; Pentericci2016; Bradac2017; Decarli2017; Matthee2017; Carniani2018; Smit2018; Hashimoto2019; Bakx2020; Bethermin2020; Harikane2020; LeFevre2020; Fujimoto2021; Laporte2021), but interestingly also a number of non-detections (cite: Ouchi2013; Gonzalez2014; Ota2014; Maiolino2015; Schaerer2015; Knudsen2016).

Because of the faint absolute UV magnitude of sub-$L^*$ galaxies at $z>6$ (cite: Ono2018), one would need at least 10 hours of ALMA observing time to detect them in \[C ii\] . In this context, and to establish a large sample of sub-$L^*$ galaxies at $z>6$, observations can be done more efficiently by targeting galaxy cluster fields as gravitational lensing will amplify the light from such distant galaxies (cite: Richard2011; Knudsen2016; Fujimoto2021; Laporte2021). Even then many galaxies remain undetected, the stacking of the data can enable a significant statistical improvement in the sensitivity (cite: Fujimoto2018; Fujimoto2019; Stanley2019; Bethermin2020; Carvajal2020; Uzgil2021).

In this paper we present a spectral line stacking analysis of the \[C ii\] line for a sample of 52 gravitationally lensed galaxies from the ALMA Lensing Cluster Survey (ALCS; Kohno et al. in prep). The ALCS is a large project observing 33 galaxy clusters using the Atacama Large millimetre/sub-millimetre Array (ALMA). The target sources of this study are in the redshift range $5.9\lesssim z\lesssim6.6$ and have not been individually detected with \[C ii\] in the ALCS data.

The structure of this paper is as follows. In Sect. 2 we describe in detail the data as well as the studied sample. Sect. 3 outlines the method and the different tools used to carry out this analysis. In Sect. 4 we present the results before discussing their implications, biases, and newly raised questions in Sect. 5. Throughout the paper we assume $H_0=70$ km/s, $\Omega_\mathrm{M} =0.3$, and $\Omega_\Lambda=0.7$.

# Data and sample

## ALMA Lensing Cluster Survey

The ALCS is an large ALMA programme accepted in cycle 6 (Project ID: 2018.1.00035.L; PI: K. Kohno). The programme observed 33 massive galaxy clusters, 16 from RELICS (cite: Coe2019), 12 from CLASH (cite: Postman2012), and 5 from the Frontier Fields survey (cite: Lotz2017), for a total of 88 arcmin$^2$ observed in band 6 (i.e. at a wavelength of $\sim\,$1.2 mm). Observations were carried out between December 2018 and December 2019 (cycles 6 and 7) in compact array configurations C43-1 and C43-2. The entire bandwidth of the survey spans a total of 15 GHz split over two spectral ranges: 250.0–257.5 GHz (tuning 1) and 265.0–272.5 GHz (tuning 2)[^1]. As ALCS utilises two spectral frequency setups, the survey provides a frequency coverage twice the size of a single setup, and this means a wider redshift coverage. The data were reduced and calibrated using the Common Astronomy Software Applications (CASA) package version 5.4.0 (cite: CASA). Data cubes were imaged using the CASA task TCLEAN down to a level of 3$\sigma$ with a channel size of 60 km s$^{-1}$. Throughout this paper, we use natural-weighted, primary-beam-corrected, and *uv*-tapered maps, with a tapering parameter of 2 arcsec (pixel size of 0.16 arcsec). We use *uv*-tapered maps so that all the stacked sources share a similar beam size, and hence a similar spatial resolution, which is essential for stacking homogeneity. However, because high-redshift sources may be small compared to the tapered beam size and for completeness, we also performed our stacking analyses on cubes in their native resolution ($\sim$ 1 arcsec; see Fig. [12](#CII_nativeRes) in the appendix). A full description of the survey and of its main objectives will be presented in a separate paper (Kohno et al. in prep). The main characteristics of the data cubes used in this analysis can be seen in Table [\[tab.cubeInfo\]](#tab.cubeInfo).

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| ID$^{(a)}$ | RMS tune 1$^{(b)}$ | RMS tune 2$^{(c)}$ | RMS continuum image$^{(d)}$ |  |  |
|  | \[mJy/beam\] | \[mJy/beam\] | \[mJy/beam\] |  |  |
| Abell2744 | 2.6 | 2.1 | 0.17 |  |  |
| MACSJ0416.1-2403 | 2.8 | 3.5 | 0.14 |  |  |
| AbellS1063 | 2.1 | 2.6 | 0.17 |  |  |
| MACSJ1149.5+2223 | 2.0 | 2.4 | 0.16 |  |  |
| MACS1206.2-0847 | 2.4 | 3.0 | 0.15 |  |  |
| RXJ1347-1145 | 2.4 | 3.0 | 0.15 |  |  |
| MACS0329.7-0211 | 2.6 | 3.3 | 0.18 |  |  |
| MACS1115.9+0129 | 2.9 | 3.6 | 0.20 |  |  |
| Abell383 | 2.8 | 3.5 | 0.19 |  |  |

Table notes: ${(a)}$ Cluster name; ${(b)}$ RMS in 60  km s$^{-1}$channels in the first tuning (250.0-257.5 GHz, unit: mJy/beam, 147 channels in total); ${(c)}$ RMS in 60  km s$^{-1}$channels in the second tuning (265.0-272.5 GHz, unit: mJy/beam, 139 channels in total); ${(d)}$ RMS in continuum image (mJy/beam).

## Sample

### Sample selection

To perform our spectral stacking analysis we select sources with redshift $5.97\lesssim z\lesssim6.17$ or $6.38\lesssim z\lesssim6.60$, that is sources whose potential \[C ii\] emission lines would fall in the observed bandwidth. Because redshift uncertainties have a drastic impact on the performance of spectral stacking analyses (cite: Jolly2020), only sources with spectroscopic redshifts or high precision photometric redshifts ($\sigma_z<0.02$, corresponding to $\sigma_v \sim$ 800 km s$^{-1}$) were selected. This ensures that line peaks are well known and lines are stacked aligned. Sources are extracted from (ordered by number of sources): The MUSE GTO (MGTO) programme catalogue (cite: Richard2020), the ASTRODEEP catalogue (cite: ASTRODEEP1; ASTRODEEP2; ASTRODEEP3), the Hubble Frontier Field Deep Space (HFFDS) catalogue (cite: HFFDSpaper), and the VLT/MUSE observations catalogue (cite: Caminha2019).

In addition, the regions of interest were queried using AstroQuery (cite: Astroquery2019), leading to the addition of two sources from the NASA/IPAC Extragalactic Database (NED[^2]). We also manually added the two images of a lensed source in Abell 383 (cite: Richard2011; Knudsen2016). HST catalogues are corrected for astrometry offset with respect to ALMA maps following (cite: Franco2018).

To avoid duplicates between different catalogues, sources are removed if they are closer than 1 arcsec from one another. Priority is given to catalogues with higher redshift precision.

For homogeneity, and to push the limit of observability towards fainter sources, we only select sources that are not individually detected in our ALMA data. After these considerations we selected a total of 52 sources (of which 23 are multiple images of same sources): 32 from MGTO, 10 from ASTRODEEP, four from HFFDS, two from VLT/MUSE, two from (cite: Richard2011; Knudsen2016), and two from our AstroQuery query. The main characteristics of the sample are presented in Tables [\[table:sample\]](#table:sample) and [\[table:physics\]](#table:physics).

From this sample, we assemble four different sub-samples as follows. As shown in (cite: Jolly2020) redshift uncertainty lead to a reduced efficiency of spectral stacking analyses. We hence perform our analysis concurrently on one sub-sample composed of only 36 sources with secure, spectroscopically determined redshifts; that is all sources with photometric redshifts, or sources with low spectroscopic redshift confidence are removed from this sub-sample (see Table [\[table:sample\]](#table:sample)).

We also split sources by their SFR, creating a sub-sample consisting solely of sources whose SFRs are greater than the median SFR of the full sample (2.05 M$_\odot$ yr$^{-1}$). Finally, we create a sub-sample composed of the sources present in both the high redshift precision and high-SFR sub-samples.

In the rest of this paper, the different samples are referred to as: ’full sample’, ’good-$z$ sub-sample’, ’high-SFR sub-sample’, and ’SFR-$z$ sub-sample’.

### Sample properties and SED fitting

The $z\sim 6$ galaxies used in this study are located behind nine clusters from the Frontier Fields and CLASH surveys, for which deep public NIR data are available [^3] [^4]. Data from three clusters have been analysed as part of the ASTRODEEP project (cite: Merlin2016), namely Abell2744, MACSJ0416.1-2403 and MACSJ1149.5+2223, and robust catalogues have been released. In addition, Abell2744 and MACSJ0416.1-2403 as well as MACS1206.2-0847, MACS0329.7-0211 and RXJ1347-1145 were analysed as part of the MUSE GTO programme, and complete catalogues were made available through their latest data-release (cite: Richard2020). In the following, we use the catalogues from the ASTRODEEP project and the MUSE-GTO data release for these six clusters, and we use our own catalogues for the remaining.

We built our catalogues using SExtractor v2.19.5 (cite: SExtractor) in double image mode, using a sum of WFC3 data as a detection picture. We extracted sources on PSF-matched data, obtained after running TinyTim (cite: TinyTim), using extraction parameters adapted to identify faint sources : DETECT_MINAREA = 5 pixels, -DETECT_THRESH = 1.5$\sigma$ and -DEBLEND_MINCOUNT = 0.00001. The number of extracted sources per cluster ranges from 4,942 (MACS1115.9+0129) to 9,079 (RXJ1347-1145) for the CLASH clusters and goes up to 20,996 for the Frontier Field cluster AS1063 because of the depth difference between the surveys (F105W$\sim$27.5AB vs. $\sim$30.3 AB at 2$\sigma$ for the CLASH and Frontier Fields data, respectively). We extracted the photometry on IRAC 3.6 $\mu$m and 4.5 $\mu$m images in a 1.2$''$ radius aperture centred at the F160W position for isolated objects. Three objects in our sample required more careful IRAC photometry extraction (namely A383-19, RXJ1347-6, RXJ1347-8). For those objects, we used GALFIT (cite: GALFIT) with the following assumptions for the input parameters: We fixed the candidate (and the neighbouring object) positions to the centroids of the F160W/HST image; we adopted Serfic galaxy profiles; the flux, the axes’ ratio, and the half-light radius were left as free parameters. The error bars were computed from the noise measured directly on the original IRAC images. In case of non-detection we used the 2$\sigma$ upper limits in the following. Among the 52 galaxies in our sample, 33 are identified in our catalogues. A visual inspection at the position of the remaining objects show no UV counterpart, suggesting they have a high Ly-$\alpha$ equivalent width (EW).

Because all galaxies in this sample are located behind lensing clusters, one needs to correct the photometry for lensing magnification. For targets in the Frontier Fields data, we used the online magnification calculator[^5], and chose the magnification factors computed with the CATS group models ((cite: Jauzac2014; Richard2014)). For the CLASH clusters, we used the updated models from (cite: Zitrin2015).

To estimate the physical properties, such as the stellar mass, age, and SFR, of the galaxies discussed in this paper, we ran BAGPIPES (cite: BAGPIPES) with four different star formation histories (SFHs): a burst, a constant, an exponential, and a combination of a young burst with a constant SFH. The IMF used in BAGPIPES is from (cite: KroupaandBoily2002). For all models, the parameter spaces allowed for the age of the component, defined as the beginning of the star formation, was between 0 and 1.0 Gyr, for the mass formed between $10^6$ and $10^{12}$ M$_{\odot}$, for the reddening between $A_V=0.0$, and 1.0 mag and we fixed the ionisation parameter at $\log U=-2$ (see for example (cite: Stark2015)). To determine the SFH that gives the best fit of the lensed-corrected SED, we applied the Bayesian information criterion (BIC) accounting for the difference in the number of parameters used in each SFH. For most of the objects, the best fit is obtained either with a constant or burst SFH, with a similar fit quality in most cases.

Among our sample, $\approx80\%$ of our targets show consistent stellar masses for either a burst or constant SFH, for the remaining $\approx 20\%$, we used the stellar mass obtained from the best fit. The SFR is computed using three methods : (i) taking the stellar mass and average age of the source, which reflects the mean SFR over the age of the galaxy, (ii) using the UV luminosity (cite: Kennicutt1998) and corrected for dust attenuation, and (iii) taking the instantaneous SFR obtained from the SFH, which gives the SFR at the observed redshift. The last method is inconsistent with the two first methods and strongly depends on the age of the burst and even more strongly on the current star formation. For the majority of sources in our sample, the SFR averaged over the age of the galaxy is $<$10 M$_{\odot}$/yr. The SFRs quoted in the rest of this paper were computed using the UV luminosity and corrected for dust attenuation (method (ii)). The attenuation of the UV light by the dust is relatively modest, with an averaged value of $A_v$=0.20$\pm$0.11 mag.

For sources not detected we used the information from the literature when available. 19 sources, mostly Lyman-alpha emitters from the MUSE GTO catalogues, are not detected in any of the HST bands and we could hence not derive reliable SFRs. This should not impact our results much since the SFRs of the rest of the sample are homogeneously distributed and that we only use the mean and median SFR of the sample, and not individual values.

The magnification factors of the sources in the full sample range from 1.77 to 72.9 with a median of 3.77 and a weighted-mean[^6] of 8.175 (see Fig. [1](#MagDistrib) and Table [\[tab.rms\]](#tab.rms). The magnification corrected SFRs range from 0.17 M$_\odot$ yr$^{-1}$ to $\sim\,$125 M$_\odot$ yr$^{-1}$, with a weighted-meanof $\sim\,$10.2 M$_\odot$ yr$^{-1}$ and a median of $\sim\,$2.0 M$_\odot$ yr$^{-1}$, SFR distribution can be seen in Figure [2](#SFRDistrib) and Table [\[tab.rms\]](#tab.rms). The redshift distribution across the samples is shown in Figure [3](#ZDistrib).

In addition to the individual SED fittings described above, we stacked all the best-fit SEDs of the sources obtained with BAGPIPES together (both using mean and median stacking) to recover the SFR$_\mathrm{UV}$. Using these methods we find SFR$_\mathrm{UV, mean}=7.73\pm0.77$ M$_{\odot}$ and SFR$_\mathrm{UV, median}=2.32\pm0.56$ M$_{\odot}$.

![](new_mag_histo.pdf)

![](new_mag_sfr.pdf)

![](z_histo.pdf)

# Stacking method

The spectral stacking analysis is performed using LINESTACKER (cite: Jolly2020). LINESTACKER is an open access stacking software developed for stacking interferometric data. It is an ensemble of CASA tasks that allow the stacking of either spectral cubes or extracted spectra. LINESTACKER comes with a suite of tools, among which are automated weighting routines, which we use in our analysis.

Sources were stacked pixel to pixel and spectral channel to spectral channel. Both weighted average and median stacking were used. Some sources are located close to the edge of the cubes[^7], making the noise levels of these sources much higher than others. For this reason, we weighted each source proportionally to the inverse of the square of the local RMS. To do so, LINESTACKER’s automated weighting schemes were used, and local noise was estimated in an area of 12.96 arcsec$^2$ (81$\times$81 pixels$^2$) around the source. Sources were not masked while computing noise as they were not individually detected in the first place.

All candidate spectral regions where the corresponding lines would be located for each source were aligned using their redshift and the emission frequency of \[C ii\] (1900.5369 GHz; see Sect. [5.1](#sec:biases) for a discussion about the impact of the redshift offsets on the stack results). Spatially, sources were stacked using their physical coordinate extracted from the corresponding catalogue. In addition to the spectral stacking analysis, we performed continuum stacking of the same sources in the same way.

# Results

## \[C ii\] stack results

The stacking analyses yielded non-detections for the full sample and all sub-samples. The stacking results are presented as moment-0 maps, integrated over 540 km s$^{-1}$ ($-270$  km s$^{-1}$ to +270  km s$^{-1}$) centred on the expected \[C ii\] line. (cite: Bethermin2020) and (cite: Schaerer2020) studied a large sample of non-lensed sources through the ALPINE project (cite: Bethermin2020; Faisst2020; LeFevre2020). Their sample at $z>5$ shows an average SFR of $\sim$ 13 M$_\odot$ yr$^{-1}$ for the undetected sources and $\sim$ 82 M$_\odot$ yr$^{-1}$ for sources with $9.00< {\rm log}(L_{\rm [CII]} /{\rm L}_\odot)<9.33$, which is either of the order of, or greater than, our sample. Their sample shows a \[C ii\] linewidth distribution with a median FWHM of $\sim$252 km s$^{-1}$. We decided to integrate over roughly two times their median linewidth in the moment-0 maps, to include lines with potentially larger width as well as to account for artificial increase in the line width that would arise from stacking lines slightly off-centre. Indeed, high uncertainty on the redshift as well as systematic offsets between redshifts derived from Lyman-$\alpha$ or \[C ii\] , may result in line emission being stacked with a small velocity shift (the ALPINE survey identified a median offset of 184$^{+201}_{-215}$ km s$^{-1}$between Lyman-$\alpha$ and \[C ii\] redshift measurement (cite: Faisst2020); this is discussed further in Section [5.1](#sec:biases)).

Integrated moment-0 weighted-average stacked maps of the samples can be seen in Figure [4](#CIIMean_combined). Similarly moment-0 median stacked maps of the same samples can be seen in Figure [10](#CIIMedian_combined) in the appendix. In addition to the moment maps we show continuum stack counterpart maps in Figure [5](#ContinuumMean_combined) for the weighted-average stacks and Figure [11](#ContinuumMedian_combined) for the median stack, in appendix. Spectra, extracted from a circular region of radius 1.12 arcsec (7 pixels) corresponding to the stacked beam of the tapered data, and centred on the stacked cube centre, of both the weighted-average and median stacking analyses of the full sample are shown in Figures [6](#CIIMean) and [9](#CIIMedian).

From the absence of detection we derive a 3-$\sigma$ upper limit on $L_{\rm [CII]}$  similarly to (cite: Schaerer2020) and (cite: Bethermin2020). $L_{\rm [CII]}$  is computed using the formula provided in (cite: SolomonVandenBout2005): $$\begin{equation}
    L_{\rm [CII]}=1.04\times10^{-3}\times I_{\rm [CII]}D_L^2 \nu_{obs}\, L_\odot , 
\end{equation}$$ where $I_{\rm [CII]}$ is the velocity integrated line intensity for \[C ii\] in Jy km s$^{-1}$ (corresponding here to 3$\,\sigma$ of the stacked moment-0 map), $D_L$ is the luminosity distance in Mpc, and $\nu_{obs}$ is the observed frequency in GHz. The derived \[C ii\] line luminosity is then corrected for the weighted mean magnification of the studied sample when performing weighted-mean stacking, or the median magnification when performing median stacking.

The $L_{\rm [CII]}$ upper-limits are reported in Table [\[tab.rms\]](#tab.rms). The rms obtained from the mean and median stacking methods being comparable, the main difference between the corresponding estimated upper limits on $L_{\rm [CII]}$ come from the difference between the weighted-average and the median magnification of the samples. Figure [7](#CIISFR) shows the relationship between the derived $L_{\rm [CII]}$ upper limit and SFR of each sample, obtained through both weighted-average and median stacking. Results from mean stacking analyses are shown with the corresponding mean SFR, results from median stacking analyses with the corresponding median SFR. While upper limits from the median stacking analyses are still compatible with the local relationship, upper limits derived from the mean stacking analyses seem to indicate a lower value of $L_{\rm [CII]}$ compared to the local relation.

Because none of the stacking analyses lead to a detection we do not perform the usual statistical tests designed to probe the significance of the stacking result. Indeed, bootstrapping tests, for example, probe the distribution of the stacked line flux; however, such tests would not serve much purpose if the stacked source is undetected.

We have studied the full sample and the defined sub-samples. It would be possible to subdivide the full sample based on other criteria (e.g. on Lyman-$\alpha$ equivalent width); however, given the clear non-detection we do not pursue further sub-samples.

One can notice the presence of a stripe pattern on the side of the moment maps in Figure [4](#CIIMean_combined). These are due to a few sources being close to the edge and some outer pixels of the stacking stamps being empty. Sources are discarded if the cube edge is closer than one beam from the stack centre. It should be noted that sources close to the edge will have intrinsically higher noise levels and will hence carry a lesser weight in the weighted-average stacks.

Extensive photo-dissociation region modelling from (cite: madden20) provides a recipe for utilising $L_{\rm [CII]}$ to estimate the total molecular gas mass of low-metallicity dwarf galaxies, $M_{\rm H_2} = 10^{2.12} \times [L_{\rm [CII]}]^{0.97}$. Applying this to our results, and with the assumption that the sample sources have sub-solar metallicity (see Section [5.3](#subsec:models)), we estimate an upper limit on the molecular gas mass, $M_{\rm H_2}$, in the range $< 1.3\times10^9 - 7.0\times10^9$ M$_\odot$. This range was derived using the two sample extremes: the $3\sigma$ upper limits derived for (i) the good-$z$ sub-sample, mean stacking analysis and (ii) the SFR+$z$ sub-sample median stacking analysis. Compared to the mean and median stellar masses of $M_{\rm stellar} \sim 1\times10^{9}$ and $2\times 10^{8}$ M$_\odot$, respectively, these suggest that $M_{\rm H_2}$ is of the order of or higher than $M_{\rm stellar}$, which is in agreement with the molecular gas-to-stellar mass fraction extrapolated from (cite: Walter2020).

(cite: Dessauges2020) find an average molecular gas fraction, $f_{\rm molgas}=M_{\rm molgas}$/($M_{\rm stellar}$+$M_{\rm molgas}$), of order $\sim 0.6$ at redshift $4.4<z<5.9$ using a sample of 44 \[C ii\] detected non-merger galaxies in the ALPINE survey with a median stellar mass of $\sim10^{9.7}$, indicating a possible flattening of the gas fraction evolution with redshift. To compare to our results, we estimated the mean and median molecular gas fraction for the (sub-)samples using the stellar mass estimate from our SED fitting analysis (we note that stellar masses estimates could not be derived for all sources (see Sect. [2.2.2](#sampleProperties)), leading to mean/median masses not exactly representative of the samples as we could only extract $M_{\rm stellar}$ for $\sim 2/3$ of the sources). Our mean results are mostly in good accordance with the average molecular gas fraction derived by (cite: Dessauges2020) as our upper limits indicate $f_{\rm molgas}\lesssim0.5$ (see Table [1](#tab:molgas)). The median results however present higher ratios, of order $\lesssim 0.9$. The large spread between the mean and median results is mainly explained by the difference between the mean and median stellar masses (see Table [1](#tab:molgas)). Indeed, the mean stellar masses are sensible to high-mass outliers, while these have no impact on the median results. As shown in (cite: Dessauges2020), a dependence is seen between $f_{\rm molgas}$ and $M_{\rm stellar}$, and the deviation between our own results and the molecular gas fraction cited above can be explained by the difference between the stellar masses probed. In addition, one should note that the $f_{\rm molgas}$ extracted from both our mean and median analyses are mostly consistent with the $f_{\rm molgas}$-$M_{\rm stellar}$ relationship at $z\sim6$ presented in (cite: Dessauges2020).

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| sample name | rms$^{(a)}$ | $L_{\rm [CII]}$$^{(b)}$ | \<SFR\>$^{(c)}$ | \<$\mu$\>$^{(d)}$ |
|  | \[mJy/beam  km s$^{-1}$\] | \[$10^7$ L$_\odot$\] | \[M$_\odot\,{\rm yr}^{-1}$\] |  |
| Full sample, mean | 44.2 | \<1.65 | 10.22$^{+55.12}_{-7.89}$ | 8.17 |
| Full sample, median | 47.7 | \<3.85 | 2.05$^{+4.16}_{-0.98}$ | 3.77 |
| Good $z$ sub-sample, mean | 45.9 | \<1.27 | 19.70$^{+63.46}_{-12.37}$ | 11.04 |
| Good $z$ sub-sample, median | 50.3 | \<3.77 | 2.68$^{+8.75}_{-1.82}$ | 4.06 |
| High-SFR sub-sample, mean | 76.7 | \<4.91 | 19.57$^{+60.78}_{-13.72}$ | 4.76 |
| High-SFR sub-sample, median | 81.9 | \<7.63 | 6.2$^{+11.69}_{-2.44}$ | 3.27 |
| SFR+$z$ sub-sample, mean | 96.9 | \<5.25 | 29.59$^{+78.10}_{-18.15}$ | 5.62 |
| SFR+$z$ sub-sample, median | 115.8 | \<8.69 | 10.51$^{+13.52}_{-5.13}$ | 4.06 |

Table notes: ${(a)}$ Rms value in the velocity integrated flux map, obtained by collapsing a channel width of 540  km s$^{-1}$(nine 60 km s$^{-1}$channels); ${(b)}$ Magnification corrected \[C ii\] line luminosity computed as discussed in section [4](#results) ; ${(c)}$ Magnification corrected SFR of the sample (see Table [\[table:physics\]](#table:physics)): weighted-average SFR of the sources in the sample for weighted-average stacking analyses and median SFR for the median stacking analyses. The errors represent the positive and negative standard deviations for the mean stacking analyses, and the positive and negative median absolute deviations for the median stacking analyses ; ${(d)}$ Magnification of the sample, weighted-average magnification of the sources in the sample for the weighted-average stacking analyses, median magnification for the median stacking analyses.

|                             |                        |                         |
|:----------------------------|:----------------------:|:-----------------------:|
| sample name                 | $f_{\rm molgas}^{(a)}$ | $M_{\rm stellar}^{(b)}$ |
|                             |                        |       (M$_\odot$)       |
| Full sample, mean           |         \<0.55         |       $10^{9.03}$       |
| Full sample, median         |         \<0.93         |       $10^{8.38}$       |
| Good-$z$ sub-sample, mean   |         \<0.38         |       $10^{9.22}$       |
| Good-$z$ sub-sample, median |         \<0.92         |       $10^{8.40}$       |
| High-SFR sub-sample, mean   |         \<0.65         |       $10^{9.31}$       |
| High-SFR sub-sample, median |         \<0.95         |       $10^{8.53}$       |
| SFR+$z$ sub-sample, mean    |         \<0.59         |       $10^{9.45}$       |
| SFR+$z$ sub-sample, median  |         \<0.95         |       $10^{8.56}$       |

: Upper limit on the molecular gas fraction and corresponding stellar mass for the different sub-samples.

Table notes: $(a)$ Upper limit on the molecular gas fraction, $f_{\rm molgas}=M_{\rm molgas}$/($M_{\rm stellar}$+$M_{\rm molgas}$), derived using the $L_{\rm [CII]}$ upper limits from the different (sub-)samples; $(b)$ Mean/median stellar mass of each (sub-)sample, extracted from our SED fitting analyses.

![image](momentMap-CII_mean_fullSample_fixedCoords_4.pdf) ![image](momentMap-CII_mean_zsub_fixedCoords_4.pdf) ![image](momentMap-CII_mean_sfrsub_fixedCoords_4.pdf) ![image](momentMap-CII_mean_sfrsubZ_fixedCoords_4.pdf)

![image](momentMap-CII_continuumCounterPart_mean_fullSample_fixedCoords_4.pdf) ![image](momentMap-CII_continuumCounterPart_mean_zsub_fixedCoords_4.pdf) ![image](momentMap-CII_continuumCounterPart_mean_sfrsub_fixedCoords_4.pdf) ![image](momentMap-CII_continuumCounterPart_mean_sfrsubZ_fixedCoords_4.pdf)

![](CII_mean_fullSample_fixedCoords4)

![](Lcii_SFR_Jolly_grey_models.png)

![](Lcii_SFR_Jolly_grey_models_only.png)

## Continuum

The stacking analyses of the continuum data yielded non-detections, consistent with the results from the spectral line stacking for \[C ii\] . The resulting rms for continuum stack of the full sample and the sub-samples are given in Table [\[tab:contstack\]](#tab:contstack). We estimate a $3\sigma$ upper limit on the far-infrared luminosity assuming that the far-infrared spectral energy distribution (SED) is well described by a modified blackbody with a temperature of $T=35$ K and $T=45$ K, both with dust emissivity $\beta = 1.5$. At the high redshift of the sample, the CMB temperature is $T_\mathrm{CMB}\sim20$ K, and we adopt the prescription from (cite: daCunha13) to correct for the effect of the CMB. We note that single photometric upper limit only provides a rough estimate on $L_{\rm FIR}$, which is subject to a large systematic uncertainty depending on, for example, the choice of temperature or $\beta$. The far-infrared luminosity upper limits are used to estimate the dust-obscured SFR, and we assume ${\rm SFR}(L_{\rm FIR}) {\rm [M_\odot\,yr^{-1}]}\sim 1.1\times10^{-10} L_{\rm FIR}[{\rm L_\odot}]$ (for a Kroupa IMF, 0.1-100 M$_\odot$, and constant star formation over a timescale of 100 Myr; (cite: calzetti11)). We note that different assumptions on the IMF and SFH could lead to a factor of two, or more, change in the estimated values (cite: rieke09; calzetti11). The estimated upper limit on the $\mathrm{SFR}_\mathrm{IR}$ is $\sim1-6$ M$_\odot$ yr$^{-1}$ after correcting for magnification, which is either similar to or below the average rest-frame UV derived SFRs of the samples (see Table [\[tab.rms\]](#tab.rms)). This implies that less than half of the star formation is obscured by dust. It is worth noting that the correction for dust extinction on the UV derived SFR presented in Table [\[tab.rms\]](#tab.rms), leads to a reduction of the SFR of $\sim3-6$M$_\odot$ yr$^{-1}$. While these numbers are not fully representative of the sample (since they are only available for the sources that we could analyse ourselves through SED fitting), the sum of $\mathrm{SFR}_\mathrm{UV}$, not corrected for dust attenuation, and $\mathrm{SFR}_\mathrm{IR}$ is comparable to the original $\mathrm{SFR}_\mathrm{UV}$, after correcting for dust attenuation.

Similarly, using the continuum upper limit we estimate an upper limit on the dust mass. We assume a dust opacity of $\kappa_\nu = \kappa_0 (\nu / \nu_0)^\beta$, using $\kappa_0 = 5.1$ cm$^2$/g for $\nu_0=1.2$THz (cite: DraineLi07), and $\beta=1.5$. This results in upper limits in the range $(0.6-8.1)\times 10^6$ M$_\odot$. However, we note that there are significant systematic uncertainties associated with this, and the values could be a factor of five higher depending on the assumptions (cite: LiDraine01; DraineLi07; Magdis12; casey14; Abergel14). If we assume $\kappa_0 =0.43$ cm$^2$/g for $\nu_0 = 350$ GHz (cite: Abergel14), the upper limits are in the range $(1.2-14.7)\times 10^6$ M$_\odot$. With the large systematic uncertainties, this is consistent with the upper limits on the molecular gas mass, and the factor of $\sim100$ between the two upper limits is consistent with our assumption that the studied galaxies have low metallicity (cite: Leroy2011). We note that the continuum emission around rest-frame 158$\mu$m is close to the peak of the dust emission, and it is thus more sensitive to the temperature and total luminosity (probing the SFR) rather than the total dust mass, which is better measured by the emission at the Rayleigh-Jeans tail (cite: Magdis12; Scoville16).

+:----------------------------+:----------------:+:-----------------------:+:----------------------------:+:-----------------------:+:-----------------------:+:----------------------------:+:-----------------------:+
|                             |                  | $T=35$ K                                                                         | $T=45$ K                                                                         |
+-----------------------------+------------------+-------------------------+------------------------------+-------------------------+-------------------------+------------------------------+-------------------------+
| sample name                 | rms$^{(a)}$      | $L_{\rm FIR}$ $^{(b)}$  | SFR$^{(c)}$                  | $M_{\rm dust}$ $^{(d)}$ | $L_{\rm FIR}$ $^{(b)}$  | SFR$^{(c)}$                  | $M_{\rm dust}$ $^{(d)}$ |
+-----------------------------+------------------+-------------------------+------------------------------+-------------------------+-------------------------+------------------------------+-------------------------+
|                             | \[$\mu$Jy/beam\] | \[$10^{10}$ L$_\odot$\] | \[M$_\odot\,{\rm yr}^{-1}$\] | \[10$^6$ M$_\odot$\]    | \[$10^{10}$ L$_\odot$\] | \[M$_\odot\,{\rm yr}^{-1}$\] | \[10$^6$ M$_\odot$\]    |
+-----------------------------+------------------+-------------------------+------------------------------+-------------------------+-------------------------+------------------------------+-------------------------+
| Full sample, mean           | 15               | \< 0.5                  | \< 0.5                       | \< 1.7                  | \<1.1                   | \<1.2                        | \<0.9                   |
+-----------------------------+------------------+-------------------------+------------------------------+-------------------------+-------------------------+------------------------------+-------------------------+
| Full sample, median         | 17               | \< 1.3                  | \< 1.4                       | \< 4.2                  | \< 2.8                  | \<3.0                        | \< 2.2                  |
+-----------------------------+------------------+-------------------------+------------------------------+-------------------------+-------------------------+------------------------------+-------------------------+
| Good $z$ sub-sample, mean   | 14               | \< 0.4                  | \< 0.4                       | \< 1.2                  | \<0.8                   | \<0.9                        | \< 0.6                  |
+-----------------------------+------------------+-------------------------+------------------------------+-------------------------+-------------------------+------------------------------+-------------------------+
| Good $z$ sub-sample, median | 16               | \< 1.1                  | \< 1.2                       | \< 3.7                  | \< 2.5                  | \< 2.7                       | \< 2.0                  |
+-----------------------------+------------------+-------------------------+------------------------------+-------------------------+-------------------------+------------------------------+-------------------------+
| High-SFR sub-sample, mean   | 25               | \< 1.5                  | \< 1.6                       | \< 4.8                  | \<3.3                   | \<3.5                        | \< 2.5                  |
+-----------------------------+------------------+-------------------------+------------------------------+-------------------------+-------------------------+------------------------------+-------------------------+
| High-SFR sub-sample, median | 26               | \< 2.3                  | \< 2.4                       | \< 7.6                  | \< 5.1                  | \<5.5                        | \<4.0                   |
+-----------------------------+------------------+-------------------------+------------------------------+-------------------------+-------------------------+------------------------------+-------------------------+
| SFR+$z$ sub-sample, mean    | 28               | \< 1.4                  | \< 1.5                       | \<4.8                   | \<3.2                   | \< 3.4                       | \< 2.5                  |
+-----------------------------+------------------+-------------------------+------------------------------+-------------------------+-------------------------+------------------------------+-------------------------+
| SFR+$z$ sub-sample, median  | 35               | \< 2.4                  | \< 2.6                       | \< 8.1                  | \< 5.5                  | \< 5.9                       | \< 4.3                  |
+-----------------------------+------------------+-------------------------+------------------------------+-------------------------+-------------------------+------------------------------+-------------------------+

Table notes: ${(a)}$ rms value in the continuum map ; ${(b)}$ upper limit on far-infrared luminosity corrected for the magnification and the effect of the CMB; ${(c)}$ upper limit on SFR estimated from the $L_{\rm FIR}$; ${(d)}$ upper limit on molecular gas mass estimated from the $L_{\rm [CII]}$.

As mentioned in section [4.1](#CII_results), one can see the presence of stripe patterns on the continuum stacked maps, even more obvious than on the \[C ii\] moment-0 maps (see Figure [5](#ContinuumMean_combined)). While only sources further than one beam from the edge of the cubes are selected in the \[C ii\] stacked maps, this edge can can be positioned at a slightly different position on the continuum maps. This is due to both the frequency dependency of the primary and synthesized beam and to the two spectral windows used to construct the continuum maps, which sometimes have different spatial coverage. We however decided to construct the continuum stacked maps as pure counterparts of the \[C ii\] stacked maps, and hence included strictly the same sources in both analyses, regardless of whether sources were closer to edge in the continuum maps.

# Discussion

## Potential biases

While our derived $L_{\rm [CII]}$ upper limit measurements indicates a possible different behaviour for high-z galaxies in the low-SFR regime compared to their equivalent at low-z, we caution that our upper limit could be underestimated.

The first and probably main bias could come from systematic redshift uncertainties. The redshifts of most of the galaxies in our samples are based on the Ly-$\alpha$ lines, which have been shown to exhibit possible systematic offsets compared to the redshift of the \[C ii\] line (cite: Capak2015; Faisst2016; Matthee2017; Bethermin2020; Cassata2020; Pahl2020). (cite: Faisst2020) show a median offset of $184^{+201}_{-215}$  km s$^{-1}$between the \[C ii\] measured redshift and redshift measured from Ly-$\alpha$ in the ALPINE survey. Because the offset redshift is not constant, there is no straightforward way to correct for it while stacking, especially since our stacking analysis leads to no detection [^8]. However, as shown in (cite: Jolly2020), redshift uncertainties of $\sim$ 180  km s$^{-1}$  lead to an average stacked line amplitude of $\sim70$% of its maximum value, and an average flux of $\sim90$% of its maximum value (stacking 30 lines of 400  km s$^{-1}$  with a S/N $\sim$ 1 pre stacking). Such systematic uncertainties would hence only lead to a modest underestimate of the upper limits derived in our analysis.

Similarly, stacking positions could also be a source of systematic uncertainties. Systematic astrometric shifts in the source catalogues compared to the ALCS data would lead to a poor overlap of stacking positions. This impact could be significant if uncertainties are high compared to the \[C ii\] size of the sources. This is, however, unlikely as offsets between HST catalogues and ALMA are well known (cite: Dunlop2017; Franco2018; Fujimoto2019; Franco2020) and accounted for, and MUSE catalogues are properly aligned (cite: Richard2020). Nonetheless, a similar effect would be expected from systematic offsets between the \[C ii\] regions and the optical regions that are the stacking targets.

As suggested by (cite: Carniani2020) \[C ii\] extended emission could also lead to reduced emission and an underestimate of the upper limit. Such an effect could be made more probable from stacking objects elongated by gravitational lensing effects. However, from the average low magnifications (most under 10) as well as the absence of evidence of elongated objects from the *HST* NIR images in our sample, we do not expect elongated \[C ii\] nor continuum emission.

Normally a basic assumption for a stacking analysis, is that the sample sources are drawn from the same parent population, thus providing a meaningful sample homogeneity. For this particular study, the sample is constructed from several catalogues of different sensitivity and different selection criteria at optical and near-infrared wavelengths, leading to a heterogeneous sample. The primary selection criteria applied here are position, redshift, and luminosity (i.e. $L_{\rm [CII]}$ below the threshold for individual detection). Our sample consists mostly of Ly-$\alpha$ emitters (all spectroscopically identified sources show Ly-$\alpha$ emission), some of which are also Lyman-break galaxies (12 sources in our sample classify as Lyman-break galaxies based on their SED). While it is expected that all normal star-forming galaxies have a \[C ii\] line, the strength of this line could be affected by different conditions and properties of each galaxy and its environment (see Sect. [5.3](#subsec:models)). We note that Ly-$\alpha$ emitters are not necessarily representative of the entire population of normal star-forming galaxies at $z\sim6$ (cite: Stark2011; Tilvi2014; DeBarros2017; harikane18; Pentericci2018; Kusakabe2020). It should be noted however, that in the good-$z$ sub-sample nearly all galaxies are selected based on a high Ly-$\alpha$ EW, which is a fairly uniform selection.

However, because our sample is biased towards Ly-$\alpha$ emitters, one can expect the studied galaxies to be dust poor. Indeed, if the observed galaxies were dust rich one would expect scattering in the ISM, leading to lower Ly-$\alpha$ emission. Therefore, one can expect to see a lower far-infrared continuum, as well as lower \[C ii\] emission.

When looking at the results presented in Figure [7](#CIISFR) one can see a significant difference between the mean and median analyses. This is not due to a drastic difference in the resulting stacked cubes, but comes essentially from the difference between the mean and median magnification of our sample. It is hence obvious that the individually derived magnifications will have a significant impact on the $L_{\rm [CII]}$-SFR limits derived through our analysis. Many lensing models exist to derive magnification values (cite: Keeton2011; Jauzac2014; Johnson2014; Ishigaki2015; Merten2015; Zitrin2015; Diego2016; Bradac2017) and our model choices (see section [2.2.2](#sampleProperties)) have a sizable impact on our result. However, and unless big systematic differences exist between models, selecting a high number of sources should, on average, reduce the impact of choosing one set of models in place of an other.

Similarly, the uncertainties on the SFR –while depicting the SFR spread over the studied sample– highlight the importance of the precision of this value. One can indeed see that the spread of the SFR is quite large in our samples and, because of this, the derived $L_{\rm [CII]}$-SFR limits may end up mostly in accordance with (cite: DeLooze2014) local value, or in total disagreement with it. It is hence important to highlight the impact of SFR derivation as well as its uncertainty. Due to the limited amount of data, and the existence of different models, derived SFR can vary by factors of several for the same source. However, and similar to the uncertainties on magnification, uncertainties on the SFR should tend to even out on average if the number of sources is high enough. Our study should hence be less impacted by SFR uncertainties than single objects studies, but these numbers should still be evaluated with caution.

Finally it should be noted that some stacked sources are multiple images of the same source, this intrinsically reduces the statistical significance of our results as it diminishes the number of independent objects observed.

## Comparison to individual detections in high-$z$, low-SFR galaxies 

To probe how much our results may differ from analyses on similar objects we compare it to individual detections in high-$z$, low-SFR galaxies. \[C ii\] has been detected in $z>6$ lensed galaxies (cite: Knudsen2016; Bradac2017; Bakx2020; Fujimoto2021; Laporte2021), and non-detections have been reported for two $z>8$ galaxies (cite: laporte19). The estimated magnification-corrected line luminosities are in the range $L_{\rm [CII]} \sim 10^{7-9}$ L$_\odot$ for SFRs $\sim\,$3-60 M$_\odot$ yr$^{-1}$, which partially overlap the SFR distribution of our sample. The lowest-SFR, non-lensed detection of \[C ii\] is seen towards BDF-3299 (cite: carniani17). The reported detections, along with the two non-detections, are either consistent or below the $L_{\rm [CII]}$-SFR relation found in low-$z$ starburst galaxies (cite: DeLooze2014), as shown in Figure [7](#CIISFR).

The rms of the stacked maps in this study are comparable to the reported observed rms values for \[CII\] detections in the literature. This suggests that if all sources in our sample were to share the properties of the individual detected sources, we would have expected at least a tentative detection in our stacked results.

The $L_{\rm [CII]}$-SFR relation has a known scatter. However, given the large number of detections (and non-detections) of $z>6$ sources distant from the local $L_{\rm [CII]}$-SFR relation, this would either imply that at $z>6$ this scatter is larger, or that the relation for high-redshift galaxies is offset from the local relation.

The ALPINE survey (cite: Bethermin2020; Schaerer2020) is another ALMA Large programme presenting \[C ii\] observations of 118 individually selected sources in the redshift range $4.4<z<5.9$. The ALCS \[C ii\] redshift coverage is effectively continuing to a higher redshift beyond the ALPINE survey. The SFR range of the ALPINE sample is $\sim 10 -300$ M$_\odot$ yr$^{-1}$, which partly overlaps with the upper range of our sample (cite: Bethermin2020). A comparison between these two sets of results depends on whether we focus on the results from the median or mean stacking. The mean SFR of the mean stacking has a wide scatter because it is dominated by a few high-SFR estimates. The resulting stacked \[C ii\] upper limit is lower than that of the ALPINE survey at a similar SFR. Focusing on the median distribution, we note that our stacked results probe a complementary region of the $L_{\rm [CII]}$-SFR plane and remains mostly compatible with the local relationship.

## Is a low $L_{\rm [CII]}$ expected for low-SFR, $z>6$ galaxies?

The comparison of the $L_{\rm [CII]}$-SFR relation from local galaxies to $z>6$ galaxies is challenging. A fraction of $z>6$ galaxies lying below the relation, including the upper limits derived from the stacked results, might be explained by the physical conditions combined with the early evolutionary stage. Metallicity, the hardness and intensity of the UV radiation field, the gas density distribution, and the star formation history are all aspects to be considered.

Given the relatively short time after the Big Bang, it is possible that the galaxies targeted in our study will not have had sufficient time to reach a solar level metallicity (cite: Stark2016). In the local universe, dwarf galaxies are known to have on average lower metallicity (cite: Cormier2015), and given the comparable stellar masses of dwarf galaxies and the target sources, it is reasonable to assume that the studied sample have sub-solar metallicity. The metallicity has been estimated only for a small number of gravitationally lensed $z>6$ galaxies (cite: Stark2015); however, the detections or non-detections of dust also give an indication of the metallicity (cite: watson15; Bakx2020). Previous modelling of photo-dissociation regions suggest that in lower metallicity-environments the \[C ii\] luminosity will be reduced (cite: Rollig2006). Modelling of the \[C ii\] luminosity for $z>6$ galaxies also shows that the low-metallicity regions have a lower $L_{\rm [CII]}$ (cite: Vallini2015; Olsen2017; Lagache2018; Ferrara2019). In addition, as shown in (cite: Vallini2015), at $z>4.5$ the CMB temperature becomes comparable to the temperature of the cold neutral medium, strongly attenuating \[C ii\] emission from these regions and reducing the overall \[C ii\] emission from high-redshift galaxies.

For a lower metallicity, and thus likely also lower dust content, UV photons have a longer mean free path. Also, it has been suggested that the binary stellar populations might yield an increased production of UV-photons (e.g. (cite: ma16; stanway16; gotberg20); however, see recent results from (cite: ma20)). An increased intensity of the UV-radiation field would also impact the ionisation state of carbon, for example resulting in an increased fraction of double- or triple-ionised carbon (the ionisation potential for double ionisation is 24.4 eV). Examples of double-ionised, and triple-ionised carbon have been found (cite: Stark2015; smit17) for $z>5$ galaxies. We note that our continuum non-detection could rule out a dust-rich ISM scenario.

Short-term variations in the star formation have also been suggested to impact the \[C ii\] luminosity relative to the estimated SFR (cite: Vallini2015; Ferrara2019). For example, upward deviations from the Kennicutt-Schmidt star formation relation could be seen as a starburst-like phase, and that in turn can suppress the \[C ii\] emission (cite: Ferrara2019).

In addition, according to the CLOUDY simulations ran by (cite: Harikane2020), the ionisation parameter may be the most important driver for a possible low \[C ii\] content at a given SFR.

For a further understanding of the non-detections from our stacking analysis, either deeper data for individual sources of the sample or a multiple-line analysis would be needed. In terms of the latter, observations of the \[O iii\] and C iii\] lines specifically would help break the degeneracy (cite: Ferrara2019; Vallini2020).

# Summary

Through our analysis we performed a spectral stacking analysis of \[C ii\] , in 52 gravitationally lensed galaxies at $z\sim6$ using data from the ALCS.

We analysed both the full sample as well as three sub-samples, one containing only the sources with good spectroscopic redshifts, one with only sources with the higher SFR, and the last one with only sources present in both sub-samples. For each (sub-)sample we also performed a continuum stacking analysis. We performed both weighted-average and median stacking analyses and none yielded a detection. We derive $3\sigma$ upper limits on the $L_{\rm [CII]}$ of $(1-9)\times10^{7}$ L$_\odot$. Compared to the local $L_{\rm [CII]}$-SFR relation, this implies a deviation towards lower $L_{\rm [CII]}$, similar to previous results for individual detections of $z>6$ lensed galaxies.

The continuum stacking analyses also yielded non-detections and we derived upper limits on the far-infrared luminosity for two different modified blackbody temperatures of 35 and 45 K. The resulting upper limits vary between $0.4\times10^{10}$ L$_\odot$ and $2.6\times10^{10}$ L$_\odot$ depending on the temperature and sub-sample. From these we estimated upper limits on the SFR, which suggest that less than half of the star formation is dust obscured.

We discuss potential source of bias in our analysis. A spectral stacking analysis relies on good knowledge of the redshift, and for example possible systematic offsets between \[C ii\] and Ly-$\alpha$ redshifts, could reduce the performance of the stacking analysis. Sample inhomogeneity could also lead to a biased result if not all objects follow the same relationship. Systematic uncertainties on derived magnification and SFR of the sample sources can impact the interpretation of our results and the comparison to the $L_{\rm [CII]}$-SFR relation. Finally, as suggested by modelling (cite: Ferrara2019; Vallini2020), several physical parameters could affect the $L_{\rm [CII]}$. For example, metallicity or gas density distribution could result in lower \[C ii\] excitation, and hence lower $L_{\rm [CII]}$.

Despite these potential biases, our analysis is the first large-scale analysis of \[C ii\] in faint lensed galaxies at the end of the EoR. Our stacking analysis allows us to reach very low RMS (of order of 1mJy/beam in 60 km s$^{-1}$ channels) and, being based on an analysis of 52 objects, our non-detection has a high statistical significance.

# Acknowledgements

We thank the anonymous referee for their helpful comments. This paper makes use of the ALMA data: ALMA #2018.1.00035.L, #2013.1.00999.S, and #2015.1.01425.S. ALMA is a partnership of the ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by the ESO, AUI/NRAO, and NAOJ. KK acknowledges support from the Swedish Research Council (2015-05580), and the Knut and Alice Wallenberg Foundation. K. Kohno acknowledges the JSPS KAKENHI Grant Number JP17H06130 and the NAOJ ALMA Scientific Research Grant Number 2017-06B. FEB acknowledges support from ANID grants CATA-Basal AFB-170002, FONDECYT Regular 1190818, 1200495 and Millennium Science Initiative ICN12_009. DE acknowledges support from a Beatriz Galindo senior fellowship (BG20/00224) from the Ministry of Science and Innovation. GEM and FV acknowledge the Villum Fonden research grant 13160 “Gas to stars, stars to dust: tracing star formation across cosmic time” and the Cosmic Dawn Center of Excellence funded by the Danish National Research Foundation under then grant No. 140. FV acknowledges support from the Carlsberg Foundation Research Grant CF18-0388 “Galaxies: Rise and Death”.

137 natexlab

(ref: Atek2015) Atek, H., Richard, J., Jauzac, M., et al. 2015, ApJ, 814, 69

(ref: Bacon2017) Bacon, R., Conseil, S., Mary, D., et al. 2017, A&A, 608, A1

(ref: Bakx2020) Bakx, T. J. L. C., Tamura, Y., Hashimoto, T., et al. 2020, MNRAS, 493, 4294

(ref: SExtractor) Bertin, E. & Arnouts, S. 1996, A&AS, 117, 393

(ref: Bethermin2020) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2

(ref: Bouwens2006) Bouwens, R. & Illingworth, G. 2006, New A Rev., 50, 152

(ref: Bouwens2007) Bouwens, R. J., Illingworth, G. D., Franx, M., & Ford, H. 2007, ApJ, 670, 928

(ref: Bouwens2015) Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2015, ApJ, 803, 34

(ref: Bouwens2012) Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2012, ApJL, 752, L5

(ref: Bradac2017) Bradač, M., Garcia-Appadoo, D., Huang, K.-H., et al. 2017, ApJL, 836, L2

(ref: Bunker2010) Bunker, A. J., Wilkins, S., Ellis, R. S., et al. 2010, MNRAS, 409, 855

(ref: calzetti11) Calzetti, D. 2013, Star Formation Rate Indicators, ed. J. Falcón-Barroso & J. H. Knapen, 419

(ref: Caminha2019) Caminha, G. B., Rosati, P., Grillo, C., et al. 2019, A&A, 632, A36

(ref: Capak2015) Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455

(ref: BAGPIPES) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379

(ref: Carniani2020) Carniani, S., Ferrara, A., Maiolino, R., et al. 2020, MNRAS, 499, 5136

(ref: carniani17) Carniani, S., Maiolino, R., Pallottini, A., et al. 2017, A&A, 605, A42

(ref: Carniani2018) Carniani, S., Maiolino, R., Smit, R., & Amorı́n, R. 2018, ApJL, 854, L7

(ref: Carvajal2020) Carvajal, R., Bauer, F. E., Bouwens, R. J., et al. 2020, A&A, 633, A160

(ref: casey14) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45

(ref: Cassata2020) Cassata, P., Morselli, L., Faisst, A., et al. 2020, A&A, 643, A6

(ref: ASTRODEEP2) Castellano, M., Amorı́n, R., Merlin, E., et al. 2016, A&A, 590, A31

(ref: Coe2019) Coe, D., Salmon, B., Bradač, M., et al. 2019, ApJ, 884, 85

(ref: Cormier2015) Cormier, D., Madden, S. C., Lebouteiller, V., et al. 2015, A&A, 578, A53

(ref: daCunha13) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13

(ref: DeBarros2017) De Barros, S., Pentericci, L., Vanzella, E., et al. 2017, A&A, 608, A123

(ref: DeLooze2011) De Looze, I., Baes, M., Bendo, G. J., Cortese, L., & Fritz, J. 2011, MNRAS, 416, 2712

(ref: DeLooze2014) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62

(ref: Decarli2017) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457

(ref: Dessauges2020) Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643, A5

(ref: ASTRODEEP3) Di Criscienzo, M., Merlin, E., Castellano, M., et al. 2017, A&A, 607, A30

(ref: Diego2016) Diego, J. M., Broadhurst, T., Wong, J., et al. 2016, MNRAS, 459, 3447

(ref: DraineLi07) Draine, B. T. & Li, A. 2007, ApJ, 657, 810

(ref: Dunlop2017) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861

(ref: Faisst2016) Faisst, A. L., Capak, P. L., Davidzon, I., et al. 2016, ApJ, 822, 29

(ref: Faisst2020) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61

(ref: Ferrara2019) Ferrara, A., Vallini, L., Pallottini, A., et al. 2019, MNRAS, 489, 1

(ref: Franco2018) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152

(ref: Franco2020) Franco, M., Elbaz, D., Zhou, L., et al. 2020, A&A, 643, A53

(ref: Fujimoto2021) Fujimoto, S., Oguri, M., Brammer, G., et al. 2021, arXiv e-prints, arXiv:2101.01937

(ref: Fujimoto2019) Fujimoto, S., Ouchi, M., Ferrara, A., et al. 2019, ApJ, 887, 107

(ref: Fujimoto2018) Fujimoto, S., Ouchi, M., Kohno, K., et al. 2018, ApJ, 861, 7

(ref: Astroquery2019) Ginsburg, A., Sipőcz, B. M., Brasseur, C. E., et al. 2019, AJ, 157, 98

(ref: Gonzalez2014) González-López, J., Riechers, D. A., Decarli, R., et al. 2014, ApJ, 784, 99

(ref: gotberg20) Götberg, Y., de Mink, S. E., McQuinn, M., et al. 2020, A&A, 634, A134

(ref: Harikane2020) Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ, 896, 93

(ref: harikane18) Harikane, Y., Ouchi, M., Shibuya, T., et al. 2018, ApJ, 859, 84

(ref: Hashimoto2019) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, PASJ, 71, 71

(ref: Hasinger2018) Hasinger, G., Capak, P., Salvato, M., et al. 2018, ApJ, 858, 77

(ref: Herrera-Camus2015) Herrera-Camus, R., Bolatto, A. D., Wolfire, M. G., et al. 2015, ApJ, 800, 1

(ref: Higuchi2019) Higuchi, R., Ouchi, M., Ono, Y., et al. 2019, ApJ, 879, 28

(ref: Ishigaki2015) Ishigaki, M., Kawamata, R., Ouchi, M., et al. 2015, ApJ, 799, 12

(ref: Jauzac2014) Jauzac, M., Clément, B., Limousin, M., et al. 2014, MNRAS, 443, 1549

(ref: Johnson2014) Johnson, T. L., Sharon, K., Bayliss, M. B., et al. 2014, ApJ, 797, 48

(ref: Jolly2020) Jolly, J.-B., Knudsen, K. K., & Stanley, F. 2020, MNRAS, 499, 3992

(ref: Karman2017) Karman, W., Caputi, K. I., Caminha, G. B., et al. 2017, A&A, 599, A28

(ref: Keeton2011) Keeton, C. R. 2011, GRAVLENS: Computational Methods for Gravitational Lensing

(ref: Kennicutt1998) Kennicutt, Robert C., J. 1998, ARA&A, 36, 189

(ref: Knudsen2016) Knudsen, K. K., Richard, J., Kneib, J.-P., et al. 2016, MNRAS, 462, L6

(ref: Kochnek2012) Kochanek, C. S., Eisenstein, D. J., Cool, R. J., et al. 2012, ApJS, 200, 8

(ref: TinyTim) Krist, J. E., Hook, R. N., & Stoehr, F. 2011, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 8127, Optical Modeling and Performance Predictions V, ed. M. A. Kahan, 81270J

(ref: KroupaandBoily2002) Kroupa, P. & Boily, C. M. 2002, MNRAS, 336, 1188

(ref: Kusakabe2020) Kusakabe, H., Blaizot, J., Garel, T., et al. 2020, A&A, 638, A12

(ref: Lagache2018) Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130

(ref: laporte19) Laporte, N., Katz, H., Ellis, R. S., et al. 2019, MNRAS, 487, L81

(ref: Laporte2021) Laporte, N., Zitrin, A., Ellis, R. S., et al. 2021, MNRAS \[\]

(ref: LeFevre2020) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1

(ref: LeFevre2013) Le Fèvre, O., Cassata, P., Cucciati, O., et al. 2013, A&A, 559, A14

(ref: Leroy2011) Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ, 737, 12

(ref: LiDraine01) Li, A. & Draine, B. T. 2001, ApJ, 554, 778

(ref: Lilly2009) Lilly, S. J., Le Brun, V., Maier, C., et al. 2009, ApJS, 184, 218

(ref: Lotz2017) Lotz, J. M., Koekemoer, A., Coe, D., et al. 2017, ApJ, 837, 97

(ref: ma16) Ma, X., Hopkins, P. F., Kasen, D., et al. 2016, MNRAS, 459, 3614

(ref: ma20) Ma, X., Quataert, E., Wetzel, A., et al. 2020, MNRAS, 498, 2001

(ref: madden20) Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A, 643, A141

(ref: Magdis12) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6

(ref: Maiolino2015) Maiolino, R., Carniani, S., Fontana, A., et al. 2015, MNRAS, 452, 54

(ref: Matthee2017) Matthee, J., Sobral, D., Darvish, B., et al. 2017, MNRAS, 472, 772

(ref: Mclure2013) McLure, R. J., Dunlop, J. S., Bowler, R. A. A., et al. 2013, MNRAS, 432, 2696

(ref: McLure2010) McLure, R. J., Dunlop, J. S., Cirasuolo, M., et al. 2010, MNRAS, 403, 960

(ref: CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: ASTRODEEP1) Merlin, E., Amorı́n, R., Castellano, M., et al. 2016a, A&A, 590, A30

(ref: Merlin2016) Merlin, E., Amorı́n, R., Castellano, M., et al. 2016b, A&A, 590, A30

(ref: Merten2015) Merten, J., Meneghetti, M., Postman, M., et al. 2015, ApJ, 806, 4

(ref: Newman2013) Newman, J. A., Cooper, M. C., Davis, M., et al. 2013, ApJS, 208, 5

(ref: Oesch2010) Oesch, P. A., Bouwens, R. J., Illingworth, G. D., et al. 2010, ApJL, 709, L16

(ref: Oesch2015) Oesch, P. A., van Dokkum, P. G., Illingworth, G. D., et al. 2015, ApJL, 804, L30

(ref: Olsen2017) Olsen, K., Greve, T. R., Narayanan, D., et al. 2017, ApJ, 846, 105

(ref: Ono2018) Ono, Y., Ouchi, M., Harikane, Y., et al. 2018, PASJ, 70, S10

(ref: Ono2012) Ono, Y., Ouchi, M., Mobasher, B., et al. 2012, ApJ, 744, 83

(ref: Ota2014) Ota, K., Walter, F., Ohta, K., et al. 2014, ApJ, 792, 34

(ref: Ouchi2013) Ouchi, M., Ellis, R., Ono, Y., et al. 2013, ApJ, 778, 102

(ref: Ouchi2009) Ouchi, M., Mobasher, B., Shimasaku, K., et al. 2009, ApJ, 706, 1136

(ref: Pahl2020) Pahl, A. J., Shapley, A., Faisst, A. L., et al. 2020, MNRAS, 493, 3194

(ref: GALFIT) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2010, AJ, 139, 2097

(ref: Pentericci2016) Pentericci, L., Carniani, S., Castellano, M., et al. 2016, ApJL, 829, L11

(ref: Pentericci2018) Pentericci, L., Vanzella, E., Castellano, M., et al. 2018, A&A, 619, A147

(ref: Abergel14) Planck Collaboration, Abergel, A., Ade, P. A. R., et al. 2014, A&A, 566, A55

(ref: Postman2012) Postman, M., Coe, D., Benı́tez, N., et al. 2012, ApJS, 199, 25

(ref: Richard2020) Richard, J., Claeyssens, A., Lagattuta, D., et al. 2021, A&A, 646, A83

(ref: Richard2014) Richard, J., Jauzac, M., Limousin, M., et al. 2014, MNRAS, 444, 268

(ref: Richard2011) Richard, J., Kneib, J.-P., Ebeling, H., et al. 2011, MNRAS, 414, L31

(ref: Riechers2013) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329

(ref: rieke09) Rieke, G. H., Alonso-Herrero, A., Weiner, B. J., et al. 2009, ApJ, 692, 556

(ref: Robertson2013) Robertson, B. E., Furlanetto, S. R., Schneider, E., et al. 2013, ApJ, 768, 71

(ref: Rollig2006) Röllig, M., Ossenkopf, V., Jeyakumar, S., Stutzki, J., & Sternberg, A. 2006, A&A, 451, 917

(ref: Sargsyan2014) Sargsyan, L., Samsonyan, A., Lebouteiller, V., et al. 2014, ApJ, 790, 15

(ref: Schaerer2015) Schaerer, D., Boone, F., Zamojski, M., et al. 2015, A&A, 574, A19

(ref: Schaerer2020) Schaerer, D., Ginolfi, M., Béthermin, M., et al. 2020, A&A, 643, A3

(ref: Schenker2012) Schenker, M. A., Stark, D. P., Ellis, R. S., et al. 2012, ApJ, 744, 179

(ref: Scoville16) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83

(ref: Shibuya2018) Shibuya, T., Ouchi, M., Harikane, Y., et al. 2018, PASJ, 70, S15

(ref: HFFDSpaper) Shipley, H. V., Lange-Vagle, D., Marchesini, D., et al. 2018, ApJS, 235, 14

(ref: Smit2018) Smit, R., Bouwens, R. J., Carniani, S., et al. 2018, Nature, 553, 178

(ref: smit17) Smit, R., Swinbank, A. M., Massey, R., et al. 2017, MNRAS, 467, 3306

(ref: SolomonVandenBout2005) Solomon, P. M. & Vanden Bout, P. A. 2005, ARA&A, 43, 677

(ref: Song2016) Song, M., Finkelstein, S. L., Livermore, R. C., et al. 2016, ApJ, 826, 113

(ref: Stacey2010) Stacey, G. J., Hailey-Dunsheath, S., Ferkinhoff, C., et al. 2010, ApJ, 724, 957

(ref: Stanley2019) Stanley, F., Jolly, J. B., König, S., & Knudsen, K. K. 2019, A&A, 631, A78

(ref: stanway16) Stanway, E. R., Eldridge, J. J., & Becker, G. D. 2016, MNRAS, 456, 485

(ref: Stark2016) Stark, D. P. 2016, ARA&A, 54, 761

(ref: Stark2013) Stark, D. P., Auger, M., Belokurov, V., et al. 2013, MNRAS, 436, 1040

(ref: Stark2011) Stark, D. P., Ellis, R. S., & Ouchi, M. 2011, ApJL, 728, L2

(ref: Stark2015) Stark, D. P., Walth, G., Charlot, S., et al. 2015, MNRAS, 454, 1393

(ref: Steidel1996) Steidel, C. C., Giavalisco, M., Pettini, M., Dickinson, M., & Adelberger, K. L. 1996, ApJL, 462, L17

(ref: Tilvi2014) Tilvi, V., Papovich, C., Finkelstein, S. L., et al. 2014, ApJ, 794, 5

(ref: Uzgil2021) Uzgil, B. D., Oesch, P. A., Walter, F., et al. 2021, ApJ, 912, 67

(ref: Vallini2020) Vallini, L., Ferrara, A., Pallottini, A., Carniani, S., & Gallerani, S. 2020, MNRAS, 495, L22

(ref: Vallini2015) Vallini, L., Gallerani, S., Ferrara, A., Pallottini, A., & Yue, B. 2015, ApJ, 813, 36

(ref: Venemans2020) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130

(ref: Venemans2016) Venemans, B. P., Walter, F., Zschaechner, L., et al. 2016, ApJ, 816, 37

(ref: Walter2020) Walter, F., Carilli, C., Neeleman, M., et al. 2020, ApJ, 902, 111

(ref: watson15) Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327

(ref: Willott2015) Willott, C. J., Carilli, C. L., Wagg, J., & Wang, R. 2015, ApJ, 807, 180

(ref: Zanella2018) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976

(ref: Zitrin2015) Zitrin, A., Fabris, A., Merten, J., et al. 2015a, ApJ, 801, 44

(ref: Zitrin2015b) Zitrin, A., Labbé, I., Belli, S., et al. 2015b, ApJL, 810, L12

# Median stacks velocity integrated maps

Because the results from the median stacks are qualitatively the same results as the mean stacking results –the main difference between mean and median in Figure [7](#CIISFR) being mostly due to the different magnifications and SFR– we decided to put here the velocity integrated maps from our median stacking analyses.

![](CII_median_fullSample_fixedCoords4)

![image](momentMap-CII_median_fullSample_fixedCoords_4.pdf) ![image](momentMap-CII_median_zsub_fixedCoords_4.pdf) ![image](momentMap-CII_median_sfrsub_fixedCoords_4.pdf) ![image](momentMap-CII_median_sfrsubZ_fixedCoords_4.pdf)

![image](momentMap-CII_continuumCounterPart_median_fullSample_fixedCoords_4.pdf) ![image](momentMap-CII_continuumCounterPart_median_zsub_fixedCoords_4.pdf) ![image](momentMap-CII_continuumCounterPart_median_sfrsub_fixedCoords_4.pdf) ![image](momentMap-CII_continuumCounterPart_median_sfrsubZ_fixedCoords_4.pdf)

![image](momentMap-CII_mean_full_old_4) ![image](momentMap-CII_median_full_old_4)

# Samples source descriptions and properties

[^1]: ALCS data are combined with existing ALMA data when available, notably the ALMA Frontier Fields Survey used in this analysis: Project ID: 2013.1.00999.S, PI: Bauer and Project ID; 2015.1.01425.S: PI: Bauer

[^2]: http://nedwww.ipac.caltech.edu/

[^3]: HST Frontier Fields : https://archive.stsci.edu/prepds/frontier/

[^4]: CLASH : https://www.stsci.edu/ postman/CLASH/

[^5]: https://archive.stsci.edu/prepds/frontier/lensmodels/#magcalc

[^6]: The weights used to compute the weighted-average magnification and weighted-average SFR are the same weights used in the weighted-average stacking analysis (see Sect. [3](#sec:stacking))

[^7]: The edges are defined according to the maps compiled in the data (see Kohno et al. in prep)

[^8]: One could otherwise try to maximise the stacked line flux by randomising redshift offsets as a Monte Carlo process. But with a non detection this would most probably lead to maximising noise peaks.

</paper>

Write the methods card for this paper.