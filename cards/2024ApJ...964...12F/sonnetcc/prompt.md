# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...964...12F\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...964...12F",
 "title": "ALMA-LEGUS. I. The Influence of Galaxy Morphology on Molecular Cloud Properties",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Finn, Molly K.",
 "n_authors": 27,
 "arxiv_id": "2401.01450",
 "doi": "10.3847/1538-4357/ad1eec",
 "alma_projects_linked_by_archive": [
  "2015.1.00782.S"
 ]
}
```

Paper text:
<paper>
# ALMA-LEGUS I: The Influence of Galaxy Morphology on Molecular Cloud Properties

## Abstract

We present a comparative study of the molecular gas in two galaxies from the LEGUS sample: barred spiral NGC 1313 and flocculent spiral NGC 7793. These two galaxies have similar masses, metallicities, and star formation rates, but NGC 1313 is forming significantly more massive star clusters than NGC 7793, especially young massive clusters ($<10$ Myr, $>10^4$ M$_\odot$). Using ALMA CO(2-1) observations of the two galaxies with the same sensitivities and resolutions of 13 pc, we directly compare the molecular gas in these two similar galaxies to determine the physical conditions responsible for their large disparity in cluster formation. By fitting size-linewidth relations for the clouds in each galaxy, we find that NGC 1313 has a higher intercept than NGC 7793, implying that its clouds have higher kinetic energies at a given size scale. NGC 1313 also has more clouds near virial equilibrium than NGC 7793, which may be connected to its higher rate of massive cluster formation. However, these virially bound clouds do not show a stronger correlation with young clusters than that of the general cloud population. We find surprisingly small differences between the distributions of molecular cloud populations in the two galaxies, though the largest of those differences are that NGC 1313 has higher surface densities and lower free-fall times.

# Introduction

![image](NGC1313_RGB.pdf) ![image](NGC7793_RGB.pdf) ![image](NGC1313_ClusterMap.pdf) ![image](NGC7793_ClusterMap.pdf)

At low redshifts, the majority of star formation takes place in spiral galaxies (cite: Brinchmann04). This means that to understand star formation in the local universe, we need to understand the influence of spiral structure on the physical conditions of the molecular gas and the processes by which that gas is converted into stars.

There have been several studies that have examined the molecular gas properties traced by CO in nearby spiral galaxies. Some examples of these studies include PAWS (PdBI Arcsecond Whirlpool Survey), which mapped M51 in CO(1-0) at 40 pc resolution (cite: Schinnerer13), CANON (CArma and NObeyama Nearby galaxies), which mapped the inner disks of nearby spiral galaxies in CO(1-0) and enabled a focused study of a subsample at 62-78 pc resolution (cite: JDM13), and the barred spiral galaxy M83 was mapped in CO(1-0) at 40 pc resolution (cite: Koda23). These three studies focused primarily on galaxies with strong spiral arms rather than flocculent spirals.

PHANGS-ALMA (Physics at High Angular resolution in Nearby Galaxies) expanded the type of galaxies included, mapping 90 galaxies in CO(2-1) at $\sim100$ pc resolution (cite: Leroy21), including galaxies with a wide range of morphologies. Comparing the galaxies in their sample by morphology type, (cite: Stuber23) found that the flocculent spirals tended to have lower total stellar masses and star formation rates than galaxies with stronger spiral patterns. Meanwhile (cite: Hart17) found that in a sample of spiral galaxies from the Sloan Digital Sky Survey, galaxies with two strong spiral arms had similar star formation rates but higher efficiency in converting their gas to stars than galaxies with many flocculent spiral arms. While studies have examined how the cloud properties of spiral galaxies vary between the disks, centers, arms, and interarm regions (cite: Koda09; Rosolowsky08; Colombo14; Sun18PHANGS; Sun20; Rosolowsky21; Querejeta21; Koda23), a more detailed examination of how the cloud properties vary between galaxies of different morphologies is not yet available.

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Galaxy | Distance$^a$ | Metallicity$^b$ | SFR$^c$ | M$_*^d$ | M$_\text{HI}^{e}$ | M$_\text{mol}^f$ | M$_\text{cluster}^g$ |
|  | (Mpc) | ($12+\log(\text{O/H})$) | (M$_\odot$/yr) | ($\times10^9$ M$_\odot$) | ($\times10^9$ M$_\odot$) | ($\times10^6$ M$_\odot$) | ($\times10^6$ M$_\odot$) |
| NGC 1313 | 4.6 | 8.4 | 1.15 | 2.6 | 2.1 | 7.6$^{f}$ | 17.3$^{g}$ |
| NGC 7793 | 3.7 | 8.52 | 0.52 | 3.2 | 0.78 | 14.0$^{f}$ | 6.4$^{g}$ |

\

Notes: $^a$ (cite: Qing15), (cite: Gao16) for NGC 1313; (cite: RadburnSmith11), (cite: Sabbi18) for NGC 7793,\
$^b$ (cite: WalshRoy97) and (cite: Stanghellini15),\
$^c$ Calculated by (cite: Calzetti15) using GALEX far-UV images, dust corrected with methods of (cite: Lee09),\
$^d$ Calculated by (cite: Calzetti15) using extinction-corrected $B$-band luminosities and methods of (cite: Bothwell09),\
$^e$ Calculated by (cite: Calzetti15) using HI observations from (cite: Koribalski04),\
$^f$ Sum of all CO(2-1) emission, multiplied by an average $X_\text{CO}$ and factor of 1.4 for each galaxy as discussed in Section [5](#sec:properties), does not cover full galaxies due to smaller observational footprint and is likely missing flux because 7m and TP data are not included here, \
$^g$ Total mass of star clusters in LEGUS catalogs, based on methods of (cite: Adamo17), does not cover full galaxies.

To better understand the role of galaxy morphology on molecular gas conditions on the scale of individual clouds and how it relates to star formation, we present a comparative study of the molecular gas in two spiral galaxies: NGC 1313 and NGC 7793 (Figure [1](#fig:RGB images)). These two galaxies are included in the Legacy ExtraGalactic UV Survey (cite: Calzetti15), a Hubble Space Telescope (HST) Treasury Program that observed 50 nearby ($<12$ Mpc) galaxies. As part of the LEGUS survey, they both have comprehensive catalogs of their young star clusters and their masses and ages using the methodology described in (cite: Adamo17), which allows us to compare the star-forming properties of each galaxy with the molecular gas at scales of $\sim10$ pc.

NGC 1313 and NGC 7793 were chosen because they have many similar properties, such as their total stellar mass (cite: Calzetti15), their overall metallicities (cite: WalshRoy97; Stanghellini15), their star formation rates (cite: Calzetti15), and their Hubble type of Sd. They are also both mostly face-on with clear views of the spiral structures in each (cite: Calzetti15) and have similar distances (cite: RadburnSmith11; Qing15; Gao16; Sabbi18). Their main properties are listed in Table [\[tab:intro comparison\]](#tab:intro comparison).

Despite these many similarities, the two galaxies have starkly different spiral structures, with NGC 1313 being barred with strong spiral arms and NGC 7793 being a flocculent spiral (see Figure [1](#fig:RGB images)). NGC 1313 also appears to be experiencing a minor interaction (see §[1.1](#subsec:NGC1313 intro)). Based on the LEGUS cluster catalogs, they also have strikingly different numbers of massive clusters. NGC 1313 has more than six times as many clusters that are more massive than $10^4$ M$_\odot$, despite having a SFR only 2.2 times higher than NGC 7793. NGC 1313 also has 2.7 times more neutral HI gas (cite: Calzetti15), but only half as much molecular gas as NGC 7793, as measured in the observational footprint presented here (see Section [5](#sec:properties)). This makes NGC 1313 and NGC 7793 an interesting pair of galaxies to compare to further understand how the spiral structure of a galaxy influences the molecular gas properties and the types of star clusters that are formed.

## NGC 1313

NGC 1313 has an irregular morphology with a strong bar and asymmetric spiral arms, which has historically been compared to the Large Magellanic Cloud (cite: deVaucouleurs63). Its irregular morphology (cite: SandageBrucato79) and observations of the HI showing a loop of gas around the galaxy and a disturbance in its velocity field in the southwest of the galaxy (cite: Peters94) indicate that it is interacting with a satellite galaxy. When measuring the galaxy’s star formation history, (cite: Larsen07) found an increase in recent star formation in the southwest of the galaxy, potentially caused by this interaction. This was further confirmed by (cite: SilvaVillaLarsen12), who found that rather than undergoing a starburst across the whole galaxy, there was only an increase in star formation in the southwestern field. They find that the regional starburst occurred $\sim100$ Myr ago.

(cite: WalshRoy97) found that NGC 1313 is one of the most massive galaxies that has no gas-phase metallicity gradient across its disk. However, the more recent study (cite: Hernandez22) shows evidence for a metallicity gradient based on the chemical abundances of young clusters. They also find a constant star formation rate across the disk of NGC 1313 with the exception of the burst in the southwest. This southwestern region where the localized starburst is observed is just outside of the observation footprint for this study. A difference in stellar metallicity tracing a separate population was found throughout the disk by (cite: Tikhonov16), which they attribute to a past merger with a low-mass dwarf satellite that did not gravitationally distort the arms or central region of NGC 1313.

The star cluster population in NGC 1313 has been characterized using the LEGUS cluster catalogs by (cite: Grasha17b), and the sizes of these clusters were further characterized by (cite: Ryon17), who found that the clusters are undergoing relaxation but appear to be gravitationally bound. (cite: Hannon19) studied the morphology of the H$\alpha$ around these clusters and report clearing times for the gas of $\lesssim1$ Myr. (cite: Messa21) added to the LEGUS catalogs by searching for embedded clusters identified with Pa$\beta$ and in the near-infrared and finding that up to 60% of the star clusters are not accounted for in the UV-optical catalogs and that gas-clearing timescales are closer to 3-4 Myr.

## NGC 7793

NGC 7793 is a member of the Sculptor group of galaxies and has been well-studied due to its proximity and high Galactic latitude. It has no bar, a small bulge with a nuclear star cluster (cite: Kacharov18), and a mostly uniform distribution of small, loose spiral arms with little coherent structure (cite: Elmegreen14), to the point that it has been called an “extreme” flocculent spiral (cite: Elmegreen84). It has nearby dwarf companions, and the HI disk is warped, suggesting some level of interaction, though they see no sign of tidal effects (cite: Koribalski18). It has drawn attention for its unusual discontinuous and positive metallicity gradient in the far outer disk (cite: Vlajic11) and its declining rotation curve in the outer edges of the disk (cite: CarignanPuch90; Dicaire08), although the latter could be due to a line-of-sight warp in the disk (cite: Bacchini19). Studies of its stellar population have also shown that it has a break in the disk where the surface brightness departs from simple exponential decrease, likely caused by radial migration of the stars (cite: RadburnSmith12).

The star formation history of NGC 7793 has been studied by (cite: Sacchi19) and they found an inside-out growth of the galaxy, with the outer regions undergoing a greater recent increase in star formation than the inner region. Inside-out growth was also seen in young clumps identified in UV light by (cite: Mondal21), who also suggest that NGC 7793 is experiencing a recent increase in its star formation rate. Its LEGUS-identified star clusters were included in the same studies as NGC 1313 by (cite: Grasha17b), (cite: Hannon19), and (cite: BrownGnedin21) to characterize their populations, cluster boundedness, and gas clearing timescales. The clusters and molecular gas were further studied by (cite: Grasha18), finding that the younger clusters are more spatially correlated with molecular clouds and that the hierarchical clustering of the clouds is shared by the young clusters. (cite: Muraoka16) has also mapped the CO(3-2) line in NGC 7793, finding that its emission is well-correlated with infrared tracers of star formation.

\
To robustly compare the properties of the molecular clouds in this pair of galaxies, we have observed both in CO(2-1) with carefully matched spatial resolutions of 13 pc and surface brightness sensitivities of $\sim0.2$ K. These observations allow us to make a direct comparison of clouds in a galaxy with strong spiral arms and in a flocculent spiral without concern for resolution or sensitivity effects. This paper is organized as follows: We present the observations used in this analysis in Section [2](#sec:obs), and the LEGUS cluster catalogs of the two galaxies in Section [3](#sec: cluster catalogs). We then discuss the decomposition of the CO(2-1) emission into substructures in Section [4](#sec:dendrogram) and the calculation of their properties in Section [5](#sec:properties). We examine the size-linewidth relations of the clouds in each galaxy in Section [6](#sec:SL plots), and the virialization of the clouds in Section [7](#sec: virial plot). We compare the distributions of all the measured and derived properties in Section [8](#sec:property comparison). In Section [9](#sec:spatial distributions), we examine how the clouds and their properties are spatially correlated with those of the clusters. We discuss our findings in Section [10](#sec:discussion) and summarize our conclusions in Section [11](#sec:conclusions).

# Observations

![image](NGC1313_moment8.pdf) ![image](NGC7793_moment8.pdf)

## NGC 1313 CO(2-1)

NGC 1313 was observed by ALMA in Band 6 (project code 2015.1.00782.S; PI: K. E. Johnson) with the 12m array. It was originally observed in Cycle 4 in 2016 but did not meet sensitivity requirements and so was observed again in Cycle 5 in 2018. The galaxy is split into two mosaics, one covering the northern arm of the galaxy, and one covering the central region and southern arm. The northern arm mosaic consists of 68 pointings with 1.9 minutes of integration per pointing with a spacing of 12.9$''$ for a total integration time of 2.2 hours. The central mosaic consists of 104 pointings with 2.2 minutes of integration per pointing for a total integration time of 3.75 hours, also with a spacing of 12.9$''$. The largest angular scale recovered with these observations is 7.4$''$, which corresponds to a spatial scale of 150 pc, much larger than any of the clouds measured in this analysis.

The data were calibrated with the ALMA data pipeline version Pipeline-CASA54-P1-B (cite: Hunter23) in CASA 5.4.0-68 using J2258-2758 for bandpass and amplitude calibration and J2353-3037 for phase calibration. It was imaged in CASA 6.1.1.15 with a robust parameter of 0.5, resulting in a synthesized beam of 0.579$''$$\times$0.486$''$ (12.8$\times$11.2 pc at a distance of 4.6 Mpc).

In Figure [2](#fig:maps), we show the image data after smoothing to a circular beam size of 13 pc to match the observations of NGC 7793, which corresponds to 0.583$''$ for NGC 7793. A summary of the resulting image is shown in Table [1](#tab:observations).

## NGC 7793 CO(2-1)

NGC 7793 was observed by ALMA in Band 6 during Cycle 4 in 2016 (project code 2015.1.00782.S; PI: K. E. Johnson) with the 12m array. The observations were a mosaic of the central 180$''$$\times$114$''$ (3$\times$2 kpc) of NGC 7793. The total integration time is 3 hours with the 12-m array with 148 pointings at 1.2 minutes of integration per pointing and a mosaic spacing of 12.9$''$ between pointings. The largest angular scale recovered with these observations is 7.0$''$, which corresponds to a spatial scale of 125 pc, much larger than any of the clouds measured in this analysis.

The data were calibrated with the ALMA data pipeline version 2020.1.0-40 (cite: Hunter23) in CASA 6.1.1.15 using J0519-4546 and J0334-4008 for bandpass and amplitude calibration and J0303-6211 for phase calibration. It was imaged using a Briggs weighting with a robust parameter of 2.0, resulting in a synthesized beam size of 0.686$''$$\times$0.595$''$ (12.3$\times$10.7 pc at a distance of 3.7 Mpc).

In Figure [2](#fig:maps), we show the image data after smoothing to a circular beam size of 13 pc to match the observations of NGC 1313, which corresponds to 0.724$''$ for NGC 7793. A summary of the resulting image is shown in Table [1](#tab:observations). These data also appeared in (cite: Grasha18).

|          |          |      |       |                   |
|:--------:|:--------:|:----:|:-----:|:-----------------:|
|  Galaxy  |   Beam   | Beam |  rms  |     Velocity      |
|          | (arcsec) | (pc) | \(K\) | Resolution (km/s) |
| NGC 1313 |   0.58   |  13  | 0.15  |       1.33        |
| NGC 7793 |   0.72   |  13  |  0.2  |       1.33        |

: ALMA $^{12}$CO(2-1) Observations

# Cluster Catalogs

In addition to the CO(2-1) data, we use catalogs of star clusters and their SED-fitted properties from the LEGUS collaboration, which used the methodology described in (cite: Adamo17). In this work, we use their catalog that uses the Milky Way extinction law from (cite: Cardelli89), averaged aperture correction method, and Padova stellar evolutionary tracks implemented by Yggdrasil (cite: Zackrisson11). We include all objects identified by LEGUS as cluster candidates, which required that they were brighter than M$_{V}$ of -6, detected above $3\sigma$ in the UBVI set of filters, and had a visual classification of 1 or 2 (compact) or class 3 (multiply-peaked). (cite: Adamo17) adopt a 90% completeness limit of 5000 M$_\odot$ for clusters with ages up to 200 Myr in NGC 602, which has a distance of 10 Mpc. However, at the distances of NGC 1313 and NGC 7793, we expect this limit to be much lower, closer to 1000 M$_\odot$ (cite: Grasha18). We represent this 1000 M$_\odot$ limit as a vertical line in the mass distributions shown in Figure [3](#fig:global cluster distributions).

Several studies have pointed out that a degeneracy in age and reddening during the fitting results in many old globular clusters incorrectly being assigned much younger ages (cite: Turner21; Hannon19; Whitmore23). In particular, (cite: Whitmore23) find that the majority of these objects with incorrectly fitted ages fall above a line extending from (6, 1) to (9, 0.1) in a plot of E(B-V) versus log(Age). They also find that these incorrect ages primarily affect objects on the high mass end ($M>10^{4.5}M_\odot$). To account for these incorrect ages without biasing our sample against high-mass objects, we remove the clusters that fall above the E(B-V)-log(Age) line from (cite: Whitmore23) only when comparing age measurements between the two galaxies. This affects 76 clusters in NGC 1313 and 29 clusters in NGC 7793 (6% of the identified clusters in both galaxies). Carefully fitting these objects with the degeneracy in mind would likely result in many of them having ages older than 1 Gyr. We also note that there are few enough of these objects that keeping or removing them does not substantially alter our results.

(cite: OrozcoDuarte22) compared the output of the LEGUS cluster catalog for NGC 7793 with results obtained using synthetic photometry and a stochastically sampled IMF and found masses that were on average 0.11 dex larger and ages that were 1 Myr younger compared to the (cite: Adamo17) method. However, we use the original LEGUS catalogs still to maintain a consistent method between the two galaxies.

(cite: Messa21) also identify a significant population of embedded clusters in NGC 1313. However, since we do not also have embedded clusters identified in NGC 7793 to compare, we do not include those clusters in this work.

The cluster catalogs for both galaxies were separated into east and west portions of the map. To combine these, we identified matching pairs of clusters in the overlap region. We then used the cluster properties from the map that had the better fit, based on their reported quality of fit Q parameter. We identified 67 overlapping clusters in NGC 1313 and 47 in NGC 7793. Each of these clumps has a fitted mass, age, and extinction from the catalog.

## Cluster Counts

+----------------+-------------------------------+----------+----------+
|                |                               | NGC 1313 | NGC 7793 |
+:===============+:==============================+:========:+:========:+
| LEGUS Clusters | All Clusters                  | 1201     | 467      |
|                +-------------------------------+----------+----------+
|                | Massive Clusters$^a$          | 333      | 53       |
|                +-------------------------------+----------+----------+
|                | Young, Massive Clusters$^a,b$ | 37       | 3        |
|                +-------------------------------+----------+----------+
|                | Trunks$^c$                    | 65       | 130      |
+----------------+-------------------------------+----------+----------+
|                | Branches$^c$                  | 82       | 187      |
+----------------+-------------------------------+----------+----------+
|                | Leaves$^c$                    | 442      | 761      |
+----------------+-------------------------------+----------+----------+
|                | Clumps$^d$                    | 531      | 965      |
+----------------+-------------------------------+----------+----------+
|                | Massive Clumps$^a,d$          | 137      | 306      |
+----------------+-------------------------------+----------+----------+

\

Note: $^a$The threshold used to define “massive” for both clumps and clusters in this table is $M>10^4 M_\odot$.\
$^b$ The threshold used to define “young” for clusters is an age $<10$ Myr.\
$^c$ Structures identified by `astrodendro`.\
$^d$ Structures identified by `quickclump`.

NGC 1313 has $\sim2.6$ times as many identified star clusters at all masses as NGC 7793, with a total of 1201 clusters compared to 467 for NGC 7793. Considering that the star formation rate in NGC 1313 is $\sim2.2$ times larger than that of NGC 7793, this represents a small excess in cluster formation. We can also account for the fraction of the total SFR included in the footprints of the LEGUS observations used to identify these clusters based on the fraction of the GALEX far-UV light. We note that the SFR traced by UV light is well-matched to the ages of the general cluster population, but may be averaged over too long a timescale to be accurate for the youngest clusters. In NGC 1313, 57% of the total SFR is included in the LEGUS footprint, and in NGC 7793 53% is included. Assuming that the cluster populations are well-matched to the SFR within each galaxy, NGC 1313 would have $\sim2110$ clusters and NGC 7793 would have $\sim880$ clusters within the total star forming area of each galaxy. This suggests then that NGC 1313 has $\sim2.4$ times as many clusters than NGC 7793 in the full galaxy, still a slight excess over the difference in total SFR.

This difference in cluster number is more extreme when we consider only the most massive clusters with $M_* > 10^4 M_\odot$. NGC 1313 has over six times as many massive clusters, having 333 massive clusters identified by LEGUS where NGC 7793 has 53. Correcting for the fraction of star formation traced by LEGUS would still leave NGC 1313 with 5.8 times more massive clusters. Furthermore, 37 of those massive clusters are young (\<10 Myr) in NGC 1313, compared to only 3 in NGC 7793. As seen in Figure [3](#fig:global cluster distributions), NGC 7793 does have a couple of particularly massive clusters, and so we can also compare the mass of clusters in both galaxies above the $M_* > 10^4 M_\odot$ threshold and we find that NGC 1313 has 2.7 times as much mass in massive clusters (2.5 times the mass when including a total SFR correction), which still represents an excess of massive cluster formation in NGC 1313 by this metric.

We also note, however, that based on the (cite: Lee09) comparison of the dust-corrected UV-based method of calculating SFR to measuring SFR with H$\alpha$, we estimate that the SFR values reported in (cite: Calzetti15) would have $1\sigma$ uncertainties of approximately $25\%$. (cite: Calzetti15) do not report uncertainties on the SFR for NGC 1313 and NGC 7793 specifically, but if we take this estimated uncertainty value from (cite: Lee09) and propagate the error, we get a ratio of 2.2$\pm$0.8 in the SFR between the two galaxies. In this case, the ratios reported here are not statistically significant when considering error from counting statistics.

Overall, NGC 1313 not only has more clusters, but also has more massive clusters than NGC 7793, despite the lower molecular gas content of NGC 1313 (as shown in Table [\[tab:intro comparison\]](#tab:intro comparison) and will be discussed in Section [5](#sec:properties)). These cluster numbers are shown in Table [\[tab:segmentation\]](#tab:segmentation).

## Cluster Property Distributions

We further consider how the distributions of cluster masses and ages compare between the two galaxies by looking at histograms, Gaussian kernel density estimations (KDEs) from `scipy` (cite: scipy), and cumulative distribution functions (CDFs). Histograms and KDEs are intuitive representations of how the values of a parameter are distributed, but they are also heavily affected by our choice in binning for the histogram and bandwidth for the KDE. We use a scalar estimator bandwidth of 0.5 dex for all KDEs in this section and Section [8](#sec:property comparison) for uniformity (Scott’s rule would result in bandwidths between 0.2 and 0.5 dex for the various distributions). CDFs are less intuitive for understanding how values of a property are distributed, but they are unaffected by binning and so are the most robust depiction of property distributions. When interpreting CDFs, a line further to the right of the plot indicates a distribution with larger values.

In Figure [3](#fig:global cluster distributions), we show the distributions of the fitted masses for both the full cluster population and for only the youngest (\<10 Myr) clusters, as well as distributions of the fitted ages of the clusters in each galaxy. We show histograms and KDEs in the left column and show CDFs in the right column. The cluster masses in NGC 1313 for both the full population and especially for the youngest clusters are skewed towards higher masses than in NGC 7793, further emphasizing the tendency towards more massive clusters in NGC 1313. The distribution of cluster ages in the two galaxies appears more similar, though NGC 1313 has slightly older clusters than NGC 7793.

![image](hist_CLmass_global.pdf) ![image](CDF_CLmass_global.png) ![image](hist_cmass_global_youngonly.png) ![image](CDF_cmass_global_youngonly.png) ![image](hist_age_global.pdf) ![image](CDF_age_global.png)

# Molecular Gas Structure Decomposition

To understand the properties of individual molecular gas structures, we use two different methods of emission decomposition to more robustly compare physical conditions between the two galaxies. One method is to use a dendrogram to hierarchically categorize the structures, and the other is to identify non-overlapping clumps. These segmentation methods are described in more detail below. Dendrograms are superior for examining the full spatial scale of molecular clouds in the region because they are able to capture the hierarchical nature of the gas, from large GMCs to smaller knots. However, dendrograms count emission multiple times and so they cannot be used for any counting statistics. We therefore use dendrograms in Sections [6](#sec:SL plots) and [7](#sec: virial plot) where we want to understand the full spatial scale of the clouds and multiply-counted emission is allowable. We use the non-overlapping clumps in Section [8](#sec:property comparison), which focuses on property distributions and so cannot include multiply-counted emission.

## Dendrogram Segmentation

We use the package `astrodendro` (cite: Rosolowsky08) to decompose the structures in each galaxy into dendrograms. This results in a hierarchical “tree” of structures that merge together at lower contour levels. The local maxima are called “leaves” and have no further substructure, while the larger merged structures are “branches” and “trunks”. Trunks are not bounded by any other structures. By convention, isolated structures that have no substructure and are also not bounded by any other structure are called leaves instead of trunks. We use the input parameters `min_value`=3$\sigma$, `min_delta`=2.5$\sigma$, and `min_npix`=2 beams, where `min_value` is the minimum intensity value of an identified emission peak, `min_delta` is the minimum intensity separation between structures merging, and `min_npix` is the minimum number of voxels in an identified structure. The breakdown of each type of dendrogram structure for each galaxy is shown in Table [\[tab:segmentation\]](#tab:segmentation).

## Clump Segmentation

We use the algorithm `quickclump` (cite: Sidorin17) to decompose the emission into clumps that have no overlap. This algorithm outputs a similar style of clump decomposition to `clumpfind` (cite: Williams95), for example. We used the input parameters `Tcutoff`=4$\sigma$, `dTleaf`=4$\sigma$, and `Npixmin`=2 beams (equal to 65 and 70 for NGC 1313 and NGC 7793, respectively). `Tcutoff` is the minimum intensity included in clump assignments, `dTleaf` is the minimum intensity differences for an emission peak to be considered a separate clump, and `Npixmin` is the minimum number of voxels in a clump. The number of clumps identified in each galaxy are shown in Table [\[tab:segmentation\]](#tab:segmentation).

# Calculating Cloud Properties

## Mass

We calculate the mass of each structure using a CO-to-H$_2$ factor, $X_\text{CO}$, where $X_\text{CO}$= $N_{H_2}$/$W_{CO}$, $N_{H_2}$ is the column density of H$_2$ in cm$^{-2}$ and $W_{CO}$ is the observed brightness of CO in K km s$^{-1}$. We use the $X_\text{CO(2-1)}$ calibration from (cite: Gong20), Table 3, Equation 3b, which determines the $X_\text{CO(2-1)}$ conversion factor between $N_{H_2}$ and CO(2-1) based on the peak brightness temperature of the clump ($T_\text{peak}$ in K), the beam size ($r_\text{b}$; 13 pc), and the metallicity ($Z$) with the equation

$$\begin{equation}
    X_{CO(2-1)} = (2.7\times10^{20}) T_\text{peak}^{-1.07+0.37\log{(r_\text{b})}}Z^{-0.5}r_\text{b}^{-0.13}.
    \label{eq:XCO}
\end{equation}$$

Using this equation, which is calibrated directly to the CO(2-1) line rather than CO(1-0), means that we do not need to assume a ratio of CO(2-1)/CO(1-0), which is known to vary across galaxies (cite: Koda12; Leroy22). For NGC 1313, we use an oxygen abundance of $12+\log{\text{(O/H)}}=8.4\pm0.1$ with no radial gradient in the galaxy (cite: WalshRoy97). NGC 7793 has a measured radial gradient of $12+\log{\text{(O/H)}}=8.572 - 0.054$ dex kpc$^{-1} \times R_\text{gal}$ (cite: Stanghellini15). Using a solar oxygen abundance of $12+\log{\text{(O/H)}}=8.69$ (cite: Asplund09), these abundances correspond to metallicities of $Z=0.51Z_\odot$ for NGC 1313 and a range of $Z=(0.56-0.76)Z_\odot$ for NGC 7793. Using the prescription from Eq. [\[eq:XCO\]](#eq:XCO) results in values of $X_\text{CO(2-1)}=(0.69-2.56)\times10^{20}$ cm$^{-2}$/(K km s$^{-1}$) for NGC 1313 and $X_\text{CO}$$=(0.64-2.65)\times10^{20}$ cm$^{-2}$/(K km s$^{-1}$) for NGC 7793.

We also consider the metallicity gradient measured for NGC 7793 by (cite: Grasha22), which instead finds $12+\log{\text{(O/H)}}=8.945 - 0.083$ dex kpc$^{-1} \times R_\text{gal}$, resulting in metallicities of $Z=(1.14-1.79)Z_\odot$ and values of $X_\text{CO(2-1)}=(0.43-1.83)\times10^{20}$ cm$^{-2}$/(K km s$^{-1}$). We find that the difference in metallicity prescription and resulting masses does not significantly affect any of the results in this paper and so we use the lower metallicities of (cite: Stanghellini15) throughout for NGC 7793. Hereafter, we refer to $X_\text{CO(2-1)}$ as $X_\text{CO}$.

We next calculate the mass of each structure using these calibrated $X_\text{CO}$ values to determine the H$_2$ column density, then multiply by the pixel size in cm$^2$ and sum over all pixels to get the mass of H$_2$. We then multiply this M$_{H_2}$ by a factor of 1.4 (which is the mean mass per hydrogen atom and assumes all the hydrogen is molecular) to get the total mass of the gas, $M$. We adopt a 10% error on the resulting masses due to the standard 10% ALMA flux calibration uncertainty (cite: Fomalont14), which we add in quadrature with the error from the measured rms noise (Table [1](#tab:observations)).

We also estimate a total mass of molecular gas in the observational footprint of each galaxy, using the total CO(2-1) emission multiplied by the respective average $X_\text{CO}$ measured for the clumps in each galaxy and multiplying by a factor of 1.4 as mentioned above. We find that NGC 7793 contains nearly twice the molecular mass as NGC 1313, with measured totals of $7.6\times10^6$ M$_\odot$ in NGC 1313 and $1.4\times10^7$ M$_\odot$ in NGC 7793. It is important to note that our observations do not cover the whole galaxy and we do not include 7m and total power data, so we are likely missing diffuse emission and these values should not be considered the total molecular masses of the galaxies. The ALMA observations do, however, cover a similar fraction of the galaxy to the LEGUS observations that clusters are derived from.

These values of observed molecular gas mass are low compared to those measured by PHANGS-ALMA in (cite: Leroy21), likely due to the smaller observational footprint and the missing diffuse gas emission since we only use the 12m array data. The CO(2-1) emission identified to be part of a clump structure accounts for approximately 82% of the total observed CO mass in NGC 1313 and 95% in NGC 7793, which implies that the molecular gas in NGC 1313 is more likely to be diffuse. The fact that NGC 1313 has nearly twice the neutral HI gas as NGC 7793 (see Table [\[tab:intro comparison\]](#tab:intro comparison)), but about half the molecular gas, suggests that there is an interesting difference in the balance between gas phases in these two galaxies and a thorough accounting of the total gas mass would be interesting for future work.

## Velocity Dispersion

We calculate the velocity dispersion for each structure by finding the intensity-weighted mean line profile and fitting a Gaussian, resulting in a fitted $\sigma_v$. We then deconvolve this $\sigma_v$ with the velocity channel width of the observations, 1.33 km s$^{-1}$, converted from FWHM to $\sigma$ with FWHM$=2.35\sigma$. The reported error in $\sigma_v$ comes from the error in the fitting method, propagated through the deconvolution. After deconvolving $\sigma_v$, measurements that were smaller than the channel width return non-number values and so are dropped from the analysis. We also remove from our analysis any structures that have a deconvolved $\sigma_v$ less than a tenth of the velocity resolution. Throughout this work, we also use the term “linewidth” to refer to $\sigma_v$.

## Radii

To determine the sizes of the structures, we fit ellipses to the half-power contours and take the two axes as the HWHM of the structure. We convert these HWHM measurements to a $\sigma_R$ by approximating $\sigma_R=$HWHM$\times2/2.35$, then multiply $\sigma_R$ by 1.91 to get an “effective radius” (cite: Solomon87) in each axis. We deconvolve each axis with the radius of the beam, 6.5 pc, then take the geometric mean of the axes to get a final $R$. The reported error in the size is determined by how non-circular the structure is, added in quadrature with a measurement error of half a pixel size, propagated through the deconvolution. After deconvolving the radii, measurements that were smaller than the beam size return non-number values and so are dropped from the analysis. We also remove from our analysis any structures that have a reported $R$ less than a tenth of the beam size.

Of the structures that were removed because they were below the resolution limits, there were 113 clumps and 88 dendrogram leaves in NGC 1313 and 166 clumps and 116 dendrogram leaves in NGC 7793. These removed structures account for 4% of the total clump mass in NGC 1313 and 2% in NGC 7793.

## Derived Quantities

From the measured mass, radius, and linewidth above, we calculate other properties of the structures, including the surface density, $\Sigma$, the virial parameter, $\alpha_\text{vir}$, the external pressure, $P_e$, and the free-fall time, $t_{ff}$. The surface density is simply the total mass divided by the structure’s area.

The virial parameter is the ratio between twice the cloud’s kinetic energy and its gravitational energy, so that a value of one indicates that the cloud is in virial equilibrium. While a negative total energy balance ($\alpha_\text{vir}$\<2) could be considered the threshold for a cloud’s boundedness, (cite: Dib07) demonstrate that the connection between boundedness and gravitational collapse is much more complicated, and clouds with a simple negative energy balance do not always collapse. By “collapse”, we mean the process by which parts of the cloud condenses and forms stars, while other parts of the cloud are dissipated. Furthermore, (cite: Zweibel90) show that more careful calculations of the virial parameter that take into account additional forces from external pressure and magnetic fields can alter the formula for virial equilibrium by factors of more than two.

Consequently, we take a more stringent threshold for gravitational collapse of $\alpha_\text{vir}$\<1. Values greater than two suggest that the cloud is not gravitationally bound and must either disperse or be constrained by an external pressure, while values less than one suggest that the cloud is dominated by gravity and will likely begin gravitational collapse. Values of $\alpha_\text{vir}$ between one and two should be interpreted cautiously. We calculate the virial parameter for each structure with the equation

$$\begin{equation}
    \alpha_\text{vir} = \frac{5 \sigma_v^2 R}{GM}.
    \label{eq:virial}
\end{equation}$$

Assuming a simplified case in which the cloud is in pressure equilibrium with the surrounding medium, the external pressure will be equal to the pressure at the edge of cloud defined by (cite: Elmegreen89) with the equation

$$\begin{equation}
    P_e = \frac{3\Pi M \sigma_v^2}{4\pi R^3},
    \label{eq:pressure}
\end{equation}$$

where $\Pi$ is defined as the ratio of the density at the edge of the cloud to the mean cloud density ($\rho_e = \Pi \langle\rho\rangle$), and here we take $\Pi=0.5$.

The free-fall time depends only on the density of the cloud and so we calculate it with the equation

$$\begin{equation}
    t_{ff} = \sqrt{\frac{3\pi}{32G\rho}} = \sqrt{\frac{\pi^2 R^3}{8GM}}.
    \label{eq:tff}
\end{equation}$$

Tables of all of these properties and their errors, for both galaxies and for both clumps and dendrogram structures, are given in Appendix [12](#append: prop tables). Given the large number of structures, we include only the first 5 entries as a demonstration of property values. The full tables are available as supplementary material.

# Size-Linewidth Relations

The sizes and linewidths of molecular cloud structures are expected to follow a power law relation (cite: Larson81) of the form

$$\begin{equation}
    \sigma_v = a_0 R^{a_1}.
\end{equation}$$

The intercept ($a_0$) and slope ($a_1$) of this relation have been measured in many different environments, though the most commonly cited value is that from (cite: Solomon87), which found $a_0 = 1.0\pm0.1$ and $a_1 = 0.5\pm0.05$ for clouds mapped in CO(1-0) in the disk of the Milky Way at 45$''$ resolution, where $\sigma_v$ is measured in km s$^{-1}$ and $R$ is measured in pc. The units of $a_0$ will vary with the value of $a_1$, but would be km s$^{-1}$ pc$^{-0.5}$ for a value of $a_1=0.5$. Since these units are dependent on $a_0$, we report the fitted values of $a_0$ without units.

Since (cite: Solomon87), other studies have measured the slope and intercept of this relation in a variety of environments and at many resolutions. In the Milky Way for example, (cite: Rice16) measure clouds with angular resolutions of 7.5’ and measure a slope of $a_1 = 0.52\pm0.03$ and (cite: MivilleDeschenes17) measure clouds with angular resolutions of 8.5’ and measure a slope of $a_1 = 0.63\pm0.3$, though neither of these studies deconvolve the sizes or linewidths with the beam and velocity channel sizes. (cite: Faesi16) measure clouds in the nearby spiral galaxy NGC 300 at 40 pc resolution with CO(2-1) and deconvolve their measurements, finding a slope of $a_1 = 0.52\pm0.2$. Steeper slopes have also been found in nearby galaxies, such as $a_1 = 0.6\pm0.1$ measured by (cite: Bolatto08) across many galaxies and with resolutions ranging from 6 to 120 pc with both CO(1-0) and CO(2-1), or $a_1 = 0.8\pm0.05$ measured by (cite: MAGMA) across the Large Magellanic Cloud (LMC) at 11 pc resolution with CO(1-0). Neither of these studies deconvolved size and linewidth measurements. Higher resolution studies (0.1-3 pc) in the LMC with CO(2-1) have performed deconvolution and found slopes ranging from $a_1 = 0.49$ to $a_1 = 0.78$ (cite: Nayak16; Indebetouw20; Wong22; Finn22). These widely varying measurements demonstrate how resolution, molecular tracer, and the method used to measure size and linewidth all have a large effect on the measured slope. Consequently, we focus instead on the fitted intercept of this relation, which still gives us information about the relative kinetic energy of the clouds across the full range of measured size scales.

We show the radii and velocity dispersions of the dendrogram structures in both galaxies with a fitted power law in Figure [4](#fig:SL intercept), where the power law is fit with orthogonal distance regression to take into account the error in both axes (cite: scipy). Due to the large number of clouds, plotting all data points results in the true distribution of points being self-obscured. We instead represent their distribution with a 2-D Gaussian KDE from `scipy.stats`, using the default Scott’s rule to determine the estimator bandwidth.

We fit the intercept only of a power-law relation by holding the slope constant at a fixed value of $a_1=0.5$. For NGC 1313, we fit a value of $a_0=0.41\pm0.01$, and for NGC 7793 we fit a value of $a_0=0.33\pm0.01$ (Figure [4](#fig:SL intercept)). The intercept of NGC 1313 is significantly higher than that of NGC 7793 by more than $3\sigma$, which suggests that NGC 1313 has more kinetic energy in its molecular clouds than NGC 7793. We also performed this fit with other values for the fixed slope in the power law to account for the wide range of fitted slopes (cite: Solomon87; Bolatto08; MAGMA; Faesi16; Nayak16; MivilleDeschenes17; Indebetouw20; Wong22; Finn22). Changing the fixed slope affects the values of the fitted intercepts, but not the conclusion that NGC 1313 has a significantly higher intercept and so more kinetic energy.

![](SL_intercept_global.png)

# Virialization

To investigate the gravitational balance of clouds in the two galaxies, we plot the velocity metric, $\sigma_v^2/R$, against the surface density, $\Sigma$, of each dendrogram structure. The results are shown in Figure [5](#fig:virial), along with a line indicating where clouds in virial equilibrium ($\alpha_\text{vir}$=1) would fall in the plot. Falling above the virial equilibrium line indicates that the clouds are super-virial and dominated by kinetic energy, while clouds below the line would be sub-virial and likely to begin forming stars. Being super-virial, especially when $\alpha_\text{vir}$\>2, implies that the clouds are likely to disperse due to their kinetic energy. However, the kinetic energy of clouds could also be enhanced if they already have begun free-fall collapse, in which case they would circumstantially fall along the line where $\alpha_\text{vir}$=2 in Figure [5](#fig:virial). The virial equilibrium line only considers the gravitational and kinetic energies of the cloud, but external pressure or magnetic fields could also affect the boundedness of the clouds by suppressing collapse or dispersal. These environmental effects have been shown to be important in simulations of GMCs in spiral galaxies (cite: Baba17).

![](VirialPlot_global.pdf)

Both galaxies fall mostly above the virial equilibrium line, suggesting that they are dominated by kinetic energy. Some clouds are consistent with being in free fall, which would enhance their observed kinetic energy. Alternatively, excess kinetic energy could indicate that many of the clouds in these galaxies are not gravitationally bound, or would require an external pressure to remain bound. This is not unexpected since many studies have found a large fraction of unbound molecular clouds in the Milky Way, nearby galaxy surveys, and simulations (cite: Goldsmith08; Liszt10; Dobbs11; Colombo14; MivilleDeschenes17; Sun18PHANGS; Rosolowsky21; Evans21).

While the two galaxies generally occupy the same parameter space in Figure [5](#fig:virial), NGC 1313 appears to have a larger scatter and have more clouds close to virial equilibrium. This could suggest that more of the clouds in NGC 1313 are close to collapsing into stars and star clusters, which could drive the larger numbers of clusters in NGC 1313 despite its fewer number of clouds. The larger scatter of NGC 1313 clouds towards the unbound parameter space also matches expectations of molecular clouds responding to galaxy interactions, which cause clouds to become unbound (cite: Pettitt18; Nguyen18). We investigate the boundedness of these structures more quantitatively by examining the spread in virial parameters, $\alpha_\text{vir}$, in Section [8](#sec:property comparison).

# Property Distribution Comparisons

We next investigate how the distributions of cloud properties compare between the two galaxies by looking at histograms, KDEs, and CDFs of the non-overlapping clump structures. In Figure [6](#fig:global distributions observed), we show the distributions of the three observed quantities (masses, radii, and linewidths) of the two galaxies. By eye, these distributions appear very similar, with NGC 7793 having a slightly broader distribution of masses at both the high and low mass end, and shifted to slightly larger radii.

![image](hist_mass_global.pdf) ![image](CDF_mass_global.png) ![image](hist_R_global.pdf) ![image](CDF_R_global.png) ![image](hist_sigv_global.pdf) ![image](CDF_sigv_global.png)

We see a bit more difference between the galaxies in the properties derived from $M$, $R$, and $\sigma_v$. We show the distributions of the virial parameter, surface density, external pressure, and free-fall time in Figure [7](#fig:global distributions derived). From these we see that NGC 1313 has more clouds at low $\alpha_\text{vir}$, which we expected from Section [7](#sec: virial plot), as well as higher surface densities, higher external pressures, and lower free-fall times.

![image](hist_alphavir_global.pdf) ![image](CDF_alphavir_global.png) ![image](hist_surfdens_global.pdf) ![image](CDF_surfdens_global.png) ![image](hist_Pe_global.pdf) ![image](CDF_Pe_global.png) ![image](hist_tff_global.pdf) ![image](CDF_tff_global.png)

To better quantify the difference between property distributions, we consider the two-sample version of both the Kolmogorov-Smirnoff (KS) test and the Anderson-Darling (AD) test, where the $p$-value indicates the probability that the two samples are pulled from the same distribution. A $p$-value of less than 5% is generally taken to be statistically significant. The KS test is most sensitive to the center of the distribution, while the AD test is more sensitive to the tails. However, because there are so many samples (in this case clouds), the comparison of every property for the two galaxies have $p$-values less than 5%, and most are also much less than 1%. This is likely an over-representation of how different the distributions truly are though because the sample sizes of clouds and clusters for the galaxies is so large. As discussed in (cite: Lazariv18), as the sample size becomes larger, KS and AD tests have increasingly higher power to discern small differences in the distributions. However, these tests do not take into account the error in the parameters, and so at large sample sizes, these tests can discern differences that are smaller than the error in the measurements, which we consider unreliable.

To combat overpowered statistical tests, we take random subsamples of the distribution for each galaxy and perform a KS and AD test, using a sample size instead of 65. After taking 1000 random subsamples, we report the average $p$-values for each property comparison as the bootstrapped result. We show these results for each property in Table [2](#tab:global ks tests). With this bootstrapped statistic, the only property that crosses a 5% threshold for significance for both KS and AD tests is the distributions of cluster masses, for both the full population and including only young clusters. This emphasizes how the cluster populations of the two galaxies appear significantly different, but none of the cloud properties match that level of difference.

We recommend caution when interpreting the bootstrapped KS and AD tests, since the $p$-value of the bootstrapped test does not necessarily indicate a statistically significant difference in the two populations. Choosing a sufficiently large sample size causes every property to appear significantly different between the two galaxies, and similarly a sufficiently small sample size makes no property have a statistically significant result. Rather, we use these results only to determine which properties show the biggest difference between the galaxies relative to the other properties.

|     Parameter      | KS $p$-value | AD $p$-value |
|:------------------:|:------------:|:------------:|
|    Cluster Mass    |     0.04     |     0.02     |
| Young Cluster Mass |     0.02     |     0.01     |
|    Cluster Age     |     0.23     |     0.09     |
|     Cloud Mass     |     0.46     |     0.20     |
|       Radius       |     0.37     |     0.16     |
|     Linewidth      |     0.46     |     0.20     |
|  Virial parameter  |     0.40     |     0.18     |
|  Surface density   |     0.34     |     0.15     |
|      Pressure      |     0.40     |     0.18     |
|   Free-fall time   |     0.20     |     0.10     |

: Boostrapped two-sample KS and AD test results between NGC 1313 and NGC 7793 global properties

These plots and tests indicate that overall, the cloud properties between the two galaxies are not particularly different. The greater number of massive clusters in NGC 1313 compared to NGC 7793 may be driven in part by higher surface densities and pressures. The lower virial parameters and free-fall times in NGC 1313 may suggest that more clouds are close to gravitational condensation and are likely to form stars more quickly and with greater efficiency, which could then result in more clusters being formed on this cloud scale.

![](DerivedPropertiesCorner.pdf)

To better understand if the highest-surface density clouds in NGC 1313 represent a high-density tail of collapsing clouds, we also plot all of the derived cloud properties against one another for both galaxies in Figure [8](#fig:derived props corner). These plots show that the surface density, pressure, and free-fall time are all closely correlated with one another, but the virial parameters are much less correlated with all three. This matches results from (cite: Sun22) that $\alpha_\text{vir}$ shows the least correlation with other clouds properties while most others are well-correlated, especially the surface density (which is unsurprising since these parameters are calculated from the same three measurements of $M$, $R$, and $\sigma_v$). The NGC 1313 structures with low virial parameters that may be closest to collapsing do not have particularly high or low surface densities or free-fall times, and slightly low external pressures. This would suggest then that the high surface densities in NGC 1313 are not high because the clouds are collapsing, although the higher surface density clouds also have lower free-fall times.

We note that the cloud masses found in this study have the unusual feature of being smaller than the maximum cluster masses seen in Figure [3](#fig:global cluster distributions). For young clusters, this difference is much smaller, with the maximum young cluster masses in NGC 7793 well below the maximum cloud masses, while the young cluster masses in NGC 1313 are comparable to the maximum cloud masses. This could be an indication that the star formation efficiency is much higher in NGC 1313 than it is in NGC 7793, which would align with recent findings by (cite: Polak23) that in simulations, higher mass star clusters form with a greater efficiency than lower mass star clusters. However, even with a higher than usual formation efficiency, we do not expect to see clusters more massive than the most massive clouds. This observation could be in part caused by missing flux at the largest size scales since our observations do not include ACA 7m or TP data. It could also be an indication that cloud and cluster masses are declining over time in the galaxies.

# Property Spatial Distributions

We next look for correlations between the clouds that are more gravitationally bound as seen in Figures [5](#fig:virial) and [7](#fig:global distributions derived) and the youngest of the identified clusters. In Figure [9](#fig:bound cloud maps), we show for each galaxy the locations of the clouds that have $\alpha_\text{vir}$$<1.5$ and the youngest clusters ($<10$ Myr), as well as the locations of all the clouds. Here we use the clump definitions rather than the dendrogram structures for the clouds. In NGC 7793, both the clouds and the clusters have a scattered spatial distribution, as would be expected for a flocculent galaxy. In NGC 1313, the clouds and clusters are primarily found in the spiral arms and the central bar, with smaller populations in the interarm regions.

![image](NGC1313_BoundCloudMap.png) ![image](NGC7793_BoundCloudMap.png)

To determine if the bound clouds are more closely associated with the young cluster population than the general cloud population, we create density maps of each and calculate the correlation coefficient between them. These density maps split the area of the galaxy into cells and count the number of objects (either clouds, bound clouds, or young clusters) in each cell. To mitigate the effects that our chosen cell size has on the results, we repeat this process with a variety of cell sizes ranging from 50 to 200 pixels in the ALMA maps (5$''$ to 20$''$, or 110 pc to 450 pc), as well as a variety of $\alpha_\text{vir}$ thresholds to determine cloud boundedness, ranging from values of 1 to 3.

In every case of cell size and $\alpha_\text{vir}$ threshold, the bound clouds are not more correlated with young clusters than the rest of the cloud population in either galaxy. Averaging over all the cell sizes and $\alpha_\text{vir}$ thresholds in NGC 1313, the correlation coefficient of the young clusters with the bound clouds is 0.24$\pm$0.06 and with the general cloud population is 0.32$\pm$0.05. In NGC 7793, the correlation coefficients are 0.36$\pm$0.18 and 0.44$\pm$0.13 for the bound clouds and all clouds, respectively. This suggests that the bound clouds are not more associated with young clusters than the general cloud population. NGC 7793 has slightly higher correlation coefficients than NGC 1313, though this difference is not statistically significant when we consider how the coefficients vary with different cell sizes and $\alpha_\text{vir}$ thresholds. This conclusion is the same if we consider the full cluster population as well instead of only the youngest clusters.

We also measure the spatial correlation coefficients between the average values of the various cloud properties and the presence of young clusters, the average masses of young clusters, and the total mass of young clusters. We use the same range of cell sizes as above to make maps of these properties and compute their correlation coefficients. In both galaxies, none of the properties show a strong correlation with any of the cluster metrics. The largest coefficient averaged across cell sizes was 0.33 for the correlation between cloud surface density in NGC 1313 and the density of clusters. This further demonstrates that no individual cloud property appears uniquely correlated to the star clusters.

![](CloudDistanceHistogram.png)

To further characterize the connection between the molecular clouds and the clusters, we plot histograms in Figure [10](#fig:cloud distance hist) of the distances between the clusters and centers of their nearest molecular clouds. We do this using the clump definitions and for both the full cluster populations as well as only the young cluster populations with ages \<10 Myr, including only clusters that fall within the ALMA observational footprints. In this figure, we see that the young clusters appear slightly closer to their nearest clouds than the full cluster population for both galaxies as we would expect. This agrees with the results of (cite: Grasha18) in NGC 7793. This difference between the young and old clusters’ distances to clouds is notably weaker than that found in M51 by (cite: Grasha19). The weakness of this trend in NGC 1313 and NGC 7793 agrees with our finding little correlation between the cloud properties and the presence of clusters. Including younger clusters that are closer to the generation of stars being formed by the clouds would likely result in a closer correlation.

Figure [10](#fig:cloud distance hist) shows a much larger difference in the cluster-cloud distances when comparing the two galaxies. Both the full cluster population and the young clusters of NGC 1313 are further from molecular clouds than those in NGC 7793. We believe the most likely explanation for this is the morphology of NGC 1313, where most of the molecular gas is swept up in the two large spiral arms while the star clusters get left behind, creating large separations between the clusters and clouds. The effect where star clusters get left behind by the spiral arms was demonstrated in other LEGUS galaxies by (cite: Shabani18). This effect is much smaller in NGC 7793 where the spiral arms are weaker and closer to each other.

# Discussion

Overall, the measured cloud properties in the two galaxies are surprisingly similar, especially given the difference in massive star cluster formation between the two. There are slight differences in the distributions of cloud masses, sizes, and linewidths, and these small differences compound to create larger differences in their densities and energy balances. This suggests that star formation variations can be driven by relatively small shifts in these properties, at least on the size scales measured here.

The primary differences that we find between the cloud properties in the two galaxies are that NGC 1313 has higher kinetic energies per spatial scale (Figure [4](#fig:SL intercept)), its clouds are closer to virial equilibrium (Figures [5](#fig:virial) and [7](#fig:global distributions derived)), and its clouds have higher surface densities, pressures, and shorter free-fall times (Figure [7](#fig:global distributions derived)). These slightly more extreme properties in NGC 1313 are likely what drive the higher rate of massive star cluster formation in the galaxy. We also see some evidence that NGC 1313 may have higher star formation efficiency than NGC 7793 based on the relative masses of the most massive clouds in each galaxy to the most massive young clusters in each galaxy.

Another difference in these two galaxies is in how the different gas phases appear to be balanced. NGC 7793 has significantly more molecular gas mass than NGC 1313 and nearly all of that molecular mass is accounted for with identified clouds, suggesting that NGC 1313 has more diffuse molecular gas than NGC 7793. NGC 1313 also has more than twice the neutral hydrogen gas and more than twice the star formation rate as NGC 7793. This suggests that the consumption time of the gas (roughly the molecular mass divided by SFR) is much shorter in NGC 1313 than in NGC 7793. This also mirrors the lower free-fall times seen in Figure [7](#fig:global distributions derived). It may be that the strong spiral density waves in NGC 1313 are important for perturbing molecular clouds to condense and begin star formation and then also shear these clouds apart to create greater quantities of diffuse molecular gas. Meanwhile in NGC 7793, the clouds are less likely to be perturbed and so can exist for a longer time in a dormant state without collapsing or being sheared apart.

However, it is still surprising how small the differences in cloud properties are when compared with the large difference in star formation outcomes. It is possible that this is because the LEGUS catalog primarily observes clusters that are optically visible and so have emerged from their natal material. It makes sense then that the cloud properties are not closely correlated with their presence as seen in Section [9](#sec:spatial distributions). (cite: Messa21) searched for embedded clusters in NGC 1313 in the near infrared and found that up to 60% of the clusters they identified are not accounted for in UV-optical catalogs. A search for embedded clusters in NGC 7793 was performed by (cite: Elmegreen19) using Spitzer data at 8 $\mu$m wavelengths. These embedded clusters would likely show a closer correlation with the molecular gas and its properties.

For future study, we recommend undertaking identical searches for embedded sources in the two galaxies so that the younger cluster populations can be directly compared. Such a study may show that the current generation of star clusters forming in the two galaxies are more similar than previous generations seen in the LEGUS catalogs, which would explain the relatively similar cloud properties. Using young, embedded clusters would also likely reveal better insights into which cloud properties are most closely correlated with ongoing star formation. This analysis could reveal a closer correlation of young, embedded clusters with virially bound clouds, which we would expect given the tendency towards collapse and the high dependence of star formation efficiency on the boundedness of clouds (cite: Kim21; Evans22).

We also note that in Figures [1](#fig:RGB images) and [9](#fig:bound cloud maps) that map the locations and ages of the LEGUS star clusters, it is clear that in NGC 1313 especially there are differences in the level of star formation among different regions in the galaxy. We examine how the cloud properties of these two galaxies vary by sub-galactic region in a follow-up study, (cite: Finn23b).

# Conclusions

We present a comparison of the molecular gas of two spiral galaxies from the LEGUS sample (cite: Calzetti15), NGC 1313 and NGC 7793, observed in CO(2-1) with ALMA. These two galaxies have similar stellar masses, metallicities, and star formation rates, yet NGC 1313 has formed significantly more massive star clusters in the last 10 Myr than NGC 7793. With observations of the same molecular tracer at the same physical resolution and the same sensitivity, we compare the properties of the molecular gas to understand what differences in gas conditions give rise to such different star formation outcomes. Our major results are summarized below.

- Comparing the clusters identified by LEGUS in the two galaxies, NGC 1313 has significantly more massive clusters ($>10^4$ M$_\odot$) and especially more young, massive clusters (\<10 Myr) than NGC 7793, even after correcting for each galaxy’s star formation rate and the area included by LEGUS. The mass distributions of these clusters (both the full population and only considering the young clusters) indicate that NGC 1313 is skewed towards more massive clusters than NGC 7793.

- Despite having less star formation, NGC 7793 has significantly more molecular gas by mass, and more identified cloud structures. This is in contrast to the greater amount of neutral hydrogen in NGC 1313, suggesting a strong difference in the gas phase balance in these two galaxies.

- We fit the intercept of a size-linewidth power law relation, holding the slope fixed at a value of $a_1=0.5$ to determine relative kinetic energies. NGC 1313 also has a significantly higher intercept than NGC 7793, suggesting that the kinetic energy of clouds in NGC 1313 are higher than in NGC 7793.

- Most of the clouds in both galaxies appear to be unbound and out of virial equilibrium based on plots of their surface densities against their velocity metrics. NGC 1313 has more clouds near virial equilibrium than NGC 7793.

- The distributions of cloud properties between the two galaxies show minimal differences, though the small differences in the observed masses, radii, and linewidths appear to compound into larger differences in the derived properties of virial parameter, surface density, pressure, and free-fall time.

- NGC 1313 has lower virial parameters and free-fall times and higher surface densities and pressures than NGC 7793. The higher surface densities of NGC 1313 are not correlated with low virial parameters, which would suggest that they are not a power-law tail caused by clouds with enhanced surface densities because they are collapsing.

- The most gravitationally bound clouds do not appear any more spatially correlated with young clusters than the general cloud population. We also find that none of the average cloud properties show a strong spatial correlation with the presence, average mass, or total mass of young star clusters. This may be because the clusters used in this study are too old to be associated with their natal molecular gas. Comparing the cloud properties to younger, embedded clusters in both galaxies would be an interesting focus of future work.

- The large difference in cluster formation between the two galaxies may be driven by perturbations from the spiral density waves in the arms of NGC 1313 causing slightly more extreme cloud properties and inducing collapse.

# Acknowledgements

This material is based upon work supported by the National Science Foundation Graduate Research Fellowship Program under Grant No. 1842490. Any opinions, findings, and conclusions or recommendations expressed in this material are those of the author(s) and do not necessarily reflect the views of the National Science Foundation.

KG is supported by the Australian Research Council through the Discovery Early Career Researcher Award (DECRA) Fellowship (project number DE220100766) funded by the Australian Government. KG is supported by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. MRK acknowledges funding from the Australian Research Council through Laureate Fellowship LF220100020.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00782.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

These data are associated with the HST GO Program 13364 (PI D. Calzetti). Support for this program was provided by NASA through grants from the Space Telescope Science Institute. Based on observations obtained with the NASA/ESA Hubble Space Telescope, at the Space Telescope Science Institute, which is operated by the Association of Universities or Research in Astronomy, Inc., under NASA contract NAS5-26555.

ALMA, HST (WFC3, ACS)

# Software

Pipeline-CASA51-P2-B v.40896 (cite: Davis21), CASA (cite: McMullin07), `astrodendro` (cite: Rosolowsky08), `quickclump` (cite: Sidorin17), Astropy (cite: astropy), Matplotlib (cite: matplotlib), NumPy (cite: numpy), SciPy (cite: scipy),

natexlab

(ref: Adamo17) Adamo, A., Ryon, J. E., Messa, M., et al. 2017, ApJ, 841, 131, doi: [`10.3847/1538-4357/aa7132`](http://doi.org/10.3847/1538-4357/aa7132)

(ref: Asplund09) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481, doi: [`10.1146/annurev.astro.46.060407.145222`](http://doi.org/10.1146/annurev.astro.46.060407.145222)

(ref: astropy) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Baba17) Baba, J., Morokuma-Matsui, K., & Saitoh, T. R. 2017, MNRAS, 464, 246, doi: [`10.1093/mnras/stw2378`](http://doi.org/10.1093/mnras/stw2378)

(ref: Bacchini19) Bacchini, C., Fraternali, F., Iorio, G., & Pezzulli, G. 2019, A&A, 622, A64, doi: [`10.1051/0004-6361/201834382`](http://doi.org/10.1051/0004-6361/201834382)

(ref: Bolatto08) Bolatto, A. D., Leroy, A. K., Rosolowsky, E., Walter, F., & Blitz, L. 2008, ApJ, 686, 948, doi: [`10.1086/591513`](http://doi.org/10.1086/591513)

(ref: Bothwell09) Bothwell, M. S., Kennicutt, R. C., & Lee, J. C. 2009, MNRAS, 400, 154, doi: [`10.1111/j.1365-2966.2009.15471.x`](http://doi.org/10.1111/j.1365-2966.2009.15471.x)

(ref: Brinchmann04) Brinchmann, J., Charlot, S., White, S. D., et al. 2004, MNRAS, 351, 1151, doi: [`10.1111/j.1365-2966.2004.07881.x`](http://doi.org/10.1111/j.1365-2966.2004.07881.x)

(ref: BrownGnedin21) Brown, G., & Gnedin, O. Y. 2021, MNRAS, 508, 5935, doi: [`10.1093/mnras/stab2907`](http://doi.org/10.1093/mnras/stab2907)

(ref: Calzetti15) Calzetti, D., Lee, J. C., Sabbi, E., et al. 2015, AJ, 149, doi: [`10.1088/0004-6256/149/2/51`](http://doi.org/10.1088/0004-6256/149/2/51)

(ref: Cardelli89) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245, doi: [`10.1086/167900`](http://doi.org/10.1086/167900)

(ref: CarignanPuch90) Carignan, C., & Puche, D. 1990, AJ, 100, 394, doi: [`10.1086/115523`](http://doi.org/10.1086/115523)

(ref: Colombo14) Colombo, D., Hughes, A., Schinnerer, E., et al. 2014, ApJ, 784, doi: [`10.1088/0004-637X/784/1/3`](http://doi.org/10.1088/0004-637X/784/1/3)

(ref: Davis21) Davis. 2024, in prep

(ref: deVaucouleurs63) de Vaucouleurs, G. 1963, ApJ, 137, 720, doi: [`10.1086/147550`](http://doi.org/10.1086/147550)

(ref: Dib07) Dib, S., Kim, J., Vázquez-Semadeni, E., Burkert, A., & Shadmehri, M. 2007, ApJ, 661, 262, doi: [`10.1086/513708`](http://doi.org/10.1086/513708)

(ref: Dicaire08) Dicaire, I., Carignan, C., Amram, P., et al. 2008, AJ, 135, 2038, doi: [`10.1088/0004-6256/135/6/2038`](http://doi.org/10.1088/0004-6256/135/6/2038)

(ref: Dobbs11) Dobbs, C. L., Burkert, A., & Pringle, J. E. 2011, MNRAS, 413, 2935, doi: [`10.1111/j.1365-2966.2011.18371.x`](http://doi.org/10.1111/j.1365-2966.2011.18371.x)

(ref: JDM13) Donovan Meyer, J., Koda, J., Momose, R., et al. 2013, ApJ, 772, doi: [`10.1088/0004-637X/772/2/107`](http://doi.org/10.1088/0004-637X/772/2/107)

(ref: Elmegreen89) Elmegreen, B. G. 1989, ApJ, 338, 178, doi: [`10.1086/167192`](http://doi.org/10.1086/167192)

(ref: Elmegreen19) Elmegreen, B. G., & Elmegreen, D. M. 2019, ApJS, 245, 14, doi: [`10.3847/1538-4365/ab4903`](http://doi.org/10.3847/1538-4365/ab4903)

(ref: Elmegreen84) Elmegreen, D. M., & Elmegreen, B. G. 1984, ApJS, 54, 127, doi: [`10.1086/190922`](http://doi.org/10.1086/190922)

(ref: Elmegreen14) Elmegreen, D. M., Elmegreen, B. G., Adamo, A., et al. 2014, ApJL, 787, L15, doi: [`10.1088/2041-8205/787/1/L15`](http://doi.org/10.1088/2041-8205/787/1/L15)

(ref: Evans21) Evans, Neal J., I., Heyer, M., Miville-Deschênes, M.-A., Nguyen-Luong, Q., & Merello, M. 2021, ApJ, 920, 126, doi: [`10.3847/1538-4357/ac1425`](http://doi.org/10.3847/1538-4357/ac1425)

(ref: Evans22) Evans, N. J., Kim, J.-G., & Ostriker, E. C. 2022, ApJL, 929, L18, doi: [`10.3847/2041-8213/ac6427`](http://doi.org/10.3847/2041-8213/ac6427)

(ref: Faesi16) Faesi, C. M., Lada, C. J., & Forbrich, J. 2016, ApJ, 821, 125, doi: [`10.3847/0004-637X/821/2/125`](http://doi.org/10.3847/0004-637X/821/2/125)

(ref: Finn22) Finn, M. K., Indebetouw, R., Johnson, K. E., et al. 2022, AJ, 164, 64, doi: [`10.3847/1538-3881/ac7aa1`](http://doi.org/10.3847/1538-3881/ac7aa1)

(ref: Finn23b) Finn, M. K., Johnson, K. E., Indebetouw, R., et al. 2024, ApJ

(ref: Fomalont14) Fomalont, E., van Kempen, T., Kneissl, R., et al. 2014, The Messenger, 155, 19

(ref: Gao16) Gao, Q., Wang, W., Liu, J.-F., & Yoachim, P. 2016, arXiv e-prints, arXiv:1602.07841, doi: [`10.48550/arXiv.1602.07841`](http://doi.org/10.48550/arXiv.1602.07841)

(ref: Goldsmith08) Goldsmith, P. F., Heyer, M., Narayanan, G., et al. 2008, ApJ, 680, 428, doi: [`10.1086/587166`](http://doi.org/10.1086/587166)

(ref: Gong20) Gong, M., Ostriker, E. C., Kim, C.-G., & Kim, J.-G. 2020, ApJ, 903, 142, doi: [`10.3847/1538-4357/abbdab`](http://doi.org/10.3847/1538-4357/abbdab)

(ref: Grasha17b) Grasha, K., Elmegreen, B. G., Calzetti, D., et al. 2017b, ApJ, 842, 25, doi: [`10.3847/1538-4357/aa740b`](http://doi.org/10.3847/1538-4357/aa740b)

(ref: Grasha18) Grasha, K., Calzetti, D., Bittle, L., et al. 2018, MNRAS, 481, 1016, doi: [`10.1093/MNRAS/STY2154`](http://doi.org/10.1093/MNRAS/STY2154)

(ref: Grasha19) Grasha, K., Calzetti, D., Adamo, A., et al. 2019, MNRAS, 483, 4707, doi: [`10.1093/mnras/sty3424`](http://doi.org/10.1093/mnras/sty3424)

(ref: Grasha22) Grasha, K., Chen, Q. H., Battisti, A. J., et al. 2022, ApJ, 929, 118, doi: [`10.3847/1538-4357/ac5ab2`](http://doi.org/10.3847/1538-4357/ac5ab2)

(ref: Hannon19) Hannon, S., Lee, J. C., Whitmore, B. C., et al. 2019, MNRAS, 490, 4648, doi: [`10.1093/mnras/stz2820`](http://doi.org/10.1093/mnras/stz2820)

(ref: numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Hart17) Hart, R. E., Bamford, S. P., Casteels, K. R. V., et al. 2017, MNRAS, 468, 1850, doi: [`10.1093/mnras/stx581`](http://doi.org/10.1093/mnras/stx581)

(ref: Hernandez22) Hernandez, S., Winch, A., Larsen, S., James, B. L., & Jones, L. 2022, AJ, 164, 89, doi: [`10.3847/1538-3881/ac7ebe`](http://doi.org/10.3847/1538-3881/ac7ebe)

(ref: matplotlib) Hunter, J. D. 2007, Computing in Science Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Hunter23) Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023, PASP, 135, 074501, doi: [`10.1088/1538-3873/ace216`](http://doi.org/10.1088/1538-3873/ace216)

(ref: Indebetouw20) Indebetouw, R., Wong, T., Chen, C. H. R., et al. 2020, ApJ, 888, 56, doi: [`10.3847/1538-4357/ab5db7`](http://doi.org/10.3847/1538-4357/ab5db7)

(ref: Kacharov18) Kacharov, N., Neumayer, N., Seth, A. C., et al. 2018, MNRAS, 480, 1973, doi: [`10.1093/mnras/sty1985`](http://doi.org/10.1093/mnras/sty1985)

(ref: Kim21) Kim, J.-G., Ostriker, E. C., & Filippova, N. 2021, ApJ, 911, 128, doi: [`10.3847/1538-4357/abe934`](http://doi.org/10.3847/1538-4357/abe934)

(ref: Koda09) Koda, J., Scoville, N., Sawada, T., et al. 2009, ApJ, 700, doi: [`10.1088/0004-637X/700/2/L132`](http://doi.org/10.1088/0004-637X/700/2/L132)

(ref: Koda12) Koda, J., Scoville, N., Hasegawa, T., et al. 2012, ApJ, 761, doi: [`10.1088/0004-637X/761/1/41`](http://doi.org/10.1088/0004-637X/761/1/41)

(ref: Koda23) Koda, J., Hirota, A., Egusa, F., et al. 2023, ApJ, 949, 108, doi: [`10.3847/1538-4357/acc65e`](http://doi.org/10.3847/1538-4357/acc65e)

(ref: Koribalski04) Koribalski, B. S., Staveley-Smith, L., Kilborn, V. A., et al. 2004, AJ, 128, 16. <http://www.atnf.csiro.au/research>

(ref: Koribalski18) Koribalski, B. S., Wang, J., Kamphuis, P., et al. 2018, MNRAS, 478, 1611, doi: [`10.1093/mnras/sty479`](http://doi.org/10.1093/mnras/sty479)

(ref: Larsen07) Larsen, S. S., Mora, M. D., Brodie, J. P., & Richtler, T. 2007, in Stellar Populations as Building Blocks of Galaxies, ed. A. Vazdekis & R. Peletier, Vol. 241, 435–439, doi: [`10.1017/S1743921307008708`](http://doi.org/10.1017/S1743921307008708)

(ref: Larson81) Larson, R. B. 1981, MNRAS, 194, 809, doi: [`10.1093/mnras/194.4.809`](http://doi.org/10.1093/mnras/194.4.809)

(ref: Lazariv18) Lazariv, T., & Lehmann, C. 2018, Goodness-of-Fit Tests for Large Datasets. [`https://arxiv.org/abs/1810.09753`](https://arxiv.org/abs/1810.09753)

