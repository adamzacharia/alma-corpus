# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...974..306S\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...974..306S",
 "title": "Constraints on the Physical Origin of Large Cavities in Transition Disks from Multiwavelength Dust Continuum Emission",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Sierra, Anibal",
 "n_authors": 11,
 "arxiv_id": "2408.15407",
 "doi": "10.3847/1538-4357/ad7460",
 "alma_projects_linked_by_archive": [
  "2011.0.00320.S",
  "2011.0.00724.S",
  "2011.0.00742.S",
  "2012.1.00870.S",
  "2013.1.00091.S",
  "2013.1.00157.S",
  "2013.1.00498.S",
  "2015.1.00296.S",
  "2015.1.00888.S",
  "2015.1.01137.S",
  "2016.1.00565.S",
  "2016.1.01042.S",
  "2018.1.00350.S",
  "2018.1.01255.S",
  "2018.1.01755.S"
 ]
}
```

Paper text:
<paper>
# Constraints on the physical origin of large cavities in transition disks from multi-wavelength dust continuum emission

## Abstract

The physical origin of the large cavities observed in transition disks is to date still unclear. Different physical mechanisms (e.g., a companion, dead zones, enhanced grain growth) produce disk cavities of different depth, and the expected spatial distribution of gas and solids in each mechanism is not the same. In this work, we analyze the multi-wavelength interferometric visibilities of dust continuum observations obtained with ALMA and VLA for six transition disks: CQTau, UXTau A, LkCa15, RXJ1615, SR24S, and DMTau, and calculate brightness radial profiles, where diverse emission morphology is revealed at different wavelengths. The multi-wavelength data is used to model the spectral energy distribution and compute constraints on the radial profile of the dust surface density, maximum grain size, and dust temperature in each disk. They are compared with the observational signatures expected from various physical mechanisms responsible for disk cavities. The observational signatures suggest that the cavities observed in the disks around UXTau A, LkCa15, and RXJ1615 could potentially originate from a dust trap created by a companion. Conversely, in the disks around CQTau, SR24S, DMTau, the origin of the cavity remains unclear, although it is compatible with a pressure bump and grain growth within the cavity.

# Introduction

Protoplanetary disks are dynamic objects. Physical processes such as photo-evaporation (cite: Alexander_2006), accretion (cite: Hartmann_2016), dust migration and segregation (cite: Whipple_1972; Weidenschilling_1977; Takeuchi_2002), dust growth (cite: Testi_2014; Birnstiel_2016), settling (cite: Schapler_2004; Avenhaus_2018; Rich_2021), and disk winds (cite: Konigl_2000; Pascucci_2023), are taking place in protoplanetary disks. These mechanisms have an important impact on the disk evolution, the spatial distribution of solids and gas, and thus, on the observed disk morphologies at different wavelengths.

In the last decade, high angular resolution observations of protoplanetary disks have unveiled a diversity of large and small spatial scale sub-structures, including vortices (cite: Brown_2009; Andrews_2009; Casassus_2013; Perez_2014; Robert_2020; Varga_2021), cavities (cite: Francis_2020), rings and gaps (cite: Huang_2018), spiral arms (cite: Mouillet_2001; Muto_2012; Perez_2016; Paneque_2021), and circumplanetary disks (cite: Isella_2019b; Benisty_2021; Christiaens_2024). The origin of the observed morphologies has been attributed to various physical mechanisms such as gravitational instabilities (cite: Toomre_1964), magneto-rotational instability (MRI, (cite: Balbus_1991)), dust traps (cite: Whipple_1972; Klahr_1997), planet-disk interactions (cite: Goldreich_1979; Lin_1979), and snow lines (cite: Hayashi_1981), among others.

The existence of large dust cavities (cite: Francis_2020) in the so-called “transition disks" was first inferred by Near Infrared observations (cite: Strom_1989), and then by their millimeter spectral energy distribution (cite: Calvet_2002), long before high angular resolution data became available. The SED of these objects shows an excess emission at millimeter wavelengths, but no excess emission at mid-infrared wavelengths. This distinct signature was initially interpreted as a deficit of hot material in the inner disk region (cite: Strom_1989; Calvet_2002; Brown_2007), an interpretation that was later confirmed through subsequent high angular resolution observations (cite: Andrews_2011).

The physical origin of large cavities in transition disks, remains unclear. Nonetheless, various proposed mechanisms aim to replicate these observed dust cavities. As pointed out by (cite: vanderMarel_2023), these mechanisms include the presence of companions (cite: Artymowicz_1996), dead zones (cite: Regaly_2012; Flock_2015), photo-evaporation (cite: Alexander_2006; Garate_2021), and/or grain growth (cite: Dullemond_2001). In scenarios involving companions, an already formed planet or a close binary can carve a significant gap in the disk, inhibiting the radial migration of dust grains and resulting in the formation of a large cavity (cite: Dong_2015). This mechanism leads to the creation of a dust trap at the outer edge of the cavity due to the pressure gradient (cite: Pinilla_2012).

A large cavity can also form by a dead zone, where the particle flow halts due to a jump in gas surface density and a pressure maximum (cite: Flock_2015). Unlike the mechanism involving a companion, the dead zone scenario does not predict a gas gap within the cavity (cite: Pinilla_2016).

On the other hand, dust cavities can also form via dust growth. In this mechanism, large grains are expected to have a fast radial migration towards the inner region of the disk (cite: Takeuchi_2002), resulting in a deficit of dust mass within the disk cavity. Additionally, very large grains (with sizes exceeding about 1 cm) have a low opacity at millimeter wavelengths (cite: Draine_2006), thereby reducing the dust continuum emission within the cavity. However, even in the most optimistic scenario where dust growth is very efficient, this mechanism alone has been shown to be insufficient for creating large cavities within 5 Myrs of dust evolution (cite: Birnstiel_2012b). Thus, in addition to dust growth, another physical mechanism producing a pressure bump is needed to reproduce the significant drop of millimeter emission within the cavities of transition disks (cite: Birnstiel_2012b).

Different observational signatures are expected depending on whether the large cavities result from a companion, dead zone, photo-evaporation, or enhanced grain growth. In scenarios involving a dust trap (created by a companion or a dead zone), one would expect an increase in both surface density and maximum grain size at the outer border of the cavity. Conversely, if enhanced grain growth and a pressure bump are responsible for the large cavity, we would expect to infer a prevalence of large dust grains in the inner region of the disk and dust grains being trapped at the border of the cavity.

Observational constraints on the dust surface density, maximum grain size, and temperature can offer valuable insights into the origin of cavities within transition disks. Fortunately, these constraints can be derived from polarized observations (cite: Kataoka_2016b; Kataoka_2016; Yang_2016; Lin_2024; Yang_2024) or from fitting the SED of the dust continuum emission (cite: Perez_2012; Carrasco-Gonzalez_2019; Macias_2021; Sierra_2021; Liu_2024). It is known that both methodologies offer different grain size estimations (hundreds for microns from polarization and a few millimeter from the SED). Although some works (cite: Tazaki_2019; Lin_2023; Zhang_2023) have demonstrated that millimeter porous grains can help to alleviate the tension, it has been shown that only the opacity of compact dust grains can reproduce the observed spectral index in disk population synthesis (cite: Delussu_2024).

In this paper, we analyze the dust continuum emission of six known transition disks: CQTau, UXTau A, LkCa15, RXJ1615, SR24S, and DMTau, with cavity sizes of approximately 50 au, 31 au, 76 au, 30 au, 35 au, and 25 au, respectively (cite: Pinilla_2014; Francis_2020). One of the goals of this work is to compare the multi-wavelength brightness profile for each disk, and infer dust properties than can provide insights into the origin of the cavities.

The observational data is presented in Section [2](#sec:obs). The analysis and modeling of dust continuum visibilities for each observation are conducted in Section [3](#sec:vismod), where high angular resolution radial profiles are computed from the data. Section [4](#sec:multiwave) presents the analysis of multi-wavelength radial profiles, revealing constraints on the dust surface density, maximum grain size, and dust temperature within each disk. The discussion of the physical mechanisms influencing each disk is outlined in Section [5](#sec:discussion), and the general properties are discussed in Section [6](#sec:origin), followed by Conclusions in Section [7](#sec:conclusions).

|         |          |       |          |               |               |
|:-------:|:--------:|:-----:|:--------:|:-------------:|:-------------:|
| Source  | Distance |  $i$  | $\rm PA$ |     $L_*$     |     $M_*$     |
|         |   (pc)   | (deg) |  (deg)   | ($L_{\odot}$) | ($M_{\odot}$) |
|  CQTau  |  149.4   | 36.3  |   46.5   |     10.0      |     1.63      |
|  UXTau  |   140    | 40.9  |  168.7   |      2.5      |      1.4      |
| LkCa15  |  157.2   | 49.7  |   62.1   |      1.3      |     1.32      |
| RXJ1615 |  155.6   | 46.9  |  146.1   |      1.3      |      1.1      |
|  SR24S  |   114    | 47.8  |   26.6   |      2.5      |     0.87      |
|  DMTau  |  144.0   | 35.7  |  157.1   |      0.2      |     0.39      |

: Stellar and disk properties

\
References: Inclination and geometry are computed in this work. The distances are taken from (cite: Gaia_2020), and the luminosity and mass of the star from: (cite: Natta_2006; Espaillat_2010; Wahhaj_2010; Andrews_2011; Manara_2014; vanderMarel_2015; Ubeira_2019; Francis_2020).

# Observations

We used 26 archival dust continuum observations of 6 transition disks: CQ Tau, UX Tau, LkCa15, RXJ1615, SR24S, and DMTau. The dust continuum observations spans from optically thick emission (observed in ALMA Band 9 or Band 7) to optically thin emission (observed in VLA Band Q or Band Ka) in all disks, with beam sizes of tens and hundreds of milli-arcseconds. The distance, stellar parameters, and geometry in each disk are summarized in Table [1](#tab:Stellar). A summary of the multi-wavelength datasets, final imaging properties, and project codes for both ALMA and VLA observations can be found in Table [\[tab:Observations\]](#tab:Observations), and a gallery of the dust continuum images in Figure [1](#fig:Observations).

The ALMA data were self-calibrated using CASA 6.4.3.27. All spectral windows and scans are combined to improve the signal-to-noise ratio (SNR) using `combine=‘spws, scans’` within the CASA `gaincal` task. We began applying phase self-calibration with an initial solution time interval equal to the total observation time. The new self-calibrated data were imaged and the signal-to-noise ratio (SNR) is computed. If SNR improves by at least a factor of 5%, we continue applying successive phase self-calibration iterations with a smaller solution time interval (it decreases by a factor of 3 in consecutive iterations). Throughout each self-calibration step, we utilized `applymode=‘calonly’` to calibrate data only, and do not apply flags from solutions. A final amplitude self-calibration iteration with an infinitive solution time interval (`solint=‘inf’`) and combining spectral windows and scans (`combine=‘spws,scans’`) is also applied to the data. The calibrated VLA data were taken from the Disks@EVLA Collaboration[^1]. The calibration process for the Disks@EVLA data is provided in Section 2.2 of (cite: Perez_2015) or Section 2 of (cite: Andrews_2014). For imaging, we employed the TCLEAN task with a multi-scale CLEAN algorithm with scales corresponding to point sources, 1, 2, and 3 times the beam Full Width at Half Maximum (FWHM). Additionally, we applied a mask covering the disk emission.

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | ALMA/ | $\nu$ | Baselines | On-Source | robust | Synthesized Beam | rms Noise | ALMA/VLA |  |  |
|  | VLA Band | (GHz) | (m-km) | Time (min) |  | (mas $\times$ mas; deg) | ($\mu \rm Jy \ beam^{-1}$) | Project Code |  |  |
| CQTau | 7 | 338 | 21 - 0.4 | 22.1 | 0.5 | 674 $\times$ 469; 15 | 530.0 | 2011.0.00320.S |  |  |
|  | 6 | 225 | 3 - 8.5 | 93.2 | 0.5 | 267 $\times$ 231; -16 | 35.0 | 2013.1.00498.S |  |  |
|  | Ka | 34 | 80 - 11.1 | 115.1 | 2.0 | 401 $\times$ 293; 61 | 7.7 | AC982 |  |  |
| UXTau A | 7 | 344 | 16 - 1.5 | 54.4 | 0.5 | 193 $\times$ 151; -22 | 49.0 | 2015.1.00888.S |  |  |
|  | 6 | 232 | 15 - 1.6 | 14.1 | 0.5 | 253 $\times$ 209; 11 | 37.3 | 2013.1.00498.S |  |  |
|  | 3 | 96 | 18 - 7.6 | 8.6 | 0.5 | 296 $\times$ 140; 49 | 27.0 | 2016.1.01042.S |  |  |
|  | Q | 42 | 78 - 11.1 | 144.2 | 2.0 | 315 $\times$ 235; -57 | 14.9 | AC982 |  |  |
| LkCa15 | 9 | 689 | 21 - 0.4 | 17.1 | 0.5 | 306 $\times$ 229; -35 | 1650.0 | 2011.0.00724.S |  |  |
|  | 7 | 340 | 34 - 8.5 | 162.1 | 0.5 | 47 $\times$ 27; 23 | 16.5 | 2018.1.00350.S |  |  |
|  | 6 | 229 | 15 - 12.7 | 140.2 | 0.5 | 84 $\times$ 57; -30 | 14.4 | 2018.1.01255.S |  |  |
|  | Q | 44 | 78 - 27.9 | 1129.0 | 2.0 | 149 $\times$ 144; 64 | 4.2 | AC982,13B-381,12B-196 |  |  |
| RXJ1615 | 9 | 689 | 21 - 0.4 | 22.2 | 0.5 | 288 $\times$ 193; -80 | 1750.0 | 2011.0.00724.S |  |  |
|  | 7 | 339 | 18 - 3.7 | 59.4 | 0.5 | 73 $\times$ 61; 84 | 28.0 | 2012.1.00870.S |  |  |
|  | Q | 44 | 243 - 11.1 | 152.4 | 2.0 | 498 $\times$ 294; -17 | 16.2 | 13B-381 |  |  |
| SR24S | 9 | 689 | 21 - 0.4 | 25.2 | 0.5 | 368 $\times$ 190; -78 | 1910.0 | 2011.0.00724.S |  |  |
|  | 7 | 337 | 15 - 1.6 | 2.0 | 0.5 | 183 $\times$ 155; 61 | 367.1 | 2013.1.00157.S |  |  |
|  | 6 | 231 | 15 - 1.6 | 21.7 | 0.5 | 222 $\times$ 192; 51 | 67.1 | 2013.1.00091.S |  |  |
|  | 3 | 109 | 19 - 9.5 | 7.2 | 0.5 | 233 $\times$ 155; 61 | 33.4 | 2016.1.01042.S |  |  |
|  | Ka | 34 | 78 - 36.6 | 327.5 | 2.0 | 180 $\times$ 148; 31 | 7.7 | AC982 |  |  |
| DMTau | 9 | 676 | 15 - 0.5 | 79.9 | 0.5 | 309 $\times$ 287; -11 | 674 | 2016.1.00565.S |  |  |
|  | 8 | 480 | 15 - 1.1 | 11.1 | 0.5 | 150 $\times$ 115; -6 | 660 | 2015.1.01137.S |  |  |
|  | 7 | 318 | 15 - 0.9 | 79.5 | 0.5 | 455 $\times$ 366; 7 | 139 | 2016.1.00565.S |  |  |
|  | 6 | 232 | 15 - 15.2 | 134.3 | 0.5 | 32 $\times$ 21; 33 | 8.4 | 2018.1.01755.S |  |  |
|  | 4 | 145 | 15 - 1.1 | 2.0 | 0.5 | 546 $\times$ 448; 24 | 84 | 2015.1.00296.S |  |  |
|  | 3 | 109 | 19 - 7.6 | 8.6 | 0.5 | 296 $\times$ 158; 48 | 27 | 2016.1.01042.S |  |  |
|  | Q | 42 | 78 - 22814 | 378.3 | 2.0 | 259 $\times$ 173; -65 | 9.0 | AC982 |  |  |

![](Gallery_Observations.pdf)

# Visibility modeling

We fit the de-projected continuum visibilities of the dust continuum emission to extract the highest angular resolution from the observational data. The de-projection of the visibilities is done using the FRANKENSTEIN tools[^2] in (cite: Jennings_2020), where the geometric projecting effects due to the orientation of the interferometer’s baselines are corrected. The de-projection consists of rotating the baseline coordinates using the disk’s position angle, and then stretching the baseline coordinates along the minor axis of the disk using the cosine of the disk inclination.

We assume azimuthal emission symmetry, which is a first order approximation of the disk morphologies in this work, as shown in Figure [1](#fig:Observations), although it is known that some these disk present some degree of azimuthal asymmetry (cite: Hashimoto_2021).

The interferometric visibilities (which for a given uv-distance, corresponds to the Real and Imaginary part of the visibility and its associated weight) are extracted from the self-calibrated measurement sets using a modified version from the *export_uvtable* function in (cite: uvplot). In our version, the uv-distances are normalized using the wavelength of each channel and spectral window, instead of the average wavelength of the whole data set. The visibility modeling is done using a non-parametric fit (Section [3.1](#sec:non-parametric)) for observations with high signal-to-noise ratio (SNR), and with a parametric model for low SNR observations (Section [3.2](#sec:parametric)). In both cases, constraints to the phase shift and geometry of each observation (Section [3.3](#sec:geometry)) are necessary when de-projecting and fitting the visibilities.

## Non-parametric fit

The non-parametric visibility modeling is performed using FRANKENSTEIN (cite: Jennings_2020), where the disk brightness (represented as a Fourier-Bessel series) is reconstructed by fitting the real part of the visibilities as a function of the uv-distance (baselines). The imaginary part of the visibilities, that mainly traces the emission from non-symmetric structures, is not used by FRANKENSTEIN given the azimuthal symmetry assumption (the imaginary part of the visibilities in our observations tends to zero when averaged over all orientations).

The reconstructed radial profile depends on two hyper-parameters: $\alpha$, $w_{\rm smooth}$. The former mimics the signal-to-noise (SNR) threshold below which the data are not used when fitting the visibilities, and the latter controls the smoothness of the fit to the power-spectrum (cite: Jennings_2020; Jennings_2021).

These hyper-parameters do not have strong effects on the reconstructed brightness profiles for disks with a high SNR; however, this is not the case for low SNR data, where a particular combination of $\alpha$, $w_{\rm smooth}$ can imprint oscillatory artifacts on the reconstructed brightness profile. For this reason, we fit all the observations using a grid of hyper-parameters varying between $\alpha = [1.05-1.30]$, and $\log_{10}(w_{\rm smooth}) = [-4, -1]$, and we choose by visual inspection the pair of hyper-parameters that minimize the oscillatory artifacts.

The longest wavelengths in our sample (Band Q and Ka from VLA) have a low SNR at all uv-distances. Thus, for these long wavelength observations, we use FRANKENSTEIN on the binned visibilities (binsize of 10 k$\lambda$).

The chosen hyper-parameters for each data set are summarized in Table [\[tab:Visibility\]](#tab:Visibility). Additional fit parameters (e.g., maximum fitting radius, number of radial points to sample the radial profile) have no important effects on the reconstructed brightness profile if the recommendations described in (cite: Jennings_2020) are taken into account. We fit the data in the logarithmic brightness space, which helps to reduce the oscillatory artifacts in the reconstructed brightness profile, and prevents negative values in the reconstructed brightness profile. However, we found no important differences when fitting the data in a linear brightness space.

## Parametric fit

The FRANKENSTEIN models for VLA data were computed by binning the visibilities. Since this procedure results in information loss, we also directly fit the non-binned VLA visibilities using a parametric model with a given intensity profile $I(r)$. The visibilities of the parametric model are computed using a Hankel transform $\mathcal{H}$ (cite: Pearson_1999):

$$\begin{equation}
    V(q) = \mathcal{H} (I(r)) = 2\pi \int _{0}^{\infty}I(r) J_0(2\pi q r) dr, 
\end{equation}$$ where $r$ is the disk radius, $J_0$ is the zeroth-order Bessel function of the first kind, $q=\sqrt{u^2+v^2}/\lambda$ is the de-projected baseline, $\lambda$ is the wavelength, and $u,v$ are the coordinates of the baseline vectors.

For each disk, the morphology of the parametric models is motivated by the brightness distribution inferred at ALMA wavelengths with FRANKENSTEIN (an extended discussion on the disk morphology is done for each particular disk in Section [5](#sec:discussion)). We also consider other physical processes that can contribute to the emission at VLA wavelengths, as free-free emission from ionized gas. However, we assume that the emission from spinning nanometer-size dust (cite: Hoang_2018) does not contribute to the observed emission, as scattering properties (taken into account in this work) can mimic similar effects to those expected from spinning dust (cite: Sierra_2020), making it difficult to differentiate between the two processes.

The free-free emission is modeled by including a compact emission point source at the disk center, simulating the expected compact free-free emission at these long wavelengths reported by previous centimeter observations of UXTau A, LkCa15, RXJ1615, and SR24S in (cite: Zapata_2017). For DM Tau, no compact free-free emission was detected in (cite: Zapata_2017), however (cite: Terada_2023) found that the free-free emission from ionized gas in DM Tau is variable. We include the free-free component in all disks, and then we compare its inferred flux with previous estimations in Appendix [9.2](#app:parametric_models).

The parameter space of the free parameters describing the parametric fit is explored using a Markov chain Monte Carlo (cite: Foreman_2013). The best fit parametric model is found by maximizing the logarithm of the likelihood function, given by

$$\begin{eqnarray}
\nonumber \ln \mathcal{L} &=& -\frac{1}{2} \sum_j W_j \left[\rm   ( ReV^{obs}_j - ReV^{mod}_j)^2 + \right. \\
 & &  \left. (\rm ImV^{obs}_j - ImV^{mod}_j)^2  \right],
\label{eq:posterior_vis}
\end{eqnarray}$$ where $W_j$ are the weights of the visibilities, and $\rm V^{obs}_j, V^{model}_j$ are the observed and model visibilities, respectively.

## Phase shift and Geometry

The offset of the disk center with respect to the phase center ($\rm \delta Ra, \delta Dec$), disk inclination ($i$), and disk position angle (PA) are fitted for each observation.

In most of the cases, the offset is computed by minimizing the imaginary part of the visibilities (cite: Isella_2019). However, in some cases (e.g. SR24S with some small azimuthal asymmetries), the obtained phase shift does not match with the disk center (visual inspection), thus, in a few cases, we fit a 2D Gaussian function (in the image plane) using a very low angular resolution image (using the UVTAPER task in CASA), where the azimuthal asymmetry vanishes. The methodology used for each observation is summarized in Table [\[tab:Visibility\]](#tab:Visibility).

The disk inclination and position angle are fitted by minimizing the spread of the de-projected visibilities for circular annuli in the visibility space (cite: Isella_2019). Error bars are computed from the percentiles 16th and 84th. The inferred disk inclination for a certain disk is consistent within the error bars. However, variations can also occur because disks are not perfectly settled to the midplane, depending on factors such as grain size and turbulent state (cite: Dubrulle_1995; Schapler_2004). Additionally, the contribution of the upper layers becomes more significant at smaller wavelengths (cite: Sierra_2019).

The inferred disk geometry for all the ALMA observations are summarized in Table [\[tab:Visibility\]](#tab:Visibility). The geometry derived from the VLA data is poorly constrained and is not included in this Table.

One of the goals in this paper is to compare the brightness radial profiles using multi-wavelength observations of each disk. For this reason, the geometry of each disk is fixed for all wavelengths. The chosen disk geometry is based on the following criteria: 1- The contribution from the disk mid-plane should be important (long wavelengths where the emission is optically thin are good candidates). 2- The angular resolution (or uv-distances) should be good enough to resolve the disk geometry. 3- High SNR (i.e., the disk geometry is well constrained). The latter discards the Band Q and Ka observations, where the geometry is poorly constrained. Thus, our final decision on the disk geometry is based on Band 6, 3, 6, 7, 6, 6, for CQTau, UXTau A, LkCa15, RXJ1615, SR24S and DMTau, respectively.

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | Band | $\alpha$ | $\log_{10}(w_{\rm s})$ | $i^{(*)}$ | PA$^{(*)}$ | ChanWidth | Centering | Resolution | Multi-wave |
|  |  |  |  | (deg) | (deg) | (MHz) | methodology | (mas) | analysis? |
| CQTau | 7 | 1.3 | -1 | $37.9_{-0.3}^{+0.5}$ | $46.7_{-0.1}^{+1.8}$ | 29 | Min vis scatter | 255.3 | No |
|  | 6 | 1.3 | -4 | $36.3^{+0.1}_{-0.6}$ | $46.5^{+0.9}_{-0.4}$ | 500 | Gaussian fit | 149.6 | Yes |
|  | Ka | 1.05 | -4 | \- | \- | 128 | Gaussian fit | 238.4 | Yes |
| UXTau A | 7 | 1.05 | -1 | $41.9_{-0.1}^{+0.5}$ | $168.0_{-0.5}^{+0.1}$ | 500 | Min vis scatter | 75.1 | Yes |
|  | 6 | 1.3 | -1 | $41.9_{-0.7}^{+0.1}$ | $166.6_{-0.2}^{+0.8}$ | 117 | Min vis scatter | 136.5 | Yes |
|  | 3 | 1.05 | -4 | $40.9_{-0.1}^{+0.6}$ | $168.7_{-0.5}^{+1.0}$ | 500 | Min vis scatter | 112.3 | Yes |
|  | Q | 1.05 | -4 | \- | \- | 128 | Gaussian fit | 157.0 | Yes |
| LkCa15 | 9 | 1.2 | -4 | $50.8_{-0.8}^{+0.2}$ | $61.7_{-0.1}^{+2.0}$ | 375 | Min vis scatter | 171.9 | No |
|  | 7 | 1.3 | -1 | $50.5_{-0.5}^{+0.1}$ | $61.6_{-0.2}^{+0.1}$ | 250 | Min vis scatter | 17.7 | Yes |
|  | 6 | 1.3 | -1 | $49.7_{-0.2}^{+0.1}$ | $62.1_{-0.1}^{+0.4}$ | 250 | Min vis scatter | 21.5 | Yes |
|  | Q | 1.05 | -4 | \- | \- | 128 | Gaussian fit | 120.0 | Yes |
| RXJ1615 | 9 | 1.05 | -4 | $40.6_{-0.9}^{+9.2}$ | $150.0_{-5.0}^{+0.1}$ | 375 | Min vis scatter | 191.4 | No |
|  | 7 | 1.3 | -1 | $46.9_{-0.9}^{+0.1}$ | $146.1_{-0.1}^{+0.6}$ | 235 | Min vis scatter | 34.2 | Yes |
|  | Q | 1.05 | -4 | \- | \- | 128 | Gaussian fit | 167.0 | Yes |
| SR24S | 9 | 1.3 | -1 | $48.7_{-0.6}^{+0.2}$ | $27.2_{-0.5}^{+0.1}$ | 375 | Gaussian fit | 157.2 | No |
|  | 7 | 1.3 | -1 | $48.6_{-0.2}^{+0.1}$ | $27.3_{-0.3}^{+0.1}$ | 16 | Gaussian fit | 118.2 | Yes |
|  | 6 | 1.3 | -1 | $47.8_{-0.1}^{+0.1}$ | $26.6_{-0.6}^{+0.1}$ | 469 | Gaussian fit | 117.2 | Yes |
|  | 3 | 1.3 | -1 | $44.8_{-0.1}^{+2.4}$ | $25.1_{-0.3}^{+4.0}$ | 63 | Gaussian fit | 98.6 | Yes |
|  | Ka | 1.05 | -4 | \- | \- | 128 | Gaussian fit | 120.1 | Yes |
| DMTau | 9 | 1.05 | -4 | $36.6_{-0.3}^{+0.1}$ | $156.3_{-1.1}^{+0.1}$ | 234 | Min vis scatter | 204.0 | No |
|  | 8 | 1.05 | -1 | $39.9_{-9.3}^{+0.4}$ | $153.3_{-7.3}^{+4.9}$ | 125 | Min vis scatter | 111.9 | Yes |
|  | 7 | 1.3 | -1 | $40.1_{-4.7}^{+1.8}$ | $153.1_{-4.2}^{+0.9}$ | 63 | Min vis scatter | 153.8 | No |
|  | 6 | 1.3 | -1 | $35.7_{-0.1}^{+0.1}$ | $157.1_{-0.1}^{+0.4}$ | 469 | Min vis scatter | 14.2 | Yes |
|  | 4 | 1.1 | -1 | $32.7_{-0.6}^{+0.1}$ | $156.0_{-6.9}^{+0.2}$ | 63 | Min vis scatter | 273.4 | No |
|  | 3 | 1.3 | -1 | $34.8_{-0.6}^{+2.6}$ | $155.2_{-4.9}^{+0.5}$ | 63 | Min vis scatter | 72.8 | Yes |
|  | Q | 1.1 | -4 | \- | \- | 128 | Gaussian fit | 69.6 | Yes |

\
$^{(*)}$ The inferred inclination ($i$) and position angle (PA) for each observation are reported in this table. However, both values are fixed to those summarized in Table [1](#tab:Stellar) during the visibility modeling.

## Results from the visibility modeling

Figure [2](#fig:Visibilities) shows the visibility modeling results for the observations in our sample. In all cases, the axi-symmetric visibility model (from Frankenstein or parametric) is a good representation of the observed visibilities. Note that the uv-coverage of each observation is diverse. For example, for LkCa15, the maximum baseline for Band 6 and 7 is close to 10M$\lambda$, but for Band 9 it is close to 1M$\lambda$. This limits the disk sub-structures that can be inferred from observations.

![](Gallery_Visibilities.pdf)

![](Gallery_RadProfiles.pdf)

Figure [3](#fig:Vis_RadProfile) shows the normalized brightness radial profile for each observation from the visibility fit and from the image plane. The radial profiles in the image plane were computed using GOFISH (cite: GoFish) and the same offset and disk geometries than in the visibility fits. We assume a filling factor (cite: Thompson_2017) of 1 everywhere. This assumption is valid at large radius, where the solid angle of concentric rings is larger than that of the beam size. However, in the most inner region ($\lesssim$ 50 mas), the radial profiles from the image plane would need a filling factor correction. Nevertheless, the radial profiles from the image plane are only used to visualize the differences compared with the radial profiles computed from the visibility fit, and they are not used in the rest of the manuscript.

The error bars $(\Delta_{\rm img})$ in the radial profile from the image plane $(I_{\rm img})$ do take into account the azimuthal intensity asymmetries, while they are not originally taken into account in the error bars from the visibility fits. The ratio of azimuthal asymmetry $(\Delta_{\rm img}/I_{\rm img})$ is small in all cases, confirming that the axi-symmetric assumption is a good approximation of the disk morphologies. We add the azimuthal asymmetries error bars computed in the image plane to the radial profile uncertainty computed from the visibility fit ($\Delta_{\rm vis}$) as: $\Delta I = \sqrt{(\Delta_{\rm vis})^2 + (I_{\rm vis} \Delta_{\rm img}/I_{\rm img})^2}$, where $I_{\rm vis}$ is the intensity radial profile from the visibility fit. These uncertainties are included in the radial profiles of Figure [4](#fig:Radial_Profiles). The bottom panels of the same Figure show the flux calibration error bar for all wavelengths. This uncertainty dominates by far the uncertainty in each radial profile.

The radial profiles from the visibility fit reveal higher contrasts between rings and gaps compared to the azimuthal radial profiles computed from the CLEAN images (Figure [1](#fig:Observations)). For example, in the brightness radial profile of LkCa15 in Bands 6 and 7, we clearly identify three main rings from the visibility fit (at $0.277^{\prime\prime}, 0.433^{\prime\prime}, 0.635^{\prime\prime}$, as also reported by (cite: Long_2022)). Additionally, there is a tentative faint ring around $\sim 1.07^{\prime \prime}$, which is also visible in the radial profile of the Band Q image, albeit at a radius of $\sim 0.99^{\prime \prime}$. Note that the width of the rings at $0.433^{\prime\prime}, 0.635^{\prime\prime}$ in Band 6 looks narrower than those at Band 7, possibly due to dust traps (cite: Pinilla_2012). Additionally, the contrast between the rings and gaps is more pronounced in Band 6, likely due to optical depth effects. These characteristics and differences are crucial when constraining the radial profiles of dust properties in Section [4](#sec:multiwave).

The parametric model for all disks was chosen based on the morphology observed at ALMA. For example, in LkCa15, the parametric model is given by two Gaussian functions at a fixed radial position of $0.433^{\prime\prime}, 0.635^{\prime\prime}$, and a point source at the disk center. We also tested the inclusion of the ring structures at $0.277^{\prime\prime}$ and $0.99^{\prime\prime}$. However, the chi-square value ($\chi^2$) does not exhibit a significant improvement when these rings are added to the model.

The radial profiles in Figure [3](#fig:Vis_RadProfile) are shown at their intrinsic angular resolution. Starting from Section [4](#sec:multiwave) and beyond, the radial profiles for a specific disk are convolved to the same angular resolution, corresponding to the lowest angular resolution among the multi-wavelength observations of each disk.

As mentioned in Section [3.2](#sec:parametric), the FRANKENSTEIN visibility model is influenced by bin size and hyper-parameters for the VLA observations with low SNR. Conversely, the parametric fit provides a robust radial profile. Consequently, the parametric model is selected as the radial profile model for VLA data across all disks. Table [2](#tab:parametric_fit) in Appendix [9.2](#app:parametric_models) provides a summary of the chosen parametric models for each disk and the best fit parameters.

Figure [8](#fig:models) in Appendix [9.1](#app:best_models) shows the CLEAN image of the disk models (sampled at the same uv-coverage than the observations). The color scale is the same than each panel in Figure [1](#fig:Observations). The difference between observations and model (Residuals) is shown in Figure [9](#fig:residuals). Although most of them have low non-axi-symmetric residuals, some exceed $+5\sigma_{\rm rms}$ or fall below $-5\sigma_{\rm rms}$. Various factors may contribute to these residuals, such as the disk potentially being brighter at the inner wall of the ring on the far side due to disk inclination, uncertainties in parameters like disk inclination, position angle, disk center, or elevated emission surfaces (cite: Andrews_2021). Also note that most of the azimuthal asymmetries observed at very long wavelengths (VLA observations) have a SNR $<3$, making it difficult to distinguish them from thermal noise. The specific disk structures are further discussed in Section [5](#sec:discussion).

# Constraints on Dust Properties

The spatially-integrated dust continuum emission at millimeter wavelengths has been used to infer dust properties of protoplanetary disks, including mean temperature, optical depths, average maximum grain size, and dust mass. This is typically achieved by fitting a black-body model to their spectral energy distribution (cite: Rilinger_2023).

Owing to the lack of multi-wavelength observations at high angular resolution, the spatial modeling of spectral energy distributions (SED) have only been spatially modeled in a small fraction of disks (cite: Perez_2012; Liu_2017; Carrasco-Gonzalez_2019; Macias_2021; Sierra_2021). In this work, we are able to resolve the expected optically thick rings around six transition disks and model the SED as function of radius. Figure [4](#fig:Radial_Profiles) shows the brightness temperature for the six transition disks in this work. The radial profiles of each disk are convolved to the same angular resolution (indicated by the horizontal bar in each panel), determined by the lowest angular resolution detailed in the last column of Table [\[tab:Visibility\]](#tab:Visibility). The effect of radial beam smearing is discussed in Appendix [10](#app:smearing).

Note that not all wavelengths were included in our multi-wavelength analysis. We opted to exclude observations with low angular resolution (compared with the rest of the multi-wavelength data) and avoided convolving most of the observations using a large beam. Additionally, we also decided to neglect the short wavelength observations at Band 9 because they likely primarily capture dust emission from the upper layers of the disk, where smaller grain sizes are expected compared to those traced by longer wavelengths in the mid-plane (cite: Sierra_2020). The last column in Table [\[tab:Visibility\]](#tab:Visibility) summarizes which datasets are used in the multi-wavelength analysis.

![](RadialProfiles.pdf)

.

The SED is fitted at each radius using the emergent intensity of the dust continuum emission at frequency $\nu$ in (cite: Sierra_2020), which is given by $$\begin{equation}
    I_{\nu} = B_{\nu}(T_d) \left[1- \exp(-\tau_{\nu}/\mu) + \omega_{\nu} F(\tau_\nu, \omega_\nu) \right],
    \label{eq:Intensity_scatI}
\end{equation}$$ where $B_{\nu}(T_d)$ is the Planck function evaluated at the dust temperature $T_d$, $\tau_{\nu}$ is the total optical depth (absorption and scattering), $\mu$ is the cosine of the disk inclination, $\omega_\nu$ is the dust albedo, and $F(\tau_\nu, \omega_\nu)$ is the contribution of scattering to the emergent intensity, given by

$$\begin{eqnarray}
    \nonumber F(\tau_{\nu}, \omega_{\nu}) = \frac{1}{\exp(-\sqrt{3}\epsilon_{\nu} \tau_{\nu} ) (\epsilon_{\nu} -1) - (\epsilon_{\nu}+1)} \times\\
    \nonumber \left[ \frac{1 - \exp(-(\sqrt{3}\epsilon_{\nu}+1/\mu)\tau_{\nu})}{\sqrt{3}\epsilon_{\nu}\mu +1} \right.+ \\
    \left. \frac{\exp(-\tau_{\nu}/\mu) - \exp(-\sqrt{3}\epsilon_{\nu} \tau_{\nu})}{\sqrt{3}\epsilon_{\nu} \mu -1} \right],
    \label{eq:Intensity_scatII}
\end{eqnarray}$$ where $\epsilon_\nu = \sqrt{1-\omega_\nu}$. The main effect of scattering (Eq. [\[eq:Intensity_scatII\]](#eq:Intensity_scatII)) is decreasing the emergent intensity in the optically thick regime, making it possible to explain spectral indices below of 2, as discussed in previous works (e.g., (cite: Liu_2019; Zhu_2019; Sierra_2020)).

The albedo and absorption dust opacity coefficient $\kappa_{\nu}$ are taken from (cite: Birnstiel_2018), and the dust grains are assumed to follow a particle size distribution (number of grain sizes per size bin) given by $n(a)da \propto a^{-p}da$, where the minimum grain size is fixed to 0.05 $\mu m$, and the maximum grain size $a_{\rm max}$ is a free parameter. The slope of the particle size distribution $p$ is fixed to 3.0. The expected value from simulations is between 2.5 and 3.5, when the maximum grain size is regulated by drift and fragmentation, respectively (cite: Birnstiel_2012). However, we tested $p$ values within this range, and the qualitative conclusions are not sensitive to this particular choice.

Equation [\[eq:Intensity_scatI\]](#eq:Intensity_scatI) can be evaluated given the dust temperature $T_{\rm d}$, maximum grain size $a_{\max}$ (which controls $\omega_{\nu}$ and $\kappa_{\nu}$), and dust surface density $\Sigma_{\rm d}$ (which controls the total optical depth: $\tau_{\nu} = \kappa_{\nu} \Sigma_{\rm d}/(1-\omega_{\nu})$). We use a Markov chain Monte Carlo (MCMC) method (cite: Foreman_2013) using 24 walkers and 10000 steps to explore the space parameter of $a_{\rm max}, \Sigma_{\rm d}$, and $T_{\rm d}$ at each radius. The chi-squared in the posterior distribution is defined as $$\begin{equation}
    \chi^2 = \sum _n \left( \frac{I_{\nu_n} - I_{\nu_n}^{\rm model}}{\Delta I_{\nu_n}} \right)^2,
\end{equation}$$ $I_{\nu_n}^{\rm model}$ is the model intensity evaluated from Equation [\[eq:Intensity_scatI\]](#eq:Intensity_scatI), and $\Delta I_{\nu_n}$ is the uncertainty of the n-th intensity. The absolute flux uncertainty is taken into account in $\delta I_{\nu_n}$ at each band according to the ALMA proposer’s guide: 5% in Band 3 and 4, 10% in Band 6 and 7, and 20% in Bands 8 and 9.

The prior is given by $p(a_{\rm max}) \times p(\Sigma_{\rm d}) \times p(T_{\rm d})$, where $p(a_{\rm max})$, $p(\Sigma_{\rm d})$ are the maximum grain size and dust surface density priors, given by a log-uniform distribution within the explored parameter space, and the temperature prior is defined as $$\begin{equation}
    p(T_{\rm d}) = \exp \left[ -\frac{1}{2} \left(\frac{T_{\rm prior} - T_{\rm d}}{\sigma_{T_{\rm prior}}}\right )^2 \right],
\end{equation}$$ i.e., the probability of a model with a temperature $T_{\rm d}$ decreases if it deviates from $T_{\rm prior}$. The latter is computed from the temperature of an passively irradiated disk $T_{\rm prior} = (0.02 L_* / 8 \pi \sigma_{\rm B} r^2)^{1/4}$. We use a wide temperature width $\sigma_{T_{\rm prior}} = 50$ K to ensure that this prior does not dominate the posterior probability distribution.

The inclusion of this prior decreases the degeneracy between the free parameters, especially when the number of wavelengths used to fit the SED is less than or equal to the number of free parameters.

The explored parameter space is log-spaced between 300 $\mu$m $\leq a_{\rm max} \leq 30$ cm, $10^{-6}$ g cm$^{-2}$ $\leq \Sigma_{\rm d}$ $\leq 10$ g cm$^{-2}$, and $3$ K $\leq T_{\rm d}$ $\leq 300$ K. The smallest value for the maximum grain size is chosen to avoid degeneracy between a small-grain solution ($a_{\rm max} < 300 \mu$m) and large grains ($a_{\rm max} \geq 300 \mu$m). As shown in Figure 4 of (cite: Birnstiel_2018), the spectral index around 300 micrometers is degenerated for large or small grain sizes. However, we also did some tests including small maximum grain sizes $a_{\rm max} = 10 \ \mu$m, but found that the walkers tend to the large maximum grain size regime after sufficient steps. The inclusion of small maximum grain sizes ($a_{\rm max} < 300 \mu$m) only delays the walkers from reaching the space parameter with the maximum posterior probability ($a_{\rm max} \geq 300 \ \mu$m.)

The best fit of each parameter is shown in Figure [5](#fig:Posterior) for the 6 transition disks in this work. The vertical lines mark the position of the rings inferred from the visibility fit (Section [3](#sec:vismod)). The error bars are computed from the percentile 32 and 68 respectively. The dust mass is shown in the bottom of each top panel, while the angular resolution of each disk is shown in the bottom panels.

Figure [6](#fig:Optdepth) shows the optical depth constraints resulting from the dust properties in Figure [5](#fig:Posterior) at different wavelengths.

![](Results_emcee_LG.pdf)

![](Results_optdep_emcee_LG.pdf)

# Discussion

The results from the disk substructures computed from the visibility fit for each observation (Figures [2](#fig:Visibilities) and [3](#fig:Vis_RadProfile)), and the dust property constraints from the multi-wavelength fit (Section [4](#sec:multiwave)), give clues about the physical origin of the large cavities observed in the six transition disks in this work. However, before discussing the results from each individual disk (Sections [5.2](#sec:Planet)-[5.3](#sec:graingrowth)), we summarize the various caveats associated with our modeling below.

## Model limitations

The exact dust properties inferred from the multi-wavelength analysis depend on the physical assumptions described in the previous section (e.g., particle size distribution slope, spherical and compact dust grains). However, general properties such as the peak position of the dust surface density or maximum grain size, are unchanged under these physical assumptions.

The maximum grain size estimations in this work are similar to previous analysis where the dust continuum SED has been modeled, and where millimeter and centimeter grain sizes have been inferred (cite: Perez_2012; Carrasco-Gonzalez_2019; Ueda_2020). However, it is important to remark that smaller grain sizes (hundreds of microns or smaller grain sizes) have been inferred from polarized observations (cite: Kataoka_2016; Hull_2018; Mori_2019). Our results are biased by the spectral index analysis. Alleviating the tension between the grain size estimations from polarization and spectral index is beyond the scope of this paper. An exception to the SED modeling has been found in the disk around DM Tau (cite: Liu_2024), where the dust emission from localized substructures is consistent with $a_{\rm max} \gtrsim 300 \ \mu$m, but the rest of the disk is consistent with small grains ($\lesssim 50 \mu$m).

On the other hand, angular resolution limitations could impact the inferred dust properties profiles. In particular, the disk cavities could potentially be contaminated by emission from optically thick rings. In such cases, the cavities would present faint emission with low spectral indices, which can be interpreted as optically thin emission with large grain sizes. Given the angular resolution of the data, it is not possible to rule out the possibility of smearing effects within the cavities, specially in those disks where large grain sizes are inferred in this region. A full discussion of the radial smearing effects are presented in Appendix [10](#app:smearing). We also emphasize that our method for inferring the intrinsic angular resolution of a FRANKENSTEIN fit does not assess the ability of such fit to resolve two independent structures (e.g., two rings). Rather, the intrinsic angular resolution corresponds to the “point spread function” of a FRANKENSTEIN fit done to an infinitely narrow ring. We tested different models with smaller separations between the two rings, but there is no clear limit at which the visibility fit is unable to separate them. The only limit is given by the sampling of the radial profile, which is not a physical measurement of the angular resolution, but is determined by the Nyquist sampling theorem (cite: Thompson_2017), which should always be satisfied. See more details in Appendix [8](#app:angular).

Additionally, we assume that the disks are axi-symmetric and compute their azimuthally averaged properties. However, some degree of asymmetry has been observed in some of them (see references in the discussion of each particular disk). In a few cases, these asymmetries are consistent with thermal noise (specially at long wavelengths).

Although we only study the multi-wavelength emission in a radial extend where the azimuthal asymmetries are low or negligible (See Section [9.1](#app:best_models)), the dust properties constraints in this work only pretend to explain the azimutally average dust properties of each analyzed disk, and a bi-dimensional analysis of the disks is beyond the scope of this work. In some cases, such as DMTau, the axi-symmetric structure observed at ALMA Bands, and the azimuthal asymmetries observed at Band Q may be explained by optical depth effects (cite: Liu_2024). In such cases, the constraints on the dust properties are mainly dominated by the morphology observed at ALMA wavelengths.

##  Disks with dust traps as a possible origin of the cavity

Disks with dust surface density and grain size maxima at ring positions are consistent with dust trap models (cite: Pinilla_2012b). The dust trap can be induced by a companion (a planet or a close binary) or a dead zone. However, if a deep gas cavity is also observed, it rules out the possibility of a dust trap created by a dead zone (cite: vanderMarel_2016), and supports the idea of a companion origin. In the following, we discuss the results obtained from disks where both a dust trap (identified in this work) and gas cavities (from the literature) have been inferred. These findings may suggest that the origin of these large cavities is a companion.

**UXTau A:** Dust continuum observations of the disk around UXTau A have been previously reported by (cite: Pinilla_2018) and (cite: Francis_2020). From the visibility modeling in this work (Figure [3](#fig:Vis_RadProfile)), we confirm the ring-shaped structure, with a peak at $0.236^{\prime \prime}$ (33.0 au). Additionally, the disk emission exhibits azimuthal asymmetries at Band 6 and 7 (Figure [9](#fig:residuals)), with higher intensities observed towards the East. The Band 3 image appears non-axi-symmetric, but these asymmetries are created by the visibility coverage and the elongated beam, as shown by the perfect axi-symmetric disk model sampled at the same visibilities in Figure [8](#fig:models). This is demonstrated in the model image of a perfectly axi-symmetric disk. Similarly, Band Q exhibits azimuthal structures along the major axis of the beam. The residuals of the enhanced emission at the South of the disk in Band Q has a SNR $< 5$, as shown in Figure [9](#fig:residuals).

The dust properties constraints (Figure [5](#fig:Posterior)) shows a peak in the dust surface density, maximum grain size, and dust temperature aligning with the location of the main ring, exhibiting characteristics consistent with dust trap signatures, which can be triggered by a companion or a dead zone.

No planet candidates have been found in UXTau A using H$\alpha$ observations (cite: Zurlo_2020). The sensitivity of the H$\alpha$ observations are consistent with a upper limit to the mass of the planet of $9$ Jupiter mass at $\sim$ 22 au. The $^{12}$CO (J:3-2) observations in (cite: Wolfer_2023) reveals a gas cavity and a ring structure in the gas that peaks near the dust ring.

**LkCa15:** Dust continuum observations of the disk around LkCa15 at high resolution have been studied by (cite: Isella_2014), (cite: Facchini_2020) and (cite: Long_2022), where three rings at at 0.277$^{\prime \prime}$ (43.5 au), 0.433$^{\prime \prime}$ (68.1 au), 0.636$^{\prime \prime}$ (100 au) have been inferred from the radial profiles in the image plane and from visibility modeling. We note a fourth faint outer ring at 1.070$^{\prime \prime}$ (168.2 au) from both the image plane and visibility modeling at ALMA wavelengths. This faint ring can also be inferred from the radial profile in the image plane at Band Q, but at a slightly smaller radius of 0.990$^{\prime \prime}$ (155.6 au).

The visibility modeling residuals at Band 6 and 7 in Figure [9](#fig:residuals) matches with those in (cite: Long_2022). At Band Q, there are no residuals with SNR $> 5$. And at Band 9, there are positive/negative residuals in the far/near-side part of the disk, possibly due to an elevated emission surface at Band 9 (cite: Andrews_2021), where the emission of small grains is traced.

The results from the SED fit in Figure [5](#fig:Posterior) for LkCa15 shows three local maxima for the dust surface density, aligning precisely with the radial positions of the three prominent rings observed in the dust continuum emission. The maximum grain size only has a clear peak around the main ring at $0.433^{\prime\prime}$ (68.1 au) at this resolution. These characteristics are indicative of dust trapping in the main ring, impeding the inward flow of dust grains and forming a large cavity.

No clear planetary signatures have been directly detected within the LkCa15 cavity, although planet candidates have been suggested (cite: Kraus_2012). Comparing SPHERE/ALMA observations and the size of the observed gaps, (cite: Lodato_2019) and (cite: Asensio-Torres_2021) estimated that the upper limit of the mass of a planet companion within the cavity is $\lesssim 1$ Jupiter mass. On other side, the Lagrangian points identified by (cite: Long_2022) suggest the possible existence of a Neptune-mass planet positioned at a projected distance of 0.27$^{\prime \prime}$ (42.4 au).

Finally, evidence of a gas cavity has been found in the molecular emission of $^{12}$CO (J=2-1), $^{13}$CO (J=2-1), and C$^{18}$O (J=2-1) (cite: Wolfer_2023), suggesting that the origin of the cavity is a companion.

**RXJ1615:** Millimeter dust continuum observations of the disk around RXJ1615 have been previously reported by (cite: vanderMarel_2015; Wolfer_2023). The visibility modeling of the disk is shown in Figures [2](#fig:Visibilities)-[3](#fig:Vis_RadProfile). At Band 9, the visibility modeling is sensitive to a ring at $0.82^{\prime \prime}$ (127.6 au), while a discernible dust cavity is absent, likely due to the limited angular resolution. The outer dust ring had previously been identified by (cite: Andrews_2011) and (cite: vanderMarel_2015).

At Band 7, the radial profile shows a complex structure. Notably, it exhibits emission from various sources: a distinct compact inner disk, an asymmetric ring with a prominent peak at $0.158^{\prime \prime}$ (24.6 au), along with additional local peaks at approximately $0.251^{\prime \prime}$ (39.0 au) and $0.368^{\prime \prime}$ (57.3 au). Moreover, two further asymmetric peaks emerge at around $0.685^{\prime \prime}$ (106.6 au) and $0.839^{\prime \prime}$ (130.5 au), distinguishable in both the visibility fit and the image plane. Overall, the observations reveal the presence of up to 5 discernible rings and an inner disk. In Band Q, the FRANKENSTEIN visibility fit fails to identify disk substructures, unlike the parametric fit, which successfully does. This is the only disk where the position of the outer ring is not fixed, but it is a free parameter (Table [2](#tab:parametric_fit)). The best-fit radial position for the outer ring is $0.73^{+0.05}_{-0.08}$, falling between the locations of the two outer rings observed in Band 7.

The dust surface density and maximum grain size (Figure [5](#fig:Posterior)) have clear local maxima at the outer ring, aligning with dust trap signatures. However, there is no clear evidence of a pressure trap in the inner ring (although it is suggested), due to the low angular resolution, which is not able to resolve the inner ring after convolution (beam size of $0.192^{\prime \prime}$ and a ring at $0.158^{\prime \prime}$, see Figure [4](#fig:Radial_Profiles)).

The findings in the outer ring align with dust trap signatures. On the other hand, a gas density drop has been detected within the disk cavity, as reported by (cite: vanderMarel_2015), suggesting that the origin of the cavity is a companion. The mass of the companion candidate has been estimated as 4.5 Jupiter masses using SPHERE observations (cite: Asensio-Torres_2021).

## Disks with possible evidence of enhanced grain growth and a pressure trap as the origin of the cavity

In some of our transition disk sample, the inferred maximum grain size radial profile ($a_{\rm max}(r)$) monotonically decreases with radius, rather than showing a distinct drop within the cavity. Additionally, the distribution of $a_{\rm max}(r)$ appears relatively flat around the ring region, possibly indicating the presence of a dust trap. On the other hand, the dust surface density radial profile shows a drop of mass within the cavity. The millimeter emission cavity in these cases is reproduced by a combination of very low densities and large dust grains with low opacity. As mentioned in Section [1](#sec:intro), these characteristics are expected for cavities created by grain growth and a pressure bump. Grain growth alone is insufficient to reproduce the low brightness within the cavity, and a pressure bump (created by a companion or a dead zone) is crucial for efficiently reducing the mass within the cavity (cite: Birnstiel_2012b).

The absence of a gas gap within some of these disks further would suggest that the origin of the large cavity is not the same as in the rest of the disks. However, as mentioned at the beginning of this section, radial smearing of optically thick emission onto the cavity regions could affect the inferred dust properties. In particular, radial smearing could mimic large dust grain sizes within the cavity, as discussed in Appendix [10](#app:smearing). In the following, we discuss the results obtained from disks where a possible origin of the dust cavity may be attributed to low dust surface density triggered by a pressure bump in the ring, coupled with enhanced grain growth within the cavity, and where deep gas cavities have not been observed.

**CQTau:** The disk morphology of the dust continuum emission around CQTau has been previously reported at high angular resolution by (cite: Pinilla_2018) and (cite: Ubeira_2019). From the visibility modeling in this work (Figure [3](#fig:Vis_RadProfile)), we confirm the ring shape structure at Band 7, 6, and Ka, with a peak at $0.3^{\prime \prime}$ (44.8 au). The ring structure is also inferred from the image plane for Bands 6 and Ka. However, for Band 7, the angular resolution in the image plane smears the ring emission within the cavity, making it discernible only through the visibility fit.

According to (cite: Ubeira_2019), the disk emission displays azimuthal asymmetries in both the continuum and CO isotopologue lines. These non-axi-symmetric structures are shown in Figure [9](#fig:residuals). At Band 6, the disk emission appears brighter in the East and South-West regions compared to the average azimuthal values. A noticeable azimuthal asymmetry is also observed in the South-West of the disk at Band Ka (Figure [9](#fig:residuals)). However, this particular asymmetry has an SNR $< 5$.

The dust properties radial profiles for CQ Tau shows a dust surface density with a peak at the ring position. The maximum grain size monotonically decreases with radius, suggesting no strong evidence of a dust trap (at this angular resolution). However, a gas cavity has been inferred from the CO isotopologue emission in (cite: Ubeira_2019). Their work shows that the gas cavity is consistent with a planet of 6-9 Jupiter masses located 20 au from the central star. Given the gas and dust observations, it is not clear what mechanism is able to explain the cavity observed in dust continuum emission for CQ Tau.

**SR24S:** High angular resolution of the disk around SR24S at millimeter wavelengths have been previously reported by (cite: Pinilla_2017), (cite: Cieza_2021) and (cite: Francis_2020). The visibility modeling for SR24S (Figures [2](#fig:Visibilities)-[3](#fig:Vis_RadProfile)) shows an asymmetric ring structure at all wavelengths, similar to two adjacent ring structures, with peaks at $\sim 0.254^{\prime \prime}$ (29.0 au), $0.441^{\prime \prime}$ (50.3 au). The asymmetric ring has been already reported in previous works (cite: Cieza_2021). The FRANKENSTEIN and parametric fit at Band Ka are able to resolve the two rings, at the same radial location observed in the ALMA data.

The dust properties constraints for SR24S shows a dust surface density increasing towards the two rings, however the maximum grain size decreases with radius, and it only has a flat distribution around the ring at $0.254^{\prime \prime}$ (29.0 au). Large dust grain sizes are inferred within the cavity, suggesting that enhanced grain growth and a pressure bump are responsible of the deficit of millimeter emission in this region.

SR24S is the only disk among the transition disks studied by (cite: vanderMarel_2015) where a drop of at least 1 or 2 orders of magnitude in the gas surface density within the disk cavity is not inferred. (cite: Pinilla_2020) confirmed that the optically thin molecular emissions of $^{13}$CO and C$^{18}$O peak at the center of the disk cavity, indicating no gas deficit within the inner cavity of the disk, unlike many transition disks. As pointed out by (cite: Pinilla_2020), a large cavity created by photoevaporation is unlikely due to the high accretion rate, the large dust cavity, and the gas emission within this region.

**DMTau:** Millimeter dust continuum observations of the disk around DMTau at high resolution have been previously studied by many authors at several wavelengths, including (cite: Andrews_2011), (cite: Semenov_2018), (cite: Hashimoto_2021), and (cite: Liu_2024).

The observations presented by (cite: Hashimoto_2021) at high angular resolution reveal an inner ring ($<0.1^{\prime \prime}$, 14.4 au), a main ring with a peak at $\sim 0.16^{\prime \prime}$ (23.0 au), and two extended faint ring structures, as shown in the radial profile from the visibility fit at Band 6 in Figure [3](#fig:Vis_RadProfile). The main ring at this wavelength only present weak azimuthal asymmetries, likely due optical depth effects. These asymmetries are better observed at optically thinner wavelengths using JVLA observations at Band Q (cite: Liu_2024), where a visibility analysis shows that the Band Q intensity is azimuthally asymmetric on the spatial scale of $\sim$ 20 au or less. The spatial resolution in this work ($\sim 18$ au) is only marginally resolve those spatial scales.

The primary ring within the disk is consistently identified across all wavelengths in the visibility fit (ranging from Band 9 to Band Q). Faint outer structures are evident across all wavelengths, but their radial positions do not align with those observed at Band 6. These faint structures disappear when the radial profiles are convolved at the same angular resolution (Figure [4](#fig:Radial_Profiles)).

The results from the SED fit for DMTau in this work (Figure [5](#fig:Posterior)) shows a dust surface density increasing towards the position of the main ring. The maximum grain size decreases with radius, and it has a flat distribution close to the disk ring. Evidence of efficient grain growth in the inner most region of DMTau has been also found by (cite: Hashimoto_2021). They found that the SED can be reproduced using a population of large dust grains (millimeter grains) that are less depleted than small dust grains (submicron size), consistent with efficient grain growth in the inner region of the disk, consistent with our grain size estimations within the cavity. However, the multi-wavelength analysis in (cite: Liu_2024) recently showed that the integrated SED from 8 to 700 GHz can be explained by two grain size components: one population of $a_{\rm max} \gtrsim 300$ microns sizes for the emission of small solid angles (as the knot observed in Band Q), and a second population of $a_{\rm max} <50$ microns for larger solid angles (similar to the spatial scale emission from ALMA wavelengths). These analysis and their apparent disagreement show why higher angular resolution observations where the emission from compact and extended sources can be resolved at several wavelengths.

No evidence of a gas gap has been found within the dust cavity (cite: Kudo_2018; Hashimoto_2021; vanderMarel_2021), although the $^{12}$CO observations used in these works may not be able to resolve the gap, and the emission could be optically thick. (cite: Wolfer_2023) studied the spatial distribution of optically thinner molecular transitions in DMTau, including $^{13}$CO and C$^{18}$O, but no evidence of a deep gas cavity or spirals/arcs structure was found, although the angular resolution could also be insufficient. Therefore, the presence of a possible gas gap inside the dust cavity is still unknown.

As pointed out by (cite: Kudo_2018), the origin of the dust cavity remains unclear. The high accretion rate disfavors photoevaporation, while the absence of a gas gap (cite: Wolfer_2023) disfavors a companion. In any case, a pressure bump at the ring location is needed to explain the deficit of dust mass within the cavity.

# Does the origin of a large cavity depend on the disk mass?

The constraints on dust properties shown in Figure [5](#fig:Posterior) offer insights into the origin of the observed large cavities. The results suggest that in UXTau A, LkCa15, and RXJ1615, the origin of the large cavities are dust traps created by a companion (a planet or a close binary). Conversely, in CQTau, SR24S and DMTau, a possible origin of the large cavities is a combination of monotonically increasing maximum grain size towards the disk center (which results in low emission at millimeter wavelengths), and a deficit of dust mass created by a pressure bump in the ring (cite: Birnstiel_2012b). In the latter scenario, the pressure bump can be generated, for example, by a dead zone or a companion.

It is important to note that resolution effects may play a significant role in inferring the increasing maximum grain size towards the disk center, possibly due to the presence of inner disks, as shown in the brightness radial profile of SR24S at Band 3 or DMTau at Band 6 (Figure [3](#fig:Vis_RadProfile)). Although the inner disks vanish when convolved to a lower angular resolution (Figure [4](#fig:Radial_Profiles)), their emission could spread to outer radii within the cavity (see discussion in Appendix [10](#app:smearing)).

Table [\[Tab:Origin\]](#Tab:Origin) summarizes various physical mechanisms consistent with the observational signatures presented in this work. Additionally, it includes constraints on gas cavities, and the detection of spirals/arms in CO maps, which have been interpreted as potential evidence of embedded companions (cite: Wolfer_2023). It is also important to remark that no evidence of a inner brown dwarf companions with a mass $>20$M$_{\mathrm{Jup}}$ has been found in UXTau A, LkCa15, RXJ1615, and SR24S, while it is only tentative for DMTau (cite: Kraus_2011).

The reported dust masses in Table [\[Tab:Origin\]](#Tab:Origin) are estimated by integrating the dust surface density profiles in Figure [5](#fig:Posterior). The final columns present similar observational signatures observed in two other transition disks (GMAur, Sz91), where multi-wavelength modeling has also been used to infer dust properties radial profiles.

+:------------------------------:+:------:+:-------:+:------:+:-------:+:------:+:-------:+:------:+:------:+
|                                | This work                                              | Literature      |
+--------------------------------+--------+---------+--------+---------+--------+---------+--------+--------+
|                                | CQTau  | UXTau A | LkCa15 | RXJ1615 | SR24S  | DMTau   | GMAur  | Sz91   |
+--------------------------------+--------+---------+--------+---------+--------+---------+--------+--------+
| $M_* [M_{\odot}]$              | 1.63   | 1.4     | 1.32   | 1.1     | 0.87   | 0.39    | 1.1    | 0.54   |
+--------------------------------+--------+---------+--------+---------+--------+---------+--------+--------+
| $M_{\rm dust} [M_{\oplus}]$    | 804    | 663     | 247    | 232     | 185    | 305     | 245    | 31.3   |
+--------------------------------+--------+---------+--------+---------+--------+---------+--------+--------+
| Dust trap - companion          |        |         |        |         |        |         |        |        |
+--------------------------------+--------+---------+--------+---------+--------+---------+--------+--------+
| Dust trap - Dead zone          |        |         |        |         |        |         |        |        |
+--------------------------------+--------+---------+--------+---------+--------+---------+--------+--------+
| Grain growth                   | $^{*}$ |         |        |         | $^{*}$ | $^{*}$  | $^{*}$ | $^{*}$ |
+--------------------------------+--------+---------+--------+---------+--------+---------+--------+--------+
| Photo-evaporation              |        |         |        |         |        |         |        |        |
+--------------------------------+--------+---------+--------+---------+--------+---------+--------+--------+
| Gas cavity$^{(1)}$             |        |         |        |         |        | $^{**}$ |        |        |
+--------------------------------+--------+---------+--------+---------+--------+---------+--------+--------+
| Kinematic spirals/arms$^{(2)}$ |        |         |        |         | \-     |         |        |        |
+--------------------------------+--------+---------+--------+---------+--------+---------+--------+--------+

\
: Compatible, : No compatible, : Tentative. $^{(*)}$Possibly affected by radial smearing of low angular resolution observations. $^{(1)}$Gas constraints from literature (references in Sections [5.2](#sec:Planet)-[5.3](#sec:graingrowth)), $^{(2)}$From kinematic signatures in (cite: Wolfer_2023). $^{(**)}$Low angular resolution observations. Stellar mass references: GMAur (cite: Macias_2018), Sz91 (cite: Francis_2020), and those in Table [1](#tab:Stellar)

The dust properties in the disks around GMAur (cite: Sierra_2021) and Sz91 (cite: Mauco_2021) show dust surface density maxima at the position of the rings, and a maximum grain size decreasing with radius, consistent with a large cavity created by a pressure bump and enhanced grain growth. However, radial smearing effects within the cavity cannot be ruled out given the spatial resolution of the observations. However, unlike SR24S and DMTau, gas cavities have been observed in GMAur and Sz91, and tentative kinematic spirals/arms in Sz91.

In our sample, the disk dust mass generally tends to increase with the stellar mass, as already reported by (cite: Pinilla_2020) in a large sample of disks. Note that the origin of the large cavities with the lowest stellar/dust mass in our sample is tentatively attributed a pressure bump and enhanced grain growth. Conversely, for higher stellar/dust masses, except possibly CQTau, the large cavities are consistent with dust traps formed by a companion. It is important to remark that the long wavelength data in this work (from DisksEVLA project, ID: AC982) are biased towards massive disks. Thus, a larger sample of transition disks covering lower disk masses is needed to confirm or rule out our suggestive findings, in addition to higher angular resolution, which can help rule out radial smearing effects.

It is known that disk mass can play a role in shaping the formation, evolution, and characteristics of protoplanetary disks (cite: Ribas_2015; Drkazkowska_2023). In transition disks, the origin of the cavities could be mass dependent, as suggested by the results in this work. Further observational modeling, high angular resolution data, and simulations are necessary to delve deeper into exploring this possibility.

# Conclusions

We analyzed millimeter dust continuum observations of transition disks surrounding CQTau, UXTau A, LkCa15, RXJ1615, SR24S, and DMTau. A total of 26 observations were used, covering wavelengths from ALMA Band 9 (435 $\mu$m) to VLA Band Ka (8.8 mm). These observations were used to fit the radial brightness profiles at sub-beam resolution, enabling a study of the radial distribution of solids.

The constraints on the dust surface density, dust temperature, and maximum grain size radial profiles inferred from modeling the SED offer valuable insights regarding the physical origin of the observed large cavities in each disk. Our main conclusions about the disk morphology and origin of the large cavities in each disk are summarized as follows.

1.  The radial brightness profiles observed in the disks around CQTau and UXTau A reveal a Gaussian-like ring at all wavelengths, and no emission from an inner disk. Additionally, the point source at the longest VLA wavelengths is consistent with a notably low flux (upper limit of $\lesssim 7\ \mu$Jy) in both disks.

2.  Across multiple wavelengths, the brightness radial profiles observed in the disks around RXJ1615, LkCa15, SR24S, and DMTau display a multi-ring structure. Notably, RXJ1615 exhibits the highest number of discernible sub-structures, particularly evident at Band 7 where the high angular resolution enables the identification of up to 5 local maxima and an inner disk. In LkCa15 and SR24S, the number of rings or local maxima is 4 and 2, respectively.

    In the case of DMTau, the primary ring observed at the Band 6 wavelength displays asymmetry. Additionally, this profile shows two faint rings in the outer disk, which are poorly constrained across other wavelengths. The disks associated to RXJ1615, LkCa15, SR24S, and DMTau have an inner disk, which can be observed at the highest angular resolution observations.

3.  The radial profiles of the dust surface density and maximum grain size in the disks around UXTau A, LkCa15, and RXJ1615 have peak values at the position of the main ring of each disk. These properties align with dust trap models, which may be formed by either a companion or a dead zone. Gas observations of these disks have unveiled gas cavities and kinematic spirals/arms, indicating that the formation of the dust trap and the large cavities in these disks could be attributed to a companion carving a deep gap.

4.  In CQTau, SR24S and DMTau, the dust surface density peaks at the ring positions, whereas the maximum grain size decreases with radius, displaying a plateau around the rings. Although the inferred large grain sizes within the cavity can be affected by radial smearing, these large grain sizes are able to reproduce the multi-wavelength observations. These findings suggest the possibility that large grains (with low opacity at millimeter wavelengths) are present in the cavity (unlike the other disks in this work), while the low dust surface densities constrained in the cavities might be triggered by a pressure bump in the ring (either by a companion or dead zone). No gas cavities and kinematic spirals/arms in molecular gas observations have been observed in SR24S and DMTau, suggesting that the origin of their cavities may differ from the rest of the disks in this work. However, the low angular resolution of existing dust continuum and molecular gas observations are not sufficient to favor a particular mechanism.

5.  The dust properties constraints in the transition disks in our sample may exhibit different characteristics, suggesting potentially different origins for the large cavities. In most of the massive disks (UXTau A, LkCa15, RXJ1615), the cavity formation can be attributed to a dust trap created by a companion. In contrast, for the less massive disks (SR24S, DMTau), the cavities may result from a deficit of dust mass created by a pressure bump and enhanced grain growth, leading to a reduction in the emergent intensity within the cavity. However, similar constraints are found in the massive disk around CQ Tau. Given the low angular resolution and possible radial smearing, the possibility of small grain sizes within the cavity (as those inferred from polarized observations) consistent with pressure traps, cannot be ruled out for CQTau, SR24S and DMTau.

# Acknowledgments

We are very thankful for the thoughtful suggestions of the anonymous referee that helped to improve our manuscript significantly. A.S. acknowledges support from FONDECYT de Postdoctorado 2022 #3220495. LP acknowledges support from ANID FONDECYT Regular #1221442. A.S, L.P., and M.B. acknowledge support from ANID BASAL project FB210003 and Programa de Cooperación Cientifica ECOS-ANID ECOS200049. We thank Nicolas Kurtovic for his help on the calculation of disk offsets and geometry constraints. We thank Elena Viscardi and Enrique Macias for their discussion about the effects of beam smearing and its impact on inferring dust properties. This project has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (PROTOPLANETS, grant agreement No. 101002188). T.H. acknowledges support from the European Research Council under the Horizon 2020 Framework Program via the ERC Advanced Grant Origins 83 24 28.

This paper makes use of the following ALMA data: ADS/JAO.ALMA #2011.0.00320.S, ADS/JAO.ALMA #2011.0.00742.S, ADS/JAO.ALMA #2012.1.00870.S, ADS/JAO.ALMA #2013.1.00091.S, ADS/JAO.ALMA #2013.1.00157.S, ADS/JAO.ALMA #2013.1.00498.S, ADS/JAO.ALMA #2015.1.00296.S, ADS/JAO.ALMA #2015.1.00888.S, ADS/JAO.ALMA #2015.1.01137.S, ADS/JAO.ALMA #2016.1.00565.S, ADS/JAO.ALMA #2016.1.01042.S, ADS/JAO.ALMA #2018.1.00350.S, ADS/JAO.ALMA #2018.1.01255.S, ADS/JAO.ALMA #2018.1.01755.S

ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. In addition, publications from NA authors must include the standard NRAO acknowledgement: The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

We acknowledge the use of data from the Very Large Array (VLA) AC982, 12B-196, 13B-381, operated by the National Radio Astronomy Observatory (NRAO). The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc

In memory of Rosita Morales, who passed away during the course of this work.

# Software

Astropy (cite: astropy:2013; astropy:2018), CASA (cite: McMullin_2007), Emcee (cite: Foreman_2013), Frankenstein (cite: Jennings_2020), Matplotlib (cite: Matplotlib_2007), Numpy (cite: Numpy_2020) .

# Angular resolution from visibility modeling

In Section [4](#sec:multiwave), we fit the spectral energy distribution (SED) of the disks as a function of radius. This requires comparing the multi-wavelength radial profiles from the visibility modeling at the same angular resolution. The uv-coverage of the observations in this work varies significantly. For instance, most of the Band 9 data were collected during ALMA Cycle 0 (in 2012), while some Band 3 or 6 datasets were observed after 2020, where the antenna configuration is more extended. Therefore, we anticipate differences in the intrinsic angular resolution of the visibility fits. As fully discussed in Section 3 in (cite: Jennings_2020), the visibility fits with FRANKENSTEIN can attain sub-beam resolution. To address the angular resolution problem, we test two different methodologies: Delta Ring, and Gaussian disk, which are described below.

## Delta Ring

We generate synthetic visibility observations of an infinitely narrow ring (a delta function) centered at a radius of $r_0 = R_{\rm max}/2$ (where $R_{\rm max}$ denotes the maximum disk radius from the visibility fit[^3]). The center $r_0$ was chosen to avoid boundary effects. However, negligible differences are found when using a different $r_0$. The synthetic visibilities of the delta ring $\delta (r-r_0)$ are computed by its Hankel transform $\mathcal{H}$ as $$\begin{equation}
    \label{eq:Hankel_Delta}
    \mathcal{H} \left[ \frac{A_0}{2\pi r_0} \delta(r-r_0)\right] = A_0 J_0(2\pi r_0 q),
\end{equation}$$ where $A_0$ is a constant that represents the total flux, and $q$ are the de-projected baselines.

These visibilities (right hand of Equation [\[eq:Hankel_Delta\]](#eq:Hankel_Delta)) are sampled at the same uv-coverage of each data set, and then we use FRANKENSTEIN to fit them (using the same methodology and hyper-parameters described in Table [\[tab:Visibility\]](#tab:Visibility)) and try to retrieve the delta function’s input brightness distribution. FRANKENSTEIN reconstructs a Gaussian function instead of a delta function, with a full width half maximum (FWHM) that depends on the uv-coverage. This FWHM represents the minimum spatial scale recoverable by the visibility fit, i.e., the intrinsic angular resolution of the visibility fit. A Gaussian function is fitted to the reconstructed brightness profile, and the FWHM is reported in the last column in Table [\[tab:Visibility\]](#tab:Visibility). We remark that this methodology is equivalent to the definition of the Point Spread Function (PSF), defined as the response of an imaging system (e.g. an interferometer) to a point source. Deconvolution and imaging software (e.g. CASA) fits the 2D intensity distribution of the PSF to quantify the minimum recoverable spatial scale for a given uv-coverage, in an analogous way to our constrain of the spatial scale that our method recovers when the source is an infinitely narrow ring.

## Gaussian Disk

As a second method to infer the intrinsic angular resolution, we compute the visibilities of a full gaussian disk of a certain FWHM ($\Theta$) at the same uv-coverage of each observation. The visibilities are computed using the Hankel transform of a gaussian disk as $$\begin{equation}
    \label{eq:Hankel_Gauss}
    \mathcal{H} \left[ \frac{1}{\Theta} \sqrt{\frac{4 \ln 2}{\pi}} \exp \left( -\frac{4 \ln2 r^2}{\Theta^2} \right) \right] = \exp \left(- \frac{(\pi \Theta q)^2}{4\ln2} \right).
\end{equation}$$ Then, these visibilities are fitted with FRANKENSTEIN, where a Gaussian function similar to that of the input model is obtained. The comparison between the input FWHM and that obtained with FRANKENSTEIN is shown in the left panel of Figure [7](#fig:Thermal_Noise) for the uv-coverage of LkCa15 at Band 6 and 9. Note that the FWHM obtained with FRANKENSTEIN differs from the input value when the latter tends to zero. The horizontal dashed lines are the angular resolutions computed from the delta rings in the previous section. These values represent the minimum spatial scale that a FRANKENSTEIN fit with a certain uv-coverage is able to resolve.

![](Thermal_Noise.pdf)

## The effects of thermal noise when resolving two delta rings

The input models for a delta ring and Gaussian disk above were computed without including thermal noise to the visibilities. In this section we demonstrate that our visibility fit resolves the emission of two delta rings, with or without the inclusion of thermal noise. The first input model consists of two delta rings separated by 50 mas around $R_{\rm max}/2 = 1.1^{\prime \prime}$. The visibilities of each delta ring are sampled at the uv-coverage of LkCa15 at Band 6 using the equation [\[eq:Hankel_Delta\]](#eq:Hankel_Delta). The second model is the same but including thermal noise to the visibilities. The thermal noise is simulated by randomly choosing a visibility measurement within the visibilities error bar at each baseline. Then we use FRANKENSTEIN in both models to reconstruct the brightness radial profile. The visibility fit to the mock data are shown in the middle panel of Figure [7](#fig:Thermal_Noise), and the reconstructed radial profiles are shown in the right panel of the same Figure. In both cases, the visibility fit is able to resolve both rings, with a FWHM of 21.5 mas, as already computed in Sections [8.1](#subsec:delta_ring)-[8.2](#subsec:gaussian_disk).

# More on visibility modeling

## Best Models and Residuals

The visibility models presented in Figure [2](#fig:Visibilities) are used to generate synthetic observations of the disks. Each model is sampled with the same uv-coverage as the observations and then imaged with identical observational parameters as described in Table [\[tab:Observations\]](#tab:Observations). Figure [8](#fig:models) shows the CLEAN images of the disk models for all the observations.

![](Gallery_Models.pdf)

On the other hand, the visibility residuals (Data - Model) are computed and also used to generate synthetic observations. After sampling the visibility residuals with the same uv-coverage as the observations, they are imaged and shown in Figure [9](#fig:residuals). Each map is normalized to the rms of each observation. The red/blue areas indicate regions with excess/deficit emission relative to the azimuthally averaged intensity of each observation.

![image](Gallery_Residuals.pdf) ![image](Gallery_Residuals_Intensity.pdf)

## Parametric Models at VLA wavelengths

The parametric models for VLA data are given by a sum of Gaussian functions and a delta function $\delta(r)$ (mimic the compact emission from free-free) at the disk center: $$\begin{equation}
    I(r) = \sum_i A_i \exp \left[ -\frac{(r-r_i)^2}{2 \sigma_i^2} \right] + f_0 \delta(r).
\end{equation}$$ The number of Gaussian functions for each disk is chosen based on the radial profile at ALMA wavelengths. The radial positions ($r_i$) of the Gaussian functions are fixed in all cases, determined by the ring locations observed at longer ALMA wavelengths for each respective disk. We also conducted tests allowing $r_i$ to be a free parameter, and the resulting posterior probability distributions aligned with those when the radial positions were fixed. Therefore, to mitigate the ambiguity between the remaining free parameters, we opted to keep the radial positions of the Gaussian functions fixed.

The free parameters ($A_i, \sigma_i, f_0$) are determined via a Markov Chain Monte Carlo (MCMC) method (cite: Foreman_2013), aiming to minimize the logarithm of the likelihood function given by Equation [\[eq:posterior_vis\]](#eq:posterior_vis), and using 64 walkers and 10000 steps. Table [2](#tab:parametric_fit) shows the parametric model chosen for each disk and the best fit for each parameter. Low and upper error bars correspond to percentiles 16 and 84, respectively.

The free-free flux (last column) for LkCa15, RXJ1615, and SR24S is 17.8, 44.7, and 11.0 $\mu$Jy respectively. These values are high compared with the rest of the disks in this work. (cite: Zapata_2017) showed that the SED of these disks can be described as a two-component power law: one of then associated to thermal dust emission, and the other to free-free emission, consistent with our estimations. Meanwhile, they claim that for UXTau A, a single power law (from optically thin dust emission) is enough to reproduce the SED. Our free-free flux estimation for UXTau A is only 0.05 $\mu$Jy, which is below the sensitivity (14.9 $\mu$Jy), and thus, it is not detected in this work. For DM Tau, the best fit is consistent with a low free-free flux of only $0.02 \mu$ Jy, which is a non-detection given the sensitivity of $9 \mu$Jy. No free-free emission was detected in (cite: Zapata_2017) in DM Tau either. However, it is known that the free-free from ionized gas is variable (cite: Terada_2023). Finally, the free-free emission of CQ Tau is also low and below the sensitivity (7 $\mu$Jy). The non-detection of free-free emission is consistent with the lack of detection at 3.6 cm and 6.0 cm, suggesting that the flux at 7 mm is dominated by dust thermal emission (cite: Testi_2001).

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | Parametric model | $\log_{10}(A_0)$ | fixed $r_0$ | $\log_{10} (\sigma_0)$ | $\log_{10}(A_1)$ | fixed $r_1$ | $\log_{10} (\sigma_1)$ | $\log_{10}(f_0)$ |
|  |  | (Jy/sr) | (arcsec) | (arcsec) | (Jy/sr) | (arcsec) | (arcsec) | (Jy) |
| CQTau | 1 Gaussian + point source | $7.83^{+0.02}_{-0.02}$ | 0.300 | $-0.92^{+0.02}_{-0.02}$ | \- | \- | \- | $-6.29^{+1.05}_{-1.14}$ |
| UXTau A | 1 Gaussian + point source | $8.43^{+0.06}_{-0.05}$ | $0.236$ | $-1.26^{+0.06}_{-0.07}$ | \- | \- | \- | $-7.31^{+1.85}_{-1.83}$ |
| LkCa15 | 2 Gaussians + point source | $7.56^{+0.06}_{-0.06}$ | $0.433$ | $-1.21^{+0.07}_{-0.07}$ | $7.08^{+0.05}_{-0.06}$ | $0.635$ | $-0.81^{+0.06}_{-0.06}$ | $-4.75^{+0.10}_{-0.12}$ |
| RXJ1615 | 2 Gaussians + point source | $7.78^{+0.08}_{-0.08}$ | 0.158 | $-0.85^{+0.07}_{-0.09}$ | $7.52^{+1.09}_{-0.62}$ | $0.73^{+0.05}_{-0.08}$ | $-1.72^{+0.90}_{-1.18}$ | $-4.35^{+0.17}_{-0.29}$ |
| SR24S | 2 Gaussian + point source | $7.74^{+0.11}_{-0.06}$ | $0.254$ | $-1.00^{+0.13}_{-0.21}$ | $7.42^{+1.25}_{-1.43}$ | $0.441$ | $-1.83^{+0.73}_{-0.77}$ | $-4.96^{+0.85}_{-0.97}$ |
| DMTau | 2 Gaussian + point source | $8.26^{+0.12}_{-0.08}$ | $0.180$ | $-1.36^{+0.08}_{-0.13}$ | $6.57^{+0.53}_{-0.25}$ | $0.860$ | $-0.83^{+
       0.38}_{-0.66}$ | $-7.57^{+1.92}_{-1.68}$ |

: Best fits of the parametric model for VLA observations.

# Radial smearing effects

The inferred dust properties depend on the lowest angular resolution of the multi-wavelength data. Higher contrasts between rings and gaps are expected in future high angular resolution observations. Radial smearing effects could potentially influence the inferred dust property profiles. For instance, optically thick emission at the rings could smear into the cavity region. This could mimic faint dust continuum emission with low spectral indices within the cavity, which might be attributed to large grain sizes (similar to those in CQTau, SR24 and DMTau).

It is important to note that our methodology for studying the dust properties radial profiles cannot directly infer the deconvolved or convolved dust properties radial profiles. Instead, it provides only an approximation of those values, depending on the angular resolution. For example, in the optically thin regime and Rayleigh Jeans approximation, the emergent intensity is the product of three free parameters: $I_{\nu} \propto T_{\rm d} \Sigma_{\rm d} \kappa_{\nu}$. Since we observe the convolved intensities $\mathcal{C} (I_{\nu})$, we can only infer the convolution of the product of the three free parameters, rather than the product of individual convolved profiles $\mathcal{C} (T_{\rm d} \Sigma_{\rm d} \kappa_{\nu})  \neq \mathcal{C} (T_{\rm d}) \times \mathcal{C} (\Sigma_{\rm d}) \times \mathcal{C} (\kappa_{\nu})$. We only have good approximations to the convolved dust properties radial profiles when the angular resolution is sufficiently high (Viscardi et al. in prep).

We study the effects of radial smearing by creating a disk model with properties similar to those of DMTau, where large grain sizes are inferred within the disk cavity. The temperature radial profile model is computed from a passively irradiated disk and the DMTau stellar parameters (Table [1](#tab:Stellar)). The maximum grain size model is given by $0.1(r/0.2^{\prime \prime})^{-0.5} + \exp[ - 0.5 ((r-0.2^{\prime \prime})/0.015^{\prime \prime})^2]$ cm, and the dust surface density is given by $0.01 + \exp(-0.5  (r-0.2^ {\prime \prime})^2/\sigma^2)$ g cm$^{-2}$, with $\sigma = 0.02^{\prime \prime}$, for $r> 0.2^{\prime \prime}$ and $\sigma = 0.005^{\prime \prime}$ for $r\leq 0.2^{\prime \prime}$ to mimic an asymmetric ring. These radial profiles, chosen to represent dust trap signatures, are shown as a solid curve in the left panels of Figure [10](#fig:smearing). The dashed lines in the same panels are the convolved radial profiles, using the resolution of the DMTau observations (120 mas). The middle panels show the convolved intensity profiles (top) and optical depths (bottom) corresponding to the same multi-wavelength observation as DMTau. The intensities and optical depths were originally computed using the dust properties models, and then these profiles were convolved to the same angular resolution.

The right panels show the best fit for dust temperature (top), maximum grain size (middle), and dust surface density (bottom). The blue dashed lines are the convolved radial profiles shown in the left panels. Any discrepancy between the radial profile from the posterior probability and the convolved radial profiles is due to the inability to independently infer the convolved dust properties radial profiles from observations (radial smearing effects), as discussed above. Note that the temperature and dust surface density radial profiles are well reproduced. However, the maximum grain size around the peak is radially smeared (much beyond the convolved radial profile), mimicking large grain sizes within the cavity, similar to the dust properties inferred in SR24S and DMTau (Figure [5](#fig:Posterior)). Thus, although large grain sizes within the cavity can reproduce the intensity profiles for CQTau, SR24S and DMTau, we cannot rule out the possibility of small grain sizes in this region, which are hidden by radial smearing effects.

![](Input_Models.pdf)

natexlab

(ref: Alexander_2006) Alexander, R. D., Clarke, C. J., & Pringle, J. E. 2006, MNRAS, 369, 229, doi: [`10.1111/j.1365-2966.2006.10294.x`](http://doi.org/10.1111/j.1365-2966.2006.10294.x)

(ref: Andrews_2011) Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42, doi: [`10.1088/0004-637X/732/1/42`](http://doi.org/10.1088/0004-637X/732/1/42)

(ref: Andrews_2009) Andrews, S. M., Wilner, D. J., Hughes, A. M., Qi, C., & Dullemond, C. P. 2009, ApJ, 700, 1502, doi: [`10.1088/0004-637X/700/2/1502`](http://doi.org/10.1088/0004-637X/700/2/1502)

(ref: Andrews_2014) Andrews, S. M., Chandler, C. J., Isella, A., et al. 2014, ApJ, 787, 148, doi: [`10.1088/0004-637X/787/2/148`](http://doi.org/10.1088/0004-637X/787/2/148)

(ref: Andrews_2021) Andrews, S. M., Elder, W., Zhang, S., et al. 2021, ApJ, 916, 51, doi: [`10.3847/1538-4357/ac00b9`](http://doi.org/10.3847/1538-4357/ac00b9)

(ref: Artymowicz_1996) Artymowicz, P., & Lubow, S. H. 1996, ApJL, 467, L77, doi: [`10.1086/310200`](http://doi.org/10.1086/310200)

(ref: Asensio-Torres_2021) Asensio-Torres, R., Henning, T., Cantalloube, F., et al. 2021, A&A, 652, A101, doi: [`10.1051/0004-6361/202140325`](http://doi.org/10.1051/0004-6361/202140325)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Avenhaus_2018) Avenhaus, H., Quanz, S. P., Garufi, A., et al. 2018, ApJ, 863, 44, doi: [`10.3847/1538-4357/aab846`](http://doi.org/10.3847/1538-4357/aab846)

(ref: Balbus_1991) Balbus, S. A., & Hawley, J. F. 1991, ApJ, 376, 214, doi: [`10.1086/170270`](http://doi.org/10.1086/170270)

(ref: Benisty_2021) Benisty, M., Bae, J., Facchini, S., et al. 2021, ApJL, 916, L2, doi: [`10.3847/2041-8213/ac0f83`](http://doi.org/10.3847/2041-8213/ac0f83)

(ref: Birnstiel_2012b) Birnstiel, T., Andrews, S. M., & Ercolano, B. 2012a, A&A, 544, A79, doi: [`10.1051/0004-6361/201219262`](http://doi.org/10.1051/0004-6361/201219262)

(ref: Birnstiel_2016) Birnstiel, T., Fang, M., & Johansen, A. 2016, Space Sci. Rev., 205, 41, doi: [`10.1007/s11214-016-0256-1`](http://doi.org/10.1007/s11214-016-0256-1)

(ref: Birnstiel_2012) Birnstiel, T., Klahr, H., & Ercolano, B. 2012b, A&A, 539, A148, doi: [`10.1051/0004-6361/201118136`](http://doi.org/10.1051/0004-6361/201118136)

(ref: Birnstiel_2018) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45, doi: [`10.3847/2041-8213/aaf743`](http://doi.org/10.3847/2041-8213/aaf743)

(ref: Brown_2009) Brown, J. M., Blake, G. A., Qi, C., et al. 2009, ApJ, 704, 496, doi: [`10.1088/0004-637X/704/1/496`](http://doi.org/10.1088/0004-637X/704/1/496)

(ref: Brown_2007) Brown, J. M., Blake, G. A., Dullemond, C. P., et al. 2007, ApJL, 664, L107, doi: [`10.1086/520808`](http://doi.org/10.1086/520808)

(ref: Calvet_2002) Calvet, N., D’Alessio, P., Hartmann, L., et al. 2002, ApJ, 568, 1008, doi: [`10.1086/339061`](http://doi.org/10.1086/339061)

(ref: Carrasco-Gonzalez_2019) Carrasco-González, C., Sierra, A., Flock, M., et al. 2019, ApJ, 883, 71, doi: [`10.3847/1538-4357/ab3d33`](http://doi.org/10.3847/1538-4357/ab3d33)

(ref: Casassus_2013) Casassus, S., van der Plas, G. M., Perez, S., et al. 2013, Nature, 493, 191, doi: [`10.1038/nature11769`](http://doi.org/10.1038/nature11769)

(ref: Christiaens_2024) Christiaens, V., Samland, M., Henning, T., et al. 2024, arXiv e-prints, arXiv:2403.04855, doi: [`10.48550/arXiv.2403.04855`](http://doi.org/10.48550/arXiv.2403.04855)

(ref: Cieza_2021) Cieza, L. A., González-Ruilova, C., Hales, A. S., et al. 2021, MNRAS, 501, 2934, doi: [`10.1093/mnras/staa3787`](http://doi.org/10.1093/mnras/staa3787)

(ref: Delussu_2024) Delussu, L., Birnstiel, T., Miotello, A., et al. 2024, arXiv e-prints, arXiv:2405.14501, doi: [`10.48550/arXiv.2405.14501`](http://doi.org/10.48550/arXiv.2405.14501)

(ref: Dong_2015) Dong, R., Zhu, Z., & Whitney, B. 2015, ApJ, 809, 93, doi: [`10.1088/0004-637X/809/1/93`](http://doi.org/10.1088/0004-637X/809/1/93)

(ref: Draine_2006) Draine, B. T. 2006, ApJ, 636, 1114, doi: [`10.1086/498130`](http://doi.org/10.1086/498130)

(ref: Drkazkowska_2023) Drkażkowska, J., Bitsch, B., Lambrechts, M., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 717, doi: [`10.48550/arXiv.2203.09759`](http://doi.org/10.48550/arXiv.2203.09759)

(ref: Dubrulle_1995) Dubrulle, B., Morfill, G., & Sterzik, M. 1995, Icarus, 114, 237, doi: [`10.1006/icar.1995.1058`](http://doi.org/10.1006/icar.1995.1058)

(ref: Dullemond_2001) Dullemond, C. P., Dominik, C., & Natta, A. 2001, ApJ, 560, 957, doi: [`10.1086/323057`](http://doi.org/10.1086/323057)

(ref: Espaillat_2010) Espaillat, C., D’Alessio, P., Hernández, J., et al. 2010, ApJ, 717, 441, doi: [`10.1088/0004-637X/717/1/441`](http://doi.org/10.1088/0004-637X/717/1/441)

(ref: Facchini_2020) Facchini, S., Benisty, M., Bae, J., et al. 2020, A&A, 639, A121, doi: [`10.1051/0004-6361/202038027`](http://doi.org/10.1051/0004-6361/202038027)

(ref: Flock_2015) Flock, M., Ruge, J. P., Dzyurkevich, N., et al. 2015, A&A, 574, A68, doi: [`10.1051/0004-6361/201424693`](http://doi.org/10.1051/0004-6361/201424693)

(ref: Foreman_2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: Francis_2020) Francis, L., & van der Marel, N. 2020, ApJ, 892, 111, doi: [`10.3847/1538-4357/ab7b63`](http://doi.org/10.3847/1538-4357/ab7b63)

(ref: Gaia_2020) Gaia Collaboration. 2020, VizieR Online Data Catalog, I/350

(ref: Garate_2021) Gárate, M., Delage, T. N., Stadler, J., et al. 2021, A&A, 655, A18, doi: [`10.1051/0004-6361/202141444`](http://doi.org/10.1051/0004-6361/202141444)

(ref: Goldreich_1979) Goldreich, P., & Tremaine, S. 1979, ApJ, 233, 857, doi: [`10.1086/157448`](http://doi.org/10.1086/157448)

(ref: Numpy_2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Hartmann_2016) Hartmann, L., Herczeg, G., & Calvet, N. 2016, ARA&A, 54, 135, doi: [`10.1146/annurev-astro-081915-023347`](http://doi.org/10.1146/annurev-astro-081915-023347)

(ref: Hashimoto_2021) Hashimoto, J., Muto, T., Dong, R., et al. 2021, ApJ, 911, 5, doi: [`10.3847/1538-4357/abe59f`](http://doi.org/10.3847/1538-4357/abe59f)

(ref: Hayashi_1981) Hayashi, C. 1981, Progress of Theoretical Physics Supplement, 70, 35, doi: [`10.1143/PTPS.70.35`](http://doi.org/10.1143/PTPS.70.35)

(ref: Hoang_2018) Hoang, T., Lan, N.-Q., Vinh, N.-A., & Kim, Y.-J. 2018, ApJ, 862, 116, doi: [`10.3847/1538-4357/aaccf0`](http://doi.org/10.3847/1538-4357/aaccf0)

(ref: Huang_2018) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJL, 869, L42, doi: [`10.3847/2041-8213/aaf740`](http://doi.org/10.3847/2041-8213/aaf740)

(ref: Hull_2018) Hull, C. L. H., Yang, H., Li, Z.-Y., et al. 2018, ApJ, 860, 82, doi: [`10.3847/1538-4357/aabfeb`](http://doi.org/10.3847/1538-4357/aabfeb)

(ref: Matplotlib_2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Isella_2019b) Isella, A., Benisty, M., Teague, R., et al. 2019a, ApJL, 879, L25, doi: [`10.3847/2041-8213/ab2a12`](http://doi.org/10.3847/2041-8213/ab2a12)

(ref: Isella_2014) Isella, A., Chandler, C. J., Carpenter, J. M., Pérez, L. M., & Ricci, L. 2014, ApJ, 788, 129, doi: [`10.1088/0004-637X/788/2/129`](http://doi.org/10.1088/0004-637X/788/2/129)

(ref: Isella_2019) Isella, A., Andrews, S. M., Dullemond, C. P., et al. 2019b, in 50th Annual Lunar and Planetary Science Conference, Lunar and Planetary Science Conference, 2821

(ref: Jennings_2021) Jennings, J., Booth, R. A., Tazzari, M., Clarke, C. J., & Rosotti, G. P. 2021, arXiv e-prints, arXiv:2103.02392. [`https://arxiv.org/abs/2103.02392`](https://arxiv.org/abs/2103.02392)

