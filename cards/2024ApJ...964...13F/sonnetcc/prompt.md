# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...964...13F\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...964...13F",
 "title": "ALMA-LEGUS. II. The Influence of Subgalactic Environments on Molecular Cloud Properties",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Finn, Molly K.",
 "n_authors": 27,
 "arxiv_id": "2401.01451",
 "doi": "10.3847/1538-4357/ad198a",
 "alma_projects_linked_by_archive": [
  "2015.1.00782.S"
 ]
}
```

Paper text:
<paper>
# ALMA-LEGUS II: The Influence of Sub-Galactic Environment on Molecular Cloud Properties

## Abstract

We compare the molecular cloud properties in sub-galactic regions of two galaxies, barred spiral NGC 1313, which is forming many massive clusters, and flocculent spiral NGC 7793, which is forming significantly fewer massive clusters despite having a similar star formation rate to NGC 1313. We find that there are larger variations in cloud properties between different regions within each galaxy than there are between the galaxies on a global scale, especially for NGC 1313. There are higher masses, linewidths, pressures, and virial parameters in the arms of NGC 1313 and center of NGC 7793 than in the interarm and outer regions of the galaxies. The massive cluster formation of NGC 1313 may be driven by its greater variation in environments, allowing more clouds with the necessary conditions to arise, although no one parameter seems primarily responsible for the difference in star formation. Meanwhile NGC 7793 has clouds that are as massive and have as much kinetic energy as clouds in the arms of NGC 1313, but have densities and pressures more similar to the interarm regions and so are less inclined to collapse and form stars. The cloud properties in NGC 1313 and NGC 7793 suggest that spiral arms, bars, interarm regions, and flocculent spirals each represent distinct environments with regard to molecular cloud populations. We see surprisingly little difference in surface densities between the regions, suggesting that the differences in surface densities frequently seen between arm and interarm regions of lower-resolution studies are indicative of the sparsity of molecular clouds, rather than differences in their true surface density.

# Introduction

![image](CO_clusteroverlay_1313.png) ![image](CO_clusteroverlay_7793.png)

Spiral galaxies are home to the majority of local star formation (cite: Brinchmann04), and so it is important for us to understand how the environments of different regions within the galaxies and different types of spiral galaxies affect star formation. The molecular gas in bars, spiral arms, interarm regions, and galaxy centers all experience different conditions, which can in turn influence the star formation taking place in each environment.

Much work has been done on understanding how spiral density waves and stellar feedback impact cloud formation, collapse, and dispersal, both from simulations and observations. There have been several surveys to study the molecular gas in nearby spiral galaxies at the scale of giant molecular clouds (GMCs), such as PAWS (PdBI Arcsecond Whirlpool Survey), which mapped M51 in CO(1-0) at 40 pc resolution (cite: Schinnerer13), CANON (CArma and NObeyama Nearby galaxies), which mapped the inner disks of nearby spiral galaxies in CO (1-0) and enabled a focused study of molecular cloud properties using a subsample at 62-78 pc resolution (cite: JDM13), PHANGS-ALMA (Physics at High Angular resolution in Nearby Galaxies), which mapped 90 galaxies in CO(2-1) at $\sim100$ pc resolution (cite: Leroy21), and most recently the barred spiral galaxy M83 was mapped in CO(1-0) at 40 pc resolution (cite: Koda23).

These studies have consistently shown that at $\sim$40-100 pc resolutions, the molecular gas in spiral arms tend to be brighter and have higher surface densities, velocity dispersions, and pressures than gas in the interarm regions, especially when a strong bar is present (cite: Colombo14; Sun18PHANGS; Sun20; Rosolowsky21; Koda23). They have also shown that the slope of the distribution of cloud masses is shallower and truncates at higher masses in the spiral arms than interarm regions (cite: Koda09; Colombo14; Rosolowsky08), but that despite the greater amount of star formation in the arms, the depletion time in the arms is not significantly shorter (cite: Querejeta21). Rather, (cite: Yu21) find that the depletion time of the gas is more closely related to the strength of the spiral arms, with stronger arms being associated with shorter depletion times and higher specific SFR.

These observations are well-modeled by simulations, especially those of grand design spiral galaxies. Simulations also find that the spiral arms are generally the sites of active star formation rather than the interarm regions (cite: Dobbs13), and that GMCs are assembled in the spiral arms and are then sheared into smaller clouds in the interarm regions, resulting in lower mass clouds being found in the interarm regions (cite: DobbsPringle13). Breaking up massive clouds via shear is well-matched to the lifetimes of clouds measured in the interarm region of M51 (cite: Meidt15) and of M83 (cite: Koda23). Massive clouds are expected to be denser and have longer lifetimes, allowing them to form more massive clusters in the spiral arms before they are dispersed (cite: Dobbs11; Dobbs17). (cite: Meidt13) propose that the higher amount of streaming motion in the interarm regions relative to the arms stabilizes the clouds and suppresses collapse.

(cite: Pettitt20) find that the cause of the spiral pattern (e.g. density wave, interaction, or underlying gravitational instability) has no effect on the simulated GMC properties. However, GMCs have a shallower mass distribution with more massive clouds after the galaxy experiences a tidal fly-by, especially in the spiral arms, and many of the clouds become unbound during this process (cite: Pettitt18; Nguyen18).

In flocculent spiral galaxies, the distinction between interarm and arm regions is less robust, but (cite: Dobbs19) still find a difference in the steepness of the cloud mass distribution, where star-forming clouds have a shallower mass distribution than non-star-forming clouds, similar to the difference between arm and interarm regions in grand design galaxies. However, (cite: Dobbs18) find that to simulate a flocculent spiral with a weak spiral structure, the stellar feedback must be higher than in a galaxy with strong spirals.

These differences in cloud properties have important repercussions not just for where in the galaxy stars form, but also what kind of stars and star clusters form. Measurements of the cluster formation efficiency, defined by (cite: Adamo15) as the fraction of stars that form in clusters, indicate that it is correlated with the surface density of the gas (cite: Adamo11; SilvaVilla13; Adamo15; Johnson16; Adamo20).

Furthermore, the maximum mass of star clusters where the mass distribution truncates appears to depend on the SFR surface density of the galaxy (cite: Adamo15; Johnson17; Messa18; Wainer22). A more extreme version of this trend has been seen in starburst environments that form massive super star clusters, such as the Antennae galaxies, where clouds have been measured to have extremely high pressures and surface densities (cite: Johnson15; Sun18PHANGS; Finn2019; Krahm23). The hierarchical clustering of the molecular gas also appears to imprint its structure on the spatial clustering of the star clusters, with implications for the evolution of the star clusters and their potential for dispersal (cite: Grasha17a; Grasha17b; Grasha18; Menon21; Turner22).

In this paper, we build upon the analysis of (cite: Finn23a) (hereafter referred to as Paper 1) to further our understanding of how different galactic environments influence the conditions and outcomes of star formation. We use for comparison two galaxies from the Legacy ExtraGalactic UV Survey (cite: Calzetti15): barred spiral NGC 1313 and flocculent spiral NGC 7793. These galaxies have similar masses (cite: Calzetti15), metallicities (cite: WalshRoy97; Stanghellini15), and star formation rates (cite: Calzetti15). However, in Paper 1 we demonstrate that NGC 1313 hosts significantly more star clusters than NGC 7793 as identified by LEGUS, and especially young, massive clusters, even after correcting for their small difference in star formation rate (see Figure [1](#fig:RGB images)). The similarities of the galaxies, combined with their similar distances (cite: RadburnSmith11; Qing15; Gao16; Sabbi18), makes the pair an excellent laboratory for directly comparing how the molecular gas conditions and galactic structure affect star cluster formation. For a more detailed description of these two galaxies, their properties, and their larger environments, see Paper 1.

In Paper 1, we found surprisingly minimal differences in the cloud properties when comparing the two galaxies as a whole. NGC 1313 had slightly higher surface densities, external pressures, and lower free-fall times than NGC 7793. The clouds in NGC 1313 also had higher kinetic energies per spatial scale when fitting a power-law to a size-linewidth relation, and more clouds were near virial equilibrium than in NGC 7793. However, the clouds with virial parameters near 1 were not any more spatially correlated with the locations of star clusters than the general cloud population in either galaxy.

We expand this previous analysis by considering how the sub-galactic environments affect the molecular cloud populations and how those relate to the cluster formation occurring in those regions. We split NGC 1313 into four regions: the bar, northern arm, southern arm, and interarm. In NGC 7793, the spiral arms are too weak for robust delineations of arm and interarm, so we instead split the galaxy into regions by galactocentric radius. These regions are defined in Section [2](#sec:obs), along with the observations, cloud structures, and their properties we use from Paper 1. In Section [3](#sec: cluster catalogs) we describe the cluster catalogs used from LEGUS. We examine how the size-linewidth relations of clouds in each region in Section [4](#sec:SL plots), and the virialization of those clouds in Section [5](#sec: virial plot). We then compare the distributions of all the different cloud properties and different galactic regions in Section [6](#sec:property comparison). We discuss our results in Section [7](#sec:discussion) and then summarize the primary findings in Section [8](#sec:conclusions).

# Observations

## CO(2-1)

Both galaxies were observed by ALMA (project code 2015.1.00782.S; PI: K. E. Johnson) using Band 6 covering the $^{12}$CO(2-1) line with the 12m array. The details of these observations, the data reduction, and the imaging process are discussed in Paper 1, with the parameters of the final images shown in Table [1](#tab:observations), reproduced from Paper 1. Figure [1](#fig:RGB images) shows the peak intensity maps of these observations, overlaid with the positions of clusters identified by LEGUS.

|          |          |      |       |                   |
|:--------:|:--------:|:----:|:-----:|:-----------------:|
|  Galaxy  |   Beam   | Beam |  rms  |     Velocity      |
|          | (arcsec) | (pc) | \(K\) | Resolution (km/s) |
| NGC 1313 |   0.58   |  13  | 0.15  |       1.33        |
| NGC 7793 |   0.72   |  13  |  0.2  |       1.33        |

: ALMA $^{12}$CO(2-1) Observations

In this study, we use the clumps and dendrogram structures identified in Section 4 of Paper 1 using `quickclump` (cite: Sidorin17) and `astrodendro` (cite: Rosolowsky08), as well as all the properties calculated for these structures in Paper 1 as described in Section 5 and published in the tables of that paper’s Appendix A. These properties include the mass ($M$), radius ($R$), velocity dispersion ($\sigma_v$), virial parameter ($\alpha_\text{vir}$), surface density ($\Sigma$), external pressure ($P_e$), and free-fall time ($t_{ff}$).

Dendrograms are hierarchical and include substructure at many size scales, so are preferred for analyses where including the various size scales of the molecular clouds is useful, such as in a size-linewidth plot. “Leaves” are the smallest of the dendrogram structures, having no substructure of their own. Leaves are bounded by structures called “branches” and “trunks”, where trunks are the largest and are not bounded by any further structures. However, because of this hierarchical nature, dendrograms count emission multiple times, and so cannot be used in any sort of counting statistic, such as examining distributions of properties in a histogram. In these cases, we use clumps instead, which have no overlap and so do not multiply count emission. We use dendrogram structures in Sections [4](#sec:SL plots) and [5](#sec: virial plot) and we use clumps in Section [6](#sec:property comparison).

## Region Selection

In this work, we are interested in how the properties of the two galaxies vary by region within the galaxies. To define these regions, we use contours of the red filter from Digitized Sky Survey (DSS) images of the two galaxies, which traces the bulk of the stellar population. These contours and the defined regions are shown in Figure [2](#fig:galactic regions).

For NGC 1313, we define regions for the bar, the northern arm, and the southern arm, and any structures that fall outside of those regions are considered interarm (Figure [2](#fig:galactic regions)). The bar region is based on the 75% brightness contour in the DSS2-red image, while the arm regions enclose the emission within the 60% contours, then follow the arm pattern out to the edges of the CO(2-1) map following the 40% contour. We separately consider the northern and southern arms.

Since NGC 7793 is a flocculent spiral and does not have clearly defined arms, we instead split the galaxy up into a circular “center” region that follows the 75% brightness contour in the DSS2-red image, and then a “ring” region surrounding the center following the 60% contour (Figure [2](#fig:galactic regions)). The rest of the structures are considered part of the “outer” region.

![image](NGC1313_RegionContours.pdf) ![image](NGC7793_RegionContours.pdf)

+:---------+:---------+:--------:+:--------:+:--------:+:--------:+:------------------:+:-----:+:---------:+:-----------:+:----------:+
|          |          | Molecular Gas Structures                                       | LEGUS Clusters                               |
+----------+----------+----------+----------+----------+----------+--------------------+-------+-----------+-------------+------------+
| Galaxy   | Region   | Trunks   | Branches | Leaves   | Clumps   | Massive Clumps$^a$ | All   | Young$^b$ | Massive$^a$ | YMCs$^a,b$ |
+----------+----------+----------+----------+----------+----------+--------------------+-------+-----------+-------------+------------+
| NGC 1313 | All      | 65       | 82       | 442      | 531      | 137                | 1201  | 618       | 333         | 37         |
+----------+----------+----------+----------+----------+----------+--------------------+-------+-----------+-------------+------------+
|          | Bar      | 7        | 1        | 61       | 69       | 7                  | 380   | 184       | 107         | 8          |
+----------+----------+----------+----------+----------+----------+--------------------+-------+-----------+-------------+------------+
|          | N Arm    | 20       | 32       | 161      | 193      | 62                 | 297   | 243       | 48          | 18         |
+----------+----------+----------+----------+----------+----------+--------------------+-------+-----------+-------------+------------+
|          | S Arm    | 27       | 44       | 156      | 188      | 55                 | 145   | 93        | 32          | 7          |
+----------+----------+----------+----------+----------+----------+--------------------+-------+-----------+-------------+------------+
|          | Interarm | 11       | 5        | 64       | 82       | 13                 | 379   | 98        | 146         | 4          |
+----------+----------+----------+----------+----------+----------+--------------------+-------+-----------+-------------+------------+
| NGC 7793 | All      | 130      | 187      | 761      | 965      | 306                | 467   | 296       | 53          | 3          |
+----------+----------+----------+----------+----------+----------+--------------------+-------+-----------+-------------+------------+
|          | Center   | 22       | 63       | 162      | 203      | 81                 | 57    | 22        | 7           | 0          |
+----------+----------+----------+----------+----------+----------+--------------------+-------+-----------+-------------+------------+
|          | Ring     | 46       | 63       | 277      | 354      | 118                | 108   | 38        | 15          | 2          |
+----------+----------+----------+----------+----------+----------+--------------------+-------+-----------+-------------+------------+
|          | Outer    | 62       | 61       | 322      | 408      | 107                | 302   | 109       | 31          | 1          |
+----------+----------+----------+----------+----------+----------+--------------------+-------+-----------+-------------+------------+

\
Note: $^a$The threshold used to define “massive” for both clumps and clusters in this table is $M>10^4 M_\odot$.\
$^b$ The threshold used to define “young” for clusters is an age $<10$ Myr.

# Cluster Catalogs

As in Paper 1, we use the catalogs of identified star clusters and their SED-fitted masses, ages, and extinctions from the LEGUS collaboration, which follow the methodology of (cite: Adamo17). For NGC 1313 and NGC 7793, we expect the 90% mass completeness limit of these catalogs to be approximately 1000 M$_\odot$ for clusters up to ages of 200 Myr. Further details about the cluster catalogs used in this study can be found in Paper 1.

In Table [\[tab:segmentation\]](#tab:segmentation), we report the number of clusters in each galaxy as well as each of the sub-galactic regions in each galaxy. Also shown are the number of clusters that are massive (\>$10^4$ M$_\odot$), young (\<10 Myr), or both. We also report in this table the numbers of molecular gas structures, and how many clumps are massive (\>$10^4$ M$_\odot$). This table is adapted from Table 3 in Paper 1, which gave these numbers for the galaxies as a whole.

From Table [\[tab:segmentation\]](#tab:segmentation) we see that the molecular clouds and star clusters in NGC 7793 are fairly evenly distributed (since the area of the center, ring, and outer regions are consecutively larger), with only the exception of a slight excess of massive gas clumps in the ring region. In NGC 1313, the molecular clouds are much more abundant in the arms than in the bar or interarm regions, but there are more clusters in the bar and interarm regions than in the arms, especially for massive clusters. However, the region with the most young clusters and young, massive clusters is the northern arm. A similar excess is not seen in the southern arm. This is surprising since we expect the two spiral arms to behave in similar ways, though perhaps not so surprising given that the southern arm is closer to the site of a burst in star formation (cite: Larsen07; SilvaVillaLarsen12).

## Cluster Property Distributions

To further examine how the cluster populations in each sub-galactic region compare, we plot their mass and age distributions using Gaussian kernel density estimations (KDEs) from `scipy` (cite: scipy), and cumulative distribution functions (CDFs). We use both of these depictions since KDEs are more intuitive to interpret, but are subject to binning effects, while CDFs do not rely on binning and so are more robust but less intuitive in understanding the underlying distribution. For figure clarity, we show only the KDEs and not the underlying histograms. For the KDEs in this section and in Section [6](#sec:property comparison), we adopt a scalar estimator bandwidth of 0.5 dex to make comparisons between regions and properties as direct as possible. These distributions are shown in Figures [3](#fig:1313 cluster distributions) and [4](#fig:7793 cluster distributions), and include mass distributions for both the full cluster population as well as for only the young (\<10 Myr) clusters.

In NGC 1313, there are clear, distinct differences in the mass and age distributions of the full cluster populations in these regions. The northern arm has much lower cluster masses than the other regions, but also is most heavily skewed towards young clusters. Meanwhile, the interarm region is more dominated by high-mass, older clusters. The southern arm and the bar have a fairly similar mass distribution, though the bar tends to have older clusters than the southern arm. When considering only the young clusters, the differences in the mass distributions between regions is much smaller be eye, to the point of appearing negligible.

![image](hist_CLmass_1313.pdf) ![image](CDF_CLmass_1313.png) ![image](hist_cmass_1313_youngonly.png) ![image](CDF_cmass_1313_youngonly.png) ![image](hist_age_1313.pdf) ![image](CDF_age_1313.png)

In NGC 7793, the center region has a bump at high masses ($\sim10^{6.5}$ M$_\odot$), but the CDF appears to show that all three regions have nearly identical mass distributions. These two supermassive clusters in the center of NGC 7793 are relatively old, with fitted ages of 0.9 and 12 Gyr. We consequently we deem them largely irrelevant to this current study and will disregard them for the remainder of this work. When considering only the young clusters, the center region instead has the steepest mass distribution, while the outer region has the most clusters at high masses. The age distributions between the regions are also quite similar. Overall, this suggests that the properties of the cluster population in NGC 7793 are fairly uniform throughout the galaxy.

![image](hist_CLmass_7793.pdf) ![image](CDF_CLmass_7793.png) ![image](hist_cmass_7793_youngonly.png) ![image](CDF_cmass_7793_youngonly.png) ![image](hist_age_7793.pdf) ![image](CDF_age_7793.png)

# Size-Linewidth Relations

To compare the molecular cloud properties in the regions of these two galaxies, we first look at their size-linewidth relations (cite: Larson81). We fit power laws to the dendrogram structures in each region of the form

$$\begin{equation}
    \sigma_v = a_0 R^{a_1}.
\end{equation}$$

The fitted slope ($a_1$) of this relation has been measured in many environments and can vary largely based on the resolution, the molecular tracer, or the methods used to measure sizes and linewidths (cite: Solomon87; Rice16; MivilleDeschenes17; Faesi16; Bolatto08; MAGMA; Nayak16; Indebetouw20; Wong22; Finn22). These slopes are also often poorly constrained and difficult to compare. We therefore focus primarily only on comparisons between regions in this study only, and we fit only the intercept of this power law relation, holding the slope constant at a value of $a_1=0.5$. This fitted intercept indicates the relative amount of kinetic energy in clouds of a given size scale between regions. The assumed value of the fixed slope affects the value of the fitted intercept, but not the conclusions about the relative kinetic energy in the regions.

In Paper 1, we fit intercepts of $a_0=0.41\pm0.01$ in NGC 1313, and $a_0=0.33\pm0.01$ for NGC 7793, indicating that the molecular clouds in NGC 1313 have significantly higher kinetic energies than those in NGC 7793. The size-linewidth relations for each of the regions in the two galaxies are shown in Figure [5](#fig:SL regions) and the fitted values for each region and the galaxies as a whole are reported in Table [2](#tab:size linewidth fits).

![](SL_intercept_1313.png)

![](SL_intercept_7793.png)

The regions of NGC 1313 show a spread of kinetic energies, with the southern arm having the highest intercept, followed by the northern arm, the bar, then the interarm regions. The fitted intercept for the southern arm is significantly higher than the intercepts for the bar and the interarm region, though is just barely consistent within $3\sigma$ with the northern arm. Similarly, the northern arm is significantly higher than the interarm region but consistent within $3\sigma$ with the bar. The bar and interarm regions are consistent with each other as well. These fitted intercepts suggest that the spiral arms of NGC 1313 have higher kinetic energy than the gas in the bar and interarm regions.

In NGC 7793, the intercepts have a much smaller range than in NGC 1313, and all are consistent with each other within $3\sigma$. The center of NGC 7793 is most similar in intercept to the northern arm of NGC 1313, while the outer region is most similar to the bar.

| Galaxy   | Region   | Intercept, $a_0$ |
|:---------|:---------|:----------------:|
| NGC 1313 | Global   |  0.41$\pm$0.01   |
|          | Bar      |  0.32$\pm$0.02   |
|          | N Arm    |  0.40$\pm$0.01   |
|          | S Arm    |  0.49$\pm$0.02   |
|          | Interarm |  0.27$\pm$0.01   |
| NGC 7793 | Global   |  0.33$\pm$0.01   |
|          | Center   |  0.38$\pm$0.01   |
|          | Ring     |  0.33$\pm$0.01   |
|          | Outer    |  0.32$\pm$0.01   |

: Fitted intercepts for size-linewidth relations with fixed slope of $a_1=0.5$

\
Note: Global fitted intercepts from Paper 1.

# Virialization

We next compare the balance between gravitational and kinetic energy in the clouds of the different regions by plotting their velocity metrics, $\sigma_v^2/R$, against their surface densities, $\Sigma$ (Figure [6](#fig:virial regions)). The line of virial equilibrium is shown as a dashed line, where gravity is balanced by kinetic energy. Above this line, clouds would be super-virial and dominated by kinetic energy, and below this line clouds are sub-virial and likely to collapse due to gravity dominating. Clouds can appear super-virial for many reasons, including the possibility that they are unbound and will disperse, that they are bounded by an external pressure, or that they are in free-fall, in which case they would fall along the dotted free-fall line where $\alpha_\text{vir}$=2. In Figure [6](#fig:virial regions), the distribution of clouds in each region are depicted with contours of the two-dimensional KDEs showing 20% and 50% of the maximum density.

![image](VirialPlot_1313.pdf) ![image](VirialPlot_7793.pdf)

In NGC 1313, all of the regions show a dip towards the virial equilibrium line, though the biggest populations close to virial equilibrium are in the bar and the interarm regions, where the 50% density contours also show that dip. The southern arm appears to extend higher in the plot, suggesting that more of its clouds are either unbound or would require an external pressure to remain bound compared to the other regions. It seems likely that this is related to the interaction history of NGC 1313 in the southwest since simulations show interaction causing clouds to become unbound (cite: Pettitt18; Nguyen18). Interestingly, the bar of NGC 1313 does not have more clouds in the unbound or pressure-bound region of the plot than other regions despite containing the galactic center of NGC 1313 and the fact that many other galactic centers exhibit high external pressures (cite: JDM13; Colombo14; Kauffmann17; Walker18; Sun18PHANGS). This is especially pronounced in the findings of (cite: Sun20) that velocity dispersions and external pressures are most enhanced in the centers of barred galaxies.

In NGC 7793, the three regions once again appear more uniform than in NGC 1313, although the center region does extend higher in the plots, suggesting that it has more clouds that are unbound or require external pressure than the ring and outer regions as we would expect for a galactic center. The ring and outer regions appear very similar, suggesting there is little variation in the virialization of clouds outside of the galaxy center. None of the regions of NGC 7793 however show a dip towards virial equilibrium like that seen in every region of NGC 1313, except for slightly in the ring region.

# Property Distribution Comparisons

## NGC 1313 Region Comparisons

We next compare the distribution of cloud properties within the bar, northern arm, southern arm, and interarm regions of NGC 131 by looking at KDEs and CDFs of the non-overlapping clump structures. The distributions of the global NGC 1313 and NGC 7793 cloud population from Paper 1 are shown as well for comparison. The observed mass, radius, and linewidth distributions are shown in Figure [7](#fig:1313 distributions observed), and the properties derived from them are shown in Figure [8](#fig:1313 distributions derived). For figure clarity, we show only the KDEs and not the underlying histograms.

There is a large difference in the mass distributions, with the spiral arms having significantly more massive clouds than the bar or interarm regions. The northern arm also appears to have slightly higher masses than the southern arm. These regional mass distribution differences agree with previous results that spiral arms truncate at higher masses than clouds in the interarm regions, seen in both observations (cite: Koda09; Colombo14; Rosolowsky21) and simulations (cite: Pettitt18; Nguyen18; Dobbs19). The differences between cloud size distributions are minimal, though the bar region appears to have slightly fewer clouds with large radii. The spiral arms have similar linewidth distributions and are higher than the other two regions, where the interarm region has the smallest linewidths, again matching previous results (cite: Colombo14; Sun20; Rosolowsky21; Koda23).

![image](hist_mass_1313.pdf) ![image](CDF_mass_1313.png) ![image](hist_R_1313.pdf) ![image](CDF_R_1313.png) ![image](hist_sigv_1313.pdf) ![image](CDF_sigv_1313.png)

Despite the large difference in mass distributions, the properties derived from the mass, radius, and linewidth do not show strong distinctions between regions. Most notably, the interarm and bar regions appears to have the lowest virial parameters, surface densities, and external pressures. The southern arm also appears to have slightly higher surface densities and pressures compared to the northern arm and other regions.

It is particularly surprising that we see so little difference in surface densities between arm and interarm regions, since that has often been a notable difference in other studies (cite: Colombo14; Sun20; Rosolowsky21; Koda23). We also note that the clouds in the bar of NGC 1313 mostly have less extreme properties than the arms, whereas other studies have often seen enhancements of the velocity dispersion, surface density, and pressure in bars and galactic centers (cite: Sun20; Rosolowsky21; Ali23). This may not be so surprising since (cite: Querejeta21) report large variations in the properties of molecular gas in bars, potentially because star formation in bars is episodic.

![image](hist_alphavir_1313.pdf) ![image](CDF_alphavir_1313.png) ![image](hist_surfdens_1313.pdf) ![image](CDF_surfdens_1313.png) ![image](hist_Pe_1313.pdf) ![image](CDF_Pe_1313.png) ![image](hist_tff_1313.pdf) ![image](CDF_tff_1313.png)

As in Paper 1, we also quantify these differences in property distributions using bootstrapped two-sample Kolmogorov-Smirnoff (KS) tests and Anderson-Darling (AD) tests. Using the full sample size of the galaxies results in an overpowered statistic as described in (cite: Lazariv18), where the tests detect every small variation in the distribution, even those that are well below the measurement errors. Since these overpowered tests are unreliable, we instead perform a bootstrapped version, taking 1000 random subsamples and reporting the average $p$-value of the tests performed on the subsamples. We choose a sample size of 65 because we are limited by the the number of clumps identified in the bar of NGC 1313. We perform these bootstrapped tests for every property and for every combination of sub-galactic region in both galaxies and plot the results in Appendix [9](#append: KS AD plots).

Looking at the bootstrapped KS and AD tests for pairings of the regions in NGC 1313, we find that none of the derived properties have statistically significant differences ($p$-values\<0.05) in their distributions between regions for both KS and AD tests except for the southern arm having significantly higher pressure than the bar and interarm regions. There are, however, statistically significant differences in their mass and linewidth distributions. The absolute value of these test results are highly subject to the size of the subsamples used in the bootstrapping, and so we do not take these as indications of whether or not the distributions are actually different, but rather that some properties are more likely to be different than others.

## NGC 7793 Region Comparisons

We next examine the distribution of cloud properties within the center, ring, and outer regions of NGC 7793. The observed mass, radius, and linewidth distributions are shown in Figure [9](#fig:7793 distributions observed), and the properties derived from them are shown in Figure [10](#fig:7793 distributions derived).

The distributions in NGC 7793 vary from the center of the galaxy to the outer region, with the center having more extreme properties, such as higher masses, higher linewidths, higher virial parameters, and higher external pressures. This generally matches what was found in other surveys for the centers of galaxies (cite: JDM13; Colombo14; Sun20; Koda23). There is not as much difference, however, in the distributions of radii, surface densities, or free-fall times. In most cases, the ring and outer regions have very similar distributions, while the center deviates more.

![image](hist_mass_7793.pdf) ![image](CDF_mass_7793.png) ![image](hist_R_7793.pdf) ![image](CDF_R_7793.png) ![image](hist_sigv_7793.pdf) ![image](CDF_sigv_7793.png)

![image](hist_alphavir_7793.pdf) ![image](CDF_alphavir_7793.png) ![image](hist_surfdens_7793.pdf) ![image](CDF_surfdens_7793.png) ![image](hist_Pe_7793.pdf) ![image](CDF_Pe_7793.png) ![image](hist_tff_7793.pdf) ![image](CDF_tff_7793.png)

These similarities and differences appear as well in comparisons of the bootstrapped KS and AD tests shown in Appendix [9](#append: KS AD plots). None of the cloud or cluster properties, either observed or derived, have statistically significant differences ($p$-values\<0.05) in their distributions among the regions of NGC 7793 for both KS and AD tests. The only exception is the center region having significantly higher linewidths than the outer region based on the AD test. Again, the absolute value of these test results are highly subject to the size of the subsamples used in the bootstrapping, so we do not take these results to indicate whether or not the distributions are actually different, but rather that some properties are more likely to be different than others.

## Inter-Galaxy Region Comparisons

Based on the regional distributions of NGC 1313 shown in Figures [7](#fig:1313 distributions observed) and [8](#fig:1313 distributions derived), none of the regions of NGC 1313 have similar property distributions to the global distributions of NGC 7793 clouds across all properties. The northern arm has the most similar mass distribution and $\alpha_\text{vir}$ distribution to NGC 7793, but the interarm region has the most similar surface density distribution, and in other property distributions, such as external pressure and free-fall time, no NGC 1313 region is similar to the clouds in NGC 7793. This suggests that the environment of a flocculent spiral like NGC 7793 is quite different from both clearly defined arms and their interarm regions. Most notably, every region of NGC 1313 contains, on average, clouds with higher surface densities and shorter free-fall times than NGC 7793.

This differences between the galaxies’ regions is seen again in Figures [9](#fig:7793 distributions observed) and [10](#fig:7793 distributions derived), which show that none of the regions of NGC 7793 have similar virial parameters, surface densities, external pressures, or free-fall times to the global distributions of NGC 1313. The ring region of NGC 7793 appears to have the most similar mass, radius, and linewidth distributions to the global distribution of NGC 1313.

Considering the comparisons of the bootstrapped KS and AD tests in Appendix [9](#append: KS AD plots), some of the most significant differences among all the pairings for both tests are between the central region of NGC 7793 and the bar and interarm regions of NGC 1313, for almost every property, with the notable exception of surface density and free-fall time. This is somewhat surprising since the bar of NGC 1313 encompasses that galaxy’s own central region and galaxy centers usually have more extreme cloud properties (cite: JDM13; Colombo14; Sun20; Koda23; Ali23). One other notable difference from the KS and AD tests is that the southern arm of NGC 1313 has statistically significant lower free-fall times than all regions of NGC 7793. This is not true for the northern arm. Since the absolute value of resulting $p$-values of these bootstrapped tests are so easily influenced by subsample size, we do not take these results to indicate whether or not the distributions are actually statistically different, but rather to indicate which property distributions are most likely to be different.

# Discussion

In Table [\[tab:comparisons\]](#tab:comparisons), we briefly outline the differences in each property between the two galaxies as discussed in Paper 1 and among the regions within each galaxy. There does not appear to be any singular property that has an out-sized influence on the star formation of either galaxy or galactic region.

| Property | Global Difference | NGC 1313 Regional | NGC 7793 Regional |
|:--:|:--:|:--:|:--:|
| Cluster mass distribution | NGC 1313 more massive | Interarm most and N arm least massive | No difference |
| Young Cluster mass distribution | NGC 1313 more massive | No difference | Outer most massive |
| Cluster age distribution | NGC 1313 older | Interarm older, N arm youngest | No difference |
| Size-Linewidth intercept | No difference | S arm higher, interarm lower | Center higher |
| Virialization plot | NGC 1313 closer to virial | Bar and interarm closer to virial | Center further from virial |
| Cloud Mass distribution | No difference | Arms more massive | Center more massive |
| Radius distribution | NGC 7793 larger | No difference | No difference |
| Linewidth distribution | No difference | Arms higher | Center higher |
| Virial parameter distribution | NGC 1313 lower | Interarm lower | Center higher |
| Surface density distributions | NGC 1313 higher | S arm higher, interarm lowest | No difference |
| External pressure distribution | NGC 1313 higher | S arm higher, interarm lowest | Center higher |
| Free-fall time distribution | NGC 1313 lower | No difference | No difference |

While the differences in the cloud properties between the two galaxies as seen in Paper 1 are surprisingly small, there is much greater variation between regions within the galaxy, especially within NGC 1313. This suggests that the local environment has a much stronger influence on cloud properties than the global galaxy environment. This was also seen when comparing regional variations and galaxy-to-galaxy variations in the PHANGS sample at 100 pc resolution (cite: Sun22).

Comparing the regional variations within the two galaxies, NGC 7793 appears much more uniform across the galaxy than NGC 1313, with more extreme properties only being seen in the center of the galaxy. The lack of clearly-defined arm and interarm regions makes direct comparison tricky, but it is at least clear that no region of NGC 7793 contains clouds with surface densities, pressures, or linewidths as high as the most extreme properties found in the arms of NGC 1313 (Figure [9](#fig:7793 distributions observed) and [10](#fig:7793 distributions derived)). (cite: Elmegreen09) posits that the degree of dispersion of the density probability distribution function determines the ability of a region to form massive, gravitationally bound star clusters. Regions that have a larger spread in densities will also achieve higher densities, and so be able to form massive clusters. It would follow then that NGC 1313 is able to create more massive star clusters than NGC 7793 because it has a greater variety of subgalactic environments, including strong spiral arm environments that have higher pressures and densities. The lack of similarly large differences in the mass distributions of young clusters could be because the clusters in the LEGUS catalogs do not include many of the youngest, highly embedded clusters (cite: Messa21), and they are no longer closely associated with their natal molecular gas, as seen in Paper 1.

It is interesting to note as well that the southern arm of NGC 1313 has slightly more extreme properties than its northern arm. We know from measurements of HI and the star formation history of NGC 1313 (cite: Peters94; Larsen07; SilvaVillaLarsen12; Hernandez22) that it is experiencing an interaction, which likely caused a recent burst in star formation in the southwest of the galaxy approximately 100 Myr ago. This interaction may also be influencing the difference in cloud properties between the northern and southern arm, suggesting that satellite galaxy interaction can drive variations in local cloud properties.

Meanwhile in NGC 7793, its loose, poorly-defined spiral arms does not result in the majority of the clouds mimicking either the arm or the interarm regions of NGC 1313. Rather, the cloud properties throughout the galaxy have similar masses and kinetic energies to the arms of NGC 1313, but their surface densities and pressures are more similar throughout to the bar and interarm regions of NGC 1313. These differences overall result in higher virial parameters and longer free-fall times throughout NGC 7793 than any other regions in NGC 1313. Essentially, NGC 7793 has clouds that are just as massive and have just as much kinetic energy as NGC 1313, but they are puffier and less pressurized, and so are less inclined to collapse and form stars. This mirrors the findings in Paper 1 that the consumption time of the molecular mass in NGC 7793 is much longer than in NGC 1313. Strong spiral density waves are likely to perturb molecular clouds to induce collapse while they are in the arms, and then shear the clouds into more diffuse gas as they enter the interarm regions. The lack of strong spiral density waves in NGC 7793 allows the clouds to exist for a longer time in a dormant state where they are neither collapsing nor being torn apart.

A notable exception to the uniformity of NGC 7793 is the center of the galaxy, where the clouds have higher masses, and fewer clouds have low linewidths, virial parameters, and pressures. This is reminiscent of the center of our own Galaxy, where the clouds have more extreme properties and some massive star clusters are present, but it is still forming fewer stars than expected based on the gas properties (cite: Kauffmann17; Walker18), though this phenomenon may be partly accounted for by considering the metallicity dependence of the $X_\text{CO}$ factor (cite: Evans22).

This work represents the highest resolution direct comparison of the molecular cloud properties in spiral arm, interarm, and flocculent environments to date. Comparing our results at 13 pc to other results at $\sim$40-100 pc resolution reveals further insights about how the molecular gas behaves at different spatial scales. For the most part, we see similar trends in that spiral arms and galaxy centers have higher masses, linewidths, and pressures than interarm and outer regions of the galaxies. However, we see notably less difference in the surface densities between these regions than other studies have found at lower resolution (cite: Colombo14; Sun20; Rosolowsky21; Koda23). This could indicate that at lower resolution, the sparse clouds of the interarm and outer regions are spread out to lower apparent surface density by the large beam size. In the arm and central regions, the clouds are sufficiently clustered that the beam is filled by clouds getting blended together, and so the apparent surface density remains high. If this is the case, the surface density seen by lower-resolution studies could be indicative of the sparsity of molecular clouds rather than their true surface density.

# Conclusions

We present a comparison of the molecular gas properties in different regions of two galaxies, barred spiral NGC 1313, which is forming many massive clusters, and flocculent spiral NGC 7793, which is forming significantly fewer massive clusters despite having a similar star formation rate. Using the cloud properties calculated in Paper 1, we split the galaxies into regions including the bar, northern arm, southern arm, and interarm regions of NGC 1313 and a center, ring, and outer region of NGC 7793 since it has no clearly defined spiral arms to use. We compare how the molecular cloud properties vary by region in these two galaxies and how those regions and their differences compare between the two galaxies. Our major results are summarized below.

- The properties of the cluster population vary slightly by region, with the interarm region of NGC 1313 having the oldest and most massive clusters, while the northern arm has the youngest and least massive clusters. By number, the southern arm has significantly fewer young, massive clusters than the northern arm. The clusters in NGC 7793 show relatively little variation with region of the galaxy. However, when only the young clusters are considered, the center region of the galaxy has the fewest massive clusters.

- We fit power laws to the size-linewidth relations for the regions of the two galaxies, holding the slope fixed at a value of $a_1=0.5$ to determine relative kinetic energies from the fitted intercepts. The spiral arms of NGC 1313 have higher fitted intercepts, and so more kinetic energy, than the bar or interarm regions. The fitted intercepts of regions in NGC 7793 meanwhile do not differ by more than $3\sigma$.

- NGC 1313 has more clouds near virial equilibrium than NGC 7793 for all regions in NGC 1313 and all regions of NGC 7793. The southern arm of NGC 1313 and the center region of NGC 7793 both show a greater spread towards the unbound region of parameter space, suggesting that more of those clouds are either unbound or would require an external pressure to remain bound.

- The spiral arms of NGC 1313 tend to have more extreme cloud properties (higher masses, linewidths, surface densities, pressures, and virial parameters) than the bar or interarm regions, and they also host significantly more of the molecular gas mass. In some properties, such as linewidth, surface density, and pressure, the southern arm appears more extreme than the northern arm. This could be because the southern arm is more strongly influenced by the galaxy interaction to the southwest. The greater number of star clusters and the greater masses of those star clusters in NGC 1313 may be driven by its greater variation in environments and cloud properties within the galaxy. Its greater variation may allow for more extreme cloud properties to arise and so drive more intensive star formation.

- The center region of NGC 7793 has more extreme properties than the ring and outer regions, which are quite similar to each other. This suggests that the disk of NGC 7793 is relatively uniform in cloud properties, which is consistent with finding less variation in cluster properties among the regions than in NGC 1313. The cloud properties in NGC 7793 are not particularly similar to any one region of NGC 1313, suggesting that flocculent environments are distinct from either strong spiral arms or their interarm regions. NGC 7793 has clouds that are as massive and have as much kinetic energy as NGC 1313, but have slightly larger radii and are less dense and pressurized, and so less inclined to collapse and form stars. This indicates that in NGC 7793, clouds are likely to be dormant and form few stars for most of their lifetime, while in NGC 1313 those clouds are perturbed by spiral density waves and either collapse and form clusters or are sheared apart into more diffuse material.

- We see surprisingly little variation in surface density between arm and interarm regions in NGC 1313 given previous lower-resolution results. This suggests that differences in surface densities between arm and interarm regions observed in galaxies at $\sim$40 pc or coarser resolution could be driven by variations in the number of clouds filling the beam, rather than intrinsic variations in the surface densities of the clouds themselves.

# Acknowledgements

This material is based upon work supported by the National Science Foundation Graduate Research Fellowship Program under Grant No. 1842490. Any opinions, findings, and conclusions or recommendations expressed in this material are those of the author(s) and do not necessarily reflect the views of the National Science Foundation.

KG is supported by the Australian Research Council through the Discovery Early Career Researcher Award (DECRA) Fellowship (project number DE220100766) funded by the Australian Government. KG is supported by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. MRK acknowledges funding from the Australian Research Council through Laureate Fellowship LF220100020.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00782.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

These data are associated with the HST GO Program 13364 (PI D. Calzetti). Support for this program was provided by NASA through grants from the Space Telescope Science Institute. Based on observations obtained with the NASA/ESA Hubble Space Telescope, at the Space Telescope Science Institute, which is operated by the Association of Universities or Research in Astronomy, Inc., under NASA contract NAS5-26555.

ALMA, HST (WFC3, ACS)

# Software

Pipeline-CASA51-P2-B v.40896 (cite: Davis21), CASA (cite: McMullin07), `astrodendro` (cite: Rosolowsky08), `quickclump` (cite: Sidorin17), Astropy (cite: astropy), Matplotlib (cite: matplotlib), NumPy (cite: numpy), SciPy (cite: scipy),

natexlab

(ref: Adamo15) Adamo, A., Kruijssen, J. M., Bastian, N., Silva-villa, E., & Ryon, J. 2015, MNRAS, 452, 246, doi: [`10.1093/mnras/stv1203`](http://doi.org/10.1093/mnras/stv1203)

(ref: Adamo17) Adamo, A., Ryon, J. E., Messa, M., et al. 2017, ApJ, 841, 131, doi: [`10.3847/1538-4357/aa7132`](http://doi.org/10.3847/1538-4357/aa7132)

(ref: Adamo20) Adamo, A., Hollyhead, K., Messa, M., et al. 2020, MNRAS, 499, 3267, doi: [`10.1093/mnras/staa2380`](http://doi.org/10.1093/mnras/staa2380)

(ref: Adamo11) Adamo, A., Östlin, G., & Zackrisson, E. 2011, MNRAS, 417, 1904, doi: [`10.1111/j.1365-2966.2011.19377.x`](http://doi.org/10.1111/j.1365-2966.2011.19377.x)

(ref: Ali23) Ali, A. A., Dobbs, C. L., Bending, T. J. R., Buckner, A. S. M., & Pettitt, A. R. 2023, MNRAS, 524, 555, doi: [`10.1093/mnras/stad1917`](http://doi.org/10.1093/mnras/stad1917)

(ref: astropy) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Bolatto08) Bolatto, A. D., Leroy, A. K., Rosolowsky, E., Walter, F., & Blitz, L. 2008, ApJ, 686, 948, doi: [`10.1086/591513`](http://doi.org/10.1086/591513)

(ref: Brinchmann04) Brinchmann, J., Charlot, S., White, S. D., et al. 2004, MNRAS, 351, 1151, doi: [`10.1111/j.1365-2966.2004.07881.x`](http://doi.org/10.1111/j.1365-2966.2004.07881.x)

(ref: Calzetti15) Calzetti, D., Lee, J. C., Sabbi, E., et al. 2015, AJ, 149, doi: [`10.1088/0004-6256/149/2/51`](http://doi.org/10.1088/0004-6256/149/2/51)

(ref: Colombo14) Colombo, D., Hughes, A., Schinnerer, E., et al. 2014, ApJ, 784, doi: [`10.1088/0004-637X/784/1/3`](http://doi.org/10.1088/0004-637X/784/1/3)

(ref: Davis21) Davis. 2024, in prep

(ref: Dobbs11) Dobbs, C. L., Burkert, A., & Pringle, J. E. 2011, MNRAS, 413, 2935, doi: [`10.1111/j.1365-2966.2011.18371.x`](http://doi.org/10.1111/j.1365-2966.2011.18371.x)

(ref: Dobbs18) Dobbs, C. L., Pettitt, A. R., Corbelli, E., & Pringle, J. E. 2018, MNRAS, 478, 3793, doi: [`10.1093/MNRAS/STY1231`](http://doi.org/10.1093/MNRAS/STY1231)

(ref: DobbsPringle13) Dobbs, C. L., & Pringle, J. E. 2013, MNRAS, 432, 653, doi: [`10.1093/mnras/stt508`](http://doi.org/10.1093/mnras/stt508)

(ref: Dobbs13) Dobbs, C. L., Pringle, J. E., & Naylor, T. 2013, MNRASL, 437, doi: [`10.1093/mnrasl/slt134`](http://doi.org/10.1093/mnrasl/slt134)

(ref: Dobbs19) Dobbs, C. L., Rosolowsky, E., Pettitt, A. R., et al. 2019, MNRAS, 485, 4997, doi: [`10.1093/mnras/stz674`](http://doi.org/10.1093/mnras/stz674)

(ref: Dobbs17) Dobbs, C. L., Adamo, A., Few, C. G., et al. 2017, MNRAS, 464, 3580, doi: [`10.1093/mnras/stw2200`](http://doi.org/10.1093/mnras/stw2200)

(ref: JDM13) Donovan Meyer, J., Koda, J., Momose, R., et al. 2013, ApJ, 772, doi: [`10.1088/0004-637X/772/2/107`](http://doi.org/10.1088/0004-637X/772/2/107)

(ref: Elmegreen09) Elmegreen, B. G. 2009, Astrophysics and Space Science, 324, 83, doi: [`10.1007/s10509-009-0131-6`](http://doi.org/10.1007/s10509-009-0131-6)

(ref: Evans22) Evans, N. J., Kim, J.-G., & Ostriker, E. C. 2022, ApJL, 929, L18, doi: [`10.3847/2041-8213/ac6427`](http://doi.org/10.3847/2041-8213/ac6427)

(ref: Faesi16) Faesi, C. M., Lada, C. J., & Forbrich, J. 2016, ApJ, 821, 125, doi: [`10.3847/0004-637X/821/2/125`](http://doi.org/10.3847/0004-637X/821/2/125)

(ref: Finn2019) Finn, M. K., Johnson, K. E., Brogan, C. L., et al. 2019, ApJ, 874, 120, doi: [`10.3847/1538-4357/ab0d1e`](http://doi.org/10.3847/1538-4357/ab0d1e)

(ref: Finn22) Finn, M. K., Indebetouw, R., Johnson, K. E., et al. 2022, AJ, 164, 64, doi: [`10.3847/1538-3881/ac7aa1`](http://doi.org/10.3847/1538-3881/ac7aa1)

(ref: Finn23a) Finn, M. K., Johnson, K. E., Indebetouw, R., et al. 2024, ApJ

(ref: Gao16) Gao, Q., Wang, W., Liu, J.-F., & Yoachim, P. 2016, arXiv e-prints, arXiv:1602.07841, doi: [`10.48550/arXiv.1602.07841`](http://doi.org/10.48550/arXiv.1602.07841)

(ref: Grasha17a) Grasha, K., Calzetti, D., Adamo, A., et al. 2017a, ApJ, 840, 113, doi: [`10.3847/1538-4357/aa6f15`](http://doi.org/10.3847/1538-4357/aa6f15)

(ref: Grasha17b) Grasha, K., Elmegreen, B. G., Calzetti, D., et al. 2017b, ApJ, 842, 25, doi: [`10.3847/1538-4357/aa740b`](http://doi.org/10.3847/1538-4357/aa740b)

(ref: Grasha18) Grasha, K., Calzetti, D., Bittle, L., et al. 2018, MNRAS, 481, 1016, doi: [`10.1093/MNRAS/STY2154`](http://doi.org/10.1093/MNRAS/STY2154)

(ref: numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Hernandez22) Hernandez, S., Winch, A., Larsen, S., James, B. L., & Jones, L. 2022, AJ, 164, 89, doi: [`10.3847/1538-3881/ac7ebe`](http://doi.org/10.3847/1538-3881/ac7ebe)

(ref: matplotlib) Hunter, J. D. 2007, Computing in Science Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Indebetouw20) Indebetouw, R., Wong, T., Chen, C. H. R., et al. 2020, ApJ, 888, 56, doi: [`10.3847/1538-4357/ab5db7`](http://doi.org/10.3847/1538-4357/ab5db7)

(ref: Johnson15) Johnson, K. E., Leroy, A. K., Indebetouw, R., et al. 2015, ApJ, 806, 35, doi: [`10.1088/0004-637X/806/1/35`](http://doi.org/10.1088/0004-637X/806/1/35)

(ref: Johnson16) Johnson, L. C., Seth, A. C., Dalcanton, J. J., et al. 2016, ApJ, 827, 33, doi: [`10.3847/0004-637X/827/1/33`](http://doi.org/10.3847/0004-637X/827/1/33)

(ref: Johnson17) —. 2017, ApJ, 839, 78, doi: [`10.3847/1538-4357/aa6a1f`](http://doi.org/10.3847/1538-4357/aa6a1f)

(ref: Kauffmann17) Kauffmann, J., Pillai, T., Zhang, Q., et al. 2017, A&A, 603, A89, doi: [`10.1051/0004-6361/201628088`](http://doi.org/10.1051/0004-6361/201628088)

(ref: Koda09) Koda, J., Scoville, N., Sawada, T., et al. 2009, ApJ, 700, doi: [`10.1088/0004-637X/700/2/L132`](http://doi.org/10.1088/0004-637X/700/2/L132)

(ref: Koda23) Koda, J., Hirota, A., Egusa, F., et al. 2023, ApJ, 949, 108, doi: [`10.3847/1538-4357/acc65e`](http://doi.org/10.3847/1538-4357/acc65e)

(ref: Krahm23) Krahm, G., Finn, M. K., Indebetouw, R., et al. subm., ApJ

(ref: Larsen07) Larsen, S. S., Mora, M. D., Brodie, J. P., & Richtler, T. 2007, in Stellar Populations as Building Blocks of Galaxies, ed. A. Vazdekis & R. Peletier, Vol. 241, 435–439, doi: [`10.1017/S1743921307008708`](http://doi.org/10.1017/S1743921307008708)

(ref: Larson81) Larson, R. B. 1981, MNRAS, 194, 809, doi: [`10.1093/mnras/194.4.809`](http://doi.org/10.1093/mnras/194.4.809)

(ref: Lazariv18) Lazariv, T., & Lehmann, C. 2018, Goodness-of-Fit Tests for Large Datasets. [`https://arxiv.org/abs/1810.09753`](https://arxiv.org/abs/1810.09753)

