# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...687A.293Q\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2024A&A...687A.293Q",
 "title": "Do spiral arms enhance star formation efficiency?",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Querejeta, Miguel",
 "n_authors": 35,
 "arxiv_id": "2405.05364",
 "doi": "10.1051/0004-6361/202449733",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S",
  "2013.1.00803.S",
  "2013.1.01161.S",
  "2015.1.00121.S",
  "2015.1.00782.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2016.1.00386.S",
  "2017.1.00886.L",
  "2018.1.01651.S"
 ]
}
```

Paper text:
<paper>
# Do spiral arms enhance star formation efficiency?

# Introduction

Spiral arms stand out as some of the most iconic features of galaxies, including our own Milky Way. Approximately two out of three galaxies in the local Universe display some kind of spiral structure (cite: 2010ApJS..186..427N; 2013MNRAS.435.2835W; 2015ApJS..217...32B), including well-delineated grand-design spirals (like M51 or NGC 1365) or more sparse multi-armed (e.g. M100 or NGC 4254) and flocculent spiral components (e.g. NGC 2775 or NGC 4298). While spiral arms are recognised as active sites of star formation, it is still unclear if this results from the mere accumulation of large amounts of gas or if it is due to a more efficient conversion of gas into stars in spiral arms than in interarm regions.

There are a few reasons we would expect spiral arms to lead to enhancements in the star formation process. By collecting gas, spirals elevate star formation rates (SFRs) by locally increasing the gas density on scales of several hundreds of pcs. They may also more actively ‘trigger’ star formation by boosting the star formation efficiency (SFE), such that more stars are formed per unit mass of gas than in regions of comparable density elsewhere in the galaxy. This ‘triggering’ of star formation is believed to either reflect a reduction in shear in spiral arms, which promotes gravitational collapse and the formation of stars (cite: 1987ApJ...312..626E; 1993prpl.conf...97E; 2002ApJ...570..132K; 2017MNRAS.470.4261D), or the development of shocks in the gas in response to spiral density waves (cite: 1969ApJ...158..123R; 1975ApJ...196..381R; 2004MNRAS.349..909G).

Several observational studies have quantified the increase of gas and star formation rate surface density in spiral arms (cite: 1988Natur.334..402V; 1993A&A...274..123G; 2003PASJ...55..191N; 2009A&A...495..795H; 2020ApJ...901L...8S; 2021A&A...656A.133Q). Leveraging the high resolution of PHANGS-ALMA maps (cite: 2021ApJS..257...43L) that probe CO emission on ${\sim} 100$ pc scales, (cite: 2021ApJ...913..113M) found evidence that gas density contrasts scale non-linearly with contrasts in the underlying stellar spiral density, consistent with shocks actively elevating the density in the arm. Even so, observational evidence suggests that the existence of a spiral shock may not immediately lead to an enhancement in the SFE. Studies comparing SFE in spiral arms and the interarm region lead to ambiguous, inconsistent results, with some pointing to enhanced SFE in the arms (cite: 1987PhDT........11L; 1988Natur.334..402V; 1990ApJ...349..497C; 1990ApJ...356..135L; 1996MNRAS.283..251K) and some suggesting overall similar SFE between spiral and interarm regions, despite local fluctuations (cite: 2003AJ....126.2831H; 2010ApJ...725..534F; 2012MNRAS.426..701M; 2012ApJ...757..155R; 2015MNRAS.452..289E; 2016ApJ...827..103K; 2018MNRAS.479.2361R; 2021A&A...656A.133Q). This might reflect additional mechanisms that act in opposition to a potential boost in SFE. For example, cloud-cloud collisions, sometimes seen as triggers of star formation, can also lead to elevated gas velocity dispersions that shift gas out of a self-gravitating state (cite: 2007MNRAS.374.1115D; 2014PASA...31...35D). Shear and differential gas flows in the arm can be another source of stability against gravitational collapse that suppresses star formation (cite: 2013ApJ...779...45M).

To unambiguously determine the efficiency of star formation in spiral arms, it is crucial to first control for as many independent factors as possible. The measured SFE can critically depend on the employed tracer, conversion factors, observational resolution, and the definition of spiral arms. Yet, even for a consistent definition of arms, different galaxies seem to show a divergent behaviour regarding SFE in spiral arms, as we recently showed for the PHANGS sample of galaxies (cite: 2021A&A...656A.133Q). Here, we aim to examine this problem in greater detail by assembling a comprehensive set of homogeneous measurements of spiral arm-to-interarm contrasts in stellar mass, gas, SFR, and SFE, applying a single consistent strategy to all spiral arms and employing state-of-the art calibrations for the gas density and star formation rate from PHANGS.

PHANGS[^1] is a multi-wavelength effort to map nearby galaxies at ${\lesssim} 1''$ resolution to study the star formation cycle. Spanning large programmes on ALMA (cite: 2021ApJS..257...43L), MUSE (cite: emsellem21), HST (cite: 2022ApJS..258...10L), and JWST (cite: 2023ApJ...944L..17L; 2024arXiv240115142W) and further complemented by a large number of ancillary observations (including atomic gas), PHANGS provides a unique view on the distribution of molecular clouds in galaxies, their collapse to form stars, and the feedback associated with the star formation process.

This paper is a natural follow-up companion to (cite: 2021ApJ...913..113M), where a study of the relation between azimuthal contrasts in stellar mass and molecular gas was presented, without explicitly identifying spiral arms. The present paper builds on (cite: 2021A&A...656A.133Q), where we presented environmental masks of morphological features for PHANGS galaxies (including spirals) and discussed how molecular gas and star formation are distributed across environments. In (cite: 2021A&A...656A.133Q), the distribution of surface densities, efficiency, and contrasts was studied at kpc resolution. Here, we examine the effect of higher resolution (${\sim}100$ pc instead of ${\sim}1$ kpc) on arm and interarm contrasts. We also consider how contrasts change if we employ thinner arm masks, with an alternative arm definition that we introduce here. While in (cite: 2021A&A...656A.133Q) we measured a single arm/interarm contrast per galaxy, here we study the contrast in individual spiral segments, and we also analyse variations with galactocentric radius. Another novelty of this paper is that we account for the spiral arm enhancement in stellar mass surface density and its relation to the contrast in molecular gas and star formation rate surface densities. We also consider the effect of including atomic gas.

The structure of this paper is the following. In Sect. [2](#Sec:data), we describe our tracers of molecular and atomic gas, star formation, and stellar mass, as well as the environmental masks and binning approach. The main results of the paper are presented in Sect. [3](#Sec:results) and discussed in Sect. [4](#Sec:discussion). We conclude with a summary in Sect. [5](#Sec:concl).

# Data and methods

![](method.png)

We focus on the 28 spiral galaxies from PHANGS–ALMA where a spiral mask was explicitly defined in (cite: 2021A&A...656A.133Q). This choice limits our study to galaxies with long and continuous spiral segments, which can be traced over most of the star-forming disc (the remaining galaxies do not have a spiral mask defined in (cite: 2021A&A...656A.133Q), as the identification of arms becomes increasingly subjective and less meaningful). This results in a sample made up predominantly of grand-design spirals, excluding a larger fraction of multi-armed and flocculent spirals, where the distinction between arm and interarm becomes fuzzier. We perform this study at a cloud-scale resolution of ${\sim}100$ pc, working with the highest-resolution maps available to us in each case[^2], which typically corresponds to ${\sim} 1\ensuremath{''}$ for CO and H$\alpha$. In Sect. [2.1](#Sec:sample), we explain how the PHANGS–ALMA sample was selected. We measure molecular gas surface densities based on the ALMA observations of CO(2–1) as explained in Sect. [2.2](#Sec:PHANGS--ALMA). In Sect. [2.3](#Sec:SFRs) we outline our measurement of star formation rates. We describe the H I data in Sect. [2.4](#Sec:HIdata). We determine stellar mass surface densities based on near-infrared (NIR) observations as explained in Sect. [2.5](#Sec:stellarmass). The masks that we use are presented in Sect. [2.6](#Sec:masks) including a new, thinner alternative for spiral arms. In Sect. [2.7](#Sec:method), we introduce our nominal approach to measure contrasts in radial bins.

## Sample

The galaxies studied in this paper are part of the nominal PHANGS–ALMA sample of 74 galaxies, excluding extensions (cite: 2021ApJS..257...43L). PHANGS–ALMA targeted virtually all the massive, star-forming galaxies out to $D \approx 17$ Mpc, which are not highly inclined and which are visible from the ALMA site. The galaxies are representative of the $z=0$ star formation ‘main sequence’ (cite: 2007ApJ...660L..43N). We refer the interested reader to (cite: 2021ApJS..257...43L) for a detailed description of the sample selection and properties.

This sub-sample of 28 galaxies with well-defined spiral arms spans stellar masses $9.5 \lesssim \log(M_\star / {\rm M}_\odot) \lesssim 11.1$, with a median $\log(M_\star / {\rm M}_\odot) = 10.5$, which is very similar to the median stellar mass in the whole PHANGS–ALMA sample ($10.4$). In terms of molecular gas mass ($8.6 \lesssim \log(M_{\rm mol} / {\rm M}_\odot) \lesssim 10.2$), the median of this spiral sub-sample ($\log(M_{\rm mol} / {\rm M}_\odot) = 9.5$) is slightly higher than the median in PHANGS–ALMA ($9.2$); for star formation rates ($-0.44 \lesssim \log({\rm SFR} / [{\rm M}_\odot\,{\rm yr}^{-1}]) \lesssim 1.23$), the median is moderately higher ($\log({\rm SFR} / [{\rm M}_\odot\,{\rm yr}^{-1}]) = 0.36$) than across PHANGS–ALMA ($0.00$). We list the galaxies studied in this paper in Table [2](#table:sample) along with some basic properties.

## Molecular gas surface densities

We measure molecular gas surface densities from the $^{12}$CO(2–1) transition using the public data from the PHANGS–ALMA survey. The observations cover the star-forming disc (typically close to the ${\sim}0.5 R_{25}$ radius[^3]) and accounting for ${\sim} 70\%$ of all the CO emission (cite: 2021ApJS..255...19L). To determine the CO integrated intensity, we employ the zeroth-order moment maps based on the ‘broad’ masks presented in (cite: 2021ApJS..255...19L) and publicly released in July 2022 (PHANGS–ALMA version 4.0). These masks feature high CO flux completeness at the expense of somewhat higher noise and thus are more suitable for our purpose.

The conversion of the CO(2–1) integrated intensity (in K km s$^{-1}$) to molecular gas surface density (in M$_\odot$ pc$^{-2}$) requires adopting both a conversion factor, $\alpha_{\rm CO}$, and a line ratio, $R_{21}= \mbox{CO(2--1)}/\mbox{CO(1--0)}$. We employed the $\alpha_{\rm CO}$ prescription adopted in many previous PHANGS studies, which includes a radial trend according to the metallicity gradient in galaxies ((cite: 2020ApJ...901L...8S), based on (cite: 2017MNRAS.470.4750A)).

We calculated azimuthal arm/interarm contrasts in radial bins (Sect. [2.7](#Sec:method) and Fig. [1](#fig:method)); thus, in practice, any radial dependence of $\alpha_{\rm CO}$ is effectively cancelled out (other than very small variations within each radial bin). This means that we would measure nearly identical contrasts if we assumed a constant Galactic of $\alpha_{\rm CO} = 4.35$ M$_\odot$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ or any other prescription that varies only with radius. However, azimuthal variations in the real $\alpha_{\rm CO}$ are not completely negligible and next we estimate the uncertainty introduced by assuming a purely radial conversion factor.

Under the assumption that $\alpha_{\rm CO}$ primarily tracks metallicity variations within galaxies, we indeed expect a predominantly radial trend with much more limited azimuthal effects. Systematic arm-to-interarm gas metallicity variations have been found in some galaxies (cite: 2017ApJ...846...39H; 2018A&A...618A..64H; 2020MNRAS.492.4149S), typically of the order of $\sim$0.05 dex in $12+\log({\rm O/H})$, while in other cases such arm-to-interarm variations were found to be even more limited or absent (cite: 2019ApJ...887...80K; 2022MNRAS.509.1303W). According to the metallicity-dependent PHANGS $\alpha_{\rm CO}$ prescription (cite: 2020ApJ...901L...8S), a change of 0.05 dex in metallicity would imply a change of 0.07-0.09 dex in $\alpha_{\rm CO}$. Therefore, we conservatively assume a 0.1 dex uncertainty on the molecular surface density contrasts as a consequence of neglecting azimuthal changes in $\alpha_{\rm CO}$.

(cite: 2024ApJ...961...42T) recently put forward an $\alpha_{\rm CO}$ prescription that depends on CO velocity dispersion, tracing the CO optical depth (while, for near-solar metallicities, the correlation of $\alpha_{\rm CO}$ with metallicity is interpreted as coincidental, as both tend to drop with increasing radius). The CO velocity dispersion measured on 150 pc scales and averaged (intensity-weighted) over 1.5 kpc-sized apertures, $\langle \Delta v \rangle_{\rm 150\,pc}$, does not vary too much between arm and interarm regions. For our sample, the median $\langle \Delta v \rangle_{\rm 150\,pc}$ is only $13$% higher in spiral arms (with a scatter of ${\sim}25$%), which has an impact of only ${\sim}10$% on $\alpha_{\rm CO}$. This is well within the 0.1 dex uncertainty that we assume (but could introduce a systematic effect on $\Sigma_\mathrm{mol}$ and SFE contrasts at the ${\sim}10$% level).

For simplicity, we adopted a constant line ratio of $R_{21}=0.65$ (cite: 2013AJ....146...19L; denBrok21). The latest studies examining $R_{21}$ variations in galaxies, albeit at coarser resolution, measure a typical azimuthal scatter of $\sim$20% in $R_{21}$ as long as we exclude galaxy outskirts (cite: denBrok21; 2022ApJ...927..149L). This roughly agrees with previous studies, which typically found standard deviations of around 0.1 dex in $R_{21}$ within a given galaxy (cite: 2013AJ....146...19L; 2021PASJ...73..257Y). The CO(2–1) line ratio is known to vary with local conditions, typically increasing towards galaxy centres and, more generally, mildly increasing with $\Sigma_{\rm SFR}$. (cite: 2022ApJ...927..149L) suggest a power-law dependence, $R_{21} \propto \Sigma_{\rm SFR}^{0.13}$, comparing measurements across different galaxies. As a corollary, this could suggest slightly higher $R_{21}$ in spiral arms than in matched interarm regions, since $\Sigma_{\rm SFR}$ is typically higher in spirals. However, (cite: denBrok21) found very limited differences in $R_{21}$ between arm and interarm within galaxies (if any, paradoxically larger $R_{21}$ in interarm regions, as seen in M51; (cite: 2022A&A...662A..89D)). Therefore, there is no clear indication for a systematically higher $R_{21}$ in spiral arms, and the observed variations are well within the 0.1 dex azimuthal scatter that we assume. Thus, we take 0.1 dex as a reasonable uncertainty on the molecular contrast due to arm-to-interarm variations in $R_{21}$. Adding this in quadrature with the uncertainty in $\alpha_{\rm CO}$, we consider a global uncertainty of 0.14 dex in our estimate of molecular gas surface density contrast.

## Star formation rate measurements

Razza et al. (in prep.) obtained ground-based narrow-band H$\alpha$ images for a total of 65 galaxies from the PHANGS–ALMA parent sample. These were observed with the Wide Field Imager (WFI) at the MPG 2.2-metre telescope in La Silla or with the DirectCCD camera at the du Pont 2.5-metre telescope in Las Campanas between 2016 and 2019 (these maps have appeared previously, e.g. in (cite: 2022ApJ...927....9P)). Both broad-band and narrow-band images were obtained, which allowed us to derive H$\alpha$ continuum-subtracted images. The resolution, limited by seeing, is typically ${\sim} 1\ensuremath{''}$ at a full width at half maximum (FWHM) ranging from $0.6\ensuremath{''}$ to $1.3\ensuremath{''}$, ${\sim}100$ pc. The H$\alpha$ maps were corrected for filter transmission as well as \[N ii\] contamination (assuming $[\textsc{N\,ii}]/\textrm{H}\alpha = 0.3$; see (cite: 2019ApJ...887...49S)).

A robust conversion from H$\alpha$ fluxes to SFR should also account for obscured star formation; otherwise, extinction will make us underestimate SFRs in regions that are strongly obscured by dust. We use narrow-band H$\alpha$ observations to trace star formation, and calibrate the impact of extinction using Balmer-corrected H$\alpha$ maps. This is possible for a subset of 13 galaxies, and for a smaller field of view than the narrow-band maps, where we have extinction-corrected H$\alpha$ SFR maps from PHANGS–MUSE (cite: 2022A&A...659A.191E; 2023A&A...670A..67B) at ${\sim} 1\ensuremath{''}$ resolution. These rely on the Balmer decrement (see e.g. (cite: 2012MNRAS.419.1402G)), which allows us to measure extinction based on the $L_{\rm H\alpha}/L_{\rm H\beta}$ ratio (assuming case B recombination, temperature $T = 10^4$ K, and density $n_{\rm e} = 10^2$ cm$^{-3}$; see (cite: 2023A&A...670A..67B) for details).

As shown in Appendix [7](#sec:AppendixMUSE), there is a tight correlation between the MUSE SFR contrasts with and without extinction (Spearman rank coefficient 0.97), with a systematic amplification of contrasts when extinction is accounted for. We find that the following power-law captures this systematic amplification very well:

$$\begin{equation}
    \log\left({\rm SFR_{contrast}^{ext-corr}}\right)=-0.0013 + 1.1799\, \log\left({\rm H\alpha_{contrast}^{no-ext}}\right),
\end{equation}$$

where ${\rm SFR_{contrast}^{ext-corr}}$ is the arm/interarm contrast of SFR from MUSE, including the extinction correction based on the Balmer decrement, and ${\rm H\alpha_{contrast}^{no-ext}}$ is the arm/interarm contrast of H$\alpha$ from MUSE, switching off the extinction correction. The scatter around this relation (${\sim}0.1$ dex) gives us an idea of the uncertainty associated with this empirical approach.

Additionally, in Appendix [7](#sec:AppendixMUSE) we also consider the uncertainty due to narrow-band H$\alpha$ calibration. We estimate this by comparing the narrow-band H$\alpha$ contrasts to the MUSE-based H$\alpha$ contrasts (ignoring extinction). The scatter in this case is slightly smaller than the effect of extinction, but not negligible (0.059 dex). Therefore, we add both in quadrature to obtain a representative uncertainty on the SFR contrasts of 0.122 dex. In Appendix [9](#Sec:DIG) we discuss that diffuse ionised gas (DIG) is unlikely to have a major impact on SFR contrasts according to our observational strategy.

## H I data

In Section [3.5](#Sec:effect_HI), we consider the effect of including neutral atomic gas in the contrast measurements. We employ 21 cm interferometric maps from a number of surveys from the Karl G. Jansky Very Large Array (VLA). Most of them come from new VLA observations for PHANGS (data that have previously appeared in (cite: 2022AJ....164...43S) and (cite: 2023arXiv231100407C)), while others come from THINGS (cite: 2008AJ....136.2563W), VIVA (cite: 2009AJ....138.1741C), HERACLES (cite: 2009AJ....137.4670L), or specific programs on individual galaxies. The resolution of the H I maps ranges from ${\sim}10{-}60''$ (FWHM), depending on the target, which translates into a physical resolution of ${\sim}0.5{-}4$ kpc for our spiral galaxy sample.

We apply the following equation to transform H I observations to atomic gas surface density, which assumes an optically thin 21 cm emission:

$$\begin{equation}
    \frac{\Sigma_{\rm atom}}{\rm M_\odot \, pc^{-2}} = 2.0\times10^{-2} \left(\frac{I_{\rm HI}}{\rm K\,km\,s^{-1}}\right) \, \cos{i}~,
    \label{eq:SigHI}
\end{equation}$$

where $\Sigma_{\rm atom}$ includes the 1.36 factor to account for helium and heavier elements. The $\cos{i}$ term corrects for galaxy inclination (adopted from the PHANGS Sample Table 1.6, following (cite: 2020ApJ...897..122L)).

## Stellar mass surface densities

For most galaxies, we use a set of stellar mass maps based on *Spitzer* $3.6$ $\mu$m imaging obtained from the *Spitzer* Survey of Stellar Structure in Galaxies (S$^4$G; (cite: 2010PASP..122.1397S)), with a PSF of $1.7''$. The mass maps rely on an Independent Component Analysis (ICA) correction for dust emission, present at $3.6$ $\mu$m on top of the photospheric emission from old stars. The method, introduced in (cite: 2012ApJ...744...17M), was applied to the entire S$^4$G sample in (cite: 2015ApJS..219....5Q). It makes use of the neighbouring 4.5 $\mu$m band and exploits the fact that stellar and dust emission are expected to have very different \[3.6\]-\[4.5\] colours. Then, ICA (similar to principal component analysis, PCA) identifies the global stellar and dust \[3.6\]-\[4.5\] colours that best describe the two underlying components. Since dust emission at $3.6$ $\mu$m is strongest around star-forming regions, the arm/interarm contrast nearly always decreases when shifting from the original IRAC $3.6$ $\mu$m to the ICA-based dust-corrected stellar mass map. For the galaxies which are not in S$^4$G, we use the original IRAC $3.6$ $\mu$m maps (not corrected with ICA, see (cite: 2021A&A...656A.133Q) for details).

The conversion from IRAC fluxes to stellar mass surface densities requires adopting a mass-to-light (M/L) ratio. We assume a constant M/L on the ICA-corrected $3.6$ $\mu$m maps following (cite: 2014ApJ...788..144M), which is expected to provide a reliable conversion to stellar masses within 0.1 dex (accounting for unconstrained age and metallicity differences, (cite: 2014ApJ...788..144M)). For our purposes, we do not care about the exact normalisation of M/L, or about possible radial variations, as they will cancel out in the arm/interarm contrasts. We still conservatively assume an uncertainty of 0.1 dex on the arm/interarm stellar surface density contrasts to account for possible arm/interarm variations in M/L (the range of M/L expected at $3.6$ $\mu$m after correcting with ICA; (cite: 2014ApJ...788..144M)). To test the robustness of our choice for the M/L and our adopted error bar, for 13 galaxies we compare the IRAC contrasts with contrasts measured from the MUSE stellar mass map and we find excellent agreement (see Appendix [8](#Sec:stellarcon)). We also consider the typical change of 0.04 dex on the arm/interarm contrast due to the ICA correction as a conservative error bar. Adding both in quadrature, we obtain a global uncertainty of 0.11 dex for the stellar arm/interarm contrasts. Figure [13](#fig:MUSE_SigStar_vs_IRAC-ICA) confirms that the stellar contrasts based on the ICA-corrected maps agree well with independent estimates from stellar population fitting in PHANGS–MUSE, and that the uncertainty of 0.11 dex assumed here is reasonable (see Appendix [8](#Sec:stellarcon) for details).

## Spiral masks

![](Fig_thin_masks.png)

### Original spiral masks

Throughout this paper, we use the spiral component of the environmental masks defined in (cite: 2021A&A...656A.133Q). These masks delimit morphological features visually identified on NIR images which, in addition to spiral arms, include centres, bars, rings, lenses, bulges, and discs.

Specifically, spiral masks were constructed following three steps. Firstly, regions of bright $3.6$ $\mu$m emission were identified along each spiral arm (using an unsharp-mask approach) and fitted with an analytic log-spiral function in the plane of the galaxy. Secondly, analytic log-spiral curves were assigned a width determined empirically based on CO emission. Finally, the resulting masks were visually inspected and the starting and ending point of some segments were extended in order to enforce continuity. For most galaxies, the near-infrared (NIR) images and the analytic log-spiral fits come from S$^4$G (cite: 2015A&A...582A..86H), but we also relied on archival and newly obtained *Spitzer* $3.6$ $\mu$m observations in some cases, where we also performed the log-spiral fitting, as explained in (cite: 2021A&A...656A.133Q).

The spiral masks from (cite: 2021A&A...656A.133Q) consist of perfectly smooth, dilated log-spiral segments, with a typical width of ${\sim}1{-}2$ kpc in order to accommodate most $3.6$ $\mu$m, CO, and H$\alpha$ emission along the arm. Locally, the distribution of molecular gas or star formation in the arms often looks thinner, but the presence of kinks and irregularities requires this width in order to warrant full coverage along the entire arm (Fig. [1](#fig:method)). In this paper, we also consider a more restrictive strategy that results in thinner (and more irregular) spiral masks, as explained next. In Appendix [10](#Sec:narrow), we show that contrasts are not strongly affected by the width of the spiral masks, and thus, for simplicity, across this paper we use the original masks presented in (cite: 2021A&A...656A.133Q).

### A set of thinner spiral maskss

To test how the width of the adopted spiral regions affects the arm/interarm contrast, we construct a set of narrower spiral masks[^4]. These masks are not used for the main measurements in this paper, which rely on the public masks from (cite: 2021A&A...656A.133Q). The alternative narrow masks introduced here are used in Appendix [10](#Sec:narrow) to quantify the effect of mask width, concluding that it should not significantly affect our main conclusions.

The strategy to build narrower masks is illustrated in Fig. [2](#fig:thin_masks). Along the log-spiral curve that defines the backbone of the spiral masks from (cite: 2021A&A...656A.133Q), we determine the line perpendicular to the log-spiral function at each point, and identify the position of the maximum CO or H$\alpha$ intensity along this perpendicular line within the boundaries of the original spiral mask. This process is repeated for all the pixels along the log-spiral curve, resulting in a distribution of pixels of peak intensity from each of these cuts perpendicular to the spiral arm. The corresponding set of pixels are assigned a value of 1, while the rest is set to zero, and the image is smoothed with an empirically chosen Gaussian kernel of ${\rm FWHM}=7.5''$, on which we impose a threshold of 0.01. This is essentially equivalent to dilating the ridge of peak emission, ignoring isolated outliers.

This process is applied independently to the CO and H$\alpha$ maps, resulting in two narrow masks that are very similar, but not identical. We take the union of the two masks to yield a final narrow mask. By construction, the narrow mask is always a subset of the original spiral mask, as we force the dilated mask to be within the original mask. The narrow mask typically covers ${\sim}50$% of the area of the original mask. In Appendix [10](#Sec:narrow) we show how this choice of spiral mask affects the arm/interarm contrast measurements.

## Strategies to measure arm/interarm contrasts

There are different approaches to derive arm/interarm contrasts in nearby galaxies. As illustrated in Fig. [1](#fig:method), our nominal method splits each galaxy into a number of radial bins in the plane of the galaxy; for each radial bin, we consider the mean[^5] surface density within the footprint of each spiral segment at that radius (arm value), and divide it by the mean surface density within the ring outside the spiral mask (interarm value). We considered the intensity maps without clipping and, therefore, we should not be biased by non-detections. At the outermost radial bins, we require at least 50% of the spiral and interarm pixels in the ring to lie within the PHANGS–ALMA field of view for the measurement to be considered. The width of the radial bins is chosen to be 500 pc in the plane of the galaxy to mitigate stochastic sampling effects[^6], which results in elliptical annuli in the plane of the sky (according to the disc inclination and position angle from the PHANGS sample table 1.6, which follow (cite: 2020ApJ...897..122L)). This allows us to plot each radial bin independently and examine trends with galactocentric radius. Each galaxy typically contributes around a dozen measurements in 500 pc-wide radial bins. Additionally, we also plot with a different symbol the average contrast across each spiral segment (typically two or three datapoints per galaxy, depending on how many spiral arms the galaxy has).

This radial approach has the advantage of simplicity, being easily reproducible, and assigning each pixel uniquely to one bin. To zeroth-order, gas in a spiral galaxy moves on approximately circular orbits, and stellar or gas surface density follow roughly exponential radial profiles; this motivates the interest of splitting bins by radius. However, since the pitch angle of spiral arms varies considerably from galaxy to galaxy, this method implies that, sometimes, a 500 pc radial bin will encompass a very large area of a spiral, spanning a large interval in azimuth (see Fig. 1), while in other cases, when the spiral is nearly perpendicular to the elliptical annulus, the resulting spiral bin will have a much smaller area. Thus, despite providing a uniform sampling in galactocentric radius, this method yields an inhomogeneous sampling in terms of spiral arm area.

In Appendix [11](#sec:sanity_checks), we consider two alternatives for the sampling of the arm/interarm contrasts. They both consider regularly spaced ‘boxes’ along each spiral segment, whose boundaries cut the log-spiral spine perpendicularly at regular intervals of 500 pc. The first alternative defines the interarm as all non-spiral pixels at matched galactocentric radii for each bin. In the second alternative approach, the spiral bins are defined exactly the same way, but the interarm is measured as adjacent boxes, on both sides immediately next to each spiral bin, to provide a more local reference for the interarm region. Even though the sampling method affects the actual values of the contrasts, our results remain qualitatively the same independently of these different choices.

We note that these methods differ from the arm/interarm contrasts presented in (cite: 2021A&A...656A.133Q). In that paper, the arm-to-interarm contrast was calculated as the ratio of the mean surface density within the spiral mask (considering all spiral segments simultaneously) to the mean surface density in the area outside the spiral mask at matched galactocentric radius. This results in a single number for each contrast per galaxy, and therefore differs from the present approach, which examines each spiral segment separately and considers the radial variation of the contrast. Our approach here is also different from the one in (cite: 2021ApJ...913..113M), who examined contrasts based on percentiles of stellar and molecular gas surface brightness as a function of radius, without explicit reference to the spiral morphology. Since we want to specifically study the role of spiral arms in this paper, we instead use the spiral masks from (cite: 2021A&A...656A.133Q). Our results yield a consistent picture with (cite: 2021ApJ...913..113M) regarding the relation between stellar and gas contrasts.

# Results

We start by presenting our measurements of arm/interarm contrasts at ${\sim}100$ pc scales

in stellar mass, molecular gas, and star formation surface density, as well as the SFE (in Sect. [3.1](#Sec:highres)). In Sect [3.2](#Sec:GD_vs_rest), we demonstrate that grand-design spirals tend to have larger contrasts. In Sect. [3.3](#Sec:correl_stellar), we examine how contrasts strongly correlate with each other. In Sect. [3.4](#Sec:SFE_in_spirals) we address the question of whether spiral arms systematically boost star formation efficiency, and we consider the role of atomic gas in Sect. [3.5](#Sec:effect_HI). We examine the radial variation of contrasts in Sect. [3.6](#Sec:radial) and symmetry between opposite spiral segments in Sect. [3.7](#Sec:results_symmetry). Finally, we assess the effect of resolution in Sect. [3.8](#Sec:effect_res). More technical details are presented in the Appendices, including an empirical calibration to account for extinction on SFR contrasts (Appendix [7](#sec:AppendixMUSE)), a comparison with alternative stellar mass tracers (Appendix [8](#Sec:stellarcon)), assessing the impact of DIG (Appendix [9](#Sec:DIG)), and mask width (Appendix [10](#Sec:narrow)), as well as additional sanity checks (Appendix [11](#sec:sanity_checks)).

## Range of arm/interarm contrasts in $\Sigma_\mathrm{\star}$, $\Sigma_\mathrm{mol}$, $\Sigma_\mathrm{SFR}$, and SFE

![](contrast_ranges.png)

|  | $\Sigma_\star$ | $\Sigma_\mathrm{mol}$ | $\Sigma_\mathrm{SFR}$ | SFE |
|:---|:--:|:--:|:--:|:--:|
| Nominal contrasts | $1.28_{-0.26}^{+0.49}$ | $2.22_{-0.96}^{+2.19}$ | $2.56_{-1.61}^{+4.59}$ | $1.16_{-0.58}^{+1.23}$ |
| Contrasts from MUSE | $1.21_{-0.29}^{+0.46}$ | $2.28_{-0.96}^{+2.12}$ | $2.72_{-1.57}^{+4.55}$ | $1.21_{-0.54}^{+0.93}$ |
| Low resolution (1.5 kpc) | $1.15_{-0.21}^{+0.48}$ | $1.49_{-0.49}^{+1.35}$ | $1.50_{-0.57}^{+2.20}$ | $1.04_{-0.31}^{+0.56}$ |
| Narrow masks | $1.28_{-0.24}^{+0.53}$ | $2.53_{-1.02}^{+2.83}$ | $3.11_{-1.97}^{+5.45}$ | $1.21_{-0.59}^{+1.23}$ |
| Thinner radial bins (250 pc) | $1.27_{-0.25}^{+0.47}$ | $2.25_{-1.10}^{+2.48}$ | $2.54_{-1.56}^{+4.92}$ | $1.15_{-0.61}^{+1.33}$ |
| Wider radial bins (1000 pc) | $1.27_{-0.29}^{+0.49}$ | $2.14_{-0.81}^{+2.48}$ | $2.34_{-1.34}^{+4.56}$ | $1.14_{-0.51}^{+1.09}$ |
| Perpendicular bins along spiral arms | $1.34_{-0.32}^{+0.68}$ | $2.31_{-1.13}^{+2.94}$ | $2.64_{-1.74}^{+7.30}$ | $1.16_{-0.63}^{+1.62}$ |
| Perpendicular bins with adjacent interarm | $1.14_{-0.18}^{+0.27}$ | $2.19_{-1.24}^{+3.37}$ | $2.76_{-1.78}^{+6.13}$ | $1.17_{-0.73}^{+1.91}$ |
| Nominal - Grand design spirals | $1.34_{-0.33}^{+0.57}$ | $2.73_{-1.36}^{+3.06}$ | $3.12_{-2.08}^{+6.74}$ | $1.16_{-0.57}^{+1.56}$ |
| Nominal - Rest of spirals | $1.23_{-0.19}^{+0.30}$ | $1.90_{-0.78}^{+1.04}$ | $2.00_{-1.14}^{+3.15}$ | $1.17_{-0.58}^{+1.06}$ |
| Nominal - High M$_\star$ | $1.34_{-0.34}^{+0.49}$ | $2.70_{-1.34}^{+3.09}$ | $3.14_{-2.14}^{+6.91}$ | $1.17_{-0.61}^{+1.51}$ |
| Nominal - Low M$_\star$ | $1.24_{-0.19}^{+0.39}$ | $1.80_{-0.68}^{+1.24}$ | $1.85_{-0.95}^{+3.18}$ | $1.13_{-0.54}^{+1.21}$ |
| Nominal - High SFR | $1.33_{-0.30}^{+0.51}$ | $2.46_{-1.15}^{+2.73}$ | $3.07_{-2.17}^{+5.28}$ | $1.18_{-0.60}^{+1.54}$ |
| Nominal - Low SFR | $1.19_{-0.20}^{+0.44}$ | $2.02_{-0.90}^{+2.00}$ | $2.13_{-1.17}^{+3.99}$ | $1.11_{-0.53}^{+1.00}$ |
| Nominal - High $\Delta$MS | $1.41_{-0.34}^{+0.48}$ | $2.32_{-1.02}^{+2.92}$ | $3.05_{-2.10}^{+5.33}$ | $1.23_{-0.64}^{+1.57}$ |
| Nominal - Low $\Delta$MS | $1.17_{-0.19}^{+0.39}$ | $2.06_{-0.93}^{+1.99}$ | $2.16_{-1.25}^{+3.84}$ | $1.09_{-0.53}^{+0.85}$ |
|  |  |  |  |  |

Table notes: arm/interarm contrasts in the surface density of stellar mass, molecular gas, star formation rates, and SFE (median and 16$^{\rm th}$–84$^{\rm th}$ percentile range, measured on galactocentric rings of 500 pc width). The nominal contrasts rely on the masks from (cite: 2021A&A...656A.133Q), while the narrow masks refer to those introduced here in Sect. [2.6.2](#Sec:thinnersp). The two alternative sampling schemes based on perpendicular bins are explained in Appendix [11](#sec:sanity_checks) (Fig. [16](#fig:binning_alternatives)). Low and high M$_\star$ refer to the bottom or top 50% of stellar masses in the sample (threshold $3.4 \times 10^{10}$ M$_\odot$); analogously for SFRs (threshold $2.3$ M$_\odot$ yr$^{-1}$) and $\Delta$MS (threshold $0.234$ dex).

For each spiral segment, we measure the arm/interarm contrast in the surface density of stellar mass ($\Sigma_\mathrm{\star}$), molecular gas ($\Sigma_\mathrm{mol}$), star formation rate ($\Sigma_\mathrm{SFR}$), and SFE of the molecular gas (which we define as the inverse of the depletion time, ${\rm SFE} = 1/ \ensuremath{\tau_\mathrm{dep}}= \ensuremath{\Sigma_\mathrm{SFR}}/ \ensuremath{\Sigma_\mathrm{mol}}$). The measurements are performed on radial bins following elliptical annuli of matched galactocentric radii with a width of 500 pc, as explained in Sect. [2.7](#Sec:method) and illustrated in Fig. [1](#fig:method). We only consider measurements if at least 50% of the pixels in a given spiral bin (and 50% of the corresponding interarm region) fall within the PHANGS–ALMA footprint, which is typically rectangular. This condition excludes NGC 1365 completely, as the CO coverage beyond the bar is very limited. When performing this analysis, we also lacked narrow-band H$\alpha$ data for six galaxies[^7], for which we could only consider $\Sigma_\star$ and $\Sigma_\mathrm{mol}$. This results in a total of 27 spiral galaxies (excluding NGC 1365, as explained above) and 59 spiral segments with $\Sigma_\mathrm{\star}$ and $\Sigma_\mathrm{mol}$ measurements, out of which 21 galaxies (44 spiral segments) also have $\Sigma_\mathrm{SFR}$ information. Table [\[table:stats\]](#table:stats) summarises the contrast distributions that we obtain for different galaxy subsets and approaches. To make measurements more directly comparable, in Table [\[table:stats\]](#table:stats) and the following figures involving SFRs, we only include stellar and CO contrasts for galaxies where SFR is available (i.e. the $\Sigma_\mathrm{\star}$ and $\Sigma_\mathrm{mol}$ ranges correspond to the same set of radial bins as the SFR contrasts).

Figure [3](#fig:contrast_ranges) shows the median and dispersion of arm/interarm contrasts for each spiral segment across PHANGS galaxies ordered by decreasing stellar mass. The stellar contrast tends to be smaller and with more limited fluctuations, whereas the CO or SFR contrasts tend to span large ranges (their $x$ axis covers different ranges), implying that, even within a given galaxy and along a single spiral segment, there are significant fluctuations with galactocentric radius. In some cases, these fluctuations even lead to negative contrasts in the logarithmic scale, which is not necessarily unphysical, and simply points to radial bins where the mean interarm value is slightly higher than the mean arm value. Looking at the distribution of SFE contrast, we see that it is not systematically positive; while some galaxies do seem to show a slight preference for either enhanced or suppressed SFE in spirals, in most cases, the SFE contrast shows values both above and below unity within a galaxy. This already highlights the diversity of physical conditions in spiral arms; we examine SFE in more detail below in Sect. [3.4](#Sec:SFE_in_spirals).

![](Violin_plots_GD_rest.png)

Figure [4](#fig:violin_plot_GD-vs-rest) shows the aggregated distribution of contrasts across all the PHANGS radial bins in our sample at ${\sim}100$ pc resolution. For a more fair comparison, here we only include bins for which $\Sigma_\mathrm{\star}$, $\Sigma_\mathrm{mol}$, and $\Sigma_\mathrm{SFR}$ measurements exist simultaneously at a given radius. It immediately stands out that the range of stellar mass contrasts is fairly modest compared to the contrast in molecular gas or star formation. The stellar contrast is typically between a few percent and around 50%, much smaller than $\Sigma_\mathrm{mol}$ or $\Sigma_\mathrm{SFR}$ contrasts, which often reach factors of ${\sim}2{-}3$ (see Table [\[table:stats\]](#table:stats)). This is because even a moderate spiral potential can trigger a strong response in the gas (as shown by (cite: 1969ApJ...158..123R)). (cite: 2021ApJ...913..113M) also found much smaller stellar than molecular gas contrasts in the PHANGS sample (based on flux percentiles in galactocentric radial bins, without explicitly defining spiral masks).

The $\Sigma_\mathrm{mol}$ and $\Sigma_\mathrm{SFR}$ contrasts follow a wide distribution, from just a few percent up to ${\sim}10$ in the most extreme cases. The median contrast is slightly higher for $\Sigma_\mathrm{SFR}$ than $\Sigma_\mathrm{mol}$, but the scatter is also particularly pronounced, exceeding the 16$^{\rm th}$–84$^{\rm th}$ percentile range of $\Sigma_\mathrm{mol}$ contrasts by as much as a factor of two (Table [\[table:stats\]](#table:stats)). This implies that the fluctuations in arm/interarm contrast are larger for star formation than for molecular gas. This could reflect the fact that spiral arms act directly on the gas, and indirectly on star formation, involving additional physics that controls the collapse of gas to form stars and which introduces scatter. We discuss this further in Sect. [4.1](#Sec:discusscontr).

One of the main questions that motivate this paper is quantifying whether star formation proceeds more efficiently in spiral arms than in interarm regions when examined at 100 pc scales. The right panel of Fig. [4](#fig:violin_plot_GD-vs-rest) provides an answer to this: in some cases SFE is indeed enhanced in spiral arms, but in (many) other cases the opposite happens. We examine this problem in greater detail below in Sect. [3.4](#Sec:SFE_in_spirals).

The magnitude of the molecular and SFR contrasts that we measure broadly agrees with previous results from the literature (most of them at lower spatial resolution), where typical gas surface densities were found to be a few times higher in spiral arms than in interarm regions (cite: 1988Natur.334..402V; 1993A&A...274..123G; 1996MNRAS.283..251K; 2003PASJ...55..191N; 2009A&A...495..795H; 2020ApJ...901L...8S). In (cite: 2021A&A...656A.133Q) we also measured for PHANGS galaxies, using the same nominal masks albeit at lower resolution, that spiral arms have typically ${\sim}2$ times higher molecular gas and SFR surface densities than the interarm, with a range from less than a factor of $2$ up to a factor of ${\sim}10$ on a linear scale. Our results are also in qualitative agreement with the analysis presented in (cite: 2021A&A...650A.134P) and (cite: 2022A&A...663A..61P), who examined star formation scaling relations involving $\Sigma_\mathrm{SFR}$, $\Sigma_\mathrm{mol}$, and $\Sigma_\mathrm{\star}$ in the PHANGS–MUSE sample (18 galaxies). Their main conclusion is that the relations involving stellar surface density vary strongly with galactic environment, with a higher normalisation in $\Sigma_\mathrm{SFR}$ and $\Sigma_\mathrm{mol}$ as a function of $\Sigma_\mathrm{\star}$ for spiral arms than for ‘disc’ (which includes interarm regions). This implies that, while globally there is a nearly linear correlation between stellar mass and molecular gas mass in galaxies, in detail, the same relation cannot hold everywhere within discs, because $\Sigma_\mathrm{mol}$ arm/interarm contrasts (or $\Sigma_\mathrm{SFR}$ contrasts) are much larger than the contrasts in $\Sigma_\mathrm{\star}$(as explicitly shown by (cite: 2021ApJ...913..113M)). This results in a higher normalisation in the scaling relations of $\Sigma_\mathrm{mol}$ and $\Sigma_\mathrm{SFR}$ as a function of $\Sigma_\mathrm{\star}$ for spiral arms (cite: 2021A&A...650A.134P; 2022A&A...663A..61P).

In detail, the measured contrast in a given galaxy depends on resolution and, to a lesser degree, on methodology (which we discuss in Sect. [4.4](#Sec:discuss_methodology)). For example, for NGC 4321, (cite: 1996A&A...308...27K) obtained an average molecular contrast of ${\sim}1.7$ and ${\sim}1.8$ for the north and south spiral, respectively, at a resolution of $15''$ (${\sim}1$ kpc). They targeted individual pointings with the Nobeyama 45 m telescope along the arms and immediate interarm regions (similar to the second binning alternative that we introduce in Appendix [11](#sec:sanity_checks)). Despite the methodological differences, these molecular contrasts are very similar to the ones we obtain at 1.5 kpc resolution, $1.8$ and $1.6$ for each arm, respectively. However, when we shift to high resolution, the molecular contrasts become 2.7 and 2.4 for the north and south arm, respectively. This warns against direct comparison of contrasts derived at different resolutions.

## Grand-design spirals show larger contrasts (and effect of $M_\star$, SFR, $\Delta$MS)

The violin plots in Fig. [4](#fig:violin_plot_GD-vs-rest) are split into grand-design spirals (17 galaxies) and the rest (multi-armed and flocculent, 11 galaxies). We follow the NIR visual classification from (cite: 2015ApJS..217...32B) for galaxies in the S$^4$G survey, and the definitions adopted in (cite: 2021ApJ...913..113M) otherwise. We find a significantly different distribution between the contrasts in grand-design galaxies and the rest for $\Sigma_\mathrm{\star}$, $\Sigma_\mathrm{mol}$, and $\Sigma_\mathrm{SFR}$. For each tracer, the contrast is higher for grand-design spirals: the median surface density enhancement is 50% higher for stellar mass, and almost a factor of two higher for molecular gas and star formation. (cite: 2021ApJ...913..113M) also found that, at fixed 3.6 $\mu$m contrast, CO contrasts are slightly larger in grand-design spirals than in multi-arm and flocculent galaxies. We ran a Kolmogorov-Smirnov test for the two populations, finding a vanishingly small probability ($p<0.1\%$) that the grand-design contrasts are drawn from the same population as the rest of spirals for $\Sigma_\mathrm{\star}$, $\Sigma_\mathrm{mol}$, and $\Sigma_\mathrm{SFR}$. This is not the case for SFE contrasts, though ($p=0.49$), which do not show a significant difference for grand-design spirals. A Jackknife approach also confirms this: if we remove one galaxy at a time and recompute medians, in all cases the $\Sigma_\mathrm{\star}$, $\Sigma_\mathrm{mol}$, and $\Sigma_\mathrm{SFR}$ contrast remains higher in grand-design spirals than in the rest. If we consider the $\Sigma_\mathrm{\star}$ contrast for an extended field of view (all $\Sigma_\mathrm{\star}$ measurements across entire spiral arms, no longer limited to the PHANGS–ALMA field of view), the difference between grand-design spirals and the rest becomes even more acute, with a median $\Sigma_\mathrm{\star}$ enhancement that is three times larger for grand-design (61%) than for the other spiral morphologies (21%), as shown in Fig. [14](#fig:violin_plot_GD-vs-rest-extended).

The difference in contrasts for grand-design spirals is also mirrored by a difference if we focus on the most massive galaxies. If we split the sample into the 50% of galaxies with the higher stellar masses (above the median $3.4 \times 10^{10}$ M$_\odot$) and the lower stellar masses (below that median), we find higher contrasts for the higher-mass sub-sample, by a similar amount as for grand-design spirals (Table [\[table:stats\]](#table:stats)). The effect is very similar to the split between grand design galaxies and the rest; indeed, grand-design spirals are known to occur preferentially on galaxies with higher stellar masses (cite: 2017MNRAS.471.1070B; 2023MNRAS.518.1022S), and this is also the case for PHANGS galaxies (cite: 2023A&A...676A.113S). Out of the 14 galaxies with the highest stellar masses, 12 galaxies (86%) are grand design, so both sub-samples are closely related. Yet, the difference is not driven exclusively by morphology, because even within grand-design spirals, we also found larger contrasts for the galaxies with higher stellar masses. We find moderate but positive rank correlation coefficients between the $\Sigma_\mathrm{\star}$, $\Sigma_\mathrm{mol}$, and $\Sigma_\mathrm{SFR}$ contrasts and total stellar mass of each galaxy (Spearman $\rho \sim 0.2$ for all datapoints, $p$ value $<1$%), but not between SFE contrast and the stellar mass of the galaxy. The correlations are similarly strong if we instead consider total SFR, and we also find a similar change in the distribution of contrasts when splitting the spiral sample into two halves based on total SFR (above and below the median of 2.29 M$_\odot$ yr$^{-1}$; also related to the split by stellar mass or morphology). However, we do not find any remarkable differences when splitting the sample based on being barred or unbarred, or based on early or late Hubble type.

In Table [\[table:stats\]](#table:stats), we also consider the offset from the star-forming main sequence of galaxies ($\Delta$MS, based on (cite: 2019ApJS..244...24L)), i.e. the vertical offset of each galaxy with respect to the best fit to the relation between SFR and $M_\star$. We find a clear trend for higher contrasts in the galaxies that lie preferentially above the main sequence ($\Delta$MS above $0.234$ dex, the median across the sample), comparable to the one for high $M_\star$. Interestingly, in this case we also find a difference for SFE contrast, which increases for galaxies in the upper half of the sample in terms of $\Delta$MS (median $1.23$ as opposed to $1.09$). Compared to the separation into grand design spirals and the rest, this slightly different SFE behaviour arises from similarly high SFR contrasts but somewhat more limited molecular contrasts for galaxies with a high $\Delta$MS. This is perhaps not too surprising; by imposing a high $\Delta$MS, we are preferentially selecting galaxies with comparatively high SFR (high SFR/$M_\star$), but at the same time those with a more limited $M_\star$, which results statistically in less extreme $\Sigma_\mathrm{mol}$ contrasts. In any case, this demonstrates that the position of a galaxy on the star-forming main sequence matters in terms of the type of spiral response (even though, of course, there is significant scatter, as attested by the large range of 16$^{\rm th}$–84$^{\rm th}$ percentile range).

## Correlations among contrasts

![](CO_SFR_SFE_vs_NIR.png)

![](SFR_vs_CO.png)

Figure [5](#fig:CO_SFR_SFE_vs_NIR) shows a clear correlation between the contrast in $\Sigma_\mathrm{mol}$ and $\Sigma_\mathrm{\star}$, and a similarly strong correlation arises between $\Sigma_\mathrm{SFR}$ and $\Sigma_\mathrm{\star}$. This suggests that the stellar contrast largely dictates how strongly molecular gas and star formation pile up in a given arm. This is perhaps not too surprising, since the stellar contrast sets the depth of the spiral gravitational potential well. The Spearman rank correlation coefficients are $0.73$ and $0.61$, respectively. The trend is superlinear, in the sense that the response of the gas (and star formation) is amplified relative to the contrast in the stellar surface density. In the case of CO, the slope from a bisector fit is $m=1.8$, while for SFR it is even steeper, $m=2.9$. The rank coefficients and linear fits refer to the mean contrasts over entire spiral segments (more details, including all radial bins and uncertainties for the fits, in Table [\[table:stats_appendix\]](#table:stats_appendix)).

(cite: 2021ApJ...913..113M) measured CO contrasts at 150 pc resolution as a function of 3.6 $\mu$m contrast, and found that they follow approximately a 2:1 relation on a log–log scale, with some vertical offset above the reference 2:1 line, and with a Pearson correlation coefficient $R \sim 0.5$. Our measured slope of $m=1.8$ is thus in good agreement with (cite: 2021ApJ...913..113M), but we do not find a vertical offset here, and we find a tighter correlation with Spearman $\rho \sim 0.73$, which could arise from the different method followed (percentiles versus environmental masks). This superlinear relation is consistent with the expectation if gas is compressed as it flows supersonically in response to non-axisymmetric stellar structures (cite: 1969ApJ...158..123R; 2021ApJ...913..113M).

Despite the strong correlation between stellar contrast and the contrast in molecular gas and SFR, the correlation between the contrasts in SFE and stellar surface density is much weaker ($\rho = 0.34$). If we perturb the data points using a Gaussian distribution according to the error bars, the weak positive correlation vanishes (with a bootstrap of $N=10\,000$ runs, the average rank coefficient drops to $\rho=-0.09$). We comment on the impact on SFE in more detail below in Sect. [3.4](#Sec:SFE_in_spirals).

We also examine the contrast in $\Sigma_\mathrm{SFR}$ as a function of $\Sigma_\mathrm{mol}$ contrast, as shown in Fig. [6](#fig:CO_vs_SFR). If the efficiency remains on average similar in spiral arms and interarm regions, we expect the $\Sigma_\mathrm{SFR}$ as a function of $\Sigma_\mathrm{mol}$ contrast to be connected by the Kennicutt-Schmidt relation (cite: 1959ApJ...129..243S; 1998ApJ...498..541K). Indeed, we find an even stronger correlation ($\rho=0.78$) than between $\Sigma_\mathrm{mol}$ or $\Sigma_\mathrm{SFR}$ and $\Sigma_\mathrm{\star}$. The best-fit regression relating the $\Sigma_\mathrm{SFR}$ contrast to the $\Sigma_\mathrm{mol}$ contrast is slightly superlinear (slope $m=1.6$), implying that the star formation contrast exceeds on average the molecular contrast slightly for the cases where the $\Sigma_\mathrm{mol}$ contrast is highest. In other words, the spiral segments or bins with the highest contrasts typically show slightly more efficient star formation in the arms than in interarm regions. This is in agreement with the finding that there is a slightly increased SFE contrast for the highest $\Sigma_\mathrm{\star}$ contrast (which at the same time corresponds to the highest $\Sigma_\mathrm{mol}$ contrasts). We discuss this in more detail in Sect. [3.4](#Sec:SFE_in_spirals).

## Star formation efficiency in spiral arms

Here we analyse whether spiral arms preferentially trigger the collapse of molecular gas to form stars, systematically boosting its SFE. We emphasise that by default we consider the efficiency associated with molecular gas only, ${\rm SFE} = \ensuremath{\Sigma_\mathrm{SFR}}/ \ensuremath{\Sigma_\mathrm{mol}}= 1/ \ensuremath{\tau_\mathrm{dep}}$ (sometimes labelled ${\rm SFE_{mol}}$). This is different from the SFE of the total gas (H I$+$H$_2$); we will examine the effect of including atomic gas below in Sect. [3.5](#Sec:effect_HI).

The right panel of Fig. [4](#fig:violin_plot_GD-vs-rest) demonstrates that SFE is not always enhanced in spiral arms. From a total of 422 radial bins, we find 244 bins in which SFE is higher in spiral arms (while in 178 bins it is higher in interarm regions). Thus, if we pick up random locations along spiral arms, in roughly six out of ten cases we will find a higher SFE in spirals.

The median SFE contrast across all radial bins is $1.16$. If we bootstrap the SFE values within their error bars $10\,000$ times, we confirm that the enhancement of the median with respect to unity is statistically significant (at the $4\sigma$ level). With a Jackknife approach, if we randomly remove half of the datapoints and repeat the process $N=10\,000$ times, the mean remains $1.16$ with a standard deviation of $0.03$ (in fact, only in ${\sim}5$ out of $10\,000$ random cases does removing half of the bins result in a mean SFE contrast below unity). This confirms that the result is robust. Yet, this enhancement of ${\sim}10{-}20$% in SFE is modest compared to the actual enhancement in $\Sigma_\mathrm{mol}$ (median enhancement 120%), $\Sigma_\mathrm{SFR}$ (160%), and is even below the limited enhancement of $\Sigma_\mathrm{\star}$(28%).

Our SFE measurements rely on H$\alpha$ fluxes corrected for extinction following the empirical calibration from Appendix [7](#sec:AppendixMUSE). If we were to take SFR as directly proportional to H$\alpha$, then the SFE enhancement would completely vanish, as shown in Fig. [12](#fig:violin_plot_GD-vs-rest-Ha-only). This emphasises the importance of the extinction correction for SFR and SFE contrasts. For the subsample of 13 galaxies in PHANGS–MUSE, we find a median SFE contrast of $1.21$ from extinction-corrected H$\alpha$ (Balmer decrement). For the same galaxies and field of view as PHANGS–MUSE, our nominal SFE contrast has a median of $1.19$, which reassuringly demonstrates the success of our strategy to account for extinction on arm/interarm contrasts (Appendix [7](#sec:AppendixMUSE)). Conversely, applying the velocity dispersion-dependent $\alpha_{\rm CO}$ from (cite: 2024ApJ...961...42T) leads to an increase of $\Sigma_\mathrm{mol}$ contrasts at the ${\sim}10$% level, which results in SFE contrasts which are ${\sim}10$% higher.

In Figure [5](#fig:CO_SFR_SFE_vs_NIR) we found a strong correlation between $\Sigma_\mathrm{\star}$ and $\Sigma_\mathrm{mol}$ or $\Sigma_\mathrm{SFR}$ contrasts, but a weaker correlation for SFE contrasts (right panel of Fig. [5](#fig:CO_SFR_SFE_vs_NIR), $\rho = 0.34$). This suggests that, while the stellar mass contrast is a clear driver of the accumulation of gas and, indirectly, star formation, it is not as directly linked, in general, with a boost in SFE. Yet, if we focus on the largest $\Sigma_\mathrm{\star}$ contrasts, the median SFE contrast increases significantly. For example, for the top 50% in $\Sigma_\mathrm{\star}$ contrasts ($>1.23$, or $>0.09$ in log), the median SFE contrast rises to $1.40$, and goes up to $2.34$ if we focus on the top 10% of $\Sigma_\mathrm{\star}$ contrasts ($>1.97$, or $>0.29$ in log). Therefore, the largest stellar contrasts do result, on average, in a noticeable increase of SFE. When splitting the sample into grand-design spirals and the rest, a difference in SFE contrasts is not apparent.

Our findings agree with some previous studies which did not find significant differences among spiral types in terms of SFE, either observationally (cite: 2008AJ....136.2846B; 2008AJ....136.2782L; 2016ApJ...827..103K; 2010ApJ...725..534F) or using simulations (cite: 2011MNRAS.417.1318D). Our results also roughly agree with the analysis of PHANGS–MUSE galaxies presented in (cite: 2021A&A...650A.134P; 2022A&A...663A..61P). The arm versus disc variation in the resolved Kennicutt-Schmidt relation ($\Sigma_\mathrm{SFR}$ vs $\Sigma_\mathrm{mol}$) was found to be very limited, the same as the corresponding coefficients in the $\Sigma_\mathrm{SFR}$-$\Sigma_\mathrm{mol}$-$\Sigma_\mathrm{\star}$ plane, in agreement with the SFE arm/interarm contrast oscillating around unity that we have found in this paper. In particular, (cite: 2021A&A...650A.134P) found that spirals show slightly higher $\Sigma_\mathrm{SFR}$ at fixed $\Sigma_\mathrm{mol}$ compared to disc values, but only below $\Sigma_\mathrm{mol} \lesssim 100$ M$_\odot$/pc$^2$ (at higher $\Sigma_\mathrm{mol}$, discs are actually slightly above spirals in the molecular Kennicutt-Schmidt relation; see their Fig. 9). We emphasise that the binned data in (cite: 2021A&A...650A.134P) aggregate measurements from different galaxies and the disc environment includes both interarm regions and discs without spiral masks. Therefore, this is not necessarily representative of the arm/interarm contrasts measured within individual galaxies, and the fact that the offset is small agrees with our overall findings. Our results also agree with Romanelli et al. (in prep.), who do not find significant differences between arm and interarm regions in terms of molecular cloud SFE (inferred cloud lifetime divided by depletion time).

## Atomic gas contrast and its effect on SFE

![](Effect_HI.png)

|  |  |  |
|:---|:--:|:--:|
|  | $\Sigma_\mathrm{gas}$ contrast | SFE contrast |
| H I | $1.22_{-0.21}^{+0.57}$ | $1.21_{-0.41}^{+1.05}$ |
| H I+H$_2$ | $1.26_{-0.27}^{+0.88}$ | $1.09_{-0.29}^{+0.49}$ |
| H$_2$ (H I galaxies) | $1.31_{-0.35}^{+1.31}$ | $1.01_{-0.24}^{+0.36}$ |
| H$_2$ high resol. (H I galaxies) | $2.43_{-1.08}^{+3.24}$ | $1.17_{-0.55}^{+1.05}$ |
| $\Sigma_\mathrm{mol}$/$\Sigma_\mathrm{atom}$ | $1.13_{-0.27}^{+0.55}$ | — |
|  |  |  |

: Effect of including atomic gas on arm/interarm contrasts.

Table notes: Gas and SFE contrasts (median and 16$^{\rm th}$–84$^{\rm th}$ percentile range, measured on galactocentric rings of 500 pc width). Limited to 15 spiral galaxies where H I observations achieve a spatial resolution better than 2.5 kpc.

So far, we have considered the contrasts based on molecular gas, without accounting for atomic gas. This seems like a reasonable choice, since molecular gas often dominates the inner parts of galaxies, and is more closely related to star formation (cite: 2008AJ....136.2846B; 2013AJ....146...19L). Another reason to focus on the molecular phase is the higher resolution of our CO observations compared to H I. Yet, the arm/interarm contrast in atomic gas is interesting, and it can tell us not only about the accumulation of gas, but also the transformation of atomic to molecular gas driven by spiral compression.

In this Section, we consider the impact of including atomic gas in arm/interarm contrasts, which we can unfortunately only examine at lower resolution (a few tens of arcsec for H I, i.e. $\sim$kpc scales, instead of ${\sim} 100$ pc scales for CO). We limit our analysis to the cases where H I achieves a physical resolution of 2.5 kpc or better (15 galaxies, keeping in each case the original H I resolution, matching CO to this resolution), restricted to the extent of the PHANGS–ALMA field of view. Table [1](#table:includingHI) lists the distribution of arm/interarm contrasts for this subsample of H I galaxies. The H$_2$ contrast drops very significantly from high to low resolution (matched to H I), and the SFE contrast also drops slightly. We examine the effect of resolution more closely in Sect. [3.8](#Sec:effect_res). Even at matched resolution, the H I contrast is typically ${\sim}10$% lower than the H$_2$ contrast (while H I+H$_2$ shows intermediate contrasts). This is also confirmed if we explicitly look at the molecular-to-atomic ratio ($\Sigma_\mathrm{mol}$/$\Sigma_\mathrm{atom}$), which shows a $13$% higher median in spiral arms.

Figure [7](#fig:effect_HI) compares point-by-point the contrast of total gas (H I+H$_2$) as a function of molecular contrast (H$_2$) matched to the resolution of H I. The correlation is very strong (Spearman $\rho=0.90$). Most datapoints cluster around relatively low contrast values (mostly ${\lesssim} 0.5$ in log scale), and in those cases the agreement between H I+H$_2$ and H$_2$ contrast is good (following the 1:1 line). Overall, the drop in the contrasts when including H I is small (median 6% lower for the average over segments, only 3% lower for all radial bins). For exceptionally high contrasts, however, the H$_2$ contrast exceeds the one for total gas by $\sim$0.1-0.2 dex ($30{-}60$%). The relation between H I+H$_2$ and H$_2$ contrast can be fitted by a power-law with slope $0.67$ (but we note that the fit tends to overestimate the difference with respect to the 1:1 line for the largest contrasts).

The boost in molecular-to-atomic ratio ($\Sigma_\mathrm{mol}$/$\Sigma_\mathrm{atom}$) in spirals points to some conversion of atomic to molecular gas due to the compression associated with spiral arms. At the same time, photodissociation of H$_2$ downstream of the arm could play a role (cite: 2013ApJ...779...42S). In any case, we find a higher H$_2$ than H I contrast, which suggests that spiral arms might trigger the formation of molecules and do not simply gather preexisting molecular gas; in addition, spiral arms might enhance the density enough to form CO (and not only H$_2$), transforming some CO-dark molecular gas to molecular gas that efficiently emits in the CO line (cite: 2007MNRAS.376.1747D; 2014MNRAS.441.1628S). We caution that the limited resolution of the H I observations might wash out some of these effects. Observations of H I at higher physical resolution would be highly desirable to deepen our understanding of such phase transitions associated with spiral arms.

Including atomic gas also affects the SFE. Table [1](#table:includingHI) shows that the median SFE contrast increases by $8$% when considering the total gas (H$_2$+H I) instead of only H$_2$. As expected, the change is even more extreme if we consider H I only, which results in an SFE contrast typically ${\sim}20$% higher than when considering only H$_2$. The difference is particularly strong for the largest molecular contrasts, where considering the SFE of the total gas (H I$+$H$_2$) results in contrasts nearly a factor of ${\sim}2$ higher than focusing exclusively on the molecular phase. To make further progress, it becomes essential to obtain observations of atomic gas at higher physical resolution. We discuss this further in Sect. [4.3](#Sec:discussSFE).

## Radial trends in arm/interarm contrast

![](Rnorm.png)

Here we examine whether the arm/interarm contrast shows significant fluctuations with galactocentric radius. Figure [8](#fig:Rnorm) shows our measurements of the arm/interarm contrast in elliptical annuli (radial bins of 500 pc) as a function of the galactocentric radius of each bin normalised by $R_{25}$. There is a very significant scatter in the contrasts at fixed $R/R_{25}$, but the running medians also show that there are some (mild) trends with radius. The enhancement of the stellar contrast above unity becomes on average a factor of ${\sim}8$ larger from the innermost to the outer radii that we sample; the median contrast in stellar mass surface density monotonically rises from just 5% in the innermost bin, up to 38% at $0.5\,R_{25}$, and then plateaus around this value. The trend is confirmed if we use the MUSE-based stellar mass maps instead (Appendix [8](#Sec:stellarcon)). Thus, spiral arm stellar contrasts are damped in inner galaxies relative to middle radii; stellar surface densities become much larger as we approach galaxy centres, while the interarm values become comparatively higher with respect to the spiral density enhancement.

The molecular gas contrast shows a more stable behaviour with radius, with running medians fluctuating around a factor $2$-$2.5$. Compared to the molecular contrast, the SFR contrast shows a strong decline towards the innermost normalised radial bins. A visual inspection of the maps suggests that this is mostly due to efficient star formation in inner rings or around bar ends, beyond the actual log-spiral mask. In other words, precisely around the point where log-spiral arms end in galactic centres or connect to a bar, there is plenty of scattered star formation, which falls inside the interarm footprint. As a consequence, the SFE contrast also shows its lowest value for the innermost bin (factor of ${\sim}0.7$), largely associated with the surroundings of bar ends and star-forming rings beyond spirals, while over most radii the running medians remain around unity or slightly above.

## Symmetry of contrasts in two-armed spirals

The large majority of the spiral galaxies in our sample are dominated by two spiral arms (22 out of 28, or 79%). Here, for two-armed spirals, we examine whether the radial variations in contrasts that we observe are symmetric or largely uncorrelated for opposite spiral arms.

If the contrasts were exactly symmetric, we would expect a perfect correlation between opposite spiral arms (rank coefficient approaching unity), with scatter only due to measurement uncertainties. On the other hand, if the radial fluctuations along a given arm were totally independent from the other arm, we would expect a lack of correlation ($\rho$ close to zero). If we calculate the Spearman rank correlation coefficient for contrasts in opposite arms, we find a relatively strong correlation for the stellar component ($\rho = 0.61$), a weaker correlation for the molecular and SFR contrast ($\rho =0.36$ and $0.43$, respectively), and an even smaller correlation for the SFE contrast ($\rho =0.21$). Therefore, there seems to be some degree of connection between both arms (the arms somehow ‘know about each other’), but the large scatter implies that fluctuations along one arm are not always perfectly mirrored by changes in the contrast of the other spiral arm. In Sect. [4.2](#Sec:symmetry) we discuss the stronger arm-to-arm correlation in NIR than in CO or SFR.

## Effect of resolution

![](Resol.png)

The main difference between the arm/interarm contrasts presented in this paper and those from (cite: 2021A&A...656A.133Q) and other previous works is the resolution of the data. Here we consider contrasts measured from data at ${\sim}$100 pc resolution as opposed to previous studies working on kpc-resolutions. In this Section, we directly assess the effect of resolution on the contrasts by comparing our ${\sim}$100 pc resolution results with the results if we convolve the maps to 1.5 kpc resolution. This is the physical resolution used in the contrasts presented in (cite: 2021A&A...656A.133Q), as it is the best common resolution possible across all PHANGS galaxies limited by the SFR tracer (WISE 22 $\mu$m). In order to convolve the maps to 1.5 kpc resolution, we employ the kernels from (cite: 2011PASP..123.1218A).

Figure [9](#fig:resol) shows that there is a reasonably good correlation between the contrast measured at 1.5 kpc and at 100 pc resolution (ranks $\rho \sim 0.8{-}0.9$ for $\Sigma_\mathrm{\star}$, $\Sigma_\mathrm{mol}$, and $\Sigma_\mathrm{SFR}$, $\rho=0.67$ for SFE). In any case, there is some scatter, especially for SFE, which is a more indirect quantity. More importantly, there is a systematic offset towards higher contrasts, especially for $\Sigma_\mathrm{mol}$ and $\Sigma_\mathrm{SFR}$, when we shift to high resolution. This is well expected because using data at 1.5 kpc will somewhat dilute the signal. The contrasts measured at 100 pc are typically 8%, 38% and 44% higher than at 1.5 kpc resolution for $\Sigma_\mathrm{\star}$, $\Sigma_\mathrm{mol}$, and $\Sigma_\mathrm{SFR}$, respectively (median difference). The lower change for $\Sigma_\mathrm{\star}$ is probably because the stellar mass distribution is intrinsically smoother than $\Sigma_\mathrm{mol}$ or $\Sigma_\mathrm{SFR}$. For SFE, if we focus on the contrasts above unity, the median increase is 9% (up to 23% if we focus on contrasts above 1.3). Indeed, at high contrast values, the amplification at high resolution is slightly larger for SFR than for CO (for contrasts above 2, the median increase for SFR is 80%, as opposed to 36% median amplification for CO); this is why the highest SFE contrasts also get slightly boosted at high resolution compared to low resolution.

# Discussion

We start by discussing the magnitude of our measured $\Sigma_\mathrm{\star}$, $\Sigma_\mathrm{mol}$, and $\Sigma_\mathrm{SFR}$ contrasts and their variation among and within galaxies in Sect. [4.1](#Sec:discusscontr). Then we discuss their radial variations and symmetry in Sect. [4.2](#Sec:symmetry). We address the question of whether spiral arms systematically boost SFE in Sect. [4.3](#Sec:discussSFE).

## Magnitude of $\Sigma_\mathrm{\star}$, $\Sigma_\mathrm{mol}$, $\Sigma_\mathrm{SFR}$ contrasts and variation with galaxy properties

Spiral arms are often regarded as locations where most gas and star formation accumulates in galaxies. Yet, as shown by (cite: 2021A&A...656A.133Q) for PHANGS, the overall contribution of arm and interarm to total molecular gas and SFR is fairly similar, while the interarm region spans a larger area (in agreement with findings from previous studies such as (cite: 2010ApJ...725..534F)). To examine this problem further, we have performed detailed measurements of the arm/interarm contrast of stellar mass, molecular gas, and star formation rate surface density, as well as the resulting efficiency, across PHANGS galaxies.

One of the main results of this paper is that the stellar surface density arm/interarm contrast is very small (about a few tens of percent), but, as it determines the gravitational potential, it is sufficient and critical to trigger a non-linear response in the gas which results in the accumulation of molecular gas and star formation in spiral arms (typical contrast of a factor ${\sim}2{-}3$). Using a morphology-independent approach to quantify gas and stellar density contrasts in these same galaxies, (cite: 2021ApJ...913..113M) found similar results. In this work, we have examined the robustness of this result against different methodological choices (e.g. spiral mask width, tracers, binning; see Appendix [11](#sec:sanity_checks)).

We found that $\Sigma_\mathrm{SFR}$ contrasts show a larger scatter than $\Sigma_\mathrm{mol}$ contrasts. This suggests that there are more fluctuations in the contrast of $\Sigma_\mathrm{SFR}$, which is probably a result of the intrinsic stochasticity of the star formation process, where a small fraction of the molecular gas is transformed into stars (cite: 2010ApJ...722.1699S; 2014MNRAS.439.3239K; 2018ApJ...861L..18U; 2019Natur.569..519K; 2020MNRAS.493.2872C). While spiral arms act directly on the gas, the effect on star formation is indirect, and modulated by changes in SFE (e.g. due to local conditions in the ISM such as pressure or magnetic fields; (cite: 2021ApJ...911..128K)). Our choice of 500 pc-wide radial bins somewhat mitigates stochastic sampling effects (which would be stronger in smaller apertures; the characteristic separation length between independent star-forming regions measured by (cite: 2022MNRAS.516.3006K) for PHANGS galaxies is ${\sim}200{-}400$ pc). However, local variations in SFE can still result in a wider distribution of SFR contrasts compared to CO contrasts. In the spiral galaxy M100, (cite: 2018ApJ...863...59E) found regularly spaced NIR clumps along filaments (with typical separations of ${\sim}400$ pc), which they interpret as the result of large-scale gravitational instabilities in shocked gas (cite: 2020NatAs...4.1064H). All these fluctuations can explain the occasional appearance of bins where the interarm surface density is slightly higher than in the arm, leading to negative contrasts in the logarithmic scale.

Our results point to a tight relationship between stellar mass, galaxy dynamics, morphology, and the reorganisation of the ISM in spiral galaxies. We found that grand-design spirals show higher stellar contrasts (up to three times higher median for an extended field of view), and molecular and SFR contrasts are also higher (${\sim}2$ higher median). This agrees with findings from (cite: 2021ApJ...913..113M) on larger CO contrasts in grand-design galaxies. Regarding the stellar contrast, (cite: 2017MNRAS.471.1070B) found significantly lower arm/interarm contrasts in flocculent galaxies, but similar ones in multi-armed and grand-design spirals. Only two galaxies in our sample are classified as flocculent (NGC 1385 and NGC 2283), as opposed to nine multi-armed and 17 grand-design. Therefore, the difference between grand-design and the rest in our case is mostly driven by multi-armed spirals (and not flocculent).

Since the most massive spirals in our sample tend to be grand-design, we also find higher contrasts for the galaxies with largest stellar mass. The increased grand-design contrasts could have a dynamical origin, as both internally and externally excited density waves (e.g. due to bars or interactions) can manifest themselves as grand-design spirals. In turn, this results in an accumulation of stellar mass in a symmetric, two-armed spiral pattern, which can drive shocks that accumulate gas and trigger star formation (following the picture from (cite: 1969ApJ...158..123R)).

Another strong piece of evidence supporting the link between dynamics and $\Sigma_\mathrm{mol}$ and $\Sigma_\mathrm{SFR}$ contrasts is the strong correlation between these quantities and $\Sigma_\mathrm{\star}$ contrasts. Specifically, we find superlinear relations (slope $m=1.8$ for $\Sigma_\mathrm{mol}$, $m=2.9$ for $\Sigma_\mathrm{SFR}$), which agrees with similar findings by (cite: 2021ApJ...913..113M), consistent with gas compressed as it flows supersonically as it enters spiral arms. Specifically, the slope of $m=2$ between gas and stellar contrast can be expected for hydrodynamic shocks with a Mach number that is set by the underlying stellar density contrast (cite: 2021ApJ...913..113M). Scatter is expected around this relation due to a number of additional effects, including gas self-gravity and magnetic fields.

## Radial variation and symmetry in arm/interarm contrasts

Our interpretation of the strong correlation between $\Sigma_\mathrm{mol}$ or $\Sigma_\mathrm{SFR}$ and $\Sigma_\mathrm{\star}$ contrasts, and the larger contrasts found in grand-design spirals, is that galaxy dynamics largely dictates, through perturbations in the gravitational potential, the accumulation of gas and, subsequently, star formation in spiral arms. Yet, this is a relation that operates ‘on average’, while the individual radial bins, and even mean values over entire spiral segments, show significant scatter around this relation. That means that on top of the stellar contrast there must be local effects at play, potentially also related to spiral arms (e.g. magnetic fields, local flows, local shear, gravitational instabilities leading to regularly spaced star-forming clumps), in addition to observational uncertainties. This is even more acute in SFR contrasts, as it is an indirect quantity which is also sensitive to many other factors (stability of molecular clouds, and specific snapshot in which we capture the star formation cycle).

We found a clear decrease in the stellar contrast as we approach galaxy centres. The median contrast in stellar mass drops from ${\sim}40$% at $0.5\,R_{25}$ to just 5% at $0.1\,R_{25}$. Overall, stellar surface densities quickly increase towards galaxy centres, which can even harbour bulges on top of a roughly exponential stellar disc. This means that the baseline interarm value is more elevated for the smallest radii, and a significant increase in spiral surface density can still appear as proportionally more limited due to this stellar bulge dilution. Furthermore, it becomes comparatively harder to excite spiral arms when stellar populations have a larger velocity dispersion (dynamically ‘hotter’, i.e. higher $\sigma_\star / v_{\rm rot}$), which is typically the case when we move towards the centres of galaxies.

We also found that $\Sigma_\mathrm{SFR}$ contrast drops by more than a factor of ten over the same radial range. As commented on in Sect. [3.6](#Sec:radial), this drop is associated with inner rings or the surroundings of bar ends, which are actively star-forming and fall within the interarm footprint. More generally, the contact points of spirals and bars, as well as galaxy centres, show complex effects where the dichotomy between spiral and interarm star formation becomes less clear. In addition to the spiral perturbation on the gaseous disc, those inner radial bins reflect other dynamical effects, such as rings connected to Lindblad resonances (cite: 1996FCPh...17...95B).

Two-fold rotational symmetry is expected in standard models of grand-design spiral structure, where an $m=2$ Fourier mode dominates. By focusing on the two-armed spirals in our sample, we found that there is a positive and significant degree of correlation between opposite spiral arms with $\rho \sim 0.6$ for the stellar component and $\rho \sim 0.4$ for the molecular and SFR component. This is consistent with an interpretation where dynamical processes drive a largely symmetric response in the stellar gravitational potential of the disc, and this leads to the accumulation of gas (and indirectly star formation), but on top of other mechanisms that ultimately set the details of the local gas response.

The effect of arm symmetry on SFE is more subtle. If radial fluctuations in SFE were driven by a (radial) dynamical process, we could expect a significant correlation among arms. Yet, if the fluctuations in SFE were driven by local processes and/or time evolution (stochasticity and sampling issues), we would expect the measurements in opposite arms to be mostly uncorrelated. Indeed, what we find is that the correlation of SFE in opposite arms is much weaker ($\rho \sim 0.2$) than the correlation of $\Sigma_\mathrm{mol}$ or $\Sigma_\mathrm{SFR}$ contrasts ($\rho \sim 0.4$), suggesting that, while axisymmetric dynamical processes could play some modulating role, local effects and stochasticity largely wash out any symmetric trends.

## Considering whether the SFE is enhanced in spiral arms

While it is clear that spiral arms accumulate gas and star formation, the question remains as to what extent the conversion of gas into stars proceeds more efficiently in spiral arms. For example, shocks or cloud-cloud collisions could trigger the collapse of molecular clouds and induce more efficient star formation.

Previous studies have addressed this long-standing problem using different tracers (e.g. gas including only H I, only H$_2$, or both) at different physical resolutions (typically ${\sim}1$ kpc), yielding contradictory results, with some papers claiming that spiral arms are sites of enhanced SFE (cite: 1990ApJ...356..135L; 1996A&A...308...27K), and others arguing that spirals pile up gas (and indirectly star formation) but do not boost the efficiency at which gas transforms into stars (cite: 2010ApJ...725..534F; 2016ApJ...827..103K). Galactic studies also point to little or no difference in the SFE between arm and interarm regions in the Milky Way (cite: 2012MNRAS.426..701M; 2015MNRAS.452..289E; 2018MNRAS.479.2361R; 2021MNRAS.500.3050U). To shed light on this problem, here we have considered the largest sample of spiral arm/interarm contrasts examined so far (28 nearby spirals) using homogeneous observations at $\sim$100 pc resolution.

Our observations do not support the simple, naive picture where spiral arms always increase the efficiency by which molecular gas forms stars. If we pick up a random location, in roughly 6 out of 10 cases we will find higher SFE in spiral arms, but in as many as 4 out of 10 cases, the opposite will hold: more efficient star formation in interarm regions (Fig. [4](#fig:violin_plot_GD-vs-rest), right panel). The median SFE enhancement across the whole sample is 16%, which, albeit statistically significant, is limited compared to the spiral increase in $\Sigma_\mathrm{mol}$ (median enhancement 120%) or $\Sigma_\mathrm{SFR}$ (160%). We note that systematic variations in the $\alpha_{\rm CO}$ conversion factor could result in an additional $10$% increase of SFE in arms compared to interarm regions (if the $\alpha_{\rm CO}$ prescription from (cite: 2024ApJ...961...42T) can be extrapolated to arm/interarm differences; see Sect. [2.2](#Sec:PHANGS--ALMA)).

While we found clearly enhanced stellar contrasts in grand-design spirals, we do not find a significant difference in the SFE contrast between grand-design spirals and the rest (Fig. [4](#fig:violin_plot_GD-vs-rest)). SFE and $\Sigma_\mathrm{\star}$ contrasts show a positive correlation, but fairly weak ($\rho = 0.34$), as opposed to the stronger correlation between $\Sigma_\mathrm{mol}$ or $\Sigma_\mathrm{SFR}$ and $\Sigma_\mathrm{\star}$ contrasts ($\rho = 0.73$ and $0.61$, respectively). Therefore, the impact of global dynamics and morphology on the regulation of SFE seems more subtle. Overall, local or stochastic effects seem to play a stronger role in setting the spiral SFE.

However, if we focus on the largest stellar contrasts, we do find a more acute boost in spiral SFE. For the top 10% of $\Sigma_\mathrm{\star}$ contrasts ($>1.97$) the median SFE contrast rises to as much as $2.34$. As we have seen, even a weak stellar spiral arm (contrast ${\sim}10{-}20$%) results in a significant, non-linear increase of molecular gas (and, indirectly, SFR) surface densities. Thus, to zeroth order, spiral arms simply pile up gas and star formation in a very efficient way. However, we need a very strong stellar contrast in the spiral (approaching a factor ${\sim}2$ or more) to produce a significant boost in the molecular SFE.

Our H I observations, albeit at lower resolution, confirm that the molecular-to-atomic ratio ($\Sigma_\mathrm{mol}$/$\Sigma_\mathrm{atom}$) increases in spiral arms. Thus, to some degree, spiral arms promote a phase transition from H I to H$_2$. As a consequence, the contrasts associated with the total gas are weaker than molecular contrasts. By promoting the formation of cold, potentially star-forming clouds, spiral arms make more gas susceptible to form stars, and could indirectly stimulate the formation of molecules. In that sense, they do result in enhanced star formation beyond just gathering gas, even if the molecular gas that is eventually available forms stars with a similar efficiency. As a corollary, the SFE contrast of the total gas (H I+H$_2$) is higher than referred exclusively to the molecular phase. To better understand the role of atomic gas in spiral arms, it is imperative to advance towards high-resolution H I mapping of spiral galaxies with matched molecular gas observations; this is already possible for very nearby spirals such as IC 342 (cite: 2023A&A...680A...4Q).

The inclusion of atomic gas can explain some of the discrepancies within the literature. For example, early studies such as (cite: 1987PhDT........11L), (cite: 1988Natur.334..402V) or (cite: 1990ApJ...349..497C) relied exclusively on H I to estimate gas and SFE contrasts. This results in a lower gas contrast and a boost of the SFE contrast (because part of the atomic gas transforms to molecular gas in spiral arms). Other studies referred to the SFE of the total (H I+H$_2$) gas, such as (cite: 1996A&A...308...27K), which can also lead to higher observed SFE, especially for the largest contrasts. On the other hand, studies limited to molecular gas typically found similar SFE values in spiral arms and interarm regions (cite: 2010ApJ...725..534F; 2016ApJ...827..103K; 2021A&A...650A.134P; 2021A&A...656A.133Q).

Regarding simulations, there is no clear support for a picture where star formation proceeds more efficiently in spiral arms. Hydrodynamical galaxy simulations indeed suggest that there is an accumulation of dense (molecular) gas in spiral arms, but the star formation rate per unit gas mass remains similar in arms and interarm (cite: 2006MNRAS.365...37B; 2009MNRAS.396.1579D; 2011MNRAS.417.1318D; 2020ApJ...898...35K; 2020MNRAS.492.2973T). According to these studies, spiral arms are sites where competing effects meet, on the one hand building up higher gas densities and larger molecular clouds, and on the other hand involving shear, flows, and elevated velocity dispersions that hinder collapse (cite: 2007MNRAS.374.1115D; 2013ApJ...779...45M; 2017ApJ...845..133S; 2018ApJ...854..100M).

Summing up, our results suggest that the impact of spiral arms on SFE is, to first order, a matter of definition. If we ask whether spiral arms simply ‘gather’ or also ‘trigger’ star formation, the answer is that they certainly passively gather, but to some extent also actively enhance star formation, because some H I transforms to H$_2$ and, thus, more gas is susceptible to form stars. On the other hand, if the question is whether the available molecular gas forms stars more efficiently in spiral arms, the answer would be on average negative; the triggering effect is at least very limited, except in the cases where the stellar contrast is very large. Here we have not examined effects such as detailed gas flows, shear patterns, or magnetic fields within spirals, but some of these effects might be able to explain why we find more or less efficient conversion of molecular gas into stars in different locations along spirals.

## Methodology and measurement caveats

Table [\[table:stats\]](#table:stats) summarises the distribution of contrasts for different methodological choices. This includes using lower resolution maps (Sect. [3.8](#Sec:effect_res)), a narrow version of the spiral masks (Appendix  [10](#Sec:narrow)), radial bins of different width, and two alternative sampling approaches (Appendix [11](#sec:sanity_checks)).

The most relevant effect is resolution. Indeed, contrasts get strongly diluted when shifting from ${\sim} 100$ pc to 1.5 kpc resolution (Fig. [9](#fig:resol)). The median stellar contrast drops from $1.28$ to $1.15$, while the median molecular and SFR contrasts drop from $2.22$ to $1.49$ and from $2.56$ to $1.50$, respectively. Importantly, the dilution effect is not totally symmetric for molecular gas and star formation, such that the SFE is also affected when degrading resolution (its median contrast drops from $1.16$ to $1.04$; even more if we degrade the resolution further to match H I, see Table [1](#table:includingHI)).

We also test how results are affected by the precise definition of the spiral mask. Using the narrower spiral masks introduced in Sect. [2.6.2](#Sec:thinnersp), Fig. [15](#fig:orig_vs_narrow) in Appendix [10](#Sec:narrow) shows that, despite covering a significantly smaller area (${\sim} 1/2$), the contrasts for the narrower masks are very similar to the nominal ones or just slightly higher. The stellar contrast remains virtually unchanged, while the median molecular and SFR contrasts are just ${\sim}10{-}20$% higher for the narrow masks. The resulting SFE is just $4$% higher for the narrow masks, so the difference is fairly limited, and much smaller than implied by the change of resolution.

A quick visual inspection of CO or SFR maps could suggest that the narrow masks better capture the enhanced densities in spirals. Yet, the relatively limited change in contrasts when using the narrow masks demonstrates that spirals are not as concentrated as one could perhaps expect. Indeed, the immediate outskirts of the spiral ridge must also have elevated surface densities compared to interarm regions, as otherwise we would expect a more acute dilution of the contrast associated with the broader masks (which typically span a twice larger area). In other words, the narrow masks better capture the ridge of molecular emission and star formation (useful for some applications), but the effect of the spiral perturbation seems to extend further out, which justifies the use of the more regular and broader nominal masks across this paper.

As shown in Table [\[table:stats\]](#table:stats), the distributions of contrasts for $\Sigma_\mathrm{\star}$, $\Sigma_\mathrm{mol}$, $\Sigma_\mathrm{SFR}$, and SFE are very similar if we choose either narrower radial bins (250 pc) or wider bins (1000 pc), instead of the nominal 500 pc-wide bins. In Appendix [11](#sec:sanity_checks), instead of elliptical annuli of a fixed width we also consider a different binning strategy, splitting the spiral masks into ‘boxes’ which follow each arm, with perpendicular cuts at regular lengths along the arm, and two alternative definitions of interarm. The impact of these alternative binning approaches on the contrasts is slightly larger that just changing the width of the radial bins, but does not lead to very strong systematic differences, as shown in Table [\[table:stats\]](#table:stats) and Appendix [11](#sec:sanity_checks).

As already discussed in Sect. [3.5](#Sec:effect_HI) and Sect. [4.3](#Sec:discussSFE), including atomic gas does have a very significant impact on the gas and SFE contrasts. Table [1](#table:includingHI) quantifies these differences.

In the Appendix, we also consider some caveats associated with our measurements. In Appendix [8](#Sec:stellarcon) we confirm that our nominal stellar mass tracer (*Spitzer* $3.6$ $\mu$m corrected for dust emission with ICA) is robust when compared to MUSE-based $\Sigma_\mathrm{\star}$ maps (from stellar population fitting). Appendix [7](#sec:AppendixMUSE) considers the correction to narrow-band H$\alpha$ to account for extinction; for the same subset of galaxies and field of view, the contrasts derived this way agree with MUSE SFRs (extiction-corrected H$\alpha$ using the Balmer decrement). In Appendix [9](#Sec:DIG) we argue that diffuse ionised gas (DIG) is unlikely to have a major impact on SFR contrasts following our observational approach. Based on geometrical arguments, we expect our broad spiral masks to capture most leaked ionising photons associated with spiral arms. Furthermore, our tests using H II region masks suggest that most DIG in the interarm regions is associated with local H II regions, and is not due to leaked photons from the spiral arms.

In addition to the distributions of contrasts presented in Table [\[table:stats\]](#table:stats) for different alternatives, in Appendix [11](#sec:sanity_checks), and specifically in Table [\[table:stats_appendix\]](#table:stats_appendix), we examine how the main correlations among contrasts are affected by these methodological choices. Based on this analysis, our main conclusions seem qualitatively robust against these details.

# Summary and conclusions

Disc galaxies in the local universe tend to develop different kinds of spiral structures, where approximately logarithmic spiral segments appear punctuated by luminous regions associated with young stars. In this paper, we have examined the increase of surface densities present in spiral arms compared to the remaining disc positions at matched galactocentric radii. We have measured these arm/interarm contrasts in the 28 nearby galaxies from PHANGS that show a clear spiral structure (according to the environmental masks from (cite: 2021A&A...656A.133Q)), split into radial bins of 500 pc width.

The main novelty here with respect to (cite: 2021A&A...656A.133Q) is that these measurements were performed at $\sim$100 pc resolution instead of $\sim$kpc resolution, and that we considered radial bins and not only averages over full spiral segments. The limiting factor in (cite: 2021A&A...656A.133Q) was the requirement to convolve the data to the resolution of the MIR map that was used in the hybridisation process to account for obscured star formation (WISE 22 $\mu$m at $15''$ resolution). In this paper, we have circumvented this limitation by employing PHANGS–MUSE observations to empirically calibrate the effect of extinction on SFR contrasts, starting directly from the H$\alpha$ contrast (see Appendix [7](#sec:AppendixMUSE) for details). This allowed us to robustly measure the SFR contrast at $\sim$100 pc resolution and therefore (indirectly) the SFE contrasts, within some moderate error bars. Compared to (cite: 2021A&A...656A.133Q), in this paper we also considered the stellar contrast and correlations among contrasts, as well as radial trends and symmetry among spiral arms in a given galaxy. Finally, we also examined a number of additional effects, including the width of the spiral masks, resolution, binning, and the inclusion of atomic gas.

Our main findings are:

1.  The arm/interarm enhancement in stellar mass surface density ($\Sigma_\star$) is very modest, typically a few $\sim$10% (median 28%). On the other hand, the molecular gas ($\Sigma_\mathrm{mol}$) and star formation rate ($\Sigma_\mathrm{SFR}$) enhancements are much higher, spanning from a few tens of percent up to a factor of a few (median contrast 2.2 and 2.6, respectively; Fig. [4](#fig:violin_plot_GD-vs-rest) and Table [\[table:stats\]](#table:stats)).

2.  The spiral enhancement is larger in grand-design spirals compared to the rest (median 50% higher for stellar mass, factor of ${\sim}2$ higher for molecular gas and star formation surface density; Fig. [4](#fig:violin_plot_GD-vs-rest)). This suggests that grand-design galaxies are particularly efficient in reorganising stellar mass, gas, and star formation into spiral structures.

3.  The contrast in $\Sigma_\mathrm{mol}$ and $\Sigma_\mathrm{SFR}$ show a significant correlation with the $\Sigma_\star$ contrast, implying that a modest contrast in stellar mass surface density largely controls the accumulation of gas and star formation, which gets amplified compared to the perturbation in the gravitational potential (see Fig. [5](#fig:CO_SFR_SFE_vs_NIR)).

4.  The contrasts show large fluctuations with galactocentric radius, with a larger scatter in $\Sigma_\mathrm{SFR}$ than in $\Sigma_\mathrm{mol}$. There is a pronounced drop in $\Sigma_\mathrm{\star}$ contrast towards galaxy centres. The $\Sigma_\mathrm{SFR}$ contrasts also show a drop towards the innermost spiral bins (Fig. [8](#fig:Rnorm)). This appears to be associated with extended star formation outside spiral arms around bar ends and galaxy centres.

5.  The star formation efficiency (SFE) of molecular gas is higher in spiral arms only in 60% of the radial bins, with a median enhancement of 16%. However, when focusing on the largest stellar contrasts ($\gtrsim 2$, top 10%), the median SFE contrast of molecular gas increases to as much as $2.34$.

6.  The molecular-to-atomic gas ratio ($\Sigma_\mathrm{mol}$/$\Sigma_\mathrm{atom}$) is higher in spiral arms, with lower atomic than molecular contrasts. When referred to the total gas (H I+H$_2$) instead of molecular gas (H$_2$) the median SFE increases by $8$% (at ${\sim}$kpc resolution available for H I). In that sense, spiral arms induce a phase transition from atomic to molecular gas, making more gas available to form stars. Thus, to some degree, spiral arms do trigger star formation, in addition to their role in gathering molecular gas.

7.  We have considered a number of technical details, including the spiral mask width, tracers, resolution, and binning. There is a significant dilution of contrasts when we shift to lower resolution (from $\sim$100 pc to 1.5 kpc), and the details of binning, specific tracers used and conversion factors do have an impact on the precise numbers in each case. In any case, these choices do not change our conclusions qualitatively.

In summary, the modest stellar contrasts largely dictate the accumulation of molecular gas and star formation in spiral arms. However, only the largest stellar contrasts result in a substantial boost in how efficiently molecular gas transforms into stars. The efficiency associated with the total gas (including the atomic phase) is slightly higher, as spirals do end up triggering some transformation of atomic to molecular gas, making a larger fraction of the gas available for star formation. In any case, the organisation of the ISM by spiral arms and the modulation of the SFE is a complex phenomenon that shows significant local fluctuations and is not fully mirrored by opposite arms even in grand-design spirals.

# Acknowledgements

This work was carried out as part of the PHANGS collaboration. We would like to thank the anonymous referee for comments that helped us improve the manuscript.

This work is based on observations and archival data obtained with the *Spitzer* Space Telescope, which is operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with NASA. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00650.S, ADS/JAO.ALMA#2013.1.00803.S, ADS/JAO.ALMA#2013.1.01161.S, ADS/JAO.ALMA#2015.1.00121.S, ADS/JAO.ALMA#2015.1.00782.S, ADS/JAO.ALMA#2015.1.00925.S, ADS/JAO.ALMA#2015.1.00956.S, ADS/JAO.ALMA#2016.1.00386.S, ADS/JAO.ALMA#2017.1.00886.L, ADS/JAO.ALMA#2018.1.01651.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

MQ, SGB, MRG, and AU acknowledge support from the Spanish grant PID2022-138560NB-I00, funded by MCIN/AEI/10.13039/501100011033/FEDER, EU. JS acknowledges support by the National Aeronautics and Space Administration (NASA) through the NASA Hubble Fellowship grant HST-HF2-51544 awarded by the Space Telescope Science Institute (STScI), which is operated by the Association of Universities for Research in Astronomy, Inc., under contract NAS 5-26555. MCS acknowledges financial support from the European Research Council under the ERC Starting Grant ‘GalFlow’ (grant 101116226) and from the Royal Society (URF\R1\221118). MC gratefully acknowledges funding from the DFG through an Emmy Noether Research Group (grant number CH2137/1-1). COOL Research DAO is a Decentralized Autonomous Organization supporting research in astrophysics aimed at uncovering our cosmic origins. LN acknowledges funding from the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) - 516405419. I.P. acknowledges funding by the European Research Council through ERC-AdG SPECMAP-CGM, GA 101020943.

108 natexlab

(ref: 2017MNRAS.470.4750A) Accurso, G., Saintonge, A., Catinella, B., et al. 2017, MNRAS, 470, 4750

(ref: 2011PASP..123.1218A) Aniano, G., Draine, B. T., Gordon, K. D., & Sandstrom, K. 2011, PASP, 123, 1218

(ref: 2023A&A...670A..67B) Belfiore, F., Leroy, A. K., Sun, J., et al. 2023, A&A, 670, A67

(ref: 2022A&A...659A..26B) Belfiore, F., Santoro, F., Groves, B., et al. 2022, A&A, 659, A26

(ref: 2008AJ....136.2846B) Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846

(ref: 2017MNRAS.471.1070B) Bittner, A., Gadotti, D. A., Elmegreen, B. G., et al. 2017, MNRAS, 471, 1070

(ref: 2006MNRAS.365...37B) Bonnell, I. A., Dobbs, C. L., Robitaille, T. P., & Pringle, J. E. 2006, MNRAS, 365, 37

(ref: 1996FCPh...17...95B) Buta, R. & Combes, F. 1996, , 17, 95

(ref: 2015ApJS..217...32B) Buta, R. J., Sheth, K., Athanassoula, E., et al. 2015, ApJS, 217, 32

(ref: 1990ApJ...349..497C) Cepa, J. & Beckman, J. E. 1990, ApJ, 349, 497

(ref: 2020MNRAS.493.2872C) Chevance, M., Kruijssen, J. M. D., Hygate, A. P. S., et al. 2020, MNRAS, 493, 2872

(ref: 2023arXiv231100407C) Chiang, I.-D., Sandstrom, K. M., Chastenet, J., et al. 2023, arXiv e-prints, arXiv:2311.00407

(ref: 2009AJ....138.1741C) Chung, A., van Gorkom, J. H., Kenney, J. D. P., Crowl, H., & Vollmer, B. 2009, AJ, 138, 1741

(ref: 2022A&A...662A..89D) den Brok, J. S., Bigiel, F., Sliwa, K., et al. 2022, A&A, 662, A89

(ref: denBrok21) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS submitted

(ref: 2014PASA...31...35D) Dobbs, C. & Baba, J. 2014, PASA, 31, e035

(ref: 2007MNRAS.374.1115D) Dobbs, C. L. & Bonnell, I. A. 2007a, MNRAS, 374, 1115

(ref: 2007MNRAS.376.1747D) Dobbs, C. L. & Bonnell, I. A. 2007b, MNRAS, 376, 1747

(ref: 2011MNRAS.417.1318D) Dobbs, C. L., Burkert, A., & Pringle, J. E. 2011, MNRAS, 417, 1318

(ref: 2009MNRAS.396.1579D) Dobbs, C. L. & Pringle, J. E. 2009, MNRAS, 396, 1579

(ref: 2017MNRAS.470.4261D) Duarte-Cabral, A. & Dobbs, C. L. 2017, MNRAS, 470, 4261

(ref: 2015MNRAS.452..289E) Eden, D. J., Moore, T. J. T., Urquhart, J. S., et al. 2015, MNRAS, 452, 289

(ref: 1987ApJ...312..626E) Elmegreen, B. G. 1987, ApJ, 312, 626

(ref: 1993prpl.conf...97E) Elmegreen, B. G. 1993, in Protostars and Planets III, ed. E. H. Levy & J. I. Lunine, 97

(ref: 2018ApJ...863...59E) Elmegreen, B. G., Elmegreen, D. M., & Efremov, Y. N. 2018, ApJ, 863, 59

(ref: emsellem21) Emsellem, E., Schinnerer, E., Santoro, F., et al. 2021, A&A submitted

(ref: 2022A&A...659A.191E) Emsellem, E., Schinnerer, E., Santoro, F., et al. 2022, A&A, 659, A191

(ref: 2010ApJ...725..534F) Foyle, K., Rix, H. W., Walter, F., & Leroy, A. K. 2010, ApJ, 725, 534

(ref: 1993A&A...274..123G) Garcia-Burillo, S., Guelin, M., & Cernicharo, J. 1993, A&A, 274, 123

(ref: 2004MNRAS.349..909G) Gittins, D. M. & Clarke, C. J. 2004, MNRAS, 349, 909

(ref: 2012MNRAS.419.1402G) Groves, B., Brinchmann, J., & Walcher, C. J. 2012, MNRAS, 419, 1402

(ref: 2023MNRAS.520.4902G) Groves, B., Kreckel, K., Santoro, F., et al. 2023, MNRAS, 520, 4902

(ref: 2009RvMP...81..969H) Haffner, L. M., Dettmar, R. J., Beckman, J. E., et al. 2009, Reviews of Modern Physics, 81, 969

(ref: 2003AJ....126.2831H) Henry, A. L., Quillen, A. C., & Gutermuth, R. 2003, AJ, 126, 2831

(ref: 2020NatAs...4.1064H) Henshaw, J. D., Kruijssen, J. M. D., Longmore, S. N., et al. 2020, Nature Astronomy, 4, 1064

(ref: 2015A&A...582A..86H) Herrera-Endoqui, M., Dı́az-Garcı́a, S., Laurikainen, E., & Salo, H. 2015, A&A, 582, A86

(ref: 2009A&A...495..795H) Hitschfeld, M., Kramer, C., Schuster, K. F., Garcia-Burillo, S., & Stutzki, J. 2009, A&A, 495, 795

(ref: 2018A&A...618A..64H) Ho, I. T., Meidt, S. E., Kudritzki, R.-P., et al. 2018, A&A, 618, A64

(ref: 2017ApJ...846...39H) Ho, I. T., Seibert, M., Meidt, S. E., et al. 2017, ApJ, 846, 39

(ref: 1998ApJ...498..541K) Kennicutt, Jr., R. C. 1998, ApJ, 498, 541

(ref: 2022MNRAS.516.3006K) Kim, J., Chevance, M., Kruijssen, J. M. D., et al. 2022, MNRAS, 516, 3006

(ref: 2021ApJ...911..128K) Kim, J.-G., Ostriker, E. C., & Filippova, N. 2021, ApJ, 911, 128

(ref: 2020ApJ...898...35K) Kim, W.-T., Kim, C.-G., & Ostriker, E. C. 2020, ApJ, 898, 35

(ref: 2002ApJ...570..132K) Kim, W.-T. & Ostriker, E. C. 2002, ApJ, 570, 132

(ref: 1996MNRAS.283..251K) Knapen, J. H. & Beckman, J. E. 1996, MNRAS, 283, 251

(ref: 1996A&A...308...27K) Knapen, J. H., Beckman, J. E., Cepa, J., & Nakai, N. 1996, A&A, 308, 27

(ref: 2016ApJ...827..103K) Kreckel, K., Blanc, G. A., Schinnerer, E., et al. 2016, ApJ, 827, 103

(ref: 2019ApJ...887...80K) Kreckel, K., Ho, I. T., Blanc, G. A., et al. 2019, ApJ, 887, 80

(ref: 2014MNRAS.439.3239K) Kruijssen, J. M. D. & Longmore, S. N. 2014, MNRAS, 439, 3239

(ref: 2019Natur.569..519K) Kruijssen, J. M. D., Schruba, A., Chevance, M., et al. 2019, Nature, 569, 519

(ref: 2020ApJ...897..122L) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122

(ref: 2023ApJ...944L..17L) Lee, J. C., Sandstrom, K. M., Leroy, A. K., et al. 2023, ApJL, 944, L17

(ref: 2022ApJS..258...10L) Lee, J. C., Whitmore, B. C., Thilker, D. A., et al. 2022, ApJS, 258, 10

(ref: 2021ApJS..255...19L) Leroy, A. K., Hughes, A., Liu, D., et al. 2021a, ApJS, 255, 19

(ref: 2022ApJ...927..149L) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2022, ApJ, 927, 149

(ref: 2019ApJS..244...24L) Leroy, A. K., Sandstrom, K. M., Lang, D., et al. 2019, ApJS, 244, 24

(ref: 2021ApJS..257...43L) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021b, ApJS, 257, 43

(ref: 2009AJ....137.4670L) Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137, 4670

(ref: 2008AJ....136.2782L) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782

(ref: 2013AJ....146...19L) Leroy, A. K., Walter, F., Sandstrom, K., et al. 2013, AJ, 146, 19

(ref: 1987PhDT........11L) Lord, S. D. 1987, PhD thesis, Massachusetts Univ., Amherst.

(ref: 1990ApJ...356..135L) Lord, S. D. & Young, J. S. 1990, ApJ, 356, 135

(ref: 2017ApJ...835...93M) Martı́nez-Garcı́a, E. E., González-Lópezlira, R. A., Magris C., G., & Bruzual A., G. 2017, ApJ, 835, 93

(ref: 2021ApJ...913..113M) Meidt, S. E., Leroy, A. K., Querejeta, M., et al. 2021, ApJ, 913, 113

(ref: 2018ApJ...854..100M) Meidt, S. E., Leroy, A. K., Rosolowsky, E., et al. 2018, ApJ, 854, 100

(ref: 2013ApJ...779...45M) Meidt, S. E., Schinnerer, E., Garcı́a-Burillo, S., et al. 2013, ApJ, 779, 45

(ref: 2012ApJ...744...17M) Meidt, S. E., Schinnerer, E., Knapen, J. H., et al. 2012, ApJ, 744, 17

(ref: 2014ApJ...788..144M) Meidt, S. E., Schinnerer, E., van de Ven, G., et al. 2014, ApJ, 788, 144

(ref: 2012MNRAS.426..701M) Moore, T. J. T., Urquhart, J. S., Morgan, L. K., & Thompson, M. A. 2012, MNRAS, 426, 701

(ref: 2010ApJS..186..427N) Nair, P. B. & Abraham, R. G. 2010, ApJS, 186, 427

(ref: 2003PASJ...55..191N) Nakanishi, H. & Sofue, Y. 2003, PASJ, 55, 191

(ref: 2007ApJ...660L..43N) Noeske, K. G., Weiner, B. J., Faber, S. M., et al. 2007, ApJL, 660, L43

(ref: 2007ApJ...661..801O) Oey, M. S., Meurer, G. R., Yelda, S., et al. 2007, ApJ, 661, 801

(ref: 2022ApJ...927....9P) Pan, H.-A., Schinnerer, E., Hughes, A., et al. 2022, ApJ, 927, 9

(ref: 2021A&A...650A.134P) Pessa, I., Schinnerer, E., Belfiore, F., et al. 2021, A&A, 650, A134

(ref: 2022A&A...663A..61P) Pessa, I., Schinnerer, E., Leroy, A. K., et al. 2022, A&A, 663, A61

(ref: 2023A&A...673A.147P) Pessa, I., Schinnerer, E., Sanchez-Blazquez, P., et al. 2023, A&A, 673, A147

(ref: 2015ApJS..219....5Q) Querejeta, M., Meidt, S. E., Schinnerer, E., et al. 2015, ApJS, 219, 5

(ref: 2023A&A...680A...4Q) Querejeta, M., Pety, J., Schruba, A., et al. 2023, A&A, 680, A4

(ref: 2021A&A...656A.133Q) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, A&A, 656, A133

(ref: 2019A&A...625A..19Q) Querejeta, M., Schinnerer, E., Schruba, A., et al. 2019, A&A, 625, A19

(ref: 2018MNRAS.479.2361R) Ragan, S. E., Moore, T. J. T., Eden, D. J., et al. 2018, MNRAS, 479, 2361

(ref: 2012ApJ...757..155R) Rebolledo, D., Wong, T., Leroy, A., Koda, J., & Donovan Meyer, J. 2012, ApJ, 757, 155

(ref: 1975ApJ...196..381R) Roberts, W. W., J., Roberts, M. S., & Shu, F. H. 1975, ApJ, 196, 381

(ref: 1969ApJ...158..123R) Roberts, W. W. 1969, ApJ, 158, 123

(ref: 2020MNRAS.492.4149S) Sánchez-Menguiano, L., Sánchez, S. F., Pérez, I., et al. 2020, MNRAS, 492, 4149

(ref: 2022A&A...658A.188S) Santoro, F., Kreckel, K., Belfiore, F., et al. 2022, A&A, 658, A188

(ref: 2023MNRAS.518.1022S) Sarkar, S., Narayanan, G., Banerjee, A., & Prakash, P. 2023, MNRAS, 518, 1022

(ref: 2019ApJ...887...49S) Schinnerer, E., Hughes, A., Leroy, A., et al. 2019, ApJ, 887, 49

(ref: 2013ApJ...779...42S) Schinnerer, E., Meidt, S. E., Pety, J., et al. 2013, ApJ, 779, 42

(ref: 1959ApJ...129..243S) Schmidt, M. 1959, ApJ, 129, 243

(ref: 2010ApJ...722.1699S) Schruba, A., Leroy, A. K., Walter, F., Sandstrom, K., & Rosolowsky, E. 2010, ApJ, 722, 1699

(ref: 2017ApJ...845..133S) Semenov, V. A., Kravtsov, A. V., & Gnedin, N. Y. 2017, ApJ, 845, 133

(ref: 2010PASP..122.1397S) Sheth, K., Regan, M., Hinz, J. L., et al. 2010, PASP, 122, 1397

(ref: 2014MNRAS.441.1628S) Smith, R. J., Glover, S. C. O., Clark, P. C., Klessen, R. S., & Springel, V. 2014, MNRAS, 441, 1628

(ref: 2023A&A...676A.113S) Stuber, S. K., Schinnerer, E., Williams, T. G., et al. 2023, A&A, 676, A113

(ref: 2022AJ....164...43S) Sun, J., Leroy, A. K., Rosolowsky, E., et al. 2022, AJ, 164, 43

(ref: 2020ApJ...901L...8S) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020, ApJL, 901, L8

(ref: 2024ApJ...961...42T) Teng, Y.-H., Chiang, I. D., Sandstrom, K. M., et al. 2024, ApJ, 961, 42

(ref: 2020MNRAS.492.2973T) Tress, R. G., Smith, R. J., Sormani, M. C., et al. 2020, MNRAS, 492, 2973

(ref: 2021MNRAS.500.3050U) Urquhart, J. S., Figura, C., Cross, J. R., et al. 2021, MNRAS, 500, 3050

(ref: 2018ApJ...861L..18U) Utomo, D., Sun, J., Leroy, A. K., et al. 2018, ApJL, 861, L18

(ref: 1988Natur.334..402V) Vogel, S. N., Kulkarni, S. R., & Scoville, N. Z. 1988, Nature, 334, 402

(ref: 2008AJ....136.2563W) Walter, F., Brinks, E., de Blok, W. J. G., et al. 2008, AJ, 136, 2563

(ref: 2013MNRAS.435.2835W) Willett, K. W., Lintott, C. J., Bamford, S. P., et al. 2013, MNRAS, 435, 2835

(ref: 2022MNRAS.509.1303W) Williams, T. G., Kreckel, K., Belfiore, F., et al. 2022, MNRAS, 509, 1303

(ref: 2024arXiv240115142W) Williams, T. G., Lee, J. C., Larson, K. L., et al. 2024, arXiv e-prints, arXiv:2401.15142

(ref: 2021PASJ...73..257Y) Yajima, Y., Sorai, K., Miyamoto, Y., et al. 2021, PASJ, 73, 257

# Spiral galaxy sample

|  | log($M_\star$/${\rm M}_\odot$) | log(SFR/\[${\rm M}_\odot$ yr$^{-1}$\]) | spiral morphology | bar | MUSE |
|:---|:--:|:--:|:--:|:--:|:--:|
| IC 1954 | 9.7 | -0.44 | M | 1 | 0 |
| NGC 0628 | 10.3 | 0.24 | M | 0 | 1 |
| NGC 1097 | 10.8 | 0.68 | G | 1 | 0 |
| NGC 1300 | 10.6 | 0.07 | G | 1 | 1 |
| NGC 1365 | 11.0 | 1.23 | G | 1 | 1 |
| NGC 1385 | 10.0 | 0.32 | F | 0 | 1 |
| NGC 1512 | 10.7 | 0.11 | G | 1 | 1 |
| NGC 1566 | 10.8 | 0.66 | G | 1 | 1 |
| NGC 1637 | 9.9 | -0.19 | M | 1 | 0 |
| NGC 1672 | 10.7 | 0.88 | G | 1 | 1 |
| NGC 2090 | 10.0 | -0.39 | G | 0 | 0 |
| NGC 2283 | 9.9 | -0.28 | F | 1 | 0 |
| NGC 2566 | 10.7 | 0.94 | G | 1 | 0 |
| NGC 2835 | 10.0 | 0.09 | G | 1 | 1 |
| NGC 2997 | 10.7 | 0.64 | G | 0 | 0 |
| NGC 3507 | 10.4 | -0.00 | G | 1 | 0 |
| NGC 3627 | 10.8 | 0.58 | G | 1 | 1 |
| NGC 4254 | 10.4 | 0.49 | M | 0 | 1 |
| NGC 4303 | 10.5 | 0.73 | M | 1 | 1 |
| NGC 4321 | 10.7 | 0.55 | G | 1 | 1 |
| NGC 4535 | 10.5 | 0.33 | M | 1 | 1 |
| NGC 4536 | 10.4 | 0.54 | M | 1 | 0 |
| NGC 4548 | 10.7 | -0.28 | G | 1 | 0 |
| NGC 4579 | 11.1 | 0.34 | G | 1 | 0 |
| NGC 4731 | 9.5 | -0.22 | G | 1 | 0 |
| NGC 5248 | 10.4 | 0.36 | G | 1 | 0 |
| NGC 5643 | 10.3 | 0.41 | M | 1 | 0 |
| NGC 6744 | 10.7 | 0.38 | M | 1 | 0 |

: Spiral galaxy sample studied in this paper.

Table notes: Stellar mass and star formation rates of the spiral galaxies studied in this paper (cite: 2021ApJS..257...43L). The spiral morphology lists the spiral family according to (cite: 2015ApJS..217...32B) or the definitions adopted in (cite: 2021ApJ...913..113M) for galaxies outside the S$^4$G survey (‘G’ stands for grand-design, ‘M’ for multi-armed, and ‘F’ for flocculent). The bar presence (1 for barred) reflects the environmental masks from (cite: 2021A&A...656A.133Q). The last column indicates if the galaxy is in the PHANGS–MUSE subsample (1) or not (0).

# Calibration of SFR arm/interarm contrasts: The effect of extinction on H$\alpha$

![](SFRcon_Ha-MUSE_vs_MUSEsfr_fit-all.png)

Here, we use the PHANGS-MUSE dataset to calibrate the effect of neglecting extinction on SFR arm/interarm contrasts based on H$\alpha$. For 13 galaxies, we have both narrow-band and MUSE data, and we consider the arm/interarm contrasts in matched radial bins for the field of view in common. Figure [10](#fig:SFR_calibration1) shows this relation, in which the degree of correlation is remarkably high (Spearman rank coefficient 0.97). Yet, the relation is not one-to-one, and amplifies the contrast, in such a way that the largest contrasts get a proportionally larger boost when extinction is accounted for. This amplification effect is well described by the power-law relation shown in the figure, $\log\left({\rm SFR_{contrast}^{ext-corr}}\right)=-0.0013 + 1.1799\, \log\left({\rm H\alpha_{contrast}^{no-ext}}\right)$, where ${\rm SFR_{contrast}^{ext-corr}}$ is the arm/interarm contrast of SFR from MUSE, including the extinction correction based on the Balmer decrement, and ${\rm H\alpha_{contrast}^{no-ext}}$ is the SFR arm/interarm contrast consistently from MUSE H$\alpha$, but switching off the extinction correction. This means that we can use H$\alpha$ contrasts from our narrow-band imaging as a surrogate for the real SFR contrasts, without the need to degrade to lower resolution to apply a hybrid recipe that accounts for obscured star formation.

The scatter around the relation shown in Figure [10](#fig:SFR_calibration1) is only 0.1 dex (standard deviation in the $y$-axis relative to the power-law fit). This informs us about the uncertainty when neglecting extinction in our SFR contrast measurements. However, there are other sources of error that can also affect the contrasts based on narrow-band H$\alpha$. Indeed, the narrow-band H$\alpha$ maps are not perfectly identical to the MUSE-based H$\alpha$ maps for a number of reasons, including the \[NII\] contamination removal and filter transmission, neglecting H$\alpha$ absorption when subtracting the continuum broad-band from the narrow-band images, and from an imperfect calibration of narrow-band against broad-band.

![](SFRcon_Ha-MUSE_vs_HaAdam_fit.png)

To gauge the uncertainty associated with narrow-band H$\alpha$ calibration effects, we quantify the scatter when plotting the narrow-band H$\alpha$ contrasts as a function of the MUSE-based H$\alpha$ contrasts, for the same field of view and radial bins in galaxies where both are available. As shown in Figure [11](#fig:SFR_calibration2), there is a very good correlation between both variables (Spearman rank coefficient 0.98), with a vertical scatter of 0.059 dex around the 1:1 relation; we consider this representative of the uncertainty associated with SFR contrasts due to calibration limitations. We add it in quadrature to the uncertainty in our empirical calibration for the effect of extinction. Like this, we obtain a final uncertainty of 0.122 dex on the SFR surface density contrasts.

With this empirical calibration we circumvent the limitation of obscured star formation and assign realistic uncertainties to the SFR contrasts. These can be propagated to the measurement of SFE contrasts, so that we can conclusively tell in how many cases SFE is statistically enhanced in spiral arms relative to the interarm. For reference, Fig. [12](#fig:violin_plot_GD-vs-rest-Ha-only) shows the distribution of SFR contrasts (split into grand-design spirals and the rest) if we totally neglect extinction and take the ratio of arm-to-interarm H$\alpha$ surface densities.

![](Violin_plots_GD_rest_Ha-only.png)

# Stellar arm/interarm contrasts using different tracers

![](MUSE_SigStar_vs_IRAC-ICA.png)

Ground- and space-based NIR imaging is a common tracer of stellar mass, but the presence of dust emission can locally bias our view of the distribution of stellar surface density. This is particularly true when it comes to estimating arm/interarm contrasts. In this paper, we rely on stellar mass maps based on *Spitzer*/IRAC imaging corrected for non-stellar emission using an independent component analysis (ICA) method (cite: 2012ApJ...744...17M; 2015ApJS..219....5Q).

Figure [13](#fig:MUSE_SigStar_vs_IRAC-ICA) compares the stellar arm/interarm contrast from NIR imaging against fully independent estimates based on PHANGS–MUSE. These stellar mass maps rely on stellar population fitting (via pPXF) to Voronoi bins on the MUSE cubes, as implemented in the PHANGS–MUSE data analysis pipeline (cite: 2022A&A...659A.191E) and presented in (cite: 2021A&A...650A.134P; 2022A&A...663A..61P; 2023A&A...673A.147P). The change from the left to the right panel in Fig. [13](#fig:MUSE_SigStar_vs_IRAC-ICA) shows that the stellar contrast drops with the ICA correction, and comes much closer to the MUSE estimate. This decrease is expected, as the dust contribution that ICA corrects for is stronger around star-forming regions, and, thus, in spiral arms. The median stellar contrast drops from 1.71 to 1.56 after applying the ICA correction (while the mean contrast drops from 1.98 to 1.71).

With the ICA correction, $\Sigma_\mathrm{\star}$ contrasts show a better agreement with MUSE. In particular, the best-fit power law to means along spiral segments changes from $0.064 + 1.128\, \log\left({\rm \Sigma_{\star ~ contrast}^{MUSE}}\right)$ to $0.023 + 1.005\, \log\left({\rm \Sigma_{\star ~ contrast}^{MUSE}}\right)$. Thus, the best-fit power-law becomes more linear and the vertical offset with respect to the 1:1 line drops by a factor of three. The correlation also becomes slightly stronger (from $\rho = 0.73$ to $\rho = 0.80$) and the median absolute deviation drops from 0.08 to 0.03 dex. This sanity check is possible for a subset of 13 galaxies. For M51, (cite: 2019A&A...625A..19Q) also found that the ICA-corrected stellar mass map agrees well (better than the original IRAC) with an independent stellar mass map of M51 obtained through Bayesian marginalisation analysis by (cite: 2017ApJ...835...93M).

For completeness, Fig. [14](#fig:violin_plot_GD-vs-rest-extended) shows our nominal stellar contrasts based on ICA-corrected $3.6$ $\mu$m for an extended field of view (beyond the end of PHANGS–ALMA CO coverage). This confirms the significantly larger stellar contrasts associated with grand-design spirals.

![](Violin_extended_GD_rest.png)

# The implications of DIG for SFR arm/interarm contrast

While H$\alpha$ is a traditional tracer of star formation, as much as $\sim$50% of H$\alpha$ emission does not originate directly from H II regions, but from a more diffuse and extended component, often known as diffuse ionised gas (cite: 2007ApJ...661..801O; 2009RvMP...81..969H; 2016ApJ...827..103K; 2020MNRAS.493.2872C). As shown by (cite: 2022A&A...659A..26B), this component originates predominantly from leaking ionising photons from H II regions, which can travel $\sim$kpc distances before they contribute to the DIG emission. Therefore, there could be a fair concern that the DIG component introduces some dilution in the arm/interarm contrast of $\Sigma_\mathrm{SFR}$. In this section we examine the issue and conclude that DIG is unlikely to have a major impact in SFR contrast dilution.

While photons can travel significant distances away from H II regions before powering DIG (mean free path for the ionising radiation of 1.9 kpc according to (cite: 2022A&A...659A..26B)), this leakage is expected to happen mostly towards higher disc scale-heights, where densities are lower, away from the thin cold gas disc. This means that, since our targets have moderate inclinations (maximum inclination in the spiral sample considered here is 66$^\circ$), if photons mostly escape away from the galaxy plane, thanks to projection we will end up finding those photons relatively close to the H II region that they originated from. Since our spiral masks are reasonably broad (1-2 kpc), based on this argument we would not expect a large leakage of ionising photons from arm to interarm (we would expect most DIG due to spiral star formation within the spiral masks).

The maps from PHANGS–MUSE show that the most intense DIG seems to accumulate immediately around H II regions, mostly within distances of a few hundred parsecs. To confirm this visual impression, we performed a test using the PHANGS–MUSE data, for which H II region masks are available (cite: 2022A&A...658A.188S; 2023MNRAS.520.4902G). Our main concern is whether a significant fraction of the H$\alpha$ emission outside H II regions in the interarm arises from DIG due to leaked photons from spiral arms, which could bias the arm/interarm SFR (and SFE) contrasts. If this were the dominant contribution to DIG in the interarm, we would expect this component to be distributed relatively smoothly across the interarm and not preferentially close to H II regions in the interarm. We find that, on average, $\sim$70% of the (Balmer-corrected) H$\alpha$ flux in the interarm is inside the H II region masks, covering an area of $\sim$15% of the interarm region. However, the remaining $\sim$30% of H$\alpha$ flux is not evenly distributed across the remaining pixels. On the contrary, most of the remaining flux is close to interarm H II regions. If we dilate the H II region masks to cover $\sim$25% of the remaining area, we do not recover 25% of the remaining flux, but as much as 60% of the remaining flux. Therefore, most DIG in the interarm regions seems quite clearly associated with interarm H II regions, and not due to leaked photons from the spiral arms.

Based on the arguments we examine above, we believe that DIG should be included in our arm/interarm contrast measurements, as we have done across this paper. Previous studies tried to correct for DIG, under the premise that it is not directly tracing star formation (cite: 2022ApJ...927....9P). If we consider the arm/interarm contrast purely arising from flux found within H II regions (setting to zero all pixels outside the H II region masks for the MUSE targets), we find that the SFR contrasts tend to go up (by 45% on average, or 34% median). However, such measurements suffer from an important bias, because the filling factor of H II regions in spiral arms is much higher than in the interarm, and this means that a leaked photon is more likely to be found within the footprint of a nearby H II region in spiral arms than in the interarm. As H II regions are more sparse in the interarm, leaked photons are less likely to be found within the footprint of another H II region.

# Effect of mask width

![](orig_vs_narrow.png)

The spiral masks released in (cite: 2021A&A...656A.133Q), the nominal option adopted in this paper, are relatively broad, with a typical width of $1{-}2$ kpc. This is in order to accommodate for local departures from a perfect log-spiral function and to encompass the different tracers that we consider (NIR, CO, H$\alpha$). In this Section, we explicitly measure the effect of spiral mask width by comparing our nominal results against the contrast using narrower spiral masks, which closely follow the ridge of molecular gas and star formation, as introduced in Sect. [2.6.2](#Sec:thinnersp). These masks have typical widths between 500 and 1000 pc, so about half the width of the original masks (still keeping a few resolution elements across the spiral mask).

Figure [15](#fig:orig_vs_narrow) shows that contrasts based on the original and narrow masks track each other very well (Spearman rank correlation coefficients $\rho \gtrsim 0.9$). If we fit a power-law for each tracer separately, we find that the relation is essentially linear with a small offset towards higher contrasts for the narrow masks in $\Sigma_\mathrm{mol}$ and $\Sigma_\mathrm{SFR}$. Indeed, the median increase in $\Sigma_\mathrm{\star}$ contrasts when measured using the narrow masks is just 1%, whereas this number is 10% and 11% for $\Sigma_\mathrm{mol}$ and $\Sigma_\mathrm{SFR}$, respectively. This is much smaller than the ${\sim} 40\%$ increase that we measured when shifting from low (1.5 kpc) to high (${\sim} 100$ pc) resolution. The change in $\Sigma_\mathrm{mol}$ and $\Sigma_\mathrm{SFR}$ when adopting the narrower masks is such that the resulting SFE remains on average the same. Therefore, the contrasts are not strongly affected by the width of the spiral mask, and the effect is far more limited than spatial resolution. Yet, there is some scatter in the plots that makes it clear that, even though it should not affect global trends, the details of the spiral masks do affect individual measurements in a non-trivial way.

# Sanity checks and alternatives to measure contrasts

![](binning_alternatives.png)

Here we consider as sanity checks several alternatives to measure contrasts. Table [\[table:stats_appendix\]](#table:stats_appendix) shows the resulting rank correlation coefficients (Spearman $\rho$) and the slope and intercept of bisector fits for different relations examined in this paper: the contrast in molecular gas ($\Sigma_\mathrm{mol}$), star formation rate ($\Sigma_\mathrm{SFR}$), and star formation efficiency (SFE) as a function of stellar contrast ($\Sigma_\mathrm{\star}$), and the star formation rate contrast as a function of the molecular gas contrast. For each of these relations, we show the correlation coefficients and fits based on the individual spiral segments (one average value per spiral segment, so typically two datapoints per galaxy), and also for all radial bins (hundreds of datapoints across all galaxies). The various blocks of rows show different alternatives, either changing tracers or methodology. The former includes using all tracers at lower resolution (Sect. [3.8](#Sec:effect_res)), measuring SFR directly from H$\alpha$ (without applying the empirical correction for extinction introduced in Sect. [7](#sec:AppendixMUSE)), estimating SFR using extinction-corrected H$\alpha$ (based on the Balmer decrement) from MUSE, which is only available for a subset of galaxies and a smaller field of fiew, or, also for MUSE galaxies, calculating the $\Sigma_\mathrm{SFR}$ contrast only within H II regions (blanking the SFR map outside the H II region mask, (cite: 2022A&A...659A..26B)). The methodological alternatives include using narrower spiral masks (Appendix [10](#Sec:narrow)), using bins that follow each spiral segment at uniform length steps compared to interarm regions at matched galactocentric radii (Fig. [16](#fig:binning_alternatives)), or the same bins along spiral segments with interarm regions defined as adjacent ‘boxes’ (immediately on top and below each spiral bin).

We see that rank coefficients become smaller when considering radial bins instead of entire spiral segments. This is expected since, on the smaller radial bins, we are more sensitive to local, stochastic variations in surface density and we are generally more affected by the noise of the individual measurements; by averaging over entire spiral segments, the contrast measurements become more robust.

In agreement with what we present in Sect. [3.8](#Sec:effect_res) and Appendix [10](#Sec:narrow), the effect of using narrower masks or employing a lower resolution can affect the actual contrast measurements, but does not affect dramatically the relations between contrasts. The slopes that we find are typically compatible within a few $\sigma$.

As shown by Fig. [12](#fig:violin_plot_GD-vs-rest-Ha-only), the application of the empirical calibration that we introduced in Sect. [7](#sec:AppendixMUSE) to account for extinction in the $\Sigma_\mathrm{SFR}$ contrasts does not affect qualitatively the distribution of SFR or SFE contrasts. Table [\[table:stats_appendix\]](#table:stats_appendix) confirms that this choice does not have a strong impact on the relations between contrasts either. If we instead use MUSE extinction-corrected H$\alpha$ for $\Sigma_\mathrm{SFR}$, we do find slopes which are quite different, but also the error bars become much larger. Since MUSE is only available for a subset of galaxies and a smaller field of fiew, the noise increases considerably. The same applies to SFR calculated for MUSE within H II regions.

If we employ either wider (1000 pc) or narrower (250 pc) radial bins, the trends remain qualitatively the same, with similar correlation coefficients and slopes that are well compatible within the uncertainties. The alternative sampling schemes introduce in practice many more bins and therefore noise increases significantly. This is particularly true if we consider all radial bins together for interarm regions defined as immediately adjacent to each spiral bin, which increases the stochasticity; averaging over an entire ring at a given range of galactocentric radii provides a more stable reference value than measuring the average surface densities on small boxes next to the arm, where local fluctuations can lead to very different arm/interarm surface density ratios.

In conclusion, the precise values of the contrasts are sensitive to the various choices in methodology and tracers, but our qualitative conclusions remain valid independently from these details.

+-------------+------------------------------------------------+---------------------------------------------------------+--------------------------------------------------------+
|             |                                                | individual spiral segments                              | all radial bins                                        |
+:============+:===============================================+:===============:+:=================:+:=================:+:===============:+:================:+:=================:+
| 3-5 (lr)6-8 |                                                | Spearman $\rho$ | Slope             | Intercept         | Spearman $\rho$ | Slope            | Intercept         |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{mol}$ | $0.73$          | $1.83 \pm  0.46$  | $0.16 \pm  0.03$  | $0.46$          | $2.23 \pm  0.15$ | $0.08 \pm  0.02$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{SFR}$ | $0.61$          | $2.89 \pm  1.29$  | $0.15 \pm  0.04$  | $0.55$          | $3.36 \pm  0.37$ | $0.01 \pm  0.02$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– SFE                   | $0.34$          | $1.68 \pm  0.30$  | $-0.09 \pm  0.04$ | $0.27$          | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{mol}$– $\Sigma_\mathrm{SFR}$   | $0.78$          | $1.61 \pm  0.25$  | $-0.13 \pm  0.08$ | $0.69$          | $1.35 \pm  0.07$ | $-0.06 \pm  0.03$ |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{mol}$ | $0.65$          | $1.83 \pm  0.48$  | $0.19 \pm  0.03$  | $0.48$          | $2.19 \pm  0.17$ | $0.13 \pm  0.02$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{SFR}$ | $0.47$          | $2.77 \pm  1.45$  | $0.21 \pm  0.05$  | $0.51$          | $3.20 \pm  0.41$ | $0.08 \pm  0.03$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– SFE                   | $0.19$          | $1.50 \pm  0.29$  | $-0.07 \pm  0.05$ | $0.24$          | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{mol}$– $\Sigma_\mathrm{SFR}$   | $0.77$          | $1.56 \pm  0.23$  | $-0.10 \pm  0.08$ | $0.68$          | $1.36 \pm  0.07$ | $-0.07 \pm  0.04$ |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{mol}$ | $0.83$          | $1.91 \pm  0.25$  | $0.05 \pm  0.02$  | $0.68$          | $1.86 \pm  0.09$ | $0.05 \pm  0.01$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{SFR}$ | $0.75$          | $2.65 \pm  0.43$  | $0.02 \pm  0.04$  | $0.64$          | $2.31 \pm  0.11$ | $0.04 \pm  0.01$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– SFE                   | $0.36$          | $1.10 \pm  0.12$  | $-0.05 \pm  0.02$ | $0.14$          | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{mol}$– $\Sigma_\mathrm{SFR}$   | $0.82$          | $1.28 \pm  0.10$  | $-0.02 \pm  0.02$ | $0.78$          | $1.23 \pm  0.05$ | $-0.02 \pm  0.01$ |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{mol}$ | $0.73$          | $1.83 \pm  0.46$  | $0.16 \pm  0.03$  | $0.46$          | $2.23 \pm  0.15$ | $0.08 \pm  0.02$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{SFR}$ | $0.61$          | $2.43 \pm  0.82$  | $0.11 \pm  0.03$  | $0.55$          | $2.87 \pm  0.26$ | $0.01 \pm  0.02$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– SFE                   | $0.27$          | $1.42 \pm  0.27$  | $-0.14 \pm  0.04$ | $0.19$          | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{mol}$– $\Sigma_\mathrm{SFR}$   | $0.78$          | $1.35 \pm  0.18$  | $-0.12 \pm  0.07$ | $0.69$          | $1.16 \pm  0.06$ | $-0.05 \pm  0.03$ |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{mol}$ | $0.55$          | $2.47 \pm  2.06$  | $0.19 \pm  0.06$  | $0.40$          | $2.66 \pm  0.51$ | $0.12 \pm  0.03$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{SFR}$ | $0.37$          | $3.05 \pm  3.80$  | $0.32 \pm  0.12$  | $0.46$          | $4.12 \pm  1.10$ | $0.12 \pm  0.04$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– SFE                   | $0.17$          | $1.08 \pm  0.85$  | $0.10 \pm  0.06$  | $0.23$          | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{mol}$– $\Sigma_\mathrm{SFR}$   | $0.71$          | $1.69 \pm  0.33$  | $-0.12 \pm  0.14$ | $0.69$          | $1.57 \pm  0.08$ | $-0.08 \pm  0.04$ |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{mol}$ | $0.55$          | $2.47 \pm  2.06$  | $0.19 \pm  0.06$  | $0.40$          | $2.66 \pm  0.51$ | $0.12 \pm  0.03$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{SFR}$ | $0.45$          | $2.14 \pm  1.41$  | $0.16 \pm  0.04$  | $0.49$          | $2.47 \pm  0.37$ | $0.09 \pm  0.02$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– SFE                   | $-0.12$         | $-1.14 \pm  0.31$ | $0.12 \pm  0.04$  | $-0.01$         | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{mol}$– $\Sigma_\mathrm{SFR}$   | $0.69$          | $0.87 \pm  0.08$  | $-0.01 \pm  0.04$ | $0.59$          | $0.92 \pm  0.05$ | $-0.02 \pm  0.03$ |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{mol}$ | $0.74$          | $1.86 \pm  0.48$  | $0.16 \pm  0.03$  | $0.45$          | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{SFR}$ | $0.58$          | $2.99 \pm  1.44$  | $0.14 \pm  0.04$  | $0.53$          | $3.43 \pm  0.28$ | $0.00 \pm  0.02$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– SFE                   | $0.25$          | $1.58 \pm  0.41$  | $-0.06 \pm  0.05$ | $0.26$          | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{mol}$– $\Sigma_\mathrm{SFR}$   | $0.79$          | $1.65 \pm  0.26$  | $-0.14 \pm  0.08$ | $0.67$          | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{mol}$ | $0.71$          | $1.64 \pm  0.38$  | $0.16 \pm  0.03$  | $0.45$          | $2.04 \pm  0.20$ | $0.10 \pm  0.02$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{SFR}$ | $0.55$          | $2.65 \pm  1.00$  | $0.13 \pm  0.04$  | $0.56$          | $3.11 \pm  0.45$ | $0.04 \pm  0.03$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– SFE                   | $0.38$          | $1.60 \pm  0.26$  | $-0.10 \pm  0.03$ | $0.29$          | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{mol}$– $\Sigma_\mathrm{SFR}$   | $0.77$          | $1.72 \pm  0.23$  | $-0.18 \pm  0.08$ | $0.72$          | $1.26 \pm  0.11$ | $-0.02 \pm  0.05$ |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{mol}$ | $0.74$          | $1.76 \pm  0.34$  | $0.16 \pm  0.03$  | $0.50$          | $1.92 \pm  0.07$ | $0.08 \pm  0.01$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{SFR}$ | $0.63$          | $2.83 \pm  1.14$  | $0.23 \pm  0.11$  | $0.58$          | $3.08 \pm  0.15$ | $-0.02 \pm  0.02$ |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– SFE                   | $0.41$          | $1.43 \pm  0.26$  | $0.05 \pm  0.05$  | $0.35$          | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{mol}$– $\Sigma_\mathrm{SFR}$   | $0.71$          | $1.37 \pm  0.22$  | $0.10 \pm  0.07$  | $0.72$          | $1.49 \pm  0.05$ | $-0.12 \pm  0.02$ |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{mol}$ | $0.57$          | $1.37 \pm  0.37$  | $0.41 \pm  0.04$  | $0.29$          | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– $\Sigma_\mathrm{SFR}$ | $0.60$          | $1.54 \pm  0.55$  | $0.59 \pm  0.04$  | $0.35$          | $3.19 \pm  0.38$ | $0.24 \pm  0.02$  |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{\star}$– SFE                   | $0.14$          | $1.02 \pm  0.19$  | $0.28 \pm  0.04$  | $0.15$          | $1.60 \pm  0.20$ | $-0.03 \pm  0.02$ |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             | $\Sigma_\mathrm{mol}$– $\Sigma_\mathrm{SFR}$   | $0.78$          | $1.12 \pm  0.09$  | $0.10 \pm  0.04$  | $0.52$          | —                | —                 |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+
|             |                                                |                 |                   |                   |                 |                  |                   |
+-------------+------------------------------------------------+-----------------+-------------------+-------------------+-----------------+------------------+-------------------+

[^1]: Physics at High Angular resolution in Nearby GalaxieS; <http://www.phangs.org>

[^2]: We note that matching to the best common CO physical resolution ($180$ pc) has a minimal effect on the contrasts (scatter of ${\sim}3$%, without systematic offsets), because this is still small compared to the width of the spiral masks (${\sim}1{-}2$ kpc).

[^3]: $R_{25}$ is the radius where the average surface brightness is $\mu_{\rm B} = 25$ mag arcsec$^{-2}$.

[^4]: <https://www.canfar.net/storage/vault/list/phangs/RELEASES/Querejeta_etal_2024>

[^5]: Using the median instead of the mean does not qualitatively affect our conclusions. We prefer the mean as we find that it is more robust, particularly for the interarm region, where the median often falls below the noise level (as already pointed out by (cite: 2021ApJ...913..113M)).

[^6]: This is just slightly above the maximum characteristic separation length between independent star-forming regions measured for PHANGS galaxies by (cite: 2022MNRAS.516.3006K); we consider the effect of varying this bin width in Appendix [11](#sec:sanity_checks).

[^7]: The galaxies without high-resolution PHANGS SFR maps are: NGC1097, NGC1637, NGC3507, NGC4536, NGC4579, and NGC5643.

</paper>

Write the methods card for this paper.