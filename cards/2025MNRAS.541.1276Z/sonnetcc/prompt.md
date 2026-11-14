# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025MNRAS.541.1276Z\sonnetcc\reply.txt

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
 "bibcode": "2025MNRAS.541.1276Z",
 "title": "The most massive star clusters in molecular clouds: insights from the integrated cloud-wide initial mass function (ICIMF) theory",
 "year": 2025,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Zhou, J. W.",
 "n_authors": 3,
 "arxiv_id": "2506.23096",
 "doi": "10.1093/mnras/staf1070",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S",
  "2013.1.00803.S",
  "2013.1.01161.S",
  "2015.1.00121.S",
  "2015.1.00782.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2016.1.00386.S",
  "2017.1.00392.S",
  "2017.1.00766.S",
  "2017.1.00886.L",
  "2018.1.00484.S",
  "2018.1.01321.S",
  "2018.1.01651.S",
  "2018.A.00062.S",
  "2019.2.00129.S"
 ]
}
```

Paper text:
<paper>
# The most massive star clusters in molecular clouds: Insights from the integrated cloud-wide initial mass function (ICIMF) theory

## Abstract

The combination of the high-resolution ALMA, JWST and HST observations provides unprecedented insights into the connection between individual molecular clouds and their internal stellar populations in nearby galaxies. The molecular clouds in five nearby galaxies were identified based on the integrated intensity maps of CO (2$-$1) emission from ALMA observations. We used the JWST 21 $\mu$m data to estimate the star formation rate (SFR) surface density of the clouds and calculate the masses of the embedded stellar populations in the clouds. After matching the star cluster and stellar association catalogs derived from the HST observations with the identified molecular clouds, we found clear correlations between the physical parameters of molecular clouds and their internal stellar populations. Based on the masses of the total stellar populations and their corresponding clouds, we obtained a typical value of the cloud-scale star formation efficiency (SFE), $\approx$1.4%. The mass of the most massive cluster ($M_{\rm cluster, max}$) in a cloud is positively proportional to the mass ($M_{\rm cloud}$), the column density, the SFR sand the SFR surface density of the cloud. The observed $M_{\rm cluster, max}$-$M_{\rm cloud}$ relation can be interpreted theoretically on the basis of the integrated cloud-wide IMF (ICIMF) theory, which provides a quantitative framework for understanding the correlations between molecular clouds and their internal stellar populations.

– ISM: clouds – galaxies: clusters – galaxies: star formation

# Introduction

![](g333/layer.png)

![](g333/case.pdf)

Galaxies act as stellar factories in the universe, producing stars through the gravitational collapse of the densest regions within molecular clouds in the interstellar medium (ISM). Molecular clouds are widely distributed within galaxies and serve as localized sites for star formation. Each molecular cloud typically contains multiple clumps, which are the local sites of star formation within the cloud and the precursors of embedded star clusters (cite: Dib2012ApJ-758; Miville2017-834; Rosolowsky2021-502; Urquhart2022-510; Zhou2023-676). The hierarchical structure of molecular gas in a galaxy determines the spatial distribution of stellar populations (cite: Gouliermis2015MNRAS-452; Elmegreen2014-787; Grasha2017-840; Chevance2023-534). Young clusters with different ages constitute a cluster population within the parent molecular cloud. The evolution of the molecular cloud is closely related to the formation and evolution of the internal star clusters. The star clusters become fully exposed after the molecular cloud is dispersed by feedback from the star clusters (cite: Kim2016-819; Kruijssen2019-569; Chevance2022-509; Watkins2023-676; Zhou2024-682-173).

It has been suggested that most if not all observed stars originate from embedded clusters (cite: Kroupa1995a-277; Kroupa1995b-277; Lada2003-41; Kroupa2005-576; Megeath2016-151; Dinnbier2022-660). Based on this viewpoint, the integrated galaxy-wide initial mass function (IGIMF) theory has been developed to calculate galaxy-wide IMFs, starting with the IMF that is observationally constrained at the star cluster scale (cite: Kroupa2003-598; Kroupa2013-115; Yan2017-607; Jerabkova2018-620; Dib2022-666; Haslbauer2024arXiv). The IMFs assembled in star-forming regions combine to create the IMF of the entire galaxy. This process involves first generating a series of embedded star clusters from the embedded cluster mass function (ECMF), then producing a series of stars for each embedded cluster from the IMF, and finally summing the stars from all clusters to construct the galaxy-wide IMF.

Star clusters first form in molecular clouds. Molecular clouds, serving as intermediaries between star clusters and the galaxy, should also be incorporated into the IGIMF theory. Molecular clouds and their internal star clusters could be quantitatively characterized using a localized IGIMF theory, which can be called the integrated cloud-wide initial mass function (ICIMF) theory. Fig.[1](#layer) illustrates the correspondence between hierarchical gas structures (star-forming regions) and hierarchically integrated IMFs, providing a depiction of their relationship.

With high-resolution observations across various wavelengths, we are now able to break down star formation into individual molecular clouds in nearby galaxies (cite: Leroy2021-257; Leroy2021-255; Lee2022-258; Emsellem2022-659; Lee2023-944). High-resolution CO imaging data from ALMA (Atacama Large Millimeter/submillimeter Array) observations enable systematic studies of molecular clouds across nearby galaxies. The JWST (James Webb Space Telescope) and HST (Hubble Space Telescope) observations can reveal embedded clusters, young star clusters, and stellar associations within molecular clouds (cite: Gouliermis2017-468; Whitmore2021-506; Thilker2022-509; Larson2023-523; Levy2024arXiv). The combination of these high-resolution observations provides an unprecedented look at the connection between individual clouds and the stellar populations (cite: Turner2022-516). Some examples of multi-band observations are shown in Fig.[2](#case). In this work, we first look for correlations between the physical parameters of molecular clouds and their internal stellar populations, and then use the ICIMF theory to interpret the observed correlations.

# Data and catalogs

## Star cluster and stellar association catalogs

The catalogs for compact clusters and multi-scale associations across five galaxies (NGC 1433, NGC 1566, NGC 1559, NGC 3351 and NGC 3627) are being made available as the DR3 release of the PHANGS-HST survey. A detailed description of these catalogs can be found in (cite: Lee2022-258; Whitmore2021-506; Thilker2022-509; Larson2023-523). Based on the classification technique, there are two kinds of compact cluster catalogs, i.e. human classified and machine learning (ML) classified. The ML classified technique greatly increases the number of identified star clusters within each galaxy, allowing for a much better statistical analysis. Therefore, we primarily use the machine learning-classified catalogs in this work, while also employing the human-classified cluster catalogs to verify the results. According to NUV–U–B–V–I photometry of the star clusters, the publicly available spectral energy distribution (SED) fitting code CIGALE was used to characterize their physical properties, such as their age, mass, and reddening (cite: Turner2021-502). For the stellar association catalogs, as described in (cite: Larson2023-523), they firstly selected point sources from the DOLPHOT source catalogs (cite: Thilker2022-509) to serve as ‘tracer’ stars, using both the HST NUV-band (F275W) and V-band (F555W). The positions of ‘tracer’ stars are used to create star density maps on which they used the watershed algorithm to identify stellar associations. All light from within the bounds of an association is used in the photometry for that structure. The measured five-band NUV, U, V, B, I photometry gives the total flux of the structure. Using the SED fitting (cite: Turner2021-502), they estimated the ages, masses, and reddening of the stellar associations according to the total flux. The associations are identified at three physical scale levels (16 pc, 32 pc and 64 pc) for all five galaxies. The NUV-band selection primarily identifies the youngest stellar populations, while the V-band traces both young and old stars, enabling the detection of stellar associations across a wider range of ages. As described in (cite: Larson2023-523), the V-band selection identifies more associations at all scale levels. Most of the associations are identified through V-band selection, with 75-85 percent of the young associations found in the NUV-band also overlapping with the larger set of associations detected in the V-band.

In this work, we exclude clusters and associations whose estimated masses are less than their mass estimation errors, as their masses are not well determined. Considering that the typical survival timescale of GMCs is 10$-$30 Myr (cite: Chevance2021; Kim2022-516), an age cut of 20 Myr is imposed to eliminate chance superpositions between older stellar populations and molecular clouds.

## CO (2-1) cube and 21 $\mu$m map

|          |         |           |             |             |             |
|:--------:|:-------:|:---------:|:-----------:|:-----------:|:-----------:|
|          | D (Mpc) | $i$ (deg) | angular (") | linear (pc) | linear (pc) |
|          |         |           |    ALMA     |    ALMA     |    JWST     |
| NGC 1433 |  18.6   |   28.6    |    1.10     |    99.1     |    58.6     |
| NGC 1559 |  19.4   |   65.4    |    1.25     |    117.5    |      –      |
| NGC 1566 |  17.7   |   29.5    |    1.25     |    107.6    |    55.7     |
| NGC 3351 |  10.0   |   45.1    |    1.46     |    70.7     |    31.5     |
| NGC 3627 |  11.3   |   57.3    |    1.63     |    89.2     |    35.6     |
|          |         |           |             |             |             |

For the five galaxies, we used the combined 12m+7m+TP PHANGS-ALMA CO (2$-$1) data cubes to investigate gas kinematics and dynamics, which have a spectral resolution of 2.5 km s$^{-1}$. We also use the JWST 21 $\mu$m (F2100W) maps from the PHANGS-JWST survey. The full width at half maximum (FWHM) of the original F2100W point spread function (PSF) is $\approx$0.65" (cite: Williams2024-273). The angular resolutions or linear resolutions of these datasets are listed in Table.[\[data\]](#data). Overviews of the PHANGS-ALMA and PHANGS-JWST surveys’ science goals, sample selection, observation strategy, and data products are described in (cite: Leroy2021-257; Leroy2021-255; Lee2023-944). All the data are available on the PHANGS team website [^4].

# Results and discussion

## Identification of molecular clouds

|          |        |        |       |       |
|:--------:|:------:|:------:|:-----:|:-----:|
|          | leaves | fitted | type1 | type3 |
| NGC 1433 |  187   |  178   |  175  |   3   |
| NGC 1559 |  262   |  253   |  246  |   7   |
| NGC 1566 |  588   |  559   |  540  |  19   |
| NGC 3351 |  271   |  264   |  263  |   1   |
| NGC 3627 |  471   |  458   |  414  |  44   |
|  total   |  1779  |  1712  | 1638  |  74   |
|          |        |        |       |       |

: Leaf structures in each galaxy, see Sec.[3.1.1](#comp) for more details.

![](g333/co.pdf)

For the five galaxies considered in this work, we conducted a direct identification of hierarchical (sub-)structures based on the 2D intensity maps. As described in (cite: Rosolowsky2008-679), the dendrogram algorithm decomposes density or intensity data into hierarchical structures called leaves, branches, and trunks. Using the *astrodendro* package [^5], there are three major input parameters for the dendrogram algorithm: *min_value* for the minimum value to be considered in the dataset, *min_delta* for a leaf that can be considered as an independent entity, and *min_npix* for the minimum area of a structure. For the CO (2$-$1) data cube, there are two types of Moment 0 maps (strictly masked and broadly masked) in the data product of the PHANGS-ALMA survey [^6]. The strictly masked maps only include emissions that are identified as signals with high confidence in the data cube, which might filter out the relatively faint structures. The broadly masked maps offer superior completeness and cover larger areas compared to the strictly masked maps. However, due to the inclusion of more regions with faint emissions or areas close to bright emissions, they tend to be noisier and may contain false positives. In order to ensure the reliability of the identified structures and because we are only interested in local dense structures, we select the strictly masked Moment 0 maps to identify structures. Since all the retained structures on the strictly masked Moment 0 maps are reliable, we only require the smallest area of the identified structure be larger than 1 beam area. We do not set additional parameters in the algorithm to minimize the dependence of the identification on parameter settings. Finally, the numbers of leaf structures in the five galaxies are listed in Table.[1](#type). In Fig.[3](#co), the CO structures identified by the dendrogram algorithm exhibit a strong correspondence with the background intensity maps. For a structure with an area $A$ and a total integrated intensity $I_{\rm CO}$, the mass of the structure can be calculated by $$\begin{equation}
M_{\rm cloud} = \alpha^{2-1}_{\rm CO} \times I_{\rm CO} \times A,
\label{mass}
\end{equation}$$ where $\alpha^{2-1}_{\rm CO} \approx 6.7~\rm M_{\odot} \rm pc^{-2} (\rm K~km~s^{-1})^{-1}$ (cite: Leroy2022-927).

For the 21 $\mu$m emission, apart from the *min_npix*= 1 beam area, we also take the values of *min_value*= 3\*$\sigma_{\rm rms}$, *min_delta* = 3\*$\sigma_{\rm rms}$, where $\sigma_{\rm rms}$ is the background intensity. We first retained as many structures as possible using these lower standards, then eliminated the diffuse structures, as done in (cite: Zhou2024MNRAS.tmp.2058Z).

The algorithm characterizes the morphology of each structure by approximating it as an ellipse. Within the dendrogram, the root mean square (rms) sizes (second moments) of the intensity distribution along the two spatial dimensions define the long and short axes of the ellipse, denoted as $a$ and $b$. As described in (cite: Zhou2024-682), the initial ellipse with $a$ and $b$ is smaller, so a multiplication factor of two is applied to appropriately enlarge the ellipse. Then the effective physical radius of an ellipse is $R_{\rm eff}$ =$\sqrt{2a \times 2b}*D$, where $D$ is the distance of the galaxy.

### Velocity component

For the identified molecular structures, we extracted the average spectrum of each structure to investigate its velocity components and gas kinematics. Large-scale velocity gradients from the galaxy’s rotation contribute to the non-thermal velocity dispersion. To address this, before extracting the average spectra, we removed the bulk motion due to galaxy rotation by creating gas dynamical models using the Kinematic Molecular Simulation (KinMS) package (cite: Davis2013-429). According to the averaged spectra, 67 structures with poor line profiles were eliminated. Then, following the procedure described in (cite: Zhou2024-682-128), we fitted the averaged spectra of 1712 leaf structures individually using the fully automated Gaussian decomposer `GAUSSPY+` algorithm (cite: Lindner2015-149; Riener2019-628). As shown in Table.[1](#type), $\approx$96% structures have a single velocity component, i.e. type1 (following the nomenclature introduced in (cite: Zhou2024-682-128)). For some structures with more than one velocity component (i.e. type3), as discussed in (cite: Zhou2024-682-173), we treat type3 structures as independent structures like type1 structures, but with more complex gas motions.

## Correlations between molecular clouds and their internal stellar populations

### Stellar associations

![](g333/assoc.pdf)

Since the beam sizes of all five galaxies are more than 64 pc, we only focus on the associations identified on the scale level of 64 pc. If the distances between the center coordinates of the associations and a molecular cloud are less than the effective radius of the cloud, we distribute these associations to the cloud. If the associations from the V-band selection and the NUV-band selection overlap, we select the one with a larger area which includes more stars. Actually, the association from the V-band selection always has a larger area, as described in Sec.[2.1](#catalog). Finally, we added the masses of all independent associations in each cloud. Combining the data of all five galaxies together, Fig.[4](#assoc)(a) shows a clear correlation between the mass of the cloud and the total mass of the associations in the cloud, i.e. the $M_{\rm assoc, tot}$-$M_{\rm cloud}$ relation. For each cloud, we also singled out the most massive association with the mass $M_{\rm assoc, max}$. As displayed in Fig.[4](#assoc)(b), the $M_{\rm assoc, max}$-$M_{\rm cloud}$ and $M_{\rm assoc, tot}$-$M_{\rm cloud}$ relations are very similar, and this is because one cloud typically corresponds to one association identified at the 64 pc level.

### Star clusters

![](g333/cluster.pdf)

; (c) The correlation between the column density of the cloud and $M_{\rm cluster, max}$, i.e. the $M_{\rm cluster, max}$-$N_{\rm cloud}$ relation; (d) The correlation between the effective radius of the cloud and $M_{\rm cluster, max}$. $r$ is the Pearson correlation coefficient.

Using the same criterion, if the distances between the center coordinates of the clusters and a molecular cloud are less than the effective radius of the cloud, we distribute these clusters to the cloud. Generally, one cloud will contain multiple star clusters. We first focus on the most massive one. Fig.[5](#cluster)(a) displays a clear correlation between the mass of the cloud and the mass of the most massive cluster in the cloud, i.e. the $M_{\rm cluster, max}$-$M_{\rm cloud}$ relation. Moreover, clear correlations are also found between the column density and the size of the cloud ($N_{\rm cloud}$ and $R_{\rm eff}$) and $M_{\rm cluster, max}$, i.e. the $M_{\rm cluster, max}$-$N_{\rm cloud}$ and $M_{\rm cluster, max}$-$R_{\rm eff}$ relations.

### Total stellar populations

![](g333/total.pdf)

A molecular cloud may contain only star clusters (case1), only stellar associations (case2), or both star clusters and stellar associations (case3). For case3, the clusters may be inside the associations or independent of them. To estimate the total mass of the stellar populations within the cloud, we need to sum the masses of both the independent clusters and the associations. To avoid redundant calculations of mass, the clusters that fall within the associations should be excluded. Similarly, if the distances between the center coordinates of the clusters and an association are less than the effective radius of the association, we distribute these clusters to the association and do not count them. Fig.[6](#total) displays a clear correlation between the mass of the cloud and the mass of the total stellar populations in the cloud, i.e. the $M_{\rm *,tot}$-$M_{\rm cloud}$ relation.

## Embedded stellar populations

![](g333/emb.pdf)

![](g333/SFR.pdf)

The embedded stellar populations in molecular clouds may not be observed in the PHANGS-HST survey, which is more sensitive to the exposed stellar populations. As done in (cite: Zhou2024MNRAS.tmp.2058Z), the JWST 21 $\mu$m emission was used to estimate the total mass of the embedded stellar populations in a cloud. This method gives quite comparable masses with those obtained from the SED fitting, as compared in (cite: Zhou2024MNRAS.tmp.2058Z). Using the prescriptions described in (cite: Leroy2021-257), the WISE 22 $\mu$m data can be used to calculate the local star formation rate (SFR) surface density via $$\begin{equation}
    \frac{\Sigma_{\rm SFR}}{\rm M_{\odot}~yr^{-1}~kpc^{-2}} = 3.8\times10^{-3} \left(\frac{I_{\rm 22 \mu m}}{\rm MJy~sr^{-1}}\right)\mathrm{cos}i,
    \label{}
\end{equation}$$ where $i$ is the inclination angle of the galaxy. Here, we used the JWST 21 $\mu$m data to estimate the SFR surface density. For NGC 628, (cite: Kim2023-944) defined the duration of the embedded phase of star formation as the time during which CO and 21 $\mu$m emissions are found to be overlapping, i.e. $t_{\mathrm{fb, 21 \mu m}}$, and they obtained $t_{\mathrm{fb, 21 \mu m}} \approx$ 5.1 Myr. We assume this timescale is also applicable to the five galaxies in this work. Following the same method as in (cite: Zhou2024MNRAS.tmp.2058Z), the spatial separation between 21 $\mu$m and CO emission peaks is used to estimate the typical age ($t_{\rm age}$) of the embedded stellar populations in the cloud. Then, the total mass of the embedded stellar populations is $$\begin{equation}
M_{\rm *, tot, emb}=\Sigma_{\rm SFR} \times A \times t_{\rm age},
    \label{}
\end{equation}$$ where $A$ is the cloud’s area. Here, we consider all 21 $\mu$m emission enclosed in the cloud. The same method is also applied to calculate the mass of bright 21 $\mu$m sources ($M_{\rm cluster, emb}$) identified in Sec.[3.1](#dendro), which represent the embedded clusters. As shown in Fig.[7](#emb), both $M_{\rm *, tot, emb}$ and $M_{\rm cluster, max, emb}$ are systematically smaller than the corresponding $M_{\rm *, tot}$ and $M_{\rm cluster, max}$ observed in the PHANGS-HST survey. This suggests a short duration of the embedded phase. (cite: Kim2021-504) found that the embedded phase of star formation in six nearby galaxies lasts for 2$-$7 Myr and constitutes 17$-$47 percent of the cloud lifetime.

Fig.[8](#SFR)(a) and (b) show clear correlations between the SFR and the $\Sigma_{\rm SFR}$ of the cloud and the mass of the most massive cluster in the cloud, i.e. the $M_{\rm cluster, max}$-${\rm SFR}_{\rm cloud}$ relation and the $M_{\rm cluster, max}$-$\Sigma_{\rm SFR, cloud}$ relation.

## Star formation efficiency

![](g333/SFE.pdf)

The star formation efficiency (SFE) of each cloud is defined as $$\begin{equation}
{\rm SFE} \approx \frac{M_{\rm *,tot}}{M_{\rm cloud}+M_{\rm *,tot}+M_{\rm I}}, 
\end{equation}$$ where $M_{\rm I}$ is the mass of the ionized gas. First, we need to assess the significance of $M_{\rm I}$ in the total mass budget. Based on the HII region catalog in (cite: Santoro2022-658; Groves2023-520), if the distances between the center coordinates of the HII regions and a molecular cloud is less than the effective radius of the cloud, we distributed these HII regions to the cloud. Generally, HII regions associated with molecular clouds are compact. Thus, we used Equation 5 of (cite: Egorov2023-678) to calculate the mass of the ionized gas and this is given by

$$\begin{equation}
    \label{eq:mass_flux_2}
    M_{\rm I} \approx 29.3 \frac{F{(\rm H\alpha)_{tot}}}{\rm 10^{-16}\ erg\ s^{-1}\ cm^{-2}} \left(\frac{D}{\rm Mpc}\right)^2\left(\frac{n_{\rm e}}{\rm cm^{-3}}\right)^{-1} M_\odot,
    
\end{equation}$$ where $F{(\rm H\alpha)_{tot}}$ is the total $H_{\alpha}$ flux in a HII region. We also use Equation 6 of (cite: Egorov2023-678) to calculate the volume-averaged electron density, $$\begin{equation}
\label{eq:dens_hii_vol}
    n_{\rm e} \approx 1.36 \times10^{-16}\left(\frac{L({\rm H\alpha})}{\rm erg\ s^{-1}}\right)^{0.5}\left(\frac{R_{\rm eff}}{\rm pc}\right)^{-1.5} {\rm cm^{-3}}, 
\end{equation}$$ where $L({\rm H\alpha}) = 4 \pi D^2 F{(\rm H\alpha)_{tot}}$.

Due to the resolution limitations, the radius of the HII region may be overestimated. Additionally, electrons might not be fully distributed throughout the HII region. These factors can lead to an underestimation of the electron density (cite: Egorov2023-678). For our samples, the typical value of the calculated electron density is only $\approx$1 cm$^{-3}$. Then we have the typical mass of ionized gas in HII regions being $\approx$10$^{4.5} M_{\odot}$, similar to the value presented in Figure 5 of (cite: Egorov2023-678) calculated by the minimum electron density. Using the maximum electron density, the typical mass of the ionized gas in Figure 5 of (cite: Egorov2023-678) is $\approx$10$^{2.5} M_{\odot}$, which means that the electron density has increased by 2 orders of magnitude overall, i.e. to $\approx$100 cm$^{-3}$. Therefore, when a reasonable estimate of the electron density is available, $M_{\rm I}$ can be neglected relative to $M_{\rm cloud}$. A typical value of $M_{\rm cloud}$ is $\approx$10$^{6.3} M_{\odot}$. Thus, we have $$\begin{equation}
\label{e-sfe}
{\rm SFE} \approx \frac{M_{\rm *,tot}}{M_{\rm cloud}+M_{\rm *,tot}}.
\end{equation}$$

Using Eq.[\[e-sfe\]](#e-sfe), we estimate the SFE for the clouds in five galaxies. The median value of the SFE in Fig.[9](#SFE) is $\approx$1.4%, which is comparable with the values listed in (cite: Kim2022-516; Chevance2023-534).

## The ICIMF theory

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| $y$ | $x$ | $k$ | $\Delta k$ | $b$ | $\Delta b$ | $r$ |
| log$_{10}$($M_{\rm assoc, tot}$/$M_{\odot}$) | log$_{10}$($M_{\rm cloud}$/$M_{\odot}$) | 0.577 | 0.064 | 0.685 | 0.410 | 0.450 |
| log$_{10}$($M_{\rm assoc, max}$/$M_{\odot}$) | log$_{10}$($M_{\rm cloud}$/$M_{\odot}$) | 0.563 | 0.064 | 0.753 | 0.411 | 0.441 |
| log$_{10}$($M_{\rm cluster, max}$/$M_{\odot}$) | log$_{10}$($M_{\rm cloud}$/$M_{\odot}$) | 0.796 | 0.082 | -1.008 | 0.536 | 0.622 |
| log$_{10}$($M_{\rm cluster, max}$/$M_{\odot}$) | log$_{10}$($N_{\rm cloud}$/${\rm cm}^{-2}$) | 0.961 | 0.117 | -16.58 | 2.527 | 0.561 |
| log$_{10}$($M_{\rm cluster, max}$/$M_{\odot}$) | log$_{10}$($R_{\rm eff}$/${\rm pc}$) | 1.539 | 0.340 | 1.005 | 0.693 | 0.350 |
| log$_{10}$($M_{\rm *, tot}$/$M_{\odot}$) | log$_{10}$($M_{\rm cloud}$/$M_{\odot}$) | 0.663 | 0.061 | 0.086 | 0.395 | 0.478 |
| log$_{10}$($M_{\rm *, tot}$/$M_{\odot}$) | log$_{10}$($M_{\rm *, tot, emb}$/$M_{\odot}$) | 0.602 | 0.054 | 2.318 | 0.175 | 0.536 |
| log$_{10}$($M_{\rm cluster, max}$/$M_{\odot}$) | log$_{10}$($M_{\rm cluster, max, emb}$/$M_{\odot}$) | 0.709 | 0.086 | 1.737 | 0.285 | 0.655 |
| log$_{10}$($M_{\rm cluster, max}$/$M_{\odot}$) | log$_{10}$\[${\rm SFR}_{\rm cloud}$/($M_{\odot} {\rm yr}^{-1}$)\] | 0.713 | 0.069 | 6.192 | 0.226 | 0.708 |
| log$_{10}$($M_{\rm cluster, max}$/$M_{\odot}$) | log$_{10}$\[$\Sigma_{\rm SFR, cloud}$/($M_{\odot} {\rm yr}^{-1} {\rm kpc}^{-2}$)\] | 0.832 | 0.081 | 5.283 | 0.141 | 0.709 |
| log$_{10}$(SFE) | log$_{10}$($M_{\rm cloud}$/$M_{\odot}$) | -0.320 | 0.058 | -0.034 | 0.374 | -0.267 |
|  |  |  |  |  |  |  |

![](g333/cmf.pdf)

![](g333/fit.pdf)

Table.[\[correlation\]](#correlation) summarizes all the fitted correlations between the physical parameters of molecular clouds and their internal stellar populations. In this section, we will verify that the $M_{\rm cluster, max}$-$M_{\rm cloud}$ relation can be understood theoretically on the basis of the integrated cloud-wide IMF (ICIMF) theory. We start by assuming all the stars in a cloud form in a population of embedded clusters with the mass function $$\begin{equation}
\label{beta}
\xi_{\mathrm{ecl}}(M_{\mathrm{ecl}})=
k_{\mathrm{ecl}} M_{\mathrm{ecl}}^{-\beta} (M_{\mathrm{ecl,min}} \leqslant M_{\mathrm{ecl}} \leqslant M_{\mathrm{ecl,max}}),
\end{equation}$$ where $k_{\mathrm{ecl}}$ is a normalization constant and $M_{\mathrm{ecl}}$ is the stellar mass of the embedded cluster. The mass of the smallest stellar group observed in (cite: Kuhn2015-812) is $\approx 5 M_{\odot}$. Thus, we take $M_{\mathrm{ecl,min}}=5 M_{\odot}$, which is also consistent with the value adopted in (cite: Yan2017-607). The embedded cluster population mass conservation gives $$\begin{equation}
\label{eq:MtotintMecl}
M_{\mathrm{*,tot}}=\int_{M_{\mathrm{ecl,min}}}^{M_{\mathrm{ecl,max}}}M_{\mathrm{ecl}}~\xi_{\mathrm{ecl}}(M_{\mathrm{ecl}})\,\mathrm{d}M_{\mathrm{ecl}},
\end{equation}$$ where $M_{\mathrm{*,tot}}$ is the total stellar mass formed in a cloud. $M_{\mathrm{*,tot}}$ and the cloud mass are linked by the star formation efficiency, i.e. $$\begin{equation}
M_{\mathrm{*,tot}} \approx \mathrm{SFE}*M_{\mathrm{cloud}}.
\end{equation}$$ To determine the stellar masses within a stellar system based on a given IMF, one needs to apply a specific sampling method. Here, we adopt the optimal sampling. The details of this method and its validity are available in (cite: Kroupa2013-115; Schulz2015-582; Kroupa2015-93; Yan2017-607; Yan2023-670). The optimal sampling normalization condition is $$\begin{equation}
\label{eq:1intMecl}
1=\int_{M_{\mathrm{ecl,max}}}^{M_{\mathrm{ecl,up}}}\xi_{\mathrm{ecl}}(M_{\mathrm{ecl}})\,\mathrm{d}M_{\mathrm{ecl}}.
\end{equation}$$ We take the upper integration limit (the hypothetical physical upper bound of embedded cluster mass) as $M_{\mathrm{ecl,up}} \approx 10^9$ M$_{\odot}$, following (cite: Yan2017-607). This normalization form is based on the assumption that there exists exactly one object within the mass range from $M_{\mathrm{ecl,max}}$ to $M_{\mathrm{ecl,up}}$ (cite: Schulz2015-582).

By solving Eqs.(8)-(11), we can build the relations between $M_{\mathrm{ecl,max}}$ ($\approx M_{\mathrm{cluster,max}}$), $M_{\mathrm{*,tot}}$ and $M_{\mathrm{cloud}}$. Setting $x \equiv M_{\mathrm{ecl,max}}$, $y \equiv M_{\mathrm{*,tot}}$, $z \equiv M_{\mathrm{ecl,min}}$ and $C \equiv M_{\mathrm{ecl,up}}$, the solution of the equations has two cases: When $\beta \neq 2$, $$\begin{equation}
\label{s1}
y= \frac{z^{2-\beta}-x^{2-\beta}}
{\frac{\beta - 2}{1 - \beta}
\left(C^{1 - \beta} - x^{1 - \beta}\right)} \approx
\frac{(\beta-1)(x^{2-\beta}-z^{2-\beta})}{(2-\beta)x^{1-\beta}}.
\end{equation}$$ When $\beta = 2$, $$\begin{equation}
\label{s2}
y= \frac{\ln{\left(x \right)}-\ln{\left(z \right)}}
{\frac{1}{1 - \beta}
\left(C^{1 - \beta} - x^{1 - \beta}\right)} \approx x\ln{\left(\frac{x}{z} \right)}.
\end{equation}$$ In Eq.[\[s1\]](#s1) and Eq.[\[s2\]](#s2), when $\beta>1$, as long as $M_{\mathrm{ecl,up}}$ is sufficiently larger than $M_{\mathrm{ecl,max}}$, its specific value is not important.

For the slope $\beta$ of the cluster mass function in Eq.[\[beta\]](#beta), generally, the value is $\approx$2 (cite: Lada2003-41; Krumholz2019-57; Mok2020-893; Wainer2022-928). For massive and compact clusters, such as Super Star Clusters (SSCs), the slope can be $\approx$1.8 (cite: Cuevas2023-525). Using the most massive clusters associated with molecular clouds presented in Fig.[5](#cluster)(a), we fitted the cluster mass function in Fig.[10](#cmf)(a). It indeed provides a slightly flatter slope, with $\beta \approx$1.82. For all clusters associated with molecular clouds, the slope is $\approx$1.94. However, as shown in Fig.[10](#cmf), the most massive clusters and all clusters have comparable mass distributions, rather than the most massive clusters having a systematically larger mass. Since we will use the model to fit the $M_{\rm cluster, max}$-$M_{\rm cloud}$ relation, taking the slope fitted in Fig.[10](#cmf)(a) is more appropriate. As shown in Fig.[11](#fit), when fixing SFE=1.4%, a smaller $\beta$ can provide a better fit. To some extent, a smaller $\beta$ and a larger SFE are equivalent.

For low-mass molecular clouds, larger SFE will yield a better fit. The fact that low-mass molecular clouds have higher SFEs can be observed in Fig.[9](#SFE).

On the galaxy scale, (cite: Weidner2013-436) suggests the embedded cluster mass function to be flatter (top heavy) for galaxies with a high SFR, with a dependence that is given by $$\begin{equation}
\label{b-sfr}
\beta=-0.106\log_{10}\mbox{SFR}+2,
\end{equation}$$ where the SFR is in unit of $[\mathrm{M}_{\odot}/\mathrm{yr}]$. In (cite: Weidner2004-350; Weidner2005-625), the observed most massive embedded star cluster in a galaxy is determined through the total galaxy-wide SFR $$\begin{equation}
\label{}
\frac{M_{\rm ecl, max}}{M_{\odot}}\propto\left(\frac{\mbox{SFR}}{\mathrm{M}_{\odot}/\mathrm{yr}}\right)^{0.75}.
\end{equation}$$ Fig.[8](#SFR)(a) shows a clear correlation between $M_{\rm cluster, max}$ and ${\rm SFR}_{\rm cloud}$, with a slope of $\approx$0.71. Thus, similar to Eq.[\[b-sfr\]](#b-sfr), a $\beta$-SFR relation should also exist on the cloud scale.

Surveying adequately complete cluster populations in molecular clouds of nearby galaxies to fit the cloud-scale $\beta$ remains challenging, but it is feasible for molecular clouds in the Milky Way. In order to better fit the observational data in Fig.[11](#fit), we need to understand how $\beta$ varies with the properties of the molecular clouds.

Both SFE and $\beta$ vary with the physical properties of the molecular clouds. Therefore, using the same parameter settings for all molecular clouds can only result in a rough fit. Moreover, in this work, we use an unified CO$-$to$-$H$_{2}$ conversion factor (i.e. $\alpha^{2-1}_{\rm CO} \approx 6.7~\rm M_{\odot} \rm pc^{-2} (\rm K~km~s^{-1})^{-1}$) for all five galaxies. But $\alpha^{2-1}_{\rm CO}$ may vary with the galaxy, and even different locations within the same galaxy may have different $\alpha^{2-1}_{\rm CO}$. Therefore, it is important to correct $\alpha^{2-1}_{\rm CO}$ for each molecular cloud to accurately estimate the mass of the cloud. This will be left for future work.

# Conclusion

In this study, we first investigated the connections between the physical characteristics of molecular clouds and their stellar populations. We then utilized the ICIMF theory to interpret the observed patterns.

The main conclusions are as follows:

1\. The molecular clouds in five galaxies (NGC 1433, NGC 1566, NGC 1559, NGC 3351 and NGC 3627) were identified based on the integrated intensity (Moment 0) maps of CO (2$-$1) emission from ALMA observations. The catalogs for compact clusters and multi-scale associations across these galaxies were matched with the identified clouds. We used the JWST 21 $\mu$m data to estimate the star formation rate (SFR) surface density of the clouds and calculate the masses of the embedded stellar populations in the clouds, and found that the embedded stellar population mass is systematically smaller than that of the exposed stellar population. This suggests a short duration of the embedded phase. We found that the mass of the most massive cluster ($M_{\rm cluster, max}$) in a cloud is positively proportional to the mass ($M_{\rm cloud}$), the column density, the SFR and the SFR surface density of the cloud.

2\. The mass of the ionized gas ($M_{\rm I}$) in each cloud can be neglected relative to $M_{\rm cloud}$. Based on the masses of the total stellar populations and their corresponding clouds, we obtained a typical value of the cloud-scale SFE, $\approx$1.4%. There is a trend that the SFE decreases as the cloud mass increases. More massive clouds lead to a larger stellar population and more massive star clusters, resulting in stronger feedback. This may suppress star formation in massive clouds, leading to a relatively lower SFE. This self-regulated star formation also supports the choice of the optimal sampling.

3\. We constructed an integrated cloud-wide IMF (ICIMF) model that provides a good fit to the observed $M_{\rm cluster, max}$-$M_{\rm cloud}$ relation. When fixing SFE$=$1.4%, there is only one free parameter $\beta$ (the slope of the cluster mass function) in the solutions. For low-mass molecular clouds, a higher SFE can yield a better fit, consistent with the observations. The ICIMF theory provides a quantitative framework for understanding the correlations between molecular clouds and their internal stellar populations.

# Data availability

All the data used in this work are available on the PHANGS team website. [^7].

# Acknowledgements

We would like to thank the referee for the detailed comments and suggestions, which have helped to improve and clarify this work. We thank Z. Q. Yan for helpful comments. It is a pleasure to thank the PHANGS team, the data cubes and other data products shared by the team make this work can be carried out smoothly.

natexlab

(ref: Chevance2021) Chevance, M. 2021, in American Astronomical Society Meeting Abstracts, Vol. 237, American Astronomical Society Meeting Abstracts, 223.03

(ref: Chevance2023-534) Chevance, M., Krumholz, M. R., McLeod, A. F., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 1, doi: [`10.48550/arXiv.2203.09570`](http://doi.org/10.48550/arXiv.2203.09570)

(ref: Chevance2022-509) Chevance, M., Kruijssen, J. M. D., Krumholz, M. R., et al. 2022, MNRAS, 509, 272, doi: [`10.1093/mnras/stab2938`](http://doi.org/10.1093/mnras/stab2938)

(ref: Cuevas2023-525) Cuevas-Otahola, B., Mayya, Y. D., Arriaga-Hernández, J., Puerari, I., & Bruzual, G. 2023, MNRAS, 525, 5262, doi: [`10.1093/mnras/stad2643`](http://doi.org/10.1093/mnras/stad2643)

(ref: Davis2013-429) Davis, T. A., Alatalo, K., Bureau, M., et al. 2013, MNRAS, 429, 534, doi: [`10.1093/mnras/sts353`](http://doi.org/10.1093/mnras/sts353)

(ref: Dib2022-666) Dib, S. 2022, A&A, 666, A113, doi: [`10.1051/0004-6361/202243793`](http://doi.org/10.1051/0004-6361/202243793)

(ref: Dib2012ApJ-758) Dib, S., Helou, G., Moore, T. J. T., Urquhart, J. S., & Dariush, A. 2012, ApJ, 758, 125, doi: [`10.1088/0004-637X/758/2/125`](http://doi.org/10.1088/0004-637X/758/2/125)

(ref: Dinnbier2022-660) Dinnbier, F., Kroupa, P., & Anderson, R. I. 2022, A&A, 660, A61, doi: [`10.1051/0004-6361/202142082`](http://doi.org/10.1051/0004-6361/202142082)

(ref: Egorov2023-678) Egorov, O. V., Kreckel, K., Glover, S. C. O., et al. 2023, A&A, 678, A153, doi: [`10.1051/0004-6361/202346919`](http://doi.org/10.1051/0004-6361/202346919)

(ref: Elmegreen2014-787) Elmegreen, D. M., Elmegreen, B. G., Adamo, A., et al. 2014, ApJL, 787, L15, doi: [`10.1088/2041-8205/787/1/L15`](http://doi.org/10.1088/2041-8205/787/1/L15)

(ref: Emsellem2022-659) Emsellem, E., Schinnerer, E., Santoro, F., et al. 2022, A&A, 659, A191, doi: [`10.1051/0004-6361/202141727`](http://doi.org/10.1051/0004-6361/202141727)

(ref: Gouliermis2015MNRAS-452) Gouliermis, D. A., Thilker, D., Elmegreen, B. G., et al. 2015, MNRAS, 452, 3508, doi: [`10.1093/mnras/stv1325`](http://doi.org/10.1093/mnras/stv1325)

(ref: Gouliermis2017-468) Gouliermis, D. A., Elmegreen, B. G., Elmegreen, D. M., et al. 2017, MNRAS, 468, 509, doi: [`10.1093/mnras/stx445`](http://doi.org/10.1093/mnras/stx445)

(ref: Grasha2017-840) Grasha, K., Calzetti, D., Adamo, A., et al. 2017, ApJ, 840, 113, doi: [`10.3847/1538-4357/aa6f15`](http://doi.org/10.3847/1538-4357/aa6f15)

(ref: Groves2023-520) Groves, B., Kreckel, K., Santoro, F., et al. 2023, MNRAS, 520, 4902, doi: [`10.1093/mnras/stad114`](http://doi.org/10.1093/mnras/stad114)

(ref: Haslbauer2024arXiv) Haslbauer, M., Yan, Z., Jerabkova, T., et al. 2024, arXiv e-prints, arXiv:2405.05313, doi: [`10.48550/arXiv.2405.05313`](http://doi.org/10.48550/arXiv.2405.05313)

(ref: Jerabkova2018-620) Jerabkova, T., Hasani Zonoozi, A., Kroupa, P., et al. 2018, A&A, 620, A39, doi: [`10.1051/0004-6361/201833055`](http://doi.org/10.1051/0004-6361/201833055)

(ref: Kim2021-504) Kim, J., Chevance, M., Kruijssen, J. M. D., et al. 2021, MNRAS, 504, 487, doi: [`10.1093/mnras/stab878`](http://doi.org/10.1093/mnras/stab878)

(ref: Kim2022-516) —. 2022, MNRAS, 516, 3006, doi: [`10.1093/mnras/stac2339`](http://doi.org/10.1093/mnras/stac2339)

(ref: Kim2023-944) —. 2023, ApJL, 944, L20, doi: [`10.3847/2041-8213/aca90a`](http://doi.org/10.3847/2041-8213/aca90a)

(ref: Kim2016-819) Kim, J.-G., Kim, W.-T., & Ostriker, E. C. 2016, ApJ, 819, 137, doi: [`10.3847/0004-637X/819/2/137`](http://doi.org/10.3847/0004-637X/819/2/137)

(ref: Kroupa1995a-277) Kroupa, P. 1995a, MNRAS, 277, 1491, doi: [`10.1093/mnras/277.4.1491`](http://doi.org/10.1093/mnras/277.4.1491)

(ref: Kroupa1995b-277) —. 1995b, MNRAS, 277, 1507, doi: [`10.1093/mnras/277.4.1507`](http://doi.org/10.1093/mnras/277.4.1507)

(ref: Kroupa2005-576) Kroupa, P. 2005, in ESA Special Publication, Vol. 576, The Three-Dimensional Universe with Gaia, ed. C. Turon, K. S. O’Flaherty, & M. A. C. Perryman, 629, doi: [`10.48550/arXiv.astro-ph/0412069`](http://doi.org/10.48550/arXiv.astro-ph/0412069)

(ref: Kroupa2015-93) —. 2015, Canadian Journal of Physics, 93, 169, doi: [`10.1139/cjp-2014-0179`](http://doi.org/10.1139/cjp-2014-0179)

(ref: Kroupa2003-598) Kroupa, P., & Weidner, C. 2003, ApJ, 598, 1076, doi: [`10.1086/379105`](http://doi.org/10.1086/379105)

(ref: Kroupa2013-115) Kroupa, P., Weidner, C., Pflamm-Altenburg, J., et al. 2013, in Planets, Stars and Stellar Systems. Volume 5: Galactic Structure and Stellar Populations, ed. T. D. Oswalt & G. Gilmore, Vol. 5, 115, doi: [`10.1007/978-94-007-5612-0_4`](http://doi.org/10.1007/978-94-007-5612-0_4)

(ref: Kruijssen2019-569) Kruijssen, J. M. D., Schruba, A., Chevance, M., et al. 2019, Nature, 569, 519, doi: [`10.1038/s41586-019-1194-3`](http://doi.org/10.1038/s41586-019-1194-3)

(ref: Krumholz2019-57) Krumholz, M. R., McKee, C. F., & Bland-Hawthorn, J. 2019, ARA&A, 57, 227, doi: [`10.1146/annurev-astro-091918-104430`](http://doi.org/10.1146/annurev-astro-091918-104430)

(ref: Kuhn2015-812) Kuhn, M. A., Feigelson, E. D., Getman, K. V., et al. 2015, ApJ, 812, 131, doi: [`10.1088/0004-637X/812/2/131`](http://doi.org/10.1088/0004-637X/812/2/131)

(ref: Lada2003-41) Lada, C. J., & Lada, E. A. 2003, ARA&A, 41, 57, doi: [`10.1146/annurev.astro.41.011802.094844`](http://doi.org/10.1146/annurev.astro.41.011802.094844)

(ref: Larson2023-523) Larson, K. L., Lee, J. C., Thilker, D. A., et al. 2023, MNRAS, 523, 6061, doi: [`10.1093/mnras/stad1600`](http://doi.org/10.1093/mnras/stad1600)

(ref: Lee2022-258) Lee, J. C., Whitmore, B. C., Thilker, D. A., et al. 2022, ApJS, 258, 10, doi: [`10.3847/1538-4365/ac1fe5`](http://doi.org/10.3847/1538-4365/ac1fe5)

(ref: Lee2023-944) Lee, J. C., Sandstrom, K. M., Leroy, A. K., et al. 2023, ApJL, 944, L17, doi: [`10.3847/2041-8213/acaaae`](http://doi.org/10.3847/2041-8213/acaaae)

(ref: Leroy2021-257) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021a, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: Leroy2021-255) Leroy, A. K., Hughes, A., Liu, D., et al. 2021b, ApJS, 255, 19, doi: [`10.3847/1538-4365/abec80`](http://doi.org/10.3847/1538-4365/abec80)

(ref: Leroy2022-927) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2022, ApJ, 927, 149, doi: [`10.3847/1538-4357/ac3490`](http://doi.org/10.3847/1538-4357/ac3490)

(ref: Levy2024arXiv) Levy, R. C., Bolatto, A. D., Mayya, D., et al. 2024, arXiv e-prints, arXiv:2408.04135, doi: [`10.48550/arXiv.2408.04135`](http://doi.org/10.48550/arXiv.2408.04135)

(ref: Lindner2015-149) Lindner, R. R., Vera-Ciro, C., Murray, C. E., et al. 2015, AJ, 149, 138, doi: [`10.1088/0004-6256/149/4/138`](http://doi.org/10.1088/0004-6256/149/4/138)

(ref: Megeath2016-151) Megeath, S. T., Gutermuth, R., Muzerolle, J., et al. 2016, AJ, 151, 5, doi: [`10.3847/0004-6256/151/1/5`](http://doi.org/10.3847/0004-6256/151/1/5)

(ref: Miville2017-834) Miville-Deschênes, M.-A., Murray, N., & Lee, E. J. 2017, ApJ, 834, 57, doi: [`10.3847/1538-4357/834/1/57`](http://doi.org/10.3847/1538-4357/834/1/57)

(ref: Mok2020-893) Mok, A., Chandar, R., & Fall, S. M. 2020, ApJ, 893, 135, doi: [`10.3847/1538-4357/ab7a14`](http://doi.org/10.3847/1538-4357/ab7a14)

(ref: Riener2019-628) Riener, M., Kainulainen, J., Henshaw, J. D., et al. 2019, A&A, 628, A78, doi: [`10.1051/0004-6361/201935519`](http://doi.org/10.1051/0004-6361/201935519)

(ref: Rosolowsky2021-502) Rosolowsky, E., Hughes, A., Leroy, A. K., et al. 2021, MNRAS, 502, 1218, doi: [`10.1093/mnras/stab085`](http://doi.org/10.1093/mnras/stab085)

(ref: Rosolowsky2008-679) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ, 679, 1338, doi: [`10.1086/587685`](http://doi.org/10.1086/587685)

(ref: Santoro2022-658) Santoro, F., Kreckel, K., Belfiore, F., et al. 2022, A&A, 658, A188, doi: [`10.1051/0004-6361/202141907`](http://doi.org/10.1051/0004-6361/202141907)

(ref: Schulz2015-582) Schulz, C., Pflamm-Altenburg, J., & Kroupa, P. 2015, A&A, 582, A93, doi: [`10.1051/0004-6361/201425296`](http://doi.org/10.1051/0004-6361/201425296)

(ref: Thilker2022-509) Thilker, D. A., Whitmore, B. C., Lee, J. C., et al. 2022, MNRAS, 509, 4094, doi: [`10.1093/mnras/stab3183`](http://doi.org/10.1093/mnras/stab3183)

(ref: Turner2021-502) Turner, J. A., Dale, D. A., Lee, J. C., et al. 2021, MNRAS, 502, 1366, doi: [`10.1093/mnras/stab055`](http://doi.org/10.1093/mnras/stab055)

(ref: Turner2022-516) Turner, J. A., Dale, D. A., Lilly, J., et al. 2022, MNRAS, 516, 4612, doi: [`10.1093/mnras/stac2559`](http://doi.org/10.1093/mnras/stac2559)

(ref: Urquhart2022-510) Urquhart, J. S., Wells, M. R. A., Pillai, T., et al. 2022, MNRAS, 510, 3389, doi: [`10.1093/mnras/stab3511`](http://doi.org/10.1093/mnras/stab3511)

(ref: Wainer2022-928) Wainer, T. M., Johnson, L. C., Seth, A. C., et al. 2022, ApJ, 928, 15, doi: [`10.3847/1538-4357/ac51cf`](http://doi.org/10.3847/1538-4357/ac51cf)

(ref: Watkins2023-676) Watkins, E. J., Kreckel, K., Groves, B., et al. 2023, A&A, 676, A67, doi: [`10.1051/0004-6361/202346075`](http://doi.org/10.1051/0004-6361/202346075)

(ref: Weidner2005-625) Weidner, C., & Kroupa, P. 2005, ApJ, 625, 754, doi: [`10.1086/429867`](http://doi.org/10.1086/429867)

(ref: Weidner2004-350) Weidner, C., Kroupa, P., & Larsen, S. S. 2004, MNRAS, 350, 1503, doi: [`10.1111/j.1365-2966.2004.07758.x`](http://doi.org/10.1111/j.1365-2966.2004.07758.x)

(ref: Weidner2013-436) Weidner, C., Kroupa, P., Pflamm-Altenburg, J., & Vazdekis, A. 2013, MNRAS, 436, 3309, doi: [`10.1093/mnras/stt1806`](http://doi.org/10.1093/mnras/stt1806)

(ref: Whitmore2021-506) Whitmore, B. C., Lee, J. C., Chandar, R., et al. 2021, MNRAS, 506, 5294, doi: [`10.1093/mnras/stab2087`](http://doi.org/10.1093/mnras/stab2087)

(ref: Williams2024-273) Williams, T. G., Lee, J. C., Larson, K. L., et al. 2024, ApJS, 273, 13, doi: [`10.3847/1538-4365/ad4be5`](http://doi.org/10.3847/1538-4365/ad4be5)

(ref: Yan2017-607) Yan, Z., Jerabkova, T., & Kroupa, P. 2017, A&A, 607, A126, doi: [`10.1051/0004-6361/201730987`](http://doi.org/10.1051/0004-6361/201730987)

(ref: Yan2023-670) —. 2023, A&A, 670, A151, doi: [`10.1051/0004-6361/202244919`](http://doi.org/10.1051/0004-6361/202244919)

(ref: Zhou2024MNRAS.tmp.2058Z) Zhou, J. W., Dib, S., & Davis, T. A. 2024a, MNRAS, 534, 683, doi: [`10.1093/mnras/stae2101`](http://doi.org/10.1093/mnras/stae2101)

(ref: Zhou2024-682) Zhou, J. W., Wyrowski, F., Neupane, S., et al. 2024b, A&A, 682, A128, doi: [`10.1051/0004-6361/202347377`](http://doi.org/10.1051/0004-6361/202347377)

(ref: Zhou2024-682-128) —. 2024c, A&A, 682, A128, doi: [`10.1051/0004-6361/202347377`](http://doi.org/10.1051/0004-6361/202347377)

(ref: Zhou2023-676) —. 2023, A&A, 676, A69, doi: [`10.1051/0004-6361/202346500`](http://doi.org/10.1051/0004-6361/202346500)

(ref: Zhou2024-682-173) Zhou, J. W., Dib, S., Wyrowski, F., et al. 2024d, A&A, 682, A173, doi: [`10.1051/0004-6361/202348108`](http://doi.org/10.1051/0004-6361/202348108)

[^1]: E-mail: jwzhou@mpifr-bonn.mpg.de

[^2]: E-mail: pkroupa@uni-bonn.de

[^3]: E-mail: dib@mpia.de

[^4]: <https://sites.google.com/view/phangs/home>

[^5]: <https://dendrograms.readthedocs.io/en/stable/index.html>

[^6]: Details of the masking strategy and completeness statistics are presented in the PHANGS pipeline paper (cite: Leroy2021-255).

[^7]: <https://sites.google.com/view/phangs/home>

</paper>

Write the methods card for this paper.