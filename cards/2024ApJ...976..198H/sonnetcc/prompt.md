# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...976..198H\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...976..198H",
 "title": "Whole-disk Sampling of Molecular Clouds in M83",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Hirota, Akihiko",
 "n_authors": 20,
 "arxiv_id": "2410.05424",
 "doi": "10.3847/1538-4357/ad8228",
 "alma_projects_linked_by_archive": [
  "2017.1.00079.S"
 ]
}
```

Paper text:
<paper>
# Whole-disk sampling of molecular clouds in M83

## Abstract

We present a catalog of clouds identified from the $^{12}$CO (1–0) data of M83, which was observed using Atacama Large Millimeter/submillimeter Array (ALMA) with a spatial resolution of $\sim$46 pc and a mass sensitivity of $\sim$10$^4$ ${M}_{\odot}$ (3 $\sigma$). The almost full-disk coverage and high sensitivity of the data allowed us to sample 5724 molecular clouds with a median mass of $\sim1.9$ $\times$ $10^5$ ${M}_{\odot}$, which is comparable to the most frequently sampled mass of Giant Molecular Clouds (GMCs) by surveys in the Milky Way. About 60 percent of the total CO luminosity in M83’s disk arises from clouds more massive than 10$^6$ ${M}_{\odot}$. Such massive clouds comprise 16 percent of the total clouds in number and tend to concentrate toward the arm, bar, and center, while smaller clouds are more prevalent in inter-arm regions. Most $>10^6$ ${M}_{\odot}$ clouds have peak brightness temperatures $T_{\mathrm{peak}}$ above 2 K with the current resolution. Comparing the observed cloud properties with the scaling relations determined by Solomon et al. 1987 (S87), $T_{\mathrm{peak}}$$>2$ K clouds follow the relations, but $T_{\mathrm{peak}}$$<2$ K clouds, which are dominant in number, deviate significantly. Without considering the effect of beam dilution, the deviations would suggest modestly high virial parameters (median ${\alpha_{\mathrm{vir}}}$ $\sim2.7$) and low surface mass densities (median $\Sigma$ $\sim$22 ${M}_{\odot}\ \mathrm{pc}^{-2}$) for the entire cloud samples, which are similar to values found for the Milky Way clouds by Rice et al. (2016) and Miville-Deschênes et al. (2017). However, once beam dilution is taken into account, the observed ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ for a majority of the clouds (mostly $T_{\mathrm{peak}}$ $<2$ K) can be potentially explained with intrinsic $\Sigma$ of $\sim$100 ${M}_{\odot}\ \mathrm{pc}^{-2}$ and ${\alpha_{\mathrm{vir}}}$ of $\sim$1, which are similar to the clouds of S87.

# Introduction

Molecular gas is directly associated with star formation in the nearby universe. The bulk of H$_2$ mass resides in giant molecular clouds (GMCs), which are concentrations of molecular gas with a temperature of around 10 K, diameter of 10 pc to 100 pc, and mass of 10$^{5-6}$ ${M}_{\odot}$ (cite: Sanders1985) [^1]. The efficiency of star formation in GMCs is determined by the complex interplay among many processes, including self-gravity, turbulence, stellar feedback, and magnetic fields, although the exact balance is still not certain. Characterizing GMCs’ properties and their relations is vital in reaching a coherent understanding of star formation in galaxies.

The conventional view of GMCs was mainly established by the early CO studies of Galactic molecular clouds about four decades ago. At that time, GMCs were mainly identified as discrete emission features in the Galactic plane (cite: Sanders1985). The early studies empirically established the scaling relations of cloud properties (cite: Larson1981; Solomon1987Larson) and also found a power-law GMC mass function (cite: Sanders1985; ScovilleSanders1987). In particular, the three relations determined by S87, namely the scaling relations of linewidth and size ${\Delta}{V}$ $\propto$ $S^{\sim0.5}$, virial mass and CO luminosity ${M}_{\mathrm{vir}}$ $\propto$ ${L}_{\mathrm{CO}}$$^{\sim0.8}$, and volume density and size $\rho$ $\propto$ $S^{-1}$, are often used as a benchmark in most subsequent studies of GMCs. Assuming that clouds are approximately in virial equilibrium, the near-linear ${M}_{\mathrm{vir}}$-${L}_{\mathrm{CO}}$ relation (2nd relation) yields a constant CO-to-H$_2$ conversion factor of $X_{\mathrm CO} \sim$2 $\times$ 10$^{20}$ cm$^{-2}\ (\mathrm{K}\ \mathrm{km\ s}^{-1})^{-1}$ for a typical Galactic GMC, which agrees with the ‘standard’ conversion factor often adopted today in metal-rich environments (cite: Bolatto2013ConversionFactor). Using the constant conversion factor, the 3rd relation suggests that the surface mass densities of GMCs are nearly constant around 200${M}_{\odot}\ \mathrm{pc}^{-2}$, which is often taken as a typical surface density in GMCs.

Subsequent studies explored the cloud properties in diverse environments, including the outer Galaxy (cite: Heyer2001OuterGalaxy), Galactic center (cite: Oka2001), and extragalactic environments (cite: Engargiola2003; Rosolowsky2005; Bolatto2008GMCs; DonovanMeyer2013; Colombo2014Env; Freeman2017; Hirota2018M83; Maeda2020NGC1300; Rosolowsky2021PhangsGMCs; Muraoka2023M33). Several studies revisited GMCs also in the inner Galactic disk with new $^{13}$CO survey data (cite: RomanDuval2010) and with a more complete coverage albeit at lower spatial resolution (cite: Rice2016; MivilleDeschenes2017MWGMC). Some confirmed the S87 relations in the inner Galactic disk (cite: RomanDuval2010) and in external galaxies (cite: Bolatto2008GMCs), but others found deviations in two aspects.

First, despite the near virial balance suggested for S87’s clouds, recent studies report a variety of dynamical stability in clouds. In the Galactic center (cite: Oka2001) and outer Galactic disk (cite: Heyer2009), many clouds appear unbound if the $X_{\rm CO}$ in the inner disk is applied. These analyses often adopt the virial parameter (cite: BertoldiMcKee1992), the ratio of kinetic to gravitational energies of clouds, and find ${\alpha_{\mathrm{vir}}}\gg$1-2 for the unbound clouds. Even in the inner Galactic disk, (cite: MivilleDeschenes2017MWGMC) suggests that only 15 percent of the clouds might be bound, although bound clouds account for 40 percent of the total molecular gas mass. In addition, recent extragalactic studies found a large scatter in ${\alpha_{\mathrm{vir}}}$ with an average value of $\sim$2 in disk regions (cite: Sun2020; Rosolowsky2021PhangsGMCs), which suggested a modestly gravitationally-bound state, but not in the virial equilibrium. (cite: Evans2021BoundCloud) found that, in general, only 20 to 40 percent of the cloud masses are bound by compiling cloud catalogs both in Galactic and extragalactic environments.

Secondly, the near constant $\Sigma$ of around 200 ${M}_{\odot}\ \mathrm{pc}^{-2}$ is also revisited by recent studies. $\Sigma$ appears to show considerable variations, with a low median value of a few $\times$ 10 ${M}_{\odot}\ \mathrm{pc}^{-2}$ in the recent Galactic plane study (cite: MivilleDeschenes2017MWGMC) and in the outer Galactic disk survey (cite: Heyer2001OuterGalaxy) but high $\Sigma$, reaching up to 1000 ${M}_{\odot}\ \mathrm{pc}^{-2}$ or higher, in galactic centers (cite: Oka2001; Leroy2015NGC253).

The large variations in ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ seen in recent studies, along with predictions from numerical simulations (cite: DobbsPringle2013; Smith2020CloudFactory), potentially require a refinement of the view of GMCs: GMCs could be modestly bound by self-gravity and are relatively transient objects, which might be prone to be dispersed by large-scale shear motions and stellar feedback (cite: Dobbs2011NotBound; Chevance2023Review).

Extragalactic studies of molecular clouds provided essential contributions to this refinement of the view of molecular clouds. However, most extragalactic studies were limited by low spatial resolutions of $>$ 50 pc to 100 pc (cite: Colombo2014Env; Hirota2018M83), even in the recent PHANGS survey (cite: Rosolowsky2021PhangsGMCs). These extragalactic ’disk’ surveys mostly achieved mass completeness limits of around 10$^6$ ${M}_{\odot}$ or more, while most of the inner Galactic disk surveys were made the completeness limit of 1–3 $\times$ 10$^5$ ${M}_{\odot}$ (cite: Sanders1985; Solomon1987Larson; ScovilleSanders1987; RomanDuval2010; Rice2016; MivilleDeschenes2017MWGMC). To build a more accurate and comprehensive view, we need a higher sensitivity and resolution to characterize the cloud properties and distribution over a wide range of cloud masses and to elucidate their environmental dependence.

Recently, the full extent of the molecular disk of the nearby galaxy M83 was observed in $^{12}$CO (1–0) using ALMA (cite: Koda2023M83). The mass sensitivity, $\sim 10^4$ ${M}_{\odot}$, is unprecedented for such a full-disk mapping of substantial spiral galaxies. M83 closely resembles the Milky Way galaxy in morphology (including the bar, spiral arms, and even interarm structures), as well as in its size, gas and stellar masses, and near Solar metallicity (cite: Koda2023M83). This study identifies molecular clouds from the $^{12}$CO data to examine the cloud properties, distributions, scaling relations, and mass distributions.

We organize this paper as follows. In §[2](#SecIdentify), we describe the data and procedure to catalog molecular clouds. In §[3](#SecResults), we present their properties, scaling relations, and spatial distribution. We examine the cloud mass function in §[4](#SecMF) and estimate the vertical cloud-to-cloud velocity dispersions in §[5](#SecVelDisp). In §[6](#SecDiscussion), we discuss the impact of beam-dilution (beam filling factor) on the cloud parameters, in particular on ${\alpha_{\mathrm{vir}}}$ and $\Sigma$, and discuss its implications to our view of molecular clouds. In §[7](#SecSummary), we present the conclusions.

# Molecular Cloud Identification

## Data

We used the $^{12}$CO (J=1–0) mapping data of M83 observed with ALMA (cite: Koda2023M83). The observations used the main 12-m array and Atacama Compact Array (ACA), i.e., the 7-m short-baseline interferometric array and the Total-Power (TP) single-dish array, to recover the flux. The interferometric and single-dish data were calibrated separately. The calibration procedure is described in (cite: Koda2023M83). The calibrated TP array data was converted into interferometric visibilities using the TP2VIS software (cite: Koda2019TP2VIS). Then, the 12-m, 7-m, and TP array visibilities were inverted onto the image plane and jointly deconvolved using the MIRIAD software package (cite: SaultTeubenWright1995MIRIAD). We refer the readers to (cite: Koda2023M83) for further details on the data processing.

Three data cubes were prepared in (cite: Koda2023M83) with velocity resolutions of 1, 2, and 5 $\mathrm{km\ s}^{-1}$, respectively. We here adopt the one with 1 $\mathrm{km\ s}^{-1}$ resolution. The restoring beam of the original data is a Gaussian with major and minor axes of 2$\ensuremath{''}$.09 $\times$ 1$\ensuremath{''}$.68 in full-width half maximum (FWHM), which corresponds to 45.6 pc $\times$ 36.7 pc at the assumed distance of M83 (cite: Thim2003M83Distance). To avoid complexities associated with the non-circular beam, we smoothed the original data cube in spatial directions to achieve a circular beam with an FWHM size of 2$\ensuremath{''}$.1, corresponding to $\sim$46 pc.

Figure [1](#FigRMSMap)(a) shows the two-dimensional map of the root-mean-square (rms) noise level. We adopted the following procedure to obtain a noise-free estimate of the noise distribution. First, we used MIRIAD’s *mossen* command to generate a two-dimensional noise distribution expected from the integration time and system noise temperature assigned to visibilities. Next, the ’expected’ noise map produced by *mossen* was compared with the ’measured’ noise map, which we made by measuring rms noise along the velocity axis at each position in the data cube. The comparison confirmed that both maps are consistent regarding the relative spatial variation within each map but are discrepant in the absolute scaling by a few tens of percent. Therefore, as the final step, we scaled the ’expected’ map so that the median noise level matches that of the ’measured’ noise map. The median noise level across the observed field is 6.5 mJy per beam.

## Cloud identification

We here describe our procedures to identify molecular clouds in the $^{12}$CO (1–0) data cube.

As a preparatory step, we constructed a signal mask to isolate voxels with significant detection. The mask was created by first identifying a set of regions that consist of voxels with SNR $\ge$ 4, then discarding small regions whose spatial extents are less than 0.6 times the beam area or whose emissions are confined in a single $1\,\rm km\,s^{-1}$ channel along the velocity axis, and finally expanding the remaining regions to include the morphologically connected surrounding voxels with SNR $\ge$ 2.

The masked data cube was decomposed into a set of independent closed surfaces using the *astrodendro*[^2] software package. Although *astrodendro* identifies hierarchically nested sets of structures, we adopted only the structures at the finest spatial scales, commonly referred to as *leaves*. This is because the utilized spatial resolution, $\sim$46 pc at FWHM, is only a factor of two smaller than the typical height of the thin molecular gas disk (cite: HeyerDame2015Review). As long as the disk height is similar between M83 and Milky Way and the size of the largest cloud is limited by the disk height, examining structures larger than individual leaves is unnecessary. Parameters for the cloud decomposition algorithm are configured such that only voxels with SNR $>2$ are included in the analysis, and *leaf* candidates with SNR contrasts between their peak and edge-level $<2$ are discarded. In addition, to avoid picking up noise fluctuations as clouds, we discarded small *leaves* with the number of voxels less than $A_{\mathrm{beam}}/A_{\mathrm{voxel}}$, where $A_{\mathrm{beam}}$ and $A_{\mathrm{voxel}}$ are the area of the beam and a voxel.

The identified *leaves* generally trace the small regions around the peaks of molecular clouds, especially in crowded areas, because by nature of the algorithm, the leaves are defined such that they do not overlap each other. The *astrodendro* decomposition left about 80% of the CO emission unassigned to any *leaves*. The unassigned voxels to any seed structures are further segmented with the watershed algorithm, using the *scikit-image* software package (cite: vanDerWalt2014ScikitImage).

5724 leaves, which are expanded by the watershed segmentation, are accepted as molecular clouds About 91 percent of the total CO luminosity within the mapped area was sampled as molecular clouds, as we will see later in §[2.6](#SubsecCOLumFraction).

## Derivation of cloud properties

The physical properties of the identified clouds are calculated in a way similar to the one adopted in (cite: Hirota2018M83). A brief description is provided here.

### Measured properties

Each cloud’s centroid position and velocity are measured as the intensity-weighted first moments. We record the maximum brightness temperature within the cloud as peak temperature $T_{\mathrm{peak}}$. The size parameters in two dimensions and velocity dispersion of each cloud are calculated as second moments and then extrapolated to the 0 K level with the procedure of (cite: Rosolowsky2006CPROPS). Hereafter, we denote the extrapolated moment values as $\sigma_{\mathrm{x,r}}$, $\sigma_{\mathrm{y,r}}$, and $\sigma_{\mathrm{v,r}}$, where $\sigma_{\mathrm{x,r}}$ $>$ $\sigma_{\mathrm{y,r}}$. The CO luminosity for each cloud (${L}_{\mathrm{CO}}$) is derived as a summation in each cloud boundary and extrapolated to 0 K level. We estimated the uncertainty in $\sigma_{\mathrm{x,r}}$, $\sigma_{\mathrm{y,r}}$, and $\sigma_{\mathrm{v,r}}$ by performing a bootstrap error estimation with 1000 trials.

### Derived properties

We derived the physical parameters of the clouds from the directly measured parameters presented above.

*Effective radius:* Effective radius of the cloud ($R_{\mathrm{eff}}$) is derived as $$\begin{equation}
R_{\mathrm{eff}}= \frac{3.4}{\sqrt{\pi}} \sqrt{\sigma_{\mathrm{x}}\sigma_{\mathrm{y}}}
\end{equation}$$ where $3.4 / \sqrt\pi$ ($\sim1.91$) is an empirical factor that is determined by S87, and $\sigma_{\mathrm{x}}$ and $\sigma_{\mathrm{y}}$ are the deconvolved cloud sizes defined below. We note that although this definition of $R_{\mathrm{eff}}$ is long used as common custom, some of the recent studies also define cloud radius as half width half maximum, $R_{\mathrm{HWHM}}$ = 1.18 $\sqrt{\sigma_{\mathrm{x}}\sigma_{\mathrm{y}}}$ (cite: Rosolowsky2021PhangsGMCs), and thus care is needed when comparing values.

The deconvolved sizes are obtained by subtracting the beam size in quadrature from the extrapolated cloud sizes of $\sigma_{\mathrm{x,r}}$ and $\sigma_{\mathrm{y,r}}$ as $$\begin{eqnarray}
\sigma_{\mathrm{x}}&=& \sqrt{\sigma_{\mathrm{x,r}}^2 - \theta_{\mathrm{b}}^2 / \left( 8 \log{2} \right)}\\
\sigma_{\mathrm{y}}&=& \sqrt{\sigma_{\mathrm{y,r}}^2 - \theta_{\mathrm{b}}^2 / \left( 8 \log{2} \right)}
\label{EqReffCorrection}
\end{eqnarray}$$ where $\theta_{\mathrm{b}}$ is the FWHM resolution of the data (2$\ensuremath{''}$.1 , $\sim$46 pc). Out of the 5724 clouds identified, 225 clouds have $\sigma_{\mathrm{y,r}}$ smaller than $\theta_{\mathrm{b}} / \sqrt{8 \log{2}}$. We marked them as “deconvolution-failed clouds" and assigned $\sigma_{\mathrm{x,r}}$ and $\sigma_{\mathrm{y,r}}$ as the upper limits on $\sigma_{\mathrm{x}}$ and $\sigma_{\mathrm{y}}$, respectively.

*Velocity dispersion:* The velocity dispersion of the cloud ($\sigma_{\mathrm{v}}$) is calculated by subtracting the instrumental velocity resolution from the extrapolated $\sigma_{\mathrm{v,r}}$ as $$\begin{equation}
\sigma_{\mathrm{v}}= \sqrt{ \sigma_{\mathrm{v,r}}^2 - \left( \Delta{V}_{\mathrm{ch}} / \sqrt{12} \right)^2 },
\end{equation}$$ where $\Delta{V}_{\mathrm{ch}}$ is the channel width of the data (1 $\mathrm{km\ s}^{-1}$). The factor of $1/\sqrt{12}$ is the ratio of the 2nd moment to the width for a boxcar profile.

*Molecular gas mass:* Molecular gas mass for each GMC (${M}_{\mathrm{cl}}$) is calculated from ${L}_{\mathrm{CO}}$ by applying a CO-to-H$_{2}$ conversion factor of 2.0 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ in combination with a correction factor of 1.36 that accounts for the contribution of Helium and other elements. (cite: Bolatto2013ConversionFactor): $$\begin{equation}
\label{EqLCOtoMsun}
\left(\frac{{M}_{\mathrm{cl}}}{ {M}_{\odot} }\right) =
\left(\frac{{\alpha_{\mathrm{CO}}}}{4.4  {M}_{\odot} / \left( \mathrm{K}\ \mathrm{km\ s}^{-1}\mathrm{pc}^2 \right) }\right)
\left(\frac{{L}_{\mathrm{CO}}}{\mathrm{K}\ \mathrm{km\ s}^{-1}\ \mathrm{pc}^{2}}\right),
\end{equation}$$ where ${\alpha_{\mathrm{CO}}}$ is the mass-to-luminosity ratio. The ${\alpha_{\mathrm{CO}}}$ of 4.4 ${M}_{\odot}$ $\left( \mathrm{K}\ \mathrm{km\ s}^{-1}\mathrm{pc}^2 \right)$ is often regarded as the ‘standard’ value for GMCs in metal-rich environments, such as in M83’s inner disk (cite: Bresolin2016), and thus the use of the ‘standard’ conversion factor is justified as the first order approximation (cite: Bolatto2013ConversionFactor). We note that, however, (cite: Lee2024M83) suggested a kpc-scale radial variation in ${\alpha_{\mathrm{CO}}}$, which is a factor of a few increase from the galactocentric radius of $\sim2$ kpc to $\sim$6 kpc. (cite: Lee2024M83) noted that the radial gradient of metallicity in the disk of M83 is insufficient to explain the observed variation in ${\alpha_{\mathrm{CO}}}$ as it can only produce a factor of $\sim1.2$ to $\sim1.3$ variations in ${\alpha_{\mathrm{CO}}}$ over the corresponding radial range by adopting the metallicity measurement of (cite: Bresolin2016) and the metallicity-dependent descriptions of ${\alpha_{\mathrm{CO}}}$ of (cite: Wilson1995Xco) and (cite: Arimoto1996). They suggested that the weak dependence of ${\alpha_{\mathrm{CO}}}$ on ${L}_{\mathrm{CO}}$, expected for gravitationally bound clouds with constant surface densities (cite: Solomon1987Larson; Bolatto2013ConversionFactor), combined with the radial variation in the cloud mass function can provide a relative variation in ${\alpha_{\mathrm{CO}}}$ comparable to the observed variation.

*Surface density:* Average gas surface density of a cloud ($\Sigma$) is calculated as, $$\begin{equation}
\Sigma= {M}_{\mathrm{cl}}/ (\pi R_{\mathrm{eff}}^2).
\label{EqSigmaDef}
\end{equation}$$

*Virial mass:* Following (cite: BertoldiMcKee1992) virial mass is calculated as $$\begin{equation}
{M}_{\mathrm{vir}}= \frac{1}{a_1} \frac{5 R \sigma_{\mathrm{v}}^2}{G},
\label{EqMVirDef}
\end{equation}$$ where $G$ is the gravitational constant and $a_1$ is a geometrical factor that is (1 - $k$/3) / (1 - 2$k$/5) for a power law density distribution of $\rho(r)$ $\propto$ $r^{-k}$. We assumed $k$ to be 1, following S87. Examinations of the nearby Galactic clouds suggest slightly larger values of $k$ (cite: Kauffmann2010RelationII; Lombardi2010). As the dependence of the geometrical factor $a_1$ on k is small, we adopt $k$=1 to keep consistency with previous studies.

*Virial parameter:* The virial parameter ${\alpha_{\mathrm{vir}}}$ is a ratio between the virial mass and gas mass and is a measure of the ratio of the kinetic to gravitational energy (cite: BertoldiMcKee1992): $$\begin{equation}
{\alpha_{\mathrm{vir}}}\equiv {M}_{\mathrm{vir}}/ {M}_{\mathrm{cl}}.
\label{EqAlphaVirDef}
\end{equation}$$ Ignoring the support from external pressure and magnetic fields, a state of simple virial equilibrium is achieved when ${\alpha_{\mathrm{vir}}}$ is 1 or a factor of few around 1, considering the uncertainty in the assumed density profile and CO-to-H$_2$ conversion factor. Clouds are loosely bound when the equipartition between the kinetic and gravitational energy is achieved with ${\alpha_{\mathrm{vir}}}$ $\sim$2 (cite: Larson1981; BallesterosParedes2011A). We note a general caveat on interpreting ${\alpha_{\mathrm{vir}}}$. As isolated clouds with simple geometry and density distribution are assumed, the observationally derived ${\alpha_{\mathrm{vir}}}$ has a limitation in characterizing the dynamical status of molecular clouds. Numerical simulations suggest that clouds could be either more bound (cite: BallesterosParedes2018; RamirezGaleano2022) or more unbound (cite: Mao2020CloudProps) than what the face value of ${\alpha_{\mathrm{vir}}}$ would suggest.

## Extrapolation factors and measurement uncertainties

The extrapolation to 0 K emission level made to basic cloud parameters §[2.3.1](#SubsecBasicProps) is needed to correct for the underestimation of the parameters that would arise if the parameters are determined at a higher edge level (cite: Rosolowsky2006CPROPS). However, the extrapolation result becomes less reliable for a cloud that requires a higher correction factor. Thus, we expect clouds with higher correction factors to have higher measurement uncertainties assigned by the bootstrap estimate. We show the amount of correction and measurement uncertainties to the clouds here.

Figure [2](#FigCorrectionFactors)(a-c) shows the correction factor of the extrapolation, which is the ratio between the extrapolated to un-extrapolated values for CO luminosity, radius, and the velocity dispersion of the clouds, plotted as functions of the cloud mass. The correction factors tend to increase toward lower cloud masses. At a mass of 2 $\times$ 10$^5$ ${M}_{\odot}$, the median of the correction factors are about 1.25, 1.16, and 1.12 for luminosity, radius, and velocity dispersion, respectively, and are modest. At the lowest mass bin of 2 $\times$ 10$^4$ ${M}_{\odot}$, the median factors are 1.96, 1.43, and 1.41, respectively.

Figure [2](#FigCorrectionFactors)(d-f) shows the measurement errors in CO luminosity, radius, and velocity dispersion expressed in the fractional form. Uncertainties in these basic three quantities are transferred to other advanced quantities following uncertainty propagation.

## GMC Catalog

Table [\[TableCatalog\]](#TableCatalog) lists the first several entries of the compiled catalog. The complete list shall be available as an electronic table. Each line in the catalog reports the parameter of an identified cloud, including the centroid position and receding velocity, $R_{\mathrm{eff}}$, the axial ratio ($\sigma_{\mathrm{y}}$/$\sigma_{\mathrm{x}}$) and position angle, $\sigma_{\mathrm{v}}$, ${L}_{\mathrm{CO}}$, ${M}_{\mathrm{vir}}$, and the binary flag that indicates whether the deconvolution failed for the cloud or not.

|  |  |  |  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|:---|
| R.A. | Decl. | $V_{\mathrm{LSR}}$ | $T_{\mathrm{peak}}$ | $R_{\mathrm{eff}}$ | $\sigma_{\mathrm{y}}/\sigma_{\mathrm{x}}$ | $P.A.$ | $\sigma_{\mathrm{v}}$ | $L_{\mathrm{CO}}$ | $M_{\mathrm{vir}}$ | deconv. flag |
|  |  | (km s$^{-1}$) | \(K\) | (pc) |  | (deg) | (km s$^{-1}$) | ($10^4$ K km s$^{-1}$ pc$^{2}$) | ($10^5$ M$_{\odot}$) |  |
| 13:37:00.310 | -29:51:52.41 | 542.6 | 17.39 | 66 | 0.51 | -157 | 13 | 640 | 110 | 0 |
| 13:37:00.755 | -29:52:07.75 | 510.9 | 16.68 | 86 | 0.78 | -122 | 22 | 1300 | 420 | 0 |
| 13:37:00.400 | -29:51:50.07 | 514.9 | 15.74 | 58 | 0.65 | -149 | 7.0 | 320 | 30 | 0 |
| 13:37:00.435 | -29:51:49.76 | 489.4 | 13.66 | 47 | 0.83 | -167 | 9.3 | 300 | 43 | 0 |
| 13:37:00.762 | -29:51:43.94 | 499.3 | 13.43 | 94 | 0.79 | -150 | 16 | 1200 | 240 | 0 |
| 13:37:00.610 | -29:51:54.27 | 481.9 | 12.91 | 57 | 0.52 | -59 | 11 | 370 | 75 | 0 |
| 13:37:00.334 | -29:51:58.93 | 564.5 | 12.32 | 74 | 0.68 | -182 | 11 | 240 | 91 | 0 |
| $\vdots$ | $\vdots$ | $\vdots$ | $\vdots$ | $\vdots$ | $\vdots$ | $\vdots$ | $\vdots$ | $\vdots$ | $\vdots$ | $\vdots$ |

: Catalog of clouds in M83

Table notes: Parameters of the identified cloud. (1) Right ascension. (2) Declination. (3) Centroid velocity. (4) Peak brightness temperature. (5) Effective radius. (6) Ratio between the minor and major axes lengths. (7) Position angle of the major axis of the cloud, measured from the North. (8) Velocity dispersion. (9) CO (1–0) luminosity. (10) Virial mass. (11) Flag indicating whether the deconvolution was successfully made (=0) or not (=1).

## Fraction of CO luminosity sampled as GMC

Table [\[TblGlobalProps\]](#TblGlobalProps) lists the total CO luminosity ${L}_{\mathrm{CO}}$ along with the fractional CO luminosities included within the signal mask ($f_{\mathrm{mask}}$) and sampled as molecular clouds ($f_{\mathrm{cl}}$). To indicate their overall radial trends, we list the values for five radial bins separated at galactocentric radii shown in figure [1](#FigRMSMap)(b). The $f_{\mathrm{mask}}$ is highest in the innermost radial bin ($\sim$97 percent) and decreases with increasing galactocentric radius to $\sim$68% in the outermost radial bin. This radially declining trend suggests that the contribution of lower mass clouds to total mass becomes increasingly significant at larger galactocentric radii.

The extrapolation process recovers part of the emission removed by applying the signal mask. Reflecting this, $f_{\mathrm{cl}}$ is higher than $f_{\mathrm{mask}}$ in all the radii. However, in the central 550 pc, $f_{\mathrm{cl}}$ slightly exceeds 1 (1.04 $\pm$ 0.03), which indicates that the flux extrapolation is over-correcting the cloud flux by a few percent. A radially declining trend of $f_{\mathrm{cl}}$ exists. It is nearly 100 percent within the central 3.1 kpc. It decreases radially down to $\sim$80% in the outermost radial bin, suggesting an increased fraction of clouds below the detection limit.

We estimate the detectable minimum cloud mass that is based on the observation and segmentation parameters. The cloud identification process in (§[2.2](#SubsecIdentify)) set the peak SNR threshold as 4, which corresponds to a brightness temperature limit of $\sim$0.5 K. Assuming that the minimum cloud has an area equivalent to the beam area and that the cloud emission has a Gaussian profile with $\sigma_{\mathrm{v}}$ of 2 $\mathrm{km\ s}^{-1}$ and $T_{\mathrm{peak}}$ of 0.5 K, the mass of the cloud is ${\alpha_{\mathrm{CO}}}\left(2 \pi \right)^{1/2} T_{\mathrm{peak}}\sigma_{\mathrm{v}}\left(1.13 \theta_{\mathrm{b}}^2 \right)$. With the assumed ${\alpha_{\mathrm{CO}}}$ of 4.4 ${M}_{\odot}$ / (K $\mathrm{km\ s}^{-1}$ pc$^2$) and $\theta_{\mathrm{b}}$ of 46 pc, the expected minimum cloud mass would be $\sim3 \times 10^{4}$ ${M}_{\odot}$. We note that this value is for clouds that exist in isolated areas, and the mass completeness limit is elevated in crowded regions.

|  |  |  |  |
|:---|:--:|:--:|:--:|
| Radial range | ${L}_{\mathrm{CO}}$ | $f^{\mathrm{mask}}$ | $f^{\mathrm{cl}}$ |
| (kpc) | (10$^7$ K km s$^{-1}$ pc$^2$) |  |  |
| All | 82.7 $\pm$ 0.17 | 0.85 | 0.93 $\pm$ 0.05 |
| 0.00 - 0.55 | 12.6 $\pm$ 0.01 | 0.98 | 1.04 $\pm$ 0.03 |
| 0.55 - 2.18 | 18.6 $\pm$ 0.05 | 0.90 | 1.00 $\pm$ 0.05 |
| 2.18 - 3.05 | 17.7 $\pm$ 0.05 | 0.90 | 0.97 $\pm$ 0.05 |
| 3.05 - 4.58 | 17.3 $\pm$ 0.08 | 0.79 | 0.86 $\pm$ 0.05 |
| 4.58 - 6.11 | 14.4 $\pm$ 0.10 | 0.73 | 0.83 $\pm$ 0.06 |

: Global CO luminosity and GMC mass in M83

Table notes: (1) Radial range. Locations of the boundary radii are shown in figure [1](#FigRMSMap)(b). (2) CO luminosity. (3) Fractional CO luminosity within the signal mask. (4) Fractional CO luminosity sampled as clouds.

# Results

## Distribution of Cloud Properties

Figure [3](#FigCloudPropHistograms) shows the distributions of the molecular cloud properties, including mass (${M}_{\mathrm{cl}}$), peak temperature ($T_{\mathrm{peak}}$), velocity dispersion $\sigma_{\mathrm{v}}$, radius ($R_{\mathrm{eff}}$), surface density ($\Sigma$), and virial parameter (${\alpha_{\mathrm{vir}}}$). Each cloud property is displayed in unweighted and mass-weighted histograms. The top panels for each parameter show unweighted histograms for all the clouds (black line), clouds with masses above 10$^6$ ${M}_{\odot}$ (blue line), those with masses between 10$^5$ and 10$^6$ ${M}_{\odot}$ (green line), and those for which the deconvolution failed to determine their sizes (dashed line). The median with 16-to-84 percentile ranges for the first three categories are displayed using markers and horizontal error bars. The bottom panels for each parameter display the mass-weighted histogram with the mass-weighted medians and horizontal bars for the 16 and 84 percentiles. Table [\[TableClProps\]](#TableClProps) lists the summary of the measurements.

lccccccc & $T_{\mathrm{peak}}$ & $\sigma_{\mathrm{v}}$ & $R_{\mathrm{eff}}$ & $M_{\mathrm{cl}}$ & $\Sigma$ & $\alpha_{\mathrm{vir}}$ & $N_{\mathrm{cl}}$\
& ($K$) & (km s$^{-1}$) & (pc) & ($10^5_{\odot}$) & ($M_{\odot}$ pc$^{-2}$) & &\
4cUn-weighted percentiles\
All & $1.1_{0.7}^{2.4}$ & $3.3_{1.8}^{4.9}$ & $59_{41}^{86}$ & $1.9_{0.51}^{8.1}$ & $22_{5.8}^{100}$ & $3.0_{1.0}^{7.0}$ & $5724$\
$>$10$^6$ M$\odot$ & $3.5_{2.5}^{5.2}$ & $5.3_{4.2}^{7.0}$ & $69_{54}^{89}$ & $18_{12}^{38}$ & $130_{75}^{280}$ & $1.0_{0.6}^{2.0}$ & $734$\
$>$10$^5$ M$\odot$ & $1.4_{0.91}^{2.1}$ & $3.6_{2.7}^{4.8}$ & $59_{42}^{83}$ & $2.6_{1.4}^{5.9}$ & $27_{10.0}^{68}$ & $3.0_{1.0}^{6.0}$ & $3124$\
4cWeighted percentiles\
All & $3.4_{1.5}^{7.6}$ & $5.4_{3.6}^{9.2}$ & $70_{51}^{94}$ & $18_{3.8}^{110}$ & $130_{35}^{520}$ & $1.0_{0.6}^{3.0}$ & $5724$\
$>$10$^6$ M$\odot$ & $4.7_{3.0}^{9.3}$ & $6.5_{4.8}^{11}$ & $78_{58}^{96}$ & $37_{15}^{160}$ & $230_{99}^{870}$ & $0.8_{0.5}^{1.0}$ & $734$\
$>$10$^5$ M$\odot$ & $1.7_{1.1}^{2.5}$ & $3.9_{3.0}^{5.1}$ & $59_{43}^{81}$ & $4.6_{2.1}^{8.0}$ & $42_{16}^{88}$ & $2.0_{1.0}^{4.0}$ & $3124$\

Table notes: Median and 16th-to-84th percentile range of the cloud properties. (1) Radial range. (2) Peak brightness temperature. (3) Velocity dispersion. (4) Effective radius. (5) Mass. (6) Surface density. (7) Virial parameter. (8) Number of clouds.

### Mass

Figure [3](#FigCloudPropHistograms)(a) shows the distribution of ${M}_{\mathrm{cl}}$. The unweighted median of ${M}_{\mathrm{cl}}$ for the entire sample is 1.9 $\times$ 10$^5$ M$\odot$, which is close to the median cloud mass found in the inner Galactic disk found by existing surveys (cite: MivilleDeschenes2017MWGMC) and also close to the lower end of a conventional definition of GMC mass range (cite: Sanders1985). The unweighted 16 percentile of cloud mass is 5 $\times$ 10$^4$ M$\odot$ and agrees with the roughly expected minimum cloud mass of $\sim3$ $\times$ 10$^{4}$ ${M}_{\odot}$ (§[2.6](#SubsecCOLumFraction)). This suggests that the present catalog samples the full range of GMCs in M83’s disk, at least when they are well isolated in space or velocity.

Figure [3](#FigCloudPropHistograms)(a), when the top and bottom panels are compared, indicates that massive GMCs are a minority in number but occupy the dominant fraction of the total CO luminosity. About 50% of the molecular gas mass (or total CO luminosity) resides in GMCs with ${M}_{\mathrm{cl}}>10^6$ M$\odot$, although such massive GMCs consist of less than 16% in number. Therefore, the small number of massive clouds contain the major fraction of the total gas mass in M83. This trend is similar to the inner Galactic disk (cite: Solomon1987Larson; MivilleDeschenes2017MWGMC). We will discuss the cloud mass spectrum in §[4](#SecMF).

### Peak temperature

Figure [3](#FigCloudPropHistograms)(b) shows that $T_{\mathrm{peak}}$ has a tail toward the higher end with a maximum value of $\sim$15 K. The unweighted and mass-weighted median values among all the GMCs are 1.3 K and 3.4 K, respectively, having more than a factor of two difference. On the contrary, the difference is smaller for massive clouds with ${M}_{\mathrm{cl}}>10^6$ ${M}_{\odot}$ (3.5 K and 4.7 K). Again, this is because the small number of massive clouds determines the mass-weighted average properties of the GMC population in M83.

We note that in previous extragalactic GMC studies, median $T_{\mathrm{peak}}$ in the sampled clouds is often around 3 K, specifically 3.0 K in M51 (cite: Colombo2014Env) and 3.3 K in M83 (cite: Hirota2018M83), and is higher than our median $T_{\mathrm{peak}}$ of 1.3 K. This is due to low sensitivities in the previous studies, which were made with similar spatial resolutions comparable to that in this study ($\sim46$ pc). In the previous studies, the most frequent cloud masses were 10$^6$ ${M}_{\odot}$ or higher. This work detects abundant clouds with smaller masses by sampling clouds with the minimum $T_{\mathrm{peak}}$ of $\sim0.5$ K.

### Velocity dispersion and radius

Figure [3](#FigCloudPropHistograms)(c) and [3](#FigCloudPropHistograms)(d) show the distribution of $\sigma_{\mathrm{v}}$ and $R_{\mathrm{eff}}$, respectively. The two quantities show different tendencies concerning the classification by ${M}_{\mathrm{cl}}$. The $\sigma_{\mathrm{v}}$ values tend to be higher for more massive clouds, but such a trend is less evident for $R_{\mathrm{eff}}$.

The distribution of $\sigma_{\mathrm{v}}$ has a skewed tail toward the higher end, extending over 20 $\mathrm{km\ s}^{-1}$. The un-weighted and mass-weighted median values of $\sigma_{\mathrm{v}}$ are 3.3 $\mathrm{km\ s}^{-1}$ and 5.3 $\mathrm{km\ s}^{-1}$, respectively. The 16 percentile of $\sigma_{\mathrm{v}}$ is 1.8 $\mathrm{km\ s}^{-1}$ and is well above the instrumental resolution of 0.3 $\mathrm{km\ s}^{-1}$ (§[2.3.2](#SubsecDerivedProps)). Hence, the measured $\sigma_{\mathrm{v}}$ should be almost unaffected by the instrumental resolution.

In contrast to $\sigma_{\mathrm{v}}$, the mass dependence is not clear for $R_{\mathrm{eff}}$. The unweighted median $R_{\mathrm{eff}}$ is 59 pc, and the maximum $R_{\mathrm{eff}}$ is $\sim$100 pc. There are 225 clouds with failure in the deconvolution for $R_{\mathrm{eff}}$ since their pre-deconvolution sizes are less than the spatial resolution (§[2.3.2](#SubsecDerivedProps)). Figure [3](#FigCloudPropHistograms) shows that such deconvolution failed clouds mostly have ${M}_{\mathrm{cl}}$ smaller than 10$^5$ ${M}_{\odot}$.

In this study, the dynamic range in $R_{\mathrm{eff}}$ is limited, with only a factor of two difference between the 16th and 84th percentiles (41 pc and 86 pc). The 84th percentile of 86 pc is easily acceptable as the most significant cloud size should be limited by the thickness of the molecular gas disk, which is estimated to be of order 100 pc in local disk galaxies. For example, the FWHM thickness of the molecular gas disk of the MW is $\sim$100 pc (cite: HeyerDame2015Review). On the other hand, the 16th percentile of 41 pc needs consideration because $R_{\mathrm{eff}}$ is deconvolved, and typical GMCs in the MW have smaller sizes. Most of the recent cloud identification algorithms have a known tendency to find structures with sizes a few times the instrumental resolution (cite: Verschuur1993BeamBias; Hughes2013GMCs), and the $R_{\mathrm{eff}}$ distribution suggests that the same tendency also applies here.

The bootstrap error estimation made in §[2.3.1](#SubsecBasicProps) indicates the measured $R_{\mathrm{eff}}$ is more uncertain than $\sigma_{\mathrm{v}}$, which would indicate that the resolution is more marginal in the spatial directions than the velocity direction. As we identified clouds from the masked data cube, in which all the valid voxels are positive ($>2$ $\sigma$), the cloud radii tend to be overestimated rather than underestimated due to the measurement uncertainty. The relatively large 16th percentile of $R_{\mathrm{eff}}$, 41 pc, could also be a consequence of the overestimation of radius in small clouds. Therefore, even if the beam deconvolution is made to $R_{\mathrm{eff}}$, there might still remain uncertainties on the beam filling factor. Further discussion about this point will be made in §[6](#SecDiscussion).

### Surface density

Figure [3](#FigCloudPropHistograms)(e) shows the distribution of $\Sigma$. The unweighted and mass-weighted median values are 22 ${M}_{\odot}\ \mathrm{pc}^{-2}$ and 128 ${M}_{\odot}\ \mathrm{pc}^{-2}$, respectively; the mass-weighted median is skewed toward massive clouds. This mass-weighted median is close to the median $\Sigma$ for clouds with $M>10^6$ ${M}_{\odot}$ (130 ${M}_{\odot}\ \mathrm{pc}^{-2}$). This alignment suggests a trend that massive GMCs account for the majority of the molecular gas mass in M83.

We note that the previous extragalactic studies in molecular-rich gas disks with shallower mass sensitivities found median $\Sigma$ similar to that for ${M}_{\mathrm{cl}}$ $>10^6$ ${M}_{\odot}$ clouds in M83. (e.g., (cite: Colombo2014Env); (cite: Hirota2018M83); (cite: Freeman2017); (cite: Rosolowsky2021PhangsGMCs) ). The unweighted median $\Sigma$ of 22 ${M}_{\odot}\ \mathrm{pc}^{-2}$ is below the median value by S87 and is close to that among the inner Galactic clouds by (cite: MivilleDeschenes2017MWGMC) ($31.6$ ${M}_{\odot}\ \mathrm{pc}^{-2}$; see also Appendix [11](#SecAppendixMWCatalogComparison)). However, we will discuss that our median aligns better with the high value of S87 after a beam dilution correction (see Section §[6](#SecDiscussion)).

### Virial parameter

Figure [3](#FigCloudPropHistograms)(f) shows distribution of ${\alpha_{\mathrm{vir}}}$. With an assumption of negligible support from magnetic fields and confinement by external pressure, ${\alpha_{\mathrm{vir}}}$ $\sim$ 1 indicates the virial equipartition and ${\alpha_{\mathrm{vir}}}$ $\sim$2 the equipartition between kinetic and gravitational energies (loosely gravitationally-bound). The unweighted median ${\alpha_{\mathrm{vir}}}$ is $\sim$2.4, which is similar to the ones found in some of the recent extragalactic cloud surveys. For example, (cite: Sun2020) found the median ${\alpha_{\mathrm{vir}}}$ of 2.7 from 70 galaxies included in the ALMA-PHANGS program. Recent Galactic cloud catalogs also report higher ${\alpha_{\mathrm{vir}}}$ than $\sim$1, which is suggested from S87’s data by assuming a constant ${\alpha_{\mathrm{CO}}}$ of 4.4 ${M}_{\odot}$ / (K $\mathrm{km\ s}^{-1}$ pc$^2$). Using the same ${\alpha_{\mathrm{CO}}}$, the clouds sampled by (cite: Rice2016) indicate a median ${\alpha_{\mathrm{vir}}}$ of 2.3 for the entire Galactic disk, although it lowers to $\sim$1.5 if the inner Galactic disk clouds are concerned (Appendix [11](#SecAppendixMWCatalogComparison)). Even higher median ${\alpha_{\mathrm{vir}}}$ of $\sim7$ and $\sim11$ are found in the inner and outer Galactic disk by (cite: MivilleDeschenes2017MWGMC).

Mass-weighted mean ${\alpha_{\mathrm{vir}}}$ is close to 1; thus, massive GMCs appear more gravitationally bound than less massive ones at first glance. We show in Appendix [10](#SecAppendixAlphaVirM) that ${\alpha_{\mathrm{vir}}}$ of the M83 clouds tends to vary as $\propto$ ${M}_{\mathrm{cl}}^{-0.5}$. A similar tendency is also seen in previous cloud studies made in different environments (cite: Heyer2001OuterGalaxy; MivilleDeschenes2017MWGMC; Evans2021BoundCloud) (cite: Chevance2023Review). We argue in Appendix [10](#SecAppendixAlphaVirM) that the limited spatial resolution could be forming the trend in the sampled M83 clouds.

## Scaling relations

The scaling relations of cloud properties were empirically established by the early studies of Galactic clouds (cite: Larson1981; Solomon1987Larson). In particular, the following relations are collectively referred to as Larson’s relationships and more qualitatively determined by S87: molecular clouds (i) have a power-law relation between their velocity dispersions $\sigma_{\mathrm{v}}$ and radius $R_{\mathrm{eff}}$, $$\begin{equation}
\sigma_{\mathrm{v}}= C R_{\mathrm{eff}}^{0.5}, \label{eq:Larson1}
\end{equation}$$ with a scaling coefficient $C$ of 0.72 $\mathrm{km\ s}^{-1}\mathrm{pc}^{-1/2}$, (ii) have a near-linear scaling between virial mass and CO luminosity, and (iii) have a constant surface density of $\sim$200 ${M}_{\odot}\ \mathrm{pc}^{-2}$ (S87).

These three relationships are inter-dependent on each other (cite: Heyer2009; BallesterosParedes2011A): by equating the two estimations of cloud mass based on luminosity ($\pi R_{\mathrm{eff}}^2 \Sigma$) and virial equations (${M}_{\mathrm{vir}}/{\alpha_{\mathrm{vir}}}$), we have $$\begin{equation}
C = {\sigma_{\mathrm{v}}}/\sqrt{R_{\mathrm{eff}}}
= \left(\frac{2}{9} {\alpha_{\mathrm{vir}}}\pi G {\Sigma} \right)^{1/2}.
\label{EqSizeLinewidthCoeff}
\end{equation}$$ Therefore, $\propto R_{\mathrm{eff}}^{1/2}$ scaling of $\sigma_{\mathrm{v}}$ (1st relationship) is derived when ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ are constant, which are derived from the 2nd and 3rd relationships. (cite: Heyer2009) also pointed out that the coefficient $C$ varies among clouds sampled in more diverse environments than S87 and it scales as $\Sigma^{1/2}$ as expected by eq. ([\[EqSizeLinewidthCoeff\]](#EqSizeLinewidthCoeff)). (cite: BallesterosParedes2011A) discussed the same dependence in the context of free-fall collapse (cite: Larson1981).

Larson’s relations (the S87’s relations) are often taken as reference relations to compare cloud properties among various environments (cite: Bolatto2008GMCs; Hughes2013GMCs). In an inner portion of M83, (cite: Hirota2018M83) sampled clouds from $^{12}$CO (1–0) data observed with ALMA and found that GMCs in the disk region show similar characteristics as S87’s clouds with median ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ of $\sim1$ and $\sim100$ ${M}_{\odot}\ \mathrm{pc}^{-2}$, respectively. The new data surpass this previous study in sensitivity, although the spatial resolutions are similar: most clouds have $T_{\mathrm{peak}}>2$ K in (cite: Hirota2018M83), while median $T_{\mathrm{peak}}$ is about 1 K in this study. In what follows, we show clouds with $T_{\mathrm{peak}}>$2 K and $<2$ K as separate subsets and show that the $T_{\mathrm{peak}}>$2 K clouds mostly agree with S87’s relations, while the $T_{\mathrm{peak}}<$2 K clouds do not and are more aligned with more recent Galactic clouds surveys (see Appendix [11](#SecAppendixMWCatalogComparison)). Later in §[6](#SecDiscussion), we will show that the majority of the $T_{\mathrm{peak}}<$2 K clouds are likely affected by beam dilution and discuss that they could also follow S87’s relations when the effect of dilution (i.e., beam filling factor) is corrected.

We note one caveat about the scaling relations. The near constant $\Sigma$ of $\sim200$ ${M}_{\odot}\ \mathrm{pc}^{-2}$ in S87’s clouds is a consequence of the selection effect, resulting from the high-intensity thresholds adopted by S87 for identifying cloud peaks (cite: Lombardi2010). Recent studies of Galactic molecular clouds report a wider range of $\Sigma$, in particular with a lower median $\Sigma$ (cite: Rice2016; MivilleDeschenes2017MWGMC; Colombo2019), which resembles low $\Sigma$ values found for the $T_{\mathrm{peak}}$ $<2$ K sample of clouds in M83. Comparison of the M83 clouds with the catalogs of (cite: Rice2016) and (cite: MivilleDeschenes2017MWGMC) is presented in Appendix [11](#SecAppendixMWCatalogComparison).

### Linewidth–size relation

Figure [4](#FigSclRelations)(a) shows the relationship between $\sigma_{\mathrm{v}}$ and $R_{\mathrm{eff}}$ for the clouds in M83. The linewidth–size relation of S87, eq. ([\[eq:Larson1\]](#eq:Larson1)), $C=0.72$ $\mathrm{km\ s}^{-1}$ pc$^{-1/2}$, is also shown with the black dashed line for reference.

Any sign of correlation is hardly seen for $\sigma_{\mathrm{v}}$-$R_{\mathrm{eff}}$ relation with the entire sample of M83 clouds with a low Spearman’s rank correlation coefficient of $\sim$0.3. The absence of the correlation is often seen in other extragalactic GMC studies (cite: Hughes2013GMCs).

Another point to note is that most samples have $\sigma_{\mathrm{v}}$ significantly lower than expected from S87’s relation. Clouds with low $T_{\mathrm{peak}}$ mostly drive the downward deviation as the 20% level contour of the distribution density of the clouds with $T_{\mathrm{peak}}$ $<2$ K is located below the line of S87’s relation. On the other hand, at least some of the clouds with $T_{\mathrm{peak}}$ $>$2 K are compatible with S87’s relation, as indicated by the location of its distribution density contour.

As further reference, we plot the median $\sigma_{\mathrm{v}}$ values derived for the binned cloud radii for the clouds with $T_{\mathrm{peak}}$ $>2$ K and $<2$ K with red and purple markers, respectively. The running-median values exhibit clear separation by $T_{\mathrm{peak}}$. While the median $\sigma_{\mathrm{v}}$ for $>2$ K clouds is located close to S87’s relation of $\sigma_{\mathrm{v}}$ $\propto$ $CR_{\mathrm{eff}}^{1/2}$ with $C$ of 0.72 $\mathrm{km\ s}^{-1}$ pc$^{-1/2}$, that for $<2$ K clouds follows the one with $C$ half of S87’s value, i.e., 0.36 $\mathrm{km\ s}^{-1}$ pc$^{-1/2}$.

The alignment of $>2$ K clouds with S87’s relation suggests that luminous clouds in M83 might share the same characteristics as the Galactic clouds sampled by S87. In the early study of S87, the Galactic clouds were identified by high-intensity detection thresholds, so the S87’s relation would represent the properties of discrete GMCs with high $\Sigma$. Therefore, the luminous clouds in M83 might have properties similar to the dense GMCs in the MW. Again, we note that these clouds are the dominant contributor to the total CO luminosity of the galaxy.

### Virial mass–CO luminosity relation

Figure [4](#FigSclRelations)(b) shows the relationship between the ${M}_{\mathrm{vir}}$ and ${L}_{\mathrm{CO}}$. The dashed line on the figure indicates the case for the simple virial equilibrium, ${\alpha_{\mathrm{vir}}}$ = 1, with the ‘standard’ CO-to-H$_2$ conversion factor of 2.0 $\times$ 10$^{20}$ cm$^{-2}$ / (K $\mathrm{km\ s}^{-1}$).

As a whole, both quantities are well correlated to each other with Spearman’s correlation coefficient of $\sim0.8$. In particular, the $>2$ K clouds exhibit tight correlation, located within a factor of 3 variation to ${\alpha_{\mathrm{vir}}}$ of 1. The $<2$K clouds also show correlation but are located upward of the line of ${\alpha_{\mathrm{vir}}}$ = 1. Such upward deviation is often interpreted as the super-virial state of clouds or the variation in the CO-to-H$_2$ conversion factor.

The Galactic clouds of S87 exhibit a narrow range of distribution on the plot, with the fitted result of ${M}_{\mathrm{vir}}$(${M}_{\odot}$) = 43 $\left[ {L}_{\mathrm{CO}}\left( \mathrm{K}\ \mathrm{km\ s}^{-1}\ \mathrm{pc}^2\right) \right]^{0.81}$ after adjusting for the adopted distance to the Galactic center (cite: Bolatto2013ConversionFactor). The $T_{\mathrm{peak}}$ $>2$K clouds mostly align with S87’s reference relation. The least-square fitting to $>2$ K clouds yield $$\begin{equation}
{M}_{\mathrm{vir}}( {M}_{\odot} ) = (114 \pm 5) \left[ {L}_{\mathrm{CO}}\left( \mathrm{K}\ \mathrm{km\ s}^{-1}\ \mathrm{pc}^2\right) \right]^{0.75\pm0.02},
\label{EqMvirLCOFit}
\end{equation}$$ which has an index similar to S87’s relation.

### Mass–size relation

Figure [4](#FigSclRelations)(c) shows the relationship between ${M}_{\mathrm{cl}}$ and $R_{\mathrm{eff}}$. The lines for $\Sigma$=1, 10, 100, and 1000 ${M}_{\odot}\ \mathrm{pc}^{-2}$ are drawn for reference with dotted lines. The Galactic clouds of S87 lie close to a constant $\Sigma$ line of $200$ ${M}_{\odot}\ \mathrm{pc}^{-2}$.

In contrast to the narrow range of $\Sigma$ seen in S87’s MW clouds, the measured properties of the M83 clouds exhibit a wide range of $\Sigma$, reaching about three orders of magnitudes on the plot. The wide range is similar to the Galactic clouds sampled by (cite: MivilleDeschenes2017MWGMC) (see their figure 7a). The correlation coefficient is low for the entire sample ($\sim0.3$). Still, the $>$2 K clouds are centered around the constant $\Sigma$ of 100 ${M}_{\odot}\ \mathrm{pc}^{-2}$. Taking the running median of ${M}_{\mathrm{cl}}$ for $>2$ K and $<2$ K clouds as was made in $\sigma_{\mathrm{v}}$–$R_{\mathrm{eff}}$ relation, it is apparent that the $>$ 2K clouds are distributed close to the line of constant $\Sigma$=100 ${M}_{\odot}\ \mathrm{pc}^{-2}$. For the $<2$ K clouds, the slope of the median mass values is shallower than those of the constant $\Sigma$ lines, suggesting a trend that (apparently) larger clouds have smaller $\Sigma$.

### Normalized velocity dispersion–surface density relationship

Figure [4](#FigSclRelations)(d) shows the relationship between the normalization coefficient of the linewidth–size relation $C (=\sigma_{\mathrm{v}}/R_{\mathrm{eff}}^{1/2})$ and $\Sigma$. As in eq. ([\[EqSizeLinewidthCoeff\]](#EqSizeLinewidthCoeff)), $C$ is proportional to $\Sigma^{1/2}$ for clouds dominated by self-gravity if ${\alpha_{\mathrm{vir}}}$ is approximately constant. The dashed and dotted lines show the expected behaviors for ${\alpha_{\mathrm{vir}}}$ of 1 and 2, corresponding to the gravitational virial equilibrium and free-fall collapse, respectively.

A high correlation coefficient of $\sim$0.8 is obtained, but this is trivially expected because the scaling between $C$ and $\Sigma^{1/2}$ is mathematically equivalent to the ${M}_{\mathrm{vir}}$–${L}_{\mathrm{CO}}$ scaling (§[3.2.2](#SubsecMvirLCO)).

If all the clouds are strongly governed by self-gravity, we would expect all the data points to be clustered around the lines of ${\alpha_{\mathrm{vir}}}$=1 and 2. However, we see upward deviations from these lines toward lower $\Sigma$, mainly driven by the clouds with $T_{\mathrm{peak}}$ $<2$ K. To characterize the deviation, a least-square fitting to the entire sample is made, $$\begin{equation}
\sigma_{\mathrm{v}}(\mathrm{km\ s}^{-1}) / \sqrt{R_{\mathrm{eff}}(\mathrm{pc})} = (0.16 \pm 0.01) \left[ \Sigma( {M}_{\odot}\ \mathrm{pc}^{-2} ) \right]^{0.30 \pm 0.01}.
\label{EqSizeLinewidthCoeffSigmaRelationFit}
\end{equation}$$ This index, $\sim$0.30, is shallower than the 0.5 for clouds governed by self-gravity (eq.[\[EqSizeLinewidthCoeff\]](#EqSizeLinewidthCoeff)).

The clouds with $T_{\mathrm{peak}}>2$ K and $T_{\mathrm{peak}}<2$ K make a clear separation on the plot. The $>2$ K clouds are mostly clustered around the line of ${\alpha_{\mathrm{vir}}}$=1 and over a factor of a few range around $\Sigma\sim 100$ ${M}_{\odot}\ \mathrm{pc}^{-2}$. On the other hand, the $<2$ K clouds are distributed systematically in the area of ${\alpha_{\mathrm{vir}}}>1$ (the 20% density level barely crosses the line of ${\alpha_{\mathrm{vir}}}$=1). Their $\Sigma$ values are lower. The shallow index of $\sim$0.3 of the $\sigma_{\mathrm{v}}/\sqrt{R}$–$\Sigma$ relation is driven by the larger ${\alpha_{\mathrm{vir}}}$ in the clouds with $T_{\mathrm{peak}}<2$ K. We will discuss the impact of beam dilution on ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ in §[6](#SecDiscussion) and also show that the beam dilution also explains the shallow index of $\sim$0.3 in Appendix [9](#SecAppendixSizelinewidthCoeffSigma).

## Spatial distribution of the clouds

Figure [5](#FigM0ByMass) shows the distribution of the identified clouds, categorized into three groups by mass: $<$10$^{5}$, 10$^{5-6}$, and $>$10$^{6}$ ${M}_{\odot}$, respectively. Massive clouds over 10$^6$ ${M}_{\odot}$ are strongly concentrated around bright galactic structures, namely the galactic center, bar, and spiral arms. On the contrary, smaller clouds (below $10^6$ ${M}_{\odot}$) prevail over the wider area, residing both in arm and inter-arm regions. This confirms the similar trends reported in other galaxies (cite: Koda2009; Colombo2014Env).

Figure [6](#FigM0ByTpeak) also shows the distribution of the clouds but categorized with $T_{\mathrm{peak}}>2$ K and $<2$ K. As ${M}_{\mathrm{cl}}$ and $T_{\mathrm{peak}}$ are correlated, figures [6](#FigM0ByTpeak) and [5](#FigM0ByMass) resemble each other. High-$T_{\mathrm{peak}}$ clouds ($>$2K) are often found within bright galactic structures, as were for the massive clouds. In the previous subsection, we saw that the properties of the $>2$ K clouds mostly agree with the relations of S87. The observation that $>2$ K clouds are found within or around larger-scale structures, such as bar, arm, and spurs, suggests that the galactic structures play an important role in assembling the massive, bright clouds that share similar properties as S87’s sample.

### Spiral arm locations traced by molecular clouds

Figure [7](#FigArmLocs)(a) plots the clouds on the $\log{R_{\mathrm{gal}}}$ - $\phi$ plane. As seen above, the massive clouds ($>$ 10$^6$ ${M}_{\odot}$) highlight the locations of the spiral arms. We identify sequences of the massive clouds on the $\log{R_{\mathrm{gal}}}$ - $\phi$ plane and linearly fit the sequences (i.e., logarithmic spiral arms with constant pitch angles). The fit results are shown in the plot.

Figure [7](#FigArmLocs)(b) displays the fitted logarithmic spiral structures in a two-dimensional map and the distribution of clouds with masses above 10$^6$ ${M}_{\odot}$. The identified structures are tied to the following knowledge. In the inner part of M83, the two main spiral arms extend from both ends of the bar. The eastern main arm is displayed with the blue line, and on the trailing side of it, a narrower molecular ridge runs parallel, shown as the yellow line. This narrow ridge is seen as a dust lane at optical wavelengths (cite: RandLordHidgon1999M83) but has weaker CO emission compared to the main arm (cite: Hirota2018M83). At first glance, The western spiral arm appears to have a long extension from the western end of the bar toward the eastern side, but it has two changes in pitch angle on the $\log{R_{\mathrm{gal}}}$ - $\phi$ plane. Therefore, it is divided into three segments, shown with the orange, green, and purple lines. In the outermost part, the eastern arm appears as "a bundle of narrower filaments or ripples" on the CO image (cite: Koda2023M83) – the purple, brown, and red lines correspond to such molecular filaments. Although the outermost western spiral segment is less defined than the inner main spirals, we tentatively identified a logarithmic spiral shown as the pink line. Further discussion on the spiral structures in the CO image is also available in (cite: Koda2023M83) (see Fig. 11).

We define a region mask using the fitted arm positions for the analyses in the following sections (figure [7](#FigArmLocs)c). In this mask, each of the logarithmic spiral arm regions has a width of 40$\ensuremath{''}$ ($\sim$880 pc) and the bar region as an ellipse with major and minor axis lengths of 86$\ensuremath{''}$ and 32$\ensuremath{''}$ respectively, with a position angle of 225$\ensuremath{^\circ}$. The central region is defined as $R_{\mathrm{gal}}$ $<16\ensuremath{''}$ ($\sim350$ pc). The mask contains a majority of massive or bright clouds. Out of 734 clouds with $>10^6$ ${M}_{\odot}$ in M83, 498 clouds reside in the arm/bar/center mask. The total mass of $>10^6$ ${M}_{\odot}$ clouds is $\sim$2.2 $\times$ 10$^9$ ${M}_{\odot}$ and about 80% of the mass is included in the mask.

# Cloud mass function

The mass distribution of GMCs is characterized by a mass function of a power-law form, i.e., ${dN}/{dM} \propto M^{\gamma}$. The early GMC surveys in the inner Galactic disk consistently found the index $\gamma$ of around $-1.5$ (cite: Sanders1985; Solomon1987Larson; WilliamsMcKee1997; Rosolowsky2005MassSpectra). Subsequent studies in other environments also found $\gamma$ mainly in the range of -1.5 to -2.5 (cite: Heyer2001OuterGalaxy; Colombo2014Env), but even steeper relations (more negative) values of $\gamma$ are also found in some environments (cite: Engargiola2003; Fukui2008). For a power-law distribution, $\gamma>-2$ means that a small number of massive clouds carry most of the total cloud mass, like the GMC mass distribution in the Galactic disk. In contrast, $\gamma<-2$ means that most cloud mass resides in the smaller mass end.

At the higher end of the mass distribution, the deficit of massive clouds is also often seen: in the Galactic disk, clouds more massive than a few 10$^6$ ${M}_{\odot}$ are frequently under-populated with respect to the power-law relation (cite: WilliamsMcKee1997). Some previous studies reported $\gamma$ steeper (smaller) than -2, but this might be a consequence of fitting cloud mass distributions above such an upper limit mass (cite: Rosolowsky2005MassSpectra).

## Functional forms

We fit the cloud mass distribution in two forms. The first form is a power-law, restricted by the upper mass limit ${M_{\mathrm{lim}}}$ as, $$\begin{equation}
\frac{dN}{dM} \propto \left(\frac{{M}_{\mathrm{cl}}}{{M_{\mathrm{lim}}}}\right)^{{\gamma_{\mathrm{PL}}}}, \ \ {M}_{\mathrm{cl}}< {M_{\mathrm{lim}}}.
\label{EqMFPowerLawDiff}
\end{equation}$$ The form is conventionally applied to the cloud mass distributions (cite: WilliamsMcKee1997; Rosolowsky2005MassSpectra; Colombo2014Env). It can be written in the integral form as follows $$\begin{equation}
N(>M) = {N_{\mathrm{u,PL}}}
\left [ \left(\frac{{M}_{\mathrm{cl}}}{{M_{\mathrm{lim}}}}\right)^{{\gamma_{\mathrm{PL}}}+ 1} - 1  \right]
\label{EqMFConventional},
\end{equation}$$ where ${N_{\mathrm{u,PL}}}$ is the number of clouds more massive than $2^{1 / ({\gamma_{\mathrm{PL}}}+ 1)} {M_{\mathrm{lim}}}$, which we denote as ${M_{\mathrm{u,PL}}}$. We call ${M_{\mathrm{u,PL}}}$ the cutoff mass for the restricted power-law form because the deviation from a power-law becomes obvious above ${M_{\mathrm{u,PL}}}$.

The second form combines the power-law distribution with an exponential cutoff, which is often called a Schechter-like function: $$\begin{equation}
\frac{dN}{dM} \propto \left(\frac{M}{{M_{\mathrm{u,exp}}}}\right)^{{\gamma_{\mathrm{exp}}}} \exp{\left(-\frac{M}{{M_{\mathrm{u,exp}}}}\right)},
\label{EqMFExpCutoff}
\end{equation}$$ where ${\gamma_{\mathrm{exp}}}$ is the index of a power-law distribution, and ${M_{\mathrm{u,exp}}}$ is the cutoff mass limit above which the distribution is suppressed with respect to the power-law. Fitting the cloud mass distribution with this Schechter-like form would help test the connection between the mass spectra of GMCs and stellar clusters as the cluster mass distributions are often characterized with this form (cite: Kruijssen2014Cluster; Adamo2015). However, the application of this form to molecular cloud distributions is limited in recent studies (cite: Freeman2017; Rosolowsky2021PhangsGMCs).

## Cloud mass spectra

Figure [8](#FigMFs) shows the cloud mass distributions for (a) all GMCs and (b-f) those in five radial bins. The latter is defined with the boundaries at $25\ensuremath{''}$ ($\sim0.55$ kpc), $100\ensuremath{''}$ ($\sim2.2$ kpc), $140\ensuremath{''}$ ($\sim3.1$ kpc), and $210\ensuremath{''}$ ($\sim4.6$ kpc), respectively, which are shown in figure [1](#FigRMSMap)(b). They are to examine the radial and environmental variation of the cloud mass distribution: The first three bins mainly cover the central region, bar, and two main spiral arms, respectively, and the last two bins divide the outer galactic disk into two.

All the histograms show declines below around $2\times10^{5}$ ${M}_{\odot}$, suggesting that cloud sampling is incomplete below that mass. As discussed in §[2.6](#SubsecCOLumFraction), our mass sensitivity in cloud identification is $\sim3\times10^{4}$ ${M}_{\odot}$ for a cloud in isolation. The difference would be attributed to the blending of cloud emissions. For a cloud to be detected above the high background surface density $\Sigma_\mathrm{bg}$ (e.g., in spiral arms), its mass has to exceed $\Sigma_{\mathrm{bg}}$ A$_\mathrm{beam}$ with A$_\mathrm{beam}$ as beam area. For example, in most spiral arms, the typical $\Sigma_{\mathrm{bg}}$ is 100${M}_{\odot}\ \mathrm{pc}^{-2}$. Therefore, the minimum detectable mass in the arms cannot go below $\sim2 \times 10^{5}$ ${M}_{\odot}$ with the current resolution of $\sim46$ pc. Hereafter, we regard $2\times10^{5}$ ${M}_{\odot}$ as the effective completeness limit. This is a conservative limit in the disk region because the limit should be smaller in the inter-arm regions. However, the mass limit is higher in the central region because $\Sigma_{\mathrm{bg}}$ reaches nearly 1000 ${M}_{\odot}\ \mathrm{pc}^{-2}$ or higher there (cite: Koda2023M83).

We fit only the clouds with $>$2$\times$ 10$^5$ ${M}_{\odot}$ (above the completeness limit) with the two forms. We fitted the power-law form using the cumulative mass distribution function and least-square minimization against the integral form (eq. [\[EqMFConventional\]](#EqMFConventional)). For the Schechter-like form (eq. [\[EqMFExpCutoff\]](#EqMFExpCutoff)), we sample the likelihood using the *emcee* software library, which implements a Markov chain Monte Carlo method (cite: ForemanMackey2013emcee). The prior distribution is configured such that the probability distribution of ${\gamma_{\mathrm{exp}}}$ is uniform between -5 and 0 and that ${M_{\mathrm{u,exp}}}$ is also uniform between 10$^5$ ${M}_{\odot}$ and 10$^9$ ${M}_{\odot}$ in the logarithmic space. Table [\[tableMFParams\]](#tableMFParams) reports the fitted parameters and $p$-values calculated with the two-sample K-S test for both forms with the null hypothesis that the fitted and observed cumulative mass distributions are drawn from the same distribution.

Figure [8](#FigMFs)(a) shows the mass distribution for all the clouds. The power-law fit gives ${\gamma_{\mathrm{PL}}}\sim -1.85$, which is comparable to the indices found in the inner Galactic disk (cite: WilliamsMcKee1997). The Schechter-like form yields an index ${\gamma_{\mathrm{exp}}}$ of $\sim-1.57$, which is shallower than ${\gamma_{\mathrm{PL}}}$ but is still comparable to the Galactic values. Both forms suggest the existence of upper cutoff masses with similar values, namely ${M_{\mathrm{u,PL}}}$ of $\sim$8.6$\times$10$^6$ ${M}_{\odot}$ and ${M_{\mathrm{u,exp}}}$ of $\sim$8.0$\times$10$^6$ ${M}_{\odot}$, respectively.

Figure [8](#FigMFs)(b) is for the innermost radial bin of $R_{\mathrm{gal}}< 25\ensuremath{''}$ ($\sim550$ pc). The fitted indices are shallow: ${\gamma_{\mathrm{PL}}}\sim$-1.33 and ${\gamma_{\mathrm{exp}}}\sim$-1.26. Due to the elevated background $\Sigma_{\mathrm{bg}}$, the shallow index is likely an artifact caused by the heavy blending of cloud emissions.

Figure [8](#FigMFs)(c–f) shows the cloud mass distributions beyond $R_{\mathrm{gal}}\sim$550 pc. Within the four radial bins, ${\gamma_{\mathrm{PL}}}$ varies within the range of $\sim$-1.7 to $\sim$-2.0 with a tendency of steeper index toward the outer radius. On the contrary, the Schechter-like form results in more minor variations in ${\gamma_{\mathrm{exp}}}$, ranging from -1.2 to -1.4, with no notable radial trend. In terms of the upper cutoff mass, both forms are again consistent. As we will comment later in §[4.3](#SubsecMFFormComparison), the Schechter-like form tends to characterize the variation in mass spectra by a change in ${M_{\mathrm{u,exp}}}$ rather than in ${\gamma_{\mathrm{exp}}}$. Both ${M_{\mathrm{lim}}}$ and ${M_{\mathrm{u,exp}}}$ exhibit a factor of three declines with increasing galactocentric radii.

Figure [9](#FigMFParamRadial) compares the upper-cutoff mass determined from the fittings, ${M_{\mathrm{u,PL}}}$ and ${M_{\mathrm{u,exp}}}$, with the radial distribution of the individual cloud masses. This plot also shows the luminosity-weighted mean cloud mass in radial bins with a width of $12\ensuremath{''}$. This luminosity-weighted mean mass declines radially, except for a slight secondary peak around $R_{\mathrm{gal}}= 100\ensuremath{''}$ where the main two spiral arms reside. The radially declining trend of the luminosity-weighted mean generally agrees with the variation of ${M_{\mathrm{u,PL}}}$ and ${M_{\mathrm{u,exp}}}$ derived from the fittings. The alignment would be reasonable as the slopes of the fitted mass functions in figure [8](#FigMFs) are mostly shallower than -2, and thus, most of the CO luminosity (and mass) should be concentrated around the upper cutoff mass.

## Comparison of the fitted results between the two forms

Because of the discrepancies between ${\gamma_{\mathrm{PL}}}$ and ${\gamma_{\mathrm{exp}}}$, one would wonder which of the two forms, namely the restricted power-law form or Schechter-like form, provides a better characterization of the cloud mass distributions. The $p$-values of the K-S test in table [\[tableMFParams\]](#tableMFParams) are inconclusive. By taking the significance level of $p$-value as 0.05, the K-S test accepts almost all the cases except the restricted power-law form applied to all samples. The values of ${\gamma_{\mathrm{exp}}}$ are shallow in most radial ranges with a slight variation (-1.2 to -1.4). The shallow and limited variation in ${\gamma_{\mathrm{exp}}}$ might be due to the limited dynamic range in fitting – there is only about an order of magnitude variation between ${M_{\mathrm{u,exp}}}$ and the adopted completeness limit of 2$\times$10$^5$ ${M}_{\odot}$. The exponential term induces a decline even below ${M_{\mathrm{u,exp}}}$ to some extent, further limiting the range available to fit as a power-law. The determination of ${\gamma_{\mathrm{exp}}}$ might become reliable only if higher resolution data becomes available to overcome the crowding effect to lower the mass completeness limit (cite: Rosolowsky2021PhangsGMCs). As the K-S test gives no clear preference and as we suspect the fitted values ${\gamma_{\mathrm{exp}}}$ might be biased, we consider that ${\gamma_{\mathrm{PL}}}$ to be preferable to ${\gamma_{\mathrm{exp}}}$, at least with the available data.

## Possible origins of the radial variation of mass spectra

The power-law fitting shows a radially steepening of ${\gamma_{\mathrm{PL}}}$ from -1.3 to -2.0 and a decrease of ${M_{\mathrm{u,PL}}}$, indicating a relative deficit of massive clouds toward the outer disk. The trends agree with other studies in M83 with shallower sensitivities (cite: Freeman2017; Hirota2018M83) and also in different environments (cite: Colombo2014Env). Several mechanisms might explain the radial trends in ${\gamma_{\mathrm{PL}}}$ and ${M_{\mathrm{u,PL}}}$. First, given that M83 has many bubble structures in infrared, HI, and CO, which likely influence and drive the evolution of molecular clouds. (cite: Inutsuka2015) and (cite: Kobayashi2017MF) provide semi-analytical calculations to describe the time evolution of molecular cloud mass functions regulated by multiple episodes of bubble expansions, which drive molecular cloud formation via shock compression of atomic gas. The idea would explain the steeper ${\gamma_{\mathrm{PL}}}$ in the outer disk as the slower cloud formation because the supernovae, which drive bubble expansions, are less frequent there. (cite: Kobayashi2017MF) also suggested the formation of massive clouds comparable to ${M_{\mathrm{u,PL}}}$ requires about 100 Myr by solving the time evolution, which agrees with the time scale predicted from the CO morphology of M83 (cite: Koda2023M83). Second, the under-population of massive clouds above ${M_{\mathrm{u,PL}}}$ might also be due to a lower molecular fraction in massive clouds – (cite: Elmegreen1989MassMetalDependence) provides that self-shielding decreases approximately as $\propto$ $M^{-0.5}$ for virialized clouds, and therefore, CO line observations might trace only the core regions in most massive clouds. As there is a radial decrease of per-cloud molecular fraction in the MW (cite: Elmegreen1987HISuperClouds), it would be intriguing to compare molecular clouds with massive HI clouds in M83.

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Range | $\gamma_{\mathrm{PL}}$ | $N_{\mathrm{u,PL}}$ | $M_\mathrm{u,PL}$ | $p$-value | $\gamma_{\mathrm{exp}}$ | $M_\mathrm{u,exp}$ | $p$-value |
|  |  |  | ($10^6  {M}_{\odot}$) |  |  | ($10^6  {M}_{\odot}$) |  |
| 0.0 kpc - 0.5 kpc | $-1.33^{+0.02}_{-0.02}$ | $6.9^{+0.6}_{-0.7}$ | $7.41^{+0.14}_{-0.37}$ | 1.00 | $-1.26^{+0.09}_{-0.09}$ | $46.29^{+38.51}_{-15.64}$ | 1.00 |
| 0.5 kpc - 2.2 kpc | $-1.73^{+0.00}_{-0.00}$ | $25.3^{+0.5}_{-0.5}$ | $5.10^{+-0.06}_{--0.07}$ | 0.10 | $-1.30^{+0.07}_{-0.08}$ | $4.52^{+1.00}_{-0.73}$ | 0.44 |
| 2.2 kpc - 3.1 kpc | $-1.60^{+0.01}_{-0.01}$ | $30.8^{+0.6}_{-0.5}$ | $3.93^{+-0.02}_{--0.02}$ | 0.46 | $-1.21^{+0.08}_{-0.08}$ | $4.69^{+1.02}_{-0.81}$ | 1.00 |
| 3.1 kpc - 4.6 kpc | $-1.86^{+0.00}_{-0.01}$ | $40.4^{+0.7}_{-0.7}$ | $2.53^{+-0.02}_{--0.02}$ | 0.33 | $-1.21^{+0.11}_{-0.10}$ | $1.79^{+0.34}_{-0.26}$ | 0.99 |
| 4.6 kpc - 6.1 kpc | $-2.01^{+0.01}_{-0.01}$ | $33.8^{+0.8}_{-0.8}$ | $2.20^{+-0.03}_{--0.03}$ | 0.27 | $-1.39^{+0.11}_{-0.11}$ | $1.45^{+0.31}_{-0.23}$ | 1.00 |
| all | $-1.85^{+0.00}_{-0.00}$ | $52.3^{+0.4}_{-0.4}$ | $8.58^{+-0.06}_{--0.06}$ | 0.00 | $-1.57^{+0.03}_{-0.03}$ | $7.93^{+1.15}_{-0.85}$ | 0.21 |

: Mass function parameters

Table notes: Mass function parameters. (1) Radial range. (2 to 4) Mass function parameters determined by the fitting with restricted power-law, namely power-law index ${\gamma_{\mathrm{PL}}}$, number of clouds at high mass end ${N_{\mathrm{u,PL}}}$, and upper-cutoff mass ${M_{\mathrm{u,PL}}}$. (5) K-S test $p$-value the restricted power-law fitting. (6 and 7) Parameters determined by the fitting with the Schechter-like form, namely index ${\gamma_{\mathrm{exp}}}$ and upper-cutoff mass ${M_{\mathrm{u,exp}}}$. (8) K-S test $p$-value the Schechter-like form fitting.

# Cloud-to-cloud velocity dispersion

Vertical cloud-to-cloud velocity dispersion of a gaseous disk is a parameter that reflects the stability of the disk. Despite its importance, the measurements of the cloud-to-cloud velocity dispersion of molecular gas are still limited. In the MW, (cite: Stark1984VelDispersion) found that the cloud-to-cloud velocity dispersion within the Galactic plane weakly depends on cloud mass, with 6.6 $\mathrm{km\ s}^{-1}$ and 9.0 $\mathrm{km\ s}^{-1}$ for cloud masses of 10$^{4-5.5}$ ${M}_{\odot}$ and 10$^{2-4}$ ${M}_{\odot}$, respectively. However, the estimation from the MW data involves an assumption of the isotropy of velocity dispersion.

Extragalactic observations of nearly face-on galaxies permit estimation of the vertical cloud-to-cloud velocity dispersion. Previous measurements were performed at sub-kpc scale resolutions, which blend several GMCs within resolution elements; they found dispersions of 6 to 9 $\mathrm{km\ s}^{-1}$ when an individual spectrum of each pointing is analyzed (cite: CombesBecquaert1997; Wilson2011JCMT; Mogotsi2016) and about 12 to 14 $\mathrm{km\ s}^{-1}$ when the spectra at multiple pointings are stacked (cite: CalduPrimo2013; CalduPrimo2016Andromeda). With the new cloud catalog and low inclination angle of M83, we can make a more direct estimation of the vertical cloud-to-cloud velocity dispersion.

## Method to estimate vertical velocity dispersion of clouds

We adopt a method similar to the one used by (cite: Hernandez2019) to estimate the vertical velocity dispersion of stellar clusters. The line-of-sight velocity ${v_{\mathrm{LOS}}}$ of a cloud rotating in the disk is written as $$\begin{equation}
{v_{\mathrm{LOS}}}= {v_{\mathrm{sys}}}+ ({v_{\mathrm{rot}}}+ {v_{\mathrm{phi}}}) \cos{\phi} \sin{i}
+ {v_{\mathrm{R}}}\sin{\phi} \sin{i}
+ {v_{\mathrm{z}}}\cos{i},
\end{equation}$$ where ${v_{\mathrm{sys}}}$, ${v_{\mathrm{rot}}}$, ${v_{\mathrm{phi}}}$, ${v_{\mathrm{R}}}$, ${v_{\mathrm{z}}}$, $\phi$, and $i$ are the systemic recession velocity, the circular rotational velocity expected from the galactic rotation curve, in-plane azimuthal and radial non-circular velocities that are mostly governed by streaming motions, vertical motion velocity, the angle from the major axis, and the inclination angle. We subtract the contributions of assumed ${v_{\mathrm{sys}}}$ and ${v_{\mathrm{rot}}}$ from ${v_{\mathrm{LOS}}}$ for each cloud. Then, the residual velocity ${v_{\mathrm{res}}}$ is left with the contributions from ${v_{\mathrm{z}}}$ and streaming motions as $$\begin{equation}
{v_{\mathrm{res}}}= {v_{\mathrm{z}}}\cos{i} + {v_{\mathrm{phi}}}\cos{\phi} \sin{i} + {v_{\mathrm{R}}}\sin{\phi} \sin{i}.
\label{EqVres}
\end{equation}$$ As long as the contributions from the in-plane non-circular motions, i.e., the last two terms in this equation, are negligible, we can estimate the cloud-to-cloud velocity dispersion, $\mathrm{<}{v_{\mathrm{z}}}\mathrm{>}$, as the dispersion of ${v_{\mathrm{res}}}/\cos{i}$ among a sample of clouds.

We adopt ${v_{\mathrm{sys}}}$ of 511 $\mathrm{km\ s}^{-1}$ and $i$ of 24$\ensuremath{^\circ}$ (cite: Koda2023M83). For ${v_{\mathrm{rot}}}$, we use the rotation curve of (cite: Hirota2014), which is obtained by subtracting the rotational velocities estimated from the stellar mass distribution using the 2MASS Large Galaxy Atlas image (cite: Jarrett20032MASS) with an assumption of the maximum disk contribution.

## Vertical cloud-to-cloud velocity dispersion

Figure [10](#FigClClVelcityDispersion)(a) shows ${v_{\mathrm{res}}}$ as a function of galactocentric radius $R_{\mathrm{gal}}$ for the M83 clouds. The clouds with masses below and above 5 $\times$ 10$^5$ ${M}_{\odot}$ are plotted separately with gray and cyan markers, respectively. The radial bins are configured with a width and increment of 24$\ensuremath{''}$ and 12$\ensuremath{''}$, up to 288$\ensuremath{''}$. The 16th, 50th, and 84th percentiles of ${v_{\mathrm{res}}}$ are plotted for each radial bin.

The absolute $|{v_{\mathrm{res}}}|$ values are elevated within the inner 100$\ensuremath{''}$ ($\sim$2.2 kpc) of M83, where the stellar bar resides. Although $|{v_{\mathrm{res}}}|$ includes the contributions from the in-plane non-circular motions and vertical velocity dispersion (eq. [\[EqVres\]](#EqVres)), the ${v_{\mathrm{phi}}}$ and ${v_{\mathrm{R}}}$ terms appear to be negligible except in the bar, which induces large non-circular streaming motions. Outside the bar, the 16th and 84th percentiles of ${v_{\mathrm{res}}}$ are within the range of $|{v_{\mathrm{res}}}|$ $<$ 10 $\mathrm{km\ s}^{-1}$, suggesting only a modest impact of the arm-induced streaming motions. This suggestion agrees with (cite: TilanusAllen1993), who found a modest streaming motion of about 15 $\mathrm{km\ s}^{-1}$ in the plane of M83.

Figure [10](#FigClClVelcityDispersion)(b) shows the radial distribution of estimated cloud-to-cloud velocity dispersions, $\mathrm{<}{v_{\mathrm{z}}}\mathrm{>}$ for clouds above (cyan) and below (black) 5$\times$10$^5$ ${M}_{\odot}$. Except for the inner bar region ($R_{\mathrm{gal}}$ $<$ 100$\ensuremath{''}$; $\sim2.2$ kpc) where the impact of streaming motion is not negligible, we consider the data points to be the fair representatives of $\mathrm{<}{v_{\mathrm{z}}}\mathrm{>}$ based on the small variation in the scatters of ${v_{\mathrm{res}}}$ at $R_{\mathrm{gal}}$ $>$ 100$\ensuremath{''}$. At $R_{\mathrm{gal}}$ $>$ 100$^{''}$, $\mathrm{<}{v_{\mathrm{z}}}\mathrm{>}$ is found to be almost constant around 8.3 $\mathrm{km\ s}^{-1}$ for $>$5$\times$10$^5$ ${M}_{\odot}$ clouds and 11 $\mathrm{km\ s}^{-1}$ for $<5$ $\times$ 10$^5$ ${M}_{\odot}$ clouds.

We performed Levene’s test at each radial bin to see the statistical significances of the differences in ${v_{\mathrm{res}}}$ between $>5\times10^5$ ${M}_{\odot}$ and $<5\times10^5$ ${M}_{\odot}$ clouds (figure [10](#FigClClVelcityDispersion)c). The test’s null hypothesis is that the underlying ${v_{\mathrm{res}}}$ distribution is the same in both groups, i.e., the vertical velocity dispersion is the same. We discard the null hypothesis if the $p$-value of the test is below 0.05. The resultant $p$-values are far below the adopted significance level of 0.05 in most of the bins beyond $R_{\mathrm{gal}}$ $>$ 100$^{''}$, suggesting that the mass dependence of $\mathrm{<}{v_{\mathrm{z}}}\mathrm{>}$ is significant there.

### Assessment of the impact of streaming motions on the estimated vertical cloud-to-cloud velocity dispersion

A caveat of the $\mathrm{<}{v_{\mathrm{z}}}\mathrm{>}$ estimation made here is that the impact of in-plane non-circular motion is just neglected. As massive clouds are concentrated toward spiral structures (§[3.3](#SubsecSpatialDistribution)), one might suspect they are more susceptible to streaming motions. To eliminate this possibility, we show the spatial distribution of ${v_{\mathrm{res}}}$ for individual clouds in figure [10](#FigClClVelcityDispersion)(d). The marker colors show the elevation of $|{v_{\mathrm{res}}}|$ around spiral arms. The locations of the galactic structures identified in §[3.3](#SubsecSpatialDistribution) are also shown for comparison.

Streaming motions around the bar and spiral arms are coherent and should show ordered patterns in this figure. While such coherent motions appear limited, there are still some signatures. For example, across the eastern, outermost arm-like feature from the trailing to leading side, ${v_{\mathrm{res}}}$ changes from positive (red markers) to negative (blue markers).

Figure [10](#FigClClVelcityDispersion)(e) is similar to figure [10](#FigClClVelcityDispersion)(b), but plots the radial variation of $\mathrm{<}{v_{\mathrm{z}}}\mathrm{>}$ for clouds in the center/bar/arm region and the inter-arm regions using the spatial mask shown in figure [10](#FigClClVelcityDispersion)(d). Except for the innermost two radial bins, the dispersions within the bar/spiral arms and inter-arm regions are similar to each other. The $p$-values obtained with Levene’s test (figure [10](#FigClClVelcityDispersion)f) also support their similarity. We here conclude that the arm-streaming motions have less impact on ${v_{\mathrm{res}}}$ than the mass-dependence of the vertical cloud-to-cloud velocity dispersion at $R_{\mathrm{gal}}$ $>2.2$ kpc.

### Comparision with the previous studies

We identify a weak mass dependence of $\mathrm{<}{v_{\mathrm{z}}}\mathrm{>}$, with $\sim$8.3 $\mathrm{km\ s}^{-1}$ and $\sim$11 $\mathrm{km\ s}^{-1}$ for clouds above and below 5$\times$10$^5$ ${M}_{\odot}$ at $R_{\mathrm{gal}}$ beyond 2.2 kpc. The former is close to the values found in other extragalactic studies at kpc-scale resolutions (cite: CombesBecquaert1997; Mogotsi2016). The consistency with our study at $\sim$46 pc resolution may be because massive clouds occupy the dominant fraction of CO luminosity and also because our radial bin has a wide width of 24$\ensuremath{''}$ ($\sim520$ pc).

The smaller vertical velocity dispersion in more massive clouds ($>$ 5 $\times$ 10$^5$ ${M}_{\odot}$) is similar to the tendency for clouds in the Solar neighborhood (cite: Stark1984VelDispersion). Massive clouds are scarce in the inter-arm regions, and thus, the reduced ${v_{\mathrm{res}}}$ dispersion in massive clouds suggests that clouds in spiral arms are likely more settled near the galactic plane than inter-arm regions. Such a trend is also observed in the Galactic plane (cite: StarkLee2005) as the reduced scale height of clouds near the spiral arm.

# Discussion

We identified 5724 molecular clouds from the $^{12}$CO (1–0) data of M83 with a spatial resolution of $\sim$46 pc, and found a median ${\alpha_{\mathrm{vir}}}$ of 2.7 (§[3.1](#SubsecCloudPropDistribution)) and a median $\Sigma$ of $\sim$20 ${M}_{\odot}\ \mathrm{pc}^{-2}$ assuming a Galactic CO-to-H2 conversion factor of 2.0 $\times$ 10$^{20}$ cm$^{-2}$ (K $\mathrm{km\ s}^{-1}$)$^{-1}$. Some of the recent cloud studies suggest that most molecular clouds are at most loosely bound by self-gravity, with ${\alpha_{\mathrm{vir}}}$ a factor of a few higher than 1 (cite: Heyer2001OuterGalaxy; Dobbs2011NotBound; MivilleDeschenes2017MWGMC; Sun2020; Evans2021BoundCloud) and also have a wide range of variation in $\Sigma$ (cite: Heyer2001OuterGalaxy; MivilleDeschenes2017MWGMC; Lada2020MassSizeRelation; Sun2020). At first glance, the median ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ agree with these recent results and suggestions. However, we take a step back to consider the possible impact of insufficient spatial resolution on the measured cloud properties. This assessment is needed because while the median of the sampled cloud masses is $\sim$1.9 $\times$ 10$^5$ ${M}_{\odot}$, the utilized $\sim$46 pc spatial resolution is larger than the sizes of the Galactic GMCs at a similar mass (cite: Sanders1985).

We organize the discussion as follows. In §[6.1](#SubsecDiscussionBeamDilutionFormulate), we discuss how the $\sim46$ pc beam affects cloud properties, in particular ${\alpha_{\mathrm{vir}}}$ and $\Sigma$, via a variation in the area-filling factor of clouds. Next, in §[6.2](#SubsecDiscussionFillingFactorCorrectedProps), we argue the possible range of the area-filling factor and intrinsic cloud properties considering the sensitivity of the observational data. In §[6.3](#SubsecDiscussionImplication), we discuss the implications of this section.

## Impact of sampling clouds with a relatively large beam

We consider the relations between intrinsic and observed parameters of the clouds affected by the effects of a limited resolution. When clouds are sampled with marginal resolution and SNR, measured cloud sizes could be overestimated even when the beam deconvolution (§[2.3.1](#SubsecBasicProps)) is made (cite: Rosolowsky2006CPROPS). This over-estimation would arise as a consequence of the SNR thresholding imposed during the cloud identification process, as only positive value pixels are included in cloud masks, and thus, the presence of noise tends to bias the measured cloud sizes toward larger values. For a cloud located in a crowded region, blending of emissions from the surrounding material also leads to the overestimation of cloud sizes. The observed distribution of $R_{\mathrm{eff}}$ appears to imply the sign of the over-estimation of radii, as over 80 percent of the clouds have $R_{\mathrm{eff}}$ larger than 40 pc §[3.1.3](#SubsubsecVDispAndRadius), which is approximately the resolution limit [^3]. The velocity dispersion $\sigma_{\mathrm{v}}$ could be similarly affected by the resolution bias, but the observed values of $\sigma_{\mathrm{v}}$ are well above the resolution limit §[3.1.3](#SubsubsecVDispAndRadius), suggesting $\sigma_{\mathrm{v}}$ is less affected. Therefore, we consider that the resolution bias mostly affects $R_{\mathrm{eff}}$ for the M83 catalog. This is also supported by the bootstrap error estimation made in §[2.3.1](#SubsecBasicProps), which indicates significantly larger fractional uncertainties on $R_{\mathrm{eff}}$ than $\sigma_{\mathrm{v}}$.

From the nature of the data considered here, we assume that the beam dilution affects the observed cloud radius $R_{\mathrm{eff}}$ such that it overestimates the intrinsic radius ${R_{{0}}}$, but does not affect the velocity dispersion $\sigma_{\mathrm{v}}$. We also assume that cloud mass ${M}_{\mathrm{cl}}$ is unaffected. When observing a cloud with a larger beam, the cloud emission is diluted, and thus, the observed brightness temperature is lowered, but the luminosity, and hence cloud mass ${M}_{\mathrm{cl}}$, should be preserved to the first order.

Under the assumed simplified configuration, the relation between the observed and intrinsic radii is $$\begin{equation}
R_{\mathrm{eff}}= {{f}}^{-1/2} {R_{{0}}},
\label{EqRFilling}
\end{equation}$$ where ${{f}}$ is the area-filling factor, the intrinsic-to-observed area ratio. By definition, ${{f}}$ is $\le$ 1.

The cloud surface mass density $\Sigma$ is affected by the beam dilution as it is dependent on $R_{\mathrm{eff}}$. The relation between the intrinsic ${\Sigma_{{0}}}$ and the observed $\Sigma$ is $$\begin{equation}
\Sigma= {{f}}{\Sigma_{{0}}}.
\label{EqSigmaFilling}
\end{equation}$$

The virial parameter ${\alpha_{\mathrm{vir}}}$ depends on $R_{\mathrm{eff}}$ as ${\alpha_{\mathrm{vir}}}$ $\propto$ $R_{\mathrm{eff}}\sigma_{\mathrm{v}}^2$. Denoting the intrinsic value of ${\alpha_{\mathrm{vir}}}$ as ${\alpha_{\mathrm{vir,0}}}$, from eq. ([\[EqMVirDef\]](#EqMVirDef)), eq. ([\[EqAlphaVirDef\]](#EqAlphaVirDef)), and eq. ([\[EqRFilling\]](#EqRFilling)), the relation between ${\alpha_{\mathrm{vir}}}$ and ${\alpha_{\mathrm{vir,0}}}$ is $$\begin{equation}
{\alpha_{\mathrm{vir}}}= {\alpha_{\mathrm{vir,0}}}{{f}}^{-1/2}.
\label{EqAlphaVirWithFillingFactor}
\end{equation}$$ As ${{f}}$ is $\le$ 1 by definition, ${\alpha_{\mathrm{vir}}}$ is elevated as ${{f}}^{-1/2}$. For example, suppose a bound cloud with ${R_{{0}}}=10$ pc and ${\alpha_{\mathrm{vir,0}}}$ = 1. With a spatial resolution of $\sim46$ pc, ${{f}}$ is $\sim$0.1 and thus, the observed ${\alpha_{\mathrm{vir}}}$ is elevated to $\sim$3.1, which would apparently indicate that the cloud is unbound even though its intrinsic ${\alpha_{\mathrm{vir,0}}}$ is 1.

Figure [11](#FigAlphaToSigma) shows the relationship between the observed ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ for the M83 clouds. The plot exhibits a solid declining trend of ${\alpha_{\mathrm{vir}}}$ toward higher $\Sigma$. This decline is consistent with the trend expected by a variation in ${{f}}$ made by the beam dilution. We re-write eq. ([\[EqAlphaVirWithFillingFactor\]](#EqAlphaVirWithFillingFactor)) by casting eq. ([\[EqSigmaFilling\]](#EqSigmaFilling)) to eliminate ${{f}}$: $$\begin{equation}
{\alpha_{\mathrm{vir}}}= {\alpha_{\mathrm{vir,0}}}\left({\Sigma_{{0}}}/ \Sigma\right)^{1/2},
\label{EqAlphaSigma}
\end{equation}$$ where $\Sigma$ $\le$ ${\Sigma_{{0}}}$. If clouds share a combination ${\Sigma_{{0}}}$ and ${\alpha_{\mathrm{vir,0}}}$ similar to each other, their observed ${\alpha_{\mathrm{vir}}}$ should decrease as $\propto$ $\Sigma^{-1/2}$. The dashed lines in figured [11](#FigAlphaToSigma) show the expected variation of the observed ${\alpha_{\mathrm{vir}}}$ for clouds in a simple virial equilibrium (${\alpha_{\mathrm{vir,0}}}$=1) with three different ${\Sigma_{{0}}}$ of 40, 160, and 640 ${M}_{\odot}\ \mathrm{pc}^{-2}$. Most clouds are distributed along these lines, and moreover, over half of the clouds are located within a factor of 4 variations around ${\Sigma_{{0}}}=$160 ${M}_{\odot}\ \mathrm{pc}^{-2}$. Notably, 160 ${M}_{\odot}\ \mathrm{pc}^{-2}$ is close to the average surface density of 200 ${M}_{\odot}\ \mathrm{pc}^{-2}$ implied from Larson’s relations (cite: HeyerDame2015Review).

A caveat is that the formulation made here is based on a crude approximation that the resolution effect mostly affects $R_{\mathrm{eff}}$, but not $\sigma_{\mathrm{v}}$ and ${M}_{\mathrm{cl}}$. In Appendix [8](#SimSourceInjection), we verify this approximation with a source injection test.

The cloud distribution on the ${\alpha_{\mathrm{vir}}}$-$\Sigma$ plane suggests that the intrinsic virial parameter and surface density may be more uniform than the observed ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ apparently tell. This also suggests the need to consider the effect of the beam dilution when interpreting the observed variations in ${\alpha_{\mathrm{vir}}}$ and $\Sigma$.

## Distribution of filling factor and intrinsic cloud properties

In the previous subsection, we showed that the observed spread of the virial parameter and surface mass density can be explained, at least partly, by the beam dilution. Their intrinsic ${\alpha_{\mathrm{vir,0}}}$ and ${\Sigma_{{0}}}$ are potentially more uniform than they appear from ${\alpha_{\mathrm{vir}}}$ and $\Sigma$. Here, we discuss the potential fraction of the clouds compatible with this possibility and estimate the distribution of intrinsic cloud properties. We address these questions by first defining a criterion to select clouds for which the discussion on the beam-dilution effect is applicable in §[6.2.1](#SubsubsecCriterion), and following in §[6.2.2](#SubsubsecCorrectedProperties), we discuss the intrinsic cloud properties after the correction for ${{f}}$.

### Criterion to select clouds for filling factor estimation

In the previous sub-section, we discussed the ${{f}}$-dependence of the observed cloud properties. Here, we crudely estimate ${{f}}$ for each cloud by comparing the observed ${\alpha_{\mathrm{vir}}}$ with an assumed value of ${\alpha_{\mathrm{vir,0}}}$ using eq. ([\[EqAlphaVirWithFillingFactor\]](#EqAlphaVirWithFillingFactor)). This procedure should apply only to clouds with a simple/single structure that can be approximated with a single temperature when observed at the current resolution and thus are describable with a single ${{f}}$.

To select such clouds, we define a peak-equivalent temperature, or simply equivalent temperature, $T_{\mathrm{eq}}$. By using the cloud’s CO luminosity ${L}_{\mathrm{CO}}$ and assuming a Gaussian spectral profile, $$\begin{equation}
T_{\mathrm{eq}}= {L}_{\mathrm{CO}}/ \left[ \sqrt{2 \pi} \sigma_{\mathrm{v}}\left( \pi R_{\mathrm{eff}}^2 \right ) \right].
\label{EqEquivalentPeakTemperature}
\end{equation}$$ Note that if the line profile of a cloud is a single Gaussian (i.e., if the cloud’s observed emission has a simple structure characterized by a single temperature), then $T_{\mathrm{eq}}$ $\sim$ $T_{\mathrm{peak}}$. As we adopted the 4 $\sigma$ detection threshold of $T_{\mathrm{peak}}$ $\gtrsim$ 0.5 K (§[2.2](#SubsecIdentify)), clouds that agree with the single-component approximation should have $T_{\mathrm{eq}}$ $>$ 0.5 K. Therefore, we adopt $T_{\mathrm{eq}}$ $>$ 0.5 K as a criterion to select clouds to estimate ${{f}}$.

We plot $T_{\mathrm{eq}}$ vs. $T_{\mathrm{peak}}$ in figure [12](#FigTavgTpeak) with $R_{\mathrm{eff}}$ color-coded. Smaller clouds are closer to the line of $T_{\mathrm{eq}}$ = $T_{\mathrm{peak}}$, and larger clouds deviate downward toward $T_{\mathrm{eq}}$ $<$ $T_{\mathrm{peak}}$. This trend is expected because smaller clouds are more likely to have a simple appearance when convolved by the beam The plot indicates that the clouds with $T_{\mathrm{eq}}$ $>$ 0.5 K mostly have $T_{\mathrm{eq}}$ $\sim$ $T_{\mathrm{peak}}$, although with modest deviations of up to a factor of 3, hinting that our criterion indeed selects the clouds that can be approximated with a single temperature under the current resolution.

### Estimation of intrinsic cloud properties

We estimate ${{f}}$ for each cloud by casting an assumed value of ${\alpha_{\mathrm{vir,0}}}$ into eq. ([\[EqAlphaVirWithFillingFactor\]](#EqAlphaVirWithFillingFactor)). We adopt two values of ${\alpha_{\mathrm{vir,0}}}$, 1 (virialized clouds) and 2 (loosely gravitationally-bound clouds). If a cloud’s ${\alpha_{\mathrm{vir}}}$ is less than the assumed ${\alpha_{\mathrm{vir,0}}}$, then ${{f}}$ is capped at 1. Although this procedure allows us to derive ${{f}}$ for all the clouds in M83, we regard the derived values of ${{f}}$ to be “valid" only for clouds with $T_{\mathrm{eq}}$ $>$ 0.5 K, i.e., clouds that are compatible with the single-component approximation. The ${{f}}$ values for clouds with $T_{\mathrm{eq}}$ $<$ 0.5 K are presented just for reference. We also note the derivation of ${{f}}$ involves the assumptions of a constant CO-to-H$_{2}$ conversion factor and dominance of H$_{2}$ in the cloud masses.

Figure [13](#FigEstimatedF)(a) shows the distribution of ${{f}}$. The solid lines indicate the “valid" ${{f}}$ values derived from the clouds compatible with the single-component approximation by assuming ${\alpha_{\mathrm{vir,0}}}=$1 (black) and 2 (green), respectively. As for reference, the dashed lines indicate ${{f}}$ for all clouds, which include “invalid" values derived from the clouds incompatible with the single-component approximation. Although the distribution of “valid" ${{f}}$ extends down to $\sim$0.01, it is chiefly between 0.1 and 1, as the 16th percentile is $\sim$0.07 ($\sim0.13$) for ${\alpha_{\mathrm{vir,0}}}$ of 1 (2).

The minimum value of ${{f}}\sim$0.1 is seemingly consistent with the detection limit of the clouds. For example, if we suppose a typical cloud with an intrinsic brightness temperature of 8 K [^4], the observed peak brightness temperature would be 0.5 K if ${{f}}$ is 0.1. As our cloud-finding procedure adopted 0.5 K as the detection limit, it is consistent that the lower limit of the estimated ${{f}}$ is around 0.1.

Figure [13](#FigEstimatedF)(b) is the same as figure [13](#FigEstimatedF)(a) but shows in the cumulative number form. On the plot, the fractional number of clouds with ${{f}}=1$ for a particular value of ${\alpha_{\mathrm{vir,0}}}$ indicates the fractional number of clouds with their observed ${\alpha_{\mathrm{vir}}}$ less than the adopted ${\alpha_{\mathrm{vir,0}}}$; about 12 (24) percent of the clouds indicate ${{f}}=$1 with ${\alpha_{\mathrm{vir,0}}}$ of 1 (2). Therefore, if the area-filling factor were not considered, we would be led to the conclusion that only a small number of clouds, less than about 20 percent, are gravitationally bound. However, contrary to this small fractional number, a majority of clouds ($\sim$57 percent) are compatible with the single-component approximation as $T_{\mathrm{eq}}$ $>$ 0.5 K. We saw that the ${{f}}$ values estimated for such clouds by assuming ${\alpha_{\mathrm{vir,0}}}$ of 1 (or 2) are consistent with the sensitivity limit of the observation; therefore, we deduce that more than half of the clouds in number are potentially bound, i.e., ${\alpha_{\mathrm{vir,0}}}< 2$ if we accept a variation in ${{f}}$.

The increase of the fraction of bound cloud by taking ${{f}}$ into account is also prominent on a mass basis. Figure [13](#FigEstimatedF)(c) shows the fractional cumulative mass distribution of ${{f}}$. About 47 (64) percent of the clouds have the observed ${\alpha_{\mathrm{vir}}}$ less than 1 (2), as seen from the cloud numbers with ${{f}}=1$. Allowing a change in ${{f}}$, most of the cloud mass ($\sim90$ percent) is explainable as being bound.

The derived ${{f}}$, if they are correct, provide the intrinsic cloud properties. We derive ${\Sigma_{{0}}}$ and ${R_{{0}}}$ from $\Sigma$ and $R_{\mathrm{eff}}$ using eq. ([\[EqRFilling\]](#EqRFilling)) and eq. ([\[EqSigmaFilling\]](#EqSigmaFilling)). Also, we derive the intrinsic peak brightness temperature of cloud $T_{{0}}$ as $$\begin{equation}
\label{EqTFilling}
T_{{0}}= T_{\mathrm{peak}}{{f}}^{-1}.
\end{equation}$$ Figure [14](#FigEstimatedIntProps)(a–c) show the distributions of ${\Sigma_{{0}}}$, ${R_{{0}}}$, and $T_{{0}}$. In each panel, the solid line indicates the ${{f}}$-corrected estimates derived assuming ${\alpha_{\mathrm{vir,0}}}=$1 (black) and 2 (green), respectively, for the nearly “single-component" clouds with $T_{\mathrm{eq}}$ $>$ 0.5 K. The uncorrected observed values, namely $\Sigma$, $R_{\mathrm{eff}}$, and $T_{\mathrm{peak}}$, are also shown for the nearly “single-component" clouds and whole cloud samples with gray dashed and dotted lines, respectively.

Figure [14](#FigEstimatedIntProps)(a) shows that ${\Sigma_{{0}}}$ is in a narrow range. The median ${\Sigma_{{0}}}$ is $\sim$150 ($\sim90$) for ${\alpha_{\mathrm{vir,0}}}$ of 1 (2), with a spread of $\sim0.3$ dex ($1\sigma$). These median and narrow ranges in ${\Sigma_{{0}}}$ are similar to the values derived by S87 for the Galactic GMCs. The estimation of the surface density is vastly different before the filling factor correction: the uncorrected $\Sigma\sim40$ ${M}_{\odot}\ \mathrm{pc}^{-2}$ with a much wider spread.

Figure [14](#FigEstimatedIntProps) (b)(c) show ${R_{{0}}}$ and $T_{{0}}$. The medians are ${R_{{0}}}\sim30$ pc ($\sim40$ pc) and $T_{{0}}\sim3.7$ K ($\sim2.3$ K) and for the assumed ${\alpha_{\mathrm{vir,0}}}$ of 1 (2). These values of ${R_{{0}}}$ and $T_{{0}}$ are similar to the typical radii and kinetic temperature (peak brightness temperature) of Galactic GMCs (cite: Sanders1985), supporting the consistency of the filling-factor estimation.

We also show the environmental variation of ${\Sigma_{{0}}}$ in figure ([15](#FigEstimatedIntPropsByRegion)). The environmental mask defined in §[3.3](#SubsecSpatialDistribution) is used here. The medians in the arm and inter-arm regions are $\sim$170 ($\sim96$) ${M}_{\odot}\ \mathrm{pc}^{-2}$ and $\sim$120 ($\sim95$) ${M}_{\odot}\ \mathrm{pc}^{-2}$, respectively, for the assumed ${\alpha_{\mathrm{vir,0}}}$ of 1 (2). The 1 $\sigma$ scatter is only about 0.3 dex for each. In the bar and center regions, ${\Sigma_{{0}}}$ is elevated compared to the arm/inter-arm regions with medians of $\sim270$ ${M}_{\odot}\ \mathrm{pc}^{-2}$ and $\sim770$ ${M}_{\odot}\ \mathrm{pc}^{-2}$, respectively. Thus, the cloud properties vary depending on the environments; the inter-arm clouds have lower ${\Sigma_{{0}}}$, or higher ${\alpha_{\mathrm{vir,0}}}$, compared to the arm clouds, and the disk clouds have lower ${\Sigma_{{0}}}$ than the clouds in the central region.

Finally, we compare the filling-factor corrected intrinsic cloud properties with the uncorrected plain values on Larson’s scaling relations. Figure [16](#FigSclRelationIntProps)(a) compares the corrected relationship, $\sigma_{\mathrm{v}}$–${R_{{0}}}$, with the uncorrected $\sigma_{\mathrm{v}}$-$R_{\mathrm{eff}}$, and figure [16](#FigSclRelationIntProps)(b) compares ${M}_{\mathrm{cl}}$–${R_{{0}}}$ with ${M}_{\mathrm{cl}}$–$R_{\mathrm{eff}}$. The clouds with $T_{\mathrm{eq}}$ $>$ 0.5 K are shown, and we here assumed ${\alpha_{\mathrm{vir,0}}}$ of 1. From the near constancy of ${\Sigma_{{0}}}$ obtained by assuming a constant ${\alpha_{\mathrm{vir,0}}}$ (figure [14](#FigEstimatedIntProps)), we would expect that the filling-corrected intrinsic cloud properties follow Larson’s scaling relations, and both plots show that the expectation is the case. Figure [16](#FigSclRelationIntProps) also plots the distribution density of S87’s data points. M83’s data points have a larger scatter than S87’s points, for which the environmental variation of ${\Sigma_{{0}}}$ seen in figure [15](#FigEstimatedIntPropsByRegion) should be at least partly responsible.

## Implications

The observed ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ vary over wide ranges in the M83 clouds (§[3.1](#SubsecCloudPropDistribution)). The wide range of variations in ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ agree with some recent GMC studies (see references at the beginning of this section). However, we saw that the ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ in the M83 clouds are distributed approximately along the ${\alpha_{\mathrm{vir}}}$ $\propto$ $\Sigma^{-1/2}$ lines on the ${\alpha_{\mathrm{vir}}}$-$\Sigma$ plane (figure [11](#FigAlphaToSigma)), which are exactly in the direction of the beam dilution (along the change of ${{f}}$). Within the limitations of the current data, it seems conceivable that a significant fraction of the clouds in M83 is consistent with those studied by S87, having ${\alpha_{\mathrm{vir}}}\sim$1-2 and $\Sigma\sim$200 ${M}_{\odot}\ \mathrm{pc}^{-2}$, but being beam-diluted with ${{f}}\sim$0.1-1.0. Specifically, we found that a cloud population of up to $\sim$57% in number and $\sim$90% in mass are potentially in agreement with the intrinsic ${\alpha_{\mathrm{vir}}}$ of $1-2$ (figure [13](#FigEstimatedF)), and the intrinsic ${\Sigma_{{0}}}$ is near-constant around the median of $\sim150$ ($\sim90$) ${M}_{\odot}\ \mathrm{pc}^{-2}$ with ${\alpha_{\mathrm{vir,0}}}=1$ (2) for such clouds. Despite relatively large variations in $\Sigma$ and ${\alpha_{\mathrm{vir}}}$ suggested in some of the recent studies, discrete and bound clouds with a high and near constant $\Sigma$ as suggested by Larson’s relations might still be the dominant component in molecular disks.

The dependence of ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ on ${{f}}$ gives a caveat when interpreting these observed parameters. The relation between the size-normalized velocity dispersion $\sigma_{\mathrm{v}}/\sqrt{R_{\mathrm{eff}}}$ and $\Sigma$ is often used to visualize the dynamical stabilities of clouds, including the impact of the confinement by external pressure (cite: Field2011; Heyer2001OuterGalaxy; Sun2020DE). For clouds with a constant ${\alpha_{\mathrm{vir}}}$, $\sigma_{\mathrm{v}}/\sqrt{R_{\mathrm{eff}}}$ should scale as $\propto \Sigma^{1/2}$, but in §[3.2](#SubsecScalingRelations), we saw that it scaled as with a shallow index, $\propto \Sigma^{\sim0.3}$. The shallower index is explainable as the variation in ${{f}}$ (Appendix [9](#SecAppendixSizelinewidthCoeffSigma)). In addition, some studies note the strong mass-dependence of ${\alpha_{\mathrm{vir}}}$, which is mostly ${\alpha_{\mathrm{vir}}}$ $\propto$ ${M}_{\mathrm{cl}}^{-0.5}$ (cite: Chevance2023Review). At least for the M83 clouds presented here, the ${\alpha_{\mathrm{vir}}}$-${M}_{\mathrm{cl}}$ scaling is also explainable by the beam-dilution effect (Appendix [10](#SecAppendixAlphaVirM)).

The fact that the distribution of the ${{f}}$-corrected ${\Sigma_{{0}}}$ has a narrow range around 100-200 ${M}_{\odot}\ \mathrm{pc}^{-2}$ by assuming ${\alpha_{\mathrm{vir,0}}}$ of 1 (or 2) (§[6.2](#SubsecDiscussionFillingFactorCorrectedProps)) would imply that in many, but not all, molecular clouds, the CO luminosity and mass are potentially concentrated at a bound component with high surface densities of around 100 ${M}_{\odot}\ \mathrm{pc}^{-2}$.

We note that the concentration of cloud mass to $\Sigma$ of around 100 ${M}_{\odot}\ \mathrm{pc}^{-2}$ and ${\alpha_{\mathrm{vir}}}$ of $<2$ is also similarly seen in the distribution of the cloud properties inspected in §[3.1](#SubsecCloudPropDistribution): despite that the inter-cloud median of $\Sigma$ is as low as $\sim20$ ${M}_{\odot}\ \mathrm{pc}^{-2}$ and also that median ${\alpha_{\mathrm{vir}}}$ is 2.7, the mass-weighted average of $\Sigma$ of ${\alpha_{\mathrm{vir}}}$ are $\sim130$ ${M}_{\odot}\ \mathrm{pc}^{-2}$ and $\sim$1.1, respectively (§[3.1](#SubsecCloudPropDistribution)). This similarity would reinforce the implication that molecular gas material with high $\Sigma$, which is also strongly influenced by self-gravity, could be the dominant component of the molecular gas disk. It would also be of interest to investigate the internal distribution of $\Sigma$ and ${\alpha_{\mathrm{vir}}}$ within individual clouds to see whether the concentration of CO luminosity to possibly gravitationally bound and high $\Sigma$ components are universal property of molecular clouds not only on inter-cloud scale scales but also on sub-cloud scales.

# Summary

We identified molecular clouds over the whole disk of M83, with the $^{12}$CO (1–0) data from ALMA (cite: Koda2023M83). M83 is one of the closest molecular gas-rich spiral galaxies seen face-on, and it resembles the Milky Way in many aspects, including the existence of the stellar bar, multiple spiral arms, and its Solar-like metallicity. At a resolution of $\sim$46 pc and high mass sensitivity of $\sim$10$^4$ ${M}_{\odot}$, we sampled 5724 clouds. By assuming a uniform CO-to-H$_2$ conversion factor of 2.0 $\times$ 10$^{20}$ cm$^{-2}$ (K $\mathrm{km\ s}^{-1}$)$^{-1}$, the median cloud mass is $\sim$2$\times$10$^5$ ${M}_{\odot}$ (§[3.1](#SubsecCloudPropDistribution)), which is close to the median cloud mass found in the inner Galactic disk found by existing surveys (cite: MivilleDeschenes2017MWGMC) and also close to the lower end of a conventional definition of GMC mass range (cite: Sanders1985). This is a significant improvement because even up to recently, molecular cloud studies that sample clouds in extragalactic disks beyond the Local Group were often made with a spatial resolution of 50-100pc with a shallower sensitivity, with the median mass of sampled clouds being $\sim10^6$ ${M}_{\odot}$ or higher (cite: Colombo2014Env; Hirota2018M83; Rosolowsky2021PhangsGMCs).

The overall distributions of the cloud properties are examined in §[3.1](#SubsecCloudPropDistribution).

-  The median cloud mass is $\sim$1.9$\times$10$^5$ ${M}_{\odot}$, and the mass-weighted mean cloud mass is $\sim$1.8 $\times$ 10$^6$ ${M}_{\odot}$. The difference indicates that the CO luminosity and molecular gas mass of M83 are concentrated predominantly in massive clouds, similar to the MW disk’s cloud population. Specifically, clouds more massive than $>10^6$ ${M}_{\odot}$ are only $\sim13\%$ in cloud number but account for $\sim65\%$ of the total CO luminosity.

-  For a subset of clouds with a mass threshold of $10^6$ ${M}_{\odot}$, which roughly corresponds to the ones sampled by the previous clouds studies in extragalactic molecular-rich disks, the median surface mass density $\Sigma$ and virial parameter ${\alpha_{\mathrm{vir}}}$ are about 130 ${M}_{\odot}\ \mathrm{pc}^{-2}$ and 1.0, respectively.

-  Without any consideration of beam dilution, the observed median $\Sigma$ and ${\alpha_{\mathrm{vir}}}$ are 22 ${M}_{\odot}\ \mathrm{pc}^{-2}$ and 2.7, respectively, for M83 clouds. The observed median $\Sigma$ is much lower than the that of the clouds of S87 (cite: Solomon1987Larson; HeyerDame2015Review), but is comparable to those found in the recent Galactic studies, which extensively sampled clouds down to low-intensity threshold (cite: MivilleDeschenes2017MWGMC; Lada2020MassSizeRelation). Also, the observed median ${\alpha_{\mathrm{vir}}}$ is similar to the values found in recent extragalactic studies, including PHANGS (cite: Sun2020; Rosolowsky2021PhangsGMCs). However, we caution that the observed median values of ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ in M83 are potentially subject to the beam filling factor as discussed in §[6](#SecDiscussion).

The scaling relations of cloud properties (§[3.2](#SubsecScalingRelations)), spatial distributions (§[3.3](#SubsecSpatialDistribution)), mass distributions (§[4](#SecMF)), and cloud-to-cloud velocity dispersion (§[5](#SecVelDisp)) are examined.

- *Scaling relations*: The observed cloud properties are compared with the scaling relations of (cite: Solomon1987Larson), namely the velocity dispersion to size, virial mass to CO luminosity, and mass to size relationships. Although the ${M}_{\mathrm{vir}}$-${L}_{\mathrm{CO}}$ relationship shows an apparent correlation with a correlation coefficient of 0.78, the signs of correlation are hardly seen for the other two relations. Still, bright clouds selected with $T_{\mathrm{peak}}>2$ K, which comprise about 20 percent of the clouds, are more aligned with Larson’s relations.

- *Normalized cloud velocity to surface mass density relation*: We see a correlation between the size-normalized velocity dispersion $\sigma_{\mathrm{v}}/\sqrt{R_{\mathrm{eff}}}$ and $\Sigma$, which is expected for clouds influenced by self-gravity (cite: Heyer2009; BallesterosParedes2011A). However, clouds with low $\Sigma$ exhibit upward deviations and fitting of the data yielded $\sigma_{\mathrm{v}}/\sqrt{R_{\mathrm{eff}}} \propto \Sigma^{\sim0.3}$, which is shallower than $\propto$ $\Sigma^{1/2}$ expected for bound clouds with a uniform ${\alpha_{\mathrm{vir}}}$.

- *Spatial distribution of clouds*: Clouds more massive than 10$^6$ ${M}_{\odot}$ are strongly concentrated around bright galactic structures, such as the spiral arms, bar, and center. Smaller clouds are more prevalent in the inter-arm regions. We fitted the distributions of the massive clouds as logarithmic arms and produced a regional mask.

- *Mass function*: Mass distributions of the identified clouds are examined and fitted with two functional forms: the power-law form, widely used in cloud studies, and a modified power-law with exponential cutoff (Schechter-like form). The fit with the power-law form yields an index ${\gamma_{\mathrm{PL}}}$ of $\sim$-1.9, while the fit with the Schechter-like form yields ${\gamma_{\mathrm{exp}}}$ of $\sim$-1.5. Both forms provide the upper cutoff mass at around $\sim$8.0 $\times$ 10$^6$ ${M}_{\odot}$. Radial variations of the mass distributions are also examined by dividing the galactic disks into five radial bins. Steepening of the slopes of mass functions is implied from the radial variations of ${\gamma_{\mathrm{PL}}}$, but not with ${\gamma_{\mathrm{exp}}}$.

- *Cloud-to-cloud velocity dispersion*: Taking advantage of the face-on inclination of M83, the vertical cloud-to-cloud velocity dispersion is estimated. Outside of the central 2.2 kpc, the estimated vertical dispersion is $\sim$8.3 $\mathrm{km\ s}^{-1}$ and $\sim$11 $\mathrm{km\ s}^{-1}$ for clouds above and below 5$\times$10$^5$ ${M}_{\odot}$, respectively.

In §[6](#SecDiscussion), we discussed the possible impact of beam dilution on the cloud properties. In particular, the dependence of the observed values of virial parameter and surface density (${\alpha_{\mathrm{vir}}}$ and $\Sigma$) on area-filling factor ${{f}}$ was discussed.

-  The observed ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ are distributed approximately along ${\alpha_{\mathrm{vir}}}$ $\propto$ $\Sigma^{-1/2}$. As a hypothetical consideration, we suggest this tendency is explainable as the effect of beam dilution. If a cloud’s beam-convolved emission distribution is simple enough to be approximated as a single component, the relations between the observed and intrinsic values are $\Sigma$ = ${{f}}$ ${\Sigma_{{0}}}$ and ${\alpha_{\mathrm{vir}}}$ = ${\alpha_{\mathrm{vir,0}}}$ ${{f}}^{-1/2}$.

-  We devised a temperature criterion to select clouds compatible with the single-component approximation, which is the prerequisite to assume the ${{f}}$ dependence of ${\alpha_{\mathrm{vir}}}$. For the selected clouds with the criterion, we estimated the values of ${{f}}$ for each cloud by assuming that they are intrinsically bound with ${\alpha_{\mathrm{vir,0}}}$ of $\le2$ and found that ${{f}}$ of the clouds is mostly between 0.1 and 1. In this way, up to $\sim57$ percent of the clouds in number, or $\sim90$ percent of the cloud masses in M83’s disk, are compatible with the assumed ${\alpha_{\mathrm{vir,0}}}$. Also, the estimated intrinsic ${\Sigma_{{0}}}$ for such clouds are found to concentrate around $150$ ${M}_{\odot}\ \mathrm{pc}^{-2}$ if the intrinsic ${\alpha_{\mathrm{vir,0}}}$ of 1 is assumed, or 90 ${M}_{\odot}\ \mathrm{pc}^{-2}$ if the intrinsic ${\alpha_{\mathrm{vir,0}}}$ of 2 is assumed. The combination of ${\alpha_{\mathrm{vir,0}}}$ and ${\Sigma_{{0}}}$ resemble the clouds found by S87, suggesting that such bound and discrete clouds are potentially the dominant component in a MW-type disk of M83.

This paper makes use of the following ALMA data: ADS/JAO. ALMA#2017.1.00079.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This research made use of astrodendro, a Python package to compute dendrograms of Astronomical data (http://www.dendrograms.org/). This research made use of APLpy, an open-source plotting package for Python hosted at http://aplpy.github.com. LCH was supported by the National Science Foundation of China (11991052, 12011540375, 12233001), the National Key R&D Program of China (2022YFF0503401), and the China Manned Space Project (CMS-CSST-2021-A04, CMS-CSST-2021-A06).

# Facilities

ALMA

# Software

astrodendro (cite: Robitaille2019), scikit-image (cite: vanDerWalt2014ScikitImage), matplotlib (cite: Hunter2007Matplotlib), emcee (cite: ForemanMackey2013emcee)

# Source injection test

The observed virial parameter ${\alpha_{\mathrm{vir}}}$ of the clouds in M83 exhibits a trend, which is approximately ${\alpha_{\mathrm{vir}}}$ $\propto$ $\Sigma^{-0.5}$ (figure [11](#FigAlphaToSigma)). In §[6.1](#SubsecDiscussionBeamDilutionFormulate), we argued that this trend possibly owes to a variation in the area-filling factor, driven by the overestimation of cloud radius $R_{\mathrm{eff}}$ for clouds smaller than the beam. We assumed there that (1) the resolution effect overestimates $R_{\mathrm{eff}}$ but does not affect the velocity dispersion $\sigma_{\mathrm{v}}$ and mass ${M}_{\mathrm{cl}}$ of clouds and that (2) the $R_{\mathrm{eff}}$ overestimation is coupled with the decrease of the area-filling factor of the beam (eq. [\[EqRFilling\]](#EqRFilling)). We test these assumptions with a simulation test, which injects model sources with known properties into a portion of the data cube and samples the injected sources via the same identification procedure utilized in §[2](#SecIdentify).

## Procedure

The test is made with two setups. A $\sim0.8$ kpc$^2$ segment of M83 is used as the target field in both setups. Within the field, CO emission from M83 mostly resides within the LSR velocity range between 410 $\mathrm{km\ s}^{-1}$ and 455 $\mathrm{km\ s}^{-1}$. The two setups are configured with different velocity ranges as follows.

-  *Noise-only* setup: A CO emission-free velocity range of from 340 $\mathrm{km\ s}^{-1}$ to 409$\mathrm{km\ s}^{-1}$ is used. This setup is used to see the impact of the noise on the cloud property measurements.

-  *Blended* setup: The velocity range between 401 $\mathrm{km\ s}^{-1}$ and 470 $\mathrm{km\ s}^{-1}$ is used to assess the combined impact of the noise and blending of CO emission surrounding the input sources.

Input model clouds are generated by assuming a Gaussian profile in both spatial and velocity directions. For each model cloud, ${M}_{\mathrm{cl}}$ is given as a parameter and $R_{\mathrm{eff}}$ and $\sigma_{\mathrm{v}}$ are determined by setting ${\alpha_{\mathrm{vir}}}$ as 1.5 and $\Sigma$ as 100 ${M}_{\odot}\ \mathrm{pc}^{-2}$, respectively. Five model clouds with ${M}_{\mathrm{cl}}$ of 0.5, 1, 2, 4, and 8 $\times$ 10$^5$ ${M}_{\odot}$ are generated and convolved to emulate the spatial resolution of $\sim$46 pc and velocity channel of 1 $\mathrm{km\ s}^{-1}$. In each round of the test, the model clouds are injected into the random positions within the data cube with an imposed minimum spacing of 80 pc. For the *noise-only* setup, a constant receding velocity of 375 $\mathrm{km\ s}^{-1}$ is assigned to the clouds. For the *blended* setup, the receding velocity of each cloud is determined such that it is offset by 12 $\mathrm{km\ s}^{-1}$ from the median velocity of the existing CO emission around the cloud. The offset velocity of 12 $\mathrm{km\ s}^{-1}$ is comparable to the RMS cloud-to-cloud velocity dispersion in the M83 clouds (§[5](#SecVelDisp)). From the source-added data cube, clouds are identified using the procedure described in §[2](#SecIdentify) and cross-matched with the input model clouds with a matching tolerance of half the FWHM cloud size in both spatial and velocity directions. The injection-identification sequence is repeated 40 times for each setup.

## Simulation results

Figure [17](#FigSimAlphaVirOff) and figure [18](#FigSimAlphaVirOn) show the test results for *noise-only* and *blended* setups, respectively. In the *noise-only* setup, the input sources are detected with high detection rates. The rate is 100 percent for the input ${M}_{\mathrm{cl}}$ of $>10^5$ ${M}_{\odot}$ and slightly lowers to $\sim80$ percent at 5$\times$10$^4$ ${M}_{\odot}$. These high recovery rates are in accordance with the minimum cloud mass of $\sim3$ $\times$ $10^4$ ${M}_{\odot}$, estimated for uncrowded regions in §[2.6](#SubsecCOLumFraction). Figure [17](#FigSimAlphaVirOff)(c), [17](#FigSimAlphaVirOff)(d), and [17](#FigSimAlphaVirOff)(e) show the ratios between the output-to-input values of ${M}_{\mathrm{cl}}$, $R_{\mathrm{eff}}$, and $\sigma_{\mathrm{v}}$. At the lower mass range, $R_{\mathrm{eff}}$ shows a significant increase in the output-to-input ratio while the ratios for ${M}_{\mathrm{cl}}$ and $\sigma_{\mathrm{v}}$ are more stable around 1. Figure [17](#FigSimAlphaVirOff)(f) shows the ${\alpha_{\mathrm{vir}}}$-$\Sigma$ plot derived from the output properties of the detected sources. As a consequence of $R_{\mathrm{eff}}$ overestimation at lower ${M}_{\mathrm{cl}}$, a trend of ${\alpha_{\mathrm{vir}}}$ $\propto$ $\Sigma^{-0.5}$ appears despite the input sources uniformly have ${\alpha_{\mathrm{vir}}}$ of 1.5 and $\Sigma$ of 100 ${M}_{\odot}\ \mathrm{pc}^{-2}$.

In the *blended* setup, the recovery rates are lower than the *noise-only* setup in all the mass ranges, with larger drops in smaller cloud masses. The rates are above 60 percent with input ${M}_{\mathrm{cl}}$ of $>2$ $\times$ $10^5$ ${M}_{\odot}$, roughly in agreement with the effective completeness limit suggested from the cloud mass spectra §[4](#SecMF). The trend of $R_{\mathrm{eff}}$ overestimation is more prominent in the *blended* setup (figure [18](#FigSimAlphaVirOn)d). In particular, the median output-to-input ratios of $R_{\mathrm{eff}}$ approximately follow the line of $\theta_{\mathrm{b}}/\theta_{\mathrm{source}}$ at lower ${M}_{\mathrm{cl}}$ of $<2\times10^5$ ${M}_{\odot}$. The ${\alpha_{\mathrm{vir}}}$-$\Sigma$ plot for the *blended* setup shown in figure [18](#FigSimAlphaVirOn)(f) again shows a trend in agreement with ${\alpha_{\mathrm{vir}}}$ $\propto$ $\Sigma^{-0.5}$ as in the *noise-only* setup.

As the CO emission widely prevails over the disk of M83, the *blended* setup would be more representative of the uncertainty trends in the M83 catalog than the *noise-only* setup. The blended setup indicates that the $R_{\mathrm{eff}}$ measurement tends to derive the beam size as cloud size in crowded environments despite the beam size deconvolution. As the overestimated cloud size is comparable to beam size, the intrinsic and observed cloud radii are associated with each other by the beam filling factor, as in eq. [\[EqRFilling\]](#EqRFilling). In addition, the trend of ${\alpha_{\mathrm{vir}}}$ $\propto$ $\Sigma^{-0.5}$ seen with the model clouds with a uniform combination of ${\alpha_{\mathrm{vir}}}$ and $\Sigma$ suggests that, to the first order, the impact of beam dilution on $\sigma_{\mathrm{v}}$ and ${M}_{\mathrm{cl}}$ are more moderate compared to $R_{\mathrm{eff}}$.

# Filling factor dependence seen in size-normalized velocity dispersion to surface density relation

The relation between the size-normalized velocity dispersion $C$ ($\equiv$ $\sigma_{\mathrm{v}}/\sqrt{R}$) and surface mass density $\Sigma$ is often used to gauge the dynamical state of clouds (cite: Heyer2009; BallesterosParedes2011A). As ${M}_{\mathrm{vir}}$ $\left( \propto R \sigma_{\mathrm{v}}^2 \right)$ = ${\alpha_{\mathrm{vir}}}$ ${M}_{\mathrm{cl}}$ is mathematically equivalent to $\sigma_{\mathrm{v}}^2/R$ $\propto$ ${\alpha_{\mathrm{vir}}}\Sigma$, clouds with a constant ${\alpha_{\mathrm{vir}}}$ should follow a line on the $\sigma_{\mathrm{v}}/\sqrt{R} - \Sigma$ plane following equation ([\[EqSizeLinewidthCoeff\]](#EqSizeLinewidthCoeff)).

We saw in §[3.2](#SubsecScalingRelations) that a majority of the M83 clouds are located upward of the line expected for ${\alpha_{\mathrm{vir}}}$ = 1 on the $\sigma_{\mathrm{v}}/\sqrt{R}$–$\Sigma$ plot. The clouds with such upward deviations are often considered to be confined by external pressure (cite: Heyer2009; Field2011; Sun2020DE), but we also saw that the deviations are rather systematic; the fitted relation indicated that $\sigma_{\mathrm{v}}/\sqrt{R}$ varies as $\propto$ $\Sigma^{\sim0.3}$ (eq. [\[EqSizeLinewidthCoeffSigmaRelationFit\]](#EqSizeLinewidthCoeffSigmaRelationFit)), although $\Sigma^{1/2}$ is expected for a constant value of ${\alpha_{\mathrm{vir}}}$ (eq. [\[EqSizeLinewidthCoeff\]](#EqSizeLinewidthCoeff)).

The observed index of $\sim0.3$ for the $\sigma_{\mathrm{v}}/\sqrt{R}$–$\Sigma$ relation is explainable with the beam-dilution effect if a significant fraction of the clouds share a similar set of combinations of the intrinsic virial parameter and surface mass density. Consider a cloud with intrinsic radius ${R_{{0}}}$, surface mass density ${\Sigma_{{0}}}$, virial parameter ${\alpha_{\mathrm{vir,0}}}$, and velocity dispersion $\sigma_{\mathrm{v}}$. As we assume the beam dilution does not affect the velocity dispersion, $\sigma_{\mathrm{v}}$ does not have a subscription. If the cloud follows Larson’s relations, the following applies to the cloud,

$$\begin{equation}
\sigma_{\mathrm{v}}/ \sqrt{{R_{{0}}}} = \left( \frac{2}{9} {{\alpha_{\mathrm{vir,0}}}} \pi G {\Sigma_{{0}}}\right)^{1/2}.
\label{EqSizeLinewidthCoeffCh}
\end{equation}$$ The observed cloud radius $R_{\mathrm{eff}}$ and surface mass density $\Sigma$ are related to ${R_{{0}}}$ and ${\Sigma_{{0}}}$ with equation ([\[EqRFilling\]](#EqRFilling)) and equation ([\[EqSigmaFilling\]](#EqSigmaFilling)), respectively. Substituting them into equation ([\[EqSizeLinewidthCoeffCh\]](#EqSizeLinewidthCoeffCh)), we obtain $$\begin{equation}
\sigma_{\mathrm{v}}/ \sqrt{R_{\mathrm{eff}}} = \left( \frac{2}{9} {{\alpha_{\mathrm{vir,0}}}} \pi G \right)^{1/2} \left( {\Sigma_{{0}}}\Sigma\right)^{1/4}.
\label{EqSizeLinewidthCoeffWithChObs}
\end{equation}$$ The equation postulates that if ${\alpha_{\mathrm{vir,0}}}$ and ${\Sigma_{{0}}}$ are constant, the scaling between the observed coefficient, $\sigma_{\mathrm{v}}/ \sqrt{R_{\mathrm{eff}}}$ to be proportional to $\Sigma^{1/4}$, which is similar to the observed relation of $\sigma_{\mathrm{v}}/\sqrt{R_{\mathrm{eff}}}$ $\propto$ $\Sigma^{\sim0.3}$.

Figure [19](#FigAppendix)(a) shows the $\sigma_{\mathrm{v}}/\sqrt{R_{\mathrm{eff}}}$–$\Sigma$ relation for the M83 clouds. The red line on the plot is the expected behavior of equation ([\[EqSizeLinewidthCoeffCh\]](#EqSizeLinewidthCoeffCh)) in the case of ${\alpha_{\mathrm{vir,0}}}$ of 1 and ${\Sigma_{{0}}}$ of 160 ${M}_{\odot}\ \mathrm{pc}^{-2}$ for a range of filling factor between 0.1 and 1, showing an alignment with the running median of the observed $\sigma_{\mathrm{v}}/R_{\mathrm{eff}}$.

# Filling factor dependence seen in virial parameter to mass relation

Some studies of molecular clouds, including this one, noted that ${\alpha_{\mathrm{vir}}}$ varies as $\propto$ ${M}_{\mathrm{cl}}$$^{\sim-0.5}$ in their samples (cite: Heyer2001OuterGalaxy; MivilleDeschenes2017MWGMC) (cite: Chevance2023Review). Figure [19](#FigAppendix)(b) shows the ${\alpha_{\mathrm{vir}}}$-${M}_{\mathrm{cl}}$ relation for the M83 clouds. The running median values of ${\alpha_{\mathrm{vir}}}$ derived within the binned ${M}_{\mathrm{cl}}$ values are also shown, and fit the running median values yield that ${\alpha_{\mathrm{vir}}}$ $\propto$ ${M}_{\mathrm{cl}}$$^{-0.45}$, which is close to the ${\alpha_{\mathrm{vir}}}$ $\propto$ ${M}_{\mathrm{cl}}$$^{-\sim0.5}$ seen in other studies quoted here.

(cite: Heyer2001OuterGalaxy) pointed out that a relation of ${\alpha_{\mathrm{vir}}}$ $\propto$ ${M}_{\mathrm{cl}}^{-0.5}$ could arise due to a limited velocity resolution; the argument of (cite: Heyer2001OuterGalaxy) is as follows. From eq. ([\[EqMVirDef\]](#EqMVirDef)) and eq. ([\[EqAlphaVirDef\]](#EqAlphaVirDef)), ${\alpha_{\mathrm{vir}}}=\ (9/2)R_{\mathrm{eff}}\sigma_{\mathrm{v}}^2 (G\alpha_{\mathrm{CO}}{L}_{\mathrm{CO}})^{-1}$, where $\alpha_{\mathrm{CO}}$ is the mass-to-luminosity conversion factor for the CO line. Combining this with ${L}_{\mathrm{CO}}$ $\simeq$ $\sqrt{2 \pi} T_{\mathrm{peak}}\sigma_{\mathrm{v}}\pi R_{\mathrm{eff}}^2$ to eliminate $R_{\mathrm{eff}}$, one obtains $$\begin{equation}
{\alpha_{\mathrm{vir}}}= 178
\left( \frac{\alpha_{\mathrm{CO}}}{4.4  {M}_{\odot} / (\mathrm{K}\ \mathrm{km\ s}^{-1}\mathrm{pc}^2)} \right)^{-1/2}
\left( \frac{\sigma_{\mathrm{v}}}{\mathrm{km\ s}^{-1}} \right)^{3/2}
\left( \frac{T_{\mathrm{peak}}}{\mathrm{K}} \right)^{-1/2}
\left( \frac{{M}_{\mathrm{cl}}}{ {M}_{\odot} } \right)^{-1/2}.
\label{EqAlphaLimit}
\end{equation}$$ Many clouds in the samples of (cite: Heyer2001OuterGalaxy) have $\sigma_{\mathrm{v}}$ close to the instrumental resolution limit. Substituting the instrumental limit of $\sigma_{\mathrm{v}}$ and the typical temperature of the clouds observed, (cite: Heyer2001OuterGalaxy) demonstrated that the above relation explains the lower envelope of their samples on the ${\alpha_{\mathrm{vir}}}$-${M}_{\mathrm{cl}}$ plot.

An argument similar to (cite: Heyer2001OuterGalaxy) would hold for the M83 cloud samples, but not in exactly the same way because $\sigma_{\mathrm{v}}$ of the clouds are well above the velocity resolution of the data (§[3.1](#SubsecCloudPropDistribution)). The red line in figure [19](#FigAppendix)(b) shows that the minimum ${\alpha_{\mathrm{vir}}}$ expected by equation ([\[EqAlphaLimit\]](#EqAlphaLimit)) are far below the observed data points. In turn, we consider that the ${\alpha_{\mathrm{vir}}}$ $\propto$ ${M}_{\mathrm{cl}}^{\sim1/2}$ relation is related to the limitation in the spatial resolution.

The marker colors in figure [19](#FigAppendix)(b) are coded to represent the value of $\sigma_{\mathrm{v}}^2/\sqrt{\Sigma}$, which is dimensionally equal to $\sigma_{\mathrm{v}}^{3/2} T_{\mathrm{peak}}^{-1/2}$ as $\Sigma$ $\propto$ $T_{\mathrm{peak}}\sigma_{\mathrm{v}}$. From the distribution of the data points, it is apparent $\sigma_{\mathrm{v}}^2/\Sigma^{1/2}$ is almost constant along the direction of ${\alpha_{\mathrm{vir}}}$ $\propto$ ${M}_{\mathrm{cl}}^{-1/2}$. We may rewrite eq. ([\[EqSizeLinewidthCoeffWithChObs\]](#EqSizeLinewidthCoeffWithChObs)) as $$\begin{equation}
\sigma_{\mathrm{v}}^{2} / \sqrt{\Sigma} \propto \sqrt{{\Sigma_{{0}}}} R_{\mathrm{eff}}.
\label{EqSizeLinewidthCoeffWithChObsRewrite}
\end{equation}$$ As seen in §[3.1](#SubsecCloudPropDistribution), the observed $R_{\mathrm{eff}}$ indeed has a limited range of variation, with 16th and 84th percentiles of 40 and 80 pc, respectively. We argued in §[6](#SecDiscussion) that once the beam dilution is taken into account, a majority of the clouds agree with ${\alpha_{\mathrm{vir}}}$ of 1 (or 2) with near uniform ${\Sigma_{{0}}}$. Therefore, when we assume that near-virial clouds with almost constant ${\Sigma_{{0}}}$ account for the dominant fraction of the M83 clouds as suggested in §[6](#SecDiscussion), equation ([\[EqSizeLinewidthCoeffWithChObsRewrite\]](#EqSizeLinewidthCoeffWithChObsRewrite)) leads that ${\sigma_{\mathrm{v}}}^2 / \sqrt{\Sigma}$, which has the same dimension as $\sigma_{\mathrm{v}}^{3/2} T_{\mathrm{peak}}^{-1/2}$, would also be constant and thus, ${M}_{\mathrm{vir}}$ $\propto$ ${M}_{\mathrm{cl}}^{\sim0.5}$ emerges from equation ([\[EqAlphaLimit\]](#EqAlphaLimit)).

# Comparison of Galactic cloud catalogs

In §[3.2](#SubsecScalingRelations), the clouds in M83 are compared with the scaling relations of S87, which have been used as the reference lines up to now. The scaling relations of S87 are determined from 273 clouds sampled from the inner Galactic disk with relatively high-intensity thresholds of a few to several Kelvin, but subsequent studies made a more extensive sampling of clouds down to lower intensity levels. In particular, (cite: Rice2016) (hereafter R16) and (cite: MivilleDeschenes2017MWGMC) (hereafter M17) sampled clouds from the Galactic plane data of (cite: Dame2001), which observed most part of the thin Galactic molecular disk in $^{12}$CO (1–0) with the 1.2m telescopes. Here, we extend the examination made in §[3.2](#SubsecScalingRelations) by including clouds in the R16 and M17 catalogs.

## Catalogs for comparison

The R16 catalog contains 1064 clouds with a total cloud mass of 2.5 $\times$ 10$^8$ ${M}_{\odot}$ and the M17 catalog lists 8107 clouds with a total mass of 1.2 $\times$ 10$^9$ ${M}_{\odot}$. The M17 catalog sampled 98 percent of the total CO luminosity within the mapped area. To compare the M83 clouds with the Galactic clouds at similar environmental conditions, we use the clouds with the Galactocentric radius within 8.5 kpc for the Galactic catalogs. Both M83 and Milky Way have radially decreasing trend of molecular fraction $f_\mathrm{mol}$ ($\equiv$ $\Sigma_{\mathrm{mol}}$ / ($\Sigma_{\mathrm{mol}}$ + $\Sigma_{\mathrm{atom}}$)). In M83, $f_{\mathrm{mol}}$ is about 0.5 at the edge of the mapped area (cite: Crosthwaite2002M83; Lee2024M83). In the Milky Way, it is about 0.1 at $R_{\mathrm{gal}}$ of 8.5 kpc (cite: NakanishiSofue2016).

For the R16 catalog, we take the radius $R$, velocity dispersion $\sigma_{\mathrm{v}}$, and cloud mass ${M}_{\mathrm{cl}}$ from the catalog. The cloud radius in R16 follows the same definition as S87. Therefore, $R$ in the R16 catalog can be directly compared with $R_{\mathrm{eff}}$ of the M83 clouds and S87 clouds. CO luminosity ${L}_{\mathrm{CO}}$ of the R16 clouds is computed from ${M}_{\mathrm{cl}}$ assuming the same conversion factor as in §[2.6](#SubsecCOLumFraction). The surface density $\Sigma$ and virial parameter ${\alpha_{\mathrm{vir}}}$ are derived following eq. ([\[EqSigmaDef\]](#EqSigmaDef)) and eq. ([\[EqAlphaVirDef\]](#EqAlphaVirDef)).

For the M17 catalog, the velocity dispersion $\sigma_v$, surface density $\Sigma$, and cloud mass ${M}_{\mathrm{cl}}$ are taken from the catalog. We compute the effective radius of M17 clouds as $R_{\mathrm{eff}}$ = $\left[M (\pi \Sigma)^{-1}\right]^{1/2}$. For ${L}_{\mathrm{CO}}$ and ${\alpha_{\mathrm{vir}}}$, they are derived in the same way as the R16 clouds.

## Comparison

Figure [20](#FigSclRelationsExtended) compares the scaling relations of cloud properties among the M83 catalog and the Galactic cloud catalogs of S87, R16, and M17. For the MW catalogs, we divide the clouds into two groups with a kinematic distance $D_{\mathrm{kin}}$ threshold of 8.5 kpc. The upper and bottom rows of figure [20](#FigSclRelationsExtended) show the Galactic clouds at $D_{\mathrm{kin}}$ $<$ 8.5 kpc and $>$ 8.5 kpc, respectively. In both rows, the MW clouds with $R_{\mathrm{gal}}$ $>8.5$ kpc are excluded, as mentioned above. In addition, we excluded the clouds with Galactic longitude $l$ within $|l|$ $<$ 5 $\ensuremath{^\circ}$ to exclude the clouds located in the directions close to the Galactic Center (GC) because the GC clouds have properties distinct from the disk clouds (cite: Oka2001) and such clouds are contained only in the M17 catalog among the three catalogs. Table [\[TablePropsMW\]](#TablePropsMW) lists the 16, 50, and 84 percentiles of the cloud properties for the three Galactic catalogs classified with the same criteria as figure [20](#FigSclRelationsExtended). We note that the R16 and M17 catalogs contain clouds in the outer Galactic disk, which have lower $\Sigma$ and higher ${\alpha_{\mathrm{vir}}}$ than the inner Galactic clouds (cite: Heyer2001OuterGalaxy). The last three rows in Table [\[TablePropsMW\]](#TablePropsMW) list the cloud properties in the three catalogs without any filtering.

### R16 catalog

Comparing the R16 and S87 clouds, the R16 clouds mostly follow scaling relations similar to that of S87, with a slight modification in coefficients. The coefficients of the cloud scaling relations are determined by $\Sigma$ and ${\alpha_{\mathrm{vir}}}$. As can be seen from table [\[TablePropsMW\]](#TablePropsMW), the R16 clouds have a median $\Sigma$, a factor of three lower than that of S87, but the median ${\alpha_{\mathrm{vir}}}$ is comparable. Because of the comparable ${\alpha_{\mathrm{vir}}}$, clouds in both catalogs show a similar scaling on the ${M}_{\mathrm{vir}}$-${L}_{\mathrm{CO}}$ plot and $\sigma_{\mathrm{v}}/\sqrt{R_{\mathrm{eff}}}$-$\Sigma$ plots. On the $\sigma_{\mathrm{v}}$-$R_{\mathrm{eff}}$ plot, the R16 clouds indicate a smaller $\sigma_{\mathrm{v}}$ at given $R_{\mathrm{eff}}$ compared to S87. R16 determined the $\sigma_{\mathrm{v}}$-$R_{\mathrm{eff}}$ scaling in the inner Galactic disk to be $\sigma_{\mathrm{v}}$ = 0.50 $R_{\mathrm{eff}}$$^{0.52}$. The coefficient value of 0.50 $\mathrm{km\ s}^{-1}$ pc$^{-1/2}$ is slightly smaller than for S87, 0.72 $\mathrm{km\ s}^{-1}$ pc$^{-1/2}$ (cite: Heyer2009). Considering the factor of two differences in the median $\Sigma$, this difference in the $\sigma_{\mathrm{v}}$-$R_{\mathrm{eff}}$ coefficient value agrees with the $\Sigma$-dependence of the $\sigma_{\mathrm{v}}$-$R_{\mathrm{eff}}$ coefficient for bound clouds (eq. [\[EqSizeLinewidthCoeff\]](#EqSizeLinewidthCoeff)).

In §[3.2](#SubsecScalingRelations), the M83 clouds with $T_{\mathrm{peak}}$ $>2$ K mostly follow the scaling relations of S87. As R16 and S87 clouds follow similar scaling relationships, the argument in §[3.2](#SubsecScalingRelations) would not change if the R16 clouds were taken as reference samples instead of the S87 clouds.

### M17 catalog

At $D_{\mathrm{kin}}$ $>$ 8.5 kpc, the M17 clouds cover a range of $R_{\mathrm{eff}}$ similar to that of the M83 clouds as median $R_{\mathrm{eff}}$ is similarly around 50 pc. However, despite the similar radii, there is quite a small overlap with that of M83 clouds on the $\sigma_{\mathrm{v}}$-$R_{\mathrm{eff}}$, ${M}_{\mathrm{vir}}$-${L}_{\mathrm{CO}}$ and $\sigma_{\mathrm{v}}/\sqrt{R_{\mathrm{eff}}}$-$\Sigma$ plots (figure [20](#FigSclRelationsExtended)e, [20](#FigSclRelationsExtended)f, [20](#FigSclRelationsExtended)h). The small overlap in these plots suggests that the M83 clouds cannot be deemed as the simple counterparts of the M17 clouds sampled in another galactic disk.

The small overlap between the M17 and M83 clouds owes to higher ${\alpha_{\mathrm{vir}}}$ in the M17 clouds compared to other Galactic catalogs. In particular, even though M17 and R16 sampled clouds from similar data sets of (cite: Dame2001), M17 clouds have about a factor 4 higher ${\alpha_{\mathrm{vir}}}$ compared to the R16 clouds. The high ${\alpha_{\mathrm{vir}}}$ in the M17 clouds is linked to the higher $\sigma_v$ at a given $R_{\mathrm{eff}}$ compared to the R16 clouds, seen on the $\sigma_v$-$R_{\mathrm{eff}}$ relation (figure [20](#FigSclRelationsExtended)a, [20](#FigSclRelationsExtended)e). The reason for this systematically higher $\sigma_{\mathrm{v}}$ in the M17 clouds compared to the R16 clouds is not completely clear, but it might reflect the difference in the ways clouds are identified, as also was suggested by (cite: Evans2021BoundCloud). M17 identified clouds by decomposing each spectrum of the data cube into a set of Gaussian components and then clustering the Gaussian components into clouds, while the methods used by S87, R16, and here in M83 are similar in that cloud peaks are identified by setting intensity thresholds. The clustering process of M17 accepts the joining of two clusters of Gaussian components at different velocities if the velocity difference between the two clusters is less than twice the velocity dispersion of individual clusters.

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| Catalog name | $R_{\mathrm{eff}}$ | $M_{\mathrm{cl}}$ | $\Sigma$ | $\sigma_{\mathrm{v}}$ | $\alpha_{\mathrm{vir}}$ | $N$ |
|  | (pc) | ($10^{5}$ $M_{\odot}$) | ($M_{\odot}$ pc$^{-2}$) | (km s$^{-1}$) |  |  |
| S87 ($D<8.5$ kpc, $R_{\mathrm{gal}}<8.5$ kpc, $|l|>5\ensuremath{^\circ}$) | $14.3_{8.2}^{27.9}$ | $1.0_{0.2}^{4.7}$ | $152.2_{100.2}^{236.8}$ | $3.1_{2.3}^{4.3}$ | $1.4_{0.9}^{2.1}$ | 166 |
| S87 ($D>8.5$ kpc, $R_{\mathrm{gal}}<8.5$ kpc, $|l|>5\ensuremath{^\circ}$) | $26.8_{17.3}^{45.0}$ | $4.8_{1.9}^{11.1}$ | $194.5_{142.6}^{288.2}$ | $3.9_{3.0}^{5.0}$ | $1.0_{0.7}^{1.4}$ | 62 |
| R16 ($D<8.5$ kpc, $R_{\mathrm{gal}}<8.5$ kpc, $|l|>5\ensuremath{^\circ}$) | $24.0_{15.5}^{40.6}$ | $0.8_{0.4}^{3.0}$ | $53.8_{25.9}^{102.9}$ | $2.5_{1.7}^{3.7}$ | $1.5_{0.8}^{3.0}$ | 324 |
| R16 ($D>8.5$ kpc, $R_{\mathrm{gal}}<8.5$ kpc, $|l|>5\ensuremath{^\circ}$) | $47.4_{26.5}^{78.8}$ | $4.2_{1.0}^{13.1}$ | $67.8_{25.8}^{120.4}$ | $3.3_{2.3}^{5.1}$ | $1.3_{0.7}^{2.9}$ | 118 |
| M17 ($D<8.5$ kpc, $R_{\mathrm{gal}}<8.5$ kpc, $|l|>5\ensuremath{^\circ}$) | $19.8_{9.4}^{37.0}$ | $0.4_{0.0}^{1.9}$ | $28.8_{7.6}^{75.2}$ | $4.0_{2.3}^{5.9}$ | $6.8_{3.2}^{35.0}$ | 2893 |
| M17 ($D>8.5$ kpc, $R_{\mathrm{gal}}<8.5$ kpc, $|l|>5\ensuremath{^\circ}$) | $60.3_{36.7}^{95.7}$ | $4.1_{1.3}^{12.4}$ | $32.7_{15.4}^{75.9}$ | $6.4_{4.5}^{8.2}$ | $5.4_{2.9}^{14.9}$ | 1177 |
| S87 (Full) | $17.0_{8.0}^{31.9}$ | $1.3_{0.2}^{6.3}$ | $152.6_{92.8}^{250.5}$ | $3.1_{2.2}^{4.4}$ | $1.3_{0.8}^{2.1}$ | 273 |
| R16 (Full) | $27.6_{15.4}^{53.6}$ | $0.5_{0.1}^{3.0}$ | $22.1_{8.6}^{76.7}$ | $2.1_{1.3}^{3.5}$ | $2.3_{1.1}^{5.2}$ | 1064 |
| M17 (Full) | $26.4_{9.0}^{60.4}$ | $0.4_{0.0}^{3.2}$ | $16.5_{4.9}^{60.0}$ | $3.6_{1.8}^{6.5}$ | $8.0_{3.2}^{34.0}$ | 8107 |

: Median cloud properties in the MW catalogs

Table notes: Median and 16th-to-84th percentile range of the cloud properties for the Galactic cloud catalogs of (cite: Solomon1987Larson), (cite: Rice2016), and (cite: MivilleDeschenes2017MWGMC). In the first six rows, the clouds with the Galactocentric of $R_{\mathrm{gal}}$ $>8.5$ kpc and the Galactic longitude $l$ within $|l|$ $<$ 5 $\ensuremath{^\circ}$ are excluded, and the remaining clouds are classified by the line-of-sight distance threshold of 8.5 kpc. In the last three rows, the full sample summaries for the catalogs are listed. (1) Catalog name and $D_{\mathrm{kin}}$ range. (2) Effective radius. (3) Cloud mass. (4) Surface density. (5) Velocity dispersion. (6) Virial parameter. (7) Number of clouds.

(ref: Adamo2015) Adamo, A., Kruijssen, J. M. D., Bastian, N., et al. 2015, MNRAS, 452, 246. doi:10.1093/mnras/stv1203

(ref: Arimoto1996) Arimoto, N., Sofue, Y., & Tsujimoto, T. 1996, PASJ, 48, 275. doi:10.1093/pasj/48.2.275

(ref: BallesterosParedes2011A) Ballesteros-Paredes, J., Hartmann, L. W., Vázquez-Semadeni, E., Heitsch, F., & Zamora-Avilés, M. A. 2011, MNRAS, 411, 65

(ref: BallesterosParedes2018) Ballesteros-Paredes, J., Vázquez-Semadeni, E., Palau, A., et al. 2018, MNRAS, 479, 2112. doi:10.1093/mnras/sty1515

(ref: BertoldiMcKee1992) Bertoldi, F., & McKee, C. F. 1992, ApJ, 395, 140

(ref: Bolatto2008GMCs) Bolatto, A. D., Leroy, A. K., Rosolowsky, E., et al. 2008, ApJ, 686, 948. doi:10.1086/591513

(ref: Bolatto2013ConversionFactor) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Bresolin2016) Bresolin, F., Kudritzki, R.-P., Urbaneja, M. A., et al. 2016, ApJ, 830, 64. doi:10.3847/0004-637X/830/2/64

(ref: CalduPrimo2013) Caldú-Primo, A., Schruba, A., Walter, F., et al. 2013, AJ, 146, 150. doi:10.1088/0004-6256/146/6/150

(ref: CalduPrimo2016Andromeda) Caldú-Primo, A. & Schruba, A. 2016, AJ, 151, 34. doi:10.3847/0004-6256/151/2/34

(ref: Chevance2023Review) Chevance, M., Krumholz, M. R., McLeod, A. F., et al. 2023, Protostars and Planets VII, 534, 1. doi:10.48550/arXiv.2203.09570

(ref: Colombo2014Env) Colombo, D., Hughes, A., Schinnerer, E., et al. 2014, ApJ, 784, 3

(ref: Colombo2019) Colombo, D., Rosolowsky, E., Duarte-Cabral, A., et al. 2019, MNRAS, 483, 4291. doi:10.1093/mnras/sty3283

(ref: CombesBecquaert1997) Combes, F. & Becquaert, J.-F. 1997, A&A, 326, 554

(ref: Crosthwaite2002M83) Crosthwaite, L. P., Turner, J. L., Buchholz, L., Ho, P. T. P., & Martin, R. N. 2002, AJ, 123, 1892

(ref: Dame2001) Dame, T. M., Hartmann, D., & Thaddeus, P. 2001, ApJ, 547, 792. doi:10.1086/318388

(ref: Dobbs2011NotBound) Dobbs, C. L., Burkert, A., & Pringle, J. E. 2011, MNRAS, 413, 2935. doi:10.1111/j.1365-2966.2011.18371.x

(ref: DobbsPringle2013) Dobbs, C. L. & Pringle, J. E. 2013, MNRAS, 432, 653. doi:10.1093/mnras/stt508

(ref: DonovanMeyer2013) Donovan Meyer, J., Koda, J., Momose, R., et al. 2013, ApJ, 772, 107. doi:10.1088/0004-637X/772/2/107

(ref: Elmegreen1987HISuperClouds) Elmegreen, B. G. & Elmegreen, D. M. 1987, ApJ, 320, 182. doi:10.1086/165534

(ref: Elmegreen1989MassMetalDependence) Elmegreen, B. G. 1989, ApJ, 338, 178. doi:10.1086/167192

(ref: Engargiola2003) Engargiola, G., Plambeck, R. L., Rosolowsky, E., et al. 2003, ApJS, 149, 343. doi:10.1086/379165

(ref: Evans2021BoundCloud) Evans, N. J., Heyer, M., Miville-Deschênes, M.-A., et al. 2021, ApJ, 920, 126. doi:10.3847/1538-4357/ac1425

(ref: Field2011) Field, G. B., Blackman, E. G., & Keto, E. R. 2011, MNRAS, 416, 710. doi:10.1111/j.1365-2966.2011.19091.x

(ref: ForemanMackey2013emcee) Foreman-Mackey, D., Hogg, D. W., Lang, D., et al. 2013, PASP, 125, 306. doi:10.1086/670067

(ref: Freeman2017) Freeman, P., Rosolowsky, E., Kruijssen, J. M. D., Bastian, N., & Adamo, A. 2017, MNRAS, 468, 1769

(ref: Fukui2008) Fukui, Y., Kawamura, A., Minamidani, T., et al. 2008, ApJS, 178, 56-70

(ref: Goldsmith2008Taurus) Goldsmith, P. F., Heyer, M., Narayanan, G., et al. 2008, ApJ, 680, 428. doi:10.1086/587166

(ref: Heyer2001OuterGalaxy) Heyer, M. H., Carpenter, J. M., & Snell, R. L. 2001, ApJ, 551, 852

(ref: Heyer2009) Heyer, M., Krawczyk, C., Duval, J., & Jackson, J. M. 2009, ApJ, 699, 1092

(ref: HeyerDame2015Review) Heyer, M. & Dame, T. M. 2015, ARA&A, 53, 583. doi:10.1146/annurev-astro-082214-122324

(ref: Hernandez2019) Hernandez, S., Larsen, S., Aloisi, A., et al. 2019, ApJ, 872, 116. doi:10.3847/1538-4357/ab017a

(ref: Hirota2014) Hirota, A., Kuno, N., Baba, J., et al. 2014, PASJ, 66, 46

(ref: Hirota2018M83) Hirota, A., Egusa, F., Baba, J., et al. 2018, PASJ, 70, 73. doi:10.1093/pasj/psy071

(ref: Hughes2013GMCs) Hughes, A., Meidt, S. E., Colombo, D., et al. 2013, ApJ, 779, 46

(ref: Hunter2007Matplotlib) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90. doi:10.1109/MCSE.2007.55

(ref: Inutsuka2015) Inutsuka, S.-i., Inoue, T., Iwasaki, K., & Hosokawa, T. 2015, A&A, 580, A49

(ref: Jarrett20032MASS) Jarrett, T. H., Chester, T., Cutri, R., Schneider, S. E., & Huchra, J. P. 2003, AJ, 125, 525

(ref: Kauffmann2010RelationII) Kauffmann, J., Pillai, T., Shetty, R., et al. 2010, ApJ, 716, 433. doi:10.1088/0004-637X/716/1/433

(ref: Kobayashi2017MF) Kobayashi, M. I. N., Inutsuka, S.-i., Kobayashi, H., & Hasegawa, K. 2017, ApJ, 836, 175

(ref: Koda2009) Koda, J., et al. 2009, ApJL, 700, L132

(ref: Koda2019TP2VIS) Koda, J., Teuben, P., Sawada, T., et al. 2019, PASP, 131, 054505. doi:10.1088/1538-3873/ab047e

(ref: Koda2023M83) Koda, J. et al.

(ref: Kruijssen2014Cluster) Kruijssen, J. M. D. 2014, Classical and Quantum Gravity, 31, 244006. doi:10.1088/0264-9381/31/24/244006

(ref: Lada2010) Lada, C. J., Lombardi, M., & Alves, J. F. 2010, ApJ, 724, 687

(ref: Lada2020MassSizeRelation) Lada, C. J. & Dame, T. M. 2020, ApJ, 898, 3. doi:10.3847/1538-4357/ab9bfb

(ref: Larson1981) Larson, R. B. 1981, MNRAS, 194, 809

(ref: Leroy2015NGC253) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2015, ApJ, 801, 25

(ref: Lee2024M83) Lee, A. M., Koda, J., Hirota, A., et al. 2024, arXiv:2404.14503. doi:10.48550/arXiv.2404.14503

(ref: Lombardi2010) Lombardi, M., Alves, J., & Lada, C. J. 2010, A&A, 519, L7. doi:10.1051/0004-6361/201015282

(ref: Maeda2020NGC1300) Maeda, F., Ohta, K., Fujimoto, Y., et al. 2020, MNRAS, 493, 5045. doi:10.1093/mnras/staa556

(ref: Mao2020CloudProps) Mao, S. A., Ostriker, E. C., & Kim, C.-G. 2020, ApJ, 898, 52. doi:10.3847/1538-4357/ab989c

(ref: MivilleDeschenes2017MWGMC) Miville-Deschênes, M.-A., Murray, N., & Lee, E. J. 2017, ApJ, 834, 57. doi:10.3847/1538-4357/834/1/57

(ref: Mogotsi2016) Mogotsi, K. M., de Blok, W. J. G., Caldú-Primo, A., et al. 2016, AJ, 151, 15. doi:10.3847/0004-6256/151/1/15

(ref: Muraoka2023M33) Muraoka, K., Konishi, A., Tokuda, K., et al. 2023, ApJ, 953, 164. doi:10.3847/1538-4357/ace4bd

(ref: NakanishiSofue2016) Nakanishi, H. & Sofue, Y. 2016, PASJ, 68, 5. doi:10.1093/pasj/psv108

(ref: Oka2001) Oka, T., Hasegawa, T., Sato, F., et al. 2001, ApJ, 562, 348. doi:10.1086/322976

(ref: RamirezGaleano2022) Ramı́rez-Galeano, L., Ballesteros-Paredes, J., Smith, R. J., et al. 2022, MNRAS, 515, 2822. doi:10.1093/mnras/stac1848

(ref: RandLordHidgon1999M83) Rand, R. J., Lord, S. D., & Higdon, J. L. 1999, ApJ, 513, 720

(ref: Rice2016) Rice, T. S., Goodman, A. A., Bergin, E. A., et al. 2016, ApJ, 822, 52. doi:10.3847/0004-637X/822/1/52

(ref: Robitaille2019) Robitaille, T., Rice, T., Beaumont, C., et al. 2019, Astrophysics Source Code Library. ascl:1907.016

(ref: RomanDuval2010) Roman-Duval, J., Jackson, J. M., Heyer, M., et al. 2010, ApJ, 723, 492. doi:10.1088/0004-637X/723/1/492

(ref: Rosolowsky2005MassSpectra) Rosolowsky, E. 2005, PASP, 117, 1403

(ref: Rosolowsky2005) Rosolowsky, E. & Blitz, L. 2005, ApJ, 623, 826. doi:10.1086/428897

(ref: Rosolowsky2006CPROPS) Rosolowsky, E., & Leroy, A. 2006, PASP, 118, 590

(ref: Rosolowsky2021PhangsGMCs) Rosolowsky, E., Hughes, A., Leroy, A. K., et al. 2021, MNRAS, 502, 1218. doi:10.1093/mnras/stab085

(ref: Sanders1985) Sanders, D. B., Scoville, N. Z., & Solomon, P. M. 1985, ApJ, 289, 373. doi:10.1086/162897

(ref: SaultTeubenWright1995MIRIAD) Sault, R. J., Teuben, P. J., & Wright, M. C. H. 1995, in ASP Conf. Ser. 77, Astronomical Data Analysis Software and Systems IV, ed. R. A. Shaw, H. E. Payne, & J. J. E. Hayes (San Francisco, CA: ASP), 433

(ref: ScovilleSanders1987) Scoville, N. Z. & Sanders, D. B. 1987, Interstellar Processes, 134, 21. doi:10.1007/978-94-009-3861-8_2

(ref: Smith2020CloudFactory) Smith, R. J., Treß, R. G., Sormani, M. C., et al. 2020, MNRAS, 492, 1594. doi:10.1093/mnras/stz3328

(ref: Solomon1987Larson) Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987, ApJ, 319, 730

(ref: Stark1984VelDispersion) Stark, A. A. 1984, ApJ, 281, 624. doi:10.1086/162137

(ref: StarkLee2005) Stark, A. A. & Lee, Y. 2005, ApJL, 619, L159. doi:10.1086/427936

(ref: Sun2020) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020, ApJL, 901, L8. doi:10.3847/2041-8213/abb3be

(ref: Sun2020DE) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2020, ApJ, 892, 148. doi:10.3847/1538-4357/ab781c

(ref: Thim2003M83Distance) Thim, F., Tammann, G. A., Saha, A., Dolphin, A., Sandage, A., Tolstoy, E., & Labhardt, L. 2003, ApJ, 590, 256

(ref: TilanusAllen1993) Tilanus, R. P. J., & Allen, R. J. 1993, A&A, 274, 707

(ref: vanDerWalt2014ScikitImage) van der Walt, S., Schönberger, J. L., Nunez-Iglesias, J., et al. 2014, PeerJ, 2, e453. doi:10.7717/peerj.453

(ref: Verschuur1993BeamBias) Verschuur, G. L. 1993, AJ, 106, 2580. doi:10.1086/116827

(ref: WilliamsMcKee1997) Williams, J. P., & McKee, C. F. 1997, ApJ, 476, 166

(ref: Wilson1995Xco) Wilson, C. D. 1995, ApJL, 448, L97. doi:10.1086/309615

(ref: Wilson2011JCMT) Wilson, C. D., Warren, B. E., Irwin, J., et al. 2011, MNRAS, 410, 1409. doi:10.1111/j.1365-2966.2010.17646.x

[^1]: The definition of GMC slightly varies from literature to literature, but (cite: Sanders1985) defined molecular clouds with a diameter larger than 22 pc and mass above 10$^5$ ${M}_{\odot}$ as GMCs. Nearby Galactic clouds with a mass of a few 10$^4$ ${M}_{\odot}$ are also often referred to as GMCs (cite: Lada2010)

[^2]: http://www.dendrograms.org

[^3]: As $R_{\mathrm{eff}}$ relates to root-mean-square cloud size $\sigma_r$ as $R_{\mathrm{eff}}=1.91\sigma_r$, the beam size $\theta_{\mathrm{b}}$ of 46 pc corresponds to $\sim$37 pc (=1.91 $\times$ $\theta_{\mathrm{b}}$ / $\sqrt{8\log{2}}$)

[^4]: In most parts within Taurus molecular cloud, which is one of the most well-studied molecular clouds, the intrinsic temperature is estimated to be between 6 and 12 K (cite: Goldsmith2008Taurus)

</paper>

Write the methods card for this paper.