(ref: Leroy21) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: McMullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Meidt13) Meidt, S. E., Schinnerer, E., García-Burillo, S., et al. 2013, ApJ, 779, doi: [`10.1088/0004-637X/779/1/45`](http://doi.org/10.1088/0004-637X/779/1/45)

(ref: Meidt15) Meidt, S. E., Hughes, A., Dobbs, C. L., et al. 2015, ApJ, 806, doi: [`10.1088/0004-637X/806/1/72`](http://doi.org/10.1088/0004-637X/806/1/72)

(ref: Menon21) Menon, S. H., Grasha, K., Elmegreen, B. G., et al. 2021, MNRAS, 507, 5542, doi: [`10.1093/mnras/stab2413`](http://doi.org/10.1093/mnras/stab2413)

(ref: Messa18) Messa, M., Adamo, A., Calzetti, D., et al. 2018, MNRAS, 477, 1683, doi: [`10.1093/mnras/sty577`](http://doi.org/10.1093/mnras/sty577)

(ref: Messa21) Messa, M., Calzetti, D., Adamo, A., et al. 2021, ApJ, 909, 121, doi: [`10.3847/1538-4357/abe0b5`](http://doi.org/10.3847/1538-4357/abe0b5)

(ref: MivilleDeschenes17) Miville-Deschênes, M.-A., Murray, N., & Lee, E. J. 2017, ApJ, 834, 57, doi: [`10.3847/1538-4357/834/1/57`](http://doi.org/10.3847/1538-4357/834/1/57)

(ref: Nayak16) Nayak, O., Meixner, M., Indebetouw, R., et al. 2016, ApJ, 831, 32, doi: [`10.3847/0004-637X/831/1/32`](http://doi.org/10.3847/0004-637X/831/1/32)

(ref: Nguyen18) Nguyen, N. K., Pettitt, A. R., Tasker, E. J., & Okamoto, T. 2018, MNRAS, 475, 27, doi: [`10.1093/mnras/stx3143`](http://doi.org/10.1093/mnras/stx3143)

(ref: Peters94) Peters, W. L., Freeman, K. C., Forster, J. R., Manchester, R. N., & Ables, J. G. 1994, MNRAS, 269, 1025, doi: [`10.1093/mnras/269.4.1025`](http://doi.org/10.1093/mnras/269.4.1025)

(ref: Pettitt20) Pettitt, A. R., Dobbs, C. L., Baba, J., et al. 2020, MNRAS, 498, 1159, doi: [`10.1093/mnras/staa2242`](http://doi.org/10.1093/mnras/staa2242)

(ref: Pettitt18) Pettitt, A. R., Egusa, F., Dobbs, C. L., et al. 2018, MNRAS, 480, 3356, doi: [`10.1093/mnras/sty2040`](http://doi.org/10.1093/mnras/sty2040)

(ref: Qing15) Qing, G., Wang, W., Liu, J.-F., & Yoachim, P. 2015, ApJ, 799, 19, doi: [`10.1088/0004-637X/799/1/19`](http://doi.org/10.1088/0004-637X/799/1/19)

(ref: Querejeta21) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, A&A, 656, A133, doi: [`10.1051/0004-6361/202140695`](http://doi.org/10.1051/0004-6361/202140695)

(ref: RadburnSmith11) Radburn-Smith, D. J., de Jong, R. S., Seth, A. C., et al. 2011, ApJS, 195, 18, doi: [`10.1088/0067-0049/195/2/18`](http://doi.org/10.1088/0067-0049/195/2/18)

(ref: Rice16) Rice, T. S., Goodman, A. A., Bergin, E. A., Beaumont, C., & Dame, T. M. 2016, ApJ, 822, 52, doi: [`10.3847/0004-637X/822/1/52`](http://doi.org/10.3847/0004-637X/822/1/52)

(ref: Rosolowsky21) Rosolowsky, E., Hughes, A., Leroy, A. K., et al. 2021, MNRAS, 502, 1218, doi: [`10.1093/mnras/stab085`](http://doi.org/10.1093/mnras/stab085)

(ref: Rosolowsky08) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ, 679, 1338, doi: [`10.1086/587685`](http://doi.org/10.1086/587685)

(ref: Sabbi18) Sabbi, E., Calzetti, D., Ubeda, L., et al. 2018, ApJS, 235, 23, doi: [`10.3847/1538-4365/aaa8e5`](http://doi.org/10.3847/1538-4365/aaa8e5)

(ref: Schinnerer13) Schinnerer, E., Meidt, S. E., Pety, J., et al. 2013, ApJ, 779, doi: [`10.1088/0004-637X/779/1/42`](http://doi.org/10.1088/0004-637X/779/1/42)

(ref: Sidorin17) Sidorin, V. 2017, Quickclump: Identify clumps within a 3D FITS datacube. [`http://ascl.net/1704.006`](http://ascl.net/1704.006)

(ref: SilvaVilla13) Silva-Villa, E., Adamo, A., & Bastian, N. 2013, MNRASL, 436, doi: [`10.1093/mnrasl/slt115`](http://doi.org/10.1093/mnrasl/slt115)

(ref: SilvaVillaLarsen12) Silva-Villa, E., & Larsen, S. S. 2012, MNRAS, 423, 213, doi: [`10.1111/j.1365-2966.2012.20797.x`](http://doi.org/10.1111/j.1365-2966.2012.20797.x)

(ref: Solomon87) Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987, ApJ, 319, 730, doi: [`10.1086/165493`](http://doi.org/10.1086/165493)

(ref: Stanghellini15) Stanghellini, L., Magrini, L., & Casasola, V. 2015, ApJ, 812, doi: [`10.1088/0004-637X/812/1/39`](http://doi.org/10.1088/0004-637X/812/1/39)

(ref: Sun18PHANGS) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860, 172, doi: [`10.3847/1538-4357/aac326`](http://doi.org/10.3847/1538-4357/aac326)

(ref: Sun20) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020, ApJL, 901, L8, doi: [`10.3847/2041-8213/abb3be`](http://doi.org/10.3847/2041-8213/abb3be)

(ref: Sun22) Sun, J., Leroy, A. K., Rosolowsky, E., et al. 2022, ApJ, 164, 43, doi: [`10.3847/1538-3881/ac74bd`](http://doi.org/10.3847/1538-3881/ac74bd)

(ref: Turner22) Turner, J. A., Dale, D. A., Lilly, J., et al. 2022, MNRAS, 516, 4612, doi: [`10.1093/mnras/stac2559`](http://doi.org/10.1093/mnras/stac2559)

(ref: scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Wainer22) Wainer, T. M., Johnson, L. C., Seth, A. C., et al. 2022, ApJ, 928, 15, doi: [`10.3847/1538-4357/ac51cf`](http://doi.org/10.3847/1538-4357/ac51cf)

(ref: Walker18) Walker, D. L., Longmore, S. N., Zhang, Q., et al. 2018, MNRAS, 474, 2373, doi: [`10.1093/mnras/stx2898`](http://doi.org/10.1093/mnras/stx2898)

(ref: WalshRoy97) Walsh, J. R., & Roy, J. R. 1997, MNRAS, 288, 726, doi: [`10.1093/mnras/288.3.726`](http://doi.org/10.1093/mnras/288.3.726)

(ref: Whitmore23) Whitmore, B. C., Chandar, R., Lee, J. C., et al. 2023, MNRAS, 520, 63, doi: [`10.1093/mnras/stad098`](http://doi.org/10.1093/mnras/stad098)

(ref: MAGMA) Wong, T., Hughes, A., Ott, J., et al. 2011, ApJS, 197, 16, doi: [`10.1088/0067-0049/197/2/16`](http://doi.org/10.1088/0067-0049/197/2/16)

(ref: Wong22) Wong, T., Oudshoorn, L., Sofovich, E., et al. 2022, ApJ, 932, 47, doi: [`10.3847/1538-4357/ac723a`](http://doi.org/10.3847/1538-4357/ac723a)

(ref: Yu21) Yu, S.-Y., Ho, L. C., & Wang, J. 2021, ApJ, 917, 88, doi: [`10.3847/1538-4357/ac0c77`](http://doi.org/10.3847/1538-4357/ac0c77)

# Kolmogorov-Smirnoff and Anderson-Darling Tests

As thoroughly discussed in (cite: Lazariv18), as the sample size increases, the discerning power of KS tests increases. However, KS tests cannot take into account error in the measurements, and so it is possible for a test to become over-powered. Even a small difference in the distribution well below the measurement uncertainty can result in a rejection of the null hypothesis that the distributions are the same. This effect is present in AD tests as well.

To combat overpowered statistical tests, we perform a bootstrapping method to measure the difference in the distributions. We take 1000 random subsamples with a size of 65 data points, perform KS and AD tests between each pairing of regions, and report the average $p$-value for the 1000 subsamples. We caution that the resulting $p$-values are highly dependent on the size of the subsample used, and so these results should only be used to compare the differences between properties and regions on equally-powered statistical footing. This is meant as an indication of which pairings are the most likely to be different, not whether the underlying distributions are truly, statistically different. It may be possible to select a subsample size based on the error of the measurements being tested, but that is outside the scope of the current work.

Figure [11](#fig:KS test grid) shows the bootstrapped KS statistic for each cloud and cluster property for each pairing of subgalactic region as well as global distributions for each galaxy. Figure [12](#fig:AD test grid) shows the same but with an AD test. KS tests are more influenced by the center of the distribution, while AD tests are more sensitive to the tails.

![image](KSgrid_mass.png) ![image](KSgrid_R.png) ![image](KSgrid_sigv.png)\
![image](KSgrid_alpha.png) ![image](KSgrid_surfdens.png)\
![image](KSgrid_Pe.png) ![image](KSgrid_tff.png) ![image](KSgrid_cmass.png)\
![image](KSgrid_ycmass.png) ![image](KSgrid_age.png)

![image](ADgrid_mass.png) ![image](ADgrid_R.png) ![image](ADgrid_sigv.png)\
![image](ADgrid_alpha.png) ![image](ADgrid_surfdens.png)\
![image](ADgrid_Pe.png) ![image](ADgrid_tff.png) ![image](ADgrid_cmass.png)\
![image](ADgrid_ycmass.png) ![image](ADgrid_age.png)

</paper>

Write the methods card for this paper.