(ref: Lee09) Lee, J. C., Gil de Paz, A., Tremonti, C., et al. 2009, ApJ, 706, 599, doi: [`10.1088/0004-637X/706/1/599`](http://doi.org/10.1088/0004-637X/706/1/599)

(ref: Leroy21) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: Leroy22) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2022, ApJ, 927, 149, doi: [`10.3847/1538-4357/ac3490`](http://doi.org/10.3847/1538-4357/ac3490)

(ref: Liszt10) Liszt, H. S., Pety, J., & Lucas, R. 2010, A&A, 518, A45, doi: [`10.1051/0004-6361/201014510`](http://doi.org/10.1051/0004-6361/201014510)

(ref: McMullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Messa21) Messa, M., Calzetti, D., Adamo, A., et al. 2021, ApJ, 909, 121, doi: [`10.3847/1538-4357/abe0b5`](http://doi.org/10.3847/1538-4357/abe0b5)

(ref: MivilleDeschenes17) Miville-Deschênes, M.-A., Murray, N., & Lee, E. J. 2017, ApJ, 834, 57, doi: [`10.3847/1538-4357/834/1/57`](http://doi.org/10.3847/1538-4357/834/1/57)

(ref: Mondal21) Mondal, C., Subramaniam, A., George, K., et al. 2021, ApJ, 909, 203, doi: [`10.3847/1538-4357/abe0b4`](http://doi.org/10.3847/1538-4357/abe0b4)

(ref: Muraoka16) Muraoka, K., Takeda, M., Yanagitani, K., et al. 2016, PASJ, 68, 18, doi: [`10.1093/pasj/psv134`](http://doi.org/10.1093/pasj/psv134)

(ref: Nayak16) Nayak, O., Meixner, M., Indebetouw, R., et al. 2016, ApJ, 831, 32, doi: [`10.3847/0004-637X/831/1/32`](http://doi.org/10.3847/0004-637X/831/1/32)

(ref: Nguyen18) Nguyen, N. K., Pettitt, A. R., Tasker, E. J., & Okamoto, T. 2018, MNRAS, 475, 27, doi: [`10.1093/mnras/stx3143`](http://doi.org/10.1093/mnras/stx3143)

(ref: OrozcoDuarte22) Orozco-Duarte, R., Wofford, A., Vidal-Garcı́a, A., et al. 2022, MNRAS, 509, 522, doi: [`10.1093/mnras/stab2988`](http://doi.org/10.1093/mnras/stab2988)

(ref: Peters94) Peters, W. L., Freeman, K. C., Forster, J. R., Manchester, R. N., & Ables, J. G. 1994, MNRAS, 269, 1025, doi: [`10.1093/mnras/269.4.1025`](http://doi.org/10.1093/mnras/269.4.1025)

(ref: Pettitt18) Pettitt, A. R., Egusa, F., Dobbs, C. L., et al. 2018, MNRAS, 480, 3356, doi: [`10.1093/mnras/sty2040`](http://doi.org/10.1093/mnras/sty2040)

(ref: Polak23) Polak, B., Mac Low, M.-M., Klessen, R. S., et al. 2023, arXiv e-prints, arXiv:2312.06509, doi: [`10.48550/arXiv.2312.06509`](http://doi.org/10.48550/arXiv.2312.06509)

(ref: Qing15) Qing, G., Wang, W., Liu, J.-F., & Yoachim, P. 2015, ApJ, 799, 19, doi: [`10.1088/0004-637X/799/1/19`](http://doi.org/10.1088/0004-637X/799/1/19)

(ref: Querejeta21) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, A&A, 656, A133, doi: [`10.1051/0004-6361/202140695`](http://doi.org/10.1051/0004-6361/202140695)

(ref: RadburnSmith11) Radburn-Smith, D. J., de Jong, R. S., Seth, A. C., et al. 2011, ApJS, 195, 18, doi: [`10.1088/0067-0049/195/2/18`](http://doi.org/10.1088/0067-0049/195/2/18)

(ref: RadburnSmith12) Radburn-Smith, D. J., Roškar, R., Debattista, V. P., et al. 2012, ApJ, 753, 138, doi: [`10.1088/0004-637X/753/2/138`](http://doi.org/10.1088/0004-637X/753/2/138)

(ref: Rice16) Rice, T. S., Goodman, A. A., Bergin, E. A., Beaumont, C., & Dame, T. M. 2016, ApJ, 822, 52, doi: [`10.3847/0004-637X/822/1/52`](http://doi.org/10.3847/0004-637X/822/1/52)

(ref: Rosolowsky21) Rosolowsky, E., Hughes, A., Leroy, A. K., et al. 2021, MNRAS, 502, 1218, doi: [`10.1093/mnras/stab085`](http://doi.org/10.1093/mnras/stab085)

(ref: Rosolowsky08) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ, 679, 1338, doi: [`10.1086/587685`](http://doi.org/10.1086/587685)

(ref: Ryon17) Ryon, J. E., Gallagher, J. S., Smith, L. J., et al. 2017, ApJ, 841, 92, doi: [`10.3847/1538-4357/aa719e`](http://doi.org/10.3847/1538-4357/aa719e)

(ref: Sabbi18) Sabbi, E., Calzetti, D., Ubeda, L., et al. 2018, ApJS, 235, 23, doi: [`10.3847/1538-4365/aaa8e5`](http://doi.org/10.3847/1538-4365/aaa8e5)

(ref: Sacchi19) Sacchi, E., Cignoni, M., Aloisi, A., et al. 2019, ApJ, 878, 1, doi: [`10.3847/1538-4357/ab1de1`](http://doi.org/10.3847/1538-4357/ab1de1)

(ref: SandageBrucato79) Sandage, A., & Brucato, R. 1979, AJ, 84, 472, doi: [`10.1086/112440`](http://doi.org/10.1086/112440)

(ref: Schinnerer13) Schinnerer, E., Meidt, S. E., Pety, J., et al. 2013, ApJ, 779, doi: [`10.1088/0004-637X/779/1/42`](http://doi.org/10.1088/0004-637X/779/1/42)

(ref: Shabani18) Shabani, F., Grebel, E. K., Pasquali, A., et al. 2018, MNRAS, 478, 3590, doi: [`10.1093/mnras/sty1277`](http://doi.org/10.1093/mnras/sty1277)

(ref: Sidorin17) Sidorin, V. 2017, Quickclump: Identify clumps within a 3D FITS datacube. [`http://ascl.net/1704.006`](http://ascl.net/1704.006)

(ref: SilvaVillaLarsen12) Silva-Villa, E., & Larsen, S. S. 2012, MNRAS, 423, 213, doi: [`10.1111/j.1365-2966.2012.20797.x`](http://doi.org/10.1111/j.1365-2966.2012.20797.x)

(ref: Solomon87) Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987, ApJ, 319, 730, doi: [`10.1086/165493`](http://doi.org/10.1086/165493)

(ref: Stanghellini15) Stanghellini, L., Magrini, L., & Casasola, V. 2015, ApJ, 812, doi: [`10.1088/0004-637X/812/1/39`](http://doi.org/10.1088/0004-637X/812/1/39)

(ref: Stuber23) Stuber, S. K., Schinnerer, E., Williams, T. G., et al. 2023, A&A, 676, A113, doi: [`10.1051/0004-6361/202346318`](http://doi.org/10.1051/0004-6361/202346318)

(ref: Sun18PHANGS) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860, 172, doi: [`10.3847/1538-4357/aac326`](http://doi.org/10.3847/1538-4357/aac326)

(ref: Sun20) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020, ApJL, 901, L8, doi: [`10.3847/2041-8213/abb3be`](http://doi.org/10.3847/2041-8213/abb3be)

(ref: Sun22) Sun, J., Leroy, A. K., Rosolowsky, E., et al. 2022, ApJ, 164, 43, doi: [`10.3847/1538-3881/ac74bd`](http://doi.org/10.3847/1538-3881/ac74bd)

(ref: Tikhonov16) Tikhonov, N. A., & Galazutdinova, O. A. 2016, Astronomy Letters, 42, 428, doi: [`10.1134/S1063773716070082`](http://doi.org/10.1134/S1063773716070082)

(ref: Turner21) Turner, J. A., Dale, D. A., Lee, J. C., et al. 2021, MNRAS, 502, 1366, doi: [`10.1093/mnras/stab055`](http://doi.org/10.1093/mnras/stab055)

(ref: scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Vlajic11) Vlajić, M., Bland-Hawthorn, J., & Freeman, K. C. 2011, ApJ, 732, 7, doi: [`10.1088/0004-637X/732/1/7`](http://doi.org/10.1088/0004-637X/732/1/7)

(ref: WalshRoy97) Walsh, J. R., & Roy, J. R. 1997, MNRAS, 288, 726, doi: [`10.1093/mnras/288.3.726`](http://doi.org/10.1093/mnras/288.3.726)

(ref: Whitmore23) Whitmore, B. C., Chandar, R., Lee, J. C., et al. 2023, MNRAS, 520, 63, doi: [`10.1093/mnras/stad098`](http://doi.org/10.1093/mnras/stad098)

(ref: Williams95) Williams, J. P., Blitz, L., & Stark, A. A. 1995, ApJ, 451, 252, doi: [`10.1086/176216`](http://doi.org/10.1086/176216)

(ref: MAGMA) Wong, T., Hughes, A., Ott, J., et al. 2011, ApJS, 197, 16, doi: [`10.1088/0067-0049/197/2/16`](http://doi.org/10.1088/0067-0049/197/2/16)

(ref: Wong22) Wong, T., Oudshoorn, L., Sofovich, E., et al. 2022, ApJ, 932, 47, doi: [`10.3847/1538-4357/ac723a`](http://doi.org/10.3847/1538-4357/ac723a)

(ref: Zackrisson11) Zackrisson, E., Rydberg, C.-E., Schaerer, D., Östlin, G., & Tuli, M. 2011, ApJ, 740, 13, doi: [`10.1088/0004-637X/740/1/13`](http://doi.org/10.1088/0004-637X/740/1/13)

(ref: Zweibel90) Zweibel, E. G. 1990, ApJ, 348, 186, doi: [`10.1086/168226`](http://doi.org/10.1086/168226)

# Cloud Property Tables

We include demonstrative tables of the properties derived in Section [5](#sec:properties), where only the first 5 entries are shown. The full tables are available as supplementary materials with the paper. We include tables for NGC 1313 dendrogram structures (Table [\[tab:ngc1313 dendro props\]](#tab:ngc1313 dendro props)) and clumps (Table [\[tab:ngc1313 clump props\]](#tab:ngc1313 clump props)), and NGC 7793 dendrogram structures (Table [\[tab:ngc7793 dendro props\]](#tab:ngc7793 dendro props)) and clumps (Table [\[tab:ngc7793 clump props\]](#tab:ngc7793 clump props)).

</paper>

Write the methods card for this paper.