(ref: Jennings_2020) Jennings, J., Booth, R. A., Tazzari, M., Rosotti, G. P., & Clarke, C. J. 2020, MNRAS, 495, 3209, doi: [`10.1093/mnras/staa1365`](http://doi.org/10.1093/mnras/staa1365)

(ref: Kataoka_2016b) Kataoka, A., Muto, T., Momose, M., Tsukagoshi, T., & Dullemond, C. P. 2016a, ApJ, 820, 54, doi: [`10.3847/0004-637X/820/1/54`](http://doi.org/10.3847/0004-637X/820/1/54)

(ref: Kataoka_2016) Kataoka, A., Tsukagoshi, T., Momose, M., et al. 2016b, ApJL, 831, L12, doi: [`10.3847/2041-8205/831/2/L12`](http://doi.org/10.3847/2041-8205/831/2/L12)

(ref: Klahr_1997) Klahr, H. H., & Henning, T. 1997, Icarus, 128, 213, doi: [`10.1006/icar.1997.5720`](http://doi.org/10.1006/icar.1997.5720)

(ref: Konigl_2000) Konigl, A., & Pudritz, R. E. 2000, in Protostars and Planets IV, ed. V. Mannings, A. P. Boss, & S. S. Russell, 759, doi: [`10.48550/arXiv.astro-ph/9903168`](http://doi.org/10.48550/arXiv.astro-ph/9903168)

(ref: Kraus_2012) Kraus, A. L., & Ireland, M. J. 2012, ApJ, 745, 5, doi: [`10.1088/0004-637X/745/1/5`](http://doi.org/10.1088/0004-637X/745/1/5)

(ref: Kraus_2011) Kraus, A. L., Ireland, M. J., Martinache, F., & Hillenbrand, L. A. 2011, ApJ, 731, 8, doi: [`10.1088/0004-637X/731/1/8`](http://doi.org/10.1088/0004-637X/731/1/8)

(ref: Kudo_2018) Kudo, T., Hashimoto, J., Muto, T., et al. 2018, ApJL, 868, L5, doi: [`10.3847/2041-8213/aaeb1c`](http://doi.org/10.3847/2041-8213/aaeb1c)

(ref: Lin_1979) Lin, D. N. C., & Papaloizou, J. 1979, MNRAS, 186, 799, doi: [`10.1093/mnras/186.4.799`](http://doi.org/10.1093/mnras/186.4.799)

(ref: Lin_2023) Lin, Z.-Y. D., Li, Z.-Y., Yang, H., et al. 2023, MNRAS, 520, 1210, doi: [`10.1093/mnras/stad173`](http://doi.org/10.1093/mnras/stad173)

(ref: Lin_2024) Lin, Z.-Y. D., Li, Z.-Y., Stephens, I. W., et al. 2024, MNRAS, 528, 843, doi: [`10.1093/mnras/stae040`](http://doi.org/10.1093/mnras/stae040)

(ref: Liu_2019) Liu, H. B. 2019, ApJL, 877, L22, doi: [`10.3847/2041-8213/ab1f8e`](http://doi.org/10.3847/2041-8213/ab1f8e)

(ref: Liu_2024) Liu, H. B., Muto, T., Konishi, M., et al. 2024, A&A, 685, A18, doi: [`10.1051/0004-6361/202348896`](http://doi.org/10.1051/0004-6361/202348896)

(ref: Liu_2017) Liu, Y., Henning, T., Carrasco-González, C., et al. 2017, A&A, 607, A74, doi: [`10.1051/0004-6361/201629786`](http://doi.org/10.1051/0004-6361/201629786)

(ref: Lodato_2019) Lodato, G., Dipierro, G., Ragusa, E., et al. 2019, MNRAS, 486, 453, doi: [`10.1093/mnras/stz913`](http://doi.org/10.1093/mnras/stz913)

(ref: Long_2022) Long, F., Andrews, S. M., Zhang, S., et al. 2022, ApJL, 937, L1, doi: [`10.3847/2041-8213/ac8b10`](http://doi.org/10.3847/2041-8213/ac8b10)

(ref: Macias_2021) Macı́as, E., Guerra-Alvarado, O., Carrasco-González, C., et al. 2021, A&A, 648, A33, doi: [`10.1051/0004-6361/202039812`](http://doi.org/10.1051/0004-6361/202039812)

(ref: Macias_2018) Macı́as, E., Espaillat, C. C., Ribas, Á., et al. 2018, ApJ, 865, 37, doi: [`10.3847/1538-4357/aad811`](http://doi.org/10.3847/1538-4357/aad811)

(ref: Manara_2014) Manara, C. F., Testi, L., Natta, A., et al. 2014, A&A, 568, A18, doi: [`10.1051/0004-6361/201323318`](http://doi.org/10.1051/0004-6361/201323318)

(ref: Mauco_2021) Maucó, K., Carrasco-González, C., Schreiber, M. R., et al. 2021, ApJ, 923, 128, doi: [`10.3847/1538-4357/ac21d0`](http://doi.org/10.3847/1538-4357/ac21d0)

(ref: McMullin_2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mori_2019) Mori, T., Kataoka, A., Ohashi, S., et al. 2019, ApJ, 883, 16, doi: [`10.3847/1538-4357/ab3575`](http://doi.org/10.3847/1538-4357/ab3575)

(ref: Mouillet_2001) Mouillet, D., Lagrange, A. M., Augereau, J. C., & Ménard, F. 2001, A&A, 372, L61, doi: [`10.1051/0004-6361:20010660`](http://doi.org/10.1051/0004-6361:20010660)

(ref: Muto_2012) Muto, T., Grady, C. A., Hashimoto, J., et al. 2012, ApJL, 748, L22, doi: [`10.1088/2041-8205/748/2/L22`](http://doi.org/10.1088/2041-8205/748/2/L22)

(ref: Natta_2006) Natta, A., Testi, L., & Randich, S. 2006, A&A, 452, 245, doi: [`10.1051/0004-6361:20054706`](http://doi.org/10.1051/0004-6361:20054706)

(ref: Paneque_2021) Paneque-Carreño, T., Pérez, L. M., Benisty, M., et al. 2021, ApJ, 914, 88, doi: [`10.3847/1538-4357/abf243`](http://doi.org/10.3847/1538-4357/abf243)

(ref: Pascucci_2023) Pascucci, I., Cabrit, S., Edwards, S., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 567, doi: [`10.48550/arXiv.2203.10068`](http://doi.org/10.48550/arXiv.2203.10068)

(ref: Pearson_1999) Pearson, T. J. 1999, in Astronomical Society of the Pacific Conference Series, Vol. 180, Synthesis Imaging in Radio Astronomy II, ed. G. B. Taylor, C. L. Carilli, & R. A. Perley, 335

(ref: Perez_2014) Pérez, L. M., Isella, A., Carpenter, J. M., & Chandler, C. J. 2014, ApJL, 783, L13, doi: [`10.1088/2041-8205/783/1/L13`](http://doi.org/10.1088/2041-8205/783/1/L13)

(ref: Perez_2012) Pérez, L. M., Carpenter, J. M., Chandler, C. J., et al. 2012, ApJL, 760, L17, doi: [`10.1088/2041-8205/760/1/L17`](http://doi.org/10.1088/2041-8205/760/1/L17)

(ref: Perez_2015) Pérez, L. M., Chandler, C. J., Isella, A., et al. 2015, ApJ, 813, 41, doi: [`10.1088/0004-637X/813/1/41`](http://doi.org/10.1088/0004-637X/813/1/41)

(ref: Perez_2016) Pérez, L. M., Carpenter, J. M., Andrews, S. M., et al. 2016, Science, 353, 1519, doi: [`10.1126/science.aaf8296`](http://doi.org/10.1126/science.aaf8296)

(ref: Pinilla_2012) Pinilla, P., Benisty, M., & Birnstiel, T. 2012a, A&A, 545, A81, doi: [`10.1051/0004-6361/201219315`](http://doi.org/10.1051/0004-6361/201219315)

(ref: Pinilla_2012b) Pinilla, P., Birnstiel, T., Ricci, L., et al. 2012b, A&A, 538, A114, doi: [`10.1051/0004-6361/201118204`](http://doi.org/10.1051/0004-6361/201118204)

(ref: Pinilla_2016) Pinilla, P., Flock, M., Ovelar, M. d. J., & Birnstiel, T. 2016, A&A, 596, A81, doi: [`10.1051/0004-6361/201628441`](http://doi.org/10.1051/0004-6361/201628441)

(ref: Pinilla_2020) Pinilla, P., Pascucci, I., & Marino, S. 2020, A&A, 635, A105, doi: [`10.1051/0004-6361/201937003`](http://doi.org/10.1051/0004-6361/201937003)

(ref: Pinilla_2014) Pinilla, P., Benisty, M., Birnstiel, T., et al. 2014, A&A, 564, A51, doi: [`10.1051/0004-6361/201323322`](http://doi.org/10.1051/0004-6361/201323322)

(ref: Pinilla_2017) Pinilla, P., Pérez, L. M., Andrews, S., et al. 2017, ApJ, 839, 99, doi: [`10.3847/1538-4357/aa6973`](http://doi.org/10.3847/1538-4357/aa6973)

(ref: Pinilla_2018) Pinilla, P., Tazzari, M., Pascucci, I., et al. 2018, ApJ, 859, 32, doi: [`10.3847/1538-4357/aabf94`](http://doi.org/10.3847/1538-4357/aabf94)

(ref: Regaly_2012) Regály, Z., Juhász, A., Sándor, Z., & Dullemond, C. P. 2012, MNRAS, 419, 1701, doi: [`10.1111/j.1365-2966.2011.19834.x`](http://doi.org/10.1111/j.1365-2966.2011.19834.x)

(ref: Ribas_2015) Ribas, Á., Bouy, H., & Merı́n, B. 2015, A&A, 576, A52, doi: [`10.1051/0004-6361/201424846`](http://doi.org/10.1051/0004-6361/201424846)

(ref: Rich_2021) Rich, E. A., Teague, R., Monnier, J. D., et al. 2021, ApJ, 913, 138, doi: [`10.3847/1538-4357/abf92e`](http://doi.org/10.3847/1538-4357/abf92e)

(ref: Rilinger_2023) Rilinger, A. M., Espaillat, C. C., Xin, Z., et al. 2023, ApJ, 944, 66, doi: [`10.3847/1538-4357/aca905`](http://doi.org/10.3847/1538-4357/aca905)

(ref: Robert_2020) Robert, C. M. T., Méheut, H., & Ménard, F. 2020, A&A, 641, A128, doi: [`10.1051/0004-6361/201937414`](http://doi.org/10.1051/0004-6361/201937414)

(ref: Schapler_2004) Schräpler, R., & Henning, T. 2004, ApJ, 614, 960, doi: [`10.1086/423831`](http://doi.org/10.1086/423831)

(ref: Semenov_2018) Semenov, D., Favre, C., Fedele, D., et al. 2018, A&A, 617, A28, doi: [`10.1051/0004-6361/201832980`](http://doi.org/10.1051/0004-6361/201832980)

(ref: Sierra_2020) Sierra, A., & Lizano, S. 2020, ApJ, 892, 136, doi: [`10.3847/1538-4357/ab7d32`](http://doi.org/10.3847/1538-4357/ab7d32)

(ref: Sierra_2019) Sierra, A., Lizano, S., Macı́as, E., et al. 2019, ApJ, 876, 7, doi: [`10.3847/1538-4357/ab1265`](http://doi.org/10.3847/1538-4357/ab1265)

(ref: Sierra_2021) Sierra, A., Pérez, L. M., Zhang, K., et al. 2021, ApJS, 257, 14, doi: [`10.3847/1538-4365/ac1431`](http://doi.org/10.3847/1538-4365/ac1431)

(ref: Strom_1989) Strom, K. M., Strom, S. E., Edwards, S., Cabrit, S., & Skrutskie, M. F. 1989, AJ, 97, 1451, doi: [`10.1086/115085`](http://doi.org/10.1086/115085)

(ref: Takeuchi_2002) Takeuchi, T., & Lin, D. N. C. 2002, ApJ, 581, 1344, doi: [`10.1086/344437`](http://doi.org/10.1086/344437)

(ref: Tazaki_2019) Tazaki, R., Tanaka, H., Kataoka, A., Okuzumi, S., & Muto, T. 2019, ApJ, 885, 52, doi: [`10.3847/1538-4357/ab45f0`](http://doi.org/10.3847/1538-4357/ab45f0)

(ref: uvplot) Tazzari, M. 2017, mtazzari/uvplot, Zenodo, doi: [`10.5281/zenodo.1003113`](http://doi.org/10.5281/zenodo.1003113)

(ref: GoFish) Teague, R. 2019, The Journal of Open Source Software, 4, 1632, doi: [`10.21105/joss.01632`](http://doi.org/10.21105/joss.01632)

(ref: Terada_2023) Terada, Y., Liu, H. B., Mkrtichian, D., et al. 2023, ApJ, 953, 147, doi: [`10.3847/1538-4357/acdedf`](http://doi.org/10.3847/1538-4357/acdedf)

(ref: Testi_2001) Testi, L., Natta, A., Shepherd, D. S., & Wilner, D. J. 2001, ApJ, 554, 1087, doi: [`10.1086/321406`](http://doi.org/10.1086/321406)

(ref: Testi_2014) Testi, L., Birnstiel, T., Ricci, L., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 339–361, doi: [`10.2458/azu_uapress_9780816531240-ch015`](http://doi.org/10.2458/azu_uapress_9780816531240-ch015)

(ref: Thompson_2017) Thompson, A. R., Moran, J. M., & Swenson, George W., J. 2017, Interferometry and Synthesis in Radio Astronomy, 3rd Edition, doi: [`10.1007/978-3-319-44431-4`](http://doi.org/10.1007/978-3-319-44431-4)

(ref: Toomre_1964) Toomre, A. 1964, ApJ, 139, 1217, doi: [`10.1086/147861`](http://doi.org/10.1086/147861)

(ref: Ubeira_2019) Ubeira Gabellini, M. G., Miotello, A., Facchini, S., et al. 2019, MNRAS, 486, 4638, doi: [`10.1093/mnras/stz1138`](http://doi.org/10.1093/mnras/stz1138)

(ref: Ueda_2020) Ueda, T., Kataoka, A., & Tsukagoshi, T. 2020, ApJ, 893, 125, doi: [`10.3847/1538-4357/ab8223`](http://doi.org/10.3847/1538-4357/ab8223)

(ref: vanderMarel_2023) van der Marel, N. 2023, European Physical Journal Plus, 138, 225, doi: [`10.1140/epjp/s13360-022-03628-0`](http://doi.org/10.1140/epjp/s13360-022-03628-0)

(ref: vanderMarel_2016) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2016, A&A, 585, A58, doi: [`10.1051/0004-6361/201526988`](http://doi.org/10.1051/0004-6361/201526988)

(ref: vanderMarel_2015) van der Marel, N., van Dishoeck, E. F., Bruderer, S., Pérez, L., & Isella, A. 2015, A&A, 579, A106, doi: [`10.1051/0004-6361/201525658`](http://doi.org/10.1051/0004-6361/201525658)

(ref: vanderMarel_2021) van der Marel, N., Birnstiel, T., Garufi, A., et al. 2021, AJ, 161, 33, doi: [`10.3847/1538-3881/abc3ba`](http://doi.org/10.3847/1538-3881/abc3ba)

(ref: Varga_2021) Varga, J., Hogerheijde, M., van Boekel, R., et al. 2021, A&A, 647, A56, doi: [`10.1051/0004-6361/202039400`](http://doi.org/10.1051/0004-6361/202039400)

(ref: Wahhaj_2010) Wahhaj, Z., Cieza, L., Koerner, D. W., et al. 2010, ApJ, 724, 835, doi: [`10.1088/0004-637X/724/2/835`](http://doi.org/10.1088/0004-637X/724/2/835)

(ref: Weidenschilling_1977) Weidenschilling, S. J. 1977, MNRAS, 180, 57, doi: [`10.1093/mnras/180.2.57`](http://doi.org/10.1093/mnras/180.2.57)

(ref: Whipple_1972) Whipple, F. L. 1972, in From Plasma to Planet, ed. A. Elvius, 211

(ref: Wolfer_2023) Wölfer, L., Facchini, S., van der Marel, N., et al. 2023, A&A, 670, A154, doi: [`10.1051/0004-6361/202243601`](http://doi.org/10.1051/0004-6361/202243601)

(ref: Yang_2024) Yang, H., Fernández-López, M., Li, Z.-Y., et al. 2024, ApJ, 963, 134, doi: [`10.3847/1538-4357/ad2346`](http://doi.org/10.3847/1538-4357/ad2346)

(ref: Yang_2016) Yang, H., Li, Z.-Y., Looney, L., & Stephens, I. 2016, MNRAS, 456, 2794, doi: [`10.1093/mnras/stv2633`](http://doi.org/10.1093/mnras/stv2633)

(ref: Zapata_2017) Zapata, L. A., Rodrı́guez, L. F., & Palau, A. 2017, ApJ, 834, 138, doi: [`10.3847/1538-4357/834/2/138`](http://doi.org/10.3847/1538-4357/834/2/138)

(ref: Zhang_2023) Zhang, S., Zhu, Z., Ueda, T., et al. 2023, ApJ, 953, 96, doi: [`10.3847/1538-4357/acdb4e`](http://doi.org/10.3847/1538-4357/acdb4e)

(ref: Zhu_2019) Zhu, Z., Zhang, S., Jiang, Y.-F., et al. 2019, ApJL, 877, L18, doi: [`10.3847/2041-8213/ab1f8c`](http://doi.org/10.3847/2041-8213/ab1f8c)

(ref: Zurlo_2020) Zurlo, A., Cugno, G., Montesinos, M., et al. 2020, A&A, 633, A119, doi: [`10.1051/0004-6361/201936891`](http://doi.org/10.1051/0004-6361/201936891)

[^1]: <https://safe.nrao.edu/evla/disks/>

[^2]: available at <https://github.com/discsim/frank>

[^3]: Note that $R_{\rm max}$ is not a rigorous measurement of the disk radius but rather the maximum radial extent in the visibility fit. As suggested by (cite: Jennings_2020), a suitable choice for $R_{\rm max}$ is typically greater than 1.5 times the expected disk radius.

</paper>

Write the methods card for this paper.