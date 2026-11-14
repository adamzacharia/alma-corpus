# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...686A.146Z\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...686A.146Z",
 "title": "Gas inflows from cloud to core scales in G332.83-0.55: Hierarchical hub-filament structures and tide-regulated gravitational collapse",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Zhou, J. W.",
 "n_authors": 7,
 "arxiv_id": "2403.13442",
 "doi": "10.1051/0004-6361/202449514",
 "alma_projects_linked_by_archive": [
  "2019.1.00685.S"
 ]
}
```

Paper text:
<paper>
# Gas inflows from cloud to core scales in G332.83-0.55: Hierarchical hub-filament structures and tide-regulated gravitational collapse

The massive star-forming region G332.83-0.55 contains at least two levels of hub-filament structures. The hub-filament structures may form through the "gravitational focusing" process. High-resolution LAsMA and ALMA observations can directly trace the gas inflows from cloud to core scales. We investigated the effects of shear and tides from the protocluster on the surrounding local dense gas structures. Our results seem to deny the importance of shear and tides from the protocluster. However, for a gas structure, it bears the tidal interactions from all external material, not only the protocluster. To fully consider the tidal interactions, we derived the tide field according to the surface density distribution. Then, we used the average strength of the external tidal field of a structure to measure the total tidal interactions that are exerted on it. For comparison, we also adopted an original pixel-by-pixel computation to estimate the average tidal strength for each structure. Both methods give comparable results. After considering the total tidal interactions, for the scaling relation between the velocity dispersion $\sigma$, the effective radius $R$, and the column density $N$ of all the structures, the slope of the $\sigma-N*R$ relation changes from 0.20$\pm$0.04 to 0.52$\pm$0.03, close to 0.5 of the pure free-fall gravitational collapse, and the correlation also becomes stronger. Thus, the deformation due to the external tides can effectively slow down the pure free-fall gravitational collapse of gas structures. The external tide tries to tear up the structure, but the external pressure on the structure prevents this process. The counterbalance between the external tide and external pressure hinders the free-fall gravitational collapse of the structure, which can also cause the pure free-fall gravitational collapse to be slowed down. These mechanisms can be called "tide-regulated gravitational collapse."

# Introduction

High-resolution observations of high-mass star-forming regions show that density enhancements are organized in filamentary gas networks, particularly in hub-filament systems. Hub-filament systems are known as a junction of three or more filaments. Filaments have lower column densities compared to the hubs (cite: Myers2009; Schneider2012; Kumar2020-642; Zhou2022-514). In such systems, converging flows funnel matter into the hub through the filaments. Previous studies have suggested that hub-filament systems are birth cradles of high-mass stars and clusters (cite: Peretto2013; Henshaw2014; Zhang2015; Liu2016; Contreras2016-456; Yuan2018; Lu2018; Issac2019; Dewangan2020; Liu2021-646; Liu2022-511; Kumar2020-642; Zhou2022-514; Liu2023-522; Xu2023arXiv; Zhou2023-676; Yang2023-953). (cite: Zhou2022-514) studied the physical properties and evolution of hub–filament systems by spectral lines that were observed in the ATOMS (ALMA Three-millimeter Observations of Massive Star-forming regions) survey (cite: Liu2020). We found that hub-filament structures can exist at various scales from 0.1 parsec to several parsec in very different Galactic environments. Below the 0.1 parcsec scale, slender structures similar to filaments, such as spiral arms, have also been detected in the surroundings of high-mass protostars (cite: Liu2015-804; Maud2017-467; Izquierdo2018-478; Chen2020-4; Sanhueza2021-915; Olguin2023-959). Therefore, a scenario was proposed in (cite: Zhou2022-514): Self-similar hub-filament structures and filamentary accretion seem to exist at all scales (from several thousand au to several parsec) in high-mass star-forming regions. This paradigm of hierarchical and multi-scale hub-filament structures was generalized from clump-core scale to cloud-clump scale in (cite: Zhou2023-676). Hierarchical collapse and hub-filament structures feeding the central regions are also described in previous works, such as (cite: Motte2018-56), (cite: Vazquez2019-490), (cite: Kumar2020-642) and references therein.

As discussed in (cite: Zhou2023-676), the change in velocity gradients with the scale in the G333 complex indicates that the morphology of the velocity field in PPV space resembles a "funnel" structure. The funnel structure can be explained as accelerated material flowing toward the central hub and gravitational contraction of star-forming clouds or clumps. To some extent, the funnel structure gives an indication of the gravitational potential well that is formed by the clustering.

In this work, we focus on a local region G333-s3a in the G333 complex, called G332.83-0.55 hereinafter, which is marked in Fig.1 of (cite: Zhou2023-676), also shown in Fig.[1](#map). G332.83-0.55 presents a typical hub-filament morphology at $\sim$10 pc. As a cloud-scale hub-filament system, its hub corresponds to the ATLASGAL clump AGAL332.826-00.549. High-resolution APEX/LAsMA $^{12}$CO and $^{13}$CO (3-2) observation allowed us to trace the gas kinematics and gas inflows from cloud to clump scales in G332.83-0.55. We also zoomed in on the hub region of G332.83-0.55 using high-resolution ALMA HCO$^{+}$ (1-0) and H$^{13}$CO$^{+}$ (1-0) observations to investigate gas motions from clump to core scales. By combing LAsMA and ALMA observations, we could directly recover the hierarchical or multi-scale hub-filament structures and gas inflows in G332.83-0.55. In addition, we were also able to characterize the details of the funnel structure at different scales.

# Observations and data

## LAsMA data

The seven pixel Large APEX sub-Millimeter Array (LAsMA) receiver of the APEX telescope was used to observe the $J=3-2$ transitions of $^{12}$CO and $^{13}$CO in the G333 molecular cloud complex. A detailed description of data calibration, imaging, and product creation procedures is presented in (cite: Zhou2023-676). The final data cubes have a velocity resolution of 0.25 km s$^{-1}$ and an angular resolution of $19.5 \ensuremath{''}$ and the pixel size is $6 \ensuremath{''}$. The final noise levels of the $^{12}$CO (3–2) and $^{13}$CO (3–2) data cubes are $\sim$0.32 K and $\sim$0.46 K, respectively. In this paper, we only focus on the subregion G332.83-0.55.

## ALMA data

We selected one source from the ATOMS survey (Project ID: 2019.1.00685.S; PI: Tie Liu). The details of the 12m array and 7m array ALMA observations were summarized in (cite: Liu2020; Liuh2021). Calibration and imaging were carried out using the CASA software package version 5.6 (cite: McMullin2007); more details can be found in (cite: Zhou2021-508). All images have been primary-beam corrected. The continuum image reaches a typical 1 $\sigma$ rms noise of $\sim$0.2 mJy in a synthesized beam FWHM size of $\sim2.2\ensuremath{''}$. In this work, we also use the H$^{13}$CO$^+$ J=1-0 and HCO$^+$ J=1-0 molecular lines. The final noise levels of the H$^{13}$CO$^+$ J=1-0 and HCO$^+$ J=1-0 data cubes are $\sim$0.008 Jy beam$^{-1}$ and $\sim$0.012 Jy beam$^{-1}$, respectively.

## Archival data

We also used ATLASGAL+Planck 870 $\mu$m data (ATLASGAL combined with Planck data), which are sensitive to a wide range of spatial scales at a resolution of $\sim21\ensuremath{''}$ (cite: Csengeri2016-585).

# Results

## Connection of gas inflows in LAsMA and ALMA observations

![](ref/map.pdf)

![](ref/flow1.pdf)

![](ref/flow.pdf)

![](ref/pv.pdf)

![](ref/peak.pdf)

Moment maps of various molecular lines are shown in Fig.[1](#map). The Moment 0 maps of $^{13}$CO (3$-$2), H$^{13}$CO$^+$ J=1-0, and HCO$^+$ J=1-0 emission show a typical hub-filament morphology. The FILFINDER algorithm (cite: Koch2015) was used to identify and characterize filaments traced by H$^{13}$CO$^{+}$ (1-0) and $^{13}$CO (3$-$2) emission. Following the method described in (cite: Zhou2022-514) and (cite: Zhou2023-676), we used the integrated intensity (Moment 0) maps to identify filaments. The skeletons of the identified filaments, overlaid on the Moment 0 maps in Fig.[2](#flow1), are highly consistent with the gas structures. We selected the filaments through the redshifted and blueshifted peaks (LAsMA-f3 and ALMA-f3), and extracted the velocity and intensity along the filaments, as shown in Fig.[3](#flow).

Fig.[4](#pv) displays the position-velocity (PV) diagrams along the dashed lines in panels (b1) and (d1) of Fig.[1](#map). For H$^{13}$CO$^+$ J=1-0 emission, feedback from the central UC-HII region identified in (cite: Zhang2023-520) has destroyed the surrounding molecular gas structure (Fig.[1](#map)(d)). Thus, the diagram looks broken, but it still has a clear double-peak velocity structure, indicating that the surrounding gas is still infalling onto the protocluster (Sec.[3.2](#infall)). In Fig.[4](#pv) (b), the central part of the PV diagram has a similar morphology to Fig.[4](#pv) (a). Large-scale gas structures with clear velocity gradients are connected to the central velocity jump. Correspondingly, large-scale filamentary structures connected to the central clump can be seen in Fig.[1](#map)(a) and (b); small-scale filamentary structures down to dense core scales are also presented in Fig.[1](#map)(c) and (d). These features indicate that cloud-scale gas inflows extend down to core scales. The inheritance of gas flows on large scales to small scales is clearly visible in Fig.[3](#flow)(c).

Fig.[5](#ppv)(a) displays the PPV map of $^{13}$CO (3$-$2) emission decomposed by the fully automated Gaussian decomposer `GAUSSPY+` (cite: Lindner2015-149; Riener2019-628); the decomposition was carried out in (cite: Zhou2023-676). We can see a funnel structure that can be a probe of gravitational collapse as discussed in (cite: Zhou2023-676). At small scales, we can roughly identify a velocity jump comprised of the redshifted and blueshifted peaks in Fig.[2](#flow1)(c), which is clearly shown in Fig.[2](#flow1)(d), thanks to the higher resolution of the ALMA data.

To conclude, G332.83-0.55 shows at least two levels of hub-filament structures. Fig.[1](#map)(a) and (b) present the first level from cloud to clump scales. The second level from clump to core scales is shown in Fig.[1](#map)(c) and (d). In a statistical study of hub-filament systems in (cite: Zhou2022-514), we found filaments are ubiquitous in proto-clusters, and hub-filament systems are very common from dense core scales ($\sim$0.1 pc) to clump and cloud scales ($\sim$1-10 pc). These observed features are reproduced in G332.83-0.55 well.

The structures marked by small red circles in Fig.[1](#map)(a) and (b) present an approximately spherical morphology due to the limited resolution in single-dish observation, usually referred to as a "clump." However, in the eyes of ALMA, the spherical clump displays anisotropic and filamentary accretion structures (hub-filament) in Fig.[1](#map)(c) and (d). Thus, relative to the traditional "infall envelope," filamentary accretion and inflow structures may be more realistic in high-mass star-forming clumps.

## Infall+rotation motions

In Fig.[1](#map)(c) and (d), on small scales, H$^{13}$CO$^+$ J=1-0 and HCO$^+$ J=1-0 emission present spiral-like structures, indicating the rotation of gas around the protocluster. PV diagrams in Fig.[4](#pv) also reveal rotation motions. The PV diagrams show two peaks separated by several km s$^{-1}$, and they are symmetrically located with respect to the gravitational center. The double-peaked feature on the PV map is often seen in cluster-forming clumps, and this feature can only be reproduced when the clump has both infall motion and rotation at the same time, thus strongly implying that the clump is collapsing with rotation (cite: Ohashi1997-475; Shimoikura2016-832; Shimoikura2018-855; Sanna2019-623; Liu2020-904; Shimoikura2022-928). Around the gravitational center, we can see the blueshifted and redshifted extrema at the end of the velocity jump in Fig.[3](#flow), which is comparable with Fig.2 of (cite: Sakai2014-507). In the schematic diagram of an infalling and rotating envelope model for IRAS 04368+2557 (cite: Sakai2014-507), the shift of blueshifted and redshifted peaks can be used to estimate the radius of the centrifugal barrier $r_{\rm c}$, where the rotation velocity $V_{\rm rotation}$ has its maximum value. According to equations (1) and (2) in (cite: Sakai2014-507), we can estimate the mass of the gravitational center according to $r_{\rm c}$ by $$\begin{equation}
M_{*}= \frac{V_{\rm rotation}^{2}r_{\rm c}}{2G}.
\label{mass}
\end{equation}$$ The initial physical quantities in this equation can be estimated from the velocity jump in Fig.[3](#flow).

Both the velocity fields traced by LAsMA and ALMA data show a velocity jump around the gravitational center. In Fig.[3](#flow)(c), the velocity fields along the large- and small-scale filaments can be roughly connected, despite the significant differences in their resolutions (2.5$\ensuremath{''}$ and 19.5$\ensuremath{''}$).

According to the velocity difference and the separation between blueshifted and redshifted peaks in Fig.[3](#flow)(c), we roughly estimate

$V_{\rm rotation,ALMA} \approx$3.29 km/s and $r_{\rm c, ALMA} \approx$ 0.21 pc. Then according to equation.[\[mass\]](#mass), the mass of the gravitational center (i.e., the protocluster) is $\sim$264 M$_{\odot}$.

As a further test, following the method described in (cite: Kauffmann2008), the mass can be computed by dust emission using $$\begin{eqnarray}
  M & = &
  \displaystyle 0.12 \, M_{\odot}
  \left( {\rm e}^{1.439 (\lambda / {\rm mm})^{-1}
      (T / {\rm 10 ~ K})^{-1}} - 1 \right) \nonumber \\
  & & \displaystyle
 \left( \frac{\kappa_{\nu}}{0.01 \rm ~ cm^2 ~ g^{-1}} \right)^{-1}
  \left( \frac{F_{\nu}}{\rm Jy} \right)
  \left( \frac{d}{\rm 100 ~ pc} \right)^2
  \left( \frac{\lambda}{\rm mm} \right)^{3},
  \label{mass_eq}
\end{eqnarray}$$ where the opacity is $$\begin{equation}
\kappa_{\nu}=0.1({\nu}/\textrm{1000~GHz})^{\beta}~{\rm cm}^{2} {\rm g}^{-1}
\end{equation}$$ and $\beta$ is the dust emissivity spectral index. Here, we consider $\beta=1.5$,

$F_\nu$ is the total flux of 3mm dust emission, $d$ is the distance to the source, and $\lambda$ is the wavelength. The temperature $T$ takes the value $\sim$31.4 K listed in Table A1 of (cite: Liu2020). A mass $\sim$264M$_{\odot}$ corresponds to the flux of 3mm dust emission $\sim$0.12 Jy. This value is $\sim$3% of the total flux of 3mm continuum emission in ALMA observations. As discussed in (cite: Keto2008-672) and (cite: Zhang2023-520), 3mm continuum emission of UC HII regions in high-resolution interferometric observations should be mostly free–free emission rather than from dust, and thus the proportion of $\sim$3% for the dust emission is reasonable.

## Local dense gas structures

The issues of identifying the structures in a PPV cube by the dendrogram algorithm are described in (cite: Zhou2024-682), and thus we adopted the same method as in (cite: Zhou2024-682) and (cite: Zhou2024-682-173) to identify dense gas structures. We directly identified hierarchical (sub)structures based on the 2D integrated intensity (Moment 0) map of H$^{13}$CO$^{+}$ (1$-$0) emission, and then extracted the average spectrum of each structure to investigate its velocity components and gas kinematics. More details can be found in (cite: Zhou2024-682-173). In this work, we focus on leaf structures, which are local gravitational centers. According to their averaged spectra, the structures with absorption features were eliminated first. Following (cite: Zhou2024-682-173), we only consider type1 (single velocity component) and type3 (blended velocity component) structures, as marked in Fig.[1](#map)(d) by ellipses.

We derived the column density by combining H$^{13}$CO$^+$ J=1-0 and HCO$^+$ J=1-0 emission using the same method described in Sec.3.3 of (cite: Zhou2024-682-173) by the local thermodynamic equilibrium (LTE) analysis. Then the masses and virial ratios of all leaf structures were calculated.

## Shear and tide from the protocluster

![](ref/scaling.pdf)

The very large velocity difference (velocity jump) around the protocluster in Fig.[3](#flow), Fig.[4](#pv) and Fig.[5](#ppv) may indicate that the surrounding gas structures bear considerable shear and tides from the protocluster, apart from infall and rotation motions. Fig.[6](#scaling)(c) shows the scaling relations between the velocity dispersion $\sigma$, the effective radius $R$, and the column density $N$ of all leaf structures, similar to (cite: Zhou2024-682) and (cite: Zhou2024-682-173), the slope of the $\sigma_{s}-N*R$ relation is $\sim$0.2, which is much smaller than 0.5 and may indicate a pure free-fall gravitational collapse is slowing down.

To investigate the shear and tides from the protocluster, here we analogy to the methods that are adopted on galaxy-cloud scales. For cloud-scale gas structures in the galaxy, as described in (cite: Hunter1998-493) and (cite: Dib2012-758), the shear parameter $S_{g}$ is defined as $$\begin{equation}
S_{g}=\frac{\Sigma_{\rm cri}}{\Sigma}.
\label{eq:6}
\end{equation}$$ We note that $\Sigma$ is the local gas surface density and $\Sigma_{\rm cri}$ is the critical surface density, which represents the minimal surface density needed to resist the shear. Following equation.7 of (cite: Dib2012-758), $$\begin{equation}
\Sigma_{\rm cri}=\frac{A \sigma \ln(C)}{2\pi G} \, .
\label{eq:5}
\end{equation}$$The $C$ represents the density contrast between leaf structures and their surroundings. The ratio between the average surface density derived from $^{13}$CO (3$-$2) emission in the FOV of the ALMA observation and the highest surface density of leaf structures is $\sim 100$, and thus we consider $C$=100. We note that $\sigma$ is the local gas velocity dispersion and $A$ is the Oort constant, which measures the local shear level. For a spherical cloud of radius $r$, with a rotational velocity $V$ at a galactocentric distance $R_{G}$, $A$ can be calculated as $$\begin{equation}
A= 0.5 \left( \frac{V}{R_{G}} - \frac{\mid V(R_{G}+r) - V(R_{G}-r) \mid}{2r} \right) \, ,
\label{shear}
\end{equation}$$ in the context of molecular clouds, $V$ is determined by the rotation curve of the galaxy. In our case, for gas structures in the clump around the protocluster, $V$ was estimated by the Kepler rotation curve, as discussed in Sec.[3.2](#infall). The $V = \sqrt{GM_{0}/R'}$, with $M_{0}$ being the mass of the protocluster and $R'$ being the distances between gas structures and the protocluster. Shear is effective at tearing apart the gas structure if $S_{g}>1$ and it can be ineffective if $S_{g}<1$.

In a galactic context, the overall gas and stellar distribution can contribute to confine or disrupt the gas structures. For a cloud at a distance $R_{G}$ from the galactic center, the edge of the cloud from the galactic center is at a distance of $R_{G}$+$r$. The tidal acceleration in the cloud is $\sim T*r$, following (cite: Stark1978-225), $$\begin{equation}
T=\frac{V^{2}}{R_{G}^{2}}-\frac{\partial}{\partial R_{G}}\left(\frac{V^{2}}{R_{G}}\right)  \, .
\label{tide}
\end{equation}$$ Inserting the Keplerian rotation curve, $T = 3GM_{0}/R'^{3}$, which is similar to equation.[\[point\]](#point). Then the effective velocity dispersion from the tide for a structure is $\sigma_{t}^2 \sim$ $T*R^2$, where $R$ is the effective radius of the structure.

In Fig.[6](#scaling), $S_{g} << 1$ and $\sigma_{t}^2/\sigma^2 << 1$; except for two structures adjacent to the protocluster, the results seem to deny the importance of the shear and tide from the protocluster. However, the analysis here is actually not entirely appropriate. For a leaf structure, it also bears the tides from other gas structures, not only the protocluster. In fact, it should be N-body tidal interactions; therefore, a complete tidal calculation would be more appropriate.

## Tidal field

![](ref/tide.pdf)

To fully consider the tidal interactions, we directly derived the tidal field according to the density distribution. Only the projected surface density map is available in the observations. To align with other projected physical quantities derived from the observations, we also calculated the 2D projected tide. We note that 3D calculations can refer to (cite: Ganguly2024) and (cite: Li2024-528).

Calculating the gravitational potential field $\phi(x, y)$ based on the surface density map $\Sigma(x, y)$ has been discussed in (cite: Gong2011-729; He2023-526). The tidal tensor described in Appendix.[6](#tide0)

has only two eigenvalues in the case of 2D, that is to say $\lambda_{i}$ (i=1,2). As described in Appendix.[6](#tide0), the tidal tensor of a structure includes both self-gravity and external tides, that is, $\mathbf{T}= \mathbf{T}_{\mathrm{ext}} + \mathbf{T}_{\mathrm{int}}$.

The decomposition of the tidal tensor is discussed in detail in Appendix.[6](#tide0). For three limiting cases, the external tides can be measured by $\lambda_{1}$, $\lambda_{2}$, and $(\lambda_{2}-\lambda_{1})/2$ and they are called T$_{\rm d,1}$, T$_{\rm d,2}$, and T$_{\rm d,3}$, respectively. Fig.[7](#tide) displays different components of the tidal tensor.

## Structure of G332.83-0.55

![](ref/compare.pdf)

As shown in Fig.1 of (cite: Zhou2023-676), G332.83-0.55 is part of a large-scale shell structure. Thus, it may have a sheet structure. In combining Fig.[1](#map)(b) and Fig.[5](#ppv)(a), the single direction gas inflows on large scales also indicate that the structure on large scales should be approximately 2D, and should be face-on. Thus, we can observe the unidirectional converging flows. Close to the center, the structure becomes thicker and thicker. The redshifted and blueshifted components may originate from the forward and backward gas motions in the hub region. However, strong rotation motions on small scales may also explain their origin. The 3D and 2D structures of G332.83-0.55 may not be very different, given its limited thickness. Therefore, 2D-projected tidal field strength should be comparable to those for 3D ones, and equation.[\[Et\]](#Et) derived from the 3D tidal tensor in Appendix.[6](#tide0) should still be effective for a 2D situation, which is confirmed in Fig.[8](#compare)(a).

## Pixel-by-pixel computation

Below we explain how we tested the above tidal tensor analysis using an original method.

### Maximum computation

![](ref/mask.pdf)

![](ref/shift.pdf)

For a structure A, located at a distance $R$ from the center of another structure B, of mass $M$, the tidal strength sustained by structure A due to the external gravity from structure B is $$\begin{equation}
T \approx \frac{2GM}{R^{3}}.
\label{point}
\end{equation}$$

The total tidal strength at a pixel measures the total deformation due to the external tides at that point.

A gas structure is neither a rigid body nor point mass, but it is a parcel of gas with malleability. Most gas structures are also not spherically symmetric, and their morphologies can be highly complex. Although the external gravity from all directions may cancel each other out in a structure, the tides inside the structure due to the external gravity do not. Therefore, we used the scalar superposition to measure the overall tidal strength in the structure from the external gravity. Tidal tearing may be an important cause for the deformation and complex morphology of gas structures, as discussed in Sec.[4.1](#regulate).

Using the mask of the dendrogram structure, we divided the density map into two parts, that is, the structure itself and all other materials apart from this structure. For the external tides from all outside material sustained by a point in structure A, a simple calculation involves using equation.[\[point\]](#point) to directly calculate the tidal strength at that point pixel by pixel, as illustrated in Fig.[9](#mask)(b). The average tidal strength of all the pixels in structure A can then represent the average tidal strength sustained by the structure.

### Minimal computation

As illustrated in Fig.[9](#mask)(b), the above computation is limited to a 2D plane. In equation.[\[point\]](#point), the tidal strength is very sensitive to the distance. If the external structure and the calculated structure are not in the same plane, the 2D calculation underestimates the distance between them and thus overestimates the tidal strength (maximum computation, T$_{\rm max}$). However, we only have the 2D projection in the observation. The 3D structure of the molecular gas is unknown, but we can consider an extreme case. Using the average effective radius ($\sim$0.03 pc) of all leaf structures as the characteristic scale height of G332.83-0.55, all external material apart from the calculated structure was moved vertically to 0.03 pc away, as illustrated in Fig.[10](#shift)(c). This is unrealistic, given the continuity of the matter distribution in a cloud. As a limiting case, the estimated tidal strength should be smaller than the actual value (minimal computation, T$_{\rm min,s}$).

The other minimal computation (T$_{\rm min,v}$) is the vector superposition of tides, which allows the tidal interactions to directly cancel each other out. Using the calculated point in the target structure as the coordinate origin to build a 2D coordinate system, all external tides were decomposed to the coordinate axes. Then we calculated the overall tidal strength at the calculated point after performing vector superposition along each axis.

### Tide from the envelope

As shown in Fig.[2](#flow1), the dendrogram structures are embedded in a larger-scale gas environment. The material outside of the FOV of ALMA observation may also produce considerable external tides (T$_{\rm out}$) on small-scale dendrogram structures. Using the H$_{2}$ column density derived from ATLASGAL+Planck 870 $\mu$m in (cite: Zhou2024-682), the matter in the FOV of ALMA observation was first masked, as shown in Fig.[9](#mask)(a). Then we calculated the external tides at each pixel in the FOV. The averaged tidal strength of all pixels is $\sim$1.4 $\times 10^{-25}$ s$^{-2}$. Compared with the tidal strength in Fig.[8](#compare)(b), T$_{\rm out}$ is very small and therefore can be ignored.

### Comparison

Fig.[8](#compare)(b) shows that the components T$_{\rm d,1}$, T$_{\rm d,2}$, and T$_{\rm d,3}$ (whose derivation is detailed in Appendix.[6](#tide0)) are comparable.

Especially, they are also comparable with T$_{\rm min,s}$ and T$_{\rm min,v}$. As expected, T$_{\rm max}$ is significantly larger than others. For T$_{\rm d,1}$, T$_{\rm d,2}$, T$_{\rm d,3}$, T$_{\rm min,s}$, and T$_{\rm min,v}$, T$_{\rm min,v}$ is slightly larger than others and the value of T$_{\rm min,s}$ is in the middle. As a compromise, we use the value of T$_{\rm min,s}$ to represent the external tides in the subsequent analysis.

# Discussion

## Tide-regulated gravitational collapse

![](ref/energy.pdf)

The average strength of the external tides T$_{\rm min,s}$ of a structure was used to measure the deformation of the structure due to the external gravity.

The effective velocity dispersion from the external tides of the structure is $\sigma_{t}^{2} \approx
T_{\rm min,s}*R^2$, and the corresponding energy $$\begin{equation}
E_{\rm t} \approx \frac{1}{2}
M *T_{\rm min,s}*R^2.
\label{tide}
\end{equation}$$ The gravitational potential energy $E_{\rm g}$ and internal kinetic energy $E_{\rm k}$ were calculated in the same way as presented in (cite: Zhou2024-682).

The slowing down of a pure free-fall gravitational collapse as revealed by the shallow $\sigma_{\rm s}-N*R$ relation means that there are some physical processes working against gravitational collapse, such as tidal tearing from external gravity. The effect of the external tides on the gravitational collapse of gas structures can also be reflected in the scaling relation. After adding the contribution of the tidal interactions to the observed velocity dispersion, the effective velocity dispersion $\sigma_{\rm s}=\sqrt{\sigma_{\rm t}^{2}+\sigma^{2}}$, then the $\sigma_{\rm s}-N*R$ relation was fitted again. As shown in Fig.[6](#scaling)(d), now the slope is close to 0.5, and the correlation also gets stronger. Thus, the deformation due to the external tides may effectively slow down the pure free-fall gravitational collapse of gas structures.

However, as shown in Fig.[11](#energy)(a), the sum of E$_{\rm k}$ and E$_{\rm t}$ is notably larger than E$_{\rm g}$. The external tidal strength may be overestimated.

The velocity dispersion is a manifestation of gas perturbations due to many physical processes, including gravitation collapse, tidal tearing, and turbulence. Thus, E$_{\rm k}$ should be overestimated. Moreover, when $E_{\rm k}+E_{\rm t}>E_{\rm g}$, it does not mean that the structure cannot be gravitationally bound. A structure is deformed by external tides from the surrounding material, and at the same time, the surrounding material also provides the structure with a confining pressure.

Previous studies have suggested that the external pressure provided by the larger-scale molecular gas might help to confine dense structures in molecular clouds (cite: Spitzer1978; McKee1989-345; Elmegreen1989-338; Ballesteros2006-372; Kirk2006-646; Dib2007-661; Lada2008-672; Pattle2015-450; Kirk2017-846; Li2020-896; Zhou2024-682). External pressure can have various origins; here we mainly consider the external pressure from the ambient cloud for each decomposed structure using $$\begin{equation}
\label{evirp}
P_{\rm cl} = \pi G \bar{\Sigma}\Sigma_{r},
\end{equation}$$ where $P_{\rm cl}$ is the gas pressure, $\bar{\Sigma}$ is the mean surface density of the cloud, and $\Sigma_{\rm r}$ is the surface density at the location of each structure (cite: McKee1989-345; Kirk2017-846). The external pressure energy can be calculated as $$\begin{equation}
\label{ep}
E_{\rm p} = -4\pi P_{\rm cl} R^{3}.
\end{equation}$$ As shown in Fig.[11](#energy)(b), after considering the external pressure, $E_{\rm k}+E_{\rm t}<E_{\rm g}+E_{\rm p}$. The external tide tries to tear up the structure, but the external pressure on the structure prevents this process from occurring. The counterbalance between the external tide and external pressure hinders the gravitational collapse of the structure, which can also cause a pure free-fall gravitational collapse to slow down.

Gravity can play multiple roles in cloud evolution. Inside dense regions, it drives fragmentation and collapse, and outside these regions, it can suppress the low-density gas from collapsing through extensive tidal forces and drive accretion (cite: Li2024-528). This work confirms that tidal interactions can significantly influence the dynamics and kinematics of gas structures and regulate their gravitational collapse. In Fig.14(c) and Fig.15(c) of (cite: Zhou2024-682), in the G333 complex, for 3608 gas structures on cloud-clump scales, the slopes of the $\sigma-N*R$ relations are $\sim$0.19 and $\sim$0.26, respectively. In the Fig.5(a) of (cite: Zhou2024-682-173), for 2420 dense gas structures on clump-core scales in 64 ATOMS sources (clumps) at different evolutionary stages, the slope of the $\sigma-N*R$ relation is $\sim$0.27. According to the above analysis, these shallow slopes (significantly smaller than 0.5) may indicate extensive tide-regulated gravitational collapse from cloud to core scales, which will be discussed in detail in future work.

## Gravitational focusing

In Fig.[4](#pv)(b) and Fig.[5](#ppv)(b), on large scales, the funnel structure is consistent with the schematic diagram in Fig.9 of (cite: Zhou2023-676). However, it looks as though the bottom of the funnel splits into two parts in Fig.[4](#pv)(b) and Fig.[5](#ppv)(b). A velocity jump appears in the center comprised of the redshifted and blueshifted components, which may be attributed to the infalling and rotating motions around the protocluster. If we turn over the redshifted component and let it merge with the blueshifted component, then we obtain the funnel structure in Fig.9 of (cite: Zhou2023-676).

Similar to lights converging to the focus, now the gas inflows are converging to the gravitational center, that is, the hub region of G332.83-0.55. Thus, there is a vivid "gravitational focusing" process, which also provides a clue as to the formation of the hub-filament structure. As shown in the Fig.1 of (cite: Zhou2023-676), the entire G333 complex has a large-scale shell structure. G332.83-0.55 is a fragment on the shell, which should have a sheet configuration initially; for more details, readers can also refer to Sec.[3.6](#sheet). Then the subsequent gravitational focusing process yields the hub-filament structure. In Fig.[1](#map)(b), the hub-filament structure is decoupling from the surrounding gas environment due to gravitational collapse.

# Summary

1\. In high-resolution APEX/LAsMA $^{12}$CO and $^{13}$CO (3-2) observations, G332.83-0.55 has a clear hub-filament morphology at $\sim$10 pc, and its hub corresponds to the ATLASGAL clump AGAL332.826-00.549. We zoomed in on the hub region of G332.83-0.55 using higher-resolution ALMA HCO$^{+}$ (1-0) and H$^{13}$CO$^{+}$ (1-0) observations, and found that it still presents a hub-filament structure. Thus, G332.83-0.55 contains at least two levels of hub-filament structures. High-resolution single-dish and ALMA observations provide the opportunity to trace gas inflows from cloud to core scales.

2\. G332.83-0.5 is collapsing with rotation. Around the gravitational center (i.e., the protocluster), both the velocity fields traced by LAsMA and ALMA observations show velocity jumps comprised of redshifted and blueshifted peaks. According to the velocity difference and the separation between blueshifted and redshifted peaks, we roughly estimated the rotation velocity $V_{\rm rotation,ALMA} \approx$3.29 km/s and the centrifugal barrier $r_{\rm c, ALMA} \approx$ 0.21 pc. Then the mass of the gravitational center (i.e., the protocluster) was estimated to be $\approx$264 M$_{\odot}$, which agrees with the mass estimated by 3mm dust emission.

3\. We directly identified local dense gas structures based on the 2D integrated intensity (Moment 0) map of H$^{13}$CO$^+$ J=1-0 emission using the dendrogram algorithm, and then extracted the average spectra to fit the velocity dispersion. The slope of the $\sigma-N*R$ relation for leaf structures is $\sim$0.2, which is much smaller than 0.5 of the pure free-fall gravitational collapse. This may indicate that a pure free-fall gravitational collapse is slowing down.

4\. We investigated the effect of shear and tides from the protocluster on the surrounding local dense gas structures. The results seem to deny the importance of shear and tides from the protocluster. However, for a gas structure, it also bears the tides from other gas structures and the general gas distribution, not only the protocluster. To fully consider the tidal interactions, we derived the tide field according to the density distribution, and then used the average strength of the external tides of a structure to measure the total tidal interactions on the structure. For comparison, we also adopted an original pixel-by-pixel computation to estimate the average tidal strength of each structure. Both methods give comparable calculation results.

5\. After considering the tidal interactions for all structures, the slope of the $\sigma-N*R$ relation is close to 0.5, and the correlation also gets stronger. Thus, the deformation due to the external tides can effectively slow down the pure free-fall gravitational collapse of gas structures. The external tide tries to tear up the structure, but the external pressure on the structure prevents this process from occurring. The counterbalance between an external tide and external pressure hinders the free-fall gravitational collapse of the structure, which can also cause a pure free-fall gravitational collapse to slow down. These mechanisms can be called "tide-regulated gravitational collapse."

# Acknowledgements

This publication is based on data acquired with the Atacama Pathfinder Experiment (APEX) under programme ID M-0109.F-9514A-2022. APEX has been a collaboration between the Max-Planck-Institut für Radioastronomie, the European Southern Observatory, and the Onsala Space Observatory. This research made use of astrodendro, a Python package to compute dendrograms of Astronomical data (http://www.dendrograms.org/). This paper makes use of the following ALMA data: ADS/JAO.ALMA$\sharp$2019.1.00685.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO,

64 natexlab

(ref: Ballesteros2006-372) Ballesteros-Paredes, J. 2006, MNRAS, 372, 443

(ref: Chen2020-4) Chen, X., Sobolev, A. M., Ren, Z.-Y., et al. 2020, Nature Astronomy, 4, 1170

(ref: Contreras2016-456) Contreras, Y., Garay, G., Rathborne, J. M., & Sanhueza, P. 2016, MNRAS, 456, 2041

(ref: Csengeri2016-585) Csengeri, T., Weiss, A., Wyrowski, F., et al. 2016, A&A, 585, A104

(ref: Dewangan2020) Dewangan, L. K., Ojha, D. K., Sharma, S., et al. 2020, ApJ, 903, 13

(ref: Dib2012-758) Dib, S., Helou, G., Moore, T. J. T., Urquhart, J. S., & Dariush, A. 2012, ApJ, 758, 125

(ref: Dib2007-661) Dib, S., Kim, J., Vázquez-Semadeni, E., Burkert, A., & Shadmehri, M. 2007, ApJ, 661, 262

(ref: Elmegreen1989-338) Elmegreen, B. G. 1989, ApJ, 338, 178

(ref: Ganguly2024) Ganguly, S., Walch, S., Clarke, S. D., & Seifried, D. 2024, MNRAS \[\]

(ref: Gong2011-729) Gong, H. & Ostriker, E. C. 2011, ApJ, 729, 120

(ref: He2023-526) He, Z.-Z., Li, G.-X., & Burkert, A. 2023, MNRAS, 526, L20

(ref: Henshaw2014) Henshaw, J. D., Caselli, P., Fontani, F., Jiménez-Serra, I., & Tan, J. C. 2014, MNRAS, 440, 2860

(ref: Hunter1998-493) Hunter, D. A., Elmegreen, B. G., & Baker, A. L. 1998, ApJ, 493, 595

(ref: Issac2019) Issac, N., Tej, A., Liu, T., et al. 2019, MNRAS, 485, 1775

(ref: Izquierdo2018-478) Izquierdo, A. F., Galván-Madrid, R., Maud, L. T., et al. 2018, MNRAS, 478, 2505

(ref: Kauffmann2008) Kauffmann, J., Bertoldi, F., Bourke, T. L., Evans, N. J., I., & Lee, C. W. 2008, A&A, 487, 993

(ref: Keto2008-672) Keto, E., Zhang, Q., & Kurtz, S. 2008, ApJ, 672, 423

(ref: Kirk2017-846) Kirk, H., Friesen, R. K., Pineda, J. E., et al. 2017, ApJ, 846, 144

(ref: Kirk2006-646) Kirk, H., Johnstone, D., & Di Francesco, J. 2006, ApJ, 646, 1009

(ref: Koch2015) Koch, E. W. & Rosolowsky, E. W. 2015, MNRAS, 452, 3435

(ref: Kumar2020-642) Kumar, M. S. N., Palmeirim, P., Arzoumanian, D., & Inutsuka, S. I. 2020, A&A, 642, A87

(ref: Lada2008-672) Lada, C. J., Muench, A. A., Rathborne, J., Alves, J. F., & Lombardi, M. 2008, ApJ, 672, 410

(ref: Li2024-528) Li, G.-X. 2024, MNRAS, 528, L52

(ref: Li2020-896) Li, S., Zhang, Q., Liu, H. B., et al. 2020, ApJ, 896, 110

(ref: Lindner2015-149) Lindner, R. R., Vera-Ciro, C., Murray, C. E., et al. 2015, AJ, 149, 138

(ref: Liu2015-804) Liu, H. B., Galván-Madrid, R., Jiménez-Serra, I., et al. 2015, ApJ, 804, 37

(ref: Liuh2021) Liu, H.-L., Liu, T., Evans, Neal J., I., et al. 2021a, MNRAS, 505, 2801

(ref: Liu2022-511) Liu, H.-L., Tej, A., Liu, T., et al. 2022, MNRAS, 511, 4480

(ref: Liu2023-522) Liu, H.-L., Tej, A., Liu, T., et al. 2023, MNRAS, 522, 3719

(ref: Liu2020-904) Liu, S.-Y., Su, Y.-N., Zinchenko, I., et al. 2020a, ApJ, 904, 181

(ref: Liu2020) Liu, T., Evans, N. J., Kim, K.-T., et al. 2020b, MNRAS, 496, 2790

(ref: Liu2016) Liu, T., Zhang, Q., Kim, K.-T., et al. 2016, ApJ, 824, 31

(ref: Liu2021-646) Liu, X.-L., Xu, J.-L., Wang, J.-J., et al. 2021b, A&A, 646, A137

(ref: Lu2018) Lu, X., Zhang, Q., Liu, H. B., et al. 2018, ApJ, 855, 9

(ref: Maud2017-467) Maud, L. T., Hoare, M. G., Galván-Madrid, R., et al. 2017, MNRAS, 467, L120

(ref: McKee1989-345) McKee, C. F. 1989, ApJ, 345, 782

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Motte2018-56) Motte, F., Bontemps, S., & Louvet, F. 2018, ARA&A, 56, 41

(ref: Myers2009) Myers, P. C. 2009, ApJ, 700, 1609

(ref: Ohashi1997-475) Ohashi, N., Hayashi, M., Ho, P. T. P., & Momose, M. 1997, ApJ, 475, 211

(ref: Olguin2023-959) Olguin, F. A., Sanhueza, P., Chen, H.-R. V., et al. 2023, ApJL, 959, L31

(ref: Pattle2015-450) Pattle, K., Ward-Thompson, D., Kirk, J. M., et al. 2015, MNRAS, 450, 1094

(ref: Peretto2013) Peretto, N., Fuller, G. A., Duarte-Cabral, A., et al. 2013, A&A, 555, A112

(ref: Riener2019-628) Riener, M., Kainulainen, J., Henshaw, J. D., et al. 2019, A&A, 628, A78

(ref: Sakai2014-507) Sakai, N., Sakai, T., Hirota, T., et al. 2014, Nature, 507, 78

(ref: Sanhueza2021-915) Sanhueza, P., Girart, J. M., Padovani, M., et al. 2021, ApJL, 915, L10

(ref: Sanna2019-623) Sanna, A., Kölligan, A., Moscadelli, L., et al. 2019, A&A, 623, A77

(ref: Schneider2012) Schneider, N., Csengeri, T., Hennemann, M., et al. 2012, A&A, 540, L11

(ref: Shimoikura2022-928) Shimoikura, T., Dobashi, K., Hirano, N., et al. 2022, ApJ, 928, 76

(ref: Shimoikura2016-832) Shimoikura, T., Dobashi, K., Matsumoto, T., & Nakamura, F. 2016, ApJ, 832, 205

(ref: Shimoikura2018-855) Shimoikura, T., Dobashi, K., Nakamura, F., Matsumoto, T., & Hirota, T. 2018, ApJ, 855, 45

(ref: Spitzer1978) Spitzer, L. 1978, Physical processes in the interstellar medium

(ref: Stark1978-225) Stark, A. A. & Blitz, L. 1978, ApJL, 225, L15

(ref: Vazquez2019-490) Vázquez-Semadeni, E., Palau, A., Ballesteros-Paredes, J., Gómez, G. C., & Zamora-Avilés, M. 2019, MNRAS, 490, 3061

(ref: Xu2023arXiv) Xu, F.-W., Wang, K., Liu, T., et al. 2023, arXiv e-prints, arXiv:2301.01895

(ref: Yang2023-953) Yang, D., Liu, H.-L., Tej, A., et al. 2023, ApJ, 953, 40

(ref: Yuan2018) Yuan, J., Li, J.-Z., Wu, Y., et al. 2018, ApJ, 852, 12

(ref: Zhang2023-520) Zhang, C., Zhu, F.-Y., Liu, T., et al. 2023, MNRAS, 520, 3245

(ref: Zhang2015) Zhang, Q., Wang, K., Lu, X., & Jiménez-Serra, I. 2015, ApJ, 804, 141

(ref: Zhou2024-682-173) Zhou, J. W., Dib, S., Wyrowski, F., et al. 2024a, A&A, 682, A173

(ref: Zhou2022-514) Zhou, J.-W., Liu, T., Evans, N. J., et al. 2022, MNRAS, 514, 6038

(ref: Zhou2021-508) Zhou, J.-W., Liu, T., Li, J.-Z., et al. 2021, MNRAS, 508, 4639

(ref: Zhou2024-682) Zhou, J. W., Wyrowski, F., Neupane, S., et al. 2024b, A&A, 682, A128

(ref: Zhou2023-676) Zhou, J. W., Wyrowski, F., Neupane, S., et al. 2023, A&A, 676, A69

# Tidal tensor

For a gravitational potential field $\Phi$, the tidal tensor $\mathbf{T}$ is defined as $$\begin{equation}
    \mathrm{T}_{ij} = \partial_i \partial_j \Phi.
\end{equation}$$

The eigenvalues of the tidal tensor contain information regarding the extent of deformation (compression and disruption) experienced at a specific point due to the local gravitational field.

The diagonalized tidal tensor is given as $$\begin{gather}
    \mathbf{T}
    =
    \begin{bmatrix}
    \lambda_1 &0&0\\
    0&\lambda_2&0\\
    0&0&\lambda_3
    \end{bmatrix}.
\end{gather}$$

The sign of the eigenvalues ($\lambda_1, \lambda_2,$ and $\lambda_3$) indicates whether the given mode is compressive ($\lambda_i > 0$) or disruptive ($\lambda_i < 0$), while the magnitude represents the strength of the respective compressive and disruptive mode.

The trace of the tidal tensor $\mathrm{Tr(\mathbf{T})}=\sum_{i=1}^{3} \lambda_i$ contains the local density information in the Poisson equation: $$\begin{equation}
    \mathrm{Tr(\mathbf{T})} = \nabla^2 \Phi = 4\pi G \rho.
    \label{trace}
\end{equation}$$

This indicates that the trace is zero when the location where the tidal tensor is assessed lies outside the distribution of mass.

As was done in (cite: Ganguly2024), the tidal tensor can be split into three parts: the tidal tensor due to only the matter inside the structure, $\mathbf{T}_{\mathrm{int}}$, and into a second component due only to the matter distribution external to the structure, $\mathbf{T}_{\mathrm{ext}}$. Their sum, due to the entire matter distribution, $$\begin{equation}
\mathbf{T} =\mathbf{T}_{\mathrm{int}}+\mathbf{T}_{\mathrm{ext}}.
\label{3t}
\end{equation}$$ Here, $\mathrm{\mathbf{T}}$ represents the net deformation due to both the structure itself and its surroundings. We note that $\mathrm{\mathbf{T}_{ext}}$ represents the deformation introduced solely due to the external materials. The trace of the three parts are the following: $$\begin{gather}
\label{eq:trace1}
    \mathrm{Tr(\mathbf{T})} = 4\pi G \rho_{\mathrm{a}}\\
    \mathrm{Tr(\mathbf{T}_{int})} = 4\pi G \rho_{\mathrm{a}}\\
    \mathrm{Tr(\mathbf{T}_{ext})} = 0,
    \label{trace3}
\end{gather}$$ where $\rho_{\mathrm{a}}$ is the average density of the structure with radius $R$ and total mass $M$, $\rho_{\mathrm{a}}= M/(4/3 \pi R^{3})$.

According to $\mathrm{Tr(\mathbf{T}_{int})} = 4\pi G \rho_{\mathrm{a}}$, the corresponding energy can be estimated by $$\begin{equation}
E_{\rm a,int} \approx \frac{1}{2}
M *\mathrm{Tr(\mathbf{T}_{int})}* R^{2} \approx \frac{GM^{2}}{R}.
\label{Et}
\end{equation}$$ Thus, the tidal tensor $\mathbf{T}_{\mathrm{int}}$ represents the self-gravity of the structure. If we want to estimate the tidal interactions from all external materials on the structure, we should focus on $\mathbf{T}_{\mathrm{ext}}$.

The trace in equation.[\[trace3\]](#trace3) indicates that $\mathrm{\mathbf{T}_{ext}}$ due to only matter distribution external to the structure must contain both compressive and disruptive modes, corresponding to positive and negative $\lambda_i$, respectively. In contrast, $\mathrm{\mathbf{T}_{int}}$ due to only the matter inside the structure and $\mathrm{\mathbf{T}}$ due to the entire matter distribution must contain at least one compressive mode, but it might also be fully compressive. These rules are also applicable for 2D projected tidal tensor. According to equation.[\[3t\]](#3t), the 2D tidal tensor can be decomposed as $$\begin{equation}
\begin{bmatrix}
    \lambda_1 &0\\
    0&\lambda_2
    \end{bmatrix} =  \begin{bmatrix}
    -A_{0} &0\\
    0&A_{0}
    \end{bmatrix} +  \begin{bmatrix}
    A_{1} &0\\
    0&A_{2}
    \end{bmatrix};
\end{equation}$$ assuming $A_{2}=k*A_{1}$, we have $A_{1}=\frac{\lambda_1+\lambda_2}{1+k}$, $A_{2}=\frac{k(\lambda_1+\lambda_2)}{1+k}$, and $A_{0}=\frac{\lambda_1+\lambda_2}{1+k}-\lambda_1$. There are three cases:

\(1\) When $k=1$, $A_{1}=A_{2}=\frac{\lambda_1+\lambda_2}{2}$, $A_{0}=\frac{\lambda_2-\lambda_1}{2}$ (Fig.[7](#tide)(c)).

\(2\) When $k<<1$, $A_{1} \approx \lambda_1+\lambda_2$, $A_{2} \approx 0$, $A_{0} \approx \lambda_2$ (Fig.[7](#tide)(b)).

\(3\) When $k>>1$, $A_{1} \approx 0$, $A_{2} \approx \lambda_1+\lambda_2$, $A_{0} \approx -\lambda_1$ (Fig.[7](#tide)(a)).

We estimated the averaged strength of the external tidal field for each structure according to Fig.[7](#tide)(a), (b) and (c), that is, the averaged value of $|A_{0, a}|$ in each structure. As shown in Fig.[8](#compare)(b), the three cases give similar estimates of the averaged strength of the external tidal field.

</paper>

Write the methods card for this paper.