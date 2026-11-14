# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...653L...9V\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...653L...9V",
 "title": "If you like C/O variations, you should have put a ring on it",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "van der Marel, Nienke",
 "n_authors": 5,
 "arxiv_id": "2108.07679",
 "doi": "10.1051/0004-6361/202141786",
 "alma_projects_linked_by_archive": [
  "2013.1.00198.S",
  "2013.1.00226.S",
  "2015.1.00671.S",
  "2015.1.00888.S",
  "2015.1.00964.S",
  "2016.1.00459.S",
  "2016.1.00627.S",
  "2017.1.00834.S",
  "2017.1.01167.S",
  "2017.A.00006.S",
  "2019.1.01619.S"
 ]
}
```

Paper text:
<paper>
# If you like C/O variations, you should have put a ring on it

The C/O-ratio as traced with C$_2$H emission in protoplanetary disks is fundamental for constraining the formation mechanisms of exoplanets and our understanding of volatile depletion in disks, but current C$_2$H observations show an apparent bimodal distribution which is not well understood, indicating that the C/O distribution is not described by a simple radial dependence. The transport of icy pebbles has been suggested to alter the local elemental abundances in protoplanetary disks, through settling, drift and trapping in pressure bumps resulting in a depletion of volatiles in the surface and an increase of the elemental C/O. We combine all disks with spatially resolved ALMA C$_2$H observations with high-resolution continuum images and constraints on the CO snowline to determine if the C$_2$H emission is indeed related to the location of the icy pebbles. We report a possible correlation between the presence of a significant CO-icy dust reservoir and high C$_2$H emission, which is only found in disks with dust rings outside the CO snowline. In contrast, compact dust disks (without pressure bumps) and warm transition disks (with their dust ring inside the CO snowline) are not detected in C$_2$H, suggesting that such disks may never have contained a significant CO ice reservoir. This correlation provides evidence for the regulation of the C/O profile by the complex interplay of CO snowline and pressure bump locations in the disk. These results demonstrate the importance of including dust transport in chemical disk models, for a proper interpretation of exoplanet atmospheric compositions, and a better understanding of volatile depletion in disks, in particular the use of CO isotopologues to determine gas surface densities.

# Introduction

Elemental abundance ratios such as C/O and C/H are some of the most fundamental properties of the composition of protoplanetary disks and, as a result, of gas giant exoplanetary atmospheres (cite: Madhusudhan2019; Cridland2020). The C/O-ratio in exoplanet atmospheres is considered a key measurement to link to the formation location of the planet in the disk. Whereas the classical view of an increasing step function in the disk at snowline locations (cite: Oberg2011) has been expanded to a more advanced view due to pebble drift (cite: Oberg2016; Booth2017; Krijt2020; Schneider2021), the precise mechanisms leading to variations in C/O are still poorly understood (cite: Bosman2021). Current disk surveys of C/O tracers such as C$_2$H (cite: Bergin2016; Semenov2018; Cleeves2018) appear to show a bimodal distribution of disks with and without C$_2$H detection indicating either high (C/O$>$1) or low (C/O$<$1) ratios (cite: Bergner2019; Miotello2019) but it is unclear whether this bimodality is an intrinsic property or the result of physical-chemical processes. The recent discovery of low C/O at the location of the asymmetric Oph IRS 48 dust trap (cite: Booth2021-irs48) suggests that pressure bumps may play a key role in regulating the C/O profile in disks, which is particularly relevant considering that pressure bumps are usually associated with giant planets (cite: Pinilla2012a; vanderMarel2016-isot) and those planets would accrete the composition of the gaseous material at the bump location. Pressure bumps act as dust traps, where large dust grains concentrate due to the gas-grain drag forces (cite: Birnstiel2010), which results in the appearance of dust rings in continuum images of protoplanetary disks (cite: Pinilla2012b). In this manuscript the term dust ring and pressure bump are used interchangeably, although dust rings without pressure bumps may also exist (cite: Okuzumi2016; Vericel2021). The samples of the C$_2$H surveys by (cite: Bergner2019; Miotello2019) are biased towards brighter millimeter continuum disks, which are known to contain pressure bumps more often (cite: Pinilla2020; vanderMarelMulders2021), as either ring disks (cite: Andrews2018) or transition disks with inner cavities (cite: Francis2020). However, a clear correlation between C$_2$H emission and dust substructure has so far not been identified (cite: Bergin2016; Miotello2019; Bosman2021).

A connection between volatile composition and pebble transport has been previously suggested for infrared line measurements of H$_2$, CO and H$_2$O in TW Hya (cite: Bosman2019), and for the anti-correlation of the H$_2$O/HCN ratio of warm rovibrational lines and radial dust disk size (cite: Najita2013; Banzatti2020). They pose a scenario where H$_2$O vapor is elevated for the most compact disks where dust has drifted inside the H2O snowline, whereas disks with pressure bumps show lower or no H$_2$O emission. The direct irradiation of the inner cavity wall may play an important role in particular in the desorption of oxygen-rich volatiles in transition disks (cite: Cleeves2011; vanderMarel2021-irs48). Although dust rings are commonly detected in the brightest disks, they may actually not be that common in the total disk population (cite: vanderMarelMulders2021): the selection bias of chemistry studies towards brighter disks could be a severe limitation in our understanding of the C/O in disks.

Interestingly, changes in the C/O-ratio as a result of pebble transport may also reflect changes in the CO/H$_2$, which is $\sim$few$\cdot10^{-4}$ in the interstellar medium (ISM). In models including pebble transport (cite: Oberg2016; Krijt2020), molecular CO is depleted by 1-2 orders of magnitude in the outer disk, which is indeed seen in spatially resolved CO isotopologue observations (cite: Schwarz2016; Schwarz2019; Zhang2019) and shown to happen in the transition between the protostellar to the protoplanetary disk phase (cite: Zhang2020evolution; Bergner2020). As the mixture of ices that are most affected by this depletion process (e.g. H$_2$O, CO$_2$, CO) is overall oxygen-rich, this process can result in outer disk surface layers with C/O$>$1 in the gas-phase (cite: Krijt2020; Bosman2021).

CO depletion can explain why CO isotopologue measurements of protoplanetary disks appear to result in very low gas masses (cite: Ansdell2016; Miotello2017; Long2017), in particular in comparison with alternative gas measurements such as HD (cite: Bergin2013; McClure2016) and typical disk accretion rates (cite: Manara2016). As the gas distribution in protoplanetary disks is fundamental for models of e.g. giant planet formation, disk evolution and planet-disk interaction (cite: Helled2014; Andrews2020), a better understanding on the effect of dust substructure on the volatile composition would also inform disk models used to infer gas masses from CO observations.

In this letter we aim to study the connection between the C/O-ratio in the gas in the outer disk, dust substructure and pebble transport by a detailed analysis of the spatially resolved C$_2$H profiles from the literature and the highest resolution ALMA continuum images available for these sources. We will focus in particular on the position of the CO snowline w.r.t. the dust rings, as dust pebbles rich in CO ice are expected to drift inwards to the nearest pressure bump and release the CO into the gas-phase inside the CO snowline through sublimation, resulting in an enrichment of the CO abundance and restoring the C/O-ratio to $\sim$1. However, dust rings may be present either inside or outside the CO snowline, depending on their location and the brightness of the star. The aim of this study is to test if the combination of the stellar properties (and resulting CO snowline) and dust substructure regulates the radial C/O profiles in the disk.

# Observations

Our sample consists of all protoplanetary disks with deep, spatially resolved C$_2$H observations from the literature, primarily from ALMA (cite: Bergin2016; Bergner2019; Miotello2019; Facchini2021) and unpublished ALMA data of IRS 48. Most of these disks are observed in the 262.006 GHz C$_2$H hyperfine doublet ($N=3-2,J=7/2-5/2,F=4-3$ and $F=3-2$), and a handful in the 349.4 GHz doublet ($N=4-3,J=7/2-5/2,F=4-3$ and $F=3-2$). The Miotello sample was selected from the brightest continuum disks in Lupus with a CO isotopologue detection and the Bergner sample from bright continuum disks covering a range of stellar and age properties. We add three other disks: TW Hya (cite: Bergin2016), PDS 70 (cite: Facchini2021) and IRS 48 (cite: vanderMarel2021-irs48). For DM Tau, two published datasets exist (cite: Bergin2016; Bergner2019) and we choose to include the latter.

The disks are observed at a range of sensitivities and are located at distances between 60 and 175 pc, covering a range of stellar luminosity, spectral type and age. The spatial resolution varies between 0.2" and 0.8", or $\sim$40 au spatial scales. The sample consists of 26 disks, with 20 C$_2$H detections and 6 non-detections. The sample is listed in Table [\[tab:sample\]](#tab:sample).

For all disks, high-resolution continuum data at either 870 $\mu$m or 1.3 mm (ALMA Band 7 or 6) have been taken with constraints on the dust substructure. Most continuum images have previously been published (references in Table [\[tab:sample\]](#tab:sample)) and have a typical spatial resolution of 0.05" or $\sim$8 au. The images are shown in Figure [3](#fig:gallery) and cover a range of dust morphologies, including compact, ring and transition disks. Compact disks are defined as disks without large scale gaps, following (cite: vanderMarelMulders2021), transition disks as disks with a cleared inner dust cavity, and ring disks as disks with one or more gaps in the outer disk.

# Analysis

In order to investigate the role of dust substructure onto the presence of C$_2$H, the C$_2$H emission needs to be normalized spatially across the sample, as the sample consists of disks of a range of sizes, and the integrated flux (as used by the original studies) may not be representative. Therefore we use the azimuthally averaged radial profiles of the integrated C$_2$H emission, and use the peak value as our main measurement of the C$_2$H brightness, or the 3$\sigma$ upper limit of the integrated emission in case of a non-detection. As the doublet lines are blended, the integrated emission represents the integration over both lines. For the data in (cite: Bergin2016), (cite: Bergner2019) and (cite: Facchini2021) such radial profiles are provided. For the sample of (cite: Miotello2019), the azimuthally averaged profiles are computed from their zero-moment maps. All profiles are presented in Appendix [7](#sec:figures). For IRS 48, the C$_2$H 349.4 GHz line upper limit was derived in Appendix [8](#sec:irs48). In order to normalize the sample across spatial scales and beam sizes, the integrated peak flux density is converted to the brightness temperature and scaled to a distance of 100 pc. The resulting scaled peak brightness temperatures are listed in Table [\[tab:sample\]](#tab:sample).

The dust continuum images can provide a measurement of the amount of dust mass inside and outside the CO snowline. The latter provides a measurement of the amount of CO-ice-covered dust mass $M_{\rm dust,CO}$ or cold dust reservoir, which is hypothesized to dominate the regulation of the elemental abundance ratio. The CO snowline is defined as the location where the temperature (computed from the stellar luminosity) drops below 22 or 30 K and the details of this calculation are provided in Section [6](#sec:dustcalc). The $M_{\rm dust,CO}$ values are listed in Table [\[tab:sample\]](#tab:sample).

![image](Temperatures_dustmass_range_C2H.pdf) ![image](C2H_asurv_Mdust.pdf)

# Results

![](Warm_cold_disk_schem_C2H_emm_color.pdf)

The disks with a C$_2$H non-detection have little or no dust emission outside the CO snowline (Figure [4](#fig:profiles)), whereas all C$_2$H detections still have a significant cold dust reservoir. The CO snowline as determined by a temperature profile is a reasonable approximation, with the note that the measured CO snowline appears to lie further out for the transition disks (suggesting a somewhat warmer temperature profile) and somewhat closer in for the ring disks, where available. Due to the lack of CO snowline measurements for the bulk of the disks the dust mass outside the CO snowline can only be derived consistently throughout the sample using the temperature profile, with the caveat that the dust mass may be somewhat underestimated for the ring disks and overestimated for the transition disks. For the transition disks most dust rings lie at or outside the CO snowline, with the exception of IRS 48 and V4046 Sgr. For J16070854 the dust ring is difficult to identify due to the spatial resolution of the image, but visibility modeling indicates an inner cavity of $\sim$40 au (cite: vanderMarel2018).

The scaled C$_2$H peak brightness varies across the sample from $<$1.1 up to 97 K km s$^{-1}$. The upper limits lie on the lower end of the detection values, but there is no obvious bimodal distribution as seen in the integrated flux (cite: Miotello2019). The scaled C$_2$H peak temperature for PDS 70, V4046 Sgr, TW Hya and IM Lup is at a similar level as the upper limits.

Using these properties, we now look for a dependence of the C$_2$H peak flux on the amount of icy dust mass in Figure [1](#fig:outerdustmass). The data points show the range of dust masses consistent with a CO snowline temperature of 22 to 30 K. As the dust emission is usually ring-like, the shift in CO snowline temperature has a profound effect in some dust masses, and negligible in others, as can be seen also in the $M_{\rm dust,CO}$ values in Table [\[tab:sample\]](#tab:sample). Beam dilution is possibly affecting the estimates for the lower resolution images so some of these values may be upper limits. Figure [1](#fig:outerdustmass) also shows the cumulative distributions of the disks with and without C$_2$H detection, using the Kaplan-Meier estimator (KME) from the ASURV package (cite: Lavalley1992). The mean icy dust mass of the C$_2$H-detection group is 18$\pm$3 $M_{\oplus}$, whereas the mean icy dust mass of the C$_2$H-non-detection group is 2.0$\pm$0.9 $M_{\oplus}$.

For the scaled C$_2$H peak fluxes we compute a two sample test using ASURV (to properly treat the upper limits of the C$_2$H data points). The Gehan’s Wilcoxon test (to include upper limits) indicates a probability of 0.5% that the two groups have been drawn from the same population. For the icy dust masses, this probability is 0.06%, so we can indeed conclude the groups are statistically distinct. In order to check that this is not caused by an underlying correlation with another parameter, we perform a Kolmogorov-Smirnov statistic test for stellar luminosity $L_*$ and total dust mass $M_{\rm dust}$, and find a probability of 92% for $L_*$ and a probability of 23% for $M_{\rm dust}$ that the two groups have been drawn from the same distribution, so the difference is likely not caused by either of these properties. For the disk dust size (defined as the radius $R_{68}$ which encircles 68% of the total flux), this probability is 3.6%, so there could be an underlying relation there as well, although not as strong as with the icy dust mass, and the two parameters are obviously related.

# Discussion and conclusions

The connection between the C$_2$H peak flux and the icy dust mass outside the CO snowline from Figure [1](#fig:outerdustmass) indicates a direct link between the C/O-ratio and the presence of a CO-ice pebble reservoir. Such a reservoir requires mm-dust at large radii, hence prevention of radial drift through pressure bumps outside the snowline. According to (cite: Krijt2020), this results in a low CO abundance and elevated C/O$\gtrsim$1 in the surface layers in the regime outside the CO snowline, where the high C/O can be enhanced to $\gtrsim$1.5 as needed for a strong C$_2$H detection (cite: Bergin2016), by additional vertical mixing and destruction of carbonaceous grains (cite: Bosman2021). Inside the CO snowline the CO abundance returns to the ISM value of 10$^{-4}$ and C$_2$H is below typical detection thresholds, which is consistent with the radial C$_2$H profiles (see Section [7](#sec:figures)). The radial extent of C$_2$H is larger than the dust extent as the outer gas disk has been depleted by settling and radial drift of icy dust grains. The observed lack of anti-correlation between C$^{18}$O and C$_2$H by (cite: Bergner2020) is not at odds with this scenario, as they state that the C$_2$H production will not increase further with CO depletion when the C/O-ratio is already elevated (cite: Cleeves2018).

In contrast, the disks with a C$_2$H non-detection contain little or no CO-ice-covered mm-dust: in fact, 4 out of 6 of these disks are compact in continuum emission and do not show any signs of substructure. The exceptions to this rule are IRS 48 and J16070384. IRS 48 has a bright, asymmetric dust trap, but this trap is located *inside* the CO snowline unlike the other transition disks, whereas J16070384 shows a large edge-on dust ring, but is overall very faint in mm-dust.

If low C/O (C$_2$H non-detection) is indeed linked to the lack of CO ice, this suggests that these disks may never have contained a significant cold dust reservoir. This is indeed possible for the compact disks, under the assumption that the disks were warmer in the embedded phase and the pebbles have drifted in before CO could freeze out. Faint CO emission in disks was recently suggested to be caused by these disks being compact and warmer (cite: Miotello2021). In that case, the scenario of ice-covered pebble drift to inside the CO snowline by (cite: Krijt2020) would not actually occur in disks. The detection of H$_2$CO and CH$_3$OH emission in IRS 48 (cite: vanderMarel2021-irs48) implies that this disk has either been cold enough to have CO-ice in the past, or has inherited H$_2$CO and CH$_3$OH from the dark cloud phase (cite: Drozdovskaya2014; Booth2021-hd100) as CH$_3$OH-ice sublimates at higher temperatures.

Other than IRS 48, the transition disks in this sample have their dust rings outside the CO snowline, implying that the bulk of the CO ice is not returned to the gas phase and they are essentially the same as ring disks. The CO snowline in transition disks may lie further out than our estimates, as revealed by the direct measurements of the CO snowline of e.g. DM Tau and LkCa 15 (cite: Qi2019). However, considering their radial profiles, this will not significantly decrease their icy dust mass to the level of the C$_2$H non-detections.

The four disks with low C$_2$H (IM Lup, TW Hya, PDS 70 and V4046 Sgr) may have a lower C/O-ratio than the bulk of the C$_2$H detections, consistent with the derived value of C/O$\sim$0.8 from the detailed analysis of IM Lup (cite: Cleeves2018). For TW Hya, (cite: Bergin2016) derived C/O$\gtrsim$1, which may still be lower than the value of C/O$>$1 of the majority of the Lupus disks derived by (cite: Miotello2019). These four disks may fall in between the two extremes of the C/O ratios in our sample. Interestingly, all but IM Lup are transition disks. Transition disks are known to have irradiated cavity walls, with higher temperatures and different compositions of sublimated species (cite: Cleeves2011; Bosman2019).

Alternatively, there is a possible correlation between the dust disk radius and the C$_2$H brightness, which would suggest that the C$_2$H non-detections may just be caused by a smaller dust surface density area. Such a correlation could be understood if C$_2$H emission is primarily produced by fragmentation of large grains that are mixed vertically into the hot surface layers, which is indeed predicted as a contributing factor to C$_2$H (cite: Bosman2021). However, such a relation would not be able to explain the low C/O in IRS 48. The current sample of available C$_2$H observations is not well-constructed to fully test our proposed scenario. Targeted, high-resolution observations of disks with pressure bumps inside and outside the CO snowline are needed.

In summary, this work suggests that the C/O value in disks (as traced by the C$_2$H emission) is related to the formation and transport of CO ice-covered dust pebbles. Figure [2](#fig:cartoon) presents a summary of the proposed scenario. In large, cold ring disks the existence of cold pebble reservoir results in a low CO abundance and uniform, high C/O ratio in the surface layers. [^1] Alternatively, compact and/or warm disks do not efficiently sequester CO-ice in the midplane and retain high CO and low C/O abundances at all radii. In general, the efficiency of CO ice sequestration in the midplane depends on the interplay between dust coagulation, vertical settling, and turbulent mixing.

In transition disks, irradiation of cavity walls increases the desorption of ices (cite: Cleeves2011), possibly lowering the gaseous C/O-ratio to $\sim0.5$ further out, as the temperature gets high enough to desorb oxygen-rich ices. This means that the C/O-ratio of giant planets inside the gaps is set by the complex interplay between pressure bumps and snowlines. If this hypothesis is correct, chemical disk models need to take dust transport and pebble history into account when analyzing CO and other molecular lines for proper interpretation, with new potential to use CO isotopologue data to derive gas surface densities in disks. Using the current dust morphology, the effect of CO depletion due to dust transport can be estimated directly and used to set the CO abundance in the disk, used to derive gas surface densities.

This result is particularly timely as many spectra of exoplanet atmospheres are expected to be delivered in the coming years with e.g. the James Webb Space Telescope (JWST). As the exoplanet atmospheric composition and C/O-ratio is set by accretion of gas and icy pebbles, including gas released from fragmentation of icy pebbles (cite: Cridland2020), its formation history can only be interpreted when the C/O distribution in disks is properly understood.

# Acknowledgements

We would like to thank the referee for their constructive comments which have helped to clarify the manuscript, and we thank Anna Miotello for useful feedback and Feng Long for the provided continuum data of the Taurus disks. N.M. acknowledges support from the Banting Postdoctoral Fellowships program, administered by the Government of Canada. G.D.M. acknowledges support from ANID — Millennium Science Initiative — ICN12_009. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/ NRAO and NAOJ. This paper makes use of the following ALMA data: 2013.1.00198.S, 2013.1.00226, 2015.1.00671.S, 2015.1.00964.S, 2016.1.00627.S, 2016.1.00459.S, 2015.1.00888.S, 2017.A.00006.S, 2017.1.01167.S, 2017.1.00834.S, 2019.1.01619.S.

62 natexlab

(ref: Andrews2020) Andrews, S. M. 2020, ARA&A, 58, 483

(ref: Andrews2018) Andrews, S. M., Terrell, M., Tripathi, A., et al. 2018, ApJ, 865, 157

(ref: Andrews2016) Andrews, S. M., Wilner, D. J., Zhu, Z., et al. 2016, ApJL, 820, L40

(ref: Ansdell2018) Ansdell, M., Williams, J. P., Trapman, L., et al. 2018, ApJ, 859, 21

(ref: Ansdell2016) Ansdell, M., Williams, J. P., van der Marel, N., et al. 2016, ApJ, 828, 46

(ref: Banzatti2020) Banzatti, A., Pascucci, I., Bosman, A. D., et al. 2020, ApJ, 903, 124

(ref: Barenfeld2016) Barenfeld, S. A., Carpenter, J. M., Ricci, L., & Isella, A. 2016, ApJ, 827, 142

(ref: Bergin2013) Bergin, E. A., Cleeves, L. I., Gorti, U., et al. 2013, Nature, 493, 644

(ref: Bergin2016) Bergin, E. A., Du, F., Cleeves, L. I., et al. 2016, ApJ, 831, 101

(ref: Bergner2020) Bergner, J. B., Öberg, K. I., Bergin, E. A., et al. 2020, ApJ, 898, 97

(ref: Bergner2019) Bergner, J. B., Öberg, K. I., Bergin, E. A., et al. 2019, ApJ, 876, 25

(ref: Birnstiel2010) Birnstiel, T., Dullemond, C. P., & Brauer, F. 2010, A&A, 513, A79

(ref: Bisschop2006) Bisschop, S. E., Fraser, H. J., Öberg, K. I., van Dishoeck, E. F., & Schlemmer, S. 2006, A&A, 449, 1297

(ref: Booth2021-irs48) Booth, A. S., van der Marel, N., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021a, A&A, 651, L6

(ref: Booth2021-hd100) Booth, A. S., Walsh, C., Terwisscha van Scheltinga, J., et al. 2021b, Nature Astronomy \[\]

(ref: Booth2017) Booth, R. A., Clarke, C. J., Madhusudhan, N., & Ilee, J. D. 2017, MNRAS, 469, 3994

(ref: Bosman2021) Bosman, A. D., Alarcón, F., Zhang, K., & Bergin, E. A. 2021, ApJ, 910, 3

(ref: Bosman2019) Bosman, A. D. & Banzatti, A. 2019, A&A, 632, L10

(ref: Chiang1997) Chiang, E. I. & Goldreich, P. 1997, ApJ, 490, 368

(ref: Cleeves2011) Cleeves, L. I., Bergin, E. A., Bethell, T. J., et al. 2011, ApJL, 743, L2

(ref: Cleeves2018) Cleeves, L. I., Öberg, K. I., Wilner, D. J., et al. 2018, ApJ, 865, 155

(ref: Cridland2020) Cridland, A. J., van Dishoeck, E. F., Alessi, M., & Pudritz, R. E. 2020, A&A, 642, A229

(ref: Drozdovskaya2014) Drozdovskaya, M. N., Walsh, C., Visser, R., Harsono, D., & van Dishoeck, E. F. 2014, MNRAS, 445, 913

(ref: Dullemond2001) Dullemond, C. P., Dominik, C., & Natta, A. 2001, ApJ, 560, 957

(ref: Facchini2020) Facchini, S., Benisty, M., Bae, J., et al. 2020, A&A, 639, A121

(ref: Facchini2021) Facchini, S., Teague, R., Bae, J., et al. 2021, arXiv, 2101.08369

(ref: Francis2020) Francis, L. & van der Marel, N. 2020, ApJ, 892, 111

(ref: Helled2014) Helled, R., Bodenheimer, P., Podolak, M., et al. 2014, in PPVI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 643

(ref: Hildebrand1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: Krijt2020) Krijt, S., Bosman, A. D., Zhang, K., et al. 2020, ApJ, 899, 134

(ref: Lavalley1992) Lavalley, M., Isobe, T., & Feigelson, E. 1992, in Astronomical Society of the Pacific Conference Series, Vol. 25, Astronomical Data Analysis Software and Systems I, ed. D. M. Worrall, C. Biemesderfer, & J. Barnes, 245

(ref: Long2019) Long, F., Herczeg, G. J., Harsono, D., et al. 2019, ApJ, 882, 49

(ref: Long2017) Long, F., Herczeg, G. J., Pascucci, I., et al. 2017, ApJ, 844, 99

(ref: Madhusudhan2019) Madhusudhan, N. 2019, ARA&A, 57, 617

(ref: Manara2016) Manara, C. F., Rosotti, G., Testi, L., et al. 2016, A&A, 591, L3

(ref: McClure2016) McClure, M. K., Bergin, E. A., Cleeves, L. I., et al. 2016, ApJ, 831, 167

(ref: Miotello2019) Miotello, A., Facchini, S., van Dishoeck, E. F., et al. 2019, A&A, 631, A69

(ref: Miotello2021) Miotello, A., Rosotti, G., Ansdell, M., et al. 2021, A&A, 651, A48

(ref: Miotello2017) Miotello, A., van Dishoeck, E. F., Williams, J. P., et al. 2017, A&A, 599, A113

(ref: Najita2013) Najita, J. R., Carr, J. S., Pontoppidan, K. M., et al. 2013, ApJ, 766, 134

(ref: Noble2012) Noble, J. A., Congiu, E., Dulieu, F., & Fraser, H. J. 2012, MNRAS, 421, 768

(ref: Oberg2016) Öberg, K. I. & Bergin, E. A. 2016, ApJL, 831, L19

(ref: Oberg2011) Öberg, K. I., Murray-Clay, R., & Bergin, E. A. 2011, ApJL, 743, L16

(ref: Okuzumi2016) Okuzumi, S., Momose, M., Sirono, S.-i., Kobayashi, H., & Tanaka, H. 2016, ApJ, 821, 82

(ref: Pinilla2012b) Pinilla, P., Benisty, M., & Birnstiel, T. 2012a, A&A, 545, A81

(ref: Pinilla2012a) Pinilla, P., Birnstiel, T., Ricci, L., et al. 2012b, A&A, 538, A114

(ref: Pinilla2020) Pinilla, P., Pascucci, I., & Marino, S. 2020, A&A, 635, A105

(ref: Pinte2018imlup) Pinte, C., Ménard, F., Duchêne, G., et al. 2018, A&A, 609, A47

(ref: Qi2015) Qi, C., Öberg, K. I., Andrews, S. M., et al. 2015, ApJ, 813, 128

(ref: Qi2019) Qi, C., Öberg, K. I., Espaillat, C. C., et al. 2019, ApJ, 882, 160

(ref: Schneider2021) Schneider, A. D. & Bitsch, B. 2021, arXiv e-prints, arXiv:2105.13267

(ref: Schwarz2016) Schwarz, K. R., Bergin, E. A., Cleeves, L. I., et al. 2016, ApJ, 823, 91

(ref: Schwarz2019) Schwarz, K. R., Bergin, E. A., Cleeves, L. I., et al. 2019, ApJ, 877, 131

(ref: Semenov2018) Semenov, D., Favre, C., Fedele, D., et al. 2018, A&A, 617, A28

(ref: vanderMarel2021-irs48) van der Marel, N., Booth, A. S., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021, A&A, 651, L5

(ref: vanderMarelMulders2021) van der Marel, N. & Mulders, G. D. 2021, AJ, 162, 28

(ref: vanderMarel2016-isot) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2016, A&A, 585, A58

(ref: vanderMarel2018) van der Marel, N., Williams, J. P., Ansdell, M., et al. 2018, ApJ, 854, 177

(ref: vantHoff2017) van ’t Hoff, M. L. R., Walsh, C., Kama, M., Facchini, S., & van Dishoeck, E. F. 2017, A&A, 599, A101

(ref: Vericel2021) Vericel, A., Gonzalez, J.-F., Price, D. J., Laibe, G., & Pinte, C. 2021, arXiv e-prints, arXiv:2108.00878

(ref: Zhang2019) Zhang, K., Bergin, E. A., Schwarz, K., Krijt, S., & Ciesla, F. 2019, ApJ, 883, 98

(ref: Zhang2020evolution) Zhang, K., Schwarz, K. R., & Bergin, E. A. 2020, ApJL, 891, L17

# Icy dust mass calculation

For our analysis we need a measurement of the amount of dust mass outside the CO snowline, the icy dust mass, using the continuum images presented in Figure [3](#fig:gallery).

![](Gallery.png)

The CO snowline is known to be located at distances corresponding to a range of temperature values between 18 and 25 K based on observations (cite: Pinte2018imlup; Qi2019) and based on laboratory work, is expected to be around 22 K for pure CO ice (cite: Bisschop2006) or as high as 30 K for CO mixed in H$_2$O ice (cite: Noble2012). Exact snowline locations in disks have been attempted to be derived using snowline tracers such as N$_2$H$^+$ and DCO$^+$ but detailed 2D models have shown that their emission is more complex than a simple anti-correlation with CO (cite: Qi2015; vantHoff2017). Therefore, we will adopt the 22 K and 30 K temperatures as the two extremes of the CO snowline location. For the temperature profile we adept the simplified expression of the midplane temperature in a passively heated, flared disk in radiative equilibrium (cite: Chiang1997; Dullemond2001): $$\begin{equation}
\label{eqn:temperature}
T(r) = \Big(\frac{\phi L_*}{8\pi\sigma_Br^2}\Big)^{1/4} 
\end{equation}$$ with $\sigma_B$ the Stefan-Boltzmann constant, $\phi$ the flaring angle (taken as 0.02) and $L_*$ the stellar luminosity. Using this equation, we can deduce the radius $r_{\rm CO}$ where $T$=30/22 K in the midplane. For many of the disks in our sample the CO snowline has been derived directly from the line data: (cite: Zhang2019) derived the snowlines of DM Tau, TW Hya, IM Lup and HD163296 at $\sim$12, 20, 30 and 60 au, respectively, which is consistently further in than the 22 K line from the temperature profile from Eqn. [\[eqn:temperature\]](#eqn:temperature). (cite: Qi2019) derived the CO snowline using detailed modeling of the N$_2$H$^+$ emission profile for DM Tau, LkCa 15 and GM Aur at 75$^{+10}_{-30}$, 58$^{+6}_{-10}$ and 48$^{+10}_{-8}$ au, respectively, and set a limit of $<$33 au for the V4046 Sgr system, the discrepancy for DM Tau may be due to the complex relation between N$_2$H$^+$ and the snowline (cite: vantHoff2017). These values are all located further out than our 22 K line, which is expected as all these disks have large inner cavities where the temperature structure is altered due to the irradiation of the cavity wall (cite: Cleeves2011). For the remaining targets, no CO snowline measurements are available in the literature.

+-----------------+----------------------+-----------------------------------------------+----------------------------------------------------------------------------------+----------+
| Target          | Stellar              | C$_2$H line properties                        | Continuum properties                                                             |          |
+:================+:==============+:=====+:=============+:===================+:==========+:============+:======+:===========+:================+:================+:==========+:=========+
|                 | $L_*$         | $d$  | $F_{integ}$  | $T_{b,peak,100pc}$ | Beam      | $F_{total}$ | $\nu$ | rms        | $M_{\rm d<30K}$ | $M_{\rm d<22K}$ | Beam      | Refs$^b$ |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
|                 | ($L_{\odot}$) | (pc) | (mJy         | (K                 | (")       | (mJy)       | (GHz) | (mJy       | ($M_{\oplus}$)  | ($M_{\oplus}$)  | (")       |          |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
|                 |               |      | km s$^{-1}$) | km s$^{-1}$)       |           |             |       | bm$^{-1}$) |                 |                 |           |          |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 1\. IRS48       | 18            | 135  | $<$11$^a$    | $<$1.1$^a$         | 0.63x0.50 | 173         | 336   | 0.05       | 4.24            | 0.01            | 0.19x0.14 | 1,6      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 2\. Sz68        | 5.5           | 154  | $<$5.3       | $<$7.1             | 0.25x0.21 | 76          | 239   | 0.02       | 0.19            | 0.01            | 0.04x0.03 | 2,7      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 3\. DOTau       | 1.4           | 139  | $<$62        | $<$2.4             | 0.63x0.49 | 120         | 225   | 0.10       | 11.77           | 0.95            | 0.09x0.07 | 3,8      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 4\. J1614-1906  | 0.5           | 143  | $<$100       | $<$5.3             | 0.56x0.45 | 20          | 239   | 0.04       | 3.62            | 2.60            | 0.22x0.20 | 3,9      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 5\. J1612-1859  | 0.3           | 139  | $<$97        | $<$3.6             | 0.56x0.45 | 5.7         | 341   | 0.26       | 0.42            | 0.33            | 0.33x0.30 | 3,10     |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 6\. J16070384   | 0.25          | 150  | $<$16        | $<$24              | 0.25x0.21 | 0.5         | 225   | 0.04       | 0.11            | 0.10            | 0.13x0.12 | 2,11     |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 7\. MWC480      | 18.6          | 162  | 1846         | 97                 | 0.73x0.47 | 264         | 225   | 0.06       | 20.0            | 1.7             | 0.17x0.11 | 3,8      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 8\. HD163296    | 17            | 101  | 4396         | 41                 | 0.55x0.47 | 634         | 239   | 0.02       | 24.1            | 1.1             | 0.05x0.04 | 3,7      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 9\. HD143006    | 3.8           | 165  | 435          | 20                 | 0.58x0.46 | 57          | 239   | 0.01       | 14.6            | 7.0             | 0.05x0.04 | 3,7      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 10\. IMLup      | 2.6           | 158  | 1450         | 18                 | 0.56x0.55 | 209         | 239   | 0.01       | 40.8            | 34.0            | 0.04x0.04 | 3,7      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 11\. Sz98       | 1.53          | 156  | 1101         | 51                 | 0.22x0.17 | 104         | 255   | 0.08       | 24.3            | 20.0            | 0.20x0.13 | 2,2      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 12\. AS209      | 1.4           | 121  | 2709         | 52                 | 0.65x0.55 | 233         | 239   | 0.02       | 30.6            | 21.9            | 0.04x0.04 | 3,7      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 13\. CITau      | 0.9           | 159  | 1041         | 59                 | 0.59x0.49 | 128         | 225   | 0.06       | 31.6            | 28.2            | 0.13x0.11 | 3,8      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 14\. MYLup      | 0.87          | 157  | 284          | 27                 | 0.22x0.17 | 78          | 239   | 0.02       | 18.4            | 14.9            | 0.04x0.04 | 2,7      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 15\. J1609-1908 | 0.4           | 138  | 563          | 56                 | 0.56x0.45 | 22          | 239   | 0.04       | 3.82            | 2.98            | 0.22x0.20 | 3,9      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 16\. Sz71       | 0.33          | 156  | 1101         | 71                 | 0.23x0.17 | 83          | 239   | 0.02       | 19.1            | 16.9            | 0.04x0.04 | 2,7      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 17\. TWHya      | 0.3           | 60   | 10720$^a$    | 15$^a$             | 0.48x0.39 | 1380        | 346   | 0.03       | 19.2            | 16.3            | 0.03x0.03 | 4,12     |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 18\. Sz114      | 0.2           | 162  | 383          | 57                 | 0.22x0.17 | 48          | 239   | 0.02       | 11.5            | 9.7             | 0.07x0.03 | 2,7      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 19\. LkCa15     | 1.3           | 159  | 2435         | 62                 | 0.59x0.49 | 229         | 341   | 0.02       | 24.1            | 24.1            | 0.05x0.03 | 3,13     |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 20\. V4046Sgr   | 0.86          | 72   | 2962         | 4.8                | 0.97x0.70 | 251         | 239   | 0.05       | 13.0            | 10.5            | 0.06x0.04 | 3,6      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 21\. J1604-2130 | 0.7           | 150  | 2632         | 52                 | 0.56x0.45 | 258         | 350   | 0.18       | 24.2            | 24.2            | 0.23x0.20 | 3,6      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 22\. Sz129      | 0.44          | 162  | 107          | 26                 | 0.26x0.21 | 82          | 239   | 0.02       | 20.9            | 17.0            | 0.04x0.03 | 2,7      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 23\. PDS70      | 0.3           | 113  | 1327         | 8.7                | 0.39x0.32 | 159         | 351   | 0.03       | 8.5             | 8.5             | 0.07x0.05 | 5,7      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 24\. DMTau      | 0.24          | 145  | 2013         | 43                 | 0.57x0.49 | 56          | 225   | 0.01       | 12.0            | 12.0            | 0.03x0.02 | 3,7      |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 25\. J16070854  | 0.18          | 176  | 647          | 62                 | 0.22x0.17 | 33          | 225   | 0.11       | 10.8            | 10.6            | 0.22x0.21 | 2,11     |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+
| 26\. J16090141  | 0.15          | 164  | 200          | 37                 | 0.25x0.21 | 7.6         | 225   | 0.02       | 2.1             | 2.1             | 0.04x0.03 | 2,14     |
+-----------------+---------------+------+--------------+--------------------+-----------+-------------+-------+------------+-----------------+-----------------+-----------+----------+

\
$^a$ C$_2$H $N=4-3$, $J=7/2-5/2$ doublet at 349.4 GHz rather than the $N=3-2$, $J=7/2-5/2$ doublet at 262.006 GHz.\
$^b$ References for the C$_2$H data (first) and for the continuum data (second).\
**Refs.** 1) This work; 2) (cite: Miotello2019); 3) (cite: Bergner2019); 4) (cite: Bergin2016); 5) (cite: Facchini2021); 6) (cite: Francis2020); 7) (cite: Andrews2018); 8) (cite: Long2019); 9) ALMA archival data 2017.1.01167.S; 10) (cite: Barenfeld2016); 11) (cite: Ansdell2018); 12) (cite: Andrews2016); 13) (cite: Facchini2020); 14) van der Marel et al. in prep.

Figure [4](#fig:profiles) shows the normalized azimuthally averaged profiles of the dust continuum, with overlaid the temperature profile from Eqn. [\[eqn:temperature\]](#eqn:temperature) and the corresponding 22-30 K range (expected CO snowline location), plus the CO snowline derived directly, where available.

The continuum flux is computed by integrating the flux density over all pixels$>3\sigma$ outside $r_{\rm CO}$, with $\sigma$ the rms noise. The corresponding dust mass is then computed using the standard assumptions of isothermal, optically thin emission of 20 K as demonstrated by (cite: Hildebrand1983) and regularly used in ALMA disk continuum surveys (cite: Ansdell2016): $$\begin{equation}
    M_{\text{dust }}=\frac{F_{\nu,CO} d^{2}}{\kappa_{\nu} B_{\nu}\left(T_{\text{dust}}\right)}
\end{equation}$$ where $B_{\nu}$ is the Planck function for a characteristic dust temperature, $T_{\text{dust}}$, $\kappa_{\nu}$ the dust grain opacity, $d$ the distance to the target in parsecs, and $F_{\nu,CO}$ the millimeter flux outside $r_{\rm CO}$. Due to the lower spatial resolution of J1609-1908, J1612-1859 and J1614-1906, these icy dust masses should be considered upper limits.

![](Profiles.pdf)

# C$_2$H profiles

This section contains the radial profiles of the C$_2$H emission from the zero-moment maps in the literature (cite: Bergin2016; Miotello2019; Bergner2019; Facchini2021).

Although the spatial resolution of the C$_2$H images is limited in current observations (cite: Bergner2019; Miotello2019), the observed ring-like structures in their C$_2$H zero-moment maps and the well-resolved TW Hya disk (cite: Bergin2016) suggest that the C$_2$H emission originates outside the CO snowline (Figure [5](#fig:c2h_miotello) and [6](#fig:c2h_bergner)). Centrally peaked C$_2$H profiles such as seen in e.g. CI Tau, J1609-1908 and LkCa 15 may just be the result of beam confusion and do not prove the presence of C$_2$H inside the CO snowline. The C$_2$H emission extends well beyond the radial dust extent, consistent with a gas disk much larger than a dust disk as icy dust pebbles settle and drift inwards, leaving the outer disk volatile-depleted.

![](Overview_C2H_Miotello_Annadata.pdf)

![](Overview_C2H_Bergner.pdf)

# Data reduction IRS 48 C$_2$H data

(cite: vanderMarel2021-irs48) presents a molecular line survey of Oph IRS 48 from ALMA dataset 2017.1.00834.S for a number of H$_2$CO and CH$_3$OH transitions. The C$_2$H $N=4-3$, $J=7/2-5/2$ doublet at 349.4 GHz is covered in these spectral windows as well, but not reported in this work. Inspection of the dataset reveals that this C$_2$H line is not detected. Considering the reported rms level of 1.2 mJy bm$^{-1}$ channel$^{-1}$ with a channel width of 1.6 km s$^{-1}$, a line width of $\sim$14 km s$^{-1}$ and a beam size of 0.63$\times$0.50" (cite: vanderMarel2021-irs48), we compute a 3$\sigma$ upper limit on the C$_2$H flux density of 11 mJy bm$^{-1}$ km s$^{-1}$, or a scaled $T_{b,peak,100pc}$ limit of $<$1.1 K km s$^{-1}$. Such a low value of C$_2$H is consistent with the low CS/SO ratio reported by (cite: Booth2021-irs48).

# ALMA archival continuum data 2017.1.01167.S

For the continuum analysis of J1614-1906 and J1609-1908 we use ALMA archival data from ALMA Cycle 5 program 2017.1.01167.S (PI Sebastian Perez). These targets were observed in Band 6 for an integration time of 4.5 minutes each on January 18th, 2018. The dataset is reduced using CASA version 5.1.1 with the provided calibration scripts, with J1517-2422 as flux and bandpass calibrator and J1634-2058 as gain calibrator. We use the three continuum spectral windows (the fourth window was centered on the $^{12}$CO 2–1 line) with an average frequency of 240 GHz and a total bandwidth of 6 GHz. The continuum images are imaged using the CASA `tclean` task with uniform weighting, resulting in a beam size of 0.22$\times$0.20 and a rms noise of 0.08 mJy beam$^{-1}$. The total integrated flux is 21 and 17 mJy for J1609-1908 and J1614-1906, respectively. Both disks are marginally resolved and the CASA `uvmodelfit` indicates a radial extent of 0.14" (20 au) and 0.08" (11 au) for J1609 and J1614, respectively. Their disk morphology classification as compact disk is debatable due to the low resolution, and high-resolution imaging is required to properly assess these two disks. The images are presented in Figure [3](#fig:gallery).

[^1]: If some pebbles can filter through the pressure bumps, the direct vicinity of the CO snowline could see high gas-phase CO abundances and C/O$\sim$1.

</paper>

Write the methods card for this